---
title: Upgradepakketten besturingssysteem beheren | Microsoft-documenten
description: Informatie over het beheren van upgradepakketten besturingssysteem in System Center Configuration Manager.
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f44505c977b511223a083a960f871371c0ff133
ms.openlocfilehash: 5fef04f26b12bced073332fd1f7b4e7c7bd7d398
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-operating-system-upgrade-packages-with-system-center-configuration-manager"></a>Upgradepakketten van het besturingssysteem beheren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een upgrade in System Center Configuration Manager-pakket bevat bronbestanden van de installatie van Windows die worden gebruikt voor het upgraden van een bestaand besturingssysteem op een computer. Gebruik de volgende secties upgradepakketten besturingssysteem in Configuration Manager beheren.

##  <a name="BKMK_AddOSUpgradePkgs"></a> Upgradepakketten voor het besturingssysteem toevoegen aan Configuration Manager  
 Voordat u een upgradepakket besturingssysteem gebruiken kunt, moet u het pakket toevoegen aan een Configuration Manager-site. Gebruik de volgende procedure om een upgradepakket voor het besturingssysteem toe te voegen aan een site.  

#### <a name="to-add-an-operating-system-upgrade-package"></a>Een upgradepakketten voor het besturingssysteem toevoegen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** het knooppunt **Besturingssystemen**uit en klik vervolgens op **Upgradepakketten voor besturingssysteem**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Upgradepakket besturingssysteem toevoegen** om de wizard Upgradepakket besturingssysteem toevoegen te starten.  

4.  Geef op de pagina **Gegevensbron** het netwerkpad op naar de installatiebronbestanden van het upgradepakket voor het besturingssysteem. Geef bijvoorbeeld de UNC **\\\server\pad** op voor de locatie waar de installatiebronbestanden zich bevinden.  

    > [!NOTE]  
    >  De installatiebronbestanden bevatten Setup.exe en andere bestanden en mappen om het besturingssysteem te installeren.  

    > [!IMPORTANT]  
    >  Beperk de toegang tot de installatiebronbestanden om ongewenste manipulatie te voorkomen.  

5.  Geef op de pagina **Algemeen** de volgende informatie op en klik op **Volgende**. Deze informatie is nuttig om een installatieprogramma te kunnen identificeren wanneer u meerdere installatieprogramma's voor besturingssystemen hebt.  

    -   **Naam**: Geef de naam van het installatieprogramma van het besturingssysteem.  

    -   **Versie**: Geef de versie van het installatieprogramma van het besturingssysteem.  

    -   **Opmerking**: Geef een korte beschrijving van het installatieprogramma van het besturingssysteem.  

6.  Voltooi de wizard.  

 U kunt het installatieprogramma voor het besturingssysteem nu distribueren naar de distributiepunten die worden gebruikt door de takenreeksen van uw implementatie.  

##  <a name="BKMK_DistributeBootImages"></a> Installatiekopieën van het besturingssysteem naar een distributiepunt distribueren  
 Installatiekopieën van het besturingssysteem worden op dezelfde manier naar distributiepunten gedistribueerd als andere inhoud. In de meeste gevallen moet u het besturingssysteem naar ten minste één distributiepunt distribueren voordat u het besturingssysteem implementeert. Zie [Inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content) voor stappen om een installatiekopie van een besturingssysteem te distribueren.  

##  <a name="BKMK_OSUpgradePkgApplyUpdates"></a> Software-updates toepassen op een updatepakket van een besturingssysteem  
 Beginnend in Configuration Manager versie 1602, kunt u nieuwe software-updates toepassen op de installatiekopie van het besturingssysteem in uw upgradepakket besturingssysteem. Voordat u kunt software-updates toepassen op een upgradepakket hebt u hebben uw software-update-infrastructuur aanwezig, is gesynchroniseerde software-updates en de software-updates gedownload naar de Inhoudsbibliotheek op de siteserver. Zie voor meer informatie [software-updates implementeren](../../sum/deploy-use/deploy-software-updates.md).  

 U kunt toepasselijke software-updates volgens een opgegeven schema toepassen op een updatepakket. Het schema dat u opgeeft, Configuration Manager geldt de software-updates die u selecteert voor het upgradepakket voor besturingssysteem en eventueel distribueert vervolgens de bijgewerkte upgradepakket naar distributiepunten. Informatie over het updatepakket van het besturingssysteem wordt opgeslagen in de sitedatabase, inclusief de software-updates die tijdens het importeren zijn toegepast. Software-updates die op het updatepakket zijn toegepast sinds de kopie voor het eerst werd toegevoegd, worden ook opgeslagen in de sitedatabase. Wanneer u de wizard start om software-updates toe te passen op het updatepakket van het besturingssysteem, wordt er een lijst opgehaald met toepasselijke software-updates die nog niet zijn toegepast op het updatepakket. U kunt dan een selectie maken uit deze lijst. Configuration Manager opgehaald van de software-updates uit de Inhoudsbibliotheek op de siteserver en de software-updates geldt voor het upgradepakket van het besturingssysteem.  

 Gebruik de volgende procedure om software-updates toe te passen op een updatepakket van een besturingssysteem.  

#### <a name="to-apply-software-updates-to-an-operating-system-upgrade-package"></a>Software-updates toepassen op een updatepakket van een besturingssysteem  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** het knooppunt **Besturingssystemen**uit en klik vervolgens op **Upgradepakketten voor besturingssysteem**.  

3.  Selecteer het updatepakket waarop u software-updates wilt toepassen.  

4.  Klik op het tabblad **Start** in de groep **Updatepakket van het besturingssysteem** op **Updates plannen** om de wizard te starten.  

5.  Selecteer op de pagina **Updates kiezen** de software-updates die moeten worden toegepast op de installatiekopie van het besturingssysteem en klik vervolgens op **Volgende**.  

6.  Geef, op de pagina **Schema instellen** , de volgende instellingen op, en klik vervolgens op **Volgende**.  

    1.  **Planning**: Geef het schema voor wanneer de software-updates worden toegepast op de installatiekopie van het besturingssysteem.  

    2.  **Doorgaan bij fout**:  Selecteer deze optie om door te gaan naar het software-updates toepassen op de installatiekopie, zelfs wanneer er een fout is opgetreden.  

    3.  **De installatiekopie distribueren naar distributiepunten**: Selecteer deze optie om de installatiekopie van het besturingssysteem op distributiepunten werken nadat de software-updates zijn toegepast.  

7.  Verifieer de informatie op de pagina **Samenvatting** en klik vervolgens op **Volgende**.  

8.  Verifieer op de pagina **Voltooiing** dat de software-updates met succes zijn toegepast op de installatiekopie van het besturingssysteem.  

