---
title: Installeer de client met Azure AD
titleSuffix: Configuration Manager
description: Installeer en wijs de Configuration Manager-client op Windows 10-apparaten met Azure Active Directory voor verificatie toe
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a44006eb-8650-49f6-94e1-18fa0ca959ee
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4a8ca1a60a249756065ee2af6cb9c37f3fe2a1e0
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="install-and-assign-configuration-manager-windows-10-clients-using-azure-ad-for-authentication"></a>Installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie

Als u wilt de Configuration Manager-client installeren op Windows 10-apparaten met behulp van Azure AD-verificatie, Configuration Manager worden geïntegreerd met Azure Active Directory (Azure AD). Clients kunnen zijn op het intranet rechtstreeks communiceert met een HTTPS-beheerpunt. Ze kunnen ook worden internetgebaseerde communiceren via de CMG of met een internet-gebaseerd beheerpunt bevindt. Dit proces maakt gebruik van Azure AD om clients naar de Configuration Manager-site te verifiëren. Azure AD vervangt de noodzaak om te configureren en gebruiken van certificaten voor clientverificatie.



## <a name="before-you-begin"></a>Voordat u begint

- Een Azure AD-tenant is een vereiste  

- Apparaatvereisten voor:  

    - Windows 10  

    - Toegevoegd aan Azure AD. pure cloud domein- of hybride Azure AD zijn toegevoegd  

- Gebruikersvereisten voor:  

    - De aangemelde gebruiker moet een Azure AD-identiteit.   

    - Als de gebruiker een identiteit federatieve of gesynchroniseerd wordt, moet u Configuration Manager [Active Directory-gebruikersdetectie](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) , evenals [Azure AD-gebruikersdetectie](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc). Zie voor meer informatie over hybride identiteiten [definiëren van een strategie voor hybride identiteit ingebruikname](/azure/active-directory/active-directory-hybrid-identity-design-considerations-identity-adoption-strategy).<!--497750-->  

- Naast de [bestaande vereisten](/sccm/core/plan-design/configs/site-and-site-system-prerequisites#bkmk_2012MPpreq) voor het beheer van sitesysteemrol, ook inschakelen **ASP.NET 4.5** op deze server. Andere opties automatisch geselecteerd bij het inschakelen van ASP.NET 4.5 bevatten.  

- Configureer alle beheerpunten voor de HTTPS-modus. Zie voor meer informatie [PKI-certificaatvereisten](/sccm/core/plan-design/network/pki-certificate-requirements) en [implementeren van het Webservercertificaat voor sitesystemen die IIS uitvoeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012).  

- Instellen (optioneel) een [management cloudgateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway) (CMG) voor het implementeren van clients op internet. Voor lokale clients die met Azure AD verifiëren, hoeft u niet een CMG.  


## <a name="configure-azure-services-for-cloud-management"></a>Azure-Services voor het Cloudbeheer van de configureren

Verbinding maken met uw Configuration Manager-site naar Azure AD als de eerste stap. Zie voor meer informatie van dit proces [configureren Azure-services](/sccm/core/servers/deploy/configure/azure-services-wizard). Maak een verbinding met de **Cloudbeheer** service.

Schakel [Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc) als onderdeel van de voorbereiding voor **Cloudbeheer**. 

Nadat u deze acties voltooid, wordt uw Configuration Manager-site is verbonden met Azure AD. 



## <a name="configure-client-settings"></a>Clientinstellingen configureren

Deze clientinstellingen helpen join Windows 10-apparaten met Azure AD. Ze kunnen ook internet gebaseerde clients CMG en cloud-distributiepunt.

1.  Configureer de volgende clientinstellingen in de **Cloudservices** sectie met de informatie in [het configureren van clientinstellingen](/sccm/core/clients/deploy/configure-client-settings).  

    - **Toegang tot clouddistributiepunt toestaan**: Schakel deze instelling bij het ophalen van de vereiste inhoud voor het installeren van Configuration Manager-client op basis van een internet-apparaten. Als de inhoud niet beschikbaar op het cloud-distributiepunt, kunnen apparaten de inhoud ophalen van de CMG. De installatie van client bootstrap pogingen het cloud-distributiepunt van vier uur voordat deze terug naar de CMG valt.<!--495533-->  

    - **Nieuwe Windows 10-apparaten die lid van domein automatisch wordt geregistreerd bij Azure Active Directory**: Ingesteld op **Ja** of **Nee**. De standaardinstelling is **Ja**. Dit gedrag is ook standaard in Windows 10 versie 1709.

    - **Clients kunnen gebruiken van een cloud management gateway** – ingesteld op **Ja** (standaard), of **Nee**.  

2.  De clientinstellingen implementeren naar de vereiste verzameling van apparaten. Implementeer deze instellingen niet op gebruikersverzamelingen.

Uitvoeren om te bevestigen op het apparaat wordt gekoppeld aan Azure AD, `dsregcmd.exe /status` in een opdrachtprompt. De **AzureAdjoined** veld in de resultaten ziet **Ja** als het apparaat Azure AD zijn toegevoegd is.



## <a name="install-and-register-the-client-using-azure-ad-identity"></a>Installeren en registreren van de client met behulp van Azure AD identity

Voor handmatige installatie van de client met behulp van Azure AD identity Lees eerst de algemene procedure op [clients handmatig installeren](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual). 

 > [!Note]  
 > Het apparaat moet toegang tot het internet contact te maken met Azure AD, maar hoeven niet te worden op basis van het internet. 

Het volgende voorbeeld ziet u de algemene structuur van de opdrachtregel: `ccmsetup.exe /mp:<source management point> CCMHOSTNAME=<internet-based management point> SMSSiteCode=<site code> SMSMP=<initial management point> AADTENANTID=<Azure AD tenant identifier> AADTENANTNAME=<Azure AD tenant name> AADCLIENTAPPID=<Azure AD client app identifier> AADRESOURCEURI=<Azure AD server app identifier>`

Zie voor meer informatie [clientinstallatie-eigenschappen](/sccm/core/clients/deploy/about-client-installation-properties).

De CCMHOSTNAME-eigenschappen en /mp Geef een van de volgende, afhankelijk van het scenario:
- Een on-premises-beheerpunt. Alleen de eigenschap /mp opgeven. De CCMHOSTNAME is niet vereist.
- Beheergateway cloud
- Internet-gebaseerd beheerpunt bevindt de SMSMP-eigenschap geeft de on-premises of een beheerpunt op internet.

In dit voorbeeld wordt een cloud-management-gateway. Hiermee vervangt u voorbeeldwaarden voor elke eigenschap: `ccmsetup.exe /mp:https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC SMSMP=https://mp1.contoso.com AADTENANTID=daf4a1c2-3a0c-401b-966f-0b855d3abd1a AADTENANTNAME=contoso AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver`

Zie het proces voor het automatiseren van de client installeren met behulp van Azure AD identity via Microsoft Intune [voorbereiden Windows 10-apparaten voor het beheer van CO](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client).



## <a name="next-steps"></a>Volgende stappen

Als u klaar is, kunt u doorgaan met [clients controleren en beheren](/sccm/core/clients/manage/monitor-clients).
