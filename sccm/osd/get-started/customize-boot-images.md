---
title: "Opstartinstallatiekopieën - Configuration Manager aanpassen | Microsoft Docs"
description: Meer informatie over het gebruik van Configuration Manager of Deployment Image Servicing and Management (DISM) opdrachtregeltool aan een opstartinstallatiekopie aanpassen op verschillende manieren.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9cbfc406-d009-446d-8fee-4938de48c919
caps.latest.revision: "15"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: ab2ecb64c9c80b4effed79ba08769c99473db0c4
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="customize-boot-images-with-system-center-configuration-manager"></a>Opstartinstallatiekopieën aanpassen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Elke versie van Configuration Manager ondersteunt een specifieke versie van de Windows Assessment and Deployment Kit (Windows ADK). U kunt de service of installatiekopieën uit de Configuration Manager-console wanneer ze zijn gebaseerd op een Windows PE-versie van de ondersteunde versie van Windows ADK aanpassen. Voor andere installatiekopieën geldt dat u ze moet aanpassen met een andere methode, zoals de Deployment Image Servicing and Management (DISM) opdrachtregeltool welke deel uitmaakt van Windows AIK en Windows ADK.  

 Hieronder vindt u de ondersteunde versie van Windows ADK, de Windows PE-versie die op waarop de opstartinstallatiekopie is gebaseerd die kan worden aangepast via de Configuration Manager-console en de Windows PE-versies waarop de opstartinstallatiekopie is gebaseerd, u kunt aanpassen met behulp van DISM en vervolgens de installatiekopie toevoegen aan Configuration Manager.  

-   **Windows ADK-versie**  

     Windows ADK voor Windows 10  

-   **Windows PE-versies voor installatiekopieën die aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 10  

-   **Ondersteunde Windows PE-versies voor installatiekopieën die niet aanpasbaar zijn via de Configuration Manager-console**  

     Windows PE 3.1<sup>1</sup> en Windows PE 5  

     <sup>1</sup> u kunt alleen een opstartinstallatiekopie toevoegen aan Configuration Manager wanneer deze is gebaseerd op Windows PE 3.1. Installeer Windows AIK Supplement voor Windows 7 SP1 om een upgrade van Windows AIK voor Windows 7 (gebaseerd op Windows PE 3) naar Windows AIK Supplement voor Windows 7 SP1 (gebaseerd op Windows PE 3.1) uit te voeren. U kunt Windows AIK Supplement voor Windows 7 SP1 downloaden via het [Microsoft Downloadcentrum](http://www.microsoft.com/download/details.aspx?id=5188).  

     Bijvoorbeeld, wanneer u Configuration Manager hebt, kunt u opstartinstallatiekopieën uit Windows ADK voor Windows 10 (gebaseerd op Windows PE 10) aanpassen via de Configuration Manager-console. Hoewel installatiekopieën die zijn gebaseerd op Windows PE 5 wel worden wel ondersteund, moet u ze aanpassen op een andere computer en moet u die versie van DISM gebruiken die is geïnstalleerd met Windows ADK voor Windows 8. Vervolgens kunt u de installatiekopie toevoegen aan de Configuration Manager-console.  

 De procedures in dit onderwerp laten zien hoe u de optionele componenten die door Configuration Manager aan de installatiekopie met behulp van de volgende Windows PE-pakketten toevoegen:  

-   **WinPE-WMI**: Voegt ondersteuning voor Windows Management Instrumentation (WMI) toe.  

-   **WinPE-Scripting**: Voegt ondersteuning voor Windows Script Host (WSH) toe.  

-   **WinPE-WDS-Tools**: Windows Deployment Services-hulpprogramma's installeert.  

 Er zijn andere Windows PE-pakketten beschikbaar die u kunt toevoegen. De volgende bronnen geven informatie over de optionele onderdelen die u kunt toevoegen aan de installatiekopie.  

-   Zie voor Windows PE 5 [WinPE: Pakketten (Optional Components Reference) toevoegen](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx)  

-   Voor Windows PE 3.1, zie het onderwerp [Add a Package to a Windows PE Image](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx) (Een pakket toevoegen aan een Windows PE-installatiekopie) in de Windows 7 TechNet Documentation Library.  

> [!NOTE]
>Wanneer u WinPE opstart vanuit een aangepaste installatiekopie die hulpprogramma's bevat die u hebt toegevoegd, kunt u een opdrachtprompt openen vanuit WinPE en de naam typen van het hulpprogramma om dit uit te voeren. De locatie van deze hulpprogramma's worden automatisch toegevoegd aan de padvariabele. De opdrachtprompt kan alleen worden toegevoegd als de **opdrachtondersteuning inschakelen (alleen testen)** instelling is geselecteerd op de **aanpassing** tabblad in de eigenschappen van de opstartinstallatiekopie.

## <a name="customize-a-boot-image-that-uses-windows-pe-5"></a>Een installatiekopie die gebruikmaakt van Windows PE 5 aanpassen.  
 Als u een opstartinstallatiekopie wilt aanpassen die gebruikmaakt van Windows PE 5, moet u Windows ADK installeren en het opdrachtregelprogramma DISM gebruiken om de opstartinstallatiekopie te koppelen, de optionele componenten en stuurprogramma's toe te voegen en de wijzigingen aan te brengen in de opstartinstallatiekopie. Gebruik de volgende procedure om de installatiekopie aan te passen.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-5"></a>Een opstartinstallatiekopie aanpassen die gebruikmaakt van Windows PE 5  

1.  De Windows ADK op een computer waarop geen andere versie van Windows AIK of Windows ADK installeren en niet alle Configuration Manager-onderdelen zijn geïnstalleerd.  

2.  Download Windows ADK voor Windows 8.1 via het [Microsoft Downloadcentrum](http://www.microsoft.com/download/details.aspx?id=39982).  

3.  Kopieer de installatiekopie (wimpe.wim) uit de Windows ADK installatiemap (bijvoorbeeld <*installatiepad*> \Windows Kits\\<*versie*> \Assessment and Deployment Kit\Windows Preinstallation Environment\\<*x86 of amd64*>\\<*landinstelling*>) naar een doelmap op de computer van waaruit u de installatiekopie gaat aanpassen. Deze procedure maakt gebruik van C:\WinPEWAIK als de naam van de doelmap.  

4.  Gebruik DISM om de installatiekopie te koppelen aan een lokale Windows PE-map. Typ bijvoorbeeld de volgende opdrachtregel:  

     **DISM.exe/mount-wim /wimfile:C:\WinPEWAIK\winpe.wim /index:1 /mountdir:C:\WinPEMount**  

     Waar C:\WinPEWAIK de map is waar de installatiekopie in staat en C:\WinPEMount de gekoppelde map.  

    > [!NOTE]
    >  Voor meer informatie over DISM, zie het onderwerp [DISM - Deployment Image Servicing and Management Technical Reference](http://technet.microsoft.com/library/hh824821.aspx) in de Windows 8.1 en Windows 8 TechNet Documentation Library.

5.  Gebruik, nadat u de installatiekopie gekoppeld hebt, DISM om optionele componenten aan de installatiekopie toe te voegen. In Windows PE 5 bevinden de optionele 64-bits componenten zich op de volgende locatie: <*Installation path*>\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs.  

    > [!NOTE]
    >  Deze procedure gebruikt de volgende locatie voor de optionele onderdelen: C:\Program bestanden (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs. Het pad dat u gebruikt kan afwijken afhankelijk van de versie en installatieopties die u voor de Windows ADK kiest.  

     Typ het volgende om de optionele componenten te installeren:  

     **DISM.exe \winpemount/Add-Package/PackagePath: 'C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-wmi.cab'**  

     **DISM.exe \winpemount/Add-Package/PackagePath: "C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-scripting.cab"**  

     **DISM.exe \winpemount/Add-Package/PackagePath: 'C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-WDS-Tools.cab'**  

     **DISM.exe \winpemount/Add-Package/PackagePath: 'C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-SecureStartup.cab'**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-SecureStartup_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-WMI_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-Scripting** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-WDS-Tools_** *<locale\>* **.cab"**  

     Waarbij C:\WinPEMount de gekoppelde map is en taal de taal voor de onderdelen. Voor de taal **en-us** typt u bijvoorbeeld:  

     **DISM.exe \winpemount/Add-Package/PackagePath: 'C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SecureStartup_en-us.cab'**  

     **DISM.exe \winpemount/Add-Package/PackagePath: 'C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab'**  

     **DISM.exe \winpemount/Add-Package/PackagePath: 'C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab'**  

     **DISM.exe \winpemount/Add-Package/PackagePath: 'C:\Program Files (x86) kits\8.1\assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WDS-Tools_en-us.cab'**  

    > [!TIP]
    >  Voor meer informatie over de optionele componenten die u aan de installatiekopie kunt toevoegen, zie het onderwerp [Windows PE Optional Components Reference](http://technet.microsoft.com/library/hh824926.aspx) (Naslagdocumentatie voor optionele componenten van Windows PE) in de Windows 8.1 en Windows 8 TechNet Documentation Library.  

6.  Gebruik DISM om specifieke stuurprogramma's aan de installatiekopie toe te voegen, indien nodig. Typ het volgende om stuurprogramma's aan de installatiekopie toe te voegen:  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:<** *pad naar .inf-bestand van stuurprogramma***>**  

     Waar C:\WinPEMount de gekoppelde map is.  

7.  Typ het volgende om het installatiekopiebestand te ontkoppelen en de wijzigingen door te voeren.  

     **DISM.exe /unmount-wim /mountdir:C:\WinPEMount/Commit**  

     Waar C:\WinPEMount de gekoppelde map is.  

8.  Voeg de bijgewerkte installatiekopie voor Configuration Manager zodat deze beschikbaar voor gebruik in uw takenreeksen. Gebruik de volgende stappen om de bijgewerkte installatiekopie te importeren:  

    1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

    2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

    3.  Klik op **Installatiekopie toevoegen** in het tabblad **Start** in de groep **Maken** om de wizard Installatiekopie toevoegen te starten.  

    4.  Geef op de pagina **Gegevensbron** de volgende opties op en klik op **Volgende**.  

        -   Geef in het venster **Pad** het pad naar het bijgewerkte installatiekopiebestand op. Het opgegeven pad moet een geldig netwerkpad zijn in UNC-indeling. Bijvoorbeeld:  **\\ \\ <**  *servername***>\\<***WinPEWAIK share***> \winpe.wim**.  

        -   Selecteer de installatiekopie in de vervolgkeuzelijst **Installatiekopie**. Als het WIM-bestand meerdere installatiekopieën bevat, wordt elke installatiekopie vermeld.  

    5.  Geef op de pagina **Algemeen** de volgende opties op en klik op **Volgende**.  

        -   Geef in het venster **Naam** een unieke naam op voor de installatiekopie.  

        -   Geef in het venster **Versie** een uniek versienummer op voor de installatiekopie.  

        -   Geef in het veld **Opmerking** een korte beschrijving van hoe de installatiekopie wordt gebruikt.  

    6.  Voltooi de wizard.  

9. U kunt een opdrachtshell in de installatiekopie inschakelen om eventuele fouten die erin staan op te sporen en te herstellen in Windows PE. Gebruik de volgende stappen om de opdrachtshell in te schakelen.  

    1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

    2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

    3.  Zoek de nieuwe installatiekopie in de lijst en identificeer de pakket-id voor de kopie. U kunt de pakket-id vinden in de kolom **Kopie-id** voor de installatiekopie.  

    4.  Typ na een opdrachtprompt **wbemtest** om de Windows Management Instrumentation Tester te openen.  

    5.  Type  **\\ \\ <**  *SMS-Providercomputer***> \root\sms\site_ <***sitecode*  **>**  in **Namespace**, en klik vervolgens op **Connect**.  

    6.  Klik op **Instantie openen**, typ **sms_bootimagepackage.packageID="<packageID\>"** en klik vervolgens op **OK**. Voer voor pakket-id de waarde in die u in stap 3 hebt geïdentificeerd.  

    7.  Klik op **Object vernieuwen** en klik vervolgens in het venster **Eigenschappen** op **EnableLabShell**.  

    8.  Klik op **Eigenschap bewerken**, wijzig de waarde in **TRUE** en klik op **Eigenschap opslaan**.  

    9. Klik op **Object opslaan** en sluit het Testprogramma voor Windows Management Instrumentation.  

10. Voordat u de installatiekopie kunt gebruiken in een takenreeks, moet u de installatiekopie distribueren naar distributiepunten, distributiepuntgroepen, of naar verzamelingen die aan distributiepuntgroepen gekoppeld zijn. Gebruik de volgende stappen om de installatiekopie te distribueren.  

    1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

    2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

    3.  Klik op de installatiekopie die u in stap 3 hebt geïdentificeerd.  

    4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Distributiepunten bijwerken**.  

## <a name="customize-a-boot-image-that-uses-windows-pe-31"></a>Een installatiekopie die gebruikmaakt van Windows PE 3.1 aanpassen  
 Om een installatiekopie die gebruikmaakt van WinPE 3.1 aan te passen, moet u Windows AIK installeren, de Windows AIK supplement voor Windows 7 SP1 installeren, en het opdrachtregelhulpprogramma DISM gebruiken om de installatiekopie te koppelen, optionele componenten en stuurprogramma's toe te voegen, en de wijzigingen door te voeren op de installatiekopie. Gebruik de volgende procedure om de installatiekopie aan te passen.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-31"></a>Een installatiekopie die gebruikmaakt van Windows PE 3.1 aanpassen  

1.  De Windows AIK op een computer waarop geen andere versie van Windows AIK of Windows ADK installeren en niet alle Configuration Manager-onderdelen zijn geïnstalleerd. Download Windows AIK via het [Microsoft Downloadcentrum](http://www.microsoft.com/download/details.aspx?id=5753).  

2.  Installeer de Windows AIK Supplement voor Windows 7 met SP1 op de computer vanaf stap 1. Download Windows AIK Supplement voor Windows 7 SP1 via het [Microsoft Downloadcentrum](http://www.microsoft.com/download/details.aspx?id=5188).  

3.  Kopieer de installatiekopie (wimpe.wim) uit de installatiemap van Windows AIK (bijvoorbeeld <*InstallationPath*>\Windows AIK\Tools\PETools\amd64\\) naar een map op de computer vanwaaruit u de installatiekopie gaat aanpassen. Deze procedure maakt gebruik van C:\WinPEWAIK als de naam van de map.  

4.  Gebruik DISM om de installatiekopie te koppelen aan een lokale Windows PE-map. Typ bijvoorbeeld de volgende opdrachtregel:  

     **DISM.exe/mount-wim /wimfile:C:\WinPEWAIK\winpe.wim /index:1 /mountdir:C:\WinPEMount**  

     Waar C:\WinPEWAIK de map is waar de installatiekopie in staat en C:\WinPEMount de gekoppelde map.  

    > [!NOTE]
    >  Voor meer informatie over DISM, zie het onderwerp [Deployment Image Servicing and Management Technical Reference](http://technet.microsoft.com/library/dd744256\(v=ws.10\).aspx) (Technische documentatie voor het implementeren van servicebeheer voor installatiekopieën) in de Windows 7 TechNet Documentation Library.  

5.  Gebruik, nadat u de installatiekopie gekoppeld hebt, DISM om optionele componenten aan de installatiekopie toe te voegen. In Windows PE 3.1 staan de optionele componenten bijvoorbeeld in <*InstallationPath*>\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\.  

    > [!NOTE]
    >  Deze procedure gebruikt de volgende locatie voor de optionele onderdelen: C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs. Het pad dat u gebruikt kan afwijken afhankelijk van de versie en installatieopties die u voor de Windows AIK kiest.  

     Typ het volgende om de optionele componenten te installeren:  

     **DISM.exe \winpemount/Add-Package/PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wmi.cab"**  

     **DISM.exe \winpemount/Add-Package/PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-scripting.cab"**  

     **DISM.exe \winpemount/Add-Package/PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wds-tools.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<locale\>* **\winpe-wmi_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<locale\>* **\winpe-scripting_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<locale\>* **\winpe-wds-tools_** *<locale\>* **.cab"**  

     Waarbij C:\WinPEMount de gekoppelde map is en taal de taal voor de onderdelen. Voor de taal **en-us** typt u bijvoorbeeld:  

     **DISM.exe \winpemount/Add-Package/PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wmi_en-us.cab"**  

     **DISM.exe \winpemount/Add-Package/PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-scripting_en-us.cab"**  

     **DISM.exe \winpemount/Add-Package/PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wds-tools_en-us.cab"**  

    > [!TIP]
    >  Voor meer informatie over de verschillende pakketten die u aan de installatiekopie kunt toevoegen, zie het onderwerp [Add a Package to a Windows PE Image](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx) (Een pakket toevoegen aan een Windows PE-installatiekopie) in de Windows 7 TechNet Documentation Library.  

6.  Gebruik DISM om specifieke stuurprogramma's aan de installatiekopie toe te voegen, indien nodig. Typ het volgende om stuurprogramma's aan de installatiekopie toe te voegen, indien nodig:  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:<** *pad naar .inf-bestand van stuurprogramma***>**  

     Waar C:\WinPEMount de gekoppelde map is.  

7.  Typ het volgende om het installatiekopiebestand te ontkoppelen en de wijzigingen door te voeren.  

     **DISM.exe /unmount-wim /mountdir:C:\WinPEMount/Commit**  

     Waar C:\WinPEMount de gekoppelde map is.  

8.  Voeg de bijgewerkte installatiekopie voor Configuration Manager zodat deze beschikbaar voor gebruik in uw takenreeksen. Gebruik de volgende stappen om de bijgewerkte installatiekopie te importeren:  

    1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

    2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

    3.  Klik op **Installatiekopie toevoegen** in het tabblad **Start** in de groep **Maken** om de wizard Installatiekopie toevoegen te starten.  

    4.  Geef op de pagina **Gegevensbron** de volgende opties op en klik op **Volgende**.  

        -   Geef in het venster **Pad** het pad naar het bijgewerkte installatiekopiebestand op. Het opgegeven pad moet een geldig netwerkpad zijn in UNC-indeling. Bijvoorbeeld:  **\\ \\ <**  *servername***>\\<***WinPEWAIK share***> \winpe.wim**.  

        -   Selecteer de installatiekopie in de vervolgkeuzelijst **Installatiekopie**. Als het WIM-bestand meerdere installatiekopieën bevat, wordt elke installatiekopie vermeld.  

    5.  Geef op de pagina **Algemeen** de volgende opties op en klik op **Volgende**.  

        -   Geef in het venster **Naam** een unieke naam op voor de installatiekopie.  

        -   Geef in het venster **Versie** een uniek versienummer op voor de installatiekopie.  

        -   Geef in het veld **Opmerking** een korte beschrijving van hoe de installatiekopie wordt gebruikt.  

    6.  Voltooi de wizard.  

9. U kunt een opdrachtshell in de installatiekopie inschakelen om eventuele fouten die erin staan op te sporen en te herstellen in Windows PE. Gebruik de volgende stappen om de opdrachtshell in te schakelen.  

    1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

    2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

    3.  Zoek de nieuwe installatiekopie in de lijst en identificeer de pakket-id voor de kopie. U kunt de pakket-id vinden in de kolom **Kopie-id** voor de installatiekopie.  

    4.  Typ na een opdrachtprompt **wbemtest** om de Windows Management Instrumentation Tester te openen.  

    5.  Type  **\\ \\ <**  *SMS-Providercomputer***> \root\sms\site_ <***sitecode*  **>**  in **Namespace**, en klik vervolgens op **Connect**.  

    6.  Klik op **Instantie openen**, typ **sms_bootimagepackage.packageID="<packageID\>"** en klik vervolgens op **OK**. Voer voor pakket-id de waarde in die u in stap 3 hebt geïdentificeerd.  

    7.  Klik op **Object vernieuwen** en klik vervolgens in het venster **Eigenschappen** op **EnableLabShell**.  

    8.  Klik op **Eigenschap bewerken**, wijzig de waarde in **TRUE** en klik op **Eigenschap opslaan**.  

    9. Klik op **Object opslaan** en sluit het Testprogramma voor Windows Management Instrumentation.  

10. Voordat u de installatiekopie kunt gebruiken in een takenreeks, moet u de installatiekopie distribueren naar distributiepunten, distributiepuntgroepen, of naar verzamelingen die aan distributiepuntgroepen gekoppeld zijn. Gebruik de volgende stappen om de installatiekopie te distribueren.  

    1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

    2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek** en klik vervolgens op **Installatiekopieën**.  

    3.  Klik op de installatiekopie die u in stap 3 hebt geïdentificeerd.  

    4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Distributiepunten bijwerken**.  
