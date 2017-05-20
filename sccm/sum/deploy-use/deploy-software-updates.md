---
title: Software-updates implementeren | Microsoft-documenten
description: Kies software-updates in de Configuration Manager-console handmatig starten van het implementatieproces of updates automatisch implementeren.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 04536d51-3bf7-45e5-b4af-36ceed10583d
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 70a0ad1da03a7ca88df206fec683ab1df2b531e1
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

#  <a name="BKMK_SUMDeploy"></a> Software-updates implementeren  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De software-update-implementatiefase is het proces van het implementeren van de software-updates. Ongeacht de manier waarop u software-updates implementeren, de updates worden meestal toegevoegd aan een software-updategroep, de software-updates worden gedownload naar distributiepunten en de updategroep wordt geïmplementeerd op clients. Wanneer u de implementatie maakt, wordt een gekoppelde software-updatebeleid naar clientcomputers, de inhoud gedownload vanaf een distributiepunt naar de lokale cache op clientcomputers wordt geïnstalleerd en vervolgens de software-updates beschikbaar zijn voor installatie van de client software-update verzonden. Clients op het Internet downloaden inhoud vanaf Microsoft Update.  

> [!NOTE]  
>  U kunt een client op het intranet configureren om software-updates te downloaden vanaf Microsoft Update als er geen distributiepunt beschikbaar is.  

> [!NOTE]  
>  In tegenstelling tot andere implementatietypes worden software-updates allemaal gedownload naar de clientcache ongeacht de maximum cachegrootte-instelling op de client. Voor meer informatie over de cache-instelling van de client, zie [De clientcache voor Configuration Manager-clients configureren](../../core/clients/manage/manage-clients.md#BKMK_ClientCache).  

Als u een vereiste software-update-implementatie configureert, worden de software-updates automatisch geïnstalleerd tegen de geplande deadline. De gebruiker op de clientcomputer kan de installatie van de software-updates ook plannen of starten vóór de deadline. Na een geprobeerde installatie versturen clientcomputers statusberichten terug naar de siteserver om te rapporteren of de installatie van de software-update geslaagd was. Zie [Implementatiewerkstromen van software-updates](../understand/software-updates-introduction.md#BKMK_DeploymentWorkflows) voor meer informatie over de implementatie van software-updates.  

Er zijn twee hoofdscenario's voor het implementeren van software-updates: handmatige implementatie en automatische implementatie. Doorgaans begint u met het handmatig implementeren van software-updates voor het maken van een basislijn voor uw client computers, en vervolgens beheert u software-updates op clients via automatische implementatie.  

## <a name="BKMK_ManualDeployment"></a>Software-updates handmatig implementeren
U kunt software-updates in de Configuration Manager-console selecteren en handmatig start het implementatieproces. Doorgaans gebruikt u deze methode van implementatie om de clientcomputers up-to-date te krijgen met de vereiste software-updates voordat u automatische implementatieregels kunt maken die de lopende maandelijkse implementaties van software-updates beheren, en om buiten-bandvereisten van software-updates te implementeren. De volgende lijst geeft de algemene werkstroom voor handmatige implementatie van software-updates:  

1. Filter voor software-updates die gebruikmaken van specifieke vereisten. U kunt bijvoorbeeld criteria opgeven die alle beveiligingsupdates of kritieke software-updates ophalen die op meer dan 50 clientcomputers zijn vereist.  
2. Maak een software-updategroep die de software-updates bevat.  
3. Downloadt de inhoud voor software-updates in de software-updategroep.  
4. De software-updategroep handmatig implementeren.

Zie voor gedetailleerde stappen [software-updates handmatig implementeert](manually-deploy-software-updates.md).

## <a name="automatically-deploy-software-updates"></a>Software-updates automatisch implementeren
De automatische implementatie van software-updates wordt geconfigureerd met een regel voor automatische implementatie (ADR). Dit is een algemene implementatiemethode voor maandelijkse software-updates zoals (meestal "Patch dinsdag" genoemd) en voor het beheren van definitie-updates. Wanneer de regel wordt uitgevoerd, software-updates verwijderd uit de software-updategroep (als u een bestaande updategroep), de software-updates die voldoen aan worden de opgegeven criteria (bijvoorbeeld alle beveiligingsupdates die in de afgelopen maand) toegevoegd aan een software-updategroep, de inhoudsbestanden voor de software-updates gedownload en gekopieerd naar distributiepunten en de software-updates worden geïmplementeerd naar clients in de doelverzameling. De volgende lijst geeft de algemene werkstroom voor software-updates automatisch implementeren:  

1.  Maak een ADR die implementatie-instellingen opgeeft.
2.  De software-updates worden toegevoegd aan een software-updategroep.  
3.  De software-updategroep wordt geïmplementeerd naar de clientcomputers in de doelverzameling, als deze is opgegeven.  

U moet bepalen welke implementatiestrategie er moet worden gebruikt in uw omgeving. U kunt bijvoorbeeld een regel voor automatische implementatie maken en een verzameling van testclients als doel nemen. Nadat u hebt gecontroleerd of de software-updates op de testgroep zijn geïnstalleerd, kunt u een nieuwe implementatie aan de regel toevoegen of de verzameling in de bestaande implementatie wijzigen in een doelverzameling die een grotere set van clients bevat. De software-updateobjecten die door de regels voor automatische implementatie worden gemaakt, zijn interactief.  

-   Software-updates die zijn geïmplementeerd met een regel voor automatische implementatie worden automatisch geïmplementeerd voor nieuwe clients die aan de doelverzameling zijn toegevoegd.  
-   Nieuwe software-updates die zijn toegevoegd aan een software-updategroep, worden automatisch geïmplementeerd naar de clients in de doelverzameling.  
-   U kunt implementaties voor de regel voor automatische implementatie op elk gewenst moment in- of uitschakelen.  

Nadat u een regel voor automatische implementatie hebt gemaakt, kunt u aanvullende implementaties aan de regel toevoegen. Dit kan helpen bij het beheren van de complexiteit van het implementeren van verschillende updates voor verschillende verzamelingen. Elke nieuwe implementatie beschikt over de volledige functionaliteit en implementatiecontrole, en elke implementatie die u toevoegt:  

-   Gebruikt dezelfde bijwerkgroep en hetzelfde bijwerkpakket die worden gemaakt wanneer de ADR voor het eerst wordt uitgevoerd  
-   U kunt een andere verzameling opgeven  
-   Ondersteunt unieke implementatie-eigenschappen, waaronder:  
   -   Activeringstijd  
   -   Deadline  
   -   Ervaringen van eindgebruikers weergeven of verbergen  
   -   Afzonderlijke waarschuwingen voor deze implementatie  

Zie voor gedetailleerde stappen [software-updates automatisch implementeren](automatically-deploy-software-updates.md)

<!-- ###  <a name="BKMK_ClientCache"></a> Client cache setting  
The Configuration Manager client downloads the content for required software updates to the local client cache soon after it receives the deployment. However, the client waits to download the content until after the **Software available time** setting for the deployment. The client does not download software updates in optional deployments (deployments that do not have a scheduled installation deadline) until the user manually starts the installation. When the configured deadline passes, the software updates client agent performs a scan to verify that the software update is still required, then the software updates client agent checks the local cache on the client computer to verify that the software update source file is still available, and then installs the software update. If the content was deleted from the client cache to make room for another deployment, the client downloads the software updates to the cache. Software updates are always downloaded to the client cache regardless of the configured maximum client cache size. For other deployments, such as applications or packages, the client only downloads content that is within the maximum cache size that you configure for the client. Cached content is not automatically deleted, but it remains in the cache for at least one day after the client used that content.  -->


 <!-- For more information about the deployment process, see [Software update deployment process](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess).  -->

