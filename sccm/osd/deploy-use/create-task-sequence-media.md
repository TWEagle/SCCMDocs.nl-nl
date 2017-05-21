---
title: Takenreeksmedia maken met System Center Configuration Manager | Microsoft-documenten
description: Maken van takenreeksmedia, zoals een CD, een besturingssysteem implementeren op een doelcomputer in uw Configuration Manager-omgeving.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 90498b4b-6a9b-43cd-b465-1d6c9a52df1c
caps.latest.revision: 8
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: bd5448d70c2d465347de840cb197d4c33075c90a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-task-sequence-media-with-system-center-configuration-manager"></a>Takenreeksmedia met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt media gebruiken om vast te leggen van de installatiekopie van een besturingssysteem vanaf een referentiecomputer of een besturingssysteem implementeren op een doelcomputer in uw omgeving voor System Center Configuration Manager. Het kan hierbij gaan om een cd, een dvd-set of een USB-flashstation.  

 Media wordt voornamelijk om besturingssystemen te implementeren op doelcomputers die geen netwerkverbinding of die een lage bandbreedteverbinding met uw Configuration Manager-site hebt gebruikt. Implementatiemedia worden echter ook gebruikt om de implementatie van een besturingssysteem buiten een bestaand Windows-besturingssysteem te starten. Deze tweede toepassing van implementatiemedia is belangrijk wanneer er geen besturingssysteem op de doelcomputer staat, wanneer het besturingssysteem niet werkt of wanneer de gebruiker met beheerdersrechten de harde schijf op de doelcomputer opnieuw wil partitioneren.  

 Implementatiemedia bestaan uit opstartbare media, zelfstandige media en voorbereide media. De inhoud van de implementatiemedia verschilt, afhankelijk van het type media dat u gebruikt. Zo bevatten zelfstandige media bijvoorbeeld de takenreeks waarmee het besturingssysteem wordt geïmplementeerd, terwijl andere mediatypen takenreeksen ophalen van het beheerpunt.  

> [!IMPORTANT]  
>  Takenreeksmedia maken, moet u een beheerder zijn op de computer van waaruit u de Configuration Manager-console. Als u geen beheerder bent, wordt u gevraagd om beheerdersreferenties wanneer u de wizard Takenreeksmedia maken start.  

##  <a name="BKMK_PlanCaptureMedia"></a>Registrerende media voor installatiekopieën van besturingssystemen  
 Met vastlegmedia kunt u vanaf een referentiecomputer de installatiekopie van een besturingssysteem vastleggen. Vastlegmedia bevatten de opstartinstallatiekopie waarmee de referentiecomputer wordt gestart en de takenreeks waarmee de installatiekopie van het besturingssysteem wordt vastgelegd. Zie [Vastlegmedia maken met System Center Configuration Manager](create-capture-media.md) voor meer informatie over het maken van vastlegmedia.  

##  <a name="BKMK_PlanBootableMedia"></a>Implementaties met opstartbare media besturingssysteem  
 Opstartbare media bevatten alleen de opstartinstallatiekopie, optionele [prestart-opdrachten](../understand/prestart-commands-for-task-sequence-media.md) en bijbehorende vereiste bestanden en binaire bestanden van Configuration Manager. Wanneer de doelcomputer wordt gestart, maakt deze verbinding met het netwerk. Vervolgens worden de takenreeks, de installatiekopie van het besturingssysteem en alle andere vereiste inhoud opgehaald van het netwerk. Omdat de takenreeks zich niet op de media bevindt, kunt u de takenreeks of de inhoud wijzigen zonder dat u de media opnieuw hoeft te maken.  

> [!IMPORTANT]  
>  De pakketten op opstartbare media zijn niet versleuteld. De gebruiker met beheerdersrechten moet gepaste beveiligingsmaatregelen nemen (door bijvoorbeeld een wachtwoord in te stellen voor de media) om te waarborgen dat de inhoud van het pakket beveiligd is tegen toegang door onbevoegde gebruikers.  

 Voor informatie over het maken van opstartbare media [opstartbare media maakt](create-bootable-media.md).  

##  <a name="BKMK_PlanPrestagedMedia"></a>Implementaties met voorbereide media besturingssysteem  
 Met voorbereide media kunt u voorafgaand aan het inrichtingsproces opstartbare media en een installatiekopie van een besturingssysteem voorbereiden op een harde schijf. De voorbereide media staat een Windows Imaging Format (WIM)-bestand dat kan worden geïnstalleerd op een bare-metal computer door de fabrikant of in een enterprise-voorbereidingscentrum dat niet is verbonden met de Configuration Manager-omgeving.  

 Voorbereide media bevatten de opstartinstallatiekopie die wordt gebruikt voor het starten van de doelcomputer en de installatiekopie van het besturingssysteem die op de doelcomputer wordt toegepast. U kunt ook toepassingen, pakketten en stuurprogrammapakketten opgeven die moeten worden opgenomen als onderdeel van de voorgefaseerde media. De takenreeks waarmee het besturingssysteem wordt geïmplementeerd, staat niet op de media. Wanneer u een takenreeks implementeert waarvoor voorbereide media worden gebruikt, controleert de client eerst de lokale takenreekscache op geldige inhoud. Als de inhoud niet wordt gevonden of is gewijzigd, wordt deze door de client gedownload vanaf het distributiepunt.  

 Voorbereide media worden toegepast op de harde schijf van een nieuwe computer voordat de computer wordt verzonden naar de eindgebruiker. Wanneer de computer voor het eerst wordt opgestart nadat de voorgefaseerde media zijn toegepast, wordt Windows PE gestart op de computer en wordt er verbinding gemaakt met een beheerpunt om de takenreeks te vinden waarmee het implementatieproces van het besturingssysteem wordt voltooid.  

> [!IMPORTANT]  
>  De pakketten op voorbereide media zijn niet versleuteld. De gebruiker met beheerdersrechten moet gepaste beveiligingsmaatregelen nemen (door bijvoorbeeld een wachtwoord in te stellen voor de media) om te waarborgen dat de inhoud van het pakket beveiligd is tegen toegang door onbevoegde gebruikers.  

 Zie voor meer informatie over het maken van voorbereide media [maken voorbereide media](create-prestaged-media.md).  

##  <a name="BKMK_PlanStandaloneMedia"></a>Implementaties met zelfstandige media-besturingssysteem  
 Zelfstandige media bevatten alles wat u nodig hebt om het besturingssysteem te implementeren, dus ook de takenreeks en alle overige vereiste inhoud. Omdat alles wat u nodig hebt om het besturingssysteem te implementeren wordt opgeslagen op de zelfstandige media, is de benodigde schijfruimte voor zelfstandige media aanzienlijk groter dan de benodigde schijfruimte voor andere mediatypen.  

 Zie voor meer informatie over het maken van zelfstandige media [maken van zelfstandige media](create-stand-alone-media.md).  

## <a name="media-considerations-when-using-site-systems-configured-for-https"></a>Overwegingen voor media bij het gebruik van sitesystemen die zijn geconfigureerd voor HTTPS  
 Wanneer het beheerpunt en de distributiepunten zijn geconfigureerd voor het gebruik van HTTPS-communicatie, moet u opstartmedia en voorbereide media maken op een primaire site, niet op de centrale beheersite. Houd ook rekening met het volgende om te bepalen of de media moeten worden geconfigureerd als dynamisch of op de site gebaseerd:  

-   Als u de media wilt configureren als dynamische media, moeten alle primaire sites de basiscertificeringsinstantie hebben van de site op basis waarvan u de media hebt gemaakt. U kunt de basiscertificeringsinstantie importeren voor alle primaire sites in de hiërarchie.  

-   Wanneer primaire sites in uw Configuration Manager-hiërarchie andere basiscertificeringsinstanties gebruiken, moet u de site gebaseerde media gebruiken op elke site.  

