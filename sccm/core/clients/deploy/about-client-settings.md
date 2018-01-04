---
title: Clientinstellingen
titleSuffix: Configuration Manager
description: Kies de instellingen voor client met behulp van de beheerconsole in System Center Configuration Manager.
ms.custom: na
ms.date: 12/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
caps.latest.revision: "15"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fe6b3508b7d54dca1d80818c159cfd4b723f7986
ms.sourcegitcommit: f1535281b2c3fecff773b722c3f7590bf6ba10a0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/03/2018
---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>Clientinstellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheert alle clientinstellingen in de Configuration Manager-console van de **clientinstellingen** knooppunt in de **beheer** werkruimte. Configuration Manager wordt geleverd met een aantal standaardinstellingen. Wanneer u de standaardclientinstellingen wijzigt, worden deze instellingen worden toegepast op alle clients in de hiërarchie. U kunt ook aangepaste clientinstellingen die de standaardclientinstellingen overschrijven wanneer u deze instellingen aan verzamelingen toewijst configureren. Zie voor meer informatie [het configureren van clientinstellingen](../../../core/clients/deploy/configure-client-settings.md).  
 

## <a name="background-intelligent-transfer-service"></a>Background Intelligent Transfer Service  

-   **Beperk de maximale netwerkbandbreedte voor BITS-overdrachten op de achtergrond**   </br>
   Wanneer deze optie is **Ja**, clients gebruiken de BITS-bandbreedtebeperking. Als u wilt de overige instellingen in deze groep configureert, moet u deze instelling inschakelen. 

-   **Begintijd beperkingsvenster**   </br>
   Geef de lokale begintijd voor de BITS-beperkingsvenster.  

-   **Eindtijd beperkingsvenster**   </br>
   Geef de lokale eindtijd voor de BITS-beperkingsvenster. Als gelijk zijn aan **begintijd Beperkingsvenster**, BITS-beperking altijd ingeschakeld.  

-   **Maximale overdrachtssnelheid tijdens het beperkingsvenster (Kbps)** </br>
    Hiermee geeft u de maximale overdrachtssnelheid die clients tijdens de periode gebruiken kunnen.  

-   **BITS-downloads buiten het beperkingsvenster toestaan**   </br>
   Toestaan dat clients afzonderlijke BITS-instellingen buiten het opgegeven venster gebruiken.  

-   **Maximale overdrachtssnelheid buiten het beperkingsvenster (Kbps)**   </br>
   Geef de maximale overdrachtssnelheid die clients buiten de BITS gebruiken-beperkingsvenster.  



## <a name="client-cache-settings"></a>Clientcache-instellingen

- **BranchCache configureren** </br>
  Gebruik deze instelling voor het instellen van de clientcomputer voor [Windows BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). Stel wilt toestaan BranchCache opslaan in cache op de client **BranchCache inschakelen** naar **Ja**.

    - **BranchCache inschakelen** </br>
    Hiermee schakelt BranchCache op clientcomputers.

    - **Cachegrootte maximale BranchCache (percentage van de schijf)** </br>
    Het percentage van de schijf waardoor BranchCache te gebruiken. 

- **Clientcachegrootte configureren** </br>
  De Configuration Manager-clientcache op Windows-computers opslaat tijdelijke bestanden gebruikt voor het installeren van toepassingen en programma's. Als deze optie is **Nee**, de standaardgrootte is 5.120 MB.</br>
    Kies **Ja**, geef vervolgens:
    - **Maximale cachegrootte (MB)**
    - **Maximumcachegrootte (percentage van de schijf)** </br>
    De grootte van de client-cache wordt uitgebreid tot de maximale grootte in megabytes (MB) of het percentage van de schijf *is afhankelijk van wat minder*. 

- **Inschakelen van Configuration Manager-client in volledige OS in staat om inhoud te delen** </br>
    Hiermee [peer-cache](/sccm/core/plan-design/hierarchy/client-peer-cache) voor Configuration Manager-clients. Kies **Ja**, geef poortinformatie waarmee de client communiceert vervolgens met de peercomputer. 
    - **Poort voor oorspronkelijke netwerk-broadcast** (standaard 8004)
    - **Poort voor downloaden van inhoud van peer** (8003 standaard) </br>
    Windows Firewall-regels zodat dit verkeer wordt automatisch geconfigureerd door Configuration Manager. Als u een andere firewall gebruikt, moet u regels voor dit verkeer handmatig configureren.




## <a name="client-policy"></a>Beleid voor client  

-   **Pollinginterval voor clientbeleid (minuten)**  </br>
     Hiermee geeft u op hoe vaak de volgende Configuration Manager-clients clientbeleid downloaden:  
      -   Windows-computers (bijvoorbeeld desktops, servers, laptops)  
      -   Mobiele apparaten die Configuration Manager schrijft  
      -   Mac-computers  
      -   Computers met Linux of UNIX  

-   **Gebruikersbeleid op clients inschakelen**   </br>
   Als u deze optie instelt op **Ja**, en gebruik [gebruikersdetectie](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), ontvangt van clients op de toepassingen en programma's die zijn gericht op de aangemelde gebruiker.  

    De Application Catalog ontvangt de lijst met beschikbare software voor gebruikers van de siteserver. Deze instelling hoeft dus niet te worden **Ja** voor gebruikers wilt weergeven en aanvragen van toepassingen uit de Application Catalog. Als deze instelling is **Nee**, de volgende problemen werken niet als gebruikers de Application Catalog gebruiken:  

      -   Gebruikers kunnen de toepassingen in de Application Catalog niet installeren.  

      -   Gebruikers zien niet meldingen over hun goedkeuringsaanvragen voor toepassingen. In plaats daarvan moeten ze de Application Catalog vernieuwen en de goedkeuringsstatus controleren.  

      -   Gebruikers ontvangen geen revisies en updates voor toepassingen die worden gepubliceerd naar de Application Catalog. Gebruikers zien wijzigingen aan de toepassingsinformatie in de Application Catalog.  

      -   Als u een toepassingsimplementatie verwijdert nadat de client de toepassing uit de Application Catalog installeert, blijven clients om te controleren dat de toepassing wordt geïnstalleerd voor maximaal twee dagen.  

    Wanneer deze instelling is bovendien **Nee**, ontvangen gebruikers geen vereiste toepassingen die u voor gebruikers implementeert. Gebruikers ook ontvangen geen andere beheertaken in gebruikersbeleid.  

    Deze instelling geldt voor gebruikers wanneer hun computer op het intranet en Internet is. Dit moet **Ja** als u ook wilt inschakelen gebruikersbeleid op het Internet.  

-   **Gebruikersbeleidsaanvragen van internetclients inschakelen**   </br>
   Deze instelling en **Ja** voor gebruikers ontvangen het gebruikersbeleid op Internet gebaseerde computers. De volgende vereisten moeten worden toegepast:  

      -   De client en de site zijn geconfigureerd voor clientbeheer op Internet

      -   De **gebruikersbeleid op clients inschakelen** instelling **Ja**  

      -   De Internet-gebaseerd beheerpunt bevindt verifieert de gebruiker met behulp van Windows-verificatie (Kerberos of NTLM)  

       Als u deze optie instelt **Nee**, of een van de vorige vereisten niet wordt voldaan, wordt een computer op het Internet ontvangt alleen het computerbeleid. In dit scenario kunnen gebruikers nog steeds toepassingen zien, aanvragen en installeren uit een Application Catalog op internet. Als deze instelling is **Nee**, maar **gebruikersbeleid op clients inschakelen** is **Ja**, gebruikers doen geen gebruikersbeleid ontvangen totdat de computer is verbonden met het intranet.  

       Zie voor meer informatie over het beheren van clients op het Internet [overwegingen voor clientcommunicatie via Internet of een niet-vertrouwd forest](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

      > [!NOTE]  
      >  Goedkeuringsaanvragen voor toepassingen van gebruikers vereisen geen gebruikersbeleid of gebruikersverificatie.  


## <a name="cloud-services"></a>Cloudservices

-   **Toegang tot clouddistributiepunt toestaan** </br>
    Deze instelling en **Ja** voor clients om inhoud te verkrijgen van een cloud-distributiepunt. Deze instelling vereist niet dat het apparaat niet op basis van het Internet.

-    **Nieuwe Windows 10-apparaten die lid van domein automatisch wordt geregistreerd bij Azure Active Directory** </br> Wanneer u Azure Active Directory voor de ondersteuning van hybride join configureert, configureert Configuration Manager Windows 10-apparaten voor deze functionaliteit. Zie voor meer informatie [hoe het configureren van hybride Azure Active Directory die lid zijn van apparaten](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup).

-   **Clients gebruiken een cloudgateway management inschakelen** </br>
    Standaard gebruiken alle clients voor Internet roaming beschikbaar [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway). Een voorbeeld van wanneer deze instelling en **Nee** is aan het gebruik van het bereik van de service, zoals tijdens een proefproject of om kosten te besparen.



##  <a name="compliance-settings"></a>Instellingen voor naleving  

-   **Compatibiliteitsevaluatie op clients toestaan** </br>
    Deze instelling en **Ja** voor het configureren van de andere instellingen in deze groep.
 
-   **Compatibiliteitsevaluatie plannen**   </br>
     Klik op **planning** het standaardschema voor de configuratie van basislijn om implementaties te maken. Deze waarde kan worden geconfigureerd voor elke basislijn in de **Configuratiebasislijn implementeren** in het dialoogvenster.  

-   **Gebruikersgegevens en -profielen inschakelen**   </br>
     Kies **Ja** als u wilt implementeren [gebruikersgegevens en -profielen](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) configuratie-items.



## <a name="computer-agent"></a>Computeragent  
-   Meldingen voor gebruikers voor vereiste implementaties </br>
    Zie voor meer informatie over de volgende drie instellingen [meldingen voor gebruikers voor vereiste implementaties](/sccm/apps/deploy-use/deploy-applications#user-notifications-for-required-deployments):
    -   **Implementatiedeadline langer dan 24 uur, gebruiker herinneren elke (uur)**
    -   **Implementatie deadline van minder dan 24 uur, gebruiker herinneren elke (uur)**  </br>
    -   **Implementatie deadline van minder dan 1 uur, gebruiker herinneren elke (minuten)**  </br>

-   **Standaard Application Catalog-websitepunt**   </br>
     Configuration Manager gebruikt deze instelling om gebruikers verbinding met de Toepassingscatalogus vanuit Software Center. Klik op **Website instellen** om op te geven van een server die als host fungeert voor de Application Catalog-websitepunt. Voert u de NetBIOS-naam of FQDN, automatische detectie of geef een URL voor aangepaste implementaties. In de meeste gevallen is automatische detectie de beste keuze, omdat het de volgende voordelen biedt:  

    -   Als de site een Application Catalog-websitepunt heeft, vervolgens clients krijgen automatisch een Application Catalog-websitepunt van hun site.  

    -   De client geeft de voorkeur aan HTTPS-functionaliteit Application Catalog-websitepunten op het intranet via HTTP-only-servers. Deze mogelijkheid biedt beveiliging tegen een rogue server.

    -   Het beheerpunt geeft clients op Internet een internetgebaseerde Application Catalog-websitepunt. Het beheerpunt geeft clients op basis van het intranet een intranet gebaseerd Application Catalog-websitepunt.  

     Automatische detectie garandeert niet dat clients de dichtstbijzijnde Application Catalog-websitepunt zijn opgegeven. U kunt kiezen om **Automatisch detecteren** niet te gebruiken om volgende redenen:  

     -   U wilt de dichtstbijzijnde server voor clients handmatig configureren of ervoor zorgen dat ze niet met server verbinden via een trage netwerkverbinding.  

     -   U wilt controleren welke clients met welke server verbinding maken. Deze configuratie kan zijn voor testdoeleinden, prestaties of zakelijke redenen.  

     -   U wilt niet wachten maximaal 25 uur of wijst op een netwerkwijziging voor clients voor gebruik van een andere Application Catalog-website.  

     Als u de Application Catalog-websitepunt opgeven in plaats van automatische detectie te gebruiken, geeft u de NetBIOS-naam in plaats van de intranet-FQDN. Deze configuratie vermindert de kans dat de webbrowser wordt gebruikers om referenties gevraagd wanneer ze toegang krijgen een intranet gebaseerd Application Catalog tot. De volgende voorwaarden moeten van toepassing zijn om de NetBIOS-naam te gebruiken:  

     -   De NetBIOS-naam is opgegeven in de eigenschappen van het Application Catalog-websitepunt.  

     -   U gebruikt WINS of alle clients bevinden zich in hetzelfde domein als de Application Catalog-websitepunt.  

     -   U configureert het Application Catalog-websitepunt voor HTTP-clientverbindingen, of de server configureren voor HTTPS en het webservercertificaat heeft de NetBIOS-naam.  

     Meestal worden gebruikers gevraagd om referenties wanneer de URL een FQDN-naam heeft, maar niet als de URL een NetBIOS-naam. Ga er van uit dat gebruikers altijd om referenties wordt gevraagd wanneer ze verbinden via het internet, omdat deze verbinding het internet-FQDN moet gebruiken. Wanneer met behulp van een client met Internet en de webbrowser, wordt gebruikers om referenties gevraagd, zorg ervoor dat het Application Catalog-websitepunt verbinding met een domeincontroller voor het gebruikersaccount maken kan. Deze configuratie kan de gebruiker te verifiëren via Kerberos.  

    > [!NOTE]  
    >  Hoe automatische detectie werkt:  
    >   
    >  De client maakt een verzoek om de servicelocatie aan een beheerpunt. Als er een Application Catalog-websitepunt in dezelfde site als de client aanwezig is, wordt de server aan de client gegeven als de te gebruiken Application Catalog-server. Als meer dan één Application Catalog-websitepunt in de site beschikbaar is, heeft een HTTPS-functionaliteit server voorrang op een server die niet is ingeschakeld voor HTTPS. Na dit filteren ontvangen alle clients krijgen een van de servers om te gebruiken als de Application Catalog. Configuration Manager voert geen taakverdeling tussen meerdere servers. Wanneer de site van de client geen een Application Catalog-websitepunt heeft, retourneert het beheerpunt een Application Catalog-websitepunt niet-deterministisch uit de hiërarchie.  
    >   
    >  Voor intranet-clients, als u de Application Catalog-websitepunt met een NetBIOS-naam voor de Application Catalog-URL configureert, geeft het beheerpunt clients deze NetBIOS-naam in plaats van de intranet-FQDN. Voor clients op Internet geeft het beheerpunt alleen de Internet-FQDN naar de client.  
    >   
    >  De client maakt dit verzoek om de servicelocatie elke 25 uur of wanneer deze een netwerkwijziging detecteert. Bijvoorbeeld als de client wordt verplaatst van het intranet naar het Internet en de client een Internet-gebaseerd beheerpunt bevindt zoekt, geeft het internetgebaseerde beheerpunt op basis van het Internet Application Catalog-website point-servers aan clients.  

-   **Voeg de standaard Application Catalog-website toe aan de zone met vertrouwde sites in Internet Explorer**   </br>
     Als deze optie is **Ja**, de client de huidige standaard Application Catalog-website-URL automatisch toegevoegd aan de zone Internet Explorer vertrouwde sites.  

     Deze instelling zorgt ervoor dat de instelling in Internet Explorer voor de Beveiligde modus niet is ingeschakeld. Als beveiligde modus is ingeschakeld, kan de Configuration Manager-client mogelijk geen toepassingen uit de Application Catalog installeren. Standaard ondersteunt de zone met vertrouwde sites ook gebruikersaanmelding voor de Application Catalog. Hiervoor is Windows-verificatie is vereist.  

     Als u deze optie ingesteld laat **Nee**, Configuration Manager-clients mogelijk geen toepassingen installeren uit de Application Catalog. Er is een alternatieve methode voor het configureren van deze instellingen voor Internet Explorer in een andere zone voor Application Catalog-URL die clients gebruiken.  

    > [!NOTE]  
    >  Wanneer de Configuration Manager een standaard Application Catalog aan de zone met vertrouwde sites toevoegt, verwijdert Configuration Manager alle eerder toegevoegde Application Catalog-URL.  
    >   
    >  Als de URL al in een van de beveiligingszones opgegeven is, toevoegen niet de URL door Configuration Manager. In dit scenario moet u de URL van de andere zone verwijderen of de vereiste instellingen voor Internet Explorer handmatig configureren.  

-   **Toestaan dat Silverlight-toepassingen worden uitgevoerd in verhoogde vertrouwensmodus**   </br>
     Deze instelling moet **Ja** gebruikers de Application Catalog gebruiken.  

     Als u deze instelling wijzigt, wordt deze van kracht wanneer gebruikers de browser de volgende keer laden of het geopende browservenster vernieuwen.  

     Zie voor meer informatie over deze instelling [certificaten voor Microsoft Silverlight 5 en verhoogde vertrouwensmodus vereist voor de application catalog](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5).  

-   **Weergegeven organisatienaam in Software Center**   </br>
     Typ de naam die wordt weergegeven in Software Center. Deze huismerkgegevens helpen gebruikers om deze toepassing als een vertrouwde bron te identificeren.  

-   **Het nieuwe Software Center gebruiken**   </br>
     Als u deze clientinstelling instelt op configureert **Ja**, en vervolgens alle clientcomputers het nieuwe Software Center gebruiken. Software Center bevat gebruikers beschikbare apps die eerder alleen toegankelijk in de Application Catalog zijn. De Application Catalog vereist Silverlight, die niet is een vereiste voor het nieuwe Software Center.   

     De Application Catalog-websitepunt en Application Catalog-webservice webservicepunt functies nog steeds vereist zijn voor gebruikers beschikbare apps zijn worden weergegeven in Software Center.  

     Zie voor meer informatie [plannen en configureren van Toepassingsbeheer](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   **Communicatie met Health Attestation-Service inschakelen**  </br>
    Deze instelling en **Ja** voor Windows 10-apparaten gebruiken [Health attestation](/sccm/core/servers/manage/health-attestation). Wanneer u deze instelling inschakelt, is ook de volgende instelling beschikbaar voor configuratie.

    -   **On-premises Health Attestation-Service gebruiken** </br>
        Deze instelling en **Ja** voor apparaten met een on-premises-service gebruiken. Deze instelling en **Nee** voor apparaten te gebruiken van Microsoft-cloudservice.  

-   **Installatiemachtigingen**   </br>
    > [!WARNING]  
    >  Deze instelling is van toepassing op de Application Catalog en Software Center. Deze instelling heeft geen effect wanneer gebruikers de bedrijfsportal gebruiken.  

     Configureer hoe gebruikers de installatie van de software, software-updates en takenreeksen kunnen initialiseren:  

    -   **Alle gebruikers**: Gebruikers met elke machtiging behalve Gast  

    -   **Alleen beheerders**: Gebruikers moeten lid zijn van de lokale groep Administrators  

    -   **Alleen beheerders en Hoofdgebruikers**: Gebruikers moeten lid zijn van de lokale groep Administrators of een primaire gebruiker van de computer  

    -   **Er zijn geen gebruikers**: Er zijn geen gebruikers aangemeld op een clientcomputer kan de installatie van software, software-updates en takenreeksen kunnen initiëren. Vereiste implementaties voor de computer wordt altijd installeren op de deadline. Gebruikers kunnen niet de installatie van software uit de Application Catalog of Software Center niet initialiseren.  

-   **Invoer BitLocker-pincode opschorten bij opnieuw opstarten**  </br>
     Als computers BitLocker-pincode is vereist, wordt deze optie overgeslagen de vereiste voor een PINCODE invoeren wanneer de computer opnieuw wordt opgestart na een software-installatie.  

    -   **Altijd**: Configuration Manager wordt tijdelijk onderbroken voor BitLocker, als er software die moet worden opgestart en een opnieuw opstarten van de computer is geïnstalleerd. Deze instelling geldt alleen voor de computer opnieuw opgestart door Configuration Manager. Deze instelling schort niet de vereiste de BitLocker-PINCODE opgeven wanneer de gebruiker de computer opnieuw opstart. De BitLocker-PINCODE vermelding vereiste hervat na het opstarten van Windows.

    -   **Nooit**: Configuration Manager schort niet BitLocker op de volgende keer opstarten van de computer nadat deze is geïnstalleerd software die moet worden opgestart. In dit scenario kan de software-installatie niet worden voltooid tot de gebruiker de pincode heeft ingevoerd om het standaardopstartproces te voltooien en Windows te laden.

-   **Aanvullende software beheert de implementatie van toepassingen en software-updates**  </br>
     Schakel deze optie alleen in als een van de volgende voorwaarden van toepassing is:  

    -   U gebruikt een leveranciersoplossing waarvoor deze instelling moet worden ingeschakeld.  

    -   U gebruikt de Configuration Manager software development kit (SDK) om clientagentmeldingen en de installatie van toepassingen en software-updates.  

    > [!WARNING]  
    >  Als u deze optie wanneer geen van deze voorwaarden van toepassing, de client software-updates en vereiste toepassingen niet wordt geïnstalleerd. Deze instelling voorkomt niet dat gebruikers toepassingen van de Application Catalog of de installatie van pakketten, programma's en takenreeksen te installeren.  

-   **PowerShell-uitvoeringsbeleid**  </br>
     Configureren hoe Configuration Manager-clients Windows PowerShell-scripts kunnen uitvoeren. Deze scripts worden vaak gebruikt voor detectie in configuratie-items voor compatibiliteitsinstellingen. Ze kunnen ook worden verzonden in een implementatie als een Standaardscript.  

    -   **Bypass**: Configuration Manager-client omzeilt de Windows PowerShell-configuratie op de clientcomputer zodat niet-ondertekende scripts kunnen uitvoeren.  

    -   **Beperkte**: Configuration Manager-client gebruikt de huidige Windows PowerShell-configuratie op de clientcomputer. Deze configuratie bepaalt of niet-ondertekende scripts kunnen worden uitgevoerd.  

    -   **Alle ondertekende**: Configuration Manager-client scripts alleen uitgevoerd als een vertrouwde uitgever ze heeft ondertekend. Deze beperking is van toepassing onafhankelijk van de huidige Windows PowerShell-configuratie op de clientcomputer.  

     Deze optie vereist ten minste Windows PowerShell versie 2.0. De standaardwaarde is **alle ondertekende**.  

    > [!TIP]  
    >  Als niet-ondertekende scripts niet kunnen worden uitgevoerd vanwege deze clientinstelling, rapporteert Configuration Manager deze fout in de volgende manieren:  
    >   
    > -   De **bewaking** werkruimte in de console weergegeven implementatie status fout-ID **0x87D00327** en beschrijving **Script is niet ondertekend**  
    > -   Rapporten weergeven fouttype **Detectiefout**, en vervolgens een foutcode **0x87D00327** en beschrijving **Script is niet ondertekend**, of foutcode  **0x87D00320** en beschrijving **de scripthost is nog niet geïnstalleerd**. Een voorbeeld van een rapport is **Details van fouten van configuratie-items in een configuratiebasislijn voor een asset**.  
    > -   De **DcmWmiProvider.log** bestand verschijnt het bericht **Script is niet ondertekend (fout: 87D 00327; Bron: CCM)**.  

-   **Meldingen weergeven voor nieuwe implementaties**  </br>
     Kies **Ja** om een melding voor implementaties die beschikbaar is minder dan een week weer te geven.  Dit bericht wordt weergegeven wanneer de clientagent wordt gestart.

-   **Willekeurig toepassen van deadline uitschakelen**  </br>
     Na de deadline van de implementatie met deze instelling bepaalt of de client een activeringsvertraging van maximaal twee uur gebruikt voor het installeren van vereiste software-updates. De vertraging is standaard uitgeschakeld.  

     Voor virtuele desktopinfrastructuur (VDI) scenario's kan deze vertraging helpt te verdelen van de CPU-verwerking en gegevensoverdracht voor een hostmachine met meerdere virtuele machines. Zelfs als u geen VDI gebruikt, kunnen CPU-gebruik op de siteserver negatief verhogen door veel clients tegelijkertijd dezelfde updates installeren. Dit probleem kan ook aan distributiepunten vertragen en de beschikbare netwerkbandbreedte significant verminderen.  

     Als clients vereiste software-updates op de deadline van de implementatie onmiddellijk moeten worden geïnstalleerd, configureert u deze instelling om **Ja**. 

-   **Respijtperiode voor afdwingen na de deadline van de implementatie (uren)** </br>
     Als u gebruikers geven meer tijd wilt voor het installeren van vereiste toepassingen of software-update-implementaties na de deadline, configureert u deze instelling om **Ja**. Deze respijtperiode is voor een computer voor langere tijd uitgeschakeld en de gebruiker moet installeren veel toepassing of update-implementaties. Als een gebruiker wordt geactiveerd vanuit een vakantie en heeft gedurende lange tijd tijdens het wachten installeert de client achterstallige toepassingsimplementaties. 

     Stel een respijtperiode van 1 tot 120 uur. Gebruik deze instelling samen met de implementatie-eigenschap **afdwingen van deze implementatie op basis van gebruikersvoorkeuren uitstellen**. Zie voor meer informatie [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications).



##  <a name="computer-restart"></a>Opnieuw opstarten van computer  
 De volgende instellingen moet korter in duur dan het kortste onderhoudsvenster toegepast op de computer.  

 Zie [Onderhoudsvensters gebruiken in System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md) voor meer informatie over onderhoudsvensters.  

-   **Een tijdelijke melding weergeven aan de gebruiker die het duurt voordat de gebruiker aangeeft wordt afgemeld of de computer opnieuw opstart (minuten)**
-   **Een dialoogvenster weergeven dat de gebruiker niet kan en sluiten waarin het aftellingsinterval voordat de gebruiker wordt afgemeld of de computer opnieuw opstart (minuten)**



##  <a name="endpoint-protection"></a>Endpoint Protection  
>  [!Tip]   
> Naast de volgende informatie vindt u meer informatie over het gebruik van Endpoint Protection-clientinstellingen in [voorbeeldscenario: System Center Endpoint Protection gebruiken om computers te beveiligen tegen schadelijke software in System Center Configuration Manager](/sccm/protect/deploy-use/scenarios-endpoint-protection).

-   **Endpoint Protection-client op clientcomputers beheren**  </br>
     Kies **Ja** als u wilt beheren van bestaande Endpoint Protection en Windows Defender-clients op computers in uw hiërarchie.  

     Selecteer deze optie als u de Endpoint Protection-client reeds hebt geïnstalleerd en u wilt beheren met Configuration Manager.  Deze afzonderlijke installatie bevat een script proces met behulp van een Configuration Manager-toepassing of pakket en programma.

-   **Endpoint Protection-client op clientcomputers installeren**   </br>
     Kies **Ja** installeren en activeren van de Endpoint Protection-client op clientcomputers de client niet is gestart.  

    > [!NOTE]  
    >  Als de Endpoint Protection-client al is geïnstalleerd, kiezen **Nee** niet door de Endpoint Protection-client verwijderd. Om te verwijderen van de Endpoint Protection-client, stelt de **beheren van Endpoint Protection-client op clientcomputers** clientinstelling instelt op **Nee**. Vervolgens implementeert u een pakket en programma om de Endpoint Protection-client te verwijderen.  

-   **Eerder geïnstalleerde antimalware-software automatisch verwijderen voordat Endpoint Protection is geïnstalleerd** </br>
    Deze instelling en **Ja** voor de Endpoint Protection-client om te verwijderen van de andere anti-malware-toepassingen. Meerdere antimalware-clients op hetzelfde apparaat kunnen een conflict veroorzaken en de systeemprestaties.

-   **Endpoint Protection-client installeren en opnieuw opstarten toestaan buiten onderhoudsvensters. Onderhoudsvensters moeten ten minste 30 minuten lang zijn voor clientinstallatie** </br>
    Deze instelling en **Ja** standaardinstallatie gedrag met onderhoudsvensters overschrijven. Deze instelling voldoet aan de zakelijke vereisten voor de prioriteit van systeemonderhoud om beveiligingsredenen. 

-   **Voor Windows Embedded-apparaten met schrijffilters installatie van Endpoint Protection-client (opnieuw opstarten noodzakelijk) toepassen**  </br>
     Kies **Ja** uit te schakelen van het schrijffilter op Windows Embedded-apparaat en het apparaat opnieuw opstarten. Deze actie voert de installatie op het apparaat.  

     Als u deze instelling configureert **Nee**, vervolgens wordt de client geïnstalleerd op een tijdelijke overlay die wordt gewist wanneer het apparaat opnieuw wordt opgestart. In dit scenario wordt de Endpoint Protection-client is niet volledig worden geïnstalleerd totdat een andere installatie wijzigingen worden doorgevoerd in het apparaat. Deze configuratie is de standaardinstelling.  

-   **Opnieuw opstarten vereist computer onderdrukken nadat de Endpoint Protection-client is geïnstalleerd**  </br>
     Kies **Ja** onderdrukken van een computer opnieuw opstarten indien nodig nadat de Endpoint Protection-client is geïnstalleerd.  

    > [!IMPORTANT]  
    >  Als de Endpoint Protection-client een opnieuw wordt opgestart vereist en deze instelling is **Nee**, klikt u vervolgens de computer opnieuw wordt opgestart ongeacht eventuele onderhoudsvensters geconfigureerd.  

-   **Toegestane periode die gebruikers verplicht opnieuw opstarten om de installatie van Endpoint Protection te voltooien kan uitstellen (uur)**  </br>
     Als een herstart nodig is nadat de Endpoint Protection-client is geïnstalleerd, is deze instelling bepaalt u het aantal uren dat gebruikers de vereiste herstart kunnen uitstellen. Deze instelling moet de **onderdrukken eventuele vereiste computer opnieuw wordt opgestart nadat de Endpoint Protection-client is geïnstalleerd** instelling is **Nee**.  

-   **Alternatieve bronnen uitschakelen (zoals Microsoft Windows Update, Microsoft Windows Server Update Services of UNC-shares) voor de initiële definitie-update op clientcomputers**  </br>
     Kies **Ja** als u wilt dat Configuration Manager alleen de initiële definitie-update op clientcomputers installeren. Deze instelling kan nuttig zijn om onnodige netwerkverbindingen te vermijden en netwerkbandbreedte te verminderen tijdens de initiële installatie van de definitie-update.  



##  <a name="enrollment"></a>Inschrijving

-   **Pollinginterval voor verouderde clients van mobiele apparaten** </br>
    Klik op **Interval instellen** om op te geven van de tijdsduur in minuten of uren die verouderde mobiele apparaten poll-frequentie voor het beleid. Deze apparaten omvatten platformen, zoals Windows CE-, Mac OS X- en Unix- of Linux.

-   **Polling-interval voor moderne apparaten (minuten)** </br>
    Voer het aantal minuten dat moderne apparaten poll-frequentie voor het beleid. Deze instelling is voor Windows 10-apparaten beheerd via on-premises-beheer voor mobiele apparaten.

-   **Kunnen gebruikers zich inschrijven van mobiele apparaten en Mac-computers** </br>
    Configureren zodat de registratie van de oudere apparaten op basis van een gebruiker deze instelling om **Ja**, en configureer vervolgens de volgende instelling:

    -   **Inschrijvingsprofiel** </br>
        Klik op **profiel instellen** te maken of een inschrijvingsprofiel selecteren. Zie voor meer informatie [configureren van clientinstellingen voor inschrijving](/sccm/core/clients/deploy/deploy-clients-to-macs#configure-client-settings-for-enrollment).

-   **Toestaan dat gebruikers moderne apparaten te registreren** </br>
    Om in te schakelen op basis van gebruiker inschrijven van moderne apparaten, configureert u deze instelling om te **Ja**, en configureer vervolgens de volgende instelling:

    -   **Inschrijvingsprofiel voor moderne apparaten** </br>
        Klik op **profiel instellen** te maken of een inschrijvingsprofiel selecteren. Zie voor meer informatie [maken van een Registratieprofiel waarmee gebruikers moderne apparaten te registreren](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm#bkmk_createProf).



##  <a name="hardware-inventory"></a>Hardware-inventaris  

-   **Hardware-inventaris op clients inschakelen** </br>
    Deze instelling is ingesteld op **Ja** standaard. Zie voor meer informatie [inleiding op hardware-inventarisatie](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory).

-   **Hardware-inventarisplanning** </br>
    Klik op **planning** om aan te passen, de frequentie waarmee clients de hardware-inventarisatie uitvoeren cyclus. Deze cyclus wordt standaard elke zeven dagen plaatsvindt.

-   **Maximale willekeurige vertraging (minuten)** </br>
    Geef het maximum aantal minuten voor de Configuration Manager-client naar de hardware-inventaris een willekeurige cyclus van de gedefinieerde planning. Deze willekeurige over alle clients helpt load balance inventaris verwerking op de siteserver. U kunt een waarde van 0-480 minuten opgeven. Deze waarde is standaard ingesteld op 240 minuten (vier uur).

-   **Maximale grootte aangepast MIF-bestand (KB)**  </br>
     Geef de maximale grootte, in kilobytes (KB) voor elk aangepast Management Information Format (MIF)-bestand dat de client worden verzameld tijdens een hardware-inventarisatiefase is toegestaan. De Configuration Manager-agent voor hardware-inventaris verwerkt geen aangepast MIF-bestanden die groter zijn dan deze limiet. U kunt een grootte van 1 KB 5.120 kB opgeven. Deze waarde is standaard ingesteld op 250 KB. Deze instelling heeft geen invloed op de grootte van het normale hardware-inventarisgegevensbestand.  

    > [!NOTE]  
    >  Deze instelling is alleen beschikbaar in de standaardclientinstellingen.  

-   **Hardware-inventarisklassen**  </br>
     Klik op **klassen instellen** uitbreiden van de hardware-informatie die u van clients verzamelt zonder het sms_def.mof-bestand handmatig te bewerken. Zie voor meer informatie [het configureren van hardware-inventaris](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

-   **MIF-bestanden verzamelen**  </br>
     Gebruik deze instelling kunt u opgeven of voor het verzamelen van MIF-bestanden van Configuration Manager-clients tijdens hardware-inventaris.  

     Voor een MIF-bestand moeten worden verzameld door hardware-inventaris, moet deze de juiste locatie op de clientcomputer. Standaard worden de bestanden bevinden zich in de volgende paden:  

    -   **IDMIF-bestanden** moet in de map Windows\System32\CCM\Inventory\Idmif 

    -   **NOIDMIF-bestanden** moet in de map Windows\System32\CCM\Inventory\Noidmif

    > [!NOTE]  
    >  Deze instelling is alleen beschikbaar in de standaardclientinstellingen.

   

##  <a name="metered-internet-connections"></a>Internetverbindingen naar gebruik  
 Beheren hoe Windows 8 en hoger computers internetverbindingen naar gebruik gebruiken om te communiceren met Configuration Manager. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.  

> [!NOTE]  
>  De geconfigureerde clientinstelling wordt niet toegepast in de volgende scenario's:  
>   
> -   De computer zich op een roaming gegevensverbinding: Configuration Manager-client voert geen taken waarbij gegevens worden overgedragen naar Configuration Manager-sites.  
> -   De verbindingseigenschappen van de Windows-netwerk zijn geconfigureerd als zonder datalimiet: Configuration Manager-client gedraagt zich alsof de verbinding zonder datalimiet is en bijgevolg gegevens naar de site verstuurt.  

-   **Clientcommunicatie bij internetverbindingen naar gebruik**  </br>
     Kies een van de volgende opties voor deze instelling:  

    -   **Toestaan dat**: Alle clientcommunicaties zijn toegestaan via de internetverbinding met datalimiet tenzij het clientapparaat een roaming gegevensverbinding gebruikt.  

    -   **Limiet**: De volgende clientcommunicaties zijn toegestaan over de internetverbinding met datalimiet:  

        -   Clientbeleid ophalen  

        -   Clientstatusberichten om te verzenden naar de site  

        -   Software-installatieaanvragen via de Application Catalog  

        -   Vereiste implementaties (zodra de installatiedeadline wordt bereikt)  

        > [!IMPORTANT]  
        >  De client is altijd toegestaan voor software-installaties van Software Center of de Toepassingscatalogus, ongeacht de instellingen van gecontroleerde internetverbinding.  

         Als de gegevensoverdrachtlimiet voor de internetverbinding met datalimiet is bereikt, probeert de client niet langer te communiceren met Configuration Manager-sites.  

    -   **Blok**: Configuration Manager-client probeert niet te communiceren met Configuration Manager-sites wanneer deze zich op een internetverbinding. Dit is de standaardoptie.  



##  <a name="power-management"></a>Energiebeheer  

-   **Energiebeheer van apparaten toestaan** </br>
    Deze instelling en **Ja** energiebeheer op clients inschakelen. Zie voor meer informatie [inleiding op Energiebeheer](/sccm/core/clients/manage/power/introduction-to-power-management).

-   **Toestaan dat gebruikers hun apparaat uit energiebeheer uitsluiten**  </br>
     Kies **Ja** zodat gebruikers van Software Center hun computer uitsluiten van een geconfigureerde energiebeheerinstellingen.  

-   **Wake-up proxy inschakelen** </br> 
     Specificeer **Ja** om te voorzien in de instelling van de Wake On LAN van de site wanneer hij geconfigureerd wordt voor unicast pakketten.  

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
         Configuration Manager-client configureert automatisch de wake-up proxypoortnummer op apparaten met Windows Defender-Firewall. Klik op **configureren** om op te geven van de gewenste firewallprofielen.

        Als clients een andere firewall uitvoeren, moet u handmatig configureren zodat deze de **Wake-up proxypoortnummer (UDP)**.  
        
    -   **IPv6-voorvoegsels indien vereist voor DirectAccess of andere Tussenkomende netwerkapparaten. Gebruik een komma om meerdere vermeldingen scheiden** </br>
        Voer de benodigde IPv6-voorvoegsels voor wake-up-proxy om te functioneren in uw netwerk.



##  <a name="remote-tools"></a>Externe hulpprogramma 's  

-   **Beheer op afsten op clients inschakelen** en **Firewall-uitzonderingsprofielen**  </br>
     Klik op **configureren** Configuration Manager-beheer op afstand inschakelen. Configureer desgewenst firewall-instellingen voor extern beheer om te werken op clientcomputers.  

     Beheer op afstand is standaard uitgeschakeld.  

    > [!IMPORTANT]  
    >  Indien firewall-instellingen niet geconfigureerd zijn, zal het kunnen gebeuren dat externe controle niet juist werkt.  

-   **Gebruikers kunnen instellingen voor beleid of meldingen in Software Center wijzigen**  </br>
     Kies of gebruikers externe controle-opties van Software Center kunnen wijzigen.  

-   **Extern beheer van een onbeheerde computer toestaan**  </br>
     Kies of een beheerder extern beheer gebruiken kan voor toegang tot een clientcomputer die afgemeld is of vergrendeld. Alleen een computer is aangemeld en ontgrendeld kan extern worden beheerd wanneer deze instelling is uitgeschakeld.  

-   **Gebruiker vragen naar machtiging voor beheer op afstand**  </br>
     Kies of de clientcomputer ziet u een bericht dat om toestemming voordat een sessie voor extern beheer van de gebruiker wordt gevraagd.  

-   **Gebruiker vragen naar machtiging voor het overbrengen van inhoud vanaf het gedeelde Klembord** </br>
    Uw gebruikers de mogelijkheid om te accepteren of weigeren van bestandsoverdrachten voordat de overdracht van inhoud van het gedeelde Klembord in een sessie voor extern beheer toestaan. Gebruikers hoeven alleen te machtigen eenmaal per sessie en de viewer heeft niet de mogelijkheid zelf om toestemming te geven om door te gaan met de bestandsoverdracht.

-   **Machtigingen voor beheer op afstand toekennen aan lokale groep beheerders**  </br>
     Kies of de externe controle-sessies op clientcomputers kan worden gemaakt door de lokale beheerders op de server waarop de beheer op afstand verbinding initieert.  

-   **Toegestaan toegangsniveau**  </br>
     Geef het niveau van beheer op afstand toegang om toe te staan. Kies in de volgende instellingen:  
    - **Geen toegang**
    - **Alleen weergeven**
    - **Volledig beheer**  

-   **Toegelaten viewers van beheer op afstand en hulp op afstand**  </br>
     Klik op **Stel Viewers** om op te geven van de namen van de Windows-gebruikers die externe controlesessies naar clientcomputers kunnen instellen.  

-   **Sessiemeldingspictogram weergeven op de taakbalk**  </br>
     Deze instelling en **Ja** om een pictogram op de taakbalk van de client om aan te geven van een actieve beheer op afstandsessie weer te geven.  

-   **Sessieverbindingsbalk weergeven**  </br>
     Deze instelling en **Ja** om een hoge visibiliteit sessieverbindingsbalk op clients om aan te geven van een actieve beheer op afstandsessie weer te geven.  

-   **Een geluid afspelen op client**  </br>
     Configureer deze instelling om geluid te gebruiken om aan te geven wanneer een externe controlesessie actief op een clientcomputer is. Selecteer een van de volgende opties:
    - **Geen geluid**
    - **Begin- en verzenden van sessie** (standaard)
    - **Herhaaldelijk tijdens een sessie**  

-   **Instellingen voor ongevraagde hulp op afstand beheren**  </br>
     Deze instelling en **Ja** Configuration Manager beheren ongevraagde externe hulpsessies te laten.  

     In een sessie voor ongevraagde hulp op afstand, de gebruiker op de clientcomputer is niet om hulp vragen aan de sessie te starten.  

-   **Instellingen voor gevraagde hulp op afstand beheren**  </br>
     Deze instelling en **Ja** Configuration Manager beheren gevraagde externe hulpsessies te laten.  

     In een sessie voor gevraagde hulp op afstand verzonden de gebruiker op de clientcomputer een aanvraag naar de beheerder voor hulp op afstand.  

-   **Toegangsniveau voor hulp op afstand**  </br>
     Kies het niveau van toegang toe te wijzen om externe hulpsessies die geïnitieerd zijn in de Configuration Manager-console.  Selecteer een van de volgende opties:
    - **Geen** (standaard)
    - **Externe weergeven**
    - **Volledig beheer**

    > [!NOTE]  
    >  De gebruiker op de clientcomputer moet altijd toegang verlenen opdat een externe hulpsessie zou kunnen plaatsvinden.  

-   **Instellingen voor extern bureaublad beheren**  </br>
     Deze instelling en **Ja** zodat Configuration Manager beheren van extern bureaublad-sessies voor computers.  

-   **Toegelaten viewers toestaan om verbinding te maken via externe bureaublad-verbinding**  </br>
     Deze instelling en **Ja** gebruikers die zijn opgegeven in de lijst met toegelaten viewers aan de lokale gebruikersgroep van extern bureaublad op clients toe te voegen.  

-   **Eis verificatie op netwerkniveau op computers die het besturingssysteem Windows Vista en latere versies uitvoeren.**  </br>
     Deze instelling en **Ja** gebruik van verificatie op netwerkniveau (NLA) tot stand brengen van extern bureaublad-verbindingen op clientcomputers. NLA vereist in eerste instantie minder externe computerbronnen omdat het gebruikersverificatie is voltooid voordat het een extern bureaublad-verbinding tot stand brengt. Met behulp van NLA is een veiligere configuratie. NLA zorgt de computer beschermen tegen kwaadwillende gebruikers of software en vermindert het risico op denial of service-aanvallen.  



## <a name="software-center"></a>Software Center

-   **Deze nieuwe instellingen om op te geven bedrijfsgegevens selecteren** </br>
    Deze instelling en **Ja**, en geef vervolgens de volgende instellingen op merk Software Center voor uw organisatie:

    - **Bedrijfsnaam** </br>
        Voer de naam van de organisatie die wordt weergegeven in Software Center.
    - **Kleurenschema voor Software Center** </br>
        Klik op **Selecteer kleur** voor het definiëren van de primaire kleur die wordt gebruikt door Software Center.
    - **Selecteer een logo voor Software Center** </br>
        Klik op **Bladeren** om een installatiekopie in Software Center weergeven te selecteren. Het logo moet een JPEG of PNG van 400 x 100 pixels en een maximale grootte van 750 KB.

-   Software Center tabblad zichtbaarheid </br>
    De extra instellingen configureren in deze groep **Ja** zichtbaar maken voor de volgende tabbladen in Software Center:
    - **Toepassingen**
    - **Updates**
    - **Besturingssystemen**
    - **Installatiestatus**
    - **Apparaatcompatibiliteit**
    - **Opties**

    Bijvoorbeeld, als uw organisatie gebruikt geen beleidsregels voor naleving en u wilt verbergen van het tabblad apparaatcompatibiliteit in Software Center, configureert de **apparaatcompatibiliteit inschakelen tabblad** instelt op **Nee**.



## <a name="software-deployment"></a>Software-implementatie  

-   **Nieuwe evaluatie voor implementaties plannen**  </br>
     Configureer een planning voor wanneer de Configuration Manager de regels voor vereisten voor alle implementaties opnieuw beoordeelt. De standaardwaarde is elke zeven dagen.  

    > [!IMPORTANT]  
    >  U wordt aangeraden dat u deze waarde niet op een lagere waarde dan de standaardwaarde wijzigt. Een agressievere planning nieuwe evaluatie van negatieve invloed op de prestaties van uw netwerk en clientcomputers.  

     Deze actie van een client starten door het kiezen van de **Beoordelingscyclus toepassingsimplementatie** van de **acties** tabblad van de **Configuration Manager** het Configuratiescherm.  



##  <a name="software-inventory"></a>Software-inventaris  

-   **Software-inventaris op clients inschakelen** </br>
    Deze instelling is ingesteld op **Ja** standaard. Zie voor meer informatie [Inleiding tot software-inventaris](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).

-   **Software-inventaris en verzamelen van bestanden plannen** </br>
    Klik op **planning** om aan te passen, de frequentie dat clients de software-inventaris en de bestandsnaam verzameling cycli uitvoeren. Deze cyclus wordt standaard elke zeven dagen plaatsvindt.

-   **Detail inventarisrapportage**  </br>
     Geef een van de volgende niveaus van te inventariseren bestandsgegevens:
    - **Alleen bestand**
    - **Alleen product**
    - **Volledige details** (standaard)

-   **Deze bestandstypen inventariseren**  </br>
     Als u opgeven welke typen bestand dat u wilt inventariseren wilt, klikt u op **Stel typen**, en configureer vervolgens de volgende opties:  

    > [!NOTE]  
    >  Als meerdere aangepaste clientinstellingen worden toegepast op een computer, wordt de inventaris die wordt geretourneerd voor elke instelling samengevoegd.  

    -   Klik op de **nieuw** pictogram toevoegen van een nieuw bestandstype aan inventaris. Geef vervolgens de volgende gegevens in de **eigenschappen geïnventariseerd bestand** in het dialoogvenster:  

        -   **Naam**: Geef een naam voor het bestand dat u wilt inventariseren. Gebruik een sterretje (**&#42;**) jokertekens vertegenwoordigt een willekeurige tekenreeks van tekst en een vraagteken (**?**) een willekeurig teken vertegenwoordigt. Bijvoorbeeld, als u inventariseren van alle bestanden met de extensie .doc wilt, de bestandsnaam opgeven  **\*.doc**.  

        -   **Locatie**: Klik op **ingesteld** openen de **padeigenschappen** in het dialoogvenster. Configureren van software-inventaris om te zoeken alle harde schijven voor het opgegeven bestand, zoek een opgegeven pad (bijvoorbeeld **C:\Folder**), of zoeken naar een opgegeven variabele (bijvoorbeeld *% windir %*). U kunt ook zoeken in alle Deelmappen onder het opgegeven pad.  

        -   **Sluit versleutelde en gecomprimeerde bestanden**: Als u deze optie kiest, worden gecomprimeerd, of versleutelde bestanden niet geïnventariseerd.  

        -   **Sluit bestanden uit in de map Windows**: Als u deze optie kiest, worden alle bestanden in de Windows-map en haar Deelmappen niet geïnventariseerd.  

    -   Klik op **OK** om het dialoogvenster **Geïnventariseerde bestandseigenschappen** te sluiten.  

    -   De bestanden die u wilt inventariseren en klik vervolgens op toevoegen **OK** sluiten de **Configureer Clientinstelling** in het dialoogvenster.  

-   **Bestanden verzamelen**  </br>
     Als u wenst bestanden te verzamelen van clientcomputers, klikt u op **Stel bestanden** en configureer vervolgens de volgende instellingen:  

    > [!NOTE]  
    >  Als meerdere aangepaste clientinstellingen worden toegepast op een computer, wordt de inventaris die wordt geretourneerd voor elke instelling samengevoegd.  

    -   In de **Configureer Clientinstelling** in het dialoogvenster, klikt u op de **nieuw** pictogram voor het toevoegen van een bestand moet worden verzameld.  

    -   Voer, in het dialoogvenster **Eigenschappen verzameld bestand** , de volgende informatie in:  

        -   **Naam**: Geef een naam voor het bestand dat u wilt verzamelen. Gebruik een sterretje (**&#42;**) jokertekens vertegenwoordigt een willekeurige tekenreeks van tekst en een vraagteken (**?**) een willekeurig teken vertegenwoordigt.  

        -   **Locatie**: Klik op **ingesteld** openen de **padeigenschappen** in het dialoogvenster. Configureren van software-inventaris om te zoeken naar alle harde schijven voor het bestand dat u wilt verzamelen, zoek een opgegeven pad (bijvoorbeeld **C:\Folder**), of zoeken naar een opgegeven variabele (bijvoorbeeld *% windir %*). U kunt ook zoeken in alle Deelmappen onder het opgegeven pad.  

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

    -   Klik op **OK** om het dialoogvenster **Verzamelde bestandseigenschappen** te sluiten.  

    -   De bestanden die u wilt verzamelen, en klik vervolgens op toevoegen **OK** sluiten de **Configureer Clientinstelling** in het dialoogvenster.  

-   **Namen instellen**  </br>
     De software-inventarisagent haalt de fabrikant en productnamen koptekstgegevens van bestand. Deze namen niet altijd gestandaardiseerd zijn in de header bestandsgegevens. Wanneer u software-inventaris in Resourceverkenner bekijkt, kunnen verschillende versies van dezelfde fabrikant of productnaam verschijnen. Deze standaardiseren weergavenamen, klikt u op **Stel namen** en configureer vervolgens de volgende instellingen:  

    -   **Naamtype**: Software-inventaris verzamelt informatie over fabrikanten en producten. Kies of u wilt configureren weergavenamen voor een **fabrikant** of een **Product**.  

    -   **Weergavenaam**: Geef de weergavenaam op die u wilt gebruiken in plaats van de namen in de **geïnventariseerde namen** lijst. Klik op de **nieuw** pictogram om op te geven van een nieuwe weergavenaam.  

    -   **Geïnventariseerde namen**: Klik op de **nieuw** pictogram een geïnventariseerde naam toe te voegen. Deze naam in software-inventaris wordt vervangen door de naam van de gekozen in de **weergavenaam** lijst. U kunt meerdere namen vervangen toevoegen.  



##  <a name="software-metering"></a>Softwaremeter

-   **Softwaremeter op clients inschakelen** </br>
    Deze instelling is ingesteld op **Ja** standaard. Zie voor meer informatie [softwarelicentiecontrole](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering#configure-software-metering).

-   **Verzamelen van gegevens plannen** </br>
    Klik op **planning** om aan te passen, de frequentie dat clients de cyclus voor softwarelicentiecontrole uitvoeren. Deze cyclus wordt standaard elke zeven dagen plaatsvindt.



##  <a name="software-updates"></a>Software-updates  

-   **Software-updates op clients inschakelen**  </br>
     Deze instelling gebruiken om softwareupdates inschakelen op Configuration Manager-clients. Wanneer u deze instelling uitschakelt, verwijdert Configuration Manager de bestaande implementatiebeleiden van de client. Wanneer u deze instelling opnieuw inschakelt, zal de client het huidige implementatiebeleid downloaden.  

    > [!IMPORTANT]  
    >  Wanneer u deze instelling uitschakelt, werkt beleidsregels voor nalevingsbeleid die afhankelijk van de software-updates zijn niet meer.  

-   **Planning software-updatescan**  </br>
     Klik op **planning** om op te geven hoe vaak de client een scan voor beoordeling van naleving initieert. Deze scan bepaalt de status voor software-updates op de client (bijvoorbeeld vereist of geïnstalleerd). Zie voor meer informatie over nalevingsbeoordeling [beoordeling van compatibiliteit van Software-updates](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

     Deze scan gebruikt standaard een eenvoudige planning om te starten elke zeven dagen. U kunt een aangepaste planning opgeven voor een exacte startdatum en -tijd, Universal Coordinated Time (UTC) of de lokale tijd gebruiken en het terugkerende interval configureren voor een specifieke dag van de week maken.  

    > [!NOTE]  
    >  Als u een interval van minder dan een dag opgeeft, wordt Configuration Manager automatisch standaard ingesteld op één dag.  

    > [!WARNING]  
    >  De daadwerkelijke starttijd op clientcomputers is de starttijd plus een willekeurige hoeveelheid tijd maximaal twee uur. Deze willekeurige wordt voorkomen dat clientcomputers de scan starten en tegelijkertijd te verbinden met het actieve software-updatepunt.  

-   **Nieuwe evaluatie van implementatie plannen**  </br>
     Klik op **planning** configureren hoe vaak de software-updates opnieuw evalueert software clientagentupdates voor de installatiestatus van Configuration Manager-clientcomputers. Wanneer eerder geïnstalleerde software-updates op clients, maar worden nog steeds vereist, de client niet meer worden gevonden, wordt de software-updates opnieuw geïnstalleerd.

     Pas deze planning op basis van bedrijfsbeleid voor compatibiliteit van software-updates en of gebruikers software-updates kunnen verwijderen. Elke cyclus voor het nieuwe evaluatie resulteert in het netwerk en clientcomputers computer processoractiviteit. Deze instelling maakt standaard gebruik van een eenvoudige planning voor het initiëren van de implementatie van nieuwe evaluatiescan elke zeven dagen.  

    > [!NOTE]  
    >  Als u een interval van minder dan een dag opgeeft, wordt Configuration Manager automatisch standaard ingesteld op één dag.  

-   **Wanneer de deadline van een software-update-implementatie is bereikt, installeert u alle andere software-update-implementaties met een deadline binnen een opgegeven periode**  </br>
     Deze instelling en **Ja** voor het installeren van alle software-updates van de vereiste implementaties met deadlines die binnen een opgegeven periode. Als een vereiste software-update-implementatie een deadline is bereikt, initieert de client-installatie voor de software-updates in de implementatie. Deze instelling bepaalt of voor het installeren van software-updates van andere vereiste implementaties met een deadline binnen de opgegeven tijdsduur hebben.  

     Deze instelling gebruiken om de installatie voor vereiste software-updates versnellen. Deze instelling mogelijk ook verhoogt de beveiliging van de client, verkleint u mogelijk meldingen voor eindgebruikers en mogelijk deze client opnieuw wordt opgestart. Deze instelling is standaard ingesteld op **Nee** dus niet is ingeschakeld.  

-   **De periode gedurende welke alle in afwachting zijnde implementaties met deadlines in deze periode eveneens worden geïnstalleerd**  </br>
     Gebruik deze instelling om op te geven van de periode voor de vorige instelling. U kunt een waarde tussen 1 en 23 uur en tussen 1 en 365 dagen invoeren. Deze instelling is standaard geconfigureerd voor de zeven dagen.  

-   **Installatie van bestanden voor snelle installatie op clients inschakelen** </br>
    Deze instelling en **Ja** wilt toestaan dat clients bestanden voor snelle installatie gebruiken. Zie voor meer informatie [installatiebestanden beheren Express voor Windows 10-updates](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).

    -   **Poort die wordt gebruikt voor het downloaden van inhoud voor de bestanden voor snelle installatie** </br>
        Deze instelling configureert u de lokale poort voor de HTTP-listener snelle inhoud te downloaden. Dit is standaard ingesteld op 8005 blijven ingedeeld. U hoeft niet te openen van deze poort in de clientfirewall.

-   **Beheer van de Office 365-Clientagent inschakelen** </br>
    Gebruik deze instelling het beheer van de Office 365-Clientagent inschakelen. Als u de waarde instelt op **Ja**, Hiermee kunt de configuratie van Office 365 installatie-instellingen, bestanden downloaden van inhoud levering bedrijfsnetwerken (CDN) en het implementeren van de bestanden als een toepassing in Configuration Manager. Zie voor meer informatie [Office 365 ProPlus beheren](/sccm/sum/deploy-use/manage-office-365-proplus-updates).



## <a name="state-messaging"></a>Messaging-status

-   **Rapportagecyclus (minuten) statusbericht**  </br>
     Geeft aan hoe vaak clients statusberichten rapporteren. Deze instelling is standaard de 15 minuten.



##  <a name="user-and-device-affinity"></a>Affiniteit van gebruiker en apparaat  

-   **Gebruiksdrempel affiniteit van gebruiker met apparaat (minuten)**  </br>
     Geef het aantal minuten voordat Configuration Manager toewijzing maakt voor een gebruiker apparaataffiniteit.  Deze waarde is standaard 2880 minuten (twee dagen).

-   **Gebruiksdrempel affiniteit van gebruiker met apparaat (dagen)**  </br>
     Geef het aantal dagen gedurende welke de client de drempel voor affiniteit tussen gebruikers-gebaseerde apparaten meet.  Deze waarde is standaard 30 dagen.

    > [!NOTE]  
    >  Geef bijvoorbeeld **gebruiker gebruiksdrempel apparaataffiniteit (minuten)** als **60** minuten en **gebruiksdrempel van affiniteit van gebruiker-apparaat (dagen)** als **5**  dagen. Vervolgens moet de gebruiker het apparaat gedurende 60 minuten gebruiken gedurende een periode van vijf dagen voor het maken van automatische affiniteit met het apparaat.  

-   **Affiniteit van gebruikers met apparaat automatisch configureren via gebruiksgegevens**  </br>
     Kies **Ja** voor het maken van automatische gebruikersaffiniteit met apparaat op basis van de gebruiksgegevens die door Configuration Manager worden verzameld.  

-   **Gebruikers toestaan hun primaire apparaten te definiëren** </br>
    Wanneer deze instelling is **Ja** en vervolgens gebruikers hun eigen primaire apparaten in Software Center kunnen herkennen.



## <a name="windows-analytics"></a>Analytics voor Windows

Zie voor meer informatie over deze instellingen [Clients configureren voor het rapportgegevens Windows Analytics](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics).
    