---
title: Linux en UNIX-servertoepassingen maken
titleSuffix: Configuration Manager
description: Zie welke overwegingen u moet rekening account wanneer u maken en implementeren van toepassingen voor Linux en Unix-apparaten.
ms.custom: na
ms.date: 04/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 79cd131a-1a24-4751-87c8-7f275e45d847
caps.latest.revision: "7"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 81a3ef6ee05a8f0f66ca1a70d56bc33017c66d9c
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-linux-and-unix-server-applications-with-system-center-configuration-manager"></a>Maken van Linux en UNIX-servertoepassingen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Rekening houden met de volgende overwegingen wanneer u toepassingen maakt en implementeert voor computers waarop Linux en UNIX wordt uitgevoerd.  

## <a name="general-considerations"></a>Algemene overwegingen  
 De Configuration Manager-client voor Linux en UNIX ondersteunt **software-implementaties die pakketten en programma's gebruiken**. U kunt geen Configuration Manager op computers met Linux en UNIX-toepassingen implementeren.  

 De mogelijkheden van de software-implementatie voor Linux en UNIX:  

-   De installatie van de software voor Linux en UNIX-servers, waaronder de volgende:  

    -   Nieuwe software-implementatie  

    -   Software-updates voor programma's die zich al op een computer  

    -   Patches voor besturingssysteem  

-   Systeemeigen Linux en UNIX-opdrachten en scripts die zich bevinden op Linux en UNIX-servers  

-   Implementaties die beperkt tot de besturingssystemen zijn die u opgeeft wanneer u de programma-optie selecteert **alleen op gespecificeerde clientplatforms**

-   Onderhoudsvensters om te bepalen wanneer software wordt geïnstalleerd

-   Statusberichten voor implementatie voor het bewaken van implementaties  

-   De optie voor de client versnelling netwerkgebruik wanneer deze software wordt gedownload van een distributiepunt  

### <a name="differences-between-deploying-to-linux-and-unix-computers-and-deploying-to-windows-devices"></a>Verschillen tussen op Linux en UNIX-computers implementeren en te implementeren op Windows-apparaten
De belangrijkste verschillen tussen het implementeren van pakketten en programma's op Linux en UNIX-computers en het implementeren van pakketten en programma's op Windows-apparaten zijn als volgt:  

|Configuration|Details|  
|-------------------|-------------|  
|Enkel configuraties gebruiken die zijn bedoeld voor computers en configuraties die bedoeld zijn voor gebruikers niet gebruiken.|Configuration Manager-client voor Linux en UNIX biedt geen ondersteuning voor configuraties die bedoeld zijn voor gebruikers.|  
|Software van het distributiepunt downloaden en uitvoeren van de programma's uit de lokale clientcache-programma's configureren.|Configuration Manager-client voor Linux en UNIX biedt geen ondersteuning voor software van het distributiepunt. In plaats daarvan moet u de software te downloaden naar de client en vervolgens geïnstalleerd.<br /><br /> Nadat de client voor Linux en UNIX software heeft geïnstalleerd, wordt deze software standaard van de clientcache verwijderd. Pakketten die geconfigureerd zijn met **Inhoud in de clientcache behouden** worden niettemin niet verwijderd van de client en blijven in de clientcache nadat de software is geïnstalleerd.<br /><br /> Configuraties voor de clientcache worden niet door de client voor Linux en UNIX ondersteund en de maximale grootte van de clientcache is enkel beperkt door de vrije schijfruimte op de clientcomputer.|  
|Het netwerktoegangsaccount voor distributiepunttoegang configureren|Linux-en UNIX-computers zijn ontworpen als werkgroepcomputers. Voor toegang tot pakketten van het distributiepunt in de Configuration Manager site server-domein, moet u het netwerktoegangsaccount voor de site configureren. U moet dit account opgeven als een componenteigenschap voor softwaredistributie en het account configureren voordat u software implementeert.<br /><br /> U kunt op elke site meerdere netwerktoegangsaccounts configureren. De client voor Linux en UNIX kan elk van de accounts die u configureert als een netwerktoegangsaccount gebruiken.<br /><br /> Zie [Siteonderdelen voor System Center Configuration Manager](../../core/servers/deploy/configure/site-components.md) voor meer informatie.|  

 U kunt pakketten en programma's implementeren naar verzamelingen die enkel Linux- of UNIX-clients bevatten of u kunt deze implementeren naar verzamelingen met een mengeling van clienttypen, zoals de **Verzameling Alle systemen**. Niet-Linux- en niet-UNIX-clients niet echter de software- of mislukte geïnstalleerd.  

 Wanneer de Configuration Manager-client voor Linux en UNIX ontvangt en een implementatie wordt uitgevoerd, worden statusberichten gegenereerd. U kunt deze statusberichten weergeven in de Configuration Manager-console of met behulp van rapporten om de implementatiestatus te controleren.  

 Zie voor meer informatie over het gebruik van pakketten en programma's [pakketten en programma's](../../apps/deploy-use/packages-and-programs.md).  

##  <a name="configure-packages-programs-and-deployments-for-linux-and-unix-servers"></a>Pakketten, programma's en implementaties voor Linux en UNIX-servers configureren  
 U kunt maken en implementeren van pakketten en programma's met behulp van de standaardopties zijn beschikbaar in de Configuration Manager-console. Unieke configuraties zijn niet vereist voor de client.  

 Gebruik de informatie in de volgende secties zowel om pakketten en programma's als implementaties te configureren.  

### <a name="packages-and-programs"></a>Pakketten en programma's  
 Gebruik voor het maken van een pakket en programma voor een Linux- of UNIX-server de **Wizard pakket maken en programma** uit de Configuration Manager-console. De meest pakketten en programma-instellingen worden door de client voor Linux en UNIX ondersteund. Diverse instellingen worden echter niet ondersteund. Als u een pakket en programma maakt en configureert, houdt u rekening met het volgende:  

-   De bestandstypen die worden ondersteund door de doelcomputers bevatten.  

-   Definieer de opdrachtregels die geschikt voor gebruik op de doelcomputer zijn.  

-   Houd er rekening mee dat de instellingen die interacties uitvoeren met gebruikers niet worden ondersteund.  

De volgende tabel bevat de eigenschappen voor pakketten en programma's die niet worden ondersteund:  

|Pakket- en programma-eigenschap|Gedrag|Meer informatie|  
|----------------------------------|--------------|----------------------|  
|Instellingen van pakketshare:<br /><br /> -Alle opties|Er is een fout gegenereerd en de software-installatie mislukt|De client biedt geen ondersteuning voor deze configuratie. De client moet in plaats hiervan de software downloaden met behulp van HTTP of HTTPS en vervolgens de opdrachtregel vanuit de lokale cache uitvoeren.|  
|Instellingen van pakketupdate:<br /><br /> -Gebruikers ontkoppelt van distributiepunten|Instellingen worden genegeerd|De client biedt geen ondersteuning voor deze configuratie.|  
|Implementatie-instellingen van besturingssysteem:<br /><br /> -Alle opties|Instellingen worden genegeerd|De client biedt geen ondersteuning voor deze configuratie.|  
|Rapportage:<br /><br /> -Gebruik pakketeigenschappen voor status-MIF-koppeling<br /><br /> -Deze velden voor status-MIF-koppeling gebruiken|Instellingen worden genegeerd|Het gebruik van status-MIF-bestanden wordt niet door de client ondersteund.|  
|**Uitvoeren**:<br /><br /> -Alle opties|Instellingen worden genegeerd|De client voert altijd pakketten uit zonder gebruikersinterface.<br /><br /> De client negeert alle configuratie-opties voor het uitvoeren.|  
|Na het uitvoeren:<br /><br />-Start de computer opnieuw configuration Manager<br /><br /> -Programma bepaalt opnieuw opstarten<br /><br /> -Configuration Manager zich de gebruiker afmeldt|Er is een fout gegenereerd en de software-installatie mislukt|Het systeem start opnieuw op en gebruikerspecifieke instellingen worden niet ondersteund.<br /><br /> Als een andere instelling dan de instelling **Geen actie vereist** in gebruik is, wordt er door de client een fout gegeneerd en wordt de software-installatie voortgezet, maar geen actie ondernomen.|  
|Het programma kan worden uitgevoerd:<br /><br /> -Alleen als een gebruiker is aangemeld|Er is een fout gegenereerd en de software-installatie mislukt|Gebruikersspecifieke instellingen worden niet ondersteund.<br /><br /> Als deze optie geconfigureerd is, wordt er door de client een fout gegeneerd en mislukt de software-installatie.<br /><br /> Andere opties worden genegeerd en de software-installatie wordt voortgezet.|  
|Uitvoermodus:<br /><br /> -Uitvoeren met gebruikersrechten|Instellingen worden genegeerd|Gebruikersspecifieke instellingen worden niet ondersteund.<br /><br /> De client ondersteunt echter de configuratie uitvoeren met beheerdersrechten.<br /><br /> Wanneer u opgeeft **uitvoeren met beheerdersrechten**, Configuration Manager-client zijn hoofdreferenties.<br /><br /> Deze instelling genereert geen fout of logboekvermelding. De software-installatie mislukt echter als de client een fout op wanneer de vereiste configuratie van genereert **programma kan worden uitgevoerd** = **alleen wanneer een gebruiker is aangemeld**.|  
|Gebruikers toestaan om te zien en gebruiken met de programma-installatie|Instellingen worden genegeerd|Gebruikersspecifieke instellingen worden niet ondersteund.<br /><br /> Deze configuratie wordt genegeerd en de software-installatie wordt voortgezet.|  
|Stationsmodus:<br /><br /> -Alle opties|Instellingen worden genegeerd|Deze instelling wordt niet ondersteund want de inhoud wordt altijd naar de client gedownload en lokaal uitgevoerd.|  
|Eerst een ander programma uitvoeren|Er is een fout gegenereerd en de software-installatie mislukt|Recursieve programma-installatie wordt niet ondersteund.<br /><br /> Als een programma geconfigureerd is om eerst een ander programma uit te voeren, mislukt de software-installatie en wordt de andere programma-installatie niet gestart.|  
|Wanneer dit programma wordt toegewezen aan een computer:<br /><br /> -Eenmaal uitvoeren voor elke gebruiker die zich aanmeldt|Instellingen worden genegeerd|Gebruikersspecifieke instellingen worden niet ondersteund.<br /><br /> De client ondersteunt echter de configuratie met één keer voor de computer.<br /><br /> Deze instelling genereert geen fout of logboekvermelding omdat een fout en logboekvermelding al werden gemaakt voor de vereiste configuratie van **Het programma kan worden uitgevoerd** = **Alleen als er een gebruiker is aangemeld**-client voor Linux en UNIX ondersteund.|  
|Programmakennisgevingen onderdrukken|Instellingen worden genegeerd|Een gebruikersinterface wordt niet door de client geïmplementeerd.<br /><br /> Als deze configuratie is geselecteerd, wordt dit genegeerd en wordt de software-installatie voortgezet.|  
|Dit programma op computers waarop dit wordt geïmplementeerd uitschakelen|Instellingen worden genegeerd|Deze instelling wordt niet ondersteund en heeft geen invloed op de software-installatie.|  
|Toestaan dat dit programma wordt geïnstalleerd door de takenreeks pakket installeren zonder te worden geïmplementeerd||Takenreeksen worden niet door de client ondersteund.<br /><br /> Deze instelling wordt niet ondersteund en heeft geen invloed op de software-installatie.|  
|Windows Installer:<br /><br /> -Alle opties|Instellingen worden genegeerd|Windows Installer-bestanden of instellingen worden niet door de client ondersteund.|  
|Onderhoudsmodus OpsMgr:<br /><br /> -Alle opties|Instellingen worden genegeerd|De client biedt geen ondersteuning voor deze configuratie.|  

### <a name="deploy-software-to-a-linux-or-unix-server"></a>Software implementeren naar een Linux- of UNIX-server
 Om software te implementeren naar een Linux- of UNIX-server met behulp van een pakket en programma, kunt u de **Wizard Software implementeren** uit de Configuration Manager-console. De meeste implementatie-instellingen worden ondersteund door de client voor Linux en UNIX. Diverse instellingen worden echter niet ondersteund. Wanneer u software implementeert, het volgende overwegen:  

-   U moet het pakket voorzien van minstens één distributiepunt dat is gekoppeld aan een grensgroep die is geconfigureerd voor locatie van inhoud.  

-   De client voor Linux en UNIX die deze implementatie ontvangt moet toegang kunnen krijgen tot dit distributiepunt vanaf zijn netwerklocatie.  

-   De client voor Linux en UNIX downloadt het pakket van het distributiepunt en voert het programma uit op de lokale computer.  

-   De client voor Linux en UNIX kan geen pakketten downloaden van gedeelde mappen. Deze downloadt pakketten van IIS-ingeschakelde distributiepunten die ondersteuning bieden voor HTTP of HTTPS.  

 De volgende tabel somt eigenschappen voor implementaties op die niet worden ondersteund:  

|Implementatie-eigenschap|Gedrag|Meer informatie|  
|-------------------------|--------------|----------------------|  
|Implementatie-instellingen – doel:<br /><br /> -Beschikbaar<br /><br /> -Vereist|Instellingen worden genegeerd|Gebruikersspecifieke instellingen worden niet ondersteund.<br /><br /> De instelling **Vereist**wordt niettemin door de client ondersteund. Dit dwingt de geplande installatietijd af maar er wordt geen handmatige installatie ondersteund die voor dit geplande tijdstip zou vallen.|  
|Ontwaakpakketten verzenden|Instellingen worden genegeerd|De client biedt geen ondersteuning voor deze configuratie.|  
|Toewijzingsplanning:<br /><br /> -aanmelding<br /><br /> -en afmelden|Er is een fout gegenereerd en de software-installatie mislukt|Gebruikersspecifieke instellingen worden niet ondersteund.<br /><br /> De instelling **Zo snel mogelijk**wordt niettemin door de client ondersteund.|  
|Instellingen voor meldingen:<br /><br /> -Gebruikers het programma onafhankelijk van toewijzingen uit te voeren|Instellingen worden genegeerd|Een gebruikersinterface wordt niet door de client geïmplementeerd.|  
|Als de geplande toegewezen tijd bereikt wordt, toestaan dat de volgende activiteiten worden uitgevoerd buiten het onderhoudsvenster:<br /><br /> -Systeem opnieuw opstarten (indien nodig om de installatie te voltooien)|Er wordt een fout gegenereerd|Het opnieuw opstarten van het systeem wordt niet door de client ondersteund.|  
|Implementatieoptie voor netwerken voor snelle (LAN-) netwerken:<br /><br /> -Programma uitvoeren vanaf distributiepunt|Er is een fout gegenereerd en de software-installatie mislukt|De software kan niet door de client worden uitgevoerd vanaf het distributiepunt en in plaats hiervan moet het programma worden gedownload voordat het kan worden uitgevoerd.|  
|Implementatieoptie voor een langzame of onbetrouwbare netwerkgrens of een terugvalbronlocatie voor inhoud:<br /><br /> -Clients inhoud te delen met andere clients in hetzelfde subnet toestaan|Instellingen worden genegeerd|Gedeelde inhoud tussen peers wordt niet door de client ondersteund.|  

 Zie voor meer informatie over Inhoudslocatie [inhoud en infrastructuur voor System Center Configuration Manager beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 Zie voor meer informatie over het maken van een implementatie [toepassingen implementeren](../../apps/deploy-use/deploy-applications.md).  

##  <a name="manage-network-bandwidth-for-software-downloads-from-distribution-points"></a>Netwerkbandbreedte beheren voor softwaredownloads van distributiepunten  
 De client voor Linux en UNIX ondersteunt netwerkbandbreedteregelingen wanneer deze software van een distributiepunt wordt gedownload.  

 De client gebruikt de Background Intelligent Transfer (BITS)-instellingen die u als clientinstellingen in Configuration Manager configureert, maar implementeert geen BITS. De client controleert in de plaats daarvoor de HTTP-aanvraag chunkgrootte en de inter-chunk vertraging voor de softwaredownload om het gebruik van de netwerkbandbreedte te bewerken.  

 U kunt de clientinstellingen voor **Background Intelligent Transfer** configureren en vervolgens de instellingen op de clientcomputer toepassen om een client te configureren om netwerkbandbreedteregelingen te gebruiken. Om bandbreedteregelingen te gebruiken, de client moet clientinstellingen ontvangen voor **Background Intelligent Transfer** met de volgende instellingen geconfigureerd als **Ja**:  

-   **Beperk de maximale netwerkbandbreedte voor BITS-overdrachten op de achtergrond**  

 De volgende configuraties voor de Background Intelligent Transfer worden door de client ondersteund:  

    -   **Begintijd beperkingsvenster**  

    -   **Eindtijd beperkingsvenster**  

    -   **Maximale overdrachtssnelheid tijdens het beperkingsvenster (Kbps)**  

    -   **Maximale overdrachtssnelheid buiten het beperkingsvenster (Kbps)**  

De volgende configuratie voor Background Intelligent Transfer wordt niet ondersteund en wordt genegeerd door de client voor Linux en UNIX:  

-   **BITS-downloads buiten het beperkingsvenster toestaan**  

 Als het downloaden van software naar de client van een distributiepunt wordt onderbroken, wordt in de client voor Linux en UNIX de download niet hervatten. In plaats daarvan wordt het downloaden van het volledige softwarepakket gestart.  

##  <a name="configure-operations-for-software-deployments"></a>Bewerkingen voor software-implementaties configureren  
 Op dezelfde manier naar de Windows-client detecteert Configuration Manager-client voor Linux en UNIX nieuwe software-implementaties bij het vragen naar en naar nieuw beleid zoekt. De frequentie waarmee de client zoekt naar nieuw beleid is afhankelijk van de clientinstellingen. U kunt onderhoudsvensters configureren om te controleren wanneer software-implementaties plaatsvinden.  

 U kunt software-implementaties configureren naar Linux- en UNIX-servers met behulp van pakketeigenschappen, programma-eigenschappen en implementatie-eigenschappen.  

 Wanneer de clients beleid voor een implementatie ontvangt, wordt een statusbericht verzonden. Deze eveneens verzonden statusberichten wanneer deze wordt gestart met de installatie van software en wanneer de installatie is voltooid of mislukt.  

 Programma's voor software-implementaties worden uitgevoerd met de waarop de Configuration Manager-client voor Linux en UNIX wordt uitgevoerd met hoofdreferenties. De afsluitcode van de programma-opdracht wordt gebruikt om slagen of mislukken te bepalen. Een afsluitcode 0 (nul) wordt beschouwd als geslaagd. Bovendien worden de **stdout** (standaarduitvoerstroom) en **stderr** (standaardfoutstroom) gekopieerd naar het logbestand wanneer het logboekniveau ingesteld wordt op INFO of TRACE.  

> [!TIP]  
>  Als de software die u wilt implementeren zich bevindt op een Network File System (NFS)-share waartoe de Linux- of UNIX-server toegang heeft, hebt u geen distributiepunt nodig om het pakket te downloaden. Als u in plaats hiervan het pakket maakt, select u het selectievakje voor **Dit pakket bevat bronbestanden**niet. Als u het programma configureert, geeft u de geschikte opdrachtregel op voor rechtstreekse toegang van het pakket tot het NFS-koppelpunt.  
