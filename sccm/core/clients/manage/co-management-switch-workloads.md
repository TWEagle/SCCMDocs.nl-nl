---
title: Configuration Manager-workloads overschakelen naar Intune
titleSuffix: System Center Configuration Manager
description: Informatie over het wijzigen van de werkbelastingen die momenteel wordt beheerd door Configuration Manager op Microsoft Intune.
ms.prod: configuration-manager
ms.suite: na
ms.technology:
- configmgr-client
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.service: ''
ms.assetid: 60e2022f-a4f9-40dd-af01-9ecb37b43878
ms.openlocfilehash: cdfe52768499b929db473ac08d42207059965ffd
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="switch-configuration-manager-workloads-to-intune"></a>Configuration Manager-workloads overschakelen naar Intune
In [voorbereiden Windows 10-apparaten voor het beheer van CO](co-management-prepare.md), u Windows 10-apparaten voor het beheer van CO voorbereid. Deze apparaten zijn toegevoegd aan AD, Azure AD, ze zijn ingeschreven bij Intune en Configuration Manager-client hebben. Hebt u waarschijnlijk nog Windows 10-apparaten die lid zijn van AD en Configuration Manager-client, maar niet toegevoegd aan Azure AD. of zijn ingeschreven in Intune. De volgende procedure bevat de stappen voor het inschakelen van CO-beheer, de rest van uw Windows 10-apparaten (Configuration Manager-clients zonder inschrijving bij Intune) voor het beheer van CO voorbereiden en kunt u starten Overschakelen van specifieke Configuration Manager werkbelastingen naar Intune.

1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices**  >  **Mede management**.    
2. Kies op het tabblad Start in de groep beheren **mede management configureren** de configuratiewizard mede management openen.    
3. Klik op de pagina abonnement **aanmelden** aanmelden bij uw Intune-tenant en klik vervolgens op **volgende**.   
4. Kies op de pagina stuk **proef** of **alle** inschakelen van automatische inschrijving bij Intune en klik vervolgens op **volgende**. Wanneer u de optie **test**, alleen de Configuration manager-clients die lid van de test-groep zijn automatisch zijn ingeschreven bij Intune. Deze optie kunt u mede beheer inschakelen voor een subset van clients te testen in eerste instantie mede beheer en mede-implementatiebeheer met behulp van een gefaseerde benadering. De opdrachtregel kan worden gebruikt voor het implementeren van Configuration Manager-client als een app in Intune voor apparaten die al zijn ingeschreven in Intune. Zie voor meer informatie [Windows 10-apparaten ingeschreven bij Intune](co-management-prepare.md#windows-10-devices-enrolled-in-intune).
5. Kies of u wilt overschakelen van Configuration Manager-workloads die worden beheerd door de test voor Intune of Intune op de pagina werkbelastingen en klik vervolgens op **volgende**. De **Intune proef** instelling verandert de bijbehorende werkbelasting alleen voor de apparaten in de test-groep. De **Intune** instelling verandert de bijbehorende werkbelasting voor alle CO beheerde Windows 10-apparaten. 
        
   > [!Important]    
   > Voordat u werkbelastingen schakelt, moet de bijbehorende werkbelasting in Intune is juist geconfigureerd en geïmplementeerd. Hiermee zorgt u ervoor dat de werkbelastingen altijd worden beheerd door een van de beheerhulpprogramma's voor uw apparaten.   
1. Configureer de volgende instellingen op de pagina fasering en klik vervolgens op **volgende**:
    - **Test**: De testgroep bevat een of meer verzamelingen die u selecteert. Deze groep gebruiken als onderdeel van uw gefaseerde implementatie van CO-beheer. U kunt beginnen met een kleine testverzameling en voeg vervolgens meer verzamelingen aan de test groep tijdens de implementatie van CO management voor meerdere gebruikers en apparaten. U kunt de verzamelingen in de testgroep op elk gewenst moment de collega beheereigenschappen wijzigen.
    - **Productie**: Configureer de **uitsluiting groep** met een of meer verzamelingen. Apparaten die lid van een van de collecties in deze groep zijn worden uitgesloten van met CO-beheer. 
2. Mede als beheer wilt inschakelen, moet u de wizard voltooien.  

## <a name="modify-your-co-management-settings"></a>Uw collega management-instellingen wijzigen
Nadat u mede-beheer met de wizard inschakelen, kunt u de instellingen in de collega beheereigenschappen wijzigen.  
- Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices**  >  **Mede management**.  
Selecteer het mede management-object en klik op het tabblad Start **eigenschappen**. 

## <a name="workloads-able-to-be-transitioned-to-intune"></a>Werkbelastingen kunnen worden overgezet naar Intune
Bepaalde werkbelastingen zijn beschikbaar via worden overgeschakeld naar Intune. De volgende lijst wordt bijgewerkt als de werkbelasting beschikbaar is om over te gaan:
1. Nalevingsbeleid voor apparaten
2. Resource-beleid
3. Windows Update-beleid
4. Endpoint Protection (te beginnen in Configuration Manager versie 1802)
      - Windows Defender Antivirus
      - Windows Defender toepassing Guard
      - Windows Defender-Firewall
      - Windows Defender SmartScreen
      - Windows-versleuteling
      - Windows Defender misbruik Guard
      - Windows Defender Toepassingsbeheer
      - Windows Defender Security Center
      - Windows Defender Advanced Threat Protection



## <a name="monitor-co-management"></a>Monitor voor CO-management
Nadat u mede-beheer inschakelen, kunt u mede management-apparaten met behulp van de volgende methoden volgen:
- **SQL weergeven en WMI-klasse**: U kunt een query de **v&#95;ClientCoManagementState** SQL-weergave in de database van de Configuration Manager-site of de **SMS&#95;Client&#95;ComanagementState** WMI-klasse. Met de informatie in de WMI-klasse, kunt u aangepaste verzamelingen maken in Configuration Manager om te bepalen van de status van uw collega management-implementatie. Zie voor meer informatie [verzamelingen maken](/sccm/core/clients/manage/collections/create-collections). De volgende velden zijn beschikbaar in de SQL-weergave en WMI-klasse: 
    - **MachineId**: Hiermee geeft u een unieke apparaat-ID voor de Configuration Manager-client.
    - **MDMEnrolled**: Geeft aan of het apparaat MDM geregistreerd. 
    - **Instantie**: Hiermee geeft u de instantie die het apparaat wordt ingeschreven.
    - **ComgmtPolicyPresent**: Geeft aan of de Configuration Manager-CO management-beleid op de client bestaat. Als de **MDMEnrolled** waarde is **0**, het apparaat is niet samen worden beheerd ongeacht of het mede management-beleid op de client bestaat.

   > [!Note]    
   > Een apparaat is CO beheerde wanneer de **MDMEnrolled** veld en **ComgmtPolicyPresent** waarde voor beide velden hebben **1**.

- **Implementatie van beleid**:  Er zijn twee beleidsregels die zijn gemaakt in **bewaking** > **implementaties**; één beleid voor de testgroep en één voor productie. Deze beleidsregels worden alleen het aantal apparaten waarop het beleid is toegepast in Configuration Manager rapporteren. U komt niet hoeveel apparaten zijn ingeschreven bij Intune, die is vereist voordat apparaten kunnen naast elkaar worden beheerd.  

## <a name="check-compliance-for-co-managed-devices"></a>Controleren op naleving voor naast beheerde apparaten
Gebruikers kunnen Software Center gebruiken om te controleren van de compatibiliteit van hun CO beheerde Windows 10-apparaten, ongeacht of voorwaardelijke toegang wordt beheerd door Configuration Manager of Intune. Gebruikers kunnen ook naleving controleren via de bedrijfsportal-app wanneer voorwaardelijke toegang wordt beheerd door Intune.

## <a name="next-steps"></a>Volgende stappen
Gebruik de volgende bronnen voor het beheren van de werkbelastingen die u naar Intune overschakelt:
- [Nalevingsbeleid voor apparaten](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Resource-beleid](https://docs.microsoft.com/intune/device-profiles)
- [Windows Update voor bedrijven-beleid](https://docs.microsoft.com/intune/windows-update-for-business-configure)
- [Endpoint Protection voor Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
