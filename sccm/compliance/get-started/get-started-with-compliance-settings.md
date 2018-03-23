---
title: Aan de slag met instellingen voor naleving
titleSuffix: Configuration Manager
description: Meer informatie over de belangrijkste concepten en hoe instellingen voor naleving werken
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2742d52-851e-4abc-b623-d12d91684c0b
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a8f672d4d92db8f1bd6e19c4a483b5b3107ad703
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="get-started-with-compliance-settings-in-system-center-configuration-manager"></a>Aan de slag met de instellingen voor naleving in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u instellingen voor naleving van Configuration Manager maakt, eerst meer informatie over de belangrijkste concepten en begrijpen hoe deze werken.  



## <a name="how-compliance-settings-work"></a>Hoe instellingen voor naleving werken  
 Instellingen voor naleving kunnen u de configuratie en naleving van clients in uw organisatie beheren.  

 Configuratie-items kunnen worden onderverdeeld in twee hoofdcategorieën:  

-   **Instellingen voor apparaten die worden beheerd met Configuration Manager-client** - doorgaans apparaten waarop u Configuration Manager-clientsoftware kunt u het apparaat te beheren hebt geïnstalleerd.  

-   **Instellingen voor apparaten die worden beheerd zonder Configuration Manager-client** - meestal apparaten die worden beheerd met Microsoft Intune of met Apparaatbeheer voor lokale Configuration Manager.  



## <a name="what-devices-are-supported"></a>Welke apparaten worden ondersteund?  

| Apparaattype | Meer informatie |  
|------------|----------------------|  
| Windows-pc's (met de Configuration Manager-client) | Aangepaste configuratie-items voor het evalueren van objecten, zoals registersleutels, bestanden en Active Directory-kenmerken maken.<br /><br /> Wanneer u de Windows 10-configuratie-itemtype gebruikt, selecteert u de instellingen van een vooraf gedefinieerde lijst. |  
| Windows-pc's (geregistreerd bij Microsoft Intune) | Selecteer de instellingen van een vooraf gedefinieerde lijst. |  
| iOS-apparaten (geregistreerd bij Microsoft Intune) | Selecteer de instellingen van een vooraf gedefinieerde lijst. |  
| Android-apparaten (geregistreerd bij Microsoft Intune) | Selecteer de instellingen van een vooraf gedefinieerde lijst. |  
| Windows Phone-apparaten (geregistreerd bij Microsoft Intune) | Selecteer de instellingen van een vooraf gedefinieerde lijst. |  
| Mac-computers (met de Configuration Manager-client) | Aangepaste configuratie-items voor het evalueren van objecten, zoals Mac OS-voorkeuren en resultaten geretourneerd door een script maken. |  
| Mac-computers (ingeschreven bij Microsoft Intune) | Selecteer de instellingen van een vooraf gedefinieerde lijst. |  



## <a name="what-is-a-configuration-item"></a>Wat is een configuratie-item?  
 Een configuratie-item is een container waarin specifieke informatie wordt opgeslagen. De informatie die u configureert, is afhankelijk van het configuratietype-item. Configuratie-items kunnen de volgende informatie bevatten:

-   **Informatie over de detectiemethode** is alleen voor Windows-configuratie-items die toepassingsinstellingen bevatten. Er wordt gedetecteerd of een toepassing is geïnstalleerd. Deze detectie maakt gebruik van het Windows installer-bestand voor de toepassing of met behulp van een aangepast script.  

-   **Instellingen** vertegenwoordigen de zakelijke of technische voorwaarden om te evalueren van Compliantie op clientapparaten. Een nieuwe instelling configureren of blader naar een bestaande instelling op een referentiecomputer.  

-   **Compliantieregels** de voorwaarden opgeven waaraan de naleving van een configuratie-item-instelling definiëren. Voordat de client een instelling voor naleving evalueert, moet ten minste één compliantieregel hebben. Sommige instellingen herstellen niet-compatibele waarden. Nieuwe regels maken of blader naar een bestaande instelling in een configuratie-item en selecteer regels in het.  

-   **Ondersteunde platforms** zijn de apparaatplatforms die u definieert waarop de client evalueert de naleving van de configuratie-items. Als u een configuratie-item op een apparaat dat zich niet in de lijst met ondersteunde platformen implementeert, beoordeelt naleving niet meer.  



## <a name="what-is-a-configuration-baseline"></a>Wat is een configuratiebasislijn?  
 Definieer een configuratiebasislijn met de configuratie-items om te evalueren. Ook de instellingen en regels die het vereiste niveau van compatibiliteit beschrijven. Deze configuratiegegevens uit Configuration Manager-configuratiepakketten importeren. Definieer deze configuratiepakketten Microsoft en andere leveranciers. Nieuwe configuratie-items en configuratiebasislijnen of maken.  

 Nadat u een configuratiebasislijn hebt gedefinieerd, kunt u dit aan gebruiker en apparaatverzamelingen implementeren. De client evalueert vervolgens de basislijninstellingen voor naleving volgens een schema. U kunt meer dan een configuratiebasislijn implementeren op apparaten. Deze granulatie biedt meer controle over de naleving. 

 Clientapparaten evalueren hun compatibiliteit aan de hand van elke geïmplementeerde configuratiebasislijn en rapporteren de resultaten rechtstreeks naar de site met behulp van statusberichten. Als een apparaat is momenteel losgekoppeld van het netwerk, maar de configuratiebasislijn wordt gedownload, evalueert deze nog steeds op compatibiliteit van de configuratie-items. De compatibiliteitsinformatie stuurt wanneer verbinding wordt gemaakt.  

### <a name="monitoring-configuration-baselines"></a>Bewaking van configuratiebasislijnen
- Controleren van de resultaten van de evaluatie van de naleving in Configuration Manager-console onder het **bewaking** werkruimte, in de **implementaties** knooppunt. Bijvoorbeeld:
    - Veelvoorkomende oorzaken van incompatibiliteit
    - Errors
    - Het aantal betrokken gebruikers en apparaten
- Voer rapporten met instellingen voor naleving met aanvullende informatie. Bijvoorbeeld:
    - Welke apparaten zijn compatibel of niet-compatibele
    - Welke elementen van de configuratiebasislijn wordt veroorzaakt door een computer wordt niet-compatibele
- Bekijken van resultaten van evaluatie van Compliantie op Windows-computers waarop de Configuration Manager-client wordt uitgevoerd. Open de **Configuration Manager** het Configuratiescherm en schakel over naar de **configuraties** tabblad.  



## <a name="user-data-and-profiles-configuration-items"></a>Configuratie-items voor gebruikersgegevens en -profielen  
 Configuratie-items voor gebruikersgegevens en -profielen bevatten instellingen die bepalen hoe gebruikers op computers met Windows 8 en hoger beheren:  
   - Mapomleiding
   - Offlinebestanden
   - Zwervende profielen  

Deze configuratie-items implementeren naar gebruikersverzamelingen. Hun naleving controleren via de **bewaking** knooppunt van de Configuration Manager-console. In tegenstelling tot andere configuratie-items niet toe te voegen aan configuratiebasislijnen voordat u ze implementeert. Deze implementeren rechtstreeks door te klikken op **implementeren** in het lint.  

 Zie voor meer informatie [gebruikersgegevens en profielen configuratie-items maken](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  



## <a name="remote-connection-profiles"></a>Profielen voor externe verbindingen  
 Profielen voor externe verbindingen bieden een set hulpprogramma's en bronnen voor hulp bij het maken, implementeren en bewaken van de instellingen voor externe verbindingen. Deze instellingen implementeert op apparaten, gemakkelijker u de eindgebruikers op hun computers aansluiten op het bedrijfsnetwerk.  

Zie voor meer informatie [maken van profielen voor externe verbindingen](/sccm/compliance/deploy-use/create-remote-connection-profiles).  



## <a name="windows-edition-upgrade"></a>Windows-editie-upgrade
De editie-Upgradebeleid worden automatisch bijgewerkt voor apparaten met bepaalde versies van Windows 10 naar een nieuwere versie. Dit beleid biedt een nieuw product of licentiegegevens bestand dat door het apparaat wordt gebruikt om bij te werken.

Zie voor meer informatie [Upgrade Windows-apparaten met de editie-Upgradebeleid](/sccm/compliance/deploy-use/upgrade-windows-version)



## <a name="microsoft-edge-browser-profiles"></a>Profielen van Microsoft Edge-browser
<!-- 1357310 -->
Vanaf versie 1802, voor klanten die gebruikmaken van de [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) web browser op Windows 10-clients, maakt u een nalevingsbeleid instellingen om verschillende Microsoft Edge-instellingen te configureren. 

Zie voor meer informatie [profielen van de browser Microsoft Edge](/sccm/compliance/deploy-use/browser-profiles).

