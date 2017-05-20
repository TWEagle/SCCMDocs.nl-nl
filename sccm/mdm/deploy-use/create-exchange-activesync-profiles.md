---
title: E-mailprofielen voor Exchange ActiveSync maken | Microsoft-documenten
description: Informatie over het maken en configureren van e-mailprofielen in System Center Configuration Manager die samenwerken met Microsoft Intune.
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 120442be-179e-450c-a0c4-284046895da3
caps.latest.revision: 4
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: bcf337d2abbcd5aad0f99098f6afd4a73ada3a0b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="exchange-activesync-email-profiles-in-system-center-configuration-manager"></a>E-mailprofielen voor Exchange ActiveSync in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt apparaten met e-mailprofielen en beperkingen instellen met behulp van Microsoft Intune en Exchange ActiveSync. Hiermee kunt uw gebruikers toegang tot bedrijfse-mail op hun apparaten met minimale instelling van hun kant.  

 U kunt de volgende typen apparaten configureren met e-mailprofielen:  

- Windows 10
- Windows Phone 8,1
- Windows Phone 8.0
- iPhones met iOS 5, iOS 6, iOS 7 en iOS 8  
- iPads met iOS 5, iOS 6, iOS 7 en iOS 8  
- Samsung KNOX Standard (4 en hoger)
- Android for Work

E-mailprofielen implementeren op apparaten, moet u de apparaten in Intune inschrijven. Zie [Mobiele apparaten beheren met Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx)voor meer informatie over het inschrijven van uw apparaten.

> [!NOTE]
> Intune biedt twee Android voor de e-mailprofielen werk, één voor de Gmail e-mail-app en negen werk e-mail-app. Deze apps zijn beschikbaar in de Google Play Store en ondersteuning van verbindingen met Exchange. Zodat de connectiviteit van de e-mailadres een van deze e-mail-apps implementeren op apparaten van uw gebruikers, en maken en implementeren van het juiste profiel. E-mail-apps negen werk is mogelijk niet beschikbaar. Controleer de app de licentiegegevens of neem contact op met de app bedrijfsportal met vragen.

 Naast het configureren van een e-mailaccount op het apparaat, kunt u de synchronisatie-instellingen voor contactpersonen, agenda en taken.  

 Wanneer u een e-mailprofiel maakt, kunt u een groot aantal beveiligingsinstellingen opnemen. Deze instellingen omvatten certificaten voor identiteit, versleuteling en ondertekening, die is ingesteld met behulp van System Center Configuration Manager-certificaatprofielen. Zie [Certificaatprofielen in System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles) voor meer informatie over certificaatprofielen.    

## <a name="create-an-exchange-activesync-email-profile"></a>Een e-mailprofiel voor Exchange ActiveSync maken  

Als u wilt een profiel maakt, moet u de Wizard Exchange ActiveSync maken e-mailprofiel gebruiken. 

1.  Kies in de Configuration Manager-console **activa en naleving**.  

2.  In de **activa en naleving** werkruimte Vouw **compatibiliteitsinstellingen**, vouw **toegang tot bedrijfsbronnen**, en kies vervolgens **e-mailprofielen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Exchange ActiveSync e-mailprofiel maken** om de wizard te starten.

4.  Op de **algemeen** pagina van de wizard, configureer dan het volgende:

    - **Naam**. Geef een beschrijvende naam voor het e-mailprofiel.

    - **Beschrijving**. Geef eventueel een beschrijving voor het e-mailprofiel waarmee u geïdentificeerd in de Configuration Manager-console.

    - **Dit e-mailprofiel voor Android voor werk is**. Selecteer deze optie als u dit e-mailprofiel naar alleen Android voor werk apparaten implementeren wilt. Als u dit selectievakje inschakelt, de **ondersteunde Platforms** pagina van de wizard niet wordt weergegeven. Alleen Android voor werk-e-mailprofielen zijn geconfigureerd.

4.  Op de **Exchange ActiveSync** pagina van de wizard de volgende informatie opgeven:  

    -   **Exchange ActiveSync-host**. Geef de hostnaam van uw bedrijf Exchange-server die als host fungeert voor Exchange ActiveSync-services.  

    -   **Accountnaam**. Geef de weergavenaam voor het e-mailaccount zoals deze wordt weergegeven voor gebruikers op hun apparaten.  

    -   **Gebruikersnaam voor account**. Kies hoe de gebruikersnaam e-mailadres op clientapparaten wordt geconfigureerd. U kunt een van de volgende opties kiezen uit de vervolgkeuzelijst:  

        -   **User Principal Name**. Gebruik de volledige principal-naam aanmelden bij Exchange.  

        -   **AccountName**. Gebruik de naam van de volledige gebruikersaccount uit Active Directory.

        -   **Primair SMTP-adres**. Gebruik het primaire SMTP-adres van de gebruiker aanmelden bij Exchange.  

    -   **E-mailadres**. Kiezen hoe het e-mailadres voor de gebruiker op elk clientapparaat wordt gegenereerd. U kunt een van de volgende opties kiezen uit de vervolgkeuzelijst:  

        -   **Primair SMTP-adres**. Gebruik het primaire SMTP-adres van de gebruiker aanmelden bij Exchange.  

        -   **User Principal Name**. Gebruik de volledige principal-naam als het e-mailadres.  

    -   **Accountdomein**. Kies een van de volgende opties:  

        -   **Ophalen van Active Directory**  

        -   **Aangepast**  

         Dit veld is van toepassing alleen als **sAMAccountName** is geselecteerd in de **gebruikersnaam voor Account** vervolgkeuzelijst.  

    -   **Verificatiemethode**. Kies een van de volgende verificatiemethoden die worden gebruikt voor het verifiëren van de verbinding met Exchange ActiveSync:  

        -   **Certificaten**. Een identiteitscertificaat wordt gebruikt om de Exchange ActiveSync-verbinding te verifiëren.  

        -   **Gebruikersnaam en wachtwoord**. Gebruiker van het apparaat moet een wachtwoord invoeren om te verbinden met Exchange ActiveSync. (De gebruikersnaam is geconfigureerd als onderdeel van het e-mailprofiel).  

    -   **Identiteitscertificaat**. Kies **Selecteer** en kies vervolgens een certificaat voor identiteit.  

        > [!NOTE]  
        > Voordat u het identiteitscertificaat kiezen kunt, moet u het eerst configureren als certificaatprofiel voor Simple Certificate Enrollment Protocol (SCEP). Zie [Certificaatprofielen in System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles) voor meer informatie over certificaatprofielen.  

         Deze optie is alleen beschikbaar als u hebt gekozen **certificaten** onder **verificatiemethode**.  

    -   **S/MIME gebruiken**. Verzend uitgaande e-mail met S/MIME-codering. Deze optie is alleen van toepassing op iOS-apparaten. Kies uit de volgende opties:

        -   **Versleutelingscertificaten**. Kies **Selecteer** en kies vervolgens een certificaat wilt gebruiken voor versleuteling. U kunt alleen een PFX-certificaat te gebruiken als een versleutelingscertificaat.

        Als u een versleutelingscertificaat en een handtekeningcertificaat kiest, moet deze beide in PDF-indeling.

        > [!NOTE]  
        > Voordat u certificaten kunt, moet u ze eerst configureren als een SCEP- of PFX-certificaatprofiel. Zie [Certificaatprofielen in System Center Configuration Manager](/sccm/protect/deploy-use/introduction-to-certificate-profiles) voor meer informatie over certificaatprofielen.  

## <a name="configure-synchronization-settings-for-the-exchange-activesync-email-profile"></a>Synchronisatie-instellingen voor het e-mailprofiel voor Exchange ActiveSync configureren  

Geef op de pagina **Synchronisatie-instellingen configureren** van de wizard E-mailprofiel voor Exchange ActiveSync maken de volgende informatie op:  

-   **Planning**. Kies het schema waarmee apparaten gegevens van de Exchange-server worden gesynchroniseerd. Deze optie is alleen van toepassing op Windows Phone-apparaten. U kunt kiezen uit:  

    -   **Niet geconfigureerd**. Een schema voor synchronisatie wordt niet afgedwongen. Hiermee kunnen gebruikers hun eigen Synchronisatieplanning configureren.  

    -   **Als berichten binnenkomen**. Gegevens zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd wanneer ze binnenkomen.  

    -   **15 minuten**. Gegevens zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd om de 15 minuten.  

    -   **30 minuten**. Gegevens zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd elke 30 minuten.  

    -   **60 minuten**. Gegevens zoals e-mailberichten en agenda-items worden automatisch gesynchroniseerd om de 60 minuten.  

    -   **Handmatige**. Gebruiker van het apparaat moet synchronisatie handmatig starten.  

-   **Aantal dagen aan e-mail synchroniseren**. Kies in de vervolgkeuzelijst het aantal dagen aan e-mail dat u wilt synchroniseren. Kies een van de volgende waarden:  

    -   **Niet geconfigureerd**. De instelling wordt niet afgedwongen. Deze kan gebruikers instellen hoeveel e-mailberichten naar het apparaat worden gedownload.  

    -   **Onbeperkt**. Alle beschikbare e-mail synchroniseren.  

    -   **1 dag**  

    -   **3 dagen**  

    -   **1 week**  

    -   **2 weken**  

    -   **1 maand**  

-   **Toestaan dat berichten worden verplaatst naar andere e-mailaccounts**. Kies deze optie om gebruikers e-mailberichten verplaatsen tussen verschillende accounts die ze op hun apparaat hebben geconfigureerd. Deze optie is alleen van toepassing op iOS-apparaten.  

-   **Toestaan dat e-mails worden verzonden vanuit toepassingen van derden**. Selecteer deze optie om gebruikers e-mail verzenden vanuit bepaalde niet-standaard derde e-mailtoepassingen te laten. Deze optie is alleen van toepassing op iOS-apparaten.  

-   **Recent gebruikte e-mailadressen synchroniseren**. Selecteer deze optie voor het synchroniseren van de lijst met e-mailadressen die recent zijn gebruikt op het apparaat. Deze optie is alleen van toepassing op iOS-apparaten.  

-   **Gebruik van SSL**. Selecteer deze optie voor het gebruik van Secure Sockets Layer (SSL)-communicatie voor het verzenden van e-mailberichten, e-mailberichten ontvangt en communiceert met de Exchange-server.  

-   **Inhoudstype synchroniseren**. Kies de inhoudstypen die u wilt synchroniseren naar apparaten. Deze optie is alleen van toepassing op Windows Phone-apparaten. U kunt kiezen uit:  

    -   **E-mail**  

    -   **Contactpersonen**  

    -   **Kalender**  

    -   **Taken**  

## <a name="specify-supported-platforms-for-the-exchange-activesync-email-profile"></a>Ondersteunde platforms voor het e-mailprofiel voor Exchange ActiveSync opgeven  

1.  Op de **ondersteunde Platforms** pagina van de Wizard Exchange ActiveSync maken e-mailprofiel, kies de besturingssystemen waarop het e-mailprofiel wordt geïnstalleerd. Of kies **Alles selecteren** voor het installeren van het e-mailprofiel op alle beschikbare besturingssystemen.  

2.  Sluit de wizard af.

Zie voor meer informatie over het implementeren van e-mailprofielen voor Exchange ActiveSync [profielen in System Center Configuration Manager implementeren](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md).  

