---
title: Serviceverbindingspunt | Microsoft-documenten
description: Meer informatie over deze sitesysteemrol van de Configuration Manager en begrijpen en plannen voor de reeks wordt gebruikt.
ms.custom: na
ms.date: 3/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
caps.latest.revision: 18
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6accec2d356861b273b25ba2b6338d9684a46ff6
ms.openlocfilehash: ad6df047beff670411d203220576b87f7d56d50c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="about-the-service-connection-point-in-system-center-configuration-manager"></a>Informatie over het serviceaansluitpunt in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De System Center Configuration Manager service connection point is een sitesysteemrol die een aantal belangrijke functies voor de hiërarchie fungeert. Voordat u de service connection point instelt, te begrijpen en plannen voor de reeks wordt gebruikt, die mogelijk van invloed op hoe u deze sitesysteemrol instellen:  

-   **Mobiele apparaten beheren met Microsoft Intune** -deze rol wordt vervangen door de Windows Intune-connector met eerdere versies van Configuration Manager gebruikt en kunnen worden geconfigureerd met de details van uw Intune-abonnement. Zie [hybride mobiel Apparaatbeheer (MDM) met System Center Configuration Manager en Microsoft Intune](../../../../mdm/understand/hybrid-mobile-device-management.md).  

-   **Mobiele apparaten beheren met lokale MDM** -deze rol biedt ondersteuning voor lokale apparaten die u beheert en die geen verbinding maken met Internet. Zie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

-   **Gebruiksgegevens van Configuration Manager-infrastructuur uploaden** -u kunt bepalen het niveau of de hoeveelheid details die u uploadt. Geüploade gegevens helpen ons bij het volgende:  

    -   Proactief problemen vaststellen en deze oplossen  

    -   Onze producten en de service verbeteren  

    -   Identificeren van updates voor Configuratiebeheer die betrekking hebben op de versie van Configuration Manager die u gebruikt  

  Zie voor informatie over gegevens die elk niveau worden verzameld en hoe u het niveau verzameling wijzigen nadat de rol is geïnstalleerd, [diagnostische en gebruiksgegevens](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data), en volgt u de koppeling voor de versie van Configuration Manager die u gebruikt.  

  Zie voor meer informatie [gebruik hebben en instellingen](../../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

-   **Downloaden van updates voor uw Configuration Manager-infrastructuur** - alleen relevante updates voor uw infrastructuur beschikbaar worden gemaakt op basis van gebruiksgegevens die u uploadt.  

- **Elke hiërarchie ondersteunt slechts één exemplaar van deze rol:**  

 -   De sitesysteemrol kan alleen worden geïnstalleerd op de bovenste site van uw hiërarchie, dit een centrale beheersite of zelfstandige primaire site is.  

  -   Als u een zelfstandige primaire site naar een grotere hiërarchie uitbreiden, kunt u deze rol van de primaire site moet verwijderen en kan vervolgens installeren op de centrale beheersite.  


##  <a name="bkmk_modes"></a>Modi  
 Het serviceverbindingspunt ondersteunt twee bewerkingsmodi:  

-   In **onlinemodus**, de service connection point automatisch elke 24 uur op updates controleert en downloadt hij nieuwe updates die beschikbaar voor uw huidige infrastructuur en het product versie zijn zodat ze beschikbaar zijn in de Configuration Manager-console.  

-   In **offlinemodus**, de service connection point geen verbinding maken met de cloudservice van Microsoft en moet u [gebruik het hulpprogramma voor Service-verbinding voor System Center Configuration Manager](../../../../core/servers/manage/use-the-service-connection-tool.md) beschikbare updates importeren.  

Wanneer u tussen de online of offline modus nadat u de service connection point wijzigt, moet u de thread SMS_DMP_DOWNLOADER van de Configuration Manager SMS_Executive-service vervolgens opnieuw voordat deze wijziging wordt van kracht. Gebruik hiervoor de Service van Configuration Manager alleen de SMS_DMP_DOWNLOADER thread van de SMS Executive-service opnieuw starten. U kunt ook de SMS Executive-service voor Configuration Manager, die de meeste Siteonderdelen opnieuw is opgestart, opnieuw of u kunt wachten op een geplande taak als een site back-up wordt gestopt en start de SMS Executive-service voor u vervolgens later opnieuw.  

Voor het gebruik van de Configuration Manager-servicebeheer, in de console gaat u naar **bewaking** > **systeemstatus** > **Onderdeelstatus**, kies **Start**, en kies vervolgens **Configuration Manager-servicebeheer**. In de servicebeheerfunctie:  

-   Vouw de site in het navigatievenster uit, vouw **onderdelen**, en kies vervolgens het onderdeel dat u opnieuw wilt opstarten.  

-   In het detailvenster met de rechtermuisknop op het onderdeel en kies vervolgens **Query**.  

-   Nadat de status van het onderdeel is bevestigd, opnieuw met de rechtermuisknop op het onderdeel en kiest u **stoppen**.  

-   **Query** het onderdeel opnieuw om te bevestigen dat deze is gestopt, met de rechtermuisknop op het onderdeel nog een keer, en kies vervolgens **Start**.  

> [!IMPORTANT]  
>  Het proces dat Microsoft Intune-abonnement automatisch toegevoegd aan de service connection point Hiermee stelt u de sitesysteemrol online zijn. De service connection point biedt geen ondersteuning voor offline modus wanneer deze ingesteld met een Intune-abonnement.  

**Wanneer de rol wordt geïnstalleerd op een computer die extern is van de siteserver:**  

-   Het computeraccount van de siteserver moet een lokale beheerder op de computer die als host fungeert voor een externe verbinding.

-   U moet de systeemserver van de site die als host fungeert voor de rol met een Installatieaccount instellen.  

-   Het Distributiebeheer op de siteserver gebruikt de sitesysteem-Installatieaccount om over te dragen van updates van de service connection point.

##  <a name="bkmk_urls"></a>Vereisten voor internettoegang  
Schakel bewerking door de computer die als host fungeert voor de service connection point en eventuele firewalls tussen de computer en het Internet moet uitwisselt via **poort TCP 443** en **poort TCP 443** voor de volgende locaties met Internet. Het serviceverbindingspunt ook ondersteunt het gebruik van een webproxy (met of zonder verificatie) om deze locaties te gebruiken.  Als u moet een web proxy account Zie configureren: [Ondersteuning voor proxy-server in System Center Configuration Manager](/sccm/core/plan-design/network/proxy-server-support).

**Updates en onderhoud**  

-   *.akamaiedge.net  

-   *.manage.microsoft.com

-   go.microsoft.com

-   blob.core.windows.net  

-   download.microsoft.com  

-   Download.windowsupdate.com

-   sccmconnected-a01.cloudapp.net  

**Microsoft Intune**  

-   *manage.microsoft.com  
-   https://bspmts.MP.Microsoft.com/V
-   https://login.microsoftonline.com/{TenantID}


**Onderhoud van Windows 10**  

-   download.microsoft.com  

-   https://go.microsoft.com/fwlink/?LinkID=619849  

## <a name="install-the-service-connection-point"></a>De service connection point installeren
Bij het uitvoeren van **Setup** voor het installeren van de site op hoogste niveau van een hiërarchie, hebt u de optie voor het installeren van de service connection point.

Nadat setup is uitgevoerd of als u de sitesysteemrol opnieuw installeert, gebruikt u de **sitesysteemrollen toevoegen** wizard of het **Sitesysteemserver maken** wizard voor het installeren van het sitesysteem op een server op de bovenste site van uw hiërarchie, dat wil, de centrale beheersite of een zelfstandige primaire site. Beide wizards zijn op de **Start** tabblad in de console op **beheer** > **siteconfiguratie** > **Servers en sitesysteemrollen**.

## <a name="log-files-used-by-the-service-connection-point"></a>Logboekbestanden die worden gebruikt door de service connection point
Informatie over het uploaden naar Microsoft, vindt u de **Dmpuploader.log** op de computer met de service connection point.  Voor de Downloadvoortgang van updates, inclusief-downloads bekijken **Dmpdownloader.log**. Zie voor de volledige lijst met betrekking tot de service connection point logboeken [serviceverbindingspunt](/sccm/core/plan-design/hierarchy/log-files#BKMK_WITLog) in het onderwerp van Configuration Manager logboek bestanden.

U kunt ook de volgende stroomdiagrammen gebruiken om de processtroom en belangrijke logboekvermeldingen voor update downloaden en replicatie van updates op andere sites te begrijpen:
 - [Stroomdiagram - updates downloaden](/sccm/core/servers/manage/download-updates-flowchart)
 - [Stroomdiagram - Update-replicatie](/sccm/core/servers/manage/update-replication-flowchart)

