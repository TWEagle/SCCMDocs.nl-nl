---
title: PXE gebruiken om Windows te implementeren via het netwerk | Microsoft Docs
description: "Gebruik PXE geïnitieerde besturingssysteemimplementaties te vernieuwen besturingssysteem van een computer of een nieuwe versie van Windows op een nieuwe computer installeren."
ms.custom: na
ms.date: 06/15/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
caps.latest.revision: 19
caps.handback.revision: 0
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4c46bfab9b40b29654f4e883817a5508ab25b74
ms.openlocfilehash: b88ab3799027c78a8c605e934b247097b31e1d21
ms.contentlocale: nl-nl
ms.lasthandoff: 06/28/2017


---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De van de Preboot-uitvoeringsomgeving (PXE) gestart implementaties van besturingssystemen in System Center Configuration Manager laat client computers aanvragen en implementeren van besturingssystemen via het netwerk. In dit implementatiescenario verzendt u de installatiekopie van het besturingssysteem en de x86- en x64 Windows PE-opstartinstallatiekopieën naar een distributiepunt dat is geconfigureerd om PXE-opstartaanvragen te accepteren.

> [!NOTE]  
>  Bij het maken van een besturingssysteemimplementatie die doelen alleen x64 BIOS-computers, zowel de x64 opstartinstallatiekopie x86 als de opstartinstallatiekopie moet beschikbaar zijn op het distributiepunt.

U kunt besturingssysteemimplementaties die worden uitgevoerd met PXE gebruiken bij de volgende implementatiescenario’s voor besturingssystemen:

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

Voer de stappen in een van de implementatiescenario's voor besturingssystemen en gebruik vervolgens de volgende secties om voor te bereiden voor PXE-geïnitieerde implementaties.

##  <a name="BKMK_Configure"></a> Ten minste één bestaand distributiepunt configureren voor de acceptatie van PXE-aanvragen
Gebruiken om besturingssystemen te implementeren op clients die PXE-opstartaanvragen maken, een of meer distributiepunten die zijn geconfigureerd om te reageren op de PXE-opstartaanvragen. Zie voor de stappen in te schakelen van PXE voor een distributiepunt [distributiepunten configureren voor de acceptatie van PXE-aanvragen](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint).

## <a name="prepare-a-pxe-enabled-boot-image"></a>Een opstartinstallatiekopie die geschikt is voor gebruik met PXE voorbereiden
Als u PXE wilt gebruiken voor het implementeren van besturingssystemen, moet u een x86- en x64-opstartinstallatiekopie die geschikt zijn voor gebruik met PXE hebben gedistribueerd naar een of meer distributiepunten met PXE-functionaliteit. U kunt als volgt PXE inschakelen voor een opstartinstallatiekopie en deze distribueren naar distributiepunten:

-   Als u PXE voor een opstartinstallatiekopie selecteert **deze opstartinstallatiekopie implementeren vanaf het distributiepunt met PXE-functionaliteit** van de **gegevensbron** tabblad in de eigenschappen van de opstartinstallatiekopie.

-   Als u de eigenschappen voor de opstartinstallatiekopie wijzigt, moet opnieuw de opstartinstallatiekopie naar distributiepunten distribueren. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).

##  <a name="BKMK_PXEExclusionList"></a> Een uitsluitingslijst voor PXE-implementaties maken
Wanneer u besturingssystemen met PXE implementeert, kunt u een uitsluitingslijst maken op elk distributiepunt. De MAC-adressen toevoegen aan de uitsluitingslijst van de computers die u wilt dat het distributiepunt te negeren. Genoemde computers ontvangt geen de takenreeksen voor besturingssysteemimplementaties die Configuration Manager voor PXE-implementaties gebruikt.

#### <a name="to-create-the-exclusion-list"></a>De uitsluitingslijst maken

1.  Maak een tekstbestand op het distributiepunt met PXE-functionaliteit. Geef dit tekstbestand bijvoorbeeld de naam **pxeExceptions.txt**.

2.  Gebruik een teksteditor zoals Kladblok, en voeg de MAC-adressen van de computers moeten worden genegeerd door het distributiepunt met PXE-functionaliteit. Scheid de MAC-adressen met een dubbele punt van elkaar en geef elk adres op een aparte regel op. Bijvoorbeeld: `01:23:45:67:89:ab`

3.  Bewaar het tekstbestand op de sitesysteemserver voor het distributiepunt met PXE-functionaliteit. Het tekstbestand dat kan worden opgeslagen op een willekeurige locatie op de server.

4.  Bewerk het register van het distributiepunt PXE-functionaliteit maken een **MACIgnoreListFile** registersleutel. De string-waarde van het volledige pad voor het tekstbestand op de sitesysteemserver PXE-ingeschakelde distributiepunt toevoegen. Gebruik het volgende registerpad:

     **HKLM\Software\Microsoft\SMS\DP**  

    > [!WARNING]  
    >  Als u de Register-Editor onjuist gebruikt, kunt u ernstige problemen waarvoor u het besturingssysteem opnieuw installeren kan veroorzaken. Microsoft biedt geen garantie dat u problemen kunt oplossen die veroorzaakt worden door onjuist gebruik van de Registry Editor. Gebruik de Registry Editor op eigen risico.

     Het is niet nodig om de server opnieuw te starten nadat u deze wijziging hebt aangebracht aan het register.

##  <a name="BKMK_RamDiskTFTP"></a>RamDisk TFTP-blokgrootte en venstergrootte
U kunt de RamDisk TFTP-blokgrootte en begin in Configuration Manager versie 1606, de grootte van het venster voor distributiepunten met PXE-functionaliteit aanpassen. Als u uw netwerk hebt aangepast, kan dit ertoe leiden dat het downloaden van de opstartinstallatiekopie mislukt met een time-outfout omdat het blok of het venster te groot is. Met RamDisk TFTP-blok- en venstergrootteaanpassing kunt u het TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten. De aangepaste instellingen in uw omgeving om te bepalen van de meest efficiënte manier testen. Zie voor meer informatie [de RamDisk TFTP-blokgrootte en venstergrootte op distributiepunten met PXE-functionaliteit aanpassen](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren
Als u gebruik wilt maken van een besturingssysteemimplementatie die met PXE wordt uitgevoerd, moet u de implementatie zo configureren dat het besturingssysteem beschikbaar wordt gesteld voor PXE-opstartaanvragen. U kunt beschikbare besturingssystemen configureren op de **implementatie-instellingen** pagina van de Wizard Software implementeren of de **implementatie-instellingen** tabblad in de eigenschappen voor de implementatie. Configureer een van de volgende waarden voor de instelling **Toegankelijk maken voor de volgende** :

-   Configuration Manager-clients, media en PXE

-   Alleen media en PXE

-   Alleen media en PXE (verborgen)

##  <a name="BKMK_Deploy"></a> De takenreeks implementeren
Implementeer het besturingssysteem in een doelverzameling. Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie. Wanneer u besturingssystemen met PXE implementeert, kunt u configureren of de implementatie vereist of beschikbaar is.

-   **Vereiste implementatie**: Implementaties gebruik PXE zonder tussenkomst van de gebruiker vereist. De gebruiker niet mogelijk voor het overslaan van de PXE-opstart. Als de gebruiker de PXE-opstart annuleert voordat het distributiepunt reageert, won't u het besturingssysteem geïmplementeerd.

-   **Beschikbare implementatie**: Beschikbare implementaties vereisen dat de gebruiker aanwezig op de doelcomputer is zodat ze op de F12-toets om de PXE-opstartproces voort te kunnen drukken. Als de gebruiker niet aanwezig is om op F12 te drukken, wordt de computer opgestart met het huidige besturingssysteem of vanaf het volgende beschikbare opstartapparaat.

U kunt een vereiste PXE-implementatie opnieuw implementeren door de status van de laatste PXE-implementatie toegewezen aan een Configuration Manager-verzameling of computer te wissen. Deze actie wordt de status van die implementatie opnieuw ingesteld en de meest recente vereiste implementaties wordt opnieuw geïnstalleerd.

> [!IMPORTANT]
> Het PXE-protocol is niet veilig. Zorg dat de PXE-server en de PXE-client zich op een fysiek beveiligd netwerk (bijvoorbeeld in een datacentrum) bevinden om onbevoegde toegang tot uw site te voorkomen.

##  <a name="how-is-the-boot-image-selected-for-clients-booting-with-pxe"></a>Hoe wordt de opstartinstallatiekopie geselecteerd voor clients met PXE wordt opgestart?
Wanneer een client met PXE wordt opgestart, biedt Configuration Manager de client aan een opstartinstallatiekopie te gebruiken. Vanaf Configuration Manager versie 1606, Configuration Manager maakt gebruik van een opstartinstallatiekopie met een overeenkomst exact architectuur. Als u een opstartinstallatiekopie met de exacte architectuur niet beschikbaar is, wordt in Configuration Manager een opstartinstallatiekopie met een compatibele architectuur gebruikt. De volgende lijst bevat informatie over hoe een opstartinstallatiekopie voor opstarten met PXE-clients wordt geselecteerd.
1. Configuration Manager zoekt in de sitedatabase voor de systeem-record die overeenkomt met de MAC-adres of SMBIOS van de client die probeert op te starten.  

    > [!NOTE]
    > Als een computer die is toegewezen aan een site met PXE voor een andere site opstart, het beleid niet zichtbaar voor de computer. Bijvoorbeeld, als een client al aan een site toegewezen is, het beheerpunt en distributiepunt voor site B niet mogelijk toegang hebben tot de beleidsregels van site A. De client niet het geval is dat PXE wordt opgestart.

2. Configuration Manager zoekt naar takenreeksen die zijn geïmplementeerd voor de systeem-record gevonden in stap 1.

3. In de lijst met takenreeksen gevonden in stap 2, zoekt Configuration Manager naar een installatiekopie die overeenkomt met de architectuur van de client die probeert op te starten. Als een opstartinstallatiekopie met dezelfde architectuur wordt gevonden, wordt die installatiekopie wordt gebruikt.

4. Als u een opstartinstallatiekopie is niet gevonden met dezelfde architectuur, zoekt de Configuration Manager een opstartinstallatiekopie die compatibel is met de architectuur van de client. Het lijkt erop in de lijst met takenreeksen gevonden in stap 2. Bijvoorbeeld, is een 64-bits-client compatibel met 32-bits en 64-bits installatiekopieën. Een 32-bits-client is compatibel met alleen 32-bits installatiekopieën. Een UEFI-client is compatibel met alleen 64-bits installatiekopieën.

