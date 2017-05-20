---
title: "Installatiekopieën van besturingssystemen - Configuration Manager aanpassen | Microsoft-documenten"
description: Vastleggen en build takenreeksen, handmatige configuratie of een combinatie van beide gebruiken voor het aanpassen van een installatiekopie van een besturingssysteem.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95033a9b-ff13-4b70-b1de-bcb25bcb6024
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: 485cb3ca4988f983c1ec71b6c8daf136571bf0ea
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="customize-operating-system-images-with-system-center-configuration-manager"></a>Installatiekopieën van een besturingssysteem aanpassen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Installatiekopieën van besturingssystemen in System Center Configuration Manager zijn WIM-bestanden en een gecomprimeerde verzameling referentiebestanden en -mappen die vereist zijn om correct te installeren en configureren van een besturingssysteem op een computer vertegenwoordigen. Een installatiekopie van een besturingssysteem wordt samengesteld en vastgelegd vanaf een referentiecomputer die u configureert met alle vereiste besturingssysteembestanden, ondersteuningsbestanden, software-updates, hulpprogramma's en andere softwaretoepassingen. U bepaalt zelf de mate waarin u de referentiecomputer handmatig configureert. U kunt de configuratie van de referentiecomputer volledig automatiseren door een takenreeks samen te stellen en vast te leggen, u kunt een aantal aspecten van de referentiecomputer handmatig configureren en vervolgens de rest automatiseren met behulp takenreeksen of u kunt de referentiecomputer handmatig configureren zonder gebruik te maken van takenreeksen. Gebruik de volgende secties voor het aanpassen van een besturingssysteem.

##  <a name="BKMK_PrepareReferenceComputer"></a>De referentiecomputer voorbereiden  
 Voordat u een installatiekopie van besturingssysteem van een referentiecomputer vastlegt, moet u rekening houden met verschillende aspecten.  

###  <a name="BKMK_RefComputerDecide"></a>Kiezen tussen een automatische of handmatige configuratie  
 Verderop vindt u informatie over de voordelen en nadelen van een automatische en handmatige configuratie van de referentiecomputer.  

#### <a name="automated-configuration"></a>Automatische configuratie  
 **Voordelen**  

-   De configuratie kan volledig zonder toezicht gebeuren, wat de noodzaak van de aanwezigheid van een beheerder of gebruiker elimineert.  

-   U kunt de takenreeks opnieuw gebruiken om de configuratie van bijkomende referentiecomputers te herhalen met een hoger vertrouwensniveau.  

-   U kunt de takenreeks wijzigen om de verschillen in referentiecomputers op te vangen zonder dat de volledige takenreeks opnieuw moet gecreëerd worden.  

 **Nadelen**  

-   De initiële actie om een takenreeks te bouwen, kan een lange tijd vergen voor de creatie en het testen.  

-   Indien de vereisten voor referentiecomputers significant veranderen, kan het lange tijd duren om de takenreeks opnieuw te bouwen en opnieuw te testen.  

#### <a name="manual-configuration"></a>Handmatige configuratie  
 **Voordelen**  

-   U moet de takenreeks niet creëren of de tijd nemen om de takenreeks te testen en er de fouten van op te sporen en te herstellen.  

-   U kunt rechtstreeks vanaf cd's installeren zonder al de softwarepakketten (inclusief Windows zelf) plaatsen in een Configuration Manager-pakket.  

 **Nadelen**  

-   De nauwkeurigheid van de computerconfiguratie hangt af van de beheerder of de gebruiker die de computer configureert.  

-   U moet nog altijd verifiëren dat de referentiecomputer juist geconfigureerd is.  

-   U kunt de configuratiemethode niet opnieuw gebruiken.  

-   Vereist een persoon die actief betrokken wordt tijdens het proces.  

###  <a name="BKMK_RefComputerConsiderations"></a>Overwegingen voor de referentiecomputer  
 Verderop staat de lijst van basiselementen waarmee u rekening moet houden bij de configuratie van een referentiecomputer.  

-   **Te implementeren besturingssysteem**  

     De referentiecomputer moet geïnstalleerd worden met het besturingssysteem dat u van plan bent te gebruiken op uw doelcomputers. Zie voor meer informatie over de besturingssystemen die u kunt implementeren, [vereisten voor de infrastructuur voor implementatie van besturingssysteem](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

-   **Juist servicepack**  

     De referentiecomputer moet geïnstalleerd worden met het besturingssysteem dat u van plan bent te gebruiken op uw doelcomputers.  

-   **Juiste software-updates**  

     Installeer alle softwaretoepassingen die u wenst op te nemen in de installatiekopie van het besturingssysteem die u vastlegt van de referentiecomputer. U kunt ook softwaretoepassingen installeren als u de geregistreerde installatiekopie van het besturingssysteem op de doelcomputers implementeert.  

-   **Lidmaatschap van een werkgroep**  

     De referentiecomputer moet geconfigureerd zijn als een lid van een werkgroep.  

-   **Sysprep**  

     Het hulpprogramma voor systeemvoorbereiding (Sysprep) is een technologie die u kunt gebruiken met andere implementatiehulpprogramma's om Windows besturingssystemen te installeren op nieuwe hardware. Sysprep bereidt een computer voor op het nemen van een installatiekopie op harde schijf of voor levering aan een gebruiker door de computer te configureren zodat een nieuwe beveiligings-ID (SID) wordt gecreëerd bij het opnieuw opstarten van de computer. Bovendien ruimt Sysprep gebruikers- en computerspecifieke instellingen en gegevens op die niet moeten worden gekopieerd naar een doelcomputer.  

     U kunt handmatig de systeemvoorbereiding (Sysprep) van de referentiecomputer uitvoeren door de volgende opdracht uit te voeren:  

     `Sysprep /quiet /generalize /reboot`  

     De optie /generalize geeft Sysprep de opdracht systeemspecifieke gegevens uit de Windows-installatie te verwijderen. Systeemspecifieke informatie bevat gebeurtenislogboeken, unieke beveiligings-id (SID's) en andere unieke informatie. Nadat de unieke systeeminformatie is verwijderd, wordt de computer opnieuw opgestart.  

     U kunt Sysprep automatiseren door gebruik te maken van de [Windows voorbereiden voor vastleggen](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) takenreeks of van registratiemedia.  

    > [!IMPORTANT]  
    >  De [Windows voorbereiden voor vastleggen](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) takenreeks tracht het lokale beheerderswachtwoord op de referentiecomputer opnieuw in te stellen op een lege waarde voordat Sysprep draait. Indien het lokale beveiligingsbeleid **Het wachtwoord moet aan de complexiteitsvereisten voldoen** ingeschakeld is, slaagt deze takenreeksstap er niet in om het beheerderswachtwoord opnieuw in te stellen. Schakel in dit geval het beleid uit indien u de takenreeks uitvoert.  

     Zie [Technische naslaginformatie over systeemvoorbereiding (Sysprep)](http://go.microsoft.com/fwlink/?LinkId=280286) voor meer informatie over Sysprep.  

-   **Juiste hulpprogramma's en scripts die zijn vereist om in te perken installatiescenario 's**  

     Juiste hulpprogramma's en scripts die zijn vereist om installatie-scenario's in te perken  

-   **Juiste bureaubladaanpassing, zoals achtergrond, huisstijl en standaardgebruikersprofiel**  

     U kunt de referentiecomputer configureren met de aanpassingskenmerken voor het bureaublad die u wenst over te nemen wanneer u de installatiekopie van het besturingssysteem van de referentiecomputer vastlegt. Bureaubladkenmerken omvatten achtergrond, huisstijl van de organisatie en een standaardgebruikersprofiel.  

##  <a name="BKMK_ManuallyBuildReference"></a>Handmatig een referentiecomputer maken  
 Gebruik de volgende procedure om handmatig een referentiecomputer te bouwen.  

> [!NOTE]  
>  Als u de referentiecomputer handmatig bouwt, kunt u de installatiekopie van het besturingssysteem vastleggen met vastlegmedia. Zie voor meer informatie [vastlegmedia maken](../deploy-use/create-capture-media.md).  

#### <a name="to-manually-build-the-reference-computer"></a>De referentiecomputer handmatig bouwen  

1.  Identificeer de te gebruiken computer als de referentiecomputer.  

2.  Configureer de referentiecomputer met het juiste besturingssysteem en andere software die nodig is om de installatiekopie van het besturingssysteem te maken dat u wenst te implementeren.  

    > [!WARNING]  
    >  Installeer minimaal het juiste besturingssysteem en servicepack, de juiste stuurprogramma's voor ondersteuning en de vereiste software-updates.  

3.  Configureer de referentiecomputer als een lid van een werkgroep.  

4.  Zet het beheerderwachtwoord terug op de referentiecomputer zodat de waarde van het wachtwoord leeg is.  

5.  Voer Sysprep uit met de opdracht: **sysprep /quiet /generalize /reboot**. De optie /generalize geeft Sysprep de opdracht systeemspecifieke gegevens uit de Windows-installatie te verwijderen. Systeemspecifieke informatie bevat gebeurtenislogboeken, unieke beveiligings-id (SID's) en andere unieke informatie. Nadat de unieke systeeminformatie is verwijderd, wordt de computer opnieuw opgestart.  

 Zodra de referentiecomputer klaar is, gebruikt u een takenreeks om de installatiekopie van het besturingssysteem van de referentiecomputer vast te leggen.  Zie [Een installatiekopie van een besturingssysteem vastleggen vanaf een bestaande referentiecomputer](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_CaptureExistingRefComputer) voor gedetailleerde stappen.  

##  <a name="BKMK_UseTSToBuildReference"></a>Een takenreeks gebruiken een referentiecomputer maken  
 U kunt het proces voor het maken van een referentiecomputer automatiseren door een takenreeks te gebruiken waarmee u het besturingsysteem, de stuurprogramma's, de toepassingen, enzovoort implementeert.  Voer de volgende stappen uit om de referentiecomputer te bouwen en vervolgens de installatiekopie van het besturingssysteem vanaf de referentiecomputer vast te leggen.  

-   Gebruik een takenreeks om de installatiekopie van het referentiebesturingssysteem te maken en vast te leggen.  Zie [Een referentiecomputer bouwen en vastleggen met behulp van een takenreeks](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_BuildCaptureTS) voor gedetailleerde stappen.  

