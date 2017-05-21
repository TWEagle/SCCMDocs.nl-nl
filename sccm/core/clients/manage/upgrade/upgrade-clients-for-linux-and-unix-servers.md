---
itle: 'Upgrade clients | Microsoft Docs | Linux UNIX '
description: Upgrade van een client op een Linux of UNIX-server in System Center Configuration Manager.
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
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 394ba7c236c05cc90a3d7f99eb6146b15d620f11
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-upgrade-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Clients voor Linux- en UNIX-servers bijwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de versie van de client voor Linux en UNIX op een computer bijwerken naar een nieuwere clientversie zonder dat u de huidige client eerst hoeft te verwijderen. Hiervoor installeert u het clientinstallatiepakket op de computer tijdens met gebruik van de opdrachtregeleigenschap **-keepdb** . Wanneer de client voor Linux en UNIX wordt geïnstalleerd, worden de bestaande clientgegevens overschreven met de nieuwe clientbestanden. Echter, de **- keepdb** opdrachtregel-eigenschap opgeeft, stuurt het installatieproces voor de clients unique identifier (GUID) van informatie, lokale-database behouden en het certificaatarchief. Deze informatie wordt vervolgens gebruikt door de nieuwe clientinstallatie.  

 Als u bijvoorbeeld een RHEL5 x64-computer hebt waarop de client uit de oorspronkelijke release van de Configuration Manager-client voor Linux en UNIX wordt uitgevoerd. Als u deze client bijwerken naar de clientversie cumulatieve update 1, die u handmatig uitvoert de **installeren** script voor het installeren van de toepasselijke clientpakket cumulatieve update 1, met de toevoeging van de **- keepdb** opdrachtregelparameter. De opdrachtregel u lijkt op het volgende: **. / -mp installeren < hostnaam\> - sitecode < code\> - keepdb ccm Universal x64. < bouwen\>.tar**  

## <a name="how-to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Een software-implementatie gebruiken om de client op Linux- en UNIX-servers bij te werken  
 Een software-implementatie gebruiken om de client op Linux- en UNIX-servers bij te werken De System Center Configuration Manager-client kan niet echter rechtstreeks uitvoeren voor het script voor installatie om de nieuwe client installeert, omdat de installatie van een nieuwe client moet de huidige client eerst verwijderen. Hierdoor zou het proces van de Configuration Manager-client waarop het script voor installatie wordt uitgevoerd voordat u begint de installatie van de nieuwe client beëindigd. Als u wilt gebruiken met succes een software-implementatie om de nieuwe client te installeren, moet u de installatie te starten op een later tijdstip en wordt uitgevoerd door het besturingssysteem ingebouwde mogelijkheden voor planning plannen.  

 Hiervoor gebruikt u een software-implementatie om eerst de bestanden voor het nieuwe clientinstallatiepakket naar de clientcomputer te kopiëren en vervolgens een script te implementeren en uit te voeren om het clientinstallatieproces te plannen. Het script maakt gebruik van het besturingssysteem ingebouwde **op** opdracht later wilt starten. Vervolgens, wanneer het script wordt uitgevoerd, wordt de werking ervan wordt beheerd door het besturingssysteem van de client en niet de Configuration Manager-client op de computer. Hiermee wordt de opdrachtregel aangeroepen door het script naar de Configuration Manager-client eerst verwijderen en installeer vervolgens de nieuwe client het voltooien van de upgrade van de client op Linux of UNIX-computer. Nadat de upgrade is voltooid, blijft de bijgewerkte client beheerd door Configuration Manager.  

 Gebruik de volgende procedure om een software-implementatie te configureren waarmee de client voor Linux en UNIX kan worden bijgewerkt. Met de volgende stappen en voorbeelden wordt een RHEL5 x64-computer waarop de initiële release van de client wordt uitgevoerd, bijgewerkt naar de clientversie van de cumulatieve update 1.  

#### <a name="to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>Een software-implementatie gebruiken om de client op Linux- en UNIX-servers bij te werken  

1.  Kopieer het nieuwe pakketbestand van de client-installatie naar de computer met de Configuration Manager-client die u wilt bijwerken.  

     U kunt het clientinstallatiepakket en het installatiescript voor cumulatieve update 1 bijvoorbeeld opslaan op de volgende locatie op de clientcomputer: **/tmp/PATCH**  

2.  Maken van een script voor het beheren van de upgrade van de Configuration Manager-client en plaatst u een kopie van het script in dezelfde map op de clientcomputer als de clientinstallatiebestanden bij stap 1.  

     Het script is niet vereist voor een specifieke naam, maar moet bevatten opdrachtregels voldoende de installatiebestanden van de client gebruik van een lokale map op de clientcomputer en het installatiepakket voor de client installeren via de **- keepdb** opdrachtregel-eigenschap opgeeft. U gebruikt de **- keepdb** opdrachtregel-eigenschap voor het onderhouden van de unieke id van de huidige client voor gebruik door de nieuwe client die u installeert.  

     U kunt bijvoorbeeld een script met de naam **upgrade.sh** maken die de volgende regels bevat en het script vervolgens kopiëren naar de map **/tmp/PATCH** op de clientcomputer:  

    ```  
    #!/bin/sh  
    #  
    /tmp/PATCH/install -sitecode <code> -mp <hostname> -keepdb /tmp/PATCH/ccm-Universal-x64.<build>.tar  

    ```  

3.  Gebruik software-implementatie om ervoor te zorgen dat elke client de ingebouwde **at** -opdracht van de computer gebruikt om het script **upgrade.sh** met een korte vertraging uit te voeren voordat het script wordt uitgevoerd.  

     Bijvoorbeeld, de volgende opdrachtregel gebruiken het script uit te voeren: **op -f /tmp/upgrade.sh -m nu + 5 minuten**  

 Nadat de client de uitvoering van het script **upgrade.sh** heeft gepland, wordt er een statusbericht door de client verzonden dat de software-implementatie is voltooid. De werkelijke clientinstallatie wordt na de vertraging vervolgens beheerd door de computer. Nadat de clientupgrade is voltooid, valideert u de installatie door het bestand **/var/opt/microsoft/scxcm.log** op clientcomputer te controleren. Daarnaast kunt u bevestigen dat de client geïnstalleerd is en communiceert met de site is door het bekijken van details voor de client in de **apparaten** knooppunt van de **activa en naleving** werkruimte in de Configuration Manager-console.  

