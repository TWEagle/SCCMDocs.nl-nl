---
title: Extern beheer van Windows-computer | Microsoft-documenten
description: Een externe Windows client-computer te beheren met System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 63113a2928c0aca292e6ca07ffe1187324801b7b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>Hoe u een Windows client-computer op afstand te beheren met behulp van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Neem de informatie in de volgende onderwerpen door voordat u aan de slag gaat met beheer op afstand:  

-   [Vereisten voor beheer op afstand in System Center Configuration Manager](../../../../core/clients/manage/remote-control/prerequisites-for-remote-control.md)  

-   [Extern beheer configureren in System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md)  

Hier zijn drie manieren om de viewer voor beheer op afstand starten:  

-   In de Configuration Manager-console.  

-   In een Windows-opdrachtprompt.  

-   Op het Windows **Start** menu op een computer met de Configuration Manager-console uit de **Microsoft System Center** programmagroep.  

### <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Een clientcomputer op afstand beheren vanuit de Configuration Manager-console  

1.  Kies in de Configuration Manager-console **activa en naleving** > **apparaten** of **Apparaatverzamelingen**.  

3.  Selecteer de computer die u op afstand wilt beheren en klik in de **Start** tabblad, in de **apparaat** groep, kiest u **Start** > **beheer op afstand**.  

    > [!IMPORTANT]  
    >  Als de clientinstelling **Gebruikers vragen naar machtiging voor Beheer op afstand** is ingesteld op **Waar**, wordt de verbinding pas geïnitieerd als de gebruiker op de externe computer hiermee instemt. Zie voor meer informatie [beheer op afstand configureren in System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).  

4.  Als het venster **Configuration Manager - Beheer op afstand** wordt geopend, kunt u de clientcomputer op afstand beheren. Gebruik de volgende opties om de verbinding te configureren.  

    > [!NOTE]  
    >  Als de computer waarop u verbinding met maakt meerdere beeldschermen heeft, wordt de weergave van alle monitors weergegeven in het venster voor beheer op afstand.  

    -   **Bestand - verbinding** -verbinding maken met een andere computer. Deze optie is niet beschikbaar als een sessie voor beheer op afstand actief is.  

    -   **Bestand - verbreken** - de actieve beheer op afstand-sessie verbreekt maar sluit niet de **afstandbediening voor Configuration Manager** venster.  

    -   **Bestand - sluiten** : de actieve beheer op afstand-sessie wordt verbroken en sluit de **afstandbediening voor Configuration Manager** venster.  

        > [!NOTE]  
        >  Wanneer u de verbinding van een sessie voor beheer op afstand verbreekt, wordt op de computer die u weergeeft de inhoud van het Windows Klembord verwijderd.  

    -   **Weergave - Volledig scherm** -maximaliseert de **afstandbediening voor Configuration Manager** venster.  

        > [!NOTE]  
        >  Druk op Ctrl+Alt+Break om de modus voor volledig scherm af te sluiten.  

    -   **Weergave - aanpassen aan pagina** -past de weergave van de externe computer aan de grootte van de **afstandbediening voor Configuration Manager** venster.  

    -   **Weergave - statusbalk** -Hiermee wordt de weergave van de **afstandbediening voor Configuration Manager** statusbalk venster.  

    -   **Actie - verzenden Ctrl + Alt + Del sleutel** -verzendt een toetscombinatie Ctrl + Alt + Del naar de externe computer.  

    -   **Actie - Enable Klembord delen** -kunt u items naar en van de externe computer kopiëren en plakken. Als u deze waarde wijzigt, moet u de sessie voor beheer op afstand opnieuw starten om de wijziging door te voeren.  

        > [!NOTE]  
        >  Als u niet wilt dat Klembord delen zijn ingeschakeld in de Configuration Manager-console op de computer met de console en stel de waarde van de registersleutel **HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote Control\Clipboard delen** naar **0**.  

    -   **Actie - vergrendeling extern toetsenbord en muis** -vergrendelt externe toetsenbord en muis te voorkomen dat de gebruiker de externe computer.  

    -   **Help - beheer op afstand** -geeft IDE huidige versie van de viewer.  

5.  Gebruikers op de externe computer meer informatie over de sessie voor beheer op afstand wanneer ze op de Configuration Manager kunnen bekijken**beheer op afstand** pictogram in het Windows-systeemvak of het pictogram op de menubalk van beheer op afstand-sessie.  

### <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>De viewer voor beheer op afstand starten via de Windows-opdrachtregel  

-   Typ bij de Windows-opdrachtprompt *< Configuration Manager-installatiemap\>***\AdminConsole\Bin\x64\CmRcViewer.exe**  

    > [!NOTE]  
    >  CmRcViewer.exe ondersteunt de volgende opdrachtregelopties:  
    >   
    >  -   *< adres\>*  -Hiermee geeft u de NetBIOS-naam, de volledig gekwalificeerde domeinnaam (FQDN) of het IP-adres van de client waarmee u verbinding wilt maken.  
    > -   *< naam van de siteserver\>*  -geeft de naam van de System Center Configuration Manager-siteserver die u wilt statusberichten die zijn gerelateerd aan de sessie voor beheer op afstand verzenden.  
    > -   **/?** -Geeft de opdrachtregelopties voor beheer op afstand viewer.  
    >   
    >  **Example:CmRcViewer.exe** *< adres\>*   *< \\\Site-servernaam >*  

