---
title: Maken en implementeren van een nalevingsbeleid voor apparaten
titleSuffix: Configuration Manager
description: Informatie over het maken en implementeren van beleid voor apparaatcompatibiliteit in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fd76043-d7ee-423d-8c5f-aa7e9ed58ce0
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
robots: noindex
ms.openlocfilehash: bf0099cdf4df1b7421a257e910c8682e63f8ee1e
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-and-deploy-a-device-compliance-policy"></a>Maken en implementeren van een nalevingsbeleid voor apparaten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="create-a-compliance-policy"></a>Een nalevingsbeleid maken

1.  Kies in de System Center Configuration Manager-console **activa en naleving**.

2.  In de **activa en naleving** werkruimte Vouw **instellingen voor naleving**, en kies vervolgens **nalevingsbeleid**.

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **nalevingsbeleid maken**.

4.  Op de **algemene** pagina van de Wizard nalevingsbeleid maken, geeft u de volgende informatie:

  * **Naam**. Voer een unieke naam in voor het nalevingsbeleid. U kunt maximaal 256 tekens gebruiken.

  * **Beschrijving**. Voer een beschrijving die een overzicht van het VPN-profiel en kan geïdentificeerd in de Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.

  * **Type nalevingsbeleid**. Selecteer het type beleid dat u maken wilt, afhankelijk van of het apparaat wordt beheerd door Configuration Manager. Dit geldt voor versie of later.<br /><br /> Kies de optie **Nalevingsegels voor apparaten die worden beheerd zonder Configuration Manager-client** voor apparaten die worden beheerd door Intune. Wanneer u deze optie selecteert, kunt u ook het type platform dat u wilt dat dit beleid wilt toepassen.

  * **Niet-nageleefd ernst voor rapporten**. Geef de ernst aan die wordt gerapporteerd als wordt vastgesteld dat het nalevingsbeleid niet compatibel is. U kunt kiezen uit de volgende ernstniveaus:

     * **Geen**. Apparaten die niet voldoen aan deze compliantieregel wordt de ernst voor rapporten van Configuration Manager niet rapporteren.
     * **Informatie**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.   
     * **Waarschuwing**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.
     * **Kritieke**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **Kritiek** voor Configuration Manager-rapporten.
     * **Kritiek met gebeurtenis**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **Kritiek** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.      

5.  Op de **ondersteunde Platforms** pagina, kiest u de apparaatplatforms waarop dit nalevingsbeleid wordt geëvalueerd of kies **Alles selecteren** om alle apparaatplatforms te kiezen. De ondersteunde platforms zijn: Windows 7, Windows 8.1 en Windows 10; Windows Server 2008 R2, WindowsServer 2012, Windows Server 2012 R2 en WindowsServer 2016.

6.  Op de pagina **Regels** definieert u een of meer regels die de configuratie bepalen die apparaten moeten hebben om als compatibel te worden beoordeeld. Wanneer u nalevingsbeleid maakt, worden bepaalde regels standaard ingeschakeld, maar u kunt deze bewerken of verwijderen. Zie de sectie 'Beleidsregels voor naleving' verderop in dit onderwerp voor een volledige lijst met alle regels.

  > [!NOTE]  
  >  Op Windows-pc's wordt Windows-versie van besturingssysteem 8.1 gerapporteerd als 6.3 in plaats van 8.1. Als de besturingssysteemversieregel is ingesteld op Windows 8.1 voor Windows, klikt u vervolgens het apparaat gerapporteerd als niet-compatibel zelfs als het apparaat Windows 8.1 heeft. Zorg ervoor dat u bij het instellen van het recht *gerapporteerd* versie van Windows voor de minimale en maximale OS-regels. Het versienummer moet overeenkomen met de versie die de **winver** opdracht retourneert. Windows Phone-telefoons hebben dit probleem niet. De versie wordt zoals verwacht gerapporteerd als 8.1. Voor Windows-pc's met het Windows 10-besturingssysteem, de versie moet worden ingesteld als **10.0** plus de OS-build die de **winver** opdracht retourneert.

7.  Op de **samenvatting** pagina Controleer de instellingen die u hebt gemaakt van de wizard en voltooi de wizard.

 Het nieuwe beleid wordt weergegeven in de **nalevingsbeleid** knooppunt van de **activa en naleving** werkruimte.

## <a name="deploy-a-compliance-policy"></a>Een nalevingsbeleid implementeren

1.  Kies in de Configuration Manager-console **activa en naleving**.

2.  In de **activa en naleving** werkruimte Vouw **instellingen voor naleving**, en kies vervolgens **nalevingsbeleid**.

3.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **implementeren**.

4.  In de **nalevingsbeleid implementeren** dialoogvenster Kies **Bladeren** selecteren van de Gebruikersverzameling waarop het beleid te implementeren.

     Bovendien kunt u opties waarschuwingen worden gegenereerd wanneer het beleid is niet compatibel met en het instellen van de planning waarmee dit beleid wordt beoordeeld op naleving.

5.  Als u klaar bent, kiest u **OK**.

## <a name="monitor-the-compliance-policy"></a>Het nalevingsbeleid bewaken

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Nalevingsresultaten weergeven in de Configuration Manager-console

1.  Kies in de Configuration Manager-console **bewaking**.

2.  In de **bewaking** werkruimte, kiest u **implementaties**.

3.  Selecteer het nalevingsbeleid waarvan u de nalevingsgegevens wilt controleren in de lijst **Implementaties** .

4.  Op de hoofdpagina kunt u samenvattingsinformatie over de naleving van de beleidsimplementatie controleren. Meer gedetailleerde informatie weergeven, selecteert u de implementatie en klik vervolgens op de **Start** tabblad, in de **implementatie** groep, kiest u **Status weergeven** openen de **Implementatiestatus** pagina.

    De **Implementatiestatus** pagina heeft de volgende tabbladen:

    -   **Compatibele**. Geeft de naleving van het beleid op basis van het aantal betrokken activa. U kunt een regel voor het maken van een tijdelijk knooppunt onder de **gebruikers** of **apparaten** knooppunt van de **activa en naleving** werkruimte, die alle gebruikers of apparaten die aan deze regel voldoen bevat. De **activumgegevens** deelvenster geeft de gebruikers of apparaten die aan het beleid voldoen. Dubbelklik op een gebruiker of apparaat in de lijst om extra informatie te geven.

    -   **Fout**. Geeft een lijst weer met alle fouten voor de geselecteerde Beleidsimplementatie op basis van het aantal betrokken activa. U kunt een regel voor het maken van een tijdelijk knooppunt onder de **gebruikers** of **apparaten** knooppunt van de **activa en naleving** werkruimte, die alle gebruikers of apparaten bevat die fouten met deze regel genereerden. Wanneer u een gebruiker of apparaat, selecteert de **activumgegevens** deelvenster geeft de gebruikers of apparaten die een probleem ondervindt. Dubbelklik op een gebruiker of apparaat in de lijst om aanvullende informatie over het probleem weergeven.

    -   **Niet-compatibele**. Geeft een lijst weer met alle niet-compatibele regels binnen het beleid, op basis van het aantal betrokken activa. U kunt een regel voor het maken van een tijdelijk knooppunt onder de **gebruikers** of **apparaten** knooppunt van de **activa en naleving** werkruimte, die alle gebruikers of apparaten bevat die niet aan deze regel voldoen. Wanneer u een gebruiker of apparaat, selecteert de **activumgegevens** deelvenster geeft de gebruikers of apparaten die een probleem ondervindt. Dubbelklik op een gebruiker of apparaat in de lijst om verdere informatie over het probleem weergeven.

    -   **Onbekende**. Bevat een overzicht van alle gebruikers en apparaten die geen compatibiliteitsstatus is gerapporteerd voor de implementatie van het geselecteerde beleid, samen met de huidige clientstatus van apparaten.

#### <a name="to-monitor-the-compliance-status-of-an-individual-device"></a>Voor het bewaken van de status van naleving van een afzonderlijk apparaat

1.  Kies in de Configuration Manager-console de **activa en naleving** werkruimte.

2.  Kies **apparaten**.

3.  Met de rechtermuisknop op een van de kolommen om in te schakelen meer kolommen.

  U kunt de volgende kolommen toevoegen:

  - **Apparaat-ID van Azure Active Directory**.  De unieke id voor het apparaat in Azure Active Directory.

  - **Details van compatibiliteit fout**.  Details van foutbericht wanneer de end-to-end-proces mis gaat. Als u deze kolom leeg is, betekent dit zijn geen fouten gevonden en wordt de status van naleving met succes is gerapporteerd.

  - **Naleving Foutlocatie**.  Meer informatie over waar de compatibiliteit is mislukt. Als u deze kolom leeg is, betekent dit zijn geen fouten gevonden en wordt de status van naleving met succes is gerapporteerd. Voorbeelden van waar de nalevingsproces mislukken: 
      - ConfigMgr-Client
      - Beheerpunt
      - Intune
      - Azure Active Directory
<br></br>
  - **Naleving evaluatietijd**. Laatste keer dat de compatibiliteit is gecontroleerd.

  - **Naleving tijd instellen**. Laatste keer dat de compatibiliteit is bijgewerkt naar Azure Active Directory.

  - **Voorwaardelijke toegang compatibele**.  Of de computer voldoet aan beleidsregels voor voorwaardelijke toegang.

  > [!IMPORTANT]
  > Deze kolommen worden niet standaard weergegeven.

#### <a name="to-view-intune-compliance-policies-charts"></a>Grafieken om weer te geven van de Intune-nalevingsbeleid
1. Vanaf versie 1610 van Configuration Manager in de Configuration Manager-console, kies **bewaking**.

2. In de **bewaking** werkruimte, gaat u naar **overzicht** > **instellingen voor naleving** > **nalevingsbeleid**.

   De volgende grafieken weergegeven:

    - **Algemene apparaatcompatibiliteit**. Toont de algemene compatibiliteit van apparaten voor alle beleidsregels voor naleving.
    - **Belangrijkste redenen voor niet-naleving**. Toont de belangrijkste beleidsregels voor welke apparaten niet compatibel zijn.

3. Kies een sectie in een grafiek om een lijst van de apparaten in die categorie.

#### <a name="to-view-a-health-attestation-report"></a>Een health attestation-rapport weergeven

1.  Vanaf versie 1602 van Configuration Manager in de Configuration Manager-console, kies **bewaking**.

2.  U kunt een overzichtsrapport van de huidige status van apparaten op nalevingssstatus bekijken **beveiliging**, en kies vervolgens **Health Attestation**.

3.  U kunt een rapport met een lijst met alle apparaten en alle health attestation-kenmerken bekijken **beveiliging**, en kies vervolgens **Health Attestation**.

## <a name="compliance-policy-rules"></a>Beleidsregels voor naleving
* **Wachtwoordinstellingen vereisen op mobiele apparaten**. U kunt vereisen dat gebruikers een wachtwoord moeten invoeren om toegang te krijgen hun apparaat tot.

  **Ondersteund op:**
    * Windows Phone 8+
    * iOS 6+
    * Android 4.0+
    * Samsung KNOX Standard 4.0+

* **Wachtwoord vereisen voor het ontgrendelen van een inactief apparaat** (1602-update). U kunt vereisen dat gebruikers een wachtwoord invoeren voor toegang tot een apparaat dat is vergrendeld.

  **Ondersteund op:**
  * Windows Phone 8+
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Minuten van inactiviteit voordat wachtwoord vereist is** (1602-update). U kunt opgeven dat de niet-actieve tijd voordat de gebruiker het wachtwoord moet invoeren. De waarde ingesteld op een van de beschikbare opties: **1 minute**, **5 minutes**, **15 minutes**, **30 minutes**, **1 hour**.

  Deze regel moet worden gebruikt met **wachtwoord vereisen voor een inactief apparaat te ontgrendelen**. De hier ingestelde waarde bepaalt wanneer het apparaat wordt beschouwd als niet-actief en wordt vergrendeld. Wanneer **wachtwoord vereisen voor een inactief apparaat te ontgrendelen** is ingesteld op **True**, de gebruiker moet een wachtwoord invoeren voor toegang tot het vergrendelde apparaat.

  **Ondersteund op:**
  * Windows Phone 8+
  * Windows RT/8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Automatische updates vereisen** (1602-update). U kunt apparaten met Windows 8.1 of hoger vereisen dat updates automatisch worden geïnstalleerd en u kunt de updateklasse opgeven.

  De waarde moet worden ingesteld op **geen** om te voorkomen dat automatische installatie tot **aanbevolen** automatisch alle aanbevolen updates worden geïnstalleerd of **belangrijk** om alleen de updates die zijn geclassificeerd als belangrijk te installeren.

  **Ondersteund op:**
  * Windows Phone 8+

* **Eenvoudige wachtwoorden toestaan**. U kunt gebruikers eenvoudige wachtwoorden, zoals '1234' of "1111." Deze instelling is standaard uitgeschakeld.

  **Ondersteund op:**
  * Windows Phone 8+
  * iOS 6+

* **Minimale wachtwoordlengte**. U kunt opgeven dat het minimale aantal cijfers of tekens aan dat het wachtwoord van de gebruiker (6 standaard) moet hebben.

  **Ondersteund op:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

  >[!NOTE]
  >Voor apparaten die Windows uitvoeren en worden beveiligd met een Microsoft-account, het nalevingsbeleid geen goede controles worden uitgevoerd als **minimale wachtwoordlengte** groter is dan 8 tekens of als **minimumaantal tekensets** is meer dan 2.

* **Bestandsversleuteling op mobiel apparaat**. U kunt het apparaat worden versleuteld om verbinding met bronnen vereisen. Apparaten met Windows Phone 8 worden automatisch versleuteld. Apparaten met iOS worden versleuteld wanneer u de instelling **Wachtwoordinstellingen vereisen voor mobiele apparaten**configureert. Deze instelling is standaard ingeschakeld.

  **Ondersteund op:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Apparaat mag niet gekraakt of geroot**. Als u deze instelling inschakelt, die voldoen opengebroken (iOS) of geroote (Android) apparaten niet compatibel zijn. Deze instelling is standaard uitgeschakeld.

  **Ondersteund op:**
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **E-mailprofiel moet worden beheerd door Intune**. Als u deze optie instelt op **Ja**, het e-mailprofiel dat is geïmplementeerd op het apparaat moet worden gebruikt door het apparaat. Het apparaat wordt als niet-compatibel beschouwd als het e-mailprofiel niet in dezelfde gebruikersgroep wordt geïmplementeerd als de doelgroep waarop het nalevingsbeleid is gericht.

  Het apparaat wordt ook als niet-compatibel beschouwd als de gebruiker al een e-mailaccount op het apparaat heeft ingesteld dat overeenkomt met het Intune-e-mailprofiel dat op het apparaat is geïmplementeerd. In dit geval kan Intune het door de gebruiker ingerichte profiel niet overschrijven en kan het daarom niet beheren. De gebruiker kan het apparaat onder naleving brengen door het verwijderen van de bestaande e-mailinstellingen waarmee Intune het beheerde e-mailprofiel installeren.

  Zie [Toegang tot zakelijke e-mail inschakelen met behulp van e-mailprofielen en Microsoft Intune](https://technet.microsoft.com/library/dn800672.aspx)voor meer informatie over e-mailprofielen. Deze instelling is standaard uitgeschakeld.

  **Ondersteund op:**
  * iOS 6+

* **E-mailprofiel**. Als **e-mailaccount moet worden beheerd door Intune** is geselecteerd, kiest u **Selecteer** de e-mailprofiel dat apparaten moeten worden beheerd door te kiezen. Het e-mailprofiel moet aanwezig zijn op het apparaat.

  **Ondersteund op:**
  * iOS 6+

* **Minimale OS vereist**. Wanneer een apparaat niet aan de minimum versievereisten voor OS die u opgeeft voldoet, wordt het gerapporteerd als niet-compatibel. Een koppeling met informatie over het bijwerken wordt weergegeven. De gebruiker kan kiezen om bij te werken van hun apparaat, waarna ze zich voor toegang tot bedrijfsbronnen.

  **Ondersteund op:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Maximale versie van besturingssysteem toegestaan**. Wanneer een apparaat een versie van het besturingssysteem hoger is dan die u in de regel opgeeft gebruikt, wordt toegang tot bedrijfsbronnen geblokkeerd en wordt de gebruiker gevraagd contact opnemen met hun IT-beheerder. Totdat u de regel voor het toestaan van de versie van het besturingssysteem wijzigt, kan dit apparaat niet worden gebruikt voor toegang tot bedrijfsresources.

  **Ondersteund op:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Vereisen dat apparaten worden gerapporteerd als goed** (1602-update). U kunt een regel instellen om te vereisen dat Windows 10-apparaten moeten worden gerapporteerd als goed in een nieuw of bestaand nalevingsbeleid. Als u deze instelling inschakelt, worden Windows 10-apparaten via de Health Attestation Service (HAS) voor de volgende gegevenspunten beoordeeld:

  - **BitLocker is ingeschakeld**. Als BitLocker ingeschakeld is, kan het apparaat gegevens die zijn opgeslagen op het station tegen onbevoegde toegang wanneer het systeem is uitgeschakeld of naar de slaapstand overschakelt kunt beveiligen.

   Windows BitLocker-stationsversleuteling versleutelt alle gegevens die zijn opgeslagen op het Windows-besturingssysteemvolume. BitLocker gebruikt de TPM om het Windows-besturingssysteem en de gebruikersgegevens te beveiligen. Het helpt om ervoor te zorgen dat een computer wordt geknoeid, zelfs niet als deze zonder toezicht, verloren of gestolen.
   
   Als de computer is uitgerust met een compatibele TPM, gebruikt BitLocker de TPM om de versleutelingssleutels die de gegevens beveiligen te vergrendelen. Als gevolg hiervan zijn de sleutels niet toegankelijk totdat de TPM de status van de computer heeft gecontroleerd.

  - **Code-integriteit is ingeschakeld**. Code-integriteit is een functie die de integriteit van een stuurprogramma of systeembestand valideert telkens wanneer dit in het geheugen wordt geladen. Code-integriteit detecteert of een niet-ondertekend stuurprogramma of systeembestand-bestand in de kernel wordt geladen. Daarnaast wordt gedetecteerd of een systeembestand is gewijzigd door schadelijke software die wordt uitgevoerd door een gebruikersaccount met beheerdersbevoegdheden.

  - **Beveiligd opstarten is ingeschakeld**. Als beveiligd opstarten is ingeschakeld, wordt het systeem geforceerd te starten in een vertrouwde fabrieksstatus. Als beveiligd opstarten is ingeschakeld, moeten de kernonderdelen die worden gebruikt om de machine te starten moeten ook juiste cryptografische handtekeningen die worden vertrouwd door de organisatie die het apparaat heeft geproduceerd. De UEFI-firmware verifieert dit voordat de machine wordt opgestart. Als er bestanden zijn gemanipuleerd, waardoor de handtekening wordt verbroken het systeem niet gestart.

  - **Early launch antimalware is ingeschakeld**. Deze instelling geldt alleen voor pc's. Early Launch Antimalware (ELAM) biedt beveiliging voor de computers in uw netwerk wanneer deze worden opgestart en voordat stuurprogramma's van derden worden geïnitialiseerd.
  
   Deze regel is standaard uitgeschakeld.

  Zie [Health Attestation CSP](https://msdn.microsoft.com/library/dn934876.aspx)(Engelstalig) voor meer informatie over de werking van de HAS-service.

  **Ondersteund op:**
  * Windows 10 en Windows 10 Mobile

- **Apps die niet kunnen worden geïnstalleerd op het apparaat**. Als gebruikers een app uit de lijst admin niet-compatibele apps installeren, moeten deze worden geblokkeerd wanneer ze proberen toegang tot zakelijke e-mail en andere bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang. Deze regel moet de appnaam van de en de app-ID wanneer een app toe te voegen aan de lijst met niet-compatibele gedefinieerd door de beheerder. De uitgever van de app kan ook worden toegevoegd, maar dit is niet vereist.

    **Ondersteund op:**
      * iOS 6+
      * Android 4.0+
      * Samsung KNOX Standard 4.0+
<br></br>
* **Vereist Wachtwoordtype**. Geef op of de gebruiker een alfanumeriek wachtwoord of een numerieke wachtwoord moet maken. Voor alfanumerieke wachtwoorden, moet u ook het minimum aantal tekensets opgegeven waaruit het wachtwoord moet opgeven. De vier tekensets zijn: Kleine letters, hoofdletters, symbolen en cijfers.

    **Ondersteund op:**
    * Windows Phone 8+
    * Windows 8.1 +
    * iOS 6+
<br></br>
* **Blok USB-foutopsporing op apparaat**. U beschikt niet over deze instellingen configureren, zoals USB-foutopsporing is al uitgeschakeld op Android voor Work-apparaten.

    **Ondersteund op:**
    * Android 4.0+
    * Samsung KNOX Standard 4.0+
<br></br>
* **Blokkeren van apps van onbekende bronnen**. Vereisen dat de installatie van apps van onbekende bronnen worden voorkomen. U beschikt niet over deze instelling wilt configureren als Android voor werk apparaten altijd installatie vanuit onbekende bronnen beperken.

    **Ondersteund op:**
    * Android 4.0+
    * Samsung KNOX Standard 4.0+
<br></br>
* **Threat moeten worden gescand op apps**. Deze instelling geeft aan dat de functie van de apps controleren is ingeschakeld op het apparaat. 

    **Ondersteund op:**
    * Android 4.2 via 4.4
    * Samsung KNOX Standard 4.0+

### <a name="find-an-app-id"></a>Een app-ID vinden

Een app-ID is een id die een unieke identificatie van de app in de Apple en Google toepassingsservices. Een voorbeeld is com.contoso.myapp. Te zoeken:

- **Android**
    - U vindt de app-ID in de Google Play-URL die is gebruikt voor het maken van de app opslaan. Een voorbeeld-app-ID is: *...? id=com.companyname.appname & hl = nl*

- **iOS**
    1. Opslaan in de iTunes URL, zoek het id-nummer, zoals in dit voorbeeld: */id875948587? mt = 8*

    2. In een webbrowser, gaat u naar de volgende URL en het aantal vervangen door de id die u zojuist hebt gevonden (in dit geval het vorige voorbeeld): https://itunes.apple.com/lookup?id=875948587

    3. Download en open het tekstbestand.
  
    4. Zoek de tekst **bundel-id**.

    Een voorbeeld-app-ID is: "*bundel-id*": "*com.companyname.appname*' 

