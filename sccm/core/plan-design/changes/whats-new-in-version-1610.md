---
title: Nieuwe versie 1610 | Microsoft-documenten
description: "Meer informatie over deze wijzigingen en nieuwe functies die zijn geïntroduceerd in versie 1610 van System Center Configuration Manager."
ms.custom: na
ms.date: 11/23/2016
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7eb0803-3f8f-4ab6-825a-99ac11f5ba7d
caps.latest.revision: 40
author: Brenduns
ms.author: brenduns
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 831d8a66c827d246069c7415cdce7a7c4bb95b33
ms.openlocfilehash: 19e3099773f887129374413482702de3f4b0a36f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1610-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1610 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1610 voor System Center Configuration Manager huidige vertakking is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1511, 1602 of 1606.


> [!TIP]  
> Een nieuwe site installeren, moet u een basislijn-versie van Configuration Manager.  
>  Meer informatie over:    
>  -   [Installatie van nieuwe sites](https://technet.microsoft.com/library/mt590197.aspx)  
>  -   [Installatie van updates op sites](https://technet.microsoft.com/library/mt607046.aspx)  
>  -   [Basislijn en update-versies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die is geïntroduceerd in versie 1610 van Configuration Manager.  


## <a name="in-console-monitoring-of-update-installation-status"></a>Console bewaking van de status van de update-installatie  
Vanaf versie 1610, wanneer u een updatepakket te installeren en controleren van de installatie in de console, vindt u een nieuwe fase. **Na de installatie**. Deze stap bevat de status van taken, zoals het opnieuw opstarten van belangrijke services en initialisatie van de bewaking van replicatie. (Deze stap is niet beschikbaar in de console pas na de site-updates naar versie 1610.) Zie voor meer informatie over de installatiestatus van de update [-console updates installeren](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).


## <a name="exclude-clients-from-automatic-upgrade"></a>Clients uitsluiten voor automatische upgrade
U kunt Windows-clients uitsluiten van het ophalen van bijgewerkt met nieuwe versies van de clientsoftware. Om dit te doen, kunt u de clientcomputers opnemen in een verzameling die moeten worden uitgesloten van de upgrade is opgegeven. Clients in de verzameling uitgesloten negeren aanvragen voor het bijwerken van de clientsoftware.  Zie voor meer informatie [clients Windows uitsluiten van upgrades](../../clients/manage/upgrade/exclude-clients-windows.md).


## <a name="improvements-for-boundary-groups"></a>Verbeteringen voor grensgroepen
Versie 1610 introduceert belangrijke wijzigingen aan grensgroepen, en hoe ze werken met distributiepunten. Deze wijzigingen kunnen u het ontwerp van uw infrastructuur inhoud tijdens het doorgeven van meer controle over hoe en wanneer clients terugval om te zoeken naar aanvullende distributie als locatie van de inhoudsbron verwijst vereenvoudigen. Dit omvat zowel lokaal als cloud-gebaseerde distributiepunten.
Deze verbeteringen concepten en gedrag dat u bekend bent met (zoals het configureren van distributiepunten als snel of traag) worden vervangen. Het nieuwe model moet eenvoudiger instellen en onderhouden. Deze wijzigingen vast ook de basis leggen voor toekomstige wijzigingen die andere sitesysteemrollen die u aan grensgroepen koppelen verbeteren.

Wanneer u naar versie 1610 bijwerkt, zet de update voor uw huidige configuratie van de groep grens aan te passen van het nieuwe model zodat deze wijzigingen niet configuraties van uw bestaande distributie van inhoud storen.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#a-namebkmkboundarygroupsa-boundary-groups).


## <a name="peer-cache-for-content-distribution-to-clients"></a>Peercache voor de distributie van inhoud naar clients
Begin met versie 1610, client **Peercache** helpt u bij de implementatie van inhoud naar clients op externe locaties. Peercache is een ingebouwde Configuration Manager-oplossing voor clients inhoud te delen met andere clients, rechtstreeks vanuit de lokale cache.

Nadat u clientinstellingen die Peer-Cache op een verzameling inschakelen hebt geïmplementeerd, kunnen leden van deze verzameling fungeren als een peer-inhoudsbron voor andere clients in dezelfde grensgroep.

Bovendien kunt u de nieuwe **Client gegevensbronnen** dashboard om het gebruik van Peer Cache inhoudsbronnen in uw omgeving te begrijpen.

> [!TIP]  
> Peer-Cache en het dashboard van gegevensbronnen van de Client zijn versie 1610 pre-release functies. Als u wilt inschakelen, Zie [gebruikmaken van de functies van updates pre-release](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

Zie voor meer informatie [Peercache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache), en [Client gegevensbronnen dashboard](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).


## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Meerdere gedeelde distributiepunten op hetzelfde moment migreren
U kunt nu de optie voor het **opnieuw toewijzen van distributiepunt** gedeelde distributiepunten in de Configuration Manager-proces parallel het opnieuw toewijzen van maximaal 50 hebben op hetzelfde moment. Vóór deze release zijn opnieuw toegewezen distributiepunten verwerkte één voor één opnieuw. Zie voor meer informatie, [meerdere gedeelde distributiepunten op hetzelfde moment migreren](/sccm/core/migration/planning-a-content-deployment-migration-strategy#migrate-multiple-shared-distribution-points-at-the-same-time).

## <a name="cloud-management-gateway-for-managing-internet-based-clients"></a>Cloud management gateway voor het beheren van clients op Internet

Cloud management gateway biedt een eenvoudige manier voor het beheren van Configuration Manager-clients op het Internet. De cloud management gateway-service die wordt geïmplementeerd op Microsoft Azure en een Azure-abonnement vereist, maakt verbinding met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van het cloud-gateway verbinding beheerpunt. Zodra het is volledig geïmplementeerd en geconfigureerd, worden clients kunnen communiceren met de sitesysteemfuncties van Configuration Manager op locatie en cloud-gebaseerde distributiepunten ongeacht of ze naar het interne particulier netwerk of op het Internet zijn verbonden. Zie voor meer informatie en om te zien hoe cloud management gateway wordt vergeleken met de Internet-gebaseerd clientbeheer [beheren van clients op het Internet](/sccm/core/clients/manage/manage-clients-internet).

## <a name="improvements-to-the-windows-10-edition-upgrade-policy"></a>Verbeteringen in het upgradebeleid van de Windows 10-editie
In deze release zijn de volgende verbeteringen aangebracht in dit beleidstype:

- U kunt de upgrade beleid edition nu gebruiken met Windows 10-computers waarop de Configuration Manager-client naast Windows 10-computers die zijn ingeschreven met Microsoft Intune.
- U kunt upgraden van Windows 10 Professional met een van de platforms die compatibel met de hardware zijn in de wizard.

## <a name="manage-hardware-identifiers"></a>Hardware-id's beheren
U kunt nu een lijst van hardware-id's in Configuration Manager moeten worden genegeerd voor de PXE-opstart- en client registratie opgeven. Er zijn twee algemene problemen die dit bij het adres helpt:

1. Veel apparaten, zoals de 3 Surface Pro is een ingebouwde Ethernet-poort niet inbegrepen. Een USB-Ethernet-adapter wordt doorgaans gebruikt voor het implementeren van een besturingssysteem bekabelde verbinding te maken. Vanwege de kosten en algemene bruikbaarheid zijn echter vaak gedeelde adapters. Omdat het MAC-adres van deze adapter wordt gebruikt voor identificatie van het apparaat, wordt opnieuw gebruiken van de adapter problematische zonder extra beheerder acties tussen elke implementatie. Nu in Configuration Manager versie 1610, kunt u uitsluiten het MAC-adres van deze adapter zodat deze gemakkelijk kan worden gebruikt in dit scenario.
2. De SMBIOS-ID moet een unieke hardware-id zijn, maar sommige hardwareapparaten specialisatie zijn gebouwd met dubbele id. Dit probleem wordt mogelijk niet als algemene als het USB-Ethernet-adapter scenario zojuist hebben bekeken, maar u kunt dit oplossen met behulp van de lijst met uitgesloten hardware-id's.

Zie voor meer informatie, [dubbele hardware-id's beheren](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Uitbreidingen voor Windows Store voor Business-integratie met Configuration Manager
Wijzigingen in deze release:
- Eerder, kunt u gratis apps uit de Windows Store voor bedrijven alleen implementeren. Configuration Manager nu bovendien ondersteunt implementeren online betaalde licentie apps (voor Intune ingeschreven apparaten).
- U kunt nu een onmiddellijke synchronisatie tussen de Windows Store voor bedrijven en Configuration Manager te starten.
- Nu kunt u de client geheime sleutel die u hebt ontvangen van Azure Active Directory wijzigen.
- U kunt een abonnement op het archief verwijderen.

Zie voor meer informatie, [apps beheren vanuit de Windows Store voor bedrijven met System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


## <a name="policy-sync-for-intune-enrolled-devices"></a>Synchronisatie van beleid voor Intune zijn ingeschreven apparaten
U kunt nu een synchronisatie met beleid voor een Intune-ingeschreven apparaat aanvragen van de Configuration Manager-console in plaats van dat nodig is om aan te vragen van een synchronisatie van de bedrijfsportal-app op het apparaat zelf. Informatie over de status van de synchronisatie-aanvraag is beschikbaar als een nieuwe kolom in de apparaat-weergaven kunt genoemd **afstand synchronisatiestatus**. De informatie is ook beschikbaar in de sectie discovery data van de **eigenschappen** dialoogvenster voor elk apparaat.
Zie voor meer informatie, [beleid op Intune ingeschreven apparaten uit de Configuration Manager-console op afstand synchroniseren](/sccm/mdm/deploy-use/sync-intune-device).


## <a name="use-compliance-settings-to-configure-windows-defender-settings"></a>Compatibiliteitsinstellingen gebruiken voor Windows Defender-instellingen configureren
U kunt nu instellingen voor Windows Defender-client op Intune zijn ingeschreven Windows 10-computers configureren met behulp van configuratie-items in de Configuration Manager-console.
Zie voor meer informatie, de **Windows Defender** in sectie [configuratie-items maken voor Windows 8.1 en Windows 10-apparaten beheerd zonder dat de System Center Configuration Manager-client](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).



## <a name="general-improvements-to-software-center"></a>Algemene verbeteringen in Software Center
- Gebruikers kunnen nu apps vragen aan Software Center, evenals de Application Catalog.
- Verbeteringen aan gebruikers uitleggen welke software nieuwe en relevant is.

## <a name="new-columns-in-device-collection-views"></a>Nieuwe kolommen in apparaat verzameling weergaven
U kunt nu de weergeven kolommen voor **IMEI-nummer** en **serienummer** (voor iOS-apparaten) in apparaat verzameling weergaven.
Zie voor meer informatie [Predeclare apparaten met IMEI-nummer of iOS-serienummers](https://docs.microsoft.com/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id).

## <a name="customizable-branding-for-software-center-dialogs"></a>Aanpasbare huisstijl voor Software Center dialoogvensters
Aangepaste huisstijl voor het Software Center is ingevoerd in Configuration Manager versie 1602. In versie 1610 die branding nu uitgebreid tot alle bijbehorende dialoogvensters om een consistente ervaring voor gebruikers in Software Center.

Aangepaste huisstijl voor het Software Center wordt toegepast volgens de volgende regels:

- Als de Application Catalog-website-puntrol siteserver is niet geïnstalleerd en Software Center wordt vervolgens de organisatienaam die is opgegeven in de **Computeragent** clientinstelling **weergegeven organisatienaam in Software Center**. Zie voor instructies [het configureren van clientinstellingen](../../clients/deploy/configure-client-settings.md).

- Als de Application Catalog-website-puntrol siteserver is geïnstalleerd, worden Software Center de naam van de organisatie en kleur die is opgegeven in de Application Catalog-website site server-roleigenschappen. Zie voor meer informatie [configuratieopties voor de Application Catalog-websitepunt](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#Application-Catalog-website-point).

- Als een Microsoft Intune-abonnement is geconfigureerd en met de Configuration Manager-omgeving verbonden, geeft Software Center de naam van de organisatie, kleur en bedrijfslogo opgegeven in de eigenschappen van de Intune-abonnement. Zie [Het Windows Intune-abonnement configureren](/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription) voor meer informatie.


## <a name="enforcement-grace-period-for-required-application-and-software-update-deployments"></a>Respijtperiode afdwingen voor vereiste toepassingen en software-update-implementaties
In sommige gevallen is het raadzaam om gebruikers meer tijd voor implementaties van toepassingen installeren die zijn vereist of software-updates buiten een deadlines die u instelt. Bijvoorbeeld, kan dit noodzakelijk zijn wanneer een computer gedurende langere tijd is uitgeschakeld en moet het installeren van een groot aantal toepassing of update-implementaties. Als een eindgebruiker net van vakantie is geretourneerd, moeten ze mogelijk geduld voor een Long-waarde als achterstallig toepassing implementaties worden geïnstalleerd. Om te helpen bij het oplossen van dit probleem, kunt u nu een respijtperiode afdwinging definiëren door de instellingen voor Configuration Manager-client implementeren op een verzameling. 

De respijtperiode configureren, moet u de volgende acties uitvoeren:
1.      Op de **Computeragent** pagina configureren van instellingen van de client de nieuwe eigenschap **respijtperiode voor afdwinging na implementatie deadline (uren)** met een waarde tussen **1** en **120** uur.
2.      In een nieuwe implementatie van de vereiste toepassing, of in de eigenschappen van een bestaande implementatie op de **planning** pagina, schakel het selectievakje **stellen afdwinging van deze implementatie volgens gebruikersvoorkeuren tot de respijtperiode gedefinieerd in de clientinstellingen**. De respijtperiode afdwinging maakt gebruik van alle implementaties met dit selectievakje is ingeschakeld en zijn bedoeld voor apparaten waarop u de clientinstelling ook hebt geïmplementeerd.

Als u een respijtperiode afdwinging configureren en schakel het selectievakje in als de toepassing installeren deadline is bereikt, wordt deze geïnstalleerd in het eerste niet-business-venster dat de gebruiker tot die respijtperiode geconfigureerd. De gebruiker kan echter nog steeds Software Center wordt geopend en de toepassing op elk gewenst moment die ze willen installeren. Zodra de respijtperiode is verlopen, hersteld afdwinging normale gedrag voor achterstallige implementaties. Vergelijkbare opties zijn toegevoegd aan de implementatiewizard van software-updates, de wizard Regels voor automatische implementatie en de pagina eigenschappen.



## <a name="improved-functionality-in-dialog-boxes-about-required-software"></a>Verbeterde functionaliteit in de dialoogvensters over de vereiste software
Vereiste software met een gebruiker Radiotuner ontvangt van het **uitstellen en Help me herinneren:** instelt, kunnen ze selecteren uit de volgende lijst vervolgkeuzelijst met waarden: 
- **Later**. Hiermee geeft u op dat meldingen worden gepland op basis van de instellingen voor meldingen geconfigureerd in de instellingen voor Clientagent.
- **Vaste tijd**. Hiermee geeft u op dat de melding wordt gepland om opnieuw weergeven nadat de geselecteerde tijd (bijvoorbeeld in 30 minuten).

![Agent-pagina in de clientagentinstellingen computer](media/client-notification-settings.png)

De maximale uitstellen tijd is gebaseerd op de melding ingestelde waarden in de clientagentinstellingen. Bijvoorbeeld, als de **groter is dan 24 uur deadline voor implementatie, gebruikers herinneren elke (uur)** instellen op de Computer Agent pagina is geconfigureerd voor 10 uur en meer dan 24 uur vóór de deadline, de gebruiker ziet een set opties uitstellen tot maar nooit meer dan 10 uur. Als de deadline nadert, zijn minder opties beschikbaar, consistent zijn met de relevante clientagentinstellingen voor elk onderdeel van de implementatie van een planning.

Daarnaast voor een hoog risico implementatie, zoals een takenreeks die een besturingssysteem implementeert is de gebruikerservaring van de melding nu ingrijpender. In plaats van een tijdelijke taakbalk melding, telkens wanneer de gebruiker wordt geïnformeerd dat essentieel softwareonderhoud vereist is, een dialoogvenster zoals het volgende wordt weergegeven op de computer van de gebruiker:

![Dialoogvenster voor vereiste Software](media/client-toast-notification.png)


Voor meer informatie:
- [Instellingen voor het beheren van implementaties met een hoog risico](../../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Het configureren van clientinstellingen](../../clients/deploy/configure-client-settings.md)

## <a name="software-updates-dashboard"></a>Dashboard voor software-updates
Gebruik het nieuwe dashboard van de software-updates om weer te geven van de huidige status van naleving van apparaten in uw organisatie en sneller kunt analyseren van de gegevens te zien welke apparaten zijn kwetsbaar voor. De als dashboard wilt weergeven, gaat u naar **bewaking** > **overzicht** > **beveiliging** > **Software-Updates Dashboard**.

Zie voor meer informatie, [software-updates controleren](/sccm/sum/deploy-use/monitor-software-updates).


## <a name="improvements-to-the-application-request-process"></a>Verbeteringen in het proces voor het aanvragen van toepassing
Nadat u een toepassing voor de installatie hebt goedgekeurd, kunt u vervolgens de aanvraag weigeren door te klikken op **weigeren** in de Configuration Manager-console. Eerder deze knop niet beschikbaar na goedkeuring.

Deze actie wordt niet van apparaten verwijderd van de toepassing. Het echter voorkomen dat gebruikers nieuwe exemplaren van de toepassing installeren via Software Center.

## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filteren op de omvang van de inhoud in de regels voor automatische implementatie
Nu kunt u filteren op de grootte van de inhoud voor software-updates in de regels voor automatische implementatie. Bijvoorbeeld, enkel software-updates die kleiner dan 2 MB zijn downloaden, kunt u instellen de **inhoud grootte (KB)** filteren op **< 2048**. Met dit filter wordt voorkomen dat grote software-updates automatisch worden gedownload, welke betere ondersteunt vereenvoudigd Windows downlevel onderhoud als netwerkbandbreedte beperkt is. Zie voor meer informatie:
- [Configuration Manager en vereenvoudigd Windows onderhoud op omlaag niveau besturingssystemen](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)
- [Software-updates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates)

Configureren van de **inhoud grootte (KB)** veld, een van de volgende handelingen uit:
- Als u een regel voor automatische implementatie in de wizard regel voor automatische implementatie maken maakt, gaat u naar de **Software-Updates** pagina.
- In de eigenschappen voor een bestaande regel voor automatische implementatie, gaat u naar de **Software-Updates** tabblad.

## <a name="office-365-client-management-dashboard"></a>Office 365 clientbeheer dashboard
Het dashboard clientbeheer voor Office 365 is nu beschikbaar in de Configuration Manager-console. Het dashboard, Ga naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.

Het dashboard geeft grafieken voor het volgende weer:

- Aantal Office 365-clients
- Office 365-clientversies
- Clienttalen voor Office 365
- Office 365 client kanalen     

Zie voor meer informatie, [Office 365 ProPlus beheren updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Takenreeksstappen voor het beheren van BIOS UEFI-conversie
U kunt nu een takenreeks voor implementatie van besturingssysteem met een nieuwe variabele TSUEFIDrive, zodat de **Computer opnieuw opstarten** stap bereidt een FAT32-partitie op de harde schijf voor de overgang naar UEFI. De volgende procedure geeft een voorbeeld van hoe u takenreeksstappen voor het voorbereiden van de harde schijf voor het BIOS UEFI conversie kunt maken. Zie voor meer informatie, [Takenreeksstappen voor het beheren van BIOS UEFI conversie](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion).

##  <a name="improvements-to-the-task-sequence-step-prepare-configmgr-client-for-capture"></a>Verbeteringen in de takenreeksstap: Prepare ConfigMgr Client for Capture  
De ConfigMgr-Client voorbereiden stap wordt de Configuration Manager-client in plaats van alleen verwijderen sleutelinformatie nu volledig verwijderd. Wanneer de takenreeks de vastgelegde installatiekopie implementeert, wordt wordt telkens wanneer een nieuwe Configuration Manager-client geïnstalleerd. Zie voor meer informatie, [Takenreeksstappen](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture).



## <a name="intune-compliance-policy-charts"></a>Intune compatibiliteit beleid grafieken
Kunt u nu een snelle weergave van algemene compatibiliteit voor apparaten, en de bovenkant mogelijke redenen voor non-compatibiliteit, met behulp van nieuwe grafieken onder de **bewaking** werkruimte in de Configuration Manager-console. U kunt een sectie in de grafiek worden ingezoomd om een lijst van de apparaten in die categorie te klikken. Zie voor meer informatie, [het nalevingsbeleid bewaken](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="lookout-integration-for-hybrid-implementations-to-protect-ios-and-android-devices"></a>Zoek integratie voor hybride implementaties iOS en Android-apparaten te beschermen
Microsoft is integreren met de oplossing voor de beveiliging van de altijd mobiele bedreiging bij het beveiligen van iOS en Android mobiele apparaten door de detectie van malware, riskant apps en meer informatie over apparaten. Zoek de oplossing kunt u bepalen het risiconiveau, kan worden geconfigureerd. U kunt een beleidsregel naleving in System Center Configuration Manager om te bepalen op basis van de risicoanalyse door altijd apparaatcompatibiliteit maken. Met behulp van beleid voor voorwaardelijke toegang, kunt u toestaan of blokkeren van toegang tot bedrijfsbronnen op basis van de compatibiliteitsstatus van het apparaat. Zie voor meer informatie over de integratie en hoe het werkt, [toegang op basis van het apparaat, netwerk- en toepassing risico beheren](/sccm/protect/deploy-use/manage-access-based-on-device-network-app-risk).

Gebruikers van niet-compatibele iOS-apparaten wordt gevraagd om in te schrijven. Kan deze persoon zich altijd werk app op hun apparaten installeren, het activeren van de app en het herstellen van bedreigingen die zijn gerapporteerd in altijd werktoepassing toegang te krijgen tot bedrijfsgegevens nodig. Leer hoe u [configureren en dan implementeert voor zakelijke apps](/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps).



## <a name="new-compliance-settings-for-configuration-items"></a>Nieuwe compatibiliteitsinstellingen voor configuratie-items
Er zijn veel nieuwe instellingen die kunt u in uw configuratie-items voor verschillende apparaatplatforms. Dit zijn de instellingen die eerder beschikbaar waren in Microsoft Intune in een zelfstandige configuratie en zijn nu beschikbaar wanneer u Intune met Configuration Manager.
Zie voor meer informatie, [configuratie-items voor apparaten beheerd zonder dat de System Center Configuration Manager-client](/sccm/compliance/deploy-use/configuration-items-for-devices-managed-without-the-client).

### <a name="new-settings-for-android-devices"></a>Nieuwe instellingen voor Android-apparaten
#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Wachtwoordgeschiedenis onthouden**
- **Vingerafdruk toestaan ontgrendelen**

#### <a name="security-settings"></a>Beveiligingsinstellingen
- **Versleuteling vereisen voor opslagkaarten**
- **Schermafbeelding toestaan**
- **Verzending van diagnostische gegevens toestaan**

#### <a name="browser-settings"></a>Browserinstellingen
- **Webbrowser toestaan**
- **Automatisch invullen toestaan**
- **Pop-upblokkering toestaan**
- **Cookies toestaan**
- **Active scripting toestaan**

#### <a name="app-settings"></a>App-instellingen
- **Google Play store toestaan**

#### <a name="device-capability-settings"></a>Mogelijkheid apparaatinstellingen
- **Verwisselbare opslag toestaan**
- **Wi-Fi-tethering toestaan**
- **Geolocatie toestaan**
- **NFC toestaan**
- **Bluetooth toestaan**
- **Spraakroaming toestaan**
- **Gegevensroaming toestaan**
- **SMS-en MMS-berichten toestaan**
- **Spraakassistent toestaan**
- **Nummer inspreken toestaan**
- **Kopiëren en plakken toestaan**

### <a name="new-settings-for-ios-devices"></a>Nieuwe instellingen voor iOS-apparaten
#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Aantal complexe tekens vereist in wachtwoord**
- **Eenvoudige wachtwoorden toestaan**
- **Minuten van inactiviteit voordat wachtwoord vereist is**
- **Wachtwoordgeschiedenis onthouden**

### <a name="new-settings-for-mac-os-x-devices"></a>Nieuwe instellingen voor Mac OS X-apparaten
#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Aantal complexe tekens vereist in wachtwoord**
- **Eenvoudige wachtwoorden toestaan**
- **Wachtwoordgeschiedenis onthouden**
- **Minuten van inactiviteit voordat de screensaver wordt geactiveerd**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Nieuwe instellingen voor Windows 10 Desktop en Mobile-apparaten
#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Minimum aantal tekensets**
- **Wachtwoordgeschiedenis onthouden**
- **Wachtwoord vereisen wanneer het apparaat wordt geactiveerd vanuit een niet-actieve status**

#### <a name="security-settings"></a>Beveiligingsinstellingen
- **Versleuteling vereisen op mobiele apparaten**
- **Handmatige unenrollment toestaan**

#### <a name="device-capability-settings"></a>Mogelijkheid apparaatinstellingen
- **VPN via mobiele verbinding toestaan**
- **VPN-roaming via mobiele verbinding toestaan**
- **Opnieuw instellen van telefoon toestaan**
- **USB-verbinding toestaan**
- **Cortana toestaan**
- **Meldingen van Onderhoudscentrum toestaan**

### <a name="new-settings-for-windows-10-team-devices"></a>Nieuwe instellingen voor Windows 10 Team-apparaten
#### <a name="device-settings"></a>Instellingen voor apparaten
- **Azure Operational Insights inschakelen**
- **Draadloze projectie Miracast inschakelen**
- **Kies de vergadering informatie die wordt weergegeven op het welkomstscherm te selecteren**
- **URL achtergrondafbeelding Lockscreen**

### <a name="new-settings-for-windows-81-devices"></a>Nieuwe instellingen voor Windows 8.1-apparaten
#### <a name="applicability-settings"></a>Instellingen van toepassing
- **Alle configuraties toepassen op Windows 10**

#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Vereist Wachtwoordtype**
- **Minimum aantal tekensets**
- **Minimale wachtwoordlengte**
- **Aantal herhaalde, mislukte aanmeldingen dat is toegestaan voordat het apparaat wordt gewist**
- **Minuten van inactiviteit voordat het scherm wordt uitgeschakeld**
- **Wachtwoord verloopt (dagen)**
- **Wachtwoordgeschiedenis onthouden**
- **Hergebruik van wachtwoorden voorkomen**
- **Afbeeldingswachtwoord en PINCODE toestaan**

#### <a name="browser-settings"></a>Browserinstellingen
- **Automatische detectie van intranetnetwerk toestaan**

### <a name="new-settings-for-windows-phone-81-devices"></a>Nieuwe instellingen voor Windows Phone 8.1-apparaten
#### <a name="applicability-settings"></a>Instellingen van toepassing
- **Alle configuraties toepassen op Windows 10**

#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Minimum aantal tekensets**
- **Eenvoudige wachtwoorden toestaan**
- **Wachtwoordgeschiedenis onthouden**

#### <a name="device-capability-settings"></a>Mogelijkheid apparaatinstellingen
- **Automatische verbinding met gratis Wi-Fi-hotspots toestaan**

