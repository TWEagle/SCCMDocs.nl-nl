---
title: Toepassingen implementeren
titleSuffix: Configuration Manager
description: Maken of een implementatie van een toepassing in de verzameling van een apparaat of gebruiker simuleren
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0101ba0eade5775577f52920f301a782afd7bbda
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="deploy-applications-with-system-center-configuration-manager"></a>Implementeren van toepassingen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Maken of een implementatie van een toepassing in een verzameling in Configuration Manager met het apparaat of gebruiker simuleren. Deze implementatie biedt instructies voor de Configuration Manager-client op hoe en wanneer de software te installeren. 

Voordat u een toepassing implementeren kunt, moet u ten minste één implementatietype voor de toepassing maken. Zie voor meer informatie [toepassingen maken](/sccm/apps/deploy-use/create-applications).

 U kunt de implementatie van een toepassing ook simuleren. Deze simulatie test u de toepasselijkheid van een implementatie zonder installeren of verwijderen van de toepassing. Een gesimuleerde implementatie de detectiemethode, vereisten en afhankelijkheden voor een implementatietype geëvalueerd en rapporteert de resultaten in de **implementaties** knooppunt van de **bewaking** werkruimte. Zie voor meer informatie [toepassingsimplementaties simuleren](/sccm/apps/deploy-use/simulate-application-deployments).

> [!IMPORTANT]
>  U kunt de implementatie van de vereiste toepassingen, maar geen pakketten of software-updates simuleren.   
>  MDM-ingeschreven apparaten ondersteunen niet gesimuleerde implementaties, gebruikerservaring en programmatie-instellingen.



## <a name="deploy-an-application"></a>Een toepassing implementeren

1.  Ga in de Configuration Manager-console naar **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.

2.  Selecteer, in de lijst **Toepassingen** de toepassing die u wenst te implementeren. Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.

### <a name="specify-general-information-about-the-deployment"></a>Geef algemene informatie over de implementatie

Op de **algemene** pagina van de wizard Software implementeren geeft u de volgende informatie:

- **Software**: Deze waarde wordt weergegeven voor de toepassing te implementeren. Klik op **Bladeren** om een andere toepassing te selecteren.
- **Verzameling**: Klik op **Bladeren** om de verzameling voor het implementeren van de toepassing te selecteren.
- **Gebruik standaarddistributiepuntengroepen die gekoppeld zijn aan deze verzameling**: Inhoud van de toepassing opslaan op de verzameling standaard distributiepuntengroep. Als u de geselecteerde verzameling niet hebt gekoppeld aan een distributiepuntgroep, wordt deze optie grijs weergegeven.
- **Inhoud voor afhankelijkheden automatisch distribueren**: Als er implementatietypes zijn die in de toepassing afhankelijkheden bevatten, klikt u vervolgens stuurt de site ook afhankelijke inhoud naar distributiepunten.

    >[!IMPORTANT]
    > Als u de afhankelijke toepassing na de implementatie van de primaire toepassing bijwerkt, distribueren niet de site automatisch alle nieuwe inhoud voor de afhankelijkheid.

- **Commentaren (optioneel)**: Voer eventueel een beschrijving voor deze implementatie.

### <a name="specify-content-options-for-the-deployment"></a>Inhoudopties voor de implementatie opgeven

Op de **inhoud** pagina, klikt u op **toevoegen** om toe te voegen inhoud die is gekoppeld aan de implementatie naar distributiepunten of distributiepuntengroepen. Als u selecteert **gebruik standaarddistributiepunten gekoppeld aan deze verzameling** op de **algemene** pagina, en vervolgens deze optie wordt automatisch ingevuld. Alleen een lid van de beveiligingsrol van beheerder van de toepassing kunt wijzigen.

### <a name="specify-deployment-settings"></a>Implementatie-instellingen opgeven

Op de **implementatie-instellingen** pagina van de wizard Software implementeren geeft u de volgende informatie:

- **Actie**: Kies in de vervolgkeuzelijst of deze implementatie moeten worden **installeren** of **verwijderen** de toepassing.

    > [!NOTE]
    >  Als een toepassing tweemaal geïmplementeerd is op een apparaat, enerzijds met actie van **installeren** en anderzijds met een actie van **verwijderen**, de implementatie van de toepassing met een actie van **installeren** voorrang.

  U kunt de actie van een implementatie niet wijzigen nadat u dit hebt gemaakt.

- **Doel**: Kies een van de volgende opties in de vervolgkeuzelijst:  
    - **Beschikbare**: Als de toepassing wordt geïmplementeerd voor een gebruiker, wordt de gebruiker ziet de gepubliceerde toepassing in Software Center en kan deze op verzoek installeren.
    - **Vereist**: De toepassing is automatisch geïmplementeerd volgens de planning. Als de implementatiestatus van de toepassing niet verborgen is, kan iedereen met behulp van de toepassing de implementatiestatus bijhouden en de toepassing installeren vanuit Software Center vóór de deadline.

    > [!NOTE]   
    >  Wanneer de implementatie-actie is ingesteld op **verwijderen**, het doel van de implementatie automatisch ingesteld op **vereist**. U kunt dit gedrag niet wijzigen.  

- **Automatisch implementeren volgens schema of een gebruiker is aangemeld of niet**: Als de implementatie voor een gebruiker, selecteert u deze optie om de toepassing op de primaire apparaten van de gebruiker te implementeren. Deze instelling vereist niet dat de gebruiker zich aanmeldt vóór de implementatie draait. Selecteer deze optie niet als de gebruiker met de installatie communiceren moet. Deze optie is enkel beschikbaar als de implementatie een **Vereist**doel heeft.

- **Verzenden van ontwaakpakketten**: Als het implementatiedoel **vereist**, een ontwaakpakket verzonden naar computers voordat de client de implementatie wordt uitgevoerd. Dit pakket uit de slaapstand wordt de computers deadline van de installatie. Voordat u deze optie gebruikt, worden computers en netwerken geconfigureerd voor Wake On LAN.
- **Laat clients toe op een internetverbinding naar gebruik om inhoud te downloaden na de installatiedeadline, waarvoor extra kosten in rekening kan worden**: Deze optie is alleen beschikbaar voor implementaties met als doel **vereist**.
- **Automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type**: Zie voor meer informatie [controleren om uitvoerbare bestanden uit te voeren voordat u een toepassing installeert](#how-to-check-for-running-executable-files-before-installing-an-application).

- **Goedkeuring door beheerder vereisen als gebruikers deze toepassing aanvragen**: Voor versies 1710 en eerdere keurt de beheerder van de verzoeken van gebruikers voor de toepassing voordat de gebruiker kan het installeren. Deze optie wordt grijs weergegeven wanneer het implementatiedoel **vereist**, of wanneer de toepassing wordt geïmplementeerd op een apparatenverzameling.  

    > [!NOTE]
    >  Verzoeken voor gebruik van een toepassing worden weergegeven in het knooppunt **Goedkeuringsaanvragen** onder **Toepassingbeheer** in de werkruimte **Softwarebibliotheek** . Als een aanvraag is niet binnen 45 dagen werd goedgekeurd, wordt deze verwijderd. De client opnieuw installeert, kan verzoeken van in afwachting van goedkeuring annuleren.  
    >  Nadat u een toepassing voor de installatie hebt goedgekeurd, kunt u **weigeren** de aanvraag in de Configuration Manager-console. Deze actie niet zorgen dat de client de toepassing verwijderen van apparaten, maar deze voorkomen dat gebruikers nieuwe exemplaren van de toepassing installeren vanuit Software Center.

- **Een beheerder een aanvraag voor deze toepassing op het apparaat moet goedkeuren**: Vanaf versie 1802 biedt goedkeuren de beheerder van de verzoeken van gebruikers voor de toepassing voordat de gebruiker deze op het opgegeven apparaat kunt installeren. Als de beheerder de aanvraag goedkeurt, is alleen de gebruiker kan de toepassing op het apparaat installeren. De gebruiker moet een nieuwe aanvraag voor het installeren van de toepassing op een ander apparaat verzenden. Deze optie wordt grijs weergegeven wanneer het implementatiedoel **vereist**, of wanneer de toepassing wordt geïmplementeerd op een apparatenverzameling. <!--1357015-->  

    Dit is een optionele functie. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options). Als u deze functie niet is ingeschakeld, ziet u de ervaring.  

    > [!Important]  
    > Configuration Manager-client moet op versie 1802 ook. U moet ook gebruikmaken van het nieuwe Software Center.  

    > [!Note]  
    > Weergave **goedkeuringsaanvragen** onder **Toepassingsbeheer** in de **softwarebibliotheek** werkruimte van de Configuration Manager-console. Er is nu een **apparaat** kolom in de lijst voor elke aanvraag. Wanneer u actie op de aanvraag ondernemen, bevat het dialoogvenster aanvraag voor ook de naam van het apparaat waarvan de gebruiker de aanvraag heeft ingediend.  
    >  Als een aanvraag is niet binnen 45 dagen werd goedgekeurd, wordt deze verwijderd. De client opnieuw installeert, kan verzoeken van in afwachting van goedkeuring annuleren.  
    >  Nadat u een toepassing voor de installatie hebt goedgekeurd, kunt u **weigeren** de aanvraag in de Configuration Manager-console. Deze actie niet zorgen dat de client de toepassing verwijderen van apparaten, maar deze voorkomen dat gebruikers nieuwe exemplaren van de toepassing installeren vanuit Software Center.

- **Automatisch elke vervangen versie van deze toepassing updaten**: De client wordt bijgewerkt elke vervangen versie van de toepassing door de vervangende toepassing.    

    > [!NOTE]  
    > Vanaf versie 1802, voor **beschikbaar** of **vereist** doel, installeert u kunt inschakelen of uitschakelen van deze optie. <!--1351266--> 


### <a name="specify-scheduling-settings-for-the-deployment"></a>Schema-instellingen voor de implementatie opgeven

Op de **planning** pagina van de Software implementeren wizard, het tijdstip waarop deze toepassing worden geïmplementeerd of beschikbaar is voor clientapparaten instellen.
De opties op deze pagina verschillen afhankelijk van of de implementatieactie ingesteld is op **beschikbaar** of **vereist**.

In sommige gevallen is het raadzaam om gebruikers meer tijd voor implementaties van toepassingen installeren die zijn vereist of software-updates buiten een deadlines die u instelt. Dit gedrag is normaal gesproken vereist wanneer een computer lange tijd is uitgeschakeld en moet veel toepassingen te installeren. Bijvoorbeeld, als een gebruiker heeft geretourneerd van vakantie, wellicht ze wacht gedurende een lange periode als achterstallig toepassingsimplementaties zijn geïnstalleerd. U kunt nu een respijtperiode afdwingen door Configuration Manager-clientinstellingen implementeren naar een verzameling om dit probleem op te lossen definiëren.

Voor het configureren van de respijtperiode is, moet u de volgende acties uitvoeren:

- Op de **Computeragent** pagina configureren van clientinstellingen, de nieuwe eigenschap **respijtperiode voor afdwingen na de implementatie (uren) deadline** met een waarde tussen **1** en **120** uur.
- Op de **planning** pagina van de implementatie van een vereiste toepassing wilt **afdwingen van deze implementatie op basis van gebruikersvoorkeuren tot de respijtperiode die is gedefinieerd in de clientinstellingen uitstellen**. De respijtperiode voor afdwinging van toepassing op alle implementaties met deze optie is ingeschakeld en gericht op apparaten die u ook de client-instelling geïmplementeerd.

Nadat de toepassing installeren deadline is bereikt, installeert de client de toepassing in het eerste niet-zakelijk venster, de gebruiker geconfigureerd tot die respijtperiode. De gebruiker kan echter nog steeds openen van Software Center en de toepassing op elk gewenst moment die ze willen installeren. Nadat de respijtperiode is verlopen, hersteld afdwinging normaal gedrag voor implementaties van achterstallige.

Als de toepassing die u implementeert een andere toepassing vervangt, kunt u de installatiedeadline instellen wanneer gebruikers de nieuwe toepassing krijgen. Stel de **Installatiedeadline** om gebruikers met de vervangen toepassing te upgraden.

### <a name="specify-user-experience-settings-for-the-deployment"></a>Geef instellingen voor gebruikerservaring voor de implementatie

Op de **gebruikerservaring** pagina van de wizard Software implementeren geeft u informatie over hoe gebruikers met de installatie van de toepassing werken kunnen.

Wanneer u toepassingen voor Windows Embedded-apparaten schrijffilters ingeschakeld implementeert, kunt u de toepassing op de tijdelijke overlay en wijzigingen vastleggen om later te installeren. U kunt ook opgeven om de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Als u wijzigingen tegen de installatiedeadline of tijdens een onderhoudsvenster doorvoert, moet u het apparaat opnieuw te starten. De wijzigingen behouden blijven op het apparaat.

>[!NOTE]
    >  Wanneer u een toepassing implementeert op een Windows Embedded-apparaat, zorg er dan voor dat het is lid van een verzameling met een onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters en Windows Embedded-apparaten, [maken Windows Embedded-toepassingen](../../apps/get-started/creating-windows-embedded-applications.md).
    > De opties **Software-installatie** en **Systeem opnieuw opstarten (indien nodig om de installatie te vervolledigen)** worden niet gebruikt als het implementatiedoel ingesteld is op **Beschikbaar**. U kunt ook het niveau van melding configureren dat een gebruiker ziet wanneer de toepassing is geïnstalleerd.

### <a name="specify-alert-options-for-the-deployment"></a>Opties voor de implementatie opgeven

Op de **waarschuwingen** pagina van de wizard Software implementeren hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren instellen. U kunt drempels configureren voor het rapporteren van waarschuwingen en de rapportering van de duur van de implementatie uitschakelen.

### <a name="associate-the-deployment-with-an-ios-app-configuration-policy"></a>De implementatie koppelen aan een iOS-app-configuratiebeleid

Op de **Configuratiebeleidsregels** pagina, klikt u op **nieuw** deze implementatie koppelen aan een iOS-app-configuratiebeleid (als u deze hebt gemaakt). Zie voor meer informatie over dit type beleid [iOS-apps configureren met configuratiebeleidsregels](../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).

### <a name="deployment-properties"></a>Implementatie-eigenschappen

Zoeken naar de nieuwe implementatie in de **implementaties** knooppunt van de **bewaking** werkruimte. U kunt de kenmerken van deze implementatie bewerken of de implementatie wissen van het tabblad **Implementaties** van het detailpaneel van de toepassing.



## <a name="delete-an-application-deployment"></a>Implementatie van een toepassing verwijderen

1.  Ga in de Configuration Manager-console naar **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.
3.  In de **toepassingen** , selecteert u de toepassing die gebruikmaakt van de implementatie die u hebt verwijderd.
4.  Selecteer op het tabblad **Implementaties** van de lijst *<toepassingsnaam\>* de toepassingsimplementatie die u wilt wissen. Klik op de **implementatie** tabblad, in de **implementatie** groep, klikt u op **verwijderen**.

Wanneer u een toepassingsimplementatie wist, worden niet worden instanties van de toepassing die al zijn geïnstalleerd verwijderd. Deze om toepassingen te verwijderen, moet u de toepassing op computers met implementeren **verwijderen**. Als u een toepassingsimplementatie wist of een resource uit de verzameling die u verwijdert naar implementeert, is de toepassing niet meer zichtbaar in Software Center.



## <a name="user-notifications-for-required-deployments"></a>Meldingen voor gebruikers voor vereiste implementaties
Wanneer u vereiste software van ontvangt de **uitstellen en Help me herinneren** instelt, kunt u in de volgende lijst in de vervolgkeuzelijst van waarden:
- **Later**: Hiermee geeft u op dat meldingen worden gepland op basis van de instellingen voor meldingen geconfigureerd in de clientinstellingen.
- **Vaste tijd**: Hiermee geeft u op dat de melding is gepland om opnieuw op de geselecteerde tijd weer te geven. Bijvoorbeeld, als u 30 minuten selecteert, de melding wordt weergegeven in 30 minuten opnieuw.

![Computeragent groeperen in standaard clientinstellingen](media/ComputerAgentSettings.png)

De maximale uitstellen is altijd op basis van tijd op de melding waarden die zijn geconfigureerd in de clientinstellingen op elk moment langs de tijdlijn voor implementatie. Bijvoorbeeld:
- U configureert de **langer dan 24 uur deadline voor implementatie, gebruikers herinneren elke (uur)** instellen op de **Computeragent** pagina 10 uur.
- De client wordt het dialoogvenster melding weergegeven voordat de implementatiedeadline langer dan 24 uur.
- Het dialoogvenster bevat opties voor bewerkingen worden uitgesteld tot maar nooit meer dan 10 uur. 
- Als de implementatiedeadline nadert, ziet u het dialoogvenster minder opties. Deze opties zijn consistent met de relevante clientinstellingen voor elk onderdeel van de implementatie-tijdlijn.

De gebruikerservaring van de melding is voor een implementatie met hoog risico, zoals een takenreeks die een besturingssysteem implementeert ingrijpender. In plaats van een melding van tijdelijke taakbalk, zoals hieronder wordt weergegeven wanneer u een dialoogvenster met het bericht dat essentieel softwareonderhoud is vereist:

![Vereiste software dialoogvenster waarschuwt u essentieel softwareonderhoud](media/client-toast-notification.png)



## <a name="how-to-check-for-running-executable-files-before-installing-an-application"></a>Hoe moet worden gecontroleerd om uitvoerbare bestanden uit te voeren voordat u een toepassing installeert

In de **eigenschappen** in het dialoogvenster van een implementatie hebt getypt, op de **gedrag installeren** tabblad, geeft u een of meer uitvoerbare bestanden. Als een van deze uitvoerbare bestanden op de client wordt uitgevoerd, wordt de installatie van het implementatietype geblokkeerd. De gebruiker moet de lopende uitvoerbaar bestand sluiten voordat de client het implementatietype kunt installeren. Voor implementaties met als doel vereist, de client kan automatisch sluiten het actief uitvoerbare bestand.

1. Open de **eigenschappen** in het dialoogvenster voor eender welk implementatietype.
2. Op de **gedrag installeren** tabblad van de *<deployment type name>* **eigenschappen** in het dialoogvenster, klikt u op **toevoegen**.
3. In de **toevoegen of uitvoerbaar bestand bewerken** dialoogvenster en voer de naam van het uitvoerbare bestand dat, als uitgevoerd, blokken van de toepassing installeren. U kunt eventueel ook een beschrijvende naam voor de toepassing te herkennen in de lijst invoeren.
4. Klik op **OK**, sluit de *<deployment type name>* **eigenschappen** in het dialoogvenster.
5. Wanneer u de toepassing implementeert op de **implementatie-instellingen** pagina van de Wizard Software implementeren, selecteer **eventuele actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het implementatietype automatisch sluiten in het dialoogvenster Eigenschappen**.

Nadat de implementatie wordt ontvangen door clients, geldt het volgende gedrag:

- Als u de toepassing als geïmplementeerd **beschikbaar**, en een eindgebruiker probeert te installeren, vraagt de gebruiker te sluiten van de opgegeven actief uitvoerbare bestanden voordat u doorgaat met de installatie van de client.

- Als u de toepassing als geïmplementeerd **vereist**, en naar opgegeven **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type**, klikt u vervolgens de gebruiker ziet een dialoogvenster met de mededeling dat het opgegeven uitvoerbare bestanden automatisch worden gesloten wanneer de deadline van de installatie van de toepassing is bereikt. U kunt plannen dat deze dialoogvensters in **clientinstellingen** > **Computeragent**. Als u niet dat de eindgebruiker deze berichten te zien wilt, selecteert u **verbergen in Software Center en alle meldingen verbergen** op de **gebruikerservaring** tabblad van de implementatie-eigenschappen.

- Als u de toepassing als geïmplementeerd **vereist**, en niet opgeven voor **automatisch sluit alle actieve uitvoerbare bestanden die u hebt opgegeven op het tabblad voor het gedrag van installatie van het dialoogvenster voor eigenschappen van implementatie type**, vervolgens de installatie van de app mislukt als een of meer van de opgegeven toepassingen worden uitgevoerd.



## <a name="deploy-user-available-applications-on-azure-ad-joined-devices"></a>Gebruikers beschikbare toepassingen op Azure AD-die lid zijn van apparaten implementeren
<!-- 1322613 -->
Als u toepassingen als beschikbaar voor gebruikers implementeert, kunnen vanaf versie 1802 ze bladeren en deze installeren via Software Center op Azure Active Directory (Azure AD)-apparaten.  

#### <a name="prerequisites"></a>Vereisten

- HTTPS inschakelen op het beheerpunt  

- De site met integreren [Azure AD](/sccm/core/servers/deploy/configure/azure-services-wizard) voor **Cloudbeheer**  

    - Configureer [Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

- Een toepassing als beschikbaar implementeren op een verzameling gebruikers van Azure AD  

- Een toepassingsinhoud distribueert naar een [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)  

- Schakel de clientinstelling **nieuwe Software Center gebruiken** in de [computeragent](/sccm/core/clients/deploy/about-client-settings#computer-agent) groep  

- De client-besturingssysteem moet Windows 10 en toegevoegd aan Azure AD. Hetzij als puur cloud domein- of hybride Azure AD zijn toegevoegd.  

- Ter ondersteuning van clients op internet:  

    - [Beheergateway cloud](/sccm/core/clients/manage/plan-cloud-management-gateway)  

    - Schakel de clientinstelling: **Gebruikersbeleidsaanvragen van internetclients toestaan** in de [clientbeleid](/sccm/core/clients/deploy/about-client-settings#client-policy) groep  

- Ter ondersteuning van clients op het intranet:  

    - Het cloud-distributiepunt toevoegen aan een grensgroep die wordt gebruikt door de clients  

    - Clients moeten kunnen omzetten van de volledig gekwalificeerde domeinnaam (FQDN) van het HTTPS-beheerpunt  



## <a name="next-steps"></a>Volgende stappen

   -  [Instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md)  
   -  [Clientinstellingen configureren](../../core/clients/deploy/configure-client-settings.md)
   -  [Gebruikershandleiding voor de software Center](/sccm/core/understand/software-center)

