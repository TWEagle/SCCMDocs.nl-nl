---
title: Koppelen van gebruikers en apparaten met gebruikersapparaataffiniteit | Microsoft-documenten
description: Koppelen van gebruikers en apparaten met apparaataffiniteit van gebruikers en implementeren van apps automatisch op alle apparaten die zijn gekoppeld aan een gebruiker.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b30b0d5-722d-4d4b-9ed7-5a43de315461
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6b1393b2a329bcd017dc961366afb09fa7a77899
ms.openlocfilehash: 4e8e677851ad9ae7d027ab685e842a8ff5e35573
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="link-users-and-devices-with-user-device-affinity-in-system-center-configuration-manager"></a>Koppelen van gebruikers en apparaten met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Affiniteit tussen gebruikers en apparaten in System Center Configuration Manager (Configuration Manager) koppelt een gebruiker aan een of meer apparaten. Dit kan de behoefte om de namen van Gebruikersapparaten voor het implementeren van een toepassing voor de gebruiker te weten wegnemen. In plaats van de toepassing voor alle apparaten van een gebruiker te implementeren, kunt u de toepassing voor de gebruiker zelf implementeren. Affiniteit tussen gebruikers en apparaten zorgt er daarna automatisch voor dat de toepassing wordt geïnstalleerd op alle apparaten die aan die gebruiker zijn gekoppeld.  

 U kunt primaire apparaten die zijn doorgaans de apparaten die gebruikers dagelijks gebruiken om hun werk te doen. Wanneer u affiniteit tussen een gebruiker en een apparaat instelt, beschikt u over meer implementatieopties voor apps. Bijvoorbeeld als een gebruiker Microsoft Visio vereist, kunt u installeren deze op het primaire apparaat van de gebruiker met behulp van een Windows Installer-implementatie. Op een apparaat dat geen primair apparaat is, implementeren u echter Visio als een virtuele toepassing. Ook kunt u apparaataffiniteit van gebruikers aan vooraf software op een gebruikersapparaat wanneer de gebruiker niet is aangemeld, zodat, wanneer de gebruiker zich aanmeldt, de app al is geïnstalleerd en gereed om uit te voeren.  

 U moet de gegevens van gebruikersaffiniteit met apparaat voor computers beheren. Affiniteiten van gebruikersapparaat voor de geregistreerde mobiele apparaten wordt automatisch beheerd door Configuration Manager.  

## <a name="manually-set-up-user-device-affinity"></a>Gebruikersaffiniteit met apparaat handmatig instellen  

1.  Kies in de Configuration Manager-console **activa en naleving** > **apparaten**.  

3.  Selecteer een apparaat in de lijst. Klik vervolgens op de **Start** tabblad, in de **apparaat** groep, kiest u **primaire gebruikers bewerken**.  

4.  In de **primaire gebruikers bewerken** in het dialoogvenster Zoek en selecteer vervolgens de gebruikers toe te voegen als primaire gebruikers voor het geselecteerde apparaat. Kies **toevoegen**.  

    > [!NOTE]  
    > De **primaire gebruikers** lijst worden weergegeven voor gebruikers die al primaire gebruikers van dit apparaat en de methode volgens welke iedere gebruiker-apparaat relatie is toegewezen.  

## <a name="set-up-primary-devices-for-a-user"></a>Primaire apparaten voor een gebruiker instellen  

1.  Kies in de Configuration Manager-console **activa en naleving** > **gebruikers**.  

3.  Selecteer een gebruiker in de lijst. Klik vervolgens op de **apparaat** Kies **primaire apparaten bewerken**.  

4.  In de **primaire apparaten bewerken** Zoek en selecteer de apparaten toe te voegen als primaire apparaten voor de geselecteerde gebruiker in het dialoogvenster. Kies **toevoegen**.  

    > [!NOTE]  
    > De **primaire apparaten** lijst met apparaten weergegeven die al zijn ingesteld als primaire apparaten voor deze gebruiker en de methode volgens welke iedere gebruiker-apparaat relatie is toegewezen.  

## <a name="automatically-create-user-device-affinities-windows-pcs-only"></a>Automatisch affiniteit tussen gebruikers en apparaten instellen (alleen Windows-pc's)  
 Configuration Manager leest gegevens over gebruikersaanmeldingen uit het Windows-gebeurtenislogboek. Voor het automatisch maken van affiniteiten tussen gebruikers en apparaten, moet u deze twee opties in het lokale beveiligingsbeleid op clientcomputers wordt geïnstalleerd voor het opslaan van aanmeldingsgebeurtenissen in het gebeurtenislogboek van Windows inschakelen:  

-   **Aanmeldingsgebeurtenissen voor accounts controleren**  
-   **Aanmeldingsgebeurtenissen controleren**  

 Configureren van deze instellingen Windows groepsbeleid gebruiken.  

> [!IMPORTANT]  
> Als een fout veroorzaakt in de Windows-gebeurtenislogboek voor het genereren van een groot aantal vermeldingen, kunt u een nieuw gebeurtenislogboek mogelijk gemaakt. Als dit gebeurt zijn worden bestaande aanmeldingsgebeurtenissen niet langer mogelijk beschikbaar voor Configuration Manager.  
>   
> Wees voorzichtig wanneer u op de **Aanmeldingsgebeurtenissen controleren account** en **Aanmeldingsgebeurtenissen controleren** instellingen in Windows XP. Standaard het bewaarbeleid is 7 dagen en is het zeer waarschijnlijk dat deze gebeurtenissen vol. van het beveiligingslogboek. Standaardgebruikers kunnen niet mogelijk om aan te melden als het gebeurtenislogboek vol is. Om dit te voorkomen, voor het beveiligingslogboek, stelt u het beleid **bewaarmethode** van waarde naar **gebeurtenissen overschrijven indien nodig**. Voor voldoende gegevens voor apparaataffiniteit van gebruikers, moet u ook de grootte van het beleid maximale beveiliging gebeurtenislogboek instellen op een redelijke waarde zoals 5-20 MB.  

### <a name="set-up-the-site-to-automatically-create-user-device-affinities"></a>Instellen van de site automatisch gebruikersaffiniteiten apparaat  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen**.  

2.  Selecteer voor het wijzigen van de standaardclientinstellingen **Standaardclientinstellingen**, en klik op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**. Als u aangepaste clientagentinstellingen instellingen, selecteert de **clientinstellingen** knooppunt en klik op de **Start** tabblad, in de **maken** groep, kiest u **aangepaste Clientapparaatinstellingen maken**.  

    > [!NOTE]  
    > Als u de standaardclientinstellingen aanpast, worden deze instellingen geïmplementeerd voor alle computers in de hiërarchie. Zie voor meer informatie over het configureren van clientinstellingen [clientinstellingen configureren in System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

3.  Voor **Apparaataffiniteit van gebruiker en**, stelt u het volgende:  

    -   **Gebruiksdrempel van affiniteit van gebruiker apparaat (minuten)**. Stel het aantal minuten van het gebruik van het apparaat voordat gebruikersaffiniteit met apparaat wordt gemaakt.  

    -   **Gebruiksdrempel affiniteit van gebruiker met apparaat (dagen)**. Stel het aantal dagen op waarover de op gebruik gebaseerde affiniteitsdrempel wordt gemeten.  

    -   **Automatisch configureren aan de affiniteit tussen gebruikers en apparaten van gebruiksgegevens**. Selecteer zodat de site automatisch affiniteit tussen gebruikers apparaat, uit de vervolgkeuzelijst **waar**. Als u selecteert **False**, moet u alle apparaten toewijzingen van gebruikersaffiniteit goedkeuren.  

    > [!TIP]  
    > **Voorbeeld:** Als u instelt **gebruiksdrempel van affiniteit van gebruiker apparaat (minuten)** naar **60** minuten en u stelt **gebruiksdrempel affiniteit van gebruiker met apparaat (dagen)** naar**5** dagen, moet de gebruiker gebruiken het apparaat minstens 60 minuten gedurende een periode van 5 dagen automatisch een gebruikersaffiniteit met apparaat te maken.  

Nadat een automatische gebruikersaffiniteit met apparaat is gemaakt, blijft de Configuration Manager de gebruiksdrempels van affiniteit van gebruiker apparaat bewaken. Als de Gebruikersactiviteit voor het apparaat minder is dan de drempelwaarden die u hebt ingesteld, wordt de gebruikersaffiniteit van apparaten verwijderd. Stel **gebruiksdrempel affiniteit van gebruiker met apparaat (dagen)** naar een waarde van ten minste **7** dagen om situaties te voorkomen waarin een automatisch geconfigureerde gebruikersaffiniteit met apparaat mogelijk verloren wanneer de gebruiker is niet aangemeld, bijvoorbeeld tijdens het weekend.  

## <a name="import-user-device-affinities-from-a-file"></a>Affiniteiten tussen gebruikers en apparaten importeren vanuit een bestand  
 Voor het maken van vele relaties kunt u in één keer een bestand dat de gegevens voor meerdere gebruikersaffiniteiten met apparaten importeren. Voor deze procedure moeten de betreffende apparaten moeten zijn gedetecteerd en als bronnen in de Configuration Manager-database bestaan, of de procedure werkt niet.  

1.  Kies in de Configuration Manager-console **activa en naleving** > **gebruikers** of **apparaten**.  

2.  Op de **Start** tabblad, in de **maken** groep, kiest u **Apparaataffiniteit van gebruikers importeren**.  

3.  In de Import Wizard Apparaataffiniteiten van gebruikers, op de **toewijzing selecteren** pagina, stelt u deze informatie:  

    -   **Bestandsnaam**. Geef een bestand met door komma's gescheiden waarden (CSV) met een lijst met gebruikers en apparaten die u wilt de affiniteit. In dit bestand moet elke gebruiker-en-apparaatpaar in een eigen rij met waarden, gescheiden door een komma. Gebruik de volgende notatie: <*domein*> &#92; <*gebruikersnaam*>, <*apparaat NetBIOS-naam*>.  

    -   **Dit bestand heeft kolomkoppen voor referentiedoeleinden**. Het CSV-bestand heeft een kopregel heeft, selecteer deze optie als de rij met koppen tijdens het importeren wordt genegeerd.  

4.  Als het bestand dat u importeert meer dan twee items in elke rij heeft, kunt u **kolom** en **toewijzen** om op te geven welke kolom gebruikers en apparaten vertegenwoordigt en welke kolommen moeten worden genegeerd tijdens het importeren.  

5.  Kies **volgende**, en voltooi de Import Wizard Apparaataffiniteiten van gebruikers.  

## <a name="let-users-create-their-own-device-affinities"></a>Kunnen gebruikers hun eigen gebruikersaffiniteit met apparaat maken  
 Met de volgende procedures kunt u een gebruiker instellen voor het maken van hun eigen gebruikersaffiniteit met apparaat in de app Software Center.  

### <a name="set-up-the-site-to-allow-user-created-user-device-affinity-requests"></a>Instellen van de site waarmee gebruikers gecreëerde affiniteitsaanvragen van Gebruikersapparaten  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen**.  

2.  Selecteer voor het wijzigen van de standaardclientinstellingen **Standaardclientinstellingen**, en klik op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**. Als u aangepaste clientagentinstellingen instellingen, selecteert de **clientinstellingen** knooppunt en klik op de **Start** tabblad, in de **maken** groep, kiest u **aangepaste Clientgebruikersinstellingen maken**.  

    > [!NOTE]  
    > Als u de standaardclientinstellingen aanpast, worden deze instellingen geïmplementeerd voor alle computers in de hiërarchie. Zie voor meer informatie over het configureren van clientinstellingen [clientinstellingen configureren](../../core/clients/deploy/configure-client-settings.md).  

3.  Selecteer de clientinstelling **Affiniteit van gebruiker en apparaat** en selecteer in de vervolgkeuzelijst **Gebruiker toestaan hun primaire apparaten te definiëren** de optie **Waar**.  

### <a name="set-up-a-user-device-affinity"></a>Gebruikersaffiniteit met apparaat instellen  

1.  Kies in de Application Catalog **Mijn systemen**.  

2.  Selecteer de optie **ik gebruik deze computer regelmatig voor mijn werk**.  

## <a name="manage-user-device-affinity-requests-from-users"></a>Aanvragen van gebruikers voor affiniteit tussen gebruikers en apparaten beheren  
 Wanneer de clientinstelling **Affiniteit van gebruiker met apparaat automatisch configureren aan de hand van gebruiksgegevens** is ingesteld op **Onwaar**, moet u alle toewijzingen van affiniteit tussen gebruikers en apparaten goedkeuren.  

### <a name="approve-or-reject-a-user-device-affinity-request"></a>Goedkeuren of afwijzen een gebruikersaanvraag voor de affiniteit van apparaat  

1.  Kies in de Configuration Manager-console **activa en naleving**.  

2.  Selecteer in de werkruimte **Activa en naleving** de gebruikers- of apparaatverzameling waarvoor u de affiniteitsaanvragen wilt beheren.  

3.  Op de **Start** tabblad, in de **verzameling** groep, kiest u **Affiniteitsaanvragen**.  

4.  In de **beheren Affiniteitsaanvragen van Gebruikersapparaten** in het dialoogvenster selecteert u een aanvraag affiniteit en kies vervolgens **goedkeuren** of **afwijzen**.  

