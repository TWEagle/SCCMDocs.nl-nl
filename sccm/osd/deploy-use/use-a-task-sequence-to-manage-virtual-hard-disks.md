---
title: Een takenreeks gebruiken voor het beheren van virtuele harde schijven
titleSuffix: Configuration Manager
description: Maken en een VHD wijzigen, toepassingen en software-updates toevoegen en de VHD publiceren naar System Center Virtual Machine Manager (VMM) van Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0212b023-804a-4f84-b880-7a59cdb49c67
caps.latest.revision: "5"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 89e30f81648aff16de2f7db55cbdda06cf69551d
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="use-a-task-sequence-to-manage-virtual-hard-disks-in-system-center-configuration-manager"></a>Een takenreeks gebruiken voor het beheren van virtuele harde schijven in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager kunt u virtuele harde schijven (VHD's) beheren en integreren van de VHD's die u in uw datacenter vanuit de Configuration Manager-console maakt. U kunt in het bijzonder maken en een VHD wijzigen, toepassingen en software-updates toevoegen aan de VHD en publiceren van de VHD naar System Center Virtual Machine Manager (VMM) vanuit de Configuration Manager-console.  

 Gebruik de volgende secties voor het beheren van VHD's in Configuration Manager.

## <a name="prerequisites"></a>Vereisten  
 Controleer de volgende vereisten voordat u begint:  

-   De computer van waaruit u de VHD's beheert moet werken op een van de volgende besturingssystemen:  

    -   Windows 8.1 x 64  

    -   Windows 8 x64  

    -   Windows Server 2008 R2  

    -   Windows Server 2012  

    -   Windows Server 2012 R2  

-   Virtualisatie moet zijn ingeschakeld in het BIOS en Hyper-V moet zijn geïnstalleerd op de computer van waaruit u de Configuration Manager-console voor het beheren van VHD's uitvoert. Installeer als aanbevolen werkwijze ook de Hyper-V hulpprogramma's voor het beheer om uw virtuele harde schijven te testen en problemen op te lossen. De Hyper-V hulpprogramma's voor het beheer moeten bijvoorbeeld zijn geïnstalleerd voor het controleren van de smsts.log  om de voortgang van de takenreeks in Hyper-V op te volgen. Zie [Installatievereisten voor Hyper-V](http://technet.microsoft.com/library/cc731898.aspx)voor meer informatie over de vereisten voor Hyper-V.  

    > [!IMPORTANT]  
    >  Het proces om een VHD te maken verbruikt tijd en geheugen van de processor. Daarom is het aanbevolen VHD's te beheren vanuit een Configuration Manager-console dat niet is geïnstalleerd op de siteserver.  

-   De siteserver moet voorzien zijn van **Schrijfmachtiging** tot de map die het VHD-bestand bevat, wanneer u VHD's beheert vanuit een computer die extern is aan de siteserver.  

-   Controleer dat u voldoende beschikbare schijfruimte heeft op de computer van waaruit u de VHD's beheert. De vereisten voor de hardeschijfruimte van de VHD variëren afhankelijk van het besturingssysteem en de toepassingen die u installeert.  

-   Controleer dat de computer van waaruit u de VHD's beheert over voldoende ruimte beschikt. De virtuele machine is geconfigureerd om tijdens het proces om de VHD te maken 2 GB aan geheugen te verbruiken.  

-   Installeer de System Center Virtual Machine Manager (VMM)-console van waaruit u de VHD naar VMM uploadt. U kunt de VMM-console installeren op een afzonderlijke computer van waaruit u uw VHD's beheert. Dit betekent dat installatie van de Hyper-V niet vereist is om de VHD naar VMM te importeren.  

    > [!NOTE]  
    >  Als u de VMM-console installeert terwijl de Configuration Manager-console geopend is, moet u de Configuration Manager-console opnieuw opstarten nadat de installatie van de VMM-console is voltooid. Anders Configuration Manager wordt geen verbinding maken met de VMM-beheerserver om een VHD te uploaden.  

##  <a name="BKMK_CreateVHDSteps"></a> Stappen voor het maken van een VHD  
 Voor het maken van een VHD, moet u een takenreeks maken die de stappen bevat om de VHD te maken en vervolgens de takenreeks gebruiken in de wizard om een virtueel hardeschijfstation te maken om de VHD te maken. In de volgende secties vindt u de stappen voor het maken van de VHD.  

###  <a name="BKMK_CreateTS"></a> Takenreeks voor de VHD maken  
 U moet een takenreeks maken die de stappen bevat om de VHD te maken. In de wizard Takenreeks maken, moet u de optie **Een installatiekopie installeren op een virtuele harde schijf** hebben, die de stappen maakt om de VHD te maken. De wizard voegt bijvoorbeeld de volgende vereiste stappen toe: Opnieuw opstarten in Windows PE, schijf formatteren en partitioneren, besturingssysteem en Computer afsluiten toepassen. U kunt de VHD niet maken in het volledige besturingssysteem. Configuration Manager moet ook wachten tot de virtuele machine is afgesloten voordat het pakket kan worden voltooid. De wizard wacht standaard 5 minuten voordat deze de virtuele machine afsluit. Nadat u de takenreeks maakt, kunt u indien nodig aanvullende stappen toevoegen.  

> [!IMPORTANT]  
>  De volgende procedure maakt de takenreeks met behulp van de optie **Een bestaande installatiekopie op een virtuele harde schijf installeren** . Deze omvat automatisch de vereiste stappen voor het maken van de VHD. Als u kiest om een bestaande takenreeks te gebruiken of handmatig een takenreeks te maken, zorgt u dat u de stap Computer afsluiten toevoegt op het einde van de takenreeks. Zonder deze stap wordt de tijdelijke virtuele machine niet verwijderd en het proces voor het maken van de VHD niet voltooid. De wizard is niettemin voltooid en duidt de goede afloop aan.  

 Gebruik de volgende procedure voor het maken van de takenreeks om de VHD te maken:  

#### <a name="to-create-the-task-sequence-to-create-the-vhd"></a>Takenreeks voor het maken van de VHD maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Klik op **Bestaand installatiekopiepakket installeren op een virtuele harde schijf** op de pagina **Nieuwe takenreeks maken**en klik vervolgens op **Volgende**.  

5.  Configureer op de pagina **Takenreeksinformatie** de volgende instellingen en klik op **Volgende**.  

    -   **Takenreeksnaam**: Geef een naam die de takenreeks identificeert.  

    -   **Beschrijving**: Geef een beschrijving van de takenreeks.  

    -   **Opstartinstallatiekopie**: Geef de opstartinstallatiekopie die het besturingssysteem wordt geïnstalleerd op de doelcomputer. Zie voor meer informatie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

6.  Geef op de pagina **Windows installeren** de volgende opties op en klik op **Volgende**.  

    -   **Installatiekopiepakket**: Geef het pakket met de installatiekopie van het besturingssysteem te installeren.  

    -   **Afbeelding**: Als het installatiekopiepakket van het besturingssysteem meerdere installatiekopieën bevat, geeft u de index van de installatiekopie van het besturingssysteem te installeren.  

    -   **Productcode**: Geef de productcode voor het Windows-besturingssysteem te installeren. U kunt gecodeerde volumelicentiesleutels en standaardproductsleutels opgeven. Als u een niet-gecodeerde productcode gebruikt, moet elke groep van 5 tekens gescheiden worden door een streepje (-). Bijvoorbeeld: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Serverlicentiemodus**: Geef op of de serverlicentie **Per seat**, **Per server**, of dat er geen licentie is opgegeven. Als de serverlicentie **Per server**is, geef dan ook het maximum aantal serververbindingen op.  

    -   Geef op hoe het beheerdersaccount moet worden afgehandeld dat wordt gebruikt wanneer de installatiekopie van het besturingssysteem wordt geïmplementeerd.  

        -   **Willekeurig wachtwoord genereren voor lokale beheerder en het account uitschakelen op alle ondersteunde platforms (aanbevolen)**: Gebruik deze instelling zodat de wizard willekeurig een wachtwoord voor het lokale administrator-account maken en het account uitschakelen wanneer de installatiekopie van het besturingssysteem is geïmplementeerd.  

        -   **Het account inschakelen en geef het lokale beheerderswachtwoord**: Deze instelling gebruiken om een specifiek wachtwoord gebruiken voor het lokale beheerdersaccount op alle computers waarop de installatiekopie van het besturingssysteem wordt geïmplementeerd.  

7.  Geef op de pagina **Netwerk configureren** de volgende opties op en klik op **Volgende**.  

    -   **Lid worden van een werkgroep**: Geef op of de doelcomputer wordt toegevoegd aan een werkgroep.  

    -   **Lid worden van een domein**: Geef op of de doelcomputer aan een domein toevoegen. Geef in **Domein**de naam op van het domein.  

        > [!IMPORTANT]  
        >  U kunt bladeren om domeinen te zoeken in het lokaal forest, maar u moet de domeinnaam opgeven voor een extern forest.  

         U kunt ook een organisatie-eenheid (OE) opgeven. Dit is een optionele instelling die de LDAP X.500-DN-naam van de OE specificeert waarin het computeraccount moet worden aangemaakt als het nog niet bestaat.  

    -   **Account**: Geef de gebruikersnaam en wachtwoord voor het account met machtigingen die aan het opgegeven domein. Bijvoorbeeld: *domein\gebruiker* of *%variabele%*.  

8.  Op de **Configuration Manager installeren** pagina, geeft u het clientpakket voor Configuration Manager om te installeren op de doelcomputer en klik vervolgens op **volgende**.  

9. Geef op de pagina **Toepassingen installeren** de toepassingen op die moeten worden geïnstalleerd op de doelcomputer en klik op **Volgende**. Als u meerdere toepassingen opgeeft, kunt u opgeven dat de takenreeks wordt voortgezet als de installatie van een bepaalde toepassing mislukt.  

10. Voltooi de wizard.  

###  <a name="BKMK_CreateVHD"></a> Een VHD maken  
 Nadat u een takenreeks voor de VHD maakt, gebruikt u de wizard om de virtuele harde schijven maken om de VHD te maken.  

> [!IMPORTANT]  
>  Controleer, voordat u deze procedure uitvoert, dat u voldoet aan de vereisten die opgesomd zijn bovenaan dit onderwerp.  

 Gebruik de volgende procedure om een VHD te maken.  

#### <a name="to-create-a-vhd"></a>Een VHD maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Virtuele harde schijven**.  

3.  Klik op **Virtuele harde schijf maken** in het tabblad **Start** , in de groep **Maken** om de wizard Virtuele harde schijf maken te starten.  

    > [!NOTE]  
    >  Hyper-V moet zijn geïnstalleerd op de computer met de Configuration Manager-console van waaruit u de VHD's beheert of de **virtuele harde schijf maken** optie is niet ingeschakeld. Zie [Installatievereisten voor Hyper-V](http://technet.microsoft.com/library/cc731898.aspx)voor meer informatie over de vereisten voor Hyper-V.  

    > [!TIP]  
    >  Maak, om uw VHD's te organiseren, een nieuwe map of selecteer een bestaande map in knooppunt **Virtuele harde schijven** en klik vervolgens op **Virtuele harde schijf maken** van de map.  

4.  Stel op de pagina **Algemeen** de volgende instellingen in en klik op **Volgende**.  

    -   **Naam**: Geef een unieke naam voor de VHD.  

    -   **Versie**: Geef een uniek versienummer op voor de VHD. Dit is een optionele instelling.  

    -   **Opmerking**: Geef een beschrijving voor de VHD.  

    -   **Pad**: Geef de naam van het pad en de bestandsnaam voor waar de wizard het VHD-bestand zal maken.  

         U moet een geldig netwerkpad in de UNC-indeling invoeren. Bijvoorbeeld:  **\\\servername\\< sharename\>\\< filename\>.vhd**.  

        > [!WARNING]  
        >  Configuration Manager moet hebben **schrijven** toegang hebben tot het opgegeven pad voor het maken van de VHD. Als Configuration Manager toegang tot het pad is mislukt, wordt de gekoppelde foutmelding in het distmgr.log-bestand op de siteserver gelogd.  

5.  Op de pagina **Takenreeks** geeft u de takenreeks op die u in de voorgaande sectie hebt opgegeven en klikt u vervolgens op **Volgende**.  

6.  Selecteer, op de pagina **Distributiepunten** , een of meer distributiepunten die de inhoud bevatten die vereist is door de takenreeks, en klik vervolgens op **Volgende**.  

7.  Klik op de pagina **Aanpassing** op **Volgende**. Het proces om de VHD te maken negeert alle instellingen die u op deze pagina hebt opgegeven.  

8.  Controleer de instellingen en klik vervolgens op **Volgende**. De wizard maakt de VHD.  

    > [!TIP]  
    >  De tijd om het proces van het maken van de VHD af te ronden kan variëren. Terwijl de wizard door dit proces werkt, kunt u de volgende logboekbestanden controleren om de voortgang op te volgen. Standaard de logboeken bevinden zich op de computer waarop de Configuration Manager-console wordt uitgevoerd op %*ProgramFiles(x86)*%\Microsoft Configuration Manager\AdminConsole\AdminUILog.  
    >   
    >  -   **CreateTSMedia.log**: De wizard schrijft informatie in dit logboek bij het maken van de takenreeksmedia. Bekijk dit logboekbestand om de voortgang van de wizard op te volgen bij het maken van de zelfstandige media.  
    > -   **DeployToVHD.log**: De wizard schrijft informatie in dit logboek tijdens het door het proces om de VHD te maken. Bekijk dit logboekbestand voor het opvolgen van de voortgang van de wizard voor alle stappen na het maken van de zelfstandige media.  
    >   
    >  Bij het starten van de installatie van het besturingssysteem, kunt u ook Hyper-V Manager openen (indien u Hyper-V hulpprogramma's voor het beheer op de computer hebt geïnstalleerd) en verbinding maken met de tijdelijke virtuele machine die is gemaakt door de wizard om de uitvoering van de takenreeks te zien. U kunt vanuit de virtuele machine het bestand smsts.log controleren om de voortgang van de takenreeks te volgen. Wanneer er problemen zijn om een stap van de takenreeks uit te voeren, kunt u met behulp van dit logbestand de fout opsporen. Het bestand smsts.log bevindt zich in x: \windows\temp\smstslog\smsts.log voordat de harde schijf wordt geformatteerd en in c:\\_SMSTaskSequence\Logs\Smstslog\ nadat deze is geformatteerd. Nadat de stappen van de takenreeks zijn uitgevoerd, wordt de virtuele machine (standaard) na 5 minuten uitgeschakeld en verwijderd.  

 Configuration Manager de VHD heeft gemaakt, bevindt zich in de **virtueel hardeschijfstation** knooppunt in de Configuration Manager-console onder het **Besturingssysteemimplementatie** knooppunt in de **softwarebibliotheek** werkruimte.  

> [!NOTE]  
>  Configuration Manager haalt de grootte van de VHD door verbinding te maken naar de bronlocatie van de VHD. Als Configuration Manager geen toegang het VHD-bestand tot **0** wordt weergegeven in de **grootte (KB)** kolom voor de VHD.  

##  <a name="BKMK_ModifyVHDSteps"></a> Stappen voor het wijzigen van een bestaande VHD  
 Voor het wijzigen van een VHD, moet u een takenreeks maken met de vereiste stappen om de VHD te wijzigen. Selecteer vervolgens de takenreeks in de wizard Virtueel hardeschijfstation wijzigen. De wizard sluit de VHD aan op de virtuele machine, voert de takenreeks uit in de VHD en werkt vervolgens het VHD-bestand bij. In de volgende secties vindt u de stappen voor het wijzigen van de VHD.  

###  <a name="BKMK_ModifyTS"></a> Een takenreeks maken om de VHD te wijzigen  
 Voor het wijzigen van een bestaande VHD, moet u eerst een takenreeks maken. Kies enkel de stappen die nodig zijn om de takenreeks te wijzigen. Als u bijvoorbeeld een toepassing wilt toevoegen aan de VHD, maakt u een aangepaste takenreeks en voegt vervolgens enkel de stap Toepassing installeren toe.  

 Gebruik de volgende procedure om een takenreeks te maken om de VHD te wijzigen.  

#### <a name="to-create-a-custom-task-sequence-to-modify-the-vhd"></a>Een aangepaste takenreeks maken om de VHD te wijzigen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Op de pagina **Nieuwe takenreeks maken** selecteert u **Nieuwe aangepaste takenreeks maken**en klikt u vervolgens op **Volgende**.  

5.  Configureer op de pagina **Takenreeksinformatie** de volgende instellingen en klik op **Volgende**.  

    -   **Takenreeksnaam**: Geef een naam die de takenreeks identificeert.  

    -   **Beschrijving**: Geef een beschrijving van de takenreeks.  

    -   **Opstartinstallatiekopie**: Geef de opstartinstallatiekopie die het besturingssysteem wordt geïnstalleerd op de doelcomputer. Zie voor meer informatie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

6.  Voltooi de wizard.  

 Gebruik de volgende procedure om takenreeksstappen toe te voegen aan de aangepaste takenreeks.  

#### <a name="to-add-task-sequence-steps-to-the-custom-task-sequence"></a>Toevoegen van takenreeksstappen aan de aangepaste takenreeks  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  In de werkruimte **Softwarebibliotheek** **Besturingssystemen**uitvouwen en klikken op **Takenreeksen**en vervolgens de aangepaste takenreeks selecteren die u in de vorige procedure hebt gemaakt.  

3.  Klik op het tabblad **Start** in de groep **Takenreeks** op **Bewerken** om de takenreekseditor te starten.  

4.  De takenreeksstappen toevoegen om de VHD te wijzigen.  

5.  Klik op **OK** om de takenreekseditor af te sluiten.  

###  <a name="BKMK_ModifyVHD"></a> Een VHD wijzigen  
 Wanneer u een takenreeks voor de VHD hebt gemaakt, gebruikt u de wizard Virtuele harde schijven wijzigen om de VHD te wijzigen.  

 Gebruik de volgende procedure om een VHD te wijzigen.  

#### <a name="to-modify-a-vhd"></a>Een VHD wijzigen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  **Besturingssystemen** uitvouwen in de werkruimte **Softwarebibliotheek**, klikken op **Virtuele harde schijven**en vervolgens de VHD selecteren.  

3.  Klik op **Virtuele harde schijf wijzigen** op het tabblad **Start** in de groep **Virtuele harde schijf** om de wizard Virtuele harde schijf wijzigen te starten.  

    > [!NOTE]  
    >  Hyper-V moet zijn geïnstalleerd op de computer met de Configuration Manager-console van waaruit u de VHD's beheert of de **virtuele hardeschijf wijzigen** optie is niet ingeschakeld. Zie [Installatievereisten voor Hyper-V](http://technet.microsoft.com/library/cc731898.aspx)voor meer informatie over de vereisten voor Hyper-V.  

4.  Bevestig op de pagina **Algemeen** de volgende instellingen en klik vervolgens op **Volgende**.  

    -   **Naam**: Hiermee geeft u de unieke naam voor de VHD.  

    -   **Versie**: Hiermee geeft u het versienummer voor de VHD. Dit is een optionele instelling.  

    -   **Opmerking**: Hiermee geeft u de beschrijving voor de VHD.  

    -   **Pad**: Geeft de naam van het pad en de bestandsnaam op waar het VHD-bestand. U kunt deze instelling niet wijzigen.  

        > [!WARNING]  
        >  Configuration Manager moet hebben **schrijven** toegang hebben tot het opgegeven pad voor het maken van de VHD. Als Configuration Manager toegang tot het pad is mislukt, wordt de gekoppelde foutmelding in het distmgr.log-bestand op de siteserver gelogd.  

5.  Op de pagina **Takenreeks** de aangepaste takenreeks opgeven die u in de voorgaande sectie hebt gemaakt en vervolgens klikken op **Volgende**.  

6.  Selecteer, op de pagina **Distributiepunten** , een of meer distributiepunten die de inhoud bevatten die vereist is door de takenreeks, en klik vervolgens op **Volgende**.  

7.  Klik op de pagina **Aanpassing** op **Volgende**. Het proces om de VHD te wijzigen negeert alle instellingen die u op deze pagina hebt opgegeven.  

8.  Controleer de instellingen en klik vervolgens op **Volgende**. De wizard maakt de gewijzigde VHD.  

    > [!TIP]  
    >  De tijd om het proces van het wijzigen van de VHD af te ronden kan variëren. Terwijl de wizard door dit proces werkt, kunt u de volgende logboekbestanden controleren om de voortgang op te volgen. Standaard de logboeken bevinden zich op de computer waarop de Configuration Manager-console wordt uitgevoerd op %*ProgramFiles(x86)*%\Microsoft Configuration Manager\AdminConsole\AdminUILog.  
    >   
    >  -   **CreateTSMedia.log**: De wizard schrijft informatie in dit logboek bij het maken van de takenreeksmedia. Bekijk dit logboekbestand om de voortgang van de wizard op te volgen bij het maken van de zelfstandige media.  
    > -   **DeployToVHD.log**: De wizard schrijft informatie in dit logboek tijdens het door het proces om de VHD te wijzigen. Bekijk dit logboekbestand voor het opvolgen van de voortgang van de wizard voor alle stappen na het maken van de zelfstandige media.  
    >   
    >  U kunt ook Hyper-V Manager openen (als u de beheerprogramma's van Hyper-V op de computer hebt geïnstalleerd) en verbinding maken met de tijdelijke, door de wizard gemaakte virtuele machine om te zien of de takenreeks wordt uitgevoerd. U kunt vanuit de virtuele machine het bestand smsts.log controleren om de voortgang van de takenreeks te volgen. Wanneer er problemen zijn om een stap van de takenreeks uit te voeren, kunt u met behulp van dit logbestand de fout opsporen. Het bestand smsts.log bevindt zich in x: \windows\temp\smstslog\smsts.log voordat de harde schijf wordt geformatteerd en in c:\\_SMSTaskSequence\Logs\Smstslog\ nadat deze is geformatteerd. Nadat de stappen van de takenreeks zijn uitgevoerd, wordt de virtuele machine (standaard) na 5 minuten uitgeschakeld en verwijderd.  

##  <a name="BKMK_ApplyUpdates"></a> Software-updates toepassen op een VHD  
 Er worden regelmatig nieuwe software-updates uitgebracht die van toepassing zijn op het besturingssysteem in uw VHD. U kunt de toepasselijke software-updates op een VHD toepassen volgens een opgegeven planning. Op de planning die u opgeeft, is de software-updates die u selecteert door Configuration Manager van toepassing op de VHD.  

 Informatie over de VHD wordt in de sitedatabase opgeslagen, inclusief de software-updates die zijn toegepast op het tijdstip dat u de VHD maakte. Software-updates die zijn toegepast op de VHD sinds de eerste keer dat deze is gemaakt, worden tevens opgeslagen in de sitedatabase. Wanneer u de wizard start voor de toepassing van software-updates op de VHD, haalt de wizard een lijst van toepasselijke software-updates op die nog niet op de VHD zijn toegepast, waaruit u een selectie kan maken.  

 U kunt selecteren de **Doorgaan bij fout** -instelling voor Configuration Manager om te blijven toepassen van software-updates zelfs wanneer er een fout opgetreden bij het toepassen van een of meer van de software-updates die u hebt geselecteerd.  

> [!NOTE]  
>  De software-updates worden uit de inhoudbibliotheek op de siteserver gekopieerd.  

 Gebruik de volgende procedure om software-updates toe te passen op VHD.  

#### <a name="to-apply-software-updates-to-a-vhd"></a>Software-updates toepassen op een VHD  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Virtuele harde schijven**.  

3.  Selecteer de VHD voor de toepassing van software-updates.  

4.  Klik op het tabblad **Start** in de groep **Virtuele harde schijf** op **Updates plannen** om de wizard te starten.  

5.  Selecteer op de pagina **Updates kiezen** de software-updates die u op de VHD wilt toepassen en klik daarna op **Volgende**.  

6.  Geef, op de pagina **Schema instellen** , de volgende instellingen op, en klik vervolgens op **Volgende**.  

    1.  **Planning**: Geef de planning voor wanneer de software-updates worden toegepast op de VHD.  

    2.  **Doorgaan bij fout**: Selecteer deze optie om door te gaan naar het software-updates toepassen op de installatiekopie, zelfs wanneer er een fout opgetreden.  

7.  Verifieer de informatie op de pagina **Samenvatting** en klik vervolgens op **Volgende**.  

8.  Verifieer op de pagina **Voltooiing** dat de software-updates met succes zijn toegepast op de installatiekopie van het besturingssysteem.  

##  <a name="BKMK_ImportToVMM"></a> De VHD importeren voor System Center Virtual Machine Manager  
 System Center VMM is een beheeroplossing voor het gevirtualiseerde datacenter, waarmee u uw virtualisatiehost, netwerken en opslagbronnen kunt configureren en beheren om virtuele machines en services voor door u gemaakte privéclouds te maken en te implementeren. Nadat u een VHD in Configuration Manager maken, kunt u importeren en beheren van uw VHD door middel van VMM.  

> [!TIP]  
>  Controleer, voordat u een VHD naar VMM uploadt, of de VMM-console verbinding heeft met de VMM-beheerserver.  

 Gebruik de volgende procedure om een VHD naar VMM te importeren.  

#### <a name="to-import-a-vhd-to-vmm"></a>Een VHD naar VMM importeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Virtuele harde schijven**.  

3.  Klik op het tabblad **Start** in de groep **Virtuele harde schijf** op **Uploaden naar Virtual Machine Manager** om de wizard voor het uploaden naar de Virtual Machine Manager te starten.  

4.  Configureer op de pagina **Algemeen** de volgende instellingen en klik daarna op **Volgende**.  

    -   **De naam van de VMM-server**: Geef de FQDN van de computer waarop de VMM-beheerserver is geïnstalleerd. The wizard maakt verbinding met de VMM-beheerserver om de bibliotheekshares voor de server te downloaden.  

    -   **VMM-bibliotheekshare**: Geef de VMM-bibliotheekshare uit de vervolgkeuzelijst.  

    -   **Niet-versleutelde overdrachten gebruiken**: Selecteer deze instelling om over te dragen van het VHD-bestand met de VMM-beheerserver zonder het gebruik van versleuteling.  

5.  Controleer op de pagina Overzicht de instellingen en voltooi daarna de wizard. De tijdsduur voor het uploaden van de VHD kan verschillen op basis van de grootte van het VHD-bestand en de bandbreedte van het netwerk voor de VMM-beheerserver.  
