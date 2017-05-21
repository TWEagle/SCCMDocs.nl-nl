---
title: Nalevingsbeleid voor apparaten | Microsoft-documenten
description: Informatie over het beheren van nalevingsbeleid in System Center Configuration Manager waarmee apparaten compatibel zijn met voorwaardelijke toegang beleidsregels.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
caps.latest.revision: 18
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bcaa2a9b5474e06bf344dc4fd47dbb160ea36297
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="device-compliance-policies-in-system-center-configuration-manager"></a>Nalevingsbeleid voor apparaten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

**Nalevingsbeleid** in System Center Configuration Manager bevat de regels en instellingen waaraan een apparaat moet voldoen om ook te voldoen door voorwaardelijke toegang beleid. U kunt ook nalevingsbeleid gebruiken om nalevingsproblemen met apparaten te bewaken en onafhankelijk van voorwaardelijke toegang op te lossen.  


> [!IMPORTANT]  
>  Dit artikel beschrijft het nalevingsbeleid voor apparaten die worden beheerd door Microsoft Intune.    Het nalevingsbeleid voor pc's die worden beheerd door System Center Configuration Manager wordt beschreven in [Toegang beheren tot O365-services voor pc's die worden beheerd door System Center Configuration Manager](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

 Deze regels omvatten vereisten zoals:  

-   PINCODE en wachtwoorden voor toegang tot een apparaat

-   Versleuteling van gegevens die zijn opgeslagen op het apparaat

-   Of het apparaat jailbroken of geroot is  

-   E-mail op het apparaat wordt beheerd door een Intune-beleid, of als het apparaat als beschadigd gemeld door de Windows-apparaat health attestation-service.
-   Apps die op het apparaat kunnen niet worden geïnstalleerd.


 U implementeert nalevingsbeleid bij gebruikersverzamelingen. Wanneer een nalevingsbeleid wordt geïmplementeerd voor een gebruiker, worden alle apparaten van de gebruiker gecontroleerd op naleving.  

 De volgende tabel bevat de apparaattypen die worden ondersteund door nalevingsbeleid en informatie over hoe niet-compatibele instellingen worden beheerd als het beleid wordt gebruikt met beleid voor voorwaardelijke toegang.  

|Regel|Windows 8.1 en hoger|Windows Phone 8.1 en hoger|iOS 6.0 en hoger|Android 4.0 en hoger Samsung KNOX Standard 4.0 of hoger, Android for Work|  
|----------|---------------------------|---------------------------------|-----------------------|---------------------------|-----------------------------------------|  
|**Configuratie van de PINCODE of wachtwoord**|Hersteld|Hersteld|Hersteld|In quarantaine|  
|**Apparaatversleuteling**|n.v.t.|Hersteld|Hersteld (door een pincode in te stellen)|In quarantaine<br>(Android for Work altijd versleuteld)|  
|**Opengebroken of geroot apparaat**|n.v.t.|n.v.t.|In quarantaine (geen instelling)|In quarantaine (geen instelling)|  
|**E-mailprofiel**|n.v.t.|n.v.t.|In quarantaine|n.v.t.|  
|**Minimale versie van het besturingssysteem**|In quarantaine|In quarantaine|In quarantaine|In quarantaine|  
|**Maximale versie van het besturingssysteem**|In quarantaine|In quarantaine|In quarantaine|In quarantaine|  
|**Apparaat Health Attestation (1602 update)**|De instelling is niet van toepassing op Windows 8.1<br /><br /> Windows 10 en Windows 10 Mobile zijn in quarantaine geplaatst.|n.v.t.|n.v.t.|n.v.t.|  
|**Apps die niet worden geïnstalleerd**|n.v.t.|n.v.t.|In quarantaine|In quarantaine|

 **Hersteld** : naleving wordt afgedwongen door het besturingssysteem van het apparaat (de gebruiker moet bijvoorbeeld een pincode instellen).  Het is dan nooit het geval dat de instelling niet aan de voorwaarden voldoet.  

 **In quarantaine** : het besturingssysteem van het apparaat dwingt geen naleving af (gebruikers hoeven hun Android-apparaat bijvoorbeeld niet per se te versleutelen).  In dat geval:  

-   Het apparaat wordt geblokkeerd als de gebruiker niet in naleving handelt van een beleid voor voorwaardelijke toegang.  

-   De bedrijfsportal of webportal stelt de gebruiker op de hoogte van nalevingsproblemen.  


### <a name="next-steps"></a>Volgende stappen  
[Maken en implementeren van een nalevingsbeleid voor apparaten](create-compliance-policy.md)
### <a name="see-also"></a>Zie tevens  
 [Toegang tot services in System Center Configuration Manager beheren](../../protect/deploy-use/manage-access-to-services.md)

