---
title: Windows to Go met System Center Configuration Manager implementeren | Microsoft Docs
description: Informatie over het inrichten van Windows To Go in System Center Configuration Manager voor het maken van een Windows To Go-werkruimte die opstart vanaf een extern station.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8eed50f5-80a4-422e-8aa6-a7ccb2171475
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: a8b1a42c43438553cfbb62328bed933378bb344c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="deploy-windows-to-go-with-system-center-configuration-manager"></a>Windows to Go met System Center Configuration Manager implementeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat de stappen voor het inrichten van Windows To Go in System Center Configuration Manager. Windows To Go is een ondernemingsfunctie van Windows 8, die het mogelijk maakt een Windows To Go-werkruimte te maken die kan worden opgestart vanaf een via een USB-verbinding aangesloten extern station op computers die voldoen aan de certificeringsvereisten van Windows 7 of Windows 8, ongeacht het besturingssysteem van de computer. Windows To Go-werkruimten kunnen dezelfde installatiekopie gebruiken die ondernemingen gebruiken voor hun desktops en laptops en kunnen op dezelfde wijze worden beheerd.  

 Zie voor meer informatie inzake Windows To Go [Windows To Go Functieoverzicht](http://go.microsoft.com/fwlink/p/?LinkId=263433).  

## <a name="provision-windows-to-go"></a>Inrichting Windows To Go  
 Windows To Go is een besturingssysteem dat is opgeslagen op een extern station dat is aangesloten via een USB-verbinding. U kunt het Windows To Go-station inrichten zoals u andere implementaties van het besturingssysteem inricht. Niettemin moet u een lichtjes andere benadering gebruiken om deze stations in te richten, omdat Windows To Go is ontwikkeld als een op de gebruiker gerichte, zeer mobiele oplossing.  

 Op een hoog niveau is Windows To Go een implementatie in twee fasen, waarin u het Windows To Go-apparaat kunt configureren en inhoud voorbereiden voor de implementatie van het besturingssysteem. U kunt dit doen met minimale gevolgen voor de gebruiker en waarbij de downtime voor de computer van de gebruiker. Nadat u de computer hebt voorbereid, moet u het inrichtingsproces voltooien om te zorgen dat de computer klaar is voor de gebruiker. Het inrichtingsproces lijkt veel op het actuele implementatieproces van het besturingssysteem. Hieronder ziet u de algemene werkstroom voor de voorbereiding van de inhoud en inrichting van Windows To Go:  

1.  [Vereisten voor het inrichten van Windows To Go](#BKMK_Prereqs)  

2.  [Voorbereide media maken](#BKMK_CreatePrestagedMedia)  

3.  [Een Windows To Go Creator-pakket maken](#BKMK_CreatePackage)  

4.  [De takenreeks bijwerken om BitLocker voor Windows To Go in te schakelen](#BKMK_UpdateTaskSequence)  

5.  [Het Windows To Go Creator-pakket en de takenreeks implementeren](#BKMK_Deployments)  

6.  [Windows To Go Creator wordt uitgevoerd door de gebruiker](#BKMK_UserExperience)  

7.  [Het Windows To Go-station wordt geconfigureerd en voorbereid door Configuration Manager](#BKMK_ConfigureStageDrive)  

8.  [Gebruiker meldt zich aan bij Windows 8](#BKMK_UserLogsIn)  

###  <a name="BKMK_Prereqs"></a> Vereisten voor het inrichten van Windows To Go  
 Voordat u Windows To Go inricht, moet u het volgende in Configuration Manager voltooien:  

-   **Een opstartinstallatiekopie naar een distributiepunt distribueren**  

     Voordat u voorgefaseerde media maakt, moet u de opstartinstallatiekopie naar een distributiepunt distribueren.  

    > [!NOTE]  
    >  Opstartinstallatiekopieën worden gebruikt voor het installeren van het besturingssysteem op de doelcomputers in uw Configuration Manager-omgeving. Ze bevatten een versie van Windows PE waarmee het besturingssysteem en eventuele benodigde apparaatstuurprogramma's worden geïnstalleerd. Configuration Manager biedt twee opstartinstallatiekopieën: Één ter ondersteuning van x86-platformen en één ter ondersteuning van x64 platforms. U kunt ook uw eigen opstartinstallatiekopieën maken. Zie voor meer informatie [opstartinstallatiekopieën beheren](../get-started/manage-boot-images.md).  

-   **De installatiekopie van het Windows 8-besturingssysteem naar een distributiepunt distribueren**  

     Voordat u voorgefaseerde media maakt, moet u de installatiekopie van het Windows 8-besturingssysteem naar een distributiepunt distribueren.  

    > [!NOTE]  
    >  Installatiekopieën van besturingssystemen zijn WIM-bestanden. Ze omvatten een gecomprimeerde verzameling referentiebestanden en -mappen die zijn vereist om een besturingssysteem correct te installeren en configureren op een computer. Zie voor meer informatie [installatiekopieën van besturingssystemen beheren](../get-started/manage-operating-system-images.md).  

-   **Takenreeks maken om Windows 8 te implementeren**  

     U moet een takenreeks maken voor een implementatie van Windows 8 waarnaar u verwijst bij het maken van voorgefaseerde media. Zie voor meer informatie [beheren van takenreeksen om taken te automatiseren](manage-task-sequences-to-automate-tasks.md).  

###  <a name="BKMK_CreatePrestagedMedia"></a> Voorbereide media maken  
 Voorbereide media bevatten de opstartinstallatiekopie die wordt gebruikt voor het starten van de doelcomputer en de installatiekopie van het besturingssysteem die op de doelcomputer wordt toegepast. De computer die u inricht met voorgefaseerde media kan worden gestart met behulp van de opstartinstallatiekopie. De computer kan vervolgens een bestaande takenreeks voor implementatie van een besturingssysteem uitvoeren om een volledige implementatie van het besturingssysteem te installeren. De takenreeks waarmee het besturingssysteem wordt geïmplementeerd, staat niet op de media.  

 U kunt inhoud toevoegen, zoals toepassingen en stuurprogramma's, naast de installatiekopie en de opstartinstallatiekopie van het besturingssysteem tijdens de voorbereidende fase. Dit verkort de termijn die nodig is om een besturingssysteem te implementeren en vermindert het netwerkverkeer want de inhoud bevindt zich reeds in het station.  

 De volgende procedure gebruiken om de voorgefaseerde media te maken.  

#### <a name="to-create-prestaged-media"></a>Voorbereide media maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeksmedia maken** om de wizard Takenreeksmedia maken te starten.  

4.  Geef op de pagina **Mediatype selecteren** de volgende informatie op en klik op **Volgende**.  

    -   Selecteer **Voorbereide media**.  

    -   Selecteer **Implementatie van besturingssysteem zonder toezicht toestaan** om de implementatie van Windows To Go gebruikersinteractie op te starten.  

        > [!IMPORTANT]  
        >  Als u deze optie gebruikt met SMSTSPreferredAdvertID aangepaste variabele (later in dit proces instellen), is geen gebruikersinteractie vereist en zal de computer automatisch opstarten naar de implementatie van Windows To Go wanneer deze een Windows To Go-station detecteert. De gebruiker wordt nog steeds gevraagd om een wachtwoord als de media hiervoor is geconfigureerd. Als u de instelling **Implementatie van besturingssysteem zonder toezicht toestaan** gebruikt zonder de variabele SMSTSPreferredAdvertID te configureren, treedt een fout op wanneer u de takenreeks implementeert.  

5.  Geef op de pagina **Mediabeheer** de volgende informatie op en klik op **Volgende**.  

    -   Selecteer **Dynamische media** als u wilt toestaan dat een beheerpunt media omleidt naar een ander beheerpunt op basis van de clientlocatie binnen de sitegrenzen.  

    -   Selecteer **Op site gebaseerde media** als u wilt dat de media alleen contact maken met het opgegeven beheerpunt.  

6.  Geef op de pagina **Media-eigenschappen**  de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Gemaakt door**: Geef op wie het medium is gemaakt.  

    -   **Versie**: Geef het versienummer van de media.  

    -   **Opmerking**: Geef een unieke beschrijving van wat de media wordt gebruikt.  

    -   **Mediabestand**: Geef de naam en pad van de uitvoerbestanden op. De wizard schrijft de uitvoerbestanden naar deze locatie. Bijvoorbeeld:  **\\\servername\folder\outputfile.wim**  

7.  Geef op de pagina **Beveiliging** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   Selecteer **Schakel onbekende computerondersteuning** zodat de media een besturingssysteem implementeren op een computer die niet wordt beheerd door Configuration Manager. Er is geen record van deze computers in de Configuration Manager-database. Onbekende computers omvatten het volgende:  

        -   Een computer waarop de Configuration Manager-client niet is geïnstalleerd  

        -   Een computer die is niet geïmporteerd in Configuration Manager  

        -   Een computer die door Configuration Manager niet is gedetecteerd  

    -   Selecteer **De media beveiligen met een wachtwoord** en voer een sterk wachtwoord in om de media te beveiligen tegen onbevoegde toegang. Wanneer u een wachtwoord opgeeft, moet de gebruiker dat wachtwoord leveren om de voorbereide media te gebruiken.  

        > [!IMPORTANT]  
        >  Wijs, als een beste praktijk op vlak van beveiliging, altijd een wachtwoord toe om te helpen de vooraf geplaatste media te beschermen.  

        > [!NOTE]  
        >  Wanneer u de voorgefaseerde media beveiligt met een wachtwoord, wordt de gebruiker om het wachtwoord verzocht zelfs wanneer de media is geconfigureerd met de instelling **Implementatie van besturingssysteem zonder toezicht toestaan** .  

    -   Selecteer **Zelfondertekend certificaat maken**voor HTTP-communicatie en geef vervolgens de begin- en verloopdatum voor het certificaat op.  

    -   Selecteer **PKI-certificaat importeren**voor HTTPS-communicatie en geef vervolgens het certificaat op dat moet worden geïmporteerd met het bijbehorende wachtwoord.  

         Zie voor meer informatie over dit clientcertificaat dat wordt gebruikt voor opstartinstallatiekopieën [PKI-certificaatvereisten](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Affiniteit van gebruikersapparaat**: Ter ondersteuning van de gebruiker gericht beheer in Configuration Manager, moet u opgeven hoe u wilt dat de media gebruikers koppelen aan de doelcomputer. Zie voor meer informatie over hoe gebruikersapparaataffiniteit ondersteuning biedt voor implementatie van besturingssystemen, [gebruikers koppelen aan een doelcomputer](../get-started/associate-users-with-a-destination-computer.md).  

        -   Stel **Affiniteit tussen gebruikers en apparaten toestaan met automatische goedkeuring** in als u wilt dat de media gebruikers automatisch koppelen aan de doelcomputer. Deze functionaliteit is gebaseerd op de acties van de takenreeks waardoor het besturingssysteem wordt geïmplementeerd. In dit scenario brengt de takenreeks een relatie tot stand tussen de opgegeven gebruikers en de doelcomputer wanneer deze het besturingssysteem op de doelcomputer implementeert.  

        -   Stel **Affiniteit tussen gebruikers en apparaten toestaan in afwachting van goedkeuring door beheerder** in als u wilt dat de media gebruikers aan de doelcomputer koppelen nadat er goedkeuring is verleend. Deze functionaliteit is gebaseerd op het bereik van de takenreeks waardoor het besturingssysteem wordt geïmplementeerd. In dit scenario brengt de takenreeks een relatie tot stand tussen de opgegeven gebruikers en de doelcomputer, maar wordt er gewacht op goedkeuring van een gebruiker met beheerderrechten voordat het besturingssysteem wordt geïmplementeerd.  

        -   Stel **Geen affiniteit tussen gebruikers en apparaten toestaan** in als niet wilt dat de media gebruikers aan de doelcomputer koppelen. In dit scenario koppelt de takenreeks geen gebruikers aan de doelcomputer wanneer dit het besturingssysteem implementeert.  

8.  Op de pagina **Takenreeks** de takenreeks van Windows 8 opgeven die u in de voorgaande sectie hebt gemaakt.  

9. Geef op de pagina **Opstartinstallatiekopie** de volgende informatie op en klik vervolgens op **Volgende**.  

    > [!IMPORTANT]  
    >  De architectuur van de opstartinstallatiekopie die wordt gedistribueerd moet toepasselijk zijn voor de architectuur van de doelcomputer. Op een x64-doelcomputer kan een x86- of x64-opstartinstallatiekopie worden opgestart en uitgevoerd. Op een x86-doelcomputer kan echter alleen een x86-opstartinstallatiekopie worden opgestart en uitgevoerd. Voor Windows 8-gecertificeerde computers in EFI-modus, moet u een x64 opstartinstallatiekopie gebruiken.  

    -   **Opstartinstallatiekopie**: Geef de opstartinstallatiekopie voor het starten van de doelcomputer.  

    -   **Distributiepunt**: Geef het distributiepunt dat als host fungeert voor de opstartinstallatiekopie. De wizard haalt de opstartinstallatiekopie op van het distributiepunt en schrijft deze naar de media.  

        > [!NOTE]  
        >  De gebruiker met beheerdersrechten moet **Leesrechten** hebben tot de inhoud van de opstartinstallatiekopie op het distributiepunt. Zie voor meer informatie [accounts voor toegang tot inhoud beheren](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).  

    -   Als u **Op site gebaseerde media** selecteerde op de pagina **Mediabeheer** van deze wizard, geeft u in het venster **Beheerpunt** een beheerpunt op van een primaire site.  

    -   Als u **Dynamische media** selecteerde op de pagina **Mediabeheer** van de wizard, geeft u in het venster **Gekoppelde beheerpunten** de te gebruiken beheerpunten van de primaire site op en een volgorde van prioriteit voor de eerste communicaties.  

10. Geef op de pagina **Installatiekopieën** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Installatiekopiepakket**: Geef het pakket met de installatiekopie van het besturingssysteem Windows 8.  

    -   **Installatiekopie-index**: Geef de afbeelding als het pakket meerdere installatiekopieën van besturingssystemen bevat te implementeren.  

    -   **Distributiepunt**: Geef het distributiepunt dat als host fungeert voor het installatiekopiepakket van het besturingssysteem. De wizard haalt de opstartinstallatiekopie van het besturingssysteem op van het distributiepunt en schrijft deze naar de media.  

        > [!NOTE]  
        >  De gebruiker met beheerdersrechten moet **Leesrechten** hebben tot de inhoud van de installatiekopie van het besturingssysteem op het distributiepunt. Zie voor meer informatie [accounts voor toegang tot inhoud beheren](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).  

11. Op de pagina **Toepassing selecteren** de toepassingsinhoud opgeven voor opname in het mediabestand en klikken op **Volgende**.  

12. Op de pagina **Pakket selecteren** de aanvullende pakketinhoud opgeven voor opname in het mediabestand en klikken op **Volgende**.  

13. Op de pagina **Stuurprogrammapakket selecteren** de stuurprogramma-inhoud opgeven voor opname in het mediabestand en klikken op **Volgende**.  

14. Selecteer, op de pagina **Distributiepunten** , een of meer distributiepunten die de inhoud bevatten die vereist is door de takenreeks, en klik vervolgens op **Volgende**.  

15. Geef op de pagina **Aanpassing** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Variabelen**: Geef de variabelen op die de takenreeks gebruikt voor het implementeren van het besturingssyteem. Gebruik voor Windows To Go, de variabele SMSTSPreferredAdvertID om automatisch de implementatie van Windows To Go te selecteren met behulp van de volgende indeling:  

         SMSTSPreferredAdvertID = {*DeploymentID*}, waarbij DeploymentID de implementatie-id is die gekoppeld is aan de takenreeks die u gebruikt om het inrichtingsproces voor het Windows To Go-station te voltooien.  

        > [!TIP]  
        >  Als u deze variabele gebruikt met de takenreeks die ingesteld is om zonder toezicht te worden uitgevoerd (voorheen in dit proces ingesteld), is geen gebruikersinteractie vereist en start de computer automatisch op naar de implementatie van Windows To Go wanneer deze een Windows To Go-station detecteert. De gebruiker wordt nog steeds gevraagd om een wachtwoord als de media hiervoor is geconfigureerd.  

    -   **Prestart-opdrachten**: Geef eventuele prestart-opdrachten op die u wilt uitvoeren voordat de takenreeks wordt uitgevoerd. Prestart-opdrachten kunnen bestaan uit een script of een uitvoerbaar bestand dat kan communiceren met de gebruiker in Windows PE voordat de takenreeks wordt uitgevoerd om het besturingssysteem te installeren. Het volgende voor de implementatie van Windows To Go configureren:  

        -   **OSDBitLockerPIN**: BitLocker voor Windows To Go vereist een wachtwoordzin. De variabele **OSDBitLockerPIN** instellen als onderdeel van een prestart-opdracht om de BitLocker-wachtwoordzin voor het Windows To Go-station in te stellen.  

            > [!WARNING]  
            >  Nadat BitLocker is ingeschakeld voor de wachtwoordzin, moet de gebruiker de wachtwoordzin invoeren telkens wanneer de computer opstart naar het Windows To Go-station.  

        -   **SMSTSUDAUsers**: Geeft de primaire gebruiker van de doelcomputer op. Gebruik deze variabele om de gebruikersnaam in te zamelen, die vervolgens kan worden gebruikt om de gebruiker te koppelen aan het apparaat. Zie voor meer informatie [gebruikers koppelen aan een doelcomputer](../get-started/associate-users-with-a-destination-computer.md).  

            > [!TIP]  
            >  Om de gebruikersnaam op te halen, kunt u een invoervak maken als onderdeel van de prestart-opdracht, laat u de gebruiker zijn gebruikersnaam invoeren en stelt vervolgens de variabele met de waarde in. U kunt bijvoorbeeld de volgende regels toevoegen aan het scriptbestand van de prestart-opdracht:  
            >   
            >  `UserID = inputbox("Enter Username" ,"Enter your username:","",400,0)`  
            >   
            >  `env("SMSTSUDAUsers") = UserID`  

         Zie voor meer informatie over het maken van een scriptbestand om te gebruiken als uw prestart-opdracht [Prestart-opdrachten voor takenreeksmedia](../understand/prestart-commands-for-task-sequence-media.md).  

16. Voltooi de wizard.  

    > [!NOTE]  
    >  De wizard kan er lang over doen om het voorgefaseerde mediabestand te voltooien.  

###  <a name="BKMK_CreatePackage"></a> Een Windows To Go Creator-pakket maken  
 Als onderdeel van de implementatie van Windows To Go, moet u een pakket maken om het voorgefaseerde mediabestand te implementeren. Het pakket moet het hulpprogramma bevatten dat het Windows To Go-station configureert en de voorgefaseerde media naar het station uitvoert. Gebruik de volgende procedure om het Windows To Go Creator-pakket te maken.  

#### <a name="to-create-the-windows-to-go-creator-package"></a>Het Windows To Go Creator-pakket maken  

1.  Maak op de server om de Windows To Go Creator pakketbestanden te hosten, een bronmap voor de pakketbronbestanden.  

    > [!NOTE]  
    >  Het computeraccount van de siteserver moet **Leesrechten** voor de bronmap hebben.  

2.  Kopieer het voorgefaseerde mediabestand dat u maakte in de sectie [Create prestaged media](#BKMK_CreatePrestagedMedia) naar de pakketbronmap.  

3.  Kopieer het hulpprogramma van Windows To Go Creator (WTGCreator.exe) naar de pakketbronmap. Het hulpprogramma creator is beschikbaar op elke primaire siteserver op de volgende locatie: <*ConfigMgrInstallationFolder*> \OSD\Tools\WTG\Creator.  

4.  Maak een pakket en programma met behulp van de wizard Pakket en Programma maken.  

5.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

6.  Vouw **Toepassingsbeheer** uit in de werkruimte **Softwarebibliotheek**en klik vervolgens op **pakketten**.  

7.  Klik op **Pakket maken** in het tabblad **Start** in de groep **Maken**.  

8.  Geef op de pagina **Pakket** de naam en beschrijving van het pakket. Voer voor de pakketnaam bijvoorbeeld **Windows To Go** in en geef voor de pakketbeschrijving **Package to configure a Windows To Go drive using System Center Configuration Manager** op.  

9. Selecteer **Dit pakket bevat bronbestanden**, geef het pad op naar de pakketbronmap die u maakte in stap 1 en klik vervolgens op **Next**.  

10. Op de pagina **Programmatype** selecteert u **Standaardprogramma**, en klikt u dan op **Volgende**.  

11. Op de pagina **Standaardprogramma** het volgende opgeven:  

    -   **Naam**: Geef de naam van het programma. Typ bijvoorbeeld **Creator** voor de programmanaam.  

    -   **Opdrachtregel**: Type **WTGCreator.exe /wim:PrestageName.wim**, waarbij PrestageName de naam van het voorgefaseerde bestand dat u maakte en kopieerde naar de pakketbronmap voor het Windows To Go Creator-pakket.  

         Eventueel kunt u de volgende opties toevoegen:  

        -   **enableBootRedirect**: opdrachtregeloptie om de opstartopties van Windows To Go te wijzigen en een omleiding voor opstarten toe te staan. Als u deze optie gebruikt, zal de computer opstarten vanuit USB zonder dat wijziging van de opstartvolgorde van de computer firmware vereist is of de gebruiker moet worden geselecteerd uit een lijst met opstartopties bij het opstarten. Als een Windows To Go-station is gedetecteerd, start de computer op naar dit station.  

    -   **Uitvoeren**: Geef **normaal** uit te voeren op basis van het systeem en standaardprogramma.  

    -   **Programma kan worden uitgevoerd**: Geef op of het programma kan alleen uitgevoerd als een gebruiker is aangemeld.  

    -   **Uitvoermodus**: Geef op of het programma wordt uitgevoerd met aangemelde gebruikersmachtigingen of met beheerdersmachtigingen. Verhoogde machtigingen zijn vereist om Windows To Go Creator uit te voeren.  

    -   Selecteer **Gebruikers toestaan de programma-installatie te bekijken en interacties uit te voeren**en klik vervolgens op **Volgende**.  

12. Op de pagina Vereisten het volgende opgeven:  

    -   **Platformvereisten**: Selecteer de toepasselijke Windows 8-platformen om toe te staan inrichten.  

    -   **Geschatte schijfruimte**: Geef de grootte van de pakketbronmap voor het Windows To Go Creator.  

    -   **Maximale toegestane uitvoeringstijd (minuten)**: Hiermee geeft u de maximale tijd die het programma uit te voeren op de clientcomputer wordt verwacht. Deze waarde is standaard ingesteld op 120 minuten.  

        > [!IMPORTANT]  
        >  Als u onderhoudsvensters gebruikt voor de verzameling waarop dit programma wordt uitgevoerd, kan er een conflict optreden als de **Maximum toegestane uitvoeringstijd** langer is dan het geplande onderhoudsvenster. Als de maximum uitvoeringstijd is ingesteld op **Onbekend**, zal het starten tijdens het onderhoudsvenster, maar zal het verder worden uitgevoerd tot het voltooid of mislukt is nadat het onderhoudsvenster is gesloten. Als u de maximum uitvoeringstijd instelt op een specifieke periode (niet ingesteld op Onbekend) die langer is dan de lengte van enig beschikbaar onderhoudsvenster, zal het programma niet worden uitgevoerd.  

        > [!NOTE]  
        >  Als de waarde is ingesteld op **onbekende**, Configuration Manager stelt de maximale toegestane uitvoeringstijd in op 12 uur (720 minuten).  

        > [!NOTE]  
        >  Als de maximum uitvoeringstijd (hetzij ingesteld door de gebruiker hetzij als de standaardwaarde) overschreden is, wordt in Configuration Manager wordt gestopt als **uitvoeren met beheerdersrechten** is geselecteerd en **toestaan dat gebruikers de programma-installatie kunnen zien en** niet is geselecteerd op de **standaardprogramma** pagina.  

     Klik op **Volgende** en voltooi de wizard.  

###  <a name="BKMK_UpdateTaskSequence"></a> De takenreeks bijwerken om BitLocker voor Windows To Go in te schakelen  
 Windows To Go schakelt BitLocker in op een extern opstartbaar station zonder het gebruik van TPM. Daarom moet u een afzonderlijk hulpprogramma gebruiken om BitLocker op het Windows To Go-station te configureren. Om BitLocker in te schakelen, moet u een actie toevoegen aan de takenreeks na de stap **Windows en ConfigMgr installeren** .  

> [!NOTE]  
>  BitLocker voor Windows To Go vereist een wachtwoordzin. In de stap [Create prestaged media](#BKMK_CreatePrestagedMedia) stelt u de wachtwoordzin in als deel van een prestart-opdracht door de OSDBitLockerPIN-variabele te gebruiken.  

 Gebruik de volgende procedure om de Windows 8-takenreeks bij te werken om BitLocker voor Windows To Go in te schakelen.  

#### <a name="to-update-the-windows-8-task-sequence-to-enable-bitlocker"></a>Bijwerken van de Windows 8-takenreeks om BitLocker in te schakelen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Toepassingsbeheer** uit in de werkruimte **Softwarebibliotheek**en klik vervolgens op **pakketten**.  

3.  Klik op **Pakket maken** in het tabblad **Start** in de groep **Maken**.  

4.  Geef op de pagina **Pakket** de naam en beschrijving van het pakket. Typ voor de pakketnaam bijvoorbeeld **BitLocker for Windows To Go** en geef voor de pakketbeschrijving **Package to update BitLocker for Windows To Go** op.  

5.  Selecteer **Dit pakket bevat bronbestanden**, specificeer de locatie voor het BitLocker-hulpprogramma voor Windows To Go, en klik vervolgens op **Volgende**. Het hulpprogramma BitLocker is beschikbaar op elke primaire siteserver van Configuration Manager op de volgende locatie: <*ConfigMgrInstallationFolder*> \OSD\Tools\WTG\BitLocker\  

6.  Selecteer op de pagina **Programmatype** **Geen programma maken**.  

7.  Klik op **Volgende** en voltooi de wizard.  

8.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

9. Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

10. Selecteer de Windows 8-takenreeks waarnaar u verwijst in de voorgefaseerde media.  

11. Klik in het tabblad **Start** in de groep **Takenreeks** op **Bewerken**.  

12. Klik op de stap **Windows en ConfigMgr installeren** , klik op **Toevoegen**, klik op **Algemeen**, en klik vervolgens op **Opdrachtregel uitvoeren**. De stap Opdrachtregel uitvoeren wordt toegevoegd na de stap Windows en ConfigMgr installeren.  

13. Voeg op het tabblad **Eigenschappen** voor de stap **Opdrachtregel uitvoeren** het volgende toe:  

    1.  **Naam**: Geef een naam voor de opdrachtregel, zoals **inschakelen BitLocker voor Windows To Go**.  

    2.  **Opdrachtregel**: i386\osdbitlocker_wtg.exe/Enable/pwd: < *geen &#124; AD*>  

         Parameters:  

        -   / pwd: < none &#124; AD >-Geef de BitLocker-wachtwoordherstelmodus. Deze parameter is vereist als u de parameter /Enable in de opdrachtregel gebruikt.  

             Selecteer **AD** om BitLocker-stationsversleuteling te configureren om een back-up te maken van herstelinformatie voor door BitLocker beschermde stations naar Active Directory Domain Services (AD DS). Het maken van een back-up van herstelwachtwoorden voor een door BitLocker beschermd station laat beheerders toe het station te herstellen als het vergrendeld is. Dit zorgt ervoor dat versleutelde gegevens die behoren tot de onderneming, altijd kunnen worden geopend door geautoriseerde gebruikers. Wanneer u **Geen**specificeert, is de gebruiker verantwoordelijk voor het bewaren van een kopie van het herstelwachtwoord of de herstelsleutel. Als de gebruiker die informatie verliest of negeert om het station te ontsleutelen voordat hij de organisatie verlaat, kunnen beheerders niet gemakkelijk toegang krijgen tot het station.  

        -   / wait: < TRUE &#124; FALSE >-opgeven of de takenreeks moet voor versleuteling is voltooid wachten voordat deze is voltooid.  

    3.  Selecteer **Pakket**, en geef dan het pakket dat u aan het begin van deze procedure hebt gemaakt.  

    4.  Specificeer op het tabblad **Opties** de volgende condities:  

        -   Conditie = Takenreeksvariabele  

        -   Variabele = _SMSTSWTG  

        -   Conditie = is gelijk aan  

        -   Waarde = True  

    > [!NOTE]  
    >  De stap **BitLocker inschakelen** , die waarschijnlijk is na de nieuwe opdrachtregelstap, wordt niet gebruikt om BitLocker voor Windows To Go in te schakelen. U kunt deze stap echter in de takenreeks houden om te gebruiken voor Windows 8-implementaties die geen Windows To Go-station gebruiken.  

###  <a name="BKMK_Deployments"></a> Het Windows To Go Creator-pakket en de takenreeks implementeren  
 Windows To Go is een proces voor hybride implementatie. Daarom moet u het Windows To Go Creator-pakket en de Windows 8-takenreeks implementeren. Gebruik de volgende procedures om de implementatieproces te voltooien.  

#### <a name="to-deploy-the-windows-to-go-creator-package"></a>Het Windows To Go Creator-pakket implementeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Toepassingsbeheer** uit in de werkruimte **Softwarebibliotheek**en klik vervolgens op **pakketten**.  

3.  Selecteer het Windows To Go-pakket dat u in de stap [Een Windows To Go Creator-pakket maken](#BKMK_CreatePackage) hebt gemaakt.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

5.  Geef op het tabblad **Algemeen** de volgende instellingen op:  

    1.  **Software**: Controleer of het pakket voor Windows To Go is geselecteerd.  

    2.  **Verzameling**: Klik op **Bladeren** om de verzameling waarnaar u wilt implementeren van het Windows To Go-pakket te selecteren.  

    3.  **Gebruik standaarddistributiepuntengroepen die gekoppeld zijn aan deze verzameling**: Selecteer deze optie als u wilt opslaan van inhoud van het pakket op de verzamelingen standaard distributiepuntengroep. Als u de geselecteerde verzameling niet hebt gekoppeld aan een distributiepuntgroep, wordt deze optie onbeschikbaar.  

6.  Klik op de pagina **Inhoud** op **Toevoegen** en selecteer vervolgens de distributiepunten of distributiepuntgroepen waarop u de inhoud wilt implementeren die is gekoppeld met dit pakket en programma.  

7.  Op de pagina **Implementatie-instellingen** selecteert u **Beschikbaar** voor het implementatietype, en klikt u vervolgens op **Volgende**.  

8.  Configureer op de **Planning**wanneer dit pakket en programma zullen worden geïmplementeerd of beschikbaar zullen worden gemaakt voor clientapparaten.  

     De opties op deze pagina zullen verschillen afhankelijk van of de implementatieactie ingesteld is op **Beschikbaar** of **Vereist**.  

9. Configureer op de pagina **Planning**de volgende instellingen en klik vervolgens op **Volgende**.  

    1.  **Plannen wanneer deze implementatie beschikbaar zal worden**: Geef de datum en tijd wanneer het pakket en programma wordt uitgevoerd op de doelcomputer. Wanneer u **UTC**selecteert, zorgt deze instelling ervoor dat het pakket en programma beschikbaar zijn voor meerdere doelcomputers tegelijkertijd eerder dan op verschillende tijdstippen, volgens de lokale tijd op de doelcomputers.  

    2.  **Plannen wanneer deze implementatie zal verlopen**: Geef de datum en tijd wanneer het pakket en programma verlopen op de doelcomputer. Wanneer u **UTC**selecteert, zorgt deze instelling ervoor dat de takenreeks verloopt op meerdere doelcomputers tegelijkertijd eerder dan op verschillende tijdstippen, volgens de lokale tijd op de doelcomputers.  

10. Geef op de pagina **Gebruikerservaring** van de wizard de volgende informatie:  

    -   **Software-installatie**: Hierdoor kan de software worden geïnstalleerd buiten de geconfigureerde onderhoudsvensters.  

    -   **Systeem opnieuw opstarten (indien nodig om de installatie te voltooien)**: Hiermee kunt een apparaat opnieuw opstarten buiten de geconfigureerde onderhoudsvensters wanneer vereist door de software-installatie.  

    -   **Embedded-apparaten**: Bij het implementeren van pakketten en programma's op Windows Embedded-apparaten met schrijffilter is ingeschakeld, kunt u opgeven voor het installeren van de pakketten en programma's op de tijdelijke overlay en doorvoeren wijzigingen later of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

11. Geef op de pagina **Distributiepunten** de volgende informatie:  

    -   **Implementatie-opties:** Geef **inhoud downloaden vanaf het distributiepunt en lokaal uitvoeren**.  

    -   **Toestaan dat clients inhoud te delen met andere clients in hetzelfde subnet**: Selecteer deze optie om de belasting op het netwerk te verminderen door clients inhoud downloaden van andere clients op het netwerk dat al hebben gedownload en gecached. Deze optie gebruikt Windows BranchCache en kan worden gebruikt op computers die Windows Vista SP2 en recenter uitvoeren.  

    -   **Alle clients een terugvalbronlocatie voor inhoud te gebruiken**: Geef op of clients mogen terugvallen en gebruik een niet-voorkeursdistributiepunt als de bronlocatie voor inhoud wanneer de inhoud niet beschikbaar op een voorkeursdistributiepunt is.  

12. Voltooi de wizard.  

#### <a name="to-deploy-the-windows-8-task-sequence"></a>De Windows 8-takenreeks implementeren  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Selecteer de Windows 8-takenreeks die in u stap [Prerequisites to provision Windows To Go](#BKMK_Prereqs) hebt gemaakt.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

5.  Geef op het tabblad **Algemeen** de volgende instellingen op:  

    1.  **Takenreeks**: Controleer of de Windows 8-takenreeks is geselecteerd.  

    2.  **Verzameling**: Klik op **Bladeren** om de verzameling die alle apparaten waarvoor een gebruiker Windows To Go kan inrichten bevat selecteren.  

        > [!IMPORTANT]  
        >  Als de voorgefaseerde media die u in de sectie [Create prestaged media](#BKMK_CreatePrestagedMedia) hebt gemaakt, gebruik maakt van de SMSTSPreferredAdvertID-variabele, kunt u de takenreeks implementeren op de verzameling **Alle systemen** en kunt u de instelling **Alleen Windows PE (verborgen)** op de pagina **Inhoud** specificeren. Omdat de takenreeks verborgen is, zal ze enkel beschikbaar zijn voor media.  

    3.  **Gebruik standaarddistributiepuntengroepen die gekoppeld zijn aan deze verzameling**: Selecteer deze optie als u wilt opslaan van inhoud van het pakket op de verzamelingen standaard distributiepuntengroep. Als u de geselecteerde verzameling niet hebt gekoppeld aan een distributiepuntgroep, wordt deze optie onbeschikbaar.  

6.  Configureer op de pagina **Implementatie-instellingen** de volgende instellingen en klik vervolgens op **Volgende**.  

    -   **Doel**: Selecteer **beschikbaar**. Wanneer u de takenreeks op een gebruiker implementeert, ziet de gebruiker de gepubliceerde takenreeks in de Application Catalog en kan hij deze op aanvraag opvragen. Wanneer u de takenreeks op een apparaat implementeert, ziet de gebruiker de takenreeks in Software Center en kan hij deze op aanvraag installeren.  

    -   **Toegankelijk maken voor de volgende**: Opgeven of de takenreeks beschikbaar is voor Configuration Manager-clients, media of PXE.  

        > [!IMPORTANT]  
        >  Gebruik de instelling **Alleen media en PXE (verborgen)** voor geautomatiseerde implementaties van takenreeksen. Selecteer **Implementatie van besturingssysteem zonder toezicht toestaan** en stel de SMSTSPreferredAdvertID-variabele in als deel van de voorgefaseerde media om de computer automatisch te laten opstarten naar de Windows To Go-implementatie zonder gebruikersinteractie wanneer het een Windows To Go-station detecteert. Voor meer informatie over deze voorgefaseerde media-instellingen, zie de sectie [Create prestaged media](#BKMK_CreatePrestagedMedia) .  

7.  Configureer op de pagina **Planning** de volgende instellingen en klik vervolgens op **Volgende**.  

    1.  **Plannen wanneer deze implementatie beschikbaar zal worden**: Geef de datum en tijd waarop de takenreeks beschikbaar is voor uitvoeren op de doelcomputer. Wanneer u **UTC**selecteert, zorgt deze instelling ervoor dat de takenreeks toegankelijk is voor meerdere doelcomputers tegelijkertijd eerder dan op verschillende tijdstippen, volgens de lokale tijd op de doelcomputers.  

    2.  **Plannen wanneer deze implementatie zal verlopen**: Geef de datum en tijd waarop de takenreeks verloopt op de doelcomputer. Wanneer u **UTC**selecteert, zorgt deze instelling ervoor dat de takenreeks verloopt op meerdere doelcomputers tegelijkertijd eerder dan op verschillende tijdstippen, volgens de lokale tijd op de doelcomputers.  

8.  Geef op de pagina **Gebruikerservaring** de volgende informatie:  

    -   **Voortgang van Takenreeks weergeven**: Geef aan of Configuration Manager-client de voortgang van de takenreeks weergeeft.  

    -   **Software-installatie**: Geef op of de gebruiker is toegestaan voor het installeren van software buiten een geconfigureerd onderhoudsvenster na de geplande tijd.  

    -   **Systeem opnieuw opstarten (indien nodig om de installatie te voltooien)**: Hiermee kunt een apparaat opnieuw opstarten buiten de geconfigureerde onderhoudsvensters wanneer vereist door de software-installatie.  

    -   **Embedded-apparaten**: Bij het implementeren van pakketten en programma's op Windows Embedded-apparaten met schrijffilter is ingeschakeld, kunt u opgeven voor het installeren van de pakketten en programma's op de tijdelijke overlay en doorvoeren wijzigingen later of de wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster. Wanneer u wijzigingen doorvoert tegen de installatiedeadline of tijdens een onderhoudsvenster, moet er opnieuw worden opgestart, zodat de wijzigingen behouden blijven op het apparaat.  

    -   **Clients op Internet**: Geef op of de takenreeks mag worden uitgevoerd op een client met Internet. Bewerkingen waarbij er software wordt geïnstalleerd, zoals een besturingssysteem, worden bij het gebruik van deze instelling niet ondersteund. Gebruik deze optie alleen voor algemene op scripts gebaseerde takenreeksen die bewerkingen uitvoeren onder het standaardbesturingssysteem.  

9. Geef op de pagina **Waarschuwingen** de waarschuwingsinstelling die u wilt voor de implementatie van deze takenreeks en klik vervolgens op **Volgende**.  

10. Geef op de pagina **Distributiepunten** de volgende informatie op en klik vervolgens op **Volgende**.  

    -   **Implementatieopties**: Selecteer **inhoud lokaal downloaden wanneer nodig is voor de uitvoering van takenreeks**.  

    -   **Een extern distributiepunt gebruiken wanneer geen lokaal distributiepunt beschikbaar is,**: Specificeer of clients distributiepunten die zich op trage en onbetrouwbare netwerken voor het downloaden van de inhoud die is door de takenreeks vereist kunnen gebruiken.  

    -   **Clients gebruiken een terugvalbronlocatie voor inhoud toestaan**:
        - *Voorafgaand aan versie 1610*, kunt u de toestaan terugvalbronlocatie voor inhoud selectievakje wilt toestaan dat clients buiten deze grensgroepen terug te vallen en het distributiepunt gebruiken als bronlocatie voor inhoud, wanneer er geen andere distributiepunten beschikbaar zijn.
        - *Vanaf versie 1610*, u kunt niet meer configureren **terugvalbronlocatie voor inhoud toestaan**.  In plaats daarvan configureert u de relaties tussen grensgroepen om te bepalen wanneer een client beginnen kunt met het extra grensgroepen voor de locatie van een geldige inhoudsbron zoeken. 

11. Voltooi de wizard.  

###  <a name="BKMK_UserExperience"></a> Windows To Go Creator wordt uitgevoerd door de gebruiker  
 Nadat u het Windows To Go-pakket en de Window 8-takenreeks hebt geïmplementeerd, is Windows To Go Creator toegankelijk voor de gebruiker. De gebruiker kan naar de softwarecatalogus gaan, of Software Center als de Windows To Go Creator werd geïmplementeerd op apparaten, en hij kan het Windows To Go Creator-programma uitvoeren. Zodra het creator-pakket is gedownload, verschijnt een knipperend pictogram op de taakbalk. Wanneer de gebruiker op het pictogram klikt, wordt een dialoogvenster getoond aan de gebruiker om het Windows To Go-station te selecteren om in te richten (tenzij de /drive-opdrachtregeloptie wordt gebruikt). Als het station niet voldoet aan de vereisten voor windows To Go of als het station onvoldoende vrij schrijfruimte heeft om de installatiekopie te installeren, toont het creator-programma een foutboodschap. De gebruiker kan het station en de installatiekopie controleren die vanop de bevestigingspagina zullen worden toegepast. Terwijl de creator inhoud naar het Windows To Go-station configureert en voorbereidt, wordt het vooruitgangsdialoogvenster getoond. Nadat de voorbereiding voltooid is, toont de creator een prompt om de computer opnieuw op te starten om te starten naar het Windows To Go-station.  

> [!NOTE]  
>  Als u opstartomleiding niet hebt ingeschakeld als deel van de opdrachtregel voor het creator-programma in de sectie [Create a Windows To Go Creator package](#BKMK_CreatePackage) , kan de gebruiker verplicht zijn handmatig op te starten naar het Windows To Go-station telkens het systeem opnieuw opstart.  

###  <a name="BKMK_ConfigureStageDrive"></a> Het Windows To Go-station wordt geconfigureerd en voorbereid door Configuration Manager  
 Nadat de computer opnieuw opgestart is naar het Windows To Go-station, zal het station opstarten naar Windows PE en een verbinding maken met het beheerpunt om het beleid te krijgen om de implementatie van het besturingssysteem te voltooien. Configuration Manager configureert en bereidt het station. Nadat Configuration Manager het station heeft voorbereid, kan de gebruiker opnieuw starten van de computer om het inrichtingsproces (zoals het koppelen van een domein of het installeren van apps) te voltooien. Dit proces is hetzelfde voor alle voorgefaseerde media.  

###  <a name="BKMK_UserLogsIn"></a> Gebruiker meldt zich aan bij Windows 8  
 Nadat Configuration Manager het inrichtingsproces is voltooid en de Windows 8-vergrendelingsscherm heeft getoond, wordt de gebruiker zich aanmelden op het besturingssysteem.  
