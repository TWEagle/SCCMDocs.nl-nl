---
title: 'Clientbeheer voor virtuele desktopinfrastructuur (VDI) | Microsoft-documenten '
description: System Center Configuration Manager-clients in een virtual desktop infrastructure (VDI) beheren.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: abd45393-d84e-4583-bc80-74bbb3709577
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d73daf6427b8c58d21d579f3b41df513cc3e3b0b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="considerations-for-managing-system-center-configuration-manager-clients--in-a-virtual-desktop-infrastructure-vdi"></a>Overwegingen voor het beheren van System Center Configuration Manager-clients in een virtuele bureaublad infrastructuur (VDI)

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager ondersteunt de installatie van de Configuration Manager-client op de volgende virtuele desktopinfrastructuur (VDI)-scenario's:  

-   **Persoonlijke virtuele machines** -persoonlijke virtuele machines worden in het algemeen gebruikt wanneer u willen we zeker weten dat gebruikersgegevens en instellingen worden bewaard op de virtuele machine tussen sessies.  

-   **Extern bureaublad-servicessessie** -extern bureaublad-Services laten een server voor het hosten van meerdere, gelijktijdige clientsessies. Gebruikers kunnen verbinding maken met een sessie en vervolgens toepassingen op die server uitvoeren.  

-   **Gegroepeerde virtuele machines** -gegroepeerde virtuele machines blijven niet bestaan tussen sessies. Wanneer een sessie wordt gesloten, worden alle gegevens en instellingen verwijderd. Gegroepeerde virtuele machines zijn nuttig wanneer Extern bureaublad-Services kan niet worden gebruikt omdat een vereiste bedrijfstoepassing niet kan worden uitgevoerd op Windows Server die als host fungeert de clientsessies.  

 De volgende tabel geeft overwegingen voor het beheren van de Configuration Manager-client in een VDI.  

|Type van de virtuele machine|Overwegingen|  
|--------------------------|--------------------|  
|Persoonlijke virtuele machines|Configuration Manager beschouwt persoonlijke virtuele machines identiek als een fysieke computer. De Configuration Manager-client kan vooraf is geïnstalleerd op de installatiekopie van de virtuele machine of geïmplementeerd nadat de virtuele machine is geleverd.|  
|Extern bureaublad-services|De Configuration Manager-client is niet geïnstalleerd voor individuele extern bureaublad-sessies. In plaats daarvan is de client slechts eenmaal geïnstalleerd op de extern bureaublad-Services-server. Alle functies van Configuration Manager kunnen worden gebruikt op de extern bureaublad-Services-server.|  
|Gegroepeerde virtuele machines|Wanneer een gegroepeerde virtuele machine buiten werking wordt gesteld, gaan alle wijzigingen die u hebt aangebracht met behulp van Configuration Manager verloren.<br /><br /> Gegevens geretourneerd van Configuration Manager-functies zoals hardware-inventaris, software-inventarisatie en softwarelicentiecontrole mogelijk niet relevant voor uw behoeften aangezien de virtuele machine mogelijk slechts gedurende een korte periode operationeel. Overweeg gegroepeerde virtuele machines uit inventaristaken uitsluiten.|  

 Omdat virtualisatie ondersteunt meerdere Configuration Manager-clients op dezelfde fysieke computer wordt uitgevoerd, veel clientbewerkingen een ingebouwde willekeurige vertraging voor geplande acties zoals hardware hebt en software-inventarisatie, schadelijke software scant, software-installaties en software-updates scans. Deze vertraging helpt te verdelen van de CPU-verwerking en gegevensoverdracht voor een computer die meerdere virtuele machines waarop de Configuration Manager-client wordt uitgevoerd.  

> [!NOTE]  
>  Met uitzondering van Windows Embedded-clients die zich in de onderhoudsmodus bevindt, Configuration Manager-clients die niet in gevirtualiseerde omgevingen werken ook gebruiken voor deze willekeurige vertraging. Wanneer u veel geïmplementeerde clients hebt, wordt dit gedrag pieken in netwerkbandbreedte voorkomt en vermindert het CPU-verwerkingsvereiste op de Configuration Manager-sitesystemen, zoals de beheerserver en de siteserver. Het vertragingsinterval varieert volgens de Configuration Manager-functie.  
>   
>  Willekeurige vertraging is standaard uitgeschakeld voor vereiste software-updates en vereiste toepassingsimplementaties met behulp van de volgende clientinstelling: **Computeragent**: **Deadlinerandomisatie uitschakelen**.

