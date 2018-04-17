---
title: Monitor voor clients met Windows Analytics
titleSuffix: Configuration Manager
description: Windows Analytics is een set van oplossingen die worden uitgevoerd op de Operations Management Suite waarmee dat u waardevolle inzichten in de huidige status van uw omgeving tekent dankzij het gebruik van de Windows-telemetriegegevens die is gerapporteerd door apparaten in uw omgeving.
ms.custom: na
ms.date: 01/02/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: CF35CE87-3BA8-4A84-9BC8-ABCEA4666212
caps.latest.revision: 23
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 15b1d07f35f774f3ec8f082a86c90ecb989a438e
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="use-windows-analytics-with-configuration-manager"></a>Windows-Analytics gebruiken met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

[Windows Analytics](https://www.microsoft.com/WindowsForBusiness/windows-analytics) is een set van oplossingen die worden uitgevoerd op [Operations Management Suite](/azure/operations-management-suite/operations-management-suite-overview) (OMS). Deze oplossingen kunnen u meer inzicht krijgen in de huidige status van uw omgeving. Apparaten in uw omgeving rapporteren telemetriegegevens van Windows en deze gegevens kunnen worden geopend en geanalyseerd door oplossingen in de [Operations Management Suite-webportal](https://mms.microsoft.com). Door verbinding te maken [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) naar Configuration Manager u rechtstreeks toegang tot de gegevens in de **bewaking** knooppunt van de Configuration Manager-console.

De Windows-telemetriegegevens die wordt gebruikt door Windows Analytics is niet rechtstreeks op de siteserver van Configuration Manager overgedragen. Met de Windows-service telemetrie versturen clientcomputers telemetriegegevens van Windows. Deze service wordt vervolgens de relevante gegevens overdraagt naar Windows analyseoplossingen gehost in een van uw organisatie OMS werkruimten. Configuration Manager kunt u vervolgens rechtstreeks naar de relevante gegevens in de webportal met-context koppelingen of gegevens die deel uitmaakt van oplossingen die u hebt gekoppeld aan Configuration Manager rechtstreeks worden weergegeven. U kunt ook rechtstreeks een query de gegevens van de bewerking Management Suite-webportal.

>[!Important]
>[Configuration Manager diagnostische gegevens en gebruiksgegevens](../../plan-design/diagnostics/diagnostics-and-usage-data.md), dat de siteserver van Configuration Manager-rapporten naar Microsoft, is gescheiden van de analyses van Windows en Windows telemetrie.

## <a name="configure-clients-to-report-data-to-windows-analytics"></a>Clients configureren voor het rapportgegevens Windows Analytics

Voor clientapparaten voor het rapportgegevens Windows Analytics, moet u apparaten configureren met een commerciële ID-sleutel die is gekoppeld aan de OMS-werkruimte die als host fungeert voor uw Windows-analytische gegevens. U moet ook apparaten rapport telemetrie configureren op een niveau telemetrie geschikt is voor de specifieke oplossingen die u wilt gebruiken. 

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics clientinstellingen configureren
Voor het configureren van Windows Analytics, in de console Configuration Manager kiezen **beheer** > **clientinstellingen**, dubbelklikt u op **aangepaste Apparaatclientinstellingen maken**, en controleer vervolgens **Windows Analytics**.  

Na het navigeren naar de **Windows Analytics** tabblad instellingen en configureer de volgende instellingen:
  -  **Commerciële id-sleutel**  
De commerciële ID sleutel maps informatie vanaf apparaten die u naar de OMS-werkruimte die als host fungeert voor Windows Analytics-gegevens van uw organisatie beheren. Als u al een commerciële ID-sleutel voor gebruik met de gereedheid van de Upgrade hebt geconfigureerd, gebruikt u die-ID. Als u nog geen een commerciële ID-sleutel, Zie [uw commerciële ID-sleutel genereren]( https://technet.microsoft.com/itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

  -  **Telemetrie-niveau voor Windows 10-apparaten**   
Zie voor meer informatie over elk Windows 10 telemetrie niveau [telemetrie van de configuratie van Windows in uw organisatie](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

   > [!Note]
   > Met de update 1710, kunt u instellen de gegevensverzameling voor Windows 10-telemetrie op **uitgebreid (beperkt)**. Deze instelling kunt u actie worden uitgevoerd om inzicht te krijgen over de apparaten in uw omgeving zonder apparaten rapportage van de gegevens in de **uitgebreid** telemetrie niveau met Windows 10 versie 1709 of hoger. Het niveau uitgebreid (beperkt) telemetrie bevat metrische gegevens van het niveau basis, evenals een subset van de verzamelde gegevens van het niveau uitgebreid relevant zijn voor Windows Analytics.


  -  **U meldt zich aan commerciële gegevensverzameling op Windows 7, 8 en 8.1-apparaten**   
Zie voor meer informatie [velden en Windows 7, Windows 8 en Windows 8.1 appraiser telemetrische gebeurtenissen](https://go.microsoft.com/fwlink/?LinkID=822965).

  -  **Gegevensverzameling Internet Explorer configureren**  
Op apparaten met Windows 8.1 of ouder, Internet Explorer gegevens kunt verzamelen gereedheid voor Upgrade voor het detecteren van web application incompatibiliteiten die voorkomen een smooth upgrade naar Windows 10 dat kunnen. Internet Explorer gegevensverzameling kan worden ingeschakeld voor een per zone per internet. Zie voor meer informatie over de zones internet [over beveiligingszones](https://msdn.microsoft.com/library/ms537183(v=vs.85).aspx).

## <a name="use-upgrade-readiness-to-identify-windows-10-compatibility-issues"></a>Gereedheid voor Upgrade gebruiken om te identificeren van compatibiliteitsproblemen voor Windows 10

Gereedheid voor upgrade (voorheen Upgrade Analytics) kunt u voor het analyseren van de gereedheid van het apparaat en de compatibiliteit met Windows 10. Deze evaluatie kunt soepeler upgrades. Nadat u Configuration Manager gereedheid van de Upgrade, toegang krijgen tot deze client upgradecompatibiliteit gegevens rechtstreeks in de Configuration Manager-console. Vervolgens doelapparaten voor de upgrade of herstel van de lijst met apparaten.

Zie voor meer informatie en meer informatie over het configureren en verbinden van de gereedheid voor Upgrade [gereedheid voor Upgrade](../../clients/manage/upgrade/upgrade-analytics.md).

## <a name="use-windows-analytics-to-identify-gaps-in-windows-information-protection-policies"></a>Gebruik Windows Analytics naar hiaten in de Windows Information Protection-beleid

Windows 10 versie 1703 en latere apparaten die zijn geconfigureerd met een [Windows Information Protection](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) (OHW) beleid rapport telemetrie over toepassingen die toegang zakelijke gegevens in uw omgeving, maar de toepassing van OHW beleidsregels tot niet bevatten. Gebruikers hebben deze toepassingen om productief te blijven mogelijk nodig, maar OHW blokkeert de toegang van gebruikers. Kennis dat gebruikers van bedrijfsgegevens gebruikmaken is nuttig voor het onderhoud van uw Windows Information Protection-beleid in Configuration Manager. 

Toegang tot deze Windows Information Protection-gegevens met behulp van dit [Operations Management Suite query](https://go.microsoft.com/fwlink/?linkid=849952).