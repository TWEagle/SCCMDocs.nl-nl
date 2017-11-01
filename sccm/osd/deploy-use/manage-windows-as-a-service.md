---
title: 'Windows beheren als een Service '
titleSuffix: Configuration Manager
description: De status van Windows als een Service met Configuration Manager weergeven, onderhoudsplannen om implementatieringen te vormen maken en waarschuwingen weergeven wanneer Windows 10-clients het einde van ondersteuning naderen.
ms.custom: na
ms.date: 03/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da1e687b-28f6-43c4-b14a-ff2b76e60d24
caps.latest.revision: "26"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: e4ebbcec6df0bd5fdf5f94788d00f590d5e38d4d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-windows-as-a-service-using-system-center-configuration-manager"></a>Windows als een service beheren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 In System Center Configuration Manager, u kunt de status van Windows als een Service in uw omgeving weergeven, onderhoudsplannen om implementatieringen te vormen maken en zorg ervoor dat Windows 10 huidige vertakking systemen worden bijgewerkt wanneer er nieuwe builds worden vrijgegeven en waarschuwingen weergeven wanneer Windows 10-clients het einde van de ondersteuningsperiode voor hun build van Current Branch (CB) of Current Branch for Business (CBB) naderen.  

 Zie  [Windows 10-onderhoudsopties voor updates en upgrades](https://technet.microsoft.com/library/mt598226\(v=vs.85\).aspx)voor meer informatie over Windows 10-onderhoudsopties.  

 Gebruik de volgende secties voor het beheren van Windows als een service.

##  <a name="BKMK_Prerequisites"></a> Vereisten  
 U kunt als volgt de gegevens in het Windows 10-onderhoudsdashboard weergeven:  

-   Windows 10-computers moeten Configuration Manager software-updates met Windows Server Update Services (WSUS) gebruiken voor het beheer van software-updates. Wanneer computers gebruikmaken van Windows Update for Business (of Windows Insiders) voor het beheer van software-updates, wordt de computer niet geëvalueerd in de Windows 10-onderhoudsplannen. Zie [Integratie met Windows Update voor bedrijven in Windows 10](../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md) voor meer informatie.  

-   WSUS 4.0 met de [hotfix 3095113](https://support.microsoft.com/kb/3095113) moet zijn geïnstalleerd op de software-updatepunten en siteservers. Hiermee voegt u de software-updateclassificatie **Upgrades** toe. Zie voor meer informatie [vereisten voor software-updates](../../sum/plan-design/prerequisites-for-software-updates.md).  

-   WSUS 4.0 met de [hotfix 3159706](https://support.microsoft.com/kb/3159706) moet worden geïnstalleerd op uw software-updatepunten en siteservers om computers te upgraden naar Windows 10 Verjaardag Update, evenals voor subsequence versies. Er zijn handmatige stappen wordt beschreven in het ondersteuningsartikel die u uitvoeren moet om deze hotfix te installeren. Zie voor meer informatie de [Enterprise Mobility and Security-Blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/05/update-your-configmgr-1606-sup-servers-to-deploy-the-windows-10-anniversary-update/).

-   Schakel heartbeat-detectie in. De gegevens die worden weergegeven in het Windows 10-onderhoudsdashboard worden gevonden door middel van detectie. Zie [Heartbeat-detectie configureren](../../core/servers/deploy/configure/configure-discovery-methods.md#BKMK_ConfigHBDisc) voor meer informatie.  

     De volgende vertakking- en buildgegevens voor Windows 10 worden gedetecteerd en opgeslagen in de volgende kenmerken:  

    -   **Vertakkingsstatus van besturingssysteem**: Hiermee geeft u de vertakking van het besturingssysteem. Bijvoorbeeld: **0** CB = (geen upgrades niet uitstellen), **1** CBB = (uitstelt upgrades), **2** = Long Term Servicing Branch (LTSB)

    -   **Besturingssysteem Build**: De build besturingssysteem opgegeven. Bijvoorbeeld: **10.0.10240** (RTM) of **10.0.10586** (versie 1511)  

-   Het serviceaansluitpunt moet zijn geïnstalleerd en geconfigureerd voor de modus **Permanente onlineverbinding** om de gegevens te bekijken op het Windows 10-onderhoudsdashboard. Wanneer u in de offlinemodus bevindt bent, wordt u op het dashboard niet zien totdat u Configuration Manager-onderhoudsupdates ontvangt.   
     Zie voor meer informatie [over het service connection point](../../core/servers/deploy/configure/about-the-service-connection-point.md).  


-   Op de computer waarop de Configuration Manager-console moet Internet Explorer 9 of hoger worden geïnstalleerd.  

-   Software-updates moeten zijn geconfigureerd en gesynchroniseerd. U moet selecteren de **Upgrades** classificatie en software-updates synchroniseren voordat eventuele functie-upgrades voor Windows 10 beschikbaar in de Configuration Manager-console is. Zie voor meer informatie [voorbereiden voor software-updates management](../../sum/get-started/prepare-for-software-updates-management.md).  

##  <a name="BKMK_ServicingDashboard"></a> Windows 10-onderhoudsdashboard  
 In het Windows 10-onderhoudsdashboard vindt u onder andere informatie over Windows 10-computers in uw omgeving, actieve onderhoudsplannen en informatie over de compatibiliteit. Voor de weergave van de gegevens in het Windows 10-onderhoudsdashboard moet het serviceaansluitpunt zijn geïnstalleerd. Het dashboard bevat de volgende tegels:  

-   **Tegel Windows 10-gebruik**:  Bevat een verdeling van openbare builds van Windows 10. Windows Insiders-builds worden vermeld als **Overig** , evenals de builds die nog niet bekend zijn bij uw site. Er worden door het serviceaansluitpunt metagegevens met informatie over de Windows-builds gedownload en deze gegevens worden vervolgens vergeleken met de detectiegegevens.  

-   **Tegel Windows 10-ringen**:  Bevat een verdeling van Windows 10 op vertakking en gereedheidsstatus. Het segment LTSB worden alle LTSB-versies (terwijl de eerste tegel de specifieke versie. Bijvoorbeeld, Windows 10 LTSB 2015. Het segment **Release Ready** komt overeen met CB en het segment **Business ready** met CBB.  

-   **Tegel Service-Plan maken**:   Biedt een snelle manier om een onderhoudsplan te maken. U specificeert de naam, de verzameling (alleen de tien grootste verzamelingen worden weergegeven, waarbij de kleinste het eerst wordt vermeld), het implementatiepakket (alleen de tien meest recent gewijzigde pakketten worden weergegeven) en de gereedheidsstatus. Voor de overige instellingen worden de standaardwaarden gebruikt. Klik op **Geavanceerde instellingen** om de wizard Onderhoudsplan maken te starten. In de wizard kunt u alle instellingen van het onderhoudsplan configureren.  

-   **Tegel verlopen**: Geeft het percentage van apparaten met een versie van Windows 10 die voorbij het einde van de levensduur. Configuration Manager bepaalt het percentage van de metagegevens die het serviceverbindingspunt gedownload en die met de detectiegegevens vergelijkt. Een build waarvan de levensduur is verstreken, ontvangt geen maandelijkse cumulatieve updates meer, zoals beveiligingsupdates. De computers in deze categorie moeten worden bijgewerkt naar de volgende buildversie. Configuration Manager rondt af naar boven op het dichtstbijzijnde gehele getal. Als u bijvoorbeeld over 10.000 computers beschikt waarvan slechts één met een verlopen build, wordt door de tegel 1% weergegeven.  

-   **Tegel verloopt binnenkort**: Geeft het percentage van computers met een versie die in de buurt levensduur (binnen ongeveer vier maanden), vergelijkbaar met de **verlopen** tegel. Configuration Manager rondt af naar boven op het dichtstbijzijnde gehele getal.  

-   **Tegel waarschuwingen**: Bevat actieve waarschuwingen.  

-   **Tegel controle van onderhoudsplannen**: Beeldscherm onderhoudsplannen die u hebt gemaakt en een grafiek zien van de compatibiliteit voor elk. U kunt zo snel zien wat de huidige status van de onderhoudsplanimplementaties is. Als een eerdere implementatiering voldoet aan de verwachtingen voor compatibiliteit, kunt u een later onderhoudsplan (implementatiering) selecteren en op **Nu implementeren** klikken in plaats van te wachten op de automatische activering van de onderhoudsplanregels.  

-   De **tegel Windows 10-Builds**:  Weergave is een vaste afbeelding tijd regel waarmee u die een overzicht van het Windows 10-builds die momenteel zijn vrijgegeven en kunt u wanneer een algemeen beeld van builds verandert in verschillende statussen.  

> [!IMPORTANT]  
>  De gegevens die in het Windows 10-onderhoudsdashboard worden weergegeven (zoals de ondersteuningslevenscyclus voor versies van Windows 10) dienen uw gemak en zijn alleen voor intern gebruik in uw bedrijf bestemd. U moet niet alleen afgaan op deze gegevens wanneer u de compatibiliteit van updates controleert. Controleer de juistheid van de gegevens die wordt weergegeven.  

## <a name="servicing-plan-workflow"></a>Werkstroom voor onderhoudsplannen  
 Windows 10-onderhoudsplannen in Configuration Manager zijn veel vergelijkbaar met regels voor automatische implementatie voor software-updates. U maakt een onderhoudsplan met de volgende criteria die Configuration Manager evalueert:  

-   **Classificatie upgrades**: Alleen de updates die in de **Upgrades** classificatie worden geëvalueerd.  

-   **Gereedheidsstatus**: De gereedheidsstatus die is gedefinieerd in het onderhoudsplan wordt vergeleken met de gereedheidsstatus voor de upgrade. De metagegevens voor de upgrade worden opgehaald wanneer het serviceaansluitpunt controleert op updates.  

-   **Uitsteltermijn**: Het aantal dagen dat u opgeeft voor **hoeveel dagen na de publicatie van een nieuwe upgrade door Microsoft wilt u dat moet worden gewacht voordat de implementatie in uw omgeving** in het onderhoudsplan. Configuration Manager beoordeelt of een upgrade opgenomen in de implementatie als de huidige datum na de releasedatum plus het aantal dagen valt.  

 Wanneer een upgrade voldoet aan de criteria, voegt het onderhoudsplan de upgrade toe aan het implementatiepakket, distribueert dit het pakket naar de distributiepunten en implementeert het de upgrade voor de verzameling op basis van de instellingen die u in het onderhoudsplan configureert.  U kunt de implementaties controleren in de tegel Controle van onderhoudsplannen in het Windows 10-onderhoudsdashboard. Zie voor meer informatie [software-updates controleren](../../sum/deploy-use/monitor-software-updates.md).  

##  <a name="BKMK_ServicingPlan"></a> Windows 10-onderhoudsplan  
 Wanneer u Windows 10 CB implementeert, kunt u een of meer onderhoudsplannen maken voor het definiëren van de implementatieringen die u in uw omgeving wilt opnemen. U kunt deze vervolgens in het Windows 10-onderhoudsdashboard controleren.   
Voor onderhoudsplannen wordt uitsluitend gebruikgemaakt van de software-updateclassificatie **Upgrades** , en niet van de cumulatieve updates voor Windows 10. Voor die updates moet u nog steeds een implementatie uitvoeren met de werkstroom voor software-updates.  Het gebruik voor de eindgebruiker bij een onderhoudsplan is hetzelfde als bij de software-updates, waaronder de instellingen die u in het onderhoudsplan configureert.  

> [!NOTE]  
>  U kunt een takenreeks gebruiken om een upgrade voor elk Windows 10-build te implementeren, maar het vereist meer handmatig werk. U moet de bijgewerkte bronbestanden importeren als een upgradepakket voor besturingssystemen en vervolgens de takenreeks maken en implementeren voor de betreffende verzameling computers. Een takenreeks bevat echter aanvullende aangepaste opties, zoals de acties voorafgaand aan de implementatie en de acties na afloop van de implementatie.  

 U kunt een basisonderhoudsplan maken in het Windows 10 -onderhoudsdashboard. Nadat u de naam, de verzameling (alleen de tien grootste verzamelingen worden weergegeven door grootte, kleinste eerst), opgegeven implementatiepakket (alleen weergegeven die de tien meest recent pakketten gewijzigde zijn) en de gereedheid van de status, Configuration Manager het onderhoudsplan gemaakt met de standaardwaarden voor de overige instellingen. U kunt ook de wizard Onderhoudsplan maken starten om alle instellingen te configureren. U kunt aan de hand van de volgende procedure een onderhoudsplan maken met de wizard Onderhoudsplan maken.  

> [!NOTE]  
>  Vanaf versie 1602 van Configuration Manager, kunt u het gedrag voor implementaties met een hoog risico beheren. Een implementatie met een hoog risico is een implementatie die automatisch wordt geïnstalleerd en de potentie heeft om ongewenste resultaten te veroorzaken. Een takenreeks met het doel **Vereist** en waarmee Windows 10 wordt geïmplementeerd, wordt beschouwd als een implementatie met een hoog risico. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

#### <a name="to-create-a-windows-10-servicing-plan"></a>Een Windows 10-onderhoudsplan maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte Softwarebibliotheek **Onderhoud voor Windows 10**uit en klik vervolgens op **Onderhoudsplannen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Onderhoudsplan maken**. De wizard Onderhoudsplan maken wordt geopend.  

4.  Configureer de volgende instellingen op de pagina **Algemeen** :  

    -   **Naam**: Geef de naam voor het onderhoudsplan. De naam moet uniek zijn, het doel van de regel beschrijven en onderscheiden van andere gebruikers in de Configuration Manager-site.  

    -   **Beschrijving**: Geef een beschrijving voor het onderhoudsplan. De beschrijving moet bieden een overzicht van het onderhoudsplan en eventuele andere relevante informatie die helpt om te identificeren en te onderscheiden van het plan van andere implementaties in de Configuration Manager-site. Het beschrijvingsveld is optioneel en kent een limiet van 256 tekens. Het veld is standaard leeg.  

5.  Configureer op de pagina Onderhoudsplan de volgende instellingen:  

    -   **Doelverzameling**: Hiermee geeft u de doelverzameling op die moet worden gebruikt voor het onderhoudsplan. Leden van de verzameling ontvangen de Windows 10-updates die in het onderhoudsplan zijn gedefinieerd.  

        > [!NOTE]  
        >  Vanaf versie 1602 van Configuration Manager, wanneer u een implementatie met hoog risico, zoals een onderhoudsplan, implementeert de **verzameling selecteren** venster geeft alleen de aangepaste verzamelingen die voldoen aan de implementatie van de verificatie-instellingen die zijn geconfigureerd in de site eigenschappen.
        >    
        > Implementaties met een hoog risico zijn altijd beperkt tot aangepaste verzamelingen, verzamelingen die u zelf maakt en de ingebouwde verzameling **Onbekende computers** . Wanneer u een implementatie met een hoog risico maakt, kunt u geen ingebouwde verzameling selecteren, zoals **Alle systemen**. Schakel het selectievakje **lid zamelingen verbergen groter is dan de minimale configuratiegrootte** voor een overzicht van alle aangepaste verzamelingen die minder clients dan het geconfigureerde maximum bevatten. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >  
        > De instellingen voor het verifiëren van de implementatie zijn gebaseerd op het huidige lidmaatschap van de verzameling. Nadat u een onderhoudsplan hebt geïmplementeerd, wordt het lidmaatschap van de verzameling niet opnieuw geëvalueerd voor de instellingen van de implementatie met een hoog risico.  
        >  
        > Bijvoorbeeld, Stel dat u **standaardgrootte** en 100 en de **maximumgrootte** tot en met 1000. Wanneer u een implementatie met een hoog risico maakt, worden in het venster **Verzameling selecteren** alleen verzamelingen weergegeven die minder dan 100 clients bevatten. Als u het selectievakje de **lid zamelingen verbergen groter is dan de minimale configuratiegrootte** uitschakelt, het venster verzamelingen weergegeven die minder dan 1000 clients bevatten.  
        >
        > Wanneer u een verzameling met een siterol selecteert, geldt het volgende:    
        >   
        >    - Als de verzameling een sitesysteemserver bevat en u in de instellingen voor het verifiëren van de implementatie opgeeft dat verzamelingen met sitesysteemservers moeten worden geblokkeerd, wordt er een fout weergegeven en kunt u niet doorgaan.    
        >    - Als de verzameling een sitesysteemserver bevat en u in de instellingen voor het verifiëren van de implementatie opgeeft dat u moet worden gewaarschuwd als verzamelingen sitesysteemservers bevatten, de verzameling de standaardgrootte overschrijdt of als de verzameling een server bevat, wordt er in de wizard Software implementeren een waarschuwing voor een hoog risico weergegeven. U moet akkoord gaan met het maken van een implementatie met een hoog risico en er wordt een controlestatusbericht gegenereerd.  

6.  Configureer op de pagina Implementatiering de volgende instellingen:  

    -   **Geef de Windows-gereedheidsstatus waarop dit onderhoudsplan van toepassing moet zijn**: Selecteer vervolgens een van de volgende opties:  

        -   **Release Ready (Current Branch)**: Functie-updates zijn in het servicemodel CB beschikbaar zodra ze door Microsoft worden uitgegeven.

        -   **Bedrijfsgereed (huidige vertakking voor bedrijven)**: De CBB onderhoud vertakking wordt doorgaans gebruikt voor brede implementatie. Windows 10-clients in de servicing branch CBB ontvangen dezelfde build van Windows 10 die ook in de categorie CB servicing branch gebruikt, alleen op een later tijdstip.

        Zie voor meer informatie over onderhoud vertakkingen en welke opties wordt aanbevolen voor u, [vertakkingen onderhoud](https://technet.microsoft.com/itpro/windows/manage/waas-overview#servicing-branches).

    -   **Het aantal dagen dat u wilt wachten met het implementeren van een nieuwe upgrade nadat Microsoft die beschikbaar heeft gesteld**: Configuration Manager beoordeelt of een upgrade opgenomen in de implementatie als de huidige datum valt na de releasedatum plus het aantal dagen dat u voor deze instelling configureert.

    -   Voorafgaand aan versie 1602 van Configuration Manager, klikt u op **Preview** om de Windows 10-updates die zijn gekoppeld aan de gereedheidsstatus weer te geven.  

    Zie voor meer informatie [vertakkingen onderhoud](https://technet.microsoft.com/itpro/windows/manage/waas-overview#servicing-branches).
7.  Configureer de zoekcriteria om te filteren op upgrades die worden toegevoegd aan het serviceplan vanaf versie 1602 van Configuration Manager is op de pagina Upgrades. Alleen de upgrades die voldoen aan de opgegeven criteria worden aan de gekoppelde implementatie toegevoegd.  

     Klik op **Voorbeeld** om de upgrades weer te geven die voldoen aan de opgegeven criteria.  

8.  Configureer de volgende instellingen op de pagina Implementatieplanning:  

    -   **Evaluatie van planning**: Geef aan of Configuration Manager de beschikbare tijd en de tijdstippen voor de installatiedeadline evalueert op basis van UTC of van de lokale tijd van de computer waarop de Configuration Manager-console.  

        > [!NOTE]  
        >  Als u lokale tijd selecteert en selecteer vervolgens **zo snel mogelijk** voor de **tijd Software beschikbaar** of **installatiedeadline**, de huidige tijd op de computer die de Configuration Manager-console wordt gebruikt om te evalueren wanneer updates beschikbaar zijn of wanneer ze worden geïnstalleerd op een client wordt uitgevoerd. Als de client zich in een andere tijdzone bevindt, worden deze acties uitgevoerd wanneer de tijd van de client de evaluatietijd heeft bereikt.  

    -   **Tijd software beschikbaar**: Selecteer een van de volgende instellingen op te geven wanneer de software-updates beschikbaar voor clients zijn:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de softwareupdates die zijn opgenomen in de implementatie beschikbaar voor de clientcomputers zo snel mogelijk. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid en kunnen de updates verkrijgen die beschikbaar zijn voor installatie.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de softwareupdates die zijn opgenomen in de implementatie op een specifieke datum en tijd beschikbaar is voor de clientcomputers. Wanneer u de implementatie met deze instelling is ingeschakeld maakt, wordt in Configuration Manager het clientbeleid bijgewerkt. Clients detecteren de implementatie vervolgens gedurende de volgende pollingcyclus van het clientbeleid. De software-updates in de implementatie zijn echter pas na de geconfigureerde datum en het geconfigureerde tijdstip beschikbaar voor installatie.  

    -   **Installatiedeadline**: Selecteer een van de volgende instellingen om op te geven van de installatiedeadline voor de software-updates in de implementatie:  

        -   **Zo spoedig mogelijk**: Selecteer deze instelling om de software-updates in de implementatie zo spoedig mogelijk automatisch worden geïnstalleerd.  

        -   **Specifiek tijdstip**: Selecteer deze instelling om de software-updates in de implementatie op een specifieke datum en tijd automatisch worden geïnstalleerd. Configuration Manager bepaalt de deadline voor het installeren van software-updates door het geconfigureerde **specifiek tijdstip** interval voor de **tijd Software beschikbaar**.  

            > [!NOTE]  
            >  Het daadwerkelijke tijdstip van de installatiedeadline is het weergegeven deadlinetijdstip plus een willekeurige hoeveelheid die maximaal twee uur is. Hierdoor worden de mogelijk gevolgen voorkomen wanneer de updates in de implementatie gelijktijdig op alle clientcomputers in de doelverzameling zouden worden geïnstalleerd.  
            >   
            >  U kunt de **Computeragent** -clientinstelling **Willekeurig toepassen van deadline uitschakelen** configureren om de willekeurige installaties voor de vereiste updates uit te schakelen. Zie [Computeragent](../../core/clients/deploy/about-client-settings.md#computer-agent) voor meer informatie.  

9. Configureer de volgende instellingen op de pagina Gebruikerservaring:  

    -   **Meldingen voor gebruikers**: Geef op of meldingen van de updates weergeven in Software Center op de clientcomputer op de geconfigureerde **tijd Software beschikbaar** en of meldingen voor gebruikers weergegeven op de clientcomputers.  

    -   **Deadlinegedrag**: Geef het gedrag op dat moet worden vertoond als de deadline voor implementatie van de update wordt bereikt. Geef op of de updates in de implementatie moeten worden geïnstalleerd. Geef ook op of het systeem na het installeren van de updates opnieuw moet worden opgestart, ongeacht het geconfigureerde onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Gedrag voor opnieuw opstarten apparaat**: Geef op of onderdrukken van opnieuw opstarten van servers en werkstations nadat updates zijn geïnstalleerd en opnieuw opstarten is vereist om de installatie te voltooien.  

    -   **Schrijffilters voor Windows Embedded-apparaten**: Wanneer u updates voor Windows Embedded-apparaten waarvoor schrijffilters ingeschakeld implementeert zijn, kunt u opgeven om de update installeren op een tijdelijke overlay en de wijzigingen later of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

        > [!NOTE]  
        >  Wanneer u een update implementeert op een Windows Embedded-apparaat, moet u nagaan of het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster.  

10. Selecteer op de pagina Implementatiepakket een bestaand implementatiepakket of configureer de volgende instellingen voor het maken van een nieuw implementatiepakket:  

    1.  **Naam**: Geef de naam van het implementatiepakket. Dit moet een unieke naam zijn die de pakketinhoud beschrijft. Er kunnen maximaal 50 tekens worden ingevoerd.  

    2.  **Beschrijving**: Geef een beschrijving die informatie over het implementatiepakket biedt. De beschrijving mag niet langer zijn dan 127 tekens.  

    3.  **Pakketbron**: Hiermee geeft u de locatie van de bronbestanden voor software-update.  Typ een netwerkpad voor de bronlocatie, zoals **\\\\server\sharenaam\pad**, of klik op **Bladeren** en ga naar de netwerklocatie. U moet een gedeelde map maken voor de bronbestanden van het installatiepakket voordat u doorgaat naar de volgende pagina.  

        > [!NOTE]  
        >  De bronlocatie van het installatiepakket die u opgeeft, mag niet door een ander software-installatiepakket worden gebruikt.  

        > [!IMPORTANT]  
        >  Het computeraccount van de SMS-provider en de gebruiker die de wizard uitvoert voor het downloaden van de software-updates, moeten over NTFS-machtigingen voor **schrijven** op de downloadlocatie beschikken. U moet de toegang tot de downloadlocatie zorgvuldig beperken om het risico op kwaadwillenden die met bronbestanden van de software-update knoeien, te reduceren.  

        > [!IMPORTANT]  
        >  U kunt de pakketbronlocatie in de eigenschappen van het installatiepakket wijzigen nadat Configuration Manager het implementatiepakket maakt. Als u dit doet, moet u echter eerst de inhoud van de oorspronkelijke pakketbron kopiëren naar de nieuwe pakketbronlocatie.  

    4.  **Prioriteit voor verzenden**: Geef de prioriteit voor verzenden voor het implementatiepakket. Configuration Manager gebruikt de prioriteit voor verzenden voor het implementatiepakket wanneer het pakket naar distributiepunten wordt verzonden. Installatiepakketten worden in volgorde van prioriteit verzonden: Hoog, Gemiddeld of laag. Pakketten met een identieke prioriteit worden verzonden in de volgorde waarin deze zijn gemaakt. Als er geen achterstand is, wordt het pakket onmiddellijk verwerkt, ongeacht de prioriteit van het pakket.  

11. Geef op de pagina Distributiepunten de distributiepunten of distributiepuntgroepen op die als host zullen fungeren voor de updatebestanden. Zie voor meer informatie over distributiepunten [een distributiepunt configureren](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_configs).

    > [!NOTE]  
    >  Deze pagina is alleen beschikbaar wanneer u een nieuw implementatiepakket voor software-updates maakt.  

12. Geef op de pagina Downloadlocatie op of de updatebestanden moeten worden gedownload vanaf internet of vanaf uw lokale netwerk. Configureer de volgende instellingen:  

    -   **Software-updates downloaden vanaf Internet**: Selecteer deze instelling om de updates downloaden vanaf een opgegeven locatie op Internet. Deze instelling is standaard ingeschakeld.  

    -   **Software-updates downloaden vanaf een locatie op het lokale netwerk**: Selecteer deze instelling om de updates downloaden vanaf een lokale map of gedeelde map. Deze instelling is nuttig wanneer de computer waarop de wizard wordt uitgevoerd, geen toegang tot internet heeft. Computers met internettoegang kunnen de updates in eerste instantie downloaden en deze opslaan op een locatie in het lokale netwerk die toegankelijk is vanaf de computer waarop de wizard wordt uitgevoerd.  

13. Selecteer op de pagina Taal selecteren de talen waarvoor de geselecteerde updates worden gedownload. De updates worden alleen gedownload als deze beschikbaar zijn in de geselecteerde talen. Updates die niet aan een specifieke taal zijn gebonden, worden altijd gedownload. De wizard selecteert standaard de talen die u hebt geconfigureerd in de eigenschappen van het software-updatepunt. Er moet ten minste één taal worden geselecteerd voordat u doorgaat naar de volgende pagina. Wanneer u alleen talen selecteert die niet door een update worden ondersteund, mislukt het downloaden van de update.  

14. Controleer op de overzichtspagina de instellingen en klik vervolgens op **Volgende** om het onderhoudsplan te maken.  

 Nadat u de wizard hebt voltooid, wordt het onderhoudsplan uitgevoerd. Deze voegt de updates toe die voldoen aan de opgegeven criteria voor een software-updategroep, downloadt de updates naar de inhoudsbibliotheek op de siteserver, distribueert de updates naar de geconfigureerde distributiepunten en implementeert de software-updategroep voor clients in de doelverzameling.  

##  <a name="BKMK_ModifyServicingPlan"></a> Een onderhoudsplan wijzigen  
Nadat u een basisonderhoudsplan van het Windows 10 maken-onderhoudsdashboard of moet u de instellingen voor een bestaand onderhoudsplan te wijzigen, kunt u naar de eigenschappen voor het onderhoudsplan gaan.

> [!NOTE]
> U kunt instellingen configureren in de eigenschappen voor het onderhoudsplan die niet beschikbaar in de wizard bij het maken van het onderhoudsplan. De wizard gebruikt de standaardinstellingen voor de instellingen voor het volgende:-instellingen, implementatie-instellingen en waarschuwingen te downloaden.  

Gebruik de volgende procedure om de eigenschappen van een onderhoudsplan te wijzigen.  

#### <a name="to-modify-the-properties-of-a-servicing-plan"></a>De eigenschappen van een onderhoudsplan wijzigen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte Softwarebibliotheek **Onderhoud voor Windows 10**uit, klik op **Onderhoudsplannen**en selecteer vervolgens het onderhoudsplan dat u wilt wijzigen.  

3.  Klik op het tabblad **Start** op **Eigenschappen** om de eigenschappen van het geselecteerde onderhoudsplan weer te geven.

    De volgende instellingen zijn beschikbaar in de servicing plan-eigenschappen die niet zijn geconfigureerd in de wizard:

    **Implementatie-instellingen**: Configureer de volgende instellingen op het tabblad implementatie-instellingen:  

    -   **Type implementatie**: Geef het implementatietype voor de implementatie van de software-update. Selecteer **Vereist** om een verplichte software-update-implementatie te maken waarin de software-updates voor een configureerde installatiedeadline automatisch op de clients worden geïnstalleerd. Selecteer **Beschikbaar** om een optionele software-update-implementatie te maken die voor gebruikers beschikbaar is in Software Center.  

        > [!IMPORTANT]  
        >  Nadat u de software update-implementatie hebt gemaakt, kan het type implementatie niet meer worden gewijzigd.  

        > [!NOTE]  
        >  Een software-updategroep die wordt geïmplementeerd als **Vereist** , wordt gedownload op de achtergrond waarbij BITS-instellingen worden gehandhaafd, indien geconfigureerd.  
        > Software-updategroepen die worden geïmplementeerd als **Beschikbaar** , worden echter gedownload op de voorgrond waarbij BITS-instellingen worden genegeerd.  

    -   **Wake-on-LAN gebruiken om clients voor vereiste implementaties te laten ontwaken**: Geef op of Wake On LAN tegen de deadline voor het verzenden van ontwaakpakketten naar computers waarvoor een of meer software-updates in de implementatie. Computers die zich op het tijdstip van de installatiedeadline in de slaapstandmodus bevinden, worden uit deze stand gehaald, zodat de installatie van de software-update kan worden gestart. Clients die zich in de slaapstandmodus bevinden en geen software-updates nodig hebben, worden niet gestart. Deze instelling is standaard uitgeschakeld en is alleen beschikbaar wanneer **Type implementatie** is ingesteld op **Vereist**.  

        > [!WARNING]  
        >  Voordat u deze optie kunt gebruiken, moeten computers en netwerken zijn geconfigureerd voor Wake On LAN.  

    -   **Detailniveau**: Geef het detailniveau voor de statusberichten die zijn gerapporteerd door clientcomputers.  

    **Downloadinstellingen**: Configureer op het tabblad instellingen voor downloaden van de volgende instellingen:  

    - Geef op of de client de software-updates moet downloaden en installeren wanneer een client is verbonden met een langzaam netwerk of wanneer deze gebruikmaakt van een locatie terugvalinhoudlocatie.  

    - Geef op of de client de software-updates moet downloaden en installeren vanaf een terugvaldistributiepunt wanneer de inhoud voor de software-updates niet beschikbaar is op een voorkeursdistributiepunt.  

    -   **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Geef op of het gebruik van BranchCache voor inhouddownloads inschakelen. Zie voor meer informatie over BranchCache [basisconcepten voor inhoudsbeheer](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    -   Geef op of hebben clients downloaden van software-updates vanaf Microsoft Update als software-updates niet beschikbaar zijn op distributiepunten.
        > [!IMPORTANT]
        > Gebruik deze instelling niet voor onderhoud van Windows 10-updates. Configuration Manager (ten minste tot en met versie 1610) mislukt het onderhoud van Windows 10-updates te downloaden vanaf Microsoft Update.

    -   Geef op of clients mogen downloaden na een installatiedeadline wanneer deze internetverbindingen met een datalimiet gebruiken. Internetproviders brengen soms de hoeveelheid gegevens die u verzendt en ontvangt in rekening wanneer u gebruikmaakt van een internetverbinding naar gebruik.   

    **Waarschuwingen**: Op het tabblad waarschuwingen configureren hoe Configuration Manager en System Center Operations Manager waarschuwingen voor deze implementatie genereren moeten. U kunt de waarschuwingen alleen configureren wanneer **Type implementatie** op de pagina Implementatie-instellingen is ingesteld op **Vereist** .  

    > [!NOTE]  
    >  U kunt recente waarschuwingen met betrekking tot software-updates weergegeven in het knooppunt **Software-updates** in de werkruimte **Softwarebibliotheek** .  
