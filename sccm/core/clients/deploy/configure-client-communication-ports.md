---
title: Configureren van client-communicatiepoorten | Microsoft-documenten
description: Client-communicatiepoorten in System Center Configuration Manager ingesteld.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 406bbdbf-ab4a-4121-a68b-154f96ea14ec
caps.latest.revision: 5
caps.handback.revision: 0
author: robstack
ms.author: robstackmsft
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 63e033fdb436930ac5f37e7408ca9292bc444560
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-client-communication-ports-in-system-center-configuration-manager"></a>Het configureren van client-communicatiepoorten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de aangevraagde poortnummers die door System Center Configuration Manager-clients gebruiken om te communiceren met sitesystemen die HTTP en HTTPS voor communicatie gebruiken. Hoewel HTTP of HTTPS waarschijnlijk al is geconfigureerd voor firewalls, clientmeldingen die gebruikmaakt van HTTP of HTTPS meer CPU-gebruik en -geheugen op de beheerpuntcomputer dan als u een aangepast poortnummer gebruikt. U kunt ook het sitepoortnummer wilt gebruiken als u van clients ontwaken met behulp van traditionele ontwaakpakketten opgeven.  

 Wanneer u aangevraagde poorten voor HTTP en HTTPS opgeeft, kunt u zowel een standaardpoortnummer als een alternatief poortnummer opgeven. Clients proberen automatisch de alternatieve poort nadat de communicatie mislukt met de standaardpoort. U kunt instellingen opgeven voor communicatie van HTTP en HTTPS-gegevens.  

 De standaardwaarden voor de client aangevraagde poortnummers zijn **80** voor HTTP-verkeer en **443** voor HTTPS-verkeer. Wijzig deze nummers alleen als u niet wilt gebruiken deze standaardwaarden. Een typisch scenario voor het gebruik van aangepaste poorten is wanneer u een aangepaste website in IIS in plaats van de standaardwebsite. Als u de standaardpoortnummers voor de standaardwebsite in IIS en andere toepassingen ook de standaardwebsite gebruiken, zijn deze waarschijnlijk zal mislukken.  

> [!IMPORTANT]  
>  Wijzig de poortnummers in Configuration Manager niet zonder informatie over de gevolgen. Voorbeelden:  
>   
>  -   Als u de poortnummers voor de client aangevraagde services als een siteconfiguratie wijzigt en bestaande clients worden niet opnieuw geconfigureerd voor het gebruik van de nieuwe poortnummers, worden deze clients niet onbeheerd.  
> -   Voordat u een niet-standaardpoortnummer configureert, zorg ervoor dat firewalls en alle gekoppelde netwerkapparaten deze configuratie ondersteunt en configureer ze opnieuw naar behoefte. Als u clients op het Internet te beheren en de standaard HTTPS-poortnummer 443 wijzigt, blokkeren routers en firewalls op het Internet mogelijk deze communicatie.  

 Om ervoor te zorgen dat clients niet onbeheerd worden na wijziging van de aangevraagde poortnummers, moeten clients worden geconfigureerd voor gebruik van de nieuwe aangevraagde poortnummers. Wanneer u de aangevraagde poorten op een primaire site wijzigt, nemen alle gekoppelde secundaire sites automatisch dezelfde poortconfiguratie over. Gebruik de procedure in dit onderwerp voor het configureren van de aangevraagde poorten op de primaire site.  

> [!NOTE]  
>  Zie voor meer informatie over het configureren van de aanvraagpoorten voor clients op computers met Linux en UNIX [aangevraagde poorten voor de Client voor Linux en UNIX configureren](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigLnUClientCommuincations).  

 Wanneer de Configuration Manager-site is gepubliceerd naar Active Directory Domain Services, nieuwe en bestaande clients die toegang deze informatie tot wordt automatisch geconfigureerd met hun sitepoortinstellingen en hoeft u geen verdere actie te ondernemen. Clients die deze informatie die is gepubliceerd naar Active Directory Domain Services niet kunnen openen zijn onder andere werkgroepclients, clients met een andere Active Directory-forest, clients die zijn geconfigureerd voor Internet-only en clients die zich momenteel op het Internet. Als u de standaardpoortnummers wijzigt nadat deze clients zijn geïnstalleerd, installeert u deze opnieuw en installeert u alle nieuwe clients via een van de volgende methoden:  

-   De clients opnieuw installeren met behulp van de Wizard Push-clientinstallatie. Clientpushinstallatie configureert automatisch clients met de huidige sitepoortconfiguratie. Zie voor meer informatie over het gebruik van de Wizard Push-clientinstallatie [Configuration Manager-clients installeren met behulp van Clientpush](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

-   De clients opnieuw installeren met behulp van CCMSetup.exe en de client.msi installatie-eigenschappen CCMHTTPPORT en CCMHTTPSPORT. Zie voor meer informatie over deze eigenschappen [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

-   De clients opnieuw installeren met behulp van een methode die zoekt naar Active Directory Domain Services naar installatie-eigenschappen van Configuration Manager-client. Zie [About client installation properties published to Active Directory Domain Services in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md) (Informatie over eigenschappen van clientinstallaties die zijn gepubliceerd naar Active Directory Domain Services in System Center Configuration Manager) voor meer informatie.  

 Als u wilt de poortnummers voor bestaande clients opnieuw hebt geconfigureerd, kunt u ook het script PORTSWITCH gebruiken. VBS die is opgegeven op de installatiemedia in de map SMSSETUP\Tools\PortConfiguration.  

> [!IMPORTANT]  
>  Voor bestaande en nieuwe clients die zich momenteel op het Internet, moet u de niet-standaard poortnummers te configureren met behulp van de CCMSetup.exe client.msi-eigenschappen CCMHTTPPORT en CCMHTTPSPORT.  

 Na wijziging van de aangevraagde poorten op de site, nieuwe clients die zijn geïnstalleerd met behulp van de site-brede clientpushinstallatie automatisch geconfigureerd met de huidige poortnummers voor de site.  

#### <a name="to-configure-the-client-communication-port-numbers-for-a-site"></a>De clientcommunicatiepoortnummers voor een site configureren  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, klikt u op **Sites**, en selecteer de primaire site configureren.  

3.  Op de **Start** tabblad **eigenschappen**, en klik vervolgens op de **poorten** tabblad.  

4.  Selecteer een van de items en klik op het pictogram eigenschappen om weer te geven de **Poortdetails** in het dialoogvenster.  

5.  In de **Poortdetails** in het dialoogvenster Geef het poortnummer en beschrijving voor het item en klik vervolgens op **OK**.  

6.  Selecteer **aangepaste website gebruiken** als u de naam van de aangepaste website van **SMSWeb** voor sitesystemen die IIS uitvoeren.  

7.  Klik op **OK** om het dialoogvenster met eigenschappen voor de site.  

 Herhaal deze procedure voor alle primaire sites in de hiërarchie.

