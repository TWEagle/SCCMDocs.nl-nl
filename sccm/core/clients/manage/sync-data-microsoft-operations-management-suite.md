---
title: 'Gegevens synchroniseren naar de Microsoft Operations Management Suite '
titleSuffix: Configuration Manager
description: Synchroniseren van gegevens uit System Center Configuration Manager met Microsoft Operations Management Suite.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: df57255108d0e5e8b8f5e4e8d73a392c4cf2faae
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
#  <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite"></a>Gegevens synchroniseren van Configuration Manager naar de Microsoft Operations Management Suite

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de **Wizard Azure-Services** Configureer de verbinding van Configuration Manager naar de cloudservice Operations Management Suite (OMS). Vanaf versie 1706, vervangt de wizard vorige werkstromen voor het configureren van deze verbinding. Zie voor eerdere versies [synchroniseren van gegevens uit Configuration Manager met Microsoft Operations Management Suite (1702 en eerder)](#Sync-data-from-Configuration-Manager-to-the-Microsoft-Operations-Management-Suite-(1702-and-earlier)).

-   De wizard wordt gebruikt voor het configureren van cloudservices voor Configuration Manager, zoals OMS, Microsoft Store voor bedrijven en Azure Active Directory (Azure AD).  

-   Configuration Manager maakt verbinding met OMS voor functies, zoals [logboekanalyse](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), of [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics).

## <a name="prerequisites-for-the-oms-connector"></a>Vereisten voor de OMS-Connector
Vereisten voor het configureren van een verbinding met OMS is ongewijzigd ten opzichte van de vereisten [beschreven voor de huidige vertakking versie 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#prerequisites). Deze informatie wordt hier herhaald:  

-   Voordat u de OMS-connector in Configuration Manager installeert, moet u de Configuration Manager met machtigingen opgeven met OMS. U moet in het bijzonder verlenen *Inzender toegang* naar de Azure *resourcegroep* die de logboekanalyse OMS-werkruimte bevat. De procedures om dit te doen, worden beschreven in de inhoud van logboekanalyse. Zie [Configuration Manager bieden met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) in de OMS-documentatie.

-   De OMS-connector moet worden geïnstalleerd op de computer die als host fungeert voor een [serviceaansluitpunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point) die zich in [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

-   Voor OMS op het service connection point samen met de OMS-connector is geïnstalleerd, moet u Microsoft Monitoring Agent installeren. De Agent en de OMS-connector moeten worden geconfigureerd voor het gebruik van dezelfde **OMS-werkruimte**. Zie het installeren van de agent [downloaden en installeren van de agent](/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) in de OMS-documentatie.
-   Nadat u de connector en de agent hebt geïnstalleerd, moet u OMS voor het gebruik van Configuration Manager-gegevens configureren. Om dit te doen in de OMS-Portal u [Import Configuration Manager-verzamelingen](/azure/log-analytics/log-analytics-sccm#import-collections).

## <a name="use-the-azure-services-wizard-to-configure-the-connection-to-oms"></a>Gebruik de Wizard Azure-Services de verbinding met OMS configureren

1.  Ga in de console naar **beheer** > **overzicht** > **Cloudservices** > **Azure Services**. Kies **Azure-Services configureren** van de **Start** tabblad van het lint op start de **Wizard Azure-Services**.

2.  Op de **Azure Services** pagina, selecteert u de bewerking Management Suite-cloudservice. Geef een beschrijvende naam voor de **Azure servicenaam** en een optionele beschrijving en klik vervolgens op **volgende**.

3.  Op de **App** pagina, geeft u uw Azure-omgeving (de technical preview ondersteunt alleen de openbare Cloud). Klik vervolgens op **Bladeren** om de Server App-venster te openen.

4.  Selecteer een web-app:

    -   **Importeren**: Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en de tenant. Geef de Tenant-ID, Client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u **controleren** de gegevens, klikt u op **OK** om door te gaan.   

    > [!NOTE]   
    > Wanneer u OMS met deze preview configureert, OMS biedt alleen ondersteuning voor de *importeren* functie voor een web-app. Maken van een nieuwe web-app wordt niet ondersteund. U kunt een bestaande app op dezelfde manier kan niet hergebruiken voor OMS.

5.  Als u bereikt de procedures geslaagd, klikt u vervolgens de informatie op de **OMS verbindingsconfiguratie** scherm automatisch wordt weergegeven op deze pagina. Informatie over de verbindingsinstellingen moet worden weergegeven voor uw **Azure-abonnement**, **Azure-resourcegroep**, en **Operations Management Suite-werkruimte**.

6.  De wizard maakt verbinding met de OMS-service met behulp van de informatie die u hebt ingevoerd. Selecteer de apparaatverzamelingen die u wilt synchroniseren met OMS en klik vervolgens op **toevoegen**.

7.  Controleer de verbindingsinstellingen op de **samenvatting** scherm en selecteer vervolgens **volgende**. De **voortgang** scherm toont de verbindingsstatus en vervolgens moet **Complete**.

8.  Nadat de wizard is voltooid, ziet u de Configuration Manager-console dat u hebt geconfigureerd **bewerking Management Suite** als een **Cloud Service Type**.

## <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite-1702-and-earlier"></a>Gegevens synchroniseren van Configuration Manager naar de Microsoft Operations Management Suite (1702 en lager)


*Van toepassing op: System Center Configuration Manager (1702 en eerdere versies)*

U kunt de Microsoft Operations Management Suite (OMS)-Connector gegevens synchroniseren, zoals uw verzamelingen van System Center Configuration Manager met OMS Log Analytics in Microsoft Azure. De connector worden gegevens uit de Configuration Manager-implementatie zichtbaar gemaakt in OMS.
> [!TIP]
> Met ingang van Configuration Manager 1802 kan is de OMS-Connector niet langer een functie van de voorlopige versie. Zie voor meer informatie, [functies van evaluatieversies van updates gebruiken](/sccm/core/servers/manage/pre-release-features).

Vanaf versie 1702, kunt u de OMS-connector verbinding maken met een OMS-werkruimte die zich op Microsoft Azure Government cloud. Hiervoor moet u een configuratiebestand aanpassen voordat u de OMS-connector installeert. Zie [de OMS-connector gebruiken met de cloud Azure Government](#fairfaxconfig) in dit artikel.

### <a name="prerequisites"></a>Vereisten
- Voordat u de OMS-connector in Configuration Manager installeert, moet u de Configuration Manager met machtigingen opgeven met OMS. U moet in het bijzonder verlenen *Inzender toegang* naar de Azure *resourcegroep* die de logboekanalyse OMS-werkruimte bevat. De procedures om dit te doen, worden beschreven in de inhoud van logboekanalyse. Zie [Configuration Manager bieden met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) in de OMS-documentatie.

- De OMS-connector moet worden geïnstalleerd op de computer die als host fungeert voor een [serviceaansluitpunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point) die zich in [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

  Als u verbinding hebt gemaakt dat een zelfstandige primaire site OMS en een centrale beheersite toevoegen aan uw omgeving wilt, moet u de huidige verbinding verwijderen en vervolgens opnieuw configureren van de connector op de nieuwe centrale beheersite.

- Voor OMS op het service connection point samen met de OMS-connector is geïnstalleerd, moet u Microsoft Monitoring Agent installeren.  De Agent en de OMS-connector moeten worden geconfigureerd voor het gebruik van dezelfde **OMS-werkruimte**. Zie het installeren van de agent [downloaden en installeren van de agent](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) in de OMS-documentatie.

- Nadat u de connector en de agent hebt geïnstalleerd, moet u OMS voor het gebruik van Configuration Manager-gegevens configureren.  Om dit te doen in de OMS-Portal u [Import Configuration Manager-verzamelingen](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#import-collections).



### <a name="install-the-oms-connector"></a>De OMS-Connector installeren  
1. In de Configuration Manager-console configureert uw [hiërarchie gebruik van functies van evaluatieversies](/sccm/core/servers/manage/pre-release-features), en schakelt u het gebruik van de OMS-Connector.  
0
2. Ga vervolgens naar de **beheer** > **Cloudservices** > **OMS Connector**. Klik in het lint op "Verbinding maken met Operations Management Suite." Hiermee opent u deze stap de **verbinding met de Wizard bewerking Management Suite**. Selecteer **volgende**.  


3.  Op de **algemene** pagina, bevestig dat u de volgende informatie hebt, en selecteer **volgende**.  
  - Configuration Manager is geregistreerd als beheerprogramma 'Webtoepassing en/of Web-API', en dat u hebt de [client-ID van deze registratie](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).  
  - Een clientsleutel voor het geregistreerde beheerprogramma in Azure Active Directory gemaakt.  

  - Opgegeven de geregistreerde web-app in de Azure-Portal met de machtiging voor toegang tot OMS, zoals beschreven in [Configuration Manager bieden met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms).  

4.  Op de **Azure Active Directory** pagina, de instellingen voor de verbinding met OMS configureren door te geven uw **Tenant**, **Client-ID**, en **geheime sleutel van de Client**, selecteer daarna **volgende**.  

5.  Op de **OMS verbindingsconfiguratie** pagina, geeft u de verbindingsinstellingen door in te vullen uw **Azure-abonnement**, **Azure-resourcegroep**, en **Operations Management Suite-werkruimte**.  De werkruimte moet overeenkomen met de werkruimte die is geconfigureerd voor de Microsoft Management Agent die is geïnstalleerd op het serviceverbindingspunt wordt gehost.  

6.  Controleer de verbindingsinstellingen op de **samenvatting** pagina en selecteer vervolgens **volgende**. De **voortgang** ziet u de status van de verbinding vervolgens moet **Complete**.

Nadat u hebt de Configuration Manager met OMS gekoppeld, kunt u toevoegen of verwijderen van verzamelingen en bekijk de eigenschappen van de OMS-verbinding.

### <a name="verify-the-oms-connector-properties"></a>Controleer de eigenschappen van de OMS-connector
1.  Ga in de Configuration Manager-console naar **beheer** > **Cloudservices**, en selecteer vervolgens **OMS Connector** openen de **OMS Verbindingspagina**.
2.  Er zijn twee tabbladen in deze pagina:
  - **Azure Active Directory:** 
  
     Op dit tabblad ziet uw **Tenant**, **Client-ID**, **Client geheime sleutelverloop**, en kunt u controleren of uw geheime sleutel van de client is verlopen.

  - **Eigenschappen van OMS-verbinding:**  

     Op dit tabblad ziet uw **Azure-abonnement**, **Azure-resourcegroep**, **Operations Management Suite-werkruimte**, en een lijst met **apparaatverzamelingen waarbij Operations Management Suite kunt krijgen tot gegevens voor**. Gebruik de **toevoegen** en **verwijderen** knoppen om te wijzigen welke verzamelingen zijn toegestaan.

### <a name="fairfaxconfig"> </a> Gebruik de OMS-connector met de cloud Azure Government


1.  Op elke computer die de Configuration Manager-console die is geïnstalleerd, het volgende configuratiebestand om te verwijzen naar de cloud van de overheid te bewerken:  ***&lt;CM-installatiepad > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Bewerkingen:**

    Wijzig de waarde voor de naam van de instelling *FairFaxArmResourceID* moet gelijk zijn aan 'https://management.usgovcloudapi.net/'

   - **Original:** &lt;setting name="FairFaxArmResourceId" serializeAs="String">   
      &lt;waarde > &lt; /value >   
      &lt;/setting>

   - **Bewerkt:**     
      &lt;setting name="FairFaxArmResourceId" serializeAs="String"> &lt;value>https://management.usgovcloudapi.net/&lt;/value>  
      &lt;/setting>

  Wijzig de waarde voor de naam van de instelling *FairFaxAuthorityResource* moet gelijk zijn aan 'https://login.microsoftonline.us/'

  - **Original:** &lt;setting name="FairFaxAuthorityResource" serializeAs="String">   
    &lt;waarde > &lt; /value >

    - **Bewerkt:** &lt;Instellingsnaam = serializeAs 'FairFaxAuthorityResource' = 'Tekenreeks' >   
    &lt;waarde >https://login.microsoftonline.us/ &lt; /value >

2.  Nadat u het bestand met de twee wijzigingen hebt opgeslagen, wordt de Configuration Manager-console op dezelfde computer opnieuw opstarten en vervolgens die console gebruiken om de OMS-connector te installeren. Gebruik de informatie in om de connector installeert, [synchroniseren van gegevens uit Configuration Manager met de Microsoft Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), en selecteer de **Operations Management Suite-werkruimte** dat zich op de Microsoft Azure Government cloud.

3.  Nadat de OMS-connector is geïnstalleerd, is de verbinding met de cloud van de overheid beschikbaar wanneer u een console die verbinding met de site maakt.
