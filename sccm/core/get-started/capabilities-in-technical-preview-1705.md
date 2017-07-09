---
title: Technische Preview 1705 | Microsoft Docs
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1705 voor System Center Configuration Manager.
ms.custom: na
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 00684289-d21a-45f8-b1e3-c5c787d73096
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4c46bfab9b40b29654f4e883817a5508ab25b74
ms.openlocfilehash: 1a38d25fbc26bd1f45c6fa2a0e931536af2d8b2f
ms.contentlocale: nl-nl
ms.lasthandoff: 06/28/2017

---
# <a name="capabilities-in-technical-preview-1705-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1705 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1705 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md) om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    

**Bekende problemen in deze Technical Preview:**
-   **Operations Manager-Suite-connector wordt niet bijgewerkt wanneer**. Wanneer u een van een eerdere versie van de Technical Preview waarop de OMS-connector die is geconfigureerd upgrade, wordt die connector wordt niet bijgewerkt en is niet meer beschikbaar in de console. Na de upgrade, moet u [gebruik de wizard Azure-Services](capabilities-in-technical-preview-1705.md#use-azure-services-wizard-to-configure-a-connection-to-oms) en opnieuw verbinding te maken met de OMS-werkruimte.
-   **Surface stuurprogramma's niet synchroniseren met succes**. Hoewel ondersteuning voor surface stuurprogramma's worden vermeld in **wat is er nieuw** in de Configuration Manager-console voor de technical preview deze functie nog werkt niet zoals verwacht.
-   **Kan het maken van Windows Update voor uitgestelde bedrijfsbeleid**. Hoewel de mogelijkheid voor het configureren van Windows Update voor bedrijven uitgestelde beleid wordt weergegeven in **wat is er nieuw** in de Configuration Manager-console voor de technical preview de wizard niet wordt geopend en u geen configureren van beleid.


<!--  Known Issues Template
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="update-reset-tool"></a>Hulpprogramma voor het bijwerken opnieuw instellen  
U kunt het hulpprogramma Configuration Manager-Update opnieuw instellen, **CMUpdateReset.exe**, oplossen van problemen wanneer updates in de console hebben problemen met het downloaden of repliceren. Dit hulpprogramma is opgenomen in de Technical Preview-versie 1705. U kunt vinden op de siteserver van de technical preview-site nadat u het voorbeeld in de ***\cd.latest\SMSSETUP\TOOLS*** map.

U kunt dit hulpprogramma gebruiken met Technical Preview-versie 1606 of hoger. Dit achterwaartse ondersteuning wordt verleend zodat het hulpprogramma kan worden gebruikt met een bereik van technical preview bijwerken scenario's en zonder te wachten tot de volgende technische preview beschikbaar wordt.

U kunt dit hulpprogramma kunt gebruiken wanneer een update in de console nog niet is geïnstalleerd en bevindt zich in een foutstatus. Een mislukte status betekenen dat het downloaden van de update wordt uitgevoerd, maar is vastgelopen en een te lange duurt mogelijk langer dan de historische verwachtingen voor uren pakketten bijwerken van vergelijkbare grootte. Het kan ook een fout in de update gerepliceerd naar onderliggende primaire sites zijn.  

Wanneer u het hulpprogramma uitvoert, wordt deze wordt uitgevoerd voor de update die u opgeeft. Standaard wordt het hulpprogramma is geïnstalleerd of gedownloade updates niet verwijderd.  

### <a name="prerequisites"></a>Vereisten
Het account waarmee u het hulpprogramma uitvoert vereist de volgende machtigingen:
-   **Lees** en **schrijven** machtigingen tot de sitedatabase van de centrale beheersite en elke primaire site in uw hiërarchie. Als u wilt deze machtigingen instelt, kunt u het gebruikersaccount toevoegen als lid van de **db_datawriter** en **db_datareader** [vaste databaserollen](/sql/relational-databases/security/authentication-access/database-level-roles#fixed-database-roles) op de Configuration Manager-database van elke site. Het hulpprogramma communiceert niet met secundaire sites.
-   **Lokale beheerder** op het hoogste niveau van uw hiërarchie.
-   **Lokale beheerder** op de computer die als host fungeert voor het serviceverbindingspunt wordt gehost.

U moet de GUID van het updatepakket dat u wilt instellen. De GUID ophalen:
-   Ga in de console naar **beheer** > **Updates en onderhoud** en klik vervolgens in het weergavevenster met de rechtermuisknop op de kop van een van de kolommen (zoals **status**), selecteer daarna **pakket-Guid**. Hiermee voegt u deze kolom worden weergegeven en de kolom ziet u de updatepakket-GUID.

> [!TIP]  
> Selecteer de rij voor het updatepakket dat u wilt instellen voor het kopiëren van de GUID en gebruikt u CTRL + C om te kopiëren die rij. Als u de gekopieerde selectie in een teksteditor plakken, kunt u alleen de GUID voor gebruik als een parameter in opdrachtregel vervolgens kopiëren wanneer u het hulpprogramma uitvoert.

### <a name="run-the-tool"></a>Het hulpprogramma uitvoeren    
Het hulpprogramma moet worden uitgevoerd op het hoogste niveau van de hiërarchie.

Wanneer u het hulpprogramma uitvoert, gebruikt u de opdrachtregelparameters om op te geven van de SQL Server op de bovenste site van de hiërarchie, de naam van de site-database en de GUID van het updatepakket dat u wilt instellen. Het hulpprogramma identificeert de extra servers die deze toegang moet hebben op basis van de status van updates.   

Als u het updatepakket is in een *na de download* status, het hulpprogramma niet clean up gemaakt van het pakket. U kunt het verwijderen van een update is gedownload met behulp van de parameter force verwijderen (Zie opdrachtregelparameters verderop in dit onderwerp) forceren als een optie.

Nadat het hulpprogramma wordt uitgevoerd:
-   Als een pakket is verwijderd, wordt de bovenste sites SMS Executive-service opnieuw starten en vervolgens controleren op updates te downloaden van het pakket opnieuw.
-   Als een pakket is niet verwijderd, hoeft u niet te doen als de update opnieuw te initialiseren en replicatie of de installatie opnieuw starten.

**Opdrachtregelparameters:**  

| Parameter        |Beschrijving                 |  
|------------------|----------------------------|  
|**-S &lt;FQDN-naam van de SQL Server van de bovenste site >** | *Vereist* <br> U moet de FQDN van de SQL Server die als host fungeert voor de sitedatabase voor de bovenste site van uw hiërarchie opgeven.    |  
| **-D &lt;databasenaam >**                        | *Vereist* <br> U moet de naam van de database van de bovenste opgeven.  |  
| **-P &lt;pakket-GUID >**                         | *Vereist* <br> De GUID van het updatepakket dat u wilt instellen, moet u opgeven.   |  
| **-Ik &lt;SQL Server-instantienaam >**             | *Optioneel* <br> Gebruik deze om de instantie van SQL Server die als host fungeert voor de sitedatabase te identificeren. |
| **-FDELETE**                              | *Optioneel* <br> Gebruik deze geforceerd wordt verwijderd van een updatepakket zijn gedownload. |  
 **Voorbeelden:**  
 In een typisch scenario dat u wilt opnieuw instellen van een update die downloaden problemen heeft. De FQDN van uw SQL-Servers is *server1.Fabrikam.com zijn*, wordt de site datbase *CM_XYZ*, en het pakket-GUID is *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  U hebt uitgevoerd: ***CMUpdateReset.exe -S server1.Fabrikam.com zijn -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***

 In een scenario met meer extreme die u wilt verwijderen van problematisch updatepakket forceren. De FQDN van uw SQL-Servers is *server1.Fabrikam.com zijn*, wordt de site datbase *CM_XYZ*, en het pakket-GUID is *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*.  U hebt uitgevoerd: ***CMUpdateReset.exe - FDELETE -S server1.Fabrikam.com zijn -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***

### <a name="test-the-tool-with-the-technical-preview"></a>Testen van het hulpprogramma met de Technical Preview  
U kunt dit hulpprogramma gebruiken met Technical Preview-versie 1606 of hoger. Dit achterwaartse ondersteuning wordt geboden zodat het hulpprogramma kan worden gebruikt met een groot aantal scenario's de update van technical preview zonder te wachten totdat de volgende technische preview-versie beschikbaar is.

Het hulpprogramma uitvoeren op een updatepakket voor een technical preview vóór de update voor het voltooien van de controle van vereisten. Een status controleren van vereisten is voltooid wordt geïdentificeerd door een van de volgende statussen voor het pakket in **beheer** > **Updates en onderhoud**:  
-   **Vereiste controle geslaagd**
-   **Vereistencontrole voltooid met waarschuwingen**
-   **Controle van vereisten is mislukt**


## <a name="high-dpi-console-support"></a>Hoge DPI-ondersteuning

Met deze release, moeten problemen met hoe de Configuration Manager-console wordt geschaald en geeft verschillende onderdelen van de gebruikersinterface weergegeven op hoge DPI-apparaten (zoals een boek Surface) worden hersteld.


## <a name="peer-cache-improvements"></a>Verbeteringen voor peer-Cache
Vanaf deze technische preview van Peer-Cache [het netwerktoegangsaccount niet langer gebruikt](/sccm/core/plan-design/hierarchy/client-peer-cache) om downloadaanvragen van peers te verifiëren.


## <a name="improvements-for-sql-server-always-on-availability-groups"></a>Verbeteringen voor SQL Server altijd op beschikbaarheidsgroepen  
Met deze release kunt u nu asynchrone doorvoer replica's in de SQL Server Always On availability groepen die u met Configuration Manager gebruikt gebruiken.  Dit betekent dat u kunt extra replica's toevoegen aan uw beschikbaarheidsgroepen wilt gebruiken als externe (extern) back-ups en gebruik ze in een noodherstelscenario.  

-   Configuration Manager ondersteunt de synchrone replica herstellen met behulp van de replica met asynchrone doorvoer.  Zie [opties voor herstel van site](/sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption) in het onderwerp back-up en herstel voor meer informatie over om dit te bereiken.

-   Deze versie biedt geen ondersteuning voor failover voor het gebruik van de replica met asynchrone doorvoer als uw sitedatabase.
> [!CAUTION]  
> Omdat Configuration Manager wordt de status van de replica met asynchrone doorvoer om te bevestigen dat het huidige, is niet gevalideerd en [standaard deze replica kan niet synchroon](https://msdn.microsoft.com/library/ff877884(SQL.120).aspx(d=robot)#Availability%20Modes), het gebruik van een replica met asynchrone doorvoer als de sitedatabase kunt risico voor de integriteit van uw site en -gegevens.  

-   U kunt hetzelfde aantal en type van replica's in een beschikbaarheidsgroep als ondersteund door de versie van SQL Server die u gebruikt.   (Eerdere ondersteuning is beperkt tot twee synchrone doorvoer replica's.)

### <a name="configure-an-asynchronous-commit-replica"></a>Een replica met asynchrone doorvoer configureren
Toevoegen van een asynchrone replica aan een [beschikbaarheidsgroep die u met Configuration Manager gebruikt](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database), hoeft u niet de configuratiescripts vereist voor het configureren van een synchrone replica worden uitgevoerd. (Dit is omdat er is geen ondersteuning die asynchrone replica gebruiken als de sitedatabase). Zie [de documentatie van SQL Server](https://msdn.microsoft.com/library/hh213247(v=sql.120).aspx(d=robot)) voor meer informatie over de secundaire replica's toevoegen aan beschikbaarheidsgroepen.

### <a name="use-the-asynchronous-replica-to-recover-your-site"></a>De asynchrone replica gebruiken om uw site te herstellen
Voordat u een asynchrone replica gebruiken voor het herstellen van uw sitedatabase, moet u de actieve primaire site om te voorkomen dat extra schrijfbewerkingen naar de sitedatabase te stoppen. Na het stoppen van de site, kunt u de replica van een asynchrone in plaats van met behulp van een [handmatig herstelde database](/sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption).

Als u wilt stoppen van de site, kunt u de [tool hiërarchie-onderhoud](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe) belangrijke services stoppen op de siteserver. De opdrachtregel gebruiken: **Preinst.exe stopsite**   

Stoppen van de site is gelijk aan het stoppen van de Site Component Manager-service (sitecomp) gevolgd door de SMS Executive-service op de siteserver.

> [!TIP]  
> Als u een primaire replica van de passieve (geïntroduceerd in deze Technical Preview als [rol hoge beschikbaarheid Site](#site-server-role-high-availability)), u niet wilt stoppen van de passieve replica. Alleen de actieve primaire site moet worden gestopt.



## <a name="improved-user-notifications-for-office-365-updates"></a>Verbeterde berichten van de gebruiker voor Office 365-updates
Voor het benutten van de gebruikerservaring Office Klik-en-klaar wanneer een client wordt geïnstalleerd voor een update voor Office 365 zijn verbeteringen aangebracht. Dit omvat pop- en in-app-meldingen en een aftelvenster weergegeven-ervaring. Vóór deze versie wanneer een update voor Office 365 is verzonden naar een client zijn Office-toepassingen die geopend zijn automatisch gesloten zonder waarschuwing. Na deze update wordt Office-toepassingen niet meer worden onverwachts afgesloten.

### <a name="prerequisites"></a>Vereisten
Deze update geldt voor Office 365 ProPlus-clients.

### <a name="known-issues"></a>Bekende problemen
Wanneer een client een Office 365 toewijzing van de update voor de eerste keer en de update een deadline die in het verleden zijn gepland evalueert heeft, onmiddellijk gepland of gepland binnen 30 minuten, is de ervaring van de Office 365-gebruiker kan zijn inconsistent. Bijvoorbeeld, de client mogelijk een dialoogvenster voor het aftellen van 30 minuten voor de update wordt weergegeven, maar het werkelijke afdwingen voor het einde van het aftellen kan worden gestart. Om te voorkomen dat dit gedrag, het volgende overwegen:
- Implementeer de update voor Office 365 met een deadline die gedurende meer dan 60 minuten voor de huidige tijd is gepland.
- Een onderhoudsvenster configureert tijdens buiten kantooruren voor de verzameling of een respijtperiode afdwingen configureren op de implementatie.

### <a name="try-it-out"></a>Probeer het nu!
Voer de volgende taken en klikt u vervolgens Stuur ons **Feedback** van de **Start** tabblad van het lint te laten weten hoe het is gegaan:
- Implementeren naar een client een Office 365-update met een deadline instellen op een tijdstip minstens 60 minuten voor de huidige tijd. Houd rekening met de nieuwe functies op de client.


## <a name="configure-and-deploy-windows-defender-application-guard-policies"></a>Windows Defender toepassing Guard beleid configureren en implementeren

[Windows Defender toepassing Guard](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97) is een nieuwe Windows-functie die voorkomen dat uw gebruikers via niet-vertrouwde websites in een beveiligde geïsoleerde container die is niet toegankelijk voor andere onderdelen van het besturingssysteem. In deze technical preview ondersteuning voor het configureren van deze functie met Configuration Manager-instellingen voor naleving die u configureert en vervolgens implementeert op een verzameling toegevoegd.
Deze functie worden uitgebracht Preview-versie voor de 64-bits versie van de Windows 10-Creator Update (codename: RS2). Als u wilt testen van dit onderdeel nu moet u een preview-versie van deze update.


### <a name="before-you-start"></a>Voordat u begint

Voor het maken en implementeren van beleid voor Windows Defender toepassing Guard, moeten de Windows 10-apparaten waarop u het beleid implementeert worden geconfigureerd met een beleid voor het isoleren van netwerken. Zie de blog post waarnaar wordt verwezen later voor meer informatie.
Deze functie werkt alleen met huidige Insider voor Windows 10-builds. Als u wilt testen, moeten uw clients worden uitgevoerd een recente Windows 10 Insider niet maken.

### <a name="try-it-out"></a>Probeer het nu!

Zorg ervoor dat u het blogbericht om de basisbeginselen over Windows Defender toepassing Guard hebt gelezen.

Een beleid maken en om te bladeren, de beschikbare instellingen:

1.  Kies in de Configuration Manager-console **activa en naleving**.
2.  In de **activa en naleving** werkruimte, kiest u **overzicht** > **Endpoint Protection** > **Windows Defender toepassing Guard**.
3.  In de **Start** tabblad, in de **maken** groep, klikt u op **maken Windows Defender Guard toepassingsbeleid**.
4.  Met behulp van de blogbericht als uitgangspunt, kunt u bladeren en configureer de beschikbare instellingen voor de functie uitproberen.
5.  Wanneer u klaar bent, voltooi de wizard en implementeer het beleid voor een of meer Windows 10-apparaten.

### <a name="further-reading"></a>Lees hier meer over

Voor meer informatie over Windows Defender toepassing Guard, Zie [dit blogbericht]( https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97).
Zie ook voor meer informatie over Windows Defender toepassing Guard zelfstandige modus, [dit blogbericht](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).




## <a name="new-capabilities-for-azure-ad-and-cloud-management"></a>Nieuwe mogelijkheden voor Azure AD en in de cloud management

In deze release kunt u cloudservices voor het gebruik van Azure AD ter ondersteuning van de volgende scenario:

- Handmatig installeren van Configuration Manager-client van het internet en deze toewijzen aan een Configuration Manager-site.
- Intune gebruiken voor het implementeren van Configuration Manager-client op apparaten op internet.

### <a name="advantages"></a>Voordelen

Met cloudservices en Azure AD verwijdert de behoefte om te gebruiken van certificaten voor clientverificatie.

U kunt Azure AD-gebruikers in uw site moet worden gebruikt in verzamelingen en andere Configuration Manager-bewerkingen detecteren.

### <a name="before-you-start"></a>Voordat u begint

- U hebt een Azure AD-tenant.
- Uw apparaten moeten Windows 10 wordt uitgevoerd en moet Azure AD zijn toegevoegd.  Clients kunnen ook worden bovendien naar Azure AD die lid zijn verbonden met het domein).
- Naast de [bestaande vereisten](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) voor het beheer van sitesysteemrol, moet u ook controleren of **ASP.NET 4.5** (en andere opties die met deze automatisch geselecteerd) zijn ingeschakeld op de computer die als host fungeert voor deze sitesysteemrol.
- Microsoft Intune te gebruiken voor het implementeren van Configuration Manager-client:
    - U moet een werkende Intune-tenant (Configuration Manager en Intune komen niet moet worden verbonden) hebben.
    - In Intune, hebt u gemaakt en een app met de Configuration Manager-client wordt geïmplementeerd. Zie voor meer informatie over hoe u dit doet, het installeren van clients op Windows Intune MDM-beheerde apparaten.
- Configuration Manager gebruiken om de client te implementeren:
    - Ten minste één beheerpunt moet worden geconfigureerd voor HTTPS-modus.
    - U moet een Cloud Management Gateway instellen.


### <a name="set-up-the-cloud-management-gateway"></a>De Cloudgateway Management instellen

De Cloud Management Gateway instellen, kunnen clients toegang tot uw Configuration Manager-site van het internet zonder gebruik van certificaten.

Hier vindt u help-informatie over hoe u dit doet in de volgende onderwerpen:

- [Plannen in Configuration Manager management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway).
- [Instellen van de cloud management gateway voor Configuration Manager](/sccm/core/clients/manage/setup-cloud-management-gateway).
- [Monitor management cloudgateway in Configuration Manager](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway).

### <a name="set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>De app Azure-Services in Configuration Manager-Services voor Cloud instellen

Dit uw Configuration Manager-site verbindt met Azure AD en is een vereiste voor alle bewerkingen in deze sectie. U doet dit als volgt:

1.  In de **beheer** werkruimte van de Configuration Manager-console, vouw **Cloudservices**, en klik vervolgens op **Azure Services**.
2.  Op de **Start** tabblad, in de **Azure Services** groep, klikt u op **Azure-Services configureren**.
3.  Op de **Azure Services** pagina van de Azure-Services Wizard **Cloudbeheer** wilt toestaan dat clients verifiëren met de hiërarchie met gebruik van Azure AD.
4.  Op de **algemene** pagina van de wizard, geeft u een naam en een beschrijving voor uw Azure-service.
5.  Op de **App** pagina van de wizard, selecteert u uw Azure-omgeving in de lijst en klik op **Bladeren** selecteren van de server en client-apps die worden gebruikt voor het configureren van de Azure-service:
    - In de **App Server** venster, selecteer de server-app die u wilt gebruiken en klik vervolgens op **OK**. Server-apps zijn de Azure-web-apps die de configuraties voor uw Azure-account, inclusief uw Tenant-ID, Client-ID en een geheime sleutel voor clients bevatten. Als u een beschikbare server-app niet hebt, gebruikt u een van de volgende:
        - **Maak**: Klik op om een nieuwe server app **maken**. Geef een beschrijvende naam voor de app en de tenant. Vervolgens, nadat u aanmelden bij Azure, Configuration Manager maakt de web-app in Azure voor u, met inbegrip van de Client-ID en een geheime sleutel voor gebruik met de web-app. U kunt later uit de Azure-portal bekijken.
        - **Importeren**: Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en het tenantnetwerk en geef vervolgens de Tenant-ID, Client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u de gegevens controleren, klikt u op **OK** om door te gaan. Deze opton is momenteel niet beschikbaar in deze technical preview.
    - Herhaal hetzelfde proces voor de client-app.

  U moet geven de *mapgegevens lezen* machtiging van toepassing wanneer u een toepassing importeren, gebruikt de juiste machtigingen instellen in de portal. Als u gebruik maken van de toepassing de machtigingen automatisch worden gemaakt met de toepassing, maar u nog moet toestemming geven tot de toepassing in de Azure-portal.
6.  Op de **detectie** pagina van de wizard eventueel **inschakelen Azure Active Directory-Gebruikersdetectie**, en klik vervolgens op **instellingen**.
In de **Discovery-instellingen van Azure AD-gebruiker** dialoogvenster Configureer een planning voor wanneer detectie wordt uitgevoerd. U kunt ook detectie van verschillen die controleert op nieuwe of gewijzigd accounts in Azure AD inschakelen.
7.  Voltooi de wizard.

Op dit moment hebt u uw Configuration Manager-site naar Azure AD verbonden.


### <a name="install-the-cm-client-from-the-internet"></a>De CM-client installeren vanaf het Internet

Voordat u begint, zorg ervoor dat de bronbestanden van de client-installatie worden lokaal opgeslagen op het apparaat waarnaar de client te installeren.
Gebruik vervolgens de instructies in [clients implementeren op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-clients-manually) met de volgende opdrachtregel voor installatie (de waarden in het voorbeeld vervangen door uw eigen waarden):

**ccmsetup.exe usepkicert/nocrlcheck /Source:C:\CLIENT CCMHOSTNAME=SCCMPROXYCONTOSO.CLOUDAPP.NET/CCM_Proxy_ServerAuth/72457598037527932 SMSSiteCode = HEC AADTENANTID = 780433B5-E05E-4B7D-BFD1-E8013911E543 AADTENANTNAME = contoso AADCLIENTAPPID =<GUID> AADRESOURCEURI https://contososerver =**

- **/ NoCrlCheck**: Als uw management verwijzen of cloud management gateway maakt gebruik van een niet-openbaar certificaat, en vervolgens de client mogelijk niet de locatie van de CRL te bereiken.
- **/ Source**: Lokale map:   Locatie van de clientinstallatiebestanden.
- **CCMHOSTNAME**: De naam van uw Internet-beheerpunt. U kunt dit vinden door te voeren **gwmi - naamruimte naamruimte-klasse SMS_ActiveMPCandidate** vanaf een opdrachtprompt op een beheerde client.
- **SMSMP**: De naam van uw beheerpunt lookup: dit kan zijn op uw intranet.
- **SMSSiteCode**: De sitecode van de Configuration Manager-site.
- **AADTENANTID**, **AADTENANTNAME**: De ID en de naam van de Azure AD-tenant gekoppeld aan Configuration Manager. U vindt dit door dsregcmd.exe/status uitgevoerd vanaf een opdrachtprompt op een Azure AD toegevoegd apparaat.
- **AADCLIENTAPPID**: De Azure AD client app-ID. Zie voor meer informatie over het zoeken naar dit [portal gebruik maken van een Azure Active Directory-toepassing en service-principal die toegang bronnen tot](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key).
- **AADResourceUri**: De id-URI van de app vrijgegeven Azure AD-server.

## <a name="use-azure-services-wizard-to-configure-a-connection-to-oms"></a>Wizard Azure-Services gebruiken een verbinding met OMS configureren
Vanaf de 1705 technical preview-versie is die u gebruikt de **Wizard Azure-Services** Configureer de verbinding van Configuration Manager naar de cloudservice Operations Management Suite (OMS). De wizard vervangt de vorige werkstromen voor het configureren van deze verbinding.

-   De wizard wordt gebruikt voor het configureren van cloudservices voor Configuration Manager, zoals OMS-, Windows Store voor bedrijven (WSfB) en Azure Active Directory (Azure AD).  

-   Configuration Manager maakt verbinding met OMS voor functies, zoals [logboekanalyse](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), of [gereedheid voor Upgrade](/sccm/core/clients/manage/upgrade/upgrade-analytics).

### <a name="prerequisites-for-the-oms-connector"></a>Vereisten voor de OMS-Connector
Vereisten voor het configureren van een verbinding met OMS is ongewijzigd ten opzichte van die [beschreven voor de huidige vertakking versie 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#prerequisites). Deze informatie wordt hier herhaald:  

-   Configuration Manager-machtiging verlenen aan OMS.

-   De OMS-connector moet worden geïnstalleerd op de computer die als host fungeert voor een [serviceaansluitpunt](/sccm/core/servers/deploy/configure/about-the-service-connection-point) die zich in [onlinemodus](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

-   Voor OMS op het service connection point samen met de OMS-connector is geïnstalleerd, moet u Microsoft Monitoring Agent installeren. De Agent en de OMS-connector moeten worden geconfigureerd voor het gebruik van dezelfde **OMS-werkruimte**. Zie het installeren van de agent [downloaden en installeren van de agent](/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) in de OMS-documentatie.
-   Nadat u de connector en de agent hebt geïnstalleerd, moet u OMS voor het gebruik van Configuration Manager-gegevens configureren. Om dit te doen in de OMS-Portal u [Import Configuration Manager-verzamelingen](/azure/log-analytics/log-analytics-sccm#import-collections).

### <a name="use-the-azure-services-wizard-to-configure-the-connection-to-oms"></a>Gebruik de Wizard Azure-Services de verbinding met OMS configureren

1.  Ga in de console naar **beheer** > **overzicht** > **Cloudservices** > **Azure Services**, en kies vervolgens **Azure-Services configureren** van de **Start** tabblad van het lint, om te starten de **Wizard Azure-Services**.

2.  Op de **Azure Services** pagina, selecteert u de bewerking Management Suite-cloudservice. Geef een beschrijvende naam voor de **Azure servicenaam** en een optionele beschrijving en klik vervolgens op **volgende**.

3.  Op de **App** pagina, geeft u uw Azure-omgeving (de technical preview ondersteunt alleen de openbare Cloud). Klik vervolgens op **Bladeren** om de Server App-venster te openen.

4.  Selecteer een web-app:

    -   **Importeren**: Met een web-app die al in uw Azure-abonnement bestaat, klikt u op **importeren**. Geef een beschrijvende naam voor de app en het tenantnetwerk en geef vervolgens de Tenant-ID, Client-ID en de geheime sleutel voor de Azure-web-app die u wilt dat Configuration Manager te gebruiken. Nadat u **controleren** de gegevens, klikt u op **OK** om door te gaan.   

    > [!NOTE]   
    > Wanneer u OMS met deze preview configureert, OMS biedt alleen ondersteuning voor de *importeren* functie voor een web-app. Maken van een nieuwe web-app wordt niet ondersteund. U kunt een bestaande app op dezelfde manier kan niet hergebruiken voor OMS.

5.  Als u bereikt de procedures geslaagd, klikt u vervolgens de informatie op de **OMS verbindingsconfiguratie** scherm automatisch wordt weergegeven op deze pagina. Informatie over de verbindingsinstellingen moet worden weergegeven voor uw **Azure-abonnement**, **Azure-resourcegroep**, en **Operations Management Suite-werkruimte**.

6.  De wizard maakt verbinding met de OMS-service met behulp van de informatie die u hebt ingevoerd. Selecteer de apparaatverzamelingen die u wilt synchroniseren met OMS en klik vervolgens op **toevoegen**.

7.  Controleer de verbindingsinstellingen op de **samenvatting** scherm en selecteer vervolgens **volgende**. De **voortgang** scherm toont de verbindingsstatus en vervolgens moet **Complete**.

8.  Nadat de wizard is voltooid, ziet u de Configuration Manager-console dat u hebt geconfigureerd **bewerking Management Suite** als een **Cloud Service Type**.

