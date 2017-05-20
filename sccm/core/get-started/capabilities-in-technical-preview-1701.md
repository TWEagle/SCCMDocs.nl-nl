---
title: Mogelijkheden in Technical Preview 1701 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1701.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18598eaa-1131-44ff-8f8b-6093e87ac7a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: b330c97a0853d1673f1cf7e0691891b72407fa51
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1701-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1701 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1701 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="boundary-groups-improvements-for-software-update-points"></a>Grens groepen verbeteringen voor software-updatepunten
Vanaf dit voorbeeld wordt nu u grensgroepen clients koppelen aan software-updatepunten. Dit maakt deel uit van het proces wordt voortgezet werk de wijzigingen voor grensgroepen voor het beheren van extra sitesysteemrollen uitbreiden.  Wijzigingen voor grensgroepen werden geïntroduceerd in technische Preview 1609 en de huidige vertakking in 1610 versie.  

Met deze preview kunt u de nieuwe grens groep gedrag voor het beheren van welke software-updatepunten een client gebruiken kan, vergelijkbaar met hoe u welke distributiepunt beheert een client kan gebruiken:  

- Configureren van grensgroepen om te koppelen van een of meer servers die als host optreden van een software-updatepunt.
- Clients die een nieuwe software-updatepunt zoekt probeert te gebruiken dat is gekoppeld aan hun huidige grensgroep.
- Als de client niet kan bereiken hun huidige software-updatepunt en kan een van hun huidige grensgroep niet vinden, gebruikt de client Fallback gedrag uitbreiden van de beschikbare groep met software-updatepunten die kunnen worden gebruikt.    

Zie voor meer informatie over grensgroepen [grensgroepen](/sccm/core/servers/deploy/configure/boundary-groups) in de inhoud voor de huidige vertakking.

Met deze preview zijn grensgroepen voor software-updatepunten echter slechts gedeeltelijk geïmplementeerd. Kunt u software-updatepunten toevoegen en configureren van grensgroepen neighbor met software-updatepunten, maar de alternatieve tijd voor software-updatepunten wordt nog niet ondersteund en clients worden twee uur wachten voordat vanaf fallback.

De volgende tabel ziet het gedrag voor het software-updatepunten van deze technische preview:  

-    **Nieuwe clients gebruik grensgroepen om te selecteren van software-updatepunten** een client installeren nadat u versie 1701 selecteert een software-updatepunt degene die zijn gekoppeld aan de grensgroep van de client installeren.

  Dit vervangt het gedrag van het vorige waar clients selecteren op een software-updatepunt willekeurig uit een lijst met computers die het forest clients delen.   

-    **Eerder blijven geïnstalleerde clients met hun huidige software-updatepunt pas nadat deze alternatieve zoeken naar een nieuwe.**
Clients die eerder zijn geïnstalleerd en die al een software-updatepunt blijft dat software-updatepunt gebruiken tot deze alternatieve. Dit omvat software-updatepunten die niet gekoppeld aan de huidige grensgroep van de client zijn. Ze Probeer niet onmiddellijk te zoeken en gebruiken van een software-updatepunt van hun huidige grensgroep.

  Een client die al heeft een software-updatepunt begint met het gebruik van het gedrag van deze nieuwe grens groep nadat de client niet kunnen bereiken van de huidige software-updatepunt en begint met het alternatieve.
Deze vertraging van via overschakelen naar het nieuwe gedrag is opzettelijk. Dit komt doordat een wijziging van de software-updatepunt tot een grote gebruik van netwerkbandbreedte leiden kan als de client worden gegevens gesynchroniseerd met de nieuwe software-updatepunt. De vertraging in de overgangsfase kan helpen voorkomen overbelasting van uw netwerk moet al uw clients naar de nieuwe software overschakelen-updatepunten op hetzelfde moment.

-    **Configuraties voor alternatieve tijd:** Configuraties voor wanneer clients eerst fallback om te zoeken naar een nieuw software-updatepunt worden niet ondersteund in deze technische preview. Dit omvat configuraties voor **terugval time-out (in minuten)** en **nooit fallback**, dat u voor verschillende grens groepsrelaties configureert.

  In plaats daarvan behouden clients hun huidige gedrag waar een client probeert verbinding maken met de huidige software-updatepunt voor twee uur voordat er begonnen alternatief wordt vinden van een nieuwe software-updatepunt die kan gebruiken.

  Wanneer een client wordt gebruikt voor terugval, worden de configuraties van de groep grens voor terugval gebruikt voor het maken van een groep met beschikbare software-updatepunten. Deze groep bevat alle software-updatepunten van clients *huidige grensgroep*, *neighbor-grensgroepen*, en de clients *sitegrensgroep standaard*.

- **Configureer de standaardgroep voor de grens van site:**  
 Overweeg een software-updatepunt voor de *standaard---Sitegrensgroep&lt;sitecode >*. Dit zorgt ervoor dat clients die zich niet kunnen leden van een andere grensgroep terugval Ga voor een software-updatepunt.


Gebruiken voor het beheren van software-updatepunten voor grensgroepen de [procedures van de huidige vertakking documentatie](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#procedures-for-boundary-groups), maar houd er rekening mee dat fallback tijden die u configureert niet nog worden gebruikt voor software-updatepunten.


## <a name="hardware-inventory-collects-uefi-information"></a>Hardware-inventaris verzamelt informatie UEFI
Een nieuwe hardware-inventarisklasse (**SMS_Firmware**) en de eigenschap (**UEFI**) zijn beschikbaar om te bepalen of een computer in UEFI-modus start. Wanneer een computer in UEFI-modus wordt gestart de **UEFI** eigenschap is ingesteld op **waar**. Dit is standaard ingeschakeld in de hardware-inventaris. Zie voor meer informatie over hardware-inventaris [het configureren van hardware-inventaris](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="improvements-to-operating-system-deployment"></a>Verbeteringen in de implementatie van besturingssysteem
We hebben de volgende verbeteringen voor de implementatie van besturingssystemen, die het resultaat van uw stem feedback van gebruikers zijn aangebracht.
- [**Ondersteuning voor meer toepassingen voor de toepassingen installeren takenreeksstap**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17062207-task-sequence-allow-more-than-9-applications-in-t): Het maximum aantal toepassingen die u kunt installeren en 99 in grotere de **toepassingen installeren** takenreeksstap. Het vorige maximum aantal is 9-Apps.
- [**Selecteer een meerdere apps in de takenreeksstap toepassing installeren**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15459978-when-adding-items-to-an-install-application-step): Wanneer u toepassingen aan de takenreeks toepassing installeren in de takenreekseditor stap toevoegt, kunt u nu meerdere toepassingen selecteren de **Selecteer de te installeren toepassing** deelvenster.
- [**Zelfstandige media verlopen**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/14448564-provide-a-method-for-expiring-standalone-media): Wanneer u een zelfstandige media maakt, zijn er nieuwe opties voor het optionele begin- en verloopdatum datums instellen voor de media. Deze instellingen zijn standaard uitgeschakeld. De datums worden vergeleken met de systeemtijd op de computer voordat de zelfstandige media wordt uitgevoerd. Wanneer de systeemtijd ouder is dan de begintijd of hoger is dan de verlooptijd is, wordt de zelfstandige media niet gestart. Deze opties zijn ook beschikbaar via de cmdlet New-CMStandaloneMedia PowerShell.
- [**Ondersteuning voor aanvullende inhoud in zelfstandige media**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8341257-support-installation-of-packages-apps-via-dynamic): Aanvullende inhoud wordt nu ondersteund in zelfstandige media. U kunt extra pakketten en stuurprogrammapakketten toepassingen moeten worden geïnstalleerd op de media samen met de andere inhoud waarnaar wordt verwezen in de takenreeks selecteren. Alleen de inhoud waarnaar wordt verwezen in de takenreeks is eerder voorbereid op zelfstandige media.
- [**Configureerbare time-out voor automatische toepassing stuurprogramma takenreeksstap**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17153660-auto-apply-driver-timeout): Nieuwe takenreeksvariabelen zijn nu beschikbaar voor de time-outwaarde configureren op de takenreeksstap voor het automatisch toepassen stuurprogramma bij het maken van HTTP-aanvragen van catalogus. De volgende variabelen en standaardwaarden (in seconden) zijn beschikbaar:
   - Standaard SMSTSDriverRequestResolveTimeOut: 60
   - Standaard SMSTSDriverRequestConnectTimeOut: 60
   - Standaard SMSTSDriverRequestSendTimeOut: 60
   - Standaard SMSTSDriverRequestReceiveTimeOut: 480
- [**Pakket-ID wordt nu weergegeven in takenreeksstappen**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16167430-display-packageid-when-viewing-a-task-sequence-ste): Elke stap van de takenreeks die verwijst naar een pakket, stuurprogrammapakket, de installatiekopie van het besturingssysteem, opstartinstallatiekopie of upgradepakket besturingssysteem wordt nu weergegeven met de pakket-ID van het object waarnaar wordt verwezen. Wanneer een takenreeksstap verwijst naar een toepassing wordt weergegeven de object-ID.
- **Windows 10 ADK bijgehouden door de buildversie**: De Windows-ADK 10 wordt nu bijgehouden door buildversie zodat een meer ondersteunde ervaring wanneer Windows 10-opstartinstallatiekopieën aanpassen. Bijvoorbeeld, als de site de Windows ADK voor Windows 10 versie 1607 gebruikt, worden opstartinstallatiekopieën met versie 10.0.14393 aangepast in de console. Zie voor meer informatie over het aanpassen van de WinPE-versies [opstartinstallatiekopieën aanpassen](/sccm/osd/get-started/customize-boot-images).
- **Standaard opstart bronpad kan niet meer worden gewijzigd**: Standaardopstartinstallatiekopieën worden beheerd door Configuration Manager en het bronpad standaard opstart-installatiekopie kan niet meer worden gewijzigd in de Configuration Manager-console of met behulp van de Configuration Manager-SDK. U kunt een aangepaste bronpad voor aangepaste opstartinstallatiekopieën configureren blijven.

## <a name="host-software-updates-on-cloud-based-distribution-points"></a>Host-software-updates op cloud-gebaseerde distributiepunten
Beginnend met deze preview-versie, kunt u een cloud-gebaseerde distributiepunt gebruiken voor het hosten van een software-updatepakket. Echter, omdat u kunt clients downloaden van software-updates rechtstreeks vanaf Microsoft Update, kunt u de extra kosten die implementatie van een software update pakket naar een cloud-gebaseerde distributiepunt kunt in rekening worden gebracht.

Zie voor meer informatie over het gebruik van cloud-gebaseerde distributiepunten [een cloud-gebaseerde distributiepunt gebruiken](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) in de inhoud voor de huidige vertakking van Configuration Manager.

## <a name="validate-device-health-attestation-data-via-management-points"></a>Status attestation apparaatgegevens via beheerpunten valideren

Vanaf deze preview-versie, kunt u beheerpunten voor het valideren van health-verklaring rapportagegegevens voor cloud of on-premises attestation statusservice. Een nieuwe **geavanceerde opties** tabblad de **Onderdelenkenmerken** in het dialoogvenster kunt u **toevoegen**, **bewerken**, of **verwijderen** de **On-premises apparaat health attestation-service-URL**. U kunt ook opgeven **aangepaste apparaatinstellingen** voor de clientagent voor **Gebruik lokale statusservice Attestation**.  Instelling **Ja** voor deze instelling worden ingeschakeld met de on-premises reporting beheerpunt in plaats van de cloudservice.

### <a name="try-it-out"></a>Probeer het nu

- **Schakel op het lokale apparaat health attestation op een beheerpunt**<br>  In de Configuration Manager-console navigeert u naar het beheerpunt en open **onderdeel Beheerpunteigenschappen** en klik vervolgens op de **geavanceerde opties** tabblad. Klik op **toevoegen** en geeft u de lokale URL (bijvoorbeeld https://10.10.10.10) voor **On-premises apparaat health attestation-URL's**.
- **Lokale management-punt health attestation rapportage voor de clientagent inschakelen**<br>Kies in de Configuration Manager-console **beheer** > **clientinstellingen** en dubbelklikt u op of maak een nieuwe **aangepaste apparaatinstellingen**. Selecteer **Computeragent** en stel **Gebruik lokale statusservice Attestation** naar **Ja**. Als **communicatie met de apparaat-statusservice Attestation** is ingesteld op **Ja** en **Gebruik lokale Health-verklaring** is ingesteld op **Nee**, het beheerpunt de cloudgebaseerd Apparaatbeheer health attestation-service wordt gebruikt.

## <a name="use-the-oms-connector-for-microsoft-azure-government-cloud"></a>De OMS-serverconnector gebruiken voor de overheid van de Microsoft Azure-cloud
U kunt nu de Microsoft Operations Management Suite Kantoorbeheersysteem connector verbinding maken met een OMS werkruimte die zich op de overheid van de Microsoft Azure cloud van deze technische preview gebruiken.  

Een configuratiebestand om te verwijzen naar de cloud overheid hebt gewijzigd om dit te doen, en installeer vervolgens de OMS-connector.

### <a name="set-up-an-oms-connector-to-microsoft-azure-government-cloud"></a>Instellen van een connector OMS met overheid van de Microsoft Azure-cloud
1.  Op een computer waarop de Configuration Manager-console is geïnstalleerd, moet u het volgende configuratiebestand verwijzen naar de overheid van de cloud bewerken:  ***&lt;CM-installatiepad > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Bewerkingen:**

    Wijzig de waarde voor de naam van de instelling *FairFaxArmResourceID* gelijk aan "https://management.usgovcloudapi.net/"

   - **Oorspronkelijke:** 
      &lt;Instellingsnaam = "FairFaxArmResourceId" serializeAs = "Tekenreeks" >   
      &lt;waarde > &lt; /value >   
      &lt;/ instelling >

   - **Bewerkt:**     
      &lt;naam van de instelling = "FairFaxArmResourceId" serializeAs = "Tekenreeks" > &lt;waarde > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ instelling >

  Wijzig de waarde voor de naam van de instelling *FairFaxAuthorityResource* gelijk aan "https://login.microsoftonline.com/"

  - **Oorspronkelijke:** &lt;Instellingsnaam = "FairFaxAuthorityResource" serializeAs = "Tekenreeks" >   
    &lt;waarde > &lt; /value >

    - **Bewerkt:** &lt;Instellingsnaam = "FairFaxAuthorityResource" serializeAs = "Tekenreeks" >   
    &lt;waarde > https://login.microsoftonline.com/ &lt; /value >

2.    Nadat u het bestand met de twee wijzigingen opslaat, opnieuw opstarten van de Configuration Manager-console op dezelfde computer en vervolgens om deze console gebruiken om de OMS-connector te installeren. Gebruik de informatie in voor het installeren van de connector [synchroniseren van gegevens uit Configuration Manager naar de Microsoft Operations Management-pakket](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), en selecteer de **Operations Management Suite werkruimte** dat zich op de overheid van de Microsoft Azure-cloud.

3.    Nadat de OMS-connector is geïnstalleerd, is de verbinding met de overheid van de cloud beschikbaar wanneer u een console die verbinding met de site maakt.

## <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android en iOS-versies zijn niet langer targetable in wizards voor hybride MDM maken

Vanaf deze technische preview hybride beheer van mobiele apparaten (MDM) wordt moet niet langer u specifieke versies van Android en iOS doel bij het maken van nieuwe beleidsregels en -profielen voor Intune-beheerde apparaten. In plaats daarvan kunt u een van de volgende typen apparaten:

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

