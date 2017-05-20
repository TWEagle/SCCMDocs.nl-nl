---
title: Toepassingen implementeren | Microsoft-documenten
description: Maak een implementatietype te detecteren of implementatie simuleren voor een toepassing met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 0eaa1d13e9c273a6649f50d73fb357f04464d94c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="deploy-applications-with-system-center-configuration-manager"></a>Implementeren van toepassingen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Voordat u een System Center Configuration Manager-toepassing implementeren kunt, moet u ten minste één implementatietype voor de toepassing maken. Zie voor meer informatie over het maken van toepassingen en implementatietypen [toepassingen maken ](../../apps/deploy-use/create-applications.md).

 U kunt de implementatie van een toepassing ook simuleren. Met dit type implementatie test u de toepasselijkheid van een toepassingsimplementatie op computers zonder dat het nodig is de toepassing te installeren of te verwijderen. Een gesimuleerde implementatie evalueert de detectiemethode, vereisten en afhankelijkheden voor een implementatietype te detecteren en de resultaten worden vermeld in de **implementaties** knooppunt van de **bewaking** werkruimte. Zie voor meer informatie [toepassingsimplementaties simuleren ](../../apps/deploy-use/simulate-application-deployments.md).

> [!IMPORTANT]
>  U kunt implementeren (installeren of verwijderen)-toepassingen, maar geen pakketten of software-updates vereist. MDM ingeschreven apparaten bieden ook geen ondersteuning voor gesimuleerde implementaties gebruikerservaring en programmatie-instellingen.

## <a name="deploy-an-application"></a>Een toepassing implementeren

1.  Ga in de Configuration Manager-console naar **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.

2.  Selecteer, in de lijst **Toepassingen** de toepassing die u wenst te implementeren. Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.

### <a name="specify-general-information-about-the-deployment"></a>Geef algemene informatie over de implementatie

Op de **algemeen** pagina van de wizard Software implementeren, geef de volgende informatie:

- **Software**--hier worden de toepassing te implementeren. U kunt op **Bladeren** klikken om een andere toepassing te selecteren.
- **Verzameling**--klikt u op **Bladeren** om de verzameling voor het implementeren van de toepassing te selecteren.
- **Gebruik standaard distributiepuntengroepen die gekoppeld zijn aan deze verzameling**--Selecteer deze optie als u wilt dat de inhoud van de toepassing worden opgeslagen op de verzameling standaard distributiepuntengroep. Als u de geselecteerde verzameling niet hebt gekoppeld aan een distributiepuntgroep, deze optie is niet beschikbaar.
- **Verdeel automatisch inhoud voor afhankelijkheden**--als dit is ingeschakeld en als er implementatietypes zijn die de toepassing afhankelijkheden bevatten, klikt u vervolgens de afhankelijke inhoud ook naar distributiepunten verzonden.

    >[!IMPORTANT]
    > Indien u de afhankelijke toepassing updatet nadat de primaire toepassing geïmplementeerd werd, zal nieuwe inhoud voor de afhankelijkheid niet automatisch worden verdeeld.

- **Commentaren (optioneel)** oer optioneel een beschrijving van deze implementatie in.

### <a name="specify-content-options-for-the-deployment"></a>Geef opties voor de implementatie van inhoud

Op de **inhoud** pagina, klikt u op **toevoegen** toevoegen van de inhoud gekoppeld aan de implementatie naar distributiepunten of distributiepuntengroepen. Als u hebt geselecteerd **Gebruik standaard distributiepunten gekoppeld aan deze verzameling** op de **algemeen** pagina en vervolgens deze optie wordt automatisch ingevuld worden en kan alleen worden gewijzigd door een lid van de toepassingsbeheerdersrol.

### <a name="specify-deployment-settings"></a>Implementatie-instellingen opgeven

Op de **implementatie-instellingen** pagina van de wizard Software implementeren, geef de volgende informatie:

- **Actie**--Kies uit de vervolgkeuzelijst of deze implementatie bedoeld is voor **installeren** of **verwijderen** de toepassing.

    > [!NOTE]
    >  Indien een toepassing tweemaal geïmplementeerd is op een apparaat, enerzijds met een actie van **Installeren** en anderzijds met een actie van **Verwijderen**, zal de toepassingsimplementatie met de actie **Installeren** prioriteit hebben.

U kunt de actie van een implementatie niet wijzigen nadat ze werd gecreëerd.

- **Doel**--Kies uit de vervolgkeuzelijst een van de volgende opties:
    - **Beschikbare**--als de toepassing wordt geïmplementeerd voor een gebruiker, de gebruiker ziet de gepubliceerde toepassing in Software Center en kan deze op aanvraag installeren.
    - **Vereist**--de toepassing is automatisch geïmplementeerd volgens de planning. Als de status van de toepassingsimplementatie niet verborgen is, kan iedereen met behulp van de toepassing de implementatiestatus bijhouden en installeer de toepassing vanuit Software Center vóór de deadline.

    > [!NOTE]   
    >  Als de implementatie-actie ingesteld is op **Verwijderen**, wordt het doel van de implementatie automatisch ingesteld op **Vereist** en kan dit niet worden gewijzigd.  

- **Implementeer automatisch volgens planning of op een gebruiker is aangemeld of niet**--als de implementatie aan een gebruiker is, selecteert u deze optie om de toepassing op de primaire apparaten van de gebruiker te implementeren. Deze instelling vereist niet dat de gebruiker zich aanmeldt vóór de implementatie draait. Selecteer deze optie niet als de gebruiker invoer moet leveren om de installatie te vervolledigen. Deze optie is enkel beschikbaar als de implementatie een **Vereist**doel heeft.


- **Verzenden van ontwaakpakketten**--als het implementatiedoel is ingesteld op **vereist** en deze optie is geselecteerd, wordt een ontwaakpakket verzonden naar computers vóór de implementatie wordt geïnstalleerd. Dit pakket wordt de computers weer deadline van de installatie. Voordat u deze optie kunt gebruiken, moeten computers en netwerken zijn geconfigureerd voor Wake On LAN.
- **Laat clients toe op een internetverbinding inhoud te downloaden na de installatiedeadline, waarvoor extra kosten in rekening kan worden**--deze optie is alleen beschikbaar voor implementaties met als doel van **vereist**.
- **Automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type** - voor meer informatie over het configureren van een lijst met uitvoerbare bestanden die kan verhinderen dat een toepassing installeert, Zie **controleren voor het uitvoeren van uitvoerbare bestanden voordat u een toepassing installeert** verderop in dit onderwerp.
- **Goedkeuring door beheerder vereisen als gebruikers deze toepassing aanvragen**--als deze optie is geselecteerd, de beheerder geven verzoeken van gebruikers voor de toepassing moet goedkeuren voordat deze kan worden geïnstalleerd. Deze optie is niet beschikbaar wanneer het implementatiedoel **vereist** of wanneer de toepassing wordt geïmplementeerd op een apparatenverzameling.

    > [!NOTE]
    >  Verzoeken voor gebruik van een toepassing worden weergegeven in het knooppunt **Goedkeuringsaanvragen** onder **Toepassingbeheer** in de werkruimte **Softwarebibliotheek** . Als een aanvraag niet binnen 45 dagen werd goedgekeurd, wordt het verwijderd. Daarnaast de Configuration Manager-client opnieuw installeert, kan alle in afwachting van goedkeuringsaanvragen annuleren.
    >  Nadat u een toepassing voor de installatie hebt goedgekeurd, kunt u vervolgens de aanvraag weigeren door te klikken op **weigeren** in de Configuration Manager-console (voorheen deze knop niet beschikbaar na goedkeuring).
    >  Deze actie wordt niet van apparaten verwijderd van de toepassing, maar deze niet meer gebruikers nieuwe exemplaren van de toepassing wordt geïnstalleerd vanuit Software Center.



- **Automatisch elke vervangen versie van deze toepassing updaten**--als deze optie is geselecteerd, elke vervangen versie van de toepassing geüpdatet worden door de vervangende toepassing.

### <a name="specify-scheduling-settings-for-the-deployment"></a>Planning voor de implementatie-instellingen opgeven

Op de **planning** pagina van de Software implementeren wizard, de tijd waarop deze toepassing wordt geïmplementeerd of beschikbaar gesteld voor clientapparaten instellen.
De opties op deze pagina zullen verschillen afhankelijk van of de implementatieactie ingesteld is op **Beschikbaar** of **Vereist**.

In sommige gevallen is het raadzaam om gebruikers meer tijd voor implementaties van toepassingen installeren die zijn vereist of software-updates buiten een deadlines die u instelt. Dit is meestal zijn vereist wanneer een computer gedurende langere tijd is uitgeschakeld en moet voor het installeren van een groot aantal updates of implementaties van toepassingen. Als een gebruiker is alleen van vakantie geretourneerd, moeten ze mogelijk wacht gedurende een lange periode zoals implementaties van achterstallige toepassingen zijn geïnstalleerd. Om te helpen bij het oplossen van dit probleem, kunt u nu een respijtperiode afdwinging definiëren door de instellingen voor Configuration Manager-client implementeren op een verzameling.

De respijtperiode configureren, moet u de volgende acties uitvoeren:

- Op de **Computeragent** pagina configureren van instellingen van de client de nieuwe eigenschap **respijtperiode voor afdwinging na implementatie deadline (uren)** met een waarde tussen **1** en **120** uur.
- Op de **planning** pagina in een nieuwe implementatie van de vereiste toepassing, of in de eigenschappen van een bestaande implementatie, schakelt u het **stellen afdwinging van deze implementatie volgens gebruikersvoorkeuren tot de respijtperiode gedefinieerd in de clientinstellingen**. De respijtperiode afdwinging wordt gebruikt door alle implementaties die dit vakje is ingeschakeld en zijn bedoeld voor apparaten waarop u ook de instelling voor client geïmplementeerd.

Nadat de toepassing installeren deadline is bereikt, de toepassing wordt geïnstalleerd in het eerste niet-business-venster dat de gebruiker tot die respijtperiode geconfigureerd. De gebruiker kan echter nog steeds Software Center wordt geopend en de toepassing op elk gewenst moment die ze willen installeren. Zodra de respijtperiode is verlopen, hersteld afdwinging normale gedrag voor achterstallige implementaties.

Als de toepassing die u implementeert een andere toepassing vervangt, kunt u de gewenste deadline instellen wanneer gebruikers de nieuwe toepassing zullen krijgen. Dit doen met de instelling **Installatiedeadline** gebruikers met de vervangen toepassing bijwerken.

### <a name="specify-user-experience-settings-for-the-deployment"></a>Geef instellingen voor gebruikerservaring voor de implementatie


Op de **gebruikerservaring** pagina informatie over hoe gebruikers met de installatie van de toepassing interacteren kunnen opgeven van de wizard Software implementeren.

Als u toepassingen op Windows Embedded apparaten implementeert, waarvan de schrijffilter ingeschakeld is, kunt u opgeven om de toepassing te installeren op de tijdelijke overlay en later wijzigingen doorvoeren, of de wijzigingen doorvoeren op de deadline van de installatie of tijdens een onderhoudsvenster. Wanneer u wijzigingen tegen de installatiedeadline of tijdens een onderhoudsvenster doorvoert, moet u het apparaat opnieuw opstarten. De wijzigingen behouden blijven op het apparaat.

>[!NOTE]
    >  Wanneer u een toepassing implementeert op een Windows Embedded-apparaat, moet u ervoor zorgen dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster. Zie voor meer informatie over hoe onderhoudvensters worden gebruikt wanneer u toepassingen voor Windows Embedded-apparaten implementeert, [Windows Embedded maken toepassingen](../../apps/get-started/creating-windows-embedded-applications.md).
    > De opties **Software-installatie** en **Systeem opnieuw opstarten (indien nodig om de installatie te vervolledigen)** worden niet gebruikt als het implementatiedoel ingesteld is op **Beschikbaar**. U kunt ook het niveau van melding configureren dat een gebruiker ziet wanneer de toepassing is geïnstalleerd.

### <a name="specify-alert-options-for-the-deployment"></a>Geef opties op voor waarschuwingen voor de implementatie

Op de **waarschuwingen** van de wizard Software implementeren instellen hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren zullen. U kunt drempels configureren voor het rapporteren van waarschuwingen en de rapportering van de duur van de implementatie uitschakelen.

### <a name="associate-the-deployment-with-an-ios-app-configuration-policy"></a>De implementatie koppelen aan een configuratiebeleid voor iOS-app

Op de **App configuratiebeleid** pagina, klikt u op **New** deze implementatie koppelen aan een configuratiebeleid voor iOS-app (als u deze hebt gemaakt). Zie voor meer informatie over dit type beleid [iOS-apps configureren met app-configuratiebeleid](../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).

### <a name="finish-up"></a>Voltooien van

Op de **samenvatting** pagina van de wizard Software implementeren, controleert u de acties die zullen uitgevoerd worden bij deze implementatie, en klik vervolgens op **volgende** om de wizard te voltooien.

De nieuwe implementatie zal weergegeven worden in de lijst **Implementaties** in het knooppunt **Implementaties** van de werkruimte **Controle** . U kunt de kenmerken van deze implementatie bewerken of de implementatie wissen van het tabblad **Implementaties** van het detailpaneel van de toepassing.

## <a name="delete-an-application-deployment"></a>Implementatie van een toepassing verwijderen

1.  Ga in de Configuration Manager-console naar **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.

3.  In de **toepassingen** , selecteert u de toepassing die gebruikmaakt van de implementatie worden verwijderd.

4.  Selecteer op het tabblad **Implementaties** van de lijst *<toepassingsnaam\>* de toepassingsimplementatie die u wilt wissen. Klik vervolgens op de **implementatie** tabblad, in de **implementatie** groep, klikt u op **verwijderen**.

 Wanneer u een toepassingsimplementatie wist, worden instanties van de toepassing die reeds geïnstalleerd zijn niet verwijderd. Deze om toepassingen te verwijderen, moet u de toepassing op computers met implementeren **verwijderen**. Als u een toepassingsimplementatie wist of een resource verwijdert uit de verzameling waarnaar u implementeert, is de toepassing niet meer zichtbaar in Software Center.

## <a name="user-notifications-for-required-deployments"></a>Meldingen voor gebruikers voor vereiste implementaties
Wanneer u vereiste software van ontvangt de **uitstellen en Help me herinneren** stellen, kunt u in de volgende vervolgkeuzelijst lijst met waarden:
- **Later**--geeft aan dat meldingen worden gepland op basis van de instellingen voor meldingen geconfigureerd in de instellingen voor Clientagent.
- **Vaste tijd**--geeft aan dat de melding wordt gepland om opnieuw na de geselecteerde periode weer te geven. Als u 30 minuten selecteert, kunt u voor de melding, wordt weergegeven in 30 minuten opnieuw.

![Agent-pagina in de clientagentinstellingen computer](media/ComputerAgentSettings.png)

De maximale uitstellen tijd is altijd gebaseerd op de melding ingestelde waarden in de clientagentinstellingen op elk moment langs de tijdlijn voor implementatie. Bijvoorbeeld, als de **groter is dan 24 uur deadline voor implementatie, gebruikers herinneren elke (uur)** instellen op de **Computeragent** pagina is geconfigureerd voor 10 uur en het is langer dan 24 uur vóór de deadline wanneer het dialoogvenster wordt gestart, u zou worden gepresenteerd met een set opties uitstellen tot maar nooit meer dan 10 uur. Als de deadline nadert, wordt het dialoogvenster minder opties consistent zijn met de relevante clientagentinstellingen voor elk onderdeel van de implementatie-tijdlijn weergegeven.

Daarnaast voor een hoog risico implementatie, zoals een takenreeks die een besturingssysteem implementeert is de gebruikerservaring van de melding nu ingrijpender. In plaats van een melding tijdelijke taakbalk een dialoogvenster zoals hieronder wordt weergegeven op uw computer telkens wanneer u ontvangt een melding over essentieel softwareonderhoud is vereist:

![Dialoogvenster voor vereiste Software](media/client-toast-notification.png)

## <a name="how-to-check-for-running-executable-files-before-installing-an-application"></a>Het controleren van voor het uitvoeren van uitvoerbare bestanden voordat de installatie van een toepassing

>[!Tip]
>Met versie 1702 geïntroduceerd, is dit een voorlopige versie-functie. Als u wilt inschakelen, Zie [voorlopige functies in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/servers/manage/pre-release-features).

In de **eigenschappen** in het dialoogvenster van een implementatie hebt getypt, op de **gedrag installeren** tabblad kunt u een meer uitvoerbare bestanden die als uitgevoerd, wordt de installatie van het implementatietype geblokkeerd. De gebruiker moet het actief uitvoerbaar bestand sluiten (of het automatisch kan worden gesloten voor implementaties met als doel vereist) voor de implementatie van het type kan worden geïnstalleerd. Te configureren:

1. Open de **eigenschappen** in het dialoogvenster voor eender welk implementatietype.
2. Op de **gedrag installeren** tabblad van het  *<deployment type name>*  **eigenschappen** in het dialoogvenster, klikt u op **toevoegen**.
3. In de **toevoegen of bewerken uitvoerbaar bestand** dialoogvenster, voert u de naam van het uitvoerbare bestand dat als actief is, wordt de installatie van de toepassing geblokkeerd. U kunt eventueel ook een beschrijvende naam voor de toepassing te herkennen in de lijst invoeren.
4. Klik op **OK**, sluit de  *<deployment type name>*  **eigenschappen** in het dialoogvenster.
5. Volgende, wanneer u een toepassing implementeert op de **implementatie-instellingen** pagina van de Wizard Software implementeren, selecteer **automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type**, gaat u door met de toepassing implementeert.

Nadat de toepassing client-pc's bereikt, wordt het volgende van toepassing:

- Als de toepassing is geïmplementeerd als **beschikbaar**, en een eindgebruiker probeert te installeren, wordt ze gevraagd om te sluiten van een actieve uitvoerbare bestanden die u hebt opgegeven voordat de installatie kunt voortzetten.

- Als de toepassing is geïmplementeerd als **vereist**, en de optie **automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type** is geselecteerd, zien ze een dialoogvenster dat hen informeert dat uitvoerbare bestanden die u hebt opgegeven automatisch gesloten wordt na het verstrijken van de installatiedeadline voor de toepassing. U kunt plannen dat deze dialoogvensters in **clientinstellingen** > **Computeragent**. Als u niet dat de eindgebruiker deze berichten te zien wilt, selecteert u **verbergen in Software Center en alle meldingen** op de **gebruikerservaring** tabblad van de implementatie-eigenschappen.

- Als de toepassing is geïmplementeerd als **vereist** en de optie **automatisch sluiten eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad installatie gedrag van het dialoogvenster voor eigenschappen van implementatie type** niet is ingeschakeld, mislukt de installatie van de app als een of meer van de opgegeven toepassingen worden uitgevoerd.

## <a name="for-more-information"></a>Voor meer informatie:
- [Instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Het configureren van clientinstellingen](../../core/clients/deploy/configure-client-settings.md)

