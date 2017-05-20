---
title: SQL Server-cluster | Microsoft-documenten
description: Gebruik een SQL Server-cluster om de System Center Configuration Manager-sitedatabase te hosten. Bevat informatie over de ondersteunde opties.
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d09a82c6-bbd1-49ca-8ffe-e3ce87b85d33
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ce0d7fc5f3d1812c4d62e551661c0ef89707567b
ms.openlocfilehash: 53f119bbb1f8827a9c23c8b747840350bbb92790
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="use-a-sql-server-cluster-for-the-system-center-configuration-manager-site-database"></a>Gebruik een SQL Server-cluster voor de System Center Configuration Manager-sitedatabase

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 U kunt een SQL Server-cluster gebruiken om de System Center Configuration Manager-sitedatabase te hosten. De sitedatabase is de enige sitesysteemrol die op een servercluster wordt ondersteund.  

> [!IMPORTANT]  
>  Geslaagde instellen van SQL Server-clusters is afhankelijk van documentatie en -procedures die zijn opgegeven in de Documentatiebibliotheek voor SQL Server.  

 Een cluster kunt failover-ondersteuning te verbeteren van de betrouwbaarheid van de sitedatabase. Echter biedt het geen verdere verwerking of voordelen laden. In feite optreden verslechtering van de prestatie, omdat de siteserver het actieve knooppunt van de SQL Server-cluster vinden moet voordat deze verbinding met de sitedatabase maakt.  

 Voordat u Configuration Manager installeert, moet u SQL Server-cluster voor de ondersteuning van Configuration Manager voorbereiden. (Zie de vereisten verderop in deze sectie.)  

 Tijdens de installatie van Configuration Manager installeert de Volume Shadow Copy-Service Windows-schrijver op ieder fysiek computerknooppunt van de Microsoft Windows Server-cluster. Dit ondersteunt de **back-upserver van Site** onderhoudstaak.  

 Nadat de site is geïnstalleerd, controleert Configuration Manager op wijzigingen in het clusterknooppunt ieder uur. Configuration Manager worden beheerd, zullen alle wijzigingen die zijn gevonden die van invloed op installaties van Configuration Manager-onderdeel (zoals een failover van een knooppunt of toevoeging van een nieuw knooppunt aan het SQL Server-cluster).  

## <a name="supported-options-for-using-a-sql-server-failover-cluster"></a>Opties voor het gebruik van een SQL Server-failovercluster ondersteund

De volgende opties worden ondersteund voor SQL Server-failoverclusters als de sitedatabase gebruikt:

-   Een cluster met één exemplaar  

-   Configuratie met meerdere exemplaren  

-   Meerdere actieve knooppunten  

-   Een benoemde of een standaardexemplaar  

Let op de volgende vereisten:  

-   De sitedatabase mag niet op de siteserver staan. (De sitesysteemserver mag geen deel uitmaken van de cluster.)  

-   U moet het computeraccount van de site-server toevoegen aan de lokale groep Administrators van elke server in het cluster.  

-   Ter ondersteuning van Kerberos-verificatie, de **TCP/IP** netwerkcommunicatieprotocol moet zijn ingeschakeld voor de netwerkverbinding van elk SQL Server-clusterknooppunt. **Named-pipes** is niet vereist, maar kan worden gebruikt om problemen met de Kerberos-verificatie op te lossen. De instellingen voor het netwerkprotocol worden geconfigureerd in **SQL Server Configuration Manager**onder **SQL Server-netwerkconfiguratie**.  

-   Als u een PKI gebruikt, raadpleegt u PKI-certificaatvereisten voor Configuration Manager voor de specifieke certificaatvereisten wanneer u een SQL Server-cluster voor de sitedatabase gebruikt.  

Houd rekening met de volgende beperkingen:  

-   **Installatie en configuratie:**  

    -   Secundaire sites kunnen geen SQL Server-cluster gebruiken.  

    -   Wanneer u een SQL Server-cluster opgeeft kunt u geen andere locatie dan de standaardbestandslocatie voor de sitedatabase opgeven.  

-   **SMS-provider:**  

    -   Het wordt niet ondersteund voor een exemplaar van de SMS-Provider installeren op een SQL Server-cluster, of op een computer die wordt uitgevoerd als een geclusterd SQL Server-knooppunt.  

-   **Opties voor gegevensreplicatie:**  

    -   Als u wilt gebruiken **gedistribueerde weergaven**, u kunt een SQL Server-cluster niet gebruiken om de sitedatabase te hosten.  

-   **Back-up en herstel:**  

    -   Configuration Manager biedt geen ondersteuning voor back-up van Data Protection Manager (DPM) voor een SQL Server-cluster dat een benoemd exemplaar gebruikt. Maar ondersteunt back-up van DPM op een SQL Server-cluster dat gebruik maakt van het standaardexemplaar van SQL Server.  

## <a name="prepare-a-clustered-sql-server-instance-for-the-site-database"></a>Voorbereiden van een geclusterd SQL Server-exemplaar voor de sitedatabase  

Hier worden de belangrijkste taken te voltooien als u wilt voorbereiden van uw sitedatabase:

-   Maak de virtuele SQL Server-cluster om de sitedatabase te hosten in een bestaande Windows Server-clusteromgeving. Zie voor specifieke stappen over het installeren en instellen van een SQL Server-cluster de specifieke documentatie bij uw versie van SQL Server. Bijvoorbeeld, als u SQL Server 2008 R2 gebruikt, Zie [installeren van een SQL Server 2008 R2 Failover-Cluster](http://go.microsoft.com/fwlink/p/?LinkId=240231).  

-   U kunt een bestand plaatsen in de hoofdmap van ieder station waar u niet wilt dat Configuration Manager site-onderdelen installeren op elke computer in de SQL Server-cluster. De naam van het bestand moet **NO_SMS_ON_DRIVE.SMS**. Configuration Manager installeert standaard enkele onderdelen op ieder fysiek knooppunt om bewerkingen zoals back-ups te ondersteunen.  

-   Voeg het computeraccount van de siteserver toe aan de groep **Lokale beheerders** van iedere Windows Server-clusterknooppuntcomputer.  

-   Wijs in het virtuele SQL Server-exemplaar de **sysadmin** SQL Server-rol aan het gebruikersaccount dat het installatieprogramma van Configuration Manager wordt uitgevoerd.  

### <a name="to-install-a-new-site-using-a-clustered-sql-server"></a>Een nieuwe site installeren met een geclusterde SQL Server  
 Voor het installeren van een site die een geclusterde sitedatabase gebruikt, voer Configuration Manager setup na het normale proces voor het installeren van een site met de volgende afwijking:  

-   Geef op de pagina **Databasegegevens** de naam op van het virtuele SQL Server-clusterexemplaar waarop de sitedatabase wordt gehost. De naam van de computer waarop SQL Server wordt uitgevoerd, wordt vervangen door het virtuele exemplaar.  

    > [!IMPORTANT]  
    >  Wanneer u de naam van het virtuele SQL Server-clusterexemplaar invoert, voer dan niet de naam in van het virtuele Windows Server-exemplaar dat is gemaakt door de Windows Server-cluster. Als u de naam van de virtuele Windows-Server gebruikt, wordt de sitedatabase geïnstalleerd op de lokale vaste schijf van de actieve Windows Server-clusterknooppunt. Dit heeft tot gevolg dat er geen juiste failover plaatsvindt, als dit knooppunt uitvalt.  

