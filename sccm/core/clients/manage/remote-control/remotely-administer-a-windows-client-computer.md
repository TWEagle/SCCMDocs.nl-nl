---
title: Windows-computer op afstand beheren | Microsoft Docs
description: Een externe computer van de Windows-client beheren met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 07/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 9ce5adccb9944daa4fb2b0ab132fc7cf52bd7b1b
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>Hoe u een Windows-clientcomputer op afstand beheren met behulp van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Neem de informatie in de volgende onderwerpen door voordat u aan de slag gaat met beheer op afstand:  

-   [Vereisten voor extern beheer in System Center Configuration Manager](../../../../core/clients/manage/remote-control/prerequisites-for-remote-control.md)  

-   [Beheer op afstand configureren in System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md)  

Hier volgen drie manieren de viewer voor beheer op afstand starten:  

-   In de Configuration Manager-console.  

-   In een Windows-opdrachtprompt.  

-   Windows **Start** menu op een computer waarop de Configuration Manager-console van de **Microsoft System Center** programmagroep.  

### <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Een clientcomputer op afstand beheren vanuit de Configuration Manager-console  

1.  Kies in de Configuration Manager-console **activa en naleving** > **apparaten** of **Apparaatverzamelingen**.  

3.  Selecteer de computer die u extern wilt beheren en klikt u op de **Start** tabblad, in de **apparaat** groep, kiest u **Start** > **beheer op afstand**.  

    > [!IMPORTANT]  
    >  Als de clientinstelling **Gebruikers vragen naar machtiging voor Beheer op afstand** is ingesteld op **Waar**, wordt de verbinding pas geïnitieerd als de gebruiker op de externe computer hiermee instemt. Zie voor meer informatie [beheer op afstand configureren in System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).  

4.  Als het venster **Configuration Manager - Beheer op afstand** wordt geopend, kunt u de clientcomputer op afstand beheren. Gebruik de volgende opties om de verbinding te configureren.  

    > [!NOTE]  
    >  Als de computer waarmee u verbinding maakt meerdere beeldschermen heeft, wordt de weergave van alle monitors weergegeven in het venster voor beheer op afstand.  

    -   **Bestand - verbinden** -verbinding maken met een andere computer. Deze optie is niet beschikbaar als een sessie voor beheer op afstand actief is.  

    -   **Bestand - verbinding verbreken** : de sessie actieve beheer op afstand verbreekt, maar u sluit het **afstandbediening voor Configuration Manager** venster.  

    -   **Bestand - afsluiten** : de sessie actieve beheer op afstand verbreekt en sluit u de **afstandbediening voor Configuration Manager** venster.  

        > [!NOTE]  
        >  Wanneer u de verbinding van een sessie voor beheer op afstand verbreekt, wordt op de computer die u weergeeft de inhoud van het Windows Klembord verwijderd.  

    -   **Beeld - Volledig scherm** -maximaliseert de **afstandbediening voor Configuration Manager** venster.  

        > [!NOTE]  
        >  Druk op Ctrl+Alt+Break om de modus voor volledig scherm af te sluiten.  

    -   **Beeld - aanpassen aan pagina** -Hiermee wordt de weergave van de externe computer aan de grootte van de **afstandbediening voor Configuration Manager** venster.  

    -   **Beeld - Statusbalk** -Hiermee wordt de weergave van de **afstandbediening voor Configuration Manager** statusbalk venster.  

    -   **Actie - verzenden Ctrl + Alt + Del sleutel** -verzendt een toetscombinatie Ctrl + Alt + Del naar de externe computer.  

    -   **Actie - Klembord delen activeren** -kunt u items naar en van de externe computer kopiëren en plakken. Als u deze waarde wijzigt, moet u de sessie voor beheer op afstand opnieuw starten om de wijziging door te voeren.  

        > [!NOTE]  
        >  Als u niet wilt dat Klembord delen om te worden ingeschakeld in de Configuration Manager-console op de computer met de console, stelt u de waarde van de registersleutel **HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote Control\Clipboard Sharing** naar **0**.  

    -   **Actie - extern toetsenbord en muis vergrendelen** -Hiermee vergrendelt u het externe toetsenbord en muis om te voorkomen dat de gebruiker de externe computer bedient.  

    -   **Help - Info over beheer op afstand** -geeft IDE huidige versie van de viewer.  

5.  Gebruikers op de externe computer kunnen meer informatie over de sessie voor extern beheer als ze op de Configuration Manager weergeven**beheer op afstand** pictogram in het systeemvak of het pictogram op de balk van de sessie beheer op afstand.  

### <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>De viewer voor beheer op afstand starten via de Windows-opdrachtregel  

-   Typ het volgende achter de opdrachtprompt van Windows *< installatiemap van Configuration Manager\>***\AdminConsole\Bin\x64\CmRcViewer.exe**  

CmRcViewer.exe ondersteunt de volgende opdrachtregelopties:  

- *Adres* -Hiermee geeft u de NetBIOS-naam, de volledig gekwalificeerde domeinnaam (FQDN) of het IP-adres van de client waarmee u verbinding wilt maken.
- *Siteservernaam* -geeft de naam van de System Center Configuration Manager-siteserver waarnaar u wilt statusberichten die zijn gerelateerd aan de sessie voor beheer op afstand verzenden.
- **/?** -Geeft de opdrachtregelopties voor beheer op afstand viewer.  
     
**Example:CmRcViewer.exe** *< adres\> * * < \\\Site-servernaam >*  
