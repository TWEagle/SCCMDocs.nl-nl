---

title: Instellingen beheren voor software-updates | Microsoft-documenten
description: Meer informatie over de clientinstellingen die geschikt voor software-updates op uw site zijn nadat u de software-updatepunt installeert.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/26/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 0d484c1a-e903-4bff-9e9b-e452c62e38a8
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: fe4a8f56e0b554e206bcc4503a0268dc761ded81
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

#  <a name="BKMK_ManageSUSettings"></a>Instellingen voor software-updates beheren  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Na het synchroniseren van software-updates in Configuration Manager configureren en controleer de instellingen in de volgende secties.

##  <a name="BKMK_ClientSettings"></a> Clientinstellingen voor software-updates  
Wanneer u het software-updatepunt installeert, worden standaard software-updates ingeschakeld op clients en hebben de instellingen op de pagina **Software-updates** in de clientinstellingen de standaardwaarden. Instellingen voor de client worden gehele site gebruikt en zijn van invloed als het software-updates worden gescand voor compatibiliteit en hoe en wanneer software-updates zijn geïnstalleerd op clientcomputers. Voordat u software-updates implementeert, controleert u of de clientinstellingen voor software-updates op uw site.  

> [!IMPORTANT]  
>  De instelling **Software-updates op clients inschakelen** wordt standaard ingeschakeld. Als u deze instelling wist, verwijdert Configuration Manager de bestaande implementatiebeleiden van de client.  

Zie voor meer informatie over het configureren van clientinstellingen [het configureren van clientinstellingen](../../core/clients/deploy/configure-client-settings.md).  

Zie voor meer informatie over de clientinstellingen [over clientinstellingen](../../core/clients/deploy/about-client-settings.md).  

##  <a name="BKMK_GroupPolicy"></a> Groepsbeleidinstellingen voor software-updates  
Er zijn specifieke door Windows Update Agent (WUA) gebruikte groepsbeleidinstellingen op clientcomputers om verbinding te maken met WSUS die op het software-updatespunt wordt gebruikt. U kunt met deze groepsbeleidinstellingen ook de naleving van software-updates scannen en automatisch de software-updates en WUA bijwerken.

### <a name="specify-intranet-microsoft-update-service-location-local-policy"></a>Lokaal beleid voor Locatie van Microsoft-updateservice in intranet  
Wanneer er een software-updatepunt voor een site is gemaakt, ontvangen clients een machinebeleid dat de servernaam van het software-updatepunt verstrekt en het lokale beleid **Locatie van Microsoft-updateservice in intranet opgeven** op de computer configureert. De WUA haalt de in de instelling **De updateservice in intranet instellen voor het detecteren van updates** opgegeven servernaam op, waarna deze verbinding maakt met deze server wanneer de scan voor compatibiliteit van software-updates wordt uitgevoerd. Wanneer het domeinbeleid voor de instelling **Locatie van Microsoft-updateservice in intranet** wordt gemaakt, wordt het lokale beleid overschreven en maakt de WUA mogelijk verbinding met een andere server dan die van het software-updatepunt. Wanneer dit gebeurt, scant de client mogelijk voor compatibiliteit van software-updates op basis van andere producten, classificaties en talen. Daarom dient u het Active Directory-beleid voor clientcomputers niet te configureren.  

### <a name="allow-signed-content-from-intranet-microsoft-update-service-location-group-policy"></a>Ondertekende inhoud vanaf de locatie van de Microsoft-updateservice op een intranet toestaan  
U moet de groepsbeleidinstelling **Ondertekende inhoud toestaan van groepsbeleid voor locatie van Microsoft-updateservice in intranet** inschakelen voordat de WUA computers gaat scannen op software-updates die door System Center Updates Publisher zijn gemaakt en gepubliceerd. Wanneer de beleidinstelling is ingeschakeld, accepteert WUA via een intranetlocatie ontvangen software-updates, als de software-updates zijn ondertekend in het certificaatarchief **Vertrouwde uitgevers** op de lokale computer. Zie de [documentatiebibliotheek van Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=232476)voor meer informatie over de voor Updates Publisher 2011 vereiste groepsbeleidinstellingen.  

### <a name="automatic-updates-configuration"></a>Automatische updates configureren  
Met automatische updates kunt u beveiligingsupdates en andere belangrijke downloads ontvangen op clientcomputers. Automatische updates wordt geconfigureerd via de groepsbeleidinstelling **Automatische updates configureren** of via het configuratiescherm op de lokale computer. Wanneer Automatische updates is ingeschakeld, ontvangen clientcomputers updatemeldingen en downloaden en installeren de clientcomputers de vereiste updates, afhankelijk van de geconfigureerde instellingen, Wanneer Automatische updates tegelijk met software-updates wordt gebruikt, geeft elke clientcomputer mogelijk meldingspictogrammen en pop-upweergavemeldingen weer voor dezelfde update. Wanneer opnieuw opstarten is vereist, geeft elke clientcomputer mogelijk een dialoogvenster voor opnieuw opstarten weer voor dezelfde update.  

### <a name="self-update"></a>Automatische update  
Wanneer automatische updates is ingeschakeld op clientcomputers, voert de WUA een automatische update uit wanneer een nieuwere versie beschikbaar komt of wanneer er problemen zijn met een WUA-component. Wanneer Automatische updates niet is geconfigureerd of is uitgeschakeld en clientcomputers een eerdere versie van de WUA hebben, moeten de clientcomputers het WUA-installatiebestand uitvoeren.  

## <a name="software-updates-properties"></a>Eigenschappen van software-updates
De eigenschappen van software-updates bieden informatie over software-updates en gekoppelde inhoud. U kunt deze eigenschappen ook gebruiken om instellingen voor software-updates te configureren. Wanneer u de eigenschappen voor meerdere software-updates opent, worden alleen de tabbladen **Maximale uitvoeringstijd** en **Aangepaste ernst** weergegeven.   

Gebruik de volgende procedure om eigenschappen van software-updates te openen.  

#### <a name="to-open-software-update-properties"></a>Eigenschappen van software-updates openen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  
2.  Vouw in de werkruimte Softwarebibliotheek het knooppunt **Software-updates**uit en klik op **Alle software-updates**.  
3.  Selecteer een of meer software-updates en klik vervolgens op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen** .  

   > [!NOTE]  
   >  Op de **alle Software-Updates** knooppunt Configuration Manager wordt de software-updates met een **kritieke** en **beveiliging** classificatie en die in de afgelopen 30 dagen zijn vrijgegeven.  

###  <a name="BKMK_SoftwareUpdatesInformation"></a> Informatie over software-updates weergeven  
U kunt in de eigenschappen van software-updates gedetailleerde informatie over een software-update controleren. De gedetailleerde informatie wordt niet weergegeven wanneer u meer dan één software-update selecteert. In de volgende secties is de informatie beschreven die beschikbaar is voor de geselecteerde software-update.  

####  <a name="BKMK_SoftwareUpdateDetails"></a> Details over software-updates  
Op het tabblad met **updatedetails** wordt de volgende overzichtsinformatie over de geselecteerde software-update weergegeven:  

- **Bulletin-ID**: Hiermee geeft u de bulletin-ID die aan beveiligingsupdates is gekoppeld. U kunt gegevens over het beveiligingsbulletin vinden door op de bulletin-id te zoeken op de webpagina [Microsoft Security Bulletin](http://go.microsoft.com/fwlink/p/?LinkId=58313) (Microsoft-beveiligingsbulletin).  

- **Artikel-ID**: Hiermee geeft u de artikel-ID voor de software-update. Het artikel waarnaar wordt verwezen biedt gedetailleerde informatie over de software-update en het probleem dat de software-update corrigeert of verbetert.  

- **Revisiedatum**: Hiermee geeft u de datum waarop de software-update voor het laatst is gewijzigd.  

- **Maximale ernstclassificatie**: Hiermee geeft u de leverancier gedefinieerde ernstbeoordeling voor de software-update.  

- **Beschrijving**: Biedt een overzicht van welke toestand de software-update corrigeert of verbetert.  

- **Toepasselijke talen**: Een lijst met de talen waarvoor de software-update van toepassing is.  

- **Betrokken producten**: Geeft een lijst van de producten waarvoor de software-update van toepassing is.  

####  <a name="BKMK_ContentInformation"></a> Informatie over inhoud  
Op het tabblad **Informatie over inhoud** wordt de volgende informatie weergegeven over de inhoud die aan de geselecteerde software-update is gekoppeld:  

-   **ID van inhoud**: Hiermee geeft u de inhoud-ID voor de software-update.  

-   **Gedownload**: Geeft aan of de software-updatebestanden door Configuration Manager heeft gedownload.  

-   **Taal**: Hiermee geeft u de talen voor de software-update.  

-   **Bronpad**: Hiermee geeft u het pad naar de bronbestanden voor software-update.  

-   **Grootte (MB)**: Geeft de grootte van de bronbestanden van de software-update.  

####  <a name="BKMK_CustomBundleInformation"></a> Aangepaste bundelgegevens  
Op het tabblad **Aangepaste bundelgegevens** wordt informatie over aangepaste bundels voor de software-update weergegeven. Wanneer de geselecteerde software-update gebundelde software-updates bevat die in het software-updatebestand zijn opgenomen, worden deze weergegeven in de sectie **Bundelgegevens** . Op dit tabblad worden geen gebundelde software-updates weergegeven die worden weergegeven op het tabblad **Informatie over inhoud** , zoals updatebestanden voor verschillende talen.  

####  <a name="BKMK_SupersedenceInformation"></a> Vervangingsinformatie  
Op het tabblad **Vervangingsinformatie** wordt vervangingsinformatie weergegeven die op de software-update van toepassing is:  

- **Deze update is vervangen door de volgende updates**: Hiermee geeft u de software-updates die deze update, wat betekent dat de vermelde updates nieuwer zijn vervangen. In de meeste gevallen implementeert u een van de software-updates die de software-update vervangt. De software-updates die in de lijst worden weergegeven, bevatten hyperlinks naar webpagina's met meer informatie over de software-updates. Wanneer deze update niet wordt vervangen, wordt de waarde **Geen** weergegeven.  

- **Deze update vervangt de volgende updates**: Hiermee geeft u de software-updates die worden vervangen door deze software-update, wat betekent dat deze software-update nieuwer is. In de meeste gevallen implementeert u deze software-update om de software-updates te vervangen. De software-updates die in de lijst worden weergegeven, bevatten hyperlinks naar webpagina's met meer informatie over de software-updates. Wanneer deze update geen enkele andere update vervang, wordt de waarde **Geen** weergegeven.  

###  <a name="BKMK_SoftwareUpdatesSettings"></a> Instellingen voor software-updates configureren  
In de eigenschappen kunt u instellingen configureren voor een of meer software-updates. U kunt de meeste instellingen voor software-updates alleen configureren op de centrale beheersite of een zelfstandige primaire site. De volgende secties helpen u om instellingen voor software-updates te configureren.  

####  <a name="BKMK_SetMaxRunTime"></a> De maximale uitvoeringstijd instellen  
Stel op het tabblad **Maximale uitvoeringstijd** de maximale hoeveelheid tijd in die aan een software-update wordt toegewezen om op clientcomputers te worden voltooid. Als de update langer dan de maximumwaarde van de runtime duurt, Configuration Manager een statusbericht gemaakt en wordt de bewaking van de implementatie voor de installatie van software-updates gestopt. U kunt deze instelling alleen configureren op de centrale beheersite of een zelfstandige primaire site.  

Configuration Manager gebruikt deze instelling ook om te bepalen of de installatie van de software-update binnen het geconfigureerde onderhoudsvenster worden gestart. Als de waarde voor de maximale uitvoeringsduur groter is dan de hoeveelheid resterende tijd binnen het onderhoudsvenster, wordt de installatie van software-updates uitgesteld tot het volgende onderhoudsvenster. Wanneer er meerdere software-updates moeten worden geïnstalleerd op een clientcomputer met een geconfigureerd onderhoudsvenster (tijdsbestek), wordt de software-update met de geringste maximale uitvoeringsduur als eerste geïnstalleerd . Vervolgens wordt de software-update met de volgende geringste maximale uitvoeringsduur geïnstalleerd, enzovoort. Voordat elke software-update wordt geïnstalleerd, controleert de client of het beschikbare onderhoudsvenster voldoende tijd biedt voor het installeren van de software-update. Nadat het installeren van de software-update is gestart; wordt de installatie zelfs voortgezet als deze zich verder uitstrekt dan het einde van het onderhoudsvenster. Zie [Onderhoudsvensters gebruiken in System Center Configuration Manager](../../core/clients/manage/collections/use-maintenance-windows.md) voor meer informatie over onderhoudsvensters.  

U kunt op het tabblad **Maximale uitvoeringstijd** de volgende instellingen weergeven en configureren:  

- **Maximale uitvoeringstijd**: Hiermee geeft u het maximum aantal minuten dat wordt toegewezen, de installatie van een software-update voltooid voordat de installatie niet langer wordt gecontroleerd door Configuration Manager. Deze instelling wordt gebruikt om te bepalen of er voldoende beschikbare tijd resteert om de update voor het einde van een onderhoudsvenster te installeren. De standaardinstelling is 60 minuten voor servicepacks. De standaardwaarde is 10 minuten voor andere software-update-typen, als u hebt een nieuwe installatie van Configuration Manager versie 1511 of hoger en vijf minuten als u een upgrade uitgevoerd van een eerdere versie. Waarden kunnen uiteenlopen van 5 tot 9999 minuten.  

> [!IMPORTANT]  
>  Zorg ervoor dat u een kleinere waarde voor de maximale uitvoeringstijd instelt dan er voor de duur van het onderhoudsvenster is geconfigureerd. Anders wordt de installatie van de software-update nooit gestart.  

####  <a name="BKMK_SetCustomSeverity"></a> Aangepaste ernst instellen  
In de eigenschappen voor een software-update kunt u het tabblad **Aangepaste ernst** gebruiken om waarden voor aangepaste ernst voor de software-updates te configureren. Dit kan noodzakelijk zijn als de vooraf gedefinieerde ernstwaarden niet voldoen aan uw behoeften. De aangepaste waarden staan in de **aangepaste ernst** kolom in de Configuration Manager-console. U kunt de software-updates sorteren volgens de gedefinieerde waarden voor aangepaste ernst en u kunt ook query's en rapporten maken die op deze waarden kunnen worden gefilterd. U kunt deze instelling enkel configureren op de centrale beheersite of zelfstandige primaire site.  

U kunt de volgende instellingen configureren op het tabblad **Aangepaste ernst** .  

- **Aangepaste ernst**: Stelt een waarde voor aangepaste ernst voor de software-updates. Selecteer **Kritiek**, **Belangrijk**, **Gemiddeld**of **Laag** uit de lijst. De waarde voor aangepaste ernst is standaard leeg.

## <a name="crl-checking-for-software-updates"></a>CRL-controle voor software-updates
Standaard wordt de certificaatintrekkingslijst (CRL) niet gecontroleerd bij het verifiëren van de handtekening van software-updates van System Center Configuration Manager. Door de CRL te raadplegen elke keer dat er een certificaat wordt gebruikt, bent u beter beschermd tegen het gebruik van een ingetrokken certificaat. Hierdoor ontstaat echter ook een vertraging in de verbinding en vinden er extra verwerkingsactiviteiten plaats op de computer die de CRL-controle uitvoert.  

Als u gebruikt, moet CRL-controle worden ingeschakeld op de Configuration Manager-consoles waarop software-updates worden verwerkt.  

#### <a name="to-enable-crl-checking"></a>Controle van certificaatintrekkingslijst inschakelen  
Voer het volgende vanaf een opdrachtprompt op de computer die de CRL-controle uitvoert vanaf de product-DVD: **\SMSSETUP\BIN\X64\\**<*taal*>**\UpdDwnldCfg.exe /checkrevocation**.  

Bijvoorbeeld, voor Engels (V.S.) uitvoeren **\SMSSETUP\BIN\X64\00000409\UpdDwnldCfg.exe /checkrevocation**  

