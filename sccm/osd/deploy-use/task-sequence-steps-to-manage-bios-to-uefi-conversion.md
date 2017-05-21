---
title: Takenreeksstappen voor het beheren van BIOS UEFI conversie | Configuration Manager
description: Informatie over het aanpassen van een takenreeks voor implementatie van besturingssysteem om voor te bereiden overgang naar UEFI een FAT32-partitie.
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd3df04a-902f-4e91-89eb-5584b47d9efa
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: 528ce515c86c4e778532290026a90a46476c4576
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Takenreeksstappen voor het beheren van BIOS UEFI-conversie
Windows 10 biedt veel nieuwe beveiligingsfuncties die UEFI-apparaten vereisen. U hebt mogelijk moderne Windows-pc's die ondersteuning voor UEFI, maar de verouderde BIOS gebruikt. Een apparaat converteren naar UEFI is vereist dat u aan de slag met elke PC Partitioneer de harde schijf en opnieuw configureren van de firmware. Met behulp van takenreeksen in Configuration Manager, kunt u voorbereiden op een harde schijf BIOS UEFI conversie van BIOS converteren naar UEFI als onderdeel van de in-place upgrade en UEFI worden verzameld als onderdeel van de hardware-inventaris.

## <a name="hardware-inventory-collects-uefi-information"></a>Hardware-inventaris verzamelt informatie UEFI
Vanaf versie 1702 wordt een nieuwe hardware inventariseren klasse (**SMS_Firmware**) en de eigenschap (**UEFI**) zijn beschikbaar om te bepalen of een computer in UEFI-modus start. Wanneer een computer in UEFI-modus wordt gestart de **UEFI** eigenschap is ingesteld op **waar**. Dit is standaard ingeschakeld in de hardware-inventaris. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="create-a-custom-task-sequence-to-prepare-the-hard-drive-for-bios-to-uefi-conversion"></a>Maak een aangepaste takenreeks de harde schijf om voor te bereiden BIOS UEFI-conversie
U start in Configuration Manager versie 1610, nu kunt u een takenreeks voor implementatie van besturingssysteem met een nieuwe variabele TSUEFIDrive, zodat de **Computer opnieuw opstarten** stap bereidt een FAT32-partitie op de harde schijf voor de overgang naar UEFI. De volgende procedure geeft een voorbeeld van hoe u takenreeksstappen voor het voorbereiden van de harde schijf voor het BIOS UEFI conversie kunt maken.

### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>De FAT32-partitie voor de conversie naar UEFI voorbereiden:
In een bestaande takenreeks om een besturingssysteem te installeren, moet u een nieuwe groep met stappen om te doen het BIOS UEFI conversie toevoegen.

1. Een takenreeksgroep maken na de stappen voor het vastleggen van bestanden en instellingen en voor de stappen om het besturingssysteem te installeren. Maak bijvoorbeeld een groep na de **vastleggen van bestanden en instellingen** groep met de naam **BIOS op UEFI**.
2. Op de **opties** tabblad toevoegen van de nieuwe groep, een nieuwe takenreeksvariabele als een voorwaarde waar **_SMSTSBootUEFI** is **niet gelijk aan** naar **waar**. Dit voorkomt dat de stappen in de groep wordt uitgevoerd wanneer een computer al in UEFI-modus is.

  ![BIOS UEFI-groep](../../core/get-started/media/BIOS-to-UEFI-group.png)
3. Voeg onder de nieuwe groep, de **Computer opnieuw opstarten** takenreeksstap. In **aan te geven wat om uit te voeren na opnieuw opstarten**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  
4. Op de **opties** tabblad, het toevoegen van een takenreeksvariabele worden uitgevoerd als een voorwaarde waar **_SMSTSInWinPE gelijk is aan false**. Hierdoor wordt voorkomen dat deze stap uitvoeren als de computer al in Windows PE is.

  ![Stap van de Computer opnieuw opstarten](../../core/get-started/media/restart-in-windows-pe.png)
5. Een stap voor het starten van de OEM-hulpprogramma dat de firmware van BIOS wordt converteren naar UEFI toevoegen. Dit is doorgaans een **opdrachtregel uitvoeren** takenreeksstap met een opdrachtregel te gebruiken om te starten van de OEM-hulpprogramma.
6. Voeg de schijf formatteren en partitioneren takenreeksstap toe die wordt partitioneer en formatteer de vaste schijf. In de stap door het volgende te doen:
  1. Maak de FAT32-partitie gebruikt die wordt omgezet in UEFI voordat het besturingssysteem wordt geïnstalleerd. Kies **GPT** voor **type schijf**.
    ![Formatteren en partitioneren schijf stap](../media/format-and-partition-disk.png)
  2. Ga naar de eigenschappen voor de partitie FAT32. Voer **TSUEFIDrive** in de **variabele** veld. Als de takenreeks deze variabele detecteert, wordt deze voorbereiden voor de overgang UEFI voordat u de computer opnieuw opstart.
    ![Partitie-eigenschappen](../../core/get-started/media/partition-properties.png)
  3. Maak een NTFS-partitie die de takenreeks-engine gebruikt om op te slaan de status en voor het opslaan van logboekbestanden.
7. Voeg de **Computer opnieuw opstarten** takenreeksstap. In **aan te geven wat om uit te voeren na opnieuw opstarten**, selecteer **de opstartinstallatiekopie toegewezen aan deze takenreeks is geselecteerd** Start de computer in Windows PE.  

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Omzetten van BIOS UEFI tijdens een upgrade ter plekke
Windows 10 beveiligingsbeheerder Update introduceert een eenvoudige conversie-hulpprogramma dat automatiseert het proces voor het partitioneren van de harde schijf voor UEFI-functionaliteit hardware en het hulpprogramma conversie integreert in de Windows 7 voor Windows 10 in-place upgradeproces. Wanneer u dit hulpprogramma worden gecombineerd met de upgrade besturingssysteemtaaksequentie en het OEM-hulpprogramma dat de firmware van BIOS naar UEFI converteert, kunt u uw computers converteren van BIOS naar UEFI tijdens een upgrade ter plekke met Windows 10 beveiligingsbeheerder Update.

**Vereisten voor**:
- Update voor Windows 10 beveiligingsbeheerder
- Computers die ondersteuning bieden voor UEFI
- De OEM-hulpprogramma dat firmware van de computer in BIOS naar UEFI converteert

### <a name="to-convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Converteren van BIOS naar UEFI tijdens een upgrade ter plekke
1. Maak een upgrade besturingssysteemtaaksequentie die een in-place upgrade naar Windows 10 beveiligingsbeheerder Update uitvoert.
2. De takenreeks te bewerken. In de **na verwerking groep**, de volgende takenreeksstappen toevoegen:
   1. Toevoegen van algemeen, een **opdrachtregel uitvoeren** stap. Voegt u de opdrachtregel voor de MBR2GPT hulpprogramma dat zet een schijf van MBR naar GPT zonder aanpassen of verwijderen van gegevens van de schijf. In de opdrachtregel, typt u het volgende:  **MBR2GPT/Convert /disk:0 /AllowFullOS**. U kunt er ook voor kiezen om uit te voeren van de MBR2GPT. EXE-hulpprogramma in de Windows PE in plaats van in het volledige besturingssysteem. U kunt dit doen door het toevoegen van een stap om de computer voordat de stap uit te voeren van de MBR2GPT WinPE opnieuw te starten. EXE hulpprogramma en de optie /AllowFullOS verwijderen vanaf de opdrachtregel. Zie voor meer informatie over het hulpprogramma en de beschikbare opties [MBR2GPT. EXE](https://technet.microsoft.com/itpro/windows/deploy/mbr-to-gpt).
   2. Een stap voor het starten van de OEM-hulpprogramma dat de firmware van BIOS wordt converteren naar UEFI toevoegen. Dit is doorgaans een takenreeksstap opdrachtregel uitvoeren met een opdrachtregel te gebruiken om te starten van de OEM-hulpprogramma.
   3. Toevoegen van algemeen, de **Computer opnieuw opstarten** stap. Geef voor wat moet worden uitgevoerd na opnieuw opstarten, selecteer **het momenteel geïnstalleerde standaardbesturingssysteem**.
3. De takenreeks implementeert.

