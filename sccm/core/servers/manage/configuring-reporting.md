---
title: Rapportage configureren
titleSuffix: Configuration Manager
description: "Meer informatie over het instellen van rapportage in Configuration Manager-hiërarchie, inclusief informatie over SQL Server Reporting Services."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 55ae86a7-f0ab-4c09-b4da-89cd0e7fa0e0
caps.latest.revision: "6"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: be8c36c73478e232254185681546f5f52c7d701f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="configuring-reporting-in-system-center-configuration-manager"></a>Rapportage in System Center Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u kunt maken, wijzigen en uitvoeren van rapporten in de System Center Configuration Manager-console, moet u een aantal configuratietaken uitvoeren. Gebruik de volgende secties in dit onderwerp voor hulp bij het configureren van rapportage in Configuration Manager-hiërarchie:  

 Voordat u doorgaat met de installatie en configuratie van Reporting Services in uw hiërarchie, controleert u de volgende Configuration Manager onderwerpen over rapportage:  

-   [Inleiding tot rapportage in System Center Configuration Manager](../../../core/servers/manage/introduction-to-reporting.md)  

-   [Rapportage in System Center Configuration Manager plannen](../../../core/servers/manage/planning-for-reporting.md)  

##  <a name="BKMK_SQLReportingServices"></a> SQL Server Reporting Services  
 SQL Server Reporting Services is een serverrapportageplatform dat uitgebreide rapportagefunctionaliteit biedt voor een waaier aan gegevensbronnen. Reporting services-punt in Configuration Manager communiceert met SQL Server Reporting Services Configuration Manager-rapporten kopiëren naar een opgegeven rapportmap Reporting Services-instellingen te configureren en beveiligingsinstellingen voor Reporting Services te configureren. Reporting Services maakt verbinding met de database van de Configuration Manager-site voor het ophalen van gegevens die worden geretourneerd wanneer u rapporten uitvoert.  

 Voordat u het reporting servicepunt in een Configuration Manager-site installeren kunt, moet u het installeren en configureren van SQL Server Reporting Services op het sitesysteem dat als host fungeert voor de reporting services-punt-sitesysteemrol. Zie voor informatie over het installeren van Reporting Services de [SQL Server TechNet-bibliotheek](http://go.microsoft.com/fwlink/p/?LinkId=266389).  

 Gebruik de volgende procedure om te controleren of SQL Server Reporting Services is geïnstalleerd en normaal wordt uitgevoerd.  

#### <a name="to-verify-that-sql-server-reporting-services-is-installed-and-running"></a>Controleren of SQL Server Reporting Services is geïnstalleerd en wordt uitgevoerd  

1.  Klik op de bureaubladcomputer op **Start**, **Alle programma's**, **Microsoft SQL Server 2008 R2**, **Configuratiehulpprogramma's**en vervolgens op **Reporting Services Configuration Manager**.  

2.  Geef in het dialoogvenster **Reporting Services-configuratieverbinding** de naam op van de server die SQL Server Reporting Services host. Selecteer op het menu het SQL Server-exemplaar waarop u SQL Reporting Services hebt geïnstalleerd en klik op **Verbinden**. De Reporting Services Configuration Manager wordt geopend.  

3.  Controleer op de pagina **Rapportserverstatus** of de **Report Service-status** is ingesteld op **Gestart**. Is dit niet het geval, klik dan op **Start**.  

4.  Klik op de pagina **Webservice-URL** op de URL in **Webservice-URL's Report Service** om de verbinding naar de rapportmap te testen. Het venster **Windows-beveiliging** kan worden geopend en u vragen om beveiligingsreferenties. Uw gebruikersaccount wordt standaard weergegeven. Voer uw wachtwoord in en klik op **OK**. Controleer of de webpagina is geopend. Sluit  het browservenster.  

5.  Controleer op de pagina **Database** of de instelling **Rapportservermodus** is geconfigureerd via **Native**.  

6.  Klik op de pagina **Report Manager-URL** op de URL in **Identificatie van Report Manager-site** om de verbinding naar de virtuele directory voor Report Manager te testen. Het venster **Windows-beveiliging** kan worden geopend en u vragen om beveiligingsreferenties. Uw gebruikersaccount wordt standaard weergegeven. Voer uw wachtwoord in en klik op **OK**. Controleer of de webpagina is geopend. Sluit  het browservenster.  

    > [!NOTE]  
    >  Reporting Services Report Manager is niet vereist voor rapportage in Configuration Manager, maar is wel vereist als u wilt uitvoeren van rapporten op een internetbrowser of rapporten met Report Manager wilt beheren.  

7.  Klik op **afsluiten** Reporting Services Configuration Manager te sluiten.  

##  <a name="BKMK_ReportBuilder3"></a> Rapportage instellen op het gebruik van Report Builder 3.0  

#### <a name="to-change-the-report-builder-manifest-name-to-report-builder-30"></a>Wijzigen van de manifestnaam Report Builder in Report Builder 3.0  

1.  Open de Register-Editor van Windows op de computer waarop de Configuration Manager-console wordt uitgevoerd.  

2.  Blader naar **HKEY_LOCAL_MACHINE/SOFTWARE/Wow6432Node/Microsoft/ConfigMgr10/AdminUI/Reporting**.  

3.  Dubbelklik op de sleutel **ReportBuilderApplicationManifestName** om de waardegegevens te bewerken.  

4.  Wijzig **ReportBuilder_2_0_0_0.application** in **ReportBuilder_3_0_0_0.application**en klik dan op **OK**.  

5.  Sluit de Register-editor van Windows.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> Een Reporting Services-punt installeren  
 Het Reporting Services-punt moet op een site zijn geïnstalleerd om rapporten op de site te beheren. Het Reporting Services-punt kopieert rapportmappen en rapporten naar SQL Server Reporting Services, past het beveiligingsbeleid toe voor de rapporten en mappen en stelt de configuratie-instellingen in Reporting Services in. U moet een reporting services-punt configureren voordat rapporten worden weergegeven in de Configuration Manager-console en voordat u de rapporten in Configuration Manager kunt beheren. Het Reporting Services-punt is een sitesysteemrol die moet worden geconfigureerd op een server waarop Microsoft SQL Server Reporting Services is geïnstalleerd en wordt uitgevoerd. Zie voor meer informatie over vereisten [vereisten voor rapportage](prerequisites-for-reporting.md).  

> [!IMPORTANT]  
>  Wanneer u een site selecteert voor de installatie van het Reporting Services-punt, houd er dan rekening mee dat gebruikers die de rapporten openen zich in hetzelfde beveiligingsbereik bevinden als de site waarop het Reporting Services-punt is geïnstalleerd.  

> [!NOTE]  
>  Wijzig nadat u een Reporting Services-punt op een sitesysteem hebt geïnstalleerd niet de URL voor de rapportserver. Als u reporting services-punt, maken en vervolgens in Reporting Services Configuration Manager als u de URL voor de rapportserver wijzigt, blijft de Configuration Manager-console de oude URL gebruiken en kunt u zich kan niet worden uitgevoerd, bewerken of maken van rapporten uit de console. Als u de URL voor de rapportserver moet wijzigen, verwijdert u het Reporting Services-punt, wijzigt u de URL en installeert u het Reporting Services-punt vervolgens opnieuw.  

> [!IMPORTANT]    
> Wanneer u een reporting services-punt installeert, moet u een Account Reporting Services-punt. Later, wanneer gebruikers uit een ander domein proberen een rapport uitvoeren, wordt het rapport niet uitgevoerd tenzij er een wederzijdse vertrouwensrelatie tot stand gebracht tussen de domeinen.

 Gebruik de volgende procedure voor het installeren van het Reporting Services-punt.  

#### <a name="to-install-the-reporting-services-point-on-a-site-system"></a>Installeren van het Reporting Services-punt op een sitesysteem  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw in de werkruimte **Beheer** **Siteconfiguratie**uit en klik op **Servers en sitesysteemrollen**.  

    > [!TIP]  
    >  Als u alleen sitesystemen wilt opnemen die de siterol van het Reporting Services-punt host, klikt u met de rechtermuisknop op **Servers en sitesysteemrollen** om **Reporting Services-punt**te selecteren.  

3.  Voeg de sitesysteemrol van het Reporting Services-punt toe aan een nieuwe of bestaande sitesysteemserver door gebruik te maken van de gekoppelde stap:  

    > [!NOTE]  
    >  Zie voor meer informatie over het configureren van sitesystemen [sitesysteemrollen voor System Center Configuration Manager toevoegen](../deploy/configure/add-site-system-roles.md).  

    -   **Nieuw sitesysteem**: Klik in het tabblad **Start** op **Sitesysteemserver maken** in de groep **Maken**. De **wizard Sitesysteemserver maken** wordt geopend.  

    -   **Bestaand sitesysteem**: Klik op de server waarop u wilt installeren van de reporting services-punt-sitesysteemrol. Als u op een server klikt, wordt er een lijst van reeds op de server geïnstalleerde sitesysteemrollen weergegeven in het resultatenvenster.  

         Klik op **Sitesysteemrol toevoegen** in het tabblad **Start** , in de groep **Server**. Hiermee opent u de **wizard Sitesysteemrollen toevoegen** .  

4.  Op de pagina **Algemeen** specificeert u de algemene instellingen voor de sitesysteemserver. Als u het Reporting Services-punt aan een bestaande sitesysteemserver toevoegt, verifieert u de eerder geconfigureerde waarden.  

5.  Selecteer **Reporting Services-punt** uit de lijst beschikbare rollen op de pagina **Systeemrolselectie** en klik vervolgens op **Volgende**.  

6.  Configureer op het tabblad **Reporting Services-punt** de volgende instellingen:  

    -   **Naam van Sitedatabaseserver**: Geef de naam van de server die als host fungeert voor de Configuration Manager-sitedatabase. De wizard haalt meestal automatisch de FQDN (fully qualified domain name) voor de server op. Als u wilt een database-exemplaar opgeven, gebruikt u de notatie &lt; *servernaam*>\&lt; *Naam serverinstantie*>.  

    -   **Databasenaam**: Geef de naam van de Configuration Manager-site-database en klik vervolgens op **controleren** om te bevestigen dat de wizard toegang tot de sitedatabase heeft.  

        > [!IMPORTANT]  
        >  Het gebruikersaccount dat het Reporting Services-punt maakt moet **Lezen** -toegang hebben tot de sitedatabase. Als de verbindingstest niet slaagt, wordt een rood waarschuwingspictogram weergegeven. Beweeg de cursor over dit pictogram om de reden te lezen van de fout. Corrigeer de fout en klik nogmaals op **Testen** .  

    -   **Mapnaam**: Geef de naam van de map die is gemaakt en gebruikt voor het hosten van de Configuration Manager-rapporten in Reporting Services.  

    -   **Reporting Services-serverexemplaar**: Selecteer in de lijst het exemplaar van SQL Server voor Reporting Services. Als er slechts één instantie is, is deze opgenomen en geselecteerd. Als er geen instanties zijn, controleer dan of SQL Server Reporting Services is geïnstalleerd en geconfigureerd en dat de SQL Server Reporting Services-service is gestart op het sitesysteem.  

        > [!IMPORTANT]  
        >  Configuration Manager maakt een verbinding in de context van de huidige gebruiker naar Windows Management Instrumentation (WMI) op het geselecteerde sitesysteem om op te halen van het exemplaar van SQL Server voor Reporting Services. De huidige gebruiker moet **Lezen** -toegang hebben tot WMI op het sitesysteem. Is dit niet het geval, dan kunnen er geen Reporting Services-instanties worden opgehaald.  

    -   **Reporting Services-punt Account**: Klik op **ingesteld**, en selecteer vervolgens een account moet worden gebruikt wanneer SQL Server Reporting Services op het reporting services-punt verbinding maakt met de Configuration Manager-sitedatabase om op te halen van de gegevens die worden weergegeven in een rapport. Selecteer **bestaand account** opgeven van een Windows-gebruikersaccount dat eerder is geconfigureerd als een Configuration Manager-account in of selecteer **nieuwe account** om op te geven van een Windows-gebruikersaccount dat is momenteel niet geconfigureerd als een Configuration Manager-account. Configuration Manager verleent automatisch de opgegeven gebruikerstoegang tot de sitedatabase. De gebruiker wordt weergegeven in de submap **Accounts** van het knooppunt **Beveiliging** in de werkruimte **Beheer** met de accountnaam van **ConfigMgr Reporting Services-punt** .  

         Het account dat de Reporting Services uitvoert moet behoren tot de lokale beveiligingsgroep van het domein, **Groep voor toegang tot Windows-machtigingen**, en de **Lezen tokenGroupsGlobalAndUniversal** -machtiging hebben om **Toestaan**in te stellen. Er moet een wederzijdse vertrouwensrelatie tot stand gebracht voor gebruikers van een ander domein dan die van het Account Servicies punt Reporting is het uitvoeren van rapporten.

         Het opgegeven Windows-gebruikersaccount en wachtwoord zijn versleuteld en opgeslagen in de Reporting Services-database. Reporting Services haalt de gegevens op voor rapporten van de sitedatabase met dit account en wachtwoord.  

        > [!IMPORTANT]  
        >  Het account dat u opgeeft moet de machtiging **Lokaal aanmelden** hebben op de computer die de Reporting Services-database host.  

7.  Op de pagina **Reporting Services-punt** klikt u op **Volgende**.  

8.  Verifieer de instellingen op de pagina **Samenvatting** en klik vervolgens op **Volgende** om het Reporting Services-punt te installeren.  

     Nadat de wizard is voltooid, worden de mappen gemaakt en de Configuration Manager-rapporten worden gekopieerd naar de opgegeven rapportmappen.  

    > [!NOTE]  
    >  Wanneer de rapportmappen zijn gemaakt en de rapporten gekopieerd naar de rapportserver, bepaalt Configuration Manager de juiste taal voor de objecten. Als het gekoppelde taalpakket is geïnstalleerd op de site, maakt Configuration Manager de objecten in dezelfde taal als het besturingssysteem op de rapportserver op de site. Als de taal niet beschikbaar is, worden de rapporten in het Engels opgesteld en weergegeven. Als u een Reporting Services-punt installeert op een site zonder taalpakketten, worden de rapporten in het Engels geïnstalleerd. Als u een taalpakket installeert nadat u het Reporting Services-punt hebt geïnstalleerd, moet u het Reporting Services-punt verwijderen en opnieuw installeren zodat de rapporten worden weergegeven in de juiste taal van het taalpakket. Zie voor meer informatie over taalpakketten [taalpakketten in System Center Configuration Manager](../deploy/install/language-packs.md).  

###  <a name="BKMK_FileInstallationAndSecurity"></a> Bestandsinstallatie en de beveiligingsrechten van rapportmappen  
 Configuration Manager voert de volgende bewerkingen voor het reporting services-punt installeren en Reporting Services te configureren:  

> [!IMPORTANT]  
>  De bewerkingen in de volgende lijst worden uitgevoerd door de verificatiegegevens te gebruiken van het account dat is geconfigureerd voor de SMS_Executive-service, dat doorgaans het lokale systeemaccount is van de siteserver.  

-   Installeert de siterol van het Reporting Services-punt.  

-   Maakt de gegevensbron in Reporting Services met de opgeslagen verificatiegegevens die u hebt opgegeven in de wizard. Dit is het Windows-gebruikersaccount en wachtwoord dat Reporting Services gebruikt voor verbinding met de sitedatabase wanneer u rapporten uitvoert.  

-   Maakt de hoofdmap van Configuration Manager in Reporting Services.  

-   Voegt de **ConfigMgr-rapportgebruikers** en beveiligingsrollen van **ConfigMgr-rapportbeheerders** toe in Reporting Services.  

-   Maakt submappen en implementeert Configuration Manager-rapporten van %ProgramFiles%\SMS_SRSRP naar Reporting Services.  

-   Voegt de **ConfigMgr rapportgebruikers** rol in Reporting Services aan de hoofdmappen voor alle gebruikersaccounts in Configuration Manager met **Site lezen** rechten.  

-   Voegt de **ConfigMgr rapportbeheerders** rol in Reporting Services aan de hoofdmappen voor alle gebruikersaccounts in Configuration Manager met **Site wijzigen** rechten.  

-   Haalt de toewijzing tussen rapportmappen en de Configuration Manager beveiligde objecttypen (onderhouden in de Configuration Manager-sitedatabase).  

-   Configureert de volgende rechten voor gebruikers met beheerdersrechten in Configuration Manager voor specifieke rapportmappen in Reporting Services:  

    -   Voegt gebruikers toe en wijst de **ConfigMgr rapportgebruikers** rol aan de gekoppelde rapportmap voor gebruikers met beheerdersrechten die beschikken over **rapport uitvoeren** machtigingen voor de Configuration Manager-object.  

    -   Voegt gebruikers toe en wijst de **ConfigMgr rapportbeheerders** rol aan de gekoppelde rapportmap voor gebruikers met beheerdersrechten die beschikken over **rapport wijzigen** machtigingen voor de Configuration Manager-object.  

     Configuration Manager verbinding met Reporting Services en stelt de machtigingen voor gebruikers op de Configuration Manager en Reporting Services hoofdmappen en specifieke rapportmappen. Na de initiële installatie van reporting services-punt, Configuration Manager maakt verbinding met Reporting Services in een interval van 10 minuten om te controleren dat de gebruikersrechten die op de rapportmappen geconfigureerd zijn met de gekoppelde rechten die zijn ingesteld voor gebruikers met Configuration Manager. Wanneer gebruikers worden toegevoegd of gebruikersrechten worden gewijzigd op de rapportmap met behulp van Reporting Services Report Manager, worden die wijzigingen overschreven met behulp van de rolgebaseerde toewijzingen die wordt opgeslagen in de sitedatabase van Configuration Manager. Configuration Manager verwijdert tevens gebruikers die geen rapportagerechten in Configuration Manager.  

##  <a name="BKMK_SecurityRoles"></a> Reporting Services-beveiligingsrollen voor Configuration Manager  
 Wanneer Configuration Manager de reporting services-punt installeert, wordt u de volgende beveiligingsrollen toegevoegd in Reporting Services:  

-   **ConfigMgr-rapportgebruikers**: Gebruikers die zijn toegewezen aan deze beveiligingsrol kunnen Configuration Manager-rapporten alleen worden uitgevoerd.  

-   **ConfigMgr-rapportbeheerders**: Gebruikers die zijn toegewezen aan deze beveiligingsrol kunnen alle taken met betrekking tot rapportage in Configuration Manager uitvoeren.  

##  <a name="BKMK_VerifyReportingServicesPointInstallation"></a> De installatie van het Reporting Services-punt controleren  
 Nadat u de siterol van het Reporting Services-punt hebt toegevoegd, kunt u de installatie controleren door te kijken naar specifieke statusberichten en logboekvermeldingen. Gebruik de volgende procedure om te controleren of de installatie van het Reporting Services-punt geslaagd is.  

> [!WARNING]  
>  U kunt deze procedure overslaan als rapporten worden weergegeven in de **rapporten** submap van de **rapportage** knooppunt in de **bewaking** werkruimte in de Configuration Manager-console.  

#### <a name="to-verify-the-reporting-services-point-installation"></a>Controleren van de installatie van het Reporting Services-punt  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte **Bewaking** **Systeemstatus**uit en klik vervolgens op **Componentstatus**.  

3.  Klik in de lijst met componenten op **SMS_SRS_REPORTING_POINT** .  

4.  Klik op het tabblad **Start** , in de groep **Component** , op **Berichten tonen**en klik vervolgens op **Alle**.  

5.  Specificeer een datum en tijdstip voor een periode vóórdat u het Reporting Services-punt installeerde, en klik daarna op **OK**.  

6.  Controleer of statusbericht ID 1015 er bij staat, dit geeft aan dat het Reporting Services-punt succesvol geïnstalleerd is. U kunt ook het bestand Srsrp.log in openen &lt; *ConfigMgr-installatiepad*> \Logs bevindt en zoeken naar **installatie is geslaagd**.  

     Navigeer in Windows Verkenner naar &lt; *ConfigMgr-installatiepad*> \Logs.  

7.  Open Srsrp.log en loop stap voor stap door het logbestand, beginnend vanaf het tijdstip waarop het Reporting Services-punt succesvol geïnstalleerd werd. Controleer of de rapportmappen gemaakt zijn, of de rapporten geïmplementeerd zijn en of het beveiligingsbeleid op elke map bevestigd is. Zoek naar **Met succes gecontroleerd of de SRS webservice een gezonde status heeft op server** na de laatste regel van beveiligingsbeleid-bevestigingen.  

##  <a name="BKMK_Certificate"></a> Een zelfondertekend certificaat voor Configuration Manager-consolecomputers configureren  
 Er zijn veel manieren voor het maken van SQL Server Reporting Services-rapporten. Wanneer u maakt of rapporten in de Configuration Manager-console bewerkt, geeft Configuration Manager Report Builder om te gebruiken als ontwerpomgeving wordt geopend. Ongeacht hoe u uw Configuration Manager-rapporten schrijven, is een zelfondertekend certificaat vereist voor serververificatie naar de Sitedatabaseserver. Configuration Manager installeert automatisch het certificaat op de siteserver en de computers waarop de SMS-Provider geïnstalleerd. U kunt daarom maken of bewerken van rapporten uit de Configuration Manager-console wanneer deze wordt uitgevoerd op een van deze computers. Echter, wanneer u rapporten maakt of aanpast vanuit een Configuration Manager-console die is geïnstalleerd op een andere computer, moet u het certificaat exporteren van de siteserver en vervolgens toe te voegen aan de **vertrouwde personen** certificaatarchief op de computer waarop de Configuration Manager-console.  

> [!NOTE]  
>  Voor meer informatie over andere rapportontwerpomgevingen voor SQL Server Reporting Services, zie [Comparing Report Authoring Environments (Vergelijken van rapportontwerpomgevingen)](http://go.microsoft.com/fwlink/p/?LinkId=242805) in de SQL Server 2008 Books Online.  

 Gebruik de volgende procedure als voorbeeld voor het overzetten van een kopie van het zelfondertekende certificaat van de siteserver naar een andere computer waarop de Configuration Manager-console wordt uitgevoerd wanneer beide computers Windows Server 2008 R2. Raadpleeg de documentatie van uw besturingssysteem voor de juiste procedure als u deze procedure niet kunt gebruiken omdat u een andere versie hebt van het besturingssysteem.  

#### <a name="to-transfer-a-copy-of-self-signed-certificate-from-the-site-server-to-another-computer"></a>Overzetten van een exemplaar van het zelfondertekend certificaat van een siteserver naar een andere computer  

1.  Voer de volgende stappen uit op de siteserver om het zelfondertekend certificaat te exporteren:  

    1.  Klik op **Start**, klik op **Uitvoeren**en typ **mmc.exe**. Klik in de lege console op **Bestand**en klik vervolgens op **Module toevoegen/verwijderen**.  

    2.  Selecteer **Certificaten** uit de lijst van **Beschikbare modules** in het dialoogvenster **Modules toevoegen of verwijderen**en klik vervolgens op **Toevoegen**.  

    3.  Selecteer **Computeraccount** in het dialoogvenster **Module certificaten**en klik vervolgens op **Volgende**.  

    4.  Controleer in het dialoogvenster **Computer selecteren** of **Lokale computer: (de computer waarop deze console wordt uitgevoerd)** is geselecteerd en klik vervolgens op **Voltooien**.  

    5.  Klik op **OK** in het dialoogvenster **Modules toevoegen of verwijderen**.  

    6.  Vouw **Certificaten (lokale computer)**uit in de console, vouw **Vertrouwde personen**uit en selecteer **Certificaten**.  

    7.  Met de rechtermuisknop op het certificaat met de beschrijvende naam van &lt; *FQDN-naam van de siteserver*>, klik op **alle taken**, en selecteer vervolgens **exporteren**.  

    8.  Doorloop de wizard **Certificaat exporteren** door de standaardopties te gebruiken en sla het certificaat op met de extensie **.cer** .  

2.  Voer de volgende stappen uit op de computer waarop de Configuration Manager-console om het zelfondertekend certificaat toevoegen aan het certificaatarchief Vertrouwde personen:  

    1.  Herhaal de stappen 1.a tot en met 1.e voor het configureren van de **certificaat** module in MMC op de beheerpuntcomputer.  

    2.  Vouw **Certificaten (lokale computer)**uit in de console, vouw **Vertrouwde personen**uit, klik met de rechtermuisknop op **Certificaten**, selecteer **Alle taken**, en selecteer vervolgens **Importeren** om de wizard **Certificaat importeren**te starten.  

    3.  Selecteer op de pagina **Bestand om te importeren** het certificaat dat werd opgeslagen in stap 1.h, en klik daarna op **Volgende**.  

    4.  Selecteer op de pagina **Certificaatarchief** **Alle certificaten in het volgende archief plaatsen**, waarbij **Certificaatarchief** is ingesteld op **Vertrouwde personen**, en klik daarna op **Volgende**.  

    5.  Klik op **Voltooien** om de wizard te sluiten en de configuratie van het certificaat op de computer te voltooien.  

##  <a name="BKMK_ModifyReportingServicesPoint"></a> Instellingen van Reporting Services-punt wijzigen  
 Nadat het Reporting Services-punt geïnstalleerd is, kunt u de sitedatabaseverbinding en de verificatie-instellingen bij de eigenschappen van het Reporting Services-punt wijzigen. Gebruik de volgende procedure om de instellingen van het Reporting Services-punt te wijzigen.  

#### <a name="to-modify-reporting-services-point-settings"></a>Instellingen voor het Reporting Services-punt wijzigen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Siteconfiguratie** in de werkruimte **Beheer**uit en klik vervolgens op **Servers en sitesysteemrollen** om de sitesystemen te tonen.  

    > [!TIP]  
    >  Als u alleen sitesystemen wilt opnemen die de siterol van het Reporting Services-punt host, klikt u met de rechtermuisknop op **Servers en sitesysteemrollen** om **Reporting Services-punt**te selecteren.  

3.  Selecteer het sitesysteem dat het Reporting Services-punt host waarop u instellingen wilt wijzigen, en selecteer vervolgens **Reporting Service-punt** in **Sitesysteemrollen**.  

4.  Klik op **Eigenschappen** in het tabblad **Siterol** , in de groep **Eigenschappen**.  

5.  In het dialoogvenster **Eigenschappen Reporting Services-punt** kunt de volgende instellingen wijzigen:  

    -   **Naam van Sitedatabaseserver**: Geef de naam van de server die als host fungeert voor de Configuration Manager-sitedatabase. De wizard haalt meestal automatisch de FQDN (fully qualified domain name) voor de server op. Als u wilt een database-exemplaar opgeven, gebruikt u de notatie &lt; *servernaam*>\&lt; *Naam serverinstantie*>.  

    -   **Databasenaam**: Geef de naam van de System Center 2012 Configuration Manager-site-database en klik vervolgens op **controleren** om te bevestigen dat de wizard toegang tot de sitedatabase heeft.  

        > [!IMPORTANT]  
        >  Het gebruikersaccount dat het Reporting Services-punt maakt, moet beschikken over de machtiging Lezen voor de sitedatabase. Als de verbindingstest niet slaagt, wordt een rood waarschuwingspictogram weergegeven. Beweeg de cursor over dit pictogram om de reden te lezen van de fout. Corrigeer de fout en klik nogmaals op **Testen** .  

    -   **Gebruikersaccount**: Klik op **ingesteld**, en selecteer vervolgens een account dat gebruikt wordt wanneer SQL Server Reporting Services op het reporting services-punt verbinding maakt met de Configuration Manager-sitedatabase om op te halen van de gegevens die worden weergegeven in een rapport. Selecteer **bestaand account** opgeven van een Windows-gebruikersaccount dat bestaande Configuration Manager-rechten heeft of selecteer **nieuwe account** om op te geven van een Windows-gebruikersaccount dat momenteel beschikt niet over rechten in Configuration Manager. Configuration Manager verleent automatisch de opgegeven gebruikerstoegang tot de sitedatabase. Het account wordt weergegeven als het **ConfigMgr SRS reporting point** -account in de submap **Accounts** van het knooppunt **Beveiliging** in de werkruimte **Beheer** .  

         Het opgegeven Windows-gebruikersaccount en wachtwoord zijn versleuteld en opgeslagen in de Reporting Services-database. Reporting Services haalt de gegevens op voor rapporten van de sitedatabase met dit account en wachtwoord.  

        > [!IMPORTANT]  
        >  Als de sitedatabase zich op een extern sitesysteem bevindt, moet het door u gespecificeerde account beschikken over de machtiging **Lokaal inloggen** voor de computer.  

6.  Klik op **OK** om de wijzigingen op te slaan en het dialoogvenster af te sluiten.  

## <a name="upgrading-sql-server"></a>SQL Server upgraden  
 Na de upgrade van SQL Server en SQL Server Reporting Services die wordt gebruikt als gegevensbron voor reporting services-punt, kunt u fouten tegenkomen wanneer u rapporten uitvoert of vanuit de Configuration Manager-console bewerkt. Voor rapportage goed te laten werken vanuit de Configuration Manager-console, moet u de siterol reporting services-punt system voor de site verwijderen en opnieuw te installeren. Na de upgrade kunt u echter succesvol rapporten blijven uitvoeren en bewerken vanuit een internetbrowser.  

##  <a name="BKMK_ConfigureReportOptions"></a> Rapportopties configureren  
 Gebruik de rapportopties voor een Configuration Manager-site om het standaard reporting services-punt dat wordt gebruikt voor het beheren van uw rapporten te selecteren. Hoewel u meerdere Reporting Services-punten kunt hebben op een site, wordt alleen de standaard-rapportserver die bij rapportopties geselecteerd is, gebruikt om rapporten te beheren. Gebruik de volgende procedure om rapportopties voor uw site te configureren.  

#### <a name="to-configure-report-options"></a>Rapportopties configureren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte **Bewaking** **Rapportage**uit en klik vervolgens op **Rapporten**.  

3.  Klik op **Rapportopties** in het tabblad **Start** , in de groep **Instellingen**.  

4.  Selecteer de standaard-rapportserver in de lijst, en klik vervolgens op **OK**. Als er geen Reporting Services-punten in de lijst staan, controleer dan of er succesvol een Reporting Services-punt geïnstalleerd en geconfigureerd is in de site.  

## <a name="next-steps"></a>Volgende stappen
[Bewerkingen en onderhoud voor rapportage](operations-and-maintenance-for-reporting.md)
