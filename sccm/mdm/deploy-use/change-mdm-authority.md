---
title: Wijzigen van uw MDM-instantie | Microsoft Docs
description: Informatie over het wijzigen van de MDM-instantie van Configuration Manager (hybride) zelfstandige versie van Intune of vice versa.
keywords: 
author: dougeby
manager: angrobe
ms.date: 06/02/2017
ms.topic: article
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: cc397ab5-125f-4f17-905b-fab980194f49
ms.openlocfilehash: 74b9dbb1ed0172d99956e726fca3aec2b658ce77
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="change-your-mdm-authority"></a>Wijzigen van uw MDM-instantie
Vanaf versie 1610 van Configuration Manager en Microsoft Intune version 1705, kunt u uw MDM-instantie zonder contact opnemen met Microsoft Support en zonder de registratie ongedaan maken en registreren van uw bestaande beheerde apparaten.

## <a name="change-the-mdm-authority-to-intune-standalone"></a>Wijzig de MDM-instantie in zelfstandige versie van Intune
Gebruik deze sectie voor het wijzigen van een bestaande Microsoft Intune-tenant geconfigureerd via de Configuration Manager-console (hybride) zelfstandige versie van Intune zonder de registratie ongedaan maken en bestaande beheerde apparaten te registreren.

### <a name="key-considerations"></a>Belangrijke aandachtspunten
Nadat u op de nieuwe MDM-instantie, er wordt waarschijnlijk overgang tijd (maximaal 8 uur) voordat wordt het apparaat wordt ingecheckt en synchroniseert met de service. U moet opnieuw worden instellingen configureren in de nieuwe MDM-instantie (Intune zelfstandig) om ervoor te zorgen dat ingeschreven apparaten worden beheerd en beveiligd wanneer de wijziging wordt voortgezet. Houd rekening met het volgende:
- Apparaten moeten verbinding maken met de service na de wijziging zodat de instellingen van de nieuwe MDM-instantie (Intune zelfstandig) de bestaande instellingen op het apparaat vervangt.
- Nadat u de MDM-instantie hebt gewijzigd, worden enkele van de algemene instellingen (zoals profielen) uit de vorige MDM-instantie (hybride) blijven op het apparaat gedurende 7 dagen. Het is raadzaam dat u zo snel mogelijk apps en instellingen (beleid, profielen, apps, enzovoort) in de nieuwe MDM-instantie configureren en de instellingen implementeren voor de gebruikersgroepen die gebruikers bevat die u hebt bestaande geregistreerde apparaten. Als een apparaat verbinding met de service na de wijziging in de MDM-instantie maakt, wordt het ontvangen van de nieuwe instellingen van de nieuwe MDM-instantie en voorkomen dat hiaten in beheer en de beveiliging. Alle regels voor het nieuwe gerichte overschrijft bestaande beleidsregels op het apparaat.
- Nadat u de nieuwe MDM-instantie wijzigt, kan de gegevens in de Microsoft Intune-beheerconsole duren een week nauwkeurig rapporteren. De nalevingsstatussen in Azure Active Directory en op het apparaat worden echter nauwkeurige zodat het apparaat nog steeds worden beveiligd.

### <a name="prepare-to-change-the-mdm-authority-to-intune-standalone"></a>Voorbereiden om te wijzigen van de MDM-instantie in zelfstandige versie van Intune
Controleer de volgende informatie om voor te bereiden voor de wijziging van de MDM-instantie:
- U moet Configuration Manager versie 1610 of hoger om de optie voor het wijzigen van de MDM-instantie beschikbaar hebben.
- Het kan maximaal acht uur voor een apparaat verbinding maken met de service na wijziging van de nieuwe MDM-instantie duren.
- Zorg ervoor dat alle gebruikers die momenteel worden beheerd door hybride hebben een Intune/EMS-licentie specifiek aan hen zijn toegewezen voordat de wijziging in de MDM-instantie. Dit zorgt ervoor dat de gebruiker en hun apparaten worden beheerd door Intune standalone na de wijziging in de MDM-instantie. Zie voor meer informatie [toewijzen Intune-licenties aan uw gebruikersaccounts](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).
- Zorg ervoor dat het beheerdersaccount van de gebruiker een Intune/EMS-licentie toegewezen heeft en Bevestig dat het beheerdersaccount van de gebruiker bij Intune voordat de wijziging van de MDM-instantie aanmelden zich. De MDM-instantie moet worden weergegeven **Configuration Manager ingesteld als** (hybride tenant) in de Microsoft Intune-beheerconsole vóór de wijziging in de MDM-instantie.
- Verwijder alle Apparaatinschrijvingsmanager-rollen in de Configuration Manager-console. Ga naar **beheer** > **Cloudservices** > **Microsoft Intune-abonnementen**, selecteer het Microsoft Intune-abonnement, klik op **eigenschappen**, klikt u op de **Apparaatinschrijvingsmanager** tabblad en verwijder alle Apparaatinschrijvingsmanager-rollen.
- Verwijder de bestaande categorieën voor apparaatstuurprogramma in de Configuration Manager-console. Ga naar **activa en naleving** > **overzicht** > **Apparaatverzamelingen**, kies **apparaatcategorieën beheren**, en verwijder de bestaande categorieën voor apparaatstuurprogramma.
- Er mag geen merkbare invloed hebben op eindgebruikers tijdens de wijziging in de MDM-instantie. Daarom is het raadzaam om te communiceren deze wijziging voor gebruikers om ervoor te zorgen dat hun apparaten zijn ingeschakeld en dat ze verbinding met de service kort na de wijziging maken. Dit zorgt ervoor dat als veel apparaten mogelijk wordt verbinding maken en bij de service via de nieuwe autoriteit zo snel mogelijk registreren.
- Als u Configuration Manager (hybride tenant) voor het beheren van iOS-apparaten voordat de wijziging in de MDM-instantie gebruikt, moet u ervoor zorgen dat het certificaat met dezelfde Apple Push Notification service (APNs) die in Configuration Manager voorheen is vernieuwd en gebruikt voor het instellen van de tenant opnieuw in de zelfstandige versie van Intune.

    > [!IMPORTANT]  
    > Als een ander APNs-certificaat voor de zelfstandige versie van Intune gebruikt, wordt alle eerder ingeschreven iOS-apparaten worden uitgeschreven en moet u de procedure opnieuw te registreren ze te doorlopen. Voordat u de MDM-instantie wijzigen, moet u weten precies welke APNs-certificaat is gebruikt voor het beheren van iOS-apparaten in Configuration Manager. Zoek hetzelfde certificaat vermeld in de Apple Push Certificates Portal (https://identity.apple.com) en zorg ervoor dat de gebruiker met de Apple-ID is gebruikt voor het maken van het oorspronkelijke APNs-certificaat is geïdentificeerd en beschikbaar voor het vernieuwen van het dezelfde APNs-certificaat als onderdeel van de wijzigingen in de nieuwe MDM-instantie.  

### <a name="change-the-mdm-authority-to-intune-standalone"></a>Wijzig de MDM-instantie in zelfstandige versie van Intune
Het proces voor het wijzigen van de MDM-instantie zelfstandige versie van Intune bevat de volgende geavanceerde stappen:  
- In de Configuration Manager-console, gebruiken de **wijziging MDM-instantie op Microsoft Intune** optie voor het verwijderen van de bestaande Microsoft Intune-abonnement.
- In de Microsoft Intune-beheerconsole, kunt u de nieuwe MDM-instantie instellen op **Intune**.
- Het Apple APNs-certificaat configureren met behulp van het APNs-certificaat dat u vernieuwd.
- In de Microsoft Intune-beheerconsole, configureren en implementeren van nieuwe instellingen en apps op de nieuwe MDM-instantie (Intune).
- De volgende keer apparaten verbinding met de service, automatisch gesynchroniseerd en ontvangen van de nieuwe instellingen van de nieuwe MDM-instantie.

#### <a name="to-change-the-mdm-authority-to-intune-standalone"></a>Wijzigen van de MDM-instantie in zelfstandige versie van Intune
1.  Ga in de Configuration Manager-console naar **beheer** &gt; **overzicht** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en uw bestaande Intune-abonnement verwijderen.
2.  Selecteer **wijziging MDM-instantie op Microsoft Intune**, en klik vervolgens op **volgende**.

    ![De APNs-certificaataanvraag downloaden](/sccm/mdm/deploy-use/media/mdm-change-delete-subscription.png)
3.  Aanmelden bij de Intune-tenant die u oorspronkelijk hebt gebruikt bij het instellen van de MDM-instantie in Configuration Manager.
4.  Klik op **Volgende** en voltooi de wizard.
5.  De MDM-instantie wordt nu opnieuw ingesteld. Het Intune-abonnement mag niet meer weergegeven in het knooppunt van de Microsoft Intune-abonnementen van de Configuration Manager-console.
6.  Meld u aan bij de [Microsoft Intune-beheerconsole](http://manage.microsoft.com) met dezelfde Intune-tenant die u eerder hebt gebruikt.
7.  Controleer of de MDM-instantie is opnieuw instellen en stel vervolgens de MDM-instantie als **Microsoft Intune**. Nadat u de MDM-instantie hebt gewijzigd, ziet u dat deze in de console worden weergegeven. Zie voor meer informatie [het instellen van de MDM-instantie](https://docs.microsoft.com/en-us/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).
<!-- [Azure portal](https://docs.microsoft.com/en-us/intune-azure/enroll-devices/set-mdm-authority) -->


### <a name="configure-the-apns-certificate"></a>Het APNs-certificaat configureren
Wanneer u iOS-apparaten hebt, moet u het APNs-certificaat configureren in Intune.

#### <a name="to-configure-the-apns-certificate"></a>Het APNs-certificaat configureren
1.  De APNs-certificaataanvraag downloaden.
    <!--The process is different depending on how you connect to Intune:
    **Azure portal**   
    In the [Azure portal](https://azure.portal.com), choose **More Services** &gt; **Monitoring + Management** &gt; **Intune**. On the **Intune** blade, choose **Device enrollment** &gt; **Apple Enrollment** &gt; **Apple MDM Push Certificate**, and then select **Download your CSR** to download and save the .csr file locally.   
    <br/>
    **Microsoft Intune administration console**   -->
    In de [Microsoft Intune-beheerconsole](http://manage.microsoft.com), gaat u naar **beheer** &gt; **Mobile Device Management** &gt; **iOS en Mac OS X** &gt; **een APNs-certificaat uploaden**, en kies vervolgens **de APNs-certificaataanvraag downloaden**. Sla het bestand met de aanvraag voor certificaatondertekening (.csr) lokaal op.
    > [!IMPORTANT]    
    > U moet een nieuwe aanvraag voor Certificaatondertekening downloaden. Gebruik een bestaand bestand niet of zal mislukken.

    ![De APNs-certificaataanvraag downloaden](/sccm/mdm/deploy-use/media/mdm-change-download-apns-certificate.png)

2.  Ga naar de [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844), en meld u aan met de **dezelfde** Apple-ID die is gebruikt voor het eerder maken en vernieuwen van het APNs-certificaat dat u in Configuration Manager (hybride gebruikt).

    ![Aanmeldingspagina voor Apple Push Certificates-Portal](/sccm/mdm/deploy-use/media/mdm-change-apns-portal.png)

3.  Selecteer het APNs-certificaat dat u gebruikt in Configuration Manager (hybride) en klik vervolgens op **vernieuwen**.   

    ![Dialoogvenster APNs vernieuwen](/sccm/mdm/deploy-use/media/mdm-change-renew-apns.png)

4.  Selecteer het APNs-certificaat ondertekenen CSR-bestand dat u lokaal hebt gedownload en klik vervolgens op **uploaden**.

    ![Aanmeldingspagina voor Apple Push Certificates-Portal](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-upload.png)  
5.  Selecteer de dezelfde APNs en klik vervolgens op **downloaden**. Download het certificaat voor APNs (.pem) en sla het bestand lokaal.  

    ![Aanmeldingspagina voor Apple Push Certificates-Portal](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-download.png)

6.  De vernieuwd APNs-certificaat uploaden naar de Intune-tenant met dezelfde Apple-ID als voordat.
<!--The process is different depending on how to connect to Intune:  
    **Azure portal**   
    In the [Azure portal](https://azure.portal.com), choose **More Services** &gt; **Monitoring + Management** &gt; **Intune**. On the **Intune** blade, choose **Device enrollment** &gt; **Apple Enrollment**  &gt; **Apple MDM Push Certificate**, enter your Apple ID in step 3, select the certificate (.pem) file in step 4, and then click **Upload**.     
    <br/>
    **Microsoft Intune administration console**    -->
    In the [Microsoft Intune administration console](http://manage.microsoft.com), go to **Administration** &gt; **Mobile Device Management** &gt; **iOS and Mac OS X** &gt; **Upload an APNs Certificate**, and then choose **Upload the APNs certificate**. Go to the certificate (.pem) file, choose **Open**, and then enter your **Apple ID**.   

    ![Upload the APNs certificate](/sccm/mdm/deploy-use/media/mdm-change-upload-apns-certificate.png)

### <a name="next-steps"></a>Volgende stappen
Nadat de wijziging in de MDM-instantie voltooid is, controleert u de volgende stappen uit:
- Als de Intune-service detecteert dat een tenant MDM-instantie is gewijzigd, wordt verzonden uit een melding op alle geregistreerde apparaten in-en synchroniseren met de service (dit is buiten het regelmatig geplande inchecken). Daarom nadat de MDM-instantie voor de tenant is gewijzigd van hybride zelfstandige versie van Intune, alle apparaten die zijn ingeschakeld en online maakt verbinding met de service, wordt de nieuwe MDM-instantie en worden beheerd door Intune standalone voortaan. Er zijn geen gevolgen heeft voor het beheer en beveiliging van deze apparaten.
- Apparaten die uitgeschakeld of offline zijn tijdens (of kort na) de wijziging in de MDM-instantie verbonden zijn met en synchroniseren met de service onder de nieuwe MDM-instantie wanneer ze zijn ingeschakeld en online.  

  iOS-apparaten vereisen meer tijd om te vernieuwen en het instellen van het APNs-certificaat. IOS-apparaten ontvangen daarom niet de eerste aanvraag incheckt. Zelfs als iOS-apparaten ingeschakeld en online zijn tijdens (of kort na) de wijziging in de MDM-instantie, zal er een vertraging van maximaal acht uur (afhankelijk van de timing van de volgende geplande reguliere inchecken) voordat u iOS-apparaten zijn geregistreerd bij de service onder de nieuwe MDM-instantie.    

  > [!IMPORTANT]
  > Tussen het moment waarop het wijzigen van de MDM mislukken-instantie en wanneer de vernieuwd APNs-certificaat is geüpload naar de nieuwe instantie, nieuwe apparaatinschrijvingen en apparaat incheckt voor iOS-apparaten. Het is daarom belangrijk dat u bekijken en het APNs-certificaat naar de nieuwe instantie zo snel mogelijk na de wijziging in de MDM-instantie uploaden.   

- Gebruikers kunnen snel aan de nieuwe MDM-instantie wijzigen door het handmatig starten van een selectievakje in van het apparaat naar de service. Gebruikers kunnen dit eenvoudig doen met behulp van de bedrijfsportal-app en een apparaatgeschiktheidscontrole is gestart.
- Om te valideren of dingen goed werken nadat apparaten hebt ingecheckt en gesynchroniseerd met de service na de wijziging in de MDM-instantie, zoekt u de apparaten de [Microsoft Intune-beheerconsole](http://manage.microsoft.com). De apparaten die werden eerder beheerd door Configuration Manager (hybride) worden nu weergegeven als beheerde apparaten.    
- Er is een tussentijdse periode wanneer een apparaat offline gedurende de wijziging in de MDM-instantie en is als dat het apparaat wordt ingecheckt met de service. Om ervoor te zorgen dat het apparaat beveiligd en in werking tijdens deze periode tussentijdse blijft, blijft de volgende op het apparaat gedurende 7 dagen (of totdat het apparaat verbinding met de nieuwe MDM-instantie maakt en ontvangt van de nieuwe instellingen waarmee wordt de bestaande bestanden overschreven):
    - E-mailprofiel
    - VPN-profiel
    - Certificaat-profiel
    - Wi-Fi-profiel
    - Configuratieprofielen
- Zorg dat de nieuwe instellingen die zijn bedoeld om de bestaande instellingen overschreven door dezelfde naam als de vorige scripts om ervoor te zorgen dat de oude instellingen overschreven. Anders wordt kunnen de apparaten eindigen met redundant profielen en beleidsregels.
    > [!TIP]   
    > Als een best practice moet u alle instellingen en configuraties, evenals implementaties, kort nadat de wijziging van de MDM-instantie is voltooid. Dit helpt ervoor te zorgen dat apparaten zijn beveiligd en dat actief wordt beheerd in de tijdelijke periode.   
-  Nadat u de MDM-instantie hebt gewijzigd, moet u de volgende stappen voor het valideren van nieuwe apparaten met succes zijn geregistreerd bij de nieuwe instantie uitvoeren:   
    - Een nieuw apparaat registreren
    - Zorg ervoor dat het nieuw ingeschreven apparaat wordt weergegeven in de Intune-beheerconsole.
    - Een actie uitgevoerd, zoals vergrendelen op afstand van de beheerconsole voor het apparaat. Als dat lukt, wordt het apparaat wordt beheerd door de nieuwe MDM-instantie.
- Als u problemen met specifieke apparaten hebt, kunt u registratie ongedaan maken en registreren van de apparaten om op te halen ze verbonden met de nieuwe instantie van en worden beheerd zo snel mogelijk.

<!-- After the change in MDM authority and devices check-in with the service, note the following:      - The updated compliance status of devices will only display in the Azure portal immediately.
- There will be a delay for compliance status of devices to display in the Intune administrative console.-->


## <a name="change-the-mdm-authority-to-configuration-manager-hybrid"></a>Wijzigen van de MDM-instantie aan Configuration Manager (hybride)
Gebruik deze sectie voor het wijzigen van een bestaande Microsoft Intune-tenant geconfigureerd bij Intune en met de MDM-instantie ingesteld op **Microsoft Intune** (zelfstandig) naar **Configuration Manager** (hybride) zonder registratie ongedaan maken en bestaande registreren met apparaten beheerde.

### <a name="key-considerations"></a>Belangrijke aandachtspunten
Nadat u naar de nieuwe MDM-instantie, er wordt waarschijnlijk overgang tijd (maximaal 8 uur) overschakelt voordat wordt het apparaat wordt ingecheckt en synchroniseert met de service. U moet opnieuw worden instellingen configureren in de nieuwe MDM-instantie (hybride) om ervoor te zorgen dat ingeschreven apparaten worden beheerd en beveiligd wanneer de wijziging wordt voortgezet. Houd rekening met het volgende:
- Apparaten moeten verbinding maken met de service na de wijziging zodat de instellingen van de nieuwe MDM-instantie (Intune zelfstandig) de bestaande instellingen op het apparaat vervangt.
- Nadat u de MDM-instantie hebt gewijzigd, blijven sommige van de algemene instellingen (zoals profielen) uit de vorige MDM-instantie (Intune zelfstandig) op het apparaat gedurende 7 dagen of totdat het apparaat verbinding met de service voor het eerst maakt. Het is raadzaam dat u zo snel mogelijk apps en instellingen (beleid, profielen, apps, enzovoort) in de nieuwe MDM-instantie (hybride) configureren en de instellingen implementeren voor de gebruikersgroepen die gebruikers bevat die u hebt bestaande geregistreerde apparaten. Als een apparaat verbinding met de service na de wijziging in de MDM-instantie maakt, wordt het ontvangen van de nieuwe instellingen van de nieuwe MDM-instantie en voorkomen dat hiaten in beheer en de beveiliging.

### <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>Voorbereiden om te wijzigen van de MDM-instantie aan Configuration Manager (hybride)
Controleer de volgende informatie om voor te bereiden voor de wijziging van de MDM-instantie:
- U moet Configuration Manager versie 1610 of hoger om de optie voor het wijzigen van de MDM-instantie beschikbaar hebben.
- Het kan maximaal acht uur voor een apparaat verbinding maken met de service na wijziging van de nieuwe MDM-instantie duren.
- Maak een Configuration Manager-Gebruikersverzameling met alle gebruikers die momenteel wordt beheerd door Intune Standalone die u gebruiken wilt bij het instellen van het Intune-abonnement in de Configuration Manager-console. Dit helpt ervoor te zorgen dat de gebruiker en hun apparaten wordt een Configuration Manager-licentie toegewezen en worden beheerd in de hybride omgeving na de wijziging van de MDM-instantie.
- Zorg ervoor dat de gebruiker van de IT-beheerder in de Gebruikersverzameling van deze te is.  
- Voordat u de wijziging, de MDM-instantie wordt weergegeven als **ingesteld op Microsoft Intune** (zelfstandig) in de Intune-beheerconsole.
- De MDM-instantie moet worden weergegeven **ingesteld op Microsoft Intune** (zelfstandige tenant) in de Microsoft Intune-beheerconsole vóór de wijziging in de MDM-instantie.
    > [!NOTE]    
    > Als uw MDM-instantie wordt weergegeven in **beheerd door Intune en Office 365**, vervolgens uw Office 365 beheerde MDM-apparaten niet meer worden beheerd wanneer u uw MDM-instantie te wijzigen **Configuration Manager** (hybride). Het is raadzaam dat u deze gebruikers licentie voor Intune of Enterprise Mobility Suite voordat u de MDM-instantie wijzigen.   

- In de [Microsoft Intune-beheerconsole](http://manage.microsoft.com), verwijdert u de rol van Apparaatinschrijvingsmanager. Zie voor meer informatie [een apparaatinschrijvingsbeheerder uit Intune verwijderen](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Uitschakelen van een apparaat groepstoewijzingen die zijn geconfigureerd. Zie voor meer informatie [apparaten categoriseren met apparaatgroeptoewijzing in Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).
- Er mag geen merkbare invloed hebben op eindgebruikers tijdens de wijziging in de MDM-instantie. Daarom is het raadzaam om te communiceren deze wijziging voor gebruikers om ervoor te zorgen dat hun apparaten zijn ingeschakeld en dat ze verbinding met de service kort na de wijziging maken. Dit zorgt ervoor dat als veel apparaten mogelijk wordt verbinding maken en bij de service via de nieuwe autoriteit zo snel mogelijk registreren.
- Als u de zelfstandige versie van Intune voor het beheren van iOS-apparaten voordat de wijziging in de MDM-instantie gebruikt, moet u ervoor zorgen dat het certificaat met dezelfde Apple Push Notification service (APNs) die eerder is gebruikt bij Intune is vernieuwd en gebruikt voor het instellen van de tenant opnieuw in Configuration Manager (hybride).    

    > [!IMPORTANT]  
    > Als een ander APNs-certificaat wordt gebruikt voor hybride, wordt alle eerder ingeschreven iOS-apparaten worden uitgeschreven en moet u de procedure opnieuw te registreren ze te doorlopen. Voordat u de MDM-instantie wijzigen, moet u weten precies welke APNs-certificaat is gebruikt voor het beheren van iOS-apparaten in Intune. Zoek hetzelfde certificaat vermeld in de Apple Push Certificates Portal (https://identity.apple.com) en zorg ervoor dat de gebruiker met de Apple-ID is gebruikt voor het maken van het oorspronkelijke APNs-certificaat is geïdentificeerd en beschikbaar voor het vernieuwen van het dezelfde APNs-certificaat als onderdeel van de wijzigingen in de nieuwe MDM-instantie.  

### <a name="change-the-mdm-authority-to-configuration-manager"></a>Wijzigen van de MDM-instantie aan Configuration Manager
Het proces voor het wijzigen van de MDM-instantie aan Configuration Manager (hybride) omvat de volgende geavanceerde stappen:  
- Voeg het Microsoft Intune-abonnement in de Configuration Manager-console.
- Het Apple APNs-certificaat configureren met behulp van het APNs-certificaat dat u vernieuwd.
- In de Configuration Manager-console configureren en implementeren van nieuwe instellingen en apps op de nieuwe MDM-instantie (hybride).
- De volgende keer apparaten verbinding met de service, automatisch gesynchroniseerd en ontvangen van de nieuwe instellingen van de nieuwe MDM-instantie.

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>Wijzigen van de MDM-instantie aan Configuration Manager
1.  Ga in de Configuration Manager-console naar **beheer** &gt; **overzicht** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en selecteer een Intune-abonnement toevoegen.
2.  Aanmelden bij de Intune-tenant die u oorspronkelijk hebt gebruikt wanneer u de MDM-instantie ingesteld in Intune en klik op **volgende**.
3.  Selecteer **MDM-instantie verwisselen wijzigen naar Configuration Manager**, en klik op **volgende**.
4.  Selecteer de Gebruikersverzameling met alle gebruikers die worden beheerd door de nieuwe hybride MDM-instantie wordt voortgezet.
5.  Klik op **Volgende** en voltooi de wizard.  
5.  De MDM-instantie is nu gewijzigd in **Configuration Manager**.
6.  Meld u aan bij de [Microsoft Intune-beheerconsole](http://manage.microsoft.com) met de dezelfde Intune-tenant en te bevestigen dat de MDM-instantie is gewijzigd in **Configuration Manager ingesteld als**.


### <a name="enable-ios-enrollment"></a>IOS-inschrijving inschakelen
Wanneer u iOS-apparaten hebt, moet u het APNs-certificaat configureren in Configuration Manager.

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>IOS-inschrijving inschakelen en configureren van het APNs-certificaat

1. **Een aanvraag voor Certificaatondertekening downloaden**

    1.  In de Configuration Manager-console gaat u naar **beheer** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnementen**, en selecteer **maken APNs-certificaataanvraag** openen de **aanvraag voor Apple Push Notification serviceaanvraag voor Certificaatondertekening** in het dialoogvenster.  
    2.  **Blader** naar het pad om het nieuwe aanvraagbestand tot certificaatondertekening (.csr) op te slaan. Sla het bestand met de aanvraag voor certificaatondertekening (.csr) lokaal op.  
    3.  Klik op **Downloaden**. Het nieuwe Microsoft Intune CSR-bestand wordt gedownload en door Configuration Manager opgeslagen.   

    > [!IMPORTANT]
    > U moet een nieuwe aanvraag voor Certificaatondertekening downloaden. Gebruik een bestaand bestand niet of zal mislukken.  

2.  Ga naar de [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844), en meld u aan met de **dezelfde** Apple-ID die is gebruikt voor het eerder maken en vernieuwen van de APNs-certificaat dat u in de zelfstandige versie van Intune gebruikt.

    ![Aanmeldingspagina voor Apple Push Certificates-Portal](/sccm/mdm/deploy-use/media/mdm-change-apns-portal.png)

3.  Selecteer het APNs-certificaat dat u gebruikt in zelfstandige versie van Intune en klik vervolgens op **vernieuwen**.   

    ![Dialoogvenster APNs vernieuwen](/sccm/mdm/deploy-use/media/mdm-change-renew-apns.png)

4.  Selecteer het APNs-certificaat ondertekenen CSR-bestand dat u lokaal hebt gedownload en klik vervolgens op **uploaden**.

    ![Aanmeldingspagina voor Apple Push Certificates-Portal](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-upload.png)  
5.  Selecteer de dezelfde APNs en klik vervolgens op **downloaden**. Download het certificaat voor APNs (.pem) en sla het bestand lokaal.  

    ![Aanmeldingspagina voor Apple Push Certificates-Portal](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-download.png)

6.  De vernieuwd APNs-certificaat geüpload naar de hybride-tenant met dezelfde Apple-ID als voordat.

    1.  Ga in de Configuration Manager-console naar **beheer** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en kies **Platforms configureren** &gt; **iOS**.  
    2.  In de **eigenschappen van Microsoft Intune-abonnement** selecteert u de **APNs-certificaat** tabblad en klik op de **iOS en MAC OS X (MDM)-inschrijving inschakelen** selectievakje.  
    3.  Klik op **Bladeren**en ga naar het APNs-certificaatbestand (.cer) dat u bij Apple hebt gedownload. Configuration Manager geeft de APNs-certificaatinformatie weer. Klik op **OK** om het APNs-certificaat op te slaan in Intune.  

        ![Intune-abonnement eigenschappenpagina - iOS](/sccm/mdm/deploy-use/media/mdm-change-subscription-properties-ios.png)

### <a name="enable-android-enrollment"></a>Android-registratie inschakelen
1. Ga in de Configuration Manager-console naar **beheer** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en kies **Platforms configureren** &gt; **Android**.  
2. Selecteer **Android-inschrijving inschakelen** en klik op **OK**.

### <a name="enable-windows-enrollment"></a>Windows-registratie inschakelen
1. Ga in de Configuration Manager-console naar **beheer** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en kies **Platforms configureren** &gt; **Windows**.  
2. Selecteer **Windows-registratie inschakelen** en klik op **OK**.

### <a name="enable-windows-phone-enrollment"></a>Windows Phone-inschrijving inschakelen
1. Ga in de Configuration Manager-console naar **beheer** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en kies **Platforms configureren** &gt; **Windows Phone**.  
2. Selecteer het platform dat u wilt inschakelen en op **OK**.


### <a name="next-steps"></a>Volgende stappen
Nadat de wijziging in de MDM-instantie voltooid is, controleert u de volgende stappen uit:
- Als de Intune-service detecteert dat een tenant MDM-instantie is gewijzigd, wordt verzonden uit een melding op alle geregistreerde apparaten in-en synchroniseren met de service (dit is buiten het regelmatig geplande inchecken). Daarom nadat de MDM-instantie voor de tenant is gewijzigd van Intune standalone in hybride, alle apparaten die zijn ingeschakeld en online maakt verbinding met de service, ontvangt de nieuwe MDM-instantie en worden beheerd door hybride voortaan. Er zijn geen gevolgen heeft voor het beheer en beveiliging van deze apparaten.
- Zelfs voor apparaten die ingeschakeld en online zijn tijdens (of kort na) de wijziging in de MDM-instantie, wordt er een vertraging van maximaal acht uur (afhankelijk van de timing van de volgende geplande reguliere inchecken) zijn voordat deze apparaten zijn geregistreerd bij de service onder de nieuwe MDM-instantie.    

  > [!IMPORTANT]
  > Tussen het moment waarop het wijzigen van de MDM mislukken-instantie en wanneer de vernieuwd APNs-certificaat is geüpload naar de nieuwe instantie, nieuwe apparaatinschrijvingen en apparaat incheckt voor iOS-apparaten. Het is daarom belangrijk dat u bekijken en het APNs-certificaat naar de nieuwe instantie zo snel mogelijk na de wijziging in de MDM-instantie uploaden.

- Gebruikers kunnen snel aan de nieuwe MDM-instantie wijzigen door het handmatig starten van een selectievakje in van het apparaat naar de service. Gebruikers kunnen dit eenvoudig doen met behulp van de bedrijfsportal-app en een apparaatgeschiktheidscontrole is gestart.
- Om te valideren of dingen goed werken nadat apparaten hebt ingecheckt en gesynchroniseerd met de service na de wijziging in de MDM-instantie, zoekt u de apparaten de Configuration Manager-console. De apparaten die eerder zijn beheerd door Intune wordt nu weergegeven als beheerde apparaten in de Configuration Manager-console.    
- Er is een tussentijdse periode wanneer een apparaat offline gedurende de wijziging in de MDM-instantie en is als dat het apparaat wordt ingecheckt met de service. Om ervoor te zorgen dat het apparaat beveiligd en in werking tijdens deze periode tussentijdse blijft, blijft de volgende op het apparaat gedurende 7 dagen (of totdat het apparaat verbinding met de nieuwe MDM-instantie maakt en ontvangt van de nieuwe instellingen waarmee wordt de bestaande bestanden overschreven):
    - E-mailprofiel
    - VPN-profiel
    - Certificaat-profiel
    - Wi-Fi-profiel
    - Configuratieprofielen
- Nadat u de nieuwe MDM-instantie wijzigt, kan de gegevens in de Microsoft Intune-beheerconsole duren een week nauwkeurig rapporteren. De nalevingsstatussen in Azure Active Directory en op het apparaat worden echter nauwkeurige zodat het apparaat nog steeds worden beveiligd.
- Zorg dat de nieuwe instellingen die zijn bedoeld om de bestaande instellingen overschreven door dezelfde naam als de vorige scripts om ervoor te zorgen dat de oude instellingen overschreven. Anders wordt kunnen de apparaten eindigen met redundant profielen en beleidsregels.
    > [!TIP]   
    > Als een best practice moet u alle instellingen en configuraties, evenals implementaties, kort nadat de wijziging van de MDM-instantie is voltooid. Dit helpt ervoor te zorgen dat apparaten zijn beveiligd en dat actief wordt beheerd in de tijdelijke periode.   
-  Nadat u de MDM-instantie hebt gewijzigd, moet u de volgende stappen voor het valideren van nieuwe apparaten met succes zijn geregistreerd bij de nieuwe instantie uitvoeren:   
    - Een nieuw apparaat registreren
    - Zorg ervoor dat het nieuw ingeschreven apparaat wordt weergegeven in de Configuration Manager-console.
    - Een actie uitgevoerd, zoals vergrendelen op afstand van de beheerconsole voor het apparaat. Als dat lukt, wordt het apparaat wordt beheerd door de nieuwe MDM-instantie.
- Als u problemen met specifieke apparaten hebt, kunt u registratie ongedaan maken en registreren van de apparaten om op te halen ze verbonden met de nieuwe instantie van en worden beheerd zo snel mogelijk.
