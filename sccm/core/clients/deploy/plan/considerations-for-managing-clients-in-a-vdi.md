---
title: 'Clientbeheer virtuele desktopinfrastructuur (VDI) | Microsoft Docs '
description: System Center Configuration Manager-clients in een virtual desktop infrastructure (VDI) beheren.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: abd45393-d84e-4583-bc80-74bbb3709577
caps.latest.revision: "7"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: d73daf6427b8c58d21d579f3b41df513cc3e3b0b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="considerations-for-managing-system-center-configuration-manager-clients--in-a-virtual-desktop-infrastructure-vdi"></a>Overwegingen voor het beheren van System Center Configuration Manager-clients in een virtuele bureaublad infrastructuur (VDI)

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager ondersteunt de installatie van Configuration Manager-client op de volgende virtuele desktopinfrastructuur (VDI)-scenario's:  

-   **Persoonlijke virtuele machines** -persoonlijke virtuele machines worden meestal gebruikt wanneer u wilt ervoor zorgen dat gebruikersgegevens en instellingen worden bewaard op de virtuele machine tussen sessies.  

-   **Extern bureaublad-sessies** -extern bureaublad-Services laten een server voor het hosten van meerdere, gelijktijdige clientsessies. Gebruikers kunnen verbinding maken met een sessie en voer vervolgens de toepassingen op die server.  

-   **Gegroepeerde virtuele machines** -gegroepeerde virtuele machines blijven niet bestaan tussen sessies. Wanneer een sessie is afgesloten, worden alle gegevens en instellingen verwijderd. Gegroepeerde virtuele machines zijn nuttig wanneer Extern bureaublad-Services kan niet worden gebruikt omdat een vereiste bedrijfstoepassing kan niet worden uitgevoerd op de Windows Server die als host fungeert de clientsessies.  

 De volgende tabel geeft overwegingen voor het beheren van de Configuration Manager-client in een virtual desktop infrastructure.  

|Type van de virtuele machine|Overwegingen|  
|--------------------------|--------------------|  
|Persoonlijke virtuele machines|Configuration Manager beschouwt persoonlijke virtuele machines identiek als een fysieke computer. Configuration Manager-client kan vooraf is geïnstalleerd op de installatiekopie van de virtuele machine of geïmplementeerd nadat de virtuele machine is geleverd.|  
|Extern bureaublad-services|Configuration Manager-client is niet geïnstalleerd voor individuele extern bureaublad-sessies. In plaats daarvan is de client slechts één keer op de extern bureaublad-Services-server geïnstalleerd. Alle functies van Configuration Manager kunnen worden gebruikt op de server extern bureaublad-Services.|  
|Gegroepeerde virtuele machines|Wanneer een gegroepeerde virtuele machine buiten werking wordt gesteld, gaan alle wijzigingen die u aanbrengt met Configuration Manager verloren.<br /><br /> Gegevens die zijn geretourneerd door de Configuration Manager-functies, zoals hardware-inventaris, software-inventarisatie en softwarelicentiecontrole mogelijk niet relevant voor uw behoeften aangezien de virtuele machine mogelijk slechts gedurende een korte periode operationeel. Houd rekening met uitzondering van gegroepeerde virtuele machines uit inventaristaken uit.|  

 Omdat virtualisatie ondersteunt meerdere Configuration Manager-clients op dezelfde fysieke computer wordt uitgevoerd, veel clientbewerkingen een ingebouwde willekeurige vertraging voor geplande acties zoals hardware hebt en software-inventarisatie, antimalware scant, software-installaties en software-updates scans. Deze vertraging helpt de CPU-verwerking en gegevensoverdracht voor een computer die meerdere virtuele machines met de Configuration Manager-client te distribueren.  

> [!NOTE]  
>  Met uitzondering van Windows Embedded-clients die zich in de onderhoudsmodus bevindt, Configuration Manager-clients die niet worden uitgevoerd in gevirtualiseerde omgevingen ook gebruiken voor deze willekeurige vertraging. Wanneer u veel geïmplementeerde clients hebt, wordt dit gedrag pieken in netwerkbandbreedte voorkomen en vermindert het de CPU-verwerkingsvereiste op de Configuration Manager-sitesystemen, zoals het beheerpunt en de siteserver. Het vertragingsinterval varieert volgens de Configuration Manager-functie.  
>   
>  De randomisatievertraging wordt standaard uitgeschakeld voor vereiste software-updates en vereiste toepassingsimplementaties met behulp van de volgende clientinstelling: **Computeragent**: **Deadlinerandomisatie uitschakelen**.
