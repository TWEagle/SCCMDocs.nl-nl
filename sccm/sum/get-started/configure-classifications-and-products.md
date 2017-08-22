---
title: Configureer classificaties en producten voor synchronisatie | Microsoft Docs
description: Volg deze stappen voor het configureren van classificaties en producten voor synchronisatie in de Configuration Manager-console.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.openlocfilehash: 2da61e6e06850b36543b9fd41bd9a7d2368006fb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
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
    > Vanaf Configuration Manager versie 1706, u kunt ook selecteren de **opnemen Microsoft Surface stuurprogramma's en firmware-updates** selectievakje in om te synchroniseren van de Microsoft Surface stuurprogramma's. Alle software-updatepunten moeten Windows Server 2016 om te synchroniseren met succes Surface stuurprogramma's worden uitgevoerd.     
    >    
    > Dit is een functie van de voorlopige versie. Functies van evaluatieversies zijn opgenomen in het product voor vroege testdoeleinden in een productieomgeving, maar mogen niet worden beschouwd als gereed voor productie. U moet deze functie voor beschikbaar wilt inschakelen. Zie [Use pre-release features from updates](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease) (Functies van evaluatieversies gebruiken) voor meer informatie.

5.  Geef op het tabblad **Producten** de producten op waarvoor u software-updates wilt synchroniseren, en klik vervolgens op **Sluiten**.  

    > [!NOTE]  
    >  De metagegevens voor elke software-update definiëren de producten waarvoor de update van toepassing is. Een product is een specifieke editie van een besturingssysteem of toepassing, zoals Windows Server 2012. Een productfamilie is het basisbesturingssysteem of de basistoepassing waarvan de afzonderlijke producten zijn afgeleid. Een voorbeeld van een productfamilie is Windows, waarvan Windows Server 2012 een lid is. U kunt een productfamilie of individuele producten binnen een productfamilie opgeven. Hoe meer producten u selecteert, hoe langer het duurt om software-updates te synchroniseren.  
    >   
    >  Wanneer software-updates van toepassing op meerdere producten zijn, en ten minste één van de producten was geselecteerd voor synchronisatie, zullen alle producten weergegeven in de Configuration Manager-console zelfs als sommige producten niet werden geselecteerd. Als Windows Server 2012 is het enige besturingssysteem die u hebt geselecteerd, en als een software-update van toepassing op Windows 8 en Windows Server 2012, wordt bijvoorbeeld beide producten weergegeven in de Configuration Manager-console.  

    > [!IMPORTANT]  
    >  Configuration Manager slaat een lijst van producten en productfamilies op waaruit u kunt kiezen wanneer u eerst installeert de software-updatepunt. Producten en productfamilies die zijn vrijgegeven nadat Configuration Manager is uitgebracht mogelijk niet beschikbaar om te selecteren tot u de synchronisatie van software-updates, die de lijst van beschikbare prdoucten en productfamilies waaruit u kunt updates voltooid.  

## <a name="next-steps"></a>Volgende stappen
Start de synchronisatie van software-updates voor het ophalen van software-updates op basis van de nieuwe criteria. Zie voor meer informatie [software-updates synchroniseren](synchronize-software-updates.md).
