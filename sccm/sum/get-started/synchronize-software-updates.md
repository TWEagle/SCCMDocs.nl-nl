---
title: Synchronisatie van software-updates beheren | Microsoft Docs
description: Volg deze stappen om synchronisatie van software-updates plannen, handmatig starten van synchronisatie van software-updates en synchronisatie van software-updates controleren.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: ea8698c4-9df5-4cf5-8b62-ab93115b4769
ms.openlocfilehash: e68170a16a6a908e035247ed9c0f3cc6cdbe1983
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
#  <a name="BKMK_SUMSync"></a> Software-updates synchroniseren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Synchronisatie van software-updates in Configuration Manager is het proces van het ophalen van de metagegevens van de software-update die voldoet aan de criteria die u configureert. Dit omvat specifieke producten, classificaties en talen. De software-updatepunt op de centrale beheersite of op een zelfstandige primaire site haalt meestal de metagegevens van Microsoft Update. Vervolgens wordt de site op het hoogste niveau een synchronisatieaanvraag verzenden naar andere sites. Wanneer een site de synchronisatieaanvraag van de bovenliggende site ontvangt, de software-updatepunt voor de site metagegevens van software-updates opgehaald uit de upstream [synchronisatiebron](../plan-design/plan-for-software-updates.md#BKMK_SyncSource). Zie voor meer informatie over het synchronisatieproces voor software-update [synchronisatie van Software-updates](../understand/software-updates-introduction.md#BKMK_Synchronization).

U configureren software-updatesynchronisaties worden uitgevoerd volgens een schema in de eigenschappen voor de software-updatepunt op het hoogste niveau. Nadat u de synchronisatieplanning hebt ingesteld, hoeft u dit doorgaans niet te wijzigen als onderdeel van het normale gebruik. U kunt wanneer dat nodig is echter handmatig een software-updatesynchronisatie starten.

  > [!NOTE]  
  >  Software-updatepunten moeten worden verbonden met de bijbehorende stroomopwaartse synchronisatiebron gebruikt om softwareupdates te synchroniseren. Wanneer de verbinding van een software-updatepunt met de synchronisatiebron stroomopwaarts ervan is verbroken, kunt u de export- en importmethode gebruiken om software-updates te synchroniseren. Zie de sectie [Software-updates synchroniseren vanaf een niet-verbonden software-updatepunt](synchronize-software-updates-disconnected.md) voor meer informatie.  

## <a name="schedule-software-updates-synchronization"></a>Synchronisatie van software-updates plannen
Wanneer u een planning voor synchronisatie van software-updates configureert, de site op het hoogste software-updatepunt wordt synchronisatie gestart met Microsoft Update op de geplande datum en tijd. De aangepaste planning kunt u softwareupdates te synchroniseren op een datum en tijd wanneer de aanvragen van de WSUS-server, siteserver en netwerk laag zijn. U kunt bijvoorbeeld de planning instellen zodat de software-updates zijn gesynchroniseerd per week om 02.00 uur. Tijdens de geplande synchronisatie worden alle wijzigingen die sinds de laatste synchronisatie in de metagegevens van de software-updates zijn aangebracht, ingevoegd in de sitedatabase. Dit omvat nieuwe metagegevens van software-updates of metagegevens die zijn gewijzigd, verwijderd of nu zijn verlopen.

Gebruik de volgende procedures op de site op het hoogste niveau de synchronisatie van software-updates plannen.  

#### <a name="to-schedule-software-updates-synchronization"></a>Synchronisatie van software-updates plannen  

  1.  Klik op **Beheer**in de Configuration Manager-console.  

  2.  Vouw **Siteconfiguratie**uit in de beheerwerkruimte en klik vervolgens op **Sites**.  

  3.  Klik in het resultatenvenster op de centrale beheersite of de zelfstandige primaire site.  

  4.  Vouw op het tabblad **Start** in de groep **Instellingen** het knooppunt **Siteonderdelen configureren**uit en klik op **Software-updatepunt**.  

  5.  Selecteer in het dialoogvenster Eigenschappen van Software-updatepuntcomponenten **Synchronisatie op een planning inschakelen**en geef vervolgens de synchronisatieplanning op.  

## <a name="manually-start-software-updates-synchronization"></a>Synchronisatie van software-updates handmatig starten
U kunt handmatig starten synchronisatie van software-updates op het hoogste niveau in de Configuration Manager-console van de **alle Software-Updates** knooppunt in de **softwarebibliotheek** werkruimte.  

Gebruik de volgende procedures op de site op het hoogste niveau voor de synchronisatie van software-updates handmatig starten.  

#### <a name="to-manually-start-software-updates-synchronization"></a>Synchronisatie handmatig starten van software-updates  

  1.  Klik in de Configuration Manager-console die is verbonden met de centrale beheersite of zelfstandige primaire site op **softwarebibliotheek**.  

  2.  Vouw **Software-updates** uit in de Softwarebibliotheekwerkruimte en klik vervolgens op **Alle software-updates** of **Software-updategroepen**.  

  3.  Klik op het tabblad **Start** in de groep **Maken** op **Software-updates synchroniseren**. Klik op **Ja** in het dialoogvenster om te bevestigen dat u het synchronisatieproces wilt starten.  

   Nadat u het synchronisatieproces op het software-updatepunt hebt gestart, kunt u het synchronisatieproces uit de Configuration Manager-console voor alle software-updatepunten in uw hiërarchie bewaken. Gebruik de volgende procedure om het synchronisatieproces van de software-updates te controleren.  


## <a name="monitor-software-updates-synchronization"></a>Synchronisatie van software-updates bewaken
Nadat u het synchronisatieproces hebt gestart, kunt u de Configuration Manager-console kunt gebruiken voor het bewaken van het proces voor alle software-updatepunten in uw hiërarchie. Gebruik de volgende procedure om het synchronisatieproces voor software-updates te controleren. Zie voor meer informatie over het controleren van de software-updates, waaronder het synchronisatieproces [software-updates controleren](../deploy-use/monitor-software-updates.md).

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>Het synchronisatieproces voor software-updates controleren  

  1.  Klik in de Configuration Manager-console op **bewaking**.  

  2.  Klik in de werkruimte **Bewaking** op **Synchronisatiestatus van software-updatepunten**.  

    De software-updatepunten in uw Configuration Manager-hiërarchie worden weergegeven in het deelvenster met resultaten. In deze weergave kunt u de synchronisatiestatus van alle software-updatepunten controleren. Wanneer u meer gedetailleerde informatie over het synchronisatieproces wenst, kunt u het bestand wsyncmgr.log bekijken. Dit bestand bevindt zich op de volgende locatie: <*ConfigMgrInstallationPath*>\logboeken op elke siteserver.  

## <a name="next-steps"></a>Volgende stappen
Nadat u software-updates voor het eerst synchroniseert, of nadat er nieuwe classificaties of producten beschikbaar zijn, u moet [de nieuwe classificaties en producten configureren](configure-classifications-and-products.md) softwareupdates te synchroniseren met de nieuwe criteria.

Na het synchroniseren van software-updates met de criteria die u nodig hebt, [instellingen beheren voor software-updates](manage-settings-for-software-updates.md).  
