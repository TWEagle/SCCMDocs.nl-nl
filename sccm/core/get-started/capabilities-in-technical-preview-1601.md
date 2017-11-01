---
title: Mogelijkheden van Technical Preview 1601
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1601.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aae1cf2f-2c04-4f68-a03a-f4a925433c09
caps.latest.revision: "7"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: d673fce313ca0cfb0a001dac9bbe296f883a4871
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1601-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1601 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1601 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.  

 **Bekende problemen voor deze Technical Preview:**  

-   Wanneer u beheert **Clientupdateopties** als u een pre-productieclient naar productie verhogen, de tekst voor het selectievakje wordt weergegeven een clientversie van nul (0) in plaats van het werkelijke client build-nummer. De juiste clientversie voor preproductie wordt weergegeven in het gedeelte boven deze optie en de clientversie die wordt gepromoveerd voor productie wanneer u deze optie selecteert.  

-   Wanneer u bijwerkt naar Technical Preview 1601 en ervoor kiest de Configuration Manager-client testen in pre-productieverzameling, wordt het clientpakket voor de verzameling niet worden bijgewerkt. Dit probleem is alleen voor Technical Preview 1601.  

     Als tijdelijke oplossing Voer deze problemen een van de volgende:  

    -   Voer de volgende SQL-script op de primaire sitedatabase:  

        ```  
        DECLARE @PilotingPkgID NVARCHAR(8)  

        SELECT @PilotingPkgID = PilotingPackageID FROM ClientDeploymentSettings  

        MERGE INTO PkgServers_G AS T  
        USING (  
            SELECT @PilotingPkgID AS PkgID, NALPath, SiteCode, SiteName, SourceSite, RefreshTrigger, UpdateMask, [Action]  
            FROM PkgServers_G WHERE PkgID IN (SELECT UpgradePackageID FROM ClientDeploymentSettings)  
            ) AS S  
        ON T.PkgID = S.PkgID and T.NALPath = S.NALPath  

        WHEN NOT MATCHED THEN  
            INSERT (PkgID, NALPATH, SiteCode, SiteName, SourceSite, LastRefresh, RefreshTrigger, UpdateMask, [Action])  
            VALUES (S.PkgID, S.NALPath, S.SiteCode, S.SiteName, S.SourceSite, GetUTCDate(), S.RefreshTrigger, S.UpdateMask, S.[Action])  
        ;  

        ```  

    -   Een nieuwe site distributiepuntrol toevoegen aan uw labsite. Het nieuwe distributiepunt upgradet de pre-productieverzameling met het nieuwe clientpakket.  

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="bkmk_hybrid1"></a>Verbeteringen aan Microsoft Intune-integratie  
In de Technical Preview 1601 is ondersteuning voor de volgende functies toegevoegd:  

### <a name="improvements-to-conditional-access"></a>Verbeteringen aan voorwaardelijke toegang  

-   **Ondersteuning voor voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager**  

     Nu kunt u beleidsregels voor voorwaardelijke toegang instellen voor pc's die worden beheerd door System Center Configuration Manager, die wordt vereist dat de pc's compatibel met het nalevingsbeleid zijn om toegang tot Exchange Online en SharePoint Online-services.  Met deze nieuwe functionaliteit kunt u ook pc's met Azure AD via het nalevingsbeleid en bewaken en rapporteren op Azure AD-registratie te registreren.  

    > [!NOTE]  
    >  Voorwaardelijke toegang is nog niet ondersteund op Windows 10.  

    Hieronder volgen de vereisten voor het gebruik van deze functie:  

    -   Azure Active Directory Premium-abonnement en ADFS-synchronisatie.  

    -   Een Microsoft Intune-abonnement. De Microsoft Intune-abonnement moet worden geconfigureerd in Configuration Manager-Console.  

    -   [Vereisten voor automatische registratie van Azure AD](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    Voor het gebruik van de optie moet u een nalevingsbeleid in Configuration Manager maken met specifieke regels die hieronder worden beschreven en beleid voor voorwaardelijke toegang instellen in de Intune-console.  Ook om te zorgen dat alleen compatibele pc's toegang hebben, stelt u de vereiste Windows-PC op **apparaten moeten voldoen** optie. Hier volgen de compatibiliteitsbeleidsregels die van toepassing op pc's die worden beheerd door System Center Configuration manager.  

    -   **Registratie in Azure Active Directory vereisen:** Deze regel controleert u of het apparaat van de gebruiker is toegevoegd aan Azure AD en als dat niet het geval is, wordt het apparaat automatisch geregistreerd bij Azure AD. Automatische inschrijving wordt alleen ondersteund op Windows 8.1. Implementeer een MSI-bestand om automatische inschrijving voor Windows 7-pc's uit te voeren. Zie voor meer informatie [hier](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    -   **Alle vereiste updates zijn geïnstalleerd met een deadline die ouder zijn dan een bepaald aantal dagen:** Deze regel controleert om te zien als apparaat van de gebruiker beschikt over alle vereiste updates (opgegeven in de **vereiste automatische updates** regel) binnen de deadline en respijtperiode die is opgegeven door u en automatisch eventuele vereiste updates die nog niet installeren.  

    -   **BitLocker-stationsversleuteling vereisen:** Dit is een controleert u of het primaire station (bijvoorbeeld C:\\) op het apparaat BitLocker versleuteld. Als Bitlocker-versleuteling niet is ingeschakeld op het primaire station, wordt de toegang tot e-mail en SharePoint-services geblokkeerd.  

    -   **Antimalware vereisen:** Dit is een controleert u of de antimalwaresoftware (System Center Endpoint Protection of alleen Windows Defender) is ingeschakeld en worden uitgevoerd.  
         Indien dit niet is ingeschakeld, wordt de toegang tot e-mail en SharePoint-services geblokkeerd.  

    Eindgebruikers die zijn geblokkeerd vanwege niet-naleving wordt compatibiliteitsinformatie weergeven in het SCCM Software Center en een nieuwe evaluatie van het beleid wordt gestart wanneer de nalevingsproblemen zijn hersteld.  

-   **Voorwaardelijke toegang met Health Attestation-Service** u kunt nu toegang tot e-mail en 0365-services op basis van de status van apparaten, zoals gemeld door de Health Attestation-Service beperken.  Daarnaast worden apparaten die worden beheerd door Intune opgenomen in de statusrapporten over apparaten.  

    Een nieuwe regel voor naleving is toegevoegd aan de configuration manager-console kunt u opgeven of de apparaten moeten worden toegestaan of geblokkeerd toegang op basis van hun gezondheidsstatus.  Voor deze regel maakt, opent u de **Wizard nalevingsbeleid maken**, en een nieuwe regel toevoegen.  Selecteer de **door de Health Attestation-Service als health gerapporteerd** voor de voorwaarde, en stel de waarde op **True**.  Hiermee zorgt u ervoor dat alleen apparaten die worden gerapporteerd als goed toegang tot uw bedrijfsbronnen vormen hebben. Zie voor meer informatie over Health Attestation-Service en hoe de status van apparaten in Intune wordt gerapporteerd [Health Attestation van apparaten](#bkmk_devicehealth).  

-   **Nieuwe beleidsinstellingen voor naleving:** De nieuwe instellingen nalevingsbeleid betere beveiliging en bescherming op apparaten die worden gebruikt voor toegang tot bedrijfse-mail en SharePoint-services:  

    -   **Automatische updates vereisen:** U kunt apparaten met Windows 8.1 of hoger vereisen toestaan automatische installatie van updates en tevens opgeven welke klasse updates die zijn geïnstalleerd.  U kunt kiezen om te: Installeer alleen de updates die zijn gemarkeerd als belangrijk of alle aanbevolen updates installeren.  

         Voor het maken van een regel voor automatische updates, opent u de **Wizard nalevingsbeleid maken**, en een nieuwe regel toevoegen.  Selecteer **minimale classificatie van vereiste updates** als de voorwaarde, en stel de waarde in op een van de beschikbare waarden: **Geen**, **aanbevolen**, en **belangrijke**.  

        -   **Geen:** Updates worden niet automatisch geïnstalleerd.  

        -   **Aanbevolen:** Alle aanbevolen updates zijn geïnstalleerd  

        -   **Belangrijk:** Alleen de updates die zijn geclassificeerd als belangrijk worden geïnstalleerd.  

    -   **Wachtwoord vereisen voor het ontgrendelen van mobiele apparaten:** Wanneer deze instelling is ingesteld op **Ja**, de eindgebruikers een wachtwoord moeten invoeren voordat ze toegang hun apparaat tot.  

         Voor het maken van een regel voor het wachtwoord voor het ontgrendelen van mobiele apparaten, opent u de **Wizard nalevingsbeleid maken**, en een nieuwe regel toevoegen. Selecteer **wachtwoord vereisen voor een inactief apparaat te ontgrendelen** als de voorwaarde, en stel de waarde op **True**.  

    -   **Minuten van inactiviteit voordat wachtwoord vereist is:**  Hiermee geeft u aan na hoeveel niet-actieve tijd gebruikers hun wachtwoord opnieuw moeten invoeren.  

         Voor deze regel maakt, opent u de **Wizard nalevingsbeleid maken**, en een nieuwe regel toevoegen. **Selecteer minuten van inactiviteit voordat wachtwoord vereist is** als de voorwaarde, en stel de waarde in op een van de beschikbare opties: 1 minuut, 5 minuten, 15 minuten, 30 minuten ik uur.  

-   **Standaardregel negeren - altijd geregistreerd bij Intune en compatibele apparaten toegang tot Exchange on-premises toestaan:**  

     Als u deze optie inschakelt, mogen apparaten die zijn ingeschreven in Intune en voldoen aan het nalevingsbeleid toegang tot Exchange on-premises. Deze regel wordt genegeerd voor de standaardregel dit houdt in dat zelfs als u instelt dat de standaardregel quarantaine uitvoert of de toegang hiervoor blokkeren, ingeschreven en compatibele apparaten worden nog steeds toegang tot Exchange on-premises.  
     Gebruik deze instelling als u wilt dat ingeschreven en compatibele apparaten altijd toegang hebben tot e-mail via Exchange on-premises.  

     Dit wordt ondersteund op de volgende platforms:  Windows Phone 8 en hoger, iOS 6 en hoger. Android 4.0 en hoger, Samsung KNOX Standard 4.0 en hoger.  

     Om deze optie gebruikt, gaat u naar de **algemene** pagina van de **Wizard voorwaardelijke toegang configureren beleid** voor Exchange on-premises.  

##  <a name="bkmk_clientStatus"></a>Onlinestatus van clients  
Vanaf technical preview 1601, kunt u identificeren in één oogopslag of een client online of offline in de Configuration Manager-console is. Met bijgewerkte pictogrammen en kolommen in het apparaatoverzicht van de console, kunt u de status van clients in uw omgeving om probleemgebieden en andere problemen die mogelijk uw aandacht te identificeren beoordelen.  

Een client is online als deze momenteel is verbonden met een Configuration Manager management sitesysteemrol. Zolang het beheerpunt ping-achtige berichten van de client ontvangt, wordt de status online is. Als het beheer een bericht voor de 5 minuten ontvangen heeft, wordt de status van de client gewijzigd naar offline.  

### <a name="icons-for-client-status"></a>Pictogrammen voor de clientstatus  

|||  
|-|-|  
|![online-statuspictogram voor clients](media/online-status-icon.png)|Client is online.|  
|![offline-statuspictogram voor clients](media/offline-status-icon.png)|Client is offline.|  
|![onbekende-statuspictogram voor clients](media/unknown-status-icon.png)|Clientstatus is onbekend.|  

### <a name="prerequisites"></a>Vereisten  
 Onlinestatus van clients zijn geen vereisten. U kunt deze gaan gebruiken zodra de Configuration Manager technical preview 1601 is geïnstalleerd.  

### <a name="limitations"></a>Beperkingen  
 Onlinestatus van clients is alleen beschikbaar voor Windows-computers met de Configuration Manager-client is geïnstalleerd. Onlinestatus van clients wordt niet ondersteund voor Mac-computers, Linux of UNIX-computer of apparaten die worden beheerd met op\-premises Mobile Device Management.  

### <a name="to-view-client-online-status"></a>Onlinestatus van clients weergeven  

1.  Ga in de Configuration Manager-console naar **activa en naleving > overzicht > apparaten**.  

2.  Met de rechtermuisknop op de kolomkop en klik vervolgens op een van de velden van de onlinestatus van de client toe te voegen aan de apparaatweergave. De velden zijn  

    -   **Onlinestatus van het apparaat** geeft aan of de client op dit moment online of offline is.  

    -   **Laatste tijdstip Online** geeft aan wanneer de onlinestatus van clients is gewijzigd van offline naar online.  

    -   **Laatste tijdstip Offline** geeft aan wanneer de status is gewijzigd van online naar offline.  

 Als u wilt weergeven van recente wijzigingen in de status van de client, vernieuw de console.  

##  <a name="bkmk_appmgmt1601"></a>Verbeteringen aan Toepassingsbeheer  
 In Technical Preview 1601 is ondersteuning voor de volgende functies toegevoegd:  

### <a name="manage-volume-purchased-apps-for-ios-devices"></a>Volume-purchased apps voor iOS-apparaten beheren  
 Bepaalde app stores bieden u de mogelijkheid meerdere licenties voor een app die u wilt uitvoeren binnen uw bedrijf te kopen. Zodoende kunt u de administratieve overhead voor het bijhouden reduceren als u meerdere exemplaren van apps hebt aangeschaft.  

 Configuration Manager kunt u nu apps beheren die u via een dergelijk programma hebt aangeschaft door de licentiegegevens uit de appstore te importeren en bij te houden hoeveel licenties u hebt gebruikt.  

 Zie voor meer informatie [apps die u hebt aangeschaft via een volume-aankoopprogramma met Configuration Manager beheren](https://technet.microsoft.com/library/mt627954.aspx).  

### <a name="ios---app-configuration-for-applicationsbr-hybrid"></a>iOS - App-configuratie voor toepassingen<br />Hybride  
 Sommige iOS-toepassingen ondersteunen het vooraf configureren van instellingen, zoals een server of database waarmee de toepassing verbinding moet maken. Configuration Manager ondersteunt nu implementeren app configuratiebeleid naar het apparaat zodat de gebruiker de app meteen kan gebruiken zonder te weten. Ontwikkelaars moeten deze functie in hun apps inschakelen.  

 Een beperkt aantal openbaar vrijgegeven apps ondersteund momenteel vooraf configureren van instellingen; u kunt ook hebt intern ontwikkelde line-of-business-apps die deze ondersteunen.  

#### <a name="prerequisites-for-this-scenario"></a>Vereisten voor dit scenario  

-   U moet hebt toegevoegd een abonnement op Microsoft Intune aan Configuration Manager.  

-   U moet hebt een geldig Apple APNs-certificaat toegevoegd aan het Intune-abonnement.  

-   U moet een iOS-toepassing die ondersteuning biedt voor Toepassingsconfiguratie hebt geïmplementeerd.  

#### <a name="try-it-out"></a>Probeer het nu!  
 Als de bovenstaande vereisten is voldaan, moet u een Configuration Manager-toepassing die gebruikmaakt van een iOS-implementatietype maken. De app die u gebruikt, moet Toepassingsconfiguratie ondersteunen. Raadpleeg de documentatie van de leverancier van de toepassing voor meer informatie over welke specifieke items (naam/waarde-paren), kunt u configureren.  

 Vervolgens koppelt u de app-configuratiebeleid aan het iOS-implementatietype tijdens de implementatie van de app. U kunt ook implementeren met het beleid vanuit de **Configuratiebeleidsregels** knooppunt, gericht op een bestaande app en verzameling.  

 Voer de volgende taken uitvoeren en vervolgens met de feedbackinformatie boven aan dit onderwerp laat ons weten hoe het is gegaan:  

-   Als u een iOS-app die ondersteuning biedt voor app-configuratie hebt, raadpleegt u de documentatie van de leverancier van de app voor meer informatie over de naam en waarde-paren dat u moet opgeven om de toepassing te configureren.  

-   Start de **App-configuratiebeleid maken** wizard. Op de **iOS-beleid** pagina van de wizard, voegt u de naam en waarde-paren u in de documentatie van de leverancier van de app of u gevonden kunnen een XML-bestand met de vereiste waarden importeren.  

-   In de **Software distribueren** wizard op de **App-configuratiebeleid** pagina, de app-configuratiebeleid die u hebt gemaakt met een compatibele implementatietype van de toepassing koppelen.  

##  <a name="bkmk_compliance1601"></a>Verbeteringen in de instellingen voor naleving  
 In Technical Preview 1601 is ondersteuning voor de volgende functies toegevoegd:  

### <a name="microsoft-edge-browser-settings"></a>Microsoft Edge-browserinstellingen  
 Nieuwe instellingen voor de browser Microsoft Edge zijn toegevoegd aan de **Windows 8.1 en Windows 10** configuratie-item (instellingen toegepast op Windows 10-apparaten).  

 Kies een overzicht van de nieuwe instellingen **Microsoft Edge** van configuratie-item **apparaatinstellingen** pagina van de **configuratie-Item maken** wizard.  

 Zie voor meer informatie [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="compliance-settings-for-windows-10-team-devices"></a>Instellingen voor naleving voor Windows 10 Team-apparaten  
 Gebruik deze nieuwe instellingen voor naleving om apparaten met Windows 10 team, zoals Surface Hub-apparaten te configureren.  

 Kies een overzicht van de nieuwe instellingen **Windows 10 Team** van configuratie-item **apparaatinstellingen** pagina van de **configuratie-Item maken** wizard.  

 Zie voor meer informatie [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="android---kiosk-mode-for-samsung-knox-standardbr-hybrid"></a>Android: kioskmodus voor Samsung KNOX Standard<br />Hybride  
 Kioskmodus kunt u een apparaat zo vergrendelen dat alleen bepaalde functies werken. U kunt bijvoorbeeld toestaan dat een apparaat slechts één beheerde app uitvoert die u opgeeft, of kunt u de volumeknoppen op een apparaat uitschakelen. Deze instellingen kunnen worden gebruikt voor een demonstratiemodel van een apparaat of voor een apparaat dat is toegewezen aan slechts één functie, zoals een verkooppuntapparaat. Deze instellingen zijn niet beschikbaar voor Samsung KNOX Standard-apparaten in de **Windows 8.1 en Windows 10** configuratie-item (instellingen toegepast op Windows 10-apparaten).  

 Kies een overzicht van de nieuwe instellingen **kioskmodus - Samsung KNOX** van configuratie-item **apparaatinstellingen** pagina van de **configuratie-Item maken** wizard.  

 Zie voor meer informatie [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  
