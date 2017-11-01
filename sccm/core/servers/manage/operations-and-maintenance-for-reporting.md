---
title: 'Bewerkingen en onderhoud voor rapportage '
titleSuffix: Configuration Manager
description: Lees meer over het beheren van rapporten en rapportabonnementen in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b89bcfbf-f5b6-4fb1-bb5e-a5cc18ec0c78
caps.latest.revision: "5"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 05a81cdfd46ba2bf0bea17b06bd72f79296b3930
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="operations-and-maintenance-for-reporting-in-system-center-configuration-manager"></a>Bewerkingen en onderhoud voor rapportage in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat de infrastructuur aanwezig is voor rapportage in System Center Configuration Manager is, zijn er een aantal bewerkingen die u normaal gesproken uitvoert om rapporten en rapportabonnementen te beheren.  

##  <a name="BKMK_ManageReports"></a>Configuration Manager-rapporten beheren  
 Configuration Manager biedt meer dan 400 vooraf gedefinieerde rapporten waarmee u verzamelt, organiseert en presenteert informatie over gebruikers, hardware en software-inventaris, software-updates, toepassingen, sitestatus en andere Configuration Manager-bewerkingen in uw organisatie. U kunt de vooraf gedefinieerde rapporten gebruiken zoals ze zijn, of kunt u een rapport te voldoen aan uw vereisten. U kunt ook aangepaste model maken\-gebaseerd en SQL\-op basis van rapporten om te voldoen aan uw vereisten. Gebruik de volgende secties om u te helpen bij het beheren van Configuration Manager-rapporten.  

###  <a name="BKMK_RunReport"></a>Een Configuration Manager-rapport uitvoeren  
 Rapporten in Configuration Manager worden opgeslagen in SQL Server Reporting Services en de gegevens in het rapport is opgehaald uit de Configuration Manager-sitedatabase. U kunt toegang tot rapporten in de Configuration Manager-console of met Rapportbeheer, die u in een webbrowser openen. U kunt rapporten openen op elke computer die toegang heeft tot de computer waarop SQL Server Reporting Services en hebt u onvoldoende rechten om de rapporten weer te geven. Wanneer u een rapport uitvoert, worden de titel, beschrijving en categorie weergegeven in de taal van het lokale besturingssysteem.  

> [!NOTE]  
>  In sommige niet\-talen voor Engels tekens mogelijk niet correct weergegeven in rapporten.  In dit geval rapporten kunnen worden weergegeven via het web\-op basis van Rapportbeheer of via de externe beheerconsole.  

> [!WARNING]  
>  Voor het uitvoeren van rapporten, moet u hebben **lezen** rechten voor de **Site** machtigingen en de **rapport uitvoeren** machtiging die is geconfigureerd voor specifieke objecten.  

> [!IMPORTANT]    
> Er moet een wederzijdse vertrouwensrelatie tot stand gebracht voor gebruikers van een ander domein dan die van het Account Servicies punt Reporting is het uitvoeren van rapporten.

> [!NOTE]  
>  Rapportbeheer is een web-\-op basis van toegang en beheer rapportage die u gebruikt voor het beheren van een enkel rapportserverexemplaar op een externe locatie via een HTTP-verbinding. U kunt Report Manager voor operationele taken, bijvoorbeeld weergeven van rapporten, rapporteigenschappen te wijzigen en gekoppelde rapportabonnementen te beheren. Dit onderwerp vindt u de stappen voor het weergeven van een rapport en rapporteigenschappen in Rapportbeheer, maar voor meer informatie inzake andere opties van Rapportbeheer, Zie [Report Manager](http://go.microsoft.com/fwlink/p/?LinkId=224916) in SQL Server 2008 Books Online.  

 Gebruik de volgende procedures een Configuration Manager-rapport uitvoeren.  

##### <a name="to-run-a-report-in-the-configuration-manager-console"></a>Een rapport in de Configuration Manager-console uitvoeren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage**, en klik vervolgens op **rapporten** voor een lijst met de beschikbare rapporten.  

    > [!IMPORTANT]  
    >  In deze versie van Configuration Manager de **alle inhoud** rapporten enkel pakketten weer, geen toepassingen.  

    > [!TIP]  
    >  Als er geen rapporten worden weergegeven, controleert u of dat het rapportageservicepunt is geïnstalleerd en geconfigureerd. Zie voor meer informatie [Configuring reporting](configuring-reporting.md).  

3.  Selecteer het rapport dat u uitvoeren wilt, en klik vervolgens op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **uitvoeren** om het rapport te openen.  

4.  Wanneer er vereiste parameters, de parameters opgeven en klik vervolgens op **rapport weergeven**.  

#### <a name="to-run-a-report-in-a-web-browser"></a>Een rapport uitvoeren in een webbrowser  

1.  In uw webbrowser de Report Manager-URL invoeren, bijvoorbeeld **http:\/\/Server1\/rapporten**. U kunt de Report Manager-URL bepalen op de **URL van Report Manager** pagina in Reporting Services Configuration Manager.  

2.  In Rapportbeheer, klikt u op de rapportmap Configuration Manager, bijvoorbeeld **ConfigMgr\_CAS**.  

    > [!TIP]  
    >  Als er geen rapporten worden weergegeven, controleert u of dat het rapportageservicepunt is geïnstalleerd en geconfigureerd. Zie voor meer informatie [Configuring reporting](configuring-reporting.md).  

3.  Klik op de rapportcategorie voor het rapport dat u wilt uitvoeren en klik op de koppeling voor het rapport. Het rapport wordt geopend in Rapportbeheer.  

4.  Wanneer er vereiste parameters, de parameters opgeven en klik vervolgens op **rapport weergeven**.  

###  <a name="BKMK_ModifyReportProperties"></a>De eigenschappen voor een Configuration Manager-rapport wijzigen  
 U kunt de eigenschappen voor een rapport, zoals de rapportnaam en -beschrijving, maar gebruik Rapportbeheer om de eigenschappen te wijzigen in de Configuration Manager-console. Gebruik de volgende procedure om de eigenschappen voor een Configuration Manager-rapport te wijzigen.  

#### <a name="to-modify-report-properties-in-report-manager"></a>Rapporteigenschappen in Rapportbeheer wijzigen  

1.  In uw webbrowser de Report Manager-URL invoeren, bijvoorbeeld **http:\/\/Server1\/rapporten**. U kunt de Report Manager-URL bepalen op de **URL van Report Manager** pagina in Reporting Services Configuration Manager.  

2.  In Rapportbeheer, klikt u op de rapportmap Configuration Manager, bijvoorbeeld **ConfigMgr\_CAS**.  

    > [!TIP]  
    >  Als er geen rapporten worden weergegeven, controleert u of dat het Reporting Services-punt is geïnstalleerd en geconfigureerd. Zie voor meer informatie [rapportage configureren](configuring-reporting.md)  

3.  Klik op de rapportcategorie voor het rapport waarvoor u wilt de eigenschappen wijzigen en klik op de koppeling voor het rapport. Het rapport wordt geopend in Rapportbeheer.  

4.  Klik op de **eigenschappen** tabblad. U kunt de naam en beschrijving wijzigen.  

5.  Wanneer u klaar bent, klikt u op **toepassen**. De rapporteigenschappen zijn bewaard op de rapportserver en de Configuration Manager-console haalt de bijgewerkte rapporteigenschappen voor het rapport.  

###  <a name="BKMK_EditReport"></a>Een Configuration Manager-rapport bewerken  
 Wanneer een bestaand Configuration Manager-rapport de informatie die u nodig hebt niet ophaalt of niet zorgt voor de indeling of ontwerp dat u wilt, kunt u het rapport in Report Builder bewerken.  

> [!NOTE]  
>  U kunt ook een bestaand rapport te klonen Hiertoe opent u het voor het bewerken en te klikken op **OpslaanAls** opslaan als een nieuw rapport.  

> [!IMPORTANT]  
>  Het gebruikersaccount moet beschikken over **Site wijzigen** machtiging en **rapport wijzigen** machtigingen voor de specifieke objecten gekoppeld aan het rapport dat u wilt wijzigen.  

> [!IMPORTANT]  
>  Wanneer Configuration Manager wordt bijgewerkt naar een nieuwere versie, worden de vooraf gedefinieerde rapporten overschreven door nieuwe rapporten. Als u een vooraf gedefinieerd rapport wijzigt, moet u voordat u de nieuwe versie installeert en vervolgens het rapport in Reporting Services herstellen maken van het rapport. Als u belangrijke wijzigingen aan een vooraf gedefinieerd rapport doorvoert, kunt u in plaats daarvan een nieuw rapport maakt. Nieuwe rapporten die u voordat u de upgrade een site maakt worden niet overschreven.  

 Gebruik de volgende procedure om de eigenschappen voor een Configuration Manager-rapport te bewerken.  

#### <a name="to-edit-report-properties"></a>Rapporteigenschappen bewerken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage**, en klik vervolgens op **rapporten** voor een lijst met de beschikbare rapporten.  

3.  Selecteer het rapport dat u wijzigen wilt, en klik vervolgens op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **bewerken**. Voer uw gebruikersaccount en wachtwoord in als u wordt gevraagd en klik vervolgens op **OK**. Als Report Builder is niet geïnstalleerd op de computer, wordt u gevraagd om deze te installeren. Klik op **uitvoeren** voor het installeren van Report Builder is vereist om te wijzigen en rapporten maken.  

4.  In Report Builder de geschikte rapportinstellingen wijzigen en klik vervolgens op **opslaan** het rapport wilt opslaan op de rapportserver.  

###  <a name="BKMK_CreateModelBasedReport"></a>Een model maken\-gebaseerde rapport  
 Een model\-op basis van rapport kunt u interactief de items die u wilt opnemen in uw rapport selecteren. Zie voor meer informatie over het maken van aangepaste rapportmodellen [maken van aangepaste rapportmodellen voor System Center Configuration Manager in SQL Server Reporting Services](creating-custom-report-models-in-sql-server-reporting-services.md).  

> [!IMPORTANT]  
>  Het gebruikersaccount moet beschikken over **Site wijzigen** machtiging voor het maken van een nieuw rapport. De gebruiker kan enkel een rapport maken in mappen waarvoor de gebruiker heeft **rapport wijzigen** machtigingen.  

 Gebruik de volgende procedure voor het maken van een model\-op basis van Configuration Manager-rapport.  

#### <a name="to-create-a-model-based-report"></a>Maken van een model\-gebaseerde rapport  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage** en klik op **rapporten**.  

3.  Op de **Start** tabblad, in de **maken** sectie, klikt u op **rapport maken** openen de **Wizard rapport maken**.  

4.  Op de **informatie** pagina, configureer de volgende instellingen:  

    -   **Type**: Selecteer **Model\-gebaseerde rapport** te maken van een rapport in Report Builder met behulp van een Reporting Services-model.  

    -   **Naam**: Geef een naam voor het rapport.  

    -   **Beschrijving**: Geef een beschrijving voor het rapport.  

    -   **Server**: De naam weergegeven van de rapportserver waarop u dit rapport maakt.  

    -   **Pad**: Klik op **Bladeren** om op te geven van een map waarin u wilt opslaan van het rapport.  

     Klik op **Volgende**.  

5.  Op de **modelselectie** pagina, selecteert u een beschikbaar model in de lijst die u kunt dit rapport te maken. Wanneer u het rapportmodel, selecteert de **Preview** sectie vindt u de SQL Server-weergaven en entiteiten die beschikbaar zijn gesteld door het geselecteerde rapportmodel.  

6.  Bekijk de instellingen op de pagina **Samenvatting** . Klik op **vorige** de instellingen wijzigen of klik op **volgende** aan het rapport maken in Configuration Manager.  

7.  Op de **bevestiging** pagina, klikt u op **sluiten** naar de wizard af te sluiten en open vervolgens de Report Builder om de rapportinstellingen te configureren. Voer uw gebruikersaccount en wachtwoord in als u wordt gevraagd en klik vervolgens op **OK**. Als Report Builder is niet geïnstalleerd op de computer, wordt u gevraagd om deze te installeren. Klik op **uitvoeren** voor het installeren van Report Builder is vereist om te wijzigen en rapporten maken.  

8.  In Microsoft Report Builder indeling van het rapport te maken, selecteer gegevens in de beschikbare SQL Server-weergaven, parameters toevoegen aan het rapport, enzovoort. Zie de Report Builder Help voor meer informatie over het gebruik van Report Builder om een nieuw rapport maken.  

9. Klik op **uitvoeren** uw rapport uit te voeren. Controleer of dat het rapport bevat de informatie die u verwacht. Klik op **ontwerp** om terug te keren naar de ontwerpweergave om te wijzigen van het rapport, indien nodig.  

10. Klik op **opslaan** het rapport wilt opslaan op de rapportserver. U kunt uitvoeren en wijzigen van het nieuwe rapport in de **rapporten** knooppunt in de **bewaking** werkruimte.  

###  <a name="BKMK_CreateSQLBasedReport"></a>Maken van een SQL\-gebaseerde rapport  
 Een SQL\-op basis van rapport kunt u de gegevens die is gebaseerd op de SQL-instructie van een rapport ophalen.  

> [!IMPORTANT]  
>  Wanneer u een SQL-instructie voor een aangepast rapport maakt, Verwijs niet direct naar SQL Server-tabellen. In plaats daarvan verwijzen naar rapportage SQL Server-weergaven \(weergeven namen die met v beginnen\_ \) uit de sitedatabase. U kunt ook verwijzen naar openbaar opgeslagen procedures \(opgeslagen procedure met namen die met sp beginnen\_ \) uit de sitedatabase.  

> [!IMPORTANT]  
>  Het gebruikersaccount moet beschikken over **Site wijzigen** machtiging voor het maken van een nieuw rapport. De gebruiker kan enkel een rapport maken in mappen waarvoor de gebruiker heeft **rapport wijzigen** machtigingen.  

 Gebruik de volgende procedure voor het maken van een SQL\-op basis van Configuration Manager-rapport.  

#### <a name="to-create-a-sql-based-report"></a>Maken van een SQL\-gebaseerde rapport  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte **Bewaking** **Rapportage**uit en klik vervolgens op **Rapporten**.  

3.  Op de **Start** tabblad, in de **maken** sectie, klikt u op **rapport maken** openen de **Wizard rapport maken**.  

4.  Op de **informatie** pagina, configureer de volgende instellingen:  

    -   **Type**: Selecteer **SQL\-gebaseerde rapport** te maken van een rapport in Report Builder met behulp van een SQL-instructie.  

    -   **Naam**: Geef een naam voor het rapport.  

    -   **Beschrijving**: Geef een beschrijving voor het rapport.  

    -   **Server**: De naam weergegeven van de rapportserver waarop u dit rapport maakt.  

    -   **Pad**: Klik op **Bladeren** om op te geven van een map waarin u wilt opslaan van het rapport.  

     Klik op **Volgende**.  

5.  Bekijk de instellingen op de pagina **Samenvatting** . Klik op **vorige** de instellingen wijzigen of klik op **volgende** aan het rapport maken in Configuration Manager.  

6.  Op de **bevestiging** pagina, klikt u op **sluiten** de wizard af te sluiten en open de Report Builder om de rapportinstellingen te configureren. Voer uw gebruikersaccount en wachtwoord in als u wordt gevraagd en klik vervolgens op **OK**. Als Report Builder is niet geïnstalleerd op de computer, wordt u gevraagd om deze te installeren. Klik op **uitvoeren** voor het installeren van Report Builder is vereist om te wijzigen en rapporten maken.  

7.  In Microsoft Report Builder de SQL-instructie voor het rapport opgeven of de SQL-instructie maken met behulp van kolommen in beschikbare SQL Server-weergaven, parameters toevoegen aan het rapport, enzovoort.  

8.  Klik op **uitvoeren** uw rapport uit te voeren. Controleer of dat het rapport bevat de informatie die u verwacht. Klik op **ontwerp** om terug te keren naar de ontwerpweergave om te wijzigen van het rapport, indien nodig.  

9. Klik op **opslaan** het rapport wilt opslaan op de rapportserver. U kunt het nieuwe rapport uitvoeren in de **rapporten** knooppunt in de **bewaking** werkruimte.  

##  <a name="BKMK_ManageReportSubscriptions"></a>Rapportabonnementen beheren  
 Rapportabonnementen in SQL Server Reporting Services kunt u de automatische levering configureren van rapporten via e-mail of een bestandsshare met regelmatige tussenpozen. Gebruik de **Wizard voor abonnement** in System Center 2012 Configuration Manager om rapportabonnementen te configureren.  

###  <a name="BKMK_ReportSubscriptionFileShare"></a>Een rapportabonnement voor het leveren van een rapport met een bestandsshare maken  
 Wanneer u een rapportabonnement te leveren van een rapport met een bestandsshare maakt, wordt het rapport in de opgegeven indeling gekopieerd naar de bestandsshare die u opgeeft. U kunt zich abonneren op en levering slechts voor één rapport aanvragen tegelijk.  

 In tegenstelling tot de rapporten die worden gehost en beheerd door een rapportserver, zijn rapporten die worden geleverd met een gedeelde map statische bestanden. Interactieve functies die zijn gedefinieerd voor het rapport werken niet voor rapporten die zijn opgeslagen als bestanden op het bestandssysteem. Interactieve functies worden weergegeven als statische elementen. Als het rapport grafieken bevat, wordt de standaardpresentatie gebruikt. Als u de rapporten doorgelinkt worden naar een ander rapport, wordt de koppeling weergegeven als statische tekst. Als u behouden interactieve functies in een geleverd rapport wilt, gebruikt u de levering via e-mail. Zie voor meer informatie over levering via e-mail, de [een rapportabonnement maken om te leveren van een rapport via e-mail](#BKMK_ReportSubscriptionEmail) verderop in dit onderwerp.  

 Wanneer u een abonnement dat levering via bestandsshare gebruikt maakt, moet u een bestaande map als doelmap. De rapportserver maakt geen mappen op het bestandssysteem. De map die u opgeeft moet toegankelijk zijn via een netwerkverbinding. Wanneer u de doelmap in een abonnement opgeeft, wordt een UNC-pad en Neem geen afsluitende backslash-tekens in pad naar de map. Een geldig UNC-pad voor de doelmap is bijvoorbeeld: \\ \\ &lt;servername\>\\reportfiles\\operations\\2011.  

 Rapporten kunnen worden gerenderd in verschillende bestandsindelingen, zoals MHTML of Excel. Sla het rapport in een specifieke indeling, selecteert het weergaveformaat bij het maken van uw abonnement. Bijvoorbeeld slaat Excel gekozen het rapport als een Microsoft Excel-bestand. Hoewel u elk ondersteund weergaveformaat selecteren kunt, werken sommige formaten beter dan andere bij het renderen naar een bestand.  

 Gebruik de volgende procedure om een rapportabonnement voor het leveren van een rapport met een bestandsshare te maken.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-to-a-file-share"></a>Een rapportabonnement voor het leveren van een rapport met een bestandsshare maken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage** en klik op **rapporten** voor een lijst met de beschikbare rapporten. U kunt een rapportmap om alleen de rapporten die gekoppeld aan de map zijn weer te selecteren.  

3.  Selecteer het rapport dat u wilt toevoegen aan het abonnement en klikt u op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **abonnement maken** openen de **Wizard voor abonnement**.  

4.  Op de **levering van abonnement** pagina, configureer de volgende instellingen:  

    -   Rapport geleverd door: Selecteer **Windows-bestandsshare** het rapport naar een bestandsshare te leveren.  

    -   **Bestandsnaam**: Geef de bestandsnaam op voor het rapport. Het rapportbestand bevat standaard geen extensie. Selecteer **bestandsextensie toevoegen bij gemaakt** automatisch een bestandsnaamextensie toevoegen aan dit rapport op basis van de renderindeling.  

    -   **Pad**: Geef een UNC-pad naar een bestaande map waar u dit rapport te leveren \(bijvoorbeeld \\ \\ &lt;servernaam\>\\&lt;servershare\>\\&lt;rapportmap\>\).  

        > [!NOTE]  
        >  Naam van de gebruiker opgegeven later op deze pagina moet toegang hebben tot deze servershare en over schrijfbevoegdheden beschikken op de doelmap.  

    -   **Renderindeling**: Selecteer een van de volgende indelingen voor het rapportbestand:  

        -   **XML-bestand met rapportgegevens**: Slaat het rapport op in Extensible Markup Language-indeling.  

        -   **CSV \(door komma's gescheiden\)**: Slaat het rapport op in een door komma's\-gescheiden\-waarde-indeling.  

        -   **TIFF-bestand**: Slaat het rapport op in Tagged Image File Format.  

        -   **Acrobat \(PDF\) bestand**: Slaat het rapport op in Acrobat Portable Document Format.  

        -   **HTML 4.0**: Slaat het rapport als een webpagina die alleen zichtbaar met browsers die ondersteuning bieden voor HTML 4.0. Internet Explorer 5 en latere versies ondersteuning bieden voor HTML 4.0.  

            > [!NOTE]  
            >  Als u installatiekopieën in uw rapport hebt, bevat de HTML 4.0-indeling geen ze in het bestand.  

        -   **MHTML \(webarchief\)**: Slaat het rapport op in MIME HTML-indeling \(mhtml\), namelijk in veel webbrowser kan worden weergegeven.  

        -   **RPL-Renderer**: Hiermee slaat u het rapport in Report pagina-indeling \(RPL\) indeling.  

        -   **Excel**: Slaat het rapport als een Microsoft Excel-werkblad.  

        -   **Word**: Slaat het rapport als een Microsoft Word-document.  

    -   **Gebruikersnaam**: Geef een Windows-gebruikersaccount met machtigingen voor toegang tot de doelservershare en -map. Het gebruikersaccount moet toegang hebben tot deze servershare en schrijfmachtiging voor de doelmap.  

    -   **Wachtwoord**: Geef het wachtwoord voor het Windows-gebruikersaccount. In **wachtwoord bevestigen**, re\-Voer het wachtwoord.  

    -   Selecteer een van de volgende opties voor het configureren van het gedrag wanneer een bestand met dezelfde naam in de doelmap bestaat:  

        -   **Een bestaand bestand overschrijven met een nieuwere versie**: Hiermee geeft u op dat wanneer het rapportbestand al bestaat, de nieuwe versie overschreven.  

        -   **Een bestaand bestand niet overschrijven**: Hiermee geeft u op dat wanneer het rapportbestand al bestaat, er geen actie is.  

        -   **Bestandsnamen laten oplopen als nieuwe versies worden toegevoegd**: Hiermee geeft u op dat wanneer het rapportbestand al bestaat, een nummer wordt toegevoegd aan het nieuwe rapport aan de bestandsnaam te onderscheiden van andere versies.  

    -   **Beschrijving**: Hiermee geeft u de beschrijving voor het rapportabonnement.  

     Klik op **Volgende**.  

5.  Op de **Abonnementplanning** pagina, selecteer een van de volgende leveringsplanningopties voor het rapportabonnement:  

    -   **Gedeelde planning gebruiken**: Een gedeelde planning is een vooraf gedefinieerde planning die door andere rapportabonnementen kan worden gebruikt. Schakel dit selectievakje in en selecteert u een gedeelde planning in de lijst als een zijn opgegeven.  

    -   **Nieuwe planning maken**: Configureer de planning waarop dit rapport wordt uitgevoerd, inclusief het interval, start u tijd en datum en de einddatum voor dit abonnement.  

6.  Op de **Abonnementsparameters** pagina, de parameters voor dit rapport die worden gebruikt wanneer deze wordt uitgevoerd zonder toezicht opgeven. Wanneer er geen parameters voor het rapport zijn, wordt deze pagina niet weergegeven.  

7.  Op de **samenvatting** controleert u de instellingen van het rapport. Klik op **vorige** de instellingen wijzigen of klik op **volgende** om het rapportabonnement te maken.  

8.  Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten. Controleer of het rapportabonnement is gemaakt. U kunt bekijken en wijzigen met rapportabonnementen in de **abonnementen** knooppunt onder **rapportage** in de **bewaking** werkruimte.  

###  <a name="BKMK_ReportSubscriptionEmail"></a>Een rapportabonnement maken om te leveren van een rapport via e-mail  
 Wanneer u een rapportabonnement te leveren van een rapport via e-mail maakt, een e-mailbericht wordt verzonden naar de ontvangers die u configureert en het rapport wordt als bijlage toegevoegd. De rapportserver niet valideren e-mailadressen of e-mailadressen verkrijgen van een e-mailserver. U moet van tevoren weten welke e-mailadressen die u wilt gebruiken. Standaard kunt u e-rapporten naar geldige e-mailaccounts binnen of buiten uw organisatie. U kunt een of beide van de volgende e-Bezorgingsopties selecteren:  

-   Een melding en een hyperlink verzenden naar het gegenereerde rapport.  

-   Een ingesloten of bijgevoegd rapport verzenden. De renderindeling en browser bepalen of het rapport ingesloten of gekoppeld. Als uw browser HTML 4.0 en MHTML ondersteunt en u de MHTML selecteert \(webarchief\) rendering indeling, wordt het rapport ingesloten als deel van het bericht. Alle andere renderindelingen \(CSV, PDF, Word, enzovoort\) leveren rapporten als bijlagen. Reporting Services, wordt de grootte van de bijlage of het bericht niet gecontroleerd voordat het rapport wordt verzonden. Als de bijlage of het bericht het maximum aantal dat is toegestaan door uw e-mailserver overschrijdt, wordt het rapport niet bezorgd.  

> [!IMPORTANT]  
>  U moet de e-mailinstellingen configureren in Reporting Services voor de **e** levering optie niet beschikbaar. Zie voor meer informatie over het configureren van de e-mailinstellingen in Reporting Services [een rapportserver configureren voor levering via E-mail](http://go.microsoft.com/fwlink/p/?LinkId=226668) in SQL Server Books Online.  

 Gebruik de volgende procedure om een rapportabonnement voor het leveren van een rapport via e-mail te maken.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-by-email"></a>Een rapportabonnement voor het leveren van een rapport via e-mail maken  

-   Klik in de Configuration Manager-console op **bewaking**.  

-   In de **bewaking** werkruimte Vouw **rapportage** en klik op **rapporten** voor een lijst met de beschikbare rapporten. U kunt een rapportmap voor een lijst met de enige selecteren de rapporten die gekoppeld aan de map zijn.  

-   Selecteer het rapport dat u wilt toevoegen aan het abonnement en klikt u op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **abonnement maken** openen de **Wizard voor abonnement**.  

-   Op de **levering van abonnement** pagina, configureer de volgende instellingen:  

    -   **Rapport geleverd door**: Selecteer **E\-mail** leveren van het rapport als bijlage bij een e-mailbericht.  

    -   **Naar**: Geef een geldig e-mailadres voor het verzenden van dit rapport.  

        > [!NOTE]  
        >  U kunt meerdere e-mailontvangers invoeren door elk e-mailadres met een puntkomma te scheiden.  

    -   **CC**: Geef eventueel een e-mailadres kopie van dit rapport.  

    -   **BCC**: Geef eventueel een e-mailadres een controlekopie van dit rapport.  

    -   **Beantwoorden**: Geef het antwoordadres op dat moet worden gebruikt als de ontvanger het e-mailbericht beantwoordt.  

    -   **Onderwerp**: Geef een onderwerpregel op voor het abonnement e-mailbericht.  

    -   **Prioriteit**: Selecteer de gewenste prioriteitsmarkering voor dit e-mailbericht. Selecteer **laag**, **normaal**, of **hoge**. De prioriteitsinstelling wordt door Microsoft Exchange gebruikt om in te stellen van een vlag die aangeeft het belang van het e-mailbericht.  

    -   **Opmerking**: Geef tekst op die moet worden toegevoegd aan de hoofdtekst van het abonnement e-mailbericht.  

    -   **Beschrijving**: Geef de beschrijving voor dit rapportabonnement.  

    -   **Koppeling opnemen**: Bevat een URL naar het geabonneerde rapport in de hoofdtekst van het e-mailbericht.  

    -   **Rapport opnemen**: Opgeven of het rapport is gekoppeld aan de e\-e-mailbericht. De indeling waarin het rapport als bijlage is opgegeven in de **Renderindeling** lijst.  

    -   **Renderindeling**: Selecteer een van de volgende indelingen voor het bijgevoegde rapport:  

        -   **XML-bestand met rapportgegevens**: Slaat het rapport op in Extensible Markup Language-indeling.  

        -   **CSV \(door komma's gescheiden\)**: Slaat het rapport op in een door komma's\-gescheiden\-waarde-indeling.  

        -   **TIFF-bestand**: Slaat het rapport op in Tagged Image File Format.  

        -   **Acrobat \(PDF\) bestand**: Slaat het rapport op in Acrobat Portable Document Format.  

        -   **MHTML \(webarchief\)**: Slaat het rapport op in MIME HTML-indeling \(mhtml\), namelijk in veel webbrowser kan worden weergegeven.  

        -   **Excel**: Slaat het rapport als een Microsoft Excel-werkblad.  

        -   **Word**: Slaat het rapport als een Microsoft Word-document.  

-   Op de **Abonnementplanning** pagina, selecteer een van de volgende leveringsplanningopties voor het rapportabonnement:  

    -   **Gedeelde planning gebruiken**: Een gedeelde planning is een vooraf gedefinieerde planning die door andere rapportabonnementen kan worden gebruikt. Schakel dit selectievakje in en selecteert u een gedeelde planning in de lijst als een zijn opgegeven.  

    -   **Nieuwe planning maken**: Configureer de planning waarmee dit rapport wordt uitgevoerd, inclusief het interval, de starttijd en de datum en de einddatum voor dit abonnement.  

-   Op de **Abonnementsparameters** pagina, de parameters voor dit rapport die worden gebruikt wanneer deze wordt uitgevoerd zonder toezicht opgeven. Wanneer er geen parameters voor het rapport zijn, wordt deze pagina niet weergegeven.  

-   Op de **samenvatting** controleert u de instellingen van het rapport. Klik op **vorige** de instellingen wijzigen of klik op **volgende** om het rapportabonnement te maken.  

-   Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten. Controleer of het rapportabonnement is gemaakt. U kunt bekijken en wijzigen met rapportabonnementen in de **abonnementen** knooppunt onder **rapportage** in de **bewaking** werkruimte.  
