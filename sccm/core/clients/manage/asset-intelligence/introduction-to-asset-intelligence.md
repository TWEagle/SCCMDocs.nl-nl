---
title: Asset Intelligence Inleiding | Microsoft Docs
description: Maak kennis met Asset Intelligence in System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0bdfdef5-390f-4099-8bde-de51d9a89175
caps.latest.revision: "7"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 879dc3f04f361af955afbc4db180d097073e8d41
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-asset-intelligence-in-system-center-configuration-manager"></a>Inleiding op Asset Intelligence in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Asset Intelligence in System Center Configuration Manager kunt u inventariseren en gebruik van softwarelicenties in uw onderneming te beheren met behulp van de Asset Intelligence-catalogus. Veel WMI-klassen (Windows Management Instrumentation) voor hardware-inventarisatie verbeteren de reikwijdte van de gegevens die worden verzameld over de hardware en softwaretitels die worden gebruikt. Deze informatie wordt in meer dan zestig rapporten in een eenvoudig te gebruiken indeling weergegeven. Veel van deze rapporten bevatten koppelingen naar meer gedetailleerde rapporten, waarin u kunt zoeken naar algemene informatie en vervolgens gedetailleerdere informatie kunt weergeven. U kunt aangepaste gegevens toevoegen aan de Asset Intelligence-catalogus, zoals aangepaste softwarecategorieën, softwarefamilies, softwarelabels en hardwarevereisten. U kunt ook verbinding maken met System Center Online om de Asset Intelligence-catalogus dynamisch bij te werken met de meest actuele informatie die beschikbaar is. Klanten van Microsoft kunnen afstemmen licentiegebruik voor ondernemingssoftware met aangeschafte softwarelicenties die worden gebruikt door het importeren van softwarelicentiegegevens in de Configuration Manager-sitedatabase.  

##  <a name="BKMK_AssetIntelligenceCatalog"></a> Asset Intelligence-catalogus  

 De Asset Intelligence van Configuration Manager-catalogus is een reeks databasetabellen die zijn opgeslagen in de sitedatabase, en die categorisatie- en identificatie-informatie voor meer dan 300.000 softwaretitels en -versies bevatten. Deze databasetabellen worden ook gebruikt voor het beheren van hardwarevereisten voor bepaalde softwaretitels.  

 De Asset Intelligence-catalogus bevat softwarelicentiegegevens voor softwaretitels die worden gebruikt, zowel van software van Microsoft als van software van derden. Een vooraf gedefinieerde set hardwarevereisten voor softwaretitels is beschikbaar in de Asset Intelligence-catalogus en u kunt nieuwe, door de gebruiker gedefinieerde hardwarevereistegegevens maken om te voldoen aan aangepaste vereisten. Bovendien kunt u gegevens in de Asset Intelligence-catalogus aanpassen en kunt u softwaretitelgegevens voor categorisatie uploaden naar System Center Online.  

 Asset Intelligence-catalogusupdates die nieuw uitgebrachte software bevatten, zijn periodiek beschikbaar als download om catalogusupdates bulksgewijs uit te voeren. De catalogus kan ook dynamisch worden bijgewerkt via de sitesysteemrol Asset Intelligence-synchronisatiepunt.  

###  <a name="BKMK_SoftwareCategories"></a> Softwarecategorieën  
 Asset Intelligence-softwarecategorieën worden gebruikt om geïnventariseerde softwaretitels breed te categoriseren en als groeperingen op hoog niveau van bepaalde softwarefamilies. Een mogelijke softwarecategorie is bijvoorbeeld energiebedrijven en een softwarefamilie binnen deze softwarecategorie kan olie en gas of hydro-elektrisch zijn. Veel softwarecategorieën zijn vooraf gedefinieerd in de Asset Intelligence-catalogus en u kunt door de gebruiker gedefinieerde categorieën maken om geïnventariseerde software verder te definiëren. De validatiestatus voor alle vooraf gedefinieerde softwarecategorieën is altijd **Gevalideerd**, terwijl de status van aangepaste softwarecategoriegegevens toegevoegd aan de Asset Intelligence-catalogus **Door de gebruiker gedefinieerd**is. Zie voor meer informatie over het beheren van softwarecategorieën [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  Vooraf gedefinieerde softwarecategoriegegevens die zijn opgeslagen in de Asset Intelligence-catalogus, zijn alleen-lezen en kunnen niet worden gewijzigd of verwijderd. Gebruikers met beheerdersrechten kunnen door de gebruiker gedefinieerde softwarecategorieën toevoegen, wijzigen of verwijderen.  

###  <a name="BKMK_SoftwareFamilies"></a> Softwarefamilies  
 Asset Intelligence-softwarefamilies worden gebruikt om geïnventariseerde softwaretitels binnen softwarecategorieën te definiëren. Veel softwarefamilies zijn vooraf gedefinieerd in de Asset Intelligence-catalogus en u kunt door de gebruiker gedefinieerde categorieën maken om geïnventariseerde software verder te definiëren. De validatiestatus voor alle vooraf gedefinieerde softwarefamilies is altijd **Gevalideerd**, terwijl de status van gegevens van aangepaste softwarefamilies toegevoegd aan de Asset Intelligence-catalogus **Door de gebruiker gedefinieerd**is. Zie voor meer informatie over het beheren van softwarefamilies [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  Informatie over vooraf gedefinieerde softwarefamilies is alleen-lezen en kan niet worden gewijzigd. Gebruikers met beheerdersrechten kunnen door de gebruiker gedefinieerde softwarefamilies toevoegen, wijzigen of verwijderen.  

###  <a name="BKMK_CustomLabels"></a> Softwarelabels  
 Met aangepaste Asset Intelligence-softwarelabels kunt u filters maken om softwaretitels te groeperen en weer te geven met Asset Intelligence-rapporten. U kunt softwarelabels gebruiken om door de gebruiker gedefinieerde groepen softwaretitels te maken die een gemeenschappelijk kenmerk hebben. U kunt bijvoorbeeld een softwarelabel Shareware maken, dat label koppelen aan geïnventariseerde softwaretitels en vervolgens een rapport uitvoeren om alle softwaretitels met het gekoppelde softwarelabel Shareware weer te geven. Softwarelabels worden niet vooraf gedefinieerd. De validatiestatus voor softwarelabels is altijd **Door de gebruiker gedefinieerd**. Zie voor meer informatie over het beheren van softwarelabels [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

###  <a name="BKMK_HardwareRequirements"></a> Hardwarevereisten  
 U kunt hardwarevereistegegevens gebruiken om te verifiëren of computers voldoen aan de hardwarevereisten voor softwaretitels voordat ze worden geselecteerd voor software-implementaties. U kunt hardwarevereisten voor softwaretitels beheren in de werkruimte **Activa en naleving** in het knooppunt **Hardwarevereisten** onder het knooppunt **Asset Intelligence** . Veel hardwarevereisten zijn vooraf gedefinieerd in de Asset Intelligence-catalogus en u kunt nieuwe, door de gebruiker gedefinieerde hardwarevereistegegevens maken om te voldoen aan aangepaste vereisten. De validatiestatus voor alle vooraf gedefinieerde hardwarevereisten is altijd **Gevalideerd**, terwijl de status van gegevens van aangepaste hardwarevereisten toegevoegd aan de Asset Intelligence-catalogus **Door de gebruiker gedefinieerd**is. Zie voor meer informatie over het beheren van hardwarevereisten [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  De weergegeven hardwarevereisten in de Configuration Manager-console worden opgehaald uit de Asset Intelligence-catalogus en niet zijn gebaseerd op informatie over geïnventariseerde softwaretitels van System Center 2012 Configuration Manager-clients. Informatie over hardwarevereisten wordt niet bijgewerkt tijdens de synchronisatie met System Center Online. U kunt door de gebruiker gedefinieerde hardwarevereisten maken voor geïnventariseerde software die geen bijbehorende hardwarevereisten heeft.  

 Standaard wordt de volgende informatie weergegeven voor elke vermelde hardwarevereiste:  

-   **Softwaretitel**: Hiermee geeft u de softwaretitel die is gekoppeld aan de hardwarevereiste.  

-   **Minimale CPU (MHz)**: Hiermee geeft u de minimale processorsnelheid, in megahertz (MHz), vereist voor de softwaretitel.  

-   **Minimale hoeveelheid RAM (KB)**: Hiermee geeft u de minimale hoeveelheid RAM, in kilobytes (KB), die vereist is voor de softwaretitel.  

-   **Minimale schijfruimte (KB)**: Hiermee geeft u de minimale vrije schijfruimte, in KB, die vereist zijn voor de softwaretitel.  

-   **Minimale schijfgrootte (KB)**: Hiermee geeft u de grootte van de minimale harde schijf, in KB, die vereist zijn voor de softwaretitel.  

-   **Validatiestatus**: Hiermee geeft u de validatiestatus voor de hardwarevereiste.  

 Vooraf gedefinieerde hardwarevereisten opgeslagen in de Asset Intelligence-catalogus zijn alleen-lezen en kunnen niet worden verwijderd.  Gebruikers met beheerdersrechten kunnen door de gebruiker gedefinieerde hardwarevereisten toevoegen, wijzigen of verwijderen voor softwaretitels die niet in de Asset Intelligence-catalogus zijn opgeslagen.  

##  <a name="BKMK_InventoriedSoftwareTitles"></a> Geïnventariseerde softwaretitels  
 U kunt informatie over geïnventariseerde softwaretitels bekijken in de werkruimte **Activa en naleving** in het knooppunt **Geïnventariseerde software** onder het knooppunt **Asset Intelligence** . De Clientagent voor Hardware-inventaris verzamelt informatie over de geïnventariseerde software van Configuration Manager-clients op basis van de softwaretitels die zijn opgeslagen in de Asset Intelligence-catalogus.  

> [!WARNING]  
>  De clientagent voor hardware-inventarisatie verzamelt inventaris op basis van de Asset Intelligence-rapportageklassen voor hardware-inventarisatie die u inschakelt. Zie voor meer informatie over het inschakelen van de klassen, [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Standaard wordt de volgende informatie weergegeven voor elke geïnventariseerde softwaretitel:  

-   **Naam**: Hiermee geeft u de naam van de geïnventariseerde softwaretitel.  

-   **Leverancier**: Geeft de naam van de leverancier die de geïnventariseerde softwaretitel heeft ontwikkeld.  

-   **Versie**: Hiermee geeft u de productversie van de geïnventariseerde softwaretitel.  

-   **Categorie**: Hiermee geeft u de softwarecategorie die momenteel is toegewezen aan de geïnventariseerde softwaretitel.  

-   **Familie**: Hiermee geeft u de softwarefamilie die momenteel is toegewezen aan de geïnventariseerde softwaretitel.  

-   **Label** [**1**, **2**, en **3**]: Hiermee geeft u de aangepaste labels die gekoppeld aan de softwaretitel zijn. Aan geïnventariseerde softwaretitels kunnen maximaal drie aangepaste labels worden gekoppeld.  

-   **Aantal**: Hiermee geeft u het nummer van de Configuration Manager-clients die de softwaretitel is geïnventariseerd.  

-   **Status**: Hiermee geeft u de validatiestatus voor de geïnventariseerde softwaretitel.  

> [!NOTE]  
>  U kunt de categorisatiegegevens (productnaam, leverancier, softwarecategorie en softwarefamilie) voor geïnventariseerde software alleen wijzigen op de site op het hoogste niveau in uw hiërarchie. Wanneer u categorisatiegegevens voor vooraf gedefinieerde software wijzigt, wordt de validatiestatus voor de software gewijzigd van **Gevalideerd** in **Door de gebruiker gedefinieerd**.  

##  <a name="AssetIntelligenceSycnronizationPoint"></a> Asset Intelligence-synchronisatiepunt  
 De Asset Intelligence-synchronisatiepunt is een Configuration Manager-sitesysteemrol die verbinding maken met System Center Online (via TCP-poort 443) wordt gebruikt voor het beheren van dynamische Asset Intelligence-catalogusgegevens bijgewerkt. Deze siterol kan alleen worden geïnstalleerd op de site op het hoogste niveau van de hiërarchie. U moet alle aanpassingen voor Asset Intelligence-catalogus configureren met behulp van een Configuration Manager-console die is verbonden met het hoogste niveau. Hoewel alle updates moeten worden geconfigureerd op de site op het hoogste niveau, worden Asset Intelligence-catalogusgegevens gerepliceerd naar andere sites in de hiërarchie. Met de siterol Asset Intelligence-synchronisatiepunt kunt u catalogussynchronisatie op aanvraag met System Center Online aanvragen of een automatische catalogussynchronisatie plannen. Via het Asset Intelligence-synchronisatiepunt kunnen nieuwe Asset Intelligence-catalogusgegevens worden gedownload en kan informatie over aangepaste softwaretitels voor categorisatie worden geüpload naar System Center Online. Microsoft beschouwt alle softwaretitels die voor categorisatie naar System Center Online worden geüpload als openbare informatie. Daarom moet u ervoor zorgen dat uw aangepaste softwaretitels geen vertrouwelijke of eigendomsinformatie bevatten.  

> [!NOTE]  
>  Nadat een niet-gecategoriseerde softwaretitel is verzonden en er ten minste vier categorisatieaanvragen voor dezelfde softwaretitel zijn ingediend door klanten, identificeren en categoriseren System Center Online-onderzoekers de categorisatiegegevens voor de softwaretitel en worden deze vervolgens beschikbaar gemaakt voor alle klanten die de onlineservice gebruiken. Softwaretitels met de meeste aanvragen voor categorisatie krijgen de hoogste prioriteit. Aangepaste software en Line-Of-Business-toepassingen krijgen waarschijnlijk geen categorie. U kunt deze softwaretitels beter niet voor categorisatie naar Microsoft verzenden.  

> [!NOTE]  
>  De sitesysteemrol Asset Intelligence-synchronisatiepunt is vereist om verbinding te maken met System Center Online. Zie voor meer informatie over het installeren van een Asset Intelligence-synchronisatiepunt [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

##  <a name="BKMK_AssetIntelligenceHomePage"></a> Asset Intelligence-startpagina  
 De **Asset Intelligence** knooppunt in de **activa en naleving** werkruimte is de startpagina van Asset Intelligence in Configuration Manager. Op de startpagina **Asset Intelligence** wordt een overzichtsdashboard voor Asset Intelligence-catalogusgegevens weergegeven.  

> [!NOTE]  
>  De startpagina **Asset Intelligence** wordt niet automatisch bijgewerkt terwijl deze wordt weergegeven.  

 De startpagina **Asset Intelligence** is onderverdeeld in de volgende secties:  

-   **Synchronisatie catalogus**: Bevat informatie over of Asset Intelligence is ingeschakeld en de huidige status van het Asset Intelligence-synchronisatiepunt. Daarnaast wordt de synchronisatieplanning weergegeven, wordt aangegeven of de klantlicentieverklaring is geïmporteerd, wanneer de status het laatst is bijgewerkt en wanneer de volgende update is gepland, en wordt het aantal wijzigingen sinds de installatie van het sitesysteem voor het Asset Intelligence-synchronisatiepunt weergegeven.  

    > [!NOTE]  
    >  De sectie Synchronisatie catalogus van de startpagina **Asset Intelligence** wordt alleen weergegeven als de sitesysteemrol Asset Intelligence-synchronisatiepunt is geïnstalleerd.  

-   **Status geïnventariseerde Software**: Bevat het aantal en het percentage van geïnventariseerde software, softwarecategorieën en softwarefamilies die zijn geïdentificeerd door Microsoft, geïdentificeerd door een beheerder, die in afwachting van online-identificatie of niet-geïdentificeerd en niet in afwachting. De informatie in tabelindeling bevat het aantal voor elke softwaretoepassing, terwijl in de grafiek het percentage voor elke softwaretoepassing wordt weergegeven.  

##  <a name="BKMK_AssetIntelligenceReports"></a> Asset Intelligence-rapporten  
 De Asset Intelligence-rapporten bevinden zich in de Configuration Manager-console in de **bewaking** werkruimte in de Asset Intelligence-map onder de **rapportage** knooppunt. De rapporten bevatten informatie over de hardware, licentiebeheer en software. Zie voor meer informatie over rapporten in Configuration Manager [rapportage in System Center Configuration Manager](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Het aantal geïnstalleerde softwaretitels en de weergegeven licentiegegevens in Asset Intelligence-rapporten kunnen afwijken van het werkelijke aantal geïnstalleerde softwaretitels of gebruikte licenties in de omgeving. Deze afwijking wordt veroorzaakt door de complexe afhankelijkheden en beperkingen bij het inventariseren van softwarelicentiegegevens voor softwaretitels die zijn geïnstalleerd in bedrijfsomgevingen. Gebruik Asset Intelligence-rapporten niet als enige bron om de naleving van gekochte softwarelicenties te bepalen.  

###  <a name="BKMK_HardwareReports"></a> Asset Intelligence-hardwarerapporten  
 Asset Intelligence-hardwarerapporten bevatten informatie over hardwareactiva in de organisatie. Omdat er wordt gebruikgemaakt van hardware-inventarisatiegegevens, zoals snelheid, geheugen, randapparaten en meer, kan in Asset Intelligence-rapporten informatie over USB-apparaten, hardware die moet worden bijgewerkt en zelfs computers die niet gereed zijn voor een bepaalde software-upgrade worden weergegeven.  

> [!NOTE]  
>  Bepaalde gebruikersgegevens in Asset Intelligence-hardwarerapporten zijn afkomstig uit het gebeurtenislogboek van de systeembeveiliging. Voor een betere nauwkeurigheid van het rapport kunt u dit logboek beter wissen wanneer u een computer opnieuw toewijst aan een nieuwe gebruiker.  

###  <a name="BKMK_LicenseManagementReports"></a> Asset Intelligence-rapporten voor licentiebeheer  
 Asset Intelligence-rapporten voor licentiebeheer bevatten gegevens over licenties die worden gebruikt. Het rapport License-grootboek bevat een lijst met geïnstalleerde Microsoft-toepassingen in een indeling congruent met een Microsoft-licentieverklaring. Dit is een handige methode voor het vergelijken van gekochte licenties met gebruikte licenties. Andere rapporten voor licentiebeheer bieden informatie over computers die fungeren als servers waarop de sleutelbeheerservice (KMS) voor statistieken over besturingssysteemactivering wordt uitgevoerd.  

> [!IMPORTANT]  
>  In verscheidene Asset Intelligence-rapporten voor licentiebeheer wordt informatie over de functie van de sleutelbeheerservice, een methode voor het beheren van volumelicenties, weergegeven. Als er geen server voor de sleutelbeheerservice is geïmplementeerd, retourneren sommige rapporten mogelijk geen gegevens. Zoek voor meer informatie over de sleutelbeheerservice naar sleutelbeheerservice of KMS op [Microsoft TechNet](http://go.microsoft.com/fwlink/?linkid=3225).  

###  <a name="BKMK_SoftwareReports"></a> Asset Intelligence-softwarerapporten  
 Asset Intelligence-softwarerapporten bevatten informatie over softwarefamilies, categorieën en specifieke softwaretitels die zijn geïnstalleerd op computers in de organisatie. De softwarerapporten bevatten informatie over browserhelperobjecten, software die automatisch wordt gestart en meer. Deze rapporten kunnen worden gebruikt om adware, spyware en andere schadelijke software te identificeren, en softwareredundantie te identificeren om de aankoop en ondersteuning van software te stroomlijnen.  

###  <a name="BKMK_SoftwareIdTagReports"></a> Asset Intelligence-rapporten voor de identificatie van softwaretags  
 Asset Intelligence-rapporten voor de identificatie van softwaretags bevatten informatie over software met een softwaretag die in overeenstemming is met ISO/IEC 19770-2. De softwaretags bieden gezaghebbende informatie die wordt gebruikt voor het identificeren van geïnstalleerde software. Wanneer u de SMS_SoftwareTag hardware-inventarisatie inschakelt, Configuration Manager worden gegevens verzameld over de software met softwaretags. De volgende rapporten bevatten informatie over de software:  

-   **Software 14A - zoeken naar software waarbij een softwaretag is geactiveerd**: Dit rapport wordt de telling gegeven van geïnstalleerde software waarbij een softwaretag is ingeschakeld.  

-   **Software 14B - Computers met specifieke software-id-tag is geactiveerd geïnstalleerd**: Dit rapport geeft alle computers die software waarbij een specifieke software-id-tag is geactiveerd geïnstalleerde hebben.  

-   **Software 14C - geïnstalleerde software software-identificatielabel op een specifieke computer**: Dit rapport geeft alle geïnstalleerde software waarbij een specifieke software-id-tag is ingeschakeld op een specifieke computer.  

###  <a name="BKMK_ReportingLImitations"></a> Beperking voor Asset Intelligence-rapporten  
 Asset Intelligence-rapporten kunnen grote hoeveelheden gegevens bevatten over geïnstalleerde softwaretitels en gekochte softwarelicenties die worden gebruikt. U moet deze informatie echt niet als de enige bron voor de naleving van de licenties van gekochte software gebruiken.  

####  <a name="BKMK_ExampleDependencies"></a> Voorbeelden van afhankelijkheden  
 De weergegeven hoeveelheid in de Asset Intelligence-rapporten voor geïnstalleerde softwaretitels en licentiegegevens kan afwijken van de werkelijke hoeveelheden die momenteel worden gebruikt. Deze afwijking wordt veroorzaakt door de complexe afhankelijkheden bij het inventariseren van softwarelicentiegegevens voor softwaretitels die worden gebruikt in bedrijfsomgevingen. Met de volgende voorbeelden wordt aangetoond welke afhankelijkheden bij het inventariseren van geïnstalleerde software in het bedrijf met Asset Intelligence invloed kunnen hebben op de nauwkeurigheid van Asset Intelligence-rapporten:  

 **Afhankelijkheden van clienthardware-inventaris**  
 Asset Intelligence geïnstalleerd-rapporten zijn gebaseerd op gegevens die worden verzameld van Configuration Manager-clients door het uitbreiden van hardware-inventaris om in te schakelen Asset Intelligence-rapportage. Vanwege deze afhankelijkheid van hardware-inventarisatie, weerspiegelen de Asset Intelligence-rapporten alleen de gegevens van Configuration Manager-clients die processen voor hardware-inventarisatie is voltooid met de vereiste Asset Intelligence WMI rapportageklassen ingeschakeld. Bovendien omdat Configuration Manager-clients processen voor hardware-inventaris voor een schema gedefinieerd door de gebruiker met beheerdersrechten uitvoert, optreden een vertraging in de gegevensrapportage die van invloed is op de nauwkeurigheid van Asset Intelligence-rapporten. Een geïnventariseerde gelicentieerde softwaretitel kan bijvoorbeeld zijn verwijderd nadat op de client een geslaagde hardware-inventarisatiecyclus is uitgevoerd. De softwaretitel wordt echter weergegeven zoals in de Asset Intelligence-rapporten geïnstalleerd totdat de client volgende geplande hardware-inventaris cyclus voor rapportage.  

 **Afhankelijkheden van softwarepakketten**  
 Omdat Asset Intelligence-rapporten zijn gebaseerd op gegevens van de geïnstalleerde software-titel die worden verzameld met behulp van Configuration Manager client hardware-inventaris standaardprocedures, worden sommige gegevens van de titel software mogelijk niet correct verzameld. Software-installaties die niet voldoen aan standaardinstallatieprocessen of software-installaties die zijn gewijzigd vóór de installatie, kunnen bijvoorbeeld onnauwkeurigheden in Asset Intelligence-rapporten veroorzaken.  

####  <a name="BKMK_LegalLimitations"></a> Juridische beperkingen  
 De informatie die wordt weergegeven in de Asset Intelligence-rapporten is onderworpen aan een groot aantal beperkingen en de informatie die hierin wordt weergegeven vormt geen geldig juridisch, boekhoudkundig of ander professioneel advies. De informatie in Asset Intelligence-rapporten is alleen ter informatie en mag niet worden gebruikt als de enige bron van informatie om de naleving van het gebruik van de softwarelicentie te bepalen.  

 Hieronder worden voorbeelden gegeven van beperkingen bij het inventariseren van het gebruik van geïnstalleerde software en licenties in de onderneming met Asset Intelligence die invloed kunnen hebben op de nauwkeurigheid van Asset Intelligence-rapporten:  

 **Beperkingen voor het aantal gebruikte Microsoft-licenties**  
 -   Het aantal gekochte Microsoft-softwarelicenties wordt gebaseerd op informatie die beheerders opgeven en dit aantal moet zorgvuldig worden gecontroleerd om ervoor te zorgen dat het juiste aantal softwarelicenties wordt weergegeven.  

-   In het gerapporteerde aantal licenties voor Microsoft-software is alleen informatie over Microsoft-softwarelicenties die zijn verkregen via volumelicentieprogramma's verwerkt, geen informatie over softwarelicenties die zijn aangeschaft in de winkel, via een OEM of via andere verkoopkanalen voor softwarelicenties.  

-   Softwarelicenties die de afgelopen 45 dagen zijn aangeschaft, worden mogelijk niet opgenomen in het aantal gerapporteerde Microsoft-softwarelicenties vanwege rapportagevereisten en -planningen van softwareverkopers.  

-   Overdrachten van softwarelicenties vanwege bedrijfsfusies of -overnames worden mogelijk niet weerspiegeld in gerapporteerde aantallen van Microsoft-softwarelicenties.  

-   Andere dan standaardvoorwaarden en -bepalingen in een Microsoft-volumelicentieovereenkomst kunnen invloed op het aantal gerapporteerde softwarelicenties hebben en moeten daarom mogelijk extra worden gecontroleerd door een medewerker van Microsoft.  

 **Beperkingen voor het aantal geïnstalleerde softwaretitels**  
 Configuration Manager-Clients moet hardware-inventaris rapportagecycli voor Asset Intelligence-rapporten voor het correct rapporteren van het aantal geïnstalleerde softwaretitels voltooien. Daarnaast kan er na een geslaagde rapportagecyclus voor de hardware-inventaris een vertraging tussen het installeren of verwijderen van een gelicentieerde softwaretitel optreden die pas in Asset Intelligence-rapporten wordt weergegeven na de volgende geplande hardware-inventarisatie.  

 **Beperkingen voor licentieafstemming**  
 De afstemming van het aantal geïnstalleerde softwaretitels op het aantal gekochte softwarelicenties wordt berekend met behulp van een vergelijking van het licentieaantal is opgegeven door de beheerder en het aantal geïnstalleerde softwaretitels die worden verzameld van Configuration Manager client basisinventarisatie van hardware op basis van de door de beheerder ingestelde planning. Deze vergelijking weerspiegelt niet een definitieve Microsoft-conclusie van de licentieposities. De werkelijke licentiepositie is afhankelijk van de specifieke softwaretitellicentie en verleende gebruiksrechten door de licentievoorwaarden.  

##  <a name="BKMK_ValidationStates"></a> Asset Intelligence-validatiestatussen  
 Asset Intelligence-validatiestatussen weerspiegelen de oorspronkelijke en huidige validatiestatus van Asset Intelligence-catalogusgegevens. In de volgende tabel worden de mogelijke Asset Intelligence-validatiestatussen en de beheerdersacties weergegeven die deze kunnen veroorzaken.  

|**Status**|**Definitie**|**Beheerdersactie**|**Opmerking**|  
|---------------|--------------------|------------------------------|-----------------|  
|**Gevalideerd**|Catalogusitem is gedefinieerd door System Center Online-onderzoekers.|Geen.|Beste status.|  
|**Door de gebruiker gedefinieerd**|Catalogusitem is niet gedefinieerd door System Center Online-onderzoekers.|De lokale catalogusgegevens aangepast.|Deze status wordt weergegeven in Asset Intelligence-rapporten.|  
|**In behandeling**|Catalogusitem is niet gedefinieerd door System Center Online-onderzoekers, maar het item is voor categorisatie ingediend bij System Center Online.|Categorisatie aangevraagd bij System Center Online.|Het catalogusitem behoudt deze status totdat de System Center Online-onderzoekers het item categoriseren en de Asset Intelligence-catalogus is gesynchroniseerd.|  
|**Bij te werken**|Een door de gebruiker gedefinieerd catalogusitem is anders gecategoriseerd door System Center Online tijdens een volgende catalogussynchronisatie.|De lokale Asset Intelligence-catalogus is aangepast om een item als door de gebruiker gedefinieerd te categoriseren.|U kunt de actie Conflict oplossen gebruiken om te bepalen of u de nieuwe categorisatiegegevens of de vorige door de gebruiker gedefinieerde waarde wilt gebruiken. Zie voor meer informatie over het oplossen van conflicten [bewerkingen voor Asset Intelligence in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).|  
|**Niet-gecategoriseerd**|Catalogusitem is niet gedefinieerd door System Center Online-onderzoekers, het item is niet naar System Center Online verzonden voor categorisatie en de beheerder heeft geen door de gebruiker gedefinieerde categoriewaarde toegewezen.|Geen.|Vraag categorisatie aan of pas lokale catalogusgegevens aan.<br /><br /> Zie voor meer informatie over het aanvragen van categorisatie [bewerkingen voor Asset Intelligence in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).<br /><br /> Zie voor meer informatie over het wijzigen van de categorie voor de softwaretitel [bewerkingen voor Asset Intelligence in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).|  

> [!NOTE]  
>  Catalogusitems die voor categorisatie naar System Center Online worden verzonden, hebben de validatiestatus **In behandeling** op een centrale beheersite, maar worden nog met de validatiestatus **Niet-gecategoriseerd** weergegeven op onderliggende primaire sites.  

> [!NOTE]  
>  Nadat een categorisatieconflict is opgelost, wordt het item niet meer gevalideerd als conflicterend tenzij in latere categorisatie-updates nieuwe informatie over het item wordt gepresenteerd.  

 Zie voor voorbeelden van wanneer de validatiestatus mogelijk overgang van een status naar een andere [voorbeeld van validatie van statusovergangen voor Asset Intelligence in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence.md).  
