---
title: Mac-computertoepassingen maken
titleSuffix: Configuration Manager
description: Zie welke overwegingen u moet rekening account wanneer u maken en implementeren van toepassingen voor Mac-computers.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab1aecdd-d943-44f5-b0a9-e8fe7439e5d6
caps.latest.revision: "9"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 912632c672c49deefc946e089dad6a82454c4b67
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-mac-computer-applications-with-system-center-configuration-manager"></a>Mac-computertoepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Houd rekening met de volgende overwegingen wanneer u maken en implementeren van toepassingen voor Mac-computers.  

> [!IMPORTANT]  
>  De procedures in dit onderwerp wordt uitgelegd informatie over het implementeren van toepassingen op Mac-computers waarop u Configuration Manager-client hebt geïnstalleerd. Mac-computers die u hebt ingeschreven bij Microsoft Intune, bieden geen ondersteuning voor de implementatie van toepassingen.  

## <a name="general-considerations"></a>Algemene overwegingen  
 System Center Configuration Manager kunt u toepassingen implementeert voor Mac-computers waarop de Configuration Manager Mac-client wordt uitgevoerd. De stappen om software te implementeren op Mac-computers zijn vergelijkbaar met de stappen om software te implementeren op Windows-computers. Echter, voordat u maken en implementeren van toepassingen voor Mac-computers die worden beheerd door Configuration Manager, het volgende overwegen:  

-   Voordat u Mac-toepassingspakketten op Mac-computers implementeren kunt, moet u de **CMAppUtil** hulpprogramma op een Mac-computer deze om toepassingen te converteren naar een indeling die kan worden gelezen door Configuration Manager.  

-   Configuration Manager biedt geen ondersteuning voor de implementatie van Mac-toepassingen voor gebruikers. In plaats daarvan moeten deze implementaties worden aangebracht op een apparaat. Op deze manier voor Mac-toepassingsimplementaties, Configuration Manager geen ondersteuning voor de **software implementeren op het primaire apparaat van de gebruiker** kiezen op de **implementatie-instellingen** pagina van de **Wizard Software implementeren**.  

-   Mac-toepassingen ondersteunen gesimuleerde implementaties.  

-   U kunt geen toepassingen implementeren op Mac-computers die het doel **Beschikbaar**hebben.  

-   De optie om ontwaakpakketten te zenden wanneer u software implementeert, is niet ondersteund voor Mac-computers.  

-   Mac-computers ondersteunen geen Background Intelligent Transfer Service (BITS) om toepassingsinhoud te downloaden. Als het downloaden van een toepassing mislukt, opnieuw wordt gestart vanaf het begin.  

-   Configuration Manager ondersteunt geen globale voorwaarden wanneer u implementatietypes voor Mac-computers maakt.  

## <a name="steps-to-create-and-deploy-an-application"></a>Stappen voor het maken en implementeren van een toepassing  
 De volgende tabel bevat de stappen, details en informatie voor het maken en implementeren van toepassingen voor Mac-computers.  

|Stap|Details|  
|----------|-------------|  
|**Stap 1**: Mac-toepassingen voor Configuration Manager voorbereiden|Voordat u Configuration Manager-toepassingen Mac-softwarepakketten maken kunt, moet u de **CMAppUtil** hulpprogramma op een Mac-computer te converteren van de Mac-software naar een Configuration Manager**cmmac** bestand.|  
|**Stap 2**: Maak een Configuration Manager-toepassing die de Mac-software bevat|Gebruik de **Wizard toepassing maken** voor het maken van een toepassing voor de Mac-software.|  
|**Stap 3**: Een implementatietype voor de Mac-toepassing maken|Deze stap is enkel vereist indien u niet automatisch deze informatie importeerde van de toepassing.|  
|**Stap 4**: De Mac-toepassing implementeren|Gebruik de **Wizard Software implementeren** om de toepassing op Mac-computers te implementeren.|  
|**Stap 5**: Bewaak de implementatie van de Mac-toepassing|Het slagingspercentage van toepassingsimplementaties voor Mac-computers bewaken.|  

## <a name="supplemental-procedures-to-create-and-deploy-applications-for-mac-computers"></a>Aanvullende procedures voor het maken en implementeren van toepassingen voor Mac-Computers  
 Gebruik de volgende procedures om te maken en implementeren van toepassingen voor Mac-computers die worden beheerd door Configuration Manager.  

###  <a name="step-1-prepare-mac-applications-for-configuration-manager"></a>Stap 1: Mac-toepassingen voor Configuration Manager voorbereiden  
 Het proces voor het maken en implementeren van Configuration Manager-toepassingen op Mac-computers is vergelijkbaar met het implementatieproces voor Windows-computers. Voordat u Configuration Manager toepassingen die Mac-implementatietypes bevatten maken, moet u de toepassingen voorbereiden met behulp van de **CMAppUtil** hulpprogramma. Dit hulpprogramma is gedownload met de installatiebestanden van de Mac-client. Met het hulpprogramma **CMAppUtil** wordt informatie over de toepassing verzameld, waaronder gegevens van de volgende Mac-pakketten:  

-   Apple-schijfimage (.dmg)  

-   Metapakketbestand (MPKG)  

-   Mac OS X Installer-pakket (.pkg)  

-   Mac OS X-toepassing (.app)  

Nadat het hulpprogramma **CMAppUtil** toepassingsgegevens heeft verzameld, wordt een bestand gemaakt met de extensie **.cmmac**. Dit bestand bevat installatiebestanden voor de Mac-software en informatie over detectiemethodes die gebruikt kunnen worden om te beoordelen of de toepassing reeds geïnstalleerd is. Met**CMAppUtil** kunt u ook **DMG** -bestanden verwerken die meerdere Mac-toepassingen bevatten, en kunt u voor elke toepassing andere implementatietypen maken.  

1.  Kopieer het installatiepakket voor de Mac-software naar de map op de Mac-computer waarnaar u de inhoud hebt uitgepakt van het bestand **macclient.dmg** dat u hebt gedownload van het Microsoft Downloadcentrum.  

2.  Open op dezelfde Mac-computer een terminalvenster en ga naar de map waarnaar u de inhoud van het bestand **macclient.dmg** hebt uitgepakt.  

3.  Navigeer naar de **extra** map en typ de volgende opdrachtregel:  

     **./CMAppUtil** *<eigenschappen\>*  

     Stel dat u wilt converteren van de inhoud van een Apple schijfimage-bestand met de naam **MySoftware.dmg** die opgeslagen in de bureaubladmap van de gebruiker in een **cmmac** bestand in dezelfde map. Wilt u ook maken **cmmac** bestanden voor alle toepassingen die zijn gevonden in het schijfimage-bestand. Gebruik hiervoor de volgende opdrachtregel:  

     **./CMApputil –c /Gebruikers/** *<gebruikersnaam\>* **/Bureaublad/MySoftware.dmg -o /Gebruikers/** *<gebruikersnaam\>* **/Bureaublad -a**  

    > [!NOTE]  
    >  De toepassingsnaam mag niet langer zijn dan 128 tekens.  

     Gebruik de opdrachtregeleigenschappen in de volgende tabel als u opties wilt configureren voor **CMAppUtil**:  

    |Eigenschap|Meer informatie|  
    |--------------|----------------------|  
    |**-h**|Geeft de beschikbare eigenschappen van de opdrachtregel weer.|  
    |**-r**|Voert de **detection.xml** van het opgegeven **CMMAC** -bestand uit naar **stdout**. De uitvoer bevat de detectieparameters en de versie van **CMAppUtil** waarmee het **CMMAC** -bestand is gemaakt.|  
    |**-c**|Hiermee geeft u het bronbestand op dat moet worden geconverteerd.|  
    |**-o**|Hiermee geeft u het uitvoerpad in combinatie met de – c eigenschap.|  
    |**-a**|Maakt automatisch .cmmac-bestanden in combinatie met de – c eigenschap voor alle toepassingen en pakketten in het schijfimage-bestand.|  
    |**-s**|Hiermee slaat u het genereren van het bestand **detection.xml** over als er geen detectieparameters worden gevonden. Het **CMMAC** -bestand wordt dan zonder het bestand **detection.xml** gemaakt.|  
    |**-v**|Hiermee wordt meer gedetailleerde uitvoer van het hulpprogramma **CMAppUtil** evenals diagnostische informatie weergegeven.|  

4.  Controleer of het **CMMAC** -bestand in de opgegeven uitvoermap is gemaakt.  

###  <a name="create-a-configuration-manager-application-that-contains-the-mac-software"></a>Maak een Configuration Manager-toepassing die de Mac-software bevat  

Gebruik de volgende procedure kunt u een toepassing maken voor Mac-computers die worden beheerd door Configuration Manager.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **toepassing maken**.  

4.  Op de **algemene** pagina van de **Wizard toepassing maken**, selecteer **automatisch detecteren van informatie over deze toepassing uit de installatiebestanden van**.  

    > [!NOTE]  
    >  Als u opgeven van informatie over de toepassing zelf wilt, selecteert u **de toepassingsinformatie handmatig opgeven**. Zie [Toepassingen maken met System Center Configuration Manager](../../apps/deploy-use/create-applications.md) voor meer informatie over het handmatig opgeven van informatie.  

5.  Selecteer in de vervolgkeuzelijst **Type** de optie **Mac OS X**.  

6.  In de **locatie** veld, geeft u het UNC-pad in het formulier  *\\ \\< server\>\\< delen\>\\< filename\>*  naar het installatiebestand van de Mac-toepassing (**cmmac** bestand) dat de toepassingsinformatie zal detecteren. U kunt ook kiezen **Bladeren** om te bladeren naar en geef de locatie van de installatie.  

    > [!NOTE]  
    >  U moet toegang hebben tot het UNC-pad dat de toepassing bevat.  

7.  Kies **volgende**.  

8.  Op de **informatie importeren** pagina van de **Wizard toepassing maken**, lees de informatie die geïmporteerd werd. Indien nodig, kunt u **vorige** teruggaan en eventuele fouten te corrigeren. Kies **volgende** om door te gaan.  

9. Op de **algemene informatie** pagina van de **Wizard toepassing maken**, informatie over de toepassing zoals de toepassingsnaam, opmerkingen, versie en optionele referentie om te verwijzen naar de toepassing in de Configuration Manager-console opgeven.  

    > [!NOTE]  
    >  Sommige van de informatie over de toepassing mogelijk al op deze pagina als deze eerder werd verkregen van de installatiebestanden van de toepassing.  

10. Kies **volgende**, Controleer de toepassingsinformatie op de **samenvatting** pagina en voltooi vervolgens de **Wizard toepassing maken**.  

11. De nieuwe toepassing wordt weergegeven in de **toepassingen** knooppunt van de Configuration Manager-console.  

###  <a name="step-3-create-a-deployment-type-for-the-mac-application"></a>Stap 3: Een implementatietype voor de Mac-toepassing maken  
 Gebruik de volgende procedure voor het maken van een implementatietype voor Mac-computers die worden beheerd door Configuration Manager.  

> [!NOTE]  
>  Als u automatisch informatie over de toepassing in geïmporteerd de **Wizard toepassing maken**, een implementatietype voor de toepassing is mogelijk al gemaakt.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **toepassingen**.  

3.  Selecteer een toepassing. Klik op de **Start** tabblad, in de **toepassing** groep, kiest u **implementatietype maken** voor het maken van een nieuw implementatietype voor deze toepassing.  

    > [!NOTE]  
    >  U kunt ook starten de **Wizard implementatietype maken** van de **Wizard toepassing maken** en van de **implementatietypen** tabblad van de *< toepassingsnaam\>*  **eigenschappen** in het dialoogvenster.  

4.  Op de **algemene** pagina van de **Wizard implementatietype maken**, in de **Type** vervolgkeuzelijst, selecteer **Mac OS X**.  

5.  In de **locatie** veld, geeft u het UNC-pad in het formulier \\ \\< server\>\\< delen\>\\< filename\> naar het installatiebestand van de toepassing (**cmmac** bestand). U kunt ook kiezen **Bladeren** om te bladeren naar en geef de locatie van de installatie.  

    > [!NOTE]  
    >  U moet toegang hebben tot het UNC-pad dat de toepassing bevat.  

6.  Kies **volgende**.  

7.  Controleer op de pagina **Informatie importeren** van de **Wizard implementatietype maken**de informatie die is geïmporteerd. Kies indien nodig **vorige** teruggaan en eventuele fouten te corrigeren. Kies **volgende** om door te gaan.  

8.  Geef op de pagina **Algemene informatie** van de **wizard Implementatietype maken**informatie op over de toepassing, zoals de toepassingsnaam, opmerkingen en de talen waarin het implementatietype beschikbaar is.  

    > [!NOTE]  
    >  Sommige van de implementatietype-informatie mogelijk al op deze pagina als deze eerder werd verkregen van de installatiebestanden van de toepassing.  

9. Kies **volgende**.  

10. Op de **vereisten** pagina van de **Wizard implementatietype maken**, kunt u de voorwaarden waaraan moeten worden voldaan voordat het implementatietype op Mac-computers kan worden geïnstalleerd.  

11. Kies **toevoegen** openen de **vereiste maken** dialoogvenster vak en een nieuwe vereiste toe te voegen.  

    > [!NOTE]  
    >  U kunt ook nieuwe vereisten toevoegen op de **vereisten** tabblad van de *< naam implementatietype\>*  **eigenschappen** in het dialoogvenster.  

12. Selecteer in de vervolgkeuzelijst **Categorie** dat dit een vereiste voor een apparaat is.  

13. Van de **voorwaarde** vervolgkeuzelijst, selecteert u de voorwaarde die u gebruiken om te beoordelen wilt of de Mac-computer voldoet aan de installatievereisten. De inhoud van deze lijst varieert, afhankelijk van de categorie die u selecteert.  

14. Van de **Operator** vervolgkeuzelijst kiest u de operator moet worden gebruikt om te vergelijken van de geselecteerde voorwaarde en de opgegeven waarde om te beoordelen of de gebruiker of het apparaat voldoet aan de installatievereisten. De beschikbare operators variëren, afhankelijk van de geselecteerde voorwaarde.  

15. In de **waarde** veld, geeft u de waarden voor gebruik met de geselecteerde voorwaarde en operator om te beoordelen of de gebruiker of het apparaat aan de installatievoorwaarde voldoet. De beschikbare waarden variëren afhankelijk van de voorwaarde en operator die u selecteert.

16. Kies **OK** om op te slaan de vereisteregel naar en uitgang uit het **vereiste maken** in het dialoogvenster.  

17. Op de **vereisten** pagina van de **Wizard implementatietype maken**, kies **volgende**.  

18. Controleer op de pagina **Overzicht** van de **wizard Implementatietype maken**de acties die de wizard moet uitvoeren.  Kies indien nodig **vorige** teruggaan en implementatie-instellingen te wijzigen. Kies **volgende** om het implementatietype te maken.  

19. Na de **voortgang** pagina is voltooid, controleert u de acties die werden genomen en kies vervolgens **sluiten** voltooid de **Wizard implementatietype maken**.  

20. Als u deze wizard startte vanuit de **Wizard toepassing maken**, gaat u terug naar de **implementatietypen** pagina.  

###  <a name="deploy-the-mac-application"></a>De Mac-toepassing implementeren  
 De stappen om een toepassing op Mac-computers te implementeren zijn dezelfde als de stappen voor het implementeren van een toepassing op Windows-computers, met uitzondering van de volgende verschillen:  

-   De implementatie van toepassingen aan gebruikers wordt niet ondersteund.  

-   Implementaties die het doel **Beschikbaar** hebben, worden niet ondersteund.  

-   De **software implementeren op het primaire apparaat van de gebruiker** kiezen op de **implementatie-instellingen** pagina van de **Wizard Software implementeren** wordt niet ondersteund.  

-   Omdat Mac-computers Software Center, de instelling niet ondersteunen **gebruikersmeldingen** op de **gebruikerservaring** pagina van de **Wizard Software implementeren** wordt genegeerd.  

-   De optie om ontwaakpakketten te zenden wanneer u software implementeert, is niet ondersteund voor Mac-computers.  

> [!NOTE]  
>  U kunt een verzameling met alleen Mac-computers opbouwen. Om dit te doen, een verzameling maken die gebruikmaakt van een queryregel en gebruikt in het voorbeeld WQL-query in de [query's maken](../../core/servers/manage/create-queries.md) onderwerp.  

 Zie voor meer informatie [toepassingen implementeren](../../apps/deploy-use/deploy-applications.md).  

###  <a name="step-5-monitor-the-deployment-of-the-mac-application"></a>Stap 5: Bewaak de implementatie van de Mac-toepassing  
 U kunt hetzelfde proces gebruiken voor het bewaken van toepassingsimplementaties voor Mac-computers, zoals u zou doen voor toepassingsimplementaties op Windows-computers bewaken.  

 Zie voor meer informatie [toepassingen bewaken](/sccm/apps/deploy-use/monitor-applications-from-the-console).  
