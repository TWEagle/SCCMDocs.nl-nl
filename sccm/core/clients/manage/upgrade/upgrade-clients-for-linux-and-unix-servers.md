---
title: Linux- en UNIX-clients bijwerken
titleSuffix: Configuration Manager
description: Upgrade van een client op een Linux- of UNIX-server in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d2bb377-1005-4a55-bd1f-b80a6d0b22e1
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 14934ceedaee3982703c1d5f637fb79edce5426b
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-upgrade-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Clients voor Linux- en UNIX-servers bijwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de versie van de client voor Linux en UNIX op een computer bijwerken naar een nieuwere clientversie zonder dat u de huidige client eerst hoeft te verwijderen. Om dit te doen, installeert u het nieuwe clientinstallatiepakket op de computer tijdens het gebruik van de **- keepdb** opdrachtregel-eigenschap. Wanneer de client voor Linux en UNIX wordt geïnstalleerd, worden de bestaande clientgegevens overschreven met de nieuwe clientbestanden. Echter, de **- keepdb** opdrachtregeleigenschap instrueert het installatieproces voor de clients unique identifier (GUID), lokale database met gegevens behouden en het certificaatarchief. Deze informatie wordt vervolgens gebruikt door de nieuwe clientinstallatie.  

 Als u bijvoorbeeld een RHEL5 x64-computer hebt waarop de client uit de oorspronkelijke release van de Configuration Manager-client voor Linux en UNIX wordt uitgevoerd. Als u wilt upgraden deze client naar de clientversie uit cumulatieve update 1, die u handmatig uitvoert de **installeren** script voor het installeren van het desbetreffende clientpakket uit cumulatieve update 1, door het toevoegen van de **- keepdb**opdrachtregeloptie. Zie het volgende voorbeeld-opdrachtregel:  

`./install -mp <hostname\> -sitecode <code\> -keepdb ccm-Universal-x64.<build\>.tar`  



## <a name="how-to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Een software-implementatie gebruiken om de client op Linux- en UNIX-servers bij te werken  
 Een software-implementatie gebruiken om de client op Linux- en UNIX-servers bij te werken Configuration Manager-client kan geen echter rechtstreeks uitvoeren voor het installatiescript voor de installatie van de nieuwe client omdat de installatie van een nieuwe client moet de huidige client eerst verwijderen. Hierdoor zou de Configuration Manager-clientproces dat het script voor installatie wordt uitgevoerd voordat de installatie van de nieuwe client begint eindigen. Om te kunnen een software-implementatie gebruiken om de nieuwe client te installeren, moet u de installatie te starten op een later tijdstip en wordt uitgevoerd door het besturingssysteem ingebouwde mogelijkheden voor planning plannen.  

 Een software-implementatie gebruiken voor het eerst de bestanden voor het nieuwe clientinstallatiepakket naar de clientcomputer kopiëren. Vervolgens implementeren en uitvoeren van een script voor het plannen van het installatieproces van de client. Het script maakt gebruik van het besturingssysteem ingebouwd **op** opdracht later wilt starten. Wanneer het script wordt uitgevoerd, wordt de werking ervan wordt beheerd door het besturingssysteem van de client en niet de Configuration Manager-client op de computer. Dit gedrag kan de opdrachtregel die wordt aangeroepen door het script op voor de Configuration Manager-client eerst verwijderen en vervolgens de nieuwe client te installeren. Deze acties Voltooi de upgrade van de client op de Linux- of UNIX-computer. Nadat de upgrade is voltooid, blijft de bijgewerkte client beheerd door Configuration Manager.  

 Gebruik de volgende procedure om een software-implementatie te configureren waarmee de client voor Linux en UNIX kan worden bijgewerkt. Met de volgende stappen en voorbeelden wordt een RHEL5 x64-computer waarop de initiële release van de client wordt uitgevoerd, bijgewerkt naar de clientversie van de cumulatieve update 1.  

#### <a name="to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Een software-implementatie gebruiken om de client op Linux- en UNIX-servers bij te werken  

1.  Kopieer het nieuwe clientinstallatiepakket naar de computer waarop de Configuration Manager-client bijwerken.  

     Bijvoorbeeld, plaatst u het clientinstallatiepakket en installatiescript voor cumulatieve update 1 in de volgende locatie op de clientcomputer:   **/tmp/PATCH**  

2.  Een script voor het beheren van de upgrade van de Configuration Manager-client maken. Plaats een kopie van het script vervolgens in dezelfde map als de clientinstallatiebestanden uit stap 1 op de clientcomputer.  

     Het script nodig niet een specifieke naam. Deze moet voldoende gebruiken de clientinstallatiebestanden vanuit een lokale map op de clientcomputer en het installatiepakket voor de client installeren met behulp van opdrachtregels bevatten de **- keepdb** opdrachtregel-eigenschap. Gebruik de **- keepdb** opdrachtregel-eigenschap voor het onderhouden van de unieke id van de huidige client voor gebruik door de nieuwe client die u installeert.  

     Maak bijvoorbeeld een script met de naam **upgrade.sh** die de volgende regels bevat:  

    ```  
    #!/bin/sh  
    #  
    /tmp/PATCH/install -sitecode <code> -mp <hostname> -keepdb /tmp/PATCH/ccm-Universal-x64.<build>.tar  

    ```  

     Vervolgens kopiëren naar de **/tmp/PATCH** map op de clientcomputer.

3.  Gebruik software-implementatie om ervoor te zorgen dat elke client de ingebouwde **at** -opdracht van de computer gebruikt om het script **upgrade.sh** met een korte vertraging uit te voeren voordat het script wordt uitgevoerd.  

     Bijvoorbeeld de volgende opdrachtregel gebruiken het script uitvoeren: **op -f /tmp/upgrade.sh -m nu + 5 minuten**  

 Nadat de client de uitvoering van het script **upgrade.sh** heeft gepland, wordt er een statusbericht door de client verzonden dat de software-implementatie is voltooid. De werkelijke clientinstallatie wordt na de vertraging vervolgens beheerd door de computer. Nadat de clientupgrade is voltooid, valideert u de installatie door het bestand **/var/opt/microsoft/scxcm.log** op clientcomputer te controleren. Bevestig de client is geïnstalleerd en communicatie met de site door details weergeven voor de client in de **apparaten** knooppunt van de **activa en naleving** werkruimte in de Configuration Manager-console.  
