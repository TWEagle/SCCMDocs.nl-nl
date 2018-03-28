---
title: Gebruiker gebaseerde installatie
titleSuffix: Microsoft Deployment Toolkit
description: 'Handleiding voor ontwikkelaars voor gebruiker gebaseerde installatie van Microsoft Deployment Toolkit 2013. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: a2b3a3a0-7b81-4191-b1f9-c618e59347c3
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 434178f100c32a4188ecf5283066f9332035f761
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/27/2018
---
# <a name="user-driven-installation---developers-guide"></a>Gebruiker gestuurd installatie - handleiding voor ontwikkelaars
Gebruiker gebaseerde installatie UDI (User) helpt te vereenvoudigen de implementatie van Windows® clientbesturingssystemen, zoals Windows 8.1, op computers met behulp van de functie van het besturingssysteem-implementatie (OSD) in Microsoft® System Center 2012 R2 Configuration Manager. UDI maakt deel uit van de Microsoft Deployment Toolkit (MDT).  

## <a name="introduction"></a>Inleiding  
 Normaal gesproken moet u de benodigde informatie voor het implementeren van het besturingssysteem opgeven bij het implementeren van besturingssystemen met behulp van de OSD-functie. De informatie die is geconfigureerd in configuratiebestanden of in databases (zoals het CustomSettings.ini-bestand of de MDT-database [MDT DB]). Voordat u de implementatie kunt starten, moet u alle configuratie-instellingen opgeven.  

 UDI biedt een wizard-gebaseerde interface waarmee u configuratie-informatie onmiddellijk voordat de implementatie worden uitgevoerd. Dit gedrag kunt u algemene OSD-takenreeksen maken en geef vervolgens de computer-specifieke informatie op het moment van implementatie, die meer flexibiliteit in het implementatieproces biedt.  

### <a name="target-audience"></a>Doelgroep  
 Deze handleiding is geschreven voor de ontwikkelaars die het maken van aangepaste wizardpagina's voor de Wizard UDI en aangepaste wizard pagina editors voor de waarde van de Wizard UDI. Deze handleiding wordt ervan uitgegaan dat u bekend bent met de ontwikkeling van Windows-toepassingen met behulp van:  

-   C++, die wordt gebruikt voor het maken van aangepaste wizardpagina 's  

-   Microsoft .NET Framework die wordt gebruikt voor het maken van aangepaste wizardpagina editors  

-   Windows Presentation Foundation (WPF), die wordt gebruikt voor het maken van aangepaste wizardpagina editors  

-   Talen die WPF ondersteunt, zoals C#, C++ of Microsoft Visual Basic® .NET, die worden gebruikt voor het maken van aangepaste wizard pagina editors  

### <a name="about-this-guide"></a>Over deze handleiding  
 Deze handleiding bevat de benodigde informatie waarmee u kunt UTI aanpassen voor uw organisatie. Administratieve of operationele onderwerpen, zoals het installeren van de MDT (waaronder UDI), UDI voor het implementeren van besturingssystemen en toepassingen configureren of uitvoeren met de Wizard UDI implementaties wordt niet door deze handleiding worden beschreven. Zie voor meer informatie over deze onderwerpen in de onderwerpen UDI in *met behulp van de Microsoft Deployment Toolkit*, die deel uitmaakt van de MDT.  

## <a name="udi-development-overview"></a>Overzicht van UDI voor ontwikkelaars  
 UDI ontwikkeling kunt dat u de functies waarmee UDI uitbreiden. UDI ontwikkeling is normaal gesproken vereist als u wenst te verzamelen van aanvullende informatie die het implementatieproces UDI verbruikt. Deze aanvullende informatie wordt meestal opgeslagen als in een takenreeks UDI in Configuration Manager takenreeksstappen, lezen takenreeksvariabelen.  

### <a name="udi-architecture"></a>UDI-architectuur  
 Het doel op hoog niveau van UDI ontwikkeling is het maken van aangepaste wizardpagina's die kunnen worden weergegeven in de Wizard UDI. U kunt de bestaande functies van UDI om te voldoen aan de zakelijke en technische vereisten van uw organisatie uitbreiden door het maken van aangepaste wizardpagina's. Een aangepaste wizardpagina verzamelt informatie naast of in plaats van de wizardpagina's UDI biedt.  

 Afbeelding 1 ziet u de relatie tussen de waarde van de Wizard UDI en de Wizard UDI.  

 ![UDIDevelopersGuide1](media/UDIDevelopersGuide1.jpg "UDIDevelopersGuide1")  
Afbeelding 1. Relatie tussen de Wizard UDI en de Wizard UDI  

 **Afbeelding 1. Relatie tussen de Wizard UDI en de Wizard UDI**  

 Op een conceptuele niveau inclusief UDI ontwikkeling maken van:  

-   **Aangepaste wizardpagina's**. Wizardpagina's worden weergegeven in de Wizard UDI en verzamelen van de informatie die is vereist voor het voltooien van het implementatieproces. U maken wizardpagina's met C++ in Microsoft Visual Studio®. De aangepaste wizardpagina's worden geïmplementeerd als dll-bestanden in de Wizard UDI leest. De UDI software development kit (SDK) bevat een voorbeeld van het maken van aangepaste wizardpagina's.  

-   **Wizard Aangepaste pagina editors**. Wizard pagina editors kunt u de werking configureren van uw aangepaste wizardpagina. De wizard Aangepaste pagina editors worden geïmplementeerd als dll-bestanden die de waarde van de Wizard UDI leest. U maakt wizardpagina editors gebruiken:  

    -   [WPF](http://msdn.microsoft.com/library/ms754130.aspx) versie 4.0  

    -   [Microsoft Prismabewerking](http://compositewpf.codeplex.com/) versie 4.0  

    -   [Microsoft Unity Application Block](http://unity.codeplex.com/) (Unity) versie 2.1  

     MDT omvat alle assembly maken van een aangepaste wizardpagina editor voor gebruik in de waarde van de Wizard UDI. De UDI SDK bevat een voorbeeld van het maken van aangepaste wizard pagina editors.  

 De waarde van de Wizard UDI verbruikt bovendien ondersteunende wizard pagina editor-configuratiebestanden. U maken de wizard editor configuratiebestanden als onderdeel van het proces voor het maken van uw aangepaste wizardpagina's en aangepaste wizard pagina editors. De waarde van de Wizard UDI maakt de benodigde informatie in de XML in het configuratiebestand van de Wizard UDI en de bijbehorende .app-bestand.  

### <a name="preparing-the-udi-development-environment"></a>De ontwikkelomgeving UDI voorbereiden  
 Voordat u begint met het maken van uw eigen aangepaste wizardpagina's en wizardpagina editors, voer de volgende stappen voor het voorbereiden van de ontwikkelomgeving UDI:  

1.  Bereid de ontwikkeling UDI zoals beschreven in omgevingsvereisten [voorbereiden van de vereisten UDI Development Environment](#PrepareUDIDevelopmentEnvironmentPrerequisites).  

2.  De ontwikkelomgeving UDI configureren zoals beschreven in [configureren van de ontwikkelomgeving UDI](#ConfigureUDIDevelopmentEnvironment).  

3.  Controleren of de ontwikkelomgeving UDI zoals beschreven in correct is geconfigureerd [controleren van de ontwikkelomgeving UDI](#VerifyUDIDeploymentEnvironment).  

####  <a name="PrepareUDIDevelopmentEnvironmentPrerequisites"></a> De vereisten UDI ontwikkelings-omgeving voorbereiden  
 Als u de ontwikkeling UDI omgevingsvereisten voorbereiden, moet u de volgende stappen uitvoeren:  

1.  Bereid de ontwikkeling UDI omgeving hardware vereisten, zoals beschreven [voorbereiden van de vereisten UDI Development Environment Hardware](#PrepareUDIDevelopmentEnvironmentHardwarePrerequisites).  

2.  De UDI ontwikkelingsomgeving voorbereiden software vereisten zoals beschreven in [voorbereiden van de vereiste UDI Development Environment Software](#PrepareUDIDevelopmentEnvironmentSoftwarePrerequisites).  

#####  <a name="PrepareUDIDevelopmentEnvironmentHardwarePrerequisites"></a> Voorbereiden van de UDI Development Environment Hardware-vereisten  
 De UDI development environment hardware vereisten zijn de dezelfde hardwarevereisten voor de editie van Microsoft Visual Studio 2010 u gebruikt. Zie voor meer informatie over deze vereisten, de systeemvereisten voor elke editie op [Visual Studio 2010-producten](http://www.microsoft.com/visualstudio/products/2010-editions).  

#####  <a name="PrepareUDIDevelopmentEnvironmentSoftwarePrerequisites"></a> De softwarevereisten UDI ontwikkelings-omgeving voorbereiden  
 De ontwikkelomgeving UDI heeft de volgende softwarevereisten:  

-   Alle Windows-besturingssysteem die Visual Studio 2010 worden ondersteund (Windows 7 of Windows Server® 2008 R2 wordt aanbevolen.)  

     U moet een Windows-besturingssysteem die ondersteuning biedt voor de processorarchitectuur waarvoor u wilt ontwikkelen. U kunt de 32-bits en 64-bits UDI ontwikkeling met behulp van een 64-bits besturingssysteem uitvoeren. U alleen doen 32-bits UDI ontwikkeling op 32-bits besturingssystemen. Daarom moet u een 64-bits besturingssysteem.  

    > [!NOTE]
    >  IntelItanium versies (IA-64) van Windows-besturingssysteem worden niet ondersteund voor UDI ontwikkelomgevingen.  

     Zie voor meer informatie over de besturingssystemen die ondersteuning biedt voor Visual Studio 2010 de systeemvereisten voor elke editie op [Visual Studio 2010-producten](http://www.microsoft.com/visualstudio/products/2010-editions).  

-   Microsoft .NET Framework versie 4.0 (vereist door Visual Studio 2010)  

-   C++-taal (dat wil zeggen: de taal die wordt gebruikt in de uitbreiding UDI wizardpagina's)  

-   Andere talen die WPF ondersteunt, zoals C#, Visual Basic .NET of C + +/ Common Language-infrastructuur, die worden gebruikt voor het uitbreiden van de Wizard UDI wizard pagina editors  

    > [!NOTE]
    >  De voorbeeldcode van de bron voor de editors pagina van de Wizard UDI wizard is geschreven in C#. De C#-taal installeren als u wilt gebruiken de voorbeeldcode van de bron.  

####  <a name="ConfigureUDIDevelopmentEnvironment"></a> De ontwikkelomgeving UDI configureren  
 Na vervolgens UDI development environment vereisten wordt voldaan, voert u de volgende stappen voor het configureren van de ontwikkelomgeving UDI:  

1.  Install Visual Studio 2010.  

     Zorg ervoor dat u de taal C++ en een andere taal die ondersteuning biedt voor WPF installeert.  

    > [!NOTE]
    >  De voorbeeldcode van de bron voor de editor voor de Wizard UDI's is geschreven in C#. De C#-taal installeren als u wilt gebruiken de voorbeeldcode van de bron.  

     Zie voor meer informatie over het installeren van Visual Studio 2010 [Visual Studio installeren](http://msdn.microsoft.com/library/e2h7fzkw.aspx).  

2.  Installeer MDT.  

     Voor meer informatie over het installeren van MDT, Zie de sectie 'Installeren of upgraden naar MDT', in de MDT document *met behulp van de Microsoft Deployment Toolkit*.  

3.  Maak in Windows Verkenner *local_folder* (waarbij *local_folder* is een map op een lokaal station op de ontwikkelcomputer).  

4.  Kopiëren de *installation_folder*\SDK map *local_folder* (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd en *local_ map* is een map op een lokaal station op de ontwikkelcomputer).  

     U kopiëren de SDK-map op een andere locatie omdat MDT is geïnstalleerd in de map Program Files, die naar zonder verhoogde machtigingen kan worden geschreven. De SDK-map kopiëren naar een andere locatie kunt u de bestanden in de SDK-map zonder verhoogde machtigingen wijzigt.  

5.  Kopiëren de *installation_folder*\Templates\Distribution\Tools map *local_folder* (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd en *local_folder* is de map die u eerder in het proces gemaakt).  

6.  Wijzig de naam van de *local_folder*\Tools map *local_folder*\OSDSetupWizard (waar *local_folder* is de map die u eerder in het proces gemaakt).  

     Wanneer voltooid, de mapstructuur onder *local_folder* moet eruitzien als in de mapstructuur die wordt weergegeven in afbeelding 2 (waarbij *local_folder* is de map die u eerder in het proces hebt gemaakt en is weergegeven als *UDIDevelopment* in de afbeelding).  

     ![UDIDevelopersGuide2](media/UDIDevelopersGuide2.jpg "UDIDevelopersGuide2")  
Afbeelding 2. Mapstructuur voor UDI-ontwikkeling  

     **Afbeelding 2. Mapstructuur voor UDI-ontwikkeling**  

####  <a name="VerifyUDIDeploymentEnvironment"></a> Controleer of de ontwikkelomgeving UDI  
 Wanneer de ontwikkelomgeving UDI is geconfigureerd, moet u controleren of de ontwikkelomgeving UDI correct is geconfigureerd door ervoor te zorgen dat de voorbeeldprojecten correct in Visual Studio 2010 bouwen.  

 Controleren of de ontwikkelomgeving UDI correct is geconfigureerd door vast te stellen of:  

-   Het project SamplePage correct zoals beschreven in builds [Controleer of het Project SamplePage correct Builds](#VerifySamplePageProjectBuildsCorrectly)  

-   Het project SampleEditor correct zoals beschreven in builds [Controleer of het Project SampleEditor correct Builds](#VerifySampleEditorProjectBuildsCorrectly)  

#####  <a name="VerifySamplePageProjectBuildsCorrectly"></a> Controleer of het Project SamplePage correct Builds  
 Het project SamplePage bevat een voorbeeld van het maken van een aangepaste wizardpagina voor de Wizard UDI. Zie voor meer informatie over het project SamplePage [bekijken van de Visual Studio-oplossing van SamplePage](#ReviewSamplePageVisualStudioSolution).  

 **Om te controleren of het project SamplePage correct builds**  

1.  Start Visual Studio 2010.  

2.  Open het project SamplePage.  

     Het project SamplePage bevindt zich in de *local_folder*\SDK\UDI\SamplePage map (waarbij *local_folder* is de map die u eerder in het proces gemaakt).  

3.  In Visual Studio 2010 in Solution Explorer met de rechtermuisknop op het project SamplePage en klik vervolgens op **eigenschappen**.  

     De **SamplePage eigenschappenvensters** dialoogvenster wordt weergegeven.  

4.  In de **SamplePage eigenschappenvensters** in het dialoogvenster, gaat u naar configuratie-eigenschappen/foutopsporing.  

5.  In de eigenschappen van foutopsporing onder **configuratie**, selecteer **alle configuraties**.  

6.  In de eigenschappen van foutopsporing onder **opdracht**, type **$(TargetDir)\OSDSetupWizard.exe.**  

7.  In de eigenschappen van foutopsporing onder **werkmap**, type **$(TargetDir)**.  

8.  In de **SamplePage eigenschappenvensters** in het dialoogvenster, gaat u naar configuratie-eigenschappen/Build gebeurtenissen/na-Build gebeurtenis.  

9. In de eigenschappen van gebeurtenis na Build onder **opdrachtregel**, typt u het volgende:  

    ```  
    copy /y "$(ProjectDir)..\..\..\..\OSDSetupWizard\x86\*.*" "$(TargetDir)"  
    xcopy /y /i "$(ProjectDir)..\..\..\..\OSDSetupWizard\x86\en-us" "$(TargetDir)en-us"  
    copy /y "$(ProjectDir)..\..\..\..\OSDSetupWizard\OSDResults\Images\UDI_Wizard_Banner.bmp" "$(ProjectDir)header.bmp"  
    copy /y "$(ProjectDir)Config.xml" "$(TargetDir)”  
    copy /y "$(ProjectDir)header.bmp" "$(TargetDir)header.bmp"  
    ```  

10. In de **SamplePage eigenschappenpagina's** in het dialoogvenster, klikt u op **OK**.  

11. Sla het project.  

12. Van de **Debug** menu, klikt u op **foutopsporing starten**.  

     De **Microsoft Visual Studio**dialoogvenster wordt weergegeven dat aangeeft dat de bron verouderd is en wordt u gevraagd of u wilt het project te bouwen.  

13. In de **Microsoft Visual Studio** in het dialoogvenster, klikt u op **Ja**.  

     De **Nee foutopsporingsgegevens** dialoogvenster wordt weergegeven waarin wordt gemeld dat er geen informatie voor foutopsporing beschikbaar voor OSDSetupWizard.exe.  

14. In de **Nee foutopsporingsgegevens** in het dialoogvenster, klikt u op **Ja**.  

     De Wizard UDI geopend met de wizard Aangepaste pagina weergegeven.  

15. Controleer of u kunt een waarde in selecteren **Kies uw locatie**.  

16. In de **voorbeeldpagina Wizard** vormen, klikt u op **annuleren**.  

     De **Wizard annuleren** dialoogvenster wordt weergegeven.  

17. In de **Wizard annuleren** in het dialoogvenster, klikt u op **Ja**.  

18. Close Visual Studio 2010.  

#####  <a name="VerifySampleEditorProjectBuildsCorrectly"></a> Controleer of het Project SampleEditor correct Builds  
 Het project SampleEditor bevat een voorbeeld van het maken van een aangepaste wizard-pagina-editor voor de waarde van de Wizard UDI. Zie voor meer informatie over het project SampleEditor [bekijken van de Visual Studio-oplossing van SamplePage](#ReviewSamplePageVisualStudioSolution).  

 **Om te controleren of het project SampleEditor correct builds**  

1.  Start Visual Studio 2010.  

2.  Open het project SampleEditor.  

     Het project SampleEditor bevindt zich in de *local_folder*\SDK\UDI\SampleEditor map (waarbij *local_folder* is de map die u eerder in het proces gemaakt).  

3.  Selecteer het SampleEditor-project in Visual Studio 2010 in Solution Explorer.  

4.  Van de **Project** menu, klikt u op **verwijzing toevoegen**.  

     De **verwijzing toevoegen** dialoogvenster wordt geopend.  

5.  In de **verwijzing toevoegen** in het dialoogvenster, klikt u op de **Bladeren** tabblad.  

6.  Op de **Bladeren** tabblad, gaat u naar *installation_folder*\Bin (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd). De volgende bestanden te selecteren en klik vervolgens op **OK**:  

    -   Microsoft.Enterprise.UDIDesigner.Common.dll  

    -   Microsoft.Enterprise.UDIDesigner.DataService.dll  

    -   Microsoft.Enterprise.UDIDesigner.Infrastructure.dll  

    -   Microsoft.Practices.Prism.dll  

    -   Microsoft.Practices.ServiceLocation.dll  

    -   Microsoft.Practices.Unity.dll  

    -   RibbonControlsLibrary.dll  

    > [!NOTE]
    >  U kunt meerdere bestanden selecteren op de **Bladeren** tabblad door de CTRL-toets ingedrukt terwijl u de bestanden op.  

7.  Klik in Solution Explorer, gaat u naar SampleEditor/verwijzingen.  

8.  Controleer of dat geen van de verwijzingen fouten of waarschuwingen hebben.  

9. Klik in Solution Explorer met de rechtermuisknop op het project SampleEditor en klik vervolgens op **eigenschappen**.  

     De **SampleEditor eigenschappenvensters** dialoogvenster wordt weergegeven.  

10. In de **SampleEditor eigenschappenpagina's** in het dialoogvenster, klikt u op de **Debug** tabblad.  

11. Op de **Debug** tabblad **Start externe programma**.  

12. In **extern programma Start**, type ***installation_folder\Bin\UDIDesigner.exe*** (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd), en klik vervolgens op **OK**.  

    > [!TIP]
    >  U kunt klikken op de knop met weglatingstekens (...) UDIDesigner.exe en blader naar de map.  

13. Van de **bestand** menu, klikt u op **Alles opslaan**.  

14. Kopiëren de *local_folder*\SDK\SamplePage\SamplePage.dll.config-bestand naar de *installation_folder*\Bin\Config map (waarbij *local_folder* is de map u gemaakt op de ontwikkelcomputer eerder in het configuratieproces en*installation_folder* is de map waarin u MDT hebt geïnstalleerd).  

15. In Visual Studio 2010 van de **Debug** menu, klikt u op **foutopsporing starten**.  

     De waarde van de Wizard UDI wordt gestart.  

16. Klik in de de Wizard UDI, op het lint op **Open**.  

     De **Open** dialoogvenster wordt weergegeven.  

17. In de **openen** in het dialoogvenster openen de *local_folder*\SDK\SamplePage\SamplePage\Config.xml-bestand (waarbij *local_folder* is de map die u hebt gemaakt in de ontwikkeling computer eerder in het configuratieproces).  

     De Config.xml bestand wordt geopend en de aangepaste [StageGroup](#StageGroup) wordt weergegeven in het detaildeelvenster.  

18. Klik in het detailvenster op de **configureren** tabblad.  

19. Controleer de configuratie-informatie voor de **locatie** vak, waaronder de volgende:  

    -   **Niet-vergrendelde** knop, waarmee u in- of uitschakelen de **locatie** vak  

    -   **Standaardwaarde** vak waarin u een standaardwaarde moet worden weergegeven in de **locatie** vak  

    -   **Beschrijvende weergavenaam zichtbaar in de overzichtspagina**, in dat u het bijschrift voor de informatie die wordt weergegeven op de **samenvatting** pagina  

    -   **Locatie** keuzelijst met invoervak, waaronder een lijst met mogelijke locaties  

20. Sluit de Wizard UDI Designer.  

21. Close Visual Studio 2010.  

## <a name="reviewing-the-udi-sdk-examples"></a>De voorbeelden UDI SDK controleren  
 Controleer voordat u begint de ontwikkeling, de voorbeelden die is opgegeven in de SDK UDI. Gebruik de informatie in deze handleiding en de broncode in de voorbeelden voor het maken van uw eigen UDI aangepaste wizardpagina's en wizardpagina editors.  

 Ga via de UDI SDK voorbeelden aan de hand van de:  

-   Inhoud van de SDK-map die u eerder tijdens de installatie hebt gekopieerd zoals beschreven in [bekijkt u de inhoud van de SDK-map](#ReviewContentsofSDKFolder)  

-   Aangepaste UDI wizard pagina voorbeeld zoals beschreven in [SamplePage Visual Studio-oplossing controleren](#ReviewSamplePageVisualStudioSolution)  

-   Aangepaste UDI wizard pagina editor voorbeeld zoals beschreven in [SampleEditor Visual Studio-oplossing controleren](#ReviewSampleEditorVisualStudioSolution)  

###  <a name="ReviewContentsofSDKFolder"></a> Controleer de inhoud van de SDK-map  
 Tijdens het configureren van de ontwikkelomgeving UDI kunt u de SDK-map gekopieerd vanuit de map waarin u MDT geïnstalleerd naar een andere map die u hebt gemaakt. Tabel 1 ziet u de mappen direct onder de map SDK en een korte beschrijving van elke.  

### <a name="table-1-folders-in-the-udi-sdk"></a>Tabel 1. Mappen in de SDK UDI  

|**Folder**|**Deze map bevat**|  
|-|-|  
|Bevat|De C++-header-bestanden nodig voor het maken van aangepaste wizardpagina's voor de Wizard UDI|  
|Libs|De dll-bestanden voor C++ die moeten worden gekoppeld aan uw aangepaste pagina. Er zijn 32-bits en 64-bits versies van de statische link libraries. **Opmerking:**  Itanium-versies van de bibliotheken (IA-64) zijn niet beschikbaar.|  
|SampleEditor|Een Visual Studio-project voor het bouwen van een aangepaste editor gebruikt voor het bewerken van de pagina SamplePage in de Wizard UDI, die is geschreven in C#|  
|SamplePage|Een Visual Studio-project voor het bouwen van een aangepaste UDI wizardpagina, die is geschreven in Visual C++|  

###  <a name="ReviewSamplePageVisualStudioSolution"></a> Bekijk de SamplePage Visual Studio-oplossing  
 Voordat u begint met het maken van uw aangepaste wizardpagina's en wizardpagina editors, moet u de volgende taken voor het voorbereiden van de ontwikkelomgeving UDI uitvoeren:  

-   De fasen van het in de levenscyclus van een pagina van de wizard UDI bekijken, zoals beschreven in [bekijken van de levenscyclus van de Wizard pagina](#ReviewWizardPageLifeCycle).  

-   Bekijk de Visual Studio-oplossing voor het voorbeeld SamplePage in de SDK UDI zoals beschreven in [Bekijk het voorbeeld SamplePage](#ReviewSamplePageExample).  

####  <a name="ReviewWizardPageLifeCycle"></a> Bekijk de pagina levenscyclus van Wizard  
 Een pagina van de wizard UDI heeft methoden die met elke fase of fase van de levenscyclus van de pagina overeenkomen. Als onderdeel van het maken van uw aangepaste wizardpagina, moet u deze methoden met uw code overschrijven. Tabel 2 vermeldt de methoden die u wel wilt overschrijven en bevat een korte beschrijving van elke methode, zoals wanneer u het gebruik van de methode in de levenscyclus van de wizard pagina.  

### <a name="table-2-methods-in-a-wizard-page-life-cycle"></a>Tabel 2. Methoden in de Wizard een pagina levenscyclus  

|**Methode**|**Beschrijving**|  
|-|-|  
|**OnWindowCreated**|Deze methode wordt slechts één keer worden aangeroepen nadat het venster van de pagina is gemaakt.<br /><br /> Schrijf code die wordt de pagina voor het eerst geïnitialiseerd en hoeft slechts één keer worden uitgevoerd voor deze methode. Bijvoorbeeld: Gebruik deze methode initialiseren velden of voor het lezen van configuratie-informatie uit de **Setter** elementen in het configuratiebestand van de Wizard UDI.|  
|**OnWindowShown**|Deze methode wordt aangeroepen telkens wanneer die de pagina wordt weergegeven in de Wizard UDI (weergegeven). De eerste keer dat de pagina wordt weergegeven wordt genoemd en elke keer dat u navigeren naar de pagina door te klikken op **volgende** of **terug** in de wizard.<br /><br /> Voor deze methode schrijven van code die wordt voorbereid de pagina moet worden weergegeven, bijvoorbeeld lezen geheugenvariabelen, takenreeksvariabelen of omgevingsvariabelen en vervolgens de pagina op basis van wijzigingen aan deze variabelen bij te werken.|  
|**OnCommonControlEvent**|Deze methode kan worden aangeroepen wanneer de pagina van de wizard wordt weergegeven en een WM_NOTIFY-bericht van een onderliggend element ontvangt (normaal gesproken bepaalt van algemene).<br /><br /> Voor deze methode code schrijven waarmee WM_NOTIFY op basis van het meldingsbericht worden verwerkt. U wilt bijvoorbeeld reageer op gebeurtenissen van een algemene besturingselement, zoals de reacties op of dubbelklik op gebeurtenissen voor een **TreeView** besturingselement.|  
|**OnUnhandledEvent**|Deze methode wordt aangeroepen wanneer een bericht niet-verwerkte venster wordt weergegeven voor uw pagina van de wizard. Deze methode biedt de mogelijkheid te onderscheppen en verwerkt deze anders onverwerkte vensterberichten.<br /><br /> Schrijf code die verantwoordelijk is voor de vensterberichten die betrekking hebben op de wizardpagina voor deze methode. Doorgaans is het niet nodig voor het onderdrukken van deze methode.|  
|**OnNextClicked**|Deze methode wordt aangeroepen wanneer u klikt op **volgende** in de wizard.<br /><br /> Voor deze methode code schrijven waarmee de nodige stappen voordat u doorgaat naar de volgende wizardpagina uitvoert, bijvoorbeeld, het valideren van dat kan lang duren. Als de validatie mislukt, kunt u de **volgende** aanvragen en een bericht weergegeven.|  
|**OnWindowHidden**|Deze methode wordt aangeroepen telkens wanneer die de pagina is verborgen wanneer de vorige of volgende wizardpagina wordt weergegeven.<br /><br /> Voor deze methode code schrijven die worden eventuele acties uitgevoerd voordat de pagina is verborgen voorafgaand aan een andere pagina wordt weergegeven. Doorgaans is het niet nodig voor het onderdrukken van deze methode.|  

####  <a name="ReviewSamplePageExample"></a> Bekijk het voorbeeld SamplePage  
 Controleer het SamplePage voorbeeld met de volgende lijst waarmee de reeks gebeurtenissen tijdens de levenscyclus van de wizard-pagina van het voorbeeld SamplePage:  

1.  De Wizard UDI OSDSetupWizard.exe, leest de configuratie-informatie uit het configuratiebestand van de Wizard UDI in het voorbeeld (het bestand Config.xml) zoals beschreven in [stap 1: De Wizard UDI (OSDSetupWizard.exe) leest het bestand Config.xml](#UDIWizardReadstheConfigFile).  

2.  De Wizard UDI laadt de dll-bestanden die vereist zijn voor elke pagina van de wizard weergegeven in het configuratiebestand van de Wizard UDI zoals beschreven in [stap 2: De Wizard UDI laadt het DLL-bestand voor de aangepaste wizardpagina](#UDIWizardLoadstheDLLforCustomWizardPage).  

3.  De Wizard UDI aangepaste wizardpagina wordt weergegeven en kunt u de interactie desired control zoals beschreven in [stap 3: De Wizard UDI weer met de aangepaste wizardpagina](#UDIWizardDisplaysCustomWizardPage).  

4.  Uitvoeren als de aangepaste wizardpagina heeft de gegevens worden verzameld, alle taken die nodig zijn voordat u op **volgende** om door te gaan naar de volgende wizard zoals beschreven in [stap 4: De knop volgende wordt geklikt op de pagina Wizard aangepaste](#TheNextButtonisClickedinCustomWizardPage).  

#####  <a name="UDIWizardReadstheConfigFile"></a> Stap 1: De Wizard UDI (OSDSetupWizard.exe) leest het bestand Config.xml  
 Wanneer de Wizard UDI (OSDSetupWizard.exe) wordt gestart, standaard wordt de Wizard UDI configuratiebestand, het bestand UDIWizard_Config.xml gelezen: het primaire configuratiebestand voor de Wizard UDI.  

> [!NOTE]
>  Het voorbeeld wordt het bestand Config.xml als het configuratiebestand. In MDT is het standaardconfiguratiebestand de UDIWizard_Config.xml-bestand, dat zich in de map Scripts in het pakket MDT-bestanden voor de configuratie bevindt.  

 U kunt het standaardconfiguratiebestand die gebruikmaakt van de Wizard UDI door het wijzigen van de Wizard UDI takenreeksstap gebruiken overschrijven de **/definition** parameter. Zie 'Overschrijven de configuratie-bestand dat de UDI Wizard gebruikt' voor meer informatie over het onderdrukken van het configuratiebestand die gebruikmaakt van de Wizard UDI.  

 De elementen op het hoogste niveau in het bestand Config.xml zijn de  

-   [DLL-bestanden](#DLLs) element  

-   [Stijl](#Style) element  

-   [Pagina's](#Pages) element  

-   [StageGroups](#StageGroups) element  

 Zie voor meer informatie over het schema van het configuratiebestand van de Wizard UDI en elk van deze elementen [UDI Wizard Configuratie-bestandsverwijzing Schema](#UDIWizardConfigurationFileSchemaReference).  

 De Wizard UDI scant de **dll's** element zoekt naar het dll-bestanden te laden. In het voorbeeld zijn twee dll-bestanden worden weergegeven: SamplePage.dll en SharedPages.dll. Deze DLL-bestanden moeten zich bevinden in dezelfde map als extra OSDSetupWizard.exe—the\\*platform* map (waarbij *platform* x86 voor de 32-bits versie of x64 voor de 64-bits-versie).  

 De Wizard UDI scant de **pagina's** element zoekt naar de pagina's die zijn gedefinieerd. In het voorbeeld zijn twee pagina's worden gedefinieerd: **Aangepaste** en **overzichtspagina**. De **Type** kenmerk van de **pagina** element is gedefinieerd in het bestand PageClassIDs.h en een unieke definieert het type van uw aangepaste pagina.  

 In het voorbeeld wordt het gedefinieerde type is **Microsoft.SamplePage.LocationPage**. Vervang het volgende om te voorkomen dat alle mogelijke conflicten met andere pagina's die u in de toekomst mogelijk maken voor uw aangepaste pagina:  

-   De naam van uw organisatie in plaats van **Microsoft**.  

-   De projectnaam van uw in plaats van **SamplePage**.  

-   De naam van uw aangepaste wizard pagina in plaats van **LocationPage**.  

#####  <a name="UDIWizardLoadstheDLLforCustomWizardPage"></a> Stap 2: De Wizard UDI laadt het DLL-bestand voor de aangepaste wizardpagina  
 Wanneer de Wizard UDI wordt geladen voor de DLL-bestand, roept de **RegisterFactories** functie, die moet worden geïmplementeerd in de DLL-bestand. Deze functie is geïmplementeerd in het voorbeeld in het bestand dllmain.ccp. Elke wizardpagina die u maakt moet implementeren de **RegisterFactories** functie.  

 De **RegisterFactories** functie wordt gebruikt om de klasse fabrieksinstellingen van uw pagina van de wizard registreren met het register van de factory klasse voor de Wizard UDI. *Klasse van de fabrieken* zijn klassen die u kunnen geen exemplaar van een andere klasse maken. De **RegisterFactories** functie maakt een nieuw exemplaar van een fabrieksklasse en die klasse in het register van de factory klasse geeft de wizard UDI, waardoor deze factory-klasse beschikbaar is bij de wizard. De Wizard UDI zoekt naar een klasse factory is geregistreerd met een ID die overeenkomt met de **Type** kenmerk van de **pagina** element worden opgegeven voor de aangepaste wizardpagina.  

 In het voorbeeld wordt de ID is gedefinieerd als **ID_Location** in het bestand PageClassIds.h als **Microsoft.SamplePage.LocationPage**, die overeenkomt met de **Type** kenmerk voor de  **Pagina** element in het bestand Config.xml. **ID_Location** is doorgegeven als een parameter in de **RegisterFactories** functie geïmplementeerd in het bestand dllmain.ccp.  

 U kunt een functie die met behulp van de Register_*naam* functie sjabloon vereenvoudigen van het maken van een nieuw exemplaar van de factory en Registreer het zojuist gemaakte exemplaar. De **naam** waarde die is opgegeven met de functie registreren sjabloon moet worden geïmplementeerd de **iClassFactory** interface. De [ClassFactoryImpl klasse](#ClassFactoryImplClass) voert het grootste deel van de details voor het implementeren van een klasse-factory.  

 U kunt ook de **RegisterFactories** functie taaktypen en typen validatiefuncties registreren. Zie voor meer informatie de volgende onderwerpen:  

-   [Maken van aangepaste UDI taken](#CreatingCustomUDITasks)  

-   [Maken van aangepaste UDI validatiefuncties](#CreatingCustomUDIValidators)  

> [!NOTE]
>  In het voorbeeld bevat en alleen de één aangepaste wizardpagina registreert. Het voorbeeld bevat geen aangepaste taken of validatiefuncties en dus registreert niet alle aangepaste taken of validatiefuncties.  

#####  <a name="UDIWizardDisplaysCustomWizardPage"></a> Stap 3: De Wizard UDI weer met de aangepaste wizardpagina  
 De aangepaste wizardpagina in het voorbeeld is gedefinieerd in het bestand LocationPage.cpp. Wizardpagina's worden afgeleid van de sjabloonklassen die bieden dat veel van de functionaliteit van een pagina heeft. Alle wizardpagina's moeten zijn afgeleid van de [WizardPageImpl sjabloonklasse](#WizardPageImplTemplateClass), welke implementeert de [IWizardPage Interface](#IWizardPageInterface). Elke pagina van de wizard kan andere optionele template klassen en de bijbehorende interfaces op basis van de behoeften van de pagina implementeren.  

 De [WizardPageImpl sjabloonklasse](#WizardPageImplTemplateClass) bevat verschillende nuttig interfaces waarmee u aangepaste wizardpagina's schrijven. Implementeer de [WizardPageImpl sjabloonklasse](#WizardPageImplTemplateClass) als basisklasse voor uw aangepaste wizardpagina.  

 Voor een lijst van de beschikbare:  

-   Sjabloonklassen voor wizardpagina's, Zie [Helperklassen van Wizard pagina](#WizardPageHelperClasses)  

-   Interfaces voor de wizard pagina sjabloonklassen, Zie [Wizard pagina Interfaces](#WizardPageInterfaces)  

 De aangepaste wizardpagina in het voorbeeld is afgeleid van de [WizardPageImpl sjabloonklasse](#WizardPageImplTemplateClass) en implementeert de [IWizardPage Interface](#IWizardPageInterface). Bovendien de aangepaste wizardpagina implementeert de **IFieldCallback** interface. Deze zijn geïmplementeerd in het bestand LocationPage.cpp.  

 De aangepaste wizardpagina voorbeeld heeft voorrang op de volgende methoden:  

-   **OnWindowCreated**. De **OnWindowCreated** methode in het voorbeeldpagina wizard roept de volgende methoden:  

    -   [AddField](#AddField). Deze methode is gekoppeld de **IDC_COMBO_LOCATION** invoervak de **IDD_LOCATION_PAGE** resource met de [gegevens](#Data) element met de naam **locatie**in het bestand Config.xml.  

         Naast de **AddField** methode, kunt u de [AddRadioGroup](#AddRadioGroup) en [AddToGroup](#AddToGroup) methoden ter ondersteuning van andere controls en behaviors.  

        > [!NOTE]
        >  Zorg ervoor dat u aanroept de [AddField](#AddField), [AddRadioGroup](#AddRadioGroup), of [AddToGroup](#AddToGroup) methode voorafgaand aan het aanroepen van de [InitFields](#InitFields) methode.  

    -   [InitFields](#InitFields). Gebruik deze methode worden de velden (besturingselementen) die u hebt toegevoegd aan het formulier wordt geïnitialiseerd. De aanwijzer van de pagina is een parameter. In het voorbeeld wordt de **dit** wijzer wordt doorgegeven, die verwijst naar de huidige pagina.  

        > [!NOTE]
        >  Ter ondersteuning van het gebruik van de **dit** wijzer, hanteert u de **IFieldCallback** interface naast de interfaces die de [WizardPageImpl sjabloonklasse](#WizardPageImplTemplateClass) ondersteunt.  

         De **IFieldCallback** aanroepen interface de **SetFieldDefault** methode die wordt gebruikt voor de standaardwaarden instellen voor besturingselementen dan tekst in en selectievakje besturingselementen. In het voorbeeld wordt de **SetFieldDefault** methode stelt u de eerste index van de keuzelijst met invoervak op basis van de standaardwaarde opgegeven in de **standaard** element worden opgegeven voor de [veld](#Field) element in het bestand Config.xml.  

     De **OnWindowCreated** methode stelt u het formulier domeincontroller met behulp van de [IFormController interface](#IFormController-Interface). Zie voor meer informatie over het instellen van de controller formulier [instellen van het formulier](#SettingUptheForm).  

-   **InitLocations**. Deze methode vult de keuzelijst met invoervak uit de lijst van locaties in het bestand Config.xml. De [gegevens](#Data) element en de onderliggende [DataItem](#DataItem) elementen het bestand Confg.xml voorzien in de lijst van mogelijke waarden.  

-   **OnNextClicked**. Deze methode voert de volgende taken uit:  

    -   Updates de **TSLocation** takenreeksvariabele met de waarde die is geselecteerd in de keuzelijst met invoervak met behulp van de **SaveFields** methode  

    -   Voegt de informatie die wordt weergegeven op de **samenvatting** pagina met behulp van de **SaveFields** methode  

#####  <a name="TheNextButtonisClickedinCustomWizardPage"></a> Stap 4: De knop volgende wordt geklikt op de pagina Wizard aangepaste  
 Wanneer de gebruiker de velden op de pagina aangepaste wizard voltooit, hij of zij klikt op **volgende**, welke aanroepen de **OnNextClicked** methode. De **OnNextClicked** methode eventuele benodigde taken voordat u doorgaat naar de volgende wizardpagina, zoals het opnemen van eventuele configuratiewijzigingen op de pagina aangepaste wizard wordt uitgevoerd.  

 Voor de aangepaste wizard voorbeeldpagina de onderdrukking voor de **OnNextClicked** methode is geïmplementeerd in het bestand LocationPage.ccp. In de **OnNextClicked** methode in de wizard Aangepaste voorbeeldpagina, de volgende methoden worden genoemd:  

1.  [InitSection](#InitSection). Deze methode initialiseert de header (bijschrift) voor de gegevens van de samenvatting weergegeven op de **samenvatting** pagina. Normaal gesproken stelt deze waarde met behulp van de **DisplayName()** functie. De gegevens die zijn gekoppeld aan dit bijschrift is opgeslagen met de [SaveFields](#SaveFields) methode.  

2.  [SaveFields](#SaveFields). Deze methode bespaart veldwaarden takenreeksvariabelen en de gegevens die worden weergegeven op de **samenvatting** pagina.  

###  <a name="ReviewSampleEditorVisualStudioSolution"></a> Bekijk de SampleEditor Visual Studio-oplossing  
 Voordat u begint met het maken van uw eigen aangepaste wizardpagina's en wizardpagina editors, voer de volgende stappen voor het voorbereiden van de ontwikkelomgeving UDI:  

-   De architectuur van de waarde van de Wizard UDI bekijken, zoals beschreven in [bekijken van de architectuur van UDI Wizard Designer](#ReviewUDIWizardDesignerArchitecture).  

-   Bekijk de onderdelen van een pagina van de Wizard UDI die kan worden aangepast met behulp van het configuratiebestand van de Wizard UDI zoals beschreven [configureerbare onderdelen van de evaluatie van een pagina van de Wizard UDI](#ReviewConfigurableComponentsofUDIWizardPage).  

-   Bekijk het voorbeeld EditorPage is opgegeven in de UDI SDK, zoals beschreven in [Bekijk het voorbeeld EditorPage](#ReviewEditorPageExample).  

####  <a name="ReviewUDIWizardDesignerArchitecture"></a> Bekijk de ontwerpfunctie UDI Wizard-architectuur  
 De waarde van de Wizard UDI is ontwikkeld met behulp van WPF Prismabewerking en Unity. De ontwerpfunctie UDI wordt gebruikt om de Wizard UDI configuratiebestand bewerken (UDIWizard_Config.xml), die de Wizard UDI (OSDSetupWizard.exe) tijdens runtime leest. De [pagina's](#Pages) element in het configuratiebestand van de Wizard UDI bevat een lijst van pagina's met een afzonderlijke [pagina](#Page) element voor elke pagina van de wizard.  

 Wanneer u de configuratie-instellingen voor een wizardpagina bewerkt, wordt de aangepaste pagina-editor die overeenkomt met het type van de pagina wizard geladen door de waarde van de Wizard UDI. De wizard Aangepaste pagina editors zijn ontwikkeld als WPF gebruikersbesturingselementen. De aangepaste wizard-editor gebruiken pagina's de [Model-View – ViewModel](http://msdn.microsoft.com/magazine/dd419663.aspx) (MVVM) ontwerppatroon voor WPF.  

 Het ontwerppatroon MVVM helpt het scheiden van de gebruikersinterface (UI; presentatie) van de gegevens die worden gepresenteerd. De hoeveelheid gegevens is een façade de [pagina](#Page) element in de Wizard UDI configuratiebestand (het bestand Config.xml in het voorbeeld), die wordt geopend met behulp van de [CurrentPage](#CurrentPage) eigenschap van de [ IDataService](#IDataService) interface.  

 De waarde van de Wizard UDI gebruikt de **DependencyAttribute** toegang krijgen tot de **DataService** klasse op basis van het framework afhankelijkheid injectie in Unity. Zie voor meer informatie over de afhankelijkheid tussenwerpsel framework in Unity [Some levensduur invoeren in uw toepassingen: Kennismaking met het blok Unity-toepassing](http://msdn.microsoft.com/library/ff650806.aspx).  

####  <a name="ReviewConfigurableComponentsofUDIWizardPage"></a> Configureerbare onderdelen van een pagina van de Wizard UDI controleren  
 Bij het maken van uw aangepaste wizardpagina sommige van de configuratie-instellingen in de code kan worden ingesteld en kan niet worden gewijzigd nadat u de pagina zijn gecompileerd. Echter voor andere configuratie-instellingen moet u deze configuratie-instellingen worden gewijzigd met de waarde van de Wizard UDI toestaan.  

 De configuratie-instellingen die u wilt configureren met behulp van de waarde van de Wizard UDI worden meestal opgeslagen in het configuratiebestand van de Wizard UDI (het bestand Config.xml in het voorbeeld). U kunt echter ook uw eigen afzonderlijk configuratiebestand maken indien nodig. Een voorbeeld van het gebruik van een afzonderlijk configuratiebestand is de UDIWizard_Config.xml.app bestand, die de **Webtoepassingsdetectie** taak en de **ApplicationPage** wizard pagina type gebruiken.  

 Hier volgt een lijst van de standaardconfiguratie-instellingen die u kunt beheren met behulp van de Wizard UDI Designer:  

-   **Veld**. Gebruik-velden kunnen gebruikers gegevens opgeven. Velden worden weergegeven als [veld](#Field) elementen in de Wizard UDI configuratiebestand (UDIWizard_Config.xml), die de configuratie-instellingen voor elk veld bevat. De bijbehorende wizard editor moet bieden een methode voor het bewerken van de configuratie-instellingen van het veld voor de veld met de [FieldElementControl](#FieldElementControl).  

-   **Eigenschappen**. Setters helpen bij het maken van eigenschappen voor entiteiten op de pagina, zoals pagina's in de [pagina](#Page) element velden in de [veld](#Field) element of gegevenstype in de [gegevens](#Data) of [ DataItem](#DataItem) elementen. Configureren van eigenschappen in de [Setter]() elementen. Toevoegen van een afzonderlijke [Setter]() element voor elke eigenschap die u wilt definiëren. Bewerkt u de eigenschappen die met behulp van de [SetterControl](#SetterControl) en configureer andere [Setter]() elementen met andere besturingselementen.  

-   **Gegevens**. Gegevens worden gebruikt voor het opslaan van gegevens voor gebruik door de wizardpagina en andere onderdelen. U kunt gegevens voor pagina's of velden met definiëren de [gegevens](#Data) of [DataItem](#DataItem) elementen. De gegevens kunnen worden gedefinieerd in een platte of hiërarchische structuur door het juiste gebruik van de [gegevens](#Data) of [DataItem](#DataItem) elementen. De Config.xml in het voorbeeld in de SDK laat zien hoe platte gegevensstructuren bouwen.  

 De wizard aangepaste editor die u maakt moet kunnen deze configuratie-instellingen beheren.  

####  <a name="ReviewEditorPageExample"></a> Bekijk het voorbeeld EditorPage  
 In het voorbeeld EditorPage wordt gebruikt voor het configureren van de configuratie-instellingen voor de **SamplePage** wizardpagina in het configuratiebestand van de Wizard UDI. In het voorbeeld EditorPage heeft de volgende primaire onderdelen:  

-   Gebruikersinterface voor het configureren van de **locatie** keuzelijst met invoervak instellingen  

-   Gebruikersinterface toevoegen of bewerken van een locatie in de lijst van mogelijke locaties die worden weergegeven in de **locatie** keuzelijst met invoervak  

-   Configuratie-instellingen lezen uit en opgeslagen in het configuratiebestand van de Wizard UDI  

-   Ondersteuning van code voor de andere onderdelen  

 Bekijk het voorbeeld EditorPage in Visual Studio door de volgende stappen uit te voeren:  

1.  Bekijk hoe de **SampleEditor** wizard pagina editor is geladen en geïnitialiseerd in de waarde van de Wizard UDI zoals beschreven in [revisie Wizard pagina Editor geladen en initialisatie](#ReviewWizardPageEditorLoadingInitialization).  

2.  Bekijk de gebruikersinterface gebruikt om te bewerken de **locatie** keuzelijst met invoervak in de bestanden LocationPageEditor.xaml en LocationPageEditor.xaml.cs zoals beschreven in [controleren gebruikersinterface gebruikt voor het configureren van de keuzelijst met invoervak voor locatie](#ReviewUserInterfaceUsedtoConfigureLocationComboBox).  

3.  Bekijk de gebruikersinterface die wordt gebruikt voor het toevoegen of bewerken van locaties aan de lijst in de bestanden AddEditLocationView.xaml en AddEditLocationView.xaml.cs zoals beschreven in [gebruikersinterface gebruikt voor het wijzigen van de lijst van mogelijke locaties bekijken](#ReviewUserInterfaceUsedtoModifyListofPossibleLocations).  

4.  Controleer de code die wordt gebruikt voor het beheren van configuratie-informatie opgeslagen in het configuratiebestand van de Wizard UDI zoals beschreven in [bekijken de Code gebruikt om informatie over de configuratie beheren](#ReviewCodeUsedtoManageConfigurationInformation).  

#####  <a name="ReviewWizardPageEditorLoadingInitialization"></a> Wizard pagina Editor laden en initialisatie controleren  
 Wizard Aangepaste pagina editors zijn geladen door de waarde van de Wizard UDI vereist. De configuratiebestanden van de Wizard UDI zijn geladen wanneer de waarde van de Wizard UDI wordt gestart. De waarde van de Wizard UDI scant de *install_folder*\Bin\Config map (waarbij *install_folder* is de naam van de map waarin de MDT is geïnstalleerd) voor bestanden met extensie .config.  

 Tijdens de configuratie van de ontwikkelomgeving UDI u het bestand SamplePage.dll.confg gekopieerd de *install_folder*\Bin\Config map. Wanneer u de waarde van de Wizard UDI start, wordt het bestand SamplePage.dll.confg gevonden en geladen.  

 De waarde van de Wizard UDI maakt gebruik van de volgende kenmerken van de [pagina](#Page) element in het bestand SamplePage.dll.confg laden en het voorbeeld EditorPage initialiseren:  

-   **DesignerAssembly**. Dit kenmerk bepaalt de naam van het DLL-bestand moet worden geladen. Deze DLL moet worden geplaatst in dezelfde map als het bestand UDIDesigner.exe, dit is de *install_folder*map \Bin (waarbij *install_folder* is de naam van de map waarin u MDT is geïnstalleerd).  

-   **DesignerType**. Dit kenmerk is de Microsoft .NET-typenaam van de klasse met het gebruikersbesturingselement WPF.  

-   **Type**. Gebruik dit kenmerk voor het configureren van het paginatype van de aangepaste wizardpagina die door de Wizard UDI wordt geladen. De waarde van de Wizard UDI dit kenmerk wordt gezocht die de juiste [pagina](#Page) element in het configuratiebestand van de Wizard UDI.  

-   **Dll**. Dit kenmerk gebruiken voor het configureren van de [DLL](#DLL) element in het configuratiebestand van de Wizard UDI, waarbij de waarde van de Wizard UDI wordt gemaakt.  

-   **Beschrijving**. Dit kenmerk gebruiken voor meer informatie over de wizard-editor. De waarde van dit kenmerk wordt weergegeven in de **nieuwe pagina toevoegen** in het dialoogvenster in het ontwerp van de Wizard UDI, die wordt gebruikt voor het toevoegen van de pagina van de wizard aan de 'pagina bibliotheek'.  

-   **DisplayName**. Dit kenmerk gebruiken voor de naam van de aangepaste wizardpagina die wordt weergegeven in de waarde van de Wizard UDI. De waarde van dit kenmerk wordt weergegeven in de **nieuwe pagina toevoegen** in het dialoogvenster in het ontwerp van de Wizard UDI, die wordt gebruikt voor het toevoegen van de pagina van de wizard aan de 'pagina bibliotheek'.  

     In het voorbeeld wordt het type van de **SamplePage** aangepaste wizardpagina is **Microsoft.SamplePage.LocationPage**, die wordt opgeslagen in het bestand Config.xml. Het bestand Config.xml bevindt zich in de *local_folder*\SDK\SamplePage\SamplePage map (waarbij *local_folder* is de map die u hebt gemaakt op de ontwikkelcomputer eerder in de configuratie Dit proces).  

#####  <a name="ReviewUserInterfaceUsedtoConfigureLocationComboBox"></a> Bekijk de gebruikersinterface die wordt gebruikt voor het configureren van de locatie keuzelijst met invoervak  
 Wanneer de wizard-editor wordt geladen en geïnitialiseerd, de wizard SampleEditor editor wordt geladen wanneer een pagina met een type **Microsoft.SamplePage.LocationPage** wordt bewerkt. De gebruikersinterface voor de editor wordt opgeslagen in het bestand LocationPageEditor.xaml.  

 Als u de gebruikersinterface voor het controleren op de **ontwerp** tabblad en de code op de **XAML** tabblad ziet u de relatie tussen de grafische gebruikersinterface en de elementen en kenmerken in het (Extensible Application Markup Language) XAML).  

 Als u bijvoorbeeld de **besturingselementen: FieldElementControl** element in de XAML ziet u hoe die is gekoppeld aan de indeling van de bijbehorende gebruikersinterface. Gebruik de **besturingselementen: FieldElementControl** element voor het definiëren van de [FieldElementControl](#FieldElementControl) besturingselement.  

 De **Binding** parameters in het XAML-bestand de velden op de voorbeeld-editor met de informatie in het configuratiebestand van de UDI wizard binden. Bijvoorbeeld de volgende code ties de **standaardwaarde** tekstvak met de [standaard](#Default) element in het configuratiebestand van de UDI-wizard (Config.xml in het voorbeeld):  

```  
<TextBox Text="{Binding FieldData.DefaultValue,  
 UpdateSourceTrigger=PropertyChanged,  
 Mode=TwoWay}"/>  
```  

 Zie voor meer informatie [hoe: Maak gegevens beschikbaar voor de Binding in XAML](http://msdn.microsoft.com/library/ms748857.aspx).  

 Gebruik de **Views:CollectionTControl.ColumnCollectionView** -element in de XAML die aan de lijst met beschikbare locaties in de rasterweergave bewerken. U gebruikt de [CollectionTControl](#CollectionTControl) besturingselementen voor het weergeven van de rasterweergave en binden van de rasterweergave naar de [gegevens](#Data) element met de naam **locatie** in het configuratiebestand UDI.  

#####  <a name="ReviewUserInterfaceUsedtoModifyListofPossibleLocations"></a> De gebruikersinterface die wordt gebruikt voor het wijzigen van de lijst met mogelijke locaties bekijken  
 De gebruikersinterface voor het aanpassen van de lijst met mogelijke locaties bestaat uit:  

-   Een contextafhankelijke menu en lint knoppen waarmee u kunt toevoegen, bewerken, verwijderen of wijzigen van de volgorde van items in de lijst van locaties, zoals beschreven in [Context-sensitive-Menu controleren en lint knoppen voor het wijzigen van de lijst van locaties](#ReviewContextSensitiveMenuandRibbonButtons)  

-   Een dialoogvenster waarin wordt gestart wanneer u wilt toevoegen of bewerken van een item in de lijst van locaties, zoals beschreven in [in het dialoogvenster voor het toevoegen of bewerken van locaties te controleren](#ReviewDialogBoxforAddingEditingLocations)  

######  <a name="ReviewContextSensitiveMenuandRibbonButtons"></a> Contextafhankelijke Menu controleren en lint knoppen voor het wijzigen van de lijst met locaties  
 Wanneer u met de rechtermuisknop in de keuzelijst met invoervak waarin de lijst met locaties, wordt een contextafhankelijke menu wordt weergegeven. Het lint heeft een bijbehorende knoppen waarmee u kunt dezelfde taken uitvoeren. De **weergaven: CollectionsTControl** controle-element in het bestand LocationPageEditor.xaml definieert de methoden die worden aangeroepen op basis van de uitgevoerde actie en de eigenschappen die u als volgt instellen:  

-   **SelectedItem**. Deze eigenschap gegevensgebonden wordt geactiveerd wanneer de gebruiker een item in de lijst selecteert. Deze eigenschap is gekoppeld aan de **CurrentLocation** eigenschap in het model weergeven, dat zich bevindt in het bestand LocationPageEditorViewModel.cs, en die wordt gebruikt door de [CollectionTControl](#CollectionTControl) besturingselement om door te geven van het item Wanneer u bewerken of verwijderen van een bestaand item geselecteerd.  

-   **AddItemAction**. Deze actie wordt uitgevoerd wanneer de gebruiker de **Item toevoegen** optie van contextafhankelijke menu of de bijbehorende knoppen op het lint. Er is een gegevensbinding aan een eigenschap in het model weergeven die als resultaat geeft de **AddLocationAction** object. Dit object is de **AddLocationCallback** methode, zich in het bestand LocationPageEditorViewModel.cs en het dialoogvenster wordt weergegeven in het bestand AddEditLocationView.xaml.  

-   **EditItemAction**. Deze actie wordt uitgevoerd wanneer de gebruiker de **Item bewerken** optie in het snelmenu. Er is een gegevensbinding aan een eigenschap in het model weergeven die als resultaat geeft de **EditLocationAction** object. Dit object is de **EditLocationCallback** methode, zich in het bestand LocationPageEditorViewModel.cs en het dialoogvenster wordt weergegeven in het bestand AddEditLocationView.xaml.  

-   **RemoveAction**. Deze actie wordt uitgevoerd wanneer de gebruiker de **Item verwijderen** optie in het snelmenu. Er is een gegevensbinding aan een eigenschap in het model weergeven die als resultaat geeft de **RemoveAction** object. Dit object is de **EditLocationCallback** methode, zich in het bestand LocationPageEditorViewModel.cs en toont een bericht dat de verwijdering van de locatie.  

######  <a name="ReviewDialogBoxforAddingEditingLocations"></a> Controleer in het dialoogvenster voor het toevoegen of bewerken van locaties  
 Als u een nieuwe locatie aan de lijst met locaties toevoegen of een bestaande locatie, wordt een bericht weergegeven dat in het bestand AddEditLocationView.xaml. Het bericht wordt weergegeven met behulp van de [ShowDialogWindow](#ShowDialogWindow) venster methode in het bestand LocationPageEditorViewModel.cs.  

 De gebruikersinterface in het bestand AddEditLocationView.xaml bestaat uit:  

-   Een frame dialoogvenster met de naam **DialogFrame**, waaronder de volgende elementen:  

    -   Een titel die u configureert met behulp van de **DialogTitle** kenmerk van het dialoogvenster frame  

    -   Een **OK** knop stelt de status van het resultaat als voor de **goedgekeurd** eigenschap **True** (de status van het resultaat is ingeschakeld de **AddLocationCallback** methode in het bestand LocationPageEditorViewModel.cs om te bepalen of de gebruiker heeft geklikt **OK**.)  

    -   Een **annuleren** knop stelt de status van het resultaat als voor de **goedgekeurd** eigenschap **False** (de status van het resultaat is ingeschakeld de **AddLocationCallback**  methode in het bestand LocationPageEditorViewModel.cs om te bepalen of de gebruiker heeft geklikt **annuleren**.)  

-   Een WPF-element dat bevat:  

    -   Een label dat u configureert met behulp van de **inhoud** kenmerk  

    -   Een tekstvak die is gebonden aan de [gegevens](#Data) element met de naam **locatie** in het configuratiebestand UDI (het bestand Config.xml in het voorbeeld)  

######  <a name="ReviewCodeUsedtoManageConfigurationInformation"></a> De Code die wordt gebruikt voor het beheren van configuratie-informatie bekijken  
 De configuratie-informatie voor uw aangepaste wizardpagina wordt opgeslagen in het configuratiebestand van de Wizard UDI die de:  

-   Bestand Config.XML in het voorbeeld dat is opgegeven met de SDK UDI (dit bestand bevat alleen de configuratieinstellingen voor het voorbeeld).  

-   UDIWizard_Config.xml bestand dat is opgegeven met MDT, opgeslagen in de *installation_folder*\Templates\Distribution\Scripts map (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd); Dit bestand bevat de configuratie-instellingen voor de ingebouwde wizardpagina's en fasen  

 In het voorbeeld SampleEditor de **locaties** routine helpt bij de configuratie-informatie en bevindt zich in het bestand LocationPageEditorViewModel.cs. De **locaties** routine retourneert een lijst van de locaties in het configuratiebestand van de Wizard UDI. De geretourneerde lijst bevat een item in het bijzonder voor elk [DataItem](#DataItem) element in het configuratiebestand van de Wizard UDI.  

## <a name="creating-custom-udi-wizard-pages"></a>Maken van aangepaste UDI wizardpagina 's  
 Het hoofdproces voor het maken van aangepaste UDI wizardpagina's is als volgt:  

1.  Maak een kopie van de oplossing SamplePage als uitgangspunt.  

2.  Breng de gewenste beveiligingsmaatregelen (velden) in het formulier.  

3.  Schrijf code om de juiste taken uitvoeren wanneer de pagina wordt geladen (onderdrukt voor de **OnWindowCreated** methode), met inbegrip van de volgende stappen uit:  

    1.  Initialiseren van het formulier.  

    2.  Variabelen, takenreeksvariabelen, omgevingsvariabelen of XML-bestand gegevens lezen-geheugen (zoals **Setter** eigenschappen).  

4.  Schrijven van code voor het uitvoeren van de juiste taken wanneer de pagina wordt weergegeven (onderdrukt voor de **OnWindowShown** methode), met inbegrip van de volgende stappen uit:  

    1.  In- of uitschakelen van besturingselementen op basis van informatie lezen wanneer de pagina wordt geladen in stap 3.  

    2.  Update de besturingselementen op basis van informatie lezen wanneer vervolgens pagina geladen in stap 3, zoals de populatie van besturingselementen op basis van de informatie lezen.  

5.  Schrijf code om de juiste taken uitvoeren terwijl de gebruiker met de wizardpagina werkt.  

6.  Schrijven van code voor het uitvoeren van de juiste taken wanneer de gebruiker **volgende** in de Wizard UDI (onderdrukt voor de **OnNextClicked** methode), met inbegrip van de volgende stappen uit:  

    1.  Alle geheugenvariabelen, takenreeksvariabelen, omgevingsvariabelen of XML-bestandsgegevens bijwerken.  

    2.  Overzichtspagina-informatie bijwerken (indien niet uitgevoerd door de velden op de pagina).  

7.  De oplossing bouwen.  

     Zorg ervoor dat de versie van het DLL-bestand dat u hetzelfde processorplatform als voor de installatie van MDT, met name het processorplatform voor Windows Preinstallation Environment (Windows PE). De Wizard UDI kunt uitvoeren in:  

    -   **Het bestaande besturingssysteem op de doelcomputer**. U kunt de 32-bits versies van uw pagina van de wizard uitvoeren op 32-bits of 64-bits Windows-besturingssystemen. U kunt echter alleen 64-bits versies van uw pagina van de wizard uitvoeren op 64-bits Windows-besturingssystemen.  

    -   **Windows PE op de doelcomputer**. Windows PE biedt geen ondersteuning voor 32-bits toepassingen uitgevoerd op een 64-bits versie van Windows PE. U moet dus een versie op voor de wizardpagina voor elke processorarchitectuur van Windows PE die u wilt gebruiken hebt gebouwd.  

8.  Kopieer het DLL-bestand voor uw aangepaste wizardpagina *installation_folder*\Templates\Distribution\Tools\ platformmap (waarbij *installation_folder* is de map waarin u MDT en geïnstalleerd*platform* is **x86** voor de 32-bits versie of **x64** is voor de 64-bits-versie).  

9. Voltooi de stappen voor het maken van aangepaste pagina-editor.  

## <a name="creating-custom-wizard-page-editors"></a>Maken van aangepaste Wizard pagina Editors  
 Het hoofdproces voor het maken van aangepaste UDI wizard pagina editors is als volgt:  

1.  Maak een kopie van de oplossing SampleEditor als uitgangspunt.  

2.  De primaire pagina editor voor UI in een .xaml-bestand maken.  

3.  Toevoegen van exemplaren van de [FieldElementControl](#FieldElementControl) beheren zoals vereist door de pagina van de wizard te configureren (indien nodig).  

4.  Toevoegen van exemplaren van de [SetterControl](#SetterControl) beheren zoals vereist door de pagina van de wizard te configureren (indien nodig).  

5.  Toevoegen van exemplaren van de [CollectionTControl](#CollectionTControl) beheren zoals vereist door de pagina van de wizard te configureren (indien nodig).  

6.  Voeg de [IDataService](#IDataService) interface.  

7.  Schrijf de juiste code voor het bijwerken van het configuratiebestand van de Wizard UDI op basis van de configuratie-instellingen worden geconfigureerd met behulp van uw aangepaste wizard-pagina-editor.  

8.  Onderliggende dialoogvensters maken in een .xaml-bestand, en deze aanroepen vanuit de primaire pagina editor met behulp van de [IMessageBoxService](#IMessageBoxService) interface zoals vereist door de wizardpagina worden geconfigureerd.  

9. Voeg dat de juiste interfaces naar het lint UDI Wizard Designer op basis van de vereisten van de wizardpagina worden geconfigureerd.  

10. De oplossing bouwen.  

    > [!NOTE]
    >  Zorg ervoor dat de versie van het DLL-bestand dat u hetzelfde processorplatform als de MDT-installatie. Bijvoorbeeld, als u de 64-bits versie van MDT installeert, vervolgens samenstellen een 64-bits versie van uw aangepaste pagina-editor.  

11. Maak een configuratiebestand van de Wizard UDI om de benodigde DLL's laden en het toewijzen van de wizardpagina editor met de bijbehorende wizardpagina (het bestand SamplePage.dll.config in het voorbeeld).  

     Zie voor meer informatie over de elementen nodig voor het uitvoeren van de toewijzing tussen de wizardpagina en de wizard-editor de [DesignerMappings](#DesignerMappings) element, de onderliggende elementen en de bijbehorende kenmerken.  

12. Kopieer het configuratiebestand van de Wizard UDI die u hebt gemaakt in de vorige stap voor de *installation_folder*\Bin\Config map (waarbij *installation_folder* is de map waarin u geïnstalleerd MDT-versie).  

13. Kopieer het DLL-bestand voor uw aangepaste wizard-editor en het *installation_folder*map \Bin (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd).  

##  <a name="CreatingCustomUDITasks"></a> Maken van aangepaste UDI taken  
 *UDI taken* zijn geschreven in C++ DLL die implementeren de [ITask interface](#ITaskinterface). Registreren van het DLL-bestand met de bibliotheek van de Wizard UDI taak door het maken van een configuratiebestand van de Wizard UDI (.config-bestand) en plaatst deze in de *installation_folder*\Bin\Config map (waarbij *installation_ map* is de map waarin u MDT hebt geïnstalleerd).  

> [!NOTE]
>  U kunt een DLL-bestand met pagina's, taken en validatiefuncties binnen hetzelfde DLL-bestand maken. U kunt ook een enkel de Wizard UDI configuratiebestand (.config) met de configuratie-instellingen voor de wizardpagina's, taken en Validators bestaat in de DLL-bestand maken.  

 **Aangepaste UDI taken maken**  

1.  Code schrijven waarmee de [ITask Interface](#ITaskinterface) en de volgende methoden:  

    -   [Init](#Init). Deze methode wordt aangeroepen om de initialisatie van de taak.  

    -   [Execute](#Execute). Deze methode wordt aangeroepen als de taak wilt uitvoeren.  

2.  Schrijven van code die de classfactory aangepaste taak bij het factory-register registreert.  

3.  Bouw de oplossing voor uw aangepaste taak.  

    > [!NOTE]
    >  Zorg ervoor dat de versie van het DLL-bestand dat u hetzelfde processorplatform als de MDT-installatie. Bijvoorbeeld, als u de 64-bits versie van MDT installeert, vervolgens samenstellen een 64-bits versie van uw aangepaste UDI-taak.  

4.  Maak een [taak](#Task) element onder de [TaskLibrary](#TaskLibrary) element in het configuratiebestand voor de Wizard UDI vergelijkbaar met het volgende fragment:  

    ```  
    <Task DLL="OSDRefreshWizard.dll" Description="Discovers supported applications for install." Type="Microsoft.OSDRefresh.AppDiscoveryTask" Name="Application Discovery">  
       <TaskItem Type="Setter" Name="Status Bitmap">  
          <Param Name="BitmapFilename"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Log File">  
          <Param Name="log"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Write Configuration File">  
          <Param Name="writecfg"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Read Configuration File">  
          <Param Name="readcfg"/>  
       </TaskItem>  
    </Task>  
    ```  

    > [!NOTE]
    >  Alle [taak](#Task) elementen bevatten de **BitmapFilename** parameter. Geef alle overige parameters als de taak is vereist. Bijvoorbeeld, in het vorige fragment de **logboek** parameter wordt gebruikt om op te geven van een parameter voor de locatie van een logbestand.  

5.  Kopieer het configuratiebestand van de Wizard UDI gemaakt in de vorige stap voor de *installation_folder*\Bin\Config map (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd).  

6.  Kopieer het DLL-bestand voor uw aangepaste taak de *installation_folder*\Templates\Distribution\Tools\ platformmap (waarbij *installation_folder* is de map waarin u MDT en geïnstalleerd*platform* is **x86** voor de 32-bits versie of **x64** is voor de 64-bits-versie).  

##  <a name="CreatingCustomUDIValidators"></a> Maken van aangepaste UDI validatiefuncties  
 *UDI validatiefuncties* zijn geschreven in C++ DLL die implementeren de **IValidator** interface. Registreren van het DLL-bestand met de validatie van de Wizard UDI bibliotheek door het maken van een configuratiebestand van de Wizard UDI (.config-bestand) en plaatst deze in de *installation_folder*\Bin\Config map (waarbij  *installation_folder* is de map waarin u MDT hebt geïnstalleerd).  

 **Aangepaste UDI validatiefuncties maken**  

1.  Schrijven van code die u een subklasse van maakt de **BaseValidator** klasse en implementeert de volgende methoden:  

    -   **Init (IControl \*pControl, IWizardPageContainer \*pContainer, IStringProperties \*pProperties)**. Het formulier domeincontroller roept de **Init** lid initialiseren van de validatiefunctie. Deze methode moet aanroepen de **Init** methode voor de **BaseValidator** klasse. Normaal gesproken geen eigenschappen ingesteld voor de validatiefunctie uit het configuratiebestand van de Wizard UDI worden gelezen. Bijvoorbeeld, de **InvalidCharactersValidator** validator haalt de waarde van de **%{invalidchars/** eigenschap met deze methode.  

    -   **IsValid**. De controller formulier roept deze methode om te zien of het besturingselement geldige tekst bevat. Hieronder volgt een voorbeeld van de **IsValid** methode voor een validatiefunctie die valideert het veld is niet leeg zijn:  

        ```  
        BOOL IsValid(LPBSTR pMessage)  
        {  
            __super::IsValid(pMessage);  

            _bstr_t text;  
            m_pText->GetText(text.GetAddress());  
            return (text.length() > 0);  
        }  
        ```  

    -   **Init (IControl \*pControl, LPCTSTR bericht)**. De controller formulier roept dit lid voor elke toetsaanslag en andere gebeurtenissen, zodat de validatiefunctie kunt valideren van de inhoud van de controle- en bijgewerkte berichten aan de onderkant van de wizardpagina (of schakel ze).  

     Dit zijn doorgaans alleen methoden die u wilt overschrijven. Echter afhankelijk van de validatiefunctie mogelijk moet u voor het onderdrukken van andere methoden in de subklasse zijn van de **BaseValidator** klasse die u maakt. Zie voor meer informatie over deze andere methoden, de **BaseValidator** klasse.  

2.  Schrijven van code die de klasse aangepaste taak bij de Register-factory registreert.  

3.  Bouw de oplossing voor uw aangepaste taak.  

    > [!NOTE]
    >  Zorg ervoor dat de versie van het DLL-bestand dat u hetzelfde processorplatform als de MDT-installatie. Bijvoorbeeld, als u de 64-bits versie van MDT installeert, vervolgens samenstellen een 64-bits versie van uw aangepaste UDI-taak.  

4.  Maak een [Validator](#Validator) element onder de **ValidatorLibrary** element in het configuratiebestand voor de Wizard UDI vergelijkbaar met het volgende fragment:  

    ```  
    <Validator   
    <Validator DLL="" Description="Must follow a pre-defined pattern" Type="Microsoft.Wizard.Validation.RegEx" Name="NamedPattern">  
       <Param Description="Enter the message you want displayed when the text in this field doesn't match the pattern:" Name="Message" DisplayName="Message"/>  
       <Param Description="The name of a pre-defined regular expression pattern. Must be Username, ComputerName, or Workgroup" Name="NamedPattern" DisplayName="Named Pattern"/>  
    </Validator>  
    ```  

    > [!WARNING]
    >  Alle [Validator](#Validator) elementen bevatten de **bericht** parameter. Geef alle overige parameters zoals vereist door de validatiefunctie. Bijvoorbeeld, in het vorige fragment de **NamedPattern** parameter wordt gebruikt om een parameter voor de naam van een vooraf gedefinieerde reguliere-expressiepatroon opgeven.  

5.  Kopieer het configuratiebestand van de Wizard UDI gemaakt in de vorige stap voor de *installation_folder*\Bin\Config map (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd).  

6.  Kopieer het DLL-bestand voor uw aangepaste taak de *installation_folder*\Templates\Distribution\Tools\ platformmap (waarbij *installation_folder* is de map waarin u MDT en geïnstalleerd*platform* is **x86** voor de 32-bits versie of **x64** is voor de 64-bits-versie).  

## <a name="udi-wizard-reference"></a>Wizard UDI-verwijzing  

### <a name="wizard-page-components"></a>Onderdelen van de wizard  
 U kunt een van de verschillende onderdelen van het vooraf gedefinieerde gebruiken voor het bouwen van uw aangepaste pagina's.  

#### <a name="creating-component-instances"></a>Onderdeel-instanties maken  
 De Wizard UDI gebruikt klassefabrieken nieuwe exemplaren van objecten voor u te maken. Deze factory's zijn geregistreerd met een factory register, met een tekenreeks als de sleutel voor de factory. Bijvoorbeeld, de **WmiRepository** onderdeel wordt geïdentificeerd door de tekenreeks 'Microsoft.Wizard.WmiRepository' beschikbaar in het headerbestand IWmiRepository als is **ID_WmiRepository**.  

 Ervan uitgaande dat u uw pagina als een subklasse van geschreven hebt **WizardPageImpl**, kunt u een nieuw exemplaar van een **WmiRepoistory** zoals deze:  

```  
PWmiRepository pWmi;  
CreateInstance(Container(), ID_WmiRepository, &pWmi);  
```  

 De **CreateInstance** functie is een sjabloonfunctie van het type-safe voor het maken van nieuwe exemplaren van onderdelen. **PWmiRepository** is een intelligente aanwijzer, zodat deze verwijzing telling voor u verwerkt.  

#### <a name="creatable-components"></a>Onderdelen worden gemaakt  
 Er is een set van onderdelen die u met het register registreren kunt. De eerste set van onderdelen wordt altijd geregistreerd, omdat het belangrijkste uitvoerbare bestand van de Wizard UDI deze biedt. De twee sets van onderdelen vindt u in 'optioneel' dll's. Voor deze onderdelen beschikbaar zijn, moet het DLL-bestand worden vermeld in de **dll's** gedeelte van het .config-XML-bestand. Uw code hoeft niet te weten welke uitvoerbaar bestand bevat een specifiek onderdeel.  

 De lijst met onderdeel-id's voor onderdelen (naam van het onderdeel is hetzelfde als de ID, maar zonder de eerste *ID_*) geregistreerd met de factory register (gedefinieerd in OSDSetupWizard) wordt weergegeven in de tabel 3.  

### <a name="table-3-component-ids"></a>Tabel 3. Onderdeel-id 's  

|**ID**|**Beschrijving**|  
|-|-|  
|ID_ACPowerTask|(ITask IWizardComponent) Een voorbereidende taak die ervoor zorgt dat uw computer niet wordt uitgevoerd op de accu alleen|  
|ID_AppDiscoveryTask|(ITask IWizardComponent) Een speciale taak voor het detecteren van welke software u items hebt geïnstalleerd op uw computer|  
|**ID_BackgroundTask**|(**IBackgroundTask**, **IWizardComponent**) kan worden gebruikt om een taak uitvoeren op een andere thread|  
|**ID_CopyFilesTask**|(**ITask**, **IWizardComponent**) een taak om een of meer bestanden te kopiëren|  
|**ID_FormController**|(**IFormController**) wordt van de meeste dat niet moet geen exemplaar maken zelf, zoals uw pagina een eigen exemplaar ontvangt|  
|**ID_InvalidCharactersValidator**|(**IValidator**) zorgt ervoor dat er is geen tekstveld tekens uit een lijst aan de validator bevat|  
|**ID_Logger**|(**ILogger**) wordt van de meeste dat niet moet een exemplaar zelf maakt, zoals uw pagina een verwijzing naar het gedeelde exemplaar krijgt|  
|**ID_NonEmptyValidator**|(**IValidator**) een validatiefunctie dat ervoor zorgt dat er geen veld leeg is|  
|**ID_PasswordValidator**|(**IValidator**) een validatiefunctie dat ervoor zorgt dat er geen twee tekstvelden dezelfde inhoud hebben|  
|**ID_Regex**|(**IRegEx**) evalueert reguliere expressies, zoekt u overeenkomsten|  
|**ID_RegExValidator**|(**IValidator**) een validatiefunctie te valideren op basis van een reguliere expressie of een bekende patroon|  
|**ID_SimpleStringProperties**|(**IStringProperties**, **ISimpleStringProperties**) biedt een eenvoudige manier om de eigenschappen zonder gebruik van XML naar taken verzenden|  
|**ID_ShellExecuteTask**|(**ITask**, **IWizardComponent**) een extern programma uitvoeren|  
|**ID_SummaryBag**|(**ISummaryBag**) beschikbaar indirect van uw pagina via de methode formulier|  
|**ID_TaskManager**|(**ITaskManager**, **IBackgroundCallback**, **IWizardComponent**) Hiermee beheert u met een verzameling taken en de gebruikersinterface|  
|**ID_WmiRepository**|(**IWmiRepository**, **IWizardComponent**) kunt u Windows Management Instrumentation (WMI)-query's uitvoeren|  
|**ID_IXmlDocument**|(**PxDoc**) biedt een façade voor lezen en schrijven van XML-documenten|  

 De gedefinieerde OSDRefreshWizard.dll, gedeelde's en andere onderdelen van het besturingselement worden weergegeven in de tabel 4 en 5 van de tabel.  

### <a name="table-4-directory-controls"></a>Tabel 4. Directory-besturingselementen  

|**ID**|**Beschrijving**|  
|-|-|  
|**ID_Directory**|(**IDirectory**) een façade voor het verkrijgen van directory-informatie van het bestandssysteem|  

### <a name="table-5-defined-sharedpagesdll"></a>Tabel 5. Gedefinieerde SharedPages.dll  

|**ID**|**Beschrijving**|  
|-|-|  
|**ID_ADHelper**|(**IADHelper**) biedt een façade voor een beperkte set van functies in Active Directory® Domain Services (AD DS)|  
|**ID_CpuInfo**|(**ICpuInfo**) wordt bepaald of de CPU 32 of 64-bits|  
|**ID_DomainJoinValidator**|(**IDomainJoinValidator**) heeft een aantal methoden voor het controleren of een set referenties aan een domein is toegestaan|  
|**ID_DriveList**|(**IDriveList**, **IBindableList**, **IWizardComponent**) maakt gebruik van WMI om een lijst van schijven op uw computer te verkrijgen|  
|**ID_WiredNetworkTask**|(**ITask**) een taak die wordt gecontroleerd of u bent verbonden met het netwerk met een gekoppeld (in plaats van draadloos)-netwerkadapter|  

#### <a name="control-components"></a>Onderdelen van beheer  
 U communiceert met de besturingselementen op de pagina via de **GetControlWrapper** sjabloonfunctie dat toegang tot een van de typen van onderdelen biedt die worden vermeld in tabel 6.  

### <a name="table-6-components"></a>Tabel 6. Onderdelen  

|**Dialoogvenster besturingselementtypen**|**Beschrijving**|  
|-|-|  
|**CONTROL_CHECK_BOX**|(**ICheckBox**) een façade voor het werken met selectievakje besturingselementen|  
|**CONTROL_COMBO_BOX**|(**IComboBox**) een façade voor keuzelijsten met invoervak|  
|**CONTROL_GENERIC**|(**IControl**) kunt u werken met de meeste typen van besturingselementen voor het inschakelen van controle en zichtbare status|  
|**CONTROL_LIST_VIEW**|(**IListView**) een façade toegang verlenen tot de functies van een besturingselement voor lijstweergave|  
|**CONTROL_PROGRESS_BAR**|(**IProgressBar**) een façade voor het werken met de positie van een besturingselement voortgang|  
|**CONTROL_RADIO_BUTTON**|(**IRadioButton**) een façade voor het werken met keuzerondjes|  
|**CONTROL_STATIC_TEXT**|(**IStaticText**) een façade waarmee de machtiging lezen/schrijven naar de tekst van een besturingselement, zoals een label of in het tekstvak|  
|**CONTROL_TREE_VIEW**|(**ItreeView**) een façade voor het werken met een boomstructuurweergave|  

#### <a name="image-list-component"></a>Afbeelding lijstonderdeel  
 Dit onderdeel is een façade voor een **ImageList** besturingselement op de pagina. U maakt een lijst met afbeeldingen via de **IListView** of **ITreeView** interface.  

#### <a name="formcontroller-component"></a>FormController onderdeel  
 De wizard dit onderdeel voor u gemaakt en wordt doorgegeven aan uw pagina. U openen vanuit uw pagina met de **formulier** methode, waarmee de **WizardPageImpl** baseren klasse implementeert.  

#### <a name="invalidcharactervalidator-component"></a>InvalidCharacterValidator onderdeel  
 Dit is een soort validator die u op een pagina opnemen kunt. De ID is **ID_InvalidCharactersValidator** (gedefinieerd in IValidator.h), die heeft een tekstwaarde van 'Microsoft.Wizard.Validation.InvalidChars'.  

 Deze validatiefunctie wordt gezocht naar één eigenschap (een **Setter** element in het .config-bestand) aangeroepen **%{invalidchars/**, dit is een lijst met tekens die niet zijn toegestaan. Het controleren van de tekens in een tekstvak; Als de tekst tekens uit deze lijst bevat, rapporteert de component is mislukt.  

#### <a name="nonemptyvalidator-component"></a>NonEmptyValidator onderdeel  
 Dit is een soort validator die u op een pagina opnemen kunt. De ID is **ID_NonEmptyValidator** (gedefinieerd in IValidator.h), die heeft een tekstwaarde van 'Microsoft.Wizard.Validation.NonEmpty'.  

 Deze validatiefunctie meldt fout als in het tekstvak (of een ander besturingselement die ondersteuning biedt voor **IStaticText**) heeft een lege tekenreekswaarde.  

#### <a name="passwordvalidator-component"></a>PasswordValidator onderdeel  
 Dit is een soort validator die u op een pagina opnemen kunt. De ID is **ID_PasswordValidator** (gedefinieerd in IValidator.h), die heeft een tekstwaarde van 'Microsoft.Wizard.Validation.Password'.  

 Deze validatiefunctie werkt met twee verschillende Tekstbesturingselementen (die ondersteuning bieden voor bepaalt **IStaticText**) en meldt fout als ze geen dezelfde waarden bevatten. Met andere woorden, mislukt de bewerking als de **wachtwoord** en **wachtwoord bevestigen** tekstvakken komen niet overeen.  

 Omdat deze validatiefunctie twee besturingselementen vereist, moet deze meer instellen dan andere validatiefuncties. De installatie kan er ongeveer als volgt uitzien:  

```  
Form()->AddToGroup(IDC_EDIT_PASSWORD, IDC_EDIT_PASSWORD2);  
PValidator pValidator;  
Form()->AddValidator(IDC_EDIT_PASSWORD, ID_PasswordValidator, pMessage, &pValidator);  
PStaticText pPassword2;  
GetControlWrapper(View(), IDC_EDIT_PASSWORD2, CONTROL_STATIC_TEXT, &pPassword2);  
pValidator->SetProperty(0, pPassword2);  
```  

 Eerste stap definieert u de **wachtwoord bevestigen** besturingselement als een 'onderliggend' van de **wachtwoord** besturingselement. Op die manier als de controller formulier schakelt de **wachtwoord** besturingselement, wordt ook uitgeschakeld de **wachtwoord bevestigen** besturingselement. Voeg vervolgens de validatie van een wachtwoord toe aan het formulier. Ten slotte de validatiefunctie wachtwoord voorzien van de interface voor de **wachtwoord bevestigen** besturingselement.  

 Vanwege de vereisten voor twee besturingselementen, moet u code voor het instellen van deze validatiefunctie in plaats van het .config-XML-bestand.  

#### <a name="regexvalidator-component"></a>RegExValidator onderdeel  
 Dit is een soort validator die u op een pagina opnemen kunt. De ID is **ID_RegExValidator** (gedefinieerd in IValidator.h), die heeft een tekstwaarde van 'Microsoft.Wizard.Validation.RegEx'.  

 Deze validatiefunctie vergelijkt de inhoud van een besturingselement (een die ondersteuning biedt voor **IStaticText**) mislukt als de tekst komt niet overeen met de reguliere expressie en een reguliere expressie.  

 U kunt ook deze validatiefunctie gebruiken met een vooraf gedefinieerde benoemde patroon. Voor het gebruik van een reguliere expressie het XML-bestand een setter eigenschap met de naam moet bevatten **patroon**. Als u wilt een benoemde patroon in plaats daarvan gebruiken, gebruikt u een setter aangeroepen **NamedPattern** ingesteld op een van de waarden in tabel 7.  

### <a name="table-7-named-pattern-setters"></a>Tabel 7. Benoemde patroon Setters  

|**Pattern**|**Beschrijving**|  
|-|-|  
|Gebruikersnaam|Controleert of de tekst is een van de vorm Domein\Gebruiker of user@domain|  
|ComputerName|De naam moet tussen 1 en 15 tekens lang en kan niet een reeks tekens bevatten (bijvoorbeeld: en?)|  
|Werkgroep|De naam moet tussen 1 en 15 tekens bestaan en mag niet een reeks tekens (zoals =, +, en?)|  

#### <a name="factoryregistry-component"></a>FactoryRegistry onderdeel  
 Dit onderdeel houdt van alle klassefabrieken en -services. Het implementeert de **IFactoryRegistry** interface en is beschikbaar via uw pagina indirect **Container** methode. Bovendien wordt het register geladen uitbreidings-dll's. Nadat een DLL-bestand worden geladen, het register zoekt naar een geëxporteerde aangeroepen functie **RegisterFactories**. U moet deze functie implementeren en registreren in het de klassefabrieken voor uw pagina's, taken en validatiefuncties (en andere klassefabrieken die u wilt registreren). Hier volgt een voorbeeld van het voorbeeldproject:  

```  
extern "C" __declspec(dllexport) void RegisterFactories(IFactoryRegistry *factories)  
{  
Register<LocationPageFactory>(ID_LocationPage, factories);  
}  
```  

#### <a name="logger-component"></a>Berichtenlogboek onderdeel  
 Dit onderdeel is beschikbaar voor uw pagina via de **berichtenlogboek** methode (geïmplementeerd door **WizardPageImpl**). Deze methode kunt u vermeldingen in het logboekbestand schrijven. De inhoud van het logboekbestand zijn handig voor het oplossen van problemen die gebruikers hebben mogelijk uitvoeren van de Wizard UDI.  

#### <a name="propertybag-component"></a>PropertyBag-onderdeel  
 De *eigenschappenverzameling* is een container voor geheugenvariabelen. Deze beschikbaar is via uw pagina met **Container() -> Properties()**. Geheugenvariabelen zijn handig voor het doorgeven van tijdelijke gegevens tussen verschillende pagina's.  

#### <a name="tsvariablebag-and-tsrepository-components"></a>TSVariableBag en TSRepository onderdelen  
 De **TSVariableBag** onderdeel kunt u lezen en schrijven van takenreeksvariabelen. Het zorgt ervoor dat de waarden in het geheugen totdat de gebruiker klikt op **voltooien** (standaard). U hebt toegang tot de **TSVariable** eigenschappenverzameling via de pagina **TSVariables** methode (geïmplementeerd door de **WizardPageImpl** basisklasse). Deze onderdelen Meld alle lees- en schrijfbewerkingen van takenreeksvariabelen.  

#### <a name="wmirepository-component"></a>WmiRepository onderdeel  
 Dit onderdeel biedt een façade voor het werken met WMI-query's. U kunt aanroepen de **CreateInstance** Help-functie met **ID_WmiRepository** verkrijgen van een exemplaar van dit onderdeel die ondersteuning biedt voor de **IWmiRepository** interface. Dit onderdeel retourneert resultaatrecords via de **IWmiIterator** interface.  

###  <a name="WizardPageHelperClasses"></a> Wizard pagina Helperklassen  
 U kunt aangepaste UDI wizardpagina's met behulp van de ingebouwde helperklassen opgegeven met de SDK UDI maken. Tabel 8 bevat de helperklassen die u gebruiken kunt voor het maken van aangepaste wizardpagina's.  

### <a name="table-8-helper-classes"></a>Tabel 8. Helperklassen  

|**Klasse van Help**|**Beschrijving**|  
|-|-|  
|[ClassFactoryImpl klasse](#ClassFactoryImplClass)|Dit is een nuttig basisklasse op voor het maken van een classfactory die u kunt vervolgens met het register factory registreren.|  
|[Sjabloon interfaceklasse](#InterfaceTemplateClass)|Gebruik deze sjabloonklasse wanneer u wilt maken van een component die meer dan één interface implementeert.|  
|[Klasse van Help voor pad](#PathHelperClass)|Deze klasse biedt algemene bewerkingen van het bestand of de map.|  
|[De sjabloonklasse aanwijzer](#PointerTemplateClass)|Deze klasse biedt verwijzing telling voor beheer van de levensduur in COM-onderdelen. Het is belangrijk interfaces vrijgeven wanneer u klaar bent met deze. Deze sjabloonklasse verwerkt automatisch de levensduur.|  
|[PUnknown klasse](#PUnkownClass)|Deze klasse is een intelligente aanwijzer specifiek voor de IUnknown-interface. Gebruik de sjabloonklasse aanwijzer voor alle andere interfaces.|  
|[StringUtil helperklasse](#StringUtilHelperClass)|Deze klasse biedt methoden waarmee het eenvoudiger is om te werken met tekenreeksen.|  
|[Hiermee sjabloonklasse](#SubInterfaceTemplateClass)|Deze basisklasse vergemakkelijkt het implementeren van een onderdeel dat ondersteunt een interface die zichzelf overneemt van een andere interface.|  
|[UnknownImpl sjabloonklasse](#UnknownImplTemplateClass)|Deze klasse voert het grootste deel van de details van het maken van een COM-onderdeel.|  
|[WizardComponent sjabloonklasse](#WizardComponentTemplateClass)|Deze basisklasse wordt gebruikt voor het maken van de onderdelen die toegang nodig tot de wizard-services, zoals het maken van het onderdeel en logboekregistratie.|  
|[WizardPageImpl sjabloonklasse](#WizardPageImplTemplateClass)|Deze basisklasse moet worden gebruikt als de basisklasse voor alle aangepaste wizardpagina 's|  

####  <a name="ClassFactoryImplClass"></a> ClassFactoryImpl klasse  
 Dit is een nuttig basisklasse op voor het maken van een classfactory die u kunt vervolgens met het register factory registreren.  

 Het volgende is een fragment uit het bestand LocationPage.h in het voorbeeldproject voor het definiëren van de **ClassFactoryImpl** klasse.  

```  
#pragma once  

#include "ClassFactoryImpl.h"  

class LocationPageFactory :public ClassFactoryImpl  
{  
protected:  
    IUnknown *CreateNewInstance();  
};  
```  

 Hier volgt een fragment uit het bestand LocationPage.cpp in de wizard voorbeeldpagina gebruikt voor het definiëren van de classfactory voor de pagina.  

```  
IUnknown *LocationPageFactory::CreateNewInstance()  
{  
    return static_cast<IWizardPage *>(new LocationPage);  
}  
```  

####  <a name="InterfaceTemplateClass"></a> Sjabloon interfaceklasse  
 Deze sjabloonklasse gebruiken wanneer u wilt maken van een component die meer dan één interface implementeert, bijvoorbeeld:  

```  
classLocationPage :public Interface<IFieldCallback, WizardPageImpl<IDD_LOCATION_PAGE>>  
```  

 Deze code wordt gemaakt van de keten van een basisklasse die ondersteuning biedt voor beide **IFieldCalback** en de interfaces die **WizardPageImpl** ondersteunt (dat gebeurt met worden **IWizardPage**).  

####  <a name="PathHelperClass"></a> Klasse van Help voor pad  
 Deze klasse biedt algemene bewerkingen van het bestand of de map:  

```  
static inline std::wstring GetModulePath(HINSTANCE hModule)  
```  

 Ook wordt het volledige pad naar het .exe- of DLL-bestand met de sessie-ingang die u aan deze methode biedt:  

```  
static inline std::wstring GetModuleFilename(HINSTANCE hModule)  
```  

 De klasse retourneert het volledige pad en de naam van het .exe en .dll-bestand met de sessie-ingang die u opgeeft voor deze methode:  

```  
static inline std::wstring GetDirecotryName(LPCWSTR fullName)  
```  

 . . . of alleen het pad tijdens het verwijderen van oude bestandsnaam:  

```  
static inline std::wstring GetFileName(LPCWSTR fullName)  
```  

 Uitgaande van een pad met een bestandsnaam, retourneert de helperklasse pad alleen de bestandsnaam:  

```  
static inline std::wstring Combine(LPCWSTR path, LPCWSTR name)  
```  

 Ten slotte retourneert de klasse een nieuwe tekenreeks die is het gecombineerde pad en bestand naam (of een ander pad).  

####  <a name="PointerTemplateClass"></a> De sjabloonklasse aanwijzer  
 Deze klasse is gedefinieerd in Pointer.h. Omdat COM-onderdelen verwijzing telling voor beheer van de levensduur gebruiken, is het belangrijk dat u interfaces altijd vrijgeven wanneer u klaar bent met deze. Microsoft biedt een sjabloonklasse die de levensduur automatisch verwerkt. Bijvoorbeeld, als u een intelligente aanwijzer voor een XML-interface wilt, kunt u schrijven ongeveer het volgende:  

```  
Pointer<IXMLDOMNode> pNewChild  
pXmlDom->CreateNode(NODE_ELEMENT, L"MyElement", L"", &pNewChild);  
```  

 De eerste regel definieert de slimme aanwijzer. De tweede regel wordt weergegeven bij het ophalen van een smartcard aanwijzer via een andere aanroep. De **&** operator releases altijd een bestaande interface als deze een bevat en het adres voor de interne aanwijzer retourneert. Zodra u hebt opgehaald van een wijzer zoals dit de **aanwijzer** exemplaar aanroepen **Release** voor u wanneer de variabele buiten het bereik. Microsoft raadt slimme aanwijzers te gebruiken in plaats van aanroepen **AddRef** en **Release** handmatig.  

 Bovendien de **aanwijzer** aanwijzer klasse aanroepen van smartcard **QueryInterface** om op te halen van andere interfaces voor u. Bijvoorbeeld, wanneer het register factory een nieuw exemplaar van een onderdeel maakt, heeft deze code als volgt:  

```  
PWizardComponent pComp = pUnknown;  
if (pComp != nullptr)  
    pComp->SetContainer(m_pContainer);  
```  

 Het aanroepen van de eerste regel **QueryInterface** achter de schermen om aan te vragen de **IWizardComponent** interface. De resulterende slimme aanwijzer wordt gelijk **nullptr** als het onderdeel biedt geen ondersteuning voor deze interface.  

####  <a name="PUnkownClass"></a> PUnknown klasse  
 Deze klasse is een intelligente aanwijzer specifiek voor de **IUnknown** interface. Gebruik voor alle andere interfaces, de **aanwijzer** sjabloonklasse.  

####  <a name="StringUtilHelperClass"></a> StringUtil helperklasse  
 Deze klasse is gedefinieerd in Utilities.h en biedt methoden waarmee het eenvoudiger om met tekenreeksen te werken:  

```  
static inline int CompareIgnore(LPCWSTR first, LPCWSTR second)  
```  

 Deze methode vergelijkt u twee tekenreeksen tijdens niet hoofdlettergevoelig (Zie tabel 9).  

### <a name="table-9-stringutil-helper-class"></a>Tabel 9. StringUtil helperklasse  

|**retourneert**|**Beschrijving**|  
|-|-|  
|**0**|Tekenreeksen overeenkomen, niet hoofdlettergevoelig|  
|**<0**|Eerste < tweede|  
|**>0**|Eerste > tweede|  

 Hier volgt een voorbeeld:  

```  
static inline std::wstring Format(LPCWSTR input, int index, LPCWSTR value)  
static inline std::wstring Format(LPCWSTR input, int index, DWORD value)  
```  

 Deze methoden zijn enigszins zoals de Microsoft .NET **indeling** methoden in die zin dat de parameters in de vorm van zijn **{0}**. Echter, ze voeren geen opmaak van de invoer: alleen vervanging:  

```  
static inline std::wstring Printf(std::wstring format, I val)  
static inline std::wstring Printf(std::wstring format, I val1, J val2)  
static inline std::wstring Printf(std::wstring format, I val1, J val2, K val3)  
static inline std::wstring Printf(std::wstring format, I val1, J val2, K val3, L val4)  
```  

 Dit zijn de wrappers voor de **StringCchPrintf** dat rendement een **wstring** zodat er geen geheugen toewijzen voor tekenreeksen of buffers zelf.  

####  <a name="SubInterfaceTemplateClass"></a> Hiermee sjabloonklasse  
 Deze basisklasse vergemakkelijkt het implementeren van een onderdeel dat ondersteunt een interface die zichzelf overneemt van een andere interface. Bijvoorbeeld, de **ICheckBox** overneemt van interface **IControl**. Dit is hoe deze klasse wordt gebruikt voor het definiëren van de **CheckBoxWrapper**:  

```  
classCheckBoxWrapper :public SubInterface<IControl, UnknownImpl<ICheckBox> >  
```  

 De basis-interface is de eerste parameter, terwijl de afgeleide interface de tweede parameter is.  

####  <a name="UnknownImplTemplateClass"></a> UnknownImpl sjabloonklasse  
 Deze klasse is gedefinieerd in UnknownImpl.h en voert het grootste deel van de details van het maken van een COM-onderdeel. Hier volgt een voorbeeld van hoe u deze basisklasse zou gebruiken:  

```  
classDirectory :public UnknownImpl<IDirectory>  
```  

 Deze code definieert een klasse die ondersteuning biedt voor de **IDirectory** interface.  

####  <a name="WizardComponentTemplateClass"></a> WizardComponent sjabloonklasse  
 Deze klasse is gedefinieerd in IWizardComponent.h en is een nuttig basisklasse voor het maken van de onderdelen die toegang nodig tot de wizard-services, zoals het maken van het onderdeel en logboekregistratie.  

 Een voorbeeld: dit is hoe de **CopyFilesTask** onderdeel is gedefinieerd:  

```  
classCopyFilesTask :public WizardComponent<ITask>  
{  
    ...  
```  

 De parameter voor deze sjabloonklasse is de 'belangrijkste' interface die u wilt gebruiken voor het onderdeel dat in het geval van taken **ITask**. Met behulp van **WizardComponent** betekent dat het onderdeel zowel de interface uw Geef ondersteunt (**ITask** in dit voorbeeld) en **IWizardComponent**.  

 Wanneer u het register van de factory klasse voor het maken van een nieuw onderdeel, het register van het onderdeel roept **IWizardComponent -> SetContainer** methode voor het onderdeel toegang tot de services van de wizard.  

####  <a name="WizardPageImplTemplateClass"></a> WizardPageImpl sjabloonklasse  
 Deze klasse gebruiken als de basisklasse voor uw aangepaste pagina's, bijvoorbeeld:  

```  
class LocationPage :public WizardPageImpl<IDD_LOCATION_PAGE>  
```  

 De parameter is de resource-ID voor de sjabloon voor dialoogvensters.  

###  <a name="WizardPageInterfaces"></a> Wizardpagina Interfaces  
 De Wizard UDI gebruikt interfaces voor toegang tot de andere besturingselementen op de pagina. Binnen u pagina die u gebruikt de **GetControlWrapper** functie voor het ophalen van een besturingselement wrapper. Hier volgt een voorbeeld:  

```  
PStaticText pFormat;  
GetControlWrapper(View(), IDC_CHECK_PARTITION, CONTROL_STATIC_TEXT, &pFormat);  
```  

 Hier **PStaticText** is een intelligente pointer naar de **IStaticText** interface. Slimme aanwijzers automatisch het COM-onderdeel aanroepen **Release()** methode wanneer ze buiten het bereik vallen of u het adres van een variabele doorgeeft (zoals **& pFormat**) aan een methode.  

#### <a name="iadhelper-interface"></a>IADHelper Interface  

```  
__interfaceIADHelper : IUnknown  
{  
    HRESULT Init(ILogger *pLogger);  
    HRESULT ValidLogon(LPCTSTR userName, LPCTSTR password, LPCTSTR domain);  
    HRESULT HasAccess(LPCTSTR username, LPCTSTR password, LPCTSTR domain, LPCTSTR computerName, LPCTSTR accountDomain);  
};  

```  

##### <a name="hresult-initilogger-plogger"></a>HRESULT Init(ILogger \*pLogger)  
 Dit onderdeel doorgeven aan het logboek, zodat het gegevens kan vastleggen initialiseren.  

##### <a name="hresultvalidlogonlpctstr-username-lpctstr-password-lpctstr-domain"></a>HRESULTValidLogon (LPCTSTR gebruikersnaam, wachtwoord LPCTSTR, LPCTSTR domein)  
 Deze methode wordt gecontroleerd of een set referenties geldig, is zoals in tabel 10.  

### <a name="table-10-hresultvalidlogon"></a>Tabel 10. HResultValidLogon  

|**HResult**|**Beschrijving**|  
|-|-|  
|S_OK|Referenties zijn geldig|  
|S_FALSE|Referenties zijn niet geldig|  
|E_FAIL|Kan de domeincontroller; niet vinden Controleer de logboeken voor meer informatie|  

##### <a name="hresult-hasaccesslpctstr-username-lpctstr-password-lpctstr-domain-lpctstr-computername-lpctstr-accountdomain"></a>HRESULT HasAccess(LPCTSTR username, LPCTSTR password, LPCTSTR domain, LPCTSTR computerName, LPCTSTR accountDomain)  
 Deze methode wordt gecontroleerd of een set referenties lezen/schrijven toegang tot het computerobject in AD DS heeft, zoals in tabel 11.  

### <a name="table-11-hresult-hasaccess"></a>Tabel 11. HResult HasAccess  

|**HRESULT**|**Beschrijving**|  
|-|-|  
|S_OK|De gebruiker heeft toegang|  
|E_FAIL|De gebruiker heeft geen toegang. Controleer het logboekbestand voor meer informatie.|  

#### <a name="ibackgroundtask-interface"></a>IBackgroundTask-Interface  

```  
__interface IBackgroundTask : IUnknown  
{  
    HRESULT Init(ITask *pTask, int id, IBackgroundCallback *pCallback);  
    void Start(void);  
    BOOL Running(void);  
    HRESULT Wait(DWORD waitMilliseconds);  
    HRESULT Terminate(DWORD exitCode);  
    HRESULT GetExitCode(LPDWORD pCode, HRESULT *pHresult);  
    HRESULT Close(void);  
};  
```  

##### <a name="overview"></a>Overzicht  
 De **voortgang** pagina gebruikt deze klasse voor het uitvoeren van taken op een afzonderlijke thread. U kunt deze klasse als u wilt bewerkingen uitvoeren op een afzonderlijke thread. *Taken* zijn van een klasse die ondersteuning biedt voor de **ITask** interface.  

 Deze interface is geïmplementeerd door de **ID_BackgroundTask** ('Microsoft.Wizard.BackgroundTask') onderdeel, dat is gedefinieerd in de interface IBackgroundTask.h.  

##### <a name="hresult-inititask-ptask-int-id-ibackgroundcallback-pcallback"></a>HRESULT Init(ITask \*pTask, int id, IBackgroundCallback \*pCallback)  
 Deze interface initialiseert het onderdeel, zoals in tabel 12.  

### <a name="table-12-hresult-init"></a>Tabel 12. HRESULT Init  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**pTask**|Verwijzing naar de klasse met de code die u wilt uitvoeren op een andere thread|  
|**Id**|Een getal dat u in de callback gebruiken kunt **voltooid** methode om te zien welke taak is voltooid; handig als u verschillende taken die met de dezelfde retouraanroepmethode beginnen|  
|**pCallback**|Een klasse die implementeert de **voltooid** methode, die wordt aangeroepen wanneer een taak is voltooid; de aanroep van de **voltooid** methode bevindt zich op de achtergrondthread, niet de UI-thread|  

##### <a name="void-startvoid"></a>VOID Start(void)  
 Deze methode start u de taak in een achtergrondthread en retourneert de elementen in de tabel 13 wordt weergegeven.  

### <a name="table-13-return-background-thread"></a>Tabel 13. Achtergrondthread retourneren  

|**retourneert**|**Beschrijving**|  
|-|-|  
|**E_INVALIDARG**|De taak wordt al uitgevoerd, zodat u deze nu niet starten.|  
|**E_FAIL**|Er is een probleem met het starten van de thread.|  
|**S_OK**|De thread is gestart.|  

##### <a name="bool-running"></a>BOOL Running()  
 Deze methode retourneert TRUE als de taak op de achtergrond actief is en FALSE als deze niet wordt uitgevoerd.  

##### <a name="hresult-waitdword-waitmilliseconds"></a>HRESULT Wait(DWORD waitMilliseconds)  
 Deze methode wordt gewacht totdat de thread is gestopt of het aantal milliseconden is verstreken.  

##### <a name="hresult-terminatedword-exitcode"></a>HRESULT Terminate(DWORD exitCode)  
 Deze methode is funest de thread die wordt uitgevoerd (Zie tabel 14 en tabel 15). Dit proces duurt een korte tijd om te voltooien nadat deze methode retourneert.  

### <a name="table-14-hresult-terminate-exit-code"></a>Tabel 14. HRESULT afsluitcode beëindigen  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**exitCode**|De afsluitcode die worden verzonden naar de voltooide retouraanroepmethode, ook beschikbaar via worden de **GetExitCode** methode.|  

### <a name="table-15-termination-codes"></a>Tabel 15. Beëindiging  

|**retourneert**|**Beschrijving**|  
|-|-|  
|**E_FAIL**|De oproep te beëindigen is mislukt.|  
|**S_OK**|De aanvraag te beëindigen van de thread is voltooid.|  

##### <a name="hresult-getexitcodelpdword-pcode-hresult-phresult"></a>HRESULT GetExitCode(LPDWORD pCode, HRESULT \*pHresult)  
 Gebruik deze methode om de resultaten van de taak uitgevoerd op de achtergrondthread (Zie tabel 16).  

### <a name="table-16-result-codes"></a>Tabel 16. Resultaatcodes  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**pCode**|Verwijzing naar een **DWORD** die worden ingesteld van return of **nullptr** als u niet de retourwaarde hoeft. Bij afsluiten deze parameter is ingesteld op **STILL_ACTIVE** als de thread wordt uitgevoerd, wordt de code die wordt geretourneerd door de taak **Execute** methode, of de waarde die is doorgegeven aan de **beëindigen** methode als u hebt deze methode wordt aangeroepen.|  
|**pHresult**|Verwijzing naar een **HRESULT** die worden ingesteld van return of **nullptr** als u niet hoeft de **HRESULT** waarde.|  

##### <a name="hresult-closevoid"></a>HRESULT Close(void)  
 Deze methode versies de achtergrondthread. Deze retourneert **E_INVALIDARG** als de thread wordt uitgevoerd en **S_OK** anders.  

#### <a name="icheckbox-interface"></a>ICheckBox Interface  

```  
__interface ICheckBox : IControl  
{  
    void Check(BOOL check);  
    BOOL IsButtonChecked();  
};  
```  

##### <a name="void-checkbool-check"></a>Ongeldige cheque (BOOL controle)  
 Stel de ingeschakelde status van het selectievakje in. Als de methode TRUE is, wordt het selectievakje ingeschakeld; Wanneer de methode FALSE is, is het selectievakje is uitgeschakeld.  

##### <a name="bool-isbuttonchecked"></a>BOOL IsButtonChecked()  
 Deze methode rapporteert de huidige status van een selectievakje.  

#### <a name="icombobox-interface"></a>IComboBox Interface  

```  
__interface IComboBox : IControl  
{  
    HRESULT Bind([in] IBindableList *pList);  
    HRESULT Select(int index);  
    int Selected(void);  
    void Add([in] LPCTSTR caption);  
    HRESULT GetText([out, retval] LPBSTR pText);  
    void Clear();  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **CheckBoxWrapper** onderdeel. Ophalen van een exemplaar van dit onderdeel met behulp van de **GetControlWrapper** Help-functie met het type **CONTROL_COMBO_BOX**.  

##### <a name="hresult-bindin-ibindablelist-plist"></a>HRESULT Bind([in] IBindableList \*pList)  
 Gebruik deze methode wanneer u een gegevensbron hebben waarbij implementeert de **IBindableList** interface. De keuzelijst met invoervak initialiseert de inhoud met de bijschriften uit deze lijst.  

##### <a name="hresult-selectint-index"></a>HRESULT Select(int index)  
 Selecteer het item in de keuzelijst met invoervak bij de index.  

##### <a name="int-selectedvoid"></a>int Selected(void)  
 Deze methode retourneert de index van het geselecteerde item of **-1** als er niets is geselecteerd.  

##### <a name="void-addin-lpctstr-caption"></a>VOID toevoegen ([in] LPCTSTR bijschrift)  
 Een item handmatig toevoegen aan de keuzelijst met invoervak.  

##### <a name="hresult-gettextout-retval-lpbstr-ptext"></a>HRESULT GetText([out, retval] LPBSTR pText)  
 De tekenreeks van het momenteel geselecteerde item in de keuzelijst met invoervak worden opgehaald.  

##### <a name="void-clear"></a>Clear() VOID  
 Alle items in de keuzelijst met invoervak verwijderen.  

#### <a name="icontrol-interface"></a>IControl-Interface  

```  
__interface IControl : IUnknown  
{  
    HRESULT SetEnable(BOOL enable);  
    BOOL IsEnabled(void);  
    HRESULT SetVisible(BOOL visible);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **ControlWrapper** onderdeel. Ophalen van een exemplaar van dit onderdeel met behulp van de **GetControlWrapper** Help-functie met het type **CONTROL_GENERIC**.  

##### <a name="hresult-setenablebool-enable"></a>HRESULT SetEnable(BOOL enable)  
 In- of uitschakelen van het besturingselement.  

##### <a name="bool-isenabledvoid"></a>BOOL IsEnabled(void)  
 Retourneert waar als het besturingselement is ingeschakeld, FALSE als dit niet.  

##### <a name="hresult-setvisiblebool-visible"></a>HRESULT SetVisible(BOOL visible)  
 Weergeven of verbergen van het besturingselement.  

#### <a name="icpuinfo-interface"></a>ICpuInfo-Interface  

```  
__interface ICpuInfo : IUnknown  
{  
    BOOL Is64Bit(void);  
};  
```  

##### <a name="overview"></a>Overzicht  
 U deze interface verkrijgen door het maken van een nieuw **ID_CpuInfo** onderdeel. De enkele methode rapporten of de CPU is 32 of 64-bits. Houd er rekening mee dat als u een 32-bits besturingssysteem op een 64-bits computer hebt, deze methode TRUE retourneert, omdat het rapport is alleen de breedte van de CPU (niet het besturingssysteem).  

##### <a name="idirectory-interface"></a>IDirectory Interface  

```  
__interface IDirectory : IUnknown  
{  
    BOOL FileExists(LPCWSTR name);  
    BOOL FindFirst([in] LPCWSTR name);  
    HRESULT FoundName([out, retval] LPBSTR name);  
    DWORD FoundAttributes(void);  
    BOOL FindNext(void);  
    void FinishFind(void);  
};  
```  

###### <a name="overview"></a>Overzicht  
 De **Directory** onderdeel, dat u maakt met **ID_Directory**, biedt een façade voor het werken met mappen in het bestandssysteem.  

###### <a name="bool-fileexistslpcwstr-name"></a>BOOL FileExists(LPCWSTR name)  
 Deze methode retourneert waar als er een bestand met de naam die u opgeeft.  

###### <a name="bool-findfirstin-lpcwstr-name"></a>BOOL FindFirst([in] LPCWSTR name)  
 Deze methode zoeken naar eerste overeen met de naam die u opgeeft. Het ondersteunt jokertekens en retourneert de namen van bestands- en mapnamen. De methode retourneert TRUE als een overeenkomst is gevonden, FALSE anders.  

###### <a name="hresult-foundnameout-retval-lpbstr-name"></a>HRESULT FoundName([out, retval] LPBSTR name)  
 Deze methode haalt de naam van het bestand gevonden met een aanroep naar **FindFirst** of **FindNext**.  

###### <a name="dword-foundattributesvoid"></a>DWORD FoundAttributes(void)  
 Deze methode retourneert het kenmerk voor de meest recente gevonden bestand of map. U kunt de code als volgt gebruiken om te controleren of het is een map:  

```  
pDirectory->FoundAttributes() & FILE_ATTRIBUTE_DIRECTORY  
```  

###### <a name="bool-findnextvoid"></a>BOOL FindNext(void)  
 De volgende zoeken. Deze methode retourneert TRUE als een andere overeenkomst gevonden, FALSE anders is.  

###### <a name="void-finishfindvoid"></a>VOID FinishFind(void)  
 Deze methode versies resources die worden gebruikt voor de zoekbewerking.  

#### <a name="idomainjoinvalidator-interface"></a>IDomainJoinValidator-Interface  

```  
__interface IDomainJoinValidator : IUnknown  
{  
    HRESULT Init(ILogger *pLogger, IWizardPageContainer *pContainer, IStaticText *pUsername, IStaticText *pPassword, IStaticText *pComputerName);  
    HRESULT IsUsernameValid(LPCWSTR domainName);  
    BOOL CanModifyComputerAdEntry(LPCWSTR domainName);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Verkrijgen van een exemplaar van deze interface met de **ID_DomainJoinValidator** van waarde naar de **CreateInstance** sjabloonfunctie.  

##### <a name="hresult-initilogger-plogger-iwizardpagecontainer-pcontainer-istatictext-pusername-istatictext-ppassword-istatictext-pcomputername"></a>HRESULT Init (ILogger \*pLogger, IWizardPageContainer \*pContainer, IStaticText \*pUsername, IStaticText \*pPassword, IStaticText \*pComputerName)  
 Het exemplaar, zoals wordt weergegeven in de tabel 17 worden geïnitialiseerd.  

### <a name="table-17-hresult-init---instance-initialization"></a>Tabel 17. HRESULT Init - exemplaar initialisatie  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**pLogger**|Het logboek-exemplaar beschikbaar op de pagina via de pagina is **berichtenlogboek** methode|  
|**pContainer**|Geeft de resultaten van uw pagina **Container** methode|  
|**pUsername**|Het tekstvak met de naam van de gebruiker moet worden gevalideerd|  
|**pPassword**|Het tekstvak met het wachtwoord moet worden gevalideerd|  
|**PComputerName**|Het tekstvak met de naam van de computer die uiteindelijk wordt gekoppeld aan het domein|  

##### <a name="hresult-isusernamevalidlpcwstr-domainname"></a>HRESULT IsUsernameValid(LPCWSTR domainName)  
 Deze methode maakt gebruik van de **IADHelper -> ValidLogon** methode voor het werk. Zie die methode voor meer informatie.  

##### <a name="bool-canmodifycomputeradentrylpcwstr-domainname"></a>BOOL CanModifyComputerAdEntry(LPCWSTR domainName)  
 Controleer of de gebruiker de rechten voor het wijzigen van de vermelding van de computer heeft. De meeste van het werk wordt uitgevoerd door **IADHelper -> HasAccess**. Als deze methode onwaar retourneert, controleert u het logboekbestand voor meer informatie.  

#### <a name="idrivelist-interface"></a>IDriveList-Interface  

```  
__interface IDriveList : IUnknown  
{  
    HRESULT Init(IWmiRepository *pWmi);  
    HRESULT SetWhereClause(LPCTSTR whereClause);  
    HRESULT SetMinimumDriveSize(__int64 size);  
    HRESULT Update(void);  
    HRESULT AddProperty(ENUM_DISK_QUERY_SECTION section, LPCTSTR propName, LPCTSTR propNameReturned);  

    size_t Count(void);  
    HRESULT GetProperty(size_t index, LPCTSTR propName,  LPVARIANT value);  
    HRESULT GetCaption(size_t index,  LPBSTR pCaption);  
}  
```  

##### <a name="hresult-initiwmirepository-pwmi"></a>HRESULT Init(IWmiRepository \*pWmi)  
 Deze methode aanroepen voordat u andere onderdelen aanroepen. U moet een nieuwe maken **WmiRepository** voordat u deze methode niet aanroepen.  

##### <a name="hresult-setwhereclauselpctstr-whereclause"></a>HRESULT SetWhereClause(LPCTSTR whereClause)  
 Deze methode kunt u de tekst die wordt weergegeven als een 'where'-component in de query toe te voegen. De volgende regel resulteert bijvoorbeeld alleen USB-stations:  

```  
pDrives->SetWhereClause(L"WHERE InterfaceType='USB'");  
```  

##### <a name="hresult-setminimumdrivesizeint64-size"></a>HRESULT SetMinimumDriveSize (\__int64 grootte)  
 Stel de schijfgrootte minimaliseren in bytes, voor schijven die worden geretourneerd van de query.  

##### <a name="hresult-updatevoid"></a>HRESULT Update(void)  
 De query worden uitgevoerd. De lijst station beschikbaar is na het aanroepen van deze methode is gesorteerd op de stationsletter.  

##### <a name="hresult-addpropertyenumdiskquerysection-section-lpctstr-propname-lpctstr-propnamereturned"></a>HRESULT AddProperty(ENUM_DISK_QUERY_SECTION section, LPCTSTR propName, LPCTSTR propNameReturned)  
 Deze methode wordt de namen van extra eigenschappen die u beschikbaar wilt maken in de queryresultaten. Roep deze methode aan voordat u **Update**. Tabel 18 bevat drie van de nuttige eigenschappen.  

### <a name="table-18-hresult-addproperty-useful-properties"></a>Tabel 18. AddProperty HRESULT: Nuttige eigenschappen  

|**Sectie**|**Eigenschap**|**Beschrijving**|  
|-|-|-|  
|**DISKQUERY_LOGICALDISK**|**Grootte**|De grootte in bytes, weergegeven als een tekenreeks|  
|**DISKQUERY_DISKPARTITION**|**DiskIndex**|Het schijfnummer als een geheel getal, te beginnen met 0|  
|**DISKQUERY_LOGICALDISK**|**VolumeName**|De volumenaam|  

##### <a name="sizet-countvoid"></a>size_t Count(void)  
 Het aantal records de query retourneert. Roep **Update** voordat u deze methode niet aanroepen.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propname--lpvariant-value"></a>HRESULT GetProperty(size_t index, LPCTSTR propName, LPVARIANT value)  
 Deze methode haalt de waarde van een eigenschap van de resultaten van de query, zoals wordt weergegeven in de tabel 19.  

### <a name="table-19-hresult-getproperty"></a>Tabel 19. HRESULT GetProperty  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Index**|Op nul gebaseerde index van de resultaatrecord|  
|**propName**|Naam van de eigenschap, zoals 'Grootte'|  
|**Waarde**|Bij resultaat bevat deze parameter een variant-waarde van de eigenschap|  

##### <a name="hresult-getcaptionsizet-index--lpbstr-pcaption"></a>HRESULT GetCaption(size_t index, LPBSTR pCaption)  
 Deze methode haalt het bijschrift voor een record rschakelen hetzelfde als is de **bijschrift** eigenschap.  

#### <a name="iimagelist-interface"></a>IImageList-Interface  

```  
__interface IImageList  
{  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    HImageList GetImageList(void);  
    int AddImage(HInstance hInstance, int resourceId);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **ImageList** onderdeel. Ophalen van een exemplaar van dit onderdeel uit de **IListView** interface.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 Maak een nieuwe afbeeldingenlijst dit onderdeel wordt beheerd. Deze methode wordt slechts één keer aanroepen.  

##### <a name="himagelist-getimagelistvoid"></a>HImageList GetImageList(void)  
 Deze methode retourneert de ingang voor de lijst met afbeeldingen geval moet u andere bewerkingen uitvoeren op de lijst met afbeeldingen.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage (HInstance hInstance, int resourceId)  
 Een nieuwe installatiekopie naar de lijst met afbeeldingen toevoegen van een resource, zoals in tabel 20.  

### <a name="table-20-hresult-iimagelist-interface"></a>Tabel 20. HRESULT IImageList Interface  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**hInstance**|Sessie-ingang van de module die de bitmapbron bevat|  
|**resourceId**|ID van de resource te laden in de lijst met afbeeldingen|  

#### <a name="ilistview-interface"></a>IListView Interface  

```  
__interface IListView : IControl  
{  
    int AddItem([in] LPCTSTR text);  
    int AddColumn(int width, [in] LPCTSTR text);  
    HRESULT SetSubItem(int index, int column, [in] LPCTSTR text);  
    int GetWidth(void);  
    void SetExtendedStyle(DWORD style);  
    int GetSelectedItem(void);  
    HRESULT SelectItem(int index);  
    BOOL IsItemChecked(int index);  
    int GetItemCount(void);  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    int AddImage(HINSTANCE hInstance, int resourceId);  
    HRESULT SetImage(int index, int imageIndex);  
    HRESULT Clear(void);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **ControlWrapper** onderdeel. Ophalen van een exemplaar van dit onderdeel met behulp van de **GetControlWrapper** Help-functie met het type **CONTROL_LIST_VIEW**.  

##### <a name="int-additemin-lpctstr-text"></a>int AddItem ([in] LPCTSTR tekst)  
 Een nieuwe rij toegevoegd aan de keuzelijst. De methode retourneert de index van het item is zojuist toegevoegd.  

##### <a name="int-addcolumnint-width-in-lpctstr-text"></a>int AddColumn (int breedte, LPCTSTR tekst [in])  
 Een nieuwe kolom toevoegen aan de lijstweergave.  

##### <a name="hresult-setsubitemint-index-int-column-in-lpctstr-text"></a>HRESULT SetSubItem(int index, int column, [in] LPCTSTR text)  
 De tekst instellen in een kolom dan de eerste kolom van de keuzelijst met invoervak, zoals in tabel 21.  

### <a name="table-21-hresult-setsubitem"></a>Tabel 21. HRESULT SetSubItem  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**index**|De index van het lijstitem dat u wilt wijzigen|  
|**column**|De index van de kolom die u wilt bijwerken. de eerste kolom is ingesteld met **AddItem**, twee kolommen en volgende worden ingesteld met deze methode|  
|**Tekst**|De tekenreeks in de kolom worden weergegeven|  

##### <a name="int-getwidthvoid"></a>int GetWidth(void)  
 Deze methode retourneert de breedte van het volledige tekst.  

##### <a name="void-setextendedstyledword-style"></a>VOID SetExtendedStyle(DWORD style)  
 Deze methode kunt u uitgebreide stijlen instellen in de lijst, bijvoorbeeld:  

```  
m_pList->SetExtendedStyle(LVS_EX_FULLROWSELECT);  
```  

##### <a name="int-getselecteditemvoid"></a>int GetSelectedItem(void)  
 Deze methode retourneert de index van de lijstweergave is geselecteerd.  

##### <a name="hresult-selectitemint-index"></a>HRESULT SelectItem(int index)  
 Het geselecteerde item in de lijst voor deze index instellen.  

##### <a name="bool-isitemcheckedint-index"></a>BOOL IsItemChecked(int index)  
 Deze methode retourneert waar als een item in de lijst is geselecteerd. Deze methode moet u aanroepen **SetExtendedStyle** stelt u het selectievakje.  

##### <a name="int-getitemcountvoid"></a>int GetItemCount(void)  
 Deze methode retourneert het aantal items in de lijstweergave.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 Maak een nieuwe installatiekopie-lijst, en voeg dit naar de lijstweergave.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage (HINSTANCE hInstance, int resourceId)  
 Een afbeelding toevoegen aan de lijst met afbeeldingen voor de lijstweergave. U moet aan te roepen **CreateImageList**, eerste.  

##### <a name="hresult-setimageint-index-int-imageindex"></a>HRESULT SetImage(int index, int imageIndex)  
 De afbeelding die wordt weergegeven aan de linkerkant voor een specifieke lijstweergave-item in te stellen.  

##### <a name="hresult-clearvoid"></a>HRESULT Clear(void)  
 Alle objecten in de lijst verwijderd.  

#### <a name="iprogressbar-interface"></a>IProgressBar Interface  

```  
__interface IProgressBar : IControl  
{  
    HRESULT SetPercentage(int position);  
    int GetPercentage(void);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **ProgressBarWrapper** onderdeel. Ophalen van een exemplaar van dit onderdeel met behulp van de **GetControlWrapper** Help-functie met het type **CONTROL_PROGRESS_BAR**.  

##### <a name="hresult-setpercentageint-position"></a>HRESULT SetPercentage(int position)  
 Stel de positie van de voortgangsbalk met behulp van een getal tussen 0 en 100 liggen. Nieuwe Win32® staven hebben standaard een maximale bereik van 100.  

##### <a name="int-getpercentagevoid"></a>int GetPercentage(void)  
 Deze methode retourneert de huidige positie van de voortgangsbalk.  

#### <a name="iradiobutton-interface"></a>IRadioButton Interface  

```  
__interface IRadioButton : IControl  
{  
public:  
    void SetGroup(int firstId, int lastId);  
    void CheckRadio(int id);  
    BOOL IsButtonChecked(int id);  
    void EnableRadio(int id, BOOL enable);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **RadioButtonWrapper** onderdeel. Ophalen van een exemplaar van dit onderdeel met behulp van de **GetControlWrapper** Help-functie met het type **CONTROL_RADIO_BUTTON**.  

##### <a name="void-setgroupint-firstid-int-lastid"></a>VOID SetGroup (int eerste-id., int lastId)  
 De wrapper die is voorzien van het bereik van keuzerondjes die moeten worden behandeld als een groep. Deze methode niet aanroepen voordat u aanroepen **CheckRadio**.  

##### <a name="void-checkradioint-id"></a>VOID CheckRadio(int id)  
 Stel het specifieke keuzerondje één knop in de groep met keuzerondjes geselecteerd. Roep **SetGroup** voordat u deze methode aanroept.  

##### <a name="bool-isbuttoncheckedint-id"></a>BOOL IsButtonChecked(int id)  
 Deze methode retourneert TRUE als het keuzerondje momenteel is geselecteerd, FALSE anders.  

##### <a name="void-enableradioint-id-bool-enable"></a>VOID EnableRadio (int-id, BOOL inschakelen)  
 Deze methode of een keuzerondje uitgeschakeld.  

#### <a name="istatictext-interface"></a>IStaticText-Interface  

```  
__interface IStaticText : IControl  
{  
    HRESULT SetText([in] LPCTSTR pText);  
    HRESULT GetText([out, retval] LPBSTR pText);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **StaticTextWrapper** onderdeel. Ophalen van een exemplaar van dit onderdeel met behulp van de **GetControlWrapper** Help-functie met het type **CONTROL_STATIC_TEXT**.  

##### <a name="hresult-settextin-lpctstr-ptext"></a>HRESULT SetText([in] LPCTSTR pText)  
 De tekst voor het besturingselement instellen.  

##### <a name="hresult-gettextout-retval-lpbstr-ptext"></a>HRESULT GetText([out, retval] LPBSTR pText)  
 Deze methode retourneert de huidige waarde van de tekst voor het besturingselement.  

####  <a name="ITaskinterface"></a> ITask-Interface  

```  
__interface IControl : IUnknown  
{  
    HRESULT Init(IStringProperties *pProperties, ISettingsProperties *pTaskSettings);  
    HRESULT Execute(LPDWORD pReturnCode);  
};  
```  

 Deze interface geïmplementeerd als u wilt dat uw onderdeel beschikbaar als een taak op de pagina voorbereidende of als u wilt gebruiken de **BackgroundTask** onderdeel voor het uitvoeren van werk in een achtergrondthread.  

 Hier volgen de onderdelen die u implementeert de **ITask** interface:  

-   ID_ShellExecuteTask, L"Microsoft.Wizard.ShellExecuteTask"  

-   ID_CopyFilesTask, L"Microsoft.Wizard.CopyFilesTask"  

-   ID_ACPowerTask, L"Microsoft.OSDRefresh.ACPowerTask"  

-   ID_WiredNetworkTask, L"Microsoft.SharedPages.WiredNetworkTask"  

##### <a name="init"></a>Init  

```  
HRESULT Init(IStringProperties *pProperties, ISettingsProperties *pTaskSettings)  
```  

 Als u een taak voor de voorbereidende pagina schrijft, moet u deze methode om te initialiseren van de taak aanroepen. Het .config-bestand bevatten XML-bestand dat kan er als volgt uitzien:  

```  
<Task DisplayName="Check Windows Scripting Host" Type="Microsoft.Wizard.ShellExecuteTask">  
  <Setter Property="filename">%windir%\system32\cscript.exe</Setter>  
  <Setter Property="parameters">Preflight\OSDCheckWSH.vbs</Setter>  
  <Setter Property="BitmapFilename">images\WinScriptHost.bmp</Setter>  
  <ExitCodes>  
    <ExitCode State="Success" Type="0" Value="0" Text="" />  
    <ExitCode State="Error" Type="-1" Value="*" Text="Windows Scripting Host not installed." />  
  </ExitCodes>  
</Task>  
```  

 De **pProperties** parameter biedt toegang tot de setter drie waarden, terwijl de **pTaskSettings** parameter biedt toegang tot de **taak** -element en onderliggende items. De meeste taken hoeft alleen te lezen van gegevens uit de **pProperties** parameter.  

#####  <a name="Execute"></a> uitvoeren  

```  
HRESULT Execute(LPDWORD pReturnCode)  
```  

 Hier is waar u de code schrijven waarmee de taak uitvoert. Deze methode als resultaat moet geven **S_OK** als er geen fouten zijn opgetreden en er kan een andere geretourneerd **HRESULT** als een fout opgetreden tijdens het uitvoeren van de taak. Anders dan de waarden **S_OK** deze methode retourneert maximaal worden vergeleken < fout\> elementen in de < ExitCodes\> sectie als u de voorbereidende pagina.  

 De **pReturnCode** parameter moet worden bijgewerkt met een getal dat de status van de taak rapporteert. Deze waarden worden vergeleken met de pagina preflights om < ExitCode\> elementen.  

#### <a name="itreeview-interface"></a>ITreeView Interface  

```  
__interface ITreeView : IControl  
{  
    void EnableCheckboxes(void);  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    int AddImage(HINSTANCE hInstance, int resourceId);  

    HTREEITEM AddItem(LPCTSTR text, HTREEITEM hParent = NULL);  
    void SetImage(HTREEITEM item, int image, int expandImage);  

    void Clear(void);  
    BOOL SetFirstVisible(HTREEITEM item);  
    BOOL SelectItem(HTREEITEM item);  
    void CheckItem(HTREEITEM item, UINT checkState);  
    HTREEITEM SelectedItem(void);  
    int SetItemHeight(SHORT height);  
    HRESULT EnableItem(HTREEITEM item, BOOL enable);  
    void Expand(HTREEITEM hItem, BOOL expand);  

    HTREEITEM GetChild(HTREEITEM hParent);  
    HTREEITEM GetParent(HTREEITEM hNode);  
    HTREEITEM GetNextItem(HTREEITEM hPrevious);  

    UINT IsChecked(HTREEITEM item);  
    BOOL IsEnabled(HTREEITEM item);  

    INT_PTR CommonControlEvent(WORD controlId, void* pInfo, BOOL *pCancel);  
    HRESULT SetEventHandler(ITreeViewEvent *pEventHandler);  

    void SetSelectedBackColor(COLORREF color);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **TreeViewWrapper** onderdeel. Ophalen van een exemplaar van dit onderdeel met behulp van de **GetControlWrapper** Help-functie met het type **CONTROL_TREE_VIEW**.  

##### <a name="void-enablecheckboxesvoid"></a>VOID EnableCheckboxes(void)  
 Deze methode Hiermee schakelt u de selectievakjes in de boomstructuur van de weergave door in te stellen de **TVS_CHECKBOXES** stijl.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 Een nieuwe lijst van de installatiekopie toevoegen aan de boomstructuur van de weergave. De **vlaggen** parameter wordt doorgegeven in de aanroep naar de **ImageList_Create** Win32-functie.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage (HINSTANCE hInstance, int resourceId)  
 Een afbeelding toevoegen aan de lijst met afbeeldingen van een resource (**resourceId**) in de module met de sessie-ingang **hInstance**.  

##### <a name="htreeitem-additemlpctstr-text-htreeitem-hparent--null"></a>HTREEITEM AddItem(LPCTSTR text, HTREEITEM hParent = NULL)  
 Een knooppunt toevoegen aan de structuurweergave. Het nieuwe knooppunt wordt toegevoegd op het hoogste niveau als **hParent** is NULL. Anders bieden de handle naar het bovenliggende item waar u het nieuwe item is toegevoegd. Deze methode retourneert de ingang naar het nieuwe item.  

##### <a name="void-setimagehtreeitem-item-int-image-int-expandimage"></a>VOID SetImage (HTREEITEM item, image int, int expandImage)  
 De afbeelding moet worden gebruikt voor een structuurweergave-item in te stellen. U kunt zowel de normale en de uitgevouwen afbeelding instellen.  

##### <a name="void-clearvoid"></a>VOID Clear(void)  
 Alle items in de structuurweergave verwijderen.  

##### <a name="bool-setfirstvisiblehtreeitem-item"></a>BOOL SetFirstVisible(HTREEITEM item)  
 Zorg ervoor dat de structuurweergave-item zichtbaar is. De structuurweergave wordt geschoven indien nodig om dit item zichtbaar te maken.  

##### <a name="bool-selectitemhtreeitem-item"></a>BOOL SelectItem(HTREEITEM item)  
 Het momenteel geselecteerde item ingesteld op het item dat u opgeeft. U kunt aanroepen **SetFirstVisible** hierna om ervoor te zorgen dat de zojuist geselecteerde item zichtbaar is.  

##### <a name="void-checkitemhtreeitem-item-uint-checkstate"></a>VOID CheckItem (HTREEITEM item, UINT checkState)  
 De methode stelt in feite de afbeelding die wordt weergegeven voor het selectievakje in de structuurweergave. Deze installatiekopieën zijn in een apart **ImageList** besturingselement dat de structuurweergave beheert. Standaard bevat deze lijst met afbeeldingen drie afbeeldingen, weergegeven in de tabel 22.  

### <a name="table-22void-checkitem-image-list-default"></a>Tabel 22. void CheckItem installatiekopie lijst standaard  

|**checkState**|**Beschrijving**|  
|-|-|  
|**0**|Lege|  
|**1**|Uitgeschakeld|  
|**2**|Geselecteerd|  

##### <a name="htreeitem-selecteditemvoid"></a>HTREEITEM SelectedItem(void)  
 Deze methode retourneert de ingang van de structuurweergave is geselecteerd.  

##### <a name="int-setitemheightshort-height"></a>int SetItemHeight (korte hoogte)  
 Deze methode wordt de hoogte van alle items in de boomstructuur van de weergave in pixels. Deze retourneert het vorige hoogte in pixels.  

##### <a name="hresult-enableitemhtreeitem-item-bool-enable"></a>HRESULT EnableItem(HTREEITEM item, BOOL enable)  
 Deze methode of één item in de boomstructuur uitgeschakeld. Een item met de onderliggende items uit te schakelen, wordt de onderliggende elementen niet uitschakelen.  

##### <a name="void-expandhtreeitem-hitem-bool-expand"></a>VOID uit te breiden (HTREEITEM hItem, BOOL expand)  
 Deze methode wordt uitgebreid of een knooppunt in de structuur wordt samengevouwen.  

##### <a name="htreeitem-getchildhtreeitem-hparent"></a>HTREEITEM GetChild(HTREEITEM hParent)  
 Deze methode retourneert het eerste onderliggende lid van een structuurweergave-item of NULL als er geen onderliggende elementen.  

##### <a name="htreeitem-getparenthtreeitem-hnode"></a>HTREEITEM GetParent(HTREEITEM hNode)  
 Deze methode retourneert de ingang van het bovenliggende item voor een knooppunt in de structuurweergave of NULL als het knooppunt op het hoogste niveau.  

##### <a name="htreeitem-getnextitemhtreeitem-hprevious"></a>HTREEITEM GetNextItem(HTREEITEM hPrevious)  
 U kunt deze methode niet aanroepen met een ingang die **GetChild** retourneert naar alle onderliggende elementen van een knooppunt doorlopen. Deze methode retourneert het volgende lid op hetzelfde niveau in de boomstructuur die dezelfde bovenliggende activiteit deelt.  

##### <a name="uint-ischeckedhtreeitem-item"></a>UINT IsChecked(HTREEITEM item)  
 Deze methode retourneert **0** als het structuurknooppunt voor de weergave niet is ingeschakeld en **1** als het.  

##### <a name="bool-isenabledhtreeitem-item"></a>BOOL IsEnabled(HTREEITEM item)  
 Deze methode retourneert TRUE als het structuurknooppunt voor de weergave is ingeschakeld, FALSE anders.  

##### <a name="intptr-commoncontroleventword-controlid-void-pinfo-bool-pcancel"></a>INT_PTR CommonControlEvent(WORD controlId, void* pInfo, BOOL \*pCancel)  
 Deze methode is alleen voor intern gebruik.  

##### <a name="hresult-seteventhandleritreeviewevent-peventhandler"></a>HRESULT SetEventHandler(ITreeViewEvent \*pEventHandler)  
 Deze methode niet aanroepen als u ontvangen wilt wanneer het geselecteerde item wordt gewijzigd of de gebruiker de status van een structuurweergave-item wordt gewijzigd. U moet implementeren de **ITreeViewEvent** in de component voor het ontvangen van de retouraanroepen.  

##### <a name="void-setselectedbackcolorcolorref-color"></a>VOID SetSelectedBackColor(COLORREF color)  
 De achtergrondkleur die wordt gebruikt voor het geselecteerde item wordt ingesteld.  

#### <a name="iwmiiteration-interface"></a>IWmiIteration-Interface  

```  
__interface IWmiIterator : IUnknown  
{  
    HRESULT Next(void);  
    HRESULT GetProperty(LPCTSTR propertyName, [out] LPVARIANT pValue);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Doorgaans gebruikmaken van deze interface, samen met **IWmiRepository**, als u werkt met WMI-aanroepen. De **IWmiIteration** interface kunt u de waarden die een query retourneert doorlopen.  

##### <a name="hresult-nextvoid"></a>HRESULT Next(void)  
 Verplaatsen naar het volgende item in de resultaten van de query, zoals wordt weergegeven in de tabel 23.  

### <a name="table-23-hresult-nextvoid-query-returns"></a>Tabel 23. HRESULT Next(void) Query retourneert  

|**HRRESULT**|**Beschrijving**|  
|-|-|  
|**S_OK**|Verplaatst naar het volgende resultaat; u kunt **GetProperty** ophalen eigenschappen van die resulteren.|  
|**S_FALSE**|Er zijn geen items meer in de lijst.|  
|**E_NOT_SET**|Er zijn geen queryresultaten|  

##### <a name="hresult-getpropertylpctstr-propertyname-out-lpvariant-pvalue"></a>HRESULT GetProperty(LPCTSTR propertyName, [out] LPVARIANT pValue)  
 Deze methode haalt de waarde van een eigenschap van de huidige resultaatrecord, zoals wordt weergegeven in de tabel 24 en tabel 25.  

### <a name="table-24-hresult-getproperty"></a>Tabel 24. HRESULT GetProperty  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**propertyName**|Naam van de eigenschap die u wilt ophalen|  
|**pValue**|Verwijst naar een VARIANT-structuur die bij resultaat de waarde van eigenschap bevat|  

### <a name="table-25-hresult-getproperty-result"></a>Tabel 25. HRESULT GetProperty resultaat  

|**HRESULT**|**Beschrijving**|  
|-|-|  
|**S_OK**|Waarde van de eigenschap is opgehaald.|  
|**WBEM_E_NOT_FOUND**|Er is geen eigenschap met de naam.|  
|**E_NOT_VALID_STATE**|Er is geen huidige record.|  

> [!NOTE]
>  De **GetProperty** methode andere WMI-foutcodes dan degene die worden vermeld in de tabel 25 kan retourneren. De waarden die worden vermeld, zijn de algemene resultaten die zijn geretourneerd.  

#### <a name="iwmirepository-interface"></a>IWmiRepository-Interface  

```  
__interface IWmiRepository : IUnknown  
{  
    HRESULT SetNamespace(LPCWSTR namespaceName);  
    HRESULT ExecQuery(LPCWSTR query, [out] IWmiIterator **ppIterator);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **WmiRepository** onderdeel (**ID_WmiRepository**).  

##### <a name="hresult-setnamespacelpcwstr-namespacename"></a>HRESULT SetNamespace(LPCWSTR namespaceName)  
 Deze methode stelt de WMI-naamruimte die wordt gebruikt voor de query. Deze methode niet aanroepen voordat u aanroepen **ExecQuery**. Als u deze methode niet aanroepen wilt, worden de naamruimte root\cimv2. Deze methode retourneert altijd **S_OK**.  

##### <a name="hresult-execquerylpcwstr-query-out-iwmiiterator-ppiterator"></a>HRESULT ExecQuery(LPCWSTR query, [out] IWmiIterator **ppIterator)  
 Uitvoeren van een query op de WMI-naamruimte die is ingesteld met een aanroep naar **SetNamespace**, zoals wordt weergegeven in de tabel 26 en tabel 27.  

### <a name="table-26-hresult-execquery"></a>Tabel 26. HRESULT ExecQuery  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Query**|De tekenreeks voor de WMI-query die u wilt uitvoeren|  
|**ppIterator**|Een wijzer doorgeven aan een interface-aanwijzer die bij resultaat wordt ingevuld met een interface, zodat u toegang krijgt tot de queryresultaten|  

### <a name="table-27-hresult-query-result"></a>Tabel 27. Het queryresultaat HRESULT  

|**HRESULT**|**Beschrijving**|  
|-|-|  
|**S_OK**|Query is voltooid|  
|**Andere**|Als de query is mislukt, geeft u een WMI **HRESULT**|  

#### <a name="iformcontroller-interface"></a>IFormController-Interface  

```  
__interface IFormController : IUnknown  
{  
    Init(IWizardPageView *pView, IWizardPageContainer *pContainer);  
    SetPageInfo(ISettingsProperties *pPageInfo);  

    Validate(void);  

    AddToGroup(int groupControlId, int controlId);  
    UpdateCheckGroup(int groupControlId);  
    AddValidator(int controlId, IValidator *pValidator, IControl *pCOntrol = 0);  

    AddValidator(int controlId, LPCWSTR validatorId, LPCWSTR message, IValidator **ppValidator = nullptr);  
    DisableValidation(int controlId, BOOL disable);  

    AddField(LPCWSTR fieldName, int controlId, BOOL suppressLog, DialogControlTypes type);  
    AddRadioGroup(LPCWSTR groupName, int radioControlId);  
    EnableRadioGroup(LPCWSTR groupName, BOOL enable);  
    InitFields(IFieldCallback *pFieldCallback = nullptr);  
    SaveFields(IFieldCallback *pFieldCallback = nullptr);  
    BOOL IsFieldDisabled(int controlId);  

    InitSection(LPCWSTR key, LPCWSTR sectionCaption);  
    AddSummaryItem(LPCWSTR first, LPCWSTR second);  
    SuppressLogValue(LPCWSTR tsVariableName);  
    SaveText(int controlId, LPCWSTR tsVariableName, LPCWSTR summaryCaption);  
    LoadText(int controlId, LPCWSTR tsVariableName);  

    void ControlEvent(WORD eventId, WORD controlId);  
    BOOL IsValid(void);  
 };  
```  

##### <a name="overview"></a>Overzicht  
 Elke pagina in de Wizard UDI heeft een eigen formulier controller die deze interface implementeert. Deze domeincontroller kunt u verbinding maken met gegevens in het veld in het .config-XML-bestand van de besturingselementen op de pagina. De controller van het formulier wordt verwerkt veel van de details voor u.  

#####  <a name="SettingUptheForm"></a> Instellen van het formulier  
 Het algemeen, stelt u de controller van het formulier in uw pagina **OnWindowCreated** methode. Dus meestal doen omvat het aanroepen van de methoden die wordt weergegeven in de tabel 28.  

### <a name="table-28-onwindowcreated-method"></a>Tabel 28. OnWindowCreated methode  

|**Methode**|**Beschrijving**|  
|-|-|  
|**Init**|Initialiseert de formulier-controller|  
|**AddField**|Maakt een verbinding tussen een veld in het .config-XML-bestand dat is de tekenreeksnaam van een en een besturingselement in uw pagina dialoogvenster dat wordt een ID|  
|**AddRadioGroup**|Waarmee een keuzerondje verbinding met zowel een groep als een besturingselement in het dialoogvenster|  
|**AddToGroup**|Hiermee kunt u 'onderliggende'-besturingselementen die zijn ingeschakeld of uitgeschakeld samen met hun bovenliggende of op basis van welke keuzerondje is ingeschakeld|  
|**InitFields**|Nadat u alle hebt aangeroepen. Roep de **toevoegen** methoden voor het instellen van het formulier|  
|**valideren**|De eerste validatie uitvoert|  

##### <a name="processing-form-events"></a>Formulier verwerking van gebeurtenissen  
 Voeg de volgende aanroep uw **OnControlEvent** methode:  

```  
Form()->ControlEvent(eventId, controlId);  
```  

 Deze aanroep is geslaagd gebeurtenissen u aan bij de controller formulier zodat het formulier-gerelateerde gebeurtenissen kan verwerken.  

##### <a name="save-form-data"></a>Formuliergegevens opslaan  
 In de **OnNextClicked** methode en de methoden van het formulier wordt weergegeven in de tabel 29 aanroepen.  

### <a name="table-29-onnextclicked-method"></a>Tabel 29. OnNextClicked methode  

|**Methode**|**Beschrijving**|  
|-|-|  
|**InitSection**|Hier wordt de naam van de sectie die wordt weergegeven op de **samenvatting** pagina voor deze pagina|  
|**SaveFields**|Opslaan van veldwaarden takenreeksvariabelen en zo de **samenvatting** pagina|  

#####  <a name="Init"></a> Init  

```  
HRESULT Init(IWizardPageView *pView, IWizardPageContainer *pContainer)  
```  

 U meestal deze methode niet aanroepen in de buurt van het begin van uw pagina **OnWindowCreated** methode. De opdracht moet er ongeveer als volgt uitzien:  

```  
Form()->Init(View(), Container());  
```  

##### <a name="setpageinfo"></a>SetPageInfo  

```  
HRESULT SetPageInfo(ISettingsProperties *pPageInfo)  
```  

 Deze methode wordt aangeroepen, intern en u moet niet aangeroepen door uzelf. Het bevat XML van de pagina naar de controller formulier.  

##### <a name="validate"></a>valideren  

```  
HRESULT Validate(void)  
```  

 Deze methode voert de validatiefuncties die zijn gekoppeld aan besturingselementen. Als een validatiefunctie niet slaagt, de controller van het formulier een waarschuwingsbericht weergegeven en schakelt de **volgende** knop en klik vervolgens validatiefuncties verwerking stopt. Normaal gesproken hoeft u alleen te deze methode niet aanroepen aan het einde van uw **OnWindowCreated** methode; deze retourneert altijd **S_OK**.  

##### <a name="addtogroup"></a>AddToGroup  

```  
AddToGroup(int groupControlId, int controlId)  
```  

 Deze methode wordt een besturingselement als een onderliggend 'element' van een selectievakje of keuzerondje, zoals wordt weergegeven in de tabel 30. Deze onderliggende besturingselementen wordt uitgeschakeld wanneer het bovenliggende besturingselement niet is geselecteerd. De methode retourneert altijd **S_OK**.  

### <a name="table-30-addtogroup"></a>Tabel 30. AddToGroup  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**groupControlId**|De ID van het selectievakje of keuzerondje waarmee de status van het inschakelen van het onderliggende besturingselement|  
|**Controlld**|De ID van het besturingselement dat u wilt toevoegen als een onderliggend element|  

##### <a name="updatecheckgroup"></a>UpdateCheckGroup  

```  
HRESULT UpdateCheckGroup(int groupControlId)  
```  

 Deze methode updates inschakelen of uitschakelen van de status van een groep onderliggende besturingselementen op basis van de status van het bovenliggende besturingselement. In het algemeen hoeft niet deze methode niet aanroepen zelf, omdat de controller formulier voor u aangeroepen.  

##### <a name="addvalidator"></a>AddValidator  

```  
HRESULT AddValidator(int controlId, IValidator *pValidator, IControl *pControl = 0)  
```  

 Deze methode niet aanroepen alleen als u een validatiefunctie die u wilt maken in de code in plaats van met het XML-bestand hebt. Deze methode retourneert altijd **S_OK**.  

##### <a name="addvalidator"></a>AddValidator  

```  
HRESULT AddValidator(int controlId, LPCWSTR validatorId, LPCWSTR message, IValidator **ppValidator = nullptr)  
```  

 Deze methode niet aanroepen alleen als u een validatiefunctie die u wilt maken in de code in plaats van met het XML-bestand hebt.  

##### <a name="disablevalidation"></a>DisableValidation  

```  
HRESULT DisableValidation(int controlId, BOOL disable)  
```  

 Deze methode voor het expliciet uitschakelen validator voor een besturingselement of herstellen van de normale validatie aanroepen, zoals wordt weergegeven in de tabel 31. Deze methode is bijvoorbeeld handig wanneer u regels voor besturingselementen die niet met de formuliervalidatie van het worden behandeld in-of uitschakelen en u wilt valideren voor een besturingselement uitschakelen. Met andere woorden, u zou niet normaal gesproken deze methode niet aanroepen. Deze methode retourneert altijd **S_OK**.  

### <a name="table-31-hresult-disablevalidation"></a>Tabel 31. HRESULT DisableValidation  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**controlId**|Het besturingselement waarvan u wilt in- of uitschakelen van validatie|  
|**Uitschakelen**|Ingesteld op True in validatie uitschakelen en op FALSE om terug te zetten normale validatie|  

#####  <a name="AddField"></a> AddField  

```  
HRESULT AddField(LPCWSTR fieldName, int controlId, BOOL suppressLog, DialogControlTypes type)  
```  

 Toevoegen van een besturingselement toewijzing tussen de naam in een **veld** element van het .config-XML-bestand en de besturingselement-ID in het dialoogvenster voor uw pagina, zoals wordt weergegeven in de tabel 32. U moet deze methode voor de aanroep aanroepen **InitFields**omdat **InitFields** gebruikt deze informatie. Deze methode retourneert altijd **S_OK**.  

### <a name="table-32-hresult-addfield"></a>Tabel 32. HRESULT AddField  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Fieldname**|Naam van het veld zoals deze wordt weergegeven in uw pagina XML|  
|**controlId**|De ID van het besturingselement in de sjabloon voor uw pagina dialoogvensters|  
|**suppressLog**|Ingesteld op TRUE als u niet dat de waarden van dit veld is geschreven naar het logboekbestand wilt; Deze parameter altijd ingesteld op TRUE voor wachtwoord of PINCODE velden|  
|**Type**|Het type besturingselement, dat zich op een van de volgende:<br /><br /> -   **CONTROL_STATIC_TEXT**<br />-   **CONTROL_COMBO_BOX**<br />-   **CONTROL_LIST_VIEW**<br />-   **CONTROL_PROGRESS_BAR**<br />-   **CONTROL_GENERIC**<br />-   **CONTROL_RADIO_BUTTON**<br />-   **CONTROL_CHECK_BOX**<br />-   **CONTROL_TREE_VIEW**|  

#####  <a name="AddRadioGroup"></a> AddRadioGroup  

```  
HRESULT AddRadioGroup(LPCWSTR groupName, int radioControlId)  
```  

 Deze methode wordt een besturingselement toegevoegd aan een benoemde Keuzerondjesgroep, zoals wordt weergegeven in de tabel 33. Moet u dit nog aanroepen de **InitFields** methode, omdat deze methode maakt gebruik van kenmerken op het **groep met keuzerondjes** element om instellingen te beheren voor de keuzerondjes in de groep. Groepen keuzerondjes kunnen bijvoorbeeld worden vergrendeld zodat de keuzerondjes zijn uitgeschakeld, maar onderliggende besturingselementen zijn ingeschakeld of uitgeschakeld op basis van de welke keuzerondje is ingeschakeld. Deze methode retourneert altijd **S_OK**.  

### <a name="table-33-hresult-addradiogroup"></a>Tabel 33. HRESULT AddRadioGroup  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**groupName**|Een tekenreeks die een groep keuzerondjes op deze pagina definieert|  
|**radioControlId**|De ID van een enkele keuzerondje om toe te voegen aan deze groep|  

##### <a name="enableradiogroup"></a>EnableRadioGroup  

```  
HRESULT EnableRadioGroup(LPCWSTR groupName, BOOL enable)  
```  

 Deze methode kunt u in- of uitschakelen van een volledige Keuzerondjesgroep. Het uitschakelen van een groep met keuzerondjes schakelt alle het keuzerondje in de groep en eventuele onderliggende elementen van deze die zijn toegevoegd besturingselementen met keuzerondjes **AddToGroup**. Zie tabel 34 en 35 van de tabel.  

### <a name="table-34-enableradiogroup"></a>Tabel 34. EnableRadioGroup  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**groupName**|Naam van een groep met keuzerondjes die u al hebt gedefinieerd met een aanroep naar **AddRadioGroup**|  
|**Inschakelen**|Ingesteld op TRUE om in te schakelen voor de groep met keuzerondjes en FALSE uitschakelen van de groep|  

### <a name="table-35-hresult-enableradiogroup"></a>Tabel 35. HRESULT EnableRadioGroup  

|**HRESULT**|**Beschrijving**|  
|-|-|  
|**S_OK**|Groep ingeschakeld of uitgeschakeld|  
|**E_INVALIDARG**|Er is geen groep met keuzerondjes met de naam die u hebt opgegeven|  

#####  <a name="InitFields"></a> InitFields  

```  
HRESULT InitFields(IFieldCallback *pFieldCallback = nullptr)  
```  

 Voordat u deze methode aanroept, roepen **AddField** voor elk veld dat de XML-code kunt beheren. Deze methode retourneert altijd **S_OK**.  

 De **pFieldCallback** parameter is optioneel. Als u dit opgeeft, wordt de controller formulier roept **SetFieldDefault** voor besturingselementen die niet een **CONTROL_STATIC_TEXT** of **CONTROL_CHECK_BOX**. Dit gedrag kunt u een standaardwaarde ophalen uit het XML-bestand en stel deze in het besturingselement zelf.  

#####  <a name="SaveFields"></a> SaveFields  

```  
HRESULT SaveFields(IFieldCallback *pFieldCallback = nullptr)  
```  

 Deze methode bespaart veldwaarden takenreeksvariabelen en de gegevens van de samenvatting die wordt weergegeven op de **samenvatting** pagina. Bieden een wijzer in **pFieldCallback** kunt u voor het afhandelen van opgeslagen waarden voor besturingselementen die geen ondersteuning voor **CONTROL_STATIC_TEXT**.  

##### <a name="isfielddisabled"></a>IsFieldDisabled  

```  
BOOL IsFieldDisabled(int controlId)  
```  

 Deze methode kunt u bepalen of een veld is uitgeschakeld in het XML-bestand.  

#####  <a name="InitSection"></a> InitSection  

```  
HRESULT InitSection(LPCWSTR key, LPCWSTR sectionCaption)  
```  

 Deze methode initialiseert de overzichtsgegevens die wordt weergegeven op de **samenvatting** pagina, zoals wordt weergegeven in de tabel 36. Deze methode niet aanroepen uw **OnNextClicked** methode aan voordat u **SaveFields**. Deze methode retourneert altijd **S_OK**.  

### <a name="table-36-hresult-initsection"></a>Tabel 36. HRESULT InitSection  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Sleutel**|Deze parameter moet uniek zijn voor uw pagina. Wordt gebruikt om ervoor te zorgen dat elke pagina een eigen samenvattende informatie heeft.|  
|**sectionCaption**|De header die wordt weergegeven op de **samenvatting** pagina voor samenvattingsinformatie van deze pagina. Normaal gesproken gebruikt u **DisplayName()** als de waarde voor deze parameter.|  

##### <a name="addsummaryitem"></a>AddSummaryItem  

```  
HRESULT AddSummaryItem(LPCWSTR first, LPCWSTR second)  
```  

 Deze methode kunt u samenvatting items toevoegen aan de **samenvatting** pagina buiten deze items het XML-bestand in te stellen. Zie tabel 37.  

### <a name="table-37-hresult-addsummaryitem"></a>Tabel 37. HRESULT AddSummaryItem  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**eerste**|Het bijschrift voor de overzichtsitem die wordt weergegeven aan de linkerkant|  
|**Second**|De waarde die wordt weergegeven aan de rechterkant|  

##### <a name="suppresslogvalue"></a>SuppressLogValue  

```  
HRESULT SuppressLogValue(LPCWSTR tsVariableName)  
```  

 Deze methode niet aanroepen voor takenreeks variabelen die u niet wilt dat de waarden in het logboekbestand worden geschreven. Deze methode niet aanroepen voor taak takenreeksvariabelen die voor het opslaan van wachtwoorden, pincodes of andere gevoelige waarden van die een gebruiker kunt invoeren.  

##### <a name="savetext"></a>SaveText  

```  
HRESULT SaveText(int controlId, LPCWSTR tsVariableName, LPCWSTR summaryCaption)  
```  

 Deze methode bespaart de waarde van een besturingselement op een takenreeksvariabele en de samenvatting. Moet u doorgaans wordt niet aan deze methode niet aanroepen zelf, omdat de controller van het formulier dit voor alle velden wordt. Zie tabel 38.  

### <a name="table-38-hresult-savetext"></a>Tabel 38. HRESULT SaveText  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**controlId**|De ID van het tekstvak met de waarde die u wilt opslaan (of een ander besturingselement die tekst retourneren kan)|  
|**tsVariableName**|Naam van de takenreeksvariabele die u wilt wijzigen|  
|**summaryCaption**|Het bijschrift op de **samenvatting** pagina voor deze waarde|  

##### <a name="loadtext"></a>LoadText  

```  
HRESULT LoadText(int controlId, LPCWSTR tsVariableName)  
```  

 Deze methode leest de waarde van een takenreeksvariabele en wordt deze waarde ingesteld in het tekstvak.  

##### <a name="controlevent"></a>Enddialog  

```  
void ControlEvent(WORD eventId, WORD controlId)  
```  

 Deze methode niet aanroepen op uw **OnControlEvent** methode om ervoor te zorgen dat de controller formulier gebeurtenissen van besturingselementen moet doen om correct kan verwerken. De waarden die u aan deze methode doorgeeft zijn dezelfde waarden doorgegeven aan de **OnControlEvent** methode.  

##### <a name="isvalid"></a>IsValid  

```  
BOOL IsValid(void)  
```  

 Deze methode retourneert de status van de meest recente validatie van het formulier. Als een van de validatiefunctie besturingselement heeft een fout gerapporteerd, is deze methode retourneert onwaar. Met andere woorden, resulteert dit in waar alleen als alle besturingselementen op de pagina ongeldig zijn.  

#### <a name="ivalidator-interface"></a>IValidator-Interface  

```  
__interface IValidator : IUnknown  
{  
    HRESULT Init(IControl *pControl, LPCTSTR message);  
    HRESULT Init(IControl *pControl, IWizardPageContainer *pContainer, IStringProperties *pProperties);  
    BOOL, IsValid(LPBSTR pMessage);  
    HRESULT SetProperty(int propertyId, LPVARIANT pValue);  
    HRESULT SetProperty(int propertyId, IUnknown *pUnknown);  
    HRESULT SetProperty)(int propertyId, LPCTSTR pValue);  
};  
```  

##### <a name="overview"></a>Overzicht  
 *Validatiefuncties* onderdelen één besturingselement op de pagina kan valideren. De eenvoudigste manier voor het implementeren van een validatiefunctie is zodat deze een subklasse zijn van de **BaseValidator** klasse, die is gedefinieerd in het BaseValidator.h header-bestand.  

##### <a name="hresult-initicontrol-pcontrol-lpctstr-message"></a>HRESULT Init(IControl \*pControl, LPCTSTR message)  
 Als u een validatiefunctie in code maken, kunt u deze methode voor het initialiseren van de validatiefunctie kunt aanroepen. Zie tabel 39.  

### <a name="table-39-hresult-init"></a>Tabel 39. HRESULT Init  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**pControl**|Het besturingselement dat de validatiefunctie moet valideren|  
|**Bericht**|Het bericht dat wordt weergegeven op de pagina als het besturingselement niet geldig is|  

##### <a name="hresult-initicontrol-pcontrol-iwizardpagecontainer-pcontainer-istringproperties-pproperties"></a>HRESULT Init(IControl \*pControl, IWizardPageContainer \*pContainer, IStringProperties \*pProperties)  
 De controller formulier roept deze methode om te initialiseren validatiefuncties dat wordt gemaakt op basis van de XML van de pagina. Zie tabel 40.  

### <a name="table-40-hresult-init-method"></a>Tabel 40. HRESULT Init-methode  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**pControl**|Het besturingselement dat de validatiefunctie moet valideren|  
|**pContainer**|In geval uw validator heeft toegang tot het logboek of andere onderdelen maken|  
|**pProperties**|Biedt toegang tot de eigenschappen (elementen setter) voor de validatiefunctie|  

##### <a name="bool-isvalidlpbstr-pmessage"></a>BOOL, IsValid (LPBSTR pMessage)  
 Deze methode retourneert TRUE als het besturingselement is ongeldig of ONWAAR als het besturingselement ongeldig is. Op return **pMessage** moeten worden ingevuld met een nieuwe **BSTR** waarin het bericht moet worden weergegeven wanneer het besturingselement niet geldig is.  

##### <a name="hresult-setpropertyint-propertyid-lpvariant-pvalue"></a>HRESULT SetProperty(int propertyId, LPVARIANT pValue)  
 Als u extra waarden die niet beschikbaar zijn in het XML-bestand nodig hebt, kunt u deze methode implementeren.  

##### <a name="hresult-setpropertyint-propertyid-iunknown-punknown"></a>HRESULT SetProperty(int propertyId, IUnknown \*pUnknown)  
 Als u extra waarden die niet beschikbaar zijn in het XML-bestand nodig hebt, kunt u deze methode implementeren.  

##### <a name="hresult-setpropertyint-propertyid-lpctstr-pvalue"></a>HRESULT SetProperty) (int eigenschaps-id, LPCTSTR pValue)  
 Als u extra waarden die niet beschikbaar zijn in het XML-bestand nodig hebt, kunt u deze methode implementeren.  

#### <a name="iregex-interface"></a>IRegEx Interface  

```  
__interface IRegEx : IUnknown  
{  
    BOOL MatchesRegex(LPCTSTR input, LPCTSTR regex);  
    HRESULT GetMatch(size_t index, LPBSTR pValue);  
};  
```  

 Deze methode wordt geïmplementeerd door de **ID_Regex** onderdeel (IRegex.h) en biedt ondersteuning voor de verwerking van de reguliere expressie.  

##### <a name="bool-matchesregexlpctstr-input-lpctstr-regex"></a>BOOL MatchesRegex(LPCTSTR input, LPCTSTR regex)  
 Deze methode voert de reguliere expressie op basis van de ingevoerde tekst. Dit maakt gebruik van de C++ standard-bibliotheek **regex_match** functie moet het echte werk te doen. De methode retourneert TRUE als er overeenkomsten, FALSE anders waren.  

##### <a name="hresult-getmatchsizet-index-lpbstr-pvalue"></a>HRESULT GetMatch(size_t index, LPBSTR pValue)  
 Deze methode kunt u de overeenkomsten ophalen van de meest recente **MatchesRegex** aanroepen. Er is geen fout verwerking van deze methode, en wordt deze ofwel retourneert **S_OK** of er een uitzondering gegenereerd.  

#### <a name="isummaryinfo-interface"></a>ISummaryInfo-Interface  

```  
__interface ISummaryInfo : IUnknown  
{  
    size_t Count(void);  
    HRESULT Clear(void);  
    HRESULT AddInfo(LPCTSTR pFirst, LPCTSTR pSecond);  
    HRESULT GetInfo(size_t index, LPBSTR pFirst, LPBSTR pSecond);  
    HRESULT GetCaption(LPBSTR pCaption);  
    HRESULT SetCaption(LPCTSTR caption);  
};  
```  

 U hoeft niet rechtstreeks gebruik van deze interface. Gebruik in plaats daarvan **IFormController**.  

#### <a name="isummarybag"></a>ISummaryBag  

```  
__interface ISummaryBag : IUnknown  
{  
    size_t Count(void);  
    HRESULT GetInfoByIndex(size_t index, [out] ISummaryInfo **ppSummary);  
    HRESULT GetInfoByKey(LPCTSTR key, [out] ISummaryInfo **ppSummary);  
};  
```  

 U hoeft niet rechtstreeks gebruik van deze interface. Gebruik in plaats daarvan **IFormController**.  

#### <a name="itsvariablebag-interface"></a>ITSVariableBag Interface  

```  
__interface ITSVariableBag : IUnknown  
{  
    void GetValue([in] LPCTSTR variableName, [out] LPBSTR pValue);  
    void SetValue([in] LPCTSTR variableName, [in] LPCTSTR pValue);  
    void Clear(void);  
    HRESULT Remove([in] LPCTSTR variableName);  
    HRESULT SuppressLogValue([in] LPCTSTR variableName);  
    void Save(void);  
};  
```  

 Deze interface biedt toegang tot de takenreeksvariabelen. U hebt toegang tot deze interface met behulp van uw pagina **TSVariables()** methode.  

##### <a name="void-getvaluein-lpctstr-variablename-out-lpbstr-pvalue"></a>GetValue void ([in] LPCTSTR variableName LPBSTR pValue [out])  
 Deze methode leest de waarde van een takenreeksvariabele.  

> [!NOTE]
>  Waarden in de cache opgeslagen nadat de eerste gelezen.  

##### <a name="void-setvaluein-lpctstr-variablename-in-lpctstr-pvalue"></a>SetValue void ([in] LPCTSTR variableName LPCTSTR pValue [in])  
 Deze methode stelt u de waarde van een takenreeksvariabele. Deze waarde wordt opgeslagen in het geheugen. Taak sequence-waarden worden geschreven nadat u op **voltooien** in de Wizard UDI.  

##### <a name="void-clearvoid"></a>VOID Clear(void)  
 Deze methode worden alle taak sequence-waarden die zijn opgeslagen in het geheugen verwijderd.  

##### <a name="hresult-removein-lpctstr-variablename"></a>HRESULT Remove([in] LPCTSTR variableName)  
 Deze methode wordt de waarde van een specifieke taak sequence verwijderd uit het geheugen. De volgende keer dat u **GetValue** met dezelfde naam van de takenreeks, de methode probeert te halen uit de takenreeks.  

##### <a name="hresult-suppresslogvaluein-lpctstr-variablename"></a>HRESULT SuppressLogValue([in] LPCTSTR variableName)  
 Wanneer de takenreeksvariabelen worden geschreven, zoals wanneer u klikt op **voltooien** in de Wizard UDI de namen en waarden naar het logboekbestand worden geschreven. Deze methode om het vastleggen van gevoelige waarden, zoals wachtwoorden of pincodes, voor een specifieke takenreeksvariabele aanroepen.  

##### <a name="void-savevoid"></a>VOID Save(void)  
 Deze methode bespaart alle taak sequence-waarden die zijn ingesteld met aanroepen van **SetValue**.  

#### <a name="itsvariablerepository-interface"></a>ITSVariableRepository-Interface  

```  
__interface ITSVariableRepository : IUnknown  
{  
    void GetValue([in] LPCTSTR variableName, BOOL logValue, [out] LPBSTR pValue);  
    void SetValue([in] LPCTSTR variableName, BOOL logValue, [in] LPCTSTR value);  
};  
```  

 Deze interface is voor intern gebruik door **TSVariableBag** voor lezen en schrijven van takenreeksvariabelen.  

#### <a name="iwizardfinish-interface"></a>IWizardFinish-Interface  

```  
__interface IWizardFinish : IUnknown  
{  
    HRESULT Canceled(void);  
    HRESULT Finished(void);  
};  
```  

 Deze interface is handig in geavanceerde scenario's waarin u uitvoeren extra verwerking wilt wanneer u klikt op **voltooien** of **annuleren** in de Wizard UDI. De Wizard UDI bevat een **voltooien** taak waarmee takenreeksvariabelen worden opgeslagen wanneer u klikt op **voltooien**. Als u de wizard annuleert, wordt de taak alleen stelt de **OSDSetupWizCancelled** takenreeksvariabele in op TRUE en hoeft niet opslaan in een andere taak verandert takenreeksvariabelen.  

 Als u uw eigen onderdeel voltooien maakt, moet u bij de code als volgt registreren:  

```  
Register<MyFinishTaskFactory>(ID_MyFinishTask, pRegistry);  

PWizardFinish pFinish;  
CreateInstance(pRegistry, ID_MyFinishTask, &pFinish);  

PWizardFinishService pService;  
GetService<IWizardFinishService>(pRegistry, &pService);  

pService->Register(pFinish);  
```  

#### <a name="ibindablelist-interface"></a>IBindableList-Interface  

```  
__interface IBindableList : IUnknown  
{  
    size_t Count(void);  
    HRESULT GetCaption(size_t index, LPBSTR pCaption);  
};  
```  

 Deze interface implementeren als er een data source-component die u binden aan een keuzelijst met invoervak wilt door het aanroepen van de **binden** methode.  

##### <a name="sizet-countvoid"></a>size_t Count(void)  
 Deze methode retourneert het aantal items in de lijst.  

##### <a name="hresult-getcaptionsizet-index-lpbstr-pcaption"></a>HRESULT GetCaption(size_t index, LPBSTR pCaption)  
 Deze methode retourneert het bijschrift van het item op een specifieke index.  

#### <a name="idatanodes-interface"></a>IDataNodes-Interface  

```  
__interface IDataNodes : IUnknown  
{  
    size_t Count();  
    HRESULT SetCaptionProperty(LPCTSTR captionProperty);  
    HRESULT GetProperty(size_t index, LPCTSTR propertyName, [out] LPBSTR propertyValue);  
    HRESULT GetNode(size_t index, [out] ISettingsProperties **ppNode);  
};  
```  

 Deze interface biedt toegang tot hiërarchische gegevens die kunnen worden opgeslagen in een pagina. U deze interface via methoden verkrijgen op de **ISettingsProperties** interface, die beschikbaar is voor uw pagina via de **instellingen** methode.  

 Gegevens in een pagina XML kunt als volgt uitzien  

```  
      <Data Name="Network">  
        <DataItem>  
          <Setter Property="DisplayName">Public</Setter>  
          <Setter Property="Share">\\servername\Share</Setter>  
        </DataItem>  
        <DataItem>  
          <Setter Property="DisplayName">Dev Team</Setter>  
          <Setter Property="Share">\\servername\DevShare</Setter>  
        </DataItem>  
      </Data>  
```  

 Het aanroepen van **Settings() GetDataNode ('Netwerk' L & pData) ->** biedt u een **IDataNodes** -exemplaar met twee gegevensitems (die op zijn beurt heeft twee eigenschappen).  

##### <a name="sizet-count"></a>size_t Count()  
 Deze methode retourneert het aantal **DataItem** elementen.  

##### <a name="hresult-setcaptionpropertylpctstr-captionproperty"></a>HRESULT SetCaptionProperty(LPCTSTR captionProperty)  
 De component die ondersteuning biedt voor deze interface ondersteunt ook **IBindableList**, waardoor het eenvoudig voor het vullen van een keuzelijst met invoervak met gegevens van de XML van de pagina. Deze methode waarbij de eigenschap (setter) worden beheerd in elk **DataItem** element wordt gebruikt voor deze binding. Bijvoorbeeld, u kan deze methode aanroept met **DisplayName**, en wordt die eigenschap setter zou gebruiken voor gegevensbinding. De keuzelijst met invoervak bevat dan **openbare** en **Dev Team** als items.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propertyname-out-lpbstr-propertyvalue"></a>HRESULT GetProperty(size_t index, LPCTSTR propertyName, [out] LPBSTR propertyValue)  
 Deze methode krijgt u een eigenschap van een van de **DataItem** elementen. Zie tabel 41 en 42 tabel.  

### <a name="table-41-dataitem-getproperty"></a>Tabel 41. DataItem GetProperty  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Index**|De indexwaarde (te beginnen met 0) van de **DataItem** waarvoor u wilt een eigenschapswaarde ophalen|  
|**propertyName**|Naam van de setter-eigenschap die u wilt een waarde wordt opgehaald|  
|**propertyValue**|Bij resultaat, bevat de tekenreeks van een eigenschap|  

### <a name="table-42-hresult-getproperty"></a>Tabel 42. HRESULT GetProperty  

|||  
|-|-|  
|**HRESULT**|**Beschrijving**|  
|**S_OK**|De eigenschap is opgehaald.|  
|**E_INVALIDARG**|De index is voorbij het einde van de matrix.|  

##### <a name="hresult-getnodesizet-index-out-isettingsproperties-ppnode"></a>HRESULT GetNode(size_t index, [out] ISettingsProperties **ppNode)  
 Deze methode is vergelijkbaar met **GetProperty**, maar in plaats van een waarde van een **DataItem**, wordt de hele **DataItem** ingepakt een  **ISettingsProperties** interface. Zie tabel 43 en 44 van de tabel.  

### <a name="table-43-hresult-getnode"></a>Tabel 43. HRESULT GetNode  

|**Parameter**|**Beschrijving**|  
|-|-|  
|Index|De indexwaarde (te beginnen met 0) van de **DataItem** waarvoor u wilt een eigenschapswaarde ophalen|  
|**ppNode**|Bij het afsluiten, de **ISettingsProperties** interface die loopt de **DataItem** knooppunt|  

### <a name="table-44-hresult-getnode-results"></a>Tabel 44. HRESULT GetNode resultaten  

|**HRESULT**|**Beschrijving**|  
|-|-|  
|**S_OK**|Het knooppunt is opgehaald.|  
|**E_INVALIDARG**|De index is voorbij het einde van de matrix.|  

#### <a name="ifactoryregistry-interface"></a>IFactoryRegistry Interface  

```  
__interface IFactoryRegistry : IUnknown  
{  
    void Register(LPCTSTR type,  IClassFactory *pFactory);  
    HRESULT LoadAndRegister(LPCTSTR dllName, ILogger *pLogger);  
    BOOL Contains(LPCTSTR type);  
    HRESULT GetFactory(LPCTSTR type,  IClassFactory **ppFactory);  
    HRESULT CreateInstance(LPCTSTR type,  IUnknown **ppInstance);  
    HRESULT SetContainer(IWizardPageContainer *pContainer);  
    HRESULT RegisterService(REFGUID iid, IUnknown *pService);  
    HRESULT GetService(REFGUID iid,  IUnknown **ppService);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Wanneer u een nieuwe aangepaste pagina maakt, ten minste moet u maken een *pagina factory*: een klasse die implementeert **IClassFactory**. (U kunt **ClassFactoryImpl** als basisklasse voor uw gegevensfactory.)  

##### <a name="void-registerlpctstr-type--iclassfactory-pfactory"></a>VOID registreren (LPCTSTR type, IClassFactory \*pFactory)  
 Deze methode wordt een classfactory geregistreerd met het register. Zie tabel 45.  

### <a name="table-45-iclassfactory-void-register"></a>Tabel 45. IClassFactory void registreren  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Type**|Een tekenreeks die de factory aanduidt die u registreert; Deze parameter moet in het algemeen de naam van uw bedrijf hebben in de tekenreeks om ervoor te zorgen dat deze uniek is|  
|**pFactory**|Een verwijzing naar de factory-klasse-instantie|  

##### <a name="hresult-loadandregisterlpctstr-dllname-ilogger-plogger"></a>HRESULT LoadAndRegister(LPCTSTR dllName, ILogger \*pLogger)  
 Deze methode is alleen voor intern gebruik.  

##### <a name="bool-containslpctstr-type"></a>BOOL Contains(LPCTSTR type)  
 Deze methode wordt doorgaans gebruikt voor intern gebruik. Wordt gecontroleerd of een klasse-factory is geregistreerd voor een type.  

##### <a name="hresult-getfactorylpctstr-type--iclassfactory-ppfactory"></a>HRESULT GetFactory(LPCTSTR type, IClassFactory **ppFactory)  
 Deze methode kunt u de classfactory ophalen. Normaal gesproken roept u **CreateInstance**. Als u maken van een groot aantal hetzelfde onderdeel wilt, is het echter veel efficiënter de factory ophalen en vervolgens vraagt u het maken van de exemplaren die voor u.  

##### <a name="hresult-createinstancelpctstr-type--iunknown-ppinstance"></a>HRESULT CreateInstance(LPCTSTR type, IUnknown **ppInstance)  
 Deze methode maakt u een nieuw exemplaar van een onderdeel, het type opgegeven. Gebruik de **CreateInstance** sjabloon methode in plaats daarvan zodat kunt maken van het object van type-safe.  

##### <a name="hresult-setcontaineriwizardpagecontainer-pcontainer"></a>HRESULT SetContainer(IWizardPageContainer \*pContainer)  
 Deze methode is alleen voor intern gebruik.  

##### <a name="hresult-registerservicerefguid-iid-iunknown-pservice"></a>HRESULT RegisterService(REFGUID iid, IUnknown \*pService)  
 *Services* enkele exemplaren van een onderdeel dat kan worden gebruikt op meerdere plaatsen. U kunt deze methode gebruikt om een service op één pagina te registreren en vervolgens ophalen die hetzelfde exemplaar van een andere pagina.  

##### <a name="hresult-getservicerefguid-iid--iunknown-ppservice"></a>HRESULT GetService(REFGUID iid, IUnknown **ppService)  
 Deze methode wordt een service die eerder is geregistreerd met een aanroep naar RegisterService opgehaald.  

##### <a name="hresult-setlanguagelangid-languageid"></a>HRESULT SetLanguage(LANGID languageId)  
 Deze methode stelt u de taal van de Wizard UDI op de taal-id die u hebt opgegeven in de **taal-id** parameter.  

##### <a name="langid-getlanguage"></a>LANGID GetLanguage()  
 Deze methode retourneert de waarde van de taal-id die u opgaf met de **/locale** opdrachtregelparameter voor de Wizard UDI. De methode retourneert een van de volgende waarden:  

-   Waarde van de taal-id die is opgegeven met de **/locale** opdrachtregelparameter  

-   0 als u niet heeft verstrekt de **/locale** opdrachtregelparameter  

#### <a name="ilogger-interface"></a>ILogger Interface  

```  
__interface ILogger : IUnknown  
{  
    HRESULT Init(LPCWSTR logFilename);  
    HRESULT MoveLog(LPCWSTR logFilename);  
    HRESULT LogBase(EMessageType messageType, LPCTSTR component, SYSTEMTIME eventTime, LPCTSTR message);  
    HRESULT Log(EMessageType messageType, LPCTSTR component, LPCTSTR message);  
    HRESULT Error(HRESULT error, LPCTSTR component, LPCTSTR message);  
    HRESULT Error2(HRESULT error, LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Normal(LPCTSTR component, LPCTSTR message);      
    HRESULT Normal2(LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Verbose(LPCTSTR component, LPCTSTR message);  
    HRESULT Verbose2(LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Debug(LPCWSTR component, LPCWSTR message);  
    HRESULT EnableDebug(BOOL debug);  
    HRESULT Close(void);  
    HRESULT GetLogFilename(LPBSTR pFilename);  
};  
```  

##### <a name="overview"></a>Overzicht  
 De Wizard UDI registreert informatie in een logboekbestand, waardoor gevonden in het veld problemen. Het is een goed idee om uw pagina's om informatie te registreren. U kunt een verwijzing naar deze interface van verkrijgen in uw pagina met behulp van de pagina **Logger()** methode. Regels in het logboekbestand, wordt er een getal 'niveau' bevatten die de fout geeft, normaal, uitgebreid, of foutopsporingsberichten.  

> [!NOTE]
>  Foutopsporingsberichten worden niet opgeslagen in het logboekbestand tenzij ondersteuning voor foutopsporing is ingeschakeld. U kunt ondersteuning voor foutopsporing inschakelen door het toevoegen van de volgende regel om de **stijl** element in het .config-bestand:  

```  
<Setter Property="debug">true</Setter>  
```  

##### <a name="init"></a>Init  

```  
HRESULT Init(LPCWSTR logFilename)  
```  

 Deze methode is alleen voor intern gebruik.  

##### <a name="movelog"></a>MoveLog  

```  
HRESULT MoveLog(LPCWSTR logFilename)  
```  

 Deze methode is alleen voor intern gebruik.  

##### <a name="logbase"></a>LogBase  

```  
HRESULT LogBase(EMessageType messageType, LPCTSTR component, SYSTEMTIME eventTime, LPCTSTR message)  
```  

 Deze methode is alleen voor intern gebruik.  

##### <a name="log"></a>Logboek  

```  
HRESULT Log(EMessageType messageType, LPCTSTR component, LPCTSTR message)  
```  

 Deze methode is alleen voor intern gebruik.  

##### <a name="error"></a>Fout  

```  
HRESULT Error(HRESULT error, LPCTSTR component, LPCTSTR message)  
```  

 Deze methode als gegevens over een fout logboek wilt aanroepen. Zie tabel 46.  

### <a name="table-46-hresult-error"></a>Tabel 46. Fout HRESULT  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Fout**|De foutcode geretourneerd door een aanroep (u kunt deze code wordt weergegeven in de logboekvermelding als een getal.)|  
|**Component**|Een tekenreeks die de bron van de fout doorgaans wordt uw pagina of het onderdeel dat u hebt geschreven aangeeft|  
|**Bericht**|Het bericht waarin wordt uitgelegd wat de fout heeft veroorzaakt|  

#####  <a name="Error2"></a> error2  

```  
HRESULT Error2(HRESULT error, LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 Deze methode is vergelijkbaar met de **fout** methode maar kunt u een tweedelige bericht opgeven. Het laatste bericht hebben 'bericht' en 'Bericht2' in het bestand voor uitvoer. Dit is een methode gemak.  

##### <a name="normal"></a>Normaal  

```  
HRESULT Normal(LPCTSTR component, LPCTSTR message)  
```  

 Deze methode registreert een normale bericht. Zie de beschrijving van de [fout](#Error) methode voor parameters.  

##### <a name="normal2"></a>Normal2  

```  
HRESULT Normal2(LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 Deze methode registreert een normale bericht. Zie de beschrijving van de [Error2](#Error2) methode voor parameters.  

##### <a name="verbose"></a>Uitgebreid  

```  
HRESULT Verbose(LPCTSTR component, LPCTSTR message)  
```  

 Deze methode registreert een uitgebreid bericht. Zie de beschrijving van de [fout](#Error) methode voor parameters.  

##### <a name="verbose2"></a>Verbose2  

```  
HRESULT Verbose2(LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 Deze methode registreert een uitgebreid bericht. Zie de beschrijving van de [Error2](#Error2) methode voor parameters.  

##### <a name="debug"></a>Debug  

```  
HRESULT Debug(LPCWSTR component, LPCWSTR message)  
```  

 Deze methode Hiermee wordt een bericht voor foutopsporing. Zie de beschrijving van de [fout](#Error) methode voor parameters. Fouten opsporen in berichten worden niet opgeslagen in het bestand tenzij ingeschakeld. Zie de sectie overzicht voor meer informatie.  

##### <a name="enabledebug"></a>EnableDebug  

```  
HRESULT EnableDebug(BOOL debug)  
```  

 Deze methode is alleen voor intern gebruik.  

##### <a name="close"></a>Sluiten  

```  
HRESULT Close(void)  
```  

 Deze methode is alleen voor intern gebruik.  

##### <a name="getlogfilename"></a>GetLogFilename  

```  
HRESULT GetLogFilename(LPBSTR pFilename)  
```  

 Deze methode haalt de naam van het logboekbestand.  

#### <a name="iorientation-interface"></a>IOrientation-Interface  

```  
__interface IOrientation : IUnknown  
{  
    void SetController(IWizardDialogController *pController);  
    int AddPage(LPCTSTR name);  
    void SelectPage(int index);  
};  
```  

 Deze interface is alleen voor intern gebruik.  

#### <a name="isettings-interface"></a>ISettings-Interface  

```  
__interface ISettings : IUnknown  
{  
    int NumDlls();  
    int NumPages();  

    HRESULT SetStage(LPCWSTR stageName);  
    HRESULT GetDllName(long index, __out LPBSTR pDllName);  
    HRESULT GetPageInfo(long index, __out ISettingsProperties **ppPageInfo);  
    HRESULT GetStyle(__out ISettingsProperties **ppStyleInfo);  
};  
```  

 Deze interface is alleen voor intern gebruik.  

#### <a name="isettingsproperties-interface"></a>ISettingsProperties-Interface  

```  
__interface ISettingsProperties : IUnknown  
{  
    HRESULT GetAttribute(LPCTSTR attributeName, __out LPBSTR attributeValue);  
    IStringProperties * Properties();  
   RESULT SelectNodes(LPCTSTR xPath, __out IXMLDOMNodeList **ppList);  
    HRESULT SelectSingleNode(LPCTSTR xPath, __out IXMLDOMNode **ppNode);  
    HRESULT GetDataNode(LPCTSTR name, __out ISettingsProperties **ppNode);  
    HRESULT GetDataNodes(__out IDataNodes **ppNodes);  
    HRESULT GetChildDataNodes(LPCTSTR childeName, __out IDataNodes **ppNodes);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface biedt toegang tot paginagegevens. Als u naar het hoogste niveau van de paginagegevens, gebruikt u de pagina **Settings()** methode.  

##### <a name="hresult-getattributelpctstr-attributename--lpbstr-attributevalue"></a>HRESULT GetAttribute(LPCTSTR attributeName, LPBSTR attributeValue)  
 Deze methode kunt u voor het ophalen van de waarden van kenmerken op het hoofdknooppunt, is de **pagina** knooppunt wanneer u de **Settings()** methode van de pagina.  

##### <a name="istringproperties--properties"></a>IStringProperties * Properties()  
 Deze methode biedt toegang tot de waarden van de eigenschap setter onder het hoofdknooppunt. Dit zijn de eigenschappen op het hoogste niveau voor een pagina.  

##### <a name="hresult-selectnodeslpctstr-xpath--ixmldomnodelist-pplist"></a>HRESULT SelectNodes(LPCTSTR xPath, IXMLDOMNodeList **ppList)  
 Deze methode niet aanroepen als u wilt een lijst met XML-knooppunt met behulp van een XPath-expressie rechtstreeks ophalen. Het is beter om een van de andere methoden gebruiken als u de kunt. Deze methode alleen gebruiken als je geen toegang om een andere manier aan knooppunten.  

##### <a name="hresult-selectsinglenodelpctstr-xpath--ixmldomnode-ppnode"></a>HRESULT SelectSingleNode(LPCTSTR xPath, IXMLDOMNode **ppNode)  
 Deze methode niet aanroepen als u wilt ophalen rechtstreeks één XML-knooppunt met behulp van een XPath-expressie. Het is beter om een van de andere methoden gebruiken als u de kunt. Deze methode alleen gebruiken als je geen toegang tot een knooppunt een andere manier.  

##### <a name="hresult-getdatanodelpctstr-name--isettingsproperties-ppnode"></a>HRESULT GetDataNode(LPCTSTR name, ISettingsProperties **ppNode)  
 Ophalen van een **gegevens** element op basis van dat element **naam** kenmerk.  

##### <a name="hresult-getdatanodesidatanodes-ppnodes"></a>HRESULT GetDataNodes(IDataNodes **ppNodes)  
 Deze methode haalt een lijst met **DataItem** elementen onder het huidige knooppunt. Aanroepen van het paginaniveau **GetDataNode** voor het ophalen van een **ISettingsProperty** interface voor de gegevens. Roep vervolgens voor dat exemplaar **GetDataNodes** voor het ophalen van de lijst met records. Bijvoorbeeld, krijgt deze XML:  

```  
    <Page …>  
      <Data Name="Network">  
        <DataItem>  
          <Setter Property="DisplayName">Public</Setter>  
          <Setter Property="Share">\\servername\Share</Setter>  
        </DataItem>  
        <DataItem>  
          <Setter Property="DisplayName">Dev Team</Setter>  
          <Setter Property="Share">\\servername\DevShare</Setter>  
        </DataItem>  
      </Data>  

PSettingsProperties pData;  
Settings()->GetDataNode(L"Network", &pData);  
PDataNodes pNodes;  
pData->GetDataNodes(&pNodes);  
```  

##### <a name="hresult-getchilddatanodeslpctstr-childename--idatanodes-ppnodes"></a>HRESULT GetChildDataNodes(LPCTSTR childeName, IDataNodes **ppNodes)  
 Deze methode biedt een snelle manier om aan de set **DataItem** knooppunten onder een bepaalde **gegevens** knooppunt. Met behulp van de XML van de **GetDataNodes** bijvoorbeeld de volgende code wordt precies hetzelfde als de vier regels code in het voorbeeld onder **GetDataNodes** maar foutcontrole:  

```  
ISimpleStringProperties Interface  
```  

#### <a name="isimplestringproperties-interface"></a>ISimpleStringProperties Interface  

```  
__interface ISimpleStringProperties : IStringProperties  
{  
void Add(LPCTSTR propertyName, LPCTSTR value);  
};  
```  

 Zelfstandig gebruikt, deze interface niet mogelijk van pas. Maar deze is geïmplementeerd door de **ID_SimpleStringProperties** onderdeel, dat ook de **IStringProperties** interface. U kunt dit onderdeel gebruiken in gevallen waar u moet een set eigenschappen doorgeven aan een ander onderdeel, zoals een taak, maar u wilt toevoegen als waarden programmatisch met behulp van de waarden van XML. Hier volgt een voorbeeld van hoe u deze interface wilt gebruiken:  

```  
PSimpleStringProperties *pProperties;  
CreateInstance(Container(), ID_SimpleStringProperties, &pProperties);  
pProperties->Add(L"filename", L"%windir%\\system32\\cscript.exe");  
pTask->Init(pProperties, nullptr);  
IStringProperties  
__interface IStringProperties : IUnknown  
{  
    HRESULT Get(LPCTSTR propertyName, [out] LPBSTR pPropValue);  
};  
```  

 Deze interface biedt eenvoudige toegang tot een reeks setter-elementen die afkomstig van de XML zijn. Deze interface is beschikbaar voor de eigenschappen van een pagina met **Settings() -> Properties()**.  

##### <a name="hresult-getlpctstr-propertyname-out-lpbstr-ppropvalue"></a>HRESULT Get(LPCTSTR propertyName, [out] LPBSTR pPropValue)  
 Deze methode haalt een waarde één eigenschap. Zie tabel 47 en tabel 48.  

### <a name="table-47-ihresult-get-property-value"></a>Tabel 47. De waarde van de eigenschap Get IHRESULT  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**propertyName**|Naam van de eigenschap die u wilt lezen|  
|**pPropValue**|Bij het afsluiten, bevat de waarde van de eigenschap als tekenreeks (deze waarde zal worden **nullptr** als er geen dergelijke eigenschap is.)|  

### <a name="table-48-ihresult-get-property-value-results"></a>Tabel 48. IHRESULT eigenschap waarde resultaten ophalen  

|||  
|-|-|  
|**HRESULT**|**Beschrijving**|  
|**S_OK**|Waarde van de eigenschap wordt opgehaald.|  
|**E_INVALIDARG**|Er is geen eigenschap met de naam die u hebt opgegeven.|  

#### <a name="itaskmanager-interface"></a>ITaskManager-Interface  

```  
__interface ITaskManager : IUnknown  
{  
    HRESULT Init(IWizardPageView *pPageView, int idListView, int idMessage, int idRetryButton, ISettingsProperties *pPageInfo, ITaskManagerCallback *pCallback);  
    HRESULT SetFailMessage(LPCWSTR message);  

    HRESULT Start(void);  

    HRESULT GetTaskMessage(size_t index, LPBSTR message);  
    HRESULT GetResultType)(size_t index, LPBSTR type);  
    HRESULT GetProperty(size_t index, LPCTSTR propertyName, LPBSTR value);  
    int GetSelectedIndex(void);  
    HRESULT Wait(DWORD waitMilliseconds);  
    size_t FailedCount(void);  
    size_t WarningCount(void);  
    size_t SucceedCount(void);  
    size_t RunningCount(void);  

    void OnCommonControlEvent(WORD controlId, LPNMHDR pInfo);  
    void OnControlEvent(WORD eventId, WORD controlId);  
    void EnableButtons(BOOL enable);  
}  
```  

 Deze interface is geïmplementeerd door de **TaskManager** onderdeel (**ID_TaskManager** in ITaskManager.h), is het onderdeel dat taken op de pagina voorbereidende wordt uitgevoerd. Gebruik de voorbereidende pagina rechtstreeks, dit wat u meestal doen is, of uw eigen pagina, zodat dit onderdeel die het meeste werk bouwen.  

##### <a name="hresult-initiwizardpageview-ppageview-int-idlistview-int-idmessage-int-idretrybutton-isettingsproperties-ppageinfo-itaskmanagercallback-pcallback"></a>HRESULT Init(IWizardPageView \*pPageView, int idListView, int idMessage, int idRetryButton, ISettingsProperties \*pPageInfo, ITaskManagerCallback \*pCallback)  
 U moet deze methode aanroepen voordat u een andere methode. Het initialiseren van de **TaskManager** onderdeel. Zie tabel 49.  

### <a name="table-49-hresult-init"></a>Tabel 49. HRESULT Init  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**pPageView**|Biedt toegang tot de pagina die wordt uitgevoerd taken (deze pagina moet een specifieke set besturingselementen die worden beschreven in het volgende aantal parameters hebben.)|  
|**idListView**|De besturingselement-ID van een **ListView** besturingselement dat de lijst met taken en de status van deze taken worden weergegeven|  
|**idMessage**|De besturingselement-ID van een tekstvak dat wordt gebruikt voor het weergeven van een bericht voor de taak die u selecteert|  
|**idRetryButton**|De besturingselement-ID van een knop kunt u klikken de taken opnieuw uitvoeren|  
|**pPageInfo**|Een wrapper rond de pagina XML (**TaskManager** de set taken uitvoeren vanuit deze XML worden geladen.)|  
|**pCallback**|Kan null zijn (als deze parameter niet null, **TaskManager** aanroepen de **gestart** methode wanneer deze een taak wordt gestart en de **voltooid** methode voor elke taak die is voltooid.)|  

##### <a name="hresult-setfailmessagelpcwstr-message"></a>HRESULT SetFailMessage(LPCWSTR message)  
 Deze methode stelt het bericht dat wordt weergegeven als een of meer taken mislukken.  

##### <a name="hresult-startvoid"></a>HRESULT Start(void)  
 Deze methode Start alle taken. Elke taak is gestart op een afzonderlijke thread.  

##### <a name="hresult-gettaskmessagesizet-index-lpbstr-message"></a>HRESULT GetTaskMessage(size_t index, LPBSTR message)  
 Deze methode is alleen voor intern gebruik. Het ophalen van het huidige bericht voor een taak op basis van de index in de lijst met taken.  

##### <a name="hresult-getresulttypesizet-index-lpbstr-type"></a>HRESULT GetResultType) (size_t index, LPBSTR type)  
 Deze methode haalt de huidige 'type' voor een taak. 50 tabel ziet u de beschikbare typen.  

### <a name="table-50-hresult-getresulttype"></a>Tabel 50. HRESULT GetResultType  

|**Type**|**Beschrijving**|  
|-|-|  
|**0**|Hiermee geeft u een taak die is voltooid|  
|**1**|Hiermee geeft u een taak die een waarschuwing geretourneerd|  
|**-1**|Hiermee geeft u een mislukte taak|  

 Het type is opgehaald door te kijken naar de taak afsluiten of fout code en zoeken naar een overeenkomst in de taak < ExitCodes\> XML-element.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propertyname-lpbstr-value"></a>HRESULT GetProperty(size_t index, LPCTSTR propertyName, LPBSTR value)  
 Deze methode wordt gebruikt door de voortgang en preflight pagina's voor het ophalen van de **BitmapFilename** setter, zodat de installatiekopie van een naast het bericht voor de taak die u markeren weer te geven. Met andere woorden, kunt u een aangepaste setter toevoegen aan de taak XML en vervolgens ophalen met deze methode.  

##### <a name="int-getselectedindexvoid"></a>int GetSelectedIndex(void)  
 Deze methode haalt de index van de geselecteerde taak handig is als u wilt ophalen van aanvullende informatie over de taak (Zie **GetProperty** methode) moet worden weergegeven voor de geselecteerde taak. De voortgang en voorbereidende pagina's kunt u deze methode gebruiken om een installatiekopie voor de geselecteerde taak weer te geven.  

##### <a name="hresult-waitdword-waitmilliseconds"></a>HRESULT Wait(DWORD waitMilliseconds)  
 Deze methode kunt hoofdzakelijk met eenheidstests zodat de test zeker weet dat taken worden voltooid voordat de eenheid wordt afgesloten testen. U zou niet normaal gesproken deze methode niet aanroepen. Het resultaat wanneer alle taken zijn uitgevoerd of de wachttijd is verstreken.  

##### <a name="sizet-failedcountvoid"></a>size_t FailedCount(void)  
 Deze methode retourneert het aantal taken die momenteel als mislukt gemarkeerd.  

##### <a name="sizet-warningcountvoid"></a>size_t WarningCount(void)  
 Deze methode retourneert het aantal taken die momenteel zijn gemarkeerd als waarschuwing.  

##### <a name="sizet-succeedcountvoid"></a>size_t SucceedCount(void)  
 Deze methode retourneert het aantal taken die momenteel gemarkeerd als voltooid.  

##### <a name="sizet-runningcountvoid"></a>size_t RunningCount(void)  
 Deze methode retourneert het aantal taken die momenteel worden uitgevoerd.  

##### <a name="void-oncommoncontroleventword-controlid-lpnmhdr-pinfo"></a>VOID OnCommonControlEvent (WORD controlId, LPNMHDR pInfo)  
 Deze methode niet aanroepen vanaf de pagina **OnCommonControlEvent** zodat de **TaskManager** moet gebeurtenissen kan verwerken.  

##### <a name="void-oncontroleventword-eventid-word-controlid"></a>VOID OnControlEvent (WORD eventId, WORD controlId)  
 Deze methode niet aanroepen vanaf de pagina **OnControlEvent** zodat de **TaskManager** moet gebeurtenissen kan verwerken.  

##### <a name="void-enablebuttonsbool-enable"></a>VOID EnableButtons(BOOL enable)  
 Deze methode is alleen voor intern gebruik.  

#### <a name="iwizardcomponent-interface"></a>IWizardComponent Interface  

```  
__interface IWizardComponent : IUnknown  
{  
    HRESULT SetContainer(IWizardPageContainer *pContainer);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Normaal gesproken u implementeert geen deze interface rechtstreeks, maar in plaats daarvan via de **WizardComponent** sjabloonklasse. Als het onderdeel deze interface worden geïmplementeerd en u hebt een classfactory geregistreerd met het register, krijgt uw onderdeel een verwijzing naar de **IWizardPageContainer** exemplaar wanneer deze wordt gemaakt. Zo kunt u, bijvoorbeeld, toegang tot het logboek of in het register voor het maken van andere onderdelen die nodig kan zijn uw onderdeel.  

#### <a name="iwizarddialogcontroller-interface"></a>IWizardDialogController Interface  

```  
__interface IWizardDialogController : IUnknown  
{  
    void Initialize(ISettings *pSettings);  
    void InitPages(void);  
    void Start();  
    void Next();  
    void Finish();  
    void Previous();  
    int NumPages();  
    void Cancel();  

    HRESULT Focus(WizardButtons button);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage();  

    void ChangePage(size_t newIndex);  
    IUnknown *CurrentPage(void);  
    HRESULT GetCurrentTitle([out, retval] LPBSTR pDisplayName);  
};  
```  

 Deze interface is alleen voor intern gebruik.  

#### <a name="iwizarddialogview-interface"></a>IWizardDialogView Interface  

```  
__interface IWizardDialogView : IUnknown  
{  
    HRESULT LoadBannerImage(LPCTSTR bannerFilename);  
    HRESULT LoadPage(LPCTSTR pageType, ISettingsProperties *pPageSettings, IWizardPageView **view);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    HRESULT Focus(WizardButtons button);  
    void EnableFinish(BOOL isFinish);  
    void Exit(int exitCode);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage(void);  
    void SetTitle(LPCTSTR title);  
    void SetPageTitle(LPCTSTR title);  
    int ShowMessageBox(LPCTSTR message, LPCTSTR lpCaption, UINT uType);  
    HWND GetHwnd(void);  
    void UpdateFocus(void);  
};  
```  

 Deze interface is alleen voor intern gebruik.  

####  <a name="IWizardPageInterface"></a> IWizardPage-Interface  

```  
__interface IWizardPage : IUnknown  
{  
    HRESULT SetPageSettings(ISettingsProperties *pPageSettings);  
    HINSTANCE GetInstanceHandle(void);  
    int GetDialogResourceId(void);  
    void WindowCreated(IWizardPageView *pView, IWizardPageContainer *pContainer);  
    void WindowShown(void);  
    void WindowHidden(void);  

    HRESULT NextClicked(void);  
    void ControlEvent(WORD eventId, WORD controlId);  
    void CommonControlEvent(WORD controlId, LPNMHDR pInfo, LPBOOL pCancel);  
    void UnhandledEvent(HWND hwnd, UINT message, WPARAM wParam, LPARAM lParam);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door **WizardPageImpl**, zodat u doorgaans geen voor het implementeren van deze deze. De wizard roept al deze methoden voor u, als deze met uw aangepaste pagina's samenwerkt.  

#### <a name="iwizardpagecontainer-interface"></a>IWizardPageContainer Interface  

```  
__interface IWizardPageContainer : IUnknown  
{  
    ILogger * Logger(void);  
    IPropertyBag * Properties(void);  
    HRESULT CreateInstance(LPCTSTR type, [out] IUnknown **ppInstance);  
    HRESULT GetService(REFIID iid, [out] IUnknown **ppInstance);  
    HRESULT ReplaceVariables(LPCTSTR source, [out] LPBSTR pDest);  
    HRESULT GotoPage(LPCTSTR pageName);  
    int ShowMessageBox(LPCTSTR message, LPCTSTR lpCaption, UINT uType);  
    BOOL InPreview(void);  
    HWND GetHwnd(void);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is beschikbaar op de pagina via de **Container** methode (geïmplementeerd door **WizardPageImpl**) en biedt u toegang tot diverse services van de wizard.  

##### <a name="ilogger--loggervoid"></a>ILogger * Logger(void)  
 Met deze methode kunt u berichten schrijven naar het logboekbestand — bijvoorbeeld:  

```  
Logger()->Verbose(s_component, L"Message for log file");  
```  

##### <a name="ipropertybag--propertiesvoid"></a>IPropertyBag * Properties(void)  
 Deze methode biedt toegang tot '' geheugenvariabelen, die eigenschappen die in het geheugen zijn, zijn alleen wanneer de Wizard UDI wordt uitgevoerd. Deze eigenschappen zijn beschikbaar voor andere pagina's in code of in de XML met behulp van de **$memoryVarName$** syntaxis.  

##### <a name="hresult-createinstancelpctstr-type-out-iunknown-ppinstance"></a>HRESULT CreateInstance(LPCTSTR type, [out] IUnknown **ppInstance)  
 Deze methode kunt u een nieuw exemplaar van de onderdelen die is geregistreerd. Het is echter beter gebruik van de functie **CreateInstance**, omdat het wordt sterk getypeerd.  

##### <a name="hresult-getservicerefiid-iid-out-iunknown-ppinstance"></a>HRESULT GetService(REFIID iid, [out] IUnknown **ppInstance)  
 Deze methode kunt u voor het ophalen van een service die is geregistreerd. Het is echter beter om aan te roepen de **mag GetService** sjabloonfunctie, sterk getypeerd is (in plaats van **IUnknown**).  

##### <a name="hresult-replacevariableslpctstr-source-out-lpbstr-pdest"></a>HRESULT ReplaceVariables(LPCTSTR source, [out] LPBSTR pDest)  
 Deze methode verwerkt werken met variabelen binnen tekenreekswaarden. Het ondersteunt de indelingen in tabel 51 en 52 tabel wordt weergegeven.  

### <a name="table-51-hresult-replacevariables"></a>Tabel 51. HRESULT ReplaceVariables  

|**Indeling**|**Beschrijving**|  
|-|-|  
|**$Name$**|Vervangt de waarde van een variabele geheugen met deze naam (als er geen geheugen-variabele met de naam, wordt de 'token' verwijderd.)|  
|**%Name%**|Een takenreeksvariabele of een omgevingsvariabele. De volgorde is als volgt:<br /><br /> 1.  Gebruik de waarde van een takenreeksvariabele, indien aanwezig.<br />2.  Gebruik de waarde van een omgevingsvariabele, indien aanwezig.<br />3.  Anders kunnen deze tekst verwijderen uit de tekenreeks.|  

### <a name="table-52-hresult-parameter"></a>Tabel 52. HRESULT Parameter  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Bron**|De invoerreeks heeft die kan bestaan uit een combinatie van **$** en **%** variabelen of helemaal|  
|**pDest**|Op return bevat een nieuwe reeks met alle tokens volgens tabel 51 vervangen|  

##### <a name="hresult-gotopagelpctstr-pagename"></a>HRESULT GotoPage(LPCTSTR pageName)  
 Deze methode is niet volledig getest. Het idee is dat, kunt u rechtstreeks naar een bepaalde pagina gebaseerd op de naam van de pagina, zoals gedefinieerd in het .config-XML-bestand. Deze methode aanroept, omzeilt de **OnNextClicked** op de pagina. Bovendien het gedrag van deze methode kan worden gewijzigd, dus gebruiken voor uw eigen risico.  

##### <a name="int-showmessageboxlpctstr-message-lpctstr-lpcaption-uint-utype"></a>int ShowMessageBox (LPCTSTR bericht, LPCTSTR lpCaption, UINT uType)  
 Deze methode wordt weergegeven in het bericht met de tekst en het bijschrift dat u opgeeft. De **uType** -parameter is een waarde die u kunt opgeven voor de **MessageBox** Win32-functie.  

##### <a name="bool-inpreviewvoid"></a>BOOL InPreview(void)  
 Deze methode retourneert TRUE als u de wizard in de modus 'preview' door het opgeven van gestart de **/preview** overschakelen. In de voorbeeldmodus, de **volgende** knop nooit is uitgeschakeld. Deze methode kunt u code in de voorbeeldmodus, bijvoorbeeld voor het overslaan die problemen veroorzaken kan wanneer u geen geldige gegevens op de pagina hebt.  

##### <a name="hwnd-gethwndvoid"></a>HWND GetHwnd(void)  
 Deze methode retourneert de **HWND** voor de belangrijkste dialoogvenster. Gebruik deze methode zorgvuldig. In het algemeen is de Wizard UDI application programming interface zodanig ontworpen dat u nooit rechtstreeks met vensteringangen werkt.  

#### <a name="iwizardpageview-interface"></a>IWizardPageView Interface  

```  
__interface IWizardPageView : IUnknown  
{  
    HRESULT GetControlWrapper(int itemId, DialogControlTypes controlType, IUnknown **ppControl);  
    HWND GetHwnd(void);  
    HWND GetControl(int itemId);  
    HRESULT Show (void);  
    HRESULT Hide(void);  
    HRESULT Focus(int itemId);  
    IWizardPage * Page(void);  
    IFormController * Form(void);  

    HRESULT FocusWizardButton(WizardButtons button);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage(void);  
};  
```  

 Deze interface is beschikbaar voor de code in uw pagina via de **weergave** methode (geïmplementeerd door **WizardPageImpl**).  

##### <a name="hresult-getcontrolwrapperint-itemid-dialogcontroltypes-controltype-iunknown-ppcontrol"></a>HRESULT GetControlWrapper(int itemId, DialogControlTypes controlType, IUnknown \*ppControl)  
 Maakt gebruik van de Wizard UDI *wrappers*, die zijn in feite façades voor interactie met de besturingselementen op de pagina. Met deze façades in plaats van de werkelijke besturingselementen gemakkelijker veel om te schrijven tests voor de pagina omdat u mock façades van uw tests kunt opgeven.  

 In plaats van rechtstreeks gebruik van deze methode is het beter gebruik van de **GetControlWrapper** sjabloon-methode is sterk getypeerd — bijvoorbeeld:  

```  
PComboBox m_pLanguagePackCombo;  
GetControlWrapper(View(), IDC_MY_COMBO, CONTROL_COMBO_BOX, &m_pCombo);  
```  

##### <a name="hwnd-gethwndvoid"></a>HWND GetHwnd(void)  
 Deze methode retourneert de vensterkoppeling voor uw pagina. In het algemeen moet u geen toegang tot deze vensterkoppeling nodig.  

##### <a name="hwnd-getcontrolint-itemid"></a>HWND GetControl(int itemId)  
 Als u moet, kunt u deze methode voor de vensterkoppeling voor een besturingselement op de pagina aanroepen. (Is het beter om aan te roepen de **GetControlWrapper** sjabloonfunctie).  

##### <a name="hresult-show-void"></a>HRESULT weergeven (leeg)  
 Deze methode is alleen voor intern gebruik.  

##### <a name="hresult-hidevoid"></a>HRESULT Hide(void)  
 Deze methode is alleen voor intern gebruik.  

##### <a name="hresult-focusint-itemid"></a>HRESULT Focus(int itemId)  
 De invoerfocus ingesteld op een bepaald besturingselement.  

##### <a name="iwizardpage--pagevoid"></a>IWizardPage * Page(void)  
 Deze methode is alleen voor intern gebruik.  

##### <a name="iformcontroller--formvoid"></a>IFormController * Form(void)  
 Deze methode is alleen voor intern gebruik.  

##### <a name="hresult-focuswizardbuttonwizardbuttons-button"></a>HRESULT FocusWizardButton(WizardButtons button)  
 Hiermee stelt u de focus naar een van de wizard knoppen. **WizardButtons** heeft twee waarden: **BackButton** en **NextButton**.  

##### <a name="hresult-setenablewizardbuttons-button-bool-enable"></a>HRESULT SetEnable(WizardButtons button, BOOL enable)  
 Aanvraag voor een van de knoppen met de wizard worden ingeschakeld of uitgeschakeld. De knop mogelijk niet overeen met de status die u aanvraagt. Als u de Wizard UDI met uitvoert bijvoorbeeld de **/preview** overschakelen, de knoppen altijd ingeschakeld. **WizardButtons** heeft twee waarden: **BackButton** en **NextButton**.  

##### <a name="void-showwarningmessagelpctstr-message"></a>VOID ShowWarningMessage(LPCTSTR message)  
 Deze methode wordt een waarschuwingsbericht weergegeven aan de onderkant van het gebied van pagina-inhoud. Dit bericht kan de tekst die u wilt worden.  

##### <a name="void-hidewarningmessagevoid"></a>VOID HideWarningMessage(void)  
 Een waarschuwingsbericht weergegeven die worden weergegeven met een aanroep naar verbergen **ShowWarningMessage**.  

#### <a name="ixmldocument-interface"></a>IXmlDocument Interface  

```  
__interface IXmlDocument : IUnknown  
    HRESULT Load(LPCTSTR filename);  
    HRESULT LoadXml(LPCTSTR xml);  
    HRESULT Save(LPCWSTR filename);  
    HRESULT GetParseErrorMessage(LPBSTR pMessage);  
    HRESULT SelectNodes(LPCTSTR xpath, IXMLDOMNodeList **ppNodes);  
    HRESULT SelectSingleNode(LPCTSTR xpath, IXMLDOMNode **ppNode);  
    HRESULT AddSchema(LPCTSTR filename, LPCTSTR ns);  
    HRESULT AddAttribute(IXMLDOMNode *pNode, LPCWSTR name, LPCWSTR value);  
    HRESULT CreateNode(DOMNodeType type, LPCWSTR name, LPCWSTR ns, IXMLDOMNode **ppNode);  
};  
```  

##### <a name="overview"></a>Overzicht  
 Deze interface is geïmplementeerd door de **ID_IXmlDocument** onderdeel, dat een façade ontworpen om het gemakkelijker om te werken met XML-documenten in C++.  

##### <a name="hresult-loadlpctstr-filename"></a>HRESULT Load(LPCTSTR filename)  
 Deze methode wordt een XML-document geladen uit een extern bestand. Deze retourneert **S_OK** als het bestand is zonder fouten geladen of **S_FALSE** als een fout opgetreden. Als er een fout is, krijgt u het foutbericht wordt weergegeven door het aanroepen van **GetParseErrorMessage**.  

##### <a name="hresult-loadxmllpctstr-xml"></a>HRESULT LoadXml(LPCTSTR xml)  
 Deze methode wordt een XML-document van een tekenreeks in plaats van een extern bestand geladen. Het gedrag is anders dan de bron voor het lezen van het XML-bestand, hetzelfde als de **Load** methode.  

##### <a name="hresult-savelpcwstr-filename"></a>HRESULT Save(LPCWSTR filename)  
 Deze methode bespaart het XML-document dat in het geheugen naar een extern bestand.  

##### <a name="hresult-getparseerrormessagelpbstr-pmessage"></a>HRESULT GetParseErrorMessage(LPBSTR pMessage)  
 Deze methode retourneert een nieuwe tekenreeks met het foutbericht van het laden van het XML-document, indien van toepassing. Retourneert altijd **S_OK**.  

##### <a name="hresult-selectnodeslpctstr-xpath-ixmldomnodelist-ppnodes"></a>HRESULT SelectNodes(LPCTSTR xpath, IXMLDOMNodeList \**ppNodes)  
 Deze methode kunt u het gebruik van een XPath-expressie voor het ophalen van een verzameling van knooppunten uit het document. Retourneert altijd **S_OK**.  

##### <a name="hresult-selectsinglenodelpctstr-xpath-ixmldomnode-ppnode"></a>HRESULT SelectSingleNode(LPCTSTR xpath, IXMLDOMNode \**ppNode)  
 Deze methode kunt u gebruikmaken van een XPath-expressie voor het ophalen van een knooppunt uit het document. Retourneert altijd **S_OK**.  

##### <a name="hresult-addschemalpctstr-filename-lpctstr-ns"></a>HRESULT AddSchema(LPCTSTR filename, LPCTSTR ns)  
 Deze methode wordt de naam van een extern schema-bestand dat wordt gebruikt voor het valideren van het schema van uw XML-document wanneer deze worden geladen. De naamruimte die u opgeeft, is de tekenreeks die u kunt XPath-query's, hoewel dit niet is getest.  

##### <a name="hresult-addattributeixmldomnode-pnode-lpcwstr-name-lpcwstr-value"></a>HRESULT AddAttribute(IXMLDOMNode \*pNode, LPCWSTR name, LPCWSTR value)  
 Deze methode wordt een nieuw kenmerk toegevoegd aan een bestaande knooppunt in het XML-document. Zie tabel 53.  

### <a name="table-53-hresult-addattribute"></a>53 van de tabel. HRESULT AddAttribute  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**pNode**|Het knooppunt waarnaar u wilt een kenmerk toevoegen|  
|**Naam**|Naam van het nieuwe kenmerk|  
|**Waarde**|De waarde voor het nieuwe kenmerk|  

##### <a name="hresult-createnodedomnodetype-type-lpcwstr-name-lpcwstr-ns-ixmldomnode-ppnode"></a>HRESULT CreateNode(DOMNodeType type, LPCWSTR name, LPCWSTR ns, IXMLDOMNode \**ppNode)  
 Deze methode voor het maken van een nieuw knooppunt niet aanroepen:  

```  
Pointer<IXMLDOMNode> pNewChild  
pXmlDom->CreateNode(NODE_ELEMENT, L"MyElement", L"", &pNewChild);  
```  

 Wanneer u een nieuw knooppunt maakt, u kunt deze toevoegen als een onderliggend element naar een ander knooppunt door het aanroepen van de bovenliggende **appendChild** methode.  

### <a name="helper-functions"></a>Help-functies  

#### <a name="createinstance-template-function"></a>CreateInstance sjabloonfunctie  

```  
HRESULT CreateInstance(IWizardPageContainer *pContainer, LPCTSTR type, I **ppObject)  
```  

 Deze functie is gedefinieerd in IWizardPageContainer.h en biedt een type-veilige wrapper ten opzichte van de **IWizardPageContainer -> CreateInstance** methode — bijvoorbeeld:  

```  
CreateInstance<IDirectory>(Container(), ID_Directory, &pDirectory);  
```  

 Deze code maakt u een nieuwe **ID_Directory** onderdeel voor het ophalen van de **IDirectory** interface van dit onderdeel.  

#### <a name="getservice-template-function"></a>Mag GetService sjabloonfunctie  

```  
void GetService(IWizardPageContainer *pContainer, I **ppService)  
```  

 Deze functie is gedefinieerd in IWizardPageContainer.h en biedt een type-veilige wrapper ten opzichte van de **IWizardPageContainer -> mag GetService** methode — bijvoorbeeld:  

```  
GetService<ITSVariableBag>(Container(), &pTsBag);  
```  

 Deze functie haalt de taak sequence-component, die ondersteuning biedt voor de **ITSVariableBag** interface. (Voor **ITSVariableBag**, kunt u de methode TSVariables van de **WizardPageImpl** klasse, in plaats daarvan.)  

### <a name="udi-wizard-designer-configuration-file-schema-reference"></a>UDI Wizard Configuratie van de ontwerpfunctie bestandsverwijzing-Schema  
 Dit bestand wordt gebruikt door de waarde van de Wizard UDI. Een afzonderlijk bestand is gemaakt voor elke aangepaste DLL-bestand, dat aangepaste wizard pagina editors, aangepaste taken of aangepaste validatiefuncties kan bevatten. Het bestand moet eindigen met *.config* en bevinden zich in de *installation_folder*\Bin\Config map (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd).  

  54 tabel bevat de elementen in het configuratiebestand van de Wizard UDI en de bijbehorende beschrijvingen. De **DesignerConfig** -element is het hoofdknooppunt voor deze verwijzing.  

### <a name="table-54-elements-in-the-udi-wizard-designer-configuration-file-and-their-descriptions"></a>Tabel 54. Elementen in het configuratiebestand UDI Wizard Designer en de bijbehorende beschrijvingen  

|**Elementnaam**|**Beschrijving**|  
|-|-|  
|[DesignerConfig](#DesignerConfig)|Hiermee geeft u de hoofdmap voor alle andere elementen|  
|[DesignerMappings](#DesignerMappings)|Een set met groepen [pagina](#Page)elementen|  
|[Pagina](#Page)|Hiermee geeft u een wizard-pagina-editor om te worden geladen in het ontwerp van de Wizard UDI, die wordt gebruikt voor het bewerken van de configuratie-instellingen voor een wizardpagina|  
|[Param](#Param)|Hiermee geeft u een parameter die wordt doorgegeven aan de bovenliggende [taak](#Task) of [Validator](#Validator) element en komt overeen met een [Setter]() element in het configuratiebestand van de Wizard UDI **Opmerking:**  De kenmerken voor dit element zijn verschillend als de bovenliggende de [taak](#Task) of [Validator](#Validator) element.|  
|[Task](#Task)|Hiermee geeft u een taak in de tapewisselaar taak|  
|[TaskItem](#TaskItem)|Hiermee geeft u een groep van de parameters die worden doorgegeven aan de taak|  
|[TaskLibrary](#TaskLibrary)|Een set met groepen [taak](#Task) elementen|  
|[Validator](#Validator)|Hiermee geeft u een validator in de tapewisselaar validator|  
|[ValidatorLibrary](#ValidatorLibrary)|Een set met groepen [Validator](#Validator) elementen|  

####  <a name="DesignerConfig"></a> DesignerConfig  
 Dit element bevat de hoofdmap voor alle andere elementen.  

##### <a name="element-information"></a>Elementgegevens  
  Tabel 55 bevat informatie over de [DesignerConfig](#DesignerConfig) element.  

### <a name="table-55-designerconfig-element-information"></a>Tabel 55. DesignerConfig elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een: Dit element is vereist.|  
|Bovenliggende elementen|Geen|  
|Inhoud|**DesignerMappings**, **TaskLibrary**, **ValidatorLibrary**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<DesignerConfig>  
   + <TaskLibrary>  
   + <ValidatorLibrary>  
   + <DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="DesignerMappings"></a> DesignerMappings  
 Dit element een set met groepen [pagina](#Page) elementen.  

##### <a name="element-information"></a>Elementgegevens  
  Tabel 56 bevat informatie over de [DesignerMappings](#DesignerMappings) element.  

### <a name="table-56-designermappings-element-information"></a>Tabel 56. DesignerMappings elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of één binnen de [DesignerConfig](#DesignerConfig) element (dit element is optioneel als er geen aangepaste wizardpagina in het DLL-bestand dat overeenkomt met dit configuratiebestand van de Wizard UDI.)|  
|Bovenliggende elementen|**DesignerConfig**|  
|Inhoud|**Pagina**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<DesignerConfig>  
   + <TaskLibrary>  
   + <ValidatorLibrary>  
   - <DesignerMappings>  
        <Page DLL="SharedPages.dll"  
           Description="Used to display text that describes the current stagegroup"  
           Type="Microsoft.SharedPages.WelcomePage"  
           DisplayName="Welcome"   
           Image="Welcome_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.WelcomePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
        <Page DLL="OSDRefreshWizard.dll"  
           Description="Captures or restores user state data"  
           Type="Microsoft.OSDRefresh.UserStatePage"  
           DisplayName="User Data"  
           Image="UserState_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.UserStatePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
        <Page DLL="OSDRefreshWizard.dll"  
           Description="Allows selecting the image to install, target drive, and whether to format"  
           Type="Microsoft.OSDRefresh.VolumePage"  
           DisplayName="Volume"  
           Image="Volume_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.VolumePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
     </DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="Page"></a> Pagina  
 Dit element bevat een wizard-pagina-editor om te worden geladen in het ontwerp van de Wizard UDI, die op zijn beurt wordt gebruikt voor het bewerken van de configuratie-instellingen voor een pagina van de wizard.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 57 bevat informatie over de [pagina](#Page) element.  

### <a name="table-57-page-element-information"></a>Tabel 57. Pagina-Element-informatie  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer voor elke wizardpagina gedefinieerd in de [DesignerMappings](#DesignerMappings) element|  
|Bovenliggende elementen|**DesignerMappings**|  
|Inhoud|Juist opgemaakte XML-inhoud|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 58 hier worden de kenmerken van de [pagina](#Page) -element en een beschrijving op voor elke.  

### <a name="table-58-attributes-and-corresponding-values-for-the-page-element"></a>Tabel 58. Kenmerken en bijbehorende waarden voor het pagina-Element  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Beschrijving**|Hiermee geeft u de tekst die informatie biedt over de parameter die wordt weergegeven in de Wizard UDI Designer|  
|**DesignerAssembly**|Geeft de naam van het DLL-bestand dat is gekoppeld aan de wizard-editor (het DLL-bestand moet bestaan in de *installation_folder*map \Bin (waarbij *installation_folder* is de map waarin u geïnstalleerde MDT.)|  
|**DesignerType**|Geeft de naam van de wizard editor binnen het DLL-bestand dat is opgegeven in de **DesignerAssembly** kenmerk (dit is de Microsoft .NET-type voor de wizard-editor met de volledig gekwalificeerde Microsoft .NET-naamruimte.)|  
|**DisplayName**|Hiermee geeft u de beschrijvende naam van de pagina-editor, zoals wordt weergegeven in de Wizard UDI Designer|  
|**DLL**|Geeft de naam van het DLL-bestand dat is gekoppeld aan de wizardpagina (het DLL-bestand moet bestaan in de *installation_folder*\Templates\Distribution\Tools\\*platform* map (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd en *platform* is **x86** voor de 32-bits versie of **x64** is voor de 64-bits-versie.) **Opmerking:**  Zorg ervoor dat de processorarchitectuur van DLL-bestand overeenkomt met de processorarchitectuur MDT is geïnstalleerd. Bijvoorbeeld, als u een 32-bits versie van MDT hebt geïnstalleerd, zorgt dat u een 32-bits DLL-bestand gebruiken voor de wizardpagina.|  
|**Afbeelding**|Hiermee geeft u de naam van een installatiekopie van de pagina met Portable Network Graphics (PNG)-indeling (PNG-bestand moet bestaan in de *installation_folder*\Bin\Images map (waarbij *installation_folder* is de de map waarin u MDT hebt geïnstalleerd.)|  
|**Type**|Hiermee geeft u de wizard-editor en moet overeenkomen met de benoemde gebruikt wanneer de aangepaste pagina is geregistreerd|  

##### <a name="remarks"></a>Opmerkingen  
 De waarde van de Wizard UDI gebruikt de [pagina](#Page) element als een sjabloon maken van het eerste XML-bestand voor een nieuwe wizard. De waarde van de Wizard UDI voert schemavalidatie om ervoor te zorgen dat de [pagina](#Page) en onderliggende elementen hebben een ongeldige indeling. Dit element bevat een koppeling tussen het type van de Wizard UDI pagina en de informatie die de waarde van de Wizard UDI nodig heeft om te bewerken en maken van pagina's van dit type met een aangepaste pagina-editor.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Param"></a> Param  
 Dit element wordt een parameter die wordt doorgegeven aan de bovenliggende [taak](#Task) of [Validator](#Validator) element en komt overeen met een [Setter]() element in het configuratiebestand van de Wizard UDI.  

> [!NOTE]
>  De kenmerken voor dit element zijn verschillend als de bovenliggende de [taak](#Task) of [Validator](#Validator) element.  

##### <a name="element-information"></a>Elementgegevens  
 Tabel 59 bevat informatie over de [Param](#Param) element.  

### <a name="table-59-param-element-information"></a>Tabel 59. Param elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer voor elk [TaskItem](#TaskItem) of [Validator](#Validator) bovenliggend element|  
|Bovenliggende elementen|**TaskItem**, **Validator**|  
|Inhoud|Juist opgemaakte XML-inhoud|  

##### <a name="element-attributes"></a>Elementkenmerken  
  60 tabel zijn de kenmerken van de [Param](#Param) element en biedt een beschrijving van elke.  

### <a name="table-60-attributes-and-corresponding-values-for-the-param-element"></a>Tabel 60. Kenmerken en bijbehorende waarden voor het Element Param  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Beschrijving**|Hiermee geeft u de tekst die informatie biedt over de parameter die wordt weergegeven in de ontwerpfunctie van de Wizard UDI **Opmerking:**  Dit kenmerk is alleen geldig voor de [Validator](#Validator) element.|  
|**DisplayName**|Hiermee geeft u de beschrijvende naam van de validatiefunctie-parameter die wordt weergegeven voor de betreffende Wizard UDI pagina in de ontwerpfunctie van de Wizard UDI (deze naam is meestal de meer beschrijvende dan de **naam** kenmerk.) **Opmerking:**  Dit kenmerk is alleen geldig voor de [Validator](#Validator) element.|  
|**Naam**|Hiermee geeft u de naam van de parameter die wordt doorgegeven aan de taak of de validatiefunctie, afhankelijk van het bovenliggende element (dit kenmerk worden de **eigenschap** kenmerk in een [Setter]() element in de Wizard UDI het configuratiebestand.) **Opmerking:**  Deze parameter wordt gebruikt voor zowel [TaskItem](#TaskItem) en [Validator](#Validator) bovenliggende elementen.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Task"></a> Taak  
 Dit element bevat een taak in de tapewisselaar taak.  

##### <a name="element-information"></a>Elementgegevens  
 61 tabel bevat informatie over de [taak](#Task) element.  

### <a name="table-61-task-element-information"></a>61 van de tabel. Element taakgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer binnen de [TaskLibrary](#TaskLibrary) element (dit element is niet optioneel als de **TaskLibrary** element is opgegeven.)|  
|Bovenliggende elementen|**TaskLibrary**|  
|Inhoud|**TaskItem**|  

##### <a name="element-attributes"></a>Elementkenmerken  
  Tabel 62 zijn de kenmerken van de [taak](#Task) element en biedt een beschrijving van elke.  

### <a name="table-62-attributes-and-corresponding-values-for-the-task-element"></a>Tabel 62. Kenmerken en bijbehorende waarden voor het taakelement  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Beschrijving**|Hiermee geeft u de tekst die informatie biedt over de taak, die wordt weergegeven in de Wizard UDI Designer|  
|**DLL**|Geeft de naam van het DLL-bestand dat is gekoppeld aan de taak (het DLL-bestand moet bestaan in de *installation_folder*\Templates\Distribution\Tools\\*platform* map (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd en *platform* is **x86** voor de 32-bits versie of **x64** voor de 64 -bitsversie.)|  
|**Naam**|Hiermee geeft u de naam van de taak die wordt weergegeven in de desbetreffende pagina van de Wizard UDI en in de Wizard UDI Designer|  
|**Type**|Hiermee geeft u het taaktype dat is geregistreerd bij de factory-register en gebruikt voor het aanroepen van een specifieke taak binnen een DLL-bestand|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="TaskItem"></a> TaskItem  
 Dit element bevat een aantal parameters die zijn doorgegeven aan de taak.  

##### <a name="element-information"></a>Elementgegevens  
  Tabel 63 bevat informatie over de [TaskItem](#TaskItem) element.  

### <a name="table-63-taskitem-element-information"></a>Tabel 63. TaskItem elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer voor elk **taak** element|  
|Bovenliggende elementen|**Task**|  
|Inhoud|**Param**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Tabel-64 geeft een lijst van de kenmerken van de [TaskItem](#TaskItem) element en biedt een beschrijving van elke.  

### <a name="table-64-attribute-and-corresponding-values-for-the-taskitem-element"></a>Tabel 64. Kenmerk en de bijbehorende waarden voor het Element TaskItem  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Type**|Hiermee geeft u het soort element dat wordt gemaakt in het configuratiebestand van de Wizard UDI. Een XML-element er wordt gemaakt die overeenkomt met de waarde van dit kenmerk. Bijvoorbeeld, als de waarde voor dit kenmerk is [bestand](#File), en vervolgens een **bestand** element wordt gemaakt in het configuratiebestand van de Wizard UDI.<br /><br /> Op dit moment zijn de enige waarden die ondersteund:<br /><br /> -   **Bestand**, die vereist twee [Param](#Param) onderliggende elementen (één **Param** onderliggend element met de **naam** -kenmerk ingesteld op **bron**en een andere **Param** onderliggend element met de **naam** -kenmerk ingesteld op **Dest**)<br />-   [Setter](), waarvoor een **Param** onderliggend element|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="TaskLibrary"></a> TaskLibrary  
 Dit element een set met groepen [taak](#Task) elementen.  

##### <a name="element-information"></a>Elementgegevens  
 Tabel 65 bevat informatie over de [TaskLibrary](#TaskLibrary) element.  

### <a name="table-65-tasklibrary-element-information"></a>Tabel 65. TaskLibrary elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of één binnen de [DesignerConfig](#DesignerConfig) element (dit element is optioneel als er zijn geen aangepaste taken in de DLL die met dit configuratiebestand van de Wizard UDI overeenkomen.)|  
|Bovenliggende elementen|**DesignerConfig**|  
|Inhoud|**Task**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<DesignerConfig>  
   - <TaskLibrary>  
        +<Task DLL="" Description="Executes a process with the given command line." Type="Microsoft.Wizard.ShellExecuteTask" Name="Shell Execute Task">  
        +<Task DLL="OSDRefreshWizard.dll" Description="Discovers supported applications for install." Type="Microsoft.OSDRefresh.AppDiscoveryTask" Name="Application Discovery">  
        +<Task DLL="SharedPages.dll" Description="Check to ensure a wired network connection is available." Type="Microsoft.SharedPages.WiredNetworkTask" Name="Wired Network Check">  
        +<Task DLL="OSDRefreshWizard.dll" Description="Check to ensure power source is AC (not battery)." Type="Microsoft.OSDRefresh.ACPowerTask" Name="AC Power Check">  
        +<Task DLL="" Description="Check to ensure power source is AC (not battery)." Type="Microsoft.Wizard.CopyFilesTask" Name="Copy Files Task">  
     </TaskLibrary>  
   + <ValidatorLibrary>  
   + <DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="Validator"></a> Validator  
 Dit element bevat een validator in de tapewisselaar validator.  

##### <a name="element-information"></a>Elementgegevens  
 Tabel 66 bevat informatie over de [Validator](#Validator) element.  

### <a name="table-66-validator-element-information"></a>Tabel 66. Validator elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen de [ValidatorLibrary](#ValidatorLibrary) element (dit element is optioneel.)|  
|Bovenliggende elementen|**ValidatorLibrary**|  
|Inhoud|**Param**|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 67 hier worden de kenmerken van de [Validator](#Validator) element en biedt een beschrijving van elke.  

### <a name="table-67-attributes-and-corresponding-values-for-the-validator-element"></a>Tabel 67. Kenmerken en bijbehorende waarden voor het Element Validator  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Beschrijving**|Hiermee geeft u de tekst die informatie biedt over de validatiefunctie, dat wordt weergegeven in de Wizard UDI Designer|  
|**DisplayName**|Hiermee geeft u de beschrijvende naam van de validatiefunctie weergegeven in de waarde van de Wizard UDI (deze naam is meestal de meer beschrijvende dan de **naam** kenmerk.)|  
|**DLL**|Geeft de naam van het DLL-bestand dat is gekoppeld aan de validator (het DLL-bestand moet bestaan in de *installation_folder*\Templates\Distribution\Tools\\*platform* map (waarbij *installation_folder* is de map waarin u MDT hebt geïnstalleerd en *platform* is **x86** voor de 32-bits versie of **x64** voor de 64-bits-versie.)|  
|**Naam**|Geeft de naam van de validatiefunctie, dat wordt weergegeven in de desbetreffende pagina van de Wizard UDI en in de Wizard UDI Designer|  
|**Type**|Hiermee geeft u het validatietype, dat is geregistreerd bij de Register-factor en gebruikt voor het aanroepen van een specifieke validatiefunctie binnen een DLL-bestand|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="ValidatorLibrary"></a> ValidatorLibrary  
 Dit element een set met groepen [Validator](#Validator) elementen.  

##### <a name="element-information"></a>Elementgegevens  
 Tabel 68 bevat informatie over de [ValidatorLibrary](#ValidatorLibrary) element.  

### <a name="table-68-validatorlibrary-element-information"></a>Tabel 68. ValidatorLibrary elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of één binnen de [DesignerConfig](#DesignerConfig) element (dit element is optioneel als er geen aangepaste Validators bestaat in de DLL die met dit configuratiebestand van de Wizard UDI overeenkomen.)|  
|Bovenliggende elementen|**DesignerConfig**|  
|Inhoud|**Validator**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 < DesignerConfig\> + < TaskLibrary\> -< ValidatorLibrary\> + < Validator DLL = ' ' Beschrijving Type="Microsoft.Wizard.Validation.NonEmpty 'Tekst in een veld is vereist' = ' Name = 'NonEmpty'\> + < validator DLL = ' ' beschrijving = 'Bepaalde tekens in een veld niet toestaan' Type="Microsoft.Wizard.Validation.InvalidChars ' Name = '%{invalidchars/'\> + < Validator DLL = ' ' beschrijving = 'Moet een vooraf gedefinieerde patroon volgen' Type = ' Microsoft.Wizard.Validation.RegEx' Name = 'NamedPattern'\> + < Validator DLL = "' Beschrijving Type="Microsoft.Wizard.Validation.RegEx 'Moet de inhoud overeenkomt met een reguliere expressie' = ' naam = 'RegEx'\> < / ValidatorLibrary\> + < DesignerMappings\>< / DesignerConfig\>  

## <a name="udi-wizard-designer-reference"></a>UDI Wizard Designer verwijzing  

### <a name="controls"></a>Besturingselementen  
 De besturingselementen die wordt gebruikt voor het maken van aangepaste wizardpagina editors voor gebruik in de ontwerpfunctie van de Wizard UDI zijn WPF **UserControl** exemplaren. 69 tabel staan de besturingselementen die u gebruiken kunt voor het maken van aangepaste wizard pagina editors.  

### <a name="table-69-controls-that-can-be-used-to-create-custom-wizard-page-editors"></a>Tabel 69. Besturingselementen die kunnen worden gebruikt voor het maken van aangepaste Wizard pagina Editors  

|Besturingselement|Beschrijving|  
|-|-|  
|[CollectionTControl](#CollectionTControl)|Dit besturingselement wordt gebruikt voor het bewerken van gegevens die zijn opgeslagen de [gegevens](#Data) element in een [pagina](#Page) element.|  
|[FieldElementControl](#FieldElementControl)|Dit besturingselement wordt gebruikt voor het bewerken van een veld dat normaal gesproken is gekoppeld aan een besturingselement TextBox in het .xaml-pagina.|  
|[SetterControl](#SetterControl)|Dit besturingselement wordt gebruikt voor het wijzigen van de waarde van een [setter]() element in het configuratiebestand van de Wizard UDI.|  

####  <a name="CollectionTControl"></a> CollectionTControl  
 Dit besturingselement biedt veel mogelijkheden om gegevens te bewerken. De beste manier om informatie over het gebruik van dit besturingselement is om te kijken naar het voorbeeld, waarin het bewerken van gegevens onder een pagina **gegevens** element. In het bijzonder toont het voorbeeld hoe u wilt toevoegen, verwijderen en bewerken van items in dit besturingselement.  

####  <a name="FieldElementControl"></a> FieldElementControl  
 Gebruik dit besturingselement om te bewerken van een veld dat is meestal gekoppeld aan een **TextBox** besturingselement op de pagina .xaml.  

##### <a name="example"></a>Voorbeeld  
 Het volgende fragment van een .xaml-bestand ziet u het gebruik van de **FieldElementControl** voor het configureren van de standaardwaarde voor een veld op een pagina van de wizard met behulp van een onderliggend element **TextBox** besturingselement:  

```  
<Controls:FieldElementControl  
Width="450"  
Margin="0,5"  
FieldData="{Binding DataContext.Location, ElementName=ControlRoot}"  
HeaderText="Location Combo Box"  
InstructionText="Here you can configure the behavior of the location combo box."  
HideValidationTab="True">  

<TextBox Text="{Binding FieldData.DefaultValue,  
 UpdateSourceTrigger=PropertyChanged,  
 Mode=TwoWay}"/>  
</Controls:FieldElementControl>  
```  

##### <a name="properties"></a>Eigenschappen  

###### <a name="fielddata"></a>FieldData  
 Deze eigenschap bevat informatie voor het verbinden van de **FieldElementControl** naar de onderliggende XML voor het veld. De verbinding wordt gemaakt met een eigenschap van de interface van pagina-editor. Het volgende fragment van een .xaml-bestand ziet u het gebruik van de **FieldData** eigenschap:  

```  
FieldData="{Binding DataContext.Location, ElementName=ControlRoot}"  
```  

 In dit fragment, de interface van de editor pagina heet **ControlRoot** en is opgegeven in de **ElementName** parameter. De binding wordt uitgevoerd op de **DataContext.Location** eigenschap van de **ControlRoot** interface voor pagina-editor. **DataContext** is een model weergeven die naar verwijst de [pagina](#Page) element in het configuratiebestand van de Wizard UDI. **Locatie** is een eigenschap van de weergave die resulteert in een lijst van de mogelijke locaties en wordt gedefinieerd door een [gegevens](#Data) element in het configuratiebestand van de Wizard UDI. Elke locatie wordt gedefinieerd door een [DataItem](#DataItem) element in het configuratiebestand van de Wizard UDI.  

###### <a name="headertext"></a>HeaderText  
 Deze eigenschap kunt u opgeven van een koptekst voor de [FieldElementControl](#FieldElementControl) besturingselement. De header fungeert als een titel voor het besturingselement en is opgemaakt als vet, oranje tekst onmiddellijk weergegeven boven het besturingselement.  

###### <a name="instructiontext"></a>InstructionText  
 Deze eigenschap kunt u opgeven informatieve tekst voor de [FieldElementControl](#FieldElementControl) besturingselement. De tekst wordt normaal gesproken gebruikt om te bieden een korte beschrijving van het veld en wordt uitgelegd hoe het configureren van het veld gevolgen voor de bijbehorende wizardpagina.  

###### <a name="hideenablebutton"></a>HideEnableButton  
 Deze Boole-eigenschap kunt u bepalen van de zichtbaarheid van de knop die verandert van status tussen **ontgrendeld** en **vergrendeld** (ingeschakeld of uitgeschakeld). Indien ingesteld op:  

-   **De waarde True**, de knop is niet zichtbaar  

-   **ONWAAR**, de knop zichtbaar is (dit is de standaardwaarde).  

###### <a name="hidedefaulttab"></a>HideDefaultTab  
 Deze Boole-eigenschap kunt u bepalen van de zichtbaarheid van de sectie met het besturingselement dat wordt gebruikt voor het instellen van de standaardwaarde. Hoewel de eigenschap naar een tabblad verwijst, er is geen tabblad op de [FieldElementControl](#FieldElementControl) , maar in plaats daarvan een sectie die kan worden verborgen. Indien ingesteld op:  

-   **De waarde True**, de sectie is niet zichtbaar  

-   **ONWAAR**, de sectie zichtbaar is (dit is de standaardwaarde).  

###### <a name="hideborder"></a>HideBorder  
 Deze Boole-eigenschap kunt u de zichtbaarheid van de rand om het besturingselement voor het regelen. Indien ingesteld op:  

-   **De waarde True**, de rand is niet zichtbaar  

-   **ONWAAR**, de rand zichtbaar is (dit is de standaardwaarde).  

###### <a name="hideimage"></a>HideImage  
 Deze Boole-eigenschap Hiermee bepaalt u de zichtbaarheid van de afbeelding die de **FieldImageSource** eigenschap wordt geconfigureerd. Indien ingesteld op:  

-   **De waarde True**, de installatiekopie is niet zichtbaar  

-   **ONWAAR**, de afbeelding wordt weergegeven (dit is de standaardwaarde).  

###### <a name="hidevalidationtab"></a>HideValidationTab  
 Deze Boole-eigenschap kunt u bepalen van de zichtbaarheid van de sectie waar de lijst met validatiefuncties wordt beheerd. Hoewel de eigenschap naar een tabblad verwijst, er is geen tabblad op de [FieldElementControl](#FieldElementControl) , maar in plaats daarvan een sectie die kan worden verborgen. Indien ingesteld op:  

-   **De waarde True**, de sectie is niet zichtbaar  

-   **ONWAAR**, de sectie zichtbaar is (dit is de standaardwaarde).  

###### <a name="hidesummarytab"></a>HideSummaryTab  
 Deze Boole-eigenschap kunt u bepalen van de zichtbaarheid van de sectie waarin u het bijschrift van het veld Samenvatting configureren. Het bijschrift en de bijbehorende waarde uit het veld worden weergegeven op een **overzichtspagina** wizard paginatype in een stroom fase. Hoewel de eigenschap naar een tabblad verwijst, er is geen tabblad op de [FieldElementControl](#FieldElementControl) , maar in plaats daarvan een sectie die kan worden verborgen. Indien ingesteld op:  

-   **De waarde True**, de sectie is niet zichtbaar  

-   **ONWAAR**, de sectie zichtbaar is (dit is de standaardwaarde).  

###### <a name="hidetasksequencetab"></a>HideTaskSequenceTab  
 Deze Boole-eigenschap kunt u bepalen van de zichtbaarheid van de sectie waarin u de takenreeksvariabele die overeenkomt met het veld configureren. Hoewel de eigenschap naar een tabblad verwijst, er is geen tabblad op de [FieldElementControl](#FieldElementControl) , maar in plaats daarvan een sectie die kan worden verborgen. Indien ingesteld op:  

-   **De waarde True**, de sectie is niet zichtbaar  

-   **ONWAAR**, de sectie zichtbaar is (dit is de standaardwaarde).  


####  <a name="SetterControl"></a> SetterControl  
 Gebruik dit besturingselement om te wijzigen van de waarde van een [Setter]() element in het configuratiebestand van de Wizard UDI. Dit besturingselement bevat een onderliggend besturingselement gebruikt voor het wijzigen van de waarde van de **setter** element.  

##### <a name="example"></a>Voorbeeld  
 Het volgende fragment van een .xaml-bestand ziet u het gebruik van de **SetterControl** wijzigen een [Setter]() element met de naam **KeyLocationSetter** met behulp van een onderliggende **TextBox** besturingselement.  

```  
<Controls:SetterControl Margin="5"  
        Width="450"  
        HeaderText="Title text"  
        SetterData="{Binding KeyLocationSetter}"   
        InstructionText="What this means…"  
        HorizontalAlignment="Left">  

    <TextBox  
                   Margin="0,3"  
                   Text="{Binding SetterData.SetterValue, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"  
    />  

</Controls:SetterControl>  
```  

##### <a name="properties"></a>Eigenschappen  

###### <a name="setterdata"></a>SetterData  
 U moet dit te binden aan een eigenschap van de weergave of het model weergeven die verbinding met de setter-methode maakt. In dat geval is vergelijkbaar met hoe u aan een veld binden wilt, zoals beschreven voor de **FieldElementControl**.  

###### <a name="headertext"></a>HeaderText  
 Deze eigenschap kunt u de tekst die wordt weergegeven in de header van het besturingselement instellen. Deze eigenschap zien als een titel voor het besturingselement. Standaard wordt deze weergegeven als vet, oranje tekst.  

###### <a name="instructiontext"></a>InstructionText  
 Deze eigenschap instellen op de tekst die moet worden weergegeven onder de kop, meestal de tekst waarin wordt gemeld dat de gebruiker van uw aangepaste editor wanneer en waarom hij of zij willen zou om het gedrag van het veld te wijzigen.  

### <a name="interfaces"></a>Interfaces  
Tabel 70 zijn de interfaces die u gebruiken kunt voor het maken van aangepaste wizard pagina editors.  

### <a name="table-70-interfaces-that-can-be-used-to-create-custom-wizard-page-editors"></a>Tabel 70. Interfaces die kunnen worden gebruikt voor het maken van aangepaste Wizard pagina Editors  

|**Interface**|**Beschrijving**|  
|-|-|  
|[IDataService](#IDataService)|Deze interface velden in om verbinding te gebruiken de **gegevens** elementen in het configuratiebestand van de Wizard UDI.|  
|[IMessageBoxService](#IMessageBoxService)|Deze interface biedt toegang tot methoden die u gebruiken kunt om berichten weer te geven.|  

####  <a name="IDataService"></a> IDataService  
 Deze interface bevat verschillende eigenschappen en methoden, maar er is slechts één eigenschap dat u net als nodig. Deze eigenschap is de enige ze hier zijn beschreven.  

 U kunt afhankelijkheidsinjectie gebruiken om op te halen van een verwijzing naar deze interface met code als volgt in uw klasse:  

```  
[Dependency]  
public IDataService DataService { get; set; }  
```  

##### <a name="properties"></a>Eigenschappen  
 71 tabel bevat de eigenschappen voor de **IDataService** interface.  

### <a name="table-71-properties-for-the-idataservice-interface"></a>Tabel 71. Eigenschappen voor de Interface IDataService  

|**Interface**|**Beschrijving**|  
|-|-|  
|[CurrentPage](#CurrentPage)|Deze eigenschap biedt toegang tot de XML-elementen, kenmerken en waarden onder de context van de huidige pagina in het configuratiebestand van de Wizard UDI wordt bewerkt|  

######  <a name="CurrentPage"></a> CurrentPage  

```  
XElement CurrentPage { get; set; }  
```  

 Deze eigenschap biedt toegang tot de XML voor de huidige pagina. U moet deze eigenschap niet instellen, maar u het XML-bestand voor uw pagina wijzigen. De editor voorbeeld ziet u voorbeelden van het wijzigen van het XML-bestand. U gebruikt deze eigenschap voornamelijk wanneer u aangepaste gegevens hebt. Velden en eigenschappen (setters), kunt u vooraf gedefinieerde besturingselementen die voor alle details zorgt.  

####  <a name="IMessageBoxService"></a> IMessageBoxService  
 Deze interface biedt toegang tot methoden die u gebruiken kunt om berichten weer te geven. U vraagt zich misschien af waarom moet u een interface voor het weergeven van het bericht. De realiteit is dat u dit niet doet: Microsoft gebruikt deze interface met in code, omdat het helpt bij het schrijven van automatische tests voor designer's.  

 Gebruik van deze methoden biedt echter een handig voordeel: De dialoogvensters hebben altijd 'eigenaar' ingesteld op de Wizard UDI, die zorgt ervoor dat in het dialoogvenster met het hoofdvenster correct is gegroepeerd.  

 U kunt afhankelijkheidsinjectie gebruiken om op te halen van een verwijzing naar deze interface met code als volgt in uw klasse:  

```  
[Dependency]  
public IMessageBoxService MessageBoxes { get; set; }  
```  

##### <a name="methods"></a>Methoden  
 72 tabel vermeldt de methoden voor het **IMessageBoxService** interface.  

### <a name="table-72-methods-for-the-imessageboxservice-interface"></a>Tabel 72. Methoden voor de Interface IMessageBoxService  

|**Methode**|**Beschrijving**|  
|-|-|  
|[ShowMessageBox](#ShowMessageBox)|Deze overbelaste methode wordt gebruikt om een berichtvenster met de volgende leden weer te geven:<br /><br /> -   [ShowMessageBox (Tekenreeksbericht, tekenreeks bijschrift, MessageBoxImage pictogram)](#ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon)<br />-   [ShowMessageBox (Tekenreeksbericht, tekenreeks bijschrift, MessageBoxButton knop, MessageBoxImage pictogram)](#ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon)<br />-   [ShowMessageBox (uitzondering uitzondering)](#ShowMessageBox_Exception_exception)|  
|[ShowDialogWindow](#ShowDialogWindow)|Gebruik deze methode voor het maken van een nieuw dialoogvenster.|  
|[ShowWizardWindow](#ShowWizardWindow)|Gebruik deze methode om weer te geven van een aangepaste editor in een dialoogvenster waarin **volgende** en **terug** knoppen voor navigatie.|  

######  <a name="ShowMessageBox"></a> ShowMessageBox  
 Deze methode wordt het bericht dat een onderliggend element van de editor aangepaste wizard weergegeven. Dit lid is overbelast: Tabel 73 bevat een lijst van de leden en een korte beschrijving van elke. Zie de sectie die overeenkomt met elk lid voor volledige informatie over elk lid (inclusief syntaxis, syntaxis en voorbeelden).  

### <a name="table-73-overloaded-members-for-the-showmessagbox-method"></a>Tabel 73. Overbelaste leden voor de methode ShowMessagBox  

|Lid|Beschrijving|  
|-|-|  
|[ShowMessageBox (Tekenreeksbericht, tekenreeks bijschrift, MessageBoxImage pictogram)](#ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon)|Geeft een berichtvenster met een pictogram en een **OK** knop|  
|[ShowMessageBox (Tekenreeksbericht, tekenreeks bijschrift, MessageBoxButton knop, MessageBoxImage pictogram)](#ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon)|Geeft een berichtvenster met een pictogram en verschillende mogelijke combinaties van knoppen|  
|[ShowMessageBox (uitzondering uitzondering)](#ShowMessageBox_Exception_exception)|Geeft een berichtvenster bevat informatie over een uitzondering veroorzaakt en is een **OK** knop|  

######  <a name="ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon"></a> ShowMessageBox (Tekenreeksbericht, tekenreeks bijschrift, MessageBoxImage pictogram)  

```  
void ShowMessageBox(String message, String caption, MessageBoxImage icon);  
```  

 Deze methode wordt een berichtvenster met een **OK** knop. Zie tabel 74.  

### <a name="table-74-parameters-for-the-showmessageboxstring-message-string-caption-messageboximage-icon-method"></a>Tabel 74. Parameters voor de methode ShowMessageBox(String message, String caption, MessageBoxImage icon)  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Bericht**|Het bericht dat wordt weergegeven in het gebied van de inhoud van het bericht|  
|**Bijschrift**|De tekst in de titelbalk van het dialoogvenster worden weergegeven|  
|**icon**|Het type van het pictogram moet worden weergegeven in het berichtvenster|  

######  <a name="ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon"></a> ShowMessageBox (Tekenreeksbericht, tekenreeks bijschrift, MessageBoxButton knop, MessageBoxImage pictogram)  

```  
MessageBoxResult ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon);  
```  

 Deze methode wordt weergegeven een berichtvenster met de set knoppen die u weergeven wilt en rapporten welke knop geklikt. Zie tabel 75.  

### <a name="table-75-parameters-for-the-showmessageboxstring-message-string-caption-messageboxbutton-button-messageboximage-icon-method"></a>Tabel 75. Parameters voor de methode ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon)  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Bericht**|Het bericht dat wordt weergegeven in het gebied van de inhoud van het bericht|  
|**Bijschrift**|De tekst in de titelbalk van het dialoogvenster worden weergegeven|  
|**Knop**|Welke knoppen om weer te geven|  
|**icon**|Het type van het pictogram moet worden weergegeven in het berichtvenster|  

######  <a name="ShowMessageBox_Exception_exception"></a> ShowMessageBox (uitzondering uitzondering)  

```  
void ShowMessageBox(Exception exception);  
```  

 Deze methode een bericht in het rapport informatie over een uitzondering wordt weergegeven. Dit berichtvenster heeft één **OK** knop. Zie tabel 76.  

### <a name="table-76-parameters-for-the-showmessageboxexception-exception-method"></a>Tabel 76. Parameters voor de methode ShowMessageBox(Exception exception)  

|**Parameter**|**Beschrijving**|  
|-|-|  
|**Uitzondering**|De uitzondering die u rapporteren wilt (maakt gebruik van het dialoogvenster **uitzondering. Bericht** als de inhoud.)|  

######  <a name="ShowDialogWindow"></a> ShowDialogWindow  

```  
void ShowDialogWindow(Type viewType, DialogInteraction dialogPayload);  
```  

 Deze methode maakt u een nieuw dialoogvenster, de inhoud die de tekst is die u opgeeft de **viewType** parameter. De Designer UDI maakt een nieuw exemplaar van dit type en het verpakt in een dialoogvenster met **OK** en **annuleren** knoppen.  

 U kunt gegevens doorgeven aan het besturingselement met de parameter dialogPayload. De **SampleEditor** oplossing in de map SDK bevat een voorbeeld van hoe deze functie kunt gebruiken.  

######  <a name="ShowWizardWindow"></a> ShowWizardWindow  

```  
void ShowWizardWindow(Type viewType, DialogInteraction dialogPayload);  
```  

 Deze methode kunt u een aangepaste editor in een dialoogvenster waarin weergeven **volgende** en **terug** knoppen voor navigatie. Microsoft is niet opgegeven voor een voorbeeld voor het gebruik van deze methode.  

###  <a name="UDIWizardConfigurationFileSchemaReference"></a> UDI Wizard Configuratie-bestandsverwijzing Schema  
 Dit bestand wordt gebruikt door de Wizard UDI en geconfigureerd door de waarde van de Wizard UDI. Dit bestand wordt gebruikt voor het configureren van de:  

-   Wizardpagina's weergegeven in de Wizard UDI  

-   De volgorde van de wizardpagina's in de Wizard UDI  

-   Instellingen voor de velden op elke wizardpagina  

-   Beschikbare StageGroups in de Wizard UDI Designer  

-   Beschikbare fasen binnen elke implementatiewizard in de Wizard UDI Designer  

  77 bevat de elementen in het configuratiebestand van de UDI Wizard en de bijbehorende beschrijvingen. De **Wizard** element is het hoofdknooppunt voor deze verwijzing.  

### <a name="table-77-elements-in-the-udi-wizard-configuration-file-and-their-descriptions"></a>Tabel 77. Elementen in het configuratiebestand van de UDI Wizard en de bijbehorende beschrijvingen  

|**Elementnaam**|**Beschrijving**|  
|-|-|  
|[Data](#Data)|De afzonderlijke groepen [DataItem](#DataItem) elementen in een [pagina](#Page) element en de naam is door de **naam** kenmerk.|  
|[DataItem](#DataItem)|De afzonderlijke groepen [Setter]() elementen in een [pagina](#Page) element. U kunt hiërarchische gegevens maken door een of meer [gegevens](#Data) elementen in een [DataItem](#DataItem) element. Elke **DataItem** element vertegenwoordigt een afzonderlijke item. Bijvoorbeeld, een lijst van beschikbare schijven wellicht een **DataItem** voor de weergavenaam en een andere **DataItem** element voor de bijbehorende stationsletter.|  
|[Standaard](#Default)|Hiermee geeft u een standaardwaarde voor het veld dat is opgegeven in de bovenliggende [veld](#Field) of [groep met keuzerondjes](#RadioGroup) element. De standaardwaarde is ingesteld op de waarde tussen dit element.|  
|[DLL](#DLL)|Hiermee geeft u een DLL-bestand dat moet worden geladen en waarnaar wordt verwezen door de Wizard UDI en de waarde van de Wizard UDI.|  
|[DLL-bestanden](#DLLs)|De afzonderlijke groepen [DLL](#DLL) elementen.|  
|[Error](#Error)|Hiermee geeft u een mogelijke foutcode die een taak kan kunt terugkeren. De waarde van de foutcode is geretourneerd door de taak **HRESULT** en wordt onderschept door dit element kunt u specifiekere foutinformatie verstrekt.|  
|[ExitCode](#ExitCode)|Hiermee geeft u een mogelijke afsluitcode voor een taak. De afsluitcodes zijn retourcodes die de taak wordt verwacht. Maak een **ExitCode** element voor elke mogelijke afsluitcode. Anders kunt u een sterretje (\*) in de **waarde** kenmerk voor het afhandelen van retourcodes die niet wordt weergegeven in andere **ExitCode** elementen.|  
|[ExitCodes](#ExitCodes)|Een set met groepen [ExitCode](#ExitCode) en [fout](#Error) -elementen voor een [taak](#Task) element of een **fout** element.|  
|[Field](#Field)|Hiermee geeft u een exemplaar van een besturingselement in een [pagina](#Page) element dat wordt gebruikt voor aanpassing met XML. Niet alle besturingselementen kunt aanpassen met XML-alleen besturingselementen die gebruikmaken van de [veld](#Field) element.|  
|[Fields](#Fields)|De afzonderlijke groepen [veld](#Field) elementen in een [pagina](#Page) element.|  
|[Bestand](#File)|Hiermee geeft u de bron en bestemming voor een bestand kopiëren bewerking met de **Microsoft.Wizard.CopyFilesTask** type taak. U kunt een afzonderlijke opnemen **bestand** element meer dan één bestand kopiëren in één taak.|  
|[Pagina](#Page)|Hiermee geeft u een exemplaar van een pagina en bevat alle configuratie-instellingen voor de pagina.|  
|[PageRef](#PageRef)|Hiermee geeft u een verwijzing naar een exemplaar van een pagina binnen een [fase](#Stage) binnen een [StageGroup](#StageGroup).|  
|[Pagina 's](#Pages)|De afzonderlijke groepen [pagina](#Page) elementen.|  
|[RadioGroup](#RadioGroup)|Hiermee geeft u een groep keuzerondjes binnen een [veld](#Field) element.|  
|[StageGroup](#StageGroup)|Hiermee geeft u een groep van een of meer fasen.|  
|[StageGroups](#StageGroups)|Een set fase groepen in een configuratiebestand van de Wizard UDI gegroepeerd.|  
|[Setter]()|Hiermee geeft u de instelling van een eigenschap van een waarde voor een eigenschap met de naam in de **eigenschap** eigenschap.|  
|[Fase](#Stage)|Hiermee geeft u een fase binnen een [StageGroup](#StageGroup) en bevat een of meer [PageRef](#PageRef) elementen.|  
|[stijl](#Style)|De afzonderlijke groepen [setter]() elementen die de Wizard UDI uiterlijk, waaronder de titel wordt weergegeven aan de bovenkant van de wizard en de installatiekopie van het banner wordt weergegeven in de Wizard UDI configureren.|  
|[Task](#Task)|Hiermee geeft u een taak die moet worden uitgevoerd op de pagina die is opgegeven in de bovenliggende [pagina](#Page) element.|  
|[Taken](#Tasks)|Groepen van een aantal taken voor een [pagina](#Page) element.|  
|[Validator](#Validator)|Hiermee geeft u een controle voor het besturingselement dat is opgegeven in de bovenliggende [veld](#Field) element.|  
|[Wizard](#Wizard)|Hiermee geeft u de hoofdmap voor alle andere elementen.|  

####  <a name="Data"></a> Gegevens  
 Dit element de afzonderlijke groepen [DataItem](#DataItem) elementen in een [pagina](#Page) element en de naam is door de **naam** kenmerk.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 78 bevat informatie over de [gegevens](#Data) element.  

### <a name="table-78-data-element-information"></a>Tabel 78. Gegevens van Element  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen elke [pagina](#Page) element (dit element is optioneel.)|  
|Bovenliggende elementen|**Page**, **DataItem**|  
|Inhoud|**DataItem**, **Setter**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Tabel 79 hier worden de kenmerken van de [gegevens](#Data) element en biedt een beschrijving van elke.  

### <a name="table-79-attributes-and-corresponding-values-for-the-data-element"></a>Tabel 79. Kenmerken en bijbehorende waarden voor het gegevenselement  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Naam**|Geeft de naam van de [gegevens](#Data) element|  

##### <a name="remarks"></a>Opmerkingen  
 De **naam** kenmerk kunt u code voor het ophalen van een specifieke set gegevens.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="DataItem"></a> DataItem  
 Dit element de afzonderlijke groepen [Setter]() elementen in een [pagina](#Page) element. U kunt hiërarchische gegevens maken door een of meer [gegevens](#Data) elementen in een [DataItem](#DataItem) element. Elke **DataItem** element vertegenwoordigt een afzonderlijke item. Bijvoorbeeld, een lijst van beschikbare schijven wellicht een **DataItem** voor de weergavenaam en een andere **DataItem** element voor de bijbehorende stationsletter.  

##### <a name="element-information"></a>Elementgegevens  
 80 van de tabel bevat informatie over de [DataItem](#DataItem) element.  

### <a name="table-80-dataitem-element-information"></a>80 van de tabel. DataItem elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen elke [gegevens](#Data) element (dit element is optioneel.)|  
|Bovenliggende elementen|**Data**|  
|Inhoud|**Data**, **Setter**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

#### <a name="default"></a>Standaard  
 Dit element bevat een standaardwaarde voor het veld dat is opgegeven in de bovenliggende [veld](#Field) of [groep met keuzerondjes](#RadioGroup) element. De standaardwaarde is ingesteld op de waarde die dit element vierkante haken.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 81 bevat informatie over de [standaard](#Default) element.  

### <a name="table-81-default-element-information"></a>Tabel 81. Standaard-elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren |Nul of meer binnen een [veld](#Field) of [groep met keuzerondjes](#RadioGroup) element (dit element is optioneel.)|  
|Bovenliggende elementen|**Field**, **RadioGroup**|  
|Inhoud|Kan juist opgemaakte XML inhoud maar wordt doorgaans standaardtekst|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 In het volgende voorbeeld wordt de standaardwaarde voor de **tijdzone** veld is ingesteld op 'Pacific (standaardtijd)':  

```  
<Field Name="TimeZone" Enabled="true" VarName="OSDTimeZone" Summary="Time Zone:">  
  <Default>Pacific Standard Time</Default>  
```  

####  <a name="DLL"></a> DLL  
 Dit element bevat een DLL-bestand voor de Wizard UDI en de Wizard UDI laden en verwijzen naar.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 82 bevat informatie over de [DLL](#DLL) element.  

### <a name="table-82-dll-element-information"></a>Tabel 82. Elementgegevens dll-bestand  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer binnen de [dll's](#DLLs) element|  
|Bovenliggend element|**DLL-bestanden**|  
|Inhoud|Er is geen inhoud die is toegestaan voor dit element|  

##### <a name="element-attributes"></a>Elementkenmerken  
 83 tabel zijn de kenmerken van de [DLL](#DLL) element en biedt een beschrijving van elke.  

### <a name="table-83-attributes-and-corresponding-values-for-the-dll-element"></a>83 van de tabel. Kenmerken en bijbehorende waarden voor het DLL-Element  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|Name|Geeft de naam van het DLL-bestand voor de Wizard UDI en de Wizard UDI om te verwijzen naar|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<DLLs>  
  <DLL Name="OSDRefreshWizard.dll" />   
  <DLL Name="SharedPages.dll" />  
</DLLs>  
```  

####  <a name="DLLs"></a> DLL-bestanden  
 Dit element de afzonderlijke groepen [DLL](#DLL) elementen.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 84 bevat informatie over de [dll's](#DLLs) element.  

### <a name="table-84-dlls-element-information"></a>Tabel 84. Elementgegevens dll 's  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|een|  
|Bovenliggende elementen|**Wizard**|  
|Inhoud|**DLL**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<DLLs>  
   <DLL Name="OSDRefreshWizard.dll" />  
   <DLL Name="SharedPages.dll" />   
</DLLs>  
```  

####  <a name="Error"></a> Fout  
 Dit element bevat een mogelijke fout-code die een taak kan retourneren. De waarde van de foutcode is geretourneerd en onderschept door de taak **HRESULT** naar meer gedetailleerde foutinformatie verstrekt.  

##### <a name="element-information"></a>Elementgegevens  
 Tabel 85 bevat informatie over de [fout](#Error) element.  

### <a name="table-85-error-element-information"></a>Tabel 85. Informatie over de fout-Element  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen elke [ExitCode](#ExitCode) element (dit element is optioneel.)|  
|Bovenliggende elementen|**ExitCodes**|  
|Inhoud|Juist opgemaakte XML-inhoud|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Tabel 86 hier worden de kenmerken van de [fout](#Error) element en biedt een beschrijving van elke.  

###  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Status**|Hiermee geeft u de status van de afzender van een taak die is een fout opgetreden. Normaal gesproken wordt de waarde voor dit kenmerk ingesteld op fout worden ingesteld. Deze waarde wordt weergegeven in de **status** kolom in de wizard in de Wizard UDI.|  
|**Tekst**|Hiermee geeft u de beschrijvende tekst over de fout die de taak opgetreden.|  
|**Type**|Hiermee geeft u op of dit element een fout, waarschuwing of geslaagd vertegenwoordigt. De opgegeven waarde in**Type** moet uniek zijn binnen een [ExitCodes](#ExitCodes) element. De volgende zijn waarden geldig voor dit element:<br /><br /> -   **0.**het element vertegenwoordigen een is voltooid.<br />-   **1.** Het element vertegenwoordigt een waarschuwing.<br />-   **-1.** Het element vertegenwoordigt een fout.|  
|**Waarde**|Geeft de waarde van de code die de taak die is geretourneerd als een numerieke waarde. De waarde van een sterretje (*) geeft aan het standaardelement voor retourcodes die niet worden weergegeven in andere [fout](#Error) elementen.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="ExitCode"></a> ExitCode  
 Dit element bevat een mogelijk afsluitcode voor een taak. De afsluitcodes zijn retourcodes die de taak wordt verwacht. Maak een **ExitCode** element voor elke mogelijke afsluitcode. Anders kunt u een sterretje (\*) in de **waarde** kenmerk voor het afhandelen van retourcodes die niet wordt weergegeven in andere **ExitCode** elementen.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 87 bevat informatie over de [ExitCode](#ExitCode) element.  

### <a name="table-87-exitcode-element-information"></a>Tabel 87. ExitCode elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen elke [ExitCodes](#ExitCodes) element (dit element is optioneel.)|  
|Bovenliggende elementen|**ExitCodes**|  
|Inhoud|Ten minste één [ExitCode](#ExitCode) element en nul of meer [fout](#Error) elementen|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 88 hier worden de kenmerken van de [ExitCode](#ExitCode) element en biedt een beschrijving van elke.  

### <a name="table-88-attributes-and-corresponding-values-for-the-exitcode-element"></a>Tabel 88. Kenmerken en bijbehorende waarden voor het Element ExitCode  

|**Kenmerk**|Beschrijving|  
|-|-|  
|**Status**|Hiermee geeft u de status van de afzender van een taak. De waarde van dit kenmerk wordt weergegeven in de **status** kolom in de bijbehorende wizard in de Wizard UDI. U kunt geen waarden gebruiken voor dit kenmerk die relevant zijn voor de taak. Hier volgen typische waarden die voor dit kenmerk worden gebruikt:<br /><br /> -Geslaagd<br />-Waarschuwing<br />-Fout|  
|**Tekst**|Hiermee geeft u de beschrijvende tekst over de code bestaat van de taak.|  
|**Type**|Hiermee geeft u op of dit element een fout, waarschuwing of geslaagd vertegenwoordigt. De waarde die is opgegeven in het type moet uniek zijn binnen een [ExitCodes](#ExitCodes) element. De volgende zijn waarden geldig voor dit element:<br /><br /> -   **0.** Het element vertegenwoordigt een is voltooid.<br />-   **1.** Het element vertegenwoordigt een waarschuwing.<br />-   **-1.** Het element vertegenwoordigt een fout.|  
|**Waarde**|Geeft de waarde van de code die de taak die is geretourneerd als een numerieke waarde. De waarde van een sterretje (*) geeft aan het standaardelement voor retourcodes die niet worden weergegeven in andere [ExitCode](#ExitCode) elementen.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="ExitCodes"></a> ExitCodes  
 Dit element een set met groepen [ExitCode](#ExitCode) en [fout](#Error) -elementen voor een [taak](#Task) of een **fout** element.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 89 bevat informatie over de [ExitCodes](#ExitCodes) element.  

### <a name="table-89-exitcodes-element-information"></a>Tabel 89. ExitCodes elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een binnen elke [taak](#Task) element|  
|Bovenliggende elementen|**Task**|  
|Inhoud|**Error**, **ExitCode**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Field"></a> Veld  
 Dit element bevat een exemplaar van een besturingselement in een [pagina](#Page) element gebruikt voor aanpassing met XML. Niet alle besturingselementen kunt aanpassen met XML-alleen besturingselementen die gebruikmaken van de [veld](#Field) element.  

##### <a name="element-information"></a>Elementgegevens  
 Tabel 90 bevat informatie over de [veld](#Field) element.  

### <a name="table-90-field-element-information"></a>Tabel 90. Veld elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen elke [veld](#Field) element (dit element is optioneel.)|  
|Bovenliggende elementen|**Fields**|  
|Inhoud|**Standaard**, **Validator**|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 91 hier worden de kenmerken van de [veld](#Field) element en biedt een beschrijving van elke.  

### <a name="table-91-attributes-and-corresponding-values-for-the-field-element"></a>Tabel 91. Kenmerken en bijbehorende waarden voor het veldelement  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**ingeschakeld**|Geeft aan of het veld is ingeschakeld voor de gebruiker invoer (het kenmerk kan worden ingesteld op True of False.)|  
|**Naam**|Hiermee geeft u de naam van het veld|  
|**Samenvatting**|Hiermee geeft u de beschrijvende tekst die wordt weergegeven op de **samenvatting** wizardpagina voor de waarde die in dit veld wordt ingesteld|  
|**VarName**|Hiermee geeft u de variabele takenreeksnaam lezen of geconfigureerd met behulp van het veld in de bovenliggende [veld](#Field) element|  

##### <a name="remarks"></a>Opmerkingen  
 Dit element kan nul of meer bevatten [standaard](#Default) elementen en nul of meer [Validator](#Validator) elementen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Fields"></a> Velden  
 Dit element de afzonderlijke groepen [veld](#Field) elementen in een [pagina](#Page) element.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 92 bevat informatie over de [velden](#Fields) element.  

### <a name="table-92-fields-element-information"></a>Tabel 92. Elementgegevens velden  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen elke [pagina](#Page) element (dit element is optioneel.)|  
|Bovenliggende elementen|**Pagina**|  
|Inhoud|**Field**, **RadioGroup**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="File"></a> Bestand  
 Dit element geeft de bron en bestemming voor een bestand kopiëren bewerking met de **Microsoft.Wizard.CopyFilesTask** type taak. U kunt een afzonderlijke opnemen [bestand](#File) element meer dan één bestand kopiëren in één taak.  

##### <a name="element-information"></a>Elementgegevens  
 Tabel 93 bevat informatie over de [bestand](#File) element.  

### <a name="table-93-file-element-information"></a>Tabel 93. Bestandsgegevens van Element  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer voor elke taak die een type taak van **Microsoft.Wizard.CopyFilesTask**|  
|Bovenliggende elementen|**Task**|  
|Inhoud|Geen|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Tabel 94 hier worden de kenmerken van de [bestand](#File) element en biedt een beschrijving van elke.  

### <a name="table-94-attributes-and-corresponding-values-for-the-file-element"></a>Tabel 94. Kenmerken en bijbehorende waarden voor het Element File  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Dest**|Hiermee wordt het volledig gekwalificeerde of relatieve pad naar de doelmap voor het bestand dat is opgegeven in de **bron** kenmerk. Omgevingsvariabelen zijn toegestaan als onderdeel van het pad.|  
|**Bron**|Hiermee geeft u de volledig gekwalificeerde of relatieve pad naar de bron-bestand dat de **Microsoft.Wizard.CopyFilesTask** type kopieën van de taak. Dit kenmerk ondersteunt jokertekens bevatten, zodat meerdere bestanden kunnen worden gekopieerd met behulp van één [bestand](#File) element. Omgevingsvariabelen zijn toegestaan als onderdeel van het pad.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="PageElement"></a> Pagina  
 Dit element bevat een exemplaar van een pagina en bevat alle configuratie-instellingen voor de pagina.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 95 bevat informatie over de [pagina](#Page) element.  

### <a name="table-95-page-element-information"></a>Tabel 95. Pagina-Element-informatie  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer binnen elke [pagina's](#Pages) element|  
|Bovenliggende elementen|**Pagina 's**|  
|Inhoud|**Data**, **Fields**, **Setter**, **Tasks**|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 96 zijn de kenmerken van de [pagina](#Page) element en biedt een beschrijving van elke.  

### <a name="table-96-attributes-and-corresponding-values-for-the-page-element"></a>Tabel 96. Kenmerken en bijbehorende waarden voor het pagina-Element  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**DisplayName**|Hiermee geeft u de beschrijvende naam van de wizardpagina weergegeven in de waarde van de Wizard UDI. Deze naam is meestal de meer beschrijvende dan de **naam** kenmerk.|  
|**Naam**|Hiermee geeft u de naam van de wizardpagina weergegeven in de waarde van de Wizard UDI.|  
|**Type**|Geeft het type van de wizardpagina die rechtstreeks is gekoppeld aan een specifieke wizardpagina binnen een DLL-bestand.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="PageRef"></a> PageRef  
 Dit element bevat een verwijzing naar een exemplaar van een pagina binnen een [fase](#Stage) binnen een [StageGroup](#StageGroup).  

##### <a name="element-information"></a>Elementgegevens  
Tabel 97 bevat informatie over de [PageRef](#PageRef) element.  

### <a name="table-97-pageref-element-information"></a>Tabel 97. PageRef elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer binnen een [fase](#Stage) element|  
|Bovenliggende elementen|**Fase**|  
|Inhoud|Geen|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 98 geeft een lijst van het kenmerk van de [PageRef](#PageRef) element en bevat een beschrijving van deze.  

### <a name="table-98-attributes-and-corresponding-values-for-the-pageref-element"></a>Tabel 98. Kenmerken en bijbehorende waarden voor het Element PageRef  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Pagina**|Hiermee geeft u het exemplaar van een pagina binnen een [fase](#Stage) binnen een [StageGroup](#StageGroup). Deze waarde instelt op het naamkenmerk van een [pagina](#Page) element.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Pages"></a> Pagina 's  
 Dit element de afzonderlijke groepen [pagina](#Page) elementen.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 99 bevat informatie over de [pagina's](#Pages) element.  

### <a name="table-99-pages-element-information"></a>Tabel 99. Informatie over de elementen van pagina 's  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|een|  
|Bovenliggende elementen|**Wizard**|  
|Inhoud|**Pagina**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<Pages>  
   + <Page Name="WelcomePage" DisplayName="Welcome" Type="Microsoft.SharedPages.WelcomePage">  
   + <Page Name="ConfigScanPage" DisplayName="Deployment Readiness" Type="Microsoft.OSDRefresh.ConfigScanPage">  
   + <Page Name="ConfigScanBareMetal" DisplayName="Deployment Readiness" Type="Microsoft.OSDRefresh.ConfigScanPage">  
   + <Page Name="RebootPage" DisplayName="Reboot" Type="Microsoft.OSDRefresh.RebootPage">  
   + <Page Name="WelcomePageReplace" DisplayName="Welcome" Type="Microsoft.SharedPages.WelcomePage">  
   + <Page Name="VolumePage" DisplayName="Volume" Type="Microsoft.OSDRefresh.VolumePage">  
   + <Page Name="UserRestorePage" DisplayName="Select Target" Type="Microsoft.OSDRefresh.UserStatePage">  
   + <Page Name="ComputerPage" DisplayName="New Computer Details" Type="Microsoft.OSDRefresh.ComputerPage">  
   + <Page Name="AdminAccounts" DisplayName="Administrator Password" Type="Microsoft.SharedPages.AdminAccountsPage">  
   + <Page Name="UDAPage" DisplayName="User Device Affinity" Type="Microsoft.OSDRefresh.UDAPage">  
   + <Page Name="LanguagePage" DisplayName="Language" Type="Microsoft.OSDRefresh.LanguagePage">  
   + <Page Name="ApplicationPage" DisplayName="Install Programs" Type="Microsoft.OSDRefresh.ApplicationPage">  
     <Page Name="SummaryPage" DisplayName="Summary" Type="Microsoft.Shared.SummaryPage" />   
   + <Page Name="UserCapturePageOldPC" DisplayName="Select Target" Type="Microsoft.OSDRefresh.UserStatePage">  
   + <Page Name="ProgressPage" DisplayName="Capture Data" Type="Microsoft.OSDRefresh.ProgressPage">  
   + <Page Name="RebootAfterCapture" DisplayName="Reboot" Type="Microsoft.OSDRefresh.RebootPage">  
</Pages>  
```  

####  <a name="RadioGroup"></a> RadioGroup  
 Dit element bevat een groep keuzerondjes met in een [veld](#Field) element.  

##### <a name="element-information"></a>Elementgegevens  
100 van de tabel bevat informatie over de [groep met keuzerondjes](#RadioGroup) element.  

### <a name="table-100-radiogroup-element-information"></a>Tabel 100. Groep met keuzerondjes elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen een [velden](#Fields) element (dit element is optioneel.)|  
|Bovenliggende elementen|**Fields**|  
|Inhoud|**Standaard**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Tabel 101 zijn de kenmerken van de [groep met keuzerondjes](#RadioGroup) element en biedt een beschrijving van elke.  

### <a name="table-101-attributes-and-corresponding-values-for-the-radiogroup-element"></a>Tabel 101. Kenmerken en bijbehorende waarden voor de groep met keuzerondjes-Element  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Vergrendeld**|Hiermee geeft u op of de groep keuzerondjes voor invoer van de gebruiker is ingeschakeld. Het kenmerk kan worden ingesteld op:<br /><br /> -   **True**. Specificeert dat de keuzerondjes zijn uitgeschakeld en dat gebruikers een keuzerondje in de groep niet selecteren.<br />-   **False**. Specificeert dat de keuzerondjes zijn ingeschakeld en gebruikers een keuzerondje in de groep selecteren kunnen.|  
|**Naam**|Hiermee geeft u de naam van de groep keuzerondjes optie.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="StageGroup"></a> StageGroup  
 Dit element bevat een implementatiegroep fase.  

##### <a name="element-information"></a>Elementgegevens  
102 tabel bevat informatie over de [StageGroup](#StageGroup) element.  

### <a name="table-102-stagegroup-element-information"></a>102 van de tabel. StageGroup elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer binnen een [StageGroups](#StageGroups) element|  
|Bovenliggende elementen|**StageGroups**|  
|Inhoud|**Fase**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 103 tabel zijn de kenmerken van de [StageGroup](#StageGroup) -element en een beschrijving van het kenmerk.  

### <a name="table-103-attributes-and-corresponding-values-for-the-stagegroup-element"></a>Tabel 103. Kenmerken en bijbehorende waarden voor het Element StageGroup  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**DisplayName**|Hiermee geeft u de beschrijvende naam van de fase groep weergegeven in de waarde van de Wizard UDI. Deze naam is meestal de meer beschrijvende dan de **naam** kenmerk.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="StageGroups"></a> StageGroups  
 Dit element gegroepeerd op een reeks fase groepen binnen een configuratiebestand van de Wizard UDI.  

##### <a name="element-information"></a>Elementgegevens  
104 tabel bevat informatie over de [StageGroups](#StageGroups) element.  

### <a name="table-104-stagegroups-element-information"></a>Tabel 104. StageGroups elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of één binnen een [Wizard](#Wizard) element|  
|Bovenliggende elementen|**Wizard**|  
|Inhoud|**StageGroup**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Setter"></a> Setter  
 Dit element bevat een instelling voor de waarde voor een eigenschap met de naam in de **eigenschap** eigenschap.  

##### <a name="element-information"></a>Elementgegevens  
 105 tabel bevat informatie over de [Setter]() element.  

### <a name="table-105-setter-element-information"></a>105 van de tabel. Setter elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of meer binnen elke bovenliggende element (dit element is optioneel.)|  
|Bovenliggende elementen|**Data**, **DataItem**, **Page**, **Style**, **Task**, **Validator**|  
|Inhoud|Bevat een string-waarde in de **eigenschap** kenmerk|  

##### <a name="element-attributes"></a>Elementkenmerken  
106 tabel geeft een lijst van het kenmerk van de [Setter]() element en bevat een beschrijving van deze.  

### <a name="table-106-attributes-and-corresponding-values-for-the-setter-element"></a>106 tabel. Kenmerken en bijbehorende waarden voor de Setter-Element  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**Eigenschap**|Hiermee geeft u de naam van de eigenschap wordt ingesteld. Naam van de eigenschap is ingesteld op de waarde die dit kenmerk vierkante haken.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

#### <a name="stage"></a>Fase  
 Dit element bevat een [fase](#Stage) binnen een [StageGroup](#StageGroup) en bevat een of meer [PageRef](#PageRef) elementen.  

##### <a name="element-information"></a>Elementgegevens  
107 tabel bevat informatie over de [fase](#Stage) element.  

### <a name="table-107-stage-element-information"></a>107 van de tabel. Fase elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer binnen een [StageGroup](#StageGroup) element|  
|Bovenliggende elementen|**StageGroup**|  
|Inhoud|**PageRef**|  

##### <a name="element-attributes"></a>Elementkenmerken  
108 tabel zijn de kenmerken van de [fase](#Stage) element en biedt een beschrijving van elke.  

### <a name="table-108-attributes-and-corresponding-values-for-the-stage-element"></a>108 van de tabel. Kenmerken en bijbehorende waarden voor het Element fase  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**DisplayName**|Hiermee geeft u de beschrijvende naam van de wizardpagina weergegeven in de waarde van de Wizard UDI. Deze naam is meestal de meer beschrijvende dan de **naam** kenmerk.|  
|**Naam**|Hiermee geeft u de naam van de fase. De waarde van dit element wordt gebruikt bij het starten van de Wizard UDI met de **/fase: naam** opdrachtregelparameter.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Style"></a> stijl  
 Dit element de afzonderlijke groepen [Setter]() elementen die de Wizard UDI uiterlijk, waaronder de titel wordt weergegeven aan de bovenkant van de wizard en de installatiekopie van het banner wordt weergegeven in de Wizard UDI configureren.  

##### <a name="element-information"></a>Elementgegevens  
109 tabel bevat informatie over het Style-element.  

### <a name="table-109-style-element-information"></a>109 van de tabel. Stijl elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|een|  
|Bovenliggende elementen|**Wizard**|  
|Inhoud|**Setter**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<Style>  
  <Setter Property="bannerFilename">UDI_Wizard_Banner.bmp</Setter>   
  <Setter Property="title">Operating System Deployment (OSD) Refresh Wizard</Setter>   
</Style>  
```  

####  <a name="TaskElement"></a> Taak  
 Dit element bevat een taak die moet worden uitgevoerd op de pagina die is opgegeven in de bovenliggende [pagina](#Page) element.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 110 bevat informatie over de [taak](#Task) element.  

### <a name="table-110-task-element-information"></a>Tabel 110. Element taakgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Een of meer binnen een [taken](#Tasks) element|  
|Bovenliggende elementen|**Taken**|  
|Inhoud|**ExitCodes**, **File**, **Setter**|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 111 hier worden de kenmerken van de [taak](#Task) element en biedt een beschrijving van elke.  

### <a name="table-111-attributes-and-corresponding-values-for-the-task-element"></a>Tabel 111. Kenmerken en bijbehorende waarden voor het taakelement  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**DependsOn**|Hiermee geeft u op of de taak afhankelijk is van een andere taak. De waarde van dit kenmerk is ingesteld op de **naam** kenmerk van een andere [taak](#Task) element. **Opmerking:**  Dit kenmerk kan niet worden geconfigureerd met behulp van de waarde van de Wizard UDI. U kunt echter handmatig toevoegen dit kenmerk een [taak](#Task) element het .xml-bestand rechtstreeks wijzigen.|  
|**DisplayName**|Hiermee geeft u de beschrijvende naam van de taak die wordt weergegeven in de ontwerpfunctie van de Wizard UDI. Deze naam is meestal de meer beschrijvende dan de **naam** kenmerk.|  
|**Naam**|Hiermee geeft u de naam van de taak. Deze naam moet uniek zijn.|  
|Type|Geeft het taaktype voor de taak moet worden uitgevoerd die is gedefinieerd in het DLL-bestand met de taak.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Tasks"></a> Taken  
 Dit element groepen een aantal taken voor een [pagina](#Page) element.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 112 bevat informatie over de [taken](#Tasks) element.  

### <a name="table-112-tasks-element-information"></a>Tabel 112. Informatie over de elementen van taken  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of één in elk [pagina](#Page) element (dit element is optioneel.)|  
|Bovenliggende elementen|**Pagina**|  
|Inhoud|**Task**|  

##### <a name="element-attributes"></a>Elementkenmerken  
Tabel 113 hier worden de kenmerken van de [taken](#Tasks) element en biedt een beschrijving van elke.  

### <a name="table-113-attributes-and-corresponding-values-for-the-tasks-element"></a>Tabel 113. Kenmerken en bijbehorende waarden voor het Element taken  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|**NameTitle**|Hiermee geeft u het bijschrift dat wordt weergegeven boven aan de kolom met de naam van de taken in de juiste wizardpagina.|  
|**StatusTitle**|Hiermee geeft u het bijschrift dat wordt weergegeven boven aan de kolom waarin de status van de taken in de juiste wizardpagina.|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="ValidatorElement"></a> Validator  
 Dit element bevat een validatiefunctie voor het veldbesturingselement dat is opgegeven in de bovenliggende [veld](#Field) element.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 114 bevat informatie over de [Validator](#Validator) element.  

### <a name="table-114-validator-element-information"></a>Tabel 114. Validator elementgegevens  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|Nul of één binnen een [veld](#Field) element|  
|Bovenliggende elementen|**Field**|  
|Inhoud|**Setter**|  

##### <a name="element-attributes"></a>Elementkenmerken  
115 tabel geeft een lijst van het kenmerk van de [Validator](#Validator) element en bevat een beschrijving van deze.  

### <a name="table-115-attributes-and-corresponding-values-for-the-validator-element"></a>Tabel 115. Kenmerken en bijbehorende waarden voor het Element Validator  

|**Kenmerk**|**Beschrijving**|  
|-|-|  
|Type|Hiermee geeft u het type voor de validatiefunctie, die is gedefinieerd in het DLL-bestand met de validatiefunctie|  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  
 Geen.  

####  <a name="Wizard"></a> Wizard  
 Dit element bevat de hoofdmap voor alle andere elementen.  

##### <a name="element-information"></a>Elementgegevens  
Tabel 116 bevat informatie over de [Wizard](#Wizard) element.  

### <a name="table-116-wizard-element-information"></a>Tabel 116. Informatie over het Element van de wizard  

|**Kenmerk**|**Waarde**|  
|-|-|  
|Aantal exemplaren|een|  
|Bovenliggende elementen|Geen|  
|Inhoud|**DLLs**, **Pages**, **StageGroups**, **Style**|  

##### <a name="element-attributes"></a>Elementkenmerken  
 Dit element heeft geen kenmerken.  

##### <a name="remarks"></a>Opmerkingen  
 Geen.  

##### <a name="example"></a>Voorbeeld  

```  
<Wizard>  
   + <DLLs>  
   + <Style>  
   + <Pages>  
   + <StageGroups>  
</Wizard>  
```
