---
title: Bijwerken naar System Center Configuration Manager
description: Meer informatie over de stappen voor het uitvoeren van een geslaagde in-place upgrade vanaf een site en hiërarchie met System Center 2012 Configuration Manager.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c64e7483-b4bb-4738-95f4-ecdaeb6a2ba6
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 72e11a04eb64d649749f2001ac4e3550c784132c
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="upgrade-to-system-center-configuration-manager"></a>Bijwerken naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt in-place upgrade-upgrade uitvoeren naar System Center Configuration Manager van een site en hiërarchie met System Center 2012 Configuration Manager.  

 Vóór de upgrade van System Center 2012 Configuration Manager, moet u sites waarvoor u specifieke configuraties verwijderen die kunnen voorkomen dat een geslaagde upgrade en voer vervolgens het upgradeproces wanneer meer dan één site is betrokken voorbereiden.  

 > [!TIP]
 > Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt voor het beschrijven van drie afzonderlijke concepten. Zie voor meer informatie over hoe elke term wordt gebruikt, [over upgrade-, update- en installatie](/sccm/core/understand/upgrade-update-install).

##  <a name="bkmk_path"></a> In-place upgradepaden  

**Upgrade uitvoeren naar versie 1802**   
Wanneer u versie 1702 basislijnmedia hebt, kunt u de volgende upgraden naar een volledig gelicentieerde versie van System Center Configuration Manager versie 1802:   
-     De installatie van een evaluatieversie van System Center Configuration Manager versie 1802
-     System Center 2012 Configuration Manager met servicepack 1
-     System Center 2012 Configuration Manager met servicepack 2
-     System Center 2012 R2 Configuration Manager
-     System Center 2012 R2 Configuration Manager met servicepack 1

**Upgrade uitvoeren naar versie 1702**   
Wanneer u versie 1702 basislijnmedia hebt, kunt u de volgende upgraden naar een volledig gelicentieerde versie van System Center Configuration Manager versie 1702:   
-     De installatie van een evaluatieversie van System Center Configuration Manager versie 1702
-     System Center 2012 Configuration Manager met servicepack 1
-     System Center 2012 Configuration Manager met servicepack 2
-     System Center 2012 R2 Configuration Manager
-     System Center 2012 R2 Configuration Manager met servicepack 1

**Upgrade uitvoeren naar versie 1606**  
De basislijnmedia voor de versie 1606 is op 15 December 2016 uitgebracht om ondersteuning voor aanvullende upgradescenario's. Deze nieuwe versie ondersteunt de upgrade van de volgende naar een volledig gelicentieerde versie van System Center Configuration Manager versie 1606:  
-   De installatie van een evaluatieversie van System Center Configuration Manager versie 1606
-   Een release candidate-installatie van System Center Configuration Manager  
-   System Center 2012 Configuration Manager met servicepack 1  
-   System Center 2012 Configuration Manager met servicepack 2  
-   System Center 2012 R2 Configuration Manager zonder servicepack
-   System Center 2012 R2 Configuration Manager met servicepack 1  

Als u versie 1606 basislijnmedia gedownload vóór 15 December 2016, kunt u alleen de volgende upgraden naar een volledig gelicentieerde versie van System Center Configuration Manager versie 1606:
-   De installatie van een evaluatieversie van System Center Configuration Manager versie 1606
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
>  Wanneer u een van een versie van System Center 2012 Configuration Manager naar de huidige vertakking upgrade, kunt u mogelijk uw upgradeproces stroomlijnen. Zie voor meer informatie de volgende onderwerpen:  
>   
>  -   De sectie [Basislijn- en updateversies](../../../../core/servers/manage/updates.md#bkmk_Baselines) in [Updates voor System Center Configuration Manager](../../../../core/servers/manage/updates.md)  
>  -   [De CD. Meest recente map voor System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md)  

 **Het volgende wordt niet ondersteund:**  
-   Een Technical Preview voor System Center Configuration Manager bijwerken naar een volledig gelicentieerde installatie wordt niet ondersteund.  Een Technical Preview-versie kan alleen naar een nieuwere versie van de Technical Preview worden geüpgraded.  

-   Migratie van een Technical Preview naar een volledig gelicentieerde versie wordt niet ondersteund.  

##  <a name="bkmk_checklist"></a> Controlelijsten voor bijwerken  
 De volgende controlelijsten kunt u van plan bent een geslaagde upgrade naar System Center Configuration Manager.  

### <a name="before-you-upgrade"></a>Voordat u een upgrade uitvoert  

**Bekijk uw System Center 2012 Configuration Manager-omgeving** en oplossen van problemen zoals beschreven in de KB4018655: [Configuration Manager-clients opnieuw installeren om de vijf uur vanwege een terugkerende taak voor opnieuw proberen en kan leiden tot een onbedoelde Clientupgrade](https://support.microsoft.com/help/4018655).

**Zorg ervoor dat uw computeromgeving voldoet aan de ondersteunde configuraties** die vereist zijn voor het upgraden naar System Center Configuration Manager:  

Controleer de serverbesturingssystemen die worden gebruikt om sitesysteemrollen te hosten:  

-   Sommige oudere besturingssystemen wordt ondersteund door System Center 2012 Configuration Manager worden niet ondersteund door System Center Configuration Manager en de sitesysteemrollen op deze besturingssystemen moeten worden verplaatst of verwijderd vóór de upgrade. Controleer de [ondersteunde besturingssystemen voor Sitesysteemservers](../../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md) documentatie.   
-   Vereistencontrole voor Configuration Manager controleert de vereisten voor sitesysteemrollen op de siteserver of op externe sitesystemen  

Controleer de vereiste onderdelen voor alle computers die een sitesysteemrol hosten:  

-   Bijvoorbeeld, om een besturingssysteem implementeert, System Center Configuration Manager maakt gebruik van de Windows 10 Assessment and Deployment Kit (Windows ADK). Voordat u het installatieprogramma uitvoert, moet u Windows 10 ADK downloaden en installeren op de siteserver en op elke computer waarop een exemplaar van de SMS-provider wordt uitgevoerd.  

Zie [Ondersteunde configuraties voor System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md) voor algemene informatie over de ondersteunde platforms en vereiste configuraties.  

Zie voor meer informatie over het gebruik van Windows ADK met Configuration Manager [vereisten voor de infrastructuur voor besturingssysteemimplementatie in System Center Configuration Manager](../../../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

**Bekijk de site en hiërarchiestatus en controleer of er geen onopgeloste problemen zijn:**  
Voordat u een site upgradet, moet u alle operationele problemen voor de siteserver, de sitedatabaseserver, en sitesysteemrollen die op externe computers zijn geïnstalleerd, oplossen. De upgrade van een site kan mislukken door bestaande operationele problemen.  

**Installeer alle toepasselijke kritieke updates voor besturingssystemen op computers die als host fungeren voor de site, de Sitedatabaseserver en externe sitesysteemrollen:**  
Vóór de upgrade van een site installeert u alle kritieke updates voor elk toepasselijk sitesysteem. Als u voor een te installeren update computers opnieuw moet opstarten, start de desbetreffende computers dan opnieuw op voordat u de upgrade van het service pack start.  

Zie voor meer informatie [Windows Update](http://go.microsoft.com/fwlink/p/?LinkId=105851).  

**De sitesysteemrollen die niet wordt ondersteund door System Center Configuration Manager verwijderen:**  
De volgende sitesysteemrollen in System Center Configuration Manager niet meer worden gebruikt en moeten worden verwijderd voordat u een van System Center 2012 Configuration Manager upgrade:  

-   Buiten-bandbeheerpunt  
-   Systeemstatuscontrolepunt  

**Databasereplica's voor beheerpunten op primaire sites uitschakelen:**  
Configuration Manager kan niet een primaire site upgraden die een databasereplica voor beheerpunten ingeschakeld heeft. Schakel databasereplicatie uit voordat u:  

-   Een back-up van de sitedatabase maakt om de database-upgrade te testen  
-   De productiesite bijwerkt naar System Center Configuration Manager  

Zie voor meer informatie de volgende onderwerpen:  
-   System Center 2012 Configuration Manager:  [Databasereplica's voor beheerpunten configureren](https://technet.microsoft.com/library/hh846234.aspx)  
-   System Center Configuration Manager: [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md)  

**Software-updatepunten met NLB's opnieuw configureren:**  
Configuration Manager kan een site die gebruikmaakt van een Network Load Balancing (NLB) cluster host software-updatepunten niet bijwerken.  

Als u NLB-clusters voor software-updatepunten gebruikt, gebruik dan PowerShell om de NLB-cluster te verwijderen. (Vanaf System Center 2012 Configuration Manager SP1 is er geen optie was in de Configuration Manager-console om een NLB-cluster te configureren)  

**Alle siteonderhoudstaken op elke site uitschakelen voor de duur van de upgrade van die site:**  
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

Als u de basislijnmedia voor versie 1606 van de release van oktober 2016, evalueert de onafhankelijke controle de site voor het upgraden naar de huidige vertakking zowel de Long-Term Servicing Branch (LTSB) van System Center Configuration beheren. Omdat sommige functies worden niet ondersteund door de LTSB, ziet u mogelijk vermeldingen in de *ConfigMgrPrereq.log* die zijn als volgt:
 - INFO: De site is een LTSB-versie.
 - Niet-ondersteunde sitesysteemrol 'Asset Intelligence-synchronisatiepunt' voor de LTSB-versie    Fout;    Configuration Manager heeft gedetecteerd dat de 'Asset Intelligence synchronisatiepunt' is geïnstalleerd. Asset Intelligence wordt niet ondersteund voor de LTSB-editie. Voordat u kunt doorgaan, moet u de Asset Intelligence-synchronisatie sitesysteemrol verwijderen.

Als u van plan bent om te upgraden naar de huidige vertakking, kunnen fouten voor de LTSB-versie worden genegeerd. Ze zijn alleen van toepassing als u van plan bent om te upgraden naar de LTSB.

Later, wanneer u Configuration Manager Setup de upgrade uitvoert, wordt de controle op vereisten opnieuw uitvoeren en evalueren van uw site op basis van de vertakking van System Center Configuration Manager (huidige vertakking of LTSB) vereist. Als u wilt upgraden naar de huidige vertakking, worden de controle op functies die worden niet ondersteund door de LTSB niet uitgevoerd.

Zie voor meer informatie de [Prerequisite Checker](/sccm/core/servers/deploy/install/prerequisite-checker) en [lijst van de vereiste controles voor System Center Configuration Manager](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

**Download vereiste bestanden en herdistribueerbare bestanden voor System Center Configuration Manager:**    
Gebruik **Setup Downloader** vereiste herdistribueerbare bestanden, taalpakketten en de meest recente updates downloaden voor System Center Configuration Manager.  

Zie voor informatie [Setup Downloader](/sccm/core/servers/deploy/install/setup-downloader).  

**Plan het beheer van server- en clienttalen**:  
Wanneer u een site bijwerkt, installeert de site-upgrade alleen de taalpakketversies die u tijdens de upgrade selecteert.  

-   Met Setup worden de huidige taalconfiguratie van uw site gecontroleerd en worden vervolgens de taalpakketten geïdentificeerd die beschikbaar zijn in de map waar u eerder gedownloade vereiste bestanden opslaat.  
-   U kunt de selectie van de huidige server- en clienttaalpakketten dan bevestigen, of de selecties wijzigen om ondersteuning voor talen toe te voegen of te verwijderen.  
-   U kunt alleen de taalpakketten selecteren die beschikbaar zijn wanneer u Setup uitvoert (die wordt geleverd bij de vereiste bestanden die u downloadt).  

> [!NOTE]  
>  U kunt taalpakketten van System Center 2012 Configuration Manager niet gebruiken om in te schakelen van talen voor een System Center Configuration Manager-site.  

Zie voor meer informatie over taalpakketten [taalpakketten in System Center Configuration Manager](../../../../core/servers/deploy/install/language-packs.md).  

**Controleer de lijst met overwegingen voor upgrades van de site**:  
Wanneer u een site upgradet, worden bepaalde functies en configuraties opnieuw ingesteld op een standaardconfiguratie. Lees de informatie in  [Overwegingen voor bijwerken](#bkmk_considerations)ter voorbereiding op deze en verwante veranderingen.  

**Maak een back-up van de sitedatabase op de centrale beheersite en primaire sites:**  
Vóór de upgrade van een site maakt u een back-up van de sitedatabase om ervoor te zorgen dat u een geslaagde back-up hebt voor gebruik in geval van noodherstel.  

Zie [back-up en herstel voor System Center Configuration Manager](../../../../protect/understand/backup-and-recovery.md).  

**Maak een back-up van een aangepast Configuration.mof-bestand**:  
Als u een aangepast Configuration.mof-bestand gebruikt voor het definiëren van gegevensklassen die u gebruikt met de hardware-inventaris, maakt u een back-up van dit bestand voordat u de site upgradet. Herstel dit bestand op uw site nadat het upgraden is voltooid. Zie voor meer informatie over het gebruik van dit bestand [hardware-inventarisatie in System Center Configuration Manager uitbreiden](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

**Test het database-upgradeproces op een kopie van de recentste site-databasebackup:**  
Voordat u een centrale beheersite of primaire site van Configuration Manager bijwerkt, moet u het upgradeproces van de sitedatabase eerst testen op een kopie van de sitedatabase.  

-   U moet het upgradeproces voor de sitedatabase testen omdat de sitedatabase mogelijk wordt gewijzigd wanneer u een site bijwerkt.  
-   Hoewel een upgradetest van de database niet is vereist, kunt u hiermee problemen voor de upgrade identificeren voordat deze de productiedatabase beïnvloeden.  
-   Een mislukte upgrade van de sitedatabase kan leiden tot een onbruikbare sitedatabase, waardoor u mogelijk een siteherstel moet uitvoeren om de functionaliteit te herstellen.  
-   Hoewel de sitedatabase door verschillende sites in een hiërarchie wordt gedeeld, moet u de database op elke site testen voordat u die site bijwerkt.  
-   Als u databasereplica's gebruikt voor beheerpunten op een primaire site, schakelt u replicatie uit voordat u de back-up van de sitedatabase maakt.  

Configuration Manager biedt geen ondersteuning voor de back-up van secundaire sites noch de testupgrade van een secundaire sitedatabase.  

Het uitvoeren van een testdatabase-upgrade op de productie-sitedatabase wordt niet ondersteund. Dit leidt tot een upgrade van de sitedatabase en kan tot gevolg hebben dat uw site onbruikbaar wordt.  

Zie [Test the site database upgrade](#bkmk_test)(Upgrade van de sitedatabase testen) voor meer informatie.  

**Opnieuw opstarten van de siteserver en iedere computer die als host fungeert voor een sitesysteemrol**:  
Dit wordt gedaan om ervoor te zorgen dat er geen acties van een recente installatie van updates of van vereisten en is een bedrijfsspecifiek intern proces.  

**Upgrade van sites uitvoeren**:  
U start op het hoogste niveau in de hiërarchie, voert u Setup.exe uit de bronmedia van System Center Configuration Manager.  

Nadat de upgrades op het bovenste siteniveau zijn voltooid, kunt u de upgrade uitvoeren van iedere onderliggende site. Voltooi de upgrade van elke site voordat u de volgende site bijwerkt.  

Totdat alle sites in uw hiërarchie een upgrade naar System Center Configuration Manager uitvoert, wordt uw hiërarchie draait in een modus van gemengde versies.  

Zie voor meer informatie over het uitvoeren van de upgrade [upgraden van sites](#bkmk_upgrade).  

### <a name="after-you-upgrade"></a>Nadat u een upgrade hebt uitgevoerd  
**Zelfstandige Configuration Manager-consoles upgraden**:  
Standaard bij het upgraden van een centrale beheersite of primaire site, de installatie ook worden bijgewerkt de Configuration Manager-console die is geïnstalleerd op de siteserver. U moet elke console die op een andere computer dan de siteserver is geïnstalleerd, echter handmatig bijwerken.  

> [!TIP]  
>  Sluit alle geopende consoles voordat u de upgrade uitvoert.  

Zie [System Center Configuration Manager-consoles installeren](../../../../core/servers/deploy/install/install-consoles.md) voor meer informatie.  

**Databasereplica's voor beheerpunten op primaire sites opnieuw configureren:**  
Als u databasereplica's voor beheerpunten op primaire sites gebruikt, moet u de databasereplica's verwijderen vóór de upgrade van de site. Na de upgrade van een primaire site configureert u de databasereplica voor beheerpunten opnieuw.   
Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md) voor meer informatie.  

**Configureer alle databaseonderhoudstaken die hebt uitgeschakeld vóór de upgrade opnieuw:**  
Als u databaseonderhoudstaken hebt uitgeschakeld op een site vóór de upgrade ([Referentie voor onderhoudstaken voor System Center Configuration Manager](../../../../core/servers/manage/reference-for-maintenance-tasks.md)), dient u deze taken opnieuw te configureren op de site met behulp van dezelfde instellingen die reeds waren ingesteld vóór de upgrade.  

**Upgrades uitvoeren voor clients**:  
Nadat alle sites zijn bijgewerkt naar System Center Configuration Manager, plant u om clients te upgraden.  

Bij de upgrade van een client wordt de huidige clientsoftware verwijderd en wordt de nieuwe clientsoftwareversie geïnstalleerd. Als u clients wilt upgraden, kunt elke methode gebruiken die door Configuration Manager wordt ondersteund.  

> [!TIP]  
>  Wanneer u de site op het hoogste niveau van een hiërarchie bijwerkt, wordt het clientinstallatiepakket op elk distributiepunt in de hiërarchie ook bijgewerkt. Bij de upgrade van een primaire site wordt het clientupgradepakket dat beschikbaar is van de primaire site, bijgewerkt.  

Zie [How to upgrade clients for Windows computers in System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) (Cients bijwerken voor Windows-computers in System Center Configuration Manager) voor informatie over het bijwerken van bestaande clients en het installeren van nieuwe clients.  

##  <a name="bkmk_considerations"></a> Overwegingen voor bijwerken  
**Automatische acties**:  
Wanneer u upgrade naar System Center Configuration Manager uitvoert, wordt de volgende acties automatisch uitgevoerd:  

-   De site voert een reset van de site uit, hetgeen betekent dat alle sitesysteemrollen opnieuw worden geïnstalleerd.  
-   Als de site een site op het hoogste niveau van een hiërarchie is, wordt het clientinstallatiepakket op elk distributiepunt in de hiërarchie bijgewerkt. De site werkt ook de standaard opstartinstallatiekopieën bij om de nieuwe Windows PE-versie te gebruiken die is opgenomen in Windows Assessment and Deployment Kit 10. De upgrade geldt echter niet voor bestaande media voor gebruik met implementatie van de installatiekopie.  
-   Als de site een primaire site is, wordt het clientupgradepakket voor die site bijgewerkt.  

**Handmatige acties voor de gebruiker met beheerdersrechten na een upgrade**   
Nadat u een site bijwerkt, moet u ervoor zorgen dat de volgende acties worden uitgevoerd:  

-   Zorg ervoor dat clients die aan elke primaire site zijn toegewezen, de clientsoftware voor de nieuwe versie upgraden en installeren.  
-   Upgrade elke Configuration Manager-console die verbinding maakt met de site en die wordt uitgevoerd op een computer die extern zijn van de siteserver  
-   Op primaire sites waar u databasereplica's voor beheerpunten gebruikt, configureert u de databasereplica's opnieuw.  
-   Nadat de upgrade van de site is uitgevoerd, moet u handmatig fysieke media bijwerken zoals ISO-bestanden voor cd's en dvd's of USB-flashstations, of voorgefaseerde media die worden gebruikt voor Windows To Go-implementaties of die worden verschaft aan hardwareleveranciers. Hoewel de site-upgrade de standaardopstartinstallatiekopieën worden bijgewerkt er kan geen upgrade uitvoeren voor deze mediabestanden of apparaten gebruikt extern aan Configuration Manager  
-   Plan het bijwerken van niet-standaard opstartinstallatiekopieën wanneer u de oorspronkelijke (oudere) versie van Windows PE niet nodig hebt.  

**Acties die invloed hebben op configuraties en instellingen**   
Wanneer een site wordt bijgewerkt naar System Center Configuration Manager, worden bepaalde configuraties en instellingen na de upgrade verloren of worden ingesteld op een nieuwe standaardconfiguratie. De volgende tabel bevat instellingen die verloren gaan of wijzigen, en biedt details om u te helpen ze te plannen tijdens een site-upgrade:  

-   **Software Center:**  
    De volgende Software Center-items worden opnieuw ingesteld op hun standaardwaarden:  
    -   **Werkinformatie** wordt opnieuw ingesteld naar kantooruren van **5.00 u** tot **22.00 u** van maandag tot en met vrijdag.  
    -   De waarde voor **Computeronderhoud** wordt ingesteld op **Software Center-activiteiten onderbreken wanneer mijn computer zich in de presentatiemodus bevindt**.  
    -   De waarde voor **Extern beheer** wordt ingesteld op de waarde in de clientinstellingen die aan de computer zijn toegewezen.  
-   **Planningen overzicht software-updates:**  
     Aangepaste overzichtsplanningen voor software-updates of software-updategroepen worden opnieuw ingesteld op de standaardwaarde van 1 uur. Nadat de upgrade is voltooid, stelt u de aangepaste overzichtswaarden opnieuw in op de vereiste frequentie.  

##  <a name="bkmk_test"></a> De upgrade van de sitedatabase testen  
De volgende informatie geldt alleen als u een eerdere versie, zoals System Center 2012 Configuration Manager naar System Center Configuration Manager upgraden.

Voordat u een site bijwerkt, test u een kopie van die site-database voor de upgrade.  

Als u wilt testen van de database voor een upgrade, eerst u een kopie van de sitedatabase naar een exemplaar van SQL Server die niet als voor een Configuration Manager-site host. De versie van SQL Server die u gebruikt om de databasekopie te hosten, moet een versie van SQL Server ondersteunt de versie van Configuration Manager dat de bron van het database-exemplaar.  

Nadat u de sitedatabase op de SQL Server-computer herstellen Voer vervolgens Setup van Configuration Manager vanuit de bronmediamap voor System Center Configuration Manager met de **/testdbupgrade** opdrachtregeloptie te gebruiken.  

-   Zie [Command-line options for Setup](../../../../core/servers/deploy/install/command-line-options-for-setup.md) (Opdrachtregelopties voor installatie) voor meer informatie over het maken en herstellen van een back-up van een sitedatabase.  
-   Zie de tabel in [Command-line options for Setup](../../../../core/servers/deploy/install/command-line-options-for-setup.md) (Opdrachtregelopties voor installatie) voor informatie over de opdrachtregeloptie **/TESTDBUPGRADE**.  
-   Zie het onderwerp [Ondersteuning voor SQL Server-versies voor System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md) voor meer informatie over de ondersteunde versies van SQL Server.  

> [!TIP]  
>  Als u Microsoft Intune met Configuration Manager integreert:  
>   
>  Wanneer u een testdatabase-upgrade uitvoert op en kopie van de sitedatabase die meer dan vijf dagen oud is, kunt u een van de volgende berichten ontvangen:  
>   
>  -   WARN: Upgrade forceert een volledige synchronisatie naar de cloud.  
>  -   FOUT: Database-upgrade forceert een volledige synchronisatie naar de cloud.  
>   
> Beide kunnen worden genegeerd tijdens het testen van een database-upgrade niet duiden op een fout of probleem met de test-upgrade. In plaats daarvan geven ze aan dat tijdens de daadwerkelijke upgrade, worden gegevens uit de **Cloud** databasereplicatiegroep kan synchroniseren met Microsoft Intune.  

Gebruik de volgende procedure op elke centrale beheersite en primaire site die u wilt bijwerken.  

#### <a name="to-test-a-site-database-for-upgrade"></a>Een sitedatabase testen voor een upgrade  

1.  Maak een kopie van de sitedatabase en herstel die kopie op een exemplaar van SQL Server dat dezelfde editie als uw sitedatabase gebruikt en die niet als host voor een Configuration Manager-site. Als de sitedatabase wordt uitgevoerd op een exemplaar van de Enterprise-editie van SQL Server, dient u de database dus te herstellen op een SQL Server-exemplaar waarop de Enterprise-editie van SQL Server wordt uitgevoerd.  

2.  Nadat u de databasekopie teruggezet, installatieprogramma uitvoeren vanaf de bronmedia voor System Center Configuration Manager. Wanneer u Setup wilt uitvoeren, gebruikt u de opdrachtregeloptie **/TESTDBUPGRADE** . Als het SQL Server-exemplaar dat de databasekopie host niet het standaardexemplaar is, moet u ook de opdrachtregelargumenten opgeven om het exemplaar aan te duiden dat de sitedatabasekopie host.  

     Stel dat u van plan bent om een sitedatabase met de databasenaam SMS_ABC bij te werken. U herstelt een kopie van deze sitedatabase naar een ondersteund exemplaar van SQL Server met de exemplaarnaam DBTest. Als u wilt een upgrade van deze kopie van de sitedatabase testen, gebruikt u de volgende opdrachtregel: **Setup.exe /TESTDBUPGRADE DBtest\CM_ABC**  

     U vindt Setup.exe op de volgende locatie op de bronmedia voor System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

3.  Op het exemplaar van SQL Server waarop u de database-upgrade test, bevat ConfigMgrSetup.log in de hoofdmap van het systeemstation informatie over de voortgang van de bewerking:  

    -   Als de testupgrade mislukt, lost u de fouten gerelateerd aan de upgradefout op, maakt u een nieuwe back-up van de sitedatabase en test u de upgrade van de nieuwe kopie van de sitedatabase.  
    -   Wanneer de upgrade lukt, kunt u de databasekopie verwijderen.  

        > [!NOTE]  
        >  U kunt de kopie van de sitedatabase die u gebruikt voor de testupgrade niet gebruiken als sitedatabase op een site.  

Wanneer u een kopie van de sitedatabase bijgewerkt, gaat u verder met het upgraden van de Configuration Manager-site en de sitedatabase.  

##  <a name="bkmk_upgrade"></a> Upgrade van sites uitvoeren  
Nadat u configuratie vóór de upgrade voor uw site hebt voltooid, test u de upgrade van de sitedatabase op een databasekopie en download vereiste bestanden en taalpakketten voor de versie van servicepack die u wilt installeren, bent u gereed voor upgrade van uw Configuration Manager-site.  

Wanneer u een site in een hiërarchie wilt bijwerken, moet u eerst de site op het hoogste niveau van de hiërarchie bijwerken. Deze site op het hoogste niveau is een centrale beheersite of een zelfstandige primaire site. Wanneer de upgrade van een centrale beheersite is voltooid, kunt u onderliggende primaire sites in elke volgorde bijwerken. Na de upgrade van een primaire site, kunt u die site onderliggende secundaire sites bijwerken of aanvullende primaire sites een upgrade uitvoert voordat u alle secundaire sites.  

Als u een centrale beheersite of primaire site upgraden, kunt u Setup uitvoert vanuit de bronmedia van System Center Configuration Manager. Voer Setup niet uit om secundaire sites bij te werken. In plaats daarvan kunt u de Configuration Manager-console een secundaire site bijwerken nadat u de upgrade van de bovenliggende primaire site hebt voltooid.  

Voordat u een site bijwerkt, sluit u de Configuration Manager-console die is geïnstalleerd op de siteserver tot nadat de site-upgrade is voltooid. Bovendien Sluit elke Configuration Manager-console die wordt uitgevoerd op andere computers dan de siteserver. U kunt de console weer verbinden als de site is bijgewerkt. Echter totdat u een upgrade uitvoert van een Configuration Manager-console naar de nieuwe versie van Configuration Manager, die console kan geen objecten en gegevens worden weergegeven die beschikbaar zijn in de nieuwe versie van Configuration Manager.  

Gebruik de volgende procedures voor het upgraden van Configuration Manager-sites:  

#### <a name="to-upgrade-a-central-administration-site-or-primary-site"></a>Een centrale beheersite of primaire site bijwerken  

1.  Controleer of de gebruiker die Setup uitvoert over de volgende beveiligingsrechten beschikt:  

    -   Lokale beheerdersrechten op de siteservercomputer.  
    -   Lokale beheerdersrechten op de databaseserver voor de externe site.    </br></br>

2.  Open Windows Verkenner op de siteservercomputer en blader naar  **&lt;ConfigMgSourceMedia\>\SMSSETUP\BIN\X64**.  

3.  Dubbelklik op **Setup.exe**. De wizard Setup van Configuration Manager wordt geopend.  

4.  Klik op de pagina **Voordat u begint** op **Volgende**.  

5.  Op de pagina **Aan de slag** selecteert u **Deze Configuration Manager-site bijwerken**en vervolgens klikt u op **Volgende**.  

6.  Klik op de pagina **Productcode** op **Volgende**.  

     Als u eerder de evaluatie van de Configuration Manager hebt geïnstalleerd, kunt u **Installeer de gelicentieerde versie van dit product**, en voer vervolgens de productcode voor de volledige installatie van Configuration Manager om te converteren van de site naar de volledige versie.  

     U begint met de oktober 2016-release van de basislijnmedia versie 1606 voor System Center Configuration Manager, kunt u de vervaldatum van uw Software Assurance overeenkomst opgeven. U hebt ook de mogelijkheid te geven de **Software Assurance vervaldatum** van uw gebruiksrechtovereenkomst handige eraan te herinneren dat u na die datum. Als u dit tijdens de installatie invoert, kunt u later uit binnen de Configuration Manager-console opgeven.

     >  [!NOTE]   
     >  Microsoft komt niet overeen voor de vervaldatum die u hebt ingevoerd en wordt deze datum niet gebruiken voor het valideren van licenties.  In plaats daarvan kunt u deze als een herinnering van de vervaldatum. Dit is nuttig omdat Configuration Manager periodiek controleert op nieuwe software-updates die worden aangeboden online zijn en de status van uw software assurance-licentie moet actueel zijn om in aanmerking voor het gebruik van deze aanvullende updates.    

     Zie voor meer informatie [licenties en vertakkingen voor System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

7.  Lees en accepteer de licentievoorwaarden op de pagina **Licentievoorwaarden voor Microsoft-software** en klik vervolgens op **Volgende**.  

8.  Lees en accepteer de licentievoorwaarden voor de vereiste software op de pagina **Vereiste licenties** en klik vervolgens op **Volgende**. Het installatieprogramma downloadt en installeert de software automatisch op sitesystemen of clients wanneer dit nodig is. U moet alle selectievakjes inschakelen voordat u doorgaat naar de volgende pagina.  

9. Geef op de pagina **Vereiste downloads** op of de meest recente vereiste herdistribueerbare bestanden, taalpakketten en de meest recente productupdates van internet moeten worden gebruikt of dat de eerder gedownloade bestanden volstaan. Klik vervolgens op **Volgende**. Als u eerder de bestanden had gedownload met behulp van de Setup Downloader, selecteert u **Eerder gedownloade bestanden gebruiken** en specificeert u de downloadmap. Zie voor meer informatie [Setup Downloader](/sccm/core/servers/deploy/install/setup-downloader).

    > [!NOTE]  
    >  Als u eerder gedownloade bestanden gebruikt, controleert u of het pad naar de downloadmap de recentste versie van de bestanden bevat.  

10. Bekijk op de pagina **Selectie van servertaal** welke talen momenteel zijn geïnstalleerd voor de site. Selecteer extra talen die beschikbaar op deze site voor de Configuration Manager-console en voor rapporten zijn ook talen wissen die u niet meer wilt ondersteunen op deze site en klik vervolgens op **volgende**. Engels wordt standaard geselecteerd en kan niet worden verwijderd.  

    > [!IMPORTANT]  
    >  Elke versie van Configuration Manager kan geen taalpakketten uit eerdere versies van Configuration Manager gebruiken. Als ondersteuning wilt inschakelen voor een taal op een Configuration Manager-site die u bijwerkt, moet u de versie van het taalpakket voor die nieuwe versie. Voor bijvoorbeeld tijdens de upgrade van System Center 2012 Configuration Manager naar System Center Configuration Manager als de System Center Configuration Manager-versie van een taalpakket niet beschikbaar met de vereiste bestanden die u hebt gedownload, ondersteuning voor worden die taal niet geïnstalleerd.  

11. Bekijk op de pagina **Selectie van clienttaal** welke talen momenteel zijn geïnstalleerd voor de site. Selecteer extra talen die op deze site beschikbaar zijn voor clientcomputers. U kunt ook talen wissen die u niet meer wilt ondersteunen op deze site. Geef op of alle clienttalen moeten worden ingeschakeld voor clients voor mobiele apparaten en klik vervolgens op **Volgende**. Engels wordt standaard geselecteerd en kan niet worden verwijderd.  

    > [!IMPORTANT]  
    >  Elke versie van Configuration Manager kan geen taalpakketten uit eerdere versies van Configuration Manager gebruiken. Als ondersteuning wilt inschakelen voor een taal op een Configuration Manager-site die u bijwerkt, moet u de versie van het taalpakket voor die nieuwe versie. Voor bijvoorbeeld tijdens de upgrade van System Center 2012 Configuration Manager naar System Center Configuration Manager als de System Center Configuration Manager-versie van een taalpakket niet beschikbaar met de vereiste bestanden die u hebt gedownload, ondersteuning voor worden die taal niet geïnstalleerd.  

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

3.  Vouw in de werkruimte **Beheer** **Siteconfiguratie**uit en klik vervolgens op **Sites**.  

4.  Selecteer de secundaire site die u wilt bijwerken en klik vervolgens op het tabblad **Start** in de groep **Site** op **Upgrade uitvoeren**.  

5.  Klik op **Ja** om te bevestigen en de secundaire site bij te werken.  

De secundaire site wordt op de achtergrond bijgewerkt. Nadat de upgrade is voltooid, kunt u de status in de Configuration Manager-console controleren. U doet dit door de server voor de secundaire site te selecteren en op het tabblad **Start** in de groep **Site** op **Installatiestatus weergeven**te klikken.  

##  <a name="BKMK_PostUpgrade"></a> Taken na de upgrade uitvoeren  
Wanneer u een site hebt bijgewerkt naar een nieuw servicepack, moet u mogelijk aanvullende taken uitvoeren om de upgrade te voltooien of de site opnieuw te configureren. Deze taken kunnen omvatten het upgraden van Configuration Manager-clients of Configuration Manager-consoles opnieuw inschakelen van databasereplica's voor beheerpunten of het herstellen van instellingen voor Configuration Manager-functionaliteit die u gebruikt en die niet bewaard is gebleven na de servicepackupgrade.  

**Bekende problemen voor secundaire sites:**  
- **Wanneer u een upgrade naar versie 1511:** Zodat clients op secundaire sites kunnen vinden van het beheerpunt van de secundaire site (proxy-beheerpunt), het beheerpunt handmatig toevoegen aan grensgroepen die ook de distributiepunten op de secundaire site.  

- **Wanneer u een upgrade naar versie 1606 of hoger:** Proxy-beheerpunten worden automatisch toegevoegd aan grensgroepen met distributiepunten op de secundaire site.
