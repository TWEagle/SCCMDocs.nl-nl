---
title: Classificaties en producten configureren
titleSuffix: Configuration Manager
description: Volg deze stappen voor het configureren van software-updateclassificaties en producten voor synchronisatie in de Configuration Manager-console.
keywords: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 04/10/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.openlocfilehash: 9ba0872b1d2e4ef5dd027df3f7c16a6b3a94e9ac
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
#  <a name="configure-classifications-and-products-to-synchronize"></a>Configureer classificaties en producten voor synchronisatie  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


> [!NOTE]  
>  Volg de procedure in deze sectie enkel op de site op het hoogste niveau.  

 Metagegevens van software-updates opgehaald tijdens het synchronisatieproces in Configuration Manager, op basis van de instellingen die u in de eigenschappen van Software-updatepunt opgeeft. Na het synchroniseren van software-updates voor de eerste keer, of wanneer nieuwe producten en classificaties worden vrijgegeven, moet u Ga naar eigenschappen van de nieuwe items selecteren. Volg de volgende procedure om classificaties en producten te configureren die moeten worden gesynchroniseerd.  

#### <a name="to-configure-classifications-and-products-to-synchronize"></a>Classificaties en producten configureren die moeten worden gesynchroniseerd  

1.  In de **Configuration Manager** console, gaat u naar **beheer** > **siteconfiguratie** > **Sites**.

2. Selecteer de centrale beheersite of de zelfstandige primaire site.  

3.  Klik op het tabblad **Start** in de groep **Instellingen** op **Sitecomponenten configureren**en klik op **Software-updatepunt**.

4.  Geef op het tabblad **Classificaties** de software-updateclassificaties waarvoor u software-updates wilt synchroniseren.  

    > [!NOTE]  
    >  Elke software-update wordt gedefinieerd met een updateclassificatie die helpt de verschillende types updates te organiseren. Tijdens het synchronisatieproces worden de metagegevens van de software-updates voor de opgegeven classificaties gesynchroniseerd. Configuration Manager biedt de mogelijkheid om te synchroniseren van software-updates met de volgende updateclassificaties:  
    >   
    > - **Essentiële Updates**: Geeft een ruim vrijgegeven update voor een specifiek probleem die zijn gericht op een kritieke fout niet gerelateerd.  
    > - **Definitie-Updates**: Hiermee geeft u een update aan voor antivirus- of andere definitiebestanden.  
    > - **Functiepakketten**: Geeft nieuwe productfuncties die zijn gedistribueerd buiten een productrelease en die gewoonlijk zijn opgenomen in de volgende productrelease.  
    > - **Beveiligingsupdates**: Hiermee geeft u een grote schaal uitgebrachte update aan voor een productspecifiek en beveiligingsgerelateerd probleem.  
    > - **Servicepacks**: Hiermee geeft u een volledige reeks van hotfixes die op een toepassing worden toegepast. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, software-updates, enzovoort.  
    > - **Hulpprogramma's voor**: Hiermee geeft u een hulpprogramma of onderdeel dat u een of meer taken kunt voltooien.  
    > - **Updatepakketten**: Hiermee geeft u een volledige reeks van hotfixes die samen zijn verpakt voor een gemakkelijke implementatie. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, enzovoort. Een updatepakket gaat in het algemeen over een specifiek gebied, zoals beveiliging of een productcomponent.  
    > - **Updates**: Hiermee geeft u een update aan voor een toepassing of bestand dat momenteel is geïnstalleerd.  
    > - **Upgrade**: Hiermee geeft u een upgrade voor Windows 10-functies en functionaliteit. De software-updatepunten en de sites moeten uitvoeren een minimum van WSUS 4.0 met de [hotfix 3095113](https://support.microsoft.com/kb/3095113) ophalen van de **Upgrade** classificatie.    
    >       

    > [!NOTE]    
    > Vanaf Configuration Manager versie 1706, kunt u de **opnemen Microsoft Surface stuurprogramma's en firmware-updates** selectievakje in om te synchroniseren van de Microsoft Surface stuurprogramma's.<!--1098490--> Alle software-updatepunten moeten Windows Server 2016 om te synchroniseren met succes Surface stuurprogramma's worden uitgevoerd. Als u een software-updatepunt op een computer met Windows Server 2012 nadat u Surface stuurprogramma's inschakelen inschakelt, zijn de scanresultaten voor de updates voor stuurprogramma's niet juist. Dit resulteert in een onjuiste compatibiliteitsgegevens weergegeven in de Configuration Manager-console en in de Configuration Manager-rapporten.  
    >  
    > Deze functie is geïntroduceerd in versie 1706 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Vanaf versie 1710, deze functie is niet langer een voorlopige versie.  
    >  
    > Configuration Manager deze optionele functie standaard niet ingeschakeld. Voordat u deze gebruikt, moet u deze functie inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  

5.  Geef op het tabblad **Producten** de producten op waarvoor u software-updates wilt synchroniseren, en klik vervolgens op **Sluiten**.  

    > [!NOTE]  
    >  De metagegevens voor elke software-update definiëren de producten waarvoor de update van toepassing is. Een product is een specifieke editie van een besturingssysteem of toepassing, zoals Windows Server 2012. Een productfamilie is het basisbesturingssysteem of de basistoepassing waarvan de afzonderlijke producten zijn afgeleid. Een voorbeeld van een productfamilie is Windows, waarvan Windows Server 2012 een lid is. U kunt een productfamilie of individuele producten binnen een productfamilie opgeven. Hoe meer producten u selecteert, hoe langer het duurt om softwareupdates te synchroniseren.  
    >   
    >  Wanneer software-updates van toepassing op meerdere producten zijn, en ten minste één van de producten was geselecteerd voor synchronisatie, worden alle producten weergegeven in de Configuration Manager-console zelfs als sommige producten niet werden geselecteerd. Als Windows Server 2012 is het enige besturingssysteem die u hebt geselecteerd, en als een software-update van toepassing op Windows 8 en Windows Server 2012, kunt u voor beide producten, worden weergegeven in de Configuration Manager-console.  

    > [!IMPORTANT]  
    >  Configuration Manager slaat een lijst van producten en productfamilies op waaruit u kunt kiezen wanneer u eerst installeert de software-updatepunt. Producten en productfamilies die zijn vrijgegeven nadat Configuration Manager is uitgebracht mogelijk niet beschikbaar om te selecteren tot u de synchronisatie van software-updates, die de lijst van beschikbare prdoucten en productfamilies waaruit u kunt updates voltooid.  

## <a name="next-steps"></a>Volgende stappen
Start de synchronisatie van software-updates voor het ophalen van software-updates op basis van de nieuwe criteria. Zie voor meer informatie [software-updates synchroniseren](synchronize-software-updates.md).
