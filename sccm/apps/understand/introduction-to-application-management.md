---
title: Inleiding op Toepassingsbeheer | Microsoft-documenten
description: Ontdek de algemene informatie die u wilt beheren en implementeren van toepassingen van System Center Configuration Manager.
ms.custom: na
ms.date: 12/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08f711ba-83bf-4b5f-9520-a0778c6ae7eb
caps.latest.revision: 18
author: robstackmsft
ms.author: robstack
manager: angrobe
experimental: true
experiment_id: rob-table-161101
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5aef08865b232ff2dacec6906098bebf4e42e6b1
ms.openlocfilehash: 699adb5fac0c625c321db011af6989cc4c0778ec
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-application-management-in-system-center-configuration-manager"></a>Inleiding op Toepassingsbeheer in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp wordt uitgelegd hoe die u weten moet voordat u begint te werken met System Center Configuration Manager-toepassingen.  

> [!TIP]  
>  Als u al bekend met het beheren van toepassingen in Configuration Manager bent, kunt u dit onderwerp overslaan en gaat u verder met het maken van een voorbeeld van toepassing. Zie [Een toepassing maken en implementeren met System Center Configuration Manager](../../apps/get-started/create-and-deploy-an-application.md).  

## <a name="what-is-an-application"></a>Wat is een toepassing?  
 Hoewel *toepassing* is een veelgebruikte term bij computers in Configuration Manager, betekent dit dat een ander. U kunt een toepassing zien als een doos. Dit vak bevat een of meer sets van installatiebestanden voor een softwarepakket (ook wel een **implementatietype**), plus instructies over het implementeren van de software.  

 Wanneer de toepassing wordt geïmplementeerd naar apparaten, wordt op basis van **vereisten** bepaald welk implementatietype op het apparaat wordt geïnstalleerd.  

 U kunt uiteraard veel meer met een toepassing doen. Al deze mogelijkheden komen aan bod in deze handleiding. De volgende tabel bevat enkele concepten die u moet weten voordat u zich verder in dit onderwerp verdiept. Niet al deze concepten worden toegepast in elke toepassing die u maakt:  

|Concept|Beschrijving|    
|-|-|  
|**Requirements**|In eerdere versies van Configuration Manager, moet u vaak een verzameling met de apparaten die u wilt implementeren van een toepassing te maken. Hoewel u dit nog steeds kunt doen, is dit niet meer echt nodig doordat u veel gedetailleerdere criteria kunt opgeven voor de installatie van een toepassing.<br /><br /> U kunt bijvoorbeeld opgeven dat een toepassing alleen mag worden geïnstalleerd op apparaten met Windows 10. Vervolgens kunt u de toepassing naar al uw apparaten implementeren, maar wordt deze alleen geïnstalleerd op apparaten met Windows 10.<br /><br /> Configuration Manager evalueert vereisten om te bepalen of een toepassing en een van de implementatietypen ervan zal worden geïnstalleerd. Vervolgens bepaalt de client het juiste implementatietype waarmee een installatie moet worden geïnstalleerd. Standaard worden de regels voor vereisten elke zeven dagen opnieuw geëvalueerd om de compatibiliteit te garanderen volgens de clientinstelling **Nieuwe evaluatie voor implementaties plannen**.<br /><br /> Zie voor meer informatie, [maken en implementeren van een toepassing](../../apps/get-started/create-and-deploy-an-application.md).|  
|**Globale voorwaarden**|Terwijl de vereisten met een specifiek implementatietype in een enkele toepassing worden gebruikt, kunt u ook globale voorwaarden maken. Dit zijn een bibliotheek met vooraf gedefinieerde vereisten die u met een toepassing en een implementatietype gebruiken kunt.<br /><br /> Configuration Manager bevat een aantal ingebouwde globale voorwaarden en u kunt ook uw eigen maken.<br /><br /> Zie voor meer informatie, [globale voorwaarden maken](../../apps/deploy-use/create-global-conditions.md).|  
|**Gesimuleerde implementatie**|Evalueert de vereisten, detectiemethode en afhankelijkheden voor een toepassing. De resultaten worden ook vermeld zonder de toepassing daadwerkelijk te installeren.<br /><br /> Zie voor meer informatie, [toepassingsimplementaties simuleren](../../apps/deploy-use/simulate-application-deployments.md).|  
|**Implementatieactie**|Hiermee geeft u op of u wilt installeren of verwijderen (indien ondersteund), de toepassing die u implementeert.<br /><br /> Zie voor meer informatie, [toepassingen implementeren](../../apps/deploy-use/deploy-applications.md).|  
|**Implementatiedoel**|Hiermee geeft u aan of de implementatie-app **Vereist**of **Beschikbaar**is.<br /><br /> **Vereist** betekent dat de toepassing is automatisch geïmplementeerd volgens de planning die is ingesteld. Een gebruiker kan evenwel de status van de implementatie van de toepassing traceren indien hij niet verborgen is en kan de toepassing installeren vóór de deadline door gebruik te maken van het Software Center.<br /><br /> **Beschikbaar** betekent dat als de toepassing voor een gebruiker wordt geïmplementeerd, de gebruiker de gepubliceerde toepassing in Software Center kan zien en hij of zij deze op verzoek kan installeren.<br /><br /> Zie voor meer informatie, [toepassingen implementeren](../../apps/deploy-use/deploy-applications.md).|  
|**Revisies**|Wanneer u wijzigingen aanbrengt in een toepassing of een implementatietype dat is opgenomen in een toepassing, maakt Configuration Manager een nieuwe versie van de toepassing. U kunt de geschiedenis van elke toepassingsrevisie weergeven, de eigenschappen bekijken, een eerdere versie van een toepassing herstellen of een oudere versie verwijderen.<br /><br /> Zie voor meer informatie, [updates en toepassingen buiten gebruik stellen](../../apps/deploy-use/update-and-retire-applications.md).|  
|**Detectiemethode**|Detectiemethoden worden gebruikt om te detecteren of een geïmplementeerde toepassing al is geïnstalleerd. Als de detectiemethode geeft aan dat de toepassing wordt geïnstalleerd dat, probeert Configuration Manager niet nogmaals te installeren.<br /><br /> Zie voor meer informatie, [toepassingen maken](../../apps/deploy-use/create-applications.md).|  
|**Afhankelijkheden**|Afhankelijkheden definiëren een of meer implementatietypen van een andere toepassing die moeten worden geïnstalleerd voordat het implementatietype wordt geïnstalleerd. U kunt de afhankelijke implementatietypen automatisch moeten worden geïnstalleerd voordat een implementatietype wordt geïnstalleerd instellen.<br /><br /> Zie voor meer informatie, [toepassingen maken](../../apps/deploy-use/create-applications.md).|  
|**Vervanging**|Configuration Manager kunt u toepassingen upgraden of vervangen bestaande door een vervangingsrelatie te gebruiken. Wanneer u een toepassing vervangt, kunt u een nieuw implementatietype ter vervanging van het implementatietype van de vervangen toepassing opgeven. U kunt ook bepalen of wilt upgraden of verwijderen van de vervangen toepassing voordat de vervangende toepassing wordt geïnstalleerd.<br /><br /> Zie voor meer informatie, [toepassingen maken](../../apps/deploy-use/create-applications.md).|  
|**Op de gebruiker gericht beheer**|Configuration Manager-toepassingen ondersteunen de gebruiker gericht beheer, zodat u specifieke gebruikers aan specifieke apparaten koppelen. U hoeft de naam van een apparaat van een gebruiker niet te herinneren. U kunt de apps implementeren voor de gebruiker en voor het apparaat. Met deze functie kunt u ervoor zorgen dat de belangrijkste apps altijd beschikbaar zijn op elk apparaat dat een specifieke gebruiker gebruikt. Als een gebruiker een nieuwe computer, kunt u apps van de gebruiker automatisch installeren op het apparaat voordat ze zich aanmelden.<br /><br /> Zie voor meer informatie, [koppelen van gebruikers en apparaten met gebruikersapparaataffiniteit](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).|  

## <a name="what-application-types-can-you-deploy"></a>Welke toepassingstypen kunt u implementeren?  
 Configuration Manager kunt u de volgende typen app implementeren:  

- Windows Installer (*.msi file)
- Windows app-pakket (*.appx, *.appxbundle)
- Windows-app-pakket (in de Windows Store)
- Microsoft Application Virtualization 4
- Microsoft Application Virtualization 5
- Windows Mobile-cabinet
- Mac OS  


Wanneer u apparaten via Microsoft Intune beheren of Configuration Manager on-premises Apparaatbeheer, kunt u bovendien deze verdere app typen beheren:

- Windows Phone-app-pakket (XAP-bestand)
- App-pakket voor iOS (*.ipa-bestand)
- App-pakket voor Android (*.apk-bestand)
- App-pakket voor Android in Google Play
- Windows Phone-app-pakket (in de Windows Phone Store)
- Windows Installer via MDM
- Webtoepassing



## <a name="state-based-applications"></a>Toepassingen op basis van status  
 Configuration Manager-toepassingen gebruiken bewaking op basis van status, zodat u de laatste implementatiestatus van toepassing voor gebruikers en apparaten kunt bijhouden. In deze statusberichten wordt informatie over afzonderlijke apparaten weergegeven. Als een toepassing wordt geïmplementeerd voor een verzameling gebruikers, kunt u de compatibiliteitsstatus van de implementatie en het implementatiedoel weergeven in de Configuration Manager-console. U kunt de implementatie van alle software bewaken met behulp van de **bewaking** werkruimte in de Configuration Manager-console. Software-implementaties omvatten software-updates, compatibiliteitsinstellingen, toepassingen, takenreeksen, pakketten en programma's. Zie voor meer informatie [-toepassingen bewaken](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Implementaties van toepassingen worden regelmatig opnieuw geëvalueerd door Configuration Manager. Bijvoorbeeld:  

-   Een geïmplementeerde toepassing wordt verwijderd door de eindgebruiker. Bij de volgende beoordelingscyclus detecteert Configuration Manager dat de toepassing niet aanwezig is en installeert het opnieuw.  

-   Een toepassing werd niet geïnstalleerd op een apparaat omdat het niet voldeed aan de vereisten. Vervolgens wordt het apparaat gewijzigd en voldoet het aan de vereisten. Configuration Manager detecteert deze wijziging en de toepassing wordt geïnstalleerd.  


 U kunt het interval voor nieuwe evaluatie voor implementaties van toepassingen instellen met behulp van de **nieuwe evaluatie voor implementaties plannen** client-instelling. Zie voor meer informatie [over clientinstellingen](../../core/clients/deploy/about-client-settings.md).  

## <a name="get-started-creating-an-application"></a>Een toepassing maken  
 Als u wilt meedoen en beginnen met het maken van een toepassing, vindt u een overzicht voor het maken van een eenvoudige toepassing in de [maken en implementeren van een toepassing](../../apps/get-started/create-and-deploy-an-application.md) onderwerp.  

 Als u bekend met de basisbeginselen bent en zoeken naar meer informatie over de opties die zijn beschikbaar gedetailleerde, vanuit starten [toepassingen maken](/sccm/apps/deploy-use/create-applications).  

## <a name="software-center-and-the-application-catalog"></a>Software Center en Application Catalog  
 In eerdere versies van Configuration Manager is Software Center gebruikt om te installeren en plannen van software-installaties, instellingen voor extern beheer configureren, en energiebeheer instellen. Gebruikers kunnen verbinding maken met de Application Catalog kunnen zoeken en software kunnen aanvragen, bepaalde voorkeursinstellingen en hun mobiele apparaten op afstand te wissen.  

 Hoewel deze instellingen nog steeds beschikbaar in System Center Configuration Manager worden, een nieuwe versie van het Software Center is nu beschikbaar waarmee u bladeren door toepassingen. U hoeft niet te gebruiken van de Application Catalog, wat een browser ingeschakeld voor Silverlight vereist. De sitesysteemrollen voor het Application Catalog-websitepunt en het Application Catalog-webservicepunt zijn echter nog wel vereist om ervoor te zorgen dat voor gebruikers beschikbare apps worden weergegeven in Software Center.  

 Zie voor meer informatie [plannen en configureren van Toepassingsbeheer](../../apps/plan-design/plan-for-and-configure-application-management.md).  

## <a name="configuration-manager-packages-and-programs"></a>Configuration Manager-pakketten en programma 's  
 Configuration Manager blijft ondersteuning bieden voor pakketten en programma's die werden gebruikt in eerdere versies van het product. Een implementatie die pakketten en programma's gebruikt is mogelijk beter geschikt dan een implementatie die een toepassing gebruikt wanneer u het volgende implementeert:  

-   Scripts die niet worden gebruikt voor het installeren van een toepassing op een computer, zoals een script voor het defragmenteren van het schijfstation van de computer.  

-   'Eenmalige' scripts die niet voortdurend hoeven te worden bewaakt.  

-   Scripts die worden uitgevoerd volgens een herhaalde planning en die geen gebruik kunnen maken van globale evaluatie.

 Zie voor meer informatie [pakketten en programma's](../../apps/deploy-use/packages-and-programs.md).  

