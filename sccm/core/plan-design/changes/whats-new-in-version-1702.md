---
title: Nieuwe versie 1702 | Microsoft-documenten
description: "Meer informatie over deze wijzigingen en nieuwe functies die zijn geïntroduceerd in versie 1702 van System Center Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 409e26e1-7716-4f1d-a0ee-34feabf20792
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: a2954b3c6f9a09b7246347e780c4cfc49ba39ca1
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1702-of-system-center-configuration-manager"></a>Wat &#39; s is nieuw in versie 1702 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1702 voor System Center Configuration Manager huidige vertakking is beschikbaar als een update in de console voor eerder geïnstalleerde sites waarop versie 1602, 1606 of 1610. Het is ook beschikbaar als een basislijn-versie die u gebruiken kunt bij het installeren van een nieuwe implementatie.

> [!TIP]  
> Een nieuwe site installeren, moet u een basislijn-versie van Configuration Manager.  
>  Meer informatie over:    
>   - [Installatie van nieuwe sites](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Installatie van updates op sites](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Basislijn en update-versies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

De volgende secties bevatten informatie over wijzigingen en nieuwe mogelijkheden die is geïntroduceerd in versie 1702 van Configuration Manager.  

## <a name="deprecated-features-and-operating-systems"></a>Verouderde functies en besturingssystemen
Meer informatie over ondersteuning voor wijzigingen voordat ze worden geïmplementeerd in [verwijderd en afgeschafte functies](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Versie 1702 geen ondersteuning meer voor de volgende producten:
- **SQL Server 2008 R2**, voor sitedatabaseservers. Buitengebruikstelling van ondersteuning is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database) op 10 juli 2015. Deze versie van SQL Server blijft ondersteund wanneer u een Configuration Manager-versie voor versie 1702.
- **Windows Server 2008 R2**, voor de sitesysteemservers en de meeste sitesysteemrollen. Buitengebruikstelling van ondersteuning is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) op 10 juli 2015. Deze versie van Windows blijft ondersteund wanneer u een Configuration Manager-versie voor versie 1702.  
- **Windows Server 2008**, voor de sitesysteemservers en de meeste sitesysteemrollen. Buitengebruikstelling van ondersteuning is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) op 10 juli 2015.
- **Windows XP Embedded**, als een client-besturingssysteem. Afschaffing is [eerst aangekondigd](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) op 10 juli 2015. Deze versie van Windows blijft ondersteund wanneer u een Configuration Manager-versie voor versie 1702.




## <a name="site-infrastructure"></a>Site-infrastructuur

### <a name="improvements-for-in-console-search"></a>Verbeteringen voor de zoekopdracht console
Hier volgen verbeteringen op het gebruik van zoeken in de Configuration Manager-console:
 - **Pad naar het object:**  
  Veel objecten ondersteunen nu een kolom genaamd **objectpad**.  Als u zoeken en deze kolom in uw resultaten weergeven weglaat, kunt u het pad naar elk object weergeven. Als u een zoekopdracht voor apps uitvoeren in het knooppunt toepassingen en zoekt zijn onderliggende knooppunten, bijvoorbeeld de *objectpad* kolom in het resultatenvenster ziet u het pad naar elk object dat wordt geretourneerd.   

- **Behoud van zoektekst:**  
  Wanneer u tekst in het tekstvak Zoeken invoeren en vervolgens schakelen tussen het doorzoeken van een onderliggende knooppunt en het huidige knooppunt, wordt de tekst die u hebt getypt nu blijven behouden en beschikbaar blijven voor een nieuwe zoekopdracht zonder deze opnieuw in.

- **Behoud van uw keuze om te zoeken naar onderliggende knooppunten:**  
 De optie die u kiest voor het zoeken in de *huidige knooppunt* of *alle onderliggende knooppunten* nu zich blijft voordoen wanneer u het knooppunt dat u in werkt wijzigt. Dit nieuwe gedrag betekent dat u niet voortdurend dit besluit opnieuw instellen wilt als u de console verplaatsen. Wanneer u de console opent is de optie om te zoeken alleen het huidige knooppunt.


### <a name="send-feedback-from-the-configuration-manager-console"></a>Feedback verzenden vanuit de Configuration Manager-console

 U kunt de feedbackopties in de console gebruiken om feedback te verzenden rechtstreeks naar het ontwikkelteam.

 U vindt de **Feedback** optie:
 -  In het lint aan de linkerkant van het tabblad Start van elk knooppunt.  
    ![Lint](./media/feedback-home.png)

 -  Wanneer u met de rechtermuisknop op een object in de console.   
     ![Tabelkolom-optie](./media/feedback-option.png)   

 Kiezen **Feedback** Hiermee opent u de browser en de [Configuration Manager UserVoice-feedback website](https://go.microsoft.com/fwlink/?linkid=617029).


###  <a name="changes-for-updates-and-servicing"></a>Wijzigingen voor Updates en onderhoud
De volgende zijn wijzigingen voor Updates en onderhoud:

- **Locatie van knooppunt**   
  Na de installatie van versie 1702, de **Updates en onderhoud** knooppunt wordt weergegeven als een knooppunt op het hoogste niveau onder **beheer**. Het is niet langer een onderliggend knooppunt van onderstaande **Cloudservices**.

- **Nieuwe updatestatussen**  
  Wanneer u de beschikbare updates in de console weergeven, moet u er twee nieuwe statussen zijn:  
  - **Beschikbaar voor installatie** -dit is een update die is gedownload en gereed voor installatie.
  - **Gereed voor download** -met deze update is beschikbaar, maar is niet gedownload. U kunt deze update wilt downloaden, maar deze is vervangen door een meer recente update.


- **Eenvoudigere update keuzes**  
  De volgende keer die uw infrastructuur in aanmerking komt voor twee of meer updates, wordt alleen de meest recente update gedownload. Bijvoorbeeld, als uw huidige siteversie is twee of meer ouder zijn dan de meest recente versie die beschikbaar is, die meest recente updateversie automatisch wordt gedownload.  

  U kunt kiezen om te downloaden en installeren van de andere beschikbare updates, zelfs wanneer ze niet de meest recente versie. Als u een oudere update downloadt, ontvangt u een waarschuwing dat de update is vervangen door een nieuwere versie. Voor het downloaden van een update die is *beschikbaar voor Download*, selecteert u de update in de console en klik vervolgens op **downloaden**.

- **Verbeterde het opruimen van oudere updates**   
  We hebben een automatische opschonen-functie waarmee de overbodige downloads worden verwijderd uit de map 'EasySetupPayload' op de siteserver toegevoegd. Omdat dit is geïntroduceerd met versie 1702, begint opschonen na de installatie van een nieuwe update als een updatepakket of toekomstige updateversie werken.  


### <a name="data-warehouse-service-point"></a>Gegevens datawarehouse-servicepunt
 Het datawarehouse-servicepunt kunnen opslaan en maak een rapport over langetermijnopslag van historische gegevens voor uw Configuration Manager-implementatie gebruiken.

 Het datawarehouse ondersteunt maximaal 2 TB aan gegevens met een tijdstempel voor het bijhouden. Opslag van gegevens wordt gerealiseerd door geautomatiseerde synchronisaties uit de sitedatabase van Configuration Manager naar de datawarehouse-database. Deze informatie is toegankelijk is vanaf de Reporting Services-punt.

 Zie voor meer informatie [The Data Warehouse-servicepunt](/sccm/core/servers/manage/data-warehouse).


### <a name="peer-cache-improvements"></a>Peer-Cache verbeteringen
 Vanaf versie 1702 weigeren peer cache broncomputer een aanvraag voor inhoud wanneer de broncomputer peer cache voldoet aan de volgende omstandigheden:  
  -  In de modus voor laag accuvermogen is.
  -  CPU-belasting groter is dan 80% op het moment dat de inhoud wordt aangevraagd.
  -  Schijf-i/o heeft een *AvgDiskQueueLength* die groter is dan 10.
  -  Er zijn niet meer beschikbaar zijn verbindingen met de computer.   
Zie voor meer informatie **beperkte toegang tot een bron van de cache peer** in [Peercache voor Configuration Manager-clients](/sccm/core/plan-design/hierarchy/client-peer-cache).   

Daarnaast worden drie nieuwe rapporten toegevoegd aan het rapportagepunt. U kunt deze rapporten gebruiken om te begrijpen meer informatie over geweigerde aanvragen voor inhoud, inclusief welke grens groep, de computer en de inhoud is betrokken. Zie [bewaking](/sccm/core/plan-design/hierarchy/client-peer-cache#monitoring) in het onderwerp peer-cache.

### <a name="content-library-cleanup-tool"></a>Inhoudsbibliotheek-hulpprogramma
 Gebruik de [Inhoudsbibliotheek hulpprogramma](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) inhoud van distributiepunten verwijderen wanneer deze inhoud niet meer gekoppeld aan een toepassing is.


### <a name="use-the-oms-connector-with-the-azure-government-cloud"></a>Gebruik de OMS connector met de overheid van de Azure-cloud
Verbinding maken met OMS logboek Analytics in Microsoft Azure overheid cloud kunt u de connector OMS. Hiervoor moet u een configuratiebestand hebt gewijzigd voordat u de connector OMS installeren zodat de connector met de overheid van de cloud werken kan. Zie voor meer informatie [OMS connector gebruiken met de overheid van de Azure-cloud](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig).

### <a name="software-update-points-are-added-to-boundary-groups"></a>Software-updatepunten zijn toegevoegd aan grensgroepen
Vanaf versie 1702 clients gebruiken grensgroepen om te zoeken naar een nieuw software-updatepunt en terugval te zoeken naar een nieuwe software-updatepunt als hun huidige abonnement niet meer toegankelijk is. U kunt afzonderlijke software-updatepunten toevoegen aan andere grensgroepen om te bepalen welke servers die een client kunt vinden. Zie voor meer informatie [software-updatepunten](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) in de [grensgroepen configureren](/sccm/core/servers/deploy/configure/boundary-groups) onderwerp.


<!-- ## Migration  -->

<!-- ## Client management  -->

## <a name="compliance-settings"></a>Instellingen voor naleving

### <a name="new-compliance-settings-for-ios"></a>Nieuwe compatibiliteitsinstellingen voor iOS

Veel nieuwe instellingen voor iOS-apparaten om te voldoen aan die beschikbaar zijn met Microsoft Intune toegevoegd.
Zie voor een lijst met alle beschikbare instellingen [configuratie-items maken voor iOS en Mac OS X-apparaten die worden beheerd door Intune](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client).


## <a name="application-management"></a>Toepassingsbeheer

### <a name="improved-support-for-windows-store-for-business-apps"></a>Verbeterde ondersteuning voor Windows Store voor Business-apps

U kunt nu online gelicentieerde apps vanuit de Windows Store voor bedrijven om Windows 10-computers te beheren met behulp van de Configuration Manager-client te implementeren.
Zie voor meer informatie [apps beheren vanuit de Windows Store voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

### <a name="check-for-running-executable-files-before-installing-an-application"></a>Controleer voor het uitvoeren van uitvoerbare bestanden voordat de installatie van een toepassing

In de **eigenschappen** in het dialoogvenster van een implementatie hebt getypt, op de **gedrag installeren** tabblad kunt u een meer uitvoerbare bestanden die als uitgevoerd, wordt de installatie van het implementatietype geblokkeerd. De gebruiker moet het actief uitvoerbaar bestand sluiten (of het automatisch kan worden gesloten voor implementaties met als doel vereist) voor de implementatie van het type kan worden geïnstalleerd.

Als de toepassing is geïmplementeerd als **beschikbaar**, en een eindgebruiker probeert een toepassing te installeren, wordt ze gevraagd om te sluiten van een actieve uitvoerbare bestanden die u hebt opgegeven voordat de installatie kunt voortzetten.

Als de toepassing is geïmplementeerd als **vereist**, en de optie **automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type** is geselecteerd, zien ze een dialoogvenster dat hen informeert dat uitvoerbare bestanden die u hebt opgegeven automatisch gesloten wordt na het verstrijken van de installatiedeadline voor de toepassing.

### <a name="app-management-improvements-for-hybrid-mdm"></a>App management verbeteringen voor hybride MDM

- [Volume aangeschaft iOS-apps implementeren op apparaatverzamelingen](#deploy-volume-purchased-ios-apps-to-device-collections)
- [Ondersteuning voor iOS Volume Purchase Program voor onderwijs](#support-for-ios-volume-purchase-program-for-education)
- [Ondersteuning voor meerdere volume aankoop programma tokens](#support-for-multiple-volume-purchase-program-tokens)


## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen

### <a name="expire-stand-alone-media"></a>Zelfstandige media verlopen
Wanneer u een zelfstandige media maakt, zijn er nieuwe opties voor het optionele begin- en verloopdatum datums instellen voor de media. Deze instellingen zijn standaard uitgeschakeld. De datums worden vergeleken met de systeemtijd op de computer voordat de zelfstandige media wordt uitgevoerd. Wanneer de systeemtijd ouder is dan de begintijd of hoger is dan de verlooptijd is, wordt de zelfstandige media niet gestart. Deze opties zijn ook beschikbaar via de cmdlet New-CMStandaloneMedia PowerShell. Zie voor meer informatie, [maken van zelfstandige media](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="package-id-displayed-in-task-sequence-steps"></a>Pakket-ID weergegeven in stappen van takenreeksen
Elke stap van de takenreeks die verwijst naar een pakket, stuurprogrammapakket, de installatiekopie van het besturingssysteem, opstartinstallatiekopie of upgradepakket besturingssysteem wordt nu weergegeven met de pakket-ID van het object waarnaar wordt verwezen. Wanneer een takenreeksstap verwijst naar een toepassing, wordt weergegeven de object-ID.

### <a name="support-for-additional-content-in-stand-alone-media"></a>Ondersteuning voor aanvullende inhoud in zelfstandige media
Aanvullende inhoud wordt nu ondersteund in zelfstandige media. U kunt extra pakketten en stuurprogrammapakketten toepassingen moeten worden geïnstalleerd op de media samen met de andere inhoud waarnaar wordt verwezen in de takenreeks selecteren. Alleen de inhoud waarnaar wordt verwezen in de takenreeks is eerder voorbereid op zelfstandige media. Zie voor meer informatie, [maken van zelfstandige media](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="hardware-inventory-collects-uefi-information"></a>Hardware-inventaris verzamelt informatie UEFI
Een nieuwe hardware-inventarisklasse (**SMS_Firmware**) en de eigenschap (**UEFI**) zijn beschikbaar om te bepalen of een computer in UEFI-modus start. Wanneer een computer in UEFI-modus wordt gestart de **UEFI** eigenschap is ingesteld op **waar**. Dit is standaard ingeschakeld in de hardware-inventaris. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

### <a name="improvements-to-software-center-warning-messages-for-high-impact-task-sequences"></a>Verbeteringen in Software Center waarschuwingsberichten voor indrukwekkende takenreeksen
Deze versie bevat de volgende verbeteringen in Software Center waarschuwingsberichten voor takenreeksen indrukwekkende implementatie:

- In de eigenschappen voor de taak nu kunt u een takenreeks, die niet het besturingssysteemstation takenreeksen, als een implementatie met een hoog risico. Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie, [met een hoog risico implementaties beheren](/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u het meldingsbericht standaard gebruiken of maken van uw eigen aangepaste Meldingsbericht voor indrukwekkende implementaties.
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u Software Center eigenschappen, waaronder een opnieuw opstarten is vereist, moeten de downloadgrootte van de takenreeks, en de geschatte runtime.
- De indrukwekkende implementatie standaardbericht voor in-place upgrades nu statussen dat apps gegevens en instellingen worden automatisch gemigreerd. Eerder het standaardbericht voor de installatie van een besturingssysteem wordt aangegeven dat alle apps, gegevens en instellingen zou verloren gaan, die niet voor een upgrade ter plaatse waar is.

Zie voor meer informatie, [instellingen indrukwekkende takenreeks configureren](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)

### <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Teruggaan naar vorige pagina wanneer een takenreeks mislukt
U kunt nu teruggaan naar vorige pagina wanneer u een takenreeks uitvoert en er een fout is opgetreden is. Vóór deze release moest u de takenreeks wordt opnieuw gestart als er een fout opgetreden is. U kunt bijvoorbeeld de **vorige** knop in de volgende scenario's:

- Wanneer een computer in Windows PE is opgestart, wordt het dialoogvenster taak volgorde bootstrap mogelijk weergegeven voordat de takenreeks beschikbaar is. Wanneer u in dit scenario op Volgende klikt, wordt de laatste pagina van de takenreeks weergegeven met een bericht dat er geen takenreeksen beschikbaar zijn. Nu kunt u **vorige** Zoek opnieuw voor de beschikbare takenreeksen. U kunt dit proces herhalen totdat de takenreeks beschikbaar is.
- Wanneer u een takenreeks uitvoert, maar afhankelijke inhoudspakketten nog niet beschikbaar zijn op distributiepunten zijn, mislukt de takenreeks. U kunt nu de ontbrekende inhoud distribueren (als deze nog niet is gedistribueerd) of wacht totdat de inhoud moet beschikbaar zijn op distributiepunten en klik op **vorige** taak volgorde zoeken opnieuw naar de inhoud hebben.

### <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Vooraf cache-inhoud voor beschikbare implementaties en takenreeksen
Vanaf versie 1702, voor beschikbare implementaties van takenreeksen, kunt u vooraf cache-inhoud gebruiken. Vooraf cache-inhoud biedt u de optie om de client alleen de inhoud te downloaden van toepassing als de implementatie wordt ontvangen. Daarom wanneer de gebruiker **installeren** in Software Center, de inhoud gereed is en de installatie begint snel omdat de inhoud op de lokale vaste schijf. Zie voor meer informatie, [vooraf cache-inhoud configureren](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).

### <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Omzetten van BIOS UEFI tijdens een upgrade ter plekke
Windows 10 beveiligingsbeheerder Update introduceert een eenvoudige conversie-hulpprogramma dat automatiseert het proces voor het partitioneren van de harde schijf voor UEFI-functionaliteit hardware en het hulpprogramma conversie integreert in de Windows 7 voor Windows 10 in-place upgradeproces. Wanneer u dit hulpprogramma worden gecombineerd met de upgrade besturingssysteemtaaksequentie en het OEM-hulpprogramma dat de firmware van BIOS naar UEFI converteert, kunt u uw computers converteren van BIOS naar UEFI tijdens een upgrade ter plekke met Windows 10 beveiligingsbeheerder Update. Zie voor meer informatie, [Takenreeksstappen voor het beheren van BIOS UEFI conversie](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

### <a name="improvements-to-the-install-applications-task-sequence-step"></a>Verbeteringen in de takenreeks toepassingen installeren stap
Deze versie van de volgende verbeteringen geïntroduceerd:
- Vergroot het maximum aantal toepassingen die u kunt installeren en 99 in de **toepassingen installeren** takenreeksstap. Het vorige maximum aantal is 9-Apps.
- Wanneer u toepassingen toevoegt de **toepassingen installeren** takenreeksstap in de takenreekseditor, kunt u nu meerdere toepassingen uit de **Selecteer de te installeren toepassing** deelvenster.

### <a name="improvements-to-the-auto-apply-driver-task-sequence"></a>Verbeteringen in de takenreeks automatisch toepassen stuurprogramma
Nieuwe takenreeksvariabelen zijn nu beschikbaar voor de time-outwaarde configureren op de takenreeksstap voor het automatisch toepassen stuurprogramma bij het maken van HTTP-aanvragen van catalogus. De volgende variabelen en standaardwaarden (in seconden) zijn beschikbaar:
   - SMSTSDriverRequestResolveTimeOut  
     Standaardwaarde: 60
   - SMSTSDriverRequestConnectTimeOut  
     Standaardwaarde: 60
   - SMSTSDriverRequestSendTimeOut  
     Standaardwaarde: 60
   - SMSTSDriverRequestReceiveTimeOut  
     Standaardwaarde: 480

### <a name="windows-10-adk-tracked-by-build-version"></a>Windows 10 ADK bijgehouden door build-versie
De Windows-ADK 10 wordt nu bijgehouden door buildversie zodat een meer ondersteunde ervaring wanneer Windows 10-opstartinstallatiekopieën aanpassen. Bijvoorbeeld, als de site de Windows ADK voor Windows 10 versie 1607 gebruikt, worden opstartinstallatiekopieën met versie 10.0.14393 aangepast in de console. Zie voor meer informatie over het aanpassen van de WinPE-versies [opstartinstallatiekopieën aanpassen](/sccm/osd/get-started/customize-boot-images).

### <a name="default-boot-image-source-path-can-no-longer-be-changed"></a>Standaard opstart bronpad kan niet meer worden gewijzigd
Standaardopstartinstallatiekopieën worden beheerd door Configuration Manager en het bronpad standaard opstart-installatiekopie kan niet meer worden gewijzigd in de Configuration Manager-console of met behulp van de Configuration Manager-SDK. U kunt een aangepaste bronpad voor aangepaste opstartinstallatiekopieën configureren blijven.

### <a name="default-boot-images-are-regenerated-after-upgrading-configuration-manager-to-a-new-version"></a>De standaardopstartinstallatiekopieën worden opnieuw gegenereerd na de upgrade van Configuration Manager naar een nieuwe versie
In deze release vanaf het moment dat u de Windows ADK-versie bijwerken en vervolgens met updates en onderhoud Installeer de nieuwste versie van Configuration Manager, Configuration Manager genereert de standaardopstartinstallatiekopieën. Dit omvat het nieuwe venster PE-versie van de bijgewerkte Windows ADK, de nieuwe versie van de Configuration Manager-client, stuurprogramma's, aanpassingen, enzovoort. Aangepaste opstartinstallatiekopieën niet gewijzigd. Zie voor meer informatie, [opstartinstallatiekopieën beheren](/sccm/osd/get-started/manage-boot-images#BKMK_BootImageDefault).

## <a name="software-updates"></a>Software-updates

### <a name="deploy-office-365-apps-to-clients"></a>Office 365-apps implementeren op clients
Vanaf versie 1702, vanuit het dashboard clientbeheer voor Office 365, kunt u het installatieprogramma van Office 365 waarmee u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud voor de levering van bedrijfsnetwerken (CDN) en de bestanden implementeren als een toepassing in Configuration Manager starten. Zie voor meer informatie, [Office 365 ProPlus beheren updates](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps).

> [!IMPORTANT]
> De Office 365-app die u maakt en implementeert met behulp van de Wizard toepassing van Office 365 in Configuration Manager wordt niet automatisch worden beheerd door Configuration Manager totdat u de **zodat het beheer van de Office 365-Client opnieuw** clientagent voor software-updates instellen. Zie voor meer informatie, [over clientinstellingen](/sccm/core/clients/deploy/about-client-settings).

### <a name="manage-express-installation-files-for-windows-10-updates"></a>De installatiebestanden Express voor Windows 10-updates beheren
Vanaf versie 1702 wordt ondersteunt Configuration Manager voor de bestanden voor snelle installatie voor Windows 10-updates. Wanneer u een ondersteunde versie van Windows 10 gebruikt, kunt u Configuration Manager-instellingen worden alleen de wijzigingen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update gedownload. Zonder bestanden voor snelle installatie Configuration Manager de volledige Windows 10 cumulatieve Update (met inbegrip van alle updates van vorige maanden) downloadt elke maand. Gebruik van bestanden voor snelle installatie zorgt voor downloads kleiner en sneller installatietijden op clients. Zie voor meer informatie, [bestanden voor snelle installatie voor Windows 10-updates beheren](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).


<!-- ## Reporting  -->

<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>Beheer van mobiele apparaten

### <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android en iOS-versies zijn niet langer targetable in wizards voor hybride MDM maken

Vanaf versie 1702 hybride beheer van mobiele apparaten (MDM) wordt moet niet langer u specifieke versies van Android en iOS doel bij het maken van nieuwe beleidsregels en -profielen voor Intune-beheerde apparaten. In plaats daarvan kunt u een van de volgende typen apparaten:

- Android
- Samsung KNOX Standard 4.0 of hoger
- iPhone
- iPad

Deze wijziging is van invloed op de wizards voor het maken van de volgende items:

- Configuratie-items
- Nalevingsbeleid
- Certificaatprofielen
- E-mailprofielen
- VPN-profielen
- Wi-Fi-profielen

Met deze wijziging kunnen hybride implementaties ondersteuning bieden sneller voor nieuwe Android en iOS-versies zonder een nieuwe release van Configuration Manager of een uitbreiding. Als u een nieuwe versie wordt ondersteund in zelfstandige Intune-versie, is gebruikers worden kunnen hun mobiele apparaten die versie upgraden.

Om te voorkomen dat problemen bij het upgraden van eerdere versies van Configuration Manager, mobiele besturingssysteemversies nog steeds beschikbaar zijn in de pagina Eigenschappen voor deze objecten. Als u nog steeds een specifieke versie als doel wilt, kunt u de nieuw item maken en geef vervolgens de doelversie op de eigenschappenpagina van het nieuwe item.

### <a name="android-for-work-support"></a>Android voor ondersteuning van werkitems
Beginnen met 1702, beheer van hybride mobiele apparaten met Microsoft Intune biedt nu ondersteuning voor Android voor het beheer en werk apparaatinschrijving. Beheerde Android voor werk apparaat richtlijnen:

- [Android voor werk apparaten inschrijven](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)
- [Goedkeuren en implementeren van Android voor zakelijke apps](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Configuratie-items maken voor Android voor werkitems](/sccm/mdm/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-for-work-configuration-items)
- [Selectief wissen op Android voor werk apparaten](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)
- [E-mailprofielen voor Android voor werkitems](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Nalevingsbeleid voor Android voor werkitems](/sccm/mdm/deploy-use/create-compliance-policy)


### <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Volume aangeschaft iOS-apps implementeren op apparaatverzamelingen

U kunt nu gelicentieerde apps implementeren op apparaten en gebruikers. Afhankelijk van de mogelijkheid apps voor ondersteuning van apparaat licentieverlening zal de juiste licentie worden gevraagd tijdens de implementatie, als volgt:

|||||
|-|-|-|-|
|Configuration Manager-versie|App apparaat licentieverlening ondersteunt?|Verzameling van implementatietype|Vermeende licentie|
|Ouder is dan 1702|Ja|Gebruiker|Gebruikerslicentie|
|Ouder is dan 1702|Nee|Gebruiker|Gebruikerslicentie|
|Ouder is dan 1702|Ja|Apparaat|Gebruikerslicentie|
|Ouder is dan 1702|Nee|Apparaat|Gebruikerslicentie|
|1702 en hoger|Ja|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Nee|Gebruiker|Gebruikerslicentie|
|1702 en hoger|Ja|Apparaat|Apparaatlicentie|
|1702 en hoger|Nee|Apparaat|Gebruikerslicentie|

Zie voor meer informatie over het volume aangeschaft iOS-apps [volume aangeschaft iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-ios-volume-purchase-program-for-education"></a>Ondersteuning voor iOS Volume Purchase Program voor onderwijs

U kunt nu ook implementeren en apps die u hebt aangeschaft van het bestand iOS Volume Purchase Program voor onderwijs bijhouden.
Zie voor meer informatie over het volume aangeschaft iOS-apps [volume aangeschaft iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-multiple-volume-purchase-program-tokens"></a>Ondersteuning voor meerdere volume aankoop programma tokens

U kunt meerdere Apple volume aankoop programma tokens nu koppelen met Configuration Manager.
Zie voor meer informatie over het volume aangeschaft iOS-apps [volume aangeschaft iOS-apps beheren](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-line-of-business-apps-in-windows-store-for-business"></a>Ondersteuning voor LOB-apps in Windows Store voor bedrijven

U kunt nu synchroniseren aangepaste line-of-business-apps vanuit de Windows Store voor bedrijven.

### <a name="conditional-access-device-compliance-policy-improvements"></a>Voorwaardelijke toegang apparaat naleving beleid verbeteringen

Een nieuw apparaat naleving beleidsregel is beschikbaar waarmee u toegang tot bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang wanneer gebruikers apps die deel van een niet-compatibele lijst met apps uitmaken blokkeren. De niet-compatibele lijst met apps kan worden gedefinieerd door de beheerder bij het toevoegen van de nieuwe regel compatibel **Apps die niet worden geïnstalleerd**. Met deze regel vereist dat de beheerder om in te voeren de **Appnaam**de **App-ID**, en de **App Publisher** (optioneel) bij het toevoegen van een app aan de lijst met niet-compatibel. Deze instelling geldt alleen voor iOS en Android-apparaten.

Daarnaast helpt dit organisaties gegevens lekken via niet-beveiligde apps te beperken en te voorkomen dat veel gegevens verbruik via bepaalde apps.

- Meer informatie [hoe nalevingsbeleid voor apparaten werken](/sccm/mdm/deploy-use/device-compliance-policies).
- Meer informatie [apparaat nalevingsbeleid maken](/sccm/mdm/deploy-use/create-compliance-policy).

### <a name="new-mobile-threat-defense-monitoring-tools"></a>Nieuwe mobiele bedreiging verdediging controleprogramma 's

Vanaf versie 1702, hebt u nieuwe manieren om de compatibiliteitsstatus met uw serviceprovider mobiele bedreiging verdediging te controleren.

- Meer informatie [mobiele bedreiging verdediging naleving controleren](https://docs.microsoft.com/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="protect-devices"></a>Apparaten zijn beschermd

### <a name="detect-outdated-antimalware-client-versions"></a>Verouderde antimalware-clientversies detecteren
Vanaf versie 1702, kunt u een waarschuwing om ervoor te zorgen Endpoint Protection-clients niet verouderd zijn. Zie voor meer informatie [waarschuwing voor verouderde malware client](/sccm/protect/deploy-use/endpoint-configure-alerts#detect-outdated-antimalware-client-versions).

### <a name="device-health-attestation-updates"></a>Apparaat health attestation-updates
Apparaat statusservice Attestation-bewerking voor lokale clients kunnen nu worden geconfigureerd en worden beheerd vanaf het beheerpunt. Zie voor meer informatie [Health Attestation](/sccm/core/servers/manage/health-attestation).

### <a name="certificate-profiles-for-windows-hello-for-business"></a>Certificaatprofielen voor Windows Hello voor bedrijven

Als u van plan bent voor het opslaan van certificaatprofielen in de Windows Hello voor zakelijke sleutelcontainer en het profiel voor de smartcard aanmelding EKU gebruikt, configureert u machtigingen voor de sleutel registratie zodat het certificaat correct wordt gevalideerd.
Zie voor meer informatie [Windows Hello voor instellingen voor Business](/sccm/protect/deploy-use/windows-hello-for-business-settings).

### <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nieuwe Windows Hello voor zakelijke kennisgeving voor eindgebruikers
Een nieuwe Windows 10-melding informeert gebruikers dat ze extra acties voltooid Windows Hello voor de installatie van Business (bijvoorbeeld, het instellen van een PINCODE) moeten uitvoeren.

