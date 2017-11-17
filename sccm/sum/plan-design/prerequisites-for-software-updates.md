---
title: Vereisten voor software-updates
titleSuffix: Configuration Manager
description: Meer informatie over vereisten voor softwareupdates in System Center Configuration Manager.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.openlocfilehash: 905ecc023dd181a8d4801860898b05aff5e4e07f
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2017
---
# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>Vereisten voor software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp worden de vereisten voor software-updates in System Center Configuration Manager. De externe en interne afhankelijkheden voor beide worden in afzonderlijke tabellen vermeld.  

## <a name="software-update-dependencies-external-to-configuration-manager"></a>Software-Update afhankelijkheden extern aan Configuration Manager  
 De volgende secties worden de externe afhankelijkheden voor software-updates.  

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Internet Information Services (IIS) moet zich op de sitesysteemservers om uit te voeren van de software-updatepunt, het beheerpunt en het distributiepunt. Zie voor meer informatie [vereisten voor sitesysteemrollen](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)  
 WSUS wordt vereist voor synchronisatie van software-updates en voor de compatibiliteitbeoordelingsscan van de software-updates op clients. De WSUS-server moet worden geïnstalleerd voordat u de sitesysteemrol voor het software-updatepunt maakt. De volgende versies van WSUS worden ondersteund voor een software-updatepunt:  

-   WSUS 4 (rol in Windows Server 2012 en Windows Server 2012 R2)  

-   WSUS 3.2 (rol in Windows Server 2008 R2)  

 Wanneer u meerdere software-updatepunten op een site hebt, waarborgen dat ze alle dezelfde versie van WSUS.  

> [!WARNING]  
>  De **Upgrades** software-updates classificatie alleen wordt ondersteund vanaf WSUS 4.0. Voordat u deze nieuwe classificatie synchroniseert en daarmee Windows 10-computers in een Windows-10 onderhoudsschema kunt evalueren, is het essentieel dat u [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS installeert op uw software-updatepunten en siteservers. Deze hotfix schakelt WSUS in op een Windows Server 2012- of een Windows Server 2012 R2-server om te synchroniseren en functie-upgrades voor Windows 10 te distribueren. Zie voor meer informatie [Windows beheren als een service](../../osd/deploy-use/manage-windows-as-a-service.md).  
>   
>  Als u software-updates synchroniseert met de classificatie **Upgrades** voordat u [hotfix 3095113](https://support.microsoft.com/kb/3095113)installeert, zie [Herstellen als u de categorie Upgrades hebt gesynchroniseerd voordat u KB 3095113 installeert](#BKMK_RecoverUpgrades)beschreven.  

### <a name="wsus-administration-console"></a>WSUS-beheerconsole  
 De WSUS-beheerconsole is vereist op de siteserver van Configuration Manager wanneer het software-updatepunt op een externe sitesysteemserver bevindt en WSUS niet al is geïnstalleerd op de siteserver.  

> [!IMPORTANT]  
>  De WSUS-versie op de siteserver moet hetzelfde zijn als de WSUS-versie waarop de software-updatepunten.  

> [!IMPORTANT]  
>  Gebruik niet de WSUS-beheerconsole om WSUS-instellingen te configureren. Configuration Manager maakt verbinding met WSUS die wordt uitgevoerd op het software-updatepunt en configureert de toepasselijke instellingen.  

### <a name="windows-update-agent-wua"></a>Windows Update Agent (WUA)  
 De WUA-client is vereist op clients om verbinding te maken met de WSUS-server en om de lijst met software-updates op te halen die moet worden gescand voor compatibiliteit.  

 Wanneer u Configuration Manager installeert, wordt de meest recente versie van de WUA gedownload. Vervolgens, wanneer de Configuration Manager-client is geïnstalleerd, wordt de WUA indien nodig bijgewerkt. Als de installatie mislukt, moet u echter een andere methode gebruiken om de WUA bij te werken.  

## <a name="software-update-dependencies-internal-to-configuration-manager"></a>Software-Update afhankelijkheden intern aan Configuration Manager  
 De volgende secties worden de interne afhankelijkheden voor software-updates in Configuration Manager.  

### <a name="management-points"></a>Beheerpunten  
 Via beheerpunten wordt informatie overgedragen tussen clientcomputers en de Configuration Manager-site. Beheerpunten zijn vereist voor software-updates.  

### <a name="software-update-point"></a>Software-updatepunt  
 U moet een software-updatepunt installeren op de WSUS-server kunnen software-updates in Configuration Manager implementeert. Zie voor meer informatie [installeren en configureren van software-updatepunt](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Distributiepunten  
 Distributiepunten zijn vereist voor het opslaan van de inhoud voor software-updates. Zie voor meer informatie over het installeren van distributiepunten en beheren van inhoud [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>Clientinstellingen voor software-updates  
 Software-updates zijn standaard ingeschakeld voor clients. Er zijn echter andere beschikbare instellingen die bepalen hoe en wanneer clients de compatibiliteit voor de software evalueren-updates en bepalen hoe de software-updates worden geïnstalleerd.  

 Zie voor meer informatie de volgende onderwerpen:  

-   [Clientinstellingen voor software-updates](../get-started/manage-settings-for-software-updates.md#BKMK_ClientSettings).   

-   [Clientinstellingen voor software-updates](../../core/clients/deploy/about-client-settings.md#software-updates) onderwerp.  

### <a name="reporting-services-point"></a>Reporting Services-punt  
 De sitesysteemrol Reporting Services kan rapporten voor software-updates weergeven. Deze rol is optioneel, maar wordt aanbevolen. Zie voor meer informatie over het maken van een reporting services-punt [Configuring reporting](../../core/servers/manage/configuring-reporting.md) .  

##  <a name="BKMK_RecoverUpgrades"></a> Herstellen als u de categorie Upgrades hebt gesynchroniseerd voordat u KB 3095113 installeert  
 U moet [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS op uw software-updatepunten en siteservers installeren voordat u de classificatie **Upgrades** synchroniseert. Als de hotfix niet was geïnstalleerd toen de classificatie **Upgrades** werd ingeschakeld, ziet WSUS de functie-upgrade voor Windows-10-build 1511, zelfs als het de gekoppelde pakketten niet juist kan downloaden en implementeren. Als u eventuele upgrades synchroniseert zonder dat u eerst [hotfix 3095113](https://support.microsoft.com/kb/3095113)hebt geïnstalleerd, wordt de WSUS-database (SUSDB) gevuld met onbruikbare gegevens die moeten worden gewist voordat upgrades op de juiste manier kunnen worden geïmplementeerd.  Gebruik de volgende procedure van dit probleem wilt herstellen.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>Herstellen van de classificatie Upgrades synchroniseren voordat u KB 3095113 installeert  

1.  Verwijderen van software-updates met de classificatie Upgrades. U kunt een PowerShell-script dat vergelijkbaar is met het volgende voorbeeldscript gebruiken:  

    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  

    > [!IMPORTANT]  
    >  U moet het script uitvoeren op alle software-updatepunten in uw Configuration Manager-hiërarchie voordat u met de volgende stap verdergaat.  

     Als u software-updates met de classificatie Upgrades bulksgewijs wilt verwijderen, kunt u het PowerShell-script aanpassen zodat het meerdere GUID's leest uit een TXT-bestand.  

2.  Schakel de **Upgrades** classificatie in de eigenschappen van Software-updatepunt (Zie voor meer informatie [classificaties en producten configureren](../get-started/configure-classifications-and-products.md)) en start synchronisatie van software-updates (Zie voor meer informatie [software-updates synchroniseren](../get-started/synchronize-software-updates.md).  

3.  Installeereer [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS installeert op uw software-updatepunten en siteservers.  

4.  Selecteer de **Upgrades** classificatie in de eigenschappen van Software-updatepunt (Zie voor meer informatie [classificaties en producten configureren](../get-started/configure-classifications-and-products.md)) en start synchronisatie van software-updates (Zie voor meer informatie [software-updates synchroniseren](../get-started/synchronize-software-updates.md).  

## <a name="next-steps"></a>Volgende stappen
[Beheer van software-updates voorbereiden](../get-started/prepare-for-software-updates-management.md)
