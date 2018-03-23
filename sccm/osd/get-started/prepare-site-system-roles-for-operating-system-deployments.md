---
title: Sitesysteemrollen voorbereiden voor OSD
titleSuffix: Configuration Manager
description: De sitesysteemrollen configureren voordat u besturingssystemen implementeert
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0ef5f3ce-b0e4-4775-b5c2-b245e45b4194
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a1675f6ed3070972354ea4a14a65339c299ee01f
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="prepare-site-system-roles-for-operating-system-deployments-with-system-center-configuration-manager"></a>Sitesysteemrollen voorbereiden voor besturingssysteemimplementaties met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Om besturingssystemen te implementeren in Configuration Manager, moet u eerst voorbereiden de volgende site sitesysteemrollen die specifieke configuraties en overwegingen vereisen.



##  <a name="BKMK_DistributionPoints"></a> Distributiepunten  
 De sitesysteemrol distributiepunt fungeert als host van de bronbestanden voor clients om te downloaden. Deze inhoud is voor toepassingen, software-updates, OS-installatiekopieën, opstartinstallatiekopieën en stuurprogrammapakketten. U kunt inhoudsdistributie regelen met behulp van bandbreedte, bandbreedtebeperking en planningsopties.  

 Het is belangrijk dat u beschikt over voldoende distributiepunten ter ondersteuning van de implementatie van besturingssystemen op computers. Het is ook belangrijk dat u van plan voor de plaatsing van deze distributiepunten in uw hiërarchie bent. Zie voor meer informatie [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md). Dit artikel bevat enkele aanvullende planningsoverwegingen voor distributiepunten die specifiek voor de implementatie van het besturingssysteem.  


###  <a name="BKMK_AdditionalPlanning"></a> Aanvullende planningsoverwegingen voor distributiepunten  
 De volgende items zijn aanvullende planningsoverwegingen voor distributiepunten:  

-   **Hoe voorkom ik ongewenste OS-implementaties**  

     Configuration Manager geen onderscheid tussen siteservers en andere doelcomputers in een verzameling. Als u een vereiste takenreeks in een verzameling die een siteserver bevat implementeert, wordt de takenreeks wordt uitgevoerd dezelfde manier als elke andere computer in de verzameling. Zorg ervoor dat uw implementatie van het besturingssysteem maakt gebruik van een verzameling die de beoogde clients bevat.  

     Het gedrag voor implementaties van takenreeksen met een hoog risico beheren. Een implementatie met een hoog risico wordt automatisch op een client geïnstalleerd en heeft de potentie om ongewenste resultaten te veroorzaken. Bijvoorbeeld vereist een takenreeks met een doel die een besturingssysteem implementeert. Als u het risico van een implementatie met een ongewenst hoog risico, implementatie verificatie-instellingen te configureren. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   **Hoeveel computers kunnen in één keer een installatiekopie van het besturingssysteem van één distributiepunt ontvangen?**  

     Voor een schatting van het aantal distributiepunten, u moet rekening houden met de volgende variabelen:  
       - De verwerkingssnelheid van het distributiepunt.
       - De schijfsnelheid van het distributiepunt.
       - De beschikbare bandbreedte op het netwerk
       - De grootte van het installatiekopiepakket   
  
    Als u geen rekening met andere factoren voor serverbronnen houdt, is het maximum aantal computers dat een installatiekopiepakket van vier GB (Gigabyte) in één uur op een Ethernet-netwerk van 100-megabit per seconde kan verwerken 11-computers.  

    `100 megabits/sec = 12.5 megabytes/sec = 750 megabytes/min = 45 gigabytes/hour = 11 images @ 4 GB per image`  

    Als u een besturingssysteem op een specifiek aantal computers binnen een specifiek tijdsbestek implementeren moet, de installatiekopie distribueren naar een toepasselijk aantal distributiepunten.  

-   **Kan ik een besturingssysteem implementeren naar een distributiepunt?**  

     U kunt een besturingssysteem implementeren naar een distributiepunt, maar de installatiekopie van het besturingssysteem moet worden ontvangen van een ander distributiepunt.  


###  <a name="BKMK_PXEDistributionPoint"></a> Distributiepunten configureren voor de acceptatie van PXE-aanvragen  
 Voor het implementeren van besturingssystemen aan Configuration Manager-clients die PXE-opstartaanvragen maken, moet u een of meer distributiepunten om PXE-aanvragen te accepteren. Zodra u het distributiepunt configureert, reageert op PXE-opstartaanvragen en bepaalt de juiste implementatieactie te laten worden. Zie voor meer informatie [installeren of wijzigen van een distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#pxe).  


###  <a name="BKMK_RamDiskTFTP"></a> De RamDisk TFTP-blok en venster grootte op distributiepunten met PXE-functionaliteit aanpassen  
U kunt de RamDisk TFTP-blok en het venster grootten voor distributiepunten met PXE-functionaliteit kunt aanpassen. Als u uw netwerk hebt aangepast, kan een groot blok of het venster downloaden van de opstartinstallatiekopie mislukt met een time-outfout veroorzaken. De RamDisk TFTP-blok en het venster Grootte-aanpassingen kunnen u TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten. Om te bepalen welke configuratie is het meest efficiënt, test u de aangepaste instellingen in uw omgeving.  

-   **TFTP-blokgrootte**: De blokgrootte is de grootte van de gegevenspakketten die de server verzendt naar de client die het bestand wordt gedownload. Met een groter blok kan de server minder pakketten verzenden, waardoor er minder trajectvertraging optreedt tussen de server en de client. Echter, een grote blokgrootte leidt tot gefragmenteerde pakketten, waar de meeste PXE-clientimplementaties bieden geen ondersteuning voor.  

-   **TFTP-venstergrootte**: TFTP vereist een pakket bevestigingen (ACK) voor elk gegevensblok dat wordt verzonden. De server verzendt het volgende blok in de reeks pas wanneer het ACK-pakket van het vorige blok is ontvangen. TFTP-vensterbewerking kunt u bepalen hoeveel gegevensblokken er in een venster. De server verzendt de gegevensblokken achter elkaar door tot het venster is gevuld. Daarna verzendt de client een ACK-pakket. Als u dit venster vergroot, wordt er minder trajectvertraging optreedt tussen de client en server en verkleint u de totale tijd die nodig is voor het downloaden van een opstartinstallatiekopie.  
  


#### <a name="modify-the-ramdisk-tftp-window-size"></a>De grootte van het RamDisk TFTP-venster wijzigen  
Voor het aanpassen van de RamDisk TFTP-venstergrootte toevoegen de volgende registersleutel op distributiepunten met PXE-functionaliteit:  

  - **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
  - **Naam**: RamDiskTFTPWindowSize  
  - **Type**: REG_DWORD  
  - **Waarde**: &lt;aangepaste venstergrootte >  </br>
     De standaardwaarde is **1** (het venster vult één gegevensblok)  

#### <a name="modify-the-ramdisk-tftp-block-size"></a>De grootte van het RamDisk TFTP-blok wijzigen  
Voor het aanpassen van de RamDisk TFTP-venstergrootte toevoegen de volgende registersleutel op distributiepunten met PXE-functionaliteit:  

  - **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
  - **Naam**: RamDiskTFTPBlockSize  
  - **Type**: REG_DWORD  
  - **Waarde**: &lt;aangepaste blokgrootte >  </br>
     De standaardwaarde is **4096**.  


###  <a name="BKMK_DPMulticast"></a> Distributiepunten configureren voor de ondersteuning van multicast  
 Multicast is een methode voor netwerkoptimalisatie. U kunt deze gebruiken op distributiepunten wanneer meerdere clients zich waarschijnlijk voor het downloaden van de dezelfde installatiekopie van het besturingssysteem op hetzelfde moment. Wanneer u multicast gebruikt, kunnen meerdere computers tegelijkertijd de installatiekopie van het besturingssysteem downloaden als deze aangeboden door het distributiepunt wordt. Zonder multicast verzendt het distributiepunt een kopie van de gegevens naar elke client via een aparte verbinding. Zie voor meer informatie [multicast gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 Voordat u het besturingssysteem implementeert, moet u een distributiepunt voor multicast-ondersteuning configureren. Zie voor meer informatie [installeren en configureren van distributiepunten](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast).


##  <a name="BKMK_StateMigrationPoints"></a> Statusmigratiepunt  
 Het statusmigratiepunt opgeslagen gegevens van de gebruikersstatus die USMT vastgelegd op één computer en vervolgens te herstellen op een andere computer. Echter wanneer u gebruikersinstellingen voor een besturingssysteemimplementatie op dezelfde computer, zoals een implementatie waarbij u Windows op de doelcomputer vernieuwt vastleggen kunt u kiezen of u wilt de gegevens opslaan op dezelfde computer via vaste koppelingen of gebruik een statusmigratiepunt . Bij bepaalde computerimplementaties wanneer u het gegevensarchief maakt maakt Configuration Manager automatisch een koppeling tussen het statusarchief en de doelcomputer. Als u het statusmigratiepunt plant, houd rekening met de volgende factoren:    

### <a name="user-state-size"></a>Grootte van de gebruikersstatus  
 De grootte van de gebruikersstatus is direct van invloed op de schijfopslag op het statusmigratiepunt en de netwerkprestaties tijdens de migratie. Houd rekening met de grootte van de gebruikersstatus en het aantal computers dat moet worden gemigreerd. Houd ook rekening met de instellingen die vanaf de computer moeten worden gemigreerd. Bijvoorbeeld, als de **Mijn documenten** al back-up naar een server en vervolgens mogelijk u niet hoeft te migreren als onderdeel van de implementatie van de installatiekopie. Onnodige migraties te voorkomen de totale grootte van de gebruikersstatus kleiner blijven en verkleint u het effect dat deze anders op prestaties en schijf opslag op het statusmigratiepunt hebben zou.  

### <a name="user-state-migration-tool"></a>Hulpprogramma voor migratie van gebruikersstatus  
 Als u de gebruikersstatus wilt vastleggen en herstellen tijdens de implementatie van de besturingssystemen, moet u een USMT-pakket (User State Migration Tool, hulpprogramma voor migratie van gebruikersstatus) gebruiken dat verwijst naar de USMT-bronbestanden. Configuration Manager maakt automatisch dit pakket in de Configuration Manager-console in **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**. USMT 10 Configuration Manager gebruikt de gebruikersstatus van een besturingssysteem vastleggen en vervolgens te herstellen naar een andere. De Windows Assessment and Deployment Kit (Windows ADK) voor Windows 10 bevat USMT 10.

 Zie voor een beschrijving van verschillende migratiescenario's voor USMT 10 [algemene migratiescenario's](/windows/deployment/usmt/usmt-common-migration-scenarios) in de documentatie van Windows.  

### <a name="retention-policy"></a>Bewaarbeleid  
 Wanneer u het statusmigratiepunt configureert, geef de tijdsduur voor het behouden van de gegevens die zijn opgeslagen. Hoe lang de gegevens op het statusmigratiepunt moeten worden bewaard, is afhankelijk van twee afwegingen:  

-   Het effect dat de opgeslagen gegevens hebben op de schijfopslag.  

-   Het mogelijke vereiste dat de gegevens bepaalde tijd moeten worden bewaard voor het geval dat u de gegevens nogmaals moet migreren.
  
  
Statusmigratie vindt plaats in twee fasen: vastleggen van gegevens en de gegevens herstelt. Wanneer u de gegevens vastlegt, worden de gebruikersstatusgegevens verzameld en opgeslagen op het statusmigratiepunt. Wanneer u de gegevens herstelt, worden de gebruikersstatusgegevens van het statusmigratiepunt opgehaald en naar de doelcomputer geschreven. Met de stap **Statusopslag vrijgeven** uit de takenreeks worden de opgeslagen gegevens vervolgens vrijgegeven. Wanneer de gegevens worden vrijgegeven, wordt de bewaartimer gestart. Als u de optie voor gemigreerde gegevens onmiddellijk te verwijderen selecteert, wordt de gebruikersstatusgegevens verwijderd zodra ze zijn vrijgegeven. Als u de optie selecteert om de gegevens gedurende een bepaalde periode te behouden, worden de gegevens verwijderd zodra die periode is verstreken nadat de statusgegevens zijn vrijgegeven. Hoe langer instelt u de bewaarperiode, hoe meer schijfruimte u waarschijnlijk nodig.  

### <a name="select-drive-to-store-user-state-migration-data"></a>Het station selecteren waarop u de migratiegegevens voor de gebruikersstatus wilt opslaan  
 Wanneer u het statusmigratiepunt configureert, moet u het station op de server opgeven waarop de migratiegegevens voor de gebruikersstatus moeten worden opgeslagen. U kiest een station uit een vaste lijst met stations. Sommige van deze stations stellen mogelijk echter niet-schrijfbare stations voor, zoals het cd-station of een station dat niet tot de netwerkshare behoort. Sommige stationsletters mogelijk niet worden toegewezen aan een station op de computer. Een schrijfbaar, gedeeld station opgeven wanneer u het statusmigratiepunt configureert.  

### <a name="configure-a-state-migration-point"></a>Een statusmigratiepunt configureren  
 U kunt de volgende methoden gebruiken om een statusmigratiepunt te configureren om de gebruikersstatusgegevens op te slaan:  

-   Gebruik de **wizard Sitesysteemserver maken** om een nieuwe sitesysteemserver te maken voor het statusmigratiepunt.  

-   Gebruik de **wizard Sitesysteemrollen toevoegen** om een statusmigratiepunt toe te voegen aan een bestaande server.  

 Wanneer u deze wizards gebruikt, wordt u gevraagd om te bieden de volgende informatie voor het statusmigratiepunt:  

-   De mappen voor het opslaan van de gebruikersstatusgegevens.  

-   Het maximum aantal clients die gegevens op het statusmigratiepunt kunnen opslaan.  

-   De minimale hoeveelheid vrije schijfruimte voor het statusmigratiepunt om gebruikersstatusgegevens op te slaan.  

-   Het verwijderingsbeleid voor de rol. Opgeven dat de gebruikersstatusgegevens onmiddellijk worden verwijderd nadat dit is hersteld op een computer of na een bepaald aantal dagen nadat de gebruikersgegevens op een computer is hersteld.  

-   Of het statusmigratiepunt alleen moet reageren op aanvragen om gebruikersstatusgegevens terug te zetten. Wanneer u deze optie inschakelt, kunt het statusmigratiepunt niet gebruiken om de gebruikersstatusgegevens op te slaan.  

 Zie voor de stappen voor het installeren van een sitesysteemrol [sitesysteemrollen toevoegen](../../core/servers/deploy/configure/add-site-system-roles.md).  
