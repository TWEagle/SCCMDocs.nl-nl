---
title: Clientinstellingen configureren
titleSuffix: Configuration Manager
description: Selecteer clientinstellingen in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: "5"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 20a8f91d10d98542f08e440bcfbc1a6f98a51932
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>Het configureren van clientinstellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U beheert alle clientinstellingen in System Center Configuration Manager uit **beheer** > **clientinstellingen**. Wijzig de standaardinstellingen wanneer u de instellingen wilt configureren voor alle gebruikers en apparaten in de hiërarchie waarop geen aangepaste instellingen worden toegepast. Als u verschillende instellingen wilt toepassen voor slechts enkele gebruikers of apparaten, maakt u aangepaste instellingen en implementeert u deze in verzamelingen.  

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

10. Geef de volgorde weer van de aangepaste clientinstelling die u zojuist hebt gemaakt. Wanneer u meerdere aangepaste clientinstellingen hebt, worden deze toegepast volgens hun volgordenummer. Als er conflicten zijn, heft de instelling met het laagste volgordenummer de andere stellingen op. De als volgordenummer wilt wijzigen, op de **Start** tabblad, in de **clientinstellingen** groep, kiest u **Item omhoog verplaatsen** of **Item omlaag verplaatsen**.  

 Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Zie voor het initiëren van het ophaalbeleid voor één client [ophalen van beleid initiëren voor een Configuration Manager-Client](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval) in [clients in System Center Configuration Manager beheren](../../../core/clients/manage/manage-clients.md).  

## <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Windows 10 verbeterde telemetrie alleen om gegevens te verzenden relevant zijn voor Windows Analytics Apparaatstatus beperken
<!-- 1356148 -->

Met de update 1710, kunt u instellen de gegevensverzameling voor Windows 10-telemetrie op **uitgebreid (beperkt)**. Deze instelling kunt u actie worden uitgevoerd om inzicht te krijgen over de apparaten in uw omgeving zonder apparaten rapportage van de gegevens in de **uitgebreid** telemetrie niveau met Windows 10 versie 1709 of hoger.

Het niveau uitgebreid (beperkt) telemetrie bevat metrische gegevens van het niveau basis, evenals een subset van gegevens verzameld van de **uitgebreid** niveau relevant zijn voor Windows Analytics. Zie voor meer informatie over telemetrie niveaus [telemetrie niveaus](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization#telemetry-levels).

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

2.  Op de **Start** Kies **eigenschappen**.  

3.  Open **Cloudservices**, en Windows 10 telemetrie ingesteld op **uitgebreid**.

##  <a name="view-client-settings"></a>Instellingen van de client weergeven  
 Wanneer er meerdere clientinstellingen zijn geïmplementeerd voor hetzelfde apparaat, dezelfde gebruiker of dezelfde gebruikersgroep, kan de prioriteitsaanduiding en combinatie van instellingen erg complex zijn. Instellingen voor de client weergeven:  

1.  Kies in de Configuration Manager-console **activa en naleving** > **apparaten** > **gebruikers** of **Gebruikersverzamelingen**.  

3.  Selecteer een apparaat, gebruiker of gebruikersgroep en selecteer **Resulterende clientinstellingen** in de groep **Clientinstellingen**.  

4.  Selecteer een client-instelling in het linkerdeelvenster en de instellingen worden weergegeven. In deze weergave worden de instellingen zijn alleen-lezen. 

    > [!NOTE]  
    >  De als clientinstellingen wilt weergeven, moet u beschikken over leestoegang voor clientinstellingen.  

    