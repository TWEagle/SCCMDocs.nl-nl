---
title: Mogelijkheden in Technical Preview 1702 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1702.
ms.custom: na
ms.date: 02/24/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aedd608d-6db3-4ea5-851d-70f2dcda6bb5
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 3bdbcd1a3c64a1d50f2f6219b2a5e17d60979864
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1702-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1702 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1702 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="send-feedback-from-the-configuration-manager-console"></a>Feedback verzenden vanuit de Configuration Manager-console

Dit voorbeeld introduceert nieuwe opties voor klantenfeedback in de Configuration Manager-console. De opties voor klantenfeedback kunt u feedback verzenden rechtstreeks naar het ontwikkelingsteam in de Configuration Manager UserVoice-feedback-website.  

>U vindt de **Feedback** optie:
-  In het lint aan de linkerkant van het tabblad Start van elk knooppunt.  
   ![Lint](./media/feedback-home.png)

-  Wanneer u met de rechtermuisknop op een object in de console.   
    ![Tabelkolom-optie](./media/feedback-option.png)   

Kiezen **Feedback** uw browser naar de website van de Configuration Manager UserVoice feedback op https://configurationmanager.uservoice.com/forums/300492-ideas wordt geopend.
##  <a name="changes-for-updates-and-servicing"></a>Wijzigingen voor Updates en onderhoud
De volgende zijn geïntroduceerd in dit voorbeeld.

**Eenvoudigere update keuzes**  
De volgende keer die uw infrastructuur in aanmerking komt voor twee of meer updates, wordt alleen de meest recente update gedownload. Bijvoorbeeld, als uw huidige siteversie is twee of meer ouder zijn dan de meest recente versie die beschikbaar is, die meest recente updateversie automatisch wordt gedownload.  

U hebt de optie om te downloaden en installeren van de andere beschikbare updates, zelfs wanneer ze niet de meest recente versie. Echter, ontvangt u een waarschuwing dat de update is vervangen door een nieuwere versie. Voor het downloaden van een update die is *beschikbaar voor Download*, selecteert u de update in de console en klik vervolgens op **downloaden**.

**Verbeterde het opruimen van oudere updates**   
We hebben een automatische opschonen-functie waarmee de overbodige downloads worden verwijderd uit de map 'EasySetupPayload' op de siteserver toegevoegd.  


## <a name="peer-cache-improvements"></a>Peer-Cache verbeteringen
Vanaf deze release is weigeren de broncomputer van een peer-cache een aanvraag voor inhoud wanneer de broncomputer peer cache voldoet aan een van de volgende voorwaarden:  
 -     In de modus voor laag accuvermogen is.
 -  CPU-belasting groter is dan 80% op het moment dat de inhoud wordt aangevraagd.
 -  Schijf-i/o heeft een *AvgDiskQueueLength* die groter is dan 10.
 -  Er zijn niet meer beschikbaar zijn verbindingen met de computer.   

U kunt deze instellingen configureren via config agentklasse van de client voor de functie peer source (*SMS_WinPEPeerCacheConfig*) wanneer u de System Center Configuration Manager-SDK gebruiken.

Als de computer een verzoek om de inhoud afwijst, blijft de aanvragende computer te zoeken naar inhoud formulier alternatieve bronnen in de groep met beschikbare inhoudsbron locaties.   

## <a name="azurediscovery"></a>Azure Active Directory Domain Services gebruiken voor het beheren van apparaten, gebruikers en groepen

Met deze technische preview beheerd versie die u kunt apparaten beheren die zijn gekoppeld aan een Azure Active Directory (AD) domeinservices domein. U kunt ook apparaten, gebruikers en groepen in het domein met verschillende Configuration Manager-detectiemethoden detecteren.

Technische preview van site-infrastructuur, clients en het domein Azure AD Domain Services moeten alle uitvoeren in Azure.


### <a name="set-up-configuration-manager-to-use-azure-ad"></a>Configuration Manager is ingesteld op Azure AD
Voor het gebruik van Azure AD met Configuration Manager, moet u het volgende:
-    Azure-abonnement.
-    Azure AD met Domain Services (DS).
-    Een Configuration Manager-site die wordt uitgevoerd op een virtuele machine van Azure die is gekoppeld aan uw Azure AD.
-    Configuration Manager-clients die worden uitgevoerd in dezelfde Azure AD-omgeving.

Zie voor het configureren van de Service Azure AD-domein [aan de slag met Azure AD-domein Services](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started).

### <a name="discover-resources"></a>Bronnen detecteren
Nadat u Configuration Manager worden uitgevoerd in Azure AD instelt, kunt u de volgende Active Directory-detectiemethoden gebruiken om te zoeken naar Azure AD voor bronnen:  
- Active Directory-systeemdetectie
- Detectie Active Directory-gebruiker
- Active Directory-groepdetectie  

Bewerk de LDAP-query om te zoeken naar de organisatie-eenheid van Azure AD-structuren in plaats van de containers die vaak met lokale Active Directory worden voor elke methode die u gebruikt. Hiervoor moet u zich voor de query voor het zoeken naar uw Active Directory in uw Azure-abonnement.  

De volgende voorbeelden gebruiken een Azure AD van *contoso.onmicrosoft.com*:
 - **Detectie-systemen**   
Azure AD slaat apparaten onder de **AADDC Computers** organisatie-eenheid.  Het volgende configureren:  
  -    *LDAP://OU=AADDC Computers, DC = contoso, DC = onmicrosoft gebruikt, DC = com*  


- **Detectie van gebruikers** AAD slaat gebruikers onder de **AADDC gebruikers** organisatie-eenheid.  Het volgende configureren:
  - *LDAP://OU=AADDC gebruikers, DC = contoso, DC = onmicrosoft gebruikt, DC = com*


- **Groepsdetectie van**  
Azure AD beschikt niet over een organisatie-eenheid waarop groepen zijn opgeslagen. In plaats daarvan gebruik van dezelfde algemene structuur als het systeem of de gebruiker query's en configureren van de LDAP-query om te verwijzen naar de organisatie-eenheid met de groepen die dat u wilt detecteren.

Zie de volgende onderwerpen voor meer informatie over Azure AD:  
 - [Azure Active Directory Domain Services](https://azure.microsoft.com/en-us/services/active-directory-ds) op azure.microsoft.com.
 - [Active Directory Domain Services-documentatie](https://docs.microsoft.com/azure/active-directory-domain-services) op docs.microsoft.com.

## <a name="conditional-access-device-compliance-policy-improvements"></a>Voorwaardelijke toegang apparaat naleving beleid verbeteringen

Een nieuw apparaat naleving beleidsregel is beschikbaar waarmee u toegang tot bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang wanneer gebruikers apps die deel van een niet-compatibele lijst met apps uitmaken blokkeren. De niet-compatibele lijst met apps kan worden gedefinieerd door de beheerder bij het toevoegen van de nieuwe regel compatibel **Apps die niet worden geïnstalleerd**. Met deze regel vereist dat de beheerder om in te voeren de **Appnaam**de **App-ID**, en de **App Publisher** (optioneel) bij het toevoegen van een app aan de lijst met niet-compatibel. Deze instelling geldt alleen voor iOS en Android-apparaten.

Daarnaast helpt dit organisaties gegevens lekken via niet-beveiligde apps te beperken en te voorkomen dat veel gegevens verbruik via bepaalde apps.

- Meer informatie [hoe nalevingsbeleid voor apparaten werken](https://docs.microsoft.com/sccm/protect/deploy-use/device-compliance-policies).
- Meer informatie [apparaat nalevingsbeleid maken](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy).

### <a name="try-it-out"></a>Probeer het nu

**Scenario:** Apps die kan worden veroorzaakt door gegevens lekken sturen zakelijke gegevens buiten uw bedrijf of die veel gegevens verbruik, klikt u vervolgens veroorzaken identificeren [maken van een nalevingsbeleid voor apparaten van voorwaardelijke toegang](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy) waarmee deze apps in de lijst met niet-compatibele Apps worden toegevoegd. Toegang tot bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang tot de geblokkeerde app door de gebruiker verwijderen kunt wordt geblokkeerd.

## <a name="antimalware-client-version-alert"></a>Waarschuwing voor Antimalware client-versie
Vanaf deze preview-versie, voorziet Configuration Manager Endpoint Protection in een waarschuwing als meer dan 20% (standaard) van beheerde clients met een verlopen versie van de client anti (dat wil zeggen Windows Defender of Endpoint Protection-client).

### <a name="try-it-out"></a>Probeer het nu
Zorg ervoor dat Endpoint Protection is ingeschakeld op alle desktop- en -clients met behulp van beleid voor client-instellingen. U kunt nu weergeven **Antimalware-clientversie** en **Status van Endpoint Protection-implementatie** door te gaan **activa en naleving** > **overzicht** > **apparaten** > **alle bureaubladen en Clients bedienen**. Weergeven om te controleren of er een waarschuwing, **waarschuwingen** in de **bewaking** werkruimte. Als meer dan 20% van beheerde clients worden met een verlopen versie van antimalware-software, de versie van de client anti-malware is verouderd waarschuwing wordt weergegeven. Deze waarschuwing niet wordt weergegeven in de **bewaking** > **overzicht** tabblad. Inschakelen voor het bijwerken van verlopen antimalware-clients, software-updates voor antimalware-clients.

Om te configureren voor het percentage waarmee de waarschuwing is gegenereerd, vouw **bewaking** > **waarschuwingen** > **alle waarschuwingen**, dubbelklikt u op **Antimalware clients verouderd** en wijzig de **waarschuwing activeren als percentage van de beheerde clients met een verouderde versie van de client antimalware is meer dan** optie.

## <a name="compliance-assessment-for-windows-update-for-business-updates"></a>Beoordeling van naleving voor Windows Update voor Business-updates
U kunt nu een naleving beleid update-regel om een Windows-Update voor Business assessment resultaat opgenomen als onderdeel van de evaluatie van voorwaardelijke toegang configureren.
> [!IMPORTANT]
> U moet Windows 10 Insider Preview Build 15019 of hoger met beoordeling van naleving voor Windows Update voor Business-updates hebben.

### <a name="allow-windows-update-for-business-to-manage-windows-10-updates"></a>Windows Update voor bedrijven voor het beheren van Windows 10-updates toestaan
Gebruik de volgende procedure de clientagentinstelling expliciet wilt toestaan Windows Update voor bedrijven voor het beheren van Windows 10-updates configureren voor het verzamelen van assessment compatibiliteitsinformatie voor Windows Update voor Business-updates.
1. Ga in de Configuration Manager-console naar **Beheer** > **Clientinstellingen**.
2. In de eigenschappen voor instellingen voor de client, gaat u naar **Software-Updates**, en selecteer **Ja** voor de **Windows 10 beheren werkt met Windows Update voor bedrijven** instelling.

### <a name="create-a-compliance-policy-for-windows-update-for-business-assessment"></a>Een nalevingsbeleid maken voor Windows Update voor Business beoordeling
1. Ga in de Configuration Manager-console naar **activa en naleving** > **compatibiliteitsinstellingen** > **nalevingsbeleid**.
2. Klik op **nalevingsbeleid maken** of Selecteer een bestaande nalevingsbeleid om te wijzigen.
3. Geef een naam en beschrijving, Selecteer op de pagina Algemeen **compliantieregels voor apparaten die worden beheerd door de Configuration Manager-client**, stelt u de non-compliantieniveau voor rapportage en op **volgende**.
4. Selecteer op de pagina ondersteunde Platforms **Windows 10**, en klik vervolgens op **volgende**.
5. Klik op de pagina regels **nieuw...** , en vervolgens voor **voorwaarde** kiezen **Windows Update is vereist voor naleving van Business**. De **waarde** is automatisch ingesteld op **waar**.

Het nieuwe beleid wordt weergegeven in het knooppunt **Nalevingsbeleid** van de werkruimte **Activa en naleving** .

### <a name="deploy-a-compliance-policy"></a>Een nalevingsbeleid implementeren
1. Ga in de Configuration Manager-console naar **activa en naleving** > **compatibiliteitsinstellingen**, en klik vervolgens op **nalevingsbeleid**.
2. Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.
3. Klik in het dialoogvenster **Nalevingsbeleid implementeren** op **Bladeren** om de gebruikersverzameling te selecteren waarvoor het beleid moet worden geïmplementeerd.
   Verder kunt u opties selecteren om waarschuwingen te genereren als het beleid niet compatibel is en ook om het schema te configureren waarmee dit beleid wordt beoordeeld op naleving.
4. Wanneer u klaar bent, klikt u op **OK**.

### <a name="monitor-the-compliance-policy"></a>Het nalevingsbeleid bewaken
Nadat u het nalevingsbeleid hebt gemaakt, kunt u de compliantieresultaten in de Configuration Manager-console kunt bewaken. Zie voor meer informatie, [het nalevingsbeleid bewaken](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="improvements-to-software-center-settings-and-notification-messages-for-high-impact-task-sequences"></a>Verbeteringen in Software Center-instellingen en meldingen voor indrukwekkende takenreeksen
Deze versie bevat de volgende verbeteringen in Software Center-instellingen en meldingen voor takenreeksen indrukwekkende implementatie:

- In de eigenschappen voor de taak nu kunt u een takenreeks, die niet het besturingssysteemstation takenreeksen, als een implementatie met een hoog risico. Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie, [met een hoog risico implementaties beheren](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u het meldingsbericht standaard gebruiken of maken van uw eigen aangepaste Meldingsbericht voor indrukwekkende implementaties.
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u Software Center eigenschappen, waaronder een opnieuw opstarten is vereist, moeten de downloadgrootte van de takenreeks, en de geschatte runtime.
- De indrukwekkende implementatie standaardbericht voor in-place upgrades nu statussen dat apps gegevens en instellingen worden automatisch gemigreerd. Eerder het standaardbericht voor de installatie van een besturingssysteem wordt aangegeven dat alle apps, gegevens en instellingen zou verloren gaan, die niet voor een upgrade ter plaatse waar is.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Een takenreeks als een indrukwekkende takenreeks instellen
Gebruik de volgende procedure in te stellen van een takenreeks als hoge impact.
> [!NOTE]
> Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie, [met een hoog risico implementaties beheren](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks te bewerken en klikt u op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **dit is een indrukwekkende takenreeks**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Een aangepaste melding voor implementaties met een hoog risico maken
1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks te bewerken en klikt u op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **u aangepaste tekst**.
>  [!NOTE]
>  U kunt alleen gebruiker meldingstekst instellen wanneer de **dit is een indrukwekkende takenreeks** is geselecteerd.

4. Configureer de volgende instellingen (maximaal 255 tekens voor elk tekstvak):

   **Gebruiker melding kopregel**: Hiermee geeft u de blauwe tekst die wordt weergegeven op de melding van de gebruiker Software Center. Bijvoorbeeld, in de melding van de gebruiker standaard bevat in deze sectie dat lijkt op "Bevestigen die u wilt upgraden van het besturingssysteem op deze computer".

   **Tekst van melding gebruiker**: Er zijn drie tekstvakken die de hoofdtekst van de aangepaste melding bieden.
   - tekstvak 1e: Hiermee geeft u de hoofdtekst van tekst, doorgaans met instructies voor de gebruiker. Bijvoorbeeld, in de melding van de gebruiker standaard bevat in deze sectie iets zoals "het besturingssysteem upgraden lang duurt en de computer enkele keren opnieuw opstarten."
   - tekstvak 2e: Hiermee geeft u de vet weergegeven onder de hoofdtekst van tekst. Bijvoorbeeld, in de melding van de gebruiker standaard bevat in deze sectie iets zoals "deze in-place upgrade wordt het nieuwe besturingssysteem geïnstalleerd en uw apps, gegevens en instellingen automatisch wordt gemigreerd."
   - tekstvak 3e: Hiermee geeft u de laatste regel van tekst onder de vet weergegeven. Bijvoorbeeld, in de melding van de gebruiker standaard in deze sectie bevat dat lijkt op ' Klik op installeren om te beginnen. Klik anders op Annuleren."   

   Stel dat u de volgende aangepaste meldingen configureren in de eigenschappen.

   ![Aangepaste melding voor een takenreeks](.\media\user-notification.png)

   De volgende melding verschijnt wanneer de installatie van Software Center wordt geopend. de eindgebruiker.

   ![Aangepaste melding voor een takenreeks](.\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>Eigenschappen van Software Center configureren
Gebruik de volgende procedure om de gegevens voor de takenreeks weergegeven in Software Center te configureren. Deze gegevens zijn alleen ter informatie.  
1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks te bewerken en klikt u op **eigenschappen**.
3. Op de **algemeen** tabblad en de volgende instellingen voor Software Center zijn beschikbaar:
  - **Opnieuw opstarten vereist**: Kan de gebruiker weet of een herstart nodig tijdens de installatie is.
  - **Grootte (MB) downloaden**: Hiermee geeft u het aantal megabytes voor de taak wordt weergegeven in Software Center.  
  - **Geschatte uitvoeringstijd (minuten)**: Hiermee geeft u dat de geschatte tijd in minuten die wordt weergegeven in Software Center voor de takenreeks wordt uitgevoerd.


## <a name="check-for-running-executable-files-before-installing-an-application"></a>Controleer voor het uitvoeren van uitvoerbare bestanden voordat de installatie van een toepassing

In de  *<deployment type name>*  **eigenschappen** in het dialoogvenster van een implementatietype op het tabblad gedrag installeren, u kunt nu een opgeven van meer uitvoerbare bestanden die als uitgevoerd, wordt de installatie van het implementatietype geblokkeerd. De gebruiker moet het actief uitvoerbaar bestand sluiten (of het automatisch kan worden gesloten voor implementaties met als doel vereist) voor de implementatie van het type kan worden geïnstalleerd.

### <a name="try-it-out"></a>Probeer het zelf.

1.    Kies in de eigenschappen van een implementatietype voor de Configuration Manager, de **gedrag installeren** tabblad.
2.    Kies **toevoegen** toevoegen van een of meer uitvoerbaar bestandsnamen die u wilt controleren. U kunt ook een weergavenaam gemakkelijker voor gebruikers om te identificeren in de lijst met toepassingen toevoegen.
3.    Als de implementatie doel vereist, in de wizard implementeren software kunt u optioneel kunt u **automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type**.

Als de toepassing is geïmplementeerd als **beschikbaar**, en een eindgebruiker probeert een toepassing te installeren, wordt ze gevraagd om te sluiten van een actieve uitvoerbare bestanden die u hebt opgegeven voordat de installatie kunt voortzetten.

Als de toepassing is geïmplementeerd als **vereist**, en de optie **automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type** is geselecteerd, zien ze een dialoogvenster dat hen informeert dat uitvoerbare bestanden die u hebt opgegeven automatisch gesloten wordt na het verstrijken van de installatiedeadline voor de toepassing. U kunt plannen dat deze dialoogvensters in **clientinstellingen** > **Computeragent**. Als u niet dat de eindgebruiker deze berichten te zien wilt, selecteert u **verbergen in Software Center en alle meldingen** op de **gebruikerservaring** tabblad van de implementatie-eigenschappen.

Als de toepassing is geïmplementeerd als **vereist** en de optie **automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type** niet is ingeschakeld, mislukt de installatie van de app als een of meer van de opgegeven toepassingen worden uitgevoerd.

## <a name="create-pfx-certificates-with-s-mime-support"></a>PFX-certificaten met ondersteuning voor S MIME maken

U kunt nu een PFX-certificaatprofiel dat S/MIME ondersteunt maken en implementeren voor gebruikers.  Dit certificaat kan vervolgens worden gebruikt voor S/MIME-codering en decodering over apparaten die de gebruiker is geregistreerd.

Daarnaast kunt u nu meerdere certificeringsinstanties (CA's) op meerdere Certificaatregistratiepunt sitesysteemrollen opgeven en vervolgens welke aanvragen worden verwerkt CAs toewijzen als onderdeel van het certificaatprofiel.

U kunt een PFX-certificaatprofiel voor een e-mailprofiel koppelen en S/MIME-versleuteling inschakelen voor iOS-apparaten.  Dit vervolgens S/MIME kan in de native e-mailclient op iOS- en koppelt het juiste S/MIME-versleutelingscertificaat toe.

Zie voor meer informatie over certificaten in Configuration Manager [Inleiding tot certificaatprofielen in System Center Configuration Manager]( https://docs.microsoft.com/sccm/protect/deploy-use/introduction-to-certificate-profiles).


## <a name="new-compliance-settings-for-ios-devices"></a>Nieuwe compatibiliteitsinstellingen voor iOS-apparaten

Nieuwe instellingen die u in uw configuratie-items voor iOS-apparaten gebruiken kunt toegevoegd. Dit zijn de instellingen die eerder beschikbaar waren in Microsoft Intune in een zelfstandige configuratie en zijn nu beschikbaar wanneer u Intune met Configuration Manager. Als u hulp nodig met een van deze instellingen, Zie [iOS-instellingen voor Groepsbeleid in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).

- **Synchronisatie van gegevens van beheerde apps naar iCloud**
- **Leveren activiteiten voort te zetten op een ander apparaat**
- **iCloud foto's delen**
- **iCloud afbeeldingsbibliotheek**
- **Nieuwe enterprise app auteurs vertrouwen**
- **Kan de gebruiker om inhoud te downloaden uit de store iBook is gemarkeerd als 'Erotica'** (modus supervisie alleen)
- **Force gekoppeld kijkt naar Apple pols detectie gebruiken**
- **Wachtwoord voor AirPlay uitgaande aanvragen**
- **Wijzig de accountinstellingen** (modus supervisie alleen)
- **Wijzigingen in app-instellingen voor het gebruik van mobiel gegevens** (modus supervisie alleen)
- **Alle inhoud en instellingen wissen** (modus supervisie alleen)
- **Hiermee configureert u beperkingen op apparaat** (modus supervisie alleen)
- **Gebruik zijnde host koppelen voor het beheren van de apparaten een iOS-apparaat met combineren kunt** (modus supervisie alleen)
- **Installeren van certificaten en kunt u configuratieprofielen** (modus supervisie alleen)
- **Naam bewerken van het apparaat** (modus supervisie alleen)
- **Wachtwoordcode wijziging** (modus supervisie alleen)
- **Koppelen van Apple Watch** (modus supervisie alleen)
- **Melding instellingen wijziging** (modus supervisie alleen)
- **Wijziging achtergrond** (modus supervisie alleen)
- **Diagnostische gegevens verzenden instellingen wijziging** (modus supervisie alleen)
- **Bluetooth wijziging** (modus supervisie alleen)
- **AirDrop** (modus supervisie alleen)
- **Gebruik van Siri aan de gebruiker gegenereerde query-inhoud van het Internet** (modus supervisie alleen)
- **Siri taalgebruik filter** (modus supervisie alleen)
- **Resultaat van het Internet in Spotlight zoekopdracht** (modus supervisie alleen)
- **Word opzoeken** (modus supervisie alleen)
- **Voorspellende toetsenborden** (modus supervisie alleen)
- **Automatische correcties** (modus supervisie alleen)
- **Toetsenbord spelling controleren** (modus supervisie alleen)
- **Sneltoetsen** (modus supervisie alleen)
<!--- - **Enterprise app trust settings modification** --->
- **Installeren van apps met Apple Configurator en iTunes alleen** (modus supervisie alleen)
- **Automatische app downloads** (modus supervisie alleen)
- **Wijzigingen aanbrengen in de instellingen van de app Zoek mijn vrienden** (modus supervisie alleen)
- **Toegang tot de store iBooks** (modus supervisie alleen)
- **Berichten app** (modus supervisie alleen)
- **Podcasts** (modus supervisie alleen)
- **Apple muziek** (modus supervisie alleen)
- **iTunes Radio** (modus supervisie alleen)
- **Apple-nieuws** (modus supervisie alleen)
- **Game Center** (modus supervisie alleen)
- **AirDrop behandelen als een onbeheerde-doel**

## <a name="android-for-work-support"></a>Android voor ondersteuning van werkitems

Beginnen met de technische voorbeeldversie 1702, kunt u een Google-account binden aan uw hybride MDM-tenant. Hierdoor kunt u het volgende doen:

- Inschrijven [Android-apparaten ondersteund](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) als Android for Work werkprofielen aanmaken op de geregistreerde apparaten
- Apps in de Play voor werk store goedkeuren, ze te synchroniseren met de Configuration Manager-console en vervolgens implementeren voor apparaten werkprofielen
- Maken en implementeren van configuratie-items om te werken profiel instellingen en het wachtwoord voor deze apparaten configureren
- Maken en implementeren van beleid-items voor compatibiliteit en resourcetoegangsprofielen voor Android voor werk apparaten als al voor Android-apparaten
- Selectief wissen op Android voor werk apparaten uitvoeren

Wanneer u een apparaat inschrijft zoals Android for Work een werkprofiel voor op het apparaat welke Intune maakt kunnen beheren. Deze werkprofiel bestaat side-by-side met het persoonlijk profiel op het Android-apparaat. Gebruikers kunnen eenvoudig schakelen tussen werk profiel apps en apps persoonlijk profiel. U kunt geen items in het persoonlijk profiel beheren. Persoonlijke apps en gegevens blijven niet-beheerd. Configuration Manager heeft volledige controle over de werkprofiel en de inhoud ervan en van het apparaat kunt verwijderen.

Android for Work is een afzonderlijke platform van Android en moet u bepalen welke vorm van management voor Android-apparaten die ondersteuning bieden voor werkprofielen te gebruiken.

### <a name="try-it-out"></a>Probeer het nu!
De volgende secties beschrijven Android voor het beheer van werkitems.

#### <a name="enable-android-for-work-management"></a>Android inschakelen voor werkstroombeheer
1. Maak een Google-account op https://accounts.google.com/SignUp wilt gebruiken als uw Android voor werk beheeraccount die gekoppeld aan alle Android voor werk beheertaken voor deze tenant Intune is. Dit wordt mogelijk een Google-account gedeeld met de beheerders die Android-apparaten te beheren. Dit is het Google-account die gebruikmaakt van uw organisatie te beheren en publiceren van apps in de Play voor werk-console. U gebruikt dit account voor het goedkeuren van apps in de Play voor werk store, dus bijhouden van de accountnaam en wachtwoord.
2. Android-inschrijving inschakelen door het binden van Google-account voor de Intune-tenant in Configuration Manager worden beheerd:
  1. Ga naar **beheer** > **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen** en selecteer de Intune-abonnement.
  2. Klik in het lint op **Platforms configureren** > **Android** en zorg ervoor dat **inschakelen Android-inschrijving** wordt gecontroleerd.
  3. Klik in het lint op **Platforms configureren** > **Android for Work**.
  4. Klik in het dialoogvenster **Android configureren voor werkitems in de Intune-beheerconsole**. De Intune-console wordt geopend in uw webbrowser.
  5. Gebruik de Intune-beheerdersreferenties om aan te melden bij de Intune-portal.
  6. Klik op **configureren** Android van Google Play voor werk website te openen.
  7. Voer de referenties van het Google-account uit stap 1 op van Google-aanmeldingspagina, en geef vervolgens de gegevens van uw bedrijf.
3. Wanneer u naar de Intune-portal terugkeert, Android for Work is ingeschakeld en hebt u drie Inschrijvingsopties voor Android voor werk apparaten:
  - **Alle apparaten beheren als Android** - (uitgeschakeld) alle Android-apparaten, met inbegrip van apparaten die ondersteuning bieden voor Android voor werk, zal het worden ingeschreven als conventionele Android-apparaten
  - **Ondersteunde apparaten beheren als Android for Work** - (geactiveerd) alle apparaten die ondersteuning bieden voor Android for Work als Android voor werk apparaten zijn ingeschreven. Een Android-apparaat dat biedt geen ondersteuning voor Android voor werk is geregistreerd als een conventionele Android-apparaat.
  - **Ondersteunde apparaten voor gebruikers alleen in deze groepen beheren als Android for Work** -(Testing) kunt u zich richten op Android voor werkstroombeheer voor een beperkte set van gebruikers. Alleen leden van de geselecteerde groepen die een apparaat dat ondersteuning Android for Work biedt inschrijven worden geregistreerd als Android voor werk apparaten. Alle andere worden geregistreerd als Android-apparaten.
  
> [!NOTE]
> Een bekend probleem voorkomt dat de **beheren apparaten voor gebruikers in deze groepen alleen ondersteund als Android for Work** optie niet werkt zoals verwacht. Apparaten van gebruikers in de opgegeven Azure AD-groepen als Android in plaats van Android for Work gaan registreren. Als u wilt testen Android voor werk, moet u de **alle ondersteunde apparaten beheren als Android for Work**.


  Om in te schakelen Android voor de inschrijving van het werk, moet u een van de onderste twee opties. De **beheren apparaten voor gebruikers in deze groepen alleen ondersteund als Android for Work** optie moet u Azure Active Directory-beveiligingsgroepen instellen.

U ziet de accountnaam en organisatienaam in de Intune-portal als de binding voltooid is. op dat moment kunt u beide browsers sluiten.

#### <a name="approve-and-deploy-android-for-work-apps"></a>Goedkeuren en implementeren van Android voor zakelijke apps
Volg deze stappen voor het goedkeuren van apps in de Play voor werk store, ze te synchroniseren met de Configuration Manager-console en deze beheerde Android voor werk apparaten implementeren. Voor apps op werk gebruikersprofielen implementeert, moet u de apps in Play for Work goedkeuren en vervolgens de apps met de Configuration Manager-console te synchroniseren.

1. Open een browser en Ga naar: https://play.google.com/work.
2. Meld u aan met de Google-beheeraccount afhankelijk van uw Intune-tenant.
3. Apps die u wilt implementeren in uw omgeving en klik op Bladeren **goedkeuren** voor elk van deze.
4. Ga in de Configuration Manager-console naar **Administrator** > **overzicht** > **Cloudservices** > **Android for Work** en klikt u op **Sync**.
5. Wacht 10 minuten duren om apps te synchroniseren en ga vervolgens **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **licentie-informatie voor de Store-Apps**.
6. Klik op een app gesynchroniseerd vanuit Play voor het werk en klik vervolgens op **toepassing maken**.
7. Voltooi de wizard en klikt u op **sluiten**.
8. Ga naar **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**, selecteert u een Android voor zakelijke apps en gewoon implementeren.

Als u wilt synchroniseren Play voor zakelijke apps met Configuration Manager, moet u ten minste één app in de Play voor werk website goedkeuren.

#### <a name="enroll-an-android-for-work-device"></a>Een Android voor werk apparaat inschrijven
Hoe het registreren van Android voor werk apparaten is vergelijkbaar met inschrijving voor Android. Downloaden en uitvoeren van de bedrijfsportal-app voor Android op je mobiele apparaat. U wordt gevraagd een werkprofiel maken als onderdeel van het registratieproces.  Zodra de werkprofiel is gemaakt, moet u overschakelen naar de beheerde versie van de bedrijfsportal. De beheerde bedrijfsportal is gemarkeerd met een klein oranje werkmap in de rechterbenedenhoek.

#### <a name="create-and-deploy-a-configuration-item"></a>Maken en implementeren van een configuratie-item
Android for Work heeft twee instellingsgroepen voor configuratie-items:
- Wachtwoord
- Werkprofiel

U kunt inhoud delen tussen werkprofielen, evenals de volgende configuratie-items op apparaten met Android 6 of hoger configureren:
- Het gedrag voor het verzoek om een specifieke machtiging apps
- Of meldingen voor toepassingen in de werkprofiel zichtbaar zijn op het vergrendelingsscherm

Probeer een configuratie-item via de standaard werkstroom maakt, kiest u **Android for Work** op de **algemeen** pagina en configureer instellingen voor elk van de configuratie-item toevoegen aan een basislijn en implementeren van gewoon de instellingsgroepen. Deze instellingen wordt alleen toegepast op apparaten die zijn geregistreerd als Android voor werk, en niet de geregistreerd als Android.

#### <a name="perform-selective-wipe"></a>U selectief wilt wissen
Apparaten geregistreerd als Android for Work alleen selectief kan worden gewist omdat u alleen de werkprofiel te beheren. Dit voorkomt dat het persoonlijk profiel wordt gewist. Selectief wissen uitvoeren op een Android voor werk apparaat, verwijdert u de werkprofiel, inclusief alle apps en gegevens, en unenrolls van het apparaat.

Gebruiken voor het selectief wissen van een Android voor werk apparaat, de normale [selectief wissen proces](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe) in de Configuration Manager-console.

#### <a name="known-issues-for-android-for-work"></a>Bekende problemen voor Android voor werkitems
**Synchronisatie configureren ze te plannen in Android voor werk e-mailprofielen oorzaken voor de implementatie mislukt** een van de opties in de ConfigMgr-UI voor Android voor e-mailprofielen werk is 'Schema'. Dit kan de beheerder een planning voor het synchroniseren van e-mail en andere gegevens van de e-account naar de mobiele apparaten, die dit wordt geïmplementeerd voor configureren op andere platforms. Echter werkt niet voor Android voor werk-e-mailprofielen en elke optie dan 'Niet geconfigureerd' zorgt ervoor dat het profiel niet worden geïmplementeerd voor alle apparaten.

