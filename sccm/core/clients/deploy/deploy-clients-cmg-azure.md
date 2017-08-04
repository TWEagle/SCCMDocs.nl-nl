---
title: Installeer en wijs de client toe vanaf het internet | Microsoft Docs
description: Installeer en wijs de System Center Configuration Manager-client toe vanaf het internet.
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a44006eb-8650-49f6-94e1-18fa0ca959ee
caps.latest.revision: 14
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: f604557d208b2dda9dc1c6b4c4d27d896d47695e
ms.contentlocale: nl-nl
ms.lasthandoff: 07/29/2017

---

# <a name="install-and-assign-configuration-manager-clients-from-the-internet-using-azure-ad-for-authentication"></a>Installeren en toewijzen van Configuration Manager-clients via Internet met behulp van Azure AD voor verificatie

U kunt de Configuration Manager cloudservices met Azure AD gebruiken ter ondersteuning van de volgende scenario's:

- Handmatig installeren van Configuration Manager-client van het internet en deze toewijzen aan een Configuration Manager-site (vereist dat de sitesysteemrol van cloud management gateway).
- Azure AD voor verificatie van clients op het Internet toegang krijgen tot uw sites van Configuration Manager gebruiken. Azure AD vervangt de noodzaak om te configureren en gebruiken van certificaten voor clientverificatie.
- Azure AD-gebruikers in uw site moet worden gebruikt in verzamelingen en andere Configuration Manager-bewerkingen detecteren.

Gebruik de volgende stappen waarmee u kunt dit doen:

- **Stap 1: De Cloudgateway Management instellen**
- **Stap 2: De app Azure-Services in Configuration Manager-Services voor Cloud instellen**
- **Stap 3: Clientinstellingen voor het registreren van Windows 10-apparaten met Azure AD configureren**
- **Stap 4: Installeren en registreren van de Configuration Manager-client met behulp van Azure Active Directory-identiteit**


## <a name="before-you-start"></a>Voordat u begint

- U hebt een Azure AD-tenant.
- Uw apparaten moeten Windows 10 wordt uitgevoerd en moet Azure AD zijn toegevoegd. Clients kunnen ook worden bovendien naar Azure AD die lid zijn verbonden met het domein).
- Naast de [bestaande vereisten](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) voor het beheer van sitesysteemrol, moet u ook controleren of **ASP.NET 4.5** (en andere opties die automatisch zijn geselecteerd) zijn ingeschakeld op de computer die als host fungeert voor deze sitesysteemrol.
- Configuration Manager gebruiken om de client te implementeren:
    - Configureer ten minste één beheerpunt voor de HTTPS-modus.
    - Instellen van een Cloud-Management-Gateway.

## <a name="step-1-set-up-the-cloud-management-gateway"></a>Stap 1: De Cloudgateway Management instellen

De Cloud Management Gateway instellen, kunnen clients toegang tot uw Configuration Manager-site van het internet zonder gebruik van certificaten. Hulp zoeken in de volgende onderwerpen: 

- [Plannen in Configuration Manager management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway).
- [Instellen van de cloud management gateway voor Configuration Manager](/sccm/core/clients/manage/setup-cloud-management-gateway).
- [Monitor management cloudgateway in Configuration Manager](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway).

## <a name="step-2-set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>Stap 2: De app Azure-Services in Configuration Manager-Services voor Cloud instellen

Dit uw Configuration Manager-site verbindt met Azure AD en is een vereiste voor alle bewerkingen in deze sectie. 

Azure AD-Gebruikersdetectie wordt geconfigureerd als onderdeel van *Cloudbeheer*. De procedure hiervoor is beschreven in stap **6** van de procedure [maken van de Azure-web-app voor gebruik met Configuration Manager](/sccm/core/servers/deploy/configure/Azure-services-wizard#webapp) in het onderwerp *configureren van Azure services voor gebruik met Configuration Manager*.
    
Nadat u de procedure hebt voltooid, kunt u uw Configuration Manager-site hebt verbonden met Azure AD. 

## <a name="step-3-configure-client-settings-to-register-windows-10-devices-with-azure-ad"></a>Stap 3: Clientinstellingen voor het registreren van Windows 10-apparaten met Azure AD configureren

1.  Configureer de volgende client-instellingen (te vinden in de Cloud-Services) sectie met de informatie in [het configureren van clientinstellingen](/sccm/core/clients/deploy/configure-client-settings).
    - **Nieuwe Windows 10-apparaten die lid van domein automatisch wordt geregistreerd bij Azure Active Directory** – ingesteld op **Ja** (standaard), of **Nee**.
    - **Clients kunnen gebruiken van een cloud management gateway** – ingesteld op **Ja** (standaard), of **Nee**.
2.  De clientinstellingen implementeren naar de vereiste verzameling van apparaten.

Voer de opdracht uit om te bevestigen dat het apparaat wordt gekoppeld aan Azure AD, **dsregcmd.exe/status** in een opdrachtpromptvenster. De **AzureAdjoined** veld in de resultaten ziet **Ja** als het apparaat Azure AD zijn toegevoegd is.


## <a name="step-4-install-and-register-the-configuration-manager-client-using-azure-active-directory-identity"></a>Stap 4: Installeren en registreren van de Configuration Manager-client met behulp van Azure Active Directory-identiteit

Voordat u begint, zorg ervoor dat de bronbestanden van de client-installatie worden lokaal opgeslagen op het apparaat waarnaar de client te installeren. Gebruik vervolgens de instructies in [clients implementeren op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-clients-manually) met de volgende opdrachtregel voor installatie: 

**ccmsetup.exe usepkicert/nocrlcheck /Source:C:\CLIENT CCMHOSTNAME=SCCMPROXYCONTOSO.CLOUDAPP.NET/CCM_Proxy_ServerAuth/72457598037527932 SMSSiteCode = HEC AADTENANTID = 780433B5-E05E-4B7D-BFD1-E8013911E543 AADTENANTNAME = contoso AADCLIENTAPPID AADRESOURCEURI = https://contososerver =**

- **/ NoCrlCheck:** Als uw management verwijzen of cloud management gateway maakt gebruik van een niet-openbaar certificaat, en vervolgens de client mogelijk niet de locatie van de CRL te bereiken.
- **/ Bron:** Lokale map: Locatie van de clientinstallatiebestanden.
- **CCMHOSTNAME:** De naam van uw Internet-beheerpunt. U kunt dit vinden door te voeren **gwmi - naamruimte naamruimte-klasse SMS_ActiveMPCandidate** vanaf een opdrachtprompt op een beheerde client.
- **SMSMP:** De naam van uw beheerpunt lookup – het beheerpunt kan niet op uw intranet.
- **SMSSiteCode:** De sitecode van de Configuration Manager-site.
- **AADTENANTID:**, **AADTENANTNAME:** De ID en de naam van de Azure AD-tenant gekoppeld aan Configuration Manager. U vindt dit door dsregcmd.exe/status uitgevoerd vanaf een opdrachtprompt op een Azure AD toegevoegd apparaat.
- **AADCLIENTAPPID:** De Azure AD client app-ID. Zie voor meer informatie over het zoeken naar dit [portal gebruik maken van een Azure Active Directory-toepassing en service-principal die toegang bronnen tot](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key).
- **AADResourceUri:** De id-URI van de app vrijgegeven Azure AD-server.


## <a name="next-steps"></a>Volgende stappen

Als u klaar is, kunt u doorgaan met [clients controleren en beheren](/sccm/core/clients/manage/monitor-clients).

