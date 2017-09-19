---
title: 'Algemene naleving beheertaken voor Configuration Manager-client-beheerde apparaten: | Microsoft Docs'
description: Meer informatie over System Center Configuration Manager-instellingen voor naleving door het uitvoeren van enkele algemene scenario's.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e345791-74db-41ad-b472-024ce6521daf
caps.latest.revision: "8"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 84b030284602853aab6c99268a74444a693edec7
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="common-tasks-for-managing-compliance-on-devices-with-the-system-center-configuration-manager-client"></a>Algemene taken voor het beheren van naleving op apparaten met System Center Configuration Manager-client

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De scenario's in dit onderwerp krijgt u een inleiding tot het gebruik van System Center Configuration Manager-instellingen voor naleving door het uitvoeren van enkele algemene scenario's die u kunt tegenkomen.  

 Als u al bekend met instellingen voor naleving bent, gedetailleerde documentatie over functies die u gebruikt kan worden gevonden in de [configuratie-items voor apparaten die worden beheerd door de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md) sectie.  

 Lees voordat u begint, [aan de slag met instellingen voor naleving](../../compliance/get-started/get-started-with-compliance-settings.md) basisinformatie over de instellingen voor naleving en ook lezen [plannen en configureren van instellingen voor naleving](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) voor het implementeren van alle benodigde voorwaarden.  

## <a name="general-information-for-each-scenario"></a>Algemene informatie voor elk scenario  
 In elk scenario maakt u een configuratie-item waarmee een specifieke taak wordt uitgevoerd. Open de wizard Configuratie-item maken en voer de volgende stappen uit:  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **configuratie-Items**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  

4.  Geef op het tabblad **Algemeen** van de wizard Configuratie-item maken een naam en beschrijving op voor het configuratie-item, zoals hieronder wordt weergegeven. Kies vervolgens het juiste configuratie-itemtype voor elk scenario in dit onderwerp.  

     ![Pagina Algemeen van de configuratiewizard-item bevat.](/sccm/compliance/plan-design/media/Compliance-Settings-Wizard---1.png)  

## <a name="scenarios-for-windows-10-devices-managed-with-the-configuration-manager-client"></a>Scenario's voor Windows 10-apparaten die worden beheerd met de Configuration Manager-client  

### <a name="scenario-disable-the-use-of-bluetooth-on-windows-10-devices"></a>Scenario: Het gebruik van Bluetooth op Windows 10-apparaten uitschakelen  
 In dit scenario heeft uw beveiligingsafdeling vastgesteld dat de Bluetooth-mogelijkheden op apparaten kunnen worden gebruikt om vertrouwelijke bedrijfsinformatie buiten het bedrijf te verzenden. U hebt al uw pc's onlangs bijgewerkt naar Windows 10 en besloten de Bluetooth-functie op deze apparaten uit te schakelen.  

1.  Selecteer op de pagina **Algemeen** van de wizard Configuratie-item maken het configuratie-itemtype **Windows 10** en klik vervolgens op **Volgende**.  

2.  Selecteer op de pagina **Ondersteunde platforms** van de wizard alle Windows 10-platforms.  

3.  Selecteer op de pagina **Apparaatinstellingen** de optie **Apparaat**en klik vervolgens op **Volgende**.  

4.  Selecteer op de pagina **Apparaat** de optie **Niet toegestaan** als waarde voor **Bluetooth**.  

5.  Selecteer **Niet-compliante instellingen herstellen** om ervoor te zorgen dat de wijziging wordt toegepast op alle Windows 10-apparaten.  

6.  Voltooi de wizard om het configuratie-item te maken.  

 U kunt nu de informatie in de [algemene taken voor het maken en implementeren van configuratiebasislijnen met System Center Configuration Manager](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) onderwerp waarmee u de configuratie die u hebt gemaakt op apparaten implementeren.  

## <a name="scenarios-for-windows-desktop-and-server-computers-managed-with-the-configuration-manager-client"></a>Scenario's voor Windows desktop- en servercomputers die worden beheerd met de Configuration Manager-client  
 Op Mac-computers waarop de Configuration Manager-client wordt uitgevoerd, hebt u twee opties voor de beoordeling van naleving:  

-   Een bestand met Mac OS X-voorkeuren (PLIST-bestand) evalueren.  

-   Een aangepast script gebruiken en de geretourneerde resultaten evalueren.  

 Zie voor meer informatie [het maken van configuratie-items voor Mac OS X-apparaten worden beheerd met de System Center Configuration Manager-client](../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md).  

### <a name="scenario-remediate-an-incorrect-registry-value-on-windows-desktop-computers"></a>Scenario: Een onjuiste registersleutel op Windows-desktopcomputers herstellen  
 In dit scenario ontdekt u dat een belangrijke Line-Of-Business-app niet goed wordt uitgevoerd op bepaalde computers die u beheert en waarop Windows 8.1 wordt uitgevoerd. Na onderzoek ontdekt u dat dit is omdat een registersleutel met de naam **HKEY_LOCAL_MACHINE\SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1** op sommige computers is ingesteld op de waarde **0** . Voor een goede uitvoer van de Line-Of-Business-app moet deze waarde zijn ingesteld op **1**.  

 In deze procedure maakt u een configuratie-item dat controleert op onjuiste registersleutelwaarden en deze automatisch herstelt.  

1.  Selecteer op de pagina **Algemeen** van de wizard Configuratie-item maken het configuratie-itemtype **Windows-desktops en -servers** en klik vervolgens op **Volgende**.  

2.  Selecteer op de pagina **Ondersteunde platforms** van de wizard de optie **Windows 8.1** (om ervoor te zorgen dat het configuratie-item alleen van toepassing is op de betreffende computers).  

3.  Klik op de pagina **Instellingen** op **Nieuw** om een nieuwe instelling te maken.  

4.  Configureer op het tabblad **Algemeen** van het dialoogvenster **Instelling maken** het volgende:  

    -   **Naam** > **Voorbeeldinstelling**  

    -   **Instellingstype** > **Registerwaarde**  

    -   **Gegevenstype** > **Geheel getal** (de waarde bevat alleen een getal)  

    -   **Component** > **HKEY_LOCAL_MACHINE**  

    -   **Sleutel** > **SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1**  

    -   **Waarde** > **1** (de vereiste waarde)  

5.  Klik op het tabblad **Compliantieregels** van het dialoogvenster **Instelling maken** op **Nieuw**en configureer in het dialoogvenster **Regel maken** het volgende:  

    -   **Naam** > **Voorbeeldregel**  

    -   **Geselecteerde instelling** : controleer of de instelling **Voorbeeldinstelling**is geselecteerd.  

    -   **Regeltype** > **Waarde**  

    -   **De instelling moet voldoen aan de volgende regel** : controleer of de naam van de instelling correct is en configureer de optie zodanig dat de waarde van de instelling gelijk is aan **1**.  

    -   **Herstellen, waar ondersteund** : Schakel dit selectievakje in om ervoor te zorgen dat Configuration Manager wordt opnieuw ingesteld registersleutelwaarde terugzet op de juiste waarde als dit onjuist is.  

6.  Voltooi de wizard om het configuratie-item te maken.  

 U kunt nu de informatie in de [algemene taken voor het maken en implementeren van configuratiebasislijnen](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) onderwerp waarmee u de configuratie die u hebt gemaakt op apparaten implementeren.  
