---
title: 'Gegevens synchroniseren | Microsoft documenten | Microsoft Operations Management-pakket '
description: Synchronisatie van gegevens uit System Center Configuration Manager naar Microsoft Operations Management-pakket.
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
caps.latest.revision: 9
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 3acfaa2cf8c64ece5cef65b80372067336d6a815
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---


# <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite"></a>Synchronisatie van gegevens uit Configuration Manager naar de Microsoft Operations Management-pakket


*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Zoals uw verzamelingen van System Center Configuration Manager naar OMS logboek Analytics in Microsoft Azure kunt u de Connector voor Microsoft Operations Management Suite Kantoorbeheersysteem gegevens te synchroniseren. Op deze manier gegevens van de Configuration Manager-implementatie in OMS zichtbaar.
> [!TIP]
> De Connector OMS is een voorlopige versie-functie. Zie voor meer informatie, [gebruikmaken van de functies van updates pre-release](/sccm/core/servers/manage/pre-release-features).

Vanaf versie 1702, kunt u de connector OMS verbinding maken met een OMS werkruimte die zich op de overheid van de Microsoft Azure-cloud. Hiervoor moet u een configuratiebestand hebt gewijzigd voordat u de connector OMS installeert. Zie [OMS connector gebruiken met de overheid van de Azure-cloud](#fairfaxconfig) in dit onderwerp.

## <a name="prerequisites"></a>Vereisten
- Voordat u de connector OMS in Configuration Manager installeert, moet u Configuration Manager met machtigingen voor OMS opgeven. Specifiek, u moet de machtigingen *Inzender toegang* naar de Azure *resourcegroep* die de werkruimte OMS logboek Analytics bevat. De procedures om te doen zijn gedocumenteerd in het logboek Analytics-inhoud. Zie [bieden Configuration Manager met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) in de documentatie van OMS.

- De OMS-connector moet worden geïnstalleerd op de computer die als host fungeert voor een [serviceverbindingspunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point) die is opgeslagen in [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

  Als u OMS hebt verbonden met een zelfstandige primaire site en u van plan bent een centrale beheersite toevoegen aan uw omgeving, moet u de huidige verbinding verwijderen en vervolgens opnieuw configureren van de connector op de nieuwe centrale beheersite.

- U moet een Microsoft Monitoring Agent voor OMS geïnstalleerd op de service connection point samen met de connector OMS installeren.  De Agent en de OMS-connector moeten worden geconfigureerd voor het gebruik van dezelfde **OMS werkruimte**. Zie het installeren van de agent [Download en installeer de agent](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) in de documentatie van OMS.

- Nadat u de connector en de agent hebt geïnstalleerd, moet u OMS voor het gebruik van Configuration Manager-gegevens configureren.  Doet dit door in de Portal OMS u [importeren Configuration Manager-verzamelingen](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#import-collections).



## <a name="install-the-oms-connector"></a>De OMS-Connector installeren  
1. In de Configuration Manager-console, configureert u uw [hiërarchie pre-release functies gebruiken](/sccm/core/servers/manage/pre-release-features), en schakelt u het gebruik van de Connector OMS.  

2. Ga vervolgens naar de **beheer** > **Cloudservices** > **OMS Connector**. Klik in het lint op "Verbinding maken met Operations Management-pakket". Hiermee opent u de **verbinding met de bewerking Management Suite Wizard**. Selecteer **volgende**.  


3.    Op de **algemeen** pagina, bevestig dat u de volgende informatie hebt en selecteer **volgende**.  
  - Configuration Manager geregistreerd als een beheerprogramma "Web Application en/of Web API" en dat u hebt de [client-ID van deze registratie](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).  
  - Een client sleutel gemaakt voor de geregistreerde management tool in Azure Active Directory.  

  - Opgegeven de geregistreerde web-app in de Azure-beheerportal, met een machtiging voor toegang tot OMS, zoals beschreven in [bieden Configuration Manager met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms).  

4.    Op de **Azure Active Directory** pagina, configureert u de verbindingsinstellingen voor OMS doordat uw **Tenant**, **Client-ID**, en **Client geheime sleutel**, en selecteer vervolgens **volgende**.  

5.    Op de **OMS verbindingsconfiguratie** pagina, geeft u instellingen voor de verbinding door in te vullen uw **Azure-abonnement**, **Azure resourcegroep**, en **Operations Management Suite werkruimte**.  De werkruimte moet overeenkomen met de werkruimte die is geconfigureerd voor de Microsoft Management Agent die is geïnstalleerd op de service connection point.  

6.    Controleer de verbindingsinstellingen op de **samenvatting** pagina en selecteer vervolgens **volgende**. De **voortgang** ziet u de verbindingsstatus, vervolgens moet **voltooid**.

Nadat u de Configuration Manager aan OMS hebt gekoppeld, kunt u toevoegen of verwijderen van verzamelingen en de eigenschappen van de verbinding OMS bekijken.

## <a name="verify-the-oms-connector-properties"></a>Controleer of de eigenschappen van de connector OMS
1.    Ga in de Configuration Manager-console naar **beheer** > **Cloudservices**, en selecteer vervolgens **OMS Connector** openen de **OMS verbinding ** pagina**.
2.    In deze pagina zijn er twee tabbladen:
  - **Azure Active Directory:**   
    Dit tabblad bevat de **Tenant**, **Client-ID**, **Client geheime sleutel verlopen**, en kunt u controleren of de geheime sleutel van de client is verlopen.

  - **Verbindingseigenschappen OMS:**  
    Dit tabblad bevat de **Azure-abonnement**, **Azure resourcegroep**, **Operations Management Suite werkruimte**, en een lijst met **apparaatverzamelingen waarbij Operations Management Suite kunt krijgen tot gegevens voor**. Gebruik de **toevoegen** en **verwijderen** knoppen om te wijzigen welke verzamelingen zijn toegestaan.

## <a name="fairfaxconfig"></a> OMS connector gebruiken met de overheid van de Azure-cloud


1.  Op een computer waarop de Configuration Manager-console is geïnstalleerd, moet u het volgende configuratiebestand verwijzen naar de overheid van de cloud bewerken:  ***&lt;CM-installatiepad > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Bewerkingen:**

    Wijzig de waarde voor de naam van de instelling *FairFaxArmResourceID* gelijk aan "https://management.usgovcloudapi.net/"

   - **Oorspronkelijke:** 
      &lt;Instellingsnaam = "FairFaxArmResourceId" serializeAs = "Tekenreeks" >   
      &lt;waarde > &lt; /value >   
      &lt;/ instelling >

   - **Bewerkt:**     
      &lt;naam van de instelling = "FairFaxArmResourceId" serializeAs = "Tekenreeks" > &lt;waarde > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ instelling >

  Wijzig de waarde voor de naam van de instelling *FairFaxAuthorityResource* gelijk aan "https://login.microsoftonline.com/"

  - **Oorspronkelijke:** &lt;Instellingsnaam = "FairFaxAuthorityResource" serializeAs = "Tekenreeks" >   
    &lt;waarde > &lt; /value >

    - **Bewerkt:** &lt;Instellingsnaam = "FairFaxAuthorityResource" serializeAs = "Tekenreeks" >   
    &lt;waarde > https://login.microsoftonline.com/ &lt; /value >

2.    Nadat u het bestand met de twee wijzigingen opslaat, opnieuw opstarten van de Configuration Manager-console op dezelfde computer en vervolgens om deze console gebruiken om de OMS-connector te installeren. Gebruik de informatie in voor het installeren van de connector [synchroniseren van gegevens uit Configuration Manager naar de Microsoft Operations Management-pakket](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), en selecteer de **Operations Management Suite werkruimte** dat zich op de overheid van de Microsoft Azure-cloud.

3.    Nadat de OMS-connector is geïnstalleerd, is de verbinding met de overheid van de cloud beschikbaar wanneer u een console die verbinding met de site maakt.

