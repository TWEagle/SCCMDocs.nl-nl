---
title: "Een sitehiërarchie ontwerpen "
titleSuffix: Configuration Manager
description: "Overzicht van de beschikbare topologieën en beheeropties voor System Center Configuration Manager zodat u kunt uw sitehiërarchie plannen."
ms.custom: na
ms.date: 8/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 07ce872e-1558-42ad-b5ad-582c5b1bdbb4
caps.latest.revision: "22"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 845ec5210b9055ff9c52039a32f008b1baa36413
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2018
---
# <a name="design-a-hierarchy-of-sites-for-system-center-configuration-manager"></a>Een sitehiërarchie ontwerpen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u de eerste site van een nieuwe System Center Configuration Manager-hiërarchie installeert, is het een goed idee om te begrijpen van de beschikbare topologieën voor Configuration Manager, de typen beschikbare sites en hun relaties met elkaar en het bereik van beheer van elk sitetype.
Vervolgens, met inbegrip van opties voor inhoudbeheer die kunnen Verminder het aantal sites die u wilt installeren, u kunt een topologie die behoeften van uw huidige bedrijf efficiënt fungeert plannen en later kunt uitbreiden voor het beheren van toekomstige groei.  

Bij het plannen, houd er rekening mee beperkingen voor het toevoegen van extra sites aan een hiërarchie of een zelfstandige site:
-   U kunt een nieuwe primaire site onder een centrale beheersite tot installeren de [ondersteund aantal primaire sites](/sccm/core/plan-design/configs/size-and-scale-numbers) voor de hiërarchie.
-   U kunt [uitbreiden een zelfstandige primaire site voor het installeren van een nieuwe centrale beheersite](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand), zodat u kunt vervolgens extra primaire sites installeren.
-   U kunt maximaal nieuwe secundaire sites onder een primaire site installeren [ondersteund limieten voor de primaire site](/sccm/core/plan-design/configs/size-and-scale-numbers) en volledige hiërarchie.
-   U kunt een eerder geïnstalleerde site kan niet toevoegen aan een bestaande hiërarchie samenvoegen van twee zelfstandige sites. Alleen de installatie van de nieuwe sites aan een bestaande hiërarchie van sites wordt ondersteund.


> [!NOTE]
> Bij het plannen van een nieuwe installatie van Configuration Manager zich bewust zijn van de [release-opmerkingen]( /sccm/core/servers/deploy/install/release-notes), actuele problemen in de actieve versies die worden in detail beschreven. De releaseopmerkingen gelden voor alle vertakkingen van Configuration Manager.  Wanneer u echter gebruiken de [Technical Preview vertakking]( /sccm/core/get-started/technical-preview), vindt u problemen alleen op dat filiaal in de documentatie voor elke versie van de Technical Preview.  

##  <a name="bkmk_topology"></a>Hiërarchietopologie  
 Hiërarchietopologieën variëren van één zelfstandige primaire site naar een groep verbonden primaire en secundaire sites met een centrale beheersite op het hoogste niveau (bovenste) van de hiërarchie.   De belangrijkste factor voor het type en aantal sites die u in een hiërarchie gebruikt is gewoonlijk het aantal en type apparaten dat u, als volgt ondersteunen moet:   

 **Zelfstandige primaire site:** Gebruik van een zelfstandige primaire site als een enkele primaire site beheer van al uw apparaten en gebruikers ondersteunen kan (Zie [grootte en schaalgetallen](/sccm/core/plan-design/configs/size-and-scale-numbers)). Deze topologie is ook geslaagde bij uw bedrijf verschillende geografische locaties kunnen met succes worden geleverd door een enkele primaire site.  Om te helpen het netwerkverkeer beheren, kunt u voorkeursbeheerpunten en een zorgvuldig geplande inhoudsinfrastructuur (Zie [basisconcepten voor inhoudsbeheer in System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)).  

 Voordelen van deze topologie zijn onder andere:  

-   Vereenvoudigde administratieve overhead.  

-   Vereenvoudigde clientsitetoewijzing en detectie van beschikbare resources en services.  

-   Het verwijderen van eventuele vertraging weg die geïntroduceerd door databasereplicatie tussen sites.

-   De optie voor het uitbreiden van een zelfstandige primaire hiërarchie naar een grotere hiërarchie met een centrale beheersite. Hiermee kunt u nieuwe primaire sites installeren om de schaal van uw implementatie te vergroten.  


**Centrale beheersite met een of meer onderliggende primaire sites:** Deze topologie gebruiken wanneer u meer dan één primaire site voor de ondersteuning van beheer van uw apparaten en gebruikers vereist.  Dit is verplicht als u wilt meer dan één primaire site. Voordelen van deze topologie zijn onder andere:  


-   Het ondersteunt maximaal 25 primaire sites waarmee u de schaal van uw hiërarchie uitbreiden.  

-   (Tenzij u uw sites opnieuw installeert), wordt u altijd de centrale beheersite gebruiken. Dit is een permanente optie. U kunt een onderliggende primaire site zodat het een zelfstandige primaire site kan niet loskoppelen.

 In de volgende secties leest u wanneer u een specifieke site- of inhoudbeheeroptie in plaats van een extra site gebruikt.  

##  <a name="BKMK_ChooseCAS"></a>Bepalen wanneer een centrale beheersite gebruiken  
 Gebruik een centrale beheersite binnen de gehele hiërarchie-instellingen te configureren en bewaken van alle sites en objecten in de hiërarchie. Dit sitetype beheert clients niet rechtstreeks, maar het coördineert gegevensreplicatie tussen sites, waaronder de configuratie van sites en clients in de gehele hiërarchie.  

**De volgende informatie kunt u bepalen wanneer u een centrale beheersite installeert:**  

-   De centrale beheersite is het hoogste niveau in een hiërarchie.  

-   Wanneer u een hiërarchie met meer dan één primaire site configureert, moet u een centrale beheersite installeren. Als u twee of meer primaire sites onmiddellijk moeten, installeert u eerst de centrale beheersite. Wanneer u al een primaire site en installeer een centrale beheersite wilt, moet u [de zelfstandige primaire site uitbreiden](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand) voor het installeren van de centrale beheersite.

-   De centrale beheersite ondersteunt alleen primaire sites als onderliggende sites.  

-   De centrale beheersite geen clients toegewezen krijgen.  

-   De centrale beheersite ondersteunt geen sitesysteemrollen die rechtstreeks ondersteuning van clients, zoals beheerpunten en distributiepunten.  

-   U kunt alle clients in de hiërarchie beheren en sitebeheertaken uitvoeren voor elke onderliggende site wanneer u een Configuration Manager-console die is verbonden met de centrale beheersite. Dit kunnen bijvoorbeeld beheerpunten of andere sitesysteemrollen op onderliggende primaire of secundaire sites installeren.  

-   Wanneer u een centrale beheersite gebruikt, is de centrale beheersite de enige plaats waar u sitegegevens van alle sites in uw hiërarchie kunt zien. Deze gegevens omvatten informatie zoals inventaris en statusberichten.  

-   U kunt detectiebewerkingen in de gehele hiërarchie uit de centrale beheersite door toe te wijzen detectiemethoden worden uitgevoerd op de afzonderlijke sites configureren.  

-   U kunt beveiliging beheren in de gehele hiërarchie door verschillende beveiligingsrollen, beveiligingsbereiken en verzamelen toe te wijzen aan verschillende beheerders. Deze configuraties van toepassing op elke site in de hiërarchie.  

-   U kunt bestandsreplicatie en databasereplicatie configureren om communicatie tussen sites in de hiërarchie te controleren. Dit omvat de planning van databasereplicatie voor sitegegevens en het beheer van de bandbreedte voor de overdracht van gegevens op basis van bestanden tussen sites.  

##  <a name="BKMK_ChoosePriimary"></a>Bepalen wanneer een primaire site worden gebruikt  
 Gebruik primaire sites om clients te beheren. U kunt een primaire site installeren als een onderliggende primaire site onder een centrale beheersite, of als de eerste site van een nieuwe hiërarchie. Een primaire site die is geïnstalleerd als de eerste site van een hiërarchie maakt een zelfstandige primaire site. Zowel onderliggende primaire sites als zelfstandige primaire sites ondersteunen secundaire sites als onderliggende sites van de primaire site.  

 Overweeg het gebruik van een primaire site om een van de volgende redenen:  

-   Voor het beheren van apparaten en gebruikers.  

-   U kunt voor een verhoging van het aantal apparaten beheren met een enkele hiërarchie.  

-   Bieden een aanvullend connectiviteitspunt voor het beheer van uw implementatie.  

-   Het voldoen aan de beheersvereisten van de organisatie. U kunt bijvoorbeeld een primaire site op een externe locatie voor het beheren van de overdracht van implementatie-inhoud via een netwerk met lage bandbreedte installeren. Echter, met System Center Configuration Manager kunt u opties voor het gebruik van netwerkbandbreedte beperken bij de overdracht van gegevens naar een distributiepunt. Deze beheerfunctionaliteit kan de noodzaak voor het installeren van extra sites vervangen.  


**De volgende informatie kunt u bepalen wanneer u een primaire site installeert:**  

-   Een primaire site is een zelfstandige primaire site of een onderliggende primaire site in een grotere hiërarchie. Wanneer een primaire site lid is van een hiërarchie met een centrale beheersite, gebruiken de sites databasereplicatie om gegevens tussen de sites te repliceren. Tenzij u moet meer clients te ondersteunen en de apparaten dan een enkele primaire site ondersteunen kan, kunnen u een zelfstandige primaire site installeren.  Nadat een zelfstandige primaire site is geïnstalleerd, kunt u deze rapporteert aan een nieuwe centrale beheersite om te schalen van uw implementatie kunt uitbreiden.  

-   Een primaire site ondersteunt alleen een centrale beheersite als een bovenliggende site.  

-   Een primaire site ondersteunt alleen secundaire sites als onderliggende sites, en kunt bieden ook ondersteuning voor meerdere secundaire onderliggende sites.  

-   Primaire sites zijn verantwoordelijk voor het verwerken van alle clientgegevens van hun toegewezen clients.  

-   Primaire sites gebruiken databasereplicatie om te communiceren rechtstreeks met hun centrale beheersite (die wordt automatisch geconfigureerd wanneer een nieuwe site wordt geïnstalleerd).  

##  <a name="BKMK_ChooseSecondary"></a>Bepalen wanneer een secundaire site gebruiken  
 Gebruik secundaire sites voor het beheren van de overdracht van implementatie-inhoud en clientgegevens over netwerken met een lage bandbreedte.  

 U kunt een secundaire site beheren vanuit een centrale beheersite of de secundaire site direct bovenliggende primaire site. Secundaire sites moeten zijn gekoppeld aan een primaire site en u ze niet verplaatsen naar een andere bovenliggende site zonder ze eerst te verwijderen en vervolgens opnieuw installeren als een onderliggende site onder nieuwe primaire site.

U kunt echter wel inhoud versturen tussen twee peer secundaire sites voor het beheer van de op bestanden gebaseerde replicatie van implementatie-inhoud. Om clientgegevens te zetten naar een primaire site, gebruikt de secundaire site bestandsgebaseerde replicatie. Een secundaire site gebruikt ook databasereplicatie om met de bovenliggende primaire site ervan te communiceren.  

 Overweeg de installatie van een secundaire site om een van de volgende redenen:  

-   U hebt geen een lokaal connectiviteitspunt nodig voor een gebruiker met beheerdersrechten.  

-   U moet de overdracht van implementatie-inhoud naar sites lager in de hiërarchie beheren.  

-   U moet clientinformatie beheren die naar sites hoger in de hiërarchie wordt verzonden.  

 Als u geen secundaire site wilt installeren en u clients op externe locaties hebt, overweeg dan het gebruik van Windows BranchCache of de installatie van distributiepunten die zijn ingeschakeld voor bandbreedteregeling en -planning. U kunt deze inhoudbeheeropties met of zonder secundaire sites gebruiken en kunt u Verminder het aantal sites en servers die moeten worden geïnstalleerd. Zie voor meer informatie over opties voor inhoudbeheer in Configuration Manager [bepalen wanneer gebruikt u opties voor inhoudbeheer](#BKMK_ChooseSecondaryorDP).  


**De volgende informatie kunt u bepalen wanneer u een secundaire site installeert:**  

-   Secundaire sites installeren automatisch SQL Server Express tijdens site-installatie als een lokaal exemplaar van SQL Server niet beschikbaar is.  

-   Secundaire site-installatie wordt gestart vanuit de Configuration Manager-console, in plaats van het installatieprogramma uitvoert op een computer rechtstreeks.  

-   Secundaire sites gebruiken een subset van de informatie in de sitedatabase, waardoor de hoeveelheid gegevens die door databasereplicatie tussen de bovenliggende primaire en secundaire site gerepliceerd.  

-   Secundaire sites ondersteunen het versturen van op bestanden gebaseerde inhoud naar andere secundaire sites die een gemeenschappelijke bovenliggende primaire site hebben.  

-   Installaties van secundaire sites implementeren automatisch een beheerpunt en distributiepunt dat zich op de secundaire siteserver bevinden.  

##  <a name="BKMK_ChooseSecondaryorDP"></a>Bepalen wanneer gebruikt u opties voor inhoudbeheer  
 Als u clients op externe netwerklocaties hebt, overweeg dan het gebruik van een of meerdere opties voor inhoudbeheer in plaats van een primaire of secundaire site. U kunt vaak de noodzaak voor het installeren van een site wanneer u Windows BranchCache gebruiken, distributiepunten voor bandbreedteregeling configureert of inhoud handmatig naar distributiepunten (voorbereide inhoud kopieert) verwijderen.  


**Overweeg het implementeren van een distributiepunt in plaats van installatie van een andere site als een van de volgende voorwaarden van toepassing:**  

-   Uw netwerkbandbreedte is voldoende om clientcomputers op de externe locatie te communiceren met een beheerpunt om te downloaden van clientbeleid en inventaris, rapporteringsstatus en detectie-informatie verzenden.  

-   Background Intelligent Transfer Service (BITS) biedt onvoldoende bandbreedteregeling voor uw netwerkvereisten.  

 Zie voor meer informatie over opties voor inhoudbeheer in Configuration Manager [basisconcepten voor inhoudsbeheer in System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

##  <a name="bkmk_beyond"></a>Afgezien van hiërarchietopologie  
 Naast de hiërarchietopologie van een initiële, overweeg welke services of mogelijkheden beschikbaar in verschillende sites zijn in de hiërarchie (sitesysteemrollen), en hoe hiërarchiebrede configuraties en -mogelijkheden in uw infrastructuur worden beheerd. De volgende algemene overwegingen worden in afzonderlijke onderwerpen besproken. Dit zijn belangrijk omdat ze invloed kunnen hebben op of worden beïnvloed door uw hiërarchie-ontwerp:  

-   Wanneer u zich voorbereiden op [beheren van computers en apparaten met System Center Configuration Manager](/sccm/core/clients/manage/manage-clients), overweeg of de apparaten die u beheert zich on-premises, in de cloud, of apparaten die eigendom zijn van gebruiker (BYOD) opnemen.  Houd ook rekening met hoe u apparaten beheert die worden ondersteund door meerdere beheeropties, zoals Windows 10-computers die beheerd kunnen worden rechtstreeks door Configuration Manager of door integratie met Microsoft Intune.  

-   Begrijpen hoe uw beschikbare netwerkinfrastructuur invloed kan zijn op de gegevensoverdracht tussen externe locaties (Zie [uw netwerkomgeving voorbereiden voor System Center Configuration Manager](/sccm/core/plan-design/network/configure-firewalls-ports-domains)). U kunt ook waar de gebruikers en apparaten die u beheert zich geografisch heeft bevonden en of ze toegang heeft tot uw infrastructuur via uw bedrijfsdomein of via Internet.  

-   Plan voor een infrastructuur voor inhoud om de informatie die u implementeert (bestanden en apps) efficiënt te distribueren naar apparaten die u beheert (Zie [inhoud en infrastructuur voor System Center Configuration Manager beheren](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)).  

-   Bepalen welke [functies en mogelijkheden van System Center Configuration Manager](../../../core/plan-design/changes/features-and-capabilities.md) u wilt gebruiken, de sitesysteemrollen of de Windows-infrastructuur ze nodig hebben en op welke sites in een hiërarchie met meerdere sites kunt u ze implementeren voor het meest efficiënt gebruik van uw netwerk- en serverbronnen.  

-   Denk na over de beveiliging van gegevens en apparaten, waaronder het gebruik van een PKI. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  


**Controleer de volgende bronnen voor sitespecifieke configuraties:**  

-   [Plannen voor de SMS-Provider voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)  

-   [Plan voor de sitedatabase voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-site-database.md)  

-   [Plan maken voor sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)  

-   [Beveiliging in System Center Configuration Manager plannen](../../../core/plan-design/security/plan-for-security.md)  

-   [Netwerkbandbreedte beheren](../../../core/plan-design/hierarchy/manage-network-bandwidth.md) wanneer u inhoud implementeer binnen een site  


**Houd rekening met configuraties die sites en hiërarchieën omvatten:**  

-   [Opties voor hoge beschikbaarheid voor System Center Configuration Manager](/sccm/protect/understand/high-availability-options) voor sites en hiërarchieën

-   [Het Active Directory-schema uitbreiden voor System Center Configuration Manager](../../../core/plan-design/network/extend-the-active-directory-schema.md) en sites configureren voor [sitegegevens voor System Center Configuration Manager publiceren](../../../core/servers/deploy/configure/publish-site-data.md)  

-   [Gegevensoverdracht tussen sites in System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md)  

-   [Basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md)
