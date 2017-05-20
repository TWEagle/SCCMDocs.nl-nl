---
title: Mogelijkheden in Technical Preview 1606 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1606.
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
caps.latest.revision: 31
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7cb553d553a1d2e3118731118a566c38e7b4e161
ms.openlocfilehash: 08747ca981f6697e2bd621afe5df0e3bd06b332d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1606-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1606 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1606 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    

**Bekende problemen in deze Technical Preview:**  
*  Wanneer u een van Technical Preview 1604-1605 en vervolgens naar versie 1606 update, de update mislukken kan en een vergelijkbaar met de volgende fout is vastgelegd in de **cmupdate.log**:

       ERROR: Failed to execute SQL Server command:  ~ ~-- Create site boundary group ~IF  dbo.fnIsCasOrStandalonePrimary() = 1 ~BEGIN ~   PRINT N'Create site boundary group during upgrade' ~   EXEC dbo.spBuildDefaultBoundaryGroups @UserName = N'SYSTEM' ~END          

    Als dit gebeurt in de **Updates en onderhoud** knooppunt Klik **controleren op updates**, en vervolgens **probeer** installatie van de update.
    ***

**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  

## <a name="dmp_category"></a>Apparaten automatisch categoriseren in verzamelingen
Categorieën voor apparaatstuurprogramma die kunnen worden gebruikt om apparaten automatisch plaats in apparaatverzamelingen als u de Configuration Manager met Microsoft Intune gebruikt, kunt u maken. Vervolgens moeten gebruikers een apparaatcategorie kiezen wanneer ze een apparaat in Intune inschrijft. Bovendien kunt u de categorie van een apparaat wijzigen van de Configuration Manager-console.

**Belangrijk:** Deze functie werkt met de **juni 2016** versie van Microsoft Intune. Zorg ervoor dat u hebt bijgewerkt naar deze versie voordat u deze procedures uitproberen.

### <a name="try-it-out"></a>Probeer het nu!

### <a name="create-a-set-of-device-categories"></a>Maken van een aantal categorieën voor apparaatstuurprogramma
1.  In de **activa en naleving** werkruimte van de Configuration Manager-console, vouw **overzicht**, klikt u vervolgens op **Apparaatverzamelingen**.
2.  Op de **Start** tabblad, in de **categorieën** groep, klikt u op **categorieën voor apparaatstuurprogramma beheren**.
3.  In de **categorieën voor apparaatstuurprogramma beheren** in het dialoogvenster maken, bewerken of verwijderen van categorieën. Maak een nieuwe categorie.

### <a name="associate-a-collection-with-a-device-category"></a>Een verzameling koppelen aan een apparaatcategorie
Wanneer u een verzameling aan een apparaatcategorie koppelen, worden alle apparaten in de categorie die u opgeeft worden toegevoegd aan deze verzameling.
1.  In de **eigenschappen** dialoogvenster voor de apparaatverzameling van een, klikt u op **regel toevoegen** > **apparaat categorie regel**.
2.  In de **apparaat categorie lidmaatschapsregel maken** dialoogvenster de categorie die wordt toegepast op alle apparaten in de verzameling te selecteren.
3.  Sluit de **apparaat categorie lidmaatschapsregel maken** in het dialoogvenster en het dialoogvenster Eigenschappen van verzameling.

### <a name="change-the-category-of-a-device"></a>De categorie van een apparaat wijzigen
1.  In de **activa en naleving** werkruimte van de Configuration Manager-console, vouw **overzicht**, klikt u vervolgens op **apparaten**.
2.  Selecteer een apparaat van de **apparaten** lijst en klik in de **Start** tabblad, in de **apparaat** groep, klikt u op **Wijzigingscategorie**.
3.  In de **bewerken apparaatcategorie** dialoogvenster kiest u de categorie die van toepassing op dit apparaat en klik vervolgens op **OK**.

## <a name="dmp_grace"></a>Respijtperiode afdwinging voor vereiste toepassingen en software-update-implementaties

In sommige gevallen kunt u gebruikers meer tijd geven tot implementaties van toepassingen installeren die zijn vereist of software-updates buiten een deadlines die u hebt geconfigureerd. Dit kan meestal zijn vereist wanneer een computer gedurende langere tijd is uitgeschakeld en moet voor het installeren van een groot aantal toepassing of update-implementaties.
Als een eindgebruiker net van vakantie is geretourneerd, moeten ze mogelijk geduld voor een Long-waarde als achterstallig toepassing implementaties worden geïnstalleerd.
Om te helpen bij het oplossen van dit probleem, kunt u nu een respijtperiode afdwinging definiëren door de instellingen voor Configuration Manager-client implementeren op een verzameling.

### <a name="try-it-out"></a>Probeer het nu!

De respijtperiode configureren, moet u de volgende acties uitvoeren:

1.  Op de **Computeragent** pagina configureren van instellingen van de client de nieuwe eigenschap **respijtperiode voor afdwinging na implementatie deadline (uren)** met een waarde tussen **1** en **120** uur.
2.  In een nieuwe implementatie van de vereiste toepassing, of in de eigenschappen van een bestaande implementatie op de **planning** pagina, schakel het selectievakje **stellen afdwinging van deze implementatie volgens gebruikersvoorkeuren**, tot de respijtperiode gedefinieerd in de clientinstellingen.
De respijtperiode afdwinging maakt gebruik van alle implementaties die dit selectievakje geselecteerd en die zijn gericht op apparaten waarop u ook de instelling voor client geïmplementeerd.

Als u een respijtperiode afdwinging configureren en schakel het selectievakje in als de toepassing installeren deadline is bereikt, wordt deze geïnstalleerd in het eerste niet-business-venster dat de gebruiker tot die respijtperiode geconfigureerd. De gebruiker kan echter nog steeds Software Center wordt geopend en de toepassing op elk gewenst moment die ze willen installeren. Zodra de respijtperiode is verlopen, hersteld afdwinging normale gedrag voor achterstallige implementaties.
Vergelijkbare opties zijn toegevoegd aan de implementatiewizard van software-updates, de wizard Regels voor automatische implementatie en de pagina eigenschappen.

##  <a name="dmp_devg"></a>Met Configuration Manager als een beheerde installatieprogramma met apparaat-beveiliging

Apparaat-beveiliging is een functie van Windows 10 die gebruikmaakt van hardware en software-functies voor het beheren van strikt wat kan worden uitgevoerd op het apparaat.

U kunt een gedetailleerd overzicht van wat apparaat beveiligingsmethode doet en hoe het werkt op lezen [dit Technet-artikel](https://technet.microsoft.com/itpro/windows/whats-new/device-guard-overview).

In deze release Configuration Manager kunt samenwerken met de apparaat-beveiliging en [Windows AppLocker](https://technet.microsoft.com/library/dd723678(v=ws.10).aspx) dat executable en dll-bestanden die zijn geïmplementeerd met Configuration Manager automatisch vertrouwde afkomstig zijn uit een installatieprogramma beheerd zijn, wat betekent dat ze kunnen worden uitgevoerd op het doelapparaat en andere software niet uitgevoerd kunnen worden wanneer het expliciet is toegestaan om uit te voeren door andere AppLocker-regels.  

Deze mogelijkheid is momenteel niet worden geconfigureerd vanuit de Configuration Manager-console. Als het beleid wilt configureren, moet u een registersleutel te configureren op elke client en Windows-services configureren op de client.
Nadat u dit is gebeurd, configureert u het beleidsbestand AppLocker. Nadat u het bestand hebt geconfigureerd, kunt u deze kunt implementeren naar een compatibele client-apparaat.


Zoals alle AppLocker beleidsregels kunnen beleid met beheerde installatieprogramma regels uitvoeren in twee modi:

- Controlemodus – toepassingen zijn opmerking niet worden uitgevoerd, maar alle toepassingen die zijn geblokkeerd worden gerapporteerd in een logboekbestand (dit wordt ondersteund in een latere versie van Configuration Manager).
- Afdwinging ingeschakeld – toepassingen worden geblokkeerd niet kan worden uitgevoerd.

Meer informatie over het gebruik van apparaat-beveiliging met Configuration Manager vindt u op de [Enterprise Mobility en beveiliging blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/06/20/configmgr-as-a-managed-installer-with-win10).

Meer lezen:

- [Apparaat-beveiliging Inleiding](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [Apparaat-beveiliging certificeringsinstantie en naleving](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-certification-and-compliance)
- [Implementatiehandleiding voor apparaat-beveiliging](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)

 ##  <a name="dmp_onprem"></a>Meerdere apparaten beheerpunten voor On-premises mobiele apparaten beheren  
 Met de technische voorbeelden van 1606, op\-lokale Mobile Device Management (MDM) biedt ondersteuning voor een nieuwe functie in Windows 10 Verjaardag Update die wordt automatisch geconfigureerd op een geregistreerde apparaat om meer dan één Apparaatbeheer wijst beschikbaar voor gebruik. Deze mogelijkheid kunt het apparaat terugval naar een ander apparaatbeheerpunt wanneer de die normale hierbij niet beschikbaar is. Deze functie werkt alleen voor computers met Windows 10 Verjaardag Update is geïnstalleerd.  

### <a name="try-it-out"></a>Probeer het nu!  

1.  Meer dan één beheerpunt voor apparaten in uw hiërarchie installeren.  

2.  Voor een Update voor Windows 10 Verjaardag apparaat worden ingeschreven op\-premises beheer van mobiele apparaten.  

Voor informatie over het voorbereiden van uw site en -apparaten inschrijven voor op\-lokale beheer van mobiele apparaten, Zie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

## <a name="cloud_proxy"></a>Cloud-Proxy-Service voor het beheren van clients op het Internet

Cloud-Proxy-Service biedt een eenvoudige manier voor het beheren van Configuration Manager-clients op het Internet. De service die wordt geïmplementeerd op Microsoft Azure en een Azure-abonnement vereist, maakt verbinding met uw on-premises Configuration Manager-infrastructuur met behulp van een nieuwe rol met de naam van het cloud-proxypunt-connector. Zodra het is volledig geïmplementeerd en geconfigureerd, kunnen clients toegang tot lokale sitesysteemfuncties van Configuration Manager ongeacht of ze naar het interne particulier netwerk of op het Internet zijn verbonden is mogelijk.

U kunt de Configuration Manager-console de service implementeren in Azure, cloud proxy connector de rol voor het toevoegen en configureren van sitesysteemrollen voor cloud-proxy-verkeer. Cloud proxyservice ondersteunt momenteel alleen het beheerpunt, het distributiepunt en de software-update-punt rollen.

Clientcertificaten en Secure Socket Layer (SSL)-certificaten zijn vereist voor de verificatie van computers en het versleutelen van communicatie tussen de verschillende lagen van de service. Clientcomputers ontvangen doorgaans een clientcertificaat via beleidsafdwinging groep. Voor het versleutelen van het verkeer tussen clients en de sitesysteemserver die als host fungeert voor de functies, moet u een aangepaste SSL-certificaat maken vanuit de Certificeringsinstantie. Naast deze twee typen certificaten moet u ook instellen op Azure waarmee Configuration Manager voor het implementeren van Cloud-Proxy-Service kan een certificaat voor het beheren.  

### <a name="requirements-for-cloud-proxy-service-in-tp-1606"></a>Vereisten voor Cloud proxyservice in TP 1606
- Clientcomputers en de sitesysteemserver met de cloud-proxy-punt connector.
- Aangepaste SSL-certificaten van de interne Certificeringsinstantie - gebruikt voor het versleutelen van communicatie van clientcomputers en verifiëren van de identiteit van proxyservice van de Cloud.
- Azure-abonnement voor cloudservices.
- Azure-beheercertificaat - gebruikt voor het verifiëren van Configuration Manager met Azure.

### <a name="limitations-of-cloud-proxy-service-in-tp-1606"></a>Beperkingen van proxyservice van de Cloud in TP 1606

- Ondersteunt alleen het beheerpunt, het distributiepunt en de software-update-punt rollen.
- Gebruikersbeleid wordt niet ondersteund.
- Kan niet worden gebruikt met [On-premises Mobile Device Management](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) in Configuration Manager.
- Alleen ondersteund op de Azure openbare cloudplatform.


### <a name="try-it-out"></a>Probeer het nu!

Het proces voor het implementeren van Cloud-Proxy-Service omvat de volgende stappen uit:

1. Maken en uitgeven van een aangepaste SSL-certificaat voor Cloud-Proxy-Service.
1. Exporteer de hoofdmap van het clientcertificaat.
2. Upload het beheercerticaat naar Azure.
3. Cloud-Proxy-Service instellen in de Configuration Manager-console.
4. De primaire site configureren voor het gebruik van verificatie van clientcertificaten.
5. Connector proxypunt voor de cloud toevoegen aan uw site.
6. Configureer de sitesysteemrollen voor het accepteren van cloud-proxy-verkeer.

De volgende secties bevatten meer informatie over deze stappen uit te voeren.

#### <a name="create-a-custom-ssl-certificate"></a>Maak een aangepaste SSL-certificaat

U kunt een aangepaste SSL-certificaat maken voor Cloud-Proxy-Service op dezelfde manier als die u dit voor een cloud-gebaseerde distributiepunt doen zou. Volg de instructies voor [het servicecertificaat voor Cloud-gebaseerde distributiepunten implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) maar anders de volgende dingen doen:

* Bij het instellen van de nieuwe certificaatsjabloon, geven **lezen** en **inschrijven** verlenen aan de beveiligingsgroep die u voor Configuration Manager-servers instelt.

#### <a name="export-the-client-certificates-root"></a>Het clientcertificaat root exporteren

De eenvoudigste manier om op te halen exporteren de hoofdmap van de clientcertificaten in het netwerk gebruikt, opent u een clientcertificaat op een van de domein-machines met een en kopieert u deze.

>[!NOTE]
>Clientcertificaten vereist zijn op elke computer die u wilt beheren met Cloud-Proxy-Service en wijs op de sitesysteemserver die als host fungeert voor de cloud-proxy-connector. Als u toevoegen van een clientcertificaat aan elk van deze virtuele machines wilt, Zie [implementeren van het certificaat voor Windows clientcomputers](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012).

1. Typ in het venster uitvoeren **mmc** en op Return drukt.
2. Klik op het menu bestand in de beheerconsole **module toevoegen/verwijderen...** .
3. Klik in het dialoogvenster Remove-modules **certificaten**, klikt u op **toevoegen >**, klikt u op **computeraccount**, klikt u op **volgende**, klikt u op **lokale computer**, en klik vervolgens op **voltooien**. Klik op **OK** om het dialoogvenster te sluiten.
4. Ga naar **certificaten > persoonlijke > Certificaten**.
5. Dubbelklik op het certificaat voor clientverificatie op de computer, klikt u op het tabblad certificeringspad en dubbelklikt u op de basiscertificeringsinstantie (aan de bovenkant van het pad).
6.  Klik op het tabblad met Details en op **kopiëren naar bestand...** .
7. Voltooi de Wizard Certificaat exporteren met behulp van de standaardindeling voor het certificaat. Controleer de naam en locatie van het basiscertificaat dat u maakt. U moet deze Cloud proxyservice in een latere fase worden configureren.

#### <a name="upload-the-management-certificate-to-azure"></a>Upload het beheercerticaat naar Azure

Een Azure management-certificaat is vereist voor Configuratiebeheer voor toegang tot de Azure API en Cloudservice Proxy configureren. Zie de volgende artikelen in de Azure-documentatie voor meer informatie en instructies voor het uploaden van een management-certificaat:
- [Overzicht van de certificaten voor Azure Cloud Services](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)
- [Een Azure Management API Management-certificaat uploaden](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/).

Zorg ervoor dat de abonnements-ID die is gekoppeld aan het beheercertificaat te kopiëren. U moet deze voor het configureren van proxyservice van de Cloud in de Configuration Manager-console.

#### <a name="set-up-cloud-proxy-service"></a>Cloud-Proxy-Service instellen

1. Ga in de Configuration Manager-console naar **beheer > Cloudservices > Cloud proxyservice**.
2. Klik op **proxyservice Cloud maken**.
3. In de Wizard Cloud maken Proxy-Service, Voer uw Azure-abonnement-ID (overgenomen van de Azure-beheerportal), klikt u op Bladeren en selecteert u het certificaatbestand dat u gebruikt voor het uploaden van een Azure-beheercertificaat. Klik op **Volgende**. Wacht enige tijd voor de console verbinding maakt met Azure.
4. Vul de aanvullende gegevens in de wizard:
    - Geef de persoonlijke sleutel (PFX-bestand) dat u hebt geëxporteerd uit het aangepaste certificaat voor SSL.
    - Geef het basiscertificaat zijn geëxporteerd uit het clientcertificaat.
    - Geef de servicenaam dezelfde FQDN-naam die u hebt gebruikt toen u de nieuwe certificaatsjabloon gemaakt.
    - Schakel het selectievakje naast **certificaatintrekking Client controleren** (tenzij u uw gegevens CRL openbaar publiceert).
    - Klik op **volgende** als u klaar bent.
5. Controleer de instellingen en klik op **volgende**. Configuration Manager start instellen van de service. Wanneer de wizard is voltooid, klikt u op **sluiten**, maar het duurt tussen 5 tot 15 minuten voor de inrichting van de service volledig in Azure. Controleer de **Status** kolom voor de nieuwe installatie proxyservice Cloud om te bepalen wanneer de service is klaar.

#### <a name="configure-primary-site-for-client-certification-authentication"></a>Primaire site configureren voor verificatie van de certificeringsinstantie

1. Ga in de Configuration Manager-console naar **beheer > siteconfiguratie > Sites**.
2. Selecteer de primaire site van de clients die u wilt beheren via Cloud-Proxy-Service en klik op **eigenschappen**.
3. Op het tabblad clientcommunicatie voor de Computer van het eigenschappenvenster van de primaire site, schakel het selectievakje in naast **gebruik PKI-clientcertificaat (clientverificatie) indien beschikbaar**.
4. Zorg ervoor dat het selectievakje naast **Clients controleren de certificaatintrekkingslijst (CRL) voor site-systemen**. Deze optie kan alleen worden vereist als u uw CRL openbaar zijn publiceren.
5. Klik op **OK**.

#### <a name="add-the-cloud-proxy-connector-point"></a>Connector proxypunt voor de cloud toevoegen

Het cloud-proxypunt-connector is een nieuwe sitesysteemrol voor communicatie met Cloud-Proxy-Service. Volg de instructies in de cloud connector proxypunt toevoegen, [sitesysteemrollen toevoegen voor System Center Configuration Manager](../../core/servers/deploy/configure/add-site-system-roles.md).

#### <a name="configure-roles-for-cloud-proxy-traffic"></a>Rollen configureert voor cloud-proxy-verkeer

De laatste stap bij het instellen van proxyservice van de Cloud is voor het configureren van de sitesysteemrollen voor het accepteren van cloud-proxy-verkeer. Alleen de beheerpunt, het distributiepunt en het software-update-punt rollen voor technische Preview 1606 worden ondersteund voor Cloud-Proxy-Service. U moet elke rol afzonderlijk configureert.

1. Ga in de Configuration Manager-console naar **beheer > siteconfiguratie > Servers en sitesysteemrollen**.
2. Klik op de sitesysteemserver voor de rol die u wilt configureren voor cloud-proxy-verkeer.
3. Klik op de rol en klik vervolgens op **eigenschappen**.
4. Kies in het eigenschappenblad voor de rol, onder-clientverbindingen, **HTTPS**, schakel het selectievakje naast **proxyservice van Configuration Manager Cloud toestaan verkeer**, en klik vervolgens op **OK**. Herhaal deze stappen voor de resterende functies.

#### <a name="check-status-on-a-client-on-the-internet"></a>Controleer de status op een client op het Internet

Wanneer de service en de rollen zijn volledig geconfigureerd en ontvangen interne clients de locatie van Cloud-Proxy-Service op de volgende locatie-aanvraag. Clients met bijgewerkte locatiegegevens kunnen vervolgens communiceren met Configuration Manager op het Internet. De polling-cyclus voor verzoeken om locatie wordt elke 24 uur. Als u niet wilt wachten tot de aanvraag normaal geplande locatie, kunt u de aanvraag forceren door de SMS Agent Host-service (ccmexec.exe) op de computer opnieuw te starten.

Nadat clients de nieuwe locatie-informatie voor Proxy-Cloudservice hebben, Controleer de status van clients die zich niet meer op de interne particulier netwerk maar toegang tot Internet heeft. U kunt verkeer op Cloud proxyservice ook bewaken door te gaan naar **beheer > Cloudservices > Cloud proxyservice**, de service in het deelvenster met de lijst selecteren en gegevens weergeven in het detailvenster.   

## <a name="manage_o365"></a>De clientagent voor Office 365 in Configuration Manager beheren  

Technische Preview 1606 beginnen, kunt u een Configuration Manager clientagentinstelling, in plaats van Groepsbeleid, Office 365 clients toestaat te ontvangen van updates van Configuration Manager. Nadat u deze instelling niet configureren en implementeren van updates voor Office 365, wordt de Configuration Manager-clientagent communiceert met de clientagent voor Office 365 voor Office 365-updates downloaden van een distributiepunt en deze installeren. Configuration Manager ook inventarisatie van de clientagent instellen.

Zie voor meer informatie [Office 365 ProPlus beheren updates](https://technet.microsoft.com/library/mt741983.aspx).

### <a name="set-the-configuration-manager-client-setting-to-manage-the-office-365-client-agent"></a>De Configuration Manager-client instellen voor het beheren van de clientagent voor Office 365 instellen
1.  Klik in de Configuration Manager-console op **beheer** > **overzicht** > **clientinstellingen**.
2. Open de juiste apparaatstuurprogramma-instellingen voor de clientagent. Zie voor meer informatie over de standaardbeleidsregels en aangepaste clientinstellingen [clientinstellingen configureren in System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).
3. Klik op **Software-Updates** en selecteer **Ja** voor de **zodat het beheer van de Clientagent voor Office 365** instelling.  


## <a name="osdpreservedriveletter"></a>De OSDPreserveDriveLetter takenreeksvariabele is afgeschaft.
De OSDPreserveDriveLetter takenreeksvariabele bepaalt of de takenreeks de stationsaanduiding in het besturingssysteem WIM-bestand wanneer die installatiekopie wordt toegepast op een doelcomputer gebruikt.
- Deze takenreeksvariabele is afgeschaft in technische Preview 1606.

Tijdens de implementatie van een besturingssysteem bepaalt standaard Windows Setup nu de beste stationsletter (meestal C:) gebruiken. Als u opgeven van een ander station moet worden gebruikt wilt, kunt u de locatie van de takenreeksstap besturingssysteem toepassen. Ga naar de **selecteert u de locatie waar u dit besturingssysteem toepassen** stellen, selecteer **logische stationsletter opgeven**, en kies het station dat u wilt gebruiken. Er moet een station met de letter die u op de doelcomputer toegewezen. 

## <a name="updatesandservicing"></a>Wijzigingen voor de Updates en onderhoud knooppunt
Met de technische Preview 1606 zijn verscheidene wijzigingen geïntroduceerd die betrekking hebben op Updates en onderhoud in de Configuration Manager-console:
- **Wijziging van knooppunt:**

    In de **bewaking** werkruimte de **Site Servicing status** knooppunt is gewijzigd in **Updates en onderhoud Status**.
- **Meer installatiestatus:**

    Als u de installatiestatus van de update voor een site bekijkt, geeft de console nu afzonderlijke details voor de volgende acties:
    - **Download** (dit geldt alleen voor de bovenste site waarop de service connection point-sitesysteemrol is geïnstalleerd)
    - **Replicatie**
    - **Controle van vereisten**
    - **Installatie**

  Daarnaast is nu meer gedetailleerde informatie voor elke stap, inclusief in welke logboekbestand kunt u bekijken voor meer informatie.  
-   **Nieuwe optie om opnieuw te proberen de vereiste fouten:**

    In zowel de **beheer** en **bewaking** werkruimten, de **Updates en onderhoud** bevat een nieuwe knop in het lint met de naam van knooppunt **waarschuwingen voor vereisten negeren**.

    Wanneer u updates installeert zonder de optie waarschuwingen voor vereisten negeren (uit in de Wizard Updates), en dat de installatie van de update met een status van stopt **heeft waarschuwing**, kunt u selecteren **waarschuwingen voor vereisten negeren** van het lint voor het activeren van een automatische voortzetting van de update installatie die de waarschuwingen voor vereisten worden genegeerd.  



- **Schonere weergave van updates:**

    Wanneer u bekijkt de **Updates en onderhoud** knooppunt nu ziet u alleen de laatst geïnstalleerde update en er nieuwe updates die beschikbaar zijn voor u installeren. Eerder geïnstalleerde updates u Klik op de nieuwe **geschiedenis** knop die wordt weergegeven in het lint.  

-   **Nieuwe naam optie voor testomgeving:**

    In de Updates en onderhoud van knooppunt de knop Wat is de naam **opties voor de Client** is nu gewijzigd in **bevorderen pre-Productieclient**.

