---
title: Windows-apparaten upgraden naar een andere versie
titleSuffix: Configuration Manager
description: Automatisch upgraden van apparaten met Windows 10 Desktop- of Windows 10 Mobile naar een andere editie met Configuration Manager.
ms.custom: na
ms.date: 01/26/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
caps.latest.revision: 
caps.handback.revision: 
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 95e3385ad9bca9c87e48d731ffeebfa387fece65
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>Windows-apparaten met het editie-Upgradebeleid in System Center Configuration Manager upgraden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


De **editie-Upgradebeleid** kunt u automatisch upgraden van apparaten met een van de volgende versies van Windows 10 naar een andere editie:

- Windows 10 Desktop
- Windows 10 Mobile

De volgende upgradepaden worden ondersteund:

- Van Windows 10 Pro naar Windows 10 Enterprise
- Van Windows 10 thuis naar Windows 10 Education
- Van Windows 10 Mobile voor Windows 10 Mobile Enterprise

De apparaten moeten worden geregistreerd bij Microsoft Intune of de Configuration Manager-clientsoftware wordt uitgevoerd. Dit beleid is momenteel niet compatibel met pc's die worden beheerd door lokale MDM.

## <a name="before-you-start"></a>Voordat u begint  
 Voordat u begint met het upgraden van apparaten naar de nieuwste versie, controleert u de volgende vereisten:  

-   Voor bureaublad edities van Windows 10: Een geldige productcode voor de nieuwe versie van Windows op alle apparaten waarop het beleid is gericht. Deze productcode is een meervoudige activeringscode (MAK), of een generic volume licensing-sleutel (GVLK). Een GVLK wordt ook een clientinstallatiecode key management service (KMS) genoemd. Zie voor meer informatie [volumeactivering plannen](https://docs.microsoft.com/windows/deployment/volume-activation/plan-for-volume-activation-client). Zie voor een lijst met installatiecodes voor KMS-client, [bijlage A](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys) van de handleiding van Windows Server-activering. <!--496871-->  

-   Voor Windows 10 Mobile: Een licentie XML-bestand van de Microsoft Volume Licensing Service Center (VLSC). Dit bestand bevat de licentiegegevens voor de nieuwe versie van Windows op alle apparaten waarop het beleid is gericht.

- Voor het beheren van dit beleidstype, moet u in de Configuration Manager **volledige beheerder** beveiligingsrol.

## <a name="configure-the-edition-upgrade-policy"></a>Het editie-upgradebeleid configureren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Upgrade van Windows 10 Edition**.  

3.  Klik op **Editie-upgradebeleid maken** op het tabblad **Start** in de groep **Maken**.  

4.  Klik op **Beleid maken**.  

5.  Geef op de pagina **Algemeen** van de **Wizard Editie-upgradebeleid maken**de volgende informatie op:  

    -   **Naam** -Voer een naam voor de editie-Upgradebeleid  

    -   **Beschrijving** (optioneel) - eventueel een beschrijving invoeren voor het beleid dat u het kunt herkennen in de Intune-beheerconsole  

    -   **SKU-apparaat om te upgraden** - Selecteer in de vervolgkeuzelijst, selecteer de doeleditie van Windows 10 desktop en Windows 10 Mobile  

    -   **Licentiegegevens** : selecteer een van de volgende opties:  

        -   **Productcode** -Voer een geldige productsleutel voor de doel Windows 10 desktop-editie  

            > [!NOTE]  
            >  Nadat u een beleid met een productcode hebt gemaakt, kunt u de productcode later niet meer bewerken. Configuration Manager geven de sleutel uit veiligheidsoverwegingen. Als u de productcode wilt wijzigen, moet u de volledige code opnieuw invoeren.  

        -   **Licentiebestand** -Klik op **Bladeren** selecteren van een geldig licentiebestand in XML-indeling. Configuration Manager gebruikt deze licentiebestand voor het upgraden van Windows 10 Mobile-apparaten.  

6.  Voltooi de wizard.  


## <a name="deploy-the-edition-upgrade-policy"></a>Het editie-upgradebeleid implementeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Upgrade van Windows 10 Edition**.  

3.  Selecteer het editie-upgradebeleid voor Windows 10 dat u wilt implementeren en klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

4.  In de **implementeren Windows 10-editie-Upgrade** dialoogvenster vak, kiest u eerst de verzameling waarnaar u wilt het beleid implementeren. Selecteer de planning op waarmee de client het beleid evalueert en klik vervolgens op **OK**. Voor pc's die worden beheerd met Configuration Manager-client, moet u het beleid implementeren voor een apparatenverzameling. Voor pc's die zijn ingeschreven met Intune, kunt u het beleid implementeren voor een gebruiker of een apparatenverzameling. 



## <a name="next-steps"></a>Volgende stappen

Bewaken van deze implementatie van de **implementaties** knooppunt van de **bewaking** werkruimte. Als u fouten die aangeven een mislukte implementatie, bijvoorbeeld ziet:
- **Niet van toepassing voor dit apparaat**
- **Kan geen conversie van gegevenstype**

Deze fouten betekenen niet dat de implementatie is mislukt. Controleer of op de doel-PC de upgrade is uitgevoerd.

Nadat de client het betreffende beleid evalueert, wordt deze binnen twee uur om toe te passen van de upgrade opnieuw. Zorg ervoor dat u informeren over alle gebruikers waarop u het beleid implementeert, of het beleid wordt uitgevoerd buiten de gebruikers plannen werkuren.

Als u de volgende fout weergegeven **DcmWmiProvider.log** op de client, controleer dan of u de juiste sleutel voor uw scenario voor activering. Zie voor meer informatie de [voordat u begint met](#before-you-start) sectie. Als u van een service voor sleutelbeheer voor activering gebruikmaakt, moet u een [Installatiecode voor KMS-client](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys).  <!-- 496871 -->   

`Failed to execute CheckApplicabilityMethod with error = 0x80041001 OsEditionUpgradeProvider`
