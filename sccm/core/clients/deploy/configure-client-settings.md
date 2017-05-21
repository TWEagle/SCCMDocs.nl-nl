---
title: Configureren van clientinstellingen | Microsoft-documenten
description: Selecteer clientinstellingen in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 478d562bfb7fdb3921a4278741ff096e81e6092a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Clientinstellingen configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U beheert alle clientinstellingen in System Center Configuration Manager uit **beheer** > **clientinstellingen**. Wijzig de standaardinstellingen wanneer u de instellingen wilt configureren voor alle gebruikers en apparaten in de hiërarchie waarop geen aangepaste instellingen worden toegepast. Als u verschillende instellingen wilt toepassen voor slechts enkele gebruikers of apparaten, maakt u aangepaste instellingen en implementeert u deze in verzamelingen.  

Zie voor meer informatie over iedere clientinstelling [over clientinstellingen in System Center Configuration Manager](../../../core/clients/deploy/about-client-settings.md).

> [!NOTE]  
>  U kunt ook configuratie-items gebruiken om clients te beheren voor het beoordelen, bijhouden en herstellen van de configuratienaleving van apparaten. Zie voor meer informatie [Controleer apparaatcompatibiliteit met System Center Configuration Manager](../../../compliance/understand/ensure-device-compliance.md).  

##  <a name="configure-the-default-client-settings"></a>De standaardclientinstellingen configureren    

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

3.  Op de **Start** Kies **eigenschappen**.  

4.  Geef de clientinstellingen voor iedere instellingengroep in het navigatiedeelvenster weer en configureer deze.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Zie voor het initiëren van ophaalbeleid voor één client [ophalen van beleid initiëren voor een Configuration Manager-Client](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) in [in System Center Configuration Manager-clients beheren](../../../core/clients/manage/manage-clients.md).  

##  <a name="create-and-deploy-custom-client-settings"></a>Maken en implementeren van aangepaste clientinstellingen  
Wanneer u deze aangepaste instellingen implementeert, overschrijven ze de standaardclientinstellingen. Controleer voordat u met deze procedure begint of u een verzameling hebt die gebruikers of apparaten bevat waarvoor deze aangepaste clientinstellingen nodig zijn.  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **aangepaste clientinstellingen maken**, en selecteer vervolgens een:  

    -   **Aangepaste clientapparaatinstellingen maken**  

    -   **Aangepaste clientgebruikersinstellingen maken**  

4.  Geef een unieke naam en de optie beschrijving.  

5.  Selecteer een of meer van de selectievakjes in die een instellingengroep weergeven.  

6.  Kies iedere instellingengroep in het navigatiedeelvenster en configureer de beschikbare instellingen en klik vervolgens op **OK**.   

8.  Selecteer de aangepaste clientinstelling die u hebt gemaakt. Op de **Start** tabblad, in de **clientinstellingen** groep, kiest u **implementeren**.  

9. In de **verzameling selecteren** in het dialoogvenster selecteert u de juiste verzameling en kies vervolgens **OK**. U kunt de geselecteerde verzameling controleren door te klikken op het tabblad **Implementaties** in het detailvenster.  

10. Geef de volgorde weer van de aangepaste clientinstelling die u zojuist hebt gemaakt. Wanneer u meerdere aangepaste clientinstellingen hebt, worden deze toegepast volgens hun volgordenummer. Als er conflicten zijn, heft de instelling met het laagste volgordenummer de andere stellingen op. De als volgordenummer wilt wijzigen, op de **Start** tabblad, in de **clientinstellingen** groep, kiest u **Item omhoog verplaatsen** of **Item omlaag verplaatsen**.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Zie voor het initiëren van ophaalbeleid voor één client [ophalen van beleid initiëren voor een Configuration Manager-Client](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) in [in System Center Configuration Manager-clients beheren](../../../core/clients/manage/manage-clients.md).  

##  <a name="view-client-settings"></a>Client-instellingen weergeven  
 Wanneer er meerdere clientinstellingen zijn geïmplementeerd voor hetzelfde apparaat, dezelfde gebruiker of dezelfde gebruikersgroep, kan de prioriteitsaanduiding en combinatie van instellingen erg complex zijn. Instellingen voor de client weergeven:  

1.  Kies in de Configuration Manager-console **activa en naleving** > **apparaten** > **gebruikers** of **Gebruikersverzamelingen**.  

3.  Selecteer een apparaat, gebruiker of gebruikersgroep en selecteer **Resulterende clientinstellingen** in de groep **Clientinstellingen**.  

4.  Een clientinstelling selecteert in het linkerdeelvenster en de instellingen worden weergegeven. In deze weergave worden de instellingen zijn alleen-lezen. 

    > [!NOTE]  
    >  Als u wilt weergeven van de clientinstellingen, moet u leestoegang hebben voor clientinstellingen.  

    
