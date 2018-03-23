---
title: PXE gebruiken voor OSD via het netwerk
titleSuffix: Configuration Manager
description: Gebruik OS PXE geïnitieerde implementaties te vernieuwen besturingssysteem van een computer of een nieuwe versie van Windows op een nieuwe computer installeren.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 310807547df9fdb2ccd4f0098eec6b0b7ccca996
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De van de Preboot-uitvoeringsomgeving (PXE)-geïnitieerd OS implementaties in Configuration Manager, kunnen clients vragen en implementeren van besturingssystemen via het netwerk. In dit implementatiescenario verzendt u de installatiekopie van het besturingssysteem en de opstartinstallatiekopieën naar een distributiepunt met PXE-functionaliteit.

> [!NOTE]  
>  Bij het maken van een implementatie van het besturingssysteem die alleen x64 doelen BIOS-computers, zowel de x64 opstartinstallatiekopie x86 als de opstartinstallatiekopie moet beschikbaar zijn op het distributiepunt.

U kunt OS PXE geïnitieerde implementaties in de volgende scenario's:

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

Voer de stappen in een van de implementatiescenario's voor OS en gebruik vervolgens de secties in dit artikel om voor te bereiden voor PXE-geïnitieerde implementaties.



##  <a name="BKMK_Configure"></a> Ten minste één bestaand distributiepunt configureren voor de acceptatie van PXE-aanvragen
Voor het implementeren van besturingssystemen aan Configuration Manager-clients die PXE-opstartaanvragen maken, moet u een of meer distributiepunten om PXE-aanvragen te accepteren. Zodra u het distributiepunt configureert, reageert op PXE-opstartaanvragen en bepaalt de juiste implementatieactie te laten worden. Zie voor meer informatie [installeren of wijzigen van een distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#pxe).  



## <a name="prepare-a-pxe-enabled-boot-image"></a>Een opstartinstallatiekopie die geschikt is voor gebruik met PXE voorbereiden
Voor het gebruik van PXE voor het implementeren van een besturingssysteem, moet u x86- en x64 opstartinstallatiekopieën met PXE-functionaliteit die is gedistribueerd naar een of meer PXE-ingeschakelde distributiepunten hebben. U kunt als volgt PXE inschakelen voor een opstartinstallatiekopie en deze distribueren naar distributiepunten:

-   Als u PXE voor een opstartinstallatiekopie selecteert **deze opstartinstallatiekopie implementeren vanaf het distributiepunt met PXE-functionaliteit** van de **gegevensbron** tabblad in de eigenschappen van de opstartinstallatiekopie.

-   Als u de eigenschappen voor de opstartinstallatiekopie wijzigt, moet opnieuw de opstartinstallatiekopie naar distributiepunten distribueren. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).



##  <a name="BKMK_PXEExclusionList"></a> Een uitsluitingslijst voor PXE-implementaties maken
Wanneer u besturingssystemen met PXE implementeert, kunt u een uitsluitingslijst maken op elk distributiepunt. De MAC-adressen toevoegen aan de uitsluitingslijst van de computers die u wilt dat het distributiepunt te negeren. De takenreeksen voor besturingssysteemimplementaties die Configuration Manager voor PXE-implementatie gebruikt ontvangen niet door genoemde computers.

#### <a name="to-create-the-exclusion-list"></a>De uitsluitingslijst maken

1.  Maak een tekstbestand op het distributiepunt met PXE-functionaliteit. Geef dit tekstbestand bijvoorbeeld de naam **pxeExceptions.txt**.

2.  Gebruik een teksteditor zoals Kladblok, en voeg de MAC-adressen van de computers moeten worden genegeerd door het distributiepunt met PXE-functionaliteit. Scheid de MAC-adressen met een dubbele punt van elkaar en geef elk adres op een aparte regel op. Bijvoorbeeld: `01:23:45:67:89:ab`

3.  Bewaar het tekstbestand op de sitesysteemserver voor het distributiepunt met PXE-functionaliteit. Het tekstbestand dat kan worden opgeslagen op een willekeurige locatie op de server.

4.  Bewerk het register van het distributiepunt PXE-functionaliteit maken een **MACIgnoreListFile** registersleutel. De string-waarde van het volledige pad voor het tekstbestand op de sitesysteemserver PXE-ingeschakelde distributiepunt toevoegen. Gebruik het volgende registerpad:

     **HKLM\Software\Microsoft\SMS\DP**  

    > [!WARNING]  
    >  Als u de Register-Editor onjuist gebruikt, kunt u ernstige problemen waarvoor u het besturingssysteem opnieuw installeren kan veroorzaken. Microsoft biedt geen garantie dat u problemen kunt oplossen die veroorzaakt worden door onjuist gebruik van de Registry Editor. Gebruik de Registry Editor op eigen risico.

     Het is niet nodig om de server opnieuw te starten nadat u deze wijziging hebt aangebracht aan het register.



## <a name="manage-duplicate-hardware-identifiers"></a>Dubbele hardware-id's beheren
Configuration Manager kunnen meerdere computers herkennen als hetzelfde apparaat als ze dubbele SMBIOS-kenmerken hebben of een gedeelde netwerkadapter wordt gebruikt. U kunt deze problemen verhelpen door het beheer van dubbele hardware-id's in de hiërarchie-instellingen. Zie voor meer informatie [beheren dubbele hardware-id's](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).



##  <a name="BKMK_RamDiskTFTP"></a>RamDisk TFTP-blokgrootte en venstergrootte
U kunt de RamDisk TFTP-blok en het venster grootten voor distributiepunten met PXE-functionaliteit kunt aanpassen. Als u uw netwerk hebt aangepast, kan een groot blok of het venster downloaden van de opstartinstallatiekopie mislukt met een time-outfout veroorzaken. De RamDisk TFTP-blok en het venster Grootte-aanpassingen kunnen u TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten. Om te bepalen welke configuratie is het meest efficiënt, test u de aangepaste instellingen in uw omgeving. Zie voor meer informatie [de RamDisk TFTP-blokgrootte en venstergrootte op distributiepunten met PXE-functionaliteit aanpassen](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).



## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren
Voor het gebruik van een met PXE geïnitieerde besturingssysteemimplementatie, de implementatie zodat het besturingssysteem beschikbaar is voor PXE-opstartaanvragen te configureren. Beschikbare besturingssystemen te configureren op de **implementatie-instellingen** tabblad in de implementatie-eigenschappen. Voor de **toegankelijk maken voor de volgende** instelt, selecteert u een van de volgende opties:

-   Configuration Manager-clients, media en PXE

-   Alleen media en PXE

-   Alleen media en PXE (verborgen)



##  <a name="BKMK_Deploy"></a> De takenreeks implementeren
Het besturingssysteem implementeren naar een doelverzameling. Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie. Wanneer u besturingssystemen met PXE implementeert, kunt u configureren of de implementatie vereist of beschikbaar is.

-   **Vereiste implementatie**: Implementaties gebruik PXE zonder tussenkomst van de gebruiker vereist. De gebruiker overslaan niet de PXE-opstartprocedure. Echter, als de gebruiker de PXE-opstart annuleert voordat het distributiepunt reageert, wordt niet het besturingssysteem geïmplementeerd.

-   **Beschikbare implementatie**: Beschikbare implementaties moeten de gebruiker aanwezig zijn op de doelcomputer. Een gebruiker moet op de F12-toets om de PXE-opstartproces voort te klikken. Als een gebruiker niet aanwezig op F12 te drukken, start de computer op in het huidige besturingssysteem of van de volgende beschikbare opstartapparaat.

U kunt een vereiste PXE-implementatie opnieuw implementeren door de status van de laatste PXE-implementatie toegewezen aan een Configuration Manager-verzameling of computer te wissen. Voor meer informatie over de **wissen vereiste PXE-implementaties** actie, Zie [clients beheren](/sccm/core/clients/manage/manage-clients#BKMK_ManagingClients_DevicesNode) of [verzamelingen beheren](/sccm/core/clients/manage/collections/manage-collections#how-to-manage-device-collections). Deze actie wordt de status van die implementatie opnieuw ingesteld en de meest recente vereiste implementaties wordt opnieuw geïnstalleerd.

> [!IMPORTANT]
> Het PXE-protocol is niet veilig. Zorg dat de PXE-server en de PXE-client zich op een fysiek beveiligd netwerk (bijvoorbeeld in een datacentrum) bevinden om onbevoegde toegang tot uw site te voorkomen.



##  <a name="how-is-the-boot-image-selected-for-clients-booting-with-pxe"></a>Hoe wordt de opstartinstallatiekopie geselecteerd voor clients met PXE wordt opgestart?
Wanneer een client met PXE wordt opgestart, biedt Configuration Manager de client aan een opstartinstallatiekopie te gebruiken. Configuration Manager maakt gebruik van een opstartinstallatiekopie met een overeenkomst exact architectuur. Als u een opstartinstallatiekopie met de exacte architectuur niet beschikbaar is, wordt in Configuration Manager een opstartinstallatiekopie met een compatibele architectuur gebruikt. De volgende lijst bevat informatie over hoe een opstartinstallatiekopie voor opstarten met PXE-clients wordt geselecteerd.
1. Configuration Manager zoekt in de sitedatabase voor de systeem-record die overeenkomt met de MAC-adres of SMBIOS van de client die probeert op te starten.  

    > [!NOTE]
    > Als een computer die is toegewezen aan een site met PXE voor een andere site opstart, het beleid niet zichtbaar voor de computer. Bijvoorbeeld, als een client al aan een site toegewezen is, het beheerpunt en distributiepunt voor site B niet toegang kunnen krijgen tot de beleidsregels van site A. De client niet met succes PXE-opstart.

2. Configuration Manager zoekt naar takenreeksen die zijn geïmplementeerd voor de systeem-record gevonden in stap 1.

3. In de lijst met takenreeksen gevonden in stap 2, zoekt Configuration Manager naar een installatiekopie die overeenkomt met de architectuur van de client die probeert op te starten. Als een opstartinstallatiekopie met dezelfde architectuur wordt gevonden, wordt die installatiekopie wordt gebruikt.

4. Als u een opstartinstallatiekopie is niet gevonden met dezelfde architectuur, zoekt de Configuration Manager een opstartinstallatiekopie die compatibel is met de architectuur van de client. Het lijkt erop in de lijst met takenreeksen gevonden in stap 2. Bijvoorbeeld, is een 64-bits-client compatibel met 32-bits en 64-bits installatiekopieën. Een 32-bits-client is compatibel met alleen 32-bits installatiekopieën. Een UEFI-client is compatibel met alleen 64-bits installatiekopieën.
