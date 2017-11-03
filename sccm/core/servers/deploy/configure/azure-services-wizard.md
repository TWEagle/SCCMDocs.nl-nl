---
title: Wizard Azure-services
titleSuffix: Configuration Manager
description: Over de wizard Azure-services voor System Center Configuration Manager.
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a26a653e-17aa-43eb-ab36-0e36c7d29f49
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 833bc6588e079e124209d9c7adb91062e6afe6c3
ms.sourcegitcommit: d025a2cbd1ed82f42f67255c97b913f2163b3baf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/02/2017
---
# <a name="configure-azure-services-for-use-with-configuration-manager"></a>Azure-services voor gebruik met Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Vanaf versie van de huidige vertakking 1706, de **Wizard Azure-Services** wordt gebruikt voor het vereenvoudigen van het configuratieproces van de Azure-services u met Configuration Manager gebruikt.

Deze wizard biedt een gemeenschappelijke ervaring voor configuratie door middel van een **Azure AD-web-app-registratie** voor het abonnement en configuratiegegevens bieden en verifiëren van de communicatie met Azure AD. De web-app vervangt voeren dezelfde informatie telkens wanneer u een nieuwe Configuration Manager-component of de service met Azure instellen.

De volgende Azure-services kunnen worden geconfigureerd met de wizard Azure-Services:
-   **Cloud-Management**   
    [Inschakelen voor clients te verifiëren met behulp van Azure Active Directory](/sccm/core/clients/deploy/deploy-clients-cmg-azure) (Azure AD). U kunt ook [configureren van Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc).
-   **OMS Connector**
    [verbinding maken met Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS) en het synchroniseren van gegevens, zoals verzamelingen met OMS-logboekanalyse.
-   **Gereedheid voor upgrade**
    [verbinding maken met de gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) en weergeven van clientgegevens upgrade-compatibiliteit.
-   **Microsoft Store voor bedrijven** verbinding maken met de [Microsoft Store voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) en apps ophalen voor uw organisatie die u met Configuration Manager implementeren kunt.

Wanneer u de wizard voor het configureren van een service gebruikt, is enkele veelvoorkomende acties zijn beschikbaar.
Deze omvatten:
-   *Configureren van de Azure-omgeving*:  Op de **App** pagina van de wizard selecteert u de **Azure-omgeving** die u gebruikt. Zie de inhoud voor elke service voor meer informatie over het ondersteunt alleen de openbare Azure-cloud of een privécloud kan worden ondersteund.
-   *Maken of importeren van een server app*:   Op de **App** pagina van de wizard kunt u **maken** en **importeren** Azure-web-app-registratie metagegevens. De beschikbare opties zijn afhankelijk van de service die u configureert. Sommige services mogelijk ook een extra-app. Bijvoorbeeld, de **Cloud management** service vereist een **Native Client-app** die wordt gebruikt voor clients rechtstreeks om communicatie te verifiëren met Azure-services.


Zie voor meer informatie over Azure-web-apps [verificatie en autorisatie in Azure App Service](/azure/app-service/app-service-authentication-overview), en [overzicht van Web-Apps](/azure/app-service-web/app-service-web-overview).


## <a name="webapp"></a>Maken of importeren van een Azure Active Directory web-app te registreren voor gebruik met Configuration Manager

De registratie van de Azure-services-web-app verbindt uw Configuration Manager-site naar Azure AD en is een vereiste voor het gebruik van Azure-services in uw infrastructuur. U doet dit als volgt:

1.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, en klik vervolgens op **Azure Services**.
2.  Op de **Start** tabblad, in de **Azure Services** groep, klikt u op **Azure-Services configureren**.
3.  Op de **Azure Services** pagina van de Wizard Azure-Services, selecteer de Azure-service die u wilt verbinding maken met Configuration Manager.
4.  Op de **algemene** pagina van de wizard, geeft u een naam en een beschrijving voor uw Azure-service.
5.  Op de **App** pagina van de wizard, selecteert u uw Azure-omgeving in de lijst en klik op **Bladeren** selecteren de *Web-app* en *Native Client-app* (alleen indien nodig) dat wordt gebruikt voor het configureren van de Azure-service.

    **Web-app:**   Bladeren opent u de Server App-venster.    
      In de **App Server** venster, selecteer de server-app die u wilt gebruiken en klik vervolgens op **OK**. Server-apps zijn de Azure AD web app registraties die de configuraties voor uw Azure-account, inclusief uw Tenant-ID, Client-ID en een geheime sleutel voor clients bevatten.
    Als u een beschikbare app niet hebt, gebruikt u een van de volgende:

    - **Maak**: Het maken van een web-app-registratie Azure AD op basis van informatie die u in de Configuration Manager-console invoer automatiseren. Geef een beschrijvende naam voor de app, de URL van de startpagina, App-ID-URI en de geheime sleutel geldigheidsperiode. De geheime sleutel geldigheidsduur is één jaar.
        
        Als u wilt doorgaan, moet iemand nu aanmelden met hun Azure AD-referenties voor het voltooien van de web-app gemaakt in Azure. Het account waarmee u zich aanmeldt bij Azure hoeft niet te worden van hetzelfde account dat wordt uitgevoerd in de Wizard Azure-Services. Na het aanmelden bij Azure, maakt Configuration Manager de web-app in Azure voor u, met inbegrip van de Client-ID en een geheime sleutel voor gebruik met de web-app. U kunt later uit de Azure-portal bekijken.

        Als u werkt met *maken* voor het configureren van een web-app, Configuration Manager voor u de web-app kunt maken in Azure AD.
    
    - **Importeren**: Geef informatie op over een Azure AD web-app te registreren die al zijn gemaakt in de **Azure-portal** metagegevens over deze inschrijving importeren naar Configuration Manager. Geef een beschrijvende naam voor de app en het tenantnetwerk en geef vervolgens de Tenant-ID, Client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u de gegevens controleren, klikt u op **OK** om door te gaan.
        > [!NOTE]
        > Voordat u **importeren** kan worden gebruikt, een Azure AD-app-registratie van het type *Web-app / API* moeten worden gemaakt in de [Azure-portal](https://portal.azure.com). Lezen Zie informatie over het maken van een app-registratie [uw toepassing registreren met uw Azure Active Directory-tenant](/azure/active-directory/active-directory-app-registration). Bij het configureren van de gereedheid van de Upgrade of Operations Management Suite u moet ook uw zojuist geregistreerde web-app zodat *Inzender* machtigingen voor de resourcegroep met de relevante OMS-werkruimte om Configuration Manager kunnen toegang krijgen tot deze werkruimte. Hiervoor hebt uitgevoerd, om te zoeken naar de naam van de registratie van de app in de **gebruikers toevoegen** blade bij het toewijzen van de machtiging. Dit is hetzelfde proces dat moet worden gevolgd wanneer [Configuration Manager met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) voor verbindingen met [logboekanalyse](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm). Deze machtigingen worden toegewezen voordat de app is geïmporteerd in Configuration Manager.


    **Native Client-app:**  Bladeren opent het venster Client-App.  
     In de **Clientapp** venster, selecteer de client-app die u wilt gebruiken en klik vervolgens op **OK**.

     Als u een beschikbare client-app niet hebt, gebruikt u een van de volgende:
     - **Maak**: Klik op om een nieuwe Client-app **maken**. Geef vervolgens een beschrijvende naam voor de app en de omleidings-URI.

         Als u wilt doorgaan, iemand moet nu aanmelden met hun Azure AD-referenties voor het voltooien van de web-app gemaakt in Azure. Het account waarmee u kunt aanmelden bij Azure hoeft niet te worden van hetzelfde account dat wordt uitgevoerd in de Wizard Azure-Services. Na het aanmelden bij Azure, Configuration Manager de native client-app in Azure AD voor u gemaakt, met inbegrip van de Client-ID en een geheime sleutel. Later kunt bekijken uit de [Azure-portal](https://portal.azure.com). 

     - **Importeren**: Een clientapp die al in uw Azure-abonnement bestaat gebruiken. Geef een beschrijvende naam voor de app en de Client-ID. Klik vervolgens op **OK** om door te gaan.

  <!--  MOVE THIS AND STEP 6 TO configure Azure AD User Discover  content
       [!TIP]  
     When you use Import, the account you use to run the wizard must have the *Read directory data* application permission in the Azure portal. This is required to set the correct permissions for the App. When you use Create, Configuration Manager creates the app with the correct permissions. However, you still must give consent to the application in the Azure portal.   -->


6.  (Alleen bij het configureren van de **Cloud management** service) In de **detectie** pagina van de wizard, klikt u op **inschakelen Azure Active Directory-Gebruikersdetectie**, en klik vervolgens op  **Instellingen**.
In de **Discovery-instellingen van Azure AD-gebruiker** dialoogvenster Configureer een planning voor wanneer detectie wordt uitgevoerd. U kunt ook detectie van verschillen die controleert op nieuwe of gewijzigd accounts in Azure AD inschakelen. Meer informatie over [Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

7.  Voltooi de wizard.

U hebt op dit punt wordt de configuratie van een Azure in Configuration Manager-service voltooid. Dit proces voor het configureren van andere Azure-services, kunt u herhalen.

## <a name="view-the-configuration-of-an-azure-service"></a>De configuratie van een Azure-service weergeven
U kunt de eigenschappen van een Azure-service die u hebt geconfigureerd voor gebruik weergeven.

Ga in de console naar **beheer** > **overzicht** > **Cloudservices** > **Azure Services**. Kies vervolgens de service die u wilt weergeven of bewerken en klik vervolgens op **eigenschappen**.
