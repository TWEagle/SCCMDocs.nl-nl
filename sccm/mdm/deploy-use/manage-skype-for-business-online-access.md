---
title: Toegang tot Skype voor Bedrijven Online beheren
titleSuffix: Configuration Manager
description: Informatie over het beleid voor voorwaardelijke toegang gebruiken voor het beheren van toegang tot Skype voor bedrijven Online.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71c44250-626e-482c-8794-434c6aeb2fb1
caps.latest.revision: "6"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b7886d3e8f181d6d9316c5438dd948b21a658648
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-skype-for-business-online-access"></a>Toegang tot Skype voor Bedrijven Online beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Gebruik beleid voor voorwaardelijke toegang voor  **Skype voor Bedrijven Online** om toegang tot Skype voor Bedrijven Online in te stellen op basis van door u opgegeven voorwaarden.  


 Wanneer een gebruiker in de doelgroep probeert Skype voor Bedrijven Online te gebruiken op zijn of haar apparaat, wordt de volgende evaluatie uitgevoerd:![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>Vereisten  

-   Schakel moderne verificatie in voor Skype voor Bedrijven Online. Vul dit [Connect-formulier](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) in om u in te schrijven voor het programma voor moderne verificatie.  

-   Al uw eindgebruikers moeten gebruikmaken van Skype voor bedrijven Online. Als u een implementatie hebt met Skype voor bedrijven Online en Skype voor bedrijven on-premises, wordt beleid voor voorwaardelijke toegang niet worden toegepast op eindgebruikers.  

-   Het apparaat waarvoor u toegang tot Skype voor Bedrijven Online wilt inschakelen, moet:  

    -   Een Android- of iOS-apparaat zijn.  

    -   Ingeschreven zijn bij Intune.  

    -   Voldoen aan geïmplementeerd Intune-nalevingsbeleid.  

 De apparaatstatus wordt opgeslagen in Azure Active Directory, die toegang verleent of blokkeert op basis van de opgegeven voorwaarden.  
Als niet aan een voorwaarde wordt voldaan, krijgt de gebruiker een van de volgende berichten te zien wanneer deze zich aanmeldt:  

-   Als het apparaat niet is ingeschreven bij Intune of niet is geregistreerd bij Azure Active Directory, wordt een bericht weergegeven met instructies over het installeren van de bedrijfsportal-app en het inschrijven.  

-   Als het apparaat niet aan het beleid voldoet, wordt er een bericht weergegeven waarin de gebruiker naar de website van de Intune-bedrijfsportal of de bedrijfsportal-app wordt verwezen, waar informatie te vinden is over het probleem en hoe het kan worden opgelost.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Voorwaardelijke toegang configureren voor Skype voor Bedrijven Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Stap 1: Active Directory-beveiligingsgroepen configureren  
 Voordat u begint, moet u Azure Active Directory-beveiligingsgroepen configureren voor het beleid voor voorwaardelijke toegang. U kunt deze groepen configureren in het Office 365-beheercentrum. Deze groepen bevatten de gebruikers die deel uitmaken van de doelgroep, of op wie het beleid juist niet van toepassing is. Wanneer een gebruiker deel uitmaakt van de doelgroep voor het beleid, moet elk apparaat dat hij of zij gebruikt, aan het beleid voldoen om toegang te krijgen tot bronnen.  

 U kunt twee soorten groepen opgeven voor het Skype voor Bedrijven-beleid:  

-   Groepen â € gericht ' bevat groepen gebruikers waarop het beleid van toepassing  

-   Uitgesloten groepen â €' bevat groepen gebruikers die uitgesloten van het beleid (optioneel zijn)  
    Als een gebruiker zich in beide groepen bevindt, wordt het beleid niet op de gebruiker toegepast.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Stap 2: Configureer en implementeer een nalevingsbeleid  
 Zorg ervoor dat u een nalevingsbeleid maakt en implementeert op alle apparaten waarop het Skype voor Bedrijven Online-beleid van toepassing is.  

 Zie [Nalevingsbeleid voor apparaten beheren in System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md) voor meer informatie over het configureren van het nalevingsbeleid.  

> [!NOTE]  
>  Als u geen nalevingsbeleid hebt geïmplementeerd en u daarna het Skype voor Bedrijven Online-beleid inschakelt, krijgen alle apparaten uit de doelgroep toegang als ze zijn ingeschreven bij Intune.  

 Wanneer u klaar bent, gaat u door naar Stap 3.  

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Stap 3: Het Skype voor bedrijven Online-beleid configureren  
 Configureer vervolgens het beleid om ervoor te zorgen dat alleen beheerde apparaten en apparaten die aan het beleid voldoen toegang hebben tot Skype voor Bedrijven Online. Dit beleid wordt opgeslagen in Azure Active Directory.  

1.  Klik in de [Microsoft Intune-beheerconsole](https://manage.microsoft.com)op **Beleid** > **Voorwaardelijke toegang** > **Skype for Business Online Beleid**voor meer informatie over het configureren van het nalevingsbeleid.  

     ![ConditionalAccess&#95;SFBPolicy](media/ConditionalAccess_SFBPolicy.png)  

2.  Selecteer **Beleid voor voorwaardelijke toegang inschakelen**.  

3.  Onder **Toegang voor toepassingen**kunt u beleid voor voorwaardelijke toegang toepassen:  

    -   iOS  

    -   Android  

4.  Klik onder **Doelgroepen**op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop het beleid van toepassing moet zijn. U kunt ervoor kiezen dit op alle gebruikers of alleen op een bepaalde groep gebruikers toe te passen.  

5.  Klik desgewenst onder **Uitgesloten groepen**op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop dit beleid niet van toepassing is.  

6.  Wanneer u klaar bent, klikt u op **Opslaan**.  

 U hebt nu voorwaardelijke toegang voor Skype voor Bedrijven Online geconfigureerd. U hoeft het beleid voor voorwaardelijke toegang niet te implementeren; het wordt direct van kracht.  

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>De compatibiliteit en het beleid voor voorwaardelijke toegang bewaken  
 In de werkruimte Groepen kunt u de status voor voorwaardelijke toegang van uw apparaten bekijken.  

 Selecteer een groep mobiele apparaten en selecteer op het tabblad **Apparaten** een van de volgende **Filters**:  

-   **Apparaten die niet zijn geregistreerd bij AAD** â €' deze apparaten hebben geen toegang tot Skype voor bedrijven Online.  

-   **Apparaten die niet compatibel** â €' deze apparaten hebben geen toegang tot Skype voor bedrijven Online.  

-   **Apparaten die geregistreerd bij AAD en voldoen aan het beleid zijn** â €' deze apparaten hebben toegang tot Skype voor bedrijven Online.  

### <a name="see-also"></a>Zie tevens  

 [Nalevingsbeleid voor apparaten in System Center Configuration Manager beheren](../../protect/deploy-use/device-compliance-policies.md)
