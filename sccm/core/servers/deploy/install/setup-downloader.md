---
title: Setup Downloader | Microsoft Docs
description: Meer informatie over deze zelfstandige toepassing die is ontworpen om te controleren of dat uw site-installatie wordt de huidige versies van belangrijke installatiebestanden gebruikt.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bda87fc5-2e4c-4992-98a4-01770365038c
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b72148ecc16141843178cbd220fe021fab8be992
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="setup-downloader-for-system-center-configuration-manager"></a>Setup Downloader voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u Setup wilt installeren of upgraden van een System Center Configuration Manager-site uitvoert, kunt u de toepassing Setup Downloader zelfstandige versie van de versie van Configuration Manager die u installeren wilt voor het downloaden van bijgewerkte installatiebestanden.  

Bijgewerkte installatiebestanden zorgt ervoor dat uw site-installatie huidige versies van belangrijke installatiebestanden gebruikt. In oveview:   
-   Wanneer u Setup Downloader gebruikt om bestanden voorafgaand aan de installatie te downloaden, geeft u een map voor de bestanden bevatten.  
-   Het account dat u kunt Setup Downloader uitvoeren moet hebben **volledig beheer** machtigingen naar de downloadmap.  
-   Wanneer u Setup uitvoert om te installeren of upgraden van een site, kunt u rechtstreeks voor gebruik van deze lokale kopie van bestanden die u eerder hebt gedownload. Dit voorkomt dat Setup formulier dat verbinding maakt met Microsoft wanneer u de site-installatie of upgrade start.  
-   U kunt dezelfde lokale kopie van setup-bestanden gebruiken voor volgende site-installaties of -upgrades.  

De volgende typen bestanden worden gedownload door Setup Downloader:  
-   Vereiste herdistribueerbare bestanden  
-   Taalpakketten  
-   De meest recente productupdates voor Setup  

U hebt twee opties om Setup Downloader uit te voeren:
- Voer de toepassing met de gebruikersinterface
- Voor de toepassing uitvoeren vanaf een opdrachtprompt opdrachtregelopties


## <a name="run-setup-downloader-with-the-user-interface"></a>Setup Downloader uitvoeren met de gebruikersinterface  

1.  Open Windows Verkenner op een computer die toegang tot Internet heeft, en Ga naar  **&lt;ConfigMgrInstallationMedia\>\SMSSETUP\BIN\X64**.  

2.  Om Setup Downloader openen, dubbelklikt u op **Setupdl.exe**.   

3. Geef het pad voor de map waarin de bijgewerkte installatiebestanden hosten en klik vervolgens op **downloaden**. Setup Downloader controleert de bestanden die zich momenteel in de downloadmap. Deze downloadt alleen de bestanden die ontbreken of nieuwer is dan de bestaande bestanden. Setup Downloader maakt submappen voor gedownloade talen en andere vereiste submappen.  

4.  De downloadresultaten bekijken, opent u de **ConfigMgrSetup.log** bestand in de hoofdmap van station C.  .  

## <a name="run-setup-downloader-from-a-command-prompt"></a>Setup Downloader uitvoeren vanaf een opdrachtprompt  

1.  In een opdrachtpromptvenster, Ga naar  **&lt;* Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**.   

2.  Uitvoeren als u wilt openen Setup Downloader, **Setupdl.exe**.

    U kunt de volgende opdrachtregelopties met **Setupdl.exe**:   

    -   **/ CONTROLEREN**: Gebruik deze optie om te controleren of de bestanden in de downloadmap, waaronder taalbestanden. Raadpleeg het bestand ConfigMgrSetup.log in de hoofdmap van station C voor een lijst met bestanden die verouderd zijn. Er worden geen bestanden worden gedownload wanneer u deze optie gebruikt.  

    -   **/ VERIFYLANG**: Gebruik deze optie om te controleren of de taalbestanden in de downloadmap. Raadpleeg het bestand ConfigMgrSetup.log in de hoofdmap van station C voor een lijst met taalbestanden die verouderd zijn.

    -   **/ LANG**: Gebruik deze optie om alleen de taalbestanden naar de downloadmap te downloaden.  

    -   **/ NOUI**: Gebruik deze optie om Setup Downloader starten zonder de gebruikersinterface weer te geven. Als u deze optie gebruikt, moet u de **downloadpad** als onderdeel van de opdracht bij de opdrachtprompt.  

    -   **&lt;DownloadPath\>**: U kunt het pad naar de downloadmap automatisch starten van de verificatie of downloadproces opgeven. U moet het downloadpad opgeven wanneer u de **/noui** optie. Als u geen downloadpad opgeeft, moet u het pad opgeven wanneer Setup Downloader wordt geopend. Setup Downloader maakt de map als deze niet bestaat.  

    Voorbeeldopdrachten:

    -   **setupd &lt;DownloadPath\>**  

        -   Setup Downloader start, controleert de bestanden in de opgegeven downloadmap en downloadt alleen de bestanden die ontbreken of die nieuwere versies dan de bestaande bestanden.     

    -   **setupdl / /VERIFY &lt;DownloadPath\>**  

        -   Setup Downloader Start en controleert de bestanden in de opgegeven downloadmap.  

    -   **setupdl / / noui &lt;DownloadPath\>**  

        -   Setup Downloader start, controleert de bestanden in de opgegeven downloadmap en downloadt alleen de bestanden die ontbreken of nieuwer is dan de bestaande bestanden.  

    -   **setupdl / lang &lt;DownloadPath\>**  

        -   Setup Downloader start, controleert de taalbestanden in de opgegeven downloadmap en downloadt alleen de taalbestanden die ontbreken of nieuwer is dan de bestaande bestanden.  

    -   **setupdl / /VERIFY**  

        -   Setup Downloader wordt gestart en vervolgens moet u het pad naar de downloadmap opgeven. Als u klikt vervolgens **controleren**, verifieert het Downloadprogramma de bestanden in de downloadmap.  

3.  De downloadresultaten bekijken, opent u de **ConfigMgrSetup.log** bestand in de hoofdmap van station C.
