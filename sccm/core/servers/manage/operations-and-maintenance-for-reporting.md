---
title: Bewerkingen en onderhoud voor rapportage | Microsoft-documenten
description: Informatie over de details van het beheren van rapporten en rapportabonnementen in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b89bcfbf-f5b6-4fb1-bb5e-a5cc18ec0c78
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: f5a58ba9ecd9b0998c2859b6d3f45e493d7ef3cb
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="operations-and-maintenance-for-reporting-in-system-center-configuration-manager"></a>Bewerkingen en onderhoud voor rapportage in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat de infrastructuur voor rapportage in System Center Configuration Manager, wordt zijn er een aantal bewerkingen die u normaal gesproken uitvoert om rapporten en rapportabonnementen te beheren.  

##  <a name="BKMK_ManageReports"></a>Configuration Manager-rapporten beheren  
 Configuration Manager bevat meer dan 400 vooraf gedefinieerde rapporten waarmee u verzamelen, organiseren en presenteren van informatie over gebruikers, hardware en software-inventaris, software-updates, toepassingen, sitestatus en andere bewerkingen in Configuration Manager in uw organisatie. U kunt de vooraf gedefinieerde rapporten gebruiken zoals ze zijn, of u een rapport te voldoen aan uw vereisten kunt wijzigen. U kunt ook aangepaste model maken\-gebaseerd en SQL\-op basis van rapporten te voldoen aan uw vereisten. Gebruik de volgende secties om u te helpen bij het beheren van Configuration Manager-rapporten.  

###  <a name="BKMK_RunReport"></a>Een Configuration Manager-rapport uitvoeren  
 In Configuration Manager-rapporten worden opgeslagen in SQL Server Reporting Services en de gegevens in het rapport is opgehaald uit de sitedatabase van Configuration Manager. U kunt toegang tot de rapporten in de Configuration Manager-console of met behulp van Report Manager, waartoe u toegang in een webbrowser hebt. U kunt rapporten openen op elke computer die toegang heeft tot de computer waarop SQL Server Reporting Services en hebt u voldoende rechten om de rapporten weer te geven. Wanneer u een rapport hebt uitgevoerd, worden de titel, beschrijving en categorie weergegeven in de taal van het lokale besturingssysteem.  

> [!NOTE]  
>  In sommige niet\-Engels talen tekens mogelijk niet correct weergegeven worden in rapporten.  In dit geval rapporten kunnen worden weergegeven via het web\-op basis van Rapportbeheer of via de externe Administrator-Console.  

> [!WARNING]  
>  Als u wilt uitvoeren van rapporten, hebt u **lezen** rechten voor de **Site** machtiging en de **rapport uitvoeren** machtiging die is geconfigureerd voor specifieke objecten.  

> [!NOTE]  
>  Rapportbeheer is een WebApp\-op basis van toegang en beheer rapportage die u gebruikt voor het beheer van één enkel rapportserverexemplaar op een externe locatie via een HTTP-verbinding. U kunt Rapportbeheer voor uitvoerende taken, bijvoorbeeld rapporten bekijken, rapporteigenschappen te wijzigen en gekoppelde rapportabonnementen te beheren. In dit onderwerp voorziet de stappen voor het weergeven van een rapport en rapporteigenschappen in Rapportbeheer, maar voor meer informatie over de andere opties Rapportbeheer, Zie [Report Manager](http://go.microsoft.com/fwlink/p/?LinkId=224916) in SQL Server 2008 Books Online.  

 Gebruik de volgende procedures een Configuration Manager-rapport uitvoeren.  

##### <a name="to-run-a-report-in-the-configuration-manager-console"></a>Een rapport uitvoeren in de Configuration Manager-console  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage**, en klik vervolgens op **rapporten** om de beschikbare rapporten weer te geven.  

    > [!IMPORTANT]  
    >  In deze versie van Configuration Manager, de **alle inhoud** rapporten enkel pakketten weer, geen toepassingen.  

    > [!TIP]  
    >  Als er geen rapporten worden weergegeven, controleert u het reporting servicepunt is geïnstalleerd en geconfigureerd. Zie voor meer informatie [Configuring reporting](configuring-reporting.md).  

3.  Selecteer het rapport dat u uitvoeren wilt, en klik vervolgens op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **uitvoeren** om het rapport te openen.  

4.  Wanneer er parameters vereist, geeft u de parameters en klik vervolgens op **View-rapport**.  

#### <a name="to-run-a-report-in-a-web-browser"></a>Een rapport uitvoeren in een webbrowser  

1.  In uw webbrowser de Report Manager-URL invoeren, bijvoorbeeld **http:\/\/Server1\/rapporten**. U kunt de Report Manager-URL bepalen op de **URL Report Manager** pagina in Reporting Services Configuration Manager.  

2.  In Report Manager, klikt u op de rapportmap voor Configuration Manager gebruikt, bijvoorbeeld **ConfigMgr\_CAS**.  

    > [!TIP]  
    >  Als er geen rapporten worden weergegeven, controleert u het reporting servicepunt is geïnstalleerd en geconfigureerd. Zie voor meer informatie [Configuring reporting](configuring-reporting.md).  

3.  Klik op de rapportcategorie voor het rapport dat u wilt uitvoeren en klik vervolgens op de koppeling voor het rapport. Het rapport wordt geopend in Rapportbeheer.  

4.  Wanneer er parameters vereist, geeft u de parameters en klik vervolgens op **View-rapport**.  

###  <a name="BKMK_ModifyReportProperties"></a>De eigenschappen van een Configuration Manager-rapport wijzigen  
 In de Configuration Manager-console kunt u de eigenschappen voor een rapport, zoals de rapportnaam en -beschrijving, maar gebruik Rapportbeheer om de eigenschappen te wijzigen. Gebruik de volgende procedure om de eigenschappen voor een Configuration Manager-rapport.  

#### <a name="to-modify-report-properties-in-report-manager"></a>Rapporteigenschappen in Rapportbeheer wijzigen  

1.  In uw webbrowser de Report Manager-URL invoeren, bijvoorbeeld **http:\/\/Server1\/rapporten**. U kunt de Report Manager-URL bepalen op de **URL Report Manager** pagina in Reporting Services Configuration Manager.  

2.  In Report Manager, klikt u op de rapportmap voor Configuration Manager gebruikt, bijvoorbeeld **ConfigMgr\_CAS**.  

    > [!TIP]  
    >  Als er geen rapporten worden weergegeven, controleert u het Reporting Services-punt is geïnstalleerd en geconfigureerd. Zie voor meer informatie [rapportage configureren](configuring-reporting.md)  

3.  Klik op de rapportcategorie voor het rapport waarvoor u eigenschappen wilt wijzigen en klik vervolgens op de koppeling voor het rapport. Het rapport wordt geopend in Rapportbeheer.  

4.  Klik op de **eigenschappen** tabblad. U kunt de rapportnaam en -beschrijving wijzigen.  

5.  Wanneer u klaar bent, klikt u op **toepassen**. De rapporteigenschappen zijn bewaard op de rapportserver en de Configuration Manager-console haalt de bijgewerkte rapporteigenschappen voor het rapport.  

###  <a name="BKMK_EditReport"></a>Een Configuration Manager-rapport bewerken  
 Wanneer een bestaand Configuration Manager-rapport de informatie die u hebt niet ophaalt of niet zorgt voor de indeling of ontwerp dat u wilt, kunt u het rapport in Report Builder bewerken.  

> [!NOTE]  
>  U kunt ook kiezen een bestaand rapport te klonen Hiertoe opent u het voor het bewerken en te klikken op **OpslaanAls** opslaan als een nieuw rapport.  

> [!IMPORTANT]  
>  De gebruikersaccount moet beschikken over **Site wijzigen** machtiging en **rapport wijzigen** machtigingen voor de specifieke objecten gekoppeld aan het rapport dat u wilt wijzigen.  

> [!IMPORTANT]  
>  Wanneer Configuration Manager wordt bijgewerkt naar een nieuwere versie, worden de vooraf gedefinieerde rapporten overschreven door nieuwe rapporten. Als u een vooraf gedefinieerd rapport wijzigt, moet u back-up het rapport voordat u de nieuwe versie installeert en vervolgens het rapport in Reporting Services herstellen. Als u belangrijke wijzigingen aan een vooraf gedefinieerd rapport doorvoert, overweeg in plaats daarvan een nieuw rapport maken. Nieuwe rapporten die u voordat u een site bewerkt maakt worden niet overschreven.  

 Gebruik de volgende procedure de eigenschappen van een Configuration Manager-rapport te bewerken.  

#### <a name="to-edit-report-properties"></a>Rapporteigenschappen bewerken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage**, en klik vervolgens op **rapporten** om de beschikbare rapporten weer te geven.  

3.  Selecteer het rapport dat u wijzigen wilt, en klik vervolgens op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **bewerken**. Uw gebruikersaccount en wachtwoord invoeren als u hierom wordt gevraagd en klik vervolgens op **OK**. Als Report Builder niet op de computer is geïnstalleerd, wordt u gevraagd om deze te installeren. Klik op **uitvoeren** voor het installeren van Report Builder is nodig om te wijzigen en rapporten te maken.  

4.  In Report Builder de geschikte rapportinstellingen wijzigen en klik vervolgens op **opslaan** het rapport wilt opslaan op de rapportserver.  

###  <a name="BKMK_CreateModelBasedReport"></a>Maak een model\-gebaseerd rapport  
 Een model\-op basis van rapport kunt u mogelijk interactief de items die u wilt opnemen in uw rapport selecteren. Zie voor meer informatie over het maken van aangepaste rapportmodellen [aangepaste rapportmodellen maken voor System Center Configuration Manager in SQL Server Reporting Services](creating-custom-report-models-in-sql-server-reporting-services.md).  

> [!IMPORTANT]  
>  De gebruikersaccount moet beschikken over **Site wijzigen** machtiging voor het maken van een nieuw rapport. De gebruiker kan enkel een rapport maken in mappen waarvoor de gebruiker **rapport wijzigen** machtigingen.  

 Gebruik de volgende procedure voor het maken van een model\-op basis van Configuration Manager-rapport.  

#### <a name="to-create-a-model-based-report"></a>Maken van een model\-gebaseerd rapport  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage** en klikt u op **rapporten**.  

3.  Op de **Start** tabblad, in de **maken** sectie, klikt u op **rapport maken** openen van de **Wizard rapport maken**.  

4.  Op de **informatie** pagina, configureer de volgende instellingen:  

    -   **Type**: Selecteer **Model\-gebaseerd rapport** een rapport maken in Report Builder met behulp van een Reporting Services-model.  

    -   **Naam**: Geef een naam voor het rapport.  

    -   **Beschrijving**: Geef een beschrijving voor het rapport.  

    -   **Server**: Geeft de naam van de rapportserver waarop u dit rapport maakt.  

    -   **Pad**: Klik op **Bladeren** naar een map waarin u wilt opslaan van het rapport opgeven.  

     Klik op **Volgende**.  

5.  Op de **modelselectie** pagina, selecteert u een beschikbaar model in de lijst die u gebruikt om dit rapport te maken. Wanneer u het rapportmodel, selecteert de **Preview** sectie vindt u de SQL Server-weergaven en entiteiten die beschikbaar zijn gesteld door het geselecteerde rapportmodel.  

6.  Bekijk de instellingen op de pagina **Samenvatting** . Klik op **vorige** de instellingen wijzigen of klik op **volgende** aan het rapport maken in Configuration Manager.  

7.  Op de **bevestiging** pagina, klikt u op **sluiten** naar de wizard af te sluiten en open vervolgens Report Builder om de rapportinstellingen te configureren. Uw gebruikersaccount en wachtwoord invoeren als u hierom wordt gevraagd en klik vervolgens op **OK**. Als Report Builder niet op de computer is geïnstalleerd, wordt u gevraagd om deze te installeren. Klik op **uitvoeren** voor het installeren van Report Builder is nodig om te wijzigen en rapporten te maken.  

8.  In Microsoft Report Builder de indeling van het rapport te maken, selecteer gegevens in de beschikbare weergaven van SQL Server, voeg parameters toe aan het rapport, enzovoort. Zie de Report Builder Help voor meer informatie over het gebruik van Report Builder voor een nieuw rapport maken.  

9. Klik op **uitvoeren** uw rapport uit te voeren. Controleer dat het rapport geeft de informatie die u verwacht. Klik op **ontwerp** om terug te keren naar de ontwerpweergave om te wijzigen van het rapport, indien nodig.  

10. Klik op **opslaan** het rapport wilt opslaan op de rapportserver. U kunt uitvoeren en wijzigen van het nieuwe rapport in de **rapporten** knooppunt in de **bewaking** werkruimte.  

###  <a name="BKMK_CreateSQLBasedReport"></a>Maken van een SQL\-gebaseerd rapport  
 Een SQL\-op basis van rapport kunt u gegevens ophalen die is gebaseerd op een rapport SQL-instructie.  

> [!IMPORTANT]  
>  Wanneer u een SQL-instructie voor een aangepast rapport maakt, Verwijs niet direct naar SQL Server-tabellen. In plaats hiervan, naar rapportage SQL Server-weergaven \(weergeven van namen die met v beginnen\_ \) uit de sitedatabase. U kunt ook verwijzen naar openbaar opgeslagen procedures \(opgeslagen procedure van namen die met sp beginnen\_ \) uit de sitedatabase.  

> [!IMPORTANT]  
>  De gebruikersaccount moet beschikken over **Site wijzigen** machtiging voor het maken van een nieuw rapport. De gebruiker kan enkel een rapport maken in mappen waarvoor de gebruiker **rapport wijzigen** machtigingen.  

 Gebruik de volgende procedure voor het maken van een SQL\-op basis van Configuration Manager-rapport.  

#### <a name="to-create-a-sql-based-report"></a>Maken van een SQL\-gebaseerd rapport  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte **Bewaking** **Rapportage**uit en klik vervolgens op **Rapporten**.  

3.  Op de **Start** tabblad, in de **maken** sectie, klikt u op **rapport maken** openen van de **Wizard rapport maken**.  

4.  Op de **informatie** pagina, configureer de volgende instellingen:  

    -   **Type**: Selecteer **SQL\-gebaseerd rapport** een rapport maken in Report Builder met behulp van een SQL-instructie.  

    -   **Naam**: Geef een naam voor het rapport.  

    -   **Beschrijving**: Geef een beschrijving voor het rapport.  

    -   **Server**: Geeft de naam van de rapportserver waarop u dit rapport maakt.  

    -   **Pad**: Klik op **Bladeren** naar een map waarin u wilt opslaan van het rapport opgeven.  

     Klik op **Volgende**.  

5.  Bekijk de instellingen op de pagina **Samenvatting** . Klik op **vorige** de instellingen wijzigen of klik op **volgende** aan het rapport maken in Configuration Manager.  

6.  Op de **bevestiging** pagina, klikt u op **sluiten** de wizard af te sluiten en open de Report Builder om de rapportinstellingen te configureren. Uw gebruikersaccount en wachtwoord invoeren als u hierom wordt gevraagd en klik vervolgens op **OK**. Als Report Builder niet op de computer is geïnstalleerd, wordt u gevraagd om deze te installeren. Klik op **uitvoeren** voor het installeren van Report Builder is nodig om te wijzigen en rapporten te maken.  

7.  In Microsoft Report Builder de SQL-instructie voor het rapport of de SQL-instructie maken door kolommen te gebruiken in beschikbare SQL Server-weergaven, parameters toevoegen aan het rapport, enzovoort.  

8.  Klik op **uitvoeren** uw rapport uit te voeren. Controleer dat het rapport geeft de informatie die u verwacht. Klik op **ontwerp** om terug te keren naar de ontwerpweergave om te wijzigen van het rapport, indien nodig.  

9. Klik op **opslaan** het rapport wilt opslaan op de rapportserver. U kunt het nieuwe rapport uitvoeren in de **rapporten** knooppunt in de **bewaking** werkruimte.  

##  <a name="BKMK_ManageReportSubscriptions"></a>Rapportabonnementen beheren  
 Met rapportabonnementen in SQL Server Reporting Services kunt u de automatische levering configureren van rapporten via e-mail of bestandsshare met regelmatige tussenpozen. Gebruik de **Wizard voor abonnement** in System Center 2012 Configuration Manager om rapportabonnementen te configureren.  

###  <a name="BKMK_ReportSubscriptionFileShare"></a>Een rapportabonnement maken om een rapport leveren via bestandsshare  
 Wanneer u een rapportabonnement te leveren van een rapport met een bestandsshare maakt, wordt het rapport in de opgegeven indeling gekopieerd naar de bestandsshare die u opgeeft. U kunt zich abonneren op en bezorging slechts voor één rapport verzoeken tegelijk.  

 Anders dan bij rapporten die gehost en beheerd door een rapportserver, zijn rapporten die geleverd worden aan een bestandsshare statische bestanden. Interactieve functies die zijn gedefinieerd voor het rapport werken niet voor rapporten die worden opgeslagen als bestanden op het bestandssysteem. Interactieve functies worden weergegeven als statische elementen. Als het rapport grafieken bevat, wordt de standaardpresentatie gebruikt. Als de rapporten doorgelinkt worden naar een ander rapport, wordt de link weergegeven als statische tekst. Als u interactieve functies in een geleverd rapport behouden, gebruikt u de levering via e-mail. Zie voor meer informatie over levering via e-mail, de [een rapportabonnement maken om een rapport via e-mail te leveren](#BKMK_ReportSubscriptionEmail) verderop in dit onderwerp.  

 Wanneer u een abonnement dat levering via bestandsshare gebruikt maakt, moet u een bestaande map als de doelmap opgeven. De rapportserver maakt geen mappen op het bestandssysteem. De map die u opgeeft, moeten toegankelijk zijn via een netwerkverbinding. Wanneer u de doelmap in een abonnement opgeeft, wordt een UNC-pad en Neem geen afsluitende backslash-tekens op in het mappad. Bijvoorbeeld, een geldig UNC-pad voor de doelmap is: \\ \\ &lt;servername\>\\reportfiles\\operations\\2011.  

 Rapporten kunnen worden weergegeven in verschillende bestandsindelingen, zoals MHTML of Excel. Sla het rapport in een specifiek bestandsformaat, selecteert het weergaveformaat bij het maken van uw abonnement. Bijvoorbeeld slaat Excel gekozen het rapport als een Microsoft Excel-bestand. Hoewel u elk ondersteund weergaveformaat selecteren kunt, werken sommige formaten beter dan andere weergeven van een bestand.  

 Gebruik de volgende procedure om een rapportabonnement een rapport te leveren aan bestandsshare te maken.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-to-a-file-share"></a>Een rapportabonnement een rapport te leveren aan bestandsshare maken  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **rapportage** en klikt u op **rapporten** om de beschikbare rapporten weer te geven. U kunt een rapportmap selecteren om enkel de rapporten die gekoppeld aan de map zijn.  

3.  Selecteer het rapport dat u wilt toevoegen aan het abonnement en klikt u op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **abonnement maken** openen de **Wizard voor abonnement**.  

4.  Op de **levering van abonnement** pagina, configureer de volgende instellingen:  

    -   Rapport geleverd door: Selecteer **Windows bestandsshare** aan het rapport naar een bestandsshare te leveren.  

    -   **Bestandsnaam**: Geef de bestandsnaam op voor het rapport. Het rapportbestand bevat standaard geen extensie. Selecteer **bestandsextensie toevoegen bij gemaakt** automatisch een bestandsnaamextensie aan dit rapport op basis van de renderindeling toevoegen.  

    -   **Pad**: Geef een UNC-pad naar een bestaande map waar u dit rapport te leveren \(bijvoorbeeld \\ \\ &lt;servernaam\>\\&lt;servershare\>\\&lt;rapportmap\>\).  

        > [!NOTE]  
        >  Naam van de gebruiker opgegeven hoger op deze pagina moet toegang hebben tot deze servershare en over schrijfbevoegdheden beschikken op de doelmap.  

    -   **Renderindeling**: Selecteer een van de volgende indelingen voor het rapportbestand:  

        -   **XML-bestand met rapportgegevens**: Slaat het rapport op in Extensible Markup Language-indeling.  

        -   **CSV \(door komma's gescheiden\)**: Hiermee slaat u het rapport in door komma's\-gescheiden\-indeling van de waarden.  

        -   **TIFF-bestand**: Slaat het rapport op in Tagged Image File Format.  

        -   **Acrobat \(PDF\) bestand**: Slaat het rapport in Acrobat Portable Document Format.  

        -   **HTML 4.0**: Slaat het rapport als een webpagina die alleen zichtbaar met browsers die ondersteuning bieden voor HTML 4.0. Internet Explorer 5 en hoger bieden ondersteuning voor HTML 4.0.  

            > [!NOTE]  
            >  Als uw rapport afbeeldingen bevat, bevat de HTML 4.0-indeling geen ze in het bestand.  

        -   **MHTML \(webarchief\)**: Slaat het rapport op in MIME HTML-indeling \(mhtml\), die kan worden bekeken in veel webbrowser kan worden weergegeven.  

        -   **RPL-Renderer**: Hiermee slaat u het rapport in Report pagina-indeling \(RPL\) indeling.  

        -   **Excel**: Slaat het rapport als een Microsoft Excel-werkblad.  

        -   **Word**: Slaat het rapport als een Microsoft Word-document.  

    -   **Gebruikersnaam**: Geef een Windows-gebruikersaccount met machtigingen voor toegang tot de doelservershare en -map. Het gebruikersaccount moet toegang krijgen tot deze servershare en schrijfmachtigingen hebben op de doelmap.  

    -   **Wachtwoord**: Geef het wachtwoord voor het Windows-gebruikersaccount. In **wachtwoord bevestigen**, re\-voert u het wachtwoord.  

    -   Selecteer een van de volgende opties voor het configureren van het gedrag als een bestand met dezelfde naam in de doelmap bestaat:  

        -   **Een bestaand bestand overschrijven met een nieuwere versie**: Hiermee geeft u op dat wanneer het rapportbestand al bestaat, de nieuwe versie wordt overschreven door het.  

        -   **Een bestaand bestand niet overschrijven**: Hiermee geeft u op dat, wanneer het rapportbestand al bestaat, er geen actie wordt.  

        -   **Bestandsnamen als nieuwe versies worden toegevoegd**: Hiermee geeft u op dat, wanneer het rapportbestand al bestaat, een getal is toegevoegd aan het nieuwe rapport in de bestandsnaam te onderscheiden van andere versies.  

    -   **Beschrijving**: Hiermee geeft u de beschrijving voor het rapportabonnement.  

     Klik op **Volgende**.  

5.  Op de **Abonnementplanning** pagina, selecteer een van de volgende leveringsplanningopties voor het rapportabonnement:  

    -   **Gedeelde planning gebruiken**: Een gedeelde planning is een vooraf gedefinieerde planning die door andere rapportabonnementen kan worden gebruikt. Schakel dit selectievakje in en selecteer vervolgens een gedeelde planning in de lijst als eventueel opgegeven.  

    -   **Nieuw schema maken**: Configureer de planning waarin dit rapport wordt uitgevoerd, inclusief het interval, de starttijd en datum en de einddatum van dit abonnement.  

6.  Op de **Abonnementsparameters** pagina, geef de parameters op voor dit rapport die worden gebruikt wanneer dit zonder toezicht wordt uitgevoerd. Wanneer er geen parameters voor het rapport, wordt deze pagina niet weergegeven.  

7.  Op de **samenvatting** pagina, Controleer de instellingen van het rapport. Klik op **vorige** de instellingen wijzigen of klik op **volgende** om het rapportabonnement te maken.  

8.  Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten. Controleer of het rapportabonnement is gemaakt. U kunt weergeven en wijzigen met rapportabonnementen in de **abonnementen** knooppunt onder **rapportage** in de **bewaking** werkruimte.  

###  <a name="BKMK_ReportSubscriptionEmail"></a>Een rapportabonnement maken om een rapport via e-mail te leveren  
 Wanneer u een rapportabonnement maakt om te leveren van een rapport via e-mail, een e-mailbericht is verzonden naar de ontvangers die u configureert en wordt het rapport als bijlage toegevoegd. De rapportserver niet valideren e-mailadressen of e-mailadressen verkrijgen van een e-mailserver. U moet van tevoren weten welke e-mailadressen die u wilt gebruiken. Standaard kunt u e-rapporten naar geldige e-mailaccounts binnen of buiten uw organisatie. U kunt een of beide van de volgende opties voor e-mailbezorging selecteren:  

-   Een melding en een hyperlink verzenden naar het gegenereerde rapport.  

-   Een ingesloten of bijgevoegd rapport verzenden. De renderindeling en browser bepalen of het rapport wordt ingesloten of bijgevoegd. Als uw browser ondersteuning biedt voor HTML 4.0 en MHTML en u de MHTML selecteert \(webarchief\) rendering indeling, wordt het rapport ingesloten als deel van het bericht. Alle andere renderindelingen \(CSV, PDF, Word, enzovoort\) leveren rapporten als bijlage. Reporting Services controleert de grootte van de bijlage of het bericht voordat het rapport wordt verzonden. Als de bijlage of het bericht is groter dan de maximale door uw e-mailserver toegestane limiet, wordt het rapport niet geleverd.  

> [!IMPORTANT]  
>  U moet de e-mailinstellingen configureren in Reporting Services voor de **e** bezorgingsoptie beschikbaar. Zie voor meer informatie over het configureren van de e-mailinstellingen in Reporting Services [een rapportserver configureren voor levering via E-mail](http://go.microsoft.com/fwlink/p/?LinkId=226668) in SQL Server Books Online.  

 Gebruik de volgende procedure om een rapportabonnement een rapport te leveren via e-mailberichten te maken.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-by-email"></a>Een rapportabonnement een rapport te leveren via e-mail maken  

-   Klik in de Configuration Manager-console op **bewaking**.  

-   In de **bewaking** werkruimte Vouw **rapportage** en klikt u op **rapporten** om de beschikbare rapporten weer te geven. U kunt een rapportmap selecteren om het enige lijst de rapporten die gekoppeld aan de map zijn.  

-   Selecteer het rapport dat u wilt toevoegen aan het abonnement en klikt u op de **Start** tabblad, in de **rapportgroep** sectie, klikt u op **abonnement maken** openen de **Wizard voor abonnement**.  

-   Op de **levering van abonnement** pagina, configureer de volgende instellingen:  

    -   **Rapport geleverd door**: Selecteer **E\-e** voor het rapport als bijlage in een e-mailbericht.  

    -   **To**: Geef een geldig e-mailadres voor het verzenden van dit rapport.  

        > [!NOTE]  
        >  U kunt meerdere e-mailontvangers invoeren door elk e-mailadres te scheiden met een puntkomma.  

    -   **Cc**: Geef desgewenst een e-mailadres kopie van dit rapport.  

    -   **Bcc**: Geef desgewenst een e-mailadres voor een controlekopie van dit rapport.  

    -   **Antwoord aan**: Geef het antwoordadres op dat moet worden gebruikt als de ontvanger het e-mailbericht beantwoordt.  

    -   **Onderwerp**: Geef een onderwerpregel op voor het abonnement e-mailbericht.  

    -   **Prioriteit**: Selecteer de prioriteitsmarkering voor dit e-mailbericht. Select **Low**, **Normal**, or **High**. De prioriteitsinstelling wordt door Microsoft Exchange gebruikt om in te stellen van een vlag die het belang aangeeft van het e-mailbericht.  

    -   **Opmerking**: Geef tekst op die worden toegevoegd aan de hoofdtekst van het abonnement e-mailbericht.  

    -   **Beschrijving**: Geef de beschrijving voor dit rapportabonnement.  

    -   **Koppeling opnemen**: Neemt een URL naar het geabonneerde rapport in de hoofdtekst van het e-mailbericht.  

    -   **Rapport opnemen**: Opgeven of het rapport is gekoppeld aan de e\-e-mailbericht. De indeling waarin het rapport als bijlage is opgegeven in de **Renderindeling** lijst.  

    -   **Renderindeling**: Selecteer een van de volgende indelingen voor het bijgevoegde rapport:  

        -   **XML-bestand met rapportgegevens**: Slaat het rapport op in Extensible Markup Language-indeling.  

        -   **CSV \(door komma's gescheiden\)**: Hiermee slaat u het rapport in door komma's\-gescheiden\-indeling van de waarden.  

        -   **TIFF-bestand**: Slaat het rapport op in Tagged Image File Format.  

        -   **Acrobat \(PDF\) bestand**: Slaat het rapport in Acrobat Portable Document Format.  

        -   **MHTML \(webarchief\)**: Slaat het rapport op in MIME HTML-indeling \(mhtml\), die kan worden bekeken in veel webbrowser kan worden weergegeven.  

        -   **Excel**: Slaat het rapport als een Microsoft Excel-werkblad.  

        -   **Word**: Slaat het rapport als een Microsoft Word-document.  

-   Op de **Abonnementplanning** pagina, selecteer een van de volgende leveringsplanningopties voor het rapportabonnement:  

    -   **Gedeelde planning gebruiken**: Een gedeelde planning is een vooraf gedefinieerde planning die door andere rapportabonnementen kan worden gebruikt. Schakel dit selectievakje in en selecteer vervolgens een gedeelde planning in de lijst als eventueel opgegeven.  

    -   **Nieuw schema maken**: Configureer de planning waarin dit rapport wordt uitgevoerd, inclusief het interval, begintijd en datum en de einddatum van dit abonnement.  

-   Op de **Abonnementsparameters** pagina, geef de parameters op voor dit rapport die worden gebruikt wanneer dit zonder toezicht wordt uitgevoerd. Wanneer er geen parameters voor het rapport, wordt deze pagina niet weergegeven.  

-   Op de **samenvatting** pagina, Controleer de instellingen van het rapport. Klik op **vorige** de instellingen wijzigen of klik op **volgende** om het rapportabonnement te maken.  

-   Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten. Controleer of het rapportabonnement is gemaakt. U kunt weergeven en wijzigen met rapportabonnementen in de **abonnementen** knooppunt onder **rapportage** in de **bewaking** werkruimte.  

