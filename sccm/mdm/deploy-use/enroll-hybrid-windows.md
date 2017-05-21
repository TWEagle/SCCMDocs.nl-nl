---
title: Windows hybride device management met System Center Configuration Manager en Microsoft Intune instellen | Microsoft-documenten
description: Windows device management met System Center Configuration Manager en Microsoft Intune instellen.
ms.custom: na
ms.date: 03/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dc1f70f5-64ab-42ab-aa91-d3858803e12f
caps.latest.revision: 9
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 329de5ffb6eb1403c02cd1db634c32f045e82488
ms.openlocfilehash: 47348baeac26bfa2ad5016622fe4dbcb9f572483
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-windows-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybride beheer van Windows-apparaten met System Center Configuration Manager en Microsoft Intune instellen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp wordt uitgelegd IT-beheerders hoe ze hun gebruikers om Windows-pc's en mobiele apparaten te beheren met Configuratiebeheer en Microsoft Intune kunnen inschakelen.

## <a name="enable-windows-device-management"></a>Schakel beheer van Windows-apparaten
Als Windows device management voor pc's of mobiele apparaten inschakelen, gebruikt u de volgende stappen uit:

1.  Voordat u een registratie voor elk platform instelt, voldoen aan de vereisten en de procedures in [Setup hybride MDM](setup-hybrid-mdm.md).  
2.  In de Configuration Manager-console in de **beheer** werkruimte, Ga naar **overzicht** > **Cloudservices** > **Microsoft Intune-abonnementen**.  
3.  Klik in het lint op **Platforms configureren**, en selecteer vervolgens het Windows-platform:
    - **Windows** voor Windows-pc's en laptops, voert u de volgende stappen uit:
      1. In de **algemeen** en klik op de **inschrijving van Windows inschakelen** selectievakje.
      2. Als u een certificaat om de code ondertekenen en implementeer de bedrijfsportal-app, bladert u naar de **certificaat voor ondertekening van programmacode**. Gebruikers van apparaten kunnen ook de bedrijfsportal-app installeren vanuit de Windows Store of u kunt de app uit de Windows Store voor bedrijven implementeren zonder de ondertekening van programmacode.
      3. U kunt ook configureren [Windows Hello voor instellingen voor Business](windows-hello-for-business-settings.md).
    - **Windows Phone** voor Windows-telefoons en tablets, voert u de volgende stappen uit:
      1. In de **algemeen** en klik op de **Windows Phone 8.1 en Windows 10 Mobile** selectievakje. Windows Phone 8.0 niet meer wordt ondersteund.
      2. Als uw organisatie sideloaden bedrijfs-apps moet, kunt u de vereiste token of het bestand uploaden. Zie voor meer informatie over sideload-apps [maken Windows-apps](https://docs.microsoft.com/sccm/apps/get-started/creating-windows-applications).
        - **Inschrijvingstoken voor toepassingen**
        - **PFX-bestand**
        - **Geen** als u een Symantec-certificaat gebruikt, kunt u opgeven **waarschuwing weergeven voordat het Symantec-certificaten verlopen**.
4. Klik op **OK** om het dialoogvenster te sluiten.  Om te vereenvoudigen het inschrijvingsproces via de bedrijfsportal, moet u een DNS-alias voor apparaatinschrijving. U kunt vervolgens hoe gebruikers hun apparaten kunnen inschrijven.

## <a name="choose-how-to-enroll-windows-devices"></a>Kies het inschrijven van Windows-apparaten

Nadat u de Intune-licenties aan gebruikers hebt toegewezen, Windows-apparaten zonder enige bijkomende stappen kunnen worden ingeschreven, maar u kunt eenvoudiger inschrijven voor gebruikers.

Twee factoren bepalen hoe kunt u het vereiste Symantec vereenvoudigen:
- **Gebruikt u Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) is opgenomen in de Enterprise Mobility + beveiligings- en andere licentie plannen.
- **Welke versies van Windows-clients zullen registreren?** <br>Windows 10-apparaten kunnen automatisch inschrijven door een werk- of schoolaccount-account toe te voegen. Eerdere versies moeten schrijven via de bedrijfsportal-app.

||**Azure AD Premium**|**Andere AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatische inschrijving](#enable-windows-10-automatic-enrollment) |[Gebruikersregistratie](#enable-windows-enrollment-without-azure-ad-premium)|
|**Eerdere versies van Windows**|[Gebruikersregistratie](#enable-windows-enrollment-without-azure-ad-premium)|[Gebruikersregistratie](#enable-windows-enrollment-without-azure-ad-premium)|

## <a name="enable-windows-10-automatic-enrollment"></a>Automatische inschrijving van Windows 10 inschakelen

Automatische inschrijving kan gebruikers eigendom van het bedrijf of persoonlijk Windows 10-computers en Windows 10 mobiele apparaten in Intune inschrijven met het toevoegen van een werk- of schoolaccount hebt en akkoord gaat met worden beheerd. Eenvoudig. Op de achtergrond van de gebruiker-apparaat wordt geregistreerd en lid wordt van Azure Active Directory. Zodra geregistreerd, wordt het apparaat wordt beheerd met Intune.

**Vereisten**
- Azure Active Directory Premium-abonnement ([proefabonnement](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune-abonnement


### <a name="configure-automatic-mdm-enrollment"></a>Configureren van automatische MDM-inschrijving

1. Meld u aan bij de [Azure-beheerportal](https://portal.azure.com) (https://manage.windowsazure.com), en selecteer **Azure Active Directory**.

  ![Schermafdruk van de Azure-portal](../media/auto-enroll-azure-main.png)

2. Selecteer **Mobility (MDM en MAM)**.

  ![Schermafdruk van de Azure-portal](../media/auto-enroll-mdm.png)

3. Selecteer **Microsoft Intune**.

  ![Schermafdruk van de Azure-portal](../media/auto-enroll-intune.png)

4. Configureer **MDM gebruiker bereik**. Geef op welke apparaten moeten worden beheerd door Microsoft Intune. Deze gebruikers Windows 10-apparaten wordt automatisch worden ingeschreven voor beheer met Microsoft Intune.

    - **Geen**
    - **Sommige**
    - **Alle**

   ![Schermafdruk van de Azure-portal](../media/auto-enroll-scope.png)

5. Gebruik de standaardwaarden voor de volgende URL's:
    - **MDM-voorwaarden van de URL gebruiken**
    - **MDM-detectie-URL**
    - **MDM-compatibiliteit-URL**

6. Selecteer **opslaan**.


Verificatie met twee factoren is standaard niet ingeschakeld voor de service. Verificatie met twee factoren wordt echter aanbevolen bij het registreren van een apparaat. Voor verificatie met twee factoren wordt vereist voor deze service, moet u een verificatieprovider met twee factoren in Azure Active Directory configureren en uw gebruikersaccounts voor meervoudige verificatie configureren. Zie [aan de slag met de Azure multi-factor Authentication-Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Inschrijving van Windows zonder Azure AD Premium inschakelen
U kunt gebruikers hun apparaten zonder automatische inschrijving van Azure AD Premium inschrijven. Als u licenties toewijzen, kunnen gebruikers inschrijven na hun werkaccount toe te voegen aan hun persoonlijke apparaten of hun apparaten in Bedrijfseigendom toevoegen aan uw Azure AD. Maken van een DNS is alias (CNAME-recordtype) het gemakkelijker voor gebruikers hun apparaten kunnen inschrijven. Als u DNS CNAME-bronrecords maakt, kunnen gebruikers verbinding maken en inschrijven in Intune zonder te hoeven invoeren van de naam van de Intune-server.

### <a name="create-cnames-to-simplify-enrollment"></a>CNAME-records om de inschrijving te maken
Maak DNS CNAME-bronrecords voor uw bedrijfsdomein. Bijvoorbeeld, als de website van uw bedrijf contoso.com is, maakt u een CNAME in DNS die enterpriseenrollment.contoso.com doorverwijst naar enterpriseenrollment-s.manage.microsoft.com.

Hoewel DNS CNAME-vermeldingen maken optioneel is, eenvoudiger CNAME-records inschrijven voor gebruikers. Als er geen inschrijving CNAME-record wordt gevonden, worden gebruikers gevraagd handmatig invoeren van de MDM-servernaam enrollment.manage.microsoft.com.

|Type|Hostnaam|Verwijst naar|(TTL)|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.bedrijfsdomein.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 uur|

Als u meer dan één UPN-achtervoegsel hebben, moet u een CNAME voor elke domeinnaam maken en wijs een EnterpriseEnrollment-s.manage.microsoft.com. Bijvoorbeeld, als gebruikers bij Contoso name@contoso.com, maar ook gebruiken name@us.contoso.com, en name@eu.constoso.com als hun e-mailadres/UPN, de Contoso DNS-beheerder moet de volgende CNAME-records maken.

|Type|Hostnaam|Verwijst naar|(TTL)|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 uur|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 uur|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 uur|

`EnterpriseEnrollment-s.manage.microsoft.com`– Biedt ondersteuning voor een omleiding naar de Intune-service met domeinherkenning via de domeinnaam van het e-mailadres van

Wijzigingen in DNS-records kunnen om zich te verspreiden tot 72 uur duren. U kunt de DNS-wijziging in Intune kan niet controleren totdat de DNS-record wordt doorgegeven.

## <a name="tell-users-how-to-enroll-devices"></a>Gebruikers uitleggen hoe apparaten inschrijven  

 Zodra u alles hebt ingesteld, moet u uw gebruikers laten weten hoe ze hun apparaten moeten inschrijven. Zie [wat gebruikers vertellen over het inschrijven van hun apparaten](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) voor hulp. U kunt instellen dat gebruikers [uw Windows-apparaat in Intune inschrijven](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Deze informatie is van toepassing op mobiele apparaten die worden beheerd door Configuration Manager en Microsoft Intune.

> [!div class="button"]
[< Vorige stap](create-service-connection-point.md)[volgende stap >  ](set-up-additional-management.md)

