---
title: Aangepaste databasebestandslocaties | Microsoft-documenten
description: Leer hoe u aangepaste locaties voor SQL Server-databasebestanden opgeven.
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e5155aa8c03b7e0c200d083024c8fa386f97aa7
ms.openlocfilehash: cfac2c03c1b71b40c68d8acd5fbd96c5e98caaa9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="custom-locations-for-system-center-configuration-manager-site-database-files"></a>Aangepaste locaties voor System Center Configuration Manager site-databasebestanden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 System Center Configuration Manager ondersteunt aangepaste locaties voor SQL Server-databasebestanden.  

> [!NOTE]  
>  De optie voor het opgeven van niet-standaard bestandslocaties is niet beschikbaar wanneer u een SQL Server-cluster.  

 **Tijdens de installatie** van een nieuwe primaire site of centrale beheersite, kunt u:  

-   **Geef niet-standaardlocaties voor de sitedatabase**: Installatie van Configuration Manager maakt u de sitedatabase met behulp van deze locaties.  

-   **Geef het gebruik van een vooraf gemaakte database van SQL Server die gebruikmaakt van aangepaste bestandslocaties**:  Installatie van Configuration Manager gebruikt vervolgens de vooraf geconfigureerde locaties en vooraf gemaakte database.  

**Na de installatie**, kunt u de locatie van bestanden van de sitedatabase. Hiervoor moet u de site stoppen en de bestandslocatie in SQL Server bewerken:  

-   Stop op de siteserver van Configuration Manager de **SMS_Executive** service.  

-   De documentatie voor uw versie van SQL Server gebruiken om u voor het verplaatsen van een gebruikersdatabase. Bijvoorbeeld, als u SQL Server 2014, Zie [gebruikersdatabases verplaatsen](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) op TechNet.  

-   Nadat u het databasebestand verplaatst hebt voltooid, start opnieuw op de **SMS_Executive** service op de siteserver van Configuration Manager.  

