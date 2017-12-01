---
title: Nieuwe versie 1702
titleSuffix: Configuration Manager
description: "Meer informatie over deze wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1702 van System Center Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 409e26e1-7716-4f1d-a0ee-34feabf20792
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: a02d278b73d4627986b91e18d64a6523a2c7728f
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="what39s-new-in-version-1702-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1702 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1702 voor de huidige vertakking van System Center Configuration Manager is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1602 1606 of 1610 uitgevoerd. Het is ook beschikbaar als een basislijnversie die u gebruiken kunt bij het installeren van een nieuwe implementatie.

> [!TIP]  
> Een nieuwe site te installeren, moet u een basislijnversie van Configuration Manager.  
>  Meer informatie over:    
>   - [Nieuwe sites installeren](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Updates installeren op sites](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Basislijn- en updateversies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1702 van Configuration Manager.  

## <a name="deprecated-features-and-operating-systems"></a>Afgeschafte functies en -besturingssystemen
Meer informatie over ondersteuning voor wijzigingen voordat ze worden geïmplementeerd in [verwijderde en afgeschafte functies](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Versie 1702 geen ondersteuning meer voor de volgende producten:
- **SQL Server 2008 R2**, voor site-databaseservers. Afschaffing van ondersteuning is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database) op 10 juli 2015. Deze versie van SQL Server blijft ondersteund wanneer u een Configuration Manager versie voorafgaand aan versie 1702 gebruikt.
- **Windows Server 2008 R2**, voor sitesysteemservers en de meeste sitesysteemrollen. Afschaffing van ondersteuning is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) op 10 juli 2015. Deze versie van Windows blijft ondersteund wanneer u een Configuration Manager versie voorafgaand aan versie 1702 gebruikt.  
- **Windows Server 2008**, voor sitesysteemservers en de meeste sitesysteemrollen. Afschaffing van ondersteuning is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) op 10 juli 2015.
- **Windows XP Embedded**, als een client-besturingssysteem. Afschaffing is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) op 10 juli 2015. Deze versie van Windows blijft ondersteund wanneer u een Configuration Manager versie voorafgaand aan versie 1702 gebruikt.




## <a name="site-infrastructure"></a>Site-infrastructuur

### <a name="improvements-for-in-console-search"></a>Verbeteringen voor zoeken in de console
De volgende zijn verbeteringen voor het gebruik van zoeken in de Configuration Manager-console:
 - **Pad naar het object:**  
  Veel objecten ondersteunen nu een kolom genaamd **objectpad**.  Wanneer u zoeken en deze kolom in de weergave van de resultaten bevatten, kunt u het pad naar elk object kunt weergeven. Bijvoorbeeld, als u een zoekopdracht voor apps in het knooppunt toepassingen uitvoeren en zoekt ook onderliggende knooppunten de *objectpad* kolom in het resultatenvenster ziet u het pad voor elk object dat wordt geretourneerd.   

- **Behoud van zoektekst:**  
  Wanneer u tekst in het zoekvak invoeren en weer schakelen tussen het zoeken naar een onderliggende knooppunt en het huidige knooppunt, wordt de tekst die u hebt getypt nu behouden blijven en beschikbaar blijven voor een nieuwe zoekopdracht zonder deze opnieuw in te voeren.

- **Behoud van uw beslissing om te zoeken van onderliggende knooppunten:**  
 De optie die u kiest voor het zoeken in de *huidige knooppunt* of *alle onderliggende knooppunten* nu zich blijft voordoen wanneer u het knooppunt dat u in werkt wijzigt. Dit betekent dat u niet deze beslissing voortdurend opnieuw instellen wilt als u de console navigeert. Als u de console opent is de optie om te zoeken alleen het huidige knooppunt.


### <a name="send-feedback-from-the-configuration-manager-console"></a>Feedback verzenden vanuit de Configuration Manager-console

 U kunt de feedback in de console-opties gebruiken en feedback verzenden rechtstreeks naar het ontwikkelingsteam.

 U vindt de **Feedback** optie:
 -  In het lint, aan de linkerkant van het tabblad Start van elk knooppunt.  
    ![Lint](./media/feedback-home.png)

 -  Wanneer u met de rechtermuisknop op een object in de console.   
     ![De optie kopiëren en klik op](./media/feedback-option.png)   

 Kiezen **Feedback** opent uw browservenster met de [website voor Configuration Manager UserVoice-feedback over](https://go.microsoft.com/fwlink/?linkid=617029).


###  <a name="changes-for-updates-and-servicing"></a>Wijzigingen voor Updates en onderhoud
Hier volgen de wijzigingen voor Updates en onderhoud:

- **Locatie van knooppunt**   
  Na de installatie van versie 1702, de **Updates en onderhoud** knooppunt wordt weergegeven als een knooppunt op het hoogste niveau onder **beheer**. Het is niet langer een onderliggend knooppunt onderstaande **Cloudservices**.

- **Nieuwe updatestatussen**  
  Wanneer u de beschikbare updates in de console bekijken, moet u er twee nieuwe statussen zijn:  
  - **Beschikbaar voor installatie** -dit is een update die is gedownload en gereed om te installeren.
  - **Gereed voor download** -met deze update is beschikbaar, maar is niet gedownload. U kunt deze update wilt downloaden, maar deze is vervangen door een recentere update.


- **Eenvoudiger update keuzes**  
  De volgende keer dat uw infrastructuur in aanmerking komt voor twee of meer updates, wordt alleen de meest recente update gedownload. Bijvoorbeeld, als uw huidige siteversie is twee of meer ouder is dan de meest recente versie die beschikbaar is, is deze meest recente updateversie automatisch wordt gedownload.  

  U kunt downloaden en installeren van de andere beschikbare updates, zelfs wanneer ze niet de meest recente versie. Als u een oudere update downloadt, ontvangt u een waarschuwing dat de update is vervangen door een nieuwere versie. Voor het downloaden van een update die *beschikbaar voor Download*, selecteert u de update in de console en klik vervolgens op **downloaden**.

- **Verbeterde het opruimen van de oudere updates**   
  We hebben een automatische opschoning-functie die de overbodige downloads uit de map 'EasySetupPayload' op uw siteserver verwijdert toegevoegd. Omdat dit is geïntroduceerd in versie 1702, begint de opschonen na de installatie van een nieuwe update zoals een updatepakket of een toekomstige updateversie werken.  


### <a name="data-warehouse-service-point"></a>Datawarehouse-servicepunt
 Gebruik de datawarehouse-servicepunt op te slaan en te rapporteren over langetermijnopslag van historische gegevens voor uw Configuration Manager-implementatie.

 Het datawarehouse ondersteunt maximaal 2 TB aan gegevens, met een tijdstempel voor het bijhouden. Opslag van gegevens wordt gedaan door geautomatiseerde synchronisaties uit de sitedatabase van Configuration Manager met de datawarehouse-database. Deze gegevens zijn toegankelijk is vanaf uw Reporting Services-punt.

 Zie voor meer informatie [The Data Warehouse-servicepunt](/sccm/core/servers/manage/data-warehouse).


### <a name="peer-cache-improvements"></a>Verbeteringen voor peer-Cache
 Vanaf versie 1702, weigert een peer-cache-broncomputer een aanvraag voor inhoud wanneer de peer-cache-bron-computer voldoet aan een van de volgende voorwaarden:  
  -  In de modus voor laag accuvermogen is.
  -  CPU-belasting groter is dan 80% op het moment dat de inhoud wordt aangevraagd.
  -  Schijf-i/o heeft een *AvgDiskQueueLength* die groter is dan 10.
  -  Er zijn niet meer beschikbaar zijn verbindingen met de computer.   
Zie voor meer informatie **beperkte toegang tot een peer-cachebron** in [Peer-Cache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache).   

Daarnaast zijn drie nieuwe rapporten toegevoegd aan uw rapportagepunt. U kunt deze rapporten gebruiken om te begrijpen meer informatie over geweigerde aanvragen voor inhoud, inclusief welke grens groep-, computer- en inhoud is betrokken. Zie [bewaking](/sccm/core/plan-design/hierarchy/client-peer-cache#monitoring) in het onderwerp van peer-cache.

### <a name="content-library-cleanup-tool"></a>Inhoudsbibliotheek opschoonprogramma
 Gebruik de [Inhoudsbibliotheek opschoonprogramma](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) inhoud van distributiepunten verwijderen wanneer deze inhoud niet meer gekoppeld aan een toepassing is.


### <a name="use-the-oms-connector-with-the-azure-government-cloud"></a>Gebruik de OMS-connector met de cloud Azure Government
Verbinding maken met OMS Log Analytics in Microsoft Azure Government cloud kunt u de OMS-connector. Hiervoor moet u een configuratiebestand aanpassen voordat u de OMS-connector installeert, zodat de connector met de cloud van de overheid werken kunt. Zie voor meer informatie [de OMS-connector gebruiken met de cloud Azure Government](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig).

### <a name="software-update-points-are-added-to-boundary-groups"></a>Software-updatepunten zijn toegevoegd aan grensgroepen
Vanaf versie 1702, clients gebruiken grensgroepen om te zoeken naar een nieuw software-updatepunt en terugval en zoeken naar een nieuwe software-updatepunt als de huidige bewerking is niet langer toegankelijk. U kunt afzonderlijke software-updatepunten toevoegen aan verschillende grensgroepen om te bepalen welke servers een client kunt vinden. Zie voor meer informatie [software-updatepunten](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) in de [grensgroepen configureren](/sccm/core/servers/deploy/configure/boundary-groups) onderwerp.


<!-- ## Migration  -->

<!-- ## Client management  -->

## <a name="compliance-settings"></a>Instellingen voor naleving

### <a name="new-compliance-settings-for-ios"></a>Nieuwe instellingen voor naleving voor iOS

We hebt veel nieuwe instellingen voor iOS-apparaten zodat deze overeenkomen met die beschikbaar zijn met Microsoft Intune toegevoegd.
Zie voor een lijst met alle beschikbare instellingen [configuratie-items maken voor iOS en Mac OS X-apparaten worden beheerd door Intune](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client).


## <a name="application-management"></a>Toepassingsbeheer

### <a name="improved-support-for-windows-store-for-business-apps"></a>Verbeterde ondersteuning voor Windows Store voor bedrijven-apps

U kunt nu online gelicentieerde apps uit de Windows Store voor bedrijven om Windows 10-pc's die u beheert met de Configuration Manager-client te implementeren.
Zie voor meer informatie [apps beheren via de Windows Store voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

### <a name="check-for-running-executable-files-before-installing-an-application"></a>Controleer voor het uitvoeren van uitvoerbare bestanden voordat u een toepassing installeert

In de **eigenschappen** in het dialoogvenster van een implementatie hebt getypt, op de **gedrag installeren** tabblad kunt u een meer uitvoerbare bestanden die als actief is, wordt de installatie van het implementatietype blokkeren. De gebruiker moet de lopende uitvoerbaar bestand sluiten (of het automatisch kan worden gesloten voor implementaties met als doel vereist) voordat de implementatie van het type kan worden geïnstalleerd.

Als de toepassing is geïmplementeerd als **beschikbaar**, en een eindgebruiker probeert een toepassing te installeren, wordt hij gevraagd om te sluiten van alle actieve uitvoerbare bestanden opgegeven voordat ze de installatie kunnen voortzetten.

Als de toepassing is geïmplementeerd als **vereist**, en de optie **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type** is geselecteerd, zien ze een dialoogvenster waarin ze worden geïnformeerd dat uitvoerbare bestanden die u hebt opgegeven automatisch worden gesloten wanneer de deadline van de installatie van de toepassing is bereikt.

### <a name="app-management-improvements-for-hybrid-mdm"></a>App management verbeteringen voor hybride MDM

- [Volume-purchased iOS-apps implementeren op apparaatverzamelingen](#deploy-volume-purchased-ios-apps-to-device-collections)
- [Ondersteuning voor iOS Volume Purchase Program voor onderwijs](#support-for-ios-volume-purchase-program-for-education)
- [Ondersteuning voor meerdere volume purchase program-tokens](#support-for-multiple-volume-purchase-program-tokens)


## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen

### <a name="expire-stand-alone-media"></a>Verlopen van zelfstandige media
Wanneer u zelfstandige media maakt, zijn er nieuwe opties optionele begin- en verloopdatum datums instellen op de media. Deze instellingen zijn standaard uitgeschakeld. De datums worden vergeleken met de systeemtijd op de computer voordat de zelfstandige media wordt uitgevoerd. Wanneer de systeemtijd ouder dan de begintijd of hoger is dan de verlooptijd is, worden de zelfstandige media is niet gestart. Deze opties zijn ook beschikbaar via de cmdlet New-CMStandaloneMedia PowerShell. Zie voor meer informatie [zelfstandige media maken](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="package-id-displayed-in-task-sequence-steps"></a>Pakket-ID weergegeven in de stappen voor takenreeksen
Elke takenreeks die verwijst naar een pakket, stuurprogrammapakket, besturingssysteemkopie, opstartinstallatiekopie of upgradepakket voor besturingssysteem wordt nu weergegeven voor de pakket-ID van het object waarnaar wordt verwezen. Als een takenreeksstap verwijst naar een toepassing, wordt weergegeven de object-ID.

### <a name="support-for-additional-content-in-stand-alone-media"></a>Ondersteuning voor aanvullende inhoud in de zelfstandige media
Aanvullende inhoud wordt nu ondersteund in zelfstandige media. U kunt extra pakketten, stuurprogrammapakketten en toepassingen moeten worden geïnstalleerd op de media en de andere inhoud waarnaar wordt verwezen in de takenreeks selecteren. Voorheen is alleen inhoud waarnaar wordt verwezen in de takenreeks voorbereid op zelfstandige media. Zie voor meer informatie [zelfstandige media maken](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="hardware-inventory-collects-uefi-information"></a>Hardware-inventaris verzamelt UEFI-informatie
Een nieuwe hardware-inventarisklasse (**SMS_Firmware**) en de eigenschap (**UEFI**) zijn beschikbaar om te bepalen of een computer in UEFI-modus wordt gestart. Wanneer een computer in UEFI-modus is gestart de **UEFI** eigenschap is ingesteld op **TRUE**. Dit is standaard ingeschakeld in de hardware-inventaris. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

### <a name="improvements-to-software-center-warning-messages-for-high-impact-task-sequences"></a>Verbeteringen aan Software Center waarschuwingsberichten voor hoge impact takenreeksen
Deze release zijn de volgende verbeteringen aan Software Center waarschuwingsberichten voor takenreeksen hoge impact implementatie:

- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u nu een takenreeks wordt uitgevoerd, niet het besturingssysteemstation takenreeksen, waaronder als een implementatie met hoog risico configureren. Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie [beheren van implementaties met een hoog risico](/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u het meldingsbericht standaard gebruiken of maken van uw eigen aangepaste Meldingsbericht voor implementaties met hoge impact.
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u Software Center-eigenschappen, waaronder een herstart vereist is, Controleer de grootte van het downloadpakket van de takenreeks en de geschatte tijd worden uitgevoerd.
- Het standaardbericht implementatie met hoge impact voor in-place upgrades nu statussen uw apps, gegevens en instellingen automatisch gemigreerd. Voorheen het standaardbericht voor de installatie van een besturingssysteem wordt aangegeven dat alle apps, gegevens en instellingen zouden verloren gaan, die is niet true zijn voor een in-place upgrade.

Zie voor meer informatie [hoge impact taak reeks instellingen configureren](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)

### <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Terug naar vorige pagina wanneer een takenreeks mislukt
U kunt nu terugkeren naar een vorige pagina als u een takenreeks uitvoert en er een fout is. Vóór deze versie moest u de takenreeks opnieuw opstarten als er een fout is opgetreden. U kunt bijvoorbeeld de **vorige** knop in de volgende scenario's:

- Wanneer een computer wordt opgestart in Windows PE, wordt het dialoogvenster taak sequence bootstrap mogelijk weer voordat de takenreeks beschikbaar is. Wanneer u in dit scenario op Volgende klikt, wordt de laatste pagina van de takenreeks weergegeven met een bericht dat er geen takenreeksen beschikbaar zijn. Nu kunt u **vorige** opnieuw zoeken naar beschikbare takenreeksen. U kunt dit proces herhalen totdat de takenreeks beschikbaar is.
- Wanneer u een takenreeks uitvoert, maar de afhankelijke inhoud pakketten nog niet beschikbaar zijn op distributiepunten zijn, mislukt de takenreeks wordt uitgevoerd. U kunt nu de ontbrekende inhoud distribueren (indien deze nog niet is gedistribueerd) of wacht totdat de inhoud beschikbaar zijn op distributiepunten en klik op **vorige** het zoeken van de reeks taak opnieuw naar de inhoud hebben.

### <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Vooraf cache-inhoud voor beschikbare implementaties en takenreeksen
Vanaf versie 1702, voor beschikbare implementaties van takenreeksen, kunt u vooraf cache-inhoud gebruiken. Vooraf cache-inhoud biedt u de optie voor het toestaan van de client alleen de inhoud te downloaden van toepassing als de implementatie wordt ontvangen. Daarom wanneer de gebruiker klikt op **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf. Zie voor meer informatie [vooraf cache-inhoud configureren](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).

### <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Converteren van BIOS naar UEFI tijdens een upgrade ter plekke
Windows 10 auteurs Update introduceert een conversie van eenvoudige hulpprogramma dat automatiseert het proces voor het partitioneren van de harde schijf voor UEFI geschikte hardware en het hulpprogramma voor de conversie is geïntegreerd in de Windows 7 naar Windows 10 in-place upgradeproces. Wanneer u dit hulpprogramma worden gecombineerd met de upgradetakenreeks van uw besturingssysteem en het OEM-hulpprogramma dat de firmware van BIOS naar UEFI converteert, kunt u uw computers converteren vanuit BIOS naar UEFI tijdens een in-place upgrade naar de Update voor Windows 10 auteurs. Zie voor meer informatie [Takenreeksstappen voor het beheren van BIOS naar UEFI conversie](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

### <a name="improvements-to-the-install-applications-task-sequence-step"></a>Verbeteringen aan de takenreeks toepassingen installeren-stap
Deze versie zijn de volgende verbeteringen geïntroduceerd:
- Vergroot het maximum aantal toepassingen die u kunt installeren en 99 in de **toepassingen installeren** takenreeksstap. Het vorige maximum aantal is 9 toepassingen.
- Bij het toevoegen van toepassingen naar de **toepassingen installeren** takenreeksstap in de editor voor takenreeksen, kunt u nu meerdere toepassingen uit de **Selecteer de te installeren toepassing** deelvenster.

### <a name="improvements-to-the-auto-apply-driver-task-sequence"></a>Verbeteringen aan de takenreeks automatisch toepassen van stuurprogramma
Nieuwe takenreeksvariabelen zijn nu beschikbaar voor het configureren van de time-outwaarde op de takenreeksstap voor het automatisch toepassen van stuurprogramma bij het maken van HTTP-aanvragen voor catalogus. De volgende variabelen en de standaardwaarden (in seconden) zijn beschikbaar:
   - SMSTSDriverRequestResolveTimeOut  
     Standaardwaarde: 60
   - SMSTSDriverRequestConnectTimeOut  
     Standaardwaarde: 60
   - SMSTSDriverRequestSendTimeOut  
     Standaardwaarde: 60
   - SMSTSDriverRequestReceiveTimeOut  
     Standaardwaarde: 480

### <a name="windows-10-adk-tracked-by-build-version"></a>Windows 10 ADK bijgehouden door het build-versie
Windows 10 ADK wordt nu bijgehouden door het build-versie om te controleren of een meer ondersteunde ervaring bij het Windows 10-opstartinstallatiekopieën aanpassen. Als de site de Windows ADK voor Windows 10 versie 1607 gebruikt, kunnen er bijvoorbeeld opstartinstallatiekopieën met versie 10.0.14393 worden aangepast in de console. Zie voor meer informatie over het aanpassen van WinPE-versies [opstartinstallatiekopieën aanpassen](/sccm/osd/get-started/customize-boot-images).

### <a name="default-boot-image-source-path-can-no-longer-be-changed"></a>Bronpad opstartimage standaard kan niet meer worden gewijzigd.
Standaardopstartinstallatiekopieën worden beheerd door Configuration Manager en het bronpad standaard opstartimage kan niet meer worden gewijzigd in de Configuration Manager-console of met behulp van de Configuration Manager-SDK. U kunt blijven voor het configureren van een aangepaste bronpad voor aangepaste opstartinstallatiekopieën.

### <a name="default-boot-images-are-regenerated-after-upgrading-configuration-manager-to-a-new-version"></a>Standaardopstartinstallatiekopieën worden opnieuw gegenereerd na de upgrade van Configuration Manager naar een nieuwe versie
In deze release, vanaf het moment dat u de Windows ADK-versie bijwerken en vervolgens gebruiken om updates en onderhoud voor het installeren van de meest recente versie van Configuration Manager, Configuration Manager genereert de standaardopstartinstallatiekopieën. Dit omvat het nieuwe venster PE-versie van de bijgewerkte Windows ADK, de nieuwe versie van de Configuration Manager-client, stuurprogramma's, aanpassingen, enzovoort. Aangepaste opstartinstallatiekopieën worden niet gewijzigd. Zie voor meer informatie [opstartinstallatiekopieën beheren](/sccm/osd/get-started/manage-boot-images#BKMK_BootImageDefault).

## <a name="software-updates"></a>Software-updates

### <a name="deploy-office-365-apps-to-clients"></a>Office 365-apps implementeren op clients
Vanaf versie 1702, vanuit het dashboard beheer van Office 365 Client kunt u het installatieprogramma van Office 365 waarmee u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud levering bedrijfsnetwerken (CDN) en de bestanden kunnen worden geïmplementeerd als een toepassing in Configuration Manager starten. Zie voor meer informatie [beheren van Office 365 ProPlus-updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps).

> [!IMPORTANT]
> De Office 365-app die u maakt en implementeert met behulp van de Wizard toepassing van Office 365 in Configuration Manager wordt niet automatisch worden beheerd door Configuration Manager totdat u de **beheer van de Office 365 Client opnieuw inschakelen** clientagent voor software-updates instellen. Zie voor meer informatie [over clientinstellingen](/sccm/core/clients/deploy/about-client-settings).

### <a name="manage-express-installation-files-for-windows-10-updates"></a>Bestanden voor snelle installatie voor Windows 10-updates beheren
Vanaf versie 1702, ondersteunt Configuration Manager voor de bestanden voor snelle installatie voor Windows 10-updates. Wanneer u een ondersteunde versie van Windows 10, kunt u Configuration Manager-instellingen voor het downloaden van alleen de wijzigingen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update. Zonder bestanden voor snelle installatie Configuration Manager de volledige 10 cumulatieve Update voor Windows (met inbegrip van alle updates van afgelopen maanden) downloadt elke maand. Het gebruik van bestanden voor snelle installatie biedt voor kleinere downloaden en installatie sneller op clients. Zie voor meer informatie [bestanden voor snelle installatie voor Windows 10-updates beheren](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).


<!-- ## Reporting  -->

<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>Beheer van mobiele apparaten

### <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android en iOS-versies worden niet meer targetable in wizards voor hybride MDM maken

Vanaf versie 1702 voor hybride mobile device management (MDM) is hoeft niet langer te gericht op specifieke versies van Android en iOS bij het maken van nieuwe beleidsregels en profielen voor Intune-beheerde apparaten. In plaats daarvan, kies een van de volgende typen apparaten:

- Android
- Samsung KNOX Standard 4.0 en hoger
- iPhone
- iPad

Deze wijziging is van invloed op de wizards voor het maken van de volgende items:

- Configuratie-items
- Nalevingsbeleid
- Certificaatprofielen
- E-mailprofielen
- VPN-profielen
- Wi-Fi-profielen

Met deze wijziging kunnen hybride implementaties ondersteuning bieden sneller op nieuwe versies van Android en iOS zonder een nieuwe release van Configuration Manager of een uitbreiding. Wanneer een nieuwe versie wordt ondersteund in de zelfstandige versie van Intune, kunnen gebruikers zich kunnen hun mobiele apparaten voor die versie te upgraden.

Mobiele besturingssysteemversies zijn om te voorkomen dat u problemen bij een upgrade van eerdere versies van Configuration Manager, nog steeds beschikbaar in de eigenschappenpagina's voor deze items. Als u nog steeds een specifieke versie als doel wilt, kunt u de nieuw item maken en geef vervolgens de doelversie van de eigenschappenpagina van het nieuwe item. 

> [!NOTE]
> De laatste versie op de mobiele besturingssysteem beschikbaar zijn in de eigenschappenpagina's geldt voor die versie en alle latere versies. Eigenschappenpagina's bieden de volgende opties voor specifieke besturingssystemen later zijn dan 7, Android en iOS 10: 
> - **Android 7 en hoger**
> - **Alle iOS 10 en hoger iPhone of iPod touch-apparaten**
> - **Alle iOS 10 en hoger iPad-apparaten**

### <a name="android-for-work-support"></a>Android voor Work-ondersteuning
Beginnen met 1702, hybride mobile device management met Microsoft Intune biedt nu ondersteuning voor Android voor werk apparaatinschrijving en -beheer. Beheerde Android voor werk apparaat richtlijnen:

- [Android voor werk apparaten inschrijven](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)
- [Goedkeuren en implementeren van Android voor bedrijfs-apps](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Configuratie-items maken voor Android for Work.](/sccm/mdm/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-for-work-configuration-items)
- [Selectief wissen op Android voor Work-apparaten](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)
- [E-mailprofielen voor Android for Work.](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Nalevingsbeleid voor Android for Work.](/sccm/mdm/deploy-use/create-compliance-policy)


### <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Volume-purchased iOS-apps implementeren op apparaatverzamelingen

U kunt nu gelicentieerde apps implementeren op apparaten, evenals gebruikers. Afhankelijk van de apps mogelijkheid om apparaat-licentieverlening te ondersteunen, wordt een juiste licentie wordt geclaimd bij het implementeren, als volgt:

|||||
|-|-|-|-|
|Versie van Configuration Manager|App ondersteunt apparaat licentieverlening?|Implementatietype van de verzameling|De geclaimde licentie|
|Ouder dan 1702|Ja|Gebruiker|Gebruikerslicentie|
|Ouder dan 1702|Nee|Gebruiker|Gebruikerslicentie|
|Ouder dan 1702|Ja|Apparaat|Gebruikerslicentie|
|Ouder dan 1702|Nee|Apparaat|Gebruikerslicentie|
|1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Ja|Apparaat|Apparaatlicentie|
|1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

Zie voor meer informatie over volume-purchased iOS-apps, [volume-purchased iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-ios-volume-purchase-program-for-education"></a>Ondersteuning voor iOS Volume Purchase Program voor onderwijs

U kunt nu ook implementeren en bijhouden van apps die u hebt aangeschaft via de iOS Volume Purchase Program voor onderwijs.
Zie voor meer informatie over volume-purchased iOS-apps, [volume-purchased iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-multiple-volume-purchase-program-tokens"></a>Ondersteuning voor meerdere volume purchase program-tokens

U kunt meerdere Apple volume purchase program-tokens nu koppelen met Configuration Manager.
Zie voor meer informatie over volume-purchased iOS-apps, [volume-purchased iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-line-of-business-apps-in-windows-store-for-business"></a>Ondersteuning voor LOB-apps in Windows Store voor bedrijven

U kunt aangepaste LOB-apps vanuit de Windows Store voor bedrijven nu synchroniseren.

### <a name="conditional-access-device-compliance-policy-improvements"></a>Voorwaardelijke toegang apparaat naleving beleid verbeteringen

Een nieuw apparaat naleving beleidsregel is beschikbaar waarmee u toegang tot bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang, wanneer gebruikers apps die deel van een niet-compatibele lijst met apps uitmaken blokkeren. De niet-compatibele lijst met apps kan worden gedefinieerd door de beheerder bij het toevoegen van de nieuwe regel compatibele **Apps die niet kunnen worden geïnstalleerd**. Deze regel vereist dat de beheerder om in te voeren de **Appnaam**, wordt de **App-ID**, en de **App Publisher** (optioneel) wanneer een app toe te voegen aan de lijst met niet-compatibele. Deze instelling geldt alleen voor iOS en Android-apparaten.

Dit helpt bovendien organisaties lekken van gegevens via niet-beveiligde apps te beperken en het verbruik van veel gegevens via bepaalde apps te voorkomen.

- Meer informatie [de werking van beleid voor apparaatcompatibiliteit](/sccm/mdm/deploy-use/device-compliance-policies).
- Meer informatie [nalevingsbeleid voor apparaten maken](/sccm/mdm/deploy-use/create-compliance-policy).

### <a name="new-mobile-threat-defense-monitoring-tools"></a>Nieuwe mobiele Threat verdediging controlehulpprogramma 's

Vanaf versie 1702, hebt u nieuwe manieren om de compatibiliteitsstatus met uw serviceprovider Mobile Threat verdediging te controleren.

- Meer informatie [Mobile Threat verdediging naleving controleren](https://docs.microsoft.com/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="protect-devices"></a>Apparaten beveiligen

### <a name="detect-outdated-antimalware-client-versions"></a>Verouderde antimalwareclients detecteren
U kunt een waarschuwing om ervoor te zorgen Endpoint Protection-clients zijn niet verouderde vanaf versie 1702 kunt configureren. Zie voor meer informatie [waarschuwing voor verouderde malware client](/sccm/protect/deploy-use/endpoint-configure-alerts#detect-outdated-antimalware-client-versions).

### <a name="device-health-attestation-updates"></a>Apparaatupdates health attestation
Apparaat health attestation-service voor on-premises clients kunnen nu worden geconfigureerd en beheerd vanaf het beheerpunt. Zie voor meer informatie [Health Attestation](/sccm/core/servers/manage/health-attestation).

### <a name="certificate-profiles-for-windows-hello-for-business"></a>Certificaatprofielen voor Windows Hello voor bedrijven

Als u van plan bent voor het opslaan van certificaatprofielen in het Windows Hello voor bedrijven-sleutelcontainer, en het profiel voor de smartcard voor aanmelding EKU gebruikt, moet u machtigingen voor de sleutel registratie om te controleren of dat het certificaat op de juiste wijze gevalideerd configureren.
Zie voor meer informatie [Windows Hello voor bedrijven-instellingen](/sccm/protect/deploy-use/windows-hello-for-business-settings).

### <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nieuwe Windows Hello voor bedrijven kennisgeving voor eindgebruikers
Een nieuwe Windows 10-melding informeert gebruikers dat ze extra acties voltooid Windows Hello voor bedrijven-instellingen (bijvoorbeeld het instellen van een PINCODE) moeten uitvoeren.
