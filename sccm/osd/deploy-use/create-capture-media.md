---
title: Maken van vastlegmedia - Configuration Manager | Microsoft-documenten
description: Gebruik de Wizard Takenreeks maken Media te maken van vastleggende media in Configuration Manager voor het vastleggen van een installatiekopie van een besturingssysteem vanaf een referentiecomputer.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10eb8958-3848-49d7-95c0-16119b624580
caps.latest.revision: 11
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 5acf800ff5aebd849e294393337755145a60cca5
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-capture-media-with-system-center-configuration-manager"></a>Maken van vastlegmedia met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Registrerende media in Configuration Manager kunt u de installatiekopie van een besturingssysteem vanaf een referentiecomputer. Gebruik vastlegmedia voor het volgende scenario:  

-   [Maak een takenreeks voor het vastleggen van een besturingssysteem](create-a-task-sequence-to-capture-an-operating-system.md)  

##  <a name="BKMK_CreateCaptureMedia"></a> Het maken van vastleggende media  
 Gebruik vastleggende media om een installatiekopie van een besturingssysteem van een referentiecomputer vast te leggen. Vastlegmedia bevatten de opstartinstallatiekopie waarmee de referentiecomputer wordt gestart en de takenreeks waarmee de installatiekopie van het besturingssysteem wordt vastgelegd.

U kunt vastleggende media maken door de wizard Takenreeks media maken te gebruiken. Zorg ervoor dat aan de volgende voorwaarden is voldaan voordat u deze wizard uitvoert:  

|Taak|Beschrijving|  
|----------|-----------------|  
|Opstartinstallatiekopie|Overweeg het volgende met betrekking tot de opstartinstallatiekopie die u in de takenreeks gebruikt om het besturingssysteem vast te leggen:<br /><br /> -De architectuur van de opstartinstallatiekopie moet toepasselijk zijn voor de architectuur van de doelcomputer. Op een x64-doelcomputer kan een x86- of x64-opstartinstallatiekopie worden opgestart en uitgevoerd. Op een x86-doelcomputer kan echter alleen een x86-opstartinstallatiekopie worden opgestart en uitgevoerd.<br />-Zorg ervoor dat de opstartinstallatiekopie het netwerk en bulkopslagstations opslag die nodig zijn bevat voor de doelcomputer in te richten.|  
|Alle aan de takenreeks gekoppeld inhoud distribueren|U moet alle inhoud die door de takenreeks is vereist naar ten minste één distributiepunt distribueren. Dit omvat de opstartinstallatiekopie, de installatiekopie van het besturingssysteem en andere gekoppelde bestanden. De wizard haalt de informatie op van het distributiepunt wanneer het de zelfstandige media creëert. U moet over het toegangsrecht **Lezen** beschikken voor de inhoudsbibliotheek op het distributiepunt.  Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).|  
|Het verwisselbare USB-station voorbereiden|Voor een verwisselbaar USB-station:<br /><br /> Wanneer u een verwisselbaar USB-station wilt gebruiken, moet het USB-station zijn aangesloten op de computer waarop de wizard wordt uitgevoerd. Daarnaast moet het USB-station door Windows gedetecteerd kunnen worden als een verwisselbaar apparaat. De wizard schrijft rechtstreeks naar het USB-station wanneer deze het medium maakt.|  
|Een uitvoermap maken|Voor een cd/dvd-set:<br /><br /> Voordat u de wizard Takenreeksmedia maken uitvoert voor het maken van media voor een cd- of dvd-set, moet u een map maken voor de uitvoerbestanden die door de wizard worden gemaakt. Media die worden gemaakt voor een cd- of dvdset worden als .iso-bestanden direct naar de map geschreven.|  

 De volgende procedure gebruiken om vastleggende media te maken.  

#### <a name="to-create-capture-media"></a>Maken van vastleggende media  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeksmedia maken** om de wizard Takenreeksmedia maken te starten.  

4.  Selecteer **Eén computer importeren** op de pagina **Bron selecteren**en klik dan op **Volgende**.  

5.  Geef op de pagina **Mediumtype** op of het medium een flashstation of een cd/dvd-set is en klik vervolgens om het volgende te configureren:  

    -   Als u **USB-flashstation**selecteert, moet u het station opgeven waarop u de inhoud wilt opslaan.  

    -   Indien u **cd-/dvdset selecteert**, geef dan de capaciteit van de media en de naam en het pad van de uitvoerbestanden op. De wizard schrijft de uitvoerbestanden naar deze locatie. Bijvoorbeeld:  **\\\servername\folder\outputfile.iso**  

         Als de capaciteit van de media te klein is om alle inhoud op te slaan, worden er meerdere bestanden gemaakt en moet u de inhoud op meerdere cd's of dvd's opslaan. Als meerdere media nodig zijn, voegt Configuration Manager een volgnummer toe aan de naam van ieder uitvoerbestand dat wordt gemaakt. Bovendien, als u een toepassing tezamen met het besturingssysteem implementeert en de toepassing is voor één media groot te, slaat Configuration Manager de toepassing over verschillende media. Als de zelfstandige media wordt uitgevoerd, wordt Configuration Manager de gebruiker voor de volgende media waar de toepassing wordt opgeslagen.  

        > [!IMPORTANT]  
        >  Als u een bestaande .iso-afbeelding selecteert, verwijdert de wizard voor het maken van takenreeksmedia die afbeelding uit het station of de share wanneer u doorgaat naar de volgende pagina van de wizard. De bestaande installatiekopie wordt gewist, zelfs als u de wizard annuleert.  

     Klik op **Volgende**.  

6.  Geef op de pagina **Opstartinstallatiekopie** de volgende informatie op en klik vervolgens op **Volgende**.  

    > [!IMPORTANT]  
    >  De architectuur van de opstartinstallatiekopie die u opgeeft, moet toepasselijk zijn voor de architectuur van de referentiecomputer. Op een x64-referentiecomputer kan een x86- of x64-opstartinstallatiekopie worden opgestart en uitgevoerd. Op een x86-referentiecomputer kan echter alleen een x86-opstartinstallatiekopie worden opgestart en uitgevoerd.  

    -   Geef in het vakje **Opstartinstallatiekopie** de opstartinstallatiekopie op om de referentiecomputer op te starten.  

    -   Geef in het vak **Distributiepunt** het distributiepunt op waar de installatiekopie is opgeslagen. De wizard haalt de opstartinstallatiekopie op van het distributiepunt en schrijft deze naar de media.  

        > [!NOTE]  
        >  U moet leesrechten hebben voor de inhoudsbibliotheek op het distributiepunt.  

7.  Voltooi de wizard.  

