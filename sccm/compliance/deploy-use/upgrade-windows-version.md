---
title: Windows-apparaten een upgrade uitvoert naar een andere versie met Configuration Manager | Microsoft-documenten
description: Apparaten met Windows 10 Mobile, Windows 10 Mobile of Windows 10 Holographic naar een andere editie met Configuration Manager automatisch bijwerken.
ms.custom: na
ms.date: 04/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: cfde0a43947013bbd3a1093688cee19fe309fd03
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>Upgrade van Windows-apparaten met het beleid voor editie upgrade in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


De System Center Configuration Manager **Edition Upgrade beleid** kunt u automatisch upgrade apparaten met een van de volgende versies van Windows 10 naar een andere editie:

- Windows 10 Desktop
- Windows 10 Mobile
- Windows 10 Holographic

De volgende upgradepaden worden ondersteund:

- Van Windows 10 Pro voor Windows 10 Enterprise
- Windows 10 thuis Windows 10 onderwijs
- Van Windows 10 Mobile voor Windows 10 Mobile Enterprise
- Van Windows 10 Holographic Pro voor Windows 10 Holographic Enterprise

De apparaten die zijn ingeschreven bij Microsoft Intune of de Configuration Manager-clientsoftware. Dit beleid is momenteel niet compatibel met pc's die worden beheerd door MDM op locatie

## <a name="before-you-start"></a>Voordat u begint  
 Voordat u begint met het upgraden van apparaten naar de nieuwste versie, hebt u een van de volgende items nodig:  

-   Een productcode die geldig is voor het installeren van de nieuwe versie van Windows op alle apparaten waarop het beleid is gericht (voor desktopbesturingssystemen)  

-   Een licentiebestand van Microsoft met de licentiegegevens voor het installeren van de nieuwe versie van Windows op alle apparaten waarop het beleid is gericht (voor Windows 10 Mobile en Windows 10 Holographic).

- Als u wilt maken en implementeren van dit beleidstype, u moet zijn toegewezen met de Configuration Manager **volledige beheerder** beveiligingsrol is toegekend.

## <a name="configure-the-edition-upgrade-policy"></a>Het editie-upgradebeleid configureren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **compatibiliteitsinstellingen** > **Windows 10 Edition Upgrade**.  

3.  Klik op **Editie-upgradebeleid maken** op het tabblad **Start** in de groep **Maken**.  

4.  Klik op **Beleid maken**.  

5.  Geef op de pagina **Algemeen** van de **Wizard Editie-upgradebeleid maken**de volgende informatie op:  

    -   **Naam** : geef een naam voor het editie-upgradebeleid op.  

    -   **Beschrijving** (optioneel): geef eventueel een beschrijving op voor het beleid waarmee u het kunt herkennen in de Intune-console.  

    -   **SKU om het apparaat bij te werken naar** : selecteer in de vervolgkeuzelijst de versie van Windows 10 Desktop, Windows 10 Holographic of Windows 10 Mobile waarnaar u de apparaten uit de doelgroep wilt bijwerken.  

    -   **Licentiegegevens** : selecteer een van de volgende opties:  

        -   **Productcode** : voer een geldige Windows 10-productcode in die wordt gebruikt om de gewenste apparaten met Windows 10-desktopbesturingssystemen te upgraden.  

            > [!NOTE]  
            >  Nadat u een beleid met een productcode hebt gemaakt, kunt u de productcode later niet meer bewerken. Dit komt doordat de code uit veiligheidsoverwegingen wordt verborgen. Als u de productcode wilt wijzigen, moet u de volledige code opnieuw invoeren.  

        -   **Licentiebestand** : klik op **Bladeren** om een geldig licentiebestand in XML-indeling te selecteren dat wordt gebruikt om de apparaten uit de doelgroep te upgraden waarop Windows 10 Holographic- en Windows 10 Mobile-besturingssystemen worden uitgevoerd.  

6.  Voltooi de wizard.  

Het nieuwe beleid wordt weergegeven in het knooppunt **Upgrade van Windows 10 Edition** van de werkruimte **Activa en naleving** .  

## <a name="deploy-the-edition-upgrade-policy"></a>Het editie-upgradebeleid implementeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **compatibiliteitsinstellingen** > **Windows 10 Edition Upgrade**.  

3.  Selecteer het editie-upgradebeleid voor Windows 10 dat u wilt implementeren en klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

4.  In de **implementeren Windows 10 Edition Upgrade** dialoogvenster kiest u de verzameling waarnaar u wilt implementeren van het beleid en het schema waarmee het beleid wordt geëvalueerd en klik vervolgens op **OK**. Voor pc's die worden beheerd met de Configuration Manager-client, moet u het beleid implementeren voor een apparatenverzameling. Voor pc's die zijn ingeschreven met Intune, kunt u het beleid implementeren op een gebruikers- of apparaatverzameling. 

U kunt de implementatie die u zojuist hebt gemaakt, controleren vanaf het knooppunt **Implementaties** van de werkruimte **Bewaking** .  

 Als het beleid voor een bepaalde Windows-computer bereikt en wordt geëvalueerd, wordt deze opnieuw gestart binnen twee uur om toe te passen van de upgrade. Zorg ervoor dat u informeren over alle gebruikers waarvoor u het beleid implementeert, of het beleid om uit te voeren buiten de gebruikers plannen werkuren.

