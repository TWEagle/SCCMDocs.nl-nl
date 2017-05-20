---
title: Zoek integratie oplossen | System Center Configuration Manager
description: Dit onderwerp beschrijft het oplossen van problemen die vaak met zoek-integratie voorkomen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e36b98c7-d0f4-4dd6-bac3-6a6c4b4bf841
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 4fd2d3b8aae6a2f42e7c6a87723d16368be30984
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Zoek integratie met Intune oplossen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

## <a name="troubleshoot-login-errors"></a>Aanmelding fouten oplossen
### <a name="403-errors"></a>403 fouten
Wordt er een fout 403 wanneer u zich aanmelden bij de [altijd MTP console](https://aad.lookout.com): **u bent niet gemachtigd voor toegang tot de service** dit kan gebeuren wanneer de opgegeven gebruikersnaam geen lid van de Azure Active Directory (Azure AD)-groep die is geconfigureerd is voor toegang tot dan MTP.

Zoek MTP waarmee alleen gebruikers van een geconfigureerde Azure AD-groep voor toegang is geconfigureerd. Als u niet zeker weet welke groep is geconfigureerd met toegang tot MTP dan contact op met ondersteuning voor altijd.

U kunt contact op met de ondersteuning van dan door op de volgende methoden:

* E-mail:enterprisesupport@lookout.com
* Meld u aan bij de [MTP Console](http://aad.lookout.com), en gaat u naar de **ondersteuning** module.
* Ga naar: https://enterprise.support.lookout.com/hc/en-us/requests uit en maak een ondersteuningsaanvraag.

### <a name="unable-to-sign-in"></a>Kan niet aanmelden
U mag de volgende fout zien wanneer de gebruiker van de globale beheerder Azure AD is niet geaccepteerd voor de eerste installatie dan.

![Schermafdruk van het aanmeldingsscherm altijd ondertekenen met fout](media/lookout-consent-not-accepted-error.png)

Dit probleem wilt oplossen, globale beheerder moet de gebruiker het aanmelden bij de https://aad.lookout.com/les?action=consent en accepteer de prompt om de installatie te starten. Meer gedetailleerde informatie te vinden in [instellen van uw abonnement met altijd MTP](set-up-your-subscription-with-lookout.md) onderwerp

## <a name="troubleshoot-device-status-issues"></a>Oplossen van problemen met de status van apparaat

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Apparaat niet weergegeven in de lijst met Profiteer zo veel mogelijk MTP-console

Dit kan gebeuren in een van de volgende scenario's:
* Wanneer de gebruiker die eigenaar is van dit apparaat is niet in de **inschrijving groep** opgegeven in de **altijd MTP Console**.  Van de **System** module, Ga naar de **Intune-Connector** tabblad en bekijkt u de **inschrijving Management** instellingen.  Hier ziet u een of meer Azure AD-groepen geconfigureerd voor de inschrijving.  Controleer of de gebruiker die eigenaar is van het ontbrekende apparaat deel van een van de opgegeven uitmaakt Azure AD-groepen.  Nadat u een nieuwe gebruiker is toegevoegd aan de inschrijvingsgroep van het duurt voor het geconfigureerde pollinginterval (5 minuten is de standaardinstelling) om te zien van het apparaat weergegeven in de **apparaten** module van de Console altijd MTP.

* Als het apparaat wordt niet ondersteund door altijd MTP.  Apparaten die niet-ondersteunde wordt weergegeven in de **beheerde apparaten** sectie van de connector-instellingen op de altijd MTP-Console.

### <a name="device-continues-to-be-reported-as-pending"></a>Apparaat moet worden gerapporteerd als blijft **in behandeling**

Een apparaat dat wordt weergegeven **in behandeling** betekent dat de gebruiker is niet altijd werk app geopend en wel de **activeren** knop. Lees het volgende onderwerp voor meer informatie over de activering van het apparaat met Profiteer zo veel mogelijk voor werk app:

[U wordt gevraagd werk altijd installeren op een Android-apparaat](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>In de console MTP dan een apparaat wordt als actief weergegeven, maar heeft geen een apparaat-ID.
Dit betekent dat de gebruiker die eigenaar is van dit apparaat niet in de inschrijvingsgroep die is opgegeven in de Console altijd MTP.   Een apparaat kunt krijgen tot deze status is als de gebruiker die eigenaar is van het apparaat is verwijderd uit de inschrijvingsgroep of de inschrijvingsgroep die de gebruiker behoort is verwijderd.

Van de **System** module op de altijd MTP-console gaat u naar de **Intune-Connector** tabblad en bekijk de **inschrijving** instellingen.  Hier ziet u een of meer Azure AD-groepen geconfigureerd voor de inschrijving.  Controleer of de gebruiker die eigenaar is van het apparaat is onderdeel van een van de Azure AD-groepen die zijn opgegeven.

Terwijl een apparaat in deze staat is, dan blijft de gebruiker melding van alle bedreigingen gedetecteerd, maar niet bedreiging informatie sturen naar Intune.

### <a name="device-shows-disconnected-state"></a>Apparaat wordt ontkoppeld

Betekent dat altijd MTP is niet van het apparaat voor gehoord tijdens een tijdsinterval vooraf geconfigureerde verbroken (de standaardwaarde is 30 dagen met een minimum van 7 dagen). Dit betekent dat de bedrijfsportal-app of zoek naar werk app is niet geïnstalleerd op het apparaat of is verwijderd. Opnieuw te installeren de apps moet dit probleem oplossen. Wanneer de gebruiker dan werk wordt geopend en de app, het apparaat resyncs met altijd MTP en Intune activeert.

### <a name="forcing-a-resync-on-the-device"></a>Opnieuw synchroniseren op het apparaat wordt afgedwongen
Van de **apparaten** module van de Profiteer zo veel mogelijk MTP-console de beheerder kan het apparaat selecteert en wilt verwijderen.   De volgende keer dat de eigenaar van het apparaat wordt geopend altijd werk app en tikken **activeren**, de apparaatstatus, dient een volledige resync.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>De eigenaar van het apparaat is niet langer met behulp van dit apparaat
U moet het apparaat te wissen en vraagt u de nieuwe gebruiker te schrijven, zoals beschreven in [in dit onderwerp](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/wipe-lock-reset-devices#full-wipe).


U kunt ook gaan naar de **apparaten** module van de Console altijd MTP en kies **verwijderen**.

Als de nieuwe gebruiker zich in een van de inschrijving van groepen die zijn opgegeven in de console altijd MTP, wordt het apparaat wordt weergegeven als Azure AD het apparaat wordt gekoppeld aan de nieuwe gebruiker.

## <a name="compliance-remediation-workflows"></a>Compatibiliteit herstel werkstromen
[U wordt gevraagd werk altijd installeren op een Android-apparaat]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[U moet een bedreiging die altijd for Work op een Android-apparaat gevonden oplossen](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

