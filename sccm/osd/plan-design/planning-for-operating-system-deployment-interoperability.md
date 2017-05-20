---
title: Planning voor interoperabiliteit bij de implementatie besturingssysteem | Microsoft-documenten
description: "Interoperabiliteitsproblemen kennen wanneer verschillende System Center Configuration Manager-sites in een enkele hiërarchie verschillende versies gebruiken."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e327ce38-6c07-4a27-b6eb-7e5bf74ed04b
caps.latest.revision: 10
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 50a4b75b8c8c1cb6f7a8e696abad285f99080fcd
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-operating-system-deployment-interoperability-in-system-center-configuration-manager"></a>De interoperabiliteit voor de besturingssysteemimplementatie plannen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer verschillende System Center Configuration Manager-sites in een enkele hiërarchie verschillende versies gebruiken, is sommige Configuration Manager-functionaliteit niet beschikbaar. Functionaliteit van de nieuwere versie van Configuration Manager is doorgaans niet toegankelijk op sites of bij klanten die een lagere versie uitvoeren. Zie [Interoperabiliteit tussen verschillende versies van System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md) voor meer informatie.  

 Overweeg het volgende wanneer u de site op het hoogste niveau in uw hiërarchie en andere sites in uw hiërarchie Configuration Manager uitvoeren met een lagere versie upgraden:  

-   Clientinstallatiepakket  

    -   De bron voor het standaard clientinstallatiepakket automatisch bijgewerkt en alle distributiepunten in de hiërarchie zijn bijgewerkt met de nieuwe clientinstallatiepakket, zelfs op distributiepunten op sites in de hiërarchie die zich op een lagere versie.  

    -   Clients met de nieuwe versie kunnen niet worden toegewezen aan sites die nog niet zijn bijgewerkt naar de nieuwe versie. Toewijzing wordt geblokkeerd op het beheerpunt.  

-   Installatiekopieën  

    -   Wanneer u een upgrade uitvoert van het hoogste niveau naar de nieuwste versie van Configuration Manager, worden de standaardinstallatiekopieën (x86 en x64) automatisch bijgewerkt naar Windows ADK voor Windows 10-gebaseerde opstartinstallatiekopieën, die Windows PE 10 gebruiken. De bestanden die gekoppeld aan de standaardopstartinstallatiekopieën zijn worden bijgewerkt met de meest recente versie van Configuration Manager van de bestanden. Aangepaste opstartinstallatiekopieën worden niet automatisch bijgewerkt. U moet aangepaste opstartinstallatiekopieën handmatig bijwerken waaronder oudere versies van Windows PE.  

    -   Vermijd het gebruik van dynamische media wanneer uw sitehiërarchie sites met verschillende versies van Configuration Manager bevat. Gebruik in plaats daarvan site gebaseerde media contact opnemen met een bepaald beheerpunt totdat alle sites zijn bijgewerkt naar dezelfde versie van Configuration Manager.  

    -   Controleer of de nieuwste Configuration Manager-opstartinstallatiekopieën de gewenste aanpassingen bevatten en update vervolgens alle distributiepunten op de sites met de meest recente versie van Configuration Manager met de nieuwe opstartinstallatiekopieën.  

-   Hulpprogramma voor migratie van gebruikersstatus (USMT)  

    -   Wanneer u een upgrade uitvoert van het hoogste niveau naar de nieuwste versie van Configuration Manager, wordt het standaard USMT-pakket automatisch bijgewerkt naar de nieuwste versie. Aangepaste USMT-pakketten worden niet automatisch bijgewerkt. U moet deze pakketten handmatig bijwerken.  

-   Stappen voor nieuwe takenreeksen  

    -   Stappen voor nieuwe takenreeksen binnenkomen van tijd tot tijd met nieuwe versies van Configuration Manager. Wanneer u een takenreeks implementeert met een nieuwe stap voor oudere clients, mislukt de takenreeksstap. Voordat u een takenreeks implementeert met een nieuwe stap, controleert u of de clients in de doelverzameling zijn bijgewerkt naar de nieuwe versie.  

-   Media voor implementatie van besturingssysteem  

    -   Alle media (opstartbaar vastleggen, vooraf geplaatste en zelfstandige) moeten worden bijgewerkt met de nieuwe Configuration Manager-clientpakket wanneer de site wordt bijgewerkt naar een nieuwe versie.  

-   Uitbreidingen van derden voor besturingssysteemimplementaties  

    -   Wanneer u derden uitbreidingen voor implementatie van besturingssysteem hebt en u verschillende versies van Configuration Manager-sites of Configuration Manager-clients, een gemengde hiërarchie hebt, is er mogelijk problemen met de extensies.  

 Raadpleeg tijdens het bijwerken van de sites in uw hiërarchie de volgende secties voor hulp bij besturingssysteemimplementaties.  

## <a name="latest-version-of-configuration-manager-sites-in-a-mixed-hierarchy"></a>Meest recente versie van Configuration Manager-sites in een gemengde hiërarchie  
 Wanneer u een site upgradet naar de meest recente versie van Configuration Manager, takenreeksen die een verwijzing naar het standaard clientinstallatiepakket automatisch wordt gestart voor het implementeren van de meest recente clientversie van de Configuration Manager. Takenreeksen die naar een aangepast clientinstallatiepakket verwijzen, blijven de versie van de client die is opgenomen in dat aangepaste pakket (waarschijnlijk een vorige Configuration Manager-clientversie) implementeren, en moeten worden bijgewerkt om fouten bij de implementatie van takenreeksen te voorkomen. Wanneer u een takenreeks die is geconfigureerd voor gebruik van een aangepast clientinstallatiepakket hebt, moet u de takenreeksstap zodanig dat de nieuwste Configuration Manager-versie van het clientinstallatiepakket gebruikt of werkt u het aangepaste pakket voor het gebruik van de meest recente installatiebron van de Configuration Manager-client bijwerken.  

> [!IMPORTANT]  
>  Implementeer een takenreeks die verwijst naar het nieuwste Configuration Manager-clientinstallatiepakket op clients in een oudere Configuration Manager-site niet. Wanneer clients toegewezen aan een oudere Configuration Manager-site zijn bijgewerkt naar de nieuwste Configuration Manager-clientversie, blokkeert Configuration Manager de toewijzing aan de oudere Configuration Manager-site. Daarom wordt de client is niet langer toegewezen aan een site en zijn niet-beheerd totdat u handmatig de client aan het nieuwste Configuration Manager-site toewijzen of de oudere versie van de Configuration Manager van de client op de computer installeert.  

## <a name="older-versions-of-configuration-manager-in-a-mixed-hierarchy"></a>Oudere versies van Configuration Manager in een gemengde hiërarchie  
 Wanneer u uw centrale beheersite hebt bijgewerkt naar de nieuwste versie van Configuration Manager, moet u de volgende stap uit om ervoor te zorgen dat takenreeksen van het besturingssysteem-implementatie die u voor clients toegewezen aan een oudere Configuration Manager-site implementeert (nog niet bijgewerkt naar de nieuwste versie van Configuration Manager) niet op deze clients in een onbeheerde staat laat nemen.  

-   Maak een takenreeks die u gebruiken wilt voor het implementeren op clients alleen in een Configuration Manager-site. Maak een kopie van een takenreeks die u kunt implementeren op clients in de nieuwste versie van Configuration Manager-site en wijzig vervolgens de takenreeks zodat u ze op clients in een oudere Configuration Manager-site implementeren kunt. Configureer vervolgens de takenreeks om te verwijzen naar een aangepast clientinstallatiepakket die gebruikmaakt van de oudere installatiebron van de Configuration Manager-client. Als u nog een aangepast clientinstallatiepakket dat verwijst naar de oudere installatiebron van de Configuration Manager-client moet u handmatig maken een.  

