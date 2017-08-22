---
title: Voorbereiden van Windows PE-peer-cache om WAN-verkeer te beperken | Microsoft Docs
description: De Windows PE-Peer-Cache werkt in de Windows PE voor inhoud ophalen van een lokale peer en WAN-verkeer te beperken wanneer er geen lokaal distributiepunt.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 6c64f276-b88c-4b1e-8073-331876a03038
caps.latest.revision: "11"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 814c6133a30b1116d05aaeafddb0dfb7fe2a390e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="prepare-windows-pe-peer-cache-to-reduce-wan-traffic-in-system-center-configuration-manager"></a>Windows PE-Peer-Cache voorbereiden om WAN-verkeer te beperken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u een nieuw besturingssysteem in System Center Configuration Manager implementeert, kunnen computers waarop de takenreeks wordt uitgevoerd Windows PE-Peer-Cache gebruiken om inhoud te verkrijgen van een lokale peer (een peer-cachebron) in plaats van de inhoud van een distributiepunt wordt gedownload. Dit helpt het Wide Area Network-verkeer (WAN) te beperken indien er sprake is van meerdere filialen terwijl er geen lokaal distributiepunt bestaat.  

 Windows PE-Peer-Cache is vergelijkbaar met [Windows BranchCache](http://technet.microsoft.com/library/mt617255\(TechNet.10\).aspx#bkmk_branchcache), maar werkt in de Windows Preinstallation Environment (Windows PE). Als u de takenreeks start vanuit een besturingssysteemcontext, bijvoorbeeld via het Software Center op de client, wordt Windows PE-Peer-Cache niet gebruikt. De volgende termen worden gebruikt om de clients te beschrijven die Windows PE-Peer-Cache gebruiken:  

-   Een **peer-cacheclient** is een computer die is geconfigureerd voor het gebruik van Windows PE-Peer-Cache.  

-   Een **peer-cachebron** is een client die is geconfigureerd voor peer-cache en die inhoud beschikbaar stelt aan andere peer-cacheclients die deze inhoud opvragen.  

Gebruik de volgende secties om Peer-Cache te beheren.

##  <a name="BKMK_PeerCacheObjects"></a> Objecten die zijn opgeslagen in een Peer-Cache-bron  
 Een takenreeks die is geconfigureerd voor het gebruik van Windows PE-Peer-Cache kan de volgende inhoudobjecten ophalen tijdens het uitvoeren van Windows PE:  

-   Installatiekopie van besturingssysteem  

-   Stuurprogrammapakket  

-   Pakketten en programma's (als de client blijft de takenreeks uitvoert in het volledige besturingssysteem, haalt de client deze inhoud via een peer-cachebron als de takenreeks oorspronkelijk is geconfigureerd voor peer-cache bij het uitvoeren van Windows PE.)  

-   Aanvullende installatiekopieën  

 De volgende inhoudobjecten worden nooit overgedragen met behulp van Peer-Cache. Deze worden in plaats daarvan overgedragen via een distributiepunt of via Windows BranchCache als u Windows BranchCache hebt geconfigureerd in uw omgeving:  

-   Toepassingen  

-   Software-updates  

##  <a name="BKMK_PeerCacheWork"></a> Hoe werkt Windows PE-Peer-Cache?  
 Stelt u zich een scenario voor met een filiaal dat geen distributiepunt heeft, maar wel enkele clients heeft waarvoor gebruik van Windows PE-Peer-Cache is ingeschakeld. U implementeert de takenreeks die is geconfigureerd om Peer-Cache te gebruiken op verschillende clients die zijn geconfigureerd om onderdeel te vormen van de Peer-Cache-bron. De eerste client die de takenreeks uitvoert, zendt een verzoek uit voor een peer met de inhoud. Deze peer wordt niet gevonden en de inhoud wordt daarom opgehaald van een distributiepunt via het WAN. De client installeert de nieuwe installatiekopie en slaat vervolgens de inhoud in de Configuration Manager-clientcache zodat deze kan worden gebruikt als peer-cachebron voor andere clients. Wanneer de volgende client de takenreeks uitvoert, wordt er via het subnet een aanvraag verstuurd voor een peer-cachebron. De eerste client reageert dan en maakt de inhoud in de cache beschikbaar.  

##  <a name="BKMK_PeerCacheDetermine"></a> Bepalen welke clients deel uitmaken van de Windows PE-Peer-Cache-bron  
 Als u wilt bepalen welke computers u moet selecteren als Windows PE-Peer-Cache-bron, zijn er verschillende dingen die u moet overwegen:  

-   De Windows PE-Peer-Cache-bron moet een desktopcomputer zijn die altijd is ingeschakeld en beschikbaar is voor Peer-Cache-clients.  

-   De Windows PE-Peer-Cache moet een clientcache hebben die groot genoeg is om de installatiekopieën op te slaan.  

##  <a name="BKMK_PeerCacheRequirements"></a> Vereisten voor een client waarop een Windows PE-Peer-Cache-bron moet worden gebruikt  
 Clients waarop een Windows PE-Peer-Cache-bron moet worden gebruikt, moeten voldoen aan de volgende vereisten:  

-   Configuration Manager-client moet kunnen communiceren via de volgende poorten op uw netwerk:  

    -   Poort voor de eerste netwerkuitzending om een peer-cachebron te vinden. Dit is standaard poort 8004.  

    -   Poort voor downloaden van inhoud via een peer-cachebron (HTTP en HTTPS). Dit is standaard poort 8003.  

        > [!TIP]  
        >  Clients gebruiken HTTPS om inhoud te downloaden wanneer deze beschikbaar is. Hetzelfde poortnummer wordt echter voor HTTP of HTTPS gebruikt.  

-   [Configureer de Client Cache voor Configuration Manager-clients](../../core/clients/manage/manage-clients.md#BKMK_ClientCache) op clients om ervoor te zorgen dat er genoeg ruimte is voor het bewaren van de installatiekopieën die u implementeert. Windows PE-Peer-Cache heeft geen invloed op de configuratie of het gedrag van de clientcache.  

-   De implementatieopties voor de takenreeksimplementatie moeten worden geconfigureerd als Inhoud lokaal downloaden wanneer deze nodig is door de takenreeks.  

##  <a name="BKMK_PeerCacheConfigure"></a> Windows PE-Peer-Cache configureren  
 Met de volgende methoden kunt u een client inrichten met Peer-Cache-inhoud zodat deze kan dienen als Peer-Cache-bron:  

-   Een peer-cacheclient die geen peer-cachebron kan vinden met de gewenste inhoud, downloadt de inhoud van een distributiepunt.  Als de client clientinstellingen ontvangt waardoor peer-cache wordt ingeschakeld en de takenreeks zodanig wordt geconfigureerd dat de inhoud in de cache wordt bewaard, wordt de client een peer-cachebron.  

-   Een peer-cacheclient kan inhoud ophalen van een andere peer-cacheclient (een peer-cachebron).  Omdat de client is geconfigureerd voor peer-cache, wordt de client een peer-cachebron wanneer deze een takenreeks uitvoert op basis waarvan de inhoud in de cache moet worden bewaard.  

-   Een client voert een takenreeks uit die de optionele stap [Pakketinhoud downloaden](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) bevat. Deze wordt gebruikt om de relevante inhoud die is opgenomen in de Windows PE-Peer-Cache-takenreeks voor te bereiden. Wanneer u deze methode gebruikt:  

    -   De client hoeft de installatiekopie die wordt geïmplementeerd niet te installeren.  

    -   Naast de optie **Pakketinhoud downloaden** moet de takenreeks ook de optie **Configuration Manager-clientcache** gebruiken. U kunt deze optie gebruiken om de inhoud op te slaan in de cache van de client, zodat de client kan dienen als peer-cachebron voor andere peer-cacheclients.  

 Op basis van de volgende procedures kunt u Windows PE-Peer-Cache configureren op clients en takenreeksen configureren die ondersteuning bieden voor peer-cache.  

### <a name="to-configure-the-windows-pe-peer-cache-source-computers"></a>De Windows PE-Peer-Cache-broncomputers configureren  

1.  Navigeer in de Configuration Manager-console naar **beheer** > **clientinstellingen**, en maak vervolgens een nieuwe **aangepaste Clientapparaatinstellingen** of bewerk een bestaand instellingenobject. U kunt dit ook configureren voor het object **Standaardclientinstellingen** .  

    > [!TIP]  
    >  Gebruik een object met aangepaste instellingen om te beheren welke clients deze configuratie ontvangen. Het kan bijvoorbeeld zijn dat u wilt voorkomen dat dit wordt geconfigureerd op de laptops van gebruikers die vaak onderweg zijn. Een uiterst mobiel systeem kan een slechte bron zijn voor het leveren van inhoud aan andere peer-cacheclients.  
    >   
    >  Onthoud dat ook als u deze instelling als onderdeel configureert van de **Standaardclientinstellingen**, de configuratie van toepassing op is alle clients in uw omgeving.  

2.  Bij **Windows PE-Peer-Cache**stelt u **Configuration Manager-client in volledige OS in staat stellen om inhoud te delen** in op **Ja**.  

    -   Standaard is alleen HTTP ingeschakeld. Als u clients in staat wilt stellen om inhoud via HTTPS te downloaden, stelt u **HTTPS inschakelen voor clientpeercommunicatie** in op **Ja**.  

    -   De poort voor uitzendingen is standaard ingesteld op 8004 en de poort voor het downloaden van inhoud is ingesteld op 8003. U kunt beide wijzigen.  

3.  Sla de clientinstellingen op en implementeer deze voor de clients die u selecteert als Peer-Cache-bron.  

 Wanneer een apparaat is geconfigureerd met dit instellingenobject, wordt het apparaat geconfigureerd als peer-cachebron. Deze instellingen moeten worden geïmplementeerd op mogelijke peer-cacheclients om de vereiste poorten en protocollen te configureren.  

###  <a name="BKMK_PeerCacheConfigureTS"></a> Een takenreeks configureren voor Windows PE-Peer-Cache  
 Als u de takenreeks configureert, gebruikt u de volgende takenreeksvariabelen als Verzamelingsvariabelen voor de verzameling waarop de takenreeks wordt geïmplementeerd:  

-   **SMSTSPeerDownload**  

     Waarde:  DE WAARDE TRUE  

     Hiermee kan de client Windows PE-Peer-Cache gebruiken.  

-   **SMSTSPeerRequestPort**  

     Waarde: < poortnummer\>  

     Als u niet de standaardpoort die is geconfigureerd in de clientinstellingen (8004) gebruikt, moet u deze variabele configureren met een aangepaste waarde van de netwerkpoort om te gebruiken voor de eerste verzending.  

-   **SMSTSPreserveContent**  

     Waarde: DE WAARDE TRUE  

     Hiermee wordt de inhoud in de takenreeks moet worden bewaard in de Configuration Manager-clientcache na de implementatie. Dit is anders dan het gebruik van SMSTSPersisContent die alleen behouden blijft de inhoud voor de duur van de takenreeks wordt uitgevoerd en die gebruikmaakt van de takenreekscache niet de Configuration Manager-clientcache.  

 Zie voor meer informatie [Takenreeksvariabelen ingebouwde](../understand/task-sequence-built-in-variables.md).  

###  <a name="BKMK_PeerCacheValidate"></a> Het succes van het gebruik van Windows PE-Peer-Cache valideren  
 Nadat u met Windows PE-peer-cache een takenreeks voor opstartmedia hebt geïmplementeerd en geïnstalleerd, kunt u controleren of het proces peer-cache heeft gebruikt door de **smsts.log** te bekijken op de client die de takenreeks heeft uitgevoerd.  

 Zoek in het logboek een vermelding die lijkt op de volgende waarbij <*Bronservernaam*> naam van de computer van waaruit de client de inhoud heeft verkregen. Deze computer moet een peer-cachebron zijn, en geen distributiepuntserver. Andere details zijn afhankelijk van uw lokale omgeving en configuraties.  

-   *<! [Logboek [bestand gedownload van http:// < Bronservernaam\>: 8003/SCCM_BranchCache$/SS10000C/sccm?/install.wim naar C:\\_SMSTaskSequence\Packages\SS10000C\install.wim] logboek]! >< tijd = "14:24:33.329 + 420" datum = '26-06-2015' onderdeel = 'ApplyOperatingSystem' context = ' "type ="1"thread = '1256' file="downloadcontent.cpp:1626 ' >*  
