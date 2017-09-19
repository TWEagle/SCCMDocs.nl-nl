---
title: Deze clients | Microsoft Docs
description: Plannen voor ontwaken van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52ee82b2-0b91-4829-89df-80a6abc0e63a
caps.latest.revision: "6"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 5445e51268c32e6f0c9970a8dc18f2d17aee88c9
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="plan-how-to-wake-up-clients-in-system-center-configuration-manager"></a>Plannen voor ontwaken van clients in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Configuration Manager ondersteunt twee wake on LAN (LAN)-technologieën om computers te activeren in de slaapstandmodus bevinden wanneer u wilt installeren van vereiste software, zoals software-updates en toepassingen: traditionele wake-uppakketten en AMT-inschakelopdrachten.  

U kunt de traditionele wake-uppakketmethode aanvullen met behulp van de wake-up proxyclient-instellingen. Wake-up proxy gebruikt een peer-to-peer-protocol en geselecteerde computers om te controleren of andere computers op het subnet zijn ingeschakeld, en indien nodig te activeren. Wanneer de site is geconfigureerd voor Wake On LAN en clients zijn geconfigureerd voor wake-up proxy, werkt het proces als volgt:  

1.  Computers met de Configuration Manager-client is geïnstalleerd en die zijn niet actief op het subnet, controleren of andere computers op het subnet zijn ingeschakeld. Ze doen dit met het verzenden van elkaar een TCP/IP-ping-opdracht om de vijf seconden.  

2.  Als er geen reactie van andere computers, wordt uitgegaan van te zijn in de slaapstand bevindt. De computers die actief zijn geworden *beheercomputer* voor het subnet.  

     Omdat het is mogelijk dat een computer niet vanwege een reden dan reageert mogelijk is het in de slaapstand bevindt (bijvoorbeeld, als deze is uitgeschakeld, verwijderd uit het netwerk of de wake-up proxyclient instelling niet meer wordt toegepast), de computers een ontwaakpakket worden verzonden elke dag om 14: 00 lokale tijd. Computers die niet reageren wordt niet langer aangenomen dat deze worden in de slaapstand bevindt en wordt niet meer benaderd via wake-up proxy.  

     Ter ondersteuning van wake-up proxy moet ten minste drie computers actief is voor elk subnet. Om dit te bereiken, zijn niet-deterministische wijze drie computers gekozen als *guardian computers* voor het subnet. Dit betekent dat deze ingeschakeld blijven, ondanks eventueel geconfigureerd energiebeheerbeleid voor slaapstand of sluimerstand na een periode van inactiviteit. Guardian computers inwilligen afsluiten of opnieuw opdrachten, bijvoorbeeld als gevolg van onderhoudstaken. Als dit gebeurt, wordt de overige computers in de guardian wake een andere computer op het subnet zodat het subnet heeft nog steeds drie guardian-computers.  

3.  Beheercomputers verzenden een aanvraag van de netwerkswitch om netwerkverkeer voor de slapende computers naar zichzelf.  

     Het omleiden wordt verwezenlijkt doordat de beheercomputer een Ethernet-frame die gebruikmaakt van de MAC-adres van de computer in de slaapstand als bronadres uitzendt. Hierdoor kunt u de netwerkswitch gedragen zich alsof de computer in slaapstand is verplaatst naar de poort die de beheercomputer wordt. De beheercomputer verzendt tevens ARP-pakketten voor de slapende computers, zodat de vermelding in de ARP-cache actueel houden. De beheercomputer zal ook reageren op ARP-aanvragen namens de slaapstand computer en de antwoord met de MAC-adres van de computer in de slaapstand.  

    > [!WARNING]  
    >  Tijdens dit proces blijft de IP-aan-MAC-toewijzing voor de computer in slaapstand hetzelfde. Wake-up proxy werkt door de netwerkswitch wordt geïnformeerd dat een andere netwerkadapter de poort die is geregistreerd door een andere netwerkadapter wordt gebruikt. Dit gedrag is echter staat bekend als de term MAC flap en is ongebruikelijk voor standaardnetwerkbewerkingen. Sommige controleprogramma's voor netwerk zoekt u naar dit gedrag en nemen mogelijk aan dat er iets mis is. Als gevolg daarvan kunnen deze hulpmiddelen voor Netwerkcontrole waarschuwingen genereren of poorten afsluiten wanneer u wake-up proxy gebruikt.  
    >   
    >  Wake-up proxy niet gebruiken als uw hulpmiddelen voor Netwerkcontrole en services MAC flaps niet toestaan.  

4.  Wanneer een beheercomputer een nieuwe TCP-verbindingsaanvraag voor een computer in slaapstand en de aanvraag voor een poort op die computer in de slaapstand werd geluisterd is voordat ingeschakeld, wordt de beheercomputer een ontwaakpakket verzonden naar de computer in slaapstand en stopt omleiden van verkeer voor deze computer.  

5.  De computer in slaapstand ontvangt het ontwaakpakket en ontwaakt. De verzendende computer automatisch opnieuw geprobeerd de verbinding en deze tijd de computer actief is en kan reageren.  

 Wake-up proxy kent de volgende vereisten en beperkingen:  

> [!IMPORTANT]  
>  Hebt u een afzonderlijk team dat verantwoordelijk is voor de netwerkinfrastructuur en de netwerkservices, melden en dit team betrekken bij uw evaluatie en testperiode. Bijvoorbeeld, wake-up proxy in een netwerk met 802.1 X netwerktoegangsbeheer,-werkt niet en de netwerkservice kan verstoren. Wake-up proxy kan bovendien ervoor zorgen dat sommige hulpmiddelen voor het genereren van waarschuwingen wanneer de hulpprogramma's voor het verkeer wake-up van andere computers detecteren voor netwerkbeheer.  

-   De ondersteunde clients zijn Windows 7, Windows 8, Windows Server 2008 R2, Windows Server 2012.  

-   Gastbesturingssystemen die worden uitgevoerd op een virtuele machine worden niet ondersteund.  

-   Clients moeten zijn ingeschakeld voor wake-up proxy met clientinstellingen. Hoewel wake-up proxybewerking is niet afhankelijk van hardware-inventaris, clients niet gerapporteerd, de installatie van de wake-up proxyservice tenzij ze zijn ingeschakeld voor hardware-inventaris en ingediende ten minste één hardware-inventaris.  

-   Netwerk-adapters (en mogelijk de BIOS) moeten zijn ingeschakeld en geconfigureerd voor wake-uppakketten. Als de netwerkadapter is niet geconfigureerd voor wake-uppakketten of deze instelling is uitgeschakeld, wordt Configuration Manager automatisch configureren en inschakelen voor een computer wanneer de clientinstelling voor wake-up proxy inschakelen wordt ontvangen.  

-   Als een computer meer dan één netwerkadapter heeft, configureren niet u welke adapter te gebruiken voor wake-up proxy; de gekozen is niet-deterministisch. De gekozen adapter wordt echter vastgelegd in het bestand SleepAgent_ < DOMAIN\> @SYSTEM_0.log bestand.  

-   Het netwerk moet ICMP-echoaanvragen toestaan (ten minste binnen het subnet). U kunt het interval dat wordt gebruikt voor het verzenden van de ICMP ping-opdrachten van vijf seconden niet configureren.  

-   Communicatie wordt niet versleuteld en niet-geverifieerd en IPsec wordt niet ondersteund.  

-   De volgende netwerkconfiguraties worden niet ondersteund:  

    -   802. 1 X met Poortverificatie  

    -   Draadloze netwerken  

    -   Netwerkswitches die MAC-adressen aan bepaalde poorten binden  

    -   Alleen IPv6-netwerken  

    -   DHCP-leaseduur die minder dan 24 uur  

Als u computers inschakelt voor geplande software-installatie wilt, moet u elke primaire site voor het gebruik van wake-uppakketten configureren.  

 Voor het gebruik van wake-up proxy, moet u Energiebeheer voor wake-up proxyclient-instellingen naast het configureren van de primaire site implementeren.  

Ook moet u bepalen of subnet aangestuurde broadcastpakketten of unicastpakketten wilt gebruiken en welk UDP-poortnummer te gebruiken. Traditionele ontwaakpakketten worden verzonden via UDP-poort 9, maar om te helpen betere beveiliging, kunt u een alternatieve poort voor de site als deze alternatieve poort wordt ondersteund door interveniërende routers en firewalls.  

### <a name="choose-between-unicast-and-subnet-directed-broadcast-for-wake-on-lan"></a>Kies tussen Unicast en Subnet gerichte broadcasts voor Wake on LAN  
 Als u ervoor hebt gekozen om computers te activeren door te sturen van traditionele ontwaakpakketten, moet u beslissen of unicastpakketten of subnet gerichte broadcastpakketten verzendt. Als u wake-up proxy gebruikt, moet u unicastpakketten gebruiken. Gebruik anders de volgende tabel om te bepalen welke verzendingsmethode u om te kiezen.  

|Verzendingsmethode|Gebruik|Nadeel|  
|-------------------------|---------------|------------------|  
|Unicast|Een veiligere oplossing dan het subnet gerichte broadcasts omdat het pakket rechtstreeks naar een computer in plaats van naar alle computers in een subnet wordt verzonden.<br /><br /> Mogelijk niet herconfiguratie routers (mogelijk moet de ARP-cache configureren).<br /><br /> Verbruikt minder netwerkbandbreedte dan subnet gerichte broadcastverzendingen.<br /><br /> Ondersteund met IPv4 en IPv6.|Wake-uppakketten doelcomputers die het subnetadres is gewijzigd na de laatste hardware-inventarisplanning niet kunt vinden.<br /><br /> Switches wellicht worden geconfigureerd voor het doorsturen van UDP-pakketten.<br /><br /> Sommige netwerkadapters reageren mogelijk niet wake-up pakketten in alle slaapstatussen gemeld wanneer ze unicast gebruiken als de verzendingsmethode.|  
|Subnet gerichte broadcasts|Een hoger succespercentage dan unicast als u computers hebt die vaak hun IP-adres in hetzelfde subnet wijzigen.<br /><br /> Switches is niet vereist.<br /><br /> Een hoog compatibiliteitspercentage met computeradapters voor alle slaapstatussen sprake omdat subnet gerichte broadcasts de oorspronkelijke verzendingsmethode voor het verzenden van ontwaakpakketten.|Minder veilige oplossing dan het gebruik van unicast omdat een aanvaller ononderbroken streams van ICMP-echoaanvragen vanaf een vals bronadres naar het gerichte broadcastadres verzenden kan. Dit zorgt ervoor dat alle hosts het desbetreffende bronadres beantwoorden. Als routers zijn geconfigureerd voor het toestaan van subnet gerichte broadcasts, wordt de aanvullende configuratie aanbevolen vanwege veiligheidsredenen:<br /><br /> -Configureer routers zodat alleen op IP gerichte broadcasts vanaf de Configuration Manager siteserver, met behulp van een opgegeven UDP-poortnummer.<br />-Configuration Manager voor het gebruik van het opgegeven niet-standaard poortnummer configureren.<br /><br /> Mogelijk herconfiguratie van alle interveniërende routers subnet gerichte broadcasts inschakelen.<br /><br /> Verbruikt meer netwerkbandbreedte dan unicastverzendingen.<br /><br /> Ondersteund voor IPv4. IPv6 wordt niet ondersteund.|  

> [!WARNING]  
>  Er zijn beveiligingsrisico's die zijn gekoppeld aan het subnet gerichte broadcasts: Een aanvaller kan ononderbroken streams van Internet Control Message Protocol (ICMP) echoaanvragen vanaf een vals bronadres naar het gerichte broadcastadres dit leidt ertoe dat alle hosts het desbetreffende bronadres beantwoorden verzenden. Dit type denial of service-aanval wordt gewoonlijk aangeduid met een term smurf-aanval en wordt gematigd door het subnet gerichte broadcasts niet in te schakelen.
