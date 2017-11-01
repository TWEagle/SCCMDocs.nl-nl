---
title: Installeer en wijs de client vanaf het internet toe
titleSuffix: Configuration Manager
description: Installeer en wijs de System Center Configuration Manager-client toe vanaf het internet.
ms.custom: na
ms.date: 8/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a44006eb-8650-49f6-94e1-18fa0ca959ee
caps.latest.revision: "14"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 2ef7580f94864094e9420eb0f5a5c5b4dc9d6d24
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="install-and-assign-configuration-manager-windows-10-clients-using-azure-ad-for-authentication"></a>Installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie

U kunt de Configuration Manager cloudservices met Azure AD gebruiken ter ondersteuning van de volgende scenario's:

- Handmatig de Configuration Manager-client installeren op Windows 10-apparaten via internet en dit toewijzen aan een Configuration Manager-site (vereist dat de sitesysteemrol van cloud management gateway).
- Azure AD gebruikt om clients voor toegang tot uw Configuration Manager-sites te verifiëren. Azure AD vervangt de noodzaak om te configureren en gebruiken van certificaten voor clientverificatie.
- Azure AD-gebruikers in uw site moet worden gebruikt in verzamelingen en andere Configuration Manager-bewerkingen detecteren.

Gebruik de volgende stappen waarmee u kunt dit doen:

- **Stap 1: De app Azure-Services in Configuration Manager-Services voor Cloud instellen en configureren van Azure AD-Gebruikersdetectie**
- **Stap 2: Instellen van de Cloud Management Gateway** (optioneel voor lokale clients)
- **Stap 3: Clientinstellingen voor Windows 10-apparaten met Azure AD join en inschakelen van clients voor gebruik van de Cloud-Management-Gateway configureren**
- **Stap 4: Installeren en registreren van de Configuration Manager-client met behulp van Azure Active Directory-identiteit**


## <a name="before-you-start"></a>Voordat u begint

- U hebt een Azure AD-tenant.
- Uw apparaten moeten Windows 10 wordt uitgevoerd, Azure AD zijn toegevoegd, en worden aangemeld met een Azure AD-identiteit. Clients kunnen ook worden bovendien naar Azure AD die lid zijn verbonden met het domein).
- Naast de [bestaande vereisten](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) voor het beheer van sitesysteemrol, moet u ook controleren of **ASP.NET 4.5** (en andere opties die automatisch zijn geselecteerd) zijn ingeschakeld op de computer die als host fungeert voor deze sitesysteemrol.
- Configuration Manager gebruiken om de client te implementeren:
    - Configureer ten minste één beheerpunt voor de HTTPS-modus als u wilt in plaats van clientcertificaten verifiëren met Azure AD.
        Als u clientcertificaten gebruikt in plaats van de Cloud-Management-Gateway, wordt er een HTTPS-beheerpunt is optioneel maar aanbevolen. Als u Azure AD om te verifiëren, of voor op lokale of Internet-clients het HTTPS-beheerpunt vereist is.
    - Een Cloud Management Gateway instellen als u wilt implementeren, Internet-clients. Voor lokale clients, die u met Azure AD verifieert hoeft u niet te configureren van de Cloud Management Gateway.


## <a name="step-1-set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>Stap 1: De app Azure-Services in Configuration Manager-Services voor Cloud instellen

Dit uw Configuration Manager-site verbindt met Azure AD en is een vereiste voor alle bewerkingen in deze sectie. 

Azure AD-Gebruikersdetectie wordt geconfigureerd als onderdeel van *Cloudbeheer*. De procedure hiervoor is beschreven in stap **6** van de procedure [maken van de Azure-web-app voor gebruik met Configuration Manager](/sccm/core/servers/deploy/configure/Azure-services-wizard#webapp) in het onderwerp *configureren van Azure services voor gebruik met Configuration Manager*.
    
Nadat u de procedure hebt voltooid, kunt u uw Configuration Manager-site hebt verbonden met Azure AD. 

## <a name="step-2-set-up-the-cloud-management-gateway"></a>Stap 2: De Cloudgateway Management instellen

De Cloud Management Gateway instellen om u te helpen bij de cloud scenario's voor beheer in dit onderwerp beschreven. Hulp zoeken in de volgende onderwerpen: 

- [Plannen in Configuration Manager management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway).
- [Instellen van de cloud management gateway voor Configuration Manager](/sccm/core/clients/manage/setup-cloud-management-gateway).
- [Monitor management cloudgateway in Configuration Manager](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway).

## <a name="step-3-configure-client-settings-to-join-windows-10-devices-with-azure-ad-and-enable-clients-to-use-the-cloud-management-gateway"></a>Stap 3: Clientinstellingen voor Windows 10-apparaten met Azure AD join en inschakelen van clients voor gebruik van de Cloud-Management-Gateway configureren

1.  De volgende instellingen configureren (gevonden in de **Cloudservices**) sectie met de informatie in [het configureren van clientinstellingen](/sccm/core/clients/deploy/configure-client-settings).
    - **Toegang tot clouddistributiepunt toestaan** -Schakel deze instelling in om u te helpen apparaten om op te halen van de vereiste inhoud voor het installeren van Configuration Manager-client op basis van het Internet te. Als de inhoud niet beschikbaar op het cloud-distributiepunt is, kunnen apparaten de inhoud ophalen van een beheerpunt dat is verbonden met de cloud management gateway.
    - **Nieuwe Windows 10-apparaten die lid van domein automatisch wordt geregistreerd bij Azure Active Directory** – ingesteld op **Ja** (standaard), of **Nee**.
    - **Clients kunnen gebruiken van een cloud management gateway** – ingesteld op **Ja** (standaard), of **Nee**.
2.  De clientinstellingen implementeren naar de vereiste verzameling van apparaten. Implementeer deze instellingen niet op gebruikersverzamelingen.

Voer de opdracht uit om te bevestigen dat het apparaat wordt gekoppeld aan Azure AD, **dsregcmd.exe/status** in een opdrachtpromptvenster. De **AzureAdjoined** veld in de resultaten ziet **Ja** als het apparaat Azure AD zijn toegevoegd is.


## <a name="step-4-install-and-register-the-configuration-manager-client-using-azure-active-directory-identity"></a>Stap 4: Installeren en registreren van de Configuration Manager-client met behulp van Azure Active Directory-identiteit

Volg de instructies in de client installeert, [clients implementeren op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-clients-manually) met de volgende opdrachtregel voor installatie: 

**ccmsetup.exe /mp &#58; https://contoso.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057594037928100 CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057594037928100 SMSSiteCode = DFD SMSMP = https://SCCMDFPSS.contoso.corp.contoso.com AADTENANTID = 72F988BF-86F1-41AF-91AB-2D7CD011DB47 AADTENANTNAME = contoso AADCLIENTAPPID = bef323b3-042f-41a6-907a-f9faf0d17026 AADRESOURCEURI https://contososerver =**

- **/MP** – downloaden bron. Kunt instellen op CMG als bootstrap vanaf internet.
- **CCMHOSTNAME:** De naam van uw Internet-beheerpunt. U kunt dit vinden door te voeren **gwmi - naamruimte naamruimte-klasse SMS_ActiveMPCandidate** vanaf een opdrachtprompt op een beheerde client.
- **SMSSiteCode:** De sitecode van de Configuration Manager-site.
- **SMSMP:** De naam van uw beheerpunt lookup – het beheerpunt kan niet op uw intranet.
- **AADTENANTID:**, **AADTENANTNAME:** De ID en de naam van de Azure AD-tenant gekoppeld aan Configuration Manager. U vindt dit door dsregcmd.exe/status uitgevoerd vanaf een opdrachtprompt op een Azure AD toegevoegd apparaat.
- **AADCLIENTAPPID:** De Azure AD client app-ID. Zie voor meer informatie over het zoeken naar dit [portal gebruik maken van een Azure Active Directory-toepassing en service-principal die toegang bronnen tot](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key).
- **AADResourceUri:** De id-URI van de app vrijgegeven Azure AD-server. Zie voor meer informatie [configureren van Azure services voor gebruik met Configuration Manager](/sccm/core/servers/deploy/configure/azure-services-wizard).




## <a name="next-steps"></a>Volgende stappen

Als u klaar is, kunt u doorgaan met [clients controleren en beheren](/sccm/core/clients/manage/monitor-clients).
