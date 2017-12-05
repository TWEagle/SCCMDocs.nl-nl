---
title: SQL Server-cluster
titleSuffix: Configuration Manager
description: Een SQL Server-cluster gebruiken om de System Center Configuration Manager-sitedatabase te hosten. Bevat informatie over ondersteunde opties.
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d09a82c6-bbd1-49ca-8ffe-e3ce87b85d33
caps.latest.revision: "10"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: f3920c49ad9d1e11104e36569aa229bf4a13d319
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="use-a-sql-server-cluster-for-the-system-center-configuration-manager-site-database"></a>Een SQL Server-cluster gebruiken voor de sitedatabase voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 U kunt een SQL Server-cluster gebruiken om de System Center Configuration Manager-sitedatabase te hosten. De sitedatabase is de enige sitesysteemrol die op een servercluster wordt ondersteund.  

> [!IMPORTANT]  
>  Er is een geslaagde instellen van SQL Server-clusters afhankelijk van de documentatie en procedures die zijn opgegeven in de Documentatiebibliotheek van SQL Server.  

 Een cluster met failover-ondersteuning te bieden en verbeteren van de betrouwbaarheid van de sitedatabase. Echter biedt deze geen verdere verwerking of voordelen laden. Zelfs optreden verslechtering van de prestatie, omdat de siteserver het actieve knooppunt van de SQL Server-cluster vinden moet voordat deze verbinding met de sitedatabase maakt.  

 Voordat u Configuration Manager installeert, moet u de SQL Server-cluster ter ondersteuning van Configuration Manager voorbereiden. (Zie de vereisten verderop in deze sectie.)  

 Tijdens de installatie van Configuration Manager installeert de Volume Shadow Copy-Service Windows-schrijver op ieder fysiek computerknooppunt van de Microsoft Windows Server-cluster. Dit biedt ondersteuning voor de **back-upserver van Site** onderhoudstaak.  

 Nadat de site is geïnstalleerd, Configuration Manager controleert op wijzigingen in het clusterknooppunt elk uur. Configuration Manager beheert automatisch eventuele wijzigingen die zijn aangetroffen die invloed hebben op installaties van Configuration Manager-onderdeel (zoals een failover van een knooppunt of toevoeging van een nieuw knooppunt aan het SQL Server-cluster).  

## <a name="supported-options-for-using-a-sql-server-failover-cluster"></a>Ondersteunde opties voor het gebruik van een SQL Server-failovercluster

De volgende opties worden ondersteund voor SQL Server-failoverclusters gebruikt als de sitedatabase:

-   Een cluster met één exemplaar  

-   Configuratie met meerdere exemplaren  

-   Meerdere actieve knooppunten  

-   Een benoemde of een standaardexemplaar  

Let op de volgende vereisten:  

-   De sitedatabase mag niet op de siteserver staan. (De sitesysteemserver mag geen deel uitmaken van de cluster.)  

-   U moet het computeraccount van de siteserver toevoegen aan de lokale groep Administrators van elke server in het cluster.  

-   Ter ondersteuning van Kerberos-verificatie, de **TCP/IP** -netwerkcommunicatieprotocol moet zijn ingeschakeld voor de netwerkverbinding van elk SQL Server-clusterknooppunt. **Named-pipes** is niet vereist, maar kan worden gebruikt om problemen met de Kerberos-verificatie op te lossen. De instellingen voor het netwerkprotocol worden geconfigureerd in **SQL Server Configuration Manager**onder **SQL Server-netwerkconfiguratie**.  

-   Als u een PKI gebruikt, ziet u PKI-certificaatvereisten voor Configuration Manager voor de specifieke certificaatvereisten wanneer u een SQL Server-cluster voor de sitedatabase gebruikt.  

Houd rekening met de volgende beperkingen:  

-   **Installatie en configuratie:**  

    -   Secundaire sites kunnen geen SQL Server-cluster gebruiken.  

    -   Wanneer u een SQL Server-cluster opgeeft kunt u geen andere locatie dan de standaardbestandslocatie voor de sitedatabase opgeven.  

-   **SMS-provider:**  

    -   Een exemplaar van de SMS-Provider installeert op een SQL Server-cluster of op een computer die wordt uitgevoerd als een geclusterd SQL Server-knooppunt wordt niet ondersteund.  

-   **Opties voor gegevensreplicatie:**  

    -   Als u wilt gebruiken **gedistribueerde weergaven**, u een SQL Server-cluster niet gebruiken om de sitedatabase te hosten.  

-   **Back-up en herstel:**  

    -   Configuration Manager biedt geen ondersteuning voor back-up van Data Protection Manager (DPM) voor een SQL servercluster dat een benoemd exemplaar gebruikt. Echter biedt, ondersteuning voor back-up van DPM op een SQL Server-cluster dat gebruik maakt van het standaardexemplaar van SQL Server.  

## <a name="prepare-a-clustered-sql-server-instance-for-the-site-database"></a>Een geclusterd SQL Server-exemplaar voorbereiden voor de sitedatabase  

Hier volgen de belangrijkste taken voltooien om het voorbereiden van uw sitedatabase:

-   Maak de virtuele SQL Server-cluster om de sitedatabase te hosten in een bestaande Windows Server-clusteromgeving. Zie de documentatie die specifiek zijn voor uw versie van SQL Server voor specifieke stappen voor het installeren en instellen van een SQL Server-cluster. Bijvoorbeeld, als u SQL Server 2008 R2 gebruikt, Zie [installeren van een SQL Server 2008 R2-failovercluster](http://go.microsoft.com/fwlink/p/?LinkId=240231).  

-   U kunt een bestand plaatsen in de hoofdmap van ieder station waar u niet wilt dat Configuration Manager site-onderdelen installeren op elke computer in het SQL Server-cluster. De naam van het bestand moet **NO_SMS_ON_DRIVE.SMS**. Configuration Manager installeert standaard enkele onderdelen op elk fysiek knooppunt om bewerkingen zoals back-ups te ondersteunen.  

-   Voeg het computeraccount van de siteserver toe aan de groep **Lokale beheerders** van iedere Windows Server-clusterknooppuntcomputer.  

-   Wijs in het virtuele SQL Server-exemplaar de **sysadmin** SQL Server-rol aan de gebruikersaccount waarmee setup van Configuration Manager wordt uitgevoerd.  

### <a name="to-install-a-new-site-using-a-clustered-sql-server"></a>Een nieuwe site installeren met een geclusterde SQL Server  
 Voer uw normale proces voor het installeren van een site met de volgende afwijking na installatie van Configuration Manager voor het installeren van een site die gebruikmaakt van een geclusterde sitedatabase:  

-   Geef op de pagina **Databasegegevens** de naam op van het virtuele SQL Server-clusterexemplaar waarop de sitedatabase wordt gehost. De naam van de computer waarop SQL Server wordt uitgevoerd, wordt vervangen door het virtuele exemplaar.  

    > [!IMPORTANT]  
    >  Wanneer u de naam van het virtuele SQL Server-clusterexemplaar invoert, voer dan niet de naam in van het virtuele Windows Server-exemplaar dat is gemaakt door de Windows Server-cluster. Als u de naam van de virtuele Windows-Server gebruikt, wordt de sitedatabase geïnstalleerd op de lokale vaste schijf van de actieve Windows Server-clusterknooppunt. Dit heeft tot gevolg dat er geen juiste failover plaatsvindt, als dit knooppunt uitvalt.  
