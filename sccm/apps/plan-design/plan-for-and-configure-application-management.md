---
title: Plannen en configureren van Toepassingsbeheer | Microsoft-documenten
description: Implementeren en configureren van de vereiste afhankelijkheden voor het implementeren van toepassingen in System Center Configuration Manager.
ms.custom: na
ms.date: 02/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2be84a1d-ebb9-47ae-8982-c66d5b92a52a
caps.latest.revision: 13
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1c43c4968f93985515249ddb117269f8ed61302a
ms.openlocfilehash: 46cc3fcfd9516cf1c124e24b50d0aac0cb0025dc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-and-configure-application-management-in-system-center-configuration-manager"></a>Toepassingsbeheer plannen en configureren in System Center Configuration Manager 

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit artikel bij het implementeren van de vereiste afhankelijkheden voor het implementeren van toepassingen in System Center Configuration Manager.  

## <a name="dependencies-external-to-configuration-manager"></a>Afhankelijkheden extern aan Configuration Manager  

|Afhankelijkheid|Meer informatie|  
|------------------|----------------------|  
|Internet Information Services (IIS) is vereist op de sitesysteemservers waarop het Application Catalog-websitepunt, het Application Catalog-webservicepunt, het beheerpunt en het distributiepunt worden uitgevoerd.|Zie voor meer informatie over deze vereiste [ondersteunde configuraties](../../core/plan-design/configs/supported-configurations.md).|  
|Mobiele apparaten die zijn ingeschreven door Configuration Manager|Wanneer u toepassingen ondertekenen ze te implementeren op mobiele apparaten geen gebruiken een certificaat dat is gegenereerd met een sjabloon van versie 3 (**Windows Server 2008, Enterprise Edition**). Deze certificaatsjabloon maakt een certificaat dat is niet compatibel met Configuration Manager-toepassingen voor mobiele apparaten.<br /><br /> Als u Active Directory Certificate Services voor het ondertekenen van code toepassingen voor mobiele apparaten gebruikt, gebruikt u een certificaatsjabloon van versie 3 niet.|  
|Clients moeten worden geconfigureerd dat ze aanmeldingsgebeurtenissen aanmelden als u wilt gebruikersaffiniteiten met apparaten automatisch te maken.|De Configuration Manager-client leest aanmeldingsgebeurtenissen van het type **geslaagd** van het beveiligingslogboek van pc's om te bepalen van de automatische gebruikersaffiniteit voor apparaten.  Deze gebeurtenissen zijn ingeschakeld door de volgende twee beleidsregels: "<br>**Aanmeldingsgebeurtenissen voor accounts controleren**<br>**Aanmeldingsgebeurtenissen controleren**<br>Als u automatisch relaties tussen gebruikers en apparaten wilt maken, moet u ervoor zorgen dat deze twee instellingen zijn ingeschakeld op clientcomputers. U kunt het Windows-groepsbeleid gebruiken om deze instellingen te configureren.|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden   

|Afhankelijkheid|Meer informatie|  
|------------------|----------------------|  
|Beheerpunt|Clients contact op met een beheerpunt om te downloaden van clientbeleid inhoud te zoeken en verbinding maken met de Application Catalog.<br /><br /> Als clients geen toegang kunnen krijgen tot een beheerpunt, kunnen ze de toepassingscatalogus niet gebruiken.|  
|Distributiepunt|Voordat toepassingen op clients kunnen worden geïmplementeerd, moet u minstens één distributiepunt in de hiërarchie hebben. Op de siteserver is standaard een siterol van het distributiepunt ingeschakeld tijdens een standaardinstallatie. Het aantal en de locatie van distributiepunten verschilt, afhankelijk van de specifieke vereisten van uw onderneming.<br /><br /> Zie voor meer informatie over het installeren van distributiepunten en beheerinhoud [inhoud en -infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|Clientinstellingen|Veel clientinstellingen bepalen hoe toepassingen worden geïnstalleerd op de client en de gebruiker van de gebruikerservaring op de client. Deze clientinstellingen omvatten:<br /><br /><ul><li>Computeragent</li><li>Computer opnieuw opstarten</li><li>Software-implementatie</li><li>Gebruiker en Apparaataffiniteit</li></ul> Zie voor meer informatie over deze clientinstellingen [over clientinstellingen](../../core/clients/deploy/about-client-settings.md).<br /><br /> Voor over het configureren van clientinstellingen, Zie [het configureren van clientinstellingen](../../core/clients/deploy/configure-client-settings.md).|  
|Voor de toepassingcatalogus:<br /><br /> Gedetecteerde gebruikersaccounts|Configuration Manager moet eerst detecteren van gebruikers voordat ze kunnen weergeven en aanvragen van toepassingen uit de Application Catalog. Zie voor meer informatie [detectie uitvoeren](/sccm/core/servers/deploy/configure/run-discovery).|  
|App-V 4.6 SP1-client of hoger om virtuele toepassingen uit te voeren|Om te kunnen maken van virtuele toepassingen in Configuration Manager, moeten clientcomputers de App-V 4.6 SP1-client of later geïnstalleerd hebben.<br /><br /> U moet de App-V-client ook bijwerken met de hotfix beschreven in het Knowledge Base [2645225 artikel](http://go.microsoft.com/fwlink/p/?LinkId=237322) voordat u virtuele toepassingen kunt implementeren.|  
|Application Catalog-webservicepunt|Het Application Catalog-webservicepunt is een sitesysteemrol die informatie over beschikbare software uit de softwarebibliotheek verstrekt aan de Application Catalog-website.<br /><br /> Zie voor meer informatie over het configureren van deze sitesysteemrol [configureren Software Center en Application Catalog (alleen Windows-pc's)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only) in dit artikel.|  
|Application Catalog-websitepunt|Het Application Catalog-websitepunt is een sitesysteemrol die een lijst met beschikbare software versterkt aan gebruikers.<br /><br /> Zie voor meer informatie over het configureren van deze sitesysteemrol [configureren Software Center en Application Catalog (alleen Windows-pc's)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only) in dit artikel.|  
|Reporting Services-punt|Als u de rapporten in Configuration Manager gebruiken voor toepassingsbeheer, moet u eerst installeren en configureren van een reporting services-punt.<br /><br /> Zie [Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) voor meer informatie.|  
|Beveiligingsmachtigingen voor toepassingsbeheer|U moet de volgende beveiligingsmachtigingen hebben om toepassingen te kunnen beheren.<br /><br /> De **Toepassingsauteur** beveiligingsrol bevat de hiervoor genoemde machtigingen die nodig zijn voor het maken, wijzigen en buiten gebruik stellen toepassingen in Configuration Manager.<br /><br /> **Toepassingen implementeren:**<br /><br /> De **beheerder Toepassingsimplementaties** beveiligingsrol bevat de hiervoor genoemde machtigingen die vereist zijn voor het implementeren van toepassingen in Configuration Manager.<br /><br /> De **toepassingsbeheerder** beveiligingsrol heeft alle machtigingen van zowel de **Toepassingsauteur** en de **beheerder Toepassingsimplementaties** beveiligingsrollen.<br /><br /> Zie voor meer informatie [op rollen gebaseerd beheer configureert](../../core/servers/deploy/configure/configure-role-based-administration.md).|  

##  <a name="configure-software-center-and-the-application-catalog-windows-pcs-only"></a>Software Center en de toepassingscatalogus (alleen Windows-pc's) configureren  

 In System Center Configuration Manager nu hebt u twee opties voor gebruikers wilt wijzigen, bladeren door toepassingen en toepassingen installeren:  

-   **De nieuwe Software Center** -de nieuwe Software Center heeft een moderne vormgeving. Apps die u zou nu alleen in de Silverlight-afhankelijk zijn van het Application Catalog (gebruiker beschikbare apps) hebben gestaan worden weergegeven in Software Center onder de **toepassingen** tabblad. De Application Catalog nog steeds toegankelijk zijn via de koppeling onder de **installatiestatus** tabblad van het Software Center.  

     U kunt clients zo configureren dat deze het nieuwe Software Center gebruiken, door de clientinstelling **Computeragent** > **Het nieuwe Software Center gebruiken**in te schakelen.  

    > [!IMPORTANT]  
    >  Hoewel u niet langer verbinding maken met de Application Catalog, moet u de Application Catalog-websitepunt en het Application Catalog-webservicepunt als gedetailleerde nog steeds configureren in de volgende sectie.  

-   **Het vorige Software Center en de toepassingscatalogus** : standaard blijven gebruikers nog verbinding maken met de vorige versie van Software Center en de toepassingscatalogus (webbrowser met de Silverlight-invoegtoepassing is vereist) om naar beschikbare toepassingen te zoeken.  

 De versie die u gebruiken wilt, Software Center wordt automatisch geïnstalleerd wanneer u de Configuration Manager-client op Windows-pc's installeren.  

    > [!TIP]  
    >  De versie van het Software Center die gebruikers te zien is gebaseerd op de Configuration Manager-clientinstellingen. Hierdoor kunt u de flexibiliteit om te bepalen op basis van aangepaste clientinstellingen die u op een verzameling implementeert van de versie die wordt gebruikt. 

    > [!IMPORTANT]
    > In de komende maanden we verwijdert de vorige versie van het Software Center en het wordt niet meer beschikbaar zijn voor u om te gebruiken.
    > U kunt clients zo configureren dat deze het nieuwe Software Center gebruiken, door de clientinstelling **Computeragent** > **Het nieuwe Software Center gebruiken**in te schakelen. 

## <a name="steps-to-install-and-configure-the-application-catalog-and-software-center"></a>Stappen voor het installeren en configureren van de toepassingscatalogus en Software Center  

> [!IMPORTANT]  
>  Voordat u deze stappen uitvoert, zorg ervoor dat u alle eerder genoemde vereisten hebben voldaan.  

|Stappen|Details|Meer informatie|  
|-----------|-------------|----------------------|  
|**Stap 1:** Als u HTTPS-verbindingen gebruiken wilt, ervoor zorgen dat u hebt geïmplementeerd, een Webservercertificaat op sitesysteemservers.|Implementeer een webservercertificaat op de sitesysteemservers waarop het Application Catalog-websitepunt en het Application Catalog-webservicepunt worden uitgevoerd.<br /><br /> Bovendien, als u wilt dat clients de Toepassingscatalogus van het Internet gebruiken, implementeert een Webservercertificaat op minstens één beheerpunt-sitesysteemserver en configureren voor clientverbindingen van het Internet.|Zie voor meer informatie over certificaatvereisten [PKI-certificaatvereisten](../../core/plan-design/network/pki-certificate-requirements.md).|  
|**Stap 2:** Als u een PKI-certificaat voor verbindingen met beheerpunten gebruiken wilt, implementeert u een certificaat voor clientverificatie op clientcomputers.|Hoewel clients geen PKI-clientcertificaat verbinding maken met de Application Catalog gebruiken, moeten ze verbinden met een beheerpunt voordat ze de Toepassingscatalogus kunnen gebruiken. In de volgende scenario's moet u een certificaat voor clientverificatie op clientcomputers implementeren:<br /><br /><ul><li>Alle beheerpunten op het intranet accepteren alleen HTTPS-clientverbindingen.</li><li>Clients maken verbinding met de Toepassingscatalogus van het Internet.</li></ul>|Zie voor meer informatie over certificaatvereisten [PKI-certificaatvereisten](../../core/plan-design/network/pki-certificate-requirements.md).|  
|**Stap 3:** Installeer en configureer het Application Catalog-webservicepunt en de Application Catalog-website.|U moet beide sitesysteemrollen op dezelfde site installeren. U hoeft ze niet op dezelfde sitesysteemserver of in hetzelfde Active Directory-forest te installeren. Het Application Catalog-webservicepunt moet zich echter op hetzelfde forest als de sitedatabase.|Zie voor meer informatie over het plaatsen van sitesysteemrollen, [plannen voor de sitesysteemservers en sitesysteemrollen](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).<br /><br /> Zie het configureren van het Application Catalog-webservicepunt en het Application Catalog-websitepunt **stap 3: Installeer en configureer de Application Catalog-sitesysteemrollen**.|  
|**Stap 4:** Configureer clientinstellingen voor de Application Catalog en Software Center.|Configureer de standaardclientinstellingen als u wilt dat alle gebruikers dezelfde instelling hebben. Configureer anders aangepaste clientinstellingen voor specifieke verzamelingen.|Zie voor meer informatie over clientinstellingen [over clientinstellingen](../../core/clients/deploy/about-client-settings.md).<br /><br /> Zie voor meer informatie over het configureren van deze clientinstellingen **stap 4: Configureer de clientinstellingen voor de Application Catalog en Software Center**.|  
|**Stap 5:** Controleer of de Toepassingscatalogus werkt.|U kunt de Application Catalog direct vanuit een browser of vanuit Software Center.|Zie **stap 5: Controleer of de Toepassingscatalogus werkt**.|  

## <a name="supplemental-procedures-to-install-and-configure-the-application-catalog-and-software-center"></a>Aanvullende procedures voor de installatie en configuratie van de Toepassingscatalogus en het Software Center  
 Gebruik de volgende informatie wanneer de stappen in de voorgaande tabel aanvullende procedures vereisen.  

###  <a name="step-3-install-and-configure-the-application-catalog-site-system-roles"></a>Stap 3: Installeer en configureer de Application Catalog-sitesysteemrollen  
 Met deze procedures worden de sitesysteemrollen voor de Toepassingscatalogus geconfigureerd. Kies een van de volgende twee procedures, afhankelijk van het feit of u wordt een nieuwe sitesysteemserver installeert of een bestaande sitesysteemserver:  

> [!NOTE]  
>  De Toepassingscatalogus kan niet op een secundaire site of op een centrale beheersite worden geïnstalleerd.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-new-site-system-server"></a>Installeren en configureren van de Application Catalog-sitesystemen: Nieuwe sitesysteemserver  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Servers en sitesysteemrollen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Sitesysteemserver maken**.  

4.  Op de **algemeen** pagina, geeft u de algemene instellingen voor het sitesysteem en kies vervolgens **volgende**.  

    > [!TIP]  
    >  Geef op dat Internet volledig gekwalificeerde domeinnaam (FQDN) als u clientcomputers voor gebruik van de Toepassingscatalogus via het Internet.  

5.  Op de **Systeemrolselectie** optie **Application Catalog-webservicepunt** en **Application Catalog-websitepunt** uit de lijst met beschikbare rollen en kies vervolgens **volgende**.  

6.  Sluit de wizard af.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-existing-site-system-server"></a>Installeren en configureren van de Application Catalog-sitesystemen: Bestaande sitesysteemserver  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Servers en sitesysteemrollen**, en selecteer vervolgens de server moet worden gebruikt voor de Application Catalog.  

3.  Op de **Start** tabblad, in de **Server** groep, kiest u **sitesysteemrollen toevoegen**.  

4.  Op de **algemeen** pagina, geeft u de algemene instellingen voor het sitesysteem en kies vervolgens **volgende**.  

    > [!TIP]  
    >  Geef op dat Internet volledig gekwalificeerde domeinnaam (FQDN) als u clientcomputers voor gebruik van de Toepassingscatalogus via het Internet.  

5.  Op de **Systeemrolselectie** optie **Application Catalog-webservicepunt** en **Application Catalog-websitepunt** uit de lijst met beschikbare rollen en kies vervolgens **volgende**.  

6.  Sluit de wizard af.  

7. Controleer of deze sitesysteemrollen goed zijn geïnstalleerd aan de hand van statusberichten en de logboekbestanden:  

    Statusberichten: Gebruik de onderdelen **SMS_PORTALWEB_CONTROL_MANAGER** en **SMS_AWEBSVC_CONTROL_MANAGER**.  

    Bijvoorbeeld, status-ID **1015** voor **SMS_PORTALWEB_CONTROL_MANAGER** bevestigt dat Site Component Manager de Application Catalog-website-punt succesvol geïnstalleerd.  

    Logboekbestanden: Zoeken naar **SMSAWEBSVCSetup.log** en **SMSPORTALWEBSetup.log**.  

    Voor meer informatie, zoekt u de **awebsvcMSI.log** en **portlwebMSI.log** logboekbestanden.  

###  <a name="step-4-configure-the-client-settings-for-the-application-catalog-and-software-center"></a>Stap 4: Configureer de clientinstellingen voor de Application Catalog en Software Center  
 Met deze procedure worden de standaardclientinstellingen geconfigureerd voor de Toepassingscatalogus en het Software Center die op alle apparaten in de hiërarchie worden toegepast. Als u deze instellingen wilt toepassen op slechts op sommige apparaten wilt, kunt u een aangepaste clientinstelling maken en deze implementeren in een verzameling met apparaten die de specifieke instellingen. Zie voor meer informatie over het maken van een aangepaste Apparaatinstelling de [maken en implementeren van aangepaste clientinstellingen](../../core/clients/deploy/configure-client-settings.md#create-and-deploy-custom-client-settings) sectie het [clientinstellingen configureren in System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md) artikel.  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Controleer en configureer de instellingen met betrekking tot gebruikersmeldingen, de Toepassingscatalogus en het Software Center. Bijvoorbeeld:  

    1.  Groep**Computeragent** :  

        -   **Standaard Application Catalog-websitepunt**  

        -   **Voeg de standaard Application Catalog-website toe aan de zone met vertrouwde sites in Internet Explorer**  

        -   **Weergegeven organisatienaam in Software Center**  

            > [!TIP]  
            >  Geef de naam van de organisatie die wordt weergegeven in de Application Catalog en om het Websitethema te configureren, gebruiken de **aanpassing** tabblad Eigenschappen van de Application Catalog-website.  

        -   **Nieuwe Software Center gebruiken** -ingesteld op **Ja** als u de nieuwe Software Center, waarmee gebruikers zoeken en installeren van de beschikbare apps zonder de noodzaak wilt voor toegang tot de Toepassingscatalogus (hiervoor moet een ingeschakeld voor Silverlight webbrowser) gebruiken.  

        -   **Installatiemachtigingen**  

        -   **Meldingen weergeven voor nieuwe implementaties**  

    2.  Groep**Energiebeheer** :  

        -   **Toestaan dat gebruikers hun apparaat uit energiebeheer uitsluiten**  

    3.  Groep**Externe hulpprogramma's** :  

        -   **Gebruikers kunnen instellingen voor beleid of meldingen in Software Center wijzigen**  

    4.  Groep**Affiniteit van gebruiker en apparaat** :  

        -   **Toestaan dat gebruikers hun primaire apparaten definiëren**  

    > [!NOTE]  
    >  Zie voor meer informatie over de clientinstellingen [over clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).  

5.  Kies **OK** sluit de **Standaardclientinstellingen** in het dialoogvenster.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Zie voor het initiëren van ophaalbeleid voor één client [clients beheren](../../core/clients/manage/manage-clients.md).

#### <a name="how-to-customize-software-center-branding"></a>Het aanpassen van Software Center branding

Aangepaste huisstijl voor het Software Center wordt toegepast volgens de volgende regels:

1. Als de Application Catalog-website-puntrol siteserver niet is geïnstalleerd, wordt de Software Center, u de naam van de organisatie opgegeven ziet in de **Computeragent** clientinstelling **organisatienaam** weergegeven in Software Center. Zie voor instructies [het configureren van clientinstellingen](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/configure-client-settings).
2. Als de Application Catalog-website-puntrol siteserver is geïnstalleerd, wordt klikt u vervolgens Software Center weergegeven de naam van de organisatie en kleur die is opgegeven in de Application Catalog-website site server-roleigenschappen. Zie voor meer informatie [configuratieopties voor de Application Catalog-websitepunt](https://docs.microsoft.com/en-us/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#BKMK_ApplicationCatalog_Website).
3. Als een Microsoft Intune-abonnement is geconfigureerd en aan Configuration Manager verbonden, wordt klikt u vervolgens Software Center weergegeven de naam van de organisatie, kleur en het bedrijfslogo opgegeven in de eigenschappen van de Intune-abonnement. Zie [Het Windows Intune-abonnement configureren](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription) voor meer informatie.

> [!IMPORTANT]  
>  Software Center branding is gesynchroniseerd met de Intune-service die alle 14 dagen daarom is er mogelijk een vertraging voordat wijzigingen die u in Intune aanbrengt worden weergegeven in Configuration Manager.

###  <a name="step-5-verify-that-the-application-catalog-is-operational"></a>Stap 5: Controleer of de Toepassingscatalogus werkt  
 Voer de volgende procedures uit om te controleren of de Toepassingscatalogus werkt. U kunt de Application Catalog direct vanuit een browser of vanuit Software Center.  

> [!NOTE]  
>  De Toepassingscatalogus vereist Microsoft Silverlight, dat automatisch als een vereiste voor een Configuration Manager-client is geïnstalleerd. Als u de Application Catalog rechtstreeks vanuit een browser op een computer waarop geen Configuration Manager-client geïnstalleerd, moet u eerst controleren of Microsoft Silverlight op de computer is geïnstalleerd.  

> [!TIP]  
>  Ontbrekende vereisten zijn van de meest voorkomende redenen waarom de Application Catalog niet correct functioneert na de installatie. Controleer de sitesysteemrolvereisten voor de Application Catalog-sitesysteemrollen. U kunt dit doen met behulp van de [ondersteunde configuraties](../../core/plan-design/configs/supported-configurations.md) artikel.  

> [!NOTE]  
>  Als u zich aangemeld met behulp van een domein Administrator-account worden meldingen van de Configuration Manager-client (bijvoorbeeld berichten die aangeeft dat de nieuwe software beschikbaar is) worden niet weergegeven.  

### <a name="to-use-the-application-catalog-directly-from-a-browser"></a>Gebruik van de Application Catalog rechtstreeks vanuit een browser  

-   In een browser het adres invoeren van de Application Catalog-website en controleer of de webpagina drie tabbladen bevat: **Application Catalog**, **mijn toepassingsaanvragen**, en **mijn apparaten**.  

     Selecteer en gebruik het juiste adres in de volgende lijst voor de Toepassingscatalogus, waar &lt;server&gt; is de computernaam, intranet-FQDN of Internet-FQDN:  

    -   HTTPS-clientverbindingen en standaardinstellingen site-instellingen voor de sitesysteemrol: **https://&lt;server&gt;/CMApplicationCatalog**  

    -   HTTP-clientverbindingen en standaardinstellingen site-instellingen voor de sitesysteemrol: **http://&lt;server&gt;/CMApplicationCatalog**  

    -   HTTPS-clientverbindingen en aangepaste instellingen voor de rol: **https://&lt;server&gt;:&lt;poort&gt;/&lt;webtoepassingsnaam&gt;**  

    -   HTTP-clientverbindingen en aangepaste instellingen voor rol: **http://&lt;server&gt;:&lt;poort&gt;/&lt;webtoepassingsnaam&gt;**  

### <a name="to-use-the-application-catalog-from-software-center-does-not-apply-to-the-new-version-of-software-center"></a>Gebruik van de Toepassingscatalogus vanuit Software Center (niet van toepassing op de nieuwe versie van het Software Center)  

1.  Kies op een clientcomputer **Start** > **alle programma's** > **Microsoft System Center 2012** > **Configuration Manager** > **Software Center**.  

2.  Als u eerder een organisatienaam voor Software Center hebt geconfigureerd als clientinstelling, controleert u of deze wordt weergegeven zoals  opgegeven.  

3.  Kies **aanvullende toepassingen in de catalogus met toepassingen zoeken**, en bevestigt u dat de pagina toont de drie tabbladen: **Application Catalog**, **mijn toepassingsaanvragen**, en **mijn apparaten**.  

> [!WARNING]  
>  Nadat u de Application Catalog-sitesysteemrollen hebt geïnstalleerd, niet onmiddellijk ziet u de Application Catalog als u ervoor kiest de **aanvullende toepassingen in de catalogus met toepassingen zoeken** koppeling vanuit Software Center. De Toepassingscatalogus wordt beschikbaar vanuit het Software Center nadat de client de volgende keer het clientbeleid heeft gedownload of maximaal 25 uur nadat de Application Catalog-sitesysteemrollen zijn geïnstalleerd.  

