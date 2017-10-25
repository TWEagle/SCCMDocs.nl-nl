---
title: Beheerpunt databasereplica | Microsoft Docs
description: Een databasereplica gebruiken om te beperken van de CPU-belasting die door beheerpunten op de Sitedatabaseserver wordt geplaatst.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b06f781b-ab25-4d9a-b128-02cbd7cbcffe
caps.latest.revision: "9"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 130c053c9f2a1817dd85b1f3c01285aab19d59cb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="database-replicas-for-management-points-for-system-center-configuration-manager"></a>Databasereplica's voor beheerpunten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Primaire sites van System Center Configuration Manager kunnen u een databasereplica gebruiken om te verminderen de CPU-belasting op de Sitedatabaseserver geplaatst door beheerpunten serviceaanvragen van clients.  

-   Als een beheerpunt een databasereplica gebruikt, vraagt dat beheerpunt gegevens aan bij de SQL Server-computer die de databasereplica host en niet bij de sitedatabaseserver.  

-   Zodoende kunt u mogelijk de CPU-verwerkingsvereisten voor de sitedatabaseserver reduceren door de offloading van frequente verwerkingstaken die aan clients zijn gerelateerd.  Een voorbeeld van een frequente verwerkingstaak voor clients is een site met een groot aantal clients die regelmatig aanvragen voor clientbeleid indienen.  


##  <a name="bkmk_Prepare"></a> Voorbereiden van het gebruik van databasereplica's  
**Databasereplica's voor beheerpunten:**  

-   Een replica is een gedeeltelijke kopie van de sitedatabase die is gerepliceerd naar een apart exemplaar van SQL Server:  

    -   Primaire sites ondersteunen een specifieke databasereplica voor elk beheerpunt op de site (secundaire sites ondersteunen geen Databasereplica's)  

    -   Eén databasereplica kan worden gebruikt door meer dan één beheerpunt van dezelfde website.  

    -   Een SQL-server kan meerdere databasereplica's hosten voor gebruik door verschillende beheerpunten, zolang ze maar in een apart exemplaar van SQL Server worden uitgevoerd.  

-   Replica's synchroniseren op geplande tijden een kopie van de sitedatabase met de gegevens die door de sitedatabaseserver voor dit doel worden gepubliceerd.  

-   Beheerpunten kunnen worden geconfigureerd voor het gebruik van een replica wanneer u het beheerpunt installeert of op een later tijdstip door het eerder geïnstalleerde beheerpunt opnieuw te configureren voor het gebruik van de databasereplica.  

-   Controleer regelmatig de sitedatabaseserver en iedere databasereplicaserver om er zeker van te zijn dat de replicatie tussen de twee plaatsvindt en dat de prestaties van de databasereplicaserver voldoende zijn voor de site en de clientprestaties die u nodig hebt.  

**Vereisten voor databasereplica's:**  

-   **SQL Server-vereisten:**  

    -   De SQL Server die de databasereplica host, moet voldoen aan dezelfde vereisten als de sitedatabaseserver. Op de replicaserver hoeft echter niet dezelfde versie of editie van SQL Server te worden uitgevoerd als op de sitedatabaseserver, zolang maar een ondersteunde versie en editie van SQL Server wordt uitgevoerd. Zie [Ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

    -   De SQL Server-service op de computer die de replicadatabase host moet als het **systeem** account worden uitgevoerd.  

    -   Zowel op de SQL Server die de sitedatabaseserver host als op de SQL Server die een databasereplica host, moet de **SQL Server-replicatie** zijn geïnstalleerd.  

    -   De sitedatabase moet de databasereplica **publiceren** en elke externe databasereplicaserver moet zijn **geabonneerd** op de gepubliceerde gegevens.  

    -   Zowel de SQL Server die de sitedatabase host als de SQL Server die een databasereplica host, moet worden geconfigureerd voor ondersteuning van een **Max Text Repl Size** van 2 GB. Zie [Configure the max text repl size Server Configuration Option](http://go.microsoft.com/fwlink/p/?LinkId=273960)(De serverconfiguratie-optie Max text repl size configureren) voor een voorbeeld om deze optie op SQL Server 2012 te configureren.  

-   **Zelfondertekend certificaat:** Een replica-database configureren, moet u een zelfondertekend certificaat maken op de databasereplicaserver en dit certificaat beschikbaar maken voor elk beheerpunt dat die databasereplicaserver gebruikt.  

    -   Het certificaat wordt automatisch beschikbaar voor een beheerpunt dat is geïnstalleerd op de database-replicaserver.  

    -   Als u dit certificaat echter beschikbaar wil maken op externe beheerpunten, moet u het certificaat exporteren en het vervolgens toevoegen aan het certificaatarchief **Vertrouwde personen** op het externe beheerpunt.  

-   **Clientmelding:** Ter ondersteuning van clientmelding met een databasereplica voor een beheerpunt, moet u communicatie tussen de Sitedatabaseserver en de databasereplicaserver voor de **SQL Server Service Broker**. Hiervoor moet u het volgende doen:  

    -   Elke database met informatie over de andere database configureren  

    -   Certificaten uitwisselen tussen de twee databases voor een veilige communicatie  

**Beperkingen bij het gebruik van databasereplica's:**  

-   Wanneer uw site is geconfigureerd voor het publiceren van databasereplica's, moeten de volgende procedures in plaats van de normale richtlijnen worden gebruikt:  

    -   [Een siteserver verwijderen die een databasereplica publiceert](#BKMK_DBReplicaOps_Uninstall)  

    -   [Een siteserverdatabase verplaatsen die een databasereplica publiceert](#BKMK_DBReplicaOps_Move)  

-   **Upgrades naar System Center Configuration Manager**: Voordat u een site van System Center 2012 Configuration Manager naar System Center Configuration Manager bijwerkt, moet u Databasereplica's voor beheerpunten uitschakelen.  Na de upgrade van uw site, kunt u de databasereplica's voor beheerpunten opnieuw configureren.  

-   **Meerdere replica's op één SQL Server:**  Als u een databasereplicaserver voor het hosten van meerdere Databasereplica's voor beheerpunten (elke replica moet zich op een afzonderlijk exemplaar) configureert, moet u een aangepast configuratiescript (uit stap 4 van de volgende sectie) gebruiken om te voorkomen dat het zelfondertekende certificaat in gebruik door de eerder geconfigureerde databasereplica op die server wordt overschreven.  

##  <a name="BKMK_DBReplica_Config"></a> Databasereplica's configureren  
De volgende stappen zijn vereist voor het configureren van een databasereplica:  

-   [Stap 1: de sitedatabaseserver configureren voor het publiceren van de databasereplica](#BKMK_DBReplica_ConfigSiteDB)  

-   [Stap 2: de databasereplicaserver configureren](#BKMK_DBReplica_ConfigSrv)  

-   [Stap 3: beheerpunten voor het gebruik van de databasereplica configureren](#BKMK_DBReplica_ConfigMP)  

-   [Stap 4: een zelfondertekend certificaat voor de databasereplicaserver configureren](#BKMK_DBReplica_Cert)  

-   [Stap 5: SQL Server Service Broker voor de databasereplicaserver configureren](#BKMK_DBreplica_SSB)  

###  <a name="BKMK_DBReplica_ConfigSiteDB"></a> Stap 1: de sitedatabaseserver configureren voor het publiceren van de databasereplica  
 Gebruik de volgende procedure als een voorbeeld van hoe u de sitedatabaseserver configureert op een Windows Server 2008 R2-computer voor het publiceren van de databasereplica. Raadpleeg de documentatie van uw besturingssysteem als u een andere versie hebt en pas de stappen in deze procedure zo nodig aan.  

##### <a name="to-configure-the-site-database-server"></a>De sitedatabaseserver configureren  

1.  Stel op de sitedatabaseserver de SQL Server Agent in op automatisch starten.  

2.  Maak op de Sitedatabaseserver een lokale gebruikersgroep met de naam **ConfigMgr_MPReplicaAccess**. U moet het computeraccount voor iedere database-replicaserver die u op deze site gebruikt toevoegen aan deze groep om die database-replicaservers te laten synchroniseren met de gepubliceerde databasereplica.  

3.  Configureer op de Sitedatabaseserver een bestandsshare met de naam **ConfigMgr_MPReplica**.  

4.  Voeg de volgende machtigingen tot de **ConfigMgr_MPReplica** delen:  

    > [!NOTE]  
    >  Als de SQL Server Agent een ander account gebruikt dan het lokale systeemaccount, vervangt u SYSTEEM met die accountnaam in de volgende lijst.  

    -   **Sharemachtigingen**:  

        -   SYSTEEM: **Schrijven**  

        -   ConfigMgr_MPReplicaAccess: **Lezen**  

    -   **NTFS-machtigingen**:  

        -   SYSTEEM: **Volledig beheer**  

        -   ConfigMgr_MPReplicaAccess: **Lees**, **lezen & uitvoeren**, **Mapinhoud weergeven**  

5.  Gebruik **SQL Server Management Studio** voor de verbinding met de sitedatabase en voer de volgende opgeslagen procedure uit als een query: **spCreateMPReplicaPublication**  

Wanneer de opgeslagen procedure is voltooid, wordt de sitedatabaseserver geconfigureerd op het publiceren van de databasereplica.  

###  <a name="BKMK_DBReplica_ConfigSrv"></a> Stap 2: de databasereplicaserver configureren  
De database-replicaserver is een computer die SQL Server uitvoert en die een replica host van de sitedatabase voor gebruik door beheerpunten. De database-replicaserver synchroniseert op geplande tijden zijn kopie van de database met de databasereplica die wordt gepubliceerd door de sitedatabaseserver.  

De database-replicaserver moet voldoen aan dezelfde vereisten als de sitedatabaseserver. De database-replicaserver kan wel een andere editie of versie van SQL Server uitvoeren dan de versie die de sitedatabaseserver gebruikt. Zie de sectie [Ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md)voor meer informatie over de ondersteunde versies van SQL Server.  

> [!IMPORTANT]  
>  De SQL Server-service op de computer die de replicadatabase host moet als het systeemaccount worden uitgevoerd.  

Gebruik de volgende procedure als een voorbeeld van hoe u een databasereplicaserver configureert op een Windows Server 2008 R2-computer. Raadpleeg de documentatie van uw besturingssysteem als u een andere versie hebt en pas de stappen in deze procedure zo nodig aan.  

##### <a name="to-configure-the-database-replica-server"></a>De databasereplicaserver configureren  

1.  Stel op de databasereplicaserver de SQL Server Agent in op automatisch opstarten.  

2.  Gebruik **SQL Server Management Studio** op de databasereplicaserver voor verbinding met de lokale server, blader naar de map **Replicatie** , klik op Lokale abonnementen en selecteer **Nieuwe abonnementen** om de **wizard Nieuwe abonnementen**te starten:  

    1.  Op de pagina **Publicatie** in het lijstvak **Publisher** selecteert u **SQL Server Publisher zoeken**. Voer de naam in van de sitedatabaseserver en klik vervolgens op **Verbinden**.  

    2.  Selecteer **ConfigMgr_MPReplica**, en klik vervolgens op **volgende**.  

    3.  Op de **locatie distributieagent** pagina **iedere agent bij zijn abonnee (pull-abonnementen) uitvoeren**, en klik op **volgende**.  

    4.  Voer een van de volgende acties op de pagina **Abonnees** :  

        -   Selecteer een bestaande database in de database-replicaserver die u wilt gebruiken voor de databasereplica en klik op **OK**.  

        -   Selecteer **Nieuwe database** om een nieuwe database te maken voor de databasereplica. Geef op de pagina **Nieuwe database** een naam op voor de database en klik op **OK**.  

    5.  Klik op **Volgende** om verder te gaan.  

    6.  Op de **Distribution Agent Security** pagina, klikt u op de eigenschappenknop **(...)**  in de rij verbinding met abonneeserver van het dialoogvenster vak en configureer vervolgens de beveiligingsinstellingen voor de verbinding.  

        > [!TIP]  
        >  De eigenschappenknop **(...)** , wordt in de vierde kolom van het weergavevak.  

        **Beveiligingsinstellingen:**  

        -   Configureer het account dat de distributie-agentproces (het procesaccount) uitvoert:  

            -   Als de SQL Server Agent wordt uitgevoerd als lokaal systeem, selecteert u **uitgevoerd onder het account van de SQL Server Agent-service (dit is niet een aanbevolen beveiligingsprocedure.)**  

            -   Als de SQL Server Agent wordt uitgevoerd met een ander account, selecteert u **Uitvoeren onder het volgende Windows-account**en configureert u dat account. U kunt een Windows-account of een SQL Serveraccount opgeven.  

            > [!IMPORTANT]  
            >  U moet aan het account dat de distributieagent uitvoert machtigingen verlenen voor de uitgever als een pull-abonnement. Zie [Distribution Agent Security](http://go.microsoft.com/fwlink/p/?LinkId=238463) (Beveiliging voor distributieagent) in de SQL Server TechNet-bibliotheek voor meer informatie over het configureren van deze machtigingen.  

        -   Voor **Verbinding maken met de distributeur**selecteert u **Door het procesaccount te imiteren**.  

        -   Voor **Verbinding maken met de abonnee**selecteert u **Door het procesaccount te imiteren**.  

         Klik na de configuratie van de instellingen voor verbindingsbeveiliging op **OK** om ze op te slaan en klik op **Volgende**.  

    7.  Op de pagina **Synchronisatieplanning** , in het lijstvak **Schema van agent** , selecteert u **Schema definiëren**en configureert u **Nieuw taakschema**. Stel de uitvoerfrequentie in op **dagelijkse**, herhaald elke **5 minu(u)te(n)**, en de duur op **geen einddatum**. Klik op **Volgende** om de planning op te slaan en klik nogmaals op **Volgende** .  

    8.  Op de **Wizardacties** pagina, selecteert u het selectievakje voor **maken van de abonnementen (s)**, en klik vervolgens op **volgende**.  

    9. Op de pagina **De wizard voltooien** klikt u op **Voltooien**en vervolgens op **Sluiten** om de wizard te voltooien.  

3.  Onmiddellijk na voltooiing van de wizard Nieuwe abonnement, gebruikt u **SQL Server Management Studio** om verbinding te maken met de databasereplicaserver en voert u de volgende query uit om de database-eigenschap TRUSTWORTHY in te schakelen:  `ALTER DATABASE <MP Replica Database Name> SET TRUSTWORTHY ON;`  

4.  Controleer de synchronisatiestatus om te bevestigen dat het abonnement is voltooid:  

    -   Op de computer van de abonnee:  

        -   Maak in **SQL Server Management Studio**de verbinding met de database-replicaserver en vouw **Replicatie**uit.  

        -   Vouw **lokale abonnementen**, met de rechtermuisknop op het abonnement op de publicatie van de sitedatabase en selecteer vervolgens **synchronisatiestatus weergeven**.  

    -   Op de computer van de uitgever:  

        -   In **SQL Server Management Studio**verbinding met de databasecomputer, met de rechtermuisknop op de **replicatie** map en selecteer vervolgens **Replicatiecontrole**.  

5.  Gebruiken om in te schakelen integratie common language runtime (CLR) voor de databasereplica, **SQL Server Management Studio** verbinding maken met de databasereplica op de databasereplicaserver en voer de volgende opgeslagen procedure als een query: **exec sp_configure 'clr enabled', 1; CONFIGUREER DEZE OPNIEUW MET ONDERDRUKKING**  

6.  Voeg voor ieder beheerpunt dat een database-replicaserver gebruikt het computeraccount voor dat beheerpunt toe aan de lokale **beheerders** groep op die database-replicaserver.  

    > [!TIP]  
    >  De stap is niet nodig voor een beheerpunt dat wordt uitgevoerd op de database-replicaserver.  

 De databasereplica is nu gereed voor gebruik door een beheerpunt.  

###  <a name="BKMK_DBReplica_ConfigMP"></a> Stap 3: beheerpunten voor het gebruik van de databasereplica configureren  
 U kunt een beheerpunt configureren op een primaire site voor gebruik van een databasereplica wanneer u de beheerpuntrol installeert. U kunt ook een bestaand beheerpunt opnieuw configureren voor gebruik van een databasereplica.  

 Gebruik de volgende informatie om een beheerpunt te configureren voor gebruik van een databasereplica:  

-   **Een nieuw beheerpunt configureren:** Op de **Beheerpuntdatabase** pagina van de wizard die u gebruikt voor het installeren van het beheerpunt, selecteer **een databasereplica gebruiken**, en geef de FQDN van de computer die als host fungeert voor de databasereplica. Geef vervolgens voor de **Naam van ConfigMgr-sitedatabase**de databasenaam op van de databasereplica op die computer.  

-   **Een eerder geïnstalleerd beheerpunt configureren**: Open de eigenschappenpagina van het beheerpunt, selecteer de **Beheerpuntdatabase** tabblad **een databasereplica gebruiken**, en geef vervolgens de FQDN-naam van de computer die als host fungeert voor de databasereplica. Geef vervolgens voor de **Naam van ConfigMgr-sitedatabase**de databasenaam op van de databasereplica op die computer.  

-   **Voor elk beheerpunt dat gebruikmaakt van een databasereplica**, moet u handmatig het computeraccount van de beheerpuntserver naar toevoegen de **db_datareader** rol voor de databasereplica.  

Naast het configureren van het beheerpunt voor gebruik van de database-replicaserver moet u **Windows-verificatie** inschakelen in **IIS** op het beheerpunt:  

1.  Open **Internet Information Services (IIS) Manager**.  

2.  Selecteer de website die wordt gebruikt door het beheerpunt en open **Verificatie**.  

3.  Stel **Windows-verificatie** naar **ingeschakeld**, en sluit vervolgens **Internet Information Services (IIS) Manager**.  

###  <a name="BKMK_DBReplica_Cert"></a> Stap 4: een zelfondertekend certificaat voor de databasereplicaserver configureren  
 U moet een zelfondertekend certificaat maken op de databasereplicaserver en dit certificaat beschikbaar maken voor elk beheerpunt dat die databasereplicaserver gebruikt.  

 Het certificaat wordt automatisch beschikbaar voor een beheerpunt dat is geïnstalleerd op de database-replicaserver. Als u dit certificaat echter beschikbaar wil maken op externe beheerpunten, moet u het certificaat exporteren en het dan toevoegen aan het vertrouwde personen-certificaatarchief op het externe beheerpunt.  

 Gebruik de volgende procedures als voorbeeld voor het configureren van het zelfondertekende certificaat op de databasereplicaserver voor een computer met Windows Server 2008 R2. Raadpleeg de documentatie van uw besturingssysteem als u een andere versie hebt en pas de stappen in deze procedures zo nodig aan.  

##### <a name="to-configure-a-self-signed-certificate-for-the-database-replica-server"></a>Een zelfondertekend certificaat voor de database-replicaserver configureren  

1.  Open een PowerShell-opdrachtprompt met beheerdersbevoegdheden op de databasereplicaserver en voer de volgende opdracht: **set-executionpolicy UnRestricted**  

2.  Kopieer het volgende PowerShell-script en sla deze op als een bestand met de naam **CreateMPReplicaCert.ps1**. Plaats een kopie van dit bestand in de hoofdmap van de systeempartitie van de database-replicaserver.  

    > [!IMPORTANT]  
    >  Als u meer dan een databasereplica op en afzonderlijke SQL Server configureert, moet u voor elke volgende replica die u configureert een aangepaste versie van dit script voor deze procedure gebruiken. Zie  [Aanvullend script voor extra databasereplica's op één SQL Server](#bkmk_supscript)  

    ```  
    # Script for creating a self-signed certificate for the local machine and configuring SQL Server to use it.  

    Param($SQLInstance)  

    $ConfigMgrCertFriendlyName = "ConfigMgr SQL Server Identification Certificate"  

    # Get local computer name  
    $computerName = "$env:computername"  

    # Get the sql server name  
    #$key="HKLM:\SOFTWARE\Microsoft\SMS\MP"  
    #$value="SQL Server Name"  
    #$sqlServerName= (Get-ItemProperty $key).$value  
    #$dbValue="Database Name"  
    #$sqlInstance_DB_Name= (Get-ItemProperty $key).$dbValue  

    $sqlServerName = [System.Net.Dns]::GetHostByName("localhost").HostName   
    $sqlInstanceName = "MSSQLSERVER"  
    $SQLServiceName = "MSSQLSERVER"  

    if ($SQLInstance -ne $Null)  
    {  
        $sqlInstanceName = $SQLInstance  
        $SQLServiceName = "MSSQL$" + $SQLInstance  
    }  

    # Delete existing cert if one exists  
    function Get-Certificate($storename, $storelocation)  
    {   
        $store=new-object System.Security.Cryptography.X509Certificates.X509Store($storename,$storelocation)   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Certificates   
    }   

    $cert = Get-Certificate "My" "LocalMachine" | ?{$_.FriendlyName -eq $ConfigMgrCertFriendlyName}   
    if($cert -is [Object])  
    {  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("My","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()  

        # Remove this cert from Trusted People too...  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("TrustedPeople","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()      
    }  

    # Create the new cert  
    $name = new-object -com "X509Enrollment.CX500DistinguishedName.1"  
    $name.Encode("CN=" + $sqlServerName, 0)  

    $key = new-object -com "X509Enrollment.CX509PrivateKey.1"  
    $key.ProviderName = "Microsoft RSA SChannel Cryptographic Provider"  
    $key.KeySpec = 1  
    $key.Length = 1024  
    $key.SecurityDescriptor = "D:PAI(A;;0xd01f01ff;;;SY)(A;;0xd01f01ff;;;BA)(A;;0x80120089;;;NS)"  
    $key.MachineContext = 1  
    $key.Create()  

    $serverauthoid = new-object -com "X509Enrollment.CObjectId.1"  
    $serverauthoid.InitializeFromValue("1.3.6.1.5.5.7.3.1")  
    $ekuoids = new-object -com "X509Enrollment.CObjectIds.1"  
    $ekuoids.add($serverauthoid)  
    $ekuext = new-object -com "X509Enrollment.CX509ExtensionEnhancedKeyUsage.1"  
    $ekuext.InitializeEncode($ekuoids)  

    $cert = new-object -com "X509Enrollment.CX509CertificateRequestCertificate.1"  
    $cert.InitializeFromPrivateKey(2, $key, "")  
    $cert.Subject = $name  
    $cert.Issuer = $cert.Subject  
    $cert.NotBefore = get-date  
    $cert.NotAfter = $cert.NotBefore.AddDays(3650)  
    $cert.X509Extensions.Add($ekuext)  
    $cert.Encode()  

    $enrollment = new-object -com "X509Enrollment.CX509Enrollment.1"  
    $enrollment.InitializeFromRequest($cert)  
    $enrollment.CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"  
    $certdata = $enrollment.CreateRequest(0x1)  
    $enrollment.InstallResponse(0x2, $certdata, 0x1, "")  

    # Add this cert to the trusted peoples store  
    [Byte[]]$bytes = [System.Convert]::FromBase64String($certdata)  

    $trustedPeople = new-object System.Security.Cryptography.X509certificates.X509Store "TrustedPeople", "LocalMachine"  
    $trustedPeople.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)  
    $trustedPeople.Add([Security.Cryptography.X509Certificates.X509Certificate2]$bytes)  
    $trustedPeople.Close()  

    # Get thumbprint from cert  
    $sha = new-object System.Security.Cryptography.SHA1CryptoServiceProvider  
    $certHash = $sha.ComputeHash($bytes)  
    $certHashCharArray = "";  
    $certThumbprint = "";  

    # Format the bytes into a hexadecimal string  
    foreach($byte in $certHash)  
    {  
        $temp = ($byte | % {"{0:x}" -f $_}) -join ""  
        $temp = ($temp | % {"{0,2}" -f $_})  
        $certHashCharArray = $certHashCharArray+ $temp;  
    }  
    $certHashCharArray = $certHashCharArray.Replace(' ', '0');  

    # SQL needs the thumbprint in lower case  
    foreach($char in $certHashCharArray)  
    {  
        [System.String]$myString = $char;  
        $certThumbprint = $certThumbprint + $myString.ToLower();  
    }  

    # Configure SQL to use this cert  
    $path = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\Instance Names\SQL"  
    $subKey = (Get-ItemProperty $path).$sqlInstanceName  
    $realPath = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\" + $subKey + "\MSSQLServer\SuperSocketNetLib"  
    $certKeyName = "Certificate"  
    Set-ItemProperty -path $realPath -name $certKeyName -Type string -Value $certThumbprint  

    # restart sql service  
    Restart-Service $SQLServiceName -Force  
    ```  

3.  Voer op de database-replicaserver de volgende opdracht uit die van toepassing is op de configuratie van uw SQL Server:  

    -   Voor een standaardexemplaar van SQL Server: Met de rechtermuisknop op het bestand **CreateMPReplicaCert.ps1** en selecteer **uitvoeren met PowerShell**. Wanneer het script wordt uitgevoerd, maakt het zelfondertekend certificaat en configureert SQL Server voor het gebruik van het certificaat.  

    -   Voor een benoemd exemplaar van SQL Server: PowerShell gebruiken voor het uitvoeren van de opdracht **%path%\CreateMPReplicaCert.ps1 xxxxxx** waar **xxxxxx** is de naam van de SQL Server-exemplaar.  

    -   Controleer, nadat het script voltooid is, of de SQL Server Agent actief is. Als dit niet het geval is, start de SQL Server Agent dan opnieuw op.  

##### <a name="to-configure-remote-management-points-to-use-the-self-signed-certificate-of-the-database-replica-server"></a>Externe beheerpunten voor het gebruik van het zelfondertekende certificaat van de database-replicaserver configureren  

1.  Voer de volgende stappen uit op de databasereplicaserver om van de server zelf-ondertekend certificaat te exporteren:  

    1.  Klik op **Start**, klik op **Uitvoeren**en typ **mmc.exe**. Klik in de lege console op **Bestand**en klik vervolgens op **Module toevoegen/verwijderen**.  

    2.  Selecteer **Certificaten** uit de lijst van **Beschikbare modules** in het dialoogvenster **Modules toevoegen of verwijderen**en klik vervolgens op **Toevoegen**.  

    3.  Selecteer **Computeraccount** in het dialoogvenster **Module certificaten**en klik vervolgens op **Volgende**.  

    4.  Controleer in het dialoogvenster **Computer selecteren** of **Lokale computer: (de computer waarop deze console wordt uitgevoerd)** is geselecteerd en klik vervolgens op **Voltooien**.  

    5.  Klik op **OK** in het dialoogvenster **Modules toevoegen of verwijderen**.  

    6.  In de console, vouw **certificaten (lokale Computer)**, vouw **persoonlijke**, en selecteer **certificaten**.  

    7.  Met de rechtermuisknop op het certificaat met de beschrijvende naam van **ConfigMgr SQL Server Identification Certificate**, klikt u op **alle taken**, en selecteer vervolgens **exporteren**.  

    8.  Doorloop de wizard **Certificaat exporteren** door de standaardopties te gebruiken en sla het certificaat op met de extensie **.cer** .  

2.  Voer de volgende stappen uit op de beheerpuntcomputer het zelfondertekende certificaat voor de database-replicaserver toevoegen aan het certificaatarchief Vertrouwde personen op het beheerpunt:  

    1.  Herhaal de stappen 1.a tot en met 1.e voor het configureren van de **certificaat** module in MMC op de beheerpuntcomputer.  

    2.  Vouw **Certificaten (lokale computer)**uit in de console, vouw **Vertrouwde personen**uit, klik met de rechtermuisknop op **Certificaten**, selecteer **Alle taken**, en selecteer vervolgens **Importeren** om de wizard **Certificaat importeren**te starten.  

    3.  Selecteer op de pagina **Bestand om te importeren** het certificaat dat werd opgeslagen in stap 1.h, en klik daarna op **Volgende**.  

    4.  Selecteer op de pagina **Certificaatarchief** **Alle certificaten in het volgende archief plaatsen**, waarbij **Certificaatarchief** is ingesteld op **Vertrouwde personen**, en klik daarna op **Volgende**.  

    5.  Klik op **Voltooien** om de wizard te sluiten en de configuratie van het certificaat op het beheerpunt te voltooien.  

###  <a name="BKMK_DBreplica_SSB"></a> Stap 5: SQL Server Service Broker voor de databasereplicaserver configureren  
Om clientnotificatie met een databasereplica voor een beheerpunt te ondersteunen, moet u communicatie tussen de sitedatabaseserver en de databasereplicaserver voor de SQL Server Service Broker configureren. Daartoe moet elke database geconfigureerd worden met informatie over de andere database, en moeten certificaten tussen de beide databases worden uitgewisseld voor veilige communicatie.  

> [!NOTE]  
>  Voordat u de volgende procedure kunt gebruiken, moet de databasereplicaserver de initiële synchronisatie met de sitedatabaseserver voltooien.  

 De volgende procedure wijzigt de Service Broker-poort die in SQL Server geconfigureerd is voor de sitedatabaseserver of de databasereplicaserver niet. Wel configureert deze procedure elke database zodanig dat deze communiceert met de andere database door middel van de juiste Service Broker-poort.  

 Gebruik de volgende procedure om de Service Broker te configureren voor de sitedatabaseserver en de databasereplicaserver.  

##### <a name="to-configure-the-service-broker-for-a-database-replica"></a>De Service Broker configureren voor een databasereplica  

1.  Gebruik **SQL Server Management Studio** verbinding maken met de databasereplicaserver en voer de volgende query voor het inschakelen van de Service Broker op de databasereplicaserver: **ALTER DATABASE &lt;replicanaam-Database\> SET ENABLE_BROKER, HONOR_BROKER_PRIORITY op WITH ROLLBACK IMMEDIATE**  

2.  Configureer vervolgens, op de databasereplicaserver, de Service Broker voor clientnotificatie en exporteer het Service Broker-certificaat. Voer hiertoe een op SQL Server opgeslagen procedure uit die in één handeling de Service Broker configureert en het certificaat exporteert. Wanneer u de opgeslagen procedure uitvoert, moet u de FQDN van de databasereplicaserver, de naam van de databasereplica, en een locatie voor het exporteren van het certificaatbestand opgeven.  

     Voer de volgende query voor het configureren van de vereiste gegevens op de databasereplicaserver en het certificaat voor de databasereplicaserver te exporteren: **EXEC sp_BgbConfigSSBForReplicaDB '&lt;FQDN Replica SQL Server\>','&lt;naam Replica-Database\>','&lt;certificaat back-up-bestandspad\>'**  

    > [!NOTE]  
    >  Wanneer de databasereplicaserver niet op de standaardinstantie van SQL Server staat, moet u voor deze stap behalve de naam van de replica-database ook de naam van de instantie specificeren. Om dit te doen, vervangt u de **&lt;Naam van de replicadatabase\>** door **&lt;Instantienaam\\Naam van de replicadatabase\>**.  

     Plaats na het exporteren van het certificaat van de databasereplicaserver een kopie van het certificaat op de databaseserver van de primaire site.  

3.  Gebruik **SQL Server Management Studio** om een verbinding te maken met de database van de primaire site. Voer, nadat u een verbinding maakt met de database van de primaire sites, een query uit om het certificaat te importeren en specificeer de Service Broker-poort die in gebruik is op de databasereplicaserver, de FQDN van de databasereplicaserver en de naam van de database van de databasereplica's. Hiermee wordt de database van de primaire sites zodanig geconfigureerd dat de Service Broker wordt gebruikt voor de communicatie met de database van de databasereplicaserver.  

     Voer de volgende query om te Importeer het certificaat van de databasereplicaserver en specificeer de vereiste gegevens: **EXEC sp_bgbconfigssbforremoteservice 'REPLICA' naar '&lt;SQL Service Broker-poort\>','&lt;bestand certificaatpad\>','&lt;FQDN Replica SQL Server\>','&lt;naam Replica-Database\>'**  

    > [!NOTE]  
    >  Wanneer de databasereplicaserver niet op de standaardinstantie van SQL Server staat, moet u voor deze stap behalve de naam van de replica-database ook de naam van de instantie specificeren. Om dit te doen, Vervang  **&lt;naam Replica-Database\>**  met **\Instance naam\\naam Replica-Database\>**.  

4.  Voer vervolgens de volgende opdracht voor het exporteren van het certificaat voor de Sitedatabaseserver op de Sitedatabaseserver: **EXEC sp_bgbcreateandbackupsqlcert naar '&lt;certificaat back-up-bestandspad\>'**  

     Plaats na het exporteren van het certificaat van de sitedatabaseserver een kopie van het certificaat op de databasereplicaserver.  

5.  Gebruik **SQL Server Management Studio** om een verbinding te maken met de database van de databasereplicaserver. Voer, nadat u een verbinding maakt met de database van de databasereplicaserver, een query uit om het certificaat te importeren en specificeer de sitecode van de primaire site en de Service Broker-poort die in gebruik is op de sitedatabaseserver. Hiermee wordt de databasereplicaserver zodanig geconfigureerd dat de Service Broker wordt gebruikt voor de communicatie met de database van de primaire site.  

     Voer de volgende query voor het importeren van het certificaat uit de Sitedatabaseserver: **EXEC sp_bgbconfigssbforremoteservice naar '&lt;sitecode\>','&lt;SQL Service Broker-poort\>','&lt;bestand certificaatpad\>'**  

 Enkele minuten na het voltooien van de configuratie van de sitedatabase en de database van de databasereplica zet de notificatiemanager op de primaire site het Service Broker-gesprek op voor clientnotificatie van de database van de primaire site naar de databasereplica.  

###  <a name="bkmk_supscript"></a> Aanvullend script voor extra databasereplica's op één SQL Server  
 Wanneer u het script uit stap 4 gebruikt een zelfondertekend certificaat voor de database-replicaserver configureren op een SQL-Server waarop al een databasereplica die u wilt blijven gebruiken, moet u een aangepaste versie van het oorspronkelijke script gebruiken. Met de volgende wijzigingen wordt voorkomen dat het script een bestaand certificaat op de server verwijdert en worden volgende certificaten met unieke beschrijvende namen gemaakt.  Bewerk het oorspronkelijke script als volgt:  

-   Uitcommentariëren (voorkomen dat wordt uitgevoerd) elke regel tussen de scriptvermeldingen **# bestaand certificaat verwijderen als er een bestaat** en **# het nieuwe certificaat maken**. Dit doet u door een  **#**  toe te voegen als eerste teken van elke betreffende regel.  

-   Voor elke volgende databasereplica waarvoor u dit script gebruikt om te configureren, werkt u de beschrijvende naam voor het certificaat bij.  Om dit te doen, bewerkt u de regel **$enrollment. CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"** en vervang **ConfigMgr SQL Server Identification Certificate** met een nieuwe naam zoals **ConfigMgr SQL Server Identification Certificate1**.  

##  <a name="BKMK_DBReplicaOps"></a> Databasereplicaconfiguraties beheren  
 Wanneer u een databasereplica op een site gebruikt, moet u als aanvulling op het proces voor het verwijderen van een databasereplica, het verwijderen van een site die een databasereplica gebruikt, of het verplaatsen van de sitedatabase naar een nieuwe installatie van SQL Server, ook de informatie in de volgende secties gebruiken. Wanneer u informatie in de volgende secties gebruikt om publicaties te verwijderen, maak dan gebruik van de richtlijnen voor het verwijderen van transactionele replicatie voor de versie van SQL Server die u voor de databasereplica gebruikt. Bijvoorbeeld, als u SQL Server 2008 R2 gebruikt, Zie [hoe: Delete a Publication (Replication Transact-SQL Programming)](http://go.microsoft.com/fwlink/p/?LinkId=273934).  

> [!NOTE]  
>  Als u een sitedatabase herstelt die was geconfigureerd voor databasereplica's, moet u, voordat u de databasereplica's kunt gebruiken, elke databasereplica opnieuw configureren, waarbij zowel de publicaties als abonnementen opnieuw worden gemaakt.  

###  <a name="BKMK_UninstallDbReplica"></a> Een databasereplica verwijderen  
 Wanneer u een databasereplica voor een beheerpunt gebruikt, is het wellicht noodzakelijk om de databasereplica voor een bepaalde tijd te verwijderen en deze daarna opnieuw te configureren voor gebruik. Bijvoorbeeld, moet u de Databasereplica's verwijderen voordat u een Configuration Manager-site naar een nieuw servicepack bijwerkt. Nadat de upgrade van de site voltooid is, kunt u de databasereplica terugzetten voor gebruik.  

 Gebruik de volgende stappen om een databasereplica te verwijderen.  

1.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **siteconfiguratie**, selecteer daarna **Servers en sitesysteemrollen**, en selecteer vervolgens in het detailvenster de sitesysteemserver die als host fungeert voor het beheerpunt dat gebruikmaakt van de databasereplica die u verwijdert.  

2.  Klik in het deelvenster **Sitesysteemrollen** met de rechtermuisknop op **Beheerpunt** en selecteer **Eigenschappen**.  

3.  Selecteer op het tabblad **Beheerpuntdatabase** de optie **Gebruik de sitedatabase** om het beheerpunt zodanig te configureren dat de sitedatabase gebruikt wordt in plaats van de databasereplica. Klik op **OK** om de configuratie op te slaan.  

4.  Gebruik vervolgens **SQL Server Management Studio** om de volgende taken uit te voeren:  

    -   Verwijder de publicatie voor de databasereplica van de siteserverdatabase.  

    -   Verwijder het abonnement voor de databasereplica van de databasereplicaserver.  

    -   Verwijder de replica-database van de databasereplicaserver.  

    -   Schakel publiceren en distribueren op de sitedatabaseserver uit. Schakel publiceren en distribueren met de rechtermuisknop op de map replicatie en klik vervolgens op **publicatie en distributie uitschakelen**.  

5.  Nadat u de publicatie, de distributie en de replica-database verwijderd hebt en het publiceren op de sitedatabaseserver hebt uitgeschakeld, is de databasereplica verwijderd.  

###  <a name="BKMK_DBReplicaOps_Uninstall"></a> Een siteserver verwijderen die een databasereplica publiceert  
 Voordat u een site verwijdert die een databasereplica publiceert, moet u de volgende stappen uitvoeren om de publicatie en eventuele abonnementen op te schonen.  

1.  Gebruik **SQL Server Management Studio** om de publicatie van de databasereplica van de siteserverdatabase te verwijderen.  

2.  Gebruik **SQL Server Management Studio** om het abonnement van de databasereplica van elke externe SQL Server te verwijderen waarop een databasereplica voor deze site wordt gehost.  

3.  Verwijder de site.  

###  <a name="BKMK_DBReplicaOps_Move"></a> Een siteserverdatabase verplaatsen die een databasereplica publiceert  
 Wanneer u de sitedatabase naar een nieuwe computer verplaatst, voert u de volgende stappen uit:  

1.  Gebruik **SQL Server Management Studio** om de publicatie voor de databasereplica van de siteserverdatabase te verwijderen.  

2.  Gebruik **SQL Server Management Studio** om het abonnement voor de databasereplica van elke databasereplicaserver voor deze site te verwijderen.  

3.  Verplaats de database naar de nieuwe SQL Server-computer. Zie voor meer informatie de sectie [De configuratie van de sitedatabase wijzigen](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_dbconfig) in het onderwerp [Uw infrastructuur van System Center Configuration Manager aanpassen](../../../../core/servers/manage/modify-your-infrastructure.md).  

4.  Maak de publicatie voor de databasereplica op de sitedatabaseserver opnieuw. Zie [Stap 1: De sitedatabaseserver configureren voor het publiceren van de databasereplica](#BKMK_DBReplica_ConfigSiteDB) in dit onderwerp voor meer informatie.  

5.  Maak de abonnementen voor de databasereplica op elke databasereplicaserver opnieuw. Zie [Stap 2: De databasereplicaserver configureren](#BKMK_DBReplica_ConfigSrv) in dit onderwerp voor meer informatie.  
