---
title: Inhoud migreert | Microsoft-documenten
description: "Distributiepunten gebruiken om inhoud te beheren wanneer u gegevens naar een doelhiërarchie van System Center Configuration Manager migreert."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66f7759c-6272-4116-aad7-0d05db1d46cd
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 468673581e0464fab21397c472b76708b8a5438b
ms.openlocfilehash: 25619d91522193178e0415f649ca4b34c94ecc89
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-a-content-deployment-migration-strategy-in-system-center-configuration-manager"></a>Plan de strategie voor een implementatie van inhoud migratie in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Terwijl u actief gegevens naar een doelhiërarchie van System Center Configuration Manager migreert, behouden Configuration Manager-clients in zowel de bron- en Doelhiërarchieën toegang tot inhoud die u in de bronhiërarchie implementeerde. U kunt ook migratie bijwerken of opnieuw toewijzen van distributiepunten van de bronhiërarchie om er distributiepunten in de doelhiërarchie te gebruiken. Wanneer u distributiepunten deelt of opnieuw toewijst, kan deze strategie u helpen om te vermijden dat u inhouden opnieuw implementeert op nieuwe servers in de doelhiërarchie voor de clients die u migreert.  

Hoewel u inhoud opnieuw kunt creëren en verdelen in de doelhiërarchie, kunt u ook de volgende punten gebruiken om deze inhoud te beheren:  

-   Deel distributiepunten in de doelhiërarchie met clients in de doelhiërarchie.  

-   Zelfstandige Configuration Manager 2007-distributiepunten of secundaire Configuration Manager 2007-sites in de bronhiërarchie om er distributiepunten in de doelhiërarchie te upgraden.  

-   Wijs distributiepunten van een System Center Configuration Manager-bronhiërarchie aan een site in de doelhiërarchie.  

Gebruik de volgende secties om u te helpen plannen voor inhoudimplementatie tijdens migratie:  

-   [Distributiepunten delen tussen de bron- en doelhiërarchieën](#About_Shared_DPs_in_Migration)  

-   [Plant u de upgrade van Configuration Manager 2007 gedeelde distributiepunten](#Planning_to_Upgrade_DPs)  

    -   [Het upgradeproces voor distributiepunten](#BKIMK_UpgradeProcess)  

    -   [Plant u de upgrade van secundaire sites van Configuration Manager 2007](#BKMK_UpgradeSS)  

-   [Plan voor System Center Configuration Manager distributiepunten opnieuw toewijzen](#BKMK_ReassignDistPoint)  

    -   [Het opnieuw toewijzen van distributiepunten](#BKMK_ReassignProcess)  

-   [Inhoudseigendom bij het migreren van inhoud](#About_Migrating_Content)  

##  <a name="About_Shared_DPs_in_Migration"></a> Distributiepunten delen tussen de bron- en doelhiërarchieën  
Tijdens migratie kunt u distributiepunten delen van een bronhiërarchie met de doelhiërarchie. U kunt gedeelde distributiepunten gebruiken om inhoud, die u gemigreerd hebt van een bronhiärarchie, onmiddellijk beschikbaar te maken voor klanten in de doelhiërarchie zonder dat u opnieuw inhoud moet creëren, en hem dan verdelen naar nieuwe distributiepunten in de doelhiërarchie. Wanneer clients in de doelhiërarchie inhoud opvragen die geïmplementeerd is naar distributiepunten die u gedeeld hebt, kunnen de distributiepunten als geldige locaties van inhoud aangeboden worden aan de clients.  

 Behalve dat een geldige Inhoudslocatie voor clients in de doelhiërarchie terwijl de migratie van de bronhiërarchie actief blijft, is het mogelijk bijwerken of opnieuw toewijzen van een distributiepunt naar de doelhiërarchie. U kunt de Configuration Manager 2007 gedeelde distributiepunten updaten en System Center 2012 Configuration Manager-gedeelde distributiepunten opnieuw toewijzen. Als u een gedeeld distributiepunt updatet of opnieuw toewijst, wordt het distributiepunt verwijderd van de bronhiërarchie en wordt het een distributiepunt in de doelhiërarchie. Nadat u een gedeeld distributiepunt updatet of opnieuw toewijst, kunt u het distributiepunt in de doelhiërarchie blijven gebruiken nadat de migratie vanaf de bronhiërarchie beëindigd is. Zie voor meer informatie over het bijwerken van een gedeeld distributiepunt [Plan voor de upgrade van Configuration Manager 2007 gedeelde distributiepunten](#Planning_to_Upgrade_DPs). Zie voor meer informatie over hoe u een gedeeld distributiepunt opnieuw toewijst, [opnieuw toewijzen van System Center Configuration Manager distributiepunten wilt](#BKMK_ReassignDistPoint).  

 U kunt ervoor kiezen om distributiepunten te delen vanaf om het even welke bronsite in uw bronhiërarchie. Wanneer u distributiepunten voor een bronsite deelt, worden de onderliggende secundaire sites gedeeld op elk gekwalificeerd distributiepunt op de primaire site en elk van de primaire sites. Om te kwalificeren om een gedeeld distributiepunt, moet u de sitesysteemserver die het distributiepunt host instellen met een volledig gekwalificeerde domeinnaam (FQDN). Distributiepunten die zijn ingesteld met een NetBIOS-naam worden genegeerd.  

> [!TIP]  
>  Configuration Manager 2007 is niet vereist voor het instellen van een FQDN-naam voor de sitesysteemservers.  

Gebruik de volgende informatie om u te helpen bij het plannen van gedeelde distributiepunten:  

-   Distributiepunten die u deelt, moeten voldoen aan de vereisten voor gedeelde distributiepunten. Zie voor meer informatie over deze vereisten [configuraties vereist voor de migratie](../../core/migration/prerequisites-for-migration.md#BKMK_Required_Configurations) in [vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

-   De gedeelde distributiepunt-actie is een instelling die draagt over de hele site, die alle gekwalificeerde distributiepunten delen op een bronsite en op alle rechtstreeks onderliggende, secundaire sites. U kunt geen individuele distributiepunten selecteren voor het delen als u delen van distributiepunten inschakelt.  

-   Clients in de doelhiërarchie kunnen informatie over plaats van inhoud ontvangen voor pakketten die gedistribueerd zijn naar distributiepunten die gedeeld zijn vanaf de doelhiërarchie. Dit omvat vertakkingsdistributiepunten, distributiepunten op Servershares en standaarddistributiepunten voor distributiepunten van een Configuration Manager 2007-bronhiërarchie.  

    > [!WARNING]  
    >  Indien u de bronhiërarchie wijzigt, zijn gedeelde distributiepunten van de originele bronhiërarchie niet langer beschikbaar en kunnen ze niet aangeboden worden als locatie van inhoud voor clients in de doelhiërarchie. Indien u de migratie herconfigureert om de oorspronkelijke bronhiërarchie te gebruiken, worden de voordien gedeelde distributiepunten gedeeld als geldige servers van locatie van inhoud.  

-   Wanneer u een pakket migreert dat gehost is op een gedeeld distributiepunt, moet de versie van het pakket dezelfde blijven in de bron- en doelhiërarchieën. Wanneer een pakketversie niet dezelfde is in de bron- en doelhiërarchie, kunnen clients in de doelhiërarchie deze inhoud niet ophalen van het gedeelde distributiepunt. Daarom moet u, indien u een pakket updatet in de doelhiërarchie, de pakketgegevens opnieuw migreren vóór clients in de doelhiërarchie deze inhoud ophalen van een gedeeld distributiepunt.  

    > [!NOTE]  
    >  Wanneer u details weergeven voor een pakket dat wordt gehost op een gedeeld distributiepunt aanwijst, is het aantal pakketten die weergegeven worden als **gehoste gemigreerde pakketten** op de bronsite **gedeelde distributiepunten** tabblad niet geüpdatet tot de volgende gegevensverzameling-cyclus is voltooid.  

-   U kunt gedeelde distributiepunten en hun kenmerken zien in de **bronhiërarchie** knooppunt van de **beheer** werkruimte in de Configuration Manager-console die verbinding met de doelhiërarchie maakt.  

-   Kunt u een gedeeld distributiepunt van een Configuration Manager 2007-bronhiërarchie om pakketten te hosten voor Microsoft Application Virtualization (App-V). App-V pakketen moeten migreren en geconverteerd worden om te kunnen gebruikt worden door clients in de doelhiërarchie. U kunt echter een gedeeld distributiepunt van een System Center 2012 Configuration Manager of System Center Configuration Manager-bronhiërarchie aan host App-V pakketten voor clients in een doelhiërachie.  

-   Wanneer u een beveiligde distributiepunt van een Configuration Manager 2007-bronhiërarchie deelt, creëert de doelhiërarchie een grensgroep die de beschermde netwerklocaties van dat distributiepunt. U kunt deze grensgroep in de doelhiërarchie niet wijzigen. Echter, als u de informatie in de beschermde grens voor het distributiepunt in de Configuration Manager 2007-bronhiërarchie wijzigt, wordt die wijziging doorgevoerd in de doelhiërarchie nadat de volgende cyclus van verzamelen van gegevens is voltooid.  

    > [!NOTE]  
    >  System Center 2012 Configuration Manager en System Center Configuration Manager-sites het concept gebruiken van voorkeursdistributiepunten in plaats van beschermde distributiepunten. Deze voorwaarde is alleen van toepassing op distributiepunten die gedeeld worden door Configuration Manager 2007-bronsites.  

De in aanmerking komende distributiepunten zijn niet zichtbaar in de Configuration Manager-console voordat u distributiepunten vanaf een bronsite delen. Nadat u distributiepunten deelt, worden enkel de distributiepunten getoond die effectief gedeeld worden.  

Nadat u de distributiepunten hebt gedeeld, kunt u de configuratie van een gedeeld distributiepunt wijzigen in de bronhiërarchie. Wijzigingen die u maakt aan de configuratie van een distributiepunt worden weerspiegeld in de doelhiërarchie na de volgende cyclus van gegevensgaring, Distributiepunten die u updatet om ze in aanmerking te laten komen voor delen, worden automatisch gedeeld, terwijl deze die niet langer in aanmerking komen, niet langer gedeeld worden. U kunt bijvoorbeeld een distributiepunt dat is niet ingesteld met een intranet FQDN en niet initieel niet gedeeld met de doelhiërarchie hebben. Na het instellen van de FQDN voor dat distributiepunt, de volgende cyclus gegevensgaringcyclus deze configuratie en het distributiepunt wordt dan gedeeld met de doelhiërarchie.  

##  <a name="Planning_to_Upgrade_DPs"></a>Plant u de upgrade van Configuration Manager 2007 gedeelde distributiepunten  
Wanneer u van een Configuration Manager 2007-bronhiërarchie migreert, kunt u een gedeeld distributiepunt zodat dit een System Center Configuration Manager-distributiepunt bijwerken. U kunt distributiepunten updaten op primaire en secundaire sites. Het upgradeproces verwijdert het distributiepunt uit de Configuration Manager 2007-hiërarchie en maakt het een sitesysteemserver in de doelhiërarchie. Dit proces kopieert ook de bestaande inhoud die is aangesloten op het distributiepunt naar een nieuwe locatie op de distributiepuntcomputer. Het updateproces wijzigt dan de kopie van de inhoud om de single instance store te creëren voor gebruik met inhoudimplementatie in de doelhiërarchie. Daarom bij de upgrade van een distributiepunt dat er geen gemigreerde inhoud die op de Configuration Manager 2007-distributiepunt gehost werd opnieuw distribueren.  

Wanneer de inhoud wordt door Configuration Manager naar de single instance store, worden de originele broninhoud op de distributiepuntcomputer om schijfruimte vrij door Configuration Manager verwijderd. Configuration Manager gebruikt niet de originele inhoud van de bronlocatie.  

Niet alle Configuration Manager 2007-distributiepunten die u kunt delen, komen in aanmerking voor upgrade naar System Center Configuration Manager. Als u in aanmerking voor upgrade, moet een Configuration Manager 2007-distributiepunt voldoen aan de voorwaarden voor de upgrade. Deze voorwaarden zijn de sitesysteemserver waarop het distributiepunt is geïnstalleerd en wijst u het type van Configuration Manager 2007-distributiepunt dat is geïnstalleerd. U kunt bijvoorbeeld geen enkel type distributiepunt updaten dat geïnstalleerd is op de servercomputer van de primaire site, maar u kunt een standaard distributiepunt updaten dat geïnstalleerd is op de servercomputer van de site op een secundaire site.  

> [!NOTE]  
>  U kunt alleen die Configuration Manager 2007 gedeelde distributiepunten die zich op een computer met de versie van een besturingssysteem dat wordt ondersteund voor distributiepunten in de doelhiërarchie bijwerken. Bijvoorbeeld, maar u een Configuration Manager 2007-distributiepunt dat zich op een computer met Windows Vista delen kunt, upgraden u niet dit gedeelde distributiepunt omdat het besturingssysteem wordt niet ondersteund door System Center Configuration Manager voor gebruik als een distributiepunt.  

De volgende tabel bevat de ondersteunde locaties voor elk type van Configuration Manager 2007-distributiepunt dat u kunt upgraden.  

|Type distributiepunt|Distributiepunt op een sitesysteemcomputer die niet de siteserver is|Distributiepunt op een sitesysteemcomputer die niet de siteserver is en die andere systeemfuncties voor de site host|Distributiepunt op een secundaire siteserver|  
|--------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------|  
|Standaard distributiepunt|Ja|Nee|Ja|  
|Distributiepunt op server deelt<sup>1</sup>|Ja|Nee|Nee|  
|Vertakkingsdistributiepunt|Ja|Nee|Nee|  

 <sup>1</sup> system Center Configuration Manager biedt geen ondersteuning voor bestandsshares op server voor sitesystemen, maar ondersteunt de upgrade van een Configuration Manager 2007-distributiepunt dat zich op een servershare. Wanneer u een upgrade uitvoert van een Configuration Manager 2007-distributiepunt dat zich op een servershare, type van het distributiepunt automatisch geconverteerd naar een server en u moet het station selecteren op de distributiepuntcomputer dat de single instance content store zal opslaan.  

> [!WARNING]  
>  Voordat u een vertakkingsdistributiepunt bijwerkt, moet u de Configuration Manager 2007-clientsoftware verwijderen. Wanneer u een vertakkingsdistributiepunt dat de Configuration Manager 2007-clientsoftware geïnstalleerd heeft bijwerken, wordt de inhoud die eerder was geïmplementeerd op de computer van de computer verwijderd en mislukt de upgrade van het distributiepunt.  

Voor distributiepunten die in aanmerking komen voor een update in de Configuration Manager-console in de **bronhiërarchie** knooppunt, een bronsite en selecteer vervolgens de **gedeelde distributiepunten** tabblad. Distributiepunten die in aanmerking voor upgrade komen, geven **Ja** weer in de kolom **Komt in aanmerking voor upgrade** .  

Bij een upgrade van een distributiepunt dat is geïnstalleerd op een secundaire siteserver van Configuration Manager 2007, wordt de secundaire site verwijdert uit de bronhiërarchie. Hoewel dit scenario een secundaire site-upgrade wordt genoemd, is dit alleen van toepassing op de sitesysteemrol voor distributiepunten. Het resultaat is dat de secundaire site niet wordt bijgewerkt en dat deze in plaats daarvan wordt verwijderd. Hierbij blijft een distributiepunt vanuit de doelhiërarchie is ingesteld op de computer waarop de secundaire siteserver fungeerde. Als u van plan bent het distributiepunt op een secundaire site bijwerken, Zie [plant u de upgrade van secundaire sites van Configuration Manager 2007](#BKMK_UpgradeSS) in dit onderwerp.  

###  <a name="BKIMK_UpgradeProcess"></a> Het upgradeproces voor distributiepunten  
U kunt de Configuration Manager-console gebruiken om bij te werken van Configuration Manager 2007-distributiepunten die u met de doelhiërarchie hebt gedeeld. Wanneer u een gedeeld distributiepunt bijwerkt, wordt het distributiepunt verwijderd van de Configuration Manager 2007-site. Het wordt vervolgens geïnstalleerd als een distributiepunt dat is gekoppeld aan een primaire of secundaire site die u in de doelhiërarchie opgeeft. Het upgradeproces maakt een kopie van de gemigreerde inhoud die op het distributiepunt is opgeslagen en converteert deze kopie vervolgens naar de Single Instance Store voor inhoud. Wanneer een pakket wordt door Configuration Manager naar de single instance store voor inhoud, wordt verwijderd dat pakket uit de SMSPKG-share op de distributiepuntcomputer tenzij het pakket een of meer aankondigingen die zijn ingesteld heeft op **programma uitvoeren vanaf distributiepunt**.  

Als u het distributiepunt bijwerken, Configuration Manager gebruikt de **toegangsaccount bronsite** die is ingesteld voor het verzamelen van gegevens van de SMS-Provider van de bronsite. Hoewel deze account alleen vereist **lezen** machtiging voor siteobjecten voor het verzamelen van gegevens uit de bronsite, moet ook hebben **verwijderen** en **wijzigen** machtiging voor het **Site** klasse voor het distributiepunt van de Configuration Manager 2007-site verwijderen tijdens de upgrade.  

> [!NOTE]  
>  Configuration Manager kan inhoud converteren naar de single instance store op slechts één distributiepunt tegelijk. Wanneer u meerdere distributiepuntupgrades instelt, wordt de distributiepunten in de wachtrij staan voor de upgrade en één voor één verwerkt.  

Voordat u een upgrade van een gedeeld distributiepunt uitvoert, moet u ervoor zorgen dat alle inhoud die voor het distributiepunt is geïmplementeerd, wordt gemigreerd. Inhoud die u niet migreert voordat u een upgrade van het distributiepunt uitvoert, is na de upgrade niet beschikbaar in de doelhiërarchie. Wanneer u een upgrade van een distributiepunt uitvoert, wordt de inhoud in de gemigreerde pakketten geconverteerd naar een indeling die compatibel is met Single Instance Store in de doelhiërarchie.  

Als u een distributiepunt in de Configuration Manager-console bijwerken, moet de systeemserver van de Configuration Manager 2007-site de volgende voorwaarden voldoen:  

-   De configuratie en locatie van het distributiepunt moeten in aanmerking komen voor het uitvoeren van een upgrade.  

-   De distributiepuntcomputer moet over voldoende schijfruimte beschikken voor de inhoud van de Configuration Manager 2007 inhoudsopslag-indeling worden geconverteerd naar de single instance store-indeling. Voor deze conversie is een hoeveelheid beschikbare schijfruimte vereist die gelijk is aan de grootte van het grootste pakket dat op het distributiepunt is opgeslagen.  

-   Op de distributiepuntcomputer moet een besturingssysteemversie worden uitgevoerd die wordt ondersteund als een distributiepunt in de doelhiërarchie.  

    > [!NOTE]  
    >  Wanneer Configuration Manager de geschiktheid van een distributiepunt voor de upgrade controleert, wordt de besturingssysteemversie van de distributiepuntcomputer niet gevalideerd.  

Upgrade van een distributiepunt in de **beheer** werkruimte Vouw **migratie**, vouw de **bronhiërarchie** knooppunt en selecteer de site die de distributie is wijst dat u wilt upgraden. Selecteer vervolgens in het detailvenster op het tabblad **Gedeelde distributiepunten** het distributiepunt waarvoor u een upgrade wilt uitvoeren.  

U kunt controleren of het distributiepunt klaar is voor een upgrade door de status te bekijken in de kolom **Eligible for Reassignment (Kan opnieuw worden toegewezen)** .  Vervolgens op de Configuration Manager consolelint, op de **distributiepunten** tabblad, in de **distributiepunt** selecteren groep **opnieuw toewijzen**. Hiermee opent u een wizard die u gebruikt voor het voltooien van de upgrade van het distributiepunt.  

Wanneer u een upgrade uitvoert voor een gedeeld distributiepunt, moet u het distributiepunt toewijzen aan een primaire of secundaire site van uw keuze in de doelhiërarchie. Na de upgrade van het distributiepunt, beheert u het distributiepunt als een distributiepunt punt in de doelhiërarchie zoals elk ander distributiepunt.  

U kunt de voortgang van de upgrade van een distributiepunt in de Configuration Manager-console door de **migratie van distributiepunt** knooppunt onder de **migratie** knooppunt van de **beheer** werkruimte. U kunt ook informatie weergegeven via het bestand **Migmctrl.log** op de server van de centrale beheersite van de doelhiërarchie of in het bestand **distmgr.log** op de siteserver in de doelhiërarchie die het bijgewerkte distributiepunt beheert.  

> [!NOTE]  
>  Wanneer u een upgrade uitvoert van een distributiepunt naar de doelhiërarchie, wordt system distributiepuntsiterollen verwijderd uit de bronsite Configuration Manager 2007. Pakketten die zijn verzonden naar het distributiepunt worden echter niet bijgewerkt in de Configuration Manager 2007-hiërarchie. In de console Configuration Manager 2007 pakketten die zijn verzonden naar het distributiepunt nog steeds aan de sitesysteemcomputer als een distributiepunt met een **Type** van **onbekende**. Daaropvolgende updates voor het pakket in Configuration Manager 2007 leiden ertoe dat Distribution Manager fouten rapporteert in het bestand distmgr.log voor die site wanneer de site probeert bij te werken van het pakket op een onbekend sitesysteem.  

Als u niet upgraden een gedeeld distributiepunt wilt, kunt u een distributiepunt nog steeds installeren vanuit de doelhiërarchie op een voormalig Configuration Manager 2007-distributiepunt. Voordat u het nieuwe distributiepunt installeert, moet u eerst alle Configuration Manager 2007-sitesysteemrollen van de distributiepuntcomputer verwijderen. Dit omvat de Configuration Manager 2007-site als dit de siteservercomputer. Wanneer u een Configuration Manager 2007-distributiepunt verwijdert, wordt inhoud die is geïmplementeerd op het distributiepunt niet verwijderd van de computer.  

###  <a name="BKMK_UpgradeSS"></a>Plant u de upgrade van secundaire sites van Configuration Manager 2007  
 Wanneer u migratie gebruikt voor het upgraden van een gedeeld distributiepunt dat wordt gehost op een secundaire siteserver van Configuration Manager 2007, wordt het systeem distributiepuntsiterollen voor een distributiepunt in de doelhiërarchie door Configuration Manager bijgewerkt. De secundaire site wordt verwijderd uit de bronhiërarchie. Het resultaat is een System Center Configuration Manager-distributiepunt, maar geen secundaire site.  

 Voor een distributiepunt op de siteservercomputer komt past in aanmerking voor upgrade moet Configuration Manager kan de secundaire site en elk van de sitesysteemrollen op die computer verwijderen. Meestal is ook een gedeeld distributiepunt op een servershare Configuration Manager 2007 in aanmerking voor upgrade. Wanneer er echter sprake is van een servershare op een secundaire siteserver, komen de secundaire site en eventuele gedeelde distributiepunten op de desbetreffende computer niet aanmerking voor het uitvoeren van een upgrade. Dit komt doordat de servershare wordt behandeld als een aanvullend sitesysteemobject wanneer het proces probeert om de secundaire site te verwijderen en dit proces kan dit object niet verwijderen. In dit scenario kunt u een standaarddistributiepunt op de secundaire siteserver inschakelen en vervolgens de inhoud distribueren naar dit standaarddistributiepunt. Dit proces maakt geen gebruik van netwerkbandbreedte en wanneer u klaar bent, u kunt het distributiepunt verwijderen van de servershare, de servershare verwijderen en vervolgens het distributiepunt en de secundaire site bijwerken.  

 Voordat u een gedeeld distributiepunt bijwerkt, controleert u de distributiepuntconfiguratie in Configuration Manager 2007 om te voorkomen dat een upgrade van een distributiepunt op een secundaire site die u wilt nog steeds gebruiken met Configuration Manager 2007. Dit is een goede gewoonte omdat na de upgrade van een gedeeld distributiepunt dat zich op een secundaire siteserver, de sitesysteemserver is verwijderd uit de Configuration Manager 2007-hiërarchie en niet langer beschikbaar voor gebruik met de desbetreffende hiërarchie is. Wanneer de secundaire site wordt verwijderd, worden eventueel resterende distributiepunten op deze secundaire site zwevende distributiepunten. Dit betekent dat ze worden beheerd vanuit de Configuration Manager 2007 niet langer gedeeld en komt in aanmerking voor upgrade.  

> [!WARNING]  
>  Wanneer u gedeelde distributiepunten in de Configuration Manager-console weergeeft, is het niet aangegeven of een gedeeld distributiepunt zich op een externe sitesysteemserver bevindt of op de secundaire siteserver.  

 Wanneer u een secundaire site op een externe netwerklocatie die wordt gebruikt voor het beheren van de implementatie van inhoud op de desbetreffende externe locatie hebt, kunt u overwegen secundaire sites met een gedeeld distributiepunt. Omdat u bandbreedteregeling voor instellen kunt wanneer u inhoud naar een System Center Configuration Manager-distributiepunt distribueert, kunt u vaak een secundaire site bijwerken naar een distributiepunt, het distributiepunt voor bandbreedteregelingen instellen en de installeren van een secundaire site op die netwerklocatie in de doelhiërarchie vermijden.  

 Het proces voor het upgraden van een gedeeld distributiepunt op een secundaire siteserver is hetzelfde als elke andere upgrade van gedeelde distributiepunt. Inhoud wordt gekopieerd en geconverteerd naar de single instance store in gebruik door de doelhiërarchie. Echter bij een upgrade van een gedeeld distributiepunt dat zich op een secundaire siteserver, het upgradeproces het beheerpunt (indien aanwezig) en vervolgens de secundaire site van de server is verwijderd. Het resultaat is dat de secundaire site is verwijderd uit de Configuration Manager 2007-hiërarchie. Configuration Manager gebruikt voor het verwijderen van de secundaire site, het account dat is ingesteld voor het verzamelen van gegevens uit de bronsite.  

 Tijdens de upgrade is een vertraging tussen wanneer de Configuration Manager 2007-secundaire site verwijderd en wordt de wanneer de installatie van het distributiepunt in de doelhiërarchie begint. De gegevensverzameling cyclus bepaalt deze vertraging van maximaal vier uur bedraagt. De vertraging is bedoeld om tijd beschikbaar voor de secundaire site verwijderen voordat u begint met de nieuwe installatie van het distributiepunt.  

 Zie voor meer informatie over het bijwerken van een gedeeld distributiepunt [Plan voor de upgrade van Configuration Manager 2007 gedeelde distributiepunten](#Planning_to_Upgrade_DPs).  

##  <a name="BKMK_ReassignDistPoint"></a>Plan voor System Center Configuration Manager distributiepunten opnieuw toewijzen  
 Wanneer u een ondersteunde versie van System Center 2012 Configuration Manager naar een hiërarchie met dezelfde versie migreert, kunt u een gedeeld distributiepunt van de bronhiërarchie aan een site in de doelhiërarchie toewijzen. Dit is vergelijkbaar met het concept van een upgrade van een Configuration Manager 2007-distributiepunt zodat dit een distributiepunt in de doelhiërarchie. U kunt distributiepunten van primaire en secundaire sites opnieuw toewijzen. De actie van een distributiepunt opnieuw toewijst verwijdert het distributiepunt van de bronhiërarchie en zorgt ervoor dat de computer en de bijbehorende distributiepunt tot een sitesysteemserver van de site die u in de doelhiërarchie selecteert.  

 Wanneer u een distributiepunt opnieuw toewijst, hoeft u gemigreerde inhoud die op het bronsitedistributiepunt werd gehost, niet opnieuw te distribueren. Bovendien, in tegenstelling tot de upgrade van een Configuration Manager 2007-distributiepunt vereist opnieuw toewijzen van een distributiepunt geen extra schijfruimte vrij op de distributiepuntcomputer. Dit komt doordat vanaf System Center 2012 Configuration Manager, distributiepunten de single instance store-indeling voor inhoud gebruiken. De inhoud op de distributiepuntcomputer hoeft niet te worden geconverteerd wanneer het distributiepunt tussen hiërarchieën opnieuw wordt toegewezen.  

 Voor een System Center 2012 Configuration Manager-distributiepunt in aanmerking komen voor opnieuw toewijzen, moet deze voldoet aan de volgende criteria:  

-   Een gedeeld distributiepunt moet op een andere computer dan de siteserver zijn geïnstalleerd.  

-   Een gedeeld distributiepunt mag zich niet op dezelfde locatie bevinden als eventuele aanvullende sitesysteemrollen.  

Voor distributiepunten die in aanmerking komen voor opnieuw toewijzen in de Configuration Manager-console in de **bronhiërarchie** knooppunt, een bronsite en selecteer vervolgens de **gedeelde distributiepunten** tabblad. In aanmerking komende distributiepunten weergeven **Ja** in de **in aanmerking komen voor opnieuw toewijzen** kolom (deze kolom heet **in aanmerking voor Upgrade** voordat System Center 2012 R2 Configuration Manager).  

###  <a name="BKMK_ReassignProcess"></a> Het opnieuw toewijzen van distributiepunten  
 U kunt de Configuration Manager-console opnieuw toewijzen van distributiepunten die u via een actieve doelhiërarchie hebt gedeeld. Wanneer u een gedeeld distributiepunt opnieuw toewijst, wordt het distributiepunt verwijderd van de bronsite en vervolgens geïnstalleerd als een distributiepunt dat is gekoppeld aan een primaire of secundaire site die u in de doelhiërarchie opgeeft.  

 Om het distributiepunt opnieuw toewijst, gebruikt de doelhiërarchie het toegangsaccount bronsite die is ingesteld voor het verzamelen van gegevens van de SMS-Provider van de bronsite. Zie voor meer informatie over vereiste machtigingen en aanvullende vereisten [vereisten voor migratie in System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Meerdere gedeelde distributiepunten op hetzelfde moment migreren
Vanaf versie 1610, kunt u **distributiepunt opnieuw toewijst** gedeelde distributiepunten in de Configuration Manager-proces parallel het opnieuw toewijzen van maximaal 50 hebben op hetzelfde moment. Dit omvat gedeelde distributiepunten van ondersteunde bronsites die worden uitgevoerd:  
- Configuration Manager 2007
- System Center 2012 Configuration Manager
- System Center 2012 R2 Configuration Manager
- System Center Configuration Manager (huidige vertakking)

Als u distributiepunten opnieuw toewijzen, moet elk distributiepunt aanduiden worden bijgewerkt of opnieuw toegewezen. De naam van de actie en de betrokken proces (bijwerken of opnieuw toewijzen), is afhankelijk van welke versie van Configuration Manager de bronsite wordt uitgevoerd. De end-resultaten voor beide acties zijn hetzelfde: het distributiepunt is toegewezen aan een van uw huidige filialen met de bijbehorende inhoud aanwezig.

Voor versie 1610 kan Configuration Manager slechts één distributiepunt tegelijk verwerken. U kunt nu opnieuw toewijzen zo veel distributiepunten als u met de volgende voorbehouden wilt:  
- Hoewel u kunt geen meervoudige selectie distributiepunten opnieuw worden toegewezen, wanneer u in de wachtrij meer dan één staat hebt, worden Configuration Manager verwerkt door ze parallel in plaats van het wachten op een voordat u de volgende start voltooien.  
- Standaard maximaal 50 distributie worden punten parallel verwerkt op een tijdstip. Nadat het opnieuw toewijzen van het eerste distributiepunt is voltooid, wordt Configuration Manager begint met het verwerken van de 51st, enzovoort.  
- Wanneer u de Configuration Manager-SDK, kunt u **SharedDPImportThreadLimit** om het aantal van opnieuw toegewezen distributiepunten die Configuration Manager parallel verwerken kan aan te passen.


##  <a name="About_Migrating_Content"></a>Toewijzen van eigendom van inhoud wanneer u inhoud migreert  
 Wanneer u inhoud voor implementaties migreert, moet u het inhoudsobject toewijzen aan een site in de doelhiërarchie. Deze site wordt vervolgens de eigenaar van de desbetreffende inhoud in de doelhiërarchie. Hoewel de site op het hoogste niveau van uw doelhiërarchie de site die de metagegevens voor inhoud migreert, is de toegewezen site die gebruikmaakt van de oorspronkelijke bronbestanden voor de inhoud via het netwerk.  

 U kunt overwegen om het eigendom van de inhoud over te dragen aan een site in de doelhiërarchie die zich op het netwerk dicht in de buurt van de inhoudslocatie in de bronhiërarchie bevindt om de bandbreedte te minimaliseren die wordt gebruikt wanneer u inhoud migreert. Omdat informatie over de inhoud in de doelhiërarchie globaal wordt gedeeld, is deze beschikbaar op elke site.  

 Hoewel informatie over inhoud via databasereplicatie naar alle sites wordt gedeeld, verwijst inhoud die u toewijst aan een primaire site en vervolgens implementeren voor distributiepunten naar andere primaire sites overdrachten door replicatie op basis van bestanden. Deze overdracht verloopt via de centrale beheersite en vervolgens via de aanvullende primaire site. Door het centraliseren van pakketten die u distribueren naar meerdere primaire sites vóór of tijdens de migratie wilt wanneer u een site als eigenaar van de inhoud toewijst kunt u gegevensoverdrachten via netwerken met een lage bandbreedte reduceren.

