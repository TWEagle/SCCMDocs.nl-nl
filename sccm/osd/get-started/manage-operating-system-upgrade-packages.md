---
title: Upgradepakketten voor het besturingssysteem beheren
titleSuffix: Configuration Manager
description: Informatie over het beheren van upgradepakketten voor besturingssysteem in System Center Configuration Manager.
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
caps.latest.revision: "12"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: b70e8ecd32957f19b9738d14c94c7e54b0312ea5
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2017
---
# <a name="manage-operating-system-upgrade-packages-with-system-center-configuration-manager"></a>Upgradepakketten van het besturingssysteem beheren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Een upgradepakket in System Center Configuration Manager bevat de bronbestanden voor installatie van Windows die worden gebruikt voor het upgraden van een bestaand besturingssysteem op een computer. Gebruik de volgende secties upgradepakketten voor besturingssysteem in Configuration Manager beheren.

##  <a name="BKMK_AddOSUpgradePkgs"></a> Upgradepakketten voor het besturingssysteem toevoegen aan Configuration Manager  
 Voordat u een upgradepakket voor besturingssysteem gebruiken kunt, moet u het pakket toevoegen aan een Configuration Manager-site. Gebruik de volgende procedure om een upgradepakket voor het besturingssysteem toe te voegen aan een site.  

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
 Installatiekopieën van het besturingssysteem worden op dezelfde manier naar distributiepunten gedistribueerd als andere inhoud. In de meeste gevallen moet u het besturingssysteem naar ten minste één distributiepunt distribueren voordat u het besturingssysteem implementeert. Zie [Inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute) voor stappen om een installatiekopie van een besturingssysteem te distribueren.  

##  <a name="BKMK_OSUpgradePkgApplyUpdates"></a> Software-updates toepassen op een updatepakket van een besturingssysteem  
 Vanaf versie 1602 van Configuration Manager, kunt u nieuwe software-updates toepassen op de installatiekopie van het besturingssysteem in het upgradepakket van uw besturingssysteem. Voordat u kunt software-updates toepassen op een updatepakket hebt u hebben uw software-updates-infrastructuur, is gesynchroniseerd software-updates en de software-updates gedownload naar de Inhoudsbibliotheek op de siteserver. Zie voor meer informatie [software-updates implementeren](../../sum/deploy-use/deploy-software-updates.md).  

 U kunt toepasselijke software-updates volgens een opgegeven schema toepassen op een updatepakket. Het schema dat u opgeeft, Configuration Manager past de software-updates die u selecteert op het updatepakket van het besturingssysteem, en vervolgens wordt het bijgewerkte updatepakket naar distributiepunten optioneel gedistribueerd. Informatie over het updatepakket van het besturingssysteem wordt opgeslagen in de sitedatabase, inclusief de software-updates die tijdens het importeren zijn toegepast. Software-updates die op het updatepakket zijn toegepast sinds de kopie voor het eerst werd toegevoegd, worden ook opgeslagen in de sitedatabase. Wanneer u de wizard start om software-updates toe te passen op het updatepakket van het besturingssysteem, wordt er een lijst opgehaald met toepasselijke software-updates die nog niet zijn toegepast op het updatepakket. U kunt dan een selectie maken uit deze lijst. Configuration Manager kopieert de softwareupdates in de Inhoudsbibliotheek op de siteserver en past de software-updates op het updatepakket van het besturingssysteem.  

 Gebruik de volgende procedure om software-updates toe te passen op een updatepakket van een besturingssysteem.  

#### <a name="to-apply-software-updates-to-an-operating-system-upgrade-package"></a>Software-updates toepassen op een updatepakket van een besturingssysteem  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** het knooppunt **Besturingssystemen**uit en klik vervolgens op **Upgradepakketten voor besturingssysteem**.  

3.  Selecteer het updatepakket waarop u software-updates wilt toepassen.  

4.  Klik op het tabblad **Start** in de groep **Updatepakket van het besturingssysteem** op **Updates plannen** om de wizard te starten.  

5.  Selecteer op de pagina **Updates kiezen** de software-updates die moeten worden toegepast op de installatiekopie van het besturingssysteem en klik vervolgens op **Volgende**.  

6.  Geef, op de pagina **Schema instellen** , de volgende instellingen op, en klik vervolgens op **Volgende**.  

    1.  **Planning**: Geef de planning voor wanneer de software-updates worden toegepast op de installatiekopie van het besturingssysteem.  

    2.  **Doorgaan bij fout**:  Selecteer deze optie om door te gaan naar het software-updates toepassen op de installatiekopie, zelfs wanneer er een fout opgetreden.  

    3.  **De installatiekopie distribueren naar distributiepunten**: Selecteer deze optie om de installatiekopie van het besturingssysteem op distributiepunten werken nadat de software-updates zijn toegepast.  

7.  Verifieer de informatie op de pagina **Samenvatting** en klik vervolgens op **Volgende**.  

8.  Verifieer op de pagina **Voltooiing** dat de software-updates met succes zijn toegepast op de installatiekopie van het besturingssysteem.  
