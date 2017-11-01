---
title: 'Apparaten inschrijven met apparaatregistratiebeheer '
titleSuffix: Configuration Manager
description: Inschrijven van apparaten in Bedrijfseigendom met de apparaatinschrijvingsbeheerder-account met System Center Configuration Manager.
ms.custom: na
ms.date: 09/08/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2905f26e-7859-497d-b995-5ff48261efa2
caps.latest.revision: "8"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: edfda4c65ac42c228b80015653678af0dbad8da3
ms.sourcegitcommit: 1132886e07d0c0a87dcc7eeef4577dd8d8840023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/01/2017
---
# <a name="enroll-devices-with-device-enrollment-manager-with-configuration-manager"></a>Apparaten inschrijven met apparaatregistratiebeheer met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Organisaties kunnen Intune gebruiken voor het beheren van grote aantallen mobiele apparaten met één gebruikersaccount. De *apparaatinschrijvingsmanager* (DEM)-account is een speciaal gebruikersaccount gebruikt om apparaten te registreren. U kunt bestaande gebruikers toevoegen aan de DEM-account te geven de speciale DEM-mogelijkheden. Elke ingeschreven apparaat maakt gebruik van één licentie. Het is raadzaam dat u apparaten die via dit account als gedeelde apparaten zonder gebruikersaffiniteit worden ingeschreven, in plaats van persoonlijke, specifieke apparaten.  

## <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager"></a>Registreren van apparaten in Bedrijfseigendom met de apparaatinschrijvingsbeheerder  
 U kunt een winkelmanager of supervisor, bijvoorbeeld een apparaatinschrijvingsmanager toewijzen gebruikersaccount waarmee ze het volgende doen:  

-   Maximaal 1000 apparaten inschrijven voor beheer  
-   De app bedrijfsportal gebruiken voor het installeren van bedrijfsapps  
-   Configureer de toegang tot bedrijfsgegevens  

De volgende beperkingen zijn van toepassing op apparaten die worden beheerd met behulp van een apparaatinschrijvingsbeheerder-account:

- De winkelmanager kan niet opnieuw instellen van het apparaat uit de bedrijfsportal.  
- Apparaten kunnen niet worden toegevoegd aan de werkplek of die lid zijn van Azure Active Directory. Dit voorkomt dat deze apparaten met behulp van voorwaardelijke toegang.
-  Om te implementeren bedrijfs-apps op apparaten die worden beheerd met de apparaatinschrijvingsbeheerder, implementeert u bedrijfsportal-app als een **vereiste installatie** aan de apparaatinschrijvingsbeheerder-gebruikersaccount. De apparaatinschrijvingsbeheerder kunt start vervolgens de bedrijfsportal-app om aanvullende apps te installeren.
- Om prestaties te verbeteren, worden de bedrijfsportal-app alleen het lokale apparaat weergegeven. Extern beheer van andere DEM-apparaten kan alleen worden uitgevoerd vanuit de Configuration Manager-console door en de beheerder
- De bedrijfsportal-website is niet beschikbaar voor de apparaatinschrijvingsbeheerder-accounts. De bedrijfsportal-app gebruiken.
- Als u iOS-apparaten inschrijven met DEM, kunt u de Apple Configurator of Apple Device Enrollment Program (DEP) niet gebruiken om apparaten te registreren. (alleen iOS) 

 **Voorbeelden van scenario voor apparaatinschrijvingsbeheerder:**   
Een restaurant wil verkooppunt-tablets voor het bedieningspersoneel en bestellingsmonitors voor het keukenpersoneel. De werknemers moeten nooit toegang tot bedrijfsgegevens, of als een gebruiker aan te melden. De Intune-beheerder maakt een apparaatinschrijvingsbeheerder-account en schrijft de eigendom van het bedrijf met behulp van dat account. U kunt ook de beheerder kan geven inschrijving van het apparaat inschrijvingsbeheerreferenties voor een Restaurantmanager, zodat hij of zij inschrijven en beheren van apparaten.  

 De beheerder of manager kunt rolspecifieke apps implementeren naar apparaten restaurant. Een beheerder kan ook een apparaat selecteert in de console en het beheer van mobiele apparaten buiten gebruik stellen.  

#### <a name="add-a-device-enrollment-manager"></a>Een apparaatinschrijvingsmanager toevoegen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw in de werkruimte **Beheer** het knooppunt **Cloud Services** uit en klik op **Microsoft Intune-abonnementen**. Selecteer het Microsoft Intune-abonnement waarnaar u een apparaatinschrijvingsmanager toevoegt, en klik vervolgens op **eigenschappen**.  

3.  Klik in het dialoogvenster Eigenschappen van Microsoft Intune-abonnement op de **Apparaatinschrijvingsmanager** tabblad.  

4.  Klik op **toevoegen of verwijderen**.  

5.  In de **Apparaatinschrijvingsmanager** dialoogvenster, typ de gebruikersnaam van de gebruiker die u wilt toevoegen als apparaatinschrijvingsmanager en klik vervolgens op **Search**. Selecteer de gebruiker die u wilt toevoegen als Apparaatinschrijvingsmanager en klik op **toevoegen**.  

6.  Het gebruikersaccount dat apparaatinschrijvingsmanager en klik op bevestigen **toevoegen/verwijderen**.  Er is een abonnementslicentie vereist voor elke gebruiker die toegang heeft tot de service en de *apparaatinschrijvingsmanager* mag geen Intune-beheerder. Bepaal of u meer licenties toevoegen wilt voordat u deze functie gebruiken.  

7.  De apparaatinschrijvingsbeheerder kan nu inschrijven van mobiele apparaten met dezelfde procedure als die een eindgebruiker voor een scenario bring-your-own-device (BYOD) in de bedrijfsportal gebruikt.  

#### <a name="delete-a-device-enrollment-manager-from-intune"></a>Een apparaatinschrijvingsbeheerder uit Intune verwijderen  
Als u een apparaatinschrijvingsmanager verwijdert, heeft dit geen invloed op de ingeschreven apparaten. Wanneer een apparaatinschrijvingsmanager is verwijderd:  
- Er is geen geregistreerde apparaten zijn geregistreerd  
- Blijven ingeschreven apparaten volledig beheerd  
- De accountreferenties van verwijderde apparaatinschrijvingsbeheerder blijven geldig voor aanmelding bij de bedrijfsportal toegang tot apps  
- De verwijderde apparaatinschrijvingsbeheerder accountreferenties nog steeds niet wissen of buiten gebruik stellen van apparaten  
- De verwijderde apparaatinschrijvingsbeheerder-account van de relatie met ingeschreven apparaten blijft, maar er zijn geen extra apparaten kunnen worden ingeschreven.

1.  Klik op **Beheer**in de Configuration Manager-console.  
2.  Vouw in de werkruimte **Beheer** het knooppunt **Cloud Services** uit en klik op **Microsoft Intune-abonnementen**. Selecteer het Microsoft Intune-abonnement waarnaar u een apparaatinschrijvingsmanager toevoegt, en klik vervolgens op **eigenschappen**.  
3.  Klik in het dialoogvenster Eigenschappen van Microsoft Intune-abonnement op de **Apparaatinschrijvingsmanager** tabblad.  
4.  **Search** voor de apparaatinschrijvingsmanager die u wilt verwijderen en klik op **verwijderen**, klikt u vervolgens **OK**.  
