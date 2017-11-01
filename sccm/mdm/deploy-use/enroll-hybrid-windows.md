---
title: Hybride Apparaatbeheer van Windows met Microsoft Intune instellen
titleSuffix: Configuration Manager
description: Windows Apparaatbeheer met System Center Configuration Manager en Microsoft Intune instellen.
ms.custom: na
ms.date: 03/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dc1f70f5-64ab-42ab-aa91-d3858803e12f
caps.latest.revision: "9"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: dd62748f853915d71fcbad1964f5a67785aaf3f6
ms.sourcegitcommit: 1132886e07d0c0a87dcc7eeef4577dd8d8840023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/01/2017
---
# <a name="set-up-windows-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride beheer van Windows-apparaten met System Center Configuration Manager en Microsoft Intune instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp wordt uitgelegd IT-beheerders hoe ze hun gebruikers brengt van Windows-pc's en mobiele apparaten onder beheer met Configuration Manager en Microsoft Intune kunnen inschakelen.

## <a name="enable-windows-device-management"></a>Schakel het beheer van Windows-apparaten
Gebruik de volgende stappen zodat Windows-Apparaatbeheer voor pc's of mobiele apparaten:

1.  Voordat u inschrijven voor elk platform hebt ingesteld, voldoen aan de vereisten en procedures in [Setup hybride MDM](setup-hybrid-mdm.md).  
2.  In de Configuration Manager-console in de **beheer** werkruimte, gaat u naar **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen**.  
3.  Klik in het lint op **Platforms configureren**, en selecteer vervolgens het Windows-platform:
    - **Windows** voor Windows-pc's en laptops, voert u de volgende stappen uit:
      1. In de **algemene** en klik op de **Windows-registratie inschakelen** selectievakje.
      2. Als u een certificaat om de code ondertekenen en implementeren van de bedrijfsportal-app, bladert u naar de **certificaat voor ondertekening van Code**. Gebruikers van apparaten kunnen ook de bedrijfsportal-app installeren vanuit de Windows Store of u kunt de app uit de Windows Store voor bedrijven implementeren zonder de ondertekening van programmacode.
      3. U kunt ook configureren [Windows Hello voor bedrijven-instellingen](windows-hello-for-business-settings.md).
    - **Windows Phone** voor Windows Phone-telefoons en tablets, voert u de volgende stappen uit:
      1. In de **algemene** en klik op de **Windows Phone 8.1 en Windows 10 Mobile** selectievakje. Windows Phone 8.0 niet meer wordt ondersteund.
      2. Als uw organisatie bedrijfs-apps sideloaden moet, kunt u de vereiste token of het bestand uploaden. Zie voor meer informatie over sideloadapps [maken van Windows-apps](https://docs.microsoft.com/sccm/apps/get-started/creating-windows-applications).
        - **Token voor toepassingsinschrijving**
        - **PFX-bestand**
        - **Geen** als u een Symantec-certificaat gebruikt, kunt u opgeven **waarschuwing weergeven voordat het Symantec-certificaten verlopen**.
4. Klik op **OK** om het dialoogvenster te sluiten.  Om te vereenvoudigen het inschrijvingsproces via de bedrijfsportal, moet u een DNS-alias voor apparaatinschrijving maken. U kunt vervolgens hoe gebruikers hun apparaten kunnen inschrijven.

## <a name="choose-how-to-enroll-windows-devices"></a>Kiezen hoe Windows-apparaten inschrijven

Nadat u Intune-licenties aan gebruikers hebt toegewezen, Windows-apparaten kunnen worden ingeschreven zonder eventuele extra stappen, maar u kunt registratie eenvoudiger maken voor gebruikers.

Twee factoren bepalen hoe u de inschrijving van Windows-apparaten kunt vereenvoudigen:
- **Gebruikt u Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) is opgenomen in de Enterprise Mobility + Security en andere licentieverlening plannen.
- **Welke versies van Windows-clients zich inschrijven?** <br>Windows 10-apparaten kunnen automatisch registreren door een account voor werk of school toe te voegen. Eerdere versies moeten inschrijven via de bedrijfsportal-app.

||**Azure AD Premium**|**Andere AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatische inschrijving](#enable-windows-10-automatic-enrollment) |[Gebruikersinschrijving](#enable-windows-enrollment-without-azure-ad-premium)|
|**Eerdere versies van Windows**|[Gebruikersinschrijving](#enable-windows-enrollment-without-azure-ad-premium)|[Gebruikersinschrijving](#enable-windows-enrollment-without-azure-ad-premium)|

## <a name="enable-windows-10-automatic-enrollment"></a>Automatische inschrijving van Windows 10 inschakelen

Automatische inschrijving kan gebruikers die eigendom van het bedrijf of persoonlijk Windows 10-computers en Windows 10 mobiele apparaten in Intune inschrijven met een account voor werk of school toevoegen en ermee akkoord dat worden beheerd. Eenvoudig. Op de achtergrond van de gebruiker-apparaat registreert en lid wordt van Azure Active Directory. Na de registratie, het apparaat wordt beheerd met Intune.

**Vereisten**
- Azure Active Directory Premium-abonnement ([proefabonnement](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-abonnement


### <a name="configure-automatic-mdm-enrollment"></a>Configureren van automatische MDM-inschrijving

1. Aanmelden bij de [Azure-beheerportal](https://portal.azure.com) (https://manage.windowsazure.com) en selecteer **Azure Active Directory**.

  ![Schermafbeelding van de Azure portal](../media/auto-enroll-azure-main.png)

2. Selecteer **Mobility (MDM- en MAM)**.

  ![Schermafbeelding van de Azure portal](../media/auto-enroll-mdm.png)

3. Selecteer **Microsoft Intune**.

  ![Schermafbeelding van de Azure portal](../media/auto-enroll-intune.png)

4. Configureer **MDM gebruiker bereik**. Geef op welke gebruikers apparaten moeten worden beheerd door Microsoft Intune. Deze gebruikers Windows 10-apparaten worden automatisch geregistreerd voor beheer met Microsoft Intune.

    - **Geen**
    - **Sommige**
    - **Alle**

   ![Schermafbeelding van de Azure portal](../media/auto-enroll-scope.png)

5. Gebruik de standaardwaarden voor de volgende URL's:
    - **MDM-voorwaarden van de URL voor gebruik**
    - **MDM-detectie-URL**
    - **MDM-URL voor naleving**

6. Selecteer **opslaan**.


Verificatie met twee factoren is standaard niet ingeschakeld voor de service. Tweeledige verificatie wordt echter aanbevolen bij het registreren van een apparaat. Voordat u verificatie met twee factoren voor deze service, moet u een provider voor verificatie met twee factoren configureren in Azure Active Directory en uw gebruikersaccounts voor multi-factor authentication configureren. Zie [aan de slag met de Azure multi-factor Authentication-Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Inschrijving van Windows zonder Azure AD Premium inschakelen
U kunt gebruikers registreren hun apparaten zonder automatische inschrijving van Azure AD Premium. Zodra u licenties wilt toewijzen, kunnen gebruikers registreren na een werkaccount toe te voegen aan hun apparaten persoonlijk eigendom zijn of hun apparaten in Bedrijfseigendom toevoegen aan uw Azure AD. Door een DNS-gemakkelijker alias (CNAME-recordtype) voor gebruikers hun apparaten kunnen inschrijven. Als u DNS CNAME-bronrecords maakt, kunnen gebruikers verbinding maken en zich inschrijven bij Intune zonder invoeren van de naam van de Intune-server.

### <a name="create-cnames-to-simplify-enrollment"></a>CNAME-records om te vereenvoudigen inschrijving maken
Maak DNS CNAME-bronrecords voor uw bedrijfsdomein. Bijvoorbeeld, als de website van uw bedrijf contoso.com is, zou u een CNAME in DNS die enterpriseenrollment.contoso.com omleidt naar enterpriseenrollment-s.manage.microsoft.com.

Hoewel het maken van DNS CNAME-vermeldingen is optioneel, eenvoudiger CNAME-records inschrijven voor gebruikers. Als geen inschrijving CNAME-record wordt gevonden, worden gebruikers gevraagd om handmatig de MDM-servernaam in enrollment.manage.microsoft.com.

|Type|Hostnaam|Verwijst naar|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.bedrijfsdomein.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 uur|

Als er meer dan één UPN-achtervoegsel, moet u een CNAME voor elke domeinnaam maken en wijst u elk criterium naar EnterpriseEnrollment-s.manage.microsoft.com. Bijvoorbeeld, als gebruikers bij Contoso gebruiken name@contoso.com, maar ook name@us.contoso.com, en name@eu.constoso.com als hun e-mailadres/UPN, admin Contoso DNS zou moeten maken van het volgen van CNAMEs.

|Type|Hostnaam|Verwijst naar|TTL|  
|----------|---------------|---------------|---|
|CNAME|Omleid|EnterpriseEnrollment-s.manage.microsoft.com|1 uur|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 uur|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 uur|

`EnterpriseEnrollment-s.manage.microsoft.com`– Biedt ondersteuning voor een omleiding naar de Intune-service met domeinerkenning van de domeinnaam van het e-mailadres van

Wijzigingen in DNS-records kunnen worden doorgegeven 72 uur duren. U kunt de DNS-wijziging in Intune kan niet controleren, totdat de DNS-record is doorgegeven.

## <a name="tell-users-how-to-enroll-devices"></a>Vertel gebruikers hoe apparaten inschrijven  

 Zodra u alles hebt ingesteld, moet u uw gebruikers laten weten hoe ze hun apparaten moeten inschrijven. Zie [wat u uw eindgebruikers vertelt over het inschrijven van hun apparaten](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) voor hulp. U kunt gebruikers verwijzen naar [uw Windows-apparaat inschrijven bij Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

> [!div class="button"]
[< Vorige stap](create-service-connection-point.md)[volgende stap >  ](set-up-additional-management.md)
