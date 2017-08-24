---
title: Nieuwe versie 1610 | Microsoft Docs
description: "Meer informatie over deze wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1610 van System Center Configuration Manager."
ms.custom: na
ms.date: 11/23/2016
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7eb0803-3f8f-4ab6-825a-99ac11f5ba7d
caps.latest.revision: "40"
author: Brenduns
ms.author: brenduns
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 8b80f4d14eafa4cbbfb083178a118bc0e71f4019
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="what39s-new-in-version-1610-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1610 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1610 voor de huidige vertakking van System Center Configuration Manager is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1511 of 1602 1606 wordt uitgevoerd.


> [!TIP]  
> Een nieuwe site te installeren, moet u een basislijnversie van Configuration Manager.  
>  Meer informatie over:    
>  -   [Nieuwe sites installeren](https://technet.microsoft.com/library/mt590197.aspx)  
>  -   [Updates installeren op sites](https://technet.microsoft.com/library/mt607046.aspx)  
>  -   [Basislijn- en updateversies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1610 van Configuration Manager.  


## <a name="in-console-monitoring-of-update-installation-status"></a>In de console bewaking van de status van de update-installatie  
Vanaf versie 1610, wanneer u een updatepakket te installeren en controleren van de installatie in de console, wordt er een nieuwe fase wordt: **Na de installatie**. Deze fase bevat de status van taken, zoals belangrijke services en de initialisatie van de bewaking van de replicatie opnieuw te starten. (Deze fase is niet beschikbaar in de console pas na uw site is bijgewerkt naar versie 1610.) Zie voor meer informatie over de installatiestatus van de update [updates in de console installeren](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).


## <a name="exclude-clients-from-automatic-upgrade"></a>Clients uitsluiten van Automatische upgrade
U kunt Windows-clients uitsluiten van het ophalen van bijgewerkt met nieuwe versies van de clientsoftware. Om dit te doen, kunt u de clientcomputers opnemen in een verzameling die moeten worden uitgesloten van de upgrade is opgegeven. Clients in de uitgesloten verzameling negeren aanvragen voor het bijwerken van de clientsoftware.  Zie voor meer informatie [uitsluiten Windows-clients van upgrades](../../clients/manage/upgrade/exclude-clients-windows.md).


## <a name="improvements-for-boundary-groups"></a>Verbeteringen voor grensgroepen
Versie 1610 introduceert belangrijke wijzigingen aan grensgroepen en hoe deze werken met distributiepunten. Deze wijzigingen kunnen u het ontwerp van uw inhoudsinfrastructuur vereenvoudigen tijdens zodat u meer controle over hoe en wanneer clients terugvallen op extra distributiepunten zoeken als inhoudsbron locaties verwijst. Dit omvat zowel on-premises en cloud-gebaseerde distributiepunten.
Deze verbeteringen vervangen concepten en gedrag die bekend met bent (zoals het configureren van distributiepunten als snel of traag). Het nieuwe model moet gemakkelijker te instellen en onderhouden. Deze wijzigingen vast ook de basis voor toekomstige wijzigingen die andere sitesysteemrollen die u aan grensgroepen koppelen verbeteren.

Wanneer u naar versie 1610 bijwerkt, converteert de update in uw huidige configuratie van grensgroepen voor het nieuwe model passen zodat deze wijzigingen niet uw bestaande configuraties voor de distributie van inhoud storen.

Zie voor meer informatie [grensgroepen](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#a-namebkmkboundarygroupsa-boundary-groups).


## <a name="peer-cache-for-content-distribution-to-clients"></a>Peer-Cache voor de distributie van inhoud aan clients
Begin met versie 1610, client **Peer-Cache** helpt u bij de implementatie van inhoud naar clients op externe locaties. Peer-Cache is een ingebouwde Configuration Manager-oplossing voor clients om inhoud te delen met andere clients, rechtstreeks vanuit het lokale cachegeheugen.

Nadat u clientinstellingen waarmee Peer-Cache op een verzameling implementeert, fungeren leden van deze verzameling als een peer-inhoudsbron voor andere clients in dezelfde grensgroep.

U kunt ook de nieuwe **Clientgegevensbronnen** dashboard om te begrijpen van het gebruik van Peer-Cache inhoudsbronnen in uw omgeving.

> [!TIP]  
> Met versie 1610 worden Peer-Cache en het dashboard Clientgegevensbronnen functies van evaluatieversies. Zie zodat ze [functies van evaluatieversies van updates gebruiken](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

Zie voor meer informatie [Peer-Cache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache), en [Clientgegevensbronnen dashboard](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).


## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Meerdere gedeelde distributiepunten op hetzelfde moment migreren
U kunt nu de optie voor het **opnieuw toewijzen van distributiepunt** Configuration Manager-proces parallel de opnieuw toewijzen van maximaal 50 hebben van gedeelde distributiepunten op hetzelfde moment. Voorafgaand aan deze release zijn omgeleid distributiepunten verwerkte één voor één opnieuw. Zie voor meer informatie, [migreren van meerdere gedeelde distributiepunten op hetzelfde moment](/sccm/core/migration/planning-a-content-deployment-migration-strategy#migrate-multiple-shared-distribution-points-at-the-same-time).

## <a name="cloud-management-gateway-for-managing-internet-based-clients"></a>Cloud management gateway voor het beheren van clients op Internet

Beheergateway cloud biedt een eenvoudige manier voor het beheren van Configuration Manager-clients op Internet. De cloud management gateway-service die wordt geïmplementeerd voor Microsoft Azure en een Azure-abonnement is vereist, verbindt met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van het verbindingspunt cloud management gateway. Zodra het is volledig geïmplementeerd en geconfigureerd, worden clients kunnen communiceren met de lokale Configuration Manager-sitesysteemrollen en cloud-gebaseerde distributiepunten ongeacht of ze zijn verbonden met het interne particuliere netwerk of op het Internet. Zie voor meer informatie en om te zien hoe cloud management gateway wordt vergeleken met de Internet-gebaseerd clientbeheer [beheren van clients op het Internet](/sccm/core/clients/manage/manage-clients-internet).

## <a name="improvements-to-the-windows-10-edition-upgrade-policy"></a>Verbeteringen in het upgradebeleid van de Windows 10-editie
In deze release zijn de volgende verbeteringen aangebracht aan dit beleidstype:

- U kunt nu de editie-Upgradebeleid gebruiken met Windows 10-pc's waarop de Configuration Manager-client naast Windows 10-pc's die zijn geregistreerd met Microsoft Intune wordt uitgevoerd.
- U kunt Windows 10 Professional bijwerken naar een van de platforms die compatibel met uw hardware zijn in de wizard.

## <a name="manage-hardware-identifiers"></a>Hardware-id's beheren
U kunt nu een lijst met hardware-id's in Configuration Manager moeten worden genegeerd voor PXE-opstart- en clientregistratie opgeven. Er zijn twee veelvoorkomende problemen die hierdoor adres:

1. Veel apparaten, zoals Surface Pro, 3, beschikken niet over een ingebouwde Ethernet-poort. Een USB-Ethernet-adapter wordt doorgaans gebruikt een bekabelde verbinding omwille van een besturingssysteem wordt geïmplementeerd. Vanwege de kosten en algemene bruikbaarheid zijn echter vaak gedeelde adapters. Omdat het MAC-adres van deze adapter wordt gebruikt om het apparaat hebt geïdentificeerd, wordt hergebruiken van de adapter problematisch zonder extra beheerdersacties weergegeven tussen elke implementatie. Nu in Configuration Manager versie 1610, kunt u uitsluiten het MAC-adres van deze adapter zodat deze kan eenvoudig opnieuw worden gebruikt in dit scenario.
2. De SMBIOS-ID moet een unieke hardware-id zijn, maar sommige speciale hardware-apparaten zijn gebouwd met dubbele id. Dit probleem mogelijk niet als gebruikelijk zijn als het USB-Ethernet-adapter scenario hierboven wordt beschreven, maar u kunt dit oplossen met behulp van de lijst met uitgesloten hardware-id's.

Zie voor meer informatie [beheren dubbele hardware-id's](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Verbeteringen in Windows Store voor bedrijven-integratie met Configuration Manager
Wijzigingen in deze release:
- Eerder kon u alleen gratis apps uit de Windows Store voor bedrijven implementeren. Configuration Manager nu bovendien ondersteunt de implementatie van betaald online gelicentieerde apps (voor Intune ingeschreven apparaten).
- U kunt nu een directe synchronisatie tussen de Windows Store voor bedrijven en Configuration Manager initiëren.
- U kunt nu de client geheime sleutel die u hebt verkregen via Azure Active Directory wijzigen.
- U kunt een abonnement aan het archief verwijderen.

Zie voor meer informatie [apps beheren via de Windows Store voor bedrijven met System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


## <a name="policy-sync-for-intune-enrolled-devices"></a>Synchronisatie van beleid voor Intune ingeschreven apparaten
U kunt nu een synchronisatie met beleid voor een apparaat geregistreerd bij Intune aanvragen via de Configuration Manager-console, in plaats van dat voor het aanvragen van een synchronisatie uit de bedrijfsportal-app op het apparaat zelf. Informatie over de status van de synchronisatie-aanvraag is beschikbaar als een nieuwe kolom in de apparaat-weergaven, aangeroepen **status van externe synchronisatie**. De informatie is ook beschikbaar in de sectie van de discovery data van het **eigenschappen** dialoogvenster voor elk apparaat.
Zie voor meer informatie [beleid voor Intune ingeschreven apparaten uit de Configuration Manager-console op afstand synchroniseren](/sccm/mdm/deploy-use/sync-intune-device).


## <a name="use-compliance-settings-to-configure-windows-defender-settings"></a>Compatibiliteitsinstellingen gebruiken om Windows Defender-instellingen te configureren
U kunt nu instellingen voor Windows Defender-client op Intune ingeschreven Windows 10-computers configureren met behulp van configuratie-items in de Configuration Manager-console.
Zie voor meer informatie de **Windows Defender** in sectie [configuratie-items maken voor Windows 8.1 en Windows 10-apparaten worden beheerd zonder de System Center Configuration Manager-client](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).



## <a name="general-improvements-to-software-center"></a>Algemene verbeteringen aan Software Center
- Gebruikers kunnen nu apps aanvragen van Software Center, evenals de Application Catalog.
- Verbeteringen in zodat gebruikers begrijpen welke software is nieuw en relevant.

## <a name="new-columns-in-device-collection-views"></a>Nieuwe kolommen in apparaat verzameling weergaven
U kunt nu de weergeven kolommen voor **IMEI-nummer** en **serienummer** (voor iOS-apparaten) in apparaat verzameling weergaven.
Zie voor meer informatie [apparaten met IMEI-nummer of iOS-serienummers labelen](https://docs.microsoft.com/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id).

## <a name="customizable-branding-for-software-center-dialogs"></a>Aanpasbare huisstijl voor Software Center-dialoogvensters
Aangepaste huisstijl voor Software Center is geïntroduceerd in versie 1602 van Configuration Manager. In versie 1610, is die huisstijl nu uitgebreid naar alle bijbehorende dialoogvensters een consistente gebruikerservaring bieden aan gebruikers van Software Center.

Aangepaste huisstijl voor Software Center is toegepast volgens de volgende regels:

- Als de siteserverrol van Application Catalog-website-punt is niet geïnstalleerd, wordt de Software Center de organisatienaam die is opgegeven bevat in de **Computeragent** clientinstelling **weergegeven organisatienaam in Software Center**. Zie voor instructies [het configureren van clientinstellingen](../../clients/deploy/configure-client-settings.md).

- Als de siteserverrol van Application Catalog-website-punt is geïnstalleerd, worden Software Center de naam van de organisatie en de kleur die is opgegeven in de Application Catalog-website-punt eigenschappen van de siteserverrol. Zie voor meer informatie [configuratieopties voor het Application Catalog-websitepunt](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#Application-Catalog-website-point).

- Als een Microsoft Intune-abonnement is geconfigureerd en is verbonden met de Configuration Manager-omgeving, geeft Software Center de naam van de organisatie, kleur en bedrijfslogo opgegeven in de eigenschappen van de Intune-abonnement. Zie [Het Windows Intune-abonnement configureren](/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription) voor meer informatie.


## <a name="enforcement-grace-period-for-required-application-and-software-update-deployments"></a>Respijtperiode afdwingen voor vereiste toepassingen en software-update-implementaties
In sommige gevallen is het raadzaam om gebruikers meer tijd voor implementaties van toepassingen installeren die zijn vereist of software-updates buiten een deadlines die u instelt. Bijvoorbeeld: dit kan nodig zijn wanneer een computer gedurende langere tijd is uitgeschakeld en moet het installeren van een groot aantal toepassing of update-implementaties. Als een eindgebruiker is alleen van vakantie geretourneerd, moeten ze mogelijk lang wachten terwijl als achterstallig toepassing implementaties zijn geïnstalleerd. U kunt nu een respijtperiode afdwingen door Configuration Manager-clientinstellingen implementeren naar een verzameling om dit probleem op te lossen definiëren. 

Voor het configureren van de respijtperiode is, moet u de volgende acties uitvoeren:
1.      Op de **Computeragent** pagina configureren van clientinstellingen, de nieuwe eigenschap **respijtperiode voor afdwingen na de implementatie (uren) deadline** met een waarde tussen **1** en **120** uur.
2.      In een nieuwe implementatie van de vereiste toepassing of in de eigenschappen van een bestaande implementatie op de **planning** pagina, schakel het selectievakje **afdwingen van deze implementatie op basis van gebruikersvoorkeuren tot de respijtperiode die is gedefinieerd in de clientinstellingen uitstellen**. Alle implementaties die u hebt dit selectievakje is ingeschakeld en zijn bedoeld voor apparaten die u ook de clientinstelling geïmplementeerd gebruikt de respijtperiode voor afdwinging.

Als u een respijtperiode afdwingen configureren en schakel het selectievakje in als de deadline van de installatie van de toepassing is bereikt, wordt deze geïnstalleerd in het eerste niet-zakelijk venster die de gebruiker tot die respijtperiode geconfigureerd. De gebruiker kan echter nog steeds openen van Software Center en de toepassing op elk gewenst moment die ze willen installeren. Nadat de respijtperiode is verlopen, hersteld afdwinging normaal gedrag voor implementaties van achterstallige. Soortgelijke opties zijn toegevoegd aan de wizard voor implementatie van software-updates, de wizard regels automatische implementatie en eigenschappenpagina's.



## <a name="improved-functionality-in-dialog-boxes-about-required-software"></a>Verbeterde functionaliteit in dialoogvensters over de vereiste software
Wanneer een gebruiker de vereiste software ontvangt van de **uitstellen en Help me herinneren:** instelt, kunnen ze selecteren in de volgende lijst in de vervolgkeuzelijst van waarden: 
- **Later**. Hiermee geeft u op dat meldingen worden gepland op basis van de instellingen voor meldingen geconfigureerd in de clientagentinstellingen.
- **Vaste tijd**. Hiermee geeft u op dat de melding wordt gepland om de geselecteerde tijd (bijvoorbeeld in 30 minuten) opnieuw weer te geven.

![Computer Agent pagina in de clientagentinstellingen](media/client-notification-settings.png)

De maximale uitstellen tijd is gebaseerd op de melding ingestelde waarden in de clientagentinstellingen. Bijvoorbeeld, als de **langer dan 24 uur deadline voor implementatie, gebruikers herinneren elke (uur)** instellen op de Computer Agent pagina is geconfigureerd voor 10 uur en meer dan 24 uur vóór de deadline is, de gebruiker ziet een set opties uitstellen tot maar nooit meer dan 10 uur. Als de deadline nadert, zijn minder mogelijkheden beschikbaar, in overeenstemming met de relevante instellingen voor Clientagent voor elk onderdeel van de implementatie-tijdlijn.

Daarnaast voor een implementatie met hoog risico, zoals een takenreeks die een besturingssysteem implementeert is de gebruikerservaring van de melding nu ingrijpender. In plaats van een melding van tijdelijke taakbalk, elke keer dat de gebruiker wordt geïnformeerd dat essentieel softwareonderhoud vereist is, een dialoogvenster zoals de volgende wordt weergegeven op de computer van de gebruiker:

![Dialoogvenster voor vereiste Software](media/client-toast-notification.png)


Voor meer informatie:
- [Instellingen voor het beheren van implementaties met een hoog risico](../../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Clientinstellingen configureren](../../clients/deploy/configure-client-settings.md)

## <a name="software-updates-dashboard"></a>Dashboard voor software-updates
Nieuwe software-updates dashboard gebruiken om de huidige status van naleving van apparaten in uw organisatie weergeven en de gegevens om te zien welke apparaten zijn kwetsbaar voor snel analyseren. Als u wilt weergeven in het dashboard, gaat u naar **bewaking** > **overzicht** > **beveiliging** > **Software-Updates Dashboard**.

Zie voor meer informatie [software-updates controleren](/sccm/sum/deploy-use/monitor-software-updates).


## <a name="improvements-to-the-application-request-process"></a>Verbeteringen in het proces voor het aanvragen van toepassing
Nadat u een toepassing voor de installatie hebt goedgekeurd, kunt u vervolgens de aanvraag weigeren door te klikken op **weigeren** in de Configuration Manager-console. Voorheen deze knop is niet beschikbaar na de goedkeuring.

Deze actie leidt niet tot de toepassing van alle apparaten worden verwijderd. Het echter voorkomen dat gebruikers nieuwe exemplaren van de toepassing installeren vanuit Software Center.

## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filteren op Inhoudsgrootte in regels voor automatische implementatie
U kunt nu filteren op de grootte van de inhoud voor software-updates in de regels voor automatische implementatie. Bijvoorbeeld, als u wilt downloaden alleen software-updates die kleiner dan 2 MB zijn, kunt u instellen de **inhoud grootte (KB)** filteren op **< 2048**. Met dit filter voorkomt dat grote software-updates automatisch worden gedownload, die betere ondersteuning biedt vereenvoudigd Windows downlevel-onderhoud als de netwerkbandbreedte beperkt is. Zie voor meer informatie:
- [Configuration Manager en vereenvoudigd Windows onderhoud op omlaag niveau besturingssystemen](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)
- [Software-updates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates)

Voor het configureren van de **inhoud grootte (KB)** veld, een van de volgende handelingen uit:
- Wanneer u een regel voor automatische implementatie in de wizard regel voor automatische implementatie maken maakt, gaat u naar de **Software-Updates** pagina.
- In de eigenschappen voor een bestaande regel voor automatische implementatie, gaat u naar de **Software-Updates** tabblad.

## <a name="office-365-client-management-dashboard"></a>Dashboard voor Office 365-clientbeheer
Het beheer van de Client Office 365-dashboard is nu beschikbaar in de Configuration Manager-console. Als u wilt weergeven in het dashboard, gaat u naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.

Het dashboard toont de grafieken voor het volgende:

- Aantal Office 365-clients
- Versies van Office 365-client
- Clienttalen voor Office 365
- Office 365 client kanalen     

Zie voor meer informatie [beheren van Office 365 ProPlus-updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Takenreeksstappen voor het beheren van BIOS naar UEFI-conversie
U kunt nu een takenreeks voor implementatie van besturingssysteem met een nieuwe variabele, TSUEFIDrive, zodat de **Computer opnieuw opstarten** stap bereidt een FAT32-partitie op de harde schijf voor de overgang naar UEFI. De volgende procedure bevat een voorbeeld van hoe u de stappen in de takenreeks de harde schijf voorbereiden voor de conversie van UEFI-BIOS kunt maken. Zie voor meer informatie [Takenreeksstappen voor het beheren van BIOS naar UEFI conversie](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion).

##  <a name="improvements-to-the-task-sequence-step-prepare-configmgr-client-for-capture"></a>Verbeteringen in de takenreeksstap: Prepare ConfigMgr Client for Capture  
De ConfigMgr-Client voorbereiden stap wordt de Configuration Manager-client, in plaats van alleen het verwijderen van belangrijke gegevens nu volledig verwijderd. Wanneer de takenreeks de vastgelegde besturingssysteeminstallatiekopie implementeert, wordt deze elke keer dat een nieuwe Configuration Manager-client installeren. Zie voor meer informatie [Takenreeksstappen](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture).



## <a name="intune-compliance-policy-charts"></a>Intune naleving beleid grafieken
U krijgt nu een overzicht van de algemene compatibiliteit voor apparaten en de bovenkant redenen voor niet-naleving, met behulp van de nieuwe grafieken onder de **bewaking** werkruimte in de Configuration Manager-console. U kunt klikken op een sectie in het diagram om een lijst van de apparaten in die categorie. Zie voor meer informatie [het nalevingsbeleid bewaken](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="lookout-integration-for-hybrid-implementations-to-protect-ios-and-android-devices"></a>Lookout-integratie voor hybride implementaties van iOS en Android-apparaten beveiligen
Microsoft is integreren met Lookout van mobiele threat protection oplossing voor iOS- en mobiele Android-apparaten beschermen door malware, risicovolle apps en meer op apparaten te detecteren. Lookout van oplossing kunt u bepalen van het risiconiveau is configureerbaar. U kunt een beleidsregel voor naleving in System Center Configuration Manager om te bepalen op basis van de risico-evaluatie door Lookout apparaatcompatibiliteit maken. Beleid voor voorwaardelijke toegang gebruikt, kunt u toestaan of blokkeren van toegang tot bedrijfsbronnen op basis van de compatibiliteitsstatus van het apparaat. Zie voor meer informatie over de integratie en hoe het werkt, [toegang op basis van apparaat-, netwerk- en toepassing risico beheren](/sccm/protect/deploy-use/manage-access-based-on-device-network-app-risk).

Gebruikers van niet-compatibele iOS-apparaten wordt gevraagd om in te schrijven. Kan deze persoon zich vereist voor het installeren van de Lookout for Work-app op hun apparaten, de app activeren en herstellen van bedreigingen die zijn gerapporteerd in de Lookout for Work-toepassing toegang te krijgen tot bedrijfsgegevens. Meer informatie over hoe [configureren en implementeren van Lookout voor zakelijke apps](/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps).



## <a name="new-compliance-settings-for-configuration-items"></a>Nieuwe instellingen voor naleving voor configuratie-items
Er zijn veel nieuwe instellingen die kunt u in uw configuratie-items voor verschillende platforms. Dit zijn de instellingen die eerder beschikbaar waren in Microsoft Intune in een zelfstandige configuratie en zijn nu beschikbaar wanneer u Intune met Configuration Manager.
Zie voor meer informatie [configuratie-items voor apparaten die worden beheerd zonder de System Center Configuration Manager-client](/sccm/compliance/deploy-use/configuration-items-for-devices-managed-without-the-client).

### <a name="new-settings-for-android-devices"></a>Nieuwe instellingen voor Android-apparaten
#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Wachtwoordgeschiedenis onthouden**
- **Vingerafdruk toestaan ontgrendelen**

#### <a name="security-settings"></a>Beveiligingsinstellingen
- **Versleuteling vereisen op opslagkaarten**
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

#### <a name="device-capability-settings"></a>Instellingen voor apparaatfuncties
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
- **Handmatige uitschrijving toestaan**

#### <a name="device-capability-settings"></a>Instellingen voor apparaatfuncties
- **VPN via mobiele verbinding toestaan**
- **VPN-roaming via mobiele verbinding toestaan**
- **Opnieuw instellen van telefoon toestaan**
- **USB-verbinding toestaan**
- **Cortana toestaan**
- **Meldingen van Onderhoudscentrum toestaan**

### <a name="new-settings-for-windows-10-team-devices"></a>Nieuwe instellingen voor Windows 10 Team-apparaten
#### <a name="device-settings"></a>Instellingen voor apparaten
- **Operationeel inzicht van Azure inschakelen**
- **Draadloze Miracast-projectie inschakelen**
- **Kiezen welke vergaderingsinformatie wordt weergegeven op het welkomstscherm**
- **URL naar de achtergrondafbeelding van het Vergrendelingsscherm**

### <a name="new-settings-for-windows-81-devices"></a>Nieuwe instellingen voor Windows 8.1-apparaten
#### <a name="applicability-settings"></a>Toepasselijkheidsinstellingen
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
- **Afbeeldingswachtwoord en PIN toestaan**

#### <a name="browser-settings"></a>Browserinstellingen
- **Automatische detectie van intranetnetwerk toestaan**

### <a name="new-settings-for-windows-phone-81-devices"></a>Nieuwe instellingen voor Windows Phone 8.1-apparaten
#### <a name="applicability-settings"></a>Toepasselijkheidsinstellingen
- **Alle configuraties toepassen op Windows 10**

#### <a name="password-settings"></a>Wachtwoordinstellingen
- **Minimum aantal tekensets**
- **Eenvoudige wachtwoorden toestaan**
- **Wachtwoordgeschiedenis onthouden**

#### <a name="device-capability-settings"></a>Instellingen voor apparaatfuncties
- **Automatische verbinding met gratis Wi-Fi-hotspots toestaan**
