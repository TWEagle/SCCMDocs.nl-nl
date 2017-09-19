---
title: Clientcommunicatiepoorten configureren | Microsoft Docs
description: Clientcommunicatiepoorten in System Center Configuration Manager instellen.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 406bbdbf-ab4a-4121-a68b-154f96ea14ec
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: a181bd78f1925fa2f17aa4071ea81f58ae1570af
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-configure-client-communication-ports-in-system-center-configuration-manager"></a>Clientcommunicatiepoorten in System Center Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de aangevraagde poortnummers die System Center Configuration Manager-clients gebruiken om te communiceren met sitesystemen die HTTP en HTTPS voor communicatie gebruiken wijzigen. Hoewel HTTP of HTTPS is het waarschijnlijker al is geconfigureerd voor firewalls, clientmeldingen die HTTP of HTTPS is vereist meer CPU-gebruik en geheugen op de beheerpuntcomputer dan als u een aangepast poortnummer. U kunt ook het sitepoortnummer moet worden gebruikt als u clients activeert via traditionele wake-uppakketten opgeven.  

 Wanneer u aangevraagde poorten voor HTTP en HTTPS opgeeft, kunt u zowel een standaardpoortnummer als een alternatief poortnummer opgeven. Clients proberen automatisch de alternatieve poort nadat de communicatie mislukt met de standaardpoort. U kunt instellingen opgeven voor communicatie van HTTP en HTTPS.  

 De standaardwaarden voor de client aangevraagde poortnummers zijn **80** voor HTTP-verkeer en **443** voor HTTPS-verkeer. Deze alleen wijzigen als u niet wilt gebruiken van deze standaardwaarden. Een typisch scenario voor het gebruik van aangepaste poorten is wanneer u een aangepaste website in IIS in plaats van de standaardwebsite. Als u de standaardpoortnummers voor de standaardwebsite in IIS wijzigt en andere toepassingen ook de standaardwebsite gebruiken, zijn deze waarschijnlijk zal mislukken.  

> [!IMPORTANT]  
>  De poortnummers in Configuration Manager niet wijzigen zonder het begrijpen van de gevolgen. Voorbeelden:  
>   
>  -   Als u de poortnummers voor de client aangevraagde services als een siteconfiguratie wijzigt en bestaande clients worden niet opnieuw worden geconfigureerd voor het gebruik van de nieuwe poortnummers, worden deze clients niet onbeheerd.  
> -   Voordat u een niet-standaardpoortnummer configureert, zorg ervoor dat firewalls en alle gekoppelde netwerkapparaten deze configuratie ondersteunt en configureer ze opnieuw naar behoefte. Als u clients op het Internet te beheren en het standaard HTTPS-poortnummer 443 wijzigt, routers en firewalls op het Internet blokkeren mogelijk deze communicatie.  

 Om ervoor te zorgen dat clients niet onbeheerd worden na het wijzigen van de aangevraagde poortnummers, moeten clients worden geconfigureerd voor het gebruik van de nieuwe aangevraagde poortnummers. Wanneer u de aangevraagde poorten op een primaire site wijzigt, nemen alle gekoppelde secundaire sites automatisch dezelfde poortconfiguratie over. Gebruik de procedure in dit onderwerp voor het configureren van de aangevraagde poorten op de primaire site.  

> [!NOTE]  
>  Zie voor meer informatie over het configureren van de aanvraagpoorten voor clients op computers met Linux en UNIX [Aanvraagpoorten configureren voor de Client voor Linux en UNIX](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigLnUClientCommuincations).  

 Wanneer de Configuration Manager-site is gepubliceerd naar Active Directory Domain Services, nieuwe en bestaande clients die toegang deze informatie tot automatisch worden geconfigureerd met hun sitepoortinstellingen en hoeft u geen verdere actie te ondernemen. Clients die geen toegang deze informatie gepubliceerd naar Active Directory Domain Services tot zijn onder andere werkgroepclients, clients van een andere Active Directory-forest, clients die zijn geconfigureerd voor alleen-Internet, en clients die zich momenteel op het Internet. Als u de standaardpoortnummers wijzigt nadat deze clients zijn geïnstalleerd, installeert u deze opnieuw en alle nieuwe clients installeren met behulp van een van de volgende methoden:  

-   De clients opnieuw installeren met behulp van de Wizard Push-clientinstallatie. Clientpushinstallatie configureert automatisch clients met de huidige sitepoortconfiguratie. Zie voor meer informatie over het gebruik van de Wizard Push-clientinstallatie [Configuration Manager-clients installeren door met behulp van Clientpush](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

-   De clients opnieuw installeren met behulp van CCMSetup.exe en de client.msi-installatie-eigenschappen CCMHTTPPORT en CCMHTTPSPORT. Zie voor meer informatie over deze eigenschappen [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

-   De clients opnieuw installeren met behulp van een methode die zoekt naar Active Directory Domain Services naar installatie-eigenschappen van Configuration Manager-client. Zie [About client installation properties published to Active Directory Domain Services in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md) (Informatie over eigenschappen van clientinstallaties die zijn gepubliceerd naar Active Directory Domain Services in System Center Configuration Manager) voor meer informatie.  

 U kunt ook het script PORTSWITCH gebruiken om de poortnummers voor bestaande clients opnieuw, te configureren. VBS die is opgegeven in de installatiemedia in de map SMSSETUP\Tools\PortConfiguration.  

> [!IMPORTANT]  
>  Voor bestaande en nieuwe clients die zich momenteel op het Internet, moet u de niet-standaard poortnummers configureren met behulp van de CCMSetup.exe client.msi-eigenschappen CCMHTTPPORT en CCMHTTPSPORT.  

 Na het wijzigen van de aangevraagde poorten op de site, nieuwe clients die zijn geïnstalleerd met behulp van de gehele site push-clientinstallatiemethode automatisch geconfigureerd met de huidige poortnummers voor de site.  

#### <a name="to-configure-the-client-communication-port-numbers-for-a-site"></a>De poortnummers voor clientcommunicatie voor een site configureren  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, klikt u op **Sites**, en selecteer de primaire site configureren.  

3.  Op de **Start** tabblad **eigenschappen**, en klik vervolgens op de **poorten** tabblad.  

4.  Selecteer een van de items en klik op het pictogram eigenschappen om weer te geven de **Poortdetails** in het dialoogvenster.  

5.  In de **Poortdetails** in het dialoogvenster Geef het poortnummer en beschrijving voor het item en klik vervolgens op **OK**.  

6.  Selecteer **aangepaste website gebruiken** als u de naam van de aangepaste website van **SMSWeb** voor sitesystemen die IIS uitvoeren.  

7.  Klik op **OK** om het dialoogvenster met eigenschappen voor de site.  

 Herhaal deze procedure voor alle primaire sites in de hiërarchie.
