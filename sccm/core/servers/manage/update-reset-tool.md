---
title: Hulpprogramma voor het bijwerken opnieuw instellen
titleSuffix: Configuration Manager
description: Gebruik het hulpprogramma bijwerken opnieuw instellen voor updates in de console voor System Center Configuration Manager.
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25fa89d6-7e47-45a6-8f4e-70b77560fba6
caps.latest.revision: "0"
caps.handback.revision: "0"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 80a778d361800d263b286914ba8cc08379579ada
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="update-reset-tool"></a>Hulpprogramma voor het bijwerken opnieuw instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*  


Vanaf versie 1706, primaire Configuration Manager-sites en centrale beheersites omvatten het hulpprogramma Configuration Manager-Update opnieuw instellen, **CMUpdateReset.exe**. Gebruik het hulpprogramma problemen oplossen wanneer updates in de console hebben problemen met het downloaden of repliceren. Het hulpprogramma is gevonden in de ***\cd.latest\SMSSETUP\TOOLS*** map van de siteserver.

U kunt dit hulpprogramma gebruiken met een willekeurige versie van de huidige vertakking dat nog in de ondersteuning.

Gebruik dit hulpprogramma wanneer een [update in de console](/sccm/core/servers/manage/install-in-console-updates) nog niet is geïnstalleerd en bevindt zich in een foutstatus. Een mislukte status betekent dat het downloaden van de update is uitgevoerd maar vastgelopen of een te lange tijd. Een lange tijd wordt beschouwd als uren langer is dan de historische verwachtingen voor updatepakketten van vergelijkbare grootte. Het kan ook een fout in de update gerepliceerd naar onderliggende primaire sites zijn.  

Wanneer u het hulpprogramma uitvoert, wordt deze wordt uitgevoerd voor de update die u opgeeft. Standaard wordt het hulpprogramma is geïnstalleerd of gedownloade updates niet verwijderd.  

### <a name="prerequisites"></a>Vereisten
Het account waarmee u het hulpprogramma uitvoert vereist de volgende machtigingen:
-   **Lees** en **schrijven** machtigingen voor de sitedatabase van de centrale beheersite en voor elke primaire site in uw hiërarchie. Als u wilt deze machtigingen instelt, kunt u het gebruikersaccount toevoegen als lid van de **db_datawriter** en **db_datareader** [vaste databaserollen](/sql/relational-databases/security/authentication-access/database-level-roles#fixed-database-roles) op de Configuration Manager-database van elke site. Het hulpprogramma communiceert niet met secundaire sites.
-   **Lokale beheerder** op het hoogste niveau van uw hiërarchie.
-   **Lokale beheerder** op de computer die als host fungeert voor het serviceverbindingspunt wordt gehost.

U moet de GUID van het updatepakket dat u wilt instellen. De GUID ophalen:
  1.   Ga in de console naar **beheer** > **Updates en onderhoud**.
  2.   In het weergavevenster met de rechtermuisknop op de kop van een van de kolommen (zoals **status**), selecteer daarna **pakket-Guid** die kolom toevoegen aan de weergave.
  3.   De GUID van het updatepakket wordt nu weergegeven in de kolom.

> [!TIP]  
> Selecteer de rij voor het updatepakket dat u wilt instellen voor het kopiëren van de GUID en gebruikt u CTRL + C om te kopiëren die rij. Als u de gekopieerde selectie in een teksteditor plakken, kunt u alleen de GUID voor gebruik als een parameter in opdrachtregel vervolgens kopiëren wanneer u het hulpprogramma uitvoert.

### <a name="run-the-tool"></a>Het hulpprogramma uitvoeren    
Het hulpprogramma moet worden uitgevoerd op het hoogste niveau van de hiërarchie.

Wanneer u het hulpprogramma uitvoert, gebruik van opdrachtregelparameters om op te geven:
  -   De SQL Server op de bovenste site van de hiërarchie.
  -   De databasenaam van de site op de bovenste site.
  -   De GUID van het updatepakket dat u wilt instellen.

Op basis van de status van de update, identificeert het hulpprogramma de extra servers nodig voor toegang tot.   

Als u het updatepakket is in een *na de download* status, het hulpprogramma niet clean up gemaakt van het pakket. U kunt het verwijderen van een update is gedownload met behulp van de parameter force verwijderen (Zie opdrachtregelparameters verderop in dit onderwerp) forceren als een optie.

Nadat het hulpprogramma wordt uitgevoerd:
-   Als een pakket is verwijderd, start u de SMS_Executive-service op de bovenste site. Controleer op updates zodat u kunt het pakket opnieuw downloaden.
-   Als een pakket is niet verwijderd, hoeft u geen geen actie te ondernemen. De update wordt opnieuw geïnitialiseerd en wordt opnieuw opgestart replicatie of de installatie.

**Parameters voor de opdrachtregel:**  

| Parameter        |Beschrijving                 |  
|------------------|----------------------------|  
|**-S &lt;FQDN-naam van de SQL Server van de bovenste site >** | *Vereist* <br> Geef de FQDN van de SQL Server die als host fungeert voor de sitedatabase voor de bovenste site van uw hiërarchie.    |  
| **-D &lt;databasenaam >**                        | *Vereist* <br> Geef de naam van de database op de bovenste site.  |  
| **-P &lt;pakket-GUID >**                         | *Vereist* <br> Geef de GUID van het updatepakket dat u wilt instellen.   |  
| **-Ik &lt;SQL Server-instantienaam >**             | *Optioneel* <br> De instantie van SQL Server die als host fungeert voor de sitedatabase te identificeren. |
| **-FDELETE**                              | *Optioneel* <br> Verwijderen van een gedownloade updatepakket forceren. |  
 **Voorbeelden:**  
 In een typisch scenario dat u wilt opnieuw instellen van een update die downloaden problemen heeft. De FQDN van uw SQL-Servers is *server1.Fabrikam.com zijn*, de sitedatabase is *CM_XYZ*, en het pakket-GUID is *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  U hebt uitgevoerd: ***CMUpdateReset.exe -S server1.Fabrikam.com zijn -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***

 In een scenario met meer extreme die u wilt verwijderen van problematisch updatepakket forceren. De FQDN van uw SQL-Servers is *server1.Fabrikam.com zijn*, de sitedatabase is *CM_XYZ*, en het pakket-GUID is *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  U hebt uitgevoerd: ***CMUpdateReset.exe - FDELETE -S server1.Fabrikam.com zijn -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***
