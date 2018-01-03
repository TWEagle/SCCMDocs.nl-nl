---
title: Clients beheren
titleSuffix: Configuration Manager
description: Informatie over het beheren van clients in System Center Configuration Manager.
ms.custom: na
ms.date: 12/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: "17"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 2065fd0910b1d89df3f8296c87ede15b89331568
ms.sourcegitcommit: 528b1ce79803fecd34937a790e9b5cde282d4caa
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>Clients beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer de Configuration Manager-client op een apparaat installeert en is toegewezen aan een site, ziet u het apparaat in de **activa en naleving** werkruimte in de **apparaten** knooppunt en een of meer verzamelingen in de **Apparaatverzamelingen** knooppunt. Wanneer u het apparaat of een verzameling selecteert, kunt u bewerkingen kunt uitvoeren. Er zijn echter andere manieren voor het beheren van de client, die andere werkruimtes in de console, of taken buiten de beheerconsole kan erbij betrekken.  

> [!NOTE]  
>  Als Configuration Manager-client is geïnstalleerd, maar is nog niet is toegewezen aan een site, mogelijk niet weergegeven in de console. Nadat de client aan een site toewijst, het lidmaatschap van verzameling bijwerken en vernieuw de weergave van de console.  
>   
>  Bovendien een apparaat ook worden weergegeven in de console wanneer de Configuration Manager-client niet is geïnstalleerd. Dit gedrag gebeurt er als het apparaat wordt gedetecteerd, maar de client niet is geïnstalleerd en toegewezen. 
>
> Mobiele apparaten die worden beheerd met behulp van de Exchange Server-connector en de apparaten die zijn geregistreerd bij Microsoft Intune installeert de Configuration Manager-client niet.  
>   
>  Gebruik de **Client** kolom in de Configuration Manager-console om te bepalen of de client is geïnstalleerd zodat u hem vanuit de console beheren kunt.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> Clients beheren in het knooppunt Apparaten  

Afhankelijk van het apparaattype, kunnen sommige van deze opties niet beschikbaar zijn.  

1.  Kies in de Configuration Manager-console **activa en naleving** >  **apparaten**.  

3.  Selecteer een of meer apparaten en selecteer vervolgens een van deze clientbeheertaken van het lint, of door met de rechtermuisknop op het apparaat:  

    -   **Informatie van affiniteit gebruikerapparaat beheren**  

         Configureer de koppelingen tussen gebruikers en apparaten, zodat u software efficiënt voor gebruikers implementeren kunt.  

         Zie [Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)  

    -   **Het apparaat toevoegen aan een nieuwe of bestaande verzameling**  

         Het apparaat toevoegen aan een verzameling met een directe regel.  

    -   **Installeer en installeer de client opnieuw door gebruik te maken van de wizard clientpush.**  

         Installeren en opnieuw installeren van Configuration Manager-client om te herstellen of configureer het opnieuw. Deze optie omvat siteconfiguratie-instellingen en client.msi-eigenschappen die u hebt ingesteld voor push-clientinstallatie.  

        > [!TIP]  
        >  Er zijn veel verschillende manieren Configuration Manager-client installeren (en opnieuw installeren). Hoewel de wizard Clientpush een handige biedt client-installatiemethode omdat u hem vanaf de console uitvoeren kunt, wordt deze methode veel afhankelijkheden heeft en is niet geschikt voor alle omgevingen. Zie [Vereisten voor de implementatie van Configuration Manager-clients op Windows-pc's](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md) voor meer informatie over de afhankelijkheden. Zie [Clientinstallatiemethoden in System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md) voor meer informatie over de andere clientinstallatiemethoden.  

         Zie [Het installeren van Configuration Manager-Clients met behulp van clientpush](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

    -   **Site opnieuw toewijzen**  

         Wijs één of meerdere klanten, waaronder beheerde mobiele apparaten, toe aan een andere primaire site in de hiërarchie. Clients kunnen afzonderlijk opnieuw worden toegewezen of kunnen meervoudig worden geselecteerd en in bulk aan een nieuwe site worden toegewezen.  

    -   **Extern beheer van de client**  

         Resource Explorer uitvoeren om de hardware en software-inventarisatie-informatie van een Windows-client zien. Het apparaat op afstand beheren met behulp van beheer op afstand, hulp op afstand en extern bureaublad.  

         Zie [Resource Explorer gebruiken om hardware-inventaris weer te geven](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) en [Resource Explorer gebruiken om software-inventaris weer te geven](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

         Zie [extern beheren van een Windows-clientcomputer](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md).  

    -   **Een client goedkeuren**  

         Wanneer de client met sitesystemen met HTTP- en een zelfondertekend certificaat communiceert, moet u deze clients als u deze herkennen als vertrouwde computers wilt goedkeuren. Standaard keurt de siteconfiguratie automatisch clients goed van dezelfde Active Directory-forests en vertrouwde forests, zodat u niet elke client handmatig moet goedkeuren. U moet echter handmatig goedkeuren computers in werkgroepen die u vertrouwt en andere niet-goedgekeurde computers die u vertrouwt.  

        > [!WARNING]  
        >  Hoewel sommige beheerfuncties voor niet-goedgekeurde clients werken kunnen, is dit een niet-ondersteund scenario voor Configuration Manager.  

         U beschikt niet over goedkeuren die altijd communiceren met sitesystemen via HTTPS-clients of clients die een PKI-certificaat gebruiken wanneer ze communiceren met sitesystemen via HTTP. Deze clients stellen vertrouwen met behulp van de PKI-certificaten.  

    -   **Blokkeren of deblokkeringen van een client**  

         Blokkeer een client die u niet langer vertrouwt. Blokkering voorkomt dat de client beleid ontvangt en voorkomt dat sitesystemen communiceren met de client.  

        > [!WARNING]  
        >  Een client blokkeert alleen verhindert communicatie van de client naar Configuration Manager-sitesystemen en belet geen communicatie met andere apparaten. Wanneer, bijkomend, de client communiceert met sitesystemen door gebruik te maken van HTTP in plaats van HTTPS, zijn er bepaalde beveiligingsbeperkingen.  

         U kunt ook de blokkering opheffen voor een client die is geblokkeerd. 

         Zie [Bepalen of clients worden geblokkeerd in System Center Configuration Manager](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

    -   **Wissen van een vereiste PXE-implementatie**  

         Implementeer vereiste PXE-implementaties voor de computer opnieuw.  

         Zie [PXE gebruiken om Windows via het netwerk te implementeren met System Center Configuration Manager](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   **De clienteigenschappen beheren**  

         De detectiegegevens en implementaties dat voor de client weergeven. U kunt ook variabelen die takenreeksen gebruiken voor het implementeren van een besturingssysteem op het apparaat configureren.  

    -   **Verwijderen van de client**  

        > [!WARNING]  
        >  Een client niet verwijderen als u wilt de Configuration Manager-client te verwijderen of te verwijderen uit een verzameling.  

         De **verwijderen** actie wist handmatig het client-record van de Configuration Manager-database en typisch, dient u deze actie behalve probleemoplossende scenario's niet gebruiken. Als u verwijdert de clientrecord, maar de client nog steeds geïnstalleerd is en communicatie met de site, Heartbeat-detectie het clientrecord opnieuw. Het client-record opnieuw wordt weergegeven in de Configuration Manager-console, hoewel de clientgeschiedenis en vroegere koppelingen verloren.  

        > [!NOTE]  
        >  Wanneer u een client voor mobiele apparaten dat is geregistreerd door Configuration Manager verwijdert, wordt deze actie ook het PKI-certificaat dat was uitgegeven aan het mobiele apparaat worden ingetrokken en wordt dit certificaat wordt dan geweigerd door het beheerpunt, zelfs als IIS de CRL niet controleert. Certificaten op verouderde mobiele apparaten worden niet ingetrokken wanneer u deze clients wist.  

         Om de installatie van de client ongedaan te maken, zie [De installatie van de Configuration Manager-client ongedaan maken](#BKMK_UninstalClient).  

         Zie [Clients toewijzen aan een site in System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md) voor meer informatie over het toewijzen van de client aan een nieuwe primaire site.  

         Configureer, om de client te verwijderen uit een verzameling, opnieuw de eigenschappen van de verzameling. Zie [Verzamelingen beheren in System Center Configuration Manager](../../../core/clients/manage/collections/manage-collections.md).  

    -   **Een mobiel apparaat wissen**  

         U kunt mobiele apparaten wissen die de wisopdracht ondersteunen.  

         Deze actie verwijdert permanent alle gegevens op het mobiele apparaat, met inbegrip van persoonlijke instellingen en persoonlijke gegevens. Typisch zet deze actie het mobiele apparaat terug naar zijn fabrieksinstellingen. Een mobiel apparaat wissen wanneer het mobiele apparaat niet meer vertrouwd wordt. Bijvoorbeeld als het apparaat is zoekgeraakt of gestolen.  

        > [!TIP]  
        >  Raadpleeg de documentatie van de fabrikant voor meer informatie over hoe het mobiele apparaat een externe wisopdracht verwerkt.  

         Er is vaak een vertraging totdat het mobiele apparaat de wisopdracht ontvangt:  

        -   Als het mobiele apparaat is ingeschreven door Configuration Manager of door Microsoft Intune, ontvangt de client de opdracht wanneer het het clientbeleid downloadt.  

        -   Als het mobiele apparaat wordt beheerd door de Exchange Server-connector, ontvangt de opdracht wanneer het synchroniseert met Exchange.  

         U kunt de **Wisstatus** kolom om te controleren wanneer het apparaat de wisopdracht ontvangt. Totdat het apparaat een wisbevestiging naar Configuration Manager verzendt, kunt u de wisopdracht annuleren.  

    -   **Een mobiel apparaat buiten gebruik stellen**  

         De **buiten gebruik stellen** optie wordt alleen ondersteund door mobiele apparaten die zijn geregistreerd door Microsoft Intune of op\-premises beheer van mobiele apparaten.  

         Zie [Help uw gegevens beschermen met wissen op afstand, vergrendelen op afstand of opnieuw instellen van wachtwoordcode met behulp van System Center Configuration Manager](../../../mdm/deploy-use/wipe-lock-reset-devices.md) voor meer informatie.  

    -   **Het eigendom van een apparaat wijzigen**  

         Gebruik deze optie als u een apparaat is niet lid zijn van een domein en heeft geen Configuration Manager-client geïnstalleerd, de eigenaar te wijzigen **bedrijf** of **persoonlijke**.  

         U kunt deze waarde gebruiken in toepassingsvereisten om implementaties te controleren en om te bepalen hoeveel inventaris worden verzameld van de apparaten van gebruikers.  

        U wilt toevoegen de **eigenaar van het apparaat** kolom naar de weergave door met de rechtermuisknop op een kolomkop en deze te kiezen.

         Zie [Hybride Mobile Device Management (MDM) met System Center Configuration Manager en Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md) voor meer informatie.  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a>Clients beheren in het knooppunt Apparaatverzamelingen  
  Veel van de taken die beschikbaar zijn voor apparaten in de **apparaten** knooppunt zijn ook beschikbaar in verzamelingen. De bewerking de-console automatisch toegepast op alle verkiesbare apparaten in de verzameling. Deze actie op een volledige verzameling worden aanvullende netwerkpakketten genereert en verhoogt de CPU-gebruik op de siteserver.  

  Overweeg het volgende voordat u niveau verzameling taken uitvoeren. Eenmaal gestart, kunt u de taak van de console kan niet stoppen. 
 - Hoeveel apparaten worden in de verzameling?
 - Zijn de apparaten die verbonden door lage bandbreedte-netwerkverbindingen?
 - Hoeveel tijd biedt voor deze taak moet uitvoeren voor alle apparaten?

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


## <a name="restart-clients"></a>Clients opnieuw starten
Vanaf versie 1710, kunt u de Configuration Manager-console op welke clients opnieuw worden opgestart moeten. Gebruik vervolgens een actie van de melding client te starten.

> [!Tip]
> U moet ook clients upgraden naar versie 1710 voor deze mogelijkheid functie. Het is raadzaam om automatische Clientupgrade uw clients up-to-date te houden met een minimale administratieve overhead in te schakelen. Zie voor meer informatie [automatische Clientupgrade gebruikt](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#use-automatic-client-upgrade).

Om apparaten te identificeren die opnieuw opgestart worden, gaat u naar de **activa en naleving** werkruimte in de Configuration Manager-console en selecteer de **apparaten** knooppunt. De status voor elk apparaat vervolgens bekijken in het detailvenster in een nieuwe kolom die met de naam **in behandeling opnieuw**. Elk apparaat heeft een of meer van de volgende waarden: 
 - **Geen**: Er is geen te worden opgestart
 - **Configuration Manager**: deze waarde wordt opgehaald van de client opnieuw opstarten coordinator component (RebootCoordinator.log)
 - **Wijzig de naam van het bestand**: deze waarde wordt opgehaald uit Windows reporting een naamswijziging in behandeling zijnde (HKLM\SYSTEM\CurrentControlSet\Control\Session Manager, PendingFileRenameOperations)
 - **Windows Update**: deze waarde wordt opgehaald uit de Windows Update Agent rapportering in behandeling opnieuw opstarten is vereist voor een of meer updates (HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update\RebootRequired)
 - **Toevoegen of verwijderen van de functie**: deze waarde wordt opgehaald van de onderdelen gebaseerde onderhoud van Windows reporting toevoeging of verwijdering van een Windows-onderdeel moet worden opgestart (HKLM\Software\Microsoft\Windows\CurrentVersion\Component op basis van Servicing\Reboot In behandeling)

**De clientmelding opnieuw opstarten van een apparaat maken:**
1.  Zoek het apparaat dat u wilt starten binnen een verzameling in de **Apparaatverzamelingen** knooppunt van de console.
2.  Met de rechtermuisknop op het apparaat, selecteer **Clientmelding**, en selecteer vervolgens **opnieuw**. Een verschijnt informatie over het opnieuw opstarten. Klik op **OK** om te bevestigen dat de aanvraag opnieuw.

Wanneer de melding wordt ontvangen door een client een **Software Center** meldingsvenster wordt geopend om te informeren over de gebruiker over de herstart. Standaard wordt het opnieuw opstarten na 90 minuten plaatsvindt. U kunt voor het opstarten wijzigen door het configureren van [clientinstellingen](/sccm/core/clients/deploy/configure-client-settings). Instellingen voor het gedrag voor opnieuw opstarten worden gevonden op de [opnieuw opstarten van Computer](/sccm/core/clients/deploy/about-client-settings#computer-restart) tabblad van de standaardinstellingen.


##  <a name="BKMK_ClientCache"></a> De clientcache configureren voor Configuration Manager-clients  
De clientcache slaat tijdelijke bestanden voor wanneer clients toepassingen en programma's installeren. Software-updates ook de clientcache te gebruiken, maar altijd probeert te downloaden naar de cache, ongeacht de instelling. Configureer de instellingen van de cache, zoals de grootte en locatie, wanneer u de client handmatig installeert wanneer u de client-pushinstallatie gebruikt of na de installatie.

Beginnend met Configuration Manager versie 1606, kunt u de cachegrootte van de map met clientinstellingen in de Configuration Manager-console.   

 De standaardlocatie voor de Configuration Manager-clientcache is %*windir*%\ccmcache en de standaardschijfruimte is 5120 MB.  

> [!IMPORTANT]  
>  Versleutel de map die wordt gebruikt voor de clientcache niet. Door Configuration Manager kan geen inhoud naar een versleutelde map worden gedownload.  

### <a name="about-client-cache"></a>Over de clientcache  

Configuration Manager-client downloadt de inhoud voor vereiste software kort na de implementatie wordt ontvangen, maar deze wordt uitgevoerd totdat de geplande tijd. Op het geplande tijdstip, Configuration Manager-client gecontroleerd of de inhoud beschikbaar in de cache is. Als de inhoud zich in de cache en de juiste versie is, gebruikt de client de inhoud in de cache. Wanneer de vereiste versie van de inhoud wordt gewijzigd, of als de client de inhoud ruimte maken voor een ander pakket verwijdert, downloadt de client de inhoud opnieuw naar de cache.  

Als de client probeert inhoud te downloaden voor een programma dat of toepassing die groter is dan de grootte van de cache, mislukt de implementatie vanwege ontoereikende cachegrootte. De client genereert statusbericht 10050 ontoereikende cachegrootte. Als u later de cachegrootte verhoogt, wordt het resultaat is:  

-   Voor een vereist programma: De client probeert niet automatisch opnieuw de inhoud te downloaden. Het pakket en programma om de client te implementeren.  
-   Voor een vereiste toepassing: De client wordt automatisch opnieuw geprobeerd de inhoud te downloaden wanneer deze keer zijn clientbeleid downloadt.  

Als de client probeert te downloaden van een pakket dat is minder dan de grootte van de cache, maar de cache volledig is, worden alle vereiste implementaties blijven proberen totdat de cacheruimte beschikbaar is, het downloaden van de time-out of de limiet bereikt die is het aantal nieuwe pogingen. Als de cache later wordt vergroot, probeert de Configuration Manager-client te downloaden van het pakket opnieuw tijdens de volgende interval opnieuw. De client probeert de inhoud elke vier uur te downloaden tot het achttien keer is geprobeerd.  

Inhoud in de cache wordt niet automatisch verwijderd, maar blijft minimaal één dag in de cache nadat de client die inhoud heeft gebruikt. Als u de pakketeigenschappen configureert met de optie om inhoud permanent te behouden in de clientcache, wordt de pakketinhoud niet automatisch verwijderd uit de cache. Als de cacheruimte wordt gebruikt door pakketten in de afgelopen 24 uur wordt gedownload en nieuwe pakketten moeten worden gedownload, kunt u de cache vergroten of kies de optie verwijderen blijvende cache-inhoud.  

 Gebruik de volgende procedures om de clientcache te configureren tijdens de handmatige clientinstallatie of nadat de client is geïnstalleerd.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>De clientcache configureren wanneer u clients installeert op basis van een handmatige clientinstallatie  

Voer de opdracht CCMSetup.exe uit vanaf de installatiebronlocatie en geef de volgende eigenschappen op, indien vereist (gescheiden door spaties):  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Voor versie 1606, gebruikt u de cache voor grootte-instellingen beschikbaar zijn in **clientinstellingen** in de Configuration Manager-console in plaats van SMSCACHESIZE. Zie voor meer informatie [clientcache-instellingen](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

Zie voor meer informatie over het gebruik van deze opdrachtregeleigenschappen voor CCMSetup.exe [over clientinstallatie-eigenschappen](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>De clientcache configureren wanneer u clients installeert op basis van een push-clientinstallatie  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de gewenste website, en klik op de **Start** tabblad, in de **instellingen** groep, kiest u **clientinstallatie-instellingen** > **installatie-eigenschappen tabblad**.  

5.  Geef de volgende eigenschappen, gescheiden door spaties:  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Voor versie 1606, gebruikt u de cache voor grootte-instellingen beschikbaar zijn in **clientinstellingen** in de Configuration Manager-console in plaats van SMSCACHESIZE. Zie voor meer informatie [clientcache-instellingen](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

       Zie voor meer informatie over het gebruik van deze opdrachtregeleigenschappen voor CCMSetup.exe [over clientinstallatie-eigenschappen](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>De clientcachemap configureren op de clientcomputer  

1.  Navigeer op de clientcomputer naar **Configuration Manager** in het Configuratiescherm en dubbelklik om de eigenschappen te openen.  

2.  Op de **Cache** tabblad Eigenschappen ruimte en locatie instellen. De standaardlocatie is *%windir%*\ccmcache.  

3.  Voor het verwijderen van de bestanden in de cachemap kiezen **bestanden verwijderen**.  

### <a name="to-configure-client-cache-size-in-client-settings"></a>De client-cachegrootte in clientinstellingen configureren

Pas de grootte van de clientcache zonder opnieuw te installeren van de client door de grootte van de cache configureren in de Configuration Manager-console met clientinstellingen.  

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
 Configuration Manager gebruikt de hardware-id om clients te identificeren die mogelijk zijn gedupliceerd en u te waarschuwen voor conflicterende records. Bijvoorbeeld, als u een computer installeert, de hardware-id zou dezelfde, maar de GUID die wordt gebruikt door Configuration Manager kan worden gewijzigd.  

 Configuration Manager worden automatisch conflicten opgelost met behulp van Windows-verificatie van het computeraccount of een PKI-certificaat van een vertrouwde bron. Echter, wanneer Configuration Manager het conflict van dubbele hardware-id kan niet worden omgezet, een hiërarchie-instelling bepaalt u of de records automatisch samen te voegen of kunt u het gedrag bepalen. Als u besluit dubbele records handmatig te beheren, moet u de conflicterende records in de Configuration Manager-console handmatig oplossen.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>De hiërarchie-instellingen wijzigen voor het beheren van conflicterende records  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites** > **hiërarchie-instellingen**
2.  Op de **goedkeuring van Client en conflicterende Records** tabblad, kiest u **conflicterende records automatisch oplossen**, of **conflicterende records handmatig oplossen**.  

#### <a name="to-manually-resolve-conflicting-records"></a>Conflicterende records handmatig oplossen  

1.  Kies in de Configuration Manager-console **bewaking** > **systeemstatus** > **conflicterende Records**.  

3.  Selecteer een of meer conflicterende records en kies vervolgens **conflicterende Record**.  

4.  Selecteer een van de volgende opties:  

    -   **Samenvoegen** combineren van de nieuwe record met de bestaande clientrecord.  

    -   **Nieuw** : maak een nieuwe record voor de conflicterende clientrecord.  

    -   **Blokkeren** : maak een nieuwe record voor de conflicterende clientrecord, maar markeer deze als geblokkeerd.  

## <a name="manage-duplicate-hardware-identifiers"></a>Dubbele hardware-id's beheren
Met een lijst van hardware-id's die Configuration Manager worden genegeerd voor PXE opstarten en clientregistratie, kunt u twee veelvoorkomende problemen worden opgelost.

1. Veel nieuwe apparaten, zoals Surface Pro, 3, beschikken niet over een ingebouwde Ethernet-poort. Technici gebruik een USB-Ethernet-adapter een bekabelde verbinding ten behoeve van de implementatie van besturingssystemen. Deze adapters worden echter vaak vanwege de kosten en algemene bruikbaarheid gedeeld. Omdat het MAC-adres van deze adapter wordt gebruikt om het apparaat hebt geïdentificeerd, wordt hergebruiken van de adapter problematisch zonder extra beheerdersacties weergegeven tussen elke implementatie. Als u wilt gebruiken op de adapter in dit scenario, sluit u het MAC-adres.
2. Terwijl de SMBIOS-kenmerk uniek zijn moet, hebben sommige apparaten van speciale hardware dubbele id's. Deze dubbele id uitsluiten en zijn afhankelijk van de unieke MAC-adres van elk apparaat.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Toevoegen van hardware-id's voor Configuration Manager te negeren  
1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.
2. Op de **Start** tabblad, in de **Sites** groep, kiest u **hiërarchie-instellingen**.
3. Op de **goedkeuring van Client en conflicterende Records** Kies **toevoegen** in de **dubbele hardware-id's** sectie voor het toevoegen van nieuwe hardware-id's.

##  <a name="BKMK_PolicyRetrieval"></a> Ophalen van beleid initiëren voor een Configuration Manager-client  
 Een Windows Configuration Manager-client downloadt het clientbeleid volgens een schema dat u configureert als een clientinstelling. Echter, kunnen er gevallen indien u wenst te bellen op beleid op te halen van de client, bijvoorbeeld voor het oplossen van problemen of testen.  

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

2.  Op de **acties** Kies **ophaal- en evaluatiefase computerbeleid** het computerbeleid te initiëren en klik vervolgens op **nu uitvoeren**.  

4.  Kies **OK** om te bevestigen.  

5.  Herhaal stap 3 en 4 voor eventuele andere vereiste acties, bijvoorbeeld **Ophaal- en evaluatiefase gebruikersbeleid** voor gebruikersclientinstellingen.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>Clientbeleid handmatig starten door script  

1.  Open een teksteditor, zoals Kladblok.  

2.  Kopieer en de volgende voorbeeldcode voor Visual Basic Scripting Edition invoegen in het bestand:  

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
