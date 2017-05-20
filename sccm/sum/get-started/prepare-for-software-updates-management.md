---

title: Voorbereiden voor beheer van software-updates | Microsoft-documenten
description: Om voor te bereiden om updates te beheren, deze taken uitvoeren om gegevens van de compatibiliteitsbeoordeling in de System Center Configuration Manager-console weergegeven.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 01907900-e28b-4cd7-9479-42906416707b
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 5c34bd1ea108dffda10c30281fb9c97ba38ae1ae
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="prepare-for-software-updates-management"></a>Voorbereiden voor beheer van software-updates

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat de gegevens van de compatibiliteitsbeoordeling van de software-update wordt weergegeven in de System Center Configuration Manager-console en voordat u software-updates op clientcomputers kunt implementeren, moet u de stappen in de volgende secties.

## <a name="step-1-install-a-software-update-point"></a>Stap 1: Installeert een software-updatepunt  
De software-updatepunt is vereist op de centrale beheersite of zelfstandige primaire site en op primaire sites om de software-updates beoordeling van naleving en software-updates implementeren op clients. Het software-updatepunt is optioneel op secundaire sites. Zie voor meer informatie, [installeert een software-updatepunt](install-a-software-update-point.md)  

## <a name="step-2-synchronize-software-updates"></a>Stap 2: Software-Updates synchroniseren
Synchronisatie van software-updates is het proces van het ophalen van de metagegevens van de software-updates die voldoet aan de criteria die u configureert. Software-updates worden niet weergegeven in de Configuration Manager-console totdat u de software-updates synchroniseren. Zie voor meer informatie, [software-updates synchroniseren](synchronize-software-updates.md).   

## <a name="step-3-configure-classifications-and-products-to-synchronize"></a>Stap 3: Configureer classificaties en producten voor synchronisatie
Voer deze configuratie uit op de centrale beheersite of de zelfstandige primaire site. Na het synchroniseren van software-updates voor het eerst wordt een bijgewerkte lijst van classificaties en producten in Configuration Manager opgehaald. U kunt nu selecteren uit de nieuwe opties in de eigenschappen van onderdeel Software-updatepunt. Nadat u de nieuwe classificaties en producten configureren, herhaalt u stap 2 starten van synchronisatie van software-updates voor het ophalen van metagegevens van software-updates voor de nieuwe criteria. Zie voor meer informatie, [Configureer classificaties en producten voor synchronisatie](configure-classifications-and-products.md).

## <a name="step-4-manage-settings-for-software-updates"></a>Stap 4: Instellingen voor software-updates beheren
Nadat u software-updates synchroniseert, controleert u of Configuration Manager-clientinstellingen en groepsbeleidconfiguraties instellingen voor software-updates voordat u software-updates implementeren. Zie voor meer informatie, [instellingen beheren voor software-updates](manage-settings-for-software-updates.md).

