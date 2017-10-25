---
title: PFX-certificaatprofielen maken door het importeren van certificaatdetails | Microsoft Docs
description: Informatie over het PFX-bestanden in System Center Configuration Manager gebruiken voor het genereren van gebruikersspecifieke certificaten die ondersteuning van versleutelde gegevensuitwisseling.
ms.custom: na
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3bb3e13-3037-4122-93bc-504bfd080a4d
caps.latest.revision: "5"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: c8346d04c7cd9761291824f5d30f09fab9acbcf9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-pfx-certificate-profiles-by-importing-certificate-details"></a>Het PFX-certificaatprofielen maken door het importeren van certificaatdetails

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Hier kunt u informatie over het maken van een certificaatprofiel door het importeren van de referenties van externe certificaten.  

[Certificaatprofielen](../../protect/deploy-use/introduction-to-certificate-profiles.md) Geef algemene informatie over het maken en certificaatprofielen configureren. Dit onderwerp worden enkele specifieke informatie over certificaatprofielen die betrekking hebben op het PFX-certificaten.

-  Configuration Manager tal van certificaatarchieven geschikt is voor verschillende apparaten en besturingssystemen.  Deze omvatten:

 -   iOS en Mac OS/OS x
 -   Android- en Android for Work.
 -   Windows 10, met inbegrip van Windows 10 mobile.

Zie voor meer informatie, [profiel vereisten van het certificaat](../../protect/plan-design/prerequisites-for-certificate-profiles.md).

## <a name="pfx-certificate-profiles"></a>PFX-certificaatprofielen
System Center Configuration Manager kunt u referenties van het computercertificaat importeren en vervolgens inrichten van bestanden van de personal information exchange (.pfx) op apparaten van gebruikers. PFX-bestanden kunnen worden gebruikt om gebruikersspecifieke certificaten te maken ter ondersteuning van versleutelde gegevensuitwisseling.

> [!TIP]  
>  Een stapsgewijze beschrijving van dit proces is te vinden in [How to Create and Deploy PFX Certificate Profiles in Configuration Manager](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx)(Engelstalig).  

## <a name="create-import-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>Maken, importeren en een persoonlijke informatie Exchange (PFX)-certificaatprofiel implementeren  

### <a name="get-started"></a>Aan de slag

1.  Klik in de System Center Configuration Manager-console op **activa en naleving**.  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit, vouw vervolgens **Toegang tot bedrijfsbronnen**uit en klik op **Certificaatprofielen**.  

3.  Klik op **Certificaatprofiel maken** in het tabblad **Start** in de groep **Maken**.

4.  Geef op de pagina **Algemeen** van de wizard **Certificaatprofiel maken** de volgende informatie op:  

    -   **Naam**: Geef een unieke naam voor het certificaatprofiel. U kunt maximaal 256 tekens gebruiken.  

    -   **Beschrijving**: Geef een beschrijving met een van het certificaatprofiel en andere relevante informatie die helpt overzicht bij het identificeren ervan in de System Center Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.  

    -   **Geef het type certificaatprofiel dat u wilt maken**: Kies een van de volgende opties voor PFX-certificaten:  

        -   **Instellingen voor persoonlijke informatie Exchange PKCS #12 (PFX) - Import**: Maakt een certificaatprofiel door programmatisch importeren van gegevens van bestaande certificaten gebruiken.  

        -   **Personal Information Exchange - PKCS #12 (PFX)-instellingen - maken**: Maakt een PFX-certificaatprofiel met referenties die worden geleverd door een certificeringsinstantie.  Zie voor meer informatie, [het maken van een certificeringsinstantie PFX-certificaatprofielen](../../mdm/deploy-use/create-pfx-certificate-profiles.md).


### <a name="create-a-pfx-certificate-profile-for-the-imported-credentials"></a>Een PFX-certificaatprofiel voor de geïmporteerde referenties maken

Als u wilt importeren in een PFX-certificaat, kunt u de Configuration Manager-SDK gebruiken voor het implementeren van een script voor PFX maken. 

Geïmporteerde certificaten worden later ingeschreven apparaten geïmplementeerd.

1. Op de **PFX-certificaat** pagina van de **Wizard Certificaatprofiel maken**, waar het apparaat-sleutelarchiefprovider opgeven:
    -   **Installeren op TPM (Trusted Platform Module) indien aanwezig**  
    -   **Installeren op TPM (Trusted Platform Module), anders niet installeren** 
    -   **Naar Windows Hello voor bedrijven, anders niet installeren** 
    -   **Installeren op sleutelarchiefprovider van software** 
2. Klik op **Volgende**. 
3. Op de **ondersteunde Platforms** pagina van de wizard, de ondersteunde apparaatplatforms te kiezen en klik vervolgens op **volgende**.

### <a name="finish-the-profile"></a>Het profiel voltooien

1.  Klik op **Volgende**, bekijk de pagina **Samenvatting** en sluit de wizard.  
2.  Het certificaatprofiel met het PFX-bestand is nu beschikbaar via de werkruimte **Certificaatprofielen** . 
3.  Voor het implementeren van het profiel de **activa en naleving** werkruimte open **instellingen voor naleving** > **toegang tot bedrijfsbronnen** > **Certificaatprofielen**, met de rechtermuisknop op het certificaat dat u wilt en klik vervolgens op **implementeren**. 

### <a name="deploy-a-create-pfx-script"></a>Implementeren van een Script voor PFX maken

Gebruik de [Configuration Manager SDK](http://go.microsoft.com/fwlink/?LinkId=613525) voor het implementeren van een Script voor PFX maken. 

Het script voor PFX maken dat is toegevoegd in Configuration Manager 2012 SP2 voegt de klasse SMS_ClientPfxCertificate toe aan de SDK. Deze klasse omvat de volgende methoden:  

    -   `ImportForUser`  

    -   `DeleteForUser`  

Het volgende voorbeeld importeert referenties in een PFX-certificaatprofiel.

``` powershell
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

Update de volgende scriptvariabelen voor het gebruik van dit voorbeeld:  

   -   **BLOB**\-de PFX-blob base64-versleuteling  
   -   **$Password** -het wachtwoord voor het PFX-bestand  
   -   **$ProfileName** -de naam van het PFX-profiel  
   -   **Computernaam** -naam van de hostcomputer   

## <a name="see-also"></a>Zie tevens
[Maak een nieuw certificaatprofiel](../../protect/deploy-use/create-certificate-profiles.md) wordt u begeleid bij de Wizard Certificaatprofiel maken.

[Het PFX-certificaatprofielen maken door het importeren van certificaatdetails](../../mdm/deploy-use/create-pfx-certificate-profiles.md)

[Wi-Fi, VPN, e-mail en certificaatprofielen implementeren](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) weergeven voor het implementeren van certificaatprofielen worden beschreven.