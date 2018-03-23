---
title: Beheergateway voor cloud instellen
titleSuffix: System Center Configuration Manager
description: Gebruik deze stapsgewijze procedure voor het instellen van een cloud management gateway (CMG).
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.openlocfilehash: fb2a44897064e88f7ab6fd4f4b293520f54f1db7
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>Instellen van de cloud management gateway voor Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*  

Dit proces bevat de stappen die nodig zijn voor het instellen van een cloud management gateway (CMG). 

> [!Tip]
> Deze functie is geïntroduceerd in versie 1610 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1802, deze functie is niet langer een voorlopige versie.



## <a name="before-you-begin"></a>Voordat u begint

Lees het artikel eerst [plannen voor cloud-beheergateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway). Dit artikel gebruiken om te bepalen van uw ontwerp CMG. 

Gebruik de volgende controlelijst om ervoor te zorgen dat u hebt de benodigde informatie en vereisten voor het maken van een CMG:  

- De Azure-omgeving te gebruiken. De openbare Azure-Cloud of het Azure US Government-Cloud.  

- U moet een of meer certificaten voor CMG, afhankelijk van uw ontwerp. Zie voor meer informatie [certificaten voor beheer cloudgateway](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway).  

- Vanaf versie 1802, kies of u gebruikt de **Azure Resource Manager-implementatie** of een **klassieke service-implementatie**. Zie voor meer informatie [Azure Resource Manager](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager). Voor een Azure Resource Manager-implementatie van CMG moet u de volgende vereisten:  

    - Integratie met [Azure AD](/sccm/core/servers/deploy/configure/azure-services-wizard) voor **Management Cloud**. Azure AD-gebruikersdetectie is niet vereist.  

    - Er moet een abonnementsbeheerder aan te melden.  

- Voor een klassieke service-implementatie van CMG moet u de volgende vereisten:  

    - Azure-abonnement-ID  

    - Azure-beheercertificaat  

- Een globaal unieke naam voor de service. Deze naam is van de [certificaat voor serververificatie CMG](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-server-authentication-certificate).  

- De Azure-regio voor deze implementatie CMG.  

- Hoeveel exemplaren van de virtuele machine moet u voor de schaal en redundantie.  



## <a name="set-up-a-cmg"></a>Een CMG instellen

Deze procedure uitvoeren op het hoogste niveau. Deze site is een zelfstandige primaire site of de centrale beheersite.

1. Ga in de Configuration Manager-console naar de **beheer** werkruimte Vouw **Cloudservices**, en selecteer **Cloud Management Gateway**.  

2. Klik op **Cloud Management-Gateway maken** in het lint.  

3. Vanaf versie 1802, op de pagina Algemeen van de wizard eerst de implementatiemethode CMG kiezen **Azure Resource Manager-implementatie** of **klassieke service-implementatie**.  

    1. Voor de **Azure Resource Manager-implementatie**: Klik op **aanmelden** voor verificatie met een administrator-account Azure-abonnement. De wizard wordt automatisch gevuld de overige velden van de informatie opgeslagen tijdens de vereiste van Azure AD-integratie. Als u meerdere abonnementen eigenaar, selecteert u de **abonnements-ID** van het gewenste abonnement gebruiken.  

    2. Voor de **klassieke service-implementatie**, *en Configuration Manager-versies 1706 en 1710*: Voer uw Azure **abonnements-ID**. Klik vervolgens op **Bladeren** en selecteer de. PFX-bestand voor het Azure-beheercertificaat. 

4. Geef de **Azure-omgeving** voor deze CMG. De opties in de vervolgkeuzelijst kunnen variëren, afhankelijk van de methode-implementatie.  

5. Klik op **Volgende**. Wacht terwijl de site test u de verbinding met Azure.  

4. Klik op de pagina instellingen van de wizard eerst op **Bladeren** en selecteer de. PFX-bestand voor het certificaat voor serververificatie CMG. De naam van dit certificaat wordt de vereiste gevuld **Service FQDN** en **servicenaam** velden.  

   > [!NOTE]  
   > Vanaf versie 1802, ondersteunt het certificaat voor serververificatie CMG jokertekens. Als u een jokertekencertificaat gebruikt, vervangt u het sterretje (\*) in de **Service FQDN** veld met de gewenste hostnaam voor de CMG.  
   <!--491233-->  

5. Klik op de **regio** vervolgkeuzelijst de Azure-regio kiezen voor deze CMG.  

6. In versie 1802 en er wordt met behulp van een Azure Resource Manager-implementatie selecteert een **resourcegroep** optie. 
   1. Als u ervoor kiest **gebruik bestaande**, selecteert u een bestaande resourcegroep uit de vervolgkeuzelijst.
   2. Als u ervoor kiest **nieuw**, voert u de naam van de nieuwe resourcegroep.

6. In de **VM-instantie** en voer het aantal VM's voor deze service. De standaardwaarde is een, maar u kunt maximaal 16 virtuele machines per CMG schalen.  

7. Klik op **certificaten** client vertrouwde basiscertificaten toevoegen. Toevoegen maximaal twee vertrouwde basis-CA's en vier tussenliggende (onderliggende) CA's.  

8. Standaard maakt de wizard de optie voor het **certificaatintrekking Client controleren**. Een certificaatintrekkingslijst (CRL) moet openbaar zijn gepubliceerd voor deze verificatie werkt. Als u een CRL niet publiceert doen, moet u deze optie uitschakelt.  

9. Klik op **Volgende**.  

10. Kies het selectievakje in om in te schakelen drempelwaarde voor waarschuwing voor het bewaken van CMG verkeer met een drempelwaarde 14 dagen. Geef vervolgens de drempelwaarde en het percentage waarmee de verschillende waarschuwingsniveaus verhogen. Kies **volgende** wanneer u klaar bent.  

11. Controleer de instellingen en kies **volgende**. Configuration Manager start instellen van de service. Nadat u de wizard sluit, duurt het tussen vijf tot 15 minuten voor het inrichten van de service volledig in Azure. Controleer de **Status** kolom voor de nieuwe CMG om te bepalen wanneer de service is klaar.  

 > [!Note]  
 > Gebruiken om op te lossen CMG implementaties, **CloudMgr.log** en **CMGSetup.log**. Zie voor meer informatie [logboekbestanden](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).



## <a name="configure-primary-site-for-client-certificate-authentication"></a>Primaire site configureren voor verificatie van clientcertificaten

Als u [certificaten voor clientverificatie](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#client-authentication-certificate) voor clients te verifiëren met de CMG, volgt u deze procedure voor het configureren van elke primaire site.  

1. Ga in de Configuration Manager-console naar de **beheer** werkruimte Vouw **siteconfiguratie**, en selecteer **Sites**.  

2. Selecteer de primaire site waarnaar uw op internet gebaseerde clients zijn toegewezen en kies **eigenschappen**.  

3. Overschakelen naar de **Computer clientcommunicatie** tabblad van het eigenschappenvenster voor een primaire site, zoals controle **gebruik PKI-clientcertificaat (clientverificatie) indien beschikbaar**.  

4. Als u geen CRL uitgeven bent, schakelt u de optie voor **Clients controleren de certificaatintrekkingslijst (CRL) voor sitesystemen**.  



## <a name="add-the-cmg-connection-point"></a>Het verbindingspunt CMG toevoegen

Het verbindingspunt CMG is de sitesysteemrol voor communicatie met de CMG. Als u wilt toevoegen op het verbindingspunt CMG, volgt u de algemene instructies voor het [sitesysteemrollen installeren](/sccm/core/servers/deploy/configure/install-site-system-roles). Selecteer op de pagina Systeemrolselectie van de rol Wizard toevoegen **Cloudverbindingspunt management gateway**. Selecteer vervolgens de **cloudnaam management gateway** waarmee deze server verbinding kan maken. De wizard geeft de regio voor de geselecteerde CMG. 

> [!Important]
> Het verbindingspunt CMG moet hebben een [certificaat voor clientverificatie](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#client-authentication-certificate) in sommige scenario's. 

 > [!Note]  
 > Gebruiken voor het oplossen van de servicestatus CMG **CMGService.log** en **SMS_Cloud_ProxyConnector.log**. Zie voor meer informatie [logboekbestanden](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).



## <a name="configure-client-facing-roles-for-cmg-traffic"></a>Rollen voor CMG verkeer clientgerichte configureren

Configureer de punt- en software-update beheerpuntsitesystemen voor het accepteren van CMG verkeer. Deze procedure uitvoeren op de primaire site voor alle beheerpunten en software-updatepunten die clients op internet.  

1. Ga in de Configuration Manager-console naar de **beheer** werkruimte Vouw **siteconfiguratie**, met de rechtermuisknop op **Servers en sitesysteemrollen**, en selecteer **Beheerpunt** uit de lijst.  

2. Selecteer de sitesysteemserver die u wilt configureren voor CMG verkeer. Selecteer de **beheerpunt** rol in het deelvenster met details en klik op **eigenschappen** in het lint.  

3. In het Management-punt eigenschappenvenster onder clientverbindingen, schakel het selectievakje in naast **Configuration Manager toestaan cloud beheerverkeer gateway**. 
    - Afhankelijk van uw ontwerp CMG en Configuration Manager-versie, mogelijk moet u inschakelen de **HTTPS** optie. Zie voor meer informatie [beheerpunt inschakelen voor HTTPS](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#enable-management-point-for-https).  

4. Klik op **OK**.   

Herhaal deze stappen voor extra beheerpunten naar behoefte, en voor alle software-updatepunten. 



## <a name="configure-clients-for-cmg"></a>Clients configureren voor CMG

Zodra de CMG en de sitesysteemrollen worden uitgevoerd, krijgen clients de locatie van de service CMG automatisch op de volgende locatie-aanvraag. Clients moeten zich op het intranet te ontvangen van de locatie van de service CMG, tenzij u [installeren en Windows 10-clients die gebruikmaken van Azure AD voor verificatie toe te wijzen](/sccm/core/clients/deploy/deploy-clients-cmg-azure). De polling-cyclus voor verzoeken om de locatie is om de 24 uur. Als u niet wilt wachten tot de aanvraag normaal geplande locatie, dwingt u de aanvraag door de SMS Agent Host-service (ccmexec.exe) op de computer opnieuw te starten.  

> [!Note]
> Standaard ontvangen alle clients CMG beleid. Dit gedrag beheren met de clientinstelling [inschakelen voor clients gebruiken een cloud management gateway](/sccm/core/clients/deploy/about-client-settings#enable-clients-to-use-a-cloud-management-gateway).

Configuration Manager-client wordt automatisch bepaald of het is op het intranet of internet. Als de client contact opneemt met een domeincontroller of een on-premises beheer punt, stelt deze in het verbindingstype **momenteel intranet**. Anders wordt deze verandert in een **momenteel Internet**, en de locatie van de service CMG gebruikt om te communiceren met de site.

>[!NOTE]
> U kunt afdwingen dat de client gebruikt altijd de CMG ongeacht of het op het intranet of internet. Dit is handig voor testdoeleinden of voor clients op externe filialen die u wilt de CMG gebruiken. De volgende registersleutel op de client ingesteld:
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`
>
> U kunt ook opgeven met deze instelling tijdens de installatie met client de [CCMALWAYSINF](/sccm/core/clients/deploy/about-client-installation-properties#ccmalwaysinf) eigenschap.

Open een Windows PowerShell-opdrachtprompt als beheerder op de clientcomputer om te controleren dat clients het beleid opgeven van de CMG hebben, en voer de volgende opdracht: `Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}`

Deze opdracht geeft internetgebaseerde beheerpunten die de client op de hoogte. Hoewel de CMG niet technisch een internet-gebaseerd beheerpunt bevindt, wordt deze weergegeven als zodanig aan clients.

 > [!Note]  
 > Gebruik voor het oplossen van CMG clientverkeer **CMGHttpHandler.log**, **CMGService.log**, en **SMS_Cloud_ProxyConnector.log**. Zie voor meer informatie [logboekbestanden](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).



## <a name="modify-a-cmg"></a>Een CMG wijzigen

Nadat een CMG is gemaakt, kunt u enkele van de instellingen wijzigen. Selecteer de CMG in de Configuration Manager-console en klik op **eigenschappen**. De volgende instellingen worden geconfigureerd:  

- **Algemeen**  

    - **Azure-beheercertificaat**: het Azure-beheercertificaat voor de CMG wijzigen. Deze optie is handig bij het bijwerken van het certificaat voordat deze verloopt.  

- **Instellingen**  

    - **Certificaatbestand**: het certificaat voor serververificatie voor de CMG wijzigen. Deze optie is handig bij het bijwerken van het certificaat voordat deze verloopt.  

    - **VM-instantie**: Wijzig het aantal virtuele machines die de service in Azure gebruikt. Deze instelling kunt u de service dynamisch omhoog of omlaag op basis van gebruik of kosten overwegingen schalen.  

    - **Certificaten**: vertrouwde basis- of tussenliggende CA-certificaten toevoegen of verwijderen. Deze optie is handig bij het toevoegen van nieuwe CA's of buiten gebruik stellen van verlopen certificaten.  

    - **Controleer of de Client certificaatintrekking**: als u niet hebt oorspronkelijk ingeschakeld met deze instelling bij het maken van de CMG, kunt u dit inschakelen daarna zodra u de CRL publiceren.  

- **Waarschuwingen**: u kunt de waarschuwingen configureren op elk gewenst moment nadat u de CMG hebt gemaakt. 

Meer belangrijke wijzigingen, zoals de volgende configuraties vereisen dat de service:
- Klassieke implementatiemethode in Azure Resource Manager
- Abonnement
- Servicenaam
- Persoonlijke tot openbare PKI
- Regio

Houd altijd ten minste één actieve CMG voor internet-clients bijgewerkte beleid kan ontvangen. Clients op Internet kunnen niet communiceren met een verwijderde CMG. Clients weet niet over een nieuwe totdat roaming terug naar het intranet. Bij het maken van een tweede exemplaar van de CMG om het verwijderen van de eerste, moet u ook een andere CMG verbindingspunt maken.

Beleid voor het vernieuwen van clients standaard elke 24 uur wachten zodat ten minste één dag na het maken van een nieuwe CMG voordat u de oude heeft verwijdert. Als clients zijn uitgeschakeld of zonder internetverbinding, moet u mogelijk langer wachten. 

Vanaf versie 1802, hebt u een bestaande CMG van de methode klassieke implementatie, moet u een nieuwe CMG voor het gebruik van de methode voor Azure Resource Manager-implementatie implementeren.<!--509753--> Er zijn twee opties:
- Als u gebruiken dezelfde service-naam wilt:
    1. De klassieke CMG, rekening houdend met de richtlijnen altijd voor internet-clients hebben ten minste één actieve CMG eerst verwijderen.
    2. Maak een nieuwe CMG met behulp van de implementatie van een Resource Manager. Hetzelfde serverauthenticatiecertificaat hergebruiken.
    3. Het verbindingspunt CMG voor het gebruik van het nieuwe CMG-exemplaar opnieuw te configureren.
- Als u gebruiken van een nieuwe servicenaam wilt:
    1. Maak een nieuwe CMG met behulp van de implementatie van een Resource Manager. Gebruik een nieuw certificaat voor serververificatie.
    2. Een nieuw CMG verbindingspunt en een koppeling maken met de nieuwe CMG.
    3. Wacht ten minste één dag voor internet-clients beleid over de nieuwe CMG kan ontvangen.
    4. De klassieke CMG verwijderen.

Alleen de CMG uit de Configuration Manager-console te wijzigen. Wijzigingen worden aangebracht aan de service of een onderliggende virtuele machines rechtstreeks in Azure wordt niet ondersteund. Eventuele wijzigingen zijn mogelijk verloren gegaan zonder kennisgeving worden gewijzigd. Net als bij een PaaS kan de service opnieuw opbouwen van de virtuele machines op elk gewenst moment. Deze opnieuw worden opgebouwd kunnen gebeuren bij onderhoud van de back-end-hardware, of updates toepassen op het besturingssysteem van de virtuele machine.

Als u verwijderen van de CMG wilt, ook doen vanuit de Configuration Manager-console. Handmatig verwijderen van alle onderdelen in Azure zorgt ervoor dat het systeem niet consistent zijn. Deze status blijft zwevende informatie en onverwachte problemen optreden. 



## <a name="next-steps"></a>Volgende stappen

- [Clients controleren voor cloud-beheergateway](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway)
- [Veelgestelde vragen over de cloud-management-gateway](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
