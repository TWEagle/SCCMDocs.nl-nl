---
title: Windows Embedded toepassingen maken | Microsoft-documenten
description: Zie welke overwegingen die u moet ondernemen in rekening wanneer u toepassingen maken en voor Windows Embedded-apparaten implementeren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16acfd63-0c40-424c-82f4-8c63f7f1c30b
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 557888d1f1f899e3198c430bbe5ccdd44178f824
ms.openlocfilehash: cb0c22f3060ba654778dca958d620f1e1725b93c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-windows-embedded-applications-with-system-center-configuration-manager"></a>Windows Embedded toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Naast de andere vereisten voor System Center Configuration Manager en procedures voor het maken van een toepassing, moet u ook rekening met het volgende in aanmerking nemen wanneer u toepassingen maken en voor Windows Embedded-apparaten implementeren.  

## <a name="general-considerations"></a>Algemene overwegingen  

-   Wanneer u toepassingen voor Windows Embedded-apparaten die zijn ingeschakeld implementeert voor het filteren van schrijven, kunt u opgeven of het schrijffilter op het apparaat tijdens de implementatie van de app uitschakelen. U kunt vervolgens de schrijffilter na implementatie van de app opnieuw te starten. Als het schrijffilter niet wordt uitgeschakeld, wordt de software geïmplementeerd op een tijdelijke overlay. Dit betekent dat tenzij een andere implementatie afdwingt wijzigingen om vast te leggen dat, de software wordt niet meer geïnstalleerd wanneer het apparaat opnieuw wordt opgestart.  

-   Wanneer u een toepassing implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster. U kunt op deze manier beheren wanneer het schrijffilter is uitgeschakeld en ingeschakeld en wanneer het apparaat opnieuw wordt gestart.  

-   De instelling die het gedrag van het schrijffilter bepaalt, is het selectievakje **wijzigingen doorvoeren bij deadline of tijdens onderhoud (opnieuw opstarten noodzakelijk)**.  

## <a name="tips-for-deploying-applications"></a>Tips voor het implementeren van toepassingen  

**Gebruik vereiste toepassingen in plaats van beschikbare toepassingen voor Windows Embedded-apparaten waarvoor schrijffilters zijn ingeschakeld.** Omdat gebruikers geen apps vanuit Software Center op een Windows Embedded-apparaat waarop schrijffilters zijn ingeschakeld installeren, implementeert u altijd toepassingen met een implementatiedoel van **vereist** plaats **beschikbaar** op deze apparaten. Doorgaans is dit een probleem niet omdat op computers waarop een Windows Embedded-besturingssysteem vaak een enkele toepassing die moet worden uitgevoerd op dezelfde manier voor meerdere gebruikers worden uitgevoerd. Daarom worden deze apparaten in hoge mate beheerd en vergrendeld door de IT-afdeling. Vereiste toepassingen zijn geschikt voor dit scenario.

 Als gebruikers echter wel meer dan één toepassing uitvoeren op Embedded-apparaten wanneer schrijffilters zijn ingeschakeld, moet u deze gebruikers informeren over de volgende beperkingen:  

-   Gebruikers kunnen geen vereiste software installeren vanuit Software Center.  

-   Gebruikers kunnen hun kantooruren niet wijzigen op het tabblad Opties van Software Center.  

-   Gebruikers kunnen de installatie van een vereiste toepassing niet uitstellen.  

Bovendien aanmelden gebruikers met beperkte rechten niet tijdens een onderhoudsperiode als Configuration Manager wijzigingen voor software-installaties en updates doorvoert. Gedurende deze periode krijgen gebruikers een bericht te zien met de melding dat het apparaat niet beschikbaar is omdat het wordt onderhouden.  

**Implementeer geen toepassingen op Windows Embedded-apparaten waarvoor schrijffilters zijn ingeschakeld als de toepassingen moet de gebruiker de licentievoorwaarden te accepteren.** Wanneer write filters zijn uitgeschakeld zodat dat Configuration Manager software kan installeren op embedded-apparaten, kunnen gebruikers met beperkte rechten zich niet aanmelden op het apparaat. Als het voor de installatie vereist is dat de gebruiker de licentievoorwaarden accepteert, is dit niet mogelijk en zal de installatie dus mislukken. Zorg dat u geen software op Windows Embedded-apparaten implementeert als voor de installatie gebruikersinteractie vereist is. U kun de lijst Toepasselijke platforms gebruiken om deze besturingssystemen te filteren.  

