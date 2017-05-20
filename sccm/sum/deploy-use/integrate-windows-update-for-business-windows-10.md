---

title: Integratie met Windows Update voor bedrijven in Windows 10 | Microsoft-documenten
description: Gebruik Windows Update voor bedrijven voor Windows 10-apparaten in uw organisatie up-to-date te houden voor apparaten die zijn verbonden met de Windows Update-service.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 8bdbacd54632475ac69a0d0a9a34b2567c3daa13
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Integratie met Windows Update voor bedrijven in Windows 10

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met Windows Update voor bedrijven (WUfB) kunt u Windows 10-apparaten in uw organisatie altijd up-to-date te houden met de meest recente beveiligingen en Windows-onderdelen wanneer deze apparaten rechtstreeks verbinding maken met de service Windows Update (WU). Configuration Manager heeft de mogelijkheid onderscheid maken tussen Windows 10-computers die gebruikmaken van WUfB en WSUS bij het ophalen van software-updates.  

 Sommige Configuration Manager-functies zijn niet langer beschikbaar wanneer de Configuration Manager-clients zijn geconfigureerd om updates te ontvangen van WU, waaronder WUfB of Windows Insiders:  

-   Windows Update-nalevingsrapportages:  

    -   Configuration Manager worden niet op de hoogte van de updates die worden gepubliceerd naar WU. De Configuration Manager-clients die is geconfigureerd voor updates ontvangen van WU worden weergegeven **onbekende** voor deze updates in de Configuration Manager-console.  

    -   Het oplossen van problemen met de algehele compatibiliteitsstatus is lastig, omdat de status **Onbekend** voorheen alleen werd gebruikt voor clients waarvoor de scanstatus van WSUS niet was gerapporteerd.  Nu bevat ook Configuration Manager-clients die updates van WU heeft ontvangen.  

    -   Voorwaardelijke toegang (voor bedrijfsbronnen) op basis van status van de Updatevereisten werkt niet zoals verwacht voor clients die updates van WU ontvangen omdat zou nooit voldoen aan de naleving van Configuration Manager.  

    -   Compatibiliteit met definitie-updates maakt deel uit van de algehele rapportage voor updatecompatibiliteit en werkt ook niet zoals verwacht.  Compatibiliteit met definitie-updates maakt ook deel uit van de evaluatie voor voorwaardelijke toegang  

-   Algehele rapportage van Endpoint Protection voor Defender op basis van nalevingsstatus van updates retourneert geen nauwkeurige resultaten vanwege de ontbrekende scangegevens.  

-   Configuration Manager pas weer voor het implementeren van updates voor Microsoft, zoals Office, Internet Explorer en Visual Studio op clients die zijn verbonden met WUfB om updates te ontvangen.  

-   Configuration Manager pas weer voor het implementeren van 3e partij updates die zijn gepubliceerd in WSUS en worden beheerd via Configuration Manager-clients die zijn verbonden met WUfB om updates te ontvangen.  

-   Configuration Manager volledige clientimplementatie die gebruikmaakt van de infrastructuur van het software-updates werken niet voor clients die zijn verbonden met WUfB om updates te ontvangen.  

## <a name="identify-clients-that-use--wufb-for-windows-10-updates"></a>Clients identificeren die gebruikmaken van WUfB voor Windows 10-updates  
 Gebruik de volgende procedure om clients te identificeren die gebruikmaken van WUfB voor het ophalen van Windows 10-updates, deze clients zo te configureren dat ze WSUS niet meer gebruiken om updates op te halen, en een instelling voor de clientagent te implementeren om de werkstroom voor software-updates voor deze clients te uit te schakelen.  

 **Vereisten**  

-   Clients met Windows 10 Desktop Pro of Windows 10 Enterprise Edition versie 1511 of hoger  

-   [Windows Update voor bedrijven](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) wordt geïmplementeerd en clients gebruiken WUfB om Windows 10-updates en -upgrades op te halen.  

#### <a name="to-identify-clients-that-use-wufb"></a>Clients identificeren die gebruikmaken van WUfB  

1.  Schakel de Windows Update Agent uit zodat deze niet scant ten opzichte van WSUS als deze eerder werd ingeschakeld.   
    De registersleutel **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer** kunnen worden ingesteld om aan te geven of de computer wordt gescand tegen WSUS of Windows Update.  Wanneer de waarde 2 is, wordt het niet scannen met WSUS.  

2.  Er is een nieuw kenmerk **UseWUServer**onder de **Windows Update** knooppunt in de Configuration Manager Resource Explorer.  

3.  Maak een verzameling op basis van het **UseWUServer** -kenmerk voor alle computers die via WUfB zijn verbonden voor updates en upgrades.  

4.  Maak een clientagentinstelling voor het uitschakelen van de werkstroom voor software-updates en pas de instelling toe op de verzameling van computers die rechtstreeks zijn verbonden met WUfB.  

5.  De computers die worden beheerd via WUfB worden weergegeven **onbekende** in de status van naleving en won't worden geteld als onderdeel van het algehele compatibiliteitspercentage.  

