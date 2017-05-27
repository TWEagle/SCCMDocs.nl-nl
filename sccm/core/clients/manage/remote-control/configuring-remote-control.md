---
title: Configureer beheer op afstand | Microsoft-documenten
description: Beheer op afstand in System Center Configuration Manager instellen.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45affc27-aa11-4249-9493-082ac23a3a3d
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3a386c23c81f413d7d161780bdc0ab3a5b9eccae
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>Extern beheer configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Deze procedure wordt beschreven voor het configureren van de standaardclientinstellingen voor beheer op afstand. Deze instellingen gelden voor alle computers in uw hiërarchie. Als u deze instellingen wilt toepassen op alleen op bepaalde computers, toegewezen door een aangepaste apparaatclientinstelling aan een verzameling die de computers bevat. Voor meer informatie een Zie [clientinstellingen configureren in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md). 

Voor het gebruik van Hulp op afstand en extern bureaublad moet worden geïnstalleerd en geconfigureerd op de computer waarop de Configuration Manager-console. Zie de Windows-documentatie voor meer informatie over het installeren en configureren van Hulp op afstand en Extern bureaublad.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>Beheer op afstand inschakelen en clientinstellingen configureren  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **standaard** dialoogvenster Kies **externe hulpprogramma's**.  

6.  Configureer beheer op afstand, hulp op afstand en extern bureaublad clientinstellingen. Zie voor een lijst van client-instellingen voor externe hulpprogramma's die u kunt configureren, [externe hulpprogramma's](../../../../core/clients/deploy/about-client-settings.md#remote-tools).  

    U kunt de bedrijfsnaam die wordt weergegeven in het dialoogvenster **Beheer op afstand van ConfigMgr** wijzigen door een waarde te configureren voor **Organisatienaam weergegeven in Software Center** in de clientinstellingen voor **Computeragent** .  

 De volgende keer dat clientcomputers clientbeleid downloaden, worden deze geconfigureerd met deze instellingen. Raadpleeg [Clients beheren in System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md) voor informatie over het initiëren van het ophalen van beleid voor één client.  

#### <a name="enable-keyboard-translation"></a>Toetsenbord vertaling inschakelen

Standaard verzendt de Configuration Manager de belangrijkste positie van de locatie van de viewer naar de gedeelde locatie. Dit kan leiden tot een probleem met toetsenbord-configuraties die van de viewer naar gedeelde verschillen. Bijvoorbeeld, een viewer met een Engels toetsenbord typt een "A", maar de gedeelde Frans toetsenbord "Q" wilt opgeven. U hebt nu de mogelijkheid om externe controle configureren zodat het teken zelf van de viewer toetsenbord wordt verzonden naar de gedeelde resource en de viewer plan is naar het type op de gedeelde resource aankomt.

Om in te schakelen in toetsenbord vertaling **afstandbediening voor Configuration Manager**, kiezen **actie**, en kies **toetsenbord vertaling inschakelen** voor het verzenden van belangrijke positie.

> [!NOTE]
>
> Speciale drukken, zoals ~! #@ $%, niet correct worden vertaald.


## <a name="keyboard-shortcuts-for-the-remote-control-viewer"></a>Sneltoetsen voor beheer op afstand viewer

|Sneltoets|Beschrijving|  
|-----------------------|-----------------|  
|Alt + Page Up|Hiermee schakelt u van links naar rechts tussen actieve programma’s.|  
|Alt + Page Down|Hiermee schakelt u van rechts naar links tussen actieve programma’s.|  
|Alt + Insert|Hiermee schakelt u tussen actieve programma's in de volgorde waarin ze zijn geopend.|  
|Alt + Home|Hiermee opent u het menu **Start** .|  
|Ctrl + Alt + End|Hiermee opent u het dialoogvenster Windows-beveiliging (Ctrl+Alt+Del).|  
|Alt + Delete|Hiermee opent u het Windows-menu.|  
|Ctrl + Alt + minteken (op het numerieke toetsenblok)|Hiermee kopieert u het actieve venster van de lokale computer naar het Klembord van de externe computer.|  
|Ctrl + Alt + plusteken (op het numerieke toetsenblok)|Hiermee kopieert u het hele venstergebied van de lokale computer naar het Klembord van de externe computer.|  

