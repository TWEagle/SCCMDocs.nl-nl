---
title: Mogelijkheden van Technical Preview 1702
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1702.
ms.custom: na
ms.date: 02/24/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aedd608d-6db3-4ea5-851d-70f2dcda6bb5
caps.latest.revision: "5"
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: ed2a858c55cbf389a0e974f4699b5a9c548953ef
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1702-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1702 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1702 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="send-feedback-from-the-configuration-manager-console"></a>Feedback verzenden vanuit de Configuration Manager-console

Deze preview introduceert nieuwe opties voor klantenfeedback in de Configuration Manager-console. De opties voor klantenfeedback kunt u feedback rechtstreeks naar het ontwikkelingsteam via de website van de Configuration Manager UserVoice-feedback verzenden.  

>U vindt de **Feedback** optie:
-  In het lint, aan de linkerkant van het tabblad Start van elk knooppunt.  
   ![Lint](./media/feedback-home.png)

-  Wanneer u met de rechtermuisknop op een object in de console.   
    ![De optie kopiëren en klik op](./media/feedback-option.png)   

Kiezen **Feedback** uw browser naar de website van de Configuration Manager UserVoice feedback op https://configurationmanager.uservoice.com/forums/300492-ideas wordt geopend.
##  <a name="changes-for-updates-and-servicing"></a>Wijzigingen voor Updates en onderhoud
De volgende zijn geïntroduceerd in dit voorbeeld.

**Eenvoudiger update keuzes**  
De volgende keer dat uw infrastructuur in aanmerking komt voor twee of meer updates, wordt alleen de meest recente update gedownload. Bijvoorbeeld, als uw huidige siteversie is twee of meer ouder is dan de meest recente versie die beschikbaar is, is deze meest recente updateversie automatisch wordt gedownload.  

U hebt de optie voor het downloaden en installeren van de andere beschikbare updates, zelfs wanneer ze niet de meest recente versie. Echter, ontvangt u een waarschuwing dat de update is vervangen door een nieuwere versie. Voor het downloaden van een update die *beschikbaar voor Download*, selecteert u de update in de console en klik vervolgens op **downloaden**.

**Verbeterde het opruimen van de oudere updates**   
We hebben een automatische opschoning-functie die de overbodige downloads uit de map 'EasySetupPayload' op uw siteserver verwijdert toegevoegd.  


## <a name="peer-cache-improvements"></a>Verbeteringen voor peer-Cache
Vanaf deze release, weigert een peer-cache-broncomputer een aanvraag voor inhoud wanneer de peer-cache-bron-computer voldoet aan een van de volgende voorwaarden:  
 -  In de modus voor laag accuvermogen is.
 -  CPU-belasting groter is dan 80% op het moment dat de inhoud wordt aangevraagd.
 -  Schijf-i/o heeft een *AvgDiskQueueLength* die groter is dan 10.
 -  Er zijn niet meer beschikbaar zijn verbindingen met de computer.   

U kunt deze instellingen configureren via de clientklasse agent-configuratie voor de functie voor peer-source (*SMS_WinPEPeerCacheConfig*) wanneer u System Center Configuration Manager SDK gebruiken.

Als de computer een aanvraag voor de inhoud afwijst, blijft de aanvragende computer te zoeken naar inhoud formulier alternatieve bronnen in de groep met beschikbare inhoudsbron locaties.   

## <a name="azurediscovery"></a>Azure Active Directory Domain Services gebruiken voor het beheren van apparaten, gebruikers en groepen

Met deze technical preview versie die u kunt apparaten beheren die zijn gekoppeld aan een Azure Active Directory (AD) Domain-Services worden beheerd domein. U kunt ook apparaten, gebruikers en groepen in het domein detecteren met verschillende detectiemethoden van Configuration Manager.

De technical preview-site-infrastructuur, clients en het domein van Azure AD Domain Services moeten allemaal in Azure uitvoeren.


### <a name="set-up-configuration-manager-to-use-azure-ad"></a>Stel Configuration Manager in Azure AD gebruiken
Voor het gebruik van Azure AD met Configuration Manager, hebt u het volgende nodig:
-   Azure-abonnement.
-   Azure AD Domain Services (DS).
-   Een Configuration Manager-site die wordt uitgevoerd op een virtuele machine van Azure die is gekoppeld aan uw Azure AD.
-   Configuration Manager-clients die worden uitgevoerd in dezelfde Azure AD-omgeving.

Voor het configureren van Azure AD Domain Services, Zie [aan de slag met Azure AD Domain Services](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started).

### <a name="discover-resources"></a>Detecteren van bronnen
Nadat u Configuration Manager instellen om uit te voeren in Azure AD, kunt u de volgende Active Directory-detectiemethoden gebruiken om te zoeken, Azure AD voor resources:  
- Active Directory-systeemdetectie
- Detectie Active Directory-gebruiker
- Active Directory-groepdetectie  

Voor elke methode die u gebruikt, bewerkt u de LDAP-query om te zoeken naar de organisatie-eenheid van Azure AD-structuren in plaats van de containers die specifiek voor de lokale Active Directory zijn. Hiervoor moet u de query voor het zoeken naar uw Active Directory in uw Azure-abonnement wordt omgeleid.  

De volgende voorbeelden gebruikt een Azure AD van *contoso.onmicrosoft.com*:
 - **Detectie-systemen**   
Azure AD worden opgeslagen voor apparaten onder de **AADDC Computers** organisatie-eenheid.  Het volgende configureren:  
  - *LDAP://OU=AADDC Computers, DC = contoso, DC = onmicrosoft gebruikt, DC = com*  


- **Detectie van gebruikers** AAD slaat gebruikers onder de **AADDC gebruikers** organisatie-eenheid.  Het volgende configureren:
  - *LDAP://OU=AADDC gebruikers, DC = contoso, DC = onmicrosoft gebruikt, DC = com*


- **Detectie-groepen**  
Azure AD beschikt niet over een organisatie-eenheid die groepen opslaat. In plaats daarvan de dezelfde algemene structuur gebruiken als het systeem of gebruiker query's en configureren van de LDAP-query om te verwijzen naar de organisatie-eenheid waarin de groepen die dat u wilt detecteren.

Zie de volgende onderwerpen voor meer informatie over Azure AD:  
 - [Azure Active Directory Domain Services](https://azure.microsoft.com/en-us/services/active-directory-ds) op azure.microsoft.com.
 - [Active Directory Domain Services-documentatie](https://docs.microsoft.com/azure/active-directory-domain-services) op docs.microsoft.com.

## <a name="conditional-access-device-compliance-policy-improvements"></a>Voorwaardelijke toegang apparaat naleving beleid verbeteringen

Een nieuw apparaat naleving beleidsregel is beschikbaar waarmee u toegang tot bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang, wanneer gebruikers apps die deel van een niet-compatibele lijst met apps uitmaken blokkeren. De niet-compatibele lijst met apps kan worden gedefinieerd door de beheerder bij het toevoegen van de nieuwe regel compatibele **Apps die niet kunnen worden geïnstalleerd**. Deze regel vereist dat de beheerder om in te voeren de **Appnaam**, wordt de **App-ID**, en de **App Publisher** (optioneel) wanneer een app toe te voegen aan de lijst met niet-compatibele. Deze instelling geldt alleen voor iOS en Android-apparaten.

Dit helpt bovendien organisaties lekken van gegevens via niet-beveiligde apps te beperken en het verbruik van veel gegevens via bepaalde apps te voorkomen.

- Meer informatie [de werking van beleid voor apparaatcompatibiliteit](https://docs.microsoft.com/sccm/protect/deploy-use/device-compliance-policies).
- Meer informatie [nalevingsbeleid voor apparaten maken](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy).

### <a name="try-it-out"></a>Try it out in

**Scenario:** Identificeren van apps die mogelijk veroorzaakt door lekken van gegevens door zakelijke gegevens buiten uw bedrijf te verzenden of die veel gegevens verbruik, vervolgens veroorzaken [maken van een nalevingsbeleid voor apparaten van voorwaardelijke toegang](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy) waarmee deze apps in de lijst met niet-compatibele Apps worden toegevoegd. Dit wordt toegang tot bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang tot de geblokkeerde app door de gebruiker verwijderen kunt geblokkeerd.

## <a name="antimalware-client-version-alert"></a>Waarschuwing voor Antimalware client versie
Met deze preview-versie biedt, Configuration Manager Endpoint Protection vanaf een waarschuwing als meer dan 20% (standaard) van beheerde clients met een verlopen versie van de antimalware-client (dat wil zeggen Windows Defender of Endpoint Protection-client).

### <a name="try-it-out"></a>Try it out in
Zorg ervoor dat Endpoint Protection is ingeschakeld op alle desktop- en -clients met behulp van beleid voor client-instellingen. U kunt nu weergeven **Antimalware-clientversie** en **Status van Endpoint Protection-implementatie** door te gaan **activa en naleving** > **overzicht** > **apparaten** > **alle bureaubladen en Clients bedienen**. Bekijken om te controleren of een waarschuwing, **waarschuwingen** in de **bewaking** werkruimte. Als meer dan 20% van beheerde clients een verlopen versie van de antimalware-software, de versie van de Antimalware-client is verouderd waarschuwing wordt weergegeven. Deze waarschuwing niet wordt weergegeven op de **bewaking** > **overzicht** tabblad. Voor het bijwerken van verlopen antimalware-clients, moet u software-updates inschakelen voor anti-malware-clients.

Als u wilt configureren voor het percentage waarmee de waarschuwing wordt gegenereerd, vouw **bewaking** > **waarschuwingen** > **alle waarschuwingen**, dubbelklikt u op **Antimalware clients verouderd** en wijzig de **waarschuwing activeren als percentage van de beheerde clients met een verouderde versie van de antimalware-client is meer dan** optie.

## <a name="compliance-assessment-for-windows-update-for-business-updates"></a>Nalevingsbeoordeling voor Windows Update voor bedrijven-updates
U kunt nu een regel voor naleving beleid update voor een Windows Update for Business assessment resultaat opnemen als onderdeel van de evaluatie van voorwaardelijke toegang configureren.
> [!IMPORTANT]
> U moet Windows 10 Insider Preview-versie 15019 of hoger met beoordeling van compatibiliteit voor Windows Update voor bedrijven-updates hebben.

### <a name="allow-windows-update-for-business-to-manage-windows-10-updates"></a>Windows Update voor bedrijven voor het beheren van Windows 10-updates toestaan
Gebruik de volgende procedure voor het configureren van de clientagentinstelling voor expliciet toestaan Windows Update voor bedrijven voor het beheren van Windows 10-updates voor het verzamelen van assessment compatibiliteitsinformatie voor Windows Update voor bedrijven-updates.
1. Ga in de Configuration Manager-console naar **Beheer** > **Clientinstellingen**.
2. In de eigenschappen voor instellingen van de client, gaat u naar **Software-Updates**, en selecteer **Ja** voor de **beheren van Windows 10-updates met Windows Update voor bedrijven** instelling.

### <a name="create-a-compliance-policy-for-windows-update-for-business-assessment"></a>Een nalevingsbeleid maken voor Windows Update voor bedrijven-evaluatie
1. Ga in de Configuration Manager-console naar **activa en naleving** > **instellingen voor naleving** > **nalevingsbeleid**.
2. Klik op **nalevingsbeleid maken** of Selecteer een bestaand nalevingsbeleid te wijzigen.
3. Geef een naam en beschrijving, Selecteer op de pagina Algemeen **nalevingsegels voor apparaten die worden beheerd door Configuration Manager-client**, instellen van de ernst van niet-naleving voor rapportage en klikt u op **volgende**.
4. Selecteer op de pagina ondersteunde Platforms **Windows 10**, en klik vervolgens op **volgende**.
5. Klik op de pagina regels **nieuw...** , en vervolgens voor **voorwaarde** kiezen **vereisen Windows Update voor bedrijven naleving**. De **waarde** is automatisch ingesteld op **True**.

Het nieuwe beleid wordt weergegeven in het knooppunt **Nalevingsbeleid** van de werkruimte **Activa en naleving** .

### <a name="deploy-a-compliance-policy"></a>Een nalevingsbeleid implementeren
1. Ga in de Configuration Manager-console naar **activa en naleving** > **instellingen voor naleving**, en klik vervolgens op **nalevingsbeleid**.
2. Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.
3. Klik in het dialoogvenster **Nalevingsbeleid implementeren** op **Bladeren** om de gebruikersverzameling te selecteren waarvoor het beleid moet worden geïmplementeerd.
   Verder kunt u opties selecteren om waarschuwingen te genereren als het beleid niet compatibel is en ook om het schema te configureren waarmee dit beleid wordt beoordeeld op naleving.
4. Wanneer u klaar bent, klikt u op **OK**.

### <a name="monitor-the-compliance-policy"></a>Het nalevingsbeleid bewaken
Nadat u het nalevingsbeleid hebt gemaakt, kunt u de nalevingsresultaten in Configuration Manager-console kunt bewaken. Zie voor meer informatie [het nalevingsbeleid bewaken](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="improvements-to-software-center-settings-and-notification-messages-for-high-impact-task-sequences"></a>Verbeteringen aan Software Center-instellingen en meldingen voor hoge impact takenreeksen
Deze versie bevat de volgende verbeteringen aangebracht in de instellingen van Software Center en meldingen voor implementatie met hoge impact takenreeksen:

- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u nu een takenreeks wordt uitgevoerd, niet het besturingssysteemstation takenreeksen, waaronder als een implementatie met hoog risico configureren. Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie [beheren van implementaties met een hoog risico](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u het meldingsbericht standaard gebruiken of maken van uw eigen aangepaste Meldingsbericht voor implementaties met hoge impact.
- In de eigenschappen voor de takenreeks wordt uitgevoerd, kunt u Software Center-eigenschappen, waaronder een herstart vereist is, Controleer de grootte van het downloadpakket van de takenreeks en de geschatte tijd worden uitgevoerd.
- Het standaardbericht implementatie met hoge impact voor in-place upgrades nu statussen uw apps, gegevens en instellingen automatisch gemigreerd. Voorheen het standaardbericht voor de installatie van een besturingssysteem wordt aangegeven dat alle apps, gegevens en instellingen zouden verloren gaan, die is niet true zijn voor een in-place upgrade.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Een takenreeks ingesteld als een takenreeks met hoge impact
Gebruik de volgende procedure in te stellen van een takenreeks als hoge impact.
> [!NOTE]
> Elke takenreeks die voldoet aan bepaalde voorwaarden wordt automatisch gedefinieerd als hoge impact. Zie voor meer informatie [beheren van implementaties met een hoog risico](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **dit is een grote impact takenreeks**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Een aangepaste melding voor implementaties met een hoog risico maken
1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **gebruikersmelding** tabblad **u aangepaste tekst**.
>  [!NOTE]
>  U kunt alleen de berichttekst gebruiker instellen wanneer de **dit is een grote impact takenreeks** is geselecteerd.

4. Configureer de volgende instellingen (maximaal 255 tekens bestaan voor elk tekstvak):

   **Gebruiker melding kopregel**: Hiermee geeft u de blauwe tekst die wordt weergegeven op de melding voor gebruikers van Software Center. Bijvoorbeeld, in de gebruikersmelding standaard bevat in deze sectie ongeveer 'Bevestigen voor het bijwerken van het besturingssysteem op deze computer'.

   **Gebruiker melding berichttekst**: Er zijn drie tekstvakken waarmee de hoofdtekst van de aangepaste melding.
   - 1e tekstvak: Hiermee geeft u de hoofdtekst van tekst, meestal met instructies voor de gebruiker. In de gebruikersmelding standaard bevat in deze sectie bijvoorbeeld iets zoals 'besturingssysteem upgraden tijd kost en de computer enkele keren opnieuw opstarten.'
   - tekstvak voor 2e: Hiermee geeft u de vetgedrukte onder de hoofdtekst. In de gebruikersmelding standaard bevat in deze sectie bijvoorbeeld iets zoals 'deze in-place upgrade wordt het nieuwe besturingssysteem geïnstalleerd en worden uw apps, gegevens en instellingen automatisch gemigreerd.'
   - tekstvak voor 3e: Hiermee geeft u de laatste regel van de tekst onder de vetgedrukte. Bijvoorbeeld, in de gebruikersmelding standaard in deze sectie bevat dat lijkt op ' Klik op installeren om te beginnen. Klik anders op Annuleren."   

   Stel dat u de volgende aangepaste melding in de eigenschappen configureren.

   ![Aangepaste melding voor een takenreeks](.\media\user-notification.png)

   Het volgende bericht wordt weergegeven wanneer de eindgebruiker opent de installatie van Software Center.

   ![Aangepaste melding voor een takenreeks](.\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>Eigenschappen van Software Center configureren
Gebruik de volgende procedure om de gegevens voor de takenreeks weergegeven in Software Center te configureren. Deze gegevens zijn alleen ter informatie.  
1. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **besturingssystemen** > **Takenreeksen**.
2. Selecteer de takenreeks bewerken en klik op **eigenschappen**.
3. Op de **algemene** tabblad en de volgende instellingen voor Software Center zijn beschikbaar:
  - **Opnieuw opstarten vereist**: Kan de gebruiker weet of opnieuw opstarten vereist tijdens de installatie is.
  - **Grootte (MB) downloaden**: Hiermee geeft u op hoeveel megabytes wordt weergegeven in Software Center voor de takenreeks.  
  - **Geschatte uitvoeringstijd (minuten)**: Hiermee geeft u dat de geschatte tijd in minuten die wordt weergegeven in Software Center voor de takenreeks wordt uitgevoerd.


## <a name="check-for-running-executable-files-before-installing-an-application"></a>Controleer voor het uitvoeren van uitvoerbare bestanden voordat u een toepassing installeert

In de  *<deployment type name>*  **eigenschappen** in het dialoogvenster van een implementatietype op het tabblad gedrag installeren, u kunt nu een opgeven van meer uitvoerbare bestanden die als actief is, wordt de installatie van het implementatietype blokkeren. De gebruiker moet de lopende uitvoerbaar bestand sluiten (of het automatisch kan worden gesloten voor implementaties met als doel vereist) voordat de implementatie van het type kan worden geïnstalleerd.

### <a name="try-it-out"></a>Uitproberen.

1.  Kies in de eigenschappen van een implementatietype voor de Configuration Manager, de **gedrag installeren** tabblad.
2.  Kies **toevoegen** toevoegen van een of meer uitvoerbaar bestandsnamen die u wilt controleren. U kunt ook een weergavenaam om het gemakkelijker voor gebruikers om te identificeren van toepassingen in de lijst toevoegen.
3.  Als de implementatie doel vereist, in de wizard software implementeren desgewenst kunt u **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type**.

Als de toepassing is geïmplementeerd als **beschikbaar**, en een eindgebruiker probeert een toepassing te installeren, wordt hij gevraagd om te sluiten van alle actieve uitvoerbare bestanden opgegeven voordat ze de installatie kunnen voortzetten.

Als de toepassing is geïmplementeerd als **vereist**, en de optie **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type** is geselecteerd, zien ze een dialoogvenster waarin ze worden geïnformeerd dat uitvoerbare bestanden die u hebt opgegeven automatisch worden gesloten wanneer de deadline van de installatie van de toepassing is bereikt. U kunt plannen dat deze dialoogvensters in **clientinstellingen** > **Computeragent**. Als u niet dat de eindgebruiker deze berichten te zien wilt, selecteert u **verbergen in Software Center en alle meldingen verbergen** op de **gebruikerservaring** tabblad van de implementatie-eigenschappen.

Als de toepassing is geïmplementeerd als **vereist** en de optie **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type** niet is ingeschakeld, mislukt de installatie van de app als een of meer van de opgegeven toepassingen worden uitgevoerd.

## <a name="create-pfx-certificates-with-s-mime-support"></a>PFX-certificaten te maken met MIME-S-ondersteuning

U kunt nu een PFX-certificaatprofiel dat S/MIME ondersteunt maken en naar gebruikers implementeren.  Dit certificaat kan vervolgens worden gebruikt voor S/MIME-versleuteling en ontsleuteling op apparaten die de gebruiker is ingeschreven.

Bovendien kunt u nu meerdere certificeringsinstanties (CA's) op meerdere sitesysteemrollen voor Certificaatregistratiepunt opgeven en vervolgens welke aanvragen CA's verwerkt toewijzen als onderdeel van het certificaatprofiel.

U kunt voor iOS-apparaten koppelen van een profiel voor een PFX-certificaat moet een e-mailprofiel en S/MIME-versleuteling inschakelen.  Dit vervolgens S/MIME kan in de systeemeigen e-mailclient op iOS en koppelt u het juiste S/MIME-versleutelingscertificaat aan.

Zie voor meer informatie over certificaten in Configuration Manager [Inleiding tot certificaatprofielen in System Center Configuration Manager]( https://docs.microsoft.com/sccm/protect/deploy-use/introduction-to-certificate-profiles).


## <a name="new-compliance-settings-for-ios-devices"></a>Nieuwe instellingen voor naleving voor iOS-apparaten

Nieuwe instellingen die kunt u in uw configuratie-items voor iOS-apparaten toegevoegd. Dit zijn de instellingen die eerder beschikbaar waren in Microsoft Intune in een zelfstandige configuratie en zijn nu beschikbaar wanneer u Intune met Configuration Manager. Als u hulp nodig met een van deze instellingen, Zie [instellingen voor iOS-beleid in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).

- **Gegevens synchroniseren vanuit beheerde apps met iCloud**
- **Voortzetten van activiteiten op een ander apparaat via Handoff**
- **iCloud foto's delen**
- **iCloud afbeeldingsbibliotheek**
- **Nieuwe enterprise app auteurs vertrouwen**
- **Kan de gebruiker om inhoud te downloaden uit de Ibooks store als Erotisch gemarkeerd,'** (alleen in supervisiemodus)
- **Force gekoppeld kijkt naar Apple pols detectie gebruiken**
- **Wachtwoord voor aanvragen voor uitgaande AirPlay**
- **Wijzigen van accountinstellingen** (alleen in supervisiemodus)
- **Wijzigingen in de app-instellingen voor het gebruik van mobiel dataverkeer** (alleen in supervisiemodus)
- **Wissen van alle inhoud en instellingen** (alleen in supervisiemodus)
- **Configureert u beperkingen op apparaat** (alleen in supervisiemodus)
- **Gebruik een host om te bepalen met welke apparaten een iOS-apparaat kunt koppelen aan** (alleen in supervisiemodus)
- **Installeren van configuratieprofielen en -certificaten** (alleen in supervisiemodus)
- **Apparaat naam wijziging** (alleen in supervisiemodus)
- **Wijziging van de wachtwoordcode** (alleen in supervisiemodus)
- **Koppelen van Apple Watch** (alleen in supervisiemodus)
- **Melding wijziging** (alleen in supervisiemodus)
- **Achtergrond wijziging** (alleen in supervisiemodus)
- **Verzending van diagnostische gegevens wijziging** (alleen in supervisiemodus)
- **Wijziging van de Bluetooth-** (alleen in supervisiemodus)
- **AirDrop** (alleen in supervisiemodus)
- **Gebruik van Siri op door gebruikers gegenereerde query-inhoud op Internet** (alleen in supervisiemodus)
- **Siri taalgebruik filter** (alleen in supervisiemodus)
- **Retourneren van resultaten op Internet in zoekopdrachten met Spotlight** (alleen in supervisiemodus)
- **Word opzoeken** (alleen in supervisiemodus)
- **Voorspeld toetsenborden** (alleen in supervisiemodus)
- **Automatische correcties** (alleen in supervisiemodus)
- **Toetsenbord spellingcontrole** (alleen in supervisiemodus)
- **Sneltoetsen** (alleen in supervisiemodus)
<!--- - **Enterprise app trust settings modification** --->
- **Installeren van apps met Apple Configurator en alleen iTunes** (alleen in supervisiemodus)
- **Automatische app downloads** (alleen in supervisiemodus)
- **Wijzigingen aanbrengen in de instellingen van de app Zoek vrienden** (alleen in supervisiemodus)
- **Toegang tot de iBooks store** (alleen in supervisiemodus)
- **App berichten** (alleen in supervisiemodus)
- **Podcasts** (alleen in supervisiemodus)
- **Apple muziek** (alleen in supervisiemodus)
- **iTunes Radio** (alleen in supervisiemodus)
- **Apple nieuws** (alleen in supervisiemodus)
- **Game Center** (alleen in supervisiemodus)
- **AirDrop behandelen als een niet-beheerde doel**

## <a name="android-for-work-support"></a>Android voor Work-ondersteuning

Vanaf Technical Preview-versie 1702, kunt u een Google-account binden aan uw hybride MDM-tenant. Hierdoor kunt u het volgende doen:

- Inschrijven [Android-apparaten ondersteund](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) als Android for Work werkprofielen aanmaken op de ingeschreven apparaten
- Goedkeuren van apps in de Play voor werk store, deze te synchroniseren met de Configuration Manager-console en vervolgens implementeren voor apparaten werkprofielen
- Maken en implementeren van configuratie-items werk profiel en het wachtwoord alleen instellingen voor deze apparaten configureren
- Maken en implementeren van naleving beleidsitems en brontoegangsprofielen voor Android voor werk apparaten als u al voor Android-apparaten
- Selectief wissen op Android voor werk apparaten uitvoeren

Wanneer u een apparaat inschrijft omdat Android for Work een work-profiel op het apparaat welke Intune maakt kunnen beheren. Deze work-profiel bestaat naast elkaar met het persoonlijk profiel op het Android-apparaat. Gebruikers kunnen eenvoudig schakelen tussen de werkzaamheden profiel apps en apps persoonlijk profiel. U kunt items in het persoonlijk profiel niet beheren. Persoonlijke apps en gegevens blijven zonder begeleiding. Configuration Manager heeft volledig beheer over de work-profiel en de inhoud ervan en van het apparaat kunt verwijderen.

Android for Work is een afzonderlijke platform van Android en moet u om te bepalen welke vorm van management om te gebruiken voor Android-apparaten die ondersteuning bieden voor werkprofielen.

### <a name="try-it-out"></a>Probeer het nu!
De volgende secties beschrijven Android voor Work-beheer.

#### <a name="enable-android-for-work-management"></a>Android voor Work-beheer inschakelen
1. Maakt een Google-account op https://accounts.google.com/SignUp als uw Android wilt gebruiken voor werk beheeraccount die gekoppeld aan alle Android voor werk beheertaken voor Intune-tenant worden. Dit kan een Google-account gedeeld door de beheerders die voor het beheren van Android-apparaten zijn. Dit is het Google-account die uw organisatie te beheren en publiceren van apps in de Play voor Work-console gebruikt. U gebruikt deze account voor het goedkeuren van apps in de Play voor werk store, dus bijhouden van de accountnaam en het wachtwoord.
2. Android-registratie inschakelen door de binding van het Google-account voor de Intune-tenant in Configuration Manager worden beheerd:
  1. Ga naar **beheer** > **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen** en selecteer uw Intune-abonnement.
  2. Klik in het lint op **Platforms configureren** > **Android** en zorg ervoor dat **Android-inschrijving inschakelen** is ingeschakeld.
  3. Klik in het lint op **Platforms configureren** > **Android for Work**.
  4. Klik in het dialoogvenster **Android configureren voor werk in de Intune-console**. De Intune-console wordt geopend in uw webbrowser.
  5. Gebruik de referenties van uw Intune-beheerder zich aanmelden bij de Intune-portal.
  6. Klik op **configureren** Android van Google Play voor werk website openen.
  7. Op Google-aanmeldingspagina, geef de referenties van de Google-account uit stap 1 en geef vervolgens de gegevens van uw bedrijf.
3. Wanneer u naar de Intune-portal terugkeert, Android for Work is ingeschakeld en hebt u drie Inschrijvingsopties voor Android voor werk apparaten:
  - **Alle apparaten beheren als Android** - (uitgeschakeld) alle Android-apparaten, inclusief apparaten die ondersteuning bieden voor Android voor werk, zal het worden ingeschreven als conventionele Android-apparaten
  - **Ondersteunde apparaten beheren als Android for Work** - (ingeschakeld) alle apparaten die ondersteuning bieden voor Android for Work als Android voor werk apparaten zijn ingeschreven. Een Android-apparaat dat biedt geen ondersteuning voor Android for Work is als een conventionele Android-apparaat ingeschreven.
  - **Ondersteunde apparaten voor gebruikers die alleen in deze groepen beheren als Android for Work** -(Testing) kunt u Android doel voor werkstroombeheer voor een beperkt aantal gebruikers. Alleen leden van de geselecteerde groepen die een apparaat inschrijft dat biedt ondersteuning voor Android for Work worden geregistreerd als Android voor Work-apparaten. Alle andere gebruikers worden als Android-apparaten geregistreerd.
  
> [!NOTE]
> Een bekend probleem dat voorkomt dat de **beheren ondersteunde apparaten voor gebruikers die alleen in deze groepen als Android for Work** optie niet werkt zoals verwacht. Apparaten van gebruikers in de opgegeven Azure AD-groepen als Android in plaats van Android for Work zal inschrijven. Als u wilt testen op Android for Work, moet u de **alle ondersteunde apparaten beheren als Android for Work**.


  Om in te schakelen Android voor de inschrijving van het werk, moet u een van de opties onder twee. De **beheren ondersteunde apparaten voor gebruikers die alleen in deze groepen als Android for Work** optie vereist dat u hebt Azure Active Directory-beveiligingsgroepen instellen.

Ziet u de accountnaam en de naam van de organisatie in de Intune-portal als de binding voltooid is. op dat moment kunt u beide browsers sluiten.

#### <a name="approve-and-deploy-android-for-work-apps"></a>Goedkeuren en implementeren van Android voor bedrijfs-apps
Volg deze stappen apps in de Play voor werk store goedkeuren en implementeren voor beheerde Android voor werk apparaten ze naar de Configuration Manager-console synchroniseren. Voor apps op het werk gebruikersprofielen implementeert, moet u voor het goedkeuren van de apps in de Play voor werk en vervolgens de apps met de Configuration Manager-console te synchroniseren.

1. Open een browser en Ga naar: https://play.google.com/work.
2. Meld u aan met het Google-admin-account afhankelijk van uw Intune-tenant.
3. Apps die u wilt implementeren in uw omgeving en klik op Bladeren **goedkeuren** voor elk van deze.
4. Ga in de Configuration Manager-console naar **beheerder** > **overzicht** > **Cloudservices** > **Android for Work** en klik op **Sync**.
5. Wacht tot maximaal 10 minuten om apps te synchroniseren en ga vervolgens **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **licentiegegevens voor Store-Apps**.
6. Klik op een app die vanuit Play for Work zijn gesynchroniseerd en klik vervolgens op **toepassing maken**.
7. Voltooi de wizard en klikt u op **sluiten**.
8. Ga naar **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**, selecteert u een Android voor zakelijke apps en gewoon implementeren.

Als u wilt synchroniseren Play voor zakelijke apps met Configuration Manager, moet u ten minste één app in de Play voor werk website goedkeuren.

#### <a name="enroll-an-android-for-work-device"></a>Een Android voor Work-apparaat inschrijven
Hoe het inschrijven van Android voor werk apparaten is vergelijkbaar met inschrijving voor Android. Downloaden en uitvoeren van de bedrijfsportal-app voor Android op je mobiele apparaat. U wordt gevraagd een werk-profiel maken als onderdeel van het registratieproces.  Zodra de work-profiel is gemaakt, moet u overschakelen naar de beheerde versie van de bedrijfsportal. De beheerde bedrijfsportal is gemarkeerd met een klein oranje werkmap in de rechterbenedenhoek.

#### <a name="create-and-deploy-a-configuration-item"></a>Maken en implementeren van een configuratie-item
Android for Work heeft twee instellingsgroepen voor configuratie-items:
- Wachtwoord
- Work-profiel

U kunt inhoud delen tussen de werkzaamheden profielen, evenals de volgende configuratie-items op apparaten met Android 6 of hoger configureren:
- Het gedrag voor apps voor specifieke machtigingen gevraagd
- Hiermee wordt aangegeven of meldingen voor toepassingen binnen het profiel werk zijn zichtbaar op het vergrendelingsscherm

Probeer een configuratie-item via de standaard werkstroom maakt, kiest u **Android for Work** op de **algemene** pagina en configureer instellingen voor elk van de instellingsgroepen voor het configuratie-item toevoegen aan een basislijn en gewoon implementeren. Deze instellingen worden alleen op apparaten die worden ingeschreven als Android voor werk, en niet de geregistreerd als Android toegepast.

#### <a name="perform-selective-wipe"></a>U selectief wissen
Apparaten die zijn geregistreerd als Android for Work alleen selectief kan worden gewist omdat u alleen de work-profiel beheren. Dit voorkomt dat het persoonlijk profiel wordt gewist. Uitvoeren van een selectief wissen op een Android voor werk apparaat verwijdert u het profiel voor werk, met inbegrip van alle apps en gegevens, en het apparaat wordt uitgeschreven.

Voor het selectief wissen van een Android voor Work-apparaat, gebruikt u de normale [selectief gewist](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe) in de Configuration Manager-console.

#### <a name="known-issues-for-android-for-work"></a>Bekende problemen voor Android for Work.
**Synchronisatie configureren ze te plannen in Android voor werk e-mailprofielen oorzaken mislukt voor het implementeren van** een van de opties in de ConfigMgr-UI voor Android voor werk-e-mailprofielen is 'Schema'. Hierdoor kan de beheerder een planning voor het synchroniseren van e-mail en andere gegevens van de account e-mailbericht naar de mobiele apparaten, die dit wordt geïmplementeerd voor configureren op andere platforms. Echter, werkt niet voor Android voor werk-e-mailprofielen en als u een optie dan 'Niet geconfigureerd' kiest, wordt het profiel niet worden geïmplementeerd voor alle apparaten.
