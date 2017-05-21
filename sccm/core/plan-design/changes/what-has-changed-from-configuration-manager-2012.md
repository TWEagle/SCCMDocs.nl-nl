---
title: 'Van Configuration Manager 2012 gewijzigd | Microsoft-documenten '
description: Identificeer de wijzigingen en de nieuwe mogelijkheden in System Center Configuration Manager ten opzichte van System Center 2012 Configuration Manager.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3ae68fa6-8b30-45dd-9d12-50bb67cb4a9d
caps.latest.revision: 51
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 0a3eb93a99533a1569d8f72ca01d6dfcdc75da20
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="what39s-changed-in-system-center-configuration-manager-from-system-center-2012-configuration-manager"></a>Wat &#39; s is gewijzigd in System Center Configuration Manager van System Center 2012 Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 De huidige vertakking van System Center Configuration Manager introduceert belangrijke wijzigingen van System Center 2012 Configuration Manager. Dit onderwerp vindt u belangrijke wijzigingen en nieuwe functies van gevonden in de basisversie 1511 van System Center Configuration Manager. Zie voor meer informatie over wijzigingen die in de daaropvolgende updates voor System Center Configuration Manager, [wat is nieuw in System Center Configuration Manager incrementele versies](/sccm/core/plan-design/changes/whats-new-incremental-versions).



 De December 2015 release van System Center Configuration Manager (versie 1511) was het initiële versie van het huidige Configuration Manager-product van Microsoft. Dit is meestal System Center Configuration Manager huidige vertakking genoemd. *Huidige vertakking* geeft aan dat dit is een versie die ondersteuning biedt voor incrementele updates voor het product. Bovendien vindt u een manier onderscheid maken tussen deze versie en de vorige versies van Configuration Manager.  

 System Center Configuration Manager:  

-   Gebruikt een jaar of product-id niet in de naam van het product, anders dan bij vroegere versies zoals Configuration Manager 2007 of System Center 2012 Configuration Manager.

-   Biedt ondersteuning voor incrementele, in het product updates, ook wel genoemd updateversies. De eerste release is versie 1511. Latere versies worden meerdere keren per jaar als console updates, zoals versie 1610 uitgebracht.
-   Met een basislijn-versie wordt geïnstalleerd. Tijdens de oorspronkelijke versie van de basislijn 1511, nieuwe versies van de basislijn ook van tijd tot tijd verschijnen zoals 1702. Versies van de basislijn kunnen worden gebruikt om een nieuwe System Center Configuration Manager-site en hiërarchie te installeren of upgraden van een ondersteunde versie van Configuration Manager 2012.




##  <a name="bkmk_updates"></a> Updates binnen de console voor Configuration Manager  
 System Center Configuration Manager maakt gebruik van een in de console-servicemethode aangeroepen **Updates en onderhoud** waarmee u gemakkelijk te zoeken en installeren van aanbevolen updates.  

 In sommige versies zijn alleen beschikbaar als updates voor bestaande sites (uit in de Configuration Manager-console), en kan niet worden gebruikt om nieuwe Configuration Manager-sites te installeren.   
Bijvoorbeeld, is de update 1610 alleen beschikbaar vanuit de Configuration Manager-console. Het wordt gebruikt voor het bijwerken van een site waarop al een versie van System Center Configuration Manager.

Periodiek wordt ook een updateversie gepubliceerd als een nieuwe basislijn-versie (zoals update 1702). Dit soort update kan worden gebruikt voor het installeren van een nieuwe hiërarchie, zonder de noodzaak om te starten met een oudere versie van de basislijn (zoals 1511) en uw manier om de meest recente versie te upgraden.


Zie voor meer informatie over het gebruik van updates [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md).  
Zie voor meer informatie over baslines [basislijn en update versies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions).

##  <a name="bkmk_servicepoint"></a>Nieuwe sitesysteemrol: serviceverbindingspunt  
 De **Microsoft Intune-connector** wordt vervangen door een nieuwe sitesysteemrol waarmee aanvullende functionaliteit, het **serviceverbindingspunt**. Het serviceverbindingspunt:  

-   Vervangt de Microsoft Intune-connector wanneer u Intune met beheer van mobiele apparaten op het lokale System Center Configuration Manager integreert.  

-   Wordt gebruikt als een punt van de contactpersoon voor apparaten die u beheert.  

-   Gebruiksgegevens over uw implementatie geüpload naar de Microsoft-cloudservice.  

-   Updates voor uw implementatie vindt u in de Configuration Manager-console maakt.  

Deze sitesysteemrol ondersteunt online en offline modi. Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md) voor meer informatie.  

##  <a name="bkmk_usage"></a> De verzameling van gebruiksgegevens  
 System Center Configuration Manager verzamelt gebruiksgegevens over uw sites en -infrastructuur. Deze informatie is gecompileerd en verzonden naar de Microsoft cloudservice door de service connection point. Het is vereist om het inschakelen van Configuration Manager te downloaden van updates voor uw implementatie voor de versie van Configuration Manager, u gebruikt. Bij het instellen van de service connection point, kunt u zowel op het niveau van de gegevens die worden verzameld en of deze automatisch wordt ingediend (online modus) of handmatig (offlinemodus).  

 Zie voor meer informatie [gebruik hebben en instellingen](../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

##  <a name="bkmk_AMT"></a> Ondersteuning voor Intel Active Management Technology (AMT)  
 Met System Center Configuration Manager systeemeigen ondersteuning voor AMT-gebaseerde computers in de Configuration Manager-console is verwijderd. AMT-gebaseerde computers volledig beheerd blijven wanneer u de [Intel SCS-invoegtoepassing voor Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). De invoegtoepassing die u toegang biedt tot de nieuwste mogelijkheden voor het beheren van AMT, tijdens het verwijderen van beperkingen totdat Configuration Manager aanbrengen die wijzigingen kan is geïntroduceerd.  

Het verwijderen van geïntegreerde AMT voor System Center Configuration Manager omvat Out-of-Band beheer. De sitesysteemrol Out-of-Band-beheer is niet langer gebruikt en niet beschikbaar.  

Houd er rekening mee Out-of-Band Management in System Center 2012 Configuration Manager wordt niet beïnvloed door deze wijziging.

##  <a name="bkmk_out"></a> Afgeschafte functies  
 Sommige mogelijkheden, zoals systeemeigen [ondersteuning voor Intel Active Management Technology (AMT)](#bkmk_AMT) gebaseerde computers worden verwijderd uit de Configuration Manager-console. Andere mogelijkheden, zoals Network Access Protection zijn volledig verwijderd. Bovendien worden sommige oudere Microsoft-producten, zoals Windows Vista, Windows Server 2008 en SQL Server 2008 niet meer ondersteund.  

 Zie voor een lijst van afgeschaft functies [verwijderd en afgeschaft onderdelen voor System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 Zie voor meer informatie over ondersteunde producten, besturingssystemen en configuraties [ondersteunde configuraties voor System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md).  

## <a name="client-deployment"></a>Clientimplementatie  
 System Center Configuration Manager introduceert een nieuwe functie voor het testen van nieuwe versies van de Configuration Manager-client vóór de upgrade van de rest van de site met de nieuwe software. U kunt een pre-productieverzameling waarin proef uitvoeren van een nieuwe client instellen. Als u tevreden met de nieuwe clientsoftware in de testomgeving bent, bevordert u de client voor het automatisch bijwerken van de rest van de site met de nieuwe versie.  

 Zie voor meer informatie over het testen van clients [clientupgrades testen in een pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

Let op de volgende wijzigingen aan de implementatie van besturingssysteem:

-   In de Wizard Takenreeks maken, **Upgrade van een besturingssysteem vanaf upgradepakket**, een nieuwe takenreekstype beschikbaar is. De stappen voor de upgrade van computers van Windows 7, Windows 8 of Windows 8.1 en Windows 10 wordt gemaakt. Zie [Windows upgraden naar de nieuwste versie met System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md) voor meer informatie.  

-   Windows PE Peer Cache is nu beschikbaar wanneer u besturingssystemen implementeert. Computers waarop een takenreeks voor het implementeren van een besturingssysteem wordt uitgevoerd kunnen Windows PE-Peercache gebruiken om inhoud verkrijgen via een lokale peer (een peer-cachebron), in plaats van inhoud wordt gedownload van een distributiepunt. Dit helpt het Wide Area Network-verkeer (WAN) te beperken indien er sprake is van meerdere filialen terwijl er geen lokaal distributiepunt bestaat. Zie [Windows PE-Peer-Cache voorbereiden om WAN-verkeer te beperken in System Center Configuration Manager](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic) voor meer informatie.  

-   U kunt de status van Windows nu weergeven als een service in uw omgeving. U kunt ook onderhoud plannen om het formulier implementatie ringen maken en ervoor te zorgen dat Windows 10 huidige vertakking computers altijd zijn bijgewerkt wanneer er nieuwe builds zijn uitgebracht. Daarnaast kunt u waarschuwingen weergeven wanneer Windows 10 clients zich aan het einde van ondersteuning voor het samenstellen van huidige vertakking (CB) of de huidige vertakking voor Business (CBB). Zie [Windows als een service beheren met System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md) voor meer informatie.  

## <a name="application-management"></a>Toepassingsbeheer  

Let op de volgende wijzigingen met Toepassingsbeheer:

-   System Center Configuration Manager kunt u universele Windows-Platform (UWP) apps implementeren voor apparaten met Windows 10 en hoger. Zie [Windows-toepassingen maken met System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Software Center is een nieuwe, moderne vormgeving. Apps die eerder alleen in de Application Catalog (gebruiker beschikbare apps) nu werden weergegeven in Software Center op het tabblad toepassingen. Dit zorgt ervoor dat deze implementaties op te sporen en het niet nodig voor gebruikers om te verwijzen naar de Application Catalog. Bovendien is er geen browser met Silverlight meer vereist. Zie [Toepassingsbeheer plannen en configureren in System Center Configuration Manager ](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   Met het nieuwe toepassingstype Windows Installer via MDM kunt u Windows Installer-apps maken en implementeren op ingeschreven pc's met Windows 10. Zie [Windows-toepassingen maken met System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Wanneer u een toepassing voor een interne iOS-app maakt, hoeft u alleen het installatiebestand (.ipa) voor de app opgeeft. U hoeft niet meer een bijbehorend eigenschappenlijstbestand (.plist) op te geven. Zie [iOS-toepassingen maken met System Center Configuration Manager](../../../apps/get-started/creating-ios-applications.md).  

-   In Configuration Manager 2012 om op te geven van een koppeling naar een app in de Windows Store kan u de koppeling rechtstreeks opgeven, of blader naar een externe computer waarop de app is geïnstalleerd. In System Center Configuration Manager, u kunt de koppeling nog steeds rechtstreeks invoert, maar in plaats van bladeren naar een referentiecomputer, kunt u nu de store naar de app rechtstreeks vanuit de Configuration Manager-console bladeren.  

## <a name="software-updates"></a>Software-updates  

Let op de volgende wijzigingen voor software-updates:

-   System Center Configuration Manager kan nu het verschil tussen beheermethoden voor software-update voor computers detecteren. Specifiek, kan het onderscheid maken tussen een Windows-10-computer die verbinding maakt met Windows Update voor bedrijven (WUfB) voor software-updatebeheer en een computer die is verbonden aan de Windows Server Update Services (WSUS) voor software-updatebeheer. De **UseWUServer** kenmerk is er nieuw en geeft aan of de computer wordt beheerd met WUfB. U kunt deze instelling in een verzameling gebruiken om deze computers uit het software-updatebeheer te verwijderen. Zie [Integratie met Windows Update voor bedrijven in Windows 10](../../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md) voor meer informatie.  

-   U kunt nu plannen en uitvoeren van de taak WSUS opschonen van de Configuration Manager-console. In **onderdeel Software-updatepunt** eigenschappen, wanneer u selecteert voor de taak WSUS opschonen deze wordt uitgevoerd op de volgende synchronisatie van software-updates. De verlopen software-updates zijn ingesteld op status geweigerd op de WSUS-server en de Windows Update Agent op computers scant niet meer deze software-updates. Voor meer informatie, zie [De WSUS-opschoontaak plannen en uitvoeren](../../../sum/deploy-use/software-updates-maintenance.md).  

## <a name="compliance-settings"></a>Instellingen voor naleving  

Let op de volgende wijzigingen aan de instellingen voor naleving:

-   System Center Configuration Manager verbetert de werkstroom voor het maken van configuratie-items. Wanneer u nu een configuratie-item maakt en ondersteunde platformen selecteert, zijn alleen de instellingen die relevant zijn voor dat platform beschikbaar . Zie [Aan de slag met de instellingen voor naleving in System Center Configuration Manager](../../../compliance/get-started/get-started-with-compliance-settings.md).  

-   De **configuratie-Item maken** wizard nu vereenvoudigt, kiest u de configuratie-item dat u wilt maken. Daarnaast zijn er nieuwe en bijgewerkte configuratie-items beschikbaar voor:  

    -   Windows 10-apparaten die worden beheerd door de Configuration Manager-client.  

    -   Mac OS X-apparaten die worden beheerd door de Configuration Manager-client.  

    -   Windows desktop- en server-computers die worden beheerd door de Configuration Manager-client.  

    -   Windows 8.1 en Windows 10-apparaten worden beheerd zonder dat de Configuration Manager-client.  

    -   Windows Phone-apparaten te beheren zonder dat de Configuration Manager-client.  

    -   iOS- en Mac OS X-apparaten beheerd zonder dat de Configuration Manager-client.  

    -   Android en Samsung KNOX Standard apparaten te beheren zonder dat de Configuration Manager-client.  

 Zie [Configuratie-items maken in System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items.md).  

-   Ondersteuning voor het beheren van instellingen op de Mac OS X-computers die te maken met Microsoft Intune zijn ingeschreven of beheerd via de Configuration Manager-client. Zie [Configuratie-items maken voor iOS en Mac OS X-apparaten die worden beheerd zonder de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md).  

## <a name="protect-data-and-site-infrastructure"></a>Gegevens en site-infrastructuur beveiligen  
System Center Configuration Manager kunt u integratie met Windows Hello voor bedrijven (voorheen Microsoft Passport for Work). Windows Hello voor bedrijven is een alternatieve-toegestane aanmeldingsmethode die gebruikmaakt van Active Directory of een Azure Active Directory-account, een wachtwoord, smartcard of virtuele smartcard op apparaten met Windows 10 vervangen. Zie [Instellingen voor Windows Hello voor Bedrijven in System Center Configuration Manager](../../../protect/deploy-use/windows-hello-for-business-settings.md).

## <a name="mobile-device-management-with-microsoft-intune"></a>Beheer van mobiele apparaten met Microsoft Intune  
 System Center Configuration Manager introduceert verbeteringen voor het beheer van mobiele apparaten, waaronder:  

-   Een limiet van het aantal apparaten dat kan een gebruiker inschrijven.  

-   Voorwaarden en bepalingen gebruikers van de bedrijfsportal opgeven accepteren voordat ze kunnen inschrijven of de app gebruiken.  

-   Toevoegen van een apparaat inschrijving manager om te helpen bij het beheren van grote aantallen apparaten.  

Zie voor meer informatie over beheermogelijkheden voor mobiele apparaten met Configuration Manager en Intune [hybride mobiel Apparaatbeheer (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

## <a name="on-premises-mobile-device-management"></a>On-premises Mobile Device Management  
 U kunt nu mobiele apparaten beheren met behulp van de lokale Configuration Manager-infrastructuur. Alle beheer van apparaten en beheergegevens verwerkte on-premises en maakt geen deel uit van Microsoft Intune of andere cloudservices. Dit type Apparaatbeheer vereisen geen clientsoftware. Configuration Manager beheert voor apparaten met de mogelijkheden die zijn ingebouwd in de besturingssystemen van apparaten.  

 Zie voor meer informatie, [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).

