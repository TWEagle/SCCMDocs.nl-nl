---
title: Prestart-opdrachten voor takenreeksmedia | Microsoft-documenten
description: Maak een script dat wordt gebruikt voor de prestart-opdracht, de inhoud gekoppeld aan de prestart-opdracht te distribueren en de prestart-opdracht configureren voor media.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccc9f652-2953-4c38-8a90-c799484105ca
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 1c396534425179c6828d48acc578295167c566be
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prestart-commands-for-task-sequence-media-in-system-center-configuration-manager"></a>Prestart-opdrachten voor takenreeksmedia in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt een prestart-opdracht maken in System Center Configuration Manager te gebruiken met opstartbare media, zelfstandige media en voorbereide media. De prestart-opdracht is een script of een uitvoerbaar bestand dat wordt uitgevoerd voordat de takenreeks wordt geselecteerd en dat kan communiceren met de gebruiker in Windows PE. Met de prestart-opdracht kan een gebruiker om informatie worden gevraagd die vervolgens wordt opgeslagen in de takenreeksomgeving. Daarnaast kan een query op een takenreeksvariabele worden uitgevoerd om informatie te verzamelen. Wanneer de doelcomputer wordt opgestart, wordt de opdrachtregel uitgevoerd voordat het beleid wordt gedownload van het beheerpunt. Gebruik de volgende procedures om een script te maken voor de prestart-opdracht, de inhoud gekoppeld aan de prestart-opdracht te distribueren en de prestart-opdracht voor media te configureren.  

## <a name="create-a-script-file-to-use-for-the-prestart-command"></a>Een scriptbestand maken voor de prestart-opdracht  
 Takenreeksvariabelen kunnen door het COM-object Microsoft.SMS.TSEnvironment worden gelezen en geschreven terwijl de takenreeks wordt uitgevoerd. In het volgende voorbeeld wordt door een Visual Basic-scriptbestand een query op de takenreeksvariabele _SMSTSLogPath uitgevoerd om de huidige logboeklocatie te achterhalen. Met het script wordt ook een aangepaste variabele ingesteld.  

```  
dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")  
dim logPath  
' You can query the environment to get an existing variable.  
logPath = env("_SMSTSLogPath")  
' You can also set a variable in the OSD environment.  
env("MyCustomVariable") = "varname"  
```  

## <a name="create-a-package-for-the-script-file-and-distribute-the-content"></a>Een pakket voor het scriptbestand maken en de inhoud distribueren  
 Wanneer u het script of uitvoerbare bestand voor de prestart-opdracht hebt gemaakt, moet u een pakketbron maken om de bestanden voor het script of uitvoerbare bestand te hosten, een pakket voor de bestanden maken (geen programma vereist) en de inhoud vervolgens distribueren naar een distributiepunt.  

 Zie voor meer informatie over het maken van een pakket [pakketten en programma's](../../apps/deploy-use/packages-and-programs.md).  

 Zie voor meer informatie over het distribueren van inhoud [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).  

## <a name="configure-the-prestart-command-in-media"></a>De prestart-opdracht configureren voor media  
 U kunt een prestart-opdracht in de wizard Takenreeksmedia maken configureren voor zelfstandige media, opstartbare media en voorgefaseerde media. Zie voor meer informatie over de mediatypen [takenreeksmedia maken](../deploy-use/create-task-sequence-media.md). Gebruik de volgende procedure om een prestart-opdracht voor media te maken.  

#### <a name="to-create-a-prestart-command-in-media"></a>Een prestart-opdracht voor media maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeksmedia maken** om de wizard Takenreeksmedia maken te starten.  

4.  Selecteer op de pagina **Mediatype selecteren** de optie **Zelfstandige media**, **Opstartbare media**of **Voorgefaseerde media**en klik vervolgens op **Volgende**.  

5.  Navigeer naar de pagina **Aanpassing** van de wizard. Zie voor meer informatie over het configureren van de andere pagina's in de wizard [takenreeksmedia maken](../deploy-use/create-task-sequence-media.md).  

6.  Geef op de pagina **Aanpassing** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   Selecteer **Prestart-opdracht inschakelen**.  

    -   Voer in het tekstvak **Opdrachtregel** het script of uitvoerbare bestand in dat u hebt gemaakt voor de prestart-opdracht.  

        > [!IMPORTANT]  
        >  Gebruik **cmd /C < prestart-opdracht\>**  om op te geven van de prestart-opdracht. Als u bijvoorbeeld TSScript.vbs hebt gebruikt als de naam voor uw prestart-opdrachtscript, voert u dus **cmd /C TSScript.vbs** in op de opdrachtregel. Hierbij opent u met **cmd /C** een nieuw venster van de Windows-opdrachtinterpreter en wordt de omgevingsvariabele Path gebruikt om het script of uitvoerbare bestand voor de prestart-opdracht te vinden. U kunt ook het volledige pad naar de prestart-opdracht opgeven, maar de stationsletter kan afwijken op computers met andere stationsconfiguraties.  

    -   Selecteer **Inclusief bestanden voor de prestart-opdracht**.  

    -   Klik op **Instellen** om het pakket te selecteren dat is gekoppeld aan de prestart-opdrachtbestanden.  

    -   Klik op **Bladeren** om het distributiepunt te selecteren dat de inhoud voor de prestart-opdracht host.  

7.  Voltooi de wizard.  

