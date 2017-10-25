---
title: Maken van opstartbare media - Configuration Manager | Microsoft Docs
description: Opstartbare media in Configuration Manager kunt u eenvoudig een nieuwe versie van Windows installeren of de instellingen van een computer en de overdracht vervangen.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ead79e64-1b63-4d0d-8bd5-addff8919820
caps.latest.revision: "11"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 9032698fa12bf453041ea06bf330d3b4687c2a97
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="create-bootable-media-with-system-center-configuration-manager"></a>Opstartbare media maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Opstartbare media in Configuration Manager bevat de opstartinstallatiekopie, optionele prestart-opdrachten en bijbehorende bestanden en Configuration Manager-bestanden. Gebruik voorgefaseerde media voor de volgende implementatiescenario'voor besturingssystemen:  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

-   [Een bestaande computer vervangen en de instellingen overzetten](replace-an-existing-computer-and-transfer-settings.md)  

##  <a name="BKMK_CreateBootableMedia"></a> Opstartbare media maken  
 Wanneer u de opstartbare media opstart, wordt de doelcomputer gestart en maakt deze verbinding met het netwerk. Vervolgens worden de opgegeven takenreeks, de installatiekopie van het besturingssysteem en alle andere vereiste inhoud opgehaald van het netwerk. Omdat de takenreeks zich niet op de media bevindt, kunt u de takenreeks of de inhoud wijzigen zonder dat u de media opnieuw hoeft te maken. De pakketten op opstartbare media zijn niet versleuteld. U moet de gepaste beveiligingsmaatregelen nemen, zoals een wachtwoord instellen voor de media, om ervoor te zorgen dat de pakketinhoud beveiligd is tegen onbevoegde gebruikers.  

 Voordat u opstartbare media maakt met de wizard Takenreeksmedia maken, moet u ervoor zorgen dat aan de volgende voorwaarden wordt voldaan:  

|Taak|Beschrijving|  
|----------|-----------------|  
|Opstartinstallatiekopie|Overweeg het volgende met betrekking tot de opstartinstallatiekopie die u in de takenreeks gebruikt om het besturingssysteem te implementeren:<br /><br /> -De architectuur van de opstartinstallatiekopie moet geschikt is voor de architectuur van de doelcomputer. Op een x64-doelcomputer kan een x86- of x64-opstartinstallatiekopie worden opgestart en uitgevoerd. Op een x86-doelcomputer kan echter alleen een x86-opstartinstallatiekopie worden opgestart en uitgevoerd.<br />-Zorg ervoor dat de installatiekopie de netwerk- en mass storage stuurprogramma's die zijn vereist bevat voor het inrichten van de doelcomputer.|  
|Een takenreeks maken om een besturingssysteem te implementeren|Als onderdeel van de opstartbare media moet u de takenreeks voor de implementatie van het besturingssysteem opgeven. Zie voor de stappen voor het maken van een nieuwe takenreeks [een takenreeks maken om een besturingssysteem te installeren](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md).|  
|Alle aan de takenreeks gekoppeld inhoud distribueren|U moet alle inhoud die door de takenreeks is vereist naar ten minste één distributiepunt distribueren. Dit omvat de opstartinstallatiekopie en andere bijbehorende prestart-bestanden. De wizard haalt de informatie op van het distributiepunt wanneer het de opstartbare media maakt. U moet over het toegangsrecht **Lezen** beschikken voor de inhoudsbibliotheek op het distributiepunt.  Zie voor meer informatie [over de Inhoudsbibliotheek](../../core/plan-design/hierarchy/the-content-library.md).|  
|Het verwisselbare USB-station voorbereiden|Voor een verwisselbaar USB-station:<br /><br /> Wanneer u een verwisselbaar USB-station wilt gebruiken, moet het USB-station zijn aangesloten op de computer waarop de wizard wordt uitgevoerd. Daarnaast moet het USB-station door Windows gedetecteerd kunnen worden als een verwisselbaar apparaat. De wizard schrijft rechtstreeks naar het USB-station wanneer deze het medium maakt. Zelfstandige media maakt gebruik van een FAT32-bestandssysteem. U kunt geen zelfstandige media maken op een USB-flashstation waarvan de inhoud een bestand bevat dat groter is dan 4 GB.|  
|Een uitvoermap maken|Voor een cd/dvd-set:<br /><br /> Voordat u de wizard Takenreeksmedia maken uitvoert voor het maken van media voor een cd- of dvd-set, moet u een map maken voor de uitvoerbestanden die door de wizard worden gemaakt. Media die worden gemaakt voor een cd- of dvdset worden als .iso-bestanden direct naar de map geschreven.|  

 De volgende procedure gebruiken om opstartbare media te maken.  

### <a name="to-create-bootable-media"></a>Opstartbare media maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Takenreeksmedia maken** om de wizard Takenreeksmedia maken te starten.  

4.  Geef op de pagina **Mediatype selecteren** de volgende opties op en klik op **Volgende**.  

    -   Selecteer **opstartbare media**.  

    -   Selecteer optioneel, indien u wenst toe te staan dat het besturingssysteem geïmplementeerd wordt zonder tussenkomst van de gebruiker, de optie **Implementatie van het besturingssysteem zonder toezicht toestaan**.  

        > [!IMPORTANT]  
        >  Wanneer u deze optie selecteert, wordt de gebruiker niet gevraagd naar informatie over netwerkconfiguratie of naar optionele takenreeksen. De gebruiker wordt wel nog steeds gevraagd om een wachtwoord als de media hiervoor is geconfigureerd.  

5.  Geef op de pagina **Mediabeheer** één van de volgende opties op en klik dan op **Volgende**.  

    -   Selecteer **Dynamische media** als u wilt toestaan dat een beheerpunt media omleidt naar een ander beheerpunt op basis van de clientlocatie binnen de sitegrenzen.  

    -   Selecteer **Op site gebaseerde media** als u wilt dat de media alleen contact maken met het opgegeven beheerpunt.  

6.  Geef op de pagina **Mediumtype** op of het medium een flashstation of een cd/dvd-set is en klik vervolgens om het volgende te configureren:  

    > [!IMPORTANT]  
    >  Zelfstandige media maakt gebruik van een FAT32-bestandssysteem. U kunt geen zelfstandige media maken op een USB-flashstation waarvan de inhoud een bestand bevat dat groter is dan 4 GB.  

    -   Als u **USB-flashstation**selecteert, moet u het station opgeven waarop u de inhoud wilt opslaan.  

    -   Indien u **cd-/dvdset selecteert**, geef dan de capaciteit van de media en de naam en het pad van de uitvoerbestanden op. De wizard schrijft de uitvoerbestanden naar deze locatie. Bijvoorbeeld:  **\\\servername\folder\outputfile.iso**  

         Als de capaciteit van de media te klein is om alle inhoud op te slaan, worden er meerdere bestanden gemaakt en moet u de inhoud op meerdere cd's of dvd's opslaan. Als meerdere media nodig zijn, wordt een volgnummer toegevoegd aan de naam van ieder uitvoerbestand dat wordt gemaakt van Configuration Manager. Bovendien, als u een toepassing tezamen met het besturingssysteem implementeert en de toepassing is te voor één media groot, slaat Configuration Manager de toepassing over verschillende media. Wanneer de zelfstandige media wordt uitgevoerd, wordt Configuration Manager de gebruiker naar de volgende media waar de toepassing wordt opgeslagen.  

        > [!IMPORTANT]  
        >  Als u een bestaande .iso-afbeelding selecteert, verwijdert de wizard voor het maken van takenreeksmedia die afbeelding uit het station of de share wanneer u doorgaat naar de volgende pagina van de wizard. De bestaande installatiekopie wordt gewist, zelfs als u de wizard annuleert.  

     Klik op **Volgende**.  

7.  Geef op de pagina **Beveiliging** de volgende opties op en klik dan op **Volgende**.  

    -   Selecteer de **Schakel onbekende computerondersteuning** selectievakje in zodat de media een besturingssysteem implementeren op een computer die niet wordt beheerd door Configuration Manager. Er is geen record van deze computers in de Configuration Manager-database.  

         Onbekende computers omvatten het volgende:  

        -   Een computer waarop de Configuration Manager-client niet is geïnstalleerd  

        -   Een computer die is niet geïmporteerd in Configuration Manager  

        -   Een computer die door Configuration Manager niet is gedetecteerd  

    -   Selecteer het selectievakje **Bescherm de media met een wachtwoord** en voer een sterk wachtwoord in om de media te helpen te beschermen tegen onbevoegde toegang. Wanneer u een wachtwoord opgeeft, moet de gebruiker dat wachtwoord leveren om de opstartbare media te gebruiken.  

        > [!IMPORTANT]  
        >  Wijs, als een best practice op vlak van beveiliging, altijd een wachtwoord toe om te helpen de opstartbare media te beschermen.  

    -   Selecteer **Zelfondertekend certificaat maken**voor HTTP-communicatie en geef vervolgens de begin- en verloopdatum voor het certificaat op.  

    -   Selecteer **PKI-certificaat importeren**voor HTTPS-communicatie en geef vervolgens het certificaat op dat moet worden geïmporteerd met het bijbehorende wachtwoord.  

         Zie voor meer informatie over dit clientcertificaat dat wordt gebruikt voor opstartinstallatiekopieën [PKI-certificaatvereisten](../../core/plan-design/network/pki-certificate-requirements.md).  

    -   **Affiniteit van gebruikersapparaat**: Ter ondersteuning van de gebruiker gericht beheer in Configuration Manager, moet u opgeven hoe u wilt dat de media gebruikers koppelen aan de doelcomputer. Zie voor meer informatie over hoe gebruikersapparaataffiniteit ondersteuning biedt voor implementatie van besturingssystemen, [gebruikers koppelen aan een doelcomputer](../get-started/associate-users-with-a-destination-computer.md).  

        -   Stel **Affiniteit tussen gebruikers en apparaten toestaan met automatische goedkeuring** in als u wilt dat de media gebruikers automatisch koppelen aan de doelcomputer. Deze functionaliteit is gebaseerd op de acties van de takenreeks waardoor het besturingssysteem wordt geïmplementeerd. In dit scenario brengt de takenreeks een relatie tot stand tussen de opgegeven gebruikers en de doelcomputer wanneer deze het besturingssysteem op de doelcomputer implementeert.  

        -   Stel **Affiniteit tussen gebruikers en apparaten toestaan in afwachting van goedkeuring door beheerder** in als u wilt dat de media gebruikers aan de doelcomputer koppelen nadat er goedkeuring is verleend. Deze functionaliteit is gebaseerd op het bereik van de takenreeks waardoor het besturingssysteem wordt geïmplementeerd.  In dit scenario brengt de takenreeks een relatie tot stand tussen de opgegeven gebruikers en de doelcomputer, maar wordt er gewacht op goedkeuring van een gebruiker met beheerderrechten voordat het besturingssysteem wordt geïmplementeerd.  

        -   Stel **Geen affiniteit tussen gebruikers en apparaten toestaan** in als niet wilt dat de media gebruikers aan de doelcomputer koppelen. In dit scenario koppelt de takenreeks geen gebruikers aan de doelcomputer wanneer dit het besturingssysteem implementeert.  

8.  Geef op de pagina **Opstartinstallatiekopie** de volgende opties op en klik vervolgens op **Volgende**.  

    > [!IMPORTANT]  
    >  De architectuur van de opstartinstallatiekopie die wordt gedistribueerd moet toepasselijk zijn voor de architectuur van de doelcomputer. Op een x64-doelcomputer kan een x86- of x64-opstartinstallatiekopie worden opgestart en uitgevoerd. Op een x86-doelcomputer kan echter alleen een x86-opstartinstallatiekopie worden opgestart en uitgevoerd.  

    -   Geef in het vakje **Opstartinstallatiekopie** de opstartinstallatiekopie op om de doelcomputer op te starten.  

    -   Geef in het vak **Distributiepunt** het distributiepunt op waar de installatiekopie is opgeslagen. De wizard haalt de opstartinstallatiekopie op van het distributiepunt en schrijft deze naar de media.  

        > [!NOTE]  
        >  U moet over het toegangsrecht **Lezen** beschikken voor de inhoudsbibliotheek op het distributiepunt.  

    -   Als u site-gebaseerde opstartbare media op de pagina **Mediabeheer** van de wizard maakt, geeft u in het vak **Beheerpunt** een beheerpunt op van een primaire site.  

    -   Als u dynamische opstartbare media maakt op de pagina **Mediabeheer** van de wizard, geeft u in **Gekoppelde beheerpunten**de beheerpunten van de primaire site die moeten worden gebruikt en een prioriteitsvolgorde voor de eerste communicatie op.  

9. Geef op de pagina **Aanpassing** de volgende opties op en klik dan op **Volgende**.  

    -   Geef de variabelen op die de takenreeks gebruikt voor het implementeren van het besturingssyteem.  

    -   Geef eventuele prestart-opdrachten op die u wilt uitvoeren voordat de takenreeks wordt uitgevoerd. Prestart-opdrachten bestaan uit een script of een uitvoerbaar bestand dat kan communiceren met de gebruiker in Windows PE voordat de takenreeks wordt uitgevoerd om het besturingssysteem te installeren. Zie voor meer informatie [Prestart-opdrachten voor takenreeksmedia](../understand/prestart-commands-for-task-sequence-media.md).  

        > [!TIP]  
        >  Tijdens het maken van taak de media schrijft de takenreeks de pakket-ID en prestart-opdrachtregel, inclusief de waarde voor eventuele takenreeksvariabelen, naar het logboekbestand CreateTSMedia.log op de computer waarop de Configuration Manager-console. U kunt dit logboekbestand controleren om de waarde voor de takenreeksvariabelen te verifiëren.  

         Selecteer optioneel het selectievakje **Bestand voor de prestart opdracht** om vereiste bestanden op te nemen voor de prestart-opdracht.  

10. Voltooi de wizard.  

## <a name="create-bootable-media-on-a-usb-drive-from-a-network-share"></a>Opstartbare media maken op een USB-station vanaf een netwerkshare
De informatie in deze sectie helpt u opstartbare media maken op een USB-flashstation, wanneer het flash-station is niet verbonden met de computer waarop de Configuration Manager-console wordt uitgevoerd. De opstartbare media maken op het USB-station, kunt u boot takenreeksmedia maken, ISO koppelen en de bestanden van de ISO overbrengen naar het USB-station.

1. [Het opstarten van de takenreeksmedia maken](#to-create-task-boobable-media). Op de **mediatype** pagina **CD/DVD-set**. De wizard schrijft de uitvoerbestanden naar de locatie die u opgeeft. Bijvoorbeeld:  **\\\servername\folder\outputfile.iso**.  
2. Bereid het verwisselbare USB-station. Het station moet worden geformatteerd, leeg en opstartbaar.
3. De ISO koppelen vanuit de sharelocatie en de bestanden van de ISO overbrengen naar het USB-station.

## <a name="next-steps"></a>Volgende stappen  
[Opstartbare media gebruiken om Windows te implementeren via het netwerk](use-bootable-media-to-deploy-windows-over-the-network.md)  
