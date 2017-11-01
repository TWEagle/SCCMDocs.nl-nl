---
title: -Console installeren
titleSuffix: Configuration Manager
description: Lees over het installeren van de Configuration Manager-console verbinding maken met een centrale beheersite of primaire site.
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: f367f94f809863403ed562a65cf44f21de698005
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="install-the-system-center-configuration-manager-console"></a>De System Center Configuration Manager-console installeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheerders de System Center Configuration Manager-console gebruiken om de Configuration Manager-omgeving te beheren. Elke Configuration Manager-console kunt verbinding maken met een centrale beheersite of een primaire site. U kunt een Configuration Manager-console kan geen verbinding met een secundaire site.

> [!NOTE]  
>  Welke objecten ziet een beheerder die de console wordt uitgevoerd, is afhankelijk van de machtigingen die zijn toegewezen aan hun gebruikersaccount. Zie voor meer informatie over Rolgebaseerd beheer [basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 U kunt de Configuration Manager-console installeren tijdens de installatie van de site via de Wizard Setup of u een zelfstandige installatie-toepassing die gebruikmaakt van de Wizard Setup kunt uitvoeren.  

 Gebruik de volgende procedure een Configuration Manager-console installeren met behulp van de zelfstandige toepassing.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>De Configuration Manager-console installeren met behulp van de Wizard Setup  

1.  Controleer of u aan deze vereisten voldoen:  

    -  U hebt **lokale beheerder** rechten op de computer op waarop de console wordt uitgevoerd.  

    -   U hebt **lezen** machtigingen voor de locatie van de Configuration Manager-console bestanden voor installatie.  

2.  Ga naar een van deze locaties:  

    -   Op de siteserver, gaat u naar  **<* installatiepad voor Configuration Manager site server*> \Tools\ConsoleSetup**.  

    -   Ga naar in de Configuration Manager-bronmedia  **<* bronbestanden Configuration Manager*> \Smssetup\Bin\I386**.  

    > [!TIP]  
    >  Start de installatie van de console Configuration Manager vanuit een siteserver in plaats van vanaf de installatiemedia van System Center Configuration Manager als een best practice. De installatiemethode van de site server kopieert de installatiebestanden van de Configuration Manager-console en ondersteunde talenpakketten voor de site naar de **Tools\ConsoleSetup** submap. De Configuration Manager-console altijd vanaf de installatiemedia installeert, installeert de Engelse versie, ongeacht de ondersteunde talen op de siteserver of de taalinstellingen van het besturingssysteem dat op de computer wordt uitgevoerd. Desgewenst kunt u de **ConsoleSetup** map op een andere locatie om de installatie te starten.

3.  Om de Wizard Setup van Configuration Manager-Console openen, dubbelklikt u op **consolesetup.exe**.  

    > [!IMPORTANT]  
    >  Installeer de Configuration Manager-console altijd via consolesetup.exe. Hoewel de Configuration Manager-console kan worden geïnstalleerd door adminconsole.msi, deze methode wordt niet uitgevoerd vereisten of afhankelijkheden controles en de installatie mogelijk niet correct geïnstalleerd.  

4.  Selecteer in de wizard **volgende**.  

5.  Op de **siteserver** pagina, voert u de volledig gekwalificeerde domeinnaam (FQDN) van de siteserver waarmee de Configuration Manager-console verbinding maakt.  

6.  Op de **installatiemap** pagina, voert u de installatiemap voor de Configuration Manager-console. Het mappad mag geen spaties of Unicode-tekens bevatten.  

7.  Op de **Customer Experience Improvement Program** te selecteren of u deelneemt aan het Customer Experience Improvement Program (CEIP).  

8.  Op de **gereed voor installatie** pagina **installeren** de Configuration Manager-console te installeren.  

## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>De Configuration Manager-console installeren vanaf een opdrachtprompt  

1.  Open een opdrachtpromptvenster op de server van waaruit u de Configuration Manager-console installeren, en Ga naar een van de volgende locaties:  

    -   **<*Installatiepad voor Configuration Manager site server*> \Tools\ConsoleSetup**  

    -   **<*Configuration Manager-installatiemedia*> \SMSSETUP\BIN\I386**  

    > [!TIP]  
    >  Wanneer u de Configuration Manager-console vanaf een opdrachtprompt installeert, wordt de Engelse versie altijd geïnstalleerd, ongeacht de taalinstelling van het besturingssysteem dat op de computer wordt uitgevoerd. Als u wilt de Configuration Manager-console installeren in een andere taal dan Engels, moet u [de Configuration Manager-console installeren met behulp van de Wizard Setup](#to-install-the-configuration-manager-console-by-using-the-setup-wizard).  

2.  Typ het volgende achter de opdrachtprompt **consolesetup.exe**. Kies in de volgende opdrachtregelopties.  

|  Opdrachtregeloptie     | Beschrijving     |
  | :------------- | :------------- |
  |/q|Installeert de Configuration Manager-console zonder toezicht. De **EnableSQM**, **TargetDir**, en **DefaultSiteServerName** opties zijn vereist als u deze optie gebruikt.|  
  |/uninstall|Hiermee verwijdert u de Configuration Manager-console. U moet deze optie eerst specificeren wanneer u deze met gebruikt de **/q** optie.|  
  |LangPackDir|Hiermee geeft u het pad naar de map die de taalbestanden bevat. U kunt **Setup Downloader** om de taalbestanden te downloaden. Als u deze optie niet gebruikt, zoekt het installatieprogramma de taalmap in de huidige map. Als de taalmap niet wordt gevonden, wordt de installatie wordt voortgezet alleen Engels geïnstalleerd. Zie voor meer informatie [Setup Downloader](setup-downloader.md).|  
  |TargetDir|Hiermee geeft u de installatiemap voor de installatie van de Configuration Manager-console. Deze optie is verplicht wanneer u de **/q** optie.|  
  |EnableSQM|Hiermee geeft u op of u deelneemt aan het Customer Experience Improvement Program (CEIP). Gebruik een waarde van **1** lid worden van het programma voor Kwaliteitsverbetering en een waarde van **0** naar niet deelnemen aan het programma. Deze optie is verplicht wanneer u de **/q** optie.|  
  |DefaultSiteServerName|Hiermee geeft u de FQDN-naam van de siteserver waarmee de console verbinding maakt wanneer deze wordt geopend. Deze optie is verplicht wanneer u de **/q** optie.|  


  **Voorbeelden:**

  -  **consolesetup.exe /q TargetDir = 'D:\Program Files\ConfigMgr' EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe /q LangPackDir C:\Downloads\ConfigMgr TargetDir = 'D:\Program Files\ConfigMgr' Console EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com =**  

  -  **consolesetup.exe / uninstall /q**  
