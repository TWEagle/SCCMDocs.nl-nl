---
title: PXE gebruiken om Windows te implementeren via het netwerk | Microsoft-documenten
description: "Gebruik PXE geïnitieerde besturingssysteemimplementaties om te vernieuwen besturingssysteem van een computer of een nieuwe versie van Windows op een nieuwe computer installeren."
ms.custom: na
ms.date: 12/07/2016
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
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f44505c977b511223a083a960f871371c0ff133
ms.openlocfilehash: b22cdbd42693078caa47f41182ce73ea881c3515
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met PXE geïnitieerde besturingssysteemimplementaties in System Center Configuration Manager kunnen computers aanvragen en besturingssystemen implementeren via het netwerk. Bij deze besturingssysteemimplementaties worden de installatiekopie van het besturingssysteem en zowel de x86- als de x64-versie van de Windows PE-opstartinstallatiekopie verzonden naar een distributiepunt dat is geconfigureerd om PXE-opstartaanvragen te accepteren.  

> [!NOTE]  
>  Bij het maken van een implementatie voor een besturingssysteem die alleen is gericht op x64-BIOS-computers, moeten zowel de x 64-opstartinstallatiekopie als de x86-opstartinstallatiekopie beschikbaar zijn op het distributiepunt.  

 U kunt besturingssysteemimplementaties die worden uitgevoerd met PXE gebruiken bij de volgende implementatiescenario’s voor besturingssystemen:  

-   [Vernieuwen van een bestaande computer met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows installeren op een nieuwe computer (bare metal)](install-new-windows-version-new-computer-bare-metal.md)  

 Voer de stappen in een van de implementatiescenario’s voor besturingssystemen uit en bereid u vervolgens aan de hand van de volgende secties voor op implementaties die worden uitgevoerd met PXE.  

##  <a name="BKMK_Configure"></a> Ten minste één bestaand distributiepunt configureren voor de acceptatie van PXE-aanvragen  
 Om besturingssystemen te implementeren naar Configuration Manager-clients die PXE-opstartaanvragen maken, moet u een of meer distributiepunten die zijn geconfigureerd om te reageren op PXE-opstartaanvragen.  Zie voor stappen PXE moet worden ingeschakeld op een distributiepunt [configureren van distributiepunten voor de acceptatie van PXE-aanvragen](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint).  

## <a name="prepare-a-pxe-enabled-boot-image"></a>Een opstartinstallatiekopie die geschikt is voor gebruik met PXE voorbereiden  
 Als u PXE wilt gebruiken voor het implementeren van besturingssystemen, moet u een x86- en x64-opstartinstallatiekopie die geschikt zijn voor gebruik met PXE hebben gedistribueerd naar een of meer distributiepunten met PXE-functionaliteit. U kunt als volgt PXE inschakelen voor een opstartinstallatiekopie en deze distribueren naar distributiepunten:  

-   Als u PXE voor een opstartinstallatiekopie wilt inschakelen, selecteert u op het tabblad  **Gegevensbron** voor de eigenschappen van de opstartinstallatiekopie de optie **Deze opstartinstallatiekopie implementeren vanaf het PXE-distributiepunt** .  

-   Als u de eigenschappen voor de opstartinstallatiekopie wijzigt, moet u de opstartinstallatiekopie opnieuw naar de distributiepunten distribueren. Zie voor meer informatie [inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_PXEExclusionList"></a> Een uitsluitingslijst voor PXE-implementaties maken  
 Wanneer u PXE gebruikt voor het implementeren van besturingssystemen, kunt u voor elk distributiepunt een uitsluitingslijst maken zodat PXE-opstartaanvragen van computers die zijn opgenomen in de uitsluitingslijst worden genegeerd. De uitsluitingslijst bevat MAC-adressen van de computers die door het distributiepunt moeten worden genegeerd. Deze computers ontvangen niet de takenreeks voor implementatie die Configuration Manager voor PXE-implementatie gebruikt.  

 Gebruik de volgende stappen om de PXE-uitsluitingslijst te maken.  

#### <a name="to-create-the-exclusion-list"></a>De uitsluitingslijst maken  

1.  Maak een tekstbestand op het distributiepunt met PXE-functionaliteit. Geef dit tekstbestand bijvoorbeeld de naam **pxeExceptions.txt**.  

2.  Gebruik een standaardteksteditor (zoals Kladblok) en voeg de MAC-adressen toe van de computers die moeten worden genegeerd door het distributiepunt met PXE-functionaliteit. Scheid de MAC-adressen met een dubbele punt van elkaar en geef elk adres op een aparte regel op. Bijvoorbeeld: `01:23:45:67:89:ab`  

3.  Bewaar het tekstbestand op de sitesysteemserver voor het distributiepunt met PXE-functionaliteit. Het tekstbestand kan worden opgeslagen op elke locatie op de server.  

4.  Bewerk het register van het distributiepunt met PXE-functionaliteit om een **MACIgnoreListFile** -registersleutel te maken die de tekenreekswaarde bevat van het volledige pad naar de locatie van het tekstbestand op de sitesysteemserver voor het distributiepunt met PXE-functionaliteit. Gebruik het volgende registerpad:  

     **HKLM\Software\Microsoft\SMS\DP**  

    > [!WARNING]  
    >  Als u de Registry Editor onjuist gebruikt, kunt u ernstige problemen veroorzaken waardoor u mogelijk het besturingssysteem opnieuw zult moeten installeren. Microsoft biedt geen garantie dat u problemen kunt oplossen die veroorzaakt worden door onjuist gebruik van de Registry Editor. Gebruik de Registry Editor op eigen risico.  

     Het is niet nodig om de server opnieuw te starten nadat u deze wijziging hebt aangebracht aan het register.  

##  <a name="BKMK_RamDiskTFTP"></a>Blokgrootte RamDisk TFTP en venstergrootte  
U kunt de blokgrootte RamDisk TFTP en begin in Configuration Manager versie 1606, de grootte van het venster voor PXE-ingeschakelde distributiepunten aanpassen. Als u uw netwerk hebt aangepast, kan dit ertoe leiden dat het downloaden van de opstartinstallatiekopie mislukt met een time-outfout omdat het blok of het venster te groot is. Met RamDisk TFTP-blok- en venstergrootteaanpassing kunt u het TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten. U moet de aangepaste instellingen in uw omgeving testen om te bepalen het meest efficiënt is. Zie voor meer informatie [RamDisk TFTP blokgrootte en venstergrootte op PXE-ingeschakelde distributiepunten aanpassen](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren  
 Als u gebruik wilt maken van een besturingssysteemimplementatie die met PXE wordt uitgevoerd, moet u de implementatie zo configureren dat het besturingssysteem beschikbaar wordt gesteld voor PXE-opstartaanvragen. U kunt dit configureren op de pagina **Implementatie-instellingen** van de wizard Software implementeren of op het tabblad **Implementatie-instellingen** in de eigenschappen voor de implementatie.  Configureer een van de volgende waarden voor de instelling **Toegankelijk maken voor de volgende** :  

-   Configuration Manager-clients, media en PXE  

-   Alleen media en PXE  

-   Alleen media en PXE (verborgen)  

##  <a name="BKMK_Deploy"></a> De takenreeks implementeren  
 Implementeer het besturingssysteem in een doelverzameling. Zie [Een takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS) voor meer informatie. Wanneer u besturingssystemen met PXE implementeert, kunt u configureren of de implementatie vereist of beschikbaar is.  

-   **Vereiste implementatie**: Vereiste implementaties wordt PXE gebruikt zonder tussenkomst van de gebruiker. De gebruiker kan de PXE-opstartbewerking niet omzeilen. Als de gebruiker de PXE-opstartbewerking echter annuleert voordat het distributiepunt reageert, wordt het besturingssysteem niet geïmplementeerd.  

-   **Beschikbare implementatie**: Beschikbare implementaties moet dat de gebruiker aanwezig op de doelcomputer is zodat ze drukt u op de F12-toets om door te gaan van de PXE-opstartproces. Als de gebruiker niet aanwezig is om op F12 te drukken, wordt de computer opgestart met het huidige besturingssysteem of vanaf het volgende beschikbare opstartapparaat.  

 U kunt een vereiste PXE-implementatie opnieuw implementeren door de status van de laatste PXE-implementatie toegewezen aan een Configuration Manager-verzameling of een computer te wissen. Met deze actie wordt de status van die implementatie opnieuw ingesteld en worden de meest recente vereiste implementaties opnieuw geïmplementeerd.  

> [!IMPORTANT]  
>  Het PXE-protocol is niet veilig. Zorg dat de PXE-server en de PXE-client zich op een fysiek beveiligd netwerk (bijvoorbeeld in een datacentrum) bevinden om onbevoegde toegang tot uw site te voorkomen.  

##  <a name="how-is-the-boot-image-selected-for-clients-booting-with-pxe"></a>Hoe wordt de opstartinstallatiekopie geselecteerd voor opstarten met PXE-clients?
Wanneer een client met PXE wordt opgestart, geeft Configuration Manager de client aan een opstartinstallatiekopie te gebruiken. Vanaf versie 1606 van Configuration Manager, Configuration Manager gebruikt een opstartinstallatiekopie met een exacte architectuur overeenkomst als deze beschikbaar is. Als een installatiekopie met de exacte architectuur niet beschikbaar is, Configuration Manager maakt gebruik van een opstartinstallatiekopie met een compatibele architectuur. De volgende lijst bevat meer informatie over hoe een opstartinstallatiekopie is geselecteerd voor opstarten met PXE-clients.
1. Configuration Manager zoekt in de sitedatabase voor de systeem-record die overeenkomt met de MAC-adres of SMBIOS van de client die probeert te starten.
    > [!NOTE]
    > Als een computer die is toegewezen aan een site met PXE voor een site differenet opstart, zijn het beleid niet zichtbaar voor de computer. Bijvoorbeeld, als een client is al toegewezen aan site A, het beheerpunt en distributiepunt op site B pas weer toegang krijgen tot het beleid van site A en de client wordt niet met succes PXE-opstart.
2. Configuration Manager zoekt takenreeksen die zijn geïmplementeerd op het systeem record gevonden in stap 1.
3. Configuration Manager zoekt een installatiekopie die overeenkomt met de architectuur van de client die probeert te starten in de lijst van takenreeksen gevonden in stap 2. Als een opstartinstallatiekopie met dezelfde architectuur wordt gevonden, wordt die installatiekopie gebruikt.

4. Als een installatiekopie niet met dezelfde architecuture gevonden is, Configuration Manager zoekt naar een opstartinstallatiekopie (in de lijst met takenreeksen gevonden in stap 2) die compatibel is met de architectuur van de client die probeert te starten. Bijvoorbeeld, is een 64-bits client compatibel met 32-bits en 64-bits opstartinstallatiekopieën. Een 32-bits client is compatibel met alleen 32-bits opstartinstallatiekopieën. Een UEFI-client is compatibel met alleen 64-bits opstartinstallatiekopieën.

