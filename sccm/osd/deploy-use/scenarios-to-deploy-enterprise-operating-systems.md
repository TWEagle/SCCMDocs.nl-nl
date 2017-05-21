---
title: Scenario&quot;s voor het implementeren van besturingssystemen enterprise | Microsoft-documenten
description: Meer informatie over verschillende scenario&quot;s voor het implementeren van enterprise-besturingssystemen met System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f74fdb86-c7c2-447f-91f6-b42df6370d7f
caps.latest.revision: 11
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: b1bea8b1b890f7c96a432835d28ad840a9b6873d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="scenarios-to-deploy-enterprise-operating-systems-with-system-center-configuration-manager"></a>Scenario’s voor het implementeren van enterprise-besturingssystemen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Het volgen van besturingssysteem zijn implementatiescenario's beschikbaar in System Center Configuration Manager:  

-   [Upgrade van Windows voor de nieuwste versie](upgrade-windows-to-the-latest-version.md): Dit scenario werkt het besturingssysteem op computers waarop Windows 7, Windows 8, Windows 8.1 of Windows 10 momenteel wordt uitgevoerd. Bij deze upgrade blijven de toepassingen, instellingen en gebruikersgegevens op de computer behouden Er zijn geen externe afhankelijkheden, zoals Windows ADK. Bovendien verloopt dit proces sneller en biedt het meer flexibiliteit dan de traditionele besturingssysteemimplementaties.  

-   [Vernieuwen van een bestaande computer met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md): In dit scenario partities en -indelingen (wis) een bestaande computer en een nieuw besturingssysteem installeert op de computer. U kunt de instellingen en gebruikersgegevens migreren nadat het besturingssysteem is geïnstalleerd.  

-   [Een nieuwe versie van Windows installeren op een nieuwe computer (bare metal)](install-new-windows-version-new-computer-bare-metal.md): Dit scenario wordt een besturingssysteem op een nieuwe computer geïnstalleerd. Dit is een nieuwe installatie van het besturingssysteem en het omvat geen migratie van instellingen of gebruikersgegevens.  

-   [Vervangen van een bestaande computer en Overdrachtinstellingen](replace-an-existing-computer-and-transfer-settings.md): Dit scenario wordt een besturingssysteem op een nieuwe computer geïnstalleerd. U kunt eventueel instellingen en gebruikersgegevens van de oude computer naar de nieuwe computer migreren.  

## <a name="things-to-consider-before-you-deploy-operating-system-images"></a>Zaken die u moet overwegen voordat u installatiekopieën van besturingssystemen implementeert  
 U moet een aantal zaken overwegen voordat u een besturingssysteem implementeert.  

### <a name="operating-system-image-size"></a>Grootte van de installatiekopie van het besturingssysteem  
 De omvang van een installatiekopie van een besturingssysteem kan behoorlijk groot zijn. De grootte van de installatiekopie voor Windows 7 is bijvoorbeeld drie gigabyte (GB) of meer. De grootte van de installatiekopie en het aantal computers waarop u tegelijkertijd het besturingssysteem implementeert, beïnvloedt de netwerkprestatie en de beschikbare bandbreedte. Test zeker de netwerkprestatie om beter te meten wat de impact is die de implementatie van de installatiekopie heeft en de tijd die nodig is om de implementatie te vervolledigen. Configuration Manager-activiteiten die netwerkprestaties beïnvloeden, omvatten overbrengen van een installatiekopie naar een distributiepunt, het overbrengen van de installatiekopie van de ene site naar een andere en het downloaden van de installatiekopie naar de Configuration Manager-client.  

 Wees er ook zeker van dat u voldoende schrijfruimte voorziet op de distributiepunten die de installatiekopieën van de besturingssystemen hosten.  

### <a name="client-cache-size"></a>Clientcachegrootte  
 Als Configuration Manager-clients inhoud downloaden, gebruiken ze automatisch Background Intelligent Transfer Service (BITS) als deze beschikbaar is. Wanneer u een takenreeks die u een besturingssysteem installeert implementeert, kunt u een optie op de implementatie kunt instellen, zodat Configuration Manager-clients de volledige installatiekopie naar een lokale cache downloaden vóór de takenreeks wordt uitgevoerd.  

 In het algemeen, wanneer een Configuration Manager-client downloaden moet, een installatiekopie van het besturingssysteem (of een ander pakket), maar er onvoldoende ruimte in de cache is, controleert de klant de andere pakketten in de cache om te bepalen of wissen van één of alle van de oudste pakketten voldoende schijfruimte aanpassen aan de afbeelding zal vrijmaken. Als er met het verwijderen van pakketten onvoldoende schijfruimte wordt vrijgemaakt, wordt de installatiekopie niet door de client gedownload en mislukt de implementatie. Dit kan gebeuren als het cachegeheugen een groot pakket bevat die zodanig is geconfigureerd dat deze in het cachegeheugen blijft behouden. Als er met het verwijderen van pakketten voldoende geheugen wordt vrijgemaakt in de cache, worden ze verwijderd en downloadt de client de installatiekopie naar het cachegeheugen.  

 De standaardcachegrootte op Configuration Manager-clients mogelijk niet groot genoeg zijn voor de meeste implementaties van installatiekopieën van besturingssysteem. Als u van plan bent de volledige installatiekopie downloaden naar de clientcache, moet u de cachegrootte van de Configuration Manager-client op de doelcomputers om de grootte van de afbeelding die u implementeert te brengen aanpassen.  

 Zie [De clientcache configureren voor Configuration Manager-clients](../../core/clients/manage/manage-clients.md#BKMK_ClientCache) voor meer informatie.  

## <a name="task-sequence-deployments"></a>Implementaties van takenreeksen  
 De takenreeks die u kunt de installatiekopie van het besturingssysteem op een clientcomputer Configuration Manager implementeren in een van de volgende manieren:  

-   Download de installatiekopie en haar inhoud eerst naar de clientcache voor Configuration Manager van een distributiepunt en installeer deze vervolgens.  

-   Installeer de installatiekopie en haar inhoud onmiddellijk vanaf het distributiepunt.  

-   Installeer de installatiekopie en haar inhoud zoals vereist is vanaf het distributiepunt.  

 Standaard bij het maken van de implementatie voor de takenreeks de installatiekopie wordt eerst gedownload naar de clientcache voor Configuration Manager en vervolgens geïnstalleerd. Als u de installatiekopie te downloaden naar de clientcache voor Configuration Manager voordat u de installatiekopie uitvoert, en de takenreeks bevat een stap om de harde schijf te partitioneren, de stap opnieuw partitioneren mislukt omdat de vaste schijf partitioneren wist u de inhoud van de clientcache voor Configuration Manager. Indien de takenreeks de harde schijf moet partitioneren, moet u de installatie van de installatiekopie uitvoeren vanaf het distributiepunt door de optie **Programma uitvoeren vanaf het distributiepunt**  te gebruiken wanneer u de takenreeks implementeert.  

 Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie.  

