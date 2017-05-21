---
title: Windows Phone-toepassingen maken | Microsoft-documenten
description: Zie welke overwegingen die u moet ondernemen in rekening wanneer u toepassingen maken en voor Windows Phone-apparaten implementeren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe11fa-5fb2-4b81-b0f5-b6f2392fb4ad
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 6cbf2389a72c0c384ef8e84a1755ac77b64bfc6d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-windows-phone-applications-with-system-center-configuration-manager"></a>Windows Phone-toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-toepassing heeft een of meer implementatietypen die deel uitmaken van de installatiebestanden en informatie die nodig zijn voor het implementeren van software voor een apparaat. Een implementatietype bevat ook regels die specificeren waar en hoe de software wordt geïmplementeerd.  

 U kunt toepassingen maken met behulp van de volgende methoden:  

-   De implementatie van toepassingen en -typen automatisch maken via het lezen van de installatiebestanden van de toepassing.  

-   U kunt de toepassing handmatig maken en deze op een later tijdstip aan implementatietypen toevoegen.  

-   Een toepassing importeren uit een bestand.  

Zie [Start de wizard toepassing](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) voor de stappen die nodig zijn voor create Configuration Manager-toepassingen en implementatietypen. Houd ook rekening met het volgende in gedachten wanneer u toepassingen maken en voor Windows Phone-apparaten implementeren.  

## <a name="general-considerations"></a>Algemene overwegingen  
 Configuration Manager ondersteunt de volgende bestandstypen app implementeren:  

|Apparaattype|Ondersteunde bestandstypen|  
|-----------------|---------------------|  
|Windows Phone 8|.xap.|  
|Windows Phone 8,1|.xap, .appx, .appxbundle|
|Windows 10 Mobile|.xap, .appx, .appxbundle|

 De volgende implementatieacties worden ondersteund:  

|Apparaattype|Ondersteunde bewerkingen|  
|-----------------|-----------------------|  
|Windows Phone 8, Windows Phone 8.1 en Windows 10 Mobile|Beschikbaar is, vereist, verwijderen|  

## <a name="steps-to-deploy-the-latest-windows-phone-company-portal-app-with-supersedence"></a>Stappen voor het implementeren van de meest recente Windows Phone-bedrijfsportal-app met vervanging  
 De volgende tabel bevat de stappen, details en meer informatie voor het maken en implementeren van de nieuwste Windows Phone 8-bedrijfsportal-app.  

|Stap|Meer informatie|  
|----------|----------------------|  
|**Stap 1:** Download de meest recente bedrijfsportal-app.|Download de [Windows Intune-bedrijfsportal voor Windows Phone](http://go.microsoft.com/fwlink/?LinkId=268440).|  
|**Stap 2:** De bedrijfsportal-app met uw Symantec-certificaat ondertekenen.|Zie voor meer informatie over het ondertekenen van de bedrijfsportal-app [stellen Windows Phone-en Windows 10 Mobile hybride Apparaatbeheer met System Center Configuration Manager en Microsoft Intune](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**Stap 3:** Maak een nieuwe toepassing met de nieuwste versie van de bedrijfsportal-app en geef een vervangingsrelatie.|Zie voor meer informatie [toepassingen maken](../../apps/deploy-use/create-applications.md) en [herzien en vervangen van toepassingen](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Stap 4:** De toepassing bij de Wizard Microsoft Intune-abonnement toevoegen.|Zie voor meer informatie [stellen Windows Phone-en Windows 10 Mobile hybride Apparaatbeheer met System Center Configuration Manager en Microsoft Intune](../../mdm/deploy-use/enroll-hybrid-windows.md).|  
|**Stap 5:** Verwijder de implementatie die automatisch wordt gemaakt wanneer u de bedrijfsportal-app aan de Wizard Microsoft Intune-abonnement toevoegde.|De Microsoft Intune-abonnement maakte een automatische implementatie van deze app omdat deze implementatie geen vervanging ondersteunt.|  
|**Stap 6:** Maak een nieuwe implementatie van de toepassing. Op de **implementatie-instellingen** pagina van de **Wizard Software implementeren**, Controleer **automatisch upgrade alle vervangen versies van deze toepassing**.|Maak een nieuwe implementatie met vervanging door gebruik te maken van de toepassing die u maakte met de vervangingsrelatie.|  
|**Stap 7 (optioneel):** Standaard de vervangende apps installeren na 7 dagen op apparaten. Voor het implementeren van het bedrijf bedrijfsportal-app sneller om eerder geregistreerde apparaten, wijzigt u de **nieuwe evaluatie voor implementaties plannen** instellen op een lagere waarde.<br /><br /> Als u deze waarde op een lagere waarde dan de standaardwaarde instelt, kan dit de prestaties van uw netwerk en clientcomputers negatief beïnvloeden.|Geen aanvullende informatie.|  

