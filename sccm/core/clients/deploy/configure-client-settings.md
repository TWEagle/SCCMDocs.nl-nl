---
title: Clientinstellingen configureren
titleSuffix: Configuration Manager
description: Selecteer clientinstellingen in System Center Configuration Manager.
ms.custom: na
ms.date: 12/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: "5"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: c777e800d154b060040363aefbc611e284f233b4
ms.sourcegitcommit: f1535281b2c3fecff773b722c3f7590bf6ba10a0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Het configureren van clientinstellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U beheert alle clientinstellingen in System Center Configuration Manager uit **beheer** > **clientinstellingen**. Wijzig de standaardinstellingen wanneer u de instellingen wilt configureren voor alle gebruikers en apparaten in de hiërarchie waarop geen aangepaste instellingen worden toegepast. Als u verschillende instellingen toepassen voor slechts enkele gebruikers of apparaten wilt, maakt u aangepaste instellingen en implementeren in verzamelingen.  

Zie voor meer informatie over iedere clientinstelling [over clientinstellingen in System Center Configuration Manager](../../../core/clients/deploy/about-client-settings.md).

> [!NOTE]  
>  U kunt ook configuratie-items gebruiken om clients te beheren voor het beoordelen, bijhouden en herstellen van de configuratienaleving van apparaten. Zie voor meer informatie [apparaatcompatibiliteit met System Center Configuration Manager garanderen](../../../compliance/understand/ensure-device-compliance.md).  

##  <a name="configure-the-default-client-settings"></a>De standaardclientinstellingen configureren    

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

3.  Op de **Start** Kies **eigenschappen**.  

4.  Geef de clientinstellingen voor iedere instellingengroep in het navigatiedeelvenster weer en configureer deze.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Zie voor het initiëren van het ophaalbeleid voor één client [ophalen van beleid initiëren voor een Configuration Manager-Client](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) in [clients in System Center Configuration Manager beheren](../../../core/clients/manage/manage-clients.md).  

##  <a name="create-and-deploy-custom-client-settings"></a>Instellingen voor aangepaste clientinstellingen maken en implementeren  
Wanneer u deze aangepaste instellingen implementeert, overschrijven ze de standaardclientinstellingen. Controleer voordat u met deze procedure begint of u een verzameling hebt die gebruikers of apparaten bevat waarvoor deze aangepaste clientinstellingen nodig zijn.  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **aangepaste clientinstellingen maken**, en kies vervolgens een:  

    -   **Aangepaste clientapparaatinstellingen maken**  

    -   **Aangepaste clientgebruikersinstellingen maken**  

4.  Geef een unieke naam en de optie-beschrijving.  

5.  Selecteer een of meer van de selectievakjes die een groep instellingen weergeven.  

6.  Elke groep instellingen kiezen in het navigatiedeelvenster en klikt u op de beschikbare instellingen configureren **OK**.   

8.  Selecteer de aangepaste clientinstelling die u hebt gemaakt. Op de **Start** tabblad, in de **clientinstellingen** groep, kiest u **implementeren**.  

9. In de **verzameling selecteren** in het dialoogvenster selecteert u de juiste verzameling en kies vervolgens **OK**. U kunt de geselecteerde verzameling controleren door te klikken op het tabblad **Implementaties** in het detailvenster.  

10. Bekijk de volgorde van de aangepaste clientinstelling die u hebt gemaakt. Wanneer u meerdere aangepaste clientinstellingen hebt, worden deze toegepast volgens hun volgordenummer. Als er conflicten zijn, heft de instelling met het laagste volgordenummer de andere stellingen op. De als volgordenummer wilt wijzigen, op de **Start** tabblad, in de **clientinstellingen** groep, kiest u **Item omhoog verplaatsen** of **Item omlaag verplaatsen**.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Zie voor het initiëren van het ophaalbeleid voor één client [ophalen van beleid initiëren voor een Configuration Manager-Client](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) in [clients in System Center Configuration Manager beheren](../../../core/clients/manage/manage-clients.md).  



##  <a name="view-client-settings"></a>Instellingen van de client weergeven  
 Wanneer u meerdere clientinstellingen voor de hetzelfde apparaat, gebruiker of gebruikersgroep implementeert, is de prioriteitsaanduiding en combinatie van instellingen complexe. Instellingen voor de client weergeven:  

1.  Kies in de Configuration Manager-console **activa en naleving** > **apparaten** > **gebruikers** of **Gebruikersverzamelingen**.  

3.  Selecteer een apparaat, gebruiker of gebruikersgroep en selecteer **Resulterende clientinstellingen** in de groep **Clientinstellingen**.  

4.  Selecteer een client-instelling in het linkerdeelvenster en de instellingen worden weergegeven. In deze weergave worden de instellingen zijn alleen-lezen. 

    > [!NOTE]  
    >  De als clientinstellingen wilt weergeven, moet u beschikken over leestoegang voor clientinstellingen.  

    