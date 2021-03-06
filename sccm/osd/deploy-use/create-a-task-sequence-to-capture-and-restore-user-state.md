---
title: Maak een takenreeks voor het vastleggen en herstellen van gebruikersstatus
titleSuffix: Configuration Manager
description: Gebruik System Center Configuration Manager vastleggen en herstellen van gebruikersstatusgegevens in scenario's voor besturingssysteemimplementaties takenreeksen.
ms.custom: na
ms.date: 06/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d566d85c-bf7a-40e7-8239-57640a1db5f4
caps.latest.revision: "7"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 3fb30240c7d926657e01a4b9e03cef38fd2ee128
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="create-a-task-sequence-to-capture-and-restore-user-state-in-system-center-configuration-manager"></a>Maak een takenreeks voor het vastleggen en herstellen van gebruikersstatus in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt System Center Configuration Manager-takenreeksen gebruiken vastleggen en herstellen van de gebruikersstatusgegevens in implementatiescenario's van besturingssysteem waar u wilt bewaren van de gebruikersstatus van het huidige besturingssysteem. Afhankelijk van het type takenreeks dat u wilt maken, worden de stappen voor het vastleggen en terugzetten automatisch toegevoegd als onderdeel van de takenreeks. In andere situaties moet u de stappen voor het vastleggen en terugzetten misschien handmatig toevoegen. In dit onderwerp worden de stappen beschreven die u aan een bestaande takenreeks moet toevoegen om gebruikersstatusgegevens vast te leggen en terug te zetten.  

##  <a name="BKMK_CaptureRestoreUserState"></a> Gebruikersstatusgegevens vastleggen en terugzetten  
 Als u de gebruikersstatus wilt vastleggen en terugzetten, moet u de volgende stappen aan de takenreeks toevoegen:  

-   **Statusopslag opvragen**: Deze stap is alleen nodig als u de gebruikersstatus op het statusmigratiepunt opslaat.  

-   **Gebruikersstatus vastleggen**: Deze stap legt de gebruikersstatusgegevens vast en slaat deze op het statusmigratiepunt of lokaal via koppelingen.  

-   **Gebruikersstatus herstellen**: Deze stap herstelt de gebruikersstatusgegevens op de doelcomputer. Hiermee kunnen de gegevens van een gebruikersstatusmigratiepunt of van de doelcomputer worden opgehaald.  

-   **Statusopslag vrijgeven**: Deze stap is alleen nodig als u de gebruikersstatus op het statusmigratiepunt opslaat. Deze stap verwijdert deze gegevens uit het statusmigratiepunt.  

 Gebruik de volgende procedures om de takenreeksstappen toe te voegen die nodig zijn om de gebruikersstatus vast te leggen en te herstellen. Zie voor meer informatie over het maken van een takenreeks [beheren van takenreeksen om taken te automatiseren](manage-task-sequences-to-automate-tasks.md).  

#### <a name="to-add-task-sequence-steps-to-capture-the-user-state"></a>Toevoegen van takenreeksstappen voor het vastleggen van de gebruikersstatus  

1.  Selecteer een takenreeks uit de lijst **Takenreeks** en klik vervolgens op **Bewerken**.  

2.  Voeg de stap **Statusopslag opvragen** toe als u een statusmigratiepunt gebruikt om de gebruikersstatus op te slaan. Klik op **Toevoegen** in het dialoogvenster **Takenreekseditor**, ga naar **Gebruikersstatus**en klik vervolgens op **Statusopslag opvragen**. Geef de volgende eigenschappen en opties op voor de stap **Statusopslag opvragen** en klik vervolgens op **Toepassen**.  

     Geef op het tabblad **Eigenschappen** de volgende opties op:  

    -   Voer een naam en beschrijving in voor de stap.  

    -   Klik op **Status van de computer vastleggen**.  

    -   Geef in het vak **Aantal pogingen** het aantal keren op dat de takenreeks moet proberen de gebruikersstatusgegevens vast te leggen als er een fout optreedt.  

    -   Geef, in het vak **Wachttijd nieuwe poging (seconden)** , op hoeveel seconden de takenreeks moet wachten voordat er een nieuwe poging wordt ondernomen om de gegevens vast te leggen.  

    -   Selecteer de **als het computeraccount geen verbinding maken met Statusopslag, het netwerktoegangsaccount gebruiken** selectievakje in om aan te geven of de Configuration Manager [netwerktoegangsaccount](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#bkmk_NAA) verbinding maken met de Statusopslag.  

     Specificeer op het tabblad **Opties** de volgende opties:  

    -   Selecteer het selectievakje **Doorgaan bij fout** als u de takenreeks wilt laten doorgaan naar de volgende stap als deze stap mislukt.  

    -   Geef eventueel voorwaarden op waaraan moet worden voldaan voordat de takenreeks kan doorgaan als een fout optreedt.  

3.  Voeg de stap **Gebruikersstatus vastleggen** toe aan de takenreeks. Klik op **Toevoegen** in het dialoogvenster **Takenreekseditor**, ga naar **Gebruikersstatus**en klik vervolgens op **Gebruikersstatus vastleggen**. Geef de volgende eigenschappen en opties op voor de stap **Gebruikersstatus vastleggen** en klik vervolgens op **OK**.  

    > [!IMPORTANT]  
    >  Stel ook de takenreeksvariabele **OSDStateStorePath** in wanneer u deze stap toevoegt aan uw takenreeks om aan te duiden waar de gebruikersstatusgegevens worden opgeslagen. Als u de gebruikersstatus lokaal opslaat, dient u geen hoofdmap op te geven omdat dit ervoor kan zorgen dat de takenreeks niet kan worden uitgevoerd. Gebruik altijd een map of submap wanneer u de gebruikersgegevens lokaal opslaat. Zie voor meer informatie over deze variabele [vastleggen gebruiker State Task Sequence Action Variables](../understand/task-sequence-action-variables.md#BKMK_CaptureUserState).  

     Geef op het tabblad **Eigenschappen** de volgende opties op:  

    -   Voer een naam en beschrijving in voor de stap.  

    -   Geef het pakket op dat het USMT-bronbestand bevat dat wordt gebruikt om de gebruikersstatusgegevens vast te leggen.  

    -   Geef de gebruikersprofielen op voor het vastleggen van:  

        -   Klik op **Alle gebruikersprofielen vastleggen met standaardopties** om alle gebruikersprofielen vast te leggen.  

        -   Klik op **Vastlegging van gebruikersprofiel aanpassen** om individuele gebruikersprofielen op te geven om vast te leggen. Selecteer het configuratiebestand (miguser.xml, migsys.xml of migapp.xml) die de gebruikersprofielgegevens bevat. Het configuratiebestand config.xml hier niet gebruiken, maar u kunt het handmatig toevoegen aan de USMT-opdrachtregel met behulp van de variabelen OSDMigrageAdditionalCaptureOptions en OSDMigrateAdditionalRestoreOptions.

    -   Selecteer **Uitgebreide logboekregistratie inschakelen** om op te geven hoeveel informatie er naar de logboekbestanden moet worden geschreven als er een fout optreedt.  

    -   Selecteer **Bestanden die het Encrypting File System (EFS) gebruiken overslaan**.  

    -   Selecteer **Kopiëren door toegang tot bestandssysteem** om de volgende instellingen op te geven:  

        -   **Doorgaan als sommige bestanden niet kunnen worden vastgelegd**: Deze instelling kunt de takenreeksstap om door te gaan van het migratieproces, zelfs als sommige bestanden kunnen niet worden vastgelegd. De takenreeksstap mislukt als u deze optie uitschakelt en als er een bestand niet kan worden vastgelegd. Deze optie is standaard ingeschakeld.  

        -   **Lokaal vastleggen met koppelingen in plaats van door bestanden te kopiëren**: Deze instelling kunt u de migratiefunctie voor vaste koppelingen die beschikbaar is in USMT 4.0 gebruiken. Deze instelling wordt genegeerd als u USMT-versies gebruikt die ouder zijn dan USMT 4.0.  

        -   **Vastleggen in offline modus (alleen Windows PE)**: Deze instelling kunt u gebruikersstatus vastleggen vanuit Windows PE zonder op te starten naar het bestaande besturingssysteem. Deze instelling wordt genegeerd als u USMT-versies gebruikt die ouder zijn dan USMT 4.0.  

    -   Selecteer **Vastleggen met Volume Copy Shadow Service (VSS)**. Deze instelling wordt genegeerd als u USMT-versies gebruikt die ouder zijn dan USMT 4.0.  

     Specificeer op het tabblad **Opties** de volgende opties:  

    -   Selecteer het selectievakje **Doorgaan bij fout** als u de takenreeks wilt laten doorgaan naar de volgende stap als deze stap mislukt.  

    -   Geef eventueel voorwaarden op waaraan moet worden voldaan voordat de takenreeks kan doorgaan als een fout optreedt.  

4.  Als u een statusmigratiepunt gebruikt voor het opslaan van de gebruikersstatus, voegt de [Statusopslag vrijgeven](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) stap in de takenreeks wordt uitgevoerd. Klik in het dialoogvenster **Takenreekseditor** op **Toevoegen**wijs **Gebruikersstatus**aan en klik daarna op **Statusopslag vrijgeven**. Geef de volgende eigenschappen en opties voor de stap **Statusopslag vrijgeven** op en klik daarna op **OK**.  

    > [!IMPORTANT]  
    >  De takenreeksactie die vóór de stap **Statusopslag vrijgeven** wordt uitgevoerd, moet zijn gelukt voordat de stap **Statusopslag vrijgeven** is gestart.  

     Voer op het tabblad **Eigenschappen** een naam en beschrijving in voor de stap.  

     Specificeer op het tabblad **Opties** de volgende opties.  

    -   Selecteer het selectievakje **Doorgaan bij fout** als u de takenreeks wilt laten doorgaan naar de volgende stap als deze stap mislukt.  

    -   Geef eventueel voorwaarden op waaraan moet worden voldaan voordat de takenreeks kan doorgaan als een fout optreedt.  

 Implementeer deze takenreeks om de gebruikersstatus op een doelcomputer vast te leggen. Zie voor meer informatie over het implementeren van takenreeksen [een takenreeks implementeert](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

#### <a name="to-add-task-sequence-steps-to-restore-the-user-state"></a>Takenreeksstappen toevoegen om de gebruikersstatus te herstellen  

1.  Selecteer een takenreeks uit de lijst **Takenreeks** en klik vervolgens op **Bewerken**.  

2.  Voeg de [gebruikersstatus herstellen](../understand/task-sequence-steps.md#BKMK_RestoreUserState) stap in de takenreeks wordt uitgevoerd. Klik in het dialoogvenster **Takenreekseditor** op **Toevoegen**wijs **Gebruikersstatus**aan en klik daarna op **Gebruikersstatus herstellen**. Deze stap brengt een verbinding tot stand met het statusmigratiepunt. Geef de volgende eigenschappen en opties voor de stap **Gebruikersstatus herstellen** op en klik daarna op **OK**.  

     Specificeer op het tabblad **Eigenschappen** de volgende eigenschappen:  

    -   Voer een naam en beschrijving in voor de stap.  

    -   Geef het pakket op dat de USMT bevat om de gebruikersstatusgegevens te herstellen.  

    -   Geef de gebruikersprofielen op die u wilt herstellen:  

        -   Klik op **Alle geregiistreerde gebruikersprofielen met standaardopties herstellen** om alle gebruikersprofielen te herstellen.  

        -   Klik op **herstellen van het gebruikersprofiel aanpassen** om afzonderlijke gebruikersprofielen te herstellen. Selecteer het configuratiebestand (miguser.xml, migsys.xml of migapp.xml) die de gebruikersprofielgegevens bevat. Het configuratiebestand config.xml hier niet gebruiken, maar u kunt het handmatig toevoegen aan de USMT-opdrachtregel met behulp van de variabelen OSDMigrageAdditionalCaptureOptions en OSDMigrateAdditionalRestoreOptions.

    -   Selecteer **Gebruikersprofielen op lokale computers herstellen** om te voorzien in een nieuw wachtwoord voor de herstelde profielen. U kunt geen wachtwoorden voor lokale profielen migreren.  

        > [!NOTE]  
        >  Wanneer u lokale gebruikersaccounts hebt, en u gebruikt de [gebruikersstatus vastleggen](../understand/task-sequence-steps.md#BKMK_CaptureUserState) stap en selecteer **alle gebruikersprofielen met standaardopties vastleggen**, moet u de **gebruikersprofielen lokale computer herstellen** instellen in de [gebruikersstatus herstellen](../understand/task-sequence-steps.md#BKMK_RestoreUserState) stap of de takenreeks mislukt.  

    -   Selecteer **Doorgaan als bestanden niet kunnen worden hersteld** als u wilt dat de stap **Gebruikersstatus herstellen** doorgaat als een bestand niet kan worden hersteld.  

         Als u de gebruikersstatus opslaat door middel van lokale koppelingen en herstellen is mislukt, kan de gebruiker met beheerdersrechten handmatig de vaste koppelingen verwijderen die zijn gemaakt om de gegevens op te slaan of u kunt de takenreeks het hulpprogramma USMTUtils laten uitvoeren. Als u met behulp van USMTUtils de vaste koppeling verwijdert, voegt u een [Computer opnieuw opstarten](../understand/task-sequence-steps.md#BKMK_RestartComputer) stap nadat u USMTUtils hebt uitgevoerd.  

    -   Selecteer **Uitgebreide logboekregistratie inschakelen** om op te geven hoeveel informatie er naar de logboekbestanden moet worden geschreven als er een fout optreedt.  

     Specificeer op het tabblad **Opties** de volgende opties:  

    -   Selecteer het selectievakje **Doorgaan bij fout** als u de takenreeks wilt laten doorgaan naar de volgende stap als deze stap mislukt.  

    -   Geef eventueel voorwaarden op waaraan moet worden voldaan voordat de takenreeks kan doorgaan als een fout optreedt.  

3.  Als u een statusmigratiepunt gebruikt voor het opslaan van de gebruikersstatus, voegt de [Statusopslag vrijgeven](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) stap in de takenreeks wordt uitgevoerd. Klik in het dialoogvenster **Takenreekseditor** op **Toevoegen**wijs **Gebruikersstatus**aan en klik daarna op **Statusopslag vrijgeven**. Geef de volgende eigenschappen en opties voor de stap **Statusopslag vrijgeven** op en klik daarna op **OK**.  

    > [!IMPORTANT]  
    >  De takenreeksactie die vóór de stap **Statusopslag vrijgeven** wordt uitgevoerd, moet zijn gelukt voordat de stap **Statusopslag vrijgeven** is gestart.  

     Voer op het tabblad **Eigenschappen** een naam en beschrijving in voor de stap.  

     Specificeer op het tabblad **Opties** de volgende opties.  

    -   Selecteer het selectievakje **Doorgaan bij fout** als u de takenreeks wilt laten doorgaan naar de volgende stap als deze stap mislukt.  

    -   Geef eventueel voorwaarden op waaraan moet worden voldaan voordat de takenreeks kan doorgaan als een fout optreedt.  

 Implementeer deze takenreeks om de gebruikersstatus op de doelcomputer te herstellen. Zie voor meer informatie over het implementeren van takenreeksen [een takenreeks implementeert](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

## <a name="next-steps"></a>Volgende stappen
[Monitor voor de takenreeksimplementatie](monitor-operating-system-deployments.md#BKMK_TSDeployStatus)
