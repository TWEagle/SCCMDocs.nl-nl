---
title: -Console installeren
titleSuffix: Configuration Manager
description: De Configuration Manager-console verbinding maken met een centrale beheersite of primaire site installeren.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 05d19258b9bfc2a033eb4d7974f17fc0eb3d4c72
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="install-the-system-center-configuration-manager-console"></a>De System Center Configuration Manager-console installeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheerders de Configuration Manager-console gebruiken om de Configuration Manager-omgeving te beheren. Elke Configuration Manager-console kunt verbinding maken met een centrale beheersite of een primaire site. U kunt een Configuration Manager-console kan geen verbinding met een secundaire site.

> [!NOTE]  
>  Een beheerder ziet objecten in de console op basis van de machtigingen worden toegewezen aan hun gebruikersaccount. Zie voor meer informatie over Rolgebaseerd beheer [basisprincipes van beheer op basis van rollen](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 Wanneer u de siteserver installeert, kunt u de Configuration Manager-console installeren op hetzelfde moment. Het zelfstandige installatieprogramma voor het installeren van de afzonderlijke console van de installatie van de siteserver, worden uitgevoerd.  

 Gebruik de volgende procedures voor het installeren van de Configuration Manager-console met behulp van het zelfstandige installatieprogramma.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>De Configuration Manager-console installeren met behulp van de Wizard Setup  

1.  Controleer of u aan deze vereisten voldoen:  

    -  U hebt lokale **beheerder** rechten op de doelcomputer voor de console.  

    -   U hebt **lezen** machtigingen voor de locatie van de Configuration Manager-console bestanden voor installatie.  

2.  Ga naar een van deze locaties:  

    -   Op de siteserver, gaat u naar: `<Configuration Manager site server installation path>\Tools\ConsoleSetup`  

    -   Ga naar de bronmedia van Configuration Manager: `<Configuration Manager source files>\Smssetup\Bin\I386`  

    > [!TIP]  
    >  Als een best practice, start u het installatieprogramma van Configuration Manager-console van een siteserver in plaats van vanaf de installatiemedia van System Center Configuration Manager. Wanneer u een siteserver installeert, het kopieert de installatiebestanden van de Configuration Manager-console en ondersteunde talenpakketten voor de site naar de **Tools\ConsoleSetup** submap. De Configuration Manager-console altijd vanaf de installatiemedia installeert, wordt de Engelse versie geïnstalleerd. Dit gedrag gebeurt zelfs als de siteserver biedt ondersteuning voor verschillende talen of de doelcomputer OS is ingesteld op een andere taal. Desgewenst kunt u de **ConsoleSetup** map op een andere locatie om de installatie te starten.

3.  Om de Wizard Setup van Configuration Manager-Console openen, dubbelklikt u op **consolesetup.exe**.  

    > [!IMPORTANT]  
    >  De Configuration Manager-console altijd installeren met behulp van **consolesetup.exe**. Hoewel u de Configuration Manager-console installeren kunt door adminconsole.msi, wordt deze methode niet vereisten of afhankelijkheden controles uitgevoerd. De installatie mogelijk niet correct geïnstalleerd.  

4.  Selecteer in de wizard **volgende**.  

5.  Op de **siteserver** pagina, voert u de volledig gekwalificeerde domeinnaam (FQDN) van de siteserver waarmee de Configuration Manager-console verbinding maakt.  

6.  Op de **installatiemap** pagina, voert u de installatiemap voor de Configuration Manager-console. Het mappad mag geen spaties of Unicode-tekens bevatten.  

7.  Op de **Customer Experience Improvement Program** te selecteren of u deelneemt aan het Customer Experience Improvement Program (CEIP).  
    > [!Note]  
    > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.

8.  Op de **gereed voor installatie** pagina **installeren** de Configuration Manager-console te installeren.  



## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>De Configuration Manager-console installeren vanaf een opdrachtprompt  

1.  Open een opdrachtpromptvenster op de server van waaruit u de Configuration Manager-console installeren, en Ga naar een van de volgende locaties:  

    -   `<Configuration Manager site server installation path>\Tools\ConsoleSetup`  

    -   `<Configuration Manager installation media>\SMSSETUP\BIN\I386`  

    > [!TIP]  
    >  De Configuration Manager-console altijd installeren vanaf een opdrachtprompt, wordt de Engelse versie geïnstalleerd. Dit gedrag gebeurt zelfs als de doelcomputer OS is ingesteld op een andere taal. Als u wilt de Configuration Manager-console installeren in een andere taal dan Engels, moet u [de Configuration Manager-console installeren met behulp van de Wizard Setup](#to-install-the-configuration-manager-console-by-using-the-setup-wizard).  

2.  Typ het volgende achter de opdrachtprompt **consolesetup.exe**. Kies in de volgende opdrachtregelopties:  

|  Opdrachtregeloptie     | Beschrijving     |
  |-------------|-------------|
  |/q|Installeert de Configuration Manager-console zonder toezicht. De **EnableSQM**, **TargetDir**, en **DefaultSiteServerName** opties zijn vereist als u deze optie gebruikt.|  
  |/uninstall|Hiermee verwijdert u de Configuration Manager-console. Deze optie eerst specificeren wanneer u deze met gebruikt de **/q** optie.|  
  |LangPackDir|Hiermee geeft u het pad naar de map die de taalbestanden bevat. U kunt **Setup Downloader** om de taalbestanden te downloaden. Als u deze optie niet gebruikt, zoekt het installatieprogramma de taalmap in de huidige map. Als de taalmap niet wordt gevonden, wordt de installatie wordt voortgezet alleen Engels geïnstalleerd. Zie voor meer informatie [Setup Downloader](setup-downloader.md).|  
  |TargetDir|Hiermee geeft u de installatiemap voor de installatie van de Configuration Manager-console. Deze optie is verplicht wanneer u de **/q** optie.|  
  |EnableSQM|Hiermee geeft u op of u deelneemt aan het Customer Experience Improvement Program (CEIP). Gebruik een waarde van **1** lid worden van het programma voor Kwaliteitsverbetering en een waarde van **0** naar niet deelnemen aan het programma. Deze optie is verplicht wanneer u de **/q** optie.</br></br>Opmerking: Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.|  
  |DefaultSiteServerName|Hiermee geeft u de FQDN-naam van de siteserver waarmee de console verbinding maakt wanneer deze wordt geopend. Deze optie is verplicht wanneer u de **/q** optie.|  


  ### <a name="examples"></a>Voorbeelden

  -  `consolesetup.exe /q TargetDir="D:\Program Files\ConfigMgr" EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com`  

  -  `consolesetup.exe /q LangPackDir=C:\Downloads\ConfigMgr TargetDir="D:\Program Files\ConfigMgr Console" EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com`  

  -  `consolesetup.exe /uninstall /q`  
