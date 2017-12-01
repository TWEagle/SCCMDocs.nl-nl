---
title: Technische Preview 1706
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1706 voor System Center Configuration Manager.
ms.custom: na
ms.date: 09/15/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca3b4714-2a16-495e-8a17-1d87991d5556
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: d7819dd71a37bc581b629ac180f657134495f50c
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1706-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1706 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1706 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md) om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Bekende problemen in deze Technical Preview:**

-   **Verplaatsen van distributiepunt** -de opties in de console voor het verplaatsen van een distributiepunt tussen sites in deze release vanwege de technical preview-limiet van een enkele primaire site kunnen niet worden gebruikt.

-   **Instellingen voor naleving apparaten** -u kunt tegengestelde gedrag ervaren wanneer met behulp van de twee van de nieuwe instellingen voor naleving van apparaten:
    - **Blokkeren USB-foutopsporing op apparaat**
    - **Blokkeren voor apps van onbekende bronnen**

        Bijvoorbeeld, als beheerders instellen **blok USB-foutopsporing op apparaat** naar **true**, alle apparaten waarvoor geen USB-foutopsporing is ingeschakeld, worden gemarkeerd als niet-compatibel.

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improved-boundary-groups-for-software-update-points"></a>Verbeterde grensgroepen voor software-updatepunten
<!-- 1324591 -->
Deze release bevat verbeteringen voor de werking van software-updatepunten aan grensgroepen. Het volgende bevat een overzicht van het nieuwe terugval gedrag:
-   Opvang voor software-updatepunten gebruikt een configureerbare tijd nu voor terugvallen neighbor grensgroepen, met een minimale tijd van 120 minuten.

-   Onafhankelijk van de alternatieve configuratie probeert een client te bereiken van het laatste software-updatepunt dat wordt gebruikt voor 120 minuten. Lukt die server bereiken gedurende 120 minuten, controleert de client vervolgens de groep met beschikbare software-updatepunten, zodat deze een nieuw kan vinden.

  -   Alle software-updatepunten in de huidige grensgroep van de client worden toegevoegd aan de adresgroep van de client onmiddellijk.

  -   Omdat een client probeert te gebruiken van de oorspronkelijke server gedurende 120 minuten voordat het zoeken van een nieuwe, geen extra servers contact wordt opgenomen pas na twee uur zijn verstreken.

  -   Als terugval naar een neighbor-groep is geconfigureerd voor het minimum van 120 minuten, zal software-updatepunten uit deze grensgroep neighbor onderdeel zijn van de client-groep met beschikbare servers.

-   Na een failover naar de oorspronkelijke server te bereiken voor twee uur, wordt de client overschakelt naar een kortere cyclus voor het verbinden met een nieuw software-updatepunt.

    Dit betekent dat als een client geen verbinding maken met een nieuwe server, het snel de volgende server selecteert in de groep met beschikbare servers en probeert contact dat een.

  -   Deze cyclus wordt vervolgd totdat de client verbinding met een software maakt-updatepunt kan gebruiken.
  -   Totdat de client vindt een software-updatepunt, worden de extra servers toegevoegd aan de groep met beschikbare servers wanneer de terugval tijd voor elke grensgroep neighbor wordt voldaan.

Zie voor meer informatie [software-updatepunten](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) in het onderwerp Grensgroepen voor de huidige vertakking.


## <a name="site-server-role-high-availability"></a>Beschikbaarheid van de site server-rol
<!-- 1128774 -->
Hoge beschikbaarheid voor de site server-rol is een Configuration Manager op basis van oplossing voor het installeren van de server van een bijkomende primaire site in *passieve* modus. De siteserver van de passieve modus is daarnaast aan uw bestaande primaire site-server die zich in *Active* modus. Een siteserver passieve modus is beschikbaar voor onmiddellijk gebruik wanneer deze nodig is.

Een primaire siteserver in de passieve modus:
-   Maakt gebruik van dezelfde sitedatabase als de actieve siteserver.
-   Ontvangt een kopie van de actieve site servers Inhoudsbibliotheek, die vervolgens synchroon wordt gehouden.
-   Geen gegevens worden geschreven naar de sitedatabase, zolang het is in de passieve modus.
-   Ondersteunt geen installatie of verwijdering van de optionele sitesysteemrollen zolang het is in de passieve modus.

Als u de passieve modus siteserver uw siteserver actieve modus, Promoveer u handmatig deze. Hiermee schakelt u de actieve siteserver als de passieve siteserver. De sitesysteemrollen die beschikbaar op de oorspronkelijke server in de modus active zijn blijven beschikbaar, zolang die computer toegankelijk is. Alleen de siteserverrol is overgeschakeld tussen actieve en passieve modus.

Als u wilt installeren op een siteserver passieve modus, gebruikt u de **maken Wizard Sitesysteemserver** voor het configureren van een nieuwe siteserver met het Type **primaire siteserver** en een modus van **passieve**. De wizard Setup van Configuration Manager wordt vervolgens wordt uitgevoerd op de opgegeven server voor het installeren van de nieuwe siteserver in de passieve modus. Nadat de installatie is voltooid, houdt de modus active server de passieve modus-siteserver en de Inhoudsbibliotheek synchroon met wijzigingen of configuraties die u in de actieve siteserver aanbrengt.

### <a name="prerequisites-and-limitations"></a>Vereisten en beperkingen
-   Één siteserver in de passieve modus wordt ondersteund op elke primaire site.

-   De siteserver in de passieve modus kan nu on-premises of cloud-gebaseerde in Azure.

-   De actieve modus en de passieve modus siteservers moet in hetzelfde domein.

-   De actieve modus en de passieve modus siteservers moeten gebruiken voor dezelfde sitedatabase, moet extern van de computers van elke siteserver.

    -   De SQL Server die als host fungeert voor de database kunt een standaardexemplaar, benoemd exemplaar, SQL Server-cluster of een AlwaysOn-beschikbaarheidsgroep gebruiken.

    -   De siteserver in de passieve modus is geconfigureerd voor gebruik van dezelfde sitedatabase als de modus active-siteserver. Echter, de passieve modus siteserver gebruikt geen die database pas nadat deze is gepromoveerd naar de modus active.

-   De computer waarop de server van de passieve modus wordt uitgevoerd:

    -   Moet voldoen aan de [vereisten voor het installeren van een primaire site](https://docs.microsoft.com/en-us/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#primary-sites-and-the-central-administration-site).

    -   Installeert met behulp van de bronbestanden die overeenkomen met de versie van de siteserver actieve modus.

    -   Geen een sitesysteemrol van elke site voordat u de passieve modussite installeert.

-   De actieve en passieve modus site server-computers kunnen uitvoeren verschillende besturingssystemen worden uitgevoerd of servicepack-versies, zolang ze beide ondersteund door uw versie van Configuration Manager blijven.

-   Promotie van de passieve modus siteserver naar de modus active server is handmatig. Er is geen automatische failover.

-   Sitesysteemrollen kunnen alleen worden geïnstalleerd op de siteserver die in de actieve modus.

    -   Een siteserver in de actieve modus ondersteunt alle sitesysteemrollen. U kunt sitesysteemrollen niet installeren op de server wanneer deze in de passieve modus.

    -   Sitesysteemrollen die gebruikmaken van een database (zoals het rapportagepunt) hebben dat de database op een server die de actieve modus Extern en passieve modus siteservers.

    -   De SMS-provider wordt niet geïnstalleerd op de siteserver in de passieve modus. Omdat u verbinding met een SMS-provider voor de site maken moet te promoveren handmatig de passieve modus siteserver naar de actieve modus, wordt u aangeraden [ten minste één extra exemplaar van de provider installeren](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider) op een andere computer.

**Bekende probleem**:   
Met deze release **Status** voor de volgende voorwaarden worden weergegeven in de console als numerieke waarden in plaats van leesbare tekst:
-   131071 – installatie van de server site is mislukt
-   720895 – site server-rol verwijderen is mislukt
-   851967 – Failover is mislukt

### <a name="add-a-site-server-in-passive-mode"></a>Toevoegen van een siteserver in de passieve modus
1.  Ga in de console naar **beheer** > **siteconfiguratie** > **Sites** en start de [toevoegen Wizard sitesysteemrollen](/sccm/core/servers/deploy/configure/install-site-system-roles). U kunt ook de **maken Wizard Sitesysteemserver**.

2.  Op de **algemene** pagina server opgeven die als host voor de siteserver van de passieve modus fungeert. De server die u opgeeft hosten niet sitesysteemrollen voordat u een siteserver installeert in de passieve modus.

3.  Op de **Systeemrolselectie** pagina, selecteert u alleen **primaire siteserver in de passieve modus**.

4.  Om de wizard hebt voltooid, moet u de volgende informatie die wordt gebruikt voor het installatieprogramma uitvoeren en de site server-functie installeren op de opgegeven server opgeven:
    -   Kopieer de installatiebestanden van de siteserver van actief naar de nieuwe siteserver van de passieve modus, of geef een pad naar een locatie waarin de inhoud van de actieve site-server **CD. Meest recente** map.

    -   Geef de dezelfde Sitedatabaseserver en de databasenaam gebruikt door de siteserver actieve modus.

5.  Vervolgens installeert Configuration Manager de siteserver in de passieve modus op de opgegeven server.

Voor gedetailleerde installatiestatus, gaat u naar **beheer** > **siteconfiguratie** > **Sites**.
-   De status voor de siteserver in de passieve modus wordt weergegeven als **installeren**.

-   Selecteer de server en klik vervolgens op **Status weergeven** openen **Site-serverstatus installatie** voor meer informatie gedetailleerde.



### <a name="promote-the-passive-mode-site-server-to-active-mode"></a>De passieve modus siteserver promoveert naar actieve modus
Als u wijzigen in de passieve modus siteserver actieve modus wilt, u dit doen via de **knooppunten** deelvenster in **beheer** > **siteconfiguratie** > **Sites**. Zolang u toegang hebt tot een exemplaar van de SMS-provider, kunt u toegang tot de site als deze wijziging wilt aanbrengen.
1.  In de **knooppunten** deelvenster van de Configuration Manager-console, selecteer de siteserver in de passieve modus en kies vervolgens vanuit het lint **opwaarderen in actief**.

2.  Eenvoudige **Status** voor de server die u promoveert wordt weergegeven in de **knooppunten** deelvenster als **promoveren**.

3.  Nadat de promotie voltooid is, de **Status** kolom bevat **OK** voor zowel de nieuwe *Active* modus siteserver, en voor de nieuwe *passieve* modus siteserver.

4.  In **beheer** > **siteconfiguratie** > **Sites**, de naam van de primaire siteserver bevat nu de naam van de nieuwe *Active* modus siteserver.
Gedetailleerde status weergegeven, gaat u naar **bewaking** > **Site-serverstatus**.
    -   De **modus** kolom geeft aan welke server *Active* of *passieve*.

    -   Tijdens het promoveren van een server uit de passieve modus in de modus active, selecteer de siteserver die u promoveert naar actief en kies vervolgens **Status weergeven** vanuit het lint. Hiermee opent u de **Site-serverstatus promotie** venster waarin u aanvullende informatie over het proces.

Wanneer een siteserver in de modus active wordt overgeschakeld naar de passieve modus, wordt alleen de sitesysteemrol passieve gemaakt. Alle andere sitesysteemrollen die op die computer zijn geïnstalleerd blijft actief en toegankelijk is voor clients.


### <a name="daily-monitoring"></a>Dagelijks bewaking
Wanneer u een primaire site in de passieve modus, moet u het bewaken dagelijkse om ervoor te zorgen blijft deze synchroon met de modus active-siteserver en klaar voor gebruik. Om dit te doen, gaat u naar **bewaking** > **Site-serverstatus**. Hier kunt u de actieve modus en de passieve modus siteservers weergeven.

De **samenvatting** tabblad:
-   De **modus** kolom geeft aan welke server actief of passief is.
-   De **Status** kolomlijst **OK** wanneer de server passieve modus is gesynchroniseerd met de modus active-server.
-   U kunt aanvullende informatie over de status van het synchroniseren van inhoud op **status weergeven** van de synchronisatiestatus van de inhoud. Hiermee opent u de Inhoudsbibliotheek tabblad waar u proberen kunt om op te lossen problemen met synchronisatie van inhoud.

De **Inhoudsbibliotheek** tabblad:
-   Weergave de **status** voor inhoud die wordt gesynchroniseerd vanaf de actieve siteserver naar de siteserver van de passieve modus.
-   Kunt u inhoud met een status van **mislukt**, en kies vervolgens **synchroniseren van de geselecteerde items** vanuit het lint. Deze actie wordt geprobeerd om te synchroniseren die inhoud van de bron van de inhoud naar de siteserver van de passieve modus. Tijdens het herstel van de status wordt weergegeven als **Bezig**, en wanneer deze gesynchroniseerd is, wordt als **geslaagd**.

### <a name="try-it-out"></a>Probeer het nu!
Voer de volgende taken en klikt u vervolgens Stuur ons **Feedback** van de **Start** tabblad van het lint te laten weten hoe het is gegaan:
-   Ik kan een primaire site installeren in de passieve modus.
-   Ik kan de passieve modus siteserver kunt u de modus active server promoveert via de console en Bevestig de wijziging van de status van siteservers.


## <a name="include-trust-for-specific-files-and-folders-in-a-device-guard-policy"></a>Vertrouwen voor specifieke bestanden en mappen in een beleid Device Guard opnemen
<!-- 1324676 -->
In deze release toegevoegd meer mogelijkheden voor [Device Guard](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager) beleidsbeheer

U kunt vertrouwen voor specifieke bestanden of mappen nu desgewenst toevoegen in een beleid Device Guard. Hiermee kunt u:

1.  Problemen oplossen met beheerd installatieprogramma gedrag
2.  Vertrouwensrelatie van LOB-apps die met Configuration Manager kunnen niet worden geïmplementeerd
3.  Apps die zijn opgenomen in de installatiekopie van een besturingssysteem-implementatie, vertrouwen.

### <a name="try-it-out"></a>Probeer het nu!

1.  Tijdens het maken van een beleid Device Guard op het tabblad opnames van de wizard beleid voor Device Guard maken, klikt u op **toevoegen**.
2.  In de **vertrouwde bestand toevoegen of map** dialoogvenster geeft u de informatie over het bestand of map die u wilt vertrouwen. U kunt een lokaal bestand of map pad opgeven of u kunt verbinding maken met een extern apparaat waarvoor u gemachtigd bent om te koppelen en geef een bestand of map pad op dat apparaat.
3.  Voltooi de wizard.


## <a name="hide-task-sequence-progress"></a>Voortgang van de takenreeks verbergen
<!-- 1354291 -->
In deze release kunt u bepalen wanneer de voortgang van de takenreeks wordt weergegeven aan eindgebruikers met behulp van een nieuwe variabele. Gebruik in uw takenreeks de **Takenreeksvariabele instellen** stap voor het instellen van de waarde voor de **TSDisableProgressUI** variabele voortgang van de takenreeks weergeven of verbergen. U kunt de stap Takenreeksvariabele instellen meerdere keren in een takenreeks om de waarde voor de variabele te wijzigen. Hiermee kunt u de voortgang van de takenreeks in verschillende secties van de takenreeks weergeven of verbergen.

#### <a name="to-hide-task-sequence-progress"></a>Voortgang van de takenreeks verbergen
In de editor voor takenreeksen, gebruikt u de [Takenreeksvariabele instellen](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) stap voor het instellen van de waarde van de **TSDisableProgressUI** variabele **True** voor het verbergen van de voortgang van de takenreeks.

#### <a name="to-display-task-sequence-progress"></a>Voortgang van de takenreeks weergeven
In de editor voor takenreeksen, gebruikt u de [Takenreeksvariabele instellen](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) stap voor het instellen van de waarde van de **TSDisableProgressUI** variabele **False** om weer te geven van de voortgang van de takenreeks.

## <a name="specify-a-different-content-location-for-install-content-and-uninstall-content"></a>Geef een andere locatie van inhoud voor installatie-inhoud en inhoud verwijderen
<!-- 1097546 -->
In Configuration Manager vandaag de dag u de locatie van de installatie die de installatiebestanden voor een app bevat. Wanneer u een locatie voor de installatie opgeeft, wordt dit ook gebruikt als locatie voor de installatie ongedaan maken voor de inhoud van de toepassing.
Op basis van uw feedback wanneer u wilt verwijderen van een geïmplementeerde toepassing en de app-inhoud niet op de clientcomputer is, wordt vervolgens de client alle van de installatiebestanden van de app opnieuw downloaden voordat de toepassing wordt verwijderd.
U lost dit probleem, kunt u nu zowel een inhoud locatie en een optionele verwijderen Inhoudslocatie installatie opgeven. Bovendien kunt u geen op te geven van een locatie van de inhoud verwijderen.

### <a name="try-it-out"></a>Probeer het nu!

1. Klik in de eigenschappen van het implementatietype van een toepassing, op de **inhoud** tabblad.
2. Configureer de **installeren Inhoudslocatie** die normaal werken.
3. Voor **inhoudsinstellingen verwijderen**, kies een van de volgende:
    - **Hetzelfde zijn als de inhoud wordt geïnstalleerd** -locatie van de dezelfde inhoud ongeacht of u installeert, of verwijderen van de toepassing wordt gebruikt.
    - **Er is geen inhoud verwijderen** -Kies deze optie als u niet wilt dat een uninstall inhoud locatie voor de toepassing op te geven.
    - **Verschilt van de installatie-inhoud** -Kies deze optie als u wilt een Inhoudslocatie verwijderen die verschilt van de locatie van de installatie-inhoud opgeven.
5. Als u hebt geselecteerd **verschillend van installatie-inhoud**, blader naar of typ de locatie van de inhoud van de toepassing die wordt gebruikt om de toepassing te verwijderen.
6. Klik op **OK** implementatie type in het dialoogvenster Eigenschappen te sluiten.


## <a name="accessibility-improvements"></a>Verbeterde toegankelijkheid  
<!--1253000 -->
Dit voorbeeld maakt u kennis met verschillende verbeteringen van de [toegankelijkheidsfuncties](/sccm/core/understand/accessibility-features) in de Configuration Manager-console. Deze omvatten:     

**Nieuwe sneltoetsen te navigeren in de console:**
-   CTRL + M - richten Sets in het hoofdvenster (centrale).
-   CTRL + T - Sets focus naar het bovenste knooppunt in het navigatiedeelvenster. Als de focus al in dit deelvenster is, is de focus ingesteld op het laatste knooppunt die u bezocht.
-   CTRL + I - Sets focus naar de breadcrumb-balk onder het lint.
-   CTRL + L - Sets focus naar de **Search** veld, indien beschikbaar.
-   CTRL + D - Sets focus naar het detailvenster, indien beschikbaar.
-   ALT – wijzigingen focus naar en vanuit het lint.

**Algemene verbeteringen:**
-   Navigatie in het navigatiedeelvenster verbeterd wanneer u de letters van de naam van een knooppunt typt.
-   Er zijn nu toetsenbordnavigatie door middel van de belangrijkste weergave en het lint circulaire.
-   Toetsenbordnavigatie in het detailvenster is nu circulaire. Als u wilt terugkeren naar het vorige object of deelvenster, gebruik Ctrl + D, en vervolgens Shift + TAB.
-   Na het vernieuwen van een werkruimte weergave worden de focus is ingesteld op het hoofdvenster van die werkruimte.
-   Een probleem zodat schermlezers aankondigen van de namen van items in de lijst opgelost.
-   Toegevoegde toegankelijk namen voor meerdere besturingselementen op de pagina die kunnen schermlezers aankondigen van belangrijke informatie.


## <a name="changes-to-the-azure-services-wizard-to-support-upgrade-readiness"></a>Wijzigingen in de Wizard Azure-Services voor de ondersteuning van de gereedheid voor Upgrade
<!-- 1353331 -->
De Wizard Azure-Services vanaf deze release kunt gebruiken voor het configureren van een verbinding van Configuration Manager [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics). Het gebruik van de wizard vereenvoudigt de configuratie van de connector met behulp van de wizard voor een algemene voor gerelateerde Azure-services.   

Hoewel de methode voor het configureren van de verbinding is gewijzigd, zijn de vereisten voor de verbinding en hoe u de gereedheid voor Upgrade gebruiken blijven ongewijzigd.   

### <a name="prerequisites-for-upgrade-readiness"></a>Vereisten voor gereedheid voor Upgrade
De vereisten voor een [verbinding met de gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics#create-a-connection-to-upgrade-readiness) zijn ongewijzigd ten opzichte van die wordt beschreven voor de huidige vertakking van Configuration Manager. Ze worden hier herhaald voor het gemak:  

**Vereisten**
-   Om de verbinding toevoegen, moet eerst uw Configuration Manager-omgeving configureren een [serviceaansluitpunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point) in een [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation). Wanneer u de verbinding aan uw omgeving toevoegen, wordt het Microsoft Monitoring Agent ook installeren op de computer waarop deze sitesysteemrol.
-   Configuration Manager registreren als beheerprogramma 'Webtoepassing en/of Web-API' en krijgt de [client-ID van deze registratie](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
-   Maak een clientsleutel voor het geregistreerde beheerprogramma in Azure Active Directory.
-   In de Azure-beheerportal bieden u de geregistreerde web-app met de machtiging voor toegang tot OMS, zoals beschreven in [Configuration Manager bieden met machtigingen voor OMS](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

> [!IMPORTANT]       
> Bij het configureren van machtigingen voor toegang tot OMS, moet u kiezen de **Inzender** rol, en deze machtigingen toewijzen aan de resourcegroep van de geregistreerde app.

Nadat de vereiste onderdelen zijn geconfigureerd, bent u klaar voor gebruik van de Wizard om de verbinding te maken.

### <a name="use-the-azure-services-wizard-to-configure-upgrade-readiness"></a>Gebruik de Wizard Azure-Services voor het configureren van de gereedheid voor Upgrade
1.  Ga in de console naar **beheer** > **overzicht** > **Cloudservices** > **Azure Services**, en kies vervolgens **Azure-Services configureren** van de **Start** tabblad van het lint, om te starten de **Wizard Azure-Services**.

2.  Op de **Azure Services** pagina de **Upgrade gereedheid van de Connector**, en klik vervolgens op **volgende**.

3.  Op de **App** pagina uw **Azure-omgeving** (de technical preview ondersteunt alleen de openbare Cloud). Klik vervolgens op **importeren** openen de **importeren Apps** venster.

4.  In de **importeren Apps** venster details opgeven voor een web-app die al in uw Azure AD bestaat.
    -   Geef een beschrijvende naam voor de naam van de Azure AD-Tenant. Geef vervolgens het Tenant-ID, de toepassingsnaam, de Client-ID, de geheime sleutel voor de Azure-web-app en de App ID URI.
    -   Klik op **controleren**, en als dit lukt, klikt u op **OK** om door te gaan.

5.   Op de **configuratie** pagina, geeft u het abonnement, resourcegroep en Windows Analytics werkruimte die u wilt gebruiken met deze verbinding met de gereedheid van de Upgrade.  

6.  Klik op **volgende** naar de **samenvatting** pagina en voltooi de wizard om de verbinding te maken.


## <a name="new-client-settings-for-cloud-services"></a>Nieuwe clientinstellingen voor cloud-services
<!-- 1319883 -->

In deze release toegevoegd twee nieuwe clientinstellingen voor Configuration Manager. U vindt deze in de **Cloudservices** sectie.  Deze instellingen bieden u de volgende mogelijkheden:

- Bepalen welke Configuration Manager-clients toegang een geconfigureerde cloud management gateway tot hebben.
- Windows 10 domein Configuration Manager-clients automatisch wordt geregistreerd bij Azure Active Directory.

Deze nieuwe instellingen waarmee u kunt uitvoeren van de mogelijkheden die zijn beschreven in de [1705 van Configuration Manager Technical Preview](/sccm/core/get-started/capabilities-in-technical-preview-1705#new-capabilities-for-azure-ad-and-cloud-management).

### <a name="before-you-start"></a>Voordat u begint

U moet hebt geïnstalleerd en Azure AD Connect geconfigureerd tussen uw lokale Active Directory en Azure AD-tenant.

Als u de verbinding verwijdert, apparaten zijn niet afgemeld, maar er zijn geen nieuwe apparaten worden geregistreerd.

### <a name="try-it-out"></a>Probeer het nu!

1. Configureer de volgende client-instellingen (te vinden in de Cloud-Services) sectie met de informatie in [het configureren van clientinstellingen](/sccm/core/clients/deploy/configure-client-settings).
    -   **Nieuwe Windows 10-apparaten die lid van domein automatisch wordt geregistreerd bij Azure Active Directory** – ingesteld op **Ja** (standaard), of **Nee**.
    -   **Clients kunnen gebruiken van een cloud management gateway** – ingesteld op **Ja** (standaard), of **Nee**.
2.  De clientinstellingen implementeren naar de vereiste verzameling van apparaten.

Voer de opdracht uit om te bevestigen dat het apparaat wordt gekoppeld aan Azure AD, **dsregcmd.exe/status** in een opdrachtpromptvenster. De **AzureAdjoined** veld in de resultaten weergegeven **Ja** als het apparaat Azure AD zijn toegevoegd is.

## <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Maken en PowerShell-scripts uitvoeren vanaf de Configuration Manager-console
<!-- 1236459 -->

In Configuration Manager kunt u scripts voor clientapparaten die pakketten en programma's implementeren. In deze technical preview toegevoegd nieuwe functionaliteit waarmee u de volgende acties uitvoeren:

- PowerShell-Scripts importeren naar Configuration Manager
- De scripts van de Configuration Manager-console (voor niet-ondertekende scripts alleen) bewerken
- Scripts markeren als goedgekeurd of geweigerd, de beveiliging te verbeteren
- Scripts uitvoeren op verzamelingen van Windows client-pc's en lokale beheerde Windows-pc's. U kunt scripts niet implementeren, in plaats daarvan ze in bijna realtime worden uitgevoerd op clientapparaten.
- Bekijk de resultaten geretourneerd door het script in de Configuration Manager-console.


### <a name="prerequisites"></a>Vereisten

Gebruik van scripts, moet u lid zijn van de juiste Configuration Manager-beveiligingsrol.

- **Om te importeren en scripts schrijven** -uw account moet hebben **maken** machtigingen voor **SMS Scripts** in de **volledige beheerder** beveiligingsrol.
- **Goedkeuren of weigeren van scripts** -uw account moet hebben **goedkeuren** machtigingen voor **SMS Scripts** in de **volledige beheerder** beveiligingsrol.
- **Scripts uitvoeren** -uw account moet hebben **-Script uitvoeren** machtigingen voor **verzamelingen** in de **instellingen voor naleving** beveiligingsrol.

Zie voor meer informatie over beveiligingsrollen voor Configuration Manager [basisprincipes van beheer op basis van rollen](/sccm/core/understand/fundamentals-of-role-based-administration).

Standaard goedkeuren gebruikers niet van een script dat ze hebben gemaakt. Aangezien scripts krachtige, veelzijdige zijn, en kunnen worden geïmplementeerd op veel apparaten, hebben wij een nieuw concept van het bieden van de mogelijkheid voor het scheiden van de rollen tussen de persoon die auteurs het script en de persoon die het script keurt deze goed is ingesteld. Hiermee geeft u aanvullende mate van beveiliging tegen het uitvoeren van een script zonder toezicht. U kunt deze secundaire goedkeuring, voor een eenvoudige test, met name tijdens de Technical Preview-versie uitschakelen.

Zodat gebruikers kunnen hun eigen scripts goedkeuren:

1. Klik op **Beheer**in de Configuration Manager-console.
2. Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Sites**.
3. Kies in de lijst met websites, uw site en klik op de **Start** tabblad, in de **Sites** groep, klikt u op **hiërarchie-instellingen**.
4. Op de **algemene** tabblad van de **eigenschappen van hiërarchie-instellingen** dialoogvenster vak, schakel het selectievakje uit **staan geen script auteurs goed te keuren van hun eigen scripts**.


### <a name="try-it-out"></a>Probeer het nu!

#### <a name="import-and-edit-a-script"></a>Importeren en bewerken van een script

1. Klik in de Configuration Manager-console op **Softwarebibliotheek**.
2. In de **softwarebibliotheek** werkruimte, klikt u op **Scripts**.
3. Op de **Start** tabblad, in de **maken** groep, klikt u op **Script maken**.
4. Op de **Script** pagina van de **Script maken** wizard configureert u het volgende:
    - **De naam van een script** -Voer een naam voor het script. Hoewel u meerdere scripts met dezelfde naam maken kunt, maakt dit het moeilijker voor u het script u moet vinden in de Configuration Manager-console.
    - **Scripttaal** : op dit moment alleen **PowerShell** scripts worden ondersteund.
    - **Importeren** -importeren van een PowerShell-script in de console. Het script wordt weergegeven in de **Script** veld.
    - **Schakel** -Hiermee verwijdert u het huidige script van de **Script** veld.
    - **Script** -wordt het momenteel geïmporteerde script. U kunt het script in dit veld indien nodig bewerken.
5. Voltooi de wizard. Het nieuwe script wordt weergegeven in de **Script** lijst met de status van **wachten op goedkeuring**. Voordat u dit script op clientapparaten uitvoert kunt, moet u deze goedkeuren.


#### <a name="approve-or-deny-a-script"></a>Goedkeuren of weigeren van een script



Voordat u een script uitvoeren kunt, moeten worden goedgekeurd. Goedkeuren van een script:

1. Klik in de Configuration Manager-console op **Softwarebibliotheek**.
2. In de **softwarebibliotheek** werkruimte, klikt u op **Scripts**.
3. In de **Script** kiest u het script dat u wilt goedkeuren of weigeren en klik op de **Start** tabblad, in de **Script** groep, klikt u op **goedkeuren/weigeren**.
4. In de **goedkeuren of weigeren van script** in het dialoogvenster **goedkeuren**, of **weigeren** het script en voer eventueel een opmerking over uw beslissing. Als u een script weigeren, kan deze kan niet worden uitgevoerd op clientapparaten.
5. Voltooi de wizard. In de **Script** wilt weergeven, ziet u de **goedkeuring staat** kolom wijzigen, afhankelijk van de actie die u hebt gemaakt.

#### <a name="run-a-script"></a>Een script uitvoeren

Zodra een script is goedgekeurd, kunt u deze kunt uitvoeren met een verzameling die u kiest.

1. Klik op **Activa en naleving**op de Configuration Manager-console.
2. Klik op **Apparaatverzamelingen** in de werkruimte **Activa en naleving**.
3. In de **Apparaatverzamelingen** lijst, klikt u op de verzameling van apparaten waarop u wilt dat het script uit te voeren.
3. Op de **Start** tabblad, in de **alle systemen** groep, klikt u op **-Script uitvoeren**.
4. Op de **Script** pagina van de **-Script uitvoeren** wizard kiest u een script in de lijst. Alleen goedgekeurde scripts die worden weergegeven. Klik op **volgende**, en voltooi de wizard.

#### <a name="monitor-a-script"></a>Monitor voor een script

Nadat u hebt een script uitgevoerd op clientapparaten, moet u deze procedure gebruiken voor het bewaken van het succes van de bewerking.

1. Klik in de Configuration Manager-console op **bewaking**.
2. In de **bewaking** werkruimte, klikt u op **Script resultaten**.
3. In de **Script resultaten** wanneer u de resultaten voor elk script dat u hebt uitgevoerd op clientapparaten lijst bekijken. De afsluitcode van een script van **0**, geeft meestal aan dat het script is uitgevoerd.

## <a name="pxe-network-boot-support-for-ipv6"></a>Ondersteuning voor PXE-netwerk opstarten voor IPv6
<!-- 1269793 -->
U kunt nu ondersteuning voor PXE netwerk opstarten voor IPv6 starten van het besturingssysteem van een takenreeksimplementatie inschakelen. Wanneer u deze instelling gebruikt, wordt distributiepunten met PXE-functionaliteit ondersteunen zowel IPv4 als IPv6. Deze optie vereist geen WDS en WDS wordt gestopt, indien aanwezig.

#### <a name="to-enable-pxe-boot-support-for-ipv6"></a>PXE opstartondersteuning voor IPv6 inschakelen
Gebruik de volgende procedure de optie voor IPv6-ondersteuning voor PXE inschakelen.

1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **distributiepunten**, en klik op **eigenschappen** voor distributiepunten met PXE-functionaliteit.
2. Op de **PXE** tabblad **ondersteuning voor IPv6-** IPv6-ondersteuning voor PXE inschakelen.

## <a name="manage-microsoft-surface-driver-updates"></a>Updates voor Microsoft Surface stuurprogramma's beheren
<!-- 1098490 -->
U kunt nu de Configuration Manager gebruiken voor het beheren van updates voor Microsoft Surface stuurprogramma's.

### <a name="prerequisites"></a>Vereisten
Alle software-updatepunten moeten Windows Server 2016 worden uitgevoerd.

### <a name="try-it-out"></a>Probeer het nu!
Voer de volgende taken en klikt u vervolgens Stuur ons **Feedback** van de **Start** tabblad van het lint te laten weten hoe het is gegaan:
1. Synchronisatie voor Microsoft Surface stuurprogramma's inschakelen. Gebruik de procedure in [classificaties en producten configureren](/sccm/sum/get-started/configure-classifications-and-products) en selecteer **opnemen Microsoft Surface stuurprogramma's en firmware-updates** op de **classificaties** tabblad Surface stuurprogramma's inschakelen.
2. [De Microsoft Surface stuurprogramma's synchroniseren](/sccm/sum/get-started/synchronize-software-updates.md).
3. [Gesynchroniseerde Microsoft Surface stuurprogramma's implementeren](/sccm/sum/deploy-use/deploy-software-updates)

## <a name="configure-windows-update-for-business-deferral-policies"></a>Windows Update voor bedrijven uitgestelde beleid configureren
<!-- 1290890 -->
U kunt nu uitgestelde beleidsregels voor Windows 10-functie-Updates of Quality-Updates voor Windows 10-apparaten rechtstreeks beheerd door Windows Update voor bedrijven configureren. U kunt de uitgestelde beleidsregels beheren in de nieuwe **Windows Update voor bedrijven-beleid** knooppunt onder **softwarebibliotheek** > **onderhoud van Windows 10**.

### <a name="prerequisites"></a>Vereisten
Windows 10-apparaten worden beheerd door Windows Update voor bedrijven moeten verbinding met Internet hebben.

#### <a name="to-create-a-windows-update-for-business-deferral-policy"></a>Een Windows Update voor bedrijven uitgestelde-beleid maken
1. In **softwarebibliotheek** > **onderhoud van Windows 10** > **Windows Update voor bedrijven-beleid**
2. Op de **Start** tabblad, in de **maken** Selecteer **Windows Update voor bedrijven-beleid maken** openen van de Update voor Windows maken voor Wizard beleid voor bedrijven.
3. Op de **algemene** pagina, Geef een naam en beschrijving voor het beleid.
4. Op de **uitgestelde beleid** pagina, configureren of uit te stellen of onderbreken van de functie-Updates.    
    Functie-Updates zijn in het algemeen nieuwe functies voor Windows. Na het configureren van de **niveau van de gereedheid van de vertakking** instellen, kunt u opgeven of en hoe lang u wilt stellen functie-Updates na de beschikbaarheid van Microsoft ontvangen.
    - **Niveau van de gereedheid van de vertakking**: Stel de vertakking waarvoor u het apparaat ontvangt updates voor Windows (huidige vertakking of Current Branch for Business).
    - **Uitgestelde periode (dagen)**:  Geef het aantal dagen waarvoor de functie-Updates worden uitgesteld. Deze functie-Updates ontvangen voor een periode van 180 dagen na de release kan uit te stellen.
    - **Onderbreken functies Updates vanaf**: Selecteer of onderbreken apparaten functie-Updates ontvangen voor een periode van 60 dagen vanaf het moment dat u de updates wilt onderbreken. Nadat het maximum aantal dagen zijn verstreken, onderbreken functionaliteit verloopt automatisch en het apparaat Windows-Updates voor de betreffende updates scant. U kunt de updates opnieuw onderbreken na deze scan. U kunt de functie-Updates weer hervatten door het selectievakje uit te schakelen.   
5. Kies of u wilt stellen of onderbreken Quality-Updates.     
    Quality-Updates zijn meestal oplossingen en verbeteringen in bestaande Windows-functionaliteit en normaal gesproken de eerste dinsdag van elke maand worden gepubliceerd, maar kunnen worden vrijgegeven op elk gewenst moment door Microsoft. U kunt definiëren als en hoe lang u wilt stellen Quality-Updates beschikbaar zijn na ontvangen.
    - **Uitgestelde periode (dagen)**: Geef het aantal dagen waarvoor de functie-Updates worden uitgesteld. Deze functie-Updates ontvangen voor een periode van 180 dagen na de release kan uit te stellen.
    - **Onderbreken Quality-Updates vanaf**: Selecteer of onderbreken van apparaten uit ontvangt Quality-Updates voor een periode van maximaal 35 dagen vanaf het moment dat u de updates wilt onderbreken. Nadat het maximum aantal dagen zijn verstreken, onderbreken functionaliteit verloopt automatisch en het apparaat Windows-Updates voor de betreffende updates scant. U kunt de updates opnieuw onderbreken na deze scan. U kunt Updates kwaliteit hervatten door het selectievakje uit te schakelen.
6. Selecteer **installeren van updates van andere Microsoft-Products** waarmee de instelling voor Groepsbeleid die uitgestelde instellingen van toepassing op Microsoft Update, evenals de Windows-Updates.
7. Selecteer **bevat de stuurprogramma's met Windows Update** automatisch bijwerken van stuurprogramma's van Windows-Updates. Als u deze instelling uitschakelt, worden updates voor stuurprogramma's niet uit de Windows-Updates gedownload.
8. Voltooi de wizard om de nieuwe uitgestelde-beleid te maken.

#### <a name="to-deploy-a-windows-update-for-business-deferral-policy"></a>Een Windows Update voor bedrijven uitgestelde beleid implementeren
1. In **softwarebibliotheek** > **onderhoud van Windows 10** > **Windows Update voor bedrijven-beleid**
2. Op de **Start** tabblad, in de **implementatie** Selecteer **Windows Update voor bedrijven-beleid implementeren**.
3. Configureer de volgende instellingen:
    - **Configuratiebeleid implementeren**: Selecteer de Windows Update voor bedrijven-beleid dat u wilt implementeren.
    - **Verzameling**: Klik op **Bladeren** om de verzameling waar u het beleid implementeren selecteren.
    - **Herstellen, waar ondersteund**: Selecteer alle regels die niet compatibel voor Windows Management Instrumentation (WMI), het register, scripts en alle instellingen voor mobiele apparaten die zijn ingeschreven door Configuration Manager zijn automatisch oplossen.
    - **Herstel toestaan buiten het onderhoudsvenster**: Als een onderhoudsvenster is geconfigureerd voor de verzameling waarnaar u het beleid implementeert, moet u deze optie zodat de instellingen voor naleving herstellen van de waarde buiten het onderhoudsvenster inschakelen. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](/sccm/core/clients/manage/collections/use-maintenance-windows).
    - **Waarschuwing genereren**: Hiermee configureert u een waarschuwing die wordt gegenereerd als de naleving van de configuratiebasislijn kleiner dan een opgegeven percentage voor een opgegeven datum en tijd is. U kunt tevens opgeven of u een melding naar System Center Operations Manager wilt verzenden.
    - **Willekeurige vertraging (uren)**: Hiermee geeft u een vertragingsvenster op om te voorkomen overmatige Network Device Enrollment Service. De standaardwaarde is 64 uur.
    - **Planning**: Geef het evaluatieschema voor compatibiliteit op waarmee het geïmplementeerde profiel wordt beoordeeld op clientcomputers. U kunt een eenvoudig of aangepast schema opgeven. Het profiel wordt door de clientcomputers beoordeeld wanneer de gebruiker zich aanmeldt.
4.  Voltooi de wizard voor het implementeren van het profiel.



## <a name="support-for-entrust-certification-authorities"></a>Ondersteuning voor Entrust certificeringsinstanties
<!-- 1350740 -->
Configuration Manager ondersteunt nu Entrust certificeringsinstanties; Hierdoor kunnen de levering van PFX-certificaat voor apparaten die zijn ingeschreven bij Microsoft Intune.

U kunt Entrust configureren als de certificeringsinstantie (CA) bij het toevoegen van een rol Certificaatregistratiepunt in Configuration Manager. Wanneer u een nieuw certificaatprofiel die PFX-certificaten uitgeeft toevoegt, kunt u een Microsoft- of Entrust certificeringsinstantie selecteren.

**Bekende probleem**: In de technical preview 1706 zijn PFX-certificaten niet uitgegeven voor Microsoft-certificeringsinstanties. Dit geldt niet voor geïmporteerde PFX-certificaten of SCEP-profielen.


## <a name="cisco-ipsec-support-for-macos-vpn-profiles"></a>Cisco (IPsec) ondersteuning voor Mac OS VPN-profielen
<!-- 1321367 -->

U kunt een Mac OS VPN-profiel maken met Cisco (IPsec) als het verbindingstype. Zie voor meer informatie [VPN-profielen maken](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles).


## <a name="new-windows-configuration-item-settings"></a>Nieuwe configuratie-item-instellingen van Windows
<!-- 1354715 -->

In deze release toegevoegd de volgende nieuwe instellingen die kunt u in de Windows-configuratie-items:

### <a name="password"></a>Wachtwoord

- **Apparaatversleuteling**

### <a name="device"></a>Apparaat

- **Wijziging regio (alleen desktop)**
- **Wijziging van kracht en slaapstand-instellingen**
- **Taal instellingen aanpassen**
- **Aanpassing van het systeem tijd**
- **Naam wijzigt van apparaat**

### <a name="store"></a>Opslaan

- **Automatische updates store-apps**
- **Gebruik alleen persoonlijke archief**
- **Starten van de oorsprong app Store**

### <a name="microsoft-edge"></a>Microsoft Edge

- **Toegang tot informatie over blokkeren: vlaggen**
- **Het SmartScreen-prompt overschrijven**
- **Het SmartScreen-prompt overschrijven voor bestanden**
- **WebRTC localhost-IP-adres**
- **Standaardzoekmachine**
- **OpenSearch XML-URL**
- **Startpagina's (alleen desktop)**

Zie voor meer informatie over instellingen voor naleving [apparaatcompatibiliteit garanderen](/sccm/compliance/understand/ensure-device-compliance).


## <a name="new-device-compliance-policy-rules"></a>Nieuwe beleidsregels voor naleving van apparaat

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

Zie [maken en implementeren van een nalevingsbeleid voor apparaten](https://docs.microsoft.com/sccm/mdm/deploy-use/create-compliance-policy) om te proberen het nieuwe apparaat naleving van regels.

## <a name="new-mobile-application-management-policy-settings"></a>Nieuwe beleidsinstellingen voor mobile application management
Vanaf deze versie, kunt u drie nieuwe beleidsinstellingen voor mobile application management (MAM):

- **Schermafbeelding (alleen Android-apparaten) blokkeren:** Hiermee wordt opgegeven dat de schermafbeeldingsmogelijkheden van het apparaat zijn geblokkeerd bij gebruik van deze app.

- **Synchronisatie van contactpersonen uitschakelen:** Hiermee voorkomt dat de app opslaan van gegevens in de systeemeigen contactpersonen-app op het apparaat.

- **Afdrukken uitschakelen:** Voorkomt dat de app vanuit afdrukken werk- of schoolgegevens.

Zie [apps beveiligen met beleid voor app-beveiliging in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/protect-apps-using-mam-policies) om te proberen de nieuwe beleidsinstellingen van de app-beveiliging.

## <a name="android-and-ios-enrollment-restrictions"></a>Beperkingen voor android en iOS-inschrijving
<!-- 1290826 -->
Vanaf deze release, kunnen beheerders nu opgeven dat gebruikers persoonlijke Android- of iOS-apparaten in hun omgeving hybride kunnen niet registreren. Hiermee kunt u limiet ingeschreven apparaten predeclared, bedrijfseigen apparaten of alleen met Device Enrollment Program ingeschreven iOS-apparaten.

### <a name="try-it-out"></a>Try it out in
1. Ga in de Configuration Management-console in de werkruimte **Beheer** naar **Cloudservices** > **Microsoft Intune-abonnement**.
2. Op de **Start** tabblad de **abonnement** groep, kiest u **Platforms configureren** en selecteer vervolgens **Android** of **iOS**.
3. Selecteer **blok persoonlijk eigendom zijn van apparaten**.

## <a name="android-for-work-application-management-policy-for-copy-paste"></a>Android for Work application management-beleid voor kopiëren en plakken
We hebben bijgewerkt de beschrijvingen van de instelling voor Android voor werk configuratie-items voor de **toestaan gegevens delen tussen werk en persoonlijk profiel**.

|Voordat u 1706 Technical Preview | Naam van de nieuwe optie | Gedrag|
|-|-|-|
|Alle delen buiten de grenzen van voorkomen| Standaard-mediumgebruik| Werk voor persoonlijk: Standaard (verwachte geblokkeerd op alle versies) <br>Personal te werk: Standaard (toegestaan op 6.x+, geblokkeerd op 5.x)|
|Er zijn geen beperkingen|   Apps in persoonlijk profiel kunnen voor het delen van aanvragen van work-profiel verwerken| Werk voor persoonlijk: Toegestaan  <br>Personal te werk: Toegestaan|
|Apps in work-profiel kunnen verwerken met het delen van aanvragen van persoonlijk profiel |Apps in work-profiel kunnen verwerken met het delen van aanvragen van persoonlijk profiel |Werk voor persoonlijk: Standaard<br>Personal te werk: Toegestaan<br>(Dit is alleen nuttig op 5.x waar persoonlijke om te werken is geblokkeerd)|

Geen van deze opties niet rechtstreeks kopiëren en plakken gedrag. We hebben een aangepaste instelling toegevoegd aan de service en de bedrijfsportal-app in 1704 die kunnen worden geconfigureerd om te kopiëren en plakken voorkomen. Dit kan worden ingesteld via aangepaste URI.

-   OMA-URI: ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste
-   Waardetype: Boolean-waarde

DisallowCrossProfileCopyPaste instellen op waar wordt voorkomen dat gedrag kopiëren en plakken tussen Android for Work persoonlijke en zakelijke profielen.

### <a name="try-it-out"></a>Try it out in
1. Selecteer in de Configuration Manager-console **activa en naleving** > **overzicht** > **instellingen voor naleving** > **configuratie-items**.
2. Kies **maken** voor het maken van een nieuwe configuratie-item en geef **naam** en **Android for Work**.
3. Selecteer in het apparaat voor het configureren van de instellingsgroepen **Work-profiel**, en kies **volgende**.
4. Selecteer de waarde voor **gegevens delen tussen werk en persoonlijke profielen toestaan**, en voltooi de wizard.

## <a name="device-health-attestation-assessment-for-compliance-policies-for-conditional-access"></a>Apparaat Health Attestation beoordeling van van nalevingsbeleid voor voorwaardelijke toegang
<!-- 1097546 -->
Vanaf deze release u kunt gebruiken Health Attestation van apparaten status als een regel voor naleving beleid voor voorwaardelijke toegang tot bedrijfsbronnen.

### <a name="try-it-out"></a>Try it out in
Selecteer een regel Health Attestation van apparaten als onderdeel van een beoordeling van compatibiliteit beleid.
