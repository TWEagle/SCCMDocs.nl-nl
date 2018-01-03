---
title: Toegang tot Skype voor Bedrijven Online beheren
titleSuffix: Configuration Manager
description: Informatie over het beleid voor voorwaardelijke toegang gebruiken voor het beheren van toegang tot Skype voor bedrijven Online.
ms.custom: na
ms.date: 12/22/2017
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
ms.openlocfilehash: 3c1d0c84dc28fb886048cf8d7ea310c2b4dfc4aa
ms.sourcegitcommit: 92c3f916e6bbd35b6208463ff406e0247664543a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/02/2018
---
# <a name="manage-skype-for-business-online-access"></a>Toegang tot Skype voor Bedrijven Online beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Beleid voor voorwaardelijke toegang voor Skype voor bedrijven Online gebruiken voor het beheren van toegang tot Skype voor bedrijven Online op basis van door u opgegeven voorwaarden.  


 Wanneer een gebruiker in de doelgroep probeert Skype voor Bedrijven Online te gebruiken op zijn of haar apparaat, wordt de volgende evaluatie uitgevoerd:![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>Vereisten  

-   Schakel [moderne verificatie](https://aka.ms/SkypeModernAuth) voor Skype voor bedrijven Online.   

-   Alle gebruikers moet Skype voor bedrijven Online gebruiken. Als u een implementatie hebt met Skype voor bedrijven Online en Skype voor bedrijven on-premises, geldt beleid voor voorwaardelijke toegang niet voor on-premises gebruikers.  

-   Het apparaat waarvoor u toegang tot Skype voor Bedrijven Online wilt inschakelen, moet:  

    -   Een Android- of iOS-apparaat

    -   Zijn ingeschreven bij Microsoft Intune

    -   Voldoen aan geïmplementeerd Microsoft Intune-nalevingsbeleid

 Azure Active Directory slaat de status van het apparaat, die verleent of blokkeert de toegang op basis van de door u opgegeven voorwaarden.  
Als niet aan een voorwaarde wordt voldaan, ziet de gebruiker een van de volgende berichten te zien wanneer deze zich aanmeldt:  

-   Als het apparaat niet is ingeschreven bij Microsoft Intune of niet is geregistreerd in Azure Active Directory, ziet de gebruiker instructies over het installeren van de bedrijfsportal-app en het inschrijven.  

-   Als het apparaat niet compatibel is, ziet de gebruiker een bericht waarin ze worden omgeleid naar de bedrijfsportal-website of de bedrijfsportal-app. De bedrijfsportal bevat informatie over het probleem en hoe worden opgelost.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Voorwaardelijke toegang configureren voor Skype voor Bedrijven Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Stap 1: Active Directory-beveiligingsgroepen configureren  
 Voordat u begint, moet u Azure Active Directory-beveiligingsgroepen configureren voor het beleid voor voorwaardelijke toegang. Deze groepen configureren in het Office 365-beheercentrum. Deze groepen bevatten de gebruikers wilt richten of uitsluiten van het beleid. Wanneer een gebruiker deel uitmaakt van de doelgroep voor het beleid, moet elk apparaat dat hij of zij gebruikt, aan het beleid voldoen om toegang te krijgen tot bronnen.  

 U kunt twee soorten groepen opgeven voor het Skype voor Bedrijven-beleid:  

-   **Doelgroepen** bevatten gebruikers waarop het beleid van toepassing is  

-   **Uitgesloten groepen** gebruikers moeten worden uitgesloten van het beleid bevatten  
    Als een gebruiker zich in beide groepen bevindt, zijn deze uitgesloten.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Stap 2: Configureer en implementeer een nalevingsbeleid  
 Maak en implementeer een nalevingsbeleid op alle apparaten waarop het Skype voor bedrijven Online-beleid is gericht.  

 Zie voor meer informatie over het configureren van het nalevingsbeleid [nalevingsbeleid voor apparaten beheren](../../protect/deploy-use/device-compliance-policies.md).  

> [!NOTE]  
>  Als u geen nalevingsbeleid hebt geïmplementeerd en daarna het Skype voor bedrijven Online-beleid inschakelt, zijn alle apparaten toegang toegestaan als ze zijn ingeschreven bij Microsoft Intune.  


### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Stap 3: Het Skype voor bedrijven Online-beleid configureren  
 Configureer het beleid om ervoor te zorgen dat alleen beheerde en compatibele apparaten toegang tot Skype voor bedrijven Online. Dit beleid wordt opgeslagen in Azure Active Directory.  

1.  Klik in de [Microsoft Intune-beheerconsole](https://manage.microsoft.com)op **Beleid** > **Voorwaardelijke toegang** > **Skype for Business Online Beleid**voor meer informatie over het configureren van het nalevingsbeleid.  

     ![ConditionalAccess&#95;SFBPolicy](media/ConditionalAccess_SFBPolicy.png)  

2.  Selecteer **Beleid voor voorwaardelijke toegang inschakelen**.  

3.  Onder **Toegang voor toepassingen**kunt u beleid voor voorwaardelijke toegang toepassen:  

    -   iOS  

    -   Android  

4.  Onder **doelgroepen**, klikt u op **wijzigen** selecteren van de Azure Active Directory-beveiligingsgroepen waarop het beleid van toepassing is. U kunt dit beleid op alle gebruikers of alleen op bepaalde groepen gebruikers.  

5.  Klik desgewenst onder **Uitgesloten groepen**op **Wijzigen** om de Active Directory-beveiligingsgroepen te selecteren waarop dit beleid niet van toepassing is.  

6.  Wanneer u klaar bent, klikt u op **Opslaan**.  

 U hebt nu voorwaardelijke toegang voor Skype voor Bedrijven Online geconfigureerd. U hoeft het beleid voor voorwaardelijke toegang niet te implementeren; het wordt direct van kracht.  

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>De compatibiliteit en het beleid voor voorwaardelijke toegang bewaken  
 In de werkruimte Groepen kunt u de status voor voorwaardelijke toegang van uw apparaten bekijken.  

 Selecteer een groep mobiele apparaten en selecteer op het tabblad **Apparaten** een van de volgende **Filters**:  

-   **Apparaten die niet zijn geregistreerd bij AAD** geen toegang tot Skype voor bedrijven Online

-   **Apparaten die niet compatibel** geen toegang tot Skype voor bedrijven Online  

-   **Apparaten die geregistreerd bij AAD en voldoen aan het beleid zijn** hebben toegang tot Skype voor bedrijven Online  

### <a name="see-also"></a>Zie tevens  

 [Nalevingsbeleid voor apparaten in System Center Configuration Manager beheren](../../protect/deploy-use/device-compliance-policies.md)
