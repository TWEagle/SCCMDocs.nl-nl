---
title: Vereisten voor asset Intelligence
titleSuffix: Configuration Manager
description: Ophalen van de vereisten voor Asset Intelligence in System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 23ab4f94-7bfe-436e-8a6a-029409a2730c
caps.latest.revision: "10"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 88358017bd8807caca3c544ecdf07c1b751efd3f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="prerequisites-for-asset-intelligence-in-system-center-configuration-manager"></a>Vereisten voor Asset Intelligence in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Asset Intelligence in System Center Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product.  

## <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  
 De volgende tabel bevat de afhankelijkheden voor Asset Intelligence die extern aan Configuration Manager zijn.  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Controle van vereisten voor geslaagde aanmeldingsgebeurtenissen|Vier Asset Intelligence-rapporten bevatten gegevens die zijn verzameld uit de Windows-beveiligingslogboeken op clientcomputers. Als de beveiligingslogboeken niet zo zijn geconfigureerd dat alle geslaagde aanmeldingsgebeurtenissen worden geregistreerd, bevatten deze rapporten geen gegevens, ook niet als de juiste rapportageklasse voor hardware-inventarisatie is ingeschakeld.<br /><br /> De volgende Asset Intelligence-rapporten zijn afhankelijk van verzamelde gegevens uit het Windows-beveiligingslogboek:<br /><br /> -Hardware 03A - primaire computergebruikers<br />-Hardware 03B - Computers voor een specifieke primaire Consolegebruiker<br />-Hardware 04A - gedeelde Computers (meerdere gebruikers)<br />-Hardware 05A - Consolegebruikers op een specifieke Computer<br /><br /> Als u de clientagent voor hardware-inventarisatie wilt inschakelen om te inventariseren welke gegevens vereist zijn ter ondersteuning van deze rapporten, moet u eerst de instellingen voor het Windows-beveiligingslogboek op clients wijzigen zodat alle geslaagde aanmeldingsgebeurtenissen worden geregistreerd. Vervolgens schakelt u de rapportageklasse **SMS_SystemConsoleUser** voor hardware-inventarisatie in. Zie voor meer informatie over het wijzigen van alle geslaagde aanmeldingsgebeurtenissen worden geregistreerd beveiligingslogboeken [controle van geslaagde aanmeldingsgebeurtenissen inschakelen](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableSuccessLogonEvents).|  

> [!NOTE]  
>  In de **SMS_SystemConsoleUser** -rapportageklasse voor hardware-inventarisatie worden gegevens van geslaagde aanmeldingsgebeurtenissen alleen voor de afgelopen negentig dagen van het beveiligingslogboek bewaard, ongeacht de lengte van het logboek. Als het beveiligingslogboek minder dan negentig dagen aan gegevens bevat, wordt het hele logboek gelezen.  

## <a name="dependencies-internal-to-configuration-manager"></a>Afhankelijkheden intern aan Configuration Manager  
 De volgende tabel bevat de afhankelijkheden voor Asset Intelligence die intern aan Configuration Manager zijn.  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Vereisten voor clientagents|De Asset Intelligence-rapporten zijn afhankelijk van clientgegevens die worden verkregen via clienthardware- en software-inventarisrapporten. U kunt de benodigde gegevens voor alle Asset Intelligence-rapporten ontvangen als de volgende clientagents zijn ingeschakeld:<br /><br /> -Clientagent voor hardware inventaris<br />-Clientagent voor Softwaremeter|  
|Afhankelijkheden voor clientagent voor hardware-inventaris|Als u vereiste inventarisatiegegevens voor enkele Asset Intelligence-rapporten wilt verzamelen, moet de clientagent voor hardware-inventaris zijn ingeschakeld. Bovendien moeten bepaalde rapportageklassen voor hardware-inventarisatie, waarvan Asset Intelligence-rapporten afhankelijk zijn, ingeschakeld zijn op primaire siteservercomputers.<br /><br /> Zie voor meer informatie over het inschakelen van de Clientagent voor Hardware-inventaris [hardware-inventarisatie in System Center Configuration Manager uitbreiden](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).|  
|Afhankelijkheden voor clientagent voor softwaremeter|Een aantal Asset Intelligence-softwarerapporten is voor gegevens afhankelijk van de clientagent voor softwaremeter Zie voor meer informatie over het inschakelen van de Clientagent voor Software Metering [app-gebruik controleren met softwaremeter in System Center Configuration Manager](../../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).<br /><br /> De volgende Asset Intelligence-rapporten zijn voor het leveren van gegevens afhankelijk van de clientagent voor softwaremeter:<br /><br /> -Software 07A - recent gebruikte uitvoerbare programma's door het aantal Computers<br />-Software 07B - Computers die recent een opgegeven uitvoerbaar programma hebben gebruikt<br />-Software 07C - recent gebruikte uitvoerbare programma's op een specifieke Computer<br />-Software 08A - recent gebruikte uitvoerbare programma's op telling van gebruikers<br />-Software 08B - gebruikers die recent een opgegeven uitvoerbaar programma hebben gebruikt<br />-Software 08C - recent gebruikte uitvoerbare programma's door een opgegeven gebruiker|  
|Vereisten voor Asset Intelligence-rapportageklassen voor hardware-inventarisatie|Asset Intelligence-rapporten in Configuration Manager, is afhankelijk van specifieke hardware-inventarisrapportageklassen. Tot de rapportageklassen voor hardware-inventarisatie zijn ingeschakeld en clients hardware-inventaris op basis van deze klassen hebben gerapporteerd, bevatten de bijbehorende Asset Intelligence-rapporten geen gegevens. U kunt de volgende rapportageklassen voor hardware-inventarisatie inschakelen ter ondersteuning van rapportagevereisten voor Asset Intelligence:<br /><br /> -SMS_SystemConsoleUsage<sup>1</sup><br />-SMS_SystemConsoleUser<sup>1</sup><br />-SMS_InstalledSoftware<br />-SMS_AutoStartSoftware<br />-SMS_BrowserHelperObject<br />-Win32_USBDevice<br />-SMS_InstalledExecutable<br />-SMS_SoftwareShortcut<br />-SoftwareLicensingService<br />-SoftwareLicensingProduct<br />-Rapportageklasse<br /><br /> <sup>1</sup> Standaard zijn de Asset Intelligence-rapportageklassen voor hardware-inventarisatie **SMS_SystemConsoleUsage** en **SMS_SystemConsoleUser** ingeschakeld.<br /><br /> U kunt de Asset Intelligence-hardware-inventaris rapportageklassen in de Configuration Manager-console in bewerken de **activa en naleving** werkruimte wanneer u klikt op de **Asset Intelligence** knooppunt. Zie voor meer informatie de [Asset Intelligence inschakelen hardware-inventarisrapportageklassen](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md#BKMK_EnableAssetIntelligence) sectie het [Asset Intelligence configureren in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md) onderwerp.|  
|Reporting Services-punt|De sitesysteemrol Reporting Services-punt moet zijn geïnstalleerd om software-updaterapporten te kunnen weergeven. Zie [Rapportage configureren in Configuration Manager](http://go.microsoft.com/fwlink/p/?LinkId=232661)voor meer informatie over het maken van een Reporting Services-punt.|  
