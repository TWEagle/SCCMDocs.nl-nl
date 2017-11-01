---
title: App-V virtuele toepassingen implementeren
titleSuffix: Configuration Manager
description: Zie welke overwegingen u moet rekening account wanneer u maken en implementeren van virtuele toepassingen.
ms.custom: na
ms.date: 02/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddcad9f2-a542-4079-83ca-007d7cb44995
caps.latest.revision: "11"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: bf324f458c37fa137e24179eb4455fcbe75c855d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="deploy-app-v-virtual-applications-with-system-center-configuration-manager"></a>App-V virtuele toepassingen met System Center Configuration Manager implementeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u Configuration Manager gebruiken voor het beheren van virtuele toepassingen, krijgt u de volgende voordelen:  

-   Één beheerinfrastructuur  

-   Schaalbaarheid, implementatie en inhoudsdistributie functies, zoals verzamelingen en gebruikersaffiniteit apparaat  

-   Geavanceerde beheerfuncties  

-   Implementatie van besturingssystemen, software en hardware-inventaris, softwarelicentiecontrole en asset intelligence om virtuele toepassingen te ondersteunen  

Zie voor meer informatie over het maken en sequentiëren van toepassingen met Microsoft Application Virtualization (App-V) [Application Virtualization](https://technet.microsoft.com/library/cc843848.aspx) in de TechNet-bibliotheek.  

Naast de andere System Center Configuration Manager-vereisten en procedures voor het maken van een toepassing, u moet rekening houden met de volgende overwegingen wanneer u maken en implementeren van virtuele toepassingen:

-   Voor het implementeren van virtuele toepassingen naar computers, moet u de Configuration Manager-client en de App-V-Client op uw computers geïnstalleerd hebben. Clientapparaten kunnen desktop- en draagbare computers, en VDI-clients (Virtual Desktop Infrastructure) zijn. De Configuration Manager en App-V-Client software werken samen om te leveren, zoeken en openen van de virtuele-toepassingspakketten. Configuration Manager-client beheert de levering van virtuele toepassingspakketten naar de App-V-Client. De App-V-client voert de virtuele toepassing op de client uit.  

-   U moet voor het implementeren van een virtuele toepassing eerst de virtuele toepassing maken met App-V Application Virtualization Sequencer. De sequencer controleert het installatie- en configuratieproces voor een toepassing en registreert de informatie die nodig is voor het uitvoeren van de toepassing in een virtuele omgeving. U kunt de sequencer ook gebruiken om in te stellen die bestanden en configuraties op alle gebruikers toepassen en welke configuraties gebruikers kunnen aanpassen.  

-   Wanneer u een toepassing sequentieert, moet u het pakket opslaan naar een locatie die Configuration Manager hiertoe toegang heeft. U kunt vervolgens een toepassingsimplementatie maken die deze virtuele toepassing bevat.  

-   Configuration Manager biedt geen ondersteuning voor het gebruik van de gedeelde alleen-lezen cachefunctie van App-V.  

-   Configuration Manager ondersteunt de gedeelde inhoud Store-functie in App-V 5.  

-   Wanneer u een implementatietype voor een virtuele toepassing maakt, maakt Configuration Manager het implementatietype met behulp van de inhoud van het manifestbestand van de toepassing. Dit is een XML-bestand met informatie over de virtuele toepassing. Configuration Manager maakt daarnaast vereisten voor het implementatietype op basis van de inhoud van het App-V OSD-bestand met informatie over de ondersteunde besturingssystemen voor de virtuele toepassing.  

-   Clientcomputers moeten voor het implementeren van virtuele toepassingen in Configuration Manager hebben ten minste de App-V 4.6 SP1 of een latere versie van de client is geïnstalleerd.  

-   Voordat u virtuele toepassingen implementeren kunt, moet u de App-V-Client bijwerken met de hotfix beschreven in het Knowledge Base-artikel [2645225](https://support.microsoft.com/kb/2645225).  

-   Wanneer u verbindingsgroepen in App-V 5.0 gebruikt, kunnen uw geïmplementeerde virtuele toepassingen hetzelfde bestandssysteem en register op clientcomputers delen. In tegenstelling tot standaard virtuele toepassingen kunnen deze toepassingen gegevens met elkaar delen. Verbindingsgroepen behouden bovendien gebruikersinstellingen voor de toepassingen die ze bevatten. App-V virtuele omgevingen in Configuration Manager worden gebruikt voor het instellen van verbindingsgroepen op clientcomputers. Virtuele omgevingen worden op clientcomputers gemaakt of gewijzigd wanneer de toepassing wordt geïnstalleerd of wanneer clients vervolgens hun geïnstalleerde toepassingen evalueren. U kunt prioriteiten aanbrengen in deze toepassingen, zodat de hoogste prioriteit prevaleert wanneer meerdere toepassingen proberen om het bestandssysteem of een registerwaarde te wijzigen. Zie voor meer informatie [maken van App-V virtuele omgevingen](../../apps/deploy-use/create-app-v-virtual-environments.md).  

##  <a name="supported-app-v-versions"></a>Ondersteunde App-V-versies  
 Configuration Manager ondersteunt de volgende versies van App-V:  

-   **App-V 4.6**: Voor het gebruik van virtuele toepassingen in Configuration Manager, moeten de clientcomputers de App-V 4.6 SP1, App-V 4.6 SP2 of App-V 4.6 SP3-client geïnstalleerd hebben.  

     Voordat u virtuele toepassingen implementeren kunt, moet u de App-V 4.6 SP1-client ook bijwerken met de hotfix die wordt beschreven in het Knowledge Base-artikel [2645225](http://go.microsoft.com/fwlink/p/?LinkId=237322).  

-   **App-V 5, App-V 5.0 SP1, App-V 5.0 SP2, App-V 5.0 SP3 en App-V 5.1**: Voor App-V 5.0 SP2 moet u installeren [hotfixpakket 5](https://support.microsoft.com/en-us/kb/2963211) of App-V 5.0 SP3 gebruiken.  
-   **App-V 5.2**: Dit is ingebouwd in Windows 10 Enterprise (Verjaardag Update en hoger).

Zie de volgende onderwerpen voor meer informatie over App-V in Windows 10:

- [Wat is er nieuw in App-V](https://technet.microsoft.com/itpro/windows/manage/appv-about-appv)
- [Aan de slag met App-V voor Windows 10](https://technet.microsoft.com/itpro/windows/manage/appv-getting-started)
- [Bijwerken naar App-V voor Windows 10 van een bestaande installatie](https://technet.microsoft.com/itpro/windows/manage/appv-upgrading-to-app-v-for-windows-10-from-an-existing-installation)

##  <a name="steps-to-manage-app-v-virtual-applications"></a>Stappen voor het beheren van virtuele toepassingen van App-V  
 App-V virtuele toepassingen beheert, de volgende stappen uit:  

1.   **Reeks**: Sequentiëren is het proces van het converteren van een toepassing in een virtuele toepassing met behulp van de App-V-sequencer.

2.   **Maak**: Gebruik de Wizard implementatietype maken de gesequentieerde toepassing importeren in een Configuration Manager-implementatietype dat u vervolgens aan een toepassing toevoegen kunt. U kunt ook virtuele omgevingen maken die meerdere virtuele toepassingen toestaan om instellingen te delen.

3.   **Distribueren**: Distributie is het proces van beschikbaar maken van App-V-toepassingen op de Configuration Manager-distributiepunten.

4.   **Implementeer**: Implementatie is het proces van beschikbaar maken van de toepassing op clientcomputers. Dit heet streaming in een volledige App-V-infrastructuur.  

##  <a name="configuration-manager-virtual-application-delivery-methods"></a>Leveringsmethoden van virtuele toepassing Configuration Manager  
Configuration Manager ondersteunt twee methoden voor het leveren van virtuele toepassingen aan clients: streaming en lokale levering (downloaden en uitvoeren).

Wanneer u welke leveringsmethode beslist bent te gebruiken, vergelijkt u de verminderde benodigde schijfruimte voor de levering van streaming tegen de gegarandeerde beschikbaarheid van App-V-toepassingen in de lokale levering. Lokale levering vereist meer schijfruimte; deze optie kan echter nuttiger zijn voor streaminglevering om gebruikers vanuit eender welke locatie toegang te laten hebben tot de toepassing.  

###  <a name="streaming-delivery"></a>Levering via streaming
Wanneer u Configuration Manager gebruikt voor het beheren van de App-V-Client, ondersteunt dit het streamen van virtuele toepassingen via HTTP of HTTPS vanaf een distributiepunt. Streaming via HTTP of HTTPS is standaard ingeschakeld en is ingesteld in het dialoogvenster voor eigenschappen van het distributiepunt. Wanneer u een virtuele toepassing naar clientcomputers implementeert en een gebruiker de virtuele toepassing uitvoert, contact op met de Configuration Manager-client een beheerpunt om te bepalen welk distributiepunt te gebruiken. Vervolgens wordt de toepassing gestreamd vanaf het distributiepunt.  

Gebruik de informatie in deze tabel om te bepalen of de beste leveringsmethode voor u levering via streaming is:

|Voordelen|Nadelen|  
|----------------|-------------------|  
|Deze methode gebruikt standaard netwerkprotocollen om pakketinhoud te streamen vanaf distributiepunten.<br /><br /> Programmasnelkoppelingen voor virtuele toepassingen activeren een verbinding naar het distributiepunt, zodat de levering van de virtuele toepassing op aanvraag gebeurt.<br /><br /> Deze methode werkt goed voor clients met verbindingen met hoge bandbreedte naar de distributiepunten.<br /><br /> Bijgewerkte virtuele toepassingen die over het hele bedrijf zijn geïmplementeerd, zijn beschikbaar wanneer clients beleid ontvangen dat hen informeert dat de huidige versie wordt vervangen; vervolgens downloaden ze alleen de wijzigingen ten opzichte van de vorige versie.<br /><br /> Toegangsmachtigingen worden gedefinieerd aan het distributiepunt om gebruikers te verhinderen om niet-toegestane toepassingen of pakketten te openen.|Virtuele toepassingen worden niet gestreamd totdat de gebruiker de toepassing voor de eerste keer uitvoert. In dit scenario is het mogelijk dat een gebruiker programmasnelkoppelingen ontvangt voor virtuele toepassingen en vervolgens de verbinding met het netwerk verbreekt voordat de virtuele toepassingen voor de eerste keer zijn uitgevoerd. Als de gebruiker probeert uit te voeren van de virtuele toepassing terwijl de client offline is, wordt de gebruiker krijgt een foutmelding en de virtuele toepassing kan niet worden uitgevoerd omdat een distributiepunt van Configuration Manager is niet beschikbaar is om de toepassing te streamen. De toepassing zal niet beschikbaar zijn totdat de gebruiker opnieuw verbinding maakt met het netwerk en de toepassing uitvoert.<br /><br /> U kunt dit vermijden door de lokale leveringsmethode te gebruiken voor het leveren van virtuele toepassingen aan clients. U kunt ook het clientbeheer op internet voor levering via streaming inschakelen.|  

###  <a name="local-delivery-download-and-execute"></a>Lokale levering (downloaden en uitvoeren)  
Wanneer u de lokale leveringsmethode gebruikt, downloadt de Configuration Manager-client eerst het volledige virtuele toepassingspakket in de Configuration Manager-clientcache. De Configuration Manager instrueert vervolgens de App-V-Client om de toepassing uit de Configuration Manager-cache in de App-V-cache te streamen. Als u een virtuele toepassing naar clientcomputers implementeert en de inhoud niet in de App-V-cache is, wordt de App-V-Client de toepassingsinhoud vanuit de Configuration Manager-clientcache streams in de App-V-cache en vervolgens de toepassing wordt uitgevoerd. Nadat de toepassing wordt uitgevoerd, kunt u instellen dat de Configuration Manager-client te verwijderen van oudere versies van het pakket op de volgende verwijderingscyclus of ze ook behouden in Configuration Manager-clientcache.  

Gebruik de informatie in deze tabel om te bepalen of de lokale levering de beste leveringsmethode voor u is:   

|Voordelen|Nadelen|  
|----------------|-------------------|  
|De standaard distributiepuntfunctie wordt gebruikt om het pakket te downloaden door gebruik te maken van BITS (Background Intelligent Transfer Service).<br /><br /> Inhoud van de virtuele toepassing pakket zijn lokaal aan de client geleverd. Dit betekent dat gebruikers ze uitvoeren kunnen wanneer hun computer niet is verbonden met het netwerk.<br /><br /> Deze methode is geschikt voor trage of onbetrouwbare netwerkverbindingen en voor computers die alleen sporadisch verbinding maken met het netwerk.<br /><br /> Configuration Manager gebruikt Remote Differential Compression (RDC) aan clients alleen de bytes te verzenden binnen de bestanden die zijn gewijzigd wanneer de inhoud van het virtuele toepassingspakket wordt bijgewerkt. Configuration Manager-client gebruikt RDC om een nieuwe versie van een virtueel toepassingspakket op basis van de huidige versie van het pakket en eventuele wijzigingen die zijn verzonden naar de client samen te stellen.<br /><br /> Deze methode toepassingstolerantie voor mobiele gebruikers of gebruikers zonder netwerkverbinding. Beheerders kunnen kiezen om vast te leggen van het pakket in de Configuration Manager-cache na de levering als de virtuele toepassing werd geïmplementeerd met een installatiebewerking. Het pakket in de Configuration Manager-clientcache fungeert als een lokale, betrouwbare streamingbron van waar de App-V-Client het pakket in zijn cachegeheugen kan laden.|Schijfruimte die gelijk is aan maximaal twee keer de grootte van het virtuele toepassingspakket is vereist op de client wanneer de virtuele toepassing in de Configuration Manager-cache wordt bewaard.|  

###  <a name="deployment-from-an-image"></a>Implementatie van een installatiekopie

U kunt virtuele toepassingen ook vooraf installeren op een computer en vervolgens een installatiekopie maken van die computer voor implementatie naar andere computers. Maar als het virtuele toepassingspakket is gemaakt op een andere site, de replicatie binaire verschillen niet worden gebruikt om updates te downloaden tot de toepassing. Deze optie kan nuttig zijn in een Virtual Desktop Infrastructure waarbij u wilt dat toepassingen onmiddellijk beschikbaar zijn in plaats van gedownload te moeten worden nadat de gebruiker zich aanmeldt.    

##  <a name="migrating-from-an-app-v-infrastructure-to-a-configuration-manager-and-app-v-infrastructure"></a>Migreren van een App-V-infrastructuur naar een Configuration Manager en App-V-infrastructuur  
Gebruik de volgende tabel voor hulp bij het plannen van een migratie van een bestaande App-V-infrastructuur naar virtueel Toepassingsbeheer met Configuration Manager.  

|Stap|Meer informatie|  
|----------|----------------------|  
|Onderzoek uw huidige virtuele toepassingen en kies de toepassingen die u wilt migreren naar Configuration Manager-infrastructuur.|Geen aanvullende informatie.|  
|Beoordeel de gebruikers en apparaten waarnaar de virtuele toepassingen zullen worden geïmplementeerd.|Configuration Manager-verzamelingen groeperen van de gebruikers en apparaten die u wilt implementeren van virtuele toepassingen maken. Zie [inleiding op verzamelingen](/sccm/core/clients/manage/collections/introduction-to-collections).|  
|Migreer App-V 5-verbindingsgroepen naar virtuele omgevingen van Configuration Manager.|Zie de [migreren van App-V 5-verbindingsgroepen naar virtuele omgevingen van Configuration Manager](/sccm/apps/get-started/deploying-app-v-virtual-applications#migrate-app-v-5-connection-groups-to-configuration-manager-virtual-environments) in dit onderwerp.|  
|Onderzoek of een van uw virtuele toepassingen beschikbaar als volledige toepassingen in uw Configuration Manager-infrastructuur zijn.|Voor eenvoudiger beheer kunt u de virtuele toepassing toevoegen als een nieuw implementatietype naar de bestaande volledige toepassing. Zie [toepassingen maken](../../apps/deploy-use/create-applications.md).|  
|Maken van toepassingen om uw bestaande App-V-pakketten te vervangen.|Zie [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management) en [toepassingen maken](../../apps/deploy-use/create-applications.md).|  
|Configuration Manager begint met het beheren van virtuele toepassingen op een client na de eerste implementatie van een virtuele toepassing. Hierna moet Configuration Manager alle App-V-toepassingen op de computer beheren.|Geen aanvullende informatie.|  
|Distribueer de inhoud naar de geschikte distributiepunten om lokale levering van toepassingen in te schakelen.|Zie [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|De toepassing implementeren naar Configuration Manager-clients.<br /><br /> Als de App-V-toepassing is gemaakt met een eerdere versie van de sequencer die geen manifestbestand in XML maakt, kunt u deze openen en opslaan in een nieuwere versie van de sequencer het bestand te maken. Dit bestand is vereist voor het implementeren van virtuele toepassingen met Configuration Manager.<br /><br /> App-V ondersteunt de virtuele-toepassingspakketten die zijn gemaakt met de SoftGrid 4.1 SP1 of 4.2 versies van de sequencer.<br /><br /> Als de toepassingen voorheen lokaal zijn geïnstalleerd, moet u deze verwijderen voordat u een virtuele versie ervan implementeert.|Zie [toepassingen implementeren](../../apps/deploy-use/deploy-applications.md).|  
|System Center Configuration Manager biedt geen ondersteuning voor pakketten en programma's die virtuele toepassingen bevatten. Wanneer u van Configuration Manager 2007 naar System Center Configuration Manager migreert, zet Configuration Manager om deze pakketten in toepassingen.<br /><br /> Configuration Manager 2007-aankondigingen worden geconverteerd in de volgende implementatietypen:<br /><br /> -App-V-pakketten migreren zonder aankondiging:  Eén implementatietype dat gebruikmaakt van de standaard implementatietype-instellingen.<br /><br /> -App-V-pakketten migreren met één aankondiging: Eén implementatietype dat dezelfde instellingen als gebruikt de <br />                Configuration Manager 2007-aankondiging.<br /><br /> -App-V-pakketten migreren met meerdere aankondigingen: Een implementatietype voor elke <br />                Configuration Manager 2007-aankondiging dat de instellingen voor die aankondiging gebruikt.|Zie [Planning voor de migratie van Configuration Manager-objecten naar System Center Configuration Manager](../../core/migration/planning-for-the-migration-of-objects.md).|  

##  <a name="migrating-app-v-5-connection-groups-to-configuration-manager-virtual-environments"></a>Migreren App-V 5-verbindingsgroepen naar virtuele omgevingen van Configuration Manager  
App-V virtuele omgevingen in Configuration Manager kunnen virtuele toepassingen die u hebt geïmplementeerd om hetzelfde bestandssysteem en register op clientcomputers delen. Dit betekent dat deze toepassingen, in tegenstelling tot virtuele standaardtoepassingen, gegevens met elkaar kunnen delen. Virtuele omgevingen worden op clientcomputers gemaakt of gewijzigd wanneer de toepassing wordt geïnstalleerd of wanneer clients vervolgens hun geïnstalleerde toepassingen evalueren. Virtuele omgevingen zijn vergelijkbaar met verbindingsgroepen in zelfstandige App-V 5.  

Wanneer u verbindingsgroepen van zelfstandige App-V 5 naar virtuele omgevingen van Configuration Manager migreert, moet u ervoor zorgen dat Configuration Manager de verbindingsgroepen die al bestaan op clientcomputers correct worden beheerd en dat de gebruikersomgeving binnen die verbindingsgroepen wordt behouden.  

App-V 5-verbindingsgroepen te converteren naar virtuele omgevingen van Configuration Manager:  

1.  Configuration Manager toepassingen maken voor alle toepassingen die beschikbaar waren in App-V.  

2.  Implementeer de toepassingen naar gebruikers op apparaten met een implementatiedoel van **Vereist**. Implementaties naar gebruikers moeten worden geïmplementeerd op dezelfde gebruikers die de toepassing in App-V gebruikten. Implementaties naar computers moeten worden geïmplementeerd naar dezelfde computers die de toepassing in App-V hadden.  

3.  Nadat de implementatie is voltooid, maakt u virtuele omgevingen die overeenkomen met de verbindingsgroepen die zijn gepubliceerd in zelfstandige App-V. De virtuele omgeving moet dezelfde pakketten (met name implementatietypen App-V 5) in dezelfde volgorde hebben.  

Zie voor meer informatie over het maken van een virtuele omgeving van App-V [het maken van virtuele omgevingen van App-V](../../apps/deploy-use/create-app-v-virtual-environments.md).  

U kunt ook alle verbindingsgroepen uit de App-V-Client verwijderen voordat u begint met het implementeren van toepassingen met Configuration Manager. Maar alle instellingen die gebruikers in App-V-verbindingsgroepen mogelijk hebben opgeslagen gaan verloren.  

##  <a name="dynamic-suite-composition-in-app-v-46"></a>Dynamic Suite Composition in App-V 4.6  
Dynamic Suite Composition is een functie waarmee u een virtueel toepassingspakket te definiëren als met een afhankelijkheid van een ander virtueel toepassingspakket. Wanneer de toepassing wordt uitgevoerd, host de App-V-client het primaire pakket en het afhankelijke pakket in dezelfde virtuele omgeving van de toepassing.  

U kunt deze functie gebruiken met Configuration Manager, worden beide pakketten geïmplementeerd en geregistreerd met de App-V-Client. Om ervoor te zorgen dat de inhoud van afhankelijke pakket lokaal wordt gehost op de clientcomputer, instellen van de implementatie van de toepassing voor lokale levering (downloaden en uitvoeren).  

Zie de App-V-documentatie voor meer informatie over App-V Dynamic Suite Composition.  

##  <a name="converting-app-v-46-applications-to-app-v-5-applications"></a>Converteren van App-V 4.6-toepassingen naar App-V 5-toepassingen  
De indeling van het toepassingspakket voor App-V 5 is gewijzigd ten opzicht van App-V 4.6. Toepassingen die zijn gesequentieerd met App-V 4.6 worden niet meer ondersteund. Maar App-V 5 heeft een conversieprogramma voor pakketten die u gebruiken kunt om toepassingen te converteren. Zie de [App-V 5-documentatie](http://technet.microsoft.com/library/jj713472.aspx)voor meer informatie.  

U kunt met behulp van de volgende stappen App-V 4.6-toepassingen converteren naar App-V 5-toepassingen:  

1.  Converteren of resequence van de App-V 4.6-pakketten in de App-V 5-indeling.  

2.  De App-V-5-client implementeren op computers in uw hiërarchie.  

3.  Maak nieuwe toepassingen die implementatietypen bevatten voor uw App-V 5-toepassingen en maak vervangingsregels om de App-V 4.6-toepassingen te vervangen.  

4.  Maak zo nodig virtuele omgevingen.  

5.  Implementeer de nieuwe App-V-5 toepassingen op computers.  

##  <a name="user-and-deployment-configuration-files"></a>Configuratiebestanden voor gebruikers en implementatie  
Gebruikers- en configuratiebestanden van de implementatie bevatten instellingen die bepalen het gedrag van een toepassing. U kunt deze bestanden toepassingsinstellingen wijzigen zonder de toepassing resequencing gebruiken.  

Een typische 5 App-V-toepassing bevat mogelijk de volgende bestanden:  

-   Een toepassingspakketbestand (appv)  

-   Een configuratiebestand voor gebruikers  

-   Een configuratiebestand voor implementatie  

Het configuratiebestand van de gebruiker heeft de instellingen die alleen van toepassing op de aangemelde gebruiker. U kunt bijvoorbeeld de configuratiebestanden voor het wijzigen van de informatie over de snelkoppeling van de toepassing die wordt geïmplementeerd voor gebruikers bewerken. U kunt ook een Configuration Manager-toepassing maken met meerdere implementatietypen. Elk implementatietype kan een andere gebruikersconfiguratiebestand bevatten en regels voor vereisten gebruiken om ervoor te zorgen dat deze wordt geïnstalleerd voor de betreffende gebruikers.  

Het configuratiebestand voor de implementatie bevat instellingen die van toepassing op de computer, zoals registerinstellingen. Het bestand kan tevens gebruikersinstellingen worden toegepast op alle gebruikers hebben.  

Als u implementeren van virtuele App-V 5-toepassingen met Configuration Manager wilt, moeten alle drie bestanden aanwezig zijn in dezelfde map als u het App-V 5-implementatietype maakt. Als er meerdere bestanden in de map gebruik Configuration Manager van de meest recente.  

Zie de [App-V 5-documentatie](http://technet.microsoft.com/library/jj713466.aspx)voor meer informatie.  

##  <a name="app-v-local-interaction"></a>App-V lokale interactie  
In enkele implementatiescenario's, toepassingen lokaal worden geïnstalleerd op clientcomputers en andere toepassingen geïmplementeerd als virtuele toepassingen op dezelfde clientcomputer. Standaard kunnen lokaal geïnstalleerde toepassingen gevirtualiseerde toepassingen niet zien of er rechtstreeks mee communiceren. Dit is het beoogde gedrag van de toepassingsisolatie waarin App-V biedt. Lokale interactie is een functie van de App-V-Client die u voor elke toepassing zodat lokaal geïnstalleerde toepassingen die worden uitgevoerd op een clientcomputer om te zien en communiceren met gevirtualiseerde toepassingen kunt inschakelen. Configuration Manager en App-V bieden volledige ondersteuning voor lokale interactie.  

Zie de documentatie van uw App-V voor meer informatie over de App-V lokale interactie-functie.  

##  <a name="app-v-5-shared-content-store"></a>App-V 5 Shared inhoud Store  
Configuration Manager ondersteunt de functie App-V 5 Shared Content Store. Zie [Planning for the App-V 5.0 Shared Content Store (SCS)](http://technet.microsoft.com/library/jj713431.aspx)voor meer informatie.  

##  <a name="monitoring-virtual-applications"></a>Virtuele toepassingen controleren  

### <a name="virtual-application-reports"></a>Rapporten van virtuele toepassingen  
U kunt de volgende rapporten App-V in uw Configuration Manager-omgeving controleren:  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|Resultaten virtuele omgeving App-V|Geeft informatie weer over een geselecteerde virtuele omgeving die zich in een opgegeven status voor een geselecteerde verzameling (uitsluitend App-V 5).|  
|Resultaten virtuele omgeving App-V voor activa|Geeft informatie weer over een geselecteerde virtuele omgeving voor een bepaalde asset en implementatietypen voor de geselecteerde virtuele omgeving (uitsluitend App-V 5).|  
|Status virtuele omgeving App-V|Wordt compatibiliteitsinformatie weergegeven voor een geselecteerde virtuele omgeving voor een geselecteerde verzameling. De **bewaard** kolom in dit rapport bevat de activa waarin een virtuele omgeving die eerder is ingesteld niet meer van toepassing is, maar wel worden bewaard om gebruikersinstellingen in toepassingen die worden uitgevoerd in de virtuele omgeving (uitsluitend App-V 5).|  
|Computers met een specifieke virtuele toepassing|Geeft een samenvatting weer van computers die de opgegeven App-V-snelkoppeling hebben dat de Application Virtualization Management Sequencer gemaakt (uitsluitend App-V 4.6).|  
|Computers met een specifiek virtuele-toepassingspakket|Geeft een lijst weer van computers die de opgegeven App-V-toepassingspakket geïnstalleerd hebben (uitsluitend App-V 4.6).|  
|Alle exemplaren van virtuele-toepassingspakketten tellen|Geeft een telling van alle gedetecteerd App-V-toepassingspakketten (uitsluitend App-V 4.6).|  
|Alle exemplaren van virtuele toepassingen tellen|Geeft een telling van alle gedetecteerd App-V-toepassingen (uitsluitend App-V 4.6).|  

### <a name="log-files"></a>Logboekbestanden  
Configuration Manager registreert informatie over implementaties van virtuele toepassingen in logboekbestanden. Zie voor informatie over het log-die virtuele toepassingen en Configuration Manager application management-gebruik bestanden, [logbestanden in System Center Configuration Manager](../../core/plan-design/hierarchy/log-files.md).  

Voor Windows Vista, Windows 7 en Windows 8, kunt u Logboeken vinden voor de App-V-client in C:\ProgramData\Microsoft\Application virtualisatie-Client.  
