---
title: Detectie configureren | Microsoft Docs
description: Configureer detectiemethoden worden uitgevoerd op een Configuration Manager-site zoeken naar bronnen die u vanaf uw netwerkinfrastructuur en Active Directory beheren kunt.
ms.custom: na
ms.date: 7/31/2017
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
ms.translationtype: MT
ms.sourcegitcommit: 0663ba84762c44a5c303562548499f195bae9e1c
ms.openlocfilehash: 34a539ceaea6b070f81a28d2c0a9ce388e26cfeb
ms.contentlocale: nl-nl
ms.lasthandoff: 08/01/2017

---
# <a name="configure-discovery-methods-for-system-center-configuration-manager"></a>Detectiemethoden configureren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


U configureren detectiemethoden worden uitgevoerd op een System Center Configuration Manager-site zoeken naar bronnen die u van uw netwerkinfrastructuur en Active Directory beheren kunt. Hiervoor moet u inschakelen en vervolgens elke methode die u wilt gebruiken om te zoeken van uw omgeving te configureren. (U kunt ook een methode uitschakelen met behulp van dezelfde procedure die u gebruikt deze in te schakelen.)  De enige uitzondering hierop zijn Heartbeat-detectie en serverdetectie:  

-   Standaard is Heartbeat-detectie al ingeschakeld wanneer u een primaire site van Configuration Manager hebt geïnstalleerd en geconfigureerd voor uitvoering op een eenvoudige planning. Het is een goed idee om Houd Heartbeat-detectie ingeschakeld omdat Hiermee zorgt u ervoor dat de detectiegegevensrecords (DDR's) voor apparaten up-to-date zijn. Zie voor meer informatie over Heartbeat-detectie [over Heartbeat-detectie](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutHeartbeat).  

-   Serverdetectie is een automatische detectiemethode waarmee wordt gezocht naar computers die u als sitesystemen gebruikt. Configureren of niet uitschakelen.  

**Een configureerbare detectiemethode inschakelen:**  
 > [!NOTE]  
 > De volgende informatie is niet van toepassing op Azure Active Directory-Gebruikersdetectie. In plaats daarvan Zie [configureren Azure AD-Gebruikersdetectie](#azureaadisc) verderop in dit onderwerp.

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Selecteer de detectiemethode voor de site waar u detectie wilt inschakelen.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**, en klik vervolgens op de **algemene** tabblad, Controleer de **inschakelen&lt;detectiemethode\>**  vak.  

     Als dit selectievakje al is ingeschakeld, kunt u de detectiemethode uitschakelen door het selectievakje uitschakelt.  

4.  Kies **OK** aan de configuratie op te slaan.  


##  <a name="BKMK_ConfigADForestDisc"></a>Detectie van Active Directory-Forest configureren  
Voor het voltooien van de configuratie van detectie van Active Directory-Forest, moet u instellingen configureren op twee locaties:  

-   In de **detectiemethoden** knooppunt, kunt u:

    - Deze detectiemethode inschakelen.
    - Een polling-planning instellen.
    - Selecteren of detectie automatisch grenzen maakt voor de Active Directory-sites en subnetten die het detecteert.  

-   In de **Active Directory-Forests** knooppunt, kunt u:

    - Forests toevoegen die u wilt detecteren.
    - Schakel detectie van Active Directory-sites en subnetten in het forest.
    - Instellingen configureren die Configuration Manager-sites hun sitegegevens publiceren naar het forest inschakelen.
    - Een account gebruikt als de Active Directory-Forestaccount voor elke forest toewijzen.  

Gebruik de volgende procedures in Active Directory-Forestdetectie inschakelen en configureren van afzonderlijke forests voor gebruik met Active Directory Forest Discovery.  

#### <a name="to-enable-active-directory-forest-discovery"></a>Active Directory-Forestdetectie inschakelen  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Selecteer de Active Directory Forest Discovery-methode voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemene** tabblad, het selectievakje voor het inschakelen van detectie. Of u nu detectie configureren en vervolgens weer detectie later inschakelen.  

5.  Geef opties op het maken van sitegrenzen voor gedetecteerde locaties.  

6.  Geef een planning voor wanneer detectie wordt uitgevoerd.  

7.  Wanneer u klaar bent met de configuratie van Active Directory-Forestdetectie voor deze site, kiezen **OK** aan de configuratie op te slaan.  

#### <a name="to-configure-a-forest-for-active-directory-forest-discovery"></a>Een forest voor Active Directory-Forestdetectie configureren  

1.  In de **beheer** werkruimte, kiest u **Active Directory-Forests**. Als Active Directory-forestdetectie eerder is uitgevoerd, ziet u iedere gedetecteerde forest in het resultatenvenster. De lokale forest en vertrouwde forests worden gedetecteerd wanneer Active Directory-forestdetectie wordt uitgevoerd. U kunt niet-vertrouwde forests alleen handmatig toevoegen.  

    -   Voor het configureren van een eerder gedetecteerd forest, selecteert u het forest in het deelvenster met resultaten. Klik op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen** om de foresteigenschappen te openen. Ga door met stap 3.  

    -   Voor het configureren van een nieuw forest dat niet wordt vermeld, op de **Start** tabblad, in de **maken** groep, kiest u **Forest toevoegen** openen de **Forests toevoegen** in het dialoogvenster. Ga door met stap 3.  

2.  Op de **algemene** tabblad, einddatum configuraties voor de forest die u wilt detecteren en geeft de **Active Directory-Forestaccount**.  

    > [!NOTE]  
    >  Voor Active Directory-forestdetectie is een globaal account nodig om niet-vertrouwde forests te detecteren en ernaar te publiceren. Als u het computeraccount van de siteserver niet gebruikt, kunt u alleen een globaal account selecteren.  

3.  Als u van plan bent om sites sitegegevens naar dit forest te publiceren op de **Publishing** tabblad, einddatum configuraties voor publicatie naar dit forest.  

    > [!NOTE]  
    >  Als u toestaat dat sites publiceren naar een forest, moet u het Active Directory-schema van dit forest uitbreiden voor Configuration Manager. De Active Directory-Forestaccount moet machtigingen voor volledig beheer voor de systeemcontainer in dat forest hebben.  

4.  Wanneer u klaar bent met de configuratie van deze forest voor Active Directory Forest Discovery kiezen **OK** aan de configuratie op te slaan.  

##  <a name="BKMK_ConfigADDiscGeneral"></a>Detectie van Active Directory voor computers, gebruikers of groepen configureren  
 Gebruik de informatie in de volgende secties voor het configureren van detectie van computers, gebruikers of groepen. U hebt deze detectiemethoden gebruiken:  

-   Active Directory-groepdetectie  

-   Active Directory-systeemdetectie  

-   Detectie Active Directory-gebruiker  

> [!NOTE]  
>  De informatie in deze sectie geldt niet voor de detectie van Active Directory-Forest.  

 Hoewel elk van deze detectiemethoden onafhankelijk van de andere, delen ze wel soortgelijke opties. Zie voor meer informatie over deze configuratieopties [gedeeld opties voor de detectie van groep-, systeem- en gebruiker](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_shared).  

> [!WARNING]  
>  Polling van Active Directory door elk van deze detectiemethoden kan significant netwerkverkeer genereren. U kunt de planning van elke detectiemethode om uit te voeren op een tijdstip waarop dit netwerkverkeer geen belemmering zakelijke gebruik van uw netwerk.  

#### <a name="to-configure-active-directory-group-discovery"></a>Detectie van Active Directory-groepen configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies de **Active Directory Group Discovery** methode voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemene** tabblad, het selectievakje voor het inschakelen van detectie. Of u nu detectie configureren en vervolgens weer detectie later inschakelen.  

5.  Kies **toevoegen** om een detectiebereik configureert, kiest u **groepen** of **locatie**, en voltooit u de volgende configuraties in de **groepen toevoegen** of **Active Directory-locatie toevoegen** in het dialoogvenster:  

    1.  Geef een **naam** voor dit detectiebereik.  

    2.  Geef een **Active Directory-domein** of **locatie** om te zoeken:  

        -   Als u hebt gekozen **groepen**, geeft u een of meer Active Directory-groepen moeten worden gedetecteerd.  

        -   Als u hebt gekozen **locatie**, een Active Directory-container opgeven als locatie moeten worden gedetecteerd. U kunt ook een recursieve zoekopdracht van onderliggende Active Directory-containers voor deze locatie inschakelen.  

    3.  Geef de **Detectieaccount Active Directory-groepen** die wordt gebruikt om dit detectiebereik te zoeken.  

    4.  Kies **OK** om op te slaan van de configuratie van het detectiebereik.  

6.  Herhaal stap 6 voor ieder extra detectiebereik dat u wilt definiëren.  

7.  Op de **Polling-planning** tabblad, het configureren van de volledige detectiepolling-planning en deltadetectie.  

8.  Klik desgewenst op de **optie** tabblad kunt u opties wilt filteren of uitsluiten van verouderde computerrecords van detectie en het lidmaatschap van distributiegroepen te detecteren.  

    > [!NOTE]  
    >  Detectie van Active Directory-groepen detecteert standaard alleen het lidmaatschap van beveiligingsgroepen.  

9. Wanneer u klaar bent met het configureren van detectie van Active Directory-groepen voor deze site, kiezen **OK** aan de configuratie op te slaan.  

#### <a name="to-configure-active-directory-system-discovery"></a>Voor het configureren van Active Directory-Systeemdetectie  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Selecteer de methode voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemene** tabblad, het selectievakje voor het inschakelen van detectie. Of u nu detectie configureren en vervolgens weer detectie later inschakelen.  

5.  Kies de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) om op te geven van een nieuwe Active Directory-container. In de **Active Directory-Container** dialoogvenster vak, einddatum van de volgende configuraties:  

    1.  Geef een of meer zoeklocaties op.  

    2.  Geef de opties die het zoekgedrag wijzigen voor elke locatie.  

    3.  Geef voor elke locatie het account wilt gebruiken als de **Detectieaccount Active Directory**.  

        > [!TIP]  
        >  U kunt een set van detectieopties en een uniek Active Directory Discovery-Account configureren voor elke locatie die u opgeeft.  

    4.  Kies **OK** om op te slaan van de configuratie van de Active Directory-container.  

6.  Op de **Polling-planning** tabblad, het configureren van de volledige detectiepolling-planning en deltadetectie.  

7.  Klik desgewenst op de **Active Directory-attributen** tabblad kunt u extra kenmerken voor Active Directory voor computers die u wilt detecteren. De standaard-objectkenmerken worden ook vermeld.  

8.  Klik desgewenst op de **optie** tabblad kunt u opties voor het filteren of uitsluiten van verouderde computerrecords van detectie.  

9. Wanneer u klaar bent met het configureren van detectie van Active Directory-systemen voor deze site, kiezen **OK** aan de configuratie op te slaan.  

#### <a name="to-configure-active-directory-user-discovery"></a>Voor het configureren van detectie van Active Directory-gebruikers  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies de **Active Directory-Gebruikersdetectie** methode voor de site waar u detectie wilt configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemene** tabblad, het selectievakje voor het inschakelen van detectie. Of u nu detectie configureren en vervolgens weer detectie later inschakelen.  

5.  Kies de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) om op te geven van een nieuwe Active Directory-container. In de **Active Directory-Container** dialoogvenster vak, einddatum van de volgende configuraties:  

    1.  Geef een of meer zoeklocaties op.  

    2.  Geef de opties die het zoekgedrag wijzigen voor elke locatie.  

    3.  Geef voor elke locatie het account wilt gebruiken als de **Detectieaccount Active Directory**.  

        > [!NOTE]  
        >  U kunt een unieke set van detectieopties en een uniek Active Directory Discovery-Account configureren voor elke locatie die u opgeeft.  

    4.  Kies **OK** om op te slaan van de configuratie van de Active Directory-container.  

6.  Op de **Polling-planning** tabblad, het configureren van de volledige detectiepolling-planning en deltadetectie.  

7.  Klik desgewenst op de **Active Directory-attributen** tabblad kunt u extra kenmerken voor Active Directory voor computers die u wilt detecteren. De standaard-objectkenmerken worden ook vermeld.  

8.  Wanneer u klaar bent met het configureren van detectie van Active Directory-gebruikers voor deze site, kiezen **OK** aan de configuratie op te slaan.  

## <a name="azureaadisc"></a>Azure AD-Gebruikersdetectie configureren
Vanaf versie 1706, kunt u Azure Active Directory-Gebruikersdetectie configureren wanneer u verbinding maakt met Configuration Manager uw [Azure-abonnement en Azure Active Directory](/sccm/core/servers/deploy/configure/azure-services-wizard).

Azure AD-Gebruikersdetectie wordt geconfigureerd als onderdeel van *Cloudbeheer*. De procedure om dit te doen, wordt besproken in [maken van de Azure-web-app voor gebruik met Configuration Manager](/sccm/core/servers/deploy/configure/Azure-services-wizard#webapp) in het onderwerp *configureren van Azure services voor gebruik met Configuration Manager*.




##  <a name="BKMK_ConfigHBDisc"></a>Heartbeat-detectie configureren  
 Heartbeat-detectie is standaard ingeschakeld wanneer u een primaire site van Configuration Manager installeert. Hierdoor hoeft u alleen te configureren van de planning voor hoe vaak clients verzenden de Heartbeat-detectie-gegevens naar een beheerpunt opnemen wanneer u niet wilt dat de standaard elke zeven dagen.  

> [!NOTE]  
>  Als zowel client-pushinstallatie en de siteonderhoudstaak voor **Installatievlag** zijn ingeschakeld op dezelfde site, zet u de planning voor Heartbeat-detectie op korter dan de **periode Herdetectie Client** van de **Installatievlag** siteonderhoudstaak. Zie voor meer informatie over siteonderhoudstaken [onderhoudstaken voor System Center Configuration Manager](../../../../core/servers/manage/maintenance-tasks.md).  

#### <a name="to-configure-the-heartbeat-discovery-schedule"></a>De planning voor Heartbeat-detectie configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies **Heartbeat-detectie** voor de site waar u Heartbeat-detectie configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Configureer de frequentie waarmee clients Heartbeat-gegevensdetectierecord verzenden, en kies vervolgens **OK** aan de configuratie op te slaan.  

##  <a name="BKMK_ConfigNetworkDisc"></a>Netwerkdetectie configureren  
 Gebruik de informatie in de volgende secties voor hulp bij het configureren van netwerkdetectie.  

###  <a name="BKMK_AboutConfigNetworkDisc"></a>Over het configureren van netwerkdetectie  
 Voordat u netwerkdetectie configureert, moet u het volgende weten:  

-   Beschikbare niveaus van netwerkdetectie  

-   Beschikbare opties voor netwerkdetectie  

-   Beperken van netwerkdetectie op het netwerk  

Zie voor meer informatie [over netwerkdetectie](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutNetwork).  

 De volgende secties bevatten informatie over algemene configuraties voor netwerkdetectie. U kunt een of meer van deze configuraties voor gebruik tijdens dezelfde detectierun uitvoeren. Als u meerdere configuraties gebruikt, moet u plannen voor de interactie die de detectieresultaten kunnen beïnvloeden.  

 U wilt bijvoorbeeld alle Simple Network Management Protocol (SNMP)-apparaten die gebruikmaken van een specifieke SNMP-communitynaam te detecteren. U kunt bovendien detectie op een specifiek subnet uitschakelen voor de dezelfde detectierun. Wanneer detectie wordt uitgevoerd, detecteert netwerkdetectie geen SNMP-apparaten met de opgegeven communitynaam op het subnet dat u hebt uitgeschakeld.  

####  <a name="BKMK_DetermineNetTopology"></a>Uw netwerktopologie bepalen  
 Alleen-topologie detectie kunt u uw netwerk worden toegewezen. Dit type detectie detecteert geen potentiële clients. De topologie-alleen voor netwerkdetectie is afhankelijk van SNMP.  

 Wanneer u uw netwerktopologie toegewezen bent, moet u de **Maximum aantal hops** op de **SNMP** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster. Met slechts enkele hops kunnen helpen bij het beheren van de netwerkbandbreedte die wordt gebruikt wanneer detectie wordt uitgevoerd. Als u meer van uw netwerk ontdekt, kunt u het aantal hops opvoeren beter inzicht te krijgen van uw netwerktopologie om verhogen.  

 Nadat u uw netwerktopologie begrijpt, kunt u extra eigenschappen voor netwerkdetectie voor het detecteren van mogelijke clients en hun besturingssystemen, terwijl u beschikbare configuraties gebruikt voor het beperken van de netwerksegmenten dat netwerkdetectie kan zoeken.  

####  <a name="BKMK_LimitBySubnet"></a>Zoekopdrachten beperken met subnetten  
 U kunt netwerkdetectie configureren om te zoeken naar specifieke subnetten tijdens een detectierun. Netwerkdetectie doorzoekt standaard het subnet van de server die detectie uitvoert. Eventuele extra subnetten die u configureert en inschakelt alleen van toepassing op SNMP en Dynamic Host Configuration Protocol (DHCP) zoekopties. Wanneer netwerkdetectie domeinen zoekt, wordt het niet beperkt door subnetconfiguraties.  

 Als u een of meer subnetten opgeeft op de **subnetten** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster alleen de subnetten die zijn gemarkeerd als **ingeschakeld** worden doorzocht.  

 Wanneer u een subnet uitschakelt, wordt het uitgesloten van detectie en gelden de volgende voorwaarden:  

-   SNMP-query's niet uitgevoerd op het subnet.  

-   DHCP-servers reageren niet met een lijst met bronnen die zich op het subnet.  

-   Domain-query's kunnen bronnen detecteren die zich op het subnet bevinden.  

####  <a name="BKMK_SearchByDomain"></a>Zoeken in een specifiek domein  
 U kunt netwerkdetectie configureren om te zoeken in een specifiek domein of set van domeinen tijdens het uitvoeren van een detectie. Netwerkdetectie doorzoekt standaard het lokale domein van de server die detectie uitvoert.  

 Als u een of meer domeinen specificeert op het **domeinen** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster alleen de domeinen die zijn gemarkeerd als **ingeschakeld** worden doorzocht.  

 Wanneer u een domein uitschakelt, wordt het uitgesloten van detectie en gelden de volgende voorwaarden:  

-   Netwerkdetectie voert geen query's domeincontrollers in dat domein.  

-   SNMP-query's kunnen nog steeds uitgevoerd op subnetten in het domein.  

-   DHCP-servers kunnen nog steeds antwoorden met een lijst met bronnen in het domein.  

####  <a name="BKMK_LimitBySNMPname"></a>Zoekopdrachten beperken door SNMP-communitynamen te gebruiken  
 U configureren netwerkdetectie om te zoeken in een specifieke SNMP-community of set van communities tijdens het uitvoeren van een detectie. Standaard wordt de communitynaam van **openbare** is geconfigureerd voor gebruik.  

 Netwerkdetectie gebruikt communitynamen om toegang tot routers die SNMP-apparaten te krijgen. Een router kan netwerkdetectie voorzien met informatie over andere routers en subnetten die zijn gekoppeld aan de eerste router.  

> [!NOTE]  
>  SNMP-communitynamen lijken op wachtwoorden. Netwerkdetectie kan enkel informatie krijgen van een SNMP-apparaat waarvoor u een communitynaam hebt opgegeven. Elk SNMP-apparaat kan zijn eigen communitynaam hebben, maar dikwijls wordt dezelfde comunitynaam gedeeld tussen verschillende apparaten. Bovendien hebben de meeste SNMP-apparaten een standaardcommunitynaam **openbare**. Sommige organisaties wissen, maar de **openbare** communitynaam vanaf hun apparaten veiligheidsoverwegingen.  

 Als meerdere SNMP-communities worden weergegeven op de **SNMP** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster zoekt netwerkdetectie ze in de volgorde waarin ze worden weergegeven. Om te helpen het netwerkverkeer dat wordt gegenereerd door pogingen om contact met een apparaat met behulp van verschillende namen te minimaliseren, zorg ervoor dat de meest gebruikte namen aan de bovenkant van de lijst.  

> [!NOTE]  
>  Naast het gebruik van de SNMP-communitynaam, kunt u het IP-adres of herleidbare naam van een specifiek SNMP-apparaat. U dit doen op de **SNMP-apparaten** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster.  

####  <a name="BKMK_SearchByDHCP"></a>Een specifieke DHCP-server zoeken  
 U kunt netwerkdetectie voor het gebruik van een specifieke DHCP-server of meerdere servers voor het detecteren van DHCP-clients tijdens de uitvoering van een detectie configureren.  

 Netwerkdetectie doorzoekt elke DHCP-server die u opgeeft op de **DHCP** tabblad de **netwerkdetectie-eigenschappen** in het dialoogvenster. Als de server die detectie uitvoert zijn IP-adres van een DHCP-server huurt, u kunt detectie configureren zodat deze DHCP-server zoeken door het controleren van de **de DHCP-server opnemen waarvoor de siteserver is geconfigureerd voor gebruik** vak.  

> [!NOTE]  
>  Als u wilt configureren met succes een DHCP-server in netwerkdetectie, moet uw omgeving IPv4 ondersteunen. U kunt netwerkdetectie voor het gebruik van een DHCP-server in een systeemeigen IPv6-netwerkomgeving niet configureren.  

###  <a name="BKMK_HowToConfigNetDisc"></a>Het configureren van netwerkdetectie  
 Gebruik de volgende procedures om eerst enkel uw netwerktopologie te detecteren en configureer dan netwerkdetectie voor het detecteren van mogelijke clients met behulp van een of meer van de beschikbare opties voor netwerkdetectie.  

##### <a name="to-determine-your-network-topology"></a>Uw netwerktopologie bepalen  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies **netwerkdetectie** voor de site waar u netwerkdetectie wilt uitvoeren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

    -   Op de **algemene** tabblad, Controleer de **Netwerkdetectie inschakelen** vak in en kies vervolgens **topologie** van de **Type detectie** opties.  

    -   Op de **subnetten** tabblad, Controleer de **lokale subnetten doorzoeken** vak.  

        > [!TIP]  
        >  Als u welke subnetten deel uitmaken van uw netwerk weet, schakelt u de **lokale subnetten doorzoeken** vak en gebruik de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) toevoegen de specifieke subnetten die u wilt zoeken. Voor grote netwerken is het verstandig om te zoeken slechts één of twee subnetten tegelijk om het gebruik van netwerkbandbreedte te minimaliseren.  

    -   Op de **domeinen** tabblad, Controleer de **lokale domeinen doorzoeken** vak.  

    -   Op de **SNMP** tabblad, gebruikt u de **Maximum aantal hops** vervolgkeuzelijst om te specificeren hoeveel routerhops Netwerkdetectie kan duren in kaart brengen van uw topologie.  

        > [!TIP]  
        >  Wanneer u eerst uw netwerktopologie toewijst, configureert u slechts enkele routerhops om het gebruik van netwerkbandbreedte te minimaliseren.  

4.  Op de **planning** tabblad, kiest u de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) het instellen van een planning voor het uitvoeren van netwerkdetectie.  

    > [!NOTE]  
    >  U kunt een andere detectieconfiguratie te scheiden netwerkdetectieplannings niet toewijzen. Elke keer dat netwerkdetectie wordt uitgevoerd, gebruikt het de huidige detectieconfiguratie.  

5.  Kies **OK** om de configuraties te aanvaarden. Netwerkdetectie wordt uitgevoerd op het geplande tijdstip.  

##### <a name="to-configure-network-discovery"></a>Netwerkdetectie configureren  

1.  Kies in de Configuration Manager-console **beheer** > **Hiërarchieconfiguratie**, en kies vervolgens **detectiemethoden**.  

2.  Kies **netwerkdetectie** voor de site waar u netwerkdetectie wilt uitvoeren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Op de **algemene** tabblad, Controleer de **Netwerkdetectie inschakelen** vak en selecteer vervolgens het type detectie dat u uitvoeren wilt van de **Type detectie** opties.  

5.  Om detectie te configureren om te zoeken naar subnetten, kies de **subnetten** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Detectie op subnetten die lokaal op de computer die detectie uitvoert zijn uitgevoerd, Controleer de **lokale subnetten doorzoeken** vak.  

    -   Om te zoeken naar een specifiek subnet, zorg ervoor dat het subnet is opgenomen in **te doorzoeken subnetten** en heeft een **Search** waarde van **ingeschakeld**:  

        1.  Als het subnet niet wordt weergegeven, selecteert u de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuwe Subnettoewijzing** dialoogvenster en voer de **Subnet** en **masker** informatie en kies vervolgens **OK**. Een nieuw subnet is standaard ingeschakeld voor de zoekopdracht.  

        2.  Wijzigen van de **zoeken** waarde voor een subnet in de lijst, selecteert u het subnet en kies vervolgens de **in-of uitschakelen** pictogram overschakelen van de waarde tussen **uitgeschakeld** en **ingeschakeld**.  

6.  Om detectie te configureren om te zoeken naar domeinen, kies de **domeinen** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Detectie uitgevoerd op het domein van de computer die detectie uitvoert, Controleer de **lokale domeinen doorzoeken** vak.  

    -   Om te zoeken naar een specifiek domein, zorg ervoor dat het domein is opgenomen in **domeinen** en heeft een **Search** waarde van **ingeschakeld**:  

        1.  Als het domein niet wordt weergegeven, selecteert u de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **Domeineigenschappen** dialoogvenster en voer de **domein** informatie en kies vervolgens **OK**. Een nieuw domein is standaard ingeschakeld voor de zoekopdracht.  

        2.  Wijzigen van de **zoeken** waarde voor een domein in de lijst, selecteert u het domein en kies vervolgens de **wisselknop** pictogram overschakelen van de waarde tussen **uitgeschakeld** en **ingeschakeld**.  

7.  Om detectie te configureren om te zoeken naar specifieke SNMP-communitynamen voor SNMP-apparaten, kies de **SNMP** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Een SNMP-communitynaam toevoegen aan de lijst met **SNMP-communitynamen**, kies de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuwe SNMP-communitynaam** dialoogvenster geeft u de **naam** van de SNMP-community en kies vervolgens **OK**.  

    -   Als u wilt verwijderen van een SNMP-communitynaam, selecteert u de communitynaam en kies vervolgens de **verwijderen** pictogram ![pictogram verwijderen](media/Disc_delete_Icon.gif).  

    -   Als u wilt de zoekvolgorde van SNMP-communitynamen aanpassen, selecteert u een communitynaam en kies vervolgens de **Item omhoog verplaatsen** pictogram ![pictogram verplaatsen](media/Disc_moveUp_Icon.gif) of de **Item omlaag verplaatsen** pictogram ![pictogram verplaatsen](media/Disc_moveDown_Icon.gif). Wanneer detectie wordt uitgevoerd, worden communitynamen in een boven-naar-beneden volgorde doorzocht. Denk aan de volgende punten.

        > [!NOTE]  
        >  Netwerkdetectie gebruikt SNMP-communitynamen toegang te krijgen tot routers die SNMP-apparaten. Een router kan netwerkdetectie informeren over andere routers en subnetten die verbonden zijn met de eerste router.  

        -   SNMP-communitynamen lijken op wachtwoorden.  

        -   Netwerkdetectie kan enkel informatie krijgen van een SNMP-apparaat waarvoor u een communitynaam hebt opgegeven.  

        -   Elk SNMP-apparaat kan zijn eigen communitynaam hebben, maar dikwijls wordt dezelfde comunitynaam gedeeld tussen verschillende apparaten.  

        -   De meeste SNMP-apparaten hebben een standaardnaam **openbare**. U kunt deze instelling gebruiken als u geen andere communitynamen kent. Sommige organisaties wissen evenwel de **openbare** communitynaam vanaf hun apparaten veiligheidsoverwegingen.  

8.  Voor het configureren van het maximum aantal router-hops voor gebruik door SNMP-opzoekingen, kies de **SNMP** tabblad en selecteer vervolgens het aantal hops van de **Maximum aantal hops** vervolgkeuzelijst.  

9. Voor het configureren van een SNMP-apparaat, kies de **SNMP-apparaten** tabblad. Als het apparaat niet weergegeven wordt, selecteert u de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuwe SNMP-apparaat** in het dialoogvenster Geef de IP-adres of het apparaat de naam van het SNMP-apparaat en kies vervolgens **OK**.  

    > [!NOTE]  
    >  Als u een apparaatsnaam opgeeft, wordt Configuration Manager moet de NetBIOS-naam omzetten in een IP-adres.  

10. Om detectie te configureren om te doorzoeken op specifieke DHCP-servers DHCP-clients, kies de **DHCP** tabblad en configureer vervolgens een of meer van de volgende opties:  

    -   Als u wilt zoeken op de DHCP-server op de computer die detectie uitvoert, Controleer de **gebruik altijd de DHCP-server van de siteserver** vak.  

        > [!NOTE]  
        >  Om deze optie gebruikt, is de server moet het IP-adres van een DHCP-server van de lease, en een statisch IP-adres niet gebruiken.  

    -   Om te vragen een specifieke DHCP-server, kies de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif). In de **nieuwe DHCP-Server** in het dialoogvenster Geef het IP-adres of de servernaam van de DHCP-server en kies vervolgens **OK**.  

        > [!NOTE]  
        >  Als u een servernaam opgeeft, wordt Configuration Manager moet de NetBIOS-naam omzetten in een IP-adres.  

11. Als u wilt configureren wanneer detectie wordt uitgevoerd, kies de **planning** tabblad en kies vervolgens de **nieuw** pictogram ![pictogram Nieuw](media/Disc_new_Icon.gif) het instellen van een planning voor het uitvoeren van netwerkdetectie.  

     U kunt meerdere recurrente plannings- en meerdere plannings zonder recurrentie configureren.  

    > [!NOTE]  
    >  Als meerdere planningen worden weergegeven op de **planning** tabblad op hetzelfde moment, resulteren alle plannings in een uitvoering van Netwerkdetectie zoals ze geconfigureerd is op het tijdstip aangegeven in de planning. Dit geldt ook voor terugkerende schema's.  

12. Kies **OK** uw configuraties op te slaan.  

###  <a name="BKMK_HowToVerifyNetDisc"></a>Controleren of de netwerkdetectie is voltooid  
 De tijd die netwerkdetectie nodig heeft om te voltooien kan variëren afhankelijk van een verscheidenheid aan factoren. Deze factoren kunnen bevatten een of meer van de volgende opties:  

-   De grootte van uw netwerk  

-   De topologie van uw netwerk  

-   Het maximum aantal hops dat geconfigureerd is om routers te vinden in het netwerk  

-   Het type detectie dat wordt uitgevoerd  

Omdat netwerkdetectie geen berichten om u te waarschuwen wanneer detectie is voltooid maakt, kunt u de volgende procedure om te controleren wanneer detectie is voltooid.  

##### <a name="to-verify-that-network-discovery-has-finished"></a>Om te controleren of de netwerkdetectie is voltooid  

1.  Kies in de Configuration Manager-console **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **systeemstatus**, en kies vervolgens **Statusopdrachten**.  

3.  Kies **alle statusberichten**.  

4.  Op de **Start** tabblad, in de **Statusopdrachten** groep, kiest u **Toon berichten**.  

5.  In de **datum en tijd selecteren** vervolgkeuzelijst, selecteer een waarde die bevat hoe lang gelden de detectie is gestart, en kies vervolgens **OK** openen de **Configuration Manager Status Message Viewer**.  

    > [!TIP]  
    >  U kunt ook de **datum en tijd opgeven** optie voor het selecteren van een gegeven datum en tijd die u detectie uitvoerde. Deze optie is nuttig wanneer u netwerkdetectie uitvoerde op een gegeven datum en berichten wilt extraheren van enkel deze datum.  

6.  Om te valideren dat netwerkdetectie is voltooid, zoeken naar een statusbericht dat de volgende gegevens:  

    -   Bericht-ID: **502**  

    -   Onderdeel: **SMS_NETWORK_DISCOVERY**  

    -   Beschrijving: **Dit onderdeel is gestopt**  

    Als dit statusbericht niet aanwezig is, heeft niet de netwerkdetectie voltooid.  

7.  Om te valideren dat netwerkdetectie gestart, zoekt u een statusbericht dat de volgende gegevens:  

    -   Bericht-ID: **500**  

    -   Onderdeel: **SMS_NETWORK_DISCOVERY**  

    -   Beschrijving: **Dit onderdeel is gestart**  

    Deze informatie wordt gecontroleerd of netwerkdetectie wordt gestart. Als deze informatie niet aanwezig is, plan dan netwerkdetectie.  

