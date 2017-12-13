---
title: Inleiding tot besturingssysteemimplementaties
titleSuffix: Configuration Manager
description: De basisbegrippen voordat u besturingssystemen in uw Configuration Manager-omgeving implementeren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9a1c545-8301-492c-832f-2c108ff93c77
caps.latest.revision: "12"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 31f18ce9df3fcdb133589ce5214cef96372ee1b0
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="introduction-to-operating-system-deployment-in-system-center-configuration-manager"></a>Inleiding tot besturingssysteemimplementaties in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de Configuration Manager gebruiken om besturingssystemen te implementeren in een aantal verschillende manieren. Gebruik de informatie in deze sectie om te begrijpen hoe het implementeren van besturingssystemen en het automatiseren van taken. 

##  <a name="BKMK_OSDeploymentProcess"></a> Het proces van de besturingssysteemimplementatie  
 Configuration Manager biedt verschillende methoden die u gebruiken kunt om een besturingssysteem te implementeren. Ongeacht de implementatiemethode die u gebruikt, zijn er verschillende acties die u moet uitvoeren.  

-   Stel vast welke Windows-apparaatstuurprogramma's vereist zijn om de opstartinstallatiekopie op te starten en de installatiekopie van het besturingssysteem te installeren die u moet implementeren.  

-   Kies de opstartinstallatiekopie die u wilt gebruiken om de doelcomputer te starten.  

-   Gebruik een takenreeks om een installatiekopie van het besturingssysteem vast te leggen dat u wilt implementeren. U kunt ook een standaardinstallatiekopie van het besturingssysteem gebruiken.  

-   Distribueer de opstartinstallatiekopie, de installatiekopie van het besturingssysteem en eventueel gerelateerde inhoud naar een distributiepunt.  

-   Maak een takenreeks met de stappen voor het implementeren van de opstartinstallatiekopie en de installatiekopie van het besturingssysteem.  

-   Implementeer de takenreeks voor een verzameling computers  

-   Controleer de implementatie.  

##  <a name="BKMK_OSDScenarios"></a> Implementatiescenario's voor het besturingssysteem  
 Er zijn veel scenario's voor besturingssysteemimplementaties in Configuration Manager waarmee u uit, afhankelijk van uw omgeving en het doel van de installatie van het besturingssysteem kiezen kunt.  U kunt bijvoorbeeld de harde schijf van een bestaande computer in partities indelen en formatteren met een nieuwe versie van Windows of voor Windows een upgrade uitvoeren naar de nieuwste versie. Om te bepalen welke implementatiemethode voldoet aan uw behoeften, Bekijk [scenario's voor het implementeren van enterprise-besturingssystemen](../deploy-use/scenarios-to-deploy-enterprise-operating-systems.md).  U kunt kiezen uit de volgende implementatiescenario's voor besturingssystemen:  

-   [Windows bijwerken naar de laatste versie](../deploy-use/upgrade-windows-to-the-latest-version.md)  

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](../deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](../deploy-use/install-new-windows-version-new-computer-bare-metal.md)  

-   [Een bestaande computer vervangen en de instellingen overzetten](../deploy-use/replace-an-existing-computer-and-transfer-settings.md)  

##  <a name="BKMK_OSDMethods"></a> Methoden voor het implementeren van besturingssystemen  
 Er zijn verschillende methoden die u gebruiken kunt om besturingssystemen te implementeren naar Configuration Manager-clientcomputers.  

-   **PXE geïnitieerde implementaties**: PXE-geïnitieerde implementaties kunnen door clientcomputers een implementatie via het netwerk aanvragen. In deze implementatiemethode worden de installatiekopie van het besturingssysteem en een opstartinstallatiekopie van Windows PE verzonden naar een distributiepunt dat is geconfigureerd om PXE-opstartaanvragen te accepteren. Zie [PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md) voor meer informatie.  

-   **Besturingssystemen beschikbaar maken in Software Center**: U kunt een besturingssysteem implementeren en beschikbaar maken in Software Center. Configuration Manager-clients kunnen de installatie van het besturingssysteem vanuit Software Center initiëren. Zie voor meer informatie [een bestaande computer vervangen en de instellingen overzetten](../deploy-use/replace-an-existing-computer-and-transfer-settings.md).  

-   **Multicast-implementaties**: Multicastimplementaties houden netwerkbandbreedte vrij door gegevens gelijktijdig te verzenden naar meerdere clients in plaats van een kopie van de gegevens verzenden naar elke client via een aparte verbinding. In deze implementatiemethode wordt de installatiekopie van het besturingssysteem verzonden naar een distributiepunt. Dit implementeert op zijn beurt de installatiekopie wanneer clientcomputers de implementatie aanvragen. Zie voor meer informatie [multicast gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

-   **Implementaties met opstartbare media**: Implementaties met opstartbare media kunnen u het besturingssysteem implementeren wanneer de doelcomputer wordt opgestart. De doelcomputer haalt de takenreeks, de installatiekopie van het besturingssysteem en alle andere vereiste inhoud van het netwerk op tijdens het opstarten. Omdat die inhoud zich niet op de media bevindt, kunt u de inhoud bijwerken zonder de media opnieuw te moeten maken. Zie voor meer informatie [opstartbare media maakt](../deploy-use/create-bootable-media.md).  

-   **Implementaties met zelfstandige media**: Met implementaties met zelfstandige media kunt u besturingssystemen implementeren in volgende situaties:  

    -   In omgevingen waar het niet praktisch is om een installatiekopie van een besturingssysteem of andere grote pakketten over het netwerk te kopiëren.  

    -   In omgevingen zonder netwerkverbinding of de met lage netwerkbandbreedte.  

     Zie voor meer informatie [zelfstandige media maken](../deploy-use/create-stand-alone-media.md).  

-   **Media-implementaties met vooraf geplaatste**: Implementaties met voorbereide media kunt u een besturingssysteem implementeren op een computer die niet volledig is ingericht. De voorbereide media is een Windows Imaging Format (WIM)-bestand dat kan worden geïnstalleerd op een bare-metal computer door de fabrikant of in een zakelijk voorbereidingscentrum dat niet is verbonden met de Configuration Manager-omgeving.  

     Later in de Configuration Manager-omgeving, de computer wordt gestart met behulp van de door de media verstrekte opstartinstallatiekopie en maakt vervolgens verbinding met het sitebeheerpunt voor beschikbare takenreeksen waarmee het downloadproces voltooien. Deze implementatiemethode kan het netwerkverkeer verminderen omdat de opstartinstallatiekopie en de installatiekopie van het besturingssysteem zich al op de doelcomputer bevinden. U kunt toepassingen, pakketten en stuurprogrammapakketten opgeven die in de voorbereide media moeten worden opgenomen. Zie voor meer informatie [voorbereide media maken](../deploy-use/create-prestaged-media.md).  

##  <a name="BKMK_BootImages"></a> Installatiekopieën  
 Een opstartinstallatiekopie in Configuration Manager is een Windows PE (WinPE) die wordt gebruikt tijdens de implementatie van een besturingssysteem. Opstartinstallatiekopieën worden gebruikt om een computer op te starten in WinPE. Dit is een minimaal besturingssysteem met beperkte onderdelen en services dat de doelcomputer voorbereidt voor een Windows-installatie. Configuration Manager biedt twee opstartinstallatiekopieën: Één ter ondersteuning van x86-platformen en één ter ondersteuning van x64 platforms. Deze worden beschouwd als de standaardopstartinstallatiekopieën. Opstartinstallatiekopieën die u maakt en toevoegen aan Configuration Manager worden beschouwd als aangepaste installatiekopieën. Standaardopstartinstallatiekopieën kunnen automatisch worden vervangen bij het bijwerken van Configuration Manager. Zie [Opstartinstallatiekopieën beheren met System Center Configuration Manager](../get-started/manage-boot-images.md) voor meer informatie over opstartinstallatiekopieën.  

##  <a name="BKMK_OSImages"></a> Installatiekopieën van besturingssystemen:  
 Installatiekopieën van besturingssystemen in Configuration Manager worden opgeslagen met de WIM-bestandsindeling (Windows Imaging). Ze omvatten een gecomprimeerde verzameling referentiebestanden en -mappen die zijn vereist om een besturingssysteem correct te installeren en te configureren op een computer. Alle implementatiescenario's voor besturingssystemen vereisen dat u een installatiekopie van een besturingssysteem selecteert. U kunt de standaardinstallatiekopie van een besturingssysteem gebruiken of een installatiekopie van het besturingssysteem maken van een referentiecomputer die u configureert. Zie voor meer informatie [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  

##  <a name="BKMK_OSUpgradePackages"></a> Upgradepakketten voor besturingssysteem  
 Upgradepakketten voor besturingssystemen worden gebruikt om een upgrade uit te voeren voor een besturingssysteem en zijn besturingssysteemimplementaties die met een installatieprogramma worden gestart. U importeert upgradepakketten voor besturingssysteem naar Configuration Manager uit een DVD of en gekoppeld ISO-bestand. Zie voor meer informatie [upgradepakketten voor besturingssysteem beheren](../get-started/manage-operating-system-upgrade-packages.md).  

##  <a name="BKMK_OSDMedia"></a> Media voor het implementeren van besturingssystemen  
 U kunt verschillende soorten media maken die kunnen worden gebruikt om besturingssystemen te implementeren. Dit omvat vastlegmedia die wordt gebruikt voor het vastleggen van installatiekopieën van een besturingssysteem en van zelfstandige, voorbereide en opstartbare media die wordt gebruikt om een besturingssysteem te implementeren. U kunt besturingssystemen op computers die geen netwerkverbinding of die een lage bandbreedteverbinding met uw Configuration Manager-site hebben implementeren met behulp van media. Zie voor meer informatie over het gebruik van media [takenreeksmedia maken](../deploy-use/create-task-sequence-media.md).  

##  <a name="BKMK_DeviceDrivers"></a> Apparaatstuurprogramma 's  
 U kunt apparaatstuurprogramma's installeren op doelcomputers zonder ze op te nemen in de installatiekopie van het besturingssysteem die wordt geïmplementeerd. Configuration Manager bevat een stuurprogrammacatalogus met verwijzingen naar alle apparaatstuurprogramma's die u in Configuration Manager importeert. De stuurprogrammacatalogus bevindt zich in de **softwarebibliotheek** werkruimte en bestaat uit twee knooppunten: **Stuurprogramma's** en **stuurprogrammapakketten**. Het knooppunt **Stuurprogramma's** geeft alle stuurprogramma's weer die u in de stuurprogrammacatalogus hebt geïmporteerd. U kunt dit knooppunt gebruiken om de details over elk geïmporteerd stuurprogramma te detecteren, om het stuurprogrammapakket of de opstartinstallatiekopie van een stuurprogramma te wijzigen, om een stuurprogramma in of uit te schakelen, en meer. Zie voor meer informatie [stuurprogramma's beheren](../get-started/manage-drivers.md).  

##  <a name="BKMK_OSDUserState"></a> De gebruikersstatus opslaan en terugzetten  
 Tijdens het implementeren van besturingssystemen kunt u de gebruikersstatus van de doelcomputer opslaan, het besturingssysteem implementeren en vervolgens de gebruikersstatus herstellen na de implementatie van de besturingssystemen. Dit proces wordt doorgaans gebruikt wanneer u het besturingssysteem op een Configuration Manager-clientcomputer installeert.  

 De gebruikersstatusinformatie wordt vastgelegd en hersteld met takenreeksen. Als de gebruikersstatusinformatie wordt vastgelegd, kan de informatie op een van de volgende manieren worden opgeslagen:  

-   U kunt de gebruikersstatusgegevens extern opslaan door een statusmigratiepunt te configureren. De takenreeks Vastleggen verzendt de gegevens naar het statusmigratiepunt. Nadat het besturingssysteem is geïmplementeerd, haalt de takenreeks Herstellen de gegevens op en wordt de gebruikersstatus op de doelcomputer hersteld.  

-   U kunt de gebruikersstatusgegevens lokaal opslaan op een specifieke locatie. In dit scenario kopieert de takenreeks Vastleggen de gebruikersgegevens naar een specifieke locatie op de doelcomputer. Na de implementatie van het besturingssysteem haalt de takenreeks Herstellen de gebruikersgegevens op van die locatie.  

-   U kunt vaste koppelingen opgeven die kunnen worden gebruikt om de gebruikersgegevens naar de oorspronkelijke locatie te herstellen. In dit scenario blijven de gebruikersstatusgegevens aanwezig op de schijf wanneer het oude besturingssysteem wordt verwijderd. Na de implementatie van het besturingssysteem gebruikt de takenreeks Herstellen de vaste koppelingen om de gebruikersstatusgegevens te herstellen naar hun oorspronkelijke locatie.  

 Voor meer informatie [Gebruikersstatus beheren](../get-started/manage-user-state.md).  

##  <a name="BKMK_UnknownComputer"></a> Naar onbekende computers implementeren  
 U kunt een besturingssysteem implementeren op computers die niet worden beheerd door Configuration Manager. Er is geen record van deze computers in de Configuration Manager-database. Deze computers worden onbekende computers genoemd. Onbekende computers omvatten het volgende:  

-   Een computer waarop de Configuration Manager-client niet is geïnstalleerd  

-   Een computer die is niet geïmporteerd in Configuration Manager  

-   Een computer die door Configuration Manager niet is gedetecteerd  

 Zie voor meer informatie [voorbereiden voor onbekende computerimplementaties](../get-started/prepare-for-unknown-computer-deployments.md).  

##  <a name="BKMK_UDA"></a> Gebruikers koppelen aan een computer  
 Als u een besturingssysteem implementeert, kunt u gebruikers koppelen met de doelcomputer om acties voor gebruikersaffiniteit apparaat te ondersteunen. Als u een gebruiker met de doelcomputer koppelt, kan de gebruiker met beheerdersrechten later acties uitvoeren op eender welke computer die met die gebruiker is gekoppeld, zoals het implementeren van een toepassing naar de computer van een specifieke gebruiker. Wanneer u echter een besturingssysteem implementeert, kunt u dit besturingssysteem niet implementeren op de computer van een specifieke gebruiker. Zie voor meer informatie [gebruikers koppelen aan een doelcomputer](../get-started/associate-users-with-a-destination-computer.md).  

##  <a name="BKMK_TaskSequences"></a> Stappen automatiseren met takenreeksen  
 U kunt takenreeksen maken voor een waaier aan taken in uw Configuration Manager-omgeving uitvoeren. De bewerkingen van de takenreeks worden gedefinieerd in de individuele stappen van de reeks. Als de takenreeks wordt uitgevoerd, worden de bewerkingen van elke stap uitgevoerd op het niveau van de opdrachtregel zonder dat er een interventie van de gebruiker is vereist. U kunt takenreeksen gebruiken voor het volgende:  

-   [Een takenreeks maken voor het installeren van een besturingssysteem](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md)  

-   [Een takenreeks maken voor niet-besturingssysteemimplementaties](../deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md)  

-   [Een takenreeks maken voor het vastleggen van een besturingssysteem](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md)  

-   [Een takenreeks maken voor het registreren en herstellen van de gebruikersstatus](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md)  

-   [Een aangepaste takenreeks maken](../deploy-use/create-a-custom-task-sequence.md)  
