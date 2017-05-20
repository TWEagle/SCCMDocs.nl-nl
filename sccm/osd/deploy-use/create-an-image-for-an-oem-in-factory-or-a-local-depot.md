---
title: Een installatiekopie maken voor een OEM in de fabriek of een lokale depot | Microsoft-documenten
description: Implementaties met voorbereide media gebruiken voor het netwerkverkeer verminderen terwijl u een besturingssysteem implementeren op een computer die nog niet volledig is ingericht.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7d3df90-062d-4d57-9e9d-e137d3e7cd7f
caps.latest.revision: 8
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 07aba04fb1b845e389a5f75b115d536136c1569c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-an-image-for-an-oem-in-factory-or-a-local-depot-with-system-center-configuration-manager"></a>Een installatiekopie voor een OEM in de fabriek of een lokaal depot maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Implementaties met voorbereide media in System Center Configuration Manager kunnen u een besturingssysteem implementeren op een computer die nog niet volledig is ingericht. De voorbereide media staat een Windows Imaging Format (WIM)-bestand dat kan worden geïnstalleerd op een bare-metal computer door de fabrikant (OEM) of op een enterprise-voorbereidingscentrum dat niet is verbonden met de Configuration Manager-omgeving. Later in de Configuration Manager-omgeving, de computer wordt gestart met behulp van de door de media verstrekte opstartinstallatiekopie een hash-controle uitgevoerd op de voorbereide media om ervoor te zorgen geldig is en vervolgens de computer verbinding maakt met het sitebeheerpunt voor de beschikbare takenreeksen die het downloadproces voltooien.


Deze implementatiemethode kan het netwerkverkeer verminderen omdat de opstartinstallatiekopie en de installatiekopie van het besturingssysteem zich al op de doelcomputer bevinden. U kunt toepassingen, pakketten en stuurprogrammapakketten opgeven die in de voorbereide media moeten worden opgenomen. Nadat het besturingssysteem is geïnstalleerd op de computer, wordt de lokale takenreekscache eerst gecontroleerd op toepassingen, pakketten en stuurprogrammapakketten, en als de inhoud niet kan worden gevonden of is gewijzigd, wordt de inhoud gedownload vanaf een distributiepunt dat is geconfigureerd in de voorbereide media, en vervolgens geïnstalleerd.  

 U kunt vooraf geplaatste media gebruiken in de volgende implementatiescenario's van besturingssysteem:  

-   [Een nieuwe versie van Windows installeren op een nieuwe computer (bare metal)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Vervangen van een bestaande computer en instellingen overzetten](replace-an-existing-computer-and-transfer-settings.md)  

 Voer de stappen in een van de implementatiescenario’s voor besturingssystemen en gebruik de volgende secties om de voorbereide media voor te bereiden en te maken.  

## <a name="configure-deployment-settings"></a>Implementatie-instellingen configureren  
 Als u het implementatieproces voor een besturingssysteem wilt starten vanaf vooraf geplaatste media, moet u de implementatie configureren om het besturingssysteem beschikbaar te stellen voor media. U kunt dit configureren op de pagina **Implementatie-instellingen** van de wizard Software implementeren of op het tabblad **Implementatie-instellingen** in de eigenschappen voor de implementatie.  Configureer een van de volgende waarden voor de instelling **Toegankelijk maken voor de volgende** :  

-   **Configuration Manager-clients, media en PXE**  

-   **Alleen media en PXE**  

-   **Alleen media en PXE (verborgen)**  

## <a name="create-the-prestaged-media"></a>Voorbereide media maken  
 Maak de voorbereide media die naar de OEM of uw lokale depot moet worden verzonden. Zie [Voorbereide media maken met System Center Configuration Manager](create-prestaged-media.md) voor meer informatie.  

## <a name="send-the-prestaged-media-file-to-the-oem-or-local-depot"></a>Het voorbereide mediabestand naar de OEM of het lokale depot verzenden  
 Verzend de media naar de OEM of uw lokale depot om de computers voor te bereiden. Het voorbereide mediabestand wordt toegepast op een geformatteerde vaste schijf op de computer.  

## <a name="start-the-computer-to-install-the-operating-system"></a>Start de computer om het besturingssysteem te installeren  
 Het voorbereide mediabestand wordt toegepast op alle computers. Zodra de computer voor het eerst wordt gestart, start het installatieproces van het besturingssysteem.  

