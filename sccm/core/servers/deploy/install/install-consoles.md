---
title: -Console installeren | Microsoft-documenten
description: Lees over het installeren van de Configuration Manager-console verbinding maakt met een centrale beheersite of primaire site.
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: b6b47fd1f56780a40c96b5e228046b41fe3a9a47
ms.openlocfilehash: 88ecbc48fd03ce988f04408d0378844cbed1de2b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="install-the-system-center-configuration-manager-console"></a>De System Center Configuration Manager-console installeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheerders de System Center Configuration Manager-console gebruiken om de Configuration Manager-omgeving te beheren. Elke Configuration Manager-console kunt verbinding maken met een centrale beheersite of een primaire site. U kunt een Configuration Manager-console geen verbinding met een secundaire site.

> [!NOTE]  
>  Welke objecten ziet een beheerder die de console wordt uitgevoerd, is afhankelijk van de machtigingen die zijn toegewezen aan hun gebruikersaccount. Zie voor meer informatie over op rollen gebaseerd beheer [grondbeginselen van op rollen gebaseerd beheer voor System Center Configuration Manager](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 U kunt de Configuration Manager-console installeren tijdens de installatie van de siteserver via de Wizard Setup of u een zelfstandige installatie-toepassing die gebruikmaakt van de Wizard Setup kunt uitvoeren.  

 Gebruik de volgende procedure een Configuration Manager-console installeren via de zelfstandige toepassing.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>De Configuration Manager-console installeren met behulp van de Wizard Setup  

1.  Controleer of u aan deze vereisten voldoen:  

    -  U hebt **lokale beheerder** rechten op de computer waarop de console wordt uitgevoerd.  

    -   U hebt **lezen** machtigingen naar de locatie van de Configuration Manager-console installatiebestanden komen te staan.  

2.  Ga naar een van de volgende locaties:  

    -   Ga op de siteserver naar  **<* installatiepad voor Configuration Manager site server*> \Tools\ConsoleSetup**.  

    -   Vanuit de bronmedia van Configuration Manager gaat u naar  **<* Configuration Manager-bronbestanden*> \Smssetup\Bin\I386**.  

    > [!TIP]  
    >  Als een best practice gestart met de Configuration Manager console-installatie vanaf een siteserver in plaats van vanaf het installatiemedium van System Center Configuration Manager. De installatiemethode van de site server kopieert de installatiebestanden van de Configuration Manager-console en ondersteunde taalpakketten voor de site de **Tools\ConsoleSetup** submap. De Configuration Manager-console vanaf de installatiemedia altijd installeert, worden de Engelse versie, ongeacht de ondersteunde talen op de siteserver of de taalinstellingen van het besturingssysteem dat wordt uitgevoerd op de computer. Eventueel kunt u de **ConsoleSetup** map naar een alternatieve locatie om de installatie te starten.

3.  Om de Wizard Setup van Configuration Manager-Console openen, dubbelklikt u op **consolesetup.exe**.  

    > [!IMPORTANT]  
    >  Installeer altijd de Configuration Manager-console met behulp van consolesetup.exe. Hoewel de Configuration Manager-console kan worden geïnstalleerd door het uitvoeren van adminconsole.msi, deze methode wordt niet uitgevoerd vereisten of afhankelijkheid controles en de installatie mogelijk niet correct geïnstalleerd.  

4.  Selecteer in de wizard **volgende**.  

5.  Op de **siteserver** pagina, voert u de volledig gekwalificeerde domeinnaam (FQDN) van de siteserver waarmee de Configuration Manager-console verbinding maakt.  

6.  Op de **installatiemap** pagina, voert u de installatiemap voor de Configuration Manager-console. Het mappad mag geen spaties of Unicode-tekens bevatten.  

7.  Op de **programma voor kwaliteitsverbetering** te selecteren of u zich aanmeldt klant ervaring Improvement Program (CEIP).  

8.  Op de **gereed voor installatie** optie **installeren** de Configuration Manager-console te installeren.  

## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>De Configuration Manager-console installeren vanaf een opdrachtprompt  

1.  Open een opdrachtpromptvenster op de server van waaruit u de Configuration Manager-console installeert, en gaat u naar een van de volgende locaties:  

    -   **<*Installatiepad voor Configuration Manager site server*> \Tools\ConsoleSetup**  

    -   **<*Configuration Manager-installatiemedia*> \SMSSETUP\BIN\I386**  

    > [!TIP]  
    >  Wanneer u de Configuration Manager-console vanaf een opdrachtprompt installeert, is de Engelse versie altijd geïnstalleerd, ongeacht de taalinstelling van het besturingssysteem dat wordt uitgevoerd op de computer. Voor het installeren van de Configuration Manager-console in een andere taal dan Engels, moet u [de Configuration Manager-console installeren met behulp van de Wizard Setup](#to-install-the-configuration-manager-console-by-using-the-setup-wizard).  

2.  Typ bij de opdrachtprompt **consolesetup.exe**. Kies in de volgende opdrachtregelopties.  

|  Opdrachtregeloptie     | Beschrijving     |
  | :------------- | :------------- |
  |/q|De Configuration Manager-console zonder toezicht installeert. De **EnableSQM**, **TargetDir**, en **DefaultSiteServerName** opties zijn vereist als u deze optie gebruikt.|  
  |/uninstall|Hiermee verwijdert u de Configuration Manager-console. U moet deze optie eerst specificeren wanneer u deze met gebruikt de **/q** optie.|  
  |LangPackDir|Hiermee geeft u het pad naar de map die de taalbestanden bevat. U kunt **Setup Downloader** om de taalbestanden te downloaden. Als u deze optie niet gebruikt, zoekt het installatieprogramma de taalmap in de huidige map. Als de taalmap wordt gevonden, wordt de installatie wordt voortgezet alleen Engels geïnstalleerd. Zie voor meer informatie [Downloadprogramma](setup-downloader.md).|  
  |TargetDir|Hiermee geeft u de installatiemap voor de installatie van de Configuration Manager-console. Deze optie is verplicht wanneer u de **/q** optie.|  
  |EnableSQM|Hiermee geeft u op of u zich aanmeldt klant ervaring Improvement Program (CEIP). Gebruik een waarde van **1** deelnemen aan het programma voor Kwaliteitsverbetering en de waarde van **0** niet deelnemen aan het programma. Deze optie is verplicht wanneer u de **/q** optie.|  
  |DefaultSiteServerName|Hiermee geeft u de FQDN-naam van de siteserver waarmee de console verbinding maakt wanneer deze wordt geopend. Deze optie is verplicht wanneer u de **/q** optie.|  


  **Voorbeelden:**

  -  **consolesetup.exe /q TargetDir = "D:\Program Files\ConfigMgr" EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe /q LangPackDir C:\Downloads\ConfigMgr TargetDir = "D:\Program Files\ConfigMgr" Console EnableSQM = 1 DefaultSiteServerName=MyServer.Contoso.com =**  

  -  **consolesetup.exe / uninstall/q**  

