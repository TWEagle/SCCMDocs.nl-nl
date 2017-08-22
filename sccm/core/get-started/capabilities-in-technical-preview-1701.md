---
title: Mogelijkheden in Technical Preview 1701 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1701.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18598eaa-1131-44ff-8f8b-6093e87ac7a1
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b330c97a0853d1673f1cf7e0691891b72407fa51
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1701-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1701 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1701 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="boundary-groups-improvements-for-software-update-points"></a>Grens groepen verbeteringen voor software-updatepunten
Vanaf deze preview kunt u nu grensgroepen koppelen van clients met software-updatepunten gebruiken. Dit is onderdeel van de bewerking wordt voortgezet werk uit te breiden, de wijzigingen voor grensgroepen voor het beheren van extra sitesysteemrollen.  Wijzigingen voor grensgroepen is geïntroduceerd in Technical Preview 1609 en de huidige vertakking in versie 1610.  

Met deze preview kunt u de nieuwe grens groep gedrag voor het beheren van welke software-updatepunten een client gebruiken kan, vergelijkbaar met hoe u welke distributiepunt beheert een client kan gebruiken:  

- Configureren van grensgroepen voor het koppelen van een of meer servers die als host fungeren van een software-updatepunt.
- Clients die op zoek zijn nieuwe software-updatepunt zal proberen te gebruiken die is gekoppeld aan hun huidige grensgroep.
- Wanneer de client niet kan bereiken hun huidige software-updatepunt en een van hun huidige grensgroep niet kunt vinden, gebruikt de client terugval gedrag uit te breiden, de beschikbare groep met software-updatepunten die kunnen worden gebruikt.    

Zie voor meer informatie over grensgroepen [grensgroepen](/sccm/core/servers/deploy/configure/boundary-groups) in de inhoud voor de huidige vertakking.

Met deze preview zijn grensgroepen voor software-updatepunten echter slechts gedeeltelijk geïmplementeerd. U kunt software-updatepunten toevoegen en configureren van grensgroepen neighbor met software-updatepunten maar de terugval tijd voor software-updatepunten wordt nog niet ondersteund en clients twee uur moeten wachten voordat terugval wordt gestart.

De volgende tabel ziet het gedrag voor software-updatepunten met deze technical preview:  

-   **Nieuwe clients gebruiken grensgroepen om te selecteren van software-updatepunten** een client installeren nadat u versie 1701 selecteert een software-updatepunt uit die zijn verbonden met de grensgroep van de client installeren.

  Dit vervangt de vorige gedrag waar clients selecteren een software-updatepunt willekeurig uit een lijst met toepassingen die delen van het forest van de clients.   

-   **Eerder blijven geïnstalleerde clients gebruiken hun huidige software-updatepunt tot ze terugval naar een nieuwe vinden.**
Clients die eerder zijn geïnstalleerd en waarvoor al een software-updatepunt blijven gebruiken die software-updatepunt tot ze terugval. Dit omvat software-updatepunten die niet gekoppeld aan de huidige grensgroep van de client zijn. Ze probeer onmiddellijk niet om te zoeken en software-updatepunt uit hun huidige grensgroep.

  Een client die een software-updatepunt is al begint met het gedrag van deze nieuwe grens groep alleen gebruiken nadat de client niet kunnen bereiken van de huidige software-updatepunt en begint met het fallback.
Deze vertraging van via overschakelen naar het nieuwe gedrag is opzettelijk. Dit is omdat een wijziging van de software-updatepunt tot een grote gebruik van netwerkbandbreedte leiden kan als de client worden gegevens gesynchroniseerd met het nieuwe software-updatepunt. De vertraging in de overgangsfase kunt u voorkomen dat het netwerk overbelast raakt moet alle uw clients naar de nieuwe software overschakelen-updatepunten op hetzelfde moment.

-   **Configuraties voor terugval tijd:** Configuraties voor wanneer clients eerst terugval om te zoeken naar een nieuw software-updatepunt worden niet ondersteund in deze technical preview. Dit omvat configuraties voor **terugval time-out (in minuten)** en **nooit terugval**, dat u voor relaties tussen verschillende grens configureert.

  In plaats daarvan behouden clients hun huidige gedrag waar een client probeert verbinding maken met de huidige software-updatepunt voor twee uur voordat er begonnen terugval wordt vinden van een nieuw software-updatepunt die kan gebruiken.

  Wanneer een client wordt gebruikt voor terugval, wordt de configuratie van grensgroepen voor terugval gebruikt om een groep met beschikbare software-updatepunten te maken. Deze groep bevat alle software-updatepunten van de clients *huidige grensgroep*, *neighbor grensgroepen*, en de clients *sitegrensgroep standaard*.

- **Configureer de standaardgroep voor de grens van site:**  
 Overweeg een software-updatepunt voor de *-Site-grens-standaardgroep&lt;sitecode >*. Dit zorgt ervoor dat clients die niet kunnen leden van een andere grensgroep terugval Ga voor een software-updatepunt.


Voor het beheren van software-updatepunten voor grensgroepen, gebruiken de [procedures in de documentatie van de huidige vertakking](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#procedures-for-boundary-groups), maar houd er rekening mee dat terugval tijden die u configureert nog niet voor software-updatepunten gebruikt zijn.


## <a name="hardware-inventory-collects-uefi-information"></a>Hardware-inventaris verzamelt UEFI-informatie
Een nieuwe hardware-inventarisklasse (**SMS_Firmware**) en de eigenschap (**UEFI**) zijn beschikbaar om te bepalen of een computer in UEFI-modus wordt gestart. Wanneer een computer in UEFI-modus is gestart de **UEFI** eigenschap is ingesteld op **TRUE**. Dit is standaard ingeschakeld in de hardware-inventaris. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="improvements-to-operating-system-deployment"></a>Verbeteringen in de implementatie van besturingssysteem
We hebben de volgende verbeteringen voor de implementatie van besturingssystemen, die het resultaat van uw stem feedback van gebruikers zijn aangebracht.
- [**Ondersteuning voor meer toepassingen voor de toepassingen installeren takenreeksstap**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17062207-task-sequence-allow-more-than-9-applications-in-t): Het maximum aantal toepassingen die u kunt installeren en 99 in grotere de **toepassingen installeren** takenreeksstap. Het vorige maximum aantal is 9 toepassingen.
- [**Meerdere apps selecteren in de App installeren takenreeksstap**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15459978-when-adding-items-to-an-install-application-step): Wanneer u toepassingen aan de takenreeks toepassing installeren-stap in de takenreekseditor toevoegt, kunt u nu meerdere toepassingen selecteren het **Selecteer de te installeren toepassing** deelvenster.
- [**Verlopen van zelfstandige media**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/14448564-provide-a-method-for-expiring-standalone-media): Wanneer u zelfstandige media maakt, zijn er nieuwe opties optionele begin- en verloopdatum datums instellen op de media. Deze instellingen zijn standaard uitgeschakeld. De datums worden vergeleken met de systeemtijd op de computer voordat de zelfstandige media wordt uitgevoerd. Wanneer de systeemtijd ouder dan de begintijd of hoger is dan de verlooptijd is, worden de zelfstandige media is niet gestart. Deze opties zijn ook beschikbaar via de cmdlet New-CMStandaloneMedia PowerShell.
- [**Ondersteuning voor aanvullende inhoud in de zelfstandige media**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8341257-support-installation-of-packages-apps-via-dynamic): Aanvullende inhoud wordt nu ondersteund in zelfstandige media. U kunt extra pakketten, stuurprogrammapakketten en toepassingen moeten worden geïnstalleerd op de media en de andere inhoud waarnaar wordt verwezen in de takenreeks selecteren. Voorheen is alleen inhoud waarnaar wordt verwezen in de takenreeks voorbereid op zelfstandige media.
- [**Configureerbare time-out voor het automatisch toepassen van stuurprogramma takenreeksstap**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17153660-auto-apply-driver-timeout): Nieuwe takenreeksvariabelen zijn nu beschikbaar voor het configureren van de time-outwaarde op de takenreeksstap voor het automatisch toepassen van stuurprogramma bij het maken van HTTP-aanvragen voor catalogus. De volgende variabelen en de standaardwaarden (in seconden) zijn beschikbaar:
   - Standaard SMSTSDriverRequestResolveTimeOut: 60
   - Standaard SMSTSDriverRequestConnectTimeOut: 60
   - Standaard SMSTSDriverRequestSendTimeOut: 60
   - Standaard SMSTSDriverRequestReceiveTimeOut: 480
- [**Pakket-ID wordt nu weergegeven in de takenreeksstappen**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16167430-display-packageid-when-viewing-a-task-sequence-ste): Elke takenreeks die verwijst naar een pakket, stuurprogrammapakket, besturingssysteemkopie, opstartinstallatiekopie of upgradepakket voor besturingssysteem wordt nu weergegeven voor de pakket-ID van het object waarnaar wordt verwezen. Als een takenreeksstap verwijst naar een toepassing wordt weergegeven de object-ID.
- **Windows 10 ADK bijgehouden door buildversie**: Windows 10 ADK wordt nu bijgehouden door het build-versie om te controleren of een meer ondersteunde ervaring bij het Windows 10-opstartinstallatiekopieën aanpassen. Als de site de Windows ADK voor Windows 10 versie 1607 gebruikt, kunnen er bijvoorbeeld opstartinstallatiekopieën met versie 10.0.14393 worden aangepast in de console. Zie voor meer informatie over het aanpassen van WinPE-versies [opstartinstallatiekopieën aanpassen](/sccm/osd/get-started/customize-boot-images).
- **Bronpad opstartimage standaard kan niet meer worden gewijzigd**: Standaardopstartinstallatiekopieën worden beheerd door Configuration Manager en het bronpad standaard opstartimage kan niet meer worden gewijzigd in de Configuration Manager-console of met behulp van de Configuration Manager-SDK. U kunt blijven voor het configureren van een aangepaste bronpad voor aangepaste opstartinstallatiekopieën.

## <a name="host-software-updates-on-cloud-based-distribution-points"></a>Host software-updates op cloud-gebaseerde distributiepunten
Vanaf deze preview-versie, kunt u een cloud-gebaseerde distributiepunt voor het hosten van een software-updatepakket. Echter, omdat u clients voor het downloaden van software-updates rechtstreeks vanaf Microsoft Update configureren kunt, houd rekening met de extra kosten die een software implementeert pakket naar een cloud-gebaseerde distributiepunt bijwerken kunnen tot.

Zie voor meer informatie over het gebruik van cloud-gebaseerde distributiepunten [een cloud-gebaseerd distributiepunt gebruiken](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) in de inhoud voor de huidige vertakking van Configuration Manager.

## <a name="validate-device-health-attestation-data-via-management-points"></a>Apparaat health attestation-gegevens via beheerpunten valideren

U kunt beheerpunten voor het valideren van de health attestation-gegevens voor de cloud of on-premises health attestation-service reporting vanaf deze preview-versie kunt configureren. Een nieuwe **geavanceerde opties** tabblad de **eigenschappen van Beheerpuntonderdeel** in het dialoogvenster kunt u **toevoegen**, **bewerken**, of **verwijderen** de **On-premises apparaat health attestation-service-URL**. U kunt ook opgeven **aangepaste Clientapparaatinstellingen** voor de clientagent **on-premises gebruiken Health Attestation-Service**.  Instelling **Ja** voor deze instelling schakelt rapporteren aan de on-premises beheerpunt in plaats van de cloudservice.

### <a name="try-it-out"></a>Try it out in

- **Health attestation van lokale apparaten op een beheerpunt inschakelen**<br>  In de Configuration Manager-console gaat u naar het beheerpunt en open **onderdeel Beheerpunteigenschappen** en klik vervolgens op de **geavanceerde opties** tabblad. Klik op **toevoegen** en geef de lokale-URL (bijvoorbeeld https://10.10.10.10) voor **On-premises-URL's van apparaat health attestation service**.
- **Lokale management punt statusverklaringen rapportage voor de clientagent inschakelen**<br>Kies in de Configuration Manager-console **beheer** > **clientinstellingen** en dubbelklikt u op of maak een nieuw **aangepaste Clientapparaatinstellingen**. Selecteer **Computeragent** en stel **on-premises gebruiken Health Attestation-Service** naar **Ja**. Als **communicatie met Health Attestation-Service apparaat inschakelen** is ingesteld op **Ja** en **on-premises gebruiken Health Attestation** is ingesteld op **Nee**, het beheerpunt de cloudgebaseerd Apparaatbeheer health attestation-service wordt gebruikt.

## <a name="use-the-oms-connector-for-microsoft-azure-government-cloud"></a>Gebruik de OMS-connector voor Microsoft Azure Government cloud
Met deze technical preview kunt u nu de Microsoft Operations Management Suite (OMS)-connector gebruiken om te verbinden met een OMS-werkruimte die zich op Microsoft Azure Government cloud.  

Een configuratiebestand om te verwijzen naar de cloud van de overheid wijzigen om dit te doen en installeer vervolgens de OMS-connector.

### <a name="set-up-an-oms-connector-to-microsoft-azure-government-cloud"></a>Een OMS-connector voor Microsoft Azure Government cloud instellen
1.  Op elke computer die de Configuration Manager-console die is geïnstalleerd, het volgende configuratiebestand om te verwijzen naar de cloud van de overheid te bewerken:  ***&lt;CM-installatiepad > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Bewerkingen:**

    Wijzig de waarde voor de naam van de instelling *FairFaxArmResourceID* moet gelijk zijn aan 'https://management.usgovcloudapi.net/'

   - **Oorspronkelijke:** &lt;Instellingsnaam = serializeAs 'FairFaxArmResourceId' = 'Tekenreeks' >   
      &lt;waarde > &lt; /value >   
      &lt;/ instelling >

   - **Bewerkt:**     
      &lt;naam van de instelling serializeAs 'FairFaxArmResourceId' = 'Tekenreeks' = > &lt;waarde > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ instelling >

  Wijzig de waarde voor de naam van de instelling *FairFaxAuthorityResource* moet gelijk zijn aan 'https://login.microsoftonline.com/'

  - **Oorspronkelijke:** &lt;Instellingsnaam = serializeAs 'FairFaxAuthorityResource' = 'Tekenreeks' >   
    &lt;waarde > &lt; /value >

    - **Bewerkt:** &lt;Instellingsnaam = serializeAs 'FairFaxAuthorityResource' = 'Tekenreeks' >   
    &lt;waarde > https://login.microsoftonline.com/ &lt; /value >

2.  Nadat u het bestand met de twee wijzigingen hebt opgeslagen, wordt de Configuration Manager-console op dezelfde computer opnieuw opstarten en vervolgens die console gebruiken om de OMS-connector te installeren. Gebruik de informatie in om de connector installeert, [synchroniseren van gegevens uit Configuration Manager met de Microsoft Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), en selecteer de **Operations Management Suite-werkruimte** dat zich op de Microsoft Azure Government cloud.

3.  Nadat de OMS-connector is geïnstalleerd, is de verbinding met de cloud van de overheid beschikbaar wanneer u een console die verbinding met de site maakt.

## <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android en iOS-versies worden niet meer targetable in wizards voor hybride MDM maken

Vanaf deze technical preview voor hybride mobile device management (MDM) is hoeft niet langer te gericht op specifieke versies van Android en iOS bij het maken van nieuwe beleidsregels en profielen voor Intune-beheerde apparaten. In plaats daarvan, kies een van de volgende typen apparaten:

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
