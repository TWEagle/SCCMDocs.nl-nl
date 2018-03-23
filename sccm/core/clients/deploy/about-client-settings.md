---
title: Clientinstellingen
titleSuffix: Configuration Manager
description: Meer informatie over de standaard- en aangepaste instellingen voor het beheren van client-gedrag
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 42b9364fc88acc3f403db8d2ca9243a117fd78bf
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>Clientinstellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheert alle clientinstellingen in de Configuration Manager-console van de **clientinstellingen** knooppunt in de **beheer** werkruimte. Configuration Manager wordt geleverd met een aantal standaardinstellingen. Wanneer u de standaardclientinstellingen wijzigt, worden deze instellingen worden toegepast op alle clients in de hiërarchie. U kunt ook aangepaste clientinstellingen die de standaardclientinstellingen overschrijven wanneer u deze aan verzamelingen toewijzen configureren. Zie voor meer informatie [het configureren van clientinstellingen](../../../core/clients/deploy/configure-client-settings.md).

De volgende secties worden de instellingen en opties gedetailleerder beschreven.  
 

## <a name="background-intelligent-transfer-service-bits"></a>Background Intelligent Transfer Service (BITS)  

### <a name="limit-the-maximum-network-bandwidth-for-bits-background-transfers"></a>De maximale netwerkbandbreedte voor BITS overdrachten op de achtergrond beperken
Wanneer deze optie is **Ja**, clients gebruiken de BITS-bandbreedtebeperking. Als u wilt de overige instellingen in deze groep configureert, moet u deze instelling inschakelen. 

### <a name="throttling-window-start-time"></a>Begintijd beperkingsvenster
Geef de lokale begintijd voor de BITS-beperkingsvenster.  

### <a name="throttling-window-end-time"></a>Eindtijd beperkingsvenster
Geef de lokale eindtijd voor de BITS-beperkingsvenster. Als de eindtijd gelijk is aan de **begintijd Beperkingsvenster**, BITS-beperking altijd ingeschakeld.  

### <a name="maximum-transfer-rate-during-throttling-window-kbps"></a>Maximale overdrachtssnelheid tijdens het beperkingsvenster (Kbps)
Geef de maximale overdrachtssnelheid die clients tijdens de periode gebruiken kunnen.  

### <a name="allow-bits-downloads-outside-the-throttling-window"></a>BITS-downloads buiten beperkingsvenster toestaan
Toestaan dat clients afzonderlijke BITS-instellingen buiten het opgegeven venster gebruiken.  

### <a name="maximum-transfer-rate-outside-the-throttling-window-kbps"></a>Maximale overdrachtssnelheid buiten het beperkingsvenster (Kbps)
Geef de maximale overdrachtssnelheid die clients buiten de BITS gebruiken kunnen-beperkingsvenster.  



## <a name="client-cache-settings"></a>Clientcache-instellingen

### <a name="configure-branchcache"></a>BranchCache configureren
Instellen van de clientcomputer voor [Windows BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). Stel wilt toestaan BranchCache opslaan in cache op de client **BranchCache inschakelen** naar **Ja**.

- **BranchCache inschakelen** </br>
    Hiermee schakelt BranchCache op clientcomputers.

- **Cachegrootte maximale BranchCache (percentage van de schijf)** </br>
    Het percentage van de schijf waardoor BranchCache te gebruiken. 

### <a name="configure-client-cache-size"></a>Clientcachegrootte configureren
De Configuration Manager-clientcache op Windows-computers opslaat tijdelijke bestanden gebruikt voor het installeren van toepassingen en programma's. Als deze optie is ingesteld op **Nee**, de standaardgrootte is 5.120 MB.

Als u ervoor kiest **Ja**, geef vervolgens:
- **Maximale cachegrootte (MB)**
- **Maximumcachegrootte (percentage van de schijf)** </br>
Hiermee breidt u de client-cachegrootte tot de maximale grootte in megabytes (MB) of het percentage van de schijf, afhankelijk van wat is. 

### <a name="enable-configuration-manager-client-in-full-os-to-share-content"></a>Inschakelen van Configuration Manager-client in volledige OS in staat om inhoud te delen
Hiermee [peer-cache](/sccm/core/plan-design/hierarchy/client-peer-cache) voor Configuration Manager-clients. Kies **Ja**, en geef vervolgens de poort waarmee de client communiceert met de peercomputer. 
- **Poort voor oorspronkelijke netwerk-broadcast** (standaard 8004)
- **Poort voor downloaden van inhoud van peer** (8003 standaard) </br>
Windows Firewall-regels zodat dit verkeer wordt automatisch geconfigureerd door Configuration Manager. Als u een andere firewall gebruikt, moet u regels voor dit verkeer handmatig configureren.




## <a name="client-policy"></a>Beleid voor client  

### <a name="client-policy-polling-interval-minutes"></a>Pollinginterval voor clientbeleid (minuten)

Hiermee geeft u op hoe vaak de volgende Configuration Manager-clients clientbeleid downloaden:
-   Windows-computers (bijvoorbeeld desktops, servers, laptops)  
-   Mobiele apparaten die Configuration Manager schrijft  
-   Mac-computers  
-   Computers met Linux of UNIX  

### <a name="enable-user-policy-on-clients"></a>Gebruikersbeleid op clients inschakelen

Als u deze optie instelt op **Ja**, en gebruik [gebruikersdetectie](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), ontvangt van clients op de toepassingen en programma's die zijn gericht op de gebruiker is aangemeld.  

De Application Catalog ontvangt de lijst met beschikbare software voor gebruikers van de siteserver. Deze instelling hoeft dus niet te worden **Ja** voor gebruikers wilt weergeven en aanvragen van toepassingen uit de Application Catalog. Als deze instelling is **Nee**, de volgende problemen werken niet als gebruikers de Application Catalog gebruiken:  

-   Gebruikers kunnen de toepassingen in de Application Catalog niet installeren.  

-   Gebruikers zien niet meldingen over hun goedkeuringsaanvragen voor toepassingen. In plaats daarvan moeten ze de Application Catalog vernieuwen en de goedkeuringsstatus controleren.  

-   Gebruikers ontvangen geen revisies en updates voor toepassingen die worden gepubliceerd naar de Application Catalog. Gebruikers zien wijzigingen aan de toepassingsinformatie in de Application Catalog.  

-   Als u een toepassingsimplementatie verwijdert nadat de client de toepassing uit de Application Catalog installeert, blijven clients om te controleren dat de toepassing wordt geïnstalleerd voor maximaal twee dagen.  

Bovendien, als deze instelling is **Nee**, ontvangen gebruikers geen vereiste toepassingen die u voor gebruikers implementeert. Gebruikers ook ontvangen geen andere beheertaken in gebruikersbeleid.  

Deze instelling geldt voor gebruikers wanneer hun computer op het intranet of internet is. Dit moet **Ja** als u ook wilt inschakelen gebruikersbeleid op het internet.  

### <a name="enable-user-policy-requests-from-internet-clients"></a>Gebruikersbeleidsaanvragen van internetclients toestaan

Stel dit in op **Ja** voor gebruikers ontvangen het gebruikersbeleid op internet gebaseerde computers. De volgende vereisten ook van toepassing:  

-   De client en de site zijn geconfigureerd voor [internet-gebaseerd clientbeheer](/sccm/core/clients/manage/plan-internet-based-client-management) of een [management cloudgateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).  

-   De **gebruikersbeleid op clients inschakelen** instelling is **Ja**.  

-   De internet-gebaseerd beheerpunt bevindt verifieert de gebruiker met behulp van Windows-verificatie (Kerberos of NTLM). Zie voor meer informatie [overwegingen voor clientcommunicatie via internet](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

-   Vanaf versie 1710, verifieert de cloudgateway management de gebruiker met behulp van Azure Active Directory. Zie voor meer informatie [gebruikers beschikbare toepassingen op Azure AD-die lid zijn van apparaten implementeren](\sccm\apps\deploy-use\deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices).  

Als u deze optie instelt op **Nee**, of een van de vorige vereisten niet wordt voldaan, wordt een computer op het internet ontvangt alleen het computerbeleid. In dit scenario nog gebruikers kunnen zien, aanvragen en installeren van toepassingen vanaf een internet-gebaseerd Application Catalog. Als deze instelling is **Nee**, maar **gebruikersbeleid op clients inschakelen** is **Ja**, gebruikers doen geen gebruikersbeleid ontvangen totdat de computer is verbonden met het intranet.  

> [!NOTE]  
>  Voor internet-gebaseerd clientbeheer vereisen goedkeuringsaanvragen voor toepassingen van gebruikers geen gebruikersbeleid of gebruikersverificatie. De cloud management gateway biedt geen ondersteuning voor goedkeuringsaanvragen voor toepassingen.   



## <a name="cloud-services"></a>Cloudservices

### <a name="allow-access-to-cloud-distribution-point"></a>Toegang tot clouddistributiepunt toestaan
Stel dit in op **Ja** voor clients om inhoud te verkrijgen van een cloud-distributiepunt. Deze instelling vereist niet dat het apparaat niet op basis van het internet.

### <a name="automatically-register-new-windows-10-domain-joined-devices-with-azure-active-directory"></a>Nieuwe Windows 10-apparaten die lid van domein automatisch wordt geregistreerd bij Azure Active Directory 
Wanneer u Azure Active Directory voor de ondersteuning van hybride join configureert, configureert Configuration Manager Windows 10-apparaten voor deze functionaliteit. Zie voor meer informatie [hoe het configureren van hybride Azure Active Directory die lid zijn van apparaten](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup).

### <a name="enable-clients-to-use-a-cloud-management-gateway"></a>Clients gebruiken een cloudgateway management inschakelen
Standaard gebruiken alle clients voor internet roaming beschikbaar [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway). Een voorbeeld van wanneer deze instelling en **Nee** is aan het gebruik van het bereik van de service, zoals tijdens een proefproject of om kosten te besparen.



##  <a name="compliance-settings"></a>Instellingen voor naleving  

### <a name="enable-compliance-evaluation-on-clients"></a>Compatibiliteitsevaluatie op clients
Stel dit in op **Ja** voor het configureren van de andere instellingen in deze groep.
 
### <a name="schedule-compliance-evaluation"></a>Compatibiliteitsevaluatie plannen
Selecteer **planning** het standaardschema voor de configuratie van basislijn om implementaties te maken. Deze waarde kan worden geconfigureerd voor elke basislijn in de **Configuratiebasislijn implementeren** in het dialoogvenster.  

### <a name="enable-user-data-and-profiles"></a>Gebruikersgegevens en -profielen inschakelen
Kies **Ja** als u wilt implementeren [gebruikersgegevens en -profielen](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) configuratie-items.



## <a name="computer-agent"></a>Computeragent  

### <a name="user-notifications-for-required-deployments"></a>Meldingen voor gebruikers voor vereiste implementaties

Zie voor meer informatie over de volgende drie instellingen [meldingen voor gebruikers voor vereiste implementaties](/sccm/apps/deploy-use/deploy-applications#user-notifications-for-required-deployments):

-   **Implementatiedeadline langer dan 24 uur, gebruiker herinneren elke (uur)**
-   **Implementatie deadline van minder dan 24 uur, gebruiker herinneren elke (uur)** 
-   **Implementatie deadline van minder dan 1 uur, gebruiker herinneren elke (minuten)** 

### <a name="default-application-catalog-website-point"></a>Standaard Application Catalog-websitepunt

Configuration Manager gebruikt deze instelling om gebruikers verbinding met de Toepassingscatalogus vanuit Software Center. Selecteer **Website instellen** om op te geven van een server die als host fungeert voor de Application Catalog-websitepunt. Voert u de NetBIOS-naam of FQDN, automatische detectie of geef een URL voor aangepaste implementaties. In de meeste gevallen is automatische detectie de beste keuze, omdat het de volgende voordelen biedt:  

-   Als de site een Application Catalog-websitepunt heeft, vervolgens clients krijgen automatisch een Application Catalog-websitepunt van hun site.  

-   De client geeft de voorkeur aan HTTPS-functionaliteit Application Catalog-websitepunten op het intranet via HTTP-only-servers. Deze mogelijkheid biedt beveiliging tegen een rogue server.

-   Het beheerpunt geeft clients op internet een internetgebaseerde Application Catalog-websitepunt. Het beheerpunt geeft clients op basis van het intranet een intranet gebaseerd Application Catalog-websitepunt.  

Automatische detectie garandeert niet dat clients de dichtstbijzijnde Application Catalog-websitepunt zijn opgegeven. U kunt kiezen om **Automatisch detecteren** niet te gebruiken om volgende redenen:  

-   U handmatig de dichtstbijzijnde server configureren voor clients of zorg ervoor dat ze geen verbinding met een server via een trage netwerkverbinding.  

-   U wilt controleren welke clients met welke server verbinding maken. Deze configuratie kan zijn voor testdoeleinden, prestaties of zakelijke redenen.  

-   U wilt niet wachten maximaal 25 uur of wijst op een netwerkwijziging voor clients voor gebruik van een andere Application Catalog-website.  

Als u de Application Catalog-websitepunt opgeven in plaats van automatische detectie te gebruiken, geeft u de NetBIOS-naam in plaats van de intranet-FQDN. Deze configuratie vermindert de kans dat de webbrowser wordt gebruikers om referenties gevraagd wanneer ze toegang krijgen een intranet gebaseerd Application Catalog tot. De volgende voorwaarden moeten van toepassing zijn om de NetBIOS-naam te gebruiken:  

-   De NetBIOS-naam is opgegeven in de eigenschappen van het Application Catalog-websitepunt.  

-   U gebruikt WINS of alle clients bevinden zich in hetzelfde domein als de Application Catalog-websitepunt.  

-   U configureert het Application Catalog-websitepunt voor HTTP-clientverbindingen, of de server configureren voor HTTPS en het webservercertificaat heeft de NetBIOS-naam.  

Meestal worden gebruikers gevraagd om referenties wanneer de URL een FQDN-naam heeft, maar niet als de URL een NetBIOS-naam. Verwachten dat gebruikers altijd gevraagd wanneer ze via het internet verbinden, omdat deze verbinding het internet-FQDN moet gebruiken. Voor een client met internet wanneer gebruikers om referenties wordt gevraagd in de webbrowser, zorg ervoor dat het Application Catalog-websitepunt verbinding met een domeincontroller voor het gebruikersaccount maken kan. Deze configuratie kan de gebruiker te verifiëren via Kerberos.  

> [!NOTE]  
>  Hier ziet u hoe automatische detectie werkt:  
>   
>  De client maakt een verzoek om de servicelocatie aan een beheerpunt. Als er een Application Catalog-websitepunt in dezelfde site als de client aanwezig is, wordt de server aan de client gegeven als de te gebruiken Application Catalog-server. Als meer dan één Application Catalog-websitepunt in de site beschikbaar is, heeft een HTTPS-functionaliteit server voorrang op een server die niet is ingeschakeld voor HTTPS. Na dit filteren ontvangen alle clients een van de servers te gebruiken als de Application Catalog krijgen. Configuration Manager voert geen taakverdeling tussen meerdere servers. Wanneer de site van de client geen een Application Catalog-websitepunt heeft, retourneert het beheerpunt een Application Catalog-websitepunt niet-deterministisch uit de hiërarchie.  
>   
>  Voor intranet-clients, als u de Application Catalog-websitepunt met een NetBIOS-naam voor de Application Catalog-URL configureert, het beheerpunt gebruikt dit. Gebruikt niet de intranet-FQDN. Voor clients op internet geeft het beheerpunt alleen internet FQDN-naam naar de client.  
>   
>  De client deze servicelocatie-aanvraag indient elke 25 uur of wanneer deze een netwerkwijziging detecteert. Bijvoorbeeld, als de client wordt verplaatst van het intranet naar het internet, is dat een netwerkwijziging. Als de client vervolgens zoekt de client een internet-gebaseerd beheerpunt bevindt, geeft de internet-gebaseerd beheerpunt bevindt beheerpuntservers van de Application Catalog-website op basis van internet aan clients.  

### <a name="add-default-application-catalog-website-to-internet-explorer-trusted-sites-zone"></a>Voeg de standaard Application Catalog-website toe aan de zone met vertrouwde sites in Internet Explorer

Als deze optie is **Ja**, de client de huidige standaard Application Catalog-website-URL automatisch toegevoegd aan de zone Internet Explorer vertrouwde sites.  

Deze instelling zorgt ervoor dat de instelling in Internet Explorer voor de Beveiligde modus niet is ingeschakeld. Als beveiligde modus is ingeschakeld, kan de Configuration Manager-client mogelijk geen toepassingen uit de Application Catalog installeren. Standaard ondersteunt de zone met vertrouwde sites ook gebruikersaanmelding voor de Application Catalog, wat Windows-verificatie vereist.  

Als u deze optie ingesteld laat **Nee**, Configuration Manager-clients mogelijk geen toepassingen installeren uit de Application Catalog. Er is een alternatieve methode voor het configureren van deze instellingen voor Internet Explorer in een andere zone voor Application Catalog-URL die clients gebruiken.  

> [!NOTE]  
>  Wanneer de Configuration Manager een standaard Application Catalog-URL aan de zone met vertrouwde sites toevoegt, verwijdert Configuration Manager alle eerder toegevoegde Application Catalog-URL.  
>   
>  Als de URL al in een van de beveiligingszones opgegeven is, kan Configuration Manager de URL niet toevoegen. In dit scenario moet u de URL verwijderen van de andere zone of de vereiste instellingen in Internet Explorer configureren.  

### <a name="allow-silverlight-applications-to-run-in-elevated-trust-mode"></a>Toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus

Deze instelling moet **Ja** gebruikers de Application Catalog gebruiken.  

Als u deze instelling wijzigt, wordt deze van kracht wanneer gebruikers naast hun browser laadt of hun geopende browservenster vernieuwen.  

Zie voor meer informatie over deze instelling [certificaten voor Microsoft Silverlight 5 en verhoogde vertrouwensmodus vereist voor de application catalog](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5).  

### <a name="organization-name-displayed-in-software-center"></a>Weergegeven organisatienaam in Software Center

Typ de naam die wordt weergegeven in Software Center. Deze huismerkgegevens helpen gebruikers om deze toepassing als een vertrouwde bron te identificeren.  

### <a name="use-new-software-center"></a>Nieuwe Software Center gebruiken

Als u dit instellen op **Ja**, en vervolgens alle clientcomputers het Software Center gebruiken. Software Center bevat gebruikers beschikbare apps die eerder alleen toegankelijk in de Application Catalog zijn. De Application Catalog vereist Silverlight, die niet is een vereiste voor het Software Center. De standaardinstelling is gestart in Configuration Manager 1802, **Ja**.  

De Application Catalog-websitepunt en Application Catalog-webservice webservicepunt functies nog steeds vereist zijn voor gebruikers beschikbare apps zijn worden weergegeven in Software Center.  

Zie voor meer informatie [plannen en configureren van Toepassingsbeheer](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

### <a name="enable-communication-with-health-attestation-service"></a>Communicatie met Health Attestation-Service inschakelen

Stel dit in op **Ja** voor Windows 10-apparaten gebruiken [Health attestation](/sccm/core/servers/manage/health-attestation). Wanneer u deze instelling inschakelt, is ook de volgende instelling beschikbaar voor configuratie.

### <a name="use-on-premises-health-attestation-service"></a>On-premises Health Attestation-Service gebruiken

Stel dit in op **Ja** voor apparaten met een on-premises-service gebruiken. Ingesteld op **Nee** voor apparaten om de Microsoft cloud-gebaseerde service gebruiken.  

### <a name="install-permissions"></a>Installatiemachtigingen

> [!IMPORTANT]  
>  Deze instelling is van toepassing op de Application Catalog en Software Center. Deze instelling heeft geen effect wanneer gebruikers de bedrijfsportal gebruiken.  

Configureer hoe gebruikers de installatie van de software, software-updates en takenreeksen kunnen initialiseren:  

-   **Alle gebruikers**: Gebruikers met elke machtiging behalve Gast.  

-   **Alleen beheerders**: Gebruikers moeten lid zijn van de lokale groep Administrators.  

-   **Alleen beheerders en Hoofdgebruikers**: Gebruikers moeten lid zijn van de lokale groep Administrators of een primaire gebruiker van de computer.  

-   **Er zijn geen gebruikers**: Er zijn geen gebruikers die zijn aangemeld bij een clientcomputer kan de installatie van software, software-updates en takenreeksen kunnen initiëren. Vereiste implementaties voor de computer wordt altijd installeren op de deadline. Gebruikers kunnen niet de installatie van software uit de Application Catalog of Software Center niet initialiseren.  

### <a name="suspend-bitlocker-pin-entry-on-restart"></a>BitLocker-PINCODE opschorten bij opnieuw starten

Als computers BitLocker-pincode is vereist, wordt deze optie overgeslagen de vereiste voor een PINCODE invoeren wanneer de computer opnieuw wordt opgestart na een software-installatie.  

-   **Altijd**: Configuration Manager wordt BitLocker tijdelijk onderbroken nadat deze is geïnstalleerd software die moet worden opgestart en opnieuw opstarten van de computer heeft gestart. Deze instelling geldt alleen voor de computer opnieuw opgestart door Configuration Manager. Deze instelling schort niet de vereiste de BitLocker-PINCODE opgeven wanneer de gebruiker de computer opnieuw opstart. De BitLocker-PINCODE vermelding vereiste hervat na het opstarten van Windows.

-   **Nooit**: Configuration Manager schort niet BitLocker nadat deze is geïnstalleerd software die moet worden opgestart. In dit scenario kan de software-installatie niet worden voltooid tot de gebruiker de pincode heeft ingevoerd om het standaardopstartproces te voltooien en Windows te laden.

### <a name="additional-software-manages-the-deployment-of-applications-and-software-updates"></a>Aanvullende software beheert de implementatie van toepassingen en software-updates

Schakel deze optie alleen als een van de volgende voorwaarden van toepassing is:  

-   U gebruikt een leveranciersoplossing waarvoor deze instelling moet worden ingeschakeld.  

-   U gebruikt de Configuration Manager software development kit (SDK) om clientagentmeldingen en de installatie van toepassingen en software-updates.  

> [!WARNING]  
>  Als u deze optie wanneer geen van deze voorwaarden van toepassing, de client software-updates en vereiste toepassingen niet wordt geïnstalleerd. Deze instelling voorkomt niet dat gebruikers toepassingen van de Application Catalog of de installatie van pakketten, programma's en takenreeksen te installeren.  

### <a name="powershell-execution-policy"></a>PowerShell-uitvoeringsbeleid

Configureren hoe Configuration Manager-clients Windows PowerShell-scripts kunnen uitvoeren. U kunt deze scripts gebruiken voor detectie in configuratie-items voor compatibiliteitsinstellingen. U kunt ook de scripts in een implementatie als een Standaardscript verzenden.  

-   **Bypass**: Configuration Manager-client omzeilt de Windows PowerShell-configuratie op de clientcomputer zodat niet-ondertekende scripts kunnen uitvoeren.  

-   **Beperkte**: Configuration Manager-client gebruikt de huidige PowerShell-configuratie op de clientcomputer. Deze configuratie bepaalt of niet-ondertekende scripts kunnen worden uitgevoerd.  

-   **Alle ondertekende**: Configuration Manager-client scripts alleen uitgevoerd als een vertrouwde uitgever ze heeft ondertekend. Deze beperking geldt onafhankelijk van de huidige PowerShell-configuratie op de clientcomputer.  

Deze optie vereist ten minste Windows PowerShell versie 2.0. De standaardwaarde is **alle ondertekende**.  

> [!TIP]  
>  Als niet-ondertekende scripts niet kunnen worden uitgevoerd vanwege deze clientinstelling, rapporteert Configuration Manager deze fout in de volgende manieren:  
>   
> -   De **bewaking** werkruimte in de console weergegeven implementatie status fout-ID **0x87D00327**. Er wordt ook de beschrijving weergegeven **Script is niet ondertekend**.  
> -   Rapporten bevatten het fouttype **Detectiefout**. Vervolgens rapporten beide foutcode bevatten **0x87D00327** en de beschrijving **Script is niet ondertekend**, of foutcode **0x87D00320** en de beschrijving **de scripthost is nog niet geïnstalleerd**. Er is een voorbeeld van een rapport: **Details van fouten van configuratie-items in een configuratiebasislijn voor een asset**.  
> -   De **DcmWmiProvider.log** bestand verschijnt het bericht **Script is niet ondertekend (fout: 87D 00327; Bron: CCM)**.  

### <a name="show-notifications-for-new-deployments"></a>Meldingen weergeven voor nieuwe implementaties

Kies **Ja** om een melding voor implementaties die beschikbaar zijn voor minder dan een week weer te geven. Dit bericht verschijnt telkens wanneer de clientagent wordt gestart.

### <a name="disable-deadline-randomization"></a>Deadlinerandomisatie uitschakelen

Na de deadline van de implementatie met deze instelling bepaalt of de client een activeringsvertraging van maximaal twee uur gebruikt voor het installeren van vereiste software-updates. De vertraging is standaard uitgeschakeld.  

Voor virtuele desktopinfrastructuur (VDI) scenario's kan deze vertraging helpt te verdelen van de CPU-verwerking en gegevensoverdracht voor een hostmachine met meerdere virtuele machines. Zelfs als u geen VDI gebruikt, kunt veel clients tegelijkertijd dezelfde updates installeren negatief verhogen CPU-gebruik op de siteserver. Dit probleem kan ook aan distributiepunten vertragen en de beschikbare netwerkbandbreedte significant verminderen.  

Als clients vereiste software-updates op de deadline van de implementatie onmiddellijk moeten worden geïnstalleerd, configureert u deze instelling om **Ja**. 

### <a name="grace-period-for-enforcement-after-deployment-deadline-hours"></a>Respijtperiode voor afdwingen na de deadline van de implementatie (uren)

Als u gebruikers geven meer tijd wilt voor het installeren van vereiste toepassingen of software-update-implementaties na de deadline, stel dit in op **Ja**. Deze respijtperiode is voor een computer voor langere tijd uitgeschakeld en de gebruiker moet installeren veel toepassing of update-implementaties. Deze instelling is bijvoorbeeld handig als een gebruiker wordt geactiveerd vanuit een vakantie en lang wachten moet terwijl de client achterstallige toepassingsimplementaties installeert. 

Stel een respijtperiode van 1 tot 120 uur. Gebruik deze instelling samen met de implementatie-eigenschap **afdwingen van deze implementatie op basis van gebruikersvoorkeuren uitstellen**. Zie voor meer informatie [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications).


##  <a name="computer-restart"></a>Opnieuw opstarten van computer  
De volgende instellingen moet korter in duur dan het kortste onderhoudsvenster toegepast op de computer.  

-   **Een tijdelijke melding weergeven aan de gebruiker die het duurt voordat de gebruiker aangeeft wordt afgemeld of de computer opnieuw opstart (minuten)**
-   **Een dialoogvenster weergeven dat de gebruiker niet kan en sluiten waarin het aftellingsinterval voordat de gebruiker wordt afgemeld of de computer opnieuw opstart (minuten)**

Zie [Onderhoudsvensters gebruiken in System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md) voor meer informatie over onderhoudsvensters.



## <a name="delivery-optimization"></a>Leveringsoptimalisatie

<!-- 1324696 -->
U grensgroepen Configuration Manager gebruiken om te definiëren en inhoudsdistributie regelen tussen het bedrijfsnetwerk en naar externe kantoren. [Windows leveringsoptimalisatie](/windows/deployment/update/waas-delivery-optimization) is een cloud-gebaseerde, peer-to-peer-technologie voor het delen van inhoud tussen Windows 10-apparaten. Vanaf versie 1802, leveringsoptimalisatie voor het gebruik van uw grensgroepen bij het delen van inhoud tussen peers configureren.

 > [!Note]
 > Leveringsoptimalisatie is alleen beschikbaar op Windows 10-clients

### <a name="use-configuration-manager-boundary-groups-for-delivery-optimization-group-id"></a>Gebruik Configuration Manager-Grensgroepen voor levering optimalisatie groeps-ID
 Kies **Ja** toepassen van de grens groeps-id als de id van de groep leveringsoptimalisatie op de client. Wanneer de client met de cloudservice leveringsoptimalisatie communiceert, gebruikt deze id peers met de gewenste inhoud vinden. 



##  <a name="endpoint-protection"></a>Endpoint Protection  
>  [!Tip]   
> Naast de volgende informatie vindt u informatie over het gebruik van Endpoint Protection-clientinstellingen in [voorbeeldscenario: System Center Endpoint Protection gebruiken om computers te beveiligen tegen schadelijke software in System Center Configuration Manager](/sccm/protect/deploy-use/scenarios-endpoint-protection).

### <a name="manage-endpoint-protection-client-on-client-computers"></a>Endpoint Protection-client op clientcomputers beheren

Kies **Ja** als u wilt beheren van bestaande Endpoint Protection en Windows Defender-clients op computers in uw hiërarchie.  

Selecteer deze optie als u de Endpoint Protection-client reeds hebt geïnstalleerd en u wilt beheren met Configuration Manager. Deze afzonderlijke installatie bevat een script proces dat gebruikmaakt van een Configuration Manager-toepassing of pakket en programma. Vanaf Configuration Manager 1802, hoeft Windows 10-apparaten niet te hebben van de Endpoint Protection-agent die is geïnstalleerd. Echter, die apparaten nog steeds **beheren van Endpoint Protection-client op clientcomputers** ingeschakeld. <!--503654-->

### <a name="install-endpoint-protection-client-on-client-computers"></a>Endpoint Protection-client op clientcomputers installeren

Kies **Ja** installeren en activeren van de Endpoint Protection-client op clientcomputers die de client niet al worden uitgevoerd. Vanaf Configuration Manager 1802, hoeft Windows 10-clients niet te hebben van de Endpoint Protection-agent die is geïnstalleerd.  

> [!NOTE]  
>  Als de Endpoint Protection-client al is geïnstalleerd, kiezen **Nee** niet door de Endpoint Protection-client verwijderd. Om te verwijderen van de Endpoint Protection-client, stelt de **beheren van Endpoint Protection-client op clientcomputers** clientinstelling instelt op **Nee**. Vervolgens implementeert u een pakket en programma om de Endpoint Protection-client te verwijderen.  

### <a name="automatically-remove-previously-installed-antimalware-software-before-endpoint-protection-is-installed"></a>Eerder geïnstalleerde antimalware-software automatisch verwijderen voordat Endpoint Protection is geïnstalleerd

Stel dit in op **Ja** voor de Endpoint Protection-client om te verwijderen van de andere anti-malware-toepassingen. Meerdere antimalware-clients op hetzelfde apparaat kunnen een conflict veroorzaken, en de systeemprestaties.

### <a name="allow-endpoint-protection-client-installation-and-restarts-outside-maintenance-windows-maintenance-windows-must-be-at-least-30-minutes-long-for-client-installation"></a>Endpoint Protection-client installeren en opnieuw opstarten toestaan buiten onderhoudsvensters. Onderhoudsvensters moeten ten minste 30 minuten lang zijn voor clientinstallatie

Stel dit in op **Ja** standaardinstallatie gedrag met onderhoudsvensters overschrijven. Deze instelling voldoet aan de zakelijke vereisten voor de prioriteit van systeemonderhoud om beveiligingsredenen. 

### <a name="for-windows-embedded-devices-with-write-filters-commit-endpoint-protection-client-installation-requires-restarts"></a>Voor Windows Embedded-apparaten met schrijffilters installatie van Endpoint Protection-client (opnieuw opstarten noodzakelijk) toepassen

Kies **Ja** uit te schakelen van het schrijffilter op Windows Embedded-apparaat en het apparaat opnieuw opstarten. Deze actie voert de installatie op het apparaat.  

Als u ervoor kiest **Nee**, de client is geïnstalleerd op een tijdelijke overlay die wordt gewist wanneer het apparaat opnieuw wordt opgestart. In dit scenario wordt de Endpoint Protection-client is niet volledig worden geïnstalleerd totdat een andere installatie wijzigingen worden doorgevoerd in het apparaat. Deze configuratie is de standaardinstelling.  

### <a name="suppress-any-required-computer-restarts-after-the-endpoint-protection-client-is-installed"></a>Opnieuw opstarten vereist computer onderdrukken nadat de Endpoint Protection-client is geïnstalleerd

Kies **Ja** een herstart van de computer onderdrukken nadat de Endpoint Protection-client is geïnstalleerd.  

> [!IMPORTANT]  
>  Als de Endpoint Protection-client een opnieuw wordt opgestart vereist en deze instelling is **Nee**, klikt u vervolgens de computer opnieuw wordt opgestart ongeacht eventuele onderhoudsvensters geconfigureerd.  

### <a name="allowed-period-of-time-users-can-postpone-a-required-restart-to-complete-the-endpoint-protection-installation-hours"></a>Toegestane periode die gebruikers verplicht opnieuw opstarten om de installatie van Endpoint Protection te voltooien kan uitstellen (uur)

Als een herstart nodig is nadat de Endpoint Protection-client is geïnstalleerd, is deze instelling bepaalt u het aantal uren dat gebruikers de vereiste herstart kunnen uitstellen. Deze instelling vereist dat de instelling voor **onderdrukken eventuele vereiste computer opnieuw wordt opgestart nadat de Endpoint Protection-client is geïnstalleerd** is **Nee**.  

### <a name="disable-alternate-sources-such-as-microsoft-windows-update-microsoft-windows-server-update-services-or-unc-shares-for-the-initial-definition-update-on-client-computers"></a>Alternatieve bronnen uitschakelen (zoals Microsoft Windows Update, Microsoft Windows Server Update Services of UNC-shares) voor de initiële definitie-update op clientcomputers

Kies **Ja** als u wilt dat Configuration Manager alleen de initiële definitie-update op clientcomputers installeren. Deze instelling kan handig zijn om onnodige netwerkverbindingen te vermijden en netwerkbandbreedte tijdens de eerste installatie van de definitie-update.  



##  <a name="enrollment"></a>Inschrijving

### <a name="polling-interval-for-mobile-device-legacy-clients"></a>Pollinginterval voor verouderde clients van mobiele apparaten
Selecteer **Interval instellen** om op te geven van de tijdsduur in minuten of uren die verouderde mobiele apparaten poll-frequentie voor het beleid. Deze apparaten omvatten platformen, zoals Windows CE-, Mac OS X- en Unix- of Linux.

### <a name="polling-interval-for-modern-devices-minutes"></a>Polling-interval voor moderne apparaten (minuten)
Voer het aantal minuten dat moderne apparaten poll-frequentie voor het beleid. Deze instelling is voor Windows 10-apparaten die worden beheerd via on-premises-beheer voor mobiele apparaten.

### <a name="allow-users-to-enroll-mobile-devices-and-mac-computers"></a>Kunnen gebruikers zich inschrijven van mobiele apparaten en Mac-computers
Schakel inschrijving op basis van een gebruiker van de oudere apparaten door dit instellen op **Ja**, en configureer vervolgens de volgende instelling:

-   **Inschrijvingsprofiel** </br>
Selecteer **profiel instellen** te maken of een inschrijvingsprofiel selecteren. Zie voor meer informatie [configureren van clientinstellingen voor inschrijving](/sccm/core/clients/deploy/deploy-clients-to-macs#configure-client-settings-for-enrollment).

### <a name="allow-users-to-enroll-modern-devices"></a>Toestaan dat gebruikers moderne apparaten te registreren
Als u wilt inschakelen op basis van gebruiker inschrijven van moderne apparaten, dit instellen op **Ja**, en configureer vervolgens de volgende instelling:

-   **Inschrijvingsprofiel voor moderne apparaten** </br>
Selecteer **profiel instellen** te maken of een inschrijvingsprofiel selecteren. Zie voor meer informatie [maken van een Registratieprofiel waarmee gebruikers moderne apparaten te registreren](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm#bkmk_createProf).



##  <a name="hardware-inventory"></a>Hardware-inventaris  

### <a name="enable-hardware-inventory-on-clients"></a>Hardware-inventaris op clients inschakelen

Deze instelling is standaard **Ja**. Zie voor meer informatie [inleiding op hardware-inventarisatie](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory).

### <a name="hardware-inventory-schedule"></a>Hardware-inventarisplanning

Selecteer **planning** om aan te passen, de frequentie waarmee clients de hardware-inventarisatie uitvoeren cyclus. Deze cyclus wordt standaard elke zeven dagen plaatsvindt.

### <a name="maximum-random-delay-minutes"></a>Maximale willekeurige vertraging (minuten)

Geef het maximum aantal minuten voor de Configuration Manager-client naar de hardware-inventaris een willekeurige cyclus van de gedefinieerde planning. Deze willekeurige over alle clients kunt verdelen inventaris verwerking op de siteserver. U kunt een waarde tussen 0 en 480 minuten opgeven. Deze waarde is standaard ingesteld op 240 minuten (4 uur).

### <a name="maximum-custom-mif-file-size-kb"></a>Maximale bestandsgrootte aangepast MIF-bestand (KB)

Geef de maximale grootte, in kilobytes (KB) voor elk aangepast Management Information Format (MIF)-bestand dat de client worden verzameld tijdens een hardware-inventarisatiefase is toegestaan. De Configuration Manager-agent voor hardware-inventaris verwerkt geen aangepast MIF-bestanden die groter zijn dan deze limiet. U kunt een grootte van 1 KB 5.120 kB opgeven. Deze waarde is standaard ingesteld op 250 KB. Deze instelling heeft geen invloed op de grootte van het normale hardware-inventarisgegevensbestand.  

> [!NOTE]  
>  Deze instelling is alleen beschikbaar in de standaardclientinstellingen.  

### <a name="hardware-inventory-classes"></a>Hardware-inventarisklassen

Selecteer **klassen instellen** uitbreiden van de hardware-informatie die u van clients verzamelt zonder het sms_def.mof-bestand handmatig te bewerken. Zie voor meer informatie [het configureren van hardware-inventaris](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

### <a name="collect-mif-files"></a>MIF-bestanden verzamelen

Gebruik deze instelling kunt u opgeven of voor het verzamelen van MIF-bestanden van Configuration Manager-clients tijdens hardware-inventaris.  

Voor een MIF-bestand moeten worden verzameld door hardware-inventaris, moet deze de juiste locatie op de clientcomputer. Standaard worden de bestanden bevinden zich in de volgende paden:  

-   **IDMIF-bestanden** moet in de map Windows\System32\CCM\Inventory\Idmif. 

-   **NOIDMIF-bestanden** moet in de map Windows\System32\CCM\Inventory\Noidmif.

> [!NOTE]  
>  Deze instelling is alleen beschikbaar in de standaardclientinstellingen.

   

##  <a name="metered-internet-connections"></a>Internetverbindingen naar gebruik  
 Beheren hoe Windows 8 en hoger computers internetverbindingen naar gebruik gebruiken om te communiceren met Configuration Manager. Sommige betaalt internetproviders u door de hoeveelheid gegevens die u verzendt en ontvangt wanneer u van een internetverbinding gebruikmaakt.  

> [!NOTE]  
>  De geconfigureerde clientinstelling wordt niet toegepast in de volgende scenario's:  
>   
> -   Als de computer zich op een roaming gegevensverbinding, wordt in de Configuration Manager-client geen taken waarbij gegevens worden overgedragen naar Configuration Manager-sites niet uitvoeren.  
> -   Als de verbindingseigenschappen van de Windows-netwerk zijn geconfigureerd als zonder datalimiet, Configuration Manager-client gedraagt zich alsof de verbinding zonder datalimiet is en bijgevolg gegevens naar de site verstuurt.  

### <a name="client-communication-on-metered-internet-connections"></a>Clientcommunicatie bij internetverbindingen naar gebruik

Kies een van de volgende opties voor deze instelling:  

-   **Toestaan dat**: Alle clientcommunicaties zijn toegestaan over de internetverbinding met datalimiet, tenzij het clientapparaat een roaming gegevensverbinding gebruikt.  

-   **Limiet**: De volgende clientcommunicaties zijn toegestaan over de internetverbinding met datalimiet:  

    -   Clientbeleid ophalen  

    -   Clientstatusberichten om te verzenden naar de site  

    -   Software-installatieaanvragen via de Application Catalog  

    -   Vereiste implementaties (zodra de installatiedeadline wordt bereikt)  

    > [!IMPORTANT]  
    >  De client kan software-installaties van Software Center of de Toepassingscatalogus, ongeacht de internetverbindingen altijd verbindingsinstellingen.  

    Als de client de gegevensoverdrachtlimiet voor de internetverbinding met datalimiet is bereikt, probeert de client niet langer te communiceren met Configuration Manager-sites.  

-   **Blok**: Configuration Manager-client probeert niet te communiceren met Configuration Manager-sites wanneer deze zich op een internetverbinding. Dit is de standaardoptie.  



##  <a name="power-management"></a>Energiebeheer  

### <a name="allow-power-management-of-devices"></a>Energiebeheer van apparaten toestaan

Stel dit in op **Ja** energiebeheer op clients inschakelen. Zie voor meer informatie [inleiding op Energiebeheer](/sccm/core/clients/manage/power/introduction-to-power-management).

### <a name="allow-users-to-exclude-their-device-from-power-management"></a>Toestaan dat gebruikers hun apparaat uit energiebeheer uitsluiten

Kies **Ja** zodat gebruikers van Software Center hun computer uitsluiten van een geconfigureerde energiebeheerinstellingen.  

### <a name="enable-wake-up-proxy"></a>Wake-up proxy inschakelen

Geef **Ja** ter aanvulling van de instelling van de Wake On LAN van de site, wanneer hij geconfigureerd wordt voor unicastpakketten.  

Zie voor meer informatie over wake-up proxy [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

> [!WARNING]  
>  Schakel wake-up proxy niet in een productienetwerk in zonder eerst te begrijpen hoe het werkt en het te beoordelen in een testomgeving.  

Configureer vervolgens de volgende aanvullende instellingen zo nodig:

-   **Poortnummer wake-up proxy (UDP)**  </br>
         Het poortnummer die clients gebruiken voor het verzenden van ontwaakpakketten naar computers in de slaapstand. De standaardpoort 25536 behouden of wijzig het nummer in een waarde van uw keuze.  

-   **Poortnummer Wake On LAN (UDP)** </br> 
         Hou de standaardwaarde van 9, tenzij u het Wake On LAN (UDP) poortnummer hebt gewijzigd op de **poorten** tabblad van de site **eigenschappen**.  

    > [!IMPORTANT]  
    >  Dit nummer moet overeenkomen met het nummer in de **Eigenschappen**van de site. Als u dit nummer op één plaats wijzigt, is niet het automatisch bijgewerkt op de andere plaats.  

-   **Windows Defender Firewall-uitzondering voor wake-up proxy** </br>
         Configuration Manager-client configureert automatisch de wake-up proxypoortnummer op apparaten met Windows Defender-Firewall. Selecteer **configureren** om op te geven van de gewenste firewallprofielen.

    Als clients een andere firewall uitvoeren, moet u handmatig configureren zodat deze de **Wake-up proxypoortnummer (UDP)**.  
        
-   **IPv6-voorvoegsels indien vereist voor DirectAccess of andere Tussenkomende netwerkapparaten. Gebruik een komma om meerdere vermeldingen scheiden** </br>
        Voer de benodigde IPv6-voorvoegsels voor wake-up-proxy om te functioneren in uw netwerk.



##  <a name="remote-tools"></a>Externe hulpprogramma 's  

### <a name="enable-remote-control-on-clients-and-firewall-exception-profiles"></a>Beheer op afstand inschakelen op clients en Firewall-uitzonderingsprofielen

Selecteer **configureren** Configuration Manager-beheer op afstand inschakelen. Configureer desgewenst firewall-instellingen voor extern beheer om te werken op clientcomputers.  

Beheer op afstand is standaard uitgeschakeld.  

> [!IMPORTANT]  
>  Indien firewall-instellingen niet geconfigureerd zijn, zal het kunnen gebeuren dat externe controle niet juist werkt.  

### <a name="users-can-change-policy-or-notification-settings-in-software-center"></a>Gebruikers kunnen instellingen voor beleid of meldingen in Software Center wijzigen

Kies of gebruikers externe controle-opties van Software Center kunnen wijzigen.  

### <a name="allow-remote-control-of-an-unattended-computer"></a>Beheer op afstand van een onbeheerde computer toestaan

Kies of een beheerder extern beheer gebruiken kan voor toegang tot een clientcomputer die afgemeld is of vergrendeld. Alleen een computer is aangemeld en ontgrendeld kan extern worden beheerd wanneer deze instelling is uitgeschakeld.  

### <a name="prompt-user-for-remote-control-permission"></a>Gebruiker vragen naar machtiging voor extern beheer

Kies of de clientcomputer ziet u een bericht dat om toestemming voordat een sessie voor extern beheer van de gebruiker wordt gevraagd.  

### <a name="prompt-user-for-permission-to-transfer-content-from-shared-clipboard"></a>Gebruiker vragen naar machtiging voor het overbrengen van inhoud vanaf het gedeelde Klembord

Uw gebruikers de mogelijkheid om te accepteren of weigeren van bestandsoverdrachten, voordat de overdracht van inhoud van het gedeelde Klembord in een sessie voor extern beheer toestaan. Gebruikers hoeven alleen te machtigen eenmaal per sessie en de viewer heeft niet de mogelijkheid zelf om toestemming te geven om door te gaan met de bestandsoverdracht.

### <a name="grant-remote-control-permission-to-local-administrators-group"></a>Machtigingen voor beheer op afstand toekennen aan lokale groep Administrators

Kies of de externe controle-sessies op clientcomputers kan worden gemaakt door de lokale beheerders op de server waarop de beheer op afstand verbinding initieert.  

### <a name="access-level-allowed"></a>Toegestaan toegangsniveau

Geef het niveau van beheer op afstand toegang om toe te staan. Kies in de volgende instellingen:  
- **Geen toegang**
- **Alleen weergeven**
- **Volledig beheer**  

### <a name="permitted-viewers-of-remote-control-and-remote-assistance"></a>Toegelaten viewers van beheer op afstand en hulp op afstand

Selecteer **Stel Viewers** om op te geven van de namen van de Windows-gebruikers die externe controlesessies naar clientcomputers kunnen instellen.  

### <a name="show-session-notification-icon-on-taskbar"></a>Sessiemeldingspictogram op de taakbalk

Deze instelling en **Ja** om een pictogram op de taakbalk van de client om aan te geven van een actieve beheer op afstandsessie weer te geven.  

### <a name="show-session-connection-bar"></a>Sessieverbindingsbalk weergeven

Stel dit in op **Ja** om een hoge visibiliteit sessieverbindingsbalk op clients om aan te geven van een actieve beheer op afstandsessie weer te geven.  

### <a name="play-a-sound-on-client"></a>Een geluid afspelen op client

Stel dit om geluid te gebruiken om aan te geven wanneer een externe controlesessie actief op een clientcomputer is. Selecteer een van de volgende opties:
- **Geen geluid**
- **Begin- en verzenden van sessie** (standaard)
- **Herhaaldelijk tijdens een sessie**  

### <a name="manage-unsolicited-remote-assistance-settings"></a>Instellingen voor ongevraagde hulp op afstand beheren

Deze instelling en **Ja** Configuration Manager beheren ongevraagde externe hulpsessies te laten.  

In een sessie voor ongevraagde hulp op afstand, de gebruiker op de clientcomputer is niet om hulp vragen aan de sessie te starten.  

### <a name="manage-solicited-remote-assistance-settings"></a>Instellingen voor gevraagde hulp op afstand beheren

Stel dit in op **Ja** Configuration Manager beheren gevraagde externe hulpsessies te laten.  

In een sessie voor gevraagde hulp op afstand verzonden de gebruiker op de clientcomputer een aanvraag naar de beheerder voor hulp op afstand.  

### <a name="level-of-access-for-remote-assistance"></a>Toegangsniveau voor hulp op afstand

Kies het niveau van toegang toe te wijzen om externe hulpsessies die geïnitieerd zijn in de Configuration Manager-console. Selecteer een van de volgende opties:
- **Geen** (standaard)
- **Externe weergeven**
- **Volledig beheer**

> [!NOTE]  
>  De gebruiker op de clientcomputer moet altijd toegang verlenen opdat een externe hulpsessie zou kunnen plaatsvinden.  

### <a name="manage-remote-desktop-settings"></a>Instellingen voor extern bureaublad beheren

Stel dit in op **Ja** zodat Configuration Manager beheren van extern bureaublad-sessies voor computers.  

### <a name="allow-permitted-viewers-to-connect-by-using-remote-desktop-connection"></a>Toegelaten viewers verbinding maken via Extern bureaublad-verbinding toestaan

Stel dit in op **Ja** gebruikers die zijn opgegeven in de lijst met toegelaten viewers aan de lokale gebruikersgroep van extern bureaublad op clients toe te voegen.  

### <a name="require-network-level-authentication-on-computers-that-run-windows-vista-operating-system-and-later-versions"></a>Verificatie op netwerkniveau vereisen op computers waarop het besturingssysteem Windows Vista en latere versies

Stel dit in op **Ja** gebruik van verificatie op netwerkniveau (NLA) tot stand brengen van extern bureaublad-verbindingen op clientcomputers. NLA vereist in eerste instantie minder externe computerbronnen omdat het gebruikersverificatie is voltooid voordat het een extern bureaublad-verbinding tot stand brengt. Met behulp van NLA is een veiligere configuratie. NLA zorgt de computer beschermen tegen kwaadwillende gebruikers of software en vermindert het risico op denial of service-aanvallen.  



## <a name="software-center"></a>Software Center

### <a name="select-these-new-settings-to-specify-company-information"></a>Deze nieuwe instellingen om op te geven bedrijfsgegevens selecteren
Stel dit in op **Ja**, en geef vervolgens de volgende instellingen op merk Software Center voor uw organisatie:

- **Bedrijfsnaam** </br>
Voer de naam van de organisatie die wordt weergegeven in Software Center.
- **Kleurenschema voor Software Center** </br>
Selecteer **Selecteer kleur** voor het definiëren van de primaire kleur die wordt gebruikt door Software Center.
- **Selecteer een logo voor Software Center** </br>
Selecteer **Bladeren** om een installatiekopie worden weergegeven in Software Center te selecteren. Het logo moet een JPEG-, PNG of BMP van 400 x 100 pixels en een maximale grootte van 750 KB. De naam van het logo mag geen spaties bevatten.  
         
### <a name="bkmk_HideUnapproved"></a> Niet-goedgekeurde toepassingen in Software Center verbergen
U start in Configuration Manager versie 1802, wanneer deze optie is ingeschakeld, zijn gebruiker beschikbare toepassingen die moeten worden goedgekeurd verborgen in Software Center.   <!--1355146-->

### <a name="bkmk_HideInstalled"></a> Geïnstalleerde toepassingen in Software Center verbergen
U start in Configuration Manager versie 1802,-toepassingen die al zijn geïnstalleerd, worden niet meer op het tabblad toepassingen weergegeven wanneer deze optie is ingeschakeld. Deze optie is ingesteld als standaard bij het installeren of upgraden naar Configuration Manager 1802.  Geïnstalleerde toepassingen zijn nog steeds beschikbaar is voor controle op het tabblad van de status van de installatie. <!--1357592-->   
  
### <a name="software-center-tab-visibility"></a>Software Center tabblad zichtbaarheid
De extra instellingen configureren in deze groep **Ja** zichtbaar maken voor de volgende tabbladen in Software Center:
- **Toepassingen**
- **Updates**
- **Besturingssystemen**
- **Installatiestatus**
- **Apparaatcompatibiliteit**
- **Opties**

Bijvoorbeeld, als uw organisatie gebruikt geen beleidsregels voor naleving en u wilt verbergen van het tabblad apparaatcompatibiliteit in Software Center, stelt u **apparaatcompatibiliteit inschakelen tabblad** naar **Nee**.



## <a name="software-deployment"></a>Software-implementatie  

### <a name="schedule-re-evaluation-for-deployments"></a>Nieuwe evaluatie voor implementaties plannen
Configureer een planning voor wanneer de Configuration Manager de regels voor vereisten voor alle implementaties opnieuw beoordeelt. De standaardwaarde is elke zeven dagen.  

> [!IMPORTANT]  
>  U wordt aangeraden dat u deze waarde niet op een lagere waarde dan de standaardwaarde wijzigt. Een agressievere planning nieuwe evaluatie van negatieve invloed op de prestaties van uw netwerk en clientcomputers.  

Deze actie van een client als volgt te initiëren: in de **Configuration Manager** Configuratiescherm van de **acties** tabblad **Beoordelingscyclus toepassingsimplementatie**.  



##  <a name="software-inventory"></a>Software-inventaris  

### <a name="enable-software-inventory-on-clients"></a>Software-inventaris op clients inschakelen

Dit is ingesteld op **Ja** standaard. Zie voor meer informatie [Inleiding tot software-inventaris](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).

### <a name="schedule-software-inventory-and-file-collection"></a>Software-inventaris en verzamelen van bestanden plannen

Selecteer **planning** om aan te passen, de frequentie dat clients de software-inventaris en de bestandsnaam verzameling cycli uitvoeren. Deze cyclus wordt standaard elke zeven dagen plaatsvindt.

### <a name="inventory-reporting-detail"></a>Detail inventarisrapportage

Geef een van de volgende niveaus van te inventariseren bestandsgegevens:
- **Alleen bestand**
- **Alleen product**
- **Volledige details** (standaard)

### <a name="inventory-these-file-types"></a>Deze bestandstypen inventariseren

Als u opgeven welke typen bestand naar de voorraad wilt, selecteert u **Stel typen**, en configureer vervolgens de volgende opties:  

> [!NOTE]  
>  Als meerdere aangepaste clientinstellingen worden toegepast op een computer, wordt de inventaris die wordt geretourneerd voor elke instelling samengevoegd.  

-   Selecteer **nieuw** een nieuw bestandstype toevoegen aan inventaris. Geef vervolgens de volgende gegevens in de **eigenschappen geïnventariseerd bestand** in het dialoogvenster:  

    -   **Naam**: Geef een naam voor het bestand dat u wilt inventariseren. Gebruik een sterretje (**&#42;**) jokertekens vertegenwoordigt een willekeurige tekenreeks van tekst en een vraagteken (**?**) een willekeurig teken vertegenwoordigt. Bijvoorbeeld, als u inventariseren van alle bestanden met de extensie .doc wilt, de bestandsnaam opgeven  **\*.doc**.  

    -   **Locatie**: Selecteer **ingesteld** openen de **padeigenschappen** in het dialoogvenster. Configureren van software-inventaris om te zoeken alle harde schijven voor het opgegeven bestand, zoek een opgegeven pad (bijvoorbeeld **C:\Folder**), of zoeken naar een opgegeven variabele (bijvoorbeeld *% windir %*). U kunt ook zoeken in alle Deelmappen onder het opgegeven pad.  

    -   **Sluit versleutelde en gecomprimeerde bestanden**: Als u deze optie kiest, worden gecomprimeerd, of versleutelde bestanden niet geïnventariseerd.  

    -   **Sluit bestanden uit in de map Windows**: Als u deze optie kiest, worden alle bestanden in de Windows-map en haar Deelmappen niet geïnventariseerd.  

    Selecteer **OK** sluiten de **eigenschappen geïnventariseerd bestand** in het dialoogvenster. Voeg alle bestanden die u wilt inventariseren en selecteer vervolgens **OK** sluiten de **Configureer Clientinstelling** in het dialoogvenster.  

### <a name="collect-files"></a>Bestanden verzamelen

Als u wenst bestanden te verzamelen van clientcomputers, selecteert u **Stel bestanden**, en configureer vervolgens de volgende instellingen:  

> [!NOTE]  
>  Als meerdere aangepaste clientinstellingen worden toegepast op een computer, wordt de inventaris die wordt geretourneerd voor elke instelling samengevoegd.  

-   In de **Configureer Clientinstelling** dialoogvenster, **nieuw** toevoegen van een bestand moet worden verzameld.  

-   Voer, in het dialoogvenster **Eigenschappen verzameld bestand** , de volgende informatie in:  

    -   **Naam**: Geef een naam voor het bestand dat u wilt verzamelen. Gebruik een sterretje (**&#42;**) jokertekens vertegenwoordigt een willekeurige tekenreeks van tekst en een vraagteken (**?**) een willekeurig teken vertegenwoordigt.  

    -   **Locatie**: Selecteer **ingesteld** openen de **padeigenschappen** in het dialoogvenster. Configureren van software-inventaris om te zoeken naar alle harde schijven voor het bestand dat u wilt verzamelen, zoek een opgegeven pad (bijvoorbeeld **C:\Folder**), of zoeken naar een opgegeven variabele (bijvoorbeeld *% windir %*). U kunt ook zoeken in alle Deelmappen onder het opgegeven pad.  

    -   **Sluit versleutelde en gecomprimeerde bestanden**: Als u deze optie kiest, wordt gecomprimeerd, of versleutelde bestanden worden niet verzameld.  

    -   **Stoppen met verzamelen van bestanden wanneer de totale grootte van de bestanden overschrijdt (KB)**: Geef de bestandsgrootte in kilobytes (KB), waarna de client stopt het verzamelen van de opgegeven bestanden.  

    > [!NOTE]  
    >  De siteserver verzamelt de vijf meest recent gewijzigde versies van verzamelde bestanden en slaat ze op in de  *&lt;installatiemap van Configuration Manager\>*\Inboxes\Sinv.box\Filecol directory. Als een bestand niet is gewijzigd sinds de laatste software-inventarisatiefase, wordt het bestand niet opnieuw verzameld.  
    >   
    >  Software-inventaris verzamelt geen bestanden groter dan 20 MB.  
    >   
    >  De waarde **maximale grootte voor alle verzamelde bestanden (KB)** in de **Configureer Clientinstelling** in het dialoogvenster ziet u de maximale grootte voor alle verzamelde bestanden. Wanneer deze grootte is bereikt, stopt bestandsverzameling. Alle reeds verzamelde bestanden worden weerhouden en naar de siteserver gezonden.  

    > [!IMPORTANT]
    >  Als u software-inventaris voor het verzamelen van veel grote bestanden configureert, kan deze configuratie negatieve invloed hebben op de prestaties van uw netwerk- en site-server.  

    Zie voor meer informatie over het raadplegen van verzamelde bestanden [Resource Explorer gebruiken om software-inventaris weer te geven](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

    Selecteer **OK** sluiten de **eigenschappen verzameld bestand** in het dialoogvenster. Voeg alle bestanden die u wilt verzamelen, en selecteer vervolgens **OK** sluiten de **Configureer Clientinstelling** in het dialoogvenster.  

### <a name="set-names"></a>Namen instellen

De software-inventarisagent haalt de fabrikant en productnamen koptekstgegevens van bestand. Deze namen niet altijd gestandaardiseerd zijn in de header bestandsgegevens. Wanneer u software-inventaris in Resourceverkenner bekijkt, kunnen verschillende versies van dezelfde fabrikant of productnaam verschijnen. Deze standaardiseren weergavenamen, selecteer **Stel namen**, en configureer vervolgens de volgende instellingen:  

-   **Naamtype**: Software-inventaris verzamelt informatie over fabrikanten en producten. Kies of u wilt configureren weergavenamen voor een **fabrikant** of een **Product**.  

-   **Weergavenaam**: Geef de weergavenaam op die u wilt gebruiken in plaats van de namen in de **geïnventariseerde namen** lijst. U kunt een nieuwe weergavenaam opgeven, **nieuw**.  

-   **Geïnventariseerde namen**: Selecteer om een geïnventariseerde naam toe **nieuw**. Deze naam in software-inventaris wordt vervangen door de naam van de gekozen in de **weergavenaam** lijst. U kunt meerdere namen vervangen toevoegen.  



##  <a name="software-metering"></a>Softwaremeter

### <a name="enable-software-metering-on-clients"></a>Softwaremeter op clients inschakelen
Deze instelling is ingesteld op **Ja** standaard. Zie voor meer informatie [softwarelicentiecontrole](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering#configure-software-metering).

### <a name="schedule-data-collection"></a>Verzamelen van gegevens plannen
Selecteer **planning** om aan te passen, de frequentie dat clients de cyclus voor softwarelicentiecontrole uitvoeren. Deze cyclus wordt standaard elke zeven dagen plaatsvindt.



##  <a name="software-updates"></a>Software-updates  

### <a name="enable-software-updates-on-clients"></a>Software-updates op clients inschakelen

Deze instelling gebruiken om softwareupdates inschakelen op Configuration Manager-clients. Wanneer u deze instelling uitschakelt, verwijdert Configuration Manager de bestaande implementatiebeleiden van de client. Wanneer u deze instelling opnieuw inschakelt, zal de client het huidige implementatiebeleid downloaden.  

> [!IMPORTANT]  
>  Wanneer u deze instelling uitschakelt, werkt beleidsregels voor nalevingsbeleid die afhankelijk van de software-updates zijn niet meer.  

### <a name="software-update-scan-schedule"></a>Planning software-Updatescan

Selecteer **planning** om op te geven hoe vaak de client een scan voor beoordeling van naleving initieert. Deze scan bepaalt de status voor software-updates op de client (bijvoorbeeld vereist of geïnstalleerd). Zie voor meer informatie over nalevingsbeoordeling [beoordeling van compatibiliteit van Software-updates](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

Deze scan gebruikt standaard een eenvoudige planning om te starten elke zeven dagen. U kunt een aangepaste planning kunt maken. U kunt opgeven voor een exacte startdatum en -tijd, Universal Coordinated Time (UTC) of de lokale tijd gebruiken en het terugkerende interval configureren voor een specifieke dag van de week.  

> [!NOTE]  
>  Als u een interval van minder dan een dag opgeeft, wordt Configuration Manager automatisch standaard ingesteld op één dag.  

> [!WARNING]  
>  De daadwerkelijke starttijd op clientcomputers is de starttijd plus een willekeurige hoeveelheid tijd, maximaal twee uur. Deze willekeurige wordt voorkomen dat clientcomputers de scan starten en tegelijkertijd te verbinden met het actieve software-updatepunt.  

### <a name="schedule-deployment-re-evaluation"></a>Nieuwe evaluatie van implementatie plannen

Selecteer **planning** configureren hoe vaak de software-updates opnieuw evalueert software clientagentupdates voor de installatiestatus van Configuration Manager-clientcomputers. Wanneer eerder geïnstalleerde software-updates op clients, maar worden nog steeds vereist, de client niet meer worden gevonden, wordt de software-updates opnieuw geïnstalleerd.

Pas deze planning op basis van bedrijfsbeleid voor compatibiliteit van software-update, en of gebruikers software-updates kunnen verwijderen. Elke cyclus voor het nieuwe evaluatie resulteert in het netwerk en clientcomputers computer processoractiviteit. Deze instelling maakt standaard gebruik van een eenvoudige planning voor het initiëren van de implementatie van nieuwe evaluatiescan elke zeven dagen.  

> [!NOTE]  
>  Als u een interval van minder dan een dag opgeeft, wordt Configuration Manager automatisch standaard ingesteld op één dag.  

### <a name="when-any-software-update-deployment-deadline-is-reached-install-all-other-software-update-deployments-with-deadline-coming-within-a-specified-period-of-time"></a>Wanneer de deadline van een software-update-implementatie is bereikt, installeert u alle andere software-update-implementaties met een deadline binnen een opgegeven periode

Stel dit in op **Ja** voor het installeren van alle software-updates van de vereiste implementaties met deadlines die binnen een opgegeven periode. Als een vereiste software-update-implementatie een deadline is bereikt, initieert de client-installatie voor de software-updates in de implementatie. Deze instelling bepaalt of voor het installeren van software-updates van andere vereiste implementaties met een deadline binnen de opgegeven tijdsduur hebben.  

Deze instelling gebruiken om de installatie voor vereiste software-updates versnellen. Deze instelling heeft ook de mogelijkheid tot een betere beveiliging van de client, meldingen aan de gebruiker te verkleinen en verkleinen van de client opnieuw wordt opgestart. Deze waarde is standaard ingesteld op **Nee**.  

### <a name="period-of-time-for-which-all-pending-deployments-with-deadline-in-this-time-will-also-be-installed"></a>Periode waarvoor alle implementaties in behandeling met een deadline binnen deze tijd worden ook geïnstalleerd

Gebruik deze instelling om op te geven van de periode voor de vorige instelling. U kunt een waarde invoeren tussen 1 en 23 uur en tussen 1 en 365 dagen. Deze instelling is standaard geconfigureerd op 7 dagen.  

### <a name="enable-installation-of-express-installation-files-on-clients"></a>Installatie van bestanden voor snelle installatie op clients inschakelen

Stel dit in op **Ja** wilt toestaan dat clients bestanden voor snelle installatie gebruiken. Zie voor meer informatie [installatiebestanden beheren Express voor Windows 10-updates](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).

### <a name="port-used-to-download-content-for-express-installation-files"></a>Poort die wordt gebruikt voor het downloaden van inhoud voor de bestanden voor snelle installatie

Deze instelling configureert u de lokale poort voor de HTTP-listener snelle inhoud te downloaden. Dit is standaard ingesteld op 8005 blijven ingedeeld. U hoeft niet te openen van deze poort in de clientfirewall.

### <a name="enable-management-of-the-office-365-client-agent"></a>Beheer van de Office 365-Clientagent inschakelen

Wanneer u dit instellen op **Ja**, hierdoor kan de installatie-instellingen voor Office 365 worden geconfigureerd. Bovendien kunnen downloaden van bestanden van inhoud levering bedrijfsnetwerken (CDN) en het implementeren van de bestanden als een toepassing in Configuration Manager. Zie voor meer informatie [Office 365 ProPlus beheren](/sccm/sum/deploy-use/manage-office-365-proplus-updates).



## <a name="state-messaging"></a>Messaging-status

### <a name="state-message-reporting-cycle-minutes"></a>Rapportagecyclus (minuten) statusbericht
Geeft aan hoe vaak clients statusberichten rapporteren. Deze instelling is standaard de 15 minuten.



##  <a name="user-and-device-affinity"></a>Affiniteit van gebruiker en apparaat  

### <a name="user-device-affinity-usage-threshold-minutes"></a>Gebruiker gebruiksdrempel apparaataffiniteit (minuten)
Geef het aantal minuten voordat Configuration Manager toewijzing maakt voor een gebruiker apparaataffiniteit.  Deze waarde is standaard 2880 minuten (2 dagen).

### <a name="user-device-affinity-usage-threshold-days"></a>Gebruiksdrempel van affiniteit van gebruiker-apparaat (dagen)
Geef het aantal dagen gedurende welke de client de drempel voor affiniteit tussen gebruikers-gebaseerde apparaten meet.  Deze waarde is standaard 30 dagen.

> [!NOTE]  
>  Geef bijvoorbeeld **gebruiker gebruiksdrempel apparaataffiniteit (minuten)** als **60** minuten en **gebruiksdrempel van affiniteit van gebruiker-apparaat (dagen)** als **5**  dagen. Vervolgens moet de gebruiker het apparaat gedurende 60 minuten gebruiken gedurende een periode van 5 dagen voor het maken van automatische affiniteit met het apparaat.  

### <a name="automatically-configure-user-device-affinity-from-usage-data"></a>Gebruikersapparaataffiniteit apparaat automatisch configureren van gebruiksgegevens
Kies **Ja** voor het maken van automatische gebruikersaffiniteit met apparaat op basis van de gebruiksgegevens die door Configuration Manager worden verzameld.  

### <a name="allow-user-to-define-their-primary-devices"></a>Toestaan dat gebruikers hun primaire apparaten definiëren
Wanneer deze instelling is **Ja**, gebruikers hun eigen primaire apparaten in Software Center kunnen herkennen.



## <a name="windows-analytics"></a>Windows Analytics

Zie voor meer informatie over deze instellingen [Clients configureren voor het rapportgegevens Windows Analytics](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics).
    
