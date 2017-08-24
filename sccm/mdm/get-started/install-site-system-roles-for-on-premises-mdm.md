---
title: Functies voor On-premises MDM - Configuration Manager installeren | Microsoft Docs
description: Sitesysteemrollen installeren voor On-premises Mobile Device Management in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c3cf9f64-c2b9-4ace-9527-2aba6d4eef04
caps.latest.revision: "9"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 4913606e2f8a36e0004f711b24ecd836d0485124
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="install-site-system-roles-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Sitesysteemrollen installeren voor On-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager op\-premises beheer van mobiele apparaten vereist de volgende sitesysteemrollen in uw Configuration Manager-site-infrastructuur:  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

-   Distributiepunt  

-   Apparaatbeheerpunt  

-   Serviceverbindingspunt  

 Als u wilt toevoegen op\-premises Mobile Device Management voor uw organisatie die de meeste pc's en apparaten die worden beheerd met de Configuration Manager-clientsoftware is u wellicht de meeste van de sitesysteemrollen al geïnstalleerd als onderdeel van uw bestaande infrastructuur. Als dit niet het geval is, Zie [sitesysteemrollen voor System Center Configuration Manager toevoegen](../../core/servers/deploy/configure/add-site-system-roles.md) voor volledige informatie over het toe te voegen aan uw site.  

> [!NOTE]  
>  Als u Databasereplica's met uw apparaat management sitesysteemrol gebruikt, nieuw ingeschreven apparaten in eerste instantie geen verbinding maken met het apparaatbeheerpunt totdat de replica-database is gesynchroniseerd. Deze verbindingsfout treedt op omdat de databasereplica niet over de informatie over het nieuw ingeschreven apparaat nodig zijn voor de verbinding is geslaagd beschikt. Replica's synchroniseren elke 5 minuten, zodat apparaten geen verbinding maken voor de eerste vijf minuten na de inschrijving (meestal 2 verbindingspogingen), waarna het apparaat verbinding.  

 Hiermee wordt aangegeven of u gebruikmaakt van bestaande sitesysteemrollen of nieuwe toevoegt, moet u ze moet worden gebruikt voor het beheren van moderne apparaten configureren. Volg onderstaande stappen voor het configureren van het distributiepunt en apparaatbeheerpunt te laten functioneren voor op\-premises Mobile Device Management:  

> [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt alleen intranetverbindingen van apparaten naar de distributiepunten en apparaatbeheerpunten voor op\-premises Mobile Device Management. Als u ook Mac OS X-computers beheert, moeten deze clients internetverbindingen met deze sitesysteemrollen. In dat geval als u de eigenschappen van het distributiepunt en het apparaatbeheerpunt configureert, moet u de **intranet en internet-verbindingen toestaan** instellen in plaats daarvan.  

### <a name="to-configure-site-system-roles-to-manage-modern-devices"></a>Voor het configureren van sitesysteemrollen om moderne apparaten te beheren:  

1.  Klik in de Configuration Manager-console op **beheer** > **overzicht** > **siteconfiguratie** > **Servers en sitesysteemrollen**.  

2.  Selecteer sitesysteemserver met het distributiepunt of de apparaatbeheerpunt die u wilt configureren, opent u de eigenschappen voor **sitesysteem** en zorg ervoor dat er een FQDN-naam opgegeven. Klik op **OK**.  

3.  Open de eigenschappen voor de distributie punt sitesysteemrol. Zorg ervoor dat op het tabblad Algemeen **HTTPS** is geselecteerd en selecteer **alleen intranetverbindingen toestaan**.  

     Als u ook afzonderlijk Mac-computers met de Configuration Manager-client beheert, gebruikt u **intranet en internet-verbindingen toestaan** in plaats daarvan.  

    > [!NOTE]  
    >  Distributiepunten die zijn geconfigureerd voor intranetverbindingen, moeten sitegrenzen worden geconfigureerd. De huidige vertakking van Configuration Manager ondersteunt alleen IPv4-bereik grenzen voor op\-premises Mobile Device Management. Zie voor meer informatie over het configureren van sitegrenzen [sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager](../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).  

4.  Schakel het selectievakje in naast **mobiele apparaten verbinding maken met dit distributiepunt toestaan**, en klik vervolgens op **OK**.  

5.  Open de eigenschappen voor het beheer punt sitesysteemrol. Zorg ervoor dat op het tabblad Algemeen **HTTPS** is geselecteerd en selecteer **alleen intranetverbindingen toestaan**.  

     Als u ook afzonderlijk Mac-computers met de Configuration Manager-client beheert, gebruikt u **intranet en internet-verbindingen toestaan** in plaats daarvan.  

6.  Schakel het selectievakje in naast **laat mobiele apparaten en Mac-Computer gebruiken dit beheerpunt**. Klik op **OK**.  

     Hiermee schakelt u effectief het beheerpunt in een apparaatbeheerpunt.  

 Zodra de sitesysteemrollen zijn toegevoegd en geconfigureerd voor het beheer van moderne apparaten, moet u vervolgens de servers die als host fungeert voor de functies als vertrouwde eindpunten voor inschrijven en communicatie met beheerde apparaten configureren. Zie [certificaten voor vertrouwde communicatie voor On-premises Mobile Device Management in System Center Configuration Manager instellen](../../mdm/get-started/set-up-certificates-on-premises-mdm.md) voor meer informatie.  
