---
title: Mogelijkheden in Technical Preview 1511 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager versie 1511.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69473706-21b3-498b-a67e-670fdc988f0d
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: d0bde2c085cc9b330bc772e68081d629ca9e2f11
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1511-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1511 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager versie 1511 zijn. Deze versie is een basislijn installatie voor de technical preview kunt u een nieuwe technische preview-site installeren of upgraden van een eerdere versie van de technical preview.   Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.  

Hier volgen nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="BKMK_WUfB"></a>Integratie met Windows Update voor bedrijven in Windows 10  
 Configuration Manager heeft nu de mogelijkheid om te onderscheiden van een Windows 10-computer die direct is verbonden via Windows Update voor bedrijven (WUfB) die met WSUS zijn verbonden voor het ophalen van Windows 10-updates en upgrades.  De updates en upgrades kunnen worden beheerd met de frequentie die is ingesteld door een gebruiker met beheerdersrechten via Groepsbeleid of MDM-beleidsregels voor computers die via WUfB zijn verbonden, en deze updates/upgrades rechtstreeks vanuit WUfB kunnen worden geïnstalleerd.    
Voor computers die via WUfB zijn verbonden, zal Configuration Manager niet mogelijk om te rapporteren over de compatibiliteitsstatus (inclusief Windows-Updates of Updates voor definities). Configuration Manager wordt ook niet worden kunnen Microsoft-Updates of updates 3e derden implementeren op deze computers.  

 **Vereisten voor dit scenario:**  

-   Windows 10 Desktop Pro of Windows 10 Enterprise Edition versie 1511 of hoger  

-   Computers moeten worden beheerd via [Windows Update voor bedrijven](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx).  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taak en gebruik daarna de feedbackinformatie boven aan dit onderwerp te laten weten hoe het is gegaan:  

1.  Schakel de Windows Update Agent uit zodat deze niet scant ten opzichte van WSUS als deze eerder werd ingeschakeld.   
    De registersleutel **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\useWSUSServer** kan worden ingesteld om aan te geven of de computer bij WSUS of Windows Update scant.  Wanneer de waarde 2 is, wordt niet gescand ten opzichte van WSUS.  

2.  Let op het nieuwe kenmerk **UseWUServer**onder de **Windows Update** knooppunt in de Configuration Manager Resource Explorer.  

3.  Maak een verzameling op basis van het **UseWUServer** -kenmerk voor alle computers die via WUfB zijn verbonden voor updates en upgrades.  

4.  Maak een clientagentinstelling voor het uitschakelen van de werkstroom voor software-updates en pas de instelling toe op de verzameling van computers die rechtstreeks zijn verbonden met WUfB.  

5.  Op computers die via WUfB worden beheerd, wordt **Onbekend** weergegeven in de compatibiliteitsstatus en worden niet geteld als onderdeel van het algehele compatibiliteitspercentage.  

##  <a name="BKMK_Office365ProPlus"></a>Update voor Office 365 ProPlus-Client via System Center Configuration Manager beheren  
 Configuration Manager heeft nu de mogelijkheid voor het beheren van updates voor Office 365-desktopclients met de werkstroom voor Software-updatebeheer van Configuration Manager.    
Wanneer Microsoft publiceert een nieuwe update voor Office 365-desktopclients naar Windows Server Updates Services (WSUS), zich Configuration Manager de update naar de catalogus synchroniseren als de update voor Office 365 als onderdeel van de catalogussynchronisatie is geconfigureerd.  De siteserver van Configuration Manager gedownload van de updates voor Office 365-clients en distribueert het pakket naar distributiepunten van Configuration Manager.  Configuration Manager-client vervolgens informeert Office 365-desktopclients waar u de updates verkrijgen en wanneer u om de update-installatieproces te starten.  

**Vereisten voor dit scenario:**  

### <a name="try-it-out"></a>Probeer het nu!  
 Voer de volgende taak en gebruik daarna de feedbackinformatie boven aan dit onderwerp te laten weten hoe het is gegaan:  

1.  U kunt Office 365-updates naar de Configuration Manager-siteserver synchroniseren en deze uit de Configuration Manager-console te bekijken.  

2.  U kunt goedkeuren en implementeren van updates voor Office 365.  

3.  U kunt downloaden en met succes Office 365-updates op clients.  

4.  U kunt de naleving voor Office 365-updates controleren via in-console bewaking of rapporten.  

 Zie voor gedetailleerde stappen [clientupdates van Office 365 beheren met System Center Configuration Manager Technical Preview](https://technet.microsoft.com/library/mt628083.aspx).  

##  <a name="BKMK_AlwasyOn"></a>Ondersteuning voor SQL Server AlwaysOn voor maximaal beschikbare databases  
 Configuration Manager ondersteunt nu het gebruik van een SQL Server AlwaysOn-beschikbaarheidsgroepen voor het hosten van de sitedatabase.  Wanneer u een nieuwe site installeert, kunt u het installatieprogramma voor de beschikbaarheidsgroep gebruiken in plaats van een normaal exemplaar van SQL Server verwijzen.  

> [!NOTE]  
>  Geslaagde configuratie en het gebruik van beschikbaarheidsgroepen vereist bekendheid met het configureren van SQL Server-beschikbaarheidsgroepen en is afhankelijk van de documentatie en procedures die zijn opgegeven in de Documentatiebibliotheek van SQL Server.  

Het hoogste niveau proces om te configureren en gebruiken van beschikbaarheidsgroepen omvat:  

1.  De beschikbaarheidsgroep in SQL Server configureren.  

2.  Een nieuwe Configuration Manager-site installeert en directe tijdens de installatie van de site te gebruiken van de beschikbaarheidsgroep door te geven van het eindpunt van de groep.  

**Vereisten voor dit scenario:**  

-   Vereist een versie van SQL Server wordt ondersteund door de Configuration Manager Technical Preview  

-   U moet maken en de SQL Server-beschikbaarheidsgroep configureren voor de installatie van Configuration Manager  

-   De beschikbaarheidsgroep moet één primaire replica hebben, en mag maximaal twee gesynchroniseerde, secundaire replica’s hebben  

-   De beschikbaarheidsgroep moet ten minste één eindpunt hebben.  

-   U moet een netwerklocatie bevindt die elke SQL-Server in de beschikbaarheidsgroep toegang tot hebben. Deze locatie door Setup wordt gebruikt bij het configureren van de beschikbaarheidsgroep, en kan worden verwijderd nadat Setup is voltooid.  

**Bekende problemen voor deze release:**  

-   U kan niet met succes een nieuw replicalid toevoegen aan een beschikbaarheidsgroep die al in gebruik als een sitedatabase. In plaats daarvan moet u de site opnieuw nadat het nieuwe replicalid is toegevoegd.  

-   Voor dit scenario moet u mogelijk voor het installeren van de **SQL Server 2012 native client** ([van SQL Server 2012 Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065)) op de beheerpuntserver. Dit voorkomt dat SQL-verbindingsfouten optreden (deze worden vastgelegd in de **mp_getauth.log** op de beheerpuntserver).  

### <a name="try-it-out"></a>Probeer het nu!  
Voer de volgende taken uitvoeren en vervolgens met de feedbackinformatie boven aan dit onderwerp laat ons weten hoe het is gegaan:  

-   Ik kan een primaire site die gebruikmaakt van een databaseserver die is geconfigureerd voor de SQL AlwaysOn-beschikbaarheidsgroepen installeren  

-   Ik kan mijn SQL AlwaysOn-beschikbaarheidsgroep groep naar een nieuwe replica in de groep failover en de primaire site werkt nog altijd  

### <a name="configuring-sql-server-alwayson-for-configuration-manager"></a>SQL Server AlwaysOn configureren voor Configuration Manager  
 Gebruik de volgende procedures om eerst maken en configureren van de beschikbaarheidsgroep en installeer vervolgens een nieuwe Configuration Manager-site die gebruikmaakt van de beschikbaarheidsgroep.  

#### <a name="to-create-a-sql-server-alwayson-availability-group"></a>Een SQL Server AlwaysOn-beschikbaarheidsgroep maken  
Het proces voor het [maken van een SQL Server-beschikbaarheidsgroep](https://technet.microsoft.com/library/ff878265\(v=sql.120\).aspx) wordt beschreven in de Documentatiebibliotheek van SQL Server.  Wanneer u de beschikbaarheidsgroep maakt, moet u dat de volgende vereisten voor gebruik met Configuration Manager worden voldaan:  

-   Maximaal drie leden:  

    -   Eén primaire replica en maximaal twee secundaire replica's  

    -   Secundaire replica's moet gesynchroniseerd zijn.  

        > [!TIP]  
        >  We raden aan dat de secundaire replica's worden geconfigureerd als alleen-lezen. Hiermee kunt u een secundaire replica gebruiken voor functies zoals rapportage, terwijl de prestaties van de primaire replica voor site-operaties.  

-   Ten minste één eindpunt. De virtuele naam van dit eindpunt wordt gebruikt wanneer u de Configuration Manager-site installeert.  

    > [!TIP]  
    >  Hoewel de groep meerdere eindpunten bevatten kan, kunt alleen Configuration Manager maken gebruik van een.  

#### <a name="to-install-a-configuration-manager-site-that-uses-the-availability-group"></a>Een Configuration Manager-site installeren die gebruikmaakt van de beschikbaarheidsgroep.  
Voor het installeren van een site die gebruikmaakt van een SQL Server-beschikbaarheidsgroep:  

1.  Vervang het volgende wanneer u wordt gevraagd door Setup van Configuration Manager:  

    -   **SQL Server-naam**: Voer de virtuele naam van het eindpunt dat u bij het maken van de beschikbaarheidsgroep hebt geconfigureerd. De virtuele naam moet een volledige DNS-naam, zoals  **&lt;endpointServer\>. fabrikam.com**.  

    -   **Exemplaar**:  Deze waarde moet leeg blijven. Er is geen exemplaar in deze configuratie.  

    -   **Database**: Voer de naam van de database die u hebt gemaakt op de primaire replica van de beschikbaarheidsgroep.  

2.  Vervolgens moet u een netwerklocatie die toegankelijk elke SQL-Server in de groep opgeven:  

    -   De computeraccount en de serviceaccount van elke SQL Server moeten volledige beheertoegang krijgen tot deze locatie.  

    -   Deze locatie worden wordt alleen gebruikt tijdens de installatie en geannuleerd of worden verwijderd nadat Setup is voltooid en de site is geïnstalleerd.  

3.  Nadat u deze informatie opgeeft, voltooit u de installatie volgens uw normale proces en configuraties.  

##  <a name="BKMK_ClusterServerUpdates"></a>Clusterservers onderhouden  
U kunt nu een verzameling met servers in een cluster maken en configureer vervolgens de clusterinstellingen te gebruiken wanneer u updates voor het cluster implementeert. U kunt bepalen welk percentage van de servers die online op een bepaald moment zijn over het configureren van de PowerShell-scripts voor vóór en na de implementatie om aangepaste acties worden uitgevoerd.  

**Bekende problemen voor deze release:**  

-   Reporting is niet beschikbaar om te controleren van de status van de implementatie van software-updates voor clusterservers.  

-   De optie onderhoudsreeks op de **clusterinstellingen** pagina is uitgeschakeld en niet beschikbaar in deze release.  

### <a name="try-it-out"></a>Probeer het nu!  
Voer de volgende taak en gebruik daarna de feedbackinformatie boven aan dit onderwerp te laten weten hoe het is gegaan:  

-   Ik kan een verzameling die staat voor een cluster van servers maken. Voor deze test kunt u uw verzamelde lidmaatschapsregels met 2 machines in deze verzameling.  

-   Ik kan opgeven dat slechts 50% van de servers in het cluster op enig moment in de onderhoudsmodus cluster offline kan zijn. Gebruik de voorbeeldscripts in de procedure om de scripts voor vóór en na de implementatie.  

-   Implementeer een update aan deze verzameling. Controleert u de bestanden start.txt en end.txt in C:\temp en controleer of de begin- en eindtijden voor de implementatie op de servers in het cluster. Controleer het bestand updatesdeployment.log voor meer informatie.  

#### <a name="to-create-a-collection-for-a-server-cluster"></a>Een verzameling voor een servercluster maken  

1.  [Maak een apparaatverzameling](https://technet.microsoft.com/library/gg712295.aspx) waarin zich de servers in het cluster.  

2.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**, met de rechtermuisknop op de verzameling met de servers in het cluster en klik vervolgens op **eigenschappen**.  

3.  Op de **algemene** tabblad **alle apparaten zijn onderdeel van hetzelfde servercluster**, en klik vervolgens op **instellingen**.  

4.  Op de **clusterinstellingen** pagina, selecteert u het percentage van de servers die kunnen worden uitgevoerd offline tegelijkertijd naar softwareupdates zijn geïnstalleerd. Één clusterserver mogelijk offline worden gehaald tegelijk ongeacht het percentage dat u opgeeft. Configuration Manager wordt naar beneden afgerond bij het selecteren van het aantal servers waaraan tegelijk service. Bijvoorbeeld, als u kiest voor 51% en er 4 servers in het cluster, zal 2 servers offline worden gehaald op hetzelfde moment.  

5.  Geef op of een script vóór implementatie (knooppuntcorrectie) of een script ná implementatie (knooppunthervatting) wilt gebruiken.  

    > [!TIP]  
    >  Hier volgen voorbeelden die u gebruiken kunt bij het testen voorafgaand aan de implementatie en na de implementatie scripts die de huidige tijd naar een tekstbestand schrijven:  
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
    >  **Na de implementatie**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-cluster"></a>Software-updates implementeren op de server-cluster  

1.  [Software-updates implementeren](https://technet.microsoft.com/library/gg712304.aspx) aan de verzameling van server-cluster.  

2.  [De implementatie van de software-update controleren](https://technet.microsoft.com/library/gg712304.aspx).  
