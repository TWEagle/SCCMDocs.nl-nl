---
title: Dynamics CRM Online toegang beheren | Microsoft-documenten
description: Leer hoe u toegang tot Microsoft Dynamics CRM Online beheren vanuit iOS en Android-apparaten met voorwaardelijke toegang voor Microsoft Intune.
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bfc4c51-b25c-4c70-b81e-8a3b6ddf02c8
caps.latest.revision: 5
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: bd00f12ae3bc14a34d24c22c3d5277d275d51e85
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-dynamics-crm-online-access-in-system-center-configuration-manager"></a>Dynamics CRM Online toegang in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt toegang tot Microsoft Dynamics CRM Online beheren van iOS en Android-apparaten met voorwaardelijke toegang voor Microsoft Intune.  Voorwaardelijke toegang voor Intune bestaat uit twee onderdelen:
* [Nalevingsbeleid voor apparaten](../../protect/deploy-use/device-compliance-policies.md) dat het apparaat voldoen moet om ook te voldoen.
* [Beleid voor voorwaardelijke toegang](../../protect/deploy-use/manage-access-to-services.md) die waar u de voorwaarden specificeren waaraan het apparaat moet voldoen aan voor toegang tot de service.

Lees voor meer informatie over hoe voorwaardelijke toegang werkt de [toegang tot services beheren](../../protect/deploy-use/manage-access-to-services.md) artikel.


Wanneer een gebruiker in de doelgroep probeert te gebruiken van de Dynamics CRM-app op hun apparaat, wordt de volgende evaluatie uitgevoerd:

![Diagram van de beschikking punten gebruikt om te bepalen of een apparaat toegang tot een service wordt toegestaan of geblokkeerd weergeven](media/mdm-ca-dynamics-crm-flow-diagram.png)

Moet het apparaat waarvoor u toegang tot Dynamics CRM Online:
* Worden een **Android** of **iOS** apparaat.
* Worden **ingeschreven** met Microsoft Intune.
* Worden **compatibel** geïmplementeerd met een nalevingsbeleid van Microsoft Intune.

De apparaatstatus wordt opgeslagen in Azure Active Directory, die toegang verleent of blokkeert op basis van de opgegeven voorwaarden.

Als niet aan een voorwaarde wordt voldaan, krijgt de gebruiker een van de volgende berichten te zien wanneer deze zich aanmeldt:
* Als het apparaat niet bij Microsoft Intune ingeschreven is of is niet geregistreerd in Azure Active Directory, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en registreren.
* Als het apparaat niet compatibel is, wordt een bericht weergegeven waarin stelt de gebruiker naar de website van Microsoft Intune-bedrijfsportal of de bedrijfsportal-app wanneer ze informatie over het probleem en het herstellen van deze kunnen vinden.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Voorwaardelijke toegang configureren voor Dynamics CRM Online  
### <a name="step-1-configure-active-directory-security-groups"></a>Stap 1: Active Directory-beveiligingsgroepen configureren

Voordat u begint, moet u Azure Active Directory-beveiligingsgroepen configureren voor het beleid voor voorwaardelijke toegang. U kunt deze groepen configureren in de **Office 365-beheercentrum**. Deze groepen zal worden gebruikt voor het doel of uitgesloten gebruikers uit het beleid. Wanneer een gebruiker deel uitmaakt van de doelgroep voor het beleid, moet elk apparaat dat hij of zij gebruikt, aan het beleid voldoen om toegang te krijgen tot bronnen.

U kunt twee soorten groepen gebruiken voor het beleid Dynamics CRM opgeven:
* **Doelgroepen** – gebruikersgroepen waarop het beleid van toepassing bevat.
* **Uitgesloten groepen** – dit zijn groepen gebruikers die uitgesloten van het beleid zijn.

Als een gebruiker zich in beide groepen bevindt, wordt het beleid niet op de gebruiker toegepast.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Stap 2: Configureer en implementeer een nalevingsbeleid
[Maken en implementeren van](../../protect/deploy-use/device-compliance-policies.md) een nalevingsbeleid op alle apparaten die worden beïnvloed door het beleid. Deze moeten de apparaten die worden gebruikt door de gebruikers in de doel-groepen.

> [!NOTE]
> Terwijl nalevingsbeleid wordt geïmplementeerd voor Microsoft Intune-groepen, worden de beleidsregels voor voorwaardelijke toegang gericht op Azure Active Directory-beveiligingsgroepen.

> [!IMPORTANT]
> Als u geen nalevingsbeleid hebt geïmplementeerd, worden de apparaten behandeld als compatibel.

Wanneer u klaar bent, gaat u door naar Stap 3.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>Stap 3: Dynamics CRM-beleid configureren
Vervolgens configureert u het beleid om te vereisen dat alleen beheerde en compatibele apparaten toegang hebben tot Dynamics CRM. Dit beleid wordt opgeslagen in Azure Active Directory.

1.  Kies in de Microsoft Intune-beheerconsole **beleid > voorwaardelijke toegang > Dynamics CRM Online-beleid**.

     ![Schermafbeelding van de Dynamics CRM Online-beleid pagina voor voorwaardelijke toegang](media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Selecteer **voorwaardelijke toegang inschakelen** beleid.
3.  Onder **Toegang voor toepassingen**kunt u beleid voor voorwaardelijke toegang toepassen:
  * **iOS**
  * **Android**
4.  Onder **doelgroepen**, kies **wijzigen** om te selecteren van de Azure Active Directory-beveiligingsgroepen waarop het beleid toepast. U kunt ervoor kiezen dit op alle gebruikers of alleen op een bepaalde groep gebruikers toe te passen.
5.  Onder **uitgesloten groepen**desgewenst kiezen **wijzigen** om te selecteren van de Azure Active Directory-beveiligingsgroepen waarop dit beleid niet van toepassing.
6.  Als u klaar bent, kiest u **opslaan**.

Voorwaardelijke toegang is nu geconfigureerd voor Dynamics CRM. U hoeft het beleid voor voorwaardelijke toegang niet te implementeren; het wordt direct van kracht.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>De compatibiliteit en het beleid voor voorwaardelijke toegang bewaken

In de **groepen** werkruimte kunt u de status voor voorwaardelijke toegang van uw apparaten bekijken.

Selecteer een groep mobiele apparaten en selecteer op het tabblad **Apparaten** een van de volgende **Filters**:
* **Apparaten die niet zijn geregistreerd bij AAD** – deze apparaten hebben geen toegang tot Dynamics CRM.
* **Apparaten die niet compatibel zijn** – deze apparaten hebben geen toegang tot Dynamics CRM.
* **Apparaten die geregistreerd bij AAD en compatibel zijn** – deze apparaten krijgen toegang tot Dynamics CRM.

###  <a name="see-also"></a>Zie tevens
[Toegang tot e-mail beheren](../../protect/deploy-use/manage-email-access.md)

[Toegang tot SharePoint Online beheren](../../protect/deploy-use/manage-sharepoint-online-access.md)

[Toegang tot Skype voor bedrijven Online beheren](../../protect/deploy-use/manage-skype-for-business-online-access.md)

