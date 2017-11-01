---
title: Implementaties van besturingssystemen bewaken
titleSuffix: Configuration Manager
description: De Configuration Manager-console biedt om u te helpen controleren besturingssysteem-implementatie-objecten, waarschuwingen, rapporten en verschillende statusindicatoren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08085d94-295c-432f-b5e3-9736bce0193b
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 2e738b0ae9bd16829857edfaae0fb7e398979627
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="monitor-operating-system-deployments-in-system-center-configuration-manager"></a>Implementaties van besturingssystemen in System Center Configuration Manager controleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De Configuration Manager-console biedt de volgende manieren om te controleren van besturingssysteem-implementatie-objecten.  


##  <a name="BKMK_OSDAlerts"></a> Waarschuwingen voor besturingssysteemimplementaties  
 U kunt een waarschuwing configureren in de instellingen voor takenreeksimplementaties om gebruikers met beheerdersrechten te waarschuwen wanneer compatibiliteitsniveaus voor de implementatie onder het geconfigureerde percentage uitkomen.  

 Nadat u de instellingen voor waarschuwingen hebt geconfigureerd als de opgegeven voorwaarden wordt voldaan, wordt in Configuration Manager een waarschuwing genereert. U kunt waarschuwingen voor takenreeksimplementaties op de volgende locaties bekijken:  

1.  U kunt recente waarschuwingen bekijken in het knooppunt **Besturingssystemen** in de werkruimte **Softwarebibliotheek** .  

2.  U kunt de geconfigureerde waarschuwingen beheren in het knooppunt **Waarschuwingen** in de werkruimte **Controle** .  

##  <a name="BKMK_TSDeployStatus"></a> Status van de takenreeksimplementatie  
 Nadat u een takenreeks hebt geïmplementeerd, kunt u de implementatiestatus controleren. Gebruik de volgende procedure om de implementatiestatus van een takenreeks te controleren.  

#### <a name="to-monitor-deployment-status"></a>De implementatiestatus controleren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Klik in de werkruimte Controle op **Implementaties**.  

3.  Klik op de takenreeks waarvoor u de implementatiestatus wilt controleren.  

4.  Klik op het tabblad **Starten** in de groep **Implementatie** op **Status weergeven**.  

##  <a name="BKMK_TSReports"></a> Rapporten voor besturingssysteemimplementaties  
 Er zijn veel vooraf gedefinieerde rapporten voor besturingssysteemimplementaties beschikbaar. Deze zijn ingedeeld in verscheidene categorieën en kunnen worden gebruikt voor het rapporteren van specifieke informatie over statusmigratie en takenreeksimplementaties. U kunt naast deze vooraf geconfigureerde rapporten ook aangepaste software-updaterapporten maken op basis van de behoeften van uw bedrijf. Zie voor meer informatie [bewerkingen en onderhoud voor rapportage](../../core/servers/manage/operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_MonitorContent"></a> Inhoud controleren  
 U kunt de inhoud in de Configuration Manager-console om te controleren van de status van alle pakkettypen in relatie tot de gekoppelde distributiepunten bewaken. Dit kan het volgende omvatten: de validatiestatus voor de inhoud in het pakket, de status van inhoud die is toegewezen aan een specifieke distributiepuntengroep, de status van inhoud die is toegewezen aan een distributiepunt en de status van optionele functies voor de afzonderlijke distributiepunten (inhoudvalidatie, PXE en multicast).  

###  <a name="BKMK_ContentStatus"></a> Controle van de status van inhoud  
 Het knooppunt **Status van inhoud** in de werkruimte **Controle** biedt informatie over inhoudspakketten. U kunt algemene informatie over het pakket, de distributiestatus voor het pakket en gedetailleerde statusinformatie over het pakket weergeven. Gebruik de volgende procedure om de status van inhoud weer te geven.  

#### <a name="to-monitor-content-status"></a>De status van inhoud controleren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte Controle het knooppunt **Distributiestatus**uit en klik vervolgens op **Inhoudsstatus**. De pakketten worden weergegeven.  

3.  Selecteer het pakket waarvoor u gedetailleerde statusinformatie wilt weergeven.  

4.  Klik op het tabblad **Start** op **Status weergeven**. De gedetailleerde statusinformatie voor het pakket wordt weergegeven.  

###  <a name="BKMK_DPGroupStatus"></a> Status van distributiepuntengroep  
 Het knooppunt **Status van distributiepuntengroep** in de werkruimte **Controle** biedt informatie over distributiepuntengroepen. U kunt algemene informatie weergeven over de distributiepuntengroep, zoals de status van de distributiepuntengroep en het compatibiliteitspercentage, evenals gedetailleerde statusinformatie voor de distributiepuntengroep. Gebruik de volgende procedure om de status van een distributiepuntengroep weer te geven.  

#### <a name="to-monitor-distribution-point-group-status"></a>De status van een distributiepuntengroep bewaken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte Controle het knooppunt **Distributiestatus**uit en klik vervolgens op **Status van distributiepuntengroep**. De distributiepuntengroepen worden weergegeven.  

3.  Selecteer de distributiepuntengroep waarvoor u gedetailleerde statusinformatie wilt weergeven.  

4.  Klik op het tabblad **Start** op **Status weergeven**. Er wordt gedetailleerde statusinformatie voor de distributiepuntengroep weergegeven.  

###  <a name="BKMK_DPConfigStatus"></a> Configuratiestatus van distributiepunt  
 Het knooppunt **Configuratiestatus van distributiepunt** in de werkruimte **Controle** biedt informatie over de distributiepuntengroep. U kunt weergeven welke kenmerken voor het distributiepunt zijn ingeschakeld, zoals PXE, multicast en validatie van inhoud. U kunt tevens gedetailleerde statusinformatie voor het distributiepunt weergeven. Gebruik de volgende procedure om de configuratiestatus van een distributiepuntengroep weer te geven.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>Bewaken van de configuratiestatus van distributiepunten  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte Bewaking **Distributiestatus**uit en klik vervolgens op **Configuratiestatus van distributiepunt**. De distributiepunten worden weergegeven.  

3.  Selecteer het distributiepunt waarvoor u de statusinformatie wilt weergeven.  

4.  Klik op het tabblad **Details** in het resultatenvenster. De statusinformatie voor het distributiepunt wordt weergegeven.  
