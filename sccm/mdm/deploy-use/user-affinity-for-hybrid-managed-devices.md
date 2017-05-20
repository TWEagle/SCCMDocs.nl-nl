---
title: Affiniteit tussen gebruikers en hybride beheerde apparaten in Configuration Manager | Microsoft-documenten
description: Affiniteit van gebruiker configureren voor beheerde apparaten in Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5d520a7-e9e5-40ee-91f9-f2684214beb6
caps.latest.revision: 6
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: d039792a88b9e7704f37718a88f841dd9216d1b1
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="user-affinity-for-hybrid-managed-devices-in-configuration-manager"></a>Affiniteit tussen gebruikers en hybride beheerde apparaten in Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u profielen voor apparaten in Bedrijfseigendom configureert, kan de beheerder opgeven of de beheerde apparaten kunnen hebben *affiniteit tussen gebruikers en* die een specifieke gebruiker wordt geïdentificeerd met het apparaat.  

##  <a name="BKMK_iOSCP"></a>Beheerde apparaten affiniteit tussen gebruikers  
 Op apparaten die zijn geconfigureerd met **user affinity** kan de bedrijfsportal-app worden geïnstalleerd en uitgevoerd om apps te downloaden en apparaten te beheren. Nadat gebruikers hun apparaten hebben ontvangen, moeten zij een aantal extra stappen uitvoeren om Configuratieassistent te voltooien en de bedrijfsportal-app te installeren.  

#### <a name="how-to-enroll-ios-devices-with-user-affinity"></a>Het inschrijven van iOS-apparaten met affiniteit tussen gebruikers  

1.  Wanneer gebruikers eerst power op hun nieuwe apparaten, wordt ze gevraagd de Configuratieassistent voltooid. Het inschrijvingsprofiel kunt opgeven dat referenties vragen tijdens de installatie. Gebruikers moeten de referenties (dat wil zeggen de unieke naam of de UPN) dat is gekoppeld aan het Intune-abonnement gebruiken.  

2.  Tijdens de installatie, kunnen gebruikers ook worden gevraagd om een Apple-ID. Een Apple-ID moet worden opgegeven voordat het apparaat kan de bedrijfsportal installeren. Gebruikers kunnen een Apple-ID opgeven na de installatie van de iOS **instellingen** menu.  

3.  Nadat setup is voltooid, het iOS-apparaat moet installeren de app bedrijfsportal uit de App Store bijvoorbeeld [bedrijfsportal-app](https://itunes.apple.com/us/app/id719171358).  

4.  De gebruiker kan nu aanmelden bij de bedrijfsportal met de UPN gebruikt bij het instellen van het apparaat.  

5.  Na het aanmelden, wordt de gebruiker gevraagd om hun apparaat te registreren. De eerste stap is het **identificeren van het apparaat**. De app geeft een lijst met iOS-apparaten die zakelijke ingeschreven en toegewezen aan de eindgebruiker Intune-account. Kies het desbetreffende apparaat.  

     Als dit apparaat nog niet voor het bedrijf is ingeschreven, selecteert u 'nieuw apparaat' om door te gaan met de standaardinschrijving.  

6.  De gebruiker moet het serienummer van het nieuwe apparaat bevestigen in het volgende scherm. De gebruiker kan op de koppeling Bevestig het serienummer tikken om de app Instellingen te starten, waarmee het serienummer wordt geverifieerd. De gebruiker moet vervolgens de laatste 4 tekens van het serienummer invoeren in de bedrijfsportal-app.  

     Met deze stap wordt gecontroleerd of het apparaat het bedrijfsapparaat is dat is ingeschreven in Intune. Als het serienummer op het apparaat niet overeenkomt, is het verkeerde apparaat geselecteerd. Ga terug naar het vorige scherm en selecteer een ander apparaat.  

7.  Wanneer het serienummer is geverifieerd, wordt de app bedrijfsportal wordt omgeleid naar de website van de bedrijfsportal te voltooien wilt inschrijven en vervolgens vraagt de gebruiker om terug te keren naar de app.  

8.  De inschrijving is nu voltooid. U kunt dit apparaat nu gebruiken met de volledige set mogelijkheden.  

##  <a name="BKMK_noUA"></a>Beheerde apparaten zonder affiniteit tussen gebruikers  
 Op apparaten die zijn geconfigureerd met **no user affinity** bieden geen ondersteuning voor de bedrijfsportal. Installeer de app niet op deze apparaten. De bedrijfsportal is bedoeld voor gebruikers met zakelijke referenties die toegang tot persoonlijke bedrijfsresources (bijvoorbeeld e-mail) nodig hebben. Apparaten die zijn ingeschreven **zonder gebruikersaffiniteit** zijn niet bedoeld voor gebruik met een specifieke gebruikersaanmelding. Kiosks, verkooppunten (POS) of gedeelde hulpmiddelen zijn typische gebruiksvoorbeelden van apparaten die zonder gebruikersaffiniteit worden ingeschreven. Als gebruikersaffiniteit vereist is, moet **Gebruikersaffiniteit** in het inschrijvingsprofiel van het apparaat zijn geselecteerd voordat het apparaat wordt ingeschreven. U wijzigt de status van de affiniteit op een apparaat, moet u buiten gebruik stellen en het apparaat opnieuw inschrijven.

