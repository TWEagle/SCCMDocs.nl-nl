---
title: Mogelijkheden van Technical Preview 1606
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager versie 1606.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 134a2f60-811e-4dc9-a8f5-1ce0018c5c12
caps.latest.revision: 
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: 59a57e20a21aac7c650c25e13df0f3180c2110ea
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1606-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1606 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager versie 1606 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    

**Bekende problemen in deze Technical Preview:**  
*  Wanneer u een van Technical Preview 1604-1605 en vervolgens naar versie 1606 update, de update mislukken en een vergelijkbaar met de volgende fout vastgelegd in de **cmupdate.log**:

       ERROR: Failed to execute SQL Server command:  ~ ~-- Create site boundary group ~IF  dbo.fnIsCasOrStandalonePrimary() = 1 ~BEGIN ~   PRINT N'Create site boundary group during upgrade' ~   EXEC dbo.spBuildDefaultBoundaryGroups @UserName = N'SYSTEM' ~END          

    Als dit gebeurt, in de **Updates en onderhoud** knooppunt Klik **controleren op updates**, en vervolgens **probeer** installatie van de update.
    ***

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="dmp_category"></a>Apparaten automatisch categoriseren in verzamelingen
U kunt apparaatcategorieën dat kunnen worden gebruikt voor apparaten worden automatisch op apparaatverzamelingen plaatsen wanneer u van Configuration Manager met Microsoft Intune gebruikmaakt kunt maken. Gebruikers hoeven vervolgens een apparaatcategorie kiezen wanneer ze een apparaat bij Intune inschrijven. Bovendien kunt u de categorie van een apparaat wijzigen vanuit de Configuration Manager-console.

**Belangrijk:** Deze mogelijkheid werkt met de **juni 2016** versie van Microsoft Intune. Zorg ervoor dat u hebt bijgewerkt naar deze versie voordat u deze procedures.

### <a name="try-it-out"></a>Probeer het nu!

### <a name="create-a-set-of-device-categories"></a>Maken van een reeks apparaatcategorieën
1.  In de **activa en naleving** werkruimte van de Configuration Manager-console, vouw **overzicht**, klikt u vervolgens op **Apparaatverzamelingen**.
2.  Op de **Start** tabblad, in de **categorieën** groep, klikt u op **apparaatcategorieën beheren**.
3.  In de **apparaatcategorieën beheren** in het dialoogvenster maken, bewerken of verwijderen van categorieën. Probeer een nieuwe categorie te maken.

### <a name="associate-a-collection-with-a-device-category"></a>Een verzameling koppelen aan een apparaatcategorie
Als u een verzameling met een apparaatcategorie koppelt, worden alle apparaten in de categorie die u opgeeft worden toegevoegd aan deze verzameling.
1.  In de **eigenschappen** dialoogvenster voor een apparaatverzameling, klikt u op **regel toevoegen** > **apparaat categorie regel**.
2.  In de **apparaat categorie lidmaatschapsregel maken** dialoogvenster Selecteer de categorie die wordt toegepast op alle apparaten in de verzameling.
3.  Sluit de **apparaat categorie lidmaatschapsregel maken** in het dialoogvenster en het dialoogvenster Eigenschappen van verzameling.

### <a name="change-the-category-of-a-device"></a>De categorie van een apparaat wijzigen
1.  In de **activa en naleving** werkruimte van de Configuration Manager-console, vouw **overzicht**, klikt u vervolgens op **apparaten**.
2.  Selecteer een apparaat van de **apparaten** lijst en klikt u op de **Start** tabblad, in de **apparaat** groep, klikt u op **Wijzigingscategorie**.
3.  In de **apparaatcategorie bewerken** dialoogvenster vak, kiest u de categorie die van toepassing op dit apparaat en klik vervolgens op **OK**.

## <a name="dmp_grace"></a>Respijtperiode afdwingen voor vereiste toepassingen en software-update-implementaties

In sommige gevallen kunt u gebruikers meer tijd te geven tot implementaties van toepassingen installeren die zijn vereist of software-updates buiten een deadlines die u hebt geconfigureerd. Dit kan doorgaans zijn vereist wanneer een computer gedurende langere tijd is uitgeschakeld en moet voor het installeren van een groot aantal toepassing of update-implementaties.
Als een eindgebruiker is alleen van vakantie geretourneerd, moeten ze mogelijk lang wachten terwijl als achterstallig toepassing implementaties zijn geïnstalleerd.
U kunt nu een respijtperiode afdwingen door Configuration Manager-clientinstellingen implementeren naar een verzameling om dit probleem op te lossen definiëren.

### <a name="try-it-out"></a>Probeer het nu!

Voor het configureren van de respijtperiode is, moet u de volgende acties uitvoeren:

1.  Op de **Computeragent** pagina configureren van clientinstellingen, de nieuwe eigenschap **respijtperiode voor afdwingen na de implementatie (uren) deadline** met een waarde tussen **1** en **120** uur.
2.  In een nieuwe implementatie van de vereiste toepassing of in de eigenschappen van een bestaande implementatie op de **planning** pagina, selecteert u het selectievakje **afdwingen van deze implementatie op basis van gebruikersvoorkeuren uitstellen**, tot de respijtperiode die in de clientinstellingen is gedefinieerd.
Alle implementaties die dit selectievakje ingeschakeld hebben en die gericht zijn op apparaten die u ook de client-instelling geïmplementeerd gebruikt de respijtperiode voor afdwinging.

Als u een respijtperiode afdwingen configureren en schakel het selectievakje in als de deadline van de installatie van de toepassing is bereikt, wordt deze geïnstalleerd in het eerste niet-zakelijk venster die de gebruiker tot die respijtperiode geconfigureerd. De gebruiker kan echter nog steeds openen van Software Center en de toepassing op elk gewenst moment die ze willen installeren. Nadat de respijtperiode is verlopen, hersteld afdwinging normaal gedrag voor implementaties van achterstallige.
Soortgelijke opties zijn toegevoegd aan de wizard voor implementatie van software-updates, de wizard regels automatische implementatie en eigenschappenpagina's.

##  <a name="dmp_devg"></a>Configuration Manager gebruiken als een beheerd installatieprogramma met Device Guard

Device Guard is een Windows 10-functie die gebruikmaakt van hardware en software-onderdelen strikt bepalen wat mag worden uitgevoerd op het apparaat.

U kunt een gedetailleerd overzicht van wat Device Guard doet en hoe het werkt op lezen [dit Technet-artikel](https://technet.microsoft.com/itpro/windows/whats-new/device-guard-overview).

In deze release Configuration Manager kunnen samenwerken met Device Guard en [Windows AppLocker](https://technet.microsoft.com/library/dd723678(v=ws.10).aspx) zodat uitvoerbaar bestand en dll-bestanden die zijn geïmplementeerd met Configuration Manager automatisch vertrouwde zijn als ze afkomstig van een beheerd installatieprogramma zijn, wat betekent dat ze mag worden uitgevoerd op het doelapparaat en andere software niet mag worden uitgevoerd, tenzij expliciet mag worden uitgevoerd door andere AppLocker-regels.  

Deze mogelijkheid is momenteel niet worden geconfigureerd vanuit de Configuration Manager-console. Om het beleid te configureren, moet u een registersleutel configureren op elke client en Windows-services configureren op de client.
Zodra dit is gebeurd, configureert u het bestand met beleidsregel van AppLocker. Nadat u het beleidsbestand dat u hebt geconfigureerd, kunt u deze kunt implementeren op apparaten compatibele client.


Net als alle AppLocker-beleidsregels kunnen beleidsregels met beheerd installatieprogramma regels uitvoeren in twee modi:

- De controlemodus – toepassingen zijn opmerking niet worden uitgevoerd, maar alle toepassingen die zijn geblokkeerd worden gerapporteerd in een logboekbestand (dit wordt ondersteund in een latere versie van Configuration Manager).
- Afdwinging ingeschakeld – toepassingen zijn geblokkeerd.

Meer informatie over het gebruik van Device Guard met Configuration Manager vindt u op de [Enterprise Mobility and Security blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/06/20/configmgr-as-a-managed-installer-with-win10).

Lees hier meer over:

- [Device Guard Inleiding](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [Device Guard certificering en naleving](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-certification-and-compliance)
- [Implementatiehandleiding voor Device Guard](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)

 ##  <a name="dmp_onprem"></a>Meerdere apparaatbeheerpunten voor On-premises Mobile Device Management  
 Met Technical Preview-1606 op\-premises Mobile Device Management (MDM) biedt ondersteuning voor een nieuwe functie in Windows 10 Verjaardag Update die u automatisch een ingeschreven apparaat configureert om meer dan één Apparaatbeheer wijst beschikbaar voor gebruik. Deze mogelijkheid staat toe dat het apparaat terugvallen op een ander apparaatbeheerpunt bij een die normale wordt gebruikt, niet beschikbaar is. Deze functie werkt alleen voor pc's met Windows 10 Verjaardag Update is geïnstalleerd.  

### <a name="try-it-out"></a>Probeer het nu!  

1.  Meer dan één beheerpunt voor apparaten in uw hiërarchie installeren.  

2.  Een apparaat met Windows 10 Verjaardag Update voor inschrijven op\-premises Mobile Device Management.  

Voor informatie over het voorbereiden van uw site en het inschrijven van apparaten voor op\-premises Mobile Device Management, Zie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

## <a name="cloud_proxy"></a>Cloudproxyservice voor het beheren van clients op het Internet

Cloudproxyservice biedt een eenvoudige manier voor het beheren van Configuration Manager-clients op Internet. De service, die wordt geïmplementeerd voor Microsoft Azure en een Azure-abonnement is vereist, maakt verbinding met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van de cloudproxyconnectorpunt. Zodra het is volledig geïmplementeerd en geconfigureerd, worden clients toegang kunnen krijgen tot lokale sitesysteemrollen van Configuration Manager ongeacht of ze zijn verbonden met het interne particuliere netwerk of op het Internet.

U kunt de Configuration Manager-console de service implementeren in Azure, rol van het cloud-proxy connector toevoegen en configureren van sitesysteemrollen voor cloud-proxy-verkeer. Cloudproxyservice ondersteunt momenteel alleen het beheerpunt, het distributiepunt en de software-update-punt rollen.

Clientcertificaten en Secure Socket Layer (SSL)-certificaten zijn vereist voor het verifiëren van computers en het versleutelen van communicatie tussen de verschillende lagen van de service. Clientcomputers ontvangen meestal een certificaat via Groepsbeleid worden afgedwongen. Voor het versleutelen van het verkeer tussen clients en de sitesysteemserver die als host fungeert voor de functies die u wilt maken van een aangepaste SSL-certificaat van de CA. Naast deze twee typen certificaten, nodig u ook instellen een beheercertificaat in Azure waarmee Configuration Manager Cloudproxyservice implementeren.  

### <a name="requirements-for-cloud-proxy-service-in-tp-1606"></a>Vereisten voor Cloudproxyservice in TP 1606
- Clientcomputers en de sitesysteemserver met de cloud-proxy connector punt.
- Aangepaste SSL-certificaten van de interne CA - gebruikt voor het versleutelen van communicatie van de clientcomputers en de identiteit van Cloudproxyservice verifiëren.
- Azure-abonnement voor cloudservices.
- Azure-beheercertificaat - gebruikt voor het verifiëren van Configuration Manager met Azure.

### <a name="limitations-of-cloud-proxy-service-in-tp-1606"></a>Beperkingen van Cloudproxyservice in TP 1606

- Ondersteunt alleen het beheerpunt, het distributiepunt en de software-update-punt rollen.
- Gebruikersbeleid worden niet ondersteund.
- Kan niet worden gebruikt met [On-premises Mobile Device Management](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) in Configuration Manager.
- Alleen ondersteund op de Azure openbare cloud-platform.


### <a name="try-it-out"></a>Probeer het nu!

Het proces voor het implementeren van Cloudproxyservice omvat de volgende stappen uit:

1. Maken en uitgeven van een aangepaste SSL-certificaat voor Cloudproxyservice.
1. Hoofdmap van het clientcertificaat exporteren.
2. Het management-certificaat uploaden naar Azure.
3. Cloudproxyservice instellen in de Configuration Manager-console.
4. Configureer de primaire site voor het gebruik van verificatie van clientcertificaten.
5. De cloudproxyconnectorpunt toevoegen aan uw site.
6. Configureer de sitesysteemrollen voor het accepteren van verkeer van de cloud-proxy.

De volgende secties bevatten meer informatie voor het uitvoeren van deze stappen.

#### <a name="create-a-custom-ssl-certificate"></a>Een aangepaste SSL-certificaat maken

U kunt een aangepaste SSL-certificaat voor Cloudproxyservice maken op dezelfde manier als die u dit voor een cloud-gebaseerd distributiepunt doen zou. Volg de instructies voor [het servicecertificaat voor Cloud-gebaseerde distributiepunten implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) maar anders de volgende dingen doen:

* Bij het instellen van de nieuwe certificaatsjabloon, geven **lezen** en **inschrijven** machtigingen aan de beveiligingsgroep die u hebt ingesteld voor Configuration Manager-servers.

#### <a name="export-the-client-certificates-root"></a>Hoofdmap van het clientcertificaat exporteren

De gemakkelijkste manier om te exporteren, de hoofdmap van de clientcertificaten gebruikt op het netwerk, opent u een certificaat op een van de domein-machines met een en dit te kopiëren.

>[!NOTE]
>Clientcertificaten zijn vereist op elke computer die u wilt beheren met Cloudproxyservice en op de sitesysteemserver die als host fungeert voor de cloudproxyconnector wordt gehost. Als u moet een certificaat toevoegen aan een van deze apparaten, Zie [implementeren van de Client-certificaat voor Windows-Computers](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012).

1. Typ in het venster uitvoeren **mmc** en drukt u op terug.
2. Klik in het menu bestand in de beheerconsole **module toevoegen/verwijderen...** .
3. Klik in het dialoogvenster Add of Remove-modules op **certificaten**, klikt u op **toevoegen >**, klikt u op **computeraccount**, klikt u op **volgende**, klikt u op **lokale computer**, en klik vervolgens op **voltooien**. Klik op **OK** om het dialoogvenster te sluiten.
4. Ga naar **certificaten > persoonlijke > Certificaten**.
5. Dubbelklik op het certificaat voor clientverificatie op de computer, klikt u op het tabblad certificeringspad en dubbelklikt u op de basiscertificeringsinstantie (aan de bovenkant van het pad).
6.  Klik op het tabblad met Details en klikt u op **kopiëren naar bestand...** .
7. Voltooi de Wizard Certificaat exporteren met behulp van de standaardindeling van het certificaat. Controleer de naam en locatie van het basiscertificaat dat u maakt. U hebt deze Cloudproxyservice in een later stadium te configureren.

#### <a name="upload-the-management-certificate-to-azure"></a>Het management-certificaat uploaden naar Azure

Een Azure-beheercertificaat is vereist voor Configuration Manager voor toegang tot de Azure-API en Cloudproxyservice configureren. Zie de volgende artikelen in de Azure-documentatie voor meer informatie en instructies voor het uploaden van een beheercertificaat:
- [Certificaten voor Azure Cloud Services-overzicht](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)
- [Een Azure Management API Management-certificaat uploaden](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/).

Zorg ervoor dat de abonnements-ID die is gekoppeld aan het beheercertificaat te kopiëren. U hebt deze voor het configureren van Cloudproxyservice in de Configuration Manager-console.

#### <a name="set-up-cloud-proxy-service"></a>Cloudproxyservice instellen

1. Ga in de Configuration Manager-console naar **beheer > Cloudservices > Cloudproxyservice**.
2. Klik op **Cloudproxyservice maken**.
3. In de Wizard Cloud maken Proxy-Service, Voer uw Azure-abonnement-ID (overgenomen van de Azure-beheerportal), klik op Bladeren en selecteer het certificaatbestand dat u gebruikt voor het uploaden als een Azure-beheercertificaat. Klik op **Volgende**. Wacht enige tijd voor de console verbinding maken met Azure.
4. Vul in de aanvullende informatie in de wizard:
    - Geef de persoonlijke sleutel (PFX-bestand) die u hebt geëxporteerd uit het aangepaste certificaat voor SSL.
    - Geef het basiscertificaat is geëxporteerd uit het clientcertificaat.
    - Geef de servicenaam dezelfde FQDN-naam die u hebt gebruikt toen u de nieuwe certificaatsjabloon gemaakt.
    - Schakel het selectievakje naast **certificaatintrekking Client controleren** (tenzij u uw CRL-gegevens openbaar publiceert).
    - Klik op **volgende** wanneer u klaar bent.
5. Controleer de instellingen en klik op **volgende**. Configuration Manager start instellen van de service. Wanneer de wizard is voltooid, klikt u op **sluiten**, maar het duurt tussen 5 tot 15 minuten voor het inrichten van de service volledig in Azure. Controleer de **Status** kolom voor de nieuwe installatie Cloudproxyservice om te bepalen wanneer de service is klaar.

#### <a name="configure-primary-site-for-client-certification-authentication"></a>Primaire site voor clientverificatie certificeringsinstantie configureren

1. Ga in de Configuration Manager-console naar **beheer > siteconfiguratie > Sites**.
2. Selecteer de primaire site voor de clients die u wilt beheren via Cloudproxyservice en klikt u op **eigenschappen**.
3. Op het tabblad clientcommunicatie voor de Computer van het eigenschappenvenster van de primaire site, schakel het selectievakje in naast **gebruik PKI-clientcertificaat (clientverificatie) indien beschikbaar**.
4. Zorg ervoor dat u het selectievakje naast **Clients controleren de certificaatintrekkingslijst (CRL) voor sitesystemen**. Deze optie alleen zijn vereist als u uw CRL openbaar zijn publiceren.
5. Klik op **OK**.

#### <a name="add-the-cloud-proxy-connector-point"></a>De cloudproxyconnectorpunt toevoegen

De cloudproxyconnectorpunt is een nieuwe sitesysteemrol voor communicatie met Cloudproxyservice. Volg de instructies in als u wilt toevoegen de cloudproxyconnectorpunt, [sitesysteemrollen voor System Center Configuration Manager toevoegen](../../core/servers/deploy/configure/add-site-system-roles.md).

#### <a name="configure-roles-for-cloud-proxy-traffic"></a>Rollen voor verkeer van de cloud-proxy configureren

De laatste stap bij het instellen van Cloudproxyservice is voor het configureren van de sitesysteemrollen voor het accepteren van verkeer van de cloud-proxy. Voor technische Preview 1606 is worden alleen van toepassing op het beheerpunt, distributiepunt en software-update-punt functies ondersteund voor Cloudproxyservice. U moet elke rol afzonderlijk configureren.

1. Ga in de Configuration Manager-console naar **beheer > siteconfiguratie > Servers en sitesysteemrollen**.
2. Klik op de sitesysteemserver voor de rol die u wilt configureren voor verkeer van de cloud-proxy.
3. Klik op de rol en klik vervolgens op **eigenschappen**.
4. Kies in het eigenschappenvenster rol onder-clientverbindingen, **HTTPS**, schakel het selectievakje in naast **proxyservice van Configuration Manager Cloud toestaan verkeer**, en klik vervolgens op **OK**. Herhaal deze stappen voor de overige rollen.

#### <a name="check-status-on-a-client-on-the-internet"></a>Controleer de status op een client op Internet

Nadat de service en -rollen zijn volledig geconfigureerd, ontvangt de interne clients de locatie van Cloudproxyservice bij de volgende locatie-aanvraag. Clients met informatie over de bijgewerkte locatie kunnen vervolgens met Configuration Manager op het Internet communiceren. De polling-cyclus voor verzoeken om de locatie is om de 24 uur. Als u niet wilt wachten tot de aanvraag normaal geplande locatie, dwingt u de aanvraag door de SMS Agent Host-service (ccmexec.exe) op de computer opnieuw te starten.

Nadat clients de nieuwe locatie-informatie voor Cloudproxyservice hebben, Controleer de status van clients die niet langer in het interne particuliere netwerk, maar hebben toegang tot Internet. U kunt ook verkeer op Cloudproxyservice controleren door te gaan naar **beheer > Cloudservices > Cloudproxyservice**, de service in het lijstdeelvenster selecteren en gegevens weergeven in het detaildeelvenster.   

## <a name="manage_o365"></a>De Office 365-clientagent in Configuration Manager beheren  

Vanaf Technical Preview 1606, kunt u een Configuration Manager clientagentinstelling, in plaats van Groepsbeleid, zodat Office 365-clients om updates te ontvangen van Configuration Manager gebruiken. Nadat u deze instelling configureren en implementeren van updates voor Office 365, wordt de clientagent voor Configuration Manager-communiceert met de Office 365-clientagent voor Office 365-updates vanaf een distributiepunt downloaden en te installeren. Configuration Manager ook inventarisatie van de clientagent instellen.

Zie voor meer informatie [beheren van Office 365 ProPlus-updates](https://technet.microsoft.com/library/mt741983.aspx).

### <a name="set-the-configuration-manager-client-setting-to-manage-the-office-365-client-agent"></a>De Configuration Manager-client instellen voor het beheren van de Office 365-clientagent instellen
1.  Klik in de Configuration Manager-console op **beheer** > **overzicht** > **clientinstellingen**.
2. Open de juiste apparaatstuurprogramma-instellingen voor de clientagent. Zie voor meer informatie over standaard en aangepaste clientinstellingen [het configureren van clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).
3. Klik op **Software-Updates** en selecteer **Ja** voor de **beheer van de Office 365-Clientagent inschakelen** instelling.  


## <a name="osdpreservedriveletter"></a>De takenreeksvariabele OSDPreserveDriveLetter is afgeschaft.
De takenreeksvariabele OSDPreserveDriveLetter bepaalt of de takenreeks de stationsletter, vastgelegd in het WIM-bestand van het besturingssysteem, wanneer die installatiekopie wordt toegepast op een doelcomputer gebruikt.
- Deze takenreeksvariabele is afgeschaft in Technical Preview 1606.

Tijdens de implementatie van een besturingssysteem bepaalt standaard Windows Setup nu de beste stationsletter te gebruiken (meestal C:). Als u opgeven van een ander station moet worden gebruikt wilt, kunt u de locatie van de takenreeksstap besturingssysteem toepassen. Ga naar de **selecteert u de locatie waar u wilt toepassen van dit besturingssysteem** optie **logische stationsletter opgeven**, en kies het station dat u wilt gebruiken. Er moet een station dat is toegewezen met de letter die u op de doelcomputer kiest. 

## <a name="updatesandservicing"></a>Wijzigingen voor het knooppunt Updates en onderhoud
Technische Preview-versie 1606 enkele wijzigingen zijn uitgevoerd die betrekking hebben op Updates en onderhoud in de Configuration Manager-console:
- **Wijziging van knooppunt:**

    In de **bewaking** werkruimte de **Site Servicing status** knooppunt is gewijzigd in **Updates en onderhoudsstatus**.
- **Meer installatiestatus:**

    Wanneer u de installatiestatus van de update voor een site bekijkt, geeft de console nu afzonderlijke details voor de volgende acties:
    - **Download** (dit geldt alleen voor de bovenste site waarop de service connection point-sitesysteemrol is geïnstalleerd)
    - **Replicatie**
    - **Controle van vereisten**
    - **Installatie**

  Bovendien is nu meer gedetailleerde informatie voor elke stap, zoals in het logboekbestand dat die u kunt bekijken voor meer informatie.  
-   **Nieuwe optie om opnieuw te proberen de vereiste fouten:**

    In zowel de **beheer** en **bewaking** werkruimten, de **Updates en onderhoud** knooppunt bevat een nieuwe knop in het lint genaamd **waarschuwingen over vereisten negeren**.

    Wanneer u updates installeert zonder de optie voor het negeren van waarschuwingen voor vereisten (van in de Wizard Updates), en dat de installatie van de update met de melding van stopt **waarschuwingen voor vereisten**, kunt u selecteren **waarschuwingen over vereisten negeren** vanuit het lint voor het activeren van een automatische voortzetting van die update-installatie die de waarschuwingen voor vereisten worden genegeerd.  



- **Schonere weergave van updates:**

    Wanneer u bekijkt de **Updates en onderhoud** knooppunt nu ziet u alleen de laatst geïnstalleerde update en er nieuwe updates die beschikbaar zijn voor u installeren. U kunt eerder geïnstalleerde updates u op de nieuwe **geschiedenis** knop die wordt weergegeven in het lint.  

-   **Nieuwe naam optie voor preproductie:**

    In het knooppunt Updates en onderhoud, de knop Wat is de naam **clientopties** is nu gewijzigd in **promoveren pre-Productieclient**.
