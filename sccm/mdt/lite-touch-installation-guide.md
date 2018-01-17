---
title: Snel starten - installatie van Lite Touch
titleSuffix: Microsoft Deployment Toolkit
description: 'Een Quick Start guide voor Microsoft-implementatietoolkit lite touch installatie. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 21bedd68-e925-46e0-a540-df8c0aba2d6c
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 63ddb0c95fe08051dee8e9d003d542307d21b28c
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2018
---
# <a name="quick-start-guide-for-lite-touch-installation"></a>Quick Start Guide voor de installatie van Lite Touch  
 Microsoft Deployment Toolkit (MDT) 2013 biedt technologie voor het implementeren van Windows-besturingssystemen en Microsoft Office. Deze handleiding helpt u snel evalueren MDT 2013 met verkorte, stapsgewijze instructies voor het gebruik ervan voor het installeren van het besturingssysteem Windows 8.1 via Lite Touch Installation (LTI) met opstartbare media (DVD of USB-flashstation). Deze handleiding wordt uitgelegd hoe u het implementatiescenario voor de nieuwe Computer met behulp van een share met MDT 2013 implementatie uitvoert. Het implementatiescenario voor de nieuwe Computer bevat informatie over de implementatie van Windows 8.1 naar een nieuwe computer. Dit scenario wordt ervan uitgegaan dat er is geen gebruikersgegevens of profiel behouden.  

> [!NOTE]     
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

 Bekijk na het evalueren van MDT met behulp van deze handleiding, de rest van de MDT-richtlijnen voor meer informatie over geavanceerde functies van de technologie.  

## <a name="prerequisites"></a>Vereisten  
 De omgeving moet voldoen aan de volgende software- en configuratievereisten voor het implementeren van besturingssystemen en toepassingen met MDT.  

### <a name="required-software"></a>Vereiste Software  
 De volgende software is vereist voor het voltooien van deze handleiding:  

-   Windows 8.1  

     Als u besluit om te voltooien van deze handleiding op een besturingssysteem dan Windows 8.1, moet MDT de volgende elementen:  

    -   Microsoft .NET Framework versie 3.5 met Service Pack 1  

    -   Windows PowerShell™ versie 2.0  

     Windows 8.1 omvat de volgende functies.  

-   Windows Assessment and Deployment Kit (Windows ADK) voor Windows 8.1  

-   Netwerkservices, met inbegrip van Domain Name System en Dynamic Host Configuration Protocol  

> [!NOTE]   
>  De Taaksequencer gebruikt voor implementaties van MDT is vereist dat het maken van globale Object recht worden toegewezen aan de referenties die worden gebruikt voor toegang tot en het uitvoeren van de Workbench-implementatie en het implementatieproces. Dit recht is normaal gesproken beschikbaar voor accounts met machtigingen op Administrator-niveau (tenzij expliciet worden verwijderd). Ook de beveiliging gespecialiseerde – beveiligingsprofiel beperkte functionaliteit (SSLF) Hiermee verwijdert u het recht globale objecttoegang maken en moet niet worden toegepast op computers wordt geïmplementeerd met MDT totdat de MDT-proces voltooid is.  

### <a name="computer-configuration"></a>Computerconfiguratie  
 Instellen van de computers die worden vermeld in de volgende tabel voor het voltooien van deze handleiding. Deze computers kunnen zijn voor fysieke computers of virtuele machines (VM's) met de systeembronnen die is aangewezen.  


|**Computernaam**|**Beschrijving**|  
|-|-|  
|WDG-MDT-01|Deze computer wordt uitgevoerd van de MDT- en Windows 8.1 en is geïnstalleerd in een domein met de naam *mdt2013.corp.woodgrovebank.com* met de naam van een network basic input/output system (NetBIOS) van *MDT2013*. De resources van de computer zijn:<br /><br /> -Processor van 1,4 gigahertz (GHz) of sneller uitgevoerd.<br />-1 gigabyte (GB) of meer fysiek geheugen.<br />-Er wordt één schijfpartitie met 16 GB of meer schijfruimte beschikbaar die de station C-partitie fungeren zal.<br />-Een CD-ROM of dvd-station dat wordt toegewezen de letter station D.|  
|WDG-REF-01|Dit is de referentiecomputer en er is geen huidige besturingssysteem wordt uitgevoerd. De resources van de computer zijn:<br /><br /> -Processor van 1,4 GHz of sneller uitgevoerd.<br />-1 GB of meer fysiek geheugen.<br />-16 GB of meer van de beschikbare schijfruimte.|  
|WDG-CLI-01|Dit is de doelcomputer en er is geen huidige besturingssysteem wordt uitgevoerd. De resources van de computer zijn:<br /><br /> -Processor van 1,4 GHz of sneller uitgevoerd.<br />-1 GB of meer fysiek geheugen.<br />-16 GB of meer van de beschikbare schijfruimte.|  

> [!NOTE]   
>  Deze handleiding wordt ervan uitgegaan dat u MDT op 64-bits (x 64) fysieke of virtuele computers evalueert. Als de evaluatie MDT op 32-bits (x 86) platforms, downloaden en installeren de x86-edities van MDT en de onderdelen die in deze handleiding worden beschreven.  

## <a name="step-1-obtain-the-required-software"></a>Stap 1: De vereiste Software verkrijgen  
 Deze handleiding wordt ervan uitgegaan dat de 64-bits versie van Windows 8.1 is geïnstalleerd op een computer met de naam *MDT-01-WDG*. Als de computer die u gebruikt een andere naam heeft, vervangen door de naam van de computer voor *MDT-01-WDG*.  

> [!NOTE]   
>  Deze sectie wordt ervan uitgegaan dat u een nieuwe infrastructuur voor MDT maakt.  

 De volgende software is vereist voor het uitvoeren van implementaties van LTI:  

-   MDT 2013  

-   Windows ADK voor Windows 8.1  

-   Windows 8.1 distributiebestanden  

-   Apparaatstuurprogramma's vereist zijn voor de doelcomputer, WDG-CLI-01  

-   Apparaatstuurprogramma's vereist zijn voor de referentiecomputer, WDG-REF-01  

## <a name="step-2-prepare-the-mdt-environment"></a>Stap 2: De MDT-omgeving voorbereiden  
 In deze stap bereidt u de MDT-environment voorafgaand aan de referentiecomputer maken en implementeren van een vastgelegde installatiekopie van de referentiecomputer op de doelcomputer (WDG-CLI-01).  

 De MDT-omgeving door voorbereiden:  

-   MDT installeren zoals is beschreven in [stap 2-1: MDT installeren](#InstallMDT)  

-   Installatie van Windows ADK, zoals beschreven in [stap 2-2: Windows ADK installeren](#InstallWindowsADK)  

###  <a name="InstallMDT"></a>Stap 2-1: MDT installeren  
 Voor installatie MDT, voert u de volgende stappen uit:  

1.  Dubbelklik op **MicrosoftDeploymentToolkit2013_x64.msi** (voor 64-bits besturingssystemen) of **MicrosoftDeploymentToolkit2013_x86.msi** (voor 32-bits besturingssystemen), en klik vervolgens op **Installeren**.  

     De Microsoft Deployment Toolkit 2013-installatiewizard wordt gestart.  

2.  Voltooi de Microsoft Deployment Toolkit 2013 Setup Wizard met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Welkom bij de Microsoft Deployment Toolkit 2013-installatiewizard**|Klik op **Volgende**.|  
    |**Gebruiksrechtovereenkomst**|Klik op **ik ga akkoord met de voorwaarden in deze gebruiksrechtovereenkomst**, en klik vervolgens op **volgende**.|  
    |**Aangepaste installatie**|Klik op **Volgende**.|  
    |**Gereed voor installatie van Microsoft Deployment Toolkit 2013**|Klik op **Installeren**.|  
    |**Microsoft Deployment Toolkit 2013 installeren**|De voortgang voor het installeren van MDT wordt weergegeven.|  
    |**De Wizard Setup van Microsoft Deployment Toolkit 2013 voltooien**|Klik op **Voltooien**.|  

 De Wizard Setup van Microsoft Deployment Toolkit 2013 is voltooid en MDT is geïnstalleerd op de MDT-01-WDG.  

###  <a name="InstallWindowsADK"></a>Stap 2-2: Windows ADK installeren  
 Als u wilt Windows ADK installeert, moet u de volgende stappen uitvoeren:  

1.  Koppel de distributiebestanden van Windows ADK op een fysieke of virtuele cd-rom-station.  

2.  In Windows Verkenner, Ga naar de hoofdmap van het cd-rom-station en dubbelklik vervolgens op **adksetup.exe**.  

     De Assessment and Deployment Kit-installatiewizard wordt gestart.  

3.  Voltooi de Assessment and Deployment Kit Setup Wizard met behulp van de volgende informatie.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Geef de locatie**|Klik op **Volgende**.|  
    |**Deelnemen aan het programma voor kwaliteitsverbetering (CEIP)**|Klik op **Ja** als u wilt deelnemen aan of **Nee** als dit niet. Klik vervolgens op **volgende**.|  
    |**Gebruiksrechtovereenkomst**|Klik op **accepteren**.|  
    |**Selecteer de functies die u wilt installeren**|Zorg ervoor dat alleen de selectievakjes voor de volgende functies zijn geselecteerd en klik vervolgens op **volgende**:<br /><br /> -Implementatieprogramma 's<br />-Windows voorinstallatieomgeving (Windows PE)<br />-Windows User State Migration Tool **Opmerking:**  MDT is geen andere functies vereist, maar ze kunnen worden geïnstalleerd, indien gewenst.|  
    |**Installeren van functies**|De voortgang voor het installeren van de functies wordt weergegeven.|  
    |**Welkom bij de Assessment and Deployment Kit**|Klik op **Sluiten**.|  

4.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

5.  Sluit alle geopende vensters.  

> [!NOTE]   
>  Na de installatie van Windows ADK, meld u af en meld u vervolgens aan bij de computer zodat de omgevingsvariabele PATH is bijgewerkt met de map % Files%\Windows Imaging.  

## <a name="step-3-configure-mdt-to-create-the-reference-computer"></a>Stap 3: MDT voor het maken van de referentiecomputer configureren  
 Wanneer u de MDT-omgeving hebt voorbereid, maakt u de referentiecomputer. De referentiecomputer is de sjabloon voor het implementeren van installatiekopieën van het nieuwe op de doelcomputers. Configureer deze computer precies zoals de doelcomputers wordt geconfigureerd. U wordt Windows 8.1 implementeren op de referentiecomputer (WDG-REF-01), een installatiekopie van de referentiecomputer en vervolgens implementeert de vastgelegde installatiekopie op de doelcomputer (WDG-CLI-01).  

 MDT voor het maken van een referentiecomputer door configureren:  

-   Maken van een share van de MDT-implementatie, zoals beschreven in [stap 3-1: Maak een MDT-Implementatieshare](#CreateMDTDeployShare)  

-   Bestanden van besturingssysteem toevoegen aan de implementatieshare, zoals beschreven in [stap 3-2: Bestanden van besturingssysteem toevoegen aan de Implementatieshare](#AddOSFilestoDeployShare)  

-   Apparaatstuurprogramma's toevoegen aan de implementatieshare, zoals beschreven in [stap 3-3: Apparaatstuurprogramma's toevoegt aan de Implementatieshare](#AddDriverstoDeployShare)  

-   Maken van een takenreeks voor de referentiecomputer, zoals beschreven in [stap 3 en 4: Een Takenreeks maken voor de referentiecomputer](#CreateTaskSequence)  

-   Controle van het implementatieproces van LTI, zoals beschreven in inschakelen [stap 3-5: Inschakelen van de implementatie van de LTI procesbewaking](#EnableLTIDeployMonitor)  

-   Bijwerken van de implementatieshare, zoals beschreven in [stap 3-6: De Implementatieshare bijwerken](#UpdateDeployShare)  

###  <a name="CreateMDTDeployShare"></a>Stap 3-1: Maak een MDT-Implementatieshare  
 Voordat implementatie beginnen kunt, maakt u MDT-implementatieshare in de implementatie-Workbench. Deze implementatieshare is de opslagplaats voor installatiekopieën van besturingssystemen, taalpakketten, toepassingen, stuurprogramma's en andere software geïmplementeerd op de doelcomputers.  

 **Maken van een implementatieshare in de Workbench-implementatie**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  Ga naar de implementatie Workbench/Implementatieshares in de consolestructuur van de implementatie-Workbench.  

3.  Klik in het deelvenster Acties op **nieuwe Implementatieshares**.  

     De Wizard Nieuwe Deployment Share wordt gestart.  

4.  Voltooi de implementatie van Wizard Nieuwe Share met de volgende gegevens.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Path**|In **implementatie sharepad**, type **C:\DeploymentShare$**, en klik vervolgens op **volgende**.|  
    |**Delen**|Klik op **Volgende**.|  
    |**Beschrijvende naam**|Klik op **Volgende**.|  
    |**Opties**|Klik op **Volgende**.|  
    |**Samenvatting**|Klik op **Volgende**.|  
    |**Progress**|De voortgang voor het maken van de implementatieshare wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De Wizard Nieuw implementatietype is voltooid en de nieuwe implementatieshare: MDT Deployment Share (C:\DeploymentShare$)—appears in het detaildeelvenster.  

###  <a name="AddOSFilestoDeployShare"></a>Stap 3-2: Bestanden van besturingssysteem toevoegen aan de Implementatieshare  
 MDT fungeert als een opslagplaats voor de bestanden van het besturingssysteem geïmplementeerd op de referentiecomputer (WDG-REF-01) en de doelcomputer (WDG-CLI-01). Het besturingssysteem in het knooppunt besturingssystemen in de Workbench-implementatie met de Wizard importeren besturingssysteem toevoegen.  

 **De bestanden van het besturingssysteem Windows 8.1 toevoegen aan de implementatieshare**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Operating systemen.  

3.  Klik in het deelvenster Acties op **importeren besturingssysteem**.  

     De Wizard importeren besturingssysteem wordt gestart.  

4.  Voltooi de Wizard importeren besturingssysteem met behulp van de volgende informatie.    

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Op deze wizardpagina**|**Dit doet**|  
    |**Type besturingssysteem**|Klik op **volledige set van bronbestanden**, en klik vervolgens op **volgende**.|  
    |**Bron**|In **bronmap**, type ***source_path*** (waarbij *source_path* is het volledig gekwalificeerde pad naar de distributiebestanden Windows 8.1), en klik vervolgens op  **Volgende**.|  
    |**Destination**|Klik op **Volgende**.|  
    |**Samenvatting**|Klik op **Volgende**.|  
    |**Progress**|De voortgang voor het importeren van het besturingssysteem wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De Wizard importeren besturingssysteem is voltooid. Windows 8.1 is toegevoegd aan de lijst met besturingssystemen in het deelvenster met details en gekopieerd naar de *deployment_share*\Operating systemen\\*operating_system* map (waarbij  *deployment_share* de gedeelde netwerkmap die u eerder in het proces hebt gemaakt en *operating_system* is de naam van het besturingssysteem die u hebt toegevoegd aan de implementatieshare).  

###  <a name="AddDriverstoDeployShare"></a>Stap 3-3: Apparaatstuurprogramma's toevoegt aan de Implementatieshare  
 Nadat u Windows 8.1 aan de implementatie-Workbench hebt toegevoegd, toevoegen eventuele apparaatstuurprogramma's vereist zijn voor de referentiecomputer (WDG-REF-01) en de doelcomputer (WDG-CLI-01). Deze apparaatstuurprogramma's wordt toegevoegd aan Windows PE en geïmplementeerd met Windows 8.1. Voeg de apparaatstuurprogramma's in het knooppunt Out-of-box stuurprogramma's in de Workbench-implementatie met behulp van de Wizard Nieuw stuurprogramma, die de stuurprogrammabestanden aan de implementatie kopieert delen in Out-of-Box stuurprogramma's\\*device_driver* () waar *device_driver* is de naam van de apparaatstuurprogramma's die u hebt toegevoegd aan de implementatieshare).  

> [!NOTE]   
>  Als de apparaatstuurprogramma's voor de referentiecomputer (WDG-REF-01) en de doelcomputer (WDG-CLI-01) opgenomen in Windows 8.1 zijn, wordt deze stap overslaan en doorgaan met de volgende stap.  

 **De apparaatstuurprogramma's voor de referentie- en doelcomputers computers toevoegen aan de distributieshare**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Out-of-Box stuurprogramma's.  

3.  Klik in het deelvenster Acties op **stuurprogramma's importeren**.  

     De Wizard importeren stuurprogramma wordt gestart.  

4.  Voltooi de Wizard importeren met behulp van de volgende informatie.

    |**Op deze wizardpagina**|**Dit doet**|
    |-|-|  
    |**Specify Directory**|In **stuurprogramma bronmap**, type ***driver_path*** (waarbij *driver_path* is het volledig gekwalificeerde pad naar de map met de apparaatstuurprogramma's), en klik vervolgens op  **Volgende**.|  
    |**Samenvatting**|Klik op **Volgende**.|  
    |Voortgang|De voortgang voor het importeren van apparaatstuurprogramma's wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De Wizard importeren is voltooid. De apparaatstuurprogramma's worden toegevoegd aan de lijst met besturingssystemen in het deelvenster met details en gekopieerd naar de *deployment_share*\Out-of-box stuurprogramma's map (waarbij *deployment_share* is de implementatie u delen gemaakt eerder in het proces).  

###  <a name="CreateTaskSequence"></a>Stap 3 en 4: Een Takenreeks maken voor de referentiecomputer  
 MDT-takenreeksen in het knooppunt Takenreeksen in de Workbench-implementatie met behulp van de Wizard Nieuwe Takenreeks maken. MDT bevat de sjabloon standaard Clienttakenreeks die u gebruiken kunt voor het implementeren van het beoogde besturingssysteem op de referentiecomputer (WDG-REF-01).  

 **Maken van een takenreeks voor het implementeren van de referentiecomputer**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Task reeksen  

3.  Klik in het deelvenster Acties op **nieuwe Takenreeks**.  

     De Wizard Nieuwe Takenreeks wordt gestart.  

4.  Voltooi de Wizard Nieuwe Takenreeks met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Algemene instellingen**|1.  In **volgorde-ID van de taak**, type **WIN8_REFERENCE**.<br />2.  In **takenreeksnaam**, type **Windows 8.1 implementeren naar referentiecomputer**.<br />3.  In **Task sequence opmerkingen**, type **Takenreeks voor het Windows 8.1 implementeren op de referentiecomputer (WDG-REF-01)**.<br />4.  Klik op **Volgende**.|  
    |**Sjabloon selecteren**|In **de volgende taak reeks sjablonen beschikbaar zijn. Selecteer de gateway die u wilt gebruiken als uitgangspunt**, selecteer **standaard Clienttakenreeks**, en klik vervolgens op **volgende**.|  
    |**Besturingssysteem selecteren**|In **de volgende installatiekopieën van besturingssystemen zijn beschikbaar om te worden geïmplementeerd met deze takenreeks**. **Selecteer een te gebruiken**, selecteer **Windows 8.1 *edition***  (waarbij *edition* is de editie van Windows 8.1 toegevoegd aan het knooppunt besturingssystemen in de Implementatie-Workbench), en klik vervolgens op **volgende**.|  
    |**Productcode opgeven**|Klik op **Geef een productcode op dit moment geen**, en klik vervolgens op **volgende**.|  
    |**OS-instellingen**|1.  In **volledige naam**, type **Woodgrove Bank werknemer**.<br /><br /> 2.  In **organisatie**, type **Woodgrove Bank**.<br /><br /> 3.  In **startpagina van Internet Explorer**, type **http://www.woodgrovebank.com**.<br /><br /> 4.  Klik op **Volgende**.|  
    |**Beheerderswachtwoord**|In **beheerderswachtwoord** en **Controleer of de Administrator-wachtwoord**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Samenvatting**|Klik op **Volgende**.|  
    |**Progress**|De voortgang voor het maken van de takenreeks wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De Wizard Takenreeks importeren is voltooid, en de **Windows 8.1 implementeren naar referentiecomputer** takenreeks is toegevoegd aan de lijst van takenreeksen.  

###  <a name="EnableLTIDeployMonitor"></a>Stap 3-5: Inschakelen van de implementatie van de LTI procesbewaking  
 Schakel de bewaking van het implementatieproces LTI vóór de implementatie van de referentiecomputer (WDG-REF-01) met de LTI opstartbare media die u eerder in het proces hebt gemaakt. U bewaken het implementatieproces LTI in het knooppunt controle in de implementatieshare. U inschakelen bewaking op de **bewaking** tabblad in het eigenschappenvenster van de implementatie-share. Later in het proces bewaakt u de LTI-implementatieproces.  

 **Bewaking van het implementatieproces LTI wilt inschakelen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  Ga naar de implementatie Workbench/Implementatieshares in de consolestructuur van de implementatie-Workbench.  

3.  Klik in het detailvenster op **MDT-Implementatieshare (C:\DeploymentShare$)**.  

4.  Klik in het deelvenster Acties op **eigenschappen**  

     De **eigenschappen van de MDT-Implementatieshare (C:\DeploymentShare$)** dialoogvenster wordt geopend.  

5.  In de **eigenschappen MDT Deployment Share (C:\DeploymentShare$)** in het dialoogvenster op de **bewaking** tabblad de **Schakel bewaking voor deze implementatieshare** selectievakje , en klik vervolgens op **toepassen**.  

6.  In de **eigenschappen van de MDT-Implementatieshare (C:\DeploymentShare$)** in het dialoogvenster op de **regels** tabblad, zoals u ziet de **EventService** eigenschap is toegevoegd aan de CustomSettings.ini-bestand en klik vervolgens op **OK**.  

7.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="UpdateDeployShare"></a>Stap 3-6: De Implementatieshare bijwerken  
 Na het configureren van de implementatieshare bijwerken. Bijwerken van de implementatieshare alle MDT-configuratiebestanden bijgewerkt en genereert een aangepaste versie van Windows PE. U kunt de aangepaste versie van Windows PE start de referentiecomputer en implementatie van de LTI te initiëren.  

 **Bijwerken van de implementatieshare in de Workbench-implementatie**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  Ga naar de implementatie Workbench/Implementatieshares in de consolestructuur van de implementatie-Workbench.  

3.  Klik in het detailvenster op **MDT-Implementatieshare (C:\DeploymentShare$)**.  

4.  Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

5.  Voltooi de Wizard Update Deployment Share met de volgende gegevens. Accepteer de standaardwaarden tenzij anders vermeld.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Opties**|Klik op **Volgende**.|  
    |**Samenvatting**|Klik op **Volgende**.|  
    |**Progress**|De voortgang voor het bijwerken van de implementatieshare wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De Workbench-implementatie wordt gestart voor het bijwerken van de implementatieshare MDT Deployment Share (C:\DeploymentShare$). De implementatie-Workbench maakt ook de bestanden LiteTouchPE_x64.iso en LiteTouchPE_x64.wim-bestanden (voor 64-bits doelcomputers) of de bestanden LiteTouchPE_x86.iso en LiteTouchPE_x86.wim (voor 32-bits doelcomputers) in de *deployment_share*Map \Boot (waarbij *deployment_share* de gedeelde netwerkmap gebruikt als de implementatieshare is).  

## <a name="step-4-deploy-windows-81-and-capture-an-image-of-the-reference-computer"></a>Stap 4: Implementeer Windows 8.1 en een installatiekopie van de referentiecomputer  
 Na het maken van de takenreeks voor Windows 8.1 implementeren op de referentiecomputer, het starten van de implementatie van besturingssystemen en de installatiekopie vastleggen vanaf de referentiecomputer de LTI opstartbare media.  

 Windows 8.1 implementeren en een installatiekopie van de referentiecomputer door:  

-   Maken van de LTI opstartbare media, zoals beschreven in [stap 4-1: De LTI opstartbare Media maken](#CreateLTIBootable)  

-   De referentiecomputer beginnen met de LTI opstartbare media en bewaking van het implementatieproces van LTI, zoals beschreven in [stap 4-2: Start de referentiecomputer met de LTI opstartbare Media](#StartRefCompwithLTIBootable)  

###  <a name="CreateLTIBootable"></a>Stap 4-1: De LTI opstartbare Media maken  
 U moet een methode voor het starten van de computer met de aangepaste versie van Windows PE die u hebt gemaakt wanneer u de implementatieshare is bijgewerkt. De implementatie-Workbench maakt u de bestanden LiteTouchPE_x64.iso en LiteTouchPE_x64.wim-bestanden (voor 64-bits doelcomputers) of de bestanden LiteTouchPE_x86.iso en LiteTouchPE_x86.wim (voor 32-bits doelcomputers) in de *deployment_share*Map \Boot (waarbij *deployment_share* de gedeelde netwerkmap gebruikt als de implementatieshare is). Maak de juiste LTI opstartbare media van een van deze installatiekopieën.  

 **De LTI opstartbare media maken**  

1.  In Windows Verkenner, Ga naar C:\DeploymentShare$\Boot.  

2.  Op basis van het type van de computer die wordt gebruikt voor de referentiecomputer (WDG-REF-01), voer een van de volgende taken:  

    -   Als de referentiecomputer een fysieke computer is, maakt u een fysieke CD of DVD van de bestanden LiteTouchPE_x64.iso of LiteTouchPE_x86.iso-bestand.  

    -   Als de referentiecomputer een virtuele machine is, start u de virtuele machine rechtstreeks vanuit het bestand bestanden LiteTouchPE_x64.iso of LiteTouchPE_x86.iso of vanaf een CD of DVD van de bestanden standaard ISO (International Organization).  

###  <a name="StartRefCompwithLTIBootable"></a>Stap 4-2: Start de referentiecomputer met de LTI opstartbare Media  
 Start de referentiecomputer (WDG-REF-01) met de LTI opstartbare media die u eerder in het proces hebt gemaakt. De opstartbare media LTI wordt Windows PE gestart op de referentiecomputer en implementatie start. Windows 8.1 wordt aan het einde van het implementatieproces MDT geïmplementeerd op de referentiecomputer.  

> [!NOTE]   
>  U kunt een 32-bits opstartinstallatiekopie gebruiken voor het implementeren van zowel 32-bits en 64-bits besturingssystemen; een 64-bits opstartinstallatiekopie kan echter alleen worden gebruikt om 64-bits besturingssystemen te implementeren.  

 Het proces kan ook door de doelcomputer vanaf in Windows Deployment Services worden geïnitieerd. Zie voor meer informatie de sectie 'Voorbereiden van Windows Deployment Services', in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

 **Starten van de referentiecomputer met de LTI opstartbare media**  

1.  WDG-REF-01 beginnen met de LTI opstartbare media die u eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Windows-implementatie wordt gestart.  

2.  Voltooi de Wizard implementatie van Windows met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Welcome**|Klik op **de Wizard voor het installeren van een nieuw besturingssysteem uitvoeren**.|  
    |**Referenties**|1.  In **gebruikersnaam**, type **beheerder**.<br />2.  In **wachtwoord**, type  **P@ssw0rd** .<br />3.  In **domein**, type **MDT2013**.<br />4.  Klik op **OK**.|  
    |**Takenreeks**|Klik op **Windows 8.1 implementeren naar referentiecomputer**, en klik vervolgens op **volgende**.|  
    |**Computerdetails**|In **computernaam**, **WDG-REF-01 Typ**, en klik vervolgens op **volgende**.|  
    |**Verplaatsen van gegevens en instellingen**|Klik op **Volgende**.|  
    |**User Data (herstel)**|Klik op **Volgende**.|  
    |**De landinstelling en -tijd**|Klik op **Volgende**.|  
    |**Installatiekopie vastleggen**|Klik op **installatiekopie van een van deze referentiecomputer vastleggen**, en klik vervolgens op **volgende**.|  
    |**Gereed**|1.  Klik op **Details** om weer te geven van de informatie in de wizard.<br />2.  Klik op **begint**.|  

 **Voor het controleren van het implementatieproces van de referentie-computer de volgende stappen op de MDT-01-WDG**  

1.  Klik op WDG-MDT-01 **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Monitoring.  

3.  In het deelvenster met details weergeven het implementatieproces voor **WDG-REF-01**.  

4.  Klik in het deelvenster Acties periodiek op **vernieuwen**.  

     De status van het implementatieproces is bijgewerkt in het detaildeelvenster.  

     Blijven volgen het implementatieproces totdat het proces voltooid is.  

5.  Klik in het detailvenster op **WDG-REF-01**.  

6.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **WDG-REF-01-eigenschappen** in het dialoogvenster wordt weergegeven.  

7.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster op de **identiteit** tabblad, de controle-informatie gegeven over het implementatieproces, zoals beschreven in de volgende tabel weergeven.

    |**Informatie**|**Beschrijving**|  
    |-|-|  
    |**ID**|De unieke id voor de computer wordt geïmplementeerd.|  
    |**Computernaam**|De naam van de computer wordt geïmplementeerd.|  
    |**Implementatiestatus**|De huidige status van de computer wordt geïmplementeerd; de status kan een van de volgende zijn:<br /><br /> -   **Met**. De takenreeks is in orde en wordt uitgevoerd.<br />-   **Kan geen**. De takenreeks is mislukt en het implementatieproces is mislukt.<br />-   **Voltooid**. De takenreeks is voltooid.<br />-   **Niet-reagerende**. De takenreeks heeft de status ervan niet bijgewerkt in de afgelopen vier uur en wordt ervan uitgegaan dat niet meer reageert.|  
    |**Stap**|De huidige takenreeksstap wordt uitgevoerd.|  
    |**Progress**|De algemene voortgang van de takenreeks wordt uitgevoerd. De voortgangsbalk geeft aan hoeveel takenreeksstappen van het totale aantal met takenreeksstappen zijn uitgevoerd.|  
    |**Start**|De tijd die het implementatieproces gestart.|  
    |**End**|De tijd die het implementatieproces is beëindigd.|  
    |**Verstreken**|Hoe lang het implementatieproces actief is geweest of duurde om uit te voeren als de implementatie is voltooid.|  
    |**Fouten**|Het aantal fouten zijn opgetreden tijdens het implementatieproces.|  
    |**Waarschuwingen**|Het aantal waarschuwingen aangetroffen tijdens het implementatieproces.|  
    |**Extern bureaublad**|Deze knop kunt u extern bureaublad verbinding te maken met de computer wordt geïmplementeerd met behulp van de functie Extern bureaublad van Windows. Deze methode wordt ervan uitgegaan dat:<br /><br /> -Het beoogde besturingssysteem wordt uitgevoerd en ondersteuning voor externe bureaublad is ingeschakeld<br />-   **mstsc.exe** zich in het pad **Opmerking:**  Deze knop wordt altijd weergegeven, maar mogelijk niet tot stand brengen van een extern bureaublad-sessiehost als de bewaakte computer wordt uitgevoerd Windows PE, installatie van het beoogde besturingssysteem niet is voltooid of beschikt niet over de functie Extern bureaublad is ingeschakeld.|  
    |**VM-verbinding**|Deze knop kunt u extern bureaublad verbinding te maken met een virtuele machine in HyperV® uitgevoerd. Deze methode wordt ervan uitgegaan dat:<br /><br /> -De implementatie wordt uitgevoerd op een virtuele machine waarop Hyper-V<br />-   **vmconnect.exe** bevindt zich in de map %ProgramFiles%\Hyper-V **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat de onderdelen voor Hyper-V-integratie worden uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**DaRT extern beheer**|Deze knop kunt u tot stand brengen van een sessie voor extern beheer met de viewer voor extern-functie in de Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Deze methode wordt ervan uitgegaan dat:<br /><br /> -DaRT is geïmplementeerd op de doelcomputer en wordt momenteel uitgevoerd.<br />-   **DartRemoteViewer.exe** bevindt zich in de map %ProgramFiles%\Microsoft DaRT 7\v7 **Opmerking:**  Deze knop wordt weergegeven wanneer ZTIGather.wsf detecteert dat DaRT wordt uitgevoerd op de bewaakte computer. Anders wordt is deze knop alleen zichtbaar.|  
    |**Deze informatie om de tien seconden automatisch worden vernieuwd**|Selectievakje die bepaalt of de informatie in het dialoogvenster automatisch wordt vernieuwd. Als het selectievakje is:<br /><br /> -Geselecteerd, de gegevens worden vernieuwd elke 10 seconden<br />-Uitgeschakeld, de informatie is niet automatisch vernieuwd en moet handmatig vernieuwen met behulp van de **nu vernieuwen** knop|  
    |**Nu vernieuwen**|Deze knop wordt onmiddellijk vernieuwd voor de informatie die wordt weergegeven in het dialoogvenster.|  

8.  In de **WDG-REF-01-eigenschappen** in het dialoogvenster, klikt u op **OK**.  

9. Sluit de implementatie-Workbench.  

 Voor het voltooien van het implementatieproces van de referentie-computer, moet u de volgende stappen uitvoeren op WDG-REF-01:  

1.  Op WDG-REF-01, in de **implementatieoverzicht** in het dialoogvenster, klikt u op **Details**.  

     Als er fouten of waarschuwingen optreden, bekijk de fouten of waarschuwingen en diagnostische informatie vastgelegd.  

2.  In de **implementatieoverzicht** in het dialoogvenster, klikt u op **voltooien**.  

 Windows 8.1 wordt nu geïnstalleerd op de referentiecomputer en de vastgelegde Windows Imaging Format (WIM)-bestand van de referentiecomputer (WIN7_REFERENCE.wim) wordt opgeslagen in de *deployment_share*\Captures map (waarbij  *deployment_share* de gedeelde map als share van de implementatie gebruikt). Als er fouten of waarschuwingen optreden, Raadpleeg het document MDT *probleemoplossing verwijzing*.  

## <a name="step-5-configure-mdt-to-deploy-windows-81-to-the-target-computer"></a>Stap 5: MDT om Windows 8.1 implementeren met de doelcomputer configureren  
 Wanneer u een installatiekopie van de referentiecomputer (MDT-REF-01) hebt gemaakt, kunt u dit naar de doelcomputer (MDT-CLI-01) implementeren. U kunt de vastgelegde installatiekopie importeren in de Workbench-implementatie met de Wizard importeren besturingssysteem. Maak vervolgens een takenreeks voor het implementeren van de vastgelegde installatiekopie op de doelcomputer.  

 MDT om Windows 8.1 implementeren met de doelcomputer door configureren:  

-   De vastgelegde installatiekopie van de referentiecomputer toevoegen aan de implementatie-Workbench, zoals beschreven in [stap 5-1: De vastgelegde installatiekopie van de referentiecomputer toevoegen aan de implementatie-Workbench](#AddCapturedImagetoDeployWB)  

-   Maken van een takenreeks voor de doelcomputer, zoals beschreven in [stap 5 2: Een Takenreeks maken voor de doelcomputer](#CreateTaskSequenceforTarget)  

###  <a name="AddCapturedImagetoDeployWB"></a>Stap 5-1: De vastgelegde installatiekopie van de referentiecomputer toevoegen aan de implementatie-Workbench  
 Als u wilt implementeren de vastgelegde installatiekopie van de referentiecomputer op de doelcomputer, toevoegen de vastgelegde installatiekopie aan de lijst met besturingssystemen in het knooppunt besturingssystemen in de implementatie-Workbench. De Wizard importeren besturingssysteem kopieert de bestanden van het besturingssysteem naar de *deployment_share*\Operating systemen\\*operating_system* map (waarbij *deployment_ delen* is de implementatiesharemap eerder in het proces hebt gemaakt en *operating_system* is de naam van het besturingssysteem die is toegevoegd aan de implementatieshare).  

 **De vastgelegde installatiekopie van de referentiecomputer toevoegen aan de implementatie-Workbench**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Operating systemen.  

3.  Klik in het deelvenster Acties op **importeren besturingssysteem**.  

     De Wizard importeren besturingssysteem wordt gestart.  

4.  Voltooi de Wizard importeren besturingssysteem met behulp van de informatie in de volgende tabel.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Type besturingssysteem**|Klik op **bestand met aangepaste installatiekopie**, en klik vervolgens op **volgende**.|  
    |**Afbeelding**|In **bronbestand**, type **C:\DeploymentShare$\Captures\WIN8_REFERENCE.wim**, en klik vervolgens op **volgende**.|  
    |**Setup**|Klik op **Volgende**.|  
    |**Destination**|Klik op **Volgende**.|  
    |**Samenvatting**|Klik op **Volgende**.|  
    |**Progress**|De voortgang voor het importeren van het besturingssysteem wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

     De Wizard importeren besturingssysteem is voltooid. De vastgelegde installatiekopie van het besturingssysteem van de referentie-computer (WDG-REF-01) is toegevoegd aan de lijst met besturingssystemen in het deelvenster met details en wordt gekopieerd naar de *deployment_share*\Operating systemen\\  *operating_system* map (waarbij *deployment_share* is de implementatiesharemap eerder in het proces hebt gemaakt en *operating_system* is de naam van het besturingssysteem systeem toegevoegd aan de implementatieshare).  

5.  Sluit alle geopende vensters en dialoogvensters.  

###  <a name="CreateTaskSequenceforTarget"></a>Stap 5-2: Een Takenreeks maken voor de doelcomputer  
 Maak een MDT-takenreeks voor de doelcomputer in het knooppunt Takenreeksen in de Workbench-implementatie met behulp van de Wizard Nieuwe Takenreeks. Deze takenreeks wordt gebruikt voor het implementeren van de vastgelegde installatiekopie van de referentiecomputer op de doelcomputer.  

 **Maken van een takenreeks voor het implementeren van de vastgelegde installatiekopie op de doelcomputer**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Punt **naar Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:DeploymentShare$) / Takenreeksen.  

3.  Klik in het deelvenster Acties op **nieuwe Takenreeks**.  

     De Wizard Nieuwe Takenreeks wordt gestart.  

4.  Voltooi de Wizard Nieuwe Takenreeks met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Algemene instellingen**|1.  In **volgorde-ID van de taak**, type **WIN8_TARGET**.<br />2.  In **takenreeksnaam**, type **vastgelegde installatiekopie implementeren naar de doelcomputer**.<br />3.  In **Task sequence opmerkingen**, type **Takenreeks voor de vastgelegde installatiekopie van Windows 8.1 van referentiecomputer (WDG-REF-01) naar de doelcomputer (WDG-CLI-01)**.<br />4.  Klik op **Volgende**.|  
    |**Sjabloon selecteren**|In **de volgende taak reeks sjablonen zijn beschikbaar**. **Selecteer de gateway die u wilt gebruiken als uitgangspunt**, selecteer standaard **Clienttakenreeks**, en klik vervolgens op **volgende**.|  
    |**Besturingssysteem selecteren**|In **de volgende installatiekopieën van besturingssystemen zijn beschikbaar om te worden geïmplementeerd met deze takenreeks**. **Selecteer een te gebruiken**, selecteer **WIN8_RERENCEDrive in 'WIN8_REFERENCE\WIN8_REFERENCE.wim'**, en klik vervolgens op **volgende**.|  
    |**Productcode opgeven**|Klik op **Geef een productcode op dit moment geen**, en klik vervolgens op **volgende**.|  
    |**OS-instellingen**|1.  In **volledige naam**, type **Woodgrove Bank werknemer**.<br />2.  In **organisatie**, type **Woodgrove Bank**.<br />3.  In **startpagina van Internet Explorer**, type **http://www.woodgrovebank.com**.<br />4.  Klik op **Volgende**.|  
    |**Beheerderswachtwoord**|In **beheerderswachtwoord** en **Controleer of de Administrator-wachtwoord**, type  **P@ssw0rd** , en klik vervolgens op **volgende**.|  
    |**Samenvatting**|Klik op **Volgende**.|  
    |**Progress**|De voortgang voor het maken van de takenreeks wordt weergegeven.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

     De Wizard Takenreeks importeren is voltooid, en de **WIN8_TARGET** takenreeks is toegevoegd aan de lijst van takenreeksen.  

5.  Sluit alle geopende vensters en dialoogvensters.  

## <a name="step-6-deploy-the-captured-image-of-the-reference-computer-to-the-target-computer"></a>Stap 6: De vastgelegde installatiekopie van de referentiecomputer implementeren op de doelcomputer  
 Wanneer u hebt een installatiekopie van de referentiecomputer vastgelegd en gemaakt en de juiste takenreeks geconfigureerd, moet u de vastgelegde installatiekopie implementeren. Configureer MDT om op te geven van alle benodigde configuratie-instellingen voor de implementatie van de doelcomputer. De installatiekopie van de referentiecomputer met Windows 8.1 is na het initiëren van het implementatieproces automatisch geïmplementeerd op de doelcomputer en geconfigureerd met de instellingen die zijn gedefinieerd.  

 De vastgelegde installatiekopie van de referentiecomputer implementeren op de doelcomputer door:  

-   De doelcomputer wordt gestart met de LTI opstartbare media en controleren van het implementatieproces van LTI, zoals beschreven in [stap 6-1: Start de doelcomputer met de LTI opstartbare Media](#StartTargetwithLTIBootable)  

###  <a name="StartTargetwithLTIBootable"></a>Stap 6-1: Start de doelcomputer met de LTI opstartbare Media  
 Start de doelcomputer (WDG-CLI-01) met de LTI opstartbare media die u eerder in het proces hebt gemaakt. Deze CD wordt Windows PE gestart op de doelcomputer en implementatie start. Windows 8.1 wordt aan het einde van het proces geïmplementeerd op de doelcomputer.  

> [!NOTE]
>  Starten van de doelcomputer vanaf de Windows Deployment Services kunt u ook implementatie initiëren. Zie voor meer informatie het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

 **Starten van de doelcomputer met de LTI opstartbare media**  

1.  CLI-01-WDG beginnen met de LTI opstartbare media die u eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Windows-implementatie wordt gestart.  

2.  Voltooi de Wizard implementatie van Windows met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.   

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Welcome**|Klik op **de Wizard voor het installeren van een nieuw besturingssysteem uitvoeren**.|  
    |**Referenties**|1.  In **gebruikersnaam**, type **beheerder**.<br />2.  In **wachtwoord**, type  **P@ssw0rd** .<br />3.  In **domein**, type **MDT2013**.<br />4.  Klik op **OK**.|  
    |**Takenreeks**|Klik op **vastgelegde installatiekopie implementeren naar de doelcomputer**, en klik vervolgens op **volgende**.|  
    |**Computerdetails**|In **computernaam**, type **WDG-CLI-01**, en klik vervolgens op **volgende**.|  
    |**Verplaatsen van gegevens en instellingen**|Klik op **Volgende**.|  
    |**User Data (herstel)**|Klik op **Volgende**.|  
    |**De landinstelling en -tijd**|**Klik op volgende**.|  
    |**Installatiekopie vastleggen**|Klik op **Volgende**.|  
    |**BitLocker**|Klik op **Volgende**.|  
    |**Gereed**|1.  Klik op **Details** om weer te geven van de informatie in de wizard.<br />2.  Klik op **begint**.|  

 De wizard wordt gestart, en de implementatie van het besturingssysteem wordt gestart.  

 **Voor het controleren van het implementatieproces van de doel-computer de volgende stappen op de MDT-01-WDG**  

1.  Klik op WDG-MDT-01 **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/implementatie Shares/MDT-Implementatieshare (C:\DeploymentShare$)/Monitoring  

3.  Klik in het deelvenster Acties periodiek op **vernieuwen**.  

4.  In het deelvenster met details weergeven het implementatieproces voor **CLI-01-WDG**.  

5.  Klik in het deelvenster Acties periodiek op **vernieuwen**.  

     De status van het implementatieproces is bijgewerkt in het detaildeelvenster. Blijven volgen het implementatieproces totdat het proces voltooid is.  

6.  Sluit de implementatie-Workbench.  

 **Voor het voltooien van het implementatieproces van de doel-computer, kunt u de volgende stappen uitvoeren op WDG-CLI-01**  

1.  Op WDG-CLI-01, in de **implementatieoverzicht** in het dialoogvenster, klikt u op **Details**.  

     Als er fouten of waarschuwingen optreden, bekijk de fouten of waarschuwingen en diagnostische informatie vastgelegd.  

2.  In de **implementatieoverzicht** in het dialoogvenster, klikt u op **voltooien**.  

 Aan het einde van het implementatieproces van de MDT de **implementatieoverzicht** dialoogvenster wordt weergegeven. De installatiekopie van Windows 8.1 vastgelegd vanaf de referentiecomputer is nu geïnstalleerd op de doelcomputer. Als er fouten of waarschuwingen optreden, Raadpleeg het document MDT *probleemoplossing verwijzing*.
