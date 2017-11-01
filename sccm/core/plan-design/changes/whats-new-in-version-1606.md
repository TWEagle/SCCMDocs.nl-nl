---
title: Nieuw in versie 1606
titleSuffix: Configuraton Manager
description: "Meer informatie over deze wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1606 van System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df2e57b9-6445-4067-98e7-ace85d4e6aa6
caps.latest.revision: "40"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 346a1c7199a2d9dbb2cb174502adbb8d03a39f86
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="what39s-new-in-version-1606-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1606 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1606 voor System Center Configuration Manager is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1511 of 1602 wordt uitgevoerd. Versie 1511 is de initiële basislijnversie die u gebruikt om nieuwe Configuration Manager-sites te installeren.
> [!TIP]  
>  Meer informatie over:  
>   
>  -   [Nieuwe sites installeren](/sccm/core/servers/deploy/install) (met behulp van een basislijnversie zoals 1511)  
>  -   [Updates installeren op sites](/sccm/core/servers/manage/updates) (zoals update 1602 of 1606)  

 De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1606 van Configuration Manager.  



## <a name="updatesandservicing"></a>Updates en onderhoud

### <a name="changes-for-the-updates-and-servicing-node"></a>Wijzigingen voor de Updates en onderhoud van knooppunt
Hieronder vindt u wijzigingen in de Updates en onderhoud van knooppunt in de Configuration Manager-console:
> [!NOTE]
> Deze wijzigingen zijn niet beschikbaar totdat nadat versie 1606 is geïnstalleerd.

- **Wijziging van knooppunt:**

    In de **bewaking** werkruimte de **Site Servicing status** knooppunt is gewijzigd in **Updates en onderhoudsstatus**.
- **Meer details van de status:**

    Wanneer u de installatiestatus van de update voor een site bekijkt, geeft de console nu afzonderlijke details voor de volgende acties:
    - **Download** (dit geldt alleen voor de bovenste site waarop de service connection point-sitesysteemrol is geïnstalleerd.)
    - **Replicatie**
    - **Controle van vereisten**
    - **Installatie**

  Er is bovendien nu meer gedetailleerde informatie voor elke stap, met inbegrip van logboekbestand dat u kunt bekijken voor meer informatie.  
-   **Nieuwe optie om opnieuw te proberen de vereiste fouten:**

    In zowel de **beheer** en **bewaking** werkruimten, de **Updates en onderhoud** knooppunt bevat een nieuwe knop op het lint genaamd **waarschuwingen over vereisten negeren**.

    Wanneer u updates installeert zonder de optie voor het negeren van waarschuwingen voor vereisten (van in de Wizard Updates), en de installatie van die update stopt vanwege een waarschuwing, kunt u selecteren **waarschuwingen over vereisten negeren** vanuit het lint. Dit activeert een automatische voortzetting van de update-installatie.  



- **Schonere weergave van updates:**

    In de **Updates en onderhoud** knooppunt nu ziet u alleen de laatst geïnstalleerde update en er nieuwe updates die beschikbaar zijn voor u installeren. Eerder geïnstalleerde updates wil weergeven, klikt u op de nieuwe **geschiedenis** knop die wordt weergegeven in het lint.  

-   **Nieuwe naam optie voor preproductie:**

    In de **Updates en onderhoud** knooppunt de **clientopties** knop heet nu **promoveren pre-Productieclient**.


###  <a name="pre-release-features"></a>Pre-release functies
Vanaf versie 1606 dient u toestemming wilt gebruiken, functies van evaluatieversies in System Center Configuration Manager voordat u kunt selecteren en het gebruik ervan. Zie [Use pre-release features from updates](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease) (Functies van evaluatieversies gebruiken) voor meer informatie.

### <a name="new-distribution-point-update-behavior"></a>Nieuwe updategedrag van de distributie-punt
Update 1606 introduceert wijzigingen ter verbetering van de beschikbaarheid van distributiepunten wanneer u toekomstige updates installeert.

Na de update 1606 is geïnstalleerd, wanneer vervolgens installeert u een update op die site waarvoor u de automatische installatie van de standaard- en pull-distributiepunt punt sitesysteemrollen, alle distributiepunten niet langer om bij te werken op hetzelfde moment offline gaan. In plaats daarvan gebruikt de siteserver van de site-instellingen voor het distribueren van inhoud voor het distribueren van de update op een subset van distributiepunten op een bepaald moment. Het resultaat is dat alleen bepaalde distributiepunten verbreken om de update te installeren. Hiermee worden distributiepunten die nog niet zijn begonnen om bij te werken of dat de update, blijven online en kunnen leveren van inhoud aan clients hebt voltooid.



## <a name="accessibility"></a>Toegankelijkheid
U kunt nu de eerste letter van de naam van een knooppunt om te navigeren tussen de verschillende knooppunten van een werkruimte, invoeren. Elke toets te drukken verplaatst de cursor naar het volgende knooppunt dat met die letter begint. Voor gebruikers die een lezer scherm, leest de lezer van de naam van dat knooppunt. Zie voor meer informatie over toegankelijkheidsopties [toegankelijkheidsfuncties in System Center Configuration Manager](../../../core/understand/accessibility-features.md).

## <a name="administration"></a>Beheer
Hieronder vindt u wijzigingen in beheer in de Configuration Manager-console:
### <a name="oms-connector"></a>OMS-Connector

U kunt nu de Configuration Manager verbinding als verzamelingen van System Center Configuration Manager en de [Microsoft Operations Management Suite (OMS)](https://azure.microsoft.com/en-us/documentation/articles/operations-management-suite-overview/). Hierdoor kan de gegevens, zoals verzamelingen van uw Configuration Manager-implementatie zichtbaar in OMS. Meer informatie, Zie [synchroniseren van gegevens uit Configuration Manager naar de Microsoft Operations Management Suite hier](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md).

De OMS-Connector is een functie van de voorlopige versie. Als u wilt inschakelen, Zie [functies van evaluatieversies van updates gebruiken](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="support-for-cache-size-in-client-settings"></a>Ondersteuning voor de grootte van de cache in de clientinstellingen

U kunt nu de grootte van de cachemap configureren op clientcomputers met **clientinstellingen** in de Configuration Manager-console. Voorheen kan u alleen de cachegrootte van de client bij het installeren of de clientsoftware opnieuw instellen. Nu de cachegrootte als een clientinstelling (standaard of aangepast opgeven) en vervolgens installeert u die instellingen toegepast met de volgende beleidsupdate op de client zonder dat een client opnieuw. Zie [De clientcache configureren voor Configuration Manager-clients](../../../core/clients/manage/manage-clients.md#BKMK_ClientCache) voor meer informatie.

## <a name="on-premises-mobile-device-management"></a>Lokaal beheer van mobiele apparaten

### <a name="support-for-multiple-device-management-points"></a>Ondersteuning voor meerdere apparaatbeheerpunten

Een on-premises beheer van mobiele apparaten (MDM) ondersteunt nu een nieuwe functie in Windows 10 Verjaardag Update die u automatisch een ingeschreven apparaat configureert om meer dan één beheerpunt apparaten beschikbaar voor gebruik. Deze mogelijkheid is het apparaat terugvallen op een ander apparaatbeheerpunt, wanneer een normaal gesproken gebruikt niet beschikbaar. Deze functie werkt alleen voor pc's en apparaten met de Windows 10 Verjaardag Update is geïnstalleerd.


## <a name="application-management"></a>Toepassingsbeheer

### <a name="manage-apps-from-the-windows-store-for-business"></a>Apps beheren via de Windows Store voor Bedrijven

De [Windows Store voor bedrijven](https://www.microsoft.com/business-store) kunt u vinden en Windows-apps voor uw organisatie, kopen, afzonderlijk of in volume. De store koppelt aan Configuration Manager, kunt u de lijst met apps die u met Configuration Manager hebt aangeschaft, bekijk deze in de Configuration Manager-console en deze implementeert, net als elke andere app synchroniseren.

Zie voor meer informatie [apps beheren via de Windows Store voor bedrijven met System Center Configuration Manager](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business.md).

### <a name="manage-ios-volume-purchased-apps"></a>Volume-purchased iOS-apps beheren

De werkstroom voor het volume-purchased iOS-apps beheren en implementeren van deze met Configuration Manager is verbeterd.

Zie voor meer informatie [volume-purchased iOS-apps met System Center Configuration Manager beheren](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).

### <a name="software-center-user-interface"></a>Software Center-gebruikersinterface

De gebruikersinterface van het Software Center is gestroomlijnd voor de detectie van eenvoudiger.
*  De **installatiestatus** en **geïnstalleerde Software** tabbladen zijn gecombineerd in één **installatiestatus** tabblad.
*  **Updates**, **besturingssystemen**, en **toepassingen** in drie afzonderlijke tabbladen zijn gescheiden.
* Meerdere updates kunnen nu worden geselecteerd voor installatie in één keer of alle updates tegelijk kunnen worden geïnstalleerd door te klikken op **installeert alle**.

### <a name="content-status-links"></a>Status van inhoud koppelingen
Op de eigenschappen van een toepassing of pakket wordt nu een koppeling waarmee u naar de status voor dat object.

## <a name="software-updates"></a>Software-updates

### <a name="client-setting-to-manage-the-office-365-client-agent"></a>Client-instelling voor het beheren van de Office 365-clientagent
Nu kunt u een Configuration Manager-client instellen voor het beheren van de clientagent voor Office 365. Nadat u dit instellen en implementeren van updates voor Office 365, werkt de clientagent voor Configuration Manager met de Office 365-clientagent downloaden en installeren van updates voor Office 365 vanaf een distributiepunt.

Zie voor meer informatie [Office 365 ProPlus beheren met Configuration Manager-updates](../../../sum/deploy-use/manage-office-365-proplus-updates.md).

### <a name="manually-switch-clients-to-a-new-software-update-point"></a>Clients handmatig overschakelen naar een nieuwe software-updatepunt
U kunt nu een optie waarmee Configuration Manager de switch clients naar een nieuw software-updatepunt als er problemen met het actieve software-updatepunt zijn kunt inschakelen. Nadat deze optie is ingeschakeld, zoeken de clients naar een ander software-updatepunt bij de volgende scan.

Zie voor meer informatie [plannen voor software-updates in Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_ManuallySwitchSUPs).

### <a name="restart-options-for-windows-10-clients-after-software-update-installation"></a>Opties voor het opnieuw opstarten van Windows 10-clients na de installatie van een software-update
Wanneer een software-update waarvoor opnieuw opstarten wordt geïmplementeerd met behulp van Configuration Manager en op een computer is geïnstalleerd, wordt opnieuw gepland. Een dialoogvenster voor opnieuw opstarten wordt ook weergegeven. Vanaf Configuration Manager versie 1606, de opties **bijwerken en opnieuw opstarten** en **bijwerken en afsluiten** beschikbaar zijn wanneer er een te worden opgestart voor een software-update van Configuration Manager. Deze zijn beschikbaar in de Windows-Energiebeheer van Windows 10-computers. Als u een van deze opties, weergegeven het dialoogvenster voor opnieuw opstarten niet nadat de computer opnieuw is opgestart.

Zie voor meer informatie [plannen voor software-updates in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_RestartOptions).

### <a name="run-software-updates-compliance-scan-immediately-after-a-client-installs-software-updates-and-restarts"></a>Nalevingsscan voor software-updates direct nadat software-updates zijn geïnstalleerd en opnieuw opgestart uitvoeren
U kunt nu een compatibiliteitsscan uitvoeren direct nadat software-updates zijn geïnstalleerd en opnieuw is opgestart. Op instellen voor een implementatie van de **gebruikerservaring** pagina van de Wizard Software implementeren Updates, selecteer **als een update in deze implementatie nodig is door het systeem opnieuw op, voer evaluatiecyclus voor implementatie na opnieuw opstarten van updates**. Hiermee kan de client om te controleren op aanvullende software-updates nadat de client opnieuw is opgestart, en vervolgens deze installeren (en zorgen voor naleving) tijdens datzelfde onderhoudsvenster. Zie voor meer informatie [softwareupdates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates) of [software-updates handmatig implementeren](/sccm/sum/deploy-use/manually-deploy-software-updates).

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen

### <a name="improvements-to-the-task-sequence-step-install-software-updates"></a>Verbeteringen in de takenreeksstap: Software-updates installeren
Een nieuwe instelling **software-updates uit scanresultaten in het cachegeheugen evalueren**, geeft u de optie om een volledige scan voor software-updates in plaats van de scanresultaten in het cachegeheugen. Zie voor meer informatie [takenreeksstappen in System Center Configuration Manager](../../../osd/understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates).

Ook een nieuwe takenreeksvariabele, **SMSTSSoftwareUpdateScanTimeout**, beschikbaar is. Deze variabele kunt u bepalen van de time-out voor de controle van de software-updates tijdens de takenreeksstap Software-Updates installeren. De standaardwaarde is 30 minuten. Zie voor meer informatie [ingebouwde variabelen voor takenreeksen in System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="osdpreservedriveletter-task-sequence-variable-has-been-deprecated"></a>Takenreeksvariabele OSDPreserveDriveLetter is afgeschaft.
De takenreeksvariabele OSDPreserveDriveLetter is afgeschaft. Vanaf Configuration Manager versie 1606, bepaalt Windows Setup het beste stationsletter (meestal C:) tijdens de implementatie van een besturingssysteem om standaard te gebruiken.

Zie voor meer informatie [ingebouwde variabelen voor takenreeksen in System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="customize-the-ramdisk-tftp-window-size-for-pxe-enabled-distribution-points"></a>De RamDisk TFTP-venstergrootte voor distributiepunten met PXE-functionaliteit aanpassen
U kunt nu de venstergrootte RamDisk voor distributiepunten met PXE-functionaliteit aanpassen. Als u uw netwerk hebt aangepast, dit kan ertoe leiden dat downloaden van de opstartinstallatiekopie mislukt met een time-outfout omdat de grootte van het venster te groot. De RamDisk Trivial File Transfer Protocol (TFTP) venster-venstergrootteaanpassing kunt u de TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten.

Zie voor meer informatie [sitesysteemrollen voorbereiden voor besturingssysteemimplementaties met System Center Configuration Manager](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="compliance-settings"></a>Instellingen voor naleving

### <a name="smart-lock-setting-for-android-devices"></a>Smart Lock-instelling voor Android-apparaten
Een nieuwe instelling **toestaan Smart Lock en andere vertrouwde agents**, is toegevoegd aan de configuratie-item voor Android en Samsung KNOX Standard.

Deze instelling kunt u de Smart Lock-functie op compatibele Android-apparaten beheren. Met deze telefoonmogelijkheid, soms ook wel 'trustagenten', kunt u uitschakelen of het wachtwoord van het apparaat vergrendelen scherm overslaan als het apparaat zich in een vertrouwde locatie. Een vertrouwde locatie kan bijvoorbeeld wanneer deze is verbonden met een bepaald Bluetooth-apparaat, of wanneer het is in de buurt van een NFC-tag bevindt. U kunt deze instelling gebruiken om te voorkomen dat gebruikers Smart Lock configureren.

Zie voor meer informatie [het maken van configuratie-items voor Android en Samsung KNOX Standard-apparaten worden beheerd zonder de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).

## <a name="device-configuration-and-protection"></a>Apparaatconfiguratie en -beveiliging

### <a name="product-name-changes"></a>Productnaam wordt gewijzigd

* Microsoft Passport for Work is nu bekend als **Windows Hello voor bedrijven**.
* Ondernemingsgegevensbescherming is nu bekend als **Windows Information Protection**.

### <a name="deployment-of-windows-hello-for-business-passport-for-work"></a>Implementatie van Windows Hello voor bedrijven (Passport for Work.)

U kunt nu Windows Hello voor bedrijven-beleid voor het domein Windows 10-apparaten worden beheerd door Configuration Manager-client.

De Configuration Manager-console is bijgewerkt om deze wijzigingen weer te geven.

### <a name="ios-activation-lock"></a>iOS-Activeringsvergrendeling
Configuration Manager kunt u iOS-Activeringsvergrendeling, een functie van de Zoek mijn iPhone-app voor iOS 7.1 en hoger apparaten beheren. Nadat de activeringsvergrendeling is ingeschakeld, moeten de Apple ID en het wachtwoord van de gebruiker worden ingevoerd voordat een van de volgende handelingen kan worden verricht:
* Zoek mijn iPhone uitschakelen.
* Het apparaat wissen.
* Het apparaat opnieuw activeren.

Configuration Manager kan u op twee manieren helpen met het beheer van de activeringsvergrendeling:

- Door activeringsvergrendeling op apparaten met supervisie in te schakelen.
- Door bypass van activeringsvergrendeling op apparaten met supervisie in te schakelen.

Zie voor meer informatie [beheren van iOS-Activeringsvergrendeling met System Center Configuration Manager](../../../mdm/deploy-use/manage-ios-activation-lock.md).


### <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

Endpoint Protection kunt beheren en controleren van Windows Defender Advanced Threat Protection (ATP). Windows Defender ATP is een nieuwe service waarmee ondernemingen te detecteren, onderzoeken en reageren op geavanceerde aanvallen in hun netwerken. Configuration Manager-beleid kunnen u helpen bij het vrijgeven en beheerde computers bewaken met Windows 10 versie 1607 (build 14328) of hoger.

Zie voor meer informatie [Windows Defender Advanced Threat Protection](../../../protect/deploy-use/windows-defender-advanced-threat-protection.md).

### <a name="device-categories"></a>Categorieën voor apparaatstuurprogramma
U kunt apparaatcategorieën die kunnen worden gebruikt om apparaten in apparaatverzamelingen automatisch wanneer u van Configuration Manager met Microsoft Intune gebruikmaakt kunt maken. Gebruikers hoeven vervolgens een apparaatcategorie kiezen wanneer ze een apparaat bij Intune inschrijven. Bovendien kunt u de categorie van een apparaat van de Configuration Manager-console.

Zie voor meer informatie [hoe apparaten automatisch categoriseren in verzamelingen met System Center Configuration Manager](../../../core/clients/manage/collections/automatically-categorize-devices-into-collections.md).

### <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Apparaten met IMEI-nummer of iOS-serienummers labelen

U kunt apparaten in Bedrijfseigendom identificeren met hun nummers van international station mobile equipment identity (IMEI-nummer) of een iOS-serienummers importeren. U kunt een door komma's gescheiden waarden (.csv)-bestand met IMEI-nummers van apparaten uploaden of u kunt de apparaatgegevens handmatig invoeren. Geïmporteerde gegevens wordt het eigendom van de apparaten die worden ingeschreven als 'Bedrijfseigendom' ingesteld in een lijst met apparaten. Een Intune-licentie is nog steeds vereist zijn voor elke gebruiker die toegang heeft tot de service.

Zie voor meer informatie [apparaten met IMEI-nummer of iOS-serienummers labelen](../../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

### <a name="on-premises-health-attestation-service-communication"></a>Lokale Health Attestation-servicecommunicatie

U kunt nu bewaking voor Windows 10-pc's met behulp van alleen on-premises infrastructuur Health Attestation-services inschakelen, zodat computers zonder Internet toegang hebben tot rapport apparaat Health Attestation (DHA) kunt gebruiken.

Zie voor meer informatie [Health attestation voor System Center Configuration Manager](../../../core/servers/manage/health-attestation.md#how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers).  

## <a name="remote-control"></a>Extern beheer
Uw gebruikers de mogelijkheid om te accepteren of weigeren van bestandsoverdrachten voordat de overdracht van inhoud van het gedeelde Klembord in een sessie voor extern beheer toestaan. Gebruikers hoeven alleen te machtigen eenmaal per sessie en de viewer heeft niet de mogelijkheid zelf om toestemming te geven om door te gaan met de bestandsoverdracht. U vindt deze nieuwe instelling in de **beheer** werkruimte. Ga naar **clientinstellingen**, en klik vervolgens in **standaardinstellingen**, open de **externe hulpprogramma's** Configuratiescherm.
