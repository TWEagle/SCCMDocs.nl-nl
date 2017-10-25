---
title: Detectiemethoden | Microsoft Docs
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed931751-18f2-4230-a09e-a0a329fbfa1c
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 442e5e1fbddd00248819a8de79adc78929474fc0
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="about-discovery-methods-for-system-center-configuration-manager"></a>Detectiemethoden voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Detectiemethoden voor System Center Configuration Manager vindt andere apparaten in uw netwerk of de apparaten en gebruikers uit Active Directory. U moet voor het efficiënt gebruik van een detectiemethode, de beschikbare configuraties en beperkingen begrijpen.  

##  <a name="bkmk_aboutForest"></a>Detectie van Active Directory-forests  
 **Configureerbare:** Ja  

 **Standaard is ingeschakeld:** Nee  

 **Accounts** kunt u deze methode niet uitvoeren:  

-   **Detectieaccount Active Directory-Forest** (de gebruiker gedefinieerd)  

-   **Computeraccount** van de siteserver  

In tegenstelling tot andere Active Directory-detectiemethoden detecteren Active Directory Forest Discovery niet van bronnen die u kunt beheren. In plaats daarvan detecteert deze methode netwerklocaties die zijn geconfigureerd in Active Directory en kunnen deze locaties converteren grenzen voor gebruik binnen de hiërarchie.  

Wanneer deze methode wordt uitgevoerd, er wordt gezocht naar de lokale Active Directory-forest, elk vertrouwd forest, en elke extra forest dat u configureert in de **Active Directory-Forests** knooppunt van de Configuration Manager-console.  

Gebruik Active Directory-Forest detectie:  

-   Active Directory-sites en -subnets detecteren en maak vervolgens Configuration Manager-grenzen op basis van deze netwerklocaties.  

-   Identificeer supernets die zijn toegewezen aan een Active Directory-site en elk supernet converteren naar een grens van IP-adresbereik.  

-   Publiceren naar Active Directory Domain Services (AD DS) in een forest wanneer publiceren naar dit forest is ingeschakeld en het opgegeven Active Directory-Forestaccount machtigingen voor dat forest heeft.  

U kunt Active Directory Forest Discovery beheren in de Configuration Manager-console vanaf de volgende knooppunten onder **Hiërarchieconfiguratie** in de **beheer** werkruimte:  

-   **Detectiemethoden**: Hier kunt u detectie van Active Directory-Forest om uit te voeren op het hoogste niveau van uw hiërarchie. U kunt ook een simpele planning uitvoeren van detectie opgeven en configureren om automatisch grenzen te maken van de IP-subnetten en Active Directory-sites die het detecteert. Detectie van Active Directory-forests kan niet worden uitgevoerd op een onderliggende primaire site of op een secundaire site.  

-   **Active Directory-Forests**: Hier configureert u de extra Active Directory-forests die u wilt detecteren, geeft u het account wilt gebruiken als de Active Directory-Forestaccount voor elke forest en publiceren naar elke forest te configureren. Bovendien kunt u het detectieproces bewaken en IP-subnetten en Active Directory-sites aan Configuration Manager toevoegen als grenzen en leden van grensgroepen.  

Om publiceren te configureren voor Active Directory-forests voor elke site in uw hiërarchie, door de Configuration Manager-console verbinding te maken met het hoogste niveau van uw hiërarchie. De **Publishing** tabblad in een Active Directory-site **eigenschappen** in het dialoogvenster ziet alleen de huidige site en de onderliggende sites. Wanneer publiceren ingeschakeld is voor een forest en dat forest-schema voor Configuration Manager is uitgebreid, wordt de volgende informatie gepubliceerd voor elke site die is ingeschakeld voor het publiceren naar deze Active Directory-forest:  

-    **SMS-Site -&lt;sitecode >**

-   **SMS-MP -&lt;site code >-&lt;sitesysteemservernaam >**  

-   **SMS-SLP -&lt;site code >-&lt;sitesysteemservernaam >**  

-   **SMS -&lt;site code >-&lt;Active Directory-sitenaam of -subnet >**  

> [!NOTE]  
>  Secundaire sites gebruiken steeds het computeraccount van de secundaire siteserver om naar Active Directory te publiceren. Als u wilt dat secundaire sites kunnen publiceren naar Active Directory, zorg ervoor dat het computeraccount van de secundaire siteserver gemachtigd is voor publiceren naar Active Directory. Een secundaire site publiceren geen gegevens naar een niet-vertrouwd forest.  

> [!CAUTION]  
>  Wanneer u de optie voor het publiceren van een site aan een Active Directory-forest uitschakelt, wordt alle eerder gepubliceerde informatie voor die site, inclusief beschikbare sitesysteemrollen, verwijderd uit Active Directory.  

Acties voor Active Directory-Forestdetectie worden geregistreerd in de volgende Logboeken:  

-   Alle acties, met uitzondering van de acties die verband houden met publiceren, worden geregistreerd in de **ADForestDisc.Log** bestand de  **&lt;InstallationPath > \Logs** map op de siteserver.  

-   Detectie van Active Directory-Forest publishing acties worden vastgelegd in de **hman.log** en **sitecomp.log** bestanden in de  **&lt;InstallationPath > \Logs** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutGroup"></a>Detectie van Active Directory-groep  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode niet uitvoeren:  

-   **Detectieaccount Active Directory-groepen** (de gebruiker gedefinieerd)  

-   **Computeraccount** van de siteserver  

> [!TIP]  
>  Naast de informatie in deze sectie, Zie [algemene functies van Active Directory-groep, systeem en detectie van gebruikers](#bkmk_shared).  

Gebruik deze methode om te zoeken van Active Directory Domain Services om te identificeren:  

-   Lokale, globale en universele beveiligingsgroepen.  

-   Het lidmaatschap van groepen.  

-   Beperkte informatie over de computers die lid zijn van een groep en de gebruikers, zelfs wanneer een andere detectiemethode heeft niet eerder gedetecteerd die computers en gebruikers.  

Deze detectiemethode is bedoeld om groepen en de groeprelaties van leden van groepen te identificeren. Standaard worden alleen beveiligingsgroepen gedetecteerd. Als u ook vinden het lidmaatschap van distributiegroepen wilt, moet u het selectievakje voor de optie **het lidmaatschap van distributiegroepen detecteren** op de **optie** tabblad de **detectie eigenschappen voor Active Directory-groepen** in het dialoogvenster.  

Detectie van Active Directory-groep biedt geen ondersteuning voor de uitgebreide Active Directory-kenmerken die kunnen worden geïdentificeerd met behulp van Active Directory-Systeemdetectie of Active Directory-Gebruikersdetectie. Omdat deze detectiemethode niet geoptimaliseerd is om computer- en -bronnen te detecteren, overweeg dan deze detectiemethode uitgevoerd nadat u de Active Directory-Systeemdetectie en Active Directory-Gebruikersdetectie hebt uitgevoerd. Dit is omdat deze methode maakt u een volledige detectiegegevensrecord (DDR) voor groepen, maar alleen een beperkte DDR voor computers en gebruikers die lid van groepen zijn.  

U kunt de volgende detectiebereiken die bepalen hoe deze methode wordt gezocht naar informatie configureren:  

-   **Locatie**: Gebruik een locatie als u wilt zoeken naar een of meer Active Directory-containers. Deze bereikoptie ondersteunt een recursief zoeken van de opgegeven Active Directory-containers die ook zoekt naar elke onderliggende container onder de container die u opgeeft. Dit proces wordt vervolgd totdat er geen meer onderliggende containers worden gevonden.  

-   **Groepen**: Groepen gebruiken als u wilt zoeken van een of meer specifieke Active Directory-groepen. U kunt configureren **Active Directory-domein** voor het gebruik van het standaarddomein en forest of zoeken beperken tot een individuele domeincontroller. Bovendien kunt u een of meer groepen om te zoeken. Als u niet ten minste één groep opgeeft, wordt alle groepen gevonden in de opgegeven **Active Directory-domein** locatie worden doorzocht.  

> [!CAUTION]  
>  Wanneer u een detectiebereik configureert, kiest u alleen de groepen die u moet detecteren. Dit is omdat detectie van Active Directory-groep probeert te achterhalen welke elk lid van elke groep in het detectiebereik. Detectie van grote groepen kan uitgebreid gebruik van bandbreedte en Active Directory-bronnen vereisen.  

> [!NOTE]  
>  Uitvoeren voordat u kunt verzamelingen maken die zijn gebaseerd op uitgebreide Active Directory-kenmerken (Zorg ervoor dat nauwkeurige detectieresultaten scanresultaten voor computers en gebruikers), Active Directory-Systeemdetectie of Active Directory-Gebruikersdetectie, afhankelijk van wat u wilt detecteren.  

Acties voor detectie van Active Directory-groep zijn opgenomen in het bestand **adsgdis.log** in de  **&lt;InstallationPath\>\LOGS** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutSystem"></a>Active Directory-Systeemdetectie  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode niet uitvoeren:  

-   **Detectieaccount Active Directory-systeem** (de gebruiker gedefinieerd)  

-   **Computeraccount** van de siteserver  

> [!TIP]  
>  Naast de informatie in deze sectie, Zie [algemene functies van Active Directory-groep, systeem en detectie van gebruikers](#bkmk_shared).  

Deze detectiemethode gebruiken om te zoeken naar de opgegeven Active Directory Domain Services-locaties voor computerbronnen die kunnen worden gebruikt voor het maken van verzamelingen en query's. U kunt de Configuration Manager-client ook installeren op een apparaat gedetecteerde met behulp van push-clientinstallatie.  

Deze methode detecteert standaard basisinformatie over de computer, waaronder het volgende:  

-   Computernaam  

-   Besturingssysteem en versie  

-   Active Directory-containernaam  

-   Het IP-adres  

-   Active Directory-site  

-   Tijdstempel van de laatste aanmelding  

Voor het maken van een DDR voor een computer, moet Active Directory-Systeemdetectie kunnen identificeren van de computeraccount en vervolgens de naam van de computer een IP-adres worden opgelost.  

In de **eigenschappen van Active Directory Discovery** in het dialoogvenster op de **Active Directory-attributen** tabblad vindt u de volledige lijst met standaard-objectkenmerken Active Directory-Systeemdetectie heeft geretourneerd. U kunt ook de methode voor het detecteren van extra (uitgebreid) kenmerken configureren.  

Acties voor detectie van Active Directory-systemen worden vastgelegd in het bestand **adsysdis.log** in de  **&lt;InstallationPath\>\LOGS** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutUser"></a>Detectie Active Directory-gebruikers  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode niet uitvoeren:  

-   **Detectieaccount Active Directory-gebruiker** (de gebruiker gedefinieerd)  

-   **Computeraccount** van de siteserver  

> [!TIP]  
>  Naast de informatie in deze sectie, Zie [algemene functies van Active Directory-groep, systeem en detectie van gebruikers](#bkmk_shared).  

Deze detectiemethode gebruiken om te zoeken in Active Directory Domain Services om gebruikersaccounts en gekoppelde attributen te identificeren. Deze methode detecteert standaard algemene informatie over het gebruikersaccount waaronder de volgende:  

-   Gebruikersnaam  

-   Unieke gebruikersnaam (inclusief de domeinnaam)  

-   Domein  

-   Namen van Active Directory-containers  

In de **eigenschappen van Active Directory Discovery** in het dialoogvenster op de **Active Directory-attributen** tabblad vindt u de volledige standaardlijst van objectattributen die detectie van Active Directory-gebruikers heeft geretourneerd. U kunt ook de methode voor het detecteren van extra (uitgebreid) kenmerken configureren.

Acties voor detectie van Active Directory-gebruiker worden geregistreerd in het bestand **adusrdis.log** in de  **&lt;InstallationPath\>\LOGS** map op de siteserver.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

## <a name="azureaddisc"></a>Azure Active Directory-Gebruikersdetectie
Vanaf versie 1706, kunt u detectie voor gebruikers van Azure Active Directory (Azure AD), wanneer u uw omgeving te gebruiken van Azure-services configureert.
Deze detectiemethode gebruiken om te zoeken van uw Azure AD voor gebruikers die worden geverifieerd met uw exemplaar van Azure AD, vinden de volgende kenmerken:  
-   object-id
-   Weergavenaam
-   E-mail
-   mailNickname
-   onPremisesSecurityIdentifier
-   UserPrincipalName
-   AAD-tenant-id

Deze methode biedt ondersteuning voor een volledige synchronisatie en Deltasynchronisatie van gebruikersgegevens van Azure AD. Deze informatie kan vervolgens gebruikte langs-side-discovery-gegevens die u van de andere detectiemethoden verzamelt worden.

Acties voor Azure AD-Gebruikersdetectie worden opgenomen in het bestand SMS_AZUREAD_DISCOVERY_AGENT.log op de server van de bovenste site van de hiërarchie.

Azure AD-gebruiker om detectie te configureren, moet u de Wizard Azure-Services gebruiken.  Zie voor meer informatie over het configureren van deze detectiemethode [configureren Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/configure-discovery-methods).





##  <a name="bkmk_aboutHeartbeat"></a>Heartbeat-detectie  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Ja  

**Accounts** kunt u deze methode niet uitvoeren:  

-   **Computeraccount** van de siteserver  

Heartbeat-detectie verschilt van andere detectiemethoden Configuration Manager. Dit is standaard ingeschakeld en wordt uitgevoerd op elke computerclient (in plaats van op een siteserver) voor het maken van een DDR. Voor mobiele apparaatclients wordt dit DDR gemaakt door het beheerpunt dat van de client voor mobiele apparaten gebruikmaakt. Om te waarborgen van de databaserecord van Configuration Manager-clients, schakel Heartbeat-detectie niet. Naast de databaserecord onderhouden, wordt met deze methode kan detectie van een computer als een nieuwe bronrecord forceren of kan het databaserecord van een computer die is verwijderd uit de database opnieuw.  

Heartbeat-detectie wordt uitgevoerd op een schema dat is geconfigureerd voor alle clients in de hiërarchie, of als u handmatig wordt aangeroepen, op een specifieke client door het uitvoeren van de **Verzamelfase zoekgegevens** op de **actie** tabblad in de Configuration Manager-programma van een client. Het standaardschema voor Heartbeat-detectie is ingesteld op elke 7 dagen. Als u het interval voor heartbeat-detectie wijzigt, zorg ervoor dat deze wordt vaker dan de siteonderhoudstaak uitgevoerd **verouderde Detectiegegevens verwijderen**, die inactieve clientrecords uit de sitedatabase wist. U kunt de **verouderde Detectiegegevens verwijderen** taak alleen voor primaire sites.  

Wanneer Heartbeat-detectie wordt uitgevoerd, wordt een DDR die actuele informatie van de client heeft gemaakt. De client kopieert deze klein bestand (ongeveer 1 KB groot) naar een beheerpunt dat een primaire site kan worden verwerkt. Het bestand heeft de volgende informatie:  

-   Netwerklocatie  

-   NetBIOS-naam  

-   Versie van de clientagent  

-   Details van de operationele status  

Heartbeat-detectie is de enige detectiemethode die details over de installatiestatus van de client geeft. Dit gebeurt met het bijwerken van het kenmerk en de systeembronclient om in te stellen een waarde gelijk is aan **Ja**.  

> [!NOTE]  
>  Zelfs wanneer Heartbeat-detectie is uitgeschakeld, zijn nog steeds DDR's gemaakt en verzonden voor actieve mobiele apparaatclients. Dit zorgt ervoor dat de **verouderde Detectiegegevens verwijderen** taak heeft geen invloed op actieve mobiele apparaten. Dit gebeurt omdat wanneer de **verouderde Detectiegegevens verwijderen** taak een databaserecord voor een mobiel apparaat wist, trekt het ook het apparaatcertificaat en blokkeert het mobiele apparaat verbinding kunnen maken met beheerpunten.  

Acties voor Heartbeat-detectie zijn geregistreerd in de volgende locaties:  

-   Voor computerclients worden acties van Heartbeat-detectie geregistreerd op de client in de **InventoryAgent.log** bestand de *%Windir%\CCM\Logs* map.  

-   Voor clients van mobiele apparaten, acties van Heartbeat-detectie geregistreerd in de **DMPRP.log** bestand de *% Program Files%\CCM\Logs* map van het beheerpunt dat gebruikmaakt van de client voor mobiele apparaten.  

Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutNetwork"></a>Netwerkdetectie  
**Configureerbare:** Ja  

**Standaard is ingeschakeld:** Nee  

**Accounts** kunt u deze methode niet uitvoeren:  

-   **Computeraccount** van de siteserver  

Gebruik deze methode om de topologie van uw netwerk te detecteren en te detecteren van apparaten in uw netwerk die een IP-adres hebben. Netwerkdetectie doorzoekt uw netwerk naar bronnen IP ingeschakeld door query's op servers met een Microsoft-implementatie van DHCP, ARP Address Resolution Protocol ()-caches in routers, apparaten met SNMP ingeschakeld en Active Directory-domeinen.  

Voordat u netwerkdetectie gebruiken kunt, moet u de *niveau* van detectie moet worden uitgevoerd. U ook configureren een of meer detectiemechanismen die netwerkdetectie aan de query voor netwerksegmenten of apparaten inschakelen. U kunt ook instellingen configureren die detectieacties besturingselement op het netwerk helpen. Tot slot definieert u een of meer planningen voor wanneer netwerkdetectie wordt uitgevoerd.  

Voor deze methode is een resource te detecteren moet netwerkdetectie het IP-adres en het subnetmasker van de bron identificeren. De volgende methoden worden gebruikt voor het identificeren van het subnetmasker van een object:  

-   **Router ARP-cache:** Netwerkdetectie query de ARP-cache van een router om Subnetinformatie te vinden. Gegevens in een router ARP-cache heeft doorgaans een korte tijd-to-live. Daarom wanneer netwerkdetectie een query de ARP-cache, de ARP-cache niet langer mogelijk informatie over het aangevraagde object.  

-   **DHCP:** Netwerkdetectie query elke DHCP-server die u opgeeft voor het detecteren van de apparaten waarvoor de DHCP-server een lease heeft geleverd. Netwerkdetectie ondersteunt alleen DHCP-servers die worden uitgevoerd van de Microsoft-implementatie van DHCP.  

-   **SNMP-apparaat:** Netwerkdetectie kan rechtstreeks query uitvoeren op een SNMP-apparaat. Opdat netwerkdetectie een apparaat, moet het apparaat een lokale SNMP-agent geïnstalleerd hebben. U moet ook netwerkdetectie configureren om te gebruiken van de community-naam die door de SNMP-agent wordt gebruikt.  

Wanneer detectie een object met IP-adres identificeert en subnetmasker van het object kan bepalen, maakt u een DDR voor dat object. Omdat verschillende types apparaten verbinding met het netwerk maken kunnen, kan netwerkdetectie bronnen die ondersteuning voor de Configuration Manager-clientsoftware kunnen niet detecteren. Apparaten die kunnen worden gedetecteerd, maar niet worden beheerd bijvoorbeeld printers en routers.  

Netwerkdetectie kan verschillende kenmerken terugsturen als onderdeel van het detectierecord dat wordt gemaakt. Deze omvatten:  

-   NetBIOS-naam  

-   IP-adressen  

-   Brondomein  

-   Sitesysteemrollen  

-   SNMP-communitynaam  

-   MAC-adressen  

Activiteit van netwerkdetectie wordt geregistreerd in de **Netdisc.log** bestanden per  *&lt;InstallationPath\>\Logs* op de siteserver die detectie uitvoert.  

 Zie voor meer informatie over het configureren van deze detectiemethode [detectiemethoden configureren voor System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

> [!NOTE]  
>  Complexe netwerken en lage bandbreedte kunnen ervoor zorgen dat netwerkdetectie traag wordt uitgevoerd en significant netwerkverkeer genereren. Als een best practice-netwerkdetectie alleen uitvoeren als de andere detectiemethoden kunnen de resources die u hebt voor het detecteren van niet vinden. Gebruik netwerkdetectie bijvoorbeeld als u werkgroepcomputers moet detecteren. Andere detectiemethoden detecteert geen computers in werkgroepen.  

###  <a name="BKMK_NetDiscLevels"></a>Niveaus van netwerkdetectie  
Wanneer u netwerkdetectie configureert, Geef een van drie detectieniveaus:  

|Niveau van detectie|Details|  
|------------------------|-------------|  
|Topologie|Dit niveau detecteert routers en subnetten, maar geeft niet een subnetmasker voor objecten.|  
|Topologie en client|Naast topologie detecteert dit niveau mogelijke clients zoals computers en bronnen, zoals printers en routers. Dit detectieniveau probeert te identificeren van het subnetmasker van objecten die worden gevonden.|  
|Topologie, client- en client-besturingssysteem|Naast topologie en mogelijke clients probeert dit niveau voor het detecteren van de computernaam van het besturingssysteem en versie. Dit niveau maakt gebruik van Windows-Browser en Windows Networking-oproepen.|  

 Met elk incrementeel niveau verhoogt de netwerkdetectie haar activiteit en gebruik van de netwerkbandbreedte. Houd rekening met het netwerkverkeer dat kan worden gegenereerd voordat u alle aspecten van netwerkdetectie inschakelt.  

 Wanneer u netwerkdetectie voor het eerst gebruikt, kunt u bijvoorbeeld bijvoorbeeld voor starten met enkel het topologieniveau om te bepalen van uw netwerkinfrastructuur. Vervolgens kunt u netwerkdetectie voor het detecteren van objecten en hun besturingssystemen van apparaten opnieuw configureren. U kunt ook instellingen configureren die netwerkdetectie tot een specifiek bereik van netwerksegmenten beperken. Op die manier kunt u objecten in netwerklocaties die u nodig hebt en te voorkomen dat onnodig netwerkverkeer en u kunt objecten van randrouters of van detecteren detecteren buiten uw netwerk.  

###  <a name="BKMK_NetDiscOptions"></a>Opties voor netwerkdetectie  
Om netwerkdetectie om te zoeken naar apparaten met een IP-adres, moet u een of meer van de volgende opties die specificeren hoe apparaten worden opgevraagd.  

> [!NOTE]  
>  Netwerkdetectie wordt uitgevoerd in de context van het computeraccount van de siteserver die detectie uitvoert. Als het computeraccount geen machtigingen heeft voor een niet-vertrouwd domein, mislukt het domein en de DHCP server-configuraties om bronnen te detecteren.  

**DHCP:**  

Geef elke DHCP-server dat u netwerkdetectie opvraagt wilt. (Netwerkdetectie ondersteunt alleen DHCP-servers die worden uitgevoerd van de Microsoft-implementatie van DHCP.)  

-   Netwerkdetectie haalt informatie via externe procedureaanroepen weer dat met de database op de DHCP-server.  

-   Netwerkdetectie kan zowel 32-bits en 64-bits DHCP-servers voor een lijst met apparaten die zijn geregistreerd bij elke server opvragen.  

-   Voor netwerkdetectie is een DHCP-server, moet het computeraccount van de server die detectie uitvoert een lid van de groep DHCP-gebruikers op de DHCP-server. Dit toegangsniveau bestaat bijvoorbeeld wanneer een van de volgende voldaan wordt:  

    -   De opgegeven DHCP-server is de DHCP-server van de server die detectie uitvoert.  

    -   De computer die detectie uitvoert en de DHCP-server zich in hetzelfde domein.  

    -   Er bestaat een wederzijdse vertrouwensrelatie tussen de computer die detectie uitvoert en de DHCP-server.  

    -   De siteserver is lid van de groep DHCP-gebruikers.  

-   Wanneer netwerkdetectie een DHCP-server inventariseren, detecteert deze altijd geen statische IP-adressen. Netwerkdetectie vindt geen IP-adressen die deel van een uitgesloten bereik van IP-adressen op de DHCP-server uitmaken. Deze detecteert ook geen IP-adressen die zijn gereserveerd voor handmatige toewijzing.  

**Domeinen:**  

Geef elk domein dat u netwerkdetectie opvraagt wilt.  

-   Het computeraccount van de siteserver die detectie uitvoert, moet leesmachtigingen voor de domeincontrollers in elk opgegeven domein hebben.  

-   Om computers te detecteren van het lokale domein, moet u de Computer Browser-service op ten minste één computer die zich in hetzelfde subnet als de siteserver die netwerkdetectie uitvoert inschakelen.  

-   Netwerkdetectie kan elke computer die u vanop uw siteserver bekijken kunt wanneer u het netwerk bladert detecteren.  

-   Netwerkdetectie haalt het IP-adres en vervolgens gebruikt een Internet Control Message Protocol-echoaanvraag om elk apparaat dat het vindt te pingen. De **ping** opdracht helpt te bepalen welke computers momenteel actief zijn.  

**SNMP-apparaten:**  

Geef elk SNMP-apparaat dat u netwerkdetectie opvraagt wilt.  

-   Netwerkdetectie haalt de ipNetToMediaTable-waarde van elk SNMP-apparaat dat met de query overeenkomt. Deze waarde retourneert matrices van IP-adressen die clientcomputers of andere bronnen zoals printers, routers of andere apparaten met een IP-adres.  

-   Om te vragen een apparaat, moet u de IP-adres of de NetBIOS-naam van het apparaat.  

-   U moet netwerkdetectie voor het gebruik van de community-naam van het apparaat configureren of het apparaat verwerpt de op SNMP gebaseerde query.  

###  <a name="BKMK_LimitNetDisc"></a>Netwerkdetectie beperken  
Wanneer netwerkdetectie een SNMP-apparaat op de rand van uw netwerk opvraagt, kan het informatie over subnetten en SNMP-apparaten die zich buiten uw onmiddellijke netwerk identificeren. Gebruik de volgende informatie voor netwerkdetectie beperken door de SNMP-apparaten te configureren dat de detectie kan communiceren met en op te geven van de netwerksegmenten om op te vragen.  

**Subnetten:**  

Configureer de subnetten die netwerkdetectie opvraagt wanneer het de SNMP- en DHCP-opties gebruikt. Deze twee opties zoeken alleen de ingeschakelde subnetten.  

Een DHCP-aanvraag kan apparaten bijvoorbeeld terugsturen vanuit locaties binnen uw volledige netwerk. Als u wilt dat alleen apparaten op een specifiek subnet te detecteren, geef en schakel dan dat specifieke subnet in de **subnetten** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster. Wanneer u subnetten geeft en inschakelt, beperkt u toekomstige DHCP- en SNMP-detectie taken bij deze subnetten.  

> [!NOTE]  
>  Subnetconfiguraties beperken niet de objecten die de **domeinen** optie domeindetectie detecteert.  

**SNMP-communitynamen:**  

Om netwerkdetectie worden opgevraagd een SNMP-apparaat, moet u netwerkdetectie configureren met de communitynaam van het apparaat. Als netwerkdetectie niet is geconfigureerd met behulp van de community-naam van het SNMP-apparaat, verwerpt het apparaat de query.  

**Maximum aantal hops:**  

Wanneer u het maximum aantal router-hops configureert, beperkt u het aantal netwerksegmenten en routers die netwerkdetectie opvragen kan via SNMP.  

Het aantal hops dat u configureert, beperkt het aantal bijkomende apparaten en netwerksegmenten dat netwerkdetectie kan opvragen.  

Bijvoorbeeld, een alleen-topologie-detectie met **0** (nul) router-hops detecteert het subnet waarop de oorspronkelijke server zich bevindt. Dit omvat alle routers in dat subnet.  

Het volgende diagram toont wat een topologie-alleen netwerkdetectie query vindt wanneer ze op Server 1 uitvoert met 0 router-hops opgegeven: subnet D en Router 1.  

 ![Afbeelding van detectie met nul jump router](media/Disc-0.gif)  

 Het volgende diagram toont wat een topologie en client netwerkdetectie query vindt wanneer ze op Server 1 met 0 gespecificeerde router-hops uitvoert: subnet D en Router 1 en alle potentiële clients op subnet D.  

 ![Afbeelding van detectie met één router gaan](media/Disc-1.gif)  

 Als u een beter idee krijgen van hoe bijkomende router hops kunnen vergroten de hoeveelheid netwerkbronnen die zijn gedetecteerd, kunt u overwegen het volgende netwerk:  

 ![Afbeelding van detectie met twee router jumps](media/Disc-2.gif)  

 Een topologie-alleen netwerkdetectie vanaf Server 1 uitgevoerd met één router-hops detecteert het volgende:  

-   Router 1 en subnet 10.1.10.0 (gevonden met nul hops)  

-   Subnetten 10.1.20.0 en 10.1.30.0, subnet A en Router 2 (gevonden op de eerste hop)  

> [!WARNING]  
>  Elke toename van het aantal router-hops kan aanzienlijk Verhoog het aantal detecteerbare bronnen en verhogen van de netwerkbandbreedte die netwerkdetectie gebruikt.  

##  <a name="bkmk_aboutServer"></a>Serverdetectie  
**Configureerbare:** Nee  

Naast de gebruiker configureerbare detectiemethoden maakt Configuration Manager maakt gebruik van een proces met de naam **serverdetectie** (SMS_WINNT_SERVER_DISCOVERY_AGENT). Deze detectiemethode maakt bronrecords voor computers die sitesystemen, zoals een computer die is geconfigureerd als een beheerpunt.  

##  <a name="bkmk_shared"></a>Algemene functies van Active Directory Group Discovery-Systeemdetectie en detectie van gebruikers  
Deze sectie bevat informatie over functies die gemeenschappelijk voor de volgende detectiemethoden zijn:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

> [!NOTE]  
>  De informatie in deze sectie geldt niet voor de detectie van Active Directory-Forest.  

Deze drie detectiemethoden zijn vergelijkbaar in configuratie en werking. Ze kunnen computers, gebruikers en informatie over groepslidmaatschappen van bronnen die zijn opgeslagen in Active Directory Domain Services detecteren. Het detectieproces wordt beheerd door een detectieagent die wordt uitgevoerd op de siteserver op elke site waarvoor detectie is geconfigureerd om uit te voeren. U kunt elk van deze detectiemethoden om te zoeken naar een of meer Active Directory-locaties zoals locatie-instanties in de lokale of externe forests te configureren.  

Wanneer detectie een niet-vertrouwd forest voor bronnen zoekt, moet de detectieagent kunnen omzetten van de volgende succesvol zijn:  

-   Voor het detecteren van de computerbron van een met behulp van Active Directory System Discovery, moet de detectieagent kunnen omzetten van de FQDN-naam van de resource. Als de FQDN-naam kan niet worden omgezet, probeer het omzetten van de resource met de NetBIOS-naam.  

-   Als u wilt een gebruiker of groepsbron detecteren met behulp van detectie van Active Directory-gebruikers of Active Directory Group Discovery, moet de detectieagent kunnen omzetten van de FQDN van de domeincontrollernaam die u voor de Active Directory-locatie opgeeft.  

Voor elke locatie die u opgeeft, kunt u individuele zoekopties, zoals het inschakelen van een recursieve zoekopdracht van de locatie onderliggende Active Directory-containers. U kunt ook een uniek account moet worden gebruikt wanneer er wordt gezocht naar die locatie configureren. Dit geeft flexibiliteit bij het configureren van een detectiemethode op één site om te zoeken van meerdere Active Directory-locaties voor meerdere forests zonder dat voor het configureren van een enkel account dat over machtigingen voor alle locaties beschikt.  

Wanneer elk van deze drie detectiemethoden op een specifieke site wordt uitgevoerd, wordt de Configuration Manager-siteserver op die site contact met de dichtstbijzijnde domeincontroller in het opgegeven Active Directory-forest om Active Directory-bronnen te vinden. Het domein en forest kunnen zich in eender welke ondersteunde Active Directory-modus. Het account dat u aan elk locatie-exemplaar toewijst moet hebben **lezen** toegangsmachtiging voor de gespecificeerde Active Directory-locaties.

Detectie zoekt de opgegeven locaties voor objecten en probeert vervolgens informatie verzamelen over die objecten. Een DDR wordt gemaakt wanneer er voldoende informatie over een bron kan worden geïdentificeerd. De vereiste gegevens varieert afhankelijk van de detectiemethode die wordt gebruikt.  

Als u dezelfde detectiemethode om uit te voeren op verschillende sites van Configuration Manager om te profiteren van query's op lokale Active Directory-servers configureert, kunt u elke site configureren met een unieke set van detectieopties. Omdat detectiegegevens wordt gedeeld met elke site in de hiërarchie, voorkomen dat u overlapping tussen deze configuraties om efficiënt elke bron één keer detecteren.

U kunt voor kleinere omgevingen overwegen uitgevoerd elke detectiemethode op slechts één site in uw hiërarchie om administratieve overhead en de mogelijkheden voor meerdere detectieacties dezelfde bronnen opnieuw detecteren te verminderen. Wanneer u het aantal sites dat detectie uitvoeren, u de totale netwerkbandbreedte die detectie beperken kunt minimaliseren wordt gebruikt. U kunt ook het totale aantal DDR's die zijn gemaakt en moeten worden verwerkt door uw siteservers beperken.  

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

Detectie van verschillen is geen een onafhankelijke detectiemethode maar een optie die beschikbaar zijn voor de detectiemethodes van toepassing. Detectie van verschillen zoekt specifieke Active Directory-kenmerken voor wijzigingen die zijn aangebracht sinds de laatste volledige detectiecyclus van de toepasselijke detectiemethode. De kenmerkwijzigingen worden verzonden naar de Configuration Manager-database bijwerken van de detectierecord van de resource.  

Detectie van verschillen wordt standaard uitgevoerd op een cyclus van vijf minuten. Dit is een veel hoger zijn dan het standaard schema voor een volledige detectiecyclus.  Deze cyclus frequente is mogelijk omdat detectie van verschillen minder siteserver gebruikt en netwerkbronnen dan een volledige detectiecyclus komt. Wanneer u detectie van verschillen gebruikt, kunt u de frequentie van de volledige detectiecyclus voor die detectiemethode te reduceren.  

Hier volgen de meest voorkomende wijzigingen die detectie van verschillen detecteert:  

-   Nieuwe computers of gebruikers die zijn toegevoegd aan Active Directory  

-   Wijzigingen in basisinformatie computer en gebruiker  

-   Nieuwe computers of gebruikers die zijn toegevoegd aan een groep  

-   Computers of gebruikers die zijn verwijderd uit een groep  

-   Wijzigingen in de systeemgroepsobjecten  

Hoewel detectie van verschillen nieuwe resources en wijzigingen aan groepslidmaatschap detecteren kan, kan deze niet detecteren wanneer een bron is verwijderd uit Active Directory. DDR's die zijn gemaakt door de detectie van verschillen, worden verwerkt op dezelfde manier als de DDR's die zijn gemaakt door een volledige detectiecyclus.  

U configureert detectie van verschillen op de **Polling-planning** tabblad in de eigenschappen voor elke detectiemethode.  

###  <a name="bkmk_stalelogon"></a>Verouderde computerrecords filteren op aanmelden bij domein  
Beschikbaar voor:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

U kunt detectie configureren zodat computers uitsluiten met verouderde computerrecords op basis van de laatste domeinaanmelding van de computer. Wanneer deze optie is ingeschakeld, beoordeelt Active Directory-Systeemdetectie elke computer die wordt geïdentificeerd. Detectie van Active Directory-groepen beoordeelt elke computer die lid is van een groep die wordt gedetecteerd.  

Deze optie wilt gebruiken:  

-   Computers moeten worden geconfigureerd voor het bijwerken van de **lastLogonTimeStamp** kenmerk in Active Directory Domain Services.  

-   Het functionele niveau van het Active Directory-domein moet worden ingesteld op Windows Server 2003 of hoger.  

Bij het configureren van de tijd die na de laatste aanmelding die u wilt gebruiken voor deze instelling, overweeg dan het interval voor replicatie tussen domeincontrollers.  

U configureert filtering op het **optie** tabblad de **eigenschappen van Active Directory Discovery** en **detectie eigenschappen voor Active Directory-groepen** dialoogvensters. Kies de optie **alleen computers detecteren die zijn aangemeld bij een domein in een bepaalde periode**.  

> [!WARNING]  
>  Wanneer u dit filter configureert en **verlopen records filteren op computerwachtwoord**, computers die voldoen aan de criteria van een filter zijn uitgesloten van detectie.  

###  <a name="bkmk_stalepassword"></a>Verlopen records filteren op computerwachtwoord  
Beschikbaar voor:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

U kunt detectie configureren zodat computers uitsluiten met verouderde computerrecords op basis van de laatste update van computer account wachtwoord door de computer. Wanneer deze optie is ingeschakeld, beoordeelt Active Directory-Systeemdetectie elke computer die wordt geïdentificeerd. Detectie van Active Directory-groepen beoordeelt elke computer die lid is van een groep die wordt gedetecteerd.  

Deze optie wilt gebruiken:  

-   Computers moeten worden geconfigureerd voor het bijwerken van de **pwdLastSet** kenmerk in Active Directory Domain Services.  

Wanneer u deze optie configureert, houd rekening met het interval voor updates voor dit attribuut, alsook de replicatie-interval tussen domeincontrollers.  

U configureert filtering op het **optie** tabblad de **eigenschappen van Active Directory Discovery** en **detectie eigenschappen voor Active Directory-groepen** dialoogvensters. Kies de optie **alleen computers detecteren die wachtwoord van computeraccount hebben bijgewerkt in een bepaalde periode**.  

> [!WARNING]  
>  Wanneer u dit filter configureert en **verlopen records filteren op aanmelden bij domein**, computers die voldoen aan de criteria van een filter zijn uitgesloten van detectie.  

###  <a name="bkmk_customAD"></a>Aangepaste kenmerken voor Active Directory zoeken  
 Beschikbaar voor:  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

Elke detectiemethode ondersteunt een unieke lijst van Active Directory-attributen die kunnen worden gedetecteerd.  

U kunt bekijken en configureren van de lijst met aangepaste kenmerken op het **Active Directory-attributen** tabblad de **eigenschappen van Active Directory Discovery** en **eigenschappen van Active Directory Discovery** dialoogvensters.  
