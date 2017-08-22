---
title: Beveiliging in System Center Configuration Manager plannen | Microsoft Docs
description: Aanbevolen procedures en andere informatie over beveiliging in System Center Configuration Manager opgehaald.
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a216814-ca8c-4d2e-bcef-dc00966a3c9f
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 6145cb69c69dba1eb1b9842079ee1a33686bb18a
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="plan-for-security-in-system-center-configuration-manager"></a>De beveiliging plannen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

##  <a name="BKMK_PlanningForCertificates"></a>Plannen voor certificaten (zelfondertekend en PKI)  
 Configuration Manager gebruikt een combinatie van zelfondertekende certificaten en openbare-sleutelinfrastructuur (PKI)-certificaten.  

 Voor een betere beveiliging, gebruik waar mogelijk PKI-certificaten. Zie voor meer informatie over PKI-certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md). Wanneer Configuration Manager PKI-certificaten aanvraagt, moet zoals tijdens de inschrijving voor mobiele apparaten en Intel Active Management Technology (AMT) inrichting, u Active Directory Domain Services en een bedrijfscertificeringsinstantie. U moet voor alle andere PKI-certificaten implementeren en beheren ze onafhankelijk van Configuration Manager.  

 PKI-certificaten zijn ook vereist wanneer clientcomputers verbinding met sitesystemen op Internet maken en het is raadzaam dat u PKI-certificaten gebruiken wanneer clients verbinding maken met sitesystemen die Internet Information Services (IIS) uitvoeren. Zie voor meer informatie over clientcommunicatie [clientcommunicatiepoorten in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-communication-ports.md).  

 Wanneer u een PKI gebruikt, kunt u ook IPsec gebruiken om te helpen beveiligen van de server naar server-communicatie tussen sitesystemen in een site, tussen sites, en voor andere gegevensoverdracht tussen computers. Implementatie van IPsec is onafhankelijk van Configuration Manager.  

 Configuration Manager kan automatisch zelfondertekende certificaten genereren wanneer PKI-certificaten niet beschikbaar zijn en sommige certificaten in Configuration Manager zijn altijd zelfondertekend. In de meeste gevallen Configuration Manager beheert automatisch de zelfondertekende certificaten en hoeft u geen verdere actie te ondernemen. Een mogelijke uitzondering is het handtekeningcertificaat van de siteserver. Het handtekeningcertificaat van de siteserver is altijd zelfondertekend en het garandeert dat het clientbeleid dat clients downloaden van het beheerpunt zijn verzonden vanaf de siteserver en niet zijn gemanipuleerd.  

### <a name="plan-for-the-site-server-signing-certificate-self-signed"></a>Plan voor het handtekeningcertificaat van siteserver (zelfondertekend)  
 Clients kunnen veilig een kopie van het handtekeningcertificaat van siteserver ophalen uit Active Directory Domain Services en push-clientinstallatie. Als clients een kopie van het handtekeningcertificaat van siteserver niet door een van deze methoden ophalen kunnen, als een best practice bij beveiliging installeren een kopie van het handtekeningcertificaat van siteserver wanneer u de client installeert. Dit is vooral belangrijk als de eerste communicatie van de client met de site van het Internet is, omdat het beheerpunt is verbonden met een niet-vertrouwd netwerk en daarom kwetsbaar voor aanvallen. Als u deze extra stap niet uitvoert, downloaden clients automatisch een kopie van het handtekeningcertificaat van de siteserver van het beheerpunt.  

 Scenario's als clients kunnen niet veilig een kopie van het certificaat van de site server omvatten het volgende:  

-   U installeert de client niet met behulp van client-push en een van de volgende voorwaarden is waar:  

    -   Active Directory-schema is voor Configuration Manager niet uitgebreid.  

    -   Site van de client niet is gepubliceerd op Active Directory Domain Services.  

    -   De client is van een niet-vertrouwde forest of een werkgroep.  

-   U installeert de client wanneer deze zich op het internet bevindt.  

##### <a name="to-install-clients-with-a-copy-of-the-site-server-signing-certificate"></a>Installeren van clients met een kopie van het handtekeningcertificaat van de siteserver  

1.  Zoek het handtekeningcertificaat van siteserver op de primaire siteserver van de client. Het certificaat wordt opgeslagen in de **SMS** certificaatarchief en heeft de objectnaam **siteserver** en de beschrijvende naam **handtekeningcertificaat van siteserver**.  

2.  Exporteer het certificaat zonder persoonlijke sleutel, sla het bestand veilig en alleen toegang tot deze vanaf een veilig kanaal, bijvoorbeeld met behulp van Server Message Block (SMB) ondertekening of IPsec.  

3.  De client installeren met behulp van de Client.msi-eigenschap **SMSSIGNCERT =***&lt;volledig pad en de naam\>*, met CCMSetup.exe.  

###  <a name="BKMK_PlanningForCRLs"></a>Plan voor PKI-certificaatintrekking  
Wanneer u PKI-certificaten met Configuration Manager gebruikt, plan dan hoe en of clients en servers gaan gebruiken een certificaatintrekkingslijst (CRL) om te controleren of het certificaat op de verbindende computer. De CRL is een bestand dat een certificeringsinstantie (CA) maakt en meldt zich en er is een lijst met certificaten die de CA is verleend, maar ingetrokken. Een CA-beheerder kan certificaten intrekken, bijvoorbeeld als een uitgegeven certificaat bewezen of mogelijk onveilig.  

> [!IMPORTANT]  
>  Omdat de locatie van de CRL wordt toegevoegd aan een certificaat CA's die deze, zorg ervoor dat u van plan voor de CRL bent voordat u implementeert PKI-certificaten die Configuration Manager zal gebruiken.  

Standaard, IIS controleert altijd de CRL voor clientcertificaten en u deze configuratie in Configuration Manager niet wijzigen. Standaard controleren altijd de CRL voor sitesystemen Configuration Manager-clients. U kunt deze instelling uitschakelen door op te geven van een site-eigenschap en een CCMSetup-eigenschap op te geven. Als u Intel AMT gebaseerde computers buiten-band beheert, kunt u ook inschakelen CRL-controle voor de out-of-band-servicepunt en voor computers waarop de Out of Band Management-console wordt uitgevoerd.  

Computers die controle voor certificaatintrekking gebruiken maar de CRL niet vinden gedragen zich alsof alle certificaten in de certificeringsketen zijn ingetrokken omdat hun afwezigheid van de lijst kan niet worden geverifieerd. In dit scenario mislukken alle verbindingen die certificaten vereisen en een CRL gebruiken.  

Als de certificaatintrekkingslijst wel altijd wordt gecontroleerd wanneer een certificaat wordt gebruikt, bent u beter beschermd tegen het gebruik van een ingetrokken certificaat. Hierdoor ontstaat echter ook een vertraging in de verbinding en vinden er extra verwerkingsactiviteiten plaats op de client. U zult deze extra beveiligingscontrole waarschijnlijk eerder nodig hebben wanneer clients zich op het internet of op niet-vertrouwde netwerken bevinden.  

Raadpleeg uw PKI-beheerders voordat u besluit of Configuration Manager-clients moeten de CRL te controleren en Overweeg vervolgens houden van deze optie is ingeschakeld in Configuration Manager te wanneer beide volgende voorwaarden waar zijn:  

-   Uw PKI-infrastructuur ondersteunt een CRL en deze wordt gepubliceerd waar alle Configuration Manager-clients hem kunnen vinden. Dit kan dus ook clients op het internet betreffen, als u clientbeheer over het internet gebruikt, en clients op niet-vertrouwde forests.  

-   De vereiste om te controleren van de CRL voor elke verbinding met een sitesysteem dat geconfigureerd voor gebruik van een PKI-certificaat is groter dan de vereiste voor snellere verbindingen, efficiënte verwerking op de client en het risico van clients die geen verbinding maken met servers als ze de CRL niet vinden.  

###  <a name="BKMK_PlanningForRootCAs"></a>Plannen voor de PKI vertrouwde basis-certificaten en de lijst met certificaatverleners  
Als uw IIS-sitesystemen PKI-clientcertificaten gebruiken voor clientverificatie over HTTP of voor clientverificatie en versleuteling over HTTPS, moet u mogelijk basis-CA-certificaten importeren als een site-eigenschap. Hier volgen de twee scenario's:  

-   U besturingssystemen implementeert met behulp van Configuration Manager en de beheerpunten accepteren alleen HTTPS-clientverbindingen.  

-   U kunt PKI-clientcertificaten gebruiken die zich niet onder het basis-CA-certificaat bevinden dat wordt vertrouwd door beheerpunten.  

    > [!NOTE]  
    >  Als u client-PKI-certificaten uitgeeft van dezelfde CA-hiërarchie die de servercertificaten uitgeeft die u gebruikt voor beheerpunten, hoeft u dit basis-CA-certificaat niet op te geven. Echter, als u meerdere CA-hiërarchieën gebruikt en u niet zeker weet of ze elkaar vertrouwen, de basiscertificeringsinstantie importeren voor de clients CA-hiërarchie.  

Als u basis-CA-certificaten voor Configuration Manager te importeren moet, exporteert u ze van de verlenende CA of vanaf de clientcomputer. Als u het certificaat exporteert van de verlenende certificeringsinstantie dat ook het basis-CA-certificaat is, zorg dan dat de persoonlijke sleutel niet wordt geëxporteerd. Sla het geëxporteerde certificaatbestand op een veilige locatie om manipulatie te voorkomen. U moet toegang kunnen krijgen tot het bestand bij het instellen van de site. Als u het bestand via het netwerk openen, moet u ervoor dat de communicatie is beschermd tegen manipulatie door SMB-ondertekening of IPsec.  

Als u een basiscertificaat dat u importeert, wordt verlengd, moet u het verlengde certificaat importeren.  

Deze geïmporteerde basis-CA-certificaten en het basis-CA-certificaat van ieder beheerpunt maken van de lijst met certificaatverleners die gebruikmaken van de Configuration Manager-computers in de volgende manieren:  

-   Wanneer clients verbinding met beheerpunten maken, controleert het beheerpunt dat het clientcertificaat overeenkomt met een vertrouwd basiscertificaat in de lijst met certificaatverleners van de site van het certificaat. Is dit niet het geval, dan wordt het certificaat geweigerd en de PKI-verbinding mislukt.  

-   Wanneer clients een PKI-certificaat selecteren en een lijst met certificaatverleners hebben, selecteren ze op een certificaat dat is gekoppeld aan een vertrouwd basiscertificaat in de lijst met certificaatverleners. Als het certificaat niet overeenkomt, selecteert de client geen PKI-certificaat. Zie voor meer informatie over het clientcertificaatproces, de [plannen voor selectie van PKI-clientcertificaten](#BKMK_PlanningForClientCertificateSelection) sectie in dit artikel.  

Onafhankelijk van de siteconfiguratie mogelijk ook moet een basis-CA-certificaat importeren wanneer u mobiele apparaten inschrijven, Mac-computers inschrijven en Intel AMT gebaseerde computers voor draadloze netwerken instellen.  

###  <a name="BKMK_PlanningForClientCertificateSelection"></a>Plan voor selectie van PKI-clientcertificaten  
 Als uw IIS-sitesystemen PKI-clientcertificaten voor clientverificatie over HTTP of voor clientverificatie en versleuteling over HTTPS, plan hoe Windows-clients wordt het certificaat selecteren om te gebruiken voor Configuration Manager.  

> [!NOTE]  
>  Sommige apparaten bieden geen ondersteuning voor een certificaatselectiemethode. In plaats daarvan selecteren ze automatisch van het eerste certificaat dat voldoet aan de certificaatvereisten. Clients op Mac-computers en mobiele apparaten ondersteunen bijvoorbeeld geen certificaatselectiemethode.  

In veel gevallen zijn de standaardconfiguratie en -gedrag voldoende. Configuration Manager-client op Windows-computers filtert meerdere certificaten met behulp van deze criteria in deze volgorde:  

1.  De lijst met certificaatverleners: Het certificaat is gekoppeld aan een basis-CA die wordt vertrouwd door het beheerpunt.  

2.  Het certificaat bevindt zich in het standaardcertificaatarchief **Persoonlijk**.  

3.  Het certificaat is geldig, is niet ingetrokken en niet verlopen. De geldigheidscontrole verifieert dat de persoonlijke sleutel toegankelijk is en of het certificaat niet is gemaakt met een certificaatsjabloon van versie 3, die niet compatibel is met Configuration Manager.  

4.  Het certificaat heeft een clientverificatie-optie of is verleend aan de computernaam.  

5.  Het certificaat heeft de langste geldigheidsduur.  

Clients kunnen worden ingesteld op het gebruik van de lijst met certificaatverleners met behulp van de volgende mechanismen:  

-   Het is gepubliceerd als Configuration Manager-site-informatie naar Active Directory Domain Services.  

-   Clients worden met behulp van clientpush geïnstalleerd.  

-   Clients downloaden de lijst van het beheerpunt nadat ze zijn toegewezen aan hun site.  

-   Het is opgegeven tijdens de installatie van de client als een CCMSetup client.msi-eigenschap van CCMCERTISSUERS.  

Clients die niet de lijst met certificaatverleners hebben wanneer ze eerst worden geïnstalleerd en nog niet zijn toegewezen aan de site wordt deze controle overslaan. Wanneer clients hebben de lijst met certificaatverleners en beschikt niet over een PKI-certificaat dat overeenkomt met een vertrouwd basiscertificaat in de lijst met certificaatverleners, mislukt de certificaatselectie en clients niet door met de andere certificaatselectiecriteria.  

In de meeste gevallen identificeert de Configuration Manager-client een uniek en geschikt bruikbaar PKI-certificaat. Echter, als dit niet het geval is, in plaats van het selecteren van het certificaat op basis van de mogelijkheid tot clientverificatie, u kunt instellen twee alternatieve selectiemethodes:  

-   Een gedeeltelijke tekenreeksovereenkomst op de onderwerpnaam van het clientcertificaat. Deze overeenkomst is niet-hoofdlettergevoelig en is geschikt als u een FQDN (Fully Qualified Domain Name) van een computer gebruikt in het onderwerpveld en de certificaatselectie wilt baseren op het domeinachtervoegsel, bijvoorbeeld **contoso.com**. U kunt deze selectiemethode echter gebruiken om iedere reeks vervolgtekens te identificeren in de onderwerpnaam van het certificaat die het certificaat onderscheiden van andere certificaten in het clientcertificaatarchief.  

    > [!NOTE]  
    >  U kunt de gedeeltelijke tekenreeksovereenkomst gebruiken met de alternatieve naam voor het onderwerp (SAN) als een site-instelling. Hoewel u een gedeeltelijke tekenreeksovereenkomst kunt opgeven voor de SAN door gebruik te maken van CCMSetup, zal deze in de volgende scenario's overschreven worden door de site-eigenschappen:  
    >   
    >  -   Clients halen site-informatie op die naar Active Directory Domain Services is gepubliceerd.  
    > -   Clients worden met behulp van clientpushinstallatie geïnstalleerd.  
    >   
    >  Gebruik een gedeeltelijke tekenreeksovereenkomst in de SAN alleen wanneer u clients handmatig installeert en wanneer ze geen site-informatie worden opgehaald uit Active Directory Domain Services. Deze voorwaarden zijn bijvoorbeeld van toepassing op clients met alleen internetverbinding.  

-   Een overeenkomst op de kenmerkwaarden van de onderwerpnaam van het clientcertificaat of de kenmerkwaarden van de alternatieve naam voor het onderwerp (SAN). Dit is een hoofdlettergevoelige overeenkomst die geschikt is als u met behulp van een X500 DN-naam of een equivalent Object-id's (OID's) in overeenstemming met RFC 3280 gebruikt en u wilt dat de certificaatselectie wordt gebaseerd op de kenmerkwaarden. U kunt alleen de kenmerken en hun waarden opgeven die u nodig hebt om het certificaat uniek te identificeren of valideren en het certificaat te onderscheiden van andere in het certificaatarchief.  

De volgende tabel toont de kenmerkwaarden die Configuration Manager voor selectiecriteria van het clientcertificaat ondersteunt.  

|OID-kenmerk|DN-naamkenmerk|Kenmerkdefinitie|  
|-------------------|----------------------------------|--------------------------|  
|0.9.2342.19200300.100.1.25|DC|Domeinonderdeel|  
|1.2.840.113549.1.9.1|E of e-mailbericht|E-mailadres|  
|2.5.4.3|CN|Algemene naam|  
|2.5.4.4|SN|Onderwerpnaam|  
|2.5.4.5|SERIENUMMER|Serienummer|  
|2.5.4.6|C|Landcode|  
|2.5.4.7|L|Plaats|  
|2.5.4.8|S of ST|Naam van staat of provincie|  
|2.5.4.9|STRAAT|Straat|  
|2.5.4.10|O|Naam van de organisatie|  
|2.5.4.11|OU|Organisatie-eenheid|  
|2.5.4.12|T of titel|Titel|  
|2.5.4.42|G of GN of voornaam|Voornaam|  
|2.5.4.43|I of initialen|Initialen|  
|2.5.29.17|(geen waarde)|Alternatieve onderwerpnaam|  

Als meer dan een geschikt certificaat bevindt na het toepassen van de selectiecriteria, kunt u de standaardconfiguratie voor het certificaat met de langste geldigheidsduur selecteren en in plaats daarvan opgeven dat er geen certificaat is geselecteerd overschrijven. In dit scenario wordt zich de client niet kan communiceren met IIS-sitesystemen met een PKI-certificaat. De client stuurt een foutbericht naar zijn toegewezen terugvalstatuspunt om u te waarschuwen voor de selectie van certificaat mislukt zodat u kunt wijzigen of verfijnen van uw certificaatselectiecriteria. Het clientgedrag is dan afhankelijk van of de mislukte verbinding zich voordeed via HTTPS of HTTP:  

-   Als de mislukte verbinding zich voordeed via HTTPS: De client probeert verbinding te maken via HTTP en gebruikt het zelfondertekende certificaat van de client.  

-   Als de mislukte verbinding zich voordeed via HTTP: De client probeert opnieuw verbinding te maken via HTTP met behulp van het zelfondertekend certificaat.  

Als u wilt een uniek PKI-clientcertificaat te identificeren, kunt u ook een aangepast archief dan de standaardwaarde van opgeven **persoonlijke** in de **Computer** opslaan. Echter, u moet maken dit archief onafhankelijk van Configuration Manager en moet kunnen om certificaten te implementeren op dit aangepast archief te vernieuwen voordat de geldigheidsperiode verstrijkt.  

Zie voor meer informatie over het configureren van de instellingen voor clientcertificaten de [instellingen configureren voor PKI-clientcertificaten](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) sectie het [beveiliging configureren in System Center Configuration Manager](../../../core/plan-design/security/configure-security.md) artikel.  

###  <a name="BKMK_PlanningForPKITransition"></a>Plannen van een overgangsstrategie voor PKI-certificaten en clientbeheer op Internet  
De flexibele configuratieopties in Configuration Manager kunnen u geleidelijk overgang van clients en de site voor het gebruik van PKI-certificaten om beveiligde clienteindpunten te helpen. PKI-certificaten bieden betere beveiliging en kunnen u Internet-clients beheren.  

Er is geen enkele manier voor de overgang van een site, zodat alle clients HTTPS-verbindingen gebruiken vanwege het aantal configuratieopties en -keuzes in Configuration Manager. U kunt echter deze stappen volgen als richtlijn:  

1.  Installeer de Configuration Manager-site en configureer deze zodat sitesystemen clientverbindingen over HTTPS en HTTP accepteren.  

2.  Configureer de **Clientcomputercommunicatie** tabblad in de site-eigenschappen zodat die de **Sitesysteeminstellingen** is **HTTP of HTTPS**, en selecteer **gebruik PKI-clientcertificaat (mogelijkheid tot clientverificatie) indien beschikbaar**.  Zie voor meer informatie de [instellingen configureren voor PKI-clientcertificaten](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) sectie het [beveiliging configureren in System Center Configuration Manager](../../../core/plan-design/security/configure-security.md) artikel.  

3.  Proef uitvoeren van een PKI-rollout voor clientcertificaten. Zie voor een voorbeeldimplementatie de *implementeren van de Client-certificaat voor Windows-Computers* sectie het [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) artikel.  

4.  Clients met behulp van de clientpushinstallatiemethode installeren. Zie voor meer informatie de [Configuration Manager-clients installeren door met behulp van Clientpush](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush) sectie het [clients implementeren op Windows-computers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) artikel.  

5.  Clientimplementatie en -status bewaken met behulp van de rapporten en informatie in de Configuration Manager-console.  

6.  Volg hoeveel clients een PKI-clientcertificaat gebruiken in de kolom **Clientcertificaat** in de werkruimte **Activa en naleving** en het knooppunt **Apparaten** .  

     U kunt ook implementeren met Configuration Manager HTTPS Readiness Assessment Tool (**cmHttpsReadiness.exe**) aan computers en gebruik de rapporten om weer te geven hoeveel computers een PKI-client kunnen gebruiken met Configuration Manager-certificaat.  

    > [!NOTE]  
    >  Wanneer de Configuration Manager-client is geïnstalleerd, de **cmHttpsReadiness.exe** hulpprogramma is geïnstalleerd in de *% windir %***\CCM** map. Bij het uitvoeren van dit hulpprogramma kunt u de volgende opties opgeven:  
    >   
    >  -   / Store:&lt;naam\>  
    > -   / Certificaatverleners:&lt;lijst\>  
    > -   / Criteria:&lt;criteria\>  
    > -   /SelectFirstCert  
    >   
    >  Deze opties zijn respectievelijk gekoppeld aan de  Client.msi-eigenschappen **CCMCERTSTORE**, **CCMCERTISSUERS**, **CCMCERTSEL**en **CCMFIRSTCERT** . Zie voor meer informatie over deze opties [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

7.  Wanneer u er zeker van bent dat voldoende clients is de client-PKI-certificaat voor verificatie via HTTP, volg deze stappen:  

    1.  Implementeer een PKI-webservercertificaat naar een lidserver waarop een bijkomend beheerpunt voor de site zal worden uitgevoerd, en configureer dat certificaat in IIS. Zie voor meer informatie de *het Webservercertificaat voor Sitesystemen die IIS uitvoeren implementeren* sectie het [voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) artikel.  

    2.  Installeer de beheerpuntrol op deze server en configureer de optie **Clientverbindingen** in de beheerpunteigenschappen voor **HTTPS**  

8.  Controleer en verifieer of clients die een PKI-certificaat hebben het nieuwe beheerpunt via HTTPS gebruiken. U kunt IIS-logboekregistratie of prestatiemeteritems gebruiken om dit te verifiëren.  

9. Configureer andere sitesysteemrollen opnieuw voor het gebruik van HTTPS-clientverbindingen. Als u clients wilt beheren op het internet, zorg er dan voor dat sitesystemen een internet-FQDN hebben en configureer individuele beheerpunten en distributiepunten om clientverbindingen van het internet te accepteren.  

    > [!IMPORTANT]  
    >  Voordat u sitesysteemrollen ingesteld om verbindingen via Internet te accepteren, controleert u de planninginformatie en de vereisten voor clientbeheer op Internet. Zie voor meer informatie [communicatie tussen de eindpunten in System Center Configuration Manager](../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

10. Breid de rollout van PKI-certificaat voor clients en sitesystemen die IIS uitvoeren en de sitesysteemrollen voor HTTPS-clientverbindingen en internetverbindingen, zoals vereist in te stellen.  

11. Voor een optimale beveiliging: Als u zeker weet dat alle clients een PKI-certificaat voor verificatie en versleuteling gebruiken, moet u de eigenschappen van de site alleen gebruik van HTTPS wijzigen.  

 Wanneer u dit plan volgt om PKI-certificaten geleidelijk te introduceren, eerst vermindert voor verificatie over HTTP en vervolgens voor verificatie en versleuteling over HTTPS, u het risico dat clients niet beheerd. Bovendien profiteert u van de beste beveiliging die ondersteuning biedt voor Configuration Manager.  

##  <a name="BKMK_PlanningForRTK"></a>Plan voor de vertrouwde basissleutel  
De Configuration Manager vertrouwde basissleutel biedt een mechanisme voor Configuration Manager-clients te verifiëren dat sitesystemen deel uitmaken van hun hiërarchie. Elke siteserver genereert een uitwisselingssleutel om te communiceren met andere sites. De uitwisselingssleutel van de site op het hoogste niveau in de hiërarchie wordt de vertrouwde basissleutel genoemd.  

De functie van de vertrouwde basissleutel in Configuration Manager is vergelijkbaar met een basiscertificaat in een openbare-sleutelinfrastructuur dat alles ondertekend door de persoonlijke sleutel van de vertrouwde basissleutel vertrouwd verder omlaag in de hiërarchie wordt. Bijvoorbeeld door het beheerpuntcertificaat te ondertekenen met de persoonlijke sleutel van het vertrouwde basis-sleutelpaar en een kopie van de openbare sleutel van het vertrouwde basis-sleutelpaar door beschikbaar te maken voor clients, clients kunnen onderscheid maken tussen beheerpunten die zich in hun hiërarchie en beheerpunten die zich niet in hun hiërarchie. Clients gebruiken Windows Management Instrumentation (WMI) voor het opslaan van een kopie van de vertrouwde basissleutel in de **naamruimte** naamruimte.  

Clients kunnen de openbare kopie van de vertrouwde basissleutel automatisch ophalen door gebruik te maken van twee mechanismen:  

-   Het Active Directory-schema wordt uitgebreid voor Configuration Manager, de site is gepubliceerd naar Active Directory Domain Services en clients kunnen deze site-informatie ophalen van een globale-catalogusserver.  

-   Clients worden met behulp van clientpush geïnstalleerd.  

Als clients de vertrouwde basissleutel niet kunnen ophalen via één van deze mechanismen, vertrouwen ze de vertrouwde basissleutel die door het eerste beheerpunt waarmee ze communiceren, wordt verleend. In dit scenario kan de verkeerd een client wordt omgeleid naar een kwaadwillende persoon beheerpunt waarop het beleid van het rogue beheerpunt ontvangt. Dit kan het werk zijn van een geavanceerde aanvaller en kan zich alleen voordoen in een beperkte periode voordat de client de vertrouwde basissleutel ophaalt van een geldig beheerpunt. Echter, u verkleint dit risico van een aanvaller clients naar een rogue beheerpunt omleidt door, u kunt de clients inrichten vooraf met de vertrouwde basissleutel.  

Gebruik de volgende procedures om vooraf in te richten en controleer of de vertrouwde basissleutel voor een Configuration Manager-client:  

-   Richt een client vooraf in met de vertrouwde basissleutel met behulp van een bestand.  

-   Richt een client vooraf in met de vertrouwde basissleutel zonder een bestand.  

-   Verifieer de vertrouwde basissleutel op een client.  

> [!NOTE]  
>  U beschikt niet over een client vooraf inrichten met behulp van de vertrouwde basissleutel als ze dit uit Active Directory Domain Services ophalen kunnen of ze met clientpush worden geïnstalleerd. U hebt bovendien niet aan de clients vooraf in te richten wanneer ze HTTPS-communicatie naar beheerpunten gebruiken, omdat het vertrouwen wordt bevestigd door PKI-certificaten.  

U kunt de vertrouwde basissleutel verwijderen van een client met behulp van de Client.msi-eigenschap **RESETKEYINFORMATION = TRUE**, met CCMSetup.exe. Als u de vertrouwde basissleutel wilt vervangen, installeert u de client opnieuw met de nieuwe vertrouwde basissleutel, bijvoorbeeld door clientpush te gebruiken of door de **SMSPublicRootKey** -eigenschap van Client.msi op te geven met CCMSetup.exe.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-by-using-a-file"></a>Een client vooraf inrichten met de vertrouwde basissleutel door gebruik te maken van een bestand  

1.  Open het bestand in een teksteditor  *&lt;Configuration Manager-map\>***\bin\mobileclient.tcf**.  

2.  Zoek de invoer **SMSPublicRootKey =**, Kopieer de sleutel van die regel en sluit het bestand zonder wijzigingen.  

3.  Maak een nieuw tekstbestand en plak de sleutelinformatie die u van het bestand mobileclient.tcf hebt gekopieerd.  

4.  Sla het bestand op en plaats deze in een locatie waar alle computers toegang toe, maar waarop het bestand wordt beveiligd om manipulatie te voorkomen.  

5.  De client installeren met behulp van een installatiemethode die Client.msi-eigenschappen accepteert en geef de Client.msi-eigenschap **SMSROOTKEYPATH =***&lt;volledig pad en de naam\>*.  

    > [!IMPORTANT]  
    >  Wanneer u de vertrouwde basissleutel voor extra beveiliging tijdens de clientinstallatie opgeeft, moet u ook de sitecode opgeven met behulp van de Client.msi-eigenschap **SMSSITECODE =&lt;sitecode\>**.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-without-using-a-file"></a>Een client vooraf inrichten met de vertrouwde basissleutel en zonder een bestand  

1.  Open het bestand in een teksteditor  *&lt;Configuration Manager-map\>***\bin\mobileclient.tcf**.  

2.  Zoek de invoer, SMSPublicRootKey =, noteer de sleutel van die regel of kopieer deze naar het Klembord en sluit het bestand zonder wijzigingen.  

3.  De client installeren met behulp van een installatiemethode die Client.msi-eigenschappen accepteert en geef de Client.msi-eigenschap **SMSPublicRootKey =***&lt;sleutel\>*, waarbij  *&lt;sleutel\>*  is de tekenreeks die u in mobileclient.tcf kopieerde.  

    > [!IMPORTANT]  
    >  Wanneer u de vertrouwde basissleutel voor extra beveiliging tijdens de clientinstallatie opgeeft, moet u ook de sitecode opgeven met behulp van de Client.msi-eigenschap **SMSSITECODE =&lt;sitecode\>**.  

#### <a name="to-verify-the-trusted-root-key-on-a-client"></a>Verifiëren van de vertrouwde basissleutel op een client.  

1.  Op de **Start** menu kiezen **uitvoeren**, en voer vervolgens **Wbemtest**.  

2.  In de **Windows Management Instrumentation Tester** dialoogvenster Kies **Connect**.  

3.  In de **Connect** het dialoogvenster de **Namespace** Voer **naamruimte**, en kies vervolgens **Connect**.  

4.  In de **Windows Management Instrumentation Tester** het dialoogvenster de **IWbemServices** sectie **klassen opsommen**.  

5.  In de **gegevens over superklasse** dialoogvenster Kies **recursieve**, en kies vervolgens **OK**.  

6.  Scroll in het venster **Queryresultaten** naar onderaan de lijst en dubbelklik vervolgens op **TrustedRootKey ()**.  

7.  In de **Objecteditor voor TrustedRootKey** dialoogvenster Kies **exemplaren**.  

8.  In het nieuwe **queryresultaat** venster waarin de exemplaren van **TrustedRootKey**, dubbelklikt u op **TrustedRootKey = @**.  

9. In de **Objecteditor voor TrustedRootKey = @** het dialoogvenster de **eigenschappen** sectie, schuif omlaag naar **TrustedRootKey CIM_STRING**. De tekenreeks in de rechterkolom is de vertrouwde basissleutel. Controleer of dat deze overeenkomt met de **SMSPublicRootKey** waarde in het bestand  *&lt;Configuration Manager-map\>***\bin\mobileclient.tcf**.  

##  <a name="BKMK_PlanningForSigningEncryption"></a>Plan voor ondertekening en versleuteling  
 Wanneer u PKI-certificaten gebruikt voor alle clientcommunicatie, hoeft u geen plan voor ondertekening en versleuteling te hebben om communicatie van clientgegevens te helpen beveiligen. Maar als u de sitesystemen die IIS zodat HTTP-clientverbindingen uitvoeren instelt, moet u bepalen hoe u om te helpen beveiligen de communicatie van clients voor de site.  

 U kunt gegevens moeten worden ondertekend vereisen ter bescherming van de gegevens die clients naar beheerpunten verzenden. U kunt ook verlangen dat alle ondertekende gegevens van clients die HTTP gebruiken, ondertekend zijn met behulp van het algoritme SHA-256. Hoewel dit een veiliger instelling is, moet u deze optie alleen inschakelen als alle clients SHA-256 ondersteunen. SHA-256 wordt door veel besturingssystemen ondersteund, maar voor oudere besturingssystemen kan een update of hotfix noodzakelijk zijn. Zo moeten computers die Windows Server 2003 SP2 uitvoeren bijvoorbeeld een hotfix installeren waarnaar gerefereerd wordt in het [KB-artikel 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666).  

 Ondertekening helpt de gegevens beveiligen tegen onrechtmatige wijziging; versleuteling helpt de gegevens beveiligen tegen openbaarmaking van informatie. U kunt 3DES-versleuteling inschakelen voor de inventarisgegevens en faseberichten die door clients verstuurd worden naar beheerpunten in de site. U hoeft niet te installeren updates op clients om ondersteuning voor deze optie, maar u kunt de aanvullende CPU-verbruik dat zal worden verplicht op clients en het beheerpunt voor de versleuteling en ontsleuteling.  

 Zie voor meer informatie over het configureren van de instellingen voor ondertekening en versleuteling, de [Configureer ondertekening en versleuteling](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) sectie het [beveiliging configureren in System Center Configuration Manager](../../../core/plan-design/security/configure-security.md) artikel.  

##  <a name="BKMK_PlanningForRBA"></a>Plannen voor op rollen gebaseerd beheer  
 Voor deze informatie, Zie [basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md).  

### <a name="see-also"></a>Zie tevens
[Technische naslaginformatie voor cryptografische besturingselementen voor System Center Configuration Manager](../../../protect/deploy-use/cryptographic-controls-technical-reference.md).  
