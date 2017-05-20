---
title: De Inhoudsbibliotheek | Microsoft-documenten
description: Meer informatie over de Inhoudsbibliotheek die System Center Configuration Manager gebruikt om te beperken van de totale grootte van gedistribueerde inhoud.
ms.custom: na
ms.date: 2/14/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65c88e54-3574-48b0-a127-9cc914a89dca
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d31fecdb71b498864df2bce7403a4290ea9700ae
ms.openlocfilehash: 0fa9f431c00476d71b2b08f92f914d76636d1a27
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="the-content-library-in-system-center-configuration-manager"></a>De Inhoudsbibliotheek in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De Inhoudsbibliotheek is een single instance store voor inhoud dat System Center Configuration Manager gebruikt om te beperken van de totale grootte van de gecombineerde hoofdtekst van de inhoud die u distribueert. De Inhoudsbibliotheek slaat alle inhoudsbestanden op voor software-updates, toepassingen en implementaties van besturingssystemen.

 - Een kopie van de Inhoudsbibliotheek automatisch wordt gemaakt en onderhouden op elke **siteserver** en op elke **distributiepunt**.

 - Voordat Configuration Manager inhoudsbestanden naar de siteserver downloadt of de bestanden naar distributiepunten kopieert, Configuration Manager gecontroleerd of elk inhoudsbestand al in de Inhoudsbibliotheek.
 - Als het inhoudsbestand beschikbaar is, wordt Configuration Manager heeft het bestand niet kopiëren en in plaats daarvan wordt het bestaande inhoudsbestand gekoppeld aan de toepassing of het pakket.

Op computers waarop u een distributiepunt installeert, kunt u het volgende configureren:

- Een of meer schijfstations waarop u wilt maken van de Inhoudsbibliotheek.
- De prioriteit voor elke schijf die u gebruikt.

Wanneer Configuration Manager inhoudsbestanden kopieert, kopieert het ze naar het station met de hoogste prioriteit totdat dat station minder dan een minimale hoeveelheid vrije schijfruimte die u opgeeft.
- U configureert de stationinstellingen tijdens de installatie van het distributiepunt.
- U kunt de stuurprogramma-instellingen in eigenschappen van het distributiepunt kan niet configureren nadat de installatie is voltooid.


Zie voor meer informatie over het configureren van de stuurprogramma-instellingen voor het distributiepunt [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


>  [!IMPORTANT]  
>  Gebruiken om de Inhoudsbibliotheek verplaatsen naar een andere locatie op een distributiepunt na de installatie, de **Content Library Transfer tool** in de werkset System Center 2012 R2 Configuration Manager. U kunt de werkset downloaden via de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

## <a name="about-the-content-library-on-the-central-administration-site"></a>Over de Inhoudsbibliotheek op de centrale beheersite  
 Configuration Manager maakt standaard een Inhoudsbibliotheek op de centrale beheersite wanneer de site is geïnstalleerd. De Inhoudsbibliotheek bevindt zich op het station van de siteserver die de meeste vrije schijfruimte heeft. Omdat u een distributiepunt op de centrale beheersite installeren kunt, kan niet u volgorde bepalen van stations voor gebruik door de Inhoudsbibliotheek. Net als de Inhoudsbibliotheek op andere siteservers en distributiepunten, als het station dat de Inhoudsbibliotheek bevat onvoldoende beschikbare schijfruimte, de Inhoudsbibliotheek automatisch over naar het volgende beschikbare station.  

 Configuration Manager gebruikt de Inhoudsbibliotheek op de centrale beheersite in de volgende scenario's:  

-   Wanneer u inhoud maakt op de centrale beheersite.  

-   Wanneer u inhoud migreert van een andere Configuration Manager-site en de centrale beheersite toewijst als de site die inhoud beheert.  

> [!NOTE]  
>  Wanneer u inhoud op een primaire site maakt en hem dan naar een andere primaire site of een secundaire site onder een andere primaire site verdelen, de centrale beheersite bewaart die inhoud tijdelijk in de plannerinbox opslaat op de centrale beheersite maar voegt die inhoud niet aan de Inhoudsbibliotheek.  

 Gebruik de volgende opties om de Inhoudsbibliotheek op de centrale beheersite te beheren:  

-   Om te voorkomen dat de Inhoudsbibliotheek op een specifiek station wordt geïnstalleerd, maakt u een leeg bestand met de naam **no_sms_on_drive.sms**, en kopieer deze naar de hoofdmap van de schijf voordat de Inhoudsbibliotheek wordt gemaakt.  

-   Nadat de Inhoudsbibliotheek is gemaakt, gebruikt u **Content Library Transfer tool** uit de werkset voor het beheren van de locatie van de Inhoudsbibliotheek System Center 2012 R2 Configuration Manager. U kunt de werkset downloaden via de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=279566).  

