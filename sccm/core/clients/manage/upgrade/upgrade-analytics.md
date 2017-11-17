---
title: Gereedheid voor upgrade
titleSuffix: Configuration Manager
description: "Gereedheid voor Upgrade worden geïntegreerd met Configuration Manager. Toegang tot upgradecompatibiliteit gegevens in de beheerconsole. Apparaten voor herstel of upgrade."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angerobe
ms.date: 7/31/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.openlocfilehash: df2950551e527788aeb01d57cdbf01ad19817ccd
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2017
---
# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Gereedheid voor Upgrade integreren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gereedheid voor upgrade (voorheen Upgrade Analytics) maakt deel uit van [Windows Analytics](https://www.microsoft.com/WindowsForBusiness/windows-analytics) waarmee u om te beoordelen en analyseren van de gereedheid van apparaten in uw omgeving voor een upgrade naar Windows 10. U kunt de specifieke versie kunt configureren. Gereedheid voor upgrade kan worden geïntegreerd met Configuration Manager toegang tot gegevens van de client upgradecompatibiliteit in de beheerconsole van Configuration Manager. U kunt doelapparaten voor een upgrade of herstel met behulp van dynamische verzamelingen die zijn gemaakt op basis van deze gegevens.

Gereedheid voor upgrade is een oplossing die wordt uitgevoerd op [Operations Management Suite (OMS)](/azure/operations-management-suite/operations-management-suite-overview). Meer informatie over de gereedheid van de Upgrade in [beheren wordt bijgewerkt met de gereedheid voor Upgrade](/windows/deployment/upgrade/manage-windows-upgrades-with-upgrade-readiness).

## <a name="configure-clients"></a>Clients configureren

Gereedheid voor upgrade, zoals alle Windows Analytics-oplossingen, afhankelijk van telemetriegegevens van Windows. Gereedheid voor Upgrade voldoende telemetriegegevens ontvangt worden de volgende vereisten voldaan:

- Alle clients moeten worden geconfigureerd met een **commerciële ID sleutel**. 
- Windows 10-clients moeten telemetrie die zijn geconfigureerd voor het rapporteren van ten minste basic niveau telemetrie hebben.
-  Clients met oudere versies van Windows moeten hebben geïnstalleerd van specifieke kB zoals beschreven in [aan de slag met de gereedheid voor Upgrade](/windows/deployment/upgrade/upgrade-readiness-get-started#deploy-the-compatibility-update-and-related-kbs). Telemetrie is ingeschakeld in het moet ook over **clientinstellingen**.

Commerciële ID-sleutel en de telemetrie van Windows kunnen worden geconfigureerd in **clientinstellingen**. Zie voor meer informatie, [Windows Analytics voor gebruik met Configuration Manager](../monitor-windows-analytics.md).

>[!NOTE]
>Als u problemen met de gereedheid voor Upgrade ontvangt geen telemetriegegevens van apparaten in uw omgeving ondervindt zoals verwacht wordt dat sommige van deze problemen kunnen worden opgelost met behulp van de [implementatiescript gereedheid voor Upgrade](/windows/deployment/upgrade/upgrade-readiness-deployment-script). Echter, in de meeste omgevingen implementeert de juiste KB configureren commerciële id-sleutel en telemetrie in **clientinstellingen** moet voldoende.

## <a name="connect-configuration-manager-to-upgrade-readiness"></a>Verbinding maken met Configuration Manager voor gereedheid voor Upgrade

Vanaf versie van de huidige vertakking 1706, de [wizard Azure-services](../../../servers/deploy/configure/azure-services-wizard.md) wordt gebruikt voor het vereenvoudigen van het proces van het configureren van Azure services die u met Configuration Manager gebruikt. Configuration Manager een verbinding maakt met een Azure AD-app-registratie van het type van Upgrade gereedheid *Web-app / API* moeten worden gemaakt in de [Azure-portal](https://portal.azure.com). Lezen Zie informatie over het maken van een app-registratie [uw toepassing registreren met uw Azure Active Directory-tenant](/azure/active-directory/active-directory-app-registration). In de **Azure-portal**, moet u ook uw zojuist geregistreerde web-app zodat *Inzender* machtigingen voor de resourcegroep met de OMS-werkruimte die als host fungeert voor uw gegevens gereedheid voor Upgrade. De **wizard Azure-services** deze registratie van de app wordt gebruikt om toe te staan van Configuration Manager voor veilige communicatie met Azure AD en uw infrastructuur verbinden met uw gegevens gereedheid voor Upgrade.

>[!IMPORTANT]
>*Inzender* moeten machtigingen worden toegekend aan de app zelf in plaats van de identiteit van een Azure AD-gebruiker. Dit is omdat deze de geregistreerde app en niet in het geval van een Azure AD-gebruiker die toegang heeft tot de gegevens namens uw Configuration Manager-infrastructuur. Hiervoor hebt uitgevoerd, om te zoeken naar de naam van de registratie van de app in de **gebruikers toevoegen** blade bij het toewijzen van de machtiging. Dit wordt hetzelfde proces dat als moet worden gevolgd [Configuration Manager met machtigingen voor OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) voor verbindingen met [logboekanalyse](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm). Deze stappen moeten worden voltooid voordat de app-registratie is geïmporteerd in Configuration Manager met de *wizard Azure-services*.

### <a name="use-the-azure-wizard-to-create-the-connection"></a>Gebruik de Wizard Azure-verbinding

Volg de instructies in [configureren van Azure services voor gebruik met Configuration Manager](../../../servers/deploy/configure/azure-services-wizard.md) voor het maken van een verbinding met de gereedheid van de Upgrade door het importeren van de registratie van de web-app die eerder is gemaakt. 

Op de *configuratie* pagina de volgende waarden zijn al ingevuld als de web-app importeren geslaagd is en de juiste machtigingen zijn toegewezen de **Azure-portal**. 
-  Azure-abonnementen
-  Azure-resourcegroep
-  Windows Analytics-werkruimte

Meer dan één resourcegroep of werkruimte wordt alleen beschikbaar zijn als de geregistreerde Azure AD web-app heeft *Inzender* machtigingen op meer dan één resourcegroep of als de geselecteerde resourcegroep meer dan een OMS-werkruimte bevat.
 
## <a name="view-and-use-upgrade-readiness-information-in-configuration-manager"></a>Weergeven en gebruiken van gegevens van de gereedheid van de Upgrade in Configuration Manager

Nadat u hebt gereedheid voor Upgrade geïntegreerd met Configuration Manager, kunt u de analyse van de gereedheid voor upgrade van uw clients weergeven.

1. Kies in de Configuration Manager-console **bewaking** > **overzicht** > **gereedheid voor Upgrade**.
2. Controleer de gegevens, waaronder de status van de gereedheid voor upgrade en het percentage van de Windows-apparaten die telemetrie rapporteren.
3. U kunt het dashboard om gegevens voor apparaten in specifieke verzamelingen weer te filteren.
4. U kunt de apparaten in een bepaalde gereedheidsstatus weergeven en een dynamische verzameling voor apparaten maken zodat u kunt upgraden van deze apparaten als gereed of maatregelen apparaten die worden geblokkeerd van upgrade.

## <a name="using-the-upgrade-readiness-connector-version-1702-and-earlier"></a>Met behulp van de Upgrade gereedheid van de Connector (versie 1702 en lager)

In Configuration Manager versie 1702 of ouder, zijn een andere reeks stappen en vereisten nodig zijn om een verbinding met de gereedheid van de Upgrade.

### <a name="prerequisites"></a>Vereisten

- Om de verbinding toevoegen, moet eerst uw Configuration Manager-omgeving configureren een [serviceaansluitpunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point) in een [onlinemodus](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/). Wanneer u de verbinding aan uw omgeving toevoegen, wordt het Microsoft Monitoring Agent ook installeren op de computer waarop deze sitesysteemrol.
- Configuration Manager registreren als beheerprogramma 'Webtoepassing en/of Web-API' en krijgt de [client-ID van deze registratie](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
- Maak een clientsleutel voor het geregistreerde beheerprogramma in Azure Active Directory.
- In de Azure-portal bieden u de geregistreerde web-app met de machtiging voor toegang tot OMS, zoals beschreven in [Configuration Manager bieden met machtigingen voor OMS](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

    > [!IMPORTANT]
    > Bij het configureren van machtigingen voor toegang tot OMS, moet u kiezen de **Inzender** rol, en deze machtigingen toewijzen aan de resourcegroep van de geregistreerde app.

### <a name="create-the-connection"></a>De verbinding maken

1.  Kies in de Configuration Manager-console **beheer** > **Cloudservices** > **Upgrade gereedheid van de Connector** > **verbinding maken met Analytics Upgrade** starten de **Wizard upgradepakket toevoegen Analytics verbinding**.
3.  Op de **Azure Active Directory** scherm, bieden **Tenant**, **Client-ID**, en **geheime sleutel van de Client**, selecteer daarna **volgende**.
4.  Op de **gereedheid voor Upgrade** scherm, geeft u de verbindingsinstellingen door in te vullen uw **Azure-abonnement**, **Azure-resourcegroep**, en **Operations Management Suite-werkruimte**.
5.  Controleer de verbindingsinstellingen op de **samenvatting** scherm en selecteer vervolgens **volgende**.

    > [!NOTE]
    > U moet gereedheid voor Upgrade verbinden met de hoogste site in uw hiërarchie. Als u verbinding maken met gereedheid voor Upgrade van een zelfstandige primaire site en vervolgens een centrale beheersite toe te aan uw omgeving voegen, moet u deze verwijderen en opnieuw maken van de OMS-verbinding in de nieuwe hiërarchie.
