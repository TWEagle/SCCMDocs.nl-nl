---
title: Mogelijkheden in Technical Preview 1601 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1601.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aae1cf2f-2c04-4f68-a03a-f4a925433c09
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ef0db5b11ae2be5edcb4db87400c5c273c89972e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1601-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1601 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1601 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.  

 **Bekende problemen voor deze Technical Preview:**  

-   Als u beheert **Clientupdateopties** als u een pre-productieclient gemaakt via productie verhogen, door de tekst voor het selectievakje een clientversie van nul (0) in plaats van het werkelijke client build-nummer wordt weergegeven. De juiste pre-productieclient-versie op het eerste gezicht boven deze optie wordt weergegeven en wordt de versie van de client die wordt gemaakt via productie gepromoveerd wanneer u deze optie selecteert.  

-   Bij het bijwerken naar technische Preview 1601 en kies daarbij de Configuration Manager-client testen in een pre-productieverzameling, zal het clientpakket voor de verzameling niet worden bijgewerkt. Dit probleem heeft alleen betrekking op technische Preview 1601.  

     Naar tijdelijke oplossing Doe deze problemen het volgende:  

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

    -   Een nieuwe system distributiepuntsiterollen toevoegen aan uw lab-site. Het nieuwe distributiepunt werkt de pre-productieverzameling met het nieuwe clientpakket.  

**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="bkmk_hybrid1"></a>Verbeteringen in Microsoft Intune-integratie  
In de Technical Preview 1601 hebben we toegevoegde ondersteuning voor de volgende functies:  

### <a name="improvements-to-conditional-access"></a>Verbeteringen in voorwaardelijke toegang  

-   **Ondersteuning voor voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager**  

     Nu kunt u beleidsregels voor voorwaardelijke toegang voor pc's die worden beheerd door System Center Configuration Manager, waardoor er dat de pc's compatibel met het nalevingsbeleid zijn voor toegang tot Exchange Online en SharePoint Online services instellen.  Met deze nieuwe functionaliteit, kunt u ook pc's met Azure AD via het nalevingsbeleid en bewaken en rapporteren van Azure AD-registratie te registreren.  

    > [!NOTE]  
    >  Voorwaardelijke toegang is nog niet ondersteund op Windows 10.  

    Hier volgen de vereisten voor het gebruik van deze functie:  

    -   Azure Active Directory Premium-abonnement en AD FS-synchronisatie.  

    -   Een Microsoft Intune-abonnement. De Microsoft Intune-abonnement moet worden geconfigureerd in Configuration Manager-Console.  

    -   [Vereisten voor Azure AD automatische registratie](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    Voor het gebruik van de optie moet u een nalevingsbeleid maken in Configuration Manager met specifieke regels die hieronder worden beschreven en beleid voor voorwaardelijke toegang instellen in de Intune-console.  Bovendien om er zeker van te zijn uitsluitend compatibel pc's toegang hebben, stelt u de vereiste Windows-PC op **apparaten moeten compatibel zijn** optie. Hieronder vindt u de compatibel beleidsregels die van toepassing op pc's die worden beheerd door System Center Configuration manager zijn.  

    -   **Registratie in Azure Active Directory vereisen:** Deze regel controleert of het apparaat van de gebruiker is werk plaats lid zijn van Azure AD en als dat niet het apparaat automatisch wordt geregistreerd in Azure AD. Automatische inschrijving wordt alleen ondersteund op Windows 8.1. Implementeer een MSI-bestand om automatische inschrijving voor Windows 7-pc's uit te voeren. Zie voor meer informatie [hier](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    -   **Alle vereiste updates zijn geïnstalleerd met een deadline die ouder zijn dan een bepaald aantal dagen:** Deze regel controleert om te zien of apparaat van de gebruiker alle heeft vereiste updates (opgegeven in de **vereiste automatische updates** regel) binnen de deadline en de respijtperiode is opgegeven door u en automatisch eventuele vereiste updates installeren.  

    -   **BitLocker-stationsversleuteling vereisen:** Dit is een selectievakje om te controleren of de primaire schijf (bijvoorbeeld C:\\) op het apparaat wordt BitLocker versleuteld. Als Bitlocker-versleuteling niet is ingeschakeld op het primaire station, wordt de toegang tot e-mail en SharePoint-services geblokkeerd.  

    -   **Antimalware vereisen:** Dit is een selectievakje om te controleren of de antimalware-software (System Center Endpoint Protection of alleen Windows Defender) is ingeschakeld en worden uitgevoerd.  
         Indien dit niet is ingeschakeld, wordt de toegang tot e-mail en SharePoint-services geblokkeerd.  

    Eindgebruikers die zijn geblokkeerd vanwege niet-naleving wordt compatibiliteitsinformatie weergeven in de SCCM Software Center en wordt een nieuwe evaluatie van beleid initiëren wanneer de nalevingsproblemen zijn hersteld.  

-   **Voorwaardelijke toegang met Attestation statusservice** kunt u nu toegang tot e-mail en 0365 services op basis van de status van de apparaten, zoals gemeld door de Attestation-statusservice beperken.  Daarnaast worden apparaten die worden beheerd door Intune opgenomen in de rapporten van de status van apparaat.  

    Een nieuwe regel voor naleving is toegevoegd aan de configuration manager-console u opgeven kunt als de apparaten moeten worden toegestaan of geblokkeerd op basis van hun gezondheidsstatus toegang.  Als u deze regel maakt, opent u de **maken compatibiliteit Wizard beleid voor**, en voeg een nieuwe regel toe.  Selecteer de **gerapporteerd als health door Attestation statusservice** voor de voorwaarde, en stel de waarde op **waar**.  Zorgt ervoor dat alleen apparaten die zijn gerapporteerd goede status toegang tot uw bedrijfsbronnen hebben. Zie voor meer informatie over Health Attestation-Service en hoe de status van de apparaten in Intune wordt gerapporteerd, [apparaat Health Attestation](#bkmk_devicehealth).  

-   **Nieuwe naleving beleidsinstellingen:** De nieuwe instellingen voor naleving te verbeteren van beveiligings- en op apparaten die worden gebruikt voor toegang tot bedrijfse-mail en SharePoint services:  

    -   **Automatische updates vereisen:** U kunt apparaten met Windows 8.1 of hoger nodig hebt om automatische installatie van updates toestaan en geef ook op de klasse van updates die zijn geïnstalleerd.  U kunt kiezen om te: installatie van alleen de updates die zijn gemarkeerd als belangrijk of alle aanbevolen updates.  

         Openen voor het maken van een regel voor automatische updates, de **maken compatibiliteit Wizard beleid voor**, en voeg een nieuwe regel toe.  Selecteer **minimale classificatie van de vereiste updates** als de voorwaarde, en de waarde op een van de beschikbare waarden: **Geen**, **aanbevolen**, en **belangrijke**.  

        -   **Geen:** Updates worden niet automatisch geïnstalleerd.  

        -   **Aanbevolen:** Alle aanbevolen updates zijn geïnstalleerd  

        -   **Belangrijk:** Alleen de updates die zijn geclassificeerd als belangrijk worden geïnstalleerd.  

    -   **Wachtwoord vereisen voor het ontgrendelen van mobiele apparaten:** Als deze instelling is ingesteld op **Ja**, de eindgebruikers een wachtwoord moeten invoeren voordat ze toegang krijgen hun apparaat tot.  

         Openen voor het maken van een regel voor het wachtwoord voor het ontgrendelen van mobiele apparaten, de **maken compatibiliteit Wizard beleid voor**, en voeg een nieuwe regel toe. Selecteer **wachtwoord vereist voor een niet-actieve apparaat hebt ontgrendeld** als de voorwaarde, en stel de waarde op **waar**.  

    -   **Minuten van inactiviteit voordat wachtwoord vereist is:**  Hiermee geeft u aan na hoeveel niet-actieve tijd gebruikers hun wachtwoord opnieuw moeten invoeren.  

         Als u deze regel maakt, opent u de **maken compatibiliteit Wizard beleid voor**, en voeg een nieuwe regel toe. **Selecteer minuten van inactiviteit voordat wachtwoord vereist is** als de voorwaarde, en de waarde op een van de beschikbare opties: 1 minuut, 5 minuten, 15, 30 minuten ik uur.  

-   **Onderdrukking van de regel standaard - Intune geregistreerd en compatibele apparaten toegang tot Exchange on-premises altijd toestaan:**  

     Als u deze optie inschakelt, worden apparaten die zijn ingeschreven in Intune en voldoet aan het nalevingsbeleid voor toegang tot Exchange on-premises toegestaan. Deze regel overschrijft de standaardregel, wat inhoudt dat zelfs als u de standaardregel in quarantaine worden geplaatst of de toegang blokkeren ingeschreven en compatibele apparaten worden nog steeds toegang tot Exchange on-premises.  
     Gebruik deze instelling als u wilt ingeschreven en compatibele apparaten altijd toegang tot e-mail via Exchange lokale hebben.  

     Dit wordt ondersteund door de volgende platforms:  Windows Phone 8 en hoger, iOS 6 en hoger. Android 4.0 en hoger, Samsung KNOX Standard 4.0 of hoger.  

     Om deze optie gebruikt, gaat u naar de **algemeen** pagina van de **configureren voorwaardelijke toegang Wizard beleid voor** voor Exchange on-premises.  

##  <a name="bkmk_clientStatus"></a>Online clientstatus  
Technische preview 1601 vanaf, kunt u identificeren in één oogopslag of een client online of offline zijn in de Configuration Manager-console is. Bijgewerkte pictogrammen en kolommen in de console apparaat aanbiedingen bepaalt u de status van clients in uw omgeving om probleemgebieden en andere problemen die uw aandacht mogelijk te identificeren.  

Een client is online als deze momenteel is verbonden met een Configuration Manager management sitesysteemrol. Als het beheerpunt ping-achtige berichten van de client ontvangen is, wordt de status online is. Als het management een voor 5 minuten bericht heeft niet, wordt de status van de client gewijzigd naar offline.  

### <a name="icons-for-client-status"></a>Pictogrammen voor de clientstatus  

|||  
|-|-|  
|![online-statuspictogram voor clients](media/online-status-icon.png)|Client is online.|  
|![offline-statuspictogram voor clients](media/offline-status-icon.png)|Client is offline.|  
|![onbekende-statuspictogram voor clients](media/unknown-status-icon.png)|Status van de client is onbekend.|  

### <a name="prerequisites"></a>Vereisten  
 Online status van de client heeft geen vereisten. U kunt starten met behulp van deze zo technische preview van Configuration Manager 1601 is geïnstalleerd.  

### <a name="limitations"></a>Beperkingen  
 Online status van de client is alleen beschikbaar voor Windows-computers met de Configuration Manager-client is geïnstalleerd. Online status van de client wordt niet ondersteund voor Mac-computers, Linux of UNIX-computer of apparaten die worden beheerd met op\-premises beheer van mobiele apparaten.  

### <a name="to-view-client-online-status"></a>Client online status weergeven  

1.  Ga in de Configuration Manager-console naar **activa en naleving > overzicht > apparaten**.  

2.  Met de rechtermuisknop op de kolomkop en klik vervolgens op een van de client onlinestatus velden toe te voegen aan het apparaat weergeven. De velden zijn  

    -   **Onlinestatus van het apparaat** geeft aan of de client op dit moment online of offline is.  

    -   **Online-tijd van recentste** geeft aan wanneer de client online status is gewijzigd van offline om online.  

    -   **Offline-tijd van recentste** geeft aan wanneer de status is gewijzigd van online offline.  

 Om aan te geven recente wijzigingen aan de status van de client, vernieuw de console.  

##  <a name="bkmk_appmgmt1601"></a>Verbeteringen voor toepassingsbeheer  
 In de 1601 Technical Preview hebben we toegevoegde ondersteuning voor de volgende functies:  

### <a name="manage-volume-purchased-apps-for-ios-devices"></a>Volume-purchased apps voor iOS-apparaten beheren  
 Sommige zogeheten app stores geven u meerdere licenties koopt voor een app die u wilt uitvoeren in uw bedrijf. Zodoende kunt u de administratieve overhead voor het bijhouden reduceren als u meerdere exemplaren van apps hebt aangeschaft.  

 Configuration Manager nu helpt u bij het beheren van apps die u hebt aangeschaft via zo'n programma door de licentiegegevens uit de appstore en bijhouden hoeveel van de licenties die u hebt gebruikt.  

 Zie voor meer informatie, [apps die u hebt aangeschaft via een programma volume aankoop met Configuration Manager beheren](https://technet.microsoft.com/library/mt627954.aspx).  

### <a name="ios---app-configuration-for-applicationsbr-hybrid"></a>iOS - App-configuratie voor toepassingen<br />Hybride  
 Sommige iOS-toepassingen ondersteunen het vooraf configureren van instellingen, zoals een server of database waarmee de toepassing verbinding moet maken. Configuration Manager ondersteunt nu implementeren app configuratiebeleid op het apparaat waarmee de gebruiker met de app aan onmiddellijk zonder te weten. Ontwikkelaars moeten deze functie in hun apps inschakelen.  

 Een beperkt aantal openbaar vrijgegeven apps ondersteund momenteel vooraf configuratie instellingen; u mogelijk ook hebt intern ontwikkelde line-of-business-apps die ondersteuning bieden voor deze.  

#### <a name="prerequisites-for-this-scenario"></a>Vereisten voor dit scenario  

-   U moet hebt toegevoegd een abonnement op Microsoft Intune naar Configuration Manager.  

-   U moet hebt een geldig certificaat voor Apple APNs toegevoegd aan het Intune-abonnement.  

-   U moet een toepassing voor iOS die ondersteuning biedt voor Toepassingsconfiguratie hebt geïmplementeerd.  

#### <a name="try-it-out"></a>Probeer het nu!  
 Als de bovenstaande vereisten wordt voldaan, moet u een Configuration Manager-toepassing die gebruikmaakt van een iOS-implementatietype maken. De app die u moet de toepassingsconfiguratie ondersteunen. Raadpleeg de documentatie van de leverancier van de toepassing voor informatie over welke specifieke items (naam/waarde-paren), maar u kunt configureren.  

 Vervolgens koppelt u het configuratiebeleid app aan het implementatietype iOS tijdens de implementatie van de app. U kunt ook implementeren met het beleid van de **App configuratiebeleid** knooppunt gericht op een bestaande app en de verzameling.  

 Probeer de volgende taken uitvoeren en vervolgens de feedbackgegevens boven in dit onderwerp gebruiken om te laat ons weten hoe ze besteed:  

-   Als u een iOS-app die ondersteuning biedt voor configuratie van app hebt, raadpleegt u de documentatie van de leverancier van de app als u wilt weten de naam en waarde-paren dat u moet opgeven voor het configureren van de toepassing.  

-   Start de **App configuratiebeleid maken** wizard. Op de **iOS-beleid** van de wizard probeer toevoegen van een XML-bestand met de vereiste waarden door de naam en waarde-paren u in de documentatie van de leverancier van de app of u gevonden kunnen importeren.  

-   In de **Software distribueren** wizard, op de **App configuratiebeleid** pagina, het app-configuratiebeleid die u hebt gemaakt met een compatibele implementatietype van de toepassing koppelen.  

##  <a name="bkmk_compliance1601"></a>Verbeteringen in de instellingen voor naleving  
 In de 1601 Technical Preview hebben we toegevoegde ondersteuning voor de volgende functies:  

### <a name="microsoft-edge-browser-settings"></a>Microsoft Edge browserinstellingen  
 Nieuwe instellingen voor de browser Microsoft Edge zijn toegevoegd aan de **Windows 8.1 en Windows 10** configuratie-item (instellingen van toepassing op Windows 10-apparaten).  

 Kies een overzicht van de nieuwe instellingen **Microsoft Edge** van de configuratie-item **apparaatinstellingen** pagina van de **configuratie-Item maken** wizard.  

 Zie voor meer informatie [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten beheerd zonder dat de System Center Configuration Manager-client](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="compliance-settings-for-windows-10-team-devices"></a>Compatibiliteitsinstellingen voor Windows 10 Team-apparaten  
 Deze nieuwe compatibiliteitsinstellingen gebruiken om apparaten met Windows 10 team, zoals oppervlak Hub-apparaten te configureren.  

 Kies een overzicht van de nieuwe instellingen **Windows 10 Team** van de configuratie-item **apparaatinstellingen** pagina van de **configuratie-Item maken** wizard.  

 Zie voor meer informatie [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten beheerd zonder dat de System Center Configuration Manager-client](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="android---kiosk-mode-for-samsung-knox-standardbr-hybrid"></a>Android - kioskmodus voor Samsung KNOX Standard<br />Hybride  
 Kioskmodus kunt u een apparaat zo vergrendelen dat alleen bepaalde functies werken. U kunt bijvoorbeeld toestaan dat een apparaat slechts één beheerde app uitvoert die u opgeeft, of kunt u de volumeknoppen op een apparaat uitschakelen. Deze instellingen kunnen worden gebruikt voor een demonstratiemodel van een apparaat of voor een apparaat dat is toegewezen aan slechts één functie, zoals een verkooppuntapparaat. Deze instellingen zijn niet beschikbaar voor Samsung KNOX Standard-apparaten in de **Windows 8.1 en Windows 10** configuratie-item (instellingen van toepassing op Windows 10-apparaten).  

 Kies een overzicht van de nieuwe instellingen **kioskmodus - Samsung KNOX** van de configuratie-item **apparaatinstellingen** pagina van de **configuratie-Item maken** wizard.  

 Zie voor meer informatie [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten beheerd zonder dat de System Center Configuration Manager-client](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

