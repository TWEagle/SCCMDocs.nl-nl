---
title: Upgrade van Windows voor de nieuwste versie | Microsoft-documenten
description: Informatie over het upgraden van een besturingssysteem van Windows 7 of hoger en Windows 10 met Configuration Manager.
ms.custom: na
ms.date: 02/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 288a4c649f371d9701fe7249449356aa222bf372
ms.openlocfilehash: 35f04e237efffbdb12893f658950a99dc0b98b85
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>Windows upgraden naar de nieuwste versie met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp voorziet de stappen in System Center Configuration Manager bijwerken van een besturingssysteem op een computer van Windows 7 of hoger en Windows 10. U kunt kiezen uit verschillende implementatiemethoden, zoals zelfstandige media of Software Center. Scenario voor de in-place upgrade van Windows 10:  

-   voert een upgrade van het besturingssysteem uit op computers met Windows 7, Windows 8 of Windows 8.1. U kunt ook build-naar-build-upgrades van Windows 10 uitvoeren. U kunt bijvoorbeeld Windows 10 RTM upgraden naar Windows 10, versie 1511.  

-   Toepassingen, instellingen en gebruikersgegevens op de computer blijven behouden.  

-   Heeft geen externe afhankelijkheden, zoals de Windows ADK.  

-   Gaat doorgaans sneller en is toleranter dan traditionele implementaties van besturingssystemen.  

 Gebruik de volgende secties om besturingssystemen via het netwerk te implementeren met behulp van een takenreeks.  

##  <a name="BKMK_Plan"></a> Plan  

-   **De beperkingen bekijken voor de takenreeks om een besturingssysteem te upgraden**  

     Bekijk de volgende vereisten en beperkingen voor de takenreeks voor het upgraden van een besturingssysteem om ervoor te zorgen dat het voldoet aan wat u nodig hebt:  

    -   U wordt aangeraden alleen takenreeksstappen toe te voegen die te maken hebben met de hoofdtaken (het implementeren van besturingssystemen en computers configureren nadat de kopie is geïnstalleerd). Dit omvat stappen waarbij pakketten, toepassingen of updates worden geïnstalleerd en stappen waarbij opdrachtregels worden uitgevoerd, PowerShell wordt uitgevoerd of dynamische variabelen worden ingesteld.  

    -   Bekijk welke stuurprogramma's en toepassingen zijn geïnstalleerd op computers om te controleren of ze compatibel zijn met Windows 10 voordat u de upgradetakenreeks implementeert.  

    -   De volgende taken zijn niet compatibel met de in-place upgrade. U moet hier traditionele besturingssysteemimplementatie voor gebruiken:  

        -   Het domeinlidmaatschap van de computer wijzigen of de lokale beheerders bijwerken.  

        -   Een basiswijziging implementeren op de computer, zoals de schijf partitioneren, overstappen van x86 naar x64, UEFI implementeren of de basisbesturingssysteemtaal wijzigen.  

        -   U hebt aangepaste vereisten, waaronder het gebruik van een aangepaste basisinstallatiekopie met schijfversleuteling van een 3<sup>de</sup> partij, of er worden offline WinPE-bewerkingen vereist.  

-   **Infrastructuurvereisten plannen en implementeren**  

     De enige vereisten voor het upgradescenario zijn dat er een distributiepunt beschikbaar is voor het upgradepakket van het besturingssysteem en andere pakketten die u in de takenreeks opneemt. Zie voor meer informatie [installeren of te wijzigen van een distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

##  <a name="BKMK_Configure"></a> Configurerenren  

1.  **Het upgradepakket voor het besturingssysteem voorbereiden**  

     Het Windows 10-upgradepakket bevat de bronbestanden die nodig zijn om het besturingssysteem op de doelcomputer te upgraden. Het upgradepakket moet beschikken over dezelfde versie, architectuur en taal als de clients die u gaat upgraden.  Zie voor meer informatie [upgradepakketten besturingssysteem beheren](../get-started/manage-operating-system-upgrade-packages.md).  

2.  **Een takenreeks maken om het besturingssysteem bij te werken**  

     Gebruik de stappen in [maken van een takenreeks om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md) voor het automatiseren van de upgrade van het besturingssysteem.  

    > [BELANGRIJKE] Als u zelfstandige media, moet u een opstartinstallatiekopie opnemen in de takenreeks om te worden weergegeven in de Wizard Takenreeksmedia.


    > [!NOTE]  
    >  Gewoonlijk gebruikt u de stappen in [maken van een takenreeks om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md) een takenreeks om een upgrade van een besturingssysteem naar Windows 10 te maken. De takenreeks bevat het besturingssysteem upgraden stap, evenals de extra aanbevolen stappen en groepen om af te handelen end-to-end-upgradeproces. U kunt echter een aangepaste takenreeks maken en toevoegen de [besturingssysteem bijwerken](../understand/task-sequence-steps.md#BKMK_UpgradeOS) takenreeksstap werk het besturingssysteem. Dit is de enige stap die is vereist om het besturingssysteem te upgraden naar Windows 10. Als u deze methode, ook toevoegen de [Computer opnieuw opstarten](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer) stap na de stap besturingssysteem bijwerken om de upgrade te voltooien. Zorg ervoor dat u de **het momenteel geïnstalleerde standaardbesturingssysteem** instelling van de computer opnieuw opstarten in het geïnstalleerde besturingssysteem en niet Windows PE.  

##  <a name="BKMK_Deploy"></a> Implementeren  

-   Gebruik een van de volgende implementatiemethoden om het besturingssysteem te implementeren:  

    -   [Software Center gebruiken om Windows te implementeren via het netwerk](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [Zelfstandige media gebruiken om Windows te implementeren zonder het gebruik van het netwerk](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **De takenreeksimplementatie controleren**  

     Zie voor het controleren van de implementatie van takenreeks om het besturingssysteem te upgraden, [bewaken van implementaties van besturingssystemen](monitor-operating-system-deployments.md).  

