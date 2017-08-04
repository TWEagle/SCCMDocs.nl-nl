---
title: Clients - gebruik Windows Analytics met Configuration Manager controleren | Microsoft Docs
description: Windows Analytics is een set van oplossingen die worden uitgevoerd op de Operations Management Suite waarmee dat u waardevolle inzichten in de huidige status van uw omgeving tekent dankzij het gebruik van de Windows-telemetriegegevens die is gerapporteerd door apparaten in uw omgeving.
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: CF35CE87-3BA8-4A84-9BC8-ABCEA4666212
caps.latest.revision: 23
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: adabe8f475eb12dd44005ec07344e8565be20582
ms.contentlocale: nl-nl
ms.lasthandoff: 07/29/2017

---

# <a name="use-windows-analytics-with-configuration-manager"></a>Windows-Analytics gebruiken met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

[Windows Analytics](https://www.microsoft.com/en-us/WindowsForBusiness/windows-analytics) is een set van oplossingen die worden uitgevoerd op [Operations Management Suite](/azure/operations-management-suite/operations-management-suite-overview). De oplossingen kunnen u formulier inzicht in de huidige status van uw omgeving. Apparaten in uw omgeving rapporteren Windows telemetrische gegevens. Deze gegevens kan worden geopend en geanalyseerd door oplossingen in de [Operations Management Suite-webportal](https://mms.microsoft.com). In het geval van [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics) de gegevens kunnen ook rechtstreeks beschikbaar gesteld in het knooppunt controle van de Configuration Manager-console door verbinding te maken gereedheid voor upgrade uitvoeren naar Configuration Manager.

De Windows-telemetriegegevens die wordt gebruikt door Windows Analytics is niet rechtstreeks op de siteserver van Configuration Manager overgedragen. Windows-telemetriegegevens verzenden clientcomputers naar de telemetrie-service. De relevante gegevens wordt vervolgens overgedragen naar Windows analyseoplossingen gehost in een van uw organisatie OMS werkruimten. Configuration Manager kan vervolgens een u rechtstreeks naar de relevante gegevens in de webportal met-context koppelingen of rechtstreeks gegevens weergeven die deel uitmaakt van oplossingen die u hebt gekoppeld aan Configuration Manager. U kunt ook rechtstreeks een query de gegevens van de bewerking Management Suite-webportal.

>[!Important]
>[Configuration Manager diagnostische gegevens en gebruiksgegevens](../../plan-design/diagnostics/diagnostics-and-usage-data.md), die wordt gemeld aan Microsoft van de siteserver van Configuration Manager is volledig gescheiden van de analyses van Windows en Windows telemetrie.

## <a name="configure-clients-to-report-data-to-windows-analytics"></a>Clients configureren voor het rapportgegevens Windows Analytics

In de volgorde voor clientapparaten naar rapport gegevens naar Windows Analytics, apparaten moeten worden geconfigureerd met een commerciële-ID sleutel gekoppeld aan de Operations Management Suite-werkruimte die als host fungeert voor de Windows analytische gegevens voor uw organisatie. De apparaten moeten ook worden geconfigureerd voor het rapport telemetrie op een niveau telemetrie geschikt is voor een bepaalde oplossing of oplossingen die u wilt gebruiken. 

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics clientinstellingen configureren
Voor het configureren van Windows Analytics, in de console Configuration Manager kiezen **beheer** > **clientinstellingen**, dubbelklikt u op **aangepaste Apparaatclientinstellingen maken**, en controleer vervolgens **Windows Analytics**.  

Na het navigeren naar de **Windows Analytics** tabblad instellingen configureert u het volgende:
  -  **Commerciële-ID**  
De commerciële ID sleutel maps informatie vanaf apparaten die u naar de OMS-werkruimte die als host fungeert voor Windows Analytics-gegevens van uw organisatie beheren. Als u al een commerciële ID-sleutel voor gebruik met de gereedheid van de Upgrade hebt geconfigureerd, gebruikt u die-ID. Als u nog geen een commerciële ID-sleutel, Zie [uw commerciële ID-sleutel genereren]( https://technet.microsoft.com/itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

  -  **Telemetrie-niveau voor Windows 10-apparaten**   
Zie voor informatie over wat op elk Windows 10 telemetrie-niveau worden verzameld, [telemetrie van de configuratie van Windows in uw organisatie](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

  -  **U meldt zich aan commerciële gegevensverzameling op Windows 7, 8 en 8.1-apparaten**   
Voor informatie over de gegevens verzameld van deze besturingssystemen wanneer u meedoen, Zie downloaden de [velden en Windows 7, Windows 8 en Windows 8.1 appraiser telemetrische gebeurtenissen](https://go.microsoft.com/fwlink/?LinkID=822965) PDF-bestand van Microsoft.

  -  **Gegevensverzameling Internet Explorer configureren**  
Op apparaten met Windows 8.1 of ouder, Internet Explorer gegevens kunt verzamelen gereedheid voor Upgrade voor het detecteren van web application incompatibiliteiten die voorkomen een smooth upgrade naar Windows 10 dat kunnen. Internet Explorer gegevensverzameling kan worden ingeschakeld voor een per zone per internet. Zie voor meer informatie over de zones internet [over beveiligingszones](https://msdn.microsoft.com/library/ms537183(v=vs.85).aspx).

## <a name="use-upgrade-readiness-to-identify-windows-10-compatibility-issues"></a>Gereedheid voor Upgrade gebruiken om te identificeren van compatibiliteitsproblemen voor Windows 10

Gereedheid voor upgrade (voorheen Upgrade Analytics) kunt u voor het analyseren van de gereedheid van het apparaat en de compatibiliteit met Windows 10. Deze evaluatie kunt soepeler upgrades. Nadat u Configuration Manager gereedheid van de upgrade uitvoert, kunt u deze client upgradecompatibiliteit gegevens rechtstreeks in de Configuration Manager-console openen. Vervolgens moet u kunnen doelapparaten voor herstel of upgrade van de lijst met apparaten.

Zie voor meer informatie en meer informatie over het configureren en verbinden van de gereedheid voor Upgrade [gereedheid voor Upgrade](../../clients/manage/upgrade/upgrade-analytics.md).

## <a name="use-windows-analytics-to-identify-gaps-in-windows-information-protection-policies"></a>Gebruik Windows Analytics naar hiaten in de Windows Information Protection-beleid

Windows 10 versie 1703 en latere apparaten die zijn geconfigureerd met een [Windows Information Protection](https://docs.microsoft.com/en-us/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) (OHW) beleid rapport telemetrie over toepassingen die toegang tot zakelijke gegevens in uw omgeving, maar die niet zijn verwerkt in de regels van het OHW-toepassing. Deze worden mogelijk toepassingen die gebruikers in uw omgeving nodig hebben om productief te blijven, maar die worden geblokkeerd toegang, dus kennis dat ze toegang hebben tot zakelijke gegevens nuttig bij het onderhoud van uw Windows Information Protection-beleid in Configuration Manager zijn kan. 

Deze Windows Information Protection-gegevens zijn toegankelijk via dit [Operations Management Suite query](https://go.microsoft.com/fwlink/?linkid=849952).
