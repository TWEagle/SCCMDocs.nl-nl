---
title: Technische Preview 1709
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1709 voor System Center Configuration Manager.
ms.custom: na
ms.date: 09/28/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3ef6bdc-a204-4c4c-a02f-2bd03f35183e
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: f0acc5ae0d8207dce92c56a4c80e8321faf51393
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1709-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1709 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1709 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md) om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Bekende problemen in deze Technical Preview:**
-   **Update voor de preview-versie 1709 mislukt wanneer u een siteserver in de passieve modus hebt**. Als u de preview-versie 1706, 1707 of 1708 uitvoeren en hebben een [primaire siteserver in de passieve modus](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), moet u de passieve modus siteserver verwijderen voordat u de preview-site met succes naar versie 1709 bijwerken kunt. Nadat u uw site versie 1709 wordt uitgevoerd, kunt u de passieve modus siteserver opnieuw installeren.

  Verwijderen van de siteserver van de passieve modus:
  1. Ga in de console naar **beheer** > **overzicht** > **siteconfiguratie** > **Servers en sitesysteemrollen**, en selecteer vervolgens de passieve modus-siteserver.
  2. In de **sitesysteemrollen** deelvenster, rechts Klik op de **siteserver** rol, en kies vervolgens **rol verwijderen**.
  3. Met de rechtermuisknop op de siteserver van de passieve modus, en kies vervolgens **verwijderen**.
  4. Nadat de siteserver verwijdert, op de primaire siteserver van de actieve service opnieuw starten de **CONFIGURATION_MANAGER_UPDATE**.


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="improved-vpn-profile-experience-in-configuration-manager-console"></a>Verbeterde ervaring voor VPN-profiel in Configuration Manager-console
<!-- 1313282 -->
We hebben de VPN-profiel wizard eigenschappen pagina's en om weer te geven van de instellingen die geschikt is voor het geselecteerde platform bijgewerkt met deze release. Specifieke opdrachten:

- Elk platform heeft een eigen workflow, wat betekent dat nieuwe VPN-profielen alleen de instelling die wordt ondersteund door het platform bevatten.
- De **ondersteunde Platforms** pagina's worden nu weergegeven na de **algemene** pagina.  U kunt nu het platform kiezen voordat u de waarden van eigenschappen.
- Wanneer het platform is ingesteld op **Android**, **Android for Work**, of **Windows Phone 8.1**, wordt de **ondersteunde platforms** pagina is niet nodig en is niet weergegeven.
- De werkstroom op basis van een client van Configuration Manager is nu gecombineerd met de hybride mobiele apparaten (MDM)-client-werkstromen op basis van Windows 10; ze ondersteunen dezelfde instellingen.
- Elke werkstroom platform bevat alleen de instellingen die geschikt is voor die werkstroom.  De Android werkstroom bevat bijvoorbeeld instellingen voor Android; instellingen voor iOS of Windows 10 Mobile wordt niet meer weergegeven in de Android-werkstroom.
- Instellingen die worden beheerd door Configuration Manager zijn duidelijk gemarkeerd voor Windows 8.1-apparaten.
- De automatische VPN-pagina is verouderd en is verwijderd.

Deze wijzigingen van toepassing op nieuwe VPN-profielen.  

Compatibiliteit om risico te beperken, zijn de bestaande VPN-profielen ongewijzigd.  Wanneer u een bestaand profiel bewerkt, worden de instellingen weergegeven zoals wanneer het profiel is gemaakt.  

### <a name="try-it-out"></a>Probeer het nu!

Maak een nieuwe VPN-profiel met behulp van de normale proces. U ziet dat de eerste pagina van de wizard VPN-profiel van opties zijn gewijzigd.

1.  Ga naar **activa en naleving** > **overzicht** > **instellingen voor naleving** > **toegang tot bedrijfsbronnen**   >  **VPN-profielen** en kies vervolgens **VPN-profiel maken**.
2.  Geef een naam op de **algemene** pagina en kies een van de volgende opties onder **opgeven welk type VPN-profiel dat u wilt maken**:

    - Windows 10  
    - Windows 8.1  
    - Windows Phone 8,1  
    - iOS en Mac OS  
    - Android  
    - Android for Work  

3.  Als u ervoor kiest **Windows 8.1**, hebt u ook de optie te **nieuw profiel maken** of **importeren uit bestand**.
4.  Voltooi de wizard voor het voltooien van het profiel maakt.

Als u verschillende platforms selecteert, ziet u dat alleen de instellingen die relevant zijn voor de weergave van het geselecteerde platform.

## <a name="co-management-for-windows-10-devices"></a>CO-beheer voor Windows 10-apparaten    
<!-- 1350871 -->
Veel klanten willen beheren van Windows 10-apparaten op dezelfde manier beheren van mobiele apparaten met behulp van een vereenvoudigde en lagere kosten, cloud-gebaseerde oplossing. Echter, het overschakelen van traditionele management naar moderne management kan lastig zijn. Beginnen met het Windows 10 versie 1607 (ook wel bekend als de verjaardag Update), u kunt deelnemen aan een Windows 10-apparaten met on-premises Active Directory (AD) en Azure AD cloud-gebaseerd op hetzelfde moment (hybride Azure AD). Mede management maakt gebruik van deze verbetering en kunt u gelijktijdig Windows 10-apparaten beheren met behulp van zowel Configuration Manager en Intune. Het is een oplossing waarmee een verbinding met traditionele naar moderne management biedt en u een pad voor de overgang met behulp van een gefaseerde benadering. 

### <a name="prerequisites"></a>Vereisten
U moet beschikken over de volgende vereisten voordat u kunt CO-beheer inschakelen. Er zijn algemene vereisten en andere vereisten gelden voor bestaande Configuration Manager-clients en apparaten die geen clients.

### <a name="known-issues"></a>Bekende problemen
Nadat u een CO-management-beleid hebt gemaakt, kunt u het beleid niet bewerken. Het beleid wijzigen, verwijderen en vervolgens opnieuw te maken met de instellingen die u nodig hebt. 

#### <a name="general-prerequisites"></a>Algemene vereisten
Hieronder vindt u algemene vereisten voor het inschakelen van CO-beheer:  

- Technical Preview voor Configuration Manager versie 1709
- Azure AD 
- Intune- of EMS-licentie voor alle gebruikers
- Intune-abonnement &#40; MDM-instantie in Intune wordt ingesteld op **Intune**&#41;

   > [!Note]  
   > Als u een hybride MDM-omgeving (Intune geïntegreerd met Configuration Manager) hebt, kunt u mede management niet inschakelen. Als u geïnteresseerd bent in migreren naar de zelfstandige versie van Intune, raadpleegt u [beginnen met het migreren van hybride MDM zelfstandige versie van Intune](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

#### <a name="additional-prerequisites-for-existing-configuration-manager-clients"></a>Aanvullende vereisten voor bestaande Configuration Manager-clients
- Windows 10 versie 1709 (Update vallen auteurs) en hoger
- Hybride Azure AD-lid (toegevoegd aan AD en Azure AD)

#### <a name="additional-prerequisites-for-new-windows-10-devices"></a>Aanvullende vereisten voor de nieuwe Windows 10-apparaten
- Windows 10 versie 1709 (Update vallen auteurs) en hoger
- [Management Gateway cloud](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) in Configuration Manager

### <a name="workloads-you-can-switch-to-intune"></a>Werkbelastingen die u kunt overschakelen naar Intune
Nadat u mede-beheer inschakelen, blijft de Configuration Manager voor het beheren van alle werkbelastingen. Als u besluit dat u klaar bent, kunt u beginnen met beheer van beschikbare werklasten Intune kunt hebben. U kunt Intune beheren van de volgende werkbelastingen hebben in deze release.   

#### <a name="compliance-policies"></a>Nalevingsbeleid
Het nalevingsbeleid bevat de regels en instellingen waaraan een apparaat voldoen moet om te worden beschouwd als het beleid voldoen aan het beleid voor voorwaardelijke toegang. U kunt ook nalevingsbeleid gebruiken om nalevingsproblemen met apparaten te bewaken en onafhankelijk van voorwaardelijke toegang op te lossen. Zie voor meer informatie [nalevingsbeleid voor apparaten](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/device-compliance-policies).  

#### <a name="windows-update-for-business-policies"></a>Windows Update voor bedrijven-beleid
Windows Update voor bedrijven-beleid kunt u beleidsregels voor uitgestelde voor functie-updates voor Windows 10 of kwaliteit voor Windows 10-apparaten rechtstreeks beheerd door Windows Update voor bedrijven configureren. Zie voor meer informatie [Windows Update configureren voor uitgestelde bedrijfsbeleid](https://docs.microsoft.com/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies).  

### <a name="remote-actions-available-in-intune-on-azure-for-co-managed-devices"></a>Externe acties beschikbaar zijn in Intune in Azure voor naast beheerde apparaten
Wanneer een apparaat met Windows 10 is ingeschakeld voor het beheer van CO, hebt u de volgende acties op afstand beschikbaar voor u uit Intune in Azure:  
- [Fabrieksinstellingen terugzetten](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
- [Selectief wissen](https://docs.microsoft.com/intune/apps-selective-wipe)
- [Apparaten verwijderen](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
- [Opnieuw opstarten van apparaat](https://docs.microsoft.com/intune/device-restart)
- [Nieuwe start](https://docs.microsoft.com/intune/device-fresh-start)

### <a name="prepare-intune-for-co-management"></a>Intune voorbereidt op mede management
Voordat u werklasten van Configuration Manager met Intune overschakelt, de profielen maken en beleidsregels die u nodig hebt in Intune zodat uw apparaten blijven worden beveiligd.
U kunt objecten maken in Intune op basis van de objecten die u in Configuration Manager hebt. Of als uw huidige strategie is gebaseerd op verouderde of traditionele management, kunt u een stap na te denken over welke beleidsregels en profielen, u voor het beheer van moderne moet terug te nemen. Gebruik de volgende bronnen voor het maken van de beleidsregels en profielen.    
<!-- - [Device compliance policies](https://docs.microsoft.com/intune/compliance-policy-create-windows)  -->
- [Windows Update voor bedrijven-beleid](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
- [Profielen voor configuratie van apparaten](https://docs.microsoft.com/intune/device-profile-create)  

### <a name="architectural-overview-for-co-management"></a>Overzicht van de architectuur voor CO-management
Het volgende diagram biedt een overzicht van de architectuur van CO-beheer en hoe deze in de bestaande infrastructuur voor configuratie en Intune past.

![Architectuurdiagram van CO-management](./media/co-management-arch-cm1709tp.svg)

### <a name="scenarios-to-enable-co-management"></a>Scenario's voor CO-beheer inschakelen  
U kunt CO-beheer voor zowel Windows 10-apparaten zijn ingeschreven bij Microsoft Intune en de bestaande Windows 10 Configuration Manager-clients inschakelen. Beide scenario's resulteren in Windows 10-apparaten gelijktijdig worden beheerd door Configuration Manager en Intune, evenals toegevoegd aan AD en Azure AD.  

#### <a name="devices-enrolled-in-intune"></a>Apparaten die zijn ingeschreven in Intune  
Wanneer Windows 10-apparaten zijn ingeschreven bij Intune, kunt u de Configuration Manager-client installeren op de apparaten (met behulp van een specifieke opdrachtregelargument) de clients om voor te bereiden mede management. Schakel vervolgens mede beheer vanuit de Configuration Manager-console starten specifieke werkbelastingen verplaatsen naar Intune voor specifieke Windows 10-apparaten.  

Voor Windows 10-apparaten die nog niet zijn ingeschreven in Intune, kunt u automatische inschrijving in Azure gebruiken om de apparaten te registreren. Voor de nieuwe Windows 10-apparaten, kunt u Windows Automatische piloot voor het configureren van de Out of Box Experience (OOBE), waaronder automatische inschrijving dat apparaten in Intune inschrijft.  

#### <a name="configuration-manager-clients"></a>Configuration Manager-clients
Wanneer u Windows 10-apparaten die Configuration Manager-clients hebt, kunt u deze apparaten registreren en collega beheer vanuit de Configuration Manager-console. Configuration Manager-triggers automatische inschrijving bij Intune op basis van de Azure AD-tenant informatie.  

### <a name="prepare-windows-10-devices-for-co-management"></a>Windows 10-apparaten voor het beheer van CO voorbereiden
U kunt CO-beheer op Windows 10-apparaten die zijn toegevoegd aan AD en Azure AD en ingeschreven in Intune en een client in Configuration Manager inschakelen. Voor de nieuwe Windows 10-apparaten, en voor apparaten die al zijn ingeschreven in Intune, de Configuration Manager-client installeren voordat ze samen beheerd worden kunnen. Voor Windows 10-apparaten die al Configuration Manager-clients, kunt u de apparaten inschrijven bij Intune en mede-beheer in de Configuration Manager-console inschakelen.

#### <a name="command-line-to-install-configuration-manager-client"></a>Vanaf de opdrachtregel voor het installeren van Configuration Manager-client
Een app maken in Intune voor Windows 10-apparaten die nog geen Configuration Manager-clients. Wanneer u de app in de volgende secties maakt, gebruikt u de volgende opdrachtregel:

ccmsetup.msi CCMSETUPCMD = "/ mp: &#60; *URL van een cloudeindpunt management gateway wederzijdse verificatie*&#62; / CCMHOSTNAME = &#60; *URL van een cloudeindpunt management gateway wederzijdse verificatie*&#62; SMSSiteCode = &#60; *Sitecode*&#62; SMSMP = https: &#47; / &#60; *FQDN-naam van MP*&#62; AADTENANTID = &#60; *AAD-tenant-ID*&#62; AADTENANTNAME = &#60; *Tenantnaam*&#62; AADCLIENTAPPID = &#60; *Server AppID voor AAD-integratie*&#62; AADRESOURCEURI = https: &#47; / &#60; *Resource-ID*&#62; "

Bijvoorbeeld, als u had de volgende waarden:

- **URL van een cloudeindpunt management gateway wederzijdse verificatie**: https:/ &#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100    

   >[!Note]    
   >Gebruik de **MutualAuthPath** waarde in de **vProxy_Roles** SQL-weergave voor de **URL van een cloudeindpunt management gateway wederzijdse verificatie** waarde.

- **FQDN van beheerpunt (MP)**: sccmmp.corp.contoso.com    
- **Sitecode**: PS1    
- **Azure AD-tenant-ID**: 72F988BF-86F1-41AF-91AB-2D7CD011XXXX    
- **Naam van een Azure AD-tenant**: contoso    
- **Azure AD client app-ID**: bef323b3-042f-41a6-907a-f9faf0d1XXXX     
- **AAD Resource-ID-URI**: ConfigMgrServer    

  > [!Note]    
  > Gebruik de **IdentifierUri** waarde gevonden in de **vSMS_AAD_Application_Ex** SQL-weergave voor de **AAD Resource-ID-URI** waarde.

Gebruikt u de volgende opdrachtregel:

ccmsetup.msi CCMSETUPCMD = "/ mp:https: / &#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 SMSSiteCode = PS1 SMSMP = https: / &#47; sccmmp.corp.contoso.com AADTENANTID = 72F988BF-86F1-41AF-91AB-2D7CD011XXXX AADTENANTNAME = contoso AADCLIENTAPPID = bef323b3-042f-41a6-907a-f9faf0d1XXXX AADRESOURCEURI = https: / &#47; ConfigMgrServer'

> [!Tip]
>U vindt de opdrachtregelparameters voor uw site met behulp van de volgende stappen uit:     
> 1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices**  >  **Mede management**.  
> 2. Kies op het tabblad Start in de groep beheren **mede management configureren** openen van de Wizard mede management voorbereiden.    
> 3. Klik op de pagina abonnement **aanmelden** aanmelden bij uw Intune-tenant en klik vervolgens op **volgende**.    
> 4. Klik op de pagina stuk **kopie** in de **apparaten zijn ingeschreven in Intune** sectie voor de opdrachtregel naar het Klembord kopiëren en sla de opdrachtregel om te gebruiken in de procedure om de app te maken.  
> 5. Klik op **annuleren** de wizard wilt afsluiten.

#### <a name="new-windows-10-devices"></a>Nieuwe Windows 10-apparaten
Voor de nieuwe Windows 10-apparaten, kunt u de service Automatische piloot voor het configureren van de buiten-vak ervaring, waaronder het apparaat toevoegen aan AD en Azure AD, evenals het apparaat in Intune inschrijven. Vervolgens maakt u een app in Intune voor het implementeren van Configuration Manager-client.  
1. Schakel automatische piloot voor de nieuwe Windows 10-apparaten. Zie voor meer informatie [overzicht Windows Automatische piloot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot).  
2. Automatische inschrijving configureren in Azure AD voor uw apparaten automatisch worden geregistreerd bij Intune. Zie voor meer informatie [inschrijven Windows-apparaten voor Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).
3. Een app maken in Intune met het clientpakket voor Configuration Manager en de app implementeren op Windows 10-apparaten die u wilt CO beheren. Gebruik de [vanaf de opdrachtregel voor het installeren van Configuration Manager-client](#command-line-to-install-configuration-manager-client) wanneer u de stappen voor het doorloopt [-clients installeren vanaf het Internet met behulp van Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).   

#### <a name="windows-10-devices-not-enrolled-in-intune-or-a-configuration-manager-client"></a>Windows 10-apparaten die niet zijn ingeschreven in Intune of Configuration Manager-client
Voor Windows 10-apparaten die niet zijn ingeschreven in Intune of Configuration Manager-client hebt, kunt u automatische inschrijving op het apparaat inschrijven bij Intune. Vervolgens maakt u een app in Intune voor het implementeren van Configuration Manager-client.
1. Automatische inschrijving configureren in Azure AD voor uw apparaten automatisch worden geregistreerd bij Intune. Zie voor meer informatie [inschrijven Windows-apparaten voor Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).  
2. Een app maken in Intune met het clientpakket voor Configuration Manager en de app implementeren op Windows 10-apparaten die u wilt CO beheren. Gebruik de [vanaf de opdrachtregel voor het installeren van Configuration Manager-client](#command-line-to-install-configuration-manager-client) wanneer u de stappen voor het doorloopt [-clients installeren vanaf het Internet met behulp van Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).

#### <a name="windows-10-devices-enrolled-in-intune"></a>Windows 10-apparaten die zijn ingeschreven bij Intune
Voor Windows 10-apparaten die al zijn ingeschreven in Intune, moet u een app maken in Intune voor het implementeren van Configuration Manager-client. Gebruik de [vanaf de opdrachtregel voor het installeren van Configuration Manager-client](#command-line-to-install-configuration-manager-client) wanneer u de stappen voor het doorloopt [-clients installeren vanaf het Internet met behulp van Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).  

### <a name="switch-configuration-manager-workloads-to-intune"></a>Configuration Manager-workloads overschakelen naar Intune
In de vorige sectie, moet u Windows 10-apparaten voor het beheer van CO voorbereid. Deze apparaten zijn nu toegevoegd aan AD en Azure AD en ze zijn ingeschreven bij Intune en Configuration Manager-client hebben. Hebt u waarschijnlijk nog Windows 10-apparaten die lid zijn van AD en Configuration Manager-client, maar niet toegevoegd aan Azure AD. of zijn ingeschreven in Intune. De volgende procedure bevat de stappen voor het inschakelen van CO-beheer, de rest van uw Windows 10-apparaten (Configuration Manager-clients zonder inschrijving bij Intune) voor het beheer van CO voorbereiden en kunt u starten Overschakelen van specifieke Configuration Manager werkbelastingen naar Intune.

1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices**  >  **Mede management**.    
2. Kies op het tabblad Start in de groep beheren **mede management configureren** openen van de Wizard mede management voorbereiden.    
3. Klik op de pagina abonnement **aanmelden** aanmelden bij uw Intune-tenant en klik vervolgens op **volgende**.   
4. Configureer de volgende instellingen op de pagina fasering en klik vervolgens op **volgende**:
    - **Testgroep**: De testgroep bevat een of meer verzamelingen die u selecteert. Deze groep gebruiken als onderdeel van uw gefaseerde implementatie van CO-beheer. U kunt beginnen met een kleine testverzameling en voeg vervolgens meer verzamelingen aan de test groep tijdens de implementatie van CO management voor meerdere gebruikers en apparaten. U kunt de verzamelingen in de testgroep op elk gewenst moment de collega beheereigenschappen wijzigen.
    - **Productie**: Wanneer u deze instelling selecteert, worden alle ondersteunde Windows 10-apparaten zijn ingeschakeld voor het beheer van collega. Configureer de **uitsluiting groep** met een of meer verzamelingen. Apparaten die lid van een van de collecties in deze groep zijn worden uitgesloten van met CO-beheer. 
5. Kies op de pagina stuk **proef** of **alle** (afhankelijk van de instellingen die u hebt geconfigureerd op de pagina fasering) inschakelen van automatische inschrijving bij Intune en klik vervolgens op **volgende**. Wanneer u de optie **test**, alleen de Configuration manager-clients die lid van de test-groep zijn automatisch zijn ingeschreven bij Intune. Hiermee kunt u mede beheer inschakelen op een subset van clients te testen in eerste instantie mede beheer en mede-implementatiebeheer met behulp van een gefaseerde benadering. 
6. Op de pagina werkbelastingen kiezen of u wilt overschakelen van Configuration Manager workloads die moeten worden beheerd door Intune en klik vervolgens op **volgende**. Gebruik de schuifregelaars om te selecteren of u wilt overschakelen van de werkbelasting aan de groep prototype of voor alle Windows 10-clients (afhankelijk van de instellingen die u hebt geconfigureerd op de pagina fasering). 
7. Mede als beheer wilt inschakelen, moet u de wizard voltooien.  

<!--### Modify your co-management settings
After you enable co-management using the wizard, you can modify your target group and change the workloads that are managed by Configuration Manager and Intune.  
- In the Configuration Manager console, go to **Administration** > **Overview** > **Cloud Services** > **Co-management**.  
Select the co-management object, and then on the Home tab, click **Properties**. -->   

<!--### Monitor co-management
After you have enabled co-management, you can monitor which devices are managed by Configuration Manager and which are managed by Intune. You can also see which Configuration Manager workloads are managed by which product.-->

## <a name="see-also"></a>Zie tevens
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview). 
