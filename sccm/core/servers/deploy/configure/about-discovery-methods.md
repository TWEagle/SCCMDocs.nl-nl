---
title: Detectiemethoden | Microsoft-documenten
ms.custom: na
ms.date: 2/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed931751-18f2-4230-a09e-a0a329fbfa1c
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 81d7516b814d2db74d4d857871071c8911755754
ms.openlocfilehash: 6e53f501281e31f2b7df54b9740eac970f108257
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="about-discovery-methods-for-system-center-configuration-manager"></a>Detectiemethoden voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager-detectiemethoden kunnen verschillende apparaten op het netwerk of de apparaten en gebruikers uit Active Directory vinden. Voor het efficiënt gebruik van een detectiemethode moet u de beschikbare configuraties en beperkingen begrijpen.  

##  <a name="bkmk_aboutForest"></a>Detectie van Active Directory-forests  
 **Configureerbare:** Ja  

 **Standaard is ingeschakeld:** Nee  

 **Accounts** kunt u deze methode worden uitgevoerd:  

-   **Detectieaccount Active Directory-Forest** (de gebruiker gedefinieerde)  

-   **Computeraccount** van de siteserver  

In tegenstelling tot andere detectiemethoden Active Directory detecteert Active Directory-Forestdetectie geen bronnen die u kunt beheren. In plaats daarvan detecteert deze methode netwerklocaties die zijn geconfigureerd in Active Directory en kunnen deze locaties converteren voor gebruik over de hele hiërarchie.  

Wanneer deze methode wordt uitgevoerd, wordt gezocht in de lokale Active Directory-forest, elk vertrouwd forest, en elke extra forest dat u configureert in de **Active Directory-Forests** knooppunt van de Configuration Manager-console.  

Gebruik Active Directory-Forest detectie:  

-   Active Directory-sites en -subnets detecteren en maak vervolgens Configuration Manager-grenzen op basis van deze netwerklocaties.  

-   Identificeer supernets die zijn toegewezen aan een Active Directory-site en elk supernet omzetten in een grens van IP-adresbereik.  

-   Publiceren naar Active Directory Domain Services (AD DS) in een forest als publiceren naar deze forest is ingeschakeld en de opgegeven Active Directory-Forestaccount machtigingen voor dat forest heeft.  

U kunt detectie van Active Directory-forests beheren in de Configuration Manager-console uit de volgende knooppunten onder **Hiërarchieconfiguratie** in de **beheer** werkruimte:  

-   **Detectiemethoden**: Hier kunt u detectie van Active Directory-Forest om uit te voeren op de site op het hoogste niveau van uw hiërarchie. U kunt ook een simpele planning detectie uit te voeren opgeven en configureren om automatisch grenzen te maken van de IP-subnetten en Active Directory-stes die ze detecteert. Detectie van Active Directory-Forest kan niet worden uitgevoerd op een onderliggende primaire site of op een secundaire site.  

-   **Active Directory-Forests**: Hier configureert u de bijkomende Active Directory-forests die u wilt detecteren, geeft de serviceaccount te gebruiken als de Active Directory-Forestaccount voor elke forest en configureert u het publiceren naar elke forest. Daarnaast kunt u het detectieproces bewaken en IP-subnetten en Active Directory-sites naar Configuration Manager toevoegen als grenzen en leden van grensgroepen.  

Om publiceren te configureren voor Active Directory-forests voor elke site in uw hiërarchie, door de Configuration Manager-console verbinding te maken met de site op het hoogste niveau van uw hiërarchie. De **Publishing** tabblad in een Active Directory-site **eigenschappen** in het dialoogvenster alleen de huidige site en de onderliggende sites kunt zien. Als de publicatie is ingeschakeld voor een forest en dat forest schema wordt uitgebreid voor Configuration Manager, wordt de volgende informatie gepubliceerd voor elke site die is ingeschakeld voor het publiceren naar deze Active Directory-forest:  

-    **SMS-Site -&lt;sitecode >**

-   **SMS-MP -&lt;sitecode >-&lt;sitesysteemservernaam >**  

-   **SMS-SLP -&lt;sitecode >-&lt;sitesysteemservernaam >**  

-   **SMS -&lt;sitecode >-&lt;Active Directory-sitenaam of -subnet >**  

> [!NOTE]  
>  Secundaire sites gebruiken steeds het computeraccount van de secundaire siteserver om naar Active Directory te publiceren. Indien u secundaire sites wenst te publiceren naar Active Directory, zorg ervoor dat het computeraccount van de secundaire siteserver machtigingen heeft om te publiceren naar Active Directory. Een secundaire site kan geen gegevens publiceren naar een niet-vertrouwd forest.  

> [!CAUTION]  
>  Wanneer u de optie voor het publiceren van een site naar een Active Directory-forest uitschakelt, wordt alle eerder gepubliceerde informatie voor die site, inclusief beschikbare sitesysteemrollen, verwijderd uit Active Directory.  

Acties voor Active Directory-Forestdetectie worden geregistreerd in de volgende Logboeken:  

-   Alle acties, met uitzondering van de acties die verband houden met publiceren, worden geregistreerd in de **ADForestDisc.Log** bestand in de  **&lt;installatiepad > \Logs** map op de siteserver.  

-   Detectie van Active Directory-Forest publicatieacties worden geregistreerd in de **hman.log** en **sitecomp.log** -bestanden in de  **&lt;installatiepad > \Logs** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutGroup"></a>Detectie van Active Directory-groepen  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode worden uitgevoerd:  

-   **Detectieaccount Active Directory-groepen** (de gebruiker gedefinieerde)  

-   **Computeraccount** van de siteserver  

> [!TIP]  
>  Naast de informatie in deze sectie [algemene functies van Active Directory-groep-, systeem- en -Gebruikersdetectie](#bkmk_shared).  

Gebruik deze methode om te zoeken in Active Directory Domain Services om te identificeren:  

-   Lokale, globale en universele beveiligingsgroepen.  

-   Het lidmaatschap van groepen.  

-   Beperkte informatie over de computers die lid zijn van een groep en de gebruikers, zelfs wanneer een andere detectiemethode heeft niet eerder gedetecteerd deze computers en gebruikers.  

Deze detectiemethode is bedoeld om groepen en de groeprelaties van leden van groepen te identificeren. Standaard worden alleen beveiligingsgroepen gedetecteerd. Als u ook het lidmaatschap van distributiegroepen zoekt, moet u het selectievakje voor de optie **het lidmaatschap van distributiegroepen detecteren** op de **optie** tabblad de **detectie eigenschappen voor Active Directory-groepen** in het dialoogvenster.  

Detectie van Active Directory-groep biedt geen ondersteuning voor de uitgebreide Active Directory-attributen die kunnen worden geïdentificeerd met behulp van Active Directory-Systeemdetectie of Active Directory User Discovery. Omdat deze detectiemethode niet geoptimaliseerd is om computer- en -bronnen te detecteren, moet u de detectiemethode uitgevoerd nadat u Active Directory-Systeemdetectie en Active Directory-Gebruikersdetectie hebt uitgevoerd. Dit is omdat deze methode maakt u een volledige detectiegegevensrecord (DDR) voor groepen, maar enkel een beperkte DDR voor computers en gebruikers die lid van groepen zijn.  

U kunt de volgende detectiebereiken configureren die controleren hoe deze methode zoekt naar informatie:  

-   **Locatie**: Gebruik een locatie indien u wilt één of meer Active Directory-containers doorzoeken. Deze bereikoptie ondersteunt een recursief zoeken van de opgegeven Active Directory-containers dat ook doorzoekt elke onderliggende container onder de container die u opgeeft. Dit proces wordt voortgezet tot er geen meer onderliggende containers worden gevonden.  

-   **Groepen**: Gebruik groepen indien u wilt zoeken in een of meer Active Directory-groepen. U kunt configureren **Active Directory-domein** gebruikt het standaarddomein en het forest of zoeken beperken tot een individuele domeincontroller. Daarnaast kunt u een of meer groepen om te zoeken. Als u niet minstens één groep opgeeft, wordt alle groepen gevonden in de opgegeven **Active Directory-domein** locatie worden doorzocht.  

> [!CAUTION]  
>  Als u een detectiebereik configureert, kiest u alleen de groepen die u moet detecteren. Dit komt doordat de detectie van Active Directory-groep probeert te achterhalen welke elk lid van elke groep in het detectiebereik. Detectie van grote groepen kan uitgebreid gebruik van bandbreedte en Active Directory-bronnen vereisen.  

> [!NOTE]  
>  Voer alvorens kunt u verzamelingen die zijn gebaseerd op uitgebreide Active Directory-attributen (en zorg ervoor dat nauwkeurige detectieresultaten voor computers en gebruikers scanresultaten) uit Active Directory-Systeemdetectie of Active Directory User Discovery, afhankelijk van wat u wilt detecteren.  

Acties voor detectie van Active Directory-groep zijn opgenomen in het bestand **adsgdis.log** in de  **&lt;installatiepad\>\LOGS** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutSystem"></a>Active Directory-Systeemdetectie  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode worden uitgevoerd:  

-   **Detectieaccount Active Directory-systeem** (de gebruiker gedefinieerde)  

-   **Computeraccount** van de siteserver  

> [!TIP]  
>  Naast de informatie in deze sectie [algemene functies van Active Directory-groep-, systeem- en -Gebruikersdetectie](#bkmk_shared).  

Deze detectie gebruiken om te zoeken naar de opgegeven Active Directory Domain Services-locaties voor computerbronnen die kunnen worden gebruikt om verzamelingen en query's te maken. U kunt ook de Configuration Manager-client op gedetecteerde apparaten installeren met behulp van push-clientinstallatie.  

Deze methode detecteert standaard algemene informatie over de computer, waaronder het volgende:  

-   Computernaam  

-   Besturingssysteem en versie  

-   Active Directory-containernaam  

-   Het IP-adres  

-   Active Directory-site  

-   Tijdstempel van de laatste aanmelding  

Voor het maken van een DDR voor een computer, moet Active Directory-Systeemdetectie kunnen de computeraccount te identificeren en dan de naam van de computer aan een IP-adres.  

In de **eigenschappen van Active Directory Discovery** dialoogvenster op de **Active Directory-attributen** tabblad vindt u de volledige lijst van standaard-objectkenmerken die detectie van Active Directory-systemen heeft geretourneerd. U kunt ook de methode voor het detecteren van extra (uitgebreid) kenmerken configureren.  

Acties voor Active Directory-Systeemdetectie worden geregistreerd in het bestand **adsysdis.log** in de  **&lt;installatiepad\>\LOGS** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutUser"></a>Detectie van Active Directory-gebruikers  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode worden uitgevoerd:  

-   **Detectieaccount Active Directory-gebruikers** (de gebruiker gedefinieerde)  

-   **Computeraccount** van de siteserver  

> [!TIP]  
>  Naast de informatie in deze sectie [algemene functies van Active Directory-groep-, systeem- en -Gebruikersdetectie](#bkmk_shared).  

Deze detectiemethode gebruiken om te zoeken in Active Directory Domain Services om gebruikersaccounts en gekoppelde attributen te identificeren. Deze methode detecteert standaard algemene informatie over het gebruikersaccount waaronder de volgende:  

-   Gebruikersnaam  

-   Unieke gebruikersnaam (inclusief de domeinnaam)  

-   Domein  

-   Namen van Active Directory-container  

In de **eigenschappen voor Active Directory-Gebruikersdetectie** dialoogvenster op de **Active Directory-attributen** tabblad kunt u de volledige standaardlijst van objectattributen die detectie van Active Directory-gebruikers heeft geretourneerd weergeven. U kunt ook de methode voor het detecteren van extra (uitgebreid) kenmerken configureren.

Acties voor detectie van Active Directory-gebruikers zijn opgenomen in het bestand **adusrdis.log** in de  **&lt;installatiepad\>\LOGS** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutHeartbeat"></a>Heartbeat-detectie  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Ja  

**Accounts** kunt u deze methode worden uitgevoerd:  

-   **Computeraccount** van de siteserver  

Heartbeat-detectie verschilt van andere detectiemethoden Configuration Manager. Het is standaard ingeschakeld en wordt uitgevoerd op elke computerclient (in plaats van op een siteserver bevindt) te maken van een DDR. Voor clients van mobiele apparaten, wordt dit DDR gemaakt door het beheerpunt dat van de client voor mobiele apparaten gebruikmaakt. Schakel Heartbeat-detectie niet te handhaven het databaserecord van Configuration Manager-clients. Naast het databaserecord onderhouden, is deze methode kan de detectie van een computer als een nieuw bronnenrecord forceren of kan het databaserecord van een computer die is verwijderd uit de database opnieuw bevolken.  

Heartbeat-detectie wordt uitgevoerd op een schema dat is geconfigureerd voor alle clients in de hiërarchie, of als handmatig wordt aangeroepen, op een specifieke client door het uitvoeren van de **Verzamelfase zoekgegevens** op de **actie** tabblad in de Configuration Manager-programma van de client. Het standaardschema voor Heartbeat-detectie is ingesteld op elke 7 dagen. Als u het interval voor heartbeat-detectie wijzigt, zorg ervoor dat het frequenter wordt uitgevoerd dan de siteonderhoudstaak **verouderde Detectiegegevens verwijderen**, die inactieve clientrecords uit de sitedatabase wist. U kunt de **verouderde Detectiegegevens verwijderen** taak alleen voor primaire sites.  

Wanneer Heartbeat-detectie wordt uitgevoerd, wordt een DDR met de huidige informatie van de client gemaakt. Deze klein bestand (ongeveer 1 KB groot zijn) kopieert de client vervolgens naar een beheerpunt zodat een primaire site kan worden verwerkt. Het bestand heeft de volgende informatie:  

-   Netwerklocatie  

-   NetBIOS-naam  

-   Versie van de clientagent  

-   Operationele statusdetails  

Heartbeat-detectie is de enige detectiemethode die details over de installatiestatus van de client geeft. Dit gebeurt met het bijwerken van het kenmerk en de systeembronclient om in te stellen een waarde gelijk zijn aan **Ja**.  

> [!NOTE]  
>  Zelfs wanneer Heartbeat-detectie is uitgeschakeld, zijn nog steeds DDR's gemaakt en verzonden voor actieve mobiele apparaatclients. Dit zorgt ervoor dat de **verouderde Detectiegegevens verwijderen** taak heeft geen invloed op actieve mobiele apparaten. Dit gebeurt omdat wanneer de **verouderde Detectiegegevens verwijderen** taak een databaserecord voor een mobiel apparaat wist, trekt het ook het apparaatcertificaat en blokkeert het het mobiele apparaat geen verbinding maken met beheerpunten.  

Acties voor Heartbeat-detectie worden geregistreerd in de volgende locaties:  

-   Voor computerclients worden acties van Heartbeat-detectie geregistreerd op de client in de **InventoryAgent.log** bestand in de *%Windir%\CCM\Logs* map.  

-   Voor clients van mobiele apparaten, acties van Heartbeat-detectie geregistreerd de **DMPRP.log** bestand in de *% programma Files%\CCM\Logs* map van het beheerpunt dat gebruikmaakt van de client voor mobiele apparaten.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutNetwork"></a>Netwerkdetectie  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode worden uitgevoerd:  

-   **Computeraccount** van de siteserver  

Gebruik deze methode voor het detecteren van de topologie van uw netwerk en apparaten in uw netwerk met een IP-adres te detecteren. Netwerkdetectie doorzoekt uw netwerk naar bronnen met IP ingeschakeld door query's op servers met een Microsoft-implementatie van DHCP, ARP Address Resolution Protocol ()-caches in routers, -apparaten met SNMP en Active Directory-domeinen.  

Voordat u netwerkdetectie gebruiken kunt, moet u de *niveau* van detectie wordt uitgevoerd. U configureert ook een of meerdere detectiemechanismen die netwerkdetectie om netwerksegmenten of apparaten te vragen inschakelen. U kunt ook instellingen configureren die helpen detectieacties controleren op het netwerk te. Tot slot definieert u een of meer schema's voor wanneer netwerkdetectie wordt uitgevoerd.  

Voor deze methode is een om bron te detecteren moet netwerkdetectie het IP-adres en het subnetmasker van de bron identificeren. De volgende methoden worden gebruikt om het subnetmasker van een object te identificeren:  

-   **Router ARP-cache:** Netwerkdetectie via een query de ARP-cache van een router om Subnetinformatie te vinden. Gegevens in een router ARP-cache is gewoonlijk een korte tijd bestaan. Wanneer netwerkdetectie via een query de ARP-cache, kan de ARP-cache niet langer zijn daarom informatie over het opgevraagde object.  

-   **DHCP:** Netwerkdetectie via een query elke DHCP-server die u opgeeft voor het detecteren van de apparaten waarvoor de DHCP-server een lease heeft geleverd. Netwerkdetectie ondersteunt alleen DHCP-servers die Microsoft-implementatie van DHCP uitvoeren.  

-   **SNMP-apparaat:** Netwerkdetectie kan rechtstreeks query uitvoeren op een SNMP-apparaat. Opdat netwerkdetectie een apparaat, moet het apparaat een lokale SNMP-agent geïnstalleerd hebben. U moet ook netwerkdetectie voor het gebruik van de communitynaam die van de SNMP-agent gebruikmaakt configureren.  

Wanneer detectie een object met IP-adres identificeert en het subnetmasker van het object kan bepalen, maakt het een Detectiegegevensrecord voor dat object. Omdat verschillende types apparaten een verbinding met het netwerk maken kunnen, kan netwerkdetectie bronnen die ondersteuning voor de Configuration Manager-clientsoftware kunnen niet detecteren. Apparaten die kunnen worden gedetecteerd, maar niet beheerd zijn bijvoorbeeld printers en routers.  

Netwerkdetectie kan verschillende kenmerken terugsturen als deel van het detectierecord dat wordt gemaakt. Deze omvatten:  

-   NetBIOS-naam  

-   IP-adressen  

-   Brondomein  

-   Systeemrollen  

-   SNMP-communitynaam  

-   MAC-adressen  

Activiteit van netwerkdetectie wordt geregistreerd in de **Netdisc.log** in het bestand  *&lt;installatiepad\>\Logs* op de siteserver die detectie uitvoert.  

 Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

> [!NOTE]  
>  Complexe netwerken en verbindingen met lage bandbreedte kunnen ervoor zorgen dat netwerkdetectie traag wordt uitgevoerd en kunnen significant netwerkverkeer genereren. Als een best practice netwerkdetectie alleen uitvoeren als de andere detectiemethodes de bronnen die u dient te detecteren niet kunnen vinden. Gebruik netwerkdetectie bijvoorbeeld als u werkgroepcomputers moet detecteren. Andere detectiemethoden detecteert geen computers in werkgroepen.  

###  <a name="BKMK_NetDiscLevels"></a>Niveaus van netwerkdetectie  
Wanneer u netwerkdetectie configureert, specificeert u een van drie detectieniveaus:  

|Niveau van detectie|Details|  
|------------------------|-------------|  
|Topologie|Dit niveau detecteert routers en subnetten die geen subnetmasker voor objecten identificeren.|  
|Topologie en client|Naast topologie detecteert dit niveau mogelijke clients zoals computers, en bronnen zoals printers en routers. Dit niveau van detectie wordt geprobeerd om het subnetmasker van objecten dat het vindt te identificeren.|  
|Topologie, client- en client-besturingssysteem|Naast topologie en mogelijke clients probeert dit niveau voor het detecteren van de computernaam van het besturingssysteem en versie. Dit niveau maakt gebruik van Windows-Browser en Windows Networking-oproepen.|  

 Met elk incrementeel niveau verhoogt de netwerkdetectie haar activiteit en gebruik van de netwerkbandbreedte. Houd rekening met het netwerkverkeer dat kan worden gegenereerd voordat u alle aspecten van netwerkdetectie inschakelt.  

 Wanneer u netwerkdetectie voor het eerst gebruikt, kunt u bijvoorbeeld bijvoorbeeld voor starten met enkel het topologieniveau om uw netwerkinfrastructuur te identificeren. U kunt vervolgens opnieuw configureren netwerkdetectie om objecten en hun besturingssystemen van apparaten te detecteren. U kunt ook instellingen configureren die netwerkdetectie tot een specifiek bereik van netwerksegmenten beperken. Op die manier kunt u objecten in netwerklocaties die u nodig hebt en zo onnodig netwerkverkeer en kunt u objecten van randrouters of van detecteren detecteren buiten uw netwerk.  

###  <a name="BKMK_NetDiscOptions"></a>Opties voor netwerkdetectie  
Als u wilt dat netwerkdetectie om te zoeken naar apparaten met een IP-adres, moet u een of meer van de volgende opties die specificeren hoe apparaten worden opgevraagd.  

> [!NOTE]  
>  Netwerkdetectie wordt uitgevoerd in de context van het computeraccount van de siteserver die detectie uitvoert. Als het computeraccount geen machtigingen heeft voor een niet-vertrouwd domein, kunnen het domein en de configuraties van DHCP-server geen bronnen detecteren.  

**DHCP:**  

Geef elke DHCP-server die u wilt dat netwerkdetectie opvraagt. (Netwerkdetectie ondersteunt alleen DHCP-servers die Microsoft-implementatie van DHCP uitvoeren.)  

-   Netwerkdetectie haalt informatie op met behulp van externe procedureoproepen naar de database op de DHCP-server.  

-   Netwerkdetectie kan zowel 32-bits en 64-bits DHCP-servers opvragen voor een lijst met apparaten die zijn geregistreerd bij elke server.  

-   Opdat netwerkdetectie een DHCP-server zou kunnen opvragen, moet het computeraccount van de server die detectie uitvoert een lid van de DHCP-gebruikersgroep op de DHCP-server. Dit toegangsniveau bestaat bijvoorbeeld wanneer een van de volgende omstandigheden:  

    -   De opgegeven DHCP-server is de DHCP-server van de server die detectie uitvoert.  

    -   De computer die detectie uitvoert en de DHCP-server bevinden zich in hetzelfde domein bevinden.  

    -   Er bestaat een tweerichtingsvertrouwensrelatie tussen de computer die detectie uitvoert en de DHCP-server.  

    -   De siteserver is lid van de DHCP-gebruikersgroep.  

-   Wanneer netwerkdetectie een DHCP-server inventariseert, ontdekt het niet altijd statische IP-adressen. Netwerkdetectie vindt geen IP-adressen die deel van een uitgesloten bereik van IP-adressen op de DHCP-server uitmaken. Het detecteert ook geen IP-adressen die voor handmatige toewijzing voorbehouden zijn.  

**Domeinen:**  

Geef elk domein dat u wilt dat netwerkdetectie opvraagt.  

-   Het computeraccount van de siteserver die detectie uitvoert moet gemachtigd zijn om de domeincontrollers in elk opgegeven domein te lezen.  

-   Om computers te detecteren van het lokale domein, moet u de Computer Browser-service op ten minste één computer die zich in hetzelfde subnet als de siteserver die netwerkdetectie uitvoert inschakelen.  

-   Netwerkdetectie kan elke computer detecteren die u vanop uw siteserver bekijken kunt wanneer u het netwerk bladert.  

-   Netwerkdetectie haalt het IP-adres en gebruikt een Internet Control Message Protocol-echoaanvraag om elk apparaat dat het vindt te pingen. De **ping** opdracht helpt te bepalen welke computers momenteel actief zijn.  

**SNMP-apparaten:**  

Geef elk SNMP-apparaat dat u wilt dat netwerkdetectie opvraagt.  

-   Netwerkdetectie haalt de waarde ipNetToMediaTable van elk SNMP-apparaat dat met de query overeenkomt. Deze waarde stuurt matrices van IP-adressen die clientcomputers of andere bronnen zoals printers, routers of andere apparaten met een IP-adres terug.  

-   Om te vragen van een apparaat, moet u de IP-adres of de NetBIOS-naam van het apparaat.  

-   U moet netwerkdetectie configureren voor gebruik van de communitynaam van het apparaat of het apparaat verwerpt de op SNMP gebaseerde query.  

###  <a name="BKMK_LimitNetDisc"></a>Netwerkdetectie beperken  
Wanneer netwerkdetctie een SNMP-apparaat aan de rand van uw netwerk, kan het informatie over subnetten en SNMP-apparaten die zich buiten uw onmiddellijke netwerk identificeren. Gebruik de volgende informatie voor netwerkdetectie beperken door de SNMP-apparaten te configureren waarmee detectie kan communiceren, en door te geven van de netwerksegmenten te vragen.  

**Subnetten:**  

Configureer de subnetten die netwerkdetectie opvraagt wanneer het de SNMP- en DHCP-opties. Deze twee opties zoeken alleen de ingeschakelde subnetten.  

Een DHCP-aanvraag kan apparaten bijvoorbeeld terugsturen vanuit locaties binnen uw volledige netwerk. Als u wilt dat alleen apparaten op een specifiek subnet te detecteren, geef en schakel dan dat specifieke subnet in de **subnetten** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster. Wanneer u subnetten geeft en inschakelt, beperkt u toekomstige DHCP- en SNMP-detectie taken tot deze subnetten.  

> [!NOTE]  
>  Subnetconfiguraties beperken niet de objecten die de **domeinen** optie domeindetectie detecteert.  

**SNMP-communitynamen:**  

Om te schakelen netwerkdetectie om op te vragen een SNMP-apparaat, configureert u netwerkdetectie met de communitynaam van het apparaat. Als netwerkdetectie niet is geconfigureerd met behulp van de communitynaam van het SNMP-apparaat, verwerpt het apparaat de query.  

**Maximum aantal hops:**  

Wanneer u het maximum aantal router-hops configureert, beperkt u het aantal netwerksegmenten en routers die netwerkdetectie opvragen kan via SNMP.  

Het aantal hops dat u configureert, beperkt het aantal bijkomende apparaten en netwerksegmenten dat netwerkdetectie kan opvragen.  

Bijvoorbeeld, een alleen-topologie-detectie met **0** (nul) router-hops detecteert het subnet waarop de oorspronkelijke server zich bevindt. Het neemt alle routers in dat subnet.  

Het volgende diagram toont wat een topologie-alleen netwerkdetectie query vindt wanneer ze op Server 1 uitvoert met 0 router-hops gespecificeerde: subnet D en Router 1.  

 ![Afbeelding van detectie met nul Vliegende router](media/Disc-0.gif)  

 Het volgende diagram toont wat een topologie en client-netwerkdetectie query vindt wanneer ze op Server 1 met 0 gespecificeerde router-hops uitvoert: subnet D en Router 1 en alle potentiële clients op subnet D.  

 ![Afbeelding van detectie met één router gaan](media/Disc-1.gif)  

 Als u een beter idee krijgen van hoe bijkomende router hops kunnen vergroot de hoeveelheid netwerkbronnen die zijn gedetecteerd, houd rekening met het volgende netwerk:  

 ![Afbeelding van detectie met twee router sprongen](media/Disc-2.gif)  

 Een topologie-alleen netwerkdetectie detecteeert vanaf Server 1 met één router-hop het volgende:  

-   Router 1 en subnet 10.1.10.0 (gevonden met nul hops)  

-   Subnetten 10.1.20.0 en 10.1.30.0, subnet A en Router 2 (gevonden op de eerste hop)  

> [!WARNING]  
>  Elke toename van het aantal router-hops kan aanzienlijk verhogen van het aantal detecteerbare bronnen en de netwerkbandbreedte vergroten die netwerkdetectie gebruikt.  

##  <a name="bkmk_aboutServer"></a>Serverdetectie  
**Configureerbare:** Nee  

Naast de gebruiker configureerbare detectiemethoden gebruikt Configuration Manager een proces heet **serverdetectie** (SMS_WINNT_SERVER_DISCOVERY_AGENT). Deze detectiemethode maakt bronrecords voor computers die zijn sitesystemen, zoals een computer die is geconfigureerd als een beheerpunt.  

##  <a name="bkmk_shared"></a>Algemene functies van Active Directory Group Discovery, systeem-detectie en gebruiker  
Deze sectie bevat informatie over functies die gemeenschappelijk voor de volgende detectiemethoden zijn:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

> [!NOTE]  
>  De informatie in deze sectie is niet van toepassing op detectie van Active Directory-forests.  

Deze drie detectiemethoden zijn vergelijkbaar in configuratie en werking. Ze kunnen computers, gebruikers en informatie over groepslidmaatschappen van bronnen die zijn opgeslagen in Active Directory Domain Services detecteren. Het detectieproces wordt beheerd door een detectieagent die wordt uitgevoerd op de siteserver op elke site waarvoor detectie is ingeschakeld. U kunt elk van deze detectiemethoden om te zoeken naar een of meer Active Directory-locaties zoals locatie-instanties in het lokale forest of in externe forests configureren.  

Wanneer detectie naar een niet-vertrouwd forest voor bronnen zoekt, is de detectieagent moet kunnen het volgende om succesvol op te lossen:  

-   Om een computerbron met behulp van Active Directory-Systeemdetectie detecteren, moet de detectieagent kunnen omzetten van de FQDN-naam van de bron. Als de FQDN-naam kan niet worden omgezet, probeer het omzetten van de bron via de NetBIOS-naam.  

-   Voor het detecteren van een gebruiker of groepsbron met behulp van detectie van Active Directory-gebruikers of Active Directory Group Discovery, moet de detectieagent de FQDN van de controller domeinnaam die u voor de Active Directory-locatie opgeeft kunnen omzetten.  

Voor elke locatie die u opgeeft, kunt u individuele zoekopties, zoals het inschakelen van een recursieve zoekopdracht van de locatie onderliggende Active Directory-containers configureren. U kunt ook een uniek account configureren om gebruiken bij het zoeken van die locatie. Dit geeft flexibiliteit bij het configureren van een detectiemethode op één site om te zoeken naar meerdere Active Directory-locaties in meerdere forests zonder dat voor het configureren van een enkele account die machtigingen voor alle locaties heeft.  

Wanneer elk van deze drie detectiemethoden op een specifieke site wordt uitgevoerd, contact de Configuration Manager-siteserver op die site op de dichtstbijzijnde domeincontroller in het opgegeven Active Directory-forest om Active Directory-bronnen te vinden. Het domein en het forest kunnen zich in eender welke ondersteunde Active Directory-modus bevinden. Het account dat u aan elk locatie-exemplaar toewijst moet hebben **lezen** toegangsmachtiging voor de gespecificeerde Active Directory-locaties.

Detectie zoekt in de opgegeven locaties naar objecten en probeert vervolgens informatie over die objecten te verzamelen. Een DDR wordt gemaakt wanneer er voldoende informatie over een bron kan worden geïdentificeerd. De vereiste informatie is afhankelijk van de detectiemethode die wordt gebruikt.  

Als u dezelfde detectiemethode om uit te voeren op verschillende sites van Configuration Manager om te profiteren van query's op lokale Active Directory-servers configureert, kunt u elke site configureren met een unieke set van detectieopties. Omdat detectiegegevens worden gedeeld met elke site in de hiërarchie, voorkomen dat u overlapping tussen deze configuraties om efficiënt te detecteren elke bron één keer. 

Voor kleinere omgevingen, u kunt overwegen om elke detectiemethode op slechts één site in uw hiërarchie minder administratieve overhead en de mogelijkheid dat meerdere detectieacties dezelfde bronnen opnieuw detecteren. Wanneer u Beperk het aantal sites dat detectie uitvoert, kun je de totale netwerkbandbreedte die detectie gebruikt. Daarnaast kunt u het totale aantal DDR's dat wordt gemaakt en moeten worden verwerkt door uw siteservers verminderen.  

Veel van de methode detectieconfiguraties behoeven geen uitleg. Gebruik de volgende secties voor meer informatie over de detectieopties die bijkomende informatie vereisen kunnen vóór u ze configureert.  

De volgende opties zijn beschikbaar voor gebruik met meerdere Active Directory-detectiemethoden:  

-   [Detectie van verschillen](#bkmk_delta)  

-   [Verouderde computerrecords filteren op aanmelden bij domein](#bkmk_stalelogon)  

-   [Verlopen records filteren op computerwachtwoord](#bkmk_stalepassword)  

-   [Aangepaste kenmerken voor Active Directory zoeken](#bkmk_customAD)  

###  <a name="bkmk_delta"></a>Detectie van verschillen  
Beschikbaar voor:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

Detectie van verschillen is geen een onafhankelijke detectiemethode maar een optie beschikbaar voor de toepasselijke detectiemethoden. Detectie van verschillen zoekt specifieke Active Directory-attributen voor wijzigingen die zijn aangebracht sinds de laatste volledige detectiecyclus van de toepasselijke detectiemethode. Het kenmerkwijzigingen worden verzonden naar de Configuration Manager-database de detectierecord van de resource bij te werken.  

Detectie van verschillen wordt standaard uitgevoerd in een cyclus van vijf minuten uitgevoerd. Dit is veel vaker dan het standaard schema voor een volledige detectiecyclus.  Deze frequente cyclus is mogelijk omdat detectie van verschillen minder siteserver gebruikt en andere netwerkbronnen dan een volledige detectiecyclus heeft. Wanneer u detectie van verschillen gebruikt, kunt u de frequentie van de volledige detectiecyclus voor die detectiemethode te verminderen.  

Hier volgen de meest voorkomende wijzigingen die detectie van verschillen detecteert:  

-   Nieuwe computers of gebruikers die zijn toegevoegd aan Active Directory  

-   Wijzigingen in basisinformatie computer en gebruiker  

-   Nieuwe computers of gebruikers die zijn toegevoegd aan een groep  

-   Computers of gebruikers die zijn verwijderd uit een groep  

-   Wijzigingen in de systeemgroepsobjecten  

Hoewel detectie van verschillen nieuwe bronnen en wijzigingen aan groepslidmaatschap detecteren kan, kan niet detecteren wanneer een bron is verwijderd uit Active Directory. DDR's die zijn gemaakt door de detectie van verschillen worden op deze manier verwerkt als de DDR's die zijn gemaakt door een volledige detectiecyclus.  

U configureert detectie van verschillen op de **Polling-planning** tabblad in de eigenschappen voor elke detectiemethode.  

###  <a name="bkmk_stalelogon"></a>Verouderde computerrecords filteren op aanmelden bij domein  
Beschikbaar voor:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

U kunt detectie configureren zodat het uitsluiten van computers met een verouderde record op basis van de laatste domeinaanmelding van de computer. Wanneer deze optie is ingeschakeld, beoordeelt Active Directory-Systeemdetectie elke computer die het identificeert. Detectie voor Active Directory-groepen beoordeelt elke computer die lid is van een groep die is gedetecteerd.  

Deze optie wilt gebruiken:  

-   Computers moeten worden geconfigureerd voor het bijwerken van de **lastLogonTimeStamp** kenmerk in Active Directory Domain Services.  

-   Het functionele niveau van Active Directory-domein moet worden ingesteld op Windows Server 2003 of later.  

Wanneer u de tijd na de laatste aanmelding die u wilt gebruiken voor deze instelling configureert, neem dan het interval voor replicatie tussen domeincontrollers.  

U configureert filtering op het **optie** tabblad de **eigenschappen van Active Directory Discovery** en **detectie eigenschappen voor Active Directory-groepen** dialoogvensters. Kies de optie **alleen computers detecteren die zijn aangemeld bij een domein in een bepaalde periode**.  

> [!WARNING]  
>  Wanneer u dit filter configureert en **verlopen records filteren op computerwachtwoord**, computers die voldoen aan de criteria van een filter zijn uitgesloten van detectie.  

###  <a name="bkmk_stalepassword"></a>Verlopen records filteren op computerwachtwoord  
Beschikbaar voor:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

U kunt detectie configureren zodat het uitsluiten van computers met een verouderde record op basis van de laatste update van het computer account wachtwoord door de computer. Wanneer deze optie is ingeschakeld, beoordeelt Active Directory-Systeemdetectie elke computer die het identificeert. Detectie voor Active Directory-groepen beoordeelt elke computer die lid is van een groep die is gedetecteerd.  

Deze optie wilt gebruiken:  

-   Computers moeten worden geconfigureerd voor het bijwerken van de **pwdLastSet** kenmerk in Active Directory Domain Services.  

Wanneer u deze optie configureert, neem dan het interval voor updates voor dit attribuut, alsook de replicatie-interval tussen domeincontrollers.  

U configureert filtering op het **optie** tabblad de **eigenschappen van Active Directory Discovery** en **detectie eigenschappen voor Active Directory-groepen** dialoogvensters. Kies de optie **Detecteer enkel computers die hun wachtwoord van computeraccount hebben bijgewerkt in een bepaalde periode**.  

> [!WARNING]  
>  Wanneer u dit filter configureert en **verlopen records filteren op aanmelden bij domein**, computers die voldoen aan de criteria van een filter zijn uitgesloten van detectie.  

###  <a name="bkmk_customAD"></a>Aangepaste kenmerken voor Active Directory zoeken  
 Beschikbaar voor:  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

Elke detectiemethode ondersteunt een unieke lijst van Active Directory-attributen die kunnen worden gedetecteerd.  

U kunt weergeven en de lijst met aangepaste kenmerken configureren op de **Active Directory-attributen** tabblad de **eigenschappen van Active Directory Discovery** en **eigenschappen voor Active Directory-Gebruikersdetectie** dialoogvensters.  

