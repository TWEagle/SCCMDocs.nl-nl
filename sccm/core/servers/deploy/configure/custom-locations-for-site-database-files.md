---
title: Aangepaste databasebestandslocaties | Microsoft Docs
description: Informatie over het opgeven van aangepaste locaties voor SQL Server-databasebestanden.
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: cfac2c03c1b71b40c68d8acd5fbd96c5e98caaa9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="custom-locations-for-system-center-configuration-manager-site-database-files"></a>Aangepaste locaties voor System Center Configuration Manager site-databasebestanden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 System Center Configuration Manager ondersteunt aangepaste locaties voor SQL Server-databasebestanden.  

> [!NOTE]  
>  De optie voor het opgeven van niet-standaard bestandslocaties is niet beschikbaar wanneer u een SQL Server-cluster gebruikt.  

 **Tijdens de installatie** van een nieuwe primaire site of centrale beheersite, kunt u:  

-   **Geef niet-standaard bestandslocaties voor de sitedatabase**: Setup van Configuration Manager maakt vervolgens de sitedatabase met behulp van deze locaties.  

-   **Geef het gebruik van een vooraf gemaakte SQL Server-database die gebruikmaakt van aangepaste bestandslocaties**:  Setup van Configuration Manager gebruikt vervolgens die vooraf gemaakte database en de vooraf geconfigureerde bestandslocaties.  

**Na de installatie**, kunt u de locatie van de sitedatabasebestanden wijzigen. Hiervoor moet u de site stoppen en de bestandslocatie in SQL Server bewerken:  

-   Stop op de siteserver van Configuration Manager de **SMS_Executive** service.  

-   Gebruik de documentatie voor uw versie van SQL Server voor meer informatie over het verplaatsen van een gebruikersdatabase. Bijvoorbeeld, als u SQL Server 2014 gebruikt, Zie [gebruikersdatabases verplaatsen](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) op TechNet.  

-   Nadat u het databasebestand verplaatst hebt voltooid, start opnieuw op de **SMS_Executive** service op de siteserver van Configuration Manager.  
