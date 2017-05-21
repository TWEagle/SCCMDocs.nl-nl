---

title: Software-updates bewaken | Microsoft-documenten
description: De System Center Configuration Manager-console geeft waarschuwingen en statussen voor het bewaken van updates en naleving.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 9afd7b0f-5c8e-48bc-9a65-1f7d74103688
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: 956ef263a1c178b5ab5926705859f4b2d0ae5bc7
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="monitor-software-updates-in-system-center-configuration-manager"></a>Het software-updates in System Center Configuration Manager controleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager biedt veel manieren om te helpen u bij het controleren van objecten voor software-updates, processen en compatibiliteitsinformatie. Gebruik de volgende secties voor het bewaken van software-updates.

## <a name="software-updates-dashboard"></a>Dashboard voor software-updates
U start in Configuration Manager versie 1610, kunt u het Dashboard van Software-Updates weergeven van de huidige status van naleving van apparaten in uw organisatie en sneller kunt analyseren van de gegevens te zien welke apparaten zijn kwetsbaar voor. De als dashboard wilt weergeven, gaat u naar **bewaking** > **overzicht** > **beveiliging** > **Software-Updates Dashboard**.   

##  <a name="BKMK_SUAlerts"></a> Waarschuwingen voor software-updates  
 U kunt waarschuwingen voor software-updates configureren om gebruikers met beheerdersrechten te waarschuwen wanneer compatibiliteitsniveaus voor implementaties van software-updates onder het geconfigureerde percentage uitkomen. U kunt op de volgende locaties waarschuwingen voor implementaties van software-updates configureren:  

-   ADR-instelling: U kunt de instellingen voor waarschuwingen configureren in de Wizard regel voor automatische implementatie en in de eigenschappen voor de ADR.  

-   Implementatie-instelling: U kunt de instellingen voor waarschuwingen configureren in de Wizard Software-Updates implementeren en implementatie-eigenschappen.  

Nadat u de instellingen voor waarschuwingen hebt geconfigureerd als de opgegeven voorwaarden wordt voldaan, wordt Configuration Manager een waarschuwing gegenereerd. U kunt de waarschuwingen voor software-updates op de volgende locaties weergeven:  

1.  U kunt recente waarschuwingen weergeven in het knooppunt **Software-updates** in de werkruimte **Softwarebibliotheek** .  

2.  U kunt de geconfigureerde waarschuwingen beheren in het knooppunt **Waarschuwingen** in de werkruimte **Controle** .  

##  <a name="BKMK_SUSyncStatus"></a> Synchronisatiestatus van software-updates  
 Nadat u het synchronisatieproces hebt gestart, kunt u het synchronisatieproces van de Configuration Manager-console voor alle software-updatepunten in uw hiërarchie bewaken. Gebruik de volgende procedure om het synchronisatieproces voor software-updates te controleren.  

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>Het synchronisatieproces voor software-updates controleren  

- Navigeer in de Configuration Manager-console naar **bewaking** > **overzicht** > **synchronisatiestatus van Software-Update**.  

    De software-updatepunten in uw Configuration Manager-hiërarchie worden weergegeven in het deelvenster met resultaten. In deze weergave kunt u de synchronisatiestatus van alle software-updatepunten controleren. U kunt meer gedetailleerde informatie over het synchronisatieproces kunt u het bestand wsyncmgr.log openen dat zich bevindt in bekijken <*Configmgrinstallatiepad*> \Logs op elke siteserver.  

##  <a name="BKMK_SUDeployStatus"></a> Implementatiestatus van software-updates  
 Nadat u de software-updates in een software-updategroep hebt geïmplementeerd of nadat u een afzonderlijke software-updates hebt geïmplementeerd, kunt u de implementatiestatus controleren. Gebruik de volgende procedure om de implementatiestatus van een software-updategroep of software-update te controleren.  

#### <a name="to-monitor-deployment-status"></a>De implementatiestatus controleren  

1.  Navigeer in de Configuration Manager-console naar **bewaking** > **overzicht** > **implementaties**.  

2.  Klik op de software-updategroep of software-update waarvan u de implementatiestatus wilt controleren.  

3.  Klik op het tabblad **Starten** in de groep **Implementatie** op **Status weergeven**.  

##  <a name="BKMK_SUReports"></a> Rapporten van software-updates  
 De statusberichten voor software-updates bieden informatie over de compatibiliteit van software-updates en over de evaluatie en afdwingingsstatus van implementaties van software-updates. U kunt software-updaterapporten uitvoeren om deze statusberichten weer te geven. Er zijn meer dan 30 vooraf gedefinieerde software-updaterapporten beschikbaar. Deze zijn ingedeeld in verscheidene categorieën die kunnen worden gebruikt voor het rapporteren van specifieke informatie over software-updates en implementaties. U kunt naast deze vooraf geconfigureerde rapporten ook aangepaste software-updaterapporten maken op basis van de behoeften van uw bedrijf. Zie voor meer informatie [bewerkingen en onderhoud voor rapportage](../../core/servers/manage/operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_MonitorContent"></a> Inhoud controleren  
 U kunt inhoud in de Configuration Manager-console te bekijken van de status voor alle pakkettypen in relatie tot de gekoppelde distributiepunten bewaken. Dit kan het volgende omvatten: de validatiestatus voor de inhoud in het pakket, de status van inhoud die is toegewezen aan een specifieke distributiepuntengroep, de status van inhoud die is toegewezen aan een distributiepunt en de status van optionele functies voor de afzonderlijke distributiepunten (inhoudvalidatie, PXE en multicast).  

###  <a name="BKMK_ContentStatus"></a> Controle van de status van inhoud  
 Het knooppunt **Status van inhoud** in de werkruimte **Controle** biedt informatie over inhoudspakketten. U kunt algemene informatie over het pakket, de distributiestatus voor het pakket en gedetailleerde statusinformatie over het pakket weergeven. Gebruik de volgende procedure om de status van inhoud weer te geven.  

#### <a name="to-monitor-content-status"></a>De status van inhoud controleren  

1.  Navigeer in de Configuration Manager-console naar **bewaking** > **overzicht** > **distributiestatus** > **inhoudsstatus**. De pakketten worden weergegeven.  

2.  Selecteer het pakket waarvoor u gedetailleerde statusinformatie wilt weergeven.  

3.  Klik op het tabblad **Start** op **Status weergeven**. De gedetailleerde statusinformatie voor het pakket wordt weergegeven.  

###  <a name="BKMK_DPGroupStatus"></a> Status van distributiepuntengroep  
 Het knooppunt **Status van distributiepuntengroep** in de werkruimte **Controle** biedt informatie over distributiepuntengroepen. U kunt algemene informatie weergeven over de distributiepuntengroep, zoals de status van de distributiepuntengroep en het compatibiliteitspercentage, evenals gedetailleerde statusinformatie voor de distributiepuntengroep. Gebruik de volgende procedure om de status van een distributiepuntengroep weer te geven.  

#### <a name="to-monitor-distribution-point-group-status"></a>De status van een distributiepuntengroep bewaken  

1.  Navigeer in de Configuration Manager-console naar **bewaking** > **overzicht** > **distributiestatus** > **Distributiepuntengroep**. De distributiepuntengroepen worden weergegeven.  

2.  Selecteer de distributiepuntengroep waarvoor u gedetailleerde statusinformatie wilt weergeven.  

3.  Klik op het tabblad **Start** op **Status weergeven**. Er wordt gedetailleerde statusinformatie voor de distributiepuntengroep weergegeven.  

###  <a name="BKMK_DPConfigStatus"></a> Configuratiestatus van distributiepunt  
 Het knooppunt **Configuratiestatus van distributiepunt** in de werkruimte **Controle** biedt informatie over de distributiepuntengroep. U kunt weergeven welke kenmerken voor het distributiepunt zijn ingeschakeld, zoals PXE, multicast en validatie van inhoud. U kunt tevens gedetailleerde statusinformatie voor het distributiepunt weergeven. Gebruik de volgende procedure om de configuratiestatus van een distributiepuntengroep weer te geven.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>Bewaken van de configuratiestatus van distributiepunten  

1.  Navigeer in de Configuration Manager-console naar **bewaking** > **overzicht** > **distributiestatus** > **Distributiepuntconfiguraties**. De distributiepunten worden weergegeven.  

2.  Selecteer het distributiepunt waarvoor u de statusinformatie wilt weergeven.  

3.  Klik op het tabblad **Details** in het resultatenvenster. De statusinformatie voor het distributiepunt wordt weergegeven.  

