---
title: Het maken van SCEP-certificaatprofielen | Microsoft Docs
description: Informatie over het gebruiken van certificaatprofielen voor het inrichten van beheerde apparaten met de certificaten die ze nodig hebben in System Center Configuration Manager.
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 634d612c-92d7-4c03-873a-b2e730c9a72d
caps.latest.revision: "16"
caps.handback.revision: "0"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 1e00804d27ecef2aadd8bfa395db1919c46243ee
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="create-certificate-profiles"></a>Certificaatprofielen maken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Gebruik certificaatprofielen in Configuration Manager (SCCM) voor het inrichten van beheerde apparaten met de certificaten die ze nodig hebben voor toegang tot bedrijfsresources. Voordat u certificaatprofielen maakt, instellen van de certificaatinfrastructuur zoals beschreven in [certificaatinfrastructuur voor System Center Configuration Manager instellen](certificate-infrastructure.md).  

Dit onderwerp wordt beschreven hoe u vertrouwde basiscertificaten en SCEP-certificaatprofielen maken. Als u wilt een PFX-certificaatprofielen maken, Zie [maken PFX-certificaatprofielen](../../protect/deploy-use/create-pfx-certificate-profiles.md).

Een certificaatprofiel maken:

1.  Start de Wizard Certificaatprofiel maken.
1.  Geef algemene informatie over het certificaat.
1.  Een vertrouwd certificaat-certificeringsinstantie (CA) configureren.  
1.  Configureer de gegevens van SCEP-certificaat (alleen voor SCEP-certificaten).  
1.  Ondersteunde platforms voor het certificaatprofiel opgeven.


## <a name="start-the-create-certificate-profile-wizard"></a>Start de wizard Certificaatprofiel maken  

1.  Klik in de System Center Configuration Manager-console op **activa en naleving**.  

2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit, vouw vervolgens **Toegang tot bedrijfsbronnen**uit en klik op **Certificaatprofielen**.  

3.  Klik op **Certificaatprofiel maken** in het tabblad **Start** in de groep **Maken**.  

## <a name="provide-general-information-about-the-certificate-profile"></a>Geef algemene informatie over het certificaatprofiel  

Geef op de pagina **Algemeen** van de wizard Certificaatprofiel maken de volgende informatie op:  

-   **Naam**: Geef een unieke naam voor het certificaatprofiel. U kunt maximaal 256 tekens gebruiken.  

-   **Beschrijving**: Geef een beschrijving met een van het certificaatprofiel en andere relevante informatie die helpt overzicht bij het identificeren ervan in de System Center Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.  

-   **Geef het type certificaatprofiel dat u wilt maken**: Kies een van de volgende certificaatprofieltypen:  

-   **Vertrouwd CA-certificaat**: Selecteer dit certificaatprofieltype als u wilt implementeren van een vertrouwde basiscertificeringsinstantie (CA) of tussenliggend CA-certificaat naar een certificaatvertrouwensketen te vormen wanneer de gebruiker of het apparaat een ander apparaat moet verifiëren. Het apparaat zou bijvoorbeeld een Remote Authentication Dial-In User Service (RADIUS)-server of een virtueel particulier netwerk (VPN)-server kunnen zijn. U moet ook een vertrouwd CA-certificaatprofiel configureren voordat u een SCEP-certificaatprofiel kunt maken. In dit geval moet het vertrouwde CA-certificaat het vertrouwde basiscertificaat zijn voor de CA die het certificaat aan de gebruiker of het apparaat zal verlenen.  

-   **Instellingen voor Simple Certificate Enrollment Protocol (SCEP)**: Selecteer dit certificaatprofieltype als u een certificaat aanvragen voor een gebruiker of apparaat wilt, met behulp van het Simple Certificate Enrollment Protocol en de functieservice registratieservice voor netwerkapparaten.

-   **Instellingen voor persoonlijke informatie Exchange PKCS #12 (PFX) - Import**: Selecteer deze optie om een PFX-certificaat te importeren. Voor meer informatie over het maken van PFX-certificaat Zie [importeren PFX-certificaatprofielen](/sccm/mdm/deploy-use/import-pfx-certificate-profiles.md).

-   **Instellingen voor persoonlijke informatie Exchange PKCS #12 (PFX) - maken**: Selecteer deze optie voor het verwerken van PFX-certificaten met behulp van een certificeringsinstantie. Voor meer informatie over het maken van PFX-certificaat Zie [maken PFX-certificaatprofielen](/sccm/mdm/deploy-use/create-pfx-certificate-profiles.md).


## <a name="configure-a-trusted-ca-certificate"></a>Een vertrouwd CA-certificaat configureren  

> [!IMPORTANT]  
>  U moet minstens één vertrouwd CA-certificaatprofiel configureren voordat u een SCEP-certificaatprofiel kunt maken.    
>  
>  Als u een van deze waarden wijzigen nadat het certificaat wordt geïmplementeerd op een nieuw wordt certificaat aangevraagd:
>  -  Opslag van sleutels opgeven
>  -  De naam van certificaatsjabloon
>  -  Certificaattype
>  -  Indeling van de onderwerpnaam
>  -  Alternatieve onderwerpnaam
>  -  Geldigheidsduur van certificaat
>  -  Sleutelgebruik
>  -  Sleutelgrootte
>  -  Uitgebreide-sleutelgebruik
>  -  CA-basiscertificaat

1.  Geef op de pagina **Vertrouwd CA-certificaat** van de wizard Certificaatprofiel maken de volgende informatie op:  

 -   **Certificaatbestand**: Klik op **importeren** en blader vervolgens naar het certificaatbestand dat u wilt gebruiken.  

 -   **Doelarchief**: Voor apparaten met meer dan één certificaatarchief selecteert u waar het certificaat wilt opslaan. Voor apparaten die slechts één archief hebben, wordt deze instelling wordt genegeerd.  

2.  Gebruik de **Vingerafdruk van het certificaat** om te verifiëren dat u het juiste certificaat hebt geïmporteerd.  


## <a name="configure-scep-certificate-information-only-for-scep-certificates"></a>Gegevens van SCEP-certificaat (alleen voor SCEP-certificaten) configureren  

1.  Op de pagina **SCEP-servers** van de wizard Certificaatprofiel maken geeft u de URL's op voor de NDES-servers die via SCEP certificaten uitgeven. U kunt ervoor kiezen om automatisch een NDES-URL toe te wijzen op basis van de configuratie van de sitesysteemserver voor het Certificaatregistratiepunt of URL's handmatig toevoegen.  

2.  Voltooi de **SCEP-registratie** pagina van de Wizard Certificaatprofiel maken.

 -  **Nieuwe pogingen**: Geef het aantal keren dat het apparaat wordt automatisch opnieuw geprobeerd de certificaataanvraag naar de server waarop de Network Device Enrollment Service wordt uitgevoerd. Deze instelling ondersteunt het scenario waarbij een CA-manager een certificaataanvraag moet goedkeuren voordat het wordt geaccepteerd. Deze instelling wordt doorgaans gebruikt voor sterk beveiligde omgevingen of als u een zelfstandige verlenende CA en geen bedrijfs-CA hebt. U kunt deze instelling mogelijk ook gebruiken voor testdoeleinden zodat u de certificaataanvraagopties kunt inspecteren alvorens de verlenende CA de certificaataanvraag verwerkt. Gebruik deze instellingen met de instelling **Tijd tussen pogingen (minuten)** .  

 -   **Tijd tussen elke poging (minuten)**: Geef het interval in minuten, tussen elke registratiepoging wanneer u goedkeuring van de CA-manager gebruikt voordat het verlenende CA de certificaataanvraag verwerkt. Als u beheergoedkeuring gebruikt voor testdoeleinden, zult u waarschijnlijk een lage waarde willen opgeven ,zodat u niet lang te hoeft wachten voordat het apparaat de certificaataanvraag opnieuw probeert nadat u de aanvraag goedkeurt. Als u echter beheergoedkeuring op een productienetwerk gebruikt, zult u waarschijnlijk een hogere waarde willen opgeven om voldoende tijd te geven aan de CA-beheerder om aangevraagde goedkeuringen toe te staan of te weigeren.  

 -   **Drempelwaarde voor verlenging (%)**: Geef het percentage van de levensduur van het certificaat dat voordat het apparaat verlenging van het certificaat aanvraagt resteert.  

 -   **Sleutelarchiefprovider (KSP)**: Geef op waar de sleutel voor het certificaat wordt opgeslagen. Kies een van de volgende waarden:  

   -   **Installeren in Trusted Platform Module (TPM), indien aanwezig**: De sleutel in de TPM geïnstalleerd. Als de TPM niet aanwezig is, wordt de sleutel geïnstalleerd in de archiefprovider voor de softwaresleutel.  

   -   **Installeren in Trusted Platform Module (TPM), anders niet**: De sleutel in de TPM geïnstalleerd. De installatie mislukt als de TPM-module niet aanwezig is.  

   -   **Installatie op Windows Hello voor bedrijven, anders niet**: Deze optie is beschikbaar voor Windows 10 Desktop en Mobile-apparaten. De sleutel aan wordt geregistreerd **Windows Hello voor bedrijven**, beschreven in [Windows Hello voor bedrijven-instellingen in System Center Configuration Manager](../../protect/deploy-use/windows-hello-for-business-settings.md). Met deze optie kunt u ook opgeven dat **Meervoudige verificatie vereisen** geldt tijdens de registratie van apparaten voordat certificaten naar die apparaten worden uitgegeven. Zie [Windows-apparaten beveiligen met meervoudige verificatie](https://technet.microsoft.com/library/dn889751.aspx) voor meer informatie.

   > [!NOTE]  
   > 
   > Wanneer een gebruiker een Windows Hello voor bedrijven PINCODE maakt, verzendt Windows een melding die wordt herkend door Configuration Manager voor. Hierdoor kan Configuration Manager te snel worden op de hoogte welke gebruikers een Windows Hello PINCODE hebt gemaakt. Configuration Manager stuurt nieuwe certificaten voor deze gebruikers als Windows Hello wordt gebruikt als de Sleutelarchiefprovider in een certificaatprofiel.  

   -   **Installeren naar Sleutelarchiefprovider van Software**: De sleutel in de archiefprovider voor de softwaresleutel geïnstalleerd.  

 -   **Apparaten voor certificaatinschrijving**: Als het certificaatprofiel wordt geïmplementeerd op een Gebruikersverzameling, selecteren of toegestaan om certificaatregistratie alleen primaire apparaat met de gebruiker of op alle apparaten waarop de gebruiker zich aanmeldt. Als het certificaatprofiel wordt geïmplementeerd naar een apparaatsverzameling, dient u te selecteren of het is toegestaan om certificaatregistratie alleen voor de primaire gebruiker of voor alle gebruikers van het apparaat uit te voeren.  

3.  Geef op de pagina **Certificaateigenschappen** van de wizard Certificaatprofiel maken de volgende informatie op:  

 -   **Certificaatsjabloonnaam**: Klik op **Bladeren** de naam van een certificaatsjabloon die de Network Device Enrollment Service is geconfigureerd voor gebruik en die is toegevoegd aan een verlenende CA selecteren. Om te kunnen bladeren certificaatsjablonen, moet de gebruikersaccount die u gebruikt voor het uitvoeren van de System Center Configuration Manager-console leesmachtiging voor de certificaatsjabloon hebben. Als u **Bladeren**echter niet kunt gebruiken, typ dan de naam van het certificaatsjabloon.  

 > [!IMPORTANT]
 >   
 >  Het certificaat zal niet worden geïmplementeerd als de naam van het certificaatsjabloon niet-ASCII-tekens bevat (bijvoorbeeld teken van het Chinese alfabet). U kunt ervoor zorgen dat het certificaat wordt geïmplementeerd door eerst een kopie te maken van het certificaatsjabloon op de CA en de kopie een nieuwe naam te geven met alleen ASCII-tekens.  

   Let op het volgende, afhankelijk of u bladert naar het certificaatsjabloon of u de certificaatnaam invoert:  

 -   Als u bladert om de naam van het certificaatsjabloon te selecteren, worden sommige velden op de pagina automatisch vanaf het certificaatsjabloon ingevuld. In sommige gevallen is het niet mogelijk deze waarden te wijzigen, tenzij u een ander certificaatsjabloon selecteert.  

 -   Als u de naam van het certificaatsjabloon invoert, dient u ervoor te zorgen dat de naam exact overeenkomt met een van de certificaatsjablonen die zijn vermeld in het register van de server waarop de registratieservice van netwerkapparaten wordt uitgevoerd. Zorg ervoor dat u de naam opgeeft van het certificaatsjabloon en niet de weergavenaam van het certificaatsjabloon.  

   Als u de namen van certificaatsjablonen zoekt, gaat u naar de volgende sleutel: Hkey_local_machine\software\microsoft\cryptography\mscep bij te. De certificaatsjablonen worden hier vermeld als de waarden voor **EncryptionTemplate**, **GeneralPurposeTemplate**en **SignatureTemplate**. Standaard is **IPSECIntermediateOffline**de waarde voor deze drie certificaatsjablonen. Dit verwijst naar de sjabloonweergavenaam **IPSec (Offline-aanvraag)**.  

   > [!WARNING]  
   > 
   >  Omdat System Center Configuration Manager de inhoud van het certificaatsjabloon niet controleren kan als u de naam van het certificaatsjabloon plaats bladeren, is het mogelijk dat u opties die het certificaatsjabloon biedt geen ondersteuning voor en die resulteert in een mislukte certificaataanvraag kunt selecteren. Als dit gebeurt, ziet u een foutmelding voor w3wp.exe in het bestand CPR.log met het bericht dat de sjabloonnaam van het Certificate Signing Request (CSR) en de invoer niet overeenkomen.  
   >   
   >  Als u de naam van het certificaatsjabloon invoert dat is opgegeven voor de waarde **GeneralPurposeTemplate** , dient u de opties **Sleutelcodering** en de **Digitale handtekening** voor dit certificaatprofiel te selecteren. Als u echter alleen de optie **Sleutelcodering** in dit certificaatprofiel wilt inschakelen, dient u de naam van het certificaatsjabloon op te geven voor de sleutel **EncryptionTemplate** . Op dezelfde manier dient u, als u alleen de optie **Digitale handtekening** in dit certificaatprofiel wilt inschakelen, de naam van het certificaatsjabloon op te geven voor de sleutel **SignatureTemplate** .  

 -   **Certificaattype**: Selecteer of het certificaat zal worden geïmplementeerd op een apparaat of een gebruiker.  
 -   **Indeling van de onderwerpnaam**: Selecteer in de lijst hoe System Center Configuration Manager automatisch de onderwerpnaam in de certificaataanvraag maakt. Als het certificaat voor een gebruiker is, kunt u ook het e-mailadres van de gebruiker in de onderwerpnaam opnemen. 
    
   > [!NOTE]  
   > 
   > Selecteren **IMEI-nummer** of **serienummer** kunt u onderscheid maken tussen verschillende apparaten die eigendom zijn van dezelfde gebruiker. Deze apparaten kunnen bijvoorbeeld een algemene naam, maar niet IMEI-nummer of serienummer delen. Als een IMEI-nummer of het serienummer van het apparaat niet gerapporteerd, wordt het certificaat uitgegeven aan de algemene naam.

 -   **Alternatieve onderwerpnaam**: Geef op hoe System Center Configuration Manager automatisch de waarden voor de alternatieve onderwerpnaam (SAN) in de certificaataanvraag maakt. Als u bijvoorbeeld een gebruikerscertificaattype selecteerde, kunt u de User Principal Name (UPN) gebruiken in de alternatieve naam van het onderwerp.  Als het clientcertificaat zal worden gebruikt om een Network Policy Server te verifiëren, dient u de alternatieve naam van het onderwerp op de UPN in te stellen.  

   > [!NOTE]  
   >  - iOS-apparaten ondersteunen slechts een beperkt aantal indelingen van onderwerpnamen en alternatieve namen van onderwerpen in SCEP-certificaten. Als u een indeling opgeeft die niet wordt ondersteund, zullen er geen certificaten op iOS-apparaten worden geregistreerd. Gebruik de **Algemene naam** voor de **Indeling van de onderwerpnaam**, en de **DNS-naam**, **E-mailadres** of **UPN** voor de **Alternatieve naam voor het onderwerp**als u een SCEP-certificaatprofiel configureert voor implementatie op iOS-apparaten.  

 -   **Geldigheidsduur van certificaat**: Als u hebt de certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE opdracht op de verlenende CA, waarop een aangepaste geldigheidsperiode mogelijk is, kunt u de hoeveelheid resterende tijd voordat het certificaat verloopt. Zie voor meer informatie over deze opdracht [certificaatinfrastructuur in System Center Configuration Manager](../../protect/deploy-use/certificate-infrastructure.md) onderwerp.  

   U kunt een waarde opgeven die lager is dan de geldigheidsperiode in het opgegeven certificaatsjabloon, maar niet hoger. Als de geldigheidsperiode van het certificaat in het certificaatsjabloon bijvoorbeeld twee jaar is, kunt u wel één jaar, maar niet vijf jaar opgeven. De waarde moet ook lager is dan de resterende geldigheidsperiode van de verlenende CA-certificaat.  

 -   **Sleutelgebruik**: Geef sleutelgebruikopties voor het certificaat. U kunt kiezen uit de volgende opties:  

        -   **Sleutelcodering**: Sta sleuteluitwisseling toe alleen als de sleutel is gecodeerd.  

        -   **Digitale handtekening**: Sta sleuteluitwisseling toe alleen als een digitale handtekening de sleutel helpt beveiligen.  

   Als u een certificaatsjabloon selecteerde door gebruik te maken van **Bladeren**, is het mogelijk dat u deze instellingen niet kunt wijzigen tenzij u een ander certificaatsjabloon selecteert.  

   De certificaatsjabloon die u hebt geselecteerd, moet zijn geconfigureerd met één of beide van de hiervoor vermelde opties voor sleutelgebruik. Als dat niet het geval is, wordt in het logbestand **Crp.log** van het certificaatregistratiepunt vermeld dat het **sleutelgebruik in CSR en de vraag niet overeenkomen**.  


   -   **Sleutelgrootte (bits)**: Selecteer de grootte van de sleutel in bits.  

   -   **Uitgebreide-sleutelgebruik**: Klik op **Selecteer** om toe te voegen waarden voor het certificaat het beoogde gebruik van. In de meeste gevallen vereist het certificaat **Clientverificatie** zodat de gebruiker of het apparaat bij een server kan worden geverifieerd. U kunt echter zo nodig andere sleutelgebruiken toevoegen.  


   -   **Hash-algoritme**: Selecteer een van de typen beschikbare hash-algoritme om met dit certificaat te gebruiken. Selecteer het sterkste beveiligingsniveau dat door de verbindende apparaten wordt ondersteund.  

   > [!NOTE]  
   > 
   >  **SHA-2** ondersteunt SHA-256, SHA-384 en SHA-512. **SHA-3** ondersteunt alleen SHA-3.  

   -   **CA-basiscertificaat**: Klik op **Selecteer** kiezen van een basis-CA-certificaatprofiel die u eerder hebt geconfigureerd en geïmplementeerd voor de gebruiker of apparaat. Dit CA-certificaat moet het basiscertificaat zijn voor de CA die het certificaat verleent dat u in dit certificaatprofiel gaat configureren.  

   > [!IMPORTANT]  
   >  Als u een basis-CA-certificaat dat niet is geïmplementeerd voor de gebruiker of apparaat opgeeft, initieert System Center Configuration Manager niet de certificaataanvraag die u in dit certificaatprofiel gaat configureren.  


##  <a name="specify-supported-platforms-for-the-certificate-profile"></a>Ondersteunde platforms voor het certificaatprofiel opgeven  

1. Selecteer op de pagina **Ondersteunde platforms** van de wizard Certificaatprofiel maken de besturingssystemen waarvoor u het certificaatprofiel wilt installeren of klik op **Alles selecteren** als u het certificaatprofiel wilt installeren voor alle beschikbare besturingssystemen.
2. Controleer de **samenvatting** pagina van de wizard en kies **voltooien**. 
 
 
Het nieuwe certificaatprofiel wordt weergegeven in de **Certificaatprofielen** knooppunt in de **activa en naleving** werkruimte en is gereed om te worden geïmplementeerd voor gebruikers of apparaten, zoals beschreven in [profielen in System Center Configuration Manager implementeren](deploy-wifi-vpn-email-cert-profiles.md).  