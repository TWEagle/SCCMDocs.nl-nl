---
title: Configuratiegegevens beheren
titleSuffix: Configuration Manager
description: Nadat u configuratie-items en basislijnen in System Center Configuration Manager maakt, kunt u andere opdrachten verschillende acties uit te voeren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b48c693c-d2b0-4707-a5dd-fe92172c49fe
caps.latest.revision: "7"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 23a6bcf2e9fcb417dabde7700e09c953d436deb7
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-configuration-data-in-system-center-configuration-manager"></a>Configuratiegegevens in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u configuratie-items en configuratiebasislijnen in System Center Configuration Manager gemaakt hebt, meer zijn opdrachten beschikbaar waarmee u verschillende acties uitvoeren.  

## <a name="manage-configuration-items"></a>Configuratie-items beheren  

-   In de **activa en naleving** werkruimte Vouw **instellingen voor naleving** > **configuratie-Items**, selecteert u het configuratie-item voor het beheren en selecteer vervolgens een beheertaak.  

|Beheertaak|Details|  
|---------------------|-------------|  
|**Onderliggend configuratie-item maken**|Hiermee opent u de **Wizard Onderliggend configuratie-item maken** waarmee u een onderliggend configuratie-item kunt maken van het geselecteerde configuratie-item.<br /><br /> U kunt geen onderliggend configuratie-item maken van een configuratie-item voor mobiele apparaten.<br /><br /> Zie voor meer informatie [onderliggende configuratie-items maken](../../compliance/deploy-use/create-child-configuration-items.md).|  
|**Overzicht van wijzigingen**|Hiermee opent u het dialoogvenster **Overzicht van wijzigingen van configuratie-item** waarin u eerdere versies van het geselecteerde configuratie-item kunt weergeven en beheren.|  
|**XML-definitie weergeven**|Toont de definitie van het XML-bestand voor het geselecteerde configuratie-item in een nieuw venster. Deze informatie kan nuttig zijn wanneer u configuratiegegevens handmatig wilt maken.|  
|**Exportereneren**|Exporteert een configuratie-item naar een CAB-bestand-indeling, mits het is gemaakt op die site. U kunt deze vervolgens importeren naar dezelfde of een andere Configuration Manager-site. Configuratiegegevens worden geconverteerd naar DCM Digest.|  
|**Kopiëren**|Maakt een kopie van het geselecteerde configuratie-item met een naam die u opgeeft. Het nieuwe configuratie-item behoudt geen relatie met het oorspronkelijke configuratie-item. Dit betekent dat het dubbele configuratie-item geen configuratie-informatie blijft overnemen van het oorspronkelijke configuratie-item.|  
|**Verwijderen**|Hiermee opent u het dialoogvenster **Configuratie-item verwijderen** waarin u alle verwijzingen naar dit configuratie-item kunt bekijken.<br /><br /> U moet alle verwijzingen naar een configuratie-item verwijderen voordat u dit kunt verwijderen.|  

## <a name="manage-configuration-baselines"></a>Configuratiebasislijnen beheren  

-   In de **activa en naleving** werkruimte Vouw **instellingen voor naleving** > **Configuratiebasislijnen**, selecteer de configuratiebasislijn voor het beheren en selecteer vervolgens een beheertaak.  


|Beheertaak|Details|  
|---------------------|-------------|  
|**Leden weergeven**|Geeft alle configuratie-items weer waarnaar wordt verwezen door de configuratiebasislijn.|  
|**Overzicht plannen**|Configureert de planning op waarmee de gegevens weergegeven in de **Configuratiebasislijnen** knooppunt in de Configuration Manager-console wordt bijgewerkt met de meest recente informatie uit de sitedatabase.|  
|**Overzicht uitvoeren**|Het maken van een overzicht zorgt ervoor dat de gegevens op het knooppunt **Configuratiebasislijnen** worden vernieuwd met de meest recente gegevens uit de sitedatabase. Deze actie kan enkele minuten duren. Mogelijk moet u op **Vernieuwen** klikken voordat u de meest recente gegevens in de console kunt zien.|  
|**XML-definitie weergeven**|Toont de definitie van het XML-bestand voor de geselecteerde configuratiebasislijn in een nieuw venster. Deze informatie kan nuttig zijn wanneer u configuratiegegevens handmatig wilt maken.|  
|**Inschakelen**|Hiermee wordt een configuratiebasislijn ingeschakeld voor het bewaken van naleving.|  
|**Uitschakelen**|Hiermee wordt een configuratiebasislijn uitgeschakeld zodat deze niet langer wordt geëvalueerd voor naleving op clientcomputers. Configuratiebasislijnen die verwijzen naar deze configuratiebasislijn worden ook uitgeschakeld.|  
|**Exportereneren**|Exporteert een configuratiebasislijn naar een CAB-bestand-indeling, mits deze is gemaakt op die site. U kunt deze vervolgens importeren naar dezelfde of een andere Configuration Manager-site. Configuratiegegevens worden geconverteerd naar DCM Digest.<br /><br /> Zie voor meer informatie over het importeren van configuratiegegevens [configuratiegegevens importeren](../../compliance/deploy-use/import-configuration-data.md).|  
|**Kopiëren**|Maakt een kopie van de geselecteerde configuratiebasislijn met een naam die u opgeeft. De nieuwe configuratiebasislijn behoudt geen relatie met de oorspronkelijke configuratiebasislijn.|  
|**Verwijderen**|Hiermee opent u het dialoogvenster **Configuratiebasislijn verwijderen** waarin u alle verwijzingen naar deze configuratiebasislijn kunt bekijken.<br /><br /> U moet alle verwijzingen naar een configuratiebasislijn verwijderen voordat u deze kunt verwijderen.|  
|**Implementeren**|Hiermee opent u het dialoogvenster **Configuratiebasislijn implementeren** waarin u een of meer configuratiebasislijnen kunt implementeren op apparaten in uw hiërarchie.<br /><br /> Zie voor meer informatie [configuratiebasislijnen implementeren](../../compliance/deploy-use/deploy-configuration-baselines.md).|  
