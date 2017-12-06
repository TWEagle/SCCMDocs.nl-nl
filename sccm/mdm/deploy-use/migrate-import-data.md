---
title: Gegevens importeren in Microsoft Intune
titleSuffix: Configuration Manager
description: 
keywords: 
author: dougeby
manager: dougeby
ms.date: 12/05/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: b552391d-abc0-48a2-a429-93605a13a66a
ms.openlocfilehash: d42a5fd64b5baead8ef87d8c08a99ec659f94633
ms.sourcegitcommit: 8c6e9355846ff6a73c534c079e3cdae09cf13c45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/06/2017
---
# <a name="import-configuration-manager-data-to-microsoft-intune"></a>Configuration Manager-gegevens importeren in Microsoft Intune 

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*    

De aanbevolen eerste fase in het proces om [hybride MDM-gebruikers en apparaten migreren naar Intune standalone](migrate-hybridmdm-to-intunesa.md) in de cloudconfiguratie is het hulpprogramma voor gegevensimport Intune te gebruiken. Als u wilt, kunt u deze fase overslaan en verplaatsen naar de [Intune voorbereiden voor gebruikersmigratie van de](migrate-prepare-intune.md) fase. Dit hulpprogramma voert echter de volgende functies waarmee u veel tijd in de volgende fase besparen kunnen uit: 
1.  Verzamelt gegevens over de objecten die u in de Configuration Manager-hiërarchie selecteert. 
2.  Bevat informatie over de objecten die u kunt selecteren voor het importeren en informatie over waarom sommige objecten kunnen niet worden geïmporteerd.
3.  Importeert geselecteerde objecten in uw Microsoft Intune-tenant. 

Het hulpprogramma voor gegevensimport verandert niets aan uw Configuration Manager-omgeving op elke manier en daarom objecten importeren in Intune en controleren of alles werkt zoals verwacht zonder risico uw hybride MDM-apparaten in een onbeheerde staat verlaten. 

## <a name="what-objects-can-this-tool-import"></a>Welke objecten kan importeren door dit hulpprogramma?
Het hulpprogramma voor importeren kunt informatie verzamelen over de volgende objecttypen in Configuration Manager en bevat informatie over of de verzamelde objecten kunnen worden geïmporteerd: 
- Configuratie-items
- Certificaatprofielen
- E-mailprofielen
- VPN-profielen
- Wi-Fi-profielen
- Nalevingsbeleid
- Apps
- Implementaties

> [!Note]    
> Het importeren van implementaties is alleen nuttig voor andere objecttypen die u wilt importeren. Bijvoorbeeld, als u VPN-profielen en implementaties importeert, wordt het alleen mogelijk voor het importeren van de implementaties voor de VPN-profielen die u selecteert. Implementaties in Intune worden toewijzingen genoemd. Als u importeren van een implementatie voor een eerder geïmporteerd object wilt, moet u dat object opnieuw importeren of handmatig de toewijzing te maken in Intune in Azure. Bijvoorbeeld, als u VPN-profielen en niet-implementaties importeert, hebt u het hulpprogramma opnieuw uitvoeren en VPN-profielen en -implementaties selecteren of handmatig de toewijzing te maken in Intune in Azure.  Als u het hulpprogramma opnieuw uit, worden dubbele objecten mogelijk gemaakt dat u later in Intune in Azure kunt verwijderen.  

> [!Important]    
> Als de verzameling voor een implementatie is gebaseerd op een Active Directory-groep die is gerepliceerd naar Azure Active Directory (AAD), wordt het hulpprogramma automatisch gericht op gemigreerde objecten aan de groepen als u de juiste implementatie selecteert wanneer u het hulpprogramma uitvoert. Wanneer u complexere verzamelingen of directe lidmaatschapverzamelingen hebt, moet u ze handmatig opnieuw maken in AAD en handmatig doel object toewijzingen aan hen in Intune in Azure.


## <a name="things-to-know-before-you-run-the-tool"></a>Zaken die u moet weten voordat u het hulpprogramma uitvoeren
- Het programma wordt uitgevoerd, heeft dit geen invloed op uw Configuration Manager-omgeving op een manier.
- Het is raadzaam om eerst de procedure voor het importeren van gegevens met behulp van een proefversie van uw tenant te testen. Vervolgens, nadat u hebt gecontroleerd dat de gegevens die u verwacht dat is geïmporteerd, u hetzelfde proces met uw Intune-tenant voor productie doorloopt.
- De importfunctie van gegevens is bedoeld om de Configuration Manager-gegevens slechts één keer te importeren. Dit komt niet bijhouden van objecten in Configuration Manager of Intune. Echter, als u de importfunctie opnieuw op dezelfde computer uitvoeren als voordat, het laat u welke objecten weten u eerder hebt geïmporteerd. Het hulpprogramma weet niet als het object nog steeds in Intune bestaat of als een object is gewijzigd. Als u gegevens naar Intune meer dan één keer importeert, kunt u uiteindelijk met dubbele objecten.
- Niet alle profielinstellingen voor kunnen worden geïmporteerd. U kunt geen bijvoorbeeld kioskmodus of PFX-instellingen importeren. 
- Als er een Configuration Manager-beleid met instellingen die niet van toepassing op de geselecteerde platforms, het hulpprogramma mogelijk worden deze instellingen genegeerd tijdens het importeren. De Help bij de instellingen om te controleren of het beleid wordt genegeerd kan worden geïmporteerd en worden ondersteund door Intune. 
- Het hulpprogramma probeert te bieden u een reden voor waarom een object kan niet worden geïmporteerd. In sommige gevallen, voordat u objecten in Intune importeren, gaat u terug naar de Configuration Manager-console, los het probleem, start u de Configuration Manager objectdetectie opnieuw scannen en vervolgens de objecten importeren. Soms u mogelijk moet of wilt, deze objecten in Intune handmatig opnieuw maken.
- Er zijn een aantal profielen die afhankelijk van andere objecten zijn. Als u wilt een profiel dat afhankelijk is van een ander object, zoals een e-mailprofiel die afhankelijk zijn van een certificaat importeren moet u beide objecten op hetzelfde moment importeren, tenzij u hebt het andere object eerder geïmporteerd vanaf de computer met dezelfde gebruiker.  
- Nadat u het hulpprogramma uitvoert, moet u mogelijk extra stappen handmatig uitvoeren. Bijvoorbeeld, als doel apps en beleidsregels voor AAD-groepen. 

## <a name="prerequisites"></a>Vereisten
- Configuration Manager versie 1610 of hoger.-het is raadzaam dat u op het hoogste niveau opgeeft en het hulpprogramma uitvoeren aan een gebruiker die toegang tot alle objecten in de sitehiërarchie heeft. Het hulpprogramma detecteert alleen objecten die toegankelijk is door de gebruiker die het programma wordt uitgevoerd. 
- Een globale beheerder moet het gegevensimport hulpprogramma uitvoeren de eerste keer met de volgende ***intunedataimporter.exe - GlobalConsent*** parameter. Vervolgens kan een globale beheerder of een Intune-beheerder het hulpprogramma uitvoeren.  


<!-- ## Objects that cannot be imported
There are some Configuration Manager objects that the importer tool cannot import to Intune. You must manually create these objects in Intune. 
- Collections based on direct membership or that are based on a query. The only collections that are imported are based on a single AD group. For all other collections, you must create the assignment in Intune and add the assignment to the appropriate objects. 
- Profiles <list what we cannot import>
- Policies <??>
- Etc.
-->

## <a name="download-the-data-importer-tool"></a>Download het hulpprogramma voor gegevensimport
Het hulpprogramma voor gegevensimport is beschikbaar voor downloaden uit de opslagplaats ConfigMgrTools/Intune--gegevensimport in GitHub. Gebruik de volgende procedure voor het downloaden van het hulpprogramma.

1. Ga naar de [Intune gegevens importfunctie van GitHub releases](https://github.com/ConfigMgrTools/Intune-Data-Importer/releases) pagina.
2. Klik op voor de meest recente versie **Microsoft.Intune.Data.Importer.exe**.
3. Opslaan en uitvoeren (of alleen) de .exe en kies vervolgens een doelmap voor het uitpakken van het hulpprogramma voor gegevensimport Intune.

## <a name="run-the-data-importer-tool"></a>Voer het hulpprogramma voor gegevensimport
De wizard voor het hulpprogramma voor gegevensimport kan worden onderverdeeld in drie stappen. Deze sectie bevat informatie over het voltooien van elke sectie van de wizard en Configuration Manager-gegevens importeren in Intune. Elke stap wordt voorgezet waar de vorige stap is beëindigd.

### <a name="provide-permission-for-the-data-importer-tool-to-access-resources"></a>Machtiging voor het hulpprogramma voor gegevensimport toegang tot bronnen te bieden
Voordat u het hulpprogramma voor gegevensimport uitvoeren kunt, moet u een globale beheerdersaccount gebruiken de gegevensimport hulpprogramma om toestemming te geven in Azure voor toegang tot bronnen. Vervolgens kunt u het hulpprogramma uitvoeren met een account hoofdbeheerder of Intune-beheerder.   

1.  Een globale beheerder moet het hulpprogramma voor de eerste keer met de volgende parameter uitvoeren: ***intunedataimporter.exe - GlobalConsent*** 
2. Wanneer het hulpprogramma wordt gestart, wordt een aanmeldingsscherm weergegeven waar u zich moet aanmelden met een account met de rol globale beheerder in Azure. 
3. Klik op **accepteren** maken van een toepassing in Azure met de juiste rechten hebben in Microsoft Graph. Het hulpprogramma voor gegevensimport moet deze rechten aan objecten importeren in Microsoft Intune.   

   > [!Important]
   > Wanneer u klikt op **accepteren**, geeft u de machtiging hulpprogramma voor het volgende doen:
   > - Alle groepen lezen
   > - Aanmelden en gebruikersprofiel lezen
   > - Intune apparaatconfiguratie en -beleid lezen en schrijven
   > - Lezen en schrijven van Intune-apps
   > - Lezen en schrijven van beleid voor Intune op rollen gebaseerd beheer
   > - Lezen en schrijven van apparaten met Intune
   > - Lezen en schrijven van Intune-configuratie
1. Accepteer nadat u hebt toestemming te geven, een algemene beheerder of Intune-beheerder kan het hulpprogramma voor importeren van gegevens uit Configuration Manager in Intune in Azure uitvoeren.    
        
    > [!Note]
    > Als u toestemming heeft eerst niet geaccepteerd door een globale beheerder, het hulpprogramma mogelijk weergegeven **u geen toegang tot deze toepassing** nadat een Intune-beheerder het hulpprogramma voor gegevensimport wordt uitgevoerd en zich bij de Intune-abonnement aanmelden.

### <a name="manually-map-collections-to-azure-ad-groups"></a>Verzamelingen handmatig worden toegewezen aan Azure AD-groepen
Wanneer u het hulpprogramma voor gegevensimport uitvoert, pakt deze de naam van de AD-groep van verzamelingen met een enkele regel die gericht is op één AD-groep. Wanneer de toewijzingen worden gemaakt in Intune, de gegevensimport zoekt naar een Azure AD-groep met dezelfde naam als de AD-groep en als dit bestaat, wordt het geïmporteerde object toegewezen aan die Azure AD-groep. U kunt overschrijf de naam van de AD-groep die de gegevensimport voor een verzameling vindt en geef een of meer Azure AD-groepen moet worden gebruikt voor die verzameling. Met behulp van het toewijzingsbestand verzameling biedt een manier om u verzamelingen die meestal niet importeerbare met de importfunctie van gegevens naar Azure AD-groepen zijn toewijzen.
#### <a name="find-the-collections-that-cannot-be-imported"></a>Zoek de verzamelingen die niet kunnen worden geïmporteerd
U kunt een lijst van alle verzamelingen die niet importeerbare zodat u ze aan uw verzameling toewijzing CSV-bestand toevoegen kunt. 
1. Voer het hulpprogramma voor gegevensimport en selecteer de objecten voor importeren. Gebruik de procedures in [fase 1: Configuration Manager-objecten te detecteren en verzamelen gegevens](#phase-1:-discover-configuration-manager-objects-and-collect-data) en [fase 2: Los problemen op en selecteer de objecten voor importeren](#phase-2:-resolve-issues-and-select-the-objects-to-import) om te detecteren en kies de objecten. Klik op de **samenvatting** pagina **exporteren Details** te maken van een CSV-bestand met details van alles geselecteerd voor importeren, met inbegrip van de objecten die niet kunnen worden geïmporteerd en implementaties. 
2. Het CSV-bestand openen in Microsoft Excel en filter de gegevens op basis van de **implementatie** voor de **Type** kolom en **Nee** voor de **Importable** kolom. De naamkolom van de verzameling bevat alle verzamelingen die worden toegevoegd aan een verzameling toewijzingsbestand in volgorde voor deze implementaties moeten worden importeerbare.

#### <a name="create-the-collection-mapping-file"></a>Het toewijzingsbestand verzameling maken
Het toewijzingsbestand voor de verzameling is een door komma's gescheiden waarden (CSV)-bestand waarbij de eerste kolom de naam van de Configuration Manager-verzameling en de tweede kolom de naam van de Azure AD te gebruiken voor deze verzameling. Als u meer dan één Azure AD-groep voor één Configuration Manager-verzameling, meerdere rijen in het CSV-bestand met die verzamelingsnaam te maken. Het volgende voorbeeld wordt een CSV-bestand met twee verzamelingen. De eerste verzameling is toegewezen aan een enkele Azure AD-groep en de tweede collectie is toegewezen aan twee Azure AD-groepen.

![Voorbeeld van een verzameling toewijzing CSV-bestand](..\media\migrate-collectionmapping.png)

#### <a name="start-the-data-importer-tool-using-collection-mapping"></a>Het hulpprogramma voor gegevensimport met behulp van toewijzing van de verzameling starten
U moet voor het gebruik van een verzameling toewijzingsbestand starten de gegevensimport hulpprogramma via de *- CollectionMappingFile* opdrachtregelparameter en het volledige pad naar de verzameling toewijzing CSV-bestand wordt gebruikt, u maakt. Bijvoorbeeld:

```IntuneDataImporter.exe -CollectionMappingFile c:\Users\myuser\Documents\collectionmapping.csv```

> [!Note]
> Importfunctie van de gegevens weergegeven niet iets op een wizardpagina om aan te geven dat het toewijzingsbestand voor de verzameling is geladen. Het hulpprogramma wordt echter eventuele fouten opgetreden tijdens het lezen van het CSV-bestand weergegeven. Ook op de **samenvatting** pagina van de wizard kunt u bekijken **implementatie** typen. Het hulpprogramma **Ja** in de importeerbare kolom en een lijst met de Azure AD-groepen die wordt toegewezen aan objecten in de **notities** kolom.

### <a name="phase-1-discover-configuration-manager-objects-and-collect-data"></a>Fase 1: Configuration Manager-objecten te detecteren en verzamelen van gegevens
In stap 1 selecteert u de objecten worden gedetecteerd en dat het hulpprogramma verzamelen van informatie over de geselecteerde objecten. 
1. Open het hulpprogramma en klik op **Start**.  
2. Lees de informatie en klik vervolgens op **volgende**. 
3. Kies of u wilt importeren van een eerder uitgevoerde gegevensset of Selecteer de objecttypen die u wilt importeren:
   - **Eerder hebt geëxporteerd gegevensset importeren**: Kies **gegevensset importeren die zijn geëxporteerd uit een eerder uitgevoerde van gegevensimport Intune**, en klik op **Bladeren** voor **geëxporteerde gegevensmap** om een gegevens te selecteren die u eerder te instellen geëxporteerd met het hulpprogramma van de importfunctie van gegevens. De gebruiker die de gegevensset de invoer moet dezelfde gebruiker die de gegevens hebt geëxporteerd. Nadat u de gegevens hebt geïmporteerd, een overzicht van de objecten worden weergegeven op de **samenvatting** pagina van de wizard. Als de samenvatting er goed uitziet, gaat u naar de [fase 3: Geselecteerde object importeren naar Intune](phase-3:-import-selected-object-to-intune).
 
      > [!Note]
      > Nadat u detecteren en selecteer de objecten in uw site om te importeren, kunt u de objecten voor een set gegevens exporteren op de **aanmelden bij Intune** pagina van de wizard. U kunt de gegevensset op deze pagina vervolgens importeren. De gegevensset is versleuteld met behulp van de Windows-gebruikersreferenties van de aangemelde gebruiker, zodat alleen de gebruiker die de gegevensset geëxporteerd kunt de gegevensset in het hulpprogramma voor importeren. 
   - **Selecteer het objecttype importeren**: Kies **objecttype importeren selecteert** objecttypen om te importeren en objecten in uw omgeving detecteren selecteren. Geef de volgende informatie over uw site en de objecten die u wilt importeren.
      - **Naam van de siteserver**: Geef de volledig gekwalificeerde domeinnaam van de siteserver om objecten te importeren. Het hulpprogramma detecteert alleen objecten die toegankelijk is door de gebruiker die het programma wordt uitgevoerd. U wordt doorgaans, geef de bovenste site en het hulpprogramma uitvoeren aan een gebruiker die toegang tot alle objecten in de sitehiërarchie heeft.
      - **Sitecode**: Geef de sitecode voor de siteserver. U vindt de drieletterige code aan de bovenkant van de Configuration Manager-console.
      - **Objecttypen importeren**: Kies de objecten die u wilt dat het hulpprogramma voor het verzamelen van. U kunt kiezen **Alles selecteren** voor alle objecten kiezen of Selecteer afzonderlijke objecttypen. 
4.  Klik op **volgende** starten met het detecteren van de objecten op de site. Het hulpprogramma geeft de voortgang weer voor elk van de objecttypen. 
    - Als het hulpprogramma detecteert geen gegevens voor een geselecteerd object-type, de voortgang van de balk onmiddellijk weergegeven voor het objecttype is voltooid.
    - Objecten die u niet hebt geselecteerd, worden niet weergegeven op de **verzamelen** data-pagina. 
    - U kunt het hulpprogramma opnieuw voor objecten die zijn niet verzameld, of dat u geannuleerd tijdens de verzameling uitvoeren.

### <a name="phase-2-resolve-issues-and-select-the-objects-to-import"></a>Fase 2: Los problemen op en selecteer de objecten voor importeren  
Controleren van de objecten die worden gevonden door het hulpprogramma problemen oplossen die voorkomen dat het object wordt geïmporteerd in Intune in fase 2, en selecteer de objecten te importeren. Als u problemen hebt opgelost, terug naar de **Discover-omgeving** pagina van de wizard opnieuw de objecten worden gedetecteerd. 
5.  Klik op **volgende** om te controleren van de objecten die worden verzameld. Pagina voor het selecteren van een item is beschikbaar voor elk objecttype die worden verzameld. 
 <!--   > [!Tip]     
    > On each item selection page, you can create a filter to help you find the objects that you want to import. However, take note of the following:
    > - When you are on an item selection page and the view is filtered, the Select all checkboxes only apply to the displayed items. Any hidden objects because of a filter are not included when using the checkboxes.
    > - Objects are always grouped under their parent item even when you sort or filter the objects.
-->
6.  De objecten op de importeerbare kolom te sorteren op elke pagina item selecteren en de objecten die niet importeerbare bekijken. De informatie in de kolom notities biedt informatie over waarom het hulpprogramma voor het object kan niet worden geïmporteerd. 
7.  U moet beslissen of u wilt los de problemen voor niet-importeerbare objecten. Als u een of meer problemen hebt opgelost, klikt u op Vorige totdat u de gegevens selecteren uit de pagina met Configuration Manager en verzamelen van de gegevens opnieuw te controleren of u het probleem opgelost. U kunt fouten te herstellen totdat u tevreden bent met de objecten die importeerbare zijn blijven. 
8.  Selecteer de objecten die u wilt importeren op elke pagina item selecteren. De volgende kolommen worden weergegeven:
    - **Naam**: Naam van de Configuration Manager-object. 
    - **Importeerbare**: Hiermee geeft u op of een object kan worden geïmporteerd. U kunt alleen objecten met Ja kiezen in de kolom importeerbare. 
    - **Platform**: Hiermee geeft u het platform dat wordt ondersteund door het object.
    - **Al geïmporteerd**: Hiermee geeft u op of het object is al geïmporteerd met het hulpprogramma op deze computer. 
    - **Is vervangen** (voor apps): Hiermee geeft u op of de app is vervangen door een andere app. U moet controleren de **weergeven vervangen apps** selectievakje aan de bovenkant van de pagina voor vervangen apps om weer te geven.
    - **Opmerkingen bij de**: Bevat informatie over waarom een object kan niet worden geïmporteerd. De **notities** kolom bevat ook informatie over de instellingen die zijn genegeerd (voor bepaalde objecttypen), maar het object is nog steeds importeerbare zonder deze instellingen.
    - **Configuratiebasislijnen** (voor configuratie-items): Hiermee geeft u de configuratiebasislijnen die gekoppeld aan een configuratie-item zijn.
    - **Vereist certificaat** (voor profielen en -beleid): Hiermee geeft u op of een certificaat gekoppeld aan het object is. Wanneer een certificaat gekoppeld aan het object wordt, moet u het certificaat te importeren.
9.  Nadat u de objecten voor importeren kiest, worden deze weergegeven op de pagina overzicht. U hebt de volgende acties beschikbaar: 
    - **Gegevens exporteren**: Maakt een CSV-bestand met de informatie die wordt weergegeven op het scherm. Ook ziet u objecten die geen importeerbare en de reden waarom kan niet worden geïmporteerd. U kunt dit bestand houden voor uw archief. 
    - **Fout bij exporteren**: Exporteert een gecomprimeerd bestand dat informatie over de gegevens bevat of het hulpprogramma is niet kunnen worden geconverteerd of importeren. 

### <a name="phase-3-import-selected-objects-to-intune"></a>Fase 3: Geselecteerde objecten importeren in Intune
In de fase 3, u aanmelden bij Intune en de geselecteerde objecten importeren. 
10. Klik op **volgende**, en klik vervolgens op **aanmelden bij Intune** zich aanmeldt bij de Intune-tenant voor de gegevens importeren of Exporteer de gegevens.

    - **Exporteren**: Nadat u detecteren en selecteer de objecten in uw site om te importeren, kunt u de objecten exporteren naar een gegevensset. Hiermee kunt u objecten vanaf een computer die geen toegang tot Internet, de gegevens exporteren en vervolgens de gegevens importeren vanaf een computer met internettoegang te detecteren. De gegevensset is versleuteld met behulp van de Windows-gebruikersreferenties van de aangemelde gebruiker, zodat alleen de gebruiker die de gegevensset geëxporteerd kunt de gegevensset in het hulpprogramma voor importeren. Wanneer u deze optie kiest, kiest u het pad naar de geëxporteerde gegevens. 
      1. Klik op **exporteren** op de **aanmelden bij Intune** pagina. 
      2. Klik op **Bladeren** selecteren van de doelmap voor de export. De map moet leeg zijn. 
      3. Klik op **Start** voor het exporteren van de gegevens en wanneer het exporteren is voltooid, klikt u op **sluiten** Voltooi de wizard en de gegevensimport sluiten.
      4. De importfunctie van gegevens vanaf een andere computer met toegang tot Internet met behulp van de dezelfde referenties en selecteer starten **importeren eerder hebt geëxporteerd gegevensset** op de tweede pagina van de wizard. Nadat de gegevens worden geïmporteerd, de wizard gaat u naar de **aanmelden bij Intune** pagina. 
    - **Aanmelden bij Intune**: U moet zich aanmelden met een globale beheerder of de Intune-beheerder. Nadat u zich aanmeldt, wordt het importproces gestart.
    
      > [!Important]
      > Het is raadzaam om eerst de procedure voor het importeren van gegevens met behulp van een proefversie van uw tenant te testen. Vervolgens, nadat u hebt gecontroleerd dat de gegevens die u verwacht dat is geïmporteerd, u hetzelfde proces met uw Intune-tenant voor productie doorloopt.
12. De pagina Voortgang biedt de voortgang, zoals de objecten worden geïmporteerd. Klik op **volgende** wanneer het importeren is voltooid. 
13. Op de pagina voltooiing worden de geïmporteerde objecten weergegeven. Controleer de status voor alle objecten die is een fout tijdens het importeren opgetreden. U hebt de volgende acties beschikbaar: 
    - **Gegevens exporteren**: Maakt een CSV-bestand met de informatie die wordt weergegeven op het scherm. U kunt dit bestand houden voor uw archief. 
    - **Fout bij exporteren**: Exporteert een gecomprimeerd bestand dat informatie over de gegevens bevat of het hulpprogramma is niet kunnen worden geconverteerd of importeren.

## <a name="next-steps"></a>Volgende stappen
Nadat u de gegevens in Intune importeren, moet u de stappen te nemen [Intune voorbereiden voor gebruikersmigratie van de](migrate-prepare-intune.md). 