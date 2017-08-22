---
title: Endpoint Protection-puntsitesysteemrol maken | Microsoft Docs
description: Informatie over het configureren van Endpoint Protection voor het beheren van beveiliging en schadelijke software op clientcomputers van Configuration Manager.
defintion: 
definition: 
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a9dc0fe-a942-40a2-bab1-7eeee4d95380
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 6e717bcbe5ef8c3f2efa717d0cebb9e675e7c127
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="create-an-endpoint-protection-point-site-system-role"></a>Endpoint Protection-puntsitesysteemrol maken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 De sitesysteemrol Endpoint Protection-punt moet zijn geïnstalleerd voordat u Endpoint Protection kunt gebruiken. Het moet slechts op één sitesysteemserver en op het hoogste niveau in de hiërarchie op een centrale beheersite of een zelfstandige primaire site worden geïnstalleerd.

 Gebruik een van de volgende procedures, afhankelijk van of u wilt installeren van een nieuwe sitesysteemserver voor Endpoint Protection of een bestaande sitesysteemserver:
 - [Installeren op een nieuwe sitesysteemserver](#new-site-system-server)
 - [Installeren op een bestaande sitesysteemserver](#existing-site-system-server)

> [!IMPORTANT]
>  Wanneer u Endpoint Protection-punt installeert, wordt er een Endpoint Protection-client geïnstalleerd op de server die als host fungeert voor de Endpoint Protection-punt. Services en scans op deze client worden uitgeschakeld zodat het in combinatie met een bestaande anti-malwareoplossing op de server kan worden gebruikt. Als u later deze server voor beheer door Endpoint Protection inschakelt en selecteer de optie voor het verwijderen van een derde partij antimalwareoplossing, wordt het product van derden niet verwijderd. U moet dit product handmatig verwijderen.

## <a name="new-site-system-server"></a>Nieuwe sitesysteemserver

1.  Klik op **Beheer**in de Configuration Manager-console.

2.  Vouw in de werkruimte **Beheer** **Siteconfiguratie**uit en klik op **Servers en sitesysteemrollen**.

3.  Klik op **Sitesysteemserver maken** in het tabblad **Start** , in de groep **Maken**.

4.  Configureer de algemene instellingen voor het sitesysteem op de pagina **Algemeen** en klik vervolgens op **Volgende**.

5.  Selecteer **Endpoint Protection-punt** in de lijst met beschikbare rollen op de pagina **Systeemrolselectie** en klik vervolgens op **Volgende**.

6.  Schakel op de pagina **Endpoint Protection** het selectievakje **Ik ga akkoord met de licentievoorwaarden van Endpoint Protection** in en klik vervolgens op **Volgende**.

    > [!IMPORTANT]
    >  U niet Endpoint Protection in Configuration Manager niet gebruiken tenzij u de licentievoorwaarden accepteren.

7.  Op de **Cloud beveiligingsservice** pagina, selecteert u het niveau van de gegevens die u verzenden naar Microsoft wilt te helpen bij het ontwikkelen van nieuwe definities en klik vervolgens op **volgende**.

    > [!NOTE]
    >  Deze optie configureert de instellingen van de Cloud Protection-Service (voorheen bekend als Microsoft Active Protection Service of MAPS) die worden standaard gebruikt. U kunt vervolgens aangepaste instellingen configureren voor elk beleid dat u maakt. Aanmelden bij Cloud Protection Service om te helpen uw computers om beter te beschermen door voorbeelden van malware die kunnen helpen bij Microsoft Anti-malwaredefinities up-to-date te houden. Wanneer u aanmelden bij Cloud Protection Service, kan de Endpoint Protection-client ook gebruiken de service voor dynamische handtekeningen nieuwe definities gedownload voordat ze worden gepubliceerd naar Windows Update. Zie voor meer informatie [maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Voltooi de wizard.


## <a name="existing-site-system-server"></a>Bestaande sitesysteemserver

1.  Klik op **Beheer**in de Configuration Manager-console.

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, klikt u op **Servers en sitesysteemrollen**, en selecteer vervolgens de server die u wilt gebruiken voor Endpoint Protection.

3.  Klik op **Sitesysteemrollen toevoegen** in het tabblad **Start** , in de groep **Server**.

4.  Configureer de algemene instellingen voor het sitesysteem op de pagina **Algemeen** en klik vervolgens op **Volgende**.

5.  Selecteer **Endpoint Protection-punt** in de lijst met beschikbare rollen op de pagina **Systeemrolselectie** en klik vervolgens op **Volgende**.

6.  Schakel op de pagina **Endpoint Protection** het selectievakje **Ik ga akkoord met de licentievoorwaarden van Endpoint Protection** in en klik vervolgens op **Volgende**.

    > [!IMPORTANT]
    >  U niet Endpoint Protection in Configuration Manager niet gebruiken tenzij u de licentievoorwaarden accepteren.

7.  Op de **Cloud beveiligingsservice** pagina, selecteert u het niveau van de gegevens die u verzenden naar Microsoft wilt te helpen bij het ontwikkelen van nieuwe definities en klik vervolgens op **volgende**.

    > [!NOTE]
    >  Deze optie configureert de beveiligingsservice Cloud instellingen (voorheen bekend als MAPS) worden standaard gebruikt. U kunt aangepaste instellingen configureren voor elk anti-malwarebeleid dat u maakt. Zie voor meer informatie [maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).

8.  Voltooi de wizard.
