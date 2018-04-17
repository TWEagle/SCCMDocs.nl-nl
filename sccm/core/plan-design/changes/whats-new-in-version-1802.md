---
title: Nieuwe versie 1802
titleSuffix: Configuration Manager
description: Meer informatie over deze wijzigingen en nieuwe mogelijkheden die zijn geïntroduceerd in versie 1802 van Configuration Manager.
ms.custom: na
ms.date: 04/11/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5bd637b1-d7a1-411b-877a-c7aae9741173
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a667c34dc39ef0578ff840e5603080b09c67c63c
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="whats-new-in-version-1802-of-system-center-configuration-manager"></a>Wat is er nieuw in versie 1802 van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Update 1802 voor de huidige vertakking van Configuration Manager is beschikbaar als een update in de console. Deze update toepassen op de sites waarop versie 1702 1706 of 1710 uitgevoerd. <!-- baseline only statement: -->Als u een nieuwe site installeert, is het ook beschikbaar als basislijnversie.

Deze versie bevat naast de nieuwe functies ook extra wijzigingen zoals oplossingen voor problemen. Zie voor meer informatie [overzicht van wijzigingen in System Center Configuration Manager current branch versie 1802](https://support.microsoft.com/help/4101375).

<!--
The following additional updates to this release are also now available:
- [Update rollup for System Center Configuration Manager current branch, version 1710](https://support.microsoft.com/help/4057517)
-->

> [!TIP]  
> Een nieuwe site te installeren, moet u een basislijnversie van Configuration Manager.  
>
>  Meer informatie over:    
>   - [Nieuwe sites installeren](/sccm/core/servers/deploy/install/installing-sites)  
>   - [Updates installeren op sites](/sccm/core/servers/manage/updates)  
>   - [Basislijn- en updateversies](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

De volgende secties bevatten informatie over de wijzigingen en nieuwe mogelijkheden in versie 1802 van Configuration Manager.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated items](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated).

Version 1802 drops support for the following products:
-->


## <a name="site-infrastructure"></a>Site-infrastructuur

### <a name="reassign-distribution-point"></a>Opnieuw toewijzen van distributiepunt
<!-- 1306937 -->
Veel klanten hebben grote Configuration Manager-infrastructuur en vermindert primaire of secundaire sites voor het vereenvoudigen van hun omgeving. Nog steeds behouden moeten blijven distributiepunten op filialen inhoud voor beheerde clients bedienen. Deze distributiepunten bevatten vaak meerdere terabytes of meer van de inhoud. Deze inhoud is kost het veel tijd en netwerkbandbreedte te distribueren naar deze externe servers. Deze functie kunt u een distributiepunt naar een andere primaire site opnieuw toewijzen zonder de inhoud opnieuw distribueren. Met deze actie werkt de sitetoewijzing van het systeem tijdens het persistent maken van alle inhoud op de server. Zie voor meer informatie [een distributiepunt opnieuw toewijst](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_reassign).

### <a name="configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups"></a>Windows leveringsoptimalisatie voor het gebruik van Configuration Manager-grensgroepen configureren
<!-- 1324696 -->
U grensgroepen Configuration Manager gebruiken om te definiëren en inhoudsdistributie regelen tussen het bedrijfsnetwerk en naar externe kantoren. [Windows leveringsoptimalisatie](/windows/deployment/update/waas-delivery-optimization) is een cloud-gebaseerde, peer-to-peer-technologie voor het delen van inhoud tussen Windows 10-apparaten. U start in deze release, leveringsoptimalisatie voor het gebruik van uw grensgroepen bij het delen van inhoud tussen peers configureren. Een nieuwe client-instelling past de grens groeps-id als de levering van optimalisatie-id op de client. Wanneer de client met de cloudservice leveringsoptimalisatie communiceert, gebruikt deze id peers met de gewenste inhoud vinden. Zie voor meer informatie [basisconcepten voor inhoudsbeheer](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization).

### <a name="support-for-windows-10-arm64-devices"></a>Ondersteuning voor Windows 10 ARM64 apparaten
<!-- 1353704 -->
In deze release die Configuration Manager-client wordt ondersteund op Windows 10 ARM64 apparaten wordt gestart. Functies voor bestaande client moeten samenwerken met deze nieuwe apparaten. Bijvoorbeeld, hardware en software-inventaris, software-updates en toepassingen beheren. Implementatie van besturingssysteem is momenteel niet ondersteund. 

### <a name="improved-support-for-cng-certificates"></a>Verbeterde ondersteuning voor CNG-certificaten
<!-- 1357314 -->
Configuration Manager (huidige vertakking) versie 1710 ondersteunt [cryptografie: Volgende Generation (CNG)-certificaten](/sccm/core/plan-design/network/cng-certificates-overview). Ondersteuning voor versie 1710 limieten aan clientcertificaten in verschillende scenario's. 

U start in deze release, CNG-certificaten gebruiken voor de volgende serverfuncties voor HTTPS-functionaliteit:
- Beheerpunt
- Distributiepunt
- Sitesysteemrollen toevoegen
- Statusmigratiepunt  


### <a name="boundary-group-fallback-for-management-points"></a>Grensgroep voor beheerpunten terugval
<!-- 1324594 -->
Configureer terugval relaties voor beheerpunten tussen [grensgroepen](/sccm/core/servers/deploy/configure/boundary-groups). Dit gedrag biedt meer controle over de beheerpunten die clients gebruiken. Zie voor meer informatie [grensgroepen configureren](/sccm/core/servers/deploy/configure/boundary-groups#management-points).


### <a name="cloud-distribution-point-site-affinity"></a>Cloud distribution point site affiniteit
<!--503719-->
Deze functie voordelen biedt voor klanten met een meerdere locaties geografisch verspreide hiërarchie met clouddistributiepunten. Wanneer een client met internet wordt gezocht voor inhoud, eerder is er geen volgorde aan de lijst met clouddistributiepunten ontvangen door de client. Dit gedrag kan leiden tot internet gebaseerde clients inhoud ontvangen van geografisch verafgelegen clouddistributiepunten. Inhoud downloaden vanaf een externe server is gewoonlijk trager dan een dichter server.
 
Met cloud distribution point site affiniteit ontvangt een client met internet een geordende lijst. Deze lijst bepaalt de volgorde van clouddistributiepunten van de client toegewezen site. Dit gedrag kan de beheerder om te behouden hun ontwerp-type voor het downloaden van inhoud van sitebronnen.
 

## <a name="management-insights"></a>Management insights
<!-- 1353967 -->
Insights Management in System Center Configuration Manager bieden informatie over de huidige status van uw omgeving. De informatie is gebaseerd op de analyse van gegevens uit de sitedatabase. Insights kunnen u beter inzicht in uw omgeving en Neem maatregelen op basis van het inzicht. Zie voor meer informatie, [Management Insights](/sccm/core/servers/manage/management-insights)

In Configuration Manager 1802, zijn de volgende inzichten zijn beschikbaar:
- Toepassingen:
    - Toepassingen zonder implementaties
- Cloudservices: <!--1356412-->
    - Beoordeling van gereedheid van de CO-management 
    - Inschakelen van uw apparaten worden hybride die lid zijn van Azure Active Directory
    - Uw infrastructuur identiteits- en toegangsbeheer moderniseren
    -  Upgrade uitvoeren voor uw clients op Windows 10 versie 1709 of hoger 
- Verzamelingen:
    - Lege verzamelingen
- Eenvoudig beheer:  <!--1355148-->
    - Verouderde client versie  
- Software Center: 
    - Directe gebruikers naar Software Center in plaats van Application Catalog  
    - De nieuwe versie van Software Center gebruiken 
- Windows 10: <!--1357421-->
    - Configureer Windows Telemetrie en commerciële id-sleutel 
    - Verbinding maken met Configuration Manager voor gereedheid voor Upgrade 
   
<!-- ## Migration  -->



## <a name="client-management"></a>Clientbeheer

### <a name="cloud-management-gateway-support-for-azure-resource-manager"></a>Ondersteuning voor Azure Resource Manager-gateway cloud
<!-- 1324735 -->
Bij het maken van een exemplaar van de [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway) (CMG), de wizard biedt nu de optie voor het maken van een **Azure Resource Manager-implementatie**. [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) is een moderne platform voor het beheren van alle resources van de oplossing als één entiteit aangeroepen een [resourcegroep](/azure/azure-resource-manager/resource-group-overview#resource-groups). Bij het implementeren van CMG met Azure Resource Manager, de site maakt gebruik van Azure Active Directory (Azure AD) om te verifiëren en het maken van de benodigde cloud-bronnen. Deze gemoderniseerde implementatie vereist geen de klassieke Azure-beheercertificaat. Zie voor meer informatie [CMG topologie ontwerpen](/sccm/core/clients/manage/plan-cloud-management-gateway#azure-resource-manager).

> [!IMPORTANT]
> Deze mogelijkheid biedt geen ondersteuning voor Azure Cloud Service Providers (CSP) inschakelen. De implementatie CMG met Azure Resource Manager blijft de klassieke cloud-service biedt geen ondersteuning voor de CSP. Zie voor meer informatie [beschikbare Azure-services in Azure CSP](/azure/cloud-solution-provider/overview/azure-csp-available-services).  

### <a name="improvements-to-cloud-management-gateway"></a>Verbeteringen in de cloud beheergateway  

- Vanaf deze release de **management cloudgateway** is niet langer een functie van de voorlopige versie.  

- De functiedocumentatie is herzien en uitgebreid. Zie voor meer informatie de volgende artikelen:
    - [Plan voor de cloud-management-gateway](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
    - [De cloud management gateway-grootte en schaal cijfers](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
    - [Beveiliging en privacy voor cloudbeheergateway](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
    - [Veelgestelde vragen over de cloud-management-gateway](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
    - [Certificaten voor cloudbeheergateway](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
    - [Een cloudbeheergateway instellen](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)  


### <a name="configure-hardware-inventory-to-collect-strings-larger-than-255-characters"></a>Configureren van hardware-inventaris voor het verzamelen van tekenreeksen die groter is dan 255 tekens
<!-- 1357389 -->
U kunt de lengte van tekenreeksen moet groter zijn dan 255 tekens voor hardware-inventarisatie-eigenschappen configureren. Deze wijziging geldt alleen voor toegevoegde klassen en voor hardware-inventarisatie-eigenschappen die niet van sleutels. Zie voor meer informatie de [uitbreiden hardware-inventaris](/sccm/core/clients/manage/inventory/extend-hardware-inventory#BKMK_GreaterThan255) artikel. 

 ### <a name="deprecation-announcement-for-linux-and-unix-client-support"></a>Afschaffing aankondiging voor ondersteuning van clients voor Linux en Unix
 <!--510139-->
Microsoft zal de Linux- en UNIX-client-ondersteuning in System Center Configuration Manager afschaffen ongeveer één jaar, zoals dat de clients worden niet opgenomen in de SCCM-1902 in vroege kalender 2019 release.  De release van Configuration Manager 1810 in latere kalender 2018, is de laatste versie op te nemen van de Linux- en UNIX-clients, en ze worden ondersteund voor de volledige levenscyclus van Configuration Manager 1810.  Na de Configuration Manager 1810 overwegen klanten van Microsoft Operations Management Suite voor het beheren van Linux-servers.  OMS heeft uitgebreide Linux ondersteunen die in de meeste gevallen Configuration Manager-functionaliteit, waaronder het patchbeheer voor end-to-end voor Linux overschrijden.

### <a name="surface-device-dashboard"></a>Surface apparaat dashboard
<!--1355788-->
Het dashboard Surface apparaat bevat informatie over de apparaten die Surface gevonden in uw omgeving. Ga in de console naar **bewaking** > **oppervlak apparaten**. U kunt de items bekijken:
- percentage van het oppervlak
- percentage van het oppervlak modellen
- Top 5 firmware-versies

Zie voor meer informatie de [water dashboard](/sccm/core/clients/manage/surface-device-dashboard) artikel.

### <a name="change-in-the-configuration-manager-client-install"></a>Wijziging in de Configuration Manager-client installeren
<!--1356195-->
U start in deze release, wordt Silverlight niet meer op clientapparaten automatisch geïnstalleerd. Zie voor meer informatie [vereisten voor het implementeren van clients op Windows-computers](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#bkmk_ExternalDependencies)

## <a name="co-management"></a>CO-management

### <a name="transition-endpoint-protection-workload-to-intune-using-co-management"></a>Overgang Endpoint Protection werkbelasting voor Intune met CO-management
<!-- 1357365 -->
 De Endpoint Protection-werkbelasting kunt Intune na het inschakelen van CO-beheer zijn overgezet. Om de overgang van de werkbelasting van de Endpoint Protection, gaat u naar de eigenschappenpagina mede management en de schuifknop te verplaatsen van Configuration Manager **proef** of **alle**. Zie voor meer informatie over de werkbelastingen [werkbelastingen kunnen worden overgezet naar Intune](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune). Zie voor meer informatie over het beheer van CO [mede management voor Windows 10-apparaten](/sccm/core/clients/manage/co-management-overview).
 
### <a name="co-management-dashboard-in-system-center-configuration-manager"></a>Dashboard mede management in System Center Configuration Manager
<!--1356648-->
U begint in deze release, kunt u een dashboard met informatie over het beheer van CO weergeven. Het dashboard kunt u computers die CO beheerde in uw omgeving zijn controleren. De grafieken kunnen u apparaten identificeren die aandacht vereisen mogelijk. Zie voor meer informatie de [mede management dashboard](\sccm\core\clients\manage\client-management-dashboard) artikel. 


## <a name="compliance-settings"></a>Instellingen voor naleving

### <a name="microsoft-edge-browser-policies"></a>Microsoft Edge-browser-beleid
<!-- 1357310 -->
Voor klanten die gebruikmaken van de [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) web browser op Windows 10-clients, maakt u een nalevingsbeleid voor Configuration Manager-instellingen voor verschillende instellingen voor Microsoft Edge configureren. Zie voor meer informatie [maken Microsoft Edge-browser-profiel](/sccm/compliance/deploy-use/browser-profiles). 



## <a name="application-management"></a>Toepassingsbeheer

### <a name="allow-user-interaction-when-installing-an-application"></a>Interactie van de gebruiker toestaan bij het installeren van een toepassing
<!-- 1356976 -->
Toestaan dat een eindgebruiker om te communiceren met de installatie van een toepassing tijdens het uitvoeren van de takenreeks. Bijvoorbeeld: een setup-proces dat wordt de eindgebruiker gevraagd voor verschillende opties uitvoeren. Sommige installatieprogramma van de toepassing kunnen niet stilte gebruikersvragen of het installatieproces moet u mogelijk specifieke configuratiewaarden alleen bekend is dat de gebruiker. Deze functie kunt u deze installatie-scenario's te verwerken. Zie voor meer informatie [opties voor gebruikerservaring opgeven voor het implementatietype](/sccm/apps/deploy-use/create-applications#specify-user-experience-options-for-the-deployment-type).

### <a name="do-not-automatically-upgrade-superseded-applications"></a>Vervangen van toepassingen niet automatisch bijgewerkt
<!-- 1351266 -->
De implementatie van een toepassing om een upgrade niet automatisch elke vervangen versie te configureren. Nu bij het maken van de implementatie op de **implementatie-instellingen** pagina van de **Wizard Software implementeren**, voor **beschikbaar** of **vereist**doel, installeert u kunt inschakelen of uitschakelen van de optie voor het **automatisch upgraden een vervangen versies van deze toepassing**. Zie voor meer informatie [implementatie-instellingen opgeven](/sccm/apps/deploy-use/deploy-applications#specify-deployment-settings).

### <a name="approve-application-requests-for-users-per-device"></a>Goedkeuren van aanvragen van toepassingen voor gebruikers per apparaat
<!-- 1357015 -->
In deze release wordt gestart wanneer een gebruiker een toepassing die moet worden goedgekeurd aanvraagt, is de specifieke apparaatnaam nu een onderdeel van de aanvraag. Als de beheerder de aanvraag goedkeurt, is alleen de gebruiker kan de toepassing op het apparaat installeren. De gebruiker moet een nieuwe aanvraag voor het installeren van de toepassing op een ander apparaat verzenden. Zie voor meer informatie [implementatie-instellingen opgeven](/sccm/apps/deploy-use/deploy-applications#specify-deployment-settings).

 > [!Note]  
 > Dit is een optionele functie. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).  


### <a name="run-scripts-improvements"></a>Verbeteringen in scripts uitvoeren 
<!-- 1236459 -->
 Vanaf deze release **Scripts uitvoeren** is niet langer een functie van de voorlopige versie. De uitvoer van het script retourneert nu gebruik van JSON-opmaak. Zie voor meer informatie [maken en uitvoeren van PowerShell-scripts uit de Configuration Manager-console](/sccm/apps/deploy-use/create-deploy-scripts).


## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen

### <a name="windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway"></a>Takenreeks Windows 10 in-place upgrade via cloud management gateway
<!-- 1357149 -->
Het Windows 10- [in-place upgrade takenreeks](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version) biedt nu ondersteuning voor implementatie op internet gebaseerde clients beheerd via de [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway). Deze mogelijkheid kunnen externe gebruikers gemakkelijker upgraden naar Windows 10 zonder verbinding maken met het bedrijfsnetwerk. Zie [Een takenreeks implementeren](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#deploy-windows-10-in-place-upgrade-via-cmg) voor meer informatie.

### <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Verbeteringen in de takenreeks Windows 10 in-place upgrade
<!-- 1357425 -->
De standaard taak sequence-sjabloon voor een upgrade ter plekke van Windows 10 bevat nu extra groepen met aanbevolen acties om toe te voegen voor en na het upgradeproces. Deze acties gelden veel klanten die met succes apparaten naar Windows 10 upgraden. Zie voor meer informatie [een takenreeks om een upgrade van een besturingssysteem te maken](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#recommended-task-sequence-steps-to-prepare-for-upgrade).

### <a name="improvements-to-operating-system-deployment"></a>Verbeteringen in de implementatie van besturingssysteem
Deze versie bevat de volgende verbeteringen aangebracht in de implementatie van besturingssysteem:
 - In Windows PE, tijdens het starten van cmtrace.exe, u niet langer gevraagd te kiezen of maken van dit programma van de standaard-viewer voor logboekbestanden. <!-- SMS 500897 -->
 - Toevoegen van opstartinstallatiekopieën naar de [pakketinhoud downloaden](/sccm/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent) takenreeksstap.
 - Verbeteringen in de [Takenreeks uitvoeren](/sccm/osd/understand/task-sequence-steps#child-task-sequence) stap: <!-- 1261338 -->   
     - Ondersteuning voor alle implementatiescenario's van besturingssysteem vanuit Software Center, PXE en media.
     - Verbeteringen in de console acties zoals kopiëren, import, export en waarschuwing tijdens het verwijderen van objecten.
     - Ondersteuning voor de [voorbereid inhoudsbestand maken](/sccm/core/plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent) wizard.
     - Integratie met implementatieverificatie. Zie voor meer informatie [riskante takenreeksimplementaties](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS). 
     - De Takenreeks uitvoeren stap kan nu worden gebruikt op meerdere niveaus van takenreeksen, niet alleen een één-bovenliggende / onderliggende relatie. Met meerdere niveaus relaties verhogen van de complexiteit, dus wees voorzichtig. Deze relaties worden nog steeds gecontroleerd voor kringverwijzingen bevatten.
    
### <a name="deployment-templates-for-task-sequences"></a>Implementatiesjablonen voor takenreeksen
<!-- 1357391 -->
De [implementatiewizard voor takenreeksen](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS) kunt nu een implementatiesjabloon maken. De sjabloon voor de implementatie kan worden opgeslagen en worden toegepast op een bestaande of nieuwe takenreeks maken van een implementatie. 

### <a name="phased-deployments-for-task-sequences"></a>Gefaseerde implementaties voor takenreeksen
<!--1356837-->
 Gefaseerde implementaties wordt een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Gefaseerde implementaties automatiseren een gecoördineerde, geordende rollout van een takenreeks in meerdere verzamelingen. U kunt [gefaseerde implementaties maken](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence) met de standaardwaarde van twee fasen bestaat, of handmatig configureren van meerdere fasen. Gefaseerde implementatie van takenreeksen biedt geen ondersteuning voor PXE of media-installatie.




## <a name="software-center"></a>Software Center

### <a name="install-multiple-applications-in-software-center"></a>Meerdere toepassingen in Software Center installeren
<!-- 1357126 -->
Als een eindgebruiker of bureaublad technicus moet meerdere toepassingen installeren op een apparaat, Software Center biedt nu ondersteuning voor het installeren van meerdere geselecteerde toepassingen. Dit gedrag kan de gebruiker tijdens het wachten geen één installatie is voltooid voordat u begint de volgende efficiënter zijn. Zie voor meer informatie [meerdere toepassingen installeert](/sccm/core/understand/software-center#install-multiple-applications) in de gebruikershandleiding voor de nieuwe Software Center.

### <a name="use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices"></a>Software Center gebruiken om te zoeken en installeren van de gebruiker beschikbare toepassingen op Azure AD-die lid zijn van apparaten
<!-- 1322613 -->
Als u toepassingen als beschikbaar voor gebruikers implementeert, kunnen ze nu bladeren en deze op Azure Active Directory (Azure AD)-apparaten installeren via Software Center. Zie voor meer informatie [gebruikers beschikbare toepassingen op Azure AD-die lid zijn van apparaten implementeren](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices).

### <a name="hide-installed-applications-in-software-center"></a>Geïnstalleerde toepassingen in Software Center verbergen
<!--1357592-->
Geïnstalleerde toepassingen kunnen nu worden verborgen in Software Center. Toepassingen die al zijn geïnstalleerd, worden niet meer weergegeven op het tabblad toepassingen wanneer deze optie is ingeschakeld in de clientinstellingen. Deze optie is ingesteld als standaard bij het installeren of upgraden naar Configuration Manager 1802.  Geïnstalleerde toepassingen zijn nog steeds beschikbaar is voor controle op het tabblad van de status van de installatie. [De toepassingen geïnstalleerd verbergen in Software Center](/sccm/core/clients/deploy/about-client-settings#BKMK_HideInstalled) bevat aanvullende informatie.   

### <a name="hide-unapproved-applications-in-software-center"></a>Niet-goedgekeurde toepassingen in Software Center verbergen
 <!--1355146-->
Wanneer deze clientoptie-instelling is ingeschakeld, worden de beschikbare toepassingen die moeten worden goedgekeurd verborgen in Software Center.  [Niet-goedgekeurde toepassingen in Software Center verbergen](/sccm/core/clients/deploy/about-client-settings#BKMK_HideUnapproved) bevat aanvullende informatie.  

### <a name="software-center-shows-user-additional-compliance-information"></a>Software Center bevat informatie over de aanvullende compatibiliteit van de gebruiker
<!-- 1235616 -->
 Wanneer u Health Attestation van apparaten status als een regel voor naleving beleid voor voorwaardelijke toegang tot bedrijfsbronnen, bevat Software Center nu de gebruiker de instelling voor Health Attestation van apparaten die niet compatibel is.


 ## <a name="software-updates"></a>Software-updates 

### <a name="schedule-automatic-deployment-rule-evaluation-to-be-offset-from-a-base-day"></a>Automatische implementatie Regeltoepassing verschoven ten opzichte van een base dag plannen. 
<!--1357133-->
Regels voor automatische implementatie kunnen worden gepland om te evalueren verschuiving ten opzichte van een base dag. Dit betekent dat als patch dinsdag daadwerkelijk op woensdag voor u valt, worden de evaluatieplanning ingesteld voor de tweede dinsdag van de verschuiving van de maand op één dag. Zie voor meer informatie [softwareupdates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates#BKMK_CreateAutomaticDeploymentRule). 



## <a name="reporting"></a>Rapporten

### <a name="report-for-default-browser-counts"></a>Rapport voor standaard browser aantallen
<!-- 1357830 -->
Er is nu een nieuw rapport om de telling van clients met een specifieke webbrowser als de standaard Windows weer te geven. Zie de **standaardbrowser telt** rapport in de **Software - bedrijven en producten** groep rapporten. Zie voor meer informatie de [lijst met rapporten](/sccm/core/servers/manage/list-of-reports#software---companies-and-products).

### <a name="report-on-windows-autopilot-device-information"></a>Rapport over Windows Automatische piloot apparaatgegevens
<!-- 1351442 -->
Windows Automatische piloot is een oplossing voor onboarding en nieuwe Windows 10-apparaten op een moderne manier configureren. Zie voor meer informatie een [overzicht Windows Automatische piloot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot). Er is één methode voor het registreren van bestaande apparaten met Windows Automatische piloot van apparaatgegevens uploaden naar de Microsoft Store voor bedrijven en Education. Deze informatie omvat het serienummer van het apparaat, Windows-product-id en een hardware-id. Gebruik Configuration Manager voor het verzamelen en rapporteren van deze gegevens van een apparaat met het nieuwe rapport **Windows Automatische piloot apparaatgegevens**, in de **Hardware - algemeen** knooppunt rapporten. Zie voor meer informatie [nieuwe Windows 10-apparaten](/sccm/core/clients/manage/co-management-prepare#new-windows-10-devices) bij het voorbereiden op mede management.

### <a name="report-on-windows-10-servicing-details-for-a-specific-collection"></a>Rapport over details voor een specifieke verzameling onderhoud van Windows 10
<!--1357653-->
De **onderhoud van Windows 10 details voor een specifieke verzameling** lijst bevat algemene informatie over het onderhoud van Windows 10 voor een specifieke verzameling. Dit rapport geeft de Resource-ID, NetBIOS-naam, OS-naam, de naam van de OS-versie, build, OS vertakking en onderhoud voor Windows 10-apparaten. Zie voor meer informatie de [lijst met rapporten](/sccm/core/servers/manage/list-of-reports#operating-system)



<!-- ## Inventory  -->



<!-- ## Mobile device management -->



 ## <a name="protect-devices"></a>Apparaten beveiligen

### <a name="improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard"></a>Verbeteringen in Configuration Manager-beleid voor Windows Defender misbruiken Guard
<!-- 1356220 -->
Extra instellingen voor de [kwetsbaarheid voor aanvallen vermindering](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy#BKMK_ASR) en [beheerde toegang tot de map](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy#BKMK_CFA) componenten hebt toegevoegd in Configuration Manager voor [Windows Defender misbruiken Guard ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard).

### <a name="new-host-interaction-settings-for-windows-defender-application-guard"></a>Nieuwe host interactie van de instellingen voor Windows Defender toepassing Guard
<!-- 1356256 -->
Voor Windows 10 versie 1709 en hogere apparaten er zijn twee nieuwe host interactie van de instellingen voor [Windows Defender toepassing Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy#BKMK_HIS): 
- Websites kunnen toegang krijgen tot virtuele graphics-processor van de host. 
- Bestanden gedownload in de container kunnen persistent worden gemaakt op de host. 




## <a name="configuration-manager-console"></a>Configuration Manager-console

### <a name="improvements-to-the-configuration-manager-console"></a>Verbeteringen in de Configuration Manager-console 
Deze versie bevat de volgende verbeteringen aangebracht in de Configuration Manager-console.
- De primaire gebruiker weergegeven apparatenlijsten onder activa en naleving, apparaten, nu standaard. In deze kolom wordt alleen weergegeven in het knooppunt apparaten. De laatste aangemelde gebruiker kan ook worden toegevoegd als een optionele kolom.<!-- 1357280 --> Schakel [affiniteit van gebruiker en apparaat](/sccm/core/clients/deploy/about-client-settings#user-and-device-affinity) clientinstellingen voor de site een primaire gebruiker koppelen aan een apparaat.
- Als een verzameling lid van een andere verzameling is en de naam wordt gewijzigd, wordt de nieuwe naam onder lidmaatschapsregels bijgewerkt.<!--1357282--> 
- Wanneer u beheer op afstand op een client met meerdere beeldschermen op verschillende schaal (DPI), de muisaanwijzer nu correct toegewezen ertussen. <!--433170-->
- De [clientbeheer voor Office 365-dashboard](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard) geeft een lijst met relevante apparaten wanneer grafiek secties zijn geselecteerd. <!--1357281 --> 



## <a name="next-steps"></a>Volgende stappen
Wanneer u klaar bent om deze versie te installeren, Zie [Updates voor Configuration Manager](/sccm/core/servers/manage/updates).
