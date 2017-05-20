---
title: Nieuw in System Center Configuration Manager bijwerken 1606 | Microsoft-documenten
description: "Meer informatie over deze wijzigingen en nieuwe functies die zijn geïntroduceerd in versie 1606 van System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df2e57b9-6445-4067-98e7-ace85d4e6aa6
caps.latest.revision: 40
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 34809ddf7819eab5deb3995cd8138c7b38cd2f9a
ms.openlocfilehash: 9fdff6049d6e5cde1032864e5d7aa8df71e53686
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1606-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1606 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1606 voor System Center Configuration Manager is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1511 of 1602 wordt uitgevoerd. Versie 1511 is de initiële basislijnkopie-versie die u gebruikt om nieuwe Configuration Manager-sites te installeren.
> [!TIP]  
>  Meer informatie over:  
>   
>  -   [Installatie van nieuwe sites](/sccm/core/servers/deploy/install) (met behulp van een basislijn versie zoals 1511)  
>  -   [Installatie van updates op sites](/sccm/core/servers/manage/updates) (zoals 1602 of 1606 bijwerken)  

 De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die is geïntroduceerd in versie 1606 van Configuration Manager.  



## <a name="updatesandservicing"></a>Updates en onderhoud

### <a name="changes-for-the-updates-and-servicing-node"></a>Wijzigingen voor de Updates en onderhoud van knooppunt
De volgende zijn wijzigingen in de Updates en onderhoud knooppunt in de Configuration Manager-console:
> [!NOTE]
> Deze wijzigingen zijn pas beschikbaar nadat 1606-versie is geïnstalleerd.

- **Wijziging van knooppunt:**

    In de **bewaking** werkruimte de **Site Servicing status** knooppunt is gewijzigd in **Updates en onderhoud Status**.
- **Statusdetails meer installatie:**

    Als u de installatiestatus van de update voor een site bekijkt, geeft de console nu afzonderlijke details voor de volgende acties:
    - **Download** (dit geldt alleen voor de bovenste site waarop de service connection point-sitesysteemrol is geïnstalleerd.)
    - **Replicatie**
    - **Controle van vereisten**
    - **Installatie**

  Bovendien is er nu meer gedetailleerde informatie voor elke stap, inclusief welke logboekbestand kunt u bekijken voor meer informatie.  
-   **Nieuwe optie om opnieuw te proberen de vereiste fouten:**

    In zowel de **beheer** en **bewaking** werkruimten, de **Updates en onderhoud** knooppunt bevat een nieuwe knop in het lint genoemd **waarschuwingen voor vereisten negeren**.

    Wanneer u updates installeert zonder de optie waarschuwingen voor vereisten negeren (uit in de Wizard Updates), en die update-installatie wordt afgebroken vanwege een waarschuwing, kunt u selecteren **waarschuwingen voor vereisten negeren** van het lint. Dit activeert een automatische voortzetting van de installatie van updates.  



- **Schonere weergave van updates:**

    In de **Updates en onderhoud** knooppunt nu ziet u alleen de laatst geïnstalleerde update en er nieuwe updates die beschikbaar zijn voor u installeren. Als u wilt eerder geïnstalleerde updates weergeven, klikt u op de nieuwe **geschiedenis** knop die wordt weergegeven in het lint.  

-   **Nieuwe naam optie voor testomgeving:**

    In de **Updates en onderhoud** knooppunt de **opties voor de Client** knop heet nu **bevorderen pre-Productieclient**.


###  <a name="pre-release-features"></a>Pre-release functies
Beginnend met 1606, moet u toestemming geven pre-release functies gebruiken in System Center Configuration Manager voordat u kunt selecteren en hun gebruik inschakelen. Zie [Use pre-release features from updates](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease) (Functies van evaluatieversies gebruiken) voor meer informatie.

### <a name="new-distribution-point-update-behavior"></a>Nieuw punt update distributiegedrag
Update 1606 introduceert wijzigingen ter verbetering van de beschikbaarheid van distributiepunten tijdens de installatie van toekomstige updates.

Na de update 1606 is geïnstalleerd, wanneer vervolgens installeert u een update op die site waarvoor u de automatische installatie van de standard- en pull-distributiepunt sitesysteemrollen, wordt alle distributiepunten niet langer verbreken om bij te werken op hetzelfde moment. In plaats daarvan gebruikt de siteserver van de site-instellingen voor het distribueren van inhoud te distribueren van de update op een subset van distributiepunten op een bepaald moment. Het resultaat is dat alleen bepaalde distributiepunten verbreken om de update te installeren. Hiermee wordt de distributiepunten die nog niet begonnen om bij te werken of dat de update moet worden bewaard online is en kan om inhoud voor clients hebt voltooid.



## <a name="accessibility"></a>Toegankelijkheid
Om te navigeren tussen de verschillende knooppunten van een werkruimte, kunt u nu de eerste letter van de naam van een knooppunt invoeren. Elke toets verplaatst de cursor naar het volgende knooppunt dat met deze letter begint. Voor gebruikers die een Reader scherm, leest de lezer van de naam van dat knooppunt. Zie voor meer informatie over toegankelijkheidsopties [toegankelijkheidsfuncties in System Center Configuration Manager](../../../core/understand/accessibility-features.md).

## <a name="administration"></a>Beheer
De volgende zijn wijzigingen voor beheer in de Configuration Manager-console:
### <a name="oms-connector"></a>OMS-Connector

U kunt nu Configuration Manager verbinding als verzamelingen van System Center Configuration Manager naar de [Microsoft Operations Management Suite Kantoorbeheersysteem](https://azure.microsoft.com/en-us/documentation/articles/operations-management-suite-overview/). Op deze manier gegevens, zoals verzamelingen van de Configuration Manager-implementatie in OMS zichtbaar. Voor meer informatie, Zie [synchroniseren van gegevens uit Configuration Manager naar de Microsoft Operations Management-pakket hier](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md).

De Connector OMS is een voorlopige versie-functie. Als u wilt inschakelen, Zie [gebruikmaken van de functies van updates pre-release](../../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).

### <a name="support-for-cache-size-in-client-settings"></a>Ondersteuning voor cachegrootte in de clientinstellingen

Nu kunt u de grootte van de cachemap op clientcomputers met **clientinstellingen** in de Configuration Manager-console. U kunt de client-cachegrootte bij het installeren of opnieuw installeren van de clientsoftware eerder alleen instellen. Nu de cachegrootte als een clientinstelling (standaard of aangepast opgeven) en vervolgens installeert u deze instellingen toegepast met de volgende beleidsupdate op de client zonder dat een client opnieuw. Zie [De clientcache configureren voor Configuration Manager-clients](../../../core/clients/manage/manage-clients.md#BKMK_ClientCache) voor meer informatie.

## <a name="on-premises-mobile-device-management"></a>Lokale beheer van mobiele apparaten

### <a name="support-for-multiple-device-management-points"></a>Ondersteuning voor meerdere beheerpunten voor apparaat

Lokale mobiel Apparaatbeheer (MDM) biedt nu ondersteuning voor een nieuwe functie in Windows 10 Verjaardag Update die wordt automatisch geconfigureerd op een geregistreerde apparaat om meer dan één beheerpunt apparaten beschikbaar voor gebruik. Deze mogelijkheid kunt het apparaat terugvallen op een ander apparaatbeheerpunt, wanneer een normaal gesproken gebruikt niet beschikbaar is. Deze functie werkt alleen voor pc's en apparaten met de Windows 10 Verjaardag Update is geïnstalleerd.


## <a name="application-management"></a>Toepassingsbeheer

### <a name="manage-apps-from-the-windows-store-for-business"></a>Apps beheren via de Windows Store voor Bedrijven

De [Windows Store voor bedrijven](https://www.microsoft.com/business-store) kunt u vinden en koopt van Windows-apps voor uw organisatie, afzonderlijk of in volume. De store naar de Configuration Manager verbinding maakt, kunt u de lijst met apps met Configuration Manager hebt aangeschaft, weergeven in de Configuration Manager-console en deze implementeren net als elke andere app synchroniseren.

Zie voor meer informatie, [apps beheren vanuit de Windows Store voor bedrijven met System Center Configuration Manager](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business.md).

### <a name="manage-ios-volume-purchased-apps"></a>IOS-apps volume aangeschaft beheren

De werkstroom voor het beheren van volume aangeschaft iOS-apps en implementeren van deze met Configuration Manager gebruikt, is verbeterd.

Zie voor meer informatie, [volume aangeschaft iOS-apps met System Center Configuration Manager beheren](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).

### <a name="software-center-user-interface"></a>Software Center-gebruikersinterface

De Software Center-gebruikersinterface is voor de detectie van gemakkelijker gestroomlijnd.
*  De **installatiestatus** en **geïnstalleerde Software** tabbladen zijn gecombineerd in één **installatiestatus** tabblad.
*  **Updates**, **besturingssystemen**, en **toepassingen** in drie afzonderlijke tabbladen zijn gescheiden.
* Meerdere updates kunnen nu worden geselecteerd voor installatie in één keer of alle updates in één keer kunnen worden geïnstalleerd door te klikken op **installeert alle**.

### <a name="content-status-links"></a>Status van inhoud koppelingen
Op de eigenschappen van een toepassing of het pakket is nu een koppeling waarmee u de status voor dat object.

## <a name="software-updates"></a>Software-updates

### <a name="client-setting-to-manage-the-office-365-client-agent"></a>Client-instelling voor het beheren van de clientagent voor Office 365
Nu kunt u een Configuration Manager client-instelling voor het beheren van de clientagent voor Office 365. Nadat u dit instellen en implementeren van updates voor Office 365, werkt de clientagent van Configuration Manager met de Office 365-clientagent downloaden en installeren van Office 365-updates vanaf een distributiepunt.

Zie voor meer informatie, [Office 365 ProPlus beheren met Configuration Manager-updates](../../../sum/deploy-use/manage-office-365-proplus-updates.md).

### <a name="manually-switch-clients-to-a-new-software-update-point"></a>Handmatig clients overschakelen naar een nieuw software-updatepunt
U kunt nu een optie waarmee Configuration Manager de switch clients aan een nieuwe software-updatepunt wanneer er problemen met het actieve software-updatepunt zijn kunt inschakelen. Nadat deze optie is ingeschakeld, zoeken de clients naar een ander software-updatepunt bij de volgende scan.

Zie voor meer informatie, [plannen voor software-updates in Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_ManuallySwitchSUPs).

### <a name="restart-options-for-windows-10-clients-after-software-update-installation"></a>Opties voor het opnieuw opstarten van Windows 10-clients na de installatie van een software-update
Wanneer een software-update die moet worden opgestart, wordt geïmplementeerd via Configuration Manager en op een computer is geïnstalleerd, wordt opnieuw gepland. Een dialoogvenster voor opnieuw opstarten wordt ook weergegeven. Beginnen in Configuration Manager versie 1606, de opties **bijwerken en opnieuw starten** en **Update en afsluiten** beschikbaar zijn wanneer er een te worden opgestart voor een software-update van Configuration Manager. Deze zijn beschikbaar in de Windows-Energiebeheer van Windows 10-computers. Wanneer u een van deze opties, weergegeven in het dialoogvenster opnieuw opstarten nadat de computer opnieuw is opgestart.

Zie voor meer informatie, [plannen voor software-updates in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md#BKMK_RestartOptions).

### <a name="run-software-updates-compliance-scan-immediately-after-a-client-installs-software-updates-and-restarts"></a>Controle voor compatibiliteit van software-updates uitgevoerd onmiddellijk nadat een client installeert software-updates en opnieuw opstarten
U kunt nu een compatibiliteitsscan uitvoeren onmiddellijk na een client installeert software-updates en opnieuw opstarten. Op instellen voor een implementatie van de **gebruikerservaring** pagina van de Wizard Software implementeren Updates, selecteer **als er een update in deze implementatie systeem opnieuw is opgestart, worden bijgewerkt evaluatie van implementaties releasecyclus na opnieuw opstarten vereist**. Hierdoor kunnen de client om te controleren voor extra software-updates die van toepassing wanneer de client opnieuw is opgestart, en vervolgens deze providers installeren (en compatibel) tijdens het onderhoudsvenster dezelfde. Zie voor meer informatie, [software-updates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates) of [software-updates handmatig implementeert](/sccm/sum/deploy-use/manually-deploy-software-updates).

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen

### <a name="improvements-to-the-task-sequence-step-install-software-updates"></a>Verbeteringen in de takenreeksstap: Software-updates installeren
Een nieuwe instelling **evalueren van software-updates van cache scanresultaten**, geeft u de optie om een volledige scan voor software-updates in plaats van de cache scanresultaten. Zie voor meer informatie, [takenreeksstappen in System Center Configuration Manager](../../../osd/understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates).

Ook een nieuwe takenreeksvariabele, **SMSTSSoftwareUpdateScanTimeout**, beschikbaar is. Deze variabele kunt u de time-out voor de controle van de software-updates beheren tijdens de taakstap voor de Software-Updates installeren. De standaardwaarde is 30 minuten. Zie voor meer informatie, [Takenreeksvariabelen ingebouwde in System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="osdpreservedriveletter-task-sequence-variable-has-been-deprecated"></a>Takenreeksvariabele OSDPreserveDriveLetter is afgeschaft.
De OSDPreserveDriveLetter takenreeksvariabele is afgeschaft. Vanaf versie 1606 van Configuration Manager, bepaalt Windows Setup het beste stationsletter (meestal C:) tijdens de implementatie van een besturingssysteem gebruiken standaard.

Zie voor meer informatie, [Takenreeksvariabelen ingebouwde in System Center Configuration Manager](../../../osd/understand/task-sequence-built-in-variables.md).

### <a name="customize-the-ramdisk-tftp-window-size-for-pxe-enabled-distribution-points"></a>De venstergrootte RamDisk TFTP voor PXE-ingeschakelde distributiepunten aanpassen
U kunt nu de venstergrootte RamDisk voor PXE-ingeschakelde distributiepunten aanpassen. Als u uw netwerk hebt aangepast, dit kan ervoor zorgen dat het downloaden van de installatiekopie opstart mislukt met een time-outfout optreedt, omdat de grootte van het venster is te groot. De grootte aanpassing van de RamDisk Trivial File Transfer Protocol (TFTP)-venster kunt u TFTP verkeer optimaliseren wanneer u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten.

Zie voor meer informatie, [sitesysteemrollen voorbereiden voor implementaties van besturingssystemen met System Center Configuration Manager](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="compliance-settings"></a>Instellingen voor naleving

### <a name="smart-lock-setting-for-android-devices"></a>Smart Lock-instelling voor Android-apparaten
Een nieuwe instelling **Smart vergrendelen toestaan en andere vertrouwen agents**, is toegevoegd aan de configuratie-item Android en Samsung KNOX Standard.

Deze instelling kunt u de functie Smart vergrendeling op Android-compatibele apparaten beheren. Deze mogelijkheid telefoon, ook wel "vertrouwensrelatie agents", kunt u het wachtwoord van het apparaat vergrendelen scherm overslaan als het apparaat zich in een vertrouwde locatie- of uitschakelen. Een vertrouwde locatie zijn mogelijk wanneer het is verbonden met een specifiek Bluetooth-apparaat of wanneer het een tag NFC in de buurt bevindt. U kunt deze instelling gebruiken om gebruikers te verhinderen Smart vergrendelen configureren.

Zie voor meer informatie, [het maken van configuratie-items voor Android en Samsung KNOX Standard-apparaten beheerd zonder dat de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).

## <a name="device-configuration-and-protection"></a>Apparaatconfiguratie en -beveiliging

### <a name="product-name-changes"></a>Productnaam wordt gewijzigd

* Microsoft Passport for Work nu wel **Windows Hello voor bedrijven**.
* Ondernemingsgegevensbescherming nu wel **Windows Information Protection**.

### <a name="deployment-of-windows-hello-for-business-passport-for-work"></a>Implementatie van Windows Hello voor bedrijven (Passport for Work)

U kunt nu implementeren Windows Hello voor Business-beleid voor het domein Windows 10-apparaten worden beheerd door de Configuration Manager-client.

De Configuration Manager-console is bijgewerkt naar aanleiding van deze wijzigingen.

### <a name="ios-activation-lock"></a>iOS Activeringsvergrendeling
Configuration Manager kunt u iOS Activeringsvergrendeling, een functie van de Zoek mijn iPhone-app voor iOS 7.1 en hoger apparaten beheren. Nadat de activeringsvergrendeling is ingeschakeld, moeten de Apple ID en het wachtwoord van de gebruiker worden ingevoerd voordat een van de volgende handelingen kan worden verricht:
* Schakel uit Zoek mijn iPhone.
* Het apparaat wissen.
* Activeer het apparaat.

Configuration Manager kan u op twee manieren helpen met het beheer van de activeringsvergrendeling:

- Door activeringsvergrendeling op apparaten met supervisie in te schakelen.
- Door bypass van activeringsvergrendeling op apparaten met supervisie in te schakelen.

Zie voor meer informatie, [iOS Activeringsvergrendeling met System Center Configuration Manager beheren](../../../mdm/deploy-use/manage-ios-activation-lock.md).


### <a name="windows-defender-advanced-threat-protection"></a>Windows Defender geavanceerde bedreiging beveiliging

Endpoint Protection kunt beheren en controleren van Windows Defender geavanceerde bedreiging beveiliging (vrije). Windows Defender vrije is een nieuwe service waarmee ondernemingen om te detecteren, te onderzoeken en reageren op geavanceerde aanvallen op hun netwerken. Beleid van Configuration Manager kunnen u helpen voorbereiden en beheerde computers bewaken met Windows 10, versie 1607 (build 14328) of hoger.

Zie voor meer informatie, [Windows Defender geavanceerde bedreiging Protection](../../../protect/deploy-use/windows-defender-advanced-threat-protection.md).

### <a name="device-categories"></a>Categorieën voor apparaatstuurprogramma
Kunt u categorieën voor apparaatstuurprogramma die kunnen worden gebruikt om apparaten op plaatsen apparaatverzamelingen automatisch wanneer u van Configuration Manager met Microsoft Intune gebruikmaakt. Vervolgens moeten gebruikers een apparaatcategorie kiezen wanneer ze een apparaat in Intune inschrijft. Daarnaast kunt u de categorie van een apparaat van de Configuration Manager-console.

Zie voor meer informatie, [hoe apparaten automatisch categoriseren in verzamelingen met System Center Configuration Manager](../../../core/clients/manage/collections/automatically-categorize-devices-into-collections.md).

### <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Apparaten met IMEI-nummer of iOS-serienummers predeclare

U kunt apparaten in Bedrijfseigendom identificeren door hun internationale station mobile equipment identity (IMEI) getallen of iOS-serienummers importeren. U kunt een apparaat IMEI getallen met door komma's gescheiden waarden (.csv)-bestand uploaden of u kunt de apparaatgegevens handmatig invoeren. Geïmporteerde gegevens wordt het eigendom van de apparaten die worden ingeschreven als "Bedrijf" in een lijst met apparaten. Een licentie voor Intune is nog steeds vereist is voor elke gebruiker die toegang heeft tot de service.

Zie voor meer informatie [Predeclare apparaten met IMEI-nummer of iOS-serienummers](../../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

### <a name="on-premises-health-attestation-service-communication"></a>Lokale Health-verklaring servicecommunicatie

U kunt nu Attestation-Health-services voor Windows 10-computers bewaken met alleen on-premises infrastructuur inschakelen, zodat computers zonder Internet toegang hebben tot kunt rapport apparaat Health Attestation (DHA).

Zie voor meer informatie, [Health-verklaring voor System Center Configuration Manager](../../../core/servers/manage/health-attestation.md#how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers).  

## <a name="remote-control"></a>Extern beheer
Uw gebruikers aangeven of u wilt accepteren of weigeren bestandsoverdrachten voordat de overdracht van inhoud van het gedeelde Klembord in een sessie voor extern beheer toestaan. Gebruikers hoeven alleen te machtigen eenmaal per sessie en de viewer heeft geen kunnen zichzelf machtigen om door te gaan met de bestandsoverdracht. U vindt deze nieuwe instelling in de **beheer** werkruimte. Ga naar **clientinstellingen**, en klik vervolgens in **standaardinstellingen**, open het **externe hulpprogramma's** Configuratiescherm.

