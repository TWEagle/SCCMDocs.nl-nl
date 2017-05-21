---
title: Deze clients | Microsoft-documenten
description: Plannen voor ontwaken van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52ee82b2-0b91-4829-89df-80a6abc0e63a
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 20f595a5b0634a627dff9ba6feeb848754615f2c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="plan-how-to-wake-up-clients-in-system-center-configuration-manager"></a>Plannen voor ontwaken van clients in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Configuration Manager ondersteunt twee wake-on-LAN (local area network)-technologieën om computers in de slaapstandmodus activeren als u wilt installeren van vereiste software, zoals software-updates en toepassingen: traditionele wake-uppakketten en AMT-inschakelopdrachten.  

U kunt de traditionele wake-uppakketmethode aanvullen door de wake-up proxyclient-instellingen. Wake-up proxy gebruikt een peer-to-peer-protocol en geselecteerde computers om te controleren of andere computers op het subnet zijn ingeschakeld en om ze indien nodig te activeren. Als de site is geconfigureerd voor Wake On LAN en clients zijn geconfigureerd voor wake-up proxy, werkt het proces als volgt:  

1.  Computers met de Configuration Manager-client is geïnstalleerd en die zijn niet actief op het subnet, controleren of andere computers op het subnet zijn ingeschakeld. Dit doen ze verzenden hiertoe een TCP/IP-ping-opdracht om de vijf seconden.  

2.  Als er geen reactie van andere computers, wordt aangenomen dat verzonden om te worden in de slaapstand bevindt. De computers die actief zijn worden *beheercomputer* voor het subnet.  

     Omdat het mogelijk dat een computer niet vanwege een reden uitzondering reageren mogelijk is het in de slaapstand bevindt (bijvoorbeeld is uitgeschakeld, verwijderd uit het netwerk of de wake-up proxyclient instelling is niet langer van toepassing), de computers een ontwaakpakket worden verzonden elke dag om 2 uur lokale tijd. Computers die niet reageren wordt niet langer aangenomen dat deze zich in de slaapstand bevinden en wordt niet meer benaderd via wake-up proxy.  

     Ondersteunen van wake-up proxy moet ten minste drie actieve computers aanwezig zijn voor elk subnet. Om dit te doen, worden niet-deterministische wijze drie computers gekozen als *bewakers* voor het subnet. Dit betekent dat deze ingeschakeld blijven, ondanks eventueel geconfigureerd energiebeheerbeleid voor slaapstand of sluimerstand na een periode van inactiviteit. Bewakers als afsluiten en opstarten opdrachten, bijvoorbeeld, als gevolg van onderhoudstaken. Als dit gebeurt, halen de overige guardian computers een andere computer op het subnet, zodat het subnet opnieuw over drie guardian computers beschikt.  

3.  Beheercomputers verzenden een aanvraag van de netwerkswitch om netwerkverkeer voor de slapende computers om te leiden.  

     Het omleiden wordt verwezenlijkt doordat de beheercomputer een Ethernet-frame uitzendt dat MAC-adres voor de computer in de slaapstand als bronadres gebruikt. Hierdoor kunt u de netwerkswitch zich gedragen als de computer in slaapstand is verplaatst naar de poort die de beheercomputer ingeschakeld is. De beheercomputer verzendt tevens ARP-pakketten voor de slapende computers, zodat de vermelding in de ARP-cache actueel blijft. De beheercomputer ook reageert ARP-aanvragen namens de slaapstand computer en beantwoorden met de MAC-adres van de computer in slaapstand.  

    > [!WARNING]  
    >  Tijdens dit proces blijft de IP-aan-MAC-toewijzing voor de computer in slaapstand hetzelfde. Wake-up proxy werkt volgens de netwerkswitch geïnformeerd dat een andere netwerkadapter de poort die is geregistreerd door een andere netwerkadapter wordt gebruikt. Dit gedrag is echter staat bekend als MAC flap en is ongebruikelijk voor standaardnetwerkbewerkingen. Sommige hulpmiddelen voor Netwerkcontrole detecteren dit gedrag en nemen mogelijk aan dat er iets mis is. Als gevolg daarvan kunnen deze hulpmiddelen voor Netwerkcontrole meldingen genereren of poorten afsluiten wanneer u wake-up proxy.  
    >   
    >  Gebruik wake-up proxy niet als uw Netwerkcontrole hulpprogramma's en service MAC flaps niet toestaan.  

4.  Wanneer een beheercomputer een nieuwe TCP-verbindingsaanvraag voor een computer in slaapstand en de aanvraag naar een poort waarop de computer in slaapstand werd geluisterd is voordat de ingeschakeld, wordt de beheercomputer een ontwaakpakket verzendt naar de computer in slaapstand en wordt het omleiden van verkeer voor deze computer gestopt.  

5.  De computer in slaapstand ontvangt het ontwaakpakket en wordt weer actief. De verzendende computer probeert automatisch opnieuw verbinding maken en deze keer kan de computer inmiddels actief is, reageren.  

 Wake-up proxy kent de volgende vereisten en beperkingen:  

> [!IMPORTANT]  
>  Als u een afzonderlijk team dat verantwoordelijk is voor de netwerkinfrastructuur en Netwerkservice, informeren over en dit team te betrekken bij uw evaluatie en testperiode. Bijvoorbeeld, wake-up proxy in een netwerk met 802. 1 X-netwerktoegangsbeheer-werkt niet en kan de netwerkservice worden onderbroken. Bovendien wake-up proxy leiden dat sommige hulpmiddelen voor het genereren van waarschuwingen wanneer de hulpmiddelen verkeer wake-up van andere computers detecteren netwerkbeheer.  

-   De ondersteunde clients zijn Windows 7, Windows 8, Windows Server 2008 R2, Windows Server 2012.  

-   Gastbesturingssystemen die worden uitgevoerd op een virtuele machine worden niet ondersteund.  

-   Clients moeten via clientinstellingen zijn ingesteld voor wake-up proxy. Hoewel wake-up proxy niet afhankelijk is hardware-inventaris, clients niet gerapporteerd, de installatie van de wake-up proxyservice tenzij deze zijn ingeschakeld voor hardware-inventaris en ingediende ten minste één hardware-inventaris.  

-   Netwerk-adapters (en mogelijk de BIOS) moeten zijn ingeschakeld en geconfigureerd voor ontwaakpakketten. Als de netwerkadapter is niet geconfigureerd voor wake-uppakketten of deze instelling is uitgeschakeld, wordt automatisch Configuration Manager configureren en inschakelen voor een computer, krijgt de clientinstelling voor wake-up proxy inschakelen.  

-   Als een computer meer dan één netwerkadapter heeft, configureren u niet welke adapter voor wake-up proxy; de keuze komt op een niet-deterministisch. De gekozen adapter wordt echter vastgelegd in het bestand SleepAgent_ < DOMAIN\> @SYSTEM_0.log bestand.  

-   Het netwerk moet ICMP-echoaanvragen toestaan (ten minste binnen het subnet). U kunt het interval dat wordt gebruikt voor het verzenden van de ICMP ping-opdrachten van vijf seconden niet configureren.  

-   Communicatie wordt niet versleuteld en niet-geverifieerd en IPsec wordt niet ondersteund.  

-   De volgende netwerkconfiguraties worden niet ondersteund:  

    -   802.1 X met Poortverificatie  

    -   Draadloze netwerken  

    -   Netwerkswitches die MAC-adressen aan bepaalde poorten binden  

    -   Netwerken die alleen IPv6  

    -   DHCP-leaseduur die korter is dan 24 uur  

Als u wilt dat computers inschakelt voor geplande software-installatie, moet u elke primaire site voor het gebruik van wake-uppakketten configureren.  

 Wake-up proxy wilt gebruiken, moet u clientinstellingen voor energiebeheer voor wake-up proxy naast het configureren van de primaire site implementeren.  

U moet ook bepalen of subnet aangestuurde broadcastpakketten of unicastpakketten wilt gebruiken en welk UDP-poortnummer moet worden gebruikt. Traditionele wake-uppakketten worden verzonden via UDP-poort 9, maar om te helpen de beveiliging verbeteren, kunt u een alternatieve poort voor de site selecteren als deze alternatieve poort wordt ondersteund door interveniërende routers en firewalls.  

### <a name="choose-between-unicast-and-subnet-directed-broadcast-for-wake-on-lan"></a>Kies tussen Unicast en op het Subnet gerichte broadcasts voor Wake-on-LAN  
 Als u ervoor om computers te activeren kiest door het verzenden van traditionele ontwaakpakketten, moet u bepalen of u unicastpakketten of op het subnet gerichte broadcastpakketten verzendt. Als u wake-up proxy gebruikt, moet u unicastpakketten gebruiken. Gebruik anders de volgende tabel om te bepalen welke Verzendingsmethode om te kiezen.  

|Verzendingsmethode|Gebruik|Nadeel|  
|-------------------------|---------------|------------------|  
|Unicast|Een veiligere oplossing dan op het subnet gerichte broadcasts omdat het pakket rechtstreeks naar een computer in plaats van naar alle computers in een subnet wordt verzonden.<br /><br /> Vereist mogelijk niet dat routers (mogelijk moet u de ARP-cache configureren) opnieuw worden geconfigureerd.<br /><br /> Verbruikt minder netwerkbandbreedte dan op het subnet gerichte broadcastverzendingen.<br /><br /> Ondersteund met IPv4 en IPv6.|Wake-uppakketten doelcomputers waarvan het subnetadres is gewijzigd sinds de laatste hardware-inventarisplanning niet kunt vinden.<br /><br /> Switches mogelijk moet worden geconfigureerd voor het doorsturen van UDP-pakketten.<br /><br /> Sommige netwerkadapters reageren mogelijk niet wake-up in alle slaapstatussen op ontwaakpakketten wanneer deze unicast gebruiken als de verzendingsmethode.|  
|Subnet gerichte broadcasts|Een hoger succespercentage dan unicast als uw computers regelmatig het IP-adres in hetzelfde subnet wijzigt.<br /><br /> Configureren van switches is vereist.<br /><br /> Een hoog compatibiliteitspercentage met computeradapters voor alle slaapstatussen sprake, omdat het subnet gerichte broadcasts de oorspronkelijke verzendingsmethode waren voor wake-uppakketten worden verzonden.|Minder veilige oplossing dan het gebruik van unicast omdat een aanvaller zou ononderbroken streams van ICMP verzenden kunnen-echoaanvragen vanaf een vals bronadres naar het gerichte broadcastadres. Dit leidt ertoe dat alle hosts het desbetreffende bronadres beantwoorden. Als routers zijn geconfigureerd voor het toestaan van subnet gerichte broadcasts, wordt de aanvullende configuratie om veiligheidsredenen aanbevolen:<br /><br /> -Configureer routers zodat alleen op IP gerichte broadcasts vanaf de Configuration Manager siteserver, met behulp van een opgegeven UDP-poortnummer.<br />-Configuratiebeheer voor het gebruik van het opgegeven niet-standaardpoortnummer configureren.<br /><br /> Vereist mogelijk dat alle interveniërende routers om in te schakelen van subnet gerichte broadcasts opnieuw worden geconfigureerd.<br /><br /> Dit verbruikt meer netwerkbandbreedte dan unicastverzendingen.<br /><br /> Ondersteund voor IPv4. IPv6 wordt niet ondersteund.|  

> [!WARNING]  
>  Er zijn beveiligingsrisico's gekoppeld aan het subnet gerichte broadcasts: Een aanvaller kan ononderbroken streams van Internet Control Message Protocol (ICMP) echoaanvragen verzenden vanaf een vals bronadres naar het gerichte broadcastadres dit leidt ertoe dat alle hosts het desbetreffende bronadres beantwoorden. Dit type denial of service-aanval wordt gewoonlijk aangeduid met de term smurf-aanval en wordt gematigd door het subnet gerichte broadcasts niet in te schakelen.

