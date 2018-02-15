---
title: Technische Preview 1802 | Microsoft Docs
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1802 voor System Center Configuration Manager.
ms.custom: na
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4884a2d3-13ce-44e5-88c4-a66dc7ec6014
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 83648c791117dd537968e8c0b0d71203f14f1075
ms.sourcegitcommit: e15516983883a4dd002c4bdd114147b04b811021
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2018
---
# <a name="capabilities-in-technical-preview-1802-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1802 voor System Center Configuration Manager

Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1802 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. 

Bekijk [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview) voordat u deze versie van de technical preview installeert. Dit artikel familiarizes u met de algemene vereisten en beperkingen voor het gebruik van een technical preview hoe tussen versies en hoe u feedback kunt bijwerken.     


<!--  Known Issues Template   
## Known Issues in this Technical Preview:
-   **Issue Name**. Details
    Workaround details.
-->
## <a name="known-issues-in-this-technical-preview"></a>Bekende problemen in deze Technical Preview
-   **Bijwerken naar een nieuwe preview-versie mislukt wanneer u een siteserver in de passieve modus hebt**. Als u hebt een [primaire siteserver in de passieve modus](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), en vervolgens u de passieve modus siteserver verwijderen moet voordat u bijwerkt naar deze nieuwe preview-versie. Nadat de site de update is voltooid, kunt u de passieve modus siteserver opnieuw installeren.

  Verwijderen van de siteserver van de passieve modus:
  1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie**  >  **Servers en sitesysteemrollen**, en selecteer vervolgens de passieve modus-siteserver.
  2. In de **sitesysteemrollen** deelvenster met de rechtermuisknop op de **siteserver** rol, en kies vervolgens **rol verwijderen**.
  3. Met de rechtermuisknop op de siteserver van de passieve modus, en kies vervolgens **verwijderen**.
  4. Nadat de siteserver verwijdert, op de primaire siteserver van de actieve service opnieuw starten de **CONFIGURATION_MANAGER_UPDATE**.
<!--sms 489412-->


</br>

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  


## <a name="transition-endpoint-protection-workload-to-intune-using-co-management"></a>Overgang Endpoint Protection werkbelasting voor Intune met CO-management    
<!-- 1357365 -->
In deze release kunt u nu de Endpoint Protection-werkbelasting uit Configuration Manager met Intune overstappen na het inschakelen van CO-beheer. Om de overgang van de werkbelasting van de Endpoint Protection, gaat u naar de eigenschappenpagina mede management en de schuifknop te verplaatsen van Configuration Manager **proef** of **alle**. Zie voor meer informatie [mede management voor Windows 10-apparaten](/sccm/core/clients/manage/co-management-overview).


 
## <a name="configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups"></a>Windows leveringsoptimalisatie voor het gebruik van Configuration Manager-grensgroepen configureren
<!-- 1324696 -->
U grensgroepen Configuration Manager gebruiken om te definiëren en inhoudsdistributie regelen tussen het bedrijfsnetwerk en naar externe kantoren. [Windows leveringsoptimalisatie](/windows/deployment/update/waas-delivery-optimization) is een cloud-gebaseerde, peer-to-peer-technologie voor het delen van inhoud tussen Windows 10-apparaten. U start in deze release, leveringsoptimalisatie voor het gebruik van uw grensgroepen bij het delen van inhoud tussen peers configureren. Een nieuwe client-instelling past de grens groeps-id als de levering van optimalisatie-id op de client. Wanneer de client met de cloudservice leveringsoptimalisatie communiceert, gebruikt deze id peers met de gewenste inhoud vinden. 

### <a name="prerequisites"></a>Vereisten
- Leveringsoptimalisatie is alleen beschikbaar op Windows 10-clients

### <a name="try-it-out"></a>Probeer het nu!
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. In de Configuration Manager-console **beheer** werkruimte **clientinstellingen** knooppunt maken van een aangepast clientinstellingenbeleid apparaat.
2. Selecteer de nieuwe **leveringsoptimalisatie** groep.
3. Schakel de instelling **gebruik Configuration Manager-Grensgroepen voor levering optimalisatie groeps-ID**.

Zie voor meer informatie de **groep** modus-optie voor levering in [leveringsoptimalisatie-instellingen](/windows/deployment/update/waas-delivery-optimization#group-id).



## <a name="windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway"></a>Takenreeks Windows 10 in-place upgrade via cloud management gateway
<!-- 1357149 -->

Het Windows 10- [in-place upgrade takenreeks](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version) biedt nu ondersteuning voor implementatie op internet gebaseerde clients beheerd via de [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway). Deze mogelijkheid kunnen externe gebruikers gemakkelijker upgraden naar Windows 10 zonder verbinding maken met het bedrijfsnetwerk. 

Zorg ervoor dat alle inhoud waarnaar wordt verwezen door de takenreeks in-place upgrade wordt gedistribueerd naar een [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point). Apparaten kunnen de takenreeks anders niet uitvoeren.

Wanneer u een takenreeks voor upgraden implementeert, gebruikt u de volgende instellingen:
- **Takenreeks mag worden uitgevoerd voor de client op Internet**, op het tabblad gebruikerservaring van de implementatie.
- **Alle inhoud lokaal downloaden voordat de takenreeks wordt gestart**, op het tabblad distributiepunten van de implementatie. Andere opties zoals **inhoud lokaal downloaden wanneer nodig is voor de actieve takenreeks** werken niet in dit scenario. De engine voor takenreeksen is momenteel niet mogelijk om inhoud te verkrijgen van een cloud-distributiepunt. Configuration Manager-client moet de inhoud van het cloud-distributiepunt downloaden voordat de takenreeks wordt gestart.
- (*Optioneel*) **vooraf downloaden van inhoud voor deze takenreeks**, op het tabblad Algemeen van de implementatie. Zie voor meer informatie [vooraf cache-inhoud configureren](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).



## <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Verbeteringen in de takenreeks Windows 10 in-place upgrade
<!-- 1357425 -->
De standaard taak sequence-sjabloon voor een upgrade ter plekke van Windows 10 bevat nu extra groepen met aanbevolen acties om toe te voegen voor en na het upgradeproces. Deze acties gelden veel klanten die met succes apparaten naar Windows 10 upgraden. 

### <a name="new-groups-under-prepare-for-upgrade"></a>Nieuwe groepen onder **voorbereiden voor Upgrade**
- **Accu controleert**: Stappen in deze groep om te controleren of de computer met behulp van de accu of power bekabelde toevoegen. Deze actie is vereist voor een aangepast script of het hulpprogramma voor het uitvoeren van deze controle.
- **Netwerk/bekabelde verbinding controles**: Voeg stappen toe in deze groep om te controleren of de computer is verbonden met een netwerk en is niet via een draadloze verbinding. Deze actie is vereist voor een aangepast script of het hulpprogramma voor het uitvoeren van deze controle.
- **Niet-compatibele toepassingen verwijderen**: Voeg stappen toe in deze groep te verwijderen van alle toepassingen die niet compatibel met deze versie van Windows 10 zijn. De methode voor het verwijderen van een toepassing verschilt. Als de toepassing gebruikmaakt van Windows Installer, kopieert u de **programma voor verwijderen** vanaf de opdrachtregel van de **programma's** tabblad op Windows Installer eigenschappen van het implementatietype van de toepassing. Voeg vervolgens een **opdrachtregel uitvoeren** stap in deze groep met de opdrachtregel voor verwijdering programma. Bijvoorbeeld: </br>`msiexec /x {150031D8-1234-4BA8-9F52-D6E5190D1CBA} /q`</br> 
- **Verwijderen van niet-compatibele stuurprogramma's**: Voeg stappen toe in deze groep te verwijderen van stuurprogramma's die niet compatibel met deze versie van Windows 10 zijn.
- **Beveiliging van derden verwijderen/onderbreken**: Stappen in deze groep te verwijderen of onderbreken van derden beveiligingsprogramma's, zoals antivirus toevoegen.
   - Als u van een derde schijf versleuteling programma gebruikmaakt, geeft u bijbehorende stuurprogramma versleuteling voor Windows Setup uit met de **/ReflectDrivers** [opdrachtregeloptie](/windows-hardware/manufacture/desktop/windows-setup-command-line-options). Voeg een [Takenreeksvariabele instellen](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) stap in de takenreeks wordt uitgevoerd in deze groep. De takenreeksvariabele ingesteld op **OSDSetupAdditionalUpgradeOptions**. De waarde instelt op **/ReflectDriver** met het pad naar het stuurprogramma. Dit [actie takenreeksvariabele](/sccm/osd/understand/task-sequence-action-variables#upgrade-operating-system) voegt u de Windows Setup vanaf de opdrachtregel die wordt gebruikt door de takenreeks wordt uitgevoerd. Neem contact op met de softwareleverancier voor elke extra hulp bij dit proces.

### <a name="new-groups-under-post-processing"></a>Nieuwe groepen onder **na verwerking**
- **Stuurprogramma's op basis van setup toepassen**: Voeg stappen toe in deze groep setup-stuurprogramma's (.exe) van pakketten installeren.
- **Beveiliging van derden installeren of inschakelen**: Voeg stappen toe in deze groep te installeren of programma's van derden, beveiliging, zoals antivirus inschakelen. 
- **Standaard-Windows-apps en koppelingen instellen**: Voeg stappen toe in deze groep Windows standaard-apps en bestandskoppelingen instellen. Een referentiecomputer met de gewenste app koppelingen eerst voorbereiden. Voer vervolgens de volgende opdrachtregel om te exporteren: </br>`dism /online /Export-DefaultAppAssociations:"%UserProfile%\Desktop\DefaultAppAssociations.xml"`</br>Het XML-bestand aan een pakket toevoegt. Voeg vervolgens een [opdrachtregel uitvoeren](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) stap in deze groep. Geef het pakket met het XML-bestand en geef vervolgens de volgende opdrachtregel: </br>`dism /online /Import-DefaultAppAssociations:DefaultAppAssocations.xml`</br> Zie voor meer informatie [exporteren of importeren koppelingen standaard](/windows-hardware/manufacture/desktop/export-or-import-default-application-associations).
- **Aanpassingen en persoonlijke instellingen toepassen**: Voeg stappen toe in deze groep toe te passen Start menu-aanpassingen, zoals programmagroepen indelen. Zie voor meer informatie [aanpassen van het startscherm](/windows-hardware/manufacture/desktop/customize-the-start-screen).

### <a name="additional-recommendations"></a>Extra aanbevelingen
- Windows-documentatie te lezen [upgrade fouten kunt oplossen door Windows 10](/windows/deployment/upgrade/resolve-windows-10-upgrade-errors). In dit artikel bevat ook gedetailleerde informatie over het bijwerkproces.
- Op de standaard **gereedheid controleren** stap, schakelt u **minimale vrije schijfruimte (MB) garanderen**. De waarde instelt op ten minste **16384** (16 GB) voor een 32-bits besturingssysteem upgradepakket of **20480** (20 GB) voor 64-bits. 
- Gebruik de **SMSTSDownloadRetryCount** [ingebouwde takenreeksvariabele](/sccm/osd/understand/task-sequence-built-in-variables) te downloaden beleid voor opnieuw proberen. Momenteel standaard zal de client opnieuw tweemaal te gebruiken. Deze variabele is ingesteld op twee (2). Als uw clients zich niet op een bekabeld bedrijfsnetwerk verbinding, helpen extra pogingen de client beleid verkrijgen. Met deze variabele zorgt ervoor dat er geen negatieve neveneffect dan vertraagde fout als het beleid niet kan downloaden.<!-- 501016 --> Verhoogt ook de **SMSTSDownloadRetryDelay** variabele van de standaardwaarde van 15 seconden.
- Voer een beoordeling inline-compatibiliteit. 
   - Toevoegen van een tweede **besturingssysteem bijwerken** stap vroeg in de **voorbereiden voor Upgrade** groep. Naam *Upgradebeoordeling*. Geef het upgradepakket voor dezelfde en schakelt u de optie voor het **uitvoeren van Windows-installatiecompatibiliteitsscan zonder dat de upgrade gestart**. Schakel **Doorgaan bij fout** op het tabblad Opties. 
   - Volg deze onmiddellijk *Upgradebeoordeling* stap, het toevoegen van een **opdrachtregel uitvoeren** stap. Geef de volgende opdrachtregel:</br> `cmd /c exit %_SMSTSOSUpgradeActionReturnCode%`</br>Op de **opties** tabblad, voeg de volgende voorwaarde toe: </br>`Task Sequence Variable _SMSTSOSUpgradeActionReturnCode not equals 3247440400` </br>Deze retourcode is het decimale equivalent van MOSETUP_E_COMPAT_SCANONLY (0xC1900210), een scan voor compatibiliteit van geslaagde zonder problemen. Als de *Upgradebeoordeling* stap kan worden uitgevoerd en deze code retourneert, wordt deze stap overgeslagen. Als de stap assessment een retourcode retourneert, mislukt deze stap met de takenreeks wordt uitgevoerd met de retourcode van de Windows-installatiecompatibiliteitsscan.
   - Zie voor meer informatie [besturingssysteem bijwerken](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS).
- Als u wijzigen van het apparaat van de BIOS in UEFI tijdens deze takenreeks wilt, Zie [BIOS converteren naar UEFI tijdens een upgrade ter plekke](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

Verzenden **Feedback** van de **Start** tabblad van het lint als er meer aanbevelingen of suggesties.



## <a name="improvements-to-pxe-enabled-distribution-points"></a>Verbeteringen aan distributiepunten met PXE-functionaliteit
<!-- 1357580 -->
Om te verduidelijken het gedrag van [nieuwe PXE-functionaliteit](/sccm/core/get-started/capabilities-in-technical-preview-1706#pxe-network-boot-support-for-ipv6) geïntroduceerd in Technical Preview-versie 1706, hernoemd we de **ondersteuning IPv6** optie. Op de **PXE** tabblad van de eigenschappen van het distributiepunt, selectievakje **inschakelen van een PXE-responder zonder Windows Deployment Service**. 

Deze optie kunt een PXE-responder op het distributiepunt waarvoor geen Windows Deployment Services (WDS) vereist. Als u deze nieuwe optie op een distributiepunt dat al is PXE-functionaliteit inschakelt, geeft Configuration Manager de WDS-service wordt onderbroken. Als u deze nieuwe optie is uitgeschakeld, maar nog steeds **PXE-ondersteuning inschakelen voor clients**, en vervolgens het distributiepunt WDS opnieuw kunt.

Omdat WDS niet vereist is, worden de PXE-distributiepunt een client of server-besturingssysteem op, met inbegrip van Windows Server Core. Deze nieuwe PXE-responder-service blijft ondersteuning bieden voor IPv6 en verbetert ook de flexibiliteit van distributiepunten met PXE-functionaliteit in externe kantoren.

> [!NOTE]
> Deze service gebruikt dezelfde fundamentele technologie als de [responder-service op basis van een Client PXE](/sccm/core/get-started/capabilities-in-technical-preview-1712#client-based-pxe-responder-service) in Technical Preview-versie 1712. Deze functie is niet vereist voor de overhead van de distributiepuntrol.

### <a name="multicast"></a>Multicast
Inschakelen en configureren van multicast op de **Multicast** tabblad wijst eigenschappen van het distributiepunt, het distributiepunt WDS moet gebruiken. 
- Als u **PXE-ondersteuning inschakelen voor clients** en **multicast inschakelen om gelijktijdig gegevens verzenden naar meerdere clients**, en u kunt geen **een PXE-responder zonder Windows Deployment Service inschakelen** .
- Als u **PXE-ondersteuning inschakelen voor clients** en **inschakelen van een PXE-responder zonder Windows Deployment Service**, en u kunt geen **multicast inschakelen om gelijktijdig gegevens verzenden naar meerdere clients**



## <a name="deployment-templates-for-task-sequences"></a>Implementatiesjablonen voor takenreeksen
<!-- 1357391 -->
De implementatiewizard van takenreeksen kunt nu een implementatiesjabloon maken. De sjabloon voor de implementatie kan worden opgeslagen en worden toegepast op een bestaande of nieuwe takenreeks maken van een implementatie. 

### <a name="try-it-out"></a>Probeer het nu!  
Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan. 

 **Maak een implementatiesjabloon voor een takenreeksimplementatie** <br/> 
1. In de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.
2. Met de rechtermuisknop op een takenreeks en selecteert u **implementeren**. 
3. Op de **algemene** tabblad, is nu een optie voor het **implementatiesjabloon selecteren**. 
4. Volg de stappen in de **Wizard Software implementeren** selecteren van de implementatie-instellingen voor de takenreeks. 
5. Wanneer u bereikt de **samenvatting** tabblad van de **Wizard Software implementeren**, klikt u op **opslaan als sjabloon**.
6. Geef een naam op voor de sjabloon en selecteer de instellingen in de sjabloon wilt opslaan. 
7. Klik op **Opslaan**. De sjabloon is nu beschikbaar voor gebruik van de **implementatiesjabloon selecteren** optie.



## <a name="product-lifecycle-dashboard"></a>Product lifecycle-dashboard
<!--1319632-->
De nieuwe [levenscyclus dashboard](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard) toont de status van het Microsoft Product Lifecycle-beleid voor Microsoft-producten die zijn geïnstalleerd op apparaten die worden beheerd met Configuration Manager. Het dashboard biedt u informatie over Microsoft-producten in uw omgeving, dan staat en einddatum voor ondersteuning. U kunt het dashboard gebruiken om te begrijpen van de beschikbaarheid van ondersteuning voor elk product. 

Ga naar het Lifecycle Dashboard in de Configuration Manager-console toegang tot **activa en naleving** >**Asset Intelligence** >**levenscyclus**



## <a name="improvements-to-reporting"></a>Verbeteringen aan te melden
<!--1357653-->
Als gevolg van [uw feedback](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/32434147-new-builtin-reports-about-windows-10-versions-and) hebben we een nieuw rapport toegevoegd **onderhoud van Windows 10 details voor een specifieke verzameling**. Dit rapport geeft de Resource-ID, NetBIOS-naam, OS-naam, de naam van de OS-versie, build, OS vertakking en onderhoud voor Windows 10-apparaten. Voor toegang tot het rapport, gaat u naar **bewaking** >**rapportage** >**rapporten** >**besturingssystemen**  > **Onderhoud van Windows 10 details voor een specifieke verzameling**.



## <a name="improvements-to-software-center"></a>Verbeteringen aan Software Center
<!--1357592-->
Als gevolg van [uw feedback](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/13002684-software-center-show-only-available-software-hid) geïnstalleerde toepassingen kunnen nu worden verborgen in Software Center. Toepassingen die al zijn geïnstalleerd, worden niet meer weergegeven op het tabblad toepassingen wanneer deze optie is ingeschakeld. 

### <a name="try-it-out"></a>Probeer het nu!
Schakel de **geïnstalleerde toepassingen verbergen in Software Center** instellen in de clientinstellingen voor Software Center. Het gedrag in Software Center zien wanneer de eindgebruiker een toepassing wordt geïnstalleerd.



## <a name="improvements-to-run-scripts"></a>Verbeteringen aan het uitvoeren van Scripts
<!--1236459-->
De [Scripts uitvoeren](/sccm/apps/deploy-use/create-deploy-scripts) functie retourneert nu script uitvoer met behulp van JSON-opmaak. Deze indeling retourneert consistent een leesbare scriptuitvoer. Scripts die niet kunnen worden uitgevoerd kunnen niet ophalen voor uitvoer die wordt geretourneerd. 



## <a name="boundary-group-fallback-for-management-points"></a>Grensgroep voor beheerpunten terugval
<!-- 1324594 -->
In deze release wordt gestart, kunt u terugval relaties voor beheerpunten tussen [grensgroepen](/sccm/core/servers/deploy/configure/boundary-groups). Dit gedrag biedt meer controle over de beheerpunten die clients gebruiken. Op de **relaties** tabblad van de eigenschappen van de grensgroep, is een nieuwe kolom voor beheerpunt. Wanneer u een nieuwe terugval grensgroep toevoegt, wordt de terugval tijd voor het beheerpunt is momenteel altijd nul (0). Dit gedrag is hetzelfde voor de **standaardgedrag** op de site-standaardgroep grens.

Voorheen een veelvoorkomend probleem treedt op wanneer er een beveiligde beheerpunt in een beveiligd netwerk. Clients op het bedrijfsnetwerk van de belangrijkste ontvangen beleidsregel met deze beveiligde beheerpunt, zelfs als ze niet kunnen met deze via een firewall communiceren. Om dit probleem op te lossen, gebruikt u de **nooit terugval** optie om ervoor te zorgen dat clients alleen terugval naar management verwijst met die ze kunnen communiceren.

Wanneer de site upgraden naar deze versie, voegt Configuration Manager alle beheerpunten voor internet facing toe aan de groep site standaard grens. Deze upgrade gedrag zorgt ervoor dat oudere clientversies blijven communiceren met beheerpunten. Om volledig te profiteren van deze functie, uw beheerpunten naar de gewenste grensgroepen te verplaatsen.

Management-punt grens groep terugval verandert het gedrag niet tijdens de clientinstallatie (ccmsetup). Als de opdrachtregel het initiële beheerpunt met de parameter /MP niet is opgegeven, ontvangt de nieuwe client de volledige lijst met beschikbare beheerpunten. De client gebruikt voor de eerste bootstrap-proces voor het eerste beheerpunt dat kunnen worden geopend. Nadat de client bij de site registreert, ontvangt de beheerpuntlijst correct gesorteerd met dit nieuwe gedrag. 

### <a name="prerequisites"></a>Vereisten
- Schakel [voorkeursbeheerpunten](/sccm/core/servers/deploy/configure/boundary-groups#preferred-management-points). Ga in de Configuration Manager-console naar de **beheer** werkruimte. Vouw **siteconfiguratie** en selecteer **Sites**. Klik op **hiërarchie-instellingen** in het lint. Op de **algemene** tabblad, schakelt u **Clients gebruiken liever beheerpunten die zijn opgegeven in grensgroepen**. 

### <a name="known-issues"></a>Bekende problemen
- Besturingssysteem-implementatieprocessen zijn niet op de hoogte van grensgroepen.

### <a name="troubleshooting"></a>Probleemoplossing
Nieuwe gegevens worden weergegeven de **LocationServices.log**. De **plaats** kenmerk identificeert een van de volgende statussen:
- 0: Onbekend
- 1: Het opgegeven beheerpunt bevindt zich alleen in de groep site standaard grens voor terugval
- 2: Het opgegeven beheerpunt bevindt zich in een neighbor of externe grensgroep. Als het beheerpunt zowel een neighbor en de grensgroepen van de site-standaard is, is de plaats 2.
- 3: Het opgegeven beheerpunt bevindt zich in de grensgroep lokale of huidige. Wanneer het beheerpunt in de huidige grensgroep, evenals een neighbor of de groep site standaard grens is, is de plaats 3. Als u de voorkeursbeheerpunten instellen in de hiërarchie-instellingen niet inschakelt, is de plaats altijd 3 ongeacht welke grens groep het beheerpunt is in.

Clients gebruiken beheerpunten lokale eerste (plaats 3), externe tweede (locatie 2) en terugval (locatie 1). 

Wanneer een client vijf fouten in tien minuten ontvangt en om te communiceren met een beheerpunt in de huidige grensgroep is mislukt, probeert het contact maken met een beheerpunt in een neighbor of de groep site standaard grens. Als het beheerpunt in de huidige grensgroep later weer online wordt gezet, wordt de client naar het lokale beheerpunt geretourneerd op de volgende vernieuwingscyclus. De vernieuwingscyclus is 24 uur, of wanneer de Configuration Manager-agent-service opnieuw wordt gestart.



## <a name="improved-support-for-cng-certificates"></a>Verbeterde ondersteuning voor CNG-certificaten
<!-- 1357314 -->
Configuration Manager (huidige vertakking) versie 1710 ondersteunt [cryptografie: Volgende Generation (CNG)-certificaten](/sccm/core/plan-design/network/cng-certificates-overview). Ondersteuning voor versie 1710 limieten aan clientcertificaten in verschillende scenario's. 

Vanaf deze technical preview-versie, CNG-certificaten gebruiken voor de volgende serverfuncties voor HTTPS-functionaliteit:
- Beheerpunt
- Distributiepunt
- Sitesysteemrollen toevoegen

De lijst met [niet-ondersteunde scenario's](/sccm/core/plan-design/network/cng-certificates-overview#unsupported-scenarios) hetzelfde is gebleven.



## <a name="cloud-management-gateway-support-for-azure-resource-manager"></a>Ondersteuning voor Azure Resource Manager-gateway cloud
<!-- 1324735 -->
Bij het maken van een exemplaar van de [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway) (CMG), de wizard biedt nu de optie voor het maken van een **Azure Resource Manager-implementatie**. [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) is een moderne platform voor het beheren van alle resources van de oplossing als één entiteit aangeroepen een [resourcegroep](/azure/azure-resource-manager/resource-group-overview#resource-groups). Bij het implementeren van CMG met Azure Resource Manager, de site maakt gebruik van Azure Active Directory (Azure AD) om te verifiëren en het maken van de benodigde cloud-bronnen. Deze gemoderniseerde implementatie is niet vereist voor de klassieke Azure-beheercertificaat.  

De wizard CMG biedt nog steeds de optie voor een **klassieke service-implementatie** met behulp van een Azure-beheercertificaat. Om te vereenvoudigen de implementatie en beheer van resources, wordt u aangeraden het Azure Resource Manager-implementatiemodel voor alle nieuwe CMG exemplaren. Indien mogelijk, implementeer de bestaande CMG exemplaren via Resource Manager opnieuw.

Configuration Manager worden bestaande klassieke CMG exemplaren niet gemigreerd naar het Azure Resource Manager-implementatiemodel. Maken van nieuwe CMG-exemplaren die gebruikmaken van Azure Resource Manager-implementaties en verwijder vervolgens klassieke CMG exemplaren. 

> [!IMPORTANT]
> Deze mogelijkheid biedt ondersteuning voor Azure Cloud Service Providers (CSP) niet inschakelen. De implementatie CMG met Azure Resource Manager blijft de klassieke cloud-service biedt geen ondersteuning voor de CSP. Zie voor meer informatie [beschikbare Azure-services in Azure CSP](/azure/cloud-solution-provider/overview/azure-csp-available-services).  

### <a name="prerequisites"></a>Vereisten
- Integratie met [Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure). Azure AD-gebruikersdetectie is niet vereist.
- Dezelfde [vereisten voor cloud management gateway](/sccm/core/clients/manage/plan-cloud-management-gateway#requirements-for-cloud-management-gateway), met uitzondering van het Azure-beheercertificaat.

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. In de Configuration Manager-console **beheer** werkruimte Vouw **Cloudservices**, en selecteer **Cloud Management Gateway**. Klik op **Cloud Management-Gateway maken** in het lint. 
2. Op de **algemene** pagina **Azure Resource Manager-implementatie**. Klik op **aanmelden** voor verificatie met een administrator-account Azure-abonnement. De wizard wordt automatisch gevuld de overige velden van de Azure AD-abonnementsgegevens opgeslagen tijdens de vereiste integratie. Als u meerdere abonnementen eigenaar, selecteer het gewenste abonnement gebruiken. Klik op **Volgende**.  
3. Op de **instellingen** pagina, geef de PKI-certificaatbestand zoals gebruikelijk. Dit certificaat definieert de naam van de service CMG in Azure. Selecteer de **regio**, en selecteer vervolgens een optie van de groep resource naar elk **nieuw** of **gebruik bestaande**. Voer de naam van de nieuwe resourcegroep of Selecteer een bestaande resourcegroep in de vervolgkeuzelijst. 
4. Voltooi de wizard.

> [!NOTE] 
> Voor de geselecteerde Azure AD-app server Azure wijst het abonnement **Inzender** machtiging. 

Controleer de voortgang van de service-implementatie met **cloudmgr.log** op het serviceverbindingspunt wordt gehost.



## <a name="approve-application-requests-for-users-per-device"></a>Goedkeuren van aanvragen van toepassingen voor gebruikers per apparaat
<!-- 1357015 -->
In deze release wordt gestart wanneer een gebruiker een toepassing die moet worden goedgekeurd aanvraagt, is de specifieke apparaatnaam nu een onderdeel van de aanvraag. Als de beheerder de aanvraag goedkeurt, is alleen de gebruiker kan de toepassing op het apparaat installeren. De gebruiker moet een nieuwe aanvraag voor het installeren van de toepassing op een ander apparaat verzenden. 

> [!NOTE]
> Deze functie is optioneel. Wanneer u bijwerkt naar deze versie, moet u deze functie in de wizard updates inschakelen. U kunt ook de functie in de console later inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).

### <a name="prerequisites"></a>Vereisten
- Upgrade van de Configuration Manager-client naar de nieuwste versie
- Schakel de clientinstelling **nieuwe Software Center gebruiken** in de [computeragent](/sccm/core/clients/deploy/about-client-settings#computer-agent) groep

### <a name="try-it-out"></a>Probeer het nu!
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. Een toepassing als beschikbaar implementeren op een Gebruikersverzameling.
2. Op de **implementatie-instellingen** pagina, schakelt u de optie: **Een beheerder een aanvraag voor deze toepassing op het apparaat moet goedkeuren**.
3. Als een gebruiker in de doelgroep, Software Center een aanvraag indienen voor de toepassing te gebruiken. 
4. Weergave **goedkeuringsaanvragen** onder **Toepassingsbeheer** in de **softwarebibliotheek** werkruimte van de Configuration Manager-console. Er is nu een **apparaat** kolom in de lijst voor elke aanvraag. Wanneer u actie op de aanvraag ondernemen, bevat het dialoogvenster aanvraag voor ook de naam van het apparaat waarvan de gebruiker de aanvraag heeft ingediend.



## <a name="use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices"></a>Software Center gebruiken om te zoeken en installeren van de gebruiker beschikbare toepassingen op Azure AD-die lid zijn van apparaten
<!-- 1322613 -->
Als u toepassingen als beschikbaar voor gebruikers implementeert, kunnen ze nu bladeren en deze op Azure Active Directory (Azure AD)-apparaten installeren via Software Center.  

### <a name="prerequisites"></a>Vereisten
- HTTPS inschakelen op het beheerpunt
- De site met integreren [Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure)
- Een toepassing als beschikbaar implementeren op een Gebruikersverzameling
- Een toepassingsinhoud distribueert naar een [clouddistributiepunt](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)
- Schakel de clientinstelling **nieuwe Software Center gebruiken** in de [computeragent](/sccm/core/clients/deploy/about-client-settings#computer-agent) groep
- De client moet zijn: 
   - Windows 10
   - Azure AD zijn toegevoegd, ook wel bekend als cloud domein
- Ter ondersteuning van clients op internet:
    - [Beheergateway cloud](/sccm/core/clients/manage/plan-cloud-management-gateway) 
    - Schakel de clientinstelling: **Gebruikersbeleidsaanvragen van internetclients toestaan** in de [clientbeleid](/sccm/core/clients/deploy/about-client-settings#client-policy) groep
- Ter ondersteuning van clients op het bedrijfsnetwerk bevinden:
    - Het cloud-distributiepunt toevoegen aan een grensgroep die wordt gebruikt door de clients
    - Clients moeten kunnen omzetten van de volledig gekwalificeerde domeinnaam (FQDN) van het HTTPS-beheerpunt



## <a name="report-on-windows-autopilot-device-information"></a>Rapport over Windows Automatische piloot apparaatgegevens
<!-- 1351442 -->
Windows Automatische piloot is een oplossing voor onboarding en nieuwe Windows 10-apparaten op een moderne manier configureren. Zie voor meer informatie een [overzicht van Windows Automatische piloot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot). Er is één methode voor het registreren van bestaande apparaten met Windows Automatische piloot van apparaatgegevens uploaden naar de Microsoft Store voor bedrijven en Education. Deze informatie omvat het serienummer van het apparaat, Windows-product-id en een hardware-id. Configuration Manager gebruiken voor het verzamelen en rapporteren van deze gegevens van een apparaat. 

### <a name="prerequisites"></a>Vereisten
- Deze apparaat-informatie is alleen van toepassing op clients op Windows 10 versie 1703 en hoger

### <a name="try-it-out"></a>Probeer het nu!
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. In de Configuration Manager-console **bewaking** werkruimte, vouw de **rapportage** knooppunt uitvouwen **rapporten**, en selecteer de **Hardware - algemeen**  knooppunt.
2. Voer het nieuwe rapport **Windows Automatische piloot apparaatgegevens** en bekijk de resultaten. 
3. Klik in de rapportviewer de **exporteren** pictogram en selecteer **CSV (door komma's gescheiden)** optie.
4. Nadat het bestand is opgeslagen, moet u de gegevens uploaden naar de Microsoft Store voor bedrijven en Education. Zie voor meer informatie [apparaten toevoegen in Microsoft Store voor bedrijven en Education](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile). 



## <a name="improvements-to-configuration-manager-policies-for-windows-device-exploit-guard"></a>Verbeteringen in Configuration Manager-beleid voor Windows-apparaat misbruiken Guard
<!-- 1356220 -->
Extra instellingen voor de kwetsbaarheid voor aanvallen vermindering en beheerd map toegang onderdelen zijn toegevoegd voor Windows Device misbruiken Guard in Configuration Manager.

**Nieuwe instellingen voor toegang tot de map van beheerd**<br/>
Er zijn twee extra opties wanneer u toegang tot de map van beheerd configureert: **Alleen schijfsectoren blokkeren** en **Audit schijfsectoren alleen**. Deze twee instellingen beheerd maptoegang worden ingeschakeld voor opstartsectoren alleen toestaan en kunnen niet de bescherming van specifieke mappen of de standaardmappen beveiligd. 

**Nieuwe instellingen kwetsbaarheid voor aanvallen te beperken**
- Geavanceerde beveiliging tegen ransomware gebruiken.
- Referentie stelen van het Windows-subsysteem lokaal beveiligingsbeleid autoriteit blokkeren. 
- Voorkomen dat uitvoerbare bestanden uitgevoerd tenzij ze voldoen aan een invloed, leeftijd of lijst met vertrouwde criteria. 
- Niet-vertrouwde en niet-ondertekende processen die worden uitgevoerd vanaf een USB blokkeren.



## <a name="microsoft-edge-browser-policies"></a>Microsoft Edge-browser-beleid
<!-- 1357310 -->
Voor klanten die gebruikmaken van de [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) webbrowser op Windows 10-clients, u kunt nu een Configuration Manager-instellingen nalevingsbeleid voor het configureren van de verschillende Microsoft Edge-instellingen maken. Dit beleid bevat momenteel de volgende instellingen:
- **De Microsoft Edge-browser ingesteld als standaard**: Hiermee configureert u de Windows 10-app-instelling voor standaard voor webbrowser Microsoft Edge
- **Adres toestaan balk vervolgkeuzelijst**: Windows 10 versie 1703 of hoger vereist. Zie voor meer informatie [AllowAddressBarDropdown browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowaddressbardropdown).
- **Favorieten synchronisatie tussen Microsoft browsers toestaan**: Windows 10 versie 1703 of hoger vereist. Zie voor meer informatie [SyncFavoritesBetweenIEAndMicrosoftEdge browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-syncfavoritesbetweenieandmicrosoftedge).
- **Schakel bladeren door gegevens bij afsluiten toestaan**: Windows 10 versie 1703 of hoger vereist. Zie voor meer informatie [ClearBrowsingDataOnExit browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-clearbrowsingdataonexit).
- **Toestaan dat Do Not Track-headers**: Zie voor meer informatie [AllowDoNotTrack browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowdonottrack).
- **Automatisch invullen toestaan**: Zie voor meer informatie [AllowAutofill browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowautofill).
- **Cookies toestaan**: Zie voor meer informatie [AllowCookies browser-beleid](/windows/client-management/mdm/policy-csp-browser#browser-allowcookies).
- **Pop-upblokkering toestaan**: Zie voor meer informatie [AllowPopups browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowpopups).
- **Zoeksuggesties in de adresbalk toestaan**: Zie voor meer informatie [AllowSearchSuggestionsinAddressBar browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowsearchsuggestionsinaddressbar).
- **Verzenden van intranetverkeer naar Internet Explorer toestaan**: Zie voor meer informatie [SendIntranetTraffictoInternetExplorer browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-sendintranettraffictointernetexplorer).
- **Wachtwoord toestaan manager**: Zie voor meer informatie [AllowPasswordManager browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager).
- **Hulpprogramma's voor ontwikkelaars toestaan**: Zie voor meer informatie [AllowDeveloperTools browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowdevelopertools).
- **Toestaan dat extensies**: Zie voor meer informatie [AllowExtensions browser-beleid](/windows/client-management/mdm/policy-csp-browser#browser-allowextensions).

### <a name="prerequisites"></a>Vereisten
- Windows 10-client die lid zijn van een Azure Active Directory. 

### <a name="known-issues"></a>Bekende problemen
- On-premises domein apparaten kunnen dit beleid in deze release niet toepassen. Dit probleem heeft ook betrekking op hybride domein-apparaten.

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

**Het beleid maken**
1. Ga in de Configuration Manager-console naar de **activa en naleving** werkruimte. Vouw **instellingen voor naleving** en selecteer de nieuwe **Microsoft Edge-Browser-profielen** knooppunt. Klik op de optie lint **Microsoft Edge Browser-beleid maken**.
2. Geef een **naam** voor het beleid (optioneel) Voer een **beschrijving**, en klik op **volgende**.
3. Op de **instellingen** pagina, wijzig de waarde in **geconfigureerde** voor de instellingen voor opname in dit beleid en klik op **volgende**.
4. Op de **ondersteunde Platforms** pagina, selecteert u de versies van besturingssystemen en architecturen waarop dit beleid van toepassing is en op **volgende**. 
5. Voltooi de wizard.

**Het beleid implementeren**
1. Selecteer uw beleid en klik op de optie lint **implementeren**.
2. Klik op **Bladeren** selecteren van de verzameling gebruikers of apparaten waarop het beleid te implementeren. 
3. Selecteer extra opties indien nodig. Waarschuwingen genereren wanneer het beleid niet compatibel is. Stel de planning op waarmee de client de apparaatcompatibiliteit met dit beleid evalueert.
4. Klik op **OK** de implementatie te maken.

Net als alle instellingen voor nalevingsbeleid herstelt de client de instellingen op de planning die u opgeeft. [Bewaken en rapporteren over apparaatcompatibiliteit](/sccm/compliance/deploy-use/monitor-compliance-settings) in de Configuration Manager-console.



## <a name="report-for-default-browser-counts"></a>Rapport voor standaard browser aantallen
<!-- 1357830 -->
Er is nu een nieuw rapport om de telling van clients met een specifieke webbrowser als de standaard Windows weer te geven. 

### <a name="known-issues"></a>Bekende problemen
- Wanneer u het rapport voor het eerst opent, ziet deze alleen het aantal en niet de BrowserProgID. Om dit probleem omzeilen door de query voor het rapport aan de volgende syntaxis te bewerken:  
    `select BrowserProgId00 as BrowserProgId, Count(*) as Count`  
    `from DEFAULT_BROWSER_DATA as dbd`  
    `group by BrowserProgId00`

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.
1. In de **Configuration Manager** console **bewaking** werkruimte Vouw **rapportage**, vouw **rapporten**, selecteer **Software - bedrijven en producten**.
2. Voer de **standaardbrowser telt** rapport.

Gebruik de volgende verwijzing voor algemene BrowserProgIDs:
- **AppXq0fevzme2pys62n3e0fbqa7peapykr8v**: Microsoft Edge
- **IE.HTTP**: Microsoft Internet Explorer
- **ChromeHTML**: Google Chrome
- **OperaStable**: Opera Software
- **FirefoxURL-308046B0AF4A39CB**: Mozilla Firefox



## <a name="support-for-windows-10-arm64-devices"></a>Ondersteuning voor Windows 10 ARM64 apparaten
<!-- 1353704 -->
In deze release die Configuration Manager-client wordt ondersteund op Windows 10 ARM64 apparaten wordt gestart. Functies voor bestaande client moeten samenwerken met deze nieuwe apparaten. Bijvoorbeeld, hardware en software-inventaris, software-updates en toepassingen beheren. Implementatie van besturingssysteem is momenteel niet ondersteund. 

## <a name="changes-to-phased-deployments"></a>Wijzigingen in gefaseerde implementaties
<!-- 1357405 -->
Gefaseerde implementaties automatiseren een gecoördineerde, geordende rollout van software zonder dat er meerdere implementaties. De wizard gefaseerde implementatie kan worden voltooid voor takenreeksen in de beheerconsole en implementaties worden gemaakt in deze Technical Preview-versie. Echter, de productiefase niet automatisch wordt gestart als is voldaan aan de criteria voor succes van de testfase. De productiefase kan handmatig worden gestart met een SQL-instructie.   

### <a name="try-it-out"></a>Probeer het nu!  
  Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.
 
**Een gefaseerde implementatie voor een takenreeks maken** </br>
1. In de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.
2. Met de rechtermuisknop op een bestaande takenreeks en selecteert u **gefaseerde implementatie maken**. 
3. Op de **algemene** tabblad, geef de gefaseerde implementatie een naam, beschrijving (optioneel) en selecteer **automatisch maken standaard test en productie fasen**. 
4. Vul de **verzameling testfase** en **Productieverzameling** velden. Selecteer **volgende**.
5. Op de **instellingen** tabblad, kiest u een optie voor elk van de schema-instellingen en selecteer **volgende** wanneer u klaar. 
6. Op de **fasen** tabblad, een van de fasen Bewerk indien nodig en klik vervolgens op **volgende**.
7. Bevestig uw selecties op de **samenvatting** tabblad en klik vervolgens op **volgende** om door te gaan.
8. Wanneer de succescriteria voor de testfase is bereikt en volg de instructies voor de productiefase beginnen met een SQL-instructie.
 
**Productiefase beginnen met een SQL-instructie**
1. Identificeer de PhasedDeploymentID voor de implementatie die u hebt gemaakt met de volgende SQL-query:<br/> `Select * from PhasedDeployment`
2. Voer de volgende instructie voor het starten van de productiefase bevindt:<br/> `UPDATE PhasedDeployment SET EvaluatePhasedDeployment = 1, Action = 3 WHERE PhasedDeploymentID = <Phased Deployment ID>`


## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
