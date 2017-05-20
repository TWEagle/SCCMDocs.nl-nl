---
title: Voorziet u BitLocker in Windows PE | Microsoft-documenten
description: De taak Preprovision BitLocker in Configuration Manager schakelt BitLocker vanuit de Windows Preinstallation Environment voordat de implementatie van besturingssystemen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7c94ba0-d709-4129-8077-075a8abaea1c
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: baca498dbc5b8e168852aa3c18ee23a9c483e69c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="preprovision-bitlocker-in-windows-pe-with-system-center-configuration-manager"></a>Voorziet u BitLocker in Windows PE met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De **BitLocker vooraf inrichten** takenreeksstap in System Center Configuration Manager kunt u BitLocker inschakelen vanuit de Windows Preinstallation Environment (Windows PE) voorafgaand aan de implementatie van besturingssysteem. Alleen de gebruikte schijfruimte is versleuteld. De versleutelingstijd is daarom veel sneller. Hierbij wordt een willekeurig gegenereerde niet-versleutelde sleutelbeveiliging toegepast op het geformatteerde volume en wordt het volume versleuteld voorafgaand aan het Windows-installatieproces. De mogelijkheid om BitLocker vooraf in te richten is ingevoerd in Windows 8 en Windows Server 2012. U kunt echter BitLocker vooraf inrichten op een harde schijf en Windows 7 installeren mits u specifieke stappen volgt. Nadat Setup van Windows 7 is voltooid, moet een BitLocker-sleutelbeveiliging worden ingesteld, omdat in het Windows 7 BitLocker-configuratiescherm geen ondersteuning wordt geboden voor BitLocker met een niet-versleutelde sleutelbeveiliging. U moet een sleutelbeveiliging toevoegen met behulp van de stap **BitLocker inschakelen** of met het opdrachtregelprogramma manage-bde.exe.  

 U moet over het algemeen de volgende stappen nemen om BitLocker in te richten op een computer waarop Windows 7 wordt geïnstalleerd:  

-   De computer opnieuw opstarten in Windows PE  

    > [!IMPORTANT]  
    >  U moet een opstartinstallatiekopie met Windows PE 4 of hoger gebruiken om BitLocker vooraf in te richten. Zie voor meer informatie over ondersteunde Windows PE-versies in Configuration Manager [afhankelijkheden extern aan Configuration Manager](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_ExternalDependencies).  

-   De vaste schijf partitioneren en formatteren  

-   BitLocker vooraf inrichten  

-   Windows 7 met specifieke besturingssysteem- en netwerkinstellingen installeren  

-   Een sleutelbeveiliging aan BitLocker toevoegen  

 In Configuration Manager, de aanbevolen manier om BitLocker vooraf in te richten op een harde schijf en Windows 7 te installeren wordt een nieuwe takenreeks maken en selecteer **bestaand installatiekopiepakket installeren** van de **nieuwe Takenreeks maken** pagina van de **Wizard Takenreeks**. De wizard maakt de takenreeksstappen die in de volgende tabel worden vermeld.  

> [!NOTE]  
>  Er zijn mogelijk extra stappen in de takenreeks afhankelijk van hoe de instellingen in de wizard zijn geconfigureerd. U hebt bijvoorbeeld mogelijk de stap **Windows-instellingen vastleggen** als u de optie **Windows-instellingen vastleggen** hebt geselecteerd op de pagina **Statusmigratie** van de wizard.  

|Takenreeksstap|Details|  
|------------------------|-------------|  
|BitLocker uitschakelen|Met deze stap wordt BitLocker-versleuteling uitgeschakeld, als deze momenteel is ingeschakeld. Zie voor meer informatie [BitLocker uitschakelen](../understand/task-sequence-steps.md#BKMK_DisableBitLocker).|  
|Computer opnieuw opstarten in Windows PE|Met deze stap wordt de computer opnieuw opgestart in Windows PE door het uitvoeren van de opstartinstallatiekopie die aan de takenreeks is toegewezen. U moet een opstartinstallatiekopie met Windows PE 4 of hoger gebruiken om BitLocker vooraf in te richten. Zie voor meer informatie [Computer opnieuw opstarten](../understand/task-sequence-steps.md#BKMK_RestartComputer).|  
|Schijf 0 - BIOS partitioneren<br /><br /> Schijf 0 - UEFI partitioneren|Met deze stappen wordt de opgegeven schijf op de doelcomputer met behulp van BIOS of UEFI geformatteerd en gepartitioneerd. De takenreeks maakt gebruik van UEFI wanneer gedetecteerd wordt dat de doelcomputer zich in UEFI-modus bevindt. Zie voor meer informatie [schijf formatteren en partitioneren](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk).|  
|BitLocker vooraf inrichten|Met deze stap wordt BitLocker op een station ingeschakeld in Windows PE. Alleen de gebruikte schijfruimte wordt versleuteld. Versleuteling gaat erg snel omdat de vaste schijf bij de vorige stap is gepartitioneerd en geformatteerd en alle gegevens zijn gewist. Zie voor meer informatie [BitLocker vooraf inrichten](../understand/task-sequence-steps.md#BKMK_PreProvisionBitLocker).|  
|Besturingssysteem toepassen|In deze stap wordt het antwoordbestand voorbereid dat wordt gebruikt bij het installeren van het besturingssysteem op de doelcomputer en wordt de takenreeksvariabele OSDTargetSystemDrive ingesteld op de stationsletter van de partitie die de besturingssysteembestanden bevat. Het antwoordbestand en de variabele worden gebruikt in de Windows-installatie en ConfigMgr-stap om het besturingssysteem te installeren. Zie [Installatiekopie van het besturingssysteem toepassen](../understand/task-sequence-steps.md#BKMK_ApplyOperatingSystemImage) voor meer informatie.|  
|Windows-instellingen toepassen|In deze stap worden Windows-instellingen aan het antwoordbestand toegevoegd. Het antwoordbestand wordt gebruikt in de Windows-installatie en ConfigMgr-stap om het besturingssysteem te installeren. Zie voor meer informatie [Windows-instellingen toepassen](../understand/task-sequence-steps.md#BKMK_ApplyWindowsSettings).|  
|Netwerkinstellingen toepassen|In deze stap worden netwerkinstellingen aan het antwoordbestand toegevoegd. Het antwoordbestand wordt gebruikt in de Windows-installatie en ConfigMgr-stap om het besturingssysteem te installeren. Zie voor meer informatie [stap netwerkinstellingen toepassen](../understand/task-sequence-steps.md#BKMK_ApplyNetworkSettings).|  
|Apparaatstuurprogramma's toepassen|In deze stap worden compatibele stuurprogramma's gezocht en geïnstalleerd als onderdeel van de implementatie van het besturingssysteem. Zie voor meer informatie [stuurprogramma's automatisch toepassen](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers).|  
|Windows en ConfigMgr installeren|In deze stap wordt de overgang van Windows PE naar het nieuwe besturingssysteem uitgevoerd. Deze takenreeksstap is een vereist onderdeel van iedere besturingssysteemimplementatie. Het Configuration Manager-client installeert met het nieuwe besturingssysteem en bereidt de takenreeks op uitvoering in het nieuwe besturingssysteem. Zie voor meer informatie [Windows en ConfigMgr installeren](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).|  
|BitLocker inschakelen|In deze stap wordt BitLocker-versleuteling op de vaste schijf ingeschakeld en de sleutelbeveiligingen ingesteld. Deze stap verloopt erg snel omdat de vaste schijf vooraf is ingericht met BitLocker. Windows 7 vereist dat u een sleutelbeveiliging toevoegt. Als u deze stap niet uitvoert, kunt u het opdrachtregelprogramma manage-bde.exe uitvoeren om een sleutelbeveiliging in te stellen. Zie voor meer informatie [BitLocker inschakelen](../understand/task-sequence-steps.md#BKMK_EnableBitLocker).|  

