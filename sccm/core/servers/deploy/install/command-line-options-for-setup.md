---
title: Opdrachtregelopties voor Setup | Microsoft-documenten
description: Gebruik de informatie in dit artikel scripts configureren of System Center Configuration Manager installeren vanaf een opdrachtregel te gebruiken.
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0da167f1-52cf-4dfd-8f73-833ca3eb8478
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 04fe7b3e674287c4255563ab4a308e54d0b6c3aa
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="command-line-options-for-setup-in-system-center-configuration-manager"></a>Opdrachtregelopties voor Setup in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Gebruik de volgende informatie voor het configureren van scripts of System Center Configuration Manager installeren vanaf een opdrachtregel te gebruiken.  

##  <a name="bkmk_setup"></a>Opdrachtregelopties voor Setup  
 **/ DEINSTALL**  
 Hiermee verwijdert u de site. U moet Setup uitvoeren vanaf de siteservercomputer.  

 **/ DONTSTARTSITECOMP**  
 Hiermee installeert u een site, maar voorkomt dat de service Site Component Manager wordt gestart. De site is pas actief nadat de service Site Component Manager is gestart. Site Component Manager is verantwoordelijk voor installeren en starten van de service SMS_Executive en aanvullende processen op de site. Nadat de installatie van de site is voltooid, wanneer u de service Site Component Manager start, installeert de SMS Executive-service en aanvullende processen die nodig zijn voor de werking van de site.  

 **/ VERBORGEN**  
 Hiermee verbergt de gebruikersinterface tijdens de installatie. Gebruik deze optie alleen in combinatie met de **/SCRIPT** optie. Het script zonder toezicht-bestand moet alle vereiste opties opgeven, anders mislukt Setup.  

 **/ NOUSERINPUT**  
 Gebruikersinvoer uitgeschakeld tijdens de installatie, maar de Wizard Setup wordt weergegeven. Gebruik deze optie alleen in combinatie met de **/SCRIPT** optie. Het script zonder toezicht-bestand moet alle vereiste opties opgeven, anders mislukt Setup.  

 **/ RESETSITE**  
 Voert een site opnieuw instellen die de database en serviceaccounts voor de site wordt opnieuw ingesteld. U moet Setup uitvoeren via  **<* installatiepad voor Configuration Manager*> \BIN\X64** op de siteserver. Zie voor meer informatie over het opnieuw instellen van de site de [een sitereset uitvoeren](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_reset) in sectie [wijzigen van de System Center Configuration Manager-infrastructuur](../../../../core/servers/manage/modify-your-infrastructure.md).  

 **/ TESTDBUPGRADE <*exemplaarnaam*>\\<*databasenaam*>**  
 Voert een test uit op een back-up van de sitedatabase om ervoor te zorgen dat de database geschikt is voor een upgrade is. U moet de instantienaam en databasenaam op voor de sitedatabase opgeven. Als u alleen de databasenaam opgeeft, gebruikt Setup de standaardinstantienaam.  

> [!IMPORTANT]  
>  Voer deze opdrachtregeloptie te gebruiken op uw productie-sitedatabase niet. Deze opdrachtregeloptie te gebruiken op uw productie-sitedatabase wordt uitgevoerd een upgrade van de sitedatabase en kan dat uw site onbruikbaar wordt.  

 **/ UPGRADE**  
 Voert een upgrade zonder toezicht van een site. Bij het gebruik van **/UPGRADE**, moet u de productcode, inclusief de liggende streepjes (-). Bovendien moet u het pad naar het eerder gedownloade vereiste bestanden voor Setup.  

 Voorbeeld: `setupwpf.exe /UPGRADE xxxxx-xxxxx-xxxxx-xxxxx-xxxxx <path to external component files>`  

 Zie voor meer informatie over voor Setup vereiste bestanden [Downloadprogramma](setup-downloader.md).  

 **/ SCRIPT <*pad naar Setup-script*>**  
 Installaties zonder toezicht uitvoert. Is een Setup-initialisatiebestand vereist wanneer u de **/SCRIPT** optie. Zie voor meer informatie over het uitvoeren van installaties zonder toezicht [sites via een opdrachtregel installeren](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).  

 **/ SDKINST <*FQDN-naam van de SMS-Provider*>**  
 De SMS-Provider wordt geïnstalleerd op de opgegeven computer. U moet de volledig gekwalificeerde domeinnaam (FQDN) voor de computer van de SMS-Provider opgeven. Zie voor meer informatie over de SMS-Provider [plannen voor de SMS-Provider voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

 **/ SDKDEINST <*FQDN-naam van de SMS-Provider*>**  
 Hiermee verwijdert u de SMS-Provider op de opgegeven computer. U moet de FQDN-naam opgeven voor de computer van de SMS-Provider.  

 **/ MANAGELANGS <*scriptpad taal*>**  
 Hiermee beheert u de talen die op een eerder geïnstalleerde site worden geïnstalleerd. Om deze optie gebruikt, u moet Setup uitvoeren via  **<* installatiepad voor Configuration Manager*> \BIN\X64** op de siteserver en de locatie opgeven voor het taalscriptbestand dat de taalinstelling bevat. Zie voor meer informatie over de beschikbare taalopties in het scriptbestand [opdrachtregelopties voor het beheren van talen](#bkmk_Lang) in dit onderwerp.  

##  <a name="bkmk_Lang"></a>Opdrachtregelopties voor het beheren van talen  
 **Identificatie**  

-   **Sleutelnaam:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** ManageLanguages  

    -   **Details:** Hiermee beheert u server-, client- en mobiele clienttaalondersteuning op een site.  

**Opties**  

-   **Sleutelnaam:** AddServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de servertalen die beschikbaar zijn voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar.  

-   **Sleutelnaam:** AddClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de talen die beschikbaar zijn voor clientcomputers. Engels is standaard beschikbaar.  

-   **Sleutelnaam:** DeleteServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Sleutelnaam:** DeleteClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar is voor clientcomputers. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Sleutelnaam:** MobileDeviceLanguage  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee geeft u op of de clienttalen van het mobiele apparaat zijn geïnstalleerd.  

-   **Sleutelnaam:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of Setup vereiste bestanden die reeds zijn gedownload. Bijvoorbeeld, als u een waarde van **0**, zal Setup de bestanden downloaden.  

-   **Sleutelnaam:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar Setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor Setup. Afhankelijk van de waarde van **PrerequisiteComp** gebruikt het installatieprogramma dit pad om de gedownloade bestanden op te slaan of om naar de eerder gedownloade bestanden te zoeken.  

##  <a name="bkmk_Unattended"></a>Bestand zonder toezicht installatiescriptsleutels  
 Gebruik de volgende secties voor hulp bij het maken van het script voor installatie zonder toezicht. De lijsten tonen de beschikbare installatiescriptsleutels, de overeenkomstige waarden, of ze zijn vereist, welk type installatie ze worden gebruikt voor en een korte beschrijving van de sleutel.  

### <a name="unattended-install-for-a-central-administration-site"></a>Installatie zonder toezicht voor een centrale beheersite  
 Gebruik de volgende informatie op een centrale beheersite installeren met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Sleutelnaam:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** InstallCAS  

    -   **Details:** Een centrale beheersite installeert.  

-   **Sleutelnaam:** CDLatest  

    -   **Vereist:** Ja – alleen als u media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media op CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite te herstellen. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**Opties**  

-   **Sleutelnaam:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *of* Eval  

    -   **Details:** Hiermee geeft u de Configuration Manager installatieproductcode, inclusief de liggende streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Sleutelnaam:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren.  

-   **Sleutelnaam:** Sitenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Hiermee geeft u de naam voor deze site.  

-   **Sleutelnaam:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad voor Configuration Manager*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Sleutelnaam:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als voor de SMS-Provider host fungeert. U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.  

-   **Sleutelnaam:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of Setup vereiste bestanden die reeds zijn gedownload. Bijvoorbeeld, als u een waarde van **0**, zal Setup de bestanden downloaden.  

-   **Sleutelnaam:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar Setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor Setup. Afhankelijk van de waarde van **PrerequisiteComp** gebruikt het installatieprogramma dit pad om de gedownloade bestanden op te slaan of om naar de eerder gedownloade bestanden te zoeken.  

-   **Sleutelnaam:** AdminConsole  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u de Configuration Manager-console te installeren.  

-   **Sleutelnaam:** JoinCEIP  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet deelnemen aan  

         1 = join  

    -   **Details:** Hiermee geeft u op of u zich aanmeldt klant ervaring Improvement Program (CEIP).  

-   **Sleutelnaam:** AddServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de servertalen die beschikbaar zijn voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar.  

-   **Sleutelnaam:** AddClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de talen die beschikbaar zijn voor clientcomputers. Engels is standaard beschikbaar.  

-   **Sleutelnaam:** DeleteServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Sleutelnaam:** DeleteClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar is voor clientcomputers. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Sleutelnaam:** MobileDeviceLanguage  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee geeft u op of de clienttalen van het mobiele apparaat zijn geïnstalleerd.  

**SQLConfigOptions**  

-   **Sleutelnaam:** SQL Server-naam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*naam van SQL server*>  

    -   **Details:** Hiermee geeft u de naam van de server of de geclusterde instantie die SQL Server wordt uitgevoerd en die fungeert als host voor de sitedatabase.  

-   **Sleutelnaam:** Databasenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>  

    -   **Details:** Hiermee geeft u de naam van de SQL Server-database maken of de SQL Server-database moet worden gebruikt bij de installatie van de database van de centrale beheersite.  

        > [!IMPORTANT]  
        >  U moet de naam van het exemplaar en de naam van de sitedatabase opgeven als u het standaardexemplaar niet gebruikt.  

-   **Sleutelnaam:** SQLSSBPort  

    -   **Vereist:** Nee  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Geeft de poort voor SQL Server Service Broker (SSB) die SQL Server gebruikt. SSB is standaard geconfigureerd voor gebruik van TCP-poort 4022, maar u kunt een andere poort.  

-   **Sleutelnaam:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar .mdb voor database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie om de database .mdb-bestand te maken.  

-   **Sleutelnaam:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar de database LDF-bestand*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**CloudConnectorOptions**  

-   **Sleutelnaam:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u een service connection point op deze site installeren. Omdat de service connection point kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Sleutelnaam:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Sleutelnaam:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee geeft u op of de service connection point een proxyserver gebruiken.  

-   **Sleutelnaam:** ProxyName  

    -   **Vereist:** Vereist wanneer **UseProxy** is gelijk aan 1  

    -   **Waarden:** <*FQDN-naam van de Proxy-server*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die wordt gebruikt door de service connection point-sitesysteemrol.  

-   **Sleutelnaam:** ProxyPort  

    -   **Vereist:** Vereist wanneer **UseProxy** is gelijk aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer moet worden gebruikt voor de proxyserver-poort.  

### <a name="unattended-install-for-a-primary-site"></a>Installatie zonder toezicht voor een primaire site  
Gebruik de volgende informatie voor het installeren van een primaire site met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Sleutelnaam:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** InstallPrimarySite  

    -   **Details:** Een primaire site installeert.  

-   **Sleutelnaam:** CDLatest  

    -   **Vereist:** Ja – alleen als u media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media op CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite te herstellen. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**Opties**  

-   **Sleutelnaam:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *of* Eval  

    -   **Details:** Hiermee geeft u de Configuration Manager installatieproductcode, inclusief de liggende streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Sleutelnaam:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren.  

-   **Sleutelnaam:** Sitenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Hiermee geeft u de naam voor deze site.  

-   **Sleutelnaam:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad voor Configuration Manager*>

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Sleutelnaam:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als voor de SMS-Provider host fungeert. U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.  

-   **Sleutelnaam:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of Setup vereiste bestanden die reeds zijn gedownload. Bijvoorbeeld, als u een waarde van **0**, zal Setup de bestanden downloaden.  

-   **Sleutelnaam:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar Setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor Setup. Afhankelijk van de waarde van **PrerequisiteComp** gebruikt het installatieprogramma dit pad om de gedownloade bestanden op te slaan of om naar de eerder gedownloade bestanden te zoeken.  

-   **Sleutelnaam:** AdminConsole  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u de Configuration Manager-console te installeren.  

-   **Sleutelnaam:** JoinCEIP  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet deelnemen aan  

         1 = join  

    -   **Details:** Hiermee geeft u op of u wilt deelnemen aan het programma voor Kwaliteitsverbetering.  

-   **Sleutelnaam:** ManagementPoint  

    -   **Vereist:** Nee  

    -   **Waarden:** <*beheerpunt FQDN-naam siteserver*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de sitesysteemrol management host fungeert.  

-   **Sleutelnaam:** ManagementPointProtocol  

    -   **Vereist:** Nee  

    -   **Waarden:** HTTPS *of* HTTP  

    -   **Details:** Hiermee geeft u het protocol moet worden gebruikt voor het beheerpunt.  

-   **Sleutelnaam:** DistributionPoint  

    -   **Vereist:** Nee  

    -   **Waarden:** <*site distributiepuntserver FQDN-naam*>  

    -   **Details:** Hiermee geeft u het protocol te gebruiken voor het distributiepunt.  

-   **Sleutelnaam:** DistributionPointProtocol  

    -   **Vereist:** Nee  

    -   **Waarden:** HTTPS *of* HTTP  

    -   **Details:** Hiermee geeft u het protocol te gebruiken voor het distributiepunt.  

-   **Sleutelnaam:** RoleCommunicationProtocol  

    -   **Vereist:** Ja  

    -   **Waarden:** EnforceHTTPS *of* HTTPorHTTPS  

    -   **Details:** Geeft aan of alle sitesystemen zo accepteren alleen HTTPS-communicatie van clients, of de communicatiemethode voor elke sitesysteemrol moet worden geconfigureerd. Als u inschakelt om **EnforceHTTPS**, moet de clientcomputer een geldige openbare-sleutelinfrastructuur (PKI)-certificaat voor clientverificatie hebben.  

-   **Sleutelnaam:** ClientsUsePKICertificate  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet gebruiken  

         1 = gebruiken  

    -   **Details:** Hiermee geeft u op of clients een PKI-certificaat gebruiken om te communiceren met sitesysteemrollen.  

-   **Sleutelnaam:** AddServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de servertalen die beschikbaar zijn voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar.  

-   **Sleutelnaam:** AddClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee geeft u de talen die beschikbaar zijn voor clientcomputers. Engels is standaard beschikbaar.  

-   **Sleutelnaam:** DeleteServerLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar voor de Configuration Manager-console, rapporten en Configuration Manager-objecten. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Sleutelnaam:** DeleteClientLanguages  

    -   **Vereist:** Nee  

    -   **Waarden:** DUI, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HON, ITA, KOR, NLD, PLK, PTB, PTG, ZWE, TRK, of ZHH  

    -   **Details:** Hiermee wijzigt een site nadat deze is geïnstalleerd. Hiermee geeft u de te verwijderen talen en die niet langer beschikbaar is voor clientcomputers. Engels is standaard beschikbaar en kan niet worden verwijderd.  

-   **Sleutelnaam:** MobileDeviceLanguage  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee geeft u op of de clienttalen van het mobiele apparaat zijn geïnstalleerd.  

**SQLConfigOptions**  

-   **Sleutelnaam:** SQL Server-naam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*naam van SQL server*>  

    -   **Details:** Hiermee geeft u de naam van de server of de geclusterde instantie die SQL Server wordt uitgevoerd en die fungeert als host voor de sitedatabase.  

-   **Sleutelnaam:** Databasenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>  

    -   **Details:** Hiermee geeft u de naam van de SQL Server-database maken of de SQL Server-database moet worden gebruikt bij de installatie van de primaire sitedatabase.  

        > [!IMPORTANT]  
        >  U moet de naam van het exemplaar en de naam van de sitedatabase opgeven als u het standaardexemplaar niet gebruikt.  

-   **Sleutelnaam:** SQLSSBPort  

    -   **Vereist:** Nee  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Hiermee geeft u de SSB-poort die de SQL Server gebruikt. SSB is standaard geconfigureerd voor gebruik van TCP-poort 4022, maar u kunt een andere poort.  

-   **Sleutelnaam:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar .mdb voor database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie om de database .mdb-bestand te maken.  

-   **Sleutelnaam:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar de database LDF-bestand*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**HierarchyExpansionOption**  

-   **Sleutelnaam:** CCARSiteServer  

    -   **Vereist:** Nee  

    -   **Waarden:** <*centrale beheersite FQDN-naam*>  

    -   **Details:** Hiermee geeft u de centrale beheersite waarmee een primaire site zal worden gekoppeld wanneer het lid van de Configuration Manager-hiërarchie. Tijdens de installatie moet u de centrale beheersite.  

-   **Sleutelnaam:** CASRetryInterval  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Interval*>  

    -   **Details:** Hiermee geeft u het interval (in minuten) om een verbinding met de centrale beheersite nadat de verbinding is mislukt. Bijvoorbeeld, als de verbinding met de centrale beheersite mislukt, de primaire site wacht gedurende het aantal minuten dat u opgeeft voor de **CASRetryInterval** waarde en probeert het dan opnieuw de verbinding.  

-   **Sleutelnaam:** WaitForCASTimeout  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Time-out*>  

         Een waarde van **0** naar **100**  

    -   **Details:** Hiermee geeft u het maximum time-outwaarde (in minuten) voor een primaire site verbinding maken met de centrale beheersite. Bijvoorbeeld, als een primaire site geen verbinding maken met een centrale beheersite, probeert de primaire site de verbinding met de centrale beheersite op basis van de **CASRetryInterval** waarde pas de **WaitForCASTimeout** periode is bereikt. U kunt een waarde opgeven van **0** naar **100**.  

**CloudConnectorOptions**  

-   **Sleutelnaam:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u een service connection point op deze site installeren. Omdat de service connection point kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Sleutelnaam:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*\>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Sleutelnaam:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee geeft u op of de service connection point een proxyserver gebruiken.  

-   **Sleutelnaam:** ProxyName  

    -   **Vereist:** Vereist wanneer **UseProxy** is gelijk aan 1  

    -   **Waarden:** <*FQDN-naam van de Proxy-server*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die wordt gebruikt door de service connection point-sitesysteemrol.  

-   **Sleutelnaam:** ProxyPort  

    -   **Vereist:** Vereist wanneer **UseProxy** is gelijk aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer moet worden gebruikt voor de proxyserver-poort.  

### <a name="unattended-recovery-for-a-central-administration-site"></a>Herstel voor een centrale beheersite zonder toezicht  
 Gebruik de volgende informatie op een centrale beheersite herstellen met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Sleutelnaam:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** RecoverCCAR  

    -   **Details:** Herstelt een centrale beheersite.  

-   **Sleutelnaam:** CDLatest  

    -   **Vereist:** Ja – alleen als u media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media op CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite te herstellen. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**RecoveryOptions**  

-   **Sleutelnaam:** ServerRecoveryOptions  

    -   **Vereist:** Ja  

    -   **Waarden:** 1, 2 of 4  

         1 = siteserver herstellen en SQL Server.  

         2 = Alleen siteserver herstellen.  

         4 = Alleen SQL Server herstellen.  

    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide zal herstellen. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instellen voor de **ServerRecoveryOptions** instelling:  

        -   Waarde = 1: U hebt de mogelijkheid om op te geven van een waarde voor de **SiteServerBackupLocation** sleutel voor het herstellen van de site met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 2: U hebt de mogelijkheid om op te geven van een waarde voor de **SiteServerBackupLocation** sleutel voor het herstellen van de site met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 4: De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

-   **Sleutelnaam:** DatabaseRecoveryOptions  

    -   **Vereist:** Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.  

    -   **Waarden:** 10, 20, 40 of 80  

         10 = De sitedatabase uit de back-up herstellen.  

         20 = Gebruik een sitedatabase die handmatig wordt hersteld met behulp van een andere methode.  

         40 = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  

         80 = databaseherstel overslaan.  

    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door Setup wordt hersteld.  

-   **Sleutelnaam:** ReferenceSite  

    -   **Vereist:** Deze sleutel is vereist wanneer de instelling **DatabaseRecoveryOptions** een waarde heeft van **40**.  

    -   **Waarden:** <*referentiesite FQDN-naam*>  

    -   **Details:** Hiermee geeft u de primaire site die de centrale beheersite gebruikt voor het herstellen van globale gegevens als de databaseback-up ouder dan de bewaarperiode bijhouden is of wanneer u een site zonder een back-up herstelt.  

         Wanneer u geen referentiesite opgeeft en de back-up ouder dan de bewaarperiode bijhouden is, worden alle primaire sites opnieuw geïnitialiseerd met de herstelde gegevens van de centrale beheersite.  

         Wanneer u geen referentiesite opgeeft en de back-up valt binnen de bewaarperiode bijhouden, alleen de wijzigingen die zijn aangebracht nadat de back-up worden gerepliceerd van primaire sites. Wanneer er conflicterende wijzigingen van verschillende primaire sites zijn, gebruikt de centrale beheersite de eerste die het ontvangt.  

-   **Sleutelnaam:** SiteServerBackupLocation  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar back-upset van de siteserver*>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

-   **Sleutelnaam:** Back-uplocatie  

    -   **Vereist:** Deze sleutel is vereist bij het configureren van een waarde van **1** of **4** voor de **ServerRecoveryOptions** sleutel en kunt u een waarde van configureert **10** voor de **DatabaseRecoveryOptions** sleutel.  

    -   **Waarden:** <*pad naar back-upset van de sitedatabase*>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de sitedatabase.  

**Opties**  

-   **Sleutelnaam:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *of* Eval  

    -   **Details:** Hiermee geeft u de Configuration Manager installatieproductcode, inclusief de liggende streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Sleutelnaam:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren. U moet de sitecode opgeven die site voordat deze uitviel gebruikte.

-   **Sleutelnaam:** Sitenaam  

    -   **Vereist:** Nee  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Hiermee geeft u de naam voor deze site.  

-   **Sleutelnaam:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad voor Configuration Manager*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Sleutelnaam:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als voor de SMS-Provider host fungeert. U moet de server opgeven die als host optrad voor de SMS-provider voorafgaand aan de fout.  

         U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie. Zie voor meer informatie over de SMS-Provider [plannen voor de SMS-Provider voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Sleutelnaam:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of Setup vereiste bestanden die reeds zijn gedownload. Bijvoorbeeld, als u een waarde van **0**, zal Setup de bestanden downloaden.  

-   **Sleutelnaam:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar Setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor Setup. Afhankelijk van de waarde van **PrerequisiteComp** gebruikt het installatieprogramma dit pad om de gedownloade bestanden op te slaan of om naar de eerder gedownloade bestanden te zoeken.  

-   **Sleutelnaam:** AdminConsole  

    -   **Vereist:** Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u de Configuration Manager-console te installeren.  

-   **Sleutelnaam:** JoinCEIP  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet deelnemen aan  

         1 = join  

    -   **Details:** Hiermee geeft u op of u wilt deelnemen aan het programma voor Kwaliteitsverbetering.  

**SQLConfigOptions**  

-   **Sleutelnaam:** SQL Server-naam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*naam van SQL server*>  

    -   **Details:** Hiermee geeft u de naam van de server of de geclusterde instantie die SQL Server wordt uitgevoerd en die fungeert als host voor de sitedatabase. U moet dezelfde server opgeven die als host optrad voor de sitedatabase voorafgaand aan de fout.  

-   **Sleutelnaam:** Databasenaam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>  

    -   **Details:** Hiermee geeft u de naam van de SQL Server-database maken of de SQL Server-database moet worden gebruikt bij de installatie van de database van de centrale beheersite. U moet dezelfde databasenaam opgeven die werd gebruikt voorafgaand aan de fout.  

        > [!IMPORTANT]  
        >  U moet de naam van het exemplaar en de naam van de sitedatabase opgeven als u het standaardexemplaar niet gebruikt.  

-   **Sleutelnaam:** SQLSSBPort  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Hiermee geeft u de SSB-poort die de SQL Server gebruikt. SSB is standaard geconfigureerd voor gebruik van TCP-poort 4022. U moet dezelfde SSB-poort opgeven die werd gebruikt vóór de fout.  

-   **Sleutelnaam:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar .mdb voor database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie om de database .mdb-bestand te maken.  

-   **Sleutelnaam:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar de database LDF-bestand*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**CloudConnectorOptions**  

-   **Sleutelnaam:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u een service connection point op deze site installeren. Omdat de service connection point kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Sleutelnaam:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Sleutelnaam:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee geeft u op of de service connection point een proxyserver gebruiken.  

-   **Sleutelnaam:** ProxyName  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*FQDN-naam van de Proxy-server*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die wordt gebruikt door de service connection point-sitesysteemrol.  

-   **Sleutelnaam:** ProxyPort  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer moet worden gebruikt voor de proxyserver-poort.  

### <a name="unattended-recovery-for-a-primary-site"></a>Herstel voor een primaire site zonder toezicht  
 Gebruik de volgende informatie voor het herstellen van een primaire site met behulp van een scriptbestand voor installatie zonder toezicht.  

**Identificatie**  

-   **Sleutelnaam:** Actie  

    -   **Vereist:** Ja  

    -   **Waarden:** <*RecoverPrimarySite*>  

    -   **Details:** Een primaire site herstelt.  

-   **Sleutelnaam:** CDLatest  

    -   **Vereist:** Ja – alleen als u media vanaf de CD. Meest recente map.    

    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.

    -   **Details:** Wanneer u setup vanaf media op CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite te herstellen. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.    

**RecoveryOptions**  

-   **Sleutelnaam:** ServerRecoveryOptions  

    -   **Vereist:** Ja  

    -   **Waarden:** 1, 2 of 4  

         1 = siteserver herstellen en SQL Server.  

         2 = Alleen siteserver herstellen.  

         4 = Alleen SQL Server herstellen.  

    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide zal herstellen. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instellen voor de **ServerRecoveryOptions** instelling:  

        -   Waarde = 1: U hebt de mogelijkheid om op te geven van een waarde voor de **SiteServerBackupLocation** sleutel voor het herstellen van de site met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 2: U hebt de mogelijkheid om op te geven van een waarde voor de **SiteServerBackupLocation** sleutel voor het herstellen van de site met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

        -   Waarde = 4: De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.  

-   **Sleutelnaam:** DatabaseRecoveryOptions  

    -   **Vereist:** Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.  

    -   **Waarden:** 10, 20, 40 of 80  

         10 = De sitedatabase uit de back-up herstellen.  

         20 = Gebruik een sitedatabase die handmatig wordt hersteld met behulp van een andere methode.  

         40 = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  

         80 = databaseherstel overslaan.  

    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door Setup wordt hersteld.  

-   **Sleutelnaam:** SiteServerBackupLocation  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar back-upset van de siteserver*>  

    -   **Details:**  

         Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.  

-   **Sleutelnaam:** Back-uplocatie  

    -   **Vereist:** Deze sleutel is vereist bij het configureren van een waarde van **1** of **4** voor de **ServerRecoveryOptions** sleutel en configureert u een waarde van **10** voor de **DatabaseRecoveryOptions** sleutel.  

    -   **Waarden:** <*pad naar back-upset van de sitedatabase*>  

    -   **Details:** Hiermee geeft u het pad naar de back-upset van de sitedatabase.  

**Opties**  

-   **Sleutelnaam:** Product-id  

    -   **Vereist:** Ja  

    -   **Waarden:** *xxxxx-xxxxx-xxxxx-xxxxx-xxxxx* of *Eval*  

    -   **Details:** Hiermee geeft u de Configuration Manager installatieproductcode, inclusief de liggende streepjes. Voer **Eval** om de evaluatieversie van Configuration Manager te installeren.  

-   **Sleutelnaam:** SiteCode  

    -   **Vereist:** Ja  

    -   **Waarden:** <*sitecode*>  

    -   **Details:** Hiermee geeft u drie alfanumerieke tekens die de site in uw hiërarchie identificeren. U moet de sitecode opgeven die site voordat deze uitviel gebruikte.

-   **Sleutelnaam:** Sitenaam  

    -   **Vereist:** Nee  

    -   **Waarden:** <*sitenaam*>  

    -   **Details:** Hiermee geeft u de naam voor deze site.  

-   **Sleutelnaam:** SMSInstallDir  

    -   **Vereist:** Ja  

    -   **Waarden:** <*installatiepad voor Configuration Manager*>  

    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.  

-   **Sleutelnaam:** SDKServer  

    -   **Vereist:** Ja  

    -   **Waarden:** <*FQDN-naam van de SMS-Provider*>  

    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als voor de SMS-Provider host fungeert. U moet de server opgeven die als host optrad voor de SMS-provider voorafgaand aan de fout. U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie. Zie voor meer informatie over de SMS-Provider [plannen voor de SMS-Provider voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Sleutelnaam:** PrerequisiteComp  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = downloaden  

         1 = reeds gedownload  

    -   **Details:** Hiermee geeft u op of Setup vereiste bestanden die reeds zijn gedownload. Bijvoorbeeld, als u een waarde van **0**, zal Setup de bestanden downloaden.  

-   **Sleutelnaam:** PrerequisitePath  

    -   **Vereist:** Ja  

    -   **Waarden:** <*pad naar Setup vereiste bestanden*>  

    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor Setup. Afhankelijk van de waarde van **PrerequisiteComp** gebruikt het installatieprogramma dit pad om de gedownloade bestanden op te slaan of om naar de eerder gedownloade bestanden te zoeken.  

-   **Sleutelnaam:** AdminConsole  

    -   **Vereist:** Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u de Configuration Manager-console te installeren.  

-   **Sleutelnaam:** JoinCEIP  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet deelnemen aan  

         1 = join  

    -   **Details:** Hiermee geeft u op of u wilt deelnemen aan het programma voor Kwaliteitsverbetering.  

**SQLConfigOptions**  

-   **Sleutelnaam:** SQL Server-naam  

    -   **Vereist:** Ja  

    -   **Waarden:** <*naam van SQL server*>  

    -   **Details:** Hiermee geeft u de naam van de server of de geclusterde instantie die SQL Server wordt uitgevoerd en die fungeert als host voor de sitedatabase. U moet dezelfde server opgeven die als host optrad voor de sitedatabase voorafgaand aan de fout.  

-   **Sleutelnaam:** Databasenaam  

    -   **Vereist:** Ja  

    -   **Waarden:**  <*Sitedatabasenaam*> of <*exemplaarnaam*>\\<*naam van de sitedatabase*>

    -   **Details:**  

         Hiermee geeft u de naam van de SQL Server-database maken of de SQL Server-database moet worden gebruikt bij de installatie van de database van de centrale beheersite. U moet dezelfde databasenaam opgeven die werd gebruikt voorafgaand aan de fout.  

        > [!IMPORTANT]  
        >  U moet de naam van het exemplaar en de naam van de sitedatabase opgeven als u het standaardexemplaar niet gebruikt.  

-   **Sleutelnaam:** SQLSSBPort  

    -   **Vereist:** Ja  

    -   **Waarden:** <*SSB-poortnummer*>  

    -   **Details:** Hiermee geeft u de SSB-poort die de SQL Server gebruikt. SSB is standaard geconfigureerd voor het gebruik van TCP-poort 4022. U moet dezelfde SSB-poort opgeven die werd gebruikt vóór de fout.  

-   **Sleutelnaam:** SQLDataFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar .mdb voor database*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie om de database .mdb-bestand te maken.  

-   **Sleutelnaam:** SQLLogFilePath  

    -   **Vereist:** Nee  

    -   **Waarden:** <*pad naar de database LDF-bestand*>  

    -   **Details:** Hiermee geeft u een alternatieve locatie voor het maken van de database LDF-bestand.  

**HierarchyExpansionOptions**  

-   **Sleutelnaam:** CCARSiteServer  

    -   **Vereist:** Zie de details.  

    -   **Waarden:** <*sitecode voor de centrale beheersite*>  

    -   **Details:** Hiermee geeft u de centrale beheersite op waaraan een primaire site wordt gekoppeld wanneer het lid van de Configuration Manager-hiërarchie. Deze instelling is vereist als de primaire site was gekoppeld aan een centrale beheersite vóór de fout. U moet de sitecode opgeven die werd gebruikt door de centrale beheersite vóór de fout.  

-   **Sleutelnaam:** CASRetryInterval  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Interval*>  

    -   **Details:** Hiermee geeft u het interval (in minuten) om een verbinding met de centrale beheersite nadat de verbinding is mislukt. Bijvoorbeeld, als de verbinding met de centrale beheersite mislukt, de primaire site wacht gedurende het aantal minuten dat u opgeeft voor de **CASRetryInterval** waarde en probeert het dan opnieuw de verbinding.  

-   **Sleutelnaam:** WaitForCASTimeout  

    -   **Vereist:** Nee  

    -   **Waarden:** <*Time-out*>  

    -   **Details:** Hiermee geeft u het maximum time-outwaarde (in minuten) voor een primaire site verbinding maken met de centrale beheersite. Bijvoorbeeld, als een primaire site geen verbinding maken met een centrale beheersite, probeert de primaire site de verbinding met de centrale beheersite op basis van de **CASRetryInterval** waarde pas de **WaitForCASTimeout** periode is bereikt. U kunt een waarde opgeven van **0** naar **100**.  

**CloudConnectorOptions**  

-   **Sleutelnaam:** CloudConnector  

    -   **Vereist:** Ja  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee kunt u een service connection point op deze site installeren. Omdat de service connection point kan alleen worden geïnstalleerd op de bovenste site van een hiërarchie, moet deze waarde **0** voor een onderliggende primaire site.  

-   **Sleutelnaam:** CloudConnectorServer  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*Service connection point-server FQDN-naam*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de server die als voor de service connection point-sitesysteemrol host fungeert.  

-   **Sleutelnaam:** UseProxy  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** 0 of 1  

         0 = komen niet installeren  

         1 = installeren  

    -   **Details:** Hiermee geeft u op of de service connection point een proxyserver gebruiken.  

-   **Sleutelnaam:** ProxyName  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*FQDN-naam van de Proxy-server*>  

    -   **Details:** Hiermee geeft u de FQDN-naam van de proxyserver die wordt gebruikt door de service connection point-sitesysteemrol.  

-   **Sleutelnaam:** ProxyPort  

    -   **Vereist:** Vereist wanneer **CloudConnector** is gelijk aan 1  

    -   **Waarden:** <*poortnummer*>  

    -   **Details:** Hiermee geeft u het poortnummer moet worden gebruikt voor de proxyserver-poort.  

