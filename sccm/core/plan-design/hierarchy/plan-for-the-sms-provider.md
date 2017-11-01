---
title: Plannen van de SMS-Provider
titleSuffix: Configuration Manager
description: Meer informatie over hoe de SMS-Provider helpt u bij het beheren van System Center Configuration Manager.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5d5d6273-0d8a-43c7-865a-cdb1736dcae3
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5ee2ebea24fed329a4e5974c67d95c6d854484e2
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="plan-for-the-sms-provider-for-system-center-configuration-manager"></a>Plannen voor de SMS-provider voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voor het beheren van System Center Configuration Manager, gebruikt u een Configuration Manager-console die verbinding met een exemplaar van maakt de **SMS-Provider**. Standaard een SMS-Provider wordt geïnstalleerd op de siteserver wanneer u een centrale beheersite of primaire site installeert. 


##  <a name="BKMK_PlanSMSProv"></a> Over de SMS-provider  
 De SMS-Provider is een Windows Management Instrumentation (WMI)-provider die wordt toegewezen **lezen** en **schrijven** toegang tot de Configuration Manager-database op een site:  

-   Elke centrale beheersite of primaire site moet ten minste één SMS-provider bevatten. U kunt indien nodig aanvullende providers installeren.  
-   De **SMS Admins** beveiligingsgroep biedt toegang tot de SMS-Provider. Deze groep Configuration Manager automatisch gemaakt op de siteserver en op elke computer waarop u een exemplaar van de SMS-Provider installeert.  

-   Secundaire sites bieden geen ondersteuning voor de SMS-provider.  


Gebruikers met beheerdersrechten Configuration Manager gebruiken voor toegang tot informatie die is opgeslagen in de database een SMS-Provider. Om dit te doen, kunnen beheerders de Configuration Manager-console, Resourceverkenner, hulpprogramma's en aangepaste scripts gebruiken. De SMS-Provider communiceert niet met Configuration Manager-clients. Wanneer een Configuration Manager-console verbinding met een site maakt, wordt in de Configuration Manager-console WMI zoekt op de siteserver om te bepalen welke instantie van de SMS-Provider te gebruiken.  

 De SMS-Provider helpt Configuration Manager-beveiliging afdwingen. De methode retourneert alleen de informatie die de gebruiker met beheerdersrechten die de Configuration Manager-console wordt uitgevoerd is gemachtigd om te bekijken.  

> [!IMPORTANT]  
>  Wanneer iedere computer met een SMS-Provider voor een site offline is, wordt Configuration Manager-consoles kunnen geen verbinding met de database van die site.  

 Voor meer informatie over het beheren van de SMS-provider, zie [De SMS-provider beheren](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) [Uw infrastructuur van System Center Configuration Manager aanpassen](../../../core/servers/manage/modify-your-infrastructure.md).  

## <a name="prerequisites-to-install-the-sms-provider"></a>Vereisten voor het installeren van de SMS-Provider  

 De SMS-provider ondersteunen:  

-   De computer moet zich in een domein met een tweerichtingsvertrouwensrelatie heeft met de siteserver en de sitedatabasesystemen.  

-   De computer mag geen sitesysteemrol van een andere site gebruiken.  

-   De computer mag geen SMS-provider van een willekeurige site gebruiken.  

-   Op de computer moet een besturingssysteem worden uitgevoerd dat wordt ondersteund voor een siteserver.  

-   De computer moet ten minste 650 MB aan vrije schijfruimte voor de Windows Automated Deployment Kit (Windows ADK)-onderdelen die zijn geïnstalleerd met de SMS-Provider hebben. Zie de sectie [Windows Automated Installation Kit-vereisten voor de SMS-provider](#BKMK_WAIKforSMSProv) in dit onderwerp voor meer informatie over Windows AIK en de SMS-provider.  

##  <a name="bkmk_location"></a> Locaties van de SMS-provider  
 Als u een site installeert, installeert u automatisch de eerste SMS-Provider voor de site. U kunt elk van de volgende ondersteunde locaties opgeven voor de SMS-provider:  

-   De siteservercomputer  

-   De sitedatabasecomputer  

-   Een servercomputer waarop geen SMS-Provider of een sitesysteemrol van een andere site  


Als u wilt weergeven in de locaties van elke SMS-Provider die is geïnstalleerd op een site, selecteer de **algemene** tabblad van de site **eigenschappen** in het dialoogvenster.  

 Elke SMS-provider ondersteunt gelijktijdige verbindingen met betrekking tot meerdere aanvragen. De enige beperkingen met betrekking tot deze verbindingen zijn het aantal serververbindingen dat beschikbaar is op de SMS-providercomputer en de beschikbare bronnen op de SMS-providercomputer voor het afhandelen van de verbindingsaanvragen.  

 Nadat de site is geïnstalleerd, kunt u Setup opnieuw uitvoeren op de siteserver om de locatie van een bestaande SMS-provider te wijzigen of om aanvullende SMS-providers te installeren voor de desbetreffende site. U kunt slechts één SMS-provider installeren op een computer en het is niet mogelijk om SMS-providers van meer dan één site op een computer te installeren.  

 Gebruik de volgende informatie om de voordelen en nadelen te identificeren van het installeren van een SMS-provider op elke ondersteunde locatie:  

 **Configuration Manager-siteserver**  

-   **Voordelen:**  

    -   De SMS-provider gebruikt geen systeembronnen op de sitedatabasecomputer.  

    -   Deze locatie is in staat om betere prestaties te bieden dan een SMS-provider op een andere computer dan de siteserver of sitedatabasecomputer.  

-   **Nadelen:**  

    -   De SMS-provider gebruikt systeem- en netwerkbronnen die kunnen worden toegekend voor siteserverbewerkingen.  


**Het SQL Server-exemplaar dat als host voor de sitedatabase fungeert**  

-   **Voordelen:**  

    -   De SMS-provider gebruikt geen sitesysteembronnen op de siteserver.  

    -   Deze locatie kan de beste prestaties bieden van de drie locaties wanneer er voldoende serverbronnen beschikbaar zijn.  

-   **Nadelen:**  

    -   De SMS-provider gebruikt systeem- en netwerkbronnen die kunnen worden toegekend voor sitedatabasebewerkingen.  

    -   Wanneer de sitedatabase wordt gehost op een geclusterd exemplaar van SQL Server, kunt u deze locatie niet gebruiken.  


**Een andere computer dan de siteserver of sitedatabasecomputer**  

-   **Voordelen:**  

    -   De SMS-provider maakt geen gebruikt van de siteserver of bronnen van de sitedatabasecomputer.  

    -   Het type locatie stelt u in staat om aanvullende SMS-providers te implementeren om een hoge beschikbaarheid voor verbindingen te bieden.  

-   **Nadelen:**  

    -   De prestaties van de SMS-Provider kan worden verkleind vanwege de extra netwerk-activiteit die is vereist voor coördinatie met de siteserver en de sitedatabasecomputer.  

    -   Deze server moet altijd toegankelijk zijn met de databasecomputer, en op alle computers met de Configuration Manager-console die is geïnstalleerd.  

    -   Deze locatie kan systeembronnen gebruiken die anders aan andere services worden toegekend.  

##  <a name="BKMK_SMSProvLanguages"></a>Over de talen van de SMS-Provider  
 De SMS-provider werkt onafhankelijk van de weergavetaal van de computer waarop deze is geïnstalleerd.  

 Wanneer een gebruiker met beheerdersrechten of Configuration Manager-proces aanvragen gegevens met behulp van de SMS-Provider, de SMS-Provider probeert deze gegevens te retourneren in een indeling die overeenkomt met de taal van het besturingssysteem van de aanvragende computer.

De manier wordt geprobeerd te overeenkomt met de taal is enigszins indirecte. De SMS-provider vertaalt geen informatie van de ene taal in een andere taal. In plaats daarvan wanneer gegevens worden geretourneerd voor weergave in de Configuration Manager-console, afhankelijk de weergavetaal van de gegevens van de bron van het object en het type opslag.  

 Wanneer gegevens voor een object in de database worden opgeslagen, is welke talen beschikbaar zijn, afhankelijk van het volgende:  

-   Objecten die door Configuration Manager gemaakt worden opgeslagen in de database met behulp van ondersteuning voor meerdere talen. Het object wordt opgeslagen door gebruik te maken van de talen die worden geconfigureerd op de site waarop het object wordt gemaakt wanneer u Setup uitvoert. Deze objecten worden weergegeven in de Configuration Manager-console in de weergavetaal van de aanvragende computer wanneer die taal beschikbaar voor het object is. Als het object niet kan worden weergegeven in de weergavetaal van de aanvragende computer, wordt dit weergegeven in de standaardtaal, Engels.  

-   Objecten die door een beheergebruiker worden gemaakt, worden opgeslagen in de database in de taal die is gebruikt om het object te maken. Deze objecten weergegeven in de Configuration Manager-console in deze zelfde taal. Deze kunnen niet worden vertaald door de SMS-Provider en hebben geen opties voor meerdere talen.  

##  <a name="BKMK_MultiSMSProv"></a> Meerdere SMS-providers gebruiken  
 Nadat het installeren van een site is voltooid, kunt u aanvullende SMS-providers voor de site installeren. Voor het installeren van extra SMS-Providers Setup van Configuration Manager op de siteserver worden uitgevoerd. Overweeg om aanvullende SMS-providers te installeren wanneer er sprake is van een of meer van de volgende omstandigheden:  

-   Hebt u veel administratieve gebruikers die bij het uitvoeren van een Configuration Manager-console en maak verbinding met een site op hetzelfde moment.  

-   U gebruikt de Configuration Manager-SDK of andere producten, waardoor er mogelijk sprake van regelmatige aanroepen naar de SMS-Provider.  

-   U wilt een hoge beschikbaarheid voor de SMS-provider garanderen.  


Als meerdere SMS-Providers zijn geïnstalleerd op een site en een verbindingsaanvraag wordt verzonden, wordt elke nieuwe verbindingsaanvraag gebruik van een geïnstalleerde SMS-Provider willekeurig toegewezen door de site. Het is niet mogelijk om de SMS-providerlocatie op te geven die voor een specifieke verbindingssessie moet worden gebruikt.  

> [!NOTE]  
>  U kunt de voordelen en nadelen van elke locatie van de SMS-Provider. Saldo daarbij rekening met de informatie dat u welke SMS-Provider kan niet bepalen voor elke nieuwe verbinding wordt gebruikt.  

Bijvoorbeeld, als u een Configuration Manager-console voor het eerst verbinding met een site, de verbinding een query WMI op de siteserver om te identificeren van een exemplaar van de SMS-Provider die de console kan gebruiken. Deze specifieke instantie van de SMS-Provider blijft in gebruik door de Configuration Manager-console totdat u de Configuration Manager consolesessie wordt beëindigd. Als de sessie eindigt omdat de SMS-providercomputer niet meer beschikbaar is op het netwerk wanneer u de Configuration Manager-console opnieuw verbinding maakt, wordt de taak van de identiteit van een exemplaar van de SMS-Provider verbinding maken met gewoon herhaald in de site. Mogelijk wordt deze toegewezen aan dezelfde SMS-providercomputer die niet beschikbaar is. Als dit het geval is, kunt u proberen opnieuw verbinding maken met de Configuration Manager-console totdat er een beschikbare SMS-providercomputer wordt toegewezen.  

##  <a name="BKMK_AboutSMSAdmins"></a> Over de groep SMS Admins  
 U kunt de SMS Admins-groep gebruiken om beheergebruikers toegang tot de SMS-provider te bieden. De groep wordt automatisch op de siteserver gemaakt wanneer de site wordt geïnstalleerd en op elke computer waarop een SMS-provider wordt geïnstalleerd. Hier volgt aanvullende informatie over de SMS Admins-groep:  

-   Wanneer de computer een lidserver is, wordt de SMS Admins-groep gemaakt als een lokale groep.  

-   Wanneer de computer een domeincontroller is, wordt de SMS Admins-groep gemaakt als een lokale groep van het domein.  

-   Wanneer de SMS-provider van een computer wordt verwijderd, blijft de SMS Admins-groep op de computer staan.  


Een gebruiker kan pas een verbinding met een SMS-provider tot stand brengen, als het gebruikersaccount van deze gebruiker lid is van de SMS Admins-groep. Elke gebruiker met beheerdersrechten die u in de Configuration Manager-console configureert wordt automatisch toegevoegd aan de SMS Admins-groep op elke siteserver en op elke computer van de SMS-Provider in de hiërarchie. Wanneer u een gebruiker met beheerdersrechten uit de Configuration Manager-console verwijdert, wordt die gebruiker verwijderd uit de SMS Admins-groep op elke siteserver en op elke computer van de SMS-Provider in de hiërarchie.  

Nadat een gebruiker verbinding met de SMS-Provider maakt, op rollen gebaseerd beheer bepaald welke Configuration Manager resources die gebruiker toegang of beheren.  

U kunt bekijken en SMS Admins-groepsrechten en machtigingen configureren met behulp van de WMI Control MMC-module. Standaard beschikt **Iedereen** over de machtigingen **Methoden uitvoeren**, **Schrijftoegang tot providerobjecten**en **Account inschakelen** . Nadat een gebruiker verbinding met de SMS-Provider, kan die gebruiker toegang tot gegevens in de sitedatabase, op basis van hun op rollen gebaseerde beheerbeveiligingsrechten zoals gedefinieerd in de Configuration Manager-console is verleend. De SMS Admins-groep worden nadrukkelijk de machtigingen **Account inschakelen** en **extern activeren** machtigingen voor de **Root\SMS** naamruimte.  

> [!NOTE]  
>  Elke gebruiker met beheerdersrechten die gebruik maakt van een externe Configuration Manager-console vereist Remote Activation DCOM-machtigingen op de siteservercomputer en op de computer van de SMS-Provider. Hoewel u deze rechten aan een gebruiker of groep op te geven kunt, is het een goed idee te kennen aan de groep SMS Admins te vereenvoudigen. Zie voor meer informatie de sectie [DCOM-machtigingen configureren voor externe Configuration Manager-consoles](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) in het onderwerp [Uw infrastructuur van System Center Configuration Manager aanpassen](../../../core/servers/manage/modify-your-infrastructure.md).  


##  <a name="BKMK_SMSProvNamespace"></a>Over de naamruimte van de SMS-Provider  
De structuur van de SMS-provider wordt gedefinieerd via het WMI-schema. Schemanaamruimten beschrijven de locatie van Configuration Manager-gegevens binnen het SMS-providerschema. De volgende tabel bevat enkele van de algemene naamruimten die door de SMS-provider worden gebruikt.  

|Naamruimte|Beschrijving|  
|---------------|-----------------|  
|Root\SMS\site_*&lt;sitecode\>*|De SMS-Provider, die grote schaal wordt gebruikt door de Configuration Manager-console, Resource Explorer, Configuration Manager-hulpprogramma's en scripts.|  
|Root\SMS\SMS_ProviderLocation|De locatie van de SMS-Provider-computers voor een site.|  
|Root\CIMv2|De locatie voor WMI-naamruimte informatie tijdens de hardware en software-inventarisatie zijn geïnventariseerd.|  
|Wordt teruggedraaid|Configuration Manager-clientconfiguratiebeleid en -clientgegevens.|  
|root\CIMv2\SMS|De locatie van inventarisrapportageklassen die zijn verzameld door de inventarisclientagent. Deze instellingen worden gecompileerd door clients tijdens de evaluatie van het beleid en zijn gebaseerd op de configuratie van de client-instellingen voor de computer.|  

##  <a name="BKMK_WAIKforSMSProv"></a>Vereisten voor besturingssysteemimplementatie voor de SMS-Provider  
De computer waarop u een exemplaar van de SMS-Provider installeert, moet de vereiste versie van Windows ADK die de versie van Configuration Manager, u moet hebben.  

 -   Bijvoorbeeld, vereist versie 1511 van Configuration Manager dat de versie Windows 10 RTM (10.0.10240) van Windows ADK.  

 -   Zie voor meer informatie over deze vereiste [vereisten voor de infrastructuur voor besturingssysteemimplementatie](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

Als u implementaties van besturingssystemen beheert, kunnen de Windows ADK de SMS-Provider verschillende taken uitvoeren, zoals:  

-   Details WIM-bestand weergeven.  

-   Stuurprogrammabestanden toevoegen aan bestaande opstartinstallatiekopieën.  

-   Voor opstarten maken. ISO-bestanden.  


De installatie van Windows ADK kan tot 650 MB vrije schijfruimte vereisen op elke computer waarop de SMS-provider wordt geïnstalleerd. Deze hoge eisen voor schijfruimte is nodig voor Configuration Manager voor het installeren van de Windows PE-opstartinstallatiekopieën.  
