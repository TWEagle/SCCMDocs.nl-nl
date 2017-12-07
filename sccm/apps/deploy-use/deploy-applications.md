---
title: Toepassingen implementeren
titleSuffix: Configuration Manager
description: Maken van een implementatietype of implementatie simuleren voor een toepassing met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 12/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
caps.latest.revision: "10"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 97d1ac775a3b38f63372f0ab01243dfdfeb4edb5
ms.sourcegitcommit: 52b956cfe32c3f06ae68d6ba6fc3244ce5a66325
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/06/2017
---
# <a name="deploy-applications-with-system-center-configuration-manager"></a>Implementeren van toepassingen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u een System Center Configuration Manager-toepassing implementeren kunt, moet u ten minste één implementatietype voor de toepassing maken. Zie voor meer informatie over het maken van toepassingen en implementatietypen [toepassingen maken](/sccm/apps/deploy-use/create-applications).

 U kunt de implementatie van een toepassing ook simuleren. Met dit type implementatie test u de toepasselijkheid van een toepassingsimplementatie op computers zonder dat het nodig is de toepassing te installeren of te verwijderen. Een gesimuleerde implementatie de detectiemethode, vereisten en afhankelijkheden voor een implementatietype geëvalueerd en rapporteert de resultaten in de **implementaties** knooppunt van de **bewaking** werkruimte. Zie voor meer informatie [toepassingsimplementaties simuleren](/sccm/apps/deploy-use/simulate-application-deployments).

> [!IMPORTANT]
>  U kunt implementeren (installeren of verwijderen)-toepassingen, maar geen pakketten of software-updates vereist. MDM ingeschreven apparaten bieden ook geen ondersteuning voor gesimuleerde implementaties, gebruikerservaring en programmatie-instellingen.

## <a name="deploy-an-application"></a>Een toepassing implementeren

1.  Ga in de Configuration Manager-console naar **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.

2.  Selecteer, in de lijst **Toepassingen** de toepassing die u wenst te implementeren. Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.

### <a name="specify-general-information-about-the-deployment"></a>Geef algemene informatie over de implementatie

Op de **algemene** pagina van de wizard Software implementeren geeft u de volgende informatie:

- **Software**  
U ziet nu de toepassing te implementeren. U kunt op **Bladeren** klikken om een andere toepassing te selecteren.
- **Verzameling**  
Klik op **Bladeren** om de verzameling voor het implementeren van de toepassing te selecteren.
- **Gebruik standaarddistributiepuntengroepen die gekoppeld zijn aan deze verzameling**  
Selecteer deze optie als u wilt opslaan van inhoud van de toepassing op de verzameling standaard distributiepuntengroep. Als u de geselecteerde verzameling niet hebt gekoppeld aan een distributiepuntgroep, wordt deze optie grijs weergegeven.
- **Inhoud voor afhankelijkheden automatisch distribueren**  
Als deze optie is ingeschakeld en als er implementatietypes zijn die in de toepassing afhankelijkheden bevatten, klikt u vervolgens de afhankelijke inhoud ook naar distributiepunten verzonden.

    >[!IMPORTANT]
    > Indien u de afhankelijke toepassing updatet nadat de primaire toepassing geïmplementeerd werd, zal nieuwe inhoud voor de afhankelijkheid niet automatisch worden verdeeld.

- **Commentaren (optioneel)**  
Voer eventueel een beschrijving voor deze implementatie.

### <a name="specify-content-options-for-the-deployment"></a>Inhoudopties voor de implementatie opgeven

Op de **inhoud** pagina, klikt u op **toevoegen** om toe te voegen inhoud die is gekoppeld aan de implementatie naar distributiepunten of distributiepuntengroepen. Als u hebt geselecteerd **gebruik standaarddistributiepunten gekoppeld aan deze verzameling** op de **algemene** pagina, en vervolgens deze optie wordt automatisch ingevuld en kan alleen worden gewijzigd door een lid van de beveiligingsrol van beheerder van de toepassing.

### <a name="specify-deployment-settings"></a>Implementatie-instellingen opgeven

Op de **implementatie-instellingen** pagina van de wizard Software implementeren geeft u de volgende informatie:

- **Actie**  
Kies in de vervolgkeuzelijst of deze implementatie is bedoeld om **installeren** of **verwijderen** de toepassing.

    > [!NOTE]
    >  Als een toepassing tweemaal geïmplementeerd is op een apparaat, enerzijds met actie van **installeren** en anderzijds met een actie van **verwijderen**, de implementatie van de toepassing met een actie van **installeren** voorrang.

U kunt de actie van een implementatie niet wijzigen nadat ze werd gecreëerd.

- **Doel**  
Kies een van de volgende opties in de vervolgkeuzelijst:
    - **Beschikbaar**  
    Als de toepassing wordt geïmplementeerd voor een gebruiker, wordt de gebruiker ziet de gepubliceerde toepassing in Software Center en kan deze op verzoek installeren.
    - **Vereist**  
    De toepassing is automatisch geïmplementeerd volgens de planning. Als de implementatiestatus van de toepassing niet verborgen is, kan iedereen met behulp van de toepassing de implementatiestatus bijhouden en de toepassing installeren vanuit Software Center vóór de deadline.

    > [!NOTE]   
    >  Als de implementatie-actie ingesteld is op **Verwijderen**, wordt het doel van de implementatie automatisch ingesteld op **Vereist** en kan dit niet worden gewijzigd.  

- **Automatisch implementeren volgens schema of een gebruiker is aangemeld of niet**  
Als de implementatie voor een gebruiker, selecteert u deze optie om de toepassing op de primaire apparaten van de gebruiker te implementeren. Deze instelling vereist niet dat de gebruiker zich aanmeldt vóór de implementatie draait. Selecteer deze optie niet als de gebruiker invoer moet leveren om de installatie te vervolledigen. Deze optie is enkel beschikbaar als de implementatie een **Vereist**doel heeft.

- **Ontwaakpakketten verzenden**  
Als het implementatiedoel is ingesteld op **vereist** en deze optie is geselecteerd, wordt een ontwaakpakket verzonden naar computers vóór de implementatie is geïnstalleerd. Dit pakket uit de slaapstand wordt de computers deadline van de installatie. Voordat u deze optie kunt gebruiken, moeten computers en netwerken zijn geconfigureerd voor Wake On LAN.
- **Laat clients toe op een internetverbinding inhoud te downloaden na de installatiedeadline, waarvoor extra kosten met zich kan brengen**  
Deze optie is alleen beschikbaar voor implementaties met als doel **vereist**.
- **Alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type automatisch sluiten**  
Zie voor meer informatie over het configureren van een lijst met uitvoerbare bestanden die voorkomen een toepassing installeert dat kunnen **controleren om uitvoerbare bestanden uit te voeren voordat u een toepassing installeert** verderop in dit onderwerp.
- **Goedkeuring door beheerder vereisen als gebruikers deze toepassing aanvragen**  
Als deze optie is ingeschakeld, kan de beheerder van de verzoeken van gebruikers voor de toepassing moet goedkeuren voordat deze kan worden geïnstalleerd. Deze optie wordt grijs weergegeven wanneer het implementatiedoel **vereist** of wanneer de toepassing wordt geïmplementeerd op een apparatenverzameling.

    > [!NOTE]
    >  Verzoeken voor gebruik van een toepassing worden weergegeven in het knooppunt **Goedkeuringsaanvragen** onder **Toepassingbeheer** in de werkruimte **Softwarebibliotheek** . Als een aanvraag is niet binnen 45 dagen werd goedgekeurd, wordt deze verwijderd. Bovendien de Configuration Manager-client opnieuw installeert, kan verzoeken van in afwachting van goedkeuring annuleren.
    >  Nadat u een toepassing voor de installatie hebt goedgekeurd, kunt u vervolgens de aanvraag weigeren door te klikken op **weigeren** in de Configuration Manager-console (voorheen deze knop is lichter gekleurd weergegeven na de goedkeuring).
    >  Deze actie wordt de toepassing worden verwijderd van apparaten die niet, maar deze voorkomen dat gebruikers nieuwe exemplaren van de toepassing installeren vanuit Software Center.

- **Automatisch elke vervangen versie van deze toepassing updaten**  
Als deze optie is geselecteerd, wordt elke vervangen versie van de toepassing bijgewerkt door de vervangende toepassing.

### <a name="specify-scheduling-settings-for-the-deployment"></a>Schema-instellingen voor de implementatie opgeven

Op de **planning** pagina van de Software implementeren wizard, het tijdstip waarop deze toepassing worden geïmplementeerd of beschikbaar is voor clientapparaten instellen.
De opties op deze pagina verschillen afhankelijk van of de implementatieactie ingesteld is op **beschikbaar** of **vereist**.

In sommige gevallen is het raadzaam om gebruikers meer tijd voor implementaties van toepassingen installeren die zijn vereist of software-updates buiten een deadlines die u instelt. Dit is normaal gesproken vereist wanneer een computer gedurende langere tijd is uitgeschakeld en moet een groot aantal updates of implementaties van toepassingen te installeren. Bijvoorbeeld, als een gebruiker heeft geretourneerd van vakantie, wellicht ze wacht gedurende een lange periode als achterstallig toepassingsimplementaties zijn geïnstalleerd. U kunt nu een respijtperiode afdwingen door Configuration Manager-clientinstellingen implementeren naar een verzameling om dit probleem op te lossen definiëren.

Voor het configureren van de respijtperiode is, moet u de volgende acties uitvoeren:

- Op de **Computeragent** pagina configureren van clientinstellingen, de nieuwe eigenschap **respijtperiode voor afdwingen na de implementatie (uren) deadline** met een waarde tussen **1** en **120** uur.
- Op de **planning** pagina in een nieuwe implementatie van de vereiste toepassing of in de eigenschappen van een bestaande implementatie, selecteert u het selectievakje **afdwingen van deze implementatie op basis van gebruikersvoorkeuren tot de respijtperiode die is gedefinieerd in de clientinstellingen uitstellen**. De respijtperiode afdwingen wordt gebruikt door alle implementaties die u hebt dit vakje is ingeschakeld en zijn bedoeld voor apparaten die u ook de client-instelling geïmplementeerd.

Nadat de toepassing geïnstalleerd deadline wordt bereikt, de toepassing wordt geïnstalleerd in het eerste niet-zakelijk venster die de gebruiker tot die respijtperiode geconfigureerd. De gebruiker kan echter nog steeds openen van Software Center en de toepassing op elk gewenst moment die ze willen installeren. Nadat de respijtperiode is verlopen, hersteld afdwinging normaal gedrag voor implementaties van achterstallige.

Als de toepassing die u implementeert een andere toepassing vervangt, kunt u de installatiedeadline instellen wanneer gebruikers de nieuwe toepassing krijgen. Dit doen met behulp van de instelling **Installatiedeadline** om gebruikers met de vervangen toepassing te upgraden.

### <a name="specify-user-experience-settings-for-the-deployment"></a>Geef instellingen voor gebruikerservaring voor de implementatie


Op de **gebruikerservaring** pagina van de wizard Software implementeren geeft u informatie over hoe gebruikers met de installatie van de toepassing werken kunnen.

Als u toepassingen op Windows Embedded apparaten implementeert, waarvan de schrijffilter ingeschakeld is, kunt u opgeven om de toepassing te installeren op de tijdelijke overlay en later wijzigingen doorvoeren, of de wijzigingen doorvoeren op de deadline van de installatie of tijdens een onderhoudsvenster. Wanneer u wijzigingen tegen de installatiedeadline of tijdens een onderhoudsvenster doorvoert, moet u het apparaat opnieuw te starten. De wijzigingen behouden blijven op het apparaat.

>[!NOTE]
    >  Wanneer u een toepassing implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster. Zie voor meer informatie over hoe onderhoudvensters worden gebruikt wanneer u toepassingen voor Windows Embedded-apparaten implementeert, [maken Windows Embedded-toepassingen](../../apps/get-started/creating-windows-embedded-applications.md).
    > De opties **Software-installatie** en **Systeem opnieuw opstarten (indien nodig om de installatie te vervolledigen)** worden niet gebruikt als het implementatiedoel ingesteld is op **Beschikbaar**. U kunt ook het niveau van melding configureren dat een gebruiker ziet wanneer de toepassing is geïnstalleerd.

### <a name="specify-alert-options-for-the-deployment"></a>Opties voor de implementatie opgeven

Op de **waarschuwingen** pagina van de wizard Software implementeren hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren instellen. U kunt drempels configureren voor het rapporteren van waarschuwingen en de rapportering van de duur van de implementatie uitschakelen.

### <a name="associate-the-deployment-with-an-ios-app-configuration-policy"></a>De implementatie koppelen aan een iOS-app-configuratiebeleid

Op de **Configuratiebeleidsregels** pagina, klikt u op **nieuw** deze implementatie koppelen aan een iOS-app-configuratiebeleid (als u deze hebt gemaakt). Zie voor meer informatie over dit type beleid [iOS-apps configureren met configuratiebeleidsregels](../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).

### <a name="finish-up"></a>Voltooien

Op de **samenvatting** pagina bekijken van de wizard Software implementeren de acties die worden uitgevoerd tijdens deze implementatie en klik vervolgens op **volgende** om de wizard te voltooien.

De nieuwe implementatie wordt weergegeven in de **implementaties** lijst de **implementaties** knooppunt van de **bewaking** werkruimte. U kunt de kenmerken van deze implementatie bewerken of de implementatie wissen van het tabblad **Implementaties** van het detailpaneel van de toepassing.

## <a name="delete-an-application-deployment"></a>Implementatie van een toepassing verwijderen

1.  Ga in de Configuration Manager-console naar **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.
3.  In de **toepassingen** , selecteert u de toepassing die gebruikmaakt van de implementatie die u hebt verwijderd.
4.  Selecteer op het tabblad **Implementaties** van de lijst *<toepassingsnaam\>* de toepassingsimplementatie die u wilt wissen. Klik op de **implementatie** tabblad, in de **implementatie** groep, klikt u op **verwijderen**.

Wanneer u een toepassingsimplementatie wist, worden instanties van de toepassing die reeds geïnstalleerd zijn niet verwijderd. Deze om toepassingen te verwijderen, moet u de toepassing op computers met implementeren **verwijderen**. Als u een toepassingsimplementatie wist of een resource verwijdert uit de verzameling waarnaar u implementeert, is de toepassing niet meer zichtbaar in Software Center.

## <a name="user-notifications-for-required-deployments"></a>Meldingen voor gebruikers voor vereiste implementaties
Wanneer u vereiste software van ontvangt de **uitstellen en Help me herinneren** instelt, kunt u in de volgende lijst in de vervolgkeuzelijst van waarden:
- **Later**  
Hiermee geeft u op dat meldingen worden gepland op basis van de instellingen voor meldingen geconfigureerd in de clientagentinstellingen.
- **Vaste tijd**  
Hiermee geeft u op dat de melding wordt gepland om opnieuw op de geselecteerde tijd weer te geven. Bijvoorbeeld, als u 30 minuten selecteert, de melding wordt weergegeven in 30 minuten opnieuw.

![Computer Agent pagina in de clientagentinstellingen](media/ComputerAgentSettings.png)

De maximale uitstellen is altijd op basis van tijd op de melding ingestelde waarden in de clientagentinstellingen op elk moment langs de tijdlijn voor implementatie. Bijvoorbeeld, als de **langer dan 24 uur deadline voor implementatie, gebruikers herinneren elke (uur)** instellen op de **Computeragent** pagina is geconfigureerd voor 10 uur en meer dan 24 uur vóór de deadline is wanneer het dialoogvenster wordt gestart, u zou worden gepresenteerd met een set opties voor bewerkingen worden uitgesteld tot maar nooit meer dan 10 uur. Als de deadline nadert, ziet u het dialoogvenster minder mogelijkheden consistent zijn met de relevante instellingen voor Clientagent voor elk onderdeel van de implementatie-tijdlijn.

Daarnaast voor een implementatie met hoog risico, zoals een takenreeks die een besturingssysteem implementeert is de gebruikerservaring van de melding nu ingrijpender. In plaats van een melding tijdelijke taakbalk worden een dialoogvenster zoals hieronder wordt weergegeven op uw computer telkens wanneer u gewaarschuwd dat essentieel softwareonderhoud is vereist:

![Dialoogvenster voor vereiste Software](media/client-toast-notification.png)

## <a name="how-to-check-for-running-executable-files-before-installing-an-application"></a>Hoe moet worden gecontroleerd om uitvoerbare bestanden uit te voeren voordat u een toepassing installeert

>[!Tip]
> Deze functie is geïntroduceerd in versie 1702 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1706, deze functie is niet langer een voorlopige versie.

In de **eigenschappen** in het dialoogvenster van een implementatie hebt getypt, op de **gedrag installeren** tabblad kunt u een of meer uitvoerbare bestanden die als actief is, de installatie van het implementatietype blokkeren opgeven. De gebruiker moet de lopende uitvoerbaar bestand sluiten (of het automatisch kan worden gesloten voor implementaties met als doel vereist) voordat de implementatie van het type kan worden geïnstalleerd. Configureer dit als volgt:

1. Open de **eigenschappen** in het dialoogvenster voor eender welk implementatietype.
2. Op de **gedrag installeren** tabblad van de  *<deployment type name>*  **eigenschappen** in het dialoogvenster, klikt u op **toevoegen**.
3. In de **toevoegen of uitvoerbaar bestand bewerken** dialoogvenster en voer de naam van het uitvoerbare bestand dat, als uitgevoerd, blokken van de toepassing installeren. U kunt eventueel ook een beschrijvende naam voor de toepassing te herkennen in de lijst invoeren.
4. Klik op **OK**, sluit de  *<deployment type name>*  **eigenschappen** in het dialoogvenster.
5. Volgende, wanneer u een toepassing implementeert op de **implementatie-instellingen** pagina van de Wizard Software implementeren, selecteer **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type**, gaat u verder met de toepassing implementeren.

Nadat de toepassing client-pc's bereikt, geldt het volgende gedrag:

- Als de toepassing is geïmplementeerd als **beschikbaar**, en een eindgebruiker probeert te installeren, wordt ze gevraagd om te sluiten van alle actieve uitvoerbare bestanden opgegeven voordat ze de installatie kunnen voortzetten.

- Als de toepassing is geïmplementeerd als **vereist**, en de optie **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type** is geselecteerd, wordt er een dialoogvenster waarin ze worden geïnformeerd dat uitvoerbare bestanden die u hebt opgegeven automatisch worden gesloten wanneer de deadline van de installatie van de toepassing is bereikt. U kunt plannen dat deze dialoogvensters in **clientinstellingen** > **Computeragent**. Als u niet dat de eindgebruiker deze berichten te zien wilt, selecteert u **verbergen in Software Center en alle meldingen verbergen** op de **gebruikerservaring** tabblad van de implementatie-eigenschappen.

- Als de toepassing is geïmplementeerd als **vereist** en de optie **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type** niet is geselecteerd, wordt de installatie van de app is mislukt als een of meer van de opgegeven toepassingen worden uitgevoerd.

## <a name="for-more-information"></a>Voor meer informatie

   -  [Instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md)  
   -  [Clientinstellingen configureren](../../core/clients/deploy/configure-client-settings.md)
