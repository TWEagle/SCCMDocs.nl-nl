---
title: Installatie van Updates Publisher | Microsoft Docs
description: System Center Updates Publisher installeren in uw omgeving
ms.custom: na
ms.date: 07/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab5cda93-b67c-4aa5-904d-7b63ce790aa0
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 70772ba7d08560aa66abcce29dc6cc6334aa2032
ms.openlocfilehash: 63ea0383497a3f06870c0907c732010259d1a809
ms.contentlocale: nl-nl
ms.lasthandoff: 07/03/2017

---
# <a name="install-updates-publisher"></a>Installatie van Updates Publisher

*Van toepassing op: System Center Updates Publisher*

De informatie in dit onderwerp kunt u verkrijgen, installeren en instellen van Updates Publisher voor gebruik met uw omgeving.


## <a name="prerequisites-and-limitations"></a>Vereisten en beperkingen
De volgende secties detailleren de vereisten voor het installeren en gebruiken van Updates Publisher en beperkingen of bekende problemen voor het gebruik ervan.

### <a name="operating-systems"></a>Besturingssystemen
Installeren en uitvoeren van Updates Publisher op een 64-bits versies van de volgende besturingssystemen. Er zijn geen minimale cumulatieve update of service pack-vereisten.

-   WindowsServer 2016 (Standard, Datacenter)
-   Windows Server 2012 R2 (Standard, Datacenter)
-   Windows 10 (Pro, Education, Pro, Education en Enterprise)
-   Windows 8.1 (Professional, Enterprise)

### <a name="prerequisites"></a>Vereisten
Het volgende is vereist op de computer waarop Updates Publisher wordt uitgevoerd.

-   **64-bits besturingssysteem**: De computer waarop het installeren van Updates Publisher moet een 64-bits besturingssysteem uitvoeren.
-   **WSUS 4.0 of hoger**:
    -   Installeer de standaard-beheerconsole om te voldoen aan deze vereiste op Windows Server.
    -   Voor Windows 10 en Windows 8.1, installeert u de [Remote Server Administration Tools (RSAT) voor Windows-besturingssystemen](https://support.microsoft.com/help/2693643/remote-server-administration-tools-rsat-for-windows-operating-systems). Hiermee installeert u de benodigde ondersteuning voor het gebruik van Updates Publisher (*API en PowerShell-cmdlets*, en *beheerconsole voor gebruikersinterface*).
-   **Machtigingen**:
    -   Installatie: Lokale beheerder
    -   De meeste bewerkingen: lokale gebruiker
    -   Publicatie of bewerkingen die betrekking hebben op WSUS: Lid van de groep WSUS-Administrators op de WSUS-Server.

### <a name="supported-languages"></a>Ondersteunde talen
Updates Publisher is alleen beschikbaar in het Engels, maar kunt beheren van updates voor andere talen. De taalondersteuning is afhankelijk van de taak, zoals het publiceren, maken of bewerken van updates.

Wanneer u exporteert of updates publiceren, weergegeven Updates Publisher de titel en beschrijving van de software-update op basis van de landinstellingen van de computer waarop Updates Publisher is geïnstalleerd.

U maakt bijvoorbeeld een software-update met een titel voor Engels en Spaans.

-   Als u de update op een computer waarvan de landinstelling Engels standaard is maakt, ziet u de titel en beschrijving in het Engels.
-   Als u vervolgens exporteren of publiceert dat de update op een computer waarvan de landinstelling Spaans is, op die computer ziet u de titel en beschrijving in het Spaans.

### <a name="publishing"></a>Publiceren
Wanneer u software-updates publiceert, kunt u de taal van het binaire bestand voor software-update. U kunt ook opgeven dat het binaire bestand taalonafhankelijk. De volgende talen worden ondersteund:

-   Arabisch
-   Chinees (Hongkong SAR)
-   Chinees (Traditioneel)
-   Chinees (Vereenvoudigd)
-   Tsjechisch
-   Deens
-   Nederlands
-   Engels
-   Fins
-   Frans
-   German
-   Grieks
-   Hebreeuws
-   Hongaars
-   Italian
-   Japans
-   Koreaans
-   Noors
-   Pools
-   Portugees
-   Portugees (Brazilië)
-   Russisch
-   Spaans
-   Zweeds
-   Turks

### <a name="software-update-titles-and-descriptions"></a>Software-update titels en beschrijvingen
De volgende talen worden ondersteund voor software-update titels en beschrijvingen.

-   Chinees (Traditioneel)
-   Chinees (Vereenvoudigd)
-   Engels
-   Frans
-   German
-   Italian
-   Japans
-   Koreaans
-   Portugees (Brazilië)
-   Russisch
-   Spaans



## <a name="install-updates-publisher"></a>Installatie van Updates Publisher
Ophalen van de **UpdatesPubliser.msi** voor het installeren van System Center Updates Publisher van de [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=847967).

U installeert de Updates Publisher, **UpdatesPublisher.msi** op een computer die voldoet aan de *vereisten*. Het installatieprogramma maakt de volgende map bevat de bestanden die nodig zijn om uit te voeren van Updates Publisher:  *&lt;pad&gt;\Program Files\Microsoft\UpdatesPublisher*.

Omdat deze map alle bestanden bevat met Updates Publisher, kunt u de map en haar inhoud kopiëren naar een nieuwe locatie of de computer en vervolgens met Updates Publisher vanaf die locatie. Echter, de nieuwe locatie of de computer moet voldoen aan de vereisten voor het uitvoeren van Updates Publisher.

Nadat de installatie is voltooid, voert u **UpdatesPublisher.exe** van de *UpdatesPublisher* map voor het starten van de Updates Publisher.

## <a name="next-steps"></a>Volgende stappen
 Na de installatie van Updates Publisher, raden we u [configureren van de opties](updates-publisher-options.md) voor Updates Publisher. Voordat u bepaalde functies van Updates Publisher kunt gebruiken, moet u enkele mogelijkheden configureren.

 Als u wilt de standaardinstellingen te gebruiken en niet van plan bent om updates te implementeren op een server of op beheerde apparaten, kunt u echter het recht om te gaan [software-update-catalogussen beheren](updates-publisher-catalogs.md), of [software-updates maken](create-updates-with-updates-publisher.md) en update catalogi van uw eigen maakt.

