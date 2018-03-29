---
title: Installeren en configureren van uitbreidingen Security Content Automation Protocol (SCAP)
titleSuffix: System Center Configuration Manager
description: Installeren en configureren van de extensies Security Content Automation Protocol (SCAP)
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f53b484b-5123-48f0-be2f-4e30318f3d39
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 03fc9fa9f82aeae8ab22d6b4c3fa7858e93401cc
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="install-and-configure-the-scap-extensions-for-microsoft-system-center-configuration-manager"></a>Installeer en configureer SCAP Extensions voor Microsoft System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

> [!Tip]  
> Deze functie is geïntroduceerd in Technical Preview-versie 1803 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Deze voorlopige versie van de SCAP-extensies kan worden geïnstalleerd op alle ondersteunde versies van de huidige vertakking van Configuration Manager en LTSB 1606. Het installatiebestand bevindt zich op cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi vanaf technical preview 1803.   

Na het voorbereiden van de vereiste infrastructuur, bent u klaar om te installeren en configureren van de SCAP-extensies voor Microsoft System Center Configuration Manager op de computer van waaruit u wilt uitvoeren van dit proces.

## <a name="install-scap-extensions-configuration-manager"></a>SCAP Extensions Configuration Manager installeren

1. Configuration Manager uitvoeren\_extensies\_voor\_SCAP.msi het hulpprogramma te installeren.
2. In Windows Verkenner, Ga naar de map waarin u gedownload de **ConfigMgr\_extensies\_voor\_SCAP.msi** bestand en dubbelklik vervolgens op de **ConfigMgr\_ Extensies\_voor\_SCAP.msi** bestand. Hiermee start u de SCAP-extensies voor Microsoft System Center Configuration Manager-installatiewizard.

Voltooi de **SCAP Extensions voor Microsoft System Center Configuration Manager-installatiewizard** met de informatie in de volgende tabel, accepteert de wizard&#39;s standaardwaarden tenzij u hoeft te geven.

**Tabel 1.0** SCAP Extensions voor Microsoft System Center Configuration Manager-installatiewizard proces

| Paginanaam van wizard | Gebruikersactie |
| --- | --- |
| Welkom en gebruiksrechtovereenkomst |1. Lees de gebruiksrechtovereenkomst|
| Welkom en gebruiksrechtovereenkomst|2. Klik op **ik ga akkoord met de voorwaarden in deze gebruiksrechtovereenkomst**.|
| Welkom en gebruiksrechtovereenkomst|3. Klik op **Installeren**.|
| De SCAP-extensies voltooien voor Microsoft System Center Configuration Manager-installatiewizard |4. Klik op **Voltooien**.|
 



De SCAP Extensions voor Microsoft System Center Configuration Manager-installatiewizard installeert de extensies standaard in de installatiemap van de Configuration Manager-console.



## <a name="download-and-install-the-scap-data-stream-files"></a>Download en installeer de SCAP-Gegevensstroombestanden

Voordat u de SCAP-extensies voor SCAP-Gegevensstroombestanden converteren en vervolgens importeren in de functie instellingen voor naleving uitvoeren kunt, moet u downloaden de SCAP-Gegevensstroombestanden uit de National Vulnerability Database (NVD) [downloadpagina](http://nvd.nist.gov/fdcc/download_fdcc.cfm)Website. Kopieer deze vervolgens naar de map waarin u SCAP Extensions hebt geïnstalleerd

Afhankelijk van uw omgeving moet u mogelijk niet alle de SCAP-Gegevensstroombestanden vermeld op de downloadpagina.

De SCAP-gegevensstromen installeren

1. Ga naar de [NVD-website](http://nvd.nist.gov/) voor het identificeren van de SCAP-gegevensstromen die voor uw organisatie vereist zijn.
De SCAP-gegevensstromen gepubliceerd door NIST, worden ingedeeld in meerdere pakketten, worden ook wel _controlelijsten_.

2. Download de SCAP-gegevensstromen van de [NVD-website](http://nvd.nist.gov/home.cfm), deze worden opgeslagen als gecomprimeerde bestanden met de extensie .zip of gemarkeerd als DataStream XML-bestand.

    >[!IMPORTANT] 
    >Er zijn veel SCAP-Gegevensstroombestanden met de .xml-extensie die u uit de NVD downloaden kunt. Echter alleen XML-bestanden die XCCDF bevatten (SCAP1.0 en 1.1) / inhoud DataStream (SCAP1.2) zijn geschikt voor gebruik met de SCAP-extensies.

3. Pak de SCAP gegevensstromen ZIP-bestanden/DataStream XML-bestand dat u hebt gedownload naar de map waarin u SCAP Extensions hebt geïnstalleerd.

## <a name="convert-and-import-the-scap-data-stream-files-using-the-import-scap-content-wizard"></a>Converteren en importeren van de SCAP-Gegevensstroombestanden met behulp van de Wizard importeren SCAP inhoud

Nadat u de SCAP-gegevensstromen, kunt u importeren en de gegevensstromen converteren naar configuratiebasislijnen. De SCAP-gegevensstromen gepubliceerd door NIST, worden ingedeeld in meerdere pakketten. Ga als volgt NIST&#39;s instructies om te controleren welke pakketten te gebruiken in uw omgeving. Er is bijvoorbeeld een afzonderlijk pakket voor elke versie van Windows, een andere versiespecifiek pakket voor de firewallconfiguratie en een bundel voor Internet Explorer 8.0. Gebruik de volgende procedures in deze taak uit te voeren.

### <a name="to-import-the-scap-data-streams-into-configuration-manager"></a>De SCAP-gegevensstromen importeren in Configuration Manager

1. Start de Wizard importeren SCAP inhoud van het lint van de Configuratiebasislijn.

     ![Start de wizard importeren SCAP inhoud van basislijn-lint CI](./media/import-scap-content.png)

2. Selecteer inhoudstype.

      ![Inhoudstype selecteren](./media/import-new-scap-content.png)

3. Selecteer de SCAP-datastream-bestand, XCCDF en CPE woordenlijstbestand of inhoud Oval-bestand.

     ![Selecteer het SCAP datastream-bestand](./media/select-datastream-file.png)

4. Als de datastream SCAP 1.2 selecteren Selecteer vervolgens de benchmark en het profiel voor SCAP 1.x.  Selecteer **volgende** om de inhoud te converteren. Hier ziet u een voortgangsbalk weergegeven.

      ![Selecteer de benchmark en het profiel voor SCAP 1.2](./media/select-benchmark-and-profile.png)

5. Bevestig de configuratiegegevens worden geïmporteerd.

      ![Bevestig de configuratie-schermafbeelding](./media/confirm-configuration.png)

6. Klik op**volgende** de configuratiegegevens importeren.

      ![Het importeren voltooien](./media/complete-import.png)

## <a name="alternate-method-convert-and-import-the-scap-data-stream-files-using-the-cmd-line-tool"></a>(Alternatieve methode) Converteren en importeren van de SCAP-Gegevensstroombestanden het cmd-opdrachtregelprogramma

Nadat u de SCAP-gegevensstromen, kunt u het hulpprogramma Microsoft.Sces.ScapToDcm.exe SCAP-gegevensstromen converteren naar instellingen voor naleving compatibele CAB-bestanden. Vervolgens importeren in Configuration Manager de CAB-bestanden. Het hulpprogramma Microsoft.Sces.ScapToDcm.exe converteert de SCAP-gegevensstromen naar configuratie-items en configuratiebasislijnen die u kunt openen met de functie instellingen voor naleving in Configuration Manager. Het hulpprogramma Microsoft.Sces.ScapToDcm.exe converteert de SCAP-gegevensstromen naar XML-manifesten. Deze worden vervolgens de XML-manifesten verpakt in een CAB-bestand dat u in Configuration Manager kunt importeren.

De SCAP-gegevensstromen gepubliceerd door NIST, worden ingedeeld in meerdere pakketten. Ga als volgt NIST&#39;s instructies om te controleren welke pakketten te gebruiken in uw omgeving. Er is bijvoorbeeld een afzonderlijk pakket voor elke versie van Windows, een andere versiespecifiek pakket voor de firewallconfiguratie en een bundel voor Internet Explorer 8.0. Gebruik de volgende procedures in deze taak uit te voeren.





## <a name="to-import-the-scap-data-streams-into-configuration-manager"></a>De SCAP-gegevensstromen importeren in Configuration Manager

1. Converteer de SCAP-gegevensstromen naar een compatibele CAB-bestand van instellingen voor naleving.
2. Importeer het .cab-bestand naar Configuration Manager.

### <a name="convert-the-scap-data-streams-into-compliance-settings-compliant-cab-files"></a>De SCAP-gegevensstromen converteren naar naleving instellingen compatibele CAB-bestanden

Voordat u kunt analyseren en beoordelen van de compatibiliteit van uw systemen, moet u de SCAP-gegevensstromen in XML-indeling converteren naar XML-manifesten die compatibel met de instellingen voor naleving configuratie-items en configuratiebasislijnen zijn. Het hulpprogramma Microsoft.Sces.ScapToDcm.exe converteert de SCAP-gegevensstromen naar XML-manifesten. Deze worden vervolgens de XML-manifesten verpakt in een CAB-bestand dat u later naar Configuration Manager kunt importeren.

#### <a name="to-convert-the-scap-data-streams-into-compliance-settings-compliant-cab-files-using-the-microsoftscesscaptodcmexe-tool"></a>**De SCAP-gegevensstromen converteren naar instellingen voor naleving compatibele CAB-bestanden met het hulpprogramma Microsoft.Sces.ScapToDcm.exe**

Bij de opdrachtprompt, gaat u naar AdminConsole\Bin map Microsoft.Sces.ScapToDcm.exe voor het genereren van een compatibiliteitsinstellingen compatibele CAB-bestand en importeer ze in de Configuration Manager-site.

   >[!NOTE] 
   > Uw account moet lezen/schrijven machtigingen hebben voor de map voor uitvoer

**Voor SCAP 1.0/1.1-inhoud (XCCDF XML-bestand, zoals USGCB- en DISA-inhoud):**

 Microsoft.Sces.ScapToDcm.exe xccdf &lt;xccdf.xml&gt; - cpe &lt;cpe.xml&gt; -out &lt;outputFolder&gt; [-benchmark of het profiel selecteren] [-Meld LogFileName]

   >[!NOTE] 
   >Als u&#39;t de benchmark of het profiel opgeven met behulp van de parameter, selecteer vervolgens het hulpprogramma een DCM-cab voor elke benchmark in het inhoudsbestand wordt gegenereerd.

**Voor SCAP1.2-inhoud (DataStream XML-bestand, zoals de meest recente USGCB-inhoud-):**

Microsoft.Sces.ScapToDcm.exe – scap &lt;scapdatastreamfile.xml&gt; -out &lt;outputFolder&gt; [-benchmark-datastream-profiel selecteren] [-Meld LogFileName]

   >[!NOTE] 
   > Als u&#39;t geeft de datastream, de benchmark of het profiel met behulp van de – Selecteer deze optie parameter en het hulpprogramma een DCM-cab voor elke benchmark in het inhoudsbestand wordt gegenereerd.

**Voor één OVAL-bestand met externe variabelen:**

Microsoft.Sces.ScapToDcm.exe – oval &lt;singleOvalFile.xml&gt; [-variabele &lt;externalVariableFile.xml&gt;]-out &lt;outputFolder&gt; [-Meld LogFileName]

   >[!NOTE] 
   > Als er meerdere waarden voor een variabele in het bestand met externe variabelen, klikt u vervolgens het hulpprogramma Microsoft.Sces.ScapToDcm.exe wordt de waarden worden behandeld als een matrix voor deze variabele.



#### <a name="microsoftscesscaptodcmexe-command-line-parameters"></a>Microsoft.Sces.ScapToDcm.exe. Opdrachtregelparameters

| **Parameter** | **Gebruik** | **Vereist** |
| --- | --- | --- |
| -scap [scap-gegevenstroombestand] | Het SCAP-gegevensstroombestand opgeven | Ja (voor SCAP 1.2-gegevensstroom, wederzijds uitsluitend met xccdf en -oval / - variable) |
| -xccdf [xccdf-bestand] | Geef het XCCDF-bestand | Ja (voor SCAP 1.0/1.1 XCCDF, wederzijds uitsluitend met-scap en -oval / - variable) |
| -cpe [cpe-bestand] | Geef het CPE-bestand | Ja (voor SCAP 1.0/1.1 XCCDF, wederzijds uitsluitend met-scap en -oval / - variable) |
| -oval [oval-bestand] | Geef het OVAL-bestand | Ja (voor een zelfstandig OVAL-bestand, wederzijds uitsluitend met xccdf en scap) |
| -variabele [oval bestand met externe variabelen] | Geef het OVAL bestand met externe variabelen | Er is geen (optioneel voor een zelfstandig OVAL-bestand wanneer er een OVAL bestand met externe variabelen, wederzijds uitsluitend met xccdf en scap) |
| -Selecteer [xccdfbenchmark /-profiel] | Selecteer XCCDF-benchmark of het profiel op via het SCAP-gegevensstroombestand of het XCCDF-bestand | Nee (We raden deze switch opgeven. Als u niet opgeeft, kunnen het hulpprogramma wordt een CAB-bestand voor alle profielen gegenereerd in alle ingesloten gegevensstromen/benchmarks) |
| -out [uitvoermap] | Geef op waar voor uitvoer van het DCM cab-bestand | Nee (als dit niet wordt opgegeven, vermeldt het hulpprogramma alleen de inhoud zonder conversie) |
| -log [logboekbestand] | Geef het logboekbestand | Nee (als dit niet is opgegeven, wordt het logboek wordt geschreven naar Microsoft.Sces.ScapToDcm.log-bestand) |
| -help / -? | Hulpprogrammagebruik afdrukken | Nee |





#### <a name="the-following-command-lines-are-samples-for-the-microsoftscesscaptodcmexe-tool"></a>De volgende opdrachtregels enkele voorbeelden voor het hulpprogramma Microsoft.Sces.ScapToDcm.exe:

**SCAP1.2-inhoud:**

  Microsoft.Sces.ScapToDcm.exe –scap scap\_gov.nist\_USTCB-ie8.xml –out .\mytestfolder –select mySCAPDataStreamID/myBenchMarkID/myProfileID

**SCAP1.0/1.1-inhoud:**

   Microsoft.Sces.ScapToDcm.exe–xccdf scap\_gov.nist\_Test-WinXP\_xccdf.xml –cpe scap\_gov.nist\_Test-WinXP\_cpe.xml –out .\mytestfolder –select XCCDFBenchmarkID/MyProfileID

**OVAL SCAP-inhoud:**

  Microsoft.Sces.ScapToDcm.exe – oval myOvalFile.xml – variabele myOvalExternalVariableFile.xml – uit. \mytestfolder

**De volgende uitvoer is een voorbeeld van het hulpprogramma Microsoft.Sces.ScapToDcm.exe:**

  Instellingen voor naleving compatibele cab-bestand gemaakt:

  Valideren van het schema van SCAP-gegevensstroombestand C:\24SCAP\BVT\_Test\_gegevens\_Stream.xml

  Het schema van SCAP-gegevensstroombestand C:\24SCAP\BVT met succes valideren\_Test\_gegevens\_Stream.xml

  Proces XCCDF-Benchmark xccdf\_tst.bvt\_benchmark\_Windows-F

  Proces XCCDF-profiel: xccdf\_tst.bvt\_profiel\_versie\_1.0.0.0-BVT profiel #1

  Processen OVAL: scap\_tst.bvt\_comp\_Windows-F-oval.xml

  Met succes voltooid OVAL: scap\_tst.bvt\_comp\_Windows-F-oval.xml

  Processen OVAL: scap\_tst.bvt\_comp\_Windows-F-cpe-oval.xml

  Met succes voltooid OVAL: scap\_tst.bvt\_comp\_Windows-F-cpe-oval.xml proces SCAP-gegevensstroombestand: scap\_tst.bvt\_datastream\_Windows F.zip SCAP-gegevens Stream: [scap\_tst.bvt\_datastream\_Windows F.zip]

  Versie: [1.2]

  Tijdstempel: [24-2/2012]

  Use case: [CONFIGURATION]

  CPE woordenboek: [scap\_tst.bvt\_comp\_Windows-F-cpe-dictionary.xml]

  OVAL: Productnaam [Windows-F-cpe-oval.xml]: [National Institute of Standards and Technology]

  Productversie:]

  Schemaversie: [5.3]

  Tijdstempel: [24-2/2012]

  XCCDF-Benchmark: [xccdf\_tst.bvt\_benchmark\_Windows-F]

  Versie: Update [v1.0.0.0]: [http://usgcb.nist.gov]

  Tijdstempel: [24-2/2012]

  Status: [geaccepteerd]

  Statusdatum: [24-2/2012]

  Titel: [geselecteerd nieuwe BVT voor SCAP 1.2]

 Beschrijving: [Mijn beschrijving]

  XCCDF-profiel: [xccdf\_tst.bvt\_profiel\_versie\_1.0.0.0]
 
  OVAL:              [Windows-F-oval.xml]

   Naam van het product: [scaptool]

   Productversie:]

   Schemaversie: [5.4]

   Tijdstempel: [24-2/2012]

  SCAP naar DCM-conversie starten...

  Verwerking van SCAP-gegevensstroombestand: scap\_tst.bvt\_datastream\_Windows F.zip

  Verwerking van CPE woordenlijst: scap\_tst.bvt\_comp\_Windows-F-cpe-dictionary.xml

  …

  CI basislijn cab-bestand genereren: C:\28\bbt\xccdf\_tst.bvt\_benchmark\_Windows-F[xccdf\_tst.bvt\_profile\_version\_1.0.0.0].cab

  CI basislijn cab-bestand is gegenereerd: C:\28\bbt\xccdf\_tst.bvt\_benchmark\_Windows-F[xccdf\_tst.bvt\_profile\_version\_1.0.0.0].cab

  Heeft geconverteerd XCCDF-profiel: xccdf\_tst.bvt\_profiel\_versie\_1.0.0.0 in DCM-basislijn xccdf\_tst.bvt\_benchmark\_Windows-F [xccdf \_tst.bvt\_profiel\_versie\_1.0.0.0].cab

## <a name="next-step"></a>Volgende stap
> [!div class="nextstepaction"]
> [SCAP-instellingen voor naleving importeren en exporteer de nalevingsresultaten](/sccm/compliance/plan-design/scap/import-scap-compliance-settings)
