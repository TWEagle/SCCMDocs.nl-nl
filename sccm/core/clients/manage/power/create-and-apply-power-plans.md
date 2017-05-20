---
title: Maken en toepassen van energiebeheerschema&quot;s | Microsoft-documenten
description: Maken en toepassen van energiebeheerschema&quot;s in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 738eddaa-52e2-467f-b453-821ef2884d47
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: de81da31b524cebe8e820766a64ecc5fdb7e4771
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-and-apply-power-plans-in-system-center-configuration-manager"></a>Het maken en toepassen van energiebeheerschema's in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Energiebeheer in System Center Configuration Manager kunt u om toe te passen energiebeheerschema's die worden geleverd met Configuration Manager naar verzamelingen computers in uw hiërarchie, of uw eigen aangepaste energiebeheerschema's maken. Volg de procedure in dit onderwerp om een ingebouwd of aangepast energiebeheerschema op computers toe te passen.  

> [!IMPORTANT]  
>  U kunt alleen Configuration Manager energiebeheerschema's toegepast op apparaatverzamelingen.  

 Als een computer lid is van meerdere verzamelingen, die elk verschillende energiebeheerschema’s toepassen, worden de volgende acties ondernomen:  

-   Energiebeheerschema voor: Als u meerdere waarden voor energie-instellingen worden toegepast op een computer, wordt de minst beperkende waarde gebruikt.  

-   Tijd voor Wake-up: Als meerdere keren voor Wake-up worden toegepast op een desktopcomputer, wordt de tijd die het dichtst bij middernacht gebruikt.  

 Gebruik het rapport **Computers met meerdere energiebeheerschema's** om alle computers weer te geven waarop meerdere energiebeheerschema's worden toegepast. Hierdoor kunt u computers met energiebeheerconflicten ontdekken. Zie voor meer informatie over power management-rapporten, [monitor en plannen voor energiebeheer in System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

> [!IMPORTANT]  
>  Energie-instellingen die zijn geconfigureerd met behulp van Windows-groepsbeleid overschrijven de instellingen zijn geconfigureerd door Configuration Manager-energiebeheer.  

 Gebruik de volgende procedure voor het maken en toepassen van een energiebeheerschema voor Configuration Manager.  

### <a name="to-create-and-apply-a-power-plan"></a>Een energiebeheerschema maken en toepassen  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  Klik op **Apparaatverzamelingen** in de werkruimte **Activa en naleving**.  

3.  Klik in de lijst **Apparaatverzamelingen** op de verzameling waarop u instellingen voor energiebeheer wilt toepassen en klik vervolgens op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.  

4.  In de **energiebeheer** tabblad van het *< Collectienaam\>***eigenschappen** in het dialoogvenster Selecteer **instellingen voor energiebeheer opgeven voor deze verzameling**.  

    > [!NOTE]  
    >  U kunt ook klikken op **Bladeren** en de instellingen voor energiebeheer van een geselecteerde verzameling naar de geselecteerde verzameling kopiëren.  

5.  Geef in het veld **Start** en het veld **Einde** de begin- en eindtijd voor piekuren (of kantooruren) op.  

6.  Schakel **Activeringstijd (desktopcomputers)** in om een tijd op te geven waarop een desktopcomputer uit de slaapstand of sluimerstand wordt gehaald om geplande updates of software-installaties te installeren.  

    > [!IMPORTANT]  
    >  Energiebeheer maakt gebruik van de interne Windows-activeringsfunctie om computers uit de slaapstand of sluimerstand te halen. Activeringstijdinstellingen worden niet toegepast op draagbare computers om te voorkomen dat ze worden geactiveerd wanneer ze niet op netstroom zijn aangesloten. De activeringstijd wordt op een willekeurig tijdstip ingesteld en computers worden ergens gedurende een periode van één uur na de opgegeven activeringstijd geactiveerd.  

7.  Als u een aangepast energiebeheerschema voor piekuren (of kantooruren) wilt configureren, selecteert u **Aangepaste piek (ConfigMgr)** in de vervolgkeuzelijst **Schema voor piekuren** en klikt u vervolgens op **Bewerken**. Als u een energiebeheerschema voor niet-piekuren (of buiten kantooruren) wilt configureren, selecteert u **Aangepaste niet-piek (ConfigMgr)** in de vervolgkeuzelijst **Schema voor niet-piekuren** en klikt u vervolgens op **Bewerken**.  

    > [!NOTE]  
    >  U kunt het rapport **Computeractiviteit** gebruiken om de planning te bepalen die moet worden gebruikt voor piek- en niet-piekuren wanneer u energiebeheerschema's op verzamelingen computers toepast. Zie voor meer informatie [monitor en plannen voor energiebeheer in System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

     U kunt ook een selectie maken in de ingebouwde energiebeheerschema's, **Gebalanceerd (ConfigMgr)**, **Hoge prestaties (ConfigMgr)** en **Energiebesparing (ConfigMgr)**, en vervolgens op **Weergeven** klikken om de eigenschappen van elk energiebeheerschema weer te geven.  

    > [!NOTE]  
    >  U kunt het ingebouwde energiebeheerschema niet wijzigen.  

8.  In de *< naam van energiebeheerschema\>***eigenschappen** dialoogvenster Configureer de volgende instellingen:  

    -   **Naam:** Geef een naam op voor dit schema of de opgegeven standaardwaarde.  

    -   **Beschrijving:**  Geef een beschrijving op voor dit schema of de opgegeven standaardwaarde.  

    -   **Geef de eigenschappen voor deze energieplanning:** Configureer de eigenschappen van power plan. Schakel het selectievakje uit als u een eigenschap wilt uitschakelen. Zie [Available power management plan settings](#BKMK_Plans) in dit onderwerp voor meer informatie over de beschikbare instellingen.  

        > [!IMPORTANT]  
        >  Ingeschakelde instellingen worden toegepast op computers wanneer het energiebeheerschema wordt toegepast. Als u het selectievakje voor een energiebeheerschema uitschakelt, wordt de waarde op de clientcomputer niet gewijzigd wanneer het energiebeheerschema wordt toegepast. Door een selectievakje uit te schakelen worden de energiebeheerinstellingen niet hersteld naar de vorige waarde voordat een energiebeheerschema werd toegepast.  

9. Klik op **OK** sluit de *< naam van energiebeheerschema\>***eigenschappen** in het dialoogvenster.  

10. Klik op **OK** sluit de *< Collectienaam\>***instellingen** in het dialoogvenster en het energiebeheerschema toe te passen.  

##  <a name="BKMK_Plans"></a> Available power management plan settings  
 De volgende tabel bevat de instellingen voor energiebeheer beschikbaar in Configuration Manager. U kunt afzonderlijke instellingen configureren voor wanneer de computer op netstroom is aangesloten of op de accu werkt. Afhankelijk van de versie van Windows die u gebruikt, kunnen bepaalde instellingen mogelijk niet worden geconfigureerd.  

> [!NOTE]  
>  Energie-instellingen die u niet configureert, behouden hun huidige waarde op clientcomputers.  

|Naam|Beschrijving|  
|----------|-----------------|  
|**Beeldscherm uitschakelen na (minuten)**|Hiermee geeft u de tijdsduur aan in minuten die de computer inactief moet zijn voordat het beeldscherm wordt uitgeschakeld. Geef de waarde **0** op als u niet wilt dat energiebeheer het beeldscherm uitschakelt.|  
|**Slaapstand na (minuten)**|Hiermee geeft u de tijdsduur in minuten aan die de computer inactief moet zijn voordat de slaapstand in werking treedt. Geef de waarde **0** op als u niet wilt dat energiebeheer de computer naar de slaapstand laat overschakelen.|  
|**Een wachtwoord vereisen bij uit slaapstand komen**|Een **Ja** of **Nee** waarde geeft aan of een wachtwoord vereist voor het ontgrendelen van de computer wanneer deze wake uit de slaapstand krijgt is.|  
|**Actie knop Energie**|Hiermee geeft u de actie aan die moet worden uitgevoerd wanneer de aan-uitknop van de computer wordt ingedrukt. Hiermee geeft u de actie aan die wordt uitgevoerd wanneer de gebruiker het deksel een draagbare computer sluit. Mogelijke waarden **niets doen**, **slaapstand**, **slaapstand**, en **afgesloten**.|  
|**Aan-uitknop in het menu Start**|Hiermee geeft u de actie op die wordt uitgevoerd wanneer u in het menu Start op de knop **Aan/uit** klikt. Hiermee geeft u de actie aan die wordt uitgevoerd wanneer de gebruiker het deksel een draagbare computer sluit. Mogelijke waarden **slaapstand**, **slaapstand**, en **afgesloten**.|  
|**Actie van de slaapstandknop**|Hiermee geeft u de actie aan die wordt uitgevoerd wanneer u op de computer op de **slaapstandknop** drukt. Hiermee geeft u de actie aan die wordt uitgevoerd wanneer de gebruiker het deksel een draagbare computer sluit. Mogelijke waarden **niets doen**, **slaapstand**, **slaapstand**, en **afgesloten**.|  
|**Actie deksel sluiten**|Hiermee geeft u de actie aan die wordt uitgevoerd wanneer de gebruiker het deksel een draagbare computer sluit. Mogelijke waarden **niets doen**, **slaapstand**, **slaapstand**, en **afgesloten**.|  
|**Vaste schijf uitschakelen na (minuten)**|Hiermee geeft u de tijdsduur aan in minuten die de vaste schijf van computer inactief moet zijn voordat de schijf wordt uitgeschakeld. Geef de waarde **0** op als u niet wilt dat energiebeheer de vaste schijf van de computer uitschakelt.|  
|**Sluimerstand na (minuten)**|Hiermee geeft u de tijdsduur in minuten aan die de computer inactief moet zijn voordat de sluimerstand in werking treedt. Geef de waarde **0** op als u niet wilt dat energiebeheer de computer naar de sluimerstand overschakelt.|  
|**Actie batterij laag**|Hiermee geeft u de actie aan die zich voordoet wanneer de accu van de computer het opgegeven lage meldingsniveau bereikt. Hiermee geeft u de actie aan die wordt uitgevoerd wanneer de gebruiker het deksel een draagbare computer sluit. Mogelijke waarden **niets doen**, **slaapstand**, **slaapstand**, en **afgesloten**.|  
|**Actie kritieke batterij**|Hiermee geeft u de actie aan die wordt genomen wanneer de accu van de computer het opgegeven kritieke meldingsniveau bereikt. Hiermee geeft u de actie aan die wordt uitgevoerd wanneer de gebruiker het deksel een draagbare computer sluit. Mogelijke waarden zijn **slaapstand**, **slaapstand**, en **afgesloten**.|  
|**Hybride slaapstand toestaan**|Selecteren van de **op** of **uit** waarde geeft aan of Windows een sluimerstandbestand slaat bij het invoeren van de slaapstand, die kan worden gebruikt om de status van de computer in het geval van stroomstoring herstellen terwijl slaapstand heeft ingevoerd.<br /><br /> De hybride slaapstand is bedoeld voor desktopcomputers en is standaard niet ingeschakeld op draagbare computers. Op computers waarop Windows 7 wordt uitgevoerd, schakelt u met de hybride slaapstand de functionaliteit van de sluimerstand in.|  
|**Stand-bystatus toestaan tijdens slaapactie**|Selecteren van de **op** of **uit** waarde schakelt u de computer als stand-by die nog steeds verbruikt sommige stroom, maar kan de computer in slaapstand sneller. Als deze instelling wordt ingesteld op **Uit**kan de computer alleen in de sluimerstand worden gezet of worden uitgeschakeld.|  
|**Vereiste inactiviteit voor slaapstand (%)**|Hiermee geeft u het percentage niet-actieve tijd van de processortijd van de computer op die is vereist om de computer te laten overschakelen naar de slaapstand. Voor computers met Windows 7, altijd deze waarde is ingesteld op **0**.|  
|**Windows-ontwaaktimer inschakelen voor bureaubladcomputers**|Selecteren van de **inschakelen** of **uitschakelen** waarde timer voor het ingebouwde Windows moeten worden gebruikt door energiebeheer voor wake-een desktopcomputer kunt inschakelen. Wanneer een desktopcomputer wordt geactiveerd door middel van de Windows-ontwaaktimer, blijft deze standaard 10 minuten actief zodat de computer updates kan installeren of beleid kan ontvangen.<br /><br /> Ontwaaktimers worden niet ondersteund op draagbare computers om te voorkomen dat ze worden geactiveerd wanneer ze niet op netstroom zijn aangesloten.|  

