---
title: Windows-clients implementeren | Microsoft-documenten
description: Informatie over het implementeren van clients op Windows-computers in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 341f0d0b-f907-44cf-9e10-e1b41fc15f82
caps.latest.revision: 13
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 83878b71b876c725920b228190000fc849a063db
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-clients-to-windows-computers-in-system-center-configuration-manager"></a>Clients implementeren op Windows-computers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u Configuration Manager-clients installeert, zorg ervoor dat alle de [vereisten](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) zijn aanwezig en dat u alle vereiste implementatieconfiguraties hebt voltooid.   

##  <a name="BKMK_ClientPush"></a>Het installeren van clients met client-push  

U kunt push-clientinstallatie voor een site configureren, en clientinstallatie zal automatisch worden uitgevoerd op de computers die zijn gedetecteerd binnen de geconfigureerde grenzen van de site wanneer deze grenzen als een grensgroep zijn geconfigureerd. Of u kunt een push-clientinstallatie starten door de Push-clientinstallatiewizard uit te voeren voor een specifieke verzameling of bron binnen een verzameling.  

U kunt ook de Wizard Push-clientinstallatie gebruiken voor het installeren van de Configuration Manager-client [query](../../../core/servers/manage/queries-technical-reference.md) resultaten. Voor de installatie te voltooien, moet een van de items die door de query het kenmerk **ResourceID** van de klasse **systeembron**.   

Als de siteserver kan geen contact op met de clientcomputer of het installatieproces start, wordt de herhaalt installatiepoging automatisch opnieuw elk uur gedurende 7 dagen.  

Om het installatieproces van de client te helpen opvolgen, installeert u een terugvalstatuspuntsitesysteem voordat u de clients installeert. Wanneer er een terugvalstatuspunt is geïnstalleerd, wordt het automatisch toegewezen aan clients wanneer ze door de push-clientinstallatiemethode zijn geïnstalleerd. Bekijk de clientimplementatie en toewijzingsrapporten om de vooruitgang van de clientinstallatie te volgen. 

Logboekbestanden van client bieden dat meer gedetailleerde informatie voor probleemoplossing en vereisen geen een terugvalstatuspunt. Het CCM.log-bestand op de siteserver registreert bijvoorbeeld problemen die de siteserver heeft tijdens het maken van een verbinding met de computer, en het CCMSetup.log-bestand op de client registreert het installatieproces.  

> [!IMPORTANT]  
>  Opdat client-push zou lukken, dient u ervoor te zorgen dat alle vereiste onderdelen zijn geïnstalleerd. Deze zijn opgenomen in de sectie 'Afhankelijkheden bij installatiemethoden' in [vereisten voor de implementatie van clients op Windows-computers in System Center Configuration Manager](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md).  

### <a name="to-configure-the-site-to-automatically-use-client-push-for-discovered-computers"></a>De site configureren om client-push automatisch te gebruiken voor gedetecteerde computers.

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de site waarvoor u wenst te configureren van automatische site-brede clientpushinstallatie.  

4.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **clientinstallatie-instellingen** > **Push-clientinstallatie**.  

5.  Op de **algemeen** tabblad van het **Clientpushinstallatie-eigenschappen** dialoogvenster, selecteer **Schakel automatische site-brede clientpushinstallatie**. Selecteer de systeemtypes waarop de Configuration Manager de clientsoftware moet pushen.  

6.  Selecteer of u wilt dat de client te installeren op domeincontrollers.  

7.  Op de **Accounts** tabblad, geeft u een of meer accounts voor Configuration Manager bij het verbinden met de computer gebruiken om de clientsoftware te installeren. Klik op de **maken** pictogram en voer de **gebruikersnaam** en **wachtwoord** (niet meer dan 38 tekens), bevestig het wachtwoord en klik vervolgens op **OK**. U moet ten minste één push-clientinstallatieaccount opgeven. Dit account moet lokale beheerdersrechten hebben op elke computer waarop u de client wilt installeren. Als u een push-clientinstallatieaccount niet opgeeft, wordt Configuration Manager probeert de site system computeraccount, waardoor tussen domeinen clientpush te gebruiken.  

    
    > [!NOTE]  
    >  Als u de push-clientinstallatiemethode van een secundaire site wilt gebruiken, moet de account gespecificeerd worden op de secundaire site die de client-push start.  
    >   
    >  Zie de volgende procedure "de Push-Clientinstallatiewizard gebruiken" voor meer informatie over de push-clientinstallatieaccount.  

8.  Voltooi de **installatie-eigenschappen** tabblad.

     [Eigenschappen van clientinstallatie](../../../core/clients/deploy/about-client-installation-properties.md) die zijn opgegeven op dit tabblad worden gepubliceerd naar Active Directory Domain Services als het schema wordt uitgebreid voor Configuration Manager en gelezen door clientinstallaties waar CCMSetup uitgevoerd wordt zonder installatie-eigenschappen.  

    > [!NOTE]  
    >  Als u push-clientinstallatie op een secundaire site inschakelt, zorg ervoor dat de SMSSITECODE-eigenschap is ingesteld op de naam van de Configuration Manager-site van de bovenliggende primaire site. Als het Active Directory-schema wordt uitgebreid voor Configuration Manager, kunt u dit ook instellen op AUTO om automatisch te vinden de juiste sitetoewijzing.  

### <a name="to-use-the-client-push-installation-wizard"></a>De Wizard Push-clientinstallatie gebruiken

1.  Kies in de Configuration Manager-console **beheer** >  **siteconfiguratie** > **Sites**.  

3.  Selecteer de site waarvoor u wenst te configureren van automatische site-brede clientpushinstallatie.  

4.  Op de **Start** tabblad > **instellingen** groep, kiest u **clientinstallatie-instellingen** > **Push-clientinstallatie**.  

5.  Voltooi de **installatie-eigenschappen** tabblad.  

     [Eigenschappen van clientinstallatie](../../../core/clients/deploy/about-client-installation-properties.md) die zijn opgegeven op dit tabblad worden gepubliceerd naar Active Directory Domain Services als het schema wordt uitgebreid voor Configuration Manager en gelezen door clientinstallaties waar CCMSetup uitgevoerd wordt zonder installatie-eigenschappen.  

6.  Kies in de Configuration Manager-console **activa en naleving**.  

7.  Selecteer in de werkruimte **Activa en naleving** een of meerdere computers, of een verzameling van computers.  

8.  Kies een van de volgende acties op het tabblad **Start**:  

    -   Als u wilt dat de client te installeren op één computer of meerdere computers in de **apparaat** groep, kiest u **Client installeren**.  

    -   Als u wilt dat de client te installeren op een verzameling van computers in de **verzameling** groep, kiest u **Client installeren**.  

9. Op de **voordat u begint** pagina van de **Clientwizard installeren**, lees de informatie in en kies vervolgens **volgende**.  

10. Voltooi de **installatieopties** pagina.  

11. Controleer de installatie-instellingen en sluit vervolgens de wizard.  

> [!NOTE]  
>  U kunt de wizard gebruiken om clients te installeren zelfs als de site niet is geconfigureerd voor client-push.  

##  <a name="BKMK_ClientSUP"></a>Clients installeren met software-update-gebaseerde installatie  
 Software-update gebaseerde clientinstallatie publiceert de client naar een software-updatepunt als een software-update. Gebruik deze methode voor een nieuwe installatie of upgrade.  

 Als een computer de client is geïnstalleerd heeft, geeft Configuration Manager de client met het clientbeleid, met inbegrip van software-update servernaam en poort van waaruit softwareupdates worden verkregen.   

> [!IMPORTANT]  
>  Om installatie op basis van software-updates te gebruiken, moet u dezelfde Windows Server Update Services (WSUS)-server gebruiken voor clientinstallatie en software-updates. Deze server moet het actieve software-updatepunt in een primaire site zijn. Zie voor meer informatie [installeert een software-updatepunt](../../../sum/get-started/install-a-software-update-point.md).  

Als een computer niet de Configuration Manager-client is geïnstalleerd heeft, moet u configureren en toewijzen van een GPO Group Policy Object () in Active Directory Domain Services om op te geven van de servernaam van software-update.  

U kunt geen opdrachtregeleigenschappen toevoegen aan een clientinstallatie op basis van software-updates. Als u hebt het Active Directory-schema voor Configuration Manager uitgebreid, vragen clientcomputers automatisch Active Directory Domain Services naar installatie-eigenschappen wanneer ze installeren.  

Als u de Active Directory-planning niet hebt uitgebreid, kunt u Groepsbeleid gebruiken om clientinstallatie-instellingen te geven aan computers in uw site. Deze instellingen worden automatisch toegepast op installaties op basis van software-updates. Voor meer informatie, zie [Eigenschappen van clientinstallatie inrichten (groepsbeleid en clientinstallatie op basis van software-update)](#BKMK_Provision) en[ Clients toewijzen aan een site in System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

Gebruik de volgende procedures voor het configureren van computers zonder een Configuration Manager-client de softwareupdate te gebruiken voor clientinstallatie en software-updates en publiceren van de client software op het software-updatepunt.  

> [!NOTE]  
>  Als een herstart voor een computer in behandeling is na een eerdere software-installatie, wordt de computer mogelijk opnieuw opgestart door een op een software-update gebaseerde clientinstallatie.  

### <a name="configure-a-group-policy-object-in-active-directory-domain-services-to-specify-the-software-update-point-for-client-installation-and-software-updates"></a>Een groepsbeleidobject in Active Directory Domain Services om op te geven van de software-updatepunt voor client-installatie- en software-updates configureren:  

1.  Gebruik de Console Groepsbeleidsbeheer om een nieuw of bestaand Groepsbeleidobject te openen.  

2.  Vouw in de console **Computerconfiguratie**, vouw **Beheersjablonen**, vouw **Windows-onderdelen**, en kies vervolgens **Windows Update**.  

3.  Open de eigenschappen van de instelling **Microsoft updateservicelocatie in intranet opgeven**, en kies vervolgens **ingeschakeld**.  

4.  In het vak **stellen de updateservice in intranet voor het detecteren van updates**, geef de naam en poort van de software-updatepuntserver:  

    -   Als het Configuration Manager-sitesysteem is geconfigureerd voor een volledig gekwalificeerde domeinnaam (FQDN) gebruiken, gebruikt u de FQDN-indeling.  

    -   Als het Configuration Manager-sitesysteem niet is geconfigureerd voor het gebruik van een FQDN-naam, gebruikt u een kort naamformaat.  

    > [!NOTE]  
    >  Om te bepalen het poortnummer, Zie [bepalen van de gebruikte poortinstellingen door WSUS in System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

     Voorbeeld: **http://server1.contoso.com:8530**  

5.  In het vak **intranetserver voor statistische gegevens**, geef de naam van de intranetserver voor statistische gegevens. Heeft niet dezelfde zijn als de software-updatepuntserver en de indeling heeft geen overeenkomen als het dezelfde server.  

6.  De Group Policy Object toewijzen aan de computers waarop u wilt installeren van de client en software-updates wilt ontvangen.  

### <a name="to-publish-the-configuration-manager-client-to-the-software-update-point"></a>De Configuration Manager-client op het software-updatepunt publiceren  

1.  Klik in de Configuration Manager-console op **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de site waarvoor u wilt configureren van software-update gebaseerde clientinstallatie.  

4.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **clientinstallatie-instellingen**, en kies vervolgens **clientinstallatie**.  

5.  Selecteer **schakelen van software-update gebaseerde clientinstallatie**.  

6.  Als de clientsoftware op de siteserver van Configuration Manager een latere versie is dan die van de software-updatepunt, de **latere versie van clientpakket gedetecteerd** dialoogvenster wordt geopend. Klik op **Ja** voor het publiceren van de meest recente versie.  

    > [!NOTE]  
    >  Als de clientsoftware is niet eerder is gepubliceerd op de software-updatepunt, zal dit vak leeg zijn.  

De software-update voor de Configuration Manager-client wordt niet automatisch bijgewerkt wanneer er een nieuwe versie. Bij de upgrade van de site, die een nieuwe clientversie bevat, moet u deze procedure herhalen en op **Ja** klikken voor stap 6.  

##  <a name="BKMK_ClientGP"></a>Het installeren van clients met Groepsbeleid  
 U kunt Groepsbeleid in Active Directory Domain Services publiceren of toewijzen van de Configuration Manager-client installeren op computers in uw onderneming. De client wordt geïnstalleerd wanneer de computer wordt gestart. Wanneer u Groepsbeleid, toont de client in het Configuratiescherm **software** voor de gebruiker te installeren.  

 Het Windows Installer-pakket (CCMSetup.msi) voor installaties op basis van een Groepsbeleid gebruiken. Dit bestand staat in de map  **&lt;Configuration Manager-installatiemap\>\bin\i386** op de siteserver van Configuration Manager. U kunt geen eigenschappen toevoegen aan dit bestand installatiegedrag te wijzigen.  

> [!IMPORTANT]  
>  U moet beheerdersmachtigingen voor toegang tot de clientinstallatiebestanden.  

-   Als het Active Directory-schema voor Configuration Manager is uitgebreid en **deze site publiceren in Active Directory Domain Services** is geselecteerd in de **Geavanceerd** tabblad van het **voor Site-eigenschappen** in het dialoogvenster zoeken clientcomputers automatisch Active Directory Domain Services naar installatie-eigenschappen. Zie [About client installation properties published to Active Directory Domain Services in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md) (Over eigenschappen van clientinstallaties die zijn gepubliceerd naar Active Directory Domain Services in System Center Configuration Manager) voor meer informatie over de installatie-eigenschappen die worden gepubliceerd.  

-   Als het Active Directory-schema niet is uitgebreid, kunt u de procedure in dit onderwerp voor het opslaan van installatie-eigenschappen in het register van computers: [Hoe clientinstallatie-eigenschappen (Groepsbeleid en Software-Update gebaseerde clientinstallatie)](#BKMK_Provision). Deze installatie-eigenschappen wordt gebruikt wanneer de client is geïnstalleerd.  

Voor informatie over hoe Groepsbeleid in Active Directory Domain Services moet worden gebruikt om software te installeren, raadpleegt u uw Windows Server-documentatie.  

##  <a name="BKMK_Manual"></a>Clients handmatig installeren  
 U kunt handmatig de clientsoftware installeren op computers in uw bedrijf met behulp van het programma CCMSetup.exe. Dit programma en de ondersteunende bestanden ervan staan de **Client** map van de Configuration Manager-installatiemap op de siteserver en op beheerpunten in uw site. Deze map wordt op het netwerk gedeeld als  

 \\\\*&lt;Servernaam van site\>*\SMS_*&lt;sitecode\>*\Client\  

 waar  *&lt;Siteservernaam\>*  is de naam van een van de servers die als host fungeert voor een beheerpunt en  *&lt;sitecode\>*  is de code voor de primaire site de client moet behoren.  Als u CCMSetup.exe vanaf de opdrachtregel op de client wilt uitvoeren, moet u een netwerkstation toewijzen aan deze locatie en daarna de opdracht uitvoeren.  

> [!IMPORTANT]  
>  U moet beheerdersmachtigingen voor toegang tot de clientinstallatiebestanden.  

 CCMSetup.exe kopieert alle vereiste onderdelen op de clientcomputer en roept het Windows Installer-pakket (Client.msi) om de client te installeren. Client.msi kan niet rechtstreeks worden uitgevoerd.  

 U kunt opdrachtregeleigenschappen opgeven zowel voor CCMSetup.exe  als voor Client.msi om het gedrag van de clientinstallatie te wijzigen. Zorg ervoor dat u CCMSetup-eigenschappen opgeeft (de eigenschappen die met beginnen  **/** ) voordat u de Client.msi-eigenschappen opgeeft. Bijvoorbeeld:  

```  
CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=AUTO FSP=SMSFP01  
```  
dan wordt de client geïnstalleerd met de volgende eigenschappen:  

|Eigenschap|Beschrijving|  
|--------------|-----------------|  
|**/MP:SMSMP01**|Deze CCMSetup-eigenschap geeft het beheerpunt SMSMP01 op om de vereiste clientinstallatiebestanden te downloaden.|  
|**/logon**|Deze CCMSetup-eigenschap geeft aan dat de installatie moet worden stopgezet als een bestaande Configuration Manager-client op de computer is gevonden.|  
|**SMSSITECODE = AUTO**|Deze Client.msi-eigenschap geeft aan dat de client wordt gezocht naar de Configuration Manager-sitecode te gebruiken, bijvoorbeeld met behulp van Active Directory Domain Services.|  
|**FSP = SMSFP01**|Deze Client.msi-eigenschap geeft op dat het terugvalstatuspunt met naam SMSFP01 wordt gebruikt voor de ontvangst van statusberichten die verzonden worden vanaf de clientcomputer.|  

 Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over alle CCMSetup.exe-eigenschappen.  

### <a name="examples"></a>Voorbeelden
 Deze voorbeelden gelden voor Active Directory-clients op het intranet. Hierbij wordt gebruikgemaakt van de volgende waarden voor verschillende aspecten van de site:  

 **MPSERVER** = server die als host fungeert voor het beheerpunt   
**FSPSERVER** = server die als host fungeert voor het terugvalstatuspunt  
**ABC** = sitecode  
**contoso.com** = domeinnaam  

 Alle sitesysteemservers worden geconfigureerd met een intranet FQDN en de site wordt gepubliceerd naar Active Directory-forest van de client.  

 Op de clientcomputer, moet u zich aanmelden als een lokale beheerder, wijst een station (z:) toe aan\\\MPSERVER\SMS_ABC\Client, de opdrachtprompt overschakelen naar het station z en voer vervolgens een van de volgende opdrachten.  

 **Voorbeeld 1:**  

```  
CCMSetup.exe  
```  
In dit voorbeeld installeert de client zonder aanvullende eigenschappen zodat de client wordt automatisch geconfigureerd met de clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services. Bijvoorbeeld, de client is geconfigureerd voor de sitecode (vereist dat de netwerklocatie van de client moet worden opgenomen in een grensgroep die is geconfigureerd voor clienttoewijzing), een beheerpunt, het terugvalstatuspunt en of de client enkel via HTTPS moet communiceren. Voor meer informatie over de eigenschappen van de clientinstallatie die automatisch kunnen worden geconfigureerd voor Active Directory-clients, zie [Gepubliceerde eigenschappen van clientinstallaties naar Active Directory-domeinservices in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

 **Voorbeeld 2:**  

```  
CCMSetup.exe /MP:mpserver.contoso.com /UsePKICert SMSSITECODE=ABC CCMHOSTNAME=server05.contoso.com CCMFIRSTCERT=1 FSP=server06.constoso.com  
```  
In dit voorbeeld de automatische configuratie overschreven die Active Directory Domain Services kan voorzien en is niet vereist dat de netwerklocatie van de client wordt opgenomen in een grensgroep die is geconfigureerd voor clienttoewijzing. De installatie geeft daarvoor in de plaats op: de site, een intranetbeheerpunt en een internet-gebaseerd beheerpunt, een terugvalstatuspunt dat verbindingen aanvaardt van het internet en om een client PKI-certificaat te gebruiken (indien beschikbaar) met de langste geldigheidsperiode.  

##  <a name="BKMK_ClientLogonScript"></a>Clients met aanmeldingsscripts installeren  
 Configuration Manager ondersteunt aanmeldingsscripts om de Configuration Manager-clientsoftware te installeren. U kunt het programmabestand **CCMSetup.exe** gebruiken in een aanmeldingsscript om de clientinstallatie te activeren.  

 Voor de aanmeldingsscriptinstallatie worden dezelfde methodes gebruikt als handmatige clientinstallatie. U kunt de **/logon** installatie-eigenschap voor CCMSsetup.exe opgeven, die voorkomt dat de client installeert indien er al een versie van de client op de computer bestaat. Dit voorkomt dat de client opnieuw wordt geïnstalleerd telkens wanneer het aanmeldingsscript uitgevoerd wordt.  

 Als geen installatiebron opgegeven is die de **/Source** eigenschap en geen beheerpunt van waaruit worden verkregen installatie is opgegeven met behulp van de **/MP** eigenschap CCMSetup.exe kan het beheerpunt lokaliseren door Active Directory Domain Services zoeken als het schema is uitgebreid voor Configuration Manager en de site wordt gepubliceerd naar Active Directory Domain Services. De client kan in plaats daarvan DNS of WINS gebruiken om een beheerpunt te zoeken.  

##  <a name="BKMK_ClientApp"></a>Het installeren van clients met een pakket en programma  
 U kunt de Configuration Manager gebruiken voor het maken en implementeren van een pakket en programma dat de clientsoftware voor geselecteerde computers in uw hiërarchie bijwerkt. Een pakketdefinitiebestand dat de pakketeigenschappen met gewoonlijk gebruikte waarden invult wordt geleverd met Configuration Manager. U kunt het gedrag van de clientinstallatie aanpassen door aanvullende opdrachtregeleigenschappen op te geven.  

> [!NOTE]  
>  U upgraden Configuration Manager 2007-clients met deze methode niet. Gebruik in plaats daarvan de automatische clientupgrade, waarbij automatisch een pakket wordt geïmplementeerd met de meest recente versie van de client. Zie [Clients bijwerken in System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) voor meer informatie.  
>   
>  Zie voor meer informatie over het migreren van oudere versies van de Configuration Manager-client [een strategie voor clientmigratie in System Center Configuration Manager plannen](../../../core/migration/planning-a-client-migration-strategy.md).  

 
###<a name="to-create-a-package-and-program-for-the-client-software"></a>Een pakket en programma voor de clientsoftware maken  

Gebruik de volgende procedure voor het maken van een Configuration Manager-pakket en programma dat u kunt implementeren op clientcomputers van Configuration Manager om de clientsoftware te werken.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **pakket maken vanuit definitie**.  

4.  Op de **pakketdefinitie** pagina van de wizard, selecteert u **Microsoft** van de **Publisher** vervolgkeuzelijst en selecteer **Configuration Manager-Clientupgrade** van de **definitie van het pakket** lijst.  

5.  Op de **bronbestanden** optie **altijd bestanden van de bronmap ophalen**.  

6.  Op de **bronmap** optie **netwerkpad (UNC-naam)** en voert u het netwerkpad naar de computer en de map met de clientinstallatiebestanden.  

    > [!NOTE]  
    >  De computer waarop de Configuration Manager-implementatie wordt uitgevoerd toegang moeten hebben tot de netwerkmap die u opgeeft, anders mislukt de installatie.  

    Als u een van de eigenschappen van clientinstallatie wilt veranderen, kunt u de CCMSetup.exe opdrachtregelparameters op tabblad **Algemeen** van het programmadialoogvenster **Eigenschappen van Configuration Manager-agentupgrade op de achtergrond** wijzigen. De standaard installatie-eigenschappen zijn **/noservice SMSSITECODE=AUTO**.  

9. Het pakket naar alle distributiepunten distribueren waarnaar u het clientupgradepakket wilt hosten. U kunt het pakket vervolgens implementeren naar verzamelingen van computers met clients die u wilt bijwerken.  

## <a name="how-to-install-clients-to-intune-mdm-managed-windows-devices"></a>Clients installeren op Windows Intune MDM-beheerde apparaten

U kunt de clientinstallatiebestanden implementeren op computers die zijn ingeschreven bij Microsoft Intune. 

Het apparaat in een beheerde status blijft nadat de clientsoftware is geïnstalleerd, zodat moet het apparaat op het bedrijfsnetwerk bevinden en binnen de sitegrens van een Configuration Manager. 

> [!NOTE]
> Nadat de clientsoftware is geïnstalleerd, wordt het apparaat wordt uitgeschreven uit Intune.

### <a name="to-install-clients-with-intune"></a>Clients installeren met Intune:

1. In Intune, [maken van een app](/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) met het installatiebestand van de Configuration Manager-client **ccmsetup.msi**.

2. In de Intune-Software-uitgever parameters gebruiken om de volgende opdrachtregel:

  **CCMSETUPCMD = "/ MP:&lt;FQDN-naam van het beheerpunt > SMSMP =&lt;FQDN-naam van het beheerpunt > SMSSITECODE =&lt;uw sitecode > DNSSUFFIX =&lt;DNS-achtervoegsel van het beheerpunt >"**

3. [Implementeer de app](/intune/deploy-use/deploy-apps-in-microsoft-intune) op ingeschreven Windows-computers.

##  <a name="BKMK_ClientImage"></a>Het installeren van clients met een installatiekopie  
U kunt de Configuration Manager-clientsoftware op een master-image computer die u gebruikt voor andere computers installeren vanaf installatiekopie vooraf installeren.   

### <a name="to-prepare-the-client-computer-for-imaging"></a>De clientcomputer voorbereiden voor imaging  

1.  De Configuration Manager-clientsoftware handmatig installeren op de master-image computer. Zie [Configuration Manager-clients handmatig installeren](#BKMK_Manual) voor meer informatie.  

    > [!IMPORTANT]  
    >  Geef een Configuration Manager-sitecode voor de client in de CCMSetup.exe opdrachtregeleigenschappen.  

2.  Typ **net stop ccmexec** op een opdrachtegel om ervoor te zorgen dat de **Host van SMS-agent**-service (Ccmexec.exe) niet wordt uitgevoerd op de computer met de masterinstallatiekopie.  

3.  Verwijder certificaten die opgeslagen zijn in de lokale opslag van de computer op de computer met de masterinstallatiekopie.  Als u bijvoorbeeld PKI (Public Key Infrastructure)-certificaten gebruikt, dan moet u de certificaten verwijderen in het **Persoonlijke** archief voor de **Computer** en **Gebruiker** voordat u een installatiekopie van de computer maakt.

4.  Als de clients zullen worden geïnstalleerd in een andere Configuration Manager-hiërarchie dan de master-image computer, verwijdert u de vertrouwde basissleutel van de master-image computer.  
    > [!NOTE]  
    >  Als de clients Active Directory Domain Services niet kunnen verzoeken een beheerpunt te zoeken, dan gebruiken deze de vertrouwde basissleutel om vertrouwde beheerpunten te bepalen. Als alle clients waarvan een installatiekopie is gemaakt worden geïmplementeerd in dezelfde hiërarchie als de hoofdcomputer, behoudt u de vertrouwde basissleutel. Als de clients in verschillende hiërarchieën worden geïmplementeerd, verwijdert u de vertrouwde basissleutel en voorziet u, als aanbevolen procedure, deze clients met de nieuwe vertrouwde basissleutel. Zie [Planning voor de vertrouwde basissleutel](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) voor meer informatie. 

5.  Gebruik uw software voor het maken van installatiekopieën om de installatiekopie van de mastercomputer vast te leggen.  

6.  De installatiekopie implementeren op doelcomputers.  

##  <a name="BKMK_ClientWorkgroup"></a>Clients installeren op computers in werkgroepen  
 Configuration Manager ondersteunt clientinstallatie voor computers in werkgroepen. Installeer de client op werkgroepcomputers via de in [Handmatig Configuration Manager-clients installeren](#BKMK_Manual) beschreven methode.  

 Vereisten:  

-   De client moet handmatig worden geïnstalleerd op elke werkgroepcomputer. Tijdens de installatie, moet de aangemelde gebruiker lokale beheerdersrechten hebben.  

-   Voor toegang tot bronnen in het domein van Configuration Manager site server, moet het netwerktoegangsaccount worden geconfigureerd voor de site. Dit account opgeven als een eigenschap softwaredistributie-onderdeel. Zie [Siteonderdelen voor System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md) voor meer informatie.  

 Beperkingen:  

-   Werkgroepclients kunnen geen beheerpunten localiseren vanaf Active Directory Domain Services en moeten in plaats daarvan DNS, WINS of een ander beheerpunt gebruiken.  

-   Globale roaming wordt niet ondersteund, omdat client Active Directory Domain Services niet kunnen bevragen voor site-informatie.  

-   Active Directory-detectiemethoden kunnen computers in werkgroepen niet detecteren.  

-   U kunt software niet implementeren voor gebruikers van computers in werkgroepen.  

-   U kunt de clientpushinstallatiemethode niet gebruiken om de client te installeren op werkgroepcomputers.  

-   Werkgroepclients kunnen Kerberos niet gebruiken voor verificatie en kunnen handmatige goedkeuring vereisen.  

-   Een werkgroep-client kan niet worden geconfigureerd als een distributiepunt. Configuration Manager vereist dat distributiepuntcomputers lid zijn van een domein.  

### <a name="to-install-the-client-on-workgroup-computers"></a>De client installeren op computers in werkgroepen  

Controleer de vereisten en volg de aanwijzingen in de sectie [Configuration Manager-Clients handmatig installeren](#BKMK_Manual).  

   In dit voorbeeld installeert de client voor intranetclientbeheer en geeft de sitecode en DNS-achtervoegsel om een beheerpunt te vinden:`**CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=constoso.com**`  

     

   Dit voorbeeld vereist dat de client zich op een netwerklocatie bevindt die geconfigureerd is in een grensgroep zodat automatische sitetoewijzing kan slagen. De opdracht bevat een terugvalstatuspunt op server FSPSERVER, voor het bijhouden van de implementatie van clients te identificeren en eventuele problemen met clientcommunicatie:`**CCMSetup.exe FSP=fspserver.constoso.com**`  

      

##  <a name="BKMK_ClientInternet"></a>Het installeren van clients voor clientbeheer via Internet  
 Wanneer de Configuration Manager-site Internet-gebaseerd clientbeheer voor clients die soms op het intranet, en soms ook op het Internet ondersteunt, hebt u twee opties wanneer u clients op het intranet installeert:  

-   U kunt de Client.msi-eigenschap van CCMHOSTNAME opnemen =*&lt;Internet-FQDN van het Internet gebaseerde beheerpunt\>*  wanneer u de client installeert, bijvoorbeeld met behulp van handmatige installatie of client-push. Wanneer u deze methode gebruikt, moet u ook de client direct toewijzen aan de site en kunt u niet automatische sitetoewijzing gebruiken. De sectie [Handmatig Configuration Manager-clients toewijzen](#BKMK_Manual) in dit onderwerp levert een voorbeeld van deze configuratiemethode.  

-   U kunt de client installeren voor clientbeheer op intranet, en vervolgens wijst u een Internet-gebaseerd clientbeheer wijst de client met behulp van de clienteigenschappen van de Configuration Manager-in het Configuratiescherm, of via een script. Wanneer u deze methode gebruikt, kunt u automatische clienttoewijzing gebruiken. Zie voor meer informatie, de sectie [Clients configureren voor internetclientbeheer na clientinstallatie](#BKMK_ConfigureIBCM_MP) in dit onderwerp.  

 Indien u clients moet installeren die op het Internet zijn omdat ze alleen-Internet clients zijn, of omdat u ze moet installeren vóór ze terugkeren naar het intranet, kies dan één van de volgende ondersteunde methodes:  

-   Bieden een mechanisme voor deze clients om tijdelijk te verbinden met het intranet met een virtueel particulier netwerk (VPN) en installeer ze dan door een geschikte clientinstallatiemethode te gebruiken.  

-   Gebruik een installatiemethode die onafhankelijk is van Configuration Manager, zoals het verpakken van de clientinstallatiebronbestanden op uitwisselbare media die u naar gebruikers zenden kunt om te installeren met behulp van instructies. De clientinstallatiebronbestanden bevinden zich in de  *&lt;installatiepad\>*\Client map op de Configuration Manager site server en beheerpunten. Neem op de media ook een script op om handmatig te kopiëren via de clientmap en vanaf deze map, installeer de client door gebruik te maken van CCMSetup.exe en van alle geschikte CCMSetup-opdrachtregeleigenschappen.  

> [!NOTE]  
>  Configuration Manager biedt geen ondersteuning voor het installeren van een client direct vanuit het internetgebaseerde beheerpunt of vanuit het internetgebaseerde software-updatepunt.  

 Verzeker dat deze clients ook certificaten hebben geïnstalleerd met openbare-sleutelinfrastructuur vóór u ze installeert, omdat clients die via het Internet beheerd worden, moeten communiceren met Internetsitesystemen U moet deze certificaten onafhankelijk van Configuration Manager installeert. Zie [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md) voor meer informatie over de certificaatvereisten.  

### <a name="to-install-clients-on-the-internet-by-specifying-ccmsetup-command-line-properties"></a>Clients installeren op het Internet door het opgeven van CCMSetup-opdrachtregeleigenschappen  

1.  Volg de richtlijnen in de sectie [Handmatig Configuration Manager clients installeren](#BKMK_Manual) en neem altijd het volgende op:  

    -   CCMSetup-opdrachtregeleigenschap **/source:***&lt;lokale pad naar de map van de gekopieerde Client\>*  

    -   CCMSetup-opdrachtregel eigenschap **/UsePKICert**  

    -   Client.msi-eigenschap **CCMHOSTNAME =***&lt;FQDN-naam van de Internet-gebaseerd beheerpunt bevindt\>*  

    -   Client.msi-eigenschap **SMSSIGNCERT =***&lt;lokale pad naar het geëxporteerde handtekeningcertificaat van siteserver\>*  

    -   Client.msi-eigenschap **SMSSITECODE =***&lt;sitecode van het beheerpunt op Internet\>*  

    > [!NOTE]  
    >  Indien de site meer dan één beheerpunt op Internet heeft, heeft het geen belang welk beheerpunt op Internet u opgeeft voor de CCMHOSTNAME-eigenschap. Wanneer een Configuration Manager-client verbinding met de opgegeven internetgebaseerde beheerpunt maakt, het beheerpunt stuurt de client een lijst met beschikbare internetgebaseerde beheerpunten in de site en de client selecteert één van de lijst willekeurig.  

2.  Indien u niet wilt dat de client de certificaatintrekkingslijst controleert (CRL), geef dan de CCMSetup-opdrachtregeleigenschap op **/NoCRLCheck**.  

3.  Als u een Internet-terugvalstatuspunt op, geef de Client.msi-eigenschap **FSP =***&lt;Internet-FQDN van het Internet gebaseerde terugvalstatuspunt\>*.  

4.  Indien u de client installeert voor alleen-internet clientbeheer, geef dan de Client.msi-eigenschap **CCMALWAYSINF=1** op.  

5.  Controleer of u bijkomende CCMSetup-opdrachtregeleigenschappen opgeven. Mogelijk moet u een certificaat selectiecriterium opgeven als de client meer dan één geldig PKI-certificaat heeft. Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor een lijst met beschikbare eigenschappen.  

   Voorbeeld: `**CCMSetup.exe /source: D:\Clients /UsePKICert CCMHOSTNAME=server1.contoso.com SMSSIGNCERT=siteserver.cer SMSSITECODE=ABC FSP=server2.contoso.com CCMALWAYSINF=1 CCMFIRSTCERT=1**`  

   Dit voorbeeld installeert de clientbronbestanden van een map op het D-station met instellingen om een client-PKI-certificaat te gebruiken en om het certificaat te selecteren met de langste geldigheidsduur voor Internetclientbeheer, en wijst de client toe om het beheerpunt op Internet SERVER1 te gebruiken en het terugvalstatuspunt op Internet in het contoso.com domein, en wijst de client toe aan de ABC-site.  

###  <a name="BKMK_ConfigureIBCM_MP"></a>Clients configureren voor Internet-gebaseerd clientbeheer na de clientinstallatie  
 Gebruik één van de volgende procedures om het beheerpunt op Internet toe te wijzen nadat de client geïnstalleerd is: De eerste vereist handmatige configuratie en geschikt is voor enkele clients. De tweede is meer geschikt is voor het configureren van veel clients.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-assigning-the-internet-based-management-point-in-configuration-manager-properties"></a>Client voor clientbeheer via Internet configureren na clientinstallatie door het beheerpunt op Internet in Configuration Manager-eigenschappen toe te wijzen  

1.  Navigeer naar **Configuration Manager** in het configuratiescherm van de clientcomputer en dubbelklik er vervolgens op om de eigenschappen ervan te openen.  

2.  Voer op het tabblad **Internet** de volledig gekwalificeerde domeinnaam in van het beheerpunt op internet in het FQDN-internettekstvak.  

    > [!NOTE]  
    >  Het tabblad **Internet** is enkel beschikbaar als de client een PKI-certificaat heeft.  

3.  Voer proxyserverinstellingen in als de client toegang zal krijgen tot het Internet door gebruik te maken van een proxyserver.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-using-a-script"></a>Clients configureren voor clientbeheer via Internet na installatie van de client door gebruik te maken van een script.  

1.  Open een teksteditor, zoals Kladblok.  

2.  Kopieer het volgende en voeg in het bestand. Vervang *mp.contoso.com* met de internet-FQDN van uw beheerpunt op internet.  

    ```  
    on error resume next  

    ' Create variables.  
    Dim newInternetBasedManagementPointFQDN  
    Dim client  

    newInternetBasedManagementPointFQDN = "mp.contoso.com"  

    ' Create the client COM object.  
    Set client = CreateObject ("Microsoft.SMS.Client")  

    ' Set the Internet-Based Management Point FQDN by calling the SetCurrentManagementPoint method.  
    client.SetInternetManagementPointFQDN newInternetBasedManagementPointFQDN  

    ' Clear variables.  
    Set client = Nothing  
    Set internetBasedManagementPointFQDN = Nothing  

    ```  

    > [!NOTE]  
    >  Als u een opgegeven beheerpunt op internet wilt wissen zodat de client niet is geconfigureerd om een beheerpunt op internet te gebruiken, verwijdert u de waarde binnen de aanhalingstekens zodat deze regel **newInternetBasedManagementPointFQDN = ""** wordt.  

4.  Sla het bestand op met een VBS-extensie.  

5.  Gebruik cscript om het script uit te voeren op clientcomputers, door één van de volgende methodes te gebruiken:  

    -   Implementeer het bestand naar bestaande Configuration Manager-clients door gebruik te maken van een pakket en een programma.  

    -   Voer het bestand lokaal uit op bestaande Configuration Manager-clients door te dubbelklikken op het scriptbestand in Windows Explorer.  

 U moet wellicht opnieuw opstarten van de client om de wijzigingen van kracht te laten worden.  

##  <a name="BKMK_Provision"></a>Hoe clientinstallatie-eigenschappen (groep beleid en software-update gebaseerde clientinstallatie)  
 U kunt Windows groepsbeleid gebruiken om van computers met Configuration Manager clientinstallatie-eigenschappen. Deze eigenschappen worden opgeslagen in het register van de computer en worden gelezen wanneer de clientsoftware is geïnstalleerd. Deze procedure is normaal niet vereist, maar het kan nodig zijn voor sommige scenario's van clientinstallatie, zoals:  

-   U gebruikt de instellingen voor Groepsbeleid of software-update gebaseerde methode voor clientinstallatie en u hebt het Active Directory-schema niet uitgebreid voor Configuration Manager.  

-   U wilt de eigenschappen van clientinstallatie op specifieke computers overschrijven.  

> [!NOTE]  
>  Indien installatie-eigenschappen ingebracht worden op de CCMSetup.exe opdrachtregel, zullen installatie-eigenschappen geleverd op computers niet gebruikt worden.  

 Een Groepsbeleid beheersjabloon ConfigMgrInstallation.adm genaamd is geleverd op de installatiemedia van Configuration Manager, die kunnen worden gebruikt om clientcomputers met installatie-eigenschappen in te richten.   

### <a name="to-configure-and-assign-client-installation-properties-by-using-a-group-policy-object"></a>Eigenschappen van clientinstallatie configureren en toewijzen door gebruik te maken van een groepsbeleidsobject  

1.  Importeer de beheersjabloon ConfigMgrInstallation.adm in een nieuw of bestaand groepsbeleidsobject, door gebruik te maken van een editor zoals Windows groepsbeleidsobject-editor. Het bestand kan worden gevonden in de map **TOOLS\ConfigMgrADMTemplates** op de installatiemedia van Configuration Manager.  

2.  Open de eigenschappen van de geïmporteerde instelling **Configureer instellingen clientimplementatie**.  

3.  Kies **ingeschakeld**.  

4.  Voer in het vakje **CCMSetup** de vereiste CCMSetup-opdrachtregeleigenschappen in. Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor een lijst met alle CCMSetup-opdrachtregeleigenschappen en voorbeelden waarin ze gebruikt worden.  

5.  De Group Policy Object toewijzen aan de computers die u inrichten met Configuration Manager clientinstallatie-eigenschappen wilt.  

 Raadpleeg uw Windows Server-documentatie voor informatie over Windows groepsbeleid.  

### <a name="see-also"></a>Zie tevens
[Installatiemethoden voor clients in System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md)
