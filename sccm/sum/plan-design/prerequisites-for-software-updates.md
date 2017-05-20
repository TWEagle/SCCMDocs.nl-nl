---
title: Vereisten voor software-updates | Microsoft-documenten
description: Meer informatie over vereisten voor software-updates in System Center Configuration Manager.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.translationtype: Machine Translation
ms.sourcegitcommit: 238ef5814c0c1b832c28d63c9f3879e21a6c439b
ms.openlocfilehash: 179f076f228daa5adf612275a822cd379b0ce1e3
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>Vereisten voor software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp worden de vereisten voor software-updates in System Center Configuration Manager. De externe en interne afhankelijkheden voor beide worden in afzonderlijke tabellen vermeld.  

## <a name="software-update-dependencies-external-to-configuration-manager"></a>Software-Update afhankelijkheden extern aan Configuration Manager  
 De volgende gedeelten worden de externe afhankelijkheden voor software-updates.  

### <a name="internet-information-services-iis"></a>Internet Information Services (IIS)  
 Internet Information Services (IIS) moeten op de sitesysteemservers om uit te voeren van de software-updatepunt, het beheerpunt en het distributiepunt. Zie voor meer informatie [vereisten voor sitesysteemrollen](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS)  
 WSUS wordt vereist voor synchronisatie van software-updates en voor de compatibiliteitbeoordelingsscan van de software-updates op clients. De WSUS-server moet worden geïnstalleerd voordat u de sitesysteemrol voor het software-updatepunt maakt. De volgende versies van WSUS worden ondersteund voor een software-updatepunt:  

-   WSUS 4 (rol in Windows Server 2012 en Windows Server 2012 R2)  

-   WSUS 3.2 (rol in Windows Server 2008 R2)  

 Wanneer u meerdere software-updatepunten op een site hebt, ervoor te zorgen dat ze worden uitgevoerd dezelfde versie van WSUS.  

> [!WARNING]  
>  De **Upgrades** software-updates classificatie alleen wordt ondersteund begin in WSUS 4.0. Voordat u deze nieuwe classificatie synchroniseert en daarmee Windows 10-computers in een Windows-10 onderhoudsschema kunt evalueren, is het essentieel dat u [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS installeert op uw software-updatepunten en siteservers. Deze hotfix schakelt WSUS in op een Windows Server 2012- of een Windows Server 2012 R2-server om te synchroniseren en functie-upgrades voor Windows 10 te distribueren. Zie voor meer informatie [beheren Windows als een service](../../osd/deploy-use/manage-windows-as-a-service.md).  
>   
>  Als u software-updates synchroniseert met de classificatie **Upgrades** voordat u [hotfix 3095113](https://support.microsoft.com/kb/3095113)installeert, zie [Herstellen als u de categorie Upgrades hebt gesynchroniseerd voordat u KB 3095113 installeert](#BKMK_RecoverUpgrades)beschreven.  

### <a name="wsus-administration-console"></a>WSUS-beheerconsole  
 De WSUS-beheerconsole is vereist op de siteserver van Configuration Manager wanneer het software-updatepunt op een externe sitesysteemserver bevindt en WSUS niet al is geïnstalleerd op de siteserver.  

> [!IMPORTANT]  
>  De WSUS-versie op de siteserver moet dezelfde zijn als de WSUS-versie die wordt uitgevoerd op de software-updatepunten.  

> [!IMPORTANT]  
>  Gebruik de WSUS-beheerconsole geen WSUS-instellingen configureren. Configuration Manager maakt verbinding met WSUS die op het software-updatepunt wordt uitgevoerd en configureert de toepasselijke instellingen.  

### <a name="windows-update-agent-wua"></a>Windows Update Agent (WUA)  
 De WUA-client is vereist op clients om verbinding te maken met de WSUS-server en om de lijst met software-updates op te halen die moet worden gescand voor compatibiliteit.  

 Wanneer u Configuration Manager installeert, wordt de meest recente versie van de WUA gedownload. Klik wanneer de Configuration Manager-client is geïnstalleerd, wordt de WUA indien nodig bijgewerkt. Als de installatie mislukt, moet u echter een andere methode gebruiken om de WUA bij te werken.  

## <a name="software-update-dependencies-internal-to-configuration-manager"></a>Software-Update afhankelijkheden intern aan Configuration Manager  
 De volgende gedeelten worden de interne afhankelijkheden voor software-updates in Configuration Manager.  

### <a name="management-points"></a>Beheerpunten  
 Via beheerpunten wordt informatie overgedragen tussen clientcomputers en de Configuration Manager-site. Beheerpunten zijn vereist voor software-updates.  

### <a name="software-update-point"></a>Software-updatepunt  
 U moet een software-updatepunt installeren op de WSUS-server te kunnen voor het implementeren van software-updates in Configuration Manager. Zie voor meer informatie [installeren en configureren van een software-updatepunt](../get-started/install-a-software-update-point.md).

### <a name="distribution-points"></a>Distributiepunten  
 Distributiepunten zijn vereist voor het opslaan van de inhoud voor software-updates. Zie voor meer informatie over het installeren van distributiepunten en beheerinhoud [inhoud en -infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="client-settings-for-software-updates"></a>Clientinstellingen voor software-updates  
 Software-updates zijn standaard ingeschakeld voor clients. Er zijn echter andere instellingen beschikbaar die bepalen hoe en wanneer clients de compatibiliteit voor de software evalueren-updates en bepalen hoe de software-updates worden geïnstalleerd.  

 Zie voor meer informatie de volgende onderwerpen:  

-   [Clientinstellingen voor software-updates](../get-started/manage-settings-for-software-updates.md#a-namebkmkclientsettingsa-client-settings-for-software-updates).  

-   [Clientinstellingen voor software-updates](../../core/clients/deploy/about-client-settings.md#software-updates) onderwerp.  

### <a name="reporting-services-point"></a>Reporting Services-punt  
 De sitesysteemrol Reporting Services kan rapporten voor software-updates weergeven. Deze rol is optioneel, maar wordt aanbevolen. Zie voor meer informatie over het maken van een reporting services-punt [Configuring reporting](../../core/servers/manage/configuring-reporting.md) .  

##  <a name="BKMK_RecoverUpgrades"></a> Herstellen als u de categorie Upgrades hebt gesynchroniseerd voordat u KB 3095113 installeert  
 U moet [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS op uw software-updatepunten en siteservers installeren voordat u de classificatie **Upgrades** synchroniseert. Als de hotfix niet was geïnstalleerd toen de classificatie **Upgrades** werd ingeschakeld, ziet WSUS de functie-upgrade voor Windows-10-build 1511, zelfs als het de gekoppelde pakketten niet juist kan downloaden en implementeren. Als u eventuele upgrades synchroniseert zonder dat u eerst [hotfix 3095113](https://support.microsoft.com/kb/3095113)hebt geïnstalleerd, wordt de WSUS-database (SUSDB) gevuld met onbruikbare gegevens die moeten worden gewist voordat upgrades op de juiste manier kunnen worden geïmplementeerd.  Gebruik de volgende procedure van dit probleem te herstellen.  

#### <a name="to-recover-from-synchronizing-the-upgrades-classification-before-you-install-kb-3095113"></a>Herstellen van de classificatie Upgrades synchroniseren voordat u KB 3095113 installeert  

1.  Verwijder de software-updates met de classificatie Upgrades. U kunt een PowerShell-script vergelijkbaar met het script in het volgende voorbeeld:  

    ```  
    $Server = Get-WSUSServer  
    $Config = $Server.GetConfiguration()  
    $Update10563 = “df4e45a3-946d-4467-b3fd-8621174bb666”  
    $UpdateGUID = New-Object Guid($Update10563)  
    $Server.DeleteUpdate($UpdateGUID)  
    ```  

    > [!IMPORTANT]  
    >  U moet het script uitvoeren op alle software-updatepunten in uw hiërarchie Configuration Manager voordat u met de volgende stap verdergaat.  

     Als u software-updates met de classificatie Upgrades bulksgewijs wilt verwijderen, kunt u het PowerShell-script aanpassen zodat het meerdere GUID's leest uit een TXT-bestand.  

2.  Schakel de **Upgrades** classificatie in de eigenschappen van Software-updatepunt (voor meer informatie, Zie [Configureer classificaties en producten](../get-started/configure-classifications-and-products.md)) en start vervolgens de synchronisatie van software-updates (Zie voor meer informatie, [software-updates synchroniseren](../get-started/synchronize-software-updates.md).  

3.  Installeereer [hotfix 3095113](https://support.microsoft.com/kb/3095113) voor WSUS installeert op uw software-updatepunten en siteservers.  

4.  Selecteer de **Upgrades** classificatie in de eigenschappen van Software-updatepunt (voor meer informatie, Zie [Configureer classificaties en producten](../get-started/configure-classifications-and-products.md)) en start vervolgens de synchronisatie van software-updates (Zie voor meer informatie, [software-updates synchroniseren](../get-started/synchronize-software-updates.md).  

## <a name="next-steps"></a>Volgende stappen
[Voorbereiden voor beheer van software-updates](../get-started/prepare-for-software-updates-management.md)

