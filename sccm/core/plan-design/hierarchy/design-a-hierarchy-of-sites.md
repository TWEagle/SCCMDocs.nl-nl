---
title: "Ontwerp een sitehiërarchie - Configuration Manager | Microsoft-documenten"
description: "De beschikbare topologieën en beheeropties voor System Center Configuration Manager begrijpen zodat u uw sitehiërarchie kunt plannen."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 07ce872e-1558-42ad-b5ad-582c5b1bdbb4
caps.latest.revision: 22
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 35e48666f4d1a2363304650f960531fd0630a291
ms.openlocfilehash: e346e83b0ae0dc7a612cef7a7b9fb1fdb42236bc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="design-a-hierarchy-of-sites-for-system-center-configuration-manager"></a>Een sitehiërarchie ontwerpen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u de eerste site van een nieuwe System Center Configuration Manager-hiërarchie installeert, is het een goed idee om te begrijpen van de beschikbare topologieën voor Configuration Manager, de typen beschikbare sites en hun relaties met andere en het bereik van beheer van elk sitetype.
Vervolgens, nadat u overweegt opties voor inhoudbeheer die kunnen Verminder het aantal sites die u wilt installeren, u een topologie dat uw huidige bedrijfsbehoeften efficiënt kunt plannen en later kunt uitbreiden voor het beheren van toekomstige groei.  

> [!NOTE]
> Als u een nieuwe installatie van Configuration Manager, worden op de hoogte van de [releaseopmerkingen]( /sccm/core/servers/deploy/install/release-notes), die actuele problemen in de actieve versies beschreven. De releaseopmerkingen gelden voor alle vertakkingen van Configuration Manager.  Wanneer u echter gebruiken de [technische Preview vertakking]( /sccm/core/get-started/technical-preview), zult u problemen met specifieke alleen aan dat filiaal in de documentatie voor elke versie van de Technical Preview.  

##  <a name="bkmk_topology"></a>Hiërarchie-topologie  
 Hiërarchie topologieën variëren van een enkele zelfstandige primaire site met een groep verbonden primaire en secundaire sites met een centrale beheersite op het hoogste siteniveau (hoogste niveau) van de hiërarchie.   Het belangrijkste stuurprogramma van het type en aantal sites die u in een hiërarchie gebruikt is gewoonlijk het aantal en type van apparaten die u, als volgt ondersteunen moet:   

 **Zelfstandige primaire site:** Gebruik van een zelfstandige primaire site als een enkele primaire site beheer van al uw apparaten en gebruikers ondersteunen kan (Zie [grootte en schaal getallen](/sccm/core/plan-design/configs/size-and-scale-numbers)). Voor deze topologie is mislukt bij verschillende geografische locaties van uw bedrijf met succes kunnen worden geleverd door een enkele primaire site.  Om te helpen het netwerkverkeer beheren, kunt u voorkeursbeheerpunten en een zorgvuldig geplande inhoud infrastructuur (Zie [fundamentele concepten voor content management in System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)).  

 Voordelen van deze topologie zijn onder andere:  

-   Vereenvoudigde administratieve overhead.  

-   Vereenvoudigd sitetoewijzing van clients en de detectie van de beschikbare bronnen en services.  

-   Eliminatie van mogelijke vertraging die geïntroduceerd door databasereplicatie tussen sites.

-   Optie voor het uitbreiden van een zelfstandige primaire hiërarchie naar een grotere hiërarchie met een centrale beheersite. Hiermee kunt u nieuwe primaire sites installeren om de schaal van uw implementatie te vergroten.  


**Centrale beheersite met een of meer onderliggende primaire sites:** Gebruik voor deze topologie wanneer u meer dan één primaire site voor de ondersteuning van beheer van uw apparaten en gebruikers vereisen.  Wanneer u meer dan een enkele primaire site is vereist. Voordelen van deze topologie zijn onder andere:  


-   Het ondersteunt maximaal 25 primaire sites die u uit te breiden de schaal van uw hiërarchie.  

-   U altijd de centrale beheersite gebruikt (tenzij u uw sites herinstalleert). Dit is een permanente optie. U kunt een onderliggende primaire site zodat dit een zelfstandige primaire site kan niet loskoppelen.

 In de volgende secties leest u wanneer u een specifieke site- of inhoudbeheeroptie in plaats van een extra site gebruikt.  

##  <a name="BKMK_ChooseCAS"></a>Bepalen wanneer een site voor Centraal beheer gebruiken  
 Gebruik een centrale beheersite binnen de gehele hiërarchie-instellingen te configureren en voor het bewaken van alle sites en objecten in de hiërarchie. Dit sitetype beheert clients niet rechtstreeks, maar het coördineert gegevensreplicatie tussen sites, hetgeen de configuratie van sites en clients in de gehele hiërarchie omvat.  

**De volgende informatie kunt u bepalen wanneer u een centrale beheersite installeren:**  

-   De centrale beheersite is de site op het hoogste niveau in een hiërarchie.  

-   Wanneer u een hiërarchie configureert die meer dan één primaire site heeft, moet u een centrale beheersite installeren en deze moet de eerste site die u installeert.  

-   De centrale beheersite ondersteunt enkel primaire sites als onderliggende sites.  

-   De centrale beheersite geen clients toegewezen krijgen.  

-   De centrale beheersite ondersteunt geen sitesysteemrollen die rechtstreeks ondersteuning bieden voor clients, zoals beheerpunten en distributiepunten.  

-   U kunt alle clients in de hiërarchie beheren en sitebeheertaken uitvoeren voor eender welke onderliggende site wanneer u een Configuration Manager-console die is verbonden met de centrale beheersite. Dit kan ook beheerpunten of andere sitesysteemrollen op onderliggende primaire of secundaire sites installeren.  

-   Wanneer u een centrale beheersite gebruikt, is de centrale beheersite de enige plaats waar u sitegegevens van alle sites in uw hiërarchie kunt zien. Deze gegevens omvatten informatie zoals inventarisgegevens en statusberichten.  

-   U kunt detectiebewerkingen in de gehele hiërarchie vanuit de centrale beheersite door detectiemethodes om uit te voeren op individuele sites te configureren.  

-   U kunt beveiliging beheren in de gehele hiërarchie door verschillende beveiligingsrollen, beveiligingsbereiken en verzamelen toe te wijzen aan verschillende beheerders. Deze configuraties van toepassing op elke site in de hiërarchie.  

-   U kunt bestandsreplicatie en databasereplicatie configureren om communicatie tussen sites in de hiërarchie te controleren. Dit omvat de planning van databasereplicatie voor sitegegevens en het beheer van de bandbreedte voor de overdracht van gegevens op basis van bestanden tussen sites.  

##  <a name="BKMK_ChoosePriimary"></a>Bepalen wanneer een primaire site worden gebruikt  
 Gebruik primaire sites om clients te beheren. U kunt een primaire site installeren als een onderliggende primaire site onder een centrale beheersite, of als de eerste site van een nieuwe hiërarchie. Een primaire site die is geïnstalleerd als de eerste site van een hiërarchie maakt een zelfstandige primaire site. Zowel onderliggende primaire sites als zelfstandige primaire sites ondersteunen secundaire sites als onderliggende sites van de primaire site.  

 Overweeg het gebruik van een primaire site om een van de volgende redenen:  

-   Voor het beheren van apparaten en gebruikers.  

-   Het aantal apparaten dat u met een enkele hiërarchie beheren kunt verhogen.  

-   Een extra contactpunt connectiviteit bieden voor het beheer van uw implementatie.  

-   Het voldoen aan de beheersvereisten van de organisatie. U kunt bijvoorbeeld een primaire site op een externe locatie voor het beheren van de overdracht van implementatie-inhoud via een netwerk met lage bandbreedte installeren. Echter met System Center Configuration Manager kunt u opties voor het gebruik van netwerkbandbreedte beperken bij de overdracht van gegevens naar een distributiepunt. Die mogelijkheid inhoudsbeheer kan de noodzaak voor het installeren van extra sites vervangen.  


**De volgende informatie kunt u bepalen wanneer een primaire site wilt installeren:**  

-   Een primaire site kan een zelfstandige primaire site of een onderliggende primaire site in een grotere hiërarchie zijn. Wanneer een primaire site lid is van een hiërarchie met een centrale beheersite, gebruiken de sites databasereplicatie om gegevens tussen de sites te repliceren. Tenzij u meer clients te ondersteunen en moet apparaten dan een enkele primaire site ondersteunen kan, kunnen u een zelfstandige primaire site installeren.  Nadat u een zelfstandige primaire site is geïnstalleerd, kunt u deze om te rapporteren aan een nieuwe centrale beheersite scale-up van uw implementatie kunt uitbreiden.  

-   Een primaire site ondersteunt enkel een centrale beheersite als een bovenliggende site.  

-   Een primaire site ondersteunt enkel secundaire sites als onderliggende sites, en kunt ook ondersteuning voor meerdere secundaire onderliggende sites.  

-   Primaire sites zijn verantwoordelijk voor de verwerking van alle clientsgegevens van hun toegewezen clients.  

-   Primaire sites gebruiken databasereplicatie om te communiceren rechtstreeks met hun centrale beheersite (die wordt automatisch geconfigureerd als een nieuwe site is geïnstalleerd).  

##  <a name="BKMK_ChooseSecondary"></a>Bepalen wanneer een secundaire site te gebruiken  
 Gebruik secundaire sites voor het beheren van de overdracht van implementatie-inhoud en clientgegevens over netwerken met een lage bandbreedte.  

 U beheren een secundaire site vanuit een centrale beheersite of de secundaire site direct bovenliggende primaire site. Secundaire sites moeten gekoppeld zijn aan een primaire site en u niet te verplaatsen naar een andere bovenliggende site zonder ze eerst te verwijderen en vervolgens opnieuw installeren als een onderliggende site onder nieuwe primaire site.

U kunt echter inhoud versturen tussen twee peer secundaire site voor het beheer van de op bestanden gebaseerde replicatie van implementatie-inhoud. Om clientgegevens te brengen met een primaire site, gebruikt de secundaire site bestandsgebaseerde replicatie. Een secundaire site gebruikt ook databasereplicatie om met de bovenliggende primaire site ervan te communiceren.  

 Overweeg de installatie van een secundaire site om een van de volgende redenen:  

-   U hebt een lokaal contactpunt van de verbinding niet voor een gebruiker met beheerdersrechten nodig.  

-   U moet de overdracht van implementatie-inhoud naar sites lager in de hiërarchie beheren.  

-   U moet clientinformatie beheren die naar sites hoger in de hiërarchie wordt verzonden.  

 Als u geen secundaire site wilt installeren en u clients op externe locaties hebt, overweeg dan het gebruik van Windows BranchCache of de installatie van distributiepunten die zijn ingeschakeld voor bandbreedteregeling en -planning. U kunt deze inhoudbeheeropties met of zonder secundaire sites, en ze kunnen u helpen te Verminder het aantal sites en servers die moeten worden geïnstalleerd. Zie voor meer informatie over opties voor inhoudbeheer in Configuration Manager [bepalen wanneer te gebruiken opties voor inhoudbeheer](#BKMK_ChooseSecondaryorDP).  


**De volgende informatie kunt u bepalen wanneer een secundaire site te installeren:**  

-   Secundaire sites installeren automatisch SQL Server Express tijdens site-installatie als een lokaal exemplaar van SQL Server niet beschikbaar is.  

-   Installatie van secundaire site wordt gestart vanaf de Configuration Manager-console in plaats van het installatieprogramma uitvoert op een computer rechtstreeks.  

-   Secundaire sites gebruiken een subset van de informatie in de sitedatabase, waardoor de hoeveelheid gegevens die zijn gerepliceerd door databasereplicatie tussen de bovenliggende primaire en secundaire site.  

-   Secundaire sites ondersteunen het versturen van op bestanden gebaseerde inhoud naar andere secundaire sites die een gemeenschappelijke bovenliggende primaire site hebben.  

-   Installaties van secundaire sites implementeren automatisch een beheerpunt en distributiepunt dat zich op de secundaire siteserver.  

##  <a name="BKMK_ChooseSecondaryorDP"></a>Bepalen wanneer te gebruiken opties voor inhoudbeheer  
 Als u clients op externe netwerklocaties hebt, overweeg dan het gebruik van een of meerdere opties voor inhoudbeheer in plaats van een primaire of secundaire site. Vaak kunt u de noodzaak voor het installeren van een site wanneer u gebruikmaakt van Windows BranchCache, distributiepunten voor bandbreedteregeling configureert, of inhoud handmatig naar distributiepunten (voorbereide inhoud kopieert).  


**Overweeg de implementatie van een distributiepunt in plaats van de installatie van een andere site als een van de volgende voorwaarden is voldaan:**  

-   Uw netwerkbandbreedte is voldoende om clientcomputers op de externe locatie te communiceren met een beheerpunt om te downloaden van clientbeleid en inventaris, rapporteringsstatus en detectie-informatie verzenden.  

-   Background Intelligent Transfer Service (BITS) biedt onvoldoende bandbreedteregeling voor uw netwerkvereisten.  

 Zie voor meer informatie over opties voor inhoudbeheer in Configuration Manager [fundamentele concepten voor content management in System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

##  <a name="bkmk_beyond"></a>Boven hiërarchie-topologie  
 Naast de topologie van een eerste hiërarchie bedenken welke services of mogelijkheden beschikbaar van andere sites in de hiërarchie (sitesysteemrollen), en hoe gehele hiërarchie configuraties en mogelijkheden in uw infrastructuur worden beheerd. De volgende algemene overwegingen bij de worden in de afzonderlijke onderwerpen besproken. Dit zijn belangrijk omdat ze beïnvloeden kunnen of worden beïnvloed door uw hiërarchie-ontwerp:  

-   Wanneer u zich voorbereiden op [beheren van computers en apparaten met System Center Configuration Manager](/sccm/core/clients/manage/manage-clients), overweeg dan of de apparaten die u beheert lokaal, in de cloud, of een gebruiker eigenaar apparaten (BYOD).  Houd ook rekening met hoe u apparaten die worden ondersteund door meerdere beheeropties, zoals Windows 10-computers die kunnen worden beheerd rechtstreeks door Configuration Manager beheert en Hoewel integratie met Microsoft Intune.  

-   Begrijpen hoe uw beschikbare netwerkinfrastructuur de gegevensoverdracht tussen externe locaties kan beïnvloeden (Zie [uw netwerkomgeving voorbereiden voor System Center Configuration Manager](/sccm/core/plan-design/network/configure-firewalls-ports-domains)). Overweeg daarnaast waar de gebruikers en apparaten die u wilt beheren zich geografisch bevinden en of ze toegang heeft tot uw infrastructuur via uw bedrijfsdomein of Internet.  

-   Plan voor een inhoud-infrastructuur om de informatie die u implementeert (bestanden en apps) efficiënt te distribueren naar apparaten die u beheert (Zie [inhoud en -infrastructuur voor System Center Configuration Manager beheert](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)).  

-   Bepalen welke [functies en mogelijkheden van System Center Configuration Manager](../../../core/plan-design/changes/features-and-capabilities.md) u wilt gebruiken, de sitesysteemrollen of de Windows-infrastructuur ze nodig hebben en op welke sites in een hiërarchie met meerdere sites kunt u ze implementeren voor het meest efficiënt gebruik van uw netwerk- en -bronnen.  

-   Denk na over de beveiliging van gegevens en apparaten, waaronder het gebruik van een PKI. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  


**Controleer de volgende bronnen voor sitespecifieke configuraties:**  

-   [Plannen voor de SMS-Provider voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)  

-   [Plan voor de sitedatabase voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-site-database.md)  

-   [Plannen voor de sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)  

-   [Plannen van beveiliging in System Center Configuration Manager](../../../core/plan-design/security/plan-for-security.md)  

-   [Netwerkbandbreedte beheren](../../../core/plan-design/hierarchy/manage-network-bandwidth.md) wanneer u inhoud implementeer binnen een site  


**Overweeg die sites en hiërarchieën omvatten:**  

-   [Opties voor hoge beschikbaarheid voor System Center Configuration Manager](/sccm/protect/understand/high-availability-options) voor sites en hiërarchieën

-   [Het Active Directory-schema uitbreidt voor System Center Configuration Manager](../../../core/plan-design/network/extend-the-active-directory-schema.md) en sites te configureren [sitegegevens publiceren voor System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md)  

-   [De gegevensoverdracht tussen sites in System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md)  

-   [De grondbeginselen van op rollen gebaseerd beheer voor System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md)

