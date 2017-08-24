---
title: Testclient upgrades pre-productieverzameling | Microsoft Docs
description: Clientupgrades testen in pre-productieverzameling in System Center Configuration Manager.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49ef2ed2-2e15-4637-8b63-1d5b7f9c17e1
caps.latest.revision: "10"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 572ef13883f7930e69ec1f1f53c9bfe029898c81
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-test-client-upgrades-in-a-pre-production-collection-in-system-center-configuration-manager"></a>Clientupgrades testen in pre-productieverzameling in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt een nieuwe clientversie van de Configuration Manager-testen in pre-productieverzameling voordat u de rest van de site bijwerkt.  Als u dit doet, worden alleen apparaten die deel van de testverzameling uitmaken bijgewerkt. Zodra u hebt voor het testen van de client die u kunt de client promoveren, waardoor de nieuwe versie van de clientsoftware beschikbaar voor de rest van de site.

> [!NOTE]
> Als u een testclient naar productie verhogen, moet u zijn aangemeld als een gebruiker met de beveiligingsrol van **volledige beheerder** en een beveiligingsbereik van **alle**. Zie voor meer informatie [basisprincipes van beheer op basis van rollen](/sccm/core/understand/fundamentals-of-role-based-administration). U moet ook worden aangemeld bij een server die is verbonden met de centrale beheersite of een op het hoogste niveau zelfstandige primaire site.

 Er zijn 3 basisstappen voor het testen van clients in een testomgeving.  

1.  Automatische clientupgrades voor het gebruik van pre-productieverzameling configureren.  

2.  Een Configuration Manager-update een nieuwe versie van de client bevat installeert.  

3.  De nieuwe client naar productie promoten.  

##  <a name="to-configure-automatic-client-upgrades-to-use-a-pre-production-collection"></a>Automatische clientupgrades voor het gebruik van pre-productieverzameling configureren  

1. [Instellen van een verzameling](..\collections\create-collections.md) die de computers die u wilt implementeren de preproductie-client bevat. Geen computers in werkgroepen niet opnemen in verzamelingen voor preproductie. Ze de verificatie is vereist voor het distributiepunt niet gebruiken voor toegang tot de pre-productieclientpakket.   

1.  In de Configuration Manager-console openen **beheer** > **siteconfiguratie** > **Sites**, en kies **hiërarchie-instellingen**.  

     Op het tabblad **Clientupgrade** van de **Eigenschappen van de hiërarchie-instellingen**:  

    -   Selecteer **Automatisch upgrade uitvoeren voor alle clients in de pre-productieverzameling met gebruik van pre-productieclient**  

    -   Geef de naam van een verzameling op om te gebruiken als pre-productieverzameling  

![Clientupgrades testen](media/test-client-upgrades.png)

>[!NOTE]
>Deze instellingen wilt wijzigen, moet uw account lid zijn van de **volledige beheerder** beveiligingsrol en de **alle** beveiligingsbereik.


##  <a name="to-install-a-configuration-manager-update-that-includes-a-new-version-of-the-client"></a>Een Configuration Manager-update met een nieuwe versie van de client te installeren  

1.  Open in de Configuration Manager-console **beheer** > **Updates en onderhoud**, selecteer een **beschikbaar** bijwerken, en kies vervolgens **updatepakket installeren**. (Voorafgaand aan versie 1702, Updates en onderhoud is onder **beheer** > **Cloudservices**.)

     Zie [Updates voor System Center Configuration Manager](../../../../core/servers/manage/updates.md) voor meer informatie over het installeren van updates.  

2.  Tijdens de installatie van de update op de **clientopties** pagina van de wizard de optie **testen in pre-productieverzameling**.  

3.  Voltooi de rest van de wizard en installeer het updatepakket.  

     Nadat de wizard is voltooid, beginnen clients in de pre-productieverzameling met het implementeren van de bijgewerkte client. U kunt de implementatie van bijgewerkte clients controleren door naar **Controleren** > **Clientstatus** > **Pre-productieclientimplementatie**te gaan. Zie [De clientimplementatiestatus controleren in System Center Configuration Manager](../../../../core/clients/deploy/monitor-client-deployment-status.md) voor meer informatie.

    > [!NOTE]
    > De status van de implementatie op computers die als host fungeert voor sitesysteemrollen in een pre-productieverzameling kan worden gerapporteerd als **niet compatibel** zelfs wanneer de client is geïmplementeerd. Wanneer u promoveert naar productie, wordt de status van de implementatie correct gerapporteerd.

##  <a name="to-promote-the-new-client-to-production"></a>De nieuwe client naar productie promoten  

1.  Open in de Configuration Manager-console **beheer** > **Updates en onderhoud**, en kies **promoveren pre-Productieclient**. (Voorafgaand aan versie 1702, Updates en onderhoud is onder **beheer** > **Cloudservices**.)

    > [!TIP]
    > De knop **Niveau van de pre-productieclient verhogen** is ook beschikbaar als u clientimplementaties controleert in de console via **Controleren** > **Clientstatus** > **Clientimplementatie vóór productie**.

2.  Bekijk de clientversies in productie- en preproductie, controleert u of de juiste de pre-productieverzameling is opgegeven, en klik vervolgens op **opwaarderen**, klikt u vervolgens **Ja**.  

3.  Nadat u het dialoogvenster wordt gesloten, vervangt de bijgewerkte clientversie de versie van de client gebruikt in uw hiërarchie. Vervolgens kunt u de clients voor de gehele site upgraden. Zie [Clients voor Windows-computers bijwerken in System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) voor meer informatie.  

>[!NOTE]
>Inschakelen van de pre-productieclient of een pre-productieclient tot een productieclient promoten, uw account moet lid zijn van een beveiligingsrol die heeft **lezen** en **wijzigen** machtigingen voor de **updatepakketten** object.
>Clientupgrades voldoen aan de Configuration Manager-onderhoudsvensters die u hebt geconfigureerd.
