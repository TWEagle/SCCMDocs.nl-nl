---
title: Updates | Microsoft-documenten
description: Meer informatie over een in de console-servicemethode aangeroepen **Updates en onderhoud** waarmee u gemakkelijk te zoeken en installeren van aanbevolen updates.
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
caps.latest.revision: 51
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: a33960fb89b71c0f8128e21a5054f5b63cfc6b17
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="updates-for-system-center-configuration-manager"></a>Updates voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager maakt gebruik van een in de console-servicemethode aangeroepen **Updates en onderhoud** waarmee u gemakkelijk om te zoeken en installeren aanbevolen updates voor uw Configuration Manager-infrastructuur. Deze servicing methode in de console wordt aangevuld met out-of-band-updates zoals hotfixes die zijn bedoeld voor klanten met nodig problemen oplossen die mogelijk specifiek zijn voor hun omgeving.  

> [!TIP]
> Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt om te beschrijven van drie verschillende concepten... Zie voor meer informatie over hoe elke term wordt gebruikt, [over upgrade-, update- en installatie](/sccm/core/understand/upgrade-update-install).


 **De volgende onderwerpen vindt u leert hoe u om te zoeken en installeren van de verschillende update-typen voor System Center Configuration Manager:**  

-   [In de console updates installeren voor System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md)  

-   [Gebruik het hulpprogramma voor Service-verbinding voor System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md)  

-   [De Update registratie-hulpprogramma gebruiken om te importeren hotfixes voor System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)  

-   [De Hotfix-installatieprogramma gebruiken om updates te installeren voor System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  


Als u de vertakking Technical Preview, Zie [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview) voor aanvullende informatie die specifiek is voor dat filiaal.


##  <a name="bkmk_Baselines"></a> Basislijn- en updateversies  
 De eerste versie van System Center Configuration Manager huidige vertakking is versie 1511, die een versie van de basislijn is. Meer recente versies van de basislijn omvatten versie 1606 en 1702:

-   Gebruik de meest recente versie van de basislijn wanneer u een nieuwe site in een nieuwe hiërarchie installeert.  

-   Voor een upgrade van System Center 2012 Configuration Manager moet u een basislijnversie gebruiken.  

-   Periodiek worden aanvullende basislijn versies gepubliceerd. Wanneer u een nieuwe hiërarchie die u Voorkom dat de installatie van een verouderde versie van Configuration Manager installeren via de meest recente versie van de basislijn, gevolgd door een upgrade van uw infrastructuur om deze up-to-date te brengen.  

Nadat u een basislijnversie hebt geïnstalleerd, zijn aanvullende versies van Configuration Manager als updates beschikbaar in de console. Met de updates in de console wordt uw infrastructuur bijgewerkt naar de nieuwste versie van Configuration Manager.  

-   U installeert de updates in de console om de versie van uw site op het hoogste niveau bij te werken.  

-   Updates die u op de centrale beheersite installeert, worden automatisch geïnstalleerd op onderliggende primaire sites, tenzij deze worden geblokkeerd door een onderhoudsvenster dat u hebt geconfigureerd op de primaire site.  

-   Secundaire sites moet u vanuit de console handmatig bijwerken naar een nieuwe updateversie.  

Wanneer u een update installeert, worden de installatiebestanden voor die versie op de siteserver opgeslagen in een map met de naam CD.Latest. Zie [de CD. Meest recente map voor System Center Configuration Manager](../../../core/servers/manage/the-cd.latest-folder.md) voor meer informatie over deze bestanden.  

-   U gebruikt de bestanden in de map CD.Latest tijdens het siteherstel en voor het installeren van extra sites in een hiërarchie waarmee geen basislijnversie meer wordt uitgevoerd.  

-   U kunt installatiebestanden uit CD.Latest niet gebruiken om de eerste site van een nieuwe hiërarchie te installeren of om een upgrade van een site uit te voeren vanaf System Center 2012 Configuration Manager.  

Sommige updates voor Configuration Manager zijn beschikbaar als updateversie in de console voor de bestaande infrastructuur en als nieuwe basislijnversie.  

De volgende versies van Configuration Manager zijn beschikbaar als basislijn, als update of als beide:  

|Versie |Beschikbaarheidsdatum|[Einddatum voor ondersteuning](/sccm/core/servers/manage/current-branch-versions-supported) |Basislijn|Update in de console|  
|-------------|-----------|------------|--------------|------------------------|  
|[1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)<br /><br /> 5.00.8498.1000|3/27/2017| 3/27/2018|Ja|Ja|
|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)<br /><br /> 5.00.8458.1000|11/18/2016| 11/18/2017|Nee|Ja|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)<br /><br /> 5.00.8412.1000|7/22/2016| 7/22/2017|Nee|Ja|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606) met het updatepakket 1606 hotfix (KB3186654) </br></br>5.00.8412.1307 *(Houd er rekening mee 1)* |10/12/2016| 7/22/2017|Ja|Nee|
| 1602<br /><br /> 5.00.8355.1000|11-3-2016| 3/11/2017|Nee|Ja|
| 1511 <br /><br /> 5.00.8325.1000|8-12-2015| 12/8/2016|Ja|Nee|  


*(Zie Opmerking 1) * Deze basislijn 1606 media is verkrijgbaar als onderdeel van Microsoft System Center 2016 of release voor System Center Configuration Manager (huidige vertakking en langetermijnbeveiliging onderhoud vertakking 1606).

Ga in de linkerbovenhoek van de console naar **Info over System Center Configuration Manager** waar de nieuwe site en consoleversie worden weergegeven als u de versie van uw Configuration Manager-site wilt controleren.  

##  <a name="bkmk_inconsole"></a> Updates en onderhoud in de console  
 Wanneer u een productie gereed installatie van System Center Configuration Manager, ook worden aangeduid als de huidige vertakking wordt weergegeven, zijn de meeste updates die u installeert beschikbaar via de Updates en onderhoud kanaal. Met deze methode worden de updates die van toepassing zijn op de huidige versie en configuratie van uw infrastructuur geïdentificeerd, gedownload en beschikbaar gesteld en worden er alleen updates opgenomen die worden aanbevolen voor alle klanten.   
 Deze omvatten:  

-   Nieuwe versies, zoals versie 1610  

-   Updates, waaronder nieuwe functies voor uw huidige versie  

-   Hotfixes voor uw versie van Configuration Manager, die alle klanten moeten installeren  

De updates in de console bieden een verbeterde stabiliteit en oplossingen voor algemene problemen. Deze vervangen de typen updates die werden gebruikt voor eerdere productversies voor servicepacks, cumulatieve updates, hotfixes die van toepassing zijn op alle klanten en de uitbreiding voor Microsoft Intune. Deze updates kunnen van toepassing zijn op een of meer van de volgende items:  

-   Primaire en centrale beheersiteservers  

-   Sitesysteemrollen en sitesysteemservers  

-   Exemplaren van de SMS-provider  

-   Configuration Manager-consoles  

-   Configuration Manager-clients  

Configuration Manager detecteert nieuwe updates voor u wanneer u uw service verbinding sitesysteemrol worden gesynchroniseerd met de cloudservice van Microsoft en Downloadcentrum:  

-   Wanneer uw serviceaansluitpunt zich in de onlinemodus bevindt, synchroniseert uw site elke dag met Microsoft om automatisch nieuwe updates te identificeren die van toepassing zijn op uw infrastructuur.  Downloaden van updates en redist-bestanden voor updates, de computer die als host fungeert voor de Service Connection Point-sitesysteemrol gebruikt de **System** context voor toegang tot de volgende locaties Internet: go.microsoft.com en download.microsoft.com. Zie voor meer informatie over de aanvullende locatie van de service connection point maakt verbinding met [vereisten voor internettoegang](../../../core/servers/deploy/configure/about-the-service-connection-point.md#bkmk_urls) in [over de verbinding met de punt in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   Als uw serviceaansluitpunt zich in de offlinemodus bevindt, gebruikt u het hulpprogramma voor serviceverbindingen om handmatig te synchroniseren met de Microsoft-cloud. Zie [Het hulpprogramma voor serviceverbindingen in System Center Configuration Manager gebruiken](../../../core/servers/manage/use-the-service-connection-tool.md) voor meer informatie.  

-   Dankzij de updates in de console is het niet meer nodig om individuele updates, servicepacks en nieuwe functies onafhankelijk van elkaar te zoeken en installeren.  

-   U installeert alleen de gewenste updates in de console en bij de installatie van bepaalde updates kunt u de afzonderlijke onderdelen selecteren die u wilt inschakelen en gebruiken. Zie voor meer informatie [optionele functies van updates inschakelen](../../../core/servers/manage/install-in-console-updates.md#bkmk_options).  

Wanneer u een update in de console installeert, geldt het volgende:  

-   De vereisten worden automatisch gecontroleerd. U kunt deze controle ook uitvoeren vóór u de installatie start.  

-   De installatie wordt automatisch uitgevoerd op de centrale beheersite (indien aanwezig) en op primaire sites. U kunt bepalen wanneer elke primaire siteserver is toegestaan voor het bijwerken van de infrastructuur met behulp van [windows voor siteservers Service](../../../core/servers/manage/service-windows.md).  

-   Nadat een siteserver is bijgewerkt, worden alle betrokken sitesysteemrollen (met inbegrip van exemplaren van de SMS-provider) ook automatisch bijgewerkt. Configuration Manager-consoles ook de consolegebruiker vragen naar de console bijwerken wanneer de site de update is geïnstalleerd.  

-   Als een update de Configuration Manager-client bevat, krijgt u de optie voor het testen van de update in test of de update onmiddellijk toepassen op alle clients.  

-   Nadat een primaire site is bijgewerkt, worden secundaire sites niet automatisch bijgewerkt. In plaats daarvan moet u de update van de secundaire site starten.  

> [!NOTE]  
>  De productierelease van System Center Configuration Manager (huidige vertakking), de vertakking langetermijndoelen onderhoud en technische Preview van System Center Configuration Manager zijn verschillende releases. Updates die van toepassing zijn voor een vertakking zijn daarom niet beschikbaar als de console updates voor de andere takken. Zie voor meer informatie over beschikbare vertakkingen [welke vertakking van Configuration Manager moet ik gebruiken?](/sccm/core/understand/which-branch-should-i-use)

##  <a name="bkmk_outofband"></a> Out-of-band-hotfixes  
Bepaalde hotfixes worden uitgebracht met beperkte beschikbaarheid om specifieke problemen te verhelpen of zijn van toepassing op alle klanten, maar kunnen niet worden geïnstalleerd via de console. Deze oplossingen worden out-of-band geleverd en worden niet gedetecteerd via de Microsoft-cloudservice.  

Normaal gesproken u meer informatie over out-of-band hotfixes van Microsoft-klantondersteuning, Knowledge Base-artikel of van de [System Center Configuration Manager-teamblog](https://blogs.technet.microsoft.com/configmgrteam) wanneer u zoekt oplossen of een probleem met uw implementatie van Configuration Manager.  

U installeert deze oplossingen handmatig op een van de twee volgende manieren:  

-   **Registratie van update:** De hotfix voor importeert dit hulpprogramma handmatig in uw Configuration Manager-console waar u kunt vervolgens de update installeren zoals u zou-console updates die automatisch worden gedetecteerd. Deze methode wordt gebruikt voor updates die gebruikmaken van de volgende bestandsnaamstructuur: **.update.exe**.  De volledige bestandsnaam voor dit type hotfix lijkt op: **&lt;Product\>-&lt;productversie\>-&lt;KB-artikel-ID\>-ConfigMgr.Update.exe**.  

     Zie voor meer informatie [de Update registratie-hulpprogramma gebruiken om te importeren hotfixes voor System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

-   **Hotfix-installatieprogramma:** Dit hulpprogramma wordt gebruikt voor het handmatig een hotfix installeren waarnaar kan niet worden geïnstalleerd via de methode in de console. Deze methode wordt gebruikt voor de oplossingen die gebruikmaken van de structuur van de naam van het volgende: **&lt;Product\>-&lt;product version\>-&lt;KB article ID\>-&lt;platform\>-&lt;language\>.exe**.

     Zie voor meer informatie [de Hotfix-installatieprogramma gebruiken om updates te installeren voor System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md).

