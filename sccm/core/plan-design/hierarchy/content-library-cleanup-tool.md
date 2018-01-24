---
title: De Inhoudsbibliotheek opschoonprogramma
titleSuffix: Configuration Manager
description: Gebruik het hulpprogramma Inhoudsbibliotheek opruimen zwevende inhoud niet meer gekoppeld aan een implementatie van System Center Configuration Manager te verwijderen.
ms.custom: na
ms.date: 4/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 226cbbb2-9afa-4e2e-a472-be989c0f0e11
caps.latest.revision: "4"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 334b79e675ea7804128b0feb9678de4ad06dbc93
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="the-content-library-cleanup-tool-for-system-center-configuration-manager"></a>De Inhoudsbibliotheek opschoonprogramma voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Vanaf versie 1702, kunt u een opdrachtregel-hulpprogramma (**ContentLibraryCleanup.exe**) inhoud die niet meer is gekoppeld aan een pakket of toepassing van een distributiepunt te verwijderen (en gaat zweven inhoud). Dit hulpprogramma heet de Inhoudsbibliotheek opschoonprogramma en vervangt oudere versies van vergelijkbare hulpmiddelen uitgebracht voor afgelopen Configuration Manager-producten.  

Het hulpprogramma is alleen van invloed op de inhoud op het distributiepunt dat u opgeeft wanneer u het hulpprogramma uitvoert. Inhoud van het hulpprogramma niet verwijderen uit de Inhoudsbibliotheek op de siteserver.

U vindt **ContentLibraryCleanup.exe** in de \*%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* map op de siteserver op een centrale beheersite of primaire site.

## <a name="requirements"></a>Vereisten  
 Het hulpprogramma kan alleen worden uitgevoerd voor één distributiepunt tegelijk.  
 - Het kunt rechtstreeks op de computer die als host fungeert voor het distributiepunt dat u wilt opruimen of extern vanaf een andere server uitvoeren.
 - Het gebruikersaccount dat het hulpprogramma uitvoert, moet direct op rollen gebaseerd beheer-machtigingen die gelijk aan een volledige beheerder op de Configuration Manager-hiërarchie zijn hebben. De tool werkt niet wanneer het account ontvangt deze machtigingen als lid van een Windows-beveiligingsgroep die de volledige beheerdersrechten heeft.

## <a name="modes-of-operation"></a>Bedrijfsmodi
U kunt het hulpprogramma uitvoeren in de volgende twee modi. We raden u het hulpprogramma uitvoeren in *wat-als* zodat u de resultaten bekijken kunt voordat u het hulpprogramma uitvoeren in de modus *verwijderen modus*:
  1.    **Wat-als de modus**:   
      Als u niet geeft de **/verwijderen** switch, en het hulpprogramma wordt uitgevoerd in de modus wat-als de inhoud die worden verwijderd van het distributiepunt identificeert.
   - Wanneer in deze modus wordt uitgevoerd verwijderd het hulpprogramma geen aanwezige gegevens.
   - Informatie over de inhoud die worden verwijderd is geschreven naar het logboekbestand van de hulpprogramma's en u niet gevraagd om elke mogelijke verwijdering te bevestigen.  
      </br>   

  2. **De modus verwijderen**:   
    Wanneer u het hulpprogramma uitvoert met de **/verwijderen** switch, het hulpprogramma wordt uitgevoerd in de modus verwijderen.

     - Wanneer in deze modus wordt uitgevoerd, kan zwevende inhoud die is gevonden op het opgegeven distributiepunt worden verwijderd uit de Inhoudsbibliotheek het distributiepunt.
     -  Voordat u een bestand te verwijderen, moet u bevestigen dat het bestand moet worden verwijderd.  U kunt selecteren, **Y** Ja, **N** voor Nee, of **Ja op Alles** verdere aanwijzingen overslaan en alle zwevende inhoud verwijderen.  
     </br>

Wanneer het hulpprogramma wordt uitgevoerd in de modus, wordt automatisch een logboekbestand gemaakt met een naam met de modus voor die het hulpprogramma wordt uitgevoerd in de naam van het distributiepunt en de datum en tijd van de bewerking. Het logboekbestand wordt automatisch geopend wanneer het hulpprogramma is voltooid.

Standaard wordt het logboekbestand geschreven naar de map temp van het gebruikersaccount dat het hulpprogramma uitgevoerd op de computer waarop het hulpprogramma wordt uitgevoerd. U kunt de **/log** overschakelen naar het logboekbestand omleiden naar een andere locatie, met inbegrip van een netwerkshare.


## <a name="run-the-tool"></a>Het hulpprogramma uitvoeren
Het hulpprogramma uitvoert:
1. Open een beheeropdrachtprompt naar een map met **ContentLibraryCleanup.exe**.  
2. Geef vervolgens een opdrachtregel met de vereiste opdrachtregelparameters en schakelopties die u wilt gebruiken.

**Bekende probleem** wanneer het hulpprogramma wordt uitgevoerd, een fout als volgt kan worden geretourneerd wanneer een pakket of de implementatie is mislukt of uitgevoerd wordt:
-  *System.InvalidOperationException: Deze Inhoudsbibliotheek kan niet worden opgeschoond nu omdat pakket <packageID> niet volledig is geïnstalleerd.*

**Tijdelijke oplossing:** Geen. Het hulpprogramma kan geen betrouwbare zwevende bestanden bepalen wanneer inhoud uitgevoerd wordt of is mislukt om te implementeren. Daarom kunt het hulpprogramma niet u tot de inhoud opschonen totdat dit probleem opgelost is.

### <a name="command-line-switches"></a>Opdrachtregelopties  
De volgende opdrachtregelopties kunnen worden gebruikt in een willekeurige volgorde.   

|Switch|Details|
|---------|-------|
|**/ Delete**  |**Optioneel** </br> Gebruik deze switch als u inhoud wilt verwijderen uit het distributiepunt. U wordt gevraagd voordat inhoud wordt verwijderd. </br></br> Wanneer deze switch niet gebruikt wordt, registreert het hulpprogramma resultaten over welke inhoud wordt verwijderd, maar verwijdert niet de inhoud van het distributiepunt. </br></br> Voorbeeld: ***/ Delete ContentLibraryCleanup.exe /dp server1.contoso.com*** |
| **/q**       |**Optioneel** </br> Het hulpprogramma door deze switch wordt uitgevoerd in de stille modus onderdrukt alle vragen (zoals de aanwijzingen voor het verwijderen van inhoud) en het logboekbestand niet automatisch geopend. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;distribution point FQDN >**  | **Vereist** </br> Geef de volledig gekwalificeerde domeinnaam (FQDN) van het distributiepunt dat u wilt opruimen. </br></br> Voorbeeld:  ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/PS &lt;primaire site FQDN >**       | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br>Het hulpprogramma verbinding met de bovenliggende primaire site query's uitvoeren op basis van SMS-provider. Deze query's kunt het hulpprogramma kunt u bepalen welke inhoud moet op het distributiepunt zodat deze kan herkennen de inhoud die is zwevend en kan worden verwijderd. Deze verbinding naar de bovenliggende primaire site moet worden gemaakt voor distributiepunten op een secundaire site, omdat de vereiste gegevens rechtstreeks vanuit de secundaire site niet beschikbaar zijn.</br></br> Geef de FQDN van de primaire site die deel uitmaakt van het distributiepunt naar of van de bovenliggende primaire bovenliggende wanneer het distributiepunt zich op een secundaire site. </br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;primaire sitecode >**  | **Optionele** bij het opschonen van de inhoud van een distributiepunt op een primaire site.</br>**Vereist** bij het opschonen van de inhoud van een distributiepunt op een secundaire site. </br></br> Geef de sitecode van de primaire site die het distributiepunt bij of van de bovenliggende primaire site wanneer het distributiepunt zich op een secundaire site.</br></br> Voorbeeld: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Optioneel** </br> Geef de locatie waar het hulpprogramma voor het logboekbestand geschreven. Dit kan een lokaal station of een netwerkshare.</br></br> Wanneer deze switch niet gebruikt wordt, wordt het logboekbestand geplaatst in de map temp van de gebruiker op de computer waarop het hulpprogramma wordt uitgevoerd.</br></br> Voorbeeld van de lokale schijf: ***ContentLibraryCleanup.exe /dp server1.contoso.com/log C:\Users\Administrator\Desktop*** </br></br>Voorbeeld van een netwerkshare bevinden: ***/ Log ContentLibraryCleanup.exe /dp server1.contoso.com \\ &lt;delen >\&lt; map >***|
