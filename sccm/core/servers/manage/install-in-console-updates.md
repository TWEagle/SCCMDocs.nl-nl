---
title: Console-updates
titleSuffix: Configuration Manager
description: System Center Configuration Manager worden gesynchroniseerd met de Microsoft cloud ophalen van updates die u vanuit de console installeren kunt.
ms.custom: na
ms.date: 09/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
caps.latest.revision: "36"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 081935ebb3ef2cc12d2023d86c0b68bbd816f2f3
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="install-in-console-updates-for-system-center-configuration-manager"></a>Updates binnen de console installeren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager worden gesynchroniseerd met de Microsoft-cloudservice om updates te downloaden. Vervolgens kunt u deze updates van de Configuration Manager-console installeren.

## <a name="get-available-updates"></a>Beschikbare updates downloaden
Alleen de updates die van toepassing zijn op uw infrastructuur en versie, worden gedownload en beschikbaar gesteld voor uw hiërarchie. Deze synchronisatie kan automatisch of handmatig, afhankelijk van hoe u het serviceverbindingspunt voor uw hiërarchie configureert zijn:

-   In **onlinemodus**maakt het serviceverbindingspunt automatisch verbinding met de Microsoft-cloudservice en worden toepasselijke updates gedownload.  

     Standaard controleert Configuration Manager op nieuwe updates elke 24 uur. U kunt ook controleren op updates direct door te kiezen **controleren op Updates** in de **beheer** > **Updates en onderhoud** knooppunt van de Configuration Manager-console. (Voorafgaand aan versie 1702, wordt dit knooppunt is onder **beheer** > **Cloudservices**.)

-   In **offlinemodus**, het serviceverbindingspunt geen verbinding met de Microsoft-cloudservice. Om te downloaden en vervolgens importeren van beschikbare updates [het hulpprogramma voor serviceverbindingen gebruiken voor System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md).  

> [!NOTE]  
>   U kunt de out-of-band fixes naar de console importeren. Gebruik hiervoor de [hulpprogramma registratie bijwerken](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes). Deze oplossingen out-of-band vormen een aanvulling op de updates die u krijgt wanneer u met de Microsoft Cloud-service synchroniseren.


Nadat de updates worden gesynchroniseerd, kunt u deze bekijken in de Configuration Manager-console door te gaan naar de **beheer** > **Updates en onderhoud** knooppunt:  

-   Updates die u niet hebt geïnstalleerd, worden weergegeven als **Beschikbaar**.

-   Updates die u wel hebt geïnstalleerd, worden weergegeven als **Geïnstalleerd**.  Alleen de laatst geïnstalleerde update weergegeven. U kunt de **geschiedenis** knop in het lint weergeven van eerder geïnstalleerde updates.



Voordat u het serviceverbindingspunt configureert, begrijpt en plannen voor de aanvullende mogelijkheden ervan. De volgende doeleinden gebruiken kunnen invloed hebben op hoe het configureren van deze sitesysteemrol:  

-   Het serviceverbindingspunt wordt gebruikt voor het uploaden van gebruiksgegevens over uw site. Deze informatie helpt de Microsoft-cloudservice bij het identificeren van de updates die beschikbaar zijn voor de huidige versie van uw infrastructuur. Zie voor meer informatie [diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

-   Het serviceverbindingspunt wordt gebruikt voor het beheren van apparaten met Microsoft Intune en het gebruik van beheer van mobiele apparaten op de lokale Configuration Manager. Zie voor meer informatie [hybride mobile device management (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

Om beter te begrijpen wat gebeurt er wanneer updates worden gedownload, Zie:  

-   [Stroomdiagram: updates downloaden voor System Center Configuration Manager](../../../core/servers/manage/download-updates-flowchart.md)

-   [Stroomdiagram - Update-replicatie voor System Center Configuration Manager](../../../core/servers/manage/update-replication-flowchart.md)  

## <a name="assign-permissions-to-view-and-manage-updates-and-features"></a>Machtigingen toewijzen aan weergeven en beheren van updates en functies
Als updates wilt weergeven in de console, moet een gebruiker een beveiligingsrol Rolgebaseerd beheer met de klasse security hebben **updatepakketten**. Deze klasse verleent toegang tot het weergeven en beheren van updates in de Configuration Manager-console.    

**Informatie over de klasse Pakketten bijwerken:**  
Standaard maakt **Pakketten bijwerken** (SMS_CM_Updatepackages) deel uit van de volgende ingebouwde beveiligingsrollen met de onderstaande machtigingen:
 -  **Volledige beheerder** met de machtigingen **Wijzigen** en **Lezen** :
    -   Een gebruiker met deze beveiligingsrol en toegang tot de **alle** beveiligingsbereik kunt weergeven en installeren van updates. De gebruiker kan ook functies inschakelen tijdens de installatie en afzonderlijke functies inschakelen nadat de update is geïnstalleerd.
    - Een gebruiker met deze beveiligingsrol en toegang tot de **standaard** beveiligingsbereik kunt weergeven en installeren van updates. De gebruiker kan ook functies inschakelen tijdens de installatie en functies bekijken nadat een update is geïnstalleerd. Maar deze gebruiker niet de functies inschakelen nadat de update is geïnstalleerd.

- **Alleen-lezenanalist** met **lees** machtigingen:
  -  Een gebruiker met deze beveiligingsrol en toegang tot de **standaard** bereik kan updates weergeven maar ze niet zijn geïnstalleerd. Deze gebruiker kan ook functies bekijken nadat een update is geïnstalleerd, maar ze niet inschakelen.

**Machtigingen die vereist zijn voor updates en onderhoud:**   
  - Gebruik een account dat is toegewezen aan een beveiligingsrol die de klasse **Pakketten bijwerken** met beide machtigingen **Wijzigen** en **Lezen** omvat.
  - Het account moet worden toegewezen aan het bereik **Standaard** .

**Machtigingen voor alleen updates weergeven**:
  - Gebruik een account dat is toegewezen aan een beveiligingsrol die de klasse **Pakketten bijwerken** met alleen de machtiging **Lezen** omvat.
  - Het account moet worden toegewezen aan het bereik **Standaard** .

**Machtigingen vereist voor het inschakelen van functies nadat updates zijn geïnstalleerd:**
  -  Gebruik een account dat is toegewezen aan een beveiligingsrol die de klasse **Pakketten bijwerken** met beide machtigingen **Wijzigen** en **Lezen** omvat.
  -  Het account moet worden toegewezen aan het bereik **Alles** .



##  <a name="bkmk_beforeinstall"></a> Voordat u een update binnen de console installeert  
 Bekijk de volgende stappen uit voordat u een update van de Configuration Manager-console installeert.  

###  <a name="bkmk_step1"></a>Stap 1: Bekijk de controlelijst voor bijwerken  
Controleer de betreffende controlelijst voor bijwerken acties moet uitvoeren voordat u de update start:

- Bijwerken naar 1606: Zie [controlelijst voor het installeren van update 1606](../../../core/servers/manage/checklist-for-installing-update-1606.md).  

- Bijwerken van beide 1606 naar 1610: Zie [controlelijst voor het installeren van update 1610](../../../core/servers/manage/checklist-for-installing-update-1610.md).  

- Bijwerken van 1606 of 1610 naar 1702: Zie [controlelijst voor het installeren van update 1702](../../../core/servers/manage/checklist-for-installing-update-1702.md).

<!-- Removed as update guidance 6/6/2017. The Test DB Upgrade details are no longer recommended nor required. They live on in a new topic for customers who still want to use them. -->

###  <a name="step-2-run-the-prerequisite-checker-before-installing-an-update"></a>Stap 2: De prerequisite checker uitvoeren voordat u een update installeert  
Het wordt aangeraden de controle op vereisten voor een update uit te voeren voordat u deze update installeert. Als u de prerequisite checker uitvoert voordat u een update installeert:  

-   De updatebestanden worden gerepliceerd naar andere sites voordat u de update installeert.  

-   De controle op vereisten automatisch opnieuw uitgevoerd wanneer u ervoor kiest om de update te installeren.  

> [!NOTE]   
> Wanneer u een controle van vereisten start en vervolgens weer de status van de **installatie** fase actief lijkt te zijn, maar de update niet daadwerkelijk wordt geïnstalleerd. Voor het uitvoeren van de controle van vereisten, het updateproces pakt het pakket uit de Inhoudsbibliotheek en plaatst deze in een map voor gefaseerde installatie waarbij de huidige controles van vereisten kunnen worden geopend.  Dit hetzelfde proces wordt uitgevoerd als u een update installeert. Daarom wordt de installatie weergegeven als wordt uitgevoerd. Alleen de *updatepakket uitpakken* stap wordt weergegeven in de categorie van de installatie.  

Later, wanneer u de update installeert, kunt u de update voor het negeren van waarschuwingen voor vereisten configureren.  

#### <a name="to-run-the-prerequisite-checker-before-installing-an-update"></a>De controle van vereisten uitvoeren voordat u een update installeert  

1.  Ga in de Configuration Manager-console naar **beheer** > **Updates en onderhoud**.   

2.  Klik met de rechtermuisknop op het updatepakket dat u wilt de controle op vereisten uitvoeren.  

3.  Kies **Controle van vereisten uitvoeren**.  

     Wanneer u de controle op vereisten uitvoert, wordt inhoud voor de update gerepliceerd naar onderliggende sites.  U kunt het bestand distmgr.log weergeven op de site om te controleren of de inhoud wordt gerepliceerd.  

4.  Om weer te geven de resultaten van de controle, in de Configuration Manager-console gaat u naar **bewaking** > **Updates en onderhoudsstatus** en zoekt u de status van de vereisten. U kunt ook het bestand ConfigMgrPrereq.log op de siteserver bekijken voor meer informatie.  



##  <a name="bkmk_install"></a> Updates binnen de console installeren  
 Wanneer u gereed om te installeren vanuit de Configuration Manager-console updates bent, begint u met de bovenste site van uw hiërarchie. Dit is de centrale beheersite of een zelfstandige primaire site.  

 Het is raadzaam dat u de update installeert buiten kantooruren voor elke site om te voorkomen dat de gevolgen van zakelijke activiteiten. Dit is omdat de update-installatie kan onder andere acties zoals Siteonderdelen en sitesysteemrollen opnieuw te installeren.  

-   De update wordt automatisch gestart op onderliggende primaire sites nadat de installatie van de update is voltooid op de centrale beheersite. Dit is de standaardinstelling en aanbevolen proces. U kunt echter [Service van windows voor siteservers](/sccm/core/servers/manage/service-windows) om te bepalen wanneer een primaire site updates installeert.  

-   Secundaire sites uit binnen de Configuration Manager-console handmatig bijwerken nadat de update van de bovenliggende primaire site voltooid is. Het automatisch bijwerken van secundaire siteservers wordt niet ondersteund.  

-   Wanneer u een Configuration Manager-console gebruikt nadat de site is bijgewerkt, wordt u gevraagd de console bij te werken.  

-  Nadat de siteserver wordt installatie van een update is voltooid, worden alle toepasselijke sitesysteemrollen automatisch bijgewerkt.  Hoewel alleen is bedoeld voor distributiepunten. Wanneer u een update installeert, alle distributiepunten niet opnieuw te installeren en om bij te werken op hetzelfde moment offline gaan. In plaats daarvan gebruikt de siteserver van de site-instellingen voor het distribueren van inhoud voor het distribueren van de update op een subset van distributiepunten op een tijdstip. Het resultaat is dat alleen bepaalde distributiepunten gaan offline om de update te installeren. Distributiepunten die niet begonnen met het bijwerken of dat de update hebt uitgevoerd, blijven online en kunnen leveren van inhoud aan clients.


###  <a name="bkmk_overview"></a> Overzicht van de installatie van een update binnen de console  
**1. Wanneer de update-installatie wordt gestart**  
De wizard Updates wordt weergegeven waarin u een lijst ziet van de productgebieden waarop de update van toepassing is.  

-   Op de pagina **Algemeen** van de wizard kunt u **Waarschuwingen voor vereiste onderdelen**configureren.  
      -   De installatie van de update wordt altijd gestopt als een fout optreedt in de vereisten. Fouten oplossen voordat u kunt de installatie van update opnieuw. Zie [De installatie van een mislukte update opnieuw uitvoeren](#bkmk_retry) voor meer informatie.  

    -   Waarschuwingen voor vereisten kunnen ook de installatie van updates stoppen. Waarschuwingen oplossen voordat u de installatie van de update opnieuw uitvoeren. Zie voor meer informatie [installatie van een mislukte update opnieuw uitvoeren](#bkmk_retry).  
    -   De optie **waarschuwingen voor vereisten negeren en deze update installeren ongeacht ontbrekende vereisten** stelt u een voorwaarde voor de installatie van de update die waarschuwingen voor vereisten worden genegeerd. Hiermee wordt de update-installatie om door te gaan. Als u deze optie niet selecteert, wordt de installatie van de update gestopt wanneer een waarschuwing is opgetreden. Tenzij u eerder controle van vereisten en vaste waarschuwingen voor vereisten voor een site hebt uitgevoerd, raden we niet gebruik van deze optie.  

      In zowel de **beheer** en **bewaking** werkruimten, het knooppunt Updates en onderhoud omvat een knop in het lint genaamd **waarschuwingen over vereisten negeren**. Deze knop is alleen beschikbaar wanneer u een updatepakket mislukt om de installatie als gevolg van waarschuwingen voor vereisten te voltooien. Bijvoorbeeld, u een update installeert zonder de optie voor het negeren van waarschuwingen voor vereisten (van de wizard Updates). Installatie van de update stopt met een status van de vereiste Waarschuwing maar zonder fouten. U kunt later **waarschuwingen over vereisten negeren** vanuit het lint voor het activeren van een automatische voortzetting van de installatie van deze update waarbij waarschuwingen voor vereisten worden genegeerd. Als u deze optie gebruikt, wordt de installatie van de update automatisch voortgezet na een paar minuten.



-   Wanneer een update van toepassing op Configuration Manager-client, krijgt u de optie voor het testen van de clientupdate met een beperkte set clients. Zie voor meer informatie [clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

**2. Tijdens de installatie van updates**  
Als onderdeel van de update-installatie Configuration Manager:  

-   Opnieuw installeren beïnvloede onderdelen, zoals sitesysteemrollen of de Configuration Manager-console.  

-   Updates voor clients op basis van de selecties die u hebt gemaakt voor de clientproef en voor beheert [automatische clientupgrades](https://technet.microsoft.com/library/mt627885.aspx).  

-   Wordt niet opnieuw opgestart sitesysteemservers als onderdeel van de update tenzij .NET is geïnstalleerd als onderdeel van een vereiste voor sitesysteemrollen.  

> [!TIP]  
>  Wanneer updates worden geïnstalleerd, wordt ook de CD in Configuration Manager bijgewerkt. Meest recente map. Deze map wordt gebruikt tijdens het herstel van een site.  

**3. De voortgang van de updates bewaken tijdens de installatie van**  
U kunt de voortgang als volgt bewaken:  

-   In de Configuration Manager-console: **Beheer** > **Updates en onderhoud** knooppunt. Dit knooppunt geeft de installatiestatus weer voor alle updatepakketten.


-   In de Configuration Manager-console: **Bewaking** > **overzicht** > **Updates en onderhoudsstatus** knooppunt. Dit knooppunt geeft de installatiestatus van de updatepakket dat momenteel wordt geïnstalleerd.  

    Installeren van het updatepakket is onderverdeeld naar de volgende fasen voor bewaking gemakkelijker te maken. Aanvullende gegevens bevatten voor elke fase, welke logboekbestand voor meer informatie weergeven:  
    -   **Download** (deze fase geldt alleen voor de bovenste site waarop de service connection-site is geïnstalleerd.)   

    -   **Replicatie**   

    -   **Controle van vereisten**   

    -   **Installatie**    

    -   **Na de installatie** ([taken na de installatie](#post-installation-tasks) beschikbaar zijn te beginnen met versie 1610.)  

-   U vindt de **CMUpdate.log** bestanden per  **&lt;ConfigMgr_Installation_Directory > \Logs**  

**4. Wanneer de update-installatie is voltooid**  
Nadat de installatie van de update voor de eerste site is voltooid:  

-   Onderliggende primaire sites de update automatisch geïnstalleerd. Er is geen verdere actie vereist.  

-   Secundaire sites moeten handmatig worden bijgewerkt vanuit de Configuration Manager-console.
> [!TIP]
> Hoewel de versie van een secundaire site niet wordt weergegeven in de console, kunt u de Configuration Manager-SDK gebruiken om te bevestigen dat de versie van een site. Zie [SMS_Site Server WMI-klasse](https://technet.microsoft.com/library/hh442832(CMSDK.16).aspx).


-   Uw hiërarchie draait in een modus van gemengde versies totdat alle sites in uw hiërarchie zijn bijgewerkt naar de nieuwe versie. Zie [Interoperabiliteit tussen verschillende versies van System Center Configuration Manager](../../../core/plan-design/hierarchy/interoperability-between-different-versions.md) voor meer informatie.  

**5.   Configuration Manager-consoles bijwerken**  
Nadat een centrale beheersite of primaire site is bijgewerkt, moet ook elke Configuration Manager-console die verbinding met die site maakt bijwerken. U wordt gevraagd een console bijwerken:  

-   Wanneer u de console opent.  

-   Wanneer u gaat naar een nieuw knooppunt in een geopende console.  

U wordt aangeraden de update onmiddellijk te installeren.  

Nadat de update van de console is voltooid, kunt u controleren of de versie van de console en site correct zijn. Ga naar **over System Center Configuration Manager** op de linkerbovenhoek van de console.  

###  <a name="bkmk_toptier"></a> De installatie van de update op de bovenste site starten  
Op de bovenste site van uw hiërarchie, in de Configuration Manager-console gaat u naar **beheer** > **Updates en onderhoud**, selecteer een **beschikbaar** bijwerken en klik vervolgens op **updatepakket installeren**.  

###  <a name="bkmk_secondary"></a> De installatie van de update op een secundaire site starten  
Nadat een secundaire site bovenliggende primaire site is bijgewerkt, kunt u de secundaire site vanuit de Configuration Manager-console bijwerken.  Hiervoor gebruikt u de **Wizard Upgrade van secundaire Site**.  

1.  Ga in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**, selecteer de site die u wilt bijwerken, en klik vervolgens op de startpagina tabblad, in de **Site** groep, kiest u **Upgrade**.  

2.  Klik op **Ja** om de update van de secundaire site te starten.  

Selecteer de secundaire siteserver voor het controleren van de installatie van de update op een secundaire site. Klik op de **Start** tabblad, in de **Site** groep, kiest u **installatiestatus tonen**. U kunt ook de kolom **Versie** toevoegen aan de console-weergave, zodat u de versie van elke secundaire site kunt bekijken.  

Na een secundaire site is updates, als de status in de console niet worden vernieuwd of de update is mislukt stelt, gebruikt u de **installatie opnieuw uitvoeren** optie. Deze optie de update voor een secundaire site die heeft de update is geïnstalleerd, maar zorgt ervoor dat de console bijwerken van de status niet opnieuw worden geïnstalleerd.

### <a name="post-installation-tasks"></a>Taken na de installatie
Vanaf versie 1610, kunt u informatie over de taken na de installatie weergeven.

Wanneer een site een update is geïnstalleerd, zijn er verschillende taken die pas beginnen kunnen nadat de update-installatie op de siteserver is voltooid. Hier volgt een lijst van de taken na de installatie die essentieel voor de site-en hiërarchie zijn. Omdat ze essentieel zijn, worden ze actief bewaakt. Aanvullende taken die niet rechtstreeks worden bewaakt, bevatten de installatie van sitesysteemrollen. Selecteer om te geven de status van de taken kritieke na de installatie, **na de installatie** taak bij de bewaking van de installatie van de update voor een site.

Niet alle taken voltooid onmiddellijk. Sommige taken start niet totdat de installatie van de update is voltooid voor elke site. Nieuwe functionaliteit die u verwacht kan daarom worden uitgesteld totdat deze taken worden voltooid. Bijvoorbeeld, omdat de nieuwe functies inschakelen start niet totdat alle sites update-installatie voltooien, nieuwe functies mogelijk niet meer zichtbaar gedurende een bepaalde periode.

De taken na de installatie zijn onder andere:

-   **SMS Executive-service installeren**
  -   Kritieke service die wordt uitgevoerd op de siteserver.
  -   Opnieuw installeren van deze service moet snel worden voltooid.


-   **SMS_DATABASE_NOTIFICATION_MONITOR onderdeel installeren**
  -   Kritieke site onderdeel thread van SMS Executive-service.
  -   Opnieuw installeren van deze service moet snel worden voltooid.


-   **SMS_HIERARCHY_MANAGER onderdeel installeren**
  -   Kritieke site-component die wordt uitgevoerd op de siteserver.
  -   Verantwoordelijk voor het opnieuw installeren van sitesysteemrollen op sitesysteemservers.  De status van afzonderlijke site system rol herinstallatie weergegeven niet.
  -   Opnieuw installeren van deze service moet snel worden voltooid.


-   **SMS_REPLICATION_CONFIGURATION_MONITOR onderdeel installeren**
  -   Kritieke site-component die wordt uitgevoerd op de siteserver.
  -   Opnieuw installeren van deze service moet snel worden voltooid.


-   **SMS_POLICY_PROVIDER onderdeel installeren**
  -   Kritieke siteonderdeel dat alleen op primaire sites werkt.
  -   Opnieuw installeren van deze service moet snel worden voltooid.


-   **Replicatie-initialisatie bewaking**   
  -   Hiermee worden weergegeven op alleen de centrale beheersite en de onderliggende primaire sites.
  -   Afhankelijk van de SMS_REPLICATION_CONFIGURATION_MONITOR.
  -   Snel moet worden voltooid.


-   **Het bijwerken van Configuration Manager-Client preproductie-pakket**    
  -   U ziet nu zelfs wanneer client preproductie (ook wel clientproef genoemd) niet is ingeschakeld voor gebruik.
  -   Start niet totdat alle sites in de hiërarchie klaar bent met het installeren van de update.


-   **Client-map op de siteserver wordt bijgewerkt**
  -   Dit wordt niet weergegeven als u de client in een preproductieverzameling gebruiken.  
  -   Snel moet worden voltooid.


-   **Bijwerken van Configuration Manager-clientpakket**
  -   Dit wordt niet weergegeven als u de client in een preproductieverzameling gebruiken.  
  -   Is voltooid nadat de update voor alle sites installeren.  


-   **Functies inschakelen**
  -   U ziet nu alleen op de bovenste site van de hiërarchie.
  -   Start niet totdat alle sites in de hiërarchie klaar bent met het installeren van de update.
  -   Afzonderlijke functies worden niet weergegeven.


##  <a name="bkmk_retry"></a> De installatie van een mislukte update opnieuw uitvoeren  
Wanneer een update niet kan worden geïnstalleerd, bekijkt u de feedback in de console om oplossingen voor waarschuwingen en fouten te identificeren. U kunt ook het bestand ConfigMgrPrereq.log op de siteserver bekijken voor meer informatie. Voordat u de installatie van een update opnieuw uitvoert, moet u moet fouten oplossen en los waarschuwingen.  

> [!TIP]  
> Als een update heeft problemen bij het downloaden of repliceren, kunt u de [update opnieuw instellen van hulpprogramma](/sccm/core/servers/manage/update-reset-tool). Dit hulpprogramma is beschikbaar via de sites waarop versie 1706 uitgevoerd of hoger.

Wanneer u klaar bent voor de installatie van een update opnieuw uitvoeren, selecteert u de mislukte update en kies vervolgens een optie die van toepassing. De werking van de update-installatie opnieuw proberen, is afhankelijk van het knooppunt waar u het opnieuw starten en de nieuwe pogingen-optie die u gebruikt.  

1.  **De installatie voor de hiërarchie opnieuw uitvoeren:**  
U kunt de installatie van een update voor de gehele hiërarchie opnieuw uitvoeren wanneer deze update een van de volgende statussen heeft:  

    -   Controle van vereisten is voltooid met een of meer waarschuwingen en de optie voor het negeren van waarschuwingen voor vereisten is niet ingesteld in de Wizard Update. (De waarde van de update voor **waarschuwingen voor vereisten negeren** in de **Updates en onderhoud** knooppunt **Nee**.)   
    -   De vereiste is mislukt    
    -   De installatie is mislukt
    -   De replicatie van de inhoud naar de site is mislukt   

    Ga naar **beheer** > **Updates en onderhoud**, selecteer de update en kies vervolgens een van de volgende opties:  

    -   **Probeer** - tijdens het uitvoeren van **probeer** vanuit dit knooppunt, installatie van de update opnieuw gestart en worden waarschuwingen over vereisten automatisch genegeerd. Inhoud voor de update ook opnieuw gerepliceerd als replicatie eerder is mislukt.
    - **Waarschuwingen over vereisten negeren** -vanaf versie 1606, als de installatie van de update stopt vanwege een waarschuwing, u kunt vervolgens **waarschuwingen over vereisten negeren**. Met deze actie gaat de installatie van de update verder (na enkele minuten) en wordt de optie gebruikt voor het negeren van waarschuwingen voor vereisten.   

2.  **De installatie voor de site opnieuw uitvoeren:**  
 U kunt de installatie van een update voor een specifieke site opnieuw uitvoeren wanneer deze update een van de volgende statussen heeft:  

    -   Controle van vereisten is voltooid met een of meer waarschuwingen en optie voor het negeren van waarschuwingen voor vereisten is niet ingesteld in de Wizard Update. (De waarden van de updates voor **waarschuwingen voor vereisten negeren** in het knooppunt Updates en onderhoud is **Nee**.)  
    -   De vereiste is mislukt    
    -   De installatie is mislukt    

    Ga naar **bewaking** > **overzicht** > **Status siteonderhoud**, selecteer de update en klik vervolgens op een van de volgende opties:

       - **Probeer** - tijdens het uitvoeren van **probeer** vanuit dit knooppunt, u de installatie van de update alleen voor die site opnieuw starten. In tegenstelling tot uitgevoerd **probeer** van de **Updates en onderhoud** knooppunt, deze opnieuw worden waarschuwingen voor vereisten niet genegeerd.
       -    **Waarschuwingen over vereisten negeren** -vanaf versie 1606, als de update stopt vanwege een waarschuwing wilt installeren, klikt u vervolgens op **waarschuwingen over vereisten negeren**. Met deze actie gaat de installatie van de update verder (na enkele minuten) en wordt de optie gebruikt voor het negeren van waarschuwingen voor vereisten.

##  <a name="bkmk_after"></a> Nadat een op site een update is geïnstalleerd  
Gebruik de volgende controlelijst om uit te voeren algemene taken en configuraties die zijn aangebracht nadat een site is bijgewerkt.   

**Controleer of site-naar-site-replicatie actief:** Ga naar de volgende locaties weergeven van de status en ervoor te zorgen dat de replicatie is actief in de Configuration Manager-console:  

-   **Bewaking** > **Overzicht** > **Sitehiërarchie**  

-   **Bewaking** > **Overzicht** > **Databasereplicatie**  

Zie voor meer informatie [hiërarchie- en replicatie-infrastructuur bewaken in System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) en [over de Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA).  

 **Bevestig dat siteservers en externe sitesysteemservers opnieuw zijn opgestart (indien nodig):** Controleer uw site-infrastructuur en zorg ervoor dat toepasselijke siteservers en sitesysteemservers zijn opnieuw gestart. Siteservers opnieuw normaal gesproken alleen wanneer de Configuration Manager .NET als een vereiste voor een sitesysteemrol installeert.  

 **Zelfstandige Configuration Manager-consoles bijwerken:** Zorg ervoor dat alle externe Configuration Manager-consoles bijwerken naar dezelfde versie. U wordt gevraagd een console bij te werken wanneer:  

-   Gaat u naar een nieuw knooppunt in de console.  

-   U opent de console.

**Databasereplica's voor beheerpunten op primaire sites opnieuw configureren:** Als u Databasereplica's voor beheerpunten op primaire sites gebruikt, moet u de Databasereplica's verwijderen voordat u de site bijwerkt. Nadat u een primaire site hebt bijgewerkt, configureert u de databasereplica voor beheerpunten opnieuw. Zie [Databasereplica's voor beheerpunten voor System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md) voor meer informatie.  

**Configureer alle databaseonderhoudstaken die u uitgeschakeld hebt vóór de update opnieuw:** Als u de database [onderhoudstaken](../../../core/servers/manage/maintenance-tasks.md) op een site voordat u de update installeert, moet u deze taken op de site opnieuw configureren. Gebruik dezelfde instellingen die ingesteld vóór de update waren.  

**Clients bijwerken:** Zie voor informatie [clients voor Windows-computers in System Center Configuration Manager bijwerken](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

**Aanvullende configuraties:** Bekijk de wijzigingen aangebracht voordat u de update gestart en herstel vervolgens die configuraties op uw sites en hiërarchie.  

##  <a name="bkmk_options"></a> Optionele functies van updates inschakelen  
Wanneer een update een of meer optionele functies bevat, hebt u de mogelijkheid om in te schakelen die functies in uw hiërarchie.  U kunt functies inschakelen wanneer de update is geïnstalleerd, of u kunt later terugkeren naar de console en de optionele functies inschakelen.

Als u wilt weergeven van beschikbare functies en hun status, in de console gaat u naar **beheer** > **Updates en onderhoud** > **functies**.

Wanneer een functie niet optioneel is, deze wordt automatisch geïnstalleerd en niet wordt weergegeven in de **functies** knooppunt.  


Wanneer u een nieuwe functie of het onderdeel van de voorlopige versie inschakelt, moet de Configuration Manager-hiërarchie manager (HMAN) de wijziging verwerken voordat deze functie beschikbaar wordt. Verwerking van de wijziging is vaak onmiddellijke, maar duurt maximaal 30 minuten duren, afhankelijk van de HMAN verwerkingscyclus. Nadat de wijziging wordt verwerkt, moet u de console opnieuw opstarten voordat u de nieuwe gebruikersinterface die betrekking hebben op deze functie kunt weergeven.


##  <a name="bkmk_prerelease"></a> Functies van voorlopige versies van updates gebruiken
Functies van evaluatieversies zijn opgenomen in de huidige vertakking voor vroege testdoeleinden in een productieomgeving. U kunt deze functies gebruiken in uw productieomgeving, maar ze worden niet beschouwd als productie gereed. Meer informatie over [functies van evaluatieversies](/sccm/core/servers/manage/pre-release-features), met inbegrip van hoe u kunt ze inschakelen in uw omgeving.             


## <a name="known-issues"></a>Bekende problemen

###  <a name="bkmk_faq"></a>Waarom zie ik bepaalde updates niet in mijn console?  
 Als u kunt een specifieke update niet in de console na een synchronisatie met de Microsoft-cloudservice vinden, is dit mogelijk doordat:  

-   Voor de update is een configuratie vereist die niet wordt gebruikt in uw infrastructuur of uw huidige versie van het product voorziet niet in een vereiste voor het ontvangen van de update.  

     Als u van mening bent dat u de vereiste configuraties en -vereisten voor een ontbrekende update hebt, moet u controleren of uw serviceverbindingspunt in de onlinemodus bevindt. Gebruik vervolgens de **controleren op Updates** optie in de **Updates en onderhoud** knooppunt om af te dwingen een controle.  Als u zich in de offlinemodus bevindt, moet u het hulpprogramma voor serviceverbindingen gebruiken om handmatig te synchroniseren met de Microsoft-cloudservice.  

-   Uw account beschikt niet over de juiste op rollen gebaseerd beheer-machtigingen voor het weergeven van updates in de Configuration Manager-console.

    Zie [Machtigingen voor het weergeven en beheren van updates en functies](../../../core/servers/manage/install-in-console-updates.md#assign-permissions-to-view-and-manage-updates-and-features) in dit onderwerp voor informatie over vereiste machtigingen voor het weergeven van updates en het inschakelen van functies vanuit de console.

### <a name="why-do-i-see-two-updates-for-version-1610"></a>Waarom zie ik twee updates voor versie 1610?
Wanneer u updates in de console bekijkt, ziet u mogelijk twee updates 1610 versie installeren. Deze updates hebben verschillende datums. Beide weergegeven wanneer een van de volgende voorwaarden voldaan wordt:   
-   U hebt een oudere versie (zoals 1606) geïnstalleerd nadat versie 1610 beschikbaar zijn geworden

-   Uw hiërarchie versie 1511 of 1602 wordt uitgevoerd en u niet kunnen downloaden versie 1606 zijn

Er zijn twee update releases voor versie 1610 omdat deze update is opnieuw uitgebracht na enkele kleine wijzigingen in sommige binaire bestand zijn aangebracht. Deze wijzigingen hebben geen invloed op de functionaliteit van Configuration Manager of de update.

Wanneer beide updates beschikbaar in de console zijn, wordt u aangeraden dat u de update installeren op de meest recente datum. Echter, omdat beide updates dezelfde functionaliteit bieden als u een van beide al hebt geïnstalleerd niet hoeft u verdere actie te ondernemen.
-   Als u eerder de oudere update hebt geïnstalleerd, hoeft u niet de update te installeren met de nieuwere datum. Echter als u de nieuwere update na het installeren van de eerste update installeert, wordt de betreffende binaire bestanden bijgewerkt. Er zijn geen extra wijziging optreedt, en zijn geen verdere actie te ondernemen nodig.

-   Als u de nieuwste update eerder is geïnstalleerd en installeer vervolgens de update op de oudere datum, is geen verdere actie nodig. Dit komt doordat de nieuwere binaire bestanden die u al hebt geïnstalleerd niet worden overschreven door de dezelfde binaire bestanden van de oorspronkelijke update.
