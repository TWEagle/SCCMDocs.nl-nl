---
title: Cloud-gebaseerde distributiepunt | Microsoft Docs
description: Meer informatie over configuraties en beperkingen voor het gebruik van een cloud-gebaseerde distributiepunt met System Center Configuration Manager.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cd9c725-6b42-427d-9191-86e67f84e48c
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6ee0ed635ab81b5e454e3cd85637ff3e20dbb34
ms.openlocfilehash: 8caf3319d93b98680ed4a719a8db714c7e4e96ce
ms.contentlocale: nl-nl
ms.lasthandoff: 06/08/2017


---
# <a name="use-a-cloud-based-distribution-point-with-system-center-configuration-manager"></a>Een clouddistributiepunt voor System Center Configuration Manager gebruiken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een cloud-gebaseerde distributiepunt is een System Center Configuration Manager-distributiepunt dat wordt gehost in Microsoft Azure. De volgende informatie gaat over configuraties en beperkingen voor het gebruik van een distributiepunt in de cloud.

Nadat u hebt geïnstalleerd op een primaire site en kunt u een cloud-gebaseerde distributiepunt installeert, Zie [cloud-gebaseerde distributiepunten installeren in Azure](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md).


## <a name="plan-to-use-a-cloud-based-distribution-point"></a>Het gebruik van een distributiepunt in de cloud plannen
Als u een clouddistributie gebruikt, kunt u het volgende:  

-   **Configureren van clientinstellingen** om in te schakelen gebruikers en apparaten toegang tot de inhoud.  

-   **Een primaire site opgeven voor de overdracht van inhoud** naar het distributiepunt.  

-   **Drempels opgeven** voor de hoeveelheid inhoud die u wilt opslaan op het distributiepunt en de hoeveelheid inhoud die u wilt inschakelen voor clients om over te dragen van het distributiepunt.  


Op basis van de drempels die u configureert, kan Configuration Manager waarschuwingen die u waarschuwen wanneer de gecombineerde hoeveelheid inhoud die u hebt opgeslagen op het distributiepunt in de buurt van de opgegeven opslaghoeveelheid, of wanneer een gegevensoverdracht door clients de drempels benadert die u hebt gedefinieerd.  

Cloud-gebaseerde distributiepunten ondersteunen verschillende functies die ook worden aangeboden via on-premises distributiepunten:  

-   U beheert distributiepunten in de cloud-gebaseerde individueel of als leden van distributiepuntgroepen.  

-   U kunt een cloud-gebaseerd distributiepunt gebruiken als een locatie terugvalinhoudlocatie.  

-   U ontvangt ondersteuning voor clients op het intranet en Internet.  


Cloud-gebaseerde distributiepunten bieden de volgende extra voordelen:  

-   Inhoud die wordt verzonden naar een cloud-gebaseerd distributiepunt wordt door Configuration Manager versleuteld voordat Configuration Manager naar Azure verzonden.  

-   In Azure, kunt u de cloudservice om te voldoen aan veranderende verzoeken voor inhoudsaanvragen door clients zonder de vereiste voor het installeren en het inrichten van extra distributiepunten handmatig schalen.  

-   Het distributiepunt in de cloud ondersteunt de download van inhoud door clients die zijn geconfigureerd voor Windows BranchCache.  


Een distributiepunt in de cloud heeft de volgende beperkingen:  

-  Voordat u versie 1610 met de Hotfix KB4010155, kunt u een cloud-gebaseerde distributiepunt host software-updatepakketten niet gebruiken. Dit probleem is opgelost met versie 1702 begin- en hoger.  

-   Kunt u een cloud-gebaseerde distributiepunt voor PXE of ingeschakelde multicast-implementaties.  

-   Clients krijgen geen distributiepunt in de cloud aangeboden als een inhoudslocatie voor een takenreeks die is geïmplementeerd met behulp van de implementatieoptie **De inhoud lokaal downloaden wanneer deze nodig is voor de takenreeks die wordt uitgevoerd**. Takenreeksen die worden geïmplementeerd met behulp van de implementatieoptie **Alle inhoud lokaal downloaden voordat de takenreeks wordt gestart** , kunnen een distributiepunt in de cloud echter gebruiken als een geldige inhoudslocatie.  

-   Een distributiepunt in de cloud ondersteunt geen pakketten die vanaf het distributiepunt worden uitgevoerd. Alle inhoud moet worden gedownload door de client en vervolgens lokaal worden uitgevoerd.  

-   Een distributiepunt in de cloud ondersteunt geen streamingtoepassingen met behulp van Application Virtualization of gelijkaardige programma's.  

-   Een distributiepunt in de cloud biedt geen ondersteuning voor voorbereide inhoud. De distribution manager van de primaire site die het distributiepunt beheert verwijzen verzendt alle inhoud naar het distributiepunt.  

-   Een clouddistributiepunt kan niet worden geconfigureerd als een pull-distributiepunt.  

##  <a name="BKMK_PrereqsCloudDP"></a> Vereisten voor clouddistributiepunten  
 Een distributiepunt in de cloud vereist de volgende vereiste onderdelen voor het gebruik ervan:  

-   Een abonnement op Azure (Zie [over abonnementen en certificaten](#BKMK_CloudDPCerts) in dit onderwerp).

-   Een zelfondertekend of openbare-sleutelinfrastructuur (PKI)-beheercertificaat voor communicatie vanaf een primaire siteserver van Configuration Manager naar de cloudservice in Azure (Zie [over abonnementen en certificaten](#BKMK_CloudDPCerts) in dit onderwerp).

-   Een servicecertificaat (PKI) waarmee Configuration Manager-clients verbinding maken met cloud-gebaseerde distributiepunten en inhoud daarvan te downloaden met behulp van HTTPS.  

-  Een apparaat of gebruiker moet hebben **toegang geven tot cloud distribution points** ingesteld op **Ja** in de client instellen van **Cloudservices** voordat een apparaat of gebruiker toegang inhoud van een cloud-gebaseerd distributiepunt tot. Deze waarde is standaard ingesteld op **Nee**.  

-   Een client moet de naam van de cloudservice waarvoor een Domain Name System (DNS)-alias en een CNAME-record in uw DNS-naamruimte kunnen omzetten.  

-   Een client moet toegang kunnen hebben tot het Internet om het distributiepunt in de cloud te gebruiken.  

##  <a name="BKMK_CloudDPCost"></a> De kosten van het gebruik van clouddistributie  
 Wanneer u een cloud-gebaseerd distributiepunt gebruikt, kunt u plannen voor de kosten van gegevensopslag en de download-overdrachten die Configuration Manager-clients uitvoeren.  

 Configuration Manager bevat opties voor het beheer van kosten en toegang tot gegevens kunt controleren:  

-   U kunt de hoeveelheid inhoud die u in een cloudservice opslaat beheren en controleren.  

-   U kunt Configuration Manager om u te waarschuwen wanneer **drempelwaarden** voor clientdownloads bereiken of maandelijkse limieten overschrijden.  

-   U kunt bovendien peer-caching (Windows BranchCache) gebruiken om te beperken het aantal gegevensoverdrachten van cloud-gebaseerde distributiepunten door clients. Configuration Manager-clients die zijn geconfigureerd voor BranchCache kunnen inhoud overbrengen met behulp van cloud-gebaseerde distributiepunten.  


**Opties:**  

-   **Clientinstellingen voor Cloud**: Beheren van toegang tot alle cloud-gebaseerde distributiepunten in een hiërarchie met behulp van **clientinstellingen**.  

     In **Clientinstellingen**ondersteunt de categorie **Cloudinstellingen** de instelling **Toegang toestaan tot clouddistributiepunten**. Deze waarde is standaard ingesteld op **Nee**. U kunt deze instelling inschakelen voor gebruikers en apparaten.  

-   **Drempelwaarden voor gegevensoverdracht**: U kunt drempels opgeven voor de hoeveelheid gegevens die u wilt opslaan op het distributiepunt en voor de hoeveelheid gegevens die clients kunnen downloaden vanaf het distributiepunt.  

     Drempelwaarden voor clouddistributiepunten zijn:  

    -   **Waarschuwingsdrempel voor opslag**: Een drempel voor Opslagwaarschuwing stelt een bovenlimiet in voor de hoeveelheid gegevens of inhoud die u wilt opslaan op het cloud-gebaseerde distributiepunt. Configuration Manager kan een waarschuwing genereren wanneer de resterende vrije ruimte is bereikt die u opgeeft.  

    -   **Overdrachtmeldingsdrempel**: Een overdrachtmeldingsdrempel helpt u bij het controleren van de hoeveelheid inhoud die wordt overgedragen van het distributiepunt naar clients gedurende een periode van 30 dagen. De overdrachtmeldingsdrempel bewaakt de overdracht van gegevens voor de afgelopen 30 dagen en kan een waarschuwing en een kritieke waarschuwing genereren wanneer overdrachten waarden bereikt die u definieert.  

        > [!IMPORTANT]  
        >  Configuration Manager bewaakt de overdracht van gegevens, maar stopt de overdracht van gegevens boven de opgegeven overdrachtwaarschuwingsdrempel niet.  

 U kunt drempels opgeven voor elk clouddistributiepunt tijdens de installatie van het distributiepunt of u kunt de eigenschappen bewerken van elk clouddistributiepunt nadat het geïnstalleerd is.  

-   **Waarschuwingen**: U kunt de Configuration Manager voor het genereren van waarschuwingen over gegevensoverdrachten naar en van elk cloud-gebaseerde distributiepunt op basis van de drempelwaarden voor gegevensoverdracht die u opgeeft. Deze waarschuwingen helpen u gegevensoverdrachten te bewaken en kunt u beslissen wanneer de cloudservice stopt, pas de inhoud die u opslaat op het distributiepunt of wijzigen welke clients kunnen cloud-gebaseerd distributiepunt gebruiken verwijst.  

     In een cyclus van een uur, de primaire site die het clouddistributiepunt bewaakt transactiegegevens gedownload van Azure en slaat ze op in de CloudDP -&lt;ServiceName\>.log op de siteserver. Configuration Manager beoordeelt vervolgens deze informatie met betrekking tot de opslag- en overdrachtquota voor elk cloud-gebaseerd distributiepunt. Wanneer de overdracht van gegevens bereikt of het opgegeven volume voor waarschuwingen of kritieke waarschuwingen overschrijdt, Configuration Manager de juiste melding genereert.  

    > [!WARNING]  
    >  Omdat informatie over gegevensoverdrachten wordt gedownload van Azure hourly, dat kan gegevensgebruik een waarschuwing of kritieke drempelwaarde voordat Configuration Manager kunt toegang de gegevens tot en een melding kan genereren.  

    > [!NOTE]  
    >  Waarschuwingen voor een cloud-gebaseerde distributiepunt hangen af van gebruikersstatistieken van Azure, dit kan tot 24 uur beschikbaar duren. Zie voor informatie over Opslaganalyse voor Azure, met inbegrip van hoe vaak Azure updates gebruik maken van statistieken, [Opslaganalyse](http://go.microsoft.com/fwlink/p/?LinkID=275111) in de MSDN-bibliotheek.  


-   **Stoppen of starten van de cloudservice op aanvraag**: De optie kunt u een cloudservice op elk gewenst moment om te voorkomen dat clients met behulp van de service continu te stoppen. Wanneer u de cloudservice stopt, verhindert u onmiddellijk clients om bijkomende inhoud te downloaden van de service. Bijkomend kunt u de cloudservice opnieuw opstarten om toegang te herstellen voor clients. Bijvoorbeeld zou u kunnen de cloudservice willen stoppen wanneer gegevensdrempels bereikt zijn.  

     Wanneer u een cloudservice stopt, wist de cloudservice niet de inhoud van het distributiepunt en verhindert ze de siteserver niet om bijkomende inhoud over te dragen van het clouddistributiepunt.  

     Als u wilt stoppen van een cloudservice in de Configuration Manager-console, selecteert u het distributiepunt in de **Clouddistributiepunten** knooppunt onder **Cloudservices**, in de **beheer** werkruimte. Kies vervolgens **-service stoppen** stoppen van de cloudservice die wordt uitgevoerd in Azure.  

##  <a name="BKMK_CloudDPCerts"></a> Abonnementen en certificaten voor clouddistributiepunten  
 Cloud-gebaseerde distributiepunten vereisen certificaten om in te schakelen van Configuration Manager voor het beheren van de cloudservice die het distributiepunt host, en voor clients voor toegang tot inhoud van het distributiepunt. De volgende informatie bevat een overzicht over deze certificaten. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md) voor gedetailleerdere informatie.  

 **Certificaten**  

-   **Beheercertificaat voor siteserver naar distributiepunt communicatie**: Het beheercertificaat brengt een vertrouwensrelatie tussen de Azure management API en de Configuration Manager tot stand. Deze methode kunt Configuration Manager op de Azure-API niet aanroepen wanneer u taken uitvoert zoals het distribueren van inhoud of het starten en de cloudservice wordt gestopt. U kunt uw eigen beheercertificaten zelfondertekende certificaten of certificaten die zijn uitgegeven door een certificeringsinstantie (CA) te maken met behulp van Azure:  

    -   Geef het .cer-bestand van het beheercertificaat naar Azure wanneer u Azure voor Configuration Manager configureren. Het .cer-bestand bevat de publieke sleutel voor het beheercertificaat. Voordat u een cloud-gebaseerde distributiepunt installeert, moet u dit certificaat uploaden naar Azure. Dit certificaat kunt Configuration Manager voor toegang tot de Azure-API.  

    -   Geef het .pfx-bestand van het beheercertificaat aan Configuration Manager wanneer u het cloud-gebaseerde distributiepunt installeert. Het PFX-bestand bevat de persoonlijke sleutel voor het beheercertificaat. Configuration Manager slaat dit certificaat in de sitedatabase. Omdat het .pfx-bestand de persoonlijke sleutel bevat, moet u het wachtwoord op voor het importeren van dit certificaatbestand in de Configuration Manager-database opgeven.  

    Als u een zelfondertekend certificaat maakt, moet u het certificaat eerst exporteren als een cer-bestand en vervolgens opnieuw exporteren als een .pfx-bestand.  

    Desgewenst kunt u een versie één **.publishsettings** bestand van de Azure SDK 1.7. Raadpleeg de documentatie van Azure voor meer informatie over .publishsettings-bestanden.  

    Zie voor meer informatie [het maken van een beheercertificaat](http://go.microsoft.com/fwlink/p/?LinkId=220281) en [een beheercertificaat toevoegen aan een Azure-abonnement](http://go.microsoft.com/fwlink/p/?LinkId=241722) in de Azure-platform-sectie van de MSDN-bibliotheek.  

-   **Servicecertificaat voor clientcommunicatie naar het distributiepunt**: De Configuration Manager clouddistributiepunt-servicecertificaat vertrouwensrelatie tussen de Configuration Manager-clients en het cloud-gebaseerde distributiepunt te worden ingesteld en beveiligt de gegevens die clients daarvan downloaden met behulp van Secure Socket Layer (SSL) via HTTPS.  

    > [!IMPORTANT]  
    >  De algemene naam in het certificaatvak van het servicecertificaat moet uniek zijn in uw domein en mag niet overeenkomen met het apparaat dat lid is van een domein.  

   Zie de sectie voor een Voorbeeldimplementatie van dit certificaat, **het servicecertificaat voor cloud-gebaseerde distributiepunten implementeren** in het onderwerp [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

##  <a name="bkmk_Tasks"></a> Algemene beheertaken voor clouddistributiepunten  

-   **Siteserver naar de cloud-gebaseerd distributiepunt communicatie**: Wanneer u een cloud-gebaseerde distributiepunt installeert, moet u één primaire site voor het beheren van de overdracht van inhoud naar de cloudservice toewijzen. Deze actie is gelijk aan het installeren van de sitesysteemrol van distributiepunt op een specifieke site.  

-   **Cloud-gebaseerd distributiepunt punt communicatie tussen clients**: Wanneer een apparaat of gebruiker van een apparaat met de clientinstelling die het gebruik van een cloud-gebaseerde distributiepunt is geconfigureerd, kan het apparaat het clouddistributiepunt ontvangen als een geldige Inhoudslocatie:  

    -   Het cloud-gebaseerde distributiepunt als een extern distributiepunt beschouwd wanneer een client beschikbare inhoudslocaties evalueert.  

    -   Cloud-gebaseerde distributiepunten clients op het intranet alleen gebruiken als een terugvaloptie als on-premises distributiepunten niet beschikbaar.  

    Hoewel u cloud-gebaseerde distributiepunten in specifieke gebieden van Azure installeert, worden clients die gebruikmaken van cloud-gebaseerde distributiepunten zijn niet op de hoogte van de Azure-regio's en niet-deterministische wijze een cloud-gebaseerde distributiepunt selecteren.

Dit betekent dat als u cloud-gebaseerde distributiepunten in meerdere gebieden installeert en een client meerdere cloud-gebaseerde distributiepunten als inhoudslocaties ontvangt, de client geen een cloud-gebaseerde distributiepunt uit dezelfde Azure-regio als de client gebruikt mogelijk.  

Clients die gebruikmaken van cloud-gebaseerde distributiepunten gebruiken de volgende reeks voor aanvragen van de locatie van inhoud:  

1.  Een client die is geconfigureerd om distributiepunten in de cloud te gebruiken, probeert altijd eerst inhoud te verkrijgen uit een voorkeursdistributiepunt.  

2.  Wanneer een voorkeursdistributiepunt niet beschikbaar is, gebruikt de client een extern distributiepunt, als de implementatie deze optie ondersteunt, en als een extern distributiepunt beschikbaar is.  

3.  Wanneer er geen voorkeursdistributiepunt of extern distributiepunt beschikbaar is, kan de client terugvallen om de inhoud van een distributiepunt in de cloud te verkrijgen.  



  Wanneer een client een cloud-gebaseerde distributiepunt als een Inhoudslocatie gebruikt, verifieert de client zichzelf aan het cloud-gebaseerde distributiepunt met behulp van een toegangstoken van Configuration Manager. Als de client het certificaat van Configuration Manager cloud-gebaseerd distributiepunt punt vertrouwt, kan de client vervolgens de gevraagde inhoud downloaden.  

-   **Cloud-gebaseerde distributiepunten bewaken**: U kunt de inhoud die u naar elk cloud-gebaseerde distributiepunt implementeert bewaken en u kunt de cloudservice bewaken die als host fungeert voor het distributiepunt.  

    -   **Inhoud**: U bewaakt de inhoud die u naar een cloud-gebaseerde distributiepunt dezelfde manier als die u doen implementeert wanneer u inhoud voor on-premises distributiepunten implementeren.  

    -   **Cloudservice**: Configuration Manager controleert periodiek de Azure service en genereert een waarschuwing als de service niet actief is of als er zijn problemen met abonnementen of certificaten. U kunt ook details zien over het distributiepunt in de **Clouddistributiepunten** knooppunt onder **Cloudservices** in de **beheer** werkruimte van de Configuration Manager-console. Vanuit deze locatie ziet weergeven u informatie over het distributiepunt op hoog niveau. U kunt ook een distributiepunt selecteren en vervolgens de eigenschappen bewerken.  

    Wanneer u de eigenschappen van een clouddistributiepunt bewerkt, kunt u het volgende doen:  

    -   De gegevensdrempels voor opslag en waarschuwingen.  

    -   Inhoud beheren zoals u zou doen voor een on-premises distributiepunt.  

    Tenslotte kunt u voor elk clouddistributiepunt het abonnement-ID, de servicenaam en andere gerelateerde details, die worden gespecificeerd wanneer het clouddistributiepunt wordt geïnstalleerd, zien, maar niet bewerken.  

-   **Back-up en herstel voor cloud-gebaseerde distributiepunten**: Wanneer u een cloud-gebaseerd distributiepunt in uw hiërarchie gebruikt, gebruik de volgende informatie om te plannen voor back-up of herstel van het distributiepunt:  

    -   Wanneer u de vooraf gedefinieerde gebruikt **back-upserver van Site** onderhoudstaak gebruikt, Configuration Manager omvat automatisch de configuraties voor de cloud-gebaseerd distributiepunt.  

    -   Het is een best practice back-up en sla een kopie van zowel de beheercertificaat en servicecertificaat die worden gebruikt met een cloud-gebaseerd distributiepunt. Als u de primaire site van Configuration Manager die het cloud-gebaseerd distributiepunt naar een andere computer beheert herstelt, moet u de certificaten opnieuw importeren voordat u kunt doorgaan met ze te gebruiken.  

-   **Verwijderen van een cloud-gebaseerde distributiepunt** : Wilt u een cloud-gebaseerde distributiepunt verwijderen, selecteert u het distributiepunt in de Configuration Manager-console en selecteer vervolgens **verwijderen**.  

    Wanneer u een clouddistributiepunt uit een hiërarchie verwijdert, verwijdert Configuration Manager de inhoud van de cloudservice in Azure.  

