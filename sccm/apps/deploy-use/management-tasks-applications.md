---
title: Beheertaken voor toepassingen
titleSuffix: Configuration Manager
description: System Center Configuration Manager-toepassingen en implementatietypen beheren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4041e21-21ff-4d95-ab05-14007e0047cf
caps.latest.revision: "8"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 8d4cc2cd8de9626b6911dc50dbdec2ccdaada94c
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="management-tasks-for-system-center-configuration-manager-applications"></a>Beheertaken voor System Center Configuration Manager-toepassingen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit artikel voor het beheren van System Center Configuration Manager-toepassingen en implementatietypen.  

Zie voor informatie over het maken van toepassingen en implementatietypen [toepassingen maken](../../apps/deploy-use/create-applications.md).  

> [!IMPORTANT]  
>  Afhankelijk van het type toepassing of implementatietype sommige beheeropties mogelijk niet beschikbaar.  

##  <a name="manage-applications"></a>Toepassingen beheren  
 In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer** > **toepassingen**, kies de toepassing om te beheren en kies vervolgens een beheertaak.  

|Taak|Details|  
|----------|-------------|  
|**Toegangsaccounts beheren**|Hiermee wordt het dialoogvenster **Toegangsaccounts beheren** geopend, waarin u het toegangsniveau kunt opgeven dat is toegestaan voor de inhoud die aan de geselecteerde toepassing is gekoppeld.|  
|**Voorbereid inhoudsbestand maken**|Hiermee wordt de **Wizard Voorbereid inhoudsbestand maken** geopend, waarmee u de distributie van inhoud naar externe distributiepunten kunt beheren. Wanneer met planning en beperking geen geldige oplossing wordt geboden voor het externe distributiepunt, kunt u de inhoud voorbereiden op het distributiepunt<br /><br /> Zie [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Overzicht van wijzigingen**|Hiermee opent u de **overzicht van Toepassingsrevisies** in het dialoogvenster waarmee u de eigenschappen van revisies die zijn aangebracht aan deze toepassing weergeven, oude toepassingsrevisies kunt verwijderen en oude versies van deze toepassing te herstellen.<br /><br /> Zie [hoe toepassingen herzien en vervangen](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Implementatietype maken**|Hiermee opent u de **Wizard implementatietype maken** waarmee u een nieuw implementatietype kunt toevoegen aan de geselecteerde toepassing.<br /><br /> Zie [toepassingen maken](../../apps/deploy-use/create-applications.md).|  
|**Statistieken bijwerken**|Hiermee wordt de informatie bijgewerkt die in het knooppunt **Implementaties** van de werkruimte **Bewaking** wordt weergegeven over de implementaties van deze toepassing.<br /><br /> Zie [toepassingen bewaken vanuit de System Center Configuration Manager-console](../../apps/deploy-use/monitor-applications-from-the-console.md).|  
|**Opnieuw invoeren**|Wordt een toepassing die buiten gebruik werd gesteld met behulp van de **buiten gebruik stellen** beheertaak.|  
|**Buiten gebruik stellen**|Wanneer u een toepassing buiten gebruik stellen, is niet meer beschikbaar voor implementatie, maar de toepassing en implementaties van de toepassing niet worden verwijderd. Bestaande exemplaren van deze toepassing die op clientcomputers werden geïnstalleerd, worden niet verwijderd. Eventuele wijzigingen aan de toepassing worden na 60 dagen uit Configuration Manager verwijderd. Maar geïnstalleerde exemplaren van de toepassing niet worden verwijderd.<br /><br /> Als u wilt verwijderen van een toepassing, moet u eerst buiten gebruik stellen van de toepassing, alle implementaties verwijderd, verwijzingen naar de toepassing uit andere implementaties verwijderen en vervolgens alle revisies van de toepassing te verwijderen.<br /><br /> Zie [herzien en vervangen van toepassingen](../../apps/deploy-use/revise-and-supersede-applications.md).|  
|**Exportereneren**|Hiermee opent u de **Wizard toepassing exporteren** waarmee u de geselecteerde toepassingen naar een ZIP-bestand dat u vervolgens kunt archiveren of op een andere site installeert exporteren. Als u ervoor kiest toepassingsinhoud te exporteren, kunt u een map die de inhoud wordt gemaakt.<br /><br /> U kunt ook toepassingsafhankelijkheden, vervangingsrelaties en voorwaarden en inhoud voor de toepassing en de bijbehorende afhankelijkheden exporteren.<br /><br /> De Windows PowerShell-cmdlet **Export-CMApplication**, wordt dezelfde functie. Zie voor meer informatie [Export-CMApplication](http://go.microsoft.com/fwlink/p/?LinkID=258880) in de documentatie van Microsoft System Center 2012 Configuration Manager SP1 cmdlet-verwijzing.|  
|**Verwijderen**|Hiermee verwijdert u de geselecteerde toepassing.<br /><br /> U kunt een toepassing niet verwijderen als andere toepassingen ervan afhankelijk zijn, als er een actieve implementatie van de toepassing is of als de toepassing afhankelijke takenreeksen heeft.|  
|**Implementatie simuleren**|Hiermee wordt de **Wizard Implementatie van toepassing simuleren** geopend, waarin u de resultaten van een toepassingsimplementatie op computers kunt testen zonder de toepassing daadwerkelijk te installeren of verwijderen.<br /><br /> Zie [toepassingsimplementaties simuleren](../../apps/deploy-use/simulate-application-deployments.md).|  
|**Implementeren**|Hiermee wordt de **Wizard Software implementeren** geopend, waarin u de geselecteerde toepassing kunt implementeren naar verzamelingen computers in uw hiërarchie.<br /><br /> Zie [toepassingen implementeren](../../apps/deploy-use/deploy-applications.md).|  
|**Inhoud distribueren**|Hiermee wordt de **Wizard Inhoud distribueren** geopend, waarin u de inhoud voor de geselecteerde toepassing kunt kopiëren naar distributiepunten in uw hiërarchie.<br /><br /> Zie [inhoud en infrastructuur beheren](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Relaties weergeven**|Toont een grafische voorstelling van de relaties van geselecteerde toepassingen voor andere toepassingen. Kies een van de volgende opties:<br><br><ul><li>**Afhankelijkheid** – worden toepassingen weergegeven die afhankelijk van de geselecteerde toepassing en de toepassingen die afhankelijk zijn zijn van de geselecteerde toepassing.</li><li>**Vervanging** – geeft toepassingen die de geselecteerde toepassing vervangt en toepassingen die door de geselecteerde toepassing is vervangen.</li><li>**Globale voorwaarden** – ziet u de globale voorwaarden waarnaar wordt verwezen door deze toepassing.</li></ol><br /> Zie [herzien en vervangen van toepassingen](../../apps/deploy-use/revise-and-supersede-applications.md) en [globale voorwaarden maken](../../apps/deploy-use/create-global-conditions.md).|  

##  <a name="manage-deployment-types"></a>Implementatietypen beheren  
 In de **softwarebibliotheek** werkruimte Vouw **Toepassingsbeheer**, kies **toepassingen**, en kies vervolgens de toepassing die heeft het implementatietype dat u wilt beheren. Kies in het detailvenster de **implementatietypen** tabblad, kiest u het implementatietype dat u wilt beheren en kies vervolgens een beheertaak.  

|Taak|Details|  
|----------|-------------|  
|**Prioriteit verhogen**|Hiermee wordt de prioriteit van het geselecteerde implementatietype verhoogd. Implementatietypen worden opeenvolgend geëvalueerd. Wanneer een implementatietype voldoet aan de opgegeven vereisten, wordt uitgevoerd en vervolgens geen verdere implementatietypen in de prioriteitenlijst wordt geëvalueerd.|  
|**Prioriteit verlagen**|Hiermee wordt de prioriteit van het geselecteerde implementatietype verlaagd.|  
|**Verwijderen**|Hiermee wordt het geselecteerde implementatietype verwijderd.<br><br>U kunt een implementatietype niet verwijderen als ernaar wordt verwezen door een implementatietype in een andere toepassing.<br>Als u wilt verwijderen van een implementatietype, moet u alle afhankelijkheden van het implementatietype in andere implementatietypen verwijderen.<br>Bovendien moet u ook eerdere revisies van alle toepassingen waarvoor een implementatietype dat verwijst naar het implementatietype dat u wilt verwijderen verwijderen.|  
|**Inhoud bijwerken**|Hiermee wordt de inhoud vernieuwd voor het geselecteerde implementatietype.<br /><br /> Wanneer u deze wizard start voor een implementatietype dat een virtuele toepassing, is de **Wizard inhoud bijwerken** is gestart. Deze wizard kunt u publicatieopties en regels voor vereisten voor de geselecteerde virtuele toepassing kunt wijzigen. Zie voor meer informatie [toepassingen maken](../../apps/deploy-use/create-applications.md).<br /><br /> Wanneer u de inhoud van een implementatietype vernieuwt, wordt er een nieuwe revisie van de toepassing gemaakt. Hierdoor worden clientapparaten mogelijk bijgewerkt met de nieuwe toepassing.|  
