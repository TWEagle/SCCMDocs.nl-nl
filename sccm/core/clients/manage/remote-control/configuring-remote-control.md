---
title: Extern beheer configureren | Microsoft Docs
description: Instellen van beheer op afstand in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45affc27-aa11-4249-9493-082ac23a3a3d
caps.latest.revision: "4"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 633336049feca35f76e3a57e14cc42088a303f8d
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="configuring-remote-control-in-system-center-configuration-manager"></a>Beheer op afstand configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Deze procedure beschrijft de standaardclientinstellingen voor beheer op afstand te configureren. Deze instellingen gelden voor alle computers in uw hiërarchie. Als u deze instellingen wilt toepassen op alleen op enkele computers, wijst u een aangepaste apparaatclientinstelling aan een verzameling waartoe deze computers. Voor meer informatie een Zie [het configureren van clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md). 

Voor het gebruik van Hulp op afstand en extern bureaublad moet worden geïnstalleerd en geconfigureerd op de computer waarop de Configuration Manager-console. Zie de Windows-documentatie voor meer informatie over het installeren en configureren van Hulp op afstand en Extern bureaublad.  

#### <a name="to-enable-remote-control-and-configure-client-settings"></a>Beheer op afstand inschakelen en clientinstellingen configureren  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **standaard** dialoogvenster Kies **externe hulpprogramma's**.  

6.  Beheer op afstand, hulp op afstand en extern bureaublad-clientinstellingen configureren. Zie voor een lijst met clientinstellingen voor externe hulpprogramma's die u kunt configureren, [externe hulpprogramma's](../../../../core/clients/deploy/about-client-settings.md#remote-tools).  

    U kunt de bedrijfsnaam die wordt weergegeven in het dialoogvenster **Beheer op afstand van ConfigMgr** wijzigen door een waarde te configureren voor **Organisatienaam weergegeven in Software Center** in de clientinstellingen voor **Computeragent** .  

 De volgende keer dat clientcomputers clientbeleid downloaden, worden deze geconfigureerd met deze instellingen. Raadpleeg [Clients beheren in System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md) voor informatie over het initiëren van het ophalen van beleid voor één client.  

#### <a name="enable-keyboard-translation"></a>Toetsenbord-omzetting inschakelen

Standaard verzendt de Configuration Manager de belangrijkste positie van de viewer locatie naar de gedeelde locatie. Dit kan een probleem voor toetsenbord-configuraties die van de viewer naar gedeelde afwijken leiden. Bijvoorbeeld, een viewer met een Engels toetsenbord typt een "A", maar de gedeelde Franse toetsenbord 'Q' wilt opgeven. U hebt nu de mogelijkheid om beheer op afstand configureren zodat het teken zelf wordt overgebracht van de viewer toetsenbord naar de gedeelde en wat de viewer wil typt u bij de gedeelde resource aankomt.

In toetsenbord-omzetting inschakelen **afstandbediening voor Configuration Manager**, kies **actie**, en kies **toetsenbord-omzetting inschakelen** voor het verzenden van de belangrijkste positie.

> [!NOTE]
>
> Speciale drukken, zoals ~! # $@ %, niet correct worden vertaald.


## <a name="keyboard-shortcuts-for-the-remote-control-viewer"></a>Sneltoetsen voor de viewer voor beheer op afstand

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
