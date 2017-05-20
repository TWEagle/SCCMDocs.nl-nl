---
title: Upgraden naar System Center Configuration Manager | Microsoft-documenten
description: "Informatie over de stappen voor het uitvoeren van een geslaagde upgrade ter plaatse van een site en hiërarchie met System Center 2012 Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c64e7483-b4bb-4738-95f4-ecdaeb6a2ba6
caps.latest.revision: 21
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 9e58ab8dd892adf25429564adfd6f86849ddcbdf
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-to-system-center-configuration-manager"></a>Bijwerken naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt in-place upgrade-upgrade uitvoeren naar System Center Configuration Manager vanuit een site en hiërarchie met System Center 2012 Configuration Manager.  

 Vóór de upgrade van System Center 2012 Configuration Manager, moet u voorbereiden sites waarvoor u specifieke configuraties die kunnen voorkomen dat een geslaagde upgrade en vervolgens de upgradevolgorde wordt aangehouden wanneer meer dan één site is betrokken te verwijderen.  

 > [!TIP]
 > Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt om te beschrijven van drie verschillende concepten... Zie voor meer informatie over hoe elke term wordt gebruikt, [over upgrade-, update- en installatie](/sccm/core/understand/upgrade-update-install).

##  <a name="bkmk_path"></a> In-place upgradepaden  

**Upgrade uitvoeren naar versie 1702**   
Wanneer u versie 1702 basislijn media hebt, kunt u het volgende kunt bijwerken naar een volledig gelicentieerde versie van System Center Configuration Manager versie 1702:   
-      Een evaluatie-installatie van System Center Configuration Manager versie 1702
-      System Center 2012 Configuration Manager met servicepack 1
-      System Center 2012 Configuration Manager met servicepack 2
-      System Center 2012 R2 Configuration Manager
-      System Center 2012 R2 Configuration Manager met servicepack 1

**Upgrade uitvoeren naar versie 1606**  
De basislijn media voor versie 1606 is op 15 December 2016 uitgebracht om toe te voegen ondersteuning voor aanvullende upgradescenario's. Deze nieuwe versie ondersteunt de upgrade van de volgende naar een volledig gelicentieerde versie van System Center Configuration Manager versie 1606:  
-   Een evaluatie-installatie van System Center Configuration Manager versie 1606
-   Een release candidate installatie van System Center Configuration Manager  
-   System Center 2012 Configuration Manager met servicepack 1  
-   System Center 2012 Configuration Manager met servicepack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager met servicepack 1  

Als u versie 1606 basislijn media gedownload vóór 15 December 2016 kunt u alleen de volgende bijwerken naar een volledig gelicentieerde versie van System Center Configuration Manager versie 1606:
-   Een evaluatie-installatie van System Center Configuration Manager versie 1606
-   System Center 2012 Configuration Manager met servicepack 2
-   System Center 2012 R2 Configuration Manager met servicepack 1

<!-- Version 1511 has now dropped out of support
**Upgrade to version 1511**  
When you have version 1511 baseline media, you can upgrade the following to a fully licensed  version of System Center Configuration Manager version 1511:  
-   An evaluation install of System Center Configuration Manager version 1511
-   A release candidate install of System Center Configuration Manager  
-   System Center 2012 Configuration Manager with Service Pack 1  
-   System Center 2012 Configuration Manager with Service Pack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager with Service Pack 1  
-->


> [!TIP]  
>  Wanneer u een van een versie van System Center 2012 Configuration Manager op de vertakking van de huidige upgrade, kunt u mogelijk uw upgradeproces stroomlijnen. Zie voor meer informatie de volgende onderwerpen:  
>   
>  -   De sectie [Basislijn- en updateversies](../../../../core/servers/manage/updates.md#bkmk_Baselines) in [Updates voor System Center Configuration Manager](../../../../core/servers/manage/updates.md)  
>  -   [De CD. Meest recente map voor System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md)  

 **Het volgende wordt niet ondersteund:**  
-   Technische Preview van System Center Configuration Manager bijwerken naar een volledig gelicentieerde installatie wordt niet ondersteund.  Een Technical Preview-versie kan alleen naar een nieuwere versie van de Technical Preview worden geüpgraded.  

-   Migratie van een Technical Preview naar een volledig gelicentieerde versie wordt niet ondersteund.  

##  <a name="bkmk_checklist"></a> Controlelijsten voor bijwerken  
 De volgende controlelijsten kunt u van plan bent een upgrade naar System Center Configuration Manager.  

### <a name="before-you-upgrade"></a>Voordat u een upgrade uitvoert  

**Controleer uw System Center 2012 Configuration Manager-omgeving** en oplossen van problemen, zoals beschreven in de KB4018655: [Configuration Manager-clients opnieuw installeren om de vijf uur vanwege een terugkerende taak voor opnieuw proberen en kunnen leiden tot een onbedoeld Clientupgrade](https://support.microsoft.com/help/4018655).

**Zorg ervoor dat uw computeromgeving voldoet aan de ondersteunde configuraties** die nodig zijn voor het upgraden naar System Center Configuration Manager:  

Controleer de serverbesturingssystemen die worden gebruikt om sitesysteemrollen te hosten:  

-   Sommige oudere besturingssystemen wordt ondersteund door System Center 2012 Configuration Manager worden niet ondersteund door System Center Configuration Manager, en sitesysteemrollen op deze besturingssystemen moeten worden verplaatst of verwijderd vóór de upgrade. Controleer de [ondersteunde besturingssystemen voor systeemservers van sites](../../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md) documentatie.   
-   Prerequisite Checker voor Configuration Manager controleert de vereisten voor sitesysteemrollen op de siteserver of op externe sitesystemen  

Controleer de vereiste onderdelen voor alle computers die een sitesysteemrol hosten:  

-   Bijvoorbeeld, om een besturingssysteem implementeert, System Center Configuration Manager maakt gebruik van de Windows 10 Assessment and Deployment Kit (Windows ADK). Voordat u het installatieprogramma uitvoert, moet u Windows 10 ADK downloaden en installeren op de siteserver en op elke computer waarop een exemplaar van de SMS-provider wordt uitgevoerd.  

Zie [Ondersteunde configuraties voor System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md) voor algemene informatie over de ondersteunde platforms en vereiste configuraties.  

Zie voor meer informatie over het gebruik van de Windows ADK met Configuration Manager [vereisten voor de infrastructuur voor implementatie van besturingssystemen in System Center Configuration Manager](../../../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

**Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen:**  
Voordat u een site upgradet, moet u alle operationele problemen voor de siteserver, de sitedatabaseserver, en sitesysteemrollen die op externe computers zijn geïnstalleerd, oplossen. De upgrade van een site kan mislukken door bestaande operationele problemen.  

**Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:**  
Vóór de upgrade van een site installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als u voor een te installeren update computers opnieuw moet opstarten, start de desbetreffende computers dan opnieuw op voordat u de upgrade van het service pack start.  

Zie voor meer informatie [Windows Update](http://go.microsoft.com/fwlink/p/?LinkId=105851).  

**Verwijder de sitesysteemrollen die niet ondersteund door System Center Configuration Manager:**  
De volgende sitesysteemrollen in System Center Configuration Manager worden niet meer worden gebruikt en moeten worden verwijderd voordat u een van System Center 2012 Configuration Manager upgrade:  

-   Buiten-bandbeheerpunt  
-   Servicestatuscontrolepunt  

**Databasereplica's voor beheerpunten op primaire sites uitschakelen:**  
Configuration Manager kan niet een primaire site upgraden die een databasereplica voor beheerpunten ingeschakeld heeft. Schakel databasereplicatie uit voordat u:  

-   Een back-up van de sitedatabase maakt om de database-upgrade te testen  
-   Upgrade van de productiesite naar System Center Configuration Manager  

Zie voor meer informatie de volgende onderwerpen:  
-   System Center 2012 Configuration Manager:  [Databasereplica's voor beheerpunten configureren](https://technet.microsoft.com/library/hh846234.aspx)  
-   System Center Configuration Manager: [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md)  

**Software-updatepunten met NLB opnieuw:**  
Configuration Manager kan geen upgrade uitvoeren van een site die een Network Load Balancing (NLB) cluster host software-updatepunten gebruikt.  

Als u NLB-clusters voor software-updatepunten gebruikt, gebruik dan PowerShell om de NLB-cluster te verwijderen. (Beginnen met System Center 2012 Configuration Manager SP1, er is geen optie in de Configuration Manager-console voor het configureren van een NLB-cluster)  

**Schakel alle siteonderhoudstaken op elke site tijdens de duur van die site-upgrade:**  
Voordat u een naar System Center Configuration Manager upgrade, schakel alle siteonderhoudstaken die mogelijk worden uitgevoerd tijdens de tijd die het upgradeproces actief is. Dit omvat, maar is niet beperkt tot het volgende:  

-   Back-upserver van site  
-   Verouderde clientbewerkingen verwijderen  
-   Verouderde detectiegegevens verwijderen  

Wanneer een onderhoudstaak van de sitedatabase wordt uitgevoerd tijdens het upgradeproces, kan de site-upgrade mislukken.  

Voordat u een taak uitschakelt, registreert u het schema van de taak zodat u de configuratie ervan kunt herstellen nadat de site-upgrade voltooid is.  

Voor meer informatie over siteonderhoudstaken zie:  

-   System Center 2012 Configuration Manager:  [Planning voor onderhoudstaken voor Configuration Manager](https://technet.microsoft.com/library/gg712686.aspx)  
-   System Center Configuration Manager:  [Verwijzing voor onderhoudstaken voor System Center Configuration Manager](../../../../core/servers/manage/reference-for-maintenance-tasks.md)  

**Voer Prerequisite Checker van de installatie uit**:  
Vóór de upgrade van een site kunt u **Prerequisite Checker** onafhankelijk van Setup uitvoeren om te valideren dat uw site aan de vereisten voldoet. Later, wanneer u de site bijwerkt, Prerequisite Checker opnieuw uitgevoerd.  

Als u de media basislijn voor versie 1606 sinds de release van oktober 2016, evalueert onafhankelijke bepaalt de controle van de site voor een upgrade naar de huidige vertakking en de langetermijndoelen onderhoud vertakking (LTSB) van System Center Configuration beheren. Omdat sommige functies worden niet ondersteund door de LTSB, ziet u de vermeldingen in de *ConfigMgrPrereq.log* die vergelijkbaar zijn met het volgende:
 - INFO: De site is een LTSB-editie.
 - Niet-ondersteunde sitesysteemrol 'Asset Intelligence-synchronisatiepunt' voor de editie LTSB;    -Fout.    Configuration Manager heeft gedetecteerd dat de 'Asset Intelligence synchronisatiepunt' is geïnstalleerd. Asset Intelligence wordt niet ondersteund voor de LTSB-editie. U moet de Asset Intelligence synchronisatie sitesysteemrol verwijderen voordat u doorgaat.

Als u van plan bent om te werken naar de huidige vertakking fouten voor de editie LTSB kunnen veilig worden genegeerd. Ze alleen van toepassing als u van plan bent om te werken naar de LTSB.

Later, wanneer u Configuration Manager Setup voor de upgrade uitvoert, wordt de vereiste controle opnieuw uitvoeren en evalueren van uw site op basis van de vertakking van System Center Configuration Manager u installeren wilt (huidige vertakking of LTSB). Als u wilt bijwerken naar de huidige vertakking wordt weergegeven, worden de controle op functies die niet wordt ondersteund door de LTSB niet uitgevoerd.

Zie voor meer informatie de [vereistencontrole](/sccm/core/servers/deploy/install/prerequisite-checker) en [lijst van de vereiste controles voor System Center Configuration Manager](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

**Download vereiste bestanden en herdistribueerbare bestanden voor System Center Configuration Manager:**    
Gebruik **Setup Downloader** downloaden vereiste herdistribueerbare bestanden, taalpakketten en de recentste productupdates voor System Center Configuration Manager.  

Zie voor meer informatie, [Downloadprogramma](/sccm/core/servers/deploy/install/setup-downloader).  

**Plan het beheer van server- en clienttalen**:  
Wanneer u een site bijwerkt, installeert de site-upgrade alleen de taalpakketversies die u tijdens de upgrade selecteert.  

-   Met Setup worden de huidige taalconfiguratie van uw site gecontroleerd en worden vervolgens de taalpakketten geïdentificeerd die beschikbaar zijn in de map waar u eerder gedownloade vereiste bestanden opslaat.  
-   U kunt de selectie van de huidige server- en clienttaalpakketten dan bevestigen, of de selecties wijzigen om ondersteuning voor talen toe te voegen of te verwijderen.  
-   U kunt alleen de taalpakketten selecteren die beschikbaar zijn wanneer u Setup uitvoert (die wordt geleverd bij de vereiste bestanden die u downloadt).  

> [!NOTE]  
>  U kunt taalpakketten van System Center 2012 Configuration Manager niet gebruiken voor de talen voor een System Center Configuration Manager-site inschakelen.  

Zie voor meer informatie over taalpakketten [taalpakketten in System Center Configuration Manager](../../../../core/servers/deploy/install/language-packs.md).  

**Controleer de lijst met overwegingen voor upgrades van de site**:  
Wanneer u een site upgradet, worden bepaalde functies en configuraties opnieuw ingesteld op een standaardconfiguratie. Lees de informatie in  [Overwegingen voor bijwerken](#bkmk_considerations)ter voorbereiding op deze en verwante veranderingen.  

**Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:**  
Vóór de upgrade van een site maakt u een back-up van de sitedatabase om ervoor te zorgen dat u een geslaagde back-up hebt voor gebruik in geval van noodherstel.  

Zie [back-up en herstel voor System Center Configuration Manager](../../../../protect/understand/backup-and-recovery.md).  

**Maak een back-up van een aangepast Configuration.mof-bestand**:  
Als u een aangepast Configuration.mof-bestand gebruikt voor het definiëren van gegevensklassen die u gebruikt met de hardware-inventaris, maakt u een back-up van dit bestand voordat u de site upgradet. Herstel dit bestand op uw site nadat het upgraden is voltooid. Zie voor meer informatie over het gebruik van dit bestand [het uitbreiden van hardware-inventaris in System Center Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

**Test het database-upgradeproces op een kopie van de databaseback-up van de meest recente site:**  
Voordat u een centrale beheersite of primaire site van Configuration Manager bijwerkt, moet u het upgradeproces van de sitedatabase eerst testen op een kopie van de sitedatabase.  

-   U moet het upgradeproces voor de sitedatabase testen omdat de sitedatabase mogelijk wordt gewijzigd wanneer u een site bijwerkt.  
-   Hoewel een upgradetest van de database niet is vereist, kunt u hiermee problemen voor de upgrade identificeren voordat deze de productiedatabase beïnvloeden.  
-   Een mislukte upgrade van de sitedatabase kan leiden tot een onbruikbare sitedatabase, waardoor u mogelijk een siteherstel moet uitvoeren om de functionaliteit te herstellen.  
-   Hoewel de sitedatabase door verschillende sites in een hiërarchie wordt gedeeld, moet u de database op elke site testen voordat u die site bijwerkt.  
-   Als u databasereplica's gebruikt voor beheerpunten op een primaire site, schakelt u replicatie uit voordat u de back-up van de sitedatabase maakt.  

Configuration Manager biedt geen ondersteuning voor de back-up van secundaire sites noch de testupgrade van een secundaire sitedatabase.  

Het uitvoeren van een testdatabase-upgrade op de productie-sitedatabase wordt niet ondersteund. Dit leidt tot een upgrade van de sitedatabase en kan tot gevolg hebben dat uw site onbruikbaar wordt.  

Zie [Test the site database upgrade](#bkmk_test)(Upgrade van de sitedatabase testen) voor meer informatie.  

**Start opnieuw op de siteserver en iedere computer die als host fungeert voor een sitesysteemrol**:  
Dit wordt gedaan om ervoor te zorgen dat er geen acties van een recente installatie van updates of van de vereisten en is een bedrijfsspecifiek intern proces.  

**Upgrade van sites uitvoeren**:  
Beginnen bij de site op het hoogste niveau in de hiërarchie, voert u Setup.exe uit de bronmedia van System Center Configuration Manager.  

Nadat de upgrades op het bovenste siteniveau zijn voltooid, kunt u de upgrade uitvoeren van iedere onderliggende site. Voltooi de upgrade van elke site voordat u de volgende site bijwerkt.  

Totdat alle sites in uw hiërarchie naar System Center Configuration Manager upgraden, wordt uw hiërarchie draait in een modus van gemengde versies.  

Zie voor meer informatie over het uitvoeren van upgrade [sites bijwerken](#bkmk_upgrade).  

### <a name="after-you-upgrade"></a>Nadat u een upgrade hebt uitgevoerd  
**Zelfstandige Configuration Manager-consoles bijwerken**:  
Standaard, wanneer u een centrale beheersite of primaire site upgradet, upgradet de installatie ook de Configuration Manager-console is geïnstalleerd op de siteserver. U moet elke console die op een andere computer dan de siteserver is geïnstalleerd, echter handmatig bijwerken.  

> [!TIP]  
>  Sluit alle geopende consoles voordat u de upgrade uitvoert.  

Zie [System Center Configuration Manager-consoles installeren](../../../../core/servers/deploy/install/install-consoles.md) voor meer informatie.  

**Databasereplica's voor beheerpunten op primaire sites opnieuw configureren:**  
Als u databasereplica's voor beheerpunten op primaire sites gebruikt, moet u de databasereplica's verwijderen vóór de upgrade van de site. Na de upgrade van een primaire site configureert u de databasereplica voor beheerpunten opnieuw.   
Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md) voor meer informatie.  

**Configureer alle databaseonderhoudstaken die u uitgeschakeld hebt vóór de upgrade opnieuw:**  
Als u databaseonderhoudstaken hebt uitgeschakeld op een site vóór de upgrade ([Referentie voor onderhoudstaken voor System Center Configuration Manager](../../../../core/servers/manage/reference-for-maintenance-tasks.md)), dient u deze taken opnieuw te configureren op de site met behulp van dezelfde instellingen die reeds waren ingesteld vóór de upgrade.  

**Upgrades uitvoeren voor clients**:  
Wanneer uw sites hebt bijgewerkt naar System Center Configuration Manager, kunt u plannen om clients te upgraden.  

Bij de upgrade van een client wordt de huidige clientsoftware verwijderd en wordt de nieuwe clientsoftwareversie geïnstalleerd. Als u clients wilt upgraden, kunt elke methode gebruiken die door Configuration Manager wordt ondersteund.  

> [!TIP]  
>  Wanneer u de site op het hoogste niveau van een hiërarchie bijwerkt, wordt het clientinstallatiepakket op elk distributiepunt in de hiërarchie ook bijgewerkt. Bij de upgrade van een primaire site wordt het clientupgradepakket dat beschikbaar is van de primaire site, bijgewerkt.  

Zie [How to upgrade clients for Windows computers in System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) (Cients bijwerken voor Windows-computers in System Center Configuration Manager) voor informatie over het bijwerken van bestaande clients en het installeren van nieuwe clients.  

##  <a name="bkmk_considerations"></a> Overwegingen voor bijwerken  
**Automatische acties**:  
Wanneer u een naar System Center Configuration Manager upgrade, wordt de volgende acties automatisch uitgevoerd:  

-   De site voert een reset van de site uit, hetgeen betekent dat alle sitesysteemrollen opnieuw worden geïnstalleerd.  
-   Als de site een site op het hoogste niveau van een hiërarchie is, wordt het clientinstallatiepakket op elk distributiepunt in de hiërarchie bijgewerkt. De site werkt ook de standaard opstartinstallatiekopieën bij om de nieuwe Windows PE-versie te gebruiken die is opgenomen in Windows Assessment and Deployment Kit 10. De upgrade geldt echter niet voor bestaande media voor gebruik met implementatie van de installatiekopie.  
-   Als de site een primaire site is, wordt het clientupgradepakket voor die site bijgewerkt.  

**Handmatige acties voor de gebruiker met beheerdersrechten na een upgrade**   
Zorg ervoor dat de volgende acties worden uitgevoerd na de upgrade van een site:  

-   Zorg ervoor dat clients die aan elke primaire site zijn toegewezen, de clientsoftware voor de nieuwe versie upgraden en installeren.  
-   Elke Configuration Manager-console die verbinding maakt met de site en die wordt uitgevoerd op een computer die extern is van de siteserver bijwerken  
-   Op primaire sites waar u databasereplica's voor beheerpunten gebruikt, configureert u de databasereplica's opnieuw.  
-   Nadat de upgrade van de site is uitgevoerd, moet u handmatig fysieke media bijwerken zoals ISO-bestanden voor cd's en dvd's of USB-flashstations, of voorgefaseerde media die worden gebruikt voor Windows To Go-implementaties of die worden verschaft aan hardwareleveranciers. Hoewel de site-upgrade de standaardopstartinstallatiekopieën worden bijgewerkt er kan geen upgrade uitvoeren mediabestanden of apparaten gebruikt extern aan Configuration Manager  
-   Plan het bijwerken van niet-standaard opstartinstallatiekopieën wanneer u de oorspronkelijke (oudere) versie van Windows PE niet nodig hebt.  

**Acties die invloed hebben op configuraties en instellingen**   
Wanneer een site wordt bijgewerkt naar System Center Configuration Manager, worden bepaalde configuraties en instellingen verloren na de upgrade of worden ingesteld op een nieuwe standaardconfiguratie. De volgende tabel bevat instellingen die verloren gaan of wijzigen, en biedt details om u te helpen ze te plannen tijdens een site-upgrade:  

-   **Software Center:**  
    De volgende Software Center-items worden opnieuw ingesteld op hun standaardwaarden:  
    -   **Werkinformatie** wordt opnieuw ingesteld naar kantooruren van **5.00 u** tot **22.00 u** van maandag tot en met vrijdag.  
    -   De waarde voor **Computeronderhoud** wordt ingesteld op **Software Center-activiteiten onderbreken wanneer mijn computer zich in de presentatiemodus bevindt**.  
    -   De waarde voor **Extern beheer** wordt ingesteld op de waarde in de clientinstellingen die aan de computer zijn toegewezen.  
-   **Planningen overzicht software-updates:**  
     Aangepaste overzichtsplanningen voor software-updates of software-updategroepen worden opnieuw ingesteld op de standaardwaarde van 1 uur. Nadat de upgrade is voltooid, stelt u de aangepaste overzichtswaarden opnieuw in op de vereiste frequentie.  

##  <a name="bkmk_test"></a> De upgrade van de sitedatabase testen  
De volgende informatie is van toepassing alleen wanneer u een eerdere versoin zoals System Center 2012 Configuration Manager naar System Center Configuration Manager upgraden. Als uw site wordt al uitgevoerd voor System Center Configuration Manager en u een nieuwe update installeert, Zie [stap 2: Testen van de upgrade van de database voordat u een update installeert](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) van **voordat u een update in de console**.

Voordat u een site upgradet, test u een exemplaar van de sitedatabase voor de upgrade.  

Als u wilt testen van de database voor een upgrade, eerst u een kopie van de sitedatabase naar een exemplaar van SQL Server die niet als van een Configuration Manager-site host. De versie van SQL Server die u gebruikt om de databasekopie te hosten, moet een versie van SQL Server dat de versie van Configuration Manager wordt de bron van de databasekopie ondersteund.  

Voer vervolgens, na het herstellen van de sitedatabase op de computer met SQL Server Configuration Manager-installatie van de bronmap van media voor System Center Configuration Manager met de **/testdbupgrade** opdrachtregeloptie te gebruiken.  

-   Zie [Command-line options for Setup](../../../../core/servers/deploy/install/command-line-options-for-setup.md) (Opdrachtregelopties voor installatie) voor meer informatie over het maken en herstellen van een back-up van een sitedatabase.  
-   Zie de tabel in [Command-line options for Setup](../../../../core/servers/deploy/install/command-line-options-for-setup.md) (Opdrachtregelopties voor installatie) voor informatie over de opdrachtregeloptie **/TESTDBUPGRADE**.  
-   Zie het onderwerp [Ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md) voor meer informatie over de ondersteunde versies van SQL Server.  

> [!TIP]  
>  Als u Microsoft Intune geïntegreerd met Configuration Manager:  
>   
>  Wanneer u een testdatabase-upgrade uitvoert op en kopie van de sitedatabase die meer dan vijf dagen oud is, kunt u een van de volgende berichten ontvangen:  
>   
>  -   WAARSCHUWING: Upgrade wordt gedwongen volledige synchronisatie met cloud.  
>  -   FOUT: Database-upgrade wordt gedwongen volledige synchronisatie met cloud.  
>   
> Beide kunnen veilig worden genegeerd tijdens het testen van een database-upgrade ze verwijzen niet naar een fout of een probleem met de test-upgrade. In plaats daarvan, duiden ze op die tijdens de daadwerkelijke upgrade is uitgevoerd op gegevens uit de **Cloud** database replicatiegroep kan synchroniseren met Microsoft Intune.  

Gebruik de volgende procedure op elke centrale beheersite en primaire site die u wilt bijwerken.  

#### <a name="to-test-a-site-database-for-upgrade"></a>Een sitedatabase testen voor een upgrade  

1.  Maak een kopie van de sitedatabase en herstel die kopie op een exemplaar van SQL Server dat dezelfde editie als uw sitedatabase gebruikt en die niet als host van een Configuration Manager-site. Als de sitedatabase wordt uitgevoerd op een exemplaar van de Enterprise-editie van SQL Server, dient u de database dus te herstellen op een SQL Server-exemplaar waarop de Enterprise-editie van SQL Server wordt uitgevoerd.  

2.  Voer na het herstellen van de databasekopie Setup vanaf het BRONmedium voor System Center Configuration Manager. Wanneer u Setup wilt uitvoeren, gebruikt u de opdrachtregeloptie **/TESTDBUPGRADE** . Als het SQL Server-exemplaar dat de databasekopie host niet het standaardexemplaar is, moet u ook de opdrachtregelargumenten opgeven om het exemplaar aan te duiden dat de sitedatabasekopie host.  

     Stel dat u van plan bent om een sitedatabase met de databasenaam SMS_ABC bij te werken. U herstelt een kopie van deze sitedatabase naar een ondersteund exemplaar van SQL Server met de exemplaarnaam DBTest. Als u wilt testen van een upgrade van deze kopie van de sitedatabase, gebruik de volgende opdrachtregel: **Setup.exe/testdbupgrade DBtest\CM_ABC**  

     U vindt Setup.exe op de volgende locatie op het BRONmedium voor System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

3.  Op het exemplaar van SQL Server waarop u de database-upgrade test, bevat ConfigMgrSetup.log in de hoofdmap van het systeemstation informatie over de voortgang van de bewerking:  

    -   Als de testupgrade mislukt, lost u de fouten gerelateerd aan de upgradefout op, maakt u een nieuwe back-up van de sitedatabase en test u de upgrade van de nieuwe kopie van de sitedatabase.  
    -   Wanneer de upgrade lukt, kunt u de databasekopie verwijderen.  

        > [!NOTE]  
        >  U kunt de kopie van de sitedatabase die u gebruikt voor de testupgrade niet gebruiken als sitedatabase op een site.  

Wanneer u een kopie van de sitedatabase bijgewerkt, gaat u verder met het bijwerken van de Configuration Manager-site en de sitedatabase.  

##  <a name="bkmk_upgrade"></a> Upgrade van sites uitvoeren  
Nadat u configuraties vóór bijwerken voltooid voor uw site, test u de upgrade van de sitedatabase op een databasekopie en download vereiste bestanden en taalpakketten voor de versie van servicepack die u wilt installeren, bent u klaar om uw Configuration Manager-site te upgraden.  

Wanneer u een site in een hiërarchie wilt bijwerken, moet u eerst de site op het hoogste niveau van de hiërarchie bijwerken. Deze site op het hoogste niveau is een centrale beheersite of een zelfstandige primaire site. Wanneer de upgrade van een centrale beheersite is voltooid, kunt u onderliggende primaire sites in elke volgorde bijwerken. Wanneer u een primaire site hebt bijgewerkt, kunt u die site onderliggende secundaire sites bijwerken of extra primaire sites bijwerken voordat u secundaire sites bijwerkt.  

Als u een centrale beheersite of primaire site bijwerken, moet u Setup uitvoeren vanaf het BRONmedium van System Center Configuration Manager. Voer Setup niet uit om secundaire sites bij te werken. In plaats daarvan kunt u de Configuration Manager-console een secundaire site werken nadat u de upgrade van de bovenliggende primaire site.  

Voordat u een site upgradet, sluit u de Configuration Manager-console die is geïnstalleerd op de siteserver pas nadat de site-upgrade is voltooid. Sluit ook elke Configuration Manager-console wordt uitgevoerd op andere computers dan de siteserver. U kunt de console weer verbinden als de site is bijgewerkt. Echter totdat u een upgrade uitvoert van een Configuration Manager-console naar de nieuwe versie van Configuration Manager, die console kan geen objecten en gegevens worden weergegeven die beschikbaar zijn in de nieuwe versie van Configuration Manager.  

Gebruik de volgende procedures om Configuration Manager-sites te upgraden:  

#### <a name="to-upgrade-a-central-administration-site-or-primary-site"></a>Een centrale beheersite of primaire site bijwerken  

1.  Controleer of de gebruiker die Setup uitvoert over de volgende beveiligingsrechten beschikt:  

    -   Lokale beheerdersrechten op de siteservercomputer.  
    -   Lokale beheerdersrechten op de databaseserver voor de externe site.    </br></br>

2.  Open Windows Verkenner op de siteservercomputer en blader naar  **&lt;ConfigMgSourceMedia\>\SMSSETUP\BIN\X64**.  

3.  Dubbelklik op **Setup.exe**. De Configuration Manager-installatiewizard wordt geopend.  

4.  Klik op de pagina **Voordat u begint** op **Volgende**.  

5.  Op de pagina **Aan de slag** selecteert u **Deze Configuration Manager-site bijwerken**en vervolgens klikt u op **Volgende**.  

6.  Klik op de pagina **Productcode** op **Volgende**.  

     Als u eerder de evaluatie van de Configuration Manager is geïnstalleerd, kunt u **Installeer de gelicentieerde versie van dit product**, en voer vervolgens de productcode voor de volledige installatie van Configuration Manager converteren van de site naar de volledige versie.  

     Beginnen met de oktober 2016-release van de versie 1606 basislijn media voor System Center Configuration Manager, kunt u de verloopdatum van uw Software Assurance-overeenkomst opgeven. U hebt ook de mogelijkheid om op te geven de **Software Assurance-vervaldatum** van uw gebruiksrechtovereenkomst als u een handige herinnering na die datum. Als u geen dit tijdens de installatie, kunt u deze later vanuit binnen de Configuration Manager-console.

     >  [!NOTE]   
     >  Microsoft heeft de verloopdatum die u hebt ingevoerd en wordt deze datum niet gebruiken voor validatie van de licentie niet valideren.  In plaats daarvan kunt u dit gebruiken als een herinnering aan de vervaldatum. Dit is handig omdat Configuration Manager periodiek controleert op nieuwe software-updates die worden aangeboden online en de status van uw software assurance-licentie moet actueel zijn om in aanmerking voor het gebruik van deze aanvullende updates.    

     Zie voor meer informatie [volumelicenties en vertakkingen voor System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

7.  Lees en accepteer de licentievoorwaarden op de pagina **Licentievoorwaarden voor Microsoft-software** en klik vervolgens op **Volgende**.  

8.  Lees en accepteer de licentievoorwaarden voor de vereiste software op de pagina **Vereiste licenties** en klik vervolgens op **Volgende**. Het installatieprogramma downloadt en installeert de software automatisch op sitesystemen of clients wanneer dit nodig is. U moet alle selectievakjes inschakelen voordat u doorgaat naar de volgende pagina.  

9. Geef op de pagina **Vereiste downloads** op of de meest recente vereiste herdistribueerbare bestanden, taalpakketten en de meest recente productupdates van internet moeten worden gebruikt of dat de eerder gedownloade bestanden volstaan. Klik vervolgens op **Volgende**. Als u eerder de bestanden had gedownload met behulp van de Setup Downloader, selecteert u **Eerder gedownloade bestanden gebruiken** en specificeert u de downloadmap. Zie voor meer informatie [Downloadprogramma](/sccm/core/servers/deploy/install/setup-downloader).

    > [!NOTE]  
    >  Als u eerder gedownloade bestanden gebruikt, controleert u of het pad naar de downloadmap de recentste versie van de bestanden bevat.  

10. Bekijk op de pagina **Selectie van servertaal** welke talen momenteel zijn geïnstalleerd voor de site. Selecteer extra talen die beschikbaar op deze site voor de Configuration Manager-console en voor rapporten zijn of de selectievakjes van de talen die u niet meer wilt ondersteunen op deze site en klik vervolgens op **volgende**. Engels wordt standaard geselecteerd en kan niet worden verwijderd.  

    > [!IMPORTANT]  
    >  Elke versie van Configuration Manager kan geen taalpakketten uit eerdere versies van Configuration Manager gebruiken. Als ondersteuning wilt inschakelen voor een taal op een Configuration Manager-site waarop u een upgrade uitvoert, moet u de versie van het taalpakket voor die nieuwe versie gebruiken. Voor bijvoorbeeld tijdens de upgrade van System Center 2012 Configuration Manager voor System Center Configuration Manager als de System Center Configuration Manager-versie van een taalpakket niet beschikbaar is met de vereiste bestanden die u hebt gedownload, ondersteuning voor worden die taal niet geïnstalleerd.  

11. Bekijk op de pagina **Selectie van clienttaal** welke talen momenteel zijn geïnstalleerd voor de site. Selecteer extra talen die op deze site beschikbaar zijn voor clientcomputers. U kunt ook talen wissen die u niet meer wilt ondersteunen op deze site. Geef op of alle clienttalen moeten worden ingeschakeld voor clients voor mobiele apparaten en klik vervolgens op **Volgende**. Engels wordt standaard geselecteerd en kan niet worden verwijderd.  

    > [!IMPORTANT]  
    >  Elke versie van Configuration Manager kan geen taalpakketten uit eerdere versies van Configuration Manager gebruiken. Als ondersteuning wilt inschakelen voor een taal op een Configuration Manager-site waarop u een upgrade uitvoert, moet u de versie van het taalpakket voor die nieuwe versie gebruiken. Voor bijvoorbeeld tijdens de upgrade van System Center 2012 Configuration Manager voor System Center Configuration Manager als de System Center Configuration Manager-versie van een taalpakket niet beschikbaar is met de vereiste bestanden die u hebt gedownload, ondersteuning voor worden die taal niet geïnstalleerd.  

12. Klik op de pagina **Samenvatting van instellingen** op **Volgende** om Prerequisite Checker te starten om te bepalen in hoeverre de server gereed is voor het bijwerken van de site.  

13. Klik, als er geen problemen worden vermeld, op de pagina **Controle van vereisten voor installatie** op **Volgende** om de site en sitesysteemrollen bij te werken. Als Prerequisite Checker een probleem aantreft, klikt u op een item in de lijst voor gegevens over hoe u het probleem kunt oplossen. Alle items met de status **Fout** in de lijst moeten worden opgelost voordat u de installatie kunt voortzetten. Klik na het oplossen van het probleem op **Controle uitvoeren** om de controle van vereiste software opnieuw te starten. U kunt ook het bestand ConfigMgrPrereq.log openen in de systeemhoofdmap om de resultaten van Prerequisite Checker te controleren. Het logboekbestand kan aanvullende informatie bevatten die niet is weergegeven in de gebruikersinterface. Zie voor een lijst van de installatie vereiste regels en beschrijvingen [Prerequisite Checker](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

Op de pagina **Upgrade uitvoeren** wordt de algehele voortgang weergegeven. Wanneer het installatieprogramma de installatie van de hoofdsiteserver en het sitesysteem voltooit, kunt u de wizard sluiten. Siteconfiguratie gaat door op de achtergrond.  

#### <a name="to-upgrade-a-secondary-site"></a>Een secundaire site bijwerken  

1.  Controleer of de gebruiker met beheerdersrechten die het installatieprogramma uitvoert beschikt over de volgende beveiligingsrechten:  

    -   Lokale beheerdersrechten op de computer voor de secundaire site  
    -   De beveiligingsrol Infrastructuurbeheerder of Volledige beheerder op de bovenliggende primaire site  
    -   Systeembeheerdersrechten voor de sitedatabase van de secundaire site.  
    </br>
2.  Klik op **Beheer**in de Configuration Manager-console.  

3.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Sites**.  

4.  Selecteer de secundaire site die u wilt bijwerken en klik vervolgens op het tabblad **Start** in de groep **Site** op **Upgrade uitvoeren**.  

5.  Klik op **Ja** om te bevestigen en de secundaire site bij te werken.  

De secundaire site wordt op de achtergrond bijgewerkt. Nadat de upgrade is voltooid, kunt u de status in de Configuration Manager-console controleren. U doet dit door de server voor de secundaire site te selecteren en op het tabblad **Start** in de groep **Site** op **Installatiestatus weergeven**te klikken.  

##  <a name="BKMK_PostUpgrade"></a> Taken na de upgrade uitvoeren  
Wanneer u een site hebt bijgewerkt naar een nieuw servicepack, moet u mogelijk aanvullende taken uitvoeren om de upgrade te voltooien of de site opnieuw te configureren. Deze taken kunnen de upgrade van Configuration Manager-clients of Configuration Manager-consoles, opnieuw inschakelen van databasereplica's voor beheerpunten of het herstellen van instellingen voor Configuration Manager-functionaliteit die u gebruikt en die niet bewaard is gebleven na de servicepackupgrade bevatten.  

**Bekende problemen voor secundaire sites:**  
- **Wanneer u een upgrade naar versie 1511:** Opdat clients op secundaire sites kunt zoeken naar het beheerpunt van de secundaire site (proxy-beheerpunt), het beheerpunt handmatig toevoegen aan grensgroepen, waaronder ook de distributiepunten op de secundaire site.  

- **Wanneer u een upgrade naar versie 1606 of hoger:** Proxy-beheerpunten worden automatisch toegevoegd aan grensgroepen die op de secundaire site distributiepunten.

