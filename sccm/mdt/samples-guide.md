---
title: MDT-voorbeelden
titleSuffix: Microsoft Deployment Toolkit
description: 'Voorbeelden van de Microsoft Deployment Toolkit. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 2ff0100c-b7ef-4e09-8c96-fc1898390b6d
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fe61cecea2b2a4f4083933b937af90dfb61ea5bf
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/27/2018
---
# <a name="microsoft-deployment-toolkit-samples-guide"></a>Handleiding voor Microsoft Deployment Toolkit-voorbeelden  
 Deze handleiding is onderdeel van Microsoft® Deployment Toolkit (MDT) 2013 en leidt een team speciale instructies voor het implementeren van Windows-besturingssystemen en Microsoft Office. Deze handleiding is met name zodanig ontworpen dat voorbeeld configuratie-instellingen voor specifieke implementatiescenario's.  

> [!NOTE]
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

 **Deze handleiding gebruiken**  

 Bekijk de lijst met onderwerpen in de inhoudsopgave.  

1.  Selecteer het scenario dat wordt aangeduid implementatiedoelstellingen voor uw organisatie.  

2.  Bekijk het voorbeeld configuratie-instellingen voor het geselecteerde scenario.  

3.  De voorbeeld-configuratie-instellingen gebruikt als basis voor de configuratie-instellingen in uw omgeving.  

4.  De voorbeeld-configuratie-instellingen voor uw omgeving aanpassen.  

 In veel gevallen mogelijk meer dan één scenario nodig zijn voor de configuratie-instellingen voor de omgeving.  

 Omdat deze handleiding alleen voorbeeld configuratie-instellingen bevat, kan de handleidingen bij die worden vermeld in de volgende tabel bekijken verdere assistentie bij het aanpassen van de configuratie-instellingen voor de omgeving.  

 |Handleiding|Deze handleiding biedt hulp bij het|  
 |-|-|  
 |*Quick Start Guide voor Microsoft System Center 2012 R2 Configuration Manager* |Gebruik System Center 2012 R2 Configuration Manager voor het installeren van het besturingssysteem Windows 8.1 in een nieuwe Computer implementatiescenario.|  
 |*Quick Start Guide voor de installatie van Lite Touch* |Het besturingssysteem Windows 8.1 via Lite Touch Installation (LTI) met opstartbare media in het implementatiescenario van een nieuwe Computer installeren.|  
 |*Snelstartgids voor de installatie door gebruikers geïnitieerde* |Installeer het besturingssysteem Windows 8.1 met Driven installatie en System Center 2012 R2 Configuration Manager in een nieuwe Computer implementatiescenario.|  
 |*Microsoft Deployment Toolkit gebruiken* |Verder aanpassen van de configuratiebestanden in implementaties van Zero Touch installatie (ZTI) en LTI gebruikt. Deze handleiding bevat ook algemene richtlijnen en technische naslaginformatie voor configuratie-instellingen.|


## <a name="deploying-windows-8-applications-using-mdt"></a>Implementatie van Windows 8-toepassingen met MDT  
 MDT kunt Windows 8-toepassingspakketten, waarvoor een extensie .appx-bestand implementeren. Deze toepassingspakketten zijn nieuw in Windows 8. Zie voor meer informatie over deze toepassingen [Windows Store-App-ontwikkeling.](http://msdn.microsoft.com/windows/apps)  

 Implementeer Windows 8-toepassingen met MDT door de volgende stappen uit te voeren:  

-   Met behulp van LTI, zoals beschreven in Windows 8-toepassingen implementeren [implementeren van Windows 8-toepassingen met behulp van LTI](#DeployWin8LTI).  

-   Met behulp van UDI (User Driven installatie), zoals beschreven in Windows 8-toepassingen implementeren [implementeren van Windows 8-toepassingen met behulp van UDI](#DeployWin8UDI).  

###  <a name="DeployWin8LTI"></a> Implementatie van Windows 8-toepassingen met behulp van LTI  
 U kunt Windows 8-toepassingen met behulp van LTI zoals een andere toepassing die het installatieproces vanaf een opdrachtregel initieert implementeren. U kunt Windows 8-toepassingen voor implementaties van LTI toevoegen in het knooppunt toepassingen in de implementatie-Workbench.  

 **Voor het implementeren van een Windows 8-toepassing met behulp van LTI**  

1.  Maak een gedeelde netwerkmap waarin de toepassing opgeslagen.  

2.  Kopieer de Windows 8-toepassing naar de gedeelde netwerkmap die u in de vorige stap hebt gemaakt.  

     Zorg ervoor dat u kopieert het appx-bestand van de Windows 8-toepassing en eventuele andere vereiste bestanden, zoals een cer-bestand met het toepassingscertificaat.  

3.  Een item van de toepassing LTI voor de Windows 8-toepassing in het knooppunt toepassingen in de Workbench-implementatie met de Wizard Nieuwe toepassing maken.  

     Tijdens het uitvoeren van de Wizard Nieuwe toepassing op de **Opdrachtdetails** pagina wizard **opdrachtregel**, type **app_file_name** (waarbij *app_file_name*  is de naam van de Windows 8-toepassing).  

     Zie voor meer informatie over het voltooien van de Wizard Nieuwe toepassing in de Workbench-implementatie in de volgende secties in het document MDT *met behulp van de Microsoft Deployment Toolkit*:  

    -   'Een nieuwe toepassing die Is geïmplementeerd maken van de Implementatieshare'  

    -   'Een nieuwe toepassing die wordt geïmplementeerd vanaf een andere gedeelde netwerkmap maken'  

4.  Selecteer de LTI-item toepassing gemaakt in de vorige stap in een takenreeks LTI.  

###  <a name="DeployWin8UDI"></a> Implementatie van Windows 8-toepassingen met behulp van UDI  
 U kunt Windows 8-toepassingen met behulp van UDI zoals een andere toepassing die het installatieproces vanaf een opdrachtregel initieert implementeren. U kunt Windows 8-toepassingen voor UDI implementaties toevoegen op de **ApplicationPage** wizardpagina in de ontwerpfunctie van de Wizard UDI.  

> [!NOTE]
>  Implementatie van Windows 8 en Windows 8-toepassingen met behulp van UDI is vereist voor System Center 2012 R2 Configuration Manager.  

 **Voor het implementeren van een Windows 8-toepassing met behulp van UDI**  

1.  Maak een gedeelde netwerkmap waarin de toepassing opgeslagen.  

     Deze map worden de bronmap voor de Configuration Manager-toepassing die u later in het proces wilt maken.  

2.  Kopieer de Windows 8-toepassing naar de gedeelde netwerkmap die u in de vorige stap hebt gemaakt.  

     Zorg ervoor dat u kopieert het appx-bestand van de Windows 8-toepassing en eventuele andere vereiste bestanden, zoals een cer-bestand met het toepassingscertificaat.  

3.  De Windows 8-toepassing toevoegen als een Configuration Manager-toepassing  

4.  Maak een item van de toepassing Configuration Manager voor de Windows 8-toepassing met de Wizard toepassing maken in de Configuration Manager-console.  

     Maak een implementatietype voor het implementeren van de Windows 8-toepassing met behulp van de Wizard implementatietype maken tijdens het uitvoeren van de Wizard toepassing maken. In de Wizard implementatietype maken op de **inhoud** pagina **installatieprogramma**, type **app_file_name** (waarbij *app_file_name*is de naam van de Windows 8-toepassing).  

     Zie voor meer informatie over het voltooien van de Wizard toepassing maken in de Configuration Manager-console de volgende secties in de Documentatiebibliotheek voor System Center 2012 Configuration Manager die wordt geleverd met Configuration Manager:  

    -   [Toepassingen maken in Configuration Manager](http://technet.microsoft.com/library/gg682159.aspx)  

    -   [Het maken van implementatietypen in Configuration Manager](http://technet.microsoft.com/library/gg682174.aspx#BKMK_Step3)  

    -   [Het beheren van toepassingen en implementatietypen in Configuration Manager](http://technet.microsoft.com/library/gg682031)  

5.  Zorg ervoor dat de functie gebruikersaffiniteit apparaat (UDA) in Configuration Manager juist is geconfigureerd voor ondersteuning van affiniteit tussen gebruikers en apparaten voor Configuration Manager-toepassingsimplementatie.  

     Zie voor meer informatie over het configureren van UDA ter ondersteuning van Configuration Manager-toepassingsimplementatie [het beheren van affiniteit van gebruikersapparaat in Configuration Manager](http://technet.microsoft.com/library/gg699365).  

6.  Implementeer de toepassing gemaakt in stap 4 aan de beoogde gebruikers.  

     Zie voor meer informatie over het implementeren van een toepassing aan gebruiker [toepassingen implementeren in Configuration Manager](http://technet.microsoft.com/library/gg682082).  

7.  Configureer de **ApplicationPage** wizardpagina om op te nemen van de Configuration Manager-toepassing die is gemaakt in stap 4 met behulp van de waarde van de Wizard UDI.  

     Voor meer informatie over het configureren van de **ApplicationPage** pagina van de wizard met behulp van de ontwerpfunctie van de Wizard UDI Zie de sectie ' stap 5-11: Het configuratiebestand van de UDI Wizard aanpassen voor de doelcomputer', in het document MDT *Snelstartgids voor Driven installatie*.  

8.  Selecteer het UDI toepassing item in de vorige stap in een takenreeks UDI gemaakt.  

    > [!NOTE]
    >  De Windows 8-toepassing niet is geïnstalleerd door de takenreeks wordt uitgevoerd, maar in plaats van te zijn geïnstalleerd de eerste keer dat de gebruiker zich aanmeldt bij de doelcomputer (zoals gedefinieerd door de UDA-instelling in stap 5 hebt geconfigureerd) met de functie gebruikersgerichte App-installatieprogramma (AppInstall.exe) in UDI.  

     Zie de sectie 'Gebruikersgerichte App installatieprogramma Reference', in de MDT-document voor meer informatie over de functie App-installatieprogramma gebruikersgerichte in UDI *Toolkit verwijzing*.  

## <a name="managing-mdt-using-windows-powershell"></a>Het beheren van MDT met Windows PowerShell  
 U kunt met behulp van de Windows PowerShell en implementatie-Workbench MDT-implementatieshares beheren. MDT bevat een Windows PowerShell™ module in—Microsoft.BDD.SnapIn—that moet worden geladen voordat de MDT-specifieke functies in Windows PowerShell. De MDT Windows PowerShell-module bevat:  

-   Een Windows PowerShell-provider: MDTProvider, die toegang biedt tot de inhoud van een implementatieshare  

-   -Cmdlets die de mogelijkheid bieden voor het beheren van de MDT-implementatieshares  

 Beheren van MDT implementatieshares met Windows PowerShell met de volgende stappen uit te voeren:  

-   Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

-   Maak een implementatieshare met Windows PowerShell, zoals beschreven in [maken van een implementatie delen met Windows PowerShell](#CreateDeployShare).  

-   Weergeven met Windows PowerShell, zoals beschreven in eigenschappen van implementatieshare [weergeven implementatie delen eigenschappen met Windows PowerShell](#ViewDeployShareProp).  

-   De lijst weergeven met implementatieshares met Windows PowerShell, zoals beschreven in [weergeven van de lijst van implementatie-Shares met behulp van Windows PowerShell](#ViewListDeployShare).  

-   Bijwerken van een implementatieshare, die wordt gegenereerd installatiekopieën voor de nieuwe Windows Preinstallation Environment (Windows PE), zoals beschreven in [bijwerken van een implementatie delen met Windows PowerShell](#UpdateDeployShare).  

-   Bijwerken van een implementatieshare gekoppelde, die wordt gerepliceerd inhoud van een implementatieshare naar de share van de gekoppelde implementatie, zoals beschreven in [bijwerken van een gekoppelde implementatie delen met Windows PowerShell](#UpdateLinkedDeployShare).  

-   Bijwerken van media voor implementatie, die de inhoud van een implementatieshare gerepliceerd naar de media voor implementatie en genereert vervolgens nieuwe opstartbare installatiekopieën, zoals beschreven in [bijwerken implementatie Media Windows PowerShell gebruiken](#UpdateDeployMedia).  

-   Items in een implementatieshare (zoals besturingssystemen, stuurprogrammapakketten besturingssysteem, toepassingen en stuurprogramma's) te beheren, zoals beschreven in [Items beheren in een implementatie delen met Windows PowerShell](#ManageItemDeployShare).  

-   De populatie van items in een implementatieshare (zoals besturingssystemen, stuurprogrammapakketten besturingssysteem, toepassingen en stuurprogramma's) automatiseren zoals beschreven in [automatiseren populatie van een Deployment Share](#AutomatePopulateDeployShare).  

-   Beheren van de mappen in een implementatie met Windows PowerShell, zoals beschreven in [beheren implementatie delen mappen met Windows PowerShell](#ManageDeployShareFolder).  

###  <a name="LoadMDTSnapIn"></a> Bij het laden van de MDT Windows PowerShell-module  
 De MDT-cmdlets beschikbaar zijn in een Windows PowerShell-module **Microsoft.BDD.SnapIn** die moeten worden geladen voordat de MDT-cmdlets gebruiken. U kunt laden de MDT Windows PowerShell-module die met een van de volgende methoden:  

-   Laad de MDT Windows PowerShell-module die met behulp van de console venster PowerShell-Modules, zoals beschreven in [laden van de MDT Windows PowerShell-module met behulp van de importtaak System Modules](#LoadMDTSnapInImport).  

-   Load de MDT Windows PowerShell-module met behulp van de **toevoegen-PSSnapIn** cmdlet zoals beschreven in [laden van de MDT Windows PowerShell-module met behulp van de Cmdlet Add-PSSnapIn](#LoadMDTSnapInCmdlet).  

####  <a name="LoadMDTSnapInImport"></a> Laden van de MDT Windows PowerShell-module met behulp van de importtaak voor systeem-Modules  
 De taak voor Import System Modules omvat automatisch de Windows PowerShell-modules en -modules die zich in de modules in de map %Windir%\System32\WindowsPowerShell\1.0\Modules. MDT installeert automatisch de MDT Windows PowerShell-module **Microsoft.BDD.SnapIn** in die map tijdens de MDT-installatie.  

> [!NOTE]
>  De taak voor Import System Modules is alleen beschikbaar in Windows 7 en Windows Server 2008 R2 wanneer Windows PowerShell 3.0 niet is geïnstalleerd op de computer. Vanaf Windows PowerShell 3.0 worden modules automatisch geïmporteerd de eerste keer dat u een cmdlet in de module.  

 U kunt een Windows PowerShell-console met de taak voor Import System Modules starten door het uitvoeren van een van de volgende procedures:  

-   In de taakbalk met de rechtermuisknop op de **Windows PowerShell** pictogram en klik vervolgens op **importeren System Modules**.  

-   Klik op **Start**, wijs **Systeembeheer** en klik vervolgens op **Windows PowerShell-Modules**.  

 Zie voor meer informatie over het Start een Windows PowerShell-console met systeem-Modules importeren [Windows PowerShell starten met systeem-Modules importeren](http://msdn.microsoft.com/library/windows/desktop/hh847866.aspx).  

####  <a name="LoadMDTSnapInCmdlet"></a> Laad de MDT Windows PowerShell-module met de Cmdlet-PSSnapIn  
 Kunt u de MDT Windows PowerShell-module laden **Microsoft.BDD.PSSnapIn** vanuit een Windows PowerShell-omgeving met de [toevoegen-PSSnapIn](http://technet.microsoft.com/library/hh849705.aspx) als weergeven in het volgende voorbeeld-cmdlet:  

```  
Add-PSSnapin -Name Microsoft.BDD.PSSnapIn  
```  

###  <a name="CreateDeployShare"></a> Maken van de Share van een implementatie met Windows PowerShell  
 U kunt implementatieshares MDT Windows PowerShell-cmdlets gebruiken. De hoofdmap voor de implementatieshare wordt gemaakt en gedeeld met behulp van standaard Windows PowerShell-cmdlets en aanroepen naar Windows Management Instrumentation (WMI) klasse opdrachten. De implementatieshare is gevuld met de MDTProvider Windows PowerShell-provider en de [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet. De MDTProvider Windows PowerShell-station is persistent met behulp van de **toevoegen MDTPersistentDrive** cmdlet.  

 **Voorbereiden van de share van een implementatie met MDT Windows PowerShell-cmdlets**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Maak de map die de hoofdmap van de nieuwe implementatie share via de **New Item** cmdlet als in het volgende voorbeeld wordt weergegeven en beschreven in [met de Cmdlet New-Item](http://technet.microsoft.com/library/ee176914.aspx):  

    ```  
    New-Item "C:\MDTDeploymentShare$" -Type directory  
    ```  

     De cmdlet geeft de geslaagde maken van de map.  

3.  Deel de map die is gemaakt in de vorige stap met behulp van de **WMI win32_share** klasse zoals ingezaaide in het volgende voorbeeld:  

    ```  
    ([wmiclass]"win32_share").Create("C:\MDTDeploymentShare$", "MDTDeploymentShare$",0)  
    ```  

     De aanroep van de **win32_share** klasse retourneert de resultaten van de aanroep. Als de waarde van **ReturnValue** is nul (0), wordt de aanroep is geslaagd.  

4.  Geef op de nieuwe gedeelde map als een deployment share met de [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "C:\MDTDeploymentShare$" -Description "MDT Deployment Share Created with Cmdlets" -NetworkPath "\\WDG-MDT-01\MDTDeploymentShare$" -Verbose  
    ```  

     De cmdlet start automatisch maken van de implementatieshare en de sjabloongegevens kopiëren naar de nieuwe implementatieshare. Na voltooiing van het kopieerproces toont de cmdlet de informatie voor de nieuwe implementatieshare.  

    > [!NOTE]
    >  De waarde die is opgegeven de *naam* parameter (DS002) moeten uniek zijn en mag niet overeenkomen met een bestaande Windows PowerShell-station van de implementatieshare.  

5.  Controleer of de juiste share implementatiemappen zijn gemaakt met behulp van de **dir** opdracht als weergeven in het volgende voorbeeld:  

    ```  
    dir ds002:  
    ```  

     De lijst met standaardmappen in de hoofdmap van de implementatieshare wordt weergegeven.  

6.  De nieuwe implementatieshare toevoegen aan de lijst met persistente MDT-implementatieshares met de **toevoegen MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    $NewDS=Get-PSDrive "DS002"  
    Add-MDTPersistentDrive  -Name "DS002" -InputObject $NewDS Verbose  
    ```  

     In dit voorbeeld wordt de *$NewDS* variabele wordt gebruikt om aan te geven van het Windows PowerShell-station-object voor de share van de nieuwe implementatie aan de cmdlet.  

     U kunt ook u kan gecombineerde de [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) en **toevoegen MDTPersistentDrive** cmdlets, zoals weergegeven in het volgende voorbeeld:  

    ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "C:\MDTDeploymentShare$" -Description "MDT Deployment Share Created with Cmdlets" -NetworkPath "\\WDG-MDT-01\MDTDeploymentShare$" -Verbose | Add-MDTPersistentDrive -Verbose  
    ```  

     In het vorige voorbeeld bevat de Windows PowerShell-pijplijn de *naam* en *InputObject* parameters.  

###  <a name="ViewDeployShareProp"></a> Eigenschappen van Implementatieshare met Windows PowerShell weergeven  
 Vindt u de eigenschappen van de MDT-implementatieshares met de [Get ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet en de MDTProvider Windows PowerShell-provider. Deze eigenschappen kunnen bekijken in de implementatie-Workbench.  

 **Om weer te geven van eigenschappen van implementatieshare MDT Windows PowerShell-cmdlets gebruiken**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties delen Windows PowerShell stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  Controleer of de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows PowerShell-stations die worden geleverd met behulp van de MDTProvider worden weergegeven.  

4.  Bekijk de eigenschappen van de implementatie share via de [Get ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-ItemProperty "DS002:"  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3. De cmdlet retourneert de eigenschappen voor de implementatieshare.  

###  <a name="ViewListDeployShare"></a> De lijst weergeven met behulp van Windows PowerShell-Implementatieshares  
 U kunt de lijst weergeven met shares MDT-implementatie met de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet en de MDTProvider Windows PowerShell-provider. Dezelfde lijst met implementatieshares kan ook worden weergegeven in de implementatie-Workbench.  

 **Een lijst weergeven van implementatieshares MDT Windows PowerShell-cmdlets gebruiken**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties deelt met Windows PowerShell stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  De lijst met MDT-implementaties die delen van Windows PowerShell-stations, één voor elke implementatieshare weergeven met behulp van de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows-PowerShell stations die zijn opgegeven met behulp van de MDTProvider worden vermeld, één voor elke implementatieshare.  

###  <a name="UpdateDeployShare"></a> Bijwerken van de Share van een implementatie met Windows PowerShell  
 U kunt bijwerken met implementatieshares de **Update MDTDeploymentShare** cmdlet en de MDTProvider Windows PowerShell-provider. Bijwerken van een implementatieshare maakt de Windows PE-opstartinstallatiekopieën (WIM en International Organization for Standardization [ISO]-bestanden) om te kunnen starten van de implementatie van de LTI. U kunt hetzelfde proces met behulp van de implementatie-Workbench kunt uitvoeren, zoals beschreven in "Update een Share in de Implementatieworkbench-implementatie".  

 **Bijwerken van de share van een implementatie met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  Controleer of de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows PowerShell-stations die zijn opgegeven met behulp van de MDTProvider worden weergegeven.  

4.  Bijwerken deployment share met de **Update MDTDeploymentShare** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Update-MDTDeploymentShare -Path "DS002:" -Force  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

    > [!NOTE]
    >  Bijwerken van de implementatieshare kan lang duren. De voortgang van de cmdlet wordt weergegeven boven aan de Windows PowerShell-console.  

     De cmdlet retourneert geen uitvoer als de update geslaagd is.  

###  <a name="UpdateLinkedDeployShare"></a> Bijwerken van een gekoppelde Deployment Share met Windows PowerShell  
 U kunt bijwerken (repliceren) gekoppelde implementatieshares met de **Update MDTLinkedDS** cmdlet en de MDTProvider Windows PowerShell-provider. De inhoud van de oorspronkelijke implementatieshare bijwerken van een gekoppelde implementatieshare worden gerepliceerd naar de share van de gekoppelde implementatie. U kunt hetzelfde proces met behulp van de implementatie-Workbench kunt uitvoeren, zoals beschreven in "Repliceren gekoppelde Shares in de Implementatieworkbench-implementatie".  

 **Bijwerken van een gekoppelde implementatieshare met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  Controleer of de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows PowerShell-stations die zijn opgegeven met behulp van de MDTProvider worden weergegeven.  

4.  Bijwerken deployment share met de **Update MDTDeploymentShare** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Update-MDTLinkedDS -Path "DS002:\Linked Deployment Shares\LINKED002"  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

    > [!NOTE]
    >  De gekoppelde implementatieshare bijwerken kan lang duren. De voortgang van de cmdlet wordt weergegeven boven aan de Windows PowerShell-console.  

     De cmdlet retourneert geen uitvoer als de update geslaagd is.  

###  <a name="UpdateDeployMedia"></a> Bijwerken van Media voor implementatie met Windows PowerShell  
 U kunt bijwerken (genereren) implementatie media met de **Update MDTMedia** cmdlet en de MDTProvider Windows PowerShell-provider. Bijwerken van implementatiemedia repliceert de inhoud van de share van de oorspronkelijke implementatie naar de gekoppelde implementatieshare en genereert vervolgens ISO en WIM-bestanden. U kunt hetzelfde proces met behulp van de implementatie-Workbench kunt uitvoeren, zoals beschreven in 'Genereren Media afbeeldingen in de implementatie-Workbench'.  

 Wanneer de **Update MDTMedia** cmdlet is voltooid, worden de volgende bestanden gemaakt:  

-   Een ISO-bestand in de *media_folder* map (waarbij *media_folder* is de naam van de map die u hebt opgegeven voor de media)  

     Het ISO-bestand genereren is een optie die u configureert:  

    -   Selecteren van de **een Lite-Touch opstartbare ISO-installatiekopie gegenereerd** selectievakje op de **algemene** tabblad van de **media eigenschappen** dialoogvenster (Schakel dit selectievakje in zodat u minder tijd nodig voor het genereren van de media tenzij u hoeft te maken van opstartbare dvd's of virtuele machines [VM's] starten via het ISO-bestand.)  

    -   Instellen dezelfde eigenschap met de [Set-ItemProperty](http://technet.microsoft.com/library/hh849844) cmdlet  

-   WIM-bestanden in de *media_folder*\Content\Deploy\Boot map (waarbij *media_folder* is de naam van de map die u hebt opgegeven voor de media)  

 **Bijwerken van een gekoppelde implementatieshare met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties deelt met Windows PowerShell stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  Controleer of de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows PowerShell-stations die zijn opgegeven met behulp van de MDTProvider worden weergegeven.  

4.  Bijwerken deployment share met de **Update MDTDeploymentShare** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Update-MDTLinkedDS -Path "DS002:\Linked Deployment Shares\LINKED002"  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

    > [!NOTE]
    >  De gekoppelde implementatieshare bijwerken kan lang duren. De voortgang van de cmdlet wordt weergegeven boven aan de Windows PowerShell-console.  

     De cmdlet retourneert geen uitvoer als de update geslaagd is.  

###  <a name="ManageItemDeployShare"></a> Het beheren van Items in een implementatie met Windows PowerShell  
 Een implementatieshare bevat items die worden gebruikt voor het uitvoeren van implementaties, zoals besturingssystemen, toepassingen, stuurprogramma's, besturingssysteempakketten en takenreeksen. Deze items kunnen worden beheerd met behulp van Windows PowerShell en die worden verstrekt met MDT-cmdlets.  

 Zie voor meer informatie over het bewerken van items die rechtstreeks met Windows PowerShell-cmdlets, [Items rechtstreeks bewerken van](http://technet.microsoft.com/library/dd315266.aspx). De mapstructuur voor een implementatieshare kan ook worden beheerd met behulp van Windows PowerShell. Zie voor meer informatie [beheren implementatie Share mappen met Windows PowerShell](#ManageDeployShareFolder).  

####  <a name="ImportItemDeployShare"></a> Importeren van een Item in een Implementatieshare  
 U kunt elk type item, zoals besturingssystemen, toepassingen of apparaatstuurprogramma's importeren met behulp van de MDT-cmdlets. Er is een specifieke MDT-cmdlet voor elk type van item. Als u wilt importeren van meerdere item in de share van een implementatie met Windows PowerShell, Zie [automatiseren populatie van een Deployment Share](#AutomatePopulateDeployShare).  

 De volgende tabel bevat de MDT Windows PowerShell-cmdlets gebruikt om items te importeren in een implementatieshare en bevat een korte beschrijving van elke cmdlet. Voorbeelden van het gebruik van elke cmdlet vindt u in de sectie die overeenkomt met elke cmdlet.  

 |**Cmdlet** | **Beschrijving** |  
 |-|-|  
 |**Importeren MDTApplication** |Kunt u een toepassing importeren in een implementatieshare|  
 |**Import-MDTDriver** |Een of meer apparaatstuurprogramma's importeert in een implementatieshare|  
 |**Import-MDTOperatingSystem** |Een of meer besturingssystemen importeert in een implementatieshare|  
 |**Importeren MDTPackage** |Een of meer pakketten van het besturingssysteem in een implementatieshare geïmporteerd|  
 |**Import-MDTTaskSequence** |Een takenreeks importeert in een implementatieshare|  

####  <a name="ViewPropertyDeployShare"></a> De eigenschappen van een Item in een Implementatieshare weergeven  
 Elk item in een implementatieshare heeft een andere set eigenschappen. U kunt de eigenschappen van een item weergeven in een implementatie share met de [Get ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet. De [Get ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet gebruikt om de eigenschappen voor een specifiek item weer te geven van de MDTProvider net zoals u de eigenschappen in de implementatie-Workbench ziet.  

 Als u wilt de eigenschappen van meerdere items weergeven in een implementatie wilt delen met Windows PowerShell, raadpleegt u [automatiseren populatie van een Deployment Share](#AutomatePopulateDeployShare).  

 **De eigenschappen van een item weergeven in een implementatie met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  Controleer of de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows PowerShell-stations die zijn opgegeven met behulp van de MDTProvider worden weergegeven.  

4.  Een lijst van de items voor het type item waarvoor u de eigenschappen met weergeven zijn productiviteitsniveau retourneren de [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-Item "DS001:\Operating Systems\*" | Format-List  
    ```  

     In het vorige voorbeeld wordt wordt een lijst van de besturingssystemen in de implementatieshare weergegeven. De uitvoer wordt doorgegeven naar de **lijst indelen** cmdlet zodat de lange namen van de besturingssystemen kunnen worden weergegeven. Voor meer informatie over het gebruik van de **lijst indelen** cmdlet, Zie [met de Cmdlet lijst indelen](http://technet.microsoft.com/library/ee176830.aspx). Hetzelfde proces kan worden gebruikt voor het retourneren van de lijst met andere soorten items, zoals de apparaatstuurprogramma's of toepassingen.  

    > [!TIP]
    >  U kunt ook hebt gebruikt de **dir** opdracht voor het weergeven van de lijst met besturingssystemen in plaats van de [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet.  

5.  Bekijk de eigenschappen van een van de items die worden vermeld in de vorige stap met behulp van de [Get ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-ItemProperty -Path "DS002:\Operating Systems\Windows 8 in Windows 8 x64 install.wim"  
    ```  

     In dit voorbeeld wordt de waarde van de *pad* parameter is het volledig gekwalificeerde Windows PowerShell-pad naar het item, inclusief de bestandsnaam die is geretourneerd in de vorige stap. U kunt hetzelfde proces gebruiken om de eigenschappen van andere typen van items, zoals de apparaatstuurprogramma's of toepassingen weer te geven.  

####  <a name="RemoveItemDeployShare"></a> Een Item uit een Implementatieshare verwijderen  
 U kunt een item verwijderen van een implementatie share met de [Item verwijderen](http://technet.microsoft.com/library/hh849765) cmdlet. De [Item verwijderen](http://technet.microsoft.com/library/hh849765) cmdlet wordt de MDTProvider verwijderd met een specifiek item net zoals u kunt een item in de Workbench-implementatie verwijderen. Als u wilt verwijderen meerdere items in een implementatie delen met behulp van Windows PowerShell, raadpleegt u [automatiseren populatie van een Deployment Share](#AutomatePopulateDeployShare).  

> [!NOTE]
>  Verwijderen van een item die gebruikmaakt van een takenreeks zorgt ervoor dat de takenreeks mislukt. Zorg ervoor dat een item niet wordt verwezen door andere items in de implementatieshare voorafgaand aan het item te verwijderen. Wanneer een item wordt verwijderd, kan deze niet worden hersteld.  

 **Een item te verwijderen uit de share van een implementatie met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  Controleer of de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows PowerShell-stations die zijn opgegeven met behulp van de MDTProvider worden weergegeven.  

4.  Een lijst van de items voor het type item waarvoor u de eigenschappen met weergeven zijn productiviteitsniveau retourneren de [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-Item "DS001:\Operating Systems\*" | Format-List  
    ```  

     In het vorige voorbeeld wordt wordt een lijst van de besturingssystemen in de implementatieshare weergegeven. De uitvoer wordt doorgegeven naar de **lijst indelen** cmdlet zodat de lange namen van de besturingssystemen kunnen worden weergegeven. Voor meer informatie over het gebruik van de **lijst indelen** cmdlet, Zie [met de Cmdlet lijst indelen](http://technet.microsoft.com/library/ee176830.aspx). U kunt hetzelfde proces gebruiken om te retourneren van de lijst met andere soorten items, zoals de apparaatstuurprogramma's of toepassingen.  

    > [!TIP]
    >  U kunt ook hebt gebruikt de **dir** opdracht voor het weergeven van de lijst met besturingssystemen in plaats van de [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet.  

5.  Verwijder een van de items die worden vermeld in de vorige stap met behulp van de [Item verwijderen](http://technet.microsoft.com/library/hh849765) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Remove-Item -Path "DS002:\Operating Systems\Windows 8 in Windows 8 x64 install.wim"  
    ```  

     In dit voorbeeld wordt de waarde van de *pad* parameter is het volledig gekwalificeerde Windows PowerShell-pad naar het item, inclusief de bestandsnaam die is geretourneerd in de vorige stap.  

     U kunt hetzelfde proces gebruiken om te verwijderen van andere typen items, zoals de apparaatstuurprogramma's of toepassingen.  

    > [!NOTE]
    >  Verwijderen van een item die gebruikmaakt van een takenreeks zorgt ervoor dat de takenreeks mislukt. Zorg ervoor dat een item niet wordt verwezen door andere items in de implementatieshare voorafgaand aan het item te verwijderen.  

###  <a name="AutomatePopulateDeployShare"></a> Populatie van een Implementatieshare automatiseren  
 De MDT Windows PowerShell-cmdlets kunt u afzonderlijke items beheren. Met behulp van enkele van de functies uitvoeren van scripts in Windows PowerShell, kunnen de cmdlets worden gebruikt voor het automatiseren van de populatie van een implementatieshare.  

 Bijvoorbeeld een organisatie kan het nodig voor het implementeren van meerdere implementatieshares voor verschillende business units of een organisatie kan bieden operating system deployment-services van andere organisaties. In beide voorbeelden moeten de organisaties de mogelijkheid om te maken en vullen implementatieshares die consistent zijn geconfigureerd.  

 Een methode voor het beheren van meerdere items kan worden gebruikt een door komma's gescheiden waarden (CSV)-bestand met een lijst met alle de items die u wilt beheren in een implementatie delen met behulp van de [importeren CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet.  

 Het volgende is een fragment van een Windows PowerShell-script voor het importeren van een lijst met toepassingen op basis van de informatie in een CSV-bestand met de [importeren CSV](http://technet.microsoft.com/library/dd347665.aspx), [ForEach-Object](http://technet.microsoft.com/library/hh849731), en  **Importeren MDTApplication** cmdlets:  

```  
$List=Import-CSV "C:\MDT\Import-MDT-Apps.csv"  
ForEach-Object ($App in $List) {  
Import-MDTApplication –path $App.ApplicationFolder -enable "True" –Name $App.DescriptiveName –ShortName $App.Shortname –Version $App.Version –Publisher $App.Publisher –Language $App.Language –CommandLine $App.CommandLine –WorkingDirectory $App.WorkingDirectory –ApplicationSourcePath $App.SourceFolder –DestinationFolder $App.DestinationFolder –Verbose  
}  
```  

 In dit voorbeeld bevat het bestand C:\MDT\Import-MDT-Apps.csv een veld voor elke variabele die nodig zijn voor een toepassing importeren. Voor meer informatie over het maken van een CSV-bestand voor gebruik met de [importeren CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet, Zie [met de Cmdlet Import-Csv](http://technet.microsoft.com/library/ee176874.aspx).  

 U kunt deze dezelfde methode gebruiken voor het importeren van besturingssystemen, stuurprogramma's en andere items in een implementatieshare door de volgende stappen uit te voeren:  

1.  Maak een .csv-bestand voor elk type deployment share-item dat u wilt vullen.  

2.  Voor meer informatie over het maken van een CSV-bestand voor gebruik met de [importeren CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet, Zie [met de Cmdlet Import-Csv](http://technet.microsoft.com/library/ee176874.aspx).  

3.  Maak een Windows PowerShell-scriptbestand dat wordt gebruikt voor het automatiseren van de populatie van de implementatieshare.  

     Zie voor meer informatie over het maken van een Windows PowerShell-script [met Windows PowerShell-scripts](http://technet.microsoft.com/scriptcenter/powershell.aspx).  

4.  Alle vereiste mapstructuur vereist in de implementatieshare vóór het importeren van de implementatie-share-items maken.  

     Zie voor meer informatie [beheren implementatie Share mappen met Windows PowerShell](#ManageDeployShareFolder).  

5.  Voeg de [importeren CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet-regel voor een van de CSV-bestanden die zijn gemaakt in stap 1.  

     Voor meer informatie over de [importeren CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet, Zie [met de Cmdlet Import-Csv](http://technet.microsoft.com/library/ee176874.aspx).  

6.  Maak een [ForEach-Object](http://technet.microsoft.com/library/hh849731) cmdlet lus dat elk item van het CSV-bestand waarnaar wordt verwezen in verwerkt de [importeren CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet in de vorige stap.  

     Voor meer informatie over de [ForEach-Object](http://technet.microsoft.com/library/hh849731) cmdlet, Zie [met de Cmdlet ForEach-Object](http://technet.microsoft.com/library/ee176828).  

7.  Toevoegen van de bijbehorende MDT-cmdlet voor het importeren van de items van de implementatie-share op de [ForEach-Object](http://technet.microsoft.com/library/hh849731) cmdlet lus in de vorige stap hebt gemaakt.  

     Zie voor meer informatie over de MDT-cmdlets gebruikt om items te importeren in een implementatieshare [importeren van een Item in een Deployment Share](#ImportItemDeployShare).  

###  <a name="ManageDeployShareFolder"></a> Het beheren van Implementatiemappen van Share met Windows PowerShell  
 U kunt mappen in een implementatieshare met de opdrachtregelprogramma's zoals beheren de **mkdir** opdracht of met Windows PowerShell-cmdlets, zoals de [New Item](http://technet.microsoft.com/library/hh849795) cmdlet en de MDTProvider Windows PowerShell-provider. De mapstructuur implementatieshares kan ook worden gezien en beheerd in de implementatie-Workbench. Zie voor meer informatie over het bewerken van items die rechtstreeks met Windows PowerShell-cmdlets, [Items rechtstreeks bewerken van](http://technet.microsoft.com/library/dd315266.aspx).  

#### <a name="create-a-folder-in-a-deployment-share-using-windows-powershell"></a>Maak een map in de Share van een implementatie met Windows PowerShell  
 **Een map maken in de share van een implementatie met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  De lijst met MDT-implementaties die delen van Windows PowerShell-stations, één voor elke implementatieshare weergeven met behulp van de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows-PowerShell stations die zijn opgegeven met behulp van de MDTProvider worden vermeld, één voor elke implementatieshare  

4.  Maak een map met de naam *Windows_8* delen in de map besturingssystemen in een implementatie met behulp van de **mkdir** opdracht, zoals wordt weergegeven in het volgende voorbeeld:  

    ```  
    mkdir "DS002:\Operating Systems\Windows_8"  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

5.  Controleer of de map correct is gemaakt door de volgende opdracht te typen:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     De map Windows_8 en eventuele bestaande mappen in de map besturingssystemen wordt weergegeven.  

6.  Maak een map met de naam *Windows_7* map in de map besturingssystemen in een implementatie share met de [New Item](http://technet.microsoft.com/library/hh849795) cmdlet als in het volgende voorbeeld wordt weergegeven en beschreven in [werken met de Nieuw Item Cmdlet](http://technet.microsoft.com/library/ee176914.aspx):  

    ```  
    New-Item "DS002:\Operating Systems\Windows_7" -Type directory  
    ```  

     De cmdlet geeft de geslaagde maken van de map.  

7.  Controleer of de map correct is gemaakt door de volgende opdracht te typen:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     De map Windows_7 en eventuele bestaande mappen in de map besturingssystemen wordt weergegeven.  

#### <a name="delete-a-folder-in-a-deployment-share-using-windows-powershell"></a>Verwijderen van een map in de Share van een implementatie met Windows PowerShell  
 **Een map in een implementatie met Windows PowerShell verwijderen**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  De lijst met MDT-implementaties die delen van Windows PowerShell-stations, één voor elke implementatieshare weergeven met behulp van de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows-PowerShell stations die zijn opgegeven met behulp van de MDTProvider worden vermeld, één voor elke implementatieshare.  

4.  Verwijderen (verwijderen), een map met de naam *Windows_8* delen in de map besturingssystemen in een implementatie met behulp van de **mkdir** opdracht, zoals wordt weergegeven in het volgende voorbeeld:  

    ```  
    rmdir "DS002:\Operating Systems\Windows_8"  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

5.  Controleer of de map correct is verwijderd door de volgende opdracht te typen:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     De map Windows_8 wordt niet meer weergegeven in de lijst met mappen in de map besturingssystemen.  

6.  Verwijderen (verwijderen), een map met de naam *Windows_7* map in de map besturingssystemen in een implementatie share met de [Item verwijderen](http://technet.microsoft.com/library/hh849765) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Remove-Item "DS002:\Operating Systems\Windows_7"  
    ```  

     De cmdlet geeft de geslaagde verwijdering van de map.  

7.  Controleer of de map correct is gemaakt door de volgende opdracht te typen:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     De map Windows_7 is niet meer weergegeven in de lijst met mappen in de map besturingssystemen.  

#### <a name="rename-a-folder-in-a-deployment-share-using-windows-powershell"></a>Wijzig de naam van een map in de Share van een implementatie met Windows PowerShell  
 **Naam wijzigen van een map in de share van een implementatie met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties deelt met Windows PowerShell stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  De lijst weergeven met MDT implementaties delen Windows PowerShell-stations, één voor elke implementatie delen, met behulp van de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet als volgt:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows-PowerShell stations die zijn opgegeven met behulp van de MDTProvider worden vermeld, één voor elke implementatieshare.  

4.  Wijzig de naam van een map met de naam *Windows_8* naar *Win_8* delen in de map besturingssystemen in een implementatie met behulp van de **ren** opdracht, zoals wordt weergegeven in het volgende voorbeeld:  

    ```  
    ren "DS002:\Operating Systems\Windows_8" "Win_8"  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

5.  Controleer of de map correct is verwijderd door de volgende opdracht te typen:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     De map Windows_8 is gewijzigd in *Win_8*.  

6.  Wijzig de naam van een map met de naam *Windows_7* naar *Win 7* delen in de map besturingssystemen in een implementatie met behulp van de [Rename-Item](http://technet.microsoft.com/library/hh849763) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Rename-Item "DS002:\Operating Systems\Windows_7" "Win_7"  
    ```  

     De cmdlet geeft de geslaagde Wijzig de naam van de map.  

7.  Controleer of de map correct is gemaakt door de volgende opdracht te typen:  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     De map Windows_7 is gewijzigd in *Win_7*.  

## <a name="automating-the-application-of-operating-system-service-packs-in-deployment-shares"></a>Automatisering van de toepassing van het besturingssysteem, Service Packs in Implementatieshares  
 Besturingssysteem, servicepacks normale deel uitmaken van de levenscyclus van de software. De bestaande besturingssystemen in shares worden bijgewerkt met deze servicepacks moeten om ervoor te zorgen dat nieuwe geïmplementeerd of vernieuwd computers implementatie zijn van de meest recente aanbevelingen voor beveiliging en configuratie-instellingen.  

 In gevallen waarin een organisatie veel implementatieshares met meerdere besturingssystemen in elke implementatieshare heeft, kan het proces voor de besturingssystemen in elke implementatieshare handmatig bij te werken met de servicepacks enige tijd duren. De methoden voor het automatiseren van de toepassing van het besturingssysteem, service packs in de implementatie shares omvatten:  

-   Bijgewerkte broninhoud die al deel uit van het servicepack (bijvoorbeeld, Windows 7 met SP1-media) kopiëren naar de map in de implementatieshare in die het bestaande besturingssysteem zich bevindt, zoals beschreven in [automatisering van de toepassing van Servicepacks besturingssysteem vanaf het BRONmedium bijgewerkt](#AutomateAppFromUSM)  

-   Het servicepack toepassen op een referentiecomputer en vervolgens een bijgewerkte installatiekopie van een referentiecomputer vastlegt, zoals beschreven in [automatisering van de toepassing van besturingssysteem Service Packs gebruikmaakt van een referentiecomputer en de Windows PowerShell](#AutomateAppUsingRef)  

###  <a name="AutomateAppFromUSM"></a> De toepassing van het besturingssysteem, servicepacks vanaf het BRONmedium bijgewerkte automatiseren  
 U kunt het proces van het besturingssysteem servicepacks met Windows PowerShell als er bronmedia die het service Pack, zoals een DVD met Windows 7 met SP1 al is geïntegreerd met bijwerken automatiseren.  

 Voor deze methode wordt de bronmedia besturingssysteem met het servicepack gekopieerd via de bestaande bestanden van besturingssysteem zonder servicepack in de share van de implementatie met Windows PowerShell.  

 **Voor het automatiseren van de toepassing van het besturingssysteem, servicepacks vanaf het BRONmedium van updates met Windows PowerShell**  

1.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

2.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

3.  De lijst weergeven met MDT implementaties delen Windows PowerShell-stations, één voor elke implementatie delen, met behulp van de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows-PowerShell stations die zijn opgegeven met behulp van de MDTProvider worden vermeld, één voor elke implementatieshare.  

4.  De map voor het bestaande besturingssysteem verwijderen uit de deployment share via de [Get-ChildItem](http://technet.microsoft.com/library/hh849800) en [Item verwijderen](http://technet.microsoft.com/library/hh849765) cmdlets, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-ChildItem “DS002:\Operating Systems\Windows 7” –recurse | Remove-Item –recurse –force  
    ```  

     In dit voorbeeld *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

5.  Kopieer de inhoud van de bronbestanden van het besturingssysteem waarvoor het servicepack geïntegreerd met de [Copy-Item](http://technet.microsoft.com/library/hh849793) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Copy-Item "E:\*" -Destination "DS002:\Operating Systems\Windows 7"-Recurse -Force  
    ```  

     In dit voorbeeld wordt de bronbestanden van het besturingssysteem zich op station E, en *DS002:* is de naam van een Windows PowerShell-station werd verkregen in stap 3.  

6.  Bijwerken van de MDT-implementatiemedia op basis van een implementatie met behulp van share **Update MDTMedia** cmdlet.  

 Voor meer informatie over het bijwerken van MDT media voor implementatie op basis van implementatie delen met behulp van **Update MDTMedia** cmdlet, Zie [bijwerken implementatie Media Windows PowerShell gebruiken](#UpdateDeployMedia).  

###  <a name="AutomateAppUsingRef"></a> De toepassing van servicepacks besturingssysteem met behulp van een referentiecomputer en de Windows PowerShell automatiseren  
 U kunt het proces van het besturingssysteem servicepacks met Windows PowerShell als u alleen het nog niet is geïntegreerd met het besturingssysteem, zoals met SP1 voor Windows 7 nog niet is geïntegreerd met een installatiekopie van Windows 7 servicepack hebt bijwerken automatiseren.  

 Bij deze methode wordt door het besturingssysteem zonder servicepack naar een referentiecomputer te implementeren. Het servicepack vervolgens toepassen op de referentiecomputer. Vervolgens de installatiekopie van een besturingssysteem van de referentiecomputer vastleggen. Ten slotte het vastgelegde WIM-bestand kopiëren via het bestand Install.wim in het besturingssysteem in de share van de implementatie met Windows PowerShell.  

 **Voor het automatiseren van de toepassing van het besturingssysteem, servicepacks vanaf het BRONmedium van updates met Windows PowerShell**  

1.  Het beoogde besturingssysteem implementeren op een referentiecomputer.  

     Zie voor meer informatie over het implementeren van een referentiecomputer de volgende bronnen in het document MDT *met behulp van de Microsoft Deployment Toolkit*:  

    -   "LTI-implementatie op de referentiecomputer voorbereiden"  

    -   'Om te implementeren en een installatiekopie van de referentiecomputer in LTI vastleggen'  

2.  De gewenste servicepack installeren op de referentiecomputer.  

     Zie de documentatie bij het servicepack voor meer informatie over het installeren van het servicepack.  

3.  Leg een installatiekopie van de referentiecomputer vast door te maken en implementeren van een takenreeks op basis van de **Sysprep en vastleggen** taak sequence sjabloon.  

     Voor meer informatie over het maken van een takenreeks op basis van de **Sysprep en vastleggen** task sequence sjabloon, raadpleegt u 'Maak een nieuwe taak volgorde in de implementatie-Workbench'.  

4.  Laad de MDT Windows PowerShell-module, zoals beschreven in [bij het laden van de MDT Windows PowerShell Snap-In](#LoadMDTSnapIn).  

5.  Zorg ervoor dat de MDT-implementaties die delen van Windows PowerShell-stations zijn teruggezet met behulp van de **terugzetten MDTPersistentDrive** cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Als de MDT-implementaties die delen van Windows PowerShell-stations zijn al hersteld, ontvangt u een waarschuwingsbericht dat aangeeft dat de cmdlet kan niet worden hersteld van de schijf.  

6.  De lijst weergeven met MDT implementaties delen Windows PowerShell-stations, één voor elke implementatie delen, met behulp van de [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     De lijst met Windows-PowerShell stations die zijn opgegeven met behulp van de MDTProvider worden vermeld, één voor elke implementatieshare.  

7.  Kopieer het WIM-bestand dat is vastgelegd in stap 3 via het bestand Install.wim in het besturingssysteem in het deployment share met de [Copy-Item](http://technet.microsoft.com/library/hh849793) cmdlet, zoals weergegeven in het volgende voorbeeld:  

    ```  
    Copy-Item "DS002:\Captures\Win7SP1.wim" -Destination "DS002:\Operating Systems\Windows 7\sources\Install.wim" Force  
    ```  

     In dit voorbeeld wordt de vastgelegde installatiekopie besturingssysteembestand (Win7SP1.wim) in de map opnamen in de share DS002: de naam van een Windows PowerShell-station geretourneerd in stap 6 en het bestaande Windows 7-besturingssysteem wordt opgeslagen in de map met de naam  *Windows 7*.  

8.  Bijwerken van de MDT-implementatiemedia op basis van een implementatie met behulp van share **Update MDTMedia** cmdlet.  

     Voor meer informatie over het bijwerken van MDT media voor implementatie op basis van implementatie delen met behulp van **Update MDTMedia** cmdlet, Zie [bijwerken implementatie Media Windows PowerShell gebruiken](#UpdateDeployMedia).  

## <a name="customizing-deployment-based-on-chassis-type"></a>Implementatie aanpassen op basis van chassistype  
 U kunt de implementatie op basis van het chassistype van de computer. De scripts lokale variabelen maken die kunnen worden verwerkt in het CustomSettings.ini-bestand. De lokale variabelen `IsLaptop`, `IsDesktop`, en `IsServer` geeft aan of de computer een draagbare computer, een desktopcomputer of een server, respectievelijk is.  

> [!NOTE]
>  In eerdere versies van de implementatie-Workbench de `IsServer` vlag aangegeven dat het bestaande besturingssysteem een serverbesturingssysteem (zoals Windows Server 2003, Enterprise Edition is). Deze vlag is gewijzigd in `IsServerOS`.  

 **Lokale variabelen in het bestand CustomSettings.ini implementeren**  

1.  In de `[Settings]` sectie op de `Priority` regel, een aangepaste sectie voor het aanpassen van de implementatie op basis van het chassistype toevoegen (`ByChassisType` in het volgende voorbeeld, waarbij *Chassis* vertegenwoordigt het type computer).  

2.  Maken van de aangepaste sectie die overeenkomt met de aangepaste sectie die is gedefinieerd in stap 1 (`ByChassisType` in het voorbeeld in het volgende voorbeeld, waarbij *Chassis* vertegenwoordigt het type computer).  

3.  Definieer een subsectie voor elk chassistype voor het detecteren van (`Subsection=Laptop-%IsLaptop%, Subsection=Desktop-%IsDesktop%, Subsection=Server-%IsServer%` in het volgende voorbeeld).  

4.  Maak een subsectie voor elk `True` en `False` status van elke subsectie gedefinieerd in stap 3 (zoals `[Laptop-True], [Laptop-False], [Desktop-True], [Desktop-False]` in het volgende voorbeeld).  

5.  Onder elke `True` en `False` subsectie, de gewenste instellingen op basis van het chassistype toevoegen.  

 **Aanbieding 1. Voorbeeld van een implementatie op basis van chassistype in het bestand CustomSettings.ini aanpassen**  

```  
[Settings]  

Priority=...,ByLaptopType,ByDesktopType,ByServerType  

[ByLaptopType]  
Subsection=Laptop-%IsLaptop%  

[ByDesktopType]  
Subsection=Desktop-%IsDesktop%  

[ByServerType]  
Subsection=Server-%IsServer%  
.  
.  
.  

[Laptop-True]  
.  
.  
.  

[Laptop-False]  
.  
.  
.  

[Desktop-True]  
.  
.  
.  

[Desktop-False]  
.  
.  
.  

[Server-True]  
.  
.  
.  

[Server-False]  
.  
.  
.  
```  

## <a name="deploying-applications-based-on-earlier-application-versions"></a>Implementatie van toepassingen op basis van eerdere versies van de toepassing  
 Als u een besturingssysteem installeert op een bestaande computer, installeert u vaak de toepassingen die u eerder hebt geïnstalleerd op de computer. Dit doen met behulp van MDT-scripts (met name ZTIGather.wsf) twee afzonderlijke bronnen met informatie opvragen:  

-   **Configuration Manager software-inventarisatie-functie.** Een record voor elk pakket bevat: in dit geval, lijsten in programma's en onderdelen in Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2: de laatste keer dat Configuration Manager geïnventariseerd geïnstalleerd de computer.  

-   **Een toewijzingstabel.** Hierin wordt beschreven welke pakket en programma worden geïnstalleerd voor elke record moeten (omdat de records programma en functies of een programma verwijderen of geef geen precies welke pakket geïnstalleerd voor de toepassing, waardoor het onmogelijk om het pakket automatisch selecteren op basis van alleen inventarisatie).  

 **De installatie van een dynamische computer-specifieke toepassing uitvoeren**  

1.  Gebruik de tabel in de MDT-database koppelen specifieke pakketten met toepassingen die worden vermeld in het beoogde besturingssysteem.  

2.  De tabel met gegevens die wordt gekoppeld aan het juiste pakket met de toepassing die worden vermeld in programma en functies of een programma verwijderen of vullen.

     **SQL-Query voor het vullen van de tabel**  

    ```  
    use [MDTDB]  
    go  
    INSERT INTO [PackageMapping] (ARPName, Packages) VALUES('Office12.0', 'XXX0000F:Install Office 2010 Professional Plus')  
    go  
    ```  

     De ingevoegde rij verbindt elke computer met de vermelding `Office12.0` pakket met de Microsoft Office 2010 Professional Plus.  

     Dit betekent dat Microsoft Office 2010 Professional Plus wordt geïnstalleerd op elke computer die momenteel met de 2007 Microsoft Office-systeem (Office 12.0). Vergelijkbare vermeldingen voor alle andere pakketten toevoegen. Een item waarvoor er geen vermelding is wordt genegeerd (kan geen pakket wordt geïnstalleerd).  

3.  Maak een opgeslagen procedure voor het koppelen van de informatie in de nieuwe tabel met de inventarisatiegegevens vereenvoudigen.  

    ```  
    use [MDTDB]  
    go  

    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[RetrievePackages]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
    drop procedure [dbo].[RetrievePackages]  
    go  

    CREATE PROCEDURE [dbo].[RetrievePackages]  
    @MacAddress CHAR(17)  
    AS  

    SET NOCOUNT ON  

    /* Select and return all the appropriate records based on current inventory */  
    SELECT * FROM PackageMapping  
    WHERE ARPName IN  
    (  
      SELECT ProdID0 FROM CM_DB.dbo.v_GS_ADD_REMOVE_PROGRAMS a, CM_DB.dbo.v_GS_NETWORK_ADAPTER n  
      WHERE a.ResourceID = n.ResourceID AND  
      MACAddress0 = @MacAddress  
    )  
    go  
    ```  

     De opgeslagen procedure in het voorgaande voorbeeld wordt ervan uitgegaan dat de Configuration Manager-database centrale, primaire site bevindt zich op de computer waarop SQL Server wordt uitgevoerd als de MDT-database. Als de centrale, primaire site-database zich op een andere computer bevindt, moeten de juiste wijzigingen worden aangebracht in de opgeslagen procedure. Daarnaast is de naam van de database (`CM_DB`) moeten worden bijgewerkt. Ook rekening houden met extra accounts lezen toegang verlenen tot de **v_GS_ADD_REMOVE_PROGRAMS** weergave in de Configuration Manager-database.  

4.  Configureren van het CustomSettings.ini-bestand om op te vragen van deze databasetabel door te geven van de naam van een sectie (`[DynamicPackages]` in de **prioriteit** lijst) die verwijst naar de database-informatie.  

    ```  
    [Settings]  
    …  
    Priority=MacAddress, DefaultGateway, DynamicPackages, Default  
    …  
    ```  

5.  Maak een `[DynamicPackages]` sectie de naam van een sectie database opgeven.  

    ```  
    [DynamicPackages]  
    SQLDefault=DB_DynamicPackages  
    ```  

6.  Maak een sectie database om de details van de database en de query opgeven.  

    ```  
    [DB_DynamicPackages]  
    SQLServer=SERVER1  
    Database=MDTDB  
    StoredProcedure=RetrievePackages  
    Parameters=MacAddress  
    SQLShare=Logs  
    Instance=SQLEnterprise2005  
    Port=1433  
    Netlib=DBNMPNTW  
    ```  

     In het voorgaande voorbeeld wordt de MDT-database met de naam *MDTDB* op de computer met de SQL-Server gestart met de naam *SERVER1* wordt gezocht. De database bevat een opgeslagen procedure met de naam `RetrievePackages` (gemaakt in stap 3).  

 Wanneer ZTIGather.wsf wordt uitgevoerd, wordt een Structured Query Language (SQL) `SELECT` instructie automatisch wordt gegenereerd, en de waarde van de **MakeModelQuery** aangepaste sleutel is doorgegeven als parameter aan de query:  

 ```  
 EXECUTE RetrievePackages ?  
 ```  

 De werkelijke waarde van de **MACAddress** aangepaste sleutel worden vervangen door de bijbehorende '? '.  Deze query retourneert een record met de rijen die in stap 2 hebt opgegeven.  

 Een variabel aantal argumenten kan niet worden doorgegeven aan een opgeslagen procedure. Als gevolg hiervan, wanneer een computer meer dan één MAC-adres heeft, kan niet alle MAC-adressen kunnen worden doorgegeven aan de opgeslagen procedure. Als alternatief kunt vervangen door de opgeslagen procedure een weergave waarmee opvragen van de weergave met een `SELECT` instructie met een `IN` component om door te geven van alle waarden voor MAC-adres.  

 Op basis van het scenario dat hier wordt weergegeven als de huidige computer de waarde heeft `Office12.0` ingevoegd in de tabel (stap 2), wordt de ene rij geretourneerd (`XXX0000F:Install Office 2010 Professional Plus`). Hiermee wordt aangegeven dat pakket die xxx0000f:Install Office 2001 Professional Plus wordt geïnstalleerd door het proces ZTI tijdens de fase voor het herstellen van status.  

## <a name="fully-automated-lti-deployment-scenario"></a>Volledig geautomatiseerde LTI implementatiescenario  
 Het belangrijkste doel van LTI is voor het automatiseren van het implementatieproces zo veel mogelijk. Hoewel ZTI volledige implementatie automation met behulp van de MDT-scripts en de Windows Deployment Services biedt, wordt de LTI ontworpen voor gebruik met minder vereisten voor de infrastructuur.  

 U kunt de Wizard implementatie van Windows gebruikt in het implementatieproces LTI te verlagen (of elimineren) op de wizardpagina's weergegeven automatiseren. U kunt de volledige versie van Windows Deployment Wizard overslaan door op te geven de **SkipWizard** eigenschap in CustomSettings.ini. Om over te slaan afzonderlijke wizardpagina's, gebruikt u de volgende eigenschappen:  

-   **SkipAdminPassword**  

-   **SkipApplications**  

-   **SkipBDDWelcome**  

-   **SkipBitLocker**  

-   **SkipBitLockerDetails**  

-   **SkipTaskSequence**  

-   **SkipCapture**  

-   **SkipComputerBackup**  

-   **SkipComputerName**  

-   **SkipDomainMembership**  

-   **SkipFinalSummary**  

-   **SkipLocaleSelection**  

-   **SkipPackageDisplay**  

-   **SkipProductKey**  

-   **SkipSummary**  

-   **SkipTimeZone**  

-   **SkipUserData**  

Zie voor meer informatie over deze afzonderlijke eigenschappen, de overeenkomstige eigenschap in het document MDT *Toolkit verwijzing*.  

Geef de waarden voor de bijbehorende eigenschappen die doorgaans worden verzameld via de wizardpagina in de bestanden CustomSettings.ini en BootStrap.ini voor elke pagina overgeslagen. Zie de sectie 'Bieden eigenschappen voor overgeslagen implementatie wizardpagina's ', in het document MDT voor meer informatie over de eigenschappen die in deze bestanden moeten worden geconfigureerd, *Toolkit verwijzing*.  

## <a name="fully-automated-lti-deployment-for-a-refresh-computer-scenario"></a>Implementatie van de volledig geautomatiseerde LTI voor een Computer vernieuwen Scenario  
 Het volgende voorbeeld illustreert CustomSettings.ini-bestand dat wordt gebruikt voor een scenario Computer vernieuwen om over te slaan, alle pagina's van Windows Deployment-Wizard. In dit voorbeeld zijn de eigenschappen op te geven wanneer de wizardpagina overslaan direct onder de eigenschap die de wizardpagina wordt overgeslagen.  

```  
[Settings]  
Priority=Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac /lae  
SkipCapture=YES  
SkipAdminPassword=YES  
SkipProductKey=YES  

DeploymentType=REFRESH  

SkipDomainMembership=YES  
JoinDomain=DomainName  
DomainAdmin=Administrator  
DomainAdminDomain=DomainName  
DomainAdminPassword=a_secure_password  

SkipUserData=yes  
UserDataLocation=AUTO  
UDShare=\\Servername\Sharename\Directory  
UDDir=%ComputerName%  

SkipComputerBackup=YES  
ComputerBackuplocation=AUTO  
BackupShare=\\Servername\Backupsharename  
BackupDir=%ComputerName%  

SkipTaskSequence=YES  
TaskSequenceID=Enterprise  

SkipComputerName=YES  
OSDComputerName=%ComputerName%  

SkipPackageDisplay=YES  
LanguagePacks001={3af4e3ce-8122-41a2-9cf9-892145521660}  
LanguagePacks002={84fc70d4-db4b-40dc-a660-d546a50bf226}  

SkipLocaleSelection=YES  
UILanguage=en-US  
UserLocale=en-CA  
KeyboardLocale=0409:00000409  

SkipTimeZone=YES  
TimeZoneName=China Standard Time  

SkipApplications=YES  
Applications001={a26c6358-8db9-4615-90ff-d4511dc2feff}  
Applications002={7e9d10a0-42ef-4a0a-9ee2-90eb2f4e4b98}  
UserID=Administrator  
UserDomain=DomainName  
UserPassword=P@ssw0rd  

SkipBitLocker=YES  
SkipSummary=YES  
Powerusers001=DomainName\Username  
```  

## <a name="fully-automated-lti-deployment-for-a-new-computer-scenario"></a>Implementatie van de volledig geautomatiseerde LTI voor een nieuwe Computer Scenario  
 Hier volgt een voorbeeld van het CustomSettings.ini-bestand dat wordt gebruikt voor een scenario voor de nieuwe Computer over te slaan, alle pagina's van Windows Deployment-Wizard. In dit voorbeeld zijn de eigenschappen op te geven wanneer de wizardpagina overslaan direct onder de eigenschap die de wizardpagina wordt overgeslagen.  

```  
[Settings]  
Priority=Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac /lae  

SkipCapture=YES  
ComputerBackupLocation=\\WDG-MDT-01\Backup$\  
BackupFile=MyCustomImage.wim  

SkipAdminPassword=YES  
SkipProductKey=YES  

SkipDomainMembership=YES  
JoinDomain=WOODGROVEBANK  
DomainAdmin=Administrator  
DomainAdminDomain=WOODGROVEBANK  
DomainAdminPassword=P@ssw0rd  

SkipUserData=Yes  
UserDataLocation=\\WDG-MDT-01\UserData$\Directory\usmtdata  

SkipTaskSequence=YES  
TaskSequenceID=Enterprise  

SkipComputerName=YES  
OSDComputerName=%SerialNumber%  

SkipPackageDisplay=YES  
LanguagePacks001={3af4e3ce-8122-41a2-9cf9-892145521660}  
LanguagePacks002={84fc70d4-db4b-40dc-a660-d546a50bf226}  

SkipLocaleSelection=YES  
UILanguage=en-US  
UserLocale=en-CA  
KeyboardLocale=0409:00000409  

SkipTimeZone=YES  
TimeZoneName=China Standard Time  

SkipApplications=YES  
Applications001={a26c6358-8db9-4615-90ff-d4511dc2feff}  
Applications002={7e9d10a0-42ef-4a0a-9ee2-90eb2f4e4b98}  

SkipBitLocker=YES  
SkipSummary=YES  
Powerusers001=WOODGROVEBANK\PilarA  
CaptureGroups=YES  
SLShare=\\WDG-MDT-01\UserData$\Logs  
Home_page=http://www.microsoft.com/NewComputer  
```  

## <a name="calling-web-services-in-mdt"></a>De webservices aanroepen in MDT  
 In eerdere versies van MDT regels voor de verwerking werd ondersteund via CustomSettings.ini en databases, van waaruit u de waarden van de lokale computer kan ophalen, meestal met behulp van WMI, om beslissingen te nemen op wat nodig om te worden uitgevoerd op elke computer tijdens de implementatie. Bovendien kunt u SQL-query's en opgeslagen procedure-aanroepen naar aanvullende informatie ophalen uit externe databases. Er echter zijn uitdagingen bij deze aanpak, vooral bij het maken van beveiligde SQL-verbindingen.  

 MDT biedt om te helpen bij dit probleem, de mogelijkheid web service aanroepen op basis van eenvoudige regels die zijn gedefinieerd in CustomSettings.ini. Deze web service-aanvragen vereisen speciale beveiligingscontext geen en welke TCP/IP-poort nodig is voor het vereenvoudigen van firewallconfiguraties kunnen gebruiken.  

 Hieronder ziet u het CustomSettings.ini voor het aanroepen van een bepaalde webservice configureren. De webservice wordt in dit scenario wordt willekeurig geselecteerd uit een zoekopdrachten op Internet. Het duurt een postcode als invoer en retourneert de stad, staat, netnummer en tijdzone (als een letter) voor de opgegeven postcode.  

```  
[Settings]  
Priority=Default, USZipService  
Properties=USZip, City, State, Zip, Area_Code, Time_Zones   
[Default]  
USZip=98052   
[USZipService]  
WebService=http://www.webservicex.net/uszip.asmx/GetInfoByZIP  
Parameters=USZip  
```  

 Deze code wordt uitgevoerd, wordt de uitvoer ziet er als volgt:
```  
Added new custom property USZIP  
Added new custom property CITY  
Added new custom property STATE  
Added new custom property ZIP  
Added new custom property AREA_CODE  
Added new custom property TIME_ZONES  
Using from [Settings]: Rule Priority = DEFAULT, USZIPSERVICE  
------ Processing the [DEFAULT] section ------  
Property USZIP is now = 98052  
Using from [DEFAULT]: USZIP = 98052  
------ Processing the [USZIPSERVICE] section ------  
Using COMMAND LINE ARG: Ini file = CustomSettings.ini  
CHECKING the [USZIPSERVICE] section  
About to execute web service call to http://www.webservicex.net/uszip.asmx/GetInfoByZIP: USZip=98052  
Response from web service: 200 OK  
Successfully executed the web service.  
Property CITY is now = Redmond  
Obtained CITY value from web service:  CITY = Redmond  
Property STATE is now = WA  
Obtained STATE value from web service:  STATE = WA  
Property ZIP is now = 98052  
Obtained ZIP value from web service:  ZIP = 98052  
Property AREA_CODE is now = 425  
Obtained AREA_CODE value from web service:  AREA_CODE = 425  
------ Done processing CustomSettings.ini ------  
```  

 Er zijn een paar kleine problemen moeten worden gecontroleerd bij het uitvoeren van een webservice:  

-   Doe iets speciale met proxyservers. Als er een anonieme proxy aanwezig is, worden gebruikt, maar het verifiëren van proxy's problemen kan veroorzaken. In de meeste gevallen wordt een webservice niet worden aangeroepen.  

-   CustomSettings.ini of ZTIGather.xml zoekopdrachten voor eigenschappen die zijn gedefinieerd in de XML-opmaak geretourneerd als gevolg van de aanroep van webservice (net als bij een databasequery of een andere regel). De XML-zoekactie is echter wel hoofdlettergevoelig. Gelukkig retourneert de hier beschreven webservice alle hoofdletters eigenschapnamen, dit is wat ZTIGather.xml verwacht. Het is mogelijk opnieuw toewijzen van kleine letters of hoofdletters vermeldingen voor dit omzeilen.  

-   Een `POST` aanvraag met de webservice wordt aanbevolen, zodat de webserviceaanroep moeten kunnen ondersteunen een `POST`.  

## <a name="connecting-to-network-resources"></a>Verbinding maken met netwerkbronnen  
 Tijdens de LTI en ZTI implementatieprocessen mogelijk u toegang hebben tot een netwerkbron op een server die verschilt van de server die als host fungeert voor de implementatieshare. U moet op de andere server worden geverifieerd, zodat u toegang hebt tot gedeelde mappen of er services. Bijvoorbeeld, kunt u een toepassing installeert vanaf een gedeelde map op een server dan de server die als host fungeert voor de share van de implementatie die gebruikmaken van de MDT-scripts.  

> [!NOTE]
>  Om te vragen van SQL Server-databases die worden gehost op een andere server dan de server die als host fungeert voor de implementatieshare, Zie de **Database**, **DBID**, **DBPwd**, **exemplaar** , **NetLib**, **volgorde**, **Parameters**, **ParameterCondition**, **SQLServer** , **SQLShare**, en **tabel** eigenschappen in het document MDT *Toolkit verwijzing*.  

 Met het script ZTIConnect.wsf, kunt u verbinding maken met andere servers en toegang tot resources op deze. De syntaxis voor het script ZTIConnect.wsf is als volgt (waarbij *unc_path* een Universal Naming Convention [UNC] pad verbinding maken met de server is):  

```  
Cscript.exe “%SCRIPTROOT%\ZTIConnect.wsf” /uncpath:unc_path  
```  

 In de meeste gevallen kunt u het script ZTIConnect.wsf uitvoeren als een taak Taaksequencer. Voer het script ZTIConnect.wsf voordat taken waarvoor de toegang tot een andere server dan de server die als host fungeert voor de implementatieshare.  

 **Het script ZTIConnect.wsf als een taak toevoegen aan de takenreeks van een build**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Task reeksen (waarbij *deployment_share* is de naam van de implementatieshare configureren ).  

3.  Klik in het detailvenster op ***task_sequence*** (waarbij *task_sequence* is de takenreeks te wijzigen).  

4.  Klik in het deelvenster Acties op **eigenschappen**.  

5.  Klik op het tabblad Takenreeks wordt uitgevoerd, bladert u naar **groep** (waarbij *groep* is de groep waarin het script ZTIConnec.wsf uitvoeren), en klik op **toevoegen**. Klik op **algemene**, en klik vervolgens op **opdrachtregel uitvoeren**.  

    > [!NOTE]
    >  De taak toevoegen voordat u alle taken waarvoor toegang tot bronnen op de doelserver toevoegt.  

6.  Voltooi de **eigenschappen** tabblad van de nieuwe taak met de volgende gegevens:

    |**In dit vak** |**Dit doet** |  
    |-|-|  
    |**Naam** |Type **verbinding maken met server** (waarbij server de naam van de server waarmee verbinding moet is).|  
    |**Beschrijving** |Typ de tekst waarin wordt uitgelegd waarom de verbinding moet worden gemaakt.|  
    |**opdracht** |Type **Cscript.exe "% SCRIPTROOT%\ZTIConnect.wsf" /uncpath:unc_path** (waarbij *unc_path* het UNC-pad naar een gedeelde map op de server is).|  

7.  Voltooi de **opties** tabblad van de nieuwe taak met de volgende gegevens. Tenzij anders aangegeven, accepteer de standaardwaarden en klik vervolgens op **OK**.  

    |**In dit vak** |**Dit doet** |  
    |-|-|  
    |**Geslaagd-codes** |Type **0 3010**. (ZTIConnect.wsf script retourneert deze codes na geslaagde voltooiing.)|  
    |**Voorwaarden keuzelijst met invoervak** |De voorwaarden die u mogelijk toevoegen. (In de meeste gevallen moet deze taak geen voorwaarden.)|  

 Na het toevoegen van de taak die wordt uitgevoerd het script ZTIConnect.wsf latere taken hebben toegang tot netwerkbronnen op de server die is opgegeven in de **/uncpath** optie van het script ZTIConnect.wsf.  

## <a name="deploying-the-correct-device-drivers-to-computers-with-the-same-hardware-devices-but-different-make-and-model"></a>De juiste apparaatstuurprogramma's implementeren op Computers met de dezelfde hardwareapparaten, maar verschillende merk en Model  
 Variaties op het modelnummers en namen kunnen met vrijwel geen verschil in de stuurprogrammaset bestaan. Deze verschillen in de modelnummers en namen kunnen onnodig tijd besteed aan het maken van meerdere items in de database van een bepaald model verhogen. De volgende procedure laat zien hoe een nieuwe eigenschap met behulp van een gebruiker afsluiten functieaanroep die een subtekenreeks van het modelnummer retourneert definiëren.  

 **Aliassen model maken**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  In de **eigenschappen** in het dialoogvenster, klikt u op de **regels** tabblad.  

5.  Aliassen voor hardwaretypen in de secties van het merk en Model van de MDT-database maken. Afkappen van het modeltype op de haakjes openen '(' in de naam van het model. Bijvoorbeeld: *HP DL360 (G112)* wordt *HP DL360*.  

6.  Toevoegen van aangepaste variabele **ModelAlias** naar elke sectie.  

7.  Maak een nieuwe `[SetModel]` sectie.  

8.  Voeg de `[SetModel]` sectie aan de **prioriteit** instellingen in de `[Settings]` sectie.  

9. Een regel toe te voegen de `ModelAlias` sectie om te verwijzen naar een script voor het afsluiten van gebruiker die worden afgekapt door de naam van het model op de "(".  

10. Maak een **MMApplications** zoekacties in de database waar **ModelAlias** gelijk is aan **Model**.  

11. Een gebruiker afsluiten script maken en plaats deze in dezelfde map als het CustomSettings.ini-bestand, de modelnaam worden afgekapt.  

    Hieronder ziet u een CustomSettings.ini en de gebruiker sluiten script, respectievelijk.  

     **CustomSettings.ini**:  

    ```  
    [Settings]   
    Priority=SetModel, MMApplications, Default   
    Properties= ModelAlias   
    [SetModel]   
    ModelAlias=#SetModelAlias()#   
    Userexit=Userexit.vbs   
    [MMApplications]   
    SQLServer=Server1  
    Database=MDTDB   
    Netlib=DBNMPNTW   
    SQLShare=logs   
    Table= MakeModelSettings    
    Parameters=Make, ModelAlias   
    ModelAlias=Model   
    Order=Sequence  
    ```  

     **Exit gebruikersscript**:  

    ```  
    Function UserExit(sType, sWhen, sDetail, bSkip)   
      UserExit = Success   
    End Function   

    Function SetModelAlias()   
      If Instr(oEnvironment.Item("Model"), "(") <> 0 Then   
        SetModelAlias = Left(oEnvironment.Item("Model"), _  
                          Instr(oEnvironment.Item("Model"), _  
                            "(") - 1)   
        oLogging.CreateEntry "USEREXIT – " & _  
          "ModelAlias has been set to " & SetModelAlias, _  
          LogTypeInfo  
      Else   
        SetModelAlias = oEnvironment.Item("Model")   
        oLogging.CreateEntry " USEREXIT - " & _  
          "ModelAlias has not been changed.", LogTypeInfo   
      End if   
    End Function  
    ```  

## <a name="configuring-conditional-task-sequence-steps"></a>Voorwaardelijke Takenreeksstappen configureren  
 In sommige scenario's, kunt u een takenreeksstap voorwaardelijk instellen op basis van de gedefinieerde criteria uitgevoerd. Elke combinatie van deze voorwaarden kunnen worden toegevoegd om te bepalen of de takenreeksstap moet worden uitgevoerd. Gebruik bijvoorbeeld de waarde van een takenreeksvariabele en de waarde van een registerinstelling om te bepalen of een takenreeksstap moet worden uitgevoerd.  

 Met MDT, voert u een takenreeks voorwaardelijk instellen op basis van:  

-   Een of meer **als** instructies  

-   Een takenreeksvariabele  

-   De versie van het beoogde besturingssysteem  

-   De Booleaanse resultaten van een WMI-query  

-   Een registerinstelling  

-   De software is geïnstalleerd op de doelcomputer  

-   De eigenschappen van een map  

-   De eigenschappen van een bestand  

### <a name="configuring-a-conditional-task-sequence-step"></a>Een voorwaardelijke Takenreeksstap configureren  
 Voorwaardelijke takenreeksstappen in de implementatie-Workbench zijn geconfigureerd op de **opties** tabblad van een takenreeksstap. U kunt een of meer voorwaarden toevoegen aan de takenreeksstap voor het maken van de juiste voorwaarde voor het uitvoeren of de stap niet uitgevoerd.  

> [!NOTE]
>  Elke voorwaardelijke takenreeksstap moet ten minste één **als** instructie.  

 **Het tabblad Opties van een takenreeksstap weergeven**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Task reeksen (waarbij *deployment_share* is de naam van de implementatieshare configureren ).  

3.  Klik in het detailvenster op **task_sequence** (waarbij *task_sequence* is de naam van de takenreeks te configureren).  

4.  Klik in het deelvenster Acties op **eigenschappen**.  

5.  In de ***task_sequence*** **eigenschappen** in het dialoogvenster op de **Takenreeks** tabblad ***stap*** (waarbij *stap* is de naam van de takenreeksstap configureren), en klik vervolgens op de **opties** tabblad.  

 Op de **opties** tabblad van de takenreeksstap, de volgende acties uitvoeren:  

-   **Add.** Klik op deze knop om een voorwaarde toevoegen aan de takenreeksstap.  

-   **Remove.** Klik op deze knop om het verwijderen van een bestaande voorwaarde van een takenreeksstap.  

-   **Edit.** Klik op deze knop om een bestaande voorwaarde van een takenreeksstap wijzigen.  

### <a name="if-statements-in-conditions"></a>Als de instructies in de voorwaarden  
 Alle taak takenreeks voorwaarden zijn een of meer **als** instructies. **Als** -instructies zijn de basis voor het maken van voorwaardelijke taak stappen. Een takenreeksstap stap groepsvoorwaarde kan slechts één bevatten **als** instructie, maar meerdere **als** instructies onder het hoogste niveau kunnen worden genest **als** instructie complexere maken voorwaarden.  

 Een **als** instructie kan zijn gebaseerd op de voorwaarden die worden vermeld in de volgende tabel, die zijn geconfigureerd in de **IF-instructie-eigenschappen** in het dialoogvenster.  

 |**Voorwaarde** |**Selecteer deze optie voor het uitvoeren van de takenreeks als** |  
 |-|-|  
 |**Alle voorwaarden** |De voorwaarden onder dit **als** instructie moet worden voldaan.|  
 |**De voorwaarden** |Alle voorwaarden onder dit **als** instructie wordt voldaan.|  
 |**Geen** |Geen van de voorwaarden onder dit **als** instructie wordt voldaan.|  

 Voltooi de voorwaarde voor het uitvoeren van de takenreeksstap door andere criteria toe te voegen aan de voorwaarden (bijvoorbeeld takenreeksvariabelen of waarden in een registerinstelling).  

 **Een IF-instructie voorwaarde toevoegen aan een takenreeksstap**  

1.  Op de ***stap*** **optie** tabblad (waarbij *stap* is de naam van de takenreeksstap configureren), klikt u op **toevoegen**, en klik vervolgens op **Als instructie**.  

2.  In de **als instructie-eigenschappen** in het dialoogvenster, klikt u op **voorwaarde** (waar *voorwaarde* is een van de voorwaarden die worden vermeld in de vorige tabel), en klik vervolgens op **OK**.  

### <a name="task-sequence-variables-in-conditions"></a>Takenreeksvariabelen in voorwaarden  
 Gebruik de **Takenreeksvariabele** voorwaarde voor het evalueren van een takenreeksvariabele gemaakt door een **Takenreeksvariabele instellen** taak of door elke taak in de takenreeks. Neem bijvoorbeeld een netwerk met Windows XP-clientcomputers die deel van een domein uitmaken en sommige die zijn opgenomen in een werkgroep. Weten dat het huidige domeinbeleid zorgt ervoor dat alle instellingen van de gebruiker op het netwerk worden opgeslagen, gebruikersinstellingen mogelijk moeten worden opgeslagen alleen voor computers die geen deel uitmaken van het domein, dat wil zeggen, de computers die zich in de werkgroep. In dit geval is, Voeg een voorwaarde waarmee wordt de **vastleggen van gebruikersbestanden en -instellingen** taak die gericht is op de computers in de werkgroep.  

 **Een voorwaarde op basis van een takenreeksvariabele toevoegen**  

1.  Op de ***stap*** **opties** tabblad (waarbij *stap* is de naam van de takenreeksstap configureren), klikt u op **voorwaarde toevoegen**, en klik vervolgens op **Takenreeksvariabele**.  

2.  In de **Takenreeksvariabele** in het dialoogvenster probleem in de **variabele** in het vak **OSDJoinType**.  

    > [!NOTE]
    >  Deze variabele is ingesteld op **0** voor computers die lid zijn van een domein en zo de **1** voor gebruikers in een werkgroep.  

3.  In de **voorwaarde** Klik **gelijk**.  

4.  In de **waarde** in het vak **1**, en klik vervolgens op **OK**.  

### <a name="operating-system-version-in-conditions"></a>Versie van besturingssysteem in de voorwaarden  
 Gebruik de **besturingssysteemversie** voorwaarde om te controleren of de bestaande versie van besturingssysteem van een doelcomputer of de bestaande client (bij het vastleggen van een afbeelding). Overweeg bijvoorbeeld een netwerk met meerdere servers die worden geüpgraded van Windows Server 2003 naar Windows Server 2008. Netwerkinstellingen moeten worden gekopieerd en worden alleen toegepast op servers met Windows Server 2003. Alle andere servers moeten de standaardinstellingen van het netwerk die gebruikmaakt van Windows Server 2008.  

 **Een voorwaarde op basis van de versie van besturingssysteem toevoegen**  

1.  In de Editor voor Takenreeksen, klikt u op de **netwerkinstellingen vastleggen** taak.  

2.  Klik op **voorwaarde toevoegen**, en klik vervolgens op **besturingssysteemversie**.  

3.  In de **architectuur** vak, klikt u op de desbetreffende server. Klik op voor dit voorbeeld **x86**.  

4.  In de **besturingssysteem** vak, klikt u op het besturingssysteem en versie waarvoor u een voorwaarde in te stellen. Klik op voor dit voorbeeld **x86 Windows 2003**.  

5.  In de **voorwaarde** op de relevante voorwaarde, en klik vervolgens op **OK**.  

### <a name="file-properties-in-conditions"></a>Eigenschappen van het bestand in de voorwaarden  
 Gebruik de **bestandseigenschappen** voorwaarde om te controleren of de versie en/of tijden tamp van een bepaald bestand om te bepalen of een taak of een groep taken uit te voeren. In dit voorbeeld bevat de productieomgeving een Windows Server 2003-installatiekopie die voortdurend wordt bijgewerkt en gebruikt voor elke nieuwe server die wordt toegevoegd aan het netwerk. Alle server-computers in de omgeving uitvoert een aangepaste toepassing waarvoor de digitale Access Object (DAO) application programming interface (API) versie 3.60.6815.  

 Alle bestaande servers werkt goed. Er is echter elke nieuwe server toegevoegd aan het netwerk met de installatiekopie kan niet worden uitgevoerd van de toepassing. Omdat het is de verantwoordelijkheid van een andere groep voor het onderhouden en installatiekopieën bijwerken, kunt u bepalen dat de takenreeks voor implementatie worden gewijzigd in de desbetreffende versie van DAO installeren als de bestaande versie van DAO geïmplementeerd met de installatiekopie is onjuist.  

 **Als u wilt de eigenschappen van een bestand toevoegen voorwaarde aan een takenreeks stap in de Configuration Manager 2007 R3**  

1.  Maak een pakket voor het installeren van DAO 3.60.6815 in Configuration Manager 2007 R3. Dit pakket aanroepen *DAO*, met een programma, *InstallDAO*. Zie voor meer informatie over het maken van pakketten, [het maken van een pakket](http://technet.microsoft.com/library/bb693627.aspx).  

2.  Maak een **Software installeren** stap voor het implementeren van het pakket DAO.  

3.  Klik op de **Software installeren** takenreeksstap in stap 2 hebt gemaakt en klik vervolgens op de **opties** tabblad.  

4.  Klik op **voorwaarde toevoegen**, en klik vervolgens op **bestandseigenschappen**.  

5.  In de **pad** in het vak **C:\Program Files\Microsoft Shared\DAO\dao360.dll**.  

6.  Selecteer de **controleren de versie** selectievakje en klik vervolgens op **niet gelijk aan** voor de voorwaarde.  

7.  In de **versie** in het vak **3.60.6815**.  

8.  In dit geval schakelt u de **controleren de tijdstempel** selectievakje en klik vervolgens op **OK**.  

### <a name="folder-properties-in-conditions"></a>Mapeigenschappen in de voorwaarden  
 Gebruik de **mapeigenschappen** voorwaarde om te controleren of de tijdstempel van een bepaalde map om te bepalen of een taak of een groep taken uit te voeren. Bijvoorbeeld: u kunt een situatie waarin een intern ontwikkelde toepassing is bijgewerkt om te werken met Windows 8. Echter niet alle computers in het netwerk hebben dat de meest recente versie van de toepassing is geïnstalleerd en moet u een gegevens-conversie uitvoeren voordat u de toepassing een upgrade kunt uitvoeren.  

 Als de tijdstempel van de map waarin de toepassing is geïnstalleerd is 31-12-2007 of ouder, wordt de doelcomputer de incompatibele versie van de toepassing wordt uitgevoerd, en u de gegevens-conversie op de doelcomputer uitvoeren moet. Voorwaardelijk, voer een takenreeksstap voor het uitvoeren van het conversieproces op de gegevens op computers waarop een eerdere versie van de toepassing.  

 **Een voorwaarde voor de eigenschappen van mappen toevoegen aan een takenreeksstap**  

1.  In de Configuration Manager-console of in de Workbench-implementatie in de takenreekseditor bewerken ***task_sequence*** (waarbij *takenreeks* is de takenreeks die u wilt bewerken).  

2.  Maak een **opdrachtregel** taak uit te voeren van het data-conversieproces.  

3.  Klik op de taak die is gemaakt in stap 1.  

4.  Klik op **voorwaarde toevoegen**, en klik vervolgens op **mapeigenschappen**.  

5.  In de **pad** typt u het pad van de map waarin de toepassing.  

6.  Selecteer de **controleren de tijdstempel** selectievakje.  

7.  Klik op **kleiner dan of gelijk aan** voor de voorwaarde.  

8.  In de **datum** Klik **31-12-2007**.  

9. In de **tijd** Klik **12:00:00 AM**, en klik vervolgens op **OK**.  

### <a name="registry-settings-in-conditions"></a>Registerinstellingen in voorwaarden  
 Gebruik de **registerinstelling** voorwaarde om te controleren of de aanwezigheid van sleutels en waarden in het register en de bijbehorende gegevens die zijn opgeslagen in de registerwaarden. Neem bijvoorbeeld een geval waarin een toepassing momenteel wordt gebruikt op een kleine set computers kan niet worden uitgevoerd op Windows 8 en een implementatie van Windows 8 is voor het bijwerken van computers die momenteel worden uitgevoerd van Windows XP. Een voorwaarde maken voor de eerste taak in een volgorde om te controleren van het register naar een vermelding voor de niet-compatibele toepassing en het implementatieproces voor die computer onderbreken als deze is gevonden.  

 **Een registerinstelling voorwaarde toevoegen aan een takenreeksstap**  

1.  In de Configuration Manager-console of in de Workbench-implementatie in de takenreekseditor bewerken ***task_sequence*** (waarbij *takenreeks* is de takenreeks die Windows 8 implementeert).  

2.  Klik op de eerste taak in de volgorde en klik vervolgens op de **opties** tabblad.  

3.  Klik op **voorwaarde toevoegen**, en klik vervolgens op **registerinstelling**.  

4.  In de **basissleutel** lijst, klikt u op **HKEY_LOCAL_MACHINE**.  

5.  In de **sleutel** in het vak **SOFTWARE\WOODGROVE**.  

6.  Klik op **niet bestaat** voor de voorwaarde. In dit geval wordt de taak wordt uitgevoerd en de volgorde alleen worden voortgezet als de sleutel bestaat niet.  

7.  Optioneel, de voorwaarde kan controleren op om een waarde als de waardenaam is opgegeven de **waardenaam** vak.  

8.  Als een andere conditie dan **bestaat/niet bestaat** is gebruikt, Geef een waarde en een waardetype.  

9. Klik op **OK**.  

### <a name="wmi-queries-in-conditions"></a>WMI-query's in de voorwaarden  
 Gebruik de **WMI-Query** voorwaarde een WMI-query uit te voeren. De voorwaarde is geëvalueerd als waar als de query ten minste één resultaat retourneert. Denk bijvoorbeeld dat een implementatieteam moet werk het besturingssysteem van alle servers van een bepaald model: Dell 1950 voor exemplaar. Een WMI-query kunt u elke computer model controleren door te gaan met de implementatie alleen als het juiste model wordt gevonden.  

 **De voorwaarde van een WMI-Query toevoegen aan een takenreeksstap**  

1.  In de Configuration Manager-console of in de Workbench-implementatie in de takenreekseditor bewerken ***task_sequence*** (waarbij *takenreeks* is de takenreeks die de servers wordt een upgrade).  

2.  Klik op de eerste taak in de volgorde en klik vervolgens op de **opties** tabblad.  

3.  Klik op **voorwaarde toevoegen**, en klik vervolgens op **query uitvoeren op WMI**.  

4.  In de **WMI Namespace** in het vak **root\cimv2**.  

5.  In de **WQL-Query** in het vak **Selecteer \* van Win32_ComputerSystem waar Model zoals ' % Dell %% 1950% '**. Klik op **OK**.  

### <a name="installed-software-in-conditions"></a>Geïnstalleerde Software in de voorwaarden  
 Gebruik een **geïnstalleerde Software** voorwaarde waarmee wordt gecontroleerd of een bepaald onderdeel van de software die momenteel is geïnstalleerd op een doelcomputer. Alleen software worden geïnstalleerd met behulp van Microsoft Installer (MSI)-bestanden kan worden geëvalueerd met behulp van deze voorwaarde. Denk bijvoorbeeld aan dat u wilt upgraden van het besturingssysteem van alle servers met uitzondering van de Microsoft SQL Server 2012 wordt uitgevoerd.  

 **Een installatie van Software-voorwaarde toevoegen aan een takenreeksstap**  

1.  In de Configuration Manager-console of in de Workbench-implementatie in de takenreekseditor bewerken ***task_sequence*** (waarbij *takenreeks* is de takenreeks die de servers wordt een upgrade).  

2.  Klik op de eerste taak in de volgorde en klik vervolgens op de **opties** tabblad.  

3.  Klik op **voorwaarde toevoegen**, en klik vervolgens op **geïnstalleerde Software**.  

4.  Klik op **Bladeren**, en klik vervolgens op het MSI-bestand voor SQL Server 2012.  

5.  Selecteer de **overeenkomt met dit specifieke product** selectievakje in om op te geven dat alleen computers met SQL Server 2012 en geen andere versies de doelcomputers moet bij het detecteren van deze query zijn.  

6.  Klik op **OK**.  

### <a name="complex-conditions"></a>Complexe voorwaarden  
 Meerdere voorwaarden kunnen worden gegroepeerd met **als** instructies complexe voorwaarden maken. Denk bijvoorbeeld aan een bepaalde stap kan alleen worden uitgevoerd voor Contoso 1950 computers met Windows Server 2003 of Windows Server 2008. Geschreven als een programmatische **als** instructie, zou deze er ongeveer als het volgende:  

```  
IF ((Computer Model IS “Contoso 1950”) AND (operating system=2003 OR operating system=2008))  
```  

 **Een complexe voorwaarde toevoegen**  

1.  In de Configuration Manager-console of in de Workbench-implementatie in de takenreekseditor bewerken ***task_sequence*** (waarbij *takenreeks* is de takenreeks die de servers wordt een upgrade).  

2.  Klik op de takenreeksstap waarop de voorwaarde toevoegen en klik vervolgens op de **opties** tabblad.  

3.  Klik op **voorwaarde toevoegen**, klikt u op **If-instructie**, en klik vervolgens op **alle voorwaarden**. Klik op **OK**.  

4.  Klik op de voorwaardeninstructie, **voorwaarde toevoegen**, en klik vervolgens op **WMI-Query**.  

5.  Zorg ervoor dat **root\cimv2** is opgegeven als de WMI-naamruimte en klikt u op de **WQL-Query** in het vak **Selecteer \* van Win32_ComputerSystem waar ComputerModel zoals 'Contoso % 1950% '**. Klik op **OK**.  

6.  Klik op de **als** -instructie en klik vervolgens op **voorwaarde toevoegen**. Klik op **als instructie**, en klik vervolgens op **elke voorwaarde**. Klik op **OK**.  

7.  Klik op de tweede **als** instructie. Klik op **voorwaarde toevoegen**, en klik vervolgens op **besturingssysteemversie**.  

8.  In de **architectuur** vak, klikt u op de architectuur voor de servers. Klik op voor dit voorbeeld **x86**.  

9. In de **besturingssysteem** vak, klikt u op het besturingssysteem en versie. Klik op voor dit voorbeeld **x86 Windows 2003 oorspronkelijke versie**. Klik op **OK**.  

10. Klik op de tweede **als** instructie. Klik op **voorwaarde toevoegen**, en klik vervolgens op **besturingssysteemversie**.  

11. In de **architectuur** vak, klikt u op de architectuur voor de servers. Klik op voor dit voorbeeld **x86**.  

12. In de **besturingssysteem** vak, klikt u op het besturingssysteem en versie. Klik op voor dit voorbeeld **x86 Windows 2008 oorspronkelijke versie**. Klik op **OK**.  

## <a name="creating-a-highly-scalable-lti-deployment-infrastructure"></a>Maken van een uiterst schaalbare LTI implementatie-infrastructuur  
 In dit scenario is geen elektronische softwaredistributie beschikbaar voor de implementatie-infrastructuur gebruiken, zodat u MDT gebruiken voor het bouwen van een volledig geautomatiseerde LTI implementatie-infrastructuur. De schaalbare infrastructuur van de LTI maakt gebruik van SQL Server, Windows Deployment Services en Windows Server 2003 Distributed File System Replication (DFS-R)-technologieën.  

 De infrastructuur LTI door schalen:  

-   Waarborgen dat de juiste infrastructuur bestaat, zoals beschreven in [zorgt u ervoor dat de juiste infrastructuur aanwezig](#EnsureInfrastructure)  

-   Inhoud toevoegen aan MDT, zoals beschreven in [toe te voegen inhoud naar MDT](#AddContent)  

-   Voorbereiden van Windows Deployment Services, zoals beschreven in [voorbereiden van Windows Deployment Services](#PrepareDeployment)  

-   DFS-R configureren zoals beschreven in [configureren Distributed File System Replication](#ConfigureFileReplication)  

-   Voorbereiden voor SQL Server-replicatie, zoals beschreven in [voorbereiden voor SQL Server-replicatie](#PrepareSQLReplication)  

-   SQL Server-replicatie configureren zoals beschreven in [SQL Server-replicatie configureren](#ConfigureSQLReplication)  

 Dit scenario wordt ervan uitgegaan dat MDT is geconfigureerd op een master deployment server en dat de configuratie van de MDT-database is al voltooid zoals beschreven aan het begin van dit document.  

###  <a name="EnsureInfrastructure"></a> Bevestigen dat de juiste infrastructuur bestaat  
 De uiterst schaalbare infrastructuur van de LTI-implementatie maakt gebruik van een hub en spoke-topologie voor replicatie van de inhoud; Daarom wijst eerst een implementatieserver in de productieomgeving die door de rol van de master deployment server worden uitgevoerd.  Hieronder vindt u de vereiste onderdelen voor de van de master-implementatieserver.  

 |**Vereiste component** |**Doel/Opmerking** |  
 |-|-|  
 |Windows Server 2003 R2|Vereist ter ondersteuning van DFS-R|  
 |MDT |Bevat het originele exemplaar van de implementatieshare|  
 |SQL Server 2005|Moet een volledige versie zodat de replicatie van de MDT-DB|  
 |DFS-R |Vereist voor de replicatie van de implementatieshare|  
 |Windows Deployment Services |Vereist voor PXE gebaseerde netwerkinstallaties tot stand wordt gebracht|  

 Wanneer u de van de master-implementatieserver hebt geselecteerd, moet u extra servers op elke site ter ondersteuning van implementaties van LTI inrichten.  Hieronder vindt u de vereiste onderdelen voor de onderliggende implementatie-server.  

 |**Vereiste component** |**Doel/Opmerking** |  
 |-|-|  
 |Windows Server 2003 R2|Vereist ter ondersteuning van DFS-R|  
 |Microsoft SQL Server 2005 Express Edition |Ontvangt gerepliceerde kopieën van de MDT-DB|  
 |DFS-R |Vereist voor de replicatie van de implementatieshare|  
 |Windows Deployment Services |Vereist voor PXE gebaseerde netwerkinstallaties tot stand wordt gebracht|  

> [!NOTE]
>  Windows Deployment Services moet worden ingesteld en geconfigureerd op elke server onderliggende, maar het is niet nodig opstart- of installatiekopieën toe te voegen.  

###  <a name="AddContent"></a> Inhoud toevoegen aan MDT  
 De master deployment server in te vullen met inhoud met behulp van de implementatie-Workbench en maken en vullen van de MDT-database, zoals beschreven in de volgende secties. Voor informatie over het vullen van de database met:  

-   Toepassingen, Zie de sectie 'Configureren van toepassingen in de implementatie-Workbench', in het document MDT *met behulp van de Microsoft Deployment Toolkit*  

-   Besturingssystemen, Zie de sectie 'Configureren van besturingssystemen in de implementatie-Workbench', in het document MDT *met behulp van de Microsoft Deployment Toolkit*  

-   Besturingssysteem-pakketten, Zie de sectie 'Configureren van pakketten in de implementatie-Workbench', in het document MDT *met behulp van de Microsoft Deployment Toolkit*  

-   Stuurprogramma's, Zie de sectie 'Configureren apparaat stuurprogramma's in de implementatie-Workbench', in het document MDT *met behulp van de Microsoft Deployment Toolkit*  

-   Takenreeksen, Zie de sectie 'Configureren Taakreeksen in de implementatie-Workbench', in het document MDT *met behulp van de Microsoft Deployment Toolkit*  

> [!NOTE]
>  Zorg ervoor dat het LiteTouchPE_x86.wim-bestand gemaakt wanneer de implementatieshare is bijgewerkt is toegevoegd aan Windows Deployment Services.  

###  <a name="PrepareDeployment"></a> Voorbereiden van Windows Deployment Services  
 Omdat het bestand LiteTouchPE_x86.wim wordt periodiek door de DFS-R-replicatiegroep zijn gerepliceerd, moet de boot configuration data store regelmatig worden bijgewerkt naar aanleiding van de zojuist gerepliceerde Windows PE-omgeving. De volgende stappen uitvoeren op elk van de implementatie-servers.  

 **Voorbereiden van Windows Deployment Services**  

1.  Open een opdrachtpromptvenster.  

2.  Type **WDSUtil/set-server/BCDRefreshPolicy/Enabled: yes / RefreshPeriod:60**, en druk op ENTER.  

> [!NOTE]
>  In het voorbeeld dat hier wordt gepresenteerd, is het vernieuwingsinterval ingesteld op 60 minuten. u kunt deze waarde om te repliceren gedurende een periode die gelijk zijn aan die van de DFS-r echter kan configureren  

###  <a name="ConfigureFileReplication"></a> Configureren van Distributed File System Replication  
 Tijdens het schalen van de architectuur van de LTI-implementatie, gebruikt u DFS-R als basis voor het repliceren van de inhoud van de MDT-implementatieshare en de Windows PE Lite-Touch opstartomgeving en van de van basispagina-implementatieserver naar de onderliggende implementatie-servers.  

> [!NOTE]
>  Zorg ervoor dat DFS-R is geïnstalleerd voordat u de volgende stappen uitvoert.  

 **DFS-R om te repliceren van de implementatie-inhoud configureren**  

1.  Open DFS-beheer-console.  

2.  Vouw in de console van DFS-beheer DFS-beheer.  

3.  Met de rechtermuisknop op **replicatie**, en klik vervolgens op **nieuwe replicatiegroep**.  

4.  In de Wizard Nieuwe replicatiegroep, op de **replicatie groepstype** pagina, klikt u op **nieuwe Multipurpose replicatiegroep**.  

5.  Klik op **Volgende**.  

6.  Op de **naam en het domein** pagina, typt u de volgende informatie:  

    -   In de **naam voor de replicatiegroep** typt u een naam voor de replicatiegroep — bijvoorbeeld **MDT 2010 replicatiegroep**.  

    -   In de **desgewenst een beschrijving van de replicatiegroep** typt u een beschrijving van de replicatiegroep — bijvoorbeeld **groep voor replicatie van gegevens van de MDT 2010**.  

    -   Zorg ervoor dat de **domein** vak bevat de naam van het juiste domein.  

7.  Klik op **Volgende**.  

8.  Op de **leden replicatiegroep** pagina, voert u deze stappen:  

    1.  Klik op **Toevoegen**.  

    2.  Typ de namen van alle servers die moeten worden leden van deze replicatiegroep — bijvoorbeeld alle onderliggende implementatie-servers en de van de master-implementatieserver.  

    3.  Klik op **OK**.  

9. Klik op **Volgende**.  

10. Op de **topologie selectie** pagina, klikt u op **Hub en Spoke**, en klik vervolgens op **volgende**.  

11. Op de **hubleden** pagina, klikt u op de master deployment server en klik vervolgens op **toevoegen**.  

12. Klik op **Volgende**.  

13. Op de **Hub en spaak verbindingen** pagina, zorg ervoor dat voor elke onderliggende implementatieserver de master implementatieserver vermeld de **vereist hublid**.  

14. Klik op **Volgende**.  

15. Op de **schema voor replicatiegroep en bandbreedte** pagina, geeft u een planning voor het repliceren van de inhoud tussen servers.  

16. Klik op **Volgende**.  

17. Op de **primaire lid** pagina in de **primaire lid** vak, klikt u op de master implementatieserver.  

18. Klik op **Volgende**.  

19. Op de **mappen die u wilt repliceren** pagina, klikt u op **toevoegen**, en voer deze stappen uit:  

    1.  In de **lokale pad van de map voor replicatie van** Klik **Bladeren** naar de *X:\\*Implementatiemap (waarbij *X* is de stationsletter op de server implementeren).  

    2.  Klik op **gebruik de naam op basis van pad**.  

    3.  Klik op **OK**.  

    4.  Klik op **Toevoegen**.  

    5.  In de **map toevoegen repliceren** in het dialoogvenster, klikt u op **Bladeren** naar de *X:*\RemoteInstall\Boot map.  

    6.  Klik op **gebruik de naam op basis van pad**.  

20. Klik op **Volgende**.  

21. Op de **lokale pad van de distributiepunten op andere leden** pagina, voert u deze stappen:  

    1.  Selecteer alle leden in de distributiegroep, en klik vervolgens op **bewerken**.  

    2.  In de **lokaal pad bewerken** in het dialoogvenster, klikt u op **ingeschakeld**.  

    3.  Typ het pad waar de Implementatieshare-map op de onderliggende implementatie-server moet worden opgeslagen, bijvoorbeeld ***X:\Deployment*** (waarbij *X* de stationsletter op de implementatieserver).  

    4.  Klik op **OK**.  

22. Klik op **Volgende**.  

23. Op de **lokale pad van de opstartinstallatiekopie op andere leden** pagina, voert u deze stappen:  

    1.  Selecteer alle leden in de distributiegroep, en klik vervolgens op **bewerken**.  

    2.  In de **lokaal pad bewerken** in het dialoogvenster, klikt u op **ingeschakeld**.  

    3.  Typ het pad waar de opstartmap moet worden opgeslagen op de onderliggende implementatie-server, bijvoorbeeld ***X:\RemoteInstall\Boot*** (waarbij *X* de stationsletter op de implementatieserver).  

    4.  Klik op **OK**.  

24. Klik op **Volgende**.  

25. Op de **instellingen voor externe verbindingen en replicatiegroep maken** pagina, klikt u op **maken** voltooid de Wizard Nieuwe replicatiegroep.  

26. Op de **bevestiging** pagina, klikt u op **sluiten** om de wizard te sluiten.  

> [!NOTE]
>  Zorg ervoor dat de nieuwe replicatiegroep wordt nu weergegeven onder het knooppunt replicatie.  

###  <a name="PrepareSQLReplication"></a> Voorbereiden voor SQL Server-replicatie  
 Voordat u SQL Server-replicatie kan worden geconfigureerd, voltooid verschillende vooraf configuratiestappen om ervoor te zorgen dat de gebruikte servers correct zijn geconfigureerd.  

 **Voorbereiden voor SQL Server-replicatie op de implementatieserver van basispagina**  

1.  Maak een map voor het opslaan van de momentopnamen van databases en configureer vervolgens de map als share.  

    > [!NOTE]
    >  Zie voor meer informatie over het beveiligen van de snapshotmap [beveiliging van de Snapshotmap](http://msdn2.microsoft.com/library/ms151151.aspx).  

2.  Zorg ervoor dat de SQL Server Browser-service is ingeschakeld en ingesteld op automatisch.  

3.  In de **SQL Server Surface Area Configuration** Klik **lokale en externe verbindingen**.  

 **SQL Server-replicatie op de onderliggende implementatie-server voorbereiden**  

1.  In de **SQL Server Surface Area Configuration** Klik **lokale en externe verbindingen**.  

2.  Maak eventueel een lege database voor het hosten van de gerepliceerde MDT-DB.  

> [!NOTE]
>  Deze database moet dezelfde naam als de MDT-DB worden verleend voor de master implementatieserver. Bijvoorbeeld, als de MDT-database op de master deployment server heet *MDTDB*, maakt u een lege database aangeroepen *MDTDB* op de onderliggende implementatie-server.  

###  <a name="ConfigureSQLReplication"></a> SQL Server-replicatie configureren  
 Na het configureren van de replicatie van bestanden en mappen die zijn vereist voor het bouwen van de implementatie-infrastructuur, SQL Server om te repliceren van de MDT-database te configureren.  

> [!NOTE]
>  Het is ook mogelijk, zodat alleen een één centrale MDT DB. door het onderhouden van een gerepliceerde versie van de MDT-DB kan meer controle worden beheerd via gegevens overbrengen via het wide area network (WAN).  

 SQL Server 2005 maakt gebruik van een replicatiegroep die vergelijkbaar is met een distributiemodel magazine:  

1.  Een *magazine* beschikbaar wordt gesteld (gepubliceerd) door een *publisher*.  

2.  *Distributeurs* worden gebruikt voor het distribueren van de publicatie.  

3.  *Lezers* kunnen zich abonneren op een publicatie, zodat de publicatie is geleverd op de abonnee regelmatig (een *push-abonnement*).  

 Deze terminologie wordt gebruikt door de SQL Server-replicatie-installatie en configuratie-wizards.  

#### <a name="configure-a-sql-server-publisher"></a>Een SQL Server-Publisher configureren  
 Als u wilt de master deployment server configureren als een SQL Server-publisher, kunt u deze stappen uitvoeren:  

1.  Open SQL Server Management Studio.  

2.  Met de rechtermuisknop op de **replicatie** knooppunt en klik vervolgens op **distributiepunt configureren**.  

3.  Klik in de Wizard distributiepunten configureren op **volgende**.  

4.  Op de **Distributor** pagina, klikt u op **zal fungeren als een eigen Distributor; SQL Server maakt een distributiedatabase en logboekbestanden**, en klik vervolgens op **volgende**.  

5.  Op de **Snapshotmap** pagina in de **voorbereiden voor SQL Server-replicatie** sectie, typt u het UNC-pad naar de momentopnamemap is gemaakt.  

6.  Op de **distributiedatabase** pagina, klikt u op **volgende**.  

7.  Op de **uitgevers** pagina, klikt u op de master deployment server instellen als de distributor en klikt u op **volgende**.  

8.  Op de **Wizardacties** pagina, klikt u op **distributiepunt configureren**, en klik vervolgens op **volgende**.  

9. Klik op **voltooien**, en klik vervolgens op **sluiten** wanneer de wizard is voltooid.  

#### <a name="enable-the-mdt-db-for-replication"></a>De MDT-database voor replicatie inschakelen  
 Als u wilt inschakelen voor replicatie op de master deployment server waarnaar de MDT-database, moet u deze stappen uitvoeren:  

1.  SQL Server Management Studio, met de rechtermuisknop op de **replicatie** knooppunt en klik vervolgens op **eigenschappen van de publicatieserver**.  

2.  Op de **eigenschappen van de publicatieserver** pagina, voert u deze stappen:  

    1.  Klik op **Publisher Databases**.  

    2.  Klik op de MDT-database en klik vervolgens op **transactioneel**.  

    3.  Klik op **OK**.  

 De MDT-database is nu geconfigureerd voor transactionele en momentopname replicatie.  

#### <a name="create-a-publication-of-the-mdt-db"></a>Een publicatie van de MDT-database maken  
 Voer deze stappen voor het maken van een publicatie van de MDT-database waarnaar de onderliggende implementatie-servers kunnen zich abonneren:  

1.  Vouw in SQL Server Management Studio replicatie, met de rechtermuisknop op **lokale publicaties**, en klik vervolgens op **nieuwe publicatie**.  

2.  Klik in de Wizard Nieuwe publicatie **volgende**.  

3.  Op de **publicatiedatabase** pagina, klikt u op de MDT-database en klik vervolgens op **volgende**.  

4.  Op de **publicatietype** pagina, klikt u op **momentopnamepublicatie**, en klik vervolgens op **volgende**.  

5.  Op de **artikelen** pagina, selecteert u alle **tabellen, opgeslagen Procedures**, en **weergaven**, en klik vervolgens op **volgende**.  

6.  Op de **artikelen problemen** pagina, klikt u op **volgende**.  

7.  Op de **Filter tabelrijen** pagina, klikt u op **volgende**.  

8.  Op de **Snapshot Agent** pagina, voert u deze stappen:  

    1.  Selecteer **onmiddellijk een momentopname maken en het behouden van de momentopname beschikbaar om abonnementen te initialiseren**.  

    2.  Klik op **plannen Snapshot Agent worden uitgevoerd op de volgende tijden**.  

    3.  Klik op **Wijzigen**.  

    > [!NOTE]
    >  Geef een planning die zich één uur voordoen voordat de database repliceert.  

9. Klik op **Volgende**.  

10. Op de **Agent Security** pagina, klikt u op het account waaronder de snapshot agent uitvoeren en klik vervolgens op **volgende**.  

11. Op de **Wizardacties** pagina, klikt u op **maken van de publicatie**, en klik vervolgens op **volgende**.  

12. Op de **Voltooi de Wizard** pagina in de **publicatienaam** Typ een beschrijvende publicatienaam.  

13. Klik op **voltooien** Voltooi de wizard en klik vervolgens op **sluiten** wanneer de wizard de publicatie is gemaakt.  

    > [!NOTE]
    >  De publicatie worden nu weergegeven onder het knooppunt lokale publicaties in SQL Server Management Studio.  

#### <a name="subscribe-child-deployment-servers-to-the-published-mdt-db"></a>Abonneren onderliggende implementatie-Servers aan de gepubliceerde MDT-DB  
 Nu dat de MDT-database is gepubliceerd, kunt u de onderliggende implementatie-servers toevoegen als abonnees aan deze publicatie. dat wil zeggen dat ze een kopie van de database op een schema ontvangt dat tijdens de implementatie van een query de clientcomputers een database die is lokaal op het netwerk in plaats van te gaan via het WAN.  

 **Voor een abonnement van de onderliggende implementatie-servers op de publicatie van de MDT-DB**  

1.  Ga naar replicatie/lokaal publicaties in SQL Server Management Studio.  

2.  Met de rechtermuisknop op de publicatie in de vorige sectie hebt gemaakt en klik vervolgens op **nieuwe abonnementen**.  

3.  Klik in de Wizard Nieuwe abonnementen op **volgende**.  

4.  Op de **publicatie** pagina, klikt u op de publicatie in de vorige sectie hebt gemaakt.  

5.  Op de **locatie distributieagent** pagina, klikt u op **alle agents worden uitgevoerd op de Distributor SERVERNAME (push-abonnementen)**, en klik vervolgens op **volgende**.  

6.  Op de **abonnees** pagina, voegt u elk van de onderliggende implementatie-servers door de volgende stappen uit te voeren:  

    1.  Klik op **abonnee toevoegen**, en klik vervolgens op **SQL Server-abonnee toevoegen**.  

    2.  Elke onderliggende implementatie-server toevoegen.  

    3.  Voor elke onderliggende implementatie-server toegevoegd in de **abonneedatabase** vak, klikt u op de lege MDT-database op die onderliggende implementatie-server.  

    > [!NOTE]
    >  Als de lege MDT-database nog niet is gemaakt, in de **abonneedatabase** Selecteer de optie voor het maken van een nieuwe database.  

    > [!NOTE]
    >  Deze database moet dezelfde naam als de MDT-DB worden verleend voor de master implementatieserver. Bijvoorbeeld, als de MDT-database op de master deployment server heet *MDTDB*, maakt u een lege database aangeroepen *MDTDB* op de onderliggende implementatie-server.  

7.  Klik op **Volgende**.  

8.  Op de **Distribution Agent Security** pagina, klikt u op **...** openen van de **Distribution Agent Security** in het dialoogvenster.  

9. Typ de details van het account gebruiken voor de agent voor softwaredistributie en klik vervolgens op **volgende**.  

10. Op de **Synchronisatieplanning** pagina, voert u deze stappen:  

    1.  In de **schema van Agent** Klik **< schema definiëren\>**.  

    2.  Geef de planning die moet worden gebruikt voor de database repliceren tussen hoofd- en onderliggende implementatie-servers en klik vervolgens op **volgende**.  

11. Op de **geïnitialiseerd abonnement** pagina, klikt u op **volgende**.  

12. Op de **Wizardacties** pagina, klikt u op **maken van de abonnementen**, en klik vervolgens op **volgende**.  

13. Klik op **voltooien**, en klik vervolgens op **sluiten** wanneer de wizard is voltooid.  

 SQL Server-replicatie is nu geconfigureerd en de MDT-database van de van de master-implementatieserver wordt gerepliceerd naar alle onderliggende implementatie-servers die bent geabonneerd op het periodiek.  

#### <a name="configure-customsettingsini"></a>CustomSettings.ini configureren  
 De LTI implementatie-infrastructuur is nu gemaakt en elke locatie een implementatieserver LTI met een gerepliceerde exemplaar van bevat:  

-   De implementatieshare  

-   De MDT-DB  

-   De LiteTouchPE_x86 Windows PE-omgeving die is toegevoegd aan Windows Deployment Services  

 Nu kunt u het CustomSettings.ini-bestand voor gebruik van de implementatie-inhoud (implementatieshare en database) van de server lokaal te implementeren, de server die de omgeving LiteTouchPE_x86.wim via Windows-implementatie biedt de share van de implementatie configureren Services.  

 Als het bestand LiteTouchPE_x86.wim wordt afgeleverd van Windows Deployment Services, wordt een registersleutel is geconfigureerd met de naam van de Windows Deployment Services-server die u gebruikt. MDT bevat de naam van deze server in een variabele die u gebruiken kunt voor het configureren van CustomSettings.ini (% WDSServer %).  

 **Gebruik altijd de lokale server van de LTI-implementatie**  

> [!NOTE]
>  De volgende procedure wordt ervan uitgegaan dat de implementatieshare is gemaakt en ingesteld als de implementatie$-share.  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  Klik op de **regels** tabblad en wijzigt u het CustomSettings.ini-bestand voor het configureren van de volgende eigenschappen:  

    -   Configureren voor elke sectie SQL Server is toegevoegd, **SQLServer** gebruik van de servernaam **% WDSServer % —**bijvoorbeeld **SQLServer = % WDSServer %**.  

    -   Als u configureert **DeployRoot**, configureren **DeployRoot** gebruiken de **% WDSServer %** variabele — bijvoorbeeld **DeployRoot =\\ \\%WDSServer%\Deployment$**.  

5.  Klik op **Bootstrap.ini bewerken**.  

6.  Configureer BootStrap.ini te gebruiken de **% WDSServer %** eigenschap toe te voegen of te wijzigen van de **DeployRoot** van waarde naar **DeployRoot =\\\\%WDSServer%\Deployment$** .  

7.  Klik op **bestand**, en klik vervolgens op **opslaan** de wijzigingen wilt opslaan naar het bestand BootStrap.ini.  

8.  Klik op **OK**.  

     De implementatieshare en LiteTouchPE_x86.wim Windows PE-omgeving moeten worden bijgewerkt.  

9. Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

10. Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

11. Op de **samenvatting** pagina, controleert u of de gegevens juist zijn en klik vervolgens op **volgende**.  

12. Op de **bevestiging** pagina, klikt u op **voltooien**.  

 Het volgende voorbeeld illustreert CustomSettings.ini na het uitvoeren van de stappen in deze sectie wordt beschreven.  

 **Voorbeeld CustomSettings.ini geconfigureerd voor schaalbare LTI implementatie-infrastructuur**  

```  
[Settings]  
Priority=CSettings,CPackages, CApps, CAdmins, CRoles, Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac  

[CSettings]  
SQLServer=%WDSServer%  
Instance=  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerSettings  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  

[CPackages]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerPackages  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
Order=Sequence  

[CApps]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerApplications  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
Order=Sequence  

[CAdmins]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerAdministrators  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  

[CRoles]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerRoles  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
```  

## <a name="selecting-a-local-mdt-server-when-multiple-servers-exist"></a>Een lokale MDT-Server te selecteren wanneer er meerdere Servers bestaan  
 In dit scenario worden meerdere MDT-servers gebruikt ter ondersteuning van een groot aantal gelijktijdige implementaties en implementaties op meerdere sites. Wanneer een implementatie van de LTI wordt geïnitialiseerd, is het standaardgedrag voor het aanvragen van een pad naar de MDT-server verbinding maken met en toegang tot de benodigde bestanden om te beginnen met de implementatie.  

 De Wizard Windows-implementatie kunt het bestand LocalServer.xml gebruiken om een keuze van de implementatie van de bekende servers voor elke locatie.  

 Gebruik het bestand LocationServer.xml door:  

-   Informatie over het doel en gebruik van LocationServer.xml zoals beschreven in [Understanding LocationServer.xml](#UnderstandingLocationServer)  

-   Maken van het bestand LocationServer.xml zoals beschreven in [maken van het bestand LocationServer.xml](#CreateLocationServer)  

-   Het bestand LocationServer.xml toe te voegen aan de map met Extra bestanden zoals beschreven in het bestand LocationServer.xml toe te voegen aan de map met Extra bestanden  

-   Bijwerken van het bestand BootStrap.ini zoals beschreven in [bijwerken van het bestand BootStrap.ini](#UpdateBootstrap)  

-   Bijwerken van de implementatieshare, zoals beschreven in [de Implementatieshare bijwerken](#UpdateDeploymentShare)  

 Dit scenario veronderstelt dat MDT is geconfigureerd op de implementatieserver van een.  

###  <a name="UnderstandingLocationServer"></a> Understanding LocationServer.xml  
 Eerst moet u begrijpen dat hoe MDT LocationServer.xml gebruikt. Tijdens de LTI, MDT scripts lezen en te verwerken van het bestand BootStrap.ini om initiële informatie over de implementatie te verzamelen. Dit gebeurt voordat een verbinding is gemaakt met de implementatieserver. Daarom de **DeployRoot** eigenschap wordt meestal gebruikt om op te geven in het bestand BootStrap.ini de implementatieserver waarmee deze verbinding moet maken.  

 Als het bestand BootStrap.ini geen bevat een **DeployRoot** eigenschap MDT scripts laden van een pagina van de wizard om de gebruiker gevraagd om een pad naar de implementatieserver. Tijdens het initialiseren van de **HTML-toepassing (HTA)** wizardpagina MDT scripts controleren op het bestaan van het bestand LocationServer.xml en, indien aanwezig, LocationServer.xml gebruiken om de implementatie van de beschikbare servers weer te geven.  

#### <a name="understand-when-to-use-locationserverxml"></a>Begrijpen wanneer u LocationServer.xml  
 MDT biedt verschillende manieren om te bepalen welke server verbinding maakt met tijdens de implementatie van een LTI. Verschillende methoden voor het zoeken naar de implementatieserver zijn geschikt voor verschillende scenario's; Daarom is het belangrijk om te begrijpen wanneer u LocationServer.xml.  

 MDT biedt verschillende methoden voor het automatisch detecteren en gebruiken van de meest geschikte implementatieserver. Deze methoden worden vermeld in de volgende tabel.

 |**Methode** |**Details** |  
 |-|-|  
 |**%WDSServer%** |Deze methode wordt gebruikt wanneer de MDT-server naast elkaar op de Windows Deployment Services-server wordt gehost.<br /><br /> Wanneer een implementatie van de LTI wordt gestart vanuit Windows Deployment Services, een omgevingsvariabele: % WDSServer % — wordt gemaakt en gevuld met de naam van de Windows Deployment Services-server.<br /><br /> De **DeployRoot** variabele kunt deze variabele gebruiken om automatisch te verbinden met een implementatieshare op de Windows Deployment Services-server, bijvoorbeeld:<br /><br /> **DeployRoot=\\\\%WDSServer%\Deployment$** |  
 |**Op basis van locatie automation** |MDT kunt automatisering op basis van locatie in het bestand BootStrap.ini gebruiken om te bepalen van de server waarop deze moet implementeren.<br /><br /> Gebruik de **standaardgateway** eigenschap onderscheid maken tussen verschillende locaties; voor elk **standaardgateway**, een andere MDT-server is opgegeven.<br /><br /> Raadpleeg voor meer informatie over het gebruik van automatisering op basis van locatie 'Selecteren van de methoden voor toepassen van configuratie-instellingen'.|  

 Elke benadering vermeld in de voorgaande tabel biedt een manier om de selectie van de deployment server op een bepaalde locatie voor bepaalde scenario's te automatiseren. Deze methoden zijn gericht op specifieke scenario's, bijvoorbeeld wanneer de MDT-server is CO gehoste met Windows Deployment Services.  

 Er zijn andere scenario's waarin deze methoden niet geschikt zijn — bijvoorbeeld, als er meerdere servers voor implementatie op een opgegeven locatie of de automation-logica is niet mogelijk (bijvoorbeeld, het netwerk is niet onderverdeeld voldoende is voor de bepaling van de locatie of de MDT-server is gescheiden van Windows Deployment Services).  

 In deze scenario's biedt het bestand LocationServer.xml een flexibele manier om deze informatie tijdens de implementatie zonder kennis van de servernamen van de en deployment share.  

###  <a name="CreateLocationServer"></a> Maken van het bestand LocationServer.xml  
 Als u wilt een lijst met beschikbare implementatie servers aanwezig tijdens de implementatie van een LTI, een LocationServer.xml-bestand met informatie over elke server te maken. Er is geen standaard LocationServer.xml-bestand in MDT, dus maak een met de volgende richtlijnen.  

#### <a name="create-a-locationserverxml-file-to-support-multiple-locations"></a>Maak een bestand LocationServer.xml ter ondersteuning van meerdere locaties  
 De eenvoudigste methode voor maken en gebruiken van LocationServer.xml is het maken van een bestand LocationServer.xml en vermeldingen voor elke implementatieserver toevoegen in de omgeving (dit kan zijn op dezelfde locatie of op verschillende locaties).  

 Het bestand LocationServer.xml maken door het maken van een nieuwe sectie voor elke server en vervolgens toe te voegen van de volgende informatie:  

-   Een unieke id  

-   De locatienaam van een, gebruikt om de naam van een gemakkelijk te identificeren voor die locatie  

-   Een UNC-pad naar de MDT-server voor die locatie  

 Het volgende ziet u hoe het bestand LocationServer.xml wordt gemaakt met behulp van elk van deze eigenschappen met behulp van een voorbeeldbestand LocationServer.xml geconfigureerd voor meerdere locaties.  

 **Voorbeeld van een bestand LocationServer.xml ter ondersteuning van meerdere locaties**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS01\Deployment$</UNCPath>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso NYC, New York, USA  
        </friendlyname>  
        <UNCPath>\\NYCDS01\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

 Met deze indeling, geef andere server adressen voor elke locatie of voor situaties waarin er meerdere servers binnen één locatie zijn door te geven van een andere server-vermelding voor elke server op die locatie, zoals weergegeven in het volgende voorbeeld.   

 **Voorbeeld van een bestand LocationServer.xml ter ondersteuning van meerdere Servers op meerdere locaties**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ DS1, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS01\Deployment$</UNCPath>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso HQ DS2, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS02\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

#### <a name="create-a-locationserverxml-file-to-load-balance-multiple-servers-at-different-locations"></a>Een bestand LocationServer.xml om taken te verdelen van meerdere Servers op verschillende locaties maken  
 LocationServer.xml Geef meerdere servers per locatievermelding en voert u taakverdeling basic zodat als een locatie hebt gekozen, MDT deployment-server automatisch geselecteerd in de lijst met beschikbare servers. Deze functionaliteit bieden, het bestand LocationServer.xml ondersteunt een metriek weging opgeven.  

 Het volgende voorbeeld illustreert een voorbeeldbestand LocationServer.xml geconfigureerd voor meerdere servers op verschillende locaties.  

 **Voorbeeld LocationServer.xml-bestand voor verschillende locaties**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ, Seattle, USA  
        </friendlyname>  
        <Server1>\\STLDS01\Deployment$</Server1>  
        <Server2>\\STLDS02\Deployment$</Server2>  
        <Server3>\\STLDS03\Deployment$</Server3>  
        <Server weight=”1”>\\STLDS01\Deployment$</Server>  
        <Server weight=”2”>\\STLDS02\Deployment$</Server>  
        <Server weight=”4”>\\STLDS03\Deployment$</Server>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso NYC, New York, USA  
        </friendlyname>  
        <UNCPath>\\NYCDS01\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

 De metriek weging opgeven met behulp van de < server gewicht\> tag, die MDT wordt gebruikt in het proces voor de selectie van servers. De kans op een server die wordt geselecteerd, wordt berekend door:  

 **Server gewicht/som van alle server-gewicht**  

 In het vorige voorbeeld worden de drie servers op het hoofdkantoor Contoso vermeld als 1, 2 en 4. De kans op een server met een gewicht van 2 wordt geselecteerd, wordt 2 in 7. Daarom voor het gebruik van het wegingssysteem bepaalt de capaciteit van de servers die beschikbaar zijn op een locatie en het gewicht van elke server door de servercapaciteit ten opzichte van elk van de andere servers.  

### <a name="adding-the-locationserverxml-file-to-the-extra-files-directory"></a>Het bestand LocationServer.xml toe te voegen aan de map met Extra bestanden  
 Nadat u het bestand LocationServer.xml hebt gemaakt, deze toevoegen aan de LiteTouch_x86 en LiteTouch_x64 Windows PE-opstartinstallatiekopieën in de ***X:\\Deploy\Control map***. Met behulp van de implementatie-Workbench, andere bestanden en mappen toevoegen aan deze Windows PE-installatiekopieën door te geven van een extra map toevoegen in de eigenschappen van implementatieshare.  

 **LocationServer.xml toevoegen aan de implementatieshare**  

1.  Maak een map *Extra bestanden* in de hoofdmap deployment share bevindt (bijvoorbeeld D:\Production implementatie Share\Extra-bestanden).  

2.  Maak een mapstructuur in de map Extra bestanden die overeenkomt met de Windows PE-locatie waar het aanvullende bestand moet zich bevinden.  

     Bijvoorbeeld: het bestand LocationServer.xml moet zich bevinden in de map \Deploy\Control in Windows PE; Daarom maakt dezelfde mapstructuur onder Extra bestanden (bijvoorbeeld D:\Production implementatie Share\Extra Files\Deploy\Control).  

3.  Kopieer LocationServer.xml naar de *deployment_share*\Extra Files\Deploy\Control map (waarbij *deployment_share* is het volledig gekwalificeerde pad naar de hoofdmap van de implementatieshare).  

4.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

5.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

6.  Klik in het deelvenster Acties op **eigenschappen**.  

7.  In de ***deployment_shareProperties*** in het dialoogvenster (deployment_share is waar de naam van de implementatieshare) deze stappen uitvoeren:  

    1.  Klik op de **Windows PE-platform instellingen** tabblad (waarbij *platform* is de architectuur van de Windows PE-installatiekopie worden geconfigureerd).  

    2.  In de **aanpassingen van Windows PE** sectie in de **Extra map toevoegen** in het vak ***pad*** (waar *pad* is volledig gekwalificeerd pad naar de map Extra bestanden, bijvoorbeeld D:\Production implementatie Share\Extra bestanden), en klik vervolgens op **OK**.  

###  <a name="UpdateBootstrap"></a> Het bestand BootStrap.ini bijwerken  
 Wanneer u een share met behulp van de implementatie-Workbench-implementatie maakt een **DeployRoot** eigenschap automatisch wordt gemaakt en ingevuld in het bestand BootStrap.ini. Omdat het bestand LocationServer.xml wordt gebruikt voor het vullen van de **DeployRoot** eigenschap, moet u deze waarde verwijderen uit het bestand BootStrap.ini.  

 **De eigenschap DeployRoot uit BootStrap.ini verwijderen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  In de ***deployment_shareProperties*** in het dialoogvenster (waarbij *deployment_share* is de naam van de implementatieshare), klikt u op de **regels** tabblad en klik vervolgens op **Bewerken BootStrap.ini**.  

5.  Verwijder de **DeployRoot** waarde (bijvoorbeeld **DeployRoot =\\\Server\Deployment$**).  

6.  Klik op **bestand**, en klik vervolgens op **opslaan** de wijzigingen wilt opslaan naar het bestand BootStrap.ini.  

7.  Klik op **OK** de wijzigingen wilt indienen.  

###  <a name="UpdateDeploymentShare"></a> De Implementatieshare bijwerken  
 De implementatieshare moet vervolgens worden bijgewerkt voor het genereren van een nieuwe LiteTouch_x86 en LiteTouch_x64 boot-omgeving waarin het bestand LocationServer.xml en de bijgewerkte BootStrap.ini-bestand.  

 **De implementatieshare bijwerken**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

4.  Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

5.  Op de **samenvatting** pagina, controleert u of de gegevens juist zijn en klik vervolgens op **volgende**.  

6.  Op de **bevestiging** pagina, klikt u op **voltooien**.  

> [!NOTE]
>  Wanneer de update is voltooid, voeg de nieuwe LiteTouch_x86 en LiteTouch_x64 Windows PE-omgeving naar Windows Deployment Services of branden media te gebruiken tijdens de implementatie wordt opgestart.  

## <a name="replacing-an-existing-computer-with-a-new-computer-using-lite-touch-installation"></a>Een bestaande Computer vervangen door een nieuwe Computer met behulp van de installatie van Lite Touch  
 U kunt MDT gebruiken voor het implementeren van een installatiekopie naar een nieuwe computer die wordt vervangen door een bestaande computer in de enterprise-architectuur. Deze situatie kan zich voordoen bij het upgraden van een besturingssysteem naar een andere (een nieuw besturingssysteem kan nieuwe hardware vereist) of als de organisatie nieuwere, sneller computers voor bestaande toepassingen moet.  

 Als een bestaande computer vervangen door een nieuwe computer, is het raadzaam om rekening houdend met alle instellingen die van de ene computer naar een andere, zoals gebruikers- en statusgegevens van gebruikers worden gemigreerd. Daarnaast is het belangrijk dat er een hersteloplossing als de migratie mislukt.  

 In deze voorbeeldimplementatie vervangen door de bestaande computer (WDG bestaan-01-) een nieuwe computer (WDG-nieuwe-02) in het domein CORP toevoegen door het vastleggen van gegevens van de gebruikersstatus van WDG bestaan-01- en op een netwerkshare op te slaan. Vervolgens een bestaande installatiekopie implementeren op WDG nieuwe 02 en ten slotte de vastgelegde gegevens van de gebruikersstatus te herstellen naar WDG nieuwe 02. De implementatie worden van een implementatieserver (WDG MDT-01-) uitgevoerd.  

 In MDT, door de sjabloon standaard vervangen Clienttakenreeks te gebruiken voor het maken van een takenreeks die de benodigde implementatietaken uitvoert.  

 Deze demonstratie wordt ervan uitgegaan dat:  

-   MDT is geïnstalleerd op de implementatieserver (WDG MDT 01)  

-   De implementatieshare is al gemaakt en ingevuld, met inbegrip van installatiekopieën van besturingssystemen, toepassingen en stuurprogramma 's  

-   Een afbeelding van een referentiecomputer al is vastgelegd en wordt geïmplementeerd naar de nieuwe computer (WDG nieuwe 02)  

-   Een gedeelde netwerkmap (UserStateCapture$) is gemaakt en gedeeld op de implementatieserver (WDG MDT 01) met de juiste share-machtigingen  

 Een implementatieshare moet vóór het begin van dit voorbeeld bestaan. Zie de sectie 'Beheren implementatie Shares in de implementatie-Workbench', in de MDT-document voor meer informatie over het maken van een implementatieshare *met behulp van de Microsoft Deployment Toolkit*.  

### <a name="step-1-create-a-task-sequence-to-capture-the-user-state"></a>Stap 1: Maak een Takenreeks voor het vastleggen van status van de gebruiker  
 MDT-takenreeksen in het knooppunt Takenreeksen in de Workbench-implementatie met behulp van de Wizard Nieuwe Takenreeks maken. Als u het eerste deel van de Computer vervangen implementatiescenario (de status van de gebruiker op de bestaande computer vastleggen), selecteert u de standaard vervangen Clienttakenreeks-sjabloon in de Wizard Nieuwe Takenreeks.  

 **Maken van een takenreeks voor het vastleggen van de status van de gebruiker in het implementatiescenario Computer vervangen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares / *deployment_share*/Task reeksen (waarbij *deployment_share* is de naam van de implementatieshare configureren ).  

3.  Klik in het deelvenster Acties op **nieuwe Takenreeks**.  

     De Wizard Nieuwe Takenreeks wordt gestart.  

4.  Voltooi de Wizard Nieuwe Takenreeks met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina** |**Dit doet** |  
    |-|-|  
    |**Algemene instellingen** |1.  In **volgorde-ID van de taak**, type **VISTA_EXIST**.<br />2.  In **takenreeksnaam**, type **Scenario met vervangen computers op bestaande Computer uitvoeren**.<br />3.  Klik op **Volgende**.|  
    |**Sjabloon selecteren** |In **de volgende taak reeks sjablonen zijn beschikbaar**. **Selecteer de gateway die u wilt gebruiken als uitgangspunt**, selecteer **standaard vervangen Clienttakenreeks**, en klik vervolgens op **volgende**.|  
    |**Samenvatting** |Controleer of de configuratiegegevens juist zijn en klik vervolgens op **volgende**.|  
    |**Bevestiging** |Klik op **Voltooien**.|  

 De Wizard Nieuwe Takenreeks is voltooid, en de **VISTA_EXIST** takenreeks is toegevoegd aan de lijst van takenreeksen.  

### <a name="step-2-create-a-task-sequence-to-deploy-operating-system-and-restore-the-user-state"></a>Stap 2: Maak een Takenreeks voor het besturingssysteem implementeert en de gebruikersstatus herstellen  
 MDT takenreeksen in het knooppunt Takenreeksen in de implementatie-Workbench maken met behulp van de Wizard Nieuwe Takenreeks. Om uit te voeren van het tweede gedeelte van het implementatiescenario vervangen Computer selecteert (voor het implementeren van het besturingssysteem en het herstellen van de status van de gebruiker op de bestaande computer), u de sjabloon standaard Clienttakenreeks in de Wizard Nieuwe Takenreeks.  

 **Maken van een takenreeks voor het implementeren van de status van de gebruiker in het implementatiescenario Computer vervangen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Task reeksen (waarbij *deployment_share* is de naam van de implementatieshare configureren ).  

3.  Klik in het deelvenster Acties op **nieuwe Takenreeks**.  

     De Wizard Nieuwe Takenreeks wordt gestart.  

4.  Voltooi de Wizard Nieuwe Takenreeks met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Algemene instellingen**|1.  In **volgorde-ID van de taak**, type **VISTA_NEW**.<br />2.  In **takenreeksnaam**, type **Scenario met vervangen computers op de nieuwe Computer uitvoeren**.<br />3.  Klik op **Volgende**.|  
    |**Sjabloon selecteren**|In **de volgende taak reeks sjablonen zijn beschikbaar**. **Selecteer de gateway die u wilt gebruiken als uitgangspunt**, selecteer **standaard Clienttakenreeks**, en klik vervolgens op **volgende**.|  
    |**Besturingssysteem selecteren**|In **de volgende installatiekopieën van besturingssystemen zijn beschikbaar om te worden geïmplementeerd met deze takenreeks**. Selecteer een wilt gebruiken, selecteert u ***captured_vista_image*** (waarbij *captured_vista_image* is de vastgelegde installatiekopie van de referentiecomputer toegevoegd aan het knooppunt besturingssystemen in de Implementatieworkbench), en vervolgens Klik op *volgende*.|  
    |**Productcode opgeven**|Selecteer **Geef een productcode op dit moment geen**, en klik vervolgens op **volgende**.|  
    |OS-instellingen|1.  In **volledige naam**, type **Woodgrove werknemer**.<br />2.  In **organisatie**, type **Woodgrove Bank**.<br />3.  In **startpagina van Internet Explorer**, type **http://www.woodgrovebank.com**.<br />4.  Klik op **Volgende**.|  
    |**Beheerderswachtwoord**|In **beheerderswachtwoord** en **Controleer of de Administrator-wachtwoord**, type **P@ssw0rd**, en klik vervolgens op **voltooien**.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De Wizard Nieuwe Takenreeks is voltooid, en de **VISTA_NEW** takenreeks is toegevoegd aan de lijst van takenreeksen.  

### <a name="step-3-customize-the-mdt-configuration-files"></a>Stap 3: De MDT-configuratiebestanden aanpassen  
 Wanneer de takenreeks MDT is gemaakt, aanpassen van de MDT-configuratiebestanden die de configuratie-instellingen opgeven voor het vastleggen van informatie over de status van de gebruiker. In het bijzonder het CustomSettings.ini-bestand aanpassen door het wijzigen van het bestand in de eigenschappen van de implementatieshare eerder in het implementatieproces gemaakt. In een latere stap, worden de implementatieshare bijgewerkt om ervoor te zorgen dat het configuratiebestand in de implementatieshare is bijgewerkt.  

 **Voor het aanpassen van de MDT-configuratiebestanden voor informatie over gebruikersstatus vastleggen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **eigenschappen** dialoogvenster wordt weergegeven.  

4.  In de **eigenschappen** in het dialoogvenster, klikt u op de **regels** tabblad.  

5.  Op de **regels** wijzigt u het CustomSettings.ini-bestand met de benodigde wijzigingen zoals weergegeven in de volgende exampple. Breng eventuele aanvullende wijzigingen die zijn vereist voor de omgeving.  

     **Aangepaste CustomSettings.ini-bestand**  

    ```  
    [Settings]  
    Priority=Default  
    Properties=MyCustomProperty  

    [Default]  
    OSInstall=Y  

    UDShare=\\WDG-MDT-01\UserStateCapture$  
    UDDir=%OSDCOMPUTERNAME%  
    UserDataLocation=NETWORK  
    SkipCapture=NO  
    SkipAdminPassword=YES  
    SkipProductKey=YES  

    ```  

6.  In de **eigenschappen** in het dialoogvenster, klikt u op **OK**.  

7.  Sluit alle geopende vensters en dialoogvensters.  

### <a name="step-4-configure-the-windows-pe-options-for-the-deployment-share"></a>Stap 4: Configureer de Windows PE-opties voor de Implementatieshare  
 Configureer de Windows PE-opties voor de implementatieshare in het knooppunt Implementatieshares in de implementatie-Workbench.  

> [!NOTE]
>  Als de apparaatstuurprogramma's voor de bestaande computer (WDG bestaan-01-) en de nieuwe computer (WDG-nieuwe-01) opgenomen in Windows Vista zijn, wordt deze stap overslaan en doorgaan met de volgende stap.  

 **De Windows PE-opties voor de implementatieshare te configureren**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

     De **eigenschappen** dialoogvenster wordt weergegeven.  

4.  In de **eigenschappen** in het dialoogvenster op de **Windows PE *platform* onderdelen** tabblad (waarbij *platform* is de architectuur van Windows PE-installatiekopie worden geconfigureerd), in **selectie profiel**, selecteer ***device_drivers*** (waarbij *device_drivers* is de naam van het apparaat stuurprogrammaselectie profiel), en klik vervolgens op **OK**.  

### <a name="step-5-update-the-deployment-share"></a>Stap 5: De Implementatieshare bijwerken  
 Na het configureren van de Windows PE-opties voor de implementatieshare, moet u de implementatieshare bijwerken. Bijwerken van de implementatieshare alle MDT-configuratiebestanden bijgewerkt en genereert een aangepaste versie van Windows PE. De aangepaste versie van Windows PE wordt gebruikt voor het starten van de referentiecomputer en het implementatieproces LTI te initiëren.  

 **Bijwerken van de implementatieshare in de Workbench-implementatie**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **Update DeploymentShare**.  

     De Wizard Update Deployment Share wordt gestart.  

4.  Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

5.  Op de **samenvatting** pagina, controleert u of de gegevens juist zijn en klik vervolgens op **volgende**.  

6.  Op de **bevestiging** pagina, klikt u op **voltooien**.  

 De Workbench-implementatie begint de implementatieshare bijwerken. De implementatie-Workbench maakt het LiteTouchPE_x86.iso en LiteTouchPE_x86.wim bestanden (voor 32-bits doelcomputers) of de bestanden LiteTouchPE_x64.iso en LiteTouchPE_x64.wim-bestanden (voor 64-bits doelcomputers) in de *deployment_share*Map \Boot (waarbij *deployment_share* de gedeelde map als share van de implementatie gebruikt).  

### <a name="step-6-create-the-lti-bootable-media"></a>Stap 6: De LTI opstartbare Media maken  
 Bieden een methode voor het starten van de computer met de aangepaste versie van Windows PE gemaakt tijdens de implementatieshare is bijgewerkt. De implementatie-Workbench maakt het LiteTouchPE_x86.iso en LiteTouchPE_x86.wim bestanden (voor 32-bits doelcomputers) of de bestanden LiteTouchPE_x64.iso en LiteTouchPE_x64.wim-bestanden (voor 64-bits doelcomputers) in de *deployment_share*Map \Boot (waarbij *deployment_share* de gedeelde map als share van de implementatie gebruikt). Maak de juiste LTI opstartbare media van een van deze installatiekopieën.  

 **De LTI opstartbare media maken**  

1.  Navigeer in Windows Verkenner naar *deployment_share*map \Boot (waarbij *deployment_share* de gedeelde map als share van de implementatie gebruikt).  

2.  Op basis van het type computer gebruikt voor de bestaande computer (WDG bestaan-01-) en de nieuwe computer (WDG-nieuwe-02), voer een van de volgende taken:  

    -   Als de referentiecomputer een fysieke computer is, maakt u een CD of DVD van het ISO-bestand.  

    -   Als de referentiecomputer een virtuele machine is, start u de virtuele machine rechtstreeks vanuit het ISO-bestand of vanaf een CD of DVD van het ISO-bestand.  

### <a name="step-7-start-the-existing-computer-with-the-lti-bootable-media"></a>Stap 7: De bestaande Computer opstart met de LTI opstartbare Media  
 Start de bestaande computer (WDG bestaan-01-) met de LTI opstartbare media die eerder in het proces hebt gemaakt. Deze CD wordt Windows PE gestart op de bestaande computer en start het proces MDT-implementatie. Aan het einde van het implementatieproces van MDT, wordt de gebruiker statusmigratie-informatie opgeslagen in de UserStateCapture$ gedeelde map.  

> [!NOTE]
>  U kunt ook de MDT-proces starten door het starten van de doelcomputer vanaf de Windows Deployment Services. Zie voor meer informatie de sectie 'Voorbereiden van Windows Deployment Services', in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

 **De bestaande computer starten met de LTI opstartbare media**  

1.  Start WDG bestaan-01-met de LTI opstartbare media die eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Windows-implementatie wordt gestart.  

2.  Voltooi de Wizard implementatie van Windows met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Welkom bij de implementatie**|Klik op **voert u de Wizard implementatie** een nieuw besturingssysteem installeert en klik vervolgens op **volgende**.|  
    |**Geef referenties op voor het verbinden met netwerkshares.**|1.  In **gebruikersnaam**, type **beheerder**.<br />2.  In **wachtwoord**, type **P@ssw0rd**.<br />3.  In **domein**, type **CORP**.<br />4.  Klik op **OK**.|  
    |**Selecteer een takenreeks uit te voeren op deze computer.**|Klik op *Scenario met vervangen computers op bestaande Computer uitvoeren*, en klik vervolgens op **volgende**.|  
    |**Opgeven waar u uw gegevens en instellingen opslaan**|Klik op **Volgende**.|  
    |**Geef aan waar een volledige computernaam back-up opslaan**|Klik op **doen geen back-up van de bestaande computer**, en klik vervolgens op **volgende**.|  
    |**Gereed om te beginnen**|Klik op **begint**.|  

     Als er fouten of waarschuwingen optreden, Raadpleeg het document MDT *probleemoplossing verwijzing*.  

3.  In de **implementatieoverzicht** in het dialoogvenster, klikt u op **Details**.  

     Als er fouten of waarschuwingen opgetreden, bekijk de fouten of waarschuwingen en noteert u diagnostische informatie.  

4.  In de **implementatieoverzicht** in het dialoogvenster, klikt u op **voltooien**.  

 De migratie van de gebruikersstatusinformatie wordt vastgelegd en wordt opgeslagen in de gedeelde netwerkmap (UserStateCapture$) eerder in het proces hebt gemaakt.  

### <a name="step-8-start-the-new-computer-with-the-lti-bootable-media"></a>Stap 8: Start de nieuwe Computer met de LTI opstartbare Media  
 Start de nieuwe computer (WDG-nieuwe-02) met de LTI opstartbare media die eerder in het proces hebt gemaakt. Deze CD wordt Windows PE gestart op de referentiecomputer en start het proces MDT-implementatie. Windows Vista wordt geïmplementeerd op de nieuwe computer aan het einde van het implementatieproces van de MDT en de vastgelegde migratie van de gebruikersstatusinformatie wordt hersteld naar de nieuwe computer.  

> [!NOTE]
>  U kunt ook de MDT-proces starten door het starten van de doelcomputer vanaf de Windows Deployment Services. Zie voor meer informatie de sectie 'Voorbereiden van Windows Deployment Services', in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

 **Starten van de nieuwe computer met de LTI opstartbare media**  

1.  WDG nieuwe 02 beginnen met de LTI opstartbare media die eerder in het proces hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Windows-implementatie wordt gestart.  

2.  Voltooi de Wizard Windows-implementatie met behulp van de volgende informatie. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |--|--|
    |**Welkom bij de implementatie**|Klik op **de Wizard voor het installeren van een nieuw besturingssysteem uitvoeren**, en klik vervolgens op **volgende**.|  
    |**Geef referenties op voor het verbinden met netwerkshares.**|1.  In **gebruikersnaam**, type **beheerder**.<br />2.  In **wachtwoord**, type **P@ssw0rd**.<br />3.  In **domein**, type **CORP**.<br />4.  Klik op **OK**.|  
    |**Selecteer een takenreeks uit te voeren op deze computer.**|Klik op **Scenario met vervangen computers op de nieuwe Computer uitvoeren**, en klik vervolgens op **volgende**.|  
    |**Naam van de computer configureren**|In **computernaam**, type **WDG nieuwe 02**, en klik vervolgens op **volgende**.|  
    |**De computer toevoegen aan een domein of werkgroep**|Klik op **Volgende**.|  
    |**Geef op of om gebruikersgegevens te herstellen**|1.  Klik op **Geef een locatie**.<br />2.  In **locatie**, type  **\\\WDG-MDT-01\UserStateCapture$\WDG-EXIST-01**.<br />3.  Klik op **Volgende**.|  
    |**Landinstellingen-selectie**|Klik op **Volgende**.|  
    |**Stel de tijdzone**|Klik op **Volgende**.|  
    |**Geef op of een installatiekopie vastleggen**|Klik op **niet een afbeelding van deze computer vastlegt**, en klik vervolgens op **volgende**.|  
    |**Geef de BitLocker-configuratie**|Klik op **BitLocker inschakelen voor deze computer**, en klik vervolgens op **volgende**.|  
    |**Gereed om te beginnen**|Klik op **begint**.|  

     Als er fouten of waarschuwingen moeten worden uitgevoerd, raadpleegt u het document MDT *probleemoplossing verwijzing*.  

3.  In de **implementatieoverzicht** in het dialoogvenster, klikt u op **Details**.  

     Als er fouten of waarschuwingen opgetreden, bekijk de fouten of waarschuwingen en noteert u diagnostische informatie.  

4.  In de **implementatieoverzicht** in het dialoogvenster, klikt u op **voltooien**.  

 Windows Vista wordt nu geïnstalleerd op de nieuwe computer en de vastgelegde gebruiker statusmigratie-informatie ook is hersteld.  

## <a name="integrating-custom-deployment-code-into-mdt"></a>Aangepaste implementatiecode integreren in MDT  
 Het is gebruikelijk voor een implementatieteam om complexe behoeften, specifiek voor de doelomgeving, die niet wordt voldaan door de implementatie-Workbench vooraf gedefinieerde takenreeksacties of standaard MDT-configuratiebestanden. In dit geval aangepaste code om te voldoen aan de vereisten te implementeren.  

 Aangepaste implementatiecode integreren met MDT door:  

-   Een scripttaal kiezen, zoals beschreven in [kiezen van de juiste taal voor het uitvoeren van scripts](#ChooseAppropLanguage)  

-   Het afwegen van ZTIUtility.vbs zoals beschreven in [begrijpen hoe u wilt gebruiken voor de ZTIUtility](#UnderstandLeverageZTI)  

-   Aangepaste implementatiecode integreren, zoals beschreven in [integreren van aangepaste Code voor implementatie](#IntegrateCustomDeploy)  

 De volgende secties wordt ervan uitgegaan dat MDT is geconfigureerd op de implementatieserver van een.  

###  <a name="ChooseAppropLanguage"></a> De juiste taal kiezen  
 Hoewel elke code die kan worden uitgevoerd op Windows of in Windows PE kan worden aangeroepen als de installatie van een toepassing of via een MDT takenreeksstap, wordt aangeraden met behulp van scripts in de vorm van .vbs of .wsf-bestanden.  

 Het voordeel van .wsf-bestanden is ingebouwd logboekregistratie bovendien sommige andere vooraf gedefinieerde functies al gebruikt door de processen van ZTI en LTI. Deze functies zijn beschikbaar in het script ZTIUtility is gedistribueerd met MDT.  

 Wanneer er wordt verwezen vanuit een aangepast script, initialiseert het script ZTIUtility de MDT-omgeving en setup-klassen. Deze klassen zijn beschikbaar:  

-   **Logging**. Deze klasse biedt de functionaliteit van logboekregistratie die alle MDT-scripts gebruiken. Dit leidt ook tot één logboekbestand voor elk script wordt uitgevoerd tijdens de implementatie en een geconsolideerde logbestand van alle scripts uitvoeren. Deze logboekbestanden worden gemaakt in een indeling die is ontworpen om te worden gelezen door TRACE32; Dit hulpprogramma is beschikbaar in de [System Center Configuration Manager 2007 Toolkit V2](https://www.microsoft.com/download/en/details.aspx?id=9257).  

-   **Omgeving**. Deze klasse omgevingsvariabelen die worden verzameld via WMI en MDT regelverwerking configureert en kan ze rechtstreeks vanuit het script worden verwezen. Hierdoor kunnen implementatie-eigenschappen moeten worden gelezen, toegang geven tot alle configuratie-informatie die wordt gebruikt door de processen van ZTI en LTI.  

-   **Hulpprogramma voor**. Deze klasse biedt algemene hulpprogramma's die in ZTI en LTI scripts worden gebruikt. Microsoft raadt aan dat elk gewenst moment aangepaste code die is ontwikkeld voor deze klasse moet worden onderzocht om te zien als code gewoon kan worden hergebruikt. Als u meer informatie over een aantal van de functionaliteit van deze klasse is later in deze sectie worden opgenomen.  

-   **Database**. Deze klasse voert functies zoals verbinding maken met databases en het lezen van gegevens van databases. In het algemeen toegang tot de database-klasse direct wordt niet aanbevolen; in plaats daarvan moet regelverwerking worden gebruikt om uit te voeren database zoekacties.  

-   **Tekenreeksen**. Deze klasse voert algemene tekenreeks verwerking routines zoals het maken van een gescheiden lijst met items om weer te geven een hexadecimale waarde, bijsnijden spaties uit een reeks rechts uitlijnen van een tekenreeks, links uitlijnen van een tekenreeks, forceren van een waarde voor de indeling van tekenreeks, waardoor een waarde naar matrix indeling genereren van een willekeurige globally unique identifier (GUID) en Base64-conversies.  

-   **FileHandling**. Deze klasse voert functies zoals normaliseren paden en kopiëren, verplaatsen en verwijderen van bestanden en mappen.  

-   **clsRegEx**. Deze klasse voert functies van de reguliere expressie.  

 Enkele wijzigingen aan in MDT, zijn geïmplementeerd met de architectuur van het script om ervoor te client Microsoft Visual Basic® Scripting Edition (VBScript) meer robuuste en betrouwbare. Deze wijzigingen omvatten:  

-   Uitgebreide wijzigingen in ZTIUtility.vbs (het hoofdscript library), met inbegrip van nieuwe API's en betere foutafhandeling  

-   Een nieuw overzicht met de algemene structuur van de ZTI_*xxx*.wsf scripts  

 De algemene structuur van de MDT-scripts is ook gewijzigd. De meeste MDT-scripts zijn nu ingesloten in VBScript **klasse** objecten. De klasse is geïnitialiseerd en is aangeroepen met de **RunNewInstance** functie.  

> [!NOTE]
>  De meeste bestaande MDT 2008 Update 1-scripts, werken als-is in MDT, zelfs met de uitgebreide wijzigingen in ZTIUtility.vbs, het meeste MDT scripts ZTIUtility.vbs zal bevatten.  

###  <a name="UnderstandLeverageZTI"></a> Informatie over hoe u ZTIUtility  
 Het bestand ZTIUtility.vbs bevat objectklassen die kunnen worden gebruikt in uw aangepaste code. Aangepaste code met MDT geïntegreerd met behulp van de:  

-   Logboekregistratie klasse is gedefinieerd in ZTIUtility.vbs, zoals beschreven in [de klasse ZTIUtility logboekregistratie gebruiken](#UseZTILogging)  

-   Omgeving klasse is gedefinieerd in ZTIUtility.vbs, zoals beschreven in [de ZTIUtility omgeving klasse gebruiken](#UseZTIEnvironment)  

-   Hulpprogramma voor klasse is gedefinieerd in ZTIUtility.vbs, zoals beschreven in [de ZTIUtility hulpprogrammaklasse gebruiken](#UseZTIUtility)  

####  <a name="UseZTILogging"></a> Gebruik de klasse ZTIUtility-logboekregistratie  
 De klasse logboekregistratie in ZTIUtiliy.vbs biedt een eenvoudige mechanisme voor aangepaste code logboekgegevens status, waarschuwingen en fouten op dezelfde manier als andere scripts tijdens de implementatie van een ZTI of LTI. Deze standaardisatie zorgt ook voor dat de **LTI implementatieoverzicht** correct meldt de status van elke gewenste aangepaste code die wordt uitgevoerd in het dialoogvenster.  

 Hieronder ziet u een aangepaste code voorbeeldscript die gebruikmaakt van de **oLogging.CreateEntry** en **TestAndFail** functies aan te melden berichten, afhankelijk van de resultaten van de verschillende soorten scriptacties.  

 **Voorbeeldscript ZTIUtility logboekregistratie gebruiken: ZTI_Example.wsf**  

```  
<job id="ZTI_Example">  
<script language="VBScript" src="ZTIUtility.vbs"/>  
<script language="VBScript">  

' //*******************************************************  
' //  
' // Copyright (c) Microsoft Corporation.  All rights reserved  
' // Microsoft Deployment Toolkit Solution Accelerator  
' // File: ZTI_Example.wsf  
' //  
' // Purpose: Example of scripting with the  
' //          Microsoft Deployment Toolkit.  
' //  
' // Usage: cscript ZTI_Example.wsf [/debug:true]  
' //  
' //*******************************************************  

Option Explicit  
RunNewInstance  

'//--------------------------------------------------------  
'// Main Class  
'//--------------------------------------------------------  
Class ZTI_Example  

'//--------------------------------------------------------  
'// Main routine  
'//--------------------------------------------------------  

Function Main()  

  Dim iRetVal  
  Dim sScriptPath  

  iRetVal = SUCCESS  

  oLogging.CreateEntry "Begin example script…", _  
    LogTypeInfo  

  ' %ServerA% is a generic variable available within  
  ' every CustomSettings.ini file.  

  sScriptPath = "\\" & oEnvironment.Item("ServerA") & _  
    "\public\products\Applications\User\Technet\USEnglish"  

  ' Validate a connection to server, net connect with  
  ' credentials if necessary.  
  iRetVal = oUtility.ValidateConnection( sScriptPath )  
  TestAndFail iRetVal, 9991, "Validate Connection to [" & _  
    sScriptPath & "]"  

  'Run Setup Program  

  iRetVal = oUtility.RunWithHeartbeat( """" & _  
    sScriptPath & "\setup.exe"" /?" )  
  TestAndFail iRetVal, 9991, "RunWithHeartbeat [" & _  
    sScriptPath & "]"  

  'Perform any cleanup from installation process  

  oShell.RegWrite "HKLM\Software\Microsoft\SomeValue", _  
    "Done with Execution of XXX.", "REG_SZ"  

  Main = iRetVal  

End Function  

End Class  

</script>  
</job>  
```  

> [!NOTE]
>  Als u wilt doorgaan met behulp van scripts die aanroep **ZTIProcess()** met **ProcessResults()**, kunt u blijven doen. Bepaalde Verbeterde foutafhandeling functies wordt echter niet worden ingeschakeld.  

####  <a name="UseZTIEnvironment"></a> Gebruik de klasse ZTIUtility-omgeving  
 De klasse omgeving in ZTIUtiliy.vbs biedt toegang tot en de mogelijkheid om bij te werken, MDT-eigenschappen. In het voorgaande voorbeeld **oEnvironment.Item("Memory")** wordt gebruikt voor het ophalen van de hoeveelheid RAM-geheugen beschikbaar; Dit kan ook worden gebruikt voor het ophalen van de waarde van een van de eigenschappen die worden beschreven in het document MDT *Toolkit-verwijzing* .  

####  <a name="UseZTIUtility"></a> Gebruik het hulpprogramma ZTIUtility-klasse  
 Het script ZTIUtility.vbs bevat een aantal veelgebruikte hulpprogramma's die een script voor een aangepaste implementatie kunt gebruiken. U kunt deze hulpprogramma's aan toevoegen elk script dezelfde manier als de **oLogging** en **oEnvironment** klassen.  

De volgende tabel details over een aantal handige functies beschikbaar en de uitvoer. Raadpleeg het bestand ZTIUtility.vbs voor een volledige lijst met de beschikbare functies.  

|**Functie**|**Uitvoer**|  
|-|-|
|**oUtility.LocalRootPath**|Retourneert het pad van de hoofdmap wordt gebruikt door het implementatieproces op de doelcomputer — bijvoorbeeld C:\MININT|  
|**oUtility.BootDevice**|Retourneert het opstartapparaat system — bijvoorbeeld MULTI(0)DISK(0)RDISK(0)PARTITION(1)|  
|**oUtility.LogPath**|Retourneert het pad naar de map met logbestanden wordt gebruikt tijdens de implementatie — bijvoorbeeld C:\MININT\SMSOSD\OSDLOGS|  
|**oUtility.StatePath**|Retourneert het pad van de momenteel geconfigureerde Statusopslag — bijvoorbeeld C:\MININT\StateStore|  
|**oUtility.ScriptName**|Retourneert de naam van het script aanroepen van de functie — bijvoorbeeld Z RAMTest|  
|**oUtility.ScriptDir**|Retourneert het pad naar het script dat de functie aanroept, bijvoorbeeld \\\server_name\Deployment$\Scripts|  
|**oUtility.ComputerName**|Bepaalt de naam van de computer die wordt gebruikt tijdens het maken, bijvoorbeeld computernaam|  
|**oUtility.ReadIni (bestand, sectie, item)**|Kan het opgegeven item moet worden gelezen uit het ini-bestand|  
|**oUtility.WriteIni (bestand, sectie, item, waarde)**|Kan het opgegeven item naar een ini-bestand worden geschreven|  
|**oUtility.Sections(file)**|Leest de secties van een ini-bestand en slaat ze op in een object voor verwijzing|  
|**oUtility.SectionContents (bestand, sectie)**|De inhoud van het opgegeven .ini-bestand wordt gelezen en slaat ze op in een object|  
|**oUtility.RunWithHeartbeat(sCmd)**|Wanneer de opdracht wordt uitgevoerd, heartbeat informatie schrijven naar de logboeken om de 0,5 seconden|  
|**oUtility.FindFile**<br /><br /> **(sFilename,sFoundPath)**|Hiermee zoekt u naar het opgegeven bestand in de map DeployRoot en standaard submappen, inclusief onderhoud, hulpprogramma's voor USMT, sjablonen, Scripts en beheer|  
|**oUtility.findMappedDrive(sServerUNC)**|Controleert of een station is toegewezen aan het opgegeven UNC-pad is en de stationsletter retourneert|  
|**oUtility.ValidateConnection(sServerUNC)**|Controleert of er een bestaande verbinding met de opgegeven server is en als er geen is, probeert te maken van een|  
|**MapNetworkDrive**<br /><br /> **(sShare, SDomID, sDomPwd)**|Een stationsletter toegewezen aan het UNC-pad dat is opgegeven als de share en retourneert de stationsletter gebruikt; retourneert een fout als mislukt|  
|**VerifyPathExists(strPath)**|Hiermee wordt gecontroleerd of het opgegeven pad bestaat|  
|**oEnvironment.Substitute(sVal)**|Breidt variabelen of functies binnen deze tekenreeks opgegeven een tekenreeks|  
|**oEnvironment.Item**<br /><br /> **(sName)**|Lees- of schrijfbewerking een variabele naar een permanente opslag|  
|**oEnvironment.Exists**<br /><br /> **(sName)**|Tests uit om te zien of de variabele bestaat|  
|**oEnvironment.ListItem**<br /><br /> **(sName)**|Lees- of schrijfbewerking een variabele van type **matrix** naar een permanente opslag|  
|**oLogging.ReportFailure**<br /><br /> **(sMessage, iError)**|Gebruikt voor het afsluiten van een gestructureerde uitvoeren als er een onherstelbare fout wordt gedetecteerd|  
|**oLogging.CreateEvent**<br /><br /> **(iEventID, iType, sbericht, arrParms)**|Een bericht naar het logboekbestand geschreven en waarmee de gebeurtenis met een gedefinieerde server|  
|**oLogging.CreateEntry**<br /><br /> **(sLogMsg, iType)**|Een bericht naar het logboekbestand geschreven|  
|**TestAndFail (iRc, iError, sbericht)**|Het script wordt afgesloten **iError** als **iRc** false of is mislukt|  
|**TestAndLog (iRc, sbericht)**|Hiermee wordt een waarschuwing alleen als geregistreerd **iRc** false of is mislukt|  

###  <a name="IntegrateCustomDeploy"></a> Integratie van aangepaste implementatiecode  
 Aangepaste implementatiecode kan worden geïntegreerd in de MDT-proces op verschillende manieren; ongeacht de methode die wordt gebruikt, moeten de volgende twee regels worden voldaan:  

-   De naam van het aangepaste implementatie code script moet altijd beginnen met de letter Z.  

-   De aangepaste implementatie-code moet worden geplaatst in de map Scripts op de implementatieshare: bijvoorbeeld D:\Production implementatie Share\Scripts.  

 De meest gebruikte methoden voor het integreren van aangepaste code die zorg er ook voor consistente logboekregistratie zijn:  

-   De code als een MDT-toepassing implementeren  

-   Start de code als een MDT taak sequence-opdracht  

-   Start de code als een gebruiker afsluiten script  

#### <a name="deploy-custom-code-as-an-mdt-application"></a>Aangepaste Code implementeren als een MDT-toepassing  
 Aangepaste implementatiecode kan worden geïmporteerd in de Workbench-implementatie en op dezelfde manier als een andere toepassing beheerd.  

 **Maken van een nieuwe toepassing aangepaste implementatiecode uit te voeren**  

1.  De aangepaste implementatie worden gekopieerd naar de *deployment_share*\Scripts map (waarbij *deployment_share* is het volledig gekwalificeerde pad naar de implementatieshare).  

2.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

3.  Ga in de consolestructuur van de implementatie-Workbench naar Implementatieshares /*deployment_share*/Applications (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

4.  Klik in het deelvenster Acties op **nieuwe toepassing**.  

     De Wizard Nieuwe toepassing wordt gestart.  

5.  Voltooi de Wizard Nieuwe toepassing met de volgende gegevens. Accepteer de standaardwaarden tenzij anders vermeld.  

    |**Op deze wizardpagina**|**Dit doet**|  
    |-|-|  
    |**Toepassingstype**|Klik op **toepassing zonder bronbestanden of ergens anders op het netwerk**, en klik vervolgens op **volgende**.|  
    |**Details**|Deze pagina op basis van de gegevens van de toepassing, en klik vervolgens op **volgende**.|  
    |**Opdrachtdetails**|1.  In de **opdrachtregel** in het vak **cscript.exe %SCRIPTROOT%\custom_code** (waarbij *custom_code* is de naam van de aangepaste code die is ontwikkeld).<br />2.  In de **werkmap** in het vak ***working_directory*** (waar working_directory is de naam van de werkmap van de aangepaste code; dit is doorgaans de dezelfde map die is opgegeven in de **Opdrachtregel** vak).<br />3.  Klik op **Volgende**.|  
    |**Samenvatting**|Controleer of de configuratie-instellingen juist zijn en klik vervolgens op **volgende**.|  
    |**Bevestiging**|Klik op **Voltooien**.|  

 De toepassing wordt weergegeven in het knooppunt toepassingen in de implementatie-Workbench.  

#### <a name="add-the-custom-code-as-a-task-sequence-step"></a>De aangepaste Code toevoegen als een Takenreeksstap  
 Aangepaste implementatiecode kan worden aangeroepen rechtstreeks vanaf een punt binnen een takenreeks; Dit biedt toegang tot de gebruikelijke taak reeks regels en de opties.  

 **De van aangepaste implementatiecode toevoegen aan een bestaande takenreeks**  

1.  De aangepaste implementatie worden gekopieerd naar de *deployment_share*\Scripts map (waarbij *deployment_share* is het volledig gekwalificeerde pad naar de implementatieshare).  

2.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

3.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share/Takenreeksen* (waarbij *deployment_share* is de naam van de implementatieshare configureren ).  

4.  Klik in het detailvenster op ***task_sequence*** (waarbij *task_sequence* is de naam van de takenreeks die de aangepaste code wordt uitgevoerd).  

5.  Klik in het deelvenster Acties op **eigenschappen**.  

6.  In de ***task_sequenceProperties*** in het dialoogvenster, klikt u op de **Takenreeks** tabblad.  

7.  Ga in de consolestructuur naar *groep* (waarbij *groep* is de groep toevoegen van de takenreeksstap).  

8.  Klik op **toevoegen**, klikt u op **algemene**, en klik vervolgens op **opdrachtregel uitvoeren**.  

9. Klik in de consolestructuur op **opdrachtregel uitvoeren**, en klik vervolgens op de **eigenschappen** tabblad.  

10. In de **naam** in het vak ***naam*** (waarbij *naam* is een beschrijvende naam van de aangepaste code).  

11. Op de **eigenschappen** tabblad, in de **opdrachtregel** in het vak ***command_line*** (waarbij *command_line* is de opdracht de aangepaste code uit te voeren: bijvoorbeeld: **cscript.exe %SCRIPTROOT%\CustomCode.vbs**).  

12. In de **starten in** in het vak ***pad*** (waarbij *pad* is het volledig gekwalificeerde pad naar de map van de aangepaste code; dit is meestal hetzelfde pad opgegeven in de  **Command line** vak), en klik vervolgens op **OK**.  

 De zojuist gemaakte takenreeksstap wordt weergegeven in de lijst met takenreeksstappen.  

#### <a name="run-custom-code-as-a-user-exit-script"></a>Aangepaste Code als een gebruiker afsluiten Script uitvoeren  
 Ook is het mogelijk de aangepaste code als een gebruiker afsluiten script uitvoeren vanuit CustomSettings.ini met de **UserExit** richtlijn. Dit biedt een mechanisme voor gegevens worden doorgegeven in het validatieproces van CustomSettings.ini regel en biedt een dynamische update van de MDT-eigenschappen  

 Voor meer informatie over de gebruiker sluiten scripts en de **UserExit** richtlijn, Zie de sectie 'Gebruiker sluiten Scripts in het bestand CustomSettings.ini', in het document MDT *met behulp van de Microsoft Deployment Toolkit*.  

## <a name="installing-device-drivers-using-various-installation-methods"></a>Apparaatstuurprogramma's met behulp van verschillende installatiemethoden installeren  
 In dit scenario kunt u MDT gebruiken voor het implementeren van een besturingssysteem op verschillende typen hardware. Als onderdeel van het implementatieproces identificeren en apparaatstuurprogramma's te installeren, zodat elk hardwaretype behoren. Er zijn twee soorten apparaatstuurprogramma's; elk moet anders worden verwerkt tijdens de implementatie:  

-   Apparaatstuurprogramma's die een INF-bestand dat kan worden gebruikt voor het apparaatstuurprogramma importeren in de implementatie-Workbench bevatten  

-   Apparaatstuurprogramma's die worden geleverd als een toepassing en die moet worden geïnstalleerd als een toepassing  

 MDT kunt u beide typen stuurprogramma's verwerken als onderdeel van een besturingssysteem-implementatie.  

 Apparaatstuurprogramma's installeren:  

-   Bepalen van de methoden voor het installeren van elk apparaatstuurprogramma zoals beschreven in [te bepalen dat de methode om een apparaatstuurprogramma te installeren](#WhichMethodtoInstallDriver)  

-   Via de out-of-box stuurprogramma's-methode, zoals beschreven in [installeren apparaat stuurprogramma's via de Out-of-Box stuurprogramma's-methode](#InstallOutofBoxDrivers)  

-   Als toepassingen installeren, zoals beschreven in [apparaatstuurprogramma's installeren als toepassingen](#InstallDriversasApplications)  

 Dit scenario veronderstelt dat MDT wordt uitgevoerd op een implementatieserver.  

###  <a name="WhichMethodtoInstallDriver"></a> Bepalen welke methode u wilt gebruiken om een apparaatstuurprogramma te installeren  
 Hardwarefabrikanten release apparaatstuurprogramma's in een van twee vormen:  

-   Als een pakket dat u kunt bevat uitpakken en die INF-bestanden voor het importeren van het stuurprogramma in de Workbench-implementatie  

-   Als een toepassing die u moet installeren via de installatieprocedures van de traditionele toepassing  

 Voor toegang tot INF-bestanden kunnen worden geëxtraheerd apparaatstuurprogrammapakketten kunnen MDT automatisch stuurprogramma detectie en installatie proces gebruiken door de eerste importeren van het stuurprogramma in het knooppunt Out-of-Box stuurprogramma's in de implementatie-Workbench.  

 Apparaatstuurprogrammapakketten niet kunnen worden geëxtraheerd isoleren INF-bestanden of die niet goed zonder eerst werken wordt geïnstalleerd met behulp van het installatieprogramma van een toepassing zoals een MSI of de Setup.exe-bestand kunt gebruiken de functie van de MDT-toepassing installeren en het apparaat installeren stuurprogramma net als voor een normale toepassing tijdens de implementatie.  

###  <a name="InstallOutofBoxDrivers"></a> Apparaatstuurprogramma's via de methode Out-of-Box stuurprogramma's installeren  
 U kunt apparaatstuurprogrammapakketten zoals een INF-bestand voor de implementatie-Workbench en deze automatisch worden geïnstalleerd als onderdeel van het implementatieproces importeren. Voor het implementeren van dit type apparaat stuurprogramma implementatie, moet u eerst de apparaatstuurprogramma's toevoegen aan de implementatie-Workbench.  

 **De apparaatstuurprogramma's toevoegen aan de implementatie-Workbench**  

1.  Downloaden van de vereiste apparaatstuurprogramma's voor de hardwaretypen worden geïmplementeerd en uitpakken van het apparaatstuurprogrammapakket naar een tijdelijke locatie.  

2.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

3.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Out-of-Box stuurprogramma's (waarbij *deployment_share* is de naam van de share van de implementatie naar Configureer).  

4.  Klik in het deelvenster Acties op **stuurprogramma's importeren**.  

     De Wizard apparaatstuurprogramma importeren wordt gestart.  

5.  Op de **Directory opgeven** pagina in de **station bron** mapsectie, klikt u op **Bladeren** gaat u naar de map waarin de nieuwe stuurprogramma's en klik vervolgens op  **Volgende**.  

    > [!NOTE]
    >  De Wizard nieuwe apparaatstuurprogramma zoekt alle submappen van de bronmap van het stuurprogramma; dus als er meerdere stuurprogramma's te installeren, mappen in de hoofdmap van de dezelfde uitgepakt en stel het stuurprogramma bronmap als de hoofdmap waarin alle van het stuurprogramma bronmappen.  

6.  Op de **samenvatting** pagina, controleert u of de instellingen juist zijn en klik vervolgens op **volgende** de stuurprogramma's importeren in de implementatie-Workbench.  

7.  Op de **bevestiging** pagina, klikt u op **voltooien**.  

 Als de apparaatstuurprogramma's bevatten voor opstarten essentiële stuurprogramma's zoals massaopslag of netwerk klasse's, moet naast de implementatieshare worden bijgewerkt voor het genereren van een nieuwe LiteTouch_x86 en LiteTouch_x64 boot-omgeving met de nieuwe stuurprogramma's.  

 **Apparaatstuurprogramma's toevoegen aan de Lite Touch Windows PE-installatiekopieën**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

4.  Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

5.  Op de **samenvatting** pagina, Controleer of de details en klik vervolgens op **volgende**.  

6.  Op de **bevestiging** pagina, klikt u op **voltooien**.  

###  <a name="InstallDriversasApplications"></a> Apparaatstuurprogramma's installeren als toepassingen  
 Apparaatstuurprogramma's die worden geleverd, zoals toepassingen en u kunt geen uitpakken naar een map met een INF-bestand, naast de stuurprogramma's worden toegevoegd aan de implementatie-Workbench als een toepassing voor de installatie van tijdens het implementatieproces.  

 Toepassingen kunnen worden opgegeven als een takenreeksstap of opgegeven in CustomSettings.ini; apparaattoepassingen stuurprogramma moeten echter alleen wanneer de takenreeks wordt uitgevoerd op een computer met de apparaten worden geïnstalleerd. Voer de takenreeksstap voor het implementeren van de relevante apparaattoepassingen stuurprogramma als een voorwaardelijke takenreeksstap zodat dit. De voorwaardelijke criteria kunnen worden opgegeven voor het uitvoeren van de takenreeksstap met behulp van WMI-query's voor het apparaat op de doelcomputer.  

#### <a name="add-the-device-driver-application-to-the-deployment-workbench"></a>De apparaat-stuurprogrammatoepassing toevoegen aan de implementatie-Workbench  
 Elk apparaat stuurprogramma-toepassing moet eerst worden geïmporteerd in de implementatie-Workbench.  

> [!NOTE]
>  Configureren of de toepassing moet zichtbaar is tijdens de implementatie op de **eigenschappen** in het dialoogvenster van elke toepassing in te schakelen de **verbergen van deze toepassing in de Wizard implementatie** selectievakje. Herhaal dit proces voor elk apparaat stuurprogrammatoepassing tijdens de implementatie gebruikt.  

 **Het apparaat stuurprogrammatoepassing toevoegen aan de implementatie-Workbench**  

1.  De toepassing van apparaat-stuurprogramma downloaden en opslaan op een tijdelijke locatie.  

2.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

3.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Applications (waarbij *deployment_share* is de naam van de implementatieshare configureren) .  

4.  Klik in het deelvenster Acties op **nieuwe toepassing**.  

     De Wizard Nieuwe toepassing wordt gestart.  

5.  Op de **toepassingstype** pagina, klikt u op **toepassing met de bronbestanden van**, en klik vervolgens op **volgende**.  

6.  Op de **Details** pagina, typt u relevante informatie over de toepassing en klik vervolgens op **volgende**.  

7.  Op de **bron** pagina **de bronmap** sectie, klikt u op **Bladeren** gaat u naar en klik vervolgens op de map waarin de bronbestanden van de apparaat-stuurprogramma-toepassing. Klik op **OK**.  

8.  Klik op **Volgende**.  

9. Op de **bestemming** pagina, typ een naam voor de doelmap en klik vervolgens op **volgende**.  

10. Op de **Opdrachtdetails** pagina in de **opdrachtregel** sectie, typt u de opdracht waarmee de installatie op de achtergrond van de toepassing van apparaat-stuurprogramma.  

11. Op de **samenvatting** pagina, controleert u of de instellingen juist zijn en klik vervolgens op **volgende** de apparaat-stuurprogrammatoepassing importeren in de implementatie-Workbench.  

12. Op de **bevestiging** pagina, klikt u op **voltooien**.  

 Nadat de toepassingen in de implementatie-Workbench worden geïmporteerd, kunt u deze aan het implementatieproces met behulp van de juiste logica om ervoor te zorgen dat de toepassing wordt geïnstalleerd alleen indien uitgevoerd op de juiste hardware toevoegen. Er zijn verschillende methoden voor het om dat te bereiken:  

-   Geef de apparaat-stuurprogrammatoepassing als onderdeel van een takenreeks voor implementatie.  

-   Geef de apparaat-stuurprogramma-toepassing in CustomSettings.ini.  

-   Geef de apparaat-stuurprogramma-toepassing in de MDT-database.  

 Elke benadering wordt nader beschreven in de volgende secties beschreven.  

####  <a name="SpecifyDeviceAppTask"></a> De apparaat-stuurprogramma-toepassing opgeven als onderdeel van een Takenreeks  
 De eerste methode voor het toevoegen van een apparaat stuurprogrammatoepassing aan het implementatieproces is het gebruik van een takenreeks toevoegen van stappen voor elke apparaattoepassing-stuurprogramma.  

 Er zijn twee belangrijkste methoden voor het beheren van apparaat stuurprogrammatoepassingen in de takenreeks:  

-   Maak een nieuwe takenreeksgroep voor elk hardwaremodel en voeg vervolgens een query die groep van acties uitvoeren als de computer overeenkomt met een specifieke hardware-type.  

-   Maak een takenreeksgroep voor hardware-specifieke toepassingen en voeg vervolgens de query's voor elke takenreeksactie zodat elke stap van de takenreeks wordt geëvalueerd op basis van het hardwaretype en wordt alleen uitgevoerd als een overeenkomst is gevonden.  

 **Maken van een nieuwe takenreeksgroep voor elk type hardware**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Task reeksen (waarbij *deployment_share* is de naam van de implementatieshare configureren ).  

3.  Klik in het detailvenster op ***task_sequence*** (waarbij *task_sequence* is de takenreeks voor implementatie dat moet worden opgegeven voor het installeren van de toepassing van de stuurprogramma apparaat).  

4.  Klik in het deelvenster Acties op **eigenschappen**.  

5.  In de ***task_sequenceProperties*** in het dialoogvenster op de **Takenreeks** tabblad, in het deelvenster met details gaat u naar de status terugzetten/Windows Update (vooraf toepassingsinstallatie).  

6.  Op de **Takenreeks** tabblad **toevoegen**, en klik vervolgens op **nieuwe groep**.  

     Hiermee maakt u een nieuwe takenreeksgroep in de takenreeks. Gebruik deze nieuwe takenreeksgroep te maken van de stappen voor het installeren van de hardware-specifieke apparaat-stuurprogramma-toepassingen.  

7.  Klik in het detailvenster op **nieuwe groep**.  

8.  Op de **eigenschappen** tabblad, in de **naam** in het vak ***naam_groep*** (waarbij *naam_groep* is de naam van de groep; voor voorbeeld, *Hardware specifieke toepassingen – Dell Computer Corporation*).  

9. Op de **opties** tabblad **toevoegen**, en klik vervolgens op **query uitvoeren op WMI**.  

10. In de **Takenreeksstap WMI groepsvoorwaarde** dialoogvenster typt u de volgende details:  

    -   In de **WMI-naamruimte** in het vak **root\cimv2**.  

    -   In de **WQL-query** typt u een WMI Query Language (WQL) query met de **Win32_ComputerSystem** klasse om ervoor te zorgen dat de toepassing wordt alleen geïnstalleerd voor een specifieke toepassingstype, bijvoorbeeld:  

         **Selecteer \* van Win32_ComputerSystem waar Model zoals *% hardware_model %* en fabrikant zoals *% hardware_manufacturer %***  

         In dit voorbeeld *hardware_model* is de naam van het computermodel (zoals breedtegraad D620) en *hardware_manufacturer* is de naam van de computer maakt (zoals de Dell Corporation).  

         De **%** symbool is een jokerteken die is opgenomen in de namen van de beheerders toestaan om te retourneren van alle computermodellen of fabrikanten met de opgegeven waarde voor ***hardware_model***of ***hardware_manufacturer***.  

     Zie de sectie 'Toevoegen WMI-query's naar reeks stap voorwaarden taak', in de MDT-document voor meer informatie over WMI- en WQL-query's *met behulp van de Microsoft Deployment Toolkit*, en zien [opvragen met WQL](http://msdn.microsoft.com/library/aa392902.aspx).  

11. Klik op **OK** verzenden van de query en klik vervolgens op **OK** wijzigingen aan de takenreeks wilt indienen.  

> [!NOTE]
>  Dit proces moet worden herhaald voor elk hardwaretype op elk apparaat stuurprogrammatoepassing wordt geïnstalleerd.  

 Na de hardware-specifieke taak zijn takenreeksgroepen gemaakt, apparaatstuurprogramma toepassingen kunnen worden toegevoegd aan elke groep.  

 **Toevoegen van stuurprogramma apparaattoepassingen aan takenreeksgroepen van specifieke hardware**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Task reeksen (waarbij *deployment_share* is de naam van de implementatieshare configureren ).  

3.  Klik in het detailvenster op ***task_sequence*** (waarbij *task_sequence* is de takenreeks voor implementatie dat moet worden opgegeven voor het installeren van de toepassing van de stuurprogramma apparaat).  

4.  Klik in het deelvenster Acties op **eigenschappen**.  

5.  In de ***task_sequenceProperties*** in het dialoogvenster, klikt u op de **Takenreeks** tabblad.  

6.  In het detailvenster, gaat u naar de staat herstellen /*hardware_specific_group* (waarbij *hardware_specific_group* is de naam van de specifieke hardware-groep waaraan u de takenreeksstap wordt toegevoegd voor het installeren van de apparaat stuurprogramma-toepassing).  

7.  Op de **Takenreeks** tabblad **toevoegen**, klikt u op **algemene**, en klik vervolgens op **toepassing installeren**.  

     De **toepassing installeren** takenreeksstap wordt weergegeven in het detaildeelvenster.  

8.  Klik in het detailvenster op **toepassing installeren.**  

9. Op de **eigenschappen** tabblad **één toepassing installeren**, en in de **te installeren toepassing** selecteert ***hardware_application***(waarbij *hardware_application* is de toepassing voor het installeren van de specifieke hardware-toepassing).  

> [!NOTE]
>  Dit proces moet worden herhaald voor elk apparaat stuurprogramma-toepassing die moet worden gebruikt tijdens een implementatie.  

#### <a name="specify-the-device-driver-application-in-customsettingsini"></a>Geef de apparaat-stuurprogramma-toepassing in CustomSettings.ini  
 Wanneer de implementatie van een LTI of ZTI begint, is een van de eerste acties moeten worden voltooid de verwerking van de BootStrap.ini en CustomSettings.ini-bestanden. Beide bestanden bevatten regels die kunnen worden gebruikt voor het dynamisch aanpassen van de implementatie.  

 Vanwege de manier waarop die MDT het CustomSettings.ini-bestand verwerkt, kunt u deze toepassingen op basis van bepaalde voorwaarden toevoegen. Deze logica wordt gebruikt voor het toevoegen van stuurprogramma-specifieke apparaattoepassingen tijdens de implementatie op basis van specifieke hardwaretypen. Toepassingen zijn waarnaar wordt verwezen in CustomSettings.ini door de GUID van de toepassing, zich in het bestand Applications.xml in de implementatieshare.  

 **GUID van een geïmporteerde toepassing opzoeken**  

1.  Open de map van het besturingselement in de share van de implementatie van de deployment server — bijvoorbeeld D:\Production implementatie Share\Control.  

2.  Zoek en open het bestand Applications.xml.  

3.  Ga naar de vereiste toepassing.  

4.  GUID van de toepassing vinden door het zoeken naar de regel die is ingesloten in de toepassing `<guid>` tags; bijvoorbeeld `<application guid={c303fa6e-3a4d-425e-8102-77db9310e4d0}>`.  

 Als onderdeel van het initialisatieproces, de LTI-en ZTI informatie verzamelen over de computer waarop deze wordt uitgevoerd. Als onderdeel van dit proces, WMI-query's worden uitgevoerd en de waarden uit de **Win32_ComputerSystem** klasse voor het merk en fabrikant zijn ingevuld als variabelen **zorg %** en **% Model %,** respectievelijk.  

 Deze waarden kunnen worden gebruikt tijdens het verwerken van het CustomSettings.ini-bestand te lezen dynamisch secties van het bestand, afhankelijk van het merk en model gedetecteerd.  Het volgende voorbeeld toont een voorbeeld van het CustomSettings.ini-bestand.  

 **Voorbeeld CustomSettings.ini geconfigureerd voor de installatie van een specifieke Hardware-toepassing**  

```  
[Settings]  
Priority=Make, Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  

[Dell Computer Corporation]  
Subsection=Dell-%Model%  

[Dell-Latitude D620]  
MandatoryApplications001={1D7DF331-47B7-472C-87B3-442597EC2F7D}  

[Dell-Latitude D610]  
MandatoryApplications001={c303fa6e-3a4d-425e-8102-77db9310e4d0}  
```  

 Gebruik de volgende eigenschappen voor toepassingen in CustomSettings.ini opgeven:  

-   **Toepassingen**. Deze eigenschap kan worden gebruikt wanneer de implementatie-beheerders niet wilt aanbieden wizard toepassing als onderdeel van het implementatieproces door te geven **SkipApplications = YES** in CustomSettings.ini.  

-   **MandatoryApplications**. Deze eigenschap kan worden gebruikt als beheerders van de implementatie aanbieden van de wizard toepassing tijdens de implementatie wilt waarmee implementatie engineers aanvullende toepassingen worden geïnstalleerd tijdens de implementatie te selecteren.  

     Als u de wizard toepassing gebruikt zonder de **MandatoryApplications** eigenschap (bijvoorbeeld **SkipApplications = Nee**), overschrijft deze toepassingen die zijn opgegeven door de **toepassingen**  eigenschap.  

     De sampole previousi laat zien hoe u de **zorg %** en **Model %** waarden van variabelen dynamisch manipuleren hoe de lijst met toepassingen wordt gemaakt. De waarden voor het merk en model van elk type hardware kunnen worden gevonden met een van de volgende methoden:  

-   **Het hulpprogramma Systeeminfo**. Het knooppunt Systeemoverzicht in dit hulpprogramma gebruiken om te identificeren de **fabrikant van het systeem** (maken) en **systeemmodel** (model).  

-   **Windows PowerShell**. Gebruik de **Get-WMIObject – klasse Win32_ComputerSystem** cmdlet om te bepalen van het merk en model van de computer.  

-   **Windows Management Instrumentation-opdrachtregel**. Gebruik **CSProduct Get Name, leverancier** om de naam (model) en de leverancier (maken) van de computer te retourneren.  

 **CustomSettings.ini om toe te voegen logica van specifieke hardware wijzigen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  Klik op de **regels** tabblad.  

5.  Gegevens die op dit tabblad is opgeslagen in het CustomSettings.ini-bestand. Wijzigen van de vermeldingen van het bestand CustomSettings.ini om toe te voegen logica voor elk hardwaremodel met een toepassing van de stuurprogramma-specifieke apparaten, zoals beschreven in [opgeven van de toepassing van de stuurprogramma-apparaat als onderdeel van een Takenreeks](#SpecifyDeviceAppTask).  

6.  Klik op **OK** de wijzigingen wilt indienen.  

7.  Klik in het detailvenster op *deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

8.  Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

9. Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

10. Op de **samenvatting** pagina, controleert u of de gegevens juist zijn en klik vervolgens op **volgende**.  

11. Op de **bevestiging** pagina, klikt u op **voltooien**.  

 Standaard worden alle beschikbare toepassingen tijdens een implementatie van de LTI weergegeven in de Wizard Windows-implementatie. Omdat apparaat stuurprogramma-specifieke toepassingen alleen van toepassing op specifieke hardwaretypen zijn, wilt u mogelijk niet worden weergegeven de tijd. Het apparaat stuurprogramma-specifieke toepassingspakket in CustomSettings.ini opgeeft, de toepassing kan worden verborgen met behulp van de **verbergen van de toepassing in de Wizard implementatie** optie in de toepassingsconfiguratie.  

 **Voor het verbergen van een toepassing in de Wizard implementatie**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Applications (waarbij *deployment_share* is de naam van de implementatieshare configureren) .  

3.  Klik in het detailvenster op ***device_driver_application*** (waarbij *device_driver_application* worden verborgen in de Wizard implementatie van de toepassing is).  

4.  Klik in het deelvenster Acties op **eigenschappen**.  

5.  Op de **algemene** tabblad de **verbergen van de toepassing in de Wizard implementatie** selectievakje.  

6.  Klik op **toepassen**, en sluit vervolgens de **eigenschappen** in het dialoogvenster.  

#### <a name="specify-the-device-driver-application-in-the-mdt-db"></a>Geef de apparaat-stuurprogramma-toepassing in de MDT-DB  
 De MDT-database is een databaseversie van het CustomSettings.ini-bestand en kunnen worden opgevraagd tijdens de implementatie voor gegevens die worden gebruikt tijdens de implementatie. Zie voor meer informatie over het gebruik van de MDT-DB 'Selecteren van de methoden voor toepassen van configuratie-instellingen'.  

 Tijdens het opvragen van de MDT-DB tijdens de implementatie, zijn drie methoden beschikbaar voor het identificeren van de doelcomputer:  

-   Zoeken naar de afzonderlijke computer (met behulp van de MAC-adres, de inventaristag, of vergelijkbaar).  

-   Zoeken naar de locatie van de computer (met behulp van de standaard-gateway).  

-   Zoeken naar het merk en model van de computer (met behulp van WMI-fabrikant of het merk en model van query's).  

 Voor elke database-item dat u maakt, kunt u de eigenschappen van de implementatie, toepassingen, opgeven of u wilt gebruiken van Configuration Manager-pakketten en -administrators. Door het maken van vermeldingen met het merk en model in de database, kunt u de vereiste hardware-specifieke stuurprogramma apparaattoepassingen toevoegen.  

 **Vermeldingen maken in de MDT-DB stuurprogrammatoepassingen zodat de installatie van apparaat**  

> [!NOTE]
>  Herhaal dit proces voor elke hardware merk en model waarvoor de toepassing van een apparaat stuurprogramma.  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /**deployment_share**geavanceerde configuratie/Database/merk en Model (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **nieuw**.  

4.  In de **eigenschappen** in het dialoogvenster op de **identiteit** tabblad, in de **zorg** in het vak ***make_name*** (waarbij *make_name*  is de naam van een gemakkelijk te identificeren aan de fabrikant van de doelcomputer wilt koppelen).  

5.  In de **Model** in het vak ***modelnaam*** (waarbij *modelnaam* is de naam van een gemakkelijk te identificeren om te koppelen aan het model van de doelcomputer).  

6.  Op de **toepassingen** tabblad, het toevoegen van elk van de apparaattoepassingen stuurprogramma voor dit model van de hardware vereist.  

## <a name="initiating-mdt-using-windows-deployment-services"></a>Initiëren van MDT met Windows Deployment Services  
 Windows Server 2008 gebruikt Windows Deployment Services als een bijgewerkte en herziene versie van Remote Installation Services, de standaard deployment tool in Windows Server 2003 met SP2. Met Windows Deployment Services, kunt u Windows-besturingssystemen implementeren, met name Windows 7, Windows Server 2008 of latere besturingssystemen, via een netwerk met behulp van een computer netwerk PXE-functionaliteit adapter of boot media.  

 Voordat u Windows Deployment Services implementeert, wordt bepaald welke van de volgende integratieopties best past bij uw omgeving:  

-   Optie 1. Computers opstarten in PXE het proces LTI te initiëren.  

-   Optie 2. Een installatiekopie van het besturingssysteem van de Windows Deployment Services image store implementeren.  

-   Optie 3. Multicast gebruiken met MDT en de Windows Server 2008, Windows Deployment Services-serverfunctie.  

### <a name="option-1-boot-computers-in-pxe-to-initiate-the-lti-process"></a>Optie 1: Boot-Computers in PXE het proces LTI te initiëren  
 Een minimum te beperken van de kosten van het beheren van implementaties van besturingssystemen op basis van het implementatieproces van MDT met Windows Deployment Services in combinatie met Dynamic Host Configuration Protocol. Hiermee verwijdert u de vereiste van het maken en opstartbare media leveren aan elke doelcomputer.  

#### <a name="create-and-import-the-deployment-workbench-windows-pe-image-into-windows-deployment-services"></a>Maken en de implementatie Workbench Windows PE-installatiekopie in Windows Deployment Services importeren  
 Wanneer een nieuwe MDT-implementatieshare maken of wijzigen van een bestaande implementatie van de MDT deelt, kunt u een aangepaste Windows PE-opstartinstallatiekopie. Wanneer de implementatieshare is bijgewerkt, de Windows PE-installatiekopie is automatisch gegenereerd en bijgewerkt met informatie over de implementatieshare, en er geen extra stuurprogramma's of onderdelen die zijn opgegeven tijdens de configuratie van de implementatie-share wordt invoeren.  

 De Windows PE-installatiekopie wordt gegenereerd als een ISO-installatiekopiebestand kunt u naar een CD of DVD schrijven, en als een opstartbare WIM-bestand. U kunt het WIM-bestand importeren aan Windows Deployment Services, zodat computers die kunnen worden opgestart in PXE kunnen downloaden en uitvoeren van de LTI Windows PE-installatiekopie via een netwerk dat wordt gebruikt voor het initialiseren van een installatie.  

 **Maken van opstartbare Windows PE-installatiekopie in de Workbench-implementatie**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

     In de ***deployment_shareProperties*** in het dialoogvenster, klikt u op de **Windows PE *platform* instellingen** tabblad (platform is de architectuur van de Windows PE-installatiekopie worden geconfigureerd).  

4.  In de **Lite Touch installatiekopie opstartinstellingen** gebied, selecteer de **een Lite-Touch opstartbare RAM-schijf ISO-installatiekopie gegenereerd** selectievakje.  

5.  Klik op de **Windows PE *platform* onderdelen** tabblad (waarbij *platform* is de architectuur van de Windows PE-installatiekopie worden geconfigureerd).  

6.  In de **toevoegen van stuurprogramma's** sectie, klikt u op de juiste stuurprogramma typen om op te nemen.  

    > [!NOTE]
    >  Deze stap is niet nodig als Windows PE al de benodigde apparaatstuurprogramma's bevat.  

7.  In de **toevoegen van stuurprogramma's** sectie in het **selectie profiel** , selecteert u het juiste stuurprogramma selectie profiel.  

8.  In de **eigenschappen** in het dialoogvenster, klikt u op **OK**.  

    > [!NOTE]
    >  Deze stap is niet nodig als Windows PE al de benodigde apparaatstuurprogramma's bevat.  

9. Klik in het detailvenster op ***deployment_share*** (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

10. Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

11. Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

12. Op de **samenvatting** pagina, controleert u of de gegevens juist zijn en klik vervolgens op **volgende**.  

13. Op de **bevestiging** pagina, klikt u op **voltooien**.  

     Wanneer dit proces voltooid is, de map opstarten in de implementatieshare bevat een aantal opstartinstallatiekopieën, bijvoorbeeld:  

     D:\Production Deployment Share\Boot\LiteTouchPE_x64.iso  

     D:\Production Deployment Share\Boot\LiteTouchPE_x64.wim  

     D:\Production Deployment Share\Boot\LiteTouchPE_x86.iso  

     D:\Production Deployment Share\Boot\LiteTouchPE_x86.wim  

 U kunt de ISO-bestanden die zijn gegenereerd schrijft rechtstreeks naar een CD of DVD of ze initialiseren van het proces LTI op nieuwe hardware gebruiken. U kunt de opstart-WIM-bestanden importeren in Windows Deployment Services, evenals, zodat nieuwe computers het implementatieproces LTI zonder een fysiek medium kunnen worden geïnitialiseerd.  

 **De Windows PE-installatiekopie importeren in Windows Deployment Services**  

1.  Start de Windows Deployment Services-console en maak verbinding met Windows Deployment Services.  

2.  In de consolestructuur met de rechtermuisknop op **opstartinstallatiekopieën**, en klik vervolgens op **installatiekopie toevoegen**.  

3.  Blader naar de WIM-installatiekopie moeten worden geïmporteerd, bijvoorbeeld D:\Production implementatie Share\Boot\LiteTouchPE_x86.wim.  

4.  Het importproces automatisch leest de metagegevens van de opstartinstallatiekopie, maar de **Installatiekopienaam** en **beschrijving van afbeelding** waarden kunnen worden bewerkt; de **installatiekopie met de naam** is van invloed op de optie opstarten informatie door Windows Opstartbeheer weergegeven wanneer de client in PXE wordt opgestart.  

5.  Wanneer de opstartinstallatiekopie is geïmporteerd, zich een computer met PXE wordt opgestart en ontvangt een antwoord van Windows Deployment Services voor het downloaden van de LTI-installatiekopie en de installatie van een LTI te initiëren.  

 Installeren en configureren van Windows Deployment Services wordt niet in deze handleiding besproken. Zie voor meer informatie over Windows Deployment Services, de [handleiding voor Windows Deployment Services](http://technet.microsoft.com/library/cc265612.aspx).  

#### <a name="use-windows-deployment-services-to-automatically-detect-the-deployment-server"></a>Windows Deployment Services gebruiken om automatisch te detecteren de implementatieserver  
 Een extra optie is alleen beschikbaar wanneer u Windows Deployment Services aan opstartinstallatiekopieën host MDT wanneer de MDT-implementatieshare wordt gehost op dezelfde server als de Windows Deployment Services.  

 Wanneer een PXE-client wordt geladen voor de MDT opstartinstallatiekopie, de naam van de Windows Deployment Services-server die als host fungeert voor de installatiekopie is vastgelegd en geplaatst in de MDTProperty **WDSServer**. U kunt vervolgens verwijzen naar deze eigenschap in de opstartinstallatiekopie BootStrap.ini bestand en in de implementatieshare CustomSettings.ini-bestand door de **DeployRoot** eigenschap. In dat geval resulteert in een client die opstart vanuit Windows Deployment Services automatisch met de implementatieshare gehost op de Windows Deployment Services-server. Hierdoor moet een servernaam opgeven in een configuratiebestand.  

 **De lokale Windows Deployment Services-server als de implementatieserver instellen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*geavanceerde configuratie/Database (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  Klik op de **regels** tabblad.  

     Gegevens die op dit tabblad is opgeslagen in het CustomSettings.ini-bestand.  

5.  Configureer de **DeployRoot** eigenschap te gebruiken de **% WDSServer %** variabele: bijvoorbeeld **DeployRoot =\\\\%WDSServer%\Deployment$**.  

6.  Klik op **Bootstrap.ini bewerken**.  

7.  Configureer BootStrap.ini te gebruiken de **% WDSServer %** eigenschap toe te voegen of te wijzigen van de **DeployRoot** van waarde naar **DeployRoot =\\\\%WDSServer%\Deployment$** .  

8.  Op de **bestand** menu, klikt u op **opslaan** de wijzigingen wilt opslaan naar het bestand BootStrap.ini.  

9. Klik op **OK**.  

     Share van de implementatie moet worden bijgewerkt.  

10. Klik in het detailvenster op **deployment_share** (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

11. Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

12. Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

13. Op de **samenvatting** pagina, controleert u of de gegevens juist zijn en klik vervolgens op **volgende**.  

14. Op de **bevestiging** pagina, klikt u op **voltooien**.  

15. Importeer de bijgewerkte opstart-WIM in Windows Deployment Services.  

### <a name="option-2-deploy-an-operating-system-image-from-the-windows-deployment-services-store"></a>Optie 2: De installatiekopie van een besturingssysteem van de Windows Deployment Services-Store implementeren  
 Als u al van Windows Deployment Services voor implementatie van besturingssystemen gebruikmaakt, de functionaliteit van MDT uitbreiden door te verwijzen naar de installatiekopieën van het besturingssysteem Windows Deployment Services al in gebruik in plaats van een eigen store en om te configureren voor het Windows Deployment Services-implementaties met stuurprogrammabeheer, toepassingsimplementatie, update-installatie, regelverwerking en andere functionaliteit van MDT aanvullen. Nadat MDT is verwijst naar een installatiekopie van het besturingssysteem Windows Deployment Services, kunt u het behandelen als elk besturingssysteem waarmee eenmaal is gestart op een share van de MDT-implementatie.  

 **Als u verwijst naar een installatiekopie van het besturingssysteem Windows Deployment Services**  

> [!NOTE]
>  De volgende stappen vereist dat ten minste één installatiekopie van het besturingssysteem is eerder geïmporteerd in de Windows Deployment Services-server.  

1.  MDT om toegang tot de installatiekopieën van Windows Deployment Services door de volgende bestanden zijn gekopieerd uit de map bronnen van het Windows-medium naar de map C:\Program Files\Microsoft implementatie Toolkit\bin op de Windows Deployment Services-server bijwerken:  

    -   Wdsclientapi.dll  

    -   Wdscsl.dll  

    -   Wdsimage.dll  

    -   Wdstptc.dll (dit is alleen van toepassing bij het kopiëren van de bron-mappen van Windows Server 2008)  

    > [!NOTE]
    >  De bronmap van Windows wordt gebruikt, moet overeenkomen met het platform van het besturingssysteem dat wordt uitgevoerd op de computer waarop de MDT is geïnstalleerd.  

2.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

3.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Operating Systems (waarbij *deployment_share* is de naam van de share van de implementatie naar Configureer).  

4.  Klik in het deelvenster Acties op **importeren besturingssysteem**.  

     De Wizard nieuwe besturingssysteem wordt gestart.  

5.  Op de **Type besturingssysteem** pagina, klikt u op **installatiekopieën van Windows Deployment Services**, en klik vervolgens op **volgende**.  

6.  Op de **WDS-Server** pagina, typ de naam van de Windows Deployment Services-server naar worden verwezen — bijvoorbeeld **WDSSvr001**, en klik vervolgens op **volgende**.  

7.  Op de **samenvatting** pagina, controleert u of de instellingen juist zijn en klik vervolgens op **volgende**.  

8.  Op de **bevestiging** pagina, klikt u op **voltooien**.  

     Alle installatiekopieën beschikbaar op de Windows Deployment Services-server kan nu worden MDT takenreeksen.  

> [!NOTE]
>  Afbeeldingen importeren uit Windows Deployment Services is niet kopiëren de bronbestanden van de Windows Deployment Services-server naar de implementatieshare. MDT blijft de bronbestanden gebruiken vanuit hun oorspronkelijke locatie.  

### <a name="option-3-use-multicasting-with-mdt-and-the-windows-server-2008-windows-deployment-services-role"></a>Optie 3: Gebruik van Multicasting met MDT en de functie Windows Server 2008 Windows Deployment Services  
 Windows Deployment Services is met de release van Windows Server 2008, ter ondersteuning van de implementatie van installatiekopieën via multicast gegevensoverdrachten verbeterd. MDT bevat ook updates voor het integreren van MDT met Windows Deployment Services multicasting.  

 Daarnaast bevat een bijgewerkte Windows Automated Installation Kit (Windows AIK), versie 1.1, Wdsmcast.exe. Hiermee kan multicastsessies handmatig worden toegevoegd en kan de client Wdsmcast.exe om bestanden te kopiëren van een actieve multicast-sessie te starten.  

 Het script LTIApply.wsf gebruikt Wdsmcast.exe bij het toegang verkrijgt de bronbestanden van besturingssysteem van de implementatieshare tot. LTIApply.wsf zoekt Wdsmcast.exe op de implementatie delen in de *deployment_share*\Tools\x86 of de *deployment_share*\Tools\x64 map (waarbij *deployment_share* is de naam van de bestandssysteemmap waarin de implementatieshare), afhankelijk van de versie van Windows PE die wordt uitgevoerd.  

 Wanneer LTIApply.wsf wordt uitgevoerd altijd probeert te openen en het downloaden van een bestaande multicast-stroom WIM afbeeldingen, maar deze wordt terugvallen op een standaard bestandskopie als een multicast-stream niet bestaat.  

> [!NOTE]
>  Deze procedure geldt alleen voor WIM-bestanden.  

 De server-vereisten voor implementatie voor te bereiden voor multicasting van MDT zijn:  

-   De implementatieserver moet worden gebruik van WindowsServer 2008 of hoger  

-   De functie Windows Deployment Services moet worden geïnstalleerd van de console Serverbeheer  

-   1.1 van de Windows AIK voor Windows Server 2008 moet worden geïnstalleerd.  

-   MDT moet worden geïnstalleerd.  

-   Als bij een implementatie met MDT, ten minste één besturingssysteem WIM-installatiekopie mag zijn geïmporteerd, hetzij als een volledige set van bronbestanden of als een aangepaste installatiekopie met setup-bestanden  

> [!NOTE]
>  Het is belangrijk dat u de nieuwste versie van Windows AIK voor multicasting; het exemplaar van Windows PE is opgenomen in eerdere versies van Windows AIK, bijvoorbeeld Windows AIK 1.0, biedt geen ondersteuning voor het downloaden van een multicast-server.  

 **MDT voor multicasting van een bestaande implementatieshare configureren**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **Workbench-implementatie**  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share* (waarbij *deployment_share* is de naam van de implementatieshare configureren).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  Op de **algemene** tabblad de **multicast inschakelen voor deze implementatieshare (vereist Windows Server 2008, Windows Deployment Services)** selectievakje.  

5.  Klik op **OK**.  

6.  Klik in het deelvenster Acties op **Update Deployment Share**.  

     De Wizard Update Deployment Share wordt gestart.  

7.  Op de **opties** pagina, selecteer de gewenste opties voor het bijwerken van de implementatieshare en klik vervolgens op **volgende**.  

8.  Op de **samenvatting** pagina, controleert u of de gegevens juist zijn en klik vervolgens op **volgende**.  

9. Op de **bevestiging** pagina, klikt u op **voltooien**.  

 De implementatieshare is nu geconfigureerd voor multicast-overdracht gebruikt Windows Deployment Services.  

 Dit proces maakt een automatische conversie Windows Deployment Services multicast-overdracht die rechtstreeks gebruikmaakt van de bestaande MDT-implementatieshare. MDT maakt geen geplande Cast gegevensoverdrachten. Let ook op dat geen extra afbeeldingen in Windows Deployment Services worden ingevoerd en dat het is niet mogelijk om multicast te gebruiken voor installatiekopieën, omdat de multicast-client niet kan geladen pas worden nadat Windows PE wordt uitgevoerd.  

 **Als u wilt controleren of de multicast-overdracht is gegenereerd in Windows Deployment Services**  

1.  Klik op **Start**, wijs **Systeembeheer**, en klik vervolgens op **Windows Deployment Services**.  

2.  In de consolestructuur van de Windows Deployment Services met de rechtermuisknop op **Servers**, en klik vervolgens op **Server toevoegen**.  

3.  In de **Servers toevoegen (s)** in het dialoogvenster, klikt u op **lokale computer**, en klik vervolgens op **OK**.  

4.  Klik in de consolestructuur van de Windows Deployment Services op **Servers**, klikt u vervolgens op ***servernaam*** (waarbij *servernaam* is de naam van de computer met Windows-implementatie Services). Klik op **Multicast gegevensoverdrachten**.  

5.  In het detailvenster de verzending van een nieuwe automatische conversie voor de implementatieshare wordt weergegeven, bijvoorbeeld **implementatie BDD delen $**.  

6.  Controleer de status van de **BDD bestandsshare-implementatie$** automatisch Cast verzending is ingesteld op **Active**.  

 Nadat een computer is geïmplementeerd, moet u controleren dat het besturingssysteem van een multicast-overdracht door in het bestand BDD.log in de map \Windows\Temp\DeploymentLogs is gedownload.  

 Er worden twee vermeldingen in de map met logbestanden, die beide begint met **multicast-overdracht**; controleren om te controleren of de overdracht geslaagd is. Zie de sectie 'Inschakelen Windows Deployment Services Multicast implementatie voor LTI-implementaties', in de MDT-document voor meer informatie over multicast gegevensoverdrachten met MDT en de Windows Deployment Services *met behulp van de Microsoft Deployment Toolkit*.  

## <a name="performing-staged-deployments-using-mdt-oem-preload"></a>Implementaties met MDT (OEM Preload) uitvoeren met geplaatste  
 In veel organisaties worden computers geladen met de installatiekopie van het besturingssysteem vóór de implementatie naar het productienetwerk. In sommige gevallen wordt bij het laden van de installatiekopie van het besturingssysteem uitgevoerd door een team binnen de organisatie die verantwoordelijk is voor het bouwen van de computers in een testomgeving. In andere gevallen belden bij het laden van de installatiekopie van het besturingssysteem wordt uitgevoerd door de leverancier van de computerhardware, ook wel bekend als een *fabrikant* (OEM).  

> [!NOTE]
>  Het vooraf laden OEM-proces wordt ondersteund in MDT enkel voor implementaties die worden uitgevoerd met behulp van LTI. Configuration Manager, de functie voorbereide media gebruiken.  

### <a name="overview-of-the-oem-preload-process-in-mdt"></a>Overzicht van het vooraf laden OEM-proces in MDT  
 Het vooraf laden OEM-proces is onderverdeeld in drie fasen:  

-   **Fase 1**. Maak een media-installatiekopie van de referentiecomputer moet worden toegepast in de testomgeving.  

-   **Fase 2**. De referentie-installatiekopie van toepassing op de doelcomputer in een testomgeving.  

-   **Fase 3**. Volledige implementatie van de doelcomputer in de productieomgeving.  

 Fase 1 en fase 3 worden doorgaans uitgevoerd door de organisatie van de implementatie. Afhankelijk van het gebruik van het vooraf laden OEM-proces in de organisatie worden fase 2 uitgevoerd door de organisatie of door de leverancier van de computerhardware die de computers levert. Als de organisatie fase 2 wordt uitgevoerd, klikt u vervolgens is de testomgeving binnen de organisatie. Als een OEM fase 2 wordt uitgevoerd, klikt u vervolgens is de testomgeving in de OEM-omgeving.  

#### <a name="overview-of-mdt-configuration-files-in-the-oem-preload-process"></a>Overzicht van de MDT-configuratiebestanden in het vooraf laden OEM-proces  
 Afzonderlijke MDT-configuratiebestanden (CustomSettings.ini en Bootstrap.ini) worden gebruikt door de takenreeksen die wordt uitgevoerd tijdens de fase 1 en stap 3 van het vooraf laden OEM-proces. Beide configuratiebestanden bevinden zich echter tegelijkertijd in structuren van de andere map.  

 In de eerste fase worden de configuratiebestanden die worden gebruikt tijdens het maken van de referentiecomputer en worden opgeslagen in de map die specifiek zijn voor de takenreeks die wordt gebruikt in de desbetreffende fase. De configuratiebestanden in de derde en de laatste fase van het vooraf laden OEM-proces worden opgeslagen in de map die specifiek is voor de takenreeks die wordt gebruikt in de desbetreffende fase.  

 Zorg ervoor dat wijzigingen in het configuratiebestand zijn aangebracht die overeenkomt met de juiste takenreeks in elke fase van de preload proces OEM bij het doorvoeren van wijzigingen in de configuratiebestanden.  

#### <a name="overview-of-mdt-log-files-in-the-oem-preload-process"></a>Overzicht van de MDT-logboekbestanden in de OEM Preload-proces  
 Afzonderlijke MDT-logboekbestanden worden gegenereerd tijdens de fase 1 en stap 3 van het vooraf laden OEM-proces:  

-   De MDT-logboekbestanden voor fase 1 worden opgeslagen in de mappen C:\MININT en C:\SMSTSLog.  

-   De MDT-logboekbestanden voor fase 3 worden opgeslagen in de map %WINDIR%\System32\CCM\Logs voor x86 86 implementaties of in de map %WINDIR%\SysWow64\CCM\Logs voor x64 64-implementaties.  

 Gebruik de juiste map wanneer vaststellen of het oplossen van problemen met MDT-gerelateerde implementatie.  

### <a name="staged-deployments-using-lti"></a>Gefaseerde implementaties met LTI  
 Voor implementaties van LTI, uitvoeren wordt gebruikt door de OEM preload proces een *verwisselbare media (Media)* share implementatietype. Andere implementatietypen voor de share worden niet ondersteund voor het vooraf laden OEM-proces.  

 Als u wilt uitvoeren van het vooraf laden OEM-proces, een takenreeks maken op basis van de sjabloon Litetouch OEM-Takenreeks taak sequence, naast de takenreeksen die worden gebruikt voor het implementeren van het beoogde besturingssysteem. Vervolgens maakt u een *verwisselbare media (Media)* implementatieshare die uiteindelijk een ISO-bestand van de implementatie-inhoud, specifiek het LiteTouchPE_x86.iso-bestand of de bestanden LiteTouchPE_x64.iso-bestand maakt (op basis van het doel computer van processor-platform). Het implementatieproces van de share-update maakt ook een mapstructuur die kan worden gebruikt voor het maken van media Universal Disk Format.  

#### <a name="lti-oem-preload-processphase-1-create-a-media-based-image"></a>Vooraf OEM-proces LTI: fase 1: Een installatiekopie op basis van Media maken  
 De implementatie-organisatie voert de eerste fase in het vooraf laden OEM-proces. Het uiteindelijke product van deze fase wordt een opstartbare installatiekopie (zoals een ISO-bestand) of media (zoals een DVD) die wordt verzonden naar de OEM of bij de faseringsomgeving binnen de organisatie van de implementatie. De meeste van deze stappen worden uitgevoerd in de implementatie-Workbench.  

 **Om een installatiekopie op basis van media voor levering aan de OEM of de faseringsomgeving binnen de organisatie van de implementatie te maken**  

1.  Vul de volgende knooppunten voor de implementatieshare in de Workbench-implementatie:  

    -   Besturingssystemen  

    -   Toepassingen  

    -   Pakketten  

    -   Out of Box stuurprogramma 's  

     Zie de sectie 'Beheren implementatie Shares in de implementatie-Workbench', in de MDT-document voor meer informatie over het uitvoeren van deze stap *met behulp van de Microsoft Deployment Toolkit*.  

2.  Een nieuwe takenreeks maken op basis van de sjabloon Litetouch OEM-Takenreeks taak volgorde in de implementatie-Workbench.  

     Zie de sectie 'Configureren Taakreeksen in de implementatie-Workbench', in de MDT-document voor meer informatie over het uitvoeren van deze stap *met behulp van de Microsoft Deployment Toolkit*.  

3.  Een of meer takenreeksen maken die wordt gebruikt voor het beoogde besturingssysteem op de doelcomputer na de implementatie in de productieomgeving implementeren.  

     Zie de sectie 'Configureren Taakreeksen in de implementatie-Workbench', in de MDT-document voor meer informatie over het uitvoeren van deze stap *met behulp van de Microsoft Deployment Toolkit*.  

4.  Maak een selectie-profiel met de toepassingen, besturingssystemen, stuurprogramma's, pakketten en takenreeksen die zijn vereist voor de OEM-implementatie.  

     Zie de sectie 'Selectie profielen beheren', in de MDT-document voor meer informatie over het uitvoeren van deze stap *met behulp van de Microsoft Deployment Toolkit*.  

5.  Maakt media voor implementatie.  

     Zie de sectie 'Beheren LTI Implementatiemedia', in de MDT-document voor meer informatie over het uitvoeren van deze stap *met behulp van de Microsoft Deployment Toolkit*.  

6.  Bijwerken van de media voor implementatie in de Workbench-implementatie in de vorige stap hebt gemaakt.  

     Wanneer u de media voor implementatie van bijwerkt, wordt de implementatie-Workbench het LiteTouchMedia.iso-bestand. Zie de sectie 'Beheren LTI Implementatiemedia', in de MDT-document voor meer informatie over het uitvoeren van deze stap *met behulp van de Microsoft Deployment Toolkit*.  

7.  Branden van een DVD van het LiteTouchMedia.iso-bestand in de vorige stap hebt gemaakt.  

    > [!NOTE]
    >  Deze stap is niet nodig als het leveren van het ISO-bestand naar de OEM of naar de faseringsomgeving van de organisatie.  

8.  Leveren de ISO-bestand of de DVD naar de OEM of naar de faseringsomgeving van de organisatie.  

#### <a name="lti-oem-preload-processphase-2-apply-the-image-to-the-target-computer"></a>Vooraf OEM-proces LTI: fase 2: De installatiekopie op de doelcomputer toepassen  
 De tweede fase van het vooraf laden OEM-proces wordt uitgevoerd door de OEM of door het implementatieteam in de faseringsomgeving van de organisatie van de implementatie. De ISO-bestand of -DVD in stap 1 hebt gemaakt tijdens deze fase van het proces wordt toegepast op de doelcomputers. Het product van deze fase is de afbeelding die is geïmplementeerd op de doelcomputers, zodat ze gereed voor implementatie in de productieomgeving zijn.  

 **De installatiekopie van het toepassen op de doelcomputers**  

1.  Start een doelcomputer met de media die in de fase 1 hebt gemaakt.  

     Windows PE wordt gestart en vervolgens de Wizard Windows-implementatie wordt gestart.  

2.  Klik in de Wizard implementatie van Windows op de **Takenreeks van de OEM-voorinstallatie voor Faseringsomgeving** takenreeks.  

     De takenreeks wordt gestart en de inhoud van de opstartbare media worden gekopieerd naar de lokale harde schijf van de doelcomputer.  

3.  Wanneer de Wizard Windows-implementatie is voltooid voor de **Takenreeks van de OEM-voorinstallatie voor Faseringsomgeving** takenreeks, de harde schijf is gereed voor het starten van de rest van het implementatieproces door te voeren van de Windows De implementatiewizard voor de andere takenreeksen die worden gebruikt om het besturingssysteem te implementeren.  

     De **Takenreeks van de OEM-voorinstallatie voor Faseringsomgeving** takenreeks is verantwoordelijk voor het implementeren van de installatiekopie op de doelcomputer en het starten van de LTI-proces. De Wizard Windows-implementatie kan geen tweede keer worden uitgevoerd van de takenreeksen die wordt gebruikt voor het implementeren van het besturingssysteem op de doelcomputer wordt gestart.  

4.  Kloon van de inhoud van de eerste harde schijf met zoveel doelcomputers in de testomgeving zoals vereist.  

5.  De doelcomputers worden gedownload naar de productieomgeving voor implementatie.  

#### <a name="lti-oem-preload-processphase-3-complete-target-computer-deployment"></a>LTI OEM Preload-proces, stap 3: Doel Computerimplementatie voltooid  
 De derde fase van het vooraf laden OEM-proces wordt uitgevoerd in de productieomgeving van de organisatie van de implementatie. Tijdens deze fase van het proces wordt de doelcomputer wordt gestart en de installatiekopie opstartbare media, op de harde schijf in de testomgeving geplaatst tijdens de vorige fase wordt gestart.  

 **Implementatie van de doelcomputers in de productieomgeving voltooien**  

1.  Start de doelcomputer.  

     Windows PE wordt gestart en vervolgens de Wizard Windows-implementatie wordt gestart.  

2.  Voltooi de Wizard implementatie van Windows met de specifieke configuratie-informatie voor elke doelcomputer.  

     Zie de sectie 'Waarop de Wizard implementatie', in de MDT-document voor meer informatie over deze stap is voltooid, *met behulp van de Microsoft Deployment Toolkit*.  

 Wanneer deze fase voltooid is, wordt de doelcomputer is klaar voor gebruik in de productieomgeving.  

## <a name="using-windows-powershell-to-perform-common-tasks"></a>Veelvoorkomende taken uitvoeren met behulp van Windows PowerShell  
 De MDT-beheertaken in de Workbench-implementatie worden uitgevoerd door de onderliggende Windows PowerShell-cmdlets die u gebruiken kunt voor het automatiseren van beheertaken, zoals die in de volgende secties.  

 U kunt MDT beheer automatiseren door de volgende stappen uit te voeren:  

-   Maak een nieuwe implementatieshare zoals beschreven in [maken van een nieuwe Deployment Share](#CreateNewDeployShare).  

-   Maak een map op een implementatieshare, zoals beschreven in [maken van een map](#CreateFolder).  

-   Een map verwijderen van een implementatieshare, zoals beschreven in [als u een map](#DeleteFolder).  

-   Een apparaatstuurprogramma importeren in een share-implementatie, zoals beschreven in [importeren van een apparaatstuurprogramma](#ImportDeviceDriver).  

-   Verwijderen van een stuurprogramma van een implementatieshare zoals beschreven in [verwijderen van een apparaatstuurprogramma](#DeleteDeviceDriver).  

-   Een besturingssysteempakket importeren in een share van de implementatie, zoals beschreven in [importeren van een besturingssysteempakket](#ImportOpSysPackage).  

-   Een besturingssysteempakket verwijderen uit een implementatieshare, zoals beschreven in [verwijderen van een besturingssysteempakket](#DeleteOpSysPackage).  

-   Importeren van een besturingssysteem in een implementatieshare zoals beschreven in [importeren van een besturingssysteem](#ImportOpSys).  

-   Verwijderen van een besturingssysteem van een implementatieshare, zoals beschreven in [verwijderen van een besturingssysteem](#DeleteOpSys).  

-   Een toepassing maken in een share van de implementatie, zoals beschreven in [maken van een toepassing](#CreateApplication).  

-   Een toepassing verwijderen van een implementatieshare, zoals beschreven in [verwijderen van een toepassing](#DeleteApplication).  

-   Maak een takenreeks op een implementatieshare zoals beschreven in [maken van een Takenreeks](#CreateTaskSequence).  

-   Verwijderen van een takenreeks van een implementatieshare, zoals beschreven in [verwijderen van een Takenreeks](#DeleteTaskSequence).  

-   Maak een MDT-database, zoals beschreven in [maken van een database MDT](#CreateMDTDB).  

-   Een profiel voor een selectie maken zoals beschreven in [maken van een profiel selectie](#CreateSelectProfile).  

-   Een implementatieshare bijwerken zoals beschreven in [bijwerken van een Deployment Share](#UpdatingDeployShare).  

-   Maak een share van de gekoppelde implementatie, zoals beschreven in [maken van een gekoppelde Deployment Share](#CreateLinkedDeployShare).  

-   Een gekoppelde implementatieshare bijwerken zoals beschreven in [bijwerken van een gekoppelde Deployment Share](#UpdatingLinkedDeployShare).  

-   Verwijderen van een gekoppelde implementatieshare zoals beschreven in [verwijderen van een gekoppelde Deployment Share](#DeleteLinkedDeployShare).  

-   Maken van media voor implementatie, zoals beschreven in [maken van Media](#CreateMedia).  

-   Implementatiemedia genereren, zoals beschreven in [genereren Media](#GenerateMedia).  

-   Verwijderen van media voor implementatie, zoals beschreven in [Media verwijderen](#DeleteMedia).  

###  <a name="CreateNewDeployShare"></a> Maken van een nieuwe Implementatieshare  
 De volgende Windows PowerShell-opdrachten maakt een nieuwe implementatieshare op D:\Production Deployment Share met de naam *productie$*. De nieuwe implementatieshare wordt weergegeven in de implementatie-Workbench als productie.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "D:\Production Deployment Share" -Description "Production" -NetworkPath "\\Deployment_Server\Production$" -Verbose | add-MDTPersistentDrive -Verbose  
    ```  

###  <a name="CreateFolder"></a> Een map te maken  
 De volgende Windows PowerShell-opdrachten maken van een map Adobe in de consolestructuur van de implementatie-Workbench op implementatie-Workbench\/Implementatieshares\/productie\/toepassingen.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Applications" -enable "True" -Name "Adobe" -Comments "This folder contains Adobe software" -ItemType "folder" -Verbose remove-psdrive DS001 -Verbose  
    ```  

    > [!NOTE]
    >  Toe te voegen '`remove-psdrive`' aan het script zorgt u ervoor dat de achtergrondproces is voltooid voordat u doorgaat.  

###  <a name="DeleteFolder"></a> Als u een map  
 De volgende Windows PowerShell-opdrachten verwijderen de implementatie-Workbench\/Implementatieshares\/productie\/toepassingen\/Adobe map.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Remove-item -path "DS002:\Applications\Adobe" -Verbose  
    ```  

> [!NOTE]
>  Het script mislukt als de map niet leeg zijn is.  

###  <a name="ImportDeviceDriver"></a> Een apparaatstuurprogramma importeren  
 De volgende Windows PowerShell-opdrachten wordt de Dell 2407 WFP monitor apparaatstuurprogramma's importeren in de share van de productie-implementatie.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtdriver -path "DS002:\Out-of-Box Drivers\Monitor" -SourcePath "D:\Drivers\Dell\2407 WFP" -Verbose  
    ```  

###  <a name="DeleteDeviceDriver"></a> Verwijderen van een apparaatstuurprogramma  
 De volgende Windows PowerShell-opdracht verwijdert het stuurprogramma van de monitor Dell 2407 WFP uit de share van de productie-implementatie.  

```  
Remove-item -path "DS002:\Out-of-Box Drivers\Dell Inc. Monitor 2407WFP.INF 1.0" -Verbose  
```  

###  <a name="ImportOpSysPackage"></a> Een besturingssysteempakket importeren  
 De volgende Windows PowerShell-opdrachten importeren alle besturingssysteempakketten weergegeven onder D:\\Updates\\Microsoft\\Vista. Deze pakketten van het besturingssysteem wordt opgeslagen in de implementatieshare productie, dat zich in D: bevindt\\delen van productie-implementatie.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtpackage -path "DS002:\Packages" -SourcePath "D:\Updates\Microsoft\Vista" -Verbose  
    ```  

###  <a name="DeleteOpSysPackage"></a> Verwijderen van een besturingssysteem-pakket  
 De volgende Windows PowerShell-opdracht verwijdert het opgegeven besturingssysteem-pakket uit de share van de productie-implementatie.  

```  
Remove-item -path "DS002:\Packages\Package_1_for_KB940105 neutral x86 6.0.1.0 KB940105" -Verbose  
```  

###  <a name="ImportOpSys"></a> Importeren van een besturingssysteem  
 De volgende Windows PowerShell-opdrachten importeren van het besturingssysteem Windows Vista zich in D:\\besturingssystemen\\Windows Vista x86. Het besturingssysteem wordt opgeslagen in de implementatieshare productie, dat zich in D: bevindt\\delen van productie-implementatie.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtoperatingsystem -path "DS002:\Operating Systems" -SourcePath "D:\Operating Systems\Windows Vista x86" -DestinationFolder "Windows Vista x86" -Verbose  
    ```  

###  <a name="DeleteOpSys"></a> Verwijderen van een besturingssysteem  
 De volgende Windows PowerShell-opdracht verwijdert het besturingssysteem Windows Vista HOMEBASIC uit de share van de productie-implementatie.  

```  
Remove-item -path "DS002:\Operating Systems\Windows Vista HOMEBASIC in Windows Vista x86 install.wim" -Verbose  
```  

###  <a name="CreateApplication"></a> Maken van een toepassing  
 De volgende Windows PowerShell-opdrachten de Adobe Reader 9 toepassing maken met de bronbestanden van D:\\Software\\Adobe\\Reader 9. De toepassing wordt opgeslagen in de implementatieshare productie, dat zich in D: bevindt\\delen van productie-implementatie.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-MDTApplication -path "DS002:\Applications" -enable "True" -Name "Adobe Reader 9" -ShortName "Reader" -Version "9" -Publisher "Adobe" -Language "" -CommandLine "setup.exe" -WorkingDirectory ".\Applications\Adobe Reader 9" -ApplicationSourcePath "D:\Software\Adobe\Reader 9" -DestinationFolder "Adobe Reader 9" -Source ".\Applications\Adobe Reader 9" -Verbose  
    ```  

###  <a name="DeleteApplication"></a> Verwijderen van een toepassing  
 De volgende Windows PowerShell-opdracht worden de Adobe Reader 9-toepassing uit de share van de productie-implementatie verwijderd.  

```  
Remove-item -path "DS002:\Applications\Adobe Reader 9" -Verbose  
```  

###  <a name="CreateTaskSequence"></a> Een Takenreeks maken  
 De volgende Windows PowerShell-opdrachten maken de **Windows Vista productie bouwen** takenreeks in de implementatieshare productie, dat in D: bevindt zich\\delen van productie-implementatie.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdttasksequence -path "DS002:\Task Sequences" -Name "Windows Vista Business Production Build" -Template "Client.xml" -Comments "Approved for use in the production environment.  This task sequence uses the Standard Client task sequence template" -ID "Vista_Ref" -Version "1.0" -OperatingSystemPath "DS002:\Operating Systems\Windows Vista BUSINESS in Windows Vista x86 install.wim" -FullName "Fabrikam User" -OrgName "Fabrikam" -HomePage "http://www.Fabrikam.com" -AdminPassword "secure_password" -Verbose  
    ```  

###  <a name="DeleteTaskSequence"></a> Verwijderen van een Takenreeks  
 De volgende Windows PowerShell-opdracht verwijdert u de **Windows Vista productie bouwen** takenreeks van de share van de productie-implementatie.  

```  
Remove-item -path "DS002:\Task Sequences\Windows Vista Business Production Build" -force -Verbose  
```  

###  <a name="CreateMDTDB"></a> Maken van een MDT-DB  
 De volgende Windows PowerShell-opdrachten een nieuwe MDT-database maken op de *implementatie\_server* server voor de share van de productie-implementatie. Verbinding met de database worden via TCP\/IP.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-MDTDatabase -path "DS002:" -SQLServer "DeploymentServer" -Netlib "DBMSSOCN" -Database "MDT2010" -SQLShare "DB_Connect" -Force -Verbose  
    ```  

###  <a name="CreateSelectProfile"></a> Maken van een profiel selecteren  
 De volgende Windows PowerShell-opdrachten maken een profiel voor selectie van nieuwe toepassingen.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Selection Profiles" -enable "True" -Name "Applications" -Comments "" -Definition "<SelectionProfile><Include path="Applications" /></SelectionProfile>" -ReadOnly "False" -Verbose  
    ```  

###  <a name="UpdatingDeployShare"></a> Een Implementatieshare bijwerken  
 De volgende Windows PowerShell-opdrachten update de implementatieshare productie, dat zich in D: bevindt\\delen van productie-implementatie.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   Update\-MDTDeploymentShare \-pad ' DS002: " \-Uitgebreide  

###  <a name="CreateLinkedDeployShare"></a> Maken van een gekoppelde Implementatieshare  
 De volgende Windows PowerShell-opdrachten maken een implementatieshare die is gekoppeld aan de share van de productie-implementatie en bevindt zich onder de \\ \\ *externe\_server\_naam* \\Implementatie$-share. Alles selectie profiel wordt gebruikt om te bepalen welke inhoud wordt gerepliceerd naar de share van de gekoppelde implementatie. Inhoud van de share van de productie-implementatie wordt samengevoegd met inhoud die al bestaat in de \\ \\ *externe\_server\_naam*\\implementatie$-share.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Linked Deployment Shares" -enable "True" -Name "LINKED001" -Comments "" -Root "\\RemoteServerName\Deployment$" -SelectionProfile "Everything" -Replace "False" -Verbose  
    ```  

###  <a name="UpdatingLinkedDeployShare"></a> Een gekoppelde Implementatieshare bijwerken  
 De volgende Windows PowerShell-opdrachten update de implementatieshare LINKED001.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Replicate-MDTContent -path "DS002:\Linked Deployment Shares\LINKED001" -Verbose  
    ```  

###  <a name="DeleteLinkedDeployShare"></a> Verwijderen van een gekoppelde Implementatieshare  
 De volgende Windows PowerShell-opdrachten verwijderen de implementatieshare LINKED001.  

-   Add\-PSSnapIn Microsoft.BDD.PSSnapIn  

-   ```  
    Remove-item -path "DS002:\Linked Deployment Shares\LINKED001" -Verbose  
    ```  

###  <a name="CreateMedia"></a> Media maken  
 De volgende Windows PowerShell-opdrachten maken een bronmap met inhoud die worden gebruikt voor het maken van opstartbare media. De share van de productie-implementatie wordt gebruikt als de bron. Alles selectie profiel bepaalt welke inhoud wordt geplaatst in de map van de media-inhoud. Het bestand LiteTouchMedia.iso wordt gemaakt wanneer de media wordt gegenereerd. De media wordt x86- en x64 platforms ondersteunen.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Media" -enable "True" -Name "MEDIA001" -Comments "some comment here" -Root "D:\Media" -SelectionProfile "Everything" -SupportX86 "True" -SupportX64 "True" -GenerateISO "True" -ISOName "LiteTouchMedia.iso" -Verbose  
    ```  

-   ```  
    New-PSDrive -Name "MEDIA001" -PSProvider "MDTProvider" -Root "D:\Media\Content" -Description "Embedded media deployment share" -Force -Verbose  
    ```  

###  <a name="GenerateMedia"></a> Genereren van Media  
 De volgende Windows PowerShell-opdrachten maken het bestand LiteTouchMedia.iso in D:\\Media die de inhoud van de bronmap voor MEDIA001 media gebruikt.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Generate-MDTMedia -path "DS002:\Media\MEDIA001" -Verbose  
    ```  

###  <a name="DeleteMedia"></a> Media verwijderen  
 De volgende Windows PowerShell-opdracht verwijdert de media MEDIA001 uit de share van de productie-implementatie.  

```  
Remove-item -path "DS002:\Media\MEDIA001" -Verbos  
```  

## <a name="delaying-domain-join-to-avoid-application-of-group-policy-objects"></a>Domeinlidmaatschap vertragen om te voorkomen dat de toepassing van groepsbeleidsobjecten  
 Groepsbeleid is een uitgebreide en flexibele technologie bieden de mogelijkheid om een groot aantal computer- en gebruikersobjecten Active Directory Domain Services (AD DS) via een gecentraliseerde, een-op-veel-model efficiënt te beheren. Instellingen voor Groepsbeleid zijn opgenomen in een groepsbeleidsobject (GPO) en gekoppeld aan een of meer AD DS-containers, sites, domeinen en organisatie-eenheden (OE's).  

 Sommige organisaties hebben de instellingen voor Groepsbeleid die zijn beperkende en problemen kunnen veroorzaken tijdens implementaties van besturingssystemen. De volgende instellingen voor Groepsbeleid kunnen bijvoorbeeld een geautomatiseerde aanmeldingsproces onderbreken:  

-   Beperkingen voor automatische aanmelding  

-   Administrator-account wijzigen  

-   Juridische banner en bijschriften  

-   Beperkend beveiligingsbeleid (bijvoorbeeld de gespecialiseerde beveiliging – beperkte functionaliteit [SSLF] beleid)  

 Een optie te overwinnen van de problemen die een groepsbeleidsobject ertoe leiden tijdens de implementatie dat kan is het zo laat mogelijk in het implementatieproces de computer toevoegen aan het domein. Deze koppeling kan worden gedaan met behulp van een aangepaste takenreeksstap waarvoor de ZTIDomainJoin.wsf-script wordt uitgevoerd.  

 Als u wilt deelnemen aan de doelcomputer aan het domein, de ZTIDomainJoin.wsf script maakt gebruik van de **DomainAdmin**, **DomainAdminDomain**, **DomainAdminPassword**,  **JoinDomain**, en **MachineObjectOU** eigenschappen. U kunt deze eigenschappen met behulp van de Wizard Windows Deployment, regels voor het delen van implementatie, de DB MDT en Configuration Manager-computer- en verzameling regels declareren. Het account dat wordt gebruikt, moet de benodigde rechten voor het maken en verwijderen van computerobjecten in het domein hebben.  

 Het script ZTIConfigure.wsf updates worden meestal het bestand Unattend.xml of Unattend.txt met de waarden die deze eigenschappen opgeeft. Deze instellingen vervolgens door het Windows-installatieprogramma zijn geparseerd en het systeem probeert te koppelen aan het domein vroeg in het implementatieproces. Dit leidt tot de doelcomputer onderwerpen naar de instellingen die zijn opgegeven in domein GPO's en kan mogelijk leiden tot het implementatieproces mislukken.  

 Als u wilt opzettelijk vertraging de doelcomputer toevoegen aan het domein tijdens de implementatie, kunt u bepaalde elementen verwijderen uit het bestand Unattend.xml. Het script ZTIConfigure.wsf overslaan eigenschappen schrijven naar het bestand Unattend.XML als de gekoppelde eigenschap-element in het bestand ontbreekt.  

> [!NOTE]
>  Deze tijdelijke voorbeeld oplossing is alleen geldig bij het implementeren van de besturingssystemen Windows 7, Windows Server 2008 of Windows Server 2008 R2.  

 **Het bestand Unattend.XML voorbereiden, zodat de doelcomputer niet probeert aan het domein tijdens Windows Setup**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Task reeksen /*task_sequence* (waarbij *deployment_share*is de naam van de implementatieshare en *task_sequence* is de naam van de takenreeks wordt geconfigureerd).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  Op de **OS-Info** tabblad **Unattend.xml bewerken**.  

     Windows System Image Manager (Windows SIM) wordt gestart.  

5.  In de **antwoordbestand** deelvenster, gaat u naar **4 specialize/identificatie/referenties**. Met de rechtermuisknop op **referenties**, en klik vervolgens op **verwijderen**.  

6.  Klik op **Ja**.  

7.  Sla het antwoordbestand en sluit Windows SIM.  

8.  Klik op **OK** op de takenreeks **eigenschappen** in het dialoogvenster.  

 Met de `Credentials` elementen ontbreekt in het bestand unattend.xml, het script ZTIConfigure.wsf is niet kunnen worden ingevuld in het bestand Unattend.xml, waardoor Windows Setup probeert aan het domein de gegevens voor domeindeelname.  

 **Stap in een takenreeks die de doelcomputer aan het domein koppelt toevoegen**  

1.  Klik op **Start**, en wijs vervolgens **alle programma's**. Wijs **Microsoft Deployment Toolkit**, en klik vervolgens op **implementatie-Workbench**.  

2.  In de consolestructuur van de implementatie-Workbench gaat u naar de implementatie Workbench/Implementatieshares /*deployment_share*/Task reeksen /*task_sequence* (waarbij *deployment_share*is de naam van de implementatieshare en *task_sequence* is de naam van de takenreeks wordt geconfigureerd).  

3.  Klik in het deelvenster Acties op **eigenschappen**.  

4.  Op de **Takenreeks** tabblad, gaat u naar en vouw het knooppunt status herstellen.  

5.  Controleer de **herstellen uit domein** takenreeksstap aanwezig is. Zo ja, ga dan naar stap 9.  

6.  In de takenreeks **eigenschappen** in het dialoogvenster, klikt u op **toevoegen**, gaat u naar **instellingen**, en klik op **herstellen uit domein**.  

7.  Voeg de **herstellen uit domein** takenreeksstap naar de takenreekseditor. Controleer of de stap in de gewenste locatie in de takenreeks is.  

8.  Controleer de instellingen voor de **herstellen uit domein** takenreeksstap zijn geconfigureerd om te voldoen aan uw behoeften.  

9. Klik op **OK** op de takenreeks **eigenschappen** in het dialoogvenster opslaan van de takenreeks wordt uitgevoerd.
