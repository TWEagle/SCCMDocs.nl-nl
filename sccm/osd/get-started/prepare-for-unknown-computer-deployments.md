---
title: Voorbereiden op onbekende computerimplementaties
titleSuffix: Configuration Manager
description: Informatie over het implementeren van besturingssystemen op computers die niet door Configuration Manager worden beheerd in uw omgeving voor System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e447e34-0943-49ed-b6ba-3efebf3566c1
caps.latest.revision: "10"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: e3196bede5f069ae5012624b3ecaaf68713d9fe0
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="prepare-for-unknown-computer-deployments-in-system-center-configuration-manager"></a>Voorbereiden voor onbekende computerimplementaties in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit onderwerp om besturingssystemen te implementeren op onbekende computers in uw omgeving voor System Center Configuration Manager. Een onbekende computer is een computer die niet wordt beheerd door Configuration Manager. Dit betekent dat er geen record van deze computers in de Configuration Manager-database is. Onbekende computers omvatten het volgende:  

-   Een computer waarop de Configuration Manager-client niet is geïnstalleerd  

-   Een computer die is niet geïmporteerd in Configuration Manager  

-   Een computer die niet is gedetecteerd door Configuration Manager  

 U kunt de volgende implementatiemethoden gebruiken om besturingssystemen op onbekende computers te implementeren:  

-   [PXE gebruiken om Windows via het netwerk te implementeren](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)  

-   [Opstartbare media gebruiken om een besturingssysteem te implementeren](../deploy-use/create-bootable-media.md)  

-   [Voorbereide media gebruiken om een besturingssysteem te implementeren](../deploy-use/create-prestaged-media.md)  

## <a name="unknown-computer-deployment-workflow"></a>Werkstroom voor de implementatie op een onbekende computer  
 De volgende werkstroom bevat de basisstappen om een besturingssysteem op een onbekende computer te implementeren:  

-   Selecteer een onbekend computerobject dat in de implementatie moet worden gebruikt. U kunt het besturingssysteem implementeren op een van de onbekende computerobjecten in de verzameling **Alle onbekende computers** of u kunt de objecten in de verzameling **Alle onbekende computers** toevoegen aan een andere verzameling. Configuration Manager biedt twee onbekende computerobjecten in de **alle onbekende Computers** verzameling. Het ene object is voor x86-computers en het andere object is voor x64-computers.  

    > [!NOTE]  
    >  Het object **Onbekende x86-compute** is bedoeld voor computers die alleen in x86-architectuur werken. Het object **Onbekende x64-computer** is bedoeld voor computers die x86- en x64-architectuur ondersteunen. Met andere woorden, deze objecten beschrijven de architectuur van de doelcomputer. Ze beschrijven niet het besturingssysteem dat u op de doelcomputer wilt implementeren.  

-   Configureer een distributiepunt met PXE-functionaliteit of maak media om implementaties op onbekende computers te ondersteunen.  

-   Implementeer de takenreeks om het besturingssysteem te installeren.  

## <a name="unknown-computer-installation-process"></a>Installatieproces van onbekende computer  
 Wanneer een computer eerst wordt gestart vanuit PXE of vanaf media, controleert Configuration Manager of er voor die computer een record in de Configuration Manager-database bestaat. Als er een record, controleert Configuration Manager of er takenreeksen voor de record zijn geïmplementeerd zijn. Als er geen record bestaat, wordt Configuration Manager controleert om te zien of er takenreeksen voor een onbekend computerobject zijn geïmplementeerd. In beide gevallen voert Configuration Manager vervolgens een van de volgende acties uit:  

-   Als er een beschikbare takenreeks is, wordt Configuration Manager de gebruiker de takenreeks uitvoert.  

-   Als er een vereiste takenreeks is, wordt de takenreeks automatisch door Configuration Manager uitgevoerd.  

-   Als u een takenreeks wordt niet geïmplementeerd voor de record, Configuration Manager een fout gegenereerd dat er geen geïmplementeerde takenreeks voor de doelcomputer.  

 Wanneer een onbekende computer wordt gestart, herkent Configuration Manager de computer als een niet-ingerichte computer in plaats van een onbekende computer. Dit betekent dat de computer nu de takenreeksen kan ontvangen die zijn geïmplementeerd voor het onbekende computerobject. De geïmplementeerde takenreeks installeert vervolgens de installatiekopie van een besturingssysteem dat de Configuration Manager-client moet bevatten.  

 Nadat de Configuration Manager-client is geïnstalleerd, wordt een record voor de computer wordt gemaakt en wordt de computer vermeld in de juiste Configuration Manager-verzameling. Als de computer, mislukt de installatiekopie van het besturingssysteem of de Configuration Manager-client te installeren, een record "Onbekend" voor de computer wordt gemaakt en verschijnt de computer in de **alle systemen** verzameling.  

> [!NOTE]  
>  Tijdens de installatie van de installatiekopie van het besturingssysteem kan de takenreeks verzamelingsvariabelen, maar geen computervariabelen van deze computer ophalen.  

##  <a name="BKMK_EnablingUnknown"></a> Ondersteuning van onbekende computers inschakelen  
 Gebruik de volgende informatie om ondersteuning van onbekende computers in te schakelen wanneer u een besturingssysteem implementeert met PXE, opstartbare media en voorbereide media.  

-   **PXE**  

     Schakel het selectievakje **Ondersteuning van onbekende computers inschakelen** in op het tabblad **PXE** voor een distributiepunt met PXE-functionaliteit. Zie [Distributiepunten configureren voor de acceptatie van PXE-aanvragen](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)voor meer informatie.  

-   **Opstartbare media**  

     Schakel het selectievakje **Ondersteuning van onbekende computers inschakelen** in op de pagina **Beveiliging** van de wizard Takenreeksmedia maken. Zie [Distributiepunten configureren voor de acceptatie van PXE-aanvragen](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint) en [PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md) voor meer informatie.  

-   **Voorbereide media**  

     Schakel het selectievakje **Ondersteuning van onbekende computers inschakelen** in op de pagina **Beveiliging** van de wizard Takenreeksmedia maken. Zie [Voorbereide media maken met System Center Configuration Manager](../deploy-use/create-prestaged-media.md) voor meer informatie.  
