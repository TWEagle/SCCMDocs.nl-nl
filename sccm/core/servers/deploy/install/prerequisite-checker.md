---
title: Prerequisite Checker | Microsoft-documenten
description: Leer hoe u Prerequisite Checker gebruiken om te identificeren en oplossen van problemen die mogelijk een site of de rol sitesysteeminstallatie blokkeren.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf13bb8-4ba2-4bd7-9fac-d36a9d88a1b6
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5cc318eaf097cb3cfbfde730f7573d27af25648
ms.openlocfilehash: f0d44f82a0b6068f8cecc5808774677eccb0f8d9
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="prerequisite-checker-for-system-center-configuration-manager"></a>Vereistencontrole voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Voordat u Setup uitvoeren om te installeren of upgraden van een System Center Configuration Manager-site of voordat u een sitesysteemrol op een nieuwe server installeert, kunt u deze zelfstandige toepassing gebruiken (**Prereqchk.exe**) van de versie van Configuration Manager die u wilt gebruiken om te controleren of de gereedheid van de server. Prerequisite Checker gebruiken om te identificeren en oplossen van problemen die een site of de installatie van het sitesysteem rol wilt blokkeren.  

> [!NOTE]  
>  Prerequisite Checker wordt altijd uitgevoerd als onderdeel van de installatie.  

Standaard, wanneer de Prerequisite Checker uitgevoerd:  

-   Hiermee wordt gevalideerd de server waarop hij wordt uitgevoerd.  
-   De lokale computer gescand naar een bestaande siteserver en alleen de controles die van toepassing op de site zijn worden uitgevoerd.  
-   Alle vereiste regels worden uitgevoerd als er geen bestaande sites worden gedetecteerd.  
-   Regels om te controleren die software wordt gecontroleerd en instellingen die vereist zijn voor de installatie zijn geïnstalleerd. Het is mogelijk dat de vereiste software nodig aanvullende configuratie of software-updates die niet worden gecontroleerd door de Prerequisite Checker.  
-   Registreert hij de resultaten de **ConfigMgrPrereq.log** -bestand op het systeemstation van de computer. Het logboekbestand kan aanvullende informatie bevatten die niet wordt weergegeven in de toepassingsinterface van.  

Wanneer u Prerequisite Checker uitvoeren aan een opdrachtprompt en specifieke opdrachtregelopties opgeven:  

-   Prerequisite Checker voert alleen de controles die zijn gekoppeld aan de siteserver of sitesystemen die u in de opdrachtregel opgeeft.  
-   Om te controleren of een externe computer, moet uw gebruikersaccount de rol Administrator-rechten op de externe computer hebben.  

Zie voor meer informatie over de controles die Prerequisite Checker uitvoert, [lijst met vereiste controles voor System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

## <a name="copy-prerequisite-checker-files-to-another-computer"></a>Prerequisite Checker-bestanden kopiëren naar een andere computer  

1.  Ga in Windows Verkenner naar een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Installatiepad voor Configuration Manager*\>\BIN\X64**  

2.  Kopieer de volgende bestanden naar de doelmap op de andere computer:  

    -   Prereqchk.exe  
    -   Prereqcore.dll  
    -   Basesql.dll  
    -   Basesvr.dll  
    -   Baseutil.dll  

##  <a name="run-prerequisite-checker-with-default-checks"></a>Prerequisite Checker met standaardcontroles uitvoeren  

1.  Ga in Windows Verkenner naar een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Installatiepad voor Configuration Manager*\>\BIN\X64**  

2.  Voer **prereqchk.exe** om Prerequisite Checker te starten.   
    Prerequisite Checker detecteert bestaande sites en, indien gevonden, controleert er de gereedheid voor een upgrade. Als er geen sites worden gevonden, worden alle controles uitgevoerd. De **Sitetype** kolom bevat informatie over de siteserver of sitesysteem waaraan de regel gekoppeld is.  

##  <a name="run-prerequisite-checker-from-a-command-prompt-for-all-default-checks"></a>Prerequisite Checker uitvoeren vanaf een opdrachtprompt voor alle standaardcontroles  

1.  Open een opdrachtpromptvenster en wijzig de mappen in een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Installatiepad voor Configuration Manager*\>\BIN\X64**  

2.  Voer **prereqchk.exe/Local** Prerequisite Checker starten en alle vereiste controles op de server uit te voeren.  

## <a name="run-prerequisite-checker-from-a-command-prompt-to-use-options"></a>Prerequisite Checker uitvoeren vanaf een opdrachtprompt te gebruiken opties  

1.  Open een opdrachtpromptvenster en wijzig de mappen in een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Installatiepad voor Configuration Manager*\>\BIN\X64**  

2.  Voer **prereqchk.exe** door het toevoegen van een of meer van de volgende opdrachtregelopties.  

    Bijvoorbeeld, om te controleren of een primaire site, kunt u het volgende:  

       **prereqchk.exe [/ noui gebruikt] / PRI /SQL &lt;FQDN-naam van SQL Server\> /SDK &lt;FQDN-naam van de SMS-Provider\> [/ deelnemen aan &lt;FQDN-naam van de centrale beheersite\>] [/MP &lt;FQDN-naam van het beheerpunt\>] [/DP &lt;FQDN-naam van distributiepunt\>]**  

    **Server centrale beheersite:**  

    -   **/ NOUI**  

         Niet vereist. Start de Prerequisite Checker zonder de gebruikersinterface weer te geven. U moet deze optie als eerste een andere optie in de opdrachtregel opgeven.  

    -   **/ CA 'S**  

         Vereist. Hiermee wordt gecontroleerd of de lokale computer voldoet aan de vereisten voor de centrale beheersite.  

    -   **/ SQL &lt;* FQDN-naam van SQL Server*>**  

         Vereist. Met behulp van de volledig gekwalificeerde domeinnaam (FQDN), wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor SQL Server om de Configuration Manager-sitedatabase te hosten.  

    -   **/ SDK &lt;* FQDN-naam van de SMS-Provider*>**  

         Vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de SMS-Provider.  

    -   **/ Ssbport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor de communicatie via de poort voor SQL Server Service Broker (SSB). De standaard SSB-poort is 4022.  

    -   **InstallDir &lt;* installatiepad voor Configuration Manager*>**  

         Niet vereist. Controleert of de minimale hoeveelheid schijfruimte voor site-installatie.  

    **Primaire siteserver:**  

    -   **/ NOUI**  

        Niet vereist. Start de Prerequisite Checker zonder de gebruikersinterface weer te geven. U moet deze optie als eerste een andere optie in de opdrachtregel opgeven.  

    -   **/ PRI**  

         Vereist. Verifieert of de lokale computer voldoet aan de vereisten voor de primaire site.  

    -   **/ SQL &lt;* FQDN-naam van SQL Server*>**  

         Vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor SQL Server om de Configuration Manager-sitedatabase te hosten.  

    -   **/ SDK &lt;* FQDN-naam van de SMS-Provider*>**  

         Vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de SMS-Provider.  

    -   **/ Deelnemen aan &lt;* FQDN-naam van de centrale beheersite*>**  

         Niet vereist. Hiermee wordt gecontroleerd of de lokale computer voldoet aan de vereisten voor het verbinden met de server van centrale beheersite.  

    -   **/MP &lt;* FQDN-naam van het beheerpunt*>**  

         Niet vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de sitesysteemrol management. Deze optie wordt alleen ondersteund wanneer u de **/PRI** optie.  

    -   **/DP &lt;* FQDN-naam van distributiepunt*>**  

         Niet vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de sitesysteemrol van distributiepunt punt. Deze optie wordt alleen ondersteund wanneer u de **/PRI** optie.  

    -   **/ Ssbport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor de communicatie via de SSB-poort. De standaard SSB-poort is 4022.  

    -   **InstallDir &lt;* installatiepad voor Configuration Manager*>**  

         Niet vereist. Controleert of de minimale hoeveelheid schijfruimte voor site-installatie.  

    **Secundaire siteserver:**  

    -   **/ NOUI**  

         Niet vereist. Start de Prerequisite Checker zonder de gebruikersinterface weer te geven. U moet deze optie als eerste een andere optie in de opdrachtregel opgeven.  

    -   **/ SEC &lt;* FQDN-naam van de secundaire siteserver*>**  

         Vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de secundaire site.  

    -   **/ INSTALLSQLEXPRESS**  

         Niet vereist. Verifieert dat SQL Server Express kan worden geïnstalleerd op de opgegeven computer.  

    -   **/ Ssbport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor de communicatie voor de SSB-poort. De standaard SSB-poort is 4022.  

    -   **/ Sqlport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor communicatie voor de SQL Server-servicepoort en de poort is niet in gebruik door het benoemde exemplaar van SQL Server. De standaardpoort is 1433.  

    -   **InstallDir &lt;* installatiepad voor Configuration Manager*>**  

         Niet vereist. Controleert of de minimale hoeveelheid schijfruimte voor site-installatie.  

    -   **/ SourceDir**  

         Niet vereist. Hiermee wordt gecontroleerd of het computeraccount van de secundaire site toegang hebt tot de map die als host fungeert voor de bronbestanden voor installatie.  

   **Configuration Manager-console:**  

    -   **/ Adminui**  

         Vereist. Verifieert of de lokale computer voldoet aan de vereisten voor het installeren van Configuration Manager.  

3.  In de gebruikersinterface van de Prerequisite Checker Prerequisite Checker maakt een lijst met gedetecteerde problemen in de **vereistenresultaat** sectie.  

    -   Klik op een item in de lijst voor meer informatie over het oplossen van het probleem.  
    -   U moet alle items in de lijst met oplossen een **fout** status voordat u de siteserver, sitesysteem of Configuration Manager-console installeert.  
    -   U kunt ook openen de **ConfigMgrPrereq.log** bestand in de hoofdmap van het systeemstation van de resultaten van de Prerequisite Checker bekijken. Het logboekbestand kan aanvullende informatie bevatten die niet wordt weergegeven in de gebruikersinterface van de Prerequisite Checker.  

