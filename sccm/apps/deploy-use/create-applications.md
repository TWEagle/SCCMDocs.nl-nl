---
title: Toepassingen maken
titleSuffix: Configuration Manager
description: Maken en implementeren van toepassingen en implementatietypen met System Center Configuration Manager.
ms.custom: na
ms.date: 11/07/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: 
caps.handback.revision: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: d7073b397cdf7b233f8264bd07019303a77a610f
ms.sourcegitcommit: 2f6a13d208dcd8aa59c88f107791f9c4388e78e2
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/18/2018
---
# <a name="create-applications-with-system-center-configuration-manager"></a>Toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een System Center Configuration Manager-toepassing heeft de bestanden en gegevens die nodig zijn om software te implementeren op een apparaat. Een toepassing heeft een of meer implementatietypen waaruit de installatiebestanden en informatie die nodig zijn om software te installeren. Een implementatietype heeft ook regels die specificeren hoe en wanneer de software wordt geïmplementeerd.  

 U kunt toepassingen maken met behulp van de volgende methoden:  

-   De toepassing en implementatietype-typen automatisch maken door te lezen van de installatiebestanden van de toepassing.  

-   U kunt de toepassing handmatig maken en deze op een later tijdstip aan implementatietypen toevoegen.  

-   Een toepassing importeren uit een bestand.  

> [!NOTE]  
>  [Toepassingen voor mobiele apparaten maken](../../mdm/deploy-use/create-applications.md) bevat gedetailleerde informatie over het maken van iOS-, Windows Phone- en Android-toepassingen.  

Gebruik de volgende stappen voor het maken van Configuration Manager-toepassingen en implementatietypen.  

## <a name="start-the-create-application-wizard"></a>De wizard toepassing maken starten  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken**.  

## <a name="specify-whether-you-want-to-automatically-detect-application-information-or-manually-define-the-information"></a>Opgeven of toepassingsinformatie automatisch detecteren of de informatie handmatig definiëren  

-   Toepassingsinformatie automatisch detecteren wanneer u wilt maken van een eenvoudige toepassing met één implementatietype, zoals een Windows Installer-bestand dat geen afhankelijkheden of vereisten. Nadat u via deze procedure een toepassing hebt gemaakt, kunt deze op de gewenste wijze bewerken om implementatietypen toe te voegen of te wijzigen en om detectiemethoden, afhankelijkheden of vereisten toe te voegen.  

-   Geef handmatig de toepassingsinformatie voor het maken van complexe toepassingen met meerdere implementatietypen, afhankelijkheden, detectiemethoden of vereisten.  

### <a name="automatically-detect-application-information"></a>Toepassingsinformatie automatisch detecteren  

1.  Op de **algemene** pagina van de wizard toepassing maken selecteert **automatisch detecteren van informatie over deze toepassing uit de installatiebestanden van**.  

2.  In de **Type** vervolgkeuzelijst, selecteert het installatiebestandstype toepassing die u wilt gebruiken voor het detecteren van toepassingsinformatie. Zie [Implementatietypen die door Configuration Manager worden ondersteund](/sccm/apps/deploy-use/create-applications#deployment-types-supported-by-configuration-manager) in dit onderwerp voor meer informatie over de beschikbare installatietypen.  

3.  In de **locatie** geeft u het UNC-pad (in de vorm  *\\ \\server\\delen\\\filename*) of de opslagkoppeling voor het toepassingsinstallatiebestand dat u gebruiken wilt voor het detecteren van toepassingsinformatie. U kunt ook op **Bladeren** klikken om naar het installatiebestand te bladeren.  

    > [!IMPORTANT]  
    >  Wanneer u selecteert **Windows Installer (\*MSI-bestand)** als een toepassingstype alle bestanden in de map die u opgeeft, met de toepassing geïmporteerd en naar distributiepunten wordt verzonden. Zorg ervoor dat de map die u opgeeft alleen de bestanden die nodig zijn voor het installeren van de toepassing bevat. Configuration Manager is getest om maximaal 20.000 toepassingsbestanden in het toepassingspakket te ondersteunen. Als uw toepassing meer bestanden heeft, kunt u meerdere toepassingen met een kleiner aantal bestanden te maken.  

    >  U moet toegang hebben tot het UNC-pad met de toepassing en eventuele submappen die toepassingsinhoud bevatten.  

4.  Op de **informatie importeren** pagina van de wizard toepassing maken, controleert u de informatie die geïmporteerd is en kies vervolgens **volgende**. Indien nodig, kunt u **vorige** teruggaan en eventuele fouten te corrigeren.  

5.  Op de **algemene informatie** pagina van de wizard toepassing maken de volgende informatie opgeven:  

    > [!NOTE]  
    >  Sommige informatie is mogelijk al ingevuld als deze automatisch is opgehaald uit de installatiebestanden van de toepassing. Het kan bovendien zijn dat de weergegeven opties wisselen op basis van het toepassingstype dat u maakt.  

    -   Algemene informatie over de toepassing, zoals de toepassingsnaam, opmerkingen, versie en optionele referentie waarmee u kunt de toepassing niet vinden in de Configuration Manager-console.  

    -   **Het installatieprogramma**--Geef het installatieprogramma en alle vereiste eigenschappen die nodig zijn voor het implementatietype van de toepassing installeren.  

        > [!TIP]  
        >  Als het installatieprogramma niet wordt weergegeven, kiest u **Bladeren** en blader naar de installatieprogrammalocatie.  

    -   **Installatiegedrag**--Geef op of het implementatietype van de toepassing alleen voor de momenteel aangemelde gebruiker of voor alle gebruikers wordt geïnstalleerd. U kunt ook opgeven dat het implementatietype wordt geïnstalleerd voor alle gebruikers als dit wordt geïmplementeerd op een apparaat of alleen op een specifieke gebruiker als dit wordt geïmplementeerd voor een gebruiker.  

    -   **Een automatische VPN-verbinding gebruiken (indien geconfigureerd)**--als een VPN-profiel is geïmplementeerd op het apparaat waarop de app wordt gestart, wordt de VPN-verbinding samen met de app gestart (Windows 8.1 en alleen voor Windows Phone 8.1).  

         Op Windows Phone 8.1-apparaten, worden automatische VPN-verbindingen worden niet ondersteund als er meer dan één VPN-profiel is geïmplementeerd op het apparaat.  

         Zie voor meer informatie over VPN-profielen [VPN-profielen](../../protect/deploy-use/vpn-profiles.md).  

6.  Kies **volgende**, Controleer de toepassingsinformatie op de **samenvatting** pagina en voltooi de wizard toepassing maken.  

De nieuwe toepassing wordt weergegeven in de **toepassingen** knooppunt van de Configuration Manager-console en u klaar bent met het maken van een toepassing. Zie [Implementatietypen voor de toepassing maken](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application) in dit onderwerp als u meer implementatietypen aan de toepassing wilt toevoegen.  

### <a name="manually-specify-application-information"></a>Toepassingsinformatie handmatig opgeven  

1.  Op de **algemene** pagina van de wizard toepassing maken selecteert **de toepassingsinformatie handmatig opgeven**, en kies vervolgens **volgende**.  

2.  Geef algemene informatie over de toepassing, zoals de toepassingsnaam, opmerkingen, versie en optionele referentie waarmee u kunt de toepassing niet vinden in de Configuration Manager-console.  

3.  Op de **Application Catalog** pagina van de wizard toepassing maken de volgende informatie opgeven:  

    -   **Geselecteerde taal**--Selecteer In de vervolgkeuzelijst de taalversie van de toepassing die u wilt instellen. Kies **toevoegen/verwijderen** voor het instellen van meer talen voor deze toepassing.  

    -   **Gelokaliseerde toepassingsnaam**--Geef de toepassingsnaam op in de taal die u hebt geselecteerd in de **geselecteerde taal** vervolgkeuzelijst.  

        > [!IMPORTANT]  
        >  U moet een gelokaliseerde toepassingsnaam voor iedere taalversie die u hebt ingesteld.  

    -   **Gebruikerscategorieën**--kiezen **bewerken** Toepassingscategorieën opgeven in de taal die u hebt geselecteerd in de **geselecteerde taal** vervolgkeuzelijst. Gebruikers van Software Center kunnen deze geselecteerde categorieën gebruiken om te filteren en sorteren van de beschikbare toepassingen.  

    -   **Gebruikersdocumentatie**--kiezen **Bladeren** om op te geven van de URL, of het UNC-pad en de naam van een bestand dat gebruikers van Software Center lezen kunnen voor meer informatie over deze toepassing.  

    -   **Tekst koppeling**--Geef de tekst die wordt weergegeven in plaats van de URL van de toepassing.  

    -   **Privacy-URL van toepassing**--Geef een URL die verwijst naar de privacyverklaring voor de toepassing.  

    -   **Gelokaliseerde beschrijving**--Geef een beschrijving voor deze toepassing in de taal die u hebt geselecteerd in de **geselecteerde taal** vervolgkeuzelijst.  

    -   **Trefwoorden**--Geef een lijst met trefwoorden in de taal die u hebt geselecteerd in de **geselecteerde taal** vervolgkeuzelijst. Deze trefwoorden helpen gebruikers van Software Center zoeken naar de toepassing.  

    -   **Pictogram**--kiezen **Bladeren** selecteren van een pictogram voor deze toepassing uit de beschikbare pictogrammen. Als u geen pictogram opgeeft, wordt een standaardpictogram gebruikt voor deze toepassing. U kunt nu een pictogram met een afmetingen in pixels van maximaal 512 x 512 instellen.

    -   **Geef deze App weer als aanbevolen app en markeer deze in de bedrijfsportal**--Selecteer deze optie om de app prominent wilt weergeven in de bedrijfsportal.  

4.  Op de **implementatietypen** pagina van de wizard toepassing maken de optie **toevoegen** om een nieuw implementatietype te maken.  

 Zie voor meer informatie [implementatietypen maken voor de toepassing](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application).  

5.  Kies **volgende**, Controleer de toepassingsinformatie op de **samenvatting** pagina en voltooi de wizard toepassing maken.  

De nieuwe toepassing wordt weergegeven in de **toepassingen** knooppunt van de Configuration Manager-console.  

##  <a name="create-deployment-types-for-the-application"></a>Implementatietypen voor de toepassing maken  
 Als u selecteert **automatisch informatie identificeren over dit implementatietype vanuit installatiebestanden** op de **algemene** pagina van de wizard implementatietype maken, hoeft u mogelijk niet sommige van de stappen in de volgende procedures te voltooien.  

## <a name="start-the-create-deployment-type-wizard"></a>De wizard Implementatietype maken starten  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Selecteer een toepassing en klik vervolgens op de **Start** tabblad, in de **toepassing** groep, kiest u **implementatietype maken**.  

> [!TIP]  
>  U kunt de wizard implementatietype maken ook starten vanuit de wizard toepassing maken en naar de **implementatietypen** tabblad van de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster.  

## <a name="specify-whether-you-want-to-automatically-detect-deployment-type-information-or-manually-set-up-the-information"></a>Opgeven of toepassingsinformatie automatisch detecteren of de informatie handmatig instellen  
 Gebruik een van de volgende procedures om automatisch detecteren of implementatietype-informatie handmatig instellen.  

### <a name="automatically-detect-deployment-type-information"></a>Toepassingsinformatie automatisch detecteren  

1.  Op de **algemene** pagina van de wizard implementatietype maken, selecteer **automatisch informatie identificeren over dit implementatietype vanuit installatiebestanden**.  

2.  In de **Type** selecteert het installatiebestandstype van toepassing die u gebruiken wilt voor het detecteren van toepassingsinformatie.  

3.  In de **locatie** geeft u het UNC-pad (in de vorm  *\\ \\server\\delen\\filename*) of de opslagkoppeling voor de installatiebestanden van de toepassing en de inhoud die u gebruiken wilt voor het detecteren van de implementatietype-informatie opgeven. U kunt ook **Bladeren** om de installatiebestand te zoeken.  

    > [!NOTE]  
    >  U moet toegang hebben tot het UNC-pad met de toepassing en eventuele submappen die de toepassingsinhoud bevatten.  

4.  Op de **informatie importeren** pagina van de wizard implementatietype maken, controleert u de informatie die geïmporteerd is en kies vervolgens **volgende**. U kunt ook **vorige** teruggaan en eventuele fouten te corrigeren.  

5.  Op de **algemene informatie** pagina van de wizard implementatietype maken de volgende informatie opgeven:  

    > [!NOTE]  
    >  Sommige implementatietype-informatie is mogelijk al ingevuld als deze automatisch is opgehaald uit de installatiebestanden van de toepassing. Bovendien verschillen de weergegeven opties, afhankelijk van het implementatietype dat u maakt.  

    -   Algemene informatie over het implementatietype, zoals de naam, de beheerder opmerkingen en de beschikbare talen.  

    -   **Het installatieprogramma**--Geef het installatieprogramma en alle eigenschappen die u nodig hebt om het implementatietype te installeren.  

    -   **Installatiegedrag**--opgeven of het implementatietype voor de huidige gebruiker of voor alle gebruikers geïnstalleerd. U kunt ook opgeven of het implementatietype voor alle gebruikers installeren wanneer deze is geïmplementeerd op een apparaat, of of voor het installeren van de implementatie voor een gebruiker alleen als dit wordt geïmplementeerd voor een gebruiker.  

    -   **Een automatische VPN-verbinding gebruiken (indien geconfigureerd)**--als een VPN-profiel is geïmplementeerd op het apparaat waarop de app wordt gestart, wordt de VPN-verbinding samen met de app gestart (Windows 8.1 en alleen voor Windows Phone 8.1). Als u meerdere VPN-profielen zijn geïmplementeerd op een Windows 8.1-apparaat, wordt standaard het eerste geïmplementeerde VPN-profiel gebruikt.  

         Op Windows Phone 8.1-apparaten, worden automatische VPN-verbindingen worden niet ondersteund als er meer dan één VPN-profiel is geïmplementeerd op het apparaat.  

         Zie voor meer informatie over VPN-profielen [VPN-profielen in System Center Configuration Manager](../../protect/deploy-use/vpn-profiles.md).  

6.  Kies **volgende**, en ga verder naar [inhoudsopties voor het implementatietype opgeven](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

### <a name="manually-set-up-the-deployment-type-information"></a>Handmatig de implementatietype-informatie instellen  

1.  Op de **algemene** pagina van de wizard implementatietype maken, selecteer **Geef handmatig de implementatietype-informatie**.  

2.  In de **Type** vak, installatiebestandstype de toepassing die u gebruiken wilt voor het detecteren van toepassingsinformatie. U kunt de dezelfde installatietypen die u gebruiken wilt wanneer u de implementatietype-informatie voor het automatisch detecteren en u kunt ook een script voor het installeren van het implementatietype opgeven.  

3.  Op de **algemene informatie** pagina van de wizard implementatietype maken een naam opgeven voor het implementatietype, een optionele beschrijving en de talen waarin u wilt dat dit implementatietype beschikbaar is en kies vervolgens **volgende**.  

4.  Ga door naar [Inhoudopties voor het implementatietype opgeven](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

##  <a name="specify-content-options-for-the-deployment-type"></a>Inhoudopties voor het implementatietype opgeven  

1.  Op de **inhoud** pagina van de wizard implementatietype maken de volgende informatie opgeven:  

    -   **Locatie van inhoud**--Geef de locatie van de inhoud voor dit implementatietype of selecteer **Bladeren** kiezen van de map met inhoud implementatietype.  

        > [!IMPORTANT]  
        >  Het systeemaccount van de siteservercomputer moet machtigingen hebben voor de locatie van de inhoud die u opgeeft.  

    -   **Verwijderen van de instellingen van inhoud**--Geef een van de volgende opties:
        - **Hetzelfde zijn als de inhoud wordt geïnstalleerd**--Selecteer deze optie als de installatie en verwijdering van inhoud zijn hetzelfde. Dit is de standaardinstelling.
        - **Geen inhoud verwijderen**--Selecteer deze optie als uw toepassing heeft geen inhoud nodig om te verwijderen.
        - **Verschilt van de installatie-inhoud**--Selecteer deze optie als de inhoud verwijderen van de installatie-inhoud verschilt.

4. Als u hebt geselecteerd **verschillend van installatie-inhoud**, blader naar of typ de locatie van de inhoud van de toepassing die wordt gebruikt om de toepassing te verwijderen.
5. Klik op **OK** implementatie type in het dialoogvenster Eigenschappen te sluiten.

    -   **Inhoud in de clientcache behouden**--Selecteer deze optie om op te geven of de inhoud moet worden bewaard in de cache op de clientcomputer voor onbepaalde tijd, zelfs als deze al is uitgevoerd. Hoewel deze optie kan nuttig zijn bij sommige implementaties, zoals Windows Installer gebaseerde software waarvoor een lokale bronkopie beschikbaar zijn voor het toepassen van updates, zijn verkort deze de cacheruimte beschikbaar. Als u deze optie selecteert, kan dit ertoe leiden dat een grote implementatie op een later tijdstip mislukt als de cache niet voldoende beschikbare ruimte beschikt.  

    -   **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**--Selecteer deze optie om de belasting op het netwerk te verminderen door clients inhoud downloaden van andere lokale clients op het netwerk dat al hebben gedownload en gecached. Deze optie maakt gebruik van Windows BranchCache-technologie.  

    -   **Het installatieprogramma**--Geef de naam van het installatieprogramma en eventueel vereiste installatieparameters of kies **Bladeren** om de installatiebestand te zoeken.  

    -   **Start installatie over**--Geef eventueel de map die het installatieprogramma voor het implementatietype heeft. Deze map kan zich een absoluut pad op de client of een pad naar de distributiepuntmap die de installatiebestanden heeft.  

    -   **Programma voor verwijderen**--desgewenst de naam van het programma voor verwijderen en eventueel vereiste parameters opgeven, of kies **Bladeren** terug te vinden.  

    -   **Verwijderen start over**--Geef eventueel de map die het programma voor verwijderen voor het implementatietype heeft. Deze map kan zich een absoluut pad op de client of een pad dat ten opzichte van de distributiepuntmap die het pakket heeft.  

    -   **Installatie programma en verwijderen uitvoeren als 32-bits proces op 64-bits clients**--de 32-bits bestand en registerlocaties locaties op Windows-computers gebruiken om uit te voeren van het installatieprogramma voor het implementatietype.  

2.  Kies **volgende**.  

## <a name="set-up-detection-methods-to-indicate-the-presence-of-the-deployment-type-windows-pcs-only"></a>Detectiemethoden instellen om aan te geven van de aanwezigheid van het implementatietype (alleen Windows-pc's)  
 Deze procedure stelt u een detectiemethode die aangeeft of het implementatietype al is geïnstalleerd.  

1.  Op de **detectiemethode** pagina van de wizard implementatietype maken, selecteer **regels configureren voor het detecteren van de aanwezigheid van dit implementatietype**, en kies vervolgens **component toevoegen**.  

    > [!NOTE]  
    >  U kunt ook **Gebruik een aangepast script om de aanwezigheid van dit implementatietype te detecteren** selecteren. Zie voor meer informatie [een aangepast script gebruiken om te controleren op de aanwezigheid van een implementatietype](/sccm/apps/deploy-use/create-applications#Use-a-custom-script-to-check-for-the-presence-of-a-deployment-type).  

2.  Selecteer in de vervolgkeuzelijst **Instellingstype** in het dialoogvenster **Detectieregel** de methode die u wilt gebruiken voor het detecteren van de aanwezigheid van het implementatietype. U kunt kiezen uit de volgende beschikbare methoden:  

    -   **Bestandssysteem**--deze methode gebruiken om te detecteren of het opgegeven bestand of map op een clientapparaat bestaat, duidt dit erop dat de toepassing is geïnstalleerd.  

        > [!NOTE]  
        >  De **bestandssysteem** Instellingstype biedt geen ondersteuning voor het opgeven van een UNC-pad naar een netwerkshare in het veld pad. U kunt op het clientapparaat alleen een lokaal pad opgeven.  
        >   
        >  Als u wilt controleren 32-bits bestandslocaties voor het opgegeven bestand of map, selecteert u de optie **dit bestand of deze map is gekoppeld aan een 32-bits toepassing op 64-bits systemen** eerste. Als het bestand of de map niet wordt gevonden, wordt er op de 64-bits locaties gezocht.  

    -   **Register**--deze methode gebruiken om te detecteren of een opgegeven registersleutel of registerwaarde op een clientapparaat bestaat, duidt dit erop dat de toepassing is geïnstalleerd.  

        > [!NOTE]  
        >  Selecteer de optie om te controleren op 32-bits registerlocaties voor de opgegeven registersleutel, **deze registersleutel is gekoppeld aan een 32-bits toepassing op 64-bits systemen** eerste. Als de registersleutel niet wordt gevonden, wordt er op de 64-bits locaties gezocht.  

    -   **Windows Installer**--deze methode gebruiken om te detecteren of een opgegeven Windows Installer-bestand op een clientapparaat bestaat, duidt dit erop dat de toepassing is geïnstalleerd.  

3.  Geef details over het item dat u gebruiken om te detecteren wilt of dit implementatietype is geïnstalleerd. U kunt bijvoorbeeld een bestand, map, registersleutel, registerwaarde of een Windows Installer-productcode gebruiken.  

4.  Geef details op over de waarde die u wilt beoordelen tegen opzichte van het item dat u wilt gebruiken om te detecteren of een implementatietype is geïnstalleerd. Als u een bestandsbeheertaak gebruiken om te controleren of het implementatietype wordt geïnstalleerd, kunt u bijvoorbeeld **de bestandssysteeminstelling moet bestaan op het doelsysteem om aan te geven van de aanwezigheid van deze toepassing**.  

5.  Kies **volgende** sluiten de **detectieregel** in het dialoogvenster.  

###  <a name="use-a-custom-script-to-check-for-the-presence-of-a-deployment-type"></a>Een aangepast script gebruiken om te controleren op de aanwezigheid van een implementatietype  

1.  Op de **detectiemethode** pagina van de wizard implementatietype maken, selecteer de **een aangepast script gebruiken voor het detecteren van de aanwezigheid van dit implementatietype** vak in en kies vervolgens **bewerken**.  

2.  Selecteer in de vervolgkeuzelijst **Scripttype** in het dialoogvenster **Scripteditor** de scripttaal die u wilt gebruiken voor het detecteren van het implementatietype.  

3.  In de **inhoud Script** Voer het script dat u wilt gebruiken. U kunt ook de inhoud van een bestaand script in dit veld plakken of kies **Open** om naar een bestaand opgeslagen script te bladeren. Configuration Manager controleert de resultaten van het script door de waarde die is geschreven naar de Standard Out uitvoerstroom (STDOUT), de uitvoerstroom standaardfout (STDERR) en de afsluitcode van het script te lezen. Als de afsluitcode een andere waarde dan nul is, is het script mislukt en is de toepassingsdetectiestatus onbekend. Als de afsluitcode nul is en STDOUT gegevens bevat, is de toepassingsdetectiestatus geïnstalleerd.  

 Gebruik de volgende tabel voor informatie over het gebruiken van de uitvoer van een script om te controleren of een toepassing is geïnstalleerd.  

|Scriptafsluitcode|Details|
|--------------------------------|-----------------|
|0|**Gegevens die in STDOUT zijn gelezen**--leeg<br /><br /> **Gegevens die in STDERR zijn gelezen**--leeg<br /><br /> **Scriptresultaat**--geslaagd<br /><br /> **Detectiestatus van toepassing**--niet geïnstalleerd|  
|0|**Gegevens die in STDOUT zijn gelezen**--leeg<br /><br /> **Gegevens die in STDERR zijn gelezen**--niet leeg zijn<br /><br /> **Scriptresultaat**--fout<br /><br /> **Detectiestatus van toepassing**--onbekend|  
|0|**Gegevens die in STDOUT zijn gelezen**--niet leeg zijn<br /><br /> **Gegevens die in STDERR zijn gelezen**--leeg<br /><br /> **Scriptresultaat**--geslaagd<br /><br /> **Detectiestatus van toepassing**--geïnstalleerd|  
|0|**Gegevens die in STDOUT zijn gelezen**--niet leeg zijn<br /><br /> **Gegevens die in STDERR zijn gelezen**--niet leeg zijn<br /><br /> **Scriptresultaat**--geslaagd<br /><br /> **Detectiestatus van toepassing**--geïnstalleerd|  
|Niet-nulwaarde|**Gegevens die in STDOUT zijn gelezen**--leeg<br /><br /> **Gegevens die in STDERR zijn gelezen**--leeg<br /><br /> **Scriptresultaat**--fout<br /><br /> **Detectiestatus van toepassing**--onbekend|  
|Niet-nulwaarde|**Gegevens die in STDOUT zijn gelezen**--leeg<br /><br /> **Gegevens die in STDERR zijn gelezen**--niet leeg zijn<br /><br /> **Scriptresultaat**--fout<br /><br /> **Detectiestatus van toepassing**--onbekend|  
|Niet-nulwaarde|**Gegevens die in STDOUT zijn gelezen**--niet leeg zijn<br /><br /> **Gegevens die in STDERR zijn gelezen**--leeg<br /><br /> **Scriptresultaat**--fout<br /><br /> **Detectiestatus van toepassing**--onbekend|  
|Niet-nulwaarde|**Gegevens die in STDOUT zijn gelezen**--niet leeg zijn<br /><br /> **Gegevens die in STDERR zijn gelezen**--niet leeg zijn<br /><br /> **Scriptresultaat**--fout<br /><br /> **Detectiestatus van toepassing**--onbekend|  

De volgende tabel bevat voorbeeldscripts (VB Microsoft Visual Basic) waarmee u kunt uw eigen toepassingsdetectiescripts schrijven.  

|Visual Basic-voorbeeldscript|Beschrijving|  
|--------------------------------|-----------------|  
|**WScript.Quit(1)**|Dit script retourneert een afsluitcode die niet gelijk is aan nul, wat aangeeft dat dit is uitgevoerd. In dit geval is de status van de detectie van de toepassing onbekend.|  
|**WScript.StdErr.Write "Script is mislukt"**<br /><br /> **WScript.Quit(0)**|Het script retourneert een afsluitcode die gelijk is aan nul, maar de waarde STDERR is niet leeg, wat aangeeft dat het uitvoeren van het script is mislukt. In dit geval is de status van de detectie van de toepassing onbekend.|  
|**WScript.Quit(0)**|Dit script retourneert een afsluitcode die gelijk is aan nul, wat aangeeft dat het is uitgevoerd. De waarde voor STDOUT is echter leeg, wat aangeeft dat de toepassing niet is geïnstalleerd.|  
|**WScript.StdOut.Write "de toepassing is geïnstalleerd'**<br /><br /> **WScript.Quit(0)**|Dit script retourneert een afsluitcode die gelijk is aan nul, wat aangeeft dat het is uitgevoerd. De waarde voor STDOUT is niet leeg, wat aangeeft dat de toepassing niet is geïnstalleerd.|  
|**WScript.StdOut.Write "de toepassing is geïnstalleerd'**<br /><br /> **WScript.StdErr.Write "Completed"**<br /><br /> **WScript.Quit(0)**|Dit script retourneert een afsluitcode die gelijk is aan nul, wat aangeeft dat het is uitgevoerd. De waarden voor STDOUT en STDERR zijn niet leeg, wat aangeeft dat de toepassing is geïnstalleerd.|  

 > [!NOTE]  
 >  De maximale grootte die u voor een script kunt gebruiken, is 32 kilobytes (KB).  

4.  Kies **OK** sluiten de **scripteditor** in het dialoogvenster.  

## <a name="specify-user-experience-options-for-the-deployment-type"></a>Opties voor gebruikerservaring opgeven voor het implementatietype  
 Deze instellingen bepalen hoe de toepassing wordt geïnstalleerd op apparaten en wat de gebruiker te zien krijgen.  

1.  Op de **gebruikerservaring** pagina van de wizard implementatietype maken de volgende informatie opgeven:  

    -   **Installatiegedrag**--Selecteer In de vervolgkeuzelijst een van de volgende opties:  

        -   **Installeren voor gebruiker**--de toepassing wordt alleen geïnstalleerd voor de gebruiker aan wie de toepassing is geïmplementeerd.  

        -   **Installeren voor systeem**--de toepassing wordt slechts één keer geïnstalleerd en is beschikbaar voor alle gebruikers.  

        -   **Installeren voor systeem indien de resource is verwijderd. anders installeren voor gebruiker**--als de toepassing wordt geïmplementeerd op een apparaat, wordt deze geïnstalleerd voor alle gebruikers. Als de toepassing wordt geïmplementeerd voor een gebruiker, wordt deze alleen voor die gebruiker geïnstalleerd.  

    -   **Aanmeldvereiste**--Geef de aanmeldvereisten op voor dit implementatietype vanuit de volgende opties:  

        -   **Alleen wanneer een gebruiker is aangemeld**  

        -   **Of een gebruiker is aangemeld**  

        -   **Alleen als er geen gebruiker is aangemeld**  

        > [!NOTE]  
        >  Deze optie wordt standaard ingesteld op **alleen als een gebruiker is aangemeld**, en kan niet worden gewijzigd als u hebt geselecteerd **installeren voor gebruiker** in de **installatiegedrag** vervolgkeuzelijst.  

    -   **Zichtbaarheid installatieprogramma**--Geef de modus waarin het implementatietype op clientapparaten wordt uitgevoerd. De volgende opties zijn beschikbaar:  

        -   **Gemaximaliseerd**--het implementatietype wordt gemaximaliseerd uitgevoerd op clientapparaten. De installatieactiviteit is zichtbaar voor de gebruiker.  

        -   **Normaal**--het implementatietype wordt uitgevoerd in de normale modus op basis van systeem en standaardprogramma. Dit is de standaardmodus.  

        -   **Geminimaliseerd**--het implementatietype wordt geminimaliseerd uitgevoerd op clientapparaten. Gebruikers zien de installatieactiviteit in het systeemvak of de taakbalk mogelijk.  

        -   **Verborgen**--het implementatietype wordt op clientapparaten verborgen en gebruikers zullen geen installatieactiviteit weergegeven.  

    -   **Toestaan dat gebruikers de programma-installatie kunnen zien en**--opgeven of een gebruiker met de implementatietype-installatie communiceren kan voor het instellen van de installatieopties.  

        > [!NOTE]  
        >  Deze optie is standaard ingeschakeld als u hebt geselecteerd de **installeren voor gebruiker** optie in de **installatiegedrag** vervolgkeuzelijst.  

    -   **Maximale toegestane uitvoeringstijd (minuten)**--Geef de maximale tijd die het programma uit te voeren op de clientcomputer wordt verwacht. U kunt deze instelling opgeven als een geheel getal dat groter is dan nul. De standaardinstelling is 120 minuten.  

         Deze waarde wordt gebruikt voor:  

        -   Controleren van de resultaten van het implementatietype.  

        -   Controleer of een implementatietype wordt geïnstalleerd wanneer er op clientapparaten onderhoudsvensters zijn gedefinieerd. Wanneer u een onderhoudsvenster is ingevoerd, een programma alleen gestart als er genoeg tijd beschikbaar is in het onderhoudsvenster voor de **maximale toegestane uitvoeringstijd** instelling.  

        > [!IMPORTANT]  
        >  Een conflict optreden als de **maximale toegestane uitvoeringstijd** langer is dan het geplande onderhoudsvenster. Als de gebruiker de maximale uitvoeringsduur instelt op een periode die langer is dan de lengte van welk beschikbaar onderhoudsvenster dan ook, wordt het implementatietype niet uitgevoerd.  

    -   **Geschatte installatietijd (minuten)**--Geef de geschatte tijd die de installatie van het implementatietype wordt uitgevoerd. Deze is zichtbaar voor gebruikers van Software Center.  

    -   **Geef specifieke opnieuw opstarten gedrag**--Geef de actie na de installatie. De volgende opties zijn beschikbaar:  

        -   **Bepaal bedrag op basis van retourcodes**--verwerken op basis van de codes die zijn geconfigureerd op het tabblad retourcodes opnieuw is opgestart.  Het Software Center weergegeven **mogelijk opnieuw worden opgestart**.  Als een gebruiker is aangemeld tijdens de installatie wordt ze gevraagd, afhankelijk van de configuratie van de gebruikerservaring van de implementatie.  

        -   **Er is geen specifieke actie**--niet opnieuw opgestart na de installatie is vereist.  Het Software Center rapporteert dat opnieuw opstarten is niet vereist.  
        -   **Het software-installatieprogramma forceert mogelijk een herstart van het apparaat**--Configuration Manager wordt niet bepalen of opnieuw opstarten initiëren, maar de werkelijke installatie mogelijk doen zonder waarschuwing.  Gebruik deze instelling om te voorkomen dat Configuration Manager rapporteert installatiefout wanneer het installatieprogramma start de computer opnieuw is opgestart.  Het Software Center weergegeven **mogelijk opnieuw worden opgestart**.  

        -   **Configuration Manager-client forceert een herstart van het apparaat verplicht**--Configuration Manager forceert een apparaat opnieuw starten na geslaagde installatie.  Het Software Center rapporteert dat een herstart vereist is.  Als een gebruiker is aangemeld tijdens de installatie wordt ze gevraagd, afhankelijk van de configuratie van de gebruikerservaring van de implementatie.

## <a name="specify-requirements-for-the-deployment-type"></a>Vereisten voor het implementatietype opgeven  

1.  Op de **vereisten** pagina van de wizard implementatietype maken de optie **toevoegen** openen de **vereiste maken** dialoogvenster vak en voeg een nieuwe vereiste toe.  

    > [!NOTE]  
    >  U kunt ook nieuwe vereisten toevoegen op de **vereisten** tabblad van de *< naam implementatietype\>*  **eigenschappen** in het dialoogvenster.  

2.  Selecteer in de vervolgkeuzelijst **Categorie** of deze vereiste geldt voor een apparaat of een gebruiker of selecteer **Aangepast** als u een eerder gemaakte globale voorwaarde wilt gebruiken. Wanneer u selecteert **aangepaste**, u kunt ook **maken** voor het maken van een nieuwe globale voorwaarde. Zie voor meer informatie over globale voorwaarden [globale voorwaarden maken](../../apps/deploy-use/create-global-conditions.md).  

    > [!IMPORTANT]  
    >  Een vereiste voor de categorie **gebruiker** en de voorwaarde **primair apparaat** wordt genegeerd als u de toepassing voor een apparaatverzameling implementeren.  
    >   
    >  Als u een Windows-pakket en -programma of -takenreeks hebt gemaakt waarvoor als vereiste geldt dat Windows 10 gebruikmaakt van System Center 2012 R2 Configuration Manager SP1, en u vervolgens een upgrade uitvoert naar System Center Configuration Manager, worden de vereisten voor Windows 10 mogelijk verwijderd. U kunt dit probleem oplossen door de vereisten opnieuw op te geven. Houd er rekening mee dat hoewel de vereiste is verwijderd uit de weergave van de vereisten, het nog steeds correct op apparaten verwerkt is.  

3.  In de **voorwaarde** vervolgkeuzelijst, selecteert u de voorwaarde die u gebruiken om te beoordelen wilt of de gebruiker of het apparaat voldoet aan de installatievereisten. De inhoud van deze lijst varieert op basis van de geselecteerde categorie.  

4.  In de **Operator** vervolgkeuzelijst, selecteert u de operator die wordt gebruikt voor het vergelijken van de geselecteerde voorwaarde en de opgegeven waarde om te beoordelen of de gebruiker of het apparaat voldoet aan de installatievereisten. De beschikbare operators variëren op basis van de geselecteerde voorwaarde.  

    > [!IMPORTANT]  
    >  De beschikbare vereisten zullen variëren afhankelijk van het apparaattype dat gebruikmaakt van het implementatietype.  

5.  In de **waarde** geeft u de waarden die worden gebruikt met de geselecteerde voorwaarde en operator om te beoordelen of de gebruiker of het apparaat voldoet aan de installatievereisten. De beschikbare waarden variëren op basis van de geselecteerde voorwaarde en de geselecteerde operator.  

6.  Kies **OK** opslaan van de vereiste en sluit de **vereiste maken** in het dialoogvenster.  

## <a name="specify-dependencies-for-the-deployment-type"></a>Afhankelijkheden voor het implementatietype opgeven  
 Afhankelijkheden definiëren een of meer implementatietypen van een andere toepassing die moeten worden geïnstalleerd voordat het implementatietype wordt geïnstalleerd. U kunt de afhankelijke implementatietypen automatisch moeten worden geïnstalleerd voordat een implementatietype wordt geïnstalleerd instellen.  

> [!IMPORTANT]  
>  In sommige gevallen is een implementatietype afhankelijk van een implementatietype dat ook afhankelijkheden heeft. Het maximum aantal ondersteunde afhankelijkheden in de keten is vijf.  

1.  Op de **afhankelijkheden** pagina van de wizard implementatietype maken de optie **toevoegen** als u opgeven van de implementatietypen die moeten worden geïnstalleerd wilt voordat dit implementatietype kan worden geïnstalleerd.  

    > [!IMPORTANT]  
    >  U kunt ook nieuwe afhankelijkheden toevoegen op de **afhankelijkheden** tabblad van de *< naam implementatietype\>*  **eigenschappen** in het dialoogvenster.  

2.  In de **afhankelijkheid toevoegen** dialoogvenster Kies **toevoegen**.  

3.  In de **Geef vereiste toepassing** in het dialoogvenster, selecteer een bestaande toepassing en een van de toepassingsimplementatie implementatietypen voor gebruik als afhankelijkheid.  

    > [!TIP]  
    >  U kunt kiezen **weergave** om de eigenschappen van de geselecteerde toepassing of implementatie weer te geven.  

4.  Kies **OK** sluiten de **Geef vereiste toepassing** in het dialoogvenster.  

5.  Als u een afhankelijke toepassing automatisch wordt geïnstalleerd wilt, selecteer **automatisch installeren** naast de afhankelijke toepassing.  

    > [!NOTE]  
    >  Een afhankelijke toepassing hoeft niet te worden geïmplementeerd om te worden automatisch geïnstalleerd.  

6.  In de **afhankelijkheid toevoegen** dialoogvenster onder **naam Afhankelijkheidsgroep**, voer een naam voor het verwijzen naar deze groep toepassingsafhankelijkheden.  

7.  Gebruik eventueel de **prioriteit verhogen** en **prioriteit verlagen** knoppen om de volgorde waarin elke afhankelijkheid wordt geëvalueerd.  

8.  Kies **OK** sluiten de **afhankelijkheid toevoegen** in het dialoogvenster.  

## <a name="confirm-the-deployment-type-settings-and-finish-the-wizard"></a>Instellingen voor het implementatietype bevestigen en voltooi de wizard  

1.  Op de **samenvatting** pagina van de wizard implementatietype maken, Controleer welke acties de wizard gaat ondernemen. Kies **volgende** met het implementatietype maakt of kies een **vorige** naar Ga terug en wijzig de instellingen voor het implementatietype.  

2.  Na de **voortgang** pagina is voltooid, Controleer welke acties de wizard heeft ondernomen, en kies vervolgens **sluiten** om de wizard te voltooien.  

3.  Als u de wizard implementatietype maken hebt gestart vanuit de wizard toepassing maken, gaat u terug naar de **implementatietypen** pagina van de wizard toepassing maken.  

## <a name="set-up-additional-options-for-deployment-types-that-contain-virtual-applications"></a>Aanvullende opties instellen voor implementatietypen die virtuele toepassingen bevatten  
 Gebruik de volgende procedures voor het instellen van aanvullende opties voor implementatietypen die virtuele toepassingen bevatten.  

### <a name="set-up-content-options-for-application-virtualization-app-v-deployment-types"></a>Inhoudopties voor implementatietypen van Application Virtualization (App-V) instellen  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **toepassingen**.  

2.  In de **toepassingen** , selecteert u een toepassing met een App-V-implementatietype. Klik op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

3.  In de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster op de **implementatietypen** tabblad, selecteert u een App-V-implementatietype en kies vervolgens **bewerken**.  

4.  In de *< naam implementatietype\>*  **eigenschappen** in het dialoogvenster op de **inhoud** tabblad instellen van de volgende opties, indien nodig:  

    -   **Inhoud in de clientcache behouden**--Selecteer deze optie om ervoor te zorgen dat de inhoud voor dit implementatietype niet uit de Configuration Manager-clientcache wordt verwijderd.  

    -   **Inhoud laden in App-V-cache vóór starten**--Selecteer deze optie om ervoor te zorgen dat alle inhoud voor de virtuele toepassing in de App-V-cache wordt geladen voordat de toepassing wordt gestart. Deze optie zorgt er ook voor dat de inhoud van de toepassing niet in de cache is vastgemaakt en kan worden verwijderd, zoals wordt vereist.  

5.  Kies **OK** sluiten de *< naam implementatietype\>*  **eigenschappen** in het dialoogvenster.  

6.  Kies **OK** sluiten de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster.  

### <a name="set-up-publishing-options-for-app-v-deployment-types"></a>Publicatieopties voor implementatietypen van App-V instellen  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **toepassingen**.  

3.  In de **toepassingen** , selecteert u een toepassing met een App-V-implementatietype. Klik op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  In de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster op de **implementatietypen** tabblad, selecteert u een App-V-implementatietype en kies vervolgens **bewerken**.  

5.  In de *< naam implementatietype\>*  **eigenschappen** in het dialoogvenster op de **Publishing** tabblad, selecteert u de items in de virtuele toepassing die u wilt publiceren.  

6.  Kies **OK** sluiten de *< naam implementatietype\>*  **eigenschappen** in het dialoogvenster.  

7.  Kies **OK** sluiten de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster.  

## <a name="import-an-application"></a>Een toepassing importeren  
 Gebruik de volgende procedure een toepassing importeren in Configuration Manager. Zie voor meer informatie over het exporteren van een toepassing [beheertaken voor System Center Configuration Manager-toepassingen](../../apps/deploy-use/management-tasks-applications.md).  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.   

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **toepassing importeren**.  

4.  Op de **algemene** pagina van de **wizard toepassing importeren**, kies **Bladeren**, en geef daarna een UNC-pad naar het ZIP-bestand dat de toepassing die u wilt importeren.  

5.  Op de **bestandsinhoud** pagina, selecteert u de actie die wordt uitgevoerd als de toepassing die u probeert te importeren een duplicaat van een bestaande toepassing. U kunt een nieuwe toepassing maken of de duplicaat wordt genegeerd en een nieuwe revisie toevoegen aan de bestaande toepassing.  

6.  Op de **samenvatting** pagina, controleert u de acties worden ondernomen en voltooi de wizard.  

 De nieuwe toepassing wordt weergegeven in het knooppunt **Toepassingen**.  

> [!TIP]  
>  De Windows PowerShell-cmdlet **Import-CMApplication** heeft dezelfde functie als deze procedure. Zie voor meer informatie [Import-CMApplication](https://technet.microsoft.com/library/jj821738.aspx) in Microsoft System Center 2012 Configuration Manager SP1 Cmdlet-verwijzing.  

##  <a name="deployment-types-supported-by-configuration-manager"></a>Implementatietypen die worden ondersteund door Configuration Manager  

|Naam van implementatietype|Meer informatie|  
|--------------------------|----------------------|  
|**Windows Installer (\*MSI-bestand)**|Maakt een implementatietype van een Windows Installer-bestand.|  
|**Windows app-pakket (\*.appx, \*.appxbundle)**|Hiermee wordt een implementatietype gemaakt vanuit een Windows-app-pakketbestand of Windows-app-bundelpakket voor Windows 8, Windows RT of hoger.|  
|**Windows app-pakket (in de Windows Store)**|Maakt een implementatietype voor Windows 8, Windows RT, of later door te geven van een koppeling naar de app in de Windows Store of de store om te selecteren van de gewenste app te bladeren.<br /><br /> Als u wilt dat de app implementeren als een koppeling naar de Windows Store, controleert u of de groepsbeleidsinstelling **de Store-toepassing uitschakelen** is ingesteld op **uitgeschakelde** of **niet geconfigureerd**. Als deze instelling is ingeschakeld, kunnen clients geen verbinding maken met Windows Store om toepassingen te downloaden en installeren.<br /><br /> Windows 8-implementatietypen die gebruikmaken van een koppeling naar een archief worden altijd geëvalueerd vóór andere implementatietypen, ongeacht hun prioriteit.|  
|**Script Installer**|Maakt een implementatietype dat een script dat wordt uitgevoerd op clientapparaten om inhoud te installeren of opgeeft om een actie.|  
|**Microsoft Application Virtualization 4**|Maakt een implementatietype uit een manifest van Microsoft Application Virtualization 4.|  
|**Microsoft Application Virtualization 5**|Hiermee wordt een implementatietype gemaakt vanuit een Microsoft Application Virtualization 5-pakketbestand.|  
|**Windows Phone-app-pakket (\*XAP-bestand)**|Hiermee wordt een implementatietype gemaakt vanuit een Windows Phone-app-pakketbestand|  
|**Windows Phone-app-pakket (in de Windows Phone Store)**|Hiermee wordt een implementatietype gemaakt door een koppeling op te geven naar de app in de Windows Phone Store.|  
|**Windows Mobile Cabinet**|Maakt een implementatietype van een CAB-bestand (Windows Mobile-cabinet) voor Windows Mobile-apparaten.|  
|**App-pakket voor iOS (\*IPA-bestand)**|Hiermee wordt een implementatietype gemaakt vanuit een iOS-app-pakketbestand.|  
|**App-pakket voor iOS uit de App Store**|Hiermee wordt een implementatietype gemaakt door een koppeling op te geven naar de iOS-app in de App Store.|  
|**App-pakket voor Android (\*APK-bestand)**|Hiermee wordt een implementatietype gemaakt vanuit een Android-app-pakketbestand.|  
|**App-pakket voor Android in Google Play**|Hiermee wordt een implementatietype gemaakt door een koppeling op te geven naar de app in Google Play.|  
|**Mac OS X**|Hiermee wordt een implementatietype gemaakt voor Mac-computers vanuit een CMMAC-bestand dat u met behulp van het CMAppUtil-hulpprogramma hebt gemaakt.<br /><br /> Geldt alleen voor Mac-computers met de Configuration Manager-client.|  
|**Webtoepassing**|Hiermee wordt een implementatietype gemaakt dat een koppeling opgeeft naar een webtoepassing. Het implementatietype installeert een snelkoppeling naar de webtoepassing op het apparaat van de gebruiker.<br /><br /> Als u de Intune managed browser hebt geïnstalleerd op iOS- of Android-apparaten die u beheert, kunt u ervoor zorgen dat gebruikers alleen de beheerde browser gebruiken kunnen om de app te openen. Hiervoor gebruikt u een van de volgende indelingen wanneer u een koppeling naar de app door te vervangen opgeeft **http:** met **http-intunemam:** of **https:** met **https-intunemam:**<br /><br /> - **HTTP-intunemam: / / < pad naar de web-app\>**<br /><br /> - **HTTPS-intunemam: / / < pad naar de web-app\>**<br /><br /> U kunt de Configuration Manager-toepassingsvereisten gebruiken om ervoor te zorgen dat apps die u wilt koppelen aan de beheerde browser alleen worden geïnstalleerd op iOS en Android-apparaten.<br /><br /> Zie voor meer informatie over de Intune managed browser [internettoegang beheren met beheerde-browserbeleid](../../apps/deploy-use/manage-internet-access-using-managed-browser-policies.md).|  
|**Windows Installer via MDM (\*.msi)**|Dit installatieprogrammatype kunt u maken en implementeren van Windows Installer gebaseerde apps op pc's waarop Windows 10 wordt uitgevoerd.<br /><br /> De volgende punten zijn van toepassing wanneer u dit type installatieprogramma gebruikt:<br><br>-U kunt slechts één bestand met de extensie .msi uploaden.<br /><br /> -De productcode het bestand en de versie van het product worden gebruikt voor detectie van de app.<br /><br /> -Het standaardgedrag voor opnieuw opstarten van de app wordt gebruikt. Configuration Manager heeft hierop geen invloed.<br /><br /> -Per gebruiker MSI-pakketten worden geïnstalleerd voor één gebruiker.<br /><br /> -Per machine MSI-pakketten worden geïnstalleerd voor alle gebruikers op het apparaat.<br /><br /> -Dual-mode MSI-pakketten voeren momenteel alleen installaties voor alle gebruikers op het apparaat.<br /><br /> -App-updates worden ondersteund wanneer de MSI-productcode van elke versie dezelfde is.|  
