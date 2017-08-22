---
title: Windows upgraden naar de nieuwste versie | Microsoft Docs
description: Informatie over het upgraden van een besturingssysteem van Windows 7 of hoger naar Windows 10 met Configuration Manager.
ms.custom: na
ms.date: 02/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
caps.latest.revision: "13"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 026d61113a918e43ac4395ef092b1931f33f16d3
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>Windows upgraden naar de nieuwste versie met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat de stappen in System Center Configuration Manager om een besturingssysteem op een computer bijwerken van Windows 7 of hoger naar Windows 10 of Windows Server 2012 naar Windows Server 2016 op een doelcomputer. U kunt kiezen uit verschillende implementatiemethoden, zoals zelfstandige media of Software Center. Het in-place upgradescenario:  

-   Upgrade van het besturingssysteem op computers die momenteel worden uitgevoerd:
    - Windows 7, Windows 8 of Windows 8.1. U kunt ook build-naar-build-upgrades van Windows 10 uitvoeren. U kunt bijvoorbeeld Windows 10 RTM upgraden naar Windows 10, versie 1511.  
    - WindowsServer 2012. U kunt ook build-naar-build-upgrades van Windows Server 2016 doen. Zie voor meer informatie over ondersteunde upgradepaden [ondersteunde upgradepaden](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016).    

-   Toepassingen, instellingen en gebruikersgegevens op de computer blijven behouden.  

-   Heeft geen externe afhankelijkheden, zoals de Windows ADK.  

-   Gaat sneller en is toleranter dan traditionele besturingssysteemimplementaties.  

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

-   **Plannen en implementeren van de vereisten voor de infrastructuur**  

     De enige vereisten voor het upgradescenario zijn dat u hebt een distributiepunt beschikbaar is voor het upgradepakket voor besturingssysteem en andere pakketten die u in de takenreeks opneemt. Zie voor meer informatie [installeren of wijzigen van een distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

##  <a name="BKMK_Configure"></a> Configurerenren  

1.  **Het upgradepakket voor het besturingssysteem voorbereiden**  

     Het Windows 10-upgradepakket bevat de bronbestanden die nodig zijn om het besturingssysteem op de doelcomputer te upgraden. Het upgradepakket moet dezelfde versie, architectuur en taal als de clients die u een upgrade uitvoert.  Zie voor meer informatie [upgradepakketten voor besturingssysteem beheren](../get-started/manage-operating-system-upgrade-packages.md).  

2.  **Een takenreeks maken om het besturingssysteem bij te werken**  

     Gebruik de stappen in [een takenreeks maken om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md) voor het automatiseren van de upgrade van het besturingssysteem.  

    > [!IMPORTANT]
    > Wanneer u zelfstandige media gebruikt, moet u een opstartinstallatiekopie opnemen in de takenreeks als deze beschikbaar zijn in de Wizard Takenreeksmedia.

    > [!NOTE]  
    > Normaal gebruikt u de stappen in [een takenreeks maken om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md) voor het maken van een takenreeks een besturingssysteem te upgraden naar Windows 10. De takenreeks bevat de stap besturingssysteem bijwerken, evenals aanvullende aanbevolen stappen en groepen voor de end-to-end upgradeproces. U kunt echter een aangepaste takenreeks maken en toevoegen de [besturingssysteem bijwerken](../understand/task-sequence-steps.md#BKMK_UpgradeOS) takenreeksstap om het besturingssysteem te upgraden. Dit is de enige stap die is vereist om het besturingssysteem te upgraden naar Windows 10. Als u deze methode kiest, voegt u ook de [Computer opnieuw opstarten](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer) stap na de stap besturingssysteem bijwerken om de upgrade te voltooien. Zorg ervoor dat u de **het momenteel geïnstalleerde standaardbesturingssysteem** instelling van de computer opnieuw opstarten in het geïnstalleerde besturingssysteem en niet met Windows PE.  

##  <a name="BKMK_Deploy"></a> Implementeren  

-   Gebruik een van de volgende implementatiemethoden om het besturingssysteem te implementeren:  

    -   [Windows met Software Center via het netwerk implementeren](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [Zelfstandige media gebruiken om Windows te implementeren zonder gebruik van het netwerk](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **De takenreeksimplementatie controleren**  

     Zie voor het bewaken van de takenreeksimplementatie om het besturingssysteem te upgraden, [implementaties van besturingssystemen bewaken](monitor-operating-system-deployments.md).  
