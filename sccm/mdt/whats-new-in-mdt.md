---
title: Wat is er nieuw in MDT 2013 handleiding
titleSuffix: Microsoft Deployment Toolkit
description: 'Meer informatie over de Microsoft Deployment Toolkit 2013. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 17466fa9-1a26-4dd8-a36f-c0c68fa1984c
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fd207a77bad880a37cf04abc159aac6689a99afe
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2018
---
# <a name="whats-new-in-microsoft-deployment-toolkit-mdt-2013-guide"></a>Wat is nieuw in Microsoft Deployment Toolkit (MDT) 2013-handleiding
Microsoft Deployment Toolkit (MDT) 2013 is de volgende versie van Microsoft Solution Accelerator voor besturingssysteem en de implementatie van de toepassing. Het doel van deze handleiding is om uit te leggen van de wijzigingen in MDT 2013 van MDT 2012 Update 1.  

 Deze handleiding worden beschreven van de versie van MDT 2013 specifiek en wordt ervan uitgegaan dat bekend bent met eerdere MDT versie concepten, functies en mogelijkheden.  

> [!NOTE]   
>  In dit document, *Windows* geldt voor de besturingssystemen Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 en Windows Server 2008 R2, tenzij anders vermeld. MDT biedt geen ondersteuning voor ARM-processor gebaseerde versies van Windows. Op deze manier *MDT* verwijst naar MDT 2013, tenzij anders vermeld.  

## <a name="whats-new-in-this-release"></a>Wat is er nieuw in deze Release  
 MDT biedt verschillende verbeteringen die voegt nieuwe functies en de gebruikerservaring met MDT verbetert. Daarnaast bevat deze versie van MDT veel andere kleine verbeteringen en oplossingen voor problemen die niet hieronder worden vermeld.  

### <a name="support-for-upgrading-from-previous-versions-of-mdt"></a>Ondersteuning voor het upgraden van eerdere versies van MDT  
 MDT biedt ondersteuning voor een upgrade uitvoert van MDT 2012 Update 1.  

> [!NOTE]   
>  Maak een back-up van de bestaande infrastructuur van de MDT voordat u probeert een upgrade.  

### <a name="support-for-windows-81-and-windows-server-2012-r2"></a>Ondersteuning voor Windows 8.1 en Windows Server 2012 R2  
 U kunt MDT gebruiken voor het implementeren van de besturingssystemen Windows 8.1 en Windows Server 2012 R2 met behulp van de LTI ZTI en UDI implementatiemethoden. Functies en onderdelen die specifiek zijn voor Windows 8.1 en Windows Server 2012 R2 zijn beschikbaar in de lijst van de rol.  

### <a name="support-for-the-windows-adk-for-windows-81"></a>Ondersteuning voor Windows ADK voor Windows 8.1  
 MDT biedt ondersteuning voor het gebruik van de Windows ADK voor Windows 8.1 om besturingssystemen te implementeren. De Windows ADK voor Windows 8.1 omvat de implementatiehulpprogramma's zoals het hulpprogramma Deployment Image Servicing and Management (DISM) Windows Pre-Installation Environment (Windows PE) en de gebruiker staat Migration Tool (USMT).  

### <a name="support-for-system-center-2012-r2-configuration-manager"></a>Ondersteuning voor System Center 2012 R2 Configuration Manager  
 Ondersteuning voor integratie met System Center 2012 R2 Configuration Manager, met inbegrip van nieuwe mogelijkheden, zoals meerdere Netwerktoegangsaccounts ZTI en UDI implementatiemethoden in MDT.  

### <a name="improved-deployment-to-x86-based-computers-that-use-the-uefi-standard"></a>Verbeterde implementatie x86 86-Computers die gebruikmaken van de standaard UEFI  
 Unified Extensible Firmware Interface (UEFI) is een specificatie die een software-interface tussen een besturingssysteem en platform firmware definieert. UEFI is veiliger vervanging voor de oudere basic input/output system (BIOS)-firmware-interface aanwezig zijn in sommige computers personal blootgesteld aan schadelijke software die aanvallen tijdens het opstarten of inschakelen processen zelf testen uitvoert.  

 MDT maakt standaard de juiste partities ter ondersteuning van computers met UEFI. MDT biedt ondersteuning voor UEFI-versies van 2.0 tot 2.3.1-specificaties. UEFI 2.3.1-specificaties is een nieuwere versie van UEFI die zullen worden gebruikt op Windows 8-logo-compatibele computers.  

 Zie de sectie 'Implementeren op Computers met UEFI', in de MDT-document voor meer informatie over ondersteuning voor UEFI in MDT *met behulp van de Microsoft Deployment Toolkit*.  

## <a name="whats-been-removed-from-this-release"></a>Wat verwijderd uit deze versie?  
 Deze versie van MDT omvat niet de volgende functies die beschikbaar waren in eerdere versies van MDT:  

-   Implementatie van Windows 8.1 Preview  

-   Implementatie van Windows Server 2012 R2 Preview  

-   ZTI met  

    -   System Center Configuration Manager 2007  

    -   System Center 2012 Configuration Manager  

    -   System Center 2012 Configuration Manager SP1  

    -   System Center 2012 R2 Configuration Manager Preview  

-   Gebruik van Windows ADK voor Windows 8  

-   Gebruik van de Windows AIK voor Windows 7  

-   Implementatie van Windows XP of WindowsServer 2003  

-   Implementatie van Windows Vista of WindowsServer 2008  

-   Out of box groepsbeleidsobjecten (GPO's) van Security naleving Manager (SCM). Hulpprogramma's en groepsbeleidsobjecten moeten worden geïnstalleerd met SCM voordat ze kunnen worden gebruikt in MDT.  

## <a name="operating-system-support-in-this-release"></a>Ondersteuning voor besturingssysteem in deze Release  
De volgende tabel bevat de ondersteuning van het besturingssysteem dat LTI en implementaties van ZTI in deze versie van MDT bieden.  

|||||  
|-|-|-|-|  
|Besturingssysteem|LTI|ZTI|UDI|  
|Windows 8.1|●|●|●|  
|Windows Server 2012 R2|●|●||  
|Windows 8|●|●|●|  
|Windows Server 2012|●|●||  
|Windows 7|●|●|●|  
|Windows Server 2008 R2|●|●||  
|Windows PE-versie 5.0|●|●|●|  

 ● = ondersteund  

## <a name="windows-adk-support"></a>Windows ADK-ondersteuning  
 De volgende tabel bevat de Windows ADK en de Windows AIK-ondersteuning die implementaties van LTI, ZTI en UDI in MDT opgeven.  

|||||  
|-|-|-|-|  
|Windows ADK|LTI|ZTI|UDI|  
|Windows ADK voor Windows 8.1|●|●|●|  

 ● = ondersteund  

## <a name="microsoft-net-framework-and-windows-powershell-support"></a>Microsoft .NET Framework en Windows PowerShell-ondersteuning  
De volgende tabel bevat de versies van Microsoft .NET Framework en Windows PowerShell die worden ondersteund door MDT door de versie van Windows-besturingssysteem.  


||||  
|-|-|-|  
|Windows-versie|.NET|PowerShell|  
|Windows 8.1|4.0|3.0|  
|Windows Server 2012 R2|4.0|3.0|  
|Windows 8|4.0|3.0|  
|Windows Server 2012|4.0|3.0|  
|Windows 7|3.5 met SP1|2.0|  
|Windows Server 2008 R2|3.5 met SP1|2.0|
