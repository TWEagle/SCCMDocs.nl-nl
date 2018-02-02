---
title: Serviceverbindingspunt
titleSuffix: Configuration Manager
description: Meer informatie over deze sitesysteemrol van de Configuration Manager en begrijpen en plannen voor de verschillende mogelijkheden.
ms.custom: na
ms.date: 1/29/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: a029d54000dee669ae437a460ebcb31f359bfd27
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="about-the-service-connection-point-in-system-center-configuration-manager"></a>Informatie over het serviceaansluitpunt in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Het serviceverbindingspunt van System Center Configuration Manager is een sitesysteemrol die enkele belangrijke functies voor de hiërarchie fungeert. Voordat u het service connection point instelt, begrijpt en plannen voor de verschillende mogelijkheden.  Planning voor informatie over het gebruik mogelijk van invloed zijn op hoe u deze sitesysteemrol instellen:  

-   **Mobiele apparaten beheren met Microsoft Intune** -deze functie vervangt de Windows Intune-connector met eerdere versies van Configuration Manager gebruikt en kunnen worden geconfigureerd met de details van uw Intune-abonnement. Zie [hybride mobile device management (MDM) met System Center Configuration Manager en Microsoft Intune](../../../../mdm/understand/hybrid-mobile-device-management.md).  

-   **Beheer van mobiele apparaten met on-premises MDM** -deze rol biedt ondersteuning voor on-premises apparaten die u beheert en die niet zijn verbonden met internet. Zie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

-   **Uploaden van gebruiksgegevens van uw Configuration Manager-infrastructuur** -u kunt bepalen het niveau of de hoeveelheid details die u uploadt. Geüploade gegevens kan:  

    -   Proactief problemen vaststellen en deze oplossen  

    -   Onze producten en de service verbeteren  

    -   Identificeren van updates voor Configuration Manager die van toepassing op de versie van Configuration Manager die u gebruikt  

  Zie voor informatie over gegevens die elk niveau worden verzameld en hoe u het niveau verzameling wijzigen nadat de rol is geïnstalleerd, [diagnostische gegevens en gebruiksgegevens](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). Volg de koppeling voor de versie van Configuration Manager die u gebruikt.  

  Zie voor meer informatie [gebruiksgegevensniveaus en instellingen](../../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

-   **Updates downloaden die van toepassing zijn op uw Configuration Manager-infrastructuur** : alleen relevante updates voor uw infrastructuur worden beschikbaar gesteld op basis van gebruiksgegevens die u uploadt.  

- **Elke hiërarchie ondersteunt slechts één exemplaar van deze rol:**  

 -   De sitesysteemrol kan alleen worden geïnstalleerd op de bovenste site van uw hiërarchie een centrale beheersite of zelfstandige primaire site.  

  -   Als u een zelfstandige primaire site naar een grotere hiërarchie uitbreiden, kunt u deze rol in de primaire site moet verwijderen en kunt u deze vervolgens installeren op de centrale beheersite.  


##  <a name="bkmk_modes"></a>Bewerkingsmodi  
 Het serviceverbindingspunt ondersteunt twee bewerkingsmodi:  

-   In **onlinemodus**, het serviceverbindingspunt automatisch elke 24 uur op updates controleert. Het downloadt nieuwe updates die beschikbaar voor uw huidige infrastructuur en productversie zijn zodat ze beschikbaar zijn in de Configuration Manager-console.  

-   In **offlinemodus**, het serviceverbindingspunt geen verbinding met de Microsoft-cloudservice. [Het hulpprogramma voor serviceverbindingen gebruiken voor System Center Configuration Manager](../../../../core/servers/manage/use-the-service-connection-tool.md) beschikbare updates handmatig te importeren.  

Als u tussen online of offline modi na de installatie van het service connection point wijzigt, moet u de thread SMS_DMP_DOWNLOADER van de Configuration Manager SMS_Executive-service opnieuw starten voordat de wijziging van kracht. De Configuration Manager Service Manager kunt u alleen de thread SMS_DMP_DOWNLOADER van de SMS_Executive-service opnieuw starten. U kunt ook de SMS_Executive-service voor Configuration Manager, waarmee de meeste Siteonderdelen opnieuw wordt opgestart opnieuw. U kunt ook wachten op een geplande taak, zoals een siteback-up, die stopt en start de SMS_Executive-service voor u vervolgens het later opnieuw.  

Voor het gebruik van de Configuration Manager-servicebeheer, in de console gaat u naar **bewaking** > **systeemstatus** > **Onderdeelstatus**, kies **Start**, en kies vervolgens **Configuration Manager-servicebeheer**. In de servicebeheerfunctie:  

-   Vouw in het navigatiedeelvenster de site **onderdelen**, en kies vervolgens het onderdeel dat u wilt starten.  

-   In het detailvenster met de rechtermuisknop op het onderdeel en kies vervolgens **Query**.  

-   Nadat de status van het onderdeel hebt bevestigd, opnieuw met de rechtermuisknop op het onderdeel en kies vervolgens **stoppen**.  

-   **Query** het onderdeel opnieuw om te bevestigen dat de service is gestopt. Met de rechtermuisknop op het onderdeel een keer in en kies vervolgens **Start**.  

> [!IMPORTANT]  
>  Het proces dat wordt Microsoft Intune-abonnement toegevoegd aan het service connection point Hiermee stelt u de sitesysteemrol online te zijn. Het serviceverbindingspunt biedt geen ondersteuning voor offlinemodus wanneer deze ingesteld met een Intune-abonnement.  

**Wanneer de functie wordt geïnstalleerd op een computer die extern zijn van de siteserver:**  

-   Het computeraccount van de siteserver moet een lokale beheerder op de computer die als host fungeert voor een externe service-verbinding.

-   U moet de sitesysteemserver die als host fungeert voor de rol met een Installatieaccount instellen.  

-   Het Distributiebeheer op de siteserver gebruikt de sitesysteem-Installatieaccount om over te dragen van updates van het service connection point.

##  <a name="bkmk_urls"></a>Vereisten voor internettoegang  
Schakel bewerking door de computer die als host fungeert voor het service connection point en eventuele firewalls tussen de computer en het internet moet doorgeven communicatie uitgaande poort **TCP 443** voor HTTPS en de uitgaande poort  **TCP 80** HTTP kan de onder de internet-locaties. Het serviceverbindingspunt ook ondersteunt het gebruik van een webproxy (met of zonder verificatie) om deze locaties te gebruiken.  Als u moet een proxyaccount web Zie configureren: [Ondersteuning voor proxyserver in System Center Configuration Manager](/sccm/core/plan-design/network/proxy-server-support).

**Updates en onderhoud**  

-   *.akamaiedge.net  

-   *.akamaitechnologies.com 

-   *.manage.microsoft.com

-   go.microsoft.com

-   blob.core.windows.net  

-   download.microsoft.com  

-   download.windowsupdate.com

-   sccmconnected-a01.cloudapp.net  

**Microsoft Intune**  

-   *manage.microsoft.com  
-   https://bspmts.mp.microsoft.com/V
-   https://login.microsoftonline.com/{TenantID}


**Windows 10 servicing**  

-   download.microsoft.com  

-   https://go.microsoft.com/fwlink/?LinkID=619849  

## <a name="install-the-service-connection-point"></a>Het serviceverbindingspunt installeren
Bij het uitvoeren van **Setup** voor de bovenste site van een hiërarchie installeert, hebt u de optie voor het installeren van het serviceverbindingspunt wordt gehost.

Nadat setup is uitgevoerd of als u de sitesysteemrol opnieuw installeert, gebruikt u de **sitesysteemrollen toevoegen** wizard of de **Sitesysteemserver maken** wizard voor het installeren van het sitesysteem dat op een server op de bovenste site van uw hiërarchie, de centrale beheersite of een zelfstandige primaire site. Beide wizards zijn op de **Start** tabblad in de console op **beheer** > **siteconfiguratie** > **Servers en sitesysteemrollen**.

## <a name="log-files-used-by-the-service-connection-point"></a>Gebruikt door het service connection point-logboekbestanden
Informatie over het uploaden naar Microsoft, vindt u de **Dmpuploader.log** op de computer waarop het serviceverbindingspunt wordt gehost.  Voor het downloaden van de Downloadvoortgang van de van updates, inclusief weergeven **Dmpdownloader.log**. Zie voor de volledige lijst van logboekbestanden gerelateerd aan het service connection point [Serviceaansluitpunt](/sccm/core/plan-design/hierarchy/log-files#BKMK_WITLog) in het artikel van Configuration Manager logboek bestanden.

U kunt ook de volgende stroomdiagrammen gebruiken om de processtroom en sleutel logboekvermeldingen voor update downloaden en de replicatie van updates voor andere sites te begrijpen:
 - [Stroomdiagram: updates downloaden](/sccm/core/servers/manage/download-updates-flowchart)
 - [Stroomdiagram: updatereplicatie](/sccm/core/servers/manage/update-replication-flowchart)
