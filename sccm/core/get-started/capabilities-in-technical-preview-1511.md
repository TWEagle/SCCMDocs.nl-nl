---
title: Mogelijkheden in Technical Preview 1511 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1511.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69473706-21b3-498b-a67e-670fdc988f0d
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: d0bde2c085cc9b330bc772e68081d629ca9e2f11
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1511-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1511 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1511 zijn geïntroduceerd. Deze versie is een basislijn installatie voor de technical preview kunt u een nieuwe site technische preview installeren of upgraden van een eerdere versie van de technische preview.   Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.  

De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="BKMK_WUfB"></a>Integratie met Windows Update voor bedrijven in Windows 10  
 Configuration Manager heeft nu de mogelijkheid om te onderscheiden van een Windows-10-computer die direct is verbonden via Windows Update voor bedrijven (WUfB) ten opzichte van de verbinding met WSUS voor het verkrijgen van updates voor Windows 10 en upgrades.  Voor computers die zijn verbonden via WUfB, updates en upgrades kunnen worden beheerd op de rekenen ingesteld door een gebruiker met beheerdersrechten via Groepsbeleid of MDM-beleidsregels en deze updates/upgrades rechtstreeks vanuit WUfB kan worden geïnstalleerd.    
Voor computers die zijn verbonden via WUfB, is Configuration Manager niet mogelijk om te rapporteren over de status van de Updatevereisten (inclusief Windows-Updates of Updates voor definities). Ook pas Configuration Manager weer voor het implementeren van Updates voor Microsoft of 3e partij op deze computers.  

 **Vereisten voor dit scenario:**  

-   Windows 10 Desktop Pro of Windows 10 Enterprise Edition versie 1511 of hoger  

-   Computers die moeten worden beheerd via [Windows Update voor bedrijven](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx).  

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de volgende taak voltooid en vervolgens de feedbackgegevens boven in dit onderwerp gebruiken om te laat ons weten hoe het werkt:  

1.  Schakel de Windows Update Agent uit zodat deze niet scant ten opzichte van WSUS als deze eerder werd ingeschakeld.   
    De registersleutel **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\useWSUSServer** kunnen worden ingesteld om aan te geven of de computer wordt gescand tegen WSUS of Windows Update.  Wanneer de waarde 2 is, wordt niet gescand ten opzichte van WSUS.  

2.  Let op het nieuwe kenmerk **UseWUServer**onder de **Windows Update** knooppunt in de Configuration Manager Resource Explorer.  

3.  Maak een verzameling op basis van het **UseWUServer** -kenmerk voor alle computers die via WUfB zijn verbonden voor updates en upgrades.  

4.  Maak een clientagentinstelling voor het uitschakelen van de werkstroom voor software-updates en pas de instelling toe op de verzameling van computers die rechtstreeks zijn verbonden met WUfB.  

5.  Op computers die via WUfB worden beheerd, wordt **Onbekend** weergegeven in de compatibiliteitsstatus en worden niet geteld als onderdeel van het algehele compatibiliteitspercentage.  

##  <a name="BKMK_Office365ProPlus"></a>Office 365 ProPlus clientupdate via System Center Configuration Manager beheren  
 Configuration Manager heeft nu de mogelijkheid om Office 365 bureaubladclient updates met de Configuration Manager-Software-updatebeheer de werkstroom te beheren.    
Wanneer Microsoft publiceert een nieuwe desktop Office 365-clientupdate voor Windows Server Updates Services (WSUS), Configuration Manager kan worden gesynchroniseerd van de update naar de catalogus als de Office 365-update is geconfigureerd als onderdeel van de synchronisatie van de catalogus.  De siteserver van Configuration Manager zal downloaden van updates voor Office 365-client en distribueert het pakket naar distributiepunten van Configuration Manager.  De Configuration Manager-client zal vervolgens informeren over Office 365 bureaubladclients waar u de updates en wanneer u de update-installatieproces te starten.  

**Vereisten voor dit scenario:**  

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de volgende taak voltooid en vervolgens de feedbackgegevens boven in dit onderwerp gebruiken om te laat ons weten hoe het werkt:  

1.  U kunt ze uit de Configuration Manager-console te bekijken en Office 365-updates naar de siteserver van Configuration Manager gesynchroniseerd.  

2.  U kunt goedkeuren en Office 365-updates implementeren.  

3.  U kunt downloaden en met succes Office 365-updates naar clients.  

4.  U kunt naleving voor Office 365-updates controleren via de console bewaking of rapporten.  

 Zie voor gedetailleerde stappen [clientupdates Office 365 beheren met de technische Preview van System Center Configuration Manager](https://technet.microsoft.com/library/mt628083.aspx).  

##  <a name="BKMK_AlwasyOn"></a>Ondersteuning voor SQL Server AlwaysOn voor maximaal beschikbare databases  
 Configuration Manager ondersteunt nu het gebruik van een SQL Server AlwaysOn-beschikbaarheidsgroepen om de sitedatabase te hosten.  Wanneer u een nieuwe site installeert, kunt u de beschikbaarheidsgroep gebruiken in plaats van een normale exemplaar van SQL Server setup sturen.  

> [!NOTE]  
>  Geslaagde configuratie en gebruik van beschikbaarheidsgroepen moet worden vertrouwd bij het configureren van SQL Server-beschikbaarheidsgroepen, en is afhankelijk van de documentatie en -procedures die zijn opgegeven in de Documentatiebibliotheek voor SQL Server.  

Het hoogste niveau proces om te configureren en gebruiken van beschikbaarheidsgroepen omvat het volgende:  

1.  De beschikbaarheidsgroep in SQL Server configureren.  

2.  Een nieuwe Configuration Manager-site installeert en tijdens de installatie geeft u de site te gebruiken van de beschikbaarheidsgroep door te geven van de groepen eindpunt.  

**Vereisten voor dit scenario:**  

-   Vereist een versie van SQL Server wordt ondersteund door de Configuration Manager Technical Preview  

-   U moet maken en configureren van de beschikbaarheidsgroep van de SQL-Server voordat de installatie van Configuration Manager  

-   De beschikbaarheidsgroep moet één primaire replica hebben, en mag maximaal twee gesynchroniseerde, secundaire replica’s hebben  

-   De beschikbaarheidsgroep moet ten minste één eindpunt hebben  

-   U moet een netwerklocatie die toegankelijk is voor elke SQL-Server in de beschikbaarheidsgroep hebben. Deze locatie door Setup wordt gebruikt bij het configureren van de beschikbaarheidsgroep en kan worden verwijderd nadat Setup is voltooid.  

**Bekende problemen voor deze release:**  

-   U kunt is een nieuwe replicatielid toevoegen aan een beschikbaarheidsgroep die al in gebruik als een site-database. In plaats daarvan moet u de site opnieuw nadat het nieuwe lid van de replica is toegevoegd.  

-   Voor dit scenario moet u mogelijk installeren de **SQL Server 2012 native client** ([van SQL Server 2012 Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065)) op de beheerpuntserver. Dit voorkomt dat SQL-verbindingsfouten (die worden vastgelegd in de **mp_getauth.log** op de beheerserver punt).  

### <a name="try-it-out"></a>Probeer het nu!  
Probeer de volgende taken uitvoeren en vervolgens de feedbackgegevens boven in dit onderwerp gebruiken om te laat ons weten hoe ze besteed:  

-   Ik kan een primaire site installeert die gebruikmaakt van een databaseserver is geconfigureerd voor de SQL AlwaysOn Availability Groups  

-   Ik kan mijn SQL AlwaysOn van de beschikbaarheidsgroep naar een nieuwe replica in de groep failover en de primaire site nog steeds operationeel  

### <a name="configuring-sql-server-alwayson-for-configuration-manager"></a>SQL Server AlwaysOn configureren voor Configuration Manager  
 Gebruik de volgende procedures voor het eerst maken en configureren van de beschikbaarheidsgroep en installeer vervolgens een nieuwe Configuration Manager-site die gebruikmaakt van de beschikbaarheidsgroep.  

#### <a name="to-create-a-sql-server-alwayson-availability-group"></a>Maken van een SQL Server AlwaysOn-beschikbaarheidsgroep  
Het proces van [maken van een SQL Server-beschikbaarheidsgroep](https://technet.microsoft.com/library/ff878265\(v=sql.120\).aspx) wordt beschreven in de Documentatiebibliotheek voor SQL Server.  Wanneer u de beschikbaarheidsgroep maakt, controleert u dat de volgende vereisten voor gebruik met Configuration Manager wordt voldaan:  

-   Maximaal drie leden:  

    -   Een primaire replica en maximaal twee secundaire replica's  

    -   Secundaire replica's moet synchroon.  

        > [!TIP]  
        >  U wordt aangeraden dat de secundaire replica's worden geconfigureerd om te worden alleen-lezen. Hiermee kunt u een secundaire replica gebruiken voor functies zoals reporting behoud van de prestaties van de primaire replica voor site-operaties.  

-   Ten minste één eindpunt. De virtuele naam van dit eindpunt wordt gebruikt wanneer u de Configuration Manager-site installeert.  

    > [!TIP]  
    >  Hoewel de groep meerdere eindpunten bevatten kan, Configuration Manager alleen kunt maken gebruik van een.  

#### <a name="to-install-a-configuration-manager-site-that-uses-the-availability-group"></a>Een Configuration Manager-site die gebruikmaakt van de beschikbaarheidsgroep wilt installeren  
Om een site te installeren dat gebruikmaakt van een SQL Server-beschikbaarheidsgroep:  

1.  Vervangen door het volgende als u wordt gevraagd door Configuration Manager Setup:  

    -   **SQL Server-naam**: Geef de virtuele naam voor het eindpunt dat u hebt geconfigureerd bij het maken van de beschikbaarheidsgroep. De virtuele naam moet een volledige DNS-naam, zoals  **&lt;endpointServer\>. fabrikam.com**.  

    -   **Exemplaar**:  Deze waarde moet leeg blijven. Er is geen instantie in deze configuratie.  

    -   **Database**: Voer de naam van de database die u hebt gemaakt op de primaire replica van de beschikbaarheidsgroep.  

2.  Vervolgens moet u een netwerklocatie die toegankelijk is voor elke SQL-Server in de groep opgeven:  

    -   Het computeraccount en het serviceaccount van elke SQL Server volledig beheer toegang nodig tot deze locatie.  

    -   Deze locatie kan wordt alleen gebruikt tijdens de installatie en niet-gedeeld of verwijderd nadat Setup is voltooid en de site is geïnstalleerd.  

3.  Nadat u deze informatie hebt opgegeven, voltooit u de installatie met uw normale proces en configuraties.  

##  <a name="BKMK_ClusterServerUpdates"></a>Service een servercluster  
U kunt nu een verzameling maken die servers in een cluster bevat en configureer vervolgens de clusterinstellingen moet worden gebruikt wanneer u updates op het cluster implementeren. Het percentage van de servers die online op een bepaald moment zijn over het configureren van vóór de implementatie en post-implementatie PowerShell-scripts om aangepaste acties worden uitgevoerd, kunt u bepalen.  

**Bekende problemen voor deze release:**  

-   Reporting is niet beschikbaar voor de status van de implementatie van software-updates voor clusterservers controleren.  

-   De optie Onderhoud volgorde op de **clusterinstellingen** pagina is uitgeschakeld en niet beschikbaar in deze release.  

### <a name="try-it-out"></a>Probeer het nu!  
Probeer de volgende taak voltooid en vervolgens de feedbackgegevens boven in dit onderwerp gebruiken om te laat ons weten hoe het werkt:  

-   Ik kan een verzameling maken die een cluster van servers vertegenwoordigt. Deze test kunt u uw verzamelen lidmaatschapsregels om 2 machines in deze verzameling.  

-   Ik kan opgeven dat alleen 50% van de servers in het cluster offline op enig moment in de onderhoudsmodus cluster kunnen worden. Gebruik de voorbeeldscripts in de procedure om op te geven van de scripts die vóór de implementatie en post-implementatie.  

-   Implementeer een update op deze verzameling. Controleer de bestanden start.txt en end.txt in C:\temp en controleer of de begin- en eindtijden voor de implementatie op de servers in het cluster. Raadpleeg het bestand UpdatesDeployment.log voor meer informatie.  

#### <a name="to-create-a-collection-for-a-server-cluster"></a>Een verzameling voor een servercluster maken  

1.  [Maak een apparaatverzameling](https://technet.microsoft.com/library/gg712295.aspx) waarin de servers in het cluster.  

2.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**met de rechtermuisknop op de verzameling met de servers in het cluster en klik vervolgens op **eigenschappen**.  

3.  Op de **algemeen** tabblad **alle apparaten deel uitmaken van hetzelfde servercluster**, en klik vervolgens op **instellingen**.  

4.  Op de **clusterinstellingen** pagina, selecteert u het percentage van de servers die kunnen worden uitgeschakeld op het moment dat de software-updates geïnstalleerd. Één clusterserver mogelijk offline gezet tegelijk ongeacht het percentage die u opgeeft. Configuration Manager wordt naar beneden afronden bij het selecteren van het aantal servers tegelijk service. Bijvoorbeeld, als u ervoor 51 kiest % en er 4 servers in het cluster zijn, wordt 2 servers offline gezet op hetzelfde moment.  

5.  Geef op of een script vóór implementatie (knooppunt verwerkingsstop) of na de implementatie (knooppunt hervatten) script gebruiken.  

    > [!TIP]  
    >  Hier volgen voorbeelden dat u gebruiken kunt voor voorafgaand aan de implementatie testen en na de implementatie scripts die de huidige tijd naar een tekstbestand schrijven:  
    >   
    >  **Voorafgaand aan de implementatie**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Post-implementatie**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-cluster"></a>Voor het implementeren van software-updates naar de server-cluster  

1.  [Software-updates implementeren](https://technet.microsoft.com/library/gg712304.aspx) aan de verzameling van server-cluster.  

2.  [De implementatie van software-update controleren](https://technet.microsoft.com/library/gg712304.aspx).  

