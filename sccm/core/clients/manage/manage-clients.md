---
title: Clients beheren | Microsoft-documenten
description: Informatie over het beheren van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3a86924b2e5db3ac16eeda78b95ae6747ffd656f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>Clients beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Als een System Center Configuration Manager-client is geïnstalleerd en aan een Configuration Manager-site toegewezen, ziet u het apparaat in de **activa en naleving** werkruimte in de **apparaten** knooppunt en in een of meer verzamelingen in de **Apparaatverzamelingen** knooppunt. Wanneer u het apparaat of een verzameling selecteert, kunt u bewerkingen kunt uitvoeren. Er zijn evenwel ook andere manieren voor het beheren van de client, die andere werkruimtes in de console, of taken die gebruikmaken van de Configuration Manager-console niet kan erbij betrekken.  

> [!NOTE]  
>  Configuration Manager-client kan worden geïnstalleerd maar niet weergegeven in de Configuration Manager-console. Dit kan gebeuren als de client is nog niet aan een site toegewezen of de console moet worden geladen of een lidmaatschap moet geüpdatet.  
>   
>  Een apparaat kunt daarnaast ook weergeven in de console wanneer de Configuration Manager-client niet is geïnstalleerd. Dit kan gebeuren als het apparaat wordt gedetecteerd, maar de Configuration Manager-client niet is geïnstalleerd en toegewezen. Mobiele apparaten die worden beheerd via de Exchange Server-connector en de apparaten die zijn geregistreerd door Microsoft Intune, moeten de Configuration Manager-client niet installeren.  
>   
>  Gebruik de **Client** kolom in de Configuration Manager-console om te bepalen of de Configuration Manager-client is geïnstalleerd, zodat u hem vanaf de Configuration Manager-console beheren kunt.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> Clients beheren in het knooppunt Apparaten  

Merk op dat, afhankelijk van het apparaattype, sommige van deze opties mogelijk niet beschikbaar.  

1.  Kies in de Configuration Manager-console **activa en naleving** >  **apparaten**.  

3.  Selecteer een of meer apparaten en selecteer een van deze clientbeheertaken van het lint, of door met de rechtermuisknop op het apparaat:  

    -   **Informatie van affiniteit gebruikerapparaat beheren**  

         Configureer de koppelingen tussen gebruikers en apparaten, zodat u efficiënt software naar gebruikers kunt implementeren.  

         Zie [Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)  

    -   **Het apparaat toevoegen aan een nieuwe of bestaande verzameling**  

         Het apparaat toevoegen aan een verzameling met een directe regel.  
         
    -   **Installeer en installeer de client opnieuw door gebruik te maken van de wizard clientpush.**  

         Installeer en installeer de Configuration Manager-client om hem te herstellen of opnieuw te configureren op computers waarop Windows wordt uitgevoerd opnieuw. Bevat configuratie-opties van site en client.msi-eigenschappen die u voor push-clientinstallatie instelt.  

        > [!TIP]  
        >  Er zijn veel verschillende manieren Configuration Manager-client installeren (en opnieuw moet installeren). Hoewel de wizard Clientpush een geschikte biedt clientinstallatiemethode te gebruiken omdat u hem vanaf de console uitvoeren kunt deze methode veel afhankelijkheden heeft en is niet geschikt voor alle omgevingen. Zie [Vereisten voor de implementatie van Configuration Manager-clients op Windows-pc's](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) voor meer informatie over de afhankelijkheden. Zie [Clientinstallatiemethoden in System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md) voor meer informatie over de andere clientinstallatiemethoden.  

         Zie [Het installeren van Configuration Manager-Clients met behulp van clientpush](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

    -   **Site opnieuw toewijzen**  

         Wijs één of meerdere klanten, waaronder beheerde mobiele apparaten, toe aan een andere primaire site in de hiërarchie. Clients kunnen afzonderlijk opnieuw worden toegewezen of kunnen meervoudig worden geselecteerd en in bulk aan een nieuwe site worden toegewezen.  

    -   **Extern beheer van de client**  

         U kunt Resource Explorer uitvoeren om de informatie over hardware-en software-inventaris van een Windows-client te raadplegen, en deze te beheren op afstand met afstandsbediening, hulp op afstand, of extern bureaublad.  

         Zie [Resource Explorer gebruiken om hardware-inventaris te bekijken in System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) en [Resource Explorer gebruiken om software-inventaris te bekijken in System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

         Zie [Een Windows-clientcomputer op afstand beheren met System Center Configuration Manager](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md).  

    -   **Een client goedkeuren**  

         Wanneer de client met sitesystemen met behulp van HTTP en een zelfondertekend certificaat communiceert, moet u deze clients om ze te identificeren als vertrouwde computers goedkeuren. Standaard keurt de siteconfiguratie automatisch clients goed van dezelfde Active Directory-forests en vertrouwde forests, zodat u niet elke client handmatig moet goedkeuren. U moet evenwel handmatig werkgroepcomputers goedkeuren die u vertrouwt en andere computers die u vertrouwt, maar die niet goedgekeurd zijn.  

        > [!WARNING]  
        >  Hoewel sommige beheerfuncties voor niet-goedgekeurde clients werken kunnen, is dit een niet-ondersteund scenario voor Configuration Manager.  

         Er geen clients goedkeuren die altijd communiceren met sitesystemen met behulp van HTTPS, of clients die een PKI-certificaat gebruiken wanneer ze communiceren met sitesystemen via HTTP. Deze clients stellen vertrouwen met behulp van de PKI-certificaten.  

    -   **Blokkeren of deblokkeringen van een client**  

         Blokkeer een client die u niet langer vertrouwt, om hem te beletten clientbeleid te krijgen en om te voorkomen dat Configuration Manager site-systemen mee te communiceren.  

        > [!WARNING]  
        >  Een client blokkeert alleen communicatie vanaf de client naar Configuration Manager-sitesystemen en belet geen communicatie met andere apparaten. Wanneer, bijkomend, de client communiceert met sitesystemen door gebruik te maken van HTTP in plaats van HTTPS, zijn er bepaalde beveiligingsbeperkingen.  

         U kunt een client die geblokkeerd werd, deblokkeren. Indien u evenwel een AMT-gebaseerde computer deblokkeert die was ingericht voor AMT wanneer hij geblokkeerd was, moet u bijkomende stappen ondernemen vóór u die computer opnieuw buiten-band kunt beheren.  

         Zie [Bepalen of clients worden geblokkeerd in System Center Configuration Manager](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

    -   **Wissen van een vereiste PXE-implementatie**  

         PXE-implementaties voor de computer implementeren.  

         Zie [PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   **De clienteigenschappen beheren**  

         De detectiegegevens en implementaties voor de client is gericht weergeven. U kunt ook variabelen die takenreeksen gebruiken voor het implementeren van een besturingssysteem op het apparaat configureren.  

    -   **Verwijderen van de client**  

        > [!WARNING]  
        >  Een client niet verwijderen als u wilt de Configuration Manager-client te verwijderen of te verwijderen uit een verzameling.  

         De **verwijderen** actie wist handmatig het client-record van de Configuration Manager-database en typisch, moet u niet gebruiken, tenzij deze actie probleemoplossende scenario's. Als u het clientrecord wist en de client nog steeds geïnstalleerd en de communicatie met Configuration Manager, Heartbeat-detectie het clientrecord opnieuw creëren en zal het opnieuw verschijnen in de Configuration Manager-console, hoewel de clientgeschiedenis en vroegere koppelingen verloren zullen zijn.  

        > [!NOTE]  
        >  Wanneer u een client voor mobiele apparaten die door Configuration Manager is geregistreerd verwijdert, deze actie ook het PKI-certificaat dat was uitgegeven aan het mobiele apparaat intrekken, en dit certificaat wordt dan geweigerd door het beheerpunt, zelfs als IIS de CRL niet controleert. Certificaten op verouderde mobiele apparaten worden niet ingetrokken wanneer u deze clients wist.  

         Om de installatie van de client ongedaan te maken, zie [De installatie van de Configuration Manager-client ongedaan maken](#BKMK_UninstalClient).  

         Zie [Clients toewijzen aan een site in System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md) voor meer informatie over het toewijzen van de client aan een nieuwe primaire site.  

         Configureer, om de client te verwijderen uit een verzameling, opnieuw de eigenschappen van de verzameling. Zie [Verzamelingen beheren in System Center Configuration Manager](../../../core/clients/manage/collections/manage-collections.md).  

    -   **Een mobiel apparaat wissen**  

         U kunt mobiele apparaten wissen die de wisopdracht ondersteunen.  

         Deze actie verwijdert permanent alle gegevens op het mobiele apparaat, met inbegrip van persoonlijke instellingen en persoonlijke gegevens. Typisch zet deze actie het mobiele apparaat terug naar zijn fabrieksinstellingen. Wissen van een mobiel apparaat wanneer het mobiele apparaat niet langer vertrouwd, bijvoorbeeld als is verloren of gestolen.  

        > [!TIP]  
        >  Raadpleeg de documentatie van de fabrikant voor meer informatie over hoe het mobiel apparaat een externe wisopdracht verwerkt.  

         Er is vaak een vertraging vóór het mobiele apparaat de wisopdracht ontvangt:  

        -   Als het mobiele apparaat is ingeschreven door Configuration Manager of door Microsoft Intune, ontvangt de client de opdracht wanneer het het clientbeleid wordt gedownload.  

        -   Als het mobiele apparaat wordt beheerd door de Exchange Server-connector, ontvangt de opdracht wanneer het synchroniseert met Exchange.  

         U kunt de **Wisstatus** kolom om te controleren wanneer het apparaat de wisopdracht ontvangt. Totdat het apparaat een wisbevestiging naar de Configuration Manager verzendt kunt u steeds de wisopdracht annuleren.  

    -   **Een mobiel apparaat buiten gebruik stellen**  

         De **buiten gebruik stellen** optie wordt alleen ondersteund door mobiele apparaten die geregistreerd zijn door Intune, of door op\-premises beheer van mobiele apparaten.  

         Zie [Help uw gegevens beschermen met wissen op afstand, vergrendelen op afstand of opnieuw instellen van wachtwoordcode met behulp van System Center Configuration Manager](../../../mdm/deploy-use/wipe-lock-reset-devices.md) voor meer informatie.  

    -   **Het eigendom van een apparaat wijzigen**  

         U kunt de eigendom van apparaten te wijzigen **bedrijf** of **persoonlijke** als een apparaat niet toegevoegd aan een domein is en geen Configuration Manager-client geïnstalleerd heeft.  

         U kunt deze waarde in toepassingsvereisten gebruiken voor het beheren van implementaties te beheren, en hoeveel inventaris wordt verzameld van de apparaten van gebruikers.  

        U wilt toevoegen de **eigenaar van het apparaat** kolom naar de weergave door met de rechtermuisknop op een kolomkop en deze te selecteren.

         Zie [Hybride Mobile Device Management (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md) voor meer informatie.  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> Clients beheren in het knooppunt Apparaatverzamelingen  
  Veel van de taken die u kunt uitvoeren op één apparaat of op meerdere apparaten in de **apparaten** knooppunt kan worden uitgevoerd op verzamelingen. Dit automatisch van toepassing is de bewerking op alle verkiesbare apparaten in de verzameling. Houd er rekening mee dat dit een groot aantal netwerkpakketten genereert en verhoogt de CPU-gebruik op de siteserver.  

  Houd rekening, vóór u clientbeheertaken uitvoert op het niveau van verzameling, met het aantal apparaten in de verzameling, of ze verbonden zijn door lage-bandbreedte-netwerkverbindingen en met hoe lang de taak zal duren vóór hij wordt voltooid door alle apparaten. Eenmaal gestart, kunt u de taak van de console niet stoppen.  

#### <a name="to-manage-clients-from-the-device-collections-node"></a>Clients beheren in het knooppunt Apparaatverzamelingen  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Apparaatverzamelingen**.  

3.  Selecteer een verzameling en selecteer een van de volgende clientbeheertaken van het lint, of door met de rechtermuisknop op de verzameling. Deze clientbeheertaken kunnen *alleen* worden uitgevoerd op het niveau verzameling.  

    -   **Scan computers op schadelijke software en download anti-malware-definitiebestanden.**  

         Zie [Endpoint Protection in System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

    -   **Software, configuratiebasislijnen en takenreeksen implementeren.**  

         Zie:  

        -   [Software-updates in System Center Configuration Manager implementeren](../../../sum/deploy-use/deploy-software-updates.md)  

        -   [Plannen en configureren van instellingen voor naleving in System Center Configuration Manager](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

    -   **Energiebeheerinstellingen configureren.**  

         Zie [Energiebeheerschema's maken en toepassen in System Center Configuration Manager](../../../core/clients/manage/power/create-and-apply-power-plans.md). Energiebeheerplannen kunnen enkel worden gebruikt met computers die Windows uitvoeren.  

    -   **Verwittig zo snel mogelijk computers om beleid te downloaden.**  

         Clientmelding gebruiken om de geselecteerde Windows-clients kunnen downloaden van computerbeleid zo snel mogelijk buiten het pollinginterval voor clientbeleid in kennis.  

         Clientmeldingstaken worden weergegeven in het knooppunt **Clientbewerkingen** in de werkruimte **Bewaken** .  

##  <a name="BKMK_ClientCache"></a> De clientcache configureren voor Configuration Manager-clients  
De clientcache opslaan van tijdelijke bestanden voor wanneer clients installatie van toepassingen en programma's. De clientcache wordt eveneens gebruikt door software-updates, maar software-updates worden niet beperkt door de geconfigureerde cachegrootte en worden altijd gedownload naar de cache. U kunt de clientcache-instellingen, zoals grootte en locatie, wanneer u de Configuration Manager-client handmatig installeert, wanneer u push-clientinstallatie of nadat de client is geïnstalleerd.

Beginnend met Configuration Manager versie 1606, kunt u clientinstellingen in de Configuration Manager-console met grootte van de cachemap.   

 De standaardlocatie voor de Configuration Manager-clientcache is %*windir*%\ccmcache en de standaardschijfruimte is 5120 MB.  

> [!IMPORTANT]  
>  Versleutel de map die wordt gebruikt voor de clientcache niet. Door Configuration Manager kan geen inhoud naar een versleutelde map worden gedownload.  

### <a name="about-client-cache"></a>Over de clientcache  

De Configuration Manager-client downloadt de inhoud voor vereiste software kort na de implementatie wordt ontvangen, maar pas de geplande tijd uitgevoerd. Op het geplande tijdstip, de Configuration Manager-client gecontroleerd of de inhoud beschikbaar in de cache is. Als de inhoud bevindt zich in de cache en de juiste versie is, gebruikt de client de inhoud in cache. Wanneer de vereiste versie van de inhoud is gewijzigd of als de inhoud is verwijderd om ruimte voor een ander pakket te maken, wordt de inhoud opnieuw naar de cache gedownload.  

Als de client probeert te downloaden van inhoud voor een programma dat of toepassing die groter is dan de grootte van de cache, mislukt de implementatie vanwege ontoereikende cachegrootte en Configuration Manager genereert statusbericht-ID 10050. Als de cache later wordt vergroot, wordt het resultaat is:  

-   Voor een vereist programma: De client probeert niet automatisch opnieuw de inhoud te downloaden. U moet het pakket en programma opnieuw implementeren op de client.  
-   Voor een vereiste toepassing: De client probeert automatisch opnieuw de inhoud te downloaden wanneer deze zijn clientbeleid downloadt.  

Als de client probeert te downloaden van een pakket dat kleiner is dan de grootte van de cache, maar de cache vol is, houden geprobeerd de vereiste implementaties tot de cacheruimte beschikbaar is, totdat de download een time-out optreedt, of de limiet voor opnieuw proberen is bereikt voor het aantal. Als de cache later wordt vergroot, probeert de Configuration Manager-client het pakket te downloaden tijdens het volgende interval opnieuw. De client probeert de inhoud elke vier uur te downloaden tot het achttien keer is geprobeerd.  

Inhoud in de cache wordt niet automatisch verwijderd, maar blijft minimaal één dag in de cache nadat de client die inhoud heeft gebruikt. Als u de pakketeigenschappen configureert met de optie om inhoud permanent te behouden in de clientcache, wordt de pakketinhoud niet automatisch verwijderd uit de cache. Als de cacheruimte voor de client wordt gebruikt door pakketten die de afgelopen 24 uur zijn gedownload en er nieuwe pakketten moeten worden gedownload, kunt u de cachegrootte voor de client uitbreiden of de verwijderingsoptie kiezen om blijvende cache-inhoud te verwijderen.  

 Gebruik de volgende procedures om de clientcache te configureren tijdens de handmatige clientinstallatie of nadat de client is geïnstalleerd.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>De clientcache configureren wanneer u clients installeert op basis van een handmatige clientinstallatie  

Voer de opdracht CCMSetup.exe uit vanaf de installatiebronlocatie en geef de volgende eigenschappen op, indien vereist (gescheiden door spaties):  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Gebruik voor versie 1606 beschikbaar in de instellingen voor de cache **clientinstellingen** in de Configuration Manager-console in plaats van SMSCACHESIZE. Zie [Clientcache-instellingen](../../../core/clients/deploy/about-client-settings.md#client-cache-settings) voor meer informatie.

Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over het gebruik van deze opdrachtregeleigenschappen voor CCMSetup.exe.  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>De clientcache configureren wanneer u clients installeert op basis van een push-clientinstallatie  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de juiste site en klik op de **Start** tabblad, in de **instellingen** groep, kiest u **clientinstallatie-instellingen** > **installatie-eigenschappen tabblad**.  

5.  Geef de volgende eigenschappen, gescheiden door spaties:  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Gebruik voor versie 1606 beschikbaar in de instellingen voor de cache **clientinstellingen** in de Configuration Manager-console in plaats van SMSCACHESIZE. Zie [Clientcache-instellingen](../../../core/clients/deploy/about-client-settings.md#client-cache-settings) voor meer informatie.

       Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over het gebruik van deze opdrachtregeleigenschappen voor CCMSetup.exe.  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>De clientcachemap configureren op de clientcomputer  

1.  Navigeer op de clientcomputer naar **Configuration Manager** in het Configuratiescherm en dubbelklik op om de eigenschappen te openen.  

2.  Op de **Cache** tabblad ruimte en de locatie-eigenschappen ingesteld. De standaardlocatie is *%windir%*\ccmcache.  

5.  Kies de om bestanden te verwijderen in de cachemap, **bestanden verwijderen**.  

    > [!NOTE]
    > 
    > De cachemap is een gewone Windows-map, zodat u de verwijdering van de inhoud van de map met een script, een hulpprogramma of met de PowerShell-cmdlet kunt automatiseren `Remove-Item`. 


### <a name="to-configure-client-cache-size-in-client-settings"></a>De client-cachegrootte in clientinstellingen configureren

Vanaf versie 1606, kunt u de grootte van de cachemap van de client zonder de client opnieuw installeert aanpassen. Om dit te doen, configureert u de client-cachegrootte in de Configuration Manager-console via Clientinstellingen.  

1. Ga in de Configuration Manager-console naar **Beheer** > **Clientinstellingen**.

2. Dubbelklik op **Standaardclientinstellingen**.
  U kunt ook aangepaste clientinstellingen maken zodat u de cachegrootte selectiever kunt toepassen. Zie [Clientinstellingen in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-settings.md) voor meer informatie over standaardclientinstellingen en aangepaste clientinstellingen.

 3. Kies **clientcache-instellingen** en kies **Ja** voor **configureren van client-cachegrootte**, een gebruiken de **MB** of **percentage van de Schijfinstellingen**. De cache wordt aangepast aan de kleinste grootte.

     De Configuration Manager-client configureert de cachegrootte op grond van deze instellingen de volgende keer dat er een clientbeleid wordt gedownload.

##  <a name="BKMK_UninstalClient"></a> De Configuration Manager-client verwijderen  
 U kunt de Windows Configuration Manager-clientsoftware van een computer verwijderen met behulp van **CCMSetup.exe** met de **/Uninstall** eigenschap. Voer CCMSetup.exe op een afzonderlijke computer uit via de opdrachtprompt of implementeer een pakket en programma om de client te verwijderen voor een verzameling computers.  

> [!WARNING]  
>  U kunt de Configuration Manager-client niet verwijderen van een mobiel apparaat. Als u de Configuration Manager-client van een mobiel apparaat verwijderen moet, moet u het apparaat, verwijdert u alle gegevens op het mobiele apparaat wissen.  

#### <a name="to-uninstall-the-configuration-manager-client-from-the-command-prompt"></a>De Configuration Manager-client verwijderen via de opdrachtprompt  

1.  Open een Windows-opdrachtprompt en wijzig de map in de locatie waarin CCMSetup.exe zich bevindt.  

2.  Typ **Ccmsetup.exe /uninstall**en druk op **Enter**.  

> [!NOTE]  
>  Het verwijderingsproces bevat geen resultaten op het scherm. Om te controleren of client is verwijderd, bekijkt u het logbestand **CCMSetup.log** in de map *%windir%\ ccmsetup* op de clientcomputer.  

##  <a name="BKMK_ConflictingRecords"></a> Conflicterende records voor Configuration Manager-clients beheren  
 Configuration Manager gebruikt de hardware-ID om clients te identificeren die gedupliceerd kunnen zijn en waarschuwt u voor de conflicterende records. Bijvoorbeeld, als u een computer installeert, de hardware-ID zou dezelfde, maar de GUID die wordt gebruikt door Configuration Manager kan worden gewijzigd.  

 Wanneer Configuration Manager een conflict oplossen kan met behulp van Windows-verificatie van de computeraccount of een PKI-certificaat van een vertrouwde bron, wordt het conflict automatisch voor u opgelost. Wanneer Configuration Manager het conflict niet kan oplossen, gebruikt deze een hiërarchie-instelling dat of de records automatisch worden samengevoegd wanneer dubbele hardware-id's (de standaardinstelling) wordt gedetecteerd, of kunt u bepalen wanneer u samen te voegen, te blokkeren of nieuwe client-records maken. Als u dubbele records handmatig te beheren besluit, moet u de conflicterende records in de Configuration Manager-console handmatig oplossen.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>De hiërarchie-instellingen wijzigen voor het beheren van conflicterende records  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites** > **hiërarchie-instellingen**
2.  Op de **goedkeuring van Client en conflicterende Records** tabblad, kiest u **conflicterende records automatisch oplossen**, of **conflicterende records handmatig oplossen**.  

#### <a name="to-manually-resolve-conflicting-records"></a>Conflicterende records handmatig oplossen  

1.  Kies in de Configuration Manager-console **bewaking** > **systeemstatus** > **conflicterende Records**.  

3.  Selecteer een of meer conflicterende records en kies vervolgens **conflicterende records**.  

4.  Selecteer vervolgens een van de volgende opties:  

    -   **Samenvoegen** te combineren, de nieuwe record met de bestaande clientrecord.  

    -   **Nieuw** : maak een nieuwe record voor de conflicterende clientrecord.  

    -   **Blokkeren** : maak een nieuwe record voor de conflicterende clientrecord, maar markeer deze als geblokkeerd.  

## <a name="manage-duplicate-hardware-identifiers"></a>Dubbele hardware-id's beheren
Beginnend in Configuration Manager versie 1610, kunt u een lijst van hardware-id's in Configuration Manager wordt genegeerd voor de PXE-opstart- en client registratie opgeven. Er zijn twee algemene problemen die dit bij het adres helpt.

1. Veel nieuwe apparaten, zoals de 3 Surface Pro is een ingebouwde Ethernet-poort niet inbegrepen. Een USB-Ethernet-adapter wordt doorgaans gebruikt bekabelde verbinding ten behoeve van de implementatie van besturingssystemen te maken. Dit zijn echter vaak gedeelde adapters vanwege kosten en algemene bruikbaarheid. Omdat het MAC-adres van deze adapter wordt gebruikt voor identificatie van het apparaat, wordt opnieuw gebruiken van de adapter problematische zonder extra beheerder acties tussen elke implementatie. U kunt het MAC-adres van deze adapter van versie 1610 uitsluiten zodat deze kan worden gebruikt in dit scenario.
2. Terwijl de SMBIOS-ID een unieke hardware-id zijn moet, worden sommige hardwareapparaten specialisatie gebouwd met dubbele id. Terwijl dit niet zo gebruikelijk als de bovenstaande USB Ethernet-adapter scenario, kan de lijst met hardware-id's worden gebruikt en dit probleem op te lossen.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Toevoegen van hardware-id's voor Configuration Manager moeten worden genegeerd  
1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.
2. Op de **Start** tabblad, in de **Sites** groep, kiest u **hiërarchie-instellingen**.
3. Op de **goedkeuring van Client en conflicterende Records** Kies **toevoegen** in de **dubbele hardware-id's** sectie toevoegen van nieuwe hardware-id's.

##  <a name="BKMK_PolicyRetrieval"></a> Ophalen van beleid initiëren voor een Configuration Manager-client  
 Windows Configuration Manager-client downloadt het clientbeleid volgens een schema dat u configureert als een clientinstelling. Er kunnen zich echter situaties voordoen waarin u ophalen van de ad-hoc-beleid van de client bijvoorbeeld initiëren wilt voor probleemoplossing of testen.  

U kunt starten voor het ophalen met behulp van beleid:


- [Clientmeldingen](#initiate-client-policy-retrieval-using-client-notification) 
- [De **acties** tabblad op de client](#manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client)
- [Een script](#manually-initiate-client-policy-retrieval-by-script)

> [!NOTE]  
>   
>  Zie [Computerbeleid voor Linux- en UNIX-servers](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_PolicyforLnU) voor informatie over het ophalen van beleid voor clients met Linux en UNIX.  

#### <a name="initiate-client-policy-retrieval-using-client-notification"></a>Clientbeleid ophalen met behulp van clientmeldingen  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Apparaatverzamelingen**.  

3.  Selecteer de apparaatverzameling met de computers waarvan u beleid wilt downloaden. Op de **Start** tabblad, in de **verzamelingen** groep, kiest u **Clientmeldingen** > **computerbeleid downloaden**.  

    > [!NOTE]  
    >  U kunt Clientmelding ook gebruiken om beleid op te halen voor een of meer geselecteerde apparaten die worden weergegeven in een tijdelijk verbindingsknooppunt onder het knooppunt **Apparaten** .  

#### <a name="manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client"></a>Clientbeleid ophalen op het tabblad acties van de Configuration Manager-client handmatig starten  

1.  Selecteer **Configuration Manager** in het Configuratiescherm van de computer.  

2.  Op de **acties** tabblad kiezen **ophaal- en evaluatiefase gebruikersbeleid** het computerbeleid te initiëren en kies vervolgens **nu uitvoeren**.  

4.  Kies **OK** om te bevestigen.  

5.  Herhaal stap 3 en 4 voor eventuele andere vereiste acties, bijvoorbeeld **Ophaal- en evaluatiefase gebruikersbeleid** voor gebruikersclientinstellingen.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>Handmatig clientbeleid ophalen door het script  

1.  Open een teksteditor, zoals Kladblok.  

2.  Kopieer het volgende en voeg dit in het bestand in:  

    ```  
    on error resume next  

    dim oCPAppletMgr 'Control Applet manager object.  
    dim oClientAction 'Individual client action.  
    dim oClientActions 'A collection of client actions.  

    'Get the Control Panel manager object.  
    set  oCPAppletMgr=CreateObject("CPApplet.CPAppletMgr")  
    if err.number <> 0 then  
        Wscript.echo "Couldn't create control panel application manager"  
        WScript.Quit  
    end if  

    'Get a collection of actions.  
    set oClientActions=oCPAppletMgr.GetClientActions  
    if err.number<>0 then  
        wscript.echo "Couldn't get the client actions"  
        set oCPAppletMgr=nothing  
        WScript.Quit  
    end if  

    'Display each client action name and perform it.  
    For Each oClientAction In oClientActions  

        if oClientAction.Name = "Request & Evaluate Machine Policy" then  
            wscript.echo "Performing action " + oClientAction.Name   
            oClientAction.PerformAction  
        end if  
    next  

    set oClientActions=nothing  
    set oCPAppletMgr=nothing  
    ```  

3.  Sla het bestand op met een VBS-extensie.  

4.  Gebruik een van de volgende methoden om het bestand uit te voeren op de clientcomputer:  

    -   Navigeer in Windows Verkenner naar het bestand en dubbelklik op het scriptbestand.  

    -   Open een opdrachtprompt en typ: **cscript &lt;path\filename.vbs >**.  

5.  Kies **OK** in de **Windows Script Host** in het dialoogvenster.  

