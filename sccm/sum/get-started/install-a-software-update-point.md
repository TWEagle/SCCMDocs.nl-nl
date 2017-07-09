---

title: Installeren en configureren van software-updatepunt | Microsoft Docs
description: Primaire sites vereisen een software-updatepunt op de centrale beheersite voor beoordeling van compatibiliteit van software-updates en software-updates implementeren op clients.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 05/30/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b099a645-6434-498f-a408-1d438e394396
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc221ddf547c43ab1f25ff83c3c9bb603297ece6
ms.openlocfilehash: 7d369384d133c90a15e01df50ac53992d61f3873
ms.contentlocale: nl-nl
ms.lasthandoff: 06/01/2017



---


# <a name="install-and-configure-a-software-update-point"></a>Installeren en configureren van software-updatepunt  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


> [!IMPORTANT]  
>  Voordat u de sitesysteemrol van het software-updatepunt installeert, moet u verifiëren dat de server voldoet aan de vereiste afhankelijkheden en de software-updatepuntinfrastructuur op de site bepaalt. Zie voor meer informatie over het plannen van softwareupdates en het bepalen van uw software-updatepuntinfrastructuur [plannen voor software-updates](../plan-design/plan-for-software-updates.md).  

 Het software-updatepunt is vereist op de centrale beheersite en op de primaire sites om het inschakelen van de compatibiliteitsbeoordeling van software-updates en het implementeren van software-updates op clients mogelijk te maken. Het software-updatepunt is optioneel op secundaire sites. De sitesysteemrol van het software-updatepunt moet op een server worden gemaakt waar WSUS op is geïnstalleerd. Het software-updatepunt communiceert met de WSUS-services om de software-update-instellingen te configureren en om de synchronisatie van de metagegevens van software-updates aan te vragen. Wanneer u een Configuration Manager-hiërarchie hebt, installeren en configureren van het software-updatepunt op de centrale beheersite eerst, klikt u vervolgens op onderliggende primaire sites, en vervolgens optioneel op secundaire sites. Als u een zelfstandige primaire site hebt, en geen centrale beheersite, dient u eerst het software-updatepunt op de primaire site, en vervolgens optioneel op secundaire sites, te installeren en configureren. Sommige instellingen zijn alleen beschikbaar wanneer u het software-updatepunt op een site op het hoogste niveau configureert. Er zijn verschillende opties die u moet overwegen, afhankelijk van waar u het software-updatepunt hebt geïnstalleerd.  

> [!IMPORTANT]  
>  U kunt meerdere software-updatepunten op een site installeren. Het eerste software-updatepunt dat u installeert, wordt geconfigureerd als de synchronisatiebron: dit software-updatepunt synchroniseert de updates van Microsoft Update of van de upstream-synchronisatiebron. De andere software-updatepunten op de site zijn geconfigureerd als replica's van het eerste software-updatepunt. Daarom zijn sommige instellingen niet beschikbaar na het installeren en configureren van het oorspronkelijke software-updatepunt.  

> [!IMPORTANT]  
>  Wordt niet ondersteund voor het installeren van de sitesysteemrol van software-update-punt op een server die is geconfigureerd en gebruikt als een zelfstandige WSUS-server of met een software-updatepunt voor het rechtstreeks beheren van WSUS-clients. Bestaande WSUS-servers worden alleen ondersteund als de synchronisatiebron stroomopwaarts bronnen voor het actieve software-updatepunt. Zie [synchroniseren vanaf een gegevensbronlocatie stroomopwaarts](#BKMK_wsussync)

 U kunt de sitesysteemrol van het software-updatepunt toevoegen aan een bestaande sitesysteemserver of u kunt een nieuwe sitesysteemrol maken. Selecteer **Software-updatepunt** op de pagina **Systeemrolselectie** van de **wizard Sitesysteemserver** maken of de wizard **Sitesysteemrollen toevoegen**, afhankelijk van of u de sitesysteemrol toevoegt aan een nieuwe of bestaande siteserver. Vervolgens configureert u de instellingen voor het software-updatepunt in de wizard. De instellingen zijn verschillend afhankelijk van de versie van Configuration Manager die u gebruikt. Zie voor meer informatie over het installeren van sitesysteemrollen [sitesysteemrollen installeren](../../core/servers/deploy/configure/install-site-system-roles.md).  

 Gebruik de volgende secties voor informatie over de software-updatepuntinstellingen op een site.  

## <a name="proxy-server-settings"></a>Proxyserverinstellingen  
 U kunt de proxyserverinstellingen configureren op verschillende pagina's van de **maken Wizard Sitesysteemserver** of **toevoegen Wizard sitesysteemrollen** afhankelijk van de versie van Configuration Manager die u gebruikt.  

-   U moet de proxyserver configureren en vervolgens opgeven wanneer de proxyserver moet worden gebruikt voor software-updates. Configureer de volgende instellingen:  

    -   Configureer de proxyserverinstellingen op de pagina **Proxy** van de wizard of op het tabblad **Proxy** in de sitesysteemeigenschappen. De proxyserverinstellingen zijn sitesysteemspecifiek; dat betekent dat alle sitesysteemrollen de proxyserverinstellingen gebruikt die u opgeeft.  

    -   Geef op of de proxyserver gebruiken bij synchroniseren van Configuration Manager de software-updates en wanneer het inhoud downloadt met behulp van een regel voor automatische implementatie. Configureer de proxyserverinstellingen van het software-updatepunt op de pagina **Proxy- en accountinstellingen** van de wizard of op het tabblad **Proxy- en accountinstellingen** in de eigenschappen van het software-updatepunt.  

        > [!NOTE]  
        >  De instelling **Een proxyserver gebruiken wanneer inhoud wordt gedownload via automatische implementatieregels** is beschikbaar, maar wordt niet gebruikt voor een software-updatepunt op een secundaire site. Alleen het software-updatepunt op de centrale beheersite en de primaire site downloadt inhoud van de Microsoft Update-pagina.  

> [!IMPORTANT]  
>  Standaard wordt het account **Lokaal systeem** voor de server waarop een automatische implementatieregel is gemaakt, gebruikt om verbinding te maken met het internet en software-updates te downloaden wanneer de automatische implementatieregels worden uitgevoerd. Wanneer dit account geen toegang tot Internet heeft, mislukt de software-updates te downloaden en de volgende vermelding wordt vastgelegd in het logboekbestand ruleengine.log opgeslagen: **De update downloaden van internet is mislukt. Fout = 12007**. Configureer de referenties om verbinding te maken met de proxyserver wanneer het lokale systeemaccount geen internettoegang heeft.  


## <a name="wsus-settings"></a>WSUS-instellingen  
 U moet de WSUS-instellingen configureren op verschillende pagina's van de **maken Wizard Sitesysteemserver** of **toevoegen Wizard sitesysteemrollen** afhankelijk van de versie van Configuration Manager die u gebruikt, en in sommige gevallen, alleen in de eigenschappen voor de software-updatepunt, ook wel bekend als onderdeeleigenschappen van Software. Gebruik de informatie in de volgende secties om de WSUS-instellingen te configureren.  

### <a name="BKMK_wsusport"></a>WSUS-poortinstellingen  
 U moet de WSUS-poortinstellingen configureren op de pagina Software-updatepunt van de wizard of in de eigenschappen van het software-updatepunt. Gebruik de volgende procedure om te bepalen welke poortinstellingen worden gebruikt voor WSUS.  

#### <a name="to-determine-the-port-settings-used-in-iis"></a>Bepalen welke poortinstellingen worden gebruikt in IIS  

 1.  Open IIS-beheer (Internet Information Services) op de WSUS-server.  

 2.  Vouw **Sites**uit, klik met de rechtermuisknop op de website voor de WSUS-server en klik op **Bindingen bewerken**. In het dialoogvenster Sitebindingen worden de waarden voor de HTTP- en HTTPS-poort weergegeven in de kolom **Poort** .


### <a name="configure-ssl-communications-to-wsus"></a>SSL-communicatie naar WSUS configureren  
 U kunt SSL-communicatie configureren op de pagina **Algemeen** van de wizard of op het tabblad **Algemeen** in de eigenschappen van het software-updatepunt.  

 Voor meer informatie over het gebruik van SSL, zie [Beslissen om WSUS te configureren voor gebruik van SSL](../plan-design/plan-for-software-updates.md#BKMK_WSUSandSSL).  

### <a name="wsus-server-connection-account"></a>WSUS-serververbindingsaccount  
 U kunt een account configureren voor gebruik door de siteserver wanneer het verbinding maakt met WSUS dat op het software-updatepunt wordt uitgevoerd. Als u dit account niet configureert, wordt in de Configuration Manager het computeraccount voor de siteserver gebruikt om verbinding met WSUS. Configureer het WSUS-serververbindingsaccount op de pagina **Proxy- en accountinstellingen** van de wizard of op het tabblad **Proxy- en accountinstellingen** in de eigenschappen van het software-updatepunt.  U kunt het account configureren op verschillende plaatsen in de wizard afhankelijk van de versie van Configuration Manager die u gebruikt.  

 Zie voor meer informatie over Configuration Manager-accounts, [Accounts die worden gebruikt in System Center Configuration Manager](../../core/plan-design/hierarchy/accounts.md).  

## <a name="synchronization-source"></a>Synchronisatiebron  
 U kunt de synchronisatiebron stroomopwaarts voor de synchronisatie van software-updates configureren op de pagina **Synchronisatiebron** van de wizard, of op het tabblad **Synchronisatie-instellingen** in de eigenschappen van software-updatepuntcomponenten. Uw opties voor de synchronisatiebron variëren in functie van de site.  

 Gebruik de volgende tabl voor de beschikbare opties wanneer u he software-updatepunt op een site configureert.  

|Site|Beschikbare opties voor synchronisatiebron|  
|----------|----------------------------------------------|  
|-   Centrale beheersite<br />-   Zelfstandige primaire site|-   Synchroniseren vanaf de website Microsoft Update<br />-   Synchroniseren vanaf een gegevensbronlocatie stroomopwaarts<br />-   Niet synchroniseren vanaf Microsoft Update of een gegevensbron stroomopwaarts|  
|-   Extra software-updatepunten op een site<br />-   Onderliggende primaire site<br />-   Secundaire site|-   Synchroniseren vanaf een gegevensbronlocatie stroomopwaarts|  

 De volgende lijst geeft meer informatie over elke optie die u kunt gebruiken als de synchronisatiebron:  

-   **Synchroniseren vanuit Microsoft Update**: Gebruik deze instelling om te synchroniseren metagegevens van software-updates vanaf Microsoft Update. De centrale beheersite moet toegang tot het internet hebben; anders zal de synchronisatie mislukken. De instelling is alleen beschikbaar wanneer u het software-updatepunt op een site op het hoogste niveau configureert.  

    > [!NOTE]  
    >  Wanneer zich een firewall tussen het software-updatepunt en internet bevindt, moet de firewall mogelijk worden geconfigureerd om de HTTP- en HTTPS-poorten te accepteren die worden gebruikt voor de WSUS-website. U kunt ook kiezen om de toegang op de firewall te beperken tot beperkte domeinen. Zie [Firewalls configureren](../plan-design/plan-for-software-updates.md#BKMK_ConfigureFirewalls) voor meer informatie over het plannen van een firewall die software-updates ondersteunt.  

-   **<a name="BKMK_wsussync"></a>Synchroniseren vanaf een gegevensbronlocatie stroomopwaarts**: Deze instelling gebruiken om metagegevens van software-updates vanaf de synchronisatiebron stroomopwaarts te synchroniseren. De onderliggende primaire sites en secundaire sites worden automatisch geconfigureerd om de URL van de bovenliggende site voor deze instelling te gebruiken. U kunt de software-updates synchroniseren vanaf een bestaande WSUS-server. Geef een URL, zoals https://WSUSServer:8531, waarbij 8531 de poort is die wordt gebruikt om een verbinding te maken met de WSUS-server.  

-   **Niet synchroniseren vanuit Microsoft Update of gegevensbron stroomopwaarts**: Deze instelling gebruiken om software-updates handmatig synchroniseren wanneer het software-updatepunt op het hoogste niveau niet is verbonden met Internet. Zie de sectie [Software-updates synchroniseren vanaf een niet-verbonden software-updatepunt](synchronize-software-updates-disconnected.md) voor meer informatie.  

> [!NOTE]  
>  Wanneer zich een firewall tussen het software-updatepunt en internet bevindt, moet de firewall mogelijk worden geconfigureerd om de HTTP- en HTTPS-poorten te accepteren die worden gebruikt voor de WSUS-website. U kunt ook kiezen om de toegang op de firewall te beperken tot beperkte domeinen. Zie [Firewalls configureren](../plan-design/plan-for-software-updates.md#BKMK_ConfigureFirewalls) voor meer informatie over het plannen van een firewall die software-updates ondersteunt.  

 U kunt ook configureren of u WSUS-rapportagegebeurtenissen op de pagina **Synchronisatiebron** van de wizard of op het tabblad **Synchronisatie-instellingen** in de eigenschappen van software-updatepuntcomponenten. Configuration Manager gebruikt deze gebeurtenissen; niet Daarom kiest u doorgaans de standaardinstelling **geen WSUS-rapportagegebeurtenissen maken**.  

## <a name="synchronization-schedule"></a>Synchronisatieplanning  
 Configureer de synchronisatieplanning op het tabblad **Synchronisatieplanning** van de wizard of in de eigenschappen van software-updatepuntcomponenten. Deze instelling wordt alleen geconfigureerd op het software-updatepunt op de site op het hoogste niveau.  

 Als u de planning inschakelt, kunt u een terugkerende eenvoudige of aangepaste synchronisatieplanning configureren. Wanneer u een eenvoudige planning configureert, worden de begintijd is gebaseerd op de lokale tijd voor de computer die de Configuration Manager-console uitvoert op het moment dat u de planning maakt. Wanneer u de begintijd voor een aangepaste planning configureert, is het gebaseerd op de lokale tijd voor de computer waarop de Configuration Manager-console.  

> [!TIP]  
>  Maak een zodanige planning dat de synchronisatie van de software-updates wordt uitgevoerd met een tijdskader dat geschikt is voor uw omgeving. Een typisch scenario is het instellen van de planning voor de synchronisatie van software-updates om uit te voeren kort na de regelmatige vrijgave van de beveiligingsupdate van Microsoft op de tweede dinsdag van elke maand, die gewoonlijk Patch Dinsdag wordt genoemd. Een ander typisch scenario is het instellen van de planning voor de synchronisatie van software-updates om dagelijks uitgevoerd te worden wanneer u software-updates gebruikt om de Endpoint Protection-definitie en engine-updates te leveren.  

> [!NOTE]  
>  Wanneer u ervoor kiest geen synchronisatie van software-updates op een planning in te schakelen, kunt u software-updates handmatig synchroniseren vanuit het knooppunt **Alle software-updates** of **Software-updategroepen** in de werkruimte Softwarebibliotheek. Zie voor meer informatie [software-updates synchroniseren](synchronize-software-updates.md).  

## <a name="supersedence-rules"></a>Vervangingsregels  
 Configureer de vervangingsregels op de pagina **Vervangingsregels** van de wizard of op het tabblad **Vervangingsregels** in de eigenschappen van software-updatepuntcomponenten. U kunt de vervangingsregels enkel op de site op het hoogste niveau configureren.  

 Op deze pagina kunt u specificeren dat de vervangen software-updates onmiddellijk verlopen zijn, hetgeen voorkomt dat ze worden opgenomen in nieuwe implementaties en de bestaande implementaties markeert om aan te geven dat de vervangen software-updates een of meerdere verlopen software-updates bevatten. U kunt ook een periode opgeven waarna de vervangen software-updates verlopen, zodat u ze nog kunt blijven implementeren. Voor meer informatie, zie [Vervangingsregels](../plan-design/plan-for-software-updates.md#BKMK_SupersedenceRules).  

> [!NOTE]  
>  De pagina **Vervangingsregels** van de wizard is enkel toegankelijk wanneer u het eerste software-updatepunt op de site configureert. Deze pagina wordt niet weergegeven wanneer u aanvullende software-updatepunten installeert.  

## <a name="classifications"></a>Classificaties  
 Configureer de classificatie-instellingen op de pagina **Classificaties** van de wizard of op het tabblad **Classificaties** in de eigenschappen van software-updatepuntcomponenten. Voor meer informatie over software-updateclassificaties, zie[Updateclassificaties](../plan-design/plan-for-software-updates.md#BKMK_UpdateClassifications).  

> [!NOTE]  
>  De pagina **Classificaties** van de wizard is alleen beschikbaar wanneer u het eerste software-updatepunt op de site configureert. Deze pagina wordt niet weergegeven wanneer u aanvullende software-updatepunten installeert.  

> [!TIP]  
>  Wanneer u het software-updatepunt op de site op het hoogste niveau voor het eerst installeert, wis dan alle software-updataclassificaties. Na de initiële synchronisatie van de software-updates configureert u de classificaties vanuit een bijgewerkte lijst, en start u de synchronisatie opnieuw. Deze instelling wordt alleen geconfigureerd op het software-updatepunt op de site op het hoogste niveau.  

## <a name="products"></a>Producten  
 Configureer de productinstellingen op de pagina **Producten** van de wizard of op het tabblad **Producten** in de eigenschappen van software-updatepuntcomponenten.  

> [!NOTE]  
>  De pagina **Producten** van de wizard is alleen beschikbaar wanneer u het eerste software-updatepunt op de site configureert. Deze pagina wordt niet weergegeven wanneer u aanvullende software-updatepunten installeert.  

> [!TIP]  
>  Wanneer u het software-updatepunt op de site op het hoogste niveau voor het eerst installeert, wis dan alle producten. Na de initiële synchronisatie van de software-updates configureert u de producten vanuit een bijgewerkte lijst, en start u de synchronisatie opnieuw. Deze instelling wordt alleen geconfigureerd op het software-updatepunt op de site op het hoogste niveau.  

## <a name="languages"></a>Talen  
 Configureer de taalinstellingen op de pagina **Talen** van de wizard of op het tabblad **Talen** in de eigenschappen van software-updatepuntcomponenten. Specificeer de talen waarvoor u software-updatebestanden en overzichtsgegevens wilt synchroniseren. De **Software-updatebestand** instelling is geconfigureerd op elk software-updatepunt in de Configuration Manager-hiërarchie. De **Overzichtsgegevens** -instellingen worden enkel geconfigureerd op het software-updatepunt op het hoogste niveau. Voor meer informatie raadpleegt u [Talen](../plan-design/plan-for-software-updates.md#BKMK_UpdateLanguages).  

> [!NOTE]  
>  De pagina **Talen** van de wizard is alleen beschikbaar wanneer u het software-updatepunt op de centrale beheersite installeert. U kunt de talen van het Software-updatebestand op onderliggende sites configureren op het tabblad **Talen** in de eigenschappen van software-updatecomponenten.  

## <a name="next-steps"></a>Volgende stappen
U de software-updatepunt beginnen bij de bovenste site in uw Configuration Manager-hiërarchie hebt geïnstalleerd. Herhaal de procedures in dit onderwerp voor het installeren van de software-updatepunt op onderliggende sites.

Zodra u de software-updatepunten geïnstalleerd, gaat u naar [software-updates synchroniseren](synchronize-software-updates.md).

