---
title: Clients implementeren op Windows
titleSuffix: Configuration Manager
description: Informatie over het implementeren van Configuration Manager-client op Windows-computers.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 341f0d0b-f907-44cf-9e10-e1b41fc15f82
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3d7c3e9c9f2af8d612ef158897c281d422692268
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-deploy-clients-to-windows-computers-in-system-center-configuration-manager"></a>Clients implementeren op Windows-computers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u Configuration Manager-clients installeert, zorg ervoor dat alle de [vereisten](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) zijn voldaan en dat u alle vereiste implementatieconfiguraties hebt voltooid.   



##  <a name="BKMK_ClientPush"></a> Clients installeren met client-push  

U kunt de push-clientinstallatie voor een site configureren. Installatie van de client wordt automatisch uitgevoerd op de computers die zijn gedetecteerd binnen de geconfigureerde grenzen van de site wanneer deze grenzen als een grensgroep zijn geconfigureerd. Of u kunt een push-clientinstallatie starten door de Push-clientinstallatiewizard uit te voeren voor een specifieke verzameling of bron binnen een verzameling.  

U kunt ook de Wizard Push-clientinstallatie gebruiken voor het installeren van de Configuration Manager-client [query](../../../core/servers/manage/queries-technical-reference.md) resultaten. Voor de installatie te kunnen uitvoeren, moet een van de items die door de query het kenmerk **ResourceID** uit de klasse **systeembron**.   

Als de siteserver kan geen contact op met de clientcomputer of het installatieproces start, wordt de installatie om het uur automatisch opnieuw geprobeerd. De server blijft gedurende zeven dagen opnieuw.  

Voor het bijhouden van het installatieproces van de client, een terugvalstatuspunt te installeren voordat u de clients installeert. Wanneer een terugvalstatuspunt is geïnstalleerd, wordt deze automatisch toegewezen aan clients wanneer ze door de push-clientinstallatiemethode zijn geïnstalleerd. Als u wilt bijhouden vooruitgang van de clientinstallatie, bekijk de clientimplementatie en toewijzingsrapporten. 

Logboekbestanden van client bieden meer gedetailleerde informatie over het oplossen van problemen. De logboekbestanden hebben geen een terugvalstatuspunt nodig. Bijvoorbeeld, de **CCM.log** -bestand op de siteserver registreert problemen van de siteserver om verbinding te maken met de computer. De **CCMSetup.log** bestand op de client registreert het installatieproces.  

> [!IMPORTANT]  
>  Opdat client-push zou lukken, dient u ervoor te zorgen dat alle vereiste onderdelen zijn geïnstalleerd. Zie voor meer informatie [installatiemethode-afhankelijkheden](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#installation-method-dependencies).  

### <a name="configure-the-site-to-automatically-use-client-push-for-discovered-computers"></a>De site voor client-push automatisch te gebruiken voor gedetecteerde computers configureren

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de site waarvoor u wilt configureren van automatische gehele site clientpushinstallatie.  

4.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **clientinstallatie-instellingen** > **Push-clientinstallatie**.  

5.  Op de **algemene** tabblad van de **Clientpushinstallatie-eigenschappen** dialoogvenster Selecteer **Schakel automatische gehele site clientpushinstallatie**. Selecteer de systeemtypes waarop Configuration Manager de clientsoftware moet pushen.  

6.  Selecteer of u wilt dat de client te installeren op domeincontrollers.  

7.  Op de **Accounts** tabblad, geeft u een of meer accounts voor Configuration Manager gebruiken om verbinding te maken met de doelcomputer. Klik op de **maken** pictogram en voer de **gebruikersnaam** en **wachtwoord** (niet meer dan 38 tekens), bevestig het wachtwoord en klik vervolgens op **OK**. Geef ten minste één push-clientinstallatieaccount. Dit account moet lokale beheerdersrechten hebben op de doelcomputer om de client te installeren. Als u niet een push-clientinstallatieaccount opgeeft, wordt Configuration Manager probeert te gebruiken van het computeraccount van sitesysteem. Verschillende domeinen client-push mislukt wanneer u de computeraccount van sitesysteem.  
    > [!NOTE]  
    >  Geef voor het gebruik van client-push van een secundaire site, de account op de secundaire site die de clientpush start.  
    >   
    >  Zie de volgende procedure voor meer informatie over de push-clientinstallatieaccount [gebruik van de Wizard Push-clientinstallatie](#use-the-client-push-installation-wizard).  

8.  Voltooi de **installatie-eigenschappen** tabblad.

     Als het schema wordt uitgebreid voor Configuration Manager, de site publiceert naar Active Directory Domain Services de [clientinstallatie-eigenschappen](../../../core/clients/deploy/about-client-installation-properties.md) die u opgeeft op dit tabblad. Deze eigenschappen worden gelezen door clientinstallaties waar CCMSetup wordt uitgevoerd zonder installatie-eigenschappen.  

    > [!NOTE]  
    >  Als u push-clientinstallatie op een secundaire site inschakelt, zorg ervoor dat de **SMSSITECODE** eigenschap is ingesteld op de naam van de Configuration Manager-site van de bovenliggende primaire site. Als het Active Directory-schema is uitgebreid voor Configuration Manager, kunt u deze eigenschap ook instellen op AUTO automatisch de juiste sitetoewijzing te vinden.  

### <a name="use-the-client-push-installation-wizard"></a>Gebruik de Wizard Push-clientinstallatie

1.  Kies in de Configuration Manager-console **beheer** >  **siteconfiguratie** > **Sites**.  

3.  Selecteer de site waarvoor u wilt configureren van automatische gehele site clientpushinstallatie.  

4.  Op de **Start** tabblad > **instellingen** groep, kiest u **clientinstallatie-instellingen** > **Push-clientinstallatie**.  

5.  Voltooi de **installatie-eigenschappen** tabblad.  

     Als het schema wordt uitgebreid voor Configuration Manager, de site publiceert naar Active Directory Domain Services de [clientinstallatie-eigenschappen](../../../core/clients/deploy/about-client-installation-properties.md) die u opgeeft op dit tabblad. Deze eigenschappen worden gelezen door clientinstallaties waar CCMSetup wordt uitgevoerd zonder installatie-eigenschappen.   

6.  Kies in de Configuration Manager-console **activa en naleving**.  

7.  Selecteer in de werkruimte **Activa en naleving** een of meerdere computers, of een verzameling van computers.  

8.  Op de **Start** tabblad, kies een van de volgende opties:  

    -   Als u wilt dat de client te installeren op één computer of meerdere computers in de **apparaat** groep, kiest u **Client installeren**.  

    -   Als u wilt dat de client te installeren op een verzameling van computers in de **verzameling** groep, kiest u **Client installeren**.  

9. Op de **voordat u begint** pagina van de **Wizard Client installeren**, lees de informatie in en kies vervolgens **volgende**.  

10. Voltooi de **installatieopties** pagina.  

11. Controleer de installatie-instellingen en sluit vervolgens de wizard.  

> [!NOTE]  
>  De wizard kunt u clients installeert, zelfs als de site is niet geconfigureerd voor client-push.  



##  <a name="BKMK_ClientSUP"></a> Het installeren van clients met software-update-gebaseerde installatie  
 Software-update gebaseerde clientinstallatie publiceert de client naar een software-updatepunt als een software-update. Gebruik deze methode voor een eerste installatie of upgrade.  

 Als een computer de Configuration Manager-client is geïnstalleerd heeft, wordt het beleid voor client ontvangt van de site. Dit beleid bevat de servernaam software-updatepunt en de poort van waaruit software-updates ophalen.   

> [!IMPORTANT]  
>  Om installatie op basis van software-updates te gebruiken, moet u dezelfde Windows Server Update Services (WSUS)-server gebruiken voor clientinstallatie en software-updates. Deze server moet het actieve software-updatepunt in een primaire site zijn. Zie voor meer informatie [installeert een software-updatepunt](../../../sum/get-started/install-a-software-update-point.md).  

Als een computer geen Configuration Manager-client geïnstalleerd, configureren en toewijzen van een groepsbeleidobject in Active Directory Domain Services om op te geven de servernaam van de software-updatepunt.  

U kunt geen opdrachtregeleigenschappen toevoegen aan een software-update gebaseerde clientinstallatie. Als u hebt het Active Directory-schema voor Configuration Manager uitgebreid, vragen clientcomputers automatisch Active Directory Domain Services naar installatie-eigenschappen wanneer ze installeren.  

Als u het Active Directory-schema niet hebt uitgebreid, kunt u Groepsbeleid inrichten clientinstallatie-instellingen op computers in uw site. Deze instellingen worden automatisch toegepast op installaties op basis van software-updates. Zie voor meer informatie [inrichten clientinstallatie-eigenschappen (groep beleid en software-update gebaseerde clientinstallatie)](#BKMK_Provision) en [clients toewijzen aan een site](../../../core/clients/deploy/assign-clients-to-a-site.md).  

Gebruik de volgende procedures voor het configureren van computers zonder een Configuration Manager-client de softwareupdate te gebruiken voor clientinstallatie en software-updates en voor het publiceren van de client software op het software-updatepunt.  

> [!NOTE]  
>  Als een herstart voor een computer in behandeling is na een eerdere software-installatie, wordt de computer mogelijk opnieuw opgestart door een op een software-update gebaseerde clientinstallatie.  

### <a name="configure-a-group-policy-object-in-active-directory-domain-services-to-specify-the-software-update-point-for-client-installation-and-software-updates"></a>Een groepsbeleidobject in Active Directory Domain Services om op te geven van de software-updatepunt voor client-installatie- en software-updates configureren:  

1.  Gebruik de Console Groepsbeleidsbeheer een nieuw of bestaand groepsbeleidobject te openen.  

2.  In de console, vouw **Computerconfiguratie**, vouw **Beheersjablonen**, vouw **Windows-onderdelen**, en kies vervolgens **Windows Update**.  

3.  Open de eigenschappen van de instelling **Microsoft updateservicelocatie in intranet opgeven**, en kies vervolgens **ingeschakeld**.  

4.  In het vak **Stel de updateservice in intranet voor het detecteren van updates**, geef de naam en poort van de softwareserver-updatepunt:  

    -   Als het Configuration Manager-sitesysteem is geconfigureerd voor het gebruik van een volledig gekwalificeerde domeinnaam (FQDN), gebruikt u de FQDN-indeling.  

    -   Als het Configuration Manager-sitesysteem is niet geconfigureerd voor het gebruik van een FQDN-naam, gebruikt u een kort naamformaat.  

    > [!NOTE]  
    >  Als u wilt vaststellen welk poortnummer, Zie [het bepalen van de gebruikte poortinstellingen door WSUS](../../../sum/plan-design/plan-for-software-updates.md).  

     Voorbeeld: **http://server1.contoso.com:8530**  

5.  In het vak **intranetserver voor statistische gegevens**, geef de naam van de intranetserver voor statistische gegevens. Heeft geen moet hetzelfde zijn als de software-updatepuntserver. Als het dezelfde server, hebben niet overeenkomen met de indeling.  

6.  Het groepsbeleidsobject toewijzen aan de computers waarop u wilt de client installeren en software-updates wilt ontvangen.  

### <a name="publish-the-configuration-manager-client-to-the-software-update-point"></a>De Configuration Manager-client op het software-updatepunt publiceren  

1.  Klik in de Configuration Manager-console op **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de site waarvoor u wilt configureren van software-update gebaseerde clientinstallatie.  

4.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **clientinstallatie-instellingen**, en kies vervolgens **clientinstallatie**.  

5.  Selecteer **software-update gebaseerde clientinstallatie inschakelt**.  

6.  Als de clientsoftware op de Configuration Manager-siteserver een latere versie dan de versie op het software-updatepunt, is de **latere versie van clientpakket gedetecteerd** dialoogvenster wordt geopend. Klik op **Ja** voor het publiceren van de meest recente versie.  

    > [!NOTE]  
    >  Als de clientsoftware is niet eerder is gepubliceerd op het software-updatepunt, dit vak leeg is.  

De software-update voor Configuration Manager-client wordt niet automatisch bijgewerkt wanneer er een nieuwe versie. Als u een upgrade uitvoert van de site die een nieuwe clientversie bevat, deze procedure herhalen en op **Ja** voor stap 6.  



##  <a name="BKMK_ClientGP"></a> Het installeren van clients met Groepsbeleid  
 U kunt Groepsbeleid in Active Directory Domain Services publiceren of toewijzen van de Configuration Manager-client installeren op computers in uw onderneming. De client geïnstalleerd wanneer de computer wordt gestart. Wanneer u Groepsbeleid, toont de client in het Configuratiescherm **een programma verwijderen of** voor de gebruiker installeren.  

 Gebruik de Windows Installer-pakket (CCMSetup.msi) voor installaties van groep op basis van beleid. Dit bestand staat in de map  **&lt;installatiemap van Configuration Manager\>\bin\i386** op de siteserver van Configuration Manager. U kunt geen eigenschappen toevoegen aan dit bestand naar het installatiegedrag wijzigen.  

> [!IMPORTANT]  
>  U moet Administrator-machtigingen voor toegang tot de clientinstallatiebestanden hebben.  

-   Als het Active Directory-schema voor Configuration Manager is uitgebreid en **deze site publiceren in Active Directory Domain Services** is geselecteerd in de **Geavanceerd** tabblad van de **Site-eigenschappen** in het dialoogvenster zoeken clientcomputers automatisch Active Directory Domain Services naar installatie-eigenschappen. Zie voor meer informatie over de installatie-eigenschappen die zijn gepubliceerd, [over clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

-   Als het Active Directory-schema niet is uitgebreid, kunt u de procedure in dit onderwerp voor het opslaan van de installatie-eigenschappen in het register van computers: [Het inrichten van de clientinstallatie-eigenschappen (groep beleid en software-update gebaseerde clientinstallatie)](#BKMK_Provision). Deze installatie-eigenschappen worden gebruikt wanneer de client is geïnstalleerd.  

Raadpleeg de Windows Server-documentatie voor informatie over hoe Groepsbeleid in Active Directory Domain Services gebruiken om software te installeren.  



##  <a name="BKMK_Manual"></a> Clients handmatig installeren  
 U kunt handmatig de clientsoftware installeren op computers in uw bedrijf met behulp van het programma CCMSetup.exe. Dit programma en de ondersteunende bestanden vindt u in de **Client** map van de Configuration Manager-installatiemap op de siteserver en op beheerpunten in uw site. Deze map wordt op het netwerk gedeeld als  

 \\\\*&lt;Siteservernaam\>*\SMS_*&lt;sitecode\>*\Client\  

 waar *&lt;Siteservernaam\>* is de naam van een van de servers waarop een beheerpunt wordt gehost, en *&lt;sitecode\>* is de primaire sitecode die de client is toegewezen. Als u CCMSetup.exe vanaf de opdrachtregel op de client wilt uitvoeren, moet u een netwerkstation toewijzen aan deze locatie en daarna de opdracht uitvoeren.  

> [!IMPORTANT]  
>  U moet Administrator-machtigingen voor toegang tot de clientinstallatiebestanden hebben.  

 CCMSetup.exe kopieert alle vereisten voor de clientcomputer en roept het Windows Installer-pakket (Client.msi) om de client te installeren. Client.msi kan niet rechtstreeks worden uitgevoerd.  

 U kunt opdrachtregeleigenschappen opgeven zowel voor CCMSetup.exe  als voor Client.msi om het gedrag van de clientinstallatie te wijzigen. Zorg ervoor dat u CCMSetup-eigenschappen opgeeft (de eigenschappen die met beginnen **/**) voordat u de Client.msi-eigenschappen opgeeft. Bijvoorbeeld:  

`CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=AUTO FSP=SMSFP01`    

dan wordt de client geïnstalleerd met de volgende eigenschappen:  

|Eigenschap|Beschrijving|  
|--------------|-----------------|  
|**/mp:SMSMP01**|Deze CCMSetup-eigenschap geeft het beheerpunt SMSMP01 op om de vereiste clientinstallatiebestanden te downloaden.|  
|**/logon**|Deze CCMSetup-eigenschap geeft aan dat de installatie moet worden stopgezet als een bestaande Configuration Manager-client op de computer is gevonden.|  
|**SMSSITECODE = AUTO**|Deze Client.msi-eigenschap geeft op dat de client tracht de sitecode van de Configuration Manager-site moet worden gebruikt, bijvoorbeeld met behulp van Active Directory Domain Services vinden.|  
|**FSP=SMSFP01**|Deze Client.msi-eigenschap geeft aan dat het terugvalstatuspunt met naam SMSFP01 wordt gebruikt voor de ontvangst van statusberichten die zijn verzonden vanaf de clientcomputer.|  

 Zie voor meer informatie over alle CCMSetup.exe-eigenschappen [over clientinstallatie-eigenschappen](../../../core/clients/deploy/about-client-installation-properties.md)  

> [!Tip]  
> Zie voor de procedure voor het installeren van Configuration Manager-client op een moderne Windows 10-apparaat met behulp van Azure AD identity [installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure). Deze procedure is voor clients op het intranet of internet.  


### <a name="examples"></a>Voorbeelden
 Deze voorbeelden gelden voor Active Directory-clients op het intranet. Ze gebruikt de volgende waarden voor verschillende aspecten van de site:  

 **MPSERVER** = server die als host fungeert voor het beheerpunt   
**FSPSERVER** = server die als host fungeert voor het terugvalstatuspunt  
**ABC** = sitecode  
**contoso.com** = domeinnaam  

 Alle sitesysteemservers worden geconfigureerd met een intranet-FQDN. De site is gepubliceerd op Active Directory-forest van de client.  

 Op de clientcomputer, moet u zich aanmelden als een lokale beheerder, een station (z:) toewijzen aan\\\MPSERVER\SMS_ABC\Client, de opdrachtprompt overschakelen naar het station z en voer vervolgens een van de volgende opdrachten:  

 **Voorbeeld 1:**  

`CCMSetup.exe`  

In dit voorbeeld installeert de client zonder aanvullende eigenschappen. De client wordt automatisch geconfigureerd met de clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services. Er wordt automatisch geconfigureerd voor de volgende instellingen: 
- Sitecode. Deze instelling moet de netwerklocatie van de client moet worden opgenomen in een grensgroep die is geconfigureerd voor clienttoewijzing. 
- Beheerpunt
- Terugvalstatuspunt
- Communiceren via HTTPS alleen  
  
Zie voor meer informatie [over clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

 **Voorbeeld 2:**  

`CCMSetup.exe /MP:mpserver.contoso.com /UsePKICert SMSSITECODE=ABC CCMHOSTNAME=server05.contoso.com CCMFIRSTCERT=1 FSP=server06.constoso.com`
  
Dit voorbeeld wordt de automatische configuratie waarmee Active Directory Domain Services overschreven. Het vereist niet dat de netwerklocatie van de client wordt opgenomen in een grensgroep die is geconfigureerd voor clienttoewijzing. De installatie geeft in plaats daarvan de volgende instellingen:
- Sitecode
- Intranet-beheerpunt 
- Beheerpunt op Internet
- Terugvalstatuspunt dat verbindingen van internet aanvaardt
- Gebruik client PKI-certificaat (indien beschikbaar) is met de langste geldigheidsduur  



##  <a name="BKMK_ClientLogonScript"></a> Clients met aanmeldingsscripts installeren  
 Configuration Manager ondersteunt aanmeldingsscripts om de Configuration Manager-clientsoftware te installeren. U kunt het programmabestand **CCMSetup.exe** gebruiken in een aanmeldingsscript om de clientinstallatie te activeren.  

 Voor de aanmeldingsscriptinstallatie worden dezelfde methodes gebruikt als handmatige clientinstallatie. U kunt opgeven de **/logon** installatie-eigenschap voor CCMSsetup.exe. Als een willekeurige versie van de client al op de computer bestaat, deze eigenschap voorkomt dat van de client wordt geïnstalleerd. Dit gedrag voorkomt dat de client opnieuw wordt geïnstalleerd telkens wanneer het aanmeldingsscript uitgevoerd.  

 Als er geen installatiebron is opgegeven door de **/Source** eigenschap en geen beheerpunt van waaruit worden verkregen installatie wordt opgegeven door de **/MP** CCMSetup.exe-eigenschap wordt gezocht naar het beheerpunt door te zoeken naar Active Directory Domain Services. Dit gebeurt alleen als het schema is uitgebreid voor Configuration Manager en de site is gepubliceerd naar Active Directory Domain Services. De client kan in plaats daarvan DNS of WINS gebruiken om een beheerpunt te zoeken.  



##  <a name="BKMK_ClientApp"></a> Clients installeren met een pakket en programma  
 U kunt de Configuration Manager maken en implementeren van een pakket en programma waarmee de clientsoftware voor geselecteerde computers in uw hiërarchie bijwerkt. Een pakketdefinitiebestand dat de pakketeigenschappen met gewoonlijk gebruikte waarden invult wordt geleverd met Configuration Manager. U kunt het gedrag van de clientinstallatie aanpassen door aanvullende opdrachtregeleigenschappen.  

> [!NOTE]  
>  U kunt Configuration Manager 2007-clients niet bijwerken met deze methode. Gebruik in plaats daarvan de automatische clientupgrade, waarbij automatisch een pakket wordt geïmplementeerd met de meest recente versie van de client. Zie voor meer informatie [clients upgraden](../../../core/clients/manage/upgrade/upgrade-clients.md).  
>   
>  Zie voor meer informatie over het migreren van oudere versies van Configuration Manager-client [een strategie voor clientmigratie plannen](../../../core/migration/planning-a-client-migration-strategy.md).  

 
### <a name="create-a-package-and-program-for-the-client-software"></a>Een pakket en programma voor de clientsoftware maken  

Gebruik de volgende procedure voor het maken van een Configuration Manager-pakket en programma dat u kunt implementeren op clientcomputers van Configuration Manager om de clientsoftware te werken.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **pakketten**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **pakket maken vanuit definitie**.  

4.  Op de **pakketdefinitie** pagina van de wizard de optie **Microsoft** van de **Publisher** vervolgkeuzelijst en selecteer **Configuration Manager-Clientupgrade** van de **pakketdefinitie** lijst.  

5.  Op de **bronbestanden** pagina **altijd bestanden van de bronmap ophalen**.  

6.  Op de **bronmap** pagina **netwerkpad (UNC-naam)**. Voer vervolgens het netwerkpad naar de computer en de map met de clientinstallatiebestanden.  

    > [!NOTE]  
    >  De computer waarop de Configuration Manager-implementatie wordt uitgevoerd toegang tot de netwerkmap die u opgeeft hebben moeten, anders mislukt de installatie.  

    Als u wilt wijzigen van de eigenschappen van clientinstallatie, wijzigt u de CCMSetup.exe opdrachtregelparameters op de **algemene** tabblad van de **Configuration Manager achtergrond eigenschappen agentupgrade** programma dialoogvenster vak. De standaard installatie-eigenschappen zijn **/noservice SMSSITECODE=AUTO**.  

9. Het pakket naar alle distributiepunten distribueren waarnaar u het clientupgradepakket wilt hosten. Vervolgens kunt u het pakket implementeren naar verzamelingen van computers met clients die u wilt upgraden.  



## <a name="bkmk_mdm"></a>Het installeren van clients op Windows Intune MDM-beheerde apparaten

U kunt de installatiebestanden van de client implementeren op computers die zijn ingeschreven bij Microsoft Intune. 

Deze procedure is voor een traditionele client die is verbonden met het intranet. Deze verificatiemethoden van de traditionele client gebruikt. Om te controleren of dat het apparaat in een beheerde status blijft nadat de clientsoftware is geïnstalleerd, moet het apparaat op het intranet en binnen de sitegrens van een Configuration Manager.  

Zie voor de procedure voor het installeren van Configuration Manager-client op een moderne Windows 10-apparaat met behulp van Azure AD identity [installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

> [!NOTE]
> Nadat de clientsoftware is geïnstalleerd, wordt het apparaat uitgeschreven bij Intune.
> 
> Vanaf versie 1710, clients doen niet registratie ongedaan maken van Intune. Ze kunnen de Configuration Manager-client en de MDM-inschrijving op hetzelfde moment hebben. Zie voor meer informatie [mede management](/sccm/core/clients/manage/co-management-overview).

###  <a name="install-clients-with-intune"></a>Clients installeren met Intune:

1. In Intune, [maken van een app](/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) met het installatiebestand van de Configuration Manager-client **ccmsetup.msi**. Dit bestand staat in de map  **&lt;installatiemap van Configuration Manager\>\bin\i386** op de siteserver van Configuration Manager.

2. Voer opdrachtregelparameters in de Software-uitgever van Intune. Gebruik de volgende opdrachtregel gebruikt bijvoorbeeld met een traditionele client op het intranet:

  `CCMSETUPCMD="/MP:&lt;FQDN of management point> SMSMP=&lt;FQDN of management point> SMSSITECODE=&lt;Your site code> DNSSUFFIX=&lt;DNS Suffix of management point>"`  

   > [!Note]  
   > Zie voor een voorbeeld van de opdrachtregel gebruiken met een moderne Windows 10-client met behulp van Azure AD-verificatie, [voorbereiden Windows 10-apparaten voor het beheer van CO](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client).

3. [Implementeer de app](/intune/deploy-use/deploy-apps-in-microsoft-intune) op ingeschreven Windows-computers.



##  <a name="BKMK_ClientImage"></a> Clients installeren met de computerinstallatiekopie van een  
U kunt de Configuration Manager-clientsoftware op een referentiecomputer die u gebruikt voor het maken van een installatiekopie van het besturingssysteem vooraf installeren.   

> [!Important]
> Bij gebruik van de Configuration Manager-takenreeks voor het implementeren van de installatiekopie van het besturingssysteem, de [ConfigMgr-Client voorbereiden](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) takenreeksstap volledig worden verwijderd van de Configuration Manager-client. 

### <a name="prepare-the-client-computer-for-imaging"></a>De clientcomputer voorbereiden voor imaging  

1.  De Configuration Manager-clientsoftware handmatig installeren op de referentiecomputer. Zie [Configuration Manager-clients handmatig installeren](#BKMK_Manual) voor meer informatie.  

    > [!IMPORTANT]  
    >  Geen een Configuration Manager-sitecode opgeven voor de client in de CCMSetup.exe opdrachtregeleigenschappen.  

2.  Typ bij een opdrachtprompt `net stop ccmexec` ervoor te zorgen dat de **SMS Agent Host** service (Ccmexec.exe) wordt niet uitgevoerd op de referentiecomputer.
3.  Verwijder het bestand **SMSCFG. INI** van de **Windows** map op de referentiecomputer.  
3.  Verwijder certificaten die zijn opgeslagen in het archief van de lokale computer op de referentiecomputer. Als u bijvoorbeeld PKI (Public Key Infrastructure)-certificaten gebruikt, dan moet u de certificaten verwijderen in het **Persoonlijke** archief voor de **Computer** en **Gebruiker** voordat u een installatiekopie van de computer maakt.

4.  Als de clients zijn geïnstalleerd in een andere Configuration Manager-hiërarchie dan de referentiecomputer, verwijdert u de vertrouwde basissleutel van de referentiecomputer.  
    > [!NOTE]  
    >  Als de clients Active Directory Domain Services niet kunnen verzoeken een beheerpunt te zoeken, dan gebruiken deze de vertrouwde basissleutel om vertrouwde beheerpunten te bepalen. Als alle gerepliceerde clients worden geïmplementeerd in dezelfde hiërarchie als de hoofdcomputer, behoudt u de vertrouwde basissleutel. Als de clients in verschillende hiërarchieën worden geïmplementeerd, verwijdert u de vertrouwde basissleutel. Ook voorzien van deze clients de nieuwe vertrouwde basissleutel. Zie voor meer informatie [Planning voor de vertrouwde basissleutel](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK). 

5.  Gebruik uw software voor het maken van installatiekopieën om de installatiekopie van de mastercomputer vast te leggen.  

6.  De installatiekopie implementeren op doelcomputers.  



##  <a name="BKMK_ClientWorkgroup"></a> Clients installeren op computers in werkgroepen  
 Configuration Manager ondersteunt clientinstallatie voor computers in werkgroepen. Installeer de client op werkgroepcomputers via de in [Handmatig Configuration Manager-clients installeren](#BKMK_Manual) beschreven methode.  

 Vereisten:  

-   De client moet handmatig worden geïnstalleerd op elke werkgroepcomputer. Tijdens de installatie moet de aangemelde gebruiker lokale beheerdersrechten hebben.  

-   Voor toegang tot bronnen in het domein van Configuration Manager site server, moet het netwerktoegangsaccount worden geconfigureerd voor de site. Dit account opgeven als een eigenschap softwaredistributie-onderdeel. Zie [Siteonderdelen voor System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md) voor meer informatie.  

 Beperkingen:  

-   Werkgroepclients kunnen geen beheerpunten localiseren vanaf Active Directory Domain Services en moeten in plaats daarvan DNS, WINS of een ander beheerpunt gebruiken.  

-   Globale roaming wordt niet ondersteund, omdat client Active Directory Domain Services niet kunnen bevragen voor site-informatie.  

-   Active Directory-detectiemethoden kunnen computers in werkgroepen niet detecteren.  

-   U kunt software niet implementeren voor gebruikers van computers in werkgroepen.  

-   U kunt de clientpushinstallatiemethode niet gebruiken om de client te installeren op werkgroepcomputers.  

-   Werkgroepclients kunnen Kerberos niet gebruiken voor verificatie en handmatige goedkeuring vereisen.  

-   Een werkgroep-client kan niet worden geconfigureerd als een distributiepunt. Configuration Manager vereist dat distributiepuntcomputers lid zijn van een domein.  

### <a name="install-the-client-on-workgroup-computers"></a>De client installeren op computers in werkgroepen  

Controleer de vereisten en volg de aanwijzingen in de sectie [handmatig installeren van Configuration Manager-clients](#BKMK_Manual).  

   Dit voorbeeld installeert de client voor intranet clientbeheer en geeft de sitecode en het DNS-achtervoegsel op om een beheerpunt te localiseren. `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=constoso.com`  

     

   Dit voorbeeld vereist dat de client zich op een netwerklocatie bevindt die is geconfigureerd in een grensgroep. Deze vereiste is voor automatische sitetoewijzing kan slagen. De opdracht bevat een terugvalstatuspunt op server FSPSERVER. Deze eigenschap kunt bijhouden clientimplementatie en problemen identificeren alle clientcommunicatie. 
   `CCMSetup.exe FSP=fspserver.constoso.com`  

      

##  <a name="BKMK_ClientInternet"></a> Het installeren van clients voor internet-gebaseerd clientbeheer  
 
> [!Note]
> Deze sectie niet van toepassing op clients met behulp van een [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway). Zie het installeren van clients op internet met behulp van een cloud management gateway [installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

Wanneer de Configuration Manager-site ondersteunt [internet-gebaseerd clientbeheer](/sccm/core/clients/manage/plan-internet-based-client-management) voor clients die soms op het intranet, en soms op het internet, hebt u twee opties wanneer u clients op het intranet installeert:  

-   U kunt opnemen dat de eigenschap Client.msi van CCMHOSTNAME =*&lt;internet FQDN-naam van de internet-gebaseerd beheerpunt bevindt\>*  wanneer u de client installeert, bijvoorbeeld door handmatige installatie of clientpush. Wanneer u deze methode gebruikt, moet u ook de client direct toewijzen aan de site en kunt u niet automatische sitetoewijzing gebruiken. De [handmatig installeren van Configuration Manager-clients](#BKMK_Manual) in dit onderwerp bevat een voorbeeld van deze configuratiemethode.  

-   U kunt de client voor clientbeheer op intranet, en vervolgens wijst u een internet-gebaseerd clientbeheer verwijzen naar de client installeren. Wijzig het beheerpunt met behulp van de clienteigenschappen van de Configuration Manager-in het Configuratiescherm of via een script. Wanneer u deze methode gebruikt, kunt u automatische clienttoewijzing gebruiken. Zie voor meer informatie de [clients voor clientbeheer op internet configureren na clientinstallatie](#BKMK_ConfigureIBCM_MP) in dit onderwerp.  

 Als u clients op internet installeren moet, kiest u een van de volgende ondersteunde methodes:  

-   Bieden een mechanisme voor deze clients om tijdelijk te verbinden met het intranet met een VPN. Installeer de client door een geschikte clientinstallatiemethode te gebruiken.  

-   Gebruik een installatiemethode die onafhankelijk is van Configuration Manager. Bijvoorbeeld, de clientinstallatiebronbestanden op uitwisselbare media die u naar gebruikers zenden kunt met instructies voor het installeren van het pakket. De clientinstallatiebronbestanden bevinden zich in de  *&lt;InstallationPath\>*\Client map op de Configuration Manager-site en -beheerpunten. Neem op de media ook een script op om handmatig te kopiëren via de clientmap en vanaf deze map, installeer de client door gebruik te maken van CCMSetup.exe en van alle geschikte CCMSetup-opdrachtregeleigenschappen.  

> [!NOTE]  
>  Configuration Manager biedt geen ondersteuning voor installatie van een client direct vanuit het internetgebaseerde beheerpunt of vanuit het internetgebaseerde software-updatepunt.  

 Clients die worden beheerd via het internet moeten communiceren met sitesystemen op internet. Zorg ervoor dat deze clients ook certificaten public key infrastructure (PKI) voordat u de client installeert. Deze certificaten onafhankelijk van Configuration Manager installeren. Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten](../../../core/plan-design/network/pki-certificate-requirements.md).  

### <a name="install-clients-on-the-internet-by-specifying-ccmsetup-command-line-properties"></a>Clients installeren op het internet door het opgeven van CCMSetup-opdrachtregeleigenschappen  

1.  Volg de aanwijzingen in de sectie [handmatig installeren van Configuration Manager-clients](#BKMK_Manual) en Neem altijd het volgende:  

    -   CCMSetup-opdrachtregeleigenschap **/source: ***&lt;lokaal pad naar de gekopieerde clientmap\>*  

    -   CCMSetup-opdrachtregel eigenschap **/UsePKICert**  

    -   Client.msi-eigenschap **CCMHOSTNAME = ***&lt;FQDN van beheerpunt op internet\>*  

    -   Client.msi-eigenschap **SMSSIGNCERT = ***&lt;lokaal pad naar het geëxporteerde handtekeningcertificaat van siteserver\>*  

    -   Client.msi-eigenschap **SMSSITECODE = ***&lt;sitecode van het beheerpunt op internet\>*  

    > [!NOTE]  
    >  Als de site meer dan een internet-gebaseerd beheerpunt bevindt heeft, maakt het niet uit welke-beheerpunt op internet u voor de CCMHOSTNAME-eigenschap opgeeft. Wanneer een Configuration Manager-client verbinding met de opgegeven internet-gebaseerd beheerpunt maakt, stuurt het beheerpunt de client een lijst met beschikbare internetgebaseerde beheerpunten in de site. De client selecteert willekeurig een in de lijst.  

2.  Indien u niet wilt dat de client de certificaatintrekkingslijst controleert (CRL), geef dan de CCMSetup-opdrachtregeleigenschap op **/NoCRLCheck**.  

3.  Als u een terugvalstatuspunt op internet worden gebruikt, geeft u de Client.msi-eigenschap **FSP = ***&lt;internet FQDN-naam van het internet gebaseerde terugvalstatuspunt\>*.  

4.  Als u de client voor alleen-internet clientbeheer installeert, geef de Client.msi-eigenschap **CCMALWAYSINF = 1**.  

5.  Controleer of u moet extra CCMSetup-opdrachtregeleigenschappen opgeven. U moet een certificaat selectiecriterium opgeven als de client meer dan één geldig PKI-certificaat heeft. Zie voor een lijst met beschikbare eigenschappen [over clientinstallatie-eigenschappen](../../../core/clients/deploy/about-client-installation-properties.md).  

   Voorbeeld:  
   `CCMSetup.exe /source: D:\Clients /UsePKICert CCMHOSTNAME=server1.contoso.com SMSSIGNCERT=siteserver.cer SMSSITECODE=ABC FSP=server2.contoso.com CCMALWAYSINF=1 CCMFIRSTCERT=1`    

   In dit voorbeeld installeert de client met de volgende problemen:
   - Bronbestanden gebruiken vanuit een map op het D-station
   - Een PKI-clientcertificaat gebruiken 
   - Selecteer het certificaat met de langste geldigheidsduur 
   - Alleen-Internet clientbeheer
   - De client op internet gebaseerde beheerpunt gebruiken met de naam SERVER1 toewijzen
   - Het terugvalstatuspunt op internet punt in het domein contoso.com toewijzen
   - De client toewijzen aan de ABC-site  

###  <a name="BKMK_ConfigureIBCM_MP"></a>Clients voor clientbeheer op internet configureren na clientinstallatie  
 Als u wilt toewijzen de internet-gebaseerd beheerpunt bevindt nadat de client is geïnstalleerd, een van deze procedures te gebruiken. De eerste vereist handmatige configuratie en geschikt is voor enkele clients. De tweede is meer geschikt is voor het configureren van veel clients.  

#### <a name="configure-clients-for-internet-based-client-management-after-client-installation-by-assigning-the-internet-based-management-point-in-configuration-manager-properties"></a>Clients voor clientbeheer op internet configureren na clientinstallatie door het toewijzen van de internet-gebaseerd beheerpunt bevindt in de eigenschappen van Configuration Manager  

1.  Navigeer naar **Configuration Manager** in het configuratiescherm van de clientcomputer en dubbelklik er vervolgens op om de eigenschappen ervan te openen.  

2.  Op de **Internet** tabblad, voert u de volledig gekwalificeerde domeinnaam van de internet-gebaseerd beheerpunt bevindt in de internet-FQDN in het tekstvak.  

    > [!NOTE]  
    >  Het tabblad **Internet** is enkel beschikbaar als de client een PKI-certificaat heeft.  

3.  Als de client verbinding maakt met internet via een proxyserver, voert u de proxy-instellingen.  

#### <a name="configure-clients-for-internet-based-client-management-after-client-installation-by-using-a-script"></a>Clients voor clientbeheer op internet configureren na clientinstallatie door een script  

1.  Open een teksteditor, zoals Kladblok.  

2.  Kopieer en het volgende voorbeeld van VBScript invoegen in het bestand. Vervang *mp.contoso.com* met het internet-FQDN-naam van uw internet-gebaseerd beheerpunt bevindt.  

    ```  
    on error resume next  

    ' Create variables.  
    Dim newInternetBasedManagementPointFQDN  
    Dim client  

    newInternetBasedManagementPointFQDN = "mp.contoso.com"  

    ' Create the client COM object.  
    Set client = CreateObject ("Microsoft.SMS.Client")  

    ' Set the internet-based management point FQDN by calling the SetCurrentManagementPoint method.  
    client.SetInternetManagementPointFQDN newInternetBasedManagementPointFQDN  

    ' Clear variables.  
    Set client = Nothing  
    Set internetBasedManagementPointFQDN = Nothing  

    ```  

    > [!NOTE]  
    >  Als er een opgegeven internetgebaseerde beheerpunt wissen zodat de client is niet geconfigureerd voor het gebruik van een internet-gebaseerd beheerpunt bevindt, verwijdert u de waarde binnen de aanhalingstekens zodat deze regel: `newInternetBasedManagementPointFQDN = ""`  

4.  Sla het bestand op met een VBS-extensie.  

5.  Gebruik cscript.exe het script uitvoeren op client-computers, met behulp van een van de volgende methoden:  

    -   Implementeer het bestand naar bestaande Configuration Manager-clients door gebruik te maken van een pakket en een programma.  

    -   Voer het bestand lokaal uit op bestaande Configuration Manager-clients door te dubbelklikken op het scriptbestand in Windows Explorer.  

 U moet wellicht opnieuw opstarten van de client om de wijzigingen van kracht te laten worden.  



##  <a name="BKMK_Provision"></a> Hoe eigenschappen van clientinstallatie inrichten (groep beleid en software-update gebaseerde clientinstallatie)  
 U kunt Windows groepsbeleid inrichten van computers met Configuration Manager clientinstallatie-eigenschappen. Deze eigenschappen worden opgeslagen in het register van de computer en worden gelezen wanneer de clientsoftware is geïnstalleerd. Deze procedure is niet normaal gesproken vereist, maar het kan nodig zijn voor sommige scenario's van clientinstallatie, zoals:  

-   Gebruikt u de instellingen voor Groepsbeleid of de software-update gebaseerde clientinstallatiemethoden. U dit nog niet hebt het Active Directory-schema uitgebreid voor Configuration Manager.  

-   U wilt de eigenschappen van clientinstallatie op specifieke computers overschrijven.  

> [!NOTE]  
>  Als de installatie-eigenschappen op de CCMSetup.exe opdrachtregel ingebracht worden, worden niet installatie-eigenschappen geleverd op computers gebruikt.  

 Een beheersjabloon voor Groepsbeleid ConfigMgrInstallation.adm genaamd, is geleverd op de installatiemedia van Configuration Manager. Deze sjabloon kan worden gebruikt voor het inrichten van clientcomputers met installatie-eigenschappen.   

### <a name="configure-and-assign-client-installation-properties-by-using-a-group-policy-object"></a>Clientinstallatie configureren en toewijzen installatie-eigenschappen met behulp van een Groepsbeleid-Object  

1.  Importeer de beheersjabloon ConfigMgrInstallation.adm in een nieuw of bestaand groepsbeleidsobject, met behulp van een editor zoals Windows groepsbeleidsobject-Editor. Het bestand kan worden gevonden in de map **TOOLS\ConfigMgrADMTemplates** op de installatiemedia van Configuration Manager.  

2.  Open de eigenschappen van de geïmporteerde instelling **Configureer instellingen clientimplementatie**.  

3.  Kies **ingeschakeld**.  

4.  Voer in het vakje **CCMSetup** de vereiste CCMSetup-opdrachtregeleigenschappen in. Zie voor een lijst van alle CCMSetup-opdrachtregel eigenschappen en voorbeelden van hun gebruik, [over clientinstallatie-eigenschappen](../../../core/clients/deploy/about-client-installation-properties.md).  

5.  Het groepsbeleidsobject aan de computers die u inrichten met Configuration Manager clientinstallatie-eigenschappen wilt toewijzen.  

Raadpleeg de Windows Server-documentatie voor informatie over Windows groepsbeleid.  



## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over de Configuration Manager-client installeert [clientinstallatiemethoden](../../../core/clients/deploy/plan/client-installation-methods.md).