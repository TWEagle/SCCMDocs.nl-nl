---
title: Installatie via de opdrachtregel | Microsoft-documenten
description: Informatie over het uitvoeren van Setup van System Center Configuration Manager op de opdrachtregel voor een verscheidenheid aan site-installaties.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7cdb1a9-140a-436e-ac71-72d083110223
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: fefa5f3aa12d82b66a251cf0525475496e1e35cf
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="use-a-command-line-to-install-system-center-configuration-manager-sites"></a>Gebruik een opdrachtregel voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt Setup van System Center Configuration Manager uitvoeren op de opdrachtregel voor het installeren van verschillende typen op de site.

## <a name="supported-tasks-for-command-line-installations"></a>Ondersteunde taken voor opdrachtregel installaties
 Deze methode van het uitvoeren van Setup ondersteunt de installatie van de volgende site en siteonderhoudstaken:

-   **Een centrale beheersite of primaire site installeren vanaf een opdrachtprompt**  
  Weergave [opdrachtregelopties voor Setup](../../../../core/servers/deploy/install/command-line-options-for-setup.md)

-  **Wijzigen van de talen in gebruik is op een centrale beheersite of primaire site**  
    U moet voor het wijzigen van de talen die worden geïnstalleerd op een site via een opdrachtprompt (inclusief talen voor mobiele apparaten):  

     -   Het installatieprogramma uitvoert via  **&lt;Configmgrinstallatiepad\>\Bin\X64** op de siteserver
     -   Gebruik de **/MANAGELANGS** opdrachtregeloptie
     -   Geef een taalscriptbestand die hier worden de talen die u wilt toevoegen of verwijderen,  

    Bijvoorbeeld, gebruik de volgende opdrachtsyntaxis: **setupwpf.exe /MANAGELANGS &lt;taalscriptbestand\>**  

    Gebruik de informatie in voor het maken van het taalscriptbestand [opdrachtregelopties voor het beheren van talen](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Lang)  

-  **Een scriptbestand voor installatie gebruiken voor installaties zonder toezicht sites of siteherstel**  
    U kunt Setup uitvoeren vanaf een opdrachtprompt met behulp van een script voor installatie en u een installatie zonder toezicht uitvoeren. U kunt deze optie ook gebruiken om een site te herstellen.    

    Een script gebruiken met de installatie:  

    -   Het installatieprogramma uitvoert met de opdrachtregel-optie **/SCRIPT** en geeft u een scriptbestand.  

    -   Het scriptbestand moet worden geconfigureerd met de vereiste sleutels en waarden.  

    Voor een installatie zonder toezicht van een centrale beheersite of primaire site, moet het scriptbestand hebben de volgende secties:  

    -   Identificatie    
    -   Opties    
    -   SQLConfigOptions    
      -   HierarchyOptions    
    -   CloudConnectorOptions   

    Als u wilt herstellen op een site, moet u ook de volgende secties van het scriptbestand opnemen:  

    -   Identificatie  
    -   Herstel

Zie voor meer informatie over back-up en herstel de [zonder toezicht-bestand sleutels siteherstel](../../../../protect/understand/backup-and-recovery.md#BKMK_UnattendedSiteRecoveryKeys) in de [back-up en herstel in Configuration Manager](../../../../protect/understand/backup-and-recovery.md) onderwerp.  

Zie voor een lijst met sleutels en waarden moet worden gebruikt in een scriptbestand voor installatie zonder toezicht, [sleutels voor een scriptbestand voor installatie zonder toezicht](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Unattended).  

## <a name="about-the-command-line-script-file"></a>Over het bestand opdrachtregelscript  
 Voor installaties zonder toezicht van Configuration Manager, kunt u Setup uitvoert met de opdrachtregeloptie **/SCRIPT**, en geeft u een scriptbestand met opties voor de installatie. De volgende taken worden via deze methode ondersteund:  

-   Een centrale beheersite installeren  
-   Een primaire site installeren  
-   Een configuration Manager-console installeren  
-   Een site herstellen  

> [!NOTE]  
>  U kunt het script zonder toezicht-bestand niet gebruiken voor een evaluatiesite hebt bijgewerkt naar een gelicentieerde installatie van Configuration Manager.  

### <a name="the-cdlatest-key-name"></a>De naam van de CDLatest
Als u media vanaf de CD gebruikt. Meest recente map om uit te voeren een script van de volgende vier installatieopties wilt installeren, moet uw script omvatten de **CDLatest** sleutel met een waarde van **1**:
- Een nieuwe centrale beheersite installeren
- Een nieuwe primaire site installeert
- Een centrale beheersite herstellen
- Herstellen van een primaire site 

Deze waarde wordt niet ondersteund voor gebruik met installatiemedia waarmee u via de Microsoft Volume License-site krijgen.
Zie [opdrachtregelopties](/sccm/core/servers/deploy/install/command-line-options-for-setup) voor meer informatie over het gebruik van deze sleutelnaam in het scriptbestand.



### <a name="create-the-script"></a>Het script
Het script voor installatie wordt automatisch gemaakt wanneer u [Setup uit om te installeren van een site via de gebruikersinterface](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  Wanneer u de instellingen te bevestigen op de **samenvatting** van de wizard het volgende gebeurt:  

-   Het installatieprogramma maakt het script **%TEMP%\ConfigMgrAutoSave.ini**.  U kunt dit bestand wijzigen voordat u deze gebruiken, maar deze moet de extensie van het .ini-bestand behouden.  
-   Het script voor installatie zonder toezicht bevat de instellingen die u hebt geselecteerd in de wizard.  
-   Nadat het script is gemaakt, kunt u het script voor het installeren van andere sites in uw hiërarchie.  
-   U kunt dit script vervolgens gebruiken om uit te voeren van een installatie zonder toezicht van Configuration Manager.  

Dit scriptbestand bevat de dezelfde informatie die de installatiewizard vraagt, behalve dat er geen standaardinstellingen.   
U moet alle waarden opgeven voor de installatiesleutels die van toepassing op het type installatie dat u gebruikt.   

Wanneer het script voor installatie zonder toezicht wordt gemaakt, wordt dit ingevuld met de productsleutel die u tijdens de installatie opgeeft. Dit is een geldige productsleutel of **EVAL** wanneer u een evaluatieversie van Configuration Manager installeert. De productsleutelwaarde in het script wordt ingevuld, zodat de vereiste controle kan worden voltooid.   

Wanneer de daadwerkelijke installatie wordt gestart, is het automatisch gemaakte script geschreven om opnieuw te wissen de productsleutelwaarde in het script dat wordt gemaakt. Voordat u het script voor een installatie zonder toezicht van een nieuwe site, kunt u het script naar een geldige productsleutel of evaluatie-installatie van Configuration Manager opgeven.  

### <a name="section-names-key-names-and-values"></a>Sectienamen, sleutelnamen en waarden
Het script bevat sectienamen, sleutelnamen en waarden. Houd rekening met de volgende informatie:
-   Vereiste sectiesleutelnamen variëren afhankelijk van het installatietype waarvoor u een script schrijft.
-   De volgorde van de sleutels binnen secties en de volgorde van secties binnen het bestand is niet belangrijk.     
-   De sleutels zijn niet hoofdlettergevoelig.  
-   Wanneer u waarden voor sleutels opgeeft, moet de naam van de sleutel worden gevolgd door een gelijkteken (=) en de waarde voor de sleutel.    

> [!TIP]  
>  De volledige set opties Zie [opdrachtregelopties voor Setup en scripts](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  

## <a name="use-the-script-setup-command-line-option"></a>Gebruik de opdrachtregeloptie/script Setup

-   U moet gebruiken een scriptbestand voor installatie en de naam opgeven na de **/SCRIPT** Setup-opdrachtregeloptie. Houd rekening met de volgende informatie:   
    -   De naam van het bestand moet bevatten de **.ini** bestandsnaamextensie.  
    -   Wanneer u verwijst naar het scriptbestand voor installatie vanaf de opdrachtregel, moet u het volledige pad naar het bestand opgeven. Bijvoorbeeld, als uw installatie-initialisatiebestand Setup.ini heet en dit is opgeslagen in de map C:\Setup vanaf de opdrachtregel typt: **setup/script c:\setup\setup.ini**.  

-   De account die de installatie uitvoert moet hebben **Administrator** rechten op de computer. Wanneer u Setup met het script zonder toezicht uitvoert, open het opdrachtpromptvenster met de **als administrator uitvoeren** optie.   

