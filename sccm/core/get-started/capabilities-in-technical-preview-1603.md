---
title: Mogelijkheden van Technical Preview 1603
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1603.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f861b72-9f14-4d17-a512-4a79b660abe6
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 1dc2dc74a27806741af99a235222b8f088f371a5
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1603-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1603 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1603 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. U kunt ook wanneer u System Center Technical Preview 5 gebruikt, deze versie wordt geïnstalleerd als een basislijnversie van de System Center Configuration Manager Technical Preview. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.  

 **Bekende problemen voor deze Technical Preview:**  

-   Deze release bevat updates voor eerder uitgebrachte functies, maar wordt geen nieuwe functies. De pagina functies van de Wizard Update worden daarom leeg als u eerder hebt geüpgraded naar 1602 en alle van de functies van 1602 is ingeschakeld.  

-   Nadat uw siteserver is bijgewerkt naar Technical Preview 1603, kunnen clients geen functies van beheer op afstand gebruiken totdat ze ook naar versie 1603 bijwerken.  

 **Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="BKMK_SC1603"></a>Verbeteringen aan Software Center  

### <a name="new-tiled-view-for-apps"></a>Nieuwe tegelweergave voor apps  
 Eindgebruikers kunnen nu kiezen tussen een lijst met apps of een weergave met tegels van apps in de **toepassingen** tabblad van het Software Center.  

### <a name="select-multiple-updates-in-software-center"></a>Meerdere updates selecteren in Software Center  
 In de **Updates** tabblad van het Software Center, u kunt nu meerdere updates selecteren of selecteer **Alles bijwerken** om te beginnen met meerdere updates tegelijk installeren.  

##  <a name="BKMK_RC1603"></a>Verbeteringen aan beheer op afstand  

### <a name="limit-shared-clipboard-access-in-a-remote-control-session"></a>Toegang tot gedeeld Klembord beperken tijdens een sessie voor beheer op afstand  
 U kunt nu de nieuwe externe hulpprogramma's clientinstelling inschakelen **gebruiker vragen naar machtiging voor het gedeelde Klembord overdracht** om toegang te beperken tot het gedeelde Klembord in een sessie voor beheer op afstand.  

 Wanneer dit is ingeschakeld, moet de gebruiker die een externe sessie deelt machtigingen voor de viewer van die sessie voordat de viewer bestanden vanuit de sessie naar de lokale computer via het gedeelde Klembord overdragen kan verlenen.  

 Hiermee wordt een laag van beveiliging voor de eindgebruiker toegevoegd als voorheen als de viewer volledige controle van de eindgebruiker computer had gekregen, ze zou kunnen gebruiken het gedeelde Klembord bestanden van de sessie overbrengen naar de lokale computer op een manier die volledig transparant voor de eindgebruiker was.  

##  <a name="BKMK_RamDiskTFTP"></a> De RamDisk TFTP-blokgrootte en de -venstergrootte aanpassen op het distributiepunt met PXE-functionaliteit  
 U kunt in de Technical Preview 1603 de RamDisk TFTP-blokgrootte en venstergrootte voor distributiepunten met PXE-functionaliteit aanpassen. Als u uw netwerk hebt aangepast, kan dit ertoe leiden dat het downloaden van de opstartinstallatiekopie mislukt met een time-outfout omdat het blok of het venster te groot is. Met RamDisk TFTP-blok- en venstergrootteaanpassing kunt u het TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten.   
U moet de aangepaste instellingen in uw omgeving testen om te bepalen het meest efficiënt is.  

-   **TFTP-blokgrootte**: De blokgrootte is de grootte van de gegevenspakketten die door de server worden verzonden naar de client die het bestand downloadt (zoals beschreven in RFC 2347). Met een groter blok kan de server minder pakketten verzenden, waardoor er minder trajectvertraging optreedt tussen de server en de client. Met grotere blokken kan er echter sprake zijn van gefragmenteerde pakketten, waar de meeste PXE-clientimplementaties geen ondersteuning voor bieden.  

-   **TFTP-venstergrootte**: TFTP vereist een pakket bevestigingen (ACK) voor elk gegevensblok dat wordt verzonden. De server verzendt het volgende blok in de reeks pas wanneer het ACK-pakket van het vorige blok is ontvangen. TFTP-vensterbewerking is een functie in Windows Deployment Services waarmee u kunt instellen hoeveel gegevensblokken er in een venster passen. De server verzendt de gegevensblokken achter elkaar door tot het venster is gevuld. Daarna verzendt de client een ACK-pakket. Als u het venster vergroot, treedt er minder trajectvertraging op tussen de client en de server en is er minder tijd nodig om een opstartinstallatiekopie te downloaden.  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taken uitvoeren en vervolgens met de feedbackinformatie boven aan dit onderwerp laat ons weten hoe het is gegaan:  

-   Ik kan de RamDisk TFTP-venstergrootte op het distributiepunt met PXE-functionaliteit aanpassen.  

-   Ik kan de RamDisk TFTP-blokgrootte op het distributiepunt met PXE-functionaliteit aanpassen.  

### <a name="to-modify-the-ramdisk-tftp-window-size"></a>De grootte van het RamDisk TFTP-venster wijzigen  

-   Voeg de volgende registersleutel toe aan de distributiepunten met PXE-functionaliteit om de RamDisk TFTP-venstergrootte aan te passen:  

     **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Naam: RamDiskTFTPWindowSize  

     **Type**: REG_DWORD  

     **Waarde**: &lt;aangepaste venstergrootte\>  

 De standaardwaarde is 1 (het venster bestaat uit één gegevensblok)  

### <a name="to-modify-the-ramdisk-tftp-block-size"></a>De grootte van het RamDisk TFTP-blok wijzigen  

-   Voeg de volgende registersleutel toe aan de distributiepunten met PXE-functionaliteit om de RamDisk TFTP-venstergrootte aan te passen:  

     **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Naam: RamDiskTFTPBlockSize  

     **Type**: REG_DWORD  

     **Waarde**: &lt;aangepaste blokgrootte\>  

 De standaardwaarde is 4096 (4k).  
