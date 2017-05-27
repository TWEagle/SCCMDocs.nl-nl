---
title: De Inhoudsbibliotheek hulpprogramma | Microsoft-documenten
description: Gebruik de Inhoudsbibliotheek hulpprogramma zwevende inhoud niet meer gekoppeld aan een implementatie van System Center Configuration Manager te verwijderen.
ms.custom: na
ms.date: 4/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 226cbbb2-9afa-4e2e-a472-be989c0f0e11
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 32f7fc4ef9c8e8d3c2ec8eeaf9a3174bad992ffb
ms.openlocfilehash: 76e6772bdd5cbd32d525e728f6ebc988b045da78
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="the-content-library-cleanup-tool-for-system-center-configuration-manager"></a>De Inhoudsbibliotheek-hulpprogramma voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Vanaf versie 1702, kunt u een opdrachtregel-hulpprogramma (**ContentLibraryCleanup.exe**) inhoud die is niet meer gekoppeld aan een pakket of toepassing vanuit een distributiepunt te verwijderen (en gaat zweven inhoud). Dit hulpprogramma heet de Inhoudsbibliotheek hulpprogramma en vervangt oudere versies van vergelijkbare hulpmiddelen vrijgegeven voor afgelopen Configuration Manager-producten.  

Het hulpprogramma is alleen van invloed op de inhoud op het distributiepunt dat u opgeeft wanneer u het hulpprogramma uitvoert. Het hulpprogramma verwijderen inhoud van de Inhoudsbibliotheek op de siteserver niet.

U vindt **ContentLibraryCleanup.exe** in de *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* map op de siteserver op een centrale beheersite of primaire site.

## <a name="requirements"></a>Vereisten  
 Het hulpprogramma kan alleen worden uitgevoerd op een enkel distributiepunt tegelijk.  
 - Deze kan rechtstreeks op de computer die fungeert als host voor het distributiepunt dat u wilt reinigen, of op afstand vanaf een andere server uitvoeren.
 - Het gebruikersaccount dat het hulpprogramma uitvoert moet direct op rollen gebaseerd beheer-machtigingen die gelijk aan een volledige beheerder op de Configuration Manager-hiërarchie zijn hebben. Het hulpprogramma werkt niet wanneer het account ontvangt deze machtigingen als lid van een Windows-beveiligingsgroep die de volledige beheerdersrechten heeft.

## <a name="modes-of-operation"></a>Bedrijfsmodi
U kunt het hulpprogramma uitvoeren in de volgende twee modi. We raden u het hulpprogramma uitvoeren in *wat als* zodat u de resultaten bekijken kunt voordat u het hulpprogramma uitvoeren in de modus *modus verwijderen*:
  1.    **Wat als modus**:   
      Als u opgeeft de **/verwijderen** switch en het hulpprogramma wordt uitgevoerd in de modus wat als de inhoud die wordt verwijderd uit het distributiepunt identificeert.
   - Wanneer uitgevoerd in deze modus worden het hulpprogramma niet alle gegevens verwijderd.
   - Informatie over de inhoud die wordt verwijderd, is geschreven naar het logboekbestand van de hulpprogramma's en u niet gevraagd om elke mogelijke verwijdering te bevestigen.  
      </br>   

  2. **Modus verwijderen**:   
    Wanneer u het hulpprogramma uitvoert met de **/verwijderen** switch, het hulpprogramma wordt uitgevoerd in de modus verwijderen.

     - Wanneer in deze modus wordt uitgevoerd, kan zwevende inhoud die is gevonden op de opgegeven distributiepunt worden verwijderd uit het distributiepunt Inhoudsbibliotheek.
     -     Voordat u een bestand te verwijderen, moet u bevestigen dat het bestand moet worden verwijderd.  U kunt selecteren, **Y** Ja, **N** voor Nee, of **Ja op Alles** verdere aanwijzingen overslaan en alle zwevende inhoud verwijderen.  
     </br>

Wanneer het hulpprogramma wordt uitgevoerd in de modus, maakt deze automatisch een logboek met een naam met de modus voor die het hulpprogramma in de naam van het distributiepunt en de datum en tijd van de bewerking wordt uitgevoerd. Het logboekbestand wordt automatisch geopend wanneer het hulpprogramma is voltooid.

Standaard is het logboekbestand worden geschreven naar de tijdelijke map van het gebruikersaccount dat het hulpprogramma uitvoert op de computer waarop het hulpprogramma wordt uitgevoerd. U kunt de **/log** overschakelen naar het logboekbestand omleiden naar een andere locatie, met inbegrip van een netwerkshare.


## <a name="run-the-tool"></a>Het hulpprogramma uitvoeren
Het hulpprogramma uitvoeren:
1. Open een beheeropdrachtprompt naar een map met **ContentLibraryCleanup.exe**.  
2. Voer vervolgens een opdrachtregel te gebruiken dat de vereiste opdrachtregelparameters en schakelopties die u wilt gebruiken.

**Bekende probleem** wanneer het hulpprogramma wordt uitgevoerd, een fout als volgt kan worden geretourneerd als een pakket of de implementatie is mislukt of uitgevoerd wordt:
-  *System.InvalidOperationException: Deze Inhoudsbibliotheek kan niet worden opgeruimd nu omdat pakket <packageID> is niet volledig geïnstalleerd.*

**Tijdelijke oplossing:** Geen. Het hulpprogramma kan geen betrouwbare zwevende bestanden identificeren wanneer inhoud uitgevoerd wordt of is niet is geïmplementeerd. Daarom kunt het hulpprogramma u niet opschonen inhoud totdat dit probleem opgelost is.

### <a name="command-line-switches"></a>Opdrachtregelparameters  
De volgende opdrachtregelopties kunnen worden gebruikt in een willekeurige volgorde.   

|Switch|Details|
|---------|-------|
|**/ Delete**  |**Optionele** </br> Gebruik deze switch als u inhoud wilt verwijderen uit het distributiepunt. U wordt gevraagd voordat inhoud wordt verwijderd. </br></br> Wanneer deze schakeloptie niet wordt gebruikt, registreert het hulpprogramma resultaten over welke inhoud wordt verwijderd, maar wordt de inhoud niet verwijderd uit het distributiepunt. </br></br> Voorbeeld: ***/ Delete ContentLibraryCleanup.exe /dp server1.contoso.com*** |
| **/q**       |**Optionele** </br> Deze switch wordt het hulpprogramma uitvoert in een stille modus onderdrukt alle vragen (zoals de prompts inhoud verwijderen) en het logboekbestand niet automatisch openen. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;distribution point FQDN >**  | **Vereist** </br> Geef de volledig gekwalificeerde domeinnaam (FQDN) van het distributiepunt dat u wilt reinigen. </br></br> Voorbeeld:  ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/PS &lt;primaire site FQDN-naam >**       | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br>Het hulpprogramma maakt verbinding met de bovenliggende primaire site voor het uitvoeren van query's tegen SMS_Provider. Deze query's kunt het hulpprogramma bepalen welke inhoud kan worden op het distributiepunt zodat deze kan herkennen de inhoud die is zwevend en kan worden verwijderd. Deze verbinding naar de bovenliggende primaire site moet worden gemaakt voor distributiepunten op een secundaire site omdat de vereiste gegevens rechtstreeks vanaf de secundaire site niet beschikbaar zijn.</br></br> Geef de FQDN van de primaire site die deel uitmaakt van het distributiepunt naar of van de bovenliggende primaire bovenliggende wanneer het distributiepunt zich op een secundaire site. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;primaire sitecode >**  | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br> Geef de sitecode van de primaire site die deel uitmaakt van het distributiepunt naar of van de bovenliggende primaire site wanneer het distributiepunt zich op een secundaire site.</br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Optionele** </br> Geef de locatie waar het hulpprogramma voor het logboekbestand schrijft. Dit kan een lokaal station of een netwerkshare.</br></br> Wanneer deze schakeloptie niet wordt gebruikt, wordt het logboekbestand geplaatst in de map temp van de gebruiker op de computer waarop het hulpprogramma wordt uitgevoerd.</br></br> Voorbeeld van een lokale schijf: ***ContentLibraryCleanup.exe /dp server1.contoso.com/log C:\Users\Administrator\Desktop*** </br></br>Voorbeeld van een netwerkshare: ***/ Log ContentLibraryCleanup.exe /dp server1.contoso.com \\ &lt;delen >\&lt; map >***|

