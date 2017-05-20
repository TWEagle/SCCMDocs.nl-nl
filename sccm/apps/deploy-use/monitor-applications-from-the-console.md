---
title: Toepassingen bewaken vanuit de System Center Configuration Manager-console | Microsoft-documenten
description: Controleer de implementatie van software, waaronder updates, compatibiliteitsinstellingen en toepassingen met behulp van de werkruimte voor bewaking in Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 784c295c-b8b8-4202-ab9f-665908d49d6d
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fd7ea34b605d70f2ba9bd40384eb566ec3a87430
ms.openlocfilehash: 42d21d10489bffe32b875384f8801686239a0ba4
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="monitor-applications-from-the-system-center-configuration-manager-console"></a>Toepassingen bewaken vanuit de System Center Configuration Manager-console

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


In System Center Configuration Manager kunt u de implementatie van alle software, inclusief software-updates, compatibiliteitsinstellingen, toepassingen, takenreeksen, en pakketten en programma's bewaken. U kunt implementaties bewaken met behulp van de **bewaking** -werkruimte in de Configuration Manager-console of met behulp van rapporten.  

 Toepassingen in Configuration Manager ondersteuning voor bewaking op basis van status, zodat u de laatste implementatiestatus van toepassing voor gebruikers en apparaten kunt bijhouden. In deze statusberichten wordt informatie over afzonderlijke apparaten weergegeven. Als een toepassing wordt geïmplementeerd voor een verzameling gebruikers, kunt u de compatibiliteitsstatus van de implementatie en het implementatiedoel weergeven in de Configuration Manager-console.  

## <a name="learn-about-compliance-states-in-system-center-configuration-manager"></a>Meer informatie over de nalevingsstatussen in System Center Configuration Manager
 De implementatiestatus van een toepassing heeft een van de volgende compatibiliteitsstatussen:  

-   **Geslaagd** – De implementatie van de toepassing is geslaagd of er is gebleken dat de toepassing al is geïnstalleerd.  

-   **Wordt uitgevoerd** – De implementatie van de toepassing wordt uitgevoerd.  

-   **Onbekend** – De status van de toepassingsimplementatie kan niet worden bepaald. Deze status is niet van toepassing op implementaties met als doel **Beschikbaar**. Deze status wordt doorgaans weergegeven wanneer er nog geen statusberichten van de client zijn ontvangen.  

-   **Niet voldaan aan vereisten** – De toepassing is niet geïmplementeerd omdat deze niet voldeed aan een afhankelijkheid of een vereisteregel, of omdat het besturingssysteem waarop het werd geïmplementeerd, niet van toepassing is.  

-   **Fout** – De toepassing kon niet worden geïmplementeerd wegens een fout.  

U kunt aanvullende informatie voor elke compatibiliteitsstatus, met inbegrip van subcategorieën binnen de compatibiliteitsstatus en het aantal gebruikers en apparaten in deze categorie weergeven. Zo bevat de compatibiliteitsstatus **Fout** bijvoorbeeld de volgende subcategorieën:  

-   Fout bij het evalueren van de vereisten  

-   Aan inhoud gerelateerde fouten  

-   Installatiefouten  

 Wanneer er meer dan één compatibiliteitsstatus van toepassing is op de implementatie van een toepassing, kunt u de geaggregeerde status zien die de laagste compatibiliteit aangeeft. Bijvoorbeeld:  

    -   Als een gebruiker zich aanmeldt bij twee apparaten en de toepassing op één apparaat correct wordt geïnstalleerd maar niet kan worden geïnstalleerd op het tweede apparaat, wordt de geaggregeerde implementatiestatus van de toepassing voor die gebruiker weergegeven als **fout**.  

    -   Als een toepassing wordt geïmplementeerd voor alle gebruikers die zich bij een computer aanmeldt, ontvangt u meerdere Implementatieresultaten voor die computer. Als een van de implementaties mislukt, wordt de geaggregeerde implementatiestatus voor de computer weergegeven als **Fout**.  

De implementatiestatus voor pakket- en programma-implementaties wordt niet geaggregeerd.  

 Gebruik deze subcategorieën om snel eventuele belangrijke problemen met een toepassingsomgeving vast te stellen. U kunt ook aanvullende informatie weergeven over de apparaten die tot een bepaalde subcategorie van een nalevingsstatus behoren.  

 Toepassingsbeheer in Configuration Manager omvat een aantal ingebouwde rapporten waarmee u informatie over toepassingen en implementaties te bewaken. Deze rapporten hebben de rapportcategorie **Softwaredistributie - Toepassingscontrole**.  

 Zie voor meer informatie over het configureren van rapportage in Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  

## <a name="monitor-the-state-of-an-application-in-the-configuration-manager-console"></a>De status van een toepassing in de Configuration Manager-console bewaken  

1.  Kies in de Configuration Manager-console **bewaking** > **implementaties**.  

3.  Implementatiedetails wilt controleren voor elke conformiteitsstatus en de apparaten die status hebben, selecteert u een implementatie, en klik vervolgens op de **Start** tabblad, in de **implementatie** groep, kiest u **Status weergeven** openen van de **Implementatiestatus** deelvenster. In dit deelvenster kunt u de assets met elke nalevingsstatus weergeven. Kies een willekeurige asset om gedetailleerdere informatie over de implementatiestatus voor die asset weer te geven.  

    > [!NOTE]  
    >  Er kunnen maximaal 20.000 items worden weergegeven in het deelvenster **Implementatiestatus** . Als u meer objecten bekijken wilt, gebruikt u Configuration Manager-rapporten om gegevens over de toepassingsstatus weer te geven.  
    >   
    >  De status van implementatietypes wordt geaggregeerd in het deelvenster **Implementatiestatus** . Als u gedetailleerdere informatie over de implementatietypen wilt weergeven, gebruikt u het rapport **Fouten in toepassingsinfrastructuur** in de rapportcategorie **Softwaredistributie - Toepassingscontrole**.  

4.  Als u wilt controleren algemene statusinformatie over de implementatie van een toepassing, selecteert u een implementatie en kies vervolgens het **samenvatting** tabblad de **geselecteerde implementatie** venster.  

5.  Als u wilt weergeven van informatie over het implementatietype voor toepassingen, selecteert u een implementatie en kies vervolgens het **implementatietypen** tabblad de **geselecteerde implementatie** venster.  

De informatie die wordt weergegeven in de **Implementatiestatus** deelvenster nadat u hebt gekozen **Status weergeven** dynamische gegevens uit de Configuration Manager-database is. De informatie die wordt weergegeven in de **samenvatting** tabblad en de **implementatietypen** tabblad is samengevatte gegevens.

Als de gegevens die wordt weergegeven in de **samenvatting** tabblad en de **implementatietypen** tabblad komt niet overeen met de gegevens die wordt weergegeven in de **Implementatiestatus** deelvenster kiezen **samenvatting uitvoeren** de gegevens op deze tabbladen bij te werken. U kunt de standaardsamenvattingsinterval voor toepassingsimplementaties als volgt configureren:  

1. Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.

2. Van de **Sites** , selecteert u de site die u wilt het samenvattingsinterval configureren en klik vervolgens op de **Start** tabblad, in de **instellingen** groep, kiest u **statusoverzichten**.

3. In de **statusoverzichten** dialoogvenster Kies **Samenvattingsprogramma voor implementatie van toepassing**, en kies vervolgens **bewerken**.  

4. In de **eigenschappen voor Samenvattingsprogramma voor implementatie van toepassing** in het dialoogvenster voor het configureren van de gewenste samenvattingsintervallen en kies vervolgens **OK**.  

