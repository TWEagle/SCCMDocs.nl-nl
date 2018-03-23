---
title: Gebruikershandleiding voor de software Center
titleSuffix: Configuration Manager
description: Meer informatie over de functies en functionaliteit van het Software Center
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 9e68de6e-2b33-442b-b674-a382728d9529
ms.openlocfilehash: 4ffe2a5049f31b5d4c06267b7683f90b0bd72633
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="software-center-user-guide"></a>Gebruikershandleiding voor de software Center

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Uw organisatie IT-beheerder Software Center gebruikt voor het installeren van toepassingen, software-updates en Windows upgraden. Deze handleiding vindt u de functionaliteit van het Software Center voor gebruikers van de computer.

### <a name="general-notes-about-software-center-functionality"></a>Algemene opmerkingen over de functionaliteit van Software Center
- In dit artikel beschrijft de nieuwste functies van het Software Center. Als uw organisatie van een oudere gebruikmaakt, maar nog steeds versie van het Software Center ondersteunde, zijn niet alle functies zijn beschikbaar. Voor meer informatie contact op met uw IT-beheerder.
- Sommige aspecten van Software Center kan worden uitgeschakeld door uw IT-beheerder. Uw specifieke ervaring kan verschillen.
<!-- - Your IT admin may change the color of Software Center, and add your organization's logo. The images in this article show the default experience. -->



## <a name="how-to-open-software-center"></a>Het openen van Software Center

De eenvoudigste methode Software Center starten op een computer met Windows 10, drukt u op **Start** en het type `Software Center`. 

Als u het menu Start navigeert, zoek in de **Microsoft System Center** groep voor de **Software Center** pictogram.



## <a name="applications"></a>Toepassingen

Klik op de **toepassingen** tab om te zoeken en installeren van toepassingen die de IT-beheerder worden geïmplementeerd op u of deze computer.
- **Alle**: Geeft alle toepassingen die u kunt installeren
- **Vereist**: Uw IT-beheerder zorgt ervoor dat deze toepassingen. Als u een van deze toepassingen verwijdert, installeert het Software Center opnieuw.
- **Filters**: Uw IT-beheerder kan categorieën van toepassingen maken. Indien beschikbaar, klikt u op de vervolgkeuzelijst om de weergave tot toepassingen in een specifieke categorie te filteren. Selecteer **alle** voor alle toepassingen weergeven.
- **Sorteren op**: De lijst met toepassingen rangschikken. Standaard wordt deze lijst sorteren op **meest recente**.
- **Search**: Nog steeds niet gevonden wat u zoekt? Voer trefwoorden in het vak Zoeken te vinden.
-  De weergave switch: Klik op de pictogrammen voor schakelen tussen lijstweergave en de tegel weergeven. Standaard wordt de lijst met toepassingen weergegeven als grafische tegels. 
    - De weergave Tile: Uw IT-beheerder kan de pictogrammen kunt aanpassen. Elke tegel wordt hieronder weergegeven de toepassingsnaam, uitgever en versie. 
    - Lijstweergave: Deze weergave bevat de toepassingspictogram, naam, uitgever, versie en status. 


### <a name="install-multiple-applications"></a>Meerdere toepassingen installeren 
<!-- 1357126 -->
Meer dan één toepassing tegelijk in plaats van te wachten op een voltooien voordat u begint de volgende installeren. Niet alle toepassingen in aanmerking komen:
- De app is zichtbaar voor u
- De app nog niet gedownload of geïnstalleerd
- Uw IT-beheerder vereist geen goedkeuring van de app te installeren

Meer dan één toepassing tegelijk installeren:
 1. Om de modus voor meervoudige selectie in de lijstweergave opgeven, klikt u op het pictogram voor meervoudige selectie ![Pictogram voor meervoudige selectie van software Center](media/software-center-multi-select-apps.png) in de rechterbovenhoek.
 2. Twee of meer apps te installeren door te klikken op het selectievakje links van de apps in de lijst selecteren.
 3. Klik op de **installeren geselecteerd** knop.

De apps installeren die normaal werken nu alleen achter.




## <a name="updates"></a>Updates

Klik op de **Updates** tabblad weergeven en installeren van software-updates die uw IT-beheerder worden geïmplementeerd op deze computer.  
- **Alle**: Ziet u alle updates die u kunt installeren
- **Vereist**: Deze updates zorgt ervoor dat uw IT-beheerder.
- **Sorteren op**: De lijst met updates rangschikken. Standaard wordt deze lijst sorteren op **toepassingsnaam: A-Z**.

Om updates te installeren, klikt u op **installeert alle**.

Alleen specifieke om updates te installeren, klikt u op het pictogram om de modus voor meervoudige selectie. Controleer of de updates installeren en klik vervolgens op **installeren geselecteerd**.



## <a name="operating-systems"></a>Besturingssystemen

Klik op de **besturingssystemen** tabblad weergeven en installeren van versies van Windows die uw IT-beheerder worden geïmplementeerd op deze computer.  
- **Alle**: Ziet u alle versies van Windows die u kunt installeren
- **Vereist**: Deze upgrades zorgt ervoor dat uw IT-beheerder.
- **Sorteren op**: De lijst met updates rangschikken. Standaard wordt deze lijst sorteren op **toepassingsnaam: A-Z**.



## <a name="installation-status"></a>Installatiestatus

Klik op de **installatiestatus** tabblad om de status van toepassingen. Mogelijk ziet u de volgende statussen:
- **Geïnstalleerd**: Deze toepassing software Center al geïnstalleerd op deze computer.
- **Downloaden van**: Software Center downloadt de software te installeren op deze computer.
- **Kan geen**: Software Center heeft een fout opgetreden bij een poging om de software te installeren.



## <a name="device-compliance"></a>Apparaatcompatibiliteit

Klik op de **apparaatcompatibiliteit** tabblad om de status van naleving van deze computer.

Klik op **controleren op naleving** evalueren van instellingen voor dit apparaat op basis van het beveiligingsbeleid dat wordt gedefinieerd door uw IT-beheerder.



## <a name="options"></a>Opties

Klik op de **opties** tabblad om aanvullende instellingen voor deze computer.

### <a name="work-information"></a>Werkinformatie

Geven de uren dat u doorgaans werken. Uw IT-beheerder kan software-installaties buiten kantooruren plannen. Toestaan dat ten minste vier uur per dag voor systeemonderhoudstaken onderhoudstaken. Uw IT-beheerder kan nog steeds installeren kritieke toepassingen en software-updates tijdens kantooruren.

- Klik op de vervolgkeuzelijst om te selecteren van de eerste en laatste uur dat u deze computer. Deze waarden zijn standaard van **05: 00** via **22 uur**

- Schakel het selectievakje naast de dagen van de week gewoonlijk deze computer te gebruiken. Software Center selecteert alleen de werkdagen waarop standaard.  


### <a name="power-management"></a>Energiebeheer

Uw IT-beheerder kan power management-beleid instellen. Deze beleidsregels kunt besparen elektriciteit als deze computer zich niet in gebruik van uw organisatie. 

Als u deze computer uitgesloten van dit beleid, schakelt u het selectievakje **energie-instellingen van mijn IT-afdeling op deze computer zijn niet van toepassing**. Deze instelling is standaard uitgeschakeld. de computer past de energiebeheerinstellingen. 


### <a name="computer-maintenance"></a>Onderhoud van de computer

Geef op hoe Software Center wijzigingen in software vóór de deadline
- **Automatisch installeren of verwijderen van de vereiste software en start de computer buiten de opgegeven kantooruren**: Deze instelling is standaard uitgeschakeld.
- **Software Center-activiteiten onderbreken wanneer mijn computer zich in de presentatiemodus bevindt**: Deze instelling is standaard ingeschakeld.
- **Beleid synchroniseren**: klik op deze knop wanneer u hierom wordt gevraagd door uw IT-beheerder. Deze computer wordt gecontroleerd met de servers voor alles nieuwe, zoals toepassingen, software-updates of besturingssystemen.

