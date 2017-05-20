---
title: Mogelijkheden in Technical Preview 1603 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1603.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f861b72-9f14-4d17-a512-4a79b660abe6
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: dee2b4ce042bb4a434bb019e17a6b16e2807945c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1603-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1603 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1603 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. U kunt ook wanneer u System Center Technical Preview-versie 5 gebruikt, deze versie wordt geïnstalleerd als een basislijn-versie van de System Center Configuration Manager Technical Preview. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.  

 **Bekende problemen voor deze Technical Preview:**  

-   Deze release bevat updates voor eerder uitgebrachte functies, maar wordt geen nieuwe functies. De pagina functies van de Wizard updates worden daarom leeg als u eerder hebt bijgewerkt naar 1602 en alle 1602-functies ingeschakeld.  

-   Nadat uw siteserver-updates aan de technische Preview 1603, kunnen clients geen functies van beheer op afstand gebruiken totdat ze ook naar versie 1603 bijwerken.  

 **De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="BKMK_SC1603"></a>Verbeteringen in Software Center  

### <a name="new-tiled-view-for-apps"></a>Nieuwe naast elkaar weergave voor apps  
 Eindgebruikers kunnen nu kiezen tussen een lijst met apps of naast elkaar weergave van apps in de **toepassingen** tabblad van het Software Center.  

### <a name="select-multiple-updates-in-software-center"></a>Meerdere updates selecteren die in Software Center  
 In de **Updates** tabblad van het Software Center, u kunt nu meerdere updates selecteren of de optie **Alles bijwerken** om te beginnen met het installeren van meerdere updates tegelijkertijd.  

##  <a name="BKMK_RC1603"></a>Verbeteringen in beheer op afstand  

### <a name="limit-shared-clipboard-access-in-a-remote-control-session"></a>Gedeelde Klembord toegang beperken in een sessie voor beheer op afstand  
 U kunt nu de nieuwe instelling externe hulpprogramma's voor client inschakelen **gebruiker vragen naar machtiging voor het gedeelde Klembord overdracht** om te beperken van toegang tot het gedeelde Klembord in een sessie voor beheer op afstand.  

 Wanneer dit is ingeschakeld, moet de gebruiker die een externe sessie deelt machtigingen op de viewer van die sessie voordat de viewer van bestanden van de sessie naar hun lokale computer via het gedeelde Klembord overzetten kunt verlenen.  

 Een laag van beveiliging voor de eindgebruiker wordt toegevoegd zoals eerder, als de viewer is volledig beheer van de computer van de eindgebruiker verleend, kunt het gedeelde Klembord gebruiken voor het overzetten van bestanden van de sessie naar hun lokale computer op een manier die volledig transparant voor de eindgebruiker is.  

##  <a name="BKMK_RamDiskTFTP"></a> De RamDisk TFTP-blokgrootte en de -venstergrootte aanpassen op het distributiepunt met PXE-functionaliteit  
 U kunt in de Technical Preview 1603 RamDisk TFTP blokgrootte en venstergrootte voor PXE-ingeschakelde distributiepunten aanpassen. Als u uw netwerk hebt aangepast, kan dit ertoe leiden dat het downloaden van de opstartinstallatiekopie mislukt met een time-outfout omdat het blok of het venster te groot is. Met RamDisk TFTP-blok- en venstergrootteaanpassing kunt u het TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten.   
U moet de aangepaste instellingen in uw omgeving testen om te bepalen het meest efficiënt is.  

-   **TFTP-blokgrootte**: Grootte van het blok is de grootte van de gegevenspakketten die die door de server worden verzonden naar de client die het bestand wordt gedownload (zoals beschreven in de RFC 2347). Met een groter blok kan de server minder pakketten verzenden, waardoor er minder trajectvertraging optreedt tussen de server en de client. Met grotere blokken kan er echter sprake zijn van gefragmenteerde pakketten, waar de meeste PXE-clientimplementaties geen ondersteuning voor bieden.  

-   **TFTP-venstergrootte**: TFTP vereist een pakket bevestigingen (ACK) voor elk blok gegevens die worden verzonden. De server verzendt het volgende blok in de reeks pas wanneer het ACK-pakket van het vorige blok is ontvangen. TFTP-vensterbewerking is een functie in Windows Deployment Services waarmee u kunt instellen hoeveel gegevensblokken er in een venster passen. De server verzendt de gegevensblokken achter elkaar door tot het venster is gevuld. Daarna verzendt de client een ACK-pakket. Als u het venster vergroot, treedt er minder trajectvertraging op tussen de client en de server en is er minder tijd nodig om een opstartinstallatiekopie te downloaden.  

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de volgende taken uitvoeren en vervolgens de feedbackgegevens boven in dit onderwerp gebruiken om te laat ons weten hoe het werkt:  

-   Ik kunt de venstergrootte RamDisk TFTP op het distributiepunt met PXE-functionaliteit aanpassen.  

-   Ik kunt de blokgrootte RamDisk TFTP op het distributiepunt met PXE-functionaliteit aanpassen.  

### <a name="to-modify-the-ramdisk-tftp-window-size"></a>De grootte van het RamDisk TFTP-venster wijzigen  

-   Voeg de volgende registersleutel toe aan de distributiepunten met PXE-functionaliteit om de RamDisk TFTP-venstergrootte aan te passen:  

     **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Naam: RamDiskTFTPWindowSize  

     **Type**: REG_DWORD  

     **Waarde**: &lt;aangepast venstergrootte\>  

 De standaardwaarde is 1 (het venster bestaat uit één gegevensblok)  

### <a name="to-modify-the-ramdisk-tftp-block-size"></a>De grootte van het RamDisk TFTP-blok wijzigen  

-   Voeg de volgende registersleutel toe aan de distributiepunten met PXE-functionaliteit om de RamDisk TFTP-venstergrootte aan te passen:  

     **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Naam: RamDiskTFTPBlockSize  

     **Type**: REG_DWORD  

     **Waarde**: &lt;aangepast blokgrootte\>  

 De standaardwaarde is 4096 (4k).  

