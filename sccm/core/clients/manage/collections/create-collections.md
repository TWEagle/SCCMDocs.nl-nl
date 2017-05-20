---
title: Verzamelingen maken | Microsoft-documenten
description: Maken van verzamelingen in System Center Configuration Manager eenvoudiger groepen van gebruikers en apparaten te beheren.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1401a35e-4312-4d3b-8ceb-0abbb10d4f05
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: dee63826d8e6100f5b8402952175106076585030
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-collections-in-system-center-configuration-manager"></a>Het maken van verzamelingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Verzamelingen zijn groepen gebruikers of apparaten. Gebruik verzamelingen voor taken zoals het beheer van toepassingen, instellingen voor naleving implementeren of bij het installeren van software-updates. U kunt verzamelingen ook gebruiken om groepen clientinstellingen te beheren of te gebruiken met op rollen gebaseerd beheer om de resources op te geven waartoe een gebruiker met beheerdersrechten toegang heeft. Configuration Manager bevat verschillende ingebouwde verzamelingen. Zie voor meer informatie [Inleiding tot verzamelingen in System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md).  

> [!NOTE]  
>  Een verzameling kan bevatten, gebruikers of apparaten, maar niet beide.  

 De volgende tabel bevat de regels die u gebruiken kunt voor het configureren van de leden van een verzameling in Configuration Manager.  

|Type lidmaatschapsregel|Meer informatie|  
|--------------------------|----------------------|  
|Directe regel|Gebruiken om de gebruikers of computers die u wilt toevoegen aan een verzameling te kiezen. Lidmaatschap van deze verandert niet, tenzij u een bron van Configuration Manager verwijdert. Configuration Manager moet de resources hebben gevonden of u moet geïmporteerde resources voordat u ze aan de verzameling van een directe regel toevoegen kunt. Directe regel verzamelingen hebben een hogere administratieve overhead dan regel queryverzamelingen omdat deze vereisen dat handmatige wijzigingen.|  
|Queryregel|Het lidmaatschap van een verzameling op basis van een query die Configuration Manager wordt uitgevoerd volgens een schema dynamisch bijwerken. U kunt bijvoorbeeld een verzameling gebruikers maken die lid zijn van de organisatie-eenheid Human Resources in Active Directory Domain Services. Deze verzameling wordt automatisch bijgewerkt wanneer nieuwe gebruikers zijn toegevoegd aan of verwijderd uit de afdeling Personeelszaken.<br /><br /> Bijvoorbeeld query's die u kunt gebruiken voor het bouwen van verzamelingen, Zie [het maken van query's in System Center Configuration Manager](../../../../core/servers/manage/create-queries.md).|  
|Regel voor opnemen van verzameling|De leden van een andere verzameling opnemen in een Configuration Manager-verzameling die het lidmaatschap van de huidige verzameling wordt bijgewerkt volgens een planning als de opgenomen verzameling wordt gewijzigd.<br /><br /> U kunt meerdere regels voor het opnemen van verzamelingen toevoegen aan een verzameling.<br /> |  
|Regel voor uitsluiten van verzameling|De uitsluitingsregel voor de verzameling kunt u de leden van een andere verzameling uitsluiten van een Configuration Manager-verzameling. Het lidmaatschap van de huidige verzameling wordt bijgewerkt volgens een planning als de uitgesloten verzameling wordt gewijzigd.<br /><br /> U kunt meerdere regels voor het uitsluiten van een verzameling toevoegen aan een verzameling. Als een verzameling bevat beide verzameling opnemen en uitsluiten van regels voor het verzamelen en heeft een conflict, wordt de uitsluitingsregel voor de verzameling prioriteit krijgt.<br />              **Voorbeeld:** U maakt een verzameling die een regel voor het verzamelen en een uitsluitingsregel voor de verzameling. De regel voor het opnemen van een verzameling is bedoeld voor een verzameling Dell-desktopcomputers. De uitsluitingsverzameling is een verzameling computers met minder dan 4 GB RAM-geheugen. De nieuwe verzameling bevat Dell-desktopcomputers met minstens 4 GB RAM-geheugen.|  

 Gebruik de volgende procedures bij het maken van verzamelingen in Configuration Manager. U kunt ook de verzamelingen die zijn gemaakt op deze of een andere Configuration Manager-site importeren. Zie voor meer informatie over het exporteren en importeren van verzamelingen [beheren in System Center Configuration Manager-verzamelingen](../../../../core/clients/manage/collections/manage-collections.md).  

 Zie voor meer informatie over het maken van verzamelingen voor computers waarop Linux en UNIX [clients voor Linux en UNIX-servers in System Center Configuration Manager beheren](../../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md).  

##  <a name="BKMK_1"></a> Een apparaatverzameling maken  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Apparaatverzamelingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Apparaatverzameling maken**.  

4.  Op de **algemeen** -pagina bevatten een **naam** en een **Opmerking**. Klik op **beperkende verzameling**, kies **Bladeren** om een beperkende verzameling te selecteren. De verzameling bevat alleen leden van de beperkende verzameling.  

5.  Op de **lidmaatschapsregels** pagina van de **apparaat verzameling Wizard maken**in de **regel toevoegen** , selecteert u het type van de abonnementsregel die u wilt gebruiken voor deze verzameling. U kunt meerdere regels voor elke verzameling configureren.  

        
        ##### To configure a direct rule  

        1.  Geef op de pagina **Zoeken naar resources** van de wizard **Regel voor direct lidmaatschap maken**de volgende gegevens op:  

            -   **Bronklasse**: Selecteer het type van de resource die u wilt zoeken en toevoegen aan de verzameling. Selecteer waarden bij **Systeembron** om te zoeken naar inventarisgegevens die zijn geretourneerd door clientcomputers of bij **Onbekende computer** om een keuze te maken uit waarden die zijn geretourneerd door onbekende computers.  

            -   **De naam van kenmerk**: Selecteer het kenmerk dat is gekoppeld aan de geselecteerde bronklasse die u wilt zoeken. Als u bijvoorbeeld computers wilt selecteren op basis van hun NetBIOS-naam, selecteert u **Systeembron** in de lijst **Resourceklasse** en **NetBIOS-naam** in de lijst **Kenmerknaam** .  

            -   **Resources die als verouderd gemarkeerd uitsluiten** - als een clientcomputer is gemarkeerd als verouderd, moet u deze waarde niet opnemen in de zoekresultaten.  

            -   **Resources die geen Configuration Manager-client geïnstalleerd uitsluiten** -deze worden niet weergegeven in de zoekresultaten.  

            -   **Waarde:** Voer een waarde die u wilt zoeken naam van het geselecteerde kenmerk. U kunt het percentageteken **%** als een jokerteken gebruiken. Voer bijvoorbeeld om te zoeken naar computers met een NetBIOS-naam die begint met "M", **M %** in dit veld.  

        2.  Op de **Selecteer Resources** pagina, selecteer de resources die u wilt toevoegen aan de verzameling in de **Resources** lijst en kies vervolgens **volgende**.  


        ##### To configure a query rule  

        1.  Geef in het dialoogvenster **Queryregeleigenschappen** de volgende gegevens op:  

            -   **Naam**: Geef een unieke naam.  

            -   **Query-instructie importeren** -Hiermee opent u de **bladeren Query** waarin u kunt selecteren in het dialoogvenster een [Configuration Manager-query](../../../../core/servers/manage/create-queries.md) gebruiken als de queryregel voor de verzameling.   

            -   **Bronklasse:** Selecteer het type van de resource die u wilt zoeken en toevoegen aan de verzameling. Selecteer een waarde bij **Systeembron** om te zoeken naar inventarisgegevens die zijn geretourneerd door clientcomputers of bij **Onbekende computer** om een keuze te maken uit waarden die zijn geretourneerd door onbekende computers.  

            -   **Query-instructie bewerken** -Hiermee opent u de **Query-instructie eigenschappen** waar u een query wilt gebruiken als de regel voor de verzameling van kunt maken in het dialoogvenster. Voor meer informatie over query’s, zie [Technische documentatie over query’s in System Center Configuration Manager](../../../../core/servers/manage/queries-technical-reference.md).  

    
        ##### To configure an include collection rule  

        In the **Select Collections** dialog box, select the collections you want to include in the new collection, then choose **OK**.  

        ##### To configure an exclude collection rule  

        In the **Select Collections** dialog box, select the collections you want to exclude from the new collection, then choose **OK**.  

    -   **Incrementele updates gebruiken voor deze verzameling** : Selecteer deze optie om periodiek controleren en bijwerken alleen nieuwe of gewijzigde resources uit de vorige evaluatie van verzamelingen, onafhankelijk van een volledige verzamelingsevaluatie. Incrementele updates worden om de tien minuten uitgevoerd.  

        > [!IMPORTANT]  
        >  Verzamelingen die zijn geconfigureerd met queryregels die de volgende klassen gebruiken, ondersteunen geen incrementele updates.  
        >   
        >  -   SMS_G_System_CollectedFile  
        > -   SMS_G_System_LastSoftwareScan  
        > -   SMS_G_System_AppClientState  
        > -   SMS_G_System_DCMDeploymentState  
        > -   SMS_G_System_DCMDeploymentErrorAssetDetails  
        > -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
        > -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
        > -   SMS_G_User_DCMDeploymentCompliantAssetDetails (alleen voor verzamelingen van gebruikers)  
        > -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails (alleen voor verzamelingen van gebruikers)  
        > -   SMS_G_System_SoftwareUsageData  
        > -   SMS_G_System_CI_ComplianceState  
        > -   SMS_G_System_EndpointProtectionStatus  
        > -   SMS_GH_System_*  
        > -   SMS_GEH_System_*  

    -   **Plannen van een volledige update op deze verzameling** -een normale volledige evaluatie van het lidmaatschap van verzameling plannen.  

6.  Voltooi de wizard om de nieuwe verzameling te maken. De nieuwe verzameling wordt weergegeven in het knooppunt **Apparaatverzamelingen** van de werkruimte **Activa en naleving** .  

> [!NOTE]  
>  U moet vernieuwen of vernieuw de Configuration Manager-console om te zien van de leden van de verzameling. Echter, de leden niet weergegeven in de verzameling pas na de eerste geplande update of als u handmatig selecteren **bijwerken lidmaatschap** voor de verzameling. Het kan enkele minuten duren voordat een verzameling-update te voltooien.  

##  <a name="BKMK_2"></a> Een gebruikersverzameling maken  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Gebruikersverzamelingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Gebruikersverzameling maken**.  

4.  Op de **algemeen** pagina van de wizardprovide een **naam** en een **Opmerking**. Klik op **beperkende verzameling**, kies **Bladeren** om een beperkende verzameling te selecteren. De verzameling bevat alleen leden van de beperkende verzameling.  

5.  Op de **lidmaatschapsregels** pagina, geeft u de volgende:  

    -   Selecteer in de lijst **Regel toevoegen** het type lidmaatschapsregel dat u wilt gebruiken voor deze verzameling. U kunt meerdere regels voor elke verzameling configureren.  

         ##### <a name="to-configure-a-direct-rule"></a>Een directe regel configureren  

        1.  Op de **zoeken naar bronnen** pagina van de **Direct lidmaatschap Wizard regel**, opgeven:  

            -   **Bronklasse**: Selecteer het type van de resource die u wilt zoeken en toevoegen aan de verzameling. Selecteer een van **gebruikersbron** waarden om te zoeken naar gebruikersgegevens verzameld door Configuration Manager of **groep gebruikersbron** om te zoeken naar gebruiker groepsinformatie verzameld door Configuration Manager.  

            -   **De naam van kenmerk**: Selecteer het kenmerk dat is gekoppeld aan de bronklasse die u wilt zoeken. Als u bijvoorbeeld gebruikers wilt selecteren op basis van de naam van de organisatie-eenheid, selecteert u **Gebruikersbron** in de lijst **Resourceklasse** en **Naam van gebruikers-OE** in de lijst **Kenmerknaam** .  

            -   **Waarde:** Voer een waarde die u wilt zoeken. U kunt het percentageteken **%** als een jokerteken gebruiken. Voer bijvoorbeeld om te zoeken naar gebruikers in de OU Contoso, **Contoso** in dit veld.  

        2.  Op de **Selecteer Resources** pagina, selecteer de resources die u wilt toevoegen aan de verzameling in de **Resources** lijst.  

        ##### <a name="to-configure-a-query-rule"></a>Een queryregel configureren  

        1.  In de **Query regeleigenschappen** dialoogvenster bieden:  

            -   **Naam**: Een unieke naam.  

            -   **Query-instructie importeren** -Hiermee opent u de **bladeren Query** waarin u kunt selecteren in het dialoogvenster een [Configuration Manager-query](../../../../core/servers/manage/queries-technical-reference.md) gebruiken als de queryregel voor de verzameling.  

            -   **Bronklasse**: Selecteer het type van de resource die u wilt zoeken en toevoegen aan de verzameling. Selecteer een van **gebruikersbron** waarden om te zoeken naar gebruikersgegevens verzameld door Configuration Manager of **groep gebruikersbron** om te zoeken naar gebruiker groepsinformatie verzameld door Configuration Manager.  

            -   **Query-instructie bewerken** -opent de **Query-instructie eigenschappen** u kunt in het dialoogvenster [ontwerpen van een query](../../../../core/servers/manage/queries-technical-reference.md) gebruiken als de regel voor de verzameling.  

        ##### <a name="to-configure-an-include-collection-rule"></a>Een regel voor het opnemen van een verzameling configureren  

        In de **verzamelingen selecteren** dialoogvenster Selecteer de verzamelingen die u wilt opnemen in de nieuwe verzameling en kies vervolgens **OK**.  

        ##### <a name="to-configure-an-exclude-collection-rule"></a>Een regel voor het uitsluiten van een verzameling configureren  

        In de **verzamelingen selecteren** dialoogvenster Selecteer de verzamelingen die u wilt uitsluiten van de nieuwe verzameling en kies vervolgens **OK**.  


    -   **Incrementele updates gebruiken voor deze verzameling** : Selecteer deze optie om periodiek controleren en bijwerken alleen nieuwe of gewijzigde resources uit de vorige evaluatie van verzamelingen, onafhankelijk van een volledige verzamelingsevaluatie. Incrementele updates worden om de tien minuten uitgevoerd.  

        > [!IMPORTANT]  
        >  Verzamelingen die zijn geconfigureerd met queryregels die de volgende klassen gebruiken, ondersteunen geen incrementele updates.  
        >   
        >  -   SMS_G_System_CollectedFile  
        > -   SMS_G_System_LastSoftwareScan  
        > -   SMS_G_System_AppClientState  
        > -   SMS_G_System_DCMDeploymentState  
        > -   SMS_G_System_DCMDeploymentErrorAssetDetails  
        > -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
        > -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
        > -   SMS_G_User_DCMDeploymentCompliantAssetDetails (alleen voor verzamelingen van gebruikers)  
        > -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails (alleen voor verzamelingen van gebruikers)  
        > -   SMS_G_System_SoftwareUsageData  
        > -   SMS_G_System_CI_ComplianceState  
        > -   SMS_G_System_EndpointProtectionStatus  
        > -   SMS_GH_System_*  
        > -   SMS_GEH_System_*  

    -   **Plannen van een volledige update op deze verzameling** -een normale volledige evaluatie van het lidmaatschap van verzameling plannen.  

6.  Voltooi de wizard. De nieuwe verzameling wordt weergegeven in het knooppunt **Gebruikersverzamelingen** van de werkruimte **Activa en naleving** .  

> [!NOTE]  
>  U moet vernieuwen of vernieuw de Configuration Manager-console om te zien van de leden van de verzameling. De leden worden echter pas in de verzameling weergegeven na de eerste geplande update of als u **Lidmaatschap bijwerken** handmatig selecteert voor de verzameling. Het kan enkele minuten duren voordat een verzameling-update te voltooien.  

##  <a name="BKMK_3"></a> Een verzameling importeren  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Gebruikersverzamelingen** of **Apparaatverzamelingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **verzamelingen importeren**.  

4.  Op de **algemeen** pagina van de **Wizard verzamelingen importeren**, kies **volgende**.  

5.  Op de **MOF-bestandsnaam** pagina, kiest u **Bladeren** en blader vervolgens naar het MOF-bestand met de verzameling gegevens die u wilt importeren.  

    > [!NOTE]  
    >  Het bestand dat u wilt importeren moet zijn geëxporteerd uit een waarop dezelfde versie van Configuration Manager als deze site. Zie voor meer informatie over het exporteren van verzamelingen [beheren in System Center Configuration Manager-verzamelingen](../../../../core/clients/manage/collections/manage-collections.md).  

6.  Voltooi de wizard om de verzameling te importeren. De nieuwe verzameling wordt weergegeven in het knooppunt **Gebruikersverzamelingen** of **Apparaatverzamelingen** van de werkruimte **Activa en naleving** . Vernieuwen of vernieuw de Configuration Manager-console om te zien van de leden van de verzameling voor de zojuist geïmporteerde verzameling.  

