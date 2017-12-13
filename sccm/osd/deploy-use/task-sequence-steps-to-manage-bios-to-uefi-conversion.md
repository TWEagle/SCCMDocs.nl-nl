---
title: Takenreeksstappen voor het beheren van BIOS naar UEFI-conversie
titleSuffix: Configuration Manager
description: Informatie over het aanpassen van een takenreeks voor implementatie van besturingssysteem voorbereiden van een FAT32-partitie voor de overgang naar UEFI.
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd3df04a-902f-4e91-89eb-5584b47d9efa
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f2d53b7f525d4f827b78840a7f0d9482d203c08d
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Takenreeksstappen voor het beheren van BIOS naar UEFI-conversie
Windows 10 biedt veel nieuwe beveiligingsfuncties die UEFI-apparaten vereisen. U hebt mogelijk moderne Windows-pc's die UEFI ondersteunen, maar verouderd BIOS gebruikt. Een apparaat converteren naar UEFI is vereist dat u om te gaan op elke PC Partitioneer de harde schijf en de configuratie van de firmware. Met behulp van takenreeksen in Configuration Manager, kunt u een harde schijf voorbereiden voor BIOS UEFI conversie, BIOS converteren naar UEFI als onderdeel van de in-place upgrade en UEFI-informatie als onderdeel van de hardware-inventaris verzamelen.

## <a name="hardware-inventory-collects-uefi-information"></a>Hardware-inventaris verzamelt UEFI-informatie
Vanaf versie 1702 is een nieuwe voor hardware-inventarisatie klasse (**SMS_Firmware**) en de eigenschap (**UEFI**) zijn beschikbaar om te bepalen of een computer in UEFI-modus wordt gestart. Wanneer een computer in UEFI-modus is gestart de **UEFI** eigenschap is ingesteld op **TRUE**. Dit is standaard ingeschakeld in de hardware-inventaris. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="create-a-custom-task-sequence-to-prepare-the-hard-drive-for-bios-to-uefi-conversion"></a>Maak een aangepaste takenreeks de harde schijf om voor te bereiden BIOS naar UEFI-conversie
U start in Configuration Manager versie 1610, nu kunt u een takenreeks voor implementatie van besturingssysteem met een nieuwe variabele, TSUEFIDrive, zodat de **Computer opnieuw opstarten** stap bereidt een FAT32-partitie op de harde schijf voor de overgang naar UEFI. De volgende procedure bevat een voorbeeld van hoe u de stappen in de takenreeks de harde schijf voorbereiden voor de conversie van UEFI-BIOS kunt maken.

### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>De FAT32-partitie voor de conversie naar UEFI voorbereiden:
In een bestaande takenreeks om een besturingssysteem te installeren, wordt u een nieuwe groep met stappen om te doen het BIOS UEFI conversie toevoegen.

1. Maak een nieuwe takenreeksgroep na de stappen voor het vastleggen van bestanden en instellingen en voor de stappen voor het besturingssysteem installeren. Maakt bijvoorbeeld een groep na de **vastleggen van bestanden en instellingen** groep met de naam **BIOS-UEFI-**.
2. Op de **opties** tabblad van de nieuwe groep, een nieuwe takenreeksvariabele als een voorwaarde toevoegen waarbij **_SMSTSBootUEFI** is **niet gelijk aan** naar **true**. Dit voorkomt dat de stappen in de groep uitgevoerd wanneer een computer al in UEFI-modus is.

  ![BIOS UEFI-groep](../../core/get-started/media/BIOS-to-UEFI-group.png)
3. Voeg onder de nieuwe groep, de **Computer opnieuw opstarten** takenreeksstap. In **instellen wat moet worden uitgevoerd na herstart**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  
4. Op de **opties** tabblad, een takenreeksvariabele toevoegen als een voorwaarde waar **_SMSTSInWinPE gelijk is aan false**. Dit voorkomt dat deze stap uitvoert als de computer al in Windows PE is.

  ![Stap van de Computer opnieuw opstarten](../../core/get-started/media/restart-in-windows-pe.png)
5. Een stap voor het starten van de OEM-hulpprogramma dat de firmware van BIOS wordt converteren naar UEFI toevoegen. Dit wordt doorgaans een **opdrachtregel uitvoeren** takenreeksstap met een opdrachtregel het OEM-hulpprogramma starten.
6. De schijf formatteren en partitioneren takenreeksstap die partitioneren en formatteren van de harde schijf toevoegen. In de stap wordt het volgende doen:
  1. Maak de FAT32-partitie worden geconverteerd naar UEFI voordat het besturingssysteem wordt geïnstalleerd. Kies **GPT** voor **schijftype**.
    ![Formatteren en partitioneren schijf stap](../media/format-and-partition-disk.png)
  2. Ga naar de eigenschappen voor de FAT32-partitie. Voer **TSUEFIDrive** in de **variabele** veld. Wanneer de takenreeks deze variabele detecteert, bereidt het voor de overgang UEFI voordat de computer opnieuw wordt opgestart.
    ![Partitie-eigenschappen](../../core/get-started/media/partition-properties.png)
  3. Maak een NTFS-partitie met de engine voor takenreeksen op te slaan de status en voor het opslaan van logboekbestanden.
7. Voeg de **Computer opnieuw opstarten** takenreeksstap. In **instellen wat moet worden uitgevoerd na herstart**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Converteren van BIOS naar UEFI tijdens een upgrade ter plekke
Windows 10 auteurs Update introduceert een conversie van eenvoudige hulpprogramma dat automatiseert het proces voor het partitioneren van de harde schijf voor UEFI geschikte hardware en het hulpprogramma voor de conversie is geïntegreerd in de Windows 7 naar Windows 10 in-place upgradeproces. Wanneer u dit hulpprogramma worden gecombineerd met de upgradetakenreeks van uw besturingssysteem en het OEM-hulpprogramma dat de firmware van BIOS naar UEFI converteert, kunt u uw computers converteren vanuit BIOS naar UEFI tijdens een in-place upgrade naar de Update voor Windows 10 auteurs.

**Vereisten**:
- Bijwerken van Windows 10 maken
- Computers met UEFI ondersteunen
- OEM-hulpprogramma dat de firmware van de computer van BIOS naar UEFI converteert

### <a name="to-convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Converteren van BIOS naar UEFI tijdens een upgrade ter plekke
1. Maken van een besturingssysteemtakenreeks voor upgraden die een in-place upgrade naar Windows 10 auteurs Update uitvoert.
2. Een takenreeks bewerken. In de **groep na verwerking**, de volgende takenreeksstappen toevoegen:
   1. Toevoegen van algemeen, een **opdrachtregel uitvoeren** stap. Voegt u de opdrachtregel voor de MBR2GPT hulpprogramma dat zet een schijf van MBR naar GPT zonder te wijzigen of verwijderen van gegevens van de schijf. Op de opdrachtregel, typ het volgende:  **MBR2GPT/Convert /disk:0 /AllowFullOS**. U kunt ook de MBR2GPT uitvoeren. EXE-hulpprogramma in de Windows PE in plaats van in het volledige besturingssysteem. U kunt dit doen door een stap om opnieuw te starten van de computer in WinPE voordat de stap uit te voeren van de MBR2GPT toe te voegen. EXE-hulpprogramma en de optie /AllowFullOS verwijderen vanaf de opdrachtregel. Zie voor meer informatie over het hulpprogramma en de beschikbare opties [MBR2GPT. EXE](https://technet.microsoft.com/itpro/windows/deploy/mbr-to-gpt).
   2. Een stap voor het starten van de OEM-hulpprogramma dat de firmware van BIOS wordt converteren naar UEFI toevoegen. Dit is doorgaans een takenreeksstap in opdrachtregel uitvoeren met een opdrachtregel het OEM-hulpprogramma starten.
   3. Toevoegen van algemeen, de **Computer opnieuw opstarten** stap. Geef voor wat moet worden uitgevoerd na opnieuw opstarten, selecteer **het momenteel geïnstalleerde standaardbesturingssysteem**.
3. De takenreeks implementeert.
