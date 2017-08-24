---
title: Updates | Microsoft Docs
description: Meer informatie over een in de console-servicemethode aangeroepen ** Updates en onderhoud ** waarmee u gemakkelijk om te zoeken en installeren aanbevolen updates.
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
caps.latest.revision: "51"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d46aca88111d4ee0e96b75ca5a3ec57aa4274d6d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="updates-for-system-center-configuration-manager"></a>Updates voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager maakt gebruik van een in de console-servicemethode aangeroepen **Updates en onderhoud**. Deze methode in de console kunt u eenvoudig zoeken en installeren die zijn aanbevolen updates voor uw Configuration Manager-infrastructuur. Onderhoud in de console wordt aangevuld met out-of-band-updates, zoals hotfixes die zijn bedoeld voor klanten die willen oplossen van problemen die mogelijk specifiek zijn voor hun omgeving.  

> [!TIP]  
> Bij het beheren van System Center Configuration Manager-site en hiërarchie-infrastructuur, de voorwaarden *upgrade*, *bijwerken*, en *installeren* worden gebruikt voor het beschrijven van drie afzonderlijke concepten. Zie voor meer informatie over hoe elke term wordt gebruikt, [over upgrade-, update- en installatie](/sccm/core/understand/upgrade-update-install).


 **De volgende onderwerpen vindt u begrijpen hoe u om te zoeken en installeren van de verschillende updatetypen voor System Center Configuration Manager:**  

-   [Updates in de console voor System Center Configuration Manager installeren](../../../core/servers/manage/install-in-console-updates.md)  

-   [Gebruik het hulpprogramma voor serviceverbindingen voor System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md)  

-   [Gebruik het hulpprogramma registratie bijwerken om hotfixes te importeren naar System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)  

-   [Het installatieprogramma voor hotfixes gebruiken om updates te installeren voor System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  


Als u de vertakking Technical Preview gebruikt, Zie [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview) voor aanvullende informatie die specifiek is voor dat filiaal.


##  <a name="bkmk_Baselines"></a> Basislijn- en updateversies  
 De eerste release van System Center Configuration Manager current branch is versie 1511, waarmee een basislijnversie is. Meer recente basislijnversies omvatten versie 1606 en 1702:

-   Gebruik de meest recente versie van de basislijn wanneer u een nieuwe site in een nieuwe hiërarchie installeert.  

-   U kunt een basislijnversie gebruiken voor upgrade van System Center 2012 Configuration Manager. Na de upgrade naar System Center Configuration Manager moet u niet meer kunt basislijnversies Blijf en gebruiken in plaats daarvan alleen [updates in de console](/sccm/core/servers/manage/install-in-console-updates) bij te werken naar de nieuwste versie.  

-   Periodiek worden aanvullende basislijnversies gepubliceerd. Wanneer u de meest recente basislijnversie gebruikt om een nieuwe hiërarchie te installeren, moet u voorkomen dat een verouderde versie van Configuration Manager gevolgd door een extra upgrade van uw infrastructuur deze up-to-date te installeren.  

Nadat u een basislijnversie hebt geïnstalleerd, zijn aanvullende versies van Configuration Manager als updates beschikbaar in de console. Met de updates in de console wordt uw infrastructuur bijgewerkt naar de nieuwste versie van Configuration Manager.  

-   U installeert de updates in de console om de versie van uw site op het hoogste niveau bij te werken.  

-   Updates die u op de centrale beheersite automatisch installeert installeren op onderliggende primaire sites, tenzij geblokkeerd door een onderhoudsvenster dat u hebt geconfigureerd op de primaire site.  

-   U bijwerken secundaire sites handmatig naar een nieuwe updateversie uit binnen de console.  

Wanneer u een update installeert, worden de installatiebestanden voor die versie op de siteserver opgeslagen in een map met de naam CD.Latest. Zie voor meer informatie over deze bestanden [de CD. Meest recente map voor System Center Configuration Manager](../../../core/servers/manage/the-cd.latest-folder.md).  

-   U de bestanden in de CD. Meest recente map tijdens de Site Recovery en voor het installeren van aanvullende sites in een hiërarchie die een basislijnversie wordt niet meer uitgevoerd.  

-   U kunt installatiebestanden uit CD.Latest niet gebruiken om de eerste site van een nieuwe hiërarchie te installeren of om een upgrade van een site uit te voeren vanaf System Center 2012 Configuration Manager.  

Sommige updates voor Configuration Manager zijn beschikbaar als updateversie in de console voor de bestaande infrastructuur en als nieuwe basislijnversie.  

De volgende versies van Configuration Manager zijn beschikbaar als basislijn, als update of als beide:  

|Versie |Beschikbaarheidsdatum|[Einddatum voor ondersteuning](/sccm/core/servers/manage/current-branch-versions-supported) |Basislijn|Update in de console|  
|-------------|-----------|------------|--------------|------------------------|  
|[1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)<br /><br /> 5.00.8540.1000|31 juli 2017|31 juli 2018|Nee|Ja|
|[1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)<br /><br /> 5.00.8498.1000|27 maart 2017| 27 maart 2018|Ja|Ja|
|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)<br /><br /> 5.00.8458.1000|18 november 2016| 18 november 2017|Nee|Ja|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)<br /><br /> 5.00.8412.1000|22 juli 2016| 22 juli 2017|Nee|Ja|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606) met het updatepakket voor 1606 hotfix (KB3186654) </br></br>5.00.8412.1307 *(Opmerking 1)* |12 oktober 2016| 12 oktober 2017|Ja|Nee|
| 1602<br /><br /> 5.00.8355.1000|11 maart 2016| 11 maart 2017|Nee|Ja| 
| 1511 <br /><br /> 5.00.8325.1000|8 december 2015| 8 december 2016|Ja|Nee|  


*(Opmerking 1)*  De basislijnmedia 1606 en 1702 beschikbaar zijn als onderdeel van de Microsoft System Center 2016 of System Center Configuration Manager (huidige vertakking en Long-Term Servicing Branch) is uitgebracht op de [Volume licentie Service Center](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx) (VLSC). Bijvoorbeeld, op het VLSC u kunt zoeken naar *System Center Config Mgr (huidige vertakking en LTSB)*, basislijnmedia 1606 en 1702 versie zijn geretourneerde en gedownload.

Ga in de linkerbovenhoek van de console naar **Info over System Center Configuration Manager** waar de nieuwe site en consoleversie worden weergegeven als u de versie van uw Configuration Manager-site wilt controleren.  

##  <a name="bkmk_inconsole"></a> Updates en onderhoud in de console  
 Wanneer u een productie-gereed-installatie van System Center Configuration Manager, ook wel aangeduid als de huidige vertakking, zijn de meeste updates die u installeert beschikbaar via de Updates en onderhoud van kanaal. Met deze methode worden de updates die van toepassing zijn op de huidige versie en configuratie van uw infrastructuur geïdentificeerd, gedownload en beschikbaar gesteld en worden er alleen updates opgenomen die worden aanbevolen voor alle klanten.   
 Deze omvatten:  

-   Nieuwe versies, zoals versie 1610, 1702 of 1706.  

-   Updates, waaronder nieuwe functies voor uw huidige versie.

-   Hotfixes voor uw versie van Configuration Manager en dat alle klanten moeten installeren.

De updates in de console bieden een verbeterde stabiliteit en oplossingen voor algemene problemen. Deze vervangen de typen updates die werden gebruikt voor eerdere productversies voor servicepacks, cumulatieve updates, hotfixes die van toepassing zijn op alle klanten en de uitbreiding voor Microsoft Intune. Deze updates kunnen van toepassing zijn op een of meer van de volgende items:  

-   Primaire en centrale beheersiteservers  

-   Sitesysteemrollen en sitesysteemservers  

-   Exemplaren van de SMS-provider  

-   Configuration Manager-consoles  

-   Configuration Manager-clients  

Configuration Manager detecteert nieuwe updates voor u wanneer u uw site system serviceverbindingspuntrol met de Microsoft-cloudservice synchroniseren en download center:  

-   Wanneer uw serviceaansluitpunt zich in de onlinemodus bevindt, synchroniseert uw site elke dag met Microsoft om automatisch nieuwe updates te identificeren die van toepassing zijn op uw infrastructuur.  Voor het downloaden van updates en redist-bestanden voor updates, de computer die als host fungeert voor de sitesysteemrol van het Service Connection Point gebruikt de **System** context voor toegang tot de volgende Internet-locaties: go.microsoft.com en download.microsoft.com. Zie voor meer informatie over de aanvullende locatie van het service connection point verbinding met maakt [vereisten voor internettoegang](../../../core/servers/deploy/configure/about-the-service-connection-point.md#bkmk_urls) in [informatie over het serviceaansluitpunt in System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   Als uw serviceaansluitpunt zich in de offlinemodus bevindt, gebruikt u het hulpprogramma voor serviceverbindingen om handmatig te synchroniseren met de Microsoft-cloud. Zie [Het hulpprogramma voor serviceverbindingen in System Center Configuration Manager gebruiken](../../../core/servers/manage/use-the-service-connection-tool.md) voor meer informatie.  

-   Dankzij de updates in de console is het niet meer nodig om individuele updates, servicepacks en nieuwe functies onafhankelijk van elkaar te zoeken en installeren.  

-   U installeert alleen de gewenste updates in de console en bij de installatie van bepaalde updates kunt u de afzonderlijke onderdelen selecteren die u wilt inschakelen en gebruiken. Zie voor meer informatie [optionele functies van updates inschakelen](../../../core/servers/manage/install-in-console-updates.md#bkmk_options).  

Wanneer u een update in de console installeert, geldt het volgende:  

-   De vereisten worden automatisch gecontroleerd. U kunt deze controle ook uitvoeren vóór u de installatie start.  

-   De installatie wordt automatisch uitgevoerd op de centrale beheersite (indien aanwezig) en op primaire sites. U kunt bepalen wanneer elke primaire siteserver is toegestaan voor het bijwerken van de infrastructuur met behulp van [servicewindows voor siteservers Service](../../../core/servers/manage/service-windows.md).  

-   Nadat een siteserver is bijgewerkt, worden alle betrokken sitesysteemrollen (met inbegrip van exemplaren van de SMS-provider) ook automatisch bijgewerkt. Configuration Manager-consoles ook de consolegebruiker gevraagd om de console bijwerken nadat de site de update is geïnstalleerd.  

-   Als een update de Configuration Manager-client bevat, krijgt u de optie voor het testen van de update vóór productie of de update onmiddellijk toepassen op alle clients.  

-   Nadat een primaire site is bijgewerkt, worden secundaire sites niet automatisch bijgewerkt. In plaats daarvan moet u de update van de secundaire site starten.  

> [!NOTE]  
>  De productierelease van System Center Configuration Manager (huidige vertakking), de vertakking Long-Term onderhoud en de Technical Preview voor System Center Configuration Manager zijn verschillende releases. Updates die van toepassing zijn voor een vertakking zijn daarom niet beschikbaar als console-updates voor de andere filialen. Zie voor meer informatie over beschikbare vertakkingen [welke vertakking van Configuration Manager moet ik gebruiken?](/sccm/core/understand/which-branch-should-i-use)

##  <a name="bkmk_outofband"></a> Out-of-band-hotfixes  
Bepaalde hotfixes uitgebracht met beperkte beschikbaarheid om specifieke problemen te verhelpen of zijn van toepassing op alle klanten, maar kan niet installeren met behulp van de methode in de console. Deze oplossingen worden out-of-band geleverd en worden niet gedetecteerd via de Microsoft-cloudservice.  

Normaal gesproken u meer informatie over out-of-band-hotfixes van Microsoft-klantondersteuning, Knowledge Base-artikel of van de [System Center Configuration Manager-teamblog](https://blogs.technet.microsoft.com/configmgrteam) wanneer u zoekt is een probleem met uw implementatie van Configuration Manager wilt oplossen.  

U installeert deze oplossingen handmatig op een van de twee volgende manieren:  

-   **Registratiehulpprogramma bijwerken:** Dit hulpprogramma kunt de hotfix handmatig importeren in uw Configuration Manager-console waar u kunt vervolgens de update installeren zoals u zou in de console-updates die automatisch worden gedetecteerd. Deze methode wordt gebruikt voor updates die gebruikmaken van de volgende bestandsnaamstructuur: **.update.exe**.  De volledige bestandsnaam voor dit type hotfix ziet er als: **&lt;Product\>-&lt;productversie\>-&lt;KB-artikel-ID\>-ConfigMgr.Update.exe**.  

     Zie voor meer informatie [gebruik het hulpprogramma registratie bijwerken om hotfixes te importeren naar System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

-   **Hotfix-installatieprogramma:** Dit hulpprogramma wordt gebruikt voor het handmatig een hotfix installeren waarnaar kan niet worden geïnstalleerd via de methode in de console. Deze methode wordt gebruikt voor oplossingen die gebruikmaken van de volgende bestandsnaamstructuur: **&lt;Product\>-&lt;product version\>-&lt;KB article ID\>-&lt;platform\>-&lt;language\>.exe**.

     Zie voor meer informatie [het Hotfix-installatieprogramma gebruiken om updates te installeren voor System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md).
