---
title: Mogelijkheden in Technical Preview 1605 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1605.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bafd028-1923-4463-9e3e-ee41bc0c437b
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 8b3d472c586e704ee48e9825138c72f655d89492
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="capabilities-in-technical-preview-1605-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1605 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1605 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.  

 **Bekende problemen in deze Technical Preview:**  

-   Met de technische Preview 1605 als u de eigenschappen van een beheerpunt bijgewerkt nadat deze is geïnstalleerd, ziet u mogelijk een fout van de console die wordt afgedwongen de console dat te sluiten.  Als dit gebeurt, kunt u het beheerpunt verwijdert en opnieuw installeert het beheerpunt met de gewenste instellingen. U kunt ook het beheerpunt voor de installatie van technische Preview 1605 wijzigen.  

-   Wanneer u de Windows Store voor Business-functie met de technische Preview 1604 en vervolgens een naar technische Preview 1605 upgrade, kunt u de gegevens onboarding niet meer weergeven. Alle andere blijft functioneel werken. Als u geïmplementeerd met de technische Preview 1604, u vrijgegeven blijft na het installeren van technische Preview 1605 en hoeft er geen verdere actie te ondernemen.  

 **De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

##  <a name="BKMK_PerAppVPN"></a>Per app VPN voor Windows 10-apparaten  
 Voor Windows 10-apparaten worden beheerd met Configuration Manager met Intune, kunt u een lijst met apps die automatisch een VPN-verbinding die u hebt geconfigureerd via de Configuration Manager-beheerconsole opent toevoegen. U hebt de mogelijkheid van VPN-verkeer beperken tot die apps of kunt u doorgaan met het toestaan van al het verkeer via de VPN-verbinding.  

 **Vereisten voor**:  

-   Configuration Manager met Intune  

-   Een Windows 10-VPN-profiel dat is geïmplementeerd op ten minste één apparaat  

##  <a name="BKMK_InstallSU"></a>Verbeteringen in de takenreeks installeren software-updates  
 De volgende verbeteringen zijn aangebracht aan de takenreeks voor Software-Updates installeren:  

-   Een nieuwe takenreeksvariabele, SMSTSSoftwareUpdateScanTimeout, is beschikbaar om u te bieden de mogelijkheid om te bepalen van de time-out van de controle van de software-updates tijdens de installatie van software-updates wordt takenreeksstap. De standaardwaarde is 30 minuten.  

-   Er zijn ook voor verbeterde logboekregistratie. Het bestand smsts.log logboek bevat nieuwe logboekvermeldingen die verwijzen naar andere logboekbestanden die u helpt bij het oplossen van problemen tijdens het installatieproces van de software-updates.  

##  <a name="BKMK_PrepareConfigMgrClient"></a>Verbeteringen in de Configuration Manager-Client voorbereiden voor vastleggen takenreeksstap  
 De ConfigMgr-Client voorbereiden stap wordt de Configuration Manager-client in plaats van alleen verwijderen sleutelinformatie nu volledig verwijderd. Wanneer de takenreeks de vastgelegde installatiekopie implementeert wordt wordt telkens wanneer een nieuwe Configuration Manager-client geïnstalleerd.  

##  <a name="BKMK_Grace"></a>Respijtperiode vereiste toepassingsimplementaties  
 In sommige gevallen kunt u waarmee gebruikers meer tijd voor het installeren van vereiste toepassingsimplementaties buiten een deadlines die u hebt geconfigureerd. Als een eindgebruiker net van vakantie is geretourneerd, moeten ze mogelijk geduld voor een Long-waarde als achterstallig toepassing implementaties worden geïnstalleerd. Ze kunnen echter nog steeds onmiddellijk de toepassing op elk gewenst moment die ze willen installeren.  

 Om te helpen bij het oplossen van dit probleem, kunt u nu definiëren een **respijtperiode** door de instellingen voor Configuration Manager-client implementeren op een verzameling.  

 De respijtperiode configureren, moet u de volgende acties uitvoeren:  

1.  Op de **Computeragent** pagina configureren van instellingen van de client de nieuwe eigenschap **respijtperiode voor afdwinging na implementatie deadline (uren)** met een waarde tussen **1** en **120** uur.  

2.  In een nieuwe implementatie van toepassing, of in de eigenschappen van een bestaande implementatie op de **planning** pagina, schakel het selectievakje **stellen afdwinging van deze implementatie volgens gebruikersvoorkeuren**, tot de respijtperiode gedefinieerd in de clientinstellingen.  

     De respijtperiode maakt gebruik van alle implementaties die dit selectievakje geselecteerd en die zijn gericht op apparaten waarop u ook de instelling voor client geïmplementeerd.  

 In deze release wordt de respijtperiode die u configureert niet gebruikt door de clients. Als u een respijtperiode configureren en het selectievakje selecteert, wordt de toepassing wordt geïnstalleerd in het eerste niet-business-venster dat de gebruiker geconfigureerd na de deadline.  

 Vergelijkbare opties zijn toegevoegd aan de implementatiewizard van software-updates, de wizard Regels voor automatische implementatie en de pagina eigenschappen. Deze worden echter niet momenteel geïmplementeerd in deze technische preview.  

##  <a name="BKMK_Remote"></a>Nieuwe ervaring voor externe apparaat acties  
 De ervaring voor het externe apparaat acties uit te voeren vanuit de Configuration Manager-console, is verbeterd.  
Algemene acties zoals **buiten gebruik stellen/wissen**, **wachtwoordcode opnieuw instellen**, **vergrendelen op afstand**, en **Bypass Activeringsvergrendeling** is nu te vinden de **externe apparaat acties** menu toegankelijk is via de **activa en naleving** werkruimte.  

 ![Schermafbeelding van nieuwe externe apparaat acties](media/New-Remote-Device-Actions.png)  

 U kunt de status voor elk van deze bewerkingen in de volgende locaties vinden:  

-   In het detailvenster worden weergegeven wanneer u een apparaat van de **apparaten** knooppunt.  

-   Op de **eigenschappen** pagina voor een apparaat.  

-   Op de hoofdpagina van de **apparaten** knooppunt (niet alle kolommen kunnen zijn standaard zichtbaar).  

 Zie voor meer informatie over iOS bypass van Activeringsvergrendeling [bescherming van iOS-apparaten met Activeringsvergrendeling overslaan voor Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock), met name de **huidige bekende problemen met Activeringsvergrendeling overslaan in de Configuration Manager Technical Preview** sectie.  

##  <a name="BKMK_WSFB"></a>Windows Store voor Business-apps  
 De [Windows Store voor bedrijven](https://www.microsoft.com/business-store) kunt u vinden en apps koopt voor uw organisatie, afzonderlijk of in volume. Verbinding maken met de store naar de Configuration Manager, kunt u beheren volume aangeschaft apps vanuit de Configuration Manager-console, bijvoorbeeld:  

-   U kunt de lijst met aangekochte apps te synchroniseren met Configuration Manager  

-   Apps die zijn gesynchroniseerd, worden weergegeven in de Configuration Manager-console en u kunt deze net als andere apps implementeren  

-   Elke 24 uur Configuration Manager licentiegegevens app uit de store downloaden en u kunt dit controleren in de Configuration Manager-console  

 In de 1604 technische voorbeeldversie, kan u apps uit de Windows Store voor bedrijven weergeven in de Configuration Manager-console en gesynchroniseerd. We hebben de mogelijkheid om te maken en implementeren van Configuration Manager-toepassingen uit de gesynchroniseerde store-apps toegevoegd in deze release.  

### <a name="set-up-windows-store-for-business-synchronization"></a>Windows Store voor het synchroniseren van zakelijke instellen  

1.  Registreren bij Azure Active Directory, Configuration Manager als een "Web Application en/of Web API" management-hulpprogramma. Hiermee krijgt u een client-ID die u later nodig hebt.  

    1.  In het knooppunt Active Directory van [https://manage.windowsazure.com](https://manage.windowsazure.com), selecteer uw Azure Active Directory en klik vervolgens op **toepassingen** > **toevoegen**.  

    2.  Klik op **toevoegen van een toepassing die het ontwikkelen van mijn organisatie**.  

    3.  Voer een naam voor de toepassing, selecteer **webtoepassing** en/of **Web API**, klikt u vervolgens de **volgende** pijl.  

    4.  Geef dezelfde URL voor zowel de **aanmelding URL** en **App-ID-URI**. De URL kan en hoeft niet te herleiden tot een echte adres. Bijvoorbeeld, kunt u **https://&lt;uwdomein > / sccm**.  

    5.  Voltooi de wizard.  

2.  In Azure Active Directory, een client-sleutel voor het geregistreerde beheerprogramma te maken.  

    1.  Markeer de toepassing die u zojuist hebt gemaakt en klik op **configureren**.  

    2.  Onder **sleutels**, selecteer een duur in de lijst en klikt u op **opslaan**. Hiermee wordt een nieuwe sleutel van de client gemaakt. Geen verlaat deze pagina totdat u is vrijgegeven Windows Store voor bedrijven aan Configuration Manager hebt.  

3.  In de Windows Store voor bedrijven, configureert u Configuration Manager als het beheerprogramma store.  

    1.  Open [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/managementtools) en aanmelden als u wordt gevraagd.  

    2.  Accepteer de gebruiksvoorwaarden indien nodig.  

    3.  Onder **beheerhulpprogramma's**, klikt u op **toevoegen van een beheerprogramma**.  

    4.  In **zoekt u het hulpprogramma met de naam**, typ de naam van de toepassing die u eerder hebt in AAD gemaakt en klik vervolgens op **toevoegen**.  

    5.  Klik op **activeren** naast de toepassing die u zojuist hebt geïmporteerd.  

    6.  In de **Show Offline-Licensed Apps** wizard, klikt u op **Ja** als u toestaan dat offline gelicentieerde-toepassingen wilt te kopen.  

4.  Koop ten minste één vanuit de Windows Store voor bedrijven.  

5.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, klikt u vervolgens **Windows Store voor bedrijven.**  

6.  Op de **Start** tabblad, in de **maken** groep, klikt u op **toevoegen Windows Store voor bedrijven-Account**.  

7.  Uw tenant-ID, de client-id en de client sleutel toevoegen van Azure Active Directory en voltooi de wizard.  

8.  Nadat u klaar bent, ziet u het account dat u hebt geconfigureerd in de **Windows Store voor zakelijke Accounts** lijst in de Configuration Manager-console.  

### <a name="try-it-out"></a>Probeer het nu!  
 Voltooi de volgende en vervolgens laat het ons weten hoe het werkt met behulp van onze feedbackformulier op de [Configuration Manager feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

 Maken en implementeren van een Configuration Manager-toepassing in een Windows Store voor zakelijke offline gelicentieerde app.  

1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentie-informatie voor de Store-Apps**.  

2.  Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.  

 Een Configuration Manager-toepassing wordt gemaakt met de Windows Store voor Business-app. U kunt vervolgens implementeren en controleren van deze toepassing als u een andere Configuration Manager-toepassing.  

> [!IMPORTANT]  
>  Wanneer u een Configuration Manager-toepassing met één implementatietype van een offline gelicentieerde app maakt, kan dit worden geïmplementeerd op apparaten met MDM beheerde en tevens worden beheerd met de Configuration Manager-client. Als u een app met meerdere implementatietypen implementeren probeert, mislukt de installatie.  
>   
>  U kunt geen momenteel online gelicentieerde apps met Configuration Manager implementeren.  

##  <a name="BKMK_VPP2"></a>Algemene verbeteringen voor volume aangeschaft apps  

-   In deze release, volume aangeschaft apps uit de Windows Store voor bedrijven en de iOS-app store zijn samengevoegd in dezelfde weergave **licentie-informatie voor Apps opslaan**.  

-   Voor iOS-apps volume aangeschaft, het tabblad Apple Volume Purchase Program is verwijderd uit de **App-pakket voor iOS-Browser** in het dialoogvenster in de wizard toepassing maken. Gebruik deze stappen voor het maken van een volume aangeschaft-app voor iOS:  

    1.  1.  In de **softwarebibliotheek** werkruimte van de Configuration Manager-console, vouw **Toepassingsbeheer**, klikt u vervolgens op **licentie-informatie voor de Store-Apps**.  

    2.  2.  Kies de app die u implementeren wilt, klik op de **Start** tabblad, in de **maken** groep, klikt u op **toepassing maken**.  

-   De locatie voor het ophalen en upload een Apple VPP-token voor volume aangeschaft apps in de Configuration Manager-console is gewijzigd. U kunt dit nu doen de **Admin** werkruimte onder de **Cloudservices** > **Apple Volume aankoop programma Tokens** knooppunt.  

##  <a name="BKMK_VPP"></a>Ondernemingsgegevensbescherming (EDP)  
 U kunt configuratie-items die u bij de implementatie van uw enterprise data protection (EDP)-beleid, inclusief zodat u uw beveiligde apps en het niveau van uw EDP-beveiliging en zoeken naar enterprise gegevens op het netwerk kiest, kunnen maken. Zie de volgende onderwerpen voor meer informatie over EDP:  

-   [Uw Ondernemingsgegevens beveiligen via ondernemingsgegevensbescherming (EDP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)  

-   [Maken en implementeren van een onderneming gegevens (EDP) beveiligingsbeleid met behulp van System Center Configuration Manager](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-sccm)  

##  <a name="BKMK_End"></a>Eindgebruikers kunnen apps installeren vanuit de bedrijfsportal.  
 Lokale MDM werd geïntroduceerd in de System Center Configuration Manager versie 1511. In eerdere versies u kan geen toepassingen implementeren op MDM beheerde Windows-10-apparaten met een implementatiedoel van **vereist** voor lokale MDM-beheerde apparaten installeren.  

 In deze versie kunt u nu apps met een implementatiedoel implementeren **beschikbaar** gebruikers van lokale MDM beheerde Windows-10-computers en gebruikers kunnen deze apps zelf nu installeren via de bedrijfsportal.
In dit voorbeeld technische als de bedrijfsportal geopend voor meer dan 15 minuten is, ziet de gebruiker een foutbericht weergegeven. U kunt het probleem omzeilen, start opnieuw op de bedrijfsportal.  

### <a name="before-you-start"></a>Voordat u begint  

#### <a name="server-prerequisites"></a>Server-vereisten  

-   .NET 4.5 of hoger (opnieuw opstarten vereist)  

-   PowerShell 3.0 voor configuratiescript (opnieuw opstarten vereist)  

#### <a name="client-prerequisites"></a>Clientonderdelen  

-   Windows 10 Desktop 1511 (OS build 10586.218) of hoger  

#### <a name="general-prerequisites"></a>Algemene vereisten  

-   Zorg ervoor dat u hebt voltooid de [voorbereiding stappen voor het beheer van mobiele apparaten On-premises](https://technet.microsoft.com/library/mt613153.aspx) en [uw apparaten geregistreerd](https://technet.microsoft.com/library/mt627870.aspx).  

-   Installeren voor de beste toepassing ervaring wanneer de bedrijfsportal gebruiken, controleert u of Configuration Manager beschikt over een actieve verbinding met Microsoft Intune.  

-   Als u de optie bulkinschrijving, configureert u gebruikersapparaataffiniteit voor het geregistreerde apparaat voordat u dit scenario.  

### <a name="configuration-steps"></a>Configuratiestappen  

#### <a name="install-the-application-catalog-roles-and-enable-mobile-device-management-support"></a>Installeren van de Application Catalog-functies en ondersteuning van beheer van mobiele apparaten inschakelen  

1.  De Application Catalog-webservice en website rollen toevoegen  

    1.  Selecteer **HTTPS modus** en de **toestaan mobiele apparaten te gebruiken van dit punt Application Catalog-webservice** optie.  

    2.  In dit voorbeeld technische beperkingen:  

        -   U moet eventuele bestaande Application Catalog-rollen verwijderen voordat u selecteert de optie om mobiele apparaten verbinding moeten maken.  

        -   Zorg ervoor dat er slechts één set met Application Catalog-rollen en de rollen op hetzelfde sitesysteem met het inschrijvingspunt en Inschrijvingsproxypunt punt rollen zijn geplaatst.  

2.  Controleer of de volgende onderdelen zijn operationele vanuit het knooppunt Onderdeelstatus in de Configuration Manager-console:  

    -   **SMS_AWEBSVC_CONTROL_MANAGER**  

    -   **SMS_DMAPPSVC_CONTROL_MANAGER**  

    -   **SMS_DMCONTENTSVC_CONTROL_MANAGER**  

    -   **SMS_PORTALWEB_CONTROL_MANAGER**  

### <a name="configure-boundaries"></a>Grenzen configureren  
 Vereiste grenzen voor intranet alleen-lezen distributiepunten configureren.  

> [!NOTE]  
>  Alleen IPv4-bereik grenzen worden ondersteund op dit moment voor beheer van mobiele apparaten.  

### <a name="deploy-the-company-portal-application-and-configuration"></a>Implementeer de toepassing bedrijfsportal en de configuratie  

1.  Het configuratiescript opgenomen met de technische preview gebruiken om voor te bereiden van de bedrijfsportal-implementatie en configuratie:  

    1.  Open een verhoogde PowerShell-opdrachtvenster.  

    2.  Voer **RemoteSigned instellen-uitvoeringsbeleid**  

    3.  Uit de map  **&lt;SCCM-installatiemap\>\cd.latest\SMSSETUP\TOOLS\MDM** uitvoeren **.\ConfigurationScript.ps1**  

     Het configuratiescript doet het volgende:  

    1.  Een Configuration Manager-toepassing maakt met een Windows app pakket implementatie type met **CompanyPortalOnPremisesMDM.appx** in dezelfde map.  

    2.  Hiermee maakt u een configuratie-item en een configuratiebasislijn die configureert u de bedrijfsportal.  

    3.  De configuratiebasislijn en de toepassing wordt geïmplementeerd en wordt de toepassing naar alle distributiepunten toegevoegd.  

    > [!NOTE]  
    >  Als de Application Catalog-rollen niet dezelfde plaats bevinden als de primaire site, moet u de volgende acties uitvoeren:  
    >   
    >  -   In de **activa en naleving** werkruimte, zoek de **OnPremMDM Portal Configuration CI - URL's voor server** configuratie-item  
    > -   Wijzig de **Compliantieregels** waarde aan de FQDN-naam van het sitesysteem waar de Application Catalog-rollen zich bevinden.  

2.  Als de toepassing bedrijfsportal en de configuratie van beide zijn geïmplementeerd, Controleer of de toepassing en de configuratie basislijn zijn voldoet aan de opgegeven apparaten met **implementaties** sectie van de Configuration Manager-console. De bedrijfsportal wordt weergegeven als **bedrijfsportal (technische Preview)** in het menu Start op het apparaat.  

### <a name="try-it-out"></a>Probeer het nu!  
 De volgende taken uitvoeren en vervolgens laat het ons weten hoe het werkt met behulp van onze feedbackformulier op de [Configuration Manager feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

1.  Implementeren van meerdere toepassingen met ondersteunde implementatietypen aan de Gebruikersverzameling van een met een implementatiedoel van **beschikbaar**. Voor deze technical preview toepassingen die van de beheerder goedkeuring vereisen worden niet ondersteund en worden niet weergegeven in de bedrijfsportal.  

2.  Gebruikers kunnen vervolgens zoeken en installeren van apps via de bedrijfsportal.  

     Nadat u de bedrijfsportal opent, ziet u een dialoogvenster voor verificatie met de naam **System Center Configuration Manager** Active Directory-referenties van de gebruiker opgeven (in de vorm van user@domain of domein\gebruiker) om aan te melden.  

##  <a name="BKMK_SW1"></a>Nieuwe tabbladen voor Updates en besturingssystemen in Software Center  
 In deze release zijn de volgende wijzigingen aangebracht voor het verbeteren van de lay-out van de toepassing van Software Center:  

-   De **toepassingen** tabblad is gesplitst in drie verschillende tabbladen voor **Updates**, **besturingssystemen** (dit zijn beide eerder gevonden in de **Filters** lijst), en **toepassingen**.  

##  <a name="BKMK_ServerGroups"></a>Een groep van server-service  
 Technische Preview van System Center Configuration Manager, versie 1511, opgenomen de mogelijkheid om een verzameling waarin alle apparaten in de verzameling gezamenlijk een servergroep te maken. Vervolgens, kan de groepsinstellingen server moet worden gebruikt wanneer u software-updates implementeren op de server-groep besturingselement welk percentage van computers die zijn bijgewerkt op elk moment configureren en configureert u voorafgaand aan de implementatie en post-implementatie PowerShell-scripts om aangepaste acties worden uitgevoerd.  

 Technische Preview van System Center Configuration Manager, versie 1605, voegt de mogelijkheid om bij te werken van de computers in de servergroep in een opgegeven volgorde definiëren, voegt uitgebreide controle om de status bekijken voor de computers in de servergroep en biedt de mogelijkheid om te wissen van de implementatie-vergrendelingen die nuttig zijn wanneer clients installatie van de software-updates is mislukt en voorkomen dat andere clients hun software-updates installeren.  

### <a name="try-it-out"></a>Probeer het nu!  
 De volgende taken uitvoeren en vervolgens laat het ons weten hoe het werkt met behulp van onze feedbackformulier op de [Configuration Manager feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

-   Ik kan een verzameling maken die een servergroep vertegenwoordigt. Deze test kunt u uw verzamelen lidmaatschapsregels om 2 machines in deze verzameling.   

-   Ik kan opgeven dat de computers in de servergroep software-updates in een bepaalde volgorde op basis van de server-instellingen voor de verzameling installeren. Gebruik de voorbeeldscripts in de procedure om op te geven van de scripts die vóór de implementatie en post-implementatie.  

-   Ik kan een software-update implementeert aan deze verzameling. Controleer de bestanden start.txt en end.txt (gemaakt op basis van de voorbeeldscripts) in C:\temp en controleer of de begin- en eindtijden voor de implementatie op de computers in de servergroep. Raadpleeg het bestand UpdatesDeployment.log voor meer informatie.  

#### <a name="to-create-a-collection-for-a-server-group"></a>Een verzameling voor een servergroep maken  

1.  [Maak een apparaatverzameling](https://technet.microsoft.com/library/gg712295.aspx) die de computers in de servergroep bevat.  

2.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**met de rechtermuisknop op de verzameling die de computers in de servergroep bevat en klik vervolgens op **eigenschappen**.  

3.  Op de **algemeen** tabblad **alle apparaten deel uitmaken van dezelfde servergroep**, en klik vervolgens op **instellingen**.  

4.  Op de **instellingen** pagina, geeft u een van de volgende instellingen:  

    -   **Toestaan dat een percentage van virtuele machines tegelijk worden bijgewerkt**: Hiermee geeft u op dat alleen een bepaald percentage van clients op elk gewenst moment worden bijgewerkt. Als bijvoorbeeld de verzameling 10 clients is en de verzameling is geconfigureerd voor het bijwerken van 30% van clients op hetzelfde moment wordt slechts 3 clients software-updates op een bepaald moment installeren.  

    -   **Toestaan dat een aantal machines tegelijk worden bijgewerkt**: Hiermee geeft u op dat alleen een bepaald aantal clients op elk gewenst moment worden bijgewerkt.  

    -   **Geef de volgorde onderhoud**: Hiermee geeft u de clients in de verzameling worden bijgewerkte één voor één opnieuw in de volgorde die u configureert. Een client installeert software-updates alleen nadat de installatie van de software-updates van de client wordt dan deze in de lijst is voltooid.  

5.  Geef op of een script vóór implementatie (knooppunt verwerkingsstop) of na de implementatie (knooppunt hervatten) script gebruiken.  

    > [!TIP]  
    >  Hier volgen voorbeelden dat u gebruiken kunt voor voorafgaand aan de implementatie testen en na de implementatie scripts die de huidige tijd naar een tekstbestand schrijven:  
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
    >  **Post-implementatie**  
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

2.  [De implementatie van software-update controleren](https://technet.microsoft.com/library/gg712304.aspx). Naast de standaard controleweergaven voor implementatie van software-updates, wordt een nieuwe beschrijving van de status weergegeven wanneer een client wacht op zijn beurt de softwareupdates te installeren. **Wachten op vergrendeling** voor deze nieuwe status wordt weergegeven.  

#### <a name="to-clear-the-deployment-locks-for-computers-in-a-server-group"></a>Wissen van de implementatie wordt vergrendeld voor computers in een servergroep  

1.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**, en klik op de verzameling Schakel implementatie vergrendeld.  

2.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **wissen Server groep implementatie vergrendeld**. Wanneer clients installatie van de software-updates is mislukt en voorkomen dat andere clients hun software-updates installeren, kunnen de implementatie-vergrendelingen handmatig worden gewist.  

##  <a name="BKMK_ATP"></a>Ondersteuning voor Windows Defender geavanceerde bedreiging Protection-service  
 Windows Defender geavanceerde bedreiging beveiliging (vrije) is een nieuwe service waarmee ondernemingen om te detecteren, te onderzoeken en reageren op geavanceerde aanvallen op hun netwerken. Meer informatie over [Windows Defender vrije](https://blogs.windows.com/windowsexperience/2016/03/01/announcing-windows-defender-advanced-threat-protection). Configuration Manager kan u helpen bij het voorbereiden en beheerde Windows 10 Verjaardag Edition clientapparaten bewaken.  

### <a name="try-it-now"></a>Probeer het nu!  
 De volgende taken uitvoeren en vervolgens laat het ons weten hoe het werkt met behulp van onze feedbackformulier op de [Configuration Manager feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

-   Onboarding van apparaten tot de onlineservice Windows Defender geavanceerde bedreiging beveiliging (vrije)  

-   Controleer de implementatie van Windows Defender vrije voor beheerde apparaten  

 **Vereisten**  

-   Abonnement op de onlineservice Windows Defender geavanceerde bedreiging Protection  

-   Clients met Windows 10, Verjaardag Edition (build 14328 en hoger)  

-   Maken van een client-voorbereiding-configuratiebestand  

    ##### <a name="how-to-create-an-onboarding-configuration-file"></a>Het maken van een configuratiebestand voorbereiden  

    1.  Aanmelding bij de onlineservice Windows Defender vrije  

    2.  Klik op de **Client op tussen twee locaties** menu-item  

    3.  Selecteer **System Center Configuration Manager** en klikt u op **downloadpakket**.  

    4.  Download het bestand gecomprimeerd archief (.zip) en de inhoud te extraheren.  


##### <a name="onboard-devices-for-windows-defender-atp"></a>Onboarding van apparaten voor Windows Defender vrije  

1.  Navigeer in de Configuration Manager-console **activa en naleving** > **overzicht** > **Endpoint Protection** > **beleidsregels voor Windows Defender vrije** en klikt u op **Windows Defender vrije beleid maken**. De Wizard beleid voor Windows Defender vrije wordt geopend.  

2.  Type de **naam** en **beschrijving** voor het beleid voor Windows Defender vrije en selecteer **Onboarding**. Klik op Volgende.  

3.  **Bladeren** voor het configuratiebestand geleverd door uw organisatie Windows Defender vrije cloud service-tenant. Klik op **Volgende**.  

4.  Geef de voorbeeldbestanden die worden verzameld en gedeeld worden door beheerde apparaten voor analyse.  

    -   **Geen** – geen voorbeeldbestanden worden verzameld voor analyse  

    -   **Portable uitvoerbare bestanden** : bestanden zoals programmabestanden (.exe), dynamic bibliotheek (.dll)-koppelingsbestanden, lettertypebestanden en vergelijkbare bestanden dat kunnen worden misbruikt in cyberattacks worden verzameld en gedeeld voor analyse  

     Klik op **Volgende**.  

5.  Bekijk het overzicht en voltooi de wizard.  

6.  U kunt nu het beleid voor Windows Defender vrije implementeren voor beheerde clientcomputers door te klikken op **implementeren**.  

##### <a name="monitor-windows-defender-atp"></a>Monitor voor Windows Defender vrije  

1.  Navigeer in de Configuration Manager-console **bewaking** > **overzicht** > **beveiliging** en klik vervolgens op **Windows Defender vrije**.  

2.  Controleer het Windows Defender geavanceerde bedreiging Protection-dashboard.  

    -   **Windows Defender Agent Implementatiestatus** : het aantal en de hoeveelheid in aanmerking komende beheerde client-computers met actieve Windows Defender vrije beleid vrijgegeven  

    -   **Status van Windows Defender vrije Agent** – Percentage computerclients rapportage over de status voor hun Windows Defender vrije-agent  

        -   **Goede** -goed werkt  

        -   **Inactieve** -er zijn geen gegevens naar service worden verzonden tijdens periode  

        -   **De status van agent** -de service voor de agent in Windows wordt niet uitgevoerd  

        -   **Er zijn geen vrijgegeven** - beleid is toegepast, maar de agent niet vrijgeven beleid gemeld  

##  <a name="BKMK_DHA"></a>On-premises apparaat Health Attestation-bewerking  
 Health-verklaring voor Windows 10-apparaten kan nu worden geconfigureerd om te communiceren met de on-premises infrastructuur. Beheerders kunnen opgeven of reporting vindt plaats via de cloud of on-premises resources. Lokale voor health attestation reporting is geselecteerd, kan een URL worden opgegeven voor de service. Hierdoor kunnen client-pc's zonder internettoegang inschakelen en apparaten beheren met behulp van status Attestation-bewerking.  

### <a name="enable-health-attestation-for-on-premises-devices"></a>Health-verklaring voor lokale apparaten inschakelen  
 In 1605, hebben we enkele fouten gedetecteerd in 1604 Technical Preview opgelost.  Om te proberen het uit, lokale Attestation statusservice agent-instellingen te configureren.  

1.  Navigeer in de Configuration Manager-console **beheer** > **overzicht** > **clientinstellingen**, en vervolgens stelt u **Gebruik lokale statusservice Attestation** naar **Ja**.  

2.  Geef de **URL op voor de on-premises statusverklaringsservice**en klik op **OK**.  

##  <a name="BKMK_RestartOptions"></a>Nieuwe opties voor Windows 10 clients opnieuw te starten na installatie van software-update  
 Wanneer een software-update die is vereist opnieuw opstarten wordt geïmplementeerd met behulp van Configuration Manager en geïnstalleerd op een computer opnieuw is gepland en een dialoogvenster voor opnieuw opstarten wordt weergegeven. Op dit moment voor Windows 8 en hoger dan als u afgesloten of opnieuw opstarten van de computer met de Windows-energiebeheer (in plaats van in het dialoogvenster opnieuw starten), blijft van het dialoogvenster opnieuw opstarten nadat de computer opnieuw wordt opgestart en de computer moet opnieuw starten op de geconfigureerde deadline. In deze technische preview, de optie voor het **bijwerken en opnieuw starten** en **Update en afsluiten** beschikbaar zullen zijn op Windows-10-computers in de Windows-energiebeheer wanneer er een te worden opgestart voor een software-update van Configuration Manager. Nadat u een van deze opties hebt gebruikt, wordt het dialoogvenster voor opnieuw opstarten niet weergegeven nadat de computer opnieuw wordt opgestart.  

##  <a name="BKMK_IMEI"></a>Vooraf declareren apparaten in Bedrijfseigendom met IMEI-nummer of iOS-serienummer  
 U kunt nu apparaten in Bedrijfseigendom identificeren door het importeren van hun internationale station mobile equipment identity (IMEI) getallen. U kunt een apparaat IMEI getallen met door komma's gescheiden waarden (.csv)-bestand uploaden of u kunt de apparaatgegevens handmatig invoeren.  U kunt ook importeren serienummers voor iOS-apparaten.  Geïmporteerde gegevens wordt eigendom van de apparaten die worden ingeschreven als "Bedrijf" ingesteld.  Een licentie voor Intune is nog steeds vereist is voor elke gebruiker die toegang de service.  

### <a name="try-it-out"></a>Probeer het nu!  
 De volgende taken uitvoeren en vervolgens laat het ons weten hoe het werkt met behulp van onze feedbackformulier op de [Configuration Manager feedbackprogramma](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) pagina op de Microsoft Connect-site:  

-   Een aantal IMEI getallen in een CSV-bestand importeren. Elke rij kan de IMEI-nummer gevolgd door een veld gegevens bevatten.  

-   IMEI-nummers handmatig importeren vanuit de Configuration Manager-console.  

-   Een set van iOS-serienummers in een CSV-bestand importeren. Nogmaals, bevat elke rij een getal gevolgd door de details voor het apparaat.  

##### <a name="pre-declare-corporate-owned-devices-with-imei-or-ios-serial-number"></a>Vooraf declareren van apparaten in bedrijfseigendom met IMEI-nummer of iOS-serienummer  

1.  Ga in de Configuration Manager-console **activa en naleving** > **overzicht** > **alle apparaten in Bedrijfseigendom** > **Pre-declared apparaten**, en klik vervolgens op **Pre-declared apparaten maken**. De wizard Pre-declared apparaten wordt geopend.  

2.  Geef op hoe u wilt toevoegen, apparaatgegevens:  

    -   **Een CSV-bestand met IMEI-nummers en details uploaden** : als u wilt uploaden van een lijst met getallen, Zie stap 3.  

    -   **IMEI-nummers en gegevens handmatig toevoegen** : als u wilt gegevens handmatig invoeren, typt u de IMEI-nummer of de iOS-serienummer en de details voor de apparaten en gaat u verder met stap 4.  

3.  Blader naar het CSV-bestand met de gegevens voor het vooraf declareren apparaten in Bedrijfseigendom voor geüploade bestanden. Het bestand moet de volgende indeling, met uitzondering van de eerste rij (alleen richtlijnen ter) hebben:  

    |**IMEI-NUMMER #**|**iOS-serienummer**|**BESTURINGSSYSTEEM**|**Details**|
    |---|---|---|---|
    |123456789012345||WINDOWS|Eigendom van het bedrijf van de Windows-apparaat|
    |123456789012|A0BCD0EFGH0J|IOS|Eigendom van het bedrijf iOS-apparaten|
    |123456789012346||ANDROID|Eigendom van het bedrijf Android-apparaat|

     **Kolommen:**  

    -   Kolom 1: IMEI-nummer – ofwel een IMEI getal of een iOS-serienummer is vereist voor elke rij  

    -   Kolom 2: iOS-serienummer – alleen serienummers van iOS kunnen worden vooraf gedeclareerde. IMEI-nummer voor andere apparaatplatforms gebruiken  

    -   Kolom 3: Besturingssysteem van het apparaat (hoofdlettergebruik vereist):  

        -   IOS: alle apparaten met iOS  

        -   WINDOWS – omvat Windows Phone, Windows 10 Mobile en Windows-pc 's  

        -   ANDROID: alle Android-apparaten  

    -   Kolom 4: Details – extra apparaatgegevens die wordt weergegeven in de Configuration Manager-console  

     Klik op **Volgende**.  

4.  Bekijk de resultaten van het bestand importeren. Eerder heeft geïmporteerd IMEI-nummer of serienummers hun informatie bijgewerkt met nieuwe informatie.  Klik op **volgende** om door te gaan of **terug** bijgewerkte gegevens behouden en voltooi de wizard.  

