---
title: Aanbevolen procedures voor software-updates | Microsoft Docs
description: Gebruik deze best practices voor software-updates in System Center Configuration Manager.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 6d20389a-9de2-4a64-bced-9fc4fa519174
ms.openlocfilehash: 5df20f3703442de1be6220ca2770e182e330c036
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="best-practices-for-software-updates-in-system-center-configuration-manager"></a>Best practices voor software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp bevat aanbevolen procedures voor software-updates in System Center Configuration Manager. De informatie wordt onderverdeeld in aanbevolen procedures voor oorspronkelijke installaties en aanbevolen procedures voor actieve bewerkingen.  

## <a name="installation-best-practices"></a>Best practices voor installatie  
 Gebruik de volgende aanbevolen procedures bij het installeren van software-updates in Configuration Manager.  

### <a name="use-a-shared-wsus-database-for-software-update-points"></a>Gebruik een gedeelde WSUS-database voor software-updatepunten  
 Wanneer u meer dan één software-updatepunt op een primaire site installeert, gebruikt u dezelfde WSUS-database voor elk software-updatepunt in hetzelfde Active Directory-forest. Door dezelfde database te delen, kunt u het effect op de client- en netwerkprestaties, dat zich kan voordoen wanneer clients overschakelen naar een nieuw software-updatepunt, aanzienlijk beperken. Wanneer een client overschakelt naar een nieuw software-updatepunt dat een database deelt met het oude software-updatepunt, wordt er nog wel een deltascan uitgevoerd, maar is deze scan veel minder uitgebreid dan wanneer de WSUS-server een eigen database heeft.  

> [!IMPORTANT]  
>  Wanneer u een gedeelde WSUS-database voor software-updatepunten gebruikt, moet u de lokale mappen met WSUS-inhoud delen.  

 Zie voor meer informatie over deze instellingen, de [update schakelen tussen Software-](../../sum/plan-design/plan-for-software-updates.md#BKMK_SUPSwitching) sectie het [plannen voor software-updates in System Center Configuration Manager](../../sum/plan-design/plan-for-software-updates.md) onderwerp.  

### <a name="when-configuration-manager-and-wsus-use-the-same-sql-server-configure-one-of-these-to-use-a-named-instance-and-the-other-to-use-the-default-instance-of-sql-server"></a>Wanneer door Configuration Manager en WSUS wordt gebruikgemaakt van hetzelfde exemplaar van SQL Server, configureert u Configuration Manager of WSUS om gebruik te maken van het standaardexemplaar van SQL Server  
 Wanneer de Configuration Manager en WSUS-databases dezelfde SQL Server gebruiken en delen van hetzelfde exemplaar van SQL Server, kunt u het gebruik van bronnen tussen de twee toepassingen kan niet eenvoudig bepalen. Wanneer u een ander exemplaar van SQL Server voor Configuration Manager en WSUS gebruikt, is het eenvoudiger oplossen en diagnosticeren resource gebruik problemen die voor elke toepassing optreden kunnen.  

### <a name="specify-the-store-updates-locally-setting-for-the-wsus-installation"></a>Geef de instelling Updates lokaal opslaan op voor de WSUS-installatie  
 Wanneer u WSUS installeert, selecteert u de **updates lokaal opslaan** instelling. Wanneer deze instelling is geselecteerd, worden de licentievoorwaarden behorend bij software-updates gedownload tijdens het synchronisatieproces en opgeslagen op de lokale harde schijf voor de WSUS-server. Als deze instelling niet is geselecteerd, worden software-updates met licentievoorwaarden op clientcomputers mogelijk niet gecontroleerd op naleving. Wanneer u het software-updatepunt installeert, wordt door WSUS-synchronisatiebeheer standaard elke zestig minuten gecontroleerd of deze instelling is ingeschakeld.  

## <a name="operational-best-practices"></a>Aanbevolen operationele procedures  
 Gebruik de volgende aanbevolen procedures wanneer u software-updates gebruikt:  

### <a name="limit-software-updates-to-1000-in-a-single-software-update-deployment"></a>Beperk software-updates tot duizend in één implementatie van software-updates  
 U moet het aantal software-updates tot duizend beperken voor elke implementatie van software-updates. Wanneer u een regel voor automatische implementatie maakt, moet u controleren of de door u opgegeven criteria niet resulteren in meer dan duizend software-updates. Selecteer maximaal 1000 te implementeren updates wanneer u software-updates handmatig implementeert.  

### <a name="create-a-new-software-update-group-each-time-an-automatic-deployment-rule-runs-for-patch-tuesday-and-for-general-deployment"></a>Telkens wanneer die een regel voor automatische implementatie wordt uitgevoerd voor "Patch-dinsdag" en voor algemene implementatie van een nieuwe software-updategroep maken  
 Er geldt een limiet van duizend software-updates voor een implementatie van software-updates. Wanneer u een regel voor automatische implementatie maakt, geeft u op of een bestaande updategroep moet worden gebruikt of een nieuwe updategroep moet worden gemaakt wanneer de regel wordt uitgevoerd. Wanneer u in een regel voor automatische implementatie criteria opgeeft die resulteren in meerdere software-updates en de regel op basis van een schema regelmatig wordt uitgevoerd, geeft u op dat er een nieuwe software-updategroep moet worden gemaakt wanneer de regel wordt uitgevoerd. Op deze manier voorkomt u dat de limiet van duizend software-updates per implementatie wordt overschreden.  

### <a name="use-an-existing-software-update-group-for-automatic-deployment-rules-for-endpoint-protection-definition-updates"></a>Gebruik een bestaande software-updategroep voor regels voor automatische implementatie voor definitie-updates voor Endpoint Protection  
 Gebruik altijd een bestaande software-updategroep wanneer u een regel voor automatische implementatie gebruikt om regelmatig definitie-updates voor Endpoint Protection te implementeren. Zo voorkomt u dat er na verloop van tijd honderden software-updategroepen zijn. Doorgaans stellen uitgevers van definitie-updates in dat deze verlopen zodra er vier nieuwere updates zijn. Als gevolg daarvan bevat de software-updategroep die wordt gemaakt door de regel voor automatische implementatie nooit meer dan vier definitie-updates voor de uitgever: één actieve en drie vervangen updates.  

## <a name="see-also"></a>Zie ook  
 [Plannen voor software-updates in System Center Configuration Manager](../../sum/plan-design/plan-for-software-updates.md)
