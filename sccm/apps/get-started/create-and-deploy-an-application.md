---
title: Maken en implementeren van een toepassing | Microsoft-documenten
description: Maken en implementeren van een toepassing met een line-of-business-app en informatie over het beheren van apps effectief.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bd1e487-ea18-43c1-b7c3-acbd9b86d429
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6516db6f4c09fdd173b498c58ccc411847752c4e
ms.openlocfilehash: bbbf278f5d31c51bfe061dd44e170f7ab1ca70ad
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-and-deploy-an-application-with-system-center-configuration-manager"></a>Een toepassing maken en implementeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp, hebt u meteen en maken van een toepassing met System Center Configuration Manager. In dit voorbeeld moet u maken en implementeren van een toepassing met een line-of-business-app voor Windows-pc's genoemd **Contoso.msi**, die moet worden geïnstalleerd op alle computers met Windows 10 in uw bedrijf. Weg leert u over veel van de manieren om toepassingen te beheren effectief.  

 Deze procedure is ontworpen om u te bieden een overzicht van het maken en implementeren van toepassingen voor Configuration Manager. Echter, de configuratie van alle geldt niet voor opties of het maken en implementeren van toepassingen voor andere platforms.  

 Zie voor specifieke informatie die relevant voor elk platform zijn, een van de volgende onderwerpen:  

-   [Windows-toepassingen maken](../../apps/get-started/creating-windows-applications.md)  
-   [IOS-toepassingen maken](../../apps/get-started/creating-ios-applications.md)  
-   [Android-toepassingen maken](../../apps/get-started/creating-android-applications.md)  
-   [Windows Phone-toepassingen maken](../../apps/get-started/creating-windows-phone-applications.md)  
-   [Mac-computertoepassingen maken](../../apps/get-started/creating-mac-computer-applications.md)  
-   [Toepassingen voor Linux en UNIX-server maken](../../apps/get-started/creating-linux-and-unix-server-applications.md)
-   [Windows Embedded toepassingen maken](../../apps/get-started/creating-windows-embedded-applications.md)


Als u al bekend met Configuration Manager-toepassingen bent, kunt u dit onderwerp overslaan. U wilt misschien echter te bekijken [toepassingen maken](../../apps/deploy-use/create-applications.md) voor meer informatie over de opties die beschikbaar zijn wanneer u toepassingen maken en implementeren.  

## <a name="before-you-start"></a>Voordat u begint  

Zorg ervoor dat u de informatie in deze hebt bekeken [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management) zodat u uw site voor het installeren van toepassingen hebt voorbereid en u de terminologie begrijpen die wordt gebruikt in dit onderwerp.  

 Controleer ook of dat de installatie van de bestanden voor de **Contoso.msi** app zich in een toegankelijke locatie op uw netwerk.  

## <a name="create-the-configuration-manager-application"></a>De Configuration Manager-toepassing maken  

### <a name="to-start-the-create-application-wizard-and-create-the-application"></a>De Wizard toepassing maken starten en de toepassing maken  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken**.  

4.  Op de **algemeen** pagina van de **Wizard toepassing maken**, kies **automatisch detecteren van informatie over deze toepassing uit de installatiebestanden van**. Dit vooraf bepaalde informatie in de wizard met gegevens die zijn geëxtraheerd uit de MSI-installatiebestand gevuld. Geef vervolgens de volgende gegevens:  

    -   **Type**: Kies **Windows Installer (\*MSI-bestand)**.  

    -   **Locatie**: Typ de locatie (of kies **Bladeren** en selecteer de locatie) van het installatiebestand **Contoso.msi**. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier  *\\\Server\Share\File* voor Configuration Manager de van installatiebestanden te vinden.  

    U moet daarom iets dat lijkt op de volgende schermafbeelding:  

    ![Algemene wizardpagina App management](/sccm/apps/get-started/media/App-management-wizard-general-page.png)  

5.  Kies **volgende**. Op de **Importinformatie** pagina ziet u enkele gegevens over de app en alle bijbehorende bestanden die zijn geïmporteerd naar Configuration Manager. Als u klaar bent, kies **volgende** opnieuw.  

6.  Op de **algemene informatie** pagina kunt u informatie over de toepassing bij het sorteren en zoek het in de Configuration Manager-console verder opgeeft.  

     Bovendien de **installatieprogramma** veld kunt u de volledige opdrachtregel opgeven die wordt gebruikt voor het installeren van de toepassing op pc's. U kunt dit om toe te voegen uw eigen eigenschappen bewerken (bijvoorbeeld **/q** voor een installatie zonder toezicht).  

    > [!TIP]  
    >  Bepaalde velden op deze pagina van de wizard mogelijk zijn mogelijk automatisch ingevuld toen u de installatiebestanden van de toepassing importeerde.  

     U moet daarom een scherm weergegeven dat op de volgende schermafbeelding lijkt:  

     ![App management-wizardpagina voor algemene informatie](/sccm/apps/get-started/media/App-management-wizard-general-information-page.png)  

7.  Kies **volgende**. Op de pagina overzicht kunt u instellingen van de toepassing te bevestigen en voltooi de wizard.  

 De app is gemaakt. Deze kunt vinden, in de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, en kies vervolgens **toepassingen**. Voor dit voorbeeld wordt het volgende weergegeven:  

 ![Afbeelding van de laatste app](/sccm/apps/get-started/media/Final-app-graphic.png)  

## <a name="examine-the-properties-of-the-application-and-its-deployment-type"></a>De eigenschappen en het implementatietype van de toepassing bekijken  

Nu dat u een toepassing hebt gemaakt, kunt u de toepassingsinstellingen verfijnen als u wilt. Om te kijken naar de toepassingseigenschappen, selecteer de app en klik in de **Start** tabblad de **eigenschappen** groep, kiest u **eigenschappen**.  

 In de **< Contoso\> toepassingseigenschappen** in het dialoogvenster ziet u veel objecten die u configureren kunt om het gedrag van de toepassing. Zie voor meer informatie over de instellingen die u kunt configureren, [toepassingen maken](../../apps/deploy-use/create-applications.md). In dit voorbeeld wijzigt u enkele eigenschappen van het implementatietype van de toepassing.  

 Kies de **implementatietypen** tabblad > **Contoso toepassing** implementatietype > **bewerken**.     

Er wordt een soortgelijk dialoogvenster als hier weergegeven:  

![Pagina App management-app-eigenschappen](/sccm/apps/get-started/media/App-management-app-properties-page.png)  

## <a name="add-a-requirement-to-the-deployment-type"></a>Een vereiste toevoegen aan het implementatietype  
 Vereisten specificeren voorwaarden waaraan moet worden voldaan voordat een toepassing kan worden geïnstalleerd op een apparaat.  U kunt kiezen uit de ingebouwde vereisten of u kunt uw eigen maken. In dit voorbeeld voegt u een vereiste dat de toepassing wordt alleen geïnstalleerd op computers met Windows 10.  

1.  Kies in de implementatie van type eigenschappenpagina u zojuist hebt geopend, de **vereisten** tabblad.  

2.  Kies **toevoegen** openen van de **vereiste maken** in het dialoogvenster.  

3.  Geef in het dialoogvenster **Vereiste maken** de volgende informatie op:  

    -   **Categorie**: **Apparaat**  

    -   **Voorwaarde**: **Besturingssysteem**  

    -   **Type regel**: **Waarde**  

    -   **Operator**: **Een van**  

    -   Selecteer in de lijst met besturingssystemen **Windows 10**.  

    Het volgende dialoogvenster wordt weergegeven:  

    ![Pagina App management-vereisten](/sccm/apps/get-started/media/App-management-requirements-page.png)  

4.  Kies **OK** te sluiten van elke eigenschappenpagina die u hebt geopend. Ga daarna terug naar de **toepassingen** lijst in de Configuration Manager-console.  

> [!TIP]  
>  Vereisten kunt Verminder het aantal Configuration Manager-verzamelingen die u nodig hebt. Omdat u zojuist hebt opgegeven dat de toepassing alleen op computers met Windows 10 kan krijgen geïnstalleerd, kunt u dit later implementeren voor een verzameling met computers die veel verschillende besturingssystemen worden uitgevoerd. Maar de toepassing wordt alleen geïnstalleerd op Windows 10-computers.  

## <a name="add-the-application-content-to-a-distribution-point"></a>De toepassingsinhoud toevoegen aan een distributiepunt  

Vervolgens gebruikt om de toepassing implementeert op pc's, zorg dat de inhoud wordt gekopieerd naar een distributiepunt. Pc's toegang tot het distributiepunt om de toepassing te installeren.  

> [!TIP]  
>  Zie voor meer informatie over distributiepunten en inhoudsbeheer in Configuration Manager, [inhoud en -infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

1.  Kies in de Configuration Manager-console **softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte Vouw **toepassingen**. Selecteer in de lijst met toepassingen, de **Contoso toepassing** die u hebt gemaakt.  

3.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **inhoud distribueren**.  

4.  Op de **algemeen** pagina van de **Wizard inhoud distribueren**, Controleer of de naam van de toepassing juist is en kies vervolgens **volgende**.  

5.  Op de **inhoud** pagina, de informatie die moeten worden gekopieerd naar het distributiepunt en kies vervolgens **volgende**.  

6.  Op de **inhoud bestemming** pagina, kiest u **toevoegen** en selecteer een of meer distributiepunten of distributiepuntgroepen waarop u de inhoud van de toepassing installeren.  

7.  Voltooi de wizard.  

U kunt controleren of inhoud van de toepassing is gekopieerd naar het distributiepunt uit de **bewaking** werkruimte onder **distributiestatus** > **inhoudsstatus**.  

## <a name="deploy-the-application"></a>Implementeer de toepassing  

Vervolgens implementeert u de toepassing voor een apparaatverzameling in uw hiërarchie. In dit voorbeeld u de toepassing implementeert naar de **alle systemen** apparaatverzameling.  

> [!TIP]  
>  Houd er rekening mee dat alleen Windows 10-computers de toepassing wordt geïnstalleerd, omdat de vereisten die u eerder hebt geselecteerd.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Selecteer de toepassing die u eerder hebt gemaakt in de lijst met toepassingen (**Contoso toepassing**), en klik op de **Start** tabblad de **implementatie** groep, kiest u **implementeren**.  

4.  Op de **algemeen** pagina van de **Wizard Software implementeren**, kies **Bladeren** en selecteer de **alle systemen** verzameling apparaten.  

5.  Op de **inhoud** pagina, moet u controleren of het distributiepunt waarvoor u pc's voor het installeren van de toepassing wilt is geselecteerd.  

6.  Op de **implementatie-instellingen** pagina, zorg ervoor dat de implementatie-actie is ingesteld op **installeren**, en het implementatiedoel is ingesteld op **vereist**.  

    > [!TIP]  
    >  Door het implementatiedoel in te stellen op **vereist**, u ervoor zorgen dat de toepassing is geïnstalleerd op computers die voldoen aan de vereisten die u hebt ingesteld. Als u deze waarde instelt op **Beschikbaar**, kunnen gebruikers de toepassing op verzoek vanuit Software Center installeren.  

7.  Op de pagina **Planning** kunt u configureren wanneer de toepassing wordt geïnstalleerd. Selecteer voor dit voorbeeld **Zo snel mogelijk na het beschikbaar komen**.  

8.  Op de **gebruikerservaring** pagina, kiest u **volgende** de standaardwaarden accepteren.  

9. Voltooi de wizard.  

Gebruik de informatie in de volgende **bewaak de toepassing** sectie om te zien van de status van de implementatie van uw toepassing.  

## <a name="monitor-the-application"></a>De toepassing controleren  
 In deze sectie gaat u een kort overzicht van de status van de implementatie van de toepassing die u zojuist hebt geïmplementeerd.  

### <a name="to-review-the-deployment-status"></a>De implementatiestatus controleren  

1.  Kies in de Configuration Manager-console **bewaking** > **implementaties**.  

3.  Selecteer in de lijst met implementaties **Contoso-toepassing**.  

4.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **Status weergeven**.  

5.  Selecteer een van de volgende tabbladen om meer statusupdates over implementatie van de toepassing weer:  

    -   **Succes**: De toepassing is geïnstalleerd op de aangegeven pc's.  

    -   **Bezig**: De toepassing is niet nog installatie voltooid.  

    -   **Fout**: Er is een fout opgetreden bij het installeren van de toepassing op de aangegeven pc's. Er wordt ook meer informatie over de fout weergegeven.  

    -   **Niet voldaan aan vereisten**: Er is geen installatie is geprobeerd op de aangegeven apparaten omdat deze niet voldeed aan de vereisten die u hebt geconfigureerd (in dit voorbeeld omdat ze worden niet uitgevoerd op Windows-10).  

    -   **Onbekende**: Configuration Manager kon niet worden gegevens over de status van de implementatie. Probeer het later opnieuw.  

> [!TIP]  
>  Er zijn een aantal manieren waarop u implementaties van toepassingen kunt bewaken. Zie voor de volledige gegevens [-toepassingen bewaken](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

## <a name="end-user-experience"></a>Voor de eindgebruiker  

Pc's die worden beheerd door Configuration Manager en de actieve Windows-10 gebruikers zien een bericht om aan te geven dat moet de Contoso-toepassing te installeren. Nadat de installatie van de voorwaarden worden geaccepteerd, wordt de toepassing wordt geïnstalleerd.  

