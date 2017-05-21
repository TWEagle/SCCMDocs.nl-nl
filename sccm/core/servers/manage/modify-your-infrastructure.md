---
title: Wijzigen van de infrastructuur | Microsoft-documenten
description: "Informatie over het aanbrengen van wijzigingen of acties die invloed hebben op de Configuration Manager-infrastructuur die u hebt geïmplementeerd."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7975dc8-46ab-4dae-86b6-dc3e3cf3b2f0
caps.latest.revision: 19
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 52d2e088b8db3c2e9a0af640ca3db72b9fd7af60
ms.openlocfilehash: a5228c4984347be4b115bfa5563791fa2fb7319c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="modify-your-system-center-configuration-manager-infrastructure"></a>Uw infrastructuur van System Center Configuration Manager aanpassen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u een of meer sites hebt geïnstalleerd, moet u mogelijk configuraties wijzigen of acties ondernemen die van invloed zijn op de infrastructuur die u hebt geïmplementeerd.  


##  <a name="BKMK_ManageSMSprovider"></a>De SMS-Provider beheren  
 De SMS-Provider (een DLL-bestand: smsprov.dll) verleent het punt van beheercontact voor een of meer Configuration Manager-consoles. Als u meerdere SMS-providers installeert, kunt u redundantie verlenen aan contactpunten om u site en hiërarchie te beheren.  

 U kunt het installatieprogramma opnieuw uitvoeren op elke site Configuration Manager:  

-   Voeg een extra exemplaar van de SMS-Provider (elke extra exemplaar van de SMS-Provider moet zich op een afzonderlijke computer)  

-   Een exemplaar van de SMS-Provider verwijderen (als u wilt verwijderen van de laatste SMS-Provider voor een site, moet u de site verwijderen)  

 U kunt de installatie of verwijdering van de SMS-provider bewaken via het bestand **ConfigMgrSetup.log** in de hoofdmap van de siteserver waarop u het installatieprogramma uitvoert.  

 Lees de informatie van [Plannen voor de SMS-provider voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md) door voordat u de SMS-provider op een site aanpast.  

#### <a name="to-manage-the-sms-provider-configuration-for-a-site"></a>De configuratie van de SMS-provider voor een site beheren  

1.  Voer **installatie van Configuration Manager** van  **&lt;installatiemap Configuration Manager-site\>\BIN\X64\setup.exe**.  

2.  Selecteer op de pagina **Aan de slag** de optie **Siteonderhoud uitvoeren of deze site resetten** en klik op **Volgende**.  

3.  Op de pagina **Siteonderhoud** selecteert u **Configuratie van de SMS-provider wijzigen** en klikt u op **Volgende**.  

4.  Selecteer op de pagina **SMS-providers beheren** een van de volgende opties en voltooi de wizard met behulp van een van de volgende opties:  

    -   Ga als volgt te werk om een extra SMS-provider aan deze site toe te voegen:  

         Selecteer **Een nieuwe SMS-provider toevoegen**, geef de FQDN op voor de computer die als host gaat dienen voor de SMS-provider (en momenteel niet als host voor de SMS-provider dient) en klik op **Volgende**.  

    -   Ga als volgt te werk om een SMS-provider van een server te verwijderen:  

         Selecteer **De opgegeven SMS-provider verwijderen**, selecteer de naam van de computer waarvan u de SMS-provider wilt verwijderen, klik op **Volgende** en bevestig de actie.  

        > [!TIP]  
        >  Als u de SMS-provider tussen twee computers wilt verwijderen, moet u de SMS-provider op de nieuwe computer installeren en van de oorspronkelijke locatie verwijderen. Er is geen specifieke optie om de SMS-provider in één keer te verplaatsen tussen computers.  

 Na het uitvoeren van de installatiewizard is de configuratie van de SMS-provider voltooid. U kunt op het tabblad **Algemeen** in het dialoogvenster **Eigenschappen** van de site de computers controleren die een SMS-provider hebben geïnstalleerd voor een site.  

##  <a name="bkmk_Console"></a>De Configuration Manager-console beheren  
 Hier volgen de taken die u kunt voor het beheren van de Configuration Manager-console:  

-   **Wijzig de taal die wordt weergegeven in de Configuration Manager-console** - wijzigen van de geïnstalleerde talen Zie [consoletaal Configuration Manager beheren](#BKMK_ManageConsoleLanguages) in dit onderwerp.  

-   **Aanvullende-consoles installeren** : als u wilt installeren van extra consoles, Zie [installeert System Center Configuration Manager-consoles](/sccm/core/servers/deploy/install/install-consoles).  

-   **Configureren van DCOM** - configureren van DCOM-machtigingen om in te schakelen consoles die extern van de siteserver verbinding kan maken zijn, Zie [configureren van DCOM-machtigingen voor externe Configuration Manager-consoles](#BKMK_ConfigDCOMforRemoteConsole) in dit onderwerp.  

-   **Wijzig de machtigingen voor opleggen aan wat gebruikers met beheerdersrechten kunnen zien in de console** - beheerdersrechten toestemming hebben, welke beperken welke gebruikers kunnen zien en doen in de console, Zie wijzigen [het beheerbereik van een gebruiker met beheerdersrechten wijzigen](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_ModAdminUser).     

###  <a name="BKMK_ManageConsoleLanguages"></a>Consoletaal van Configuration Manager-beheren  
 Tijdens de installatie van site-server, worden de installatiebestanden van de Configuration Manager-console en ondersteunde talenpakketten voor de site gekopieerd naar de  **&lt;Configmgrinstallatiepad\>\Tools\ConsoleSetup** submap op de siteserver.  

-   Wanneer u de installatie van de Configuration Manager-console vanuit deze map op de siteserver start, de Configuration Manager-console en ondersteunde taalpakketbestanden naar de computer gekopieerd  

-   Wanneer een taalpakket beschikbaar voor de huidige taalinstelling op de computer is, de Configuration Manager-console geopend in die taal  

-   Als het gekoppelde taalpakket niet beschikbaar voor de Configuration Manager-console is, wordt de console geopend in het Engels  

Denk bijvoorbeeld een scenario waarin u de Configuration Manager-console installeren via een siteserver die Engels, Duits en Frans ondersteunt. Als u de Configuration Manager-console op een computer waarop de taalinstelling is ingesteld op Frans ingesteld opent, wordt de console geopend in het Frans. Als u de Configuration Manager-console op een computer met een taalinstelling is ingesteld op Japans opent, wordt de console geopend in het Engels omdat het Japanse taalpakket niet beschikbaar is.  

 Telkens wanneer die de Configuration Manager-console wordt geopend, het bepaalt welke instellingen van de taalinstelling is ingesteld voor de computer, wordt gecontroleerd of het bijbehorende taalpakket beschikbaar is voor de Configuration Manager-console en wordt de console geopend met het toepasselijke taalpakket. Wanneer u de Configuration Manager-console openen in het Engels ongeacht welke taalinstelling op de computer zijn geconfigureerd, moet u handmatig verwijderen of wijzig de naam van het taalpakket op de computer.  

 Gebruik de volgende procedures in de Configuration Manager-console starten in het Engels ongeacht de geconfigureerde landinstelling op de computer.  

##### <a name="to-install-an-english-only-version-of-the-configuration-manager-console-on-computers"></a>Een alleen-Engelse versie van de Configuration Manager-console installeren op computers  

1.  Blader in Windows Verkenner naar  **&lt;Configmgrinstallatiepad\>\Tools\ConsoleSetup\LanguagePack**  

2.  Wijzig de namen van de **MSP**- en **MST**-bestanden. U kunt **&lt;bestandsnaam\>.MSP** bijvoorbeeld wijzigen in **&lt;bestandsnaam\>.MSP.disabled**.  

3.  Installeer de Configuration Manager-console op de computer.  

    > [!IMPORTANT]  
    >  Wanneer er nieuwe servertalen voor de siteserver worden geconfigureerd, worden de MSP- en MST-bestanden opnieuw naar de **LanguagePack** map en u moet deze procedure voor het installeren van nieuwe Configuration Manager-consoles in alleen in het Engels herhalen.  

##### <a name="to-temporarily-disable-a-console-language-on-an-existing-configuration-manager-console-installation"></a>Een consoletaal voor een bestaande installatie van de Configuration Manager-console tijdelijk uitschakelen  

1.  Op de computer waarop de Configuration Manager-console wordt uitgevoerd, sluit u de Configuration Manager-console.  

2.  Blader in Windows Verkenner naar &lt; *ConsoleInstallationPath*> \Bin\ op de consolecomputer Configuration Manager-.  

3.  Wijzig de naam van de toepasselijke taalmap voor de taal die op de computer is geconfigureerd. Als de taalinstellingen voor de computer zijn ingesteld op Duits, kunt de naam van de map **de** wijzigen in **de.disabled**.  

4.  Om de Configuration Manager-console opent in de taal die is geconfigureerd voor de computer, de naam van de map in de oorspronkelijke naam. Wijzig bijvoorbeeld de naam **de.disabled** in **de**.  

##  <a name="BKMK_ConfigDCOMforRemoteConsole"></a>Configureren van DCOM-machtigingen voor externe Configuration Manager-consoles  
 Het gebruikersaccount dat de Configuration Manager-console wordt uitgevoerd is machtiging nodig voor toegang tot de sitedatabase met behulp van de SMS-Provider. Een gebruiker met beheerdersrechten die gebruik maakt van een externe Configuration Manager-console ook vereist echter **extern activeren** DCOM-machtigingen op:  

-   De siteservercomputer  

-   Elke computer waarop een exemplaar van de SMS-provider wordt gehost  

 De beveiligingsgroep **SMS-beheerders** verleent toegang tot de SMS-provider en kan ook worden gebruikt om de vereiste DCOM-machtigingen te verlenen. (Deze groep is lokaal op de computer wanneer de SMS-Provider wordt uitgevoerd op een lidserver en een lokale domeingroep is als de SMS-Provider wordt uitgevoerd op een domeincontroller.)  

> [!IMPORTANT]  
>  De Configuration Manager-console gebruikt Windows Management Instrumentation (WMI) voor verbinding met de SMS-Provider en WMI gebruikt intern DCOM. Configuration Manager vereist daarom machtigingen om te activeren van een DCOM-server op de computer van de SMS-Provider als de Configuration Manager-console wordt uitgevoerd op een andere computer dan de computer van de SMS-Provider. Standaard wordt extern activeren alleen verleend aan de leden van de groep Administrators. Als u de SMS-beheerdersgroep machtiging verleent voor extern activeren, zou een lid van deze groep DCOM-aanvallen kunnen uitvoeren op de computer van de SMS-provider. Deze configuratie verhoogt ook de kwetsbaarheid van de computer. Controleer de leden van de SMS-beheerdersgroep zorgvuldig om deze dreiging te verminderen.  

 Gebruik de volgende procedure voor het configureren van elke centrale beheersite, primaire siteserver en iedere computer waarop de SMS-Provider is geïnstalleerd externe Configuration Manager om consoletoegang te verlenen voor gebruikers met beheerdersrechten.  

#### <a name="to-configure-dcom-permissions-for-remote-configuration-manager-console-connections"></a>DCOM-machtigingen configureren voor externe verbindingen van de Configuration Manager-console  

1.  Open **Component Services** door **Dcomcnfg.exe** uit te voeren.  

2.  In **Component Services**, klikt u op **consolebasis** >  **Component Services** > **Computers**, en klik vervolgens op **Mijn Computer**. Klik in het menu **Actie** op **Eigenschappen**.  

3.  Klik in het dialoogvenster **Mijn computereigenschappen** op het tabblad **COM-beveiliging**, in de sectie **Machtigingen voor starten en activeren**, op **Beperkingen bewerken**.  

4.  Klik in het dialoogvenster **Machtigingen voor starten en activeren** op **Toevoegen**.  

5.  In de **gebruiker selecteren, Computers, serviceaccounts of groepen** het dialoogvenster de **Geef de objectnamen op (voorbeelden)** in het vak **SMS Admins**, en klik vervolgens op **OK**.  

    > [!NOTE]  
    >  U moet mogelijk de instelling voor **Vanaf deze locatie** wijzigen om de SMS-beheerdersgroep te lokaliseren. Deze groep is lokaal op de computer wanneer de SMS-provider wordt uitgevoerd op een lidserver en is een domein-lokale groep wanneer de SMS-provider wordt uitgevoerd op een domeincontroller.  

6.  Selecteer in de sectie **Machtigingen voor SMS Admins** het selectievakje **Extern activeren** om extern activeren toe te staan.  

7.  Klik op **OK** en nogmaals op **OK**. Sluit vervolgens **Computerbeheer**. Uw computer is nu geconfigureerd voor externe Configuration Manager consoletoegang tot leden van de SMS Admins-groep.  

 Herhaal deze procedure op elke computer SMS-Provider die externe Configuration Manager-consoles kan ondersteunen.  

##  <a name="bkmk_dbconfig"></a>Configuratie van de sitedatabase wijzigen  
 Nadat u een site geïnstalleerd hebt, kunt u de configuratie van de sitedatabase en sitedatabaseserver wijzigen door het installatieprogramma uit te voeren op een centrale beheersiteserver of primaire siteserver. U kunt de sitedatabase verplaatsen naar een nieuw exemplaar van SQL Server op dezelfde computer, of naar een andere computer die een ondersteunde versie van SQL Server uitvoert. Deze en gerelateerde wijzigingen worden niet ondersteund voor de databaseconfiguratie op secundaire sites.  

 Zie [Support policy for manual database changes in a Configuration Manager environment](https://support.microsoft.com/kb/3106512) (Ondersteungingsbeleid voor handmatig databasewijzigingen een Configuration Manager-omgeving) voor meer informatie over de beperkingen van de ondersteuning.  

> [!NOTE]  
>  Wanneer u de databaseconfiguratie voor een site wijzigt, wordt Configuration Manager wordt opnieuw opgestart of Configuration Manager-services wordt opnieuw geïnstalleerd op de siteserver en externe sitesysteemservers die met de database communiceren.  

**Als u de databaseconfiguratie wilt wijzigen**, dient u het installatieprogramma op de siteserver uit te voeren en de optie **Siteonderhoud uitvoeren of deze site resetten selecteren** te selecteren. Selecteer volgens de optie **SQL Server-configuratie wijzigen**. U kunt de volgende configuraties van de sitedatabase wijzigen:  

-   De Windows-server die als host fungeert voor de database.  

-   Het exemplaar van SQL Server dat wordt gebruikt op een server die de SQL Server-database host.  

-   De naam van de database.  

-   SQL Server-poort wordt gebruikt door Configuration Manager  

-   SQL Server Service Broker-poort wordt gebruikt door Configuration Manager  

**Als u de sitedatabase verplaatst, moet u het volgende configureren:**  

-   **Toegang configureren:** Wanneer u de sitedatabase naar een nieuwe computer verplaatst, Voeg het computeraccount van de siteserver verzonden om de **lokale beheerders** groep op de computer waarop SQL Server uitvoert. Als u een SQL Server-cluster voor de sitedatabase gebruikt, dient u de computeraccount toe te voegen aan de groep **Lokale beheerders** van elke Windows Server-clusterknooppuntcomputer.  

-   **Integratie van common language runtime (CLR) inschakelen:**  Wanneer u de database naar een nieuw exemplaar van SQL Server of naar een nieuwe SQL Server-computer verplaatsen, moet u de integratie van common language runtime (CLR) inschakelen. Als CLR inschakelen, gebruikt u **SQL Server Management Studio** voor verbinding met het exemplaar van SQL Server die als host fungeert voor de sitedatabase en voer de volgende opgeslagen procedure als een query: **sp_configure 'clr enabled', 1; opnieuw configureren**.  
-  **Zorg ervoor dat de nieuwe SQL Server toegang heeft tot de back-uplocatie:** Als u een UNC voor het opslaan van uw site-databasebackup na het verplaatsen van de database naar een nieuwe server, met inbegrip van een SQL Server AlwaysOn-beschikbaarheidsgroep verplaatsen of een SQL Server-cluster gebruikt, controleert het computeraccount van de nieuwe SQL Server **schrijven** machtigingen voor de UNC-locatie.  


> [!IMPORTANT]  
>  Voor dat u een database verplaatst die een of meerdere databasereplica's voor beheerpunten heeft, moet u de databasereplica's eerst verwijderen. Nadat u de database verplaatst hebt, kunt u databasereplica's opnieuw configureren. Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md) voor meer informatie.  

##  <a name="bkmk_SPN"></a>De SPN voor de Sitedatabaseserver beheren  
U kunt het account kiezen waarmee SQL-services voor de sitedatabase worden uitgevoerd:  

-   Wanneer de services worden uitgevoerd met het systeemaccount van de computer, wordt de SPN automatisch voor u geregistreerd.  

-   Wanneer de services worden uitgevoerd met een lokale domeingebruikersaccount, moet u de SPN handmatig registreren om ervoor te zorgen dat SQL-clients en andere sitesystemen een Kerberos-verificatie kunnen uitvoeren. Zonder Kerberos-verificatie, is het mogelijk dat de communicatie met de database mislukt.  

In de SQL Server-documentatie vindt u meer informatie over het [handmatig registreren van de SPN](https://technet.microsoft.com/library/ms191153\(v=sql.120\).aspx) en aanvullende achtergrondinformatie over SPN's en Kerberos-verbindingen.  

> [!IMPORTANT]  
>  -   Wanneer u een SPN voor een geclusterde SQL Server maakt, moet u de virtuele naam van de SQL Server-Cluster opgeven als de SQL Server-computernaam.  
> -   De opdracht om een SPN voor een SQL Server-benoemd exemplaar te registreren is dezelfde als diegene die u gebruikt wanneer u een SPN voor een standaard exemplaar registreert, behalve dat het poortnummer moet overeenstemmen met de poort die wordt gebruikt door het benoemde exemplaar.  

U kunt een SPN voor de SQL Server-serviceaccount van de sitedatabaseserver registreren met behulp van het **Setspn**-hulpprogramma. U moet het Setspn-hulpprogramma op een computer uitvoeren die zich in het domein van SQL Server bevindt, en het moet domeinbeheerdersreferenties gebruiken om uit te voeren.  

 Gebruik de volgende procedures als voorbeelden van hoe u de SPN voor de SQL Server-serviceaccount moet beheren die het Setspn-hulpprogramma op Windows Server 2008 R2 gebruikt. Zie [Setspn Overview (Setspn-overzicht)](http://go.microsoft.com/fwlink/p/?LinkId=226343) of gelijkaardige documentatie die specifiek is voor uw besturingssysteem voor specifieke hulp over Setspn.  

> [!NOTE]  
>  De volgende procedures verwijzen naar het opdrachtregelhulpprogramma Setspn. Het opdrachtregelhulpprogramma Setspn is opgenomen wanneer u Windows Server 2003-ondersteuningsprogramma's vanaf de product-CD of van installeren de [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=100114). Zie [Install Windows Support Tools](http://go.microsoft.com/fwlink/p/?LinkId=62270) (Windows-ondersteuningsprogramma's installeren) voor meer informatie over de installatie van Windows-ondersteuningsprogramma's van de product-cd.  

#### <a name="to-manually-create-a-domain-user-service-principal-name-spn-for-the-sql-server-service-account"></a>Een domeingebruiker Service Principal Name (SPN) voor de SQL Server-serviceaccount handmatig maken  

1.  Klik in het menu **Start** op **Uitvoeren** en voer vervolgens **cmd** in het dialoogvenster Uitvoeren in.  

2.  Blader op de opdrachtregel naar de installatiedirectory van de Windows Server-ondersteuningsprogramma's. Standaard deze hulpprogramma's bevinden zich in de **C:\Program Files\Support Tools** directory.  

3.  Voer een geldige opdracht in om de SPN te maken. Als u de SPN maakt, kunt u de NetBIOS-naam of de volledig gekwalificeerde domeinnaam (FQDN) van de computer met SQL Server. U moet echter een SPN maken voor zowel de NetBIOS-naam als de FQDN.  

    > [!IMPORTANT]  
    >  Wanneer u een SPN voor een geclusterde SQL Server maakt, moet u de virtuele naam van de SQL Server-Cluster opgeven als de SQL Server-computernaam.  

    -   Voor het maken van een SPN voor de NetBIOS-naam van de SQL Server-computer, typt u de volgende opdracht: **setspn - A MSSQLSvc /&lt;SQL Server-computernaam\>: 1433 &lt;domein\account >**  

    -   Voor het maken van een SPN voor de FQDN-naam van de SQL Server-computer, typt u de volgende opdracht: **setspn - A MSSQLSvc /&lt;SQL Server-FQDN\>: 1433 &lt;domein\account >**  

    > [!NOTE]  
    >  De opdracht om een SPN voor een SQL Server-benoemd exemplaar te registreren is dezelfde als diegene die u gebruikt wanneer u een SPN voor een standaard exemplaar registreert, behalve dat het poortnummer moet overeenstemmen met de poort die wordt gebruikt door het benoemde exemplaar.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-by-using-the-setspn-command"></a>Controleren of de SPN van de domeingebruiker correct is geregistreerd met behulp van de Setspn-opdracht.  

1.  Klik in het menu **Start** op **Uitvoeren** en voer vervolgens **cmd** in het dialoogvenster **Uitvoeren** in.  

2.  Voer de volgende opdracht uit vanaf de opdrachtregel: **setspn -L &lt;domain\SQL serviceaccount >**.  

3.  Bekijk de geregistreerde **ServicePrincipalName** om ervoor te zorgen dat er een geldige SPN is gemaakt voor de SQL Server.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-when-using-the-adsiedit-mmc-console"></a>Controleren of de SPN van de domeingebruiker correct is geregistreerd bij gebruik van de ADSIEdit MMC-console.  

1.  Klik in het menu **Start** op **Uitvoeren** en voer vervolgens **adsiedit.msc** in om de ADSIEdit MMC-console te starten.  

2.  Indien nodig, moet u een verbinding maken met het domein van de siteserver.  

3.  Vouw in het consolevenster domein van de siteserver uit, vouw **DC =&lt;server DN-naam\>**, vouw **CN = Users**, met de rechtermuisknop op **CN =&lt;Serviceaccountgebruiker\>**, en klik vervolgens op **eigenschappen**.  

4.  In de **CN =&lt;Serviceaccountgebruiker\> eigenschappen** in het dialoogvenster controleren de **servicePrincipalName** waarde om ervoor te zorgen dat een geldige SPN is gemaakt en gekoppeld met de juiste SQL Server-computer.  

#### <a name="to-change-the-sql-server-service-account-from-local-system-to-a-domain-user-account"></a>De SQL Server-serviceaccount van lokaal systeem naar een domeingebruikersaccount wijzigen  

1.  Maak een gebruikersaccount van het domein of lokale systeem of selecteer deze account die u wilt gebruiken als de SQL Server-serviceaccount.  

2.  Open **SQL Server Configuration Manager**.  

3.  Klik op **SQL Server-Services**, en dubbelklik vervolgens op **SQL Server&lt;EXEMPLAARNAAM\>**.  

4.  Selecteer op het tabblad **Aanmelden** de optie **Dit account** en voer vervolgens de gebruikersnaam en het wachtwoord in voor de domeingebruikersaccount die is gemaakt in stap 1, of klik op **Bladeren** om de gebruikersaccount in Active Directory Domain Services te zoeken, en klik vervolgens op **Toepassen**.  

5.  Klik op **Ja** in het dialoogvenster **Accountwijziging bevestigen** om de wijziging van de serviceaccount te bevestigen en de SQL Server-Service opnieuw te starten.  

6.  Klik op **OK** nadat de serviceaccount is gewijzigd.  

##  <a name="bkmk_reset"></a>Een sitereset uitvoeren  
 Wanneer een sitereset voor een centrale beheersite of primaire site wordt uitgevoerd:  

-   De Configuration Manager bestands- en registermachtigingen standaardmachtigingen wordt opnieuw toegepast  

-   Alle siteonderdelen en sitesysteemrollen worden opnieuw op de site geïnstalleerd  

Secundaire sites ondersteunen een sitereset niet.  

Een sitereset kan desgewenst handmatig worden uitgevoerd, maar ook automatisch nadat u de configuratie van de site hebt gewijzigd.  

Bijvoorbeeld, als er een wijziging aan de accounts die worden gebruikt door Configuration Manager-onderdelen is, u moet rekening houden met een site handmatig resetten zodat de site-onderdelen bijwerken voor het gebruik van de nieuwe accountdetails. Echter, als u de client of servertalen op een site wijzigt, Configuration Manager automatisch reset een site omdat de reset vereist is voordat een site deze wijziging kan gebruiken.  

> [!NOTE]  
>  Een sitereset niet opnieuw ingesteld toegangsmachtigingen voor niet - Configuration Manager-objecten.  

Tijdens een sitereset:  

1.  Setup stopt en start u de **SMS_SITE_COMPONENT_MANAGER** -service en de threadonderdelen van de **SMS_EXECUTIVE** service.  

2.  Verwijdert het installatieprogramma, en vervolgens opnieuw maakt, het sitesysteem en de **SMS Executive** onderdeel op de lokale computer en op externe sitesysteemcomputers.  

3.  Setup wordt opnieuw opgestart de **SMS_SITE_COMPONENT_MANAGER** installeert van deze service-service, de **SMS Executive** en de **SMS_SQL_MONITOR** services.  

Bovendien herstelt een sitereset de volgende objecten:  

-   De **SMS**- of **NAL**-registersleutels, en enige standaard subsleutels onder deze sleutels.  

-   De bestandsmapstructuur van Configuration Manager en standaardbestanden of submappen in deze bestandsmapstructuur.  

**Vereisten voor het uitvoeren van een sitereset**  

De account waarmee u een sitereset kunt uitvoeren, moet de volgende machtigingen hebben:  

-   De account waarmee u een sitereset kunt uitvoeren, moet de volgende machtigingen hebben:  

    -   **Centrale beheersite**: De account waarmee u een sitereset uitvoert op deze site moet een lokale beheerder op de centrale beheersiteserver en moet over bevoegdheden beschikken die gelijkwaardig zijn aan de **volledige beheerder** op rollen gebaseerde beheerbeveiligingsrol.  

    -   **Primaire site**: Het account waarmee u een sitereset uitvoert op deze site moet een lokale beheerder op de primaire siteserver en moet over bevoegdheden beschikken die gelijkwaardig zijn aan de **volledige beheerder** op rollen gebaseerde beheerbeveiligingsrol. Als de primaire site zich in een hiërarchie bevindt met een centrale beheersite, moet deze account tevens een lokale beheerder zijn op de centrale beheersiteserver.  

**Beperkingen voor een site opnieuw instellen**
  -    Vanaf versie 1602, u een sitereset om te wijzigen van de Server niet gebruiken of taalpakketten voor clients die op sties geïnstalleerd zolang de hiërarchie is geconfigureerd voor ondersteuning van [clientupgrades te testen in een pre-productieverzameling](/sccm/core/clients/manage/upgrade/test-client-upgrades).

#### <a name="to-perform-a-site-reset"></a>Een sitereset uitvoeren  

1.  Voer **installatie van Configuration Manager** van  **&lt;installatiemap Configuration Manager-site\>\BIN\X64\setup.exe**.  

    > [!TIP]  
    >  U kunt ook uitvoeren met een sitereset uitvoeren door de Configuration Manager Setup starten op de **Start** menu van de site server-computer of vanuit de bronmedia van Configuration Manager.  

2.  Selecteer op de pagina **Aan de slag** de optie **Siteonderhoud uitvoeren of deze site resetten**en klik op **Volgende**.  

3.  Selecteer op de pagina **Siteonderhoud** de optie **Site resetten zonder configuratiewijzigingen** en klik op **Volgende**.  

4.  Klik op **Ja** om met de sitereset te beginnen.  

Wanneer de sitereset is voltooid, klikt u op **Sluiten** om deze procedure te voltooien.  

##  <a name="bkmk_sitelang"></a>Taalpakketten op een site beheren  
Nadat een site is geïnstalleerd, kunt u de gebruikte taalpakketten voor de server en client wijzigen:  

**Servertaalpakketten:**  

-   **Van toepassing op:**  

     Configuration Manager-installaties  

     Nieuwe installaties van toepasselijke sitesysteemrollen  

-   **Details:**  

     Na het bijwerken van servertaalpakketten op een site, kunt u ondersteuning voor de taalpakketten toevoegen aan de Configuration Manager-consoles.  

     U voegt ondersteuning voor een servertaalpakket voor een Configuration Manager-console, moet u de Configuration Manager-console uit de **ConsoleSetup** map op een siteserver met het taalpakket dat u wilt gebruiken. Als de Configuration Manager-console al is geïnstalleerd, moet u deze zodat de nieuwe installatie om te identificeren van de huidige lijst van ondersteunde taalpakketten eerst verwijderen.  

**Client-taalpakketten:**  

-   **Van toepassing op:**  

     Wanneer er wijzigingen worden aangebracht in de clienttaalpakketten, worden de bronbestanden van de clientinstallatie bijgewerkt, zodat de nieuwe clientinstallaties en -upgrades ondersteuning bieden voor de bijgewerkte lijst met clienttalen.  

-   **Details:**  

     U moet na het bijwerken van de clienttaalpakketten op een site elke client installeren die de taalpakketten gaat gebruiken, door gebruik te maken van bronbestanden met de clienttaalpakketten.  

Zie voor meer informatie over de talen van de client en server die ondersteund worden door Configuration Manager [taalpakketten in System Center Configuration Manager](../../../core/servers/deploy/install/language-packs.md)  

#### <a name="to-modify-the-language-packs-that-are-supported-at-a-site"></a>De taalpakketten aanpassen die op een site worden ondersteund  

1.  Op de siteserver Configuration Manager Setup uitvoeren via  **&lt;installatiemap Configuration Manager-site\>\BIN\X64\setup.exe.**  

2.  Selecteer op de pagina **Aan de slag** de optie **Siteonderhoud uitvoeren of deze site resetten** en klik op **Volgende**.  

3.  Selecteer op de pagina **Siteonderhoud** de optie **Taalconfiguratie aanpassen** en klik daarna op **Volgende**.  

4.  Selecteer op de pagina **Vereisten downloads** het item **Vereiste bestanden downloaden** om updates voor taalpakketten te downloaden, of selecteer **Eerder gedownloade bestanden gebruiken** om eerder gedownloade bestanden te downloaden met de taalpakketten die u aan de site wilt toevoegen. Klik op **Volgende** om de bestanden te valideren en ga door.  

5.  Schakel op de pagina **Selectie van servertaal** het selectievakje voor servertalen in die door de site worden ondersteund, en klik daarna op **Volgende**.  

6.  Schakel op de pagina **Selectie van clienttaal** het selectievakje voor clienttalen in die door de site worden ondersteund, en klik daarna op **Volgende**.  

7.  Klik op **Volgende** om taalondersteuning op de site aan te passen.  

    > [!NOTE]  
    >  Configuration Manager initieert een site opnieuw ingesteld dat alle sitesysteemrollen op de site opnieuw geïnstalleerd.  

8.  Klik op **Sluiten** om deze procedure te voltooien.  

##  <a name="BKMK_ModDBAlert"></a>De waarschuwingsdrempel van de database-server wijzigen  
 Configuration Manager genereert standaard waarschuwingen wanneer de vrije schijfruimte op een databaseserver gering. De standaardwaarden zijn zo ingesteld dat er een waarschuwing wordt gegenereerd wanneer er 10 GB of minder vrije schijfruimte beschikbaar is. Er wordt een kritieke waarschuwing gegenereerd wanneer er 5 GB of minder vrije schijfruimte beschikbaar is. U kunt deze waarden aanpassen of waarschuwingen voor afzonderlijke sites uitschakelen.  

 Als u deze instellingen wilt wijzigen:  

1.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Sites**.  

2.  Selecteer de site die u wilt configureren en openen van die site **eigenschappen**.  

3.  In de site **eigenschappen** in het dialoogvenster, selecteer de **waarschuwing** tabblad en bewerk vervolgens de instellingen.  

4.  Klik op **OK** om het dialoogvenster met eigenschappen voor de site te sluiten.  

