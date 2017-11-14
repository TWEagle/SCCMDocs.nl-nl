---
title: Exchange ActiveSync-e-mailprofiel maken
titleSuffix: Configuration Manager
description: Informatie over het maken en configureren van e-mailprofielen in System Center Configuration Manager die werken met Microsoft Intune.
ms.custom: na
ms.date: 07/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 120442be-179e-450c-a0c4-284046895da3
caps.latest.revision: "4"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 5fc0d5e68e27b3bde9ed3aa45a439c8b333da1d6
ms.sourcegitcommit: 922d6d9c91ba2158b938df381277be1b5f1d434a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2017
---
# <a name="exchange-activesync-email-profiles-in-system-center-configuration-manager"></a>Exchange ActiveSync-e-mailprofielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt apparaten met e-mailprofielen en beperkingen instellen met behulp van Microsoft Intune en Exchange ActiveSync. Hiermee kunt uw gebruikers toegang tot bedrijfse-mail op hun apparaten met minimale instelling zelf.  

 U kunt de volgende typen apparaten configureren met e-mailprofielen:  

- Windows 10
- Windows Phone 8,1
- iPhones met iOS 9 en hoger 
- iPads met iOS 9 en hoger 
- Samsung KNOX Standard (4 en hoger)
- Android for Work

E-mailprofielen implementeren op apparaten, moet u de apparaten in Intune inschrijven. Zie [Mobiele apparaten beheren met Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx)voor meer informatie over het inschrijven van uw apparaten.

> [!NOTE]
> Intune biedt twee Android voor zakelijke e-mailprofielen, één voor de Gmail e-mail-app en de negen werk e-mail-app. Deze apps zijn beschikbaar in de Google Play Store en ondersteuning van verbindingen met Exchange. Schakel de e-connectiviteit door een van deze e-mail-apps implementeren op de apparaten van gebruikers, en maken en implementeren van het juiste profiel. E-mail-apps zoals negen werk is mogelijk niet beschikbaar. Bekijk de app de licentiegegevens of neem contact op met de app bedrijf met vragen.

 Naast het configureren van een e-mailaccount op het apparaat, kunt u de synchronisatie-instellingen voor contactpersonen, agenda en taken configureren.  

 Wanneer u een e-mailprofiel maakt, kunt u een groot aantal beveiligingsinstellingen opnemen. Deze instellingen omvatten certificaten voor identiteit, versleuteling en ondertekening, die zijn ingesteld met behulp van System Center Configuration Manager-certificaatprofielen. Zie [Certificaatprofielen in System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles.md) voor meer informatie over certificaatprofielen.    

## <a name="create-an-exchange-activesync-email-profile"></a>Een e-mailprofiel voor Exchange ActiveSync maken  

Als u wilt een profiel maakt, moet u de Wizard Exchange ActiveSync maken e-mailprofiel gebruiken. 

1.  Kies in de Configuration Manager-console **activa en naleving**.  

2.  In de **activa en naleving** werkruimte Vouw **instellingen voor naleving**, vouw **toegang tot bedrijfsbronnen**, en kies vervolgens **e-mailprofielen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Exchange ActiveSync e-mailprofiel maken** om de wizard te starten.

4.  Op de **algemene** pagina van de wizard configureert u het volgende:

    - **Naam**. Geef een beschrijvende naam voor het e-mailprofiel.

    - **Beschrijving**. Geef eventueel een beschrijving voor het e-mailprofiel waarmee u deze kunt herkennen in de Configuration Manager-console.

    - **Dit e-mailprofiel voor Android for Work is**. Selecteer deze optie als u dit e-mailprofiel op alleen Android voor werk apparaten wilt implementeren. Als u dit selectievakje inschakelt, de **ondersteunde Platforms** pagina van de wizard niet wordt weergegeven. Alleen Android voor werk-e-mailprofielen zijn geconfigureerd.

4.  Op de **Exchange ActiveSync** pagina van de wizard, geeft u de volgende informatie:  

    -   **Exchange ActiveSync-host**. Geef de hostnaam van uw bedrijf Exchange-server die als host fungeert voor Exchange ActiveSync-services.  

    -   **Accountnaam**. Geef de weergavenaam voor het e-mailaccount, zoals deze wordt weergegeven aan gebruikers op hun apparaten.  

    -   **Gebruikersnaam voor account**. Kies hoe de gebruikersnaam van de e-mailadres op clientapparaten wordt geconfigureerd. U kunt een van de volgende opties kiezen uit de vervolgkeuzelijst:  

        -   **Principalnaam van gebruiker**. Gebruik de volledige principal-naam aan te melden bij Exchange.  

        -   **AccountName**. Gebruik de naam van de volledige gebruikersaccount uit Active Directory.

        -   **Primair SMTP-adres**. Gebruik het primaire SMTP-adres van de gebruiker zich aanmeldt bij Exchange.  

    -   **E-mailadres**. Kies hoe het e-mailadres voor de gebruiker op elk clientapparaat wordt gegenereerd. U kunt een van de volgende opties kiezen uit de vervolgkeuzelijst:  

        -   **Primair SMTP-adres**. Gebruik het primaire SMTP-adres van de gebruiker zich aanmeldt bij Exchange.  

        -   **Principalnaam van gebruiker**. Gebruik de volledige principal-naam als e-mailadres.  

    -   **Accountdomein**. Kies een van de volgende opties:  

        -   **Ophalen van Active Directory**  

        -   **Aangepast**  

         Dit veld is van toepassing als **sAMAccountName** is geselecteerd in de **gebruikersnaam voor Account** vervolgkeuzelijst.  

    -   **Verificatiemethode**. Kies een van de volgende verificatiemethoden die worden gebruikt voor het verifiëren van de verbinding met Exchange ActiveSync:  

        -   **Certificaten**. Een identiteitscertificaat wordt gebruikt om de Exchange ActiveSync-verbinding te verifiëren.  

        -   **Gebruikersnaam en wachtwoord**. Gebruiker van het apparaat moet een wachtwoord verbinding maken met Exchange ActiveSync opgeven. (De gebruikersnaam is geconfigureerd als onderdeel van het e-mailprofiel).  

    -   **Identiteitscertificaat**. Kies **Selecteer** en kies vervolgens een certificaat voor identiteit.  

         Certificaten voor identiteit moet SCEP-certificaten; u kunt een PFX-certificaat niet gebruiken.  Zie voor meer informatie, [Certificaatprofielen in System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

         Deze optie is alleen beschikbaar als u hebt gekozen **certificaten** onder **verificatiemethode**.  

    -   **S/MIME gebruiken**. Uitgaande e-mail met S/MIME-codering verzenden. Deze optie is alleen van toepassing op iOS-apparaten. Kies uit de volgende opties:

        -   **Handtekeningcertificaten**.  Kies **Selecteer** en kies vervolgens het profiel voor een certificaat voor versleuteling.  

            Het profiel is een SCEP- of PFX-certificaat.  Als zowel ondertekening als versleuteling worden gebruikt, moet u echter PFX-certificaatprofielen voor selecteren *beide* ondertekening en versleuteling.

        -   **Certificaten voor bestandsversleuteling**. Kies **Selecteer** en kies vervolgens een certificaat wilt gebruiken voor versleuteling. U kunt alleen een PFX-certificaat te gebruiken als een versleutelingscertificaat.

        -   Inschakelen voor het versleutelen van alle e-mailberichten op iOS-apparaten moet de **versleuteling vereisen** selectievakje.    

         Voordat u hier kunt kiezen, moet u certiciate profielen maken.  Zie voor meer informatie, [Certificaatprofielen in System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles).  

## <a name="configure-synchronization-settings-for-the-exchange-activesync-email-profile"></a>Synchronisatie-instellingen voor het e-mailprofiel voor Exchange ActiveSync configureren  

Geef op de pagina **Synchronisatie-instellingen configureren** van de wizard E-mailprofiel voor Exchange ActiveSync maken de volgende informatie op:  

-   **Planning**. Kies het schema waarmee apparaten u gegevens van de Exchange-server synchroniseert. Deze optie is alleen van toepassing op Windows Phone-apparaten. U kunt kiezen uit:  

    -   **Niet geconfigureerd**. Een Synchronisatieplanning wordt niet afgedwongen. Hiermee kunnen gebruikers hun eigen Synchronisatieplanning configureren.  

    -   **Als berichten binnenkomen**. Gegevens, zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd wanneer ze binnenkomen.  

    -   **15 minuten**. Gegevens, zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd om de 15 minuten.  

    -   **30 minuten**. Gegevens, zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd elke 30 minuten.  

    -   **60 minuten**. Gegevens, zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd om de 60 minuten.  

    -   **Handmatige**. Gebruiker van het apparaat moet synchronisatie handmatig starten.  

-   **Aantal dagen aan e-mail synchroniseren**. Kies in de vervolgkeuzelijst het aantal dagen aan e-mail dat u wilt synchroniseren. Kies een van de volgende waarden:  

    -   **Niet geconfigureerd**. De instelling wordt niet afgedwongen. Hiermee kunt gebruikers instellen hoeveel e-mailberichten naar het apparaat wordt gedownload.  

    -   **Onbeperkte**. Alle beschikbare e-mail synchroniseren.  

    -   **1 dag**  

    -   **3 dagen**  

    -   **1 week**  

    -   **2 weken**  

    -   **1 maand**  

-   **Toestaan dat berichten worden verplaatst naar andere e-mailaccounts**. Selecteer deze optie om gebruikers e-mailberichten verplaatsen tussen verschillende accounts die zijn geconfigureerd op hun apparaat te laten. Deze optie is alleen van toepassing op iOS-apparaten.  

-   **Toestaan dat e-mails worden verzonden vanuit toepassingen van derden**. Selecteer deze optie om gebruikers e-mail verzenden vanuit bepaalde niet-standaard van derden e-mailtoepassingen te laten. Deze optie is alleen van toepassing op iOS-apparaten.  

-   **Recent gebruikte e-mailadressen synchroniseren**. Kies deze optie voor het synchroniseren van de lijst met e-mailadressen die recent zijn gebruikt op het apparaat. Deze optie is alleen van toepassing op iOS-apparaten.  

-   **SSL gebruiken**. Selecteer deze optie voor het gebruik van Secure Sockets Layer (SSL)-communicatie voor het verzenden van e-mailberichten, ontvangen van e-mailberichten en communicatie met de Exchange-server.  

-   **Inhoudtype voor synchronisatie**. Kies het type inhoud dat u wilt synchroniseren met apparaten. Deze optie is alleen van toepassing op Windows Phone-apparaten. U kunt kiezen uit:  

    -   **E-mail**  

    -   **Contactpersonen**  

    -   **Kalender**  

    -   **Taken**  

## <a name="specify-supported-platforms-for-the-exchange-activesync-email-profile"></a>Ondersteunde platforms voor het e-mailprofiel voor Exchange ActiveSync opgeven  

1.  Op de **ondersteunde Platforms** pagina van de Exchange ActiveSync E-mail Wizard profiel maken, kies de besturingssystemen waarop het e-mailprofiel wordt geïnstalleerd. Of kies **Alles selecteren** voor het installeren van het e-mailprofiel op alle beschikbare besturingssystemen.  

2.  Sluit de wizard af.

Zie voor meer informatie over het implementeren van de Exchange ActiveSync-e-mailprofielen [profielen in System Center Configuration Manager implementeren](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md).  
