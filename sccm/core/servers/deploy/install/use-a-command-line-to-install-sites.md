---
title: Installatie via de opdrachtregel | Microsoft Docs
description: Informatie over het uitvoeren van Setup van System Center Configuration Manager bij een opdrachtprompt voor een verscheidenheid aan site-installaties.
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
ms.sourcegitcommit: f7cd9c71287d62c9f5d36e2f032bc2a6065572ae
ms.openlocfilehash: 8ff48b08d1abb7481592c0ea076d4efa15c3d8ee
ms.contentlocale: nl-nl
ms.lasthandoff: 06/06/2017

---
# <a name="use-a-command-line-to-install-system-center-configuration-manager-sites"></a>Gebruik een opdrachtregel voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt Setup van System Center Configuration Manager uitvoeren bij een opdrachtprompt voor verschillende typen sites installeren.

## <a name="supported-tasks-for-command-line-installations"></a>Ondersteunde taken voor opdrachtregelinstallaties
 Deze methode van het uitvoeren van Setup ondersteunt de volgende site-installatie en taken voor siteonderhoud:

-   **Een centrale beheersite of primaire site installeren vanaf een opdrachtprompt**  
  Weergave [opdrachtregelopties voor Setup](../../../../core/servers/deploy/install/command-line-options-for-setup.md)

-  **De talen in gebruik is op een centrale beheersite of primaire site wijzigen**  
    Voor het wijzigen van de talen die zijn geïnstalleerd op een site via een opdrachtprompt (waaronder de talen voor mobiele apparaten), moet u het volgende doen:  

     -   Het installatieprogramma uitvoeren vanuit  **&lt;ConfigMgrInstallationPath\>\Bin\X64** op de siteserver
     -   Gebruik de **managelangs** opdrachtregeloptie
     -   Een taalscriptbestand die hier worden de talen die u wilt toevoegen of verwijderen, opgeven  

    Gebruik bijvoorbeeld de volgende opdrachtsyntaxis: **setupwpf.exe managelangs &lt;taalscriptbestand\>**  

    Gebruik de informatie in voor het maken van het taalscriptbestand [opdrachtregelopties gebruiken voor het beheren van talen](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Lang)  

-  **Een scriptbestand voor installatie gebruiken voor installaties zonder toezicht sites of siteherstel**  
    U kunt Setup uitvoeren vanaf een opdrachtprompt met behulp van een script voor installatie en u de installatie van een site zonder toezicht uitvoeren. U kunt deze optie ook gebruiken om een site te herstellen.    

    Een script gebruiken met de installatie:  

    -   Het installatieprogramma uitvoert met de opdrachtregeloptie **/SCRIPT** en een scriptbestand opgeven.  

    -   Het scriptbestand moet worden geconfigureerd met de vereiste sleutels en waarden.  

    Het scriptbestand moet beschikken over de volgende secties voor een installatie zonder toezicht van een centrale beheersite of primaire site:  

    -   Identificatie    
    -   Opties    
    -   SQLConfigOptions    
      -   HierarchyOptions    
    -   CloudConnectorOptions   

    U kunt een site herstellen, moet u ook de volgende secties van het scriptbestand:  

    -   Identificatie  
    -   Herstel

Zie voor meer informatie [siteherstel zonder toezicht voor Configuration Manager](/sccm/protect/understand/unattended-recovery).  

Zie voor een lijst met sleutels en waarden moet worden gebruikt in een scriptbestand voor installatie zonder toezicht [sleutels voor een scriptbestand voor installatie zonder toezicht](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Unattended).  

## <a name="about-the-command-line-script-file"></a>Over het bestand opdrachtregelscript  
 Voor installaties zonder toezicht van Configuration Manager, kunt u Setup uitvoert met de opdrachtregeloptie **/SCRIPT**, en een scriptbestand met opties voor de installatie opgeven. De volgende taken worden met deze methode ondersteund:  

-   Een centrale beheersite installeren  
-   Een primaire site installeren  
-   Een configuration Manager-console installeren  
-   Een site herstellen  

> [!NOTE]  
>  U kunt het scriptbestand niet gebruiken voor het upgraden van een evaluatiesite naar een gelicentieerde installatie van Configuration Manager.  

### <a name="the-cdlatest-key-name"></a>De sleutelnaam CDLatest
Wanneer u media vanaf de CD. Meest recente map om uit te voeren een script met het installeren van de volgende vier installatieopties, uw script moet bevatten de **CDLatest** sleutel met een waarde van **1**:
- Een nieuwe centrale beheersite installeren
- Een nieuwe primaire site installeren
- Een centrale beheersite herstellen
- Een primaire site herstellen

Deze waarde wordt niet ondersteund voor gebruik met installatiemedia die die u via de Microsoft Volume License-site.
Zie [opdrachtregelopties](/sccm/core/servers/deploy/install/command-line-options-for-setup) voor informatie over het gebruik van de naam van deze sleutel in het scriptbestand.



### <a name="create-the-script"></a>Het script maken
Het script voor installatie wordt automatisch gemaakt wanneer u [installeren van een site via de gebruikersinterface](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  Wanneer u de instellingen te bevestigen op de **samenvatting** van de wizard het volgende gebeurt:  

-   Het installatieprogramma maakt het script **%TEMP%\ConfigMgrAutoSave.ini**.  U kunt dit bestand wijzigen voordat u deze gebruiken, maar deze moet de bestandsextensie ini behouden.  
-   Het script voor installatie zonder toezicht bevat de instellingen die u hebt geselecteerd in de wizard.  
-   Nadat het script is gemaakt, kunt u het script voor het installeren van andere sites in uw hiërarchie kunt wijzigen.  
-   U kunt dit script vervolgens gebruiken om uit te voeren van een installatie zonder toezicht van Configuration Manager.  

Dit scriptbestand bevat dezelfde informatie die door de installatiewizard vraagt, behalve dat er geen standaardinstellingen.   
U moet alle waarden voor de installatiesleutels die van toepassing op het type installatie dat u gebruikt opgeven.   

Wanneer het installatieprogramma maakt het script voor installatie zonder toezicht, wordt dit ingevuld met de productsleutel die u tijdens de installatie opgeeft. Dit is een geldige productsleutel of **EVAL** wanneer u een evaluatieversie van Configuration Manager installeert. De productsleutelwaarde in het script wordt ingevuld zodat de vereiste controle kan worden voltooid.   

Wanneer Setup de daadwerkelijke installatie start, het automatisch gemaakte script opnieuw geschreven om te wissen van de productsleutelwaarde in het script dat wordt gemaakt. Voordat u het script voor een installatie zonder toezicht van een nieuwe site, kunt u het script een geldige productsleutel of evaluatie-installatie van Configuration Manager opgeven.  

### <a name="section-names-key-names-and-values"></a>Sectienamen, sleutelnamen en waarden
Het script bevat sectienamen, sleutelnamen en waarden. Houd rekening met de volgende informatie:
-   Vereiste sectiesleutelnamen variëren afhankelijk van het installatietype waarvoor u een script schrijft.
-   De volgorde van de sleutels binnen secties en de volgorde van secties binnen het bestand is niet belangrijk.     
-   De sleutels zijn niet hoofdlettergevoelig.  
-   Wanneer u waarden voor sleutels opgeeft, moet de naam van de sleutel worden gevolgd door een gelijkteken (=) en de waarde voor de sleutel.    

> [!TIP]  
>  De volledige set opties Zie [opdrachtregelopties voor het installatieprogramma en scripts](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  

## <a name="use-the-script-setup-command-line-option"></a>Gebruik de opdrachtregeloptie/script Setup

-   U moet gebruiken een Setup-scriptbestand en geef de bestandsnaam na de **/SCRIPT** Setup-opdrachtregeloptie. Houd rekening met de volgende informatie:   
    -   De naam van het bestand moet de **.ini** bestandsnaamextensie.  
    -   Wanneer u verwijst naar het Setup-scriptbestand achter de opdrachtprompt, moet u het volledige pad naar het bestand opgeven. Als uw installatie-initialisatiebestand Setup.ini heet, en deze is opgeslagen in de map C:\Setup, bij de opdrachtprompt, typ bijvoorbeeld: **setup/script c:\setup\setup.ini**.  

-   De account die de installatie uitvoert moet beschikken over **beheerder** rechten op de computer. Wanneer u Setup met het script zonder toezicht uitvoert, het venster opdrachtprompt openen met behulp van de **als administrator uitvoeren** optie.   

