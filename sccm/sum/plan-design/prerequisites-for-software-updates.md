---
title: Vereisten voor software-updates
titleSuffix: Configuration Manager
description: Meer informatie over vereisten voor softwareupdates in System Center Configuration Manager.
keywords: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 02/02/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.openlocfilehash: f64647447d206a2dd53e300b143e79719cf516c5
ms.sourcegitcommit: 52080ef1b0f9a27c123711ef274ac3ffe070e8e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>Vereisten voor software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel worden de vereisten voor software-updates in System Center Configuration Manager. De externe en interne afhankelijkheden voor beide worden in afzonderlijke tabellen vermeld.  

## <a name="software-update-dependencies-that-are-external-to-configuration-manager"></a>Afhankelijkheden van de software-update die extern aan Configuration Manager  
 De volgende secties worden de externe afhankelijkheden voor software-updates.  

### <a name="internet-information-services"></a>Internet informatieservices  
 Internet Information Services (IIS) moet worden geïnstalleerd op sitesysteemservers om uit te voeren van de software-updatepunt, het beheerpunt en het distributiepunt. Zie voor meer informatie [vereisten voor sitesysteemrollen](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services"></a>Windows Server updateservices  
 Windows Server Update Services (WSUS) is nodig voor synchronisatie van software-updates en voor de controle voor toepasselijke software-updates op clients. De WSUS-server moet worden geïnstalleerd voordat u de software-updatepuntfunctie maakt. De volgende versies van WSUS worden ondersteund voor een software-updatepunt:  

-   WSUS 10.0 (rol in Windows Server 2016)
-   WSUS 6.2 en 6.3 (rol in Windows Server 2012 en Windows Server 2012 R2)  
-   WSUS 3.2 (rol in Windows Server 2008 R2)  

Wanneer u meerdere software-updatepunten op een site hebt, zorg ervoor dat ze alle dezelfde versie van WSUS uitvoert.  

> [!WARNING]  
>  De **Upgrades** classificatie voor software-updates wordt alleen ondersteund vanaf WSUS 4.0. Voordat u deze nieuwe classificatie synchroniseert en de mogelijkheid om Windows 10-computers in een Windows 10 hebben-onderhoudsplan te evalueren, is het belangrijk dat u installeert [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS op uw software update en de site -servers. Deze hotfix schakelt WSUS in op een server met Windows Server 2012 of een Windows Server 2012 R2-server synchroniseren en functie-upgrades voor Windows 10 te distribueren. Zie voor meer informatie [Windows beheren als een service](../../osd/deploy-use/manage-windows-as-a-service.md).  
>   
>  Als u software-updates synchroniseert met de classificatie **Upgrades** voordat u [hotfix 3095113](https://support.microsoft.com/kb/3095113)installeert, zie [Herstellen als u de categorie Upgrades hebt gesynchroniseerd voordat u KB 3095113 installeert](#BKMK_RecoverUpgrades)beschreven.  

### <a name="wsus-administration-console"></a>WSUS-beheerconsole  
 De WSUS-beheerconsole is vereist op de siteserver van Configuration Manager wanneer het software-updatepunt op een externe sitesysteemserver bevindt en WSUS al op de siteserver is niet geïnstalleerd.  

> [!IMPORTANT]  
> De WSUS-versie op de siteserver moet hetzelfde zijn als de WSUS-versie die wordt uitgevoerd op de software-updatepunten.
>
> Gebruik geen WSUS-beheerconsole om WSUS-instellingen te configureren. Configuration Manager maakt verbinding met het exemplaar van de WSUS die wordt uitgevoerd op het software-updatepunt en configureert de toepasselijke instellingen.  



### <a name="windows-update-agent"></a>Windows Update-agent  
 De client voor Windows Update Agent (WUA) is vereist op clients zodat ze verbinding met de WSUS-server maken kunnen. WUA haalt de lijst met software-updates die moeten worden gescand op naleving.  

 Wanneer u Configuration Manager installeert, wordt de meest recente versie van de WUA gedownload. Vervolgens, wanneer u de Configuration Manager-client installeert, de WUA indien nodig bijgewerkt wordt. Als de installatie is mislukt, moet u een andere methode gebruiken WUA bijwerken.  

## <a name="software-update-dependencies-that-are-internal-to-configuration-manager"></a>Afhankelijkheden van de software-update die intern aan Configuration Manager  
 De volgende secties worden de interne afhankelijkheden voor software-updates in Configuration Manager.  

### <a name="management-points"></a>Beheerpunten  
 Via beheerpunten wordt informatie overgedragen tussen clientcomputers en de Configuration Manager-site. De beheerpunten zijn vereist voor software-updates.  

### <a name="software-update-points"></a>Software-updatepunten  
 U moet een software-updatepunt installeren op de WSUS-server kunnen software-updates in Configuration Manager implementeert. Zie voor meer informatie [installeren en configureren van software-updatepunt](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Distributiepunten  
 Distributiepunten zijn vereist voor het opslaan van de inhoud voor software-updates. Zie voor meer informatie over het installeren van distributiepunten en beheren van inhoud [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>Clientinstellingen voor software-updates  
 Software-updates zijn standaard ingeschakeld voor clients. Er zijn echter andere instellingen beschikbaar die regelen hoe en wanneer clients de compatibiliteit voor de software-updates evalueren en bepalen hoe de software-updates worden geïnstalleerd.  

 Zie voor meer informatie de volgende artikelen:  

-   [Clientinstellingen voor software-updates](../get-started/manage-settings-for-software-updates.md#BKMK_ClientSettings)   

-   [Clientinstellingen voor software-updates](../../core/clients/deploy/about-client-settings.md#software-updates)  

### <a name="reporting-services-points"></a>Reporting Services-punten  
 De sitesysteemrol Reporting Services kan rapporten voor software-updates weergeven. Deze rol is optioneel maar aanbevolen. Zie voor meer informatie over het maken van een reporting services-punt [Configuring reporting](../../core/servers/manage/configuring-reporting.md).  

##  <a name="BKMK_RecoverUpgrades"></a> Herstellen als u de categorie Upgrades hebt gesynchroniseerd voordat u KB 3095113 installeert  
 U moet [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS op uw software-updatepunten en siteservers installeren voordat u de classificatie **Upgrades** synchroniseert. Als de hotfix niet is geïnstalleerd toen de **Upgrades** classificatie is ingeschakeld, ziet WSUS het Windows 10-build 1511 functie-upgrade zelfs als deze niet correct downloaden en implementeren van de gekoppelde pakketten. 
 
 Als u eventuele upgrades synchroniseert zonder dat eerst geïnstalleerd [hotfix 3095113](https://support.microsoft.com/kb/3095113), vullen van de WSUS-database (SUSDB) met onbruikbare gegevens. Dat gegevens moeten worden gewist voordat upgrades kan goed worden geïmplementeerd. Gebruik de volgende procedure van dit probleem wilt herstellen.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>Herstellen van de classificatie Upgrades synchroniseren voordat u KB 3095113 installeert  

1.  Verwijderen van software-updates met de **Upgrades** classificatie. U kunt een PowerShell-script die vergelijkbaar is met het volgende voorbeeldscript gebruiken:  

    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  

    > [!IMPORTANT]  
    >  U moet het script uitvoeren op alle software-updatepunten in uw Configuration Manager-hiërarchie voordat u met de volgende stap verdergaat.  

     Voor het bulksgewijs verwijderen software-updates met de **Upgrades** indeling, kunt u de PowerShell-script voor het meerdere GUID's leest uit een tekstbestand.  

2.  Schakel de **Upgrades** classificatie in de eigenschappen van Software-updatepunt. (Zie voor meer informatie [classificaties en producten configureren](../get-started/configure-classifications-and-products.md).) Start vervolgens de synchronisatie van software-updates. (Zie voor meer informatie [software-updates synchroniseren](../get-started/synchronize-software-updates.md).)  

3.  Installeereer [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS installeert op uw software-updatepunten en siteservers.  

4.  Selecteer de **Upgrades** classificatie in de eigenschappen van Software-updatepunt. (Zie voor meer informatie [classificaties en producten configureren](../get-started/configure-classifications-and-products.md).) Vervolgens start u de synchronisatie van software-updates. (Zie voor meer informatie [software-updates synchroniseren](../get-started/synchronize-software-updates.md).)  

## <a name="next-steps"></a>Volgende stappen
[Beheer van software-updates voorbereiden](../get-started/prepare-for-software-updates-management.md)
