---
title: Windows-apparaten upgraden naar een andere versie met Configuration Manager | Microsoft Docs
description: Apparaten met Windows 10 Desktop en Windows 10 Mobile en Windows 10 Holographic naar een andere editie met Configuration Manager automatisch bijgewerkt.
ms.custom: na
ms.date: 07/31/2017
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
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: cd8c644d07dab0010dc211df8ce4f2dc6e1fa7ae
ms.contentlocale: nl-nl
ms.lasthandoff: 07/29/2017

---

# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>Windows-apparaten met het editie-Upgradebeleid in System Center Configuration Manager upgraden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


De System Center Configuration Manager **editie-Upgradebeleid** kunt u automatisch upgraden van apparaten met een van de volgende versies van Windows 10 naar een andere editie:

- Windows 10 Desktop
- Windows 10 Mobile
<!-- - Windows 10 Holographic -->

De volgende upgradepaden worden ondersteund:

- Van Windows 10 Pro naar Windows 10 Enterprise
- Van Windows 10 thuis naar Windows 10 Education
- Van Windows 10 Mobile voor Windows 10 Mobile Enterprise
<!-- - From Windows 10 Holographic Pro to Windows 10 Holographic Enterprise -->

De apparaten moeten worden geregistreerd bij Microsoft Intune of de Configuration Manager-clientsoftware wordt uitgevoerd. Dit beleid is momenteel niet compatibel met pc's die worden beheerd door lokale MDM.

## <a name="before-you-start"></a>Voordat u begint  
 Voordat u begint met het upgraden van apparaten naar de nieuwste versie, hebt u een van de volgende items nodig:  

-   Een productcode die geldig is voor het installeren van de nieuwe versie van Windows op alle apparaten waarop het beleid is gericht (voor desktopbesturingssystemen)  

-   Een licentiebestand van Microsoft die de licentiegegevens voor het installeren van de nieuwe versie van Windows op alle apparaten bevat die u met het beleid gericht (voor Windows 10 Mobile<!-- and Windows 10 Holographic-->).

- Als u wilt maken en implementeren van dit beleidstype, u moet zijn toegewezen met de Configuration Manager **volledige beheerder** beveiligingsrol.

## <a name="configure-the-edition-upgrade-policy"></a>Het editie-upgradebeleid configureren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Upgrade van Windows 10 Edition**.  

3.  Klik op **Editie-upgradebeleid maken** op het tabblad **Start** in de groep **Maken**.  

4.  Klik op **Beleid maken**.  

5.  Geef op de pagina **Algemeen** van de **Wizard Editie-upgradebeleid maken**de volgende informatie op:  

    -   **Naam** : geef een naam voor het editie-upgradebeleid op.  

    -   **Beschrijving** (optioneel): geef eventueel een beschrijving op voor het beleid waarmee u het kunt herkennen in de Intune-console.  

    -   **SKU-apparaat om te upgraden** - Selecteer in de vervolgkeuzelijst, selecteer de versie van Windows 10 Desktop <!-- Windows 10 Holographic,--> of Windows 10 Mobile die u wilt upgraden van de beoogde apparaten.  

    -   **Licentiegegevens** : selecteer een van de volgende opties:  

        -   **Productcode** : voer een geldige Windows 10-productcode in die wordt gebruikt om de gewenste apparaten met Windows 10-desktopbesturingssystemen te upgraden.  

            > [!NOTE]  
            >  Nadat u een beleid met een productcode hebt gemaakt, kunt u de productcode later niet meer bewerken. Dit komt doordat de code uit veiligheidsoverwegingen wordt verborgen. Als u de productcode wilt wijzigen, moet u de volledige code opnieuw invoeren.  

        -   **Licentiebestand** -Klik op **Bladeren** geldig licentiebestand in XML-indeling die wordt gebruikt voor het upgraden van apparaten selecteren die worden uitgevoerd is gericht <!--Windows 10 Holographic and -->Windows 10 Mobile-besturingssystemen.  

6.  Voltooi de wizard.  

Het nieuwe beleid wordt weergegeven in het knooppunt **Upgrade van Windows 10 Edition** van de werkruimte **Activa en naleving** .  

## <a name="deploy-the-edition-upgrade-policy"></a>Het editie-upgradebeleid implementeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Upgrade van Windows 10 Edition**.  

3.  Selecteer het editie-upgradebeleid voor Windows 10 dat u wilt implementeren en klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

4.  In de **implementeren Windows 10-editie-Upgrade** dialoogvenster vak, kiest u de verzameling waarnaar u implementeren van het beleid en de planning waarmee het beleid wordt geëvalueerd wilt, en klik vervolgens op **OK**. Voor pc's die worden beheerd met Configuration Manager-client, moet u het beleid implementeren voor een apparatenverzameling. Voor pc's die zijn ingeschreven met Intune, kunt u het beleid implementeren voor een gebruiker of een apparatenverzameling. 



## <a name="next-steps"></a>Volgende stappen

Wanneer u bij het bewaken van de implementatie die u zojuist hebt gemaakt in de **implementaties** knooppunt van de **bewaking** werkruimte, ziet u mogelijk fouten die wijzen op de implementatie is niet gelukt zoals:
- **Niet van toepassing voor dit apparaat**
- **Kan geen conversie van gegevenstype**

Deze fouten betekenen niet dat de implementatie is mislukt. Controleer of op de doel-PC de upgrade is uitgevoerd.

Als het beleid voor een bepaalde Windows-computer bereikt en wordt geëvalueerd, wordt deze opnieuw gestart binnen twee uur de upgrade toe te passen. Zorg ervoor dat u informeren over alle gebruikers waarop u het beleid implementeert, of het beleid wordt uitgevoerd buiten de gebruikers plannen werkuren.

