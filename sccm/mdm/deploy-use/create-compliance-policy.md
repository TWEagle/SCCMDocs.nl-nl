---
title: Maken en implementeren van een nalevingsbeleid voor apparaten | Microsoft-documenten
description: Informatie over het maken en implementeren in System Center Configuration Manager nalevingsbeleid voor apparaten.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fd76043-d7ee-423d-8c5f-aa7e9ed58ce0
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
robots: noindex
ms.translationtype: Machine Translation
ms.sourcegitcommit: 216d288aa7b7f2b98df86f59355d879366dcd44d
ms.openlocfilehash: 4baa6e0fe009f5f7dc33f5ab4adb1ec5e5c5271b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="create-and-deploy-a-device-compliance-policy"></a>Maken en implementeren van een nalevingsbeleid voor apparaten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="create-a-compliance-policy"></a>Een nalevingsbeleid maken

1.  Kies in de System Center Configuration Manager-console **activa en naleving**.

2.  In de **activa en naleving** werkruimte Vouw **compatibiliteitsinstellingen**, en kies vervolgens **nalevingsbeleid**.

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **nalevingsbeleid maken**.

4.  Op de **algemeen** pagina van de Wizard compatibiliteit beleid maken de volgende informatie opgeven:

  * **Naam**. Voer een unieke naam in voor het nalevingsbeleid. U kunt maximaal 256 tekens gebruiken.

  * **Beschrijving**. Voer een beschrijving op die een overzicht biedt van het VPN-profiel en helpt u identificeren in de Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.

  * **Type nalevingsbeleid**. Selecteer het type van het beleid dat u maken wilt, afhankelijk van of het apparaat wordt beheerd door Configuration Manager. Dit is van toepassing op versie of later.<br /><br /> Kies de optie **Nalevingsegels voor apparaten die worden beheerd zonder Configuration Manager-client** voor apparaten die worden beheerd door Intune. Wanneer u deze optie selecteert, kunt u ook het type van het platform dat u wilt dat dit beleid toepassen om te selecteren.

  * **Ernst van niet-compatibele voor rapporten**. Geef de ernst aan die wordt gerapporteerd als wordt vastgesteld dat het nalevingsbeleid niet compatibel is. U kunt kiezen uit de volgende ernstniveaus:

     * **Geen**. Apparaten die niet voldoen aan deze compliantieregel doen geen fouternst voor Configuration Manager-rapporten.
     * **Informatie**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.   
     * **Waarschuwing**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.
     * **Kritieke**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.
     * **Kritiek met gebeurtenis**. Apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.      

5.  Op de **ondersteunde Platforms** pagina, kiest u de apparaatplatforms die dit nalevingsbeleid zal worden geëvalueerd op of kies **Alles selecteren** kiezen alle platforms. De ondersteunde platforms zijn: Windows 7, Windows 8.1 en Windows 10; Windows Server 2008 R2, WindowsServer 2012, Windows Server 2012 R2 en WindowsServer 2016.

6.  Op de pagina **Regels** definieert u een of meer regels die de configuratie bepalen die apparaten moeten hebben om als compatibel te worden beoordeeld. Wanneer u nalevingsbeleid maakt, worden bepaalde regels standaard ingeschakeld, maar u kunt deze bewerken of verwijderen. Zie de sectie "Compatibiliteit beleidsregels" verderop in dit onderwerp voor een volledige lijst van alle regels.

  > [!NOTE]  
  >  Op Windows-pc's, Windows versie 8.1 gerapporteerd als 6.3 in plaats van 8.1. Als de regel OS-versie is ingesteld op Windows 8.1 voor Windows, klikt u vervolgens het apparaat gerapporteerd als niet-compatibele zelfs als het apparaat heeft Windows 8.1. Zorg ervoor dat u bij het instellen van het recht *gerapporteerd* versie van Windows voor de minimale en maximale OS-regels. Het versienummer moet overeenkomen met de versie die de **winver** opdracht geeft. Windows Phone-telefoons hebben dit probleem niet. De versie wordt zoals verwacht gerapporteerd als 8.1. Voor Windows-pc's met het Windows-10-besturingssysteem, de versie moet worden ingesteld als **10.0** plus de OS-build die de **winver** opdracht geeft.

7.  Op de **samenvatting** pagina van de wizard, Controleer de instellingen die u hebt gemaakt en vervolgens de wizard hebt voltooid.

 Het nieuwe beleid wordt weergegeven in de **nalevingsbeleid** knooppunt van de **activa en naleving** werkruimte.

## <a name="deploy-a-compliance-policy"></a>Een nalevingsbeleid implementeren

1.  Kies in de Configuration Manager-console **activa en naleving**.

2.  In de **activa en naleving** werkruimte Vouw **compatibiliteitsinstellingen**, en kies vervolgens **nalevingsbeleid**.

3.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **implementeren**.

4.  In de **nalevingsbeleid implementeren** dialoogvenster Kies **Bladeren** om de Gebruikersverzameling waarop het beleid implementeren te selecteren.

     Daarnaast kunt u opties voor waarschuwingen worden gegenereerd wanneer het beleid is niet compatibel en de planning waarop dit beleid worden geëvalueerd op compatibiliteit moet worden ingesteld.

5.  Als u klaar bent, kiest u **OK**.

## <a name="monitor-the-compliance-policy"></a>Het nalevingsbeleid bewaken

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Nalevingsresultaten weergeven in de Configuration Manager-console

1.  Kies in de Configuration Manager-console **bewaking**.

2.  In de **bewaking** werkruimte kiezen **implementaties**.

3.  Selecteer het nalevingsbeleid waarvan u de nalevingsgegevens wilt controleren in de lijst **Implementaties** .

4.  Op de hoofdpagina kunt u samenvattingsinformatie over de naleving van de beleidsimplementatie controleren. Meer gedetailleerde informatie weergeven, selecteert u de implementatie en klikt u op de **Start** tabblad, in de **implementatie** groep, kiest u **Status weergeven** openen de **Implementatiestatus** pagina.

    De **Implementatiestatus** pagina heeft de volgende tabbladen:

    -   **Compatibel**. Geeft de naleving van het beleid op basis van het aantal beïnvloede activa. U kunt een regel voor het maken van een tijdelijk knooppunt onder de **gebruikers** of **apparaten** knooppunt van de **activa en naleving** werkruimte, die alle gebruikers of apparaten die voldoen aan deze regel bevat. De **activumgegevens** deelvenster worden weergegeven voor gebruikers of apparaten die voldoen aan het beleid. Dubbelklik op een gebruiker of het apparaat in de lijst om extra informatie te geven.

    -   **Fout**. Bevat een lijst met alle fouten voor de implementatie van het geselecteerde beleid op basis van het aantal beïnvloede activa. U kunt een regel voor het maken van een tijdelijk knooppunt onder de **gebruikers** of **apparaten** knooppunt van de **activa en naleving** werkruimte, die alle gebruikers of apparaten die fouten met deze regel genereerden bevat. Wanneer u een gebruiker of apparaat, selecteert de **activumgegevens** deelvenster worden weergegeven voor gebruikers of apparaten die gevolgen heeft voor een probleem. Dubbelklik op een gebruiker of het apparaat in de lijst om aan te geven als u meer informatie over het probleem.

    -   **Niet-compatibele**. Bevat een lijst met alle niet-compatibele regels weer binnen het beleid, op basis van het aantal beïnvloede activa. U kunt een regel voor het maken van een tijdelijk knooppunt onder de **gebruikers** of **apparaten** knooppunt van de **activa en naleving** werkruimte, die alle gebruikers of apparaten die niet aan deze regel voldoen bevat. Wanneer u een gebruiker of apparaat, selecteert de **activumgegevens** deelvenster worden weergegeven voor gebruikers of apparaten die gevolgen heeft voor een probleem. Dubbelklik op een gebruiker of het apparaat in de lijst voor meer informatie over het probleem weergeven.

    -   **Onbekende**. Bevat een lijst van alle gebruikers en apparaten die geen compatibiliteitsstatus is gerapporteerd voor de implementatie van het geselecteerde beleid samen met de huidige clientstatus van apparaten.

#### <a name="to-monitor-the-compliance-status-of-an-individual-device"></a>Voor het bewaken van de compatibiliteitsstatus van een bepaald apparaat

1.  Kies in de Configuration Manager-console de **activa en naleving** werkruimte.

2.  Kies **apparaten**.

3.  Met de rechtermuisknop op een van de kolommen waarmee meer kolommen.

  U kunt de volgende kolommen toevoegen:

  - **Azure Active Directory apparaat-ID**.  De unieke id voor het apparaat in Azure Active Directory.

  - **Compatibiliteit foutdetails**.  Details van foutbericht wanneer het proces end-to-end verkeerd gaat. Als deze kolom leeg is, betekent dat er geen fouten zijn gevonden en de compatibiliteitsstatus is gemeld.

  - **Compatibiliteit Foutlocatie**.  Meer informatie over waar de compatibiliteit is mislukt. Als deze kolom leeg is, betekent dat er geen fouten zijn gevonden en de compatibiliteitsstatus is gemeld. Voorbeelden van waar de nalevingsproces mislukken: 
      - ConfigMgr-Client
      - Beheerpunt
      - Intune
      - Azure Active Directory
<br></br>
  - **Compatibiliteit evaluatietijd**. Laatste keer dat de compatibiliteit is gecontroleerd.

  - **Compatibiliteit tijd instellen**. Laatste keer dat de compatibiliteit is bijgewerkt naar Azure Active Directory.

  - **Voorwaardelijke toegang compatibel**.  Of de computer voldoet aan beleidsregels voor voorwaardelijke toegang.

  > [!IMPORTANT]
  > Deze kolommen worden niet standaard weergegeven.

#### <a name="to-view-intune-compliance-policies-charts"></a>Grafieken nalevingsbeleid Intune weergeven
1. Vanaf versie 1610 van Configuration Manager in de Configuration Manager-console, kies **bewaking**.

2. In de **bewaking** werkruimte, Ga naar **overzicht** > **compatibiliteitsinstellingen** > **nalevingsbeleid**.

   De volgende grafieken weergegeven:

    - **Algemene apparaatcompatibiliteit**. Geeft de algemene compatibiliteit van apparaten voor alle nalevingsbeleid.
    - **Top Non-compatibiliteit redenen**. Geeft de bovenste beleidsregels voor welke apparaten niet-compatibel zijn.

3. Kies een sectie in de grafiek te zoomen op een lijst van de apparaten in die categorie.

#### <a name="to-view-a-health-attestation-report"></a>Een statusrapport attestation weergeven

1.  Vanaf versie 1602 van Configuration Manager in de Configuration Manager-console, kies **bewaking**.

2.  U kunt een overzichtsrapport van de huidige status van apparaten door de status van de Updatevereisten bekijken **beveiliging**, en kies vervolgens **Health Attestation**.

3.  U kunt een rapport met een lijst met alle apparaten en de kenmerken voor de attestation-status bekijken **beveiliging**, en kies vervolgens **Health Attestation**.

## <a name="compliance-policy-rules"></a>Beleidsregels voor naleving
* **Wachtwoordinstellingen vereisen op mobiele apparaten**. U kunt gebruikers een wachtwoord moeten invoeren voordat ze toegang krijgen hun apparaat tot vereisen.

  **Ondersteund door:**
    * Windows Phone 8+
    * iOS 6+
    * Android 4.0+
    * Samsung KNOX Standard 4.0+

* **Wachtwoord vereisen voor het ontgrendelen van een niet-actieve apparaat** (1602 update). U kunt gebruikers verplichten om een wachtwoord opgeven voor toegang tot apparaat is vergrendeld.

  **Ondersteund door:**
  * Windows Phone 8+
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Minuten van inactiviteit voordat wachtwoord vereist is** (1602 update). U kunt opgeven dat de niet-actieve tijd voordat de gebruiker moet het wachtwoord opnieuw in. Stel de waarde in op een van de beschikbare opties: **1 minute**, **5 minutes**, **15 minutes**, **30 minutes**, **1 hour**.

  Deze regel moet worden gebruikt met **wachtwoord vereist voor een niet-actieve apparaat hebt ontgrendeld**. De hier ingestelde waarde bepaalt wanneer het apparaat wordt beschouwd als niet-actieve en is vergrendeld. Wanneer **wachtwoord vereist voor een niet-actieve apparaat hebt ontgrendeld** is ingesteld op **waar**, een wachtwoord in om toegang tot het apparaat vergrendeld door de gebruiker moet invoeren.

  **Ondersteund door:**
  * Windows Phone 8+
  * Windows RT/8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Automatische updates vereisen** (1602 update). U kunt apparaten met Windows 8.1 of hoger nodig hebt om updates automatisch worden geïnstalleerd en u kunt de klasse van updates opgeven.

  De waarde moet worden ingesteld op **geen** om te voorkomen dat automatische installatie tot **aanbevolen** automatisch alle aanbevolen om updates te installeren, of **belangrijk** alleen de updates die zijn geclassificeerd als belangrijk te installeren.

  **Ondersteund door:**
  * Windows Phone 8+

* **Eenvoudige wachtwoorden toestaan**. U kunt gebruikers eenvoudige wachtwoorden zoals '1234' of "1111." Deze instelling is standaard uitgeschakeld.

  **Ondersteund door:**
  * Windows Phone 8+
  * iOS 6+

* **Minimale wachtwoordlengte**. U kunt opgeven dat het minimum aantal cijfers of tekens aan dat het wachtwoord van de gebruiker (standaard 6) moet hebben.

  **Ondersteund door:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

  >[!NOTE]
  >Voor apparaten waarop Windows wordt uitgevoerd en zijn beveiligd met een Microsoft-account, het nalevingsbeleid geen goede controles als **minimale wachtwoordlengte** groter is dan 8 tekens of als **minimumaantal tekensets** is meer dan 2.

* **Bestandsversleuteling op mobiel apparaat**. U kunt het apparaat worden versleuteld om te kunnen verbinding maken met bronnen vereisen. Apparaten met Windows Phone 8 worden automatisch versleuteld. Apparaten met iOS worden versleuteld wanneer u de instelling **Wachtwoordinstellingen vereisen voor mobiele apparaten**configureert. Deze instelling is standaard ingeschakeld.

  **Ondersteund door:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Apparaat mag niet jailbroken of geroot**. Als u deze instelling inschakelt, zijn voldoen opengebroken (iOS) of geroote (Android) apparaten niet compatibel. Deze instelling is standaard uitgeschakeld.

  **Ondersteund door:**
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **E-mailprofiel moet worden beheerd door Intune**. Als u deze optie instelt op **Ja**, het e-mailprofiel dat is geïmplementeerd op het apparaat moet worden gebruikt door het apparaat. Het apparaat wordt als niet-compatibel beschouwd als het e-mailprofiel niet in dezelfde gebruikersgroep wordt geïmplementeerd als de doelgroep waarop het nalevingsbeleid is gericht.

  Het apparaat wordt ook als niet-compatibel beschouwd als de gebruiker al een e-mailaccount op het apparaat heeft ingesteld dat overeenkomt met het Intune-e-mailprofiel dat op het apparaat is geïmplementeerd. In dit geval kan Intune het door de gebruiker ingerichte profiel niet overschrijven en kan het daarom niet beheren. De gebruiker kan het apparaat in overeenstemming brengen door het verwijderen van de bestaande e-mailinstellingen waarmee Intune het beheerde e-mailprofiel installeren.

  Zie [Toegang tot zakelijke e-mail inschakelen met behulp van e-mailprofielen en Microsoft Intune](https://technet.microsoft.com/library/dn800672.aspx)voor meer informatie over e-mailprofielen. Deze instelling is standaard uitgeschakeld.

  **Ondersteund door:**
  * iOS 6+

* **E-mailprofiel**. Als **e-mailaccount moet worden beheerd door Intune** is geselecteerd, kies **selecteren** kiezen van de e-mailprofiel dat apparaten moeten worden beheerd door. Het e-mailprofiel moet aanwezig zijn op het apparaat.

  **Ondersteund door:**
  * iOS 6+

* **Minimale OS vereist**. Wanneer een apparaat niet aan de minimum versievereiste voor besturingssysteem die u opgeeft voldoet, wordt deze gerapporteerd als niet-compatibel. Een koppeling met informatie over het bijwerken wordt weergegeven. De gebruiker kan kiezen om bij te werken van hun apparaat, waarna deze kan voor toegang tot bedrijfsbronnen worden.

  **Ondersteund door:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Maximale besturingssysteemversie toegestaan**. Wanneer een apparaat een versie van het besturingssysteem later dan de computer die u in de regel gebruikt opgeeft, toegang tot bedrijfsbronnen is geblokkeerd en de gebruiker gevraagd contact opnemen met hun IT-beheerder. Totdat u de regel voor het toestaan van de versie van het besturingssysteem wijzigt, kan dit apparaat kan niet worden gebruikt voor toegang tot bedrijfsresources.

  **Ondersteund door:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung KNOX Standard 4.0+

* **Vereisen dat apparaten moet worden gerapporteerd als beschadigd** (1602 update). U kunt een regel voor het vereist dat Windows 10-apparaten moeten worden gerapporteerd goed instellen in nieuwe of bestaande nalevingsbeleid. Als u deze instelling inschakelt, worden Windows 10-apparaten via de Health Attestation-Service (HAS) voor de volgende gegevenspunten geëvalueerd:

  - **BitLocker is ingeschakeld**. Als BitLocker ingeschakeld is, kan het apparaat gegevens die zijn opgeslagen op het station tegen onbevoegde toegang, wanneer het systeem is uitgeschakeld of gaat u naar de slaapstand te beveiligen.

   Windows BitLocker-stationsversleuteling versleutelt alle gegevens die zijn opgeslagen op het Windows-besturingssysteemvolume. BitLocker gebruikt de TPM om de Windows-besturingssysteem en de gebruikersgegevens te beveiligen. Het helpt om ervoor te zorgen dat een computer kan worden geknoeid, zelfs als u deze installatie zonder toezicht, verloren of gestolen.
   
   Als de computer is uitgerust met een compatibele TPM, gebruikt BitLocker de TPM om de versleutelingssleutels die de gegevens beveiligen te vergrendelen. Als gevolg hiervan zijn de sleutels niet toegankelijk totdat de TPM de status van de computer heeft gecontroleerd.

  - **Code-integriteitsbeleidsbestand is ingeschakeld**. Code-integriteit is een functie die de integriteit van een stuurprogramma of systeembestand valideert telkens wanneer dit in het geheugen wordt geladen. Code-integriteitsbeleidsbestand detecteert of een niet-ondertekende stuurprogramma of systeem-bestand in de kernel wordt geladen. Ook wordt gedetecteerd of een systeembestand is gewijzigd door schadelijke software die wordt uitgevoerd door een gebruikersaccount met beheerdersbevoegdheden.

  - **Beveiligd opstarten is ingeschakeld**. Als beveiligd opstarten is ingeschakeld, wordt het systeem geforceerd starten in de fabrieksstatus van een vertrouwd. Ook moet als beveiligd opstarten is ingeschakeld, hebben de belangrijkste onderdelen gebruikt voor het starten van de machine juist cryptografische handtekeningen die worden vertrouwd door de organisatie die het apparaat wordt geproduceerd. De UEFI-firmware verifieert dit voordat de machine wordt opgestart. Als alle bestanden is geknoeid, hun handtekening op te splitsen het systeem niet gestart.

  - **Vroege starten antimalware is ingeschakeld**. Deze instelling geldt alleen voor pc's. Early Launch Antimalware (ELAM) biedt beveiliging voor de computers in uw netwerk wanneer deze worden opgestart en voordat stuurprogramma's van derden worden geïnitialiseerd.
  
   Deze regel is standaard uitgeschakeld.

  Zie [Health Attestation CSP](https://msdn.microsoft.com/library/dn934876.aspx)(Engelstalig) voor meer informatie over de werking van de HAS-service.

  **Ondersteund door:**
  * Windows 10 en 10 Windows Mobile

- **Apps die kunnen niet worden geïnstalleerd op het apparaat**. Als gebruikers een app uit de beheerder niet-compatibele lijst met apps installeren, moet zij wanneer ze proberen toegang tot zakelijke e-mail en andere bedrijfsbronnen die ondersteuning bieden voor voorwaardelijke toegang. Met deze regel moet de naam van de app en de app-ID wanneer een app toe te voegen aan de lijst met niet-compatibele gedefinieerd door de beheerder. Uitgever van de app kan ook worden toegevoegd, maar het is niet vereist.

    **Ondersteund door:**
      * iOS 6+
      * Android 4.0+
      * Samsung KNOX Standard 4.0+

### <a name="find-an-app-id"></a>Een app-ID vinden

Een app-ID is een id die de app in de Apple en Google toepassingsservices wordt aangeduid. Een voorbeeld is com.contoso.myapp. Te zoeken:

- **Android**
    - Hier vindt u de app-ID in de Google Play opslaan URL die is gebruikt om de app te maken. Een voorbeeld van de app-ID is: *...? id=com.companyname.appname & hl = nl*

- **iOS**
    1. Opslaan in de iTunes URL, zoek het id-nummer, zoals in dit voorbeeld: */id875948587? mt = 8*

    2. In een webbrowser, gaat u naar de volgende URL, het getal vervangen met het ID-nummer dat u zojuist hebt gevonden (in dit geval het vorige voorbeeld): https://itunes.apple.com/lookup?id=875948587

    3. Download en open het tekstbestand.
  
    4. Zoek de tekst **bundel-id**.

    Een voorbeeld van de app-ID is: "*bundel-id*": "*com.companyname.appname*" 


