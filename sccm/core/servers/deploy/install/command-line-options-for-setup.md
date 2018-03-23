---
title: Opdrachtregelopties voor Setup
titleSuffix: Configuration Manager
description: Maken van automatiseringsscripts voor System Center Configuration Manager installeren vanaf een opdrachtregel.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0da167f1-52cf-4dfd-8f73-833ca3eb8478
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: fede359c884ef8b4027935b2e3fb48a5b7543d26
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="command-line-options-for-setup-in-system-center-configuration-manager"></a>Opdrachtregelopties voor setup in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Gebruik de volgende informatie voor het configureren van scripts of System Center Configuration Manager installeren vanaf een opdrachtregel.  

##  <a name="bkmk_setup"></a> Opdrachtregelopties voor setup  
 **/ DEINSTALL**  
 Hiermee verwijdert u de site. Voer setup uit vanaf de site server-computer.  

 **/ DONTSTARTSITECOMP**  
 Hiermee installeert u een site, maar de service Site Component Manager kan niet starten. De site is niet actief totdat de service Site Component Manager is gestart. Site Component Manager is verantwoordelijk voor het installeren en starten van de service SMS_Executive en aanvullende processen op de site. Nadat de site-installatie is voltooid, wanneer u de service Site Component Manager start, installeert de service SMS_Executive en aanvullende processen die nodig zijn voor de site om te werken.  

 **/HIDDEN**  
 Hiermee verbergt u de gebruikersinterface tijdens de installatie. Gebruik deze optie alleen in combinatie met de **/SCRIPT** optie. Het script zonder toezicht-bestand moet alle vereiste opties bevatten, anders mislukt setup.  

 **/NOUSERINPUT**  
 Hiermee schakelt gebruikersinvoer tijdens de installatie, maar de wizard setup wordt weergegeven. Gebruik deze optie alleen in combinatie met de **/SCRIPT** optie. Het script zonder toezicht-bestand moet alle vereiste opties bevatten, anders mislukt setup.  

 **/RESETSITE**  
 Voert een site opnieuw instellen die de database en serviceaccounts voor de site wordt opnieuw ingesteld. Het installatieprogramma uitvoeren vanuit  **< *Configuration Manager-installatiepad*> \BIN\X64** op de siteserver. Zie voor meer informatie over het opnieuw instellen van de site, de [een site resetten](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_reset) in sectie [uw infrastructuur van System Center Configuration Manager aanpassen](../../../../core/servers/manage/modify-your-infrastructure.md).  

 **/ TESTDBUPGRADE <*exemplaarnaam*>\\<*databasenaam*>**  
 Voert een test op een back-up van de sitedatabase om ervoor te zorgen dat de database geschikt voor een upgrade is. Geef de instantienaam en databasenaam voor de sitedatabase. Als u alleen de databasenaam opgeeft, gebruikt setup de standaardinstantienaam.  

> [!IMPORTANT]  
>  Deze opdrachtregeloptie te gebruiken op uw productie-sitedatabase niet uitgevoerd. Deze opdrachtregeloptie te gebruiken op uw productiesitedatabase uitgevoerd upgrades van de sitedatabase en kan de site onbruikbaar.  

 **/UPGRADE**  
 Voert een upgrade zonder toezicht van een site. Als u werkt met **/UPGRADE**, moet u de productcode, inclusief de liggende streepjes (-). Bovendien moet u het pad naar de eerder gedownloade vereiste installatiebestanden.  

 Voorbeeld: `setupwpf.exe /UPGRADE xxxxx-xxxxx-xxxxx-xxxxx-xxxxx <path to external component files>`  

 Zie voor meer informatie over de vereiste bestanden voor setup [Setup Downloader](setup-downloader.md).  

 **/ SCRIPT <*pad naar setup-script*>**  
 Installaties zonder toezicht uitvoert. Is een setup-initialisatiebestand vereist wanneer u de **/SCRIPT** optie. Zie voor meer informatie over het voert u setup zonder toezicht [sites installeren met een opdrachtregel](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).  

 **/ SDKINST <*FQDN-naam van de SMS-Provider*>**  
 De SMS-Provider wordt geïnstalleerd op de opgegeven computer. Geef de volledig gekwalificeerde domeinnaam (FQDN) voor de computer van de SMS-Provider. Zie voor meer informatie over de SMS-Provider [plannen voor de SMS-Provider](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

 **/ SDKDEINST <*FQDN-naam van de SMS-Provider*>**  
 Hiermee verwijdert u de SMS-Provider op de opgegeven computer. Geef de FQDN-naam voor de computer van de SMS-Provider.  

 **/ MANAGELANGS <*scriptpad taal*>**  
 Beheert de talen die op een eerder geïnstalleerde site zijn geïnstalleerd. Om deze optie gebruikt, voert u setup uit vanaf  **< *Configuration Manager-installatiepad*> \BIN\X64** op de siteserver. De locatie opgeven voor het taalscriptbestand dat de taalinstellingen bevat. Zie voor meer informatie over de beschikbare taalopties in het scriptbestand voor taal, de [opdrachtregelopties voor het beheren van talen](#bkmk_Lang) sectie.  

##  <a name="bkmk_Lang"></a> Opdrachtregelopties voor het beheren van talen  
 **Identificatie**  

-   **Naam sleutel:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** ManageLanguages  

    -   **Details:** Beheert de server, client en mobiele clienttaalondersteuning op een site.  

**Opties**  

-   **Naam sleutel:** AddServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de servertalen die beschikbaar zijn voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar.  

-   **Naam sleutel:** AddClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de talen die beschikbaar zijn voor clientcomputers. Engels is standaard beschikbaar.  

-   **Naam sleutel:** DeleteServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Naam sleutel:** DeleteClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor clientcomputers. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Naam sleutel:** MobileDeviceLanguage  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Hiermee geeft u op of de clienttalen voor mobiele apparaten zijn geïnstalleerd.  

-   **Naam sleutel:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of setup vereiste bestanden al zijn gedownload. Als u een waarde van bijvoorbeeld **0**, setup de bestanden downloaden.  

-   **Naam sleutel:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor setup. Afhankelijk van de **PrerequisiteComp** waarde, gebruikt het installatieprogramma dit pad gedownloade bestanden wilt opslaan of vinden eerder gedownloade bestanden.  

##  <a name="bkmk_Unattended"></a> Sleutels voor een scriptbestand voor installatie zonder toezicht  
 Gebruik de volgende secties voor hulp bij het maken van uw script voor installatie zonder toezicht. De lijsten ziet u de beschikbare installatiescriptsleutels, de bijbehorende waarden, of ze zijn vereist, welk type installatie ze worden gebruikt voor en een korte beschrijving van de sleutel.  

### <a name="unattended-install-for-a-central-administration-site"></a>Installatie zonder toezicht voor een centrale beheersite  
 Gebruik de volgende informatie op een centrale beheersite installeren met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Naam sleutel:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** InstallCAS  

    -   **Details:** Een centrale beheersite installeert.  

-   **Naam sleutel:** CDLatest  

    -   **Vereist:** Ja, alleen bij gebruik van media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media in een CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite herstelt. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**Opties**  

-   **Naam sleutel:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *of* Eval  

    -   **Details:** Hiermee geeft u de productcode voor de Configuration Manager de installatie, inclusief de streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Naam sleutel:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren.  

-   **Naam sleutel:** Sitenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Geeft de naam voor deze site.  

-   **Naam sleutel:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad Configuration Manager*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Naam sleutel:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als host voor de SMS-Provider fungeert. U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.  

-   **Naam sleutel:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of setup vereiste bestanden al zijn gedownload. Als u een waarde van bijvoorbeeld **0**, setup de bestanden downloaden.  

-   **Naam sleutel:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor setup. Afhankelijk van de **PrerequisiteComp** waarde, gebruikt het installatieprogramma dit pad gedownloade bestanden wilt opslaan of vinden eerder gedownloade bestanden.  

-   **Naam sleutel:** AdminConsole  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of de Configuration Manager-console te installeren.  

-   **Naam sleutel:** JoinCEIP  
    > [!Note]  
    > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen geen lid worden van  

         1 = join  

    -   **Details:** Hiermee geeft u op of u deelneemt aan het Customer Experience Improvement Program (CEIP).  

-   **Naam sleutel:** AddServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de servertalen die beschikbaar zijn voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar.  

-   **Naam sleutel:** AddClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de talen die beschikbaar zijn voor clientcomputers. Engels is standaard beschikbaar.  

-   **Naam sleutel:** DeleteServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Naam sleutel:** DeleteClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor clientcomputers. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Naam sleutel:** MobileDeviceLanguage  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Hiermee geeft u op of de clienttalen voor mobiele apparaten zijn geïnstalleerd.  

**SQLConfigOptions**  

-   **Naam sleutel:** SQLServerName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SQL-servernaam*>  

    -   **Details:** Geeft de naam van de server of het geclusterde exemplaar waarop SQL Server wordt uitgevoerd en die de sitedatabase zal hosten.  

-   **Naam sleutel:** DatabaseName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>  

    -   **Details:** Hiermee geeft u de naam van de SQL Server-database te maken of de SQL Server-database moet worden gebruikt, wanneer de database van centrale beheersite wordt geïnstalleerd.  

        > [!IMPORTANT]  
        >  Als u het standaardexemplaar niet gebruikt, moet u de exemplaarnaam en de naam van de sitedatabase opgeven.  

-   **Naam sleutel:** SQLSSBPort  

    -   **Vereist:** Nee  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Geeft de poort voor SQL Server Service Broker (SSB) die SQL Server gebruikt. SSB is standaard geconfigureerd voor het gebruik van TCP-poort 4022, maar u kunt een andere poort gebruiken.  

-   **Naam sleutel:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar MDB-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database mdb-bestand.  

-   **Naam sleutel:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar LDF-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**CloudConnectorOptions**  

-   **Naam sleutel:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of voor het installeren van een service connection point op deze site. Omdat het serviceverbindingspunt kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Naam sleutel:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Naam sleutel:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of het service connection point een proxyserver gebruikt.  

-   **Naam sleutel:** ProxyName  

    -   **Vereist:** Vereist wanneer **UseProxy** gelijk is aan 1  

    -   **Waarden:** <*FQDN van proxyserver*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die gebruikmaakt van het serviceverbindingspunt wordt gehost.  

-   **Naam sleutel:** ProxyPort  

    -   **Vereist:** Vereist wanneer **UseProxy** gelijk is aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer dat moet worden gebruikt voor de proxypoort op.  

### <a name="unattended-install-for-a-primary-site"></a>Installatie zonder toezicht voor een primaire site  
Gebruik de volgende informatie op een primaire site installeren met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Naam sleutel:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** InstallPrimarySite  

    -   **Details:** Een primaire site installeert.  

-   **Naam sleutel:** CDLatest  

    -   **Vereist:** Ja, alleen bij gebruik van media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media in een CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite herstelt. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**Opties**  

-   **Naam sleutel:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *of* Eval  

    -   **Details:** Hiermee geeft u de productcode voor de Configuration Manager de installatie, inclusief de streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Naam sleutel:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren.  

-   **Naam sleutel:** SiteName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Geeft de naam voor deze site.  

-   **Naam sleutel:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad Configuration Manager*>

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Naam sleutel:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als host voor de SMS-Provider fungeert. U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.  

-   **Naam sleutel:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of setup vereiste bestanden al zijn gedownload. Als u een waarde van bijvoorbeeld **0**, setup de bestanden downloaden.  

-   **Naam sleutel:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor setup. Afhankelijk van de **PrerequisiteComp** waarde, gebruikt het installatieprogramma dit pad gedownloade bestanden wilt opslaan of vinden eerder gedownloade bestanden.  

-   **Naam sleutel:** AdminConsole  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of de Configuration Manager-console te installeren.  

-   **Naam sleutel:** JoinCEIP  
    > [!Note]  
    > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen geen lid worden van  

         1 = join  

    -   **Details:** Hiermee geeft u op of u deelneemt aan het programma voor Kwaliteitsverbetering.  

-   **Naam sleutel:** ManagementPoint  

    -   **Vereist:** Nee  

    -   **Waarden:** <*siteserver-FQDN van beheerpunt*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de sitesysteemrol management host fungeert.  

-   **Naam sleutel:** ManagementPointProtocol  

    -   **Vereist:** Nee  

    -   **Waarden:** HTTPS *of* HTTP  

    -   **Details:** Hiermee geeft u het protocol moet worden gebruikt voor het beheerpunt.  

-   **Naam sleutel:** DistributionPoint  

    -   **Vereist:** Nee  

    -   **Waarden:** <*site distributiepuntserver FQDN-naam*>  

    -   **Details:** Hiermee geeft u het protocol moet worden gebruikt voor het distributiepunt.  

-   **Naam sleutel:** DistributionPointProtocol  

    -   **Vereist:** Nee  

    -   **Waarden:** HTTPS *of* HTTP  

    -   **Details:** Hiermee geeft u het protocol moet worden gebruikt voor het distributiepunt.  

-   **Naam sleutel:** RoleCommunicationProtocol  

    -   **Vereist:** Ja  

    -   **Waarden:** EnforceHTTPS *or* HTTPorHTTPS  

    -   **Details:** Geeft aan of alle sitesystemen zo accepteren alleen HTTPS-communicatie van clients of de communicatiemethode voor elke sitesysteemrol moet worden geconfigureerd. Als u inschakelt om **EnforceHTTPS**, clientcomputer moet beschikken over een geldige openbare-sleutelinfrastructuur (PKI)-certificaat voor clientverificatie.  

-   **Naam sleutel:** ClientsUsePKICertificate  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet gebruiken  

         1 = gebruiken  

    -   **Details:** Hiermee geeft u op of clients een PKI-clientcertificaat gebruiken om te communiceren met sitesysteemrollen.  

-   **Naam sleutel:** AddServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de servertalen die beschikbaar zijn voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar.  

-   **Naam sleutel:** AddClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de talen die beschikbaar zijn voor clientcomputers. Engels is standaard beschikbaar.  

-   **Naam sleutel:** DeleteServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Naam sleutel:** DeleteClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, of ZHH  

    -   **Details:** Wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor clientcomputers. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Naam sleutel:** MobileDeviceLanguage  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Hiermee geeft u op of de clienttalen voor mobiele apparaten zijn geïnstalleerd.  

**SQLConfigOptions**  

-   **Naam sleutel:** SQLServerName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SQL-servernaam*>  

    -   **Details:** Geeft de naam van de server of het geclusterde exemplaar waarop SQL Server wordt uitgevoerd en die de sitedatabase zal hosten.  

-   **Naam sleutel:** DatabaseName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>  

    -   **Details:** Hiermee geeft u de naam van de SQL Server-database te maken of de SQL Server-database moet worden gebruikt bij het installeren van de primaire sitedatabase.  

        > [!IMPORTANT]  
        >  Als u het standaardexemplaar niet gebruikt, moet u de exemplaarnaam en de naam van de sitedatabase opgeven.  

-   **Naam sleutel:** SQLSSBPort  

    -   **Vereist:** Nee  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Hiermee geeft u de SSB-poort die SQL Server gebruikt. SSB is standaard geconfigureerd voor het gebruik van TCP-poort 4022, maar u kunt een andere poort gebruiken.  

-   **Naam sleutel:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar MDB-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database mdb-bestand.  

-   **Naam sleutel:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar LDF-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**HierarchyExpansionOption**  

-   **Naam sleutel:** CCARSiteServer  

    -   **Vereist:** Nee  

    -   **Waarden:** <*centrale beheersite FQDN-naam*>  

    -   **Details:** Hiermee geeft u de centrale beheersite die een primaire site wordt gekoppeld aan als lid van de Configuration Manager-hiërarchie. Geef de centrale beheersite tijdens de installatie.  

-   **Naam sleutel:** CASRetryInterval  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Interval*>  

    -   **Details:** Hiermee geeft u het interval (in minuten) waarna wordt geprobeerd een verbinding met de centrale beheersite nadat de verbinding is verbroken. Bijvoorbeeld, als de verbinding met de centrale beheersite mislukt, de primaire site wacht gedurende het aantal minuten dat u opgeeft voor de **CASRetryInterval** waarde en vervolgens reattempts de verbinding.  

-   **Naam sleutel:** WaitForCASTimeout  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Time-out*>  

         Een waarde van **0** naar **100**  

    -   **Details:** Hiermee geeft u de maximum time-outwaarde (in minuten) voor een primaire site verbinding maken met de centrale beheersite. Bijvoorbeeld, als een primaire site geen verbinding maken met een centrale beheersite, de primaire site opnieuw de verbinding met de centrale beheersite op basis van de **CASRetryInterval** waarde totdat de **WaitForCASTimeout** periode is bereikt. U kunt een waarde opgeven van **0** naar **100**.  

**CloudConnectorOptions**  

-   **Naam sleutel:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of voor het installeren van een service connection point op deze site. Omdat het serviceverbindingspunt kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Naam sleutel:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*\>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Naam sleutel:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of het service connection point een proxyserver gebruikt.  

-   **Naam sleutel:** ProxyName  

    -   **Vereist:** Vereist wanneer **UseProxy** gelijk is aan 1  

    -   **Waarden:** <*FQDN van proxyserver*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die gebruikmaakt van het serviceverbindingspunt wordt gehost.  

-   **Naam sleutel:** ProxyPort  

    -   **Vereist:** Vereist wanneer **UseProxy** gelijk is aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer dat moet worden gebruikt voor de proxypoort op.  

### <a name="unattended-recovery-for-a-central-administration-site"></a>Herstel voor een centrale beheersite zonder toezicht  
 Gebruik de volgende informatie op een centrale beheersite herstellen met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Naam sleutel:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** RecoverCCAR  

    -   **Details:** Een centrale beheersite herstelt.  

-   **Naam sleutel:** CDLatest  

    -   **Vereist:** Ja, alleen bij gebruik van media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media in een CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite herstelt. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**RecoveryOptions**  

-   **Naam sleutel:** ServerRecoveryOptions  

    -   **Vereist:** Ja  

    -   **Waarden:** 1, 2 of 4  

         1 = siteserver herstellen en SQL Server.  

         2 = Alleen siteserver herstellen.  

         4 = Alleen SQL Server herstellen.  

    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide wordt hersteld. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instellen voor de **ServerRecoveryOptions** instelling:  

        -   Waarde = 1: U hebt de mogelijkheid om op te geven van een waarde op voor de **SiteServerBackupLocation** sleutel op de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 2: U hebt de mogelijkheid om op te geven van een waarde op voor de **SiteServerBackupLocation** sleutel op de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 4: De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

-   **Naam sleutel:** DatabaseRecoveryOptions  

    -   **Vereist:** Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.  

    -   **Waarden:** 10, 20, 40 of 80  

         10 = De sitedatabase uit de back-up herstellen.  

         20 = Gebruik een sitedatabase die handmatig wordt hersteld met behulp van een andere methode.  

         40 = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  

         80 = databaseherstel overslaan.  

    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door setup wordt hersteld.  

-   **Naam sleutel:** ReferenceSite  

    -   **Vereist:** Deze sleutel is vereist wanneer de instelling **DatabaseRecoveryOptions** een waarde heeft van **40**.  

    -   **Waarden:** <*referentiesite FQDN-naam*>  

    -   **Details:** Hiermee geeft u de primaire site die gebruikmaakt van de centrale beheersite globale gegevens herstelt als de databaseback-up ouder dan de bewaarperiode voor wijzigingen bijhouden is of wanneer u een site zonder een back-up herstelt.  

         Wanneer u geen referentiesite opgeeft en de back-up ouder dan de bewaarperiode voor wijzigingen bijhouden is, worden alle primaire sites opnieuw geïnitialiseerd met de herstelde gegevens van de centrale beheersite.  

         Wanneer u geen referentiesite opgeeft en de back-up valt binnen de bewaarperiode voor wijzigingen bijhouden, alleen de wijzigingen die zijn aangebracht nadat de back-up worden gerepliceerd van primaire sites. Wanneer er conflicterende wijzigingen van verschillende primaire sites zijn, gebruikt de centrale beheersite de eerste die het ontvangt.  

-   **Naam sleutel:** SiteServerBackupLocation  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar back-upset siteserver*>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

-   **Naam sleutel:** Back-uplocatie  

    -   **Vereist:** Deze sleutel is vereist bij het configureren van een waarde van **1** of **4** voor de **ServerRecoveryOptions** sleutel en kunt u een waarde van configureert **10** voor de **DatabaseRecoveryOptions** sleutel.  

    -   **Waarden:** <*pad naar back-upset van sitedatabase*>  

    -   **Details:** Hiermee geeft u het pad naar back-upset van de sitedatabase.  

**Opties**  

-   **Naam sleutel:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *of* Eval  

    -   **Details:** Hiermee geeft u de productcode voor de Configuration Manager de installatie, inclusief de streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Naam sleutel:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren. De sitecode opgeven die de site vóór de fout gebruikt.

-   **Naam sleutel:** SiteName  

    -   **Vereist:** Nee  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Geeft de naam voor deze site.  

-   **Naam sleutel:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad Configuration Manager*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Naam sleutel:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als host fungeert voor de SMS-Provider. Geef op de server die als host van de SMS-Provider voorafgaand aan de fout.  

         U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie. Zie voor meer informatie over de SMS-Provider [plannen voor de SMS-Provider voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Naam sleutel:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of setup vereiste bestanden al zijn gedownload. Als u een waarde van bijvoorbeeld **0**, setup de bestanden downloaden.  

-   **Naam sleutel:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor setup. Afhankelijk van de **PrerequisiteComp** waarde, gebruikt het installatieprogramma dit pad gedownloade bestanden wilt opslaan of vinden eerder gedownloade bestanden.  

-   **Naam sleutel:** AdminConsole  

    -   **Vereist:** Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of de Configuration Manager-console te installeren.  

-   **Naam sleutel:** JoinCEIP  
    > [!Note]  
    > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen geen lid worden van  

         1 = join  

    -   **Details:** Hiermee geeft u op of u deelneemt aan het programma voor Kwaliteitsverbetering.  

**SQLConfigOptions**  

-   **Naam sleutel:** SQLServerName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SQL-servernaam*>  

    -   **Details:** Geeft de naam van de server of het geclusterde exemplaar waarop SQL Server wordt uitgevoerd en die als host fungeert voor de sitedatabase. Geef op dezelfde server die de sitedatabase voorafgaand aan de fout wordt gehost.  

-   **Naam sleutel:** DatabaseName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>  

    -   **Details:** Hiermee geeft u de naam van de SQL Server-database te maken of de SQL Server-database moet worden gebruikt bij het installeren van de database van centrale beheersite. De dezelfde databasenaam opgeven die werd gebruikt vóór de fout.  

        > [!IMPORTANT]  
        >  Als u het standaardexemplaar niet gebruikt, moet u de exemplaarnaam en de naam van de sitedatabase opgeven.  

-   **Naam sleutel:** SQLSSBPort  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Hiermee geeft u de SSB-poort die SQL Server gebruikt. SSB is standaard geconfigureerd voor het gebruik van TCP-poort 4022. Geef dezelfde SSB-poort die werd gebruikt vóór de fout.  

-   **Naam sleutel:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar MDB-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database mdb-bestand.  

-   **Naam sleutel:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar LDF-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**CloudConnectorOptions**  

-   **Naam sleutel:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of voor het installeren van een service connection point op deze site. Omdat het serviceverbindingspunt kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Naam sleutel:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Naam sleutel:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of het service connection point een proxyserver gebruikt.  

-   **Naam sleutel:** ProxyName  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*FQDN van proxyserver*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die gebruikmaakt van het serviceverbindingspunt wordt gehost.  

-   **Naam sleutel:** ProxyPort  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer dat moet worden gebruikt voor de proxypoort op.  

### <a name="unattended-recovery-for-a-primary-site"></a>Herstel voor een primaire site zonder toezicht  
 Gebruik de volgende informatie voor het herstellen van een primaire site met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Naam sleutel:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** <*RecoverPrimarySite*>  

    -   **Details:** Een primaire site herstelt.  

-   **Naam sleutel:** CDLatest  

    -   **Vereist:** Ja, alleen bij gebruik van media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media in een CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite herstelt. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.    

**RecoveryOptions**  

-   **Naam sleutel:** ServerRecoveryOptions  

    -   **Vereist:** Ja  

    -   **Waarden:** 1, 2 of 4  

         1 = siteserver herstellen en SQL Server.  

         2 = Alleen siteserver herstellen.  

         4 = Alleen SQL Server herstellen.  

    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide wordt hersteld. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instellen voor de **ServerRecoveryOptions** instelling:  

        -   Waarde = 1: U hebt de mogelijkheid om op te geven van een waarde op voor de **SiteServerBackupLocation** sleutel op de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 2: U hebt de mogelijkheid om op te geven van een waarde op voor de **SiteServerBackupLocation** sleutel op de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 4: De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

-   **Naam sleutel:** DatabaseRecoveryOptions  

    -   **Vereist:** Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.  

    -   **Waarden:** 10, 20, 40 of 80  

         10 = De sitedatabase uit de back-up herstellen.  

         20 = Gebruik een sitedatabase die handmatig wordt hersteld met behulp van een andere methode.  

         40 = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  

         80 = databaseherstel overslaan.  

    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door setup wordt hersteld.  

-   **Naam sleutel:** SiteServerBackupLocation  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar back-upset siteserver*>  

    -   **Details:**  

         Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

-   **Naam sleutel:** Back-uplocatie  

    -   **Vereist:** Deze sleutel is vereist bij het configureren van een waarde van **1** of **4** voor de **ServerRecoveryOptions** sleutel en een waarde van configureren **10** voor de **DatabaseRecoveryOptions** sleutel.  

    -   **Waarden:** <*pad naar back-upset van sitedatabase*>  

    -   **Details:** Hiermee geeft u het pad naar back-upset van de sitedatabase.  

**Opties**  

-   **Naam sleutel:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** *xxxxx-xxxxx-xxxxx-xxxxx-xxxxx* of *Eval*  

    -   **Details:** Hiermee geeft u de productcode voor de Configuration Manager de installatie, inclusief de streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Naam sleutel:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren. De sitecode opgeven die de site vóór de fout gebruikt.

-   **Naam sleutel:** SiteName  

    -   **Vereist:** Nee  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Geeft de naam voor deze site.  

-   **Naam sleutel:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad Configuration Manager*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Naam sleutel:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als host fungeert voor de SMS-Provider. Geef op de server die als host van de SMS-Provider voorafgaand aan de fout. Aanvullende SMS-Providers voor de site configureren na de eerste installatie. Zie voor meer informatie over de SMS-Provider [plannen voor de SMS-Provider](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Naam sleutel:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of setup vereiste bestanden al zijn gedownload. Als u een waarde van bijvoorbeeld **0**, setup de bestanden downloaden.  

-   **Naam sleutel:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor setup. Afhankelijk van de **PrerequisiteComp** waarde, gebruikt het installatieprogramma dit pad gedownloade bestanden wilt opslaan of vinden eerder gedownloade bestanden.  

-   **Naam sleutel:** AdminConsole  

    -   **Vereist:** Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of de Configuration Manager-console te installeren.  

-   **Naam sleutel:** JoinCEIP  
    > [!Note]  
    > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen geen lid worden van  

         1 = join  

    -   **Details:** Hiermee geeft u op of u deelneemt aan het programma voor Kwaliteitsverbetering.  

**SQLConfigOptions**  

-   **Naam sleutel:** SQLServerName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SQL-servernaam*>  

    -   **Details:** Geeft de naam van de server of het geclusterde exemplaar waarop SQL Server wordt uitgevoerd en die als host fungeert voor de sitedatabase. Geef op dezelfde server die de sitedatabase voorafgaand aan de fout wordt gehost.  

-   **Naam sleutel:** DatabaseName  

    -   **Vereist:** Ja  

    -   **Waarden:** <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>

    -   **Details:**  

         Hiermee geeft u de naam van de SQL Server-database te maken of de SQL Server-database moet worden gebruikt bij het installeren van de database van centrale beheersite. De dezelfde databasenaam opgeven die werd gebruikt vóór de fout.  

        > [!IMPORTANT]  
        >  Als u het standaardexemplaar niet gebruikt, moet u de exemplaarnaam en de naam van de sitedatabase opgeven.  

-   **Naam sleutel:** SQLSSBPort  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Hiermee geeft u de SSB-poort die SQL Server gebruikt. Doorgaans is SSB geconfigureerd voor gebruik van TCP-poort 4022. Geef dezelfde SSB-poort die werd gebruikt vóór de fout.  

-   **Naam sleutel:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar MDB-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database mdb-bestand.  

-   **Naam sleutel:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar LDF-bestand van database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**HierarchyExpansionOptions**  

-   **Naam sleutel:** CCARSiteServer  

    -   **Vereist:** Zie details.  

    -   **Waarden:** <*sitecode voor de centrale beheersite*>  

    -   **Details:** Hiermee geeft u de centrale beheersite op waaraan een primaire site wordt gekoppeld wanneer deze lid wordt van de Configuration Manager-hiërarchie. Deze instelling is vereist als de primaire site was gekoppeld aan een centrale beheersite vóór de fout. De sitecode opgeven die werd gebruikt voor de centrale beheersite vóór de fout.  

-   **Naam sleutel:** CASRetryInterval  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Interval*>  

    -   **Details:** Hiermee geeft u het interval (in minuten) waarna wordt geprobeerd een verbinding met de centrale beheersite nadat de verbinding is verbroken. Bijvoorbeeld, als de verbinding met de centrale beheersite mislukt, de primaire site wacht gedurende het aantal minuten dat u opgeeft voor de **CASRetryInterval** waarde en probeert het dan opnieuw de verbinding.  

-   **Naam sleutel:** WaitForCASTimeout  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Time-out*>  

    -   **Details:** Hiermee geeft u de maximum time-outwaarde (in minuten) voor een primaire site verbinding maken met de centrale beheersite. Bijvoorbeeld, als een primaire site geen verbinding maken met een centrale beheersite, de primaire site opnieuw de verbinding met de centrale beheersite op basis van de **CASRetryInterval** waarde totdat de **WaitForCASTimeout** periode is bereikt. U kunt een waarde opgeven van **0** naar **100**.  

**CloudConnectorOptions**  

-   **Naam sleutel:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of voor het installeren van een service connection point op deze site. Omdat het serviceverbindingspunt kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Naam sleutel:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Naam sleutel:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** 0 of 1  

         0 = geen niet installeren  

         1 = install  

    -   **Details:** Geeft aan of het service connection point een proxyserver gebruikt.  

-   **Naam sleutel:** ProxyName  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*FQDN van proxyserver*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die gebruikmaakt van het serviceverbindingspunt wordt gehost.  

-   **Naam sleutel:** ProxyPort  

    -   **Vereist:** Vereist wanneer **CloudConnector** gelijk is aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer dat moet worden gebruikt voor de proxypoort op.  
