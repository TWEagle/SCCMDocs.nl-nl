---
title: Vereistencontrole
titleSuffix: Configuration Manager
description: Informatie over het gebruik van Prerequisite Checker te identificeren en oplossen van problemen die een site of sitesysteemrolinstallatie kunnen blokkeren.
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf13bb8-4ba2-4bd7-9fac-d36a9d88a1b6
caps.latest.revision: "3"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 6709ee7e9e570c827ec9fc3433fa3acded11e0e4
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="prerequisite-checker-for-system-center-configuration-manager"></a>Vereistencontrole voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Voordat u Setup uitvoeren om te installeren of upgraden van een System Center Configuration Manager-site of voordat u een sitesysteemrol op een nieuwe server installeert, kunt u deze zelfstandige toepassing (**Prereqchk.exe**) van de versie van Configuration Manager die u wilt gebruiken om te controleren of de gereedheid van de server. Gebruik de Prerequisite Checker vaststellen en oplossen van problemen die een site of sitesysteemrolinstallatie blokkeren.  

> [!NOTE]  
>  Prerequisite Checker wordt altijd uitgevoerd als onderdeel van de installatie.  

Standaard de Prerequisite Checker uitgevoerd:  

-   Valideert de server waarop deze wordt uitgevoerd.  
-   De lokale computer gescand naar een bestaande siteserver en alleen de controles die van toepassing op de site zijn worden uitgevoerd.  
-   Als er geen bestaande sites worden gedetecteerd, worden alle vereiste regels uitgevoerd.  
-   Controleert deze regels om te controleren of software en instellingen die vereist zijn voor installatie zijn geïnstalleerd. Het is mogelijk dat de vereiste software is vereist aanvullende configuratie of software-updates die niet worden geverifieerd door Prerequisite Checker.  
-   De resultaten worden geregistreerd de **ConfigMgrPrereq.log** -bestand op het systeemstation van de computer. Het logboekbestand kan aanvullende informatie bevatten die niet wordt weergegeven in de toepassingsinterface van de.  

Wanneer u Prerequisite Checker uitvoert vanaf een opdrachtprompt en specifieke opdrachtregelopties opgeeft:  

-   Prerequisite Checker voert alleen de controles die zijn gekoppeld aan de siteserver of sitesystemen die u in de opdrachtregel opgeeft.  
-   Om te controleren op een externe computer, moet uw gebruikersaccount beheerdersrechten voor de externe computer hebben.  

Zie voor meer informatie over de controles die Prerequisite Checker uitvoert [lijst met vereistencontroles voor System Center Configuration Manager controleert](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

## <a name="copy-prerequisite-checker-files-to-another-computer"></a>Prerequisite Checker-bestanden kopiëren naar een andere computer  

1.  Ga in Windows Verkenner naar een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Configuration Manager-installatiepad*\>\BIN\X64**  

2.  Kopieer de volgende bestanden naar de doelmap op de andere computer:  

    -   Prereqchk.exe  
    -   Prereqcore.dll  
    -   Basesql.dll  
    -   Basesvr.dll  
    -   Baseutil.dll  

##  <a name="run-prerequisite-checker-with-default-checks"></a>Prerequisite Checker uitvoeren met standaardcontroles  

1.  Ga in Windows Verkenner naar een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Configuration Manager-installatiepad*\>\BIN\X64**  

2.  Voer **prereqchk.exe** om Prerequisite Checker te starten.   
    Prerequisite Checker detecteert bestaande sites, en als gevonden, controleert voor gereedheid voor upgrade. Als er geen sites worden gevonden, worden alle controles worden uitgevoerd. De **Sitetype** kolom bevat informatie over de siteserver of sitesysteem waaraan de regel gekoppeld is.  

##  <a name="run-prerequisite-checker-from-a-command-prompt-for-all-default-checks"></a>Prerequisite Checker uitvoeren vanaf een opdrachtprompt voor alle standaardcontroles  

1.  Open een opdrachtpromptvenster en wijzig de mappen in een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Configuration Manager-installatiepad*\>\BIN\X64**  

2.  Voer **prereqchk.exe/Local** Prerequisite Checker starten en alle vereiste controles op de server worden uitgevoerd.  

## <a name="run-prerequisite-checker-from-a-command-prompt-to-use-options"></a>Prerequisite Checker uitvoeren vanaf een opdrachtprompt te gebruiken opties  

1.  Open een opdrachtpromptvenster en wijzig de mappen in een van de volgende locaties:  

    -   **&lt;*Configuration Manager-installatiemedia*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Configuration Manager-installatiepad*\>\BIN\X64**  

2.  Voer **prereqchk.exe** met het toevoegen van een of meer van de volgende opdrachtregelopties.  

    Bijvoorbeeld, om te controleren op een primaire site, kunt u het volgende:  

       **prereqchk.exe [/ noui] / PRI/SQL &lt;FQDN van SQL Server\> /SDK &lt;FQDN van SMS-Provider\> [/ JOIN &lt;FQDN-naam van de centrale beheersite\>] [/MP &lt;FQDN van beheerpunt\>] [/DP &lt;FQDN van distributiepunt\>]**  

    **Server centrale beheersite:**  

    -   **/ NOUI**  

         Niet vereist. Prerequisite Checker gestart zonder de gebruikersinterface weer te geven. U moet deze optie voordat een andere optie opgeven op de opdrachtregel.  

    -   **/ CA 'S**  

         Vereist. Verifieert of de lokale computer voldoet aan de vereisten voor de centrale beheersite.  

    -   **/ SQL &lt;* FQDN van SQL Server*>**  

         Vereist. Met behulp van de volledig gekwalificeerde domeinnaam (FQDN), wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor SQL Server om de Configuration Manager-sitedatabase te hosten.  

    -   **/ SDK &lt;* FQDN van SMS-Provider*>**  

         Vereist. Verifieert of de opgegeven computer voldoet aan de vereisten voor de SMS-Provider.  

    -   **/ Ssbport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor de communicatie via de poort van SQL Server Service Broker (SSB). De standaard SSB-poort is 4022.  

    -   **InstallDir &lt;* installatiepad Configuration Manager*>**  

         Niet vereist. Controleert of de minimale schijfruimte van vereisten voor site-installatie.  

    **Primaire siteserver:**  

    -   **/ NOUI**  

        Niet vereist. Prerequisite Checker gestart zonder de gebruikersinterface weer te geven. U moet deze optie voordat een andere optie opgeven op de opdrachtregel.  

    -   **/ PRI**  

         Vereist. Verifieert of de lokale computer voldoet aan de vereisten voor de primaire site.  

    -   **/ SQL &lt;* FQDN van SQL Server*>**  

         Vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor SQL Server om de Configuration Manager-sitedatabase te hosten.  

    -   **/ SDK &lt;* FQDN van SMS-Provider*>**  

         Vereist. Verifieert of de opgegeven computer voldoet aan de vereisten voor de SMS-Provider.  

    -   **/ JOIN &lt;* FQDN-naam van de centrale beheersite*>**  

         Niet vereist. Hiermee wordt gecontroleerd of de lokale computer voldoet aan de vereisten voor het verbinden met de server van centrale beheersite.  

    -   **/MP &lt;* FQDN van beheerpunt*>**  

         Niet vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de sitesysteemrol management. Deze optie wordt alleen ondersteund wanneer u de **/PRI** optie.  

    -   **/DP &lt;* FQDN van distributiepunt*>**  

         Niet vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de sitesysteemrol distributiepunt. Deze optie wordt alleen ondersteund wanneer u de **/PRI** optie.  

    -   **/ Ssbport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor de communicatie voor de SSB-poort. De standaard SSB-poort is 4022.  

    -   **InstallDir &lt;* installatiepad Configuration Manager*>**  

         Niet vereist. Controleert of de minimale schijfruimte van vereisten voor site-installatie.  

    **Secundaire siteserver:**  

    -   **/ NOUI**  

         Niet vereist. Prerequisite Checker gestart zonder de gebruikersinterface weer te geven. U moet deze optie voordat een andere optie opgeven op de opdrachtregel.  

    -   **/ SEC &lt;* FQDN van secundaire siteserver*>**  

         Vereist. Hiermee wordt gecontroleerd of de opgegeven computer voldoet aan de vereisten voor de secundaire site.  

    -   **/ INSTALLSQLEXPRESS**  

         Niet vereist. Verifieert dat SQL Server Express kan worden geïnstalleerd op de opgegeven computer.  

    -   **/ Ssbport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor de communicatie voor de SSB-poort. De standaard SSB-poort is 4022.  

    -   **/ Sqlport**  

         Niet vereist. Controleert of een firewalluitzondering actief is voor communicatie voor de SQL Server-servicepoort en de poort is niet in gebruik door het benoemde exemplaar van SQL Server. De standaardpoort is 1433.  

    -   **InstallDir &lt;* installatiepad Configuration Manager*>**  

         Niet vereist. Controleert of de minimale schijfruimte van vereisten voor site-installatie.  

    -   **/ SourceDir**  

         Niet vereist. Hiermee wordt gecontroleerd of het computeraccount van de secundaire site toegang heeft tot de map die als host fungeert voor de bronbestanden voor installatie.  

   **Configuration Manager-console:**  

    -   **/ Adminui**  

         Vereist. Verifieert of de lokale computer voldoet aan de vereisten voor het installeren van Configuration Manager.  

3.  In de gebruikersinterface van Prerequisite Checker Prerequisite Checker maakt een lijst met gedetecteerde problemen in de **vereistenresultaat** sectie.  

    -   Klik op een item in de lijst voor meer informatie over het oplossen van het probleem.  
    -   U moet alle items in de lijst met oplossen een **fout** status voordat de installatie van de siteserver, sitesysteem of Configuration Manager-console.  
    -   U kunt ook openen de **ConfigMgrPrereq.log** bestand in de hoofdmap van het systeemstation te bekijken van resultaten van Prerequisite Checker. Het logboekbestand kan aanvullende informatie bevatten die niet wordt weergegeven in de gebruikersinterface van Prerequisite Checker.  
