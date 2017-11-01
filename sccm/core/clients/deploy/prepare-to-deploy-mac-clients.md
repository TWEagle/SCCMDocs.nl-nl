---
title: Implementatie van clientsoftware op Mac-computers voorbereiden
titleSuffix: Configuration Manager
description: Configuratietaken voordat u Configuration Manager-client implementeert op Mac-computers.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2285a953-6a86-4ed5-97dd-cd57b02bc1ee
caps.latest.revision: "12"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: b878c7b0328e89ff7b12bf44167fd12444a0cba4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="prepare-to-deploy-client-software-to-macs"></a>Implementatie van clientsoftware op Mac-computers voorbereiden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Volg deze stappen om ervoor te zorgen dat u nu [Configuration Manager-client implementeren op Mac-computers](/sccm/core/clients/deploy/deploy-clients-to-macs). 

## <a name="mac-prerequisites"></a>Vereisten voor Mac

Het installatiepakket voor Mac-client wordt niet meegeleverd met de Configuration Manager-media. Download de **Clients voor aanvullende besturingssystemen** van de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

**Ondersteunde versies:**  

-   **Mac OS X 10.6** (sneeuw Leopard) 

-   **Mac OS X 10.7** (Lion) 

-   **Mac OS X 10.8** (Mountain Lion)

-   **Mac OS X 10.9** (Mavericks)

-   **Mac OS X 10.9** (Mavericks)  

-   **Mac OS X 10.10** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10,12** (Mac OS Sierra)  

## <a name="certificate-requirements"></a>Certificaatvereisten
Vereist certificaten voor openbare-sleutelinfrastructuur (PKI) client installeren en beheren voor Mac-computers. PKI-certificaten beveiligen de communicatie tussen de Mac-computers en de Configuration Manager-site met behulp van wederzijdse verificatie en versleutelde gegevensoverdracht. Configuration Manager kunt aanvragen en installeren van een clientcertificaat voor gebruikers met behulp van Microsoft Certificate Services met een enterprise-certificeringsinstantie (CA) en de Configuration Manager inschrijving punt en de inschrijving proxy sitesysteemrollen. Of u kunt aanvragen en een computercertificaat installeren onafhankelijk van Configuration Manager als het certificaat voldoet aan de vereisten voor Configuration Manager.   
  
Configuration Manager Mac-clients voeren altijd certificaatintrekkingscontrole. U kunt deze functie niet uitschakelen.  
  
Als Mac-clients de certificaatintrekkingsstatus voor een servercertificaat kunnen niet bevestigen, omdat ze de CRL niet kunnen vinden, is ze niet mogelijk om verbinding te maken met sitesystemen van Configuration Manager. In het bijzonder voor Mac-clients in een verschillend forest dan de uitgevende certificeringsinstantie, dient u uw CRL-ontwerp te controleren om ervoor te zorgen dat Mac-clients een CRL-distributiepunt (CDP) kunnen vinden en er een verbinding mee kunnen maken om een verbinding te maken met sitesysteemservers.  

Voordat u Configuration Manager-client op een Mac-computer installeert, bepalen hoe u het clientcertificaat installeren:  

-   Gebruik Configuration Manager-inschrijving door de [CMEnroll-hulpprogramma](/sccm/core/clients/deploy/deploy-clients-to-macs#install-the-client-and-then-enroll-the-client-certificate-on-the-mac). Het inschrijvingsproces ondersteunt geen automatische certificaatsvernieuwing, daarom moet u Mac-computers opnieuw inschrijven voordat het geïnstalleerde certificaat verlopen is.  

-   [Gebruik een certificaataanvraag en -installatiemethode die onafhankelijk is van Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-macs#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager).  

Zie voor meer informatie over de certificaatsvereiste van de Mac-client en andere PKI-certificaten die vereist zijn ter ondersteuning van Mac-computers, [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

Mac-clients worden automatisch toegewezen aan de Configuration Manager-site die ze beheert. Mac-clients worden als clients met alleen internetverbinding geïnstalleerd, zelfs als de communicatie beperkt is tot het intranet. Deze clientconfiguratie betekent dat ze zullen communiceren met de sitesysteemrollen (beheerpunten en distributiepunten) in hun toegewezen site wanneer u deze sitesysteemrollen configureert om clientverbindingen van het internet toe te staan. Mac-computers communiceren niet met sitesysteemrollen buiten hun toegewezen site.  

> [!IMPORTANT]  
>  De Configuration Manager Mac-client kan niet worden gebruikt om een beheerpunt dat is geconfigureerd voor gebruik met een [databasereplica](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  


## <a name="deploy-a-web-server-certificate-to-site-system-servers"></a>Implementeer een Webservercertificaat op sitesysteemservers  
Als deze sitesystemen niet hebt, implementeert u een Webservercertificaat op de computers waarvoor deze sitesysteemrollen:  

-   Beheerpunt  

-   Distributiepunt  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

Het webservercertificaat moet de internet-FQDN bevatten dat in de sitesysteemeigenschappen is opgegeven. De server heeft geen toegankelijk zijn vanaf Internet ter ondersteuning van Mac-computers. Als u geen clientbeheer via internet vereist, kunt u de intranet FQDN-waarde voor de internet-FQDN opgeven.  

Geeft het sitesysteem Internet-FQDN-waarde in het Webservercertificaat voor het beheerpunt, het distributiepunt en het proxypunt voor inschrijving. 

Zie voor een voorbeeldimplementatie die is gemaakt en dit Webservercertificaat wordt geïnstalleerd, de [het Webservercertificaat voor Sitesystemen die IIS uitvoeren implementeren](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_webserver2008_cm2012).  


## <a name="deploy-a-client-authentication-certificate-to-site-system-servers"></a>Implementeer een certificaat voor clientverificatie op sitesysteemservers  
 Als deze sitesystemen niet hebt, implementeert u een certificaat voor clientverificatie op de computers die deze sitesysteemrollen hosten:  

-   Beheerpunt  

-   Distributiepunt  

 Zie voor een voorbeeldimplementatie die creëert en installeert het clientcertificaat voor beheerpunten, de [de Client-certificaat voor Windows-Computers implementeren](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_client2008_cm2012)  

 Zie voor een voorbeeldimplementatie die creëert en installeert het clientcertificaat voor distributiepunten, de [het clientcertificaat voor distributiepunten implementeren](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_clientdistributionpoint2008_cm2012).  

>[!IMPORTANT]
>  Voor het implementeren van de client op apparaten met Mac OS Sierra, moet de onderwerpnaam van het certificaat zijn correct geconfigureerd, bijvoorbeeld met behulp van de FQDN van de beheerpuntserver.

## <a name="prepare-the-client-certificate-template-for-macs"></a>Bereid het clientcertificaatsjabloon voor Macs  

 Het certificaatsjabloon moet de machtigingen **Lezen** en **Inschrijven** hebben voor de gebruikersaccount die het certificaat op de Mac-computer zal inschrijven.  

 Zie [het clientcertificaat voor Mac-Computers implementeren](../../plan-design/network/example-deployment-of-pki-certificates.md#BKMK_MacClient_SP1).  

## <a name="configure-the-management-point-and-distribution-point"></a>Configureer het beheerpunt en distributiepunt.  
 Configureer beheerpunten voor de volgende opties:  

-   HTTPS  

-   Clientverbindingen via Internet toestaat. Deze configuratiewaarde is vereist voor het beheren van Mac-computers. Het betekent echter niet dat sitesysteemservers toegankelijk moeten zijn vanop het internet.  

-   Laat mobiele apparaten en Mac-computers dit beheerpunt gebruiken  

 Hoewel distributiepunten niet vereist om de client te installeren, moet u distributiepunten om clientverbindingen toestaat vanaf het Internet als u software implementeren op deze computers wilt nadat de client is geïnstalleerd.  

 
### <a name="to-configure-management-points-and-distribution-points-to-support-macs"></a>Beheerpunten en distributiepunten ter ondersteuning van Macs configureren  

Voordat u deze procedure start, moet u ervoor zorgen dat de sitesysteemserver die het beheerpunt en distributiepunt uitvoert, is geconfigureerd met een internet-FQDN. Als u deze servers clientbeheer op Internet niet wordt ondersteund, kunt u de intranet-FQDN opgeven als de Internet-FQDN-waarde. 

De sitesysteemrollen moeten zich in een primaire site.  


1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Servers en sitesysteemrollen**, en kies vervolgens de server met de juiste sitesysteemrollen.  

3.  In het detailvenster met de rechtermuisknop op **beheerpunt**, kies **roleigenschappen**, en in de **Beheerpunteigenschappen** dialoogvenster deze opties configureren:  

    1.  Kies **HTTPS**.  

    2.  Kies **clientbeheer alleen verbindingen toestaan** of **intranet en internetclient verbindingen toestaan**. Deze opties vereisen een Internet of een intranet-FQDN.  

    3.  Kies **laat mobiele apparaten en Mac-computers dit beheerpunt te gebruiken**.  

4.  In het detailvenster met de rechtermuisknop op **distributiepunt**, kies **roleigenschappen**, en in de **Distributiepunteigenschappen** dialoogvenster deze opties configureren:  

    -   Kies **HTTPS**.  

    -   Kies **clientbeheer alleen verbindingen toestaan** of **intranet en internetclient verbindingen toestaan**. Deze opties vereisen een Internet of een intranet-FQDN.  

    -   Kies **certificaat importeren**, blader naar het geëxporteerde distribution point certificaatbestand en geef vervolgens het wachtwoord.  

5.  Herhaal stappen 2 t/m 4 voor alle beheerpunten en distributiepunten in primaire sites die u met Macs gebruiken wilt.  

## <a name="configure-the-enrollment-proxy-point-and-the-enrollment-point"></a>Configureer het inschrijvingsproxypunt en het registratiepunt  
 U moet deze beide sitesysteemrollen in dezelfde site installeren, maar u moet ze niet op dezelfde sitesysteemserver, of in hetzelfde Active Directory-forest installeren.  

 Zie voor meer informatie over het plaatsen van sitesysteemrollen en overwegingen [sitesysteemrollen](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) in [plan maken voor sitesysteemservers en sitesysteemrollen voor System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).  

 Deze procedures configureren de sitesysteemrollen ter ondersteuning van Mac-computers.   

-   [Nieuwe sitesysteemserver](#new-site-system-server)  

-   [Bestaande sitesysteemserver](#existing-site-system-server)  

###  <a name="new-site-system-server"></a>Nieuwe sitesysteemserver  

1.  Kies in de Configuration Manager-console **beheer** >  **siteconfiguratie** > **Servers en sitesysteemrollen**  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Sitesysteemserver maken**.  

4.  Op de **algemene** pagina, geeft u de algemene instellingen voor het sitesysteem.  Zorg ervoor dat u een waarde voor de Internet-FQDN opgeeft. Als de server is niet toegankelijk is vanaf het Internet, gebruikt u de intranet-FQDN.  

5.  Op de **Systeemrolselectie** pagina **proxypunt voor inschrijving** en **inschrijvingspunt** uit de lijst met beschikbare rollen.  

6.  Op de **proxypunt voor inschrijving** pagina, controleert u de instellingen en breng de gewenste wijzigingen.  

7.  Op de **instellingen voor Inschrijvingspunt** pagina, controleert u de instellingen en breng de gewenste wijzigingen. Voltooi de wizard.  

### <a name="existing-site-system-server"></a>Bestaande sitesysteemserver  

1.  Kies in de Configuration Manager-console **beheer** >  **siteconfiguratie** > **Servers en sitesysteemrollen**, en kies vervolgens de server die u gebruiken wilt ter ondersteuning van Macs.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **sitesysteemrollen toevoegen**.  

4.  Configureer de algemene instellingen voor het sitesysteem op de pagina **Algemeen** en klik vervolgens op **Volgende**. Zorg ervoor dat u een waarde voor de Internet-FQDN opgeeft. Als de server is niet toegankelijk is vanaf het Internet, gebruikt u de intranet-FQDN.   

5.  Op de **Systeemrolselectie** pagina **proxypunt voor inschrijving** en **inschrijvingspunt** uit de lijst met beschikbare rollen.  

6.  Op de **proxypunt voor inschrijving** pagina, controleert u de instellingen en breng de gewenste wijzigingen.  

7.  Op de **instellingen voor Inschrijvingspunt** pagina, controleert u de instellingen en breng de gewenste wijzigingen. Voltooi de wizard.  

## <a name="install-the-reporting-services-point"></a>Installeer het reporting servicepunt  
 [Installeer het reporting servicepunt](../../../core/servers/manage/configuring-reporting.md) als u wilt uitvoeren van rapporten voor Macs.  

### <a name="next-steps"></a>Volgende stappen

[Configuration Manager-client implementeren op Mac-computers](/sccm/core/clients/deploy/deploy-clients-to-macs).  