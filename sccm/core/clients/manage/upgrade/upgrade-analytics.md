---
title: Gereedheid voor upgrade | System Center Configuration Manager
description: Gereedheid voor Upgrade met Configuration Manager integreren. Toegang tot upgradecompatibiliteit gegevens in de beheerconsole. Apparaten voor herstel of upgrade.
keywords: 
author: brenduns
ms.author: brenduns
manager: angerobe
ms.date: 3/1/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcbcd57b95f304f007e92ebe2b9aeefb4b579662
ms.openlocfilehash: 986d0446209f6e7eac1b681066d1b2e2305e1975
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Gereedheid voor Upgrade integreren met System Center Configuration Manager
Gereedheid voor upgrade (voorheen Upgrade Analytics) kunt u om te beoordelen en analyseren apparaat gereedheid en compatibiliteit met Windows 10 zodat eenvoudiger en vloeiende upgrades. Gereedheid voor Upgrade worden geïntegreerd met Configuration Manager client upgradecompatibiliteit gegevens in de beheerconsole van Configuration Manager te openen. Vervolgens moet u kunt aan doelapparaten voor herstel of upgrade van de lijst met apparaten.

Gereedheid voor upgrade is een oplossing in de Microsoft Operations Management Suite Kantoorbeheersysteem. Meer informatie over de gereedheid van de Upgrade in [aan de slag met gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

## <a name="configure-clients"></a>Clients configureren

Er zijn diverse configuratiestappen die u uitvoeren moet om ervoor te zorgen dat uw clients gegevens aan gereedheid voor Upgrade leveren kunnen:

-  Client telemetrie-instellingen te configureren zoals beschreven in [telemetrische informatie bij Windows configureren in uw organisatie](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).
-  Installeren van de KB beschreven in de * implementatie van de update voor compatibiliteit en verwante kB * sectie van [aan de slag met gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

    > [!NOTE]
    > U kunt een script voor het automatiseren van veel van de client instellingstaken downloaden. Zie de *uitvoeren van de gereedheid voor Upgrade implementatiescript* sectie [aan de slag met gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness) voor informatie over het script.

## <a name="create-a-connection-to-upgrade-readiness"></a>Maak een verbinding met de gereedheid voor Upgrade

### <a name="prerequisites"></a>Vereisten

- Als u wilt toevoegen de verbinding, moet eerst uw Configuration Manager-omgeving configureren een [serviceverbindingspunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point) in een [onlinemodus](https://azure.microsoft.com/en-us/documentation/articles/resource-group-create-service-principal-portal/). Wanneer u de verbinding aan uw omgeving toevoegen, wordt het Microsoft Monitoring Agent ook installeren op de machine wordt uitgevoerd van deze sitesysteemrol.
- Configuration Manager registreren als een beheerprogramma "Web Application en/of Web API" en krijgt de [client-ID van deze registratie](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
- Maak een client-sleutel voor het geregistreerde beheerprogramma in Azure Active Directory.
- In de Azure-beheerportal opgeven die de geregistreerde web-app met machtigingen voor toegang tot OMS, zoals beschreven in [bieden Configuration Manager met machtigingen voor OMS](https://azure.microsoft.com/en-us/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

    > [!IMPORTANT]
    > Bij het configureren van machtigingen voor toegang tot OMS moet u ervoor kiezen de **Inzender** rol, en deze machtigingen toewijzen aan de resourcegroep van de geregistreerde app.

### <a name="create-the-connection"></a>De verbinding maken

1.  Kies in de Configuration Manager-console **beheer** > **Cloud Services** > **Upgrade gereedheid van de Connector** > **verbinding maken met de Upgrade Analytics** starten de **toevoegen Analytics verbinding upgradewizard**.
3.  Op de **Azure Active Directory** scherm, bieden **Tenant**, **Client-ID**, en **Client geheime sleutel**, en selecteer vervolgens **volgende**.
4.  Op de **gereedheid voor Upgrade** scherm, geeft u instellingen voor de verbinding door in te vullen uw **Azure-abonnement**, **Azure resourcegroep**, en **Operations Management Suite werkruimte**.
5.  Controleer de verbindingsinstellingen op de **samenvatting** scherm en selecteer vervolgens **volgende**.

    > [!NOTE]
    > Gereedheid voor Upgrade moet u verbinden met de site op hoogste niveau in uw hiërarchie. Als u verbinding maken met gereedheid voor Upgrade van een zelfstandige primaire site en een centrale beheersite vervolgens aan uw omgeving toevoegen, moet u verwijderen en opnieuw de verbinding OMS binnen de nieuwe hiërarchie.

### <a name="complete-upgrade-readiness-tasks"></a>Taken uitvoeren gereedheid voor Upgrade  

Nadat u hebt de verbinding in Configuration Manager maakt, deze taken uitvoeren, zoals beschreven in [aan de slag met gereedheid voor Upgrade](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).  

1. De service UpgradeReadiness toevoegt aan de werkruimte OMS.  
2. Genereren van een commerciële-ID.  
3. Abonneren op gereedheid voor Upgrade.   

## <a name="use-the-upgrade-readiness-deployment-script"></a>Gebruik een script voor de implementatie van de gereedheid voor Upgrade  

U kunt veel van de gereedheid voor Upgrade taken automatiseren en oplossen van problemen met de Microsoft delen van gegevens **implementatiescript gereedheid voor Upgrade**.  
Een script voor de implementatie van de gereedheid voor Upgrade doet het volgende:  

- Hiermee stelt u commerciële ID-toets + CommercialDataOptIn + RequestAllAppraiserVersions sleutels.  
- Controleert of computers van gebruikers kunnen gegevens naar Microsoft verzenden.  
- Controleert of de computer opnieuw opstarten in behandeling heeft.   
- Verifieert dat de nieuwste versie van KB 10.0 x pakket is geïnstalleerd (10.0.14913 of latere releases vereist).  
- Bij inschakeling wordt ingeschakeld voor het oplossen van de uitgebreide modus.  
- Met deze opdracht start de verzameling van de telemetriegegevens die Microsoft nodig heeft om de gereedheid voor upgrade van uw organisatie vast te stellen.  
- Bij inschakeling van het script wordt uitgevoerd in een venster cmd weergegeven zodat u inzicht in problemen (geslaagd of mislukt voor elke stap) en/of schrijft naar het logboekbestand.  

### <a name="to-run-the-upgrade-readiness-deployment-script"></a>De gereedheid voor Upgrade-implementatiescript uitvoeren:  

1. Download de [gereedheid voor Upgrade implementatiescript](https://go.microsoft.com/fwlink/?LinkID=822966&clcid=0x409) en UpgradeReadiness.zip uit te pakken. De bestanden in de **Diagnostics** map zijn alleen nodig als u van plan bent om uit te voeren van het script in de modus voor probleemoplossing.  
2. Deze parameters in RunConfig.bat bewerken:  
- Opslaglocatie voor de informatie in het foutenlogboek. Voorbeeld: % SystemDrive%\URDiagnostics. U kunt de informatie in het foutenlogboek opslaan op een externe bestandsshare of een lokale map. Als het script wordt geblokkeerd vanuit het maken van het logboekbestand voor het opgegeven pad, maakt de logboekbestanden in het station met de Windows-map.  
- Commerciële ID sleutel.  
- Standaard verzendt het script logboekinformatie naar de console en het logboekbestand. De als standaardgedrag wilt wijzigen, gebruikt u een van de volgende opties:  
    - logMode = 0 logboek alleen console  
    - logMode = 1 logboek bestands- en -console  
    - logMode = 2 log naar het bestand alleen  
    - Voor het oplossen van problemen ingesteld **isVerboseLogging** naar **$true** voor het genereren van logboekgegevens die helpen kan bij het oplossen van problemen. Standaard **isVerboseLogging** is ingesteld op **$false**. Zorg ervoor dat de map diagnostische gegevens in dezelfde map als het script moet worden gebruikt in deze modus wordt geïnstalleerd.  
    - Gebruikers melden als ze nodig hebben om hun computers opnieuw opstarten. Dit is standaard uitgeschakeld.  

3. Nadat u de parameters in RunConfig.bat bewerken, moet u het script uitvoeren als beheerder.  


## <a name="view-microsoft-upgrade-readiness-properties-in-configuration-manager"></a>Eigenschappen van de gereedheid voor Upgrade van Microsoft weergeven in Configuration Manager  

1.  Navigeer in de Configuration Manager-console naar **Cloudservices**, en kies vervolgens **OMS Connector** openen de **OMS verbindingseigenschappen** pagina.  

2.  In deze pagina zijn er twee tabbladen:
  * De **Azure Active Directory** tabblad toont uw **Tenant**, **Client-ID**, **Client geheime sleutel verlopen**, en kunt u **controleren** uw **Client geheime sleutel** als het certificaat is verlopen.
  * De **gereedheid voor Upgrade** tabblad toont de **Azure-abonnement**, **Azure resourcegroep**, en **Operations Management Suite werkruimte**.

## <a name="view-and-use-the-upgrade-information"></a>Weergeven en gebruiken van de upgrade-informatie

Nadat u hebt gereedheid voor Upgrade geïntegreerd met Configuration Manager, kunt u de analyse van de gereedheid voor upgrade van uw clients weergeven en vervolgens actie ondernemen.

1. Kies in de Configuration Manager-console **bewaking** > **overzicht** > **gereedheid voor Upgrade**.
2. Controleer de gegevens, waaronder de gereedheid voor upgrade-status en het percentage van de Windows-apparaten die telemetrie rapporteren.
3. U kunt het dashboard om gegevens voor apparaten weer in specifieke verzamelingen te filteren.
4. U kunt de apparaten weergeven in de status van een bepaalde gereedheid en maak een dynamische verzamelingen voor deze apparaten, zodat die apparaten als gereed upgraden of actie ondernemen om te zorgen dat ze op een status van de gereedheid van de.

