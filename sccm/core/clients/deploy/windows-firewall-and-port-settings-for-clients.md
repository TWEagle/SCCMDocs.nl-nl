---
title: Windows firewall- en poortinstellingen clientinstellingen | Microsoft Docs
description: Selecteer Windows Firewall- en poortinstellingen voor clients in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dce4b640-c92f-401a-9873-ce9aa9262014
caps.latest.revision: "8"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 79686514efcba344c4babc3d3be03b48adca7132
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="windows-firewall-and-port-settings-for-clients-in-system-center-configuration-manager"></a>Instellingen voor Windows Firewall- en poortinstellingen voor clients in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Client-computers in System Center Configuration Manager die vaak Windows Firewall uitvoeren, moet u uitzonderingen configureert om te communicatie toestaat met hun site. De uitzonderingen die u moet configureren, is afhankelijk van de beheerfuncties die u met Configuration Manager-client gebruikt.  

 Gebruik de volgende secties om deze beheerfuncties te identificeren en voor meer informatie over hoe Windows Firewall te configureren voor deze uitzonderingen.  

##  <a name="BKMK_ModifyingWindowsFirewall"></a> De poorten en programma's toegestaan door Windows Firewall wijzigen  
 Gebruik de volgende procedure om te wijzigen van de poorten en programma's op Windows Firewall voor de Configuration Manager-client.  

#### <a name="to-modify-the-ports-and-programs-permitted-by-windows-firewall"></a>De door Windows Firewall toegstane poorten en programma's wijzigen  

1.  Open configuratiescherm op de computer waarop Windows Firewall uitgevoerd wordt.  

2.  Klik met de rechtermuisknop op **Windows Firewall**en klik dan op **Open**.  

3.  Configureer vereiste uitzonderingen en aangepaste programma's en poorten die u wenst.  

## <a name="programs-and-ports-that-configuration-manager-requires"></a>Programma's en poorten die Configuration Manager vereist  
 De volgende Configuration Manager-functies vereisen uitzonderingen op de Windows Firewall:  

### <a name="queries"></a>Query's  
 Als u de Configuration Manager-console op een computer met Windows Firewall uitvoert, query's mislukken de eerste keer dat ze worden uitgevoerd en het besturingssysteem geeft een dialoogvenster waarin wordt gevraagd of u statview.exe wilt deblokkeren. Indien u statview.exe deblokkeert zullen volgende query's zonder problemen uitgevoerd worden. U kunt ook handmatig Statview.exe toevoegen aan de lijst van prgramma's en diensten op het tabblad **Uitzonderingen** van de Windows Firewall vóór u een query uitvoert.  

### <a name="client-push-installation"></a>Clientpushinstallatie  
 Gebruik client-push voor Configuration Manager-client te installeren, voeg de volgende als uitzonderingen voor Windows Firewall:  

-   Uitgaande en binnenkomende: **Bestands- en printerdeling**  

-   Binnenkomend: **Windows Management Instrumentation (WMI)**  

### <a name="client-installation-by-using-group-policy"></a>Installatie van de client via groepsbeleid  
 Voor het gebruik van Groepsbeleid om de Configuration Manager-client te installeren, Voeg **bestands- en printerdeling** als uitzondering aan de Windows Firewall.  

### <a name="client-requests"></a>Aanvragen van client  
 Voor clientcomputers om te communiceren met sitesystemen van Configuration Manager, voegt u het volgende als uitzonderingen voor Windows Firewall:  

 Uitgaand: TCP-poort **80** (voor HTTP-communicatie)  

 Uitgaand: TCP-poort **443** (voor HTTPS-communicatie)  

> [!IMPORTANT]  
>  Dit zijn standaardpoortnummers die kunnen worden gewijzigd in Configuration Manager. Zie voor meer informatie hoe [clientcommunicatiepoorten in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-communication-ports.md). Indien deze poorten gewijzigd zijn ten opzichte van hun standaardwaarden, moet u ook overeenkomstige uitzonderingen configureren op de Windows Firewall.  

### <a name="client-notification"></a>Clientmeldingen  
 Voor het beheerpunt te waarschuwen clientcomputers een actie die moet worden uitgevoerd wanneer een gebruiker met beheerdersrechten een clientactie in de Configuration Manager-console, zoals selecteert computerbeleid voor downloaden of het initiëren van een scan op malware, Voeg het volgende toe als uitzondering aan de Windows Firewall:  

 Uitgaand: TCP-poort **10123**  

 Indien deze communicatie niet slaagt, terugvalt Configuration Manager automatisch op met de bestaande client-naar-beheerpunt communicatiepoort van HTTP of HTTPS:  

 Uitgaand: TCP-poort **80** (voor HTTP-communicatie)  

 Uitgaand: TCP-poort **443** (voor HTTPS-communicatie)  

> [!IMPORTANT]  
>  Dit zijn standaardpoortnummers die kunnen worden gewijzigd in Configuration Manager. Zie voor meer informatie [clientcommunicatiepoorten in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-communication-ports.md). Indien deze poorten gewijzigd zijn ten opzichte van hun standaardwaarden, moet u ook overeenkomstige uitzonderingen configureren op de Windows Firewall.  

### <a name="remote-control"></a>Extern beheer  
 Toestaan dat de volgende poort voor het gebruik van beheer op afstand Configuration Manager:  

-   Binnenkomend: TCP-poort**2701**  

### <a name="remote-assistance-and-remote-desktop"></a>Hulp op afstand en extern bureaublad  
 Voeg het aangepaste programma voor hulp op afstand initieert van de Configuration Manager-console, **Helpsvc.exe** en de inkomende aangepaste TCP-poort **135** aan de lijst met toegestane programma's en services in Windows Firewall op de clientcomputer. U moet ook **Hulp op afstand** en **Extern bureaublad**toestaan. Indien u Hulp op afstand initieert van de clientcomputer, configureert Firewall automatisch **Hulp op afstand** en **Extern bureaublad**en laat ze ook toe.  

### <a name="wake-up-proxy"></a>Wake-Up proxy  
 Indien u de instelling voor wake-up proxy client inschakelt, gebruikt een nieuwe service met de naam ConfigMgr wake-up proxy een peer-to-peer protocol om te controleren of er computers actief zijn op het subnet en om ze indien nodig te activeren. Deze mededeling maakt gebruik van de volgende poorten:  

 Uitgaand: UDP-poort **25536**  

 Uitgaand: UDP-poort **9**  

 Dit zijn de standaardpoortnummers die kunnen worden gewijzigd in Configuration Manager met behulp van de **energiebeheer** instellingen van clients van **Wake-up proxypoortnummer (UDP)** en **Wake On LAN-pooortnummer (UDP)**. Als u opgeeft de **energiebeheer**: **Windows Firewall-uitzondering voor wake-up proxy** client, deze poorten worden automatisch geconfigureerd in Windows Firewall voor clients. Indien clients evenwel een verschillende firewall uitvoeren, moet u handmatig de uitzonderingen voor deze poortnummers configureren.  

 Behalve deze poorten gebruikt wake-up proxy ook Internet Control Message Protocol (ICMP) echoaanvraagberichten van één clientcomputer aan een andere clientcomputer. Deze communicatie wordt gebruikt om te bevestigen of de andere clientcomputer actief is op het netwerk. Naar ICMP wordt soms verwezen als TCP/IP-pingopdrachten.  

 Zie voor meer informatie over wake-up proxy [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

### <a name="windows-event-viewer-windows-performance-monitor-and-windows-diagnostics"></a>Logboeken van Windows, prestatiemeter van Windows en Windows diagnostische gegevens  
 Voor toegang tot logboeken van Windows, Prestatiemeter van Windows en Windows diagnostische gegevens van de Configuration Manager-console, inschakelen **bestands- en printerdeling** als een uitzondering op de Windows Firewall.  

## <a name="ports-used-during-configuration-manager-client-deployment"></a>Poorten die worden gebruikt tijdens de implementatie van de Configuration Manager-client  
 De volgende tabellen geeft de lijst van de poorten die gebruikt worden tijdens het installatieproces van de klant.  

> [!IMPORTANT]  
>  Bevestig, indien er een firewall is tussen de sitesysteemservers en de clientcomputer, of de firewall verkeer toestaat voor de poorten die vereist zijn voor de clientinstallatiemethode die u kiest. Firewalls verhinderen bijvoorbeeld dikwijls het succes van clientpushinstallatie omdat ze Server Message Block (SMB) en Remote Procedure Calls (RPC) blokkeren. Gebruik in dit scenario een andere clientinstallatiemethode, zoals handmatige installatie (uitvoeren van CCMSetup.exe) of groepsbeleid-gebaseerde clientinstallatie. Deze alternatieve clientinstallatiemethodes vereisen geen SMB of RPC.  

 Voor informatie over hoe Windows Firewall te configureren op de clientcomputer, zie [De poorten en programma's toegestaan door Windows Firewall wijzigen](#BKMK_ModifyingWindowsFirewall).  

### <a name="ports-that-are-used-for-all-installation-methods"></a>Poorten die worden gebruikt voor alle installatiemethoden  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP) van de clientcomputer naar een terugvalstatuspunt, wanneer een terugvalstatuspunt toegekend is aan de client.|--|80 (zie opmerking 1, **alternatieve poort beschikbaar**)|  

### <a name="ports-that-are-used-with-client-push-installation"></a>Poorten die worden gebruikt met clientpushinstallatie  
 Behalve de poorten die voorkomen in de lijst in de volgende tabel, gebruikt clientpushinstallatie ook Internet Control Message Protocol (ICMP) echoaanvraagberichten van de siteserver naar de clientcomputer om te bevestigen of de clientcomputer beschikbaar is op het netwerk. Naar ICMP wordt soms verwezen als TCP/IP-pingopdrachten. ICMP heeft geen UDP- of TCP-protocolnummer en komt dus niet voor op de lijst in de volgende tabel. Alle tussenliggende netwerkapparaten, zoals firewalls, moeten evenwel ICMP-verkeer toestaan opdat de clientpushinstallatie zou slagen.  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB) tussen de siteserver en clientcomputer.|--|445|  
|RPC eindpunttoewijzer tussen de siteserver en de clientcomputer.|135|135|  
|RPC dynamische poorten tussen de siteserver en de clientcomputer.|--|DYNAMISCH|  
|Hypertext Transfer Protocol (HTTP) van de clientcomputer naar een beheerpunt, wanneer de verbinding over HTTP gebeurt.|--|80 (zie opmerking 1, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS) van de clientcomputer naar een beheerpunt, wanneer de verbinding over HTTPS gebeurt.|--|443 (zie opmerking 1, **alternatieve poort beschikbaar**)|  

### <a name="ports-that-are-used-with-software-update-point-based-installation"></a>Poorten die worden gebruikt met punt-gebaseerde installatie van software-update  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP) van de clientcomputer naar het software-updatepunt.|--|80 of 8530 (zie opmerking 2, **Windows Server Update Services**)|  
|Secure Hypertext Transfer Protocol (HTTPS) van de clientcomputer naar het software-updatepunt.|--|443 of 8531 (zie opmerking 2, **Windows Server Update Services**)|  
|Server Message Block (SMB) tussen de bronserver en de clientcomputer wanneer u de CCMSetup-opdrachtregel-eigenschap opgeeft **/source:&lt;pad\>**.|--|445|  

### <a name="ports-that-are-used-with-group-policy-based-installation"></a>Poorten die worden gebruikt met installatie op basis van groepsbeleid  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Hypertext Transfer Protocol (HTTP) van de clientcomputer naar een beheerpunt, wanneer de verbinding over HTTP gebeurt.|--|80 (zie opmerking 1, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS) van de clientcomputer naar een beheerpunt, wanneer de verbinding over HTTPS gebeurt.|--|443 (zie opmerking 1, **alternatieve poort beschikbaar**)|  
|Server Message Block (SMB) tussen de bronserver en de clientcomputer wanneer u de CCMSetup-opdrachtregel-eigenschap opgeeft **/source:&lt;pad\>**.|--|445|  

### <a name="ports-that-are-used-with-manual-installation-and-logon-script-based-installation"></a>Poorten die gebruikt worden bij handmatige installatie en bij installatie gebaseerd op aanmeldingsscript  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB) tussen de clientcomputer en een netwerkshare van waaruit u CCMSetup.exe uitvoert.<br /><br /> Wanneer u Configuration Manager installeert, de bronbestanden van de client-installatie zijn gekopieerd en automatisch gedeeld van de  *&lt;InstallationPath\>*map \Client op beheerpunten. U kunt evenwel deze bestanden kopiëren en een nieuwe share creëren op een computer op het netwerk. Alternatief kunt u dit netwerkverkeer elimineren door lokaal CCMSetup.exe uit te voeren door, bijvoorbeeld, verwisselbare media te gebruiken.|--|445|  
|Hypertext Transfer Protocol (HTTP) vanaf de clientcomputer naar een beheerpunt wanneer de verbinding via HTTP, en u niet de CCMSetup opdrachtregeleigenschap geeft **/source:&lt;pad\>**.|--|80 (zie opmerking 1, **alternatieve poort beschikbaar**)|  
|Hypertext Transfer Protocol (HTTPS) beveiligen vanaf de clientcomputer naar een beheerpunt, wanneer de verbinding via HTTPS is en u niet de CCMSetup opdrachtregeleigenschap **/source:&lt;pad\>**.|--|443 (zie opmerking 1, **alternatieve poort beschikbaar**)|  
|Server Message Block (SMB) tussen de bronserver en de clientcomputer wanneer u de CCMSetup-opdrachtregel-eigenschap opgeeft **/source:&lt;pad\>**.|--|445|  

### <a name="ports-that-are-used-with-software-distribution-based-installation"></a>Poorten die worden gebruikt met installatie gebaseerd op softwaredistributie  

|Beschrijving|UDP|TCP|  
|-----------------|---------|---------|  
|Server Message Block (SMB) tussen het distributiepunt en de clientcomputer.|--|445|  
|Hypertext Transfer Protocol (HTTP) van de client naar een distributiepunt, wanneer de verbinding over HTTP gebeurt.|--|80 (zie opmerking 1, **alternatieve poort beschikbaar**)|  
|Secure Hypertext Transfer Protocol (HTTPS) van de client naar een distributiepunt, wanneer de verbinding over HTTPS gebeurt.|--|443 (zie opmerking 1, **alternatieve poort beschikbaar**)|  

## <a name="notes"></a>Opmerkingen  
 **1 alternatieve poort beschikbaar** In Configuration Manager, u kunt een alternatieve poort definiëren voor deze waarde. Indien een aangepaste poort is gedefinieerd, vervang dan deze aangepaste poort wanneer u de IP-filter informatie definieert voor IPsec beleidslijnen of om firewalls te configureren.  

 **2 Windows Server Update Services** U kunt Windows Server Update Service (WSUS) installeren op de standaardwebsite (poort 80) of op een aangepaste website (poort 8530).  

 Na de installatie kunt u de poort te wijzigen. U moet niet hetzelfde poortnummer gebruiken over de hele sitehiërarchie.  

 Als de HTTP-poort 80 is, moet de HTTPS-poort 443 zijn.  

 Als de HTTP-poort iets anders is, moet de HTTPS-poort 1 hoger zijn. Bijvoorbeeld 8530 en 8531.
