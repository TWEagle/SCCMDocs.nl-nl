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
ms.openlocfilehash: 1907ff5bf6b1146b967e64bd381915ac863b3e55
ms.sourcegitcommit: 389c4e5b4e9953b74c13b1689195f99c526fa737
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/09/2018
---
# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>Vereisten voor software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel worden de vereisten voor software-updates in System Center Configuration Manager. De externe en interne afhankelijkheden voor beide worden in afzonderlijke tabellen vermeld.  

## <a name="software-update-dependencies-external-to-configuration-manager"></a>Software-Update afhankelijkheden extern aan Configuration Manager  
 De volgende secties worden de externe afhankelijkheden voor software-updates.  

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Internet Information Services (IIS) moet zich op de sitesysteemservers om uit te voeren van de software-updatepunt, het beheerpunt en het distributiepunt. Zie voor meer informatie [vereisten voor sitesysteemrollen](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)  
 WSUS is nodig voor synchronisatie van software-updates en voor de controle voor toepasselijke software-updates op clients. De WSUS-server moet worden geïnstalleerd voordat u de software-updatepuntfunctie maakt. De volgende versies van WSUS worden ondersteund voor een software-updatepunt:  

-   WSUS 10.0 (rol in Windows Server 2016)
-   WSUS 6.2 en 6.3 (rol in Windows Server 2012 en Windows Server 2012 R2)  
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
 De WUA-client is vereist op clients om verbinding met de WSUS-server. WUA haalt de lijst met software-updates die moeten worden gescand op naleving.  

 Wanneer u Configuration Manager installeert, wordt de meest recente versie van de WUA gedownload. Vervolgens, wanneer de Configuration Manager-client is geïnstalleerd, wordt de WUA indien nodig bijgewerkt. Als de installatie mislukt, moet u echter een andere methode gebruiken om de WUA bij te werken.  

## <a name="software-update-dependencies-internal-to-configuration-manager"></a>Software-Update afhankelijkheden intern aan Configuration Manager  
 De volgende secties worden de interne afhankelijkheden voor software-updates in Configuration Manager.  

### <a name="management-points"></a>Beheerpunten  
 Via beheerpunten wordt informatie overgedragen tussen clientcomputers en de Configuration Manager-site. Beheerpunten zijn vereist voor software-updates.  

### <a name="software-update-point"></a>Sitesysteemrollen toevoegen  
 U moet een software-updatepunt installeren op de WSUS-server kunnen software-updates in Configuration Manager implementeert. Zie voor meer informatie [installeren en configureren van software-updatepunt](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Distributiepunten  
 Distributiepunten zijn vereist voor het opslaan van de inhoud voor software-updates. Zie voor meer informatie over het installeren van distributiepunten en beheren van inhoud [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>Clientinstellingen voor software-updates  
 Software-updates zijn standaard ingeschakeld voor clients. Er zijn echter andere instellingen beschikbaar die regelen hoe en wanneer clients de compatibiliteit voor de software-updates evalueren en bepalen hoe de software-updates worden geïnstalleerd.  

 Zie voor meer informatie de volgende onderwerpen:  

-   [Clientinstellingen voor software-updates](../get-started/manage-settings-for-software-updates.md#BKMK_ClientSettings).   

-   [Clientinstellingen voor software-updates](../../core/clients/deploy/about-client-settings.md#software-updates) artikel.  

### <a name="reporting-services-point"></a>Reporting Services-punt  
 De sitesysteemrol Reporting Services kan rapporten voor software-updates weergeven. Deze rol is optioneel, maar wordt aanbevolen. Voor meer informatie over het maken van een reporting services-punt, Zie [configureren rapportage.  

##  <a name="BKMK_RecoverUpgrades"></a> Herstellen als u de categorie Upgrades hebt gesynchroniseerd voordat u KB 3095113 installeert  
 U moet [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS op uw software-updatepunten en siteservers installeren voordat u de classificatie **Upgrades** synchroniseert. Als de hotfix niet is geïnstalleerd toen de **Upgrades** classificatie is ingeschakeld, ziet WSUS het Windows 10-build 1511 functie-upgrade zelfs als deze niet correct downloaden en implementeren van de gekoppelde pakketten. Als u eventuele upgrades synchroniseert zonder dat eerst geïnstalleerd [hotfix 3095113](https://support.microsoft.com/kb/3095113), vullen van de WSUS-database (SUSDB) met onbruikbare gegevens. Deze gegevens moet worden gewist voordat upgrades correct kunnen worden geïmplementeerd. Gebruik de onderstaande procedure van dit probleem wilt herstellen.  

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

2.  Schakel de **Upgrades** classificatie in de eigenschappen van Software-updatepunt (Zie voor meer informatie [classificaties en producten configureren](../get-started/configure-classifications-and-products.md)) en start vervolgens de software-updates synchronisatie ( Zie voor meer informatie [software-updates synchroniseren](../get-started/synchronize-software-updates.md)).  

3.  Installeereer [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS installeert op uw software-updatepunten en siteservers.  

4.  Selecteer de **Upgrades** classificatie in de eigenschappen van Software-updatepunt (Zie voor meer informatie [classificaties en producten configureren](../get-started/configure-classifications-and-products.md)) en start vervolgens de software-updates synchronisatie ( Zie voor meer informatie [software-updates synchroniseren](../get-started/synchronize-software-updates.md)).  

## <a name="next-steps"></a>Volgende stappen
[Beheer van software-updates voorbereiden](../get-started/prepare-for-software-updates-management.md)
