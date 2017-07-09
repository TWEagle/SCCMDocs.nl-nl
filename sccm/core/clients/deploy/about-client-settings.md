---
title: Clientinstellingen | Microsoft Docs
description: Kies de instellingen voor client met behulp van de beheerconsole in System Center Configuration Manager.
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c8717925dba42451b1e241a7c2f59e43896d7d99
ms.openlocfilehash: 4a169098f30e4a9d708e41ee25c6a400d5ff0e85
ms.contentlocale: nl-nl
ms.lasthandoff: 06/19/2017

---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>Clientinstellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Alle clientinstellingen in System Center Configuration Manager worden beheerd in de Configuration Manager-console van de **clientinstellingen** knooppunt in de **beheer** werkruimte. Configuration Manager wordt geleverd met een aantal standaardinstellingen. Wanneer u de standaardclientinstellingen wijzigt, worden deze instellingen worden toegepast op alle clients in de hiërarchie. U kunt ook aangepaste clientinstellingen configureren. Deze heffen de standaardclientinstellingen op wanneer u deze toewijst aan verzamelingen. Zie [Clientinstellingen in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-settings.md) voor meer informatie over het configureren van de clientinstellingen.  

Veel van de clientinstellingen behoeven geen uitleg. Anderen worden hier beschreven.  

## <a name="background-intelligent-transfer-service"></a>Background Intelligent Transfer Service  

-   **Beperk de maximale netwerkbandbreedte voor BITS-overdrachten op de achtergrond**  

   Wanneer deze optie is **True** of **Ja**, de clients gebruik van BITS-bandbreedtebeperking.  

-   **Begintijd beperkingsvenster**  

   Geef de lokale begintijd voor de BITS-beperkingsvenster.  

-   **Eindtijd beperkingsvenster**  

   Geef de lokale eindtijd voor de BITS-beperkingsvenster. Als gelijk zijn aan **begintijd Beperkingsvenster**, BITS-beperking altijd ingeschakeld.  

-   **Maximale overdrachtssnelheid tijdens het beperkingsvenster (Kbps)**  

   Geef de maximale overdrachtssnelheid die clients tijdens de periode gebruiken kunnen.  

-   **BITS-downloads buiten het beperkingsvenster toestaan**  

   Selecteer deze optie om toe te staan van Configuration Manager-clients afzonderlijke BITS-instellingen buiten het opgegeven venster gebruiken.  

-   **Maximale overdrachtssnelheid buiten het beperkingsvenster (Kbps)**  

   Geef de maximale overdrachtssnelheid die clients buiten de BITS gebruiken-beperkingsvenster, wanneer u hebt gekozen om toe te staan van BITS-beperking buiten het venster.  

## <a name="client-cache-settings"></a>Clientcache-instellingen

- **BranchCache configureren**

  Vanaf versie 1606 is deze instelling gebruiken voor het instellen van de clientcomputer voor [BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). Stel wilt toestaan BranchCache opslaan in cache op de client **BranchCache inschakelen** naar **Ja**.

- **Clientcachegrootte configureren**

  De clientcache op Windows-computers opslaat tijdelijke bestanden gebruikt voor het installeren van toepassingen en programma's. Kies **Ja** om op te geven **maximale cachegrootte** (megabytes of als percentage van schijf). De grootte van de client-cache kan worden uitgebreid tot de maximale grootte in MB of het percentage van de schijf **is afhankelijk van wat minder**. Als deze optie is **Nee**, de standaardgrootte is 5.120 MB.

## <a name="client-policy"></a>Beleid voor client  

-   **Pollinginterval voor clientbeleid (minuten)**  

   Geef op hoe vaak de volgende Configuration Manager-clients clientbeleid downloaden:  

  -   Windows-computers (bijvoorbeeld desktops, servers, laptops)  

  -   Mobiele apparaten die Configuration Manager schrijft  

  -   Mac-computers  

  -   Computers met Linux of UNIX  

-   **Polling voor gebruikersbeleid inschakelen op clients**  

   Als u deze optie instelt op **True** of **Ja**, en Configuration Manager heeft [de gebruiker gedetecteerd](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), ontvangen clients op computers toepassingen en programma's die bedoeld zijn voor de aangemelde gebruiker.  

   Omdat de Application Catalog de lijst met beschikbare software voor gebruikers van de siteserver ontvangt, deze instelling niet hoeft te worden **True** of **Ja** voor gebruikers wilt weergeven en aanvragen van toepassingen uit de Application Catalog. Maar als deze instelling is **False** of **Nee**, het volgende zal niet werken wanneer gebruikers de Application Catalog gebruiken:  

  -   Gebruikers kunnen de toepassingen in de Application Catalog niet installeren.  

  -   Meldingen over hun goedkeuringsaanvragen voor toepassingen zijn niet zichtbaar voor gebruikers. In plaats daarvan moeten ze de Application Catalog vernieuwen en de goedkeuringsstatus controleren.  

  -   Gebruikers zullen geen revisies en updates ontvangen voor toepassingen die worden gepubliceerd naar de Application Catalog. Maar zien ze wijzigingen aan de toepassingsinformatie in de Application Catalog.  

  -   Als u een toepassingsimplementatie verwijdert nadat de client de toepassing uit de Application Catalog heeft geïnstalleerd, blijven clients tot 2 dagen controleren of de toepassing is geïnstalleerd.  

   Wanneer deze instelling is bovendien **False** of **Nee**, ontvangen gebruikers geen vereiste toepassingen die u voor gebruikers of andere beheertaken in gebruikersbeleid implementeert.  

   Deze instelling geldt voor gebruikers wanneer hun computer op het intranet en Internet is. Dit moet **True** of **Ja** als u ook wilt inschakelen gebruikersbeleid op het Internet.  

-   **Gebruikersbeleidsaanvragen van internetclients inschakelen**  

   Wanneer de client en de site zijn geconfigureerd voor clientbeheer op Internet en u deze optie ingesteld **True** of **Ja** en als de volgende voorwaarden van toepassing, gebruikers ontvangen het gebruikersbeleid wanneer hun computer op Internet is:  

  -   De **de polling voor gebruikersbeleid op clients inschakelen** client-instelling is **True**, of **gebruikersbeleid op clients inschakelen** is **Ja**.  

  -   Het beheerpunt op internet verifieert de gebruiker met behulp van Windows-verificatie (Kerberos of NTLM).  

   Een computer die verbonden is met het internet ontvangt alleen het computerbeleid als u deze optie ingesteld laat op **False** of **Nee**, of als aan een van beide voorwaarden niet wordt voldaan. In dit scenario kunnen gebruikers nog steeds toepassingen zien, aanvragen en installeren uit een Application Catalog op internet. Als deze instelling is **False** of **Nee** maar **de polling voor gebruikersbeleid op clients inschakelen** is **True** of **gebruikersbeleid op clients inschakelen** is **Ja**, ontvangen gebruikers geen gebruikersbeleid totdat de computer is verbonden met het intranet.  

   Zie voor meer informatie over het beheren van clients op het Internet [overwegingen voor clientcommunicatie via Internet of een niet-vertrouwd forest](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) in [communicatie tussen de eindpunten in System Center Configuration Manager](../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

  > [!NOTE]  
  >  Goedkeuringsaanvragen voor toepassingen van gebruikers vereisen geen gebruikersbeleid of gebruikersverificatie.  

##  <a name="compliance-settings"></a>Instellingen voor naleving  

-   **Compatibiliteitsevaluatie plannen**  

     Kies **planning** maken het standaardschema die wordt weergegeven aan gebruikers wanneer ze een configuratiebasislijn implementeren. Deze waarde kan voor elke basislijn worden geconfigureerd in het dialoogvenster **Configuratiebasislijn implementeren** .  

-   **Gebruikersgegevens en -profielen inschakelen**  

     Kies **Ja** als u wilt implementeren [gebruikersgegevens en -profielen](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) configuratie-items voor Windows 8-computers in uw hiërarchie.  

## <a name="computer-agent"></a>Computeragent  

-   **Standaard Application Catalog-websitepunt**  

     Configuration Manager gebruikt deze instelling om gebruikers verbinding met de Toepassingscatalogus vanuit Software Center. U kunt een server opgeven die het Application Catalog-websitepunt host met zijn NetBIOS-naam of FQDN, automatische detectie selecteren of een URL opgeven voor aangepaste implementaties. In de meeste gevallen is automatische detectie de beste keuze, omdat het de volgende voordelen biedt:  

    -   Clients krijgen automatisch een Application Catalog-websitepunt van hun site als hun site een Application Catalog-websitepunt heeft.  

    -   Application Catalog-websitepunten op het intranet die zijn geconfigureerd voor HTTPS voorrang krijgen over die niet zijn geconfigureerd voor HTTPS. Dit biedt bescherming tegen een rogue server.

    -   Wanneer clients zijn geconfigureerd voor beheer op basis van het intranet en Internet clients, ziet deze een internetgebaseerde Application Catalog-websitepunt wanneer ze op het Internet en een intranet gebaseerd Application Catalog-websitepunt wanneer ze zich op het intranet.  

     Automatische detectie garandeert niet dat clients een Application Catalog-websitepunt zullen ontvangen dat het dichtst bij hen ligt. U kunt kiezen om **Automatisch detecteren** niet te gebruiken om volgende redenen:  

     -   U wilt de dichtstbijzijnde server voor clients handmatig configureren of ervoor zorgen dat ze niet met server verbinden via een trage netwerkverbinding.  

     -   U wilt controleren welke clients met welke server verbinding maken. U kunt dit doen voor testdoeleinden, prestaties of zakelijke redenen.  

     -   U wilt niet tot maximaal 25 uur wachten of wachten op een netwerkwijziging voordat clients worden geconfigureerd met een verschillend Application Catalog-websitepunt.  

     Als u de Application Catalog-websitepunt opgeven in plaats van automatische detectie te gebruiken, geeft u de NetBIOS-naam in plaats van de intranet-FQDN. Dit vermindert de kans dat gebruikers wordt gevraagd om referenties wanneer ze met de Application Catalog op het intranet verbinden. De volgende voorwaarden moeten van toepassing zijn om de NetBIOS-naam te gebruiken:  

     -   De NetBIOS-naam is opgegeven in de eigenschappen van het Application Catalog-websitepunt.  

     -   U gebruikt WINS of alle clients bevinden zich in hetzelfde domein als de Application Catalog-websitepunt.  

     -   De Application Catalog-websitepunt is geconfigureerd voor HTTP-clientverbindingen, of deze is geconfigureerd voor HTTPS-clientverbindingen en het webservercertificaat heeft de NetBIOS-naam.  

     Meestal worden gebruikers gevraagd om referenties wanneer de URL een FQDN-naam heeft, maar niet als de URL een NetBIOS-naam. Ga er van uit dat gebruikers altijd om referenties wordt gevraagd wanneer ze verbinden via het internet, omdat deze verbinding het internet-FQDN moet gebruiken. Wanneer gebruikers om referenties wordt gevraagd wanneer ze met het internet zijn verbonden, zorgt u ervoor dat de server waarop het Application Catalog-websitepunt wordt uitgevoerd, kan verbinden met een domeincontroller voor het gebruikersaccount, zodat de gebruiker met behulp van Kerberos kan worden geverifieerd.  

    > [!NOTE]  
    >  Hoe automatische detectie werkt:  
    >   
    >  De client maakt een verzoek om de servicelocatie aan een beheerpunt. Als er een Application Catalog-websitepunt in dezelfde site als de client aanwezig is, wordt de server aan de client gegeven als de te gebruiken Application Catalog-server. Als meer dan één Application Catalog-websitepunt in de site beschikbaar is, heeft een HTTPS-functionaliteit server voorrang op een server die niet is ingeschakeld voor HTTPS. Na dit filteren ontvangen alle clients krijgen een van de servers om te gebruiken als de Application Catalog. Configuration Manager voert geen taakverdeling tussen meerdere servers. Wanneer de site van de client geen een Application Catalog-websitepunt heeft, retourneert het beheerpunt een Application Catalog-websitepunt niet-deterministisch uit de hiërarchie.  
    >   
    >  Wanneer de client zich op het intranet als het gekozen Application Catalog-websitepunt is geconfigureerd met een NetBIOS-naam voor de Application Catalog-URL, krijgen clients deze NetBIOS-naam in plaats van de intranet-FQDN. Alleen het internet-FQDN wordt gegeven aan de client als wordt gedetecteerd dat deze met het internet is verbonden.  
    >   
    >  De client maakt dit verzoek om de servicelocatie elke 25 uur of wanneer deze een netwerkwijziging detecteert. Als de client bijvoorbeeld van het intranet naar het internet overschakelt en de client een beheerpunt op internet kan lokaliseren, geeft het beheerpunt op internet Application Catalog-websitepuntservers op internet aan clients.  

-   **Voeg de standaard Application Catalog-website toe aan de zone met vertrouwde sites in Internet Explorer**  

     Als deze optie is **True** of **Ja**, de huidige standaard Application Catalog-website URL automatisch toegevoegd aan de zone Vertrouwde sites in Internet Explorer op clients.  

     Deze instelling zorgt ervoor dat de instelling in Internet Explorer voor de Beveiligde modus niet is ingeschakeld. Als beveiligde modus is ingeschakeld, kan de Configuration Manager-client mogelijk geen toepassingen uit de Application Catalog installeren. Standaard ondersteunt de zone met vertrouwde sites ook gebruikersaanmelding voor de Application Catalog. Hiervoor is Windows-verificatie is vereist.  

     Als u deze optie ingesteld laat **False**, Configuration Manager-clients mogelijk geen toepassingen installeren uit de Application Catalog, tenzij deze instellingen voor Internet Explorer worden geconfigureerd in een andere zone voor Application Catalog-URL die clients gebruiken.  

    > [!NOTE]  
    >  Wanneer de Configuration Manager een standaard Application Catalog aan de zone met vertrouwde sites toevoegt, verwijdert Configuration Manager een eerdere standaard Application Catalog-URL die Configuration Manager toegevoegd voordat het een nieuw item toevoegt.  
    >   
    >  Configuration Manager kan de URL niet toevoegen als deze al is opgegeven in een van de beveiligingszones. In dit scenario moet u de URL van de andere zone verwijderen of de vereiste instellingen voor Internet Explorer handmatig configureren.  

-   **Toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus**  

     Deze instelling moet **Ja** als gebruikers de Configuration Manager-client wordt uitgevoerd en de Application Catalog gebruiken.  

     Als u deze instelling wijzigt, wordt deze van kracht wanneer gebruikers de browser de volgende keer laden of het geopende browservenster vernieuwen.  

     Zie voor meer informatie over deze instelling [certificaten voor Microsoft Silverlight 5 en verhoogde vertrouwensmodus vereist voor de application catalog](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5) in [beveiliging en privacy voor Toepassingsbeheer in System Center Configuration Manager](../../../apps/plan-design/security-and-privacy-for-application-management.md).  

-   **Weergegeven organisatienaam in Software Center**  

     Typ de naam die wordt weergegeven in Software Center. Deze huismerkgegevens helpen gebruikers om deze toepassing als een vertrouwde bron te identificeren.  

-   **Het nieuwe Software Center gebruiken**  

     Indien ingeschakeld, wordt het nieuwe Software Center gebruiken in alle clientcomputers waarop deze clientinstellingen. Software Center bevat gebruikers beschikbare apps die eerder alleen toegankelijk in de Silverlight-afhankelijke Application Catalog.  

     De Application Catalog-websitepunt en Application Catalog-webservice webservicepunt functies nog steeds vereist zijn voor gebruikers beschikbare apps zijn worden weergegeven in Software Center.  

     Zie [Toepassingsbeheer plannen en configureren in System Center Configuration Manager](../../../apps/plan-design/plan-for-and-configure-application-management.md)   

-   **Installatiemachtigingen**  

    > [!WARNING]  
    >  Deze instelling is van toepassing op de Application Catalog en Software Center. Deze instelling heeft geen effect wanneer gebruikers de bedrijfsportal gebruiken.  

     Configureer hoe gebruikers de installatie van de software, software-updates en takenreeksen kunnen initialiseren:  

    -   **Alle gebruikers**: Gebruikers aangemeld op een clientcomputer met elke machtiging behalve Gast, kunnen de installatie van software, software-updates en takenreeksen initiëren.  

    -   **Alleen beheerders**: Gebruikers die zijn aangemeld op een clientcomputer moeten lid is van de lokale groep Administrators om de installatie van software, software-updates en takenreeksen te initialiseren.  

    -   **Alleen beheerders en Hoofdgebruikers**: Gebruikers die zijn aangemeld op een clientcomputer moeten lid zijn van de lokale groep Administrators of een primaire gebruiker van de computer om de installatie van software, software-updates en takenreeksen te initialiseren.  

    -   **Er zijn geen gebruikers**: Er zijn geen gebruikers aangemeld op een clientcomputer kan de installatie van software, software-updates en takenreeksen kunnen initiëren. Vereiste implementaties voor de computer worden altijd op de deadline geïnstalleerd. Gebruikers kunnen niet de installatie van software uit de Application Catalog of Software Center niet initialiseren.  

-   **Invoer BitLocker-pincode opschorten bij opnieuw opstarten**  

     Als de BitLocker-pincode op computers is geconfigureerd, kan deze optie de vereiste omzeilen om een PINCODE in te geven wanneer de computer opnieuw wordt opgestart na een software-installatie.  

    -   **Altijd**: Configuration Manager wordt tijdelijk onderbroken voor BitLocker, als er software die moet worden opgestart en een opnieuw opstarten van de computer is geïnstalleerd. Deze instelling geldt alleen voor opnieuw opstarten van computer die wordt geïnitieerd door Configuration Manager en schort niet de vereiste de BitLocker-PINCODE opgeven wanneer de gebruiker de computer opnieuw opstart. De invoer van de BitLocker-pincode is opnieuw verplicht na het opstarten van Windows.

    -   **Nooit**: Configuration Manager schort niet BitLocker op de volgende keer opstarten van de computer nadat deze is geïnstalleerd software die moet worden opgestart. In dit scenario kan de software-installatie niet worden voltooid tot de gebruiker de pincode heeft ingevoerd om het standaardopstartproces te voltooien en Windows te laden.

-   **Aanvullende software beheert de implementatie van toepassingen en software-updates**  

     Schakel deze optie alleen in als een van de volgende voorwaarden van toepassing is:  

    -   U gebruikt een leveranciersoplossing waarvoor deze instelling moet worden ingeschakeld.  

    -   U gebruikt de Configuration Manager software development kit (SDK) om clientagentmeldingen en de installatie van toepassingen en software-updates.  

    > [!WARNING]  
    >  Als u deze optie kiest wanneer geen van deze voorwaarden van toepassing is, worden software-updates en vereiste toepassingen niet geïnstalleerd op clients. Deze instelling niet voorkomen dat gebruikers toepassingen uit de Application Catalog installeren, of voorkomen dat pakketten, programma's en takenreeksen op clientcomputers wordt geïnstalleerd.  

-   **PowerShell-uitvoeringsbeleid**  

     Configureren hoe Configuration Manager-clients Windows PowerShell-scripts kunnen uitvoeren. Deze scripts worden vaak gebruikt voor detectie in configuratie-items voor compatibiliteitsinstellingen. Ze kunnen ook worden verzonden in een implementatie als een Standaardscript.  

    -   **Bypass**: Configuration Manager-client omzeilt de Windows PowerShell-configuratie op de clientcomputer zodat niet-ondertekende scripts kunnen uitvoeren.  

    -   **Beperkte**: Configuration Manager-client gebruikt de huidige Windows PowerShell-configuratie op de clientcomputer. Deze configuratie bepaalt of niet-ondertekende scripts kunnen worden uitgevoerd.  

    -   **Alle ondertekende**: Configuration Manager-client scripts alleen uitgevoerd als een vertrouwde uitgever ze heeft ondertekend. Deze beperking is van toepassing onafhankelijk van de huidige Windows PowerShell-configuratie op de clientcomputer.  

     Deze optie vereist ten minste Windows PowerShell versie 2.0. De standaardwaarde is **alle ondertekende**.  

    > [!TIP]  
    >  Als niet-ondertekende scripts niet kunnen worden uitgevoerd vanwege deze clientinstelling, rapporteert Configuration Manager deze fout in de volgende manieren:  
    >   
    > -   Fout-ID **0X87D00327** en de beschrijving van **Script is niet ondertekend** als een implementatiestatusfout in de **bewaking** werkruimte van de Configuration Manager-console.  
    > -   Foutcodes en beschrijvingen van **0X87D00327** en **Script is niet ondertekend** of **0X87D00320** en **de scripthost is nog niet geïnstalleerd** met het fouttype van **Detectiefout** in rapporten. Een voorbeeld is **Details van fouten van configuratie-items in een configuratiebasislijn voor een asset**.  
    > -   Het bericht **Script is niet ondertekend (fout: 87D 00327; Bron: CCM)** in de **DcmWmiProvider.log** bestand.  

-   **Meldingen weergeven voor nieuwe implementaties**  

     Kies **Ja** als u wilt weergeven van een melding voor implementaties die beschikbaar is minder dan een week zijn.  Dit bericht wordt weergegeven telkens wanneer de clientagent wordt gestart.

-   **Willekeurig toepassen van deadline uitschakelen**  

     Deze instelling bepaalt of de client een activeringsvertraging van maximaal twee uur gebruikt voor het installeren van vereiste software-updates wanneer de deadline is bereikt. De vertraging is standaard uitgeschakeld.  

     Voor virtuele desktopinfrastructuur (VDI) scenario's kan deze vertraging kan helpen bij het distribueren van de CPU-verwerking en gegevensoverdracht voor een computer die meerdere virtuele machines die de Configuration Manager-client wordt uitgevoerd. Zelfs als u VDI, installeren veel clients tegelijkertijd dezelfde updates niet gebruikt, kan dit de CPU-gebruik op de siteserver negatief verhogen. Het kan ook aan distributiepunten vertragen en de beschikbare netwerkbandbreedte significant verminderen.  

     Als vereiste software-updates worden geïnstalleerd zonder vertraging wanneer de geconfigureerde deadline is bereikt, kiest u **Ja** voor deze instelling.  

-   **Respijtperiode voor afdwingen na de deadline van de implementatie (uren)**

     In sommige gevallen is het raadzaam om gebruikers meer tijd voor de installatie vereiste implementaties of software-updates buiten een deadlines die u hebt geconfigureerd. Dit kan doorgaans zijn vereist wanneer een computer gedurende langere tijd is uitgeschakeld en moet voor het installeren van een groot aantal toepassing of update-implementaties. Als een gebruiker alleen door vakantie is geretourneerd, moeten ze mogelijk lang wachten terwijl als achterstallig toepassing implementaties zijn geïnstalleerd. U kunt een respijtperiode afdwingen door Configuration Manager-clientinstellingen implementeren naar een verzameling definiëren om dit probleem op te lossen.

     U kunt een respijtperiode van 1 tot 120 uur instellen. Deze instelling wordt gebruikt in combinatie met de implementatie-eigenschap **afdwingen van deze implementatie op basis van gebruikersvoorkeuren uitstellen**. Zie voor meer informatie [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications).

##  <a name="computer-restart"></a>Opnieuw opstarten van computer  
 Wanneer u deze instellingen om de computer opnieuw op te starten specificeert, zorg er dan voor dat de waarde van het tijdelijke meldingsinterval voor opnieuw opstarten en de waarde voor het uiteindelijke aftelinterval korter in duur zijn dan het kortste onderhoudsvenster dat wordt toegepast op de computer.  

 Zie [Onderhoudsvensters gebruiken in System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md) voor meer informatie over onderhoudsvensters.  

##  <a name="endpoint-protection"></a>Endpoint Protection  

-   **Endpoint Protection-client op clientcomputers beheren**  

     Kies **True** of **Ja** als u wilt beheren van bestaande Endpoint Protection-clients op computers in uw hiërarchie.  

     Selecteer deze optie als u de Endpoint Protection-client reeds hebt geïnstalleerd en u wilt beheren met Configuration Manager.  

     Bovendien Kies deze optie als u wilt maken van een script voor het verwijderen van een bestaande antimalwareoplossing de Endpoint Protection-client installeren en dit script wilt implementeren met behulp van een Configuration Manager-toepassing of pakket en programma.  

-   **Endpoint Protection-client op clientcomputers installeren**  

     Kies **True** of **Ja** installeren en activeren van de Endpoint Protection-client op clientcomputers waar deze nog niet is geïnstalleerd.  

    > [!NOTE]  
    >  Als de Endpoint Protection-client al is geïnstalleerd, kiezen **False** of **Nee** om de Endpoint Protection-client niet verwijderen. Om te verwijderen van de Endpoint Protection-client, stelt de **beheren van Endpoint Protection-client op clientcomputers** clientinstelling instelt op **False** of **Nee**. Vervolgens implementeert u een pakket en programma om de Endpoint Protection-client te verwijderen.  

-   **Voor Windows Embedded-apparaten met schrijffilters voert u de installatie van de Endpoint Protection-client door (computer moet opnieuw worden opgestart)**  

     Kies **Ja** uit te schakelen van het schrijffilter op Windows Embedded-apparaat en het apparaat opnieuw opstarten. Hiermee wordt de installatie op het apparaat doorgevoerd.  

     Als **Nee** wordt opgegeven, wordt de client geïnstalleerd op een tijdelijke overlay die wordt gewist wanneer het apparaat opnieuw wordt gestart. In dit scenario wordt de Endpoint Protection-client niet toegewezen tot een andere installatie veranderingen aan het apparaat doorvoert. Dit is de standaardinstelling.  

-   **Opnieuw opstarten vereist computer onderdrukken nadat de Endpoint Protection-client is geïnstalleerd**  

     Kies **True** of **Ja** onderdrukken computer opnieuw wordt opgestart als dat nodig is nadat de Endpoint Protection-client is geïnstalleerd.  

    > [!IMPORTANT]  
    >  Als de Endpoint Protection-client een opnieuw wordt opgestart vereist en deze instelling is **False**, de wordt opnieuw opgestart ongeacht enig onderhoudsvensters die zijn geconfigureerd.  

-   **Toegestane periode die gebruikers verplicht opnieuw opstarten om de installatie van Endpoint Protection te voltooien kan uitstellen (uur)**  

     Geef het aantal uren dat gebruikers een opnieuw opstarten van computer uitstellen kunnen als dit vereist is nadat de Endpoint Protection-client is geïnstalleerd. Deze optie kan worden geconfigureerd als alleen de **onderdrukken eventuele vereiste computer opnieuw wordt opgestart nadat de Endpoint Protection-client is geïnstalleerd** optie is **False**.  

-   **Alternatieve bronnen (zoals Windows Update, Microsoft Windows Server Update Services of UNC-shares) uitschakelen voor de initiële definitie-update op clientcomputers**  

     Kies **True** of **Ja** als u wilt dat Configuration Manager alleen de initiële definitie-update op clientcomputers installeren. Deze instelling kan nuttig zijn om onnodige netwerkverbindingen te vermijden en netwerkbandbreedte te verminderen tijdens de initiële installatie van de definitie-update.  

##  <a name="hardware-inventory"></a>Hardware-inventaris  

-   **Maximale grootte aangepast MIF-bestand (KB)**  

     Geef de maximale grootte in kB, toegestaan voor elk aangepast Management Information Format (MIF)-bestand dat van een client worden verzameld tijdens een hardware-inventarisatiefase. Als bepaalde MIF-bestanden groter zijn dan deze limiet, kan de hardware-inventaris van Configuration Manager deze wordt niet verwerkt. U kunt een grootte van 1 tot en met 5000 KB opgeven. Deze waarde is standaard ingesteld op 250 KB. Deze instelling heeft geen invloed op de grootte van het normale hardware-inventarisgegevensbestand.  

    > [!NOTE]  
    >  Deze instelling is alleen beschikbaar in de standaardclientinstellingen.  

-   **Hardware-inventarisklassen**  

     In Configuration Manager kunt u de hardware-informatie die u van clients verzamelt zonder het sms_def.mof-bestand handmatig bewerkt uitbreiden. Kies **klassen instellen** als u wilt uitbreiden van hardware-inventaris van Configuration Manager. Zie voor meer informatie [hardware-inventaris configureren in System Center Configuration Manager](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

-   **MIF-bestanden verzamelen**  

     Gebruik deze instelling kunt u opgeven of voor het verzamelen van MIF-bestanden van Configuration Manager-clients tijdens hardware-inventaris.  

     Voor een MIF-bestand moeten worden verzameld door hardware-inventaris, moet deze in de juiste locatie op de clientcomputer. De bestanden bevinden zich standaard als volgt:  

    -   IDMIF-bestanden moet in de map Windows\System32\CCM\Inventory\Idmif.  

    -   NOIDMIF-bestanden moet in de map Windows\System32\CCM\Inventory\Noidmif.  

    > [!NOTE]  
    >  Deze instelling is alleen beschikbaar in de standaardclientinstellingen.

-   **Maximale vertraging voor willekeurige**

    De verzameling van hardware-informatie is ingedeeld met maximaal vier uur zodat de bewerking niet gelijktijdig op alle clients plaatsvinden. U kunt de maximale wachttijd instellen om te kunnen beperken van de tijd gedurende welke de bewerking plaatsvindt.      

##  <a name="metered-internet-connections"></a>Internetverbindingen naar gebruik  
 U kunt beheren hoe Windows 8-clientcomputers communiceren met Configuration Manager-sites wanneer ze internetverbindingen naar gebruik gebruiken. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

> [!NOTE]  
>  De geconfigureerde clientinstelling wordt in de volgende scenario's niet toegepast op Windows 8-clientcomputers:  
>   
> -   De computer zich op een roaming gegevensverbinding: Configuration Manager-client voert geen taken waarbij gegevens worden overgedragen naar Configuration Manager-sites.  
> -   De verbindingseigenschappen van de Windows-netwerk zijn geconfigureerd als zonder datalimiet: Configuration Manager-client gedraagt zich alsof dit een internetverbinding zonder datalimiet is en bijgevolg gegevens naar de Configuration Manager-sites verstuurt.  

-   **Clientcommunicatie bij internetverbindingen naar gebruik**  

     Kies uit de vervolgkeuzelijst een van de volgende voor Windows 8-clientcomputers:  

    -   **Toestaan dat**: Alle clientcommunicaties zijn toegestaan via de internetverbinding met datalimiet tenzij het clientapparaat een roaming gegevensverbinding gebruikt.  

    -   **Limiet**: De volgende clientcommunicaties zijn toegestaan over de internetverbinding met datalimiet:  

        -   Clientbeleid ophalen  

        -   Clientstatusberichten om te verzenden naar de site  

        -   Software-installatieaanvragen via de Application Catalog  

        -   Vereiste implementaties (zodra de installatiedeadline wordt bereikt)  

        > [!IMPORTANT]  
        >  Als een gebruiker een software-installatie vanuit Software Center of de Application Catalog start, zijn deze altijd toegestaan, ongeacht de instellingen van de gecontroleerde internetverbinding.  

         Als de gegevensoverdrachtlimiet voor de internetverbinding met datalimiet is bereikt, probeert de client niet langer te communiceren met Configuration Manager-sites.  

    -   **Blok**: Configuration Manager-client probeert niet te communiceren met Configuration Manager-sites wanneer deze zich op een internetverbinding. Dit is de standaardwaarde.  

##  <a name="power-management"></a>Energiebeheer  

-   **Toestaan dat gebruikers hun apparaat uit energiebeheer uitsluiten**  

     Kies in de vervolgkeuzelijst **True** of **Ja** zodat gebruikers van Software Center hun computer uitsluiten van een geconfigureerde energiebeheerinstellingen.  

-   **Wake-up proxy inschakelen**  

     Specificeer **Ja** om te voorzien in de instelling van de Wake On LAN van de site wanneer hij geconfigureerd wordt voor unicast pakketten.  

     Zie voor meer informatie over wake-up proxy [plannen voor ontwaken van clients in System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

    > [!WARNING]  
    >  Schakel wake-up proxy niet in een productienetwerk in zonder eerst te begrijpen hoe het werkt en het te beoordelen in een testomgeving.  

-   **Poortnummer wake-up proxy (UDP)**  

     Hou de standaardwaarde voor het poortnummer die computers gebruiken voor het verzenden van ontwaakpakketten naar slapende computers worden beheerd. Of het aantal verandert in een waarde van uw keuze.  

     Het hier opgegeven poortnummer is automatisch geconfigureerd voor clients die Windows Firewall uitvoeren wanneer u de **Windows Firewall-uitzondering voor wake-up proxy** optie. Indien clients een andere firewall uitvoeren, moet u hem handmatig configureren om het UDP-poortnummer toe te staan dat opgegeven is voor deze instelling.  

-   **Poortnummer Wake On LAN (UDP)**  

     Hou de standaardwaarde van 9, tenzij u het Wake On LAN (UDP) poortnummer hebt gewijzigd op de **poorten** tabblad van de site **eigenschappen**.  

    > [!IMPORTANT]  
    >  Dit nummer moet overeenkomen met het nummer in de **Eigenschappen**van de site. Als u dit nummer op één plaats wijzigt, is niet het automatisch bijgewerkt op de andere plaats.  

##  <a name="remote-tools"></a>Externe hulpprogramma 's  

-   **Beheer op afsten op clients inschakelen** en **Firewall-uitzonderingsprofielen**  

     Kies of Configuration Manager extern beheer is ingeschakeld voor alle clientcomputers die deze clientinstellingen ontvangen. Kies **configureren** beheer op afstand inschakelen. Configureer desgewenst firewall-instellingen voor extern beheer om te werken op clientcomputers.  

     Beheer op afstand is standaard uitgeschakeld.  

    > [!IMPORTANT]  
    >  Indien firewall-instellingen niet geconfigureerd zijn, zal het kunnen gebeuren dat externe controle niet juist werkt.  

-   **Gebruikers kunnen instellingen voor beleid of meldingen in Software Center wijzigen**  

     Kies of gebruikers externe controle-opties van Software Center kunnen wijzigen.  

-   **Extern beheer van een onbeheerde computer toestaan**  

     Kies of een beheerder extern beheer gebruiken kan voor toegang tot een clientcomputer die afgemeld is of vergrendeld. Alleen een computer is aangemeld en ontgrendeld kan extern worden beheerd wanneer deze instelling is uitgeschakeld.  

-   **Gebruiker vragen naar machtiging voor beheer op afstand**  

     Kies of de clientcomputer een bericht waarin wordt gevraagd om toestemming voordat een sessie voor extern beheer van de gebruiker wordt weergegeven.  

-   **Machtigingen voor beheer op afstand toekennen aan lokale groep beheerders**  

     Kies of de externe controle-sessies op clientcomputers kan worden gemaakt door de lokale beheerders op de server waarop de beheer op afstand verbinding initieert.  

-   **Toegestaan toegangsniveau**  

     Specificeer het niveau van externe controle toegang dat zal toegestaan zijn. U kunt kiezen uit:  

    -   Volledig beheer  

    -   Alleen weergeven  

    -   Geen  

-   **Toegestane viewers**  

     Kies **Stel Viewers** openen de **Configureer Clientinstelling** dialoogvenster en geef de namen van de Windows-gebruikers die externe controlesessies naar clientcomputers kunnen instellen.  

-   **Sessiemeldingspictogram weergeven op de taakbalk**  

     Selecteer deze optie om weer te geven van een pictogram op de taakbalk van client computers om aan te geven dat een externe controlesessie actief is.  

-   **Sessieverbindingsbalk weergeven**  

     Selecteer deze optie om weer te geven van een hoge visibiliteit sessieverbindingsbalk op client computers om aan te geven dat een externe controlesessie actief is.  

-   **Een geluid afspelen op client**  

     Selecteer deze optie om geluid te gebruiken om aan te geven wanneer een externe controlesessie actief op een clientcomputer is. U kunt geluid afspelen wanneer de sessie verbinding maakt of de verbinding verbreekt, of u kunt herhaaldelijk geluid afspelen tijdens de sessie.  

-   **Instellingen voor ongevraagde hulp op afstand beheren**  

     Kies deze optie om Configuration Manager ongevraagde externe hulpsessies te beheren.  

     In een sessie ongevraagde hulp op afstand de gebruiker op de clientcomputer is niet om hulp vragen aan de sessie te starten.  

-   **Instellingen voor gevraagde hulp op afstand beheren**  

     Kies deze optie om Configuration Manager gevraagde externe hulpsessies te beheren.  

     In een sessie Aangevraagde hulp op afstand heeft de gebruiker op de clientcomputer een aanvraag verzonden naar de beheerder voor hulp op afstand.  

-   **Toegangsniveau voor hulp op afstand**  

     Kies het niveau van toegang toe te wijzen om externe hulpsessies die geïnitieerd zijn in de Configuration Manager-console.  

    > [!NOTE]  
    >  De gebruiker op de clientcomputer moet altijd toegang verlenen opdat een externe hulpsessie zou kunnen plaatsvinden.  

-   **Instellingen voor extern bureaublad beheren**  

     Kies deze optie om Configuration Manager beheren van extern bureaublad-sessies voor computers.  

-   **Toegelaten viewers toestaan om verbinding te maken via externe bureaublad-verbinding**  

     Selecteer deze optie om gebruikers in die zijn opgegeven in de lijst met toegelaten viewers worden toegevoegd aan de lokale gebruikersgroep van extern bureaublad op clientcomputers te laten.  

-   **Eis verificatie op netwerkniveau op computers die het besturingssysteem Windows Vista en latere versies uitvoeren.**  

     Selecteer deze veiliger optie als u gebruiken van verificatie op netwerkniveau wilt voor extern bureaublad-verbindingen op clientcomputers met Windows Vista of hoger. Verificatie op netwerkniveau vereist in eerste instantie minder externe computerbronnen omdat het gebruikersverificatie is voltooid voordat het een extern bureaublad-verbinding tot stand brengt. Deze methode is veiliger omdat hij kan helpen de computer te beschermen tegen gebruikers of software met kwaadwillige bedoelingen, en hij het risico op Denial-of-Service-aanvallen vermindert.  

## <a name="software-deployment"></a>Software-implementatie  

-   **Nieuwe evaluatie voor implementaties plannen**  

     Configureer een planning voor wanneer de Configuration Manager de regels voor vereisten voor alle implementaties opnieuw beoordeelt. De standaardwaarde is elke 7 dagen.  

    > [!IMPORTANT]  
    >  U wordt aangeraden dat u deze waarde niet op een lagere waarde dan de standaardwaarde wijzigt. Dat doet, kan de prestaties van uw netwerk en clientcomputers negatief beïnvloeden.  

     U kunt ook deze actie van een Configuration Manager-clientcomputer initiëren door het kiezen van de actie **Beoordelingscyclus toepassingsimplementatie** van de **acties** tabblad van **Configuration Manager** in het Configuratiescherm.  

##  <a name="software-inventory"></a>Software-inventaris  

-   **Detail inventarisrapportage**  

     Geef het niveau op van te inventariseren bestandsgegevens. U kunt details over het bestand, details over het product die zijn gekoppeld aan het bestand of alle informatie over het bestand inventariseren.  

-   **Deze bestandstypen inventariseren**  

     Als u opgeven welke typen bestand dat u wilt inventariseren wilt, kiest u **Stel typen** en configureer vervolgens de volgende items in de **Configureer Clientinstelling** in het dialoogvenster:  

    > [!NOTE]  
    >  Als u meerdere aangepaste clientinstellingen worden toegepast op een computer, wordt de inventaris die wordt geretourneerd voor elke instelling samengevoegd.  

    -   Kies de **nieuw** pictogram toevoegen van een nieuw bestandstype aan inventaris. Geef vervolgens de volgende informatie in de **eigenschappen geïnventariseerd bestand** in het dialoogvenster:  

        -   **Naam**: Geef een naam voor het bestand dat u wilt inventariseren. U kunt de * *\**  teken om weer te geven welke tekst van tekenreeksen en de **?** teken om om het even welk enkelvoudig teken voor te stellen. Bijvoorbeeld, als u inventariseren van alle bestanden met de extensie .doc wilt, de bestandsnaam opgeven  **\*.doc**.  

        -   **Locatie**: Kies **ingesteld** openen de **padeigenschappen** in het dialoogvenster. U kunt software-inventaris om te zoeken alle harde schijven voor het opgegeven bestand, zoek een opgegeven pad (bijvoorbeeld **C:\Folder**), of zoeken naar een opgegeven variabele (bijvoorbeeld *% windir %*). U kunt ook zoeken in alle Deelmappen onder het opgegeven pad.  

        -   **Sluit versleutelde en gecomprimeerde bestanden**: Als u deze optie kiest, worden alle bestanden die gecomprimeerd of versleuteld, niet geïnventariseerd.  

        -   **Sluit bestanden uit in de map Windows**: Als u deze optie kiest, wordt alle bestanden in de Windows-map en haar Deelmappen niet geïnventariseerd.  

    -   Kies **OK** sluiten de **eigenschappen geïnventariseerd bestand** in het dialoogvenster.  

    -   Voeg alle bestanden die u wilt inventariseren en kies vervolgens **OK** sluiten de **Configureer Clientinstelling** in het dialoogvenster.  

-   **Bestanden verzamelen**  

     Als u bestanden te verzamelen van clientcomputers, kiest u **Stel bestanden** en configureer dan het volgende:  

    > [!NOTE]  
    >  Als u meerdere aangepaste clientinstellingen worden toegepast op een computer, wordt de inventaris die wordt geretourneerd voor elke instelling samengevoegd.  

    -   In de **Configureer Clientinstelling** dialoogvenster Kies de **nieuw** pictogram voor het toevoegen van een bestand moet worden verzameld.  

    -   Voer, in het dialoogvenster **Eigenschappen verzameld bestand** , de volgende informatie in:  

        -   **Naam**: Geef een naam voor het bestand dat u wilt verzamelen. U kunt de * *\**  teken om weer te geven welke tekst van tekenreeksen en de **?** teken om om het even welk enkelvoudig teken voor te stellen.  

        -   **Locatie**: Kies **ingesteld** openen de **padeigenschappen** in het dialoogvenster. U kunt software-inventaris om te zoeken naar alle harde schijven voor het bestand dat u wilt verzamelen, zoek een opgegeven pad (bijvoorbeeld **C:\Folder**), of zoeken naar een opgegeven variabele (bijvoorbeeld *% windir %*). U kunt ook zoeken in alle Deelmappen onder het opgegeven pad.  

        -   **Sluit versleutelde en gecomprimeerde bestanden**: Als u deze optie kiest, worden alle bestanden die gecomprimeerd of versleuteld niet verzameld.  

        -   **Stoppen met verzamelen van bestanden wanneer de totale grootte van de bestanden overschrijdt (KB)**: Geef de bestandsgrootte (in kB) die geen bestanden opgegeven onder meer **naam** zullen worden verzameld.  

          > [!NOTE]  
          >  De siteserver verzamelt de vijf meest recent gewijzigde versies van verzamelde bestanden en slaat ze op in de  *&lt;installatiemap van Configuration Manager\>*\Inboxes\Sinv.box\Filecol directory. Indien een bestand niet gewijzigd werd sedert de laatste software-inventaris werd verzameld, zal het bestand niet opnieuw verzameld worden.  
          >   
          >  Software-inventaris verzamelt geen bestanden groter dan 20 MB.  
          >   
          >  De waarde **maximale grootte voor alle verzamelde bestanden (KB)** in de **Configureer Clientinstelling** in het dialoogvenster ziet u de maximale grootte voor alle verzamelde bestanden. Wanneer deze grootte is bereikt, stopt bestandsverzameling. Alle reeds verzamelde bestanden worden weerhouden en naar de siteserver gezonden.  

          > [!IMPORTANT]
          >  Indien u software-inventaris configureert om vele grote bestanden te verzamelen, kan dit de prestaties van uw netwerk en siteserver negatief beïnvloeden.  

        Zie voor meer informatie over het raadplegen van verzamelde bestanden [Resource Explorer gebruiken om software-inventaris in System Center Configuration Manager weer te geven](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

    -   Kies **OK** sluiten de **eigenschappen verzameld bestand** in het dialoogvenster.  

    -   Voeg alle bestanden die u wilt verzamelen, en kies vervolgens **OK** sluiten de **Configureer Clientinstelling** in het dialoogvenster.  

-   **Namen instellen**  

     Tijdens software-inventarisatie, worden namen van fabrikanten en productnamen geëxtraheerd uit de informatie van de kop van bestanden die geïnstalleerd zijn op clients op de site. Omdat deze namen niet altijd gestandaardiseerd zijn in de informatie van de bestandskop, kunnen soms verschillende versies van dezelfde fabrikant of productnaam verschijnen wanneer u software-inventaris-informatie raadpleegt in Resource Explorer of u query's draait. Als u wenst te standaardiseren deze weergavenamen, kiest u **Stel namen** en configureer vervolgens de volgende items in de **Configureer Clientinstelling** in het dialoogvenster:  

    -   **Naamtype**: Software-inventaris verzamelt informatie over fabrikanten en producten. Kies in de vervolgkeuzelijst of u wilt configureren weergavenamen voor een **fabrikant** of een **Product**.  

    -   **Weergavenaam**: Geef de weergavenaam op die u wilt gebruiken in plaats van de namen in de **geïnventariseerde namen** lijst. U kunt de **nieuw** pictogram om op te geven van een nieuwe weergavenaam.  

    -   **Geïnventariseerde namen**: Kies de **nieuw** pictogram voor het toevoegen van een nieuwe geïnventariseerde naam die wordt vervangen in software-inventaris door de naam van de gekozen in de **weergavenaam** lijst. U kunt meerdere namen die worden vervangen toevoegen.  

##  <a name="software-updates"></a>Software-updates  

-   **Software-updates op clients inschakelen**  

     Deze instelling gebruiken om softwareupdates inschakelen op Configuration Manager-clients. Wanneer u deze instelling uitschakelt, verwijdert Configuration Manager de bestaande implementatiebeleiden van de client. Wanneer u deze instelling opnieuw inschakelt, zal de client het huidige implementatiebeleid downloaden.  

    > [!IMPORTANT]  
    >  Wanneer u deze instelling uitschakelt, werkt NAP en beleidsregels voor compatibiliteitsinstellingen die afhankelijk van de Apparaatinstelling voor software-updates zijn niet meer.  

-   **Planning software-updatescan**  

     Gebruik deze instelling om op te geven hoe dikwijls een client een scan initieert voor het beoordelen van naleving door software-updates. De scan voor beoordeling van naleving bepaalt de status voor software-updates op de client (bijvoorbeeld vereist of geïnstalleerd). Zie voor meer informatie over nalevingsbeoordeling [beoordeling van compatibiliteit van Software-updates](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

     Standaard wordt een eenvoudige planning gebruikt en de scan voor naleving wordt gestart om de zeven dagen. U kunt kiezen om een aangepaste planning te creëren om een exacte startdatum en starttijd op te geven, kiezen of u UTC of de lokale tijd gebruikt en het terugkerende interval configureren voor een specifieke dag van de week.  

    > [!NOTE]  
    >  Als u een interval van minder dan 1 dag opgeeft, wordt Configuration Manager automatisch standaard op 1 dag.  

    > [!WARNING]  
    >  De daadwerkelijke starttijd op clientcomputers is de starttijd plus een willekeurige tijdshoeveelheid tot maximaal 2 uur. Hiermee wordt voorkomen dat clientcomputers op hetzelfde moment de scan starten en verbinding maken met WSUS (Windows Server Update Services) op de actieve software-updatepuntserver.  

-   **Nieuwe evaluatie van implementatie plannen**  

     Gebruik deze instelling configureren hoe vaak de Clientagent voor Software-Updates opnieuw evalueert software-updates voor de installatiestatus van Configuration Manager-clientcomputers. Wanneer software-updates die eerder zijn geïnstalleerd op clientcomputers niet meer worden gevonden en nog steeds vereist, worden deze opnieuw geïnstalleerd.

     Het schema voor nieuwe evaluatie moet worden aangepast op basis van bedrijfsbeleid voor compatibiliteit van software-update, of gebruikers de mogelijkheid hebben om te verwijderen van software-updates, enzovoort. Houd er rekening mee dat elke cyclus voor het nieuwe evaluatie in een netwerk en clientcomputers computer CPU-activiteit resulteert. Standaard wordt een eenvoudige planning gebruikt en de implementatie van nieuwe evaluatiescan wordt gestart om de zeven dagen.  

    > [!NOTE]  
    >  Als u een interval van minder dan 1 dag opgeeft, wordt Configuration Manager automatisch standaard op 1 dag.  

-   **Installeer, wanneer een deadline voor software-updates is bereikt, alle andere implementaties van software-updates met een deadline die binnen een bepaalde periode valt**  

     U kunt via deze instelling alle software-updates installeren in vereiste implementaties met deadlines die binnen een bepaalde periode vallen. Wanneer een deadline is bereikt voor een vereiste software-update-implementatie, de installatie wordt gestart op de clients voor de software-updates in de implementatie. Deze instelling bepaalt of tevens moet worden gestart met de installatie van software-updates die in andere vereiste implementaties met een geconfigureerde deadline binnen de bepaalde periode zijn gedefinieerd.  

     U kunt via deze instelling de installatie van software-updates voor vereiste software-updates versnellen, mogelijkerwijs de beveiliging verbeteren, mogelijkerwijs het aantal weergegeven meldingen verminderen en mogelijkerwijs het aantal malen verminderen dat clientcomputers opnieuw moeten worden opgestart. Deze instelling is standaard uitgeschakeld.  

-   **De periode gedurende welke alle in afwachting zijnde implementaties met deadlines in deze periode eveneens worden geïnstalleerd**  

     U kunt via deze instelling de tijdsfasering voor de vorige instelling opgeven. U kunt een waarde tussen 1 en 23 uur en tussen 1 en 365 dagen invoeren. Deze instelling is standaard geconfigureerd op 7 dagen.  

-   **Installatie van bestanden voor snelle installatie op clients inschakelen**

-   **Poort die wordt gebruikt voor het downloaden van inhoud voor de bestanden voor snelle installatie**

-   **Schakel het beheer van de Office 365 Client opnieuw** deze instelling gebruiken om het beheer van de Office 365-Clientagent inschakelen. Als u de waarde instelt op **Ja**, kunt u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud levering bedrijfsnetwerken (CDN) en de bestanden kunnen worden geïmplementeerd als een toepassing in Configuration Manager.

##  <a name="user-and-device-affinity"></a>Affiniteit van gebruiker en apparaat  

-   **Gebruiksdrempel affiniteit van gebruiker met apparaat (minuten)**  

     Geef het aantal minuten voordat Configuration Manager toewijzing maakt voor een gebruiker apparaataffiniteit.  

-   **Gebruiksdrempel affiniteit van gebruiker met apparaat (dagen)**  

     Geef het aantal dagen op waarover de op gebruik gebaseerde affiniteitsdrempel wordt gemeten.  

    > [!NOTE]  
    >  Bijvoorbeeld, als **gebruiker gebruiksdrempel apparaataffiniteit (minuten)** is opgegeven als **60** minuten en **gebruiksdrempel van affiniteit van gebruiker-apparaat (dagen)** is opgegeven als **5** dagen, de gebruiker moet het apparaat gebruiken gedurende 60 minuten over een periode van 5 dagen gebruikersaffiniteit met apparaat automatisch wordt gemaakt.  

-   **Affiniteit van gebruikers met apparaat automatisch configureren via gebruiksgegevens**  

     Kies **True** of **Ja** zodat Configuration Manager automatisch gebruikersaffiniteiten met apparaten op basis van de gebruiksgegevens die worden verzameld.  

##  <a name="mobile-devices"></a>Mobiele apparaten  

-   **Inschrijvingsprofiel voor mobiele apparaten**  

     Voordat u deze instelling kan configureren, moet u eerst de gebruikersinstelling voor mobiele apparaten **Gebruikers toestaan om mobiele apparaten in te schrijven** op **Waar**instellen. Vervolgens kunt u **profiel instellen** om op te geven van een inschrijvingsprofiel bevat informatie over de certificaatsjabloon die moet worden gebruikt tijdens het inschrijvingsproces, de site die een inschrijvingspunt en inschrijvingsproxypunt bevat en de site die het apparaat na inschrijving beheert.  

    > [!IMPORTANT]  
    >  Zorg ervoor dat u het certificaatsjabloon hebt geconfigureerd dat u wilt gebruiken voor de inschrijving van mobiele apparaten, voordat u deze optie configureert.  

##  <a name="enrollment"></a>Inschrijving  

-   **Inschrijvingsprofiel voor mobiele apparaten**  

     Voordat u deze instelling kan configureren, moet u eerst de gebruikersinstelling voor inschrijving **Gebruikers toestaan om mobiele apparaten en Mac-computers in te schrijven** op **Ja**instellen. Vervolgens kunt u **profiel instellen** om op te geven van een inschrijvingsprofiel bevat informatie over de certificaatsjabloon die moet worden gebruikt tijdens het inschrijvingsproces, de site die een inschrijvingspunt en inschrijvingsproxypunt bevat en de site die het apparaat na inschrijving beheert.  

    > [!IMPORTANT]  
    >  Zorg ervoor dat u de certificaatsjabloon hebt geconfigureerd die u wilt gebruiken voor de inschrijving van mobiele apparaten of voor de inschrijving van de Mac-client, voordat u deze optie configureert.  

## <a name="user-and-device-affinity"></a>Affiniteit van gebruiker en apparaat  

-   **Gebruikers toestaan hun primaire apparaten te definiëren**  

     Opgeven of gebruikers hun eigen primaire apparaten te identificeren kunnen op de **mijn apparaten** tabblad van de Application Catalog.  

