---
title: Nieuwe versie 1706
titleSuffix: Configuration Manager
description: "Meer informatie over deze wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1706 van System Center Configuration Manager."
ms.custom: na
ms.date: 08/11/2017
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac034143-003e-4629-aac2-99eaffef4db1
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 2889de0709096aa481ca6203c5ab2bac1f064d5e
ms.sourcegitcommit: c4a1bafcd004638d264a93d307c70d8b6f7fe023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/20/2017
---
# <a name="what39s-new-in-version-1706-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1706 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1706 voor de huidige vertakking van System Center Configuration Manager is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1606, 1610 of 1702 uitgevoerd.

> [!TIP]  
> Een nieuwe site te installeren, moet u een basislijnversie van Configuration Manager.  
>  Meer informatie over:    
>   - [Nieuwe sites installeren](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Updates installeren op sites](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Basislijn- en updateversies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1706 van Configuration Manager.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated features](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Version 1706 drops support for the following products:
-->


## <a name="site-infrastructure"></a>Site-infrastructuur

### <a name="client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365"></a>Client-Peer-Cache-ondersteuning voor bestanden voor snelle installatie voor Windows 10 en Office 365  
<!-- 1352486 -->
Peer-Cache ondersteunt vanaf deze release distributie van inhoud snelle installatiebestanden voor Windows 10 en van updatebestanden voor Office 365. Er is geen aanvullende configuraties die vereist zijn ter ondersteuning van deze wijziging.

### <a name="updates-for-the-data-warehouse"></a>Updates voor het datawarehouse
<!-- 1277922 -->
Het datawarehouse is niet langer een functie van de voorlopige versie. We hebben ook de vereisten voor onder meer ondersteuning voor de database op SQL Server altijd op beschikbaarheidsgroepen en failover-clusters bijgewerkt. Zie voor meer informatie [The Data Warehouse-servicepunt](/sccm/core/servers/manage/data-warehouse).

### <a name="accessibility-improvements"></a>Verbeterde toegankelijkheid
<!-- 1253000 -->
Toegankelijkheid voor de Configuration Manager-console, hebben we extra verbeteringen toegevoegd. Zie voor meer informatie [toegankelijkheidsfuncties](/sccm/core/understand/accessibility-features).

### <a name="improvements--for-sql-server-always-on-availability-groups"></a>Verbeteringen voor SQL Server altijd op beschikbaarheidsgroepen
<!-- 1352094 -->
Met deze release kunt u nu asynchrone doorvoer replica's in de SQL Server Always On availability groepen die u met Configuration Manager gebruikt gebruiken. Dit betekent dat u kunt extra replica's toevoegen aan uw beschikbaarheidsgroepen wilt gebruiken als externe (extern) back-ups en gebruik ze in een noodherstelscenario.  
  -   Configuration Manager ondersteunt de synchrone replica herstellen met behulp van de replica met asynchrone doorvoer. Zie [opties voor herstel van site](/sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption) in het onderwerp back-up en herstel voor meer informatie over om dit te bereiken.
  -   Deze versie biedt geen ondersteuning voor failover voor het gebruik van de replica met asynchrone doorvoer als uw sitedatabase.
Zie voor meer informatie [bereidt het gebruik van AlwaysOn-beschikbaarheidsgroepen](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

### <a name="update-reset-tool"></a>Hulpprogramma voor het bijwerken opnieuw instellen
<!-- 1324589 -->
Vanaf versie 1706, primaire Configuration Manager-sites en centrale beheersites omvatten het hulpprogramma Configuration Manager-Update opnieuw instellen, **CMUpdateReset.exe**. Dit hulpprogramma gebruiken met een willekeurige versie van de huidige vertakking dat in ondersteuning resteert voor het oplossen van problemen wanneer updates in de console hebben problemen met het downloaden of repliceren. Zie voor meer informatie [Update opnieuw instellen van hulpprogramma](/sccm/core/servers/manage/update-reset-tool).

### <a name="high-dpi-console-support"></a>Hoge DPI-ondersteuning  
<!-- 1353476 -->
Met deze release, moeten problemen met hoe de Configuration Manager-console wordt geschaald en geeft verschillende onderdelen van de gebruikersinterface weergegeven op hoge DPI-apparaten (zoals een boek Surface) worden hersteld.

### <a name="improved-boundary-groups-for-software-update-points"></a>Verbeterde grensgroepen voor software-updatepunten
<!-- 1324591 -->
Deze release bevat verbeteringen voor de werking van software-updatepunten aan grensgroepen. Het volgende bevat een overzicht van het nieuwe terugval gedrag:
-   Opvang voor software-updatepunten gebruikt een configureerbare tijd nu voor terugvallen neighbor grensgroepen.
-   Onafhankelijk van de alternatieve configuratie probeert een client te bereiken van het laatste software-updatepunt dat wordt gebruikt voor 120 minuten. Lukt die server bereiken gedurende 120 minuten, controleert de client vervolgens de groep met beschikbare software-updatepunten, zodat deze een nieuw kan vinden.
-   Na een failover naar de oorspronkelijke server te bereiken voor twee uur, wordt de client overschakelt naar een kortere cyclus voor het verbinden met een nieuw software-updatepunt. Dit betekent dat als een client geen verbinding maken met een nieuwe server, het snel de volgende server selecteert in de groep met beschikbare servers en probeert contact dat een.

Zie voor meer informatie [software-updatepunten](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) in het onderwerp Grensgroepen voor de huidige vertakking.

### <a name="azure-ad-integration-with-configuration-manager"></a>Azure AD-integratie met Configuration Manager
<!-- 1248187, 1290765, 1258052, 1298097, 1319334, 1319883, 1352135, 1353331 -->
Met deze release, hebben we de integratie van Configuration Manager en Azure Active Directory (Azure AD) verbeterd.  Deze verbeteringen stroomlijnen hoe u de Azure-services die u met Configuration Manager gebruikt configureren en helpt u bij het beheren van clients en gebruikers die worden geverifieerd via Azure AD.

Verbeterde integratie maakt het volgende mogelijk:  
  -   Wizard Azure Services – met deze Wizard biedt een algemene configuratie-ervaring die wordt vervangen door de afzonderlijke werkstromen voor het instellen van de volgende Azure-services die u met Configuration Manager gebruikt.
      - **Beheer cloud** inschakelen voor clients te verifiëren met behulp van Azure Active Directory (Azure AD). U kunt ook Azure AD-Gebruikersdetectie configureren.
      - **OMS Connector** verbinding maken met Operations Manager-pakket (OMS) en sync gegevens, zoals verzamelingen met OMS-logboekanalyse.
      - **Gereedheid voor upgrade** verbinding maken met de gereedheid voor Upgrade en bekijk upgradecompatibiliteit clientgegevens.
      - **Windows Store voor bedrijven** verbinding maken met de online winkel voor Windows Store voor bedrijven en get-apps voor uw organisatie die u kunt implementeren met Configuration Manager.


  Dit wordt gedaan met behulp van een [web-app van Azure-server](/azure/azure/app-service/app-service-authentication-overview#service-to-service-authentication) om het abonnement en configuratie details die u anders telkens wanneer u een nieuwe Configuration Manager-component of de service met Azure instellen te verstrekken. Zie voor meer informatie [Wizard Azure-Services](/sccm/core/servers/deploy/configure/azure-services-wizard).

-   Azure AD voor verificatie van clients op het Internet toegang krijgen tot uw sites van Configuration Manager gebruiken. Azure AD vervangt de noodzaak om te configureren en gebruiken van certificaten voor clientverificatie. Hiervoor moet de cloud management gateway-sitesysteemrol. Zie voor meer informatie [installeren en toewijzen van Configuration Manager-clients via Internet met behulp van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

-   Installeren en beheren van de Configuration Manager-client op computers die zich op Internet bevinden. Hiervoor moet het gebruik van de cloud management gateway-sitesysteemrol. Zie voor meer informatie [installeren en toewijzen van Configuration Manager-clients via Internet met behulp van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

-   Azure AD-Gebruikersdetectie configureren.  Gebruik de Wizard Azure-Services voor het configureren van deze nieuwe detectiemethode. Deze nieuwe methode query's voor uw Azure AD voor gebruikersgegevens kunt u vervolgens aan clientzijde langs traditionele discovery-gegevens te gebruiken.  Volledige installatie en delta-synchronisatie worden ondersteund.  Zie voor meer informatie [Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

### <a name="peer-cache-improvements"></a>Verbeteringen voor peer-cache
<!-- 1252345 -->
Het netwerktoegangsaccount peer-cache niet langer gebruikt voor verificatie van aanvragen voor het downloaden van peers. Er is een voorbehoud aan dit wanneer de blijft account voor clients vereist. Dit blijft een vereiste voor clients die WinPE opstart en vervolgens toegang tot inhoud van peer-cachebron. Zie voor meer informatie [vereisten en overwegingen voor peer-cache](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements-and-considerations-for-peer-cache).


<!-- ## Migration  -->


<!-- ## Client management  -->


## <a name="compliance-settings"></a>Instellingen voor naleving

### <a name="new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client"></a>Nieuwe configuratie-instellingen voor Windows 10-apparaten die niet worden beheerd met Configuration Manager-client
<!-- 1354715 -->
In deze release toegevoegd nieuwe configuratie-iteminstellingen voor Windows 10-apparaten die zijn ingeschreven bij Intune of die on-premises worden beheerd door Configuration Manager. De instellingen zijn:

- **Wachtwoord**
    - Apparaatversleuteling
- **Apparaat**
    - Wijziging regio (alleen desktop)
    - Wijziging van kracht en slaapstand-instellingen
    - Taal instellingen aanpassen
    - Aanpassing van het systeem tijd
    - Naam wijzigt van apparaat
- **Store**
    - Automatische updates store-apps
    - Gebruik alleen persoonlijke archief
    - Starten van de oorsprong app Store
- **Microsoft Edge**
    - Toegang tot informatie over blokkeren: vlaggen
    - Het SmartScreen-prompt overschrijven
    - Het SmartScreen-prompt overschrijven voor bestanden
    - WebRTC localhost-IP-adres
    - Standaardzoekmachine
    - OpenSearch XML-URL
    - Startpagina's (alleen desktop)

Zie voor meer informatie over instellingen voor alle Windows 10, [het maken van configuratie-items voor Windows 8.1 en Windows 10-apparaten worden beheerd zonder de System Center Configuration Manager-client](/sccm/mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).

### <a name="new-device-compliance-policy-rules"></a>Nieuwe beleidsregels voor naleving van apparaat

* **Vereist Wachtwoordtype**. Geef op of de gebruiker een alfanumeriek wachtwoord of een numerieke wachtwoord moet maken. Voor alfanumerieke wachtwoorden, moet u ook het minimum aantal tekensets opgegeven waaruit het wachtwoord moet opgeven. De vier tekensets zijn: Kleine letters, hoofdletters, symbolen en cijfers.

 **Ondersteund op:**
 * Windows Phone 8+
 * Windows 8.1 +
 * iOS 6+
<br></br>
* **Blok USB-foutopsporing op apparaat**. U beschikt niet over deze instellingen configureren, zoals USB-foutopsporing is al uitgeschakeld op Android voor Work-apparaten.

 **Ondersteund op:**
 * Android 4.0+
 * Samsung KNOX Standard 4.0+
<br></br>
* **Blokkeren van apps van onbekende bronnen**. Vereisen dat de installatie van apps van onbekende bronnen worden voorkomen. U beschikt niet over deze instelling wilt configureren als Android voor werk apparaten altijd installatie vanuit onbekende bronnen beperken.

  **Ondersteund op:**
  * Android 4.0+
  * Samsung KNOX Standard 4.0+
<br></br>
* **Threat moeten worden gescand op apps**. Deze instelling geeft aan dat de functie van de apps controleren is ingeschakeld op het apparaat.

 **Ondersteund op:**
 * Android 4.2 via 4.4
 * Samsung KNOX Standard 4.0+

Zie [maken en implementeren van een nalevingsbeleid voor apparaten](https://docs.microsoft.com/sccm/mdm/deploy-use/create-compliance-policy) om te proberen het nieuwe apparaat naleving van regels

## <a name="application-management"></a>Toepassingsbeheer

### <a name="run-powershell-scripts-from-the-configuration-manager-console"></a>PowerShell-scripts uitvoeren vanaf de Configuration Manager-console
<!-- 1236459 -->

In Configuration Manager kunt u scripts voor clientapparaten die pakketten en programma's implementeren. In deze release toegevoegd nieuwe functionaliteit waarmee u de volgende acties uitvoeren:

- PowerShell-Scripts importeren naar Configuration Manager
- De scripts van de Configuration Manager-console (voor niet-ondertekende scripts alleen) bewerken
- Scripts markeren als goedgekeurd of geweigerd, de beveiliging te verbeteren
- Scripts uitvoeren op verzamelingen van Windows client-pc's en lokale beheerde Windows-pc's. U kunt scripts niet implementeren, in plaats daarvan ze in bijna realtime worden uitgevoerd op clientapparaten.
- Bekijk de resultaten geretourneerd door het script in de Configuration Manager-console.

Zie voor meer informatie [maken en uitvoeren van PowerShell-scripts uit de Configuration Manager-console](/sccm/apps/deploy-use/create-deploy-scripts).

### <a name="new-mobile-application-management-policy-settings"></a>Nieuwe beleidsinstellingen voor mobile application management    
<!--1324760-->
Vanaf deze versie, kunt u drie nieuwe beleidsinstellingen voor mobile application management (MAM):

- **Schermafbeelding (alleen Android-apparaten) blokkeren:** Hiermee wordt opgegeven dat de schermafbeeldingsmogelijkheden van het apparaat zijn geblokkeerd bij gebruik van deze app.

Zie [apps beveiligen met beleid voor app-beveiliging in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/protect-apps-using-mam-policies) om te proberen de nieuwe beleidsinstellingen van de app-beveiliging.


## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen

### <a name="hardware-inventory-collects-secure-boot-information"></a>Hardware-inventaris verzamelt gegevens van beveiligd opstarten
Hardware-inventaris verzamelt nu informatie over of beveiligd opstarten is ingeschakeld op clients. Deze informatie wordt opgeslagen in de **SMS_Firmware** klasse (geïntroduceerd in versie 1702) en ingeschakeld in hardware-inventarisatie standaard. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

### <a name="collapsible-task-sequence-groups"></a>Samenvouwbare takenreeksgroepen
Deze versie bevat de mogelijkheid om takenreeksgroepen samenvouwen uit te vouwen. U kunt uitvouwen of samenvouwen afzonderlijke groepen of groepen uitvouwen of samenvouwen alle tegelijk.

### <a name="reload-boot-images-with-current-windows-pe-version"></a>Laden van installatiekopieën voor opstarten met huidige Windows PE-versie
Bij het uitvoeren van **distributiepunten bijwerken** op een geselecteerde opstartinstallatiekopie, kunt u nu kiezen om opnieuw te laden van de nieuwste versie van Windows PE (van de installatiemap van Windows ADK) in de opstartinstallatiekopie. Zie voor meer informatie [distributiepunten bijwerken met de installatiekopie](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image).

## <a name="software-updates"></a>Software-updates

### <a name="improvements-to-express-update-download-time"></a>Verbeteringen in de Express-Update downloadtijd
In deze release, hebben we de downloadtijd aanzienlijk verbeterd voor Express-Updates. Zie voor meer informatie [installatiebestanden beheren Express voor Windows 10-updates](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).

### <a name="manage-microsoft-surface-driver-updates"></a>Updates voor Microsoft Surface stuurprogramma's beheren
<!-- 1098490 -->
U kunt nu de Configuration Manager gebruiken voor het beheren van updates voor Microsoft Surface stuurprogramma's.    


#### <a name="prerequisites"></a>Vereisten
- Alle software-updatepunten moeten Windows Server 2016 worden uitgevoerd.    
- Dit is een voorlopige versie-functie die u moet inschakelen voor deze beschikbaar zijn. Zie [Use pre-release features from updates](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease) (Functies van evaluatieversies gebruiken) voor meer informatie.

#### <a name="to-manage-surface-driver-updates"></a>Voor het beheren van updates voor Surface stuurprogramma 's

1. Synchronisatie voor Microsoft Surface stuurprogramma's inschakelen. Gebruik de procedure in [classificaties en producten configureren](/sccm/sum/get-started/configure-classifications-and-products) en selecteer de **opnemen Microsoft Surface stuurprogramma's en firmware-updates** selectievakje op het **classificaties** tabblad Surface stuurprogramma's inschakelen.
2. [De Microsoft Surface stuurprogramma's synchroniseren](/sccm/sum/get-started/synchronize-software-updates).
3. [Gesynchroniseerde Microsoft Surface stuurprogramma's implementeren](/sccm/sum/deploy-use/deploy-software-updates)

### <a name="configure-windows-update-for-business-deferral-policies"></a>Windows Update voor bedrijven uitgestelde beleid configureren
<!-- 1290890 -->
U kunt nu uitgestelde beleidsregels voor Windows 10-functie-Updates of Quality-Updates voor Windows 10-apparaten rechtstreeks beheerd door Windows Update voor bedrijven configureren. U kunt de uitgestelde beleidsregels beheren in de nieuwe **Windows Update voor bedrijven-beleid** knooppunt onder **softwarebibliotheek** > **onderhoud van Windows 10**.

Zie voor meer informatie [integratie met Windows Update voor bedrijven in Windows 10](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies).

### <a name="improved-user-notifications-for-office-365-updates"></a>Verbeterde berichten van de gebruiker voor Office 365-updates
Voor het benutten van de gebruikerservaring Office Klik-en-klaar wanneer een client wordt geïnstalleerd voor een update voor Office 365 zijn verbeteringen aangebracht. Dit omvat pop- en in-app-meldingen en een aftelvenster weergegeven-ervaring. Zie voor meer informatie [meldingen gedrag en de client opnieuw opstarten voor Office 365-updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates#restart-behavior-and-client-notifications-for-office-365-updates)

## <a name="reporting"></a>Rapporten

### <a name="use-windows-analytics-with-configuration-manager"></a>Windows-Analytics gebruiken met Configuration Manager
<!-- 1318608 -->
Windows Analytics is een set van oplossingen die worden uitgevoerd op de Operations Management Suite. De oplossingen kunnen u formulier inzicht in de huidige status van uw omgeving. Apparaten in uw omgeving rapporteren Windows telemetrische gegevens. De gegevens zijn toegankelijk via de Operations Management Suite-webportal. In het geval van de gereedheid van de Upgrade is de gegevens direct beschikbaar is in het knooppunt controle van de Configuration Manager-console.

Zie voor meer informatie [Windows Analytics voor gebruik met Configuration Manager](/sccm/core/clients/manage/monitor-windows-analytics).


<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>Beheer van mobiele apparaten

### <a name="updates-to-android-for-work-sharing-configuration"></a>Updates voor Android for Work-configuratie voor delen
<!-- 1338403 -->
Met deze versie, de waarden voor de **toestaan gegevens delen tussen werk en persoonlijk profiel** instellen in de **werkprofiel** instellen van de groep zijn bijgewerkt. Een aangepaste instellen om te kopiëren en plakken tussen werk en persoonlijke profielen blokkeren ook toegevoegd.

Zie voor meer informatie [configuratie-items voor Android voor werk apparaten](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client).

### <a name="android-and-ios-enrollment-restrictions"></a>Beperkingen voor android en iOS-inschrijving
<!-- 1290826 -->
Met deze release kunt u nu opgeven dat gebruikers persoonlijke Android- of iOS-apparaten kunnen niet registreren. Instellingen voor nieuwe apparaten beperking kunnen u Android-apparaat van de inschrijving predeclared apparaten beperken. Voor iOS-apparaten kunt u de registratie van alle apparaten met uitzondering van de ingeschreven met Apple Device Enrollment Program, Apple Configurator of het account apparaatinschrijvingsmanager Intune blokkeren.
- Zie voor meer informatie over Android-inschrijving beperkingen [Android device management instellen](/sccm/mdm/deploy-use/enroll-hybrid-android).
- Zie voor meer informatie over de beperkingen van de iOS-inschrijving [beperkingen voor iOS-inschrijving configureren](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac#configure-enrollment-restrictions).

## <a name="protect-devices"></a>Apparaten beveiligen

### <a name="include-trust-for-specific-files-and-folders-in-a-device-guard-policy"></a>Vertrouwen voor specifieke bestanden en mappen in een beleid Device Guard opnemen
<!--1324676-->
In deze release toegevoegd meer mogelijkheden voor beheer van Device Guard.

U kunt vertrouwen voor specifieke bestanden of mappen nu desgewenst toevoegen in een beleid Device Guard. Hiermee kunt u:

- Problemen oplossen met beheerd installatieprogramma gedrag
- Vertrouwensrelatie van LOB-apps die met Configuration Manager kunnen niet worden geïmplementeerd
- Vertrouwen van apps die zijn opgenomen in de installatiekopie van een besturingssysteem-implementatie

Zie voor meer informatie [Device Guard management met Configuration Manager](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager).
