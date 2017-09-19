---
title: Globale voorwaarden maken | Microsoft Docs
description: "Algemene voorwaarden om op te geven hoe een toepassing beschikbaar wordt gesteld en geïmplementeerd voor clientapparaten maken."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d5f871a-19dc-4bd3-a3ad-4230c7a69f1b
caps.latest.revision: "7"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 6aedab4ab23749061ec103e0de92edafdad13d33
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-create-global-conditions-in-system-center-configuration-manager"></a>Globale voorwaarden maken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager globale voorwaarden zijn regels die staan voor zakelijke of technische voorwaarden die u gebruiken kunt om op te geven hoe een toepassing beschikbaar wordt gesteld en geïmplementeerd voor clientapparaten. Globale voorwaarden worden geopend via de pagina **Vereisten** van de wizard Implementatietype maken.  

> [!NOTE]  
>  Globale voorwaarden alleen vanaf de site waar ze zijn gemaakt, kunt u bewerken.  

 Gebruik de volgende procedures Configuration Manager globale voorwaarden maken.  

## <a name="provide-basic-information-about-the-global-condition"></a>Algemene gegevens over de globale voorwaarde opgeven  
 Verschillende soorten globale voorwaarden zijn beschikbaar. Verschillende opties zijn gekoppeld aan de verschillende typen globale voorwaarden. Wanneer u een specifiek globale voorwaardetype kiest selecteert, ziet u Configuration Manager de opties die van toepassing zijn op uw selectie.  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **globale voorwaarden**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **globale voorwaarde maken**.  

4.  Geef in het dialoogvenster **Globale voorwaarde maken** een naam op en een optionele beschrijving voor de globale voorwaarde.  

5.  In de **apparaattype** vervolgkeuzelijst Kies of de globale voorwaarde geldt voor een **Windows** computer of een **Windows Mobile** apparaat.  

6.  Kies in het vervolgkeuzemenu **Voorwaardetype** een van de volgende opties:  

    -   **Instelling** – Met deze optie kunt u controleren of er sprake is van een of meerdere items op clientapparaten. U kunt bijvoorbeeld controleren of een sleutelwaarde bestand, map of registersleutelwaarde op een clientapparaat bestaat.  

    -   **Expressie** – deze optie kunt u complexere regels instellen om te controleren of de voorwaarde is voldaan op clientapparaten. U kunt bijvoorbeeld controleren als het fysieke geheugen op een computer tussen 2 en 4 GB groot is of als een mobiel apparaat via een aanraakscherm verloopt invoer.  

## <a name="set-up-rules-for-the-global-condition"></a>Instellen van regels voor de globale voorwaarde  
 De procedure voor het definiëren van de globale voorwaarde regels is verschillend, afhankelijk van het configureren van een instelling of een expressie. Gebruik hier de toepasselijke procedure voor het instellen van een instelling of een expressie voor de globale voorwaarde.  

### <a name="to-set-up-a-setting-for-the-global-condition"></a>Voor het instellen van een instelling voor de globale voorwaarde  

1.  Kies in het vervolgkeuzemenu **Voorwaardetype** **Instelling**.  

2.  Kies in het vervolgkeuzemenu **Instellingstype** het item dat u wilt gebruiken als de voorwaarde waarvoor u vereisten wilt controleren. De volgende Instellingstypen en configuraties zijn beschikbaar.  

    -   **Active Directory-query**  

        -   **LDAP-voorvoegsel** - Geef een geldig LDAP-voorvoegsel op in de Active Directory Domain Services-query om de compatibiliteit vast te stellen op clientcomputers. U kunt **LDAP://** of **GC://**gebruiken.  

        -   **DN-naam (Distinguished Name)** -Geef de DN-naam van het Active Directory Domain Services-object dat wordt beoordeeld op naleving op clientcomputers.  

        -   **Zoekfilter** - Geef een optionele LDAP-filter op om de resultaten van de Active Directory Domain Services-query te verfijnen om de compatibiliteit vast te stellen op clientcomputers.  

        -   **Zoekbereik** - Geef het zoekbereik op in Active Directory Domain Services:  

            -   **Base** -query's alleen het opgegeven object.  

            -   **Eén niveau** -deze optie wordt niet gebruikt in deze versie van Configuration Manager.  

            -   **De substructuur** -query's van het opgegeven object en de volledige substructuur in de map.  

        -   **Eigenschap** - Hier specificeert u de eigenschap van een Active Directory Domain Services-object dat wordt gebruikt om de compatibiliteit vast te stellen op clientcomputers.  

        -   **Query** -ziet u de LDAP-query die wordt samengesteld uit de invoer in **LDAP-voorvoegsel**, **DN-naam (Distinguished Name)**, **zoekfilter** indien opgegeven, en **eigenschap**. Deze query wordt gebruikt om de compatibiliteit vast te stellen op clientcomputers.  

    -   **Assembly**  

        -   **Naam van assembly** - Hier geeft u de naam op van het assembly-object waarnaar u wilt zoeken. De naam mag niet hetzelfde zijn als elk ander assembly-object van hetzelfde type en de naam moet worden geregistreerd in de Global Assembly Cache. De assembly-naam mag maximaal 256 tekens bestaan.  

        > [!NOTE]  
        >  Een assembly is een stuk code dat tussen toepassingen kan worden gedeeld. Assembly's kunnen de bestandsnaamextensie .dll of .exe hebben. De Global Assembly-cache is een map met de naam *%systemroot%\assembly* op clientcomputers waarin alle gedeelde assembly's zijn opgeslagen.  

    -   **Bestandssysteem**  

        -   **Type** – Selecteer in de vervolgkeuzelijst kiezen of u zoeken wilt naar een **bestand** of een **map**.  

        -   **Pad** - Geef het pad op naar het gespecificeerde bestand of de map op clientcomputers. U kunt in het pad systeemomgevingsvariabelen specificeren en de *%USERPROFILE%* -omgevingsvariabele.  

            > [!NOTE]  
            >  Als u de *%USERPROFILE%* -omgevingsvariabele gebruikt in het **Pad** of in de velden **Bestands- of mapnaam** , wordt in alle gebruikersprofielen op de clientcomputer gezocht. Dit kan leiden tot het vinden van meerdere exemplaren van het bestand of de map.  

        -   **Bestands- of mapnaam** - Geef de naam op van het bestand of het mapobject waarnaar moet worden gezocht. U kunt in de bestands- of map naam systeemomgevingsvariabelen specificeren en de *%USERPROFILE%* -omgevingsvariabele. U kunt ook de * en? jokertekens in de bestandsnaam.  

            > [!NOTE]  
            >  Als u een bestands- of mapnaam opgeeft en hierbij jokertekens gebruikt, kunt u een groot aantal resultaten krijgen. Dit kan leiden tot hoog bronnengebruik op de clientcomputer en veel netwerkverkeer wanneer resultaten rapporteren aan Configuration Manager.  

        -   **Inclusief submappen** – Schakel deze optie in als u in submappen wilt zoeken onder het opgegeven pad.  

        -   **Dit bestand of deze map is gekoppeld aan een 64-bits toepassing** -kiezen of de 64-bits systeembestandslocatie (*% windir %*\system32) moet worden doorzocht naast de 32-bits systeembestandslocatie (*% windir %*\syswow64) op de Configuration Manager-clients die een 64-bits versie van Windows uitvoeren.  

            > [!NOTE]  
            >  Als hetzelfde bestand of dezelfde map bestaat in zowel de 64-bits als de 32-bits systeembestandslocatie op dezelfde 64-bits computer, worden door de globale voorwaarde meerdere bestanden gevonden.  

         Het instellingstype **Bestandssysteem** ondersteunt geen specificatie van een UNC-pad naar een netwerkshare in het veld **Pad** .  

    -   **IIS Metabase**  

        -   **Metabasepad** - Geef een geldig pad op naar de IIS Metabase.  

        -   **Eigenschaps-id** - Geef de numerieke eigenschap op van de IIS Metabase-instelling.  

    -   **Registersleutel**  

        -   **Hive** – Selecteer in de vervolgkeuzelijst de registercomponent waarin u zoeken wilt kiezen.  

        -   **Sleutel** - Specificeer de naam van de registersleutel waarnaar u wilt zoeken. De gebruikte indeling moet *sleutel\subsleutel*zijn.  

        -   **Deze registersleutel is gekoppeld aan een 64-bits toepassing** - Hiermee geeft u op of de 64-bits registersleutels moeten worden doorzocht naast de 32-bits registersleutels op clients die worden uitgevoerd op een 64-bits versie van Windows.  

            > [!NOTE]  
            >  Als hetzelfde bestand of dezelfde map bestaat in zowel de 64-bits als de 32-bits systeembestandslocatie op dezelfde 64-bits computer, worden door de globale voorwaarde meerdere bestanden gevonden.  

    -   **Registerwaarde**  

        -   **Component** - Selecteer in de vervolgkeuzelijst de registercomponent waarin u wilt zoeken.  

        -   **Sleutel** - Specificeer de naam van de registersleutel waarnaar u wilt zoeken. De gebruikte indeling moet *sleutel\subsleutel*zijn.  

        -   **Waarde** – Specificeer de waarde die moet zijn opgenomen in de opgegeven registersleutel.  

        -   **Deze registersleutel is gekoppeld aan een 64-bits toepassing** - Hiermee geeft u op of de 64-bits registersleutels moeten worden doorzocht naast de 32-bits registersleutels op clients die worden uitgevoerd op een 64-bits versie van Windows.  

            > [!NOTE]  
            >  Als hetzelfde bestand of dezelfde map bestaat in zowel de 64-bits als de 32-bits systeembestandslocatie op dezelfde 64-bits computer, worden door de globale voorwaarde meerdere bestanden gevonden.  

    -   **Script**  

        -   **Detectiescript** – Kies **toevoegen** invoeren of blader naar het script te gebruiken. U kunt Windows PowerShell, VBScript of JScript-scripts gebruiken.  

        -   **Scripts uitvoeren met behulp van de aangemelde gebruikersreferenties** – als u deze optie inschakelt, wordt het script uitgevoerd op clientcomputers met de referenties van de gebruiker die is aangemeld.  

            > [!NOTE]  
            >  De waarde die het script heeft geretourneerd wordt gebruikt om de compatibiliteit vast te stellen van de globale voorwaarde. Bijvoorbeeld, wanneer u VBScript gebruikt, kunt u de **WScript.Echo Result** opdracht naar de variabele waarde resultaat te retourneren naar de globale voorwaarde.  
            >   
            >  Als uw script meerdere waarden retourneert, wordt deze waarden moeten zich op één regel en van elkaar gescheiden door puntkomma's. Als iedere waarde op een afzonderlijke regel staat, mislukt de evaluatie.  

    -   **SQL-query**  

        -   **SQL Server-exemplaar** – Kies of u de SQL-query wilt uitvoeren op het standaardexemplaar, alle exemplaren of op de naam van een specifiek database-exemplaar.  

            > [!NOTE]  
            >  De naam van het exemplaar moet verwijzen naar een lokaal exemplaar van de SQL Server. Gebruik een scriptinstelling om te verwijzen naar een geclusterd SQL server-exemplaar.  

        -   **Database** - Geef de naam op van de Microsoft SQL Server-database waarvoor u de SQL query wilt uitvoeren.  

        -   **Kolom** - Geef de naam van de kolom op die door de Transact-SQL-instructie is geretourneerd om de compatibiliteit vast te stellen van de globale voorwaarde.  

        -   **Transact-SQL-instructie** – Geef de volledige SQL-query op die u wilt gebruiken voor de globale voorwaarde. U kunt ook **openen** openen van een bestaande SQL-query.  

    -   **WQL-query**  

        -   **Naamruimte** - Specificeer de WMI-naamruimte die wordt gebruikt om een WQL-query samen te stellen waarvoor de compatibiliteit op clientcomputers wordt vastgesteld. De standaardwaarde is Root\cimv2.  

        -   **Klasse** - Hier geeft u de WMI-klasse op die wordt gebruikt om een WQL-query samen te stellen waarvoor de compatibiliteit op clientcomputers wordt vastgesteld.  

        -   **Eigenschap** - Hier geeft u de WMI-eigenschap op die wordt gebruikt om een WQL-query samen te stellen waarvoor de compatibiliteit op clientcomputers wordt vastgesteld.  

        -   **WHERE-component van WQL-query** - U kunt het item **WHERE-component van WQL-query** gebruiken om een WHERE-component te specificeren die moet worden toegepast op de opgegeven naamruimte en de eigenschap op clientcomputers.  

    -   **XPath-query**  

        -   **Pad** - Geef het pad op naar het XML-bestand op clientcomputers die worden gebruikt om compatibiliteit te beoordelen. Configuration Manager ondersteunt het gebruik van alle Windows-systeemomgevingsvariabelen en de *% USERPROFILE %* gebruikersvariabele in de padnaam.  

        -   **XML-bestandsnaam** -Geef de bestandsnaam met de XML-query moet worden gebruikt om naleving op clientcomputers te beoordelen.  

        -   **Inclusief submappen** - Schakel deze optie in als u in submappen wilt zoeken onder het opgegeven pad.  

        -   **Dit bestand is gekoppeld aan een 64-bits toepassing** -kiezen of de 64-bits systeembestandslocatie (*% windir %*\system32) moet worden doorzocht naast de 32-bits systeembestandslocatie (*% windir %*\syswow64) op de Configuration Manager-clients die een 64-bits versie van Windows uitvoeren.  

        -   **XPath-query** - Geef een geldig volledige XML Path-taal (XPath)-query om de compatibiliteit op clientcomputers vast te stellen.  

        -   **Naamruimten** - Hiermee opent u het dialoogvenster **XML-naamruimten** om naamruimten en voorvoegsels te identificeren voor gebruik tijdens de XPath-query.  

3.  Kies in de vervolgkeuzelijst **Gegevenstype** de indeling waarin de gegevens worden geretourneerd door de voorwaarde voordat deze wordt gebruikt om vereisten te controleren.  

    > [!NOTE]  
    >  De **gegevenstype** vervolgkeuzelijst wordt niet voor alle instellingstypes weergegeven.  

4.  Instellen van meer informatie over deze instelling onder de **Instellingstype** vervolgkeuzelijst. De items die u kunt instellen, varieert, afhankelijk van het Instellingstype dat u hebt geselecteerd.  

5.  Kies **OK** de regel op te slaan en sluit de **globale voorwaarde maken** in het dialoogvenster.  

### <a name="set-up-an-expression-for-the-global-condition"></a>Instellen van een expressie voor de globale voorwaarde  

1.  Kies in de vervolgkeuzelijst **Voorwaardetype** **Instelling**.  

2.  Kies **component toevoegen** openen de **component toevoegen** in het dialoogvenster.  

3.  Selecteer in de vervolgkeuzelijst **Categorie selecteren** of deze expressie voor een apparaat of voor een gebruiker is bedoeld. U kunt ook **Aangepast** selecteren om een vooraf geconfigureerde globale voorwaarde te gebruiken.  

4.  Selecteer in de vervolgkeuzelijst **Selecteer een voorwaarde** de voorwaarde die moet worden gebruikt om vast te stellen of de gebruiker of het apparaat voldoet aan de regelvereisten. De inhoud van deze lijst varieert op basis van de geselecteerde categorie.  

5.  Selecteer in de vervolgkeuzelijst **Operator kiezen** de operator die wordt gebruikt om de geselecteerde voorwaarde te vergelijken met de opgegeven waarde om vast te stellen of de gebruiker of het apparaat aan de regelvereisten voldoet. De beschikbare operators variëren op basis van de geselecteerde voorwaarde.  

6.  Voer in het veld **Waarde** de waarden in die worden gebruikt met de geselecteerde voorwaarde en operator om vast te stellen of de gebruiker of het apparaat voldoet aan de regelvereisten. De beschikbare waarden variëren op basis van de geselecteerde voorwaarde en de geselecteerde operator.  

7.  Kies **OK** de expressie opslaan en sluiten de **component toevoegen** in het dialoogvenster.  

8.  Wanneer u klaar bent met het componenten toe te voegen aan de globale voorwaarde kiest **OK** sluiten de **globale voorwaarde maken** in het dialoogvenster en de globale voorwaarde op te slaan.  
