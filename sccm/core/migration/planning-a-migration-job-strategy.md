---
title: Migratie-taak plannen | Microsoft Docs
description: Gebruik migratietaken om gegevens die u wilt migreren naar uw System Center Configuration Manager-omgeving te configureren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a70bfbd4-757a-4468-9312-1c3b373ef9fc
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
ms.openlocfilehash: 4c83540db763bea039a92633a1d1a808e60e27ad
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="plan-a-migration-job-strategy-in-system-center-configuration-manager"></a>Een strategie voor migratie in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik migratietaken voor het configureren van de gegevens die u wilt migreren naar uw System Center Configuration Manager-omgeving. Migratietaken identificeren de objecten die u wilt migreren en ze worden uitgevoerd op het hoogste niveau in uw doelhiërarchie. U kunt een of meer migratietaken per bronsite instellen. Hiermee kunt u alle objecten tegelijk of beperkte deelverzamelingen van gegevens per taak te migreren.  

 U kunt migratietaken maken nadat Configuration Manager gegevens heeft verzameld van een of meer sites van de bronhiërarchie. U kunt gegevens in elke volgorde migreren vanaf de bronsites die verzamelde gegevens hebben. Met een Configuration Manager 2007-bronsite kunt u gegevens migreren alleen via de site waar een object is gemaakt. Met bronsites uitgevoerd die bij System Center 2012 Configuration Manager of later zijn alle gegevens die u kunt migreren beschikbaar op het hoogste niveau van de bronhiërarchie.  

 Vóór u clients migreert tussen hiërarchieën, moet u ervoor zorgen dat de objecten die clients gebruiken, gemigreerd zijn en dat deze objecten beschikbaar zijn in de doelhiërarchie. Bijvoorbeeld, wanneer u van een Configuration Manager 2007 SP2-bronhiërarchie migreert, wellicht u een aankondiging voor inhoud die is geïmplementeerd naar een aangepaste verzameling die een client heeft. In dit scenario is het raadzaam dat u de verzameling, de advertentie en gekoppelde inhoud migreert voordat u de client migreert. Als de inhoud, de verzameling en de advertentie worden niet gemigreerd vóór de client migreert, moeten deze gegevens kan niet worden gekoppeld aan de client in de doelhiërarchie. Indien een client niet gekoppeld is aan de gegevens van een eerder uitgevoerde advertentie en inhoud, kan de client de inhoud aangeboden worden om die te installeren in de doelhiërarchie, wat overbodig kan zijn. Wanneer de client migreert nadat de gegevens zijn gemigreerd, is de client gekoppeld met deze inhoud en advertentie, en, tenzij de advertentie recurrent is, wordt de client deze inhoud voor de gemigreerde advertentie niet meer aangeboden.  

 Sommige objecten vereisen meer dan de migratie van gegevens van de bronhiërarchie naar de doelhiërarchie. Om te migreren met succes software-updates voor uw clients naar uw doelhiërarchie, moet u bijvoorbeeld een actief software-updatepunt implementeren, de productcatalogus configureren en de software-updatepunt synchroniseren met Windows Server Update Services (WSUS) in de doelhiërarchie.  

 Gebruik de volgende secties om u te helpen plannen voor migratietaken:  

-   [Typen migratietaken](#Types_of_Migration)  

-   [Algemene planning voor alle migratietaken](#About_Migration_Jobs)  

-   [Planning voor verzamelingsmigratietaken](#About_Collection_Migration)  

-   [Planning voor objectmigratietaken](#About_Object_Migration)  

-   [Planning voor eerder gemigreerde objectmigratietaken](#About_Object_Migrations)  

##  <a name="Types_of_Migration"></a>Typen migratietaken  
 Configuration Manager ondersteunt de volgende typen van migratietaken. Elk taaktype is ontworpen om u te helpen de objecten die u in deze taak opnemen kunt te definiëren.  

 **Verzamelingmigratie** (alleen ondersteund bij het migreren van Configuration Manager 2007 SP2): Migreer de objecten die verwant zijn aan de verzamelingen die u selecteert. Standaard sluit de verzamelingmigratie alle objecten die gekoppeld aan leden van de verzameling zijn. U kunt specifieke instanties van objecten uitsluiten wanneer u een verzamelingmigratietaak gebruikt.  

 **Objectmigratie**: Migreer de afzonderlijke objecten die u selecteert. U kunt enkel specifieke gegevens selecteren die u wilt migreren.  

 **Eerder gemigreerde objecten migreren**: Migreer objecten die u eerder hebt gemigreerd wanneer ze zijn bijgewerkt in de bronhiërarchie nadat ze het laatst zijn gemigreerd.  

###  <a name="Objects_that_can_migrate"></a>Objecten die kunnen worden gemigreerd  
 Niet elk object kan gemigreerd worden door een specifiek type migratietaak. In de volgende lijst staat het type objecten dat u kunt migreren met elk type migratietaak.  

> [!NOTE]  
>  Verzamelingsmigratietaken zijn alleen beschikbaar wanneer u objecten vanuit een Configuration Manager 2007 SP2-bronhiërarchie migreert.  

 **Taaktypen die u gebruiken kunt voor het migreren van elk object**  

-   **Advertenties** (beschikbaar voor migratie vanaf ondersteunde Configuration Manager 2007-bronsites)  

    -   Verzamelingmigratie  


-   **Asset Intelligence-catalogus**  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Hardwarevereisten Asset Intelligence**  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Softwarelijst Asset Intelligence**  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Grenzen**  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Configuratiebasislijnen**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Configuratie-items**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Onderhoudsvensters**  

    -   Verzamelingmigratie  


-   **Installatiekopieën van besturingssysteem-implementatie**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Stuurprogrammapakketten voor implementatie van besturingssysteem**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Implementatie van besturingssysteem**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Implementatie van installatiekopieën van besturingssystemen**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Stuurprogrammapakketten voor implementatie van besturingssysteem**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Softwaredistributiepakketten**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Regels voor softwarelicentiecontrole**  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Implementatiepakketten voor software-update**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Software-update-implementatiesjablonen**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Software-update-implementaties**  

    -   Verzamelingmigratie  


-   **Lijsten met software-updates**  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Takenreeksen**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    -   Eerder gemigreerde objecten migreren  

-   **Virtuele toepassingspakketten**  

    -   Verzamelingmigratie  

    -   Objectmigratie  

    > [!IMPORTANT]  
    >  Hoewel u een virtueel toepassingspakket met objectmigratie kunt migreren, kunt u de pakketten niet migreren met het type migratietaak **Eerder gemigreerde objecten migreren**. In plaats daarvan moet u het gemigreerde virtuele toepassingspakket wissen van de doelsite en dan een nieuwe migratietaak maken om de virtuele toepassing te migreren.  

##  <a name="About_Migration_Jobs"></a>Algemene planning voor alle migratietaken  
 Gebruik de wizard migratietaak maken om een migratietaak om objecten te migreren naar uw doelhiërarchie te maken. Het type migratietaak dat u maakt, bepaalt welke objecten beschikbaar zijn voor migratie. U kunt maken en gebruiken van meerdere migratietaken om gegevens te migreren van dezelfde bronsite of van meerdere bronsites. Het gebruik van één type migratietaak blokkeert het gebruik niet van een ander type migratietaak.  

 Wanneer een migratietaak is uitgevoerd, wordt de status ervan weergegeven als **Voltooid** en kan de taak niet nogmaals worden uitgevoerd. U kunt evenwel een nieuwe migratietaak maken om één van de objecten te migreren die door de oorspronkelijke taak gemigreerd werden, en de nieuwe migratietaak kan ook bijkomende objecten bevatten. Wanneer u bijkomende migratietaken maakt, de objecten die eerder zijn gemigreerd weergeven met de status van **gemigreerd**. U kunt deze objecten te migreren ze opnieuw kunt selecteren, maar tenzij het object is bijgewerkt in de bronhiërarchie, deze objecten opnieuw migreren is niet nodig. Als het object in de bronhiërarchie wordt bijgewerkt nadat het is gemigreerd, kunt u dat object herkennen wanneer u het type migratietaak **Objecten gewijzigd na migratie** gebruikt.  

 U kunt een migratietaak verwijderen voordat deze wordt uitgevoerd. Echter nadat een migratietaak is voltooid, blijft zichtbaar in de Configuration Manager-console en kan niet worden verwijderd. Elke migratietaak die voltooid is of is nog niet uitgevoerd blijft zichtbaar in de Configuration Manager-console totdat u het migratieproces voltooien en de migratiegegevens opschoont.  

> [!NOTE]  
>  Nadat u klaar bent met migratie met behulp van de **migratiegegevens opruimen** actie, kunt u dezelfde hiërarchie als de huidige bronhiërarchie om zichtbaarheid te herstellen om de eerder gemigreerde objecten te configureren.  

 U kunt de objecten in een migratietaak in de Configuration Manager-console door de migratietaak te selecteren en vervolgens kiezen weergeven de **objecten in taak** tabblad.  

 Gebruik de informatie in de volgende secties om u te helpen plannen voor migratietaken:  

### <a name="data-selection"></a>Gegevensselectie  
 Wanneer u een verzamelingmigratietaak maakt, moet u één of meerdere verzamelingen selecteren. Nadat u de verzamelingen selecteerde, toont de wizard Maak migratietaak de objecten die gekoppeld aan de verzamelingen zijn. Alle objecten die zijn gekoppeld aan de geselecteerde verzamelingen gemigreerd, maar u kunt de objecten die u niet wilt migreren met deze taak uitschakelen. Wanneer u een object dat afhankelijke objecten heeft uitschakelt, worden deze afhankelijke objecten ook uitgeschakeld. Alle objecten van dit selectievakje uitschakelt, worden toegevoegd aan een uitsluitingslijst staan. Objecten die op een uitsluitingslijst staan, worden verwijderd van automatische selectie voor toekomstige migratietaken. U moet handmatig de uitsluitingslijst bewerken om objecten te verwijderen die u automatisch geselecteerd wenst te zien in migratietaken die u in de toekomst zult maken.  

### <a name="site-ownership-for-migrated-content"></a>Site-eigendom van gemigreerde inhoud  
 Wanneer u inhoud voor implementaties migreert, moet u het inhoudsobject toewijzen aan een site in de doelhiërarchie. Deze site wordt vervolgens de eigenaar van de desbetreffende inhoud in de doelhiërarchie. Hoewel de site op het hoogste niveau van uw doelhiërarchie de site is die de metagegevens voor inhoud feitelijk migreert, is het de toegewezen site die de oorspronkelijke bronbestanden voor de inhoud via het netwerk benadert.  

 Overweeg om eigendom van inhoud over te dragen naar de dichtsbijgelegen site, om de netwerkbandbreedte te minimaliseren die gebruikt wordt tijdens migratie, Omdat informatie over de inhoud wordt gedeeld globaal in System Center Configuration Manager, wordt deze beschikbaar zijn op elke site.  

 Informatie over inhoud wordt gedeeld met alle sites in de doelhiërarchie door middel van databasereplicatie. Inhoud die u toewijst aan een primaire site en vervolgens implementeert op distributiepunten op andere primaire sites zijn echter van overgedragen door middel van bestandsgebaseerde replicatie. De overdracht wordt doorgestuurd via de centrale beheersite en dan naar elke bijkomende primaire site. Door het centraliseren van pakketten die u distribueren naar meerdere primaire sites vóór of tijdens de migratie wilt wanneer u een site als eigenaar van de inhoud toewijst, kunt u gegevensoverdrachten via netwerken met een lage bandbreedte reduceren.  

### <a name="role-based-administration-security-scopes-for-migrated-data"></a>Op rollen gebaseerde beheerbeveiligingsbereiken voor gemigreerde gegevens  
 Wanneer u gegevens naar een doelhiërarchie migreert, moet u een of meer op rollen gebaseerd beheer beveiligingsbereiken toewijzen aan de objecten waarvan gegevens worden gemigreerd. Dit waarborgt dat enkel de geschikte gebruikers met beheerdersrechten toegang hebben tot deze gegevens nadat ze gemigreerd zijn. De beveiligingsbereiken die u specificeert zijn gedefinieerd door de migratietaak en zijn toegepast voor elk object dat gemigreerd is door deze taak. Indien u wenst dat verschillende beveiligingsbereiken worden toegepast op verschillende sets objecten en u wilt bereiken toe te wijzen die tijdens de migratie, moet u de verschillende sets objecten migreren door verschillende migratietaken te gebruiken.  

 Voordat u een migratietaak hebt ingesteld, controleert u hoe op rollen gebaseerd beheer in System Center Configuration Manager werkt. Indien nodig, instellen van een of meer beveiligingsbereiken voor de gegevens die u migreert om te bepalen wie toegang krijgt tot de gemigreerde objecten in de doelhiërarchie.  

 Zie voor meer informatie over beveiligingsbereiken en Rolgebaseerd beheer [basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

### <a name="review-migration-actions"></a>Migratieacties controleren  
 Wanneer u een migratietaak instelt, ziet u de wizard migratietaak maken een lijst van acties die u nemen moet om een succesvolle migratie en een lijst van acties die Configuration Manager tijdens de migratie van de geselecteerde gegevens neemt. Bekijk deze informatie zorgvuldig om te controleren van het verwachte resultaat.  

### <a name="schedule-migration-jobs"></a>Migratietaken plannen  
 Standaard wordt een migratietaak uitgevoerd onmiddellijk nadat hij werd gemaakt. U kunt echter opgeven wanneer de migratietaak wordt uitgevoerd wanneer u de taak maakt of door de eigenschappen van de taak te bewerken. U kunt de migratietaak plannen om als volgt uitvoeren:  

-   Taak nu uitvoeren  

-   Voer de taak op een specifiek begin-tijdstip uit  

-   De taak niet uitvoeren  

### <a name="specify-conflict-resolution-for-migrated-data"></a>Conflictoplossing opgeven voor gemigreerde gegevens  
 Standaard overschrijven niet migratietaken gegevens in de doeldatabase tenzij u de migratietaak configureert om te slaan of te overschrijven gegevens die al eerder is gemigreerd naar de doeldatabase.  

##  <a name="About_Collection_Migration "></a>Planning voor verzamelingsmigratietaken  
 Verzamelingsmigratietaken zijn alleen beschikbaar wanneer u gegevens migreren vanaf een bronhiërarchie waarop een ondersteunde versie van Configuration Manager 2007 uitvoert. Wanneer u per verzameling migreert, moet u een of meer verzamelingen opgeven die u wilt migreren. Voor elke verzameling die u opgeeft, selecteert de migratietaak automatisch alle verwante objecten voor migratie. Als u bijvoorbeeld een specifieke verzameling gebruikers selecteert, worden vervolgens de leden van de verzameling vastgesteld, waarna u de implementatie met betrekking tot die verzameling kunt migreren. U kunt voor de migratie eventueel andere implementatie-objecten selecteren die verband houden met die leden. Al deze geselecteerde items worden aan de lijst van de te migreren objecten toegevoegd.  

 Wanneer u een verzameling migreert, System Center Configuration Manager tevens verzamelingsinstellingen, waaronder onderhoudsvensters en verzamelingsvariabelen, maar er kan geen verzamelingsinstellingen voor AMT-clientinrichting.  

 Gebruik de informatie in de volgende secties voor meer informatie over aanvullende configuraties die migratietaken op basis van een verzameling kunnen toepassen.  

### <a name="exclude-objects-from-collection-migration-jobs"></a>Objecten uitsluiten van verzamelingmigratietaken  
 U kunt specifieke objecten uitsluiten van een verzamelingmigratietaak. Wanneer u een specifiek object van een verzamelingmigratietaak uitsluit, wordt dat object toegevoegd aan een globale uitsluitingslijst dat alle objecten die u hebt uitgesloten van migratietaken die voor elke bronsite in de huidige bronhiërarchie zijn gemaakt heeft. Objecten in de uitsluitingslijst zijn alsnog beschikbaar voor migratie bij toekomstige taken, maar worden niet automatisch opgenomen wanneer u een nieuwe verzameling gebaseerde migratietaak maken.  

 U kunt de uitsluitingslijst zo bewerken, dat objecten die u eerder hebt uitgesloten, worden verwijderd. Wanneer u een object van de uitsluitingslijst hebt verwijderd, wordt deze vervolgens automatisch geselecteerd wanneer een verwante verzameling tijdens het maken van een nieuwe migratietaak wordt opgegeven.  

### <a name="unsupported-collections"></a>Niet-ondersteunde verzamelingen  
 Configuration Manager kunnen standaardgebruikersverzamelingen, apparaatverzamelingen en de meeste aangepaste verzamelingen migreren van een Configuration Manager 2007-bronhiërarchie. Echter Configuration Manager kan geen verzamelingen worden gemigreerd die gebruikers en apparaten in dezelfde verzameling bevatten.  

 De volgende verzamelingen kunnen niet worden gemigreerd:  

-   Een verzameling met gebruikers en apparaten.  

-   Een verzameling met een verwijzing naar een verzameling van een verschillend resourcetype. Bijvoorbeeld: een verzameling op basis van apparaten die een subverzameling of een koppeling naar een verzameling op basis van gebruikers. In dit voorbeeld wordt alleen de op het hoogste niveau verzameling wordt gemigreerd.  

-   Een verzameling met een regel die onbekende computers. De verzameling wordt gemigreerd, maar de regel die onbekende computers bijvoegt niet.  

### <a name="empty-collections"></a>Lege verzamelingen  
 Een lege verzameling is een verzameling waaraan geen resources zijn gekoppeld. Configuration Manager een lege verzameling wordt gemigreerd, wordt de verzameling geconverteerd in een organisatorische map die geen gebruikers of apparaten. Deze map wordt gemaakt met de naam van de lege verzameling onder het **Gebruikersverzamelingen** of **Apparaatverzamelingen** knooppunt in de **activa en naleving** werkruimte in de Configuration Manager-console.  

### <a name="linked-collections-and-subcollections"></a>Gekoppelde verzamelingen en subverzamelingen  
 Wanneer u verzamelingen die zijn gekoppeld aan andere verzamelingen of die subverzamelingen bevatten migreert, Configuration Manager maakt een map onder de **Gebruikersverzamelingen** of **Apparaatverzamelingen** knooppunt naast de gekoppelde verzamelingen en subverzamelingen.  

### <a name="collection-dependencies-and-include-objects"></a>Verzamelingafhankelijkheden en objecten opnemen  
 Wanneer u een verzameling om te migreren in de wizard migratietaak maken opgeeft, worden afhankelijke verzamelingen automatisch geselecteerd om te worden opgenomen met de taak. Dit gedrag zorgt ervoor dat alle benodigde resources na de migratie beschikbaar zijn.  

 Bijvoorbeeld: U selecteert een verzameling voor apparaten waarop Windows 7 wordt uitgevoerd en heet **Win_7**. Deze verzameling is beperkt tot een verzameling die alle uw client-besturingssystemen en heet **All_Clients**. De verzameling **All_Clients** wordt automatisch geselecteerd voor migratie.  

### <a name="collection-limiting"></a>Beperkende verzameling  
 Met System Center Configuration Manager zijn verzamelingen globale gegevens en op elke site in de hiërarchie worden geëvalueerd. Plan daarom hoe u het bereik van een verzameling wilt beperken nadat deze is gemigreerd. U kunt tijdens de migratie een verzameling uit de te gebruiken doelhiërarchie aanduiden om het bereik van de door u gemigreerde verzameling te beperken, zodat de gemigreerde verzameling geen onverwachte leden bevat.  

 In Configuration Manager 2007 worden verzamelingen bijvoorbeeld geëvalueerd op de site waarin ze zijn gemaakt en op onderliggende sites. Er wordt misschien alleen een aankondiging naar een onderliggende site geïmplementeerd, hetgeen het bereik voor die aankondiging zou beperken tot die onderliggende site. In vergelijking met System Center Configuration Manager verzamelingen op elke site geëvalueerd en gekoppelde aankondigingen worden daarna voor elke site geëvalueerd. U kunt met Beperkende verzameling de verzamelingsleden filteren op basis van een andere verzameling, om te voorkomen dat er onverwachte verzamelingsleden worden toegevoegd.  

### <a name="site-code-replacement"></a>Sitecode vervangen  
 Wanneer u een verzameling die criteria bevat die een Configuration Manager 2007-site migreert identificeert, moet u een specifieke site opgeven in de doelhiërarchie. Hiermee zorgt u ervoor dat de gemigreerde verzameling blijft werken in uw doelhiërarchie en het bereik ervan niet groter wordt.  

### <a name="specify-behavior-for-migrated-advertisements"></a>Gedrag voor gemigreerde advertenties opgeven  
 Migratietaken op basis van een verzameling schakelen standaard aankondigingen die naar de doelhiërarchie worden gemigreerd. Dit omvat alle programma's die aan de aankondiging gekoppeld zijn. Wanneer u een migratietaak op basis van een verzameling die aankondigingen is maken, ziet u de **programma's voor implementatie in Configuration Manager inschakelen nadat een advertentie is gemigreerd** kiezen op de **instellingen** pagina van de wizard migratietaak maken. Als u deze optie selecteert, worden programma's ingeschakeld die aan de aankondigingen zijn gekoppeld na hun migratie. Selecteer deze optie niet als een best practice. In plaats daarvan de programma's inschakelen na hun migratie, wanneer u de clients controleert die deze ontvangen.  

> [!NOTE]  
>  U ziet de **programma's voor implementatie in Configuration Manager inschakelen nadat een advertentie is gemigreerd** optie alleen als maakt u een migratietaak die op basis van een verzameling en de migratietaak aankondigingen bevat.  

 Als u wilt een programma na migratie wilt inschakelen, schakelt u **dit programma uitschakelen op computers waar het is aangekondigd** op de **Geavanceerd** tabblad van de programma-eigenschappen.  

##  <a name="About_Object_Migration"></a>Planning voor objectmigratietaken  
 In tegenstelling tot verzamelingmigratie moet u elk object en objectinstantie selecteren dat/die u wilt migreren. U kunt de afzonderlijke objecten zoals (aankondigingen van een Configuration Manager 2007-hiërarchie) of een publicatie van een System Center 2012 Configuration Manager of System Center Configuration Manager-hiërarchie selecteren om toe te voegen aan de lijst met objecten voor een specifieke migratietaak wilt migreren. Objecten die u niet aan de migratielijst toevoegt, worden niet door de objectmigratietaak naar de doelsite gemigreerd.  

 Migratietaken op basis van een object beschikt niet over de aanvullende configuraties kunt plannen, buiten degene die van toepassing op alle migratietaken.  

##  <a name="About_Object_Migrations"></a>Planning voor eerder gemigreerde objectmigratietaken  
 Wanneer een object dat u al naar de doelhiërarchie hebt gemigreerd, wordt bijgewerkt in de bronhiërarchie, kunt u dat object opnieuw migreren met het taaktype **Objecten gewijzigd na migratie**. Bijvoorbeeld, wanneer u wijzigen of bijwerken van de bronbestanden voor een pakket in de bronhiërarchie, de Pakketversie stapsgewijs verhoogd in de bronhiërarchie. Wanneer de pakketversie stapsgewijs is verhoogd, kan het pakket door dit taaktype worden aangeduid voor migratie.  

 Dit taaktype is gelijk aan het objectmigratietype, behalve dat wanneer u objecten selecteert die u wilt migreren, u alleen een selectie kunt maken uit objecten die zijn bijgewerkt nadat deze zijn gemigreerd door een eerdere migratietaak.   

 Wanneer u dit taaktype selecteert, het gedrag voor conflictoplossing op de **instellingen** pagina van de wizard migratietaak maken is geconfigureerd voor eerder gemigreerde objecten te overschrijven. Deze instelling kan niet worden gewijzigd.  

> [!NOTE]  
>  Deze migratietaak kan objecten aanduiden die automaisch worden bijgewerkt door de bronhiërarchie, en objecten die door een gebruiker met beheerdersrechten worden bijgewerkt.  
