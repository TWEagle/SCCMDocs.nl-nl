---
title: Azure-services configureren
titleSuffix: Configuration Manager
description: Verbinding maken met uw Configuration Manager-omgeving met Azure-services voor cloudbeheer, gereedheid voor Upgrade Microsoft Store voor bedrijven, en de Operations Management Suite.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a26a653e-17aa-43eb-ab36-0e36c7d29f49
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: b86c73f3f5662a00ca0b7f80b0c785c37aff0b1a
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-azure-services-for-use-with-configuration-manager"></a>Azure-services voor gebruik met Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de **Wizard Azure-Services** voor het vereenvoudigen van het proces van het configureren van de Azure-cloud-services die u met Configuration Manager gebruikt. Deze wizard biedt een algemene configuratie-ervaring met behulp van Azure Active Directory (Azure AD) web app registraties. Deze apps Geef details van abonnement en de configuratie en verifiëren van de communicatie met Azure AD. De app vervangt voeren dezelfde informatie telkens wanneer u een nieuwe Configuration Manager-component of de service met Azure instellen.



## <a name="available-services"></a>Beschikbare services

Configureer de volgende Azure-services met deze wizard:  

-   **Beheer cloud**: Deze service kunt u de site en de clients te verifiëren met behulp van Azure AD. Deze verificatie stelt andere scenario's, zoals:  

    - [Installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure)  

    - [Azure AD-Gebruikersdetectie configureren](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

    - Ondersteuning voor bepaalde [cloud management gatewayscenario's](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#scenarios)  

-   **OMS Connector**: [Verbinding maken met Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS). Gegevens synchroniseren, zoals verzamelingen met OMS-logboekanalyse.  

-   **Gereedheid van de Connector bijwerken**: Verbinding maken met Windows Analytics [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics). Weergave upgradecompatibiliteit clientgegevens.  

-   **Microsoft Store voor bedrijven**: Verbinding maken met de [Microsoft Store voor bedrijven](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business). Store-apps voor uw organisatie die u met Configuration Manager implementeren kunt worden opgehaald.  

### <a name="service-details"></a>Servicedetails

De volgende tabel bevat details over elk van de services.  

- **Tenants**: Het aantal service-exemplaren die u kunt configureren. Elk exemplaar moet een afzonderlijke Azure-tenant.  

- **Clouds**: Alle services ondersteunen de globale Azure-cloud, maar niet alle services ondersteuning persoonlijke clouds, zoals het Azure US Government-cloud.  

- **Web-app**: Hiermee wordt aangegeven of de service gebruikmaakt van een Azure AD-app van het type *Web-app / API*, ook wel de app in Configuration Manager op een server.  

- **Systeemeigen app**: Hiermee wordt aangegeven of de service gebruikmaakt van een Azure AD-app van het type *systeemeigen*, ook wel een client-app in Configuration Manager.  

- **Acties**: U kunt Hiermee wordt aangegeven of importeren of maken van deze apps in de Wizard Configuration Manager Azure-Services.  


|Service  |Tenants  |Clouds  |Web-app  |Systeemeigen app  |acties  |
|---------|---------|---------|---------|---------|---------|
|Cloudbeheer met</br>Azure AD-Gebruikersdetectie | Meerdere | openbare | ![Ondersteund](media/green_check.png) | ![Ondersteund](media/green_check.png) | Importeren, maken |
|OMS-Connector | een | Public, Private | ![Ondersteund](media/green_check.png) | ![Niet ondersteund](media/Red_X.png) | Importeren |
|Gereedheid voor upgrade | een | openbare | ![Ondersteund](media/green_check.png) | ![Niet ondersteund](media/Red_X.png) | Importeren |
|Microsoft Store voor</br>Bedrijfs- en Education | een | openbare | ![Ondersteund](media/green_check.png) | ![Niet ondersteund](media/Red_X.png) | Importeren, maken |


### <a name="about-azure-ad-apps"></a>Over Azure AD-apps

Andere Azure-services moeten verschillende configuraties, die u in de Azure-portal aanbrengt. Bovendien de apps voor elke service kunnen afzonderlijke machtigingen nodig voor Azure-resources.  

U kunt een enkele app gebruiken voor meerdere services. Er is slechts één object om te beheren in Configuration Manager en Azure AD. Wanneer de beveiligingssleutel in de app is verlopen, moet u alleen één sleutel vernieuwen.

De veiligste configuratie maakt gebruik van afzonderlijke apps voor elke service. Een app voor een service kunnen extra machtigingen voor een andere service niet vereist. Met behulp van één app voor verschillende services krijgt u de app met meer machtigingen dan anders is vereist. 

Wanneer u extra Azure-services in de wizard maakt, wordt Configuration Manager is ontworpen om informatie die wordt gedeeld tussen services opnieuw te gebruiken. Dit gedrag voorkomt u dat voor het invoeren van dezelfde gegevens meerdere keren. 

Zie voor meer informatie over de vereiste app-machtigingen en configuraties voor elke service, het relevante Configuration Manager-artikel in [beschikbare services](#available-services). 

Beginnen met de volgende artikelen voor meer informatie over apps van Azure:
- [Verificatie en autorisatie in Azure App Service](/azure/app-service/app-service-authentication-overview)
- [Overzicht van Web Apps](/azure/app-service-web/app-service-web-overview)
- [Basisbeginselen van het registreren van een toepassing in Azure AD](/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad)  
- [Uw toepassing registreren met uw Azure Active Directory-tenant](/azure/active-directory/active-directory-app-registration)



## <a name="before-you-begin"></a>Voordat u begint

Nadat u hebt besloten dat de service waarmee u verbinding wilt maken, Zie de tabel in [servicedetails](#service-details). Deze tabel bevat informatie die u nodig hebt om de Service Azure Wizard te voltooien. Een bespreking van tevoren met uw Azure AD-beheerder hebben. Als u handmatig de apps van tevoren in de Azure portal maken en vervolgens de app-gegevens in Configuration Manager importeren bepalen. Of Configuration Manager gebruiken voor de apps rechtstreeks in Azure AD maken. Voor het verzamelen van gegevens die nodig zijn uit Azure AD, lees de informatie in de andere secties van dit artikel.

Sommige services moet de Azure AD-apps specifieke machtigingen hebben. Controleer de gegevens voor elke service om te bepalen van de vereiste machtigingen. Bijvoorbeeld, voordat u een web-app importeren kunt, een Azure-beheerder moet deze eerst maken in de [Azure-portal](https://portal.azure.com). Wanneer de gereedheid van de Upgrade of de OMS-Connector te configureren, moet u uw zojuist geregistreerde web-app *Inzender* toegang tot de resourcegroep met de relevante OMS-werkruimte. Deze machtiging kan Configuration Manager voor toegang tot deze werkruimte. Zoeken naar de naam van de registratie van de app in de **gebruikers toevoegen** blade bij het toewijzen van de machtiging. Dit proces is hetzelfde als wanneer [Configuration Manager met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms). Een Azure-beheerder moet deze machtigingen toewijzen voordat u de app in Configuration Manager importeren.



## <a name="start-the-azure-services-wizard"></a>Start de wizard Azure-Services

1.  Ga in de Configuration Manager-console naar de **beheer** werkruimte Vouw **Cloudservices**, en selecteer de **Azure Services** knooppunt.  

2.  Op de **Start** tabblad van het lint in de **Azure Services** groep, klikt u op **Azure-Services configureren**.  

3.  Op de **Azure Services** pagina van de Wizard Azure-Services:  

    1. Geef een **naam** voor het object in Configuration Manager.  

    2. Geef een optioneel **beschrijving** voor hulp bij het identificeren van de service.  

    3. Selecteer de Azure-service die u wilt verbinden met Configuration Manager.  

4. Klik op **volgende** om door te gaan naar de [Azure app-eigenschappen](#azure-app-properties) pagina van de Wizard Azure-Services.  



## <a name="azure-app-properties"></a>Azure app-eigenschappen

Op de **App** pagina van de Wizard Azure-Services selecteert u eerst de **Azure-omgeving** uit de lijst. Zie de tabel in [servicedetails](#service-details) voor welke omgeving is momenteel beschikbaar voor de service.

De rest van de pagina is afhankelijk van de specifieke service. Zie de tabel in [servicedetails](#service-details) voor welk type app maakt gebruik van de service en welke actie u kunt gebruiken. 
- Als de app zowel import ondersteunt en acties maakt, klikt u op **Bladeren**. Hiermee opent u deze actie de [Server app-dialoogvenster](#server-app-dialog) of de [Clientapp dialoogvenster](#client-app-dialog).
- Als de app biedt alleen ondersteuning voor de actie importeren, klikt u op **importeren**. Hiermee opent u deze actie de [importeren Apps dialoogvenster (server)](#import-apps-dialog-server) of de [importeren Apps dialoogvenster (client)](#import-apps-dialog-client).

Nadat u de apps op deze pagina opgeeft, klikt u op **volgende** om door te gaan naar de [configuratie of detectie](#configuration-or-discovery) pagina van de Wizard Azure-Services.

### <a name="web-app"></a>Web-app

Deze app is het Azure AD-type *Web-app / API*, ook wel de app in Configuration Manager op een server.

#### <a name="server-app-dialog"></a>Dialoogvenster voor server-app

Wanneer u klikt op **Bladeren** voor de **Web-app** op de pagina van de Wizard Azure-Services, wordt de Server app-dialoogvenster geopend. Een lijst waarin de volgende eigenschappen van alle bestaande web-apps worden weergegeven:
- Beschrijvende naam van de tenant
- Beschrijvende naam van App
- Servicetype

Er zijn drie acties die u in het dialoogvenster van de app Server kunt uitvoeren:
- Als u wilt gebruiken op een bestaande web-app, selecteert u deze uit de lijst. 
- Klik op **importeren** openen de [importeren apps dialoogvenster](#import-apps-dialog-server).
- Klik op **maken** openen de [servertoepassing maken dialoogvenster](#create-server-application-dialog).

Nadat u selecteert, importeren of een web-app maken, klikt u op **OK** om de Server app-dialoogvenster te sluiten. Deze actie wordt de [op de pagina App](#azure-app-properties) van de Wizard Azure-Services.

#### <a name="import-apps-dialog-server"></a>Dialoogvenster van de apps importeren (server)

Wanneer u klikt op **importeren** vanuit het dialoogvenster van de app Server of de App-pagina van de Wizard Azure-Services, wordt het dialoogvenster importeren apps geopend. Deze pagina kunt u informatie over een Azure AD-web-app die al is gemaakt in de Azure portal invoeren. Deze importeert metagegevens over die WebApp in Configuration Manager. Geef de volgende informatie:
- **De naam van de Azure AD-Tenant**
- **Azure AD-Tenant-ID**
- **Toepassingsnaam**: Een beschrijvende naam voor de app.
- **Client-ID**
- **De geheime sleutel**
- **Geheime sleutel verstrijken**: Selecteer in de toekomst in de kalender. 
- **App ID URI**: Deze waarde moet uniek zijn in uw Azure AD-tenant. Het is in het toegangstoken dat wordt gebruikt door de Configuration Manager-client voor het aanvragen van toegang tot de service. Deze waarde is standaard https://ConfigMgrService.  

Klik na het invoeren van de gegevens op **controleren**. Klik vervolgens op **OK** om de apps invoer dialoogvenster te sluiten. Resultaat van deze bewerking op de [op de pagina App](#azure-app-properties) van de Wizard Azure-Services of de [Server app-dialoogvenster](#server-app-dialog).

#### <a name="create-server-application-dialog"></a>Dialoogvenster van de Server-toepassing maken

Wanneer u klikt op **maken** van de Server app-dialoogvenster wordt het dialoogvenster servertoepassing maken geopend. Deze pagina automatiseert het maken van een web-app in Azure AD. Geef de volgende informatie:
- **Toepassingsnaam**: Een beschrijvende naam voor de app.
- **URL van de startpagina**: Deze waarde wordt niet gebruikt door Configuration Manager, maar vereist door Azure AD. Deze waarde is standaard https://ConfigMgrService.  
- **App ID URI**: Deze waarde moet uniek zijn in uw Azure AD-tenant. Het is in het toegangstoken dat wordt gebruikt door de Configuration Manager-client voor het aanvragen van toegang tot de service. Deze waarde is standaard https://ConfigMgrService.  
- **Geheime sleutel geldigheidsperiode**: klik op de vervolgkeuzelijst en selecteer een **1 jaar** of **2 jaar**. Een jaar is de standaardwaarde.

Klik op **aanmelden** voor verificatie op Azure als gebruiker met beheerdersrechten. Deze referenties worden niet door Configuration Manager opgeslagen. Deze persona machtigingen in Configuration Manager niet nodig en hoeven niet te worden van hetzelfde account dat wordt uitgevoerd in de Wizard Azure-Services. Na verificatie is gelukt naar Azure, ziet u de pagina de **de naam van de Azure AD-Tenant** ter referentie. 

Klik op **OK** naar de web-app in Azure AD maken en sluit het dialoogvenster Server-toepassing maken. Deze actie wordt de [Server app-dialoogvenster](#server-app-dialog).


### <a name="native-client-app"></a>Native Client-app
    
Deze app is het Azure AD-type *systeemeigen*, ook wel een client-app in Configuration Manager.

#### <a name="client-app-dialog"></a>Het dialoogvenster App-client

Wanneer u klikt op **Bladeren** voor de **Native Client-app** op de pagina van de Wizard Azure-Services, wordt de Client-App-dialoogvenster geopend. Een lijst waarin de volgende eigenschappen van alle bestaande systeemeigen apps worden weergegeven:
- Beschrijvende naam van de tenant
- Beschrijvende naam van App
- Servicetype

Er zijn drie acties die u in het dialoogvenster voor Client-App kunt uitvoeren:
- Als u wilt gebruiken op een bestaande systeemeigen app, selecteert u deze uit de lijst. 
- Klik op **importeren** openen de [importeren apps dialoogvenster](#import-apps-dialog-client).
- Klik op **maken** openen de [Client-toepassing maken dialoogvenster](#create-client-application-dialog).

Nadat u selecteert, importeren of een systeemeigen app maken, klikt u op **OK** om het dialoogvenster van de Client-App te sluiten. Deze actie wordt de [op de pagina App](#azure-app-properties) van de Wizard Azure-Services.

#### <a name="import-apps-dialog-client"></a>Dialoogvenster van de apps importeren (client)

Wanneer u klikt op **importeren** in het dialoogvenster Client-App wordt het dialoogvenster importeren apps geopend. Deze pagina kunt u informatie over een systeemeigen Azure AD-app die al is gemaakt in de Azure portal invoeren. Metagegevens over die systeemeigen app worden geïmporteerd in Configuration Manager. Geef de volgende informatie:
- **Toepassingsnaam**: Een beschrijvende naam voor de app.
- **Client-ID** 

Klik na het invoeren van de gegevens op **controleren**. Klik vervolgens op **OK** om de apps invoer dialoogvenster te sluiten. Deze actie wordt de [Clientapp dialoogvenster](#client-app-dialog).

#### <a name="create-client-application-dialog"></a>Dialoogvenster van de Client-toepassing maken

Wanneer u klikt op **maken** in het dialoogvenster Client-App wordt het dialoogvenster clienttoepassing maken geopend. Deze pagina automatiseert het maken van een systeemeigen app in Azure AD. Geef de volgende informatie:
- **Toepassingsnaam**: Een beschrijvende naam voor de app.
- **Antwoord-URL**: Deze waarde wordt niet gebruikt door Configuration Manager, maar vereist door Azure AD. Deze waarde is standaard https://ConfigMgrService. 

Klik op **aanmelden** voor verificatie op Azure als gebruiker met beheerdersrechten. Deze referenties worden niet door Configuration Manager opgeslagen. Deze persona machtigingen in Configuration Manager niet nodig en hoeven niet te worden van hetzelfde account dat wordt uitgevoerd in de Wizard Azure-Services. Na verificatie is gelukt naar Azure, ziet u de pagina de **de naam van de Azure AD-Tenant** ter referentie. 

Klik op **OK** de systeemeigen app maken in Azure AD en sluit het dialoogvenster Client-toepassing maken. Deze actie wordt de [Clientapp dialoogvenster](#client-app-dialog).


## <a name="configuration-or-discovery"></a>Configuratie- of detectie

Na het opgeven van de web- en systeemeigen apps op de pagina Apps, de Wizard Azure-Services wordt voortgezet tot een **configuratie** of **detectie** pagina, afhankelijk van de service waarmee u verbinding maakt. De details van deze pagina verschillen van services. Zie een van de volgende artikelen voor meer informatie:  

-   **Beheer cloud** service, **detectie** pagina: [Azure AD-Gebruikersdetectie configureren](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

-   **OMS Connector** service, **configuratie** pagina: [De verbinding met OMS configureren](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#use-the-azure-services-wizard-to-configure-the-connection-to-oms)  

-   **Gereedheid van de Connector bijwerken** service, **configuratie** pagina: [Gebruik de Wizard Azure-verbinding](/sccm/core/clients/manage/upgrade/upgrade-analytics#use-the-azure-wizard-to-create-the-connection)  

-   **Microsoft Store voor bedrijven** service, **configuraties** pagina: [Microsoft Store voor bedrijven-synchronisatie instellen](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#for-configuration-manager-version-1706-and-later)  


Voltooi ten slotte de Wizard Azure-Services via de pagina Samenvatting, de voortgang en de voltooiing. U kunt de configuratie van een Azure-service in Configuration Manager hebt voltooid. Herhaal dit proces voor het configureren van andere Azure-services.


## <a name="view-the-configuration-of-an-azure-service"></a>De configuratie van een Azure-service weergeven
U kunt de eigenschappen van een Azure-service die u hebt geconfigureerd voor gebruik weergeven. Ga in de Configuration Manager-console naar de **beheer** werkruimte Vouw **Cloudservices**, en selecteer **Azure Services**. Selecteer de service die u wilt weergeven of bewerken en klik vervolgens op **eigenschappen**.

Als u een service selecteren en klik vervolgens op **verwijderen** in het lint deze actie wordt de verbinding in Configuration Manager verwijderd. Verwijder de app niet wordt deze in Azure AD. Vraag de beheerder Azure te verwijderen van de app wanneer deze niet langer nodig is. Of Voer de Wizard Azure-Service voor het importeren van de app.<!--483440-->


## <a name="cloud-management-data-flow"></a>Gegevensstroom van cloud-management

Het volgende diagram wordt een conceptuele gegevensstroom voor de interactie tussen Configuration Manager, Azure AD en cloudservices verbonden. In dit specifieke voorbeeld wordt de **Cloudbeheer** service, waaronder Windows 10-client en server en client-apps. De stromen voor andere services die zijn vergelijkbaar.

![Stroomdiagram van gegevens voor Configuration Manager met Azure AD en het beheer van de Cloud](media/aad-auth.png)

1.  De beheerder van Configuration Manager worden geïmporteerd of maakt de client en server-apps in Azure AD.  

2.  Detectiemethode van Configuration Manager Azure AD-gebruiker wordt uitgevoerd. De site maakt gebruik van de Azure AD server app-token naar Microsoft Graph query voor gebruikersobjecten.  

3.  De site slaat gegevens over de gebruikersobjecten. Zie voor meer informatie [Azure AD-Gebruikersdetectie](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).  

4.  Configuration Manager-client vraagt de token van de Azure AD-gebruiker. De client maakt de claim met de toepassings-ID van de Azure AD-client-app en de server-app als de doelgroep. Zie voor meer informatie [Claims in Azure AD-beveiligingstokens](/azure/active-directory/develop/active-directory-authentication-scenarios#claims-in-azure-ad-security-tokens).  

5.  De client wordt geverifieerd met de site in de vorm van de Azure AD-token voor de cloud-management-gateway en/of lokale HTTPS-beheerpunt.  


