---
title: Zelfstandige media gebruiken om Windows te implementeren zonder gebruik van het netwerk
titleSuffix: Configuration Manager
description: Gebruik zelfstandige media in Configuration Manager voor het implementeren van besturingssystemen, waarbij de bandbreedte beperkt wordt of als een optie voor het vernieuwen, te installeren of bijwerken van computers.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58a0d2ae-de76-401f-b854-7a5243949033
caps.latest.revision: "16"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 1da213763c99af69963b12b15fa8413f9e1965dc
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="use-stand-alone-media-to-deploy-windows-without-using-the-network-in-system-center-configuration-manager"></a>Zelfstandige media gebruiken om Windows te implementeren zonder gebruik van het netwerk in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Zelfstandige media in System Center Configuration Manager bevat alles wat vereist is om een besturingssysteem op een computer te implementeren. Dit omvat de opstartinstallatiekopie, de installatiekopie van het besturingssysteem en de takenreeks voor het installeren van het besturingssysteem, met inbegrip van toepassingen en stuurprogramma's, enzovoort. Met implementaties met zelfstandige media kunt u besturingssystemen implementeren in volgende situaties:  

-   In omgevingen waar het niet praktisch is om een installatiekopie van een besturingssysteem of andere grote pakketten over het netwerk te kopiëren.  

-   In omgevingen zonder netwerkverbinding of de met lage netwerkbandbreedte.  

U kunt voor de volgende scenario's voor besturingssysteemimplementaties zelfstandige media gebruiken:  

-   [Een bestaande computer vernieuwen met een nieuwe versie van Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Een nieuwe versie van Windows op een nieuwe computer (bare-metal) installeren](install-new-windows-version-new-computer-bare-metal.md)  

-   [Windows bijwerken naar de laatste versie](upgrade-windows-to-the-latest-version.md)  

 Voer de stappen in een van de implementatiescenario’s voor besturingssystemen en gebruik de volgende secties om de zelfstandige media voor te bereiden en te maken.  

## <a name="task-sequence-actions-not-supported-when-using-stand-alone-media"></a>Takenreeksacties die niet worden ondersteund bij het gebruik van zelfstandige media  
 Als u de stappen in een van de ondersteunde scenario's voor besturingssysteemimplementaties, de te implementeren takenreeks of upgrade hebt voltooid, is het besturingssysteem gemaakt en alle bijbehorende inhoud gedistribueerd naar een distributiepunt. Wanneer u zelfstandig media gebruikt, worden de volgende acties in de takenreeks niet ondersteund:  

-   De stap Stuurprogramma's automatisch toepassen in de takenreeks. Automatische toepassing van apparaatstuurprogramma's uit de stuurprogrammacatalogus wordt niet ondersteund, maar u kunt de stap Stuurprogramma's automatisch toepassen kiezen om een specifieke reeks stuurprogramma's beschikbaar te maken voor Windows Setup.  

-   Installatie van software-updates.  

-   Software installeren voordat het besturingssysteem wordt geïmplementeerd.  

-   Koppelen van gebruikers aan de doelcomputer ter ondersteuning van de gebruikersaffiniteit van apparaten.  

-   Dynamische pakket wordt geïnstalleerd via de taak Pakketten installeren.  

-   Dynamische toepassing wordt geïnstalleerd via de toepassing Taak installeren.  

> [!NOTE]  
>  Als uw takenreeks voor het implementeren van een besturingssysteem bevat de [pakket installeren](../understand/task-sequence-steps.md#BKMK_InstallPackage) stap en u de zelfstandige media maken op een centrale beheersite, een fout optreden. De centrale beheersite beschikt niet over de benodigde beleidsregels voor clientconfiguratie om de agent voor softwaredistributie in te schakelen tijdens het uitvoeren van de takenreeks. Mogelijk wordt de volgende fout in het bestand CreateTsMedia.log weergegeven:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`
>   
>  Voor zelfstandige media met een **pakket installeren** stap heeft, moet u de zelfstandige media maken op een primaire site die de agent voor softwaredistributie is ingeschakeld of Voeg een [opdrachtregel uitvoeren](../understand/task-sequence-steps.md#BKMK_RunCommandLine) stap na de [Windows en ConfigMgr installeren](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) stap en voor de eerste **pakket installeren** stap in de takenreeks wordt uitgevoerd. Met de stap **Opdrachtregel uitvoeren** wordt een WMIC-opdracht uitgevoerd waarmee de agent voor softwaredistributie wordt ingeschakeld voordat de eerste stap Pakket installeren wordt uitgevoerd. U kunt de volgende opdracht gebruiken in de takenreeksstap **Opdrachtregel uitvoeren** :  
>   
>  **Opdrachtregel**: **WMIC/namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName = "Enable SWDist", Enabled = "true", LockSettings = "TRUE", PolicySource = "local", PolicyVersion = "1.0", SiteSettingsKey = "1" / NOINTERACTIVE**  

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren  
 Als u het implementatieproces voor een besturingssysteem wilt starten vanaf zelfstandige media, moet u de implementatie configureren om het besturingssysteem beschikbaar te stellen voor media. U kunt dit configureren op de pagina **Implementatie-instellingen** van de wizard Software implementeren of op het tabblad **Implementatie-instellingen** in de eigenschappen voor de implementatie.  Configureer een van de volgende waarden voor de instelling **Toegankelijk maken voor de volgende** :  

-   **Configuration Manager-clients, media en PXE**  

-   **Alleen media en PXE**  

-   **Alleen media en PXE (verborgen)**  

## <a name="create-the-stand-alone-media"></a>Zelfstandige media maken  
 U kunt opgeven of de zelfstandige media een USB-flashstation of een cd/dvd-set is. De optie die u als opstartbaar station kiest, moet worden ondersteund door de computer waarop de media worden gestart. Zie voor meer informatie [zelfstandige media maken](create-stand-alone-media.md).  

## <a name="install-the-operating-system-from-stand-alone-media"></a>Het besturingssysteem installeren vanaf zelfstandige media  
 Plaats de zelfstandige media in een opstartbaar station op de computer en schakel deze vervolgens in om het besturingssysteem te installeren.  
