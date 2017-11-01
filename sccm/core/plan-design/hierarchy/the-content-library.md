---
title: De Inhoudsbibliotheek
titleSuffix: Configuration Manager
description: Meer informatie over de Inhoudsbibliotheek die System Center Configuration Manager gebruikt om te beperken van de totale grootte van gedistribueerde inhoud.
ms.custom: na
ms.date: 2/14/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65c88e54-3574-48b0-a127-9cc914a89dca
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 9e806436f482d2da2ae7d8babc6de3f24cfd80d0
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="the-content-library-in-system-center-configuration-manager"></a>De Inhoudsbibliotheek in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De Inhoudsbibliotheek is een single instance store van inhoud die System Center Configuration Manager gebruikt om te beperken van de totale grootte van alle inhoud die u distribueert. De Inhoudsbibliotheek slaat alle inhoudsbestanden voor software-updates, toepassingen en implementaties van besturingssystemen.

 - Een kopie van de Inhoudsbibliotheek automatisch wordt gemaakt en beheerd op elk **siteserver** en op elk **distributiepunt**.

 - Voordat Configuration Manager inhoudsbestanden naar de siteserver downloadt of de bestanden naar distributiepunten kopieert, Configuration Manager gecontroleerd of elk inhoudsbestand al in de Inhoudsbibliotheek.
 - Als het inhoudsbestand beschikbaar is, wordt Configuration Manager heeft het bestand niet kopiëren en in plaats daarvan koppelt het bestaande inhoudsbestand aan de toepassing of het pakket.

Op computers waarop u een distributiepunt installeert, kunt u het volgende configureren:

- Een of meer schijfstations waarop u wilt maken van de Inhoudsbibliotheek.
- Een prioriteit voor elk station dat u gebruikt.

Wanneer de Configuration Manager inhoudsbestanden kopieert, kopieert deze naar het station met de hoogste prioriteit, totdat dat station minder is dan de minimale hoeveelheid vrije ruimte die u opgeeft.
- U configureert de stationinstellingen tijdens installatie van het distributiepunt.
- U kunt de Stationsinstellingen in de eigenschappen van het distributiepunt niet configureren nadat de installatie is voltooid.


Zie voor meer informatie over het configureren van de Stationsinstellingen voor het distributiepunt [inhoud en infrastructuur voor System Center Configuration Manager beheren](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


>  [!IMPORTANT]  
>  Als u de Inhoudsbibliotheek naar een andere locatie op een distributiepunt na de installatie, gebruikt u de **Content Library Transfer tool** in System Center 2012 R2 Configuration Manager Toolkit. U kunt de werkset downloaden via de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

## <a name="about-the-content-library-on-the-central-administration-site"></a>De Inhoudsbibliotheek op de centrale beheersite  
 Configuration Manager maakt standaard een Inhoudsbibliotheek op de centrale beheersite wanneer de site is geïnstalleerd. De Inhoudsbibliotheek bevindt zich op het station van de siteserver die de meeste vrije schijfruimte heeft. Omdat u niet een distributiepunt op de centrale beheersite installeren, kunt u de stations voor gebruik door de Inhoudsbibliotheek kan geen prioriteit geven. Net als bij de Inhoudsbibliotheek op andere siteservers en op distributiepunten, wanneer het station dat de Inhoudsbibliotheek bevat beschikbare schijfruimte onvoldoende, de Inhoudsbibliotheek automatisch omvat naar het volgende beschikbare station.  

 Configuration Manager gebruikt de Inhoudsbibliotheek op de centrale beheersite in de volgende scenario's:  

-   Wanneer u inhoud maakt op de centrale beheersite.  

-   Wanneer u inhoud migreert van een andere Configuration Manager-site en de centrale beheersite toewijst als de site die die inhoud beheert.  

> [!NOTE]  
>  Wanneer u inhoud op een primaire site maakt en vervolgens naar een andere primaire site of een secundaire site onder een andere primaire site distribueert, de centrale beheersite tijdelijk die inhoud opslaat in de plannerinbox opslaat op de centrale beheersite, maar wordt deze inhoud niet toegevoegd aan de Inhoudsbibliotheek.  

 Gebruik de volgende opties voor het beheren van de Inhoudsbibliotheek op de centrale beheersite:  

-   Om te voorkomen dat de Inhoudsbibliotheek op een specifiek station wordt geïnstalleerd, maakt u een leeg bestand met de naam **no_sms_on_drive.sms**, en vervolgens naar de hoofdmap van het station te kopiëren voordat de Inhoudsbibliotheek wordt gemaakt.  

-   Nadat de Inhoudsbibliotheek is gemaakt, gebruikt u **Content Library Transfer tool** van de System Center 2012 R2 Configuration Manager Toolkit om de locatie van de Inhoudsbibliotheek te beheren. U kunt de werkset downloaden via de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  
