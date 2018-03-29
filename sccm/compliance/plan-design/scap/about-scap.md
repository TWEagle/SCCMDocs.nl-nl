---
title: Over uitbreidingen Security Content Automation Protocol (SCAP)
titleSuffix: System Center Configuration Manager
description: Meer informatie over de extensies Security Content Automation Protocol (SCAP)
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a315489d-5e12-46d6-903e-3a35235b72c5
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: fc986e2175583124377ccb7c080df4b219ea8df0
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="about-the-security-content-automation-protocol-scap-extensions"></a>Over de extensies Security Content Automation Protocol (SCAP)

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

> [!Tip]  
> Deze functie is geïntroduceerd in Technical Preview-versie 1803 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Deze voorlopige versie van de SCAP-extensies kan worden geïnstalleerd op alle ondersteunde versies van de huidige vertakking van Configuration Manager en LTSB 1606. Het installatiebestand bevindt zich op cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi vanaf technical preview 1803. 

De SCAP-extensies voor Microsoft System Center Configuration Manager helpt u bij het analyseren en beoordelen van uw netwerkomgeving voor compatibiliteit met de Security Content Automation Protocol (SCAP). SCAP is gedefinieerd en beheerd door het Amerikaanse National Institute of Standards and Technology (NIST).

De SCAP-extensies voor Microsoft System Center Configuration Manager gebruikt de functie instellingen voor naleving in Microsoft System Center Configuration Manager op de computers in uw omgeving te scannen en vervolgens het nalevingsniveau met de Verenigde Mandaat States Government Configuration Baseline (USGCB).

De uitbreidingen inschakelen Configuration Manager-gegevensstromen Security Content Automation Protocol (SCAP) gebruiken, systemen te beoordelen op naleving en rapportresultaten te genereren in SCAP-indeling. Uw organisatie kan uw bestaande Configuration Manager-infrastructuur gebruiken om te zorgen voor computers die u beheert voldoen aan deze nationale nalevingsvereiste en de vereiste USGCB-rapporten genereren voor het National Institute of Standards and Technology (NIST) en de Verenigde Staten Office van beheer en Budget (OMB).

Deze handleiding bevat informatie over het installeren, configureren en uitvoeren van de SCAP-extensies in de System Center Configuration Manager-infrastructuur.



# <a name="what39s-new-in-scap-extensions-prerelease-for-microsoft-system-center-configuration-manager"></a>Wat&#39;s Nieuw in SCAP-extensies Prerelease voor Microsoft System Center Configuration Manager

Gebruik deze sectie voor informatie over wat u&#39;nieuwe functies in de meest recente versie.

SCAP-extensies Prerelease voor System Center Configuration Manager:

- Een Configuration Manager-Console-extensie die biedt volledige ondersteuning voor converteren van SCAP-inhoud naar basislijnen voor compatibiliteitsinstellingen voor de huidige vertakking van System Center Configuration Manager bevat
- Ondersteunt SCAP versie 1.2 en is achterwaarts compatibel met de SCAP-versies 1.1 en 1.0.


  - Ondersteunt Extensible Configuration Checklist Description Format (XCCDF) versie 1.2.
  - Ondersteunt Open Vulnerability and Assessment Language (OVAL) versies tot versie 5.10.
  - Ondersteunt het genereren van Asset Reporting Format (ARF) 1.1-rapporten.
  - Ondersteunt Common Platform Enumeration (CPE) 2.3
  - Ondersteunt Common Vulnerabilities and Exposures (CVE)
  - Ondersteunt Common Configuration Enumeration (CCE) versie 5
  - Ondersteunt USGCB Internet Explorer 8, USGCB Windows 7 en USGCB Windows 7 Firewall.

- Bevat de wizard UI 1.2/1.1/1.0 SCAP en -OVAL inhoud voor conversie naar Configuratiebasislijnen importeert.


  - Staat de selectie van SCAP-Brongegevensstromen en XCCDF-maatstaven en -profielen voor conversie.

- Bevat de wizard UI resultaat van evaluatie van configuratie exporteren naar SCAP-indeling XML-rapport


  - Geeft het bronbestand, SCAP Datastream, XCCDF-Benchmark en XCCDF-profiel gebruikt voor het genereren van de basislijn.
  - Ondersteunt het genereren van het rapport Cyberscope Lightweight Asset samenvatting resultaten (LASR).

- Ondersteunt het genereren van SCAP-rapporten op basis van implementatie Configuratiebasislijn. Bevat een nieuw dashboard om de naleving door clients, evenals de compatibiliteit van de XCCDF-regel. Het dashboard ondersteunt weergeven via meer gedetailleerde rapporten, waarin u kunt zoeken en filteren.
- Verbetert de prestaties van de diverse typen die configuratie-Items geconverteerd van OVAL tests, zodat snellere evaluatie.

- Worden verschillende problemen opgelost die zijn gevonden in Windows 10 DISA v1r3 inhoud.

# <a name="scap-extensions-for-microsoft-system-center-configuration-manager-deployment-process"></a>Voor SCAP Extensions voor Microsoft System Center Configuration Manager-implementatieproces

Deze handleiding wordt beschreven hoe analyseren, beoordelen en te rapporteren over SCAP-naleving met behulp van de SCAP-extensies voor Microsoft System Center Configuration Manager. Hier&#39;s een korte samenvatting van de procedures u&#39;lle volgen:

- Bereid de vereiste infrastructuur om te profiteren van de uitbreidingen.
- Installeer en configureer SCAP Extensions voor Microsoft System Center Configuration Manager.
- Downloaden, installeren en configureren van de SCAP-Gegevensstroombestanden uit de [National Vulnerability Database](http://nvd.nist.gov) (NVD).
- Converteren en importeren van de SCAP-Gegevensstroombestanden rechtstreeks in basislijn instellingen met de naleving van System Center Configuration Manager met de Wizard importeren **of** via een CAB-bestand met de opdrachtregel Microsoft.Sces.ScapToDcm.exe hulpprogramma.
- Nalevingsresultaten exporteren naar SCAP-indeling met de Wizard exporteren of het opdrachtregelhulpprogramma Microsoft.Sces.DcmToScap.exe.

# <a name="terms"></a>Voorwaarden

**OVAL-ID:** Een id voor een specifieke OVAL definitie die aan de indeling voor de id van OVAL voldoet.

**Gegevensstroom van SCAP resultaat:** Een bundel van SCAP-onderdelen, samen met de toewijzingen van verwijzingen tussen SCAP-onderdelen die inhoud van de uitvoer (resultaat) bevatten.

**Gegevensstroom van SCAP bron:** Een bundel van SCAP-onderdelen, samen met de toewijzingen van verwijzingen tussen SCAP-onderdelen die invoer (bron) inhoud bevatten.

# <a name="prepare-the-prerequisite-infrastructure"></a>De vereiste infrastructuur voorbereiden

Zorg ervoor dat de volgende hardware- en softwarevereisten worden voldaan om te profiteren van de SCAP-extensies voor Microsoft System Center Configuration Manager.

## <a name="software-requirements"></a>Softwarevereisten

Als u wilt installeren, configureren en uitvoeren van de SCAP-extensies voor Microsoft System Center Configuration Manager, moet u een computer met de volgende software:

- Een [ondersteunde versie](/sccm/core/servers/manage/current-branch-versions-supported) van de System Center Configuration Manager-console voor huidige vertakking.
- Een besturingssysteem dat compatibel is met de System Center Configuration Manager-console. Zie voor een lijst met compatibele besturingssystemen, de [ondersteunde besturingssystemen voor System Center Configuration Manager-consoles](/sccm/core/plan-design/configs/supported-operating-systems-consoles) artikel.

Naast de computer waarop de SCAP-extensies wordt uitgevoerd, moet u ook de volgende items:

- Een vertakking van System Center Configuration Manager huidige infrastructuur. Zie voor meer informatie over de vereisten voor de implementatie van een Configuration Manager de [ondersteunde configuraties voor Configuration Manager](/sccm/core/plan-design/configs/supported-configurations) artikel.

De computers die u wilt beoordelen voor SCAP-naleving moeten de volgende software en configuraties:

- De compatibiliteit en instellingen beheren component ingeschakeld op de Configuration Manager-client.
- Windows PowerShell 2.0 of hoger.
- De Configuration Manager-PowerShell-uitvoeringsbeleid instellen op **Bypass**. Zie voor meer informatie de [PowerShell-uitvoeringsbeleid](/sccm/core/clients/deploy/about-client-settings#computer-agent) artikel.
- Een van de volgende besturingssystemen
  - Versie van Windows 7 of Sp1, 32-bits of 64-bits
  - Windows 10, 32-bits of 64-bits
  - Windows Server 2012 R2

## <a name="hardware-requirements"></a>Hardwarevereisten

De minimale systeemvereisten vindt u hier:

[Plannen voor hardwareconfiguraties voor Configuration Manager](/sccm/core/plan-design/configs/recommended-hardware)



## <a name="accessibility-features"></a>Toegankelijkheidsfuncties

De SCAP-extensies voor System Center Configuration Manager omvatten Windows-opdrachtregelprogramma's van de toegankelijkheidsfuncties profiteren kunnen en hulpprogramma's in Windows.

- Opdrachtregelparameters worden beschreven in deze handleiding voor Microsoft.Sces.ScapToDcm.exe en Microsoft.Sces.DcmToScap.exe.
- -help en -? Gebruik hulpprogramma naar het scherm beschikbaar voor schermlezers en andere ondersteunende technologie worden afgedrukt.
- Windows [toegankelijkheid](http://windows.microsoft.com/windows/help/accessibility)

SCAP Extensions maakt ook gebruik van functies in System Center Configuration Manager.  Configuration Manager bevat functies die het product beter toegankelijk voor mensen met beperkingen.

- [Toegankelijkheidsfuncties in System Center Configuration Manager](/sccm/core/understand/accessibility-features)

Voor algemene informatie over Microsoft-toegankelijkheidsproducten en -services, gaat u naar de [website Microsoft Accessibility](http://go.microsoft.com/fwlink/p/?LinkId=9212).

## <a name="next-step"></a>Volgende stap
> [!div class="nextstepaction"]
> [Installeer en configureer SCAP-extensies](/sccm/compliance/plan-design/scap/install-configure-scap)
