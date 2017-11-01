---
title: UNIX/Linux-client componentservices en opdrachten
titleSuffix: Configuration Manager
description: Meer informatie over componentservices en opdrachten voor Linux en UNIX-clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5a8c79f-5791-49c5-8055-086d742e5559
caps.latest.revision: "6"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 238a824aad1acd1f3dd41b1b01afa9248b44ab5d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="linux-and-unix-clients-component-services-and-commands-for-system-center-configuration-manager"></a>Onderdeelservices voor Linux en UNIX-clients en opdrachten voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 De volgende tabel identificeert de clientonderdeelservice van de Configuration Manager-client voor Linux en UNIX.  

|Bestandsnaam|Meer informatie|  
|---------------|----------------------|  
|ccmexec.bin|Deze service is gelijk aan de ccmexc-service op een Windows-client. Het is verantwoordelijk voor alle communicatie met Configuration Manager-sitesysteemrollen en communiceert tevens met de service omiserver.bin voor het verzamelen van hardware-inventaris van de lokale computer.<br /><br /> Voer **ccmexec -h**uit voor een lijst met alle ondersteunde opdrachtregelargumenten|  
|omiserver.bin|Deze service is de CIM-server. De CIM-server biedt een raamwerk voor pluggable softwaremodules, die providers worden genoemd. Providers communiceren met Linux en UNIX computerresources en verzamelen de hardware-inventarisgegevens. De **proces-provider** voor een Linux-computer verzamelt bijvoorbeeld gegevens die zijn gekoppeld aan de processen van het Linux-besturingssysteem.|  

 De volgende tabellen bevatten opdrachten die u kunt gebruiken om de clientservices (ccmexec.bin en omiserver.bin) op elke versie van Linux of UNIX te starten, te stoppen of opnieuw op te starten. Bij het starten of stoppen van de service ccmexec, wordt de service omniserver ook wordt gestart of gestopt.  

|Besturingssysteem|Opdrachten|  
|----------------------|--------------|  
|Universele Agent<br /><br /> RHEL 4 en SLES 9|Starten: **/etc/init d/ccmexecd start**<br /><br /> Stoppen: **/etc/init d/ccmexecd stop**<br /><br /> Opnieuw opstarten: **/etc/init d/ccmexecd restart**|  
|Solaris 9|Starten: **/etc/init d/ccmexecd start**<br /><br /> Stoppen: **/etc/init d/ccmexecd stop**<br /><br /> Opnieuw opstarten: **/etc/init d/ccmexecd restart**|  
|Solaris 10|Starten:<br /><br /> **svcadm inschakelen -s-svc: / management-toepassing/omniserver**<br /><br /> **svcadm inschakelen -s-svc: / management-toepassing/ccmexecd**<br /><br /> Stoppen:<br /><br /> **svcadm -s-svc uitschakelen: / management-toepassing/ccmexecd**<br /><br /> **svcadm -s-svc uitschakelen: / management-toepassing/omniserver**|  
|Solaris 11|Starten:<br /><br /> **svcadm inschakelen -s-svc: / management-toepassing/omniserver**<br /><br /> **svcadm inschakelen -s-svc: / management-toepassing/ccmexecd**<br /><br /> Stoppen:<br /><br /> **svcadm -s-svc uitschakelen: / management-toepassing/ccmexecd**<br /><br /> **svcadm -s-svc uitschakelen: / management-toepassing/omniserver**|  
|AIX|Starten:<br /><br /> **startsrc -s omniserver**<br /><br /> **startsrc -s ccmexec**<br /><br /> Stoppen:<br /><br /> **stopsrc -s ccmexec**<br /><br /> **stopsrc -s omniserver**|  
|HP-UX|Starten: **/sbin/init.d/ccmexecd start**<br /><br /> Stoppen: **/sbin/init.d/ccmexecd stop**<br /><br /> Opnieuw opstarten: **/sbin/init.d/ccmexecd restart**|  
