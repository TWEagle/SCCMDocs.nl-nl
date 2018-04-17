---
title: Instellen van uw testomgeving
titleSuffix: Configuration Manager
description: Een testomgeving voor het evalueren van Configuration Manager met gesimuleerde activiteiten van de praktijk instellen.
ms.custom: na
ms.date: 09/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1970688-0cd2-404f-a17f-9e2aa4a78758
caps.latest.revision: 11
caps.handback.revision: 0
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: 3441cb417a0b8fc7979b71018f6cfa345c47a02d
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-your-system-center-configuration-manager-lab"></a>Instellen van uw testomgeving voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De instructies in dit onderwerp te volgen, kunt u een testomgeving voor het evalueren van Configuration Manager met gesimuleerde activiteiten van de praktijk instellen.  

##  <a name="BKMK_LabCore"></a> Kernonderdelen  
 Instellen van uw omgeving voor System Center Configuration Manager, moeten sommige kernonderdelen de installatie van Configuration Manager ondersteunen.    

-   **De testomgeving maakt gebruik van Windows Server 2012 R2**, waarin System Center Configuration Manager wordt geïnstalleerd.  

     U kunt een evaluatieversie van Windows Server 2012 R2 van downloaden de [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2012).  

     Overweeg het wijzigen van of verbeterde beveiliging van Internet Explorer uitschakelen om eenvoudiger toegang hebt tot bepaalde downloads waarnaar wordt verwezen tijdens het verloop van deze oefeningen. Controleer [Internet Explorer: Verbeterde beveiliging van](https://technet.microsoft.com/en-us/library/dd883248\(v=ws.10\).aspx) voor meer informatie.  

-   **De testomgeving wordt SQL Server 2012 SP2** voor de sitedatabase.  

     U kunt een evaluatieversie van SQL Server 2012 from downloaden de [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=29066).  

     SQL Server heeft [ondersteunde versies van SQL Server](../../core/plan-design/configs/support-for-sql-server-versions.md#bkmk_SQLVersions) die moet worden voldaan voor gebruik met System Center Configuration Manager.  

    -   Configuration Manager vereist een 64-bits versie van SQL Server om de sitedatabase te hosten.  

    -   **SQL_Latin1_General_CP1_CI_AS** als de **SQL-sortering** klasse.  

    -   **Windows-verificatie**, [in plaats van de SQL-verificatie](https://technet.microsoft.com/library/ms144284.aspx), is vereist.  

    -   Een speciaal **SQL Server-exemplaar** is vereist.  

    -   Beperken niet de **adresseerbare systeemgeheugen** voor SQL Server.  

    -   Configureer de **SQL Server-serviceaccount** om uit te voeren met een lage rights domeingebruikersaccount.  

    -   U moet installeren **voor SQL Server reporting services**.  

    -   **Intersite-communicatie** SQL Server Service Broker op de TCP-standaardpoort 4022 te gebruiken.  

    -   **Intrasitecommunicatie** tussen de SQL Server database engine en selecteer Configuration Manager-sitesysteem functies gebruiken standaardpoort TCP 1433.  

-   **De domeincontroller maakt gebruik van Windows Server 2008 R2** met Active Directory Domain Services. De domeincontroller functioneert ook als host voor de DHCP- en de DNS-servers voor gebruik met een volledig gekwalificeerde domeinnaam.  

     Raadpleeg voor meer informatie dit [overzicht van Active Directory Domain Services](https://technet.microsoft.com/en-us/library/hh831484).  

-   **Hyper-V wordt gebruikt met een paar virtuele machines** om te controleren of de management-stappen die in deze oefeningen werken zoals verwacht. Minimaal drie virtuele machines wordt aanbevolen, met Windows 7 (of hoger) geïnstalleerd.  

     Raadpleeg voor meer informatie dit [overzicht van Hyper-V](https://technet.microsoft.com/en-us/library/hh831531.aspx).  

-   **Beheerdersmachtigingen** voor al deze onderdelen vereist zijn.  

    -   Configuration Manager vereist een beheerder met lokale machtigingen in de Windows Server-omgeving  

    -   Active Directory is vereist voor een beheerder met machtigingen om het schema te wijzigen  

    -   Virtuele machines hebben lokale machtigingen nodig op de machines zelf  

Hoewel dit niet vereist voor dit lab, kunt u bekijken [ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md) voor meer informatie over vereisten voor het implementeren van System Center Configuration Manager. Raadpleeg de documentatie voor softwareversies behalve die hier wordt verwezen.  

Als u al deze onderdelen hebt geïnstalleerd, zijn er extra stappen die u nemen moet om uw Windows-omgeving configureren voor Configuration Manager:  

##  <a name="BKMK_LabADPrep"></a> Active Directory-inhoud voor de testomgeving voorbereiden  
 Voor deze testomgeving maakt u een beveiligingsgroep en vervolgens voegt u een domeingebruiker eraan toe.  

-   Beveiligingsgroep: **Evaluatie**  

    -   Groepsbereik: **Universele**  

    -   Groepstype: **Beveiliging**  

-   Domeingebruiker: **ConfigUser**  

     Onder normale omstandigheden zou u geen universele toegang verlenen aan alle gebruikers binnen uw omgeving. U doet dit met deze gebruiker om het online brengen van uw testomgeving te stroomlijnen.  

De volgende stappen vereist voor het inschakelen van Configuration Manager-clients naar query Active Directory Domain Services om sitebronnen te vinden worden in de volgende procedures weergegeven.  

##  <a name="BKMK_CreateSysMgmtLab"></a> De container voor systeembeheer maken  
 Configuration Manager wordt niet automatisch gemaakt de vereiste container voor Systeembeheer in Active Directory Domain Services wanneer het schema is uitgebreid. Daarom maakt u deze voor uw testomgeving. Voor deze stap moet u [ADSI Bewerken installeren](https://technet.microsoft.com/en-us/library/cc773354\(WS.10\).aspx#BKMK_InstallingADSIEdit).  

 Zorg dat u bent aangemeld als een account waaraan de machtiging **Alle onderliggende objecten maken** is verleend voor de container **Systeem** in Active Directory Domain Services.  

#### <a name="to-create-the-system-management-container"></a>De container voor systeembeheer maken:  

1.  Voer **ADSI Bewerken**uit en maak verbinding met het domein waaronder de siteserver zich bevindt.  

2.  Vouw **domein&lt;computer volledig gekwalificeerde domeinnaam\>**, vouw **< DN-naam\>**, met de rechtermuisknop op **CN = systeem**, klikt u op **nieuw**, en klik vervolgens op **Object**.  

3.  Selecteer, in het **Maak object** dialoogvenster, **Container**, en klik dan op **Volgende**.  

4.  Tik in het vak **Waarde** , typ **System Management**en klik vervolgens op **Volgende**.  

5.  Klik op **Beëindig** om de procedure te vervolledigen.  

##  <a name="BKMK_SetSecPermLab"></a> Beveiligingsrechten instellen voor de container voor systeembeheer  
 Verleen het computeraccount van de siteserver de machtigingen die nodig zijn voor het publiceren van site-informatie naar de container. Voor deze taak gebruikt u ook ADSI Bewerken.  

> [!IMPORTANT]  
>  Bevestig dat u met het domein van de siteserver bent verbonden vóór het begin van de volgende procedure.  

#### <a name="to-set-security-permissions-for-the-system-management-container"></a>Beveiligingsrechten instellen voor de container voor systeembeheer:  

1.  Vouw in het consolevenster de **site-serverdomein**, vouw **DC =&lt;server DN-naam\>**, en vouw vervolgens **CN = systeem**. Klik met de rechtermuisknop op **CN=Systeembeheer**en klik dan op **Eigenschappen**.  

2.  Klik in het dialoogvenster **CN=Eigenschappen voor systeembeheer** op het tabblad **Beveiliging** en klik vervolgens op **Toevoegen** om het computeraccount van de siteserver toe te voegen. Verleen aan het account de machtigingen **Volledig beheer** .  

3.  Klik op **Geavanceerd**, selecteer de computeraccount van de siteserver en klik vervolgens op **bewerken**.  

4.  Selecteer, in de lijst **Toepassen op** , de optie **Dit object en de onderliggende objecten**.  

5.  Klik op **OK** om de **ADSI Bewerken** -console te sluiten en de procedure te voltooien.  

     Raadpleeg voor meer inzicht in deze procedure [Active Directory-schema voor System Center Configuration Manager uitbreiden](../../core/plan-design/network/extend-the-active-directory-schema.md)  

##  <a name="BKMK_ExtADSchLab"></a> Het Active Directory-schema met behulp van extadsch.exe uitbreiden  
 U kunt Active Directory-schema voor dit lab wordt uitbreiden, omdat Hiermee kunt u alle Configuration Manager-functies en functionaliteit gebruiken met zo min mogelijk administratieve overhead. Het uitbreiden van het Active Directory-schema is een configuratie voor het hele forest, die één keer per forest wordt uitgevoerd. Permanente uitbreiding van het schema wijzigt de set klassen en kenmerken in de basisconfiguratie van Active Directory. Deze actie kan niet ongedaan worden gemaakt. Het schema uitbreidt, kunt Configuration Manager voor toegang tot onderdelen die voor de meest efficiënte binnen uw testomgeving zorgen.  

> [!IMPORTANT]  
>  Verzeker u ervan dat u bent aangemeld op de schemamaster-domeincontroller met een account dat lid is van de beveiligingsgroep **Schemabeheerders** . Elke poging tot het gebruik van alternatieve referenties zal mislukken.  

#### <a name="to-extend-the-active-directory-schema-using-extadschexe"></a>Het Active Directory-schema met behulp van extadsch.exe uitbreiden:  

1.  Maak een back-up van de systeemstatus van de schemamaster-domeincontroller. Raadpleeg voor meer informatie over back-ups van de master-domeincontroller [Windows Server Backup](https://technet.microsoft.com/en-us/library/cc770757.aspx)  

2.  Navigeer naar **\SMSSETUP\BIN\X64** op het installatiemedium.  

3.  Voer **extadsch.exe**uit.  

4.  Controleer of de schema-uitbreiding is geslaagd door het **extadsch.log** te controleren dat zich in de hoofdmap van het systeemstation bevindt.  

     Raadpleeg voor meer inzicht in deze procedure [Active Directory-schema voor System Center Configuration Manager uitbreiden](../../core/plan-design/network/extend-the-active-directory-schema.md).  

##  <a name="BKMK_OtherTasksLab"></a> Andere vereiste taken  
 U moet ook de volgende taken vóór de installatie voltooien.  

 **Een map maken voor het opslaan van alle downloads**  

 Er zijn tijdens deze oefening meerdere downloads vereist voor onderdelen van het installatiemedium. Voordat u begint met een installatieprocedure, kiest u een locatie waarbij u deze bestanden niet meer hoeft te verplaatsen totdat u de testomgeving weer buiten gebruik stelt. Eén map met afzonderlijke submappen voor het opslaan van deze downloads wordt aanbevolen.  

 **.NET installeren en Windows Communication Foundation activeren**  

 U moet eerst twee .NET Frameworks installeren: eerst .NET 3.5.1 en vervolgens .NET 4.5.2+. U moet ook Windows Communication Foundation (WCF) activeren. WCF is ontworpen om een beheerbare benadering te bieden voor gedistribueerde computing, brede interoperabiliteit en rechtstreekse ondersteuning voor service-oriëntatie. WCF vereenvoudigt ook de ontwikkeling van verbonden toepassingen via een servicegericht programmeermodel. Lees [Wat is Windows Communication Foundation?](https://technet.microsoft.com/en-us/subscriptions/ms731082\(v=vs.90\).aspx) voor meer inzicht in WCF.  

#### <a name="to-install-net-and-activate-windows-communication-foundation"></a>.NET installeren en Windows Communication Foundation activeren:  

1.  Open **Server Manager**en navigeer vervolgens naar **Beheren**. Klik op **Functies en onderdelen toevoegen** om de **Functies en onderdelen toevoegen Wizard.**te openen.  

2.  Bekijk de informatie in het paneel **Voordat u begint** en klik vervolgens op **Volgende**.  

3.  Selecteer **Installatie die op de functie of het onderdeel is gebaseerd**en klik vervolgens op **Volgende**.  

4.  Selecteer de server in de **Servergroep**en klik vervolgens op **Volgende**.  

5.  Controleer het paneel **Serverfuncties** en klik vervolgens op **Volgende**.  

6.  Voeg de volgende **Functies** toe door deze te selecteren in de lijst:  

    -   **.NET Framework 3.5-functies**  

        -   **.NET Framework 3.5 (inclusief .NET 2.0 en 3.0)**  

    -   **.NET Framework 4.5-functies**  

        -   **.NET Framework 4.5**  

        -   **ASP.NET 4.5**  

        -   **WCF-services**  

            -   **HTTP-activering**  

            -   **TCP-poort delen**  

7.  Controleer het scherm **Webserverrol (IIS)** en **Functieservices** en klik vervolgens op **Volgende**.  

8.  Controleer het scherm **Bevestiging** en klik vervolgens op **Volgende**.  

9. Klik op **Installeren** en controleer of de installatie is gelukt aan de hand van het deelvenster **Meldingen** van **Serverbeheer**.  

10. Nadat de basisinstallatie van .NET is voltooid, gaat u naar het [Microsoft Downloadcentrum](https://www.microsoft.com/en-us/download/details.aspx?id=42643) om het webinstallatieprogramma voor .NET Framework 4.5.2 op te halen. Klik op de knop **Downloaden** en kies vervolgens **Uitvoeren** voor het installatieprogramma. De vereiste onderdelen worden automatisch gedetecteerd en in de geselecteerde taal geïnstalleerd.  

Bekijk de volgende artikelen voor aanvullende informatie over de reden dat deze .NET Frameworks vereist zijn:  

-   [Versies en afhankelijkheden van .NET Framework](https://technet.microsoft.com/en-us/library/bb822049.aspx)  

-   [Overzicht toepassingscompatibiliteit .NET framework 4 RTM](https://technet.microsoft.com/en-us/library/dd889541.aspx)  

-   [Procedures: Upgrade van een ASP.NET-webtoepassing naar ASP.NET 4](https://technet.microsoft.com/en-us/library/dd483478\(VS.100\).aspx)  

-   [Veelgestelde vragen levenscyclusbeleid Microsoft .NET Framework-ondersteuning](https://support.microsoft.com/en-us/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update)  

-   [CLR uitgelicht - In-Process Side-by-Side](https://msdn.microsoft.com/en-us/magazine/ee819091.aspx)  

**BITS, IIS en RDC inschakelen**  

[Background Intelligent Transfer Service (BITS)](https://technet.microsoft.com/en-us/library/dn282296.aspx) wordt gebruikt voor toepassingen die asynchroon bestanden moeten overbrengen tussen een client en een server. Door de stroom van de overdrachten op de voor- en achtergrond te reguleren, houdt BITS het reactievermogen van andere netwerktoepassingen intact. Ook worden automatisch bestandsoverdrachten hervat als een overdrachtssessie wordt onderbroken.  

U installeert BITS voor deze testomgeving, omdat deze siteserver ook wordt gebruikt als beheerpunt.  

Internet Information Services (IIS) is een flexibele, schaalbare webserver die kan worden gebruikt voor het hosten van alles op het web. Wordt gebruikt door Configuration Manager voor een aantal sitesysteemrollen. Raadpleeg voor meer informatie over IIS [Websites voor sitesysteemservers in System Center Configuration Manager](../../core/plan-design/network/websites-for-site-system-servers.md).  

[Externe differentiële compressie (RDC)](https://technet.microsoft.com/en-us/library/cc754372.aspx) is een reeks API's dat toepassingen kunnen gebruiken om te bepalen of eventuele wijzigingen zijn aangebracht in een set bestanden. Via RDC kan de toepassing alleen de gewijzigde gedeelten van een bestand repliceren, waardoor netwerkverkeer tot een minimum wordt beperkt.  

#### <a name="to-enable-bits-iis-and-rdc-site-server-roles"></a>De siteserverrollen BITS, IIS en RDC inschakelen:  

1.  Open op de siteserver **Server Manager**. Ga naar **Beheren**. Klik op **Functies en onderdelen toevoegen** om de **Wizard Functies en onderdelen toevoegen**te openen.  

2.  Bekijk de informatie in het paneel **Voordat u begint** en klik vervolgens op **Volgende**.  

3.  Selecteer **Installatie die op de functie of het onderdeel is gebaseerd**en klik vervolgens op **Volgende**.  

4.  Selecteer de server in de **Servergroep**en klik vervolgens op **Volgende**.  

5.  Voeg de volgende **Serverfuncties** toe door deze te selecteren in de lijst:  

    -   **Webserver (IIS)**  

        -   **Veelvoorkomende HTTP-functies**  

            -   **Standaarddocument**  

            -   **Bladeren door mappen**  

            -   **HTTP-fouten**  

            -   **Statische inhoud**  

            -   **HTTP-omleiding**  

        -   **Status en diagnose**  

            -   **HTTP-logboekregistratie**  

            -   **Logboekregistratieprogramma's**  

            -   **Controle aanvragen**  

            -   **Tracering**  

    -   **Prestatie**  

        -   **Compressie van statische inhoud**  

        -   **Dynamische inhoudscompressie**  

    -   **Security**  

        -   **Filtering aanvragen**  

        -   **Basisverificatie**  

        -   **Verificatie van clientcertificaattoewijzing**  

        -   **IP- en domeinbeperkingen**  

        -   **URL-autorisatie**  

        -   **Windows-autorisatie**  

    -   **Toepassingsontwikkeling**  

        -   **.NET Extensibility 3.5**  

        -   **.NET Extensibility 4.5**  

        -   **ASP**  

        -   **ASP.NET 3.5**  

        -   **ASP.NET 4.5**  

        -   **ISAPI-extensies**  

        -   **ISAPI-filters**  

        -   **Insluiten vanaf server**  

    -   **FTP-server**  

        -   **FTP-service**  

    -   **Beheerhulpprogramma's**  

        -   **IIS-beheerconsole**  

        -   **Compatibiliteit met IIS 6-beheer**  

            -   **Compatibiliteit met IIS 6-metabase**  

            -   **IIS 6-beheerconsole**  

            -   **IIS 6-scripthulpprogramma's**  

            -   **Compatibiliteit met IIS 6 WMI**  

        -   **Scripts en hulpprogramma's voor IIS 6-beheer**  

        -   **Mangementservice**  

6.  Voeg de volgende **Functies** toe door deze te selecteren in de lijst:  

    -   **Background Intelligent Transfer Service (BITS)**  

          -   **IIS-serveruitbreiding**  

    -   **Externe-serverbeheerprogramma's**  

          -   **Beheerprogramma's voor onderdelen**  

          -   **Hulpprogramma's voor BITS-serveruitbreidingen**  

7.  Klik op **Installeren** en controleer of de installatie is gelukt aan de hand van het deelvenster **Meldingen** van **Serverbeheer**.  

IIS blokkeert standaard de toegang tot verschillende bestandsextensies en locaties voor HTTP- of HTTPS-communicatie. U moet aanvraagfiltering voor IIS op het distributiepunt configureren zodat deze bestanden kunnen worden gedistribueerd naar clientsystemen. Raadpleeg voor meer informatie [IIS-Aanvraagfiltering voor distributiepunten](../../core/plan-design/network/prepare-windows-servers.md#BKMK_IISFiltering).  

#### <a name="to-configure-iis-filtering-on-distribution-points"></a>IIS-filtering configureren voor distributiepunten:  

1.  Open **IIS Manager** en selecteer de naam van de server in de zijbalk. Hierdoor komt u in het scherm **Start** .  

2.  Controleer of **Functieweergave** is geselecteerd onder aan het scherm **Start** . Ga naar **IIS** en open **Filteren aanvragen**.  

3.  Klik in het deelvenster **Acties** op **Bestandsnaamextensie toestaan**.  

4.  Typ **.msi** in het dialoogvenster en klik op **OK**.  

##  <a name="BKMK_InstallCMLab"></a> Configuration Manager installeren  
U maakt een [bepalen wanneer een primaire site gebruiken](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md#BKMK_ChoosePriimary) clients rechtstreeks te beheren. Hierdoor kan uw testomgeving beheer ondersteunen voor [Site system scale](/sccm/core/plan-design/configs/size-and-scale-numbers) van mogelijke apparaten.  
Tijdens dit proces installeert u ook de Configuration Manager-console die wordt gebruikt om uw evaluatie-apparaten voortaan te beheren.  

Voordat u de installatie begint, start de [Prerequisite Checker](/sccm/core/servers/deploy/install/prerequisite-checker) op de server met Windows Server 2012 om te bevestigen dat alle instellingen correct zijn ingeschakeld.  

#### <a name="to-download-and-install-configuration-manager"></a>Configuration Manager downloaden en installeren:  

1.  Navigeer naar de [System Center-evaluaties](https://www.microsoft.com/evalcenter/evaluate-system-center-2012-configuration-manager-and-endpoint-protection) pagina voor het downloaden van de nieuwste evaluatieversie van System Center Configuration Manager.  

2.  Decomprimeer het downloadmedium naar de vooraf gedefinieerde locatie.  

3.  Volg de installatieprocedure zoals beschreven in [een site installeren met de Setup Wizard van System Center Configuration Manager](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites). In deze procedure geeft u de volgende invoer op:  

    |Stap in de procedure voor site-installatie|Selectie|  
    |-----------------------------------------|---------------|  
    |Stap 4: de pagina **Productcode**|Selecteer **Evaluatie**.|  
    |Stap 7:  **Vereiste Downloads**|Selecteer **Vereiste bestanden downloaden** en geef de vooraf gedefinieerde locatie op.|  
    |Stap 10: **Site- en installatie-instellingen**|-   **Sitecode:LAB**<br />-   **Sitenaam:Evaluation**<br />-   **Installatiemap:** geef de vooraf gedefinieerde locatie op.|  
    |Stap 11: **Primaire Site-installatie**|Selecteer **De primaire site installeren als een zelfstandige site**en klik vervolgens op **Volgende**.|  
    |Stap 12: **Database-installatie**|-   **SQL Server-naam (FQDN):** voer hier de FQDN in.<br />-   **Exemplaarnaam:** laat dit leeg, omdat u het standaardexemplaar van SQL gebruikt dat u eerder hebt geïnstalleerd.<br />-   **Service Broker-poort:** laat de standaardpoort 4022 staan.|  
    |Stap 13: **Database-installatie**|Laat deze instellingen als standaard.|  
    |Step 14: **SMS-Provider**|Laat deze instellingen als standaard.|  
    |Stap 15: **Communicatie-instellingen voor client**|Bevestig dat **Alle sitesysteemrollen accepteren alleen HTTPS-communicatie van clients** niet is ingeschakeld.|  
    |Stap 16: **Sitesysteemrollen**|Voer de FQDN-naam in en bevestig dat **Alle sitesysteemrollen accepteren alleen HTTPS-communicatie van clients** nog steeds is uitgeschakeld.|  

##  <a name="BKMK_EnablePubLab"></a> Publicatie inschakelen voor de Configuration Manager-site  
Elke Configuration Manager-site publiceert haar eigen site-specifieke informatie naar de Systeembeheer-container binnen haar domeinpartitie in het Active Directory-schema. Bidirectionele kanalen voor communicatie tussen Active Directory en Configuration Manager moeten worden geopend voor het afhandelen van dit verkeer. U schakelt bovendien ook forestdetectie in om bepaalde onderdelen van uw Active Directory en de netwerkinfrastructuur te bepalen.  

#### <a name="to-configure-active-directory-forests-for-publishing"></a>Handel als volgt om Active Directory-forests voor publicatie te configureren:  

1.  Klik in de linkerbenedenhoek van de Configuration Manager-console op **beheer**.  

2.  Vouw in de werkruimte **Beheer** de optie **Hiërarchieconfiguratie**uit en klik vervolgens op **Detectiemethoden**.  

3.  Selecteer **Detectie van Active Directory-forests** en klik op **Eigenschappen**.  

4.  Selecteer in het dialoogvenster **Eigenschappen** de optie **Active Directory-forestdetectie inschakelen**. Als deze optie actief is, selecteert u **Automatisch Active Directory-sitegrenzen maken na detectie**. Er wordt een dialoogvenster weergegeven waarin wordt aangegeven **Wilt u zo snel mogelijk een volledige detectie uitvoeren?** Klik op **Ja**.  

5.  In de groep **Detectiemethode** aan de bovenkant van het scherm klikt u op **Forestdetectie nu uitvoeren**en vervolgens gaat u naar **Active Directory-forests** in de zijbalk. Uw Active Directory-forest moet worden weergegeven in de lijst met gedetecteerde forests.  

6.  Navigeer naar de bovenkant van het scherm op het tabblad **Algemeen** .  

7.  Vouw in de werkruimte **Beheer** de optie **Hiërarchieconfiguratie**uit en klik vervolgens op **Active Directory-forests**.  

#### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-your-active-directory-forest"></a>Een Configuration Manager-site naar site-informatie publiceren naar Active Directory-forest inschakelen:  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  U configureert een nieuw forest dat nog niet is gedetecteerd.  

3.  Klik op **Active Directory-forests** in de werkruimte **Beheer**.  

4.  Op het tabblad **Publiceren** van de site-eigenschappen selecteert u het verbonden forest en klikt u vervolgens op **Ok** om de configuratie op te slaan.
