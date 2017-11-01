---
title: App-V virtuele omgevingen maken
titleSuffix: Configuration Manager
description: Virtuele omgevingen maken met Microsoft Application Virtualization zodat apps gegevens met elkaar kunnen delen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6b86078-fcc4-46cf-87d6-4b52b914b712
caps.latest.revision: "6"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 2b831f4302657e8338dddea32bca26677472bd42
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-app-v-virtual-environments-in-system-center-configuration-manager"></a>App-V virtuele omgevingen maken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In een Microsoft Application Virtualization (App-V) kunnen het delen van virtuele omgeving zijn geïmplementeerd in System Center Configuration Manager (Configuration Manager), virtuele toepassingen hetzelfde bestandssysteem en register op de client Windows-pc's. In tegenstelling tot virtuele standaardtoepassingen, kunnen deze toepassingen gegevens met elkaar delen. Virtuele omgevingen zijn gemaakt of gewijzigd op de client-pc's wanneer de toepassing wordt geïnstalleerd of wanneer clients vervolgens hun geïnstalleerde toepassingen evalueren. U kunt deze toepassingen zodanig rangschikken dat wanneer meerdere toepassingen proberen een bestandssysteem of registerwaarde te wijzigen, de toepassing met het hoogste rangnummer prioriteit krijgt.  

> [!IMPORTANT]  
>  Vertrouw niet op de App-V virtuele omgevingen bescherming, zoals bieden tegen schadelijke software.  

 Gebruik de volgende procedure voor het maken van een virtuele omgeving van App-V in Configuration Manager.  

## <a name="create-an-app-v-virtual-environment"></a>Maak een virtuele omgeving van App-V  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **virtuele omgevingen van App-V**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **virtuele omgeving maken**.  

4.  In de **virtuele omgeving maken** dialoogvenster en voer de volgende informatie:  

    -   **Naam**.  Geef een unieke naam voor de virtuele omgeving (maximaal 128 tekens).  

    -   **Beschrijving**. (Optioneel) Voer een beschrijving voor de virtuele omgeving.  

5.  Als u wilt een nieuw implementatietype toevoegen aan de virtuele omgeving, kies **toevoegen**. U moet minstens één implementatietype toevoegen.  

6.  In de **toepassingen toevoegen** dialoogvenster geeft u een **groepsnaam** (maximaal 128 tekens). U gebruikt deze naam om te verwijzen naar de groep van toepassingen die u aan de virtuele omgeving toevoegt.  

7.  Kies **toevoegen**, selecteert u de App-V 5-toepassingen en implementatietypen die u wilt toevoegen aan de groep en kies vervolgens **OK**.  

8.  In de **toepassingen toevoegen** in het dialoogvenster kunt u **rangnummer verhogen** of **rangnummer** om in te stellen van de toepassing die prioriteit krijgt als meerdere toepassingen proberen instellingen van bestandssysteem of het register in dezelfde virtuele omgeving te wijzigen.  

9. Terugkeren naar de **virtuele omgeving maken** dialoogvenster Kies **OK**.  

10. Wanneer u klaar bent met het toevoegen van groepen kiezen **OK** voor het maken van de virtuele omgeving. De nieuwe virtuele omgeving wordt weergegeven in de **virtuele omgevingen van App-V** knooppunt van de Configuration Manager-console. U kunt de status van uw virtuele omgevingen bewaken met behulp van de Status van virtuele omgeving App-V-rapport.  

    > [!NOTE]  
    >  De virtuele omgeving wordt toegevoegd of gewijzigd op de client-pc's wanneer de toepassing wordt geïnstalleerd of wanneer de client geïnstalleerde toepassingen daarna worden geëvalueerd.  
