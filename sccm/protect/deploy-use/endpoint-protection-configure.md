---
title: Configureren van Endpoint Protection | Microsoft-documenten
description: Informatie over het instellen van Configuration Manager om te werken en distribueren van malware-definities voor Windows Defender.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a8218e23743dafaf8ff1166142cf2dcca1212133
ms.openlocfilehash: 6917644d6719a1ca636713aa5aebf277927123c8
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="configure-endpoint-protection"></a>Endpoint Protection configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u Endpoint Protection gebruiken kunt voor het beheren van beveiliging en schadelijke software op clientcomputers van Configuration Manager, moet u de configuratiestappen in dit onderwerp beschreven uitvoeren.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Endpoint Protection configureren in Configuration Manager  
 Endpoint Protection in Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product.  

### <a name="steps-to-configure-endpoint-protection-in-configuration-manager"></a>Stappen voor het configureren van Endpoint Protection in Configuration Manager  
 In de volgende tabel vindt u de stappen, gegevens en overige informatie voor het configureren van Endpoint Protection.  

> [!IMPORTANT]  
>  Als u endpoint protection voor Windows 10-computers beheert, moet u Configuration Manager om te werken en distribueren van malware-definities voor Windows Defender configureren. Windows Defender is opgenomen in Windows 10 maar SCEPInstall moet nog steeds geïnstalleerd en aangepaste clientinstellingen voor Endpoint Protection (**stap 5** hieronder) zijn nog steeds vereist.  

|Stappen|Details|  
|-----------|-------------|  
|**Stap 1:** [Endpoint Protection-puntsitesysteemrol maken](endpoint-protection-site-role.md)|De sitesysteemrol Endpoint Protection-punt moet zijn geïnstalleerd voordat u Endpoint Protection kunt gebruiken. Het moet slechts op één sitesysteemserver en op het hoogste niveau in de hiërarchie op een centrale beheersite of een zelfstandige primaire site worden geïnstalleerd. |  
|**Stap 2:** [Waarschuwingen voor Endpoint Protection configureren](endpoint-configure-alerts.md)|Met waarschuwingen wordt de beheerder op de hoogte gebracht van specifieke gebeurtenissen die hebben plaatsgevonden, zoals een malware-infectie. Waarschuwingen worden weergegeven in het knooppunt **Waarschuwingen** van de werkruimte **Bewaking** of kunnen eventueel via e-mail naar de opgegeven gebruikers worden verzonden. |  
|**Stap 3:** [Definitie-updatebronnen configureren voor Endpoint Protection-clients](endpoint-definition-updates.md)|Endpoint Protection kan worden geconfigureerd voor het gebruik van verschillende bronnen definitieupdates te downloaden. |  
|**Stap 4:** [Het standaard anti-malwarebeleid configureren en aangepaste beleidsregels voor antimalware te maken](endpoint-antimalware-policies.md)|Het standaard anti-malware-beleid wordt toegepast wanneer de Endpoint Protection-client is geïnstalleerd. Aangepaste beleidsregels die u hebt geïmplementeerd, worden standaard binnen 60 minuten na het implementeren van de client toegepast. Zorg ervoor dat u regels voor antimalwarebeleid hebt geconfigureerd voordat u de Endpoint Protection-client implementeren. |  
|**Stap 5:** [Aangepaste clientinstellingen voor Endpoint Protection configureren](endpoint-protection-configure-client.md)|Aangepaste clientinstellingen gebruiken voor het configureren van Endpoint Protection-instellingen voor verzamelingen van computers in uw hiërarchie.<br /><br /> Opmerking: De standaardinstellingen van de Endpoint Protection-client niet configureren tenzij u zeker dat u deze instellingen toegepast op alle computers in uw hiërarchie zijn. |  
