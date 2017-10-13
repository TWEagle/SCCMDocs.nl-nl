---
title: Windows Hello voor bedrijven-instellingen | Microsoft Docs
description: Informatie over het integreren van Windows Hello voor bedrijven met System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0593c07-5dd7-4d23-a0d8-d30165f49ef7
caps.latest.revision: "17"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: a97b3d97eb302e4133b0a79a8c7e27004872c8b1
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager-hybrid"></a>Windows Hello voor bedrijven-instellingen in System Center Configuration Manager (hybride)

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager kunt u de integratie met Windows Hello voor bedrijven (voorheen Microsoft Passport for Windows), een alternatieve aanmeldingsmethode voor Windows 10-apparaten is. Hello voor Bedrijven maakt gebruik van Active Directory of een Azure Active Directory-account om een wachtwoord, smartcard of virtuele smartcard te vervangen.  

Met Hello voor Bedrijven kan voor aanmelding een **gebaar van de gebruiker** in plaats van een wachtwoord worden gebruikt. Het gebaar van een gebruiker kan een eenvoudige pincode zijn, biometrische verificatie of een extern apparaat zoals een vingerafdruklezer.  

 Configuration Manager geïntegreerd met Windows Hello voor bedrijven op twee manieren:  

-   U kunt de Configuration Manager gebruiken om te bepalen welke gebaren gebruikers wel en niet gebruiken om aan te melden.  

-   U kunt verificatiecertificaten opslaan in de sleutelarchiefprovider (KSP) van Windows Hello voor Bedrijven. Zie voor meer informatie [Certificaatprofielen](create-pfx-certificate-profiles.md).  

- U kunt Windows Hello voor bedrijven-beleid voor het domein Windows 10-apparaten waarop de Configuration Manager-client wordt uitgevoerd. Deze configuratie is omschreven [configureren Windows Hello voor bedrijven op Windows 10-apparaten domein](../../protect/deploy-use/windows-hello-for-business-settings.md#configure-windows-hello-for-business-on-domain-joined-windows-10-devices). Wanneer u gebruikmaakt van Configuration Manager met Intune (hybride), kunt u deze instellingen configureren op Windows 10 en Windows 10 Mobile-apparaten, maar niet op apparaten die lid zijn van een domein met de Configuration Manager-client.   

Raadpleeg voor algemene informatie over het configureren van Windows Hello voor bedrijven-instellingen [Windows Hello voor bedrijven-instellingen in System Center Configuration Manager](../../protect/deploy-use/windows-hello-for-business-settings.md).

## <a name="configure-windows-hello-for-business-settings-hybrid"></a>Windows Hello voor bedrijven configureren instellingen (hybride)  

1.  Klik in de Configuration Manager-console op **beheer** > **Cloudservices** > **Microsoft Intune-abonnementen**.  

3.  Selecteer uw Microsoft Intune-abonnement in de lijst en klik op het tabblad **Start** in de groep **Abonnement** op **Platforms configureren** > **Windows (MDM)**.  

4.  Kies op het tabblad **Windows Hello voor Bedrijven** van het dialoogvenster **Eigenschappen van Microsoft Intune-abonnement** uit de volgende waarden. Deze waarden worden toegepast op alle ingeschreven Windows 10- en Windows 10 Mobile-apparaten:  

    -   **Windows Hello voor Bedrijven op ingeschreven apparaten uitschakelen** of **Windows Hello voor Bedrijven op ingeschreven apparaten inschakelen** : hiermee schakelt u het gebruik van Windows Hello voor Bedrijven in of uit op alle ingeschreven Windows 10- en Windows 10 Mobile-apparaten.  

    -   **Een TPM (Trusted Platform Module) gebruiken** : een TPM-chip (Trusted Platform Module) biedt een extra gegevensbeveiligingslaag. Kies een van de volgende waarden:  

        -   **Vereist** (standaard): alleen apparaten met een toegankelijke TPM kunnen Windows Hello voor Bedrijven inrichten.  

        -   **Voorkeur** : apparaten proberen eerst een TPM te gebruiken. Als deze niet beschikbaar is, kunnen ze softwareversleuteling gebruiken  

    -   **Minimumlengte voor pincode vereisen** : geef het minimum aantal tekens op dat is vereist voor de pincode van Windows Hello voor Bedrijven. Gebruik ten minste vier tekens (de standaardwaarde is zes tekens).  

    -   **Maximumlengte voor pincode vereisen** : geef het maximum aantal tekens op dat is toegestaan voor de pincode van Windows Hello voor Bedrijven. U kunt maximaal 127 tekens gebruiken.  

    -   **Kleine letters in pincode vereisen** : hiermee geeft u op of kleine letters moeten worden gebruikt in de pincode van Windows Hello voor Bedrijven. U kunt kiezen uit:  

        -   **Toegestaan** : gebruikers mogen kleine letters gebruiken in hun pincode.  

        -   **Vereist** : gebruikers moeten ten minste één kleine letter opnemen in hun pincode.  

        -   **Niet toegestaan** (standaard): gebruikers mogen geen kleine letters gebruiken in hun pincode.  

    -   **Hoofdletters in pincode vereisen** : hiermee geeft u op of hoofdletters moeten worden gebruikt in de pincode van Windows Hello voor Bedrijven. U kunt kiezen uit:  

        -   **Toegestaan** : gebruikers mogen hoofdletters gebruiken in hun pincode.  

        -   **Vereist** : gebruikers moeten ten minste één hoofdletter opnemen in hun pincode.  

        -   **Niet toegestaan** (standaard): gebruikers mogen geen hoofdletters gebruiken in hun pincode.  

    -   **Speciale tekens vereisen** : hiermee geeft u op of speciale tekens moeten worden gebruikt in de pincode. U kunt kiezen uit:  

        -   **Toegestaan** : gebruikers mogen speciale tekens gebruiken in hun pincode.  

        -   **Vereist** : gebruikers moeten ten minste één speciaal teken opnemen in hun pincode.  

        -   **Niet toegestaan** (standaard): gebruikers mogen geen speciale tekens gebruiken in hun pincode (dit is ook het gedrag als de instelling niet wordt geconfigureerd).  

         Tot de speciale tekens behoren: **! " # $ % & ' ( ) \* + , - . / : ; < = > ? @ [ \ ] ^ _ ` { &#124; } ~**.  

    -   **Aflopen van pincode vereisen (dagen)**: hiermee geeft u het aantal dagen op voordat de pincode van het apparaat moet worden gewijzigd. De standaardwaarde is 41 dagen.  

    -   **Hergebruik van vorige pincodes voorkomen** : met deze instelling kunt u het hergebruik van eerder gebruikte pincodes beperken. De standaardwaarde is dat de laatste 5 gebruikte pincodes niet opnieuw kunnen worden gebruikt.  

    -   **Biometrische gebaren inschakelen** : hiermee kunt u biometrische verificatie, zoals gezichtsherkenning of een vingerafdruk, inschakelen als alternatief voor een pincode voor Windows Hello voor Bedrijven. Gebruikers moeten toch een pincode voor Passport for Work configureren voor het geval dat biometrische verificatie mislukt.  

         Als deze optie is ingesteld op **Ingeschakeld**, is biometrische verificatie toegestaan in Windows Hello voor Bedrijven.  Als u deze optie instelt op **Uitgeschakeld**, is het gebruik van biometrische verificatie (voor alle accounttypen) niet toegestaan in Windows Hello voor Bedrijven.  

    -   **Uitgebreide anti-spoofing gebruiken, wanneer beschikbaar** : hiermee configureert u of uitgebreide anti-spoofing wordt gebruikt op apparaten die daarvoor ondersteuning bieden.  

         Als u deze optie instelt op **Ingeschakeld**, moeten alle gebruikers anti-spoofing gebruiken voor gezichtskenmerken, indien ondersteund.  

    -   **Remote Passport gebruiken** : als u deze optie instelt op **Ingeschakeld**, kunnen gebruikers een extern Hello voor Bedrijven-paspoort gebruiken als draagbaar secundair apparaat voor verificatie op desktopcomputers. De computer moet zijn toegevoegd aan Azure Active Directory en het secundaire apparaat moet worden geconfigureerd met een pincode voor Windows Hello voor Bedrijven.  

5.  Klik op **OK**als u klaar bent.  

### <a name="see-also"></a>Zie tevens  
 [Beveiligen van gegevens en site-infrastructuur met System Center Configuration Manager](../../protect/understand/protect-data-and-site-infrastructure.md)

 [ID-verificatie met behulp van Windows Hello voor bedrijven beheren](https://technet.microsoft.com/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport).  
