---
title: Configuratie-items maken voor Windows-computers client beheerd - Configuration Manager | Microsoft Docs
description: Instellingen beheren voor Windows-computers en servers met een aangepaste Windows-Desktops en Servers configuratie-item.
ms.custom: na
ms.date: 11/18/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1eb2fcaf-acac-4388-9b31-6cccafacaabe
caps.latest.revision: "9"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 9fe28782744a419acad9c1acec49ff8db6c0eaa6
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-system-center-configuration-manager-client"></a>Aangepaste configuratie-items voor Windows-desktopcomputers en -servercomputers maken die worden beheerd met de System Center Configuration Manager-client

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


De System Center Configuration Manager gebruiken **aangepaste Windows-Desktops en Servers** configuratie-item voor het beheren van instellingen voor Windows-computers en servers die worden beheerd door de Configuration Manager-client.  

## <a name="start-the-create-configuration-item-wizard"></a>Start de configuratiewizard-item

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **configuratie-Items**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  

4.  Geef op de pagina **Algemeen** van de **Wizard Configuratie-item maken** een naam en een optionele beschrijving voor het configuratie-item op.  

5.  Selecteer onder **Geef het type configuratie-item op dat u wilt maken** de optie **Windows-desktops en -servers (aangepast)**.  

    > [!TIP]  
    >  Als u instellingen voor de detectiemethode wilt opgeven om te controleren op het bestaan van een toepassing, selecteert u **Dit configuratie-item bevat toepassingsinstellingen**.  

6.  Klik op **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  

## <a name="provide-detection-method-information"></a>Gegevens voor detectiemethode opgeven  
 Gebruik deze procedure om gegevens voor de detectiemethode op te geven voor het configuratie-item.  

> [!NOTE]  
>  Dit geldt alleen als u **Dit configuratie-item bevat toepassingsinstellingen** hebt geselecteerd op de pagina **Algemeen** van de wizard.  

 Een detectiemethode in Configuration Manager bevat de regels die worden gebruikt om te detecteren of een toepassing is geïnstalleerd op een computer. Deze detectie vindt plaats voordat het configuratie-item wordt beoordeeld op naleving. Als u wilt verifiëren of een toepassing is geïnstalleerd, kunt u controleren of er een Windows Installer-bestand aanwezig is voor de toepassing, een aangepast script gebruiken of **Altijd aannemen dat de toepassing is geïnstalleerd** selecteren om het configuratie-item op naleving te controleren, ongeacht of de toepassing is geïnstalleerd.  

 Gebruik deze procedures om detectiemethoden te configureren in System Center Configuration Manager.  

### <a name="to-detect-an-application-installation-by-using-the-windows-installer-file"></a>De installatie van een toepassing detecteren met het Windows Installer-bestand  

1.  Schakel op de pagina **Detectiemethoden** van de wizard **Configuratie-item maken** het selectievakje **Detectie van Windows-installatieprogramma gebruiken** in.  

2.  Klik op **Openen**, blader naar het Windows Installer-bestand (.msi) dat u wilt detecteren en klik op **Openen**.  

3.  In het vak **Versie** wordt automatisch het versienummer ingevuld van het Windows Installer-bestand dat u hebt geselecteerd. U kunt een nieuwe versienummer in dit vak invoeren als de weergegeven waarde onjuist is.  

4.  Schakel het selectievakje **Deze toepassing is geïnstalleerd voor een of meer gebruikers** in als u elk gebruikersprofiel op de computer wilt detecteren.  

### <a name="to-detect-a-specific-application-and-deployment-type"></a>Een bepaalde toepassing en een implementatietype detecteren  

1.  Schakel op de pagina **Detectiemethoden** van de wizard **Configuratie-item configureren** het selectievakje **Een bepaalde toepassing en implementatietype detecteren** in en klik op **Selecteren**.  

2.  Selecteer in het dialoogvenster **Toepassing opgeven** de toepassing en een bijbehorend implementatietype dat u wilt detecteren.  

### <a name="to-detect-an-application-installation-by-using-a-custom-script"></a>De installatie van een toepassing detecteren met een aangepast script  

1.  Schakel op de pagina **Detectiemethoden** van de wizard **Configuratie-item maken** het selectievakje **Aangepast script gebruiken om deze toepassing te detecteren** in.  

2.  Selecteer in de lijst de taal van het script dat u wilt openen. Kies uit de volgende scripts:  

    -   **VBScript**  

    -   **JScript**  

    -   **PowerShell**  

3.  Klik op **Openen**, blader naar het script dat u wilt gebruiken en klik vervolgens op **Openen**.  

##  <a name="configure-settings"></a>Instellingen configureren  
 Gebruik deze procedure om de instellingen in het configuratie-item te configureren.  

 Instellingen vertegenwoordigen de zakelijke of technische voorwaarden die worden gebruikt voor het evalueren van naleving op clientapparaten. U kunt een nieuwe instelling configureren of naar een bestaande instelling op een referentiecomputer bladeren.  

1.  Klik op de pagina **Instellingen** van de wizard **Configuratie-item maken** op **Nieuw**.  

2.  Op het tabblad **Algemeen** van het dialoogvenster **Instellingen maken** geeft u de volgende gegevens op:  

    -   **Naam:** Geef een unieke naam voor de instelling. U kunt maximaal 256 tekens gebruiken.  

    -   **Beschrijving:** Voer een beschrijving voor de instelling. U kunt maximaal 256 tekens gebruiken.  

    -   **Instellingstype:** Kies in de lijst en configureer een van de volgende instellingstypen voor deze instelling gebruiken:  

        -   **Active Directory-query**  

             **LDAP-voorvoegsel** - Geef een geldig voorvoegsel op in de Active Directory Domain Services-query om de naleving vast te stellen op clientcomputers. U kunt **LDAP://** gebruiken of **GC://**, als u wilt zoeken in de globale catalogus.  

             **DN-naam**: Geef de DN-naam op van het Active Directory Domain Services-object dat op naleving wordt gecontroleerd op clientcomputers.  

             Als u een waarde gerelateerd aan een gebruiker met de naam John Smith in het domein corp.contoso.com wilt evalueren, voert u het volgende in:  

            -   **Zoekfilter**: Geef een optionele LDAP-filter op om de resultaten van de Active Directory Domain Services-query te verfijnen om de compatibiliteit vast te stellen op clientcomputers.  

                 Als u alle resultaten van de query wilt retourneren, voert u  **(objectklasse=\*)** in.  

            -   **Zoekbereik**: geef het zoekbereik op in Active Directory Domain Services/ U kunt kiezen uit:  

                -   **Basis**: hiermee zoekt u alleen in het opgegeven object.  

                -   **Eén niveau** -deze optie wordt niet gebruikt in deze versie van Configuration Manager.  

                -   **Substructuur**: hiermee zoekt u in het opgegeven object en de volledige substructuur in de map.  

            -   **Eigenschap**: hier geeft u de eigenschap op van een Active Directory Domain Services-object dat wordt gebruikt om de naleving te beoordelen op clientcomputers.  

                 Als u bijvoorbeeld een query wilt uitvoeren op de Active Directory-eigenschap **badPwdCount**, waarin wordt opgeslagen hoe vaak een gebruiker een wachtwoord onjuist invoert, voert u **badPwdCount** in dit veld in.  

            -   **Query**: hier wordt de query weergegeven die is samengesteld uit de invoer in **LDAP-voorvoegsel**, **DN-naam**, **Zoekfilter**, indien opgegeven, en **Eigenschap**. Deze vakken worden gebruikt om naleving op clientcomputers te beoordelen.  

             Raadpleeg de Windows Server-documentatie voor meer informatie over het maken van LDAP-query’s.  

        -   **Assembly**  

             Configureer het volgende voor dit instellingstype:  

            -   **Assembly-naam:** Hiermee geeft u de naam van het assembly-object dat u wilt zoeken. Deze naam mag niet dezelfde zijn als die van een ander assembly-object van hetzelfde type en moet zijn geregistreerd in de Global Assembly-cache. De assembly-naam mag maximaal 256 tekens lang zijn.  

             Een assembly is een stuk code dat tussen toepassingen kan worden gedeeld. Assembly's kunnen de bestandsnaamextensie .dll of .exe hebben. De Global Assembly-cache is een map met de naam *%systemroot%\Assembly* op clientcomputers waarin alle gedeelde assembly's zijn opgeslagen.  

        -   **Bestandssysteem**  

            -   **Type**: geef in de lijst aan of u wilt zoeken naar een **bestand** of **map**.  

            -   **Pad**: geef het pad op naar het opgegeven bestand of de map op clientcomputers. U kunt in het pad systeemomgevingsvariabelen specificeren en de *%USERPROFILE%*-omgevingsvariabele.  

                > [!NOTE]  
                >  Als u de omgevingsvariabele *%USERPROFILE%* gebruikt in het vak **Pad** of **Naam van bestand of map**, worden alle gebruikersprofielen op de clientcomputer doorzocht, wat kan leiden tot meerdere exemplaren van een gevonden bestand of map.  
                >   
                >  Als nalevingsinstellingen geen toegang tot het opgegeven pad hebben, wordt er een detectiefout gegenereerd. Er wordt ook een detectiefout gegenereerd als het bestand dat u zoekt momenteel in gebruik is.  

            -   **Bestands- of mapnaam**: geef de naam op van het bestands- of mapobject waarnaar moet worden gezocht. U kunt in de bestands- of map naam systeemomgevingsvariabelen specificeren en de *%USERPROFILE%*-omgevingsvariabele. U kunt ook de jokertekens * en ? in de bestandsnaam gebruiken.  

                > [!NOTE]  
                >  Als u een bestand of map opgeeft en hierbij jokertekens, wordt deze combinatie een groot aantal resultaten opleveren, kan leiden tot hoog bronnengebruik op de clientcomputer en veel netwerkverkeer wanneer resultaten rapporteren aan Configuration Manager.  

            -   **Inclusief submappen** – Schakel deze optie in als u in submappen wilt zoeken onder het opgegeven pad.  

            -   **Dit bestand of deze map is gekoppeld aan een 64-bits toepassing**: indien ingeschakeld, worden alleen 64-bits bestandslocaties (zoals *%ProgramFiles%*) gecontroleerd op 64-bits computers. Als deze optie niet is ingeschakeld, worden zowel 32-bits (zoals *% ProgramFiles(x86) %*) als 64-bits locaties gecontroleerd.  

                > [!NOTE]  
                >  Als hetzelfde bestand of dezelfde map zowel op de 64-bits als op de 32-bits systeembestandslocatie van dezelfde 64-bits computer bestaat, worden meerdere bestanden gedetecteerd door de globale voorwaarde.  

             Het instellingstype **Bestandssysteem** biedt geen ondersteuning voor de opgave van een UNC-pad naar een netwerkshare in het veld **Pad**.  

        -   **IIS Metabase**  

            -   **Metabasepad**: geef een geldig pad op naar de IIS Metabase (Internet Information Services).  

            -   **Eigenschaps-id** - Geef de numerieke eigenschap op van de IIS Metabase-instelling.  

        -   **Registersleutel**  

            -   **Component**: selecteer in de lijst de registercomponent waarin u wilt zoeken.  

            -   **Sleutel**: specificeer de naam van de registersleutel waarnaar u wilt zoeken. Gebruik de indeling *sleutel\subsleutel*.  

            -   **Deze registersleutel is gekoppeld aan een 64-bits toepassing**: hiermee geeft u op of naast de 32-bits registersleutels ook de 64-bits registersleutels moeten worden doorzocht op clients die worden uitgevoerd op een 64-bits versie van Windows.  

                > [!NOTE]  
                >  Als dezelfde registersleutel zowel op de 64-bits als op de 32-bits registerlocatie van dezelfde 64-bits computer bestaat, worden beide registersleutels gedetecteerd door de globale voorwaarde.  

        -   **Registerwaarde**  

            -   **Component**: selecteer in de lijst de registercomponent waarin u wilt zoeken.  

            -   **Sleutel**: specificeer de naam van de registersleutel waarnaar u wilt zoeken. Gebruik de indeling *sleutel\subsleutel*.  

            -   **Waarde**: specificeer de waarde die moet zijn opgenomen in de opgegeven registersleutel.  

            -   **Deze registersleutel is gekoppeld aan een 64-bits toepassing**: hiermee geeft u op of naast de 32-bits registersleutels ook de 64-bits registersleutels moeten worden doorzocht op clients die worden uitgevoerd op een 64-bits versie van Windows.  

                > [!NOTE]  
                >  Als dezelfde registersleutel zowel op de 64-bits als op de 32-bits registerlocatie van dezelfde 64-bits computer bestaat, worden beide registersleutels gedetecteerd door de globale voorwaarde.  

             U kunt ook klikken op **Bladeren** om te bladeren naar een registerlocatie op de computer of op een externe computer. Als u wilt bladeren naar een externe computer, moet u op de externe computer over beheerdersrechten beschikken en moet op de externe computer de Remote Registry-service worden uitgevoerd.  

        -   **Script**  

            -   **Detectiescript**: klik op **Toevoegen** om naar het script te bladeren dat u wilt gebruiken. U kunt Windows PowerShell-, VBScript- of Microsoft JScript-scripts gebruiken.  

            -   **Scripts uitvoeren met de referenties van de aangemelde gebruiker**: als u deze optie inschakelt, wordt het script uitgevoerd op clientcomputers met de referenties van de aangemelde gebruikers.  

                > [!NOTE]  
                >  De geretourneerde waarde door het script wordt gebruikt om de naleving van de globale voorwaarde vast te stellen. Wanneer u bijvoorbeeld VBScript gebruikt, kunt u de opdracht **WScript.Echo Result** gebruiken om de variabele waarde *Result* te retourneren naar de globale voorwaarde.  

        -   **SQL-query**  

            -   **SQL Server-exemplaar** – Kies of u de SQL-query wilt uitvoeren op het standaardexemplaar, alle exemplaren of op de naam van een specifiek database-exemplaar.  

                > [!NOTE]  
                >  De naam van het exemplaar moet verwijzen naar een lokaal exemplaar van de SQL Server. Gebruik een scriptinstelling om te verwijzen naar een geclusterd SQL server-exemplaar.  

            -   **Database**: geef de naam op van de Microsoft SQL Server-database waarvoor u de SQL query wilt uitvoeren.  

            -   **Kolom**: geef de naam van de kolom op die door de Transact-SQL-instructie wordt geretourneerd om de naleving van de globale voorwaarde vast te stellen.  

            -   **Transact-SQL-instructie**: geef de volledige SQL-query op die u wilt gebruiken voor de globale voorwaarde. U kunt ook op **Openen** klikken om een bestaande SQL-query te openen.  

                > [!IMPORTANT]  
                >  SQL Query-instellingen bieden geen ondersteuning voor SQL-opdrachten waarmee de database wordt gewijzigd. U kunt alleen SQL-opdrachten gebruiken waarmee gegevens uit de database worden gelezen.  

        -   **WQL-query**  

            -   **Naamruimte**: geef de WMI-naamruimte (Windows Management Instrumentation) op die wordt gebruikt om een WQL-query samen te stellen waarvan de naleving op clientcomputers wordt beoordeeld. De standaardwaarde is Root\cimv2.  

            -   **Klasse**: hier geeft u de WMI-klasse op die wordt gebruikt om een WQL-query samen te stellen waarvan de naleving op clientcomputers wordt beoordeeld.  

            -   **Eigenschap**: hier geeft u de WMI-eigenschap op die wordt gebruikt om een WQL-query samen te stellen waarvan de naleving op clientcomputers wordt beoordeeld.  

            -   **WHERE-component van WQL-query** - U kunt het item **WHERE-component van WQL-query** gebruiken om een WHERE-component te specificeren die moet worden toegepast op de opgegeven naamruimte en de eigenschap op clientcomputers.  

        -   **XPath-query**  

            -   **Pad**: geef het pad op naar het XML-bestand op clientcomputers die wordt gebruikt om naleving te beoordelen. Configuration Manager ondersteunt het gebruik van alle Windows-systeemomgevingsvariabelen en de *% USERPROFILE %* gebruikersvariabele in de padnaam.  

            -   **XML-bestandsnaam**: geef de naam van het bestand op dat de XML-query bevat die wordt gebruikt om naleving op clientcomputers te beoordelen.  

            -   **Inclusief submappen** - Schakel deze optie in als u in submappen wilt zoeken onder het opgegeven pad.  

            -   **Dit bestand is gekoppeld aan een 64-bits toepassing** -kiezen of de 64-bits systeembestandslocatie (*% windir %*\System32) moet worden doorzocht naast de 32-bits systeembestandslocatie (*% windir %*\Syswow64) op de Configuration Manager-clients die een 64-bits versie van Windows worden uitgevoerd.  

            -   **XPath-query**: geef een geldige, volledige query voor de XML Path-taal (XPath) op om de naleving op clientcomputers te beoordelen.  

            -   **Naamruimten**: hiermee opent u het dialoogvenster **XML-naamruimten** om naamruimten en voorvoegsels te identificeren voor gebruik tijdens de XPath-query.  

             Als u een versleuteld XML-bestand probeert te detecteren, vinden de instellingen voor naleving het bestand, maar levert de XPath-query geen resultaten op en wordt er geen fout gegenereerd.  

             Als de XPath-query ongeldig is, wordt de instelling geëvalueerd als niet-compatibel op clientcomputers.  

    -   **Gegevenstype:** Kies de indeling waarin de voorwaarde de gegevens retourneert voordat deze wordt gebruikt voor het evalueren van de instelling in de lijst. De lijst **Gegevenstype** wordt niet voor alle instellingstypen weergegeven.  

        > [!NOTE]  
        >  Het gegevenstype **Drijvende komma** ondersteunt alleen 3 cijfers na het decimaalteken.  

3.  Configureer aanvullende informatie over deze instelling onder de lijst **Instellingstype**. Welke items u kunt configureren, is afhankelijk van het instellingstype dat u hebt geselecteerd.  

    > [!NOTE]  
    >  Wanneer u instellingen van het type **Bestandssysteem**, **Registersleutel** en **Registerwaarde** maakt, kunt u op **Bladeren** klikken om de instelling te configureren op basis van waarden op een referentiecomputer. Als u wilt bladeren naar een registersleutel of waarde op een externe computer, moet op de externe computer de Remote Registry-service zijn ingeschakeld.  

4.  Klik op **OK** om de instelling op te slaan en het dialoogvenster **Instelling maken** te sluiten.  

##  <a name="configure-compliance-rules"></a>Compliantieregels configureren  
 Gebruik de volgende procedure om compliantieregels voor het configuratie-item te configureren.  

 Met compliantieregels geeft u de voorwaarden voor naleving van een configuratie-item op. Voordat een instelling kan worden beoordeeld op naleving, moet de instelling minimaal één compliantieregel hebben. Met WMI-, register- en scriptinstellingen kunt u waarden herstellen die niet compliant zijn. U kunt nieuwe regels maken of naar een bestaande instelling in een configuratie-item bladeren om regels hierin te selecteren.  

### <a name="to-create-a-compliance-rule"></a>Een compliantieregel maken  

1.  Klik op de pagina **Compliantieregels** van de wizard **Configuratie-item maken** op **Nieuw**.  

2.  Geef in het dialoogvenster **Regel maken** de volgende informatie op:  

    -   **Naam:** Voer een naam voor de compliantieregel.  

    -   **Beschrijving:** Voer een beschrijving voor de compliantieregel.  

    -   **Geselecteerde instelling:** Klik op **Bladeren** openen de **instelling selecteren** in het dialoogvenster. Selecteer de instelling waarvoor u een regel wilt definiëren of klik op **Nieuwe instelling**. Klik op **Selecteren** als u klaar bent.  

        > [!NOTE]  
        >  U kunt ook klikken op **Eigenschappen** om informatie over de geselecteerde instelling weer te geven.  

    -   **Regeltype:** Selecteer het type compliantieregel dat u wilt gebruiken:  

        -   **Waarde:** maak een regel waarmee de waarde die door de configuratie-item wordt geretourneerd, wordt vergeleken met een waarde die u opgeeft.  

        -   **Existentieel:** maak een regel om de instelling te beoordelen, afhankelijk van of deze op een clientapparaat bestaat of op basis van het aantal keren dat deze wordt gevonden.  

    -   Geef voor het regeltype **Waarde** de volgende informatie op:  

        -   **De instelling moet voldoen aan de volgende regel:** selecteer een operator en een waarde die worden beoordeeld op naleving van de geselecteerde instelling. U kunt de volgende operatoren gebruiken:  

            |Operator|Meer informatie|  
            |--------------|----------------------|  
            |Is gelijk aan|Geen aanvullende informatie|  
            |Niet gelijk aan|Geen aanvullende informatie|  
            |Groter dan|Geen aanvullende informatie|  
            |Kleiner dan|Geen aanvullende informatie|  
            |Tussen|Geen aanvullende informatie|  
            |Groter dan of gelijk aan|Geen aanvullende informatie|  
            |Kleiner dan of gelijk aan|Geen aanvullende informatie|  
            |Een van|Geef in het tekstvak één vermelding per regel op.|  
            |Geen|Geef in het tekstvak één vermelding per regel op.|  

        -   **Regels die niet compliant zijn herstellen, waar ondersteund**: Selecteer deze optie als u wilt dat Configuration Manager automatisch niet-compatibele regels oplost. Configuration Manager kan de volgende regeltypen automatisch herstellen:  

            -   **Registerwaarde**: de registerwaarde wordt hersteld als deze niet compatibel is en gemaakt als deze niet bestaat.  

            -   **Script** (door automatisch een herstelscript uit te voeren).  

            -   **WQL-Query**  

            > [!IMPORTANT]  
            >  U kunt niet-compatibele regels alleen herstellen als de regeloperator is ingesteld op **Is gelijk aan**.  

        -   **Niet-naleving melden als dit instellingsexemplaar niet wordt gevonden**: het configuratie-item rapporteert niet-naleving als deze instelling niet op clientcomputers is gevonden.  

        -   **Niet-nageleefd ernst voor rapporten:** Geef de ernst die wordt gerapporteerd (in Configuration Manager-rapporten) als deze compliantieregel mislukt. De beschikbare ernstniveaus zijn als volgt:  

            -   **Geen** Computers die niet voldoen aan deze compliantieregel niet ernst rapporteren.  

            -   **Informatie** Computers die niet voldoen aan deze compliantieregel fouternst van **informatie**.  

            -   **Waarschuwing** Computers die niet voldoen aan deze compliantieregel fouternst van **waarschuwing**.  

            -   **Kritieke** Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke**.  

            -   **Kritiek met gebeurtenis** Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke**. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  

        -   Geef voor het regeltype **Existentieel** de volgende informatie op:  

            > [!NOTE]  
            >  Welke opties worden weergegeven, hangt af van het instellingstype waarvoor u een regel configureert.  

            -   **De instelling moet bestaan op clientapparaten**  

            -   **De instelling mag niet bestaan op clientapparaten**  

            -   **De instelling komt het volgende aantal keren:**  

        -   **Niet-nageleefd ernst voor rapporten:** Geef de ernst die wordt gerapporteerd (in Configuration Manager-rapporten) als deze compliantieregel mislukt. De beschikbare ernstniveaus zijn als volgt:  

            -   **Geen** Computers die niet voldoen aan deze compliantieregel niet ernst rapporteren.  

            -   **Informatie** Computers die niet voldoen aan deze compliantieregel fouternst van **informatie**.  

            -   **Waarschuwing** Computers die niet voldoen aan deze compliantieregel fouternst van **waarschuwing**.  

            -   **Kritieke** Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke**.  

            -   **Kritiek met gebeurtenis** Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke**. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  

3.  Klik op **OK** om het dialoogvenster **Regel maken** te sluiten.  

##  <a name="specify-supported-platforms"></a>Ondersteunde platforms opgeven  
 Ondersteunde platforms zijn de besturingssystemen waarop een configuratie-item wordt beoordeeld op naleving.  

Selecteer op de pagina **Ondersteunde platforms** van de wizard **Configuratie-item maken** in de lijst de Windows-versies waarop het configuratie-item moet worden beoordeeld op naleving of klik op **Alles selecteren**.  

## <a name="complete-the-wizard"></a>Voltooi de wizard  
 Controleer welke acties moeten worden ondernomen op de pagina **Overzicht** van de wizard en voltooi de wizard. Het nieuwe configuratie-item wordt weergegeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving**.  
