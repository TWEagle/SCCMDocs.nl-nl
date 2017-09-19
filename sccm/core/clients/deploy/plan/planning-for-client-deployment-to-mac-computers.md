---
title: Clientimplementatie op Mac-computers plannen | Microsoft Docs
description: Plan de implementatie van clients op Mac-computers in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: c3108813a04cf464bfc05961113bbdffb9a81419
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="planning-for-client-deployment-to-mac-computers-in-system-center-configuration-manager"></a>Planning voor clientimplementatie op Mac-computers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de Configuration Manager-client installeren op Mac-computers waarop het Mac OS X-besturingssysteem wordt uitgevoerd en de volgende beheermogelijkheden gebruiken:  

-   **Hardware-inventaris**  

     U kunt hardware-inventaris van Configuration Manager gebruiken voor het verzamelen van informatie over de hardware en geïnstalleerde toepassingen op Mac-computers. Deze informatie kan vervolgens worden bekeken in Resourceverkenner in de Configuration Manager-console en gebruikt voor het maken van verzamelingen, query's en rapporten. Zie voor meer informatie [Resource Explorer gebruiken om hardware-inventaris in System Center Configuration Manager weer te geven](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

     Configuration Manager verzamelt de volgende hardware-informatie van Mac-computers:  

    -   Processor  

    -   Computersysteem  

    -   Harde schijf  

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
    >  U kunt de hardware-informatie die wordt verzameld van Mac-computers tijdens hardware-inventarisatie niet uitbreiden.  

-   **Instellingen voor naleving**  

     Instellingen voor naleving van Configuration Manager kunt u de compatibiliteit van en het herstellen van instellingen voor Mac OS X-voorkeur (.plist). U kunt bijvoorbeeld instellingen voor de startpagina in de Safari-webbrowser of zorg ervoor dat de Apple-firewall is ingeschakeld. U kunt ook shell-scripts gebruiken om te controleren en herstellen van instellingen in MAC OS X.  

-   **Toepassingsbeheer**  

     Configuration Manager kan software implementeren op Mac-computers. U kunt de volgende softwareformaten implementeren op Mac-computers:  

    -   Apple-schijfimage (. DMG)  

    -   Metapakketbestand (. MPKG)  

    -   Mac OS X Installer-pakket (. PAK)  

    -   Mac OS X-toepassing (. APP)  

 Wanneer u de Configuration Manager-client op Mac-computers installeert, kunt u de volgende beheermogelijkheden die worden ondersteund door de Configuration Manager-client op Windows gebaseerde computers niet gebruiken:  

-   Clientpushinstallatie  

-   Implementatie van besturingssystemen  

-   Software-updates  

    > [!NOTE]  
    >  Configuration Manager-Toepassingsbeheer kunt u vereiste Mac OS X software-updates implementeren op Mac-computers. Bovendien kunt u instellingen voor naleving om ervoor te zorgen dat computers beschikken over vereiste software-updates.  

-   Onderhoudsvensters  

-   Extern beheer  

-   Energiebeheer  

-   Clientcontrole en herstel van de clientstatus  

 Zie voor meer informatie over het installeren en configureren van de Configuration Manager Mac-client [clients implementeren op Mac-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-macs.md).
