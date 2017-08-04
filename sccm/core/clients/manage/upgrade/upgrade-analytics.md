---
title: Gereedheid voor upgrade | System Center Configuration Manager
description: "Gereedheid voor Upgrade worden geïntegreerd met Configuration Manager. Toegang tot upgradecompatibiliteit gegevens in de beheerconsole. Apparaten voor herstel of upgrade."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angerobe
ms.date: 7/31/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: b1f4cd4a6f19a02d2b2dc3f9a841aeeb2a1403dd
ms.contentlocale: nl-nl
ms.lasthandoff: 07/29/2017

---

# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Gereedheid voor Upgrade integreren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gereedheid voor upgrade (voorheen Upgrade Analytics) kunt u om te beoordelen en analyseren van de gereedheid van het apparaat met Windows 10. Gereedheid voor Upgrade worden geïntegreerd met Configuration Manager toegang tot gegevens van de client upgradecompatibiliteit in de beheerconsole van Configuration Manager. U zich aan doelapparaten voor herstel of upgrade van de lijst met apparaten.

Gereedheid voor upgrade is een oplossing in de Microsoft Operations Management Suite (OMS). U kunt meer lezen over gereedheid voor Upgrade in [aan de slag met de gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

## <a name="configure-clients"></a>Clients configureren

Er zijn diverse configuratiestappen die u uitvoeren moet om ervoor te zorgen dat uw clients gegevens voor gereedheid voor Upgrade leveren kunnen:

-  Telemetrie-clientinstellingen configureren zoals beschreven in [telemetrie van de configuratie van Windows in uw organisatie](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).
-  Installeren van de beschreven in kB de * de update voor compatibiliteit en het bijbehorende kB implementeren * sectie van [aan de slag met de gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

    > [!NOTE]
    > U kunt een script voor het automatiseren van veel van de client-instellingstaken downloaden. Zie de *het implementatiescript gereedheid voor Upgrade uitvoeren* sectie van [aan de slag met de gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness) voor meer informatie over het script.

## <a name="connect-to-upgrade-readiness"></a>Verbinding maken met de gereedheid voor Upgrade

### <a name="prerequisites"></a>Vereisten

Vanaf versie van de huidige vertakking 1706, wordt de Wizard Azure-Services gebruikt voor het vereenvoudigen van het proces van het configureren van Azure-services die u met Configuration Manager gebruikt. Om de wizard gebruikt, moet u een Azure-web-app configureren. Voor meer informatie ziet, [Wizard Azure-Services](/sccm/core/servers/deploy/configureazure-services-wizard).

### <a name="use-the-azure-wizard-to-create-the-connection"></a>Gebruik de Wizard Azure-verbinding

1.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, en klik vervolgens op **Azure Services**.
2.  Op de **Start** tabblad, in de **Azure Services** groep, klikt u op **Azure-Services configureren**.
3.  Typ een beschrijvende naam op de pagina Azure-Services. U kunt ook een beschrijving invoeren. Selecteer vervolgens **Upgrade gereedheid van de Connector** en klik op **volgende**.
4.  Geef uw Azure-omgeving op de pagina. Klik op **Bladeren** voor het instellen van een server-app.
5.  Klik op **importeren** verbinding maken met uw Web-app in Azure.
    -  Typ de **Azure AD-Tenant naam**.
    -  Typ de **Azure AD-Tenant-ID**.
    -  Typ de **toepassingsnaam**.
    -  Typ de **Client-ID**.
    -  Typ de **geheime sleutel**.
    -  Selecteer de datum voor de **geheime sleutel verstrijken** datum.
    -  Typ een URL voor de **toepassing-ID-URI**.
    -  Klik op **controleren**, en klik vervolgens op **OK**.

6.  Geef de verbinding met de gereedheid van de Upgrade op de pagina configuratie. Selecteer de volgende waarden:  
    -  Azure-abonnementen
    -  Azure-resourcegroep
    -  Windows Analytics-werkruimte
8.  Klik op **Volgende**. U kunt de verbinding in de pagina samenvatting bekijken. 

## <a name="complete-upgrade-readiness-tasks"></a>Taken uitvoeren gereedheid voor Upgrade  

Nadat u de verbinding hebt gemaakt, deze taken uitvoeren zoals is beschreven in [aan de slag met de gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).  

1. De service UpgradeReadiness toevoegen aan de OMS-werkruimte.  
2. Genereren van een commerciële-ID.  
3. Zich abonneren om de gereedheid voor Upgrade.   

## <a name="use-the-upgrade-readiness-deployment-script"></a>Gebruik het implementatiescript gereedheid voor Upgrade  

U kunt veel van de gereedheid van de Upgrade-taken automatiseren en oplossen van problemen met de Microsoft delen van gegevens **implementatiescript gereedheid voor Upgrade**.  
Het script voor gereedheid voor Upgrade-implementatie, gebeurt het volgende:  

- Hiermee stelt u commerciële ID-toets + CommercialDataOptIn + RequestAllAppraiserVersions sleutels.  
- Controleert of computers van gebruikers kunnen gegevens naar Microsoft verzenden.  
- Controleert of de computer opnieuw opstarten in behandeling heeft.   
- Verifieert dat de nieuwste versie van KB 10.0 x inpakken is geïnstalleerd (10.0.14913 of latere versies vereist).  
- Bij inschakeling Hiermee schakelt u uitgebreide modus voor het oplossen van problemen.  
- Initieert de verzameling van de telemetriegegevens die Microsoft nodig heeft om de gereedheid voor upgrade van uw organisatie vast te stellen.  
- Bij inschakeling voortgang wordt weergegeven van het script in een opdrachtvenster. Dit biedt inzicht in problemen (slagen of mislukken voor elke stap) en/of schrijft naar het logboekbestand.  

## <a name="to-run-the-upgrade-readiness-deployment-script"></a>Het implementatiescript gereedheid voor Upgrade uitvoeren:  

1. Download de [implementatiescript gereedheid voor Upgrade](https://go.microsoft.com/fwlink/?LinkID=822966&clcid=0x409) en UpgradeReadiness.zip extraheren. De bestanden in de **Diagnostics** map zijn alleen nodig als u van plan bent om uit te voeren van het script in de modus voor probleemoplossing.  
2. Deze parameters in RunConfig.bat bewerken:  
- Opslaglocatie voor de informatie in het foutenlogboek. Voorbeeld: % SystemDrive%\URDiagnostics. U kunt de informatie in het foutenlogboek opslaan op een externe bestandsshare of een lokale map. Als het script wordt geblokkeerd vanuit het maken van het logboekbestand voor het opgegeven pad, maakt de logboekbestanden in het station met de Windows-map.  
- Commerciële ID-sleutel.  
- Standaard wordt met het script logboekgegevens verzendt naar zowel de console en het logboekbestand. Als u wilt het standaardgedrag wijzigen, gebruikt u een van de volgende opties:  
    - logMode = 0 logboek alleen console  
    - logMode = 1 log-bestand en de console  
    - logMode = 2 log naar het bestand alleen  
    - Voor het oplossen van problemen ingesteld **isVerboseLogging** naar **$true** voor het genereren van logboekgegevens die u helpen kan bij het oplossen van problemen. Standaard **isVerboseLogging** is ingesteld op **$false**. Zorg ervoor dat de map diagnostische gegevens in dezelfde map als het script moet worden gebruikt in deze modus is geïnstalleerd.  
    - Waarschuw gebruikers als de computer opnieuw opstarten vereist. Dit is standaard uitgeschakeld.  

3. Nadat u de parameters in RunConfig.bat bewerken, moet u het script uitvoeren als beheerder.  


## <a name="view-microsoft-upgrade-readiness-properties-in-configuration-manager"></a>Eigenschappen van de gereedheid voor Upgrade van Microsoft weergeven in Configuration Manager  

1.  Navigeer in de Configuration Manager-console naar **Cloudservices**, en kies vervolgens **OMS Connector** openen de **OMS verbindingseigenschappen** pagina.  

2.  Er zijn twee tabbladen in deze pagina:
  * De **Azure Active Directory** tabblad toont uw **Tenant**, **Client-ID**, **Client geheime sleutelverloop**, en kunt u **controleren** uw **geheime sleutel van de Client** als deze is verlopen.
  * De **gereedheid voor Upgrade** tabblad toont uw **Azure-abonnement**, **Azure-resourcegroep**, en **Operations Management Suite-werkruimte**.

## <a name="view-and-use-the-upgrade-information"></a>Weergeven en gebruiken de informatie over de upgrade

Nadat u hebt gereedheid voor Upgrade geïntegreerd met Configuration Manager, kunt u de analyse van de gereedheid voor upgrade van uw clients weergeven en vervolgens actie ondernemen.

1. Kies in de Configuration Manager-console **bewaking** > **overzicht** > **gereedheid voor Upgrade**.
2. Controleer de gegevens, waaronder de status van de gereedheid voor upgrade en het percentage van de Windows-apparaten die telemetrie rapporteren.
3. U kunt het dashboard om gegevens voor apparaten in specifieke verzamelingen weer te filteren.
4. U kunt de apparaten in een bepaalde gereedheidsstatus weergeven en een dynamische verzameling voor apparaten maken zodat u kunt upgraden van deze apparaten als gereed of actie ondernemen om te zorgen dat ze naar een gereedheidsstatus.

## <a name="create-a-connection-to-upgrade-readiness-1702-and-earlier"></a>Maak een verbinding met gereedheid voor Upgrade (1702 en lager)

Voordat de 1706 vereist vertakking van Configuration Manager is een verbinding maken met gereedheid voor Upgrade de volgende stappen uit.

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

