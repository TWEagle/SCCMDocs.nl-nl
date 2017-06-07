---
title: Vereisten voor de implementatie van Windows client | Microsoft-documenten
description: Informatie over de vereisten voor de implementatie van clients op Windows-computers in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1a2a9b48-a95b-4643-b00c-b3079584ae2e
caps.latest.revision: 16
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 6636ce4d929326fad0210407d7634ea585eb0a2d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-deploying-clients-to-windows-computers-in-system-center-configuration-manager"></a>Vereisten voor het implementeren van clients op Windows-computers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Implementeren van Configuration Manager-clients in uw omgeving heeft de volgende externe afhankelijkheden en afhankelijkheden binnen het product. Bovendien, heeft elke client-implementatiemethode zijn eigen afhankelijkheden waaraan moet worden voldaan opdat de clientinstallaties succesvol zouden zijn.  

  Zorg ervoor dat u wordt ook aangeraden [ondersteunde configuraties voor System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md) om te bevestigen dat apparaten voorzien in de minimale vereisten voor hardware en het besturingssysteem voor de Configuration Manager-client.  

 Zie voor meer informatie over de vereisten voor de Configuration Manager-client voor Linux en UNIX [Planning voor clientimplementatie op Linux en UNIX-computers in System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).  

> [!NOTE]  
>  De in dit artikel vermelde softwareversienummers zijn alleen de minimaal vereiste versienummers.  

##  <a name="BKMK_prereqs_computers"></a>Vereisten voor computerclients  
 Gebruik de volgende informatie om de vereisten voor wanneer u de Configuration Manager-client op computers installeert te bepalen.  

### <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  

|||  
|-|-|  
|Windows Installer versie 3.1.4000.2435|Vereist om het gebruik van Windows Installer-update-(.msp)bestanden te gebruiken voor pakketten en software-updates.|  
|[KB2552033](http://go.microsoft.com/fwlink/p/?LinkId=240048)|Installeer deze hotfix op siteservers waarop Windows Server 2008 R2 wordt uitgevoerd wanneer clientpushinstallatie is ingeschakeld.|  
|Microsoft Background Intelligent Transfer Service (BITS) versie 2.5|Vereist voor de beperkte gegevensoverdracht tussen de clientcomputer en Configuration Manager-sitesystemen. BITS is niet automatisch gedownload tijdens de clientinstallatie. Wanneer BITS geïnstalleerd is op computers, is een opnieuw opstarten vereist om de installatie te vervolledigen.<br /><br /> De meeste besturingssystemen bevatten BITS, maar indien dit niet (bijvoorbeeld Windows Server 2003 R2 SP2), moet u BITS installeren voordat u de Configuration Manager-client installeert.|  
|Microsoft Task Scheduler|Schakel deze service in op de client om de clientinstallatie te voltooien.|  

### <a name="dependencies-external-to-configuration-manager-and-automatically-downloaded-during-installation"></a>Afhankelijkheden extern aan Configuration Manager en automatisch gedownload tijdens de installatie  
 De Configuration Manager-client heeft enkele potentiële externe afhankelijkheden. Deze afhankelijkheden hangen af van het besturingssysteem en de geïnstalleerde software op de clientcomputer.  

 Indien deze afhankelijkheden vereist zijn om de installatie van de client te vervolledigen, worden ze automatisch geïnstalleerd met de client software.  

|||  
|-|-|  
|Windows Update Agent versie 7.0.6000.363|Vereist door Windows ter ondersteuning van detectie van update en implementatie.|  
|Microsoft Core XML Services (MSXML) versie 6.20.5002 of hoger|Vereist voor ondersteuning voor de verwerking van XML-documenten in Windows.|  
|Microsoft Remote Differential Compression (RDC)|Vereist om gegevensoverdracht te optimaliseren via het netwerk.|  
|Microsoft Visual C++ 2013 Te distribueren pakket versie 12.0.21005.1|Vereist ter ondersteuning van clientbewerkingen. Als deze update op clientcomputers is geïnstalleerd, moeten ze mogelijk opnieuw worden opgestart om de installatie te voltooien.|  
|Microsoft Visual C++ 2005 Te distribueren pakket versie 8.0.50727.42|Vereist ter ondersteuning van Microsoft SQL Server Compact operaties voor versie 1606 en eerdere versies.|  
|Windows Imaging API's 6.0.6001.18000|Vereist voor Configuratiebeheer voor het beheren van Windows-installatiekopiebestanden (WIM).|  
|Microsoft-Beleidsplatform 1.2.3514.0|Vereist om clients toe te staan voor de evaluatie van de instellingen voor naleving.|  
|Microsoft Silverlight 5.1.41212.0 (begin in Configuration Manager versie 1602)|Vereist ter ondersteuning van de gebruikerservaring op Application Catalog-website.|  
|Microsoft .NET Framework versie 4.5.2|Vereist ter ondersteuning van clientbewerkingen. Automatisch geïnstalleerd op de clientcomputer als hierop geen Microsoft .NET Framework versie 4.5 of hoger is geïnstalleerd. Voor meer informatie, zie [Aanvullende informatie over Microsoft .NET Framework versie 4.5.2](#dotNet).|  
|Onderdelen van Microsoft SQL Server Compact 3.5 SP2|Vereist voor het opslaan van informatie met betrekking tot clientbewerkingen.|  
|Onderdelen van Microsoft Windows Imaging|Vereist door Microsoft .NET Framework 4.0 voor Windows Server 2003 of Windows XP SP2 voor 64-bits computers.|
|Microsoft Intune PC softwareclient|U kunt de Intune-PC software-client en de Configuration Manager-client niet uitvoeren op dezelfde PC. Zorg ervoor dat de Intune-client is verwijderd voordat u de Configuration Manager-client installeert.|

####  <a name="dotNet"></a>Aanvullende informatie over Microsoft .NET Framework 4.5.2 versie  

> [!NOTE]  
>  Op 12 januari 2016 is ondersteuning voor .NET 4.0, 4.5 en 4.5.1 verlopen. Zie [Veelgestelde vragen over Microsoft .NET Framework Support Lifecycle-beleid](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) op support.microsoft.com voor meer informatie.  

 Mogelijk moet het systeem opnieuw worden opgestart om de installatie van Microsoft .NET Framework versie 4.5.2 te voltooien. De gebruiker krijgt de melding **Opnieuw opstarten is vereist** te zien in het systeemvak.  Algemene scenario's waarin clientcomputers opnieuw moeten worden opgestart:  

-   .NET-toepassingen of -services worden op de computer uitgevoerd.  

-   Er ontbreken een of meer software-updates die voor de installatie van .NET vereist zijn.  

-   Het opnieuw opstarten van de computer is in behandeling voor een eerdere installatie van software-updates voor .NET Framework.  

 Nadat .NET Framework 4.5.2 is geïnstalleerd, kunnen er vervolgens aanvullende updates worden geïnstalleerd. Mogelijk moet hiervoor de computer nogmaals opnieuw worden opgestart.  

### <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  
 Voor meer informatie over de volgende sitesysteemrollen, zie de sectie [De sitesysteemrollen voor System Center Configuration Manager-clients bepalen](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

|||  
|-|-|  
|Beheerpunt|Hoewel een beheerpunt niet vereist zijn is om de Configuration Manager-client te implementeren, moet u een beheerpunt wordt informatie overgedragen tussen clientcomputers en Configuration Manager-servers hebben. Zonder een beheerpunt kunt u geen clientcomputers beheren.|  
|Distributiepunt|Het distributiepunt is een optioneel, maar aanbevolen sitesysteemrol voor clientimplementatie. Alle distributiepunten hosten de clientbronbestanden, die computers het meest nabije distributiepunt laten vinden waarvan de clientbronbestanden kunnen gedownload worden tijdens clientimplementatie. Indien de site geen distributiepunt heeft, downloaden de computers de bronbestanden van de client van hun beheerpunt.|  
|Terugvalstatuspunt|Het terugvalstatuspunt is een optioneel, maar aanbevolen sitesysteemrol voor clientimplementatie. Het terugvalsstatuspunt traceert clientimplementatie en schakelt computers in de Configuration Manager-site om statusberichten te zenden wanneer ze niet kunnen met een beheerpunt communiceren.|  
|Reporting Services-punt|Het Reporting Services-punt is een optionele, maar aanbevolen sitesysteemrol die rapporten kan weergeven gerelateerd aan clientimplementatie en -beheer. Zie [Rapportage in System Center Configuration Manager](../../../core/servers/manage/reporting.md) voor meer informatie.|  

### <a name="installation-method-dependencies"></a>Installatiemethode-afhankelijkheden  
 De volgende vereisten zijn specifiek voor de verschillende methodes van clientinstallatie.  

-   Clientpushinstallatie  

    -   Clientpushinstallatie-accounts worden gebruikt om te verbinden met computers om de client te installeren en zijn opgegeven op het tabblad **Accounts** van het dialoogvenster van de **Clientpushinstallatie-eigenschappen**. De account moet een lid zijn van de groep lokale beheerders op de doelcomputer.  

         Indien u geen clientpushinstallatie-account specificeert, zal de siteserver-computer-account gebruikt worden.  

    -   De computer waarop u de client installeren zijn gedetecteerd door ten minste één detectiemethode van Configuration Manager.  

    -   De computer heeft een ADMIN$-share.  

    -   **Schakel clientpushinstallatie voor toegewezen bronnen** moet worden geselecteerd in de **Clientpushinstallatie-eigenschappen** in het dialoogvenster als u wilt de Configuration Manager-client automatisch push gedetecteerde bronnen.  

    -   De clientcomputer moet in staat zijn om contact op te nemen met een distributie- of een beheerpunt om de ondersteunende bestanden te downloaden.  

     U moet de volgende beveiligingsmachtigingen nodig voor de Configuration Manager-client installeert met behulp van client-push hebben:  

    -   Account voor Push-clientinstallatie configureren: **Wijzig** en leesmachtiging voor het **Site** object.  

    -   Om clientpush te gebruiken voor het installeren van de client op verzamelingen, apparaten en query's: **Bron wijzigen** en **lezen** machtiging voor het verzamelingsobject.  

     De **Infrastructuur beheerder** beveiligingsrol bevat de vereiste machtigingen om de clientpushinstallatie te beheren.  

-   Installatie op basis van software-updatepunten  

    -   Als het Active Directory-schema niet is uitgebreid, of u installeert clients van een andere forest, moeten de installatie-eigenschappen voor CCMSetup.exe ingericht zijn in het register van de computer door gebruik te maken van groepsbeleid. Voor meer informatie, zie [Eigenschappen van clientinstallatie inrichten (groepsbeleid en clientinstallatie op basis van software-update)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   De Configuration Manager-client moet gepubliceerd zijn op het software-updatepunt.  

    -   De clientcomputer moet in staat zijn om contact op te nemen met een distributie- of een beheerpunt om de ondersteunende bestanden te downloaden.  

     Zie voor de vereiste machtigingen voor het beheren van Configuration Manager-software-updates, [vereisten voor software-updates in System Center Configuration Manager](../../../sum/plan-design/prerequisites-for-software-updates.md).  

-   Groepsbeleid-gebaseerde Installatie  

    -   Als het Active Directory-schema niet is uitgebreid, of u installeert clients van een andere forest, moeten de installatie-eigenschappen voor CCMSetup.exe ingericht zijn in het register van de computer door gebruik te maken van groepsbeleid. Voor meer informatie, zie [Eigenschappen van clientinstallatie inrichten (groepsbeleid en clientinstallatie op basis van software-update)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   De clientcomputer moet in staat zijn om contact op te nemen met een distributie- of een beheerpunt om de ondersteunende bestanden te downloaden.  

-   Aanmeldingscriptinstallatie  

     De clientcomputer moet in staat zijn om contact op te nemen met een distributie- of een beheerpunt om de ondersteunende bestanden te downloaden tenzij u bij de opdrachtprompt CCMSetup.exe hebt opgegeven met de opdrachtregel-eigenschap **ccmsetup /source**.  

-   Handmatige installatie  

     De clientcomputer moet in staat zijn om contact op te nemen met een distributie- of een beheerpunt om de ondersteunende bestanden te downloaden tenzij u bij de opdrachtprompt CCMSetup.exe hebt opgegeven met de opdrachtregel-eigenschap **ccmsetup /source**.  

-   Installatie van de computerwerkgroep  

     Voor toegang tot bronnen in het domein van Configuration Manager site server, moet het netwerktoegangsaccount worden geconfigureerd voor de site.  

     Zie voor meer informatie over het configureren van het netwerktoegangsaccount de [fundamentele concepten voor content management in System Center Configuration Manager](../../plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Distributie op basis van een software-installatie (alleen voor upgrades)  

    -   Als het Active Directory-schema niet is uitgebreid, of u installeert clients van een andere forest, moeten de installatie-eigenschappen voor CCMSetup.exe ingericht zijn in het register van de computer door gebruik te maken van groepsbeleid. Voor meer informatie, zie [Eigenschappen van clientinstallatie inrichten (groepsbeleid en clientinstallatie op basis van software-update)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision).  

    -   De clientcomputer moet in staat zijn om contact op te nemen met een distributie- of een beheerpunt om de ondersteunende bestanden te downloaden.  

     Zie voor de beveiligingsmachtigingen vereist om te upgraden van de Configuration Manager-client met behulp van Toepassingsbeheer, [beveiliging en privacy voor toepassingsbeheer](../../../apps/plan-design/security-and-privacy-for-application-management.md).  

-   Automatische clientupgrade  

     U moet lid zijn van de beveiligingsrol **Volledige beheerder** om de automatische clientupgrades te kunnen configureren.  

### <a name="firewall-requirements"></a>Firewallvereisten  
 Indien er een firewall is tussen de sitesysteemservers en de computers waarop u de Configuration Manager-client wenst te installeren, zie [Windows Firewall- en poortinstellingen voor clients in System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md).  

##  <a name="BKMK_prereqs_mobiledevices"></a>Vereisten voor Clients van mobiele apparaten  
 Gebruik de volgende informatie om te bepalen van de vereisten voor wanneer u de Configuration Manager-client op mobiele apparaten installeert en Configuration Manager gebruiken om ze te registreren.  

### <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  

-   Een Microsoftenterprise certificeringsinstantie (CA) met certificaatsjablonen om de vereiste certificaten voor mobiele apparaten te implementeren en te beheren.  

     De uitgevende CA moet automatisch certificaatverzoeken van de gebruikers van mobiele apparaten goedkeuren tijdens het registratieproces.  

     Zie [Beveiliging en privacy voor certificaatprofielen in System Center Configuration Manager](../../../protect/plan-design/security-and-privacy-for-certificate-profiles.md) voor meer informatie over de certificaatvereisten.  

-   Een beveiligingsgroep die gebruikers bevat die hun mobiele apparaten kunnen registreren.  

     Deze beveiligingsgroep wordt gebruikt om het certificaatsjabloon te configureren dat is gebruikt gedurende de registratie van het mobiele apparaat.  

-   Optioneel maar aangeraden: een DNS-alias (CNAME record) **ConfigMgrEnroll** genoemd, die geconfigureerd is voor de sitesysteemservernaam waarop u het registratie-proxy-punt gaat installeren.  

     De DNS-alias is vereist voor de ondersteuning van automatische detectie voor de registratieservice: Als u dit DNS-record niet configureert, moeten gebruikers handmatig de sitesysteemservernaam van het proxypunt voor inschrijving specificeren als onderdeel van het registratieproces.  

-   Sitesysteemrolafhankelijkheden voor de computers die het registratiepunt en de systeemrollen van de registratie-proxypunt-site zullen uitvoeren.  

     Zie [Ondersteunde besturingssystemen voor sitesysteemservers](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md).  

### <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  
 Voor meer informatie over de volgende sitesysteemrollen, zie de sectie [De sitesysteemrollen voor System Center Configuration Manager-clients bepalen](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md).  

-   Beheerpunt dat is geconfigureerd voor HTTPS client-verbindingen en ingeschakeld is voor mobiele apparaten  

     Een beheerpunt is altijd vereist voor het installeren van de Configuration Manager-client op mobiele apparaten. In aanvulling op de configuratie-eisen van HTTPS en ingeschakeld voor mobiele apparaten, moet het beheerpunt worden geconfigureerd met een Internet FQDN en clientverbindingen vanaf het Internet aanvaarden.  

-   Registratiepunt en proxypunt voor registratie  

     Een registratie-proxypunt beheert registratieverzoeken van mobiele apparaten en het registratiepunt vervolledigt het registratieproces. Het registratiepunt moet hetzelfde zijn in de Active Directory-forest als op de siteserver, maar het registratie-proxypunt kan zich in een andere forest bevinden.  

-   Clientinstellingen voor registratie van mobiel apparaat  

     Configureer clientinstellingen om gebruikers toe te laten om mobiele apparaten te registreren en minstens een registratieprofiel te configureren.  

-   Reporting Services-punt  

     Het Reporting Services-punt is een optionele, maar aanbevolen sitesysteemrol die rapporten kan weergeven gerelateerd aan registratie van mobiele apparaten en clientbeheer.  

     Zie [Rapportage in System Center Configuration Manager](../../../core/servers/manage/reporting.md) voor meer informatie.  

-   Om registratie te configureren voor mobiele apparaten, moet u de volgende beveiligingsmachtigingen hebben:  

    -   Als u wilt toevoegen, wijzigen en verwijderen van de sitesysteemrollen voor inschrijving: **Wijzig** machtiging voor het **Site** object.  

    -   Clientinstellingen voor inschrijving configureren: Standaardclientinstellingen vereisen **wijzigen** machtiging voor het **Site** object en aangepaste clientinstellingen vereisen **clientagent** machtigingen.  

     De **Volledige beheerder** beveiligingsrol bevat de vereiste machtigingen om de registratie-systeemrollen te configureren.  

     Om geregistreerde mobiele apparaten te beheren, moet u de volgende beveiligingsmachtigingen hebben:  

    -   Wissen of buiten gebruik stellen van een mobiel apparaat: **Bron verwijderen** voor de **verzameling** object.  

    -   Annuleren van een wissen of buiten gebruik stellen opdracht: **Bron verwijderen** voor de **verzameling** object.  

    -   Toestaan en blokkeren van mobiele apparaten: **Bron wijzigen** voor de **verzameling** object.  

    -   Op afstand, vergrendelen of opnieuw instellen van de wachtwoordcode op een mobiel apparaat: **Wijzig** resource voor de **verzameling** object.  

     De beveiligingsrol **Bewerkingenbeheerder** bevat de vereiste machtigingen om mobiele apparaten te beheren.  

     Zie voor meer informatie over het configureren van beveiligingsmachtigingen [De basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md) en [Beheer op basis van rollen configureren voor System Center Configuration Manager](../../../core/servers/deploy/configure/configure-role-based-administration.md).  

### <a name="firewall-requirements"></a>Firewallvereisten  
 Tussenkomende netwerkapparaten zoals routers en firewalls, en Windows Firewall indien van toepassing, moeten het verkeer toestaan dat gekoppeld is aan inschrijvingen van mobiele apparaten:  

-   Tussen mobiele apparaten en het proxypunt voor inschrijving: HTTPS (standaard: TCP 443)  

-   Tussen het registratieproxypunt en het registratiepunt: HTTPS (standaard: TCP 443)  

 Als u een proxywebserver gebruikt, moet deze geconfigureerd zijn voor SSL-tunneling; SSL-bridging wordt niet ondersteund voor mobiele apparaten.  
