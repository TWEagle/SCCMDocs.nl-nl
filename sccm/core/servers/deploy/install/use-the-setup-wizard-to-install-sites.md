---
title: Wizard Setup
titleSuffix: Configuration Manager
ms.custom: na
ms.date: 7/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f703376-5f2c-4fd2-8209-7028c931ddc7
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 88aaed5b4b0fb126bb4042aabfb1acaebbaa86ca
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="use-the-setup-wizard-to-install-system-center-configuration-manager-sites"></a>Gebruik de installatiewizard voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Een nieuwe System Center Configuration Manager-site installeren met behulp van een begeleide interface, moet u de Setup Wizard van Configuration Manager (setup.exe) gebruiken. De wizard ondersteunt de installatie van een primaire site of centrale beheersite. U ook de wizard te gebruiken [een evaluatie-installatie bijwerken](../../../../core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install.md) van Configuration Manager naar een volledig gelicentieerde installatie. Wanneer u niet wilt dat de wizard te gebruiken, kunt u in plaats daarvan gebruiken een [installatiescript](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md) en een opdrachtregelprogramma installatie zonder toezicht uitvoeren.

Een secundaire site te installeren, moet u de site vanuit de Configuration Manager-console installeren. Secundaire sites ondersteunen geen een scriptinstallatie van de opdrachtregel.

## <a name="bkmk_primary"></a>Een centrale beheersite of primaire site installeren
Gebruik de volgende procedure om een centrale beheersite of een primaire site te installeren of upgraden van een evaluatiesite naar een volledig gelicentieerde Configuration Manager-site.   

Voordat u begint de installatie van de site, bekend zijn met de details in de volgende artikelen:
 -  [De installatie van sites voorbereiden](../../../../core/servers/deploy/install/prepare-to-install-sites.md)
 -  [Vereisten voor het installeren van sites](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md)

Als u een centrale beheersite als onderdeel van het scenario voor site-uitbreiding installeert, raadpleegt u de [uitbreiden een zelfstandige primaire site](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) sectie van dit onderwerp voordat u de volgende procedure.

### <a name="bkmk_installpri"></a>Een primaire of centrale beheersite installeren

1.  Voer op de computer waar u de site installeert,  **&lt;InstallationMedia\>\SMSSETUP\BIN\X64\Setup.exe** starten de **installatiewizard voor System Center Configuration Manager**.  

    > [!NOTE]  
    > Wanneer u een centrale beheersite om uit te breiden op een zelfstandige primaire site installeren of een nieuwe onderliggende primaire site in een bestaande hiërarchie installeren, moet u installatiemedia (bronbestanden) die overeenkomt met de versie van de bestaande site of websites. Als u in de console-updates die zijn gewijzigd van de versie van de eerder geïnstalleerde sites hebt geïnstalleerd, hoeft u de installatie-cd. Gebruik in plaats van de bronbestanden van de [CD. Meest recente map](../../../../core/servers/manage/the-cd.latest-folder.md) van een bijgewerkte site. Configuration Manager moet u bronbestanden gebruiken die overeenkomen met de versie van de bestaande site die de nieuwe site verbinding maken.  

2.  Op de **voordat u begint** pagina **volgende**.  

3.  Op de **aan de slag** pagina, selecteert u het type site dat u wilt installeren:  

    -   **Centrale beheersite**, als de eerste site van een nieuwe hiërarchie, of wanneer een zelfstandige primaire site uitbreiden:  

        Selecteer **een centrale beheersite van Configuration Manager installeren**.  

         Tijdens een latere stap van deze procedure krijgt u de keuze voor het installeren van een centrale beheersite als de eerste site van een nieuwe hiërarchie, of voor het installeren van een centrale beheersite op een zelfstandige primaire site uitbreiden.  

    -    **Primaire site**, als een zelfstandige primaire site die de eerste site van een nieuwe hiërarchie, of als een onderliggende primaire:  

        Selecteer **een primaire site van Configuration Manager installeert**.  

        > [!TIP]  
        > Normaal gesproken alleen selecteert u de optie **gangbare installatieopties gebruiken voor een zelfstandige primaire site** als u wilt een zelfstandige primaire site installeren in een testomgeving. Wanneer u deze optie selecteert, Setup:  

        > -   Configureert de site automatisch als een zelfstandige primaire site.  
        > -   Maakt gebruik van een standaardinstallatiepad.  
        > -   Maakt gebruik van een lokale installatie van het standaardexemplaar van SQL Server voor de sitedatabase.  
        > -   Een beheerpunt en een distributiepunt installeert op de siteservercomputer.  
        > -   Configureert de site met Engels en de weergavetaal van het besturingssysteem op de primaire siteserver, als deze overeenkomt met een van de talen die ondersteuning biedt voor Configuration Manager.  

4.  Op de **productcode** pagina:
    - Kies of u het installeren van Configuration Manager als een evaluatie-editie of een gelicentieerde versie.  

      -   Als u een gelicentieerde versie selecteert, Voer uw productcode in en kies **volgende**.  

      -   Als u een evaluatieversie selecteert, kiest u **volgende**. (U kunt een evaluatie-installatie upgraden naar een volledige installatie later.)  
    - U begint met de oktober 2016-release van versie 1606 basislijnmedia voor System Center Configuration Manager, kunt u de vervaldatum van uw Software Assurance overeenkomst opgeven. Op deze pagina die u hebt de mogelijkheid te geven de **Software Assurance vervaldatum** van uw gebruiksrechtovereenkomst handige eraan te herinneren dat u na die datum. Als u geen dit tijdens de installatie opgeeft, kunt u later uit binnen de Configuration Manager-console opgeven.

      > [!NOTE]   
      > Microsoft biedt geen valideren de vervaldatum die u hebt ingevoerd en deze datum niet gebruiken voor het valideren van licenties. In plaats daarvan kunt u deze als een herinnering van de vervaldatum. Dit is nuttig omdat Configuration Manager controleert regelmatig of er nieuwe software-updates die worden aangeboden online, en de status van uw software assurance-licentie moet huidige zodat u in aanmerking voor deze aanvullende updates.    

      Zie voor meer informatie [licenties en vertakkingen voor System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

5.  Op de **licentievoorwaarden voor Microsoft-Software** lees en accepteer de licentievoorwaarden.  

6.  Op de **vereiste licenties** lees en accepteer de licentievoorwaarden voor de vereiste software. Setup downloadt en installeert de software automatisch op sitesystemen of clients wanneer dit is verplicht. U moet alle selectievakjes controleren voordat u kunt doorgaan naar de volgende pagina.  

7.  Op de **vereiste Downloads** pagina, Geef op of Setup de recentste vereiste herdistribueerbare bestanden vanaf Internet downloaden moet of eerder bestanden gebruiken gedownloade:  

    -   Als u wilt dat Setup de bestanden op dit moment downloadt, selecteert u **vereiste bestanden downloaden** en geef een locatie voor het opslaan van de bestanden in.  

    -   Als u eerder de bestanden gedownload met behulp van [Setup Downloader](../../../../core/servers/deploy/install/setup-downloader.md), selecteer **eerder gedownloade bestanden gebruiken** en geeft u de downloadmap.  

        > [!TIP]  
        > Als u eerder gedownloade bestanden gebruikt, moet u controleren of het pad naar de downloadmap de recentste versie van de bestanden bevat.  

8.  Op de **selectie van servertaal** pagina, selecteert u de talen die beschikbaar voor de Configuration Manager-console en voor rapporten zijn. (Engels is standaard ingeschakeld en kan niet worden verwijderd.)  

9. Op de **Clienttaal** pagina, selecteert u de talen die beschikbaar zijn voor clientcomputers en geef op of alle clienttalen inschakelen voor clients van mobiele apparaten. (Engels is standaard ingeschakeld en kan niet worden verwijderd.)  

    > [!IMPORTANT]  
    > Wanneer u een centrale beheersite gebruikt, zorgen ervoor dat u op de centrale beheersite configureert clienttalen alle clienttalen die u op elke onderliggende primaire site configureert. Dit is omdat clients worden geïnstalleerd vanaf een distributiepunt die toegang tot de clienttalen van de bovenste site, hebben terwijl de clients die worden geïnstalleerd vanuit een beheerpunt toegang hebben tot de clienttalen van hun toegewezen primaire site.  

10. Op de **Site en installatie-instellingen** pagina, geeft u het volgende voor de nieuwe site die u installeert:  

    -   **Sitecode:** [Elke sitecode in een hiërarchie moet uniek zijn](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_sitecodes) en bestaan uit drie alfanumerieke tekens (A-Z) en 0-9. Aangezien de sitecode in mapnamen wordt gebruikt, gebruik geen Windows-gereserveerde namen voor de site, met inbegrip van:    
        -   AUX  
        -   CON    
        -   NUL    
        -   PRN    
        -   SMS  

        > [!NOTE]  
        > Setup controleren niet of de sitecode die u opgeeft, wordt al gebruikt of dat er een gereserveerde naam.  

    -   **Naam van site:** Elke site vereist deze beschrijvende naam, waarmee u de site te identificeren.  

    -   **Installatiemap:** Dit is het pad naar de Configuration Manager-installatie. U kunt de locatie niet wijzigen nadat de site is geïnstalleerd. Het pad kan ook Unicode-tekens of afsluitende spaties bevatten.  

11. Op de **Site-installatie** pagina, gebruikt u de volgende optie die overeenkomt met het scenario:  

    -   **Ik installeer een centrale beheersite:**  

         Op de **installatie van centrale beheersite** pagina **installeren als de eerste site in een nieuwe hiërarchie**, en kies vervolgens **volgende** om door te gaan.  

    -   **Ik Breid een zelfstandige primaire naar een hiërarchie met een centrale beheersite:**  

         Op de **installatie van centrale beheersite** pagina **een bestaande zelfstandige primaire uitbreiden naar een hiërarchie**, geef de FQDN van de zelfstandige primaire siteserver en kies vervolgens **volgende** om door te gaan.  

         De media die u gebruikt voor het installeren van de nieuwe centrale beheersite moet overeenkomen met de versie van de primaire site.  

    -   **Ik installeer een zelfstandige primaire site:**  

         Op de **primaire Site-installatie** pagina **de primaire site installeren als een zelfstandige site**, en kies vervolgens **volgende**.  

    -   **Ik installeer een onderliggende primaire site:**  

         Op de **primaire Site-installatie** pagina **de primaire site lid aan een bestaande hiërarchie**, specificeer de FQDN voor de centrale beheersite en kies vervolgens **volgende**.  

12. Op de **databasegegevens** pagina, geeft u de volgende informatie:  

    -   **SQL Server-naam (FQDN):** Standaard is dit ingesteld om te worden van de siteservercomputer.

     Als u een aangepaste poort gebruikt, moet u die poort toevoegen aan de FQDN-naam van de SQL Server. Volg hiertoe de FQDN van de SQL-server met een komma en vervolgens het poortnummer.   Bijvoorbeeld: voor server *SQLServer1.fabrikam.com*, gebruikt u de volgende poort *1551*:  **SQLServer1.fabrikam.com, 1551**

    -   **Instantienaam:** Dit is standaard leeg. Het standaardexemplaar van SQL wordt gebruikt op de siteservercomputer.  

    -   **Databasenaam:** Standaard is dit ingesteld op CM_&lt;Sitecode\>. U bent een andere naam die u opgeeft kunt gebruiken.  

    -   **Service Broker-poort:** Standaard is dit ingesteld voor gebruik van de standaard SQL Server Service Broker (SSB)-poort 4022. SQL gebruikt om te communiceren rechtstreeks met de sitedatabase op andere sites.  

13. Op de tweede **databasegegevens** pagina kunt u niet-standaard locaties voor de SQL Server-gegevensbestand en het logboekbestand van SQL Server voor de sitedatabase:  

    -   Standaardbestandslocaties voor SQL Server zijn opgegeven.  

    -   De optie voor het opgeven van niet-standaard bestandslocaties is niet beschikbaar in een SQL Server-cluster.  

    -   De prerequisite checker niet uitgevoerd een controle voor de vrije schijfruimte voor niet-standaard bestandslocaties.  

14. Op de **SMS-Providerinstellingen** pagina, geef de FQDN voor de server waarop u wilt installeren van de SMS-Provider.  

    -   Standaard zijn de siteserver is opgegeven.  

    -   Nadat de site is geïnstalleerd, kunt u aanvullende SMS-Providers configureren.  

15. Op de **communicatie-instellingen voor Client** pagina, kiest u of alle sitesystemen zo accepteren alleen HTTPS-communicatie van clients of de communicatiemethode voor elke sitesysteemrol moet worden geconfigureerd.  

    Wanneer u selecteert **alle sitesysteemrollen accepteren alleen HTTPS-communicatie van clients**, de clientcomputer moet een geldig PKI-certificaat voor clientverificatie hebben. Zie voor meer informatie over PKI-certificaatvereisten [PKI-certificaatvereisten voor Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    > [!NOTE]  
    > Deze stap is alleen van toepassing wanneer u een primaire site installeert. Als u een centrale beheersite installeert, moet u deze stap overslaan.  

16. Op de **sitesysteemrollen** pagina, kies of u een beheerpunt of distributiepunt te installeren. Voor elke rol die u wilt de installatie hebt geïnstalleerd:  

    -   Moet u de **FQDN** voor de computer die als host voor de rol en kiest u de client verbindingsmethode dat de server worden ondersteund (HTTP of HTTPS).  

    -   Als u hebt geselecteerd **alle sitesysteemrollen accepteren alleen HTTPS-communicatie van clients** op de vorige pagina de clientverbindingsinstellingen automatisch geconfigureerd voor HTTPS en kan niet worden gewijzigd, tenzij u teruggaat en de instelling wijzigt.  

    > [!NOTE]  
    > Deze stap is alleen van toepassing wanneer u een primaire site installeert. Als u een centrale beheersite installeert, moet u deze stap overslaan.  

    > [!NOTE]  
    > Voor het installeren van sitesysteemrollen, gebruikt het installatieprogramma de **installatieaccount site**. Dit gebruikt standaard het computeraccount van de primaire site. Deze account moet een lokale beheerder op een externe computer voor het installeren van de sitesysteemrol. Als dit account beschikt niet over de vereiste machtigingen, schakelt u de sitesysteemrollen en deze later uit na het configureren van extra accounts te gebruiken als site-installatie systeemaccounts binnen de Configuration Manager-console installeren.  

17. Op de **gebruiksgegevens** pagina, lees de informatie over gegevens die Microsoft verzamelt en kies vervolgens **volgende**.  

18. De **serviceverbindingspunt instellen** pagina is alleen beschikbaar tijdens de installatie:  

    -   Wanneer u een zelfstandige primaire site installeert.  

    -   Wanneer u een centrale beheersite installeert.  

    > [!NOTE]  
    > Als u een onderliggende primaire site installeert, moet u deze stap (deze pagina is niet beschikbaar) overslaan.  

     Als u een centrale beheersite als onderdeel van het scenario voor site-uitbreiding installeert en deze rol is al geïnstalleerd op de zelfstandige primaire site, moet u deze rol in de zelfstandige primaire site verwijderen. Slechts één exemplaar van deze rol is toegestaan in een hiërarchie, en het alleen toegestaan op de bovenste site van de hiërarchie.  

     Nadat u een configuratie voor de **Service Connection Point**, kies **volgende**. (Nadat Setup is voltooid, kunt u deze configuratie uit binnen de Configuration Manager-console.)  

19. Op de **samenvatting van instellingen** controleert u de instelling die u hebt geselecteerd. Als u klaar bent, kiest u **volgende** de Prerequisite Checker te starten.  

20. Op de **installatiecontrole** problemen die kunnen worden geïdentificeerd aan de pagina worden weergegeven.  

    -   Als de Prerequisite Checker een probleem aantreft, kiest u een item in de lijst voor meer informatie over het oplossen van het probleem.  

    -   U moet elk item met de status oplossen **mislukt** voordat u doorgaat naar de site installeert. Items met de status van **waarschuwing** moeten worden opgelost, maar ze de installatie van de site niet blokkeren.  

    -   Na het oplossen van problemen, kies **controle uitvoeren** opnieuw uit te voeren van de Prerequisite Checker.  

     Wanneer de Prerequisite Checker wordt uitgevoerd en er geen controles ontvangen een **mislukt** status, kunt u kiezen **installatie starten** de site-installatie te starten.  

    > [!TIP]  
    > Naast de feedback die is opgegeven in de wizard, u vindt meer informatie over vereiste problemen wanneer u de **ConfigMgrPrereq.log** bestand in de hoofdmap van het systeemstation van de computer die u installeert op. Zie voor een lijst van de installatie vereiste regels en beschrijvingen [lijst met Vereistencontroles voor System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

21. Op de **installatie** pagina geeft de installatiestatus weer. Wanneer de installatie van de belangrijkste siteserver voltooid is, hebt u de optie voor het **sluiten** de installatiewizard. Wanneer u de wizard sluit, worden de installatie en eerste siteconfiguraties op de achtergrond voortgezet.  

    -   U kunt een Configuration Manager-console verbinden met de site voordat de installatie is voltooid. Deze console verbinding maakt als alleen-lezen en kunt u objecten en instellingen weergeven, maar u kunt geen bewerkingen worden uitgevoerd.  

    -   Nadat Setup is voltooid, kunt u zult kunnen verbinding maken met een console waarmee objecten en instellingen kunt bewerken.  


## <a name="bkmk_expand"></a>Een zelfstandige primaire site uitbreiden
Wanneer u een zelfstandige primaire site hebt geïnstalleerd als uw eerste site, hebt u de optie later naar die site uitbreiden naar een grotere hiërarchie door een centrale beheersite te installeren.   

Wanneer u een zelfstandige primaire site uitbreidt, kunt u een nieuwe centrale beheersite die gebruikmaakt van de bestaande zelfstandige primaire site-database als een verwijzing installeren. Nadat de nieuwe centrale beheersite is geïnstalleerd, fungeert de zelfstandige primaire site als een onderliggende primaire site.

-   Alleen een zelfstandige primaire site kan worden uitgebreid naar een nieuwe hiërarchie.  

-   Slechts één zelfstandige primaire site kan worden uitgebreid naar een specifieke hiërarchie. U kunt deze optie niet gebruiken om toe te voegen aanvullende zelfstandige primaire sites in dezelfde hiërarchie. Gebruik in plaats daarvan migratie om gegevens te migreren van een hiërarchie in een ander.  

-   Nadat u een zelfstandige site naar een hiërarchie met een centrale beheersite uitbreiden, kunt u extra onderliggende primaire sites toevoegen.  

-   Als een primaire site uit een hiërarchie met een centrale beheersite verwijderen, moet u de primaire site verwijderen.  

Als de site wilt uitbreiden, moet u de Setup Wizard van System Center Configuration Manager gebruiken voor het installeren van een nieuwe centrale beheersite met het volgende voorbehoud:  

-   U moet de centrale beheersite installeren met behulp van dezelfde versie van Configuration Manager als de zelfstandige primaire site.  

-   Op de **aan de slag** pagina van de Wizard Setup u de optie voor het installeren van een centrale beheersite. In een later stadium van de installatie kiest u een optie voor het uitbreiden van een bestaande zelfstandige primaire site.  

-   Wanneer u configureert de **Clienttaal** pagina voor de nieuwe centrale beheersite, moet u dezelfde clienttalen die zijn geconfigureerd voor de zelfstandige primaire site die u wilt uitbreiden.  

-   Op de **Site-installatie** pagina selecteert u de optie voor het uitbreiden van de zelfstandige primaire site.  

Als u een zelfstandige primaire site uitbreiden, ziet u eerst de [vereisten voor het uitbreiden van een site](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand), en gebruik vervolgens de procedure  *[voor het installeren van een primaire of centrale beheersite](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_installpri)*eerder in dit artikel.


## <a name="bkmk_secondary"></a>Een secundaire site installeren
 De Configuration Manager-console kunt u een secundaire site installeert.  

-   Als de console die u gebruikt, is niet met de primaire site die de bovenliggende site naar de nieuwe secundaire site verbonden, wordt de opdracht voor het installeren van de site worden gerepliceerd naar de juiste primaire site.  

-   Controleer voordat u begint de installatie van de site, of uw gebruikersaccount de vereiste machtigingen heeft en dat de computer die als host voor de nieuwe secundaire site fungeert voldoet aan alle vereisten voor gebruik als een secundaire siteserver.  

-   Wanneer u de secundaire site installeert, configureert Configuration Manager de nieuwe site voor het gebruik van de clientcommunicatiepoorten die op de bovenliggende primaire site zijn geconfigureerd.  

### <a name="bkmk_installsecondary"></a>Een secundaire site te installeren  


1.  Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**. Selecteer de site die de bovenliggende primaire site van de nieuwe secundaire site.  

2.  Kies **secundaire Site maken** starten de **Wizard secundaire Site maken**.  

3.  Op de **voordat u begint** pagina, Controleer of de primaire site die wordt vermeld de site die u wilt worden van het bovenliggende lid van de nieuwe secundaire site. Kies vervolgens **volgende**.  

4.  Op de **algemene** pagina, geeft u het volgende:  

    -   **Sitecode**: Elke sitecode in een hiërarchie moet uniek zijn en daarvan uit uit drie alfanumerieke tekens (A-Z) en 0-9. Aangezien de sitecode in mapnamen wordt gebruikt, gebruik geen Windows-gereserveerde namen voor de site, met inbegrip van:  

        -   AUX    
        -   CON    
        -   NUL    
        -   PRN  
        -   SMS  

       > [!NOTE]  
       > Setup controleren niet of de sitecode die u opgeeft wordt al gebruikt, of als dit een gereserveerde naam.  

    -   **Naam van de siteserver**: Dit is de FQDN-naam van de server waarop de nieuwe secundaire site wilt installeren.  

    -   **Sitenaam**: Elke site vereist deze beschrijvende naam, waarmee u de site te identificeren.  

    -   **Installatiemap**: Dit is het pad naar de Configuration Manager-installatie. U kunt de locatie niet wijzigen nadat de site is geïnstalleerd. Het pad bevatten geen Unicode-tekens of afsluitende spaties.  

    > [!IMPORTANT]  
    > Als u meer informatie op deze pagina opgeeft, kunt u **samenvatting** de standaardinstellingen gebruiken voor het restant van de secundaire site-opties en gaat u rechtstreeks naar de **samenvatting** pagina van de wizard.  

    > -   Gebruik deze optie alleen als u bekend met de standaardinstellingen in deze wizard bent, en de instellingen die u wilt gebruiken.  
    > -   Grensgroepen zijn niet gekoppeld aan het distributiepunt wanneer u de standaardinstellingen gebruikt. Totdat u grensgroepen waarin de secundaire siteserver zijn configureert, niet clients daarom het distributiepunt dat is geïnstalleerd op deze secundaire site als een bronlocatie voor inhoud gebruikt.  

5.  Op de **installatiebronbestanden** pagina, kiest u hoe de secundaire sitecomputer de bronbestanden voor installatie van de site verkrijgt.  

     Wanneer u bronbestanden gebruiken die zijn opgeslagen op het netwerk of opgeslagen op de secundaire sitecomputer:  

    -   Locatie van het bronbestand vergezeld gaan van een map met de naam **Redist** dat alle bestanden die eerder zijn gedownload met behulp van de Setup Downloader bevat.  

    -   Als een van de bestanden van **Redist** zijn niet beschikbaar is, mislukt de installatie de secundaire site te installeren.  

    -   Het computeraccount van de secundaire sitecomputer moet hebben **lezen** machtigingen aan de bron-bestand, map en -share.  

6.  Op de **SQL Server-instellingen** pagina, geef de versie van SQL Server moet worden gebruikt en configureer vervolgens gerelateerde instellingen.  

    > [!NOTE]  
    > Setup kan de gegevens die u op deze pagina invoert, totdat de installatie start niet valideren. Voordat u doorgaat, controleert u of deze instellingen.  

     **Installeren en configureren van een lokaal exemplaar van SQL Express op de secundaire sitecomputer**  

    -   **SQL Server-servicepoort**: Geef de poort van de SQL Server-service voor SQL Server Express moet worden gebruikt. Poort van de service is standaard geconfigureerd voor het gebruik van TCP-poort 1433, maar u kunt een andere poort configureren.  

    -   **SQL Server Broker-poort**: Geef de SQL Server Service Broker (SSB)-poort voor SQL Server Express moet worden gebruikt. De Service Broker is standaard geconfigureerd voor het gebruik van TCP-poort 4022, maar u kunt een andere poort configureren. U moet een geldige poort op die geen andere site of -service wordt gebruikt en dat er geen firewallbeperkingen opgeven.  

    > [!IMPORTANT]  
    > Wanneer de Configuration Manager SQL Server Express is geïnstalleerd, wordt SQL Server Express 2012 zonder servicepack geïnstalleerd:  

    > -   Voor de secundaire site worden ondersteund, nadat deze is geïnstalleerd, moet u SQL Server Express 2012 te upgraden [een ondersteunde versie](/sccm/core/plan-design/configs/support-for-sql-server-versions#bkmk_SQLVersions).
    > -   Daarnaast, als de nieuwe secundaire site-installatie niet kan worden voltooid, maar eerst de installatie van SQL Server Express 2012 is voltooid, moet u bijwerken dat exemplaar van SQL Server Express voordat Configuration Manager kan de installatie van de secundaire site opnieuw.  

     **Een bestaand exemplaar van SQL Server gebruiken**  

    -   **SQL Server-FQDN**: Controleer de FQDN voor de computer met SQL Server. U moet een lokale server met SQL Server gebruiken als host van de secundaire sitedatabase en u deze instelling niet wijzigen.  

    -   **SQL Server-exemplaar**: Geef het exemplaar van SQL Server gebruiken als de secundaire sitedatabase. Laat deze optie leeg als het standaardexemplaar gebruikt.  

    -   **Naam van ConfigMgr-sitedatabase**: Geef de naam moet worden gebruikt voor de secundaire sitedatabase.  

    -   **SQL Server Broker-poort**: Geef de SQL Server Service Broker (SSB)-poort voor SQL Server te gebruiken. U moet een geldige poort op die geen andere site of -service wordt gebruikt en die geen firewallbeperkingen blokkeren opgeven.  

    > [!TIP]  
    > Zie [ondersteund SQL Server-versies](../../../../core/plan-design/configs/support-for-sql-server-versions.md) voor een lijst van de SQL Server-versies die ondersteuning biedt voor System Center Configuration Manager.  

7.  Op de **distributiepunt** pagina, instellingen configureren voor het distributiepunt dat wordt geïnstalleerd op de secundaire siteserver.  

     **Vereiste instellingen:**  

    -   **Geef op hoe clientapparaten communiceren met het distributiepunt**: Kies tussen HTTP en HTTPS.  

    -   **Maak een zelfondertekend certificaat of importeer een PKI-clientcertificaat**: Kiezen tussen het gebruik van een zelfondertekend certificaat (waarmee u ook anonieme verbindingen toestaan van Configuration Manager-clients naar de Inhoudsbibliotheek) of een certificaat importeren uit uw PKI.  

         Het certificaat wordt gebruikt voor verificatie van het distributiepunt naar een beheerpunt voordat het distributiepunt statusberichten verzendt.  

         Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    **Optionele instellingen:**  

    -   **Installeer en Configureer IIS indien vereist door Configuration Manager**: Selecteer deze instelling om Configuration Manager installeren en configureren van Internet Information Services (IIS) op de server als deze nog niet is geïnstalleerd. IIS moet worden geïnstalleerd op alle distributiepunten.  

        > [!NOTE]  
        > Hoewel deze instelling optioneel is, moet IIS worden geïnstalleerd op de server voordat u een distributiepunt kan worden geïnstalleerd.  

    -   **BranchCache inschakelen en configureren voor dit distributiepunt**.  

    -   **Beschrijving**. Dit is een beschrijving voor het distributiepunt voor hulp bij het herkennen.  

    -   **Dit distributiepunt inschakelen voor voorbereide inhoud**.  

8.  Op de **Stationsinstellingen** pagina, geef de Stationsinstellingen voor het distributiepunt van de secundaire site.  

     U kunt maximaal twee schijfstations voor de Inhoudsbibliotheek en twee schijfstations voor de pakketshare configureren. Configuration Manager kan echter extra stations gebruiken wanneer de eerste twee de geconfigureerde stationsruimtereserve bereiken. De **Stationsinstellingen** pagina is waar u de prioriteit voor de schijfstations en de hoeveelheid vrije schijfruimte op elk schijfstation blijven configureren.  

    -   **Gereserveerde ruimte op station (MB)**: De waarde die u voor deze instelling configureert bepaalt de hoeveelheid vrije ruimte op een station voordat Configuration Manager een ander station kiest en verdergaat met het kopieerproces naar dat station. Inhoudsbestanden kunnen meerdere stations omvatten.  

    -   **Inhoudslocaties**: Geef de inhoudslocaties op voor de inhoud en de pakketshare. Configuration Manager kopieert inhoud naar de primaire Inhoudslocatie, totdat de hoeveelheid vrije schijfruimte wordt bereikt die is opgegeven voor **vrije schijfruimte (MB) reserveren**.

     De inhoudslocaties zijn standaard ingesteld op **automatische**. De primaire Inhoudslocatie is ingesteld op het schijfstation dat de meeste schijfruimte nodig tijdens de installatie is. De secundaire locatie is ingesteld op het schijfstation dat de meeste vrije schijfruimte na het primaire station heeft. Wanneer de primaire en secundaire stations de gereserveerde ruimte op station bereiken, wordt Configuration Manager selecteert een ander beschikbaar station met de meeste vrije schijfruimte en blijft het kopieerproces.  

9. Op de **Inhoudsvalidatie** pagina, Geef op of de integriteit van inhoudsbestanden op het distributiepunt moet worden gevalideerd.  

    -   Wanneer u inhoudsvalidatie op een planning inschakelt, wordt Configuration Manager start het proces op het geplande tijdstip, en wordt alle inhoud op het distributiepunt gecontroleerd.  

    -   U kunt ook de **validatieprioriteit van inhoud**.  

    -   U kunt de resultaten van het inhoudvalidatieproces in de Configuration Manager-console, Ga naar **bewaking** > **distributiestatus** > **inhoudsstatus**. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, Software-updatepakket en installatiekopie) wordt weergegeven.  

10. Op de **Grensgroepen** pagina, beheer de grensgroepen waaraan dit distributiepunt is toegewezen:  

    -   Tijdens inhoudsimplementatie moeten clients zich in een grensgroep die is gekoppeld aan het distributiepunt te gebruiken als bronlocatie voor inhoud.  

    -   U kunt selecteren de **terugvalbronlocatie voor inhoud toestaan** optie wilt toestaan dat clients buiten deze grensgroepen terug te vallen en het distributiepunt gebruiken als bronlocatie voor inhoud, wanneer er geen voorkeursdistributiepunten beschikbaar zijn.  

     Zie voor meer informatie over voorkeursdistributiepunten de [basisconcepten voor inhoudsbeheer](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) onderwerp.  

11. Op de **samenvatting** pagina, Controleer de instellingen en kies vervolgens **volgende** de secundaire site te installeren. Wanneer de wizard geeft de **voltooiing** pagina kunt u de wizard sluiten. De secundaire site-installatie wordt voortgezet op de achtergrond.  


### <a name="bkmk_verify"></a>Om te controleren of de status van de installatie van secundaire site  

1.  Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.  

2.  Selecteer de secundaire siteserver die u installeert en kies vervolgens **installatiestatus tonen**.  

    > [!TIP]  
    > Wanneer u meer dan één secundaire site tegelijk installeert, wordt de Prerequisite Checker wordt uitgevoerd op één site op een tijdstip en een site moet zijn voltooid voordat deze wordt gestart om te controleren van de volgende site.  
