---
title: Interoperabiliteit bij de implementatie van besturingssystemen plannen
titleSuffix: Configuration Manager
description: "Compatibiliteitsproblemen begrijpen wanneer verschillende System Center Configuration Manager-sites in één hiërarchie verschillende versies gebruiken."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e327ce38-6c07-4a27-b6eb-7e5bf74ed04b
caps.latest.revision: "10"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 41c7c83602f965cd4a225d38a00b90501206de45
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="planning-for-operating-system-deployment-interoperability-in-system-center-configuration-manager"></a>De interoperabiliteit voor de besturingssysteemimplementatie plannen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer verschillende System Center Configuration Manager-sites in één hiërarchie verschillende versies gebruiken, is enkele Configuration Manager-functionaliteit niet beschikbaar. De nieuwere versie van Configuration Manager-functionaliteit is normaal gesproken niet toegankelijk op sites of voor clients met een lagere versie. Zie [Interoperabiliteit tussen verschillende versies van System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md) voor meer informatie.  

 Overweeg het volgende wanneer u de site op het hoogste niveau in uw hiërarchie en andere sites in uw hiërarchie Configuration Manager uitvoeren met een lagere versie upgraden:  

-   Clientinstallatiepakket  

    -   De bron voor het standaardclientinstallatiepakket wordt automatisch bijgewerkt en alle distributiepunten in de hiërarchie zijn bijgewerkt met het nieuwe clientinstallatiepakket, zelfs op distributiepunten van sites in de hiërarchie die een lagere versie.  

    -   Clients met de nieuwe versie kunnen niet worden toegewezen aan sites die nog niet zijn bijgewerkt naar de nieuwe versie. Toewijzing wordt geblokkeerd op het beheerpunt.  

-   Installatiekopieën  

    -   Wanneer u op het hoogste niveau naar de nieuwste versie van Configuration Manager bijwerkt, worden de standaardopstartinstallatiekopieën (x86- en x64) automatisch bijgewerkt naar Windows ADK voor Windows 10-gebaseerde opstartinstallatiekopieën, die gebruikmaken van Windows PE 10. De bestanden die gekoppeld aan de standaardopstartinstallatiekopieën zijn worden bijgewerkt met de meest recente versie van Configuration Manager van de bestanden. Aangepaste opstartinstallatiekopieën worden niet automatisch bijgewerkt. U moet aangepaste opstartinstallatiekopieën handmatig bijwerken waaronder oudere versies van Windows PE.  

    -   Vermijd het gebruik van dynamische media wanneer uw sitehiërarchie sites met verschillende versies van Configuration Manager bevat. Gebruik in plaats daarvan site gebaseerde media contact opnemen met een bepaald beheerpunt totdat alle sites zijn bijgewerkt naar dezelfde versie van Configuration Manager.  

    -   Controleer of de nieuwste Configuration Manager-opstartinstallatiekopieën de gewenste aanpassingen bevatten en update vervolgens alle distributiepunten op de sites met de meest recente versie van Configuration Manager met de nieuwe opstartinstallatiekopieën.  

-   Hulpprogramma voor migratie van gebruikersstatus (USMT)  

    -   Wanneer u op het hoogste niveau naar de nieuwste versie van Configuration Manager bijwerkt, wordt het standaard USMT-pakket automatisch bijgewerkt naar de nieuwste versie. Aangepaste USMT-pakketten worden niet automatisch bijgewerkt. U moet deze pakketten handmatig bijwerken.  

-   Stappen voor nieuwe takenreeksen  

    -   Regelmatig nieuwe takenreeksstappen geïntroduceerd met nieuwe versies van Configuration Manager. Wanneer u een takenreeks implementeert met een nieuwe stap voor oudere clients, mislukt de takenreeksstap. Voordat u een takenreeks implementeert met een nieuwe stap, controleert u of de clients in de doelverzameling zijn bijgewerkt naar de nieuwe versie.  

-   Media voor implementatie van besturingssysteem  

    -   Alle media (opstartbare, voor vastlegging, vooraf geplaatste en zelfstandige) moeten worden bijgewerkt met de nieuwe Configuration Manager-clientpakket wanneer de site is bijgewerkt naar een nieuwe versie.  

-   Uitbreidingen van derden voor besturingssysteemimplementaties  

    -   Als u uitbreidingen van derden voor besturingssysteemimplementaties hebt en u verschillende versies van Configuration Manager-sites of Configuration Manager-clients, een gemengde hiërarchie hebt, is het mogelijk dat er problemen met de extensies.  

 Raadpleeg tijdens het bijwerken van de sites in uw hiërarchie de volgende secties voor hulp bij besturingssysteemimplementaties.  

## <a name="latest-version-of-configuration-manager-sites-in-a-mixed-hierarchy"></a>Meest recente versie van Configuration Manager-sites in een gemengde hiërarchie  
 Wanneer u een site bijwerkt naar de meest recente versie van Configuration Manager, takenreeksen die een verwijzing naar het standaardclientinstallatiepakket automatisch gestart wordt voor het implementeren van de meest recente clientversie van de Configuration Manager. Takenreeksen die naar een aangepast clientinstallatiepakket verwijzen, blijven de versie van de client die is opgenomen in dat aangepaste pakket (waarschijnlijk een voorgaande Configuration Manager-clientversie) implementeren, en moeten worden bijgewerkt om fouten bij de takenreeksimplementatie te voorkomen. Wanneer u een takenreeks die is geconfigureerd voor gebruik van een aangepast clientinstallatiepakket hebt, moet u de takenreeksstap voor het gebruik van de nieuwste Configuration Manager-versie van het clientinstallatiepakket of bijwerken van het aangepaste pakket voor het gebruik van de meest recente installatiebron van de Configuration Manager-client bijwerken.  

> [!IMPORTANT]  
>  Implementeer een takenreeks die verwijst naar het nieuwste Configuration Manager-clientinstallatiepakket naar clients in een oudere Configuration Manager-site niet. Wanneer clients toegewezen aan een oudere Configuration Manager-site worden bijgewerkt naar de nieuwste Configuration Manager-clientversie, blokkeert Configuration Manager de toewijzing aan de oudere Configuration Manager-site. De client wordt daarom niet langer toegewezen aan een site en deze niet-beheerd totdat u handmatig de client aan de nieuwste Configuration Manager-site toewijzen of installeer de oudere versie van Configuration Manager van de client op de computer.  

## <a name="older-versions-of-configuration-manager-in-a-mixed-hierarchy"></a>Oudere versies van Configuration Manager in een gemengde hiërarchie  
 Wanneer u uw centrale beheersite hebt bijgewerkt naar de nieuwste versie van Configuration Manager, moet u rekening houden met de volgende stap om ervoor te zorgen dat takenreeksen van het besturingssysteem-implementatie die u voor clients toegewezen aan een oudere Configuration Manager-site implementeert (nog niet bijgewerkt naar de nieuwste versie van Configuration Manager) niet deze clients in een onbeheerde staat laat.  

-   Maak een takenreeks die u gebruiken wilt om te implementeren op clients alleen in een Configuration Manager-site. Maak een kopie van een takenreeks die u kunt implementeren op clients in de nieuwste versie van Configuration Manager-site en wijzig vervolgens de takenreeks zodat u deze op clients in een oudere Configuration Manager-site implementeren kunt. Configureer vervolgens de takenreeks wordt uitgevoerd om te verwijzen naar een aangepast clientinstallatiepakket dat gebruikmaakt van de oudere installatiebron van de Configuration Manager-client. Als u nog geen een aangepast clientinstallatiepakket dat verwijst naar de oudere installatiebron van de Configuration Manager-client vervolgens u moet dit handmatig maken.  
