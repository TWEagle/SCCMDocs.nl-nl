---
title: Clients zoeken management points DNS-publicatie configureert | Microsoft-documenten
description: Clientcomputers om beheerpunten te vinden met behulp van DNS-publishing in System Center Configuration Manager ingesteld.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 03cec407-0f9f-454f-a360-b005af738d29
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d016ec3fe106b2d90b3c14b4f9296aed4d198644
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-client-computers-to-find-management-points-by-using-dns-publishing-in-system-center-configuration-manager"></a>Het configureren van clientcomputers beheerpunten vinden via DNS-publishing in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager clients moeten een beheerpunt vinden om te vervolledigen sitetoewijzing en als een continu proces om beheerd te blijven. Active Directory Domain Services is de veiligste methode om clients op het intranet beheerpunten te laten vinden. Als clients deze servicelocatiemethode echter niet kunnen gebruiken (bijvoorbeeld als u het Active Directory-schema niet hebt uitgebreid of clients deel uitmaken van een werkgroep), gebruikt u DNS-publicatie als voorkeursalternatief voor de servicelocatiemethode.  

> [!NOTE]  
>  Wanneer u de client voor Linux en UNIX installeert, moet u een beheerpunt opgeven dat moet worden gebruikt als eerste contactpunt. Zie voor meer informatie over het installeren van de client voor Linux en UNIX [clients implementeren voor UNIX en Linux-servers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

 Voordat u DNS-publicatie gebruikt voor beheerpunten, moet u ervoor zorgen dat DNS-servers op intranet servicelocatiebronrecords (SRV RR) en bijbehorende hostbronrecords (A of AAA) hebben voor de beheerpunten van de site. De servicelocatiebronrecords kunnen automatisch worden gemaakt door Configuration Manager of handmatig, door de DNS-beheerder die de records in DNS maakt.  

 Zie voor meer informatie over DNS-publicatie als servicelocatiebepalingsmethode voor Configuration Manager-clients, [begrijpen hoe clients vinden sitebronnen en services voor System Center Configuration Manager](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

 Clients zoeken standaard in DNS naar beheerpunten in hun DNS-domein. Echter, als er geen beheerpunten zijn gepubliceerd in het domein van clients, moet u handmatig configureren clients met een punt DNS-achtervoegsel. U kunt dit DNS-achtervoegsel op clients configureren tijdens of na de clientinstallatie:  

-   Als u clients tijdens de clientinstallatie wilt configureren voor het achtervoegsel van een beheerpunt, configureert u de Client.msi-eigenschappen van CCMSetup.  

-   Als u clients na de clientinstallatie wilt configureren voor het achtervoegsel van een beheerpunt, configureert u de **Eigenschappen van Configuration Manager**.  

#### <a name="to-configure-clients-for-a-management-point-suffix-during-client-installation"></a>Clients configureren voor een achtervoegsel van een beheerpunt tijdens de clientinstallatie  

-   Installeer de client met de volgende Client.msi-eigenschap van CCMSetup:  

    -   **DNSSUFFIX =**  *&lt;beheerpunt domein\>*  

         Als de site meer dan één beheerpunt heeft en deze zich in meer dan één domein bevinden, geeft u slechts één domein op. Wanneer clients verbinding maken met een beheerpunt in dit domein, downloaden ze een lijst met beschikbare beheerpunten, inclusief de beheerpunten van de andere domeinen.  

     Zie voor meer informatie over de CCMSetup-opdrachtregeleigenschappen [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

#### <a name="to-configure-clients-for-a-management-point-suffix-after-client-installation"></a>Clients configureren voor een achtervoegsel van een beheerpunt na de clientinstallatie  

1.  Navigeer in het Configuratiescherm van de clientcomputer naar **Configuration Manager**en dubbelklik vervolgens op **Eigenschappen**.  

2.  Geef op het tabblad **Site** het DNS-achtervoegsel van een beheerpunt op en klik vervolgens op **OK**.  

     Als de site meer dan één beheerpunt heeft en deze zich in meer dan één domein bevinden, geeft u slechts één domein op. Wanneer clients verbinding maken met een beheerpunt in dit domein, downloaden ze een lijst met beschikbare beheerpunten, inclusief de beheerpunten van de andere domeinen.

