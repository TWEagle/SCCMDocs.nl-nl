---
title: Setup Downloader | Microsoft-documenten
description: Meer informatie over deze zelfstandige toepassing die is ontworpen om te controleren van de site-installatie maakt gebruik van huidige versies van de belangrijkste installatiebestanden komen te staan.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bda87fc5-2e4c-4992-98a4-01770365038c
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 34e24deb90a39bf655a2e24d16cdbe07528e6193
ms.openlocfilehash: b72148ecc16141843178cbd220fe021fab8be992
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="setup-downloader-for-system-center-configuration-manager"></a>Setup Downloader voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u Setup wilt installeren of upgraden van een System Center Configuration Manager-site uitvoert, kunt u de toepassing Setup Downloader zelfstandige van de versie van Configuration Manager die u wilt installeren om bijgewerkte Setup-bestanden te downloaden.  

Bijgewerkte installatiebestanden zorgt ervoor dat uw site-installatie maakt gebruik van huidige versies van de belangrijkste installatiebestanden komen te staan. In oveview:   
-   Wanneer u Setup Downloader downloaden voordat u setup-bestanden gebruikt, geeft u een map voor de bestanden bevatten.  
-   Het account waarmee u Setup Downloader uitvoeren moet hebben **volledig beheer** machtigingen naar de downloadmap.  
-   Wanneer u Setup uitvoert om te installeren of upgraden van een site, kunt u instellen dat deze lokale kopie van de eerder gedownloade bestanden gebruiken. Hiermee wordt een formulier die verbinding maken met Microsoft wanneer u de site-installatie of upgrade start.  
-   U kunt de dezelfde lokale kopie van setup-bestanden gebruiken voor installaties van de volgende site of upgrades.  

De volgende soorten bestanden worden gedownload door Setup Downloader:  
-   Vereiste herdistribueerbare bestanden  
-   Taalpakketten  
-   De meest recente productupdates voor Setup  

Hebt u twee opties voor het uitvoeren van Setup Downloader:
- Uitvoeren van de toepassing met de gebruikersinterface
- Voor opdrachtregelopties, uitvoeren van de toepassing met een opdrachtprompt


## <a name="run-setup-downloader-with-the-user-interface"></a>Setup Downloader uitvoeren met de gebruikersinterface  

1.  Open Windows Verkenner op een computer die toegang tot Internet heeft, en gaat u naar  **&lt;ConfigMgrInstallationMedia\>\SMSSETUP\BIN\X64**.  

2.  Om Setup Downloader openen, dubbelklikt u op **Setupdl.exe**.   

3. Geef het pad voor de map waarin de Geüpdatete installatiebestanden komen te staan en klik vervolgens op **downloaden**. Setup Downloader controleert de bestanden die zich momenteel in de downloadmap. Deze downloadt alleen de bestanden die ontbreken of nieuwer is dan de bestaande bestanden. Setup Downloader maakt submappen voor gedownloade talen en andere vereiste submappen.  

4.  De downloadresultaten bekijken, opent u de **ConfigMgrSetup.log** bestand in de hoofdmap van station C.  .  

## <a name="run-setup-downloader-from-a-command-prompt"></a>Setup Downloader uitvoeren vanaf een opdrachtprompt  

1.  In een opdrachtpromptvenster, Ga naar  **&lt;* Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**.   

2.  Uitvoeren om Setup Downloader openen, **Setupdl.exe**.

    U kunt de volgende opdrachtregelopties met **Setupdl.exe**:   

    -   **/ CONTROLEREN**: Gebruik deze optie om te controleren of de bestanden in de downloadmap, waaronder taalbestanden. Raadpleeg het bestand ConfigMgrSetup.log in de hoofdmap van C-station voor een lijst met bestanden die verouderd zijn. Er worden geen bestanden gedownload als u deze optie gebruikt.  

    -   **/ VERIFYLANG**: Gebruik deze optie om de taalbestanden in te downloadmap te controleren. Raadpleeg het bestand ConfigMgrSetup.log in de hoofdmap van C-station voor een lijst met taalbestanden die verouderd zijn.

    -   **/LANG**: Gebruik deze optie alleen de taalbestanden te downloaden naar de downloadmap.  

    -   **/NOUI**: Deze optie gebruiken om Setup Downloader starten zonder de gebruikersinterface weer te geven. Als u deze optie gebruikt, moet u de **downloadpad** als onderdeel van de opdracht uit vanaf de opdrachtregel.  

    -   **&lt;Downloadpad\>**: U kunt het pad naar de downloadmap automatisch starten van de controle of het downloaden te opgeven. U moet het downloadpad specificeren wanneer u de **/noui gebruikt** optie. Als u geen downloadpad opgeeft, moet u het pad opgeven wanneer Setup Downloader wordt geopend. Setup Downloader maakt de map als deze niet bestaat.  

    Van de voorbeeldopdrachten:

    -   **setupd &lt;downloadpad\>**  

        -   Setup Downloader start, controleert de bestanden in de downloadmap en downloadt alleen de bestanden die ontbreken of nieuwere versies dan de bestaande bestanden.     

    -   **setupdl /VERIFY &lt;downloadpad\>**  

        -   Setup Downloader Start en controleert de bestanden in de downloadmap.  

    -   **setupdl/noui gebruikt &lt;downloadpad\>**  

        -   Setup Downloader start, controleert de bestanden in de downloadmap en downloadt alleen de bestanden die ontbreken of nieuwer is dan de bestaande bestanden.  

    -   **setupdl/lang &lt;downloadpad\>**  

        -   Setup Downloader start, controleert de taalbestanden in de downloadmap en downloadt alleen de taalbestanden die ontbreken of nieuwer is dan de bestaande bestanden.  

    -   **setupdl /VERIFY**  

        -   Setup Downloader wordt gestart en moet u het pad naar de downloadmap opgeven. Als u klikt vervolgens **controleren**, verifieert het Downloadprogramma de bestanden in de downloadmap.  

3.  De downloadresultaten bekijken, opent u de **ConfigMgrSetup.log** bestand in de hoofdmap van station C.

