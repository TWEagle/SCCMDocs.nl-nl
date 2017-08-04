---
title: Wizard Azure-services | Microsoft Docs
description: Over de wizard Azure-services voor System Center Configuration Manager.
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a26a653e-17aa-43eb-ab36-0e36c7d29f49
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 0663ba84762c44a5c303562548499f195bae9e1c
ms.openlocfilehash: 22203b358830903cf2e531c0532ae3111b8265fc
ms.contentlocale: nl-nl
ms.lasthandoff: 08/01/2017

---
# <a name="configure-azure-services-for-use-with-configuration-manager"></a>Azure-services voor gebruik met Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie van de huidige vertakking 1706, de **Wizard Azure-Services** wordt gebruikt voor het vereenvoudigen van het proces van het configureren van Azure services die u met Configuration Manager gebruikt.

Deze wizard biedt een gemeenschappelijke ervaring voor configuratie door middel van een **Azure-web-app** om details van abonnement en de configuratie te verstrekken. De web-app vervangt voeren dezelfde informatie telkens wanneer u een nieuwe Configuration Manager-component of de service met Azure instellen.

De volgende Azure-services zijn geconfigureerd met de wizard Azure-Services configureren:
-   **Cloud-Management**   
    [Inschakelen voor clients te verifiëren met behulp van Azure Active Directory]() (Azure AD). U kunt ook [configureren van Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc).
-   **OMS Connector**
    [verbinding maken met Operations Manager-Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS) en het synchroniseren van gegevens, zoals verzamelingen met OMS-logboekanalyse.
-   **Gereedheid voor upgrade**
    [verbinding maken met de gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) en weergeven van clientgegevens upgrade-compatibiliteit.
-   **Windows Store voor bedrijven** verbinding maken met de online winkel voor [Windows Store voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) en apps ophalen voor uw organisatie die u met Configuration Manager implementeren kunt.

Wanneer u de wizard voor het configureren van een service gebruikt, is enkele veelvoorkomende acties zijn beschikbaar.
Deze omvatten:
-   Configureer de Azure-omgeving:  Op de **App** pagina van de wizard, selecteert u de **Azure-omgeving** die u gebruikt. Zie de inhoud voor elke service voor meer informatie over het ondersteunt alleen de openbare Azure-cloud of een privécloud kan worden ondersteund.
-   Maken of importeren van een server app:   Op de **App** pagina van de wizard kunt u **maken** en **importeren** Azure-web-apps. De beschikbare opties zijn afhankelijk van de service die u configureert.  Sommige services mogelijk ook een extra-app. Bijvoorbeeld, een service ook mogelijk een **Native Client-app**.


Zie voor meer informatie over Azure-web-apps [verificatie en autorisatie in Azure App Service](/azure/app-service/app-service-authentication-overview), en [overzicht van Web-Apps](/azure/app-service-web/app-service-web-overview)


## <a name="webapp"></a>Maken van de Azure-web-app voor gebruik met Configuration Manager

De Azure-services-web-app uw Configuration Manager-site verbindt met Azure AD en is een vereiste voor het gebruik van Azure-services in uw infrastructuur. U doet dit als volgt:

1.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, en klik vervolgens op **Azure Services**.
2.  Op de **Start** tabblad, in de **Azure Services** groep, klikt u op **Azure-Services configureren**.
3.  Op de **Azure Services** pagina van de Azure-Services Wizard **Cloudbeheer** wilt toestaan dat clients verifiëren met de hiërarchie met gebruik van Azure AD.
4.  Op de **algemene** pagina van de wizard, geeft u een naam en een beschrijving voor uw Azure-service.
5.  Op de **App** pagina van de wizard, selecteert u uw Azure-omgeving in de lijst en klik op **Bladeren** selecteren de *Web-app* en *Native Client-app* dat wordt gebruikt voor het configureren van de Azure-service.     
    **Web-app:**   Bladeren opent u de Server App-venster.    
      In de **App Server** venster, selecteer de server-app die u wilt gebruiken en klik vervolgens op **OK**. Server-apps zijn de Azure-web-apps die de configuraties voor uw Azure-account, inclusief uw Tenant-ID, Client-ID en een geheime sleutel voor clients bevatten.
    Als u een beschikbare app niet hebt, gebruikt u een van de volgende:
        - **Maak**: Klik op om een nieuwe server app **maken**. Geef vervolgens een beschrijvende naam voor de app, de URL van de startpagina, App-ID-URI en de geheime sleutel geldigheidsperiode. De geheime sleutel geldigheidsduur is één jaar.

         Om door te gaan iemand moet nu aanmelden bij Azure voltooien van de web-app gemaakt in Azure. Het account waarmee u kunt aanmelden bij Azure hoeft niet te worden van hetzelfde account dat wordt uitgevoerd in de Wizard Azure-Services. Na het aanmelden bij Azure maakt Configuration Manager de web-app in Azure voor u, met inbegrip van de Client-ID en een geheime sleutel voor gebruik met de web-app. U kunt later uit de Azure-portal bekijken.

         Wanneer u maken voor het configureren van een web-app gebruikt, kan Configuration Manager de web-app voor u in Azure AD maken.
        - **Importeren**: Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en het tenantnetwerk en geef vervolgens de Tenant-ID, Client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u de gegevens controleren, klikt u op **OK** om door te gaan.

          Deze optie is niet beschikbaar voor alle services die u configureert.

   **Native Client-app:**  Bladeren opent het venster Client-App.  
     In de **Clientapp** venster, selecteer de client-app die u wilt gebruiken en klik vervolgens op **OK**.

     Als u een beschikbare client-app niet hebt, gebruikt u een van de volgende:
     - **Maak**: Klik op om een nieuwe Client-app **maken**. Naast een beschrijvende naam voor de app en de antwoord-URL opgeven.

          Om door te gaan iemand moet nu aanmelden bij Azure om uit te voeren van het client-app maken in Azure. Het account waarmee u kunt aanmelden bij Azure hoeft niet te worden van hetzelfde account dat wordt uitgevoerd in de Wizard Azure-Services. Na het aanmelden bij Azure maakt Configuration Manager de native client-app in Azure voor u, met inbegrip van de Client-ID voor gebruik met de web-app. U kunt later uit de Azure-portal bekijken.
          Wanneer u maken voor het configureren van de app gebruikt, kan Configuration Manager maakt de native client-app voor u in Azure AD.
     - **Importeren**: Voor het gebruik van een client-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en de Client-ID. Klik vervolgens op **OK** om door te gaan.
           Deze optie is niet beschikbaar voor alle services die u configureert.

  <!--  MOVE THIS AND STEP 6 TO configure Azure AD User Discover  content
       [!TIP]  
     When you use Import, the account you use to run the wizard must have the *Read directory data* application permission in the Azure portal. This is required to set the correct permissions for the App. When you use Create, Configuration Manager creates the app with the correct permissions. However, you still must give consent to the application in the Azure portal.   -->


6.  Op de **detectie** pagina van de wizard, klikt u op **inschakelen Azure Active Directory-Gebruikersdetectie**, en klik vervolgens op **instellingen**.
In de **Discovery-instellingen van Azure AD-gebruiker** dialoogvenster Configureer een planning voor wanneer detectie wordt uitgevoerd. U kunt ook detectie van verschillen die controleert op nieuwe of gewijzigd accounts in Azure AD inschakelen. Meer informatie over [Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).
 
 7. Voltooi de wizard.

Op dit moment hebt u uw Configuration Manager-site naar Azure AD verbonden.

## <a name="view-the-configuration-of-an-azure-service"></a>De configuratie van een Azure-service weergeven
U kunt de eigenschappen van een Azure-service die u hebt geconfigureerd voor gebruik weergeven.

Ga in de console naar **beheer** > **overzicht** > **Cloudservices** > **Azure Services**. Kies vervolgens de service die u wilt weergeven of bewerken en klik vervolgens op **eigenschappen**.

