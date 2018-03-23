---
title: Meer informatie over de beveiliging van de PowerShell-script
titleSuffix: System Center Configuration Manager
description: Bronnen voor hulp bij de informatie over de beveiliging van PowerShell-script.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0bd093d-67a5-4f74-bf79-dd604889f5ba
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 48b3dd53ce8df097e355908237111f0d586ddd06
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="learn-more-about-powershell-script-security"></a>Meer informatie over de beveiliging van de PowerShell-script

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Het is de verantwoordelijkheid van de beheerder om te valideren voorgestelde PowerShell en PowerShell gebruik van parameters in hun omgeving. Hier volgen enkele nuttige informatiebronnen op uw opleiden beheerders over de kracht van PowerShell en potentiële risico's bevat. Dit is het mogelijke risico verwerkingsinformatie beperken en veilige scripts kunnen worden gebruikt.

## <a name="powershell-script-security"></a>Beveiliging van de PowerShell-Script
Ingebouwd in de Scripts worden uitgevoerd, is een functie visueel controleren en goedkeuren van scripts die worden aangevraagd om te worden uitgevoerd in de omgeving. Beheerders rekening moet houden PowerShell-scripts kunnen script hebt verborgen: script schadelijke en moeilijk te detecteren met visuele inspectie tijdens het goedkeuringsproces script. Als een best practice, met bepaalde inspectie's, in extra's worden visueel controleren PowerShell-scripts, helpt u verdachte scripts problemen detecteren. Deze hulpprogramma's kunnen niet de bedoeling van de auteur van de PowerShell altijd bepalen zodat deze aandacht aan een verdachte script kunt brengen. De hulpprogramma's vereisen echter de beheerder om te beoordelen of het script schadelijke of opzettelijk syntaxis is.

## <a name="recommendations"></a>Aanbevelingen
- Maak uzelf bekend met PowerShell best practices voor beveiliging met behulp van de verschillende koppelingen waarnaar wordt verwezen hieronder.
- **Meld u aan uw scripts**: Een andere methode voor het bewaren van scripts Secure is door ze zijn goedgekeurd en vervolgens ondertekend voordat u ze importeert voor gebruik.
- Geen geheimen (zoals wachtwoorden) opslaan in PowerShell-scripts en meer informatie over het afhandelen van geheimen.


## <a name="general-information-about-powershell-security-best-practices"></a>Algemene informatie over aanbevolen beveiligingsprocedures voor PowerShell

Deze verzameling van koppelingen is geven Configuration Manager-beheerders een beginpunt voor meer informatie over aanbevolen procedures voor beveiliging PowerShell-script gekozen.  

[Inleiding tot aanbevolen beveiligingsprocedures voor PowerShell](https://blogs.msdn.microsoft.com/powershell/2013/12/16/powershell-security-best-practices/ )

[PowerShell Security Best Practices PowerPoint](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/63/74/metablogapi/1055.PowerShell-Security-Best-Practices_3CA24C32.pptx)

<iframe src="https://channel9.msdn.com/Events/Blue-Hat-Security-Briefings/BlueHat-Security-Briefings-Fall-2013-Sessions/PowerShell-Best-Practices/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

[Defending tegen PowerShell-aanvallen, PowerShell-teamblog](https://blogs.msdn.microsoft.com/powershell/2017/10/23/defending-against-powershell-attacks/)

[Defending tegen aanvallen PowerShell twitter, via een Microsoft PowerShell en beveiliging pleiten Lee Holmes](https://twitter.com/Lee_Holmes/status/922462821081694208)

[Bescherming tegen schadelijke Code kan worden ingevoegd](https://blogs.msdn.microsoft.com/powershell/2006/11/22/protecting-against-malicious-code-injection/)

[Informatie over de beveiliging van de PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2015/08/06/powershell-gallery-new-security-scan/)

[De blauwe Team PowerShell, komen aan bod grondige scriptblok logboekregistratie logboekregistratie beveiligd, anti-malware Scan Interface, API's voor Secure Code genereren](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

[Voor Windows 10 is een API voor een anti-malware scan-interface](https://cloudblogs.microsoft.com/microsoftsecure/2015/06/09/windows-10-to-offer-application-developers-new-malware-defenses/?source=mmpc)

## <a name="powershell-parameters-security"></a>Beveiliging van PowerShell-parameters
Parameters doorgeven is een manier om flexibiliteit met uw scripts hebt en beslissingen uitstellen tot uitvoering. Ook wordt geopend om een andere risico op aanvallen. Aanbevolen procedures voor het voorkomen dat schadelijke parameters of script injectie zijn:

- Kan alleen informatie over het gebruik van vooraf gedefinieerde parameters.
- Gebruik de functie reguliere expressie voor het valideren van de parameters die zijn toegestaan.
    - Voorbeeld: Als er slechts een bepaald bereik van waarden zijn toegestaan, moet u een reguliere expressie gebruiken om te controleren op alleen de tekens of waarden kunnen het bereik.
    - Valideren van parameters kunt voorkomen dat gebruikers bij gebruik van bepaalde tekens die worden escape-, zoals aanhalingstekens teken kunnen. Houd er rekening mee dat er meerdere typen aanhalingstekens, met behulp van reguliere expressies te valideren die u hebt besloten zijn toegestane tekens is vaak eenvoudiger dan probeert te definiëren van de invoer kan zijn dat niet is toegestaan.
- Gebruikmaken van de PowerShell-module ['injectie hunter'](https://www.powershellgallery.com/packages/InjectionHunter/1.0.0) in de PowerShell-galerie.
    - Er kunnen worden valse positieven, dus zoeken voor de bedoeling als er iets is gemarkeerd als verdacht zijn om te bepalen of het is een probleem met de echte niet. 
- Microsoft Visual Studio is een Script analyzer, die helpen kan bij het controleren van de PowerShell-syntaxis.
- In deze video met de titel: "DEF CON 25 - Lee Holmes - $pwnd ophalen: Een aanval strijd geharde WindowsServer' geeft een overzicht van het soort problemen die u tegen (met name de sectie 12:20 tot 17:50 beveiligen kunt):     <iframe width="560" height="315" src="https://www.youtube.com/embed/ahxMOAAani8" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="environment-recommendations"></a>Omgeving aanbevelingen
Algemene aanbevelingen voor de PowerShell-beheerders.
1. Meest recente versie van PowerShell, zoals versie 5 of hoger, implementeren ingebouwd in Windows 10. U kunt ook de [Windows Management Framework](https://www.microsoft.com/en-us/download/details.aspx?id=54616), beschikbaar omlaag tot en met Windows 7 en Windows Server 2008 R2. 
2. Schakel en verzamelen van Logboeken van PowerShell, eventueel met inbegrip van logboekregistratie beveiligd. Deze logboeken opnemen in uw handtekeningen, zoeken en werkstromen voor respons op incidenten.
3. Net genoeg beheer implementeren op hoogwaardige systemen te trekken of beperken van onbeperkte beheerderstoegang tot deze systemen.
4. Device Guard/toepassing beleid implementeren zodat de vooraf geselecteerde administratieve taken voor de volledige capaciteit van de PowerShell-taal, interactieve en niet-goedgekeurde gebruiken om een beperkte subset van de PowerShell-taal te beperken.
5. Implementeer Windows 10 zodat uw antivirus provider volledige toegang tot alle inhoud (inclusief inhoud gegenereerde of ongedaan verborgen op runtime) wordt verwerkt door Windows Scripting-Hosts met inbegrip van PowerShell.