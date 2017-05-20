---
title: Apparaten inschrijven met de apparaatinschrijvingsbeheerder - Configuration Manager | Microsoft-documenten
description: Bedrijfseigendom apparaten inschrijven met de apparaatinschrijvingsbeheerder-account met System Center Configuration Manager.
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2905f26e-7859-497d-b995-5ff48261efa2
caps.latest.revision: 8
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7573590763c68a4c97d388be1e64054c318da9cc
ms.openlocfilehash: 8c491636925670732e6af67d8c1c741e4793ef96
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-devices-with-device-enrollment-manager-with-configuration-manager"></a>Apparaten inschrijven met de apparaatinschrijvingsbeheerder met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Organisaties kunnen Intune gebruiken voor het beheren van grote aantallen mobiele apparaten met één gebruikersaccount. De *apparaatinschrijvingsbeheerder* (DEM)-account is een speciaal gebruikersaccount die maximaal 1000 apparaten kan registreren. U toevoegen bestaande gebruikers aan het account DEM om hem de speciale DEM mogelijkheden. Elke ingeschreven apparaat maakt gebruik van één licentie. U wordt aangeraden dat u gebruikt apparaten zijn ingeschreven via dit account als gedeelde apparaten geen affiniteit tussen gebruikers en in plaats van persoonlijke, specifieke apparaten.  

## <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager"></a>Apparaten met de apparaatinschrijvingsbeheerder in Bedrijfseigendom inschrijven  
 U kunt een winkelmanager of supervisor, bijvoorbeeld een apparaatinschrijvingsbeheerder toewijzen gebruikersaccount te kunnen het volgende doen:  

-   Maximaal 1000 apparaten inschrijven voor beheer  
-   De bedrijfsportal-app gebruiken voor het installeren van bedrijfsapps  
-   Toegang tot bedrijfsgegevens configureren  

De volgende beperkingen zijn van toepassing op apparaten die worden beheerd met behulp van een apparaatinschrijvingsbeheerder-account:

- De winkelmanager kan het apparaat via de bedrijfsportal niet opnieuw instellen.  
- Apparaten kunnen niet worden toegevoegd aan de werkplek of lid zijn van Azure Active Directory. Dit voorkomt dat deze apparaten met behulp van voorwaardelijke toegang.
-  Voor de implementatie van bedrijfs-apps op apparaten die worden beheerd met de apparaatinschrijvingsbeheerder implementeren bedrijfsportal-app als een **vereiste installatie** aan de apparaatinschrijvingsbeheerder-gebruikersaccount. De apparaatinschrijvingsbeheerder kan start vervolgens de bedrijfsportal-app om extra apps te installeren.
- Om prestaties te verbeteren, de bedrijfsportal-app bevat alleen het lokale apparaat. Extern beheer van andere apparaten DEM kan alleen worden uitgevoerd vanaf de Configuration Manager-console door en de beheerder
- De bedrijfsportal-website is niet beschikbaar voor de apparaatinschrijvingsbeheerder-accounts. De bedrijfsportal-app gebruiken.
- (alleen iOS) Als u DEM iOS-apparaten in te schrijven, kunt u de Apple Configurator of Apple Device Enrollment Program (DEP) niet gebruiken om apparaten te registreren.

 **Voorbeelden van scenario voor apparaatinschrijvingsbeheerder:**   
Een restaurant wil verkooppunt-tablets voor wacht medewerkers en volgorde-monitors voor het keukenpersoneel. De werknemers nodig nooit toegang tot bedrijfsgegevens, of om aan te melden als een gebruiker. De Intune-beheerder maakt een apparaatinschrijvingsbeheerder-account en schrijft de eigendom van het bedrijf met behulp van dat account. U kunt ook de beheerder kan de apparaatregistratie manager referenties geven aan een Restaurantmanager, zodat hij of zij inschrijven en beheren van de apparaten.  

 De beheerder of de manager kan rolspecifieke apps op de restaurantapparaten implementeren. Een beheerder kan ook een apparaat selecteert in de console en het beheer van mobiele apparaten buiten gebruik stellen.  

#### <a name="add-a-device-enrollment-manager"></a>Een apparaatinschrijvingsbeheerder toevoegen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw in de werkruimte **Beheer** het knooppunt **Cloud Services** uit en klik op **Microsoft Intune-abonnementen**. Selecteer het Microsoft Intune-abonnement waaraan u moet een apparaatinschrijvingsbeheerder toevoegen en klik op **eigenschappen**.  

3.  Klik in het dialoogvenster Eigenschappen van Microsoft Intune-abonnement op de **Apparaatinschrijvingsbeheerder** tabblad.  

4.  Klik op **toevoegen of verwijderen**.  

5.  In de **Apparaatinschrijvingsbeheerder** dialoogvenster, typ de gebruikersnaam van de gebruiker die u wilt toevoegen als een apparaatinschrijvingsbeheerder en klik vervolgens op **zoeken**. Selecteer de gebruiker die u wilt toevoegen als een Apparaatinschrijvingsbeheerder en klik op **toevoegen**.  

6.  Het gebruikersaccount dat een apparaatinschrijvingsbeheerder wordt en klik op bevestigen **toevoegen/verwijderen**.  Er is een abonnementslicentie vereist voor elke gebruiker die toegang de service en de *apparaatinschrijvingsbeheerder* mag geen Intune-beheerder. Bepaal of u moet meer licenties toevoegen voordat u deze functie gebruikt.  

7.  De apparaatinschrijvingsbeheerder kan nu inschrijven van mobiele apparaten met behulp van dezelfde procedure die een eindgebruiker voor een scenario bring-your-eigenaar-device (BYOD) in de bedrijfsportal gebruikt.  

#### <a name="delete-a-device-enrollment-manager-from-intune"></a>Een apparaatinschrijvingsbeheerder uit Intune verwijderen  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw in de werkruimte **Beheer** het knooppunt **Cloud Services** uit en klik op **Microsoft Intune-abonnementen**. Selecteer het Microsoft Intune-abonnement waaraan u moet een apparaatinschrijvingsbeheerder toevoegen en klik op **eigenschappen**.  

3.  Klik in het dialoogvenster Eigenschappen van Microsoft Intune-abonnement op de **Apparaatinschrijvingsbeheerder** tabblad.  

4.  **Zoekopdracht** voor de apparaatinschrijvingsbeheerder wilt verwijderen en klik op **verwijderen**, klikt u vervolgens **OK**.  

 Verwijderen van een apparaatinschrijvingsbeheerder heeft geen invloed op ingeschreven apparaten. Wanneer een apparaatinschrijvingsbeheerder wordt verwijderd:  

-   Er is geen geregistreerde apparaten worden beïnvloed  

-   Blijven ingeschreven apparaten volledig beheerd  

-   De accountreferenties van verwijderde apparaatinschrijvingsbeheerder blijven geldig voor aanmelding bij de bedrijfsportal toegang tot apps  

-   De verwijderde apparaatinschrijvingsbeheerder accountreferenties nog steeds niet wissen of buiten gebruik stellen van apparaten  

-   De verwijderde apparaatinschrijvingsbeheerder-account van gerelateerd aan ingeschreven apparaten blijft, maar er geen extra apparaten worden ingeschreven.

