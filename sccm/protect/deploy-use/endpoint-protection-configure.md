---
title: Endpoint Protection configureren
titleSuffix: Configuration Manager
description: Informatie over het instellen van Configuration Manager om te werken en distribueren van malware-definities voor Windows Defender.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 9e54b433224b86650178b4df0cd6d0f2ab827b6c
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-endpoint-protection"></a>Endpoint Protection configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u Endpoint Protection gebruiken kunt voor het beheren van beveiliging en schadelijke software op clientcomputers van Configuration Manager, moet u de configuratiestappen uiteengezet in dit artikel uitvoeren.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Endpoint Protection configureren in Configuration Manager  
 Endpoint Protection in Configuration Manager heeft externe afhankelijkheden en afhankelijkheden binnen het product.  

### <a name="steps-to-configure-endpoint-protection-in-configuration-manager"></a>Stappen voor het configureren van Endpoint Protection in Configuration Manager  
 In de volgende tabel vindt u de stappen, gegevens en overige informatie voor het configureren van Endpoint Protection.  

> [!IMPORTANT]  
>  Als u endpoint protection voor Windows 10-computers beheren, moet u Configuration Manager om te werken en distribueren van malware-definities voor Windows Defender configureren. Windows Defender is opgenomen in Windows 10 SCEPInstall moet wel nog steeds geïnstalleerd en aangepaste clientinstellingen voor Endpoint Protection (**stap 5** hieronder) zijn nog steeds vereist. </br> </br>
> Vanaf Configuration Manager 1802, hoeft Windows 10-apparaten niet te hebben van de Endpoint Protection agent (SCEPInstall) is geïnstalleerd. Als deze al is geïnstalleerd op Windows 10-apparaten, wordt Configuration Manager niet verwijderd. Beheerders kunnen de Endpoint Protection-agent op Windows 10-apparaten die met ten minste de clientversie 1802 verwijderen. SCEPInstall.exe mogelijk nog steeds in C:\Windows\ccmsetup op sommige computers aanwezig, maar niet moeten worden gedownload op de nieuwe clientinstallaties. Aangepaste clientinstellingen voor Endpoint Protection (**stap 5** hieronder) zijn nog steeds vereist. <!--503654-->

|Stappen|Details|  
|-----------|-------------|  
|**Stap 1:** [Endpoint Protection-puntsitesysteemrol maken](endpoint-protection-site-role.md)|De sitesysteemrol Endpoint Protection-punt moet zijn geïnstalleerd voordat u Endpoint Protection kunt gebruiken. Het moet slechts op één sitesysteemserver en op het hoogste niveau in de hiërarchie op een centrale beheersite of een zelfstandige primaire site worden geïnstalleerd. |  
|**Stap 2:** [Waarschuwingen voor Endpoint Protection configureren](endpoint-configure-alerts.md)|Met waarschuwingen wordt de beheerder op de hoogte gebracht van specifieke gebeurtenissen die hebben plaatsgevonden, zoals een malware-infectie. Waarschuwingen worden weergegeven in het knooppunt **Waarschuwingen** van de werkruimte **Bewaking** of kunnen eventueel via e-mail naar de opgegeven gebruikers worden verzonden. |  
|**Stap 3:** [Definitie-updatebronnen configureren voor Endpoint Protection-clients](endpoint-definition-updates.md)|Endpoint Protection kan worden geconfigureerd voor het gebruik van verschillende bronnen voor het downloaden van definitie-updates. |  
|**Stap 4:** [Het standaard antimalwarebeleid configureren en aangepaste beleidsregels voor antimalware maken](endpoint-antimalware-policies.md)|Het standaard antimalwarebeleid wordt toegepast wanneer de Endpoint Protection-client is geïnstalleerd. Aangepaste beleidsregels die u hebt geïmplementeerd, worden standaard binnen 60 minuten na het implementeren van de client toegepast. Zorg ervoor dat u anti-malwarebeleid hebt geconfigureerd voordat u de Endpoint Protection-client implementeert. |  
|**Stap 5:** [Aangepaste clientinstellingen voor Endpoint Protection configureren](endpoint-protection-configure-client.md)|Aangepaste clientinstellingen gebruiken voor het configureren van Endpoint Protection-instellingen voor verzamelingen van computers in uw hiërarchie.<br /><br /> Opmerking: Configureer de standaardinstellingen van de Endpoint Protection-client niet tenzij u zeker dat u wilt dat deze instellingen worden toegepast op alle computers in uw hiërarchie. |  
