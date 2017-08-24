---
title: Toegang tot Dynamics CRM Online beheren | Microsoft Docs
description: Ontdek hoe u toegang tot Microsoft Dynamics CRM Online beheren vanaf iOS- en Android-apparaten met Microsoft Intune voorwaardelijke toegang.
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bfc4c51-b25c-4c70-b81e-8a3b6ddf02c8
caps.latest.revision: "5"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: bd00f12ae3bc14a34d24c22c3d5277d275d51e85
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-dynamics-crm-online-access-in-system-center-configuration-manager"></a>Dynamics CRM Online-toegang in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt toegang tot Microsoft Dynamics CRM Online beheren vanaf iOS- en Android-apparaten met Microsoft Intune voorwaardelijke toegang.  Voorwaardelijke toegang van Intune bestaat uit twee onderdelen:
* [Nalevingsbeleid voor apparaten](../../protect/deploy-use/device-compliance-policies.md) dat het apparaat voldoen moet om als compatibel worden beschouwd.
* [Beleid voor voorwaardelijke toegang](../../protect/deploy-use/manage-access-to-services.md) die waarin u de voorwaarden opgeeft waaraan het apparaat voldoen moet om toegang tot de service.

Lees voor meer informatie over hoe voorwaardelijke toegang werkt de [toegang tot services beheren](../../protect/deploy-use/manage-access-to-services.md) artikel.


Wanneer een gebruiker in de doelgroep probeert de Dynamics CRM-app op hun apparaat gebruiken, wordt de volgende evaluatie uitgevoerd:

![Het diagram geeft de beslissingspunten die wordt gebruikt om te bepalen of een apparaat toegang tot een service is toegestaan of geblokkeerd](media/mdm-ca-dynamics-crm-flow-diagram.png)

Het apparaat waarvoor toegang tot Dynamics CRM Online moet:
* Worden een **Android** of **iOS** apparaat.
* Worden **ingeschreven** met Microsoft Intune.
* Worden **compatibele** aan geïmplementeerd Microsoft Intune-nalevingsbeleid.

De apparaatstatus wordt opgeslagen in Azure Active Directory, die toegang verleent of blokkeert op basis van de opgegeven voorwaarden.

Als niet aan een voorwaarde wordt voldaan, krijgt de gebruiker een van de volgende berichten te zien wanneer deze zich aanmeldt:
* Als het apparaat niet is ingeschreven bij Microsoft Intune of niet is geregistreerd in Azure Active Directory, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en het inschrijven.
* Als het apparaat niet compatibel is, wordt een bericht weergegeven waarin de gebruiker naar de website van Microsoft Intune-bedrijfsportal of de bedrijfsportal-app wordt verwezen waar ze informatie over het probleem en herstel kunnen vinden.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Configureren van voorwaardelijke toegang voor Dynamics CRM Online  
### <a name="step-1-configure-active-directory-security-groups"></a>Stap 1: Active Directory-beveiligingsgroepen configureren

Voordat u begint, moet u Azure Active Directory-beveiligingsgroepen configureren voor het beleid voor voorwaardelijke toegang. U kunt deze groepen configureren in de **Office 365-beheercentrum**. Deze groepen worden gebruikt voor het doel of uitgesloten gebruikers uit het beleid. Wanneer een gebruiker deel uitmaakt van de doelgroep voor het beleid, moet elk apparaat dat hij of zij gebruikt, aan het beleid voldoen om toegang te krijgen tot bronnen.

U kunt twee soorten groepen gebruiken voor het beleid voor Dynamics CRM opgeven:
* **Doelgroepen** : bevat groepen gebruikers waarop het beleid van toepassing.
* **Uitgesloten groepen** : bevat groepen gebruikers die uitgesloten van het beleid zijn.

Als een gebruiker zich in beide groepen bevindt, wordt het beleid niet op de gebruiker toegepast.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Stap 2: Configureer en implementeer een nalevingsbeleid
[Maken en implementeren van](../../protect/deploy-use/device-compliance-policies.md) nalevingsbeleid op alle apparaten die worden beïnvloed door het beleid. Dit zijn alle apparaten die worden gebruikt door de gebruikers in doelgroepen.

> [!NOTE]
> Terwijl nalevingsbeleid wordt geïmplementeerd voor Microsoft Intune-groepen, worden de beleidsregels voor voorwaardelijke toegang gericht op Azure Active Directory-beveiligingsgroepen.

> [!IMPORTANT]
> Als u geen nalevingsbeleid hebt geïmplementeerd, wordt de apparaten die als compatibel worden beschouwd.

Wanneer u klaar bent, gaat u door naar Stap 3.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>Stap 3: Het beleid voor Dynamics CRM configureren
Configureer vervolgens het beleid om ervoor te zorgen dat alleen beheerde en compatibele apparaten toegang hebben tot Dynamics CRM. Dit beleid wordt opgeslagen in Azure Active Directory.

1.  Kies in de Microsoft Intune-beheerconsole **beleid > voorwaardelijke toegang > beleid voor Dynamics CRM Online**.

     ![Schermafbeelding van de pagina Dynamics CRM Online voorwaardelijk beleid](media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Selecteer **inschakelen van voorwaardelijke toegang** beleid.
3.  Onder **Toegang voor toepassingen**kunt u beleid voor voorwaardelijke toegang toepassen:
  * **iOS**
  * **Android**
4.  Onder **doelgroepen**, kies **wijzigen** selecteren van de Azure Active Directory-beveiligingsgroepen waarop het beleid van toepassing. U kunt ervoor kiezen dit op alle gebruikers of alleen op een bepaalde groep gebruikers toe te passen.
5.  Onder **uitgesloten groepen**desgewenst kiezen **wijzigen** selecteren van de Azure Active Directory-beveiligingsgroepen die uitgesloten van dit beleid zijn.
6.  Als u klaar bent, kiest u **opslaan**.

U hebt nu voorwaardelijke toegang voor Dynamics CRM geconfigureerd. U hoeft het beleid voor voorwaardelijke toegang niet te implementeren; het wordt direct van kracht.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>De compatibiliteit en het beleid voor voorwaardelijke toegang bewaken

In de **groepen** werkruimte kunt u de status voor voorwaardelijke toegang van uw apparaten bekijken.

Selecteer een groep mobiele apparaten en selecteer op het tabblad **Apparaten** een van de volgende **Filters**:
* **Apparaten die niet zijn geregistreerd bij AAD** : deze apparaten hebben geen toegang tot Dynamics CRM.
* **Apparaten die niet compatibel** : deze apparaten hebben geen toegang tot Dynamics CRM.
* **Apparaten die geregistreerd bij AAD en voldoen aan het beleid zijn** : deze apparaten hebben toegang tot Dynamics CRM.

###  <a name="see-also"></a>Zie tevens
[Toegang tot e-mail beheren](../../protect/deploy-use/manage-email-access.md)

[Toegang tot SharePoint Online beheren](../../protect/deploy-use/manage-sharepoint-online-access.md)

[Toegang tot Skype voor bedrijven Online beheren](../../protect/deploy-use/manage-skype-for-business-online-access.md)
