---
title: PFX-certificaatprofielen maken | Microsoft-documenten
description: Informatie over het PFX-bestanden in System Center Configuration Manager gebruiken voor het genereren van certificaten gebruikersspecifieke die ondersteuning bieden voor het uitwisselen van versleutelde gegevens.
ms.custom: na
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3bb3e13-3037-4122-93bc-504bfd080a4d
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26feb0b166beb7e48cb800a5077d00dbc3eec51a
ms.openlocfilehash: 27435316c6e47531ff989bc8956ca0c874131a0e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-pfx-certificate-profiles-in-system-center-configuration-manager"></a>Het PFX-certificaatprofielen maken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Certificaatprofielen werken met Active Directory Certificate Services en de Network Device Enrollment Service-rol om verificatiecertificaten te richten voor beheerde apparaten, zodat gebruikers naadloos toegang krijgen bedrijfsbronnen tot. Zo kunt u bijvoorbeeld certificaatprofielen maken en implementeren om gebruikers de benodigde certificaten te geven om VPN-verbindingen en draadloze verbindingen te initiëren.

[Certificaatprofielen](../../protect/deploy-use/introduction-to-certificate-profiles.md) bevat algemene informatie over het maken en configureren van certificaatprofielen. Dit onderwerp worden enkele specifieke informatie over certificaatprofielen die betrekking hebben op het PFX-certificaten.

-  Configuration Manager ondersteunt de implementatie van certificaten in verschillende certificaatarchieven, afhankelijk van de vereisten, het apparaattype en besturingssysteem. De volgende apparaten worden ondersteund wanneer ze zijn ingeschreven bij Intune:

 -   iOS  

- Raadpleeg voor andere vereisten [profiel vereisten van het certificaat](../../protect/plan-design/prerequisites-for-certificate-profiles.md).

## <a name="pfx-certificate-profiles"></a>PFX-certificaatprofielen
System Center Configuration Manager kunt importeren en vervolgens exchange (.pfx) bestanden met persoonlijke gegevens op de Gebruikersapparaten in te richten. PFX-bestanden kunnen worden gebruikt om gebruikersspecifieke certificaten te maken ter ondersteuning van versleutelde gegevensuitwisseling.

> [!TIP]  
>  Een stapsgewijze beschrijving van dit proces is te vinden in [How to Create and Deploy PFX Certificate Profiles in Configuration Manager](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx)(Engelstalig).  

## <a name="create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>Maken en implementeren van een certificaatprofiel persoonlijke informatie Exchange (PFX)  

### <a name="get-started"></a>Aan de slag

1.  Klik in de System Center Configuration Manager-console op **activa en naleving**.  

2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit, vouw vervolgens **Toegang tot bedrijfsbronnen**uit en klik op **Certificaatprofielen**.  

3.  Klik op **Certificaatprofiel maken** in het tabblad **Start** in de groep **Maken**.

4.  Geef op de pagina **Algemeen** van de wizard **Certificaatprofiel maken** de volgende informatie op:  

    -   **Naam**: Geef een unieke naam voor het certificaatprofiel. U kunt maximaal 256 tekens gebruiken.  

    -   **Beschrijving**: Geef een beschrijving met een overzicht van het certificaatprofiel en andere relevante informatie die helpt bij het identificeren ervan in de System Center Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.  

    -   **Geef op welk type certificaatprofiel dat u wilt maken**: Kies voor PFX-certificaten:  

        -   **Instellingen voor persoonlijke informatie Exchange PKCS #12 (PFX) - Import**: Selecteer deze optie om een PFX-certificaat te importeren.  
       

### <a name="import-a-pfx-certificate"></a>Een PFX-certificaat importeren

Als u wilt een PFX-certificaat hebt geïmporteerd, moet u de Configuration Manager-SDK. De certificaten die u voor een gebruiker importeert worden geïmplementeerd voor alle apparaten waarmee de gebruiker.

1. Op de **PFX-certificaat** pagina van de **Wizard Certificaatprofiel maken**, opgeven waar het certificaat wordt opgeslagen op apparaten waarop u hem implementeren:
    -     **Installeren op TPM (Trusted Platform Module) indien aanwezig**  
    -   **Installeren op TPM (Trusted Platform Module), anders niet installeren** 
    -   **Naar Windows Hello voor zakelijke anders niet installeren** 
    -   **Installeren op sleutelarchiefprovider van software** 
2. Klik op **Volgende**. 
3. Op de **ondersteunde Platforms** pagina van de wizard, kies de apparaatplatforms waarop dit certificaat wordt geïnstalleerd en klik vervolgens op **volgende**.
4. Met behulp van de SDK voor Windows 8.1, die beschikbaar is via het Downloadcentrum ([http://go.microsoft.com/fwlink/?LinkId=613525](http://go.microsoft.com/fwlink/?LinkId=613525)), implementeert u een script voor PFX maken. Het script voor PFX maken dat is toegevoegd in Configuration Manager 2012 SP2 voegt de klasse SMS_ClientPfxCertificate toe aan de SDK. Deze klasse omvat de volgende methoden:  

    -   ImportForUser  

    -   DeleteForUser  

     Voorbeeld van een script:  

```  
    $EncryptedPfxBlob = "<blob>"  
    $Password = "abc"  
    $ProfileName = "PFX_Profile_Name"  
    $UserName = "ComputerName\Administrator"  

    #New pfx  
    $WMIConnection = ([WMIClass]"\\nksccm\root\SMS\Site_MDM:SMS_ClientPfxCertificate")  
        $NewEntry = $WMIConnection.psbase.GetMethodParameters("ImportForUser")  
        $NewEntry.EncryptedPfxBlob = $EncryptedPfxBlob  
        $NewEntry.Password = $Password  
        $NewEntry.ProfileName = $ProfileName  
        $NewEntry.UserName = $UserName  
    $Resource = $WMIConnection.psbase.InvokeMethod("ImportForUser",$NewEntry,$null)  

```  

De volgende scriptvariabelen moeten worden gewijzigd voor uw script:  

   -   blob\ = het PFX-blob met base64 gecodeerd  
   -   $Password = Het wachtwoord van het PFX-bestand  
   -   $ProfileName = De naam van het PFX-profiel  
   -   ComputerName = Naam van de hostcomputer   



### <a name="finish-up"></a>Voltooien van

1.  Klik op **Volgende**, bekijk de pagina **Samenvatting** en sluit de wizard.  
2.  Het certificaatprofiel met het PFX-bestand is nu beschikbaar via de werkruimte **Certificaatprofielen** . 
3.  Voor het implementeren van het profiel de **activa en naleving** werkruimte open **compatibiliteitsinstellingen** > **toegang tot bedrijfsbronnen** > **Certificaatprofielen**, met de rechtermuisknop op het certificaat dat u wilt en klik vervolgens op **implementeren**. 



## <a name="see-also"></a>Zie tevens
[Maak een nieuw certificaatprofiel](../../protect/deploy-use/create-certificate-profiles.md#create-a-new-certificate-profile) leidt u door de Wizard Certificaatprofiel maken.

[Wi-Fi, VPN-, e-mail en certificaatprofielen implementeren](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) bevat informatie over het implementeren van certificaatprofielen.
