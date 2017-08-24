---
title: Gebruikersstatus - Configuration Manager beheren | Microsoft Docs
description: System Center Configuration Manager maakt gebruik van User State Migration Tool vastleggen en herstellen van gebruikersstatusgegevens in implementatiescenario's van besturingssysteem.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8d5c345-1e91-410b-b8a9-0170dcfa846e
caps.latest.revision: "12"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: a0bd86587669c32377b1eafa6a890d37e10ac3f6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-user-state-in-system-center-configuration-manager"></a>De gebruikersstatus beheren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt System Center Configuration Manager-takenreeksen gebruiken vastleggen en herstellen van de gebruikersstatusgegevens in implementatiescenario's van besturingssysteem waar u wilt bewaren van de gebruikersstatus van het huidige besturingssysteem. Bijvoorbeeld:  

-   Implementaties waarbij u de gebruikersstatus wilt vastleggen van één computer om deze terug te zetten op een andere computer.  

-   Werk implementaties bij waarvan u de gebruikersstatus op dezelfde computer wilt vastleggen en herstellen.  

 Configuration Manager gebruikt User State Migration Tool (USMT) 10.0 voor het beheren van de migratie van gebruikersstatusgegevens van een broncomputer naar een doelcomputer nadat de installatie van het besturingssysteem is voltooid. Zie  [Algemene migratiescenario's](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)voor meer informatie over algemene migratiescenario's voor USMT 10.0.  

 Gebruik de volgende secties voor hulp bij het vastleggen en herstellen van gebruikersgegevens.


##  <a name="BKMK_StoringUserData"></a> Het opslaan van gebruikersstatusgegevens  
 Wanneer u de gebruikersstatus vastlegt, kunt u de gebruikersstatusgegevens opslaan op de doelcomputer of op een statusmigratiepunt. Als u wilt de gebruikersstatus opslaat op een gebruikersstatusmigratiepunt, moet u een Configuration Manager-sitesysteemserver die als host fungeert voor de status van migratie sitesysteemrol. U moet, om de gebruikersstatus op de doelcomputer op te slaan, uw takenreeks configureren om de gegevens lokaal op te slaan met behulp van koppelingen.  

> [!NOTE]  
>  De koppelingen die worden gebruikt om de gebruikersstatus lokaal op te slaan, worden vaste koppelingen genoemd. Vaste koppelingen zijn een optie van USMT 10.0 waarmee er op de computer wordt gescand naar gebruikersbestanden en -instellingen en er vervolgens een directory van vaste koppelingen naar die bestanden wordt gemaakt. De vaste koppelingen worden vervolgens gebruikt om de gebruikersgegevens te herstellen na implementatie van het nieuwe besturingssysteem.  

> [!IMPORTANT]  
>  U kunt geen statusmigratie gebruiken en wel vaste koppelingen om de gebruikersstatusgegevens op hetzelfde moment op te slaan.  

 Als de gebruikersstatusinformatie wordt vastgelegd, kan de informatie op een van de volgende manieren worden opgeslagen:  

-   U kunt de gebruikersstatusgegevens extern opslaan door een statusmigratiepunt te configureren. Met de takenreeks **Vastleggen** worden de gegevens naar het statusmigratiepunt verzonden. Nadat het besturingssysteem is geïmplementeerd, worden met de takenreeks **Terugzetten** de gegevens opgehaald en wordt de gebruikersstatus op de doelcomputer teruggezet.  

-   U kunt de gebruikersstatusgegevens lokaal opslaan op een specifieke locatie. In dit scenario worden met de takenreeks **Vastleggen** de gebruikersgegevens naar een specifieke locatie op de doelcomputer gekopieerd. Nadat het besturingssysteem vervolgens is geïmplementeerd, worden met de takenreeks **Terugzetten** de gebruikersgegevens van die locatie opgehaald.  

-   U kunt vaste koppelingen opgeven die kunnen worden gebruikt om de gebruikersgegevens naar de oorspronkelijke locatie te herstellen. In dit scenario blijven de gebruikersstatusgegevens aanwezig op de schijf wanneer het oude besturingssysteem wordt verwijderd. Nadat het nieuwe besturingssysteem vervolgens is geïmplementeerd, worden via de takenreeks **Terugzetten** met de vaste koppelingen de gebruikersstatusgegevens teruggezet op de oorspronkelijke locatie.  

###  <a name="BKMK_UserDataSMP"></a> De gebruikersgegevens opslaan op een statusmigratiepunt  
 Als u de gebruikersstatusgegevens op een statusmigratiepunt wilt opslaan, gaat u als volgt te werk:  

1.  [Configure a state migration point](#BKMK_StateMigrationPoint) om de gebruikersstatusgegevens op te slaan.  

2.  [Create a computer association](#BKMK_ComputerAssociation) tussen de broncomputer en de doelcomputer. U moet deze koppeling maken voordat u de gebruikersstatus op de broncomputer vastlegt.  

3.  [Maak een takenreeks voor het vastleggen en herstellen van gebruikersstatus in System Center Configuration Manager](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md). U moet met name de volgende takenreeksstappen voor het vastleggen van gebruikersgegevens van een computer, de gebruikersdatum op een statusmigratiepunt opslaan en herstellen van de gebruikersgegevens op een computer toevoegen:  

    -   [Statusopslag opvragen](../understand/task-sequence-steps.md#BKMK_RequestStateStore) toegang vragen tot een statusmigratiepunt bij het vastleggen van status van een computer of de status terugzet op een computer.  

    -   [Gebruikersstatus vastleggen](../understand/task-sequence-steps.md#BKMK_CaptureUserState) vastleggen en opslaan van de gebruikersstatusgegevens op het statusmigratiepunt.  

    -   [Gebruikersstatus herstellen](../understand/task-sequence-steps.md#BKMK_RestoreUserState) te herstellen van de status van de gebruiker op de doelcomputer met de gegevens ophaalt uit een gebruikersstatusmigratiepunt.  

    -   [Statusopslag vrijgeven](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) aan het statusmigratiepunt dat het vastleggen of vrijgeven is voltooid.  

###  <a name="BKMK_UserDataDestination"></a> De gebruikersgegevens lokaal opslaan  
 U kunt de gebruikersstatusgegevens als volgt lokaal opslaan:  

-   [Maak een takenreeks voor het vastleggen en herstellen van gebruikersstatus](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md). U moet met name de volgende takenreeksstappen toevoegen om de gebruikersgegevens van een computer vast te leggen en de gebruikersgegevens met vaste koppelingen op een computer terug te zetten:  

    -   [Gebruikersstatus vastleggen](../understand/task-sequence-steps.md#BKMK_CaptureUserState) vastleggen en opslaan van de gebruikersgegevens naar een lokale map met vaste koppelingen.  

    -   [Gebruikersstatus herstellen](../understand/task-sequence-steps.md#BKMK_RestoreUserState) te herstellen van de status van de gebruiker op de doelcomputer met het ophalen van de gegevens via vaste koppelingen.  

        > [!NOTE]  
        >  De gebruikersstatusgegevens waarnaar de vaste koppelingen verwijzen, blijven op de computer nadat de takenreeks het oude besturingssysteem verwijdert. Dit zijn de gegevens die worden gebruikt om de gebruikersstatus op te slaan wanneer het nieuwe besturingssysteem wordt geïmplementeerd.  

##  <a name="BKMK_StateMigrationPoint"></a> Configure a state migration point  
 Op het statusmigratiepunt worden gebruikersstatusgegevens opgeslagen die op de ene computer worden vastgelegd en vervolgens op een andere computer worden hersteld. Wanneer u echter gebruikersinstellingen voor een besturingssysteemimplementatie op dezelfde computer vastlegt, zoals een implementatie waarbij u het besturingssysteem op de doelcomputer vernieuwt, kunt u de gegevens opslaan op dezelfde computer via vaste koppelingen of op een statusmigratiepunt. Bij bepaalde computerimplementaties wanneer u het gegevensarchief maakt maakt Configuration Manager automatisch een koppeling tussen het statusarchief en de doelcomputer. U kunt de volgende methoden gebruiken om een statusmigratiepunt te configureren om de gebruikersstatusgegevens op te slaan:  

-   Gebruik de **wizard Sitesysteemserver maken** om een nieuwe sitesysteemserver te maken voor het statusmigratiepunt.  

-   Gebruik de **wizard Sitesysteemrollen toevoegen** om een statusmigratiepunt toe te voegen aan een bestaande server.  

 Als u deze wizards gebruikt, wordt u gevraagd om de volgende informatie op te geven voor het statusmigratiepunt:  

-   De mappen voor het opslaan van de gebruikersstatusgegevens.  

-   Het maximum aantal clients die gegevens op het statusmigratiepunt kunnen opslaan.  

-   De minimale hoeveelheid vrije schijfruimte voor het statusmigratiepunt om gebruikersstatusgegevens op te slaan.  

-   Het verwijderingsbeleid voor de rol. U kunt opgeven dat de gebruikersstatusgegevens onmiddellijk worden verwijderd nadat ze op een computer zijn hersteld, of na een specifiek aantal dagen nadat de gebruikersgegevens op een computer worden hersteld.  

-   Of het statusmigratiepunt alleen moet reageren op aanvragen om gebruikersstatusgegevens terug te zetten. Wanneer u deze optie inschakelt, kunt het statusmigratiepunt niet gebruiken om de gebruikersstatusgegevens op te slaan.  

 Zie voor meer informatie over het statusmigratiepunt en de stappen voor het configureren van deze [Statusmigratiepunt](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

##  <a name="BKMK_ComputerAssociation"></a> Create a computer association  
 Maak een computerkoppeling om een relatie te definiëren tussen een broncomputer en een doelcomputer wanneer u een besturingssysteem op nieuwe hardware installeert en gebruikersgegevensinstellingen wilt vastleggen en terugzetten. De broncomputer is een bestaande computer die Configuration Manager worden beheerd. Wanneer u het nieuwe besturingssysteem implementeert op de doelcomputer, bevat de broncomputer de gebruikersstatus die is gemigreerd naar de doelcomputer.  

> [!NOTE]  
>  Maak een computerkoppeling tussen computers die zich in een bovenliggende site van Configuration Manager met computers die zich op een onderliggende site wordt niet ondersteund. Computerkoppelingen zijn sitespecifiek en worden niet gerepliceerd.  

#### <a name="to-create-a-computer-association"></a>Een computerkoppeling maken  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik op **Gebruikersstatusmigratie** in de werkruimte **Activa en naleving**.  

3.  Klik op **Computerkoppeling maken** in het tabblad **Start** in de groep **Maken**.  

4.  Geef, op het tabblad **Computerkoppeling** van het dialoogvenster **Eigenschappen computerkoppeling** de broncomputer op met de te vastleggen gebruikersstatus; geef ook de doelcomputer op waarop de gebruikersstatusgegevens moeten worden hersteld.  

5.  Geef, op het tabblad **Gebruikersaccounts** , de gebruikersaccounts op die moeten worden gemigreerd naar de doelcomputer. Geef een van de volgende instellingen op:  

    -   **Vastleggen en herstellen van alle gebruikersaccounts**: Deze instelling vastgelegd en hersteld van alle gebruikersaccounts. Gebruik deze instelling om meerdere koppelingen te maken op dezelfde broncomputer.  

    -   **Alle gebruikersaccounts vastleggen en opgegeven accounts herstellen**: Deze instelling worden alle gebruikersaccounts op de broncomputer vastgelegd en alleen de accounts die u op de doelcomputer opgeeft hersteld. Bovendien kunt u deze instelling gebruiken wanneer u meervoudige koppelingen op dezelfde broncomputer wilt maken.  

    -   **Vastleggen en herstellen van opgegeven gebruikersaccounts**: Deze instelling vastgelegd en hersteld alleen de accounts die u opgeeft. U kunt geen meervoudige koppelingen naar dezelfde broncomputer maken wanneer u deze instelling selecteert.  

##  <a name="BKMK_MigrationFails"></a> Gebruikersstatusgegevens terugzetten wanneer een besturingssysteemimplementatie mislukt  
 Als de implementatie van het besturingssysteem mislukt, kunt u met de functie USMT 10.0 LoadState de gebruikersstatusgegevens ophalen die zijn vastgelegd tijdens de implementatie. Hiertoe behoren ook gegevens die op een statusmigratiepunt zijn opgeslagen en gegevens die lokaal op de doelcomputer zijn opgeslagen. Zie [LoadState Syntax (LoadState-syntax)](https://technet.microsoft.com/library/mt299188\(v=vs.85\).aspx)voor meer informatie over deze USMT-functie.  
