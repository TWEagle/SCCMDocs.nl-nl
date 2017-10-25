---
title: Sitesysteemrollen voor besturingssysteemimplementaties voorbereiden | Microsoft Docs
description: De sitesysteemrollen configureren voordat u besturingssystemen in System Center Configuration Manager implementeert.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0ef5f3ce-b0e4-4775-b5c2-b245e45b4194
caps.latest.revision: "11"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 11c0f169afebdb071fefb5ce300fd1ae3481a94f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="prepare-site-system-roles-for-operating-system-deployments-with-system-center-configuration-manager"></a>Sitesysteemrollen voorbereiden voor besturingssysteemimplementaties met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Om besturingssystemen te implementeren in System Center Configuration Manager, moet u eerst voorbereiden de volgende site sitesysteemrollen die specifieke configuraties en overwegingen vereisen.

##  <a name="BKMK_DistributionPoints"></a> Distributiepunten  
 De distributiepuntrol van het sitesysteem bevat bronbestanden die clients kunnen downloaden, zoals toepassingsinhoud, software, updates, installatiekopieën van besturingssystemen en opstartinstallatiekopieën. U kunt inhoudsdistributie regelen met behulp van bandbreedte, bandbreedtebeperking en planningsopties.  

 Het is belangrijk dat u over voldoende distributiepunten beschikt ter ondersteuning van de implementatie van besturingssystemen op computers. Daarnaast is het belangrijk dat u de plaatsing van deze distributiepunten in uw hiërarchie plant. U vindt de meeste van deze planningsinformatie in [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md). Er zijn echter enkele aanvullende planningsoverwegingen voor distributiepunten die specifiek zijn voor de besturingssysteemimplementaties.  

###  <a name="BKMK_AdditionalPlanning"></a> Aanvullende planningsoverwegingen voor distributiepunten  
 Hieronder volgen enkele aanvullende planningsoverwegingen voor distributiepunten:  

-   **Hoe voorkom ik ongewenste besturingssysteemimplementaties?**  

     Configuration Manager geen onderscheid tussen siteservers andere doelcomputers in een verzameling. Als u een vereiste takenreeks implementeert in een verzameling die een siteserver bevat, voert de siteserver de takenreeks op dezelfde manier uit als elke andere computer in de verzameling dat doet. Zorg ervoor dat uw besturingssysteemimplementatie een verzameling gebruikt die de clients bevat waarvoor u de implementatie wilt uitvoeren.  

     U kunt het gedrag voor de implementatie van takenreeksen met een hoge risico beheren. Een implementatie met een hoog risico wordt automatisch op een client geïnstalleerd en heeft de potentie om ongewenste resultaten te veroorzaken. Bijvoorbeeld een takenreeks met het doel Vereist en die een besturingssysteem implementeert. Als u het risico van een implementatie met een ongewenst hoog risico wilt voorkomen, kunt u de instellingen voor de implementatieverificatie configureren: Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   **Hoeveel computers kunnen een installatiekopie van een besturingssysteem tegelijkertijd van één distributiepunt ontvangen?**  

     Voor een schatting van het aantal distributiepunten dat u nodig hebt, moet u rekening houden met de verwerkingssnelheid en schijf-I/O van het distributiepunt, de beschikbare bandbreedte op het netwerk en het effect dat de grootte van het installatiekopiepakket op deze bronnen heeft. Voorbeeld: op een Ethernet-netwerk van 100 MB is het maximale aantal computers dat in één uur een installatiekopiepakket van 4 GB kan verwerken, 11 computers als u geen rekening houdt met andere factoren voor serverbronnen.  

     `100 Megabits/sec = 12.5 Megabytes/sec = 750 Megabytes/min = 45 Gigabytes/hour = 11 images @ 4GB per image.`  

     Als u binnen een specifiek tijdsbestek een besturingsysteem naar een specifiek aantal computers moet uitvoeren, distribueert u de installatiekopie naar een toepasselijk aantal distributiepunten.  

-   **Kan ik een besturingssysteem implementeren op een distributiepunt?**  

     U kunt een besturingssysteem implementeren op een distributiepunt, maar de installatiekopie van het besturingssysteem moet worden ontvangen van een ander distributiepunt.  

###  <a name="BKMK_PXEDistributionPoint"></a> Distributiepunten configureren voor de acceptatie van PXE-aanvragen  
 Voor het implementeren van besturingssystemen aan Configuration Manager-clients die PXE-opstartaanvragen maken, moet u een of meer distributiepunten om PXE-aanvragen te accepteren. Zodra het distributiepunt is geconfigureerd, kan het reageren op de PXE-opstartaanvraag en bepalen welke implementatieacties moeten worden ondernomen.

> [!IMPORTANT]  
>  [Windows Deployment Service](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_WDS) moet worden geïnstalleerd op alle distributiepunten met PXE-functionaliteit.  

 Gebruik de volgende procedure om een bestaand distributiepunt te wijzigen zodat het PXE-aanvragen kan accepteren. Zie [Een distributiepunt installeren of wijzigen](../../core/servers/deploy/configure/install-and-configure-distribution-points.md) voor meer informatie over het installeren van nieuwe distributiepunten.  

#### <a name="to-modify-an-existing-distribution-point-to-accept-pxe-requests"></a>Een bestaand distributiepunt wijzigen voor de acceptatie van PXE-aanvragen  

1.  Klik in de Configuration Manager-console op **beheer**, vouw **overzicht** en klik op **distributiepunten**.  

2.  Selecteer het distributiepunt dat u wilt configureren en klik in de groep **Eigenschappen** van het tabblad **Start** op de optie **Eigenschappen**.  

3.  Ga op de eigenschappenpagina van het distributiepunt naar het tabblad **PXE** en selecteer **PXE-ondersteuning voor clients inschakelen** om PXE op dit distributiepunt in te schakelen.  

4.  Klik in het dialoogvenster **Vereiste poorten voor PXE controleren** op **Ja** om te bevestigen dat u PXE wilt inschakelen. Configuration Manager configureert automatisch de standaardpoorten op een Windows-firewall. Als u een andere firewall gebruikt, moet u de poorten handmatig configureren.  

    > [!NOTE]  
    >  Als WDS en DHCP zijn geïnstalleerd op dezelfde server, moet u WDS configureren om op een andere poort te luisteren (aangezien DHCP op dezelfde poort luistert). Zie [Overwegingen wanneer u WDS en DHCP op dezelfde server uitvoert](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_WDSandDHCP) voor meer informatie.  

5.  Selecteer **Dit distributiepunt toestaan te reageren op binnenkomende PXE-aanvragen** om WDS in te schakelen, zodat er wordt gereageerd op binnenkomende PXE-serviceaanvragen. Met dit selectievakje kunt u de service in- en uitschakelen zonder de PXE-functionaliteit van het distributiepunt te verwijderen.  

6.  Selecteer **Schakel onbekende computerondersteuning** om besturingssystemen te implementeren op computers die niet worden beheerd door Configuration Manager.  

7.  Schakel **Een wachtwoord verplicht stellen wanneer computers PXE gebruiken**in en geef een sterk wachtwoord op om uw PXE-implementaties extra te beveiligen.  

8.  Kies in de lijst **Affiniteit van gebruikersapparaat** hoe het distributiepunt gebruikers moet koppelen aan de doelcomputer voor PXE-implementaties.  

    -   Schakel **Geen gebruikersaffiniteit apparaat gebruiken** in als u geen gebruikers wilt koppelen aan de doelcomputer.  

    -   Selecteer **Gebruikersaffiniteit apparaat met handmatige goedkeuring toestaan** als u wilt wachten op goedkeuring van een gebruiker met beheerdersrechten voordat gebruikers aan de doelcomputer worden gekoppeld.  

    -   Selecteer **Gebruikersaffiniteit apparaat met automatische goedkeuring toestaan** als u gebruikers automatisch wilt koppelen aan de doelcomputer zonder op goedkeuring te wachten.  

     Zie voor meer informatie [gebruikers koppelen aan een doelcomputer](../get-started/associate-users-with-a-destination-computer.md).  

9. Geef op dat het distributiepunt reageert op PXE-aanvragen van alle netwerkinterfaces of van specifieke netwerkinterfaces. Als u wilt dat het distributiepunt op specifieke netwerkinterfaces reageert, geeft u het MAC-adres voor elke netwerkinterface op.  

10. Geef in seconden op hoe lang de vertraging is voordat het distributiepunt reageert op computeraanvragen wanneer er meerdere distributiepunten met PXE-functionaliteit worden gebruikt.  

11. Klik op **OK** om de eigenschappen van het distributiepunt bij te werken.  

###  <a name="BKMK_RamDiskTFTP"></a> De RamDisk TFTP-blokgrootte en de -venstergrootte aanpassen op het distributiepunt met PXE-functionaliteit  
U kunt de RamDisk TFTP-blokgrootte en begin in Configuration Manager versie 1606, de grootte van het venster voor distributiepunten met PXE-functionaliteit aanpassen. Als u uw netwerk hebt aangepast, kan dit ertoe leiden dat het downloaden van de opstartinstallatiekopie mislukt met een time-outfout omdat het blok of het venster te groot is. Met RamDisk TFTP-blok- en venstergrootteaanpassing kunt u het TFTP-verkeer optimaliseren als u PXE gebruikt om te voldoen aan uw specifieke netwerkvereisten.   
U moet de aangepaste instellingen in uw omgeving testen om te bepalen het meest efficiënt is.  

-   **TFTP-blokgrootte**: De blokgrootte is de grootte van de gegevenspakketten die door de server worden verzonden naar de client die het bestand downloadt (zoals beschreven in RFC 2347). Met een groter blok kan de server minder pakketten verzenden, waardoor er minder trajectvertraging optreedt tussen de server en de client. Met grotere blokken kan er echter sprake zijn van gefragmenteerde pakketten, waar de meeste PXE-clientimplementaties geen ondersteuning voor bieden.  

-   **TFTP-venstergrootte**: TFTP vereist een pakket bevestigingen (ACK) voor elk gegevensblok dat wordt verzonden. De server verzendt het volgende blok in de reeks pas wanneer het ACK-pakket van het vorige blok is ontvangen. TFTP-vensterbewerking is een functie in Windows Deployment Services waarmee u kunt instellen hoeveel gegevensblokken er in een venster passen. De server verzendt de gegevensblokken achter elkaar door tot het venster is gevuld. Daarna verzendt de client een ACK-pakket. Als u het venster vergroot, treedt er minder trajectvertraging op tussen de client en de server en is er minder tijd nodig om een opstartinstallatiekopie te downloaden.  


#### <a name="to-modify-the-ramdisk-tftp-window-size"></a>De grootte van het RamDisk TFTP-venster wijzigen  

-   Voeg de volgende registersleutel toe aan de distributiepunten met PXE-functionaliteit om de RamDisk TFTP-venstergrootte aan te passen:  

     **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Naam: RamDiskTFTPWindowSize  

     **Type**: REG_DWORD  

     **Waarde**: &lt;aangepaste venstergrootte >  

 De standaardwaarde is 1 (het venster bestaat uit één gegevensblok)  

#### <a name="to-modify-the-ramdisk-tftp-block-size"></a>De grootte van het RamDisk TFTP-blok wijzigen  

-   Voeg de volgende registersleutel toe aan de distributiepunten met PXE-functionaliteit om de RamDisk TFTP-venstergrootte aan te passen:  

     **Locatie**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Naam: RamDiskTFTPBlockSize  

     **Type**: REG_DWORD  

     **Waarde**: &lt;aangepaste blokgrootte >  

 De standaardwaarde is 4096 (4k).  


###  <a name="BKMK_DPMulticast"></a> Distributiepunten configureren voor de ondersteuning van multicast  
 Multicast is een methode voor netwerkoptimalisatie die u op distributiepunten kunt gebruiken wanneer de kans bestaat dat meerdere clients tegelijkertijd dezelfde installatiekopie van een besturingssysteem downloaden. Wanneer multicast wordt gebruikt, kunnen meerdere computers tegelijkertijd de installatiekopie van het besturingssysteem downloaden, aangezien deze door het distributiepunt wordt aangeboden via multicasting. Het distributiepunt verzendt dus geen kopie van de gegevens via een aparte verbinding naar elke client. U moet ten minste één distributiepunt configureren als u multicast wilt ondersteunen. Zie voor meer informatie [multicast gebruiken om Windows te implementeren via het netwerk](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 Voordat u het besturingssysteem implementeert, moet u een distributiepunt configureren voor de ondersteuning van multicast. Gebruik de volgende procedure om een bestaand distributiepunt te wijzigen voor de ondersteuning van multicast. Zie voor meer informatie over het installeren van een nieuw distributiepunt [installeren en configureren van distributiepunten](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

#### <a name="to-enable-multicast-for-a-distribution-point"></a>Multicast inschakelen voor een distributiepunt  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw in de werkruimte **Beheer** **Overzicht**uit en selecteer het knooppunt **Distributiepunten** .  

3.  Selecteer het distributiepunt dat u wilt gebruiken voor multicasting van de installatiekopie van het besturingssysteem.  

4.  Klik in de groep **Eigenschappen** van het tabblad **Start** op **Eigenschappen**.  

5.  Selecteer het tabblad **Multicast** en configureer de volgende opties:  

    -   **Multicast inschakelen**: U moet deze optie selecteren voor het distributiepunt voor multicast-ondersteuning.  

    -   **Multicastverbindingsaccount**: Geef een account verbinding maken met de sitedatabase.  

    -   **Multicastadresinstellingen**: Geef het IP-adressen om gegevens te verzenden naar de doelcomputers. Standaard wordt het IP-adres verkregen van een DHCP-server die is ingeschakeld voor het distribueren van multicastadressen. Afhankelijk van de netwerkomgeving, kunt een reeks IP-adressen opgeven tussen 239.0.0.0 en 239.255.255.255.  

        > [!IMPORTANT]  
        >  Deze IP-adressen moeten toegankelijk zijn voor de doelcomputers die de installatiekopie van het besturingssysteem aanvragen. Dit betekent dat routers en firewalls tussen de doelcomputer en de siteserver zodanig moeten worden geconfigureerd dat multicast-verkeer is toegestaan.  

    -   **UDP-poortbereik**: Geef het UDP-poortbereik op om gegevens te verzenden naar de doelcomputers.  

        > [!IMPORTANT]  
        >  Deze poorten moeten toegankelijk zijn voor de doelcomputers die de installatiekopie van het besturingssysteem aanvragen. Dit betekent dat routers en firewalls tussen de doelcomputer en de siteserver zodanig moeten worden geconfigureerd dat multicast-verkeer is toegestaan.  

    -   **Geplande multicast inschakelen**: Geef op hoe Configuration Manager bepaalt wanneer kan ik besturingssystemen implementeren op doelcomputers. Klik op **Geplande multicast inschakelen**en selecteer de volgende opties.  

         In de **startvertraging van sessie** Geef het aantal minuten dat Configuration Manager voordat wacht het reageert op de eerste implementatieaanvraag.  

         In de **minimale sessiegrootte** Geef op hoeveel aanvragen er moeten worden ontvangen voordat Configuration Manager begint met de implementatie van het besturingssysteem.  

    -   **Overdrachtssnelheid**: Selecteer de overdrachtssnelheid om gegevens te downloaden naar de doelcomputers.  

    -   **Maximum aantal clients**: Geef het maximum aantal doelcomputers op dat het besturingssysteem vanaf dit distributiepunt kan downloaden.  

6.  Klik op **OK**.  

##  <a name="BKMK_StateMigrationPoints"></a> Statusmigratiepunt  
 Op het statusmigratiepunt worden gebruikersstatusgegevens opgeslagen die op de ene computer worden vastgelegd en vervolgens op een andere computer worden hersteld. Wanneer u echter gebruikersinstellingen voor een besturingssysteemimplementatie op dezelfde computer vastlegt, zoals een implementatie waarbij u het besturingssysteem op de doelcomputer vernieuwt, kunt u ervoor kiezen om de gegevens op dezelfde computer op te slaan via vaste koppelingen of om een statusmigratiepunt te gebruiken. Bij bepaalde computerimplementaties wanneer u het gegevensarchief maakt maakt Configuration Manager automatisch een koppeling tussen het statusarchief en de doelcomputer. Wanneer u het statusmigratiepunt plant, moet u rekening houden met de volgende factoren.  

### <a name="user-state-size"></a>Grootte van de gebruikersstatus  
 De grootte van de gebruikersstatus is direct van invloed op de schijfopslag op het statusmigratiepunt en de netwerkprestaties tijdens de migratie. Houd rekening met de grootte van de gebruikersstatus en het aantal computers dat moet worden gemigreerd. Houd ook rekening met de instellingen die vanaf de computer moeten worden gemigreerd. Als er bijvoorbeeld al een back-up van **Mijn documenten** is gemaakt op een server, hoeft u deze wellicht niet te migreren als onderdeel van de implementatie van de installatiekopie. Door onnodige migraties te voorkomen, kan de totale grootte van de gebruikersstatus kleiner blijven en neemt het effect af dat de status anders zou hebben op de netwerkprestaties en schijfopslag op het statusmigratiepunt.  

### <a name="user-state-migration-tool"></a>Hulpprogramma voor migratie van gebruikersstatus  
 Als u de gebruikersstatus wilt vastleggen en herstellen tijdens de implementatie van de besturingssystemen, moet u een USMT-pakket (User State Migration Tool, hulpprogramma voor migratie van gebruikersstatus) gebruiken dat verwijst naar de USMT-bronbestanden. Configuration Manager maakt automatisch dit pakket in de Configuration Manager-console in **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**. Configuration Manager gebruikt USMT 10.0, dat wordt gedistribueerd in de Windows Assessment and Deployment Kit (Windows ADK), de status van de gebruiker van een besturingssysteem vastleggen en vervolgens te herstellen op een ander besturingssysteem.  

 Zie [Common Migration Scenarios](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)(Algemene migratiescenario's) voor een beschrijving van verschillende migratiescenario's voor USMT 10.0.  

### <a name="retention-policy"></a>Bewaarbeleid  
 Wanneer u het statusmigratiepunt configureert, kunt u opgeven hoe lang de gebruikersstatusgegevens moeten worden bewaard die op het punt worden opgeslagen. Hoe lang de gegevens op het statusmigratiepunt moeten worden bewaard, is afhankelijk van twee afwegingen:  

-   Het effect dat de opgeslagen gegevens hebben op de schijfopslag.  

-   Het mogelijke vereiste dat de gegevens bepaalde tijd moeten worden bewaard voor het geval dat u de gegevens nogmaals moet migreren.  

 Statusmigratie vindt plaats in twee fasen: Vastleggen van gegevens en de gegevens herstelt. Wanneer u de gegevens vastlegt, worden de gebruikersstatusgegevens verzameld en opgeslagen op het statusmigratiepunt. Wanneer u de gegevens herstelt, worden de gebruikersstatusgegevens van het statusmigratiepunt opgehaald en naar de doelcomputer geschreven. Met de stap **Statusopslag vrijgeven** uit de takenreeks worden de opgeslagen gegevens vervolgens vrijgegeven. Wanneer de gegevens worden vrijgegeven, wordt de bewaartimer gestart. Als u de optie selecteert om gemigreerde gegevens onmiddellijk te verwijderen, worden de gebruikersstatusgegevens verwijderd zodra ze zijn vrijgegeven. Als u de optie selecteert om de gegevens gedurende een bepaalde periode te behouden, worden de gegevens verwijderd zodra die periode is verstreken nadat de statusgegevens zijn vrijgegeven. Hoe langer u de bewaarperiode instelt, hoe meer schijfruimte u waarschijnlijk nodig hebt.  

### <a name="select-drive-to-store-user-state-migration-data"></a>Het station selecteren waarop u de migratiegegevens voor de gebruikersstatus wilt opslaan  
 Wanneer u het statusmigratiepunt configureert, moet u het station op de server opgeven waarop de migratiegegevens voor de gebruikersstatus moeten worden opgeslagen. U kiest een station uit een vaste lijst met stations. Sommige van deze stations stellen mogelijk echter niet-schrijfbare stations voor, zoals het cd-station of een station dat niet tot de netwerkshare behoort. Bovendien zijn sommige stationsletters mogelijk niet toegewezen aan een station op de computer. U moet een schrijfbaar, gedeeld station opgeven wanneer u het statusmigratiepunt configureert.  

### <a name="configure-a-state-migration-point"></a>Een statusmigratiepunt configureren  
 U kunt de volgende methoden gebruiken om een statusmigratiepunt te configureren om de gebruikersstatusgegevens op te slaan:  

-   Gebruik de **wizard Sitesysteemserver maken** om een nieuwe sitesysteemserver te maken voor het statusmigratiepunt.  

-   Gebruik de **wizard Sitesysteemrollen toevoegen** om een statusmigratiepunt toe te voegen aan een bestaande server.  

 Als u deze wizards gebruikt, wordt u gevraagd om de volgende informatie op te geven voor het statusmigratiepunt:  

-   De mappen voor het opslaan van de gebruikersstatusgegevens.  

-   Het maximum aantal clients die gegevens op het statusmigratiepunt kunnen opslaan.  

-   De minimale hoeveelheid vrije schijfruimte voor het statusmigratiepunt om gebruikersstatusgegevens op te slaan.  

-   Het verwijderingsbeleid voor de rol. U kunt opgeven dat de gebruikersstatusgegevens onmiddellijk worden verwijderd nadat ze op een computer zijn hersteld, of na een specifiek aantal dagen nadat de gebruikersgegevens op een computer worden hersteld.  

-   Of het statusmigratiepunt alleen moet reageren op aanvragen om gebruikersstatusgegevens terug te zetten. Wanneer u deze optie inschakelt, kunt het statusmigratiepunt niet gebruiken om de gebruikersstatusgegevens op te slaan.  

 Zie voor de stappen voor het installeren van een sitesysteemrol [sitesysteemrollen toevoegen](../../core/servers/deploy/configure/add-site-system-roles.md).  
