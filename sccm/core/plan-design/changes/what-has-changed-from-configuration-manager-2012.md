---
title: 'Wijzigingen van Configuration Manager 2012 | Microsoft Docs '
description: Identificeer de wijzigingen en nieuwe mogelijkheden in System Center Configuration Manager en System Center 2012 Configuration Manager.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3ae68fa6-8b30-45dd-9d12-50bb67cb4a9d
caps.latest.revision: "51"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 0a3eb93a99533a1569d8f72ca01d6dfcdc75da20
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="what39s-changed-in-system-center-configuration-manager-from-system-center-2012-configuration-manager"></a>Wat &#39; s gewijzigd in System Center Configuration Manager van System Center 2012 Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 De huidige vertakking van System Center Configuration Manager introduceert belangrijke wijzigingen van System Center 2012 Configuration Manager. Dit onderwerp vindt u belangrijke wijzigingen en nieuwe mogelijkheden in de basislijnversie 1511 van System Center Configuration Manager. Zie voor meer informatie over wijzigingen in de daaropvolgende updates voor System Center Configuration Manager, [wat is er nieuw in System Center Configuration Manager incrementele versies](/sccm/core/plan-design/changes/whats-new-incremental-versions).



 De December 2015-release van System Center Configuration Manager (versie 1511) is de initiële versie van het huidige product van de Configuration Manager van Microsoft. Dit wordt meestal aangeduid als de huidige vertakking van System Center Configuration Manager. *Huidige vertakking* geeft aan dat dit een versie die ondersteuning biedt voor incrementele updates voor het product. Het bevat ook een manier onderscheid maken tussen deze release en eerdere versies van Configuration Manager.  

 System Center Configuration Manager:  

-   Gebruikt een jaar of product-id niet in de naam van het product, in tegenstelling tot eerdere versies zoals Configuration Manager 2007 of System Center 2012 Configuration Manager.

-   Biedt ondersteuning voor incrementele, binnen het product updates, ook wel updateversies genoemd. De eerste release is versie 1511. Latere versies worden er verschillende keren een jaar als in de console-updates, zoals versie 1610 uitgebracht.
-   Wordt geïnstalleerd met een basislijnversie. Tijdens de oorspronkelijke basislijnversie 1511, nieuwe basislijnversies ook van tijd tot tijd vrijgegeven zoals 1702. Basislijnversies kunnen worden gebruikt om een nieuwe System Center Configuration Manager-site en hiërarchie te installeren of upgraden van een ondersteunde versie van Configuration Manager 2012.




##  <a name="bkmk_updates"></a> Updates binnen de console voor Configuration Manager  
 System Center Configuration Manager maakt gebruik van een in de console-servicemethode aangeroepen **Updates en onderhoud** waarmee u gemakkelijk om te zoeken en aanbevolen updates te installeren.  

 Sommige versies zijn alleen beschikbaar als updates voor bestaande sites (uit binnen de Configuration Manager-console) en kan niet worden gebruikt om nieuwe Configuration Manager-sites te installeren.   
Bijvoorbeeld: de update 1610 is alleen beschikbaar vanuit de Configuration Manager-console. Deze wordt gebruikt voor het bijwerken van een site waarop al een versie van System Center Configuration Manager.

Een updateversie wordt ook verschijnen als nieuwe basislijnversie (zoals update 1702). Dit soort update kan worden gebruikt voor het installeren van een nieuwe hiërarchie, zonder de noodzaak om te beginnen met een oudere basislijnversie (zoals 1511) en uw manier om de meest recente versie te upgraden.


Zie voor meer informatie over het gebruik van updates [Updates voor System Center Configuration Manager](../../../core/servers/manage/updates.md).  
Zie voor meer informatie over baslines [basislijn- en updateversies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions).

##  <a name="bkmk_servicepoint"></a>Nieuwe sitesysteemrol: serviceaansluitpunt  
 De **Microsoft Intune-connector** wordt vervangen door een nieuwe sitesysteemrol die aanvullende functionaliteit mogelijk maakt de **serviceaansluitpunt**. Het serviceverbindingspunt:  

-   Vervangt de Microsoft Intune-connector wanneer u Intune met System Center Configuration Manager-op-premises mobile device management integreert.  

-   Wordt gebruikt als een punt van de contactpersoon voor apparaten die u beheert.  

-   Gebruiksgegevens over uw implementatie naar de Microsoft cloud-service geüpload.  

-   Updates voor uw implementatie beschikbaar is vanuit de Configuration Manager-console maakt.  

Deze sitesysteemrol ondersteunt zowel online als offline bewerkingsmodi. Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md) voor meer informatie.  

##  <a name="bkmk_usage"></a> De verzameling van gebruiksgegevens  
 System Center Configuration Manager verzamelt gebruiksgegevens over uw sites en infrastructuur. Deze informatie is gecompileerd en verzonden naar de Microsoft cloud-service door het serviceverbindingspunt wordt gehost. Dit is vereist voor het inschakelen van Configuration Manager downloaden van updates voor uw implementatie die betrekking hebben op de versie van Configuration Manager u gebruikt. Bij het instellen van het serviceverbindingspunt wordt gehost, kunt u zowel op het niveau van de gegevens die worden verzameld en of deze automatisch worden verzonden (onlinemodus) of handmatig (offlinemodus).  

 Zie voor meer informatie [gebruiksgegevensniveaus en instellingen](../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

##  <a name="bkmk_AMT"></a> Ondersteuning voor Intel Active Management Technology (AMT)  
 Met System Center Configuration Manager systeemeigen ondersteuning voor AMT-gebaseerde computers uit binnen de Configuration Manager-console is verwijderd. AMT-gebaseerde computers blijven volledig beheerd wanneer u de [Intel SCS-invoegtoepassing voor Microsoft System Center Configuration Manager](http://www.intel.com/content/www/us/en/software/setup-configuration-software.html). De invoegtoepassing biedt dat u toegang tot de nieuwste mogelijkheden voor het beheer van AMT terwijl beperkingen die zijn geïntroduceerd totdat Configuration Manager deze wijzigingen kon opvangen worden weggenomen.  

Het verwijderen van geïntegreerde AMT voor System Center Configuration Manager bevat Out-of-Band-beheer. De sitesysteemrol buiten-Bandbeheer is niet langer gebruikt, en is ook beschikbaar.  

Houd er rekening mee Out-of-Band-beheer in System Center 2012 Configuration Manager wordt niet beïnvloed door deze wijziging.

##  <a name="bkmk_out"></a> Afgeschafte functies  
 Sommige mogelijkheden, zoals systeemeigen [ondersteuning voor Intel Active Management Technology (AMT)](#bkmk_AMT) op computers worden verwijderd uit de Configuration Manager-console. Andere mogelijkheden, zoals Network Access Protection worden volledig verwijderd. Bovendien worden sommige oudere Microsoft-producten, zoals Windows Vista, Windows Server 2008 en SQL Server 2008 niet meer ondersteund.  

 Zie voor een lijst met afgeschafte functies [verwijderd en afgeschafte functies voor System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 Zie voor meer informatie over ondersteunde producten, besturingssystemen en configuraties [ondersteunde configuraties voor System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md).  

## <a name="client-deployment"></a>Clientimplementatie  
 System Center Configuration Manager introduceert een nieuwe functie voor het testen van nieuwe versies van Configuration Manager-client vóór de upgrade van de rest van de site met de nieuwe software. U kunt instellen wanneer er een pre-productieverzameling waarin de testfase van een nieuwe client. Wanneer u tevreden met de nieuwe clientsoftware in een testomgeving bent, kunt u de client automatisch upgraden van de rest van de site met de nieuwe versie te promoveren.  

 Zie voor meer informatie over het testen van clients [clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

Let op de volgende wijzigingen aan de implementatie van besturingssysteem:

-   In de Wizard Takenreeks maken, **Upgrade van een besturingssysteem vanaf upgradepakket**, een nieuw takenreekstype beschikbaar is. De stappen voor het bijwerken van computers met Windows 7, Windows 8 of Windows 8.1 naar Windows 10 wordt gemaakt. Zie [Windows upgraden naar de nieuwste versie met System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md) voor meer informatie.  

-   Windows PE Peer Cache is nu beschikbaar wanneer u besturingssystemen implementeert. Computers met een takenreeks om een besturingssysteem te implementeren kunnen Windows PE-Peer-Cache gebruiken om inhoud te verkrijgen van een lokale peer (een peer-cachebron), in plaats van inhoud downloaden vanaf een distributiepunt. Dit helpt het Wide Area Network-verkeer (WAN) te beperken indien er sprake is van meerdere filialen terwijl er geen lokaal distributiepunt bestaat. Zie [Windows PE-Peer-Cache voorbereiden om WAN-verkeer te beperken in System Center Configuration Manager](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic) voor meer informatie.  

-   U kunt nu de status van Windows als een service in uw omgeving weergeven. U kunt ook maken onderhoudsplannen om implementatieringen te vormen en ervoor te zorgen dat de huidige vertakking computers Windows 10 worden bijgewerkt wanneer er nieuwe builds worden vrijgegeven. Bovendien kunt u waarschuwingen weergeven wanneer Windows 10-clients het einde van de ondersteuningsperiode voor hun build van Current Branch (CB) of Current Branch for Business (CBB) naderen. Zie [Windows als een service beheren met System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md) voor meer informatie.  

## <a name="application-management"></a>Toepassingsbeheer  

Let op de volgende wijzigingen aan toepassingsbeheer:

-   System Center Configuration Manager kunt u Universal Windows Platform (UWP) apps implementeren voor apparaten met Windows 10 en hoger. Zie [Windows-toepassingen maken met System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Software Center heeft een nieuwe, moderne vormgeving. Apps die alleen in de Toepassingscatalogus (voor gebruikers beschikbare apps) nu eerst worden weergegeven in Software Center op het tabblad toepassingen. Dit maakt deze implementaties beter kunnen worden gevonden en is het niet nodig zijn voor gebruikers om te verwijzen naar de Application Catalog. Bovendien is er geen browser met Silverlight meer vereist. Zie [Toepassingsbeheer plannen en configureren in System Center Configuration Manager ](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   Met het nieuwe toepassingstype Windows Installer via MDM kunt u Windows Installer-apps maken en implementeren op ingeschreven pc's met Windows 10. Zie [Windows-toepassingen maken met System Center Configuration Manager](../../../apps/get-started/creating-windows-applications.md).  

-   Wanneer u een toepassing voor een interne iOS-app maakt, moet u alleen het installatiebestand (.ipa) voor de app opgeven. U hoeft niet meer een bijbehorend eigenschappenlijstbestand (.plist) op te geven. Zie [iOS-toepassingen maken met System Center Configuration Manager](../../../apps/get-started/creating-ios-applications.md).  

-   In Configuration Manager 2012 om een koppeling naar een app in de Windows Store, kunt u ofwel de koppeling rechtstreeks opgeven, of blader naar een externe computer die de app geïnstalleerd was. In System Center Configuration Manager, u kunt nog steeds de koppeling rechtstreeks invoeren, maar in plaats van bladeren naar een referentiecomputer, kunt u nu de store naar de app rechtstreeks vanuit de Configuration Manager-console bladeren.  

## <a name="software-updates"></a>Software-updates  

Let op de volgende wijzigingen voor software-updates:

-   System Center Configuration Manager kan nu het verschil tussen het software-update-beheermethoden voor computers detecteren. In het bijzonder kan het onderscheid maken tussen een Windows 10-computer die verbinding maakt met Windows Update voor bedrijven (WUfB) voor het beheer van software-updates, en een computer die verbinding naar de Windows Server Update Services (WSUS) voor het beheer van software-updates. De **UseWUServer** kenmerk is er nieuw en Hiermee geeft u op of de computer wordt beheerd met WUfB. U kunt deze instelling in een verzameling gebruiken om deze computers uit het software-updatebeheer te verwijderen. Zie [Integratie met Windows Update voor bedrijven in Windows 10](../../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md) voor meer informatie.  

-   U kunt nu plannen en uitvoeren van de taak WSUS-opschoning van de Configuration Manager-console. In **onderdeel Software-updatepunt** eigenschappen, wanneer u selecteert voor de WSUS-opschoning-taak, deze wordt uitgevoerd op de volgende synchronisatie van software-updates. De verlopen software-updates zijn ingesteld op de status geweigerd op de WSUS-server en de Windows Update Agent op computers scant deze software-updates niet meer. Voor meer informatie, zie [De WSUS-opschoontaak plannen en uitvoeren](../../../sum/deploy-use/software-updates-maintenance.md).  

## <a name="compliance-settings"></a>Instellingen voor naleving  

Let op de volgende wijzigingen aan de instellingen voor naleving:

-   System Center Configuration Manager verbetert de werkstroom voor het maken van configuratie-items. Wanneer u nu een configuratie-item maakt en ondersteunde platformen selecteert, zijn alleen de instellingen die relevant zijn voor dat platform beschikbaar . Zie [Aan de slag met de instellingen voor naleving in System Center Configuration Manager](../../../compliance/get-started/get-started-with-compliance-settings.md).  

-   De **configuratie-Item maken** wizard nu gemakkelijker om te kiezen van het type voor configuratie-item dat u wilt maken. Daarnaast zijn er nieuwe en bijgewerkte configuratie-items beschikbaar voor:  

    -   Windows 10-apparaten die worden beheerd door Configuration Manager-client.  

    -   Mac OS X-apparaten met Configuration Manager-client worden beheerd.  

    -   Windows desktop- en servercomputers die worden beheerd door Configuration Manager-client.  

    -   Windows 8.1 en Windows 10-apparaten worden beheerd zonder de Configuration Manager-client.  

    -   Windows Phone-apparaten die worden beheerd zonder de Configuration Manager-client.  

    -   iOS en Mac OS X-apparaten die worden beheerd zonder Configuration Manager-client.  

    -   Android en Samsung KNOX Standard-apparaten die worden beheerd zonder Configuration Manager-client.  

 Zie [Configuratie-items maken in System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items.md).  

-   Ondersteuning voor het beheren van instellingen op Mac OS X-computers die ofwel met Microsoft Intune zijn ingeschreven of beheerd via de Configuration Manager-client. Zie [Configuratie-items maken voor iOS en Mac OS X-apparaten die worden beheerd zonder de System Center Configuration Manager-client](../../../compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md).  

## <a name="protect-data-and-site-infrastructure"></a>Gegevens en site-infrastructuur beveiligen  
System Center Configuration Manager kunt u de integratie met Windows Hello voor bedrijven (voorheen Microsoft Passport for Work). Windows Hello voor bedrijven is een alternatieve aanmeldingsmethode waarbij Active Directory of een Azure Active Directory-account worden gebruikt ter vervanging van een wachtwoord, smartcard of virtuele smartcard op apparaten met Windows 10. Zie [Instellingen voor Windows Hello voor Bedrijven in System Center Configuration Manager](../../../protect/deploy-use/windows-hello-for-business-settings.md).

## <a name="mobile-device-management-with-microsoft-intune"></a>Beheer van mobiele apparaten met Microsoft Intune  
 System Center Configuration Manager introduceert verbeteringen aan de beheerervaring van mobiele apparaten, met inbegrip van:  

-   Een limiet plaatsen op het aantal apparaten dat kan een gebruiker registreren.  

-   Geven voorwaarden en bepalingen gebruikers van de bedrijfsportal moet accepteren voordat ze kunnen registreren of de app gebruiken.  

-   Een apparaatinschrijvingsmanager om u te helpen bij het beheer van grote aantallen apparaten toevoegen.  

Zie voor meer informatie over de beheermogelijkheden voor mobiele apparaten met Configuration Manager en Intune [hybride mobile device management (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

## <a name="on-premises-mobile-device-management"></a>On-premises Mobile Device Management  
 U kunt nu mobiele apparaten beheren met behulp van on-premises Configuration Manager-infrastructuur. Alle Apparaatbeheer en beheergegevens is lokaal verwerkt en maakt geen deel uit van Microsoft Intune of andere cloudservices. Dit type Apparaatbeheer vereist geen clientsoftware. Configuration Manager beheert voor apparaten met de mogelijkheden die zijn ingebouwd in de besturingssystemen van apparaten.  

 Zie voor meer informatie, [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).
