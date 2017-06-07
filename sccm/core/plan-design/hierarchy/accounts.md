---
title: Accounts die worden gebruikt door Configuration Manager | Microsoft-documenten
description: Identificeren en beheren van de Windows-groepen en de accounts in System Center Configuration Manager.
ms.custom: na
ms.date: 2/9/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72d7b174-f015-498f-a0a7-2161b9929198
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 72263ec5e7104924a1ca46dc2000be9f8568599f
ms.openlocfilehash: a776667cc9f24bd4a468afea76e466c34ce66864
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="accounts-used-in-system-center-configuration-manager"></a>Accounts die worden gebruikt System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de volgende informatie om de Windows-groepen en de accounts die worden gebruikt in System Center Configuration Manager, hoe ze worden gebruikt en eventuele vereisten te identificeren.  

## <a name="windows-groups-that-configuration-manager-creates-and-uses"></a>Windows-groepen die worden gemaakt en gebruikt met Configuration Manager  
 Configuration Manager automatisch maakt en in veel gevallen automatisch onderhoudt, worden de volgende Windows-groepen.  

> [!NOTE]  
>  Als u een groep Configuration Manager maakt op een computer die lid is van een domein, is de groep een lokale beveiligingsgroep. Als de computer een domeincontroller is, is de groep een lokale domeingroep die wordt gedeeld onder alle domeincontrollers in het domein.  


### <a name="configmgrcollectedfilesaccess"></a>ConfigMgr_CollectedFilesAccess  
Deze groep Configuration Manager gebruikt voor het verlenen van toegang tot de bestanden die zijn verzameld door software-inventaris weergeven.  

De volgende tabel bevat aanvullende informatie voor deze groep:  

|Detail|Meer informatie|  
|------------|----------------------|  
|Type en locatie|Deze groep is een lokale beveiligingsgroep die op de primaire siteserver is gemaakt.<br /><br /> Wanneer u een site verwijdert, wordt deze groep niet automatisch verwijderd. Dit moet handmatig worden verwijderd.|  
|Lidmaatschap|Het groepslidmaatschap wordt automatisch beheerd door Configuration Manager. De leden zijn onder andere beheerders aan wie de machtiging **Verzamelde bestanden weergeven** is verleend op het beveiligbare object **Verzameling** van een toegewezen beveiligingsrol.|  
|Machtigingen|Deze groep heeft standaard **lezen** machtiging op de volgende map op de siteserver: **%path%\Microsoft configuratie Manager\sinv.box\FileCol**.|  

### <a name="configmgrdviewaccess"></a>ConfigMgr_DViewAccess  
 Deze groep is een lokale beveiligingsgroep die Configuration Manager op de Sitedatabaseserver of databasereplicaserver maakt. Het wordt momenteel niet gebruikt, maar is gereserveerd voor toekomstig gebruik.  

### <a name="configmgr-remote-control-users"></a>Gebruikers van extern beheer van ConfigMgr  
 Deze groep externe hulpprogramma's van Configuration Manager gebruiken voor het opslaan van de accounts en groepen die u hebt ingesteld in de lijst van toegestane Viewers die aan elke client is toegewezen.  

 De volgende tabel bevat aanvullende informatie voor deze groep:  

|Detail|Meer informatie|  
|------------|----------------------|  
|Type en locatie|Deze groep is een lokale beveiligingsgroep gemaakt op de Configuration Manager-client wanneer de client een beleid ontvangt dat externe hulpprogramma's inschakelt.<br /><br /> Nadat u externe hulpprogramma's voor een client uitgeschakeld, wordt deze groep niet automatisch verwijderd. Dit moet handmatig worden verwijderd van elke clientcomputer.|  
|Lidmaatschap|Standaard behoren er geen leden tot deze groep. Wanneer u gebruikers aan de lijst van toegestane viewers toevoegt, worden ze automatisch aan deze groep toegevoegd.<br /><br /> U kunt de lijst van toegestane viewers gebruiken om het lidmaatschap van deze groep te beheren in plaats van gebruikers of groepen rechtstreeks aan deze groep toe te voegen.<br /><br /> Niet enkel een toegestane viewer, een gebruiker met beheerdersrechten moet hebben de **beheer op afstand** machtiging voor het **verzameling** object. U kunt deze machtiging toewijzen door de beveiligingsrol Operator voor externe hulpprogramma's te gebruiken.|  
|Machtigingen|Standaard heeft deze groep geen machtigingen op enige locaties op de computer. Dit wordt alleen gebruikt om de lijst van toegestane Viewers houdt.|  

### <a name="sms-admins"></a>SMS Admins  
 Configuration Manager maakt gebruik van deze groep om toegang te verlenen tot de SMS-Provider door middel van Windows Management Instrumentation (WMI). Toegang tot de SMS-Provider is vereist om te bekijken en wijzigen van objecten in de Configuration Manager-console.  

> [!NOTE]  
>  De op rollen gebaseerde beheerconfiguratie van een gebruiker met beheerdersrechten bepaalt welke objecten ze kunnen weergeven en beheren wanneer u de Configuration Manager-console.  

 De volgende tabel bevat aanvullende informatie voor deze groep:  

|Detail|Meer informatie|  
|------------|----------------------|  
|Type en locatie|Deze groep is een lokale beveiligingsgroep gemaakt op elke computer die een SMS-Provider heeft.<br /><br /> Wanneer u een site verwijdert, wordt deze groep niet automatisch verwijderd. Dit moet handmatig worden verwijderd.|  
|Lidmaatschap|Het groepslidmaatschap wordt automatisch beheerd door Configuration Manager. Elke beheerder in een hiërarchie en de account van de siteservercomputer is standaard lid van de SMS Admins-groep op elke computer van de SMS Provider in een site.|  
|Machtigingen|SMS Admins-rechten en machtigingen worden ingesteld in de WMI Control MMC-module. Standaard wordt de groep SMS Admins krijgt **Account inschakelen** en **afstand inschakelen** op de root/SMS-naamruimte. Geverifieerde gebruikers hebben **methoden uitvoeren**, **providerobjecten**, en **Account inschakelen**.<br /><br /> Gebruikers met beheerdersrechten die een externe Configuration Manager-console gebruikt nodig Remote Activation DCOM-machtigingen op de site server-computer en de SMS-providercomputer. Het wordt aanbevolen deze rechten toe te kennen aan de SMS Admins om het beheer te vereenvoudigen in plaats van deze rechten rechtstreeks aan gebruikers of groepen toe te kennen. Zie voor meer informatie de sectie [DCOM-machtigingen configureren voor externe Configuration Manager-consoles](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) in het onderwerp [Uw infrastructuur van System Center Configuration Manager aanpassen](../../../core/servers/manage/modify-your-infrastructure.md).|  

### <a name="smssitesystemtositeserverconnectionmpltsitecode"></a>SMS_SiteSystemToSiteServerConnection_MP_&lt;sitecode\>  
 Deze groep Configuration Manager-beheerpunten die extern van de siteserver zijn gebruiken voor verbinding met de sitedatabase. Deze groep biedt een beheerpunt toegang tot het Postvak IN op de siteserver en de sitedatabase.  

 De volgende tabel bevat aanvullende informatie voor deze groep:  

|Detail|Meer informatie|  
|------------|----------------------|  
|Type en locatie|Deze groep is een lokale beveiligingsgroep gemaakt op elke computer die een SMS-Provider heeft.<br /><br /> Wanneer u een site verwijdert, wordt deze groep niet automatisch verwijderd. Dit moet handmatig worden verwijderd.|  
|Lidmaatschap|Het groepslidmaatschap wordt automatisch beheerd door Configuration Manager. Lidmaatschap omvat standaard de computeraccounts van externe computers die een beheerpunt voor de site hebben.|  
|Machtigingen|Deze groep heeft standaard **lezen**, **lezen & uitvoeren**, en **Mapinhoud weergeven** machtiging voor het **%path%\Microsoft configuratie Manager\inboxes** map op de siteserver. Deze groep de extra machtiging heeft **schrijven** op submappen onder de **postvakken** waarnaar het beheerpunt clientgegevens schrijft.|  

### <a name="smssitesystemtositeserverconnectionsmsprovltsitecode"></a>SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;sitecode\>  
 Deze groep SMS-Provider voor Configuration Manager-computers die extern van de siteserver zijn gebruiken voor verbinding met de siteserver.  

 De volgende tabel bevat aanvullende informatie voor deze groep:  

|Detail|Meer informatie|  
|------------|----------------------|  
|Type en locatie|Deze groep is een lokale beveiligingsgroep die op de siteserver is gemaakt.<br /><br /> Wanneer u een site verwijdert, wordt deze groep niet automatisch verwijderd. Dit moet handmatig worden verwijderd.|  
|Lidmaatschap|Het groepslidmaatschap wordt automatisch beheerd door Configuration Manager. Lidmaatschap omvat standaard de computeraccount of de domeingebruikersaccount die wordt gebruikt voor verbinding met de siteserver van elke externe computer die een SMS-Provider voor de site heeft geïnstalleerd.|  
|Machtigingen|Deze groep heeft standaard **lezen**, **lezen & uitvoeren**, en **Mapinhoud weergeven** machtiging voor het **%path%\Microsoft configuratie Manager\inboxes** map op de siteserver. Deze groep de extra machtiging heeft **schrijven** of de machtigingen van **schrijven** en **wijzigen** op submappen onder de **postvakken** waartoe de SMS-Provider toegang nodig.<br /><br /> Deze groep heeft ook **lezen**, **lezen & uitvoeren**, **Mapinhoud weergeven**, **schrijven**, en **wijzigen** machtigingen op de mappen onder **%path%\Microsoft configuratie Manager\OSD\boot** en **lezen** machtiging op de mappen onder **%path%\Microsoft configuratie Manager\OSD\Bin** op de siteserver.|  

### <a name="smssitesystemtositeserverconnectionstatltsitecode"></a>SMS_SiteSystemToSiteServerConnection_Stat_&lt;sitecode\>  
 De File Dispatch Manager op externe sitesysteemcomputers Configuration Manager maakt gebruik van deze groep verbinding maken met de siteserver.  

 De volgende tabel bevat aanvullende informatie voor deze groep:  

|Detail|Meer informatie|  
|------------|----------------------|  
|Type en locatie|Deze groep is een lokale beveiligingsgroep die op de siteserver is gemaakt.<br /><br /> Wanneer u een site verwijdert, wordt deze groep niet automatisch verwijderd. Dit moet handmatig worden verwijderd.|  
|Lidmaatschap|Het groepslidmaatschap wordt automatisch beheerd door Configuration Manager. Lidmaatschap omvat standaard de computeraccount of de domeingebruikersaccount die wordt gebruikt om een verbinding te maken met de siteserver van elke externe sitesysteemcomputer die de File Dispatch Manager uitvoert.|  
|Machtigingen|Deze groep heeft standaard **lezen**, **lezen & uitvoeren**, en **Mapinhoud weergeven** machtiging voor het **%path%\Microsoft configuratie Manager\inboxes** map en submappen onder die locatie op de siteserver. Deze groep de extra machtigingen heeft **schrijven** en **wijzigen** naar de **%path%\Microsoft configuratie Manager\inboxes\statmgr.box** map op de siteserver.|  

### <a name="smssitetositeconnectionltsitecode"></a>SMS_SiteToSiteConnection_&lt;sitecode\>  
 Deze groep wordt gebruikt om in te schakelen bestandsgebaseerde replicatie tussen sites in een hiërarchie Configuration Manager. Voor elke externe site die rechtstreeks bestanden naar deze site overbrengt, heeft deze groep de accounts die zijn ingesteld als een **Account voor bestandsreplicatie**.  

 De volgende tabel bevat aanvullende informatie voor deze groep:  

|Detail|Meer informatie|  
|------------|----------------------|  
|Type en locatie|Deze groep is een lokale beveiligingsgroep die op de siteserver is gemaakt.|  
|Lidmaatschap|Wanneer u een nieuwe site als onderliggende site van een andere site installeert, Configuration Manager het computeraccount van de nieuwe site automatisch toegevoegd aan de groep op de bovenliggende siteserver. De computeraccount van de bovenliggende site Configuration Manager ook toegevoegd aan de groep op de nieuwe siteserver. Als u een ander account voor overdrachten op basis van een bestand opgeeft, moet u dat account toevoegen aan deze groep op de siteserver van bestemming.<br /><br /> Wanneer u een site verwijdert, wordt deze groep niet automatisch verwijderd. Dit moet handmatig worden verwijderd.|  
|Machtigingen|Deze groep heeft standaard **volledig beheer** naar de **%path%\Microsoft configuratie Manager\inboxes\despoolr.box\receive** map.|  

## <a name="accounts-that-configuration-manager-uses"></a>Accounts die worden gebruikt met Configuration Manager  
 U kunt u de volgende accounts instellen voor Configuration Manager.  

### <a name="active-directory-group-discovery-account"></a>Detectieaccount Active Directory-groepen  
 De **Detectieaccount Active Directory-groepen** wordt gebruikt voor het detecteren van lokale, globale en universele beveiligingsgroepen, het lidmaatschap binnen deze groepen en het lidmaatschap binnen distributiegroepen van de opgegeven locaties in Active Directory Domain Services. Distributiegroepen worden niet als groepsbronnen gedetecteerd.  

 Dit account kan een computeraccount van de siteserver zijn dat detectie uitvoert of een Windows-gebruikersaccount. Het moet beschikken over een toegangsmachtiging van het type **Lezen** voor de Active Directory-locaties die voor detectie zijn opgegeven.  

### <a name="active-directory-system-discovery-account"></a>Detectieaccount Active Directory-systeem  
 Het **detectieaccount Active Directory-systeem** wordt gebruikt voor het detecteren van computers van de opgegeven locaties in Active Directory Domain Services.  

 Dit account kan een computeraccount van de siteserver zijn dat detectie uitvoert of een Windows-gebruikersaccount. Het moet beschikken over een toegangsmachtiging van het type **Lezen** voor de Active Directory-locaties die voor detectie zijn opgegeven.  

### <a name="active-directory-user-discovery-account"></a>Detectieaccount Active Directory-gebruikers  
 Het **detectieaccount Active Directory-gebruikers** wordt gebruikt voor het detecteren van gebruikersaccounts van de opgegeven locaties in Active Directory Domain Services.  

 Dit account kan een computeraccount van de siteserver zijn dat detectie uitvoert of een Windows-gebruikersaccount. Het moet beschikken over een toegangsmachtiging van het type **Lezen** voor de Active Directory-locaties die voor detectie zijn opgegeven.  

### <a name="active-directory-forest-account"></a>Active Directory-forestaccount  
 De **Active Directory-Forestaccount** wordt gebruikt voor het detecteren van netwerkinfrastructuur van Active Directory-forests. Centrale beheersites en primaire sites ook gebruiken om sitegegevens te publiceren naar Active Directory Domain Services voor een forest.  

> [!NOTE]  
>  Secundaire sites gebruiken steeds het computeraccount van de secundaire siteserver om naar Active Directory te publiceren.  

> [!NOTE]  
>  De Active Directory-Forestaccount moet een algemene account te detecteren en te publiceren naar niet-vertrouwde forests. Als u het computeraccount van de siteserver niet gebruikt, kunt u alleen een globaal account selecteren.  

 Dit account moet **Lezen**-machtigingen hebben voor elk Active Directory-forest waar u de netwerkinfrastructuur wilt detecteren.  

 Dit account moet **Volledige bevoegdheid**-machtigingen hebben op de System Management-container en op alle onderliggende objecten daarvan in elk Active Directory-forest waar u sitegegevens wilt publiceren.  

### <a name="asset-intelligence-synchronization-point-proxy-server-account"></a>Proxyserveraccount van Asset Intelligence-synchronisatiepunt  
 De Asset Intelligence-synchronizatiepunt gebruikt de **Asset Intelligence synchronisatie Proxyserveraccount** geverifieerde toegang tot het Internet via een proxy of firewall die is vereist.  

> [!IMPORTANT]  
>  Geef een account op dat over de geringst mogelijke machtigingen voor de vereiste proxyserver of firewall beschikt.  

### <a name="certificate-registration-point-account"></a>Account voor het certificaatregistratiepunt  
 De **Account Certificaatregistratiepunt** verbindt het certificaatregistratiepunt met de Configuration Manager-database. Het computeraccount van de certificaatregistratiepuntserver wordt standaard gebruikt, maar u kunt een gebruikersaccount in plaats daarvan instellen. U moet een gebruikersaccount opgeven wanneer het certificaatregistratiepunt zich in een niet-vertrouwd domein van de siteserver bevindt. Deze account vereist alleen **lezen** toegang tot de sitedatabase, omdat het statusberichtsysteem schrijven taken verwerkt.  

### <a name="capture-operating-system-image-account"></a>Account voor het vastleggen van een besturingssysteeminstallatiekopie  
 Configuration Manager gebruikt de **vastleggen Account van een Besturingssysteeminstallatiekopie** voor toegang tot de map wanneer vastgelegde installatiekopieën worden opgeslagen wanneer u besturingssystemen implementeert. Dit account is vereist als u de stap **Besturingssysteeminstallatiekopie vastleggen** toevoegt aan een takenreeks.  

 Het account moet de machtigingen **Lezen** en **Schrijven** hebben op de netwerkshare waar de vastgelegde installatiekopie is opgeslagen.  

 Als het wachtwoord voor het account wordt gewijzigd in Windows, moet u de takenreeks met het nieuwe wachtwoord bijwerken. De Configuration Manager-client wordt het nieuwe wachtwoord ontvangen wanneer het clientbeleid op de volgende keer downloadt.  

 Als u dit account gebruikt, kunt u één domeingebruikersaccount maken met minimale machtigingen voor toegang tot de vereiste netwerkbronnen en dit gebruiken voor alle takenreeksaccounts.  

> [!IMPORTANT]  
>  Geen interactieve machtigingen voor aanmelden toewijst aan dit account.  
>   
>  Gebruik voor dit account geen netwerktoegangsaccount.  

### <a name="client-push-installation-account"></a>Account voor push-installatie client  
 De **Clientpushinstallatieaccount** wordt gebruikt voor verbinding maken met computers en de Configuration Manager-clientsoftware installeren als u clients implementeert met behulp van push-clientinstallatie. Als dit account niet is opgegeven, wordt het siteserveraccount gebruikt om te proberen de clientsoftware te installeren.  

 Dit account moet lid zijn van de lokale **beheerders** groep op de computers waarop de Configuration Manager-clientsoftware wordt geïnstalleerd. Deze account vereist geen **Domain Admin** rechten.  

 U kunt een of meer Clientpushinstallatieaccounts, die Configuration Manager elk om beurt probeert tot er één lukt opgeven.  

> [!TIP]  
>  Om accountupdates in grote Active Directory-implementaties efficiënter te coördineren, maakt een nieuwe account met een andere naam en vervolgens het nieuwe account toevoegt aan de lijst met Clientpushinstallatieaccounts in Configuration Manager. Geef voldoende tijd voor Active Directory Domain Services om de nieuwe account te repliceren en verwijder de oude account vervolgens uit Configuration Manager en Active Directory Domain Services.  

> [!IMPORTANT]  
>  Verleen deze account geen het recht Lokaal aanmelden.  

### <a name="enrollment-point-connection-account"></a>Verbindingsaccount voor inschrijvingspunt  
 De **Verbindingsaccount inschrijving** verbindt het inschrijvingspunt met de sitedatabase van Configuration Manager. Het computeraccount van het inschrijvingspunt wordt standaard gebruikt, maar u kunt een gebruikersaccount in plaats daarvan instellen. U moet een gebruikersaccount opgeven wanneer het inschrijvingspunt zich in een niet-vertrouwd domein van de siteserver bevindt. Deze account vereist **lezen** en **schrijven** toegang tot de sitedatabase.  

### <a name="exchange-server-connection-account"></a>Exchange Server-verbindingsaccount  
 Het **Exchange Server-verbindingsaccount** verbindt de siteserver met de opgegeven Exchange Server-computer om mobiele apparaten te zoeken en te beheren die een verbinding maken met Exchange Server. Dit account vereist Exchange PowerShell-cmdlets die de vereiste machtigingen op de Exchange Server-computer bieden. Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor meer informatie over de cmdlets.  

### <a name="exchange-server-connector-proxy-server-account"></a>Proxyserveraccount Exchange Server-connector  
 De Exchange Server-connector gebruikt het **Proxyserveraccount voor Exchange Server-Connector** geverifieerde toegang tot het Internet via een proxy of firewall die is vereist.  

> [!IMPORTANT]  
>  Geef een account op dat over de geringst mogelijke machtigingen voor de vereiste proxyserver of firewall beschikt.  

### <a name="management-point-connection-account"></a>Verbindingsaccount beheerpunt  
 De **Account voor Beheerpuntverbinding** wordt gebruikt voor het beheerpunt verbinding met de Configuration Manager-sitedatabase zodat het kan verzenden en opvragen van informatie voor clients. Het computeraccount van het beheerpunt wordt standaard gebruikt, maar u kunt een gebruikersaccount in plaats daarvan instellen. U moet een gebruikersaccount opgeven wanneer het beheerpunt zich in een niet-vertrouwd domein van de siteserver bevindt.  

 Maak de account aan als een laag niveau aan rechten lokaal account op de computer waarop Microsoft SQL Server uitvoert.  

> [!IMPORTANT]  
>  Ken geen interactieve aanmeldingen toe aan dit account.  

### <a name="multicast-connection-account"></a>Multicastverbindingsaccount  
 Distributiepunten die zijn ingesteld voor multicast-gebruik de **Multicastverbindingsaccount** om informatie te lezen uit de sitedatabase. Het computeraccount van het distributiepunt wordt standaard gebruikt, maar u kunt een gebruikersaccount in plaats daarvan instellen. U moet een gebruikersaccount opgeven wanneer de sitedatabase zich in een niet-vertrouwd forest bevindt. Als uw datacentrum bijvoorbeeld een perimeternetwerk heeft in een ander forest dan de siteserver en sitedatabase, kunt u dit account gebruiken om de multicastinformatie uit de sitedatabase te lezen.  

 Als u deze account maakt, kunt u deze als een lokale account op de computer waarop Microsoft SQL Server wordt uitgevoerd met weinig rechten maken.  

> [!IMPORTANT]  
>  Ken geen interactieve aanmeldingen toe aan dit account.  

### <a name="network-access-account"></a>Netwerktoegangsaccount  
 Client-computers gebruiken de **netwerktoegangsaccount** wanneer ze hun lokale computeraccount niet kunnen gebruiken voor toegang tot inhoud op distributiepunten. Dit is bijvoorbeeld van toepassing op werkgroepclients en computers uit niet-vertrouwde domeinen. Dit account kan ook worden gebruikt tijdens de implementatie van besturingssystemen wanneer de computer die het besturingssysteem installeert nog niet over een computeraccount voor het domein.  

> [!NOTE]  
>  Het netwerktoegangsaccount wordt nooit gebruikt als de beveiligingscontext uitvoeren van programma's, software-updates installeren of uitvoeren van takenreeksen. Het wordt enkel gebruikt voor toegang tot bronnen op het netwerk.  

 Verleen aan dit account de minimum geschikte machtigingen op de inhoud die de client nodig heeft voor toegang tot de software. Het account moet het recht **Deze computer via het netwerk benaderen** hebben op het distributiepunt of andere server waar de pakketinhoud staat. U kunt maximaal 10 netwerktoegangsaccounts per site configureren.  

> [!WARNING]  
>  Wanneer er wordt geprobeerd met Configuration Manager het computernaam$-account te gebruiken om de inhoud te downloaden en dit mislukt, wordt het automatisch opnieuw geprobeerd met het netwerktoegangsaccount, zelfs als dit al eerder is mislukt.  

 Maak het account in elk domein dat de noodzakelijke toegang tot bronnen zal bieden. Het netwerktoegangsaccount moet altijd een domeinnaam omvatten. Pass Through-beveiliging wordt niet ondersteund voor dit account. Als u over distributiepunten in meerdere domeinen beschikt, maakt u het account in een vertrouwd domein.  

> [!TIP]  
>  Wijzig het wachtwoord van een bestaand netwerktoegangsaccount niet om vergrendeling te voorkomen. In plaats daarvan een nieuw account maken en het nieuwe account in Configuration Manager instellen. Wanneer er voldoende tijd is verstreken waarbinnen alle clients de nieuwe accountgegevens hebben ontvangen, verwijdert u het account uit de gedeelde netwerkmappen en verwijdert u het account.  

> [!IMPORTANT]  
>  Ken geen interactieve aanmeldingen toe aan dit account.
>   
>  Aan dit account mag niet de machtiging worden toegekend om computers lid te maken van het domein. Gebruik het domeinlidmaatschapsaccount van de takenreekseditor als u tijdens een takenreeks computers lid moet maken van een domein.  

### <a name="package-access-account"></a>Pakkettoegangsaccount  
 Een **Pakkettoegangsaccount** kunt u opgeven welke gebruikers en gebruikersgroepen die toegang heeft tot een pakketmap op distributiepunten NTFS-machtigingen. Standaard Configuration Manager alleen toegang verleend aan de algemene toegangsaccounts **gebruikers** en **beheerders**. U kunt de toegang voor clientcomputers beheren via aanvullende Windows-accounts of groepen. Mobiele apparaten halen pakketinhoud steeds anoniem op; zodat ze de Accounts voor pakkettoegang niet gebruiken.  

 Standaard, wanneer de Configuration Manager het pakketshare maakt op een distributiepunt, kent het **lezen** toegang tot de lokale **gebruikers** groep en **volledig beheer** aan de lokale **beheerders** groep. De werkelijke noodzakelijke machtigingen zijn afhankelijk van het pakket. Als er sprake is van clients in werkgroepen of in niet-vertrouwde forests, kunnen deze clients het netwerktoegangsaccount gebruiken voor toegang tot de pakketinhoud. Zorg ervoor dat het netwerktoegangsaccount machtigingen heeft op het pakket door gebruik te maken van de gedefinieerde pakkettoegangsaccounts.  

 Gebruik accounts in een domein dat toegang heeft tot de distributiepunten. Als u maakt of het account wijzigen nadat het pakket is gemaakt, moet u het pakket opnieuw distribueren. Het bijwerken van het pakket verandert de NTFS-machtigingen op het pakket niet.  

 U hoeft het netwerktoegangsaccount niet toe te voegen als een pakkettoegangsaccount omdat dit al automatisch is toegevoegd via het lidmaatschap van de groep Gebruikers. Als u het pakkettoegangsaccount uitsluitend tot het netwerktoegangsaccount beperkt, blijven clients toegang houden tot het pakket.  

### <a name="reporting-services-point-account"></a>Account van Reporting Services-punt  
 SQL Server Reporting Services gebruikt de **Account voor Reporting Services-punt** voor het ophalen van de gegevens voor Configuration Manager-rapporten uit de sitedatabase. Het Windows-gebruikersaccount en wachtwoord die u opgeeft, worden versleuteld en opgeslagen in de SQL Server Reporting Services-database.  

### <a name="remote-tools-permitted-viewer-accounts"></a>Accounts van toegestane van externe hulpprogramma's  
 De accounts die u opgeeft als **toegestane viewers** voor extern beheer zijn een lijst van gebruikers die zijn gemachtigd externe hulpprogramma's te gebruiken op clients.  

### <a name="site-system-installation-account"></a>Installatieaccount voor sitesystemen  
 De siteserver gebruikt de **Installatieaccount** om te installeren, opnieuw moet installeren, te verwijderen en instellen van site-systemen. Als u het sitesysteem op de siteserver moet verbinding met dit sitesysteem initiëren, Configuration Manager ook gebruikt deze account voor pull-gegevens uit de sitesysteemcomputer nadat het sitesysteem en enige sitesysteemrollen zijn geïnstalleerd. Elk sitesysteem kan een verschillende Installatieaccount sitesysteem hebben, maar u kunt slechts één Installatieaccount instellen voor het beheren van alle sitesysteemrollen op dat sitesysteem.  

 Deze account vereist lokale beheerdersmachtigingen op de sitesystemen die beheerders zullen installeren en instellen. Dit account moet bovendien hebben **toegang tot deze computer via het netwerk** in het beveiligingsbeleid op de sitesystemen die beheerders zullen installeren en instellen.  

> [!TIP]  
>  Als u veel domeincontrollers hebt en deze accounts binnen domeinen zullen worden gebruikt, controleert u of de accounts zijn gerepliceerd voordat u het sitesysteem instelt.  
>   
>  Wanneer u een lokaal account opgeeft op elk sitesysteem dat moet worden beheerd, is deze configuratie veiliger dan het gebruik van domeinaccounts, omdat het de schade beperkt die aanvallers kunnen aanbrengen als er met het account wordt geknoeid. Domeinaccounts zijn echter gemakkelijker te beheren. Een evenwicht tussen beveiliging en doeltreffend beheer.  

### <a name="smtp-server-connection-account"></a>SMTP-serververbindingsaccount  
 De siteserver gebruikt de **SMTP-Serververbindingsaccount** om e-mailwaarschuwingen te sturen die geverifieerde toegang wanneer de SMTP-server vereist.  

> [!IMPORTANT]  
>  Geef een account die de geringst mogelijke machtigingen heeft om e-mails te verzenden.  

### <a name="software-update-point-connection-account"></a>Verbindingsaccount software-updatepunt  
 De siteserver gebruikt de **bijwerken Verbindingsaccount Software** voor de volgende twee software updateservices:  

-   Windows Server Update Services (WSUS) Configuration Manager, dat instellingen zoals productdefinities, classificaties en upstream-instellingen heeft ingesteld.  

-   WSUS Synchronization Manager, dat synchronisatie vraagt met een upstream WSUS-server of Microsoft Update.  

De Installatieaccount kunt onderdelen voor software-updates installeren, maar kan deze software-update-specifieke functies uitvoeren op het software-updatepunt. Als u het siteservercomputeraccount voor deze functie niet kunt gebruiken omdat het software-updatepunt zich in een niet-vertrouwd forest bevindt, moet u dit account opgeven naast het installatieaccount voor sitesystemen.  

Dit account moet een lokale beheerder op de computer waarop WSUS is geïnstalleerd. Het moet ook zijn onderdeel van de lokale groep WSUS-Administrators.  

### <a name="software-update-point-proxy-server-account"></a>Proxyserveraccount software-updatepunt  
 Het software-updatepunt gebruikt de **Software Update Proxyserveraccount** geverifieerde toegang tot het Internet via een proxy of firewall die is vereist.  

> [!IMPORTANT]  
>  Geef een account op dat over de geringst mogelijke machtigingen voor de vereiste proxyserver of firewall beschikt.  

### <a name="source-site-account"></a>Bronsiteaccount  
 Het migratieproces gebruikt de **Bronsiteaccount** voor toegang tot de SMS-Provider van de bronsite. Dit account vereist **Lezen**-machtigingen op siteobjecten in de bronsite om gegevens voor migratiejobs te verzamelen.  

 Als u Configuration Manager 2007-distributiepunten of secundaire sites die op dezelfde locatie hebben distributiepunten naar System Center Configuration Manager-distributiepunten bijwerkt, wordt dit account moet ook hebben **verwijderen** machtigingen voor de **Site** klasse voor het distributiepunt van de Configuration Manager 2007-site verwijderen tijdens de upgrade.  

> [!NOTE]  
>  Zowel het Bronsiteaccount als het Bronsitedatabaseaccount zijn geïdentificeerd als **Migratiebeheer** in de **Accounts** knooppunt van de **beheer** werkruimte in de Configuration Manager-console.  

### <a name="source-site-database-account"></a>Bronsitedatabaseaccount  
 Het migratieproces gebruikt de **Bronsitedatabaseaccount** voor toegang tot de SQL Server-database voor de bronsite. Om gegevens te verzamelen van de SQL Server-database van de bronsite, het Bronsitedatabaseaccount moet hebben de **lezen** en **Execute** machtigingen voor SQL Server-database van de bronsite.  

> [!NOTE]  
>  Als u het computeraccount van de System Center Configuration Manager gebruikt, zorg ervoor dat de volgende items voor dit account waar zijn:  
>   
> -   Het is lid van de beveiligingsgroep **DCOM-gebruikers** in het domein waar de Configuration Manager 2007-site zich bevindt.  
> -   Het is lid van de beveiligingsgroep **SMS Admins**.  
> -   Dit is de **lezen** machtiging op alle Configuration Manager 2007-objecten.  

> [!NOTE]  
>  Zowel het Bronsiteaccount als Bronsitedatabaseaccount worden aangeduid als **Migratiebeheer** in de **Accounts** knooppunt van de **beheer** werkruimte in de Configuration Manager-console.  

### <a name="task-sequence-editor-domain-joining-account"></a>Takenreekseditoraccount voor domeinlidmaatschap  
 Het **takenreekseditoraccount voor domeinlidmaatschap** wordt gebruikt in een takenreeks om een zojuist gerepliceerde computer lid te maken van een domein. Dit account is nodig als u de stap **Lid maken van domein of werkgroep** aan een takenreeks toevoegt en daarna **Lid maken van domein** selecteert. Dit account kan ook worden ingesteld als u de stap toevoegt **netwerkinstellingen toepassen** aan een taak, maar dit is niet vereist.  

 Voor dit account is het recht **Lid worden van domein** vereist in het domein waarvan de computer lid wordt.  

> [!TIP]  
>  Als u dit account nodig hebt voor uw takenreeksen, kunt u één domeingebruikersaccount maken met minimale machtigingen voor toegang tot de benodigde netwerkbronnen en ervan gebruik maken voor alle takenreeksaccounts.  

> [!IMPORTANT]  
>  Geen interactieve machtigingen voor aanmelden toewijst aan dit account.  
>   
>  Gebruik voor dit account geen netwerktoegangsaccount.  

### <a name="task-sequence-editor-network-folder-connection-account"></a>Takenreekseditoraccount voor netwerkmapverbinding  
 Een takenreeks maakt gebruik van de **Takenreeks Editor netwerk map Verbindingsaccount** verbinding maken met een gedeelde map op het netwerk. Dit account is vereist als u de stap **Verbinding maken met netwerkmap** toevoegt aan een takenreeks.  

 Deze account vereist machtigingen voor toegang tot de opgegeven gedeelde map. Het moet een gebruikersdomeinaccount zijn.  

> [!TIP]  
>  Als u dit account nodig hebt voor uw takenreeksen, kunt u één domeingebruikersaccount maken met minimale machtigingen voor toegang tot de benodigde netwerkbronnen en ervan gebruik maken voor alle takenreeksaccounts.  

> [!IMPORTANT]  
>  Geen interactieve machtigingen voor aanmelden toewijst aan dit account.  
>   
>  Gebruik voor dit account geen netwerktoegangsaccount.  

### <a name="task-sequence-run-as-account"></a>Uitvoeren als-account voor takenreeks  
 Het **uitvoeren als-account voor takenreeksen** wordt gebruikt om opdrachtregels in takenreeksen uit te voeren en andere referenties te gebruiken dan het lokale systeemaccount. Dit account is vereist als u de stap toevoegt **opdrachtregel uitvoeren** aan een takenreeks, maar niet wilt dat de takenreeks uitgevoerd met machtigingen van het lokale systeemaccount op de beheerde computer.  

 De account instellen voor de minimale machtigingen nodig voor het uitvoeren van de opdrachtregel die opgegeven in de takenreeks. Het account vereist interactieve rechten voor aanmelden en normaal gesproken de mogelijkheid software kunnen installeren en toegang tot netwerkbronnen.  

> [!IMPORTANT]  
>  Gebruik voor dit account geen netwerktoegangsaccount.  
>   
>  Maak nooit de account de beheerder van een domein.  
>   
>  Nooit zwervende profielen voor dit account instellen. Wanneer de takenreeks wordt uitgevoerd, zal deze het zwervend profiel voor het account downloaden. Dit betekent dat het profiel kwetsbaar voor toegang op de lokale computer.  
>   
>  Beperk het bereik van het account. Maak voor elke taakreeks bijvoorbeeld verschillende uitvoeren-als accounts voor takenreeksen, zodat, wanneer één account gevaar loopt, alleen de clientcomputers waartoe het account toegang heeft gevaar lopen.  
>   
>  Als de opdrachtregel beheerderstoegang op de computer vereist, kunt u een lokale Administrator-account maken uitsluitend voor de Takenreeks Run As-Account op alle computers die de takenreeks wordt uitgevoerd. De account verwijderen als u niet langer.  
