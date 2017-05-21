---
title: Planning van de implementatie van clients op Mac-computers | Microsoft-documenten
description: Plan voor de implementatie van clients op Mac-computers in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 75bddb41d4d1cf209fa7595c52b5a6aa831ba3dd
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-client-deployment-to-mac-computers-in-system-center-configuration-manager"></a>Planning voor clientimplementatie op Mac-computers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de Configuration Manager-client installeren op Mac-computers waarop het Mac OS X-besturingssysteem en de volgende beheermogelijkheden gebruiken:  

-   **Hardware-inventaris**  

     U kunt hardware-inventaris van Configuration Manager gebruiken voor het verzamelen van informatie over de hardware en geïnstalleerde toepassingen op Mac-computers. Deze informatie kan vervolgens worden bekeken in Resourceverkenner in de Configuration Manager-console en gebruikt voor het maken van verzamelingen, query's en rapporten. Zie voor meer informatie [Resource Explorer gebruiken om te bekijken van hardware-inventaris in System Center Configuration Manager](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

     Configuration Manager verzamelt de volgende hardware-informatie van Mac-computers:  

    -   Processor  

    -   Computersysteem  

    -   Schijfstation  

    -   Schijfpartitie  

    -   Netwerkadapter  

    -   Besturingssysteem  

    -   Service  

    -   Proces  

    -   Geïnstalleerde Software  

    -   Computersysteemproduct  

    -   USB-Controller  

    -   USB-apparaat  

    -   Cd-romstation  

    -   Videocontroller  

    -   Bureaubladmonitor  

    -   Draagbare accu  

    -   Fysiek geheugen  

    -   Printer  

    > [!IMPORTANT]  
    >  U kunt hardware-informatie wordt verzameld van Mac-computers tijdens hardware-inventaris niet uitbreiden.  

-   **Instellingen voor naleving**  

     Compatibiliteitsinstellingen van Configuration Manager kunt u de compatibiliteit van en herstellen van instellingen voor Mac OS X-voorkeur (.plist). U kunt bijvoorbeeld instellingen voor de startpagina in de Safari-webbrowser of ervoor te zorgen dat de Apple-firewall is ingeschakeld. U kunt ook shell-scripts gebruiken om te controleren en herstellen van instellingen in MAC OS X.  

-   **Toepassingsbeheer**  

     Configuration Manager kunt software implementeren op Mac-computers. U kunt de volgende softwareformaten implementeren op Mac-computers:  

    -   Apple-schijfimage (. DMG)  

    -   Metapakketbestand (. MPKG)  

    -   Mac OS X Installer-pakket (. PAK)  

    -   Mac OS X-toepassing (. APP)  

 Wanneer u de Configuration Manager-client op Mac-computers installeert, kunt u de volgende beheermogelijkheden die worden ondersteund door de Configuration Manager-client op Windows gebaseerde computers niet gebruiken:  

-   Clientpushinstallatie  

-   Implementatie van besturingssystemen  

-   Software-updates  

    > [!NOTE]  
    >  Toepassingsbeheer Configuration Manager kunt u vereiste Mac OS X software-updates implementeren op Mac-computers. Bovendien kunt u instellingen voor naleving om ervoor te zorgen dat computers beschikken over vereiste software-updates.  

-   Onderhoudsvensters  

-   Extern beheer  

-   Energiebeheer  

-   Clientcontrole en herstel van de clientstatus  

 Zie voor meer informatie over het installeren en configureren van de Configuration Manager Mac client [clients implementeren in Macs in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md).

