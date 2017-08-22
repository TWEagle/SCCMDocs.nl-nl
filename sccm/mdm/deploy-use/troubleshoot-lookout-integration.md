---
title: Problemen met Lookout integratie oplossen | System Center Configuration Manager
description: Dit onderwerp beschrijft het oplossen van problemen die vaak bij Lookout integratie voorkomen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e36b98c7-d0f4-4dd6-bac3-6a6c4b4bf841
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 4fd2d3b8aae6a2f42e7c6a87723d16368be30984
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Lookout integratie met Intune oplossen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

## <a name="troubleshoot-login-errors"></a>Meld u fouten oplossen
### <a name="403-errors"></a>403 fouten
Mogelijk ziet u een fout 403 wanneer u zich aanmelden bij de [Lookout MTP-beheerconsole](https://aad.lookout.com): **u bent niet gemachtigd voor toegang tot de service** dit kan gebeuren wanneer de gebruikersnaam die u hebt opgegeven geen lid van de Azure Active Directory (Azure AD)-groep die is geconfigureerd is voor toegang tot Lookout MTP.

Lookout MTP is geconfigureerd dat alleen gebruikers van een geconfigureerde Azure AD-groep voor toegang. Als u welke groep is geconfigureerd met toegang tot Lookout MTP weet, moet u contact op met Lookout ondersteuning.

U kunt contact opnemen met ondersteuning via Lookout op de volgende methoden:

* E-mail:enterprisesupport@lookout.com
* Meld u aan bij de [MTP Console](http://aad.lookout.com), en navigeer naar de **ondersteuning** module.
* Ga naar: https://enterprise.support.lookout.com/hc/en-us/requests en maak een ondersteuningsaanvraag.

### <a name="unable-to-sign-in"></a>Kan niet aanmelden
Mogelijk ziet u de volgende fout wanneer de globale beheerder Azure AD-gebruiker heeft niet de eerste installatie van de Lookout geaccepteerd.

![Schermafbeelding van de fout die aanmeldingsactiviteiten Lookout-aanmeldingsscherm](media/lookout-consent-not-accepted-error.png)

U lost dit probleem, globale beheerder moet de gebruiker het aanmelden bij https://aad.lookout.com/les?action=consent en accepteer de prompt voor het starten van de installatie. Meer gedetailleerde informatie vindt u in [instellen van uw abonnement met Lookout MTP](set-up-your-subscription-with-lookout.md) onderwerp

## <a name="troubleshoot-device-status-issues"></a>Oplossen van problemen met de status van apparaat

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Apparaat niet weergegeven in de lijst met Lookout MTP-console

Dit kan gebeuren in een van de volgende scenario's:
* Wanneer de gebruiker die eigenaar is van dit apparaat is het niet in de **inschrijving groep** opgegeven in de **Lookout MTP Console**.  Van de **System** -module, gaat u naar de **Intune-Connector** tabblad en bekijk de **inschrijving Management** instellingen.  Hier ziet u een of meer Azure AD-groepen geconfigureerd voor de inschrijving.  Controleer of de gebruiker die eigenaar is van het ontbrekende apparaat deel uit van een van de opgegeven Azure AD-groepen.  Nadat u een nieuwe gebruiker is toegevoegd aan de inschrijvingsgroep van het duurt voor het geconfigureerde pollinginterval (5 minuten is de standaardinstelling) om te zien van het apparaat weergegeven in de **apparaten** module van de Lookout MTP-Console.

* Als het apparaat wordt niet ondersteund door Lookout MTP.  Apparaten die niet-ondersteunde wordt weergegeven in de **beheerde apparaten** sectie van de connectorinstellingen op de Lookout MTP-Console.

### <a name="device-continues-to-be-reported-as-pending"></a>Apparaat heeft nog steeds worden gerapporteerd als **in behandeling**

Een apparaat dat wordt weergegeven **in behandeling** betekent dat de gebruiker heeft niet de Lookout for work app geopend en getikt de **activeren** knop. Lees het volgende onderwerp voor meer informatie over de activering van het apparaat met Lookout voor werk app:

[U wordt gevraagd Lookout for Work installeren op uw Android-apparaat](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>In de Lookout MTP-console een apparaat wordt weergegeven als actief, maar heeft geen een apparaat-ID.
Dit betekent dat de gebruiker die eigenaar is van dit apparaat is niet in de inschrijvingsgroep die is opgegeven in de Lookout MTP-Console.   Een apparaat kan krijgen tot deze status is als de gebruiker die eigenaar is van het apparaat is verwijderd uit de inschrijvingsgroep of de de inschrijvingsgroep waartoe de gebruiker behoort heeft is verwijderd.

Van de **System** -module op de Lookout MTP-console gaat u naar de **Intune-Connector** tabblad en bekijk de **inschrijving** instellingen.  Hier ziet u een of meer Azure AD-groepen geconfigureerd voor de inschrijving.  Controleer of de gebruiker die eigenaar is van het apparaat deel uit van een van de Azure AD-groepen die zijn opgegeven.

Terwijl een apparaat in deze staat is, Lookout blijven kennis van de gebruiker van bedreigingen die zijn gedetecteerd, maar wordt niet alle informatie verzonden naar Intune.

### <a name="device-shows-disconnected-state"></a>Apparaat wordt niet-verbonden status weergegeven

Verbinding verbroken betekent dat u Lookout MTP is niet van het apparaat voor gehoord gedurende een vooraf geconfigureerde tijdsinterval (de standaardwaarde is 30 dagen met een minimum van 7 dagen). Dit betekent dat de app bedrijfsportal of de Lookout for Work-app is niet geïnstalleerd op het apparaat of is verwijderd. De apps opnieuw te installeren, moet dit probleem oplossen. Wanneer de gebruiker wordt geopend Lookout for Work en Hiermee activeert u de app, het apparaat resyncs met Lookout MTP en Intune.

### <a name="forcing-a-resync-on-the-device"></a>Opnieuw synchroniseren op het apparaat wordt afgedwongen
Van de **apparaten** module van de beheerder de Lookout MTP-console, kunt selecteren van het apparaat en wilt verwijderen.   De volgende keer dat de eigenaar van het apparaat wordt geopend de Lookout for Work-app en tikken **activeren**, status van het apparaat een volledige resync gaat uitvoeren.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>Dit apparaat is niet meer gebruikt door de eigenaar van het apparaat
U moet het apparaat wissen en vraagt u de nieuwe gebruiker te registreren, zoals beschreven in [in dit onderwerp](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/wipe-lock-reset-devices#full-wipe).


U kunt ook gaan naar de **apparaten** module van de Lookout MTP-Console en kies **verwijderen**.

Als de nieuwe gebruiker zich in een van de inschrijving van groepen die zijn opgegeven in de Lookout MTP-console, wordt het apparaat wordt weergegeven nadat Azure AD het apparaat wordt gekoppeld aan de nieuwe gebruiker.

## <a name="compliance-remediation-workflows"></a>Werkstromen voor naleving-herstel
[U wordt gevraagd Lookout for Work installeren op uw Android-apparaat]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[U moet een bedreiging die Lookout for Work op uw Android-apparaat gevonden oplossen](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
