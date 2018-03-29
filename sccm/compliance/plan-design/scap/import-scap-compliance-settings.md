---
title: De SCAP-instellingen voor naleving importeren
titleSuffix: System Center Configuration Manager
description: De instellingen voor de SCAP-naleving als configuratiebasislijnen importeren en exporteren van de resultaten
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0bdcb018-bac2-4540-b786-6242bac73ff4
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 5863f8b9a79e8e22e215e9feac7744b4a6ce279d
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="import-the-compliance-settings-compliant-cab-files-into-system-center-configuration-manager"></a>De naleving instellingen compatibele CAB-bestanden importeren naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

> [!Tip]  
> Deze functie is geïntroduceerd in Technical Preview-versie 1803 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Deze voorlopige versie van de SCAP-extensies kan worden geïnstalleerd op alle ondersteunde versies van de huidige vertakking van Configuration Manager en LTSB 1606. Het installatiebestand bevindt zich op cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi vanaf technical preview 1803. 

De volgende stap in het proces is de Configuration Manager-Console gebruiken om te importeren van de naleving instellingen compatibele CAB-bestanden in Configuration Manager. Wanneer u de CAB-bestanden die u eerder in dit proces gemaakt importeert, worden een of meer configuratie-items en configuratiebasislijnen gemaakt in de Configuration Manager-database. Later in het proces kunt u elk van de configuratiebasislijnen toewijzen aan een computerverzameling in Configuration Manager.

## <a name="to-import-the-compliance-settings-compliant-cab-files-into-configuration-manager"></a>De instellingen voor naleving compatibele CAB-bestanden importeren naar Configuration Manager

1. Open de **Configuration Manager-Console**.
2. In de ** Configuration Manager-Console in het navigatiedeelvenster, gaat u naar **activa en naleving**> **instellingen voor naleving** > **Configuratiebasislijnen** .

3. Klik in het actiedeelvenster op **configuratiegegevens importeren** starten van de Wizard configuratiegegevens importeren.

1. Voltooi de **Wizard configuratiegegevens importeren** met behulp van de informatie in de volgende tabel en accepteer de standaardwaarden tenzij anders vermeld.



Gegevens importeren-Wizard configuratieproces

| Paginanaam van wizard | Gebruikersactie |
| --- | --- |
| **Bestanden kiezen** |1. Klik op **Toevoegen**. </br>In het dialoogvenster openen wordt weergegeven.|
||2. In de **Open** in het dialoogvenster, gaat u naar de **&lt;compatibele cab uitvoer\_map &gt;**. Klik op de  **&lt; compatibel\_CAB-bestand&gt;**CAB-bestand, waarbij _compliant CAB-bestand **uitvoer\_map** is de map die is opgegeven na de: de schakeloptie uitvoer wanneer u het hulpprogramma Sces.ScapToDcm.exe hebt uitgevoerd. **compatibele\_bestand** is de naam van een CAB-bestand dat u eerder in het proces hebt gemaakt. Klik vervolgens op **Open**. </br> De Configuration Manager-Console – dialoogvenster Beveiligingswaarschuwing wordt weergegeven.|
||3. In de **Configuration Manager-Console beveiligingswaarschuwing** in het dialoogvenster, klikt u op **uitvoeren**. Op de pagina bestanden kiezen worden de configuratiegegevens weergegeven in de lijst met basislijnen om te importeren.|
||3. Klik op **Volgende**.|
| **Samenvatting** |5. Klik op **Volgende**. |
| **De Wizard configuratiegegevens importeren voltooien** |6. Klik op **Sluiten**. |

De nieuwe configuratiebasislijn wordt weergegeven in het Informatiedeelvenster van de Configuration Manager-Console.

>[!IMPORTANT]
> U moet dit proces herhalen voor elk CAB-bestand dat u eerder in het proces hebt gemaakt. Er is een CAB-bestand voor elke selectedprofile in XCCDF/DataStreamXML-bestand dat u hebt gedownload van de NVD-website, die u door het hulpprogramma Microsoft.Sces.ScapToDcm.exe kunt verwerken.

De geïmporteerde configuratiebasislijn is alleen-lezen en heeft de Status van &#39;ingeschakeld&#39; en begin de implementatiestatus van &#39;Nee&#39;.  De &#39;wijzigingsdatum&#39; eigenschap geeft de tijd dat de basislijn is geïmporteerd.  De naam van de configuratiebasislijn wordt overgenomen uit de sectie weergavenaam van de XCCDF/Datastream XML. De naam is gebouwd met behulp van de volgende conventies:

ABC [XYZ], waarbij ABC is de ID XCCDF-Benchmark en XYZ is de profiel-ID XCCDF als (u een profiel is geselecteerd).



## <a name="assign-configuration-baselines-to-the-computer-collections"></a>Configuratiebasislijnen toewijzen aan de Computerverzamelingen

Na het maken van de juiste computerverzamelingen voor de computers die u voor SCAP-naleving wilt beoordelen, kunt u de configuratiebasislijnen die u hebt geïmporteerd, koppelen aan de computerverzamelingen toewijzen. Deze sectie bevat informatie over het toewijzen van een configuratiebasislijn aan een computerverzameling met de Configuration Manager-Console.

Een configuratiebasislijn toewijzen aan een computerverzameling:

1. Open de **Configuration Manager****Console**.  

2. In de **Configuration Manager-Console in het navigatiedeelvenster, gaat u naar **activa en naleving** > **instellingen voor naleving**  >**  Configuratie basislijnen **.
3. Klik in het navigatievenster op &lt; ** configuratie\_basislijn >, waarbij &lt; _configuratie\_basislijn&gt;_  is de naam van de configuratiebasislijn die u hebt u wilt toewijzen aan een computerverzameling.

    De lijst met configuratie-items voor de configuratiebasislijn wordt weergegeven in het Informatiedeelvenster van Configuration Manager.

4. Klik in het actiedeelvenster op **implementeren**.

5. Voltooi de **implementeren****Configuratiebasislijn****dialoogvenster** met behulp van de informatie in de volgende tabel en accepteer de standaardwaarden tenzij anders vermeld.    

### <a name="deploy-configuration-baseline-dialog-process"></a>Dialoogvenster configuratieproces van basislijn implementeren

| Paginanaam van wizard | Gebruikersactie |
| --- | --- |
| **Verzameling kiezen** | 1. Klik op **Bladeren**.|
||2. In de **verzameling selecteren** in het dialoogvenster Selecteer **Apparaatverzamelingen**. Klik vervolgens op  **&lt;computer\_verzameling&gt;**, waarbij &lt; _computer\_verzameling&gt;_  is de naam van de computerverzameling die u eerder in het proces hebt gemaakt. Klik op **OK**.|
| **Planning instellen** |3. Selecteer de planning die geschikt is voor uw organisatie.|
 
>[!IMPORTANT]
> Herhaal dit proces voor de computerverzameling van elke die u wilt toewijzen aan elke configuratiebasislijn. Ten minste toewijzen elke configuratiebasislijn aan ten minste één computerverzameling.

## <a name="verify-that-the-compliance-data-has-been-collected"></a>Controleren of de gegevens zijn verzameld

Voordat u exporteert de gegevens voor de SCAP-indeling, moet u controleren of de gegevens zijn verzameld. Nadat u een configuratiebasislijn hebt toegewezen aan een computerverzameling, verzamelt de Configuration Manager-client op elke computer in de verzameling automatisch de informatie over de compatibiliteit. De compatibiliteitsinformatie wordt vervolgens opgeslagen in de Configuration Manager-database.

U weergeven de status van de implementatie van de configuratiebasislijn in Configuration Manager om ervoor te zorgen dat de juiste gegevens zijn verzameld door de Configuration Manager-clients. Het is belangrijk om te controleren of de juiste Nalevingsgegevens zijn verzameld in Configuration Manager omdat dit kan helpen de XCCDF/DataStream-bestanden die u later in het proces maakt valideren.



### <a name="verify-that-the-compliance-data-has-been-collected"></a>Controleren of de gegevens zijn verzameld

1. Open de Configuration Manager-Console.
2. Ga in de Configuration Manager-Console in het navigatiedeelvenster naar **bewaking** > **implementaties**.
3. Klik op de **onderdeeltype** voor het implementatietype sorteren en zoek items met het type **basislijn** in de lijst.
4. Met de rechtermuisknop op de &lt;configuratie\_basislijn&gt; in de lijst die u zojuist hebt geïmplementeerd naar de verzameling en klik op **Status weergeven**.
5. Ga vervolgens naar de &lt;configuratie\_basislijn&gt; knooppunt om weer te geven van de compatibele status, als er een machine met de status onbekend is, wordt het verzamelen van de Nalevingsgegevens betekent nog niet is voltooid voor dat de machine.

### <a name="validate-the-xccdfdatastream-results"></a>Valideren van de XCCDF/Datastream-resultaten

1. Open de Configuration Manager-console.
2. Ga in de Configuration Manager-console in het navigatiedeelvenster naar **instellingen voor naleving** > **SCAP Dashboard**.
3. Selecteer de Configuratiebasislijn, toewijzing SCAP-bestand, Datastream, Benchmark en -profiel (indien van toepassing).
4. Klik op **rapport tonen**
 ![SCAP-rapport](./media/scap-report.png)



## <a name="export-compliance-results-to-scap-format"></a>Nalevingsresultaten exporteren naar SCAP-indeling

De volgende taak in het proces is de gegevens voor de instellingen voor naleving exporteren naar SCAP-indeling een bestand ARFreport in XML-/ leesbare indeling is. De SCAP-extensies exporteren en de Wizard Microsoft.Sces.DcmToScap.exe hulpprogramma exporteert een afzonderlijk XCCDF/DataStreamARF resultatenbestand voor elke configuratiebasislijn van de instellingen voor naleving. Deze bestanden komen overeen met elke XCCDF/DataStream-invoerbestanden die het hulpprogramma Microsoft.Sces.ScapToDcm.exe gebruikt voor het maken van elke configuratiebasislijn van de instellingen voor naleving.

### <a name="export-the-compliance-settings-compliance-data-using-the-export-scap-report-wizard"></a>Exporteren van de gegevens voor de instellingen voor naleving met de Wizard SCAP-rapport exporteren

1. Start de Wizard SCAP-rapport exporteren in het menu rechts Klik op het SCAP-Dashboard.
![Importeren uit de SCAP-dashboard](./media/import-from-scap-dashboard.png)

2. Selecteer de Configuratiebasislijn en toewijzing ![Selecteer basislijn](./media/select-ci-baseline.png)

3. Kies de locatie van de SCAP datastream-bestand, de XCCDF/CPE-bestand of de Oval-inhoud en variabele-bestanden.
![Kies datastream](./media/export-scap-report-datastream.png)

4. Geef de naam van de organisatie en kies de locatie van de map voor het exporteren van het SCAP-rapport.
 ![Kies datastream](./media/specify-org-export.png)

5. Bevestig de instellingen.
 ![Kies datastream](./media/confirm-export.png)

6. Kies ** naast het rapport exporteren.  Er verschijnt een voortgangsbalk weergegeven, waarna een voltooiingspagina.
 ![Het exporteren voltooid](./media/complete-report-export.png)



### <a name="alternate-method-export-the-compliance-settings-compliance-data-using-the-microsoftscesdcmtoscapexe-tool"></a>(Alternatieve methode) De gegevens voor de instellingen voor naleving met het hulpprogramma Microsoft.Sces.DcmToScap.exe exporteren

1. Bij de opdrachtprompt, gaat u naar AdminConsole\Bin maptype de opdrachtregelparameters die in de volgende tabel worden vermeld en druk vervolgens op ** ENTER:

    >[!NOTE] 
    >Uw account moet leesmachtigingen hebben voor de Configuration Manager-provider en ook schrijfmachtigingen voor de uitvoermap opgegeven de out-parameter van de opdrachtregel.

**Voor SCAP 1.0/1.1-inhoud (zoals USGCB- en DISA-inhoud):**

Microsoft.Sces.DcmToScap.exe-basislijn BaselineCIID-toewijzing AssignmentID xccdf &lt;xccdf.xml&gt; - cpe &lt;cpe.xml&gt; -Selecteer &lt;xccdfBenchmark/profiel&gt; -out &lt;outputResultFolder&gt; [-Meld logFileName]

  >[!NOTE] 
    >Moet u de – Selecteer parameter om de benchmark of het profiel dat is beoordeeld op de clients als er meerdere benchmarks/profielen in de inhoud.

**Voor SCAP1.2-inhoud (zoals de meest recente USGCB-inhoud):**

Microsoft.Sces.DcmToScap.exe-basislijn BaselineCIID-toewijzing AssignmentID-Selecteer &lt;xccdfBenchmark-datastream-profiel&gt; -out &lt;outputResultFolder&gt; [-Meld logFileName]

   >[!NOTE] 
   >Moet u de – Selecteer parameter om de datastream/benchmark of het profiel dat is beoordeeld op de clients als er meerdere datastream benchmarks/profielen in de inhoud.

**Voor één OVAL-bestand met externe variabelen:**

Microsoft.Sces.DcmToScap.exe-basislijn BaselineCIID-toewijzing AssignmentID – oval &lt;singleOvalFile.xml&gt; [-variabele &lt;externalVariableFile.xml&gt;]-out &lt;outputResultFolder &gt; [-Meld logFileName]

   >[!NOTE] 
    >De _will Microsoft.Sces.DcmToScap.exe alleen OVAL definitie resultatenrapport genereren voor elke doelcomputer, ARF-rapport wordt niet gegenereerd.

#### <a name="how-to-get-baseline-ci-id-and-assignment-id"></a>Basislijn CI-ID en de toewijzings-ID ophalen

Ga in de beheerconsole van naar **activa en naleving** > **instellingen voor naleving** > **Configuratiebasislijnen**. De CI-ID is de configuratie van basislijn-CI-ID.

![De CI-ID en de toewijzings-ID ophalen](./media/get-to-baselines.png)

Selecteer de gewenste Configuratiebasislijn, klik op tabblad implementaties als toewijzings-ID niet in de weergave, met de rechtermuisknop op de kolomkop, toewijzings-ID als u wilt inschakelen.
![De CI-ID en de toewijzings-ID ophalen](./media/get-to-baselines.png)


#### <a name="microsoftscesdcmtoscapexe-command-line-parameters"></a>Microsoft.Sces.DcmToScap.exe Command-Line Parameters

| **Parameter** | **Gebruik** | **Vereist** |
| --- | --- | --- |
| -baseline [Baseline CI ID] | Geef de Configuratiebasislijn | Ja |
| -toewijzing [toewijzings-ID] | De implementatie van de Configuratiebasislijn opgeven | Ja |
| -organization [Bedrijfsnaam] | Geef de naam van de organisatie, die in het rapport weergegeven. Kunnen worden gescheiden door &#39;; &#39; de naam van een bedrijf uit meerdere regels op te geven. | Nee |
| -type [dun/full/fullnosc] | Geef het OVAL-resultaattype: thin resultaat of full-resultaat of full-resultaat zonder systeemkenmerken. | Nee (als dit niet is opgegeven, wordt de standaardwaarde is vol) |
| -scap [scap-gegevenstroombestand] | Het SCAP-gegevensstroombestand opgeven | Ja (voor SCAP 1.2-gegevensstroom, wederzijds uitsluitend met xccdf en -oval / - variable) |
| -xccdf [xccdf-bestand] | Geef het XCCDF-bestand | Ja (voor SCAP 1.0/1.1 XCCDF, wederzijds uitsluitend met-scap en -oval / - variable) |
| -cpe [cpe-bestand] | Geef het CPE-bestand | Ja (voor SCAP 1.0/1.1 XCCDF, wederzijds uitsluitend met-scap en -oval / - variable) |
| -oval [oval-bestand] | Geef het OVAL-bestand | Ja (voor een zelfstandig OVAL-bestand, wederzijds uitsluitend met xccdf en scap) |
| -variabele [oval bestand met externe variabelen] | Geef het OVAL bestand met externe variabelen | Er is geen (optioneel voor een zelfstandig OVAL-bestand wanneer er een OVAL bestand met externe variabelen, wederzijds uitsluitend met xccdf en scap) |
| -Selecteer [xccdfbenchmark /-profiel] | Selecteer XCCDF-benchmark of het profiel op via het SCAP-gegevensstroombestand of het XCCDF-bestand | Ja (een selectie moet worden gemaakt voor een rapport genereren zodat u kunt overeenkomen met de bijbehorende DCM-basislijn in Configuration Manager-database |
| -out [uitvoermap] | Geef op waar voor uitvoer van de instellingen voor naleving cab-bestand | Nee (als niet wordt opgegeven, klikt u vervolgens het hulpprogramma zouden alleen de lijst van de inhoud zonder conversie) |
| -log [logboekbestand] | Geef het logboekbestand | Nee (als dit niet is opgegeven, wordt het logboek wordt geschreven naar Microsoft.Sces.DcmToScap.log-bestand) |
| -help / -? | Hulpprogrammagebruik afdrukken | Nee |



 >[!TIP] 
 >U kunt opgeven? -h, of -help opgeven om de syntaxis van het hulpprogramma Microsoft.Sces.DcmToScap.exe en een lijst van de parameters weer te geven.

Het hulpprogramma Microsoft.Sces.DcmToScap.exe standaard heeft toegang tot de Configuration Manager-database met uw referenties. Het hulpprogramma Microsoft.Sces.DcmToScap.exe vereist minimaal leestoegang tot de Configuration Manager-database.

Nadat u hebt gecontroleerd dat de juiste **ARF** rapport: _ARF\_xxxx.xml_ en/of **leesbare** report: xxx.txt, **Cyberscope** rapport: LASR\_xxx.xml, **ConsumedOval** rapport: xx-oval -&lt;machineName&gt;.xml, **XCCDF-Benchmark resultaat** rapport: xccdf\_xxx.xml bestanden aanwezig zijn , typ afsluiten op de opdrachtregel en druk vervolgens op **ENTER** om af te sluiten van de opdrachtprompt.

## <a name="next-step"></a>Volgende stap
> [!div class="nextstepaction"]
> [Het oplossen van problemen](/sccm/compliance/plan-design/scap/troubleshooting-scap)
