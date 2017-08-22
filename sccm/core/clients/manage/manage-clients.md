---
title: Clients beheren | Microsoft Docs
description: Informatie over het beheren van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: "17"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 3a86924b2e5db3ac16eeda78b95ae6747ffd656f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>Clients beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer een System Center Configuration Manager-client is geïnstalleerd en is toegewezen aan een Configuration Manager-site, ziet u het apparaat in de **activa en naleving** werkruimte in de **apparaten** knooppunt, en in een of meer verzamelingen in de **Apparaatverzamelingen** knooppunt. Wanneer u het apparaat of een verzameling selecteert, kunt u bewerkingen kunt uitvoeren. Er zijn echter ook andere manieren voor het beheren van de client, die andere werkruimtes in de console, of taken die geen gebruikmaken van de Configuration Manager-console kan erbij betrekken.  

> [!NOTE]  
>  Een Configuration Manager-client kan worden geïnstalleerd maar niet weergegeven in de Configuration Manager-console. Dit kan gebeuren als de client nog is nog niet aan een site toegewezen, of de console moet worden vernieuwd of een lidmaatschap moet geüpdatet.  
>   
>  Bovendien een apparaat ook worden weergegeven in de console wanneer de Configuration Manager-client niet is geïnstalleerd. Dit kan gebeuren als het apparaat wordt gedetecteerd, maar de Configuration Manager-client niet is geïnstalleerd en toegewezen. Mobiele apparaten die worden beheerd via de Exchange Server-connector en de apparaten die zijn geregistreerd door Microsoft Intune, Installeer geen Configuration Manager-client.  
>   
>  Gebruik de **Client** kolom in de Configuration Manager-console om te bepalen of Configuration Manager-client is geïnstalleerd zodat u hem vanuit de Configuration Manager-console beheren kunt.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> Clients beheren in het knooppunt Apparaten  

Houd er rekening mee dat, afhankelijk van het apparaattype sommige van deze opties mogelijk niet beschikbaar.  

1.  Kies in de Configuration Manager-console **activa en naleving** >  **apparaten**.  

3.  Selecteer een of meer apparaten en selecteer vervolgens een van deze clientbeheertaken van het lint, of door met de rechtermuisknop op het apparaat:  

    -   **Informatie van affiniteit gebruikerapparaat beheren**  

         Configureer de koppelingen tussen gebruikers en apparaten, zodat u software efficiënt voor gebruikers implementeren kunt.  

         Zie [Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)  

    -   **Het apparaat toevoegen aan een nieuwe of bestaande verzameling**  

         Het apparaat toevoegen aan een verzameling met een directe regel.  
         
    -   **Installeer en installeer de client opnieuw door gebruik te maken van de wizard clientpush.**  

         Installeren en opnieuw installeren van Configuration Manager-client om hem te herstellen of opnieuw te configureren op computers waarop Windows wordt uitgevoerd. Bevat opties voor site-configuratie en client.msi-eigenschappen die u hebt ingesteld voor push-clientinstallatie.  

        > [!TIP]  
        >  Er zijn veel verschillende manieren Configuration Manager-client installeren (en opnieuw installeren). Hoewel de wizard Clientpush een handige biedt client-installatiemethode omdat u hem vanaf de console uitvoeren kunt, wordt deze methode veel afhankelijkheden heeft en is niet geschikt voor alle omgevingen. Zie [Vereisten voor de implementatie van Configuration Manager-clients op Windows-pc's](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) voor meer informatie over de afhankelijkheden. Zie [Clientinstallatiemethoden in System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md) voor meer informatie over de andere clientinstallatiemethoden.  

         Zie [Het installeren van Configuration Manager-Clients met behulp van clientpush](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

    -   **Site opnieuw toewijzen**  

         Wijs één of meerdere klanten, waaronder beheerde mobiele apparaten, toe aan een andere primaire site in de hiërarchie. Clients kunnen afzonderlijk opnieuw worden toegewezen of kunnen meervoudig worden geselecteerd en in bulk aan een nieuwe site worden toegewezen.  

    -   **Extern beheer van de client**  

         U kunt Resource Explorer uitvoeren om de informatie over hardware-en software-inventaris van een Windows-client te raadplegen, en deze te beheren op afstand met afstandsbediening, hulp op afstand, of extern bureaublad.  

         Zie [Resource Explorer gebruiken om hardware-inventaris te bekijken in System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) en [Resource Explorer gebruiken om software-inventaris te bekijken in System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

         Zie [Een Windows-clientcomputer op afstand beheren met System Center Configuration Manager](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md).  

    -   **Een client goedkeuren**  

         Wanneer de client met sitesystemen met HTTP- en een zelfondertekend certificaat communiceert, moet u deze clients als u deze herkennen als vertrouwde computers wilt goedkeuren. Standaard keurt de siteconfiguratie automatisch clients goed van dezelfde Active Directory-forests en vertrouwde forests, zodat u niet elke client handmatig moet goedkeuren. U moet evenwel handmatig werkgroepcomputers goedkeuren die u vertrouwt en andere computers die u vertrouwt, maar die niet goedgekeurd zijn.  

        > [!WARNING]  
        >  Hoewel sommige beheerfuncties voor niet-goedgekeurde clients werken kunnen, is dit een niet-ondersteund scenario voor Configuration Manager.  

         U beschikt niet over goedkeuren die altijd communiceren met sitesystemen via HTTPS-clients of clients die een PKI-certificaat gebruiken wanneer ze communiceren met sitesystemen via HTTP. Deze clients stellen vertrouwen met behulp van de PKI-certificaten.  

    -   **Blokkeren of deblokkeringen van een client**  

         Blokkeer een client die u niet langer vertrouwt, om hem te beletten clientbeleid te krijgen en om te voorkomen dat Configuration Manager-sitesystemen mee te communiceren.  

        > [!WARNING]  
        >  Een client blokkeert alleen verhindert communicatie van de client naar Configuration Manager-sitesystemen en belet geen communicatie met andere apparaten. Wanneer, bijkomend, de client communiceert met sitesystemen door gebruik te maken van HTTP in plaats van HTTPS, zijn er bepaalde beveiligingsbeperkingen.  

         U kunt een client die geblokkeerd werd blokkering opheffen. Indien u evenwel een AMT-gebaseerde computer deblokkeert die was ingericht voor AMT wanneer hij geblokkeerd was, moet u bijkomende stappen ondernemen vóór u die computer opnieuw buiten-band kunt beheren.  

         Zie [Bepalen of clients worden geblokkeerd in System Center Configuration Manager](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

    -   **Wissen van een vereiste PXE-implementatie**  

         Implementeer vereiste PXE-implementaties voor de computer opnieuw.  

         Zie [PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   **De clienteigenschappen beheren**  

         De detectiegegevens en implementaties dat voor de client weergeven. U kunt ook variabelen die takenreeksen gebruiken voor het implementeren van een besturingssysteem op het apparaat configureren.  

    -   **Verwijderen van de client**  

        > [!WARNING]  
        >  Een client niet verwijderen als u wilt de Configuration Manager-client te verwijderen of te verwijderen uit een verzameling.  

         De **verwijderen** actie wist handmatig het client-record van de Configuration Manager-database en typisch, dient u deze actie behalve probleemoplossende scenario's niet gebruiken. Als u het clientrecord wist en de client nog steeds geïnstalleerd en communicatie met Configuration Manager door Heartbeat-detectie het clientrecord opnieuw creëren en zal het opnieuw verschijnen in de Configuration Manager-console, hoewel de clientgeschiedenis en vroegere koppelingen verloren zullen zijn.  

        > [!NOTE]  
        >  Wanneer u een client voor mobiele apparaten dat is geregistreerd door Configuration Manager verwijdert, wordt deze actie ook het PKI-certificaat dat was uitgegeven aan het mobiele apparaat worden ingetrokken en wordt dit certificaat wordt dan geweigerd door het beheerpunt, zelfs als IIS de CRL niet controleert. Certificaten op verouderde mobiele apparaten worden niet ingetrokken wanneer u deze clients wist.  

         Om de installatie van de client ongedaan te maken, zie [De installatie van de Configuration Manager-client ongedaan maken](#BKMK_UninstalClient).  

         Zie [Clients toewijzen aan een site in System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md) voor meer informatie over het toewijzen van de client aan een nieuwe primaire site.  

         Configureer, om de client te verwijderen uit een verzameling, opnieuw de eigenschappen van de verzameling. Zie [Verzamelingen beheren in System Center Configuration Manager](../../../core/clients/manage/collections/manage-collections.md).  

    -   **Een mobiel apparaat wissen**  

         U kunt mobiele apparaten wissen die de wisopdracht ondersteunen.  

         Deze actie verwijdert permanent alle gegevens op het mobiele apparaat, met inbegrip van persoonlijke instellingen en persoonlijke gegevens. Typisch zet deze actie het mobiele apparaat terug naar zijn fabrieksinstellingen. Wissen op een mobiel apparaat wanneer het mobiele apparaat niet langer vertrouwd, bijvoorbeeld als dit is zoekgeraakt of gestolen.  

        > [!TIP]  
        >  Raadpleeg de documentatie van de fabrikant voor meer informatie over hoe het mobiele apparaat een externe wisopdracht verwerkt.  

         Er is vaak een vertraging totdat het mobiele apparaat de wisopdracht ontvangt:  

        -   Als het mobiele apparaat is ingeschreven door Configuration Manager of door Microsoft Intune, ontvangt de client de opdracht wanneer het het clientbeleid downloadt.  

        -   Als het mobiele apparaat wordt beheerd door de Exchange Server-connector, ontvangt de opdracht wanneer het synchroniseert met Exchange.  

         U kunt de **Wisstatus** kolom om te controleren wanneer het apparaat de wisopdracht ontvangt. U kunt de wisopdracht annuleren totdat het apparaat een wisbevestiging naar Configuration Manager verzendt.  

    -   **Een mobiel apparaat buiten gebruik stellen**  

         De **buiten gebruik stellen** optie wordt alleen ondersteund door mobiele apparaten die zijn ingeschreven door Intune of door op\-premises Mobile Device Management.  

         Zie [Help uw gegevens beschermen met wissen op afstand, vergrendelen op afstand of opnieuw instellen van wachtwoordcode met behulp van System Center Configuration Manager](../../../mdm/deploy-use/wipe-lock-reset-devices.md) voor meer informatie.  

    -   **Het eigendom van een apparaat wijzigen**  

         U kunt de eigendom van apparaten te wijzigen **bedrijf** of **persoonlijke** als een apparaat geen lid van een domein en geen Configuration Manager-client geïnstalleerd heeft.  

         U kunt deze waarde gebruiken in toepassingsvereisten om implementaties te controleren en om te bepalen hoeveel inventaris worden verzameld van de apparaten van gebruikers.  

        U wilt toevoegen de **eigenaar van het apparaat** kolom naar de weergave door met de rechtermuisknop op een kolomkop en deze te kiezen.

         Zie [Hybride Mobile Device Management (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md) voor meer informatie.  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> Clients beheren in het knooppunt Apparaatverzamelingen  
  Veel van de taken die u kunt uitvoeren op één apparaat of op meerdere apparaten in de **apparaten** knooppunt op verzamelingen kan worden uitgevoerd. Dit de bewerking voor het automatisch toegepast op alle verkiesbare apparaten in de verzameling. Houd er rekening mee dat dit veel netwerkpakketten genereert en verhoogt de CPU-gebruik op de siteserver.  

  Houd rekening, vóór u clientbeheertaken uitvoert op het niveau van verzameling, met het aantal apparaten in de verzameling, of ze verbonden zijn door lage-bandbreedte-netwerkverbindingen en met hoe lang de taak zal duren vóór hij wordt voltooid door alle apparaten. Eenmaal gestart, kunt u de taak van de console kan niet stoppen.  

#### <a name="to-manage-clients-from-the-device-collections-node"></a>Clients beheren in het knooppunt Apparaatverzamelingen  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Apparaatverzamelingen**.  

3.  Selecteer een verzameling en selecteer vervolgens een van de volgende clientbeheertaken van het lint, of door met de rechtermuisknop op de verzameling. Deze clientbeheertaken kunnen *alleen* worden uitgevoerd op het niveau verzameling.  

    -   **Scan computers op schadelijke software en download anti-malware-definitiebestanden.**  

         Zie [Endpoint Protection in System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

    -   **Software, configuratiebasislijnen en takenreeksen implementeren.**  

         Zie:  

        -   [Software-updates in System Center Configuration Manager implementeren](../../../sum/deploy-use/deploy-software-updates.md)  

        -   [Plannen en configureren van instellingen voor naleving in System Center Configuration Manager](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

    -   **Energiebeheerinstellingen configureren.**  

         Zie [Energiebeheerschema's maken en toepassen in System Center Configuration Manager](../../../core/clients/manage/power/create-and-apply-power-plans.md). Energiebeheerplannen kunnen enkel worden gebruikt met computers die Windows uitvoeren.  

    -   **Verwittig zo snel mogelijk computers om beleid te downloaden.**  

         Gebruik clientmelding om de geselecteerde Windows-clients voor het downloaden van computerbeleid zo snel mogelijk buiten het pollinginterval voor clientbeleid in kennis.  

         Clientmeldingstaken worden weergegeven in het knooppunt **Clientbewerkingen** in de werkruimte **Bewaken** .  

##  <a name="BKMK_ClientCache"></a> De clientcache configureren voor Configuration Manager-clients  
De clientcache slaat tijdelijke bestanden voor wanneer clients toepassingen en programma's installeren. De clientcache wordt eveneens gebruikt door software-updates, maar software-updates worden niet beperkt door de geconfigureerde cachegrootte en worden altijd gedownload naar de cache. U kunt de clientcache-instellingen, zoals de grootte en locatie, configureren wanneer u de Configuration Manager-client handmatig installeert wanneer u push-clientinstallatie of nadat de client is geïnstalleerd.

Beginnend met Configuration Manager versie 1606, kunt u de cachegrootte van de map met clientinstellingen in de Configuration Manager-console.   

 De standaardlocatie voor de Configuration Manager-clientcache is %*windir*%\ccmcache en de standaardschijfruimte is 5120 MB.  

> [!IMPORTANT]  
>  Versleutel de map die wordt gebruikt voor de clientcache niet. Door Configuration Manager kan geen inhoud naar een versleutelde map worden gedownload.  

### <a name="about-client-cache"></a>Over de clientcache  

Configuration Manager-client downloadt de inhoud voor vereiste software kort na de implementatie wordt ontvangen, maar deze wordt uitgevoerd totdat de geplande tijd. Op het geplande tijdstip, Configuration Manager-client gecontroleerd of de inhoud beschikbaar in de cache is. Als de inhoud zich in de cache en de juiste versie is, gebruikt de client de inhoud in de cache. Wanneer de vereiste versie van de inhoud is gewijzigd of als de inhoud is verwijderd om ruimte voor een ander pakket te maken, wordt de inhoud opnieuw naar de cache gedownload.  

Als de client probeert inhoud te downloaden voor een programma dat of toepassing die groter is dan de grootte van de cache, mislukt de implementatie vanwege ontoereikende cachegrootte en Configuration Manager genereert statusbericht-ID 10050. Als de cache later wordt vergroot, wordt het resultaat is:  

-   Voor een vereist programma: De client probeert niet automatisch opnieuw de inhoud te downloaden. U moet het pakket en programma opnieuw implementeren op de client.  
-   Voor een vereiste toepassing: De client wordt automatisch opnieuw geprobeerd de inhoud te downloaden wanneer deze keer zijn clientbeleid downloadt.  

Als de client probeert te downloaden van een pakket dat is minder dan de grootte van de cache, maar de cache volledig is, worden alle vereiste implementaties blijven proberen totdat de cacheruimte beschikbaar is, totdat het downloaden van de time-out of totdat de limiet voor opnieuw proberen is bereikt voor de mislukking van de cache-ruimte. Als de cache later wordt vergroot, probeert de Configuration Manager-client te downloaden van het pakket opnieuw tijdens de volgende interval opnieuw. De client probeert de inhoud elke vier uur te downloaden tot het achttien keer is geprobeerd.  

Inhoud in de cache wordt niet automatisch verwijderd, maar blijft minimaal één dag in de cache nadat de client die inhoud heeft gebruikt. Als u de pakketeigenschappen configureert met de optie om inhoud permanent te behouden in de clientcache, wordt de pakketinhoud niet automatisch verwijderd uit de cache. Als de cacheruimte voor de client wordt gebruikt door pakketten die de afgelopen 24 uur zijn gedownload en er nieuwe pakketten moeten worden gedownload, kunt u de cachegrootte voor de client uitbreiden of de verwijderingsoptie kiezen om blijvende cache-inhoud te verwijderen.  

 Gebruik de volgende procedures om de clientcache te configureren tijdens de handmatige clientinstallatie of nadat de client is geïnstalleerd.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>De clientcache configureren wanneer u clients installeert op basis van een handmatige clientinstallatie  

Voer de opdracht CCMSetup.exe uit vanaf de installatiebronlocatie en geef de volgende eigenschappen op, indien vereist (gescheiden door spaties):  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Voor versie 1606, gebruikt u de cache voor grootte-instellingen beschikbaar zijn in **clientinstellingen** in de Configuration Manager-console in plaats van SMSCACHESIZE. Zie [Clientcache-instellingen](../../../core/clients/deploy/about-client-settings.md#client-cache-settings) voor meer informatie.

Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over het gebruik van deze opdrachtregeleigenschappen voor CCMSetup.exe.  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>De clientcache configureren wanneer u clients installeert op basis van een push-clientinstallatie  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de gewenste website, en klik op de **Start** tabblad, in de **instellingen** groep, kiest u **clientinstallatie-instellingen** > **installatie-eigenschappen tabblad**.  

5.  Geef de volgende eigenschappen, gescheiden door spaties:  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Voor versie 1606, gebruikt u de cache voor grootte-instellingen beschikbaar zijn in **clientinstellingen** in de Configuration Manager-console in plaats van SMSCACHESIZE. Zie [Clientcache-instellingen](../../../core/clients/deploy/about-client-settings.md#client-cache-settings) voor meer informatie.

       Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over het gebruik van deze opdrachtregeleigenschappen voor CCMSetup.exe.  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>De clientcachemap configureren op de clientcomputer  

1.  Navigeer op de clientcomputer naar **Configuration Manager** in het Configuratiescherm en dubbelklik om de eigenschappen te openen.  

2.  Op de **Cache** tabblad Eigenschappen ruimte en locatie instellen. De standaardlocatie is *%windir%*\ccmcache.  

5.  Voor het verwijderen van de bestanden in de cachemap kiezen **bestanden verwijderen**.  

    > [!NOTE]
    > 
    > De cachemap is een gewone Windows-map, zodat u de verwijdering van de inhoud van de map met een script, een hulpprogramma of met de PowerShell-cmdlet kunt automatiseren `Remove-Item`. 


### <a name="to-configure-client-cache-size-in-client-settings"></a>De client-cachegrootte in clientinstellingen configureren

Vanaf versie 1606, kunt u de grootte van de clientcachemap aanpassen zonder de client opnieuw installeert. Om dit te doen, configureert u de client-cachegrootte in de Configuration Manager-console via Clientinstellingen.  

1. Ga in de Configuration Manager-console naar **Beheer** > **Clientinstellingen**.

2. Dubbelklik op **Standaardclientinstellingen**.
  U kunt ook aangepaste clientinstellingen maken zodat u de cachegrootte selectiever kunt toepassen. Zie [Clientinstellingen in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-settings.md) voor meer informatie over standaardclientinstellingen en aangepaste clientinstellingen.

 3. Kies **clientcache-instellingen** en kies **Ja** voor **clientcachegrootte configureren**, gebruik de **MB** of **percentage van de instellingen voor de schijf**. De cache wordt aangepast aan de kleinste grootte.

     De Configuration Manager-client configureert de cachegrootte op grond van deze instellingen de volgende keer dat er een clientbeleid wordt gedownload.

##  <a name="BKMK_UninstalClient"></a> De Configuration Manager-client verwijderen  
 U kunt de Windows Configuration Manager-clientsoftware verwijderen van een computer met behulp van **CCMSetup.exe** met de **/Uninstall** eigenschap. Voer CCMSetup.exe op een afzonderlijke computer uit via de opdrachtprompt of implementeer een pakket en programma om de client te verwijderen voor een verzameling computers.  

> [!WARNING]  
>  U kunt de Configuration Manager-client niet verwijderen van een mobiel apparaat. Als u de Configuration Manager-client van een mobiel apparaat verwijdert moet, moet u het apparaat verwijdert u alle gegevens op het mobiele apparaat wissen.  

#### <a name="to-uninstall-the-configuration-manager-client-from-the-command-prompt"></a>De Configuration Manager-client verwijderen via de opdrachtprompt  

1.  Open een Windows-opdrachtprompt en wijzig de map in de locatie waarin CCMSetup.exe zich bevindt.  

2.  Typ **Ccmsetup.exe /uninstall**en druk op **Enter**.  

> [!NOTE]  
>  Het verwijderingsproces worden geen resultaten weergegeven op het scherm. Om te controleren of client is verwijderd, bekijkt u het logbestand **CCMSetup.log** in de map *%windir%\ ccmsetup* op de clientcomputer.  

##  <a name="BKMK_ConflictingRecords"></a> Conflicterende records voor Configuration Manager-clients beheren  
 Configuration Manager gebruikt de hardware-ID om clients te identificeren die mogelijk zijn gedupliceerd en u te waarschuwen voor conflicterende records. Bijvoorbeeld, als u een computer installeert, de hardware-ID zou dezelfde, maar de GUID die wordt gebruikt door Configuration Manager kan worden gewijzigd.  

 Wanneer de Configuration Manager een conflict kan oplossen met behulp van Windows-verificatie van het computeraccount of een PKI-certificaat van een vertrouwde bron, wordt het conflict automatisch voor u opgelost. Echter, wanneer het conflict kan niet worden omgezet in Configuration Manager, gebruikt een hiërarchie-instelling dat een automatisch de records worden samengevoegd wanneer dubbele hardware-id's (de standaardinstelling) worden gedetecteerd of kunt u bepalen wanneer samenvoegen, blokkeren of nieuwe client-records maken. Als u besluit dubbele records handmatig te beheren, moet u de conflicterende records in de Configuration Manager-console handmatig oplossen.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>De hiërarchie-instellingen wijzigen voor het beheren van conflicterende records  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites** > **hiërarchie-instellingen**
2.  Op de **goedkeuring van Client en conflicterende Records** tabblad, kiest u **conflicterende records automatisch oplossen**, of **conflicterende records handmatig oplossen**.  

#### <a name="to-manually-resolve-conflicting-records"></a>Conflicterende records handmatig oplossen  

1.  Kies in de Configuration Manager-console **bewaking** > **systeemstatus** > **conflicterende Records**.  

3.  Selecteer een of meer conflicterende records en kies vervolgens **conflicterende Record**.  

4.  Selecteer vervolgens een van de volgende opties:  

    -   **Samenvoegen** combineren van de nieuwe record met de bestaande clientrecord.  

    -   **Nieuw** : maak een nieuwe record voor de conflicterende clientrecord.  

    -   **Blokkeren** : maak een nieuwe record voor de conflicterende clientrecord, maar markeer deze als geblokkeerd.  

## <a name="manage-duplicate-hardware-identifiers"></a>Dubbele hardware-id's beheren
U kunt een lijst met hardware-id's in Configuration Manager wordt genegeerd voor PXE-opstart- en clientregistratie vanaf Configuration Manager versie 1610, opgeven. Er zijn twee veelvoorkomende problemen die hierdoor adres.

1. Veel nieuwe apparaten, zoals Surface Pro, 3, beschikken niet over een ingebouwde Ethernet-poort. Een USB-Ethernet-adapter wordt doorgaans een bekabelde verbinding ten behoeve van de implementatie van besturingssystemen worden gebruikt. Dit zijn echter vaak gedeelde adapters vanwege de kosten en algemene bruikbaarheid. Omdat het MAC-adres van deze adapter wordt gebruikt om het apparaat hebt geïdentificeerd, wordt hergebruiken van de adapter problematisch zonder extra beheerdersacties weergegeven tussen elke implementatie. Vanaf versie 1610, kunt u het MAC-adres van deze adapter uitsluiten, zodat deze opnieuw kan worden gebruikt in dit scenario.
2. Terwijl de SMBIOS-ID een unieke hardware-id zijn moet, worden sommige speciale hardware-apparaten zijn gebouwd met dubbele id. Hoewel dit niet zo gebruikelijk zijn als het bovenstaande USB Ethernet-adapter scenario, kan de lijst met hardware-id's voor het oplossen van dit probleem ook worden gebruikt.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Toevoegen van hardware-id's voor Configuration Manager te negeren  
1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.
2. Op de **Start** tabblad, in de **Sites** groep, kiest u **hiërarchie-instellingen**.
3. Op de **goedkeuring van Client en conflicterende Records** Kies **toevoegen** in de **dubbele hardware-id's** sectie voor het toevoegen van nieuwe hardware-id's.

##  <a name="BKMK_PolicyRetrieval"></a> Ophalen van beleid initiëren voor een Configuration Manager-client  
 Een Windows Configuration Manager-client downloadt het clientbeleid volgens een schema dat u configureert als een clientinstelling. Echter, kunnen er gevallen, als u ad-hoc beleid direct op te halen van de client, bijvoorbeeld wilt voor het oplossen van problemen of testen.  

U kunt starten ophalen met behulp van beleid:


- [Clientmeldingen](#initiate-client-policy-retrieval-using-client-notification) 
- [De **acties** tabblad op de client](#manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client)
- [Een script](#manually-initiate-client-policy-retrieval-by-script)

> [!NOTE]  
>   
>  Zie [Computerbeleid voor Linux- en UNIX-servers](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_PolicyforLnU) voor informatie over het ophalen van beleid voor clients met Linux en UNIX.  

#### <a name="initiate-client-policy-retrieval-using-client-notification"></a>Clientbeleid ophalen met behulp van clientmeldingen  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Apparaatverzamelingen**.  

3.  Selecteer de apparaatverzameling met de computers waarvan u beleid wilt downloaden. Op de **Start** tabblad, in de **verzamelingen** groep, kiest u **Clientmelding** > **computerbeleid downloaden**.  

    > [!NOTE]  
    >  U kunt Clientmelding ook gebruiken om beleid op te halen voor een of meer geselecteerde apparaten die worden weergegeven in een tijdelijk verbindingsknooppunt onder het knooppunt **Apparaten** .  

#### <a name="manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client"></a>Clientbeleid ophalen op het tabblad acties van de Configuration Manager-client handmatig te starten  

1.  Selecteer **Configuration Manager** in het Configuratiescherm van de computer.  

2.  Op de **acties** tabblad kiezen **ophaal- en evaluatiefase computerbeleid** het computerbeleid te initiëren en klik vervolgens op **nu uitvoeren**.  

4.  Kies **OK** om te bevestigen.  

5.  Herhaal stap 3 en 4 voor eventuele andere vereiste acties, bijvoorbeeld **Ophaal- en evaluatiefase gebruikersbeleid** voor gebruikersclientinstellingen.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>Clientbeleid handmatig starten door script  

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

    -   Open een opdrachtprompt en typ: **cscript &lt;pad\bestandsnaam.vbs >**.  

5.  Kies **OK** in de **Windows Script Host** in het dialoogvenster.  
