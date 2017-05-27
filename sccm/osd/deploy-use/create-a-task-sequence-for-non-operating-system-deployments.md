---
title: Maak een takenreeks voor niet - besturingssysteemimplementaties | Microsoft-documenten
description: Takenreeksen maken die niet zijn gerelateerd aan het implementeren van besturingssystemen, zoals software distribueren, bijwerken, stuurprogramma&quot;s, bewerkt statussen van de gebruiker, enzovoort.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92aaec8a-8751-442a-b64b-62ab05b5bf50
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: b4b04907f2cd48d81e864e46ca47c14a0b98a9f7
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-for-non-operating-system-deployments-with-system-center-configuration-manager"></a>Een takenreeks maken voor niet - besturingssystemen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Takenreeksen in System Center Configuration Manager worden gebruikt voor een verscheidenheid aan taken binnen uw omgeving te automatiseren. Deze taken zijn voornamelijk ontworpen en getest voor het implementeren van besturingssystemen.  Configuration Manager beschikt over vele andere functies die moeten worden de belangrijkste technologie die u voor scenario's, zoals gebruikt [toepassingsinstallatie](../../apps/understand/introduction-to-application-management.md), [installatie van software-updates](../../sum/understand/software-updates-introduction.md), [instelling configuratie](../../compliance/understand/ensure-device-compliance.md), of aangepaste automatisering. Er zijn andere Microsoft System Center-automatiseringstechnologieën, zoals [Orchestrator](https://technet.microsoft.com/library/hh237242.aspx) en [Service Management Automation](https://technet.microsoft.com/library/dn469260.aspx) , die ook moeten worden overwogen.  

De kracht van takenreeksen ligt in hun flexibiliteit en hoe u kunt deze clientinstellingen configureren, software distribueren, stuurprogramma's bijwerken, gebruiker statussen bewerken en andere taken die onafhankelijk van de implementatie van besturingssysteem uitvoeren. U kunt een aangepaste takenreeks maken om elk gewenst aantal taken toe te voegen. Het gebruik van aangepaste takenreeksen voor de implementatie van niet-besturingssysteem wordt ondersteund in Configuration Manager. Echter, als een reeks resultaten in ongewenste of inconsistente resultaten, kijken naar manieren om te vereenvoudigen de bewerking. U kunt dit bereiken door eenvoudiger stappen te volgen, de acties verdelen over meerdere takenreeksen, of door een gefaseerde benadering te maken en testen van de takenreeks.

 De volgende stappen worden ondersteund voor gebruik in een aangepaste takenreeks voor implementatie van niet-besturingssysteem:  

-   [Gereedheid controleren](../understand/task-sequence-steps.md#BKMK_CheckReadiness)  

-   [Verbinding maken met netwerkmap](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder)  

-   [Inhoud van het pakket downloaden](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent)  

-   [Toepassing installeren](../understand/task-sequence-steps.md#BKMK_InstallApplication)  

-   [Pakket installeren](../understand/task-sequence-steps.md#BKMK_InstallPackage)  

-   [Software-Updates installeren](../understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates)  

-   [Computer opnieuw opstarten](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer)  

-   [Opdrachtregel uitvoeren](../understand/task-sequence-steps.md#BKMK_RunCommandLine)  

-   [PowerShell-Script uitvoeren](../understand/task-sequence-steps.md#BKMK_RunPowerShellScript)  

-   [Dynamische variabelen instellen](../understand/task-sequence-steps.md#BKMK_SetDynamicVariables)  

-   [Takenreeksvariabele instellen](../understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable)  

## <a name="next-steps"></a>Volgende stappen
[De takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#a-namebkmkdeploytsa-deploy-a-task-sequence)

