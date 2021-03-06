---
title: Instellingen voor naleving van monitor
titleSuffix: Configuration Manager
description: Een of meer van de procedures in dit onderwerp gebruiken om de status van naleving van de configuratiebasislijn weer te geven.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92c1ccca-a748-44cd-a52e-e41d34bf981d
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 1da8bf6ab83be7c72cc95ec5e07cb9b1a17526d5
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="monitor-compliance-settings-in-system-center-configuration-manager"></a>Instellingen voor naleving in System Center Configuration Manager controleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u hebt System Center Configuration Manager-configuratiebasislijnen geïmplementeerd op apparaten in uw hiërarchie, kunt u een of meer van de procedures in dit onderwerp om de status van naleving van de configuratiebasislijn weer te geven:

> [!NOTE]  
>  De validatiecriteriavelden in de rapporten met instellingen voor naleving (het equivalent van het rapport aan de kant van de client is **Beperkingen**) geven het onderliggende SML (Service Modeling Language) weer. Dit kan het moeilijk maken voor beheerders die het configuratie-item in de Configuration Manager-console om te begrijpen wat de validatiecriteria hebt geschreven als ze geen kennis van SML. In dit geval gebruiken de **bewaking** werkruimte in de Configuration Manager-console om de eigenschappen van het configuratie-item en de validatiecriteria ervan weer te geven.  

##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Nalevingsresultaten weergeven in de Configuration Manager-console  
 Gebruik deze procedure om details te bekijken over de naleving van geïmplementeerde configuratiebasislijnen in de Configuration Manager-console.  

### <a name="view-compliance-results-in-the-configuration-manager-console"></a>Nalevingsresultaten weergeven in de Configuration Manager-console  

1.  Klik in de Configuration Manager-console op **bewaking** > **implementaties**.  

3.  Selecteer in de lijst **Implementaties** de implementatie van de configuratiebasislijn waarvoor u compatibiliteitsgegevens wilt bekijken.  

4.  U kunt samenvattingsinformatie controleren over de naleving van de implementatie van configuratiebasislijnen op de hoofdpagina. Selecteer, om meer gedetailleerde informatie te zien, de implementatie van de configuratiebasislijn en klik dan op het tabblad **Start** , in de groep **Implementatie** op **Status weergeven** om de pagina **Implementatiestatus** te openen.  

     De pagina **Implementatiestatus** bevat de volgende tabbladen:  

    -   **Compatibele**: Geeft de naleving van de configuratiebasislijn op basis van het aantal betrokken activa. U kunt klikken op een regel om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** of het knooppunt **Apparaten** in de werkruimte **Activa en naleving** , die alle gebruikers of apparaten bevat die compatibel zijn met deze regel. Het deelvenster **Activumgegevens** geeft de gebruikers of apparaten weer die compatibel zijn met de configuratiebasislijn. Dubbelklik op een gebruiker of apparaat in de lijst om extra informatie weer te geven.  

        > [!IMPORTANT]  
        >  De regel voor een configuratie-item wordt niet beoordeeld als het is niet gevonden of niet van toepassing op een clientapparaat; de regel wordt evenwel geretourneerd als compatibel.  

    -   **Fout**: Geeft een lijst met alle fouten voor de geselecteerde configuratiebasislijnimplementatie op basis van het aantal betrokken activa. U kunt klikken op een regel om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** of het knooppunt **Apparaten** in de werkruimte **Activa en naleving** , die alle gebruikers bevat die fouten genereerden met deze regel. Wanneer u een gebruiker of apparaat selecteert, geeft het deelvenster **Activumgegevens** de gebruikers of apparaten weer die met het geselecteerde probleem te maken hebben. Dubbelklik op een gebruiker of apparaat in de lijst om aanvullende informatie over het probleem weer te geven.  

    -   **Niet-compatibele**: Geeft een lijst met alle niet-compatibele regels binnen de configuratiebasislijn op basis van het aantal betrokken activa. U kunt klikken op een regel om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** of het knooppunt **Apparaten** van de werkruimte **Activa en naleving** , die alle gebruikers of apparaten bevat die niet compatibel met deze regel zijn. Wanneer u een gebruiker of apparaat selecteert, geeft het deelvenster **Activumgegevens** de gebruikers of apparaten weer die met het geselecteerde probleem te maken hebben. Dubbelklik op een gebruiker of apparaat in de lijst om aanvullende informatie weer te geven over het probleem.  

    -   **Onbekende**: Geeft een lijst met alle gebruikers en apparaten die geen compatibiliteitsstatus is gerapporteerd voor de geselecteerde configuratiebasislijnimplementatie samen met de huidige clientstatus van apparaten.  

5.  Op de pagina **Implementatiestatus** kunt u gedetailleerde informatie over de naleving van de geïmplementeerde configuratiebasislijn weergeven. Een tijdelijk knooppunt wordt gemaakt onder het knooppunt **Implementaties** waarmee u deze informatie snel kunt terugvinden.  

##  <a name="view-compliance-results-by-using-reports"></a>Nalevingsresultaten weergeven met behulp van rapporten  
 Instellingen voor naleving in Configuration Manager bevat een aantal ingebouwde rapporten waarmee u informatie over configuratie-items, configuratiebasislijnen en implementaties kunt controleren. Deze rapporten hebben de rapportcategorie van **Compatibiliteit en instellingen beheren**.  

> [!IMPORTANT]  
>  U moet een jokerteken (**%**) gebruiken wanneer u de parameters **Apparaatfilter** en Gebruikerfilter gebruikt in de rapporten met instellingen voor naleving.  

 Zie voor meer informatie over het configureren van rapportage in Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md)  

##  <a name="view-compliance-results-on-a-configuration-manager-windows-client-computer"></a>Nalevingsresultaten weergeven op een Configuration Manager Windows-clientcomputer

> [!NOTE]  
>  U kunt gegevens niet weergeven op de Configuration Manager Windows-client als u bent aangemeld met een domeingastaccount.    

1.  Navigeer naar **Configuration Manager** in het Configuratiescherm van de clientcomputer en dubbelklik om de eigenschappen ervan te openen.  

2.  Klik op het tabblad **Configuraties** en bekijk de lijst met geïmplementeerde configuratiebasislijnen.  

3.  Bekijk de **Compatibiliteitsstatus** voor elke configuratiebasislijn:  

    > [!IMPORTANT]  
    >  De resultaten van de beoordeling worden gedurende 15 minuten in cache op de client bewaard. Als u een nieuwe beoordeling binnen de periode van 15 minuten start, worden de compatibiliteitsresultaten uit deze cache geretourneerd en niet van een nieuwe beoordeling. Dus als u een wijziging op de client aanbrengt die van invloed kan zijn op de resultaten van de nalevingsbeoordelingen, wacht dan tot de 15 minuten zijn verstreken voordat u een nieuwe beoordeling begint.  

    -   **Compatibele**: De clientcomputer is in overeenstemming met de geëvalueerde configuratiebasislijn.  

    -   **Niet-compatibele**: De clientcomputer leeft de geëvalueerde configuratiebasislijn.  

    -   **Onbekende**: De clientcomputer is nog niet geëvalueerd voor de configuratiebasislijn. Als u beoordeling buiten de planning voor nalevingsbeoordeling wilt initiëren, selecteert u de te beoordelen configuratiebasislijnen en klikt u vervolgens op **Evalueren**.  

        > [!NOTE]  
        >  Als u lokale beheerdersreferenties op de clientcomputer hebt, kunt u de details van elke geëvalueerde configuratiebasislijn bekijken om te bepalen welk configuratie-item als niet-compatibel wordt gerapporteerd. Selecteer de configuratiebasislijn en klik vervolgens op **Rapport weergeven**om dit te doen.  

4.  Klik op **OK**.  

##  <a name="create-collections-based-on-configuration-baseline-compliance"></a>Verzamelingen op basis van naleving van de configuratiebasislijn maken  
 Gebruik de volgende procedure om een Configuration Manager-verzameling op basis van apparaten met een opgegeven naleving te maken. U kunt verzamelingen maken op basis van de volgende nalevingsstatussen:  

-   **Compatibel**  

-   **Fout**  

-   **Non-compliant**  

-   **Onbekend**  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Configuratiebasislijnen**.  

3.  Selecteer in de lijst **Configuratiebasislijnen** de configuratiebasislijn vanwaaruit u een verzameling wilt maken.  

4.  Klik op het tabblad **Implementatie** in de **Implementatiegroep**op **Nieuwe verzameling maken** en selecteer vervolgens in de vervolgkeuzelijst het nalevingsniveau waarvoor u een verzameling wenst te maken.  

5.  De **Wizard Gebruikersverzameling maken** of de **Wizard Apparaatverzameling maken** wordt geopend, afhankelijk van het gegeven of het configuratie-item wordt geïmplementeerd voor gebruikers of apparaten. De wizard wordt automatisch ingevuld met de juiste waarden om de verzameling te maken; u kunt deze waarden echter bewerken.  

6.  Nadat u de wizard hebt voltooid, wordt de verzameling weergegeven in het knooppunt **Gebruikersverzamelingen** of het knooppunt **Apparaatverzamelingen** in de werkruimte **Activa en naleving** .  
