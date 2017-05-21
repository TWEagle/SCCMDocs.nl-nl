---
title: Configureren van detectie | Microsoft-documenten
description: Configureren van detectiemethoden gebruiken om uit te voeren op een Configuration Manager-site om te zoeken naar bronnen die u vanaf uw netwerkinfrastructuur en Active Directory beheren kunt.
ms.custom: na
ms.date: 2/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49505eb1-d44d-4121-8712-e0f3d8b15bf5
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 860815010068422f2d8854ed2d574c24cc386891
ms.openlocfilehash: 63a3c2ef66c80d1da9b50e67166a2196cf1b081b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="configure-discovery-methods-for-system-center-configuration-manager"></a>Detectiemethoden configureren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Configureren van detectiemethoden gebruiken om uit te voeren op een System Center Configuration Manager-site om te zoeken naar bronnen die u van uw netwerkinfrastructuur en Active Directory beheren kunt. Hiervoor moet u inschakelen en vervolgens configureren elke methode die u wilt gebruiken om te zoeken in uw omgeving. (U kunt ook een methode uitschakelen met behulp van dezelfde procedure die u gebruikt in te schakelen.)  De enige uitzondering hierop zijn Heartbeat-detectie en -Server:  

-   Standaard Heartbeat-detectie is al ingeschakeld tijdens de installatie van een primaire site van Configuration Manager en geconfigureerd op basis van een eenvoudige planning wordt uitgevoerd. Er is een goed idee Heartbeat-detectie ingeschakeld omdat het ervoor zorgt dat de detectiegegevensrecords (DDR's) voor apparaten up-to-date te houden. Zie voor meer informatie over Heartbeat-detectie [over Heartbeat-detectie](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutHeartbeat).  

-   Serverdetectie is een automatische detectiemethode die zoeken naar computers die u als site-systemen gebruikt. Configureren kan of uitschakelen.  

**Alle configureerbare detectiemethode inschakelen:**  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Selecteer de detectiemethode voor de site waar u detectie wilt inschakelen.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**, en klik vervolgens op de **algemeen** tabblad controle van de **inschakelen&lt;detectiemethode\>**  vak.  

     Als dit selectievakje al is ingeschakeld, kunt u de detectiemethode uitschakelen door het selectievakje uitschakelt.  

4.  Kies **OK** aan de configuratie op te slaan.  


##  <a name="BKMK_ConfigADForestDisc"></a>Detectie van Active Directory-forests configureren  
Voor het voltooien van de configuratie van detectie van Active Directory-Forest, moet u instellingen configureren op twee locaties:  

-   In de **detectiemethoden** knooppunt, kunt u:

    - Deze detectiemethode inschakelen.
    - Een polling-planning instellen.
    - Selecteer of detectie automatisch grenzen maakt voor de Active Directory-sites en subnetten die het detecteert.  

-   In de **Active Directory-Forests** knooppunt, kunt u:

    - Forests toevoegen die u wilt detecteren.
    - Detectie van Active Directory-sites en subnetten in dat forest inschakelen.
    - Instellingen configureren om Configuration Manager-sites hun sitegegevens publiceren naar het forest.
    - Een account gebruikt als de Active Directory-Forestaccount voor elke forest toewijzen.  

Gebruik de volgende procedures om in te schakelen van detectie van Active Directory-forests en om afzonderlijke forests voor gebruik met Active Directory-Forestdetectie.  

#### <a name="to-enable-active-directory-forest-discovery"></a>Detectie van Active Directory-forests inschakelen  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Selecteer de methode Active Directory-Forestdetectie voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemeen** tabblad, schakel het selectievakje in om in te schakelen van detectie. Of nu de configuratie van detectie en keer vervolgens terug om in te schakelen detectie later.  

5.  Geef opties op het maken van sitegrenzen voor gedetecteerde locaties.  

6.  Geef een schema voor wanneer detectie wordt uitgevoerd.  

7.  Als u klaar bent met de configuratie van Active Directory-Forestdetectie voor deze site, kiest u **OK** aan de configuratie op te slaan.  

#### <a name="to-configure-a-forest-for-active-directory-forest-discovery"></a>Een forest configureren voor detectie van Active Directory-forests  

1.  In de **beheer** werkruimte kiezen **Active Directory-Forests**. Als Active Directory-forestdetectie eerder is uitgevoerd, ziet u iedere gedetecteerde forest in het resultatenvenster. De lokale forest en vertrouwde forests worden gedetecteerd wanneer Active Directory-forestdetectie wordt uitgevoerd. U kunt niet-vertrouwde forests alleen handmatig toevoegen.  

    -   Als u wilt een eerder gedetecteerd forest wilt configureren, selecteert u het forest in het deelvenster met resultaten. Klik vervolgens op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen** om de foresteigenschappen te openen. Ga door met stap 3.  

    -   Configureren van een nieuw forest die niet wordt vermeld, op de **Start** tabblad, in de **maken** groep, kiest u **Forest toevoegen** openen van de **Forests toevoegen** in het dialoogvenster. Ga door met stap 3.  

2.  Op de **algemeen** tabblad, het voltooien van de configuraties voor het forest dat u wilt detecteren, en geef de **Active Directory-Forestaccount**.  

    > [!NOTE]  
    >  Voor Active Directory-forestdetectie is een globaal account nodig om niet-vertrouwde forests te detecteren en ernaar te publiceren. Als u het computeraccount van de siteserver niet gebruikt, kunt u alleen een globaal account selecteren.  

3.  Als u van plan bent om sites sitegegevens naar dit forest te publiceren op de **Publishing** tabblad, het voltooien van de configuraties in voor publicatie naar dit forest.  

    > [!NOTE]  
    >  Als u sites publiceren naar een forest, moet u het Active Directory-schema van dit forest uitbreiden voor Configuratiebeheer. De Active Directory-Forestaccount moet machtigingen voor volledig beheer voor de systeemcontainer in dat forest hebben.  

4.  Als u klaar bent met de configuratie van deze forest voor Active Directory-Forestdetectie, kiest u **OK** aan de configuratie op te slaan.  

##  <a name="BKMK_ConfigADDiscGeneral"></a>Detectie van Active Directory voor computers, gebruikers of groepen configureren  
 Gebruik de informatie in de volgende secties voor het configureren van detectie van computers, gebruikers of groepen. U moet deze detectiemethoden gebruiken:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

> [!NOTE]  
>  De informatie in deze sectie is niet van toepassing op detectie van Active Directory-forests.  

 Hoewel elk van deze detectiemethoden onafhankelijk van de andere, delen ze wel soortgelijke opties. Zie voor meer informatie over deze configuratieopties [gedeeld opties voor de detectie van groep-, systeem- en gebruiker](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_shared).  

> [!WARNING]  
>  Polling van Active Directory door elk van deze detectiemethodes kan aanzienlijk netwerkverkeer genereren. Overweeg iedere detectiemethode te worden uitgevoerd op een tijdstip waarop dit netwerkverkeer geen belemmering zakelijke gebruik van uw netwerk vormt plannen.  

#### <a name="to-configure-active-directory-group-discovery"></a>Detectie van Active Directory-groepen configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies de **Active Directory Group Discovery** methode voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemeen** tabblad, schakel het selectievakje in om in te schakelen van detectie. Of nu de configuratie van detectie en keer vervolgens terug om in te schakelen detectie later.  

5.  Kies **toevoegen** om een detectiebereik configureert, kiest u **groepen** of **locatie**, en voltooit u de volgende configuraties in de **groepen toevoegen** of **Active Directory-locatie toevoegen** in het dialoogvenster:  

    1.  Geef een **naam** voor dit detectiebereik.  

    2.  Geef een **Active Directory-domein** of **locatie** om te zoeken:  

        -   Als u hebt gekozen **groepen**, geeft u een of meer Active Directory-groepen moeten worden gedetecteerd.  

        -   Als u hebt gekozen **locatie**, geeft u een Active Directory-container als locatie moeten worden gedetecteerd. U kunt ook een recursieve zoekopdracht van onderliggende Active Directory-containers voor deze locatie inschakelen.  

    3.  Geef de **Detectieaccount Active Directory-groepen** die wordt gebruikt om dit detectiebereik te zoeken.  

    4.  Kies **OK** om op te slaan van de configuratie van het detectiebereik.  

6.  Herhaal stap 6 voor ieder extra detectiebereik dat u wilt definiëren.  

7.  Op de **Polling-planning** tabblad, configureert u de volledige detectiepolling-planning en deltadetectie.  

8.  Klik desgewenst op de **optie** tabblad kunt u opties kunt uitfilteren of verouderde computerrecords uitsluiten van detectie en het lidmaatschap van distributiegroepen te detecteren.  

    > [!NOTE]  
    >  Detectie van Active Directory-groepen detecteert standaard alleen het lidmaatschap van beveiligingsgroepen.  

9. Als u klaar bent met het configureren van detectie van Active Directory-groepen voor deze site, kiest u **OK** aan de configuratie op te slaan.  

#### <a name="to-configure-active-directory-system-discovery"></a>Active Directory System Discovery configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Selecteer de methode voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemeen** tabblad, schakel het selectievakje in om in te schakelen van detectie. Of nu de configuratie van detectie en keer vervolgens terug om in te schakelen detectie later.  

5.  Kies de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) om op te geven van een nieuwe Active Directory-container. In de **Active Directory-Container** dialoogvenster vak, voltooien van de volgende configuraties:  

    1.  Geef een of meer zoeklocaties op.  

    2.  Geef opties op die het zoekgedrag wijzigen voor elke locatie.  

    3.  Geef voor elke locatie het account wilt gebruiken als de **Active Directory Discovery-Account**.  

        > [!TIP]  
        >  Voor elke locatie die u opgeeft, kunt u een set van detectieopties en een uniek Active Directory Discovery-Account configureren.  

    4.  Kies **OK** om op te slaan van de configuratie van de Active Directory-container.  

6.  Op de **Polling-planning** tabblad, configureert u de volledige detectiepolling-planning en deltadetectie.  

7.  Klik desgewenst op de **Active Directory-attributen** tabblad kunt u aanvullende Active Directory-attributen voor computers die u wilt detecteren. De standaard-objectkenmerken worden ook weergegeven.  

8.  Klik desgewenst op de **optie** tabblad kunt u opties om te filteren of verouderde computerrecords uitsluiten van detectie.  

9. Als u klaar bent met het configureren van detectie van Active Directory-systemen voor deze site, kiest u **OK** aan de configuratie op te slaan.  

#### <a name="to-configure-active-directory-user-discovery"></a>Detectie van Active Directory-gebruikers configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies de **Active Directory User Discovery** methode voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemeen** tabblad, schakel het selectievakje in om in te schakelen van detectie. Of nu de configuratie van detectie en keer vervolgens terug om in te schakelen detectie later.  

5.  Kies de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) om op te geven van een nieuwe Active Directory-container. In de **Active Directory-Container** dialoogvenster vak, voltooien van de volgende configuraties:  

    1.  Geef een of meer zoeklocaties op.  

    2.  Geef opties op die het zoekgedrag wijzigen voor elke locatie.  

    3.  Geef voor elke locatie het account wilt gebruiken als de **Active Directory Discovery-Account**.  

        > [!NOTE]  
        >  Voor elke locatie die u opgeeft, kunt u een unieke set van detectieopties en een uniek Active Directory Discovery-Account configureren.  

    4.  Kies **OK** om op te slaan van de configuratie van de Active Directory-container.  

6.  Op de **Polling-planning** tabblad, configureert u de volledige detectiepolling-planning en deltadetectie.  

7.  Klik desgewenst op de **Active Directory-attributen** tabblad kunt u aanvullende Active Directory-attributen voor computers die u wilt detecteren. De standaard-objectkenmerken worden ook weergegeven.  

8.  Als u klaar bent met het configureren van detectie van Active Directory-gebruikers voor deze site, kiest u **OK** aan de configuratie op te slaan.  

##  <a name="BKMK_ConfigHBDisc"></a>Heartbeat-detectie configureren  
 Heartbeat-detectie is standaard ingeschakeld wanneer u een primaire site van Configuration Manager installeert. Als gevolg hiervan, hoeft u alleen het schema te configureren voor hoe vaak clients verzenden de Heartbeat-detectie-gegevens naar een beheerpunt opnemen wanneer u niet wilt gebruiken, de standaardwaarde van zeven dagen.  

> [!NOTE]  
>  Als zowel client-pushinstallatie en de siteonderhoudstaak voor **Installatievlag** zijn ingeschakeld op dezelfde site, zet u het schema voor Heartbeat-detectie op korter dan de **periode Herdetectie Client** van de **Installatievlag** siteonderhoudstaak. Zie voor meer informatie over siteonderhoudstaken [onderhoudstaken voor System Center Configuration Manager](../../../../core/servers/manage/maintenance-tasks.md).  

#### <a name="to-configure-the-heartbeat-discovery-schedule"></a>De planning voor Heartbeat-detectie configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies **Heartbeat-detectie** voor de site waar u Heartbeat-detectie configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Configureer de frequentie waarmee clients Heartbeat-detectierecord gegevens verzenden en kies vervolgens **OK** aan de configuratie op te slaan.  

##  <a name="BKMK_ConfigNetworkDisc"></a>Netwerkdetectie configureren  
 Gebruik de informatie in de volgende secties voor hulp bij het configureren van netwerkdetectie.  

###  <a name="BKMK_AboutConfigNetworkDisc"></a>Over het configureren van netwerkdetectie  
 Voordat u netwerkdetectie configureert, moet u de volgende begrijpen:  

-   Beschikbare niveaus van netwerkdetectie  

-   Beschikbare opties voor netwerkdetectie  

-   Beperken van netwerkdetectie op het netwerk  

Zie voor meer informatie [over netwerkdetectie](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutNetwork).  

 De volgende secties bevatten informatie over algemene configuraties voor netwerkdetectie. Configureert u een of meerdere van deze configuraties voor gebruik tijdens dezelfde detectierun. Als u meerdere configuraties gebruikt, u moet de interacties plannen die de detectieresultaten kunnen beïnvloeden.  

 U wilt bijvoorbeeld alle Simple Network Management Protocol (SNMP) ook apparaten gedetecteerd die een specifieke SNMP-communitynaam gebruiken. Daarnaast voor dezelfde detectierun, uitschakelen u detectie op een specifiek subnet. Wanneer detectie wordt uitgevoerd, detecteert netwerkdetectie geen SNMP-apparaten met de opgegeven communitynaam op het subnet dat u hebt uitgeschakeld.  

####  <a name="BKMK_DetermineNetTopology"></a>Uw netwerktopologie bepalen  
 Alleen-topologie detectie kunt u uw netwerk worden toegewezen. Dit type detectie detecteert geen potentiële clients. De topologie-alleen netwerkdetectie is afhankelijk van SNMP.  

 Wanneer u uw netwerktopologie toewijzen wilt, moet u de **Maximum hops** op de **SNMP** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster. Slechts enkele hops kunt u de netwerkbandbreedte regelen die wordt gebruikt wanneer detectie wordt uitgevoerd. Naarmate u meer van uw netwerk ontdekt, kunt u het aantal hops opvoeren een beter begrip te vormen van uw netwerktopologie om verhogen.  

 Nadat u inzicht in uw netwerktopologie, kunt u extra eigenschappen configureren voor netwerkdetectie om potentiële clients en hun besturingssystemen detecteren terwijl u beschikbare configuraties gebruikt om de netwerksegmenten dat netwerkdetectie kan zoeken te beperken.  

####  <a name="BKMK_LimitBySubnet"></a>Zoekopdrachten beperken met behulp van subnetten  
 U kunt netwerkdetectie configureren om te zoeken naar specifieke subnetten tijdens een detectierun. Netwerkdetectie doorzoekt standaard het subnet van de server die detectie uitvoert. Eventuele extra subnetten die u configureert en inschakelt gelden alleen voor SNMP- en Dynamic Host Configuration Protocol (DHCP) zoekopties. Wanneer netwerkdetectie domeinen zoekt, wordt het niet beperkt door subnetconfiguraties.  

 Als u een of meerdere subnetten opgeeft op het **subnetten** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster alleen de subnetten die zijn gemarkeerd als **ingeschakeld** worden doorzocht.  

 Als u een subnet uitschakelt, wordt het van detectie uitgesloten en gelden de volgende voorwaarden:  

-   SNMP-query's worden niet uitgevoerd op het subnet.  

-   DHCP-servers reageren niet met een lijst met bronnen die zich bevinden op het subnet.  

-   Domain-query's kunnen bronnen detecteren die op het subnet.  

####  <a name="BKMK_SearchByDomain"></a>Zoeken in een specifiek domein  
 U kunt netwerkdetectie configureren om te zoeken in een specifiek domein of set van domeinen tijdens het uitvoeren van een detectie. Netwerkdetectie doorzoekt standaard het lokale domein van de server die detectie uitvoert.  

 Als u een of meer domeinen specificeert op het **domeinen** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster alleen de domeinen die zijn gemarkeerd als **ingeschakeld** worden doorzocht.  

 Wanneer u een domein uitschakelt, wordt het van detectie uitgesloten en gelden de volgende voorwaarden:  

-   Netwerkdetectie voert geen query's domeincontrollers in dat domein.  

-   SNMP-query's kunnen nog steeds uitgevoerd worden op subnetten in het domein.  

-   DHCP-servers kunnen nog steeds antwoorden met een lijst met bronnen die zich bevinden in het domein.  

####  <a name="BKMK_LimitBySNMPname"></a>Beperk zoekopdrachten door SNMP-communitynamen te gebruiken  
 U configureren netwerkdetectie om te zoeken in een specifieke SNMP-community of set van communities tijdens het uitvoeren van een detectie. Standaard wordt de communitynaam van **openbare** is geconfigureerd voor gebruik.  

 Netwerkdetectie gebruikt communitynamen om toegang tot routers die SNMP-apparaten te krijgen. Een router kan netwerkdetectie voorzien informatie over andere routers en subnetten die met de eerste router verbonden zijn.  

> [!NOTE]  
>  SNMP-communitynamen lijken op wachtwoorden. Netwerkdetectie kan enkel informatie krijgen van een SNMP-apparaat waarvoor u een communitynaam heb gespecificeerd. Elk SNMP-apparaat kan zijn eigen communitynaam hebben, maar dikwijls wordt dezelfde comunitynaam gedeeld tussen verschillende apparaten. Bovendien hebben de meeste SNMP-apparaten een standaardnaam **openbare**. Sommige organisaties wissen, maar de **openbare** communitynaam vanaf hun apparaten veiligheidsoverwegingen.  

 Als meerdere SNMP-communities worden weergegeven op de **SNMP** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster zoekt netwerkdetectie ze in de volgorde waarin ze worden weergegeven. Om te helpen het netwerkverkeer dat wordt gegenereerd door pogingen om contact op met een apparaat met behulp van verschillende namen te minimaliseren, zorg ervoor dat de meest gebruikte namen aan de bovenkant van de lijst.  

> [!NOTE]  
>  Naast het gebruik van de SNMP-communitynaam, kunt u het IP-adres of herleidbare naam van een specifiek SNMP-apparaat. U kunt hiervoor op de **SNMP-apparaten** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster.  

####  <a name="BKMK_SearchByDHCP"></a>Zoeken in een specifieke DHCP-server  
 U kunt netwerkdetectie configureren om te gebruiken van een specifieke DHCP-server of meerdere servers voor het detecteren van DHCP-clients tijdens de uitvoering van een detectie.  

 Netwerkdetectie doorzoekt elke DHCP-server die u opgeeft op het **DHCP** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster. Als de server die detectie uitvoert zijn IP-adres van een DHCP-server huurt, u kunt detectie configureren zodat deze DHCP-server zoeken door te controleren of de **de DHCP-server opnemen waarvoor de siteserver is geconfigureerd voor gebruik** vak.  

> [!NOTE]  
>  Om te kunnen configureren een DHCP-server in netwerkdetectie, moet uw omgeving IPv4 ondersteunen. U kunt netwerkdetectie voor het gebruik van een DHCP-server in een native IPv6-omgeving niet configureren.  

###  <a name="BKMK_HowToConfigNetDisc"></a>Het configureren van netwerkdetectie  
 Gebruik de volgende procedures om eerst enkel uw netwerktopologie te detecteren en configureer dan netwerkdetectie om potentiële clients detecteren met behulp van een of meer van de beschikbare opties voor netwerkdetectie.  

##### <a name="to-determine-your-network-topology"></a>Uw netwerktopologie bepalen  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies **netwerkdetectie** voor de site waar u netwerkdetectie uitvoert.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

    -   Op de **algemeen** tabblad controle van de **Netwerkdetectie inschakelen** vak en kies vervolgens **topologie** van de **Type detectie** opties.  

    -   Op de **subnetten** tabblad controle van de **lokale subnetten doorzoeken** vak.  

        > [!TIP]  
        >  Als u de specifieke subnetten waaruit uw netwerk, schakelt u de **lokale subnetten doorzoeken** vak en gebruik de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) toevoegen van de specifieke subnetten die u wilt zoeken. Voor grote netwerken is het dikwijls het beste slechts één of twee subnetten doorzoeken om het gebruik van netwerkbandbreedte te minimaliseren.  

    -   Op de **domeinen** tabblad controle van de **lokale domeinen doorzoeken** vak.  

    -   Op de **SNMP** tabblad, gebruikt u de **Maximum hops** vervolgkeuzelijst om te specificeren hoeveel routerhops Netwerkdetectie kan nemen in kaart brengen van uw topologie.  

        > [!TIP]  
        >  Wanneer u eerst uw netwerktopologie in kaart, configureert u slechts enkele routerhops om het gebruik van netwerkbandbreedte te minimaliseren.  

4.  Op de **schema** Kies de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) het instellen van een planning voor het uitvoeren van netwerkdetectie.  

    > [!NOTE]  
    >  U kunt geen andere detectieconfiguratie netwerkdetectieplannings te scheiden niet toewijzen. Elke keer dat netwerkdetectie wordt uitgevoerd, gebruikt ze de huidige detectieconfiguratie.  

5.  Kies **OK** om de configuraties te aanvaarden. Netwerkdetectie wordt uitgevoerd op het geplande tijdstip.  

##### <a name="to-configure-network-discovery"></a>Netwerkdetectie configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies **netwerkdetectie** voor de site waar u netwerkdetectie uitvoert.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemeen** tabblad controle van de **Netwerkdetectie inschakelen** vak en selecteer vervolgens het type van detectie dat u uitvoeren wilt van de **Type detectie** opties.  

5.  Om detectie te configureren om te zoeken subnetten, kies de **subnetten** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Detectie op subnetten die lokaal op de computer die detectie uitvoert zijn uitgevoerd, controleert u de **lokale subnetten doorzoeken** vak.  

    -   Om te zoeken naar een specifiek subnet, zorg ervoor dat het subnet wordt vermeld **te doorzoeken subnetten** en heeft een **zoeken** waarde van **ingeschakeld**:  

        1.  Als het subnet niet wordt vermeld, kiest u de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuwe Subnettoewijzing** dialoogvenster, voert u de **Subnet** en **masker** informatie, en kies vervolgens **OK**. Een nieuw subnet is standaard ingeschakeld voor de zoekopdracht.  

        2.  Wijzigen van de **zoeken** waarde voor een subnet in de lijst, selecteert u het subnet en kies de **in-/ uitschakelen** pictogram overschakelen van de waarde tussen **uitgeschakeld** en **ingeschakeld**.  

6.  Om detectie te configureren om te zoeken naar domeinen, kies de **domeinen** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Het uitvoeren van detectie op het domein van de computer die detectie uitvoert, controleert u de **lokale domeinen doorzoeken** vak.  

    -   Om te zoeken naar een specifiek domein, zorg ervoor dat het domein wordt vermeld **domeinen** en heeft een **zoeken** waarde van **ingeschakeld**:  

        1.  Als het domein niet wordt vermeld, kiest u de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **eigenschappen voor domein** dialoogvenster, voert u de **domein** informatie, en kies vervolgens **OK**. Een nieuw domein is standaard ingeschakeld voor de zoekopdracht.  

        2.  Wijzigen van de **zoeken** waarde voor een domein in de lijst, selecteert u het domein en kies de **in-/ uitschakelen** pictogram overschakelen van de waarde tussen **uitgeschakeld** en **ingeschakeld**.  

7.  Om detectie te configureren om specifieke SNMP-communitynamen voor SNMP-apparaten te doorzoeken, kies de **SNMP** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Een SNMP-communitynaam toevoegen aan de lijst met **SNMP-communitynamen**, kies de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuwe SNMP-communitynaam** dialoogvenster, geeft u de **naam** van de SNMP-community, en kies vervolgens **OK**.  

    -   Als u wilt verwijderen van een SNMP-communitynaam, selecteer de community-naam en kies vervolgens het **verwijderen** pictogram ![verwijderingspictogram](media/Disc_delete_Icon.gif).  

    -   Als u wilt de zoekvolgorde van SNMP-communitynamen aanpassen, selecteert u een communitynaam en kies vervolgens het **Item omhoog verplaatsen** pictogram ![pictogram verplaatsen](media/Disc_moveUp_Icon.gif) of de **Item omlaag verplaatsen** pictogram ![pictogram verplaatsen](media/Disc_moveDown_Icon.gif). Wanneer detectie wordt uitgevoerd, worden communitynamen in een boven-naar-beneden volgorde doorzocht. Denk aan de volgende punten.

        > [!NOTE]  
        >  Netwerkdetectie gebruikt SNMP-communitynamen om toegang tot routers die SNMP-apparaten te krijgen. Een router kan netwerkdetectie informeren over andere routers en subnetten die verbonden zijn met de eerste router.  

        -   SNMP-communitynamen lijken op wachtwoorden.  

        -   Netwerkdetectie kan enkel informatie krijgen van een SNMP-apparaat waarvoor u een communitynaam heb gespecificeerd.  

        -   Elk SNMP-apparaat kan zijn eigen communitynaam hebben, maar dikwijls wordt dezelfde comunitynaam gedeeld tussen verschillende apparaten.  

        -   De meeste SNMP-apparaten hebben een standaardnaam **openbare**. U kunt die gebruiken als u geen andere communitynamen kent. Sommige organisaties wissen evenwel de **openbare** communitynaam vanaf hun apparaten veiligheidsoverwegingen.  

8.  Het maximum aantal router-hops voor gebruik door SNMP-opzoekingen configureren, kiest u de **SNMP** tabblad en selecteer vervolgens het aantal hops van de **Maximum hops** vervolgkeuzelijst.  

9. Als u wilt configureren op een SNMP-apparaat, kies de **SNMP-apparaten** tabblad. Als het apparaat niet weergegeven wordt, selecteert u de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuw SNMP-apparaat** in het dialoogvenster geeft de IP-adres of het apparaat de naam van het SNMP-apparaat en kies vervolgens **OK**.  

    > [!NOTE]  
    >  Als u een apparaatsnaam opgeeft, moet de Configuration Manager staat de NetBIOS-naam omzetten in een IP-adres zijn.  

10. Om detectie te configureren om specifieke DHCP-servers opvragen voor DHCP-clients, kies de **DHCP** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Als u wilt zoeken op de DHCP-server op de computer die detectie uitvoert, controleert u de **gebruik altijd de DHCP-server van de siteserver** vak.  

        > [!NOTE]  
        >  Om deze optie gebruikt, wordt de server moet zijn IP-adres huren van een DHCP-server en een statisch IP-adres niet gebruiken.  

    -   Om een specifieke DHCP-server te bevragen, kies de **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuwe DHCP-Server** in het dialoogvenster Geef het IP-adres of de servernaam van de DHCP-server en kies vervolgens **OK**.  

        > [!NOTE]  
        >  Als u een servernaam opgeeft, moet de Configuration Manager staat de NetBIOS-naam omzetten in een IP-adres zijn.  

11. Om te configureren wanneer detectie wordt uitgevoerd, kiest u de **schema** tabblad en kies vervolgens het **New** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) het instellen van een planning voor het uitvoeren van netwerkdetectie.  

     U kunt meerdere recurrente plannings- en meerdere plannings zonder recurrentie.  

    > [!NOTE]  
    >  Als meerdere schema's worden weergegeven op de **schema** tabblad tegelijkertijd, resulteren alle plannings in een uitvoering van Netwerkdetectie zoals ze geconfigureerd is op het tijdstip aangegeven in de planning. Dit geldt ook voor terugkerende schema's.  

12. Kies **OK** uw configuraties opslaan.  

###  <a name="BKMK_HowToVerifyNetDisc"></a>Controleren of de netwerkdetectie is voltooid  
 De tijd die netwerkdetectie nodig heeft om te voltooien kan variëren afhankelijk van diverse factoren. Deze factoren kunnen één of meer van de volgende bevatten:  

-   De grootte van uw netwerk  

-   De topologie van uw netwerk  

-   Het maximum aantal hops dat geconfigureerd is om routers te vinden in het netwerk  

-   Het type detectie dat wordt uitgevoerd  

Omdat netwerkdetectie geen berichten om u te waarschuwen wanneer detectie voltooid is maakt, kunt u de volgende procedure gebruiken om te verifiëren of detectie is voltooid.  

##### <a name="to-verify-that-network-discovery-has-finished"></a>Om te controleren of de netwerkdetectie is voltooid  

1.  Kies in de Configuration Manager-console **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **systeemstatus**, en kies vervolgens **Statusopdrachten**.  

3.  Kies **alle statusberichten**.  

4.  Op de **Start** tabblad, in de **Statusopdrachten** groep, kiest u **Toon berichten**.  

5.  In de **datum en tijd selecteren** vervolgkeuzelijst, selecteert u een waarde die bevat hoe lang gelden de detectie is gestart en kies vervolgens **OK** openen van de **Configuration Manager Status Message Viewer**.  

    > [!TIP]  
    >  U kunt ook de **datum en tijd opgeven** optie voor het selecteren van een gegeven datum en tijd die u detectie uitvoerde. Deze optie is nuttig wanneer u netwerkdetectie uitvoerde op een gegeven datum en berichten wilt extraheren van enkel deze datum.  

6.  Zoeken, om te valideren dat netwerkdetectie voltooid voor een statusbericht dat de volgende gegevens:  

    -   Bericht-ID: **502**  

    -   Onderdeel: **SMS_NETWORK_DISCOVERY**  

    -   Beschrijving: **Dit onderdeel is gestopt**  

    Als dit statusbericht niet aanwezig is, is netwerkdetectie niet voltooid.  

7.  Zoeken, om te valideren dat netwerkdetectie gestart voor een statusbericht dat de volgende gegevens:  

    -   Bericht-ID: **500**  

    -   Onderdeel: **SMS_NETWORK_DISCOVERY**  

    -   Beschrijving: **Dit onderdeel is gestart**  

    Deze informatie wordt gecontroleerd of netwerkdetectie wordt gestart. Als deze informatie niet aanwezig is, plan dan netwerkdetectie.  

