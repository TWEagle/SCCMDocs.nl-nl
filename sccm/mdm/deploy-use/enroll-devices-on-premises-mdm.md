---

title: Apparaten inschrijven | Microsoft-documenten
description: Meer informatie over methoden om apparaten te registreren voor On-premises mobiele apparaten beheren in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
caps.latest.revision: 6
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b1451edaed69a972551bd060293839aa11ec8b2
ms.openlocfilehash: 4abaef35969ef1a5340ae8ca8aa5699cd3942642
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-devices-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Apparaten inschrijven voor On-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voor het beheren van computers en apparaten met System Center Configuration Manager On-premises mobiele apparaten beheren, moeten de apparaten worden ingeschreven zodat dat Configuration Manager met de apparaten voor beheertaken communiceren kan. Configuration Manager biedt twee methoden voor het inschrijven van apparaten:  

-   **Gebruikersregistratie** : bij deze methode initiëren de gebruikers zelf het inschrijvingsproces op hun apparaten. Voor gebruikersregistratie lukken, moet het apparaat een vertrouwd basiscertificaat dat is geïnstalleerd, en de gebruiker moet worden ingericht voor inschrijving door Configuration Manager.  Voor het inschrijven van het apparaat geeft de gebruiker gewoon werkreferenties op, waarna het apparaat voor beheer kan worden ingeschreven.  

     Zie voor meer informatie [hoe gebruikers apparaten inschrijven met On-premises mobiele apparaten beheren in System Center Configuration Manager](../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

-   **Bulkinschrijving** : bij deze methode hoeft de gebruiker de inschrijving van het apparaat niet zelf te initiëren. In plaats daarvan wordt een registratiepakket bulksgewijs in Configuration Manager gemaakt en vervolgens plaatsen op het apparaat en geopend. Bij het openen biedt het pakket de benodigde informatie om het apparaat in te schrijven.  

     Zie voor meer informatie [hoe bulk-apparaten inschrijven met On-premises mobiele apparaten beheren in System Center Configuration Manager](../../mdm/deploy-use/bulk-enroll-devices-on-premises-mdm.md)  

 > [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt de inschrijving in beheer van mobiele apparaten On-premises voor apparaten met de volgende besturingssystemen:  
>   
>  -   Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team 
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise   

