---
title: Softwareupdates plannen | Microsoft Docs
description: Een plan voor de software-updatepuntinfrastructuur is essentieel voordat u software-updates in een productieomgeving System Center Configuration Manager gebruiken.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: d071b0ec-e070-40a9-b7d4-564b92a5465f
ms.openlocfilehash: 8b739a01a6bb5cacf0f7109e2e6fa3b31dd666d3
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="plan-for-software-updates-in-system-center-configuration-manager"></a>Software-updates plannen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u software-updates in een productieomgeving System Center Configuration Manager gebruiken, is het belangrijk dat u hebt het planningsproces doorlopen. Met een goed plan voor de software-updatepuntinfrastructuur is essentieel voor de implementatie van een geslaagde software-updates.

## <a name="capacity-planning-recommendations-for-software-updates"></a>Aanbevelingen voor capaciteitsplanning voor software-updates  
 U kunt de volgende aanbevelingen gebruiken als basis om u te helpen bij het bepalen van de informatie voor de capaciteitsplanning van de software-updates die geschikt is voor uw organisatie. De werkelijke capaciteitsvereisten kunnen afwijken van de aanbevelingen die worden vermeld in dit onderwerp. Dit is afhankelijk van de volgende criteria: uw specifieke netwerkomgeving, de hardware die u gebruikt om het sitesysteem van het software-updatepunt te hosten, het aantal clients dat wordt geïnstalleerd en de sitesysteemrollen die op de server zijn geïnstalleerd.  

###  <a name="BKMK_SUMCapacity"></a> Capaciteitsplanning voor het software-updatepunt  
 Het aantal ondersteunde clients is afhankelijk van de versie van Windows Server Update Services (WSUS) dat wordt uitgevoerd op het software-updatepunt; het is ook afhankelijk van of de sitesysteemrol van het software-updatepunt naast een andere sitesysteemrol bestaat:  

-   Het software-updatepunt kan tot 25.000 clients ondersteunen wanneer WSUS wordt uitgevoerd op de computer van het software-updatepunt en als het software-updatepunt naast een andere sitesysteemrol bestaat.  

-   De software-updatepunt kan maximaal 150.000 clients ondersteunen wanneer de externe computer voldoet aan de vereisten voor WSUS, WSUS wordt gebruikt met Configuration Manager en u het volgende configureren:

    IIS-toepassingsgroepen:
    - Vergroot de WsusPool-wachtrijlengte tot 2.000
    - Verhoog de limiet Privégeheugenlimiet x4 of stel deze in op 0 (onbeperkt)      

    Zie voor meer informatie over hardwarevereisten voor de software-updatepunt [aanbevolen hardwarevereisten voor sitesystemen](/sccm/core/plan-design/configs/recommended-hardware#a-namebkmkscalesiesystemsa-site-systems).

-   Standaard biedt Configuration Manager geen ondersteuning voor configureren van het software-updatepunten als NLB-clusters. Voorafgaand aan de Configuration Manager versie 1702 kunt u de Configuration Manager SDK maximaal vier software-updatepunten op een NLB-cluster configureren. Echter vanaf Configuration Manager versie 1702, software-updatepunten worden niet ondersteund als NLB-clusters en upgrades naar Configuration Manager versie 1702 wordt geblokkeerd als deze configuratie wordt gedetecteerd.

### <a name="capacity-planning-for-software-updates-objects"></a>Capaciteitsplanning voor software-updateobjecten  
 Gebruik de volgende capaciteitsinformatie om te plannen voor software-updateobjecten  

-   **Limiet van 1000 software-updates in een implementatie**  

     U moet het aantal software-updates tot duizend beperken voor elke implementatie van software-updates. Als u een automatische implementatieregel maakt, dient u een criterium op te geven dat het aantal geretourneerde software-updates beperkt. De automatische implementatieregel mislukt wanneer het criterium dat u opgeeft meer dan 1000 software-updates retourneert. U kunt controleren dat de status van de regel voor automatische implementatie van de **regels voor automatische implementatie** knooppunt in de Configuration Manager-console. Selecteer maximaal 1000 te implementeren updates wanneer u software-updates handmatig implementeert.  

     U moet ook beperken het aantal software-updates en 1000 in een configuratiebasislijn. Zie voor meer informatie [configuratiebasislijnen maken](../../compliance/deploy-use/create-configuration-baselines.md).

##  <a name="BKMK_SUPInfrastructure"></a> De software-updatepuntinfrastructuur bepalen  
 De centrale beheersite en alle onderliggende primaire sites moeten een software-updatepunt hebben waar u software-updates gaat implementeren. Als u de software-updatepuntinfrastructuur plant, moet u de volgende afhankelijkheden bepalen:
 - waar u de software-updatepunt voor de site installeert
 - welke sites een software-updatepunt dat communicatie van clients op Internet aanvaardt is vereist
 - Hiermee wordt aangegeven of moet u een software-updatepunt op een secundaire site.

Gebruik de volgende secties om de infrastructuur van het software-updatepunt te bepalen.  

> [!IMPORTANT]  
>  Zie voor meer informatie over de interne en externe afhankelijkheden die vereist voor software-updates zijn [vereisten voor software-updates](prerequisites-for-software-updates.md).  

 U kunt meerdere software-updatepunten op een primaire site van Configuration Manager toevoegen. De mogelijkheid om meerdere software-updatepunten te hebben op een site biedt fouttolerantie zonder dat de complexiteit van NLB nodig is. De failover die u ontvangt met meerdere software-updatepunten is niet zo robuust als een NLB voor zuivere taakverdeling, maar is daarentegen ontwikkeld voor fouttolerantie. Het failoverontwerp van het software-updatepunt is ook anders dan het zuivere randomisatiemodel dat wordt gebruikt in het ontwerp voor beheerpunten. Anders dan in het ontwerp van beheerpunten, zijn er client- en netwerkprestatiekosten in de software-updatepunten die zijn gekoppeld aan het overschakelen naar een nieuw software-updatepunt. Wanneer de client overschakelt naar een nieuwe WSUS-server voor software-updates, is het resultaat een stijging van de catalogusgrootte en van de gekoppelde vereisten van clients en netwerkprestaties. Daarom bewaart de client affiniteit met het meest recente software-updatepunt waarnaar het met succes scande.  

 Het eerste software-updatepunt dat u installeert op een primaire site is de synchronisatiebron voor alle bijkomende software-updatepunten die u toevoegt aan de primaire site. Nadat u uw software-updatepunten hebt toegevoegd en het synchroniseren van software-updates hebt geïnitieerd, kunt u de status van de software-updatepunten en de synchronisatiebron bekijken in het knooppunt **Synchronisatiestatus van software-updatepunten** in de werkruimte **Bewaking** .  

 Als een software-updatepunt niet kan worden uitgevoerd, en als dat software-updatepunt is geconfigureerd als de synchronisatiebron voor de andere software-updatepunten op die site, dient u het niet uitgevoerde software-upatepunt handmatig te verwijderen en een nieuw software-updatepunt te selecteren als synchronisatiebron. Voor meer informatie over het verwijderen van een software-update wordt gehost, Zie [verwijderen van de sitesysteemrol van software-update-punt](../get-started/remove-a-software-update-point.md).  

###  <a name="BKMK_SUPList"></a> Lijst met software-updatepunten  
 Configuration Manager biedt u de client een lijst met software-update in de volgende scenario's: wanneer een nieuwe client het beleid voor software-updates inschakelen ontvangt, of wanneer een client geen contact krijgt met de software-updatepunt en moet overschakelen naar een ander software-updatepunt. De client selecteert willekeurig een software-updatepunt uit de lijst en bepaalt de volgorde van de software-updatepunten die zich in dezelfde forest bevinden. Configuration Manager biedt-clients met een andere lijst afhankelijk van het type client.  

-   **Clients op intranet**: Ontvangen een lijst met software-updatepunten die u configureren kunt om verbindingen alleen via het intranet te staan, of een lijst met software-updatepunten die clientverbindingen via Internet en intranet toestaan.  

-   **Clients op Internet**: Ontvangen een lijst met software-updatepunten die u configureert als u wilt toestaan verbindingen alleen via Internet, of een lijst met software-updatepunten die clientverbindingen via Internet en intranet toestaan.  

###  <a name="BKMK_SUPSwitching"></a> Overschakeling tussen software-updatepunten  
> [!NOTE]
> Vanaf versie 1702, clients gebruiken grensgroepen om te zoeken naar een nieuw software-updatepunt en terugval en zoeken naar een nieuwe software-updatepunt als de huidige bewerking is niet langer toegankelijk. U kunt afzonderlijke software-updatepunten toevoegen aan verschillende grensgroepen om te bepalen welke servers een client kunt vinden. Zie voor meer informatie [software-updatepunten](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) in de [grensgroepen configureren](/sccm/core/servers/deploy/configure/boundary-groups) onderwerp.

Als u meerdere software-updatepunten op een site hebt en er één niet kan worden uitgevoerd of niet beschikbaar wordt, zullen clients verbinding maken met een ander software-updatepunt en blijven scannen naar de meest recente software-updates. Als een client eerst wordt toegewezen aan een software-updatepunt, zal deze hieraan toegewezen blijven totdat het scannen naar software-updates op dat software-updatepunt niet kan worden uitgevoerd.  

De scan naar software-updates kan mislukken met een aantal verschillende retry- en non-retry-foutcodes. Als de scan niet kan worden uitgevoerd en er een retry-foutcode wordt gegeven, start de client een nieuwe poging om te scannen naar software-updates op het software-updatepunt. De omstandigheden die leiden tot een retry-foutcode, zijn doorgaans te wijten aan het niet beschikbaar zijn van de WSUS-server of aan een tijdelijke overbelasting ervan. De client gebruikt het volgende proces wanneer de scan naar software-updates niet kan worden uitgevoerd:  

1.  De client scant naar software-updates op het geplande tijdstip, of wanneer de client wordt gestart via het clientconfiguratiescherm of via SDK. Als de scan niet kan worden uitgevoerd, wacht de client 30 minuten om de scan opnieuw uit te voeren; hetzelfde software-updatepunt wordt gebruikt.‎  

2.  De client probeert de scan minstens vier keer uit te voeren, telkens met een interval van 30 minuten. Na de vierde fout, en nadat er nog twee minuten zijn verstreken, gaat de client verder met het volgende software-updatepunt in de lijst met software-updatepunten.  

3.  De client doorloopt hetzelfde proces op het nieuwe software-updatepunt. Na een geslaagde scan zal de client blijven verbinding maken met de nieuwe software-updatepunt.

 De volgende lijst geeft u bijkomende informatie die u kunt overwegen voor scenario's met nieuwe pogingen en overschakelingen van software-updatepunten:  

-   Als de verbinding van een client van het bedrijfsintranet wordt verbroken en het scannen naar software-updates niet kan worden uitgevoerd, zal deze niet overschakelen naar een ander software-updatepunt. Dit is een verwachte fout, omdat de client het bedrijfsnetwerk of het software-updatepunt dat verbinding via het internet toestaat, niet kan bereiken. Configuration Manager-client bepaalt de beschikbaarheid van het intranet software-updatepunt.  

-   Als clientbeheer op internet is ingeschakeld en er meerdere software-updatepunten zijn geconfigureerd om communicatie van clients op het internet te accepteren, zal het overschakelingsproces het standaardproces voor nieuwe pogingen volgen dat wordt beschreven in het voorgaande scenario.  

-   Als het scanproces is gestart en de client werd uitgeschakeld voordat de scan kon worden voltooid, wordt dit niet geregistreerd als een scanfout en geldt dit dus niet als een van de vier pogingen.  

Wanneer Configuration Manager met de volgende foutcodes van Windows Update Agent ontvangt, wordt deze client probeer opnieuw verbinding te hebben:  

2149842970, 2147954429, 2149859352, 2149859362, 2149859338, 2149859344, 2147954430, 2147747475, 2149842974, 2149859342, 2149859372, 2149859341, 2149904388, 2149859371, 2149859367, 2149859366, 2149859364, 2149859363, 2149859361, 2149859360, 2149859359, 2149859358, 2149859357, 2149859356, 2149859354, 2149859353, 2149859350, 2149859349, 2149859340, 2149859339, 2149859332, 2149859333, 2149859334, 2149859337, 2149859336, 2149859335

Als u de betekenis van een foutcode opzoeken, moet u de decimale foutcode converteren naar een hexadecimaal getal en zoek vervolgens naar de hexadecimale waarde op een site, zoals de [Windows Update Agent - fout Codes Wiki](https://social.technet.microsoft.com/wiki/contents/articles/15260.windows-update-agent-error-codes.aspx).


###  <a name="BKMK_ManuallySwitchSUPs"></a>Clients handmatig overschakelen naar een nieuwe software-updatepunt
Configuration Manager versie 1606 was de eerste versie waarin u de optie kon inschakelen dat Configuration Manager-clients kunnen overstappen op een nieuw software-updatepunt als er problemen zijn met het actieve software-updatepunt. Met deze optie worden alleen wijzigingen doorgevoerd als een client meerdere software-updatepunten ontvangt van een beheerpunt.

> [!IMPORTANT]    
> Wanneer u een nieuwe server-apparaten, met de apparaten terugval zoeken naar die nieuwe server. Daarom Controleer uw configuratie van grensgroepen en zorg ervoor dat uw software-updatepunten in de juiste grensgroepen voordat u deze wijziging. Zie voor meer informatie [Software-updatepunten](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points).
>
> Het overschakelen naar een nieuw software-updatepunt, wordt er aanvullend netwerkverkeer gegenereerd. De hoeveelheid verkeer, is afhankelijk van uw WSUS-configuratie-instellingen (updateclassificaties, producten, of de software-updatepunten een WSUS-database, enz delen.). Als u overschakelen van meerdere apparaten wilt, kunt u in dat geval tijdens onderhoudsvensters naar reduceert de gevolgen voor uw netwerk tijdens de synchronisatie met de nieuwe software-updatepuntserver.

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>De optie inschakelen om van software-updatepunt te wisselen  
Schakel deze optie in op een verzameling apparaten of op een reeks geselecteerde apparaten. Nadat deze optie is ingeschakeld, zoeken de clients naar een ander software-updatepunt bij de volgende scan.

1.  Klik in de Configuration Manager-console op **Activa en naleving > Overzicht > Apparaatverzamelingen**.  

2.  Klik op het tabblad **Start** in de groep **Verzameling** op **Clientmelding**en klik vervolgens op **Overschakelen naar het volgende software-updatepunt**.  


###  <a name="BKMK_SUP_CrossForest"></a> Software-updatepunten in een niet-vertrouwd forest  
 U kunt een of meer software-updatepunten maken op een site om clients te ondersteunen in een niet-vertrouwd forest. U kunt een software-updatepunt toevoegen aan een ander forest; hiervoor moet u eerst een WSUS-server in het forest installeren en configureren. Start vervolgens de wizard voor het toevoegen van een Configuration Manager-siteserver met de sitesysteemrol van software-update-punt. Configureer de volgende instellingen in de wizard om verbinding te maken met WSUS in het niet-vertrouwde forest:  

-   Geef een sitesysteeminstallatieaccount op dat toegang heeft tot de WSUS-server in het forest.  

-   Specificeer het WSUS-serververbindingsaccount om te gebruiken voor de verbinding met de WSUS-server.  

 U kunt bijvoorbeeld primaire site hebben in forest A met twee software-updatepunten (SUP01 en SUP02).‎ Voor de primaire site hebt u twee software-updatepunten (SUP03 en SUP04) in forest B. Wanneer het overschakelen zich in dit voorbeeld voordoet, krijgen de software-updatepunten uit hetzelfde forest als de client voorrang.  

###  <a name="BKMK_WSUSSyncSource"></a> Een bestaande WSUS-server gebruiken als synchronisatiebron op de site op het hoogste niveau  
 Doorgaans wordt de site op het hoogste niveau van uw hiërarchie geconfigureerd om de metagegevens van software-updates te synchroniseren met Microsoft Update. Wanneer het beveiligingsbeleid van uw bedrijf geen toegang tot het Internet vanaf de site op het hoogste niveau toestaat heeft, kunt u de synchronisatiebron configureren voor de site op het hoogste niveau een bestaande WSUS-server die zich niet in uw hiërarchie van Configuration Manager gebruiken. U kunt bijvoorbeeld een WSUS-server geïnstalleerd hebben in uw perimeternetwerk die internettoegang heeft terwijl de site op het hoogste niveau dat niet heeft. U kunt de WSUS-server in het perimeternetwerk configureren als uw synchronisatiebron voor de metagegevens van software-updates. U moet ervoor zorgen dat de WSUS-server in de DMZ software-updates die voldoen aan de criteria die u nodig hebt in uw Configuration Manager-hiërarchie synchroniseert. Anders is het mogelijk dat de site op het hoogste niveau de software-updates die u verwacht, niet kan synchroniseren. Bij het installeren van het software-updatepunt dient u een WSUS-server te configureren die toegang heeft tot de WSUS-server in het perimeternetwerk en te bevestigen dat de firewall verkeer toestaat voor de overeenkomstige poorten. Raadpleeg voor meer informatie de [poorten die worden gebruikt door het software-updatepunt voor de synchronisatiebron](../../core/plan-design/hierarchy/ports.md#BKMK_PortsSUP-WSUS).  

###  <a name="BKMK_NLBSUPSP1"></a> Software-updatepunt geconfigureerd om een NLB te gebruiken  
 Door tussen software-updatepunten te schakelen, wordt waarschijnlijk aan uw fouttolerantiebehoeften voldaan. Standaard biedt Configuration Manager geen ondersteuning voor configureren van het software-updatepunten als NLB-clusters. Voorafgaand aan de Configuration Manager versie 1702 kunt u de Configuration Manager SDK maximaal vier software-updatepunten op een NLB-cluster configureren. Echter vanaf Configuration Manager versie 1702, software-updatepunten worden niet ondersteund als NLB-clusters en upgrades naar Configuration Manager versie 1702 wordt geblokkeerd als deze configuratie wordt gedetecteerd. Zie voor meer informatie over de cmdlet Set-CMSoftwareUpdatePoint PowerShell de [Set-CMSoftwareUpdatePoint](http://go.microsoft.com/fwlink/?LinkId=276834).

###  <a name="BKMK_SUPSecSite"></a> Software-updatepunt op een secundaire Site  
 Het software-updatepunt is optioneel op een secundaire site. Wanneer u een software-updatepunt op een secundaire site installeert, wordt de WSUS-database geconfigureerd als een replica van het standaard software-updatepunt op de bovenliggende primaire site. U kunt slechts één software-updatepunt op een secundaire site installeren. De apparaten die aan een secundaire site zijn toegewezen, zijn geconfigureerd om een software-updatepunt te gebruiken op de bovenliggende site wanneer een software-updatepunt niet is geïnstalleerd op de secundaire site. U installeert een software-updatepunt gewoonlijk op een secundaire site wanneer er beperkte netwerkbandbreedte is tussen de apparaten die aan de secundaire site zijn toegewezen en de software-updatepunten op de bovenliggende primaire site, of wanneer het software-updatepunt de capaciteitlimiet benadert. Nadat een software-updatepunt met succes is geïnstalleerd en geconfigureerd op de secundaire site, wordt een beleid voor de gehele site bijgewerkt voor clientcomputers die zijn toegewezen aan de site, en zullen ze het nieuwe software-updatepunt beginnen te gebruiken.  

##  <a name="BKMK_SUPInstallation"></a>Plan voor de installatie van Software-updatepunt  
 Voordat u een sitesysteemrol van software-update-punt in Configuration Manager maakt, zijn er verschillende vereisten die u, afhankelijk van uw Configuration Manager-infrastructuur overwegen moet. Wanneer u het software-updatepunt configureert om te communiceren met behulp van SSL, is deze sectie in het bijzonder belangrijk omdat u extra stappen moet nemen opdat de software-upatepunten in uw hiërarchie goed zouden werken. Deze sectie geeft informatie over de stappen die u moet nemen om de installatie van een software-updatepunt met succes te plannen en voor te bereiden.  

###  <a name="BKMK_SUPSystemRequirements"></a> Vereisten voor het software-updatepunt  
 De sitesysteemrol van software-update-punt moet worden geïnstalleerd op een sitesysteem dat voldoet aan de minimale vereisten voor WSUS en de ondersteunde configuraties voor Configuration Manager-sitesystemen.  

-   Zie voor meer informatie over de minimale vereisten voor de WSUS-serverrol in Windows Server 2012, [aandachtspunten en systeemvereisten bekijken](https://technet.microsoft.com/library/hh852344.aspx#BKMK_1.1) in de Documentatiebibliotheek van Windows Server 2012.  

-   Zie voor meer informatie over de ondersteunde configuraties voor Configuration Manager-sitesystemen [Site en site-systeemvereisten](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

###  <a name="BKMK_PlanningForWSUS"></a> Planning voor de installatie van WSUS  

Software-updates vereisen dat een ondersteunde versie van WSUS is geïnstalleerd op alle sitesysteemservers die u configureert voor de sitesysteemrol van software-updatepunt. Wanneer u het software-updatepunt niet op de siteserver installeert, moet u daarnaast de WSUS-beheerconsole op de siteservercomputer installeren, als deze nog niet is geïnstalleerd. Zo kan de siteserver communiceren met WSUS dat op het software-updatepunt wordt uitgevoerd.  

 Wanneer u WSUS op Windows Server 2012 gebruikt, moet u extra machtigingen om toe te staan configureren **WSUS Configuration Manager** controleert in Configuration Manager verbinding maken met de WSUS om peridieke uitvoeren. Kies een van de volgende opties om de machtigingen te configureren:  

-   Voeg de **SYSTEM** -account toe aan de **WSUS-administrators** -groep  

-   Voeg de **NT AUTHORITY\SYSTEM** -account toe als een gebruiker voor de WSUS-database (SUSDB) en configureer een minimum van het webService-databaserollidmaatschap  

 Zie [Install the WSUS Server Role](http://go.microsoft.com/fwlink/p/?LinkId=272355) (De WSUS-serverrol installeren) in de Windows Server 2012-documentatiebibliotheek voor meer informatie over de installatie van WSUS op Windows Server 2012.  

 Wanneer u meer dan één software-updatepunt op een primaire site installeert, gebruikt u dezelfde WSUS-database voor elk software-updatepunt in hetzelfde Active Directory-forest. Als u dezelfde database deelt, vermindert het significant de impact op de prestatie van de client en het netwerk die u kunt ervaren wanneer clients overschakelen naar een nieuw software-updatepunt, maar elimineert het deze niet volledig. Een deltascan vindt nog steeds plaats wanneer een client overschakelt naar een nieuw software-updatepunt dat een database deelt met het oudere software-updatepunt, maar de scan is veel kleiner dan het normaal zou zijn als de WSUS-server zijn eigen database had.  

####  <a name="BKMK_CustomWebSite"></a> WSUS configureren voor het gebruik van een aangepaste website  
 Wanneer u WSUS installeert, hebt u de optie de bestaande IIS Standaard website te gebruiken of een aangepaste WSUS-website te maken. Maak een aangepaste website voor WSUS, zodat de WSUS-services in een speciale virtuele website in plaats van dezelfde website die wordt gebruikt door de andere Configuration Manager-sitesystemen of andere toepassingen delen door IIS worden gehost. Dit geldt in het bijzonder wanneer u de sitesysteemrol van software-updatepunt op de siteserver installeert. Wanneer u WSUS in Windows Server 2012 of Windows Server 2016 uitvoert, is WSUS standaard geconfigureerd voor gebruik van poort 8530 voor HTTP en poort 8531 voor HTTPS. U moet deze poortinstellingen opgeven wanneer u het software-updatepunt op de site maakt.  

####  <a name="BKMK_WSUSInfrastructure"></a> Een bestaande WSUS-infrastructuur gebruiken  
 U kunt een WSUS-server die actief in uw omgeving was voordat u Configuration Manager hebt geïnstalleerd als een software-updatepunt selecteren. Wanneer het software-updatepunt is geconfigureerd, moet u de synchronisatie-instellingen opgeven. Configuration Manager maakt verbinding met de WSUS-server die wordt uitgevoerd op de softwareserver-updatepunt en configureert WSUS met dezelfde instellingen. Als u WSUS gesynchroniseerd voordat deze is geconfigureerd als een software-updatepunt met producten of classificaties die u niet hebt geconfigureerd als onderdeel van de synchronisatie-instellingen van software-update-punt, de software-updates metagegevens voor de producten en classificaties gesynchroniseerd voor alle metagegevens van software-updates in de WSUS-database ongeacht de synchronisatie-instellingen die u hebt geconfigureerd voor het software-updatepunt. Dit kan leiden tot onverwachte metegagevens van software-updates in de sitedatabase. U zult hetzelfde gedrag ervaren wanneer u producten of classificaties rechtstreeks in de WSUS-beheerconsole toevoegt en dan onmiddellijk synchroniatie een. Elk uur, standaard Configuration Manager maakt verbinding met WSUS op het software-updatepunt en stelt het instellingen die zijn aangepast buiten Configuration Manager opnieuw. De software-updates die niet voldoen aan de producten en classificaties die u opgeeft in de synchronisatie-instellingen, worden ingesteld op verlopen, en ze kunnen dan worden verwijderd uit de sitedatabase.

 Wanneer u een WSUS-server is geconfigureerd als een software-updatepunt, bent u niet meer kunnen gebruiken als een zelfstandige WSUS-server. Als u een afzonderlijke, zelfstandige WSUS-server is die niet wordt beheerd door Configuration Manager moet, moet u deze configureren op een andere server.

####  <a name="BKMK_WSUSAsReplica"></a> WSUS configureren als een replicaserver  
 Wanneer u een sitesysteemrol van software-upatepunt op een primaire siteserver maakt, kunt u geen WSUS-server gebruiken die als een replica is geconfigureerd. Wanneer de WSUS-server is geconfigureerd als een replica, Configuration Manager is mislukt voor het configureren van de WSUS-server en mislukt ook de WSUS-synchronisatie. Wanneer een software-updatepunt is gemaakt op een secundaire site, configureert Configuration Manager WSUS als een replicasever van de WSUS die wordt uitgevoerd op het software-updatepunt op de bovenliggende primaire site. Het eerste software-updatepunt dat u installeert op een primaire site wordt het standaardsoftware-updatepunt. Andere software-updatepunten op de site zijn geconfigureerd als replica's van het standaardsoftware-updatepunt.  

####  <a name="BKMK_WSUSandSSL"></a> Beslissen of WSUS moet worden geconfigureerd voor het gebruik van SSL  
 U kunt het SSL-protocol gebruiken om de WSUS te helpen beveiligen die op het software-updatepunt wordt uitgevoerd. WSUS gebruikt SSL om clientcomputers en WSUS-servers stroomafwaarts naar de WSUS-server te verifiëren. WSUS gebruikt ook SSL om de metagegevens van de software-update te versleutelen. Wanneer u ervoor kiest WSUS te beveiligen van SSL, moet u de WSUS-server voorbereiden voordat u het software-updatepunt installeert.  

 Wanneer u het software-updatepunt installeert en configureert, moet u de instelling **SSL-communicaties inschakelen voor de WSUS-Server** selecteren. Configuration Manager Configureer anders WSUS SSL niet te gebruiken. Wanneer u SSL voor WSUS inschakelt dat op een software-updatepunt wordt uitgevoerd, moet WSUS dat op het software-updatepunt van enige onderliggende sites, ook worden geconfigureerd om SSL te gebruiken.  

###  <a name="BKMK_ConfigureFirewalls"></a> Firewalls configureren  
 Software-updates op een centrale beheersite van Configuration Manager communiceren met de WSUS die wordt uitgevoerd op de software-updatepunt, dat op zijn beurt met de synchronisatiebron metagegevens communiceert voor het synchroniseren van software-updates. Software-updatepunten op een onderliggende site communiceren met het software-updatepunt op de bovenliggende site. Wanneer er meer dan één software-updatepunt op een primaire site is, moeten de extra software-updatepunten communiceren met het eerste software-updatepunt dat op de site is geïnstalleerd, dat het standaardsoftware-updatepunt is.  

 De firewall moet mogelijk worden geconfigureerd voor het accepteren van de HTTP of HTTPS-poorten die worden gebruikt door WSUS in de volgende scenario's: wanneer u een bedrijfsfirewall tussen de Configuration Manager software-updatepunt en Internet; Wanneer u hebt een software-updatepunt en de bijbehorende stroomopwaartse synchronisatiebron gebruikt; of wanneer u de extra software-updatepunten. De verbinding met Microsoft Update is altijd geconfigureerd om poort 80 te gebruiken voor HTTP en poort 443 voor HTTPS. U kunt een aangepaste poort gebruiken voor de verbinding van WSUS dat op het software-updatepunt wordt uitgevoerd op een onderliggende site met WSUS dat op het software-updatepunt wordt uitgevoerd op de bovenliggende site. Wanneer uw beveiligingsbeleid de verbinding niet toelaat, moet u de export- en importsynchronisatiemethode gebruiken. Zie de sectie [Synchronisatiebron](#BKMK_SyncSource) in dit onderwerp voor meer informatie. Zie voor meer informatie over de poorten die worden gebruikt door WSUS [Bepalen welke poortinstellingen worden gebruikt door WSUS in System Center Configuration Manager](../get-started/install-a-software-update-point.md#wsus-settings).  

#### <a name="restrict-access-to-specific-domains"></a>Toegang tot specifieke domeinen beperken  
 Als uw organisatie niet toelaat dat de poorten en protocollen open zijn voor alle adressen op de firewall tussen het actieve software-upatepunt en het internet, kunt u de toegang tot de volgende domeinen beperken zodat WSUS en Automatische Updates kunnen communiceren met Microsoft Update:  

-   http://windowsupdate.microsoft.com

-   http://*.windowsupdate.microsoft.com  

-   https://*.windowsupdate.microsoft.com  

-   http://*.update.microsoft.com  

-   https://*.update.microsoft.com  

-   http://*.windowsupdate.com  

-   http://download.windowsupdate.com  

-   http://download.microsoft.com  

-   http://*.download.windowsupdate.com  

-   http://test.stats.update.microsoft.com  

-   http://ntservicepack.microsoft.com  

 Mogelijk moet u de volgende adressen toevoegen aan de firewall tussen de twee sitesystemen in de volgende gevallen: als onderliggende sites een software-update-punt hebben of als er zich een extern actief internetsoftware-updatepunt op een site bevindt:  

 **Software-updatepunt op de onderliggende site**  

-   http://<*FQDN voor software-updatepunt op onderliggende site*>  

-   https://<*FQDN voor software-updatepunt op onderliggende site*>  

-   http://<*FQDN voor software-updatepunt op bovenliggende site*>  

-   https://<*FQDN voor software-updatepunt op bovenliggende site*>  

##  <a name="BKMK_SyncSettings"></a> Planning voor synchronisatie-instellingen  
 Synchronisatie van software-updates in Configuration Manager is het proces van het ophalen van metagegevens van de software-updates op basis van criteria die u configureert. De site op het hoogste niveau in uw hiërarchie, de centrale beheersite of zelfstandige primaire site synchroniseren software-updates van Microsoft Update. U hebt de optie voor het configureren van de software-updatepunt op de bovenste site om te synchroniseren met een bestaande WSUS-server, niet in de Configuration Manager-hiërarchie. De onderliggende primaire sites synchroniseren metagegevens van software-updates van het software-updatepunt op de centrale beheersite. Voordat u een software-updatepunt installeert en configureert, moet u deze sectie gebruiken om te plannen voor de synchronisatie-instellingen.  

###  <a name="BKMK_SyncSource"></a> Synchronisatiebron  
 De synchroniatiebroninstellingen voor het software-updatepunt specificeren de locatie voor waar het software-updatepunt metagegevens van software-updates ophaalt, en of de WSUS-rapporteringsgebeuertenissen zijn gemaakt tijdens het synchronisatieproces.  

-   **Synchronisatiebron:** De software-updatepunt op het hoogste niveau configureert de synchronisatiebron voor Microsoft Update standaard. U hebt de optie de site op het hoogste niveau met een bestaande WSUS-server te synchroniseren. Het software-updatepunt op een onderliggende primaire site configureert standaard de synchroniatiebron als het software-updatepunt aan de centrale beheersite.  

    > [!NOTE]  
    >  Het eerste software-updatepunt dat u installeert op een primaire site, dat het standaardsoftware-updatepunt is, synchroniseert met de centrale beheersite. Extra software-upatepunten aan de primaier site synchroniseren met het standaardsoftware-updatepunt aan de primaire site.  

     Wanneer een software-upatepunt niet is verbonden met Microsoft Update of met de updateserver stroomopwaarts, kunt u de synchronisatiebron configureren om niet te synchroniseren met een geconfigureerde synchronisatiebron, maar in plaats daarvan de export- en importfunctie van het WSUSUtil-hulpprogramma te gebruiken om software-updates te synchroniseren. Zie de sectie [Software-updates synchroniseren vanaf een niet-verbonden software-updatepunt](../get-started/synchronize-software-updates-disconnected.md) voor meer informatie.  

-   **WSUS-rapportagegebeurtenissen:** De Windows Update Agent op clientcomputers kan gebeurtenisberichten maken die worden gebruikt voor WSUS-rapportage. Deze gebeurtenissen worden niet gebruikt door software-update in Configuration Manager en daarom wordt de **geen WSUS-rapportagegebeurtenissen maken** optie is standaard geselecteerd. Wanneer deze gebeurtenissen niet worden gemaakt, is het enige ogenblik waarop de clientcomputer verbonden moet zijn met de WSUS-server, tijdens software-update-evaluatie en compatibiliteitsscans. Als deze gebeurtenissen nodig zijn voor rapportage buiten software-updates in Configuration Manager, moet u deze instelling om te maken van de WSUS-rapportagegebeurtenissen te wijzigen.  

###  <a name="BKMK_SyncSchedule"></a> Synchronisatieplanning  
 U kunt de synchronisatieplanning alleen configureren op het software-updatepunt op het hoogste niveau in de Configuration Manager-hiërarchie. Wanneer u de synchronisatieplanning configureert, synchroniseert het software-updatepunt met de synchronisatiebron op de datum en tijd die u hebt opgegeven. De aangepaste planning laat u toe software-updates te synchroniseren op een datum en tijd wanneer de aanvragen van de WSUS-server, siteserver en het netwerk laag zijn, zoals om 2.00 eenmaal per week. U kunt synchronisatie ook starten op het hoogste niveau met behulp van de **synchronisatie Software-Updates** actie van de **alle Software-Updates** of **Software-Updategroepen** knooppunt in de Configuration Manager-console.  

> [!TIP]  
>  Plan de synchronisatie van software-updates om uit te voeren met behulp van een tijdskader dat geschikt is voor uw omgeving. Een gebruikelijk scenario is het instellen van de planning voor de synchronisatie van software-updates om uit te voeren kort na de regelmatige vrijgave van de beveiligingsupdate van Microsoft op de tweede dinsdag van elke maand, die gewoonlijk Patch Dinsdag wordt genoemd. Een ander gebruikelijk scenario is het instellen van de planning voor de synchronisatie van software-updates om dagelijks uitgevoerd te worden wanneer u software-updates gebruikt om de Endpoint Protection-definitie en engine-updates te leveren.  

 Nadat het software-updatepunt de synchronisatie heeft voltooid, wordt er een synchronisatieaanvraag verzonden naar onderliggende sites. Als u extra software-updatepunten op een primaire site hebt, wordt er een synchronisatieaanvraag verzonden naar elk software-updatepunt. Het proces wordt herhaald op elke site in de hiërarchie.  

###  <a name="BKMK_UpdateClassifications"></a> Updateclassificaties  
 Elke software-update wordt gedefinieerd met een updateclassificatie die helpt de verschillende types updates te organiseren. Tijdens het synchronisatieproces worden de metagegevens van de software-updates voor de opgegeven classificaties gesynchroniseerd. Configuration Manager kunt u softwareupdates te synchroniseren met de volgende updateclassificaties:  

-   **Essentiële Updates:** Geeft een ruim vrijgegeven update voor een specifiek probleem die zijn gericht op een kritieke fout niet gerelateerd.  

-   **Definitie-Updates:** Hiermee geeft u een update aan voor antivirus- of andere definitiebestanden.  

-   **Functiepakketten:** Geeft nieuwe productfuncties die zijn gedistribueerd buiten een productrelease en functie die gewoonlijk zijn opgenomen in de volgende volledige productrelease aan.  

-   **Beveiligingsupdates:** Hiermee geeft u een grote schaal uitgebrachte update aan voor een productspecifiek en beveiligingsgerelateerd probleem.  

-   **Servicepacks:** Hiermee geeft u een volledige reeks van hotfixes die op een toepassing worden toegepast. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, software-updates, enzovoort.  

-   **Hulpprogramma's:** Hiermee geeft u een hulpprogramma of onderdeel dat u een of meer taken kunt voltooien.  

-   **Updatepakketten:** Hiermee geeft u een volledige reeks van hotfixes die samen zijn verpakt voor een gemakkelijke implementatie. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, enzovoort. Een updatepakket gaat in het algemeen over een specifiek gebied, zoals beveiliging of een productcomponent.  

-   **Updates:** Hiermee geeft u een update aan voor een toepassing of bestand dat momenteel is geïnstalleerd.  

 De updateclassificatie-instellingen worden alleen geconfigureerd op de site op het hoogste niveau. De updateclassificatie-instellingen worden niet geconfigureerd op het software-updatepunt op onderliggende sites, omdat de metagegegevens van software-updates worden gerepliceerd van de site op het hoogste niveau naar onderliggende primaire sites. Wanneer u de updateclassificaties selecteert, let er dan op dat hoe meer classificaties u selecteert, hoe langer het duurt om de metagegevens van de software-updates te synchroniseren.  

> [!WARNING]  
>  Het wordt aanbevolen alle classificaties te wissen voordat u software-updates voor het eerst synchroniseert. Na de initiële synchronisatie selecteert u de classificaties uit Eigenschappen van software-updatepuntcomponenten, en start u de synchronisatie vervolgens opnieuw.  

###  <a name="BKMK_UpdateProducts"></a> Producten  
 De metagegevens voor elke software-update definiëren een of meerdere producten waarvoor de update van toepassing is. Een product is een specifieke editie van een besturingssysteem of programma. Een voorbeeld van een product is Microsoft Windows Server 2008. Een productfamilie is het basisbesturingssysteem of de basistoepassing waarvan de afzonderlijke producten zijn afgeleid. Een voorbeeld van een productfamilie is Microsoft Windows, waarvan Windows Server 2008 een lid is. U kunt een productfamilie of individuele producten binnen een productfamilie opgeven.  

 Wanneer software-updates van toepassing op meerdere producten zijn, en ten minste één van de producten is geselecteerd voor synchronisatie, wordt alle producten weergegeven in de Configuration Manager-console zelfs als sommige producten niet werden geselecteerd. Als Windows Server 2012 bijvoorbeeld het enige besturingssysteem is waarop u zich hebt geabonneerd, en als een software-update van toepassing is op Windows Server 2012 en Windows Server 2012 Datacenter Edition, zullen beide producten in de sitedatabase zitten.  

 De productinstellingen worden alleen geconfigureerd op de site op het hoogste niveau. De productinstellingen worden niet geconfigureerd op het software-updatepunt op onderliggende sites, omdat de metagegegevens van software-updates worden gerepliceerd van de site op het hoogste niveau naar onderliggende primaire sites. Wanneer u producten selecteert, let er dan op dat hoe meer producten u selecteert, hoe langer het duurt om de metagegevens van de software-updates te synchroniseren.  

> [!IMPORTANT]  
>  Configuration Manager slaat een lijst van producten en productfamilies waaruit u kunt kiezen wanneer u de software-updatepunt voor het eerst installeert. Producten en productfamilies die zijn vrijgegeven nadat Configuration Manager is uitgebracht mogelijk niet beschikbaar om te selecteren tot u de synchronisatie van software-updates, die de lijst van beschikbare prdoucten en productfamilies waaruit u kunt updates voltooid. Het wordt aanbevolen alle producten te wissen voordat u software-updates voor het eerst synchroniseert. Na de initiële synchronisatie selecteert u de producten uit Eigenschappen van software-updatepuntcomponenten, en start u de synchronisatie vervolgens opnieuw.  

###  <a name="BKMK_SupersedenceRules"></a>Vervangingsregels  
 Een software-updat die een andere software-update vervangt, doet gewoonlijk een of meerdere van de volgende acties:  

-   Bevordert, verbetert of werkt de oplossing bij die werd geleverd door een of meerdere eerder vrijgegeven updates.  

-   Verbetert de efficiëntie van het bestandspakket van de vervangen update, dat geïnstalleerd is op clientcomputers als de installatie van de update is goedgekeurd. Bijvoorbeeld, de vervangen update kan bestanden bevatten die niet langer relevant zijn voor de fix of voor de besturingssystemen die door de nieuwe update ondersteund worden, dus die bestanden worden niet opgenomen in het vervangende bestandspakket van de update.  

-   Werkt nieuwere versies van het product bij. Met andere woorden, het werkt versies bij die niet langer toepasselijk zijn voor oudere versies of configuraties van een product. Updates kunnen ook andere updates vervangen als er wijzigingen zijn aangebracht om taalondersteuning uit te breiden. Bijvoorbeeld, een latere revisie van een productupdate voor Microsoft Office kan de ondersteuning voor een ouder besturingssysteem verwijderen, maar kan aanvullende ondersteuning voor nieuwe talen in de initiële update-release toevoegen.  

 In de eigenschappen voor het software-updatepunt kunt u opgeven dat de vervangen software-updates onmiddellijk verlopen zijn, zodat ze niet kunnen worden opgenomen in nieuwe implementaties en de bestaande implementaties worden gemarkeerd ter aanduiding dat ze één of meer verlopen software-updates bevatten. U kunt ook een periode opgeven waarna de vervangen software-updates verlopen, zodat u ze nog kunt blijven implementeren. Denk eens aan de volgende scenario's waarin u een vervangen software-update moet implementeren:  

-   Als een vervangende software-update alleen nieuwere versies van een besturingssysteem ondersteunt, en op een aantal van uw clientcomputers eerdere versies van dat besturingssysteem staan.  

-   Als een vervangende software-update een beperktere toepasbaarheid heeft dan de software-update die hij vervangt. Hierdoor zou de software-update voor sommige clientcomputers ongeschikt zijn.  

-   Als een vervangende software-update niet is goedgekeurd voor implementatie in uw productieomgeving.  

    > [!NOTE]  
    > Wanneer een vervangen software-update in Configuration Manager wordt ingesteld op **verlopen**, de update wordt niet ingesteld op **geweigerd** in WSUS. Echter, wanneer de WSUS-opschoontaak wordt uitgevoerd, de updates ingesteld op **verlopen** in Configuration Manager zijn ingesteld op de status van **geweigerd** op de WSUS-server en de Windows Update Agent op computers scant niet meer voor deze updates. Dit betekent dat clients blijven scannen naar een verlopen update totdat de taak opschonen wordt uitgevoerd. Zie voor meer informatie over de WSUS-opschoontaak [onderhoud voor Software-updates](/sccm/sum/deploy-use/software-updates-maintenance).

###  <a name="BKMK_UpdateLanguages"></a> Talen  
 De taalinstellingen voor het software-updatepunt stellen u in staat de talen te configureren waarvoor de overzichtsgegevens (metagegevens van software-updates) gesynchroniseerd zijn voor software-updates, alsook de software-updatebestandstalen die voor software-updates worden gedownload.  

#### <a name="software-update-file"></a>Software-updatebestand  
 De talen die u configureert voor de instelling **Software-updatebestand** in de eigenschappen voor het software-updatepunt, vormen de standaardset van talen die beschikbaar zijn wanneer u software-updates van een site downloadt. Telkens wanneer de software-updates worden gedownload of geïmplementeerd, kunt u de standaard geselecteerde talen wijzigen. Tijdens het downloadproces worden de software-updatebestanden voor de geconfigureerde talen gedownload naar de bronlocatie van het implementatiepakket, als de software-updatebestanden beschikbaar zijn in de geselecteerde taal. Vervolgens worden ze gekopieerd naar de inhoudsbibliotheek op de siteserver, en daarna worden ze gekopieerd naar de distributiepunten die voor het pakket geconfigureerd zijn.  

 De taalinstellingen van software-updatebestanden moeten geconfigureerd zijn met de talen die het meest in uw omgeving worden gebruikt. Bijvoorbeeld, als clientcomputers die aan de site zijn toegewezen voornamelijk het Engels en Japans gebruiken voor het besturingssysteem of toepassingen, en er heel weinig andere talen op de site worden gebruikt, selecteert u in de kolom **Software-updatebestand** Engels en Japans wanneer u de software-update downloadt of implementeert en wist u de andere talen. Dit zorgt ervoor dat u de standaardinstellingen kunt gebruiken op de pagina **Taalselectie** van de implementatie en dat u wizards kunt downloaden. Dit voorkomt ook dat er overbodige updatebestanden worden gedownload. Deze instelling is geconfigureerd op elk software-updatepunt in de Configuration Manager-hiërarchie.  

#### <a name="summary-details"></a>Overzichtsgegevens  
 Tijdens het synchronisatieproces wordt de informatie bij de overzichtsgegevens (metagegevens van software-updates) bijgewerkt voor software-updates in de talen die u opgeeft. De metagegevens omvatten de informatie over de software-update, zoals naam, omschrijving, producten die de update ondersteunt, updateclassificatie, artikel-id, download-URL, regels voor toepasselijkheid, enzovoorts.  

 De instellingen voor de overzichtsgegevens worden alleen geconfigureerd op de site op het hoogste niveau. De overzichtsgegevens worden niet geconfigureerd op het software-updatepunt op onderliggende sites omdat de metagegevens van software-updates vanaf de centrale beheersite tot aan deze sites gerepliceerd worden met behulp van bestandsgebaseerde replicatie. Wanneer u de talen voor de overzichtsgegevens selecteert, selecteert u alleen de talen die u in uw omgeving nodig hebt. Hoe meer talen u selecteert, hoe langer het duurt om de metagegevens van software-updates te synchroniseren. Configuration Manager geeft de metagegevens van software-updates weer in de landinstellingen van het besturingssysteem waarop de Configuration Manager-console wordt uitgevoerd. Als de gelokaliseerde eigenschappen voor de software-updates niet beschikbaar zijn in de landinstellingen van het besturingssysteem, worden de gegevens van de software-updates in het Engels weergegeven.  

> [!IMPORTANT]  
>  Het is belangrijk dat u alle van de overzichtsgegevens álle talen die u in uw Configuration Manager-hiërarchie moet selecteren. Wanneer het software-updatepunt op de site op het hoogste niveau gesynchroniseerd wordt met de synchronisatiebron, bepalen de geselecteerde overzichtsgegevenstalen welke metagegevens van software-updates er worden opgehaald. Als u de overzichtsgegevenstalen wijzigt nadat er ten minste eenmaal een synchronisatie is uitgevoerd, worden de metagegevens van software-updates opgehaald voor de gewijzigde overzichtsgegevenstalen De software-updates die reeds gesynchroniseerd zijn worden niet met nieuwe metagegevens voor de gewijzigde talen bijgewerkt, tenzij er een wijziging van de software-update plaatsvindt op de synchronisatiebron.  

##  <a name="BKMK_MaintenanceWindow"></a> Planning voor een onderhoudsvenster voor software-updates  
 U kunt een onderhoudsvenster toevoegen dat speciaal is ontworpen voor installatie van software-updates. Hierdoor kunt u een algemeen onderhoudsvenster configureren en een ander onderhoudsvenster voor software-updates. Wanneer u zowel een algemeen onderhoudsvenster als een onderhoudsvenster voor software-updates configureert, installeren clients software-updates alleen via het onderhoudsvenster voor software-updates. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

##  <a name="BKMK_RestartOptions"></a> Opties voor het opnieuw opstarten van Windows 10-clients na de installatie van een software-update
Wanneer een software-update waarvoor opnieuw opstarten wordt geïmplementeerd met behulp van Configuration Manager en geïnstalleerd op een computer opnieuw is gepland en een dialoogvenster voor opnieuw opstarten wordt weergegeven.

Met ingang van Configuration Manager versie 1606 is de optie **Bijwerken en opnieuw opstarten**en **Bijwerken en afsluiten** op computers met Windows 10 bij de opties voor energiebeheer in Windows beschikbaar, als opnieuw opstarten is gepland voor een software-update van Configuration Manager. Nadat u een van deze opties hebt gebruikt, wordt het dialoogvenster voor opnieuw opstarten niet weergegeven nadat de computer opnieuw wordt opgestart.

In eerdere versies van Configuration Manager, als opnieuw opstarten in behandeling is voor Windows 8 en hoger computers, en wanneer u afsluiten of opnieuw opstarten van de computer met behulp van de opties voor energiebeheer in Windows (in plaats van in het dialoogvenster voor opnieuw opstarten), blijft van het dialoogvenster opnieuw opstarten nadat de computer opnieuw wordt opgestart en de computer nog steeds op de geconfigureerde deadline opnieuw opstarten.

## <a name="next-steps"></a>Volgende stappen
Nadat u voor software-updates plant, gaat u naar [voorbereiden voor software-updates management](../get-started/prepare-for-software-updates-management.md).
