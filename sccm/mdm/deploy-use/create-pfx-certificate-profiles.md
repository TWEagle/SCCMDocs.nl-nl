---
title: Maken van een certificeringsinstantie PFX-certificaatprofielen | Microsoft Docs
description: Informatie over het PFX-bestanden in System Center Configuration Manager gebruiken voor het genereren van gebruikersspecifieke certificaten die ondersteuning van versleutelde gegevensuitwisseling.
ms.custom: na
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d240a836-c49b-49ab-a920-784c062d6748
caps.latest.revision: 5
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: c0d94b8e6ca6ffd82e879b43097a9787e283eb6d
ms.openlocfilehash: 43d8b2217763681be69711fce93c020a65da1cd8
ms.contentlocale: nl-nl
ms.lasthandoff: 08/02/2017

---
# <a name="how-to-create-pfx-certificate-profiles-using-a-certificate-authority"></a>Het maken van een certificeringsinstantie PFX-certificaatprofielen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hier kunt u informatie over het maken van een certificaatprofiel die gebruikmaakt van een certificeringsinstantie (CA) voor referenties.

[Certificaatprofielen](../../protect/deploy-use/introduction-to-certificate-profiles.md) bevat algemene informatie over het maken en configureren van certificaatprofielen. Dit onderwerp worden enkele specifieke informatie over certificaatprofielen die betrekking hebben op het PFX-certificaten.

## <a name="pfx-certificate-profiles"></a>PFX-certificaatprofielen
System Center Configuration Manager kunt u een PFX-certificaatprofiel met referenties die zijn uitgegeven door een certificeringsinstantie maken.  Vanaf versie 1706 kunt u Microsoft of Entrust als uw instantie voor het certificaat.  Wanneer dit wordt geïmplementeerd op apparaten van gebruikers, genereren bestanden personal information exchange (.pfx) gebruikersspecifieke certificaten ter ondersteuning van versleutelde gegevensuitwisseling.

Zie voor informatie over het importeren van referenties van het computercertificaat van bestaande certificaatbestanden [PFX-certificaatprofielen maken door het importeren van certificaatdetails](../../mdm/deploy-use/import-pfx-certificate-profiles.md).

## <a name="create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>Maken en implementeren van een Personal Information Exchange (PFX)-certificaatprofiel  

### <a name="get-started"></a>Aan de slag

1.  Kies in de System Center Configuration Manager-console **activa en naleving**.  
2.  In de **activa en naleving** werkruimte, kiest u **instellingen voor naleving** &gt; **toegang tot bedrijfsbronnen** &gt; **Certificaatprofielen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Certificaatprofiel maken**.

4.  Geef op de pagina **Algemeen** van de wizard **Certificaatprofiel maken** de volgende informatie op:  

    -   **Naam**: Geef een unieke naam voor het certificaatprofiel. U kunt maximaal 256 tekens gebruiken.  

    -   **Beschrijving**: Geef een beschrijving met een van het certificaatprofiel en andere relevante informatie die helpt overzicht bij het identificeren ervan in de System Center Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.  

    -   In **opgeven welk type certificaatprofiel dat u wilt maken**, kies **Personal Information Exchange - PKCS #12 (PFX)-instellingen - maken** en kies vervolgens uw certificeringsinstantie in de vervolgkeuzelijst.  Vanaf versie 1706, kunt u ervoor kiezen **Microsoft** of **Entrust**.

### <a name="select-supported-platforms"></a>Ondersteunde platforms selecteren

De pagina ondersteunde Platforms identificeert de besturingssystemen en apparaten die ondersteuning biedt voor het certificaatprofiel.  

Certificaat profielen ondersteunen mogelijk meerdere besturingssystemen en apparaten, echter, bepaalde besturingssysteem of apparaat combinaties moet mogelijk verschillende instellingen.  In dergelijke gevallen is het raadzaam te maken van verschillende profielen voor elke unieke set van instellingen.  

Vanaf versie 1706 zijn de volgende opties beschikbaar:

- Windows 10
    - Alle Windows 10 (64-bits)
    - Alle Windows 10 (32-bits)
    - Alle Windows 10 Holographic Enterprise en hoger
    - Alle Windows 10 Holographic en hoger
    - Alle Windows 10 Team en hoger
    - Alle Windows 10 Mobile en hoger
- iPhone
- iPad
- Android
- Android for Work

> [!Note]  
> Mac OS/OS x-apparaten worden momenteel niet ondersteund.  

Als er geen andere opties zijn geselecteerd, de **Alles selecteren** selectievakje selecteert alle beschikbare opties.  Wanneer een of meer opties zijn geselecteerd, **Alles selecteren** bestaande selecties worden gewist. 

1.  Selecteer een of meer platforms ondersteund door het certificaatprofiel.

1.  Kies **volgende** om door te gaan.  


### <a name="configure-certification-authorities"></a>Certificeringsinstanties configureren

Hier kunt u het certificaatregistratiepunt (CRP) voor het verwerken van het PFX-certificaten.  

1.  Van de **primaire Site** kiest u de server met de CRP-rol voor de CA.
1.  In de lijst met **certificeringsinstanties**, kiest u de relevante CA door een vinkje in de linkerkolom te plaatsen.
1.  Wanneer u klaar bent om door te gaan, kies **volgende**.

Zie voor meer informatie, [certificaatinfrastructuur](../../protect/deploy-use/certificate-infrastructure.md).


### <a name="configure-certificate-settings-for-microsoft-ca"></a>Certificaatinstellingen voor Microsoft-CA configureren

Certificaatinstellingen configureren bij gebruik van Microsoft als de CA:

1.  Van de **Certificaatsjabloonnaam** vervolgkeuzelijst, kiest u de certificaatsjabloon.

1.  Schakel de **certificaatgebruik** selectievakje voor het certificaatprofiel voor S/MIME-ondertekening of versleuteling.

    Wanneer u deze optie tijdens het gebruik van Microsoft als de CA inschakelt, worden alle PFX-certificaten die zijn gekoppeld aan de doelgebruiker afgeleverd bij alle apparaten die zijn geregistreerd door de gebruiker.  Wanneer dit selectievakje ingeschakeld is, ontvangt elk apparaat een uniek certificaat.  

1.  Stel **indeling van de onderwerpnaam** naar elk **algemene naam** of **volledig-DN-naam**.  Als u niet zeker te gebruiken, neem contact op met de beheerder van de certificaat.

1.  Voor **alternatieve onderwerpnaam**, schakel de **e-mailadres** en **principe (User Principal name)** afhankelijk van wat geschikt is voor uw CA.

1.  **Drempelwaarde voor verlenging** bepaalt wanneer certificaten worden automatisch vernieuwd, op basis van het percentage tijd resteert voordat het verloopt.

1.  Stel de **geldigheidsduur van certificaat** op de levensduur van het certificaat.  De periode is opgegeven door het instellen van een getal (1-100) en de periode (jaar, maanden of dagen).

1.  De **Active Directory-publicatie** wordt ingeschakeld wanneer het certificaatregistratiepunt Active Directory-referenties geeft.  Schakel de optie voor het publiceren van het certificaatprofiel in Active Directory.

1.  Als u een of meer Windows 10-platforms hebt geselecteerd bij het opgeven van ondersteunde platforms:

    1.  Stel **Windows-certificaatarchief** naar **gebruiker**.  (De **lokale Computer** keuze implementeert geen certificaten en niet moeten worden gekozen.)
    1.  Selecteer de **Sleutelarchiefprovider (KSP)** van een van de volgende opties:

        - **Installeren op TPM (Trusted Platform Module) indien aanwezig**  
        - **Installeren op TPM (Trusted Platform Module), anders niet installeren** 
        - **Naar Windows Hello voor bedrijven, anders niet installeren** 
        - **Installeren op sleutelarchiefprovider van software** 

1.  Wanneer u klaar bent, kiest **volgende** of **samenvatting**.

### <a name="configure-certificate-settings-for-entrust-ca"></a>Certificaatinstellingen voor Entrust CA configureren

Voor het configureren van belasten instellingen van het certificaat bij gebruik van als de CA:

1.  Van de **digitale ID configuratie** vervolgkeuzelijst, kiest u het configuratieprofiel.  De digitale ID configuratieopties zijn gemaakt door de beheerder Entrust.

1.  Wanneer dit selectievakje inschakelt, de **certificaatgebruik** gebruikmaakt van het certificaatprofiel voor S/MIME-ondertekening of versleuteling.

    Wanneer u Entrust als de CA gebruikt, worden alle PFX-certificaten die zijn gekoppeld aan de doelgebruiker afgeleverd bij alle apparaten die zijn geregistreerd door de gebruiker.    Wanneer deze optie is *niet* dit selectievakje inschakelt, ontvangt elk apparaat een uniek certificaat.  (Zie voor meer informatie, de overeenkomstige sectie; gedrag voor verschillende CA's wordt gewijzigd.)

1.  Gebruik de **indeling** knop toewijzen Entrust **indeling van de onderwerpnaam** tokens aan de ConfigMgr-velden.  

    De **certificaat naam opmaak** dialoogvenster geeft een lijst van de variabelen van de configuratie van digitale ID belasten.  Kies de juiste LDAP-variabele van de bijbehorende vervolgkeuzelijst voor elke variabele Entrust.

1.  Gebruik de **indeling** knop toewijzen Entrust **alternatieve naam voor onderwerp** tokens voor ondersteunde LDAP-variabelen.  

    De **certificaat naam opmaak** dialoogvenster geeft een lijst van de variabelen van de configuratie van digitale ID belasten.  Kies de juiste LDAP-variabele van de bijbehorende vervolgkeuzelijst voor elke variabele Entrust.

1.  **Drempelwaarde voor verlenging** bepaalt wanneer certificaten worden automatisch vernieuwd, op basis van het percentage tijd resteert voordat het verloopt.

1.  Stel de **geldigheidsduur van certificaat** op de levensduur van het certificaat.  De periode is opgegeven door het instellen van een getal (1-100) en de periode (jaar, maanden of dagen).

1.  De **Active Directory-publicatie** wordt ingeschakeld wanneer het certificaatregistratiepunt Active Directory-referenties geeft.  Schakel de optie voor het publiceren van het certificaatprofiel in Active Directory.

1.  Als u een of meer Windows 10-platforms hebt geselecteerd bij het opgeven van ondersteunde platforms:

    1.  Stel **Windows-certificaatarchief** naar **gebruiker**.  (De **lokale Computer** keuze implementeert geen certificaten en niet moeten worden gekozen.)
    1.  Selecteer de **Sleutelarchiefprovider (KSP)** van een van de volgende opties:

        - **Installeren op TPM (Trusted Platform Module) indien aanwezig**  
        - **Installeren op TPM (Trusted Platform Module), anders niet installeren** 
        - **Naar Windows Hello voor bedrijven, anders niet installeren** 
        - **Installeren op sleutelarchiefprovider van software** 

1.  Wanneer u klaar bent, kiest **volgende** of **samenvatting**.


### <a name="finish-up"></a>Voltooien

1.  Controleer uw selecties en controleer of uw keuzes van de pagina overzicht.

1.  Wanneer u klaar bent, kiest u **volgende** om het profiel te maken.  

1.  Het certificaatprofiel met het PFX-bestand is nu beschikbaar via de werkruimte **Certificaatprofielen** . 

1.  Het profiel kan implementeren:

    1. Open de **activa en naleving** werkruimte.
    1. Kies **instellingen voor naleving** > **toegang tot bedrijfsbronnen** > **Certificaatprofielen**
    1. Met de rechtermuisknop op het gewenste profiel en kies vervolgens **implementeren**. 


## <a name="see-also"></a>Zie tevens
[Maak een nieuw certificaatprofiel](../../protect/deploy-use/create-certificate-profiles.md) wordt u begeleid bij de Wizard Certificaatprofiel maken.

[Het PFX-certificaatprofielen maken door het importeren van certificaatdetails](../../mdm/deploy-use/import-pfx-certificate-profiles.md)

[Wi-Fi, VPN, e-mail en certificaatprofielen implementeren](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) wordt beschreven hoe u certificaatprofielen implementeert.
