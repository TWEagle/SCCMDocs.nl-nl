---
title: Planningsoverwegingen voor het automatiseren van taken | Microsoft-documenten
description: Plan voordat u taken in System Center Configuration Manager automatiseren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc497a8a-3c54-4529-8403-6f6171a21c64
caps.latest.revision: 13
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 830f715b688cc9929a179da94eba9c81de8db11a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-considerations-for-automating-tasks-in-system-center-configuration-manager"></a>Planningsoverwegingen voor het automatiseren van taken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt maken van takenreeksen om taken in uw System Center Configuration Manager-omgeving te automatiseren. Deze taken gaan van het vastleggen van een besturingssysteem op een referentiecomputer tot het implementeren van het besturingssysteem op één of meer doelcomputers. De bewerkingen van de takenreeks worden gedefinieerd in de individuele stappen van de reeks. Wanneer de takenreeks wordt uitgevoerd, worden de bewerkingen van elke stap uitgevoerd op het niveau van de opdrachtregel in de Local System-context zonder dat er een interventie van de gebruiker is vereist. Gebruik de volgende secties om te plannen taken in Configuration Manager kunt automatiseren.

##  <a name="BKMK_TSStepsActions"></a>Takenreeksstappen en acties  
 Stappen zijn de basisonderdelen van een takenreeks. Ze kunnen opdrachten bevatten die configureren en vastleggen van het besturingssysteem van een referentiecomputer of ze kunnen opdrachten bevatten die het besturingssysteem, stuurprogramma's, de Configuration Manager-client en de software op de doelcomputer installeren. De opdrachten van een takenreeksstap worden gedefinieerd door de bewerkingen van de stap. Er zijn twee soorten bewerkingen: Een bewerking die u definieert door een opdrachtregeltekenreeks te gebruiken, wordt een aangepaste bewerking genoemd. Een actie die is vooraf gedefinieerd door Configuration Manager is een ingebouwde bewerking genoemd. Een takenreeks kan eender welke combinatie van aangepaste en ingebouwde bewerkingen uitvoeren.  

 Takenreeksstappen kunnen ook voorwaarden bevatten die hoe de stap zich gedraagt controleren, zoals het stoppen van de takenreeks of de takenreeks verder, als er een fout optreedt. Er worden voorwaarden toegevoegd aan de stap door een takenreeksvariabele aan de stap toe te voegen. U kunt bijvoorbeeld de variabele **SMSTSLastActionRetCode** gebruiken om de voorwaarde van de voorgaande stap te testen. Variabelen kunnen worden toegevoegd aan één stap of groep stappen.  

 Takenreeksstappen worden opeenvolgend verwerkt; dit omvat de bewerking van de stap en eventuele voorwaarden die worden toegewezen aan de stap. Wanneer Configuration Manager wordt gestart voor het verwerken van een takenreeksstap, is niet de volgende stap gestart totdat de vorige bewerking is voltooid. Een takenreeks is voltooid beschouwd wanneer alle stappen ervan zijn voltooid of wanneer een mislukte stap zorgt ervoor dat de Configuration Manager om te stoppen met de takenreeks voordat alle stappen ervan zijn voltooid. Bijvoorbeeld, wanneer de stap van een takenreeks kan niet waarnaar wordt verwezen installatiekopie of pakket met een op een distributiepunt vinden, bevat de takenreeks een gebroken referentie en Configuration Manager gestaakt de takenreeks op dat moment tenzij de mislukte stap een voorwaarde om door te gaan wanneer er een fout optreedt.  

> [!IMPORTANT]  
>  Standaard mislukt een takenreeks nadat er één stap of bewerking mislukt. Als u wilt dat de takenreeks verdergaat, zelfs wanneer een stap mislukt, bewerkt u de takenreeks, klikt u op het tabblad **Opties** en selecteert u vervolgens **Doorgaan bij fout**voor meer informatie over de stappen die aan een takenreeks kunnen worden toegevoegd.  

 Zie voor meer informatie over de stappen beschreven die kunnen worden toegevoegd aan een takenreeks [Takenreeksstappen](../understand/task-sequence-steps.md).  

##  <a name="BKMK_TSGroups"></a> Takenreeksgroepen  
 **Groepen** zijn meerdere stappen binnen een takenreeks. Een takenreeksgroep bestaat uit een naam, een optionele beschrijving en eventuele optionele voorwaarden die worden beoordeeld als een eenheid voordat de takenreeks doorgaat met de volgende stap. Groepen kunnen binnen elkaar worden genest en een groep kan een mengeling van stappen en subgroepen bevatten. Groepen kunnen nuttig zijn voor het combineren van meerdere stappen die een gemeenschappelijke voorwaarde delen.  

> [!IMPORTANT]  
>  Standaard kan een takenreeksgroep niet worden uitgevoerd wanneer er een stap of ingesloten groep binnen de groep niet kan worden uitgevoerd. Als u wilt dat de takenreeks verdergaat nadat een stap of ingesloten groep niet kan worden uitgevoerd, dient u de takenreeks te bewerken: klik op het tabblad **Opties** en selecteert u vervolgens **Doorgaan bij fout**voor meer informatie over de stappen die aan een takenreeks kunnen worden toegevoegd.  

 De volgende tabel ziet u hoe de **Doorgaan bij fout** optie werkt wanneer u stappen groepeert.  

 In dit voorbeeld zijn er twee groepen takenreeksen die drie takenreeksstappen elke bevatten.  

|Takenreeksgroep of -stap|Instelling van Doorgaan bij fout|  
|---------------------------------|-------------------------------|  
|**Takenreeksgroep 1**|**Doorgaan bij fout** geselecteerd.|  
|Takenreeksstap 1|**Doorgaan bij fout** geselecteerd.|  
|Takenreeksstap 2|Niet ingesteld.|  
|Takenreeksstap 3|Niet ingesteld.|  
|**Takenreeksgroep 2**|Niet ingesteld.|  
|Takenreeksstap 4|Niet ingesteld.|  
|Takenreeksstap 5|Niet ingesteld.|  
|Takenreeksstap 6|Niet ingesteld.|  

-   Als takenreeksstap 1 mislukt, wordt de takenreeks verder met takenreeksstap 2.  

-   Als takenreeksstap 2 mislukt, de takenreeks wordt takenreeksstap 3 niet uitgevoerd, maar blijft deze actief takenreeksstappen 4 en 5 die zich in een andere takenreeksgroep bevinden.  

-   Als takenreeksstap 4 mislukt, worden er geen stappen meer uitgevoerd en de takenreeks mislukt omdat de **Doorgaan bij fout** instelling niet is geconfigureerd voor takenreeksgroep 2.  

 U moet een naam toewijzen aan takenreeksgroepen; de groepsnaam hoeft echter niet uniek te zijn. U kunt ook een optionele beschrijving geven van de takenreeksgroep.  

##  <a name="BKMK_TSVariables"></a> Takenreeksvariabelen  
 Takenreeksvariabelen zijn een set van naam- en waardeparen die configuratie en het besturingssysteem implementatie-instellingen voor computers, besturingssystemen en gebruikersstatussen configuratietaken op een Configuration Manager-clientcomputer opgeeft. Takenreeksvariabelen bieden een mechanisme om de stappen in een takenreeks te configureren en aan te passen.  

 Als u een takenreeks uitvoert, worden er veel takenreeksinstellingen opgeslagen als omgevingsvariabelen. U kunt openen of wijzigen van de waarden van ingebouwde takenreeksvariabelen en u kunt nieuwe takenreeksvariabelen maken voor het aanpassen van de manier waarop die een takenreeks wordt uitgevoerd op een doelcomputer.  

 U kunt takenreeksvariabelen gebruiken in de takenreeksomgeving naar de volgende acties uitvoeren:  

-   Instellingen configureren voor een takenreeksbewerking  

-   Opdrachtregelargumenten leveren voor een takenreeksstap  

-   Beoordeel een voorwaarde die bepaalt of een takenreeksstap of -groep wordt uitgevoerd  

-   Geef waarden op voor aangepaste scripts die worden gebruikt in een takenreeks  

 Bijvoorbeeld, moet u wellicht een takenreeks met een **lid worden van domein of werkgroep** takenreeksstap. De takenreeks kan mogelijk naar verschillende verzamelingen worden geïmplementeerd, waarbij het lidmaatschap van de verzameling wordt bepaald door het domeinlidmaatschap. In dat geval kunt u een per-verzameling-takenreeksvariabele voor elke verzameling domeinnaam opgeven en vervolgens die takenreeksvariabele gebruiken om te leveren van de geschikte domeinnaam in de takenreeks.  

###  <a name="BKMK_TSCreateVariables"></a> Takenreeksvariabelen maken  
 U kunt nieuwe takenreeksvariabelen aanpassen en controleren van de stappen in een takenreeks toevoegen. U kunt bijvoorbeeld een takenreeksvariabele maken om een instelling voor een ingebouwde takenreeksstap te overschrijven. U kunt ook een takenreeksvariabele maken om te gebruiken met voorwaarden, opdrachtregels of aangepaste stappen in de takenreeks. Als u een takenreeksvariabele maakt, wordt de takenreeksvariabele en de gekoppelde waarde bewaard binnen de takenreeksomgeving, zelfs wanneer de reeks de doelcomputer opnieuw opstart. De variabele en de waarde ervan kunnen worden gebruikt binnen de takenreeks over verschillende besturingssysteemomgevingen. Het kan bijvoorbeeld worden gebruikt in een volledig Windows-besturingssysteem en in de Windows PE-omgeving.  

 De volgende tabel beschrijft de methoden voor het maken van een takenreeksvariabele en bijkomende gebruiksinformatie.  

|Methode maken|Gebruik|  
|-------------------|-----------|  
|Velden in takenreeksstappen instellen met de takenreekseditor|Hiermee geeft u de standaardwaarden voor de takenreeksstap op. De variabele en de waarde zijn alleen toegankelijk wanneer de stap in de takenreeks wordt uitgevoerd. Ze maken geen deel uit van de algemene reeksomgeving en ze zijn niet toegankelijk door andere takenreeksstappen in de takenreeks.<br /><br /> Zie voor een lijst van de ingebouwde variabelen en hun gekoppelde bewerkingen [actie Takenreeksvariabelen](../understand/task-sequence-action-variables.md).|  
|Toevoegen van een ingestelde takenreeksvariabelestap in een takenreeks|Specificeert de takenreeksvariabele en -waarde in de takenreeksomgeving wanneer de takenreeksstap als onderdeel van een takenreeks wordt uitgevoerd. Alle volgende takenreeksstappen hebben toegang tot de omgevingsvariabele en de waarde ervan.|  
|Een per-verzameling-variabele definiëren|Specificeert takenreeksvariabelen en -waarden voor een verzameling computers. Alle takenreeksen die zijn gericht op de verzameling, hebben toegang tot de takenreeksvariabelen en de waarden ervan.|  
|Een per-computer-variabele definiëren|Specificeert takenreeksvariabelen en -waarden voor een bepaalde computer. Alle takenreeksen die zijn gericht op de verzameling, hebben toegang tot de takenreeksvariabelen en de waarden ervan.|  
|Een takenreeksvariabele toevoegen op de pagina **Aanpassing** van de wizard Takenreeksmedia|Specificeert takenreeksvariabelen en waarden voor de takenreeks die wordt uitgevoerd vanaf de media die toegang heeft tot de takenreeksvariabele en de waarde ervan.|  

 U kunt de standaardwaarde voor een ingebouwde takenreeksvariabele overschrijven door een takenreeksvariabele te definiëren met dezelfde naam als de ingebouwde takenreeksvariabele. Zie voor een lijst met ingebouwde variabelen met de gekoppelde acties en het gebruik, [Takenreeksvariabelen ingebouwde](../understand/task-sequence-built-in-variables.md).  

 U kunt een takenreeksvariabele verwijderen uit de takenreeksomgeving door dezelfde methoden te gebruiken als het maken van een takenreeksvariabele. In dit geval een om variabele te verwijderen uit de takenreeksomgeving, stelt u de variabele waarde op een lege tekenreeks.  

 U kunt methoden combineren om te stellen van een omgevingstakenreeksvariabele op verschillende waarden voor dezelfde reeks. In een geavanceerd scenario, wilt u mogelijk de standaardwaarden instellen voor stappen in een reeks met behulp van de takenreekseditor en vervolgens een aangepaste waarde voor de variabele instellen met behulp van de verschillende aanmaakmethoden. De volgende lijst beschrijft de regels die welke waarde wordt gebruikt bepalen wanneer een takenreeksvariabele wordt gemaakt door meer dan één methode.  

1.  De **Takenreeksvariabele instellen** stap overschrijft alle andere aanmaakmethoden.  

2.  Computer-variabelen krijgen voorrang op per-verzameling-variabelen. Als u de dezelfde naam takenreeksvariabele voor een per-computer en een per-verzameling-variabele opgeeft, wordt de per-computer-variabele gebruikt wanneer de doelcomputer de geïmplementeerde takenreeks uitvoert.  

3.  Takenreeksen kunnen vanaf media worden uitgevoerd. Gebruik de mediavariabelen in plaats van per-verzameling- of per-computer-variabelen. Als de takenreeks vanaf media wordt uitgevoerd, zijn de per-computer- en per-verzameling-variabelen niet van toepassing en worden deze niet gebruikt. In plaats daarvan worden takenreeksvariabelen gedefinieerd op de **aanpassing** pagina van de wizard Takenreeksmedia worden gebruikt om waarden te stellen specifieke aan een takenreeks die vanaf media wordt uitgevoerd  

4.  Als u een waarde taak niet in de algemene reeksomgeving is ingesteld, gebruiken ingebouwde bewerkingen de standaardwaarde voor de stap, zoals ingesteld in de Takenreekseditor.  

 Naast het overschrijven van waarden voor ingebouwde takenreeksstapinstellingen, kunt u ook een nieuwe omgevingsvariabele voor gebruik in een takenreeksstap, script, opdrachtregel of voorwaarde te maken. Wanneer u een naam voor een nieuwe takenreeksvariabele opgeeft, volg deze richtlijnen:  

-   De naam van takenreeksvariabele die u opgeeft mag letters, cijfers, het onderstrepingsteken (_) en een koppelteken (-).  

-   Namen van takenreeksvariabelen zijn minimum van 1 teken en maximaal 256 tekens bestaan.  

-   De gebruiker gedefinieerde variabelen moeten beginnen met een letter (A-Z of a-z).  

-   Gebruiker gedefinieerde namen van variabelen kunnen niet beginnen met het onderstrepingsteken. Alleen-lezen takenreeksvariabelen worden voorafgegaan door het onderstrepingsteken  

    > [!NOTE]  
    >  Alleen-lezen takenreeksvariabelen kunnen worden gelezen door takenreeksstappen in een takenreeks, maar ze kunnen niet worden ingesteld. U kunt bijvoorbeeld een alleen-lezen takenreeksvariabele gebruiken als onderdeel van de opdrachtregel voor een **opdrachtregel uitvoeren** takenreeksvariabele actie toe te voegen, maar kan niet alleen-lezen variabele instellen met behulp van de **Takenreeksvariabele instellen** actie variabele.  

-   Namen van takenreeksvariabelen zijn niet hoofdlettergevoelig. OSDVAR en osdvar vertegenwoordigen bijvoorbeeld dezelfde takenreeksvariabele.  

-   Namen van takenreeksvariabelen kunnen niet beginnen of eindigen met een spatie of geen ingesloten spaties bevatten. Spaties die aan het begin of einde van een naam van takenreeksvariabele worden genegeerd.  

 De volgende tabel geeft enkele voorbeelden van geldige en ongeldige door gebruiker opgegeven takenreeksvariabelen.  

|Voorbeelden van geldige door gebruiker opgegeven namen van variabelen|Voorbeelden van ongeldige door gebruiker opgegeven namen van variabelen|  
|-------------------------------------------------------|----------------------------------------------------------|  
|MyVariable|1Variable<br /><br /> Door gebruiker opgegeven takenreeksvariabelen kunnen niet beginnen met een getal.|  
|My_Variable|MyV@riable<br /><br /> Door gebruiker opgegeven takenreeksvariabelen mogen niet de @-teken.|  
|My_Variable_2|_MyVariable<br /><br /> Door gebruiker opgegeven takenreeksvariabelen kunnen niet beginnen met een onderstrepingsteken.|  

 Algemene beperkingen voor takenreeksvariabelen:  

-   Waarden voor takenreeksvariabelen kunnen niet langer zijn dan 4000 tekens.  

-   U kunt maken of een alleen-lezen takenreeksvariabele overschrijven. Alleen-lezen-variabelen worden aangewezen door namen die beginnen met een onderstrepingsteken (_). U hebt toegang tot de waarde van de alleen-lezen-takenreeksvariabelen in uw takenreeks. U kunt hun gekoppelde waarden echter niet wijzigen.  

-   Waarden voor takenreeksvariabelen kunnen hoofdlettergevoelig zijn afhankelijk van het gebruik van de waarde. Takenreeksvariabelen zijn in de meeste gevallen niet hoofdlettergevoelig. Sommige waarden kunnen echter wel hoofdlettergevoelig zijn, zoals variabelen die een wachtwoord bevatten.  

-   Er is geen limiet voor het aantal takenreeksvariabelen kunnen worden gemaakt. Het maximale aantal variabelen is echter wel beperkt door de grootte van de takenreeksomgeving. De limiet voor de totale grootte van de takenreeksomgeving is 32 MB.  

###  <a name="BKMK_TSEnvironmentVariables"></a> Omgevingsvariabelen openen  
 Nadat u de takenreeksvariabele en de waarde ervan opgeeft met een van de methoden uit de vorige sectie, kunt u de omgevingsvariabele in uw takenreeksen. U kunt de standaardwaarden voor ingebouwde takenreeksvariabelen openen, een nieuwe waarde voor een ingebouwde variabele opgeven of een aangepaste takenreeksvariabele in een opdrachtregel of script gebruiken.  

 De volgende tabel takenreeksbewerkingen die kunnen worden uitgevoerd door het openen van de variabelen van de takenreeksomgeving.  

|Takenreeksbewerking|Gebruik|  
|-----------------------------|-----------|  
|Configureer de bewerkingsinstellingen|U kunt opgeven dat een instelling takenreeksstap wordt geleverd door een variabele waarde wanneer de reeks wordt uitgevoerd.<br /><br /> Een takenreeksstap instellen met behulp van de omgeving van een takenreeksvariabele leveren de Takenreekseditor te gebruiken om te bewerken van de stap en naam van de variabele opgeven als de veldwaarde. De naam van de variabele moet tussen procenttekens (%) worden geplaatst om aan te geven dat het een omgevingsvariabele betreft.|  
|Specificeer de opdrachtregelargumenten|U kunt een gedeelte van of alle aangepaste opdrachtregels opgeven met behulp van een omgevingsvariabele.<br /><br /> Leveren een opdrachtregelinstelling opgeven met behulp van een omgevingsvariabele gebruiken naam van de variabele als onderdeel van de **opdrachtregel** veld van de **opdrachtregel uitvoeren** takenreeksstap. Naam van de variabele moet in procenttekens (%) zijn ingesloten.<br /><br /> De volgende opdrachtregel gebruikt bijvoorbeeld een ingebouwde omgevingsvariabele de computernaam te schrijven naar C:\File.txt.<br /><br /> <br /><br /> **Cmd /C % _SMSTSMachineName % > C:\File.txt**|  
|Evalueer een stapvoorwaarde|U kunt ingebouwde of aangepaste variabelen voor takenreeksomgevingen gebruiken als onderdeel van een takenreeksstap of groepsvoorwaarde. De omgevingsvariabele zal worden geëvalueerd vóór de takenreeksstap of groep.wordt uitgevoerd.<br /><br /> Toevoegen van een voorwaarde die een variabele waarde evalueert, het volgende doen:<br /><br /> 1.  Selecteer de stap of groep die u wilt de voorwaarde wilt toevoegen.<br />2.  Op de **opties** tabblad voor de stap of groep selecteren **Takenreeksvariabele** van de **voorwaarde toevoegen** vervolgkeuzelijst.<br />3.  In de **Takenreeksvariabele** dialoogvenster, geeft u de naam van de variabele, de voorwaarde die wordt getest en de waarde van de variabele.|  
|Geef informatie op voor een aangepast script|Takenreeksvariabelen kunnen worden gelezen en geschreven met behulp van de COM-object Microsoft.SMS.TSEnvironment terwijl de takenreeks wordt uitgevoerd.<br /><br /> Het volgende voorbeeld wordt een Visual Basic-scriptbestand query op de **_SMSTSLogPath** takenreeksvariabele om de huidige Logboeklocatie te achterhalen. Met het script wordt ook een aangepaste variabele ingesteld.<br /><br /> <br /><br /> **dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")**<br /><br /> <br /><br /> **dim logPath**<br /><br /> <br /><br /> **' U kunt een query maken voor de omgeving om een bestaande variabele te verkrijgen.**<br /><br /> **logPath = env("_SMSTSLogPath")**<br /><br /> <br /><br /> **' U kunt ook een variabele instellen in de OSD-omgeving.**<br /><br /> **env("MyCustomVariable") = "varname"**<br /><br /> <br /><br /> Raadpleeg de SDK-documentatie voor meer informatie over het gebruik van takenreeksvariabelen in scripts.|  

###  <a name="BKMK_ComputerCollectionVariables"></a> Computer- en verzamelingsvariabelen  
 U kunt takenreeksen uit te voeren op meerdere computers of verzamelingen tegelijk configureren. U kunt unieke informatie per-computer of per-verzameling opgeven, zoals een productcode unieke besturingssysteem opgeven of alle leden van een verzameling toevoegen aan een opgegeven domein.  

 U kunt takenreeksvariabelen toewijzen aan een enkele computer of een verzameling. Wanneer de takenreeks wordt gestart om uit te voeren op de doelcomputer of -verzameling, wordt de opgegeven waarden worden toegepast op de doelcomputer of -verzameling.  

 U kunt takenreeksvariabelen voor een enkele computer of een verzameling opgeven. Wanneer de takenreeks wordt gestart om uit te voeren op de doelcomputer of -verzameling, wordt de opgegeven variabelen worden toegevoegd aan de omgeving en de waarden zijn beschikbaar voor alle takenreeksstappen in de takenreeks.  

> [!WARNING]  
>  Als u dezelfde naam voor een per-verzameling en de computer-variabele, neemt de computervariabele voorrang op de verzamelingsvariabele. Takenreeksvariabelen die u aan verzamelingen toewijst hebben voorrang op ingebouwde takenreeksvariabelen.  

 Zie voor meer informatie over het maken van takenreeksvariabelen voor computers en verzamelingen [maken van takenreeksvariabelen voor computers en verzamelingen](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTSVariables).  

###  <a name="BKMK_TSMediaVariables"></a> Variabelen voor takenreeksmedia  
 Variabelen voor takenreeksen die vanaf media worden uitgevoerd, kunt u opgeven. Als u media gebruikt voor het implementeren van het besturingssysteem dat u de takenreeksvariabelen toevoegen en hun waarden opgeven bij het maken van de media. de variabelen en hun waarden worden opgeslagen op de media.  

> [!NOTE]  
>  Takenreeksen worden opgeslagen op zelfstandige media. Alle andere typen media, zoals voorbereide media, halen echter de takenreeks van een beheerpunt.  

 U kunt takenreeksvariabelen opgeven op de **aanpassing** pagina van de Wizard Takenreeksmedia. Zie [Takenreeksmedia maken](../deploy-use/create-task-sequence-media.md) voor informatie over het maken van media.  

> [!TIP]  
>  De takenreeks schrijft het pakket-ID en prestart-opdrachtregel, inclusief de waarde voor eventuele takenreeksvariabelen, naar het logboekbestand CreateTSMedia.log op de computer waarop de Configuration Manager-console. U kunt dit logboekbestand controleren om de waarde voor de takenreeksvariabelen te verifiëren.  

##  <a name="BKMK_TSCreate"></a> Een takenreeks maken  
 U maakt takenreeksen via de Wizard Takenreeks maken. De wizard kan ingebouwde takenreeksen maken die specifieke taken of aangepaste takenreeksen uitvoeren, die op hun beurt veel verschillende taken kunnen uitvoeren.  

 U kunt bijvoorbeeld takenreeksen maken die een installatiekopie van een besturingssysteem van een referentiecomputer samenstellen en vastleggen, een bestaande installatiekopie van een besturingssysteem op een doelcomputer installeren, of een aangepaste takenreeks maken die een aangepaste taak uitvoert. Aangepaste takenreeksen kunt u gespecialiseerde besturingssysteemimplementaties uitvoeren.  

 Zie voor meer informatie over het maken van takenreeksen [maken van takenreeksen](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_CreateTaskSequence).  

##  <a name="BKMK_TSEdit"></a> Een takenreeks bewerken  
 De takenreeks te bewerken met de **Takenreekseditor**. De editor kunt u de volgende wijzigingen aanbrengen in de takenreeks:  

-   U kunt toevoegen of verwijderen van stappen van de takenreeks.  

-   U kunt de volgorde van de stappen van de takenreeks wijzigen.  

-   U kunt toevoegen of verwijderen van groepen van stappen.  

-   U kunt opgeven of de takenreeks verder wordt uitgevoerd wanneer er een fout optreedt.  

-   U kunt voorwaarden aan de stappen en groepen van een takenreeks toevoegen.  

> [!IMPORTANT]  
>  Als de takenreeks niet-gekoppelde verwijzingen naar een pakket of een programma als gevolg van de bewerking heeft, moet u de verwijzing te corrigeren, verwijdert het programma zonder verwijzing uit de takenreeks of de mislukte takenreeksstap tijdelijk te deactiveren totdat de verbroken verwijzing is gecorrigeerd of verwijderd.  

 Zie voor meer informatie over het bewerken van takenreeksen [een takenreeks bewerken](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

##  <a name="BKMK_TSDeploy"></a> Een takenreeks implementeren  
 U kunt een takenreeks implementeren op doelcomputers die zich in een Configuration Manager-verzameling. Dit omvat de verzameling **Alle onbekende computers** die wordt gebruikt om besturingssystemen naar onbekende computers te implementeren. U kunt een takenreeks echter niet implementeren op gebruikersverzamelingen.  

> [!IMPORTANT]  
>  Implementeer geen takenreeksen die besturingssystemen installeren naar ongeschikte verzamelingen, zoals de verzameling **Alle systemen** . Zorg ervoor dat de verzameling waar u de takenreeks naar implementeert alleen die computers bevat waarvoor u wilt dat het besturingssysteem wordt geïnstalleerd. U kunt een ongewenste besturingssysteemimplementatie voorkomen door de implementatie-instellingen te beheren. Zie voor meer informatie [instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

 Elke doelcomputer die de takenreeks ontvangt, voert de takenreeks uit volgens de instellingen die zijn opgegeven in de implementatie. De takenreeksen bevatten zelf geen gekoppelde bestanden of programma's. Bestanden waar een taak naar verwijst, moeten reeds aanwezig zijn op de doelcomputer of zich bevinden op een distributiepunt waar clients toegang tot hebben. Bovendien installeert de takenreeks de pakketten waarnaar wordt verwezen door programma's, zelfs als het programma of het pakket is al geïnstalleerd op de doelcomputer.  

> [!NOTE]  
>  Anders dan pakketten en programma's als de takenreeks een toepassing installeert de toepassing wordt geïnstalleerd als de regels voor vereisten voor de toepassing wordt voldaan en de toepassing niet al is geïnstalleerd, op basis van de detectiemethode voor de toepassing.  

 De Configuration Manager-client voert een takenreeksimplementatie wanneer deze clientbeleid downloadt. Zie [Initiate Policy Retrieval for a Configuration Manager Client](../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) (Ophalen van beleid voor een Configuration Manager-client starten) om deze bewerking te starten in plaats van te wachten tot de volgende polling-cyclus.  

 Wanneer u takenreeksen implementeert op Windows Embedded-apparaten met ingeschakelde schrijffilter, kunt u opgeven of de schrijffilter tijdens de implementatie moet worden uitgeschakeld op het apparaat en het apparaat na de implementatie opnieuw opstarten. Als het schrijffilter niet wordt uitgeschakeld, de takenreeks wordt geïmplementeerd op een tijdelijke overlay en wordt deze niet meer beschikbaar wanneer het apparaat opnieuw wordt opgestart.  

> [!NOTE]  
>  Wanneer u een takenreeks op een Windows Embedded-apparaat implementeert, zorg ervoor dat het apparaat lid is van een verzameling met een geconfigureerd onderhoudsvenster. Hiermee kunt u beheren wanneer het schrijffilter is uitgeschakeld en ingeschakeld en wanneer het apparaat opnieuw wordt opgestart.  
>   
>  Als clients takenreeksen buiten een onderhoudsvenster downloaden, wordt de takenreeks twee keer gedownload. In dit scenario wordt clients de takenreeks downloaden, de schrijffilters uitschakelen, de computer opnieuw opstarten en vervolgens opnieuw downloaden, de takenreeks omdat de takenreeks is gedownload naar de tijdelijke overlay die wordt gewist wanneer het apparaat opnieuw wordt opgestart.  

 Zie voor meer informatie over het implementeren van takenreeksen de [een takenreeks implementeren](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

##  <a name="BKMK_TSExportImport"></a> Takenreeksen exporteren en importeren  
 Configuration Manager kunt u exporteren en importeren van takenreeksen. Als u een takenreeks exporteert, kunt u de objecten toevoegen waar de takenreeks naar verwijst. Hieronder vallen de installatiekopie van een besturingssysteem, een opstartinstallatiekopie, een clientagentpakket, een stuurprogrammapakket en toepassingen die afhankelijkheden hebben.  

> [!NOTE]  
>  Proces van exporteren en importeren voor takenreeks is heel vergelijkbaar met het proces van exporteren en importeren voor toepassingen in Configuration Manager.  

 Zie voor meer informatie over het exporteren en importeren van takenreeksen [exporteren en importeren van takenreeksen](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ExportImport).  

##  <a name="BKMK_TSRun"></a> Een takenreeks uitvoeren  
 Standaard worden takenreeksen altijd uitgevoerd met behulp van het lokale systeemaccount. De opdrachtregelstap voor takenreeksen geeft u de mogelijkheid om de takenreeks als een ander account uit te voeren. Wanneer de takenreeks wordt uitgevoerd, controleert de Configuration Manager client eerst of er pakketten met verwijzingen voordat er begonnen wordt met de stappen van de takenreeks. Als een pakket met verwijzingen niet wordt gevalideerd of als het niet beschikbaar is op een distributiepunt, geeft de takenreeks een foutmelding voor de gekoppelde takenreeksstap.  

 Als een gedistribueerde takenreeks is geconfigureerd om te downloaden en uitvoeren, worden alle afhankelijke pakketten en toepassingen gedownload naar de clientcache voor Configuration Manager. De vereiste pakketten en toepassen worden verkregen vanaf distributiepunten en als de Configuration Manager-client-cachegrootte te klein is of het pakket of de toepassing kan niet worden gevonden, mislukt de takenreeks en een statusbericht gegenereerd. U kunt ook opgeven dat de client de inhoud alleen downloadt wanneer dit is vereist door de optie **De inhoud lokaal downloaden wanneer deze nodig is voor de takenreeks die wordt uitgevoerd**te selecteren. U kunt ook de optie **Programma uitvoeren vanaf distributiepunt** gebruiken om aan te geven dat de client de bestanden rechtstreeks van het distributiepunt downloadt zonder ze eerst in het cachegeheugen te downloaden. De **programma uitvoeren vanaf distributiepunt** optie is alleen beschikbaar als de instelling van de pakketten met verwijzingen hebben **de inhoud in dit pakket kopiëren naar een pakketshare op distributiepunten** ingeschakeld op de **gegevenstoegang** tabblad van het **pakket** eigenschappen.  

 Als een afhankelijk pakket of toepassing kan niet worden gevonden door de client de takenreeks wordt uitgevoerd, de client onmiddellijk een fout opgetreden bij de implementatie is geconfigureerd als **beschikbaar**. Echter, als de implementatie is geconfigureerd als **vereist**, wacht de Configuration Manager-client en pogingen die de inhoud te downloaden tot de deadline is bereikt, als de inhoud nog niet is gerepliceerd naar een distributiepunt die wijst de client toegang heeft.  

 Wanneer een takenreeks is voltooid of mislukt, registreert Configuration Manager dit in de clientgeschiedenis van de Configuration Manager. Annuleren kan of stoppen van een takenreeks nadat deze is gestart op een computer.  

> [!IMPORTANT]  
>  Als een takenreeksstap vereist dat de clientcomputer opnieuw op te starten, de client moet in staat zijn om op te starten naar een geformatteerde schijfpartitie. Anders werkt de takenreeks niet, ongeacht een eventuele door de takenreeks opgegeven foutafhandeling.  

 Wanneer een afhankelijk object van een takenreeks, zoals een softwaredistributiepakket, wordt bijgewerkt naar een nieuwere versie, wordt elke takenreeks die verwijst naar het pakket automatisch bijgewerkt; er wordt verwezen naar de nieuwste versie, ongeacht het aantal geïmplementeerde updates.  

> [!NOTE]  
>  Voordat een takenreeks van een Configuration Manager-client wordt uitgevoerd, controleert de client alle takenreeksen op mogelijke afhankelijkheden en de beschikbaarheid van die afhankelijkheden op een distributiepunt. Als de client een verwijderd object vindt waarvan de takenreeks afhangt, genereert de client een fout en wordt de takenreeks niet uitgevoerd.  

###  <a name="BKMK_RunProgram"></a> Een programma uitvoeren voordat de takenreeks wordt uitgevoerd  
 U kunt een programma selecteren dat wordt uitgevoerd voordat de takenreeks wordt uitgevoerd. Als u een programma voor het eerst, opent u de **eigenschappen** in het dialoogvenster voor de takenreeks en selecteert de **Geavanceerd** tabblad instellen van de volgende opties:  

> [!IMPORTANT]  
>  Als u wilt een programma uitvoeren voordat de takenreeks wordt uitgevoerd, wordt alle inhoud voor de taak moeten en het programma beschikbaar zijn op een pakketshare voor het pakket. U configureert de pakketshare op het tabblad **Gegevenstoegang** in de eigenschappen voor het pakket.  

-   **Eerst een ander programma uitvoeren**: Opgeven dat u een ander programma wilt uitvoeren voordat de takenreeks wordt uitgevoerd.  

    > [!IMPORTANT]  
    >  Deze instelling geldt alleen voor takenreeksen die in het volledige besturingssysteem worden uitgevoerd. Configuration Manager negeert deze instelling als de takenreeks wordt gestart via PXE of een opstartmedium.  

-   **Pakket**: Het pakket met het programma opgeven.  

-   **Programma**: Uit te voeren programma opgeven.  

-   **Altijd eerst dit programma uitvoeren**: Opgeven dat u dit programma wordt uitgevoerd telkens als de takenreeks op dezelfde client wordt uitgevoerd door Configuration Manager. Wanneer de uitvoering van een programma is gelukt, wordt dit standaard niet opnieuw uitgevoerd als de takenreeks opnieuw op dezelfde client wordt uitgevoerd.  

 Als de uitvoering van het geselecteerde programma op een client is mislukt, wordt de takenreeks niet uitgevoerd.  

##  <a name="BKMK_TSMaintenanceWindow"></a> Een onderhoudsvenster gebruiken om op te geven wanneer een takenreeks kan worden uitgevoerd  
 U kunt opgeven wanneer de takenreeks kan worden uitgevoerd door een onderhoudsvenster voor de verzameling die waartoe uw doelcomputers behoren te definiëren. Onderhoudsvensters worden geconfigureerd met een startdatum, een start- en eindtijd en een terugkeerpatroon. Wanneer u bovendien de planning instelt voor het onderhoudsvenster, kunt u aangeven dat het onderhoudsvenster alleen van toepassing is op takenreeksen. Zie voor meer informatie [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

> [!IMPORTANT]  
>  Wanneer u een onderhoudsvenster configureert om een takenreeks uit te voeren, gaat na de start van de takenreeks de uitvoering van de takenreeks gewoon door als het onderhoudsvenster wordt gesloten. De takenreeks wordt geheel voltooid of deze werkt niet.  

##  <a name="BKMK_TSNetworkAccessAccount"></a> Takenreeksen en het netwerktoegangsaccount  
 Hoewel takenreeksen alleen worden uitgevoerd in de context van het lokale systeemaccount, moet u mogelijk het netwerktoegangsaccount configureren in de volgende omstandigheden:  

-   U moet het netwerktoegangsaccount correct configureren, omdat de takenreeks anders mislukt als deze probeert toegang tot Configuration Manager-pakketten op distributiepunten om de taak te voltooien. Zie voor meer informatie over het netwerktoegangsaccount [netwerktoegangsaccount](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#a-namebkmknaaa-network-access-account).  

    > [!NOTE]  
    >  Het netwerktoegangsaccount wordt nooit gebruikt als de beveiligingscontext voor uitvoeren van programma's, installatie van toepassingen, installatie van updates of uitvoeren van takenreeksen; echter, het netwerktoegangsaccount wordt gebruikt voor toegang tot de betreffende hulpbronnen op het netwerk.  

-   Wanneer u een opstartinstallatiekopie gebruiken om de implementatie van een besturingssysteem, Configuration Manager maakt gebruik van de Windows PE-omgeving niet een volledig besturingssysteem is. De Windows PE-omgeving maakt gebruik van een automatisch gegenereerde, willekeurige naam die geen lid is van een domein. Als u het netwerktoegangsaccount niet correct configureert, is de computer wellicht niet de vereiste machtigingen om toegang tot de vereiste Configuration Manager-pakketten om te voltooien van de takenreeks.  

##  <a name="BKMK_TSCreateMedia"></a> Media maken voor takenreeksen  
 U kunt takenreeksen en verwante bestanden en afhankelijkheden naar verschillende mediatypen schrijven. Hieronder valt ook het schrijven naar verwijderbare media als een dvd- of cd-speler of een USB-stick voor registrerende, zelfstandige, opstartbare media, of het schrijven naar een WIM-bestand (WIM: Windows Imaging Format) voor voorgefaseerde media.  

 U kunt de volgende typen media maken:  

-   **Registrerende media**. Installatiekopie de registratie van de media een besturingssysteem dat is geconfigureerd en gemaakt buiten de Configuration Manager-infrastructuur. registrerende media kunnen aangepaste programma's bevatten die u kunt uitvoeren voordat een takenreeks wordt uitgevoerd. Het aangepaste programma kan met het bureaublad communiceren, de gebruiker vragen om invoerwaarden of variabelen maken die worden gebruikt door de takenreeks.  

     Zie voor meer informatie [vastlegmedia maken](../deploy-use/create-capture-media.md).  

-   **Zelfstandige media**. Zelfstandige media bevatten de takenreeks en alle gekoppelde objecten die nodig zijn voor de uitvoering van de taak. Zelfstandige media taak reeksen kunnen worden uitgevoerd wanneer de Configuration Manager heeft beperkte of geen verbinding heeft met het netwerk. Zelfstandige media kan worden uitgevoerd op de volgende manieren:  

    -   Als de doelcomputer niet is opgestart, wordt de Windows PE-installatiekopie die is gekoppeld aan de takenreeks vanaf zelfstandige media wordt gebruikt en de takenreeks begint.  

    -   De zelfstandige media kunnen handmatig worden gestart als een gebruiker is aangemeld bij het netwerk en de installatie start.  

    > [!IMPORTANT]  
    >  De stappen van een zelfstandige media takenreeks moet worden uitgevoerd zonder een bij het ophalen van gegevens vanaf het netwerk; anders mislukt de takenreeksstap die probeert de gegevens op te halen. Bijvoorbeeld, een takenreeksstap toe die vereist een distributiepunt om een pakket te verkrijgen is mislukt; maar als het benodigde pakket zich op de zelfstandige media, lukt de takenreeksstap.  

     Zie voor meer informatie [maken van zelfstandige media](../deploy-use/create-stand-alone-media.md).  

-   **Opstartbare media**. Opstartbare media bevatten de benodigde bestanden voor het starten van een doelcomputer, zodat deze verbinding kan maken met de Configuration Manager-infrastructuur om te bepalen welke takenreeksen die moeten worden uitgevoerd op basis van lidmaatschap van een verzameling. De takenreeks en afhankelijke objecten bevinden zich niet op de media. maar worden daarentegen via het netwerk van de Configuration Manager-client. Deze methode is handig voor nieuwe computers of bare-metal implementaties, of wanneer er geen Configuration Manager-client of besturingssysteem bevindt op de doelcomputer.  

     Zie voor meer informatie [opstartbare media maakt](../deploy-use/create-bootable-media.md).  

-   **Voorbereide media**. Voorgefaseerde media implementeren een installatiekopie van een besturingssysteem op een niet-ingerichte computer. De voorbereide media worden opgeslagen als een Windows Imaging Format (WIM)-bestand dat kan worden geïnstalleerd op een bare-metal computer door de fabrikant of in een enterprise-voorbereidingscentrum dat niet is verbonden met de Configuration Manager-omgeving.  

     Zie voor meer informatie [maken voorbereide media](../deploy-use/create-prestaged-media.md).  

 Wanneer u media maakt, Geef een wachtwoord voor de media om toegang tot de bestanden die zijn opgenomen op de media te beheren. Als u een wachtwoord opgeeft, is een gebruiker moet aanwezig zijn voor het invoeren van het wachtwoord op de doelcomputer wanneer de takenreeks wordt uitgevoerd.  

 Wanneer u een takenreeks uitvoert met behulp van media, de opgegeven computer chiparchitectuur op de media niet herkend en de takenreeks probeert uit te voeren, zelfs als de opgegeven architectuur niet overeenkomt met wat daadwerkelijk op de doelcomputer is geïnstalleerd. Als de chiparchitectuur op de media komt niet overeen met de chiparchitectuur die op de doelcomputer is geïnstalleerd, mislukt de installatie.  

 Zie voor meer informatie over het implementeren van besturingssystemen met behulp van media [takenreeksmedia maken](../deploy-use/create-task-sequence-media.md).  

