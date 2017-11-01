---
title: Een toepassing maken en implementeren
titleSuffix: Configuration Manager
description: Maken en implementeren van een toepassing met een line-of-business-app en informatie over het effectief beheren van apps.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bd1e487-ea18-43c1-b7c3-acbd9b86d429
caps.latest.revision: "15"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: a9f8a54400897e30d01d97f81b98e0e539fc86a7
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-and-deploy-an-application-with-system-center-configuration-manager"></a>Een toepassing maken en implementeren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp gaat u meteen en een toepassing maken met System Center Configuration Manager. In dit voorbeeld hebt u maken en implementeren van een toepassing met een line-of-business-app voor Windows-pc's **Contoso.msi**, die moet worden geïnstalleerd op alle computers waarop Windows 10 in uw bedrijf. Langs de manier waarop, vindt u meer over vele dingen die u doen kunt om effectief beheren van toepassingen.  

 Deze procedure is ontworpen om u te bieden een overzicht van het maken en implementeren van Configuration Manager-toepassingen. Echter, dit geldt niet voor alle configuratie-opties of hoe u toepassingen voor andere platforms maakt en implementeert.  

 Zie een van de volgende onderwerpen voor specifieke informatie die relevant voor elk platform zijn:  

-   [Windows-toepassingen maken](../../apps/get-started/creating-windows-applications.md)  
-   [iOS-toepassingen maken](../../apps/get-started/creating-ios-applications.md)  
-   [Android-toepassingen maken](../../apps/get-started/creating-android-applications.md)  
-   [Windows Phone-toepassingen maken](../../apps/get-started/creating-windows-phone-applications.md)  
-   [Mac-computertoepassingen maken](../../apps/get-started/creating-mac-computer-applications.md)  
-   [Linux- en UNIX-servertoepassingen maken](../../apps/get-started/creating-linux-and-unix-server-applications.md)
-   [Windows Embedded-toepassingen maken](../../apps/get-started/creating-windows-embedded-applications.md)


Als u al bekend met Configuration Manager-toepassingen bent, kunt u dit onderwerp overslaan. Echter, u mogelijk wilt bekijken [toepassingen maken](../../apps/deploy-use/create-applications.md) voor meer informatie over de opties die beschikbaar zijn wanneer u toepassingen maakt en implementeert.  

## <a name="before-you-start"></a>Voordat u begint  

Zorg ervoor dat u de informatie in hebt bekeken [inleiding op Toepassingsbeheer](/sccm/apps/understand/introduction-to-application-management) zodat u uw site voor het installeren van toepassingen hebt voorbereid en u begrijpt de terminologie die wordt gebruikt in dit onderwerp.  

 Controleer ook of de installatiebestanden voor de **Contoso.msi** app zijn op een toegankelijke locatie op uw netwerk.  

## <a name="create-the-configuration-manager-application"></a>De Configuration Manager-toepassing maken  

### <a name="to-start-the-create-application-wizard-and-create-the-application"></a>De Wizard toepassing maken starten en de toepassing maken  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken**.  

4.  Op de **algemene** pagina van de **Wizard toepassing maken**, kies **automatisch detecteren van informatie over deze toepassing uit de installatiebestanden van**. Dit vult vooraf enkele van de informatie in de wizard met informatie die wordt opgehaald uit het MSI-installatiebestand. Geef vervolgens de volgende gegevens:  

    -   **Type**: Kies **Windows Installer (\*MSI-bestand)**.  

    -   **Locatie**: Typ de locatie (of kies **Bladeren** om de locatie te selecteren) van het installatiebestand **Contoso.msi**. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier  *\\\Server\Share\File* voor Configuration Manager de van installatiebestanden te vinden.  

    U moet eindigen met iets dat op de volgende schermafbeelding lijkt:  

    ![Algemene wizardpagina App management](/sccm/apps/get-started/media/App-management-wizard-general-page.png)  

5.  Kies **volgende**. Op de **informatie importeren** pagina ziet u enkele gegevens over de app en de gekoppelde bestanden die zijn geïmporteerd naar Configuration Manager. Wanneer u klaar bent, kiest **volgende** opnieuw.  

6.  Op de **algemene informatie** pagina kunt u informatie over de toepassing om te sorteren en zoek het in de Configuration Manager-console verdere opgeven.  

     Bovendien de **installatieprogramma** veld kunt u de volledige opdrachtregel opgeven die wordt gebruikt voor het installeren van de toepassing op pc's. U kunt deze optie als u wilt toevoegen van uw eigen eigenschappen bewerken (bijvoorbeeld **/q** voor een installatie zonder toezicht).  

    > [!TIP]  
    >  Bepaalde velden op deze pagina van de wizard mogelijk zijn mogelijk automatisch ingevuld toen u de installatiebestanden van de toepassing importeerde.  

     U moet eindigen met een scherm weergegeven dat op de volgende schermafbeelding lijkt:  

     ![App management-wizardpagina voor algemene informatie](/sccm/apps/get-started/media/App-management-wizard-general-information-page.png)  

7.  Kies **volgende**. Op de pagina overzicht kunt u de toepassingsinstellingen controleren en voltooi de wizard.  

 De app is gemaakt. Zoekt in de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, en kies vervolgens **toepassingen**. Voor dit voorbeeld wordt het volgende weergegeven:  

 ![Afbeelding van de laatste app](/sccm/apps/get-started/media/Final-app-graphic.png)  

## <a name="examine-the-properties-of-the-application-and-its-deployment-type"></a>De eigenschappen en het implementatietype van de toepassing bekijken  

Nu dat u een toepassing hebt gemaakt, kunt u de toepassingsinstellingen verfijnen als u wilt. Als de toepassingseigenschappen wilt opzoeken, selecteert u de app en klikt u op de **Start** tabblad de **eigenschappen** groep, kiest u **eigenschappen**.  

 In de **< Contoso\> toepassingseigenschappen** in het dialoogvenster ziet u veel items die u configureren kunt voor het verfijnen van het gedrag van de toepassing. Zie voor meer informatie over de instellingen die u kunt configureren, [toepassingen maken](../../apps/deploy-use/create-applications.md). In dit voorbeeld wijzigt u enkele eigenschappen van het implementatietype van de toepassing.  

 Kies de **implementatietypen** tabblad > **Contoso-toepassing** implementatietype > **bewerken**.  

Er wordt een soortgelijk dialoogvenster als hier weergegeven:  

![App management-app-eigenschappenpagina](/sccm/apps/get-started/media/App-management-app-properties-page.png)  

## <a name="add-a-requirement-to-the-deployment-type"></a>Een vereiste toevoegen aan het implementatietype  
 Vereisten specificeren voorwaarden waaraan moet worden voldaan voordat een toepassing kan worden geïnstalleerd op een apparaat.  U kunt ingebouwde vereisten kiezen of u kunt uw eigen maken. In dit voorbeeld voegt u een vereiste dat de toepassing wordt alleen geïnstalleerd op pc's met Windows 10.  

1.  Kies in de implementatie type eigenschappenpagina u zojuist hebt geopend, de **vereisten** tabblad.  

2.  Kies **toevoegen** openen de **vereiste maken** in het dialoogvenster.  

3.  Geef in het dialoogvenster **Vereiste maken** de volgende informatie op:  

    -   **Categorie**: **Apparaat**  

    -   **Voorwaarde**: **Besturingssysteem**  

    -   **Regeltype**: **Waarde**  

    -   **Operator**: **Een van**  

    -   Selecteer in de lijst met besturingssystemen **Windows 10**.  

    Het volgende dialoogvenster wordt weergegeven:  

    ![Pagina App management-vereisten](/sccm/apps/get-started/media/App-management-requirements-page.png)  

4.  Kies **OK** te sluiten van pagina's met eigenschappen die u hebt geopend. Ga vervolgens terug naar de **toepassingen** in de Configuration Manager-console.  

> [!TIP]  
>  Vereisten kunt u Verminder het aantal Configuration Manager-verzamelingen die u nodig hebt. Omdat u zojuist hebt opgegeven dat de toepassing alleen op computers met Windows 10 kan ophalen geïnstalleerd, kunt u dit later implementeren voor een verzameling waartoe de computers waarop verschillende besturingssystemen. Maar de toepassing wordt alleen geïnstalleerd op Windows 10-computers.  

## <a name="add-the-application-content-to-a-distribution-point"></a>De toepassingsinhoud toevoegen aan een distributiepunt  

Vervolgens om de toepassing implementeert op pc's, zorg dat de inhoud wordt gekopieerd naar een distributiepunt. Pc's toegang tot het distributiepunt om de toepassing te installeren.  

> [!TIP]  
>  Zie voor meer informatie over distributiepunten en inhoudsbeheer in Configuration Manager, [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

1.  Kies in de Configuration Manager-console **softwarebibliotheek**.  

2.  In de **softwarebibliotheek** werkruimte Vouw **toepassingen**. Selecteer in de lijst met toepassingen, de **Contoso-toepassing** die u hebt gemaakt.  

3.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **inhoud distribueren**.  

4.  Op de **algemene** pagina van de **Wizard inhoud distribueren**, Controleer of de naam van de toepassing juist is en kies vervolgens **volgende**.  

5.  Op de **inhoud** pagina, lees de informatie die wordt gekopieerd naar het distributiepunt en kies vervolgens **volgende**.  

6.  Op de **doel van inhoud** pagina **toevoegen** selecteren van een of meer distributiepunten of distributiepuntengroepen waarop u de inhoud van de toepassing te installeren.  

7.  Voltooi de wizard.  

U kunt controleren dat inhoud van de toepassing correct is gekopieerd naar het distributiepunt van de **bewaking** werkruimte onder **distributiestatus** > **inhoudsstatus**.  

## <a name="deploy-the-application"></a>Implementeer de toepassing  

Vervolgens implementeert u de toepassing voor een apparaatverzameling in uw hiërarchie. In dit voorbeeld implementeert u de toepassing naar de **alle systemen** apparaatverzameling.  

> [!TIP]  
>  Houd er rekening mee dat Windows 10-computers de toepassing wordt geïnstalleerd, vanwege de vereisten die u eerder hebt geselecteerd.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Selecteer in de lijst met toepassingen, de toepassing die u eerder hebt gemaakt (**Contoso-toepassing**), en klik op de **Start** tabblad de **implementatie** groep, kiest u **implementeren**.  

4.  Op de **algemene** pagina van de **Wizard Software implementeren**, kies **Bladeren** selecteren de **alle systemen** apparaatverzameling.  

5.  Op de **inhoud** pagina, controleert u of het distributiepunt waarvoor u pc's voor het installeren van de toepassing wilt is geselecteerd.  

6.  Op de **implementatie-instellingen** pagina, controleert u of de implementatieactie is ingesteld op **installeren**, en het implementatiedoel is ingesteld op **vereist**.  

    > [!TIP]  
    >  Door het implementatiedoel in te stellen op **vereist**, u ervoor zorgen dat de toepassing is geïnstalleerd op computers die voldoen aan de vereisten die u instelt. Als u deze waarde instelt op **Beschikbaar**, kunnen gebruikers de toepassing op verzoek vanuit Software Center installeren.  

7.  Op de pagina **Planning** kunt u configureren wanneer de toepassing wordt geïnstalleerd. Selecteer voor dit voorbeeld **Zo snel mogelijk na het beschikbaar komen**.  

8.  Op de **gebruikerservaring** pagina **volgende** naar de standaardwaarden accepteren.  

9. Voltooi de wizard.  

Gebruik de informatie in de volgende **bewaken van de toepassing** sectie voor de status van de implementatie van uw toepassing.  

## <a name="monitor-the-application"></a>De toepassing controleren  
 In dit gedeelte gaat u een kort overzicht van de status van de implementatie van de toepassing die u zojuist hebt geïmplementeerd nemen.  

### <a name="to-review-the-deployment-status"></a>De implementatiestatus controleren  

1.  Kies in de Configuration Manager-console **bewaking** > **implementaties**.  

3.  Selecteer in de lijst met implementaties **Contoso-toepassing**.  

4.  Op de **Start** tabblad, in de **implementatie** groep, kiest u **Status weergeven**.  

5.  Selecteer een van de volgende tabbladen om meer statusupdates over de implementatie van de toepassing te bekijken:  

    -   **Geslaagde**: De toepassing is op de aangegeven computers geïnstalleerd.  

    -   **Bezig**: De toepassing is nog niet voltooid installeren.  

    -   **Fout**: Er is een fout opgetreden bij het installeren van de toepassing op de aangegeven computers. Er wordt ook meer informatie over de fout weergegeven.  

    -   **Niet voldaan aan vereisten**: Er is geen installatie is geprobeerd op de aangegeven apparaten omdat deze niet voldeed aan de vereisten die u hebt geconfigureerd (in dit voorbeeld, omdat ze niet worden uitgevoerd op Windows 10).  

    -   **Onbekende**: Configuration Manager kon geen gegevens over de status van de implementatie. Probeer het later opnieuw.  

> [!TIP]  
>  Er zijn enkele manieren waarop u toepassingsimplementaties kunt controleren. Zie voor meer details [toepassingen bewaken](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

## <a name="end-user-experience"></a>Eindgebruikerservaring  

Gebruikers die beschikken over computers die worden beheerd door Configuration Manager en actieve Windows 10 zien een bericht aan dat ze de Contoso-toepassing moeten installeren. Zodra de installatie van de voorwaarden worden geaccepteerd, wordt de toepassing wordt geïnstalleerd.  
