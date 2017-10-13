---
title: Gebruik van Asset Intelligence | Microsoft Docs
description: Algemene taken voor Asset Intelligence in System Center Configuration Manager
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8159bd9-5c2b-4d25-82f9-78fcfd732ba9
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 17168e26f13340847928f6e3623115cd4b55997b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-use-asset-intelligence-in-system-center-configuration-manager"></a>Het gebruik van Asset Intelligence in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat informatie over het beheren van typische Asset Intelligence-taken in uw System Center Configuration Manager-hiërarchie:  

##  <a name="BKMK_ViewInformation"></a> Asset Intelligence-informatie weergeven  
 U kunt Asset Intelligence-informatie weergeven op de **Asset Intelligence** -startpagina en in Asset Intelligence-rapporten.  

###  <a name="BKMK_AssetIntelligenceHomePage"></a> Asset Intelligence-startpagina  
 De **Asset Intelligence** -startpagina geeft een overzichtsdashboard voor Asset Intelligence-catalogusinformatie. Op de startpagina kunt u informatie over catalogussynchronisatie en de status van geïnventariseerde software bekijken. De **Asset Intelligence** -startpagina is onderverdeeld in de volgende secties:  

-   **Synchronisatie catalogus**: Bevat informatie over of Asset Intelligence is ingeschakeld, de huidige status van het Asset Intelligence-synchronisatiepunt, de synchronisatieplanning, of de klantlicentieverklaring is geïmporteerd, wanneer de status voor het laatst is bijgewerkt en de tijd voor de volgende geplande update en het aantal wijzigingen dat is opgetreden nadat het sitesysteem van het Asset Intelligence-synchronisatie is geïnstalleerd.  

    > [!NOTE]  
    >  De sectie Synchronisatie catalogus van de **Asset Intelligence** -startpagina wordt alleen weergegeven als de sitesysteemrol Asset Intelligence-synchronisatiepunt is geïnstalleerd.  

-   **Status geïnventariseerde Software**: Bevat het aantal en het percentage van geïnventariseerde software, softwarecategorieën en softwarefamilies die zijn geïdentificeerd door Microsoft, geïdentificeerd door een gebruiker met beheerdersrechten in afwachting van online identificatie of niet-geïdentificeerd en niet in afwachting. De informatie in tabelindeling bevat het aantal voor elke softwaretoepassing, terwijl de informatie in de grafiek het percentage voor elke softwaretoepassing toont.  

 Gebruik de volgende procedure om Asset Intelligence-informatie weer te geven op de **Asset Intelligence** -startpagina.  

##### <a name="to-view-asset-intelligence-information-on-the-asset-intelligence-home-page"></a>Asset Intelligence-informatie weergeven op de Asset Intelligence-startpagina  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**. De Asset Intelligence-rapporten worden weergegeven.  

###  <a name="BKMK_AssetIntelligenceReports"></a> Asset Intelligence-rapporten  
 Er zijn meer dan 60 Asset Intelligence-rapporten waarin de informatie wordt weergegeven die met Asset Intelligence is verzameld. Veel van deze rapporten bevatten koppelingen naar meer gedetailleerde rapporten, waarin u kunt zoeken naar algemene informatie en vervolgens gedetailleerdere informatie kunt weergeven. De Asset Intelligence-rapporten bevinden zich in de Configuration Manager-console in de **bewaking** werkruimte onder de **rapportage** knooppunt. De rapporten bevatten informatie over de hardware, licentiebeheer en software. Zie voor meer informatie over rapporten in Configuration Manager [rapportage in System Center Configuration Manager](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  De nauwkeurigheid van het aantal geïnstalleerde softwaretitels en de licentie-informatie in Asset Intelligence rapporten kan afwijken van het werkelijke aantal geïnstalleerde softwaretitels of gebruikte licenties in de omgeving vanwege de complexe afhankelijkheden en beperkingen bij het inventariseren van softwarelicentie-informatie voor softwaretitels die zijn geïnstalleerd in een bedrijfsomgeving. Asset Intelligence-rapporten mogen niet worden gebruikt als de enige bron voor het bepalen van de naleving van gekochte softwarelicenties.  

 Gebruik de volgende procedure om Asset Intelligence-informatie weer te geven met behulp van de Asset Intelligence-rapporten.  

##### <a name="to-view-collected-asset-intelligence-information-by-using-asset-intelligence-reports"></a>Asset Intelligence-informatie weergeven met behulp van Asset Intelligence-rapporten  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  Vouw in de werkruimte **Bewaking** het gedeelte **Rapportage**uit, vouw **Rapporten**uit en klik op **Asset Intelligence**. De Asset Intelligence-rapporten worden weergegeven.  

    > [!WARNING]  
    >  Als er geen rapportmappen bestaan onder het knooppunt **Rapporten** , controleert u of u rapportage hebt geconfigureerd. Zie voor meer informatie [rapportage in System Center Configuration Manager configureren](../../../../core/servers/manage/configuring-reporting.md).  

3.  Selecteer het Asset Intelligence-rapport dat u wilt uitvoeren en klik vervolgens op het tabblad **Start** in de groep **Rapportgroep** op **Uitvoeren**.  

##  <a name="BKMK_SynchronizeTheCatalog"></a> De Asset Intelligence-catalogus synchroniseren  
 U kunt de lokale Asset Intelligence-catalogus synchroniseren met System Center Online om de meest recente categorisatie van softwaretitels op te halen. Wanneer u handmatig synchronisatie van de catalogus met System Center Online aanvraagt, kan het 15 minuten of langer duren voordat de synchronisatie met System Center Online is voltooid. Configuration Manager-updates de **laatste geslaagde Update** instellen op de **Asset Intelligence** introductiepagina te gaan met de huidige tijd wanneer synchronisatie met succes is voltooid.  

> [!NOTE]  
>  Eerst moet de sitesysteemrol Asset Intelligence-synchronisatiepunt zijn geïnstalleerd voordat u de procedures gebruikt. Zie voor meer informatie over het installeren van een Asset Intelligence-synchronisatiepunt [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Gebruik de volgende procedure om een synchronisateplanning voor de Asset Intelligence-catalogus te maken.  

#### <a name="to-create-a-synchronization-schedule-for-the-asset-intelligence-catalog"></a>Een synchronisateplanning voor de Asset Intelligence-catalogus maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**.  

3.  Op het tabblad **Start** , in de groep **Maken** , klikt u op **Synchroniseren**en klikt u vervolgens op **Synchronisatie plannen**.  

4.  In het dialoogvenster **Planning Asset Intelligence-synchronisatiepunt** selecteert u **Synchronisatie volgens een planning inschakelen**en configureert u vervolgens een eenvoudige of aangepaste planning.  

5.  Klik op **OK** om de wijzigingen op te slaan.  

    > [!NOTE]  
    >  Zie voor informatie over de synchronisatieplannen, met inbegrip van de volgende geplande synchronisatie, het knooppunt **Asset Intelligence** in de werkruimte **Activa en naleving** op de site van het hoogste niveau in de hiërarchie.  

 Gebruik de volgende procedure om de Asset Intelligence-catalogus handmatig te synchroniseren.  

> [!WARNING]  
>  System Center Online accepteert slechts één handmatig synchronisatieverzoek per periode van 12 uur.  

###  <a name="BKMK_ManuallySynchronizeCatalog"></a> De Asset Intelligence-catalogus handmatig synchroniseren  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**.  

3.  Op het tabblad **Start** , in de groep **Maken** , klikt u op **Synchroniseren**, klikt u op **Asset Intelligence-catalogus synchroniseren**en klikt u vervolgens op **OK**.  

##  <a name="BKMK_CustomizeCatalog"></a> De Asset Intelligence-catalogus aanpassen  
 De categorisatie-informatie voor de Asset Intelligence-catalogus die is ontvangen van System Center Online wordt opgeslagen in de sitedatabase met alleen-lezen machtigingen en kan niet worden gewijzigd of verwijderd. U kunt wel aangepaste catalogusgegevens over softwarecategorieën, softwarefamilies, softwarelabels en hardwarevereisten maken, wijzigen of verwijderen. Vervolgens kunt u aangepaste categorisatie-informatie gebruiken in plaats van de informatie die door System Center Online is geleverd voor bestaande of door de gebruiker gedefinieerde softwaretitels. Wanneer u categorisatie-informatie wijzigt of toevoegt, wordt deze beschouwd als door de gebruiker gedefinieerd. Door de gebruiker gedefinieerde categorisatie-informatie wordt opgeslagen in andere databasetabellen dan gevalideerde catalogusinformatie.  

###  <a name="BKMK_SoftwareCategories"></a> Softwarecategorieën  
 Asset Intelligence-softwarecategorieën worden gebruikt om geïnventariseerde softwaretitels breed te categoriseren en worden ook gebruikt als groeperingen op hoog niveau van bepaalde softwarefamilies. Een mogelijke softwarecategorie is bijvoorbeeld energiebedrijven en een softwarefamilie binnen deze softwarecategorie kan olie en gas of hydro-elektrisch zijn. Veel softwarecategorieën zijn vooraf gedefinieerd in de Asset Intelligence-catalogus en u kunt aanvullende door de gebruiker gedefinieerde categorieën maken om geïnventariseerde software maken verder te definiëren. De validatiestatus voor alle vooraf gedefinieerde softwarecategorieën is altijd **Gevalideerd**, terwijl de status van gegevens van aangepaste softwarecategorieën toegevoegd aan de Asset Intelligence-catalogus **Door de gebruiker gedefinieerd**is.  

 Gebruik de volgende procedure voor het maken van een door de gebruiker gedefinieerde softwarecategorie.  

##### <a name="to-create-a-user-defined-software-category"></a>Een door de gebruiker gedefinieerde softwarecategorie maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Catalogus**.  

3.  Op het tabblad **Start** in de groep **Maken** klikt u op **Softwarecategorie maken**.  

4.  Op de pagina **Algemeen** voert u een naam in voor de nieuwe softwarecategorie en geeft u desgewenst een beschrijving op.  

    > [!NOTE]  
    >  De validatiestatus voor alle nieuwe aangepaste softwarecategorieën is altijd ingesteld op **Door de gebruiker gedefinieerd**.  

     Klik op **Volgende**.  

5.  Controleer op de pagina **Samenvatting** de instellingen en klik vervolgens op **Volgende**.  

6.  Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten.  

###  <a name="BKMK_SoftwareFamilies"></a> Softwarefamilies  
 Asset Intelligence-softwarefamilies worden gebruikt om geïnventariseerde softwaretitels binnen softwarecategorieën verder te definiëren. Een mogelijke softwarecategorie is bijvoorbeeld energiebedrijven en een softwarefamilie binnen deze softwarecategorie kan olie en gas of hydro-elektrisch zijn. Veel softwarefamilies zijn vooraf gedefinieerd in de Asset Intelligence-catalogus en u kunt aanvullende door de gebruiker gedefinieerde families maken om geïnventariseerde software maken te definiëren. De validatiestatus voor alle vooraf gedefinieerde softwarefamilies is altijd **Gevalideerd**, terwijl de status van gegevens van aangepaste softwarefamilies toegevoegd aan de Asset Intelligence-catalogus **Door de gebruiker gedefinieerd**is.  

 Gebruik de volgende procedure voor het maken van een door de gebruiker gedefinieerde softwarefamilie.  

##### <a name="to-create-a-user-defined-software-family"></a>Een door de gebruiker gedefinieerde softwarefamilie maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Catalogus**.  

3.  Op het tabblad **Start** in de groep **Maken** klikt u op **Softwarefamilie maken**.  

4.  Op de pagina **Algemeen** voert u een naam in voor de nieuwe softwarefamilie en geeft u desgewenst een beschrijving op.  

    > [!NOTE]  
    >  De validatiestatus voor alle nieuwe aangepaste softwarefamilies is altijd ingesteld op **Door de gebruiker gedefinieerd**.  

5.  Controleer op de pagina **Samenvatting** de instellingen en klik vervolgens op **Volgende**.  

6.  Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten.  

###  <a name="BKMK_SoftwareLabels"></a> Softwarelabels  
 Met aangepaste Asset Intelligence-softwarelabels kunt u filters maken die u kunt gebruiken om softwaretitels te groeperen en te bekijken met behulp van Asset Intelligence-rapporten. U kunt bijvoorbeeld het softwarelabel 'shareware' maken, koppelen aan een aantal toepassingen en vervolgens een rapport uitvoeren dat alle titels met het softwarelabel shareware bevat. De validatiestatus is **Door de gebruiker gedefinieerd** voor alle aangepaste softwarelabels die u toevoegt aan de Asset Intelligence-catalogus.  

 Gebruik de volgende procedure om een aangepast, door de gebruiker gedefinieerd label te maken.  

##### <a name="to-create-a-user-defined-software-label"></a>Een door de gebruiker gedefinieerd softwarelabel maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Catalogus**.  

3.  Op het tabblad **Start** in de groep **Maken** klikt u op **Softwarelabel maken**.  

4.  Op de pagina **Algemeen** voert u een naam in voor de nieuwe softwarefamilie en geeft u desgewenst een beschrijving op.  

    > [!NOTE]  
    >  De validatiestatus voor alle nieuwe aangepaste softwarelabels is altijd ingesteld op **Door de gebruiker gedefinieerd**.  

5.  Controleer op de pagina **Samenvatting** de instellingen en klik vervolgens op **Volgende**.  

6.  Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten.  

###  <a name="BKMK_HardwareRequirements"></a> Hardwarevereisten  
 Aan de hand van informatie over hardwarevereisten kunt u verifiëren dat computers voldoen aan de hardwarevereisten voor softwaretitels voordat ze worden geselecteerd voor software-implementaties. Veel hardwarevereisten zijn vooraf gedefinieerd in de Asset Intelligence-catalogus en u kunt nieuwe door de gebruiker gedefinieerde hardwarevereistegegevens maken om te voldoen aan aangepaste vereisten. De validatiestatus voor alle vooraf gedefinieerde hardwarevereisten is altijd **Gevalideerd**, terwijl de status van gegevens van aangepaste hardwarevereisten toegevoegd aan de Asset Intelligence-catalogus **Door de gebruiker gedefinieerd**is.  

> [!IMPORTANT]  
>  De weergegeven hardwarevereisten in de Configuration Manager-console worden opgehaald uit de Asset Intelligence-catalogus op de lokale computer en niet zijn gebaseerd op informatie over geïnventariseerde softwaretitels van System Center 2012 Configuration Manager-clients. Informatie over hardwarevereisten wordt niet bijgewerkt tijdens de synchronisatie met System Center Online. U kunt door de gebruiker gedefinieerde hardwarevereisten maken voor geïnventariseerde software die geen bijbehorende hardwarevereisten heeft.  

 Gebruik de volgende procedure om een door de gebruiker gedefinieerde vereiste te maken.  

##### <a name="to-create-a-user-defined-hardware-requirements"></a>Door de gebruiker gedefinieerde hardwarevereisten maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Hardwarevereisten**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Hardwarevereisten maken**.  

4.  Voer op de pagina **Algemeen** de volgende informatie in:  

    1.  **Softwaretitel**: Hiermee geeft u de softwaretitel waarvoor de hardwarevereisten gekoppeld zijn. De softwaretitel mag nog niet bestaan in de Asset Intelligence-catalogus.  

    2.  **Validatiestatus**: Toont de validatiestatus als **door de gebruiker gedefinieerde** voor de hardwarevereisten voldoet. U kunt deze instelling niet wijzigen.  

    3.  **Minimale CPU (MHz)**: Hiermee geeft u de minimale processorsnelheid, in megahertz (MHz), vereist voor de softwaretitel.  

    4.  **Minimale hoeveelheid RAM (KB)**: Hiermee geeft u de minimale hoeveelheid RAM, in kilobytes (KB), die vereist is voor de softwaretitel.  

    5.  **Minimale schijfruimte (KB)**: Hiermee geeft u de minimale vrije schijfruimte, in KB, die vereist zijn voor de softwaretitel.  

    6.  **Minimale schijfgrootte (KB)**: Hiermee geeft u de grootte van de minimale harde schijf, in KB, die vereist zijn voor de softwaretitel.  

     Klik op **Volgende**.  

5.  Controleer op de pagina **Samenvatting** de instellingen en klik vervolgens op **Volgende**.  

6.  Klik op de pagina **Voltooiing** op **Sluiten** om de wizard af te sluiten.  

###  <a name="BKMK_ModifyCategorization"></a> Categorisatie-informatie voor geïnventariseerde software wijzigen  
 Vooraf gedefinieerde software in de Asset Intelligence-catalogus is geconfigureerd met specifieke categorisatie-informatie, zoals productnaam, leverancier, softwarecategorie en softwarefamilie. Wanneer de vooraf gedefinieerde categoriesatie-informatie niet aan uw wensen voldoet, kunt u de informatie wijzigen in de eigenschappen van de softwaretitel. Wanneer u categorisatie-informatie voor vooraf gedefinieerde software wijzigt, wordt de validatiestatus voor de software gewijzigd van **Gevalideerd** in **Door de gebruiker gedefinieerd**.  

> [!IMPORTANT]  
>  De categorisatie-informatie kan alleen worden gewijzigd op de site van het hoogste niveau.  

 Gebruik de volgende procedure om categorisatie-informatie voor geïnventariseerde software te wijzigen.  

##### <a name="to-modify-the-categorizations-for-software-titles"></a>De categorisaties voor softwaretitels wijzigen  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Geïnventariseerde software**.  

3.  Selecteer een of meerdere softwaretitels waarvoor u de categorisaties wilt wijzigen.  

4.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

5.  Op het tabblad **Algemeen** kunt u de volgende categorisatie-informatie wijzigen:  

    -   **Productnaam**: Hiermee geeft u de naam van de geïnventariseerde softwaretitel.  

    -   **Leverancier**: Geeft de naam van de leverancier die de geïnventariseerde softwaretitel heeft ontwikkeld.  

    -   **Categorie**: Hiermee geeft u de softwarecategorie die momenteel is toegewezen aan de geïnventariseerde softwaretitel.  

    -   **Familie**: Hiermee geeft u de softwarefamilie die momenteel is toegewezen aan de geïnventariseerde softwaretitel.  

6.  Klik op **OK** om de wijzigingen op te slaan.  

 Gebruik de volgende procedure om software terug te zetten naar de oorspronkelijke categorisatie-informatie.  

### <a name="revert-categorization-information-to-original-settings-for-software"></a>Categorisatie-informatie terugzetten naar de oorspronkelijke software-instellingen  
 Configuration Manager slaat de categorisatie-informatie van System Center Online in de database. De informatie kan niet worden verwijderd. Nadat de informatie is gewijzigd, kunt u deze terugzetten naar de System Center Online-categorisatie. Geïnventariseerde software die niet in de Asset Intelligence-catalogus voorkomt kan ook worden teruggezet naar de oorspronkelijke instellingen.  

 Gebruik de volgende procedure om categorisatie-informatie terug te zetten naar de oorspronkelijke instellingen.  

##### <a name="to-revert-categorization-information-to-original-settings"></a>Categorisatie-informatie terugzetten naar de oorspronkelijke instellingen  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Geïnventariseerde software**.  

3.  Selecteer een of meerdere softwaretitels die u wilt terugzetten naar de oorspronkelijke instellingen. Alleen software met de status **Door de gebruiker gedefinieerd** kan worden teruggezet.  

    > [!TIP]  
    >  Klik op de kolom **Status** om software te sorteren op validatiestatus. Via sorteren kunt u alle software op validatiestatus bekijken en kunt u snel meerdere items selecteren die u wilt terugzetten naar de oorspronkelijke instellingen.  

4.  Klik op het tabblad **Start** in de groep **Product** op **Terugzetten**.  

5.  Klik op **Ja** om de software terug te zetten naar de oorspronkelijke categorisatie-informatie.  

6.  Wanneer u categorisatie-informatie terugzet voor software die in de Asset Intelligence-catalogus voorkomt, wordt de validatiestatus gewijzigd van **Door de gebruiker gedefinieerd** in **Gevalideerd**. Wanneer u software terugzet die niet in de catalogus voorkomt, wordt de validatiestatus gewijzigd van **Door de gebruiker gedefinieerd** in **Niet-gecategoriseerd**.  

##  <a name="BKMK_RequestCatalogUpdate"></a> Een catalogusupdate voor niet-gecategoriseerde softwaretitels aanvragen  
 Informatie over niet-gecategoriseerde softwaretitels kan worden verstuurd naar System Center Online voor onderzoek en categorisatie. Nadat een niet-gecategoriseerde softwaretitel is verzonden en ten minste 4 categorisatie-aanvragen voor dezelfde softwaretitel zijn ingediend door klanten, identificeren en categoriseren onderzoekers de softwaretitel en maken vervolgens de categorisatie-informatie vann de softwaretitel beschikbaar voor alle klanten die van de System Center Online-service gebruikmaken. Microsoft geeft de hoogste prioriteit aan softwaretitels die de meeste aanvragen voor categorisatie hebben. Aangepaste software en Line-Of-Business-toepassingen krijgen waarschijnlijk geen categorie. Als best practice kunt u deze softwaretitels beter niet voor categorisatie naar Microsoft verzenden.  

 Wanneer informatie over een softwaretitel wordt ingediend bij System Center Online voor categorisatie, gelden de volgende voorwaarden:  

-   Alleen basisinformatie over de softwaretitel wordt verzonden naar System Center Online en de te categoriseren informatie over de softwaretitel kan gecontroleerd vóór het indienen.  

-   Informatie over softwarelicenties wordt nooit verzonden.  

-   Een softwaretitel die is geüpload wordt openbaar beschikbaar als onderdeel van de System Center Online-catalogus en kan worden gedownload door andere klanten.  

-   De bron van de softwaretitel wordt niet opgeslagen in de System Center Online-catalogus. Toepassingstitels met vertrouwelijke of bedrijfseigen gegevens moeten niet worden verzonden voor categorisatie door System Center Online.  

> [!NOTE]  
>  Zie voor meer informatie over privacygegevens van Asset Intelligence [beveiliging en privacy voor Asset Intelligence in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence.md).  

 Gebruik de volgende procedure om categorisatie van softwaretitels voor de Asset Intelligence-catalogus aan te vragen bij System Center Online.  

#### <a name="to-request-a-catalog-update-for-uncategorized-software-titles"></a>Een catalogusupdate voor niet-gecategoriseerde softwaretitels aanvragen  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Geïnventariseerde software**.  

3.  Selecteer een of meerdere productnamen die voor categorisatie naar System Center Online worden verzonden. Alleen niet-gecategoriseerde geïnventariseerde softwaretitels kunnen worden verstuurd naar System Center Online voor categorisatie. Als een geïnventariseerde softwaretitel is gecategoriseerd door een beheerder, wat resulteert in een door de gebruiker gedefinieerde status, moet u met de rechtermuisknop op de geïnventariseerde softwaretitel klikken en vervolgens klikken op **Terugzetten** om de softwaretitel terug te zetten naar de status **Niet-gecategoriseerd** voordat deze kan worden verstuurd naar System Center Online voor categorisatie.  

    > [!NOTE]  
    >  Configuration Manager kan maximaal 100 softwaretitels voor categorisatie tegelijk verwerken. Als u meer dan 100 softwaretitels selecteert, worden alleen de eerste 100 softwaretitels verwerkt. U moet de resterende softwaretitels voor categorisatie selecteren in batches van minder dan 100.  

    > [!TIP]  
    >  Klik op de kolom **Status** om software te sorteren op validatiestatus. Hiermee kunt u alle niet-gecategoriseerde productnamen zien en snel meerdere items selecteren die u wilt indienen voor categorisatie.  

4.  Klik op het tabblad **Start** in de groep **Product** op **Verzoek tot bijwerken van catalogus**.  

5.  Lees het System Center Online-privacybericht over het indienen voor categorisatie. Klik op **Details** om de informatie weer te geven die wordt verzonden naar System Center Online.  

6.  Selecteer **Ik heb deze melding gelezen en begrepen**en klik vervolgens op **OK** zodat de geselecteerde softwaretitels kunnen worden verzonden voor categorisatie.  

7.  Controleer of de status van de geïnventariseerde softwareproductnamen die bij System Center Online zijn ingediend voor categorisatie is gewijzigd van **Niet-gecategoriseerd** in **In behandeling**.  

    > [!NOTE]  
    >  Software die wordt verzonden naar System Center Online voor categorisatie heeft de validatiestatus **In behandeling** op een centrale beheersite en wordt weergegeven met de validatiestatus **Niet-gecategoriseerd** op onderliggende primaire sites.  

##  <a name="BKMK_ResolveSoftwareDetails"></a> Conflicten met softwaredetails oplossen  
 Nadat bijgewerkte details van softwarecategorisatie zijn ontvangen van System Center Online die conflicteren met bestaande softwaredetails, kunt u kiezen hoe u het conflict wilt oplossen. Software met een actueel conflict heeft de validatiestatus **Bijwerkbaar**. Nadat een conflict met softwaredetails is opgelost, wordt de informatie van softwarecategorisatie bewaard in de Asset Intelligence-catalogus overeenkomstig de instelling die u opgeeft. Een conflict met softwaredetails doet zich niet voor voor dezelfde softwarecategorisatiewaarde tenzij de System Center Online waarde wijzigt nadat het conflict is opgelost.  

 Gebruik de volgende procedure om een conflict met softwaredetails op te lossen.  

#### <a name="to-resolve-a-software-details-conflict"></a>Een conflict met softwaredetails oplossen  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik in de werkruimte **Activa en naleving** op **Asset Intelligence**en klik vervolgens op **Geïnventariseerde software**.  

3.  Controleer de kolom **Status** op softwaretitels met de status **Bijwerkbaar** .  

4.  Selecteer de softwaretitel waarvoor u een conflict moet oplossen en klik vervolgens op het tabblad **Start** , in de groep **Product** en klik op **Conflict oplossen**.  

5.  Controleer de volgende informatie:  

    -   **Lokale waarde**: Hiermee geeft u de bestaande informatie over softwarecategorisatie in de Asset Intelligence-catalogus die in conflict is met nieuwere System Center Online-details voor softwarecategorisatie.  

    -   **Gedownloade waarde**: Hiermee geeft u de nieuwe System Center Online softwarecategorisatie-informatie voor de conflicterende Asset Intelligence-catalogus over softwarecategorisatie.  

6.  Selecteer een van de volgende instellingen om het conflict met softwaredetails op te lossen:  

    -   **Wijzig de lokaal bewerkte catalogusinformatiewaarde niet**: Wordt het conflict met softwaredetails opgelost met behoud van de bestaande Asset Intelligence-catalogus softwarecategorisatie-informatie. Wanneer u deze instelling selecteert, wordt de status van de softwaretitel veranderd van **Bijwerkbaar** in **Door de gebruiker gedefinieerd**.  

    -   **De lokaal bewerkte catalogusinformatiewaarde overschrijven met de gedownloade System Center Online waarde**: Wordt het conflict met softwaredetails opgelost door de bestaande Asset Intelligence-catalogusinformatie van softwarecategorisatie overschrijven met nieuw verkregen informatie van System Center Online. Wanneer u deze instelling selecteert, wordt de status van de softwaretitel veranderd van **Bijwerkbaar** in **Gevalideerd**.  

     Klik op **OK** om de conflictoplossing op te slaan.  
