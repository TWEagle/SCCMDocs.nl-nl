---
title: Mogelijkheden van Technical Preview 1605
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1605.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bafd028-1923-4463-9e3e-ee41bc0c437b
caps.latest.revision: "36"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8286b8d0f35717d1b1453fa76208c1539f3ffda4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1605-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1605 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1605 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.  

 **Bekende problemen in deze Technical Preview:**  

-   Met de technische Preview 1605, als u de eigenschappen van een beheerpunt bijwerken nadat deze is geïnstalleerd, ziet u mogelijk een fout in de console waardoor de-console te sluiten.  Als dit gebeurt, kunt u het beheerpunt verwijderen en opnieuw installeren van het beheerpunt met de gewenste instellingen. U kunt ook het beheerpunt vóór de installatie van Technical Preview 1605 wijzigen.  

-   Wanneer u de Windows Store voor bedrijven-functie met de technische Preview 1604 gebruiken en vervolgens een naar Technical Preview 1605 upgrade, kunt u de voorbereiding-gegevens niet meer weergeven. Alle andere blijft functioneel werken. Als u geïmplementeerd met de technische Preview 1604, u vrijgegeven blijft na de installatie van Technical Preview 1605 en hoeft er geen verdere actie te ondernemen.  

 **Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="BKMK_PerAppVPN"></a>Per app VPN voor Windows 10-apparaten  
 Voor Windows 10-apparaten die worden beheerd met Configuration Manager met Intune, kunt u een lijst met apps die automatisch een VPN-verbinding die u hebt geconfigureerd via de Configuration Manager-beheerconsole opent toevoegen. U hebt de mogelijkheid van VPN-verkeer beperkt tot de apps of waarmee alle verkeer via de VPN-verbinding kan worden voortgezet.  

 **Vereisten**:  

-   Configuration Manager met Intune  

-   Een Windows 10 VPN-profiel dat is geïmplementeerd op ten minste één apparaat  

##  <a name="BKMK_InstallSU"></a>Verbeteringen aan de takenreeks installeren software-updates  
 De volgende verbeteringen zijn aangebracht aan de takenreeks Software-Updates installeren:  

-   Een nieuwe takenreeksvariabele, SMSTSSoftwareUpdateScanTimeout, is beschikbaar om u te bieden de mogelijkheid om te bepalen van de time-out van de controle van de software-updates tijdens de installatie van software-updates-takenreeksstap. De standaardwaarde is 30 minuten.  

-   Er zijn verbeteringen in logboekregistratie. Het bestand smsts.log logboek bevat nieuwe logboekvermeldingen die verwijzen naar andere logboekbestanden die u helpt bij het oplossen van problemen tijdens het installatieproces van de software-updates.  

##  <a name="BKMK_PrepareConfigMgrClient"></a>Verbeteringen aan de ConfigMgr-Client voorbereiden voor vastleggen takenreeksstap  
 De ConfigMgr-Client voorbereiden stap wordt de Configuration Manager-client, in plaats van alleen het verwijderen van belangrijke gegevens nu volledig verwijderd. Wanneer de takenreeks wordt geïmplementeerd voor de vastgelegde besturingssysteeminstallatiekopie wordt deze elke keer dat een nieuwe Configuration Manager-client installeren.  

##  <a name="BKMK_Grace"></a>Respijtperiode voor vereiste toepassingsimplementaties  
 In sommige gevallen kunt u gebruikers meer tijd te geven voor het installeren van vereiste toepassingsimplementaties buiten een deadlines die u hebt geconfigureerd. Als een eindgebruiker is alleen van vakantie geretourneerd, moeten ze mogelijk lang wachten terwijl als achterstallig toepassing implementaties zijn geïnstalleerd. Ze kunnen echter nog steeds onmiddellijk de toepassing op elk gewenst moment die ze willen installeren.  

 Om dit probleem op te lossen kunt u nu definiëren een **respijtperiode** door Configuration Manager-clientinstellingen implementeren naar een verzameling.  

 Voor het configureren van de respijtperiode is, moet u de volgende acties uitvoeren:  

1.  Op de **Computeragent** pagina configureren van clientinstellingen, de nieuwe eigenschap **respijtperiode voor afdwingen na de implementatie (uren) deadline** met een waarde tussen **1** en **120** uur.  

2.  In een nieuw toepassingsimplementatie, of in de eigenschappen van een bestaande implementatie op de **planning** pagina, selecteert u het selectievakje **afdwingen van deze implementatie op basis van gebruikersvoorkeuren uitstellen**, tot de respijtperiode die in de clientinstellingen is gedefinieerd.  

     Alle implementaties die dit selectievakje ingeschakeld hebben en die gericht zijn op apparaten die u ook de client-instelling geïmplementeerd, wordt de respijtperiode is gebruikt.  

 In deze release is de respijtperiode die u configureert niet gebruikt door de clients. Als u een respijtperiode configureren en het selectievakje selecteert, wordt de toepassing geïnstalleerd in het eerste niet-zakelijk venster die de gebruiker geconfigureerd na de deadline.  

 Soortgelijke opties zijn toegevoegd aan de wizard voor implementatie van software-updates, de wizard regels automatische implementatie en eigenschappenpagina's. Maar worden deze momenteel niet geïmplementeerd in deze technical preview.  

##  <a name="BKMK_Remote"></a>Nieuwe ervaring voor acties extern apparaat  
 De ervaring voor het uitvoeren van acties extern apparaat van de Configuration Manager-console is verbeterd.  
Algemene acties zoals **buiten gebruik stellen/wissen**, **wachtwoordcode opnieuw instellen**, **vergrendelen op afstand**, en **Bypass van Activeringsvergrendeling** kan nu worden gevonden in de **acties extern apparaat** menu toegankelijk is vanuit de **activa en naleving** werkruimte.  

 ![Schermopname van nieuwe acties extern apparaat](media/New-Remote-Device-Actions.png)  

 U kunt de status voor elk van deze bewerkingen in de volgende locaties vinden:  

-   In het detailvenster wanneer u een apparaat selecteert de **apparaten** knooppunt.  

-   Op de **eigenschappen** pagina voor een apparaat.  

-   Op de hoofdpagina van de **apparaten** knooppunt (niet alle kolommen mogelijk zijn standaard zichtbaar).  

 Zie voor meer informatie over iOS-activeringsvergrendeling [iOS-apparaten met Activeringsvergrendeling overslaan voor Configuration Manager-beschermen](/sccm/mdm/deploy-use/manage-ios-activation-lock), met name de **huidige bekende problemen met Activeringsvergrendeling overslaan in de Configuration Manager Technical Preview** sectie.  

##  <a name="BKMK_WSFB"></a>Windows Store voor bedrijven-apps  
 De [Windows Store voor bedrijven](https://www.microsoft.com/business-store) kunt u vinden en apps voor uw organisatie, kopen, afzonderlijk of in volume. De store koppelt aan Configuration Manager, kunt u volume-aankoopprogramma gekochte apps bijvoorbeeld beheren vanuit de Configuration Manager-console:  

-   U kunt de lijst met aangeschafte apps synchroniseren met Configuration Manager  

-   Apps die zijn gesynchroniseerd in de Configuration Manager-console worden weergegeven en kunt u ze vervolgens net als alle andere apps implementeren  

-   Elke 24 uur Configuration Manager app-licentie-informatie uit de store downloadt en kunt u dit bekijken in de Configuration Manager-console  

 In de release van technical preview 1604 kan u synchroniseert en apps uit de Windows Store voor bedrijven weergeven in de Configuration Manager-console. In deze release, hebben we de mogelijkheid om te maken en implementeren van Configuration Manager-toepassingen van gesynchroniseerde store-apps toegevoegd.  

### <a name="set-up-windows-store-for-business-synchronization"></a>Windows Store voor bedrijven-synchronisatie instellen  

1.  Registreren bij Azure Active Directory, Configuration Manager als beheerprogramma 'Webtoepassing en/of Web-API'. Hierdoor krijgt u een client-ID die u later nodig hebt.  

    1.  In het Active Directory-knooppunt van [https://manage.windowsazure.com](https://manage.windowsazure.com), selecteer uw Azure Active Directory en klik vervolgens op **toepassingen** > **toevoegen**.  

    2.  Klik op **mijn organisatie ontwikkelt toepassing toevoegen**.  

    3.  Voer een naam voor de toepassing, selecteer **webtoepassing** en/of **Web API**, klikt u vervolgens op de **volgende** pijl.  

    4.  Voer dezelfde URL voor zowel de **aanmeldings-URL** en **App ID URI**. De URL kan van alles zijn en hoeft niet omzetten in een echte adres. Bijvoorbeeld, kunt u **https://&lt;uwdomein > / sccm**.  

    5.  Voltooi de wizard.  

2.  In Azure Active Directory, maakt u een clientsleutel voor het geregistreerde beheerprogramma.  

    1.  Markeer de toepassing die u zojuist hebt gemaakt en klik op **configureren**.  

    2.  Onder **sleutels**, selecteert u een duur in de lijst en klikt u op **opslaan**. Hiermee wordt een nieuwe clientsleutel gemaakt. Verlaat deze pagina totdat u is vrijgegeven Windows Store voor bedrijven naar Configuration Manager.  

3.  In de Windows Store voor bedrijven, configureert u de Configuration Manager als het winkelbeheerprogramma.  

    1.  Open [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/managementtools) en meld u als u wordt gevraagd.  

    2.  Accepteer de gebruiksvoorwaarden indien nodig.  

    3.  Onder **beheerhulpprogramma's**, klikt u op **beheerprogramma toevoegen**.  

    4.  In **zoeken voor het hulpprogramma met de naam**, typ de naam van de toepassing die u eerder in Add hebt gemaakt en klik vervolgens op **toevoegen**.  

    5.  Klik op **activeren** naast de toepassing die u zojuist hebt geïmporteerd.  

    6.  In de **Apps met offline licentie weergeven** wizard, klikt u op **Ja** als u toestaan dat toepassingen offline licentie wilt aan te schaffen.  

4.  Koop ten minste één app in de Windows Store voor bedrijven.  

5.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, klikt u vervolgens op **Windows Store voor bedrijven.**  

6.  Op de **Start** tabblad, in de **maken** groep, klikt u op **toevoegen Windows Store voor bedrijven-Account**.  

7.  Uw tenant-ID, client-id en clientsleutel uit Azure Active Directory toevoegen en voltooi de wizard.  

8.  Wanneer u klaar bent, ziet u het account dat u hebt geconfigureerd in de **Windows Store voor bedrijven-Accounts** in de Configuration Manager-console.  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taak en vervolgens laat ons weten hoe het is gegaan met behulp van ons feedbackformulier op de [Configuration Manager-feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

 Maken en implementeren van een Configuration Manager-toepassing in een Windows Store voor bedrijven offline gelicentieerde app.  

1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentiegegevens voor Store-Apps**.  

2.  Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.  

 Een Configuration Manager-toepassing wordt gemaakt met van de Windows Store voor bedrijven-app. U kunt implementeren en bewaken van deze toepassing, net als elke andere Configuration Manager-toepassing.  

> [!IMPORTANT]  
>  Wanneer u een Configuration Manager-toepassing met één implementatietype van een offline gelicentieerde app maakt, kan dit worden geïmplementeerd op apparaten met MDM beheerde en tevens worden beheerd met Configuration Manager-client. Als u een app implementeert met meerdere implementatietypen probeert, mislukt de installatie.  
>   
>  U kunt geen momenteel online gelicentieerde apps met Configuration Manager implementeren.  

##  <a name="BKMK_VPP2"></a>Algemene verbeteringen van de volume-aankoopprogramma gekochte apps  

-   In deze release, volume-aankoopprogramma gekochte apps uit de Windows Store voor bedrijven en de iOS app store zijn samengevoegd in dezelfde weergave **licentie-informatie voor Apps opslaan**.  

-   Voor iOS volume-aankoopprogramma gekochte apps, het tabblad Apple Volume Purchase Program is verwijderd uit de **App-pakket voor iOS-Browser** dialoogvenster in de wizard toepassing maken. Volg deze stappen voor het maken van een volume-aankoopprogramma gekochte app voor iOS:  

    1.  1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentiegegevens voor Store-Apps**.  

    2.  2.  Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.  

-   De locatie die u kunt verkrijgen en uploaden van een Apple VPP-token voor volume-aankoopprogramma gekochte apps in de Configuration Manager-console is gewijzigd. U kunt dit nu doen de **Admin** werkruimte onder de **Cloudservices** > **Apple Volume Purchase Program-Tokens** knooppunt.  

##  <a name="BKMK_VPP"></a>Ondernemingsgegevensbescherming (EDP)  
 U kunt configuratie-items die u enterprise data protection (EDP)-beleid implementeert, inclusief zodat u kunt ervoor kiezen uw beveiligde apps, uw EDP-beveiligingsniveau en het zoeken van bedrijfsgegevens op het netwerk laten maken. Zie voor meer informatie over EDP, de volgende onderwerpen:  

-   [Uw Ondernemingsgegevens beveiligen met ondernemingsgegevensbescherming (EDP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)  

-   [Een enterprise data protection (EDP)-beleid met behulp van System Center Configuration Manager maken en implementeren](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-sccm)  

##  <a name="BKMK_End"></a>Eindgebruikers kunnen apps installeren vanuit de bedrijfsportal  
 Een on-premises MDM in System Center Configuration Manager versie 1511 werd geïntroduceerd. In eerdere versies van u kan toepassingen implementeren op MDM beheerde Windows-10-apparaten met een implementatiedoel **vereist** installeren voor on-premises MDM-beheerde apparaten.  

 In deze release kunt u nu apps met een implementatiedoel van implementeren **beschikbaar** voor gebruikers van de lokale MDM beheerde Windows 10-computers en gebruikers kunnen deze apps zelf nu installeren via de bedrijfsportal.
In deze technical preview als de bedrijfsportal geopend voor meer dan 15 minuten is, ziet de gebruiker een foutbericht weergegeven. U kunt het probleem omzeilen, start opnieuw op de bedrijfsportal.  

### <a name="before-you-start"></a>Voordat u begint  

#### <a name="server-prerequisites"></a>Server-vereisten  

-   .NET 4.5 of hoger (opnieuw opstarten noodzakelijk)  

-   PowerShell 3.0 voor configuratiescript (opnieuw opstarten noodzakelijk)  

#### <a name="client-prerequisites"></a>Clientvereisten  

-   Windows 10 Desktop 1511 (build 10586.218 OS) of hoger  

#### <a name="general-prerequisites"></a>Algemene vereisten  

-   Zorg ervoor dat u hebt de [voorbereiding stappen voor On-premises Mobile Device Management](https://technet.microsoft.com/library/mt613153.aspx) en [uw apparaten ingeschreven](https://technet.microsoft.com/library/mt627870.aspx).  

-   Installeren voor de toepassing van de beste ervaring als via de bedrijfsportal, zorg ervoor dat Configuration Manager heeft een actieve verbinding met Microsoft Intune.  

-   Als u de bulkinschrijving optie kiest, configureert u gebruikersapparaataffiniteit voor het ingeschreven apparaat voordat u dit scenario.  

### <a name="configuration-steps"></a>Configuratiestappen  

#### <a name="install-the-application-catalog-roles-and-enable-mobile-device-management-support"></a>Installeer de Application Catalog-rollen en ondersteuning van beheer van mobiele apparaten inschakelen  

1.  De Application Catalog-webservice en website-rollen toevoegen  

    1.  Selecteer **HTTPS modus** en de **mobiele apparaten te gebruiken deze Application Catalog-webservice** optie.  

    2.  De beperkingen in deze Technical Preview:  

        -   U moet eventuele bestaande Application Catalog-rollen verwijderen voordat u de optie selecteert om toe te staan van mobiele apparaten verbinding moeten maken.  

        -   Zorg ervoor dat er slechts één set met Application Catalog-rollen en de rollen op hetzelfde sitesysteem met het inschrijvingspunt en Inschrijvingsproxypunt punt rollen worden geplaatst.  

2.  Controleer of de volgende onderdelen zijn operationele vanuit de node Componentstatus in de Configuration Manager-console:  

    -   **SMS_AWEBSVC_CONTROL_MANAGER**  

    -   **SMS_DMAPPSVC_CONTROL_MANAGER**  

    -   **SMS_DMCONTENTSVC_CONTROL_MANAGER**  

    -   **SMS_PORTALWEB_CONTROL_MANAGER**  

### <a name="configure-boundaries"></a>Grenzen configureren  
 Vereiste grenzen voor alleen intranet distributiepunten configureren.  

> [!NOTE]  
>  Alleen de grenzen van IPv4-bereik worden ondersteund op dit moment voor beheer van mobiele apparaten.  

### <a name="deploy-the-company-portal-application-and-configuration"></a>Implementeer de toepassing bedrijfsportal en de configuratie  

1.  Het configuratiescript die deel uitmaakt van de technical preview gebruiken voor het voorbereiden van de bedrijfsportal-App-implementatie en configuratie:  

    1.  Open een verhoogde PowerShell-opdrachtvenster.  

    2.  Voer **set-executionPolicy RemoteSigned**  

    3.  Vanuit de map  **&lt;SCCM-installatiemap\>\cd.latest\SMSSETUP\TOOLS\MDM** uitvoeren **.\ConfigurationScript.ps1**  

     Het configuratiescript doet het volgende:  

    1.  Hiermee maakt u een Configuration Manager-toepassing met een Windows app pakket implementatie type met **CompanyPortalOnPremisesMDM.appx** in dezelfde map.  

    2.  Maakt een configuratie-item en de configuratiebasislijn die u configureert u de bedrijfsportal.  

    3.  Zowel de configuratiebasislijn en de toepassing wordt geïmplementeerd en wordt de toepassing naar alle distributiepunten toegevoegd.  

    > [!NOTE]  
    >  Als de Application Catalog-rollen niet dezelfde locatie bevindt als de primaire site, moet u de volgende acties uitvoeren:  
    >   
    >  -   In de **activa en naleving** werkruimte, zoek de **OnPremMDM Portal configuratie CI - URL's voor server** configuratie-item  
    > -   Wijzig de **Compliantieregels** waarde met de volledig gekwalificeerde domeinnaam van het sitesysteem waar de Application Catalog-rollen zich bevinden.  

2.  Zodra de toepassing bedrijfsportal en de configuratie van beide worden geïmplementeerd, Controleer of de toepassing en configuratie-basislijn die compatibel zijn voor het opgegeven apparaat via **implementaties** gedeelte van de Configuration Manager-console. De bedrijfsportal wordt weergegeven als **bedrijfsportal (Technical Preview)** in het menu Start op het apparaat.  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taken en vervolgens laat ons weten hoe het is gegaan met behulp van ons feedbackformulier op de [Configuration Manager-feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

1.  Implementeren van verschillende toepassingen met ondersteunde implementatietypen die aan een Gebruikersverzameling met een implementatiedoel **beschikbaar**. Voor deze technical preview toepassingen die goedkeuring door beheerder vereisen worden niet ondersteund en worden niet weergegeven in de bedrijfsportal.  

2.  Gebruikers kunnen vervolgens zoeken naar en apps installeren vanuit de bedrijfsportal.  

     Nadat u de bedrijfsportal opent, ziet u een dialoogvenster voor verificatie met de naam **System Center Configuration Manager** Active Directory-referenties van de gebruiker opgeven (in de vorm van user@domain of domein\gebruiker) om aan te melden.  

##  <a name="BKMK_SW1"></a>Nieuwe tabbladen voor Updates en besturingssystemen in Software Center  
 In deze release zijn de volgende wijzigingen aangebracht voor het verbeteren van de indeling van de toepassing Software Center:  

-   De **toepassingen** tabblad is gesplitst in drie verschillende tabbladen voor **Updates**, **besturingssystemen** (die beide eerder gevonden in de **Filters** lijst), en **toepassingen**.  

##  <a name="BKMK_ServerGroups"></a>Een servergroep onderhouden  
 Technical Preview voor System Center Configuration Manager versie 1511, de mogelijkheid te maken van een verzameling waarin alle apparaten in de verzameling gezamenlijk een servergroep opgenomen. Vervolgens, kan de instellingen van de server te gebruiken bij het implementeren van software-updates aan de servergroep, besturingselement het percentage van computers die zijn bijgewerkt op elk gewenst configureren en configureert u PowerShell-scripts voor vóór en na de implementatie om aangepaste acties worden uitgevoerd.  

 Technical Preview voor System Center Configuration Manager, versie 1605, voegt de mogelijkheid om bij te werken van de computers in de servergroep in een bepaalde volgorde definiëren, voegt uitgebreide controle om de status voor de computers in de servergroep te bekijken en biedt de mogelijkheid om de implementatievergrendeling gewist die nuttig is wanneer clients installatie van de software-updates is mislukt en worden zo wordt voorkomen dat andere clients hun software-updates installeren.  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taken en vervolgens laat ons weten hoe het is gegaan met behulp van ons feedbackformulier op de [Configuration Manager-feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

-   Ik kan een collectie met een servergroep maken. Voor deze test kunt u uw verzamelde lidmaatschapsregels met 2 machines in deze verzameling.   

-   Ik kan opgeven dat computers in de servergroep software-updates in een bepaalde volgorde op basis van de server-instellingen voor de verzameling installeren. Gebruik de voorbeeldscripts in de procedure om de scripts voor vóór en na de implementatie.  

-   Ik kan een software-update implementeren op deze verzameling. De bestanden start.txt en end.txt-bestanden (gemaakt op basis van de voorbeeldscripts) bekijken in C:\temp en controleer of de begin- en eindtijden voor de implementatie op de computers in de servergroep. Controleer het bestand updatesdeployment.log voor meer informatie.  

#### <a name="to-create-a-collection-for-a-server-group"></a>Een verzameling van een servergroep maken  

1.  [Maak een apparaatverzameling](https://technet.microsoft.com/library/gg712295.aspx) die de computers in de servergroep bevat.  

2.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**, met de rechtermuisknop op de verzameling waartoe de computers in de servergroep en klik vervolgens op **eigenschappen**.  

3.  Op de **algemene** tabblad **alle apparaten zijn onderdeel van de servergroep met dezelfde**, en klik vervolgens op **instellingen**.  

4.  Op de **instellingen servergroep** pagina, geeft u een van de volgende instellingen:  

    -   **Toestaan dat een percentage van de machines tegelijk wordt bijgewerkt**: Hiermee geeft u op dat alleen een bepaald percentage van clients op elk gewenst moment worden bijgewerkt. Als bijvoorbeeld de verzameling 10 clients heeft en de verzameling is geconfigureerd voor het bijwerken van 30% bedraagt van clients op hetzelfde moment wordt alleen 3 clients software-updates op elk moment installeren.  

    -   **Toestaan dat een aantal machines tegelijk wordt bijgewerkt**: Hiermee geeft u op dat alleen een bepaald aantal clients op elk gewenst moment worden bijgewerkt.  

    -   **Geef de reeks onderhoud**: Geeft aan dat de clients in de verzameling wordt bijgewerkt één op een tijdstip in de volgorde die u configureert. Een client wordt alleen software-updates installeren nadat de installatie van de software-updates van de client wordt dan deze in de lijst is voltooid.  

5.  Geef op of een script vóór implementatie (knooppuntcorrectie) of een script ná implementatie (knooppunthervatting) wilt gebruiken.  

    > [!TIP]  
    >  Hier volgen voorbeelden die u gebruiken kunt bij het testen voorafgaand aan de implementatie en na de implementatie scripts die de huidige tijd naar een tekstbestand schrijven:  
    >   
    >  **Voorafgaand aan de implementatie**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Na de implementatie**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-group-and-monitor-status"></a>Implementeren van software-updates aan de groep en de monitor status van de server  

1.  [Software-updates implementeren](https://technet.microsoft.com/library/gg712304.aspx) aan de verzameling van de groep server.  

2.  [De implementatie van de software-update controleren](https://technet.microsoft.com/library/gg712304.aspx). Naast de standaard bewakingsweergaven voor implementatie van software-updates, worden een nieuwe statusbeschrijving wordt weergegeven wanneer een client wacht op zijn beurt de softwareupdates te installeren. **Wachten op vergrendeling** voor deze nieuwe status wordt weergegeven.  

#### <a name="to-clear-the-deployment-locks-for-computers-in-a-server-group"></a>De vergrendelingen voor Clusterimplementatie voor computers in een servergroep wissen  

1.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**, en klik op de verzameling om vergrendelingen van servergroepimplementaties wissen.  

2.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **wissen Server groep implementatie vergrendeld**. Wanneer clients installatie van de software-updates is mislukt en worden zo wordt voorkomen dat andere clients hun software-updates installeren, kunnen de implementatievergrendeling handmatig worden gewist.  

##  <a name="BKMK_ATP"></a>Ondersteuning voor Windows Defender Advanced Threat Protection-service  
 Windows Defender geavanceerde Threat Protection (ATP) is een nieuwe service waarmee ondernemingen te detecteren, onderzoeken en reageren op geavanceerde aanvallen in hun netwerken. Meer informatie over [Windows Defender ATP](https://blogs.windows.com/windowsexperience/2016/03/01/announcing-windows-defender-advanced-threat-protection). Configuration Manager kunt u helpen bij het vrijgeven en controleren van beheerde verjaardagseditie van Windows 10-clientapparaten.  

### <a name="try-it-now"></a>Probeer het nu!  
 Voer de volgende taken en vervolgens laat ons weten hoe het is gegaan met behulp van ons feedbackformulier op de [Configuration Manager-feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

-   Onboarding van apparaten tot de onlineservice Windows Defender Advanced Threat Protection (ATP)  

-   Controleer de implementatie van Windows Defender ATP op beheerde apparaten  

 **Vereisten**  

-   Abonnement op de Windows Defender Advanced Threat Protection-onlineservice  

-   Clients met Windows 10, Verjaardag Edition (build 14328 en hoger)  

-   Maak een configuratiebestand voor de voorbereiding van client  

    ##### <a name="how-to-create-an-onboarding-configuration-file"></a>Het maken van een configuratiebestand voorbereiden  

    1.  Aanmelden bij de Windows Defender ATP-onlineservice  

    2.  Klik op de **Client op twee locaties** menu-item  

    3.  Selecteer **System Center Configuration Manager** en klik op **downloadpakket**.  

    4.  Download het bestand gecomprimeerd archief (.zip) en pak de inhoud.  


##### <a name="onboard-devices-for-windows-defender-atp"></a>Onboarding van apparaten voor Windows Defender ATP  

1.  Navigeer in de Configuration Manager-console **activa en naleving** > **overzicht** > **Endpoint Protection** > **Windows Defender ATP-beleid** en klik op **Windows Defender ATP-beleid maken**. De Wizard Windows Defender ATP-beleid wordt geopend.  

2.  Typ de **naam** en **beschrijving** voor de Windows Defender ATP-beleid en selecteer **Onboarding**. Klik op Volgende.  

3.  **Blader** naar het configuratiebestand geleverd door Windows Defender ATP cloud service-tenant van uw organisatie. Klik op **Volgende**.  

4.  Geef de bestandsvoorbeelden die worden verzameld en gedeeld vanaf beheerde apparaten voor analyse.  

    -   **Geen** – geen voorbeeldbestanden worden verzameld voor analyse  

    -   **Draagbare uitvoerbare bestanden** : bestanden zoals programma-bestanden (.exe), koppeling van de dynamische-bibliotheek (.dll), lettertypebestanden en vergelijkbare bestanden dat kunnen worden misbruikt in cyberattacks worden verzameld en gedeeld voor analyse  

     Klik op **Volgende**.  

5.  Bekijk het overzicht en voltooi de wizard.  

6.  U kunt nu door te klikken op het Windows Defender ATP-beleid voor beheerde clientcomputers implementeren **implementeren**.  

##### <a name="monitor-windows-defender-atp"></a>Monitor voor Windows Defender ATP  

1.  Navigeer in de Configuration Manager-console **bewaking** > **overzicht** > **beveiliging** en klik vervolgens op **Windows Defender ATP**.  

2.  Controleer het Windows Defender Advanced Threat Protection-dashboard.  

    -   **Implementatiestatus van Windows Defender Agent** : het aantal en het percentage van de in aanmerking komende beheerde clientcomputers met actieve vrijgegeven voor Windows Defender ATP-beleid  

    -   **Status van Windows Defender ATP-Agent** – Percentage computerclients rapportage over de status voor hun Windows Defender ATP-agent  

        -   **In orde** -goed werkt  

        -   **Inactieve** -er zijn geen gegevens verzonden naar service periode  

        -   **De status van agent** -de systeemservice voor de agent in Windows is niet actief  

        -   **Er is geen vrijgegeven** - beleid is toegepast, maar de agent geen beleid vrijgeven heeft gerapporteerd  

##  <a name="BKMK_DHA"></a>On-premises Apparaatstatusverklaring  
 De statusverklaring voor Windows 10-apparaten kan nu worden geconfigureerd om te communiceren met de on-premises infrastructuur. Beheerders kunnen opgeven of rapportage wordt uitgevoerd via de cloud of on-premises resources. Lokale voor health attestation reporting is ingeschakeld, kan een URL worden opgegeven voor de service. Hierdoor kunnen client-pc's zonder internettoegang inschakelen en beheren met behulp van de health attestation van apparaten.  

### <a name="enable-health-attestation-for-on-premises-devices"></a>Statusverklaringen inschakelen voor on-premises apparaten  
 In 1605, hebben we enkele fouten gedetecteerd in de Technical Preview 1604 opgelost.  Probeer het uit configureren met behulp van clientagentinstellingen van lokale Health Attestation-Service.  

1.  Navigeer in de Configuration Manager-console **beheer** > **overzicht** > **clientinstellingen**, en stel vervolgens **on-premises gebruiken Health Attestation-Service** naar **Ja**.  

2.  Geef de **URL op voor de on-premises statusverklaringsservice**en klik op **OK**.  

##  <a name="BKMK_RestartOptions"></a>Nieuwe opties voor Windows 10-clients opnieuw opstarten na installatie van software-update  
 Wanneer een software-update waarvoor opnieuw opstarten wordt geïmplementeerd met behulp van Configuration Manager en geïnstalleerd op een computer opnieuw is gepland en een dialoogvenster voor opnieuw opstarten wordt weergegeven. Op dit moment voor Windows 8 en hoger, als u afsluiten en start de computer met behulp van de opties voor energiebeheer in Windows (in plaats van in het dialoogvenster voor opnieuw opstarten), blijft van het dialoogvenster opnieuw opstarten nadat de computer opnieuw wordt opgestart en de computer moet opnieuw worden opgestart voor de ingestelde deadline. In deze technical preview, de optie voor het **bijwerken en opnieuw opstarten** en **bijwerken en afsluiten** beschikbaar zullen zijn op Windows 10-computers in de Windows-energiebeheer wanneer er een te worden opgestart voor een software-update van Configuration Manager. Nadat u een van deze opties hebt gebruikt, wordt het dialoogvenster voor opnieuw opstarten niet weergegeven nadat de computer opnieuw wordt opgestart.  

##  <a name="BKMK_IMEI"></a>Vooraf declareren van apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer  
 U kunt apparaten in Bedrijfseigendom nu identificeren door het importeren van hun nummers international station mobile equipment identity (IMEI-nummer). U kunt een door komma's gescheiden waarden (.csv)-bestand met IMEI-nummers van apparaten uploaden of u kunt de apparaatgegevens handmatig invoeren.  U kunt ook importeren serienummers voor iOS-apparaten.  Geïmporteerde gegevens wordt de eigendom van de apparaten die worden ingeschreven als 'Bedrijfseigendom' ingesteld.  Een Intune-licentie is nog steeds vereist zijn voor elke gebruiker die toegang heeft tot de service.  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taken en vervolgens laat ons weten hoe het is gegaan met behulp van ons feedbackformulier op de [Configuration Manager-feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

-   Een set van IMEI-nummers in een CSV-bestand importeren. Elke rij mag de IMEI-nummer gevolgd door een veld met details.  

-   IMEI-nummers handmatig importeren vanuit de Configuration Manager-console.  

-   Een set van iOS-serienummers in een CSV-bestand importeren. Elke rij bevat ook een getal gevolgd door de details voor het apparaat.  

##### <a name="pre-declare-corporate-owned-devices-with-imei-or-ios-serial-number"></a>Vooraf declareren van apparaten in bedrijfseigendom met IMEI-nummer of iOS-serienummer  

1.  Ga in de Configuration Manager-console **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **Pre-declared apparaten**, en klik vervolgens op **Pre-declared apparaten maken**. De wizard Pre-declared apparaten wordt geopend.  

2.  Geef op hoe u gegevens van een apparaat wilt:  

    -   **Upload een CSV-bestand met IMEI-nummers en gegevens** : als u wilt uploaden van een lijst met getallen, Zie stap 3.  

    -   **IMEI-nummers en gegevens handmatig toevoegen** : als u wilt gegevens handmatig invoeren, typt u de IMEI-nummer of iOS-serienummer en de details voor de apparaten en gaat u verder met stap 4.  

3.  Blader naar het CSV-bestand met de gegevens voor apparaten in Bedrijfseigendom vooraf declareren voor geüploade bestanden. Het bestand moet de volgende indeling, met uitzondering van de eerste rij (alleen richtlijnen ter) hebben:  

    |**IMEI-NUMMER #**|**iOS-serienummer**|**BESTURINGSSYSTEEM**|**Details**|
    |---|---|---|---|
    |123456789012345||WINDOWS|Windows-apparaat eigendom van het bedrijf|
    |123456789012|A0BCD0EFGH0J|IOS|Bedrijfseigen iOS-apparaten|
    |123456789012346||ANDROID|Android-apparaat eigendom van het bedrijf|

     **Kolommen:**  

    -   Kolom 1: IMEI-nummer: ofwel een IMEI-nummer of iOS-serienummer is vereist voor elke rij  

    -   Kolom 2: iOS-serienummer – alleen iOS-serienummers kan worden vooraf aangegeven. IMEI-nummer voor andere apparaatplatforms gebruiken  

    -   Kolom 3: Besturingssysteem van het apparaat (hoofdlettergebruik vereist):  

        -   IOS: alle iOS-apparaten  

        -   WINDOWS: bevat de Windows Phone, Windows 10 Mobile en Windows-pc 's  

        -   ANDROID: alle Android-apparaten  

    -   Kolom 4: Details: aanvullende informatie die wordt weergegeven in de Configuration Manager-console  

     Klik op **Volgende**.  

4.  Bekijk de resultaten van het bestand importeren. Eerder heeft geïmporteerde IMEI- of serienummers de details bijgewerkt met nieuwe informatie.  Klik op **volgende** om door te gaan of **terug** bijgewerkte gegevens behouden en voltooi de wizard.  
