---
title: Aan de slag met instellingen voor naleving | Microsoft-documenten
description: Informatie over hoe de instellingen voor naleving in System Center Configuration Manager werken. Ook meer te weten over de belangrijkste concepten die u nodig hebt.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2742d52-851e-4abc-b623-d12d91684c0b
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: f16c87dfd0c4f80d96aedf7f5f7497f2bbd4752a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="get-started-with-compliance-settings-in-system-center-configuration-manager"></a>Aan de slag met de instellingen voor naleving in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u begint met het System Center Configuration Manager-configuratie-items maken, moet u dit onderwerp om u te begrijpen hoe de instellingen voor naleving werken en voor meer informatie over de belangrijkste concepten, moet u weten lezen.  

## <a name="how-compliance-settings-works"></a>Hoe instellingen voor naleving werken  
 Instellingen voor naleving kunnen u de configuratie en compatibiliteit van servers, laptops, desktops en mobiele apparaten in uw organisatie beheren.  

 Configuratie-items kunnen worden onderverdeeld in twee hoofdcategorieën:  

-   **Instellingen voor apparaten die worden beheerd met de Configuration Manager-client** - doorgaans apparaten waarop u Configuration Manager-clientsoftware kunt u beheren van het apparaat hebt geïnstalleerd.  

-   **Instellingen voor apparaten die worden beheerd zonder dat de Configuration Manager-client** - doorgaans apparaten die worden beheerd met Microsoft Intune of met beheer van lokale apparaten Configuration Manager.  

## <a name="what-devices-are-supported"></a>Welke apparaten worden ondersteund?  


|Apparaattype|Meer informatie|  
|------------|----------------------|  
|Windows-pc's (met de Configuration Manager-client)|Hiermee kunt u aangepaste configuratie-items maken waarmee u items zoals registersleutels, bestanden en Active Directory-kenmerken kunt beoordelen.<br /><br /> Als u het Windows 10-configuratie-itemtype gebruikt, selecteert u de gewenste instellingen in een vooraf gedefinieerde lijst.|  
|Windows-pc (ingeschreven met Microsoft Intune)|Selecteer de gewenste instellingen in een vooraf gedefinieerde lijst.|  
|iOS-apparaten (ingeschreven met Microsoft Intune)|Selecteer de gewenste instellingen in een vooraf gedefinieerde lijst.|  
|Android-apparaten (ingeschreven met Microsoft Intune)|Selecteer de gewenste instellingen in een vooraf gedefinieerde lijst.|  
|Windows Phone-apparaten (ingeschreven met Microsoft Intune)|Selecteer de gewenste instellingen in een vooraf gedefinieerde lijst.|  
|Mac-computers (met de Configuration Manager-client)|Biedt u de mogelijkheid om aangepaste configuratie-items te maken waarmee u items kunt evalueren, zoals waarden voor Mac OS X-voorkeuren (eigenschappenlijst). De resultaten worden geretourneerd door een script.|  
|Mac-computers (ingeschreven met Microsoft Intune)|Selecteer de gewenste instellingen in een vooraf gedefinieerde lijst.|  

## <a name="what-is-a-configuration-item"></a>Wat is een configuratie-item?  
 Een configuratie-item kan worden gezien als een container waarin de volgende informatie wordt opgeslagen (welke informatie u configureert, is afhankelijk van het type configuratie-item):  

-   **Informatie over de detectiemethode** (voor Windows-configuratie-items die alleen toepassingsinstellingen bevatten): hiermee kunt u detecteren of een toepassing is geïnstalleerd door het Windows Installer-bestand voor de toepassing te detecteren of door een aangepast script te gebruiken.  

-   **Instellingen** : instellingen vertegenwoordigen de zakelijke of technische voorwaarden die worden gebruikt voor het evalueren van naleving op clientapparaten. U kunt een nieuwe instelling configureren of naar een bestaande instelling op een referentiecomputer bladeren.  

-   **Compliantieregels** : met compliantieregels geeft u de voorwaarden voor naleving van een instelling van een configuratie-item op. Voordat een instelling kan worden beoordeeld op naleving, moet de instelling minimaal één compliantieregel hebben. Voor bepaalde instellingen kunt u waarden herstellen die niet compatibel zijn. U kunt nieuwe regels maken of naar een bestaande instelling in een configuratie-item bladeren om regels hierin te selecteren.  

-   **Ondersteunde platforms** : dit zijn de apparaatplatforms die u definieert waarop het configuratie-item wordt geëvalueerd op compatibiliteit. Als u een configuratie-item voor een apparaat implementeert dat niet in de lijst met ondersteunde platforms staat, wordt de compatibiliteit van het item niet geëvalueerd.  

## <a name="what-is-a-configuration-baseline"></a>Wat is een configuratiebasislijn?  
 De compatibiliteit wordt geëvalueerd door een configuratiebasislijn te definiëren met daarin de configuratie-items die u wilt evalueren en de instellingen en de regels die het compatibiliteitsniveau beschrijven. U kunt deze configuratiegegevens importeren via het web in Microsoft System Center Configuration Manager configuratiepakketten als aanbevolen procedures die zijn gedefinieerd door Microsoft en andere leveranciers, in Configuration Manager en die u vervolgens importeert in Configuration Manager. U kunt ook nieuwe configuratie-items en configuratiebasislijnen maken.  

 Nadat de configuratiebasislijn is gedefinieerd, kunt u deze via verzamelingen implementeren voor gebruikers en apparaten en kunt u de instellingen voor de compatibiliteit evalueren volgens een planning. Er kunnen meerdere configuratiebasislijnen voor apparaten zijn geïmplementeerd. Dit biedt u een hoge mate van controle.  

 Clientapparaten evalueren hun compatibiliteit aan de hand van elke geïmplementeerde configuratiebasislijn en rapporteren de resultaten rechtstreeks naar de site met behulp van statusberichten. Als een clientapparaat momenteel geen verbinding met het netwerk heeft, maar de configuratie-items heeft gedownload waarnaar in een geïmplementeerde configuratiebasislijn wordt verwezen, wordt gecontroleerd of de configuratiebasislijn aan eisen voldoet. De compatibiliteitsinformatie wordt verzonden zodra de verbinding is hersteld.  

 U kunt controleren van de resultaten van de conformiteit van configuratiebasislijn evaluatie van de **implementaties** knooppunt in de **bewaking** werkruimte in de Configuration Manager-console om weer te geven van de meest voorkomende oorzaken van incompatibiliteit en fouten en het aantal gebruikers en apparaten die worden beïnvloed. U kunt ook rapporten voor nalevingsinstellingen uitvoeren om aanvullende details te zoeken, bijvoorbeeld welke apparaten wel en niet compatibel zijn en welke elementen van de configuratiebasislijn ervoor zorgen dat een computer niet-compatibel is. U kunt ook weergaveresultaten van evaluatie van naleving van Windows-computers waarop de Configuration Manager-clientsoftware wordt uitgevoerd met behulp van de **configuraties** tabblad **Configuration Manager** in het Configuratiescherm.  

## <a name="user-data-and-profiles-configuration-items"></a>Configuratie-items voor gebruikersgegevens en -profielen  
 Items voor gebruikersgegevens en profielen configuratie bevatten instellingen die bepalen hoe gebruikers in uw hiërarchie Mapomleiding, offlinebestanden en zwervende profielen op computers met Windows 8 en hoger beheren. U kunt deze implementeren naar verzamelingen van gebruikers en vervolgens hun naleving controleren via de **bewaking** knooppunt van de Configuration Manager-console. In tegenstelling tot andere configuratie-items, voegt u deze configuratiebasislijnen niet toe voordat u ze implementeert. U kunt ze rechtstreeks implementeren via het dialoogvenster **Configuratie-item voor gebruikersgegevens en -profielen implementeren** .  

 Zie voor meer informatie, [gebruikersgegevens en profielen configuratie-items maken](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

## <a name="remote-connection-profiles"></a>Profielen voor externe verbindingen  
 Met profielen voor externe verbindingen beschikt u over een verzameling hulpprogramma's en bronnen waarmee u instellingen voor externe verbindingen kunt maken, implementeren en bewaken voor apparaten in uw organisatie. Door deze instellingen te implementeren, maakt u het voor eindgebruikers gemakkelijker om met hun computers verbinding te maken met het bedrijfsnetwerk.  

Zie voor meer informatie, [maken van profielen voor externe verbindingen](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

## <a name="windows-edition-upgrade"></a>Upgrade van Windows-editie
Het beleid Edition Upgrade kunt u automatisch upgrade apparaten met bepaalde versies van Windows 10 naar een nieuwere versie door een nieuwe sleutel of licentie productbestand te verstrekken.

Zie voor meer informatie, [Upgrade van Windows-apparaten met de editie beleid bijwerken](/sccm/compliance/deploy-use/upgrade-windows-version)

