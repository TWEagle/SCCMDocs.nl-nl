---

title: Configureer classificaties en producten voor synchronisatie | Microsoft-documenten
description: Volg deze stappen om classificaties en producten voor synchronisatie in de Configuration Manager-console te configureren.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 6add66e625c790b65edf64216c2262a5d082f820
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017



---
#  <a name="configure-classifications-and-products-to-synchronize"></a>Configureer classificaties en producten voor synchronisatie  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


> [!NOTE]  
>  Volg de procedure in deze sectie enkel op de site op het hoogste niveau.  

 Metagegevens van software-updates opgehaald tijdens het synchronisatieproces in Configuration Manager, op basis van de instellingen die u in de eigenschappen van Software-updatepunt opgeeft. Nadat u software-updates voor het eerst synchroniseert, of wanneer er nieuwe producten en classificaties zijn uitgebracht, u naar de eigenschappen gaat naar de nieuwe items te selecteren. Volg de volgende procedure om classificaties en producten te configureren die moeten worden gesynchroniseerd.  

#### <a name="to-configure-classifications-and-products-to-synchronize"></a>Classificaties en producten configureren die moeten worden gesynchroniseerd  

1.  In de **Configuration Manager** console, navigeert u naar **beheer** > **siteconfiguratie** > **Sites**.

2. Selecteer de centrale beheersite of de zelfstandige primaire site.  

3.  Klik op het tabblad **Start** in de groep **Instellingen** op **Sitecomponenten configureren**en klik op **Software-updatepunt**.

4.  Geef op het tabblad **Classificaties** de software-updateclassificaties waarvoor u software-updates wilt synchroniseren.  

    > [!NOTE]  
    >  Elke software-update wordt gedefinieerd met een updateclassificatie die helpt de verschillende types updates te organiseren. Tijdens het synchronisatieproces worden de metagegevens van de software-updates voor de opgegeven classificaties gesynchroniseerd. Configuration Manager biedt de mogelijkheid softwareupdates te synchroniseren met de volgende updateclassificaties:  
    >   
    > - **Essentiële Updates**: Geeft een ruim vrijgegeven update voor een specifiek probeem om een kritieke bug niet-beveiliging.  
    > - **Definitie-Updates**: Hiermee geeft u een update voor antivirus- of andere definitiebestanden.  
    > - **Functie Packs**: Geeft nieuwe productfuncties die zijn gedistribueerd buiten een productrelease en die gewoonlijk zijn opgenomen in de volgende productrelease.  
    > - **Beveiligingsupdates**: Geeft een ruim vrijgegeven update voor een probleem met de productspecifieke, productspecifieke beveiliging.  
    > - **Service Packs**: Hiermee geeft u een volledige reeks hotfixes die op een toepassing worden toegepast. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, software-updates, enzovoort.  
    > - **Hulpprogramma's**: Geeft een hulpprogramma of functie die u helpt een of meer taken te voltooien.  
    > - **Updatepakketten**: Hiermee geeft u een volledige reeks hotfixes die samen zijn verpakt voor een gemakkelijke implementatie. Deze hotfixes omvatten beveiligingsupdates, essentiële updates, enzovoort. Een updatepakket gaat in het algemeen over een specifiek gebied, zoals beveiliging of een productcomponent.  
    > - **Updates**: Hiermee geeft u een update voor een toepassing of bestand dat momenteel wordt geïnstalleerd.  
    > - **Upgrade**: Hiermee geeft u een upgrade voor Windows 10-functies en -functionaliteit.  
    >   
    >      De software-updatepunten en de sites moeten uitvoeren een minimum van WSUS 4.0 met de [hotfix 3095113](https://support.microsoft.com/kb/3095113) om op te halen de **Upgrade** classificatie.  

5.  Geef op het tabblad **Producten** de producten op waarvoor u software-updates wilt synchroniseren, en klik vervolgens op **Sluiten**.  

    > [!NOTE]  
    >  De metagegevens voor elke software-update definiëren de producten waarvoor de update van toepassing is. Een product is een specifieke editie van een besturingssysteem of toepassing, zoals Windows Server 2012. Een productfamilie is het basisbesturingssysteem of de basistoepassing waarvan de afzonderlijke producten zijn afgeleid. Een voorbeeld van een productfamilie is Windows, waarvan Windows Server 2012 een lid is. U kunt een productfamilie of individuele producten binnen een productfamilie opgeven. Hoe meer producten u selecteert, hoe langer het duurt om software-updates te synchroniseren.  
    >   
    >  Wanneer software-updates van toepassing op meerdere producten zijn, en ten minste één van de producten was geselecteerd voor synchronisatie, zullen alle producten weergegeven in de Configuration Manager-console zelfs als sommige producten niet werden geselecteerd. Bijvoorbeeld, als Windows Server 2012 is het enige besturingssysteem die u hebt geselecteerd, en als een software-update van toepassing op Windows 8 en Windows Server 2012, dan worden beide producten in de Configuration Manager-console weergegeven.  

    > [!IMPORTANT]  
    >  Configuration Manager slaat een lijst van producten en productfamilies op waaruit u kunt kiezen wanneer u eerst installeert de software-updatepunt. Producten en productfamilies die zijn vrijgegeven nadat Configuration Manager is uitgebracht mogelijk niet beschikbaar om te selecteren tot u de synchronisatie van software-updates, die de lijst van beschikbare prdoucten en productfamilies op waaruit u kunt kiezen bijgewerkt voltooid.  


## <a name="next-steps"></a>Volgende stappen
Start de synchronisatie van software-updates om software-updates op basis van de nieuwe criteria ophalen. Zie voor meer informatie, [software-updates synchroniseren](synchronize-software-updates.md).

