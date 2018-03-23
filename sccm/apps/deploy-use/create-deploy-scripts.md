---
title: Maken en uitvoeren van scripts
titleSuffix: Configuration Manager
description: Maak en Powershell-scripts uitvoeren op clientapparaten.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 29806161b29b87834c0cb4b1e478d92bff7a7b3c
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Maken en PowerShell-scripts uitvoeren vanaf de Configuration Manager-console

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


System Center Configuration Manager heeft een geïntegreerde mogelijkheid om uit te voeren Powershell-scripts. PowerShell heeft het voordeel van het maken van geavanceerde, geautomatiseerde scripts die zijn begrepen en gedeeld met een grotere community. De scripts vereenvoudigen aangepaste hulpprogramma's voor het beheren van software en kunt die u dat snel taken, zodat u grote werk gemakkelijker en consistenter bouwen.

> [!TIP]  
> Deze functie is geïntroduceerd in versie 1706 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1802, deze functie is niet langer een voorlopige versie.


Met deze integratie in System Center Configuration Manager, kunt u de *Scripts uitvoeren* functionaliteit voor het volgende doen:

- Maken en bewerken van scripts voor gebruik met System Center Configuration Manager.
- Beheren van het gebruik van script via de rollen en beveiligingsbereiken. 
- Scripts uitvoeren op verzamelingen of afzonderlijke lokale beheerde Windows-pc's.
- Snelle geaggregeerde script resultaten van clientapparaten ophalen.
- Uitvoering van script bewaken en rapportage resultaten van de uitvoer van het script weergeven.

>[!WARNING]
>Gezien de kracht van scripts, herinneren wij u opzettelijk en voorzichtig met het gebruik. We zijn ingebouwd in extra veiligheidsmaatregelen helpen u; gescheiden rollen en bereiken. Zorg ervoor dat de nauwkeurigheid van scripts valideren voordat u ze uitvoert en die afkomstig zijn van een vertrouwde bron, om te voorkomen dat de uitvoering van het onbedoeld script bevestigen. Houd ook rekening met uitgebreide tekens of andere codeversleuteling en Lees over het beveiligen van scripts. [Meer informatie over de beveiliging van de PowerShell-script](/sccm/apps/deploy-use/learn-script-security)

## <a name="prerequisites"></a>Vereisten

- Voor het PowerShell-scripts uitvoeren, moet op de client, PowerShell versie 3.0 of hoger worden uitgevoerd. Echter, als u het uitvoeren van een script bevat de functionaliteit van een nieuwere versie van PowerShell, de client waarop u het script uitvoert moet worden uitgevoerd die versie van PowerShell.
- Configuration Manager-clients moeten de client uitgevoerd vanaf de release 1706 of later om te kunnen uitvoeren van scripts.
- Gebruik van scripts, moet u lid zijn van de juiste Configuration Manager-beveiligingsrol.
- Importeren en scripts - schrijft u uw account moet hebben **maken** machtigingen voor **SMS Scripts**.
- Goedkeuren of weigeren van scripts - uw account moet hebben **goedkeuren** machtigingen voor **SMS Scripts**.
- Uitvoeren van scripts - uw account moet hebben **-Script uitvoeren** machtigingen voor **verzamelingen**.

Voor meer informatie over beveiligingsrollen voor Configuration Manager:</br>
[Beveiligingsbereiken voor het uitvoeren van scripts](#BKMK_Scopes)</br>
[Beveiligingsrollen voor het uitvoeren van scripts](#BKMK_ScriptRoles)</br>
[De grondbeginselen van op rollen gebaseerd beheer](/sccm/core/understand/fundamentals-of-role-based-administration).

## <a name="limitations"></a>Beperkingen

Scripts uitvoeren op dit moment ondersteunt:

- Scripttalen: PowerShell
- Parametertypen: integer, tekenreeks en lijst.


>[!WARNING]
>Let erop dat wanneer u parameters, deze wordt geopend een oppervlak voor mogelijke PowerShell injectie aanval risico. Er zijn verschillende manieren om te beperken en omzeilen, zoals het gebruik van reguliere expressies parameter invoer valideren of met behulp van vooraf gedefinieerde parameters. Algemene aanbevolen procedure is niet op te nemen aan geheimen in uw PowerShell-scripts (geen wachtwoorden, enzovoort). [Meer informatie over de beveiliging van de PowerShell-script](/sccm/apps/deploy-use/learn-script-security) <!--There are external tools available to validate your PowerShell scripts such as the [PowerShell Injection Hunter](https://www.powershellgallery.com/packages/InjectionHunter/1.0.0) tool. -->


## <a name="group-policy-considerations-for-scripts"></a>Overwegingen bij het beleid voor scripts groep
<!--While running scripts on devices, Configuration Manager sets policy to allow local scripts and remote signed scripts.--> 
Instellen van een beleid kan worden uitgevoerd via Groepsbeleid kunnen geen scripts worden uitgevoerd met Configuration Manager. Zie voor informatie over de uitvoering van het beleid en hoe u stellen de [over Uitvoeringsbeleidsregels](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies) artikel. <!--507185-->

## <a name="run-script-authors-and-approvers"></a>Voer Script auteurs en fiatteurs

Uitvoeren van Scripts gebruikt het concept van *script auteurs* en *script goedkeurders* als afzonderlijke rollen voor implementatie en uitvoering van een script. Met de auteur en de goedkeurder rollen gescheiden kunt voor een belangrijk proces controle over de krachtige hulpprogramma dat Scripts uitvoeren. Er is een extra *script uitlopers* rol waarmee de uitvoering van scripts, maar niet maken of de goedkeuring van scripts. Zie [beveiligingsrollen voor scripts maken](#BKMK_ScriptRoles).

### <a name="scripts-roles-control"></a>Scripts rollen beheren

Standaard goedkeuren gebruikers niet van een script dat ze hebben gemaakt. Omdat scripts krachtige, veelzijdige en mogelijk geïmplementeerd op veel apparaten zijn, kunt u de rollen tussen de persoon die het script maakt en de persoon die het script goedkeurt scheiden. Deze functies bieden een extra beveiligingsniveau tegen het uitvoeren van een script zonder toezicht. U kunt kunnen secundaire goedkeuring, voor een eenvoudige testen uitschakelen.

### <a name="approve-or-deny-a-script"></a>Goedkeuren of weigeren van een script

Scripts moeten worden goedgekeurd door de *script goedkeurder* rol, voordat ze kunnen worden uitgevoerd. Goedkeuren van een script:

1. Klik in de Configuration Manager-console op **Softwarebibliotheek**.
2. In de **softwarebibliotheek** werkruimte, klikt u op **Scripts**.
3. In de **Script** kiest u het script dat u wilt goedkeuren of weigeren en klik op de **Start** tabblad, in de **Script** groep, klikt u op **goedkeuren/weigeren**.
4. In de **goedkeuren of weigeren van script** dialoogvenster, **goedkeuren**, of **weigeren** voor het script. Voer eventueel een opmerking over uw beslissing.  Als u een script weigeren, kan deze kan niet worden uitgevoerd op clientapparaten. <br>
![Script - goedkeuring](./media/run-scripts/RS-approval.png)
1. Voltooi de wizard. In de **Script** wilt weergeven, ziet u de **goedkeuring staat** kolom wijzigen, afhankelijk van de actie die u hebt gemaakt.

### <a name="allow-users-to-approve-their-own-scripts"></a>Toestaan dat gebruikers hun eigen scripts goedkeuren

Deze goedkeuring wordt voornamelijk gebruikt voor de testfase van scripts te ontwikkelen.

1. Klik op **Beheer**in de Configuration Manager-console.
2. Vouw in de werkruimte **Beheer** **Siteconfiguratie**uit en klik vervolgens op **Sites**.
3. Kies in de lijst met websites, uw site en klik op de **Start** tabblad, in de **Sites** groep, klikt u op **hiërarchie-instellingen**.
4. Op de **algemene** tabblad van de **eigenschappen van hiërarchie-instellingen** dialoogvenster vak, schakel het selectievakje uit **staan geen script auteurs goed te keuren van hun eigen scripts**.

>[!IMPORTANT]
>Als een best practice niet moet u de auteur van een script om goed te keuren van hun eigen scripts toestaan. Het moet alleen toegestaan in een labomgeving. Overweeg zorgvuldig de gevolgen van het wijzigen van deze instelling in een productieomgeving.

## <a name="security-scopes"></a>Beveiligingsbereiken
*(Geïntroduceerd in versie 1710)*  
Uitvoeren van Scripts gebruikt beveiligingsbereiken, een bestaande functie van Configuration Manager, kunt u scripts schrijven en uitvoeren via het toewijzen van labels die gebruikersgroepen vertegenwoordigen. Zie voor meer informatie over het gebruik van beveiligingsbereiken [beheer op basis van rollen voor System Center Configuration Manager configureren](../../core/servers/deploy/configure/configure-role-based-administration.md).

## <a name="bkmk_ScriptRoles"></a> Beveiligingsrollen voor scripts maken
De drie beveiligingsrollen gebruikt voor het uitvoeren van scripts worden niet standaard in Configuration Manager gemaakt. Volg de stappen voor het maken van het script uitlopers, script auteurs en script goedkeurders rollen.

1. Ga in de Configuration Manager-console naar **beheer** >**beveiliging** >**beveiligingsrollen**
2. Met de rechtermuisknop op een rol en klikt u op **kopie**. De rol die u kopiëren heeft machtigingen zijn al toegewezen. Zorg ervoor dat u alleen de machtigingen die u wilt uitvoeren. 
3. Geef de aangepaste rol een **naam** en een **beschrijving**. 
4. De beveiligingsrol onderstaande machtigingen toewijzen. 

    ### <a name="security-role-permissions"></a>**Beveiligingsmachtigingen voor de rol**

     **Rolnaam**: Script uitlopers
    - **Beschrijving**: Deze machtigingen kunt deze rol alleen scripts die eerder zijn gemaakt en die zijn goedgekeurd door andere functies uitvoeren. 
    - **Machtigingen:** Zorg ervoor dat de volgende zijn ingesteld op **Ja**.
         |**Categorie**|**Machtiging**|**Status**|
         |---|---|---|
         |Verzameling|Script uitvoeren|Ja|
         |SMS-Scripts|Maken|Ja|
         |SMS-Scripts|Lezen|Ja|

     **Rolnaam**: Script auteurs
    - **Beschrijving**: Deze machtigingen kunt deze rol Auteur scripts, maar ze niet goedkeuren of ze uit te voeren. 
    - **Machtigingen**: Zorg ervoor dat de volgende machtigingen zijn ingesteld.
    - 
         |**Categorie**|**Machtiging**|**Status**|
         |---|---|---|
         |Verzameling|Script uitvoeren|Nee|
         |SMS-Scripts|Maken|Ja|
         |SMS-Scripts|Lezen|Ja|
         |SMS-Scripts|Verwijderen|Ja|
         |SMS-Scripts|Wijzigen|Ja|

    **Rolnaam**: Script auteurs
    - **Beschrijving**: Deze machtigingen kunnen deze functie om goed te keuren scripts, maar ze niet maken of ze uit te voeren. 
    - **Machtigingen:** Zorg ervoor dat de volgende machtigingen zijn ingesteld.

         |**Categorie**|**Machtiging**|**Status**|
         |---|---|---|
         |Verzameling|Script uitvoeren|Nee|
         |SMS-Scripts|Lezen|Ja|
         |SMS-Scripts|Goedkeuren|Ja|
         |SMS-Scripts|Wijzigen|Ja|
     
**Voorbeeld van de SMS-Scripts machtigingen voor de rol van de auteurs script**

 ![Voorbeeld van de SMS-Scripts machtigingen voor de rol van de auteurs script](./media/run-scripts/script_authors_permissions.png)

   

## <a name="create-a-script"></a>Een script maken

1. Klik in de Configuration Manager-console op **Softwarebibliotheek**.
2. In de **softwarebibliotheek** werkruimte, klikt u op **Scripts**.
3. Op de **Start** tabblad, in de **maken** groep, klikt u op **Script maken**.
4. Op de **Script** pagina van de maken **Script** wizard de volgende instellingen configureren:
    - **De naam van een script** -Voer een naam voor het script. Hoewel u meerdere scripts met dezelfde naam maken kunt, maakt met dubbele namen het moeilijker te vinden van het script u moet in de Configuration Manager-console.
    - **Scripttaal** -momenteel alleen PowerShell-scripts worden ondersteund.
    - **Importeren** -importeren van een PowerShell-script in de console. Het script wordt weergegeven in de **Script** veld.
    - **Schakel** -het huidige script verwijdert uit het Script-veld.
    - **Script** -wordt het momenteel geïmporteerde script. U kunt het script in dit veld indien nodig bewerken.
5. Voltooi de wizard. Het nieuwe script wordt weergegeven in de **Script** lijst met de status van **wachten op goedkeuring**. Voordat u dit script op clientapparaten uitvoert kunt, moet u deze goedkeuren. 

> [!IMPORTANT]
    >Vermijd het uitvoeren van een apparaat opnieuw te starten of opnieuw opstarten van de Configuration Manager-agent scripts wanneer de functie Scripts uitvoeren. In dat geval kan leiden tot een continue rebooting staat. Indien nodig, zijn er verbeteringen in de functie client melding waarmee opnieuw te starten-apparaten in Configuration Manager versie 1710 wordt gestart. De [in afwachting van opnieuw opstarten kolom](/sccm/core/clients/manage/manage-clients#Restart-clients) kan helpen apparaten identificeren die een herstart nodig. 
<!--SMS503978  -->

## <a name="script-parameters"></a>Scriptparameters
*(Geïntroduceerd in versie 1710)*  
Parameters toe te voegen aan een script biedt meer flexibiliteit voor uw werk. Hieronder worden de huidige capaciteit van de functie Scripts uitvoeren met scriptparameters *Tekenreeks*, *Integer* gegevenstypen. Een lijst met vooraf gedefinieerde waarden zijn ook beschikbaar. Als uw script niet-gegevenstypen ondersteunde bevat, krijgt u een waarschuwing.

In de **Script maken** dialoogvenster, klikt u op **scriptparameters** onder **Script**.

Elk van uw script parameters heeft een eigen dialoogvenster voor het toevoegen van meer details en validatie.

>[!IMPORTANT]
> Parameterwaarden mag niet een enkel aanhalingsteken. 


### <a name="parameter-validation"></a>De validatie van parameter

Elke parameter in het script heeft een **Script parametereigenschappen** dialoogvenster u validatie voor deze parameter. Na het toevoegen van validatie moet er treden fouten als u een waarde opgeeft voor een parameter die niet aan de validatie voldoet.

#### <a name="example-firstname"></a>Voorbeeld: *FirstName*

In dit voorbeeld u zich kunt instellen van de eigenschappen van de tekenreeksparameter *FirstName*.

![Scriptparameters - tekenreeks](./media/run-scripts/RS-parameters-string.png)


De sectie validatie van de **Script parametereigenschappen** dialoogvenster bevat de volgende velden voor het gebruik:

- **Minimale lengte** - minimum aantal tekens van de *FirstName* veld.
- **Maximale lengte**- maximaal aantal tekens van de *FirstName* veld
- **RegEx** - afkorting voor *reguliere expressie*. Zie voor meer informatie over het gebruik van de reguliere expressie in de volgende sectie *validatie met behulp van reguliere expressie*.
- **Aangepaste foutpagina** - handig voor het toevoegen van uw eigen aangepaste foutbericht dat eventuele foutberichten voor validatie van systeem vervangt.

#### <a name="using-regular-expression-validation"></a>Met behulp van de validatie van de reguliere expressie

Een reguliere expressie is een compacte vorm van programmeren voor het controleren van een reeks tekens op basis van een gecodeerde validatie. Bijvoorbeeld, u kan controleren of het ontbreken van een investering alfabetisch teken in de *FirstName* veld door het plaatsen van `[^A-Z]` in de *RegEx* veld.

De reguliere expressie verwerken voor dit dialoogvenster wordt ondersteund door .NET Framework. Zie voor instructies over het gebruik van reguliere expressies, [reguliere expressie van .NET](https://docs.microsoft.com/dotnet/standard/base-types/regular-expressions). 


## <a name="script-examples"></a>Voorbeelden van scripts

Hier volgen enkele voorbeelden van scripts die u mogelijk wilt gebruiken met deze mogelijkheid.

### <a name="create-a-new-folder-and-file"></a>Maak een nieuwe map en het bestand

Dit script maakt een nieuwe map en een bestand in de map, krijgt uw naming invoer.

``` powershell
Param(
[Parameter(Mandatory=$True)]
[string]$FolderName,
[Parameter(Mandatory=$True)]
[string]$FileName,
)

New-Item $FolderName -type directory
New-Item $FileName -type file
```

### <a name="get-os-version"></a>Ophalen van de versie van besturingssysteem

Dit script maakt gebruik van WMI query uitvoeren op de machine voor de versie van het besturingssysteem.

``` powershell
Write-Output (Get-WmiObject -Class Win32_operatingSystem).Caption
```

## <a name="run-a-script"></a>Een script uitvoeren

Nadat een script is goedgekeurd, kan deze kan worden uitgevoerd op basis van een enkel apparaat of een verzameling. Zodra de uitvoering van het script wordt gestart, wordt het snel gestart via een systeem met hoge prioriteit die treedt er een time-out in één uur. De resultaten van het script vervolgens met behulp van een statusberichtsysteem geretourneerd.

Selecteer een verzameling van doelen voor uw script:

1. Klik op **Activa en naleving**op de Configuration Manager-console.
2. In de activa en naleving werkruimte, klikt u op **Apparaatverzamelingen**.
3. In de **Apparaatverzamelingen** lijst, klikt u op de verzameling van apparaten waarop u wilt dat het script uit te voeren.
4. Selecteer een verzameling van uw keuze, klikt u op **-Script uitvoeren**.
5. Op de **Script** pagina van de **-Script uitvoeren** wizard kiest u een script in de lijst. Alleen goedgekeurde scripts die worden weergegeven.
6. Klik op **volgende**, en voltooi de wizard.

>[!IMPORTANT]
>Als u een script niet wordt uitgevoerd, bijvoorbeeld omdat een doelapparaat is uitgeschakeld tijdens het één uur periode, moet u deze opnieuw uitvoeren.

### <a name="target-machine-execution"></a>Doel machine worden uitgevoerd

Het script wordt uitgevoerd als de *system* of *computer* account op de betreffende client (s). Dit account heeft beperkte toegang tot het netwerk. Geen toegang hebben tot externe systemen en locaties door het script moet dienovereenkomstig worden ingericht.

## <a name="script-monitoring"></a>Script bewaking

Nadat u hebt gestart om een script uitgevoerd op een verzameling apparaten, moet u de volgende procedure gebruiken voor het bewaken van de bewerking. Vanaf versie 1710, bent u beide kunnen een script in realtime controleren, zoals deze wordt uitgevoerd en u kunt ook teruggaan naar een rapport voor een bepaalde uitvoering van Script uitvoeren. <br>

![Controleprogramma voor script - Script uitvoeringsstatus](./media/run-scripts/RS-monitoring-three-bar.png)

1. Klik in de Configuration Manager-console op **bewaking**.
2. In de **bewaking** werkruimte, klikt u op **Script Status**.
3. In de **Script Status** wanneer u de resultaten voor elk script dat u hebt uitgevoerd op clientapparaten lijst bekijken. De afsluitcode van een script van **0** geeft meestal aan dat het script is uitgevoerd.
    - Vanaf Configuration Manager 1802 kan is uitvoer van het script afgekapt tot 4 KB voor betere ervaring voor weergave.  <!--510013-->
      ![Controleprogramma voor script - ingekorte Script](./media/run-scripts/Script-monitoring-truncated.png) 

## <a name="script-output"></a>Uitvoer van het script

- Vanaf Configuration Manager versie 1802, retourneert uitvoer van het script met behulp van JSON-opmaak. Deze indeling retourneert consistent een leesbare scriptuitvoer. 
- Scripts die u een onbekend resultaat of die waar de client offline was, niet weergegeven in de grafieken of de gegevensset. <!--507179-->
- Vermijd grote scriptuitvoer retourneren omdat deze is afgekapt tot 4 KB. <!--508488-->
- Sommige functies met een script uitvoeren opmaak is niet beschikbaar bij het uitvoeren van Configuration Manager versie 1802 of hoger met een eerdere versie van de client. <!--508487-->
- Een enum-object converteren naar een string-waarde in scripts, zodat ze goed worden weergegeven in de JSON-opmaak. <!--508377--> ![Enum-object converteren naar een tekenreekswaarde](./media/run-scripts/enum-tostring-JSON.png)



## <a name="see-also"></a>Zie ook

- [Beheer op basis van rollen voor System Center Configuration Manager configureren](../../core/servers/deploy/configure/configure-role-based-administration.md)
- [Basisprincipes voor beheer op basis van rollen](/sccm/core/understand/fundamentals-of-role-based-administration)
