---
title: Setup-Wizard | Microsoft-documenten
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f703376-5f2c-4fd2-8209-7028c931ddc7
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 14b4172ad713a3981b8a5abe182405e271d78c26
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="use-the-setup-wizard-to-install-system-center-configuration-manager-sites"></a>Gebruik de Wizard Setup voor het installeren van System Center Configuration Manager-sites

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Om een nieuwe System Center Configuration Manager-site installeert met behulp van een begeleide gebruikersinterface, moet u de installatiewizard van Configuration Manager (setup.exe) gebruiken. De wizard ondersteunt de installatie van een primaire site of centrale beheersite. U ook de wizard te gebruiken [een evaluatie-installatie bijwerken](../../../../core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install.md) van Configuration Manager naar een volledig gelicentieerde installatie. Wanneer u niet wilt u de wizard gebruikt, kunt u in plaats daarvan gebruiken een [installatiescript](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md) en een opdrachtregel installatie zonder toezicht uitvoert.

Een secundaire site installeren, moet u de site vanuit de Configuration Manager-console installeren. Secundaire sites ondersteunen niet de installatie van een script vanaf de opdrachtregel.

## <a name="bkmk_primary"></a>Installeer een centrale beheersite of primaire site
Gebruik de volgende procedure om een centrale beheersite of een primaire site te installeren of upgraden van een evaluatiesite naar een volledige licentie Configuration Manager-site.   

Voordat u de site-installatie, vertrouwd zijn met de details in de volgende artikelen:
 -  [Voorbereiden om sites te installeren](../../../../core/servers/deploy/install/prepare-to-install-sites.md)
 -  [Vereisten voor het installeren van sites](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md)

Als u een centrale beheersite als onderdeel van het scenario voor site-uitbreiding installeert, zoekt u naar de [uitbreiden een zelfstandige primaire site](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) sectie van dit onderwerp voordat u de volgende procedure.

### <a name="bkmk_installpri"></a>Een primaire of centrale beheersite installeren

1.  Voer op de computer waar u de site installeert,  **&lt;InstallationMedia\>\SMSSETUP\BIN\X64\Setup.exe** starten de **System Center Configuration Manager-installatiewizard**.  

    > [!NOTE]  
    > Wanneer u een centrale beheersite installeert op een zelfstandige primaire site uitbreiden of een nieuwe onderliggende primaire site in een bestaande hiërarchie installeert, gebruikt u installatiemedia (bronbestanden) die overeenkomt met de versie van de bestaande site of websites. Als u in de console-updates die zijn gewijzigd, de versie van de eerder geïnstalleerde sites hebt geïnstalleerd, hoeft u de oorspronkelijke installatiemedia. Gebruik in plaats daarvan de bronbestanden van de [CD. Meest recente map](../../../../core/servers/manage/the-cd.latest-folder.md) van een bijgewerkte site. Configuration Manager moet u bronbestanden gebruiken die overeenkomen met de versie van de bestaande site die de nieuwe site wordt de verbinding.  

2.  Op de **voordat u begint** pagina, kiest u **volgende**.  

3.  Op de **aan de slag** pagina, selecteer het type site dat u wilt installeren:  

    -   **Centrale beheersite**, als de eerste site van een nieuwe hiërarchie, of bij het uitbreiden van een zelfstandige primaire site:  

        Selecteer **een centrale beheersite van Configuration Manager installeren**.  

         Tijdens een latere fase van deze procedure krijgt u de keuze voor het installeren van een centrale beheersite als de eerste site van een nieuwe hiërarchie of een centrale beheersite om uit te breiden op een zelfstandige primaire site installeren.  

    -    **Primaire site**, als een zelfstandige primaire site die de eerste site van een nieuwe hiërarchie, of als een onderliggende primaire:  

        Selecteer **een primaire site van Configuration Manager installeert**.  

        > [!TIP]  
        > Doorgaans kunt u alleen selecteren de optie **gangbare installatieopties gebruiken voor een zelfstandige primaire site** indien u wenst te installeren van een zelfstandige primaire site in een testomgeving. Wanneer u deze optie selecteert Setup:  

        > -   Configureert de site automatisch als een zelfstandige primaire site.  
        > -   Maakt gebruik van een standaardinstallatiepad.  
        > -   Maakt gebruik van een lokale installatie van het standaardexemplaar van SQL Server voor de sitedatabase.  
        > -   Installeert een beheerpunt en een distributiepunt op de siteservercomputer.  
        > -   Configureert de site met Engels en de weergavetaal van het besturingssysteem op de primaire siteserver als deze overeenkomt met een van de talen die ondersteuning biedt voor Configuration Manager.  

4.  Op de **productcode** pagina:
    - Kies of voor het installeren van Configuration Manager als een evaluatie-editie of een gelicentieerde versie.  

      -   Als u een gelicentieerde versie selecteert, Voer uw productcode en kies **volgende**.  

      -   Als u een evaluatie-editie selecteren, kiest u **volgende**. (U kunt een evaluatie-installatie bijwerken naar een volledige installatie later.)  
    - Beginnen met de oktober 2016-release van versie 1606 basislijn media voor System Center Configuration Manager, kunt u de verloopdatum van uw Software Assurance-overeenkomst opgeven. Op deze pagina hebt u de optie om op te geven de **Software Assurance-vervaldatum** van uw gebruiksrechtovereenkomst als u een handige herinnering na die datum. Als u dit tijdens de installatie niet invoert, kunt u deze later vanuit binnen de Configuration Manager-console.

      > [!NOTE]   
      > Microsoft biedt geen valideren de vervaldatum die u hebt ingevoerd en deze datum niet gebruiken voor validatie van de licentie. In plaats daarvan kunt u dit gebruiken als een herinnering aan de vervaldatum. Dit is handig omdat Configuration Manager controleert regelmatig of er nieuwe software-updates aangeboden online, en de status van uw software assurance-licentie moet huidige zodat u komt in aanmerking voor het gebruik van deze aanvullende updates.    

      Zie voor meer informatie [volumelicenties en vertakkingen voor System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

5.  Op de **licentievoorwaarden voor Microsoft-Software** pagina, lees en accepteer de licentievoorwaarden.  

6.  Op de **vereiste licenties** pagina, lees en accepteer de licentievoorwaarden voor de vereiste software. Het installatieprogramma downloadt en installeert de software automatisch op sitesystemen of clients wanneer het is vereist. U moet alle selectievakjes controleren voordat u naar de volgende pagina doorgaat.  

7.  Op de **vereiste Downloads** pagina, Geef op of Setup de meest recente vereiste herdistribueerbare bestanden vanaf Internet downloaden moet of eerder bestanden gebruiken gedownloade:  

    -   Als u wilt dat Setup de bestanden te downloaden op dit moment, selecteert u **vereiste bestanden downloaden** en geef een locatie voor het opslaan van de bestanden in.  

    -   Als u eerder de bestanden had gedownload met behulp van [Downloadprogramma](../../../../core/servers/deploy/install/setup-downloader.md), selecteer **eerder gedownloade bestanden gebruiken** en geeft u de downloadmap.  

        > [!TIP]  
        > Als u eerder gedownloade bestanden gebruikt, controleert u of het pad naar de downloadmap de recentste versie van de bestanden bevat.  

8.  Op de **selectie van servertaal** pagina, selecteert u de talen die beschikbaar voor de Configuration Manager-console en voor rapporten zijn. (Engels is standaard geselecteerd en kan niet worden verwijderd.)  

9. Op de **Clienttaal** pagina, selecteert u de talen die beschikbaar zijn voor clientcomputers en geef op of alle clienttalen inschakelen voor clients van mobiele apparaten. (Engels is standaard geselecteerd en kan niet worden verwijderd.)  

    > [!IMPORTANT]  
    > Wanneer u een centrale beheersite gebruikt, zorg ervoor dat clienttalen die u op de centrale beheersite configureert omvat alle clienttalen die u voor elke onderliggende primaire site configureert. Dit is omdat clients die worden geïnstalleerd vanaf een distributiepunt toegang tot de clienttalen van de site op hoogste niveau, hebben terwijl clients die worden geïnstalleerd vanaf een beheerpunt toegang tot de clienttalen van hun toegewezen primaire site hebben.  

10. Op de **Site en installatie-instellingen** pagina, geeft u de volgende voor de nieuwe site die u installeert:  

    -   **Sitecode:** [Elke sitecode in een hiërarchie moet uniek zijn](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_sitecodes) en bestaat uit drie cijfers alfanumerieke tekens (A-Z) en 0 t/m 9. Aangezien de sitecode in mapnamen wordt gebruikt, gebruik geen Windows-gereserveerde namen voor de site, met inbegrip van:    
        -   AUX  
        -   CON    
        -   NUL    
        -   PRN    
        -   SMS  

        > [!NOTE]  
        > Setup controleren niet of de sitecode die u opgeeft, wordt al gebruikt of als er een gereserveerde naam.  

    -   **Naam van site:** Elke site vereist deze beschrijvende naam, die kan helpen u bij het identificeren van de site.  

    -   **Installatiemap:** Dit is het pad naar de Configuration Manager-installatie. U kunt de locatie niet wijzigen nadat de site is geïnstalleerd. Het pad kan ook Unicode-tekens of spaties bevatten.  

11. Op de **Site-installatie** pagina, gebruikt u de volgende optie die overeenkomt met uw scenario:  

    -   **Ik ben een centrale beheersite installeert:**  

         Op de **installatie van centrale beheersite** optie **installeren als de eerste site in een nieuwe hiërarchie**, en kies vervolgens **volgende** om door te gaan.  

    -   **Ik ben een zelfstandige primaire uitbreiden naar een hiërarchie met een centrale beheersite:**  

         Op de **installatie van centrale beheersite** optie **een bestaande zelfstandige primaire uitbreiden tot een hiërarchie**, geef de FQDN van de zelfstandige primaire siteserver en kies vervolgens **volgende** om door te gaan.  

         De media die u gebruikt voor het installeren van de nieuwe centrale beheersite moet overeenkomen met de versie van de primaire site.  

    -   **Ik ben een zelfstandige primaire site installeren:**  

         Op de **primaire Site-installatie** optie **de primaire site installeren als een zelfstandige site**, en kies vervolgens **volgende**.  

    -   **Ik ben een onderliggende primaire site installeren:**  

         Op de **primaire Site-installatie** optie **de primaire site lid aan een bestaande hiërarchie**, geef de FQDN-naam voor de centrale beheersite en kies vervolgens **volgende**.  

12. Op de **databasegegevens** pagina, geeft u de volgende informatie:  

    -   **SQL-servernaam (FQDN):** Standaard is deze ingesteld op de site server-computer.  

    -   **Instantienaam:** Dit is standaard leeg. Gebruikmaakt van het standaardexemplaar van SQL op de siteservercomputer.  

    -   **Databasenaam:** Standaard wordt deze ingesteld op CM_&lt;Sitecode\>. U bent gratis gebruik een andere naam die u opgeeft.  

    -   **Service Broker-poort:** Standaard wordt deze ingesteld op de standaardpoort voor SQL Server Service Broker (SSB) van 4022 te gebruiken. SQL gebruikt om te communiceren rechtstreeks met de sitedatabase op andere sites.  

13. Op de tweede **databasegegevens** pagina niet-standaardlocaties voor de SQL Server-gegevensbestand en het logboekbestand van SQL Server voor de sitedatabase kunt opgeven:  

    -   Standaardbestandslocaties voor SQL Server worden opgegeven.  

    -   De optie voor het opgeven van niet-standaard bestandslocaties is niet beschikbaar wanneer u een SQL Server-cluster.  

    -   De prerequisite checker kan niet worden uitgevoerd controle uit voor vrije schijfruimte voor niet-standaard bestandslocaties.  

14. Op de **SMS-Providerinstellingen** pagina, de FQDN-naam voor de server waarop u wilt installeren van de SMS-Provider opgeven.  

    -   De siteserver is standaard opgegeven.  

    -   Nadat de site is geïnstalleerd, kunt u aanvullende SMS-Providers.  

15. Op de **communicatie-instellingen voor Client** pagina, kiest u of alle sitesystemen zo accepteren alleen HTTPS-communicatie van clients of de communicatiemethode voor elke sitesysteemrol moet worden geconfigureerd.  

    Wanneer u selecteert **alle sitesysteemrollen accepteren alleen HTTPS-communicatie van clients**, de clientcomputer moet een geldig PKI-certificaat voor clientverificatie hebben. Zie voor meer informatie over PKI-certificaatvereisten [PKI-certificaatvereisten voor Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    > [!NOTE]  
    > Deze stap is alleen van toepassing wanneer u een primaire site installeert. Als u een centrale beheersite installeert, moet u deze stap overslaan.  

16. Op de **sitesysteemrollen** pagina, kiest u of een beheerpunt of distributiepunt wilt installeren. Voor elke rol die u hebt geïnstalleerd door Setup:  

    -   Moet u de **FQDN** voor de computer die de host voor de functie en kies de clientverbindingsmethode dat de server (HTTP of HTTPS) ondersteunt.  

    -   Als u hebt geselecteerd **alle sitesysteemrollen accepteren alleen HTTPS-communicatie van clients** op de vorige pagina de clientverbindingsinstellingen automatisch geconfigureerd voor HTTPS en kan niet worden gewijzigd, tenzij u teruggaat en de instelling wijzigt.  

    > [!NOTE]  
    > Deze stap is alleen van toepassing wanneer u een primaire site installeert. Als u een centrale beheersite installeert, moet u deze stap overslaan.  

    > [!NOTE]  
    > Voor het installeren van sitesysteemrollen, gebruikt Setup de **installatieaccount site**. Dit gebruikt standaard de computeraccount van de primaire site. Dit account moet een lokale beheerder op een externe computer voor het installeren van de sitesysteemrol. Als dit account beschikt niet over de vereiste machtigingen, schakel de sitesysteemrollen en installeert u ze later uit in de Configuration Manager-console na de configuratie van extra accounts te gebruiken als site-installatie systeemaccounts.  

17. Op de **gebruiksgegevens** pagina, lees de informatie over gegevens die Microsoft verzamelt en kies vervolgens **volgende**.  

18. De **Service Connection Point Setup** pagina is alleen beschikbaar tijdens de installatie:  

    -   Wanneer u een zelfstandige primaire site installeert.  

    -   Wanneer u een centrale beheersite installeert.  

    > [!NOTE]  
    > Als u een onderliggende primaire site installeert, slaat u deze stap (deze pagina is niet beschikbaar).  

     Als u een centrale beheersite als onderdeel van het scenario voor site-uitbreiding installeert en deze rol is al geïnstalleerd op de zelfstandige primaire site, moet u deze rol verwijderen van de zelfstandige primaire site. Slechts één exemplaar van deze rol is toegestaan in een hiërarchie, en dit alleen toegestaan op de bovenste site van de hiërarchie.  

     Nadat u een configuratie voor de **Service Connection Point**, kies **volgende**. (Nadat Setup is voltooid, kunt u deze configuratie uit in de Configuration Manager-console.)  

19. Op de **samenvatting van instellingen** pagina, de instelling die u hebt geselecteerd. Wanneer u klaar bent, kies **volgende** om Prerequisite Checker te starten.  

20. Op de **installatiecontrole voorafgaande** eventuele problemen die kunnen worden geïdentificeerd pagina worden weergegeven.  

    -   Als de Prerequisite Checker een probleem aantreft, kiest u een item in de lijst voor meer informatie over het oplossen van het probleem.  

    -   U moet elk item met de status van oplossen **mislukt** voordat u doorgaat met de site installeert. Items met de status van **waarschuwing** moet worden omgezet, maar ze de installatie van de site niet geblokkeerd.  

    -   Na het oplossen van problemen, ervoor kiezen **controle uitvoeren** de Prerequisite Checker opnieuw uit te voeren.  

     Wanneer de vereistencontrole wordt uitgevoerd en er zijn geen controles ontvangen een **mislukt** status, kunt u kiezen **begint met installeren** om de site-installatie te starten.  

    > [!TIP]  
    > Naast de feedback die is opgegeven in de wizard, vindt u meer informatie over vereiste problemen wanneer u de **ConfigMgrPrereq.log** bestand in de hoofdmap van het systeemstation van de computer die u installeert op. Zie voor een lijst van de installatie vereiste regels en beschrijvingen [lijst van de controles op vereisten voor System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

21. Op de **installatie** pagina Setup de installatie weergegeven. Wanneer de installatie van de hoofdsiteserver voltooid is, hebt u de optie te **sluiten** de installatiewizard. Wanneer u de wizard sluit, wordt de installatie en aanvankelijke siteconfiguraties blijven op de achtergrond.  

    -   U kunt een Configuration Manager-console verbinding maken met de site voordat de installatie is voltooid. Deze console verbinding als alleen-lezen en kunt u objecten en instellingen weergeven, maar u kan geen wijzigingen aanbrengen.  

    -   Nadat Setup is voltooid, moet u een console waarmee objecten en -instellingen kunt bewerken verbinding kunnen maken.  


## <a name="bkmk_expand"></a>Een zelfstandige primaire site uitbreiden
Wanneer u een zelfstandige primaire site als uw eerste site hebt geïnstalleerd, hebt u de optie later naar die site uitbreiden tot een grotere hiërarchie door een centrale beheersite installeert.   

Als u een zelfstandige primaire site uitbreidt, installeert u een nieuwe centrale beheersite die gebruikmaakt van de bestaande zelfstandige primaire site-database als een verwijzing. Nadat de nieuwe centrale beheersite is geïnstalleerd, wordt de zelfstandige primaire site fungeert als een onderliggende primaire site.

-   Alleen een zelfstandige primaire site kan worden uitgebreid naar een nieuwe hiërarchie.  

-   Slechts één zelfstandige primaire site kan worden uitgebreid naar een specifieke hiërarchie. U kunt deze optie niet gebruiken om toe te voegen extra zelfstandige primaire sites in dezelfde hiërarchie. In plaats daarvan migratie gebruiken om gegevens te migreren vanuit één hiërarchie in een andere.  

-   Nadat u een zelfstandige site in een hiërarchie met een centrale beheersite uitbreidt, kunt u bijkomende onderliggende primaire onderliggende sites toevoegen.  

-   Als een primaire site uit een hiërarchie met een centrale beheersite verwijderen, moet u de primaire site verwijderen.  

Om de site uitbreidt, kunt u de Setup Wizard van System Center Configuration Manager gebruiken voor het installeren van een nieuwe centrale beheersite met de volgende voorbehouden:  

-   U moet de centrale beheersite installeren met behulp van dezelfde versie van Configuration Manager als de zelfstandige primaire site.  

-   Op de **aan de slag** pagina van de installatiewizard u de optie voor het installeren van een centrale beheersite. In een later stadium van de installatie kiest u een optie om een bestaande zelfstandige primaire site uitbreidt.  

-   Bij de configuratie van de **Clienttaal** pagina voor de nieuwe centrale beheersite, moet u dezelfde clienttalen die zijn geconfigureerd voor de zelfstandige primaire site die u wilt uitbreiden.  

-   Op de **Site-installatie** pagina u de optie voor de zelfstandige primaire site uitbreidt.  

Als u wilt een zelfstandige primaire site uitbreidt, ziet u eerst de [vereisten voor het uitbreiden van een site](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand), en gebruik vervolgens de procedure  *[voor het installeren van een primaire of centrale beheersite](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_installpri)*eerder in dit artikel.


## <a name="bkmk_secondary"></a>Een secundaire site installeren
 De Configuration Manager-console kunt u een secundaire site installeert.  

-   Als de console die u gebruikt geen verbinding met de primaire site die de bovenliggende site naar de nieuwe secundaire site, wordt de opdracht voor het installeren van de site worden gerepliceerd naar de juiste primaire site.  

-   Voordat u de site-installatie, moet u ervoor te zorgen dat uw gebruikersaccount de vereiste machtigingen heeft en dat de computer die als voor de nieuwe secundaire site host fungeert voldoet aan alle vereisten voor gebruik als een secundaire siteserver.  

-   Wanneer u de secundaire site installeert, configureert Configuration Manager de nieuwe site voor het gebruik van de clientcommunicatiepoorten die op de bovenliggende primaire site zijn geconfigureerd.  

### <a name="bkmk_installsecondary"></a>Een secundaire site te installeren  


1.  Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**. Selecteer de site die de bovenliggende primaire site van de nieuwe secundaire site.  

2.  Kies **secundaire Site maken** starten de **Wizard secundaire Site maken**.  

3.  Op de **voordat u begint** pagina, controleren of de primaire site die wordt vermeld, de site die u wilt worden van het bovenliggende lid van de nieuwe secundaire site is. Kies **volgende**.  

4.  Op de **algemeen** pagina, geeft u de volgende:  

    -   **Sitecode**: Elke sitecode in een hiërarchie moet uniek zijn en daarvan uit van drie cijfers alfanumerieke tekens (A-Z) en 0 t/m 9. Aangezien de sitecode in mapnamen wordt gebruikt, gebruik geen Windows-gereserveerde namen voor de site, met inbegrip van:  

        -   AUX    
        -   CON    
        -   NUL    
        -   PRN  
        -   SMS  

       > [!NOTE]  
       > Setup controleren niet of de sitecode die u opgeeft is al in gebruik is of als een gereserveerde naam.  

    -   **Naam van de siteserver**: Dit is de FQDN-naam van de server waarop de nieuwe secundaire site wilt installeren.  

    -   **Sitenaam**: Elke site vereist deze beschrijvende naam, die kan helpen u bij het identificeren van de site.  

    -   **Installatiemap**: Dit is het pad naar de Configuration Manager-installatie. U kunt de locatie niet wijzigen nadat de site is geïnstalleerd. Het pad mag geen Unicode-tekens of spaties bevatten.  

    > [!IMPORTANT]  
    > Nadat u gegevens op deze pagina opgeeft, kunt u kiezen **samenvatting** met de standaardinstellingen voor de rest van de secundaire site-opties, en gaat u rechtstreeks naar de **samenvatting** pagina van de wizard.  

    > -   Deze optie alleen gebruiken wanneer u vertrouwd met de standaardinstellingen in deze wizard bent, en ze de instellingen die u wilt gebruiken.  
    > -   Grensgroepen zijn niet gekoppeld aan het distributiepunt wanneer u de standaardinstellingen gebruikt. Totdat het configureren van grensgroepen met de secundaire siteserver niet clients daarom het distributiepunt dat is geïnstalleerd op deze secundaire site als een bronlocatie voor inhoud gebruikt.  

5.  Op de **installatiebronbestanden** pagina, kiest u hoe de secundaire sitecomputer verkrijgt bronbestanden voor installatie van de site.  

     Wanneer u bronbestanden gebruiken die zijn opgeslagen op het netwerk of op de secundaire sitecomputer opgeslagen:  

    -   De bronlocatie van het bestand moet bevatten een map genaamd **Redist** waarin de bestanden die eerder zijn gedownload met behulp van de Setup Downloader.  

    -   Als een van de bestanden van **Redist** zijn niet beschikbaar is, mislukt de installatie om de secundaire site te installeren.  

    -   De computeraccount van de secundaire site moet hebben **lezen** machtigingen aan de bron-bestand, map en -share.  

6.  Op de **SQL Server-instellingen** pagina, geef de versie van SQL Server moet worden gebruikt en configureer vervolgens gerelateerde instellingen.  

    > [!NOTE]  
    > De informatie die u op deze pagina invoert, totdat de installatie start niet door Setup worden gevalideerd. Controleer deze instellingen voordat u doorgaat.  

     **Installeren en configureren van een lokaal exemplaar van SQL Express op de secundaire sitecomputer**  

    -   **SQL Server-servicepoort**: Geef de poort voor de SQL Server-service voor SQL Server Express moet worden gebruikt. De servicepoort is standaard geconfigureerd voor het gebruik van TCP-poort 1433, maar u kunt een andere poort configureren.  

    -   **SQL Server Broker-poort**: Geef de SQL Server Service Broker (SSB)-poort voor SQL Server Express moet worden gebruikt. De Service Broker is standaard geconfigureerd voor het gebruik van TCP-poort 4022, maar u kunt een andere poort configureren. U moet een geldige poort opgeven die geen andere site of service wordt gebruikt, en die geen firewallbeperkingen.  

    > [!IMPORTANT]  
    > Wanneer Configuration Manager SQL Server Express installeert, installeert het SQL Server 2012 Express zonder servicepack:  

    > -   Voor de secundaire site worden ondersteund, nadat deze is geïnstalleerd, moet u SQL Server Express 2012 te upgraden [een ondersteunde versie](/sccm/core/plan-design/configs/support-for-sql-server-versions#bkmk_SQLVersions).
    > -   Daarnaast, als de nieuwe secundaire site-installatie niet kan worden voltooid, maar eerst de installatie van SQL Server Express 2012 is voltooid, moet u bijwerken dat exemplaar van SQL Server Express voordat Configuration Manager kan de secundaire site-installatie met succes opnieuw.  

     **Een bestaand exemplaar van SQL Server gebruiken**  

    -   **SQL Server-FQDN**: Controleer de FQDN-naam voor de computer waarop SQL Server wordt uitgevoerd. U moet een lokale server met SQL Server gebruiken voor het hosten van de secundaire sitedatabase en u deze instelling niet wijzigen.  

    -   **SQL Server-exemplaar**: Geef het exemplaar van SQL Server wilt gebruiken als de secundaire sitedatabase. Laat deze optie leeg als u wilt de standaardinstantie gebruikt.  

    -   **Naam van ConfigMgr-sitedatabase**: Geef de naam moet worden gebruikt voor de secundaire sitedatabase.  

    -   **SQL Server Broker-poort**: Geef de SQL Server Service Broker (SSB)-poort voor SQL Server moet worden gebruikt. U moet een geldige poort opgeven die geen andere site of service wordt gebruikt, en die geen geblokkeerd door firewallbeperkingen.  

    > [!TIP]  
    > Zie [ondersteund SQL Server-versies](../../../../core/plan-design/configs/support-for-sql-server-versions.md) voor een lijst van de SQL Server-versies die ondersteuning biedt voor System Center Configuration Manager.  

7.  Op de **distributiepunt** pagina, instellingen configureren voor het distributiepunt dat wordt geïnstalleerd op de secundaire siteserver.  

     **Vereiste instellingen:**  

    -   **Geef op hoe clientapparaten communiceren met het distributiepunt**: Kies tussen HTTP en HTTPS.  

    -   **Maak een zelfondertekend certificaat of importeer een PKI-clientcertificaat**: Kies tussen een zelfondertekend certificaat (waarmee u ook anonieme verbindingen toestaan van Configuration Manager-clients naar de Inhoudsbibliotheek) of een certificaat importeren uit uw PKI.  

         Het certificaat wordt gebruikt voor verificatie van het distributiepunt naar een beheerpunt voordat het distributiepunt statusberichten verzendt.  

         Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    **Optionele instellingen:**  

    -   **Installeer en Configureer IIS indien vereist door Configuration Manager**: Selecteer deze instelling om Configuration Manager installeren en configureren van Internet Information Services (IIS) op de server, als deze nog niet is geïnstalleerd. IIS moet worden geïnstalleerd op alle distributiepunten.  

        > [!NOTE]  
        > Hoewel deze instelling optioneel is, moet IIS worden geïnstalleerd op de server voordat u een distributiepunt kan worden geïnstalleerd.  

    -   **Inschakelen en configureren van BranchCache voor dit distributiepunt**.  

    -   **Beschrijving**. Dit is een beschrijving voor het distributiepunt kunt u deze herkennen.  

    -   **Dit distributiepunt inschakelen voor voorbereide inhoud**.  

8.  Op de **Stationsinstellingen** pagina, geef de Stationsinstellingen voor het distributiepunt van de secundaire site.  

     U kunt maximaal twee schijfstations voor de Inhoudsbibliotheek en twee schijfstations voor de pakketshare configureren. Configuration Manager kan echter extra stations gebruiken wanneer de eerste twee de geconfigureerde stationsruimtereserve bereiken. De **Stationsinstellingen** pagina is waar u de prioriteit configureren voor de schijfstations en de hoeveelheid vrije schijfruimte op elk schijfstation moet blijven.  

    -   **Gereserveerde ruimte op station (MB)**: De waarde die u voor deze instelling configureert bepaalt de hoeveelheid vrije ruimte op een station voordat Configuration Manager een ander station kiest en verdergaat met het kopieerproces naar dat station. Inhoudsbestanden kunnen meerdere stations omvatten.  

    -   **Inhoudslocaties**: Geef de inhoudslocaties voor de inhoud van tapewisselaar en pakket-share. Configuration Manager kopieert inhoud naar de primaire Inhoudslocatie tot de hoeveelheid vrije ruimte de waarde die is opgegeven voor bereikt **schijfruimte (MB) reserveren**.

     De inhoudslocaties zijn standaard ingesteld op **automatische**. De primaire Inhoudslocatie is ingesteld op het schijfstation dat de meeste schijfruimte heeft tijdens de installatie. De secundaire locatie is ingesteld op het schijfstation dat de meeste vrije schijfruimte na het primaire station heeft. Wanneer de primaire en secundaire stations de gereserveerde ruimte op station bereiken, wordt Configuration Manager een ander beschikbaar station met de meeste vrije schijfruimte kiest en verdergaat met het kopieerproces.  

9. Op de **Inhoudsvalidatie** pagina, opgeven of de integriteit van inhoudsbestanden op het distributiepunt moet worden gevalideerd.  

    -   Wanneer u inhoudsvalidatie op een planning inschakelt, Configuration Manager start het proces op het geplande tijdstip, en alle inhoud op het distributiepunt gecontroleerd.  

    -   U kunt ook de **inhoud validatieprioriteit**.  

    -   U kunt de resultaten van het inhoudvalidatieproces in de Configuration Manager-console, gaat u naar **bewaking** > **distributiestatus** > **inhoudsstatus**. De inhoud van ieder pakkettype (bijvoorbeeld, toepassing, Software-updatepakket en installatiekopie) wordt weergegeven.  

10. Op de **Grensgroepen** pagina, het beheren van de grensgroepen waaraan dit distributiepunt is toegewezen:  

    -   Tijdens inhoudsimplementatie moeten clients zich in een grensgroep die is gekoppeld aan het distributiepunt gebruiken als bronlocatie voor inhoud.  

    -   Kunt u de **terugvalbronlocatie voor inhoud toestaan** optie wilt toestaan dat clients buiten deze grensgroepen terug te vallen en gebruik het distributiepunt als bronlocatie voor inhoud wanneer er geen voorkeursdistributiepunten beschikbaar zijn.  

     Zie voor meer informatie over voorkeursdistributiepunten de [fundamentele concepten voor inhoudsbeheer](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) onderwerp.  

11. Op de **samenvatting** pagina, Controleer de instellingen en kies vervolgens **volgende** de secundaire site te installeren. Wanneer de wizard geeft de **voltooiing** pagina kunt u de wizard sluiten. De secundaire site-installatie wordt voortgezet op de achtergrond.  


### <a name="bkmk_verify"></a>De secundaire site-installatie controleren  

1.  Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.  

2.  Selecteer de secundaire site-server die u installeert, en kies vervolgens **installatiestatus tonen**.  

    > [!TIP]  
    > Als u meer dan één secundaire site tegelijk installeert, wordt de Prerequisite Checker op een tijdstip doel wordt uitgevoerd op een enkele site en een site moet worden voltooid voordat deze wordt gecontroleerd van de volgende site.  

