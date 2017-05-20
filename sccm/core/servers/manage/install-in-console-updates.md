---
title: Console updates | Microsoft-documenten
description: System Center Configuration Manager worden gesynchroniseerd met de Microsoft-cloud ophalen van updates die u in de console kunt installeren.
ms.custom: na
ms.date: 4/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: 29a55948a1897e1345ba14ec685b9288a844feaa
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="install-in-console-updates-for-system-center-configuration-manager"></a>Updates binnen de console installeren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager worden gesynchroniseerd met de cloudservice van Microsoft om updates te downloaden. Vervolgens kunt u deze updates van de Configuration Manager-console installeren.

## <a name="get-available-updates"></a>Beschikbare updates downloaden
Alleen de updates die van toepassing zijn op uw infrastructuur en versie, worden gedownload en beschikbaar gesteld voor uw hiërarchie. Deze synchronisatie kan worden automatisch of handmatig, afhankelijk van hoe u de service connection point voor uw hiërarchie configureert:

-   In **onlinemodus**maakt het serviceverbindingspunt automatisch verbinding met de Microsoft-cloudservice en worden toepasselijke updates gedownload.  

     Standaard controleert Configuration Manager op nieuwe updates elke 24 uur. U kunt ook controleren op updates onmiddellijk door het kiezen van **controleren op Updates** in de **beheer** > **Updates en onderhoud** knooppunt van de Configuration Manager-console. (Voor versie 1702 dit knooppunt is onder **beheer** > **Cloudservices**.)

-   In **offlinemodus**, de service connection point geen verbinding maken met de cloudservice van Microsoft. U moet handmatig [gebruik het hulpprogramma voor Service-verbinding voor System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md) downloaden en vervolgens importeren beschikbare updates.  

> [!NOTE]  
>  Naast de updates die u tijdens de synchronisatie met Microsoft-cloudservice, out-of-band oplossingen die zijn geïnstalleerd met behulp van de [Update registratie Tool](http://technet.microsoft.com/library/mt691544.aspx) ook worden geïmporteerd in de console waar u kunt vervolgens selecteren kan worden geïnstalleerd.  

Nadat updates zijn gesynchroniseerd kunt u ze weergeven in de Configuration Manager-console gaat u naar de **beheer** > **Updates en onderhoud** knooppunt:  

-   Updates die u niet hebt geïnstalleerd, worden weergegeven als **Beschikbaar**.

-   Updates die u wel hebt geïnstalleerd, worden weergegeven als **Geïnstalleerd**.  Alleen de laatst geïnstalleerde update wordt weergegeven. U kunt ervoor kiezen de **geschiedenis** knop wordt weergegeven op het lint weergeven van eerder geïnstalleerde updates.



Voordat u de service connection point configureert, begrijpt en plan voor de extra worden gebruikt. De volgende doeleinden gebruiken hebben mogelijk invloed op hoe het configureren van deze sitesysteemrol:  

-   Het serviceverbindingspunt wordt gebruikt voor het uploaden van gebruiksgegevens over uw site. Deze informatie helpt de Microsoft-cloudservice bij het identificeren van de updates die beschikbaar zijn voor de huidige versie van uw infrastructuur. Zie voor meer informatie [diagnostische en gebruiksgegevens voor System Center Configuration Manager](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

-   De service connection point wordt gebruikt voor het beheren van apparaten met Microsoft Intune, en beheer van mobiele apparaten op de lokale Configuration Manager. Zie voor meer informatie [hybride mobiel Apparaatbeheer (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

Om beter te begrijpen wat gebeurt er wanneer updates worden gedownload, Zie:  

-   [Stroomdiagram - downloaden van updates voor System Center Configuration Manager](../../../core/servers/manage/download-updates-flowchart.md)

-   [Stroomdiagram - Update-replicatie voor System Center Configuration Manager](../../../core/servers/manage/update-replication-flowchart.md)  

## <a name="assign-permissions-to-view-and-manage-updates-and-features"></a>Machtigingen toewijzen aan weergeven en beheren van updates en functies
Als u wilt weergeven van updates in de console, een gebruiker moet worden toegewezen een beveiligingsrol voor op rollen gebaseerd beheer met de beveiliging klasse met naam **updatepakketten**. Deze klasse verleent toegang om te bekijken en beheren van updates in de Configuration Manager-console.    

**Informatie over de klasse Pakketten bijwerken:**  
Standaard maakt **Pakketten bijwerken** (SMS_CM_Updatepackages) deel uit van de volgende ingebouwde beveiligingsrollen met de onderstaande machtigingen:
 -  **Volledige beheerder** met de machtigingen **Wijzigen** en **Lezen** :
    -   Een gebruiker met deze beveiligingsrol is toegekend en toegang tot de **alle** beveiligingsbereik kan updates weergeven, installeren van updates en functies inschakelen tijdens de installatie en afzonderlijke functies in te schakelen na de update is geïnstalleerd.
    - Een gebruiker met deze beveiligingsrol is toegekend en toegang tot de **standaard** beveiligingsbereik kan updates weergeven, installeren van updates en functies inschakelen tijdens de installatie en functies weergeven na een update is geïnstalleerd. Maar deze gebruiker niet de functies inschakelen nadat de update is geïnstalleerd.

- **Alleen-lezenanalist** met **lees** machtigingen:
  -  Een gebruiker met deze beveiligingsrol is toegekend en toegang tot de **standaard** bereik kan updates weergeven, maar ze niet te installeren. Deze gebruiker kan ook functies weergeven na een update is geïnstalleerd, maar ze niet inschakelen.

**Machtigingen die vereist zijn voor updates en onderhoud:**   
  - Gebruik een account dat is toegewezen aan een beveiligingsrol die de klasse **Pakketten bijwerken** met beide machtigingen **Wijzigen** en **Lezen** omvat.
  - Het account moet worden toegewezen aan het bereik **Standaard** .

**Permissoins alleen updates te bekijken**:
  - Gebruik een account dat is toegewezen aan een beveiligingsrol die de klasse **Pakketten bijwerken** met alleen de machtiging **Lezen** omvat.
  - Het account moet worden toegewezen aan het bereik **Standaard** .

**Vereiste machtigingen voor functies inschakelen nadat updates zijn geïnstalleerd:**
  -  Gebruik een account dat is toegewezen aan een beveiligingsrol die de klasse **Pakketten bijwerken** met beide machtigingen **Wijzigen** en **Lezen** omvat.
  -  Het account moet worden toegewezen aan het bereik **Alles** .






##  <a name="bkmk_beforeinstall"></a> Voordat u een update binnen de console installeert  
 Bekijk de volgende stappen voordat u een update uit in de Configuration Manager-console installeert.  

###  <a name="bkmk_step1"></a>Stap 1: De controlelijst voor bijwerken door  
Bekijk de toepasselijke update controlelijst voor acties te ondernemen voordat u begint met de update:

- Een update naar 1606: Zie [controlelijst voor de installatie van update 1606](../../../core/servers/manage/checklist-for-installing-update-1606.md).  

- Een update naar 1610 van beide 1606: Zie [controlelijst voor de installatie van update 1610](../../../core/servers/manage/checklist-for-installing-update-1610.md).  

- Een update naar 1702 van 1606 of 1610: Zie [controlelijst voor de installatie van update 1702](../../../core/servers/manage/checklist-for-installing-update-1702.md).

###  <a name="bkmk_step2"></a>Stap 2: De upgrade van de database voordat u een update installeert testen  
De informatie in deze stap is van toepassing alleen wanneer u installeert een *bijwerken* voor een System Center Configuration Manager-site. Als u *upgraden* een System Center 2012 Configuration Manager-site voor System Center Configuration Manager Zie [upgrade van de sitedatabase testen](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager#a-namebkmktesta-test-the-site-database-upgrade).

Voordat u een nieuwe update in uw hiërarchie installeert, zoals 1610 bijwerken, kunt u de upgrade van uw sitedatabase testen. De naam van de opdrachtregeloptie te gebruiken die u gebruikt voor het testen van een update installeren op een back-up van uw sitedatabase is **testdbupgrade**.  

Als u een update installeert mislukt, hoeft u niet herstellen op een site. In plaats daarvan kunt u de installatie van updates opnieuw proberen. Ja, hoewel het testen van de upgrade van de database minder essentieel is dan in eerdere versies van het product zoals System Center 2012 Configuration Manager, nog steeds wordt aangeraden deze.


#### <a name="to-run-testdbupgrade-before-installing-an-update"></a>Testdbupgrade uitvoeren voordat u een update installeert  

1.  Ophalen van een reeks bronbestanden van de **CD. Meest recente** map van een site die wordt uitgevoerd op de versie die u van plan bent om te werken naar. Dit kan ertoe leiden dat u voor de eerste installatie van een site in een testomgeving of testomgeving met deze versie van System Center Configuration Manager.  

     De **CD. Meest recente** map voor een site is de bronbestanden voor die versie. U moet deze bronbestanden gebruiken voor het uitvoeren van de testupgrade van uw sitedatabase. Zie [De map CD.Latest voor System Center Configuration Manager](../../../core/servers/manage/the-cd.latest-folder.md) voor meer informatie.  

     Als uw site versie 1606 uitvoert en u wilt bijwerken naar 1610, moet u bijvoorbeeld een CD ophalen. Meest recente map van een site die al is bijgewerkt naar versie 1610. Doorgaans kunt u een nieuwe en tijdelijke site installeert in een testomgeving en die een upgrade naar versie 1610 voor het maken van de CD. Meest recente map met de vereiste bestanden.  

2.  Kopieer de CD. Meest recente map naar een locatie op de SQL Server-instantie die u gebruiken wilt voor het uitvoeren van de database-testupgrade.

3.  Maak een back-up van de sitedatabase die u wilt testen, upgrade en herstelt u een kopie van de database naar een exemplaar van SQL Server die niet als van een Configuration Manager-site host. De SQL Server-voort moet dezelfde versie van SQL Server gebruiken als uw sitedatabase.  

4.  Voer na het herstellen van de databasekopie **Setup** vanaf de CD. Meest recente map die u in uw omgeving lab of testen kopieerde. Wanneer u Setup wilt uitvoeren, gebruikt u de opdrachtregeloptie **/TESTDBUPGRADE** . Als het SQL Server-exemplaar dat de databasekopie host niet het standaardexemplaar is, moet u ook de opdrachtregelargumenten opgeven om het exemplaar aan te duiden dat de sitedatabasekopie host.  

     Stel dat u van plan bent om een sitedatabase met de databasenaam sms_abc bij te werken. U herstelt een kopie van deze sitedatabase naar een ondersteund exemplaar van SQL Server met de exemplaarnaam DBTest. Als u wilt testen van een upgrade van deze kopie van de sitedatabase, gebruik de volgende opdrachtregel: **Setup.exe/testdbupgrade DBtest\CM_ABC**  

     U vindt Setup.exe op de volgende locatie op het BRONmedium voor System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

5.  Op het exemplaar van SQL Server waarop u de database-upgrade test, bevat ConfigMgrSetup.log in de hoofdmap van het systeemstation informatie over de voortgang van de bewerking:  

     Als de testupgrade mislukt, herstel alle problemen die betrekking hebben op de upgradefout, maak een nieuwe back-up van de sitedatabase en test u de upgrade van de nieuwe kopie van de sitedatabase.  

     Wanneer de upgrade lukt, kunt u de databasekopie verwijderen.  

    > [!NOTE]  
    >  U kunt de kopie van de sitedatabase die u gebruikt voor de testupgrade niet gebruiken als sitedatabase op een site.  

###  <a name="bkmk_step3"></a>Stap 3: De prerequisite checker uitvoeren voordat u een update installeert  
Het wordt aangeraden de controle op vereisten voor een update uit te voeren voordat u deze update installeert. Als u de prerequisite checker uitvoert voordat u een update installeert:  

-   De updatebestanden worden gerepliceerd naar andere sites vóór de installatie van de update.  

-   De controle wordt automatisch opnieuw uitgevoerd wanneer u ervoor kiest om de update te installeren.  

Later, wanneer u de update hebt de optie voor het configureren van de update voor waarschuwingen voor vereisten negeren.  

#### <a name="to-run-the-prerequisite-checker-before-installing-an-update"></a>De controle van vereisten uitvoeren voordat u een update installeert  

1.  Ga in de Configuration Manager-console naar **beheer** > **Updates en onderhoud**.   

2.  Klik met de rechtermuisknop op het updatepakket waarvoor u de controle op vereisten wilt uitvoeren.  

3.  Kies **Controle van vereisten uitvoeren**.  

     Wanneer u de controle op vereisten uitvoert, wordt inhoud voor de update gerepliceerd naar onderliggende sites.  U kunt het bestand distmgr.log weergeven op de site server om te bevestigen dat inhoud met succes repliceert.  

4.  Om weer te geven de resultaten van de controle, in de Configuration Manager-console gaat u naar **bewaking** > **Updates en onderhoud Status** en zoek naar de vereiste status. U kunt ook het bestand ConfigMgrPrereq.log op de siteserver bekijken voor meer informatie.  



##  <a name="bkmk_install"></a> Updates binnen de console installeren  
 Wanneer u klaar bent voor vanuit de Configuration Manager-console updates installeren, begint u met de site op hoogste niveau van uw hiërarchie. Dit is de centrale beheersite of een zelfstandige primaire site.  

 Het is raadzaam dat u van plan bent om de update buiten kantooruren voor elke site te installeren. Het installatieproces van de update en de bijbehorende acties opnieuw installeren van site-onderdelen en sitesysteemrollen hebben dan de minimale invloed op uw zakelijke activiteiten.  

-   De update wordt automatisch gestart op onderliggende primaire sites nadat de installatie van de update is voltooid op de centrale beheersite. Dit is de standaard en aanbevolen proces. U kunt echter [windows voor siteservers Service](/sccm/core/servers/manage/service-windows) om te beheren wanneer updates in een primaire site wordt geïnstalleerd.  

-   Nadat de update van de bovenliggende primaire site voltooid is, moet u handmatig secundaire sites van in de Configuration Manager-console bijwerken. Het automatisch bijwerken van secundaire siteservers wordt niet ondersteund.  

-   Wanneer u een Configuration Manager-console nadat de site is bijgewerkt, wordt u gevraagd of u de console bijwerken.  

-  Nadat de siteserver heeft de installatie van een update voltooid, wordt deze automatisch alle toepasselijke sitesysteemrollen.  De enige belemmering hierop is voor distributiepunten. Als u een update installeert, alle distributiepunten niet opnieuw moet installeren en de verbinding verbreekt om bij te werken op hetzelfde moment. In plaats daarvan gebruikt de siteserver van de site-instellingen voor het distribueren van inhoud te distribueren van de update op een subset van distributiepunten op een tijdstip. Het resultaat is dat alleen bepaalde distributiepunten gaan offline om de update te installeren. Hiermee wordt de distributiepunten die nog niet begonnen om bij te werken of dat de update moet worden bewaard online en in staat om inhoud voor clients hebt voltooid.


###  <a name="bkmk_overview"></a> Overzicht van de installatie van een update binnen de console  
**1. Wanneer de installatie van updates wordt gestart**  
De wizard Updates wordt weergegeven waarin u een lijst ziet van de productgebieden waarop de update van toepassing is.  

-   Op de pagina **Algemeen** van de wizard kunt u **Waarschuwingen voor vereiste onderdelen**configureren.  
      -   De installatie van de update wordt altijd gestopt als een fout optreedt in de vereisten. U moet de fouten corrigeren voordat u kunt de installatie van updates met succes opnieuw. Zie [De installatie van een mislukte update opnieuw uitvoeren](#bkmk_retry) voor meer informatie.  

    -   Waarschuwingen voor vereisten kunnen ook de installatie van updates stoppen. U moet waarschuwingen oplossen voordat u de update-installatie opnieuw uit. Zie [De installatie van een mislukte update opnieuw uitvoeren](#bkmk_retry) voor meer informatie.  
    -   De optie **alle waarschuwingen voor vereisten negeren en installeer deze update ongeacht ontbrekende vereisten**, stelt u een voorwaarde voor de installatie van de update die waarschuwingen voor vereisten worden genegeerd. Hiermee wordt de installatie van de update om door te gaan. Als u deze optie niet selecteert, wordt de installatie van updates gestopt als er een waarschuwing wordt aangetroffen. Tenzij u de controle en vaste waarschuwingen voor vereisten voor een site eerder hebt uitgevoerd, raden we niet gebruik van deze optie.  

      In zowel de **beheer** en **bewaking** werkruimten, de Updates en onderhoud van knooppunt bevat een knop in het lint met de naam **waarschuwingen voor vereisten negeren**. Deze knop is alleen beschikbaar wanneer u een updatepakket is mislukt om de installatie als gevolg van waarschuwingen voor vereisten te voltooien. Bijvoorbeeld, als u een update installeert zonder de optie waarschuwingen voor vereisten negeren (uit in de Wizard Updates), en die installatie stopt bijwerken met een status van de vereiste Waarschuwing maar zonder fouten later kunt u **waarschuwingen voor vereisten negeren** van het lint voor het activeren van een automatische voortzetting van deze installatie van updates die vervolgens waarschuwingen voor vereisten worden genegeerd. Als u deze optie gebruikt, wordt de installatie van updates automatisch voortgezet na enkele minuten duren.



-   Wanneer een update van toepassing op Configuration Manager-client, wordt weergegeven met de optie voor het testen van de clientupdate met een beperkt aantal clients. Zie voor meer informatie [clientupgrades testen in een pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

**2. Tijdens de installatie van updates**  
Als onderdeel van de installatie van updates, Configuration Manager:  

-   Alle betrokken onderdelen, zoals sitesysteemrollen of de Configuration Manager-console installeert.  

-   Beheer van de updates op clients die zijn gebaseerd op selecties die u hebt aangebracht voor client haalbaarheidsonderzoek en voor [automatische clientupgrades](https://technet.microsoft.com/library/mt627885.aspx).  

-   Hoeft niet opnieuw te starten sitesysteemservers als onderdeel van de update (tenzij .NET is geïnstalleerd als onderdeel van een vereiste site system rollen).  

> [!TIP]  
>  Wanneer updates worden geïnstalleerd, werkt Configuration Manager ook de CD. Meest recente map. Deze map wordt gebruikt tijdens het herstel van een site.  

**3. De voortgang van de updates als ze installeren**  
U kunt de voortgang als volgt bewaken:  

-   In de Configuration Manager-console: **Beheer** > **Updates en onderhoud** knooppunt. Dit knooppunt geeft de installatiestatus weer voor alle updatepakketten.


-   In de Configuration Manager-console: **Bewaking** > **overzicht** > **Updates en onderhoud Status** knooppunt. Dit knooppunt bevat de status van de installatie van de updatepakket dat momenteel wordt geïnstalleerd.  

  De installatie van de update pack is onderverdeeld naar de volgende fasen voor het gemak van bewaking. Voor elke fase bevatten aanvullende informatie welke logboekbestand voor meer informatie weergeven.:  
    -   **Download** (deze fase geldt alleen voor de bovenste site waarop de service connection point-sitesysteemrol is geïnstalleerd.)
    -   **Replicatie**
    -   **Controle van vereisten**
    -   **Installatie**
    -   **Na de installatie** (deze fase is beschikbaar vanaf versie 1610.)

-   U ziet de **CMUpdate.log** in het bestand  **&lt;ConfigMgr_Installation_Directory > \Logs**  

**4. Wanneer de update-installatie is voltooid**  
Nadat de installatie van de update voor de eerste site is voltooid:  

-   Op onderliggende primaire sites wordt de update automatisch geïnstalleerd. Er is geen verdere actie vereist.  

-   Secundaire sites moeten handmatig worden bijgewerkt vanuit de Configuration Manager-console.
> [!TIP]
> Hoewel de versie van een secundaire site niet wordt weergegeven in de console, kunt u de Configuration Manager-SDK gebruiken om te bevestigen van de versie van een site. Zie [SMS_Site Server WMI-klasse](https://technet.microsoft.com/library/hh442832(CMSDK.16).aspx).


-   Uw hiërarchie draait in een modus van gemengde versies totdat alle sites in uw hiërarchie zijn bijgewerkt naar de nieuwe versie. Zie [Interoperabiliteit tussen verschillende versies van System Center Configuration Manager](../../../core/plan-design/hierarchy/interoperability-between-different-versions.md) voor meer informatie.  

**5.   Configuration Manager-consoles bijwerken**  
Wanneer een centrale beheersite of primaire site updates, moet ook elke Configuration Manager-console die verbinding met die site maakt bijwerken. U wordt gevraagd een console bijwerken:  

-   Wanneer u de console opent.  

-   Wanneer u gaat u naar een nieuw knooppunt in een geopende console.  

U wordt aangeraden de update onmiddellijk te installeren.  

Nadat de update van de console is voltooid, kunt u controleren of de versie van de console en site correct zijn. Ga naar **over System Center Configuration Manager** op de linkerbovenhoek van de console.  

###  <a name="bkmk_toptier"></a> De installatie van de update op de bovenste site starten  
Op de bovenste site van uw hiërarchie, in de Configuration Manager-console gaat u naar **beheer** > **Updates en onderhoud**, selecteer een **beschikbaar** bijwerken en klik vervolgens op **bijwerken Pack installeren**.  

###  <a name="bkmk_secondary"></a> De installatie van de update op een secundaire site starten  
Nadat een secundaire sites bovenliggende primaire site is bijgewerkt, kunt u de secundaire site vanuit de Configuration Manager-console bijwerken.  Hiervoor gebruikt u de **Wizard Upgrade van secundaire Site**.  

1.  Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**, selecteer de site die u wilt bijwerken en klik vervolgens op de startpagina tabblad, in de **Site** groep, kiest u **Upgrade**.  

2.  Klik op **Ja** om de update van de secundaire site te starten.  

Selecteer de secundaire server voor het controleren van de installatie van de update op een secundaire site. Klik vervolgens op de **Start** tabblad, in de **Site** groep, kiest u **installatiestatus tonen**. U kunt ook de kolom **Versie** toevoegen aan de console-weergave, zodat u de versie van elke secundaire site kunt bekijken.  

Nadat een secundaire site is bijgewerkt, als de status in de console wordt niet vernieuwd of stelt de update is mislukt, kunt u de **installatie opnieuw uit** optie. Deze optie de update voor een secundaire site die heeft de update is geïnstalleerd, maar wordt de console bijwerken van de status niet opnieuw worden geïnstalleerd.


##  <a name="bkmk_retry"></a> De installatie van een mislukte update opnieuw uitvoeren  
Wanneer een update niet kan worden geïnstalleerd, Controleer de feedback is die in de console om te identificeren oplossingen voor waarschuwingen en fouten. U kunt ook het bestand ConfigMgrPrereq.log op de siteserver bekijken voor meer informatie. Voordat u de installatie van een update opnieuw proberen, u moet Corrigeer de fouten en waarschuwingen moet oplossen.  

Wanneer u klaar bent voor de installatie van een update opnieuw uit, selecteer de mislukte update en vervolgens een optie van toepassing. De update opnieuw installatiegedrag, is afhankelijk van het knooppunt waar u het opnieuw starten en de optie voor opnieuw proberen dat u gebruikt.  

1.  **De installatie voor de hiërarchie opnieuw uitvoeren:**  
U kunt de installatie van een update voor de gehele hiërarchie opnieuw uitvoeren wanneer deze update een van de volgende statussen heeft:  

    -   Vereistencontrole voltooid met een of meer waarschuwingen en de optie voor waarschuwingen voor vereisten negeren is niet ingesteld in de Wizard updates. (De waarde van de update voor **heeft waarschuwing negeren** in de **Updates en onderhoud** knooppunt **Nee**.)   
    -   De vereiste is mislukt    
    -   De installatie is mislukt
    -   De replicatie van de inhoud naar de site is mislukt   

    Ga naar **beheer** > **Updates en onderhoud**, selecteert u de update en kies een van de volgende:  

    -   **Probeer** - tijdens het uitvoeren van **probeer** van dit knooppunt de update wordt gestart opnieuw geïnstalleerd en wordt automatisch waarschuwingen voor vereisten negeren. Ook wordt de inhoud voor de update opnieuw gerepliceerd als de replicatie eerder is mislukt.
    - **Waarschuwingen voor vereisten negeren** -vanaf versie 1606, als de update stopt vanwege een waarschuwing installeren, u kunt vervolgens **waarschuwingen voor vereisten negeren**. Met deze actie gaat de installatie van de update verder (na enkele minuten) en wordt de optie gebruikt voor het negeren van waarschuwingen voor vereisten.   

2.  **De installatie voor de site opnieuw uitvoeren:**  
 U kunt de installatie van een update voor een specifieke site opnieuw uitvoeren wanneer deze update een van de volgende statussen heeft:  

    -   Vereistencontrole voltooid met een of meer waarschuwingen en kunt u waarschuwingen voor vereisten negeren is niet ingesteld in de Wizard updates (de updates waarde voor **heeft waarschuwing negeren** is in de Updates en onderhoud knooppunt **Nee**.)  
    -   De vereiste is mislukt    
    -   De installatie is mislukt    

    Ga naar **Bewaking** > **Overzicht** > **Status siteonderhoud**, selecteer de update en klik op een van de volgende opties:

       - **Probeer** - tijdens het uitvoeren van **probeer** van dit knooppunt u de installatie van de update op alleen die site opnieuw starten. In tegenstelling tot actief **probeer** van de **Updates en onderhoud** knooppunt deze opnieuw worden waarschuwingen voor vereisten niet genegeerd.
       -    **Waarschuwingen voor vereisten negeren** -vanaf versie 1606, als de update stopt vanwege een waarschuwing weergegeven installeren, klikt u vervolgens op **waarschuwingen voor vereisten negeren**. Met deze actie gaat de installatie van de update verder (na enkele minuten) en wordt de optie gebruikt voor het negeren van waarschuwingen voor vereisten.

##  <a name="bkmk_after"></a> Nadat een op site een update is geïnstalleerd  
Gebruik de volgende controlelijst om algemene taken en configuraties die zijn aangebracht nadat een site is bijgewerkt te voltooien.   

**Bevestig de replicatie van site-naar-site actief is:** Ga naar de volgende locaties weergeven van de status en ervoor zorgen dat gegevens worden gerepliceerd in de Configuration Manager-console:  

-   **Bewaking** > **Overzicht** > **Sitehiërarchie**  

-   **Bewaking** > **Overzicht** > **Databasereplicatie**  

Zie voor meer informatie [controleren-hiërarchie en de replicatie van de infrastructuur in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) en [over de Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA).  

 **Bevestig dat siteservers en externe sitesysteemservers opnieuw hebt opgestart (indien nodig):** Controleer de site-infrastructuur en zorg ervoor dat van toepassing siteservers en sitesysteemservers (externe van de siteserver) zijn opnieuw gestart.  Dit is normaal gesproken alleen wanneer de Configuration Manager installeert .NET als een vereiste voor een sitesysteemrol verwacht.  

 **Zelfstandige Configuration Manager-consoles bijwerken:** Zorg ervoor dat alle externe Configuration Manager-consoles bijwerken naar dezelfde versie. U wordt gevraagd een console bij te werken wanneer:  

-   U gaat u naar een nieuw knooppunt in de console.  

-   U opent de console.

**Databasereplica's voor beheerpunten op primaire sites opnieuw configureren:** Als u Databasereplica's voor beheerpunten op primaire sites gebruikt, moet u de Databasereplica's verwijderen voordat u de site bijwerkt. Nadat u een primaire site hebt bijgewerkt, configureert u de databasereplica voor beheerpunten opnieuw. Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md) voor meer informatie.  

**Configureer alle databaseonderhoudstaken die u uitgeschakeld hebt vóór de update opnieuw:** Als u de database uitgeschakeld [onderhoudstaken voor System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) configureren op een site vóór de update van deze taken op de site. Gebruikt u dezelfde instellingen die reeds ingesteld vóór de update waren.  

**Clients upgraden:** Zie [How to upgrade clients for Windows computers in System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) (Cients bijwerken voor Windows-computers in System Center Configuration Manager) voor informatie over het bijwerken van bestaande clients en het installeren van nieuwe clients.  

**Aanvullende configuraties:** Bekijk de wijzigingen die u hebt gemaakt voordat u de update gestart en herstel die configuraties op uw sites en hiërarchie.  

##  <a name="bkmk_options"></a> Optionele functies van updates inschakelen  
Wanneer u een update installeert die een of meer optionele functies bevat, hebt u de mogelijkheid om die functies in uw hiërarchie in te schakelen.  U kunt dus op het moment dat de update is geïnstalleerd, of u kunt later terug naar de console en de optionele functies inschakelen.

Als u wilt weergeven van functies en hun status, in de console navigeert u naar **beheer** > **Updates en onderhoud** > **functies**.

Als een functie niet optioneel is, wordt automatisch geïnstalleerd en wordt niet weergegeven in de **functies** knooppunt.  


Wanneer u een nieuwe functie of een voorlopige versie functie inschakelt, moet de Configuration Manager-hiërarchie manager (HMAN) de wijziging verwerken voordat deze functie beschikbaar is. Verwerking van de wijziging is vaak onmiddellijke kan, maar het duren tot 30 minuten duren, afhankelijk van de HMAN-mailverwerkingscyclus. Nadat de wijziging wordt verwerkt, moet u de console opnieuw opstarten voordat u de nieuwe gebruikersinterface aan die functies gerelateerde kunt weergeven.


##  <a name="bkmk_prerelease"></a> Functies van voorlopige versies van updates gebruiken
Pre-release functies zijn kenmerken die zijn opgenomen in de huidige vertakking voor vroege te testen in een productieomgeving. Deze functies niet beschouwd productie gereed, maar kunnen worden gebruikt in uw productieomgeving. Zie voor meer informatie over pre-release-functies, zoals het inschakelen van deze in uw omgeving, [pre-release functies](/sccm/core/servers/manage/pre-release-features).             


## <a name="known-issues"></a>Bekende problemen

###  <a name="bkmk_faq"></a>Waarom zie ik bepaalde updates niet in mijn console?  
 Als u een specifieke update (of er updates) in de console na een geslaagde synchronisatie met de Microsoft-cloudservice vinden kunt, kan dit zijn omdat:  

-   Voor de update is een configuratie vereist die niet wordt gebruikt in uw infrastructuur of uw huidige versie van het product voorziet niet in een vereiste voor het ontvangen van de update.  

     Als u van mening bent dat u de vereiste configuratie of u voldoen aan andere vereisten voor een update ontbreekt, controleert u dat uw serviceverbindingspunt in onlinemodus is. Gebruik vervolgens de **controleren op Updates** optie de **Updates en onderhoud** knooppunt af te dwingen een selectievakje.  Als u zich in de offlinemodus bevindt, moet u het hulpprogramma voor serviceverbindingen gebruiken om handmatig te synchroniseren met de Microsoft-cloudservice.  

-   Uw account beschikt niet over de juiste op rollen gebaseerd beheer-machtigingen updates weergeven in de Configuration Manager-console.

    Zie [Machtigingen voor het weergeven en beheren van updates en functies](../../../core/servers/manage/install-in-console-updates.md#assign-permissions-to-view-and-manage-updates-and-features) in dit onderwerp voor informatie over vereiste machtigingen voor het weergeven van updates en het inschakelen van functies vanuit de console.

### <a name="why-do-i-see-two-updates-for-version-1610"></a>Waarom zie ik twee updates voor versie 1610
Wanneer u updates in de console bekijkt, ziet u mogelijk twee updates 1610 versie installeren. Deze updates zijn verschillende datums. Dit gebeurt wanneer een van de volgende omstandigheden:   
-    U een eerdere versie (zoals 1606) hebt geïnstalleerd nadat versie 1610 beschikbaar zijn

-    U hiërarchie versie 1511 of 1602 wordt uitgevoerd en zijn niet versie 1606 downloaden

Er zijn twee update releases voor versie 1610 omdat deze update is opnieuw uitgebracht na enkele kleine wijzigingen in sommige binaire bestand zijn aangebracht. Deze wijzigingen hebben geen invloed op de functionaliteit van Configuration Manager of de update.

Bij beide updates beschikbaar in de console zijn, wordt u aangeraden dat u de update installeren op de meest recente datum. Echter, aangezien beide updates dezelfde functionaliteit bieden als u een van deze al is geïnstalleerd niet hoeft u verdere actie te ondernemen.
-    Als u de oudere update eerder is geïnstalleerd, hoeft u niet de update installeren op de nieuwere datum. Echter als u de nieuwere update na het installeren van de eerste update installeert, de binaire bestanden in het geding wordt bijgewerkt, maar er is geen aanvullende wijziging optreedt, en geen verdere acties te ondernemen nodig zijn.

-    Als u de nieuwste update eerder is geïnstalleerd en installeer vervolgens de update met de oudere datum, is geen verdere actie nodig. Dit komt doordat de nieuwere binaire bestanden die u al hebt geïnstalleerd niet worden overschreven door die dezelfde binaire bestanden van de oorspronkelijke update.

