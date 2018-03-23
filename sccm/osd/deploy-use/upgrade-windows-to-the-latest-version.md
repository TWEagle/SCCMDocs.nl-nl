---
title: Upgraden naar Windows 10
titleSuffix: Configuration Manager
description: Informatie over het upgraden van een besturingssysteem van Windows 7 of hoger naar Windows 10 met Configuration Manager.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 976a65ad27fe615a997ef795e3acf7a175f363af
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>Windows upgraden naar de nieuwste versie met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel bevat de stappen in Configuration Manager om de upgrade van het besturingssysteem op een computer. U kunt kiezen uit verschillende implementatiemethoden, zoals zelfstandige media of Software Center. Het in-place upgradescenario heeft de volgende functies:  

-   Upgrade van het besturingssysteem op computers die momenteel worden uitgevoerd:
    - Windows 7, Windows 8 of Windows 8.1. U kunt ook build-naar-build-upgrades van Windows 10 uitvoeren. U kunt bijvoorbeeld Windows 10 versie 1607 upgraden naar Windows 10 versie 1709.  
    
    - Windows Server 2012. U kunt ook build-naar-build-upgrades van Windows Server 2016 doen. Zie voor meer informatie over ondersteunde upgradepaden [ondersteunde upgradepaden](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016).    

-   Toepassingen, instellingen en gebruikersgegevens op de computer blijven behouden.  

-   Heeft geen externe afhankelijkheden, zoals de Windows ADK.  

-   Gaat sneller en is toleranter dan traditionele implementaties van het besturingssysteem.  


> [!Note]  
> Vanaf versie 1802, de takenreeks Windows 10 in-place upgrade ondersteunt de implementatie op internet gebaseerde clients beheerd via de [management cloudgateway](/sccm/core/clients/manage/plan-cloud-management-gateway). Deze mogelijkheid kunnen externe gebruikers gemakkelijker upgraden naar Windows 10 zonder verbinding maken met het intranet. Zie voor meer informatie [Windows 10 implementeren in-place upgrade via CMG](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#deploy-windows-10-in-place-upgrade-via-cmg). <!-- 1357149 -->



##  <a name="BKMK_Plan"></a> Plan  

### <a name="task-sequence-requirements-and-limitations"></a>Taak reeks vereisten en beperkingen

Lees de volgende vereisten en beperkingen voor de takenreeks een besturingssysteem bijwerken om ervoor te zorgen dat uw behoeften voldoet:  

  -   Alleen takenreeksstappen die gerelateerd zijn aan de hoofdtaken van de upgrade van het besturingssysteem toevoegen. Deze stappen omvatten voornamelijk pakketten, toepassingen of updates installeren. Gebruik ook stappen waarbij opdrachtregels, PowerShell, worden uitgevoerd of dynamische variabelen worden ingesteld.  

  -   Bekijk welke stuurprogramma's en toepassingen zijn geïnstalleerd op computers om te controleren of ze compatibel zijn met Windows 10 voordat u de upgradetakenreeks implementeert.  

  -   De volgende taken zijn niet compatibel met de in-place upgrade. Ze willen dat u traditionele OS-implementaties gebruikt:  

     -   Het domeinlidmaatschap van de computer wijzigen of bijwerken van de lokale groep Administrators.  

     -   Implementatie van een fundamentele wijziging op de computer, zoals: 
         - Het wijzigen van de partities op schijf
         - Het wijzigen van de systeemarchitectuur van x86 op x 64
         - UEFI implementeren. (Zie voor meer informatie over een mogelijke optie [BIOS converteren naar UEFI tijdens een upgrade ter plekke](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).)
         - De standaardtaal van het besturingssysteem wijzigen  

     -   U hebt aangepaste vereisten, inclusief het gebruik van een aangepaste basisinstallatiekopie met schijfversleuteling van derden of offline WinPE-bewerkingen vereist.  

### <a name="infrastructure-requirements"></a>Vereisten voor de infrastructuur  

De enige vereiste voor het upgradescenario is om een beschikbaar distributiepunt. Distribueer de OS-upgradepakket en de andere pakketten die u in de takenreeks opneemt. Zie voor meer informatie [installeren of wijzigen van een distributiepunt](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).



##  <a name="BKMK_Configure"></a> Configurerenren  

### <a name="prepare-the-os-upgrade-package"></a>Het upgradepakket voor besturingssysteem voorbereiden  

  Het Windows 10-upgradepakket bevat de bronbestanden voor het bijwerken van het besturingssysteem op de doelcomputer. Het upgradepakket moet dezelfde versie, architectuur en taal als de clients die u een upgrade uitvoert. Zie voor meer informatie [upgradepakketten voor besturingssysteem beheren](../get-started/manage-operating-system-upgrade-packages.md).  


### <a name="create-a-task-sequence-to-upgrade-the-os"></a>Een takenreeks om een upgrade van het besturingssysteem te maken  

  Gebruik de stappen in [een takenreeks maken om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md) voor het automatiseren van de upgrade van het besturingssysteem.  

   > [!NOTE]  
   > Normaal gebruikt u de stappen in [een takenreeks maken om een besturingssysteem te upgraden](create-a-task-sequence-to-upgrade-an-operating-system.md) voor het maken van een takenreeks om een besturingssysteem te upgraden naar Windows 10. De takenreeks bevat de stap besturingssysteem bijwerken, evenals aanvullende aanbevolen stappen en groepen voor de end-to-end upgradeproces. U kunt echter een aangepaste takenreeks maken en toevoegen de [besturingssysteem bijwerken](../understand/task-sequence-steps.md#BKMK_UpgradeOS) takenreeksstap bijwerken van het besturingssysteem. Deze stap is het enige vereist voor het besturingssysteem upgraden naar Windows 10. Als u deze methode kiest, voegt u ook de [Computer opnieuw opstarten](../understand/task-sequence-steps.md#BKMK_RestartComputer) stap na de stap besturingssysteem bijwerken om de upgrade te voltooien. Zorg ervoor dat u de **het momenteel geïnstalleerde standaardbesturingssysteem** instelling van de computer opnieuw opstarten in het geïnstalleerde besturingssysteem en niet met Windows PE.  



##  <a name="BKMK_Deploy"></a> Implementeren  

Gebruik een van de volgende implementatiemethoden gebruiken voor het implementeren van het besturingssysteem:  

  -   [Windows met Software Center via het netwerk implementeren](use-software-center-to-deploy-windows-over-the-network.md)  

  -   [Zelfstandige media gebruiken om Windows te implementeren zonder gebruik van het netwerk](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

      > [!IMPORTANT]  
      > Wanneer u zelfstandige media gebruikt, moet u een opstartinstallatiekopie opnemen in de takenreeks als deze beschikbaar zijn in de Wizard Takenreeksmedia.




## <a name="monitor"></a>Monitor  

Als u wilt de takenreeksimplementatie om een upgrade van het besturingssysteem te bewaken, Zie [implementaties van besturingssystemen bewaken](monitor-operating-system-deployments.md).  
