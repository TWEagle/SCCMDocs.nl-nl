---
title: Rollen voor On-premises MDM - Configuration Manager installeren | Microsoft-documenten
description: Installeer sitesysteemrollen voor On-premises mobiele apparaten beheren in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c3cf9f64-c2b9-4ace-9527-2aba6d4eef04
caps.latest.revision: 9
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 4913606e2f8a36e0004f711b24ecd836d0485124
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="install-site-system-roles-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Sitesysteemrollen installeren voor On-premises mobiele apparaten beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager op\-lokale beheer van mobiele apparaten vereist de volgende sitesysteemrollen in de Configuration Manager site-infrastructuur:  

-   Inschrijvingspunt  

-   Proxypunt voor inschrijving  

-   Distributiepunt  

-   Apparaatbeheerpunt  

-   Serviceverbindingspunt  

 Als u wilt toevoegen op\-lokaal beheer van mobiele apparaten voor uw organisatie met de meeste pc's en apparaten die worden beheerd met de Configuration Manager-clientsoftware mogelijk hebt u de meeste van de sitesysteemrollen al geïnstalleerd als onderdeel van uw bestaande infrastructuur. Als dit niet het geval is, Zie [sitesysteemrollen toevoegen voor System Center Configuration Manager](../../core/servers/deploy/configure/add-site-system-roles.md) voor volledige informatie over hoe u ze toevoegt aan uw site.  

> [!NOTE]  
>  Als u uw apparaat management sitesysteemrol databasereplica gebruikt, wordt in eerste instantie nieuw ingeschreven apparaten geen verbinding maken met het apparaatbeheerpunt totdat de replica-database wordt gesynchroniseerd met het. Deze verbindingsfout treedt op omdat de replica-database geen informatie over de nieuw ingeschreven apparaat dat nodig is voor een succesvolle verbinding heeft. Replica's synchroniseren om de 5 minuten zodat apparaten geen verbinding maken voor de eerste vijf minuten na de registratie (meestal 2 verbindingspogingen), waarna het apparaat wordt verbinding gemaakt.  

 Of u gebruikmaakt van bestaande sitesysteemrollen of u nieuwe taken toevoegt, moet u ze moet worden gebruikt voor het beheren van moderne apparaten configureren. De volgende stappen voor het configureren van het distributiepunt en apparaatbeheerpunt goed voor op\-premises beheer van mobiele apparaten:  

> [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt alleen intranet verbindingen van apparaten naar de distributiepunten en apparaatbeheerpunten voor op\-premises beheer van mobiele apparaten. Als u ook Mac OS X-computers beheert, moeten deze clients internet-verbindingen met deze sitesysteemrollen. In dat geval als u de eigenschappen van het distributiepunt en het apparaatbeheerpunt configureert, moet u de **intranet en internet-verbindingen toestaat** stellen in plaats daarvan.  

### <a name="to-configure-site-system-roles-to-manage-modern-devices"></a>Configureren van sitesysteemrollen voor het beheren van moderne apparaten:  

1.  Klik in de Configuration Manager-console op **beheer** > **overzicht** > **siteconfiguratie** > **Servers en sitesysteemrollen**.  

2.  Selecteer sitesysteemserver met het distributiepunt of de apparaatbeheerpunt die u wilt configureren, opent u de eigenschappen voor **sitesysteem** en zorg ervoor dat er een FQDN-naam opgegeven. Klik op **OK**.  

3.  Eigenschappen van het distributiepunt openen punt sitesysteemrol. Zorg ervoor dat op het tabblad Algemeen **HTTPS** is geselecteerd en selecteer **intranet alleen verbindingen toestaan**.  

     Als u ook afzonderlijk Mac-computers met Configuration Manager-client beheren bent, gebruikt u **intranet en internet-verbindingen toestaat** in plaats daarvan.  

    > [!NOTE]  
    >  Distributiepunten die zijn geconfigureerd voor intranet-verbindingen vereisen grenzen moeten worden geconfigureerd voor deze site. De huidige vertakking van Configuration Manager ondersteunt alleen IPv4-bereik grenzen voor op\-premises beheer van mobiele apparaten. Zie voor meer informatie over het configureren van de sitegrenzen [sitegrenzen en grensgroepen definiëren voor System Center Configuration Manager](../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).  

4.  Klik op het selectievakje in naast **mobiele apparaten verbinding maken met dit distributiepunt toestaan**, en klik vervolgens op **OK**.  

5.  Eigenschappen voor het beheer openen punt sitesysteemrol. Zorg ervoor dat op het tabblad Algemeen **HTTPS** is geselecteerd en selecteer **intranet alleen verbindingen toestaan**.  

     Als u ook afzonderlijk Mac-computers met Configuration Manager-client beheren bent, gebruikt u **intranet en internet-verbindingen toestaat** in plaats daarvan.  

6.  Klik op het selectievakje in naast **laat mobiele apparaten en Mac-Computer te gebruiken van dit beheerpunt**. Klik op **OK**.  

     Hiermee schakelt u effectief het beheerpunt naar een beheerpunt.  

 Zodra de sitesysteemrollen hebt toegevoegd en geconfigureerd voor moderne apparaten beheren, moet u vervolgens de servers die als host fungeert voor de rollen als vertrouwde eindpunten voor registreren en de communicatie met beheerde apparaten configureren. Zie [stellen certificaten voor vertrouwde communicatie voor On-premises mobiele apparaten beheren in System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md) voor meer informatie.  

