---
title: Het maken van SCEP-certificaatprofielen | Microsoft-documenten
description: Informatie over het gebruiken van certificaatprofielen voor het inrichten van beheerde apparaten met de certificaten die ze nodig hebben in System Center Configuration Manager.
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 634d612c-92d7-4c03-873a-b2e730c9a72d
caps.latest.revision: 16
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: aa8924a013ebdbee888cab33001fddbe7ad2d67e
ms.openlocfilehash: 80a716f5a42a81e5550eb1b5c7f14534e14a4fb7
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="create-certificate-profiles"></a>Certificaatprofielen maken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Gebruik certificaatprofielen in Configuration Manager (SCCM) voor de inrichting van beheerde apparaten met de certificaten die ze nodig hebben om toegang tot bedrijfsbronnen krijgen. Voordat u certificaatprofielen maakt, de certificaatinfrastructuur instellen zoals beschreven in [certificaatinfrastructuur voor System Center Configuration Manager instellen](certificate-infrastructure.md).  

Dit onderwerp wordt beschreven hoe u vertrouwde basiscertificaten en SCEP-certificaatprofielen maken. Als u wilt PFX-certificaatprofielen maken, Zie [maken PFX-certificaatprofielen](../../protect/deploy-use/create-pfx-certificate-profiles.md).


## <a name="create-a-new-certificate-profile"></a>Maak een nieuw Certificaatprofiel  

### <a name="start-the-create-certificate-profile-wizard"></a>Start de Wizard Certificaatprofiel maken  

1.  Klik in de System Center Configuration Manager-console op **activa en naleving**.  

2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit, vouw vervolgens **Toegang tot bedrijfsbronnen**uit en klik op **Certificaatprofielen**.  

3.  Klik op **Certificaatprofiel maken** in het tabblad **Start** in de groep **Maken**.  

### <a name="provide-general-information-about-the-certificate-profile"></a>Algemene informatie over het certificaatprofiel opgeven  

Geef op de pagina **Algemeen** van de wizard Certificaatprofiel maken de volgende informatie op:  

-   **Naam**: Geef een unieke naam voor het certificaatprofiel. U kunt maximaal 256 tekens gebruiken.  

-   **Beschrijving**: Geef een beschrijving met een overzicht van het certificaatprofiel en andere relevante informatie die helpt bij het identificeren ervan in de System Center Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.  

-   **Geef op welk type certificaatprofiel dat u wilt maken**: Kies een van de volgende certificaatprofieltypen:  

-   **Vertrouwd CA-certificaat**: Selecteer dit certificaatprofieltype als u wilt implementeren van een vertrouwde basiscertificeringsinstantie (CA) of tussenliggend CA-certificaat om een certificaatvertrouwensketen in te richten voor wanneer de gebruiker of het apparaat een ander apparaat moet verifiëren. Het apparaat zou bijvoorbeeld een Remote Authentication Dial-In User Service (RADIUS)-server of een virtueel particulier netwerk (VPN)-server kunnen zijn. U moet ook een vertrouwd CA-certificaatprofiel configureren voordat u een SCEP-certificaatprofiel kunt maken. In dit geval moet het vertrouwde CA-certificaat het vertrouwde basiscertificaat zijn voor de CA die het certificaat aan de gebruiker of het apparaat zal verlenen.  

-   **Instellingen voor Simple Certificate Enrollment Protocol (SCEP)**: Selecteer dit certificaatprofieltype als u wilt dat een certificaat wilt aanvragen voor een gebruiker of apparaat, met behulp van het Simple Certificate Enrollment Protocol en de functieservice Network Device Enrollment Service.

-   **Instellingen voor persoonlijke informatie Exchange PKCS #12 (PFX) - Import**: Selecteer deze optie om een PFX-certificaat te importeren. Voor meer informatie over het maken van het PFX-certificaat Zie [maken PFX-certificaatprofielen](../../protect/deploy-use/create-pfx-certificate-profiles.md).



### <a name="configure-a-trusted-ca-certificate"></a>Een vertrouwd CA-certificaat configureren  

> [!IMPORTANT]  
>  U moet minstens één vertrouwd CA-certificaatprofiel configureren voordat u een SCEP-certificaatprofiel kunt maken.    
>  
>  Als u een van deze waarden wijzigen nadat het certificaat wordt geïmplementeerd op een nieuw certificaat aangevraagd:
>  -  Opslag van clustersleutels opgeven
>  -  Certificaatsjabloonnaam
>  -  Certificaattype
>  -  Indeling van de onderwerpnaam
>  -  Alternatieve onderwerpnaam
>  -  Geldigheidsduur van certificaat
>  -  Sleutelgebruik
>  -  Sleutelgrootte
>  -  Uitgebreide-sleutelgebruik
>  -  Basis-CA-certificaat

1.  Geef op de pagina **Vertrouwd CA-certificaat** van de wizard Certificaatprofiel maken de volgende informatie op:  

 -   **Certificaatbestand**: Klik op **importeren** en blader vervolgens naar het certificaatbestand dat u wilt gebruiken.  

 -   **Doelarchief**: Voor apparaten met meer dan een certificaatarchief selecteert u waar het certificaat wordt opgeslagen. Voor apparaten die slechts één archief hebben, wordt deze instelling wordt genegeerd.  

2.  Gebruik de **Vingerafdruk van het certificaat** om te verifiëren dat u het juiste certificaat hebt geïmporteerd.  


### <a name="configure-scep-certificate-information-only-for-scep-certificates"></a>Gegevens van SCEP-certificaat (alleen voor SCEP-certificaten) configureren  

1.  Op de pagina **SCEP-servers** van de wizard Certificaatprofiel maken geeft u de URL's op voor de NDES-servers die via SCEP certificaten uitgeven. U kunt ervoor kiezen om automatisch een NDES-URL toe te wijzen op basis van de configuratie van de sitesysteemserver voor het Certificaatregistratiepunt of URL's handmatig toevoegen.  

2.  Voltooi de **SCEP-registratie** pagina van de Wizard Certificaatprofiel maken.

 -  **Nieuwe pogingen**: Geef het aantal keren dat het apparaat wordt automatisch opnieuw geprobeerd de certificaataanvraag op de server waarop de Network Device Enrollment Service wordt uitgevoerd. Deze instelling ondersteunt het scenario waarbij een CA-manager een certificaataanvraag moet goedkeuren voordat het wordt geaccepteerd. Deze instelling wordt doorgaans gebruikt voor sterk beveiligde omgevingen of als u een zelfstandige verlenende CA en geen bedrijfs-CA hebt. U kunt deze instelling mogelijk ook gebruiken voor testdoeleinden zodat u de certificaataanvraagopties kunt inspecteren alvorens de verlenende CA de certificaataanvraag verwerkt. Gebruik deze instellingen met de instelling **Tijd tussen pogingen (minuten)** .  

 -   **Tijd tussen elke poging (minuten)**: Geef het interval in minuten, tussen elke registratiepoging wanneer u goedkeuring van de CA-manager gebruikt voordat de verlenende CA de certificaataanvraag verwerkt. Als u beheergoedkeuring gebruikt voor testdoeleinden, zult u waarschijnlijk een lage waarde willen opgeven ,zodat u niet lang te hoeft wachten voordat het apparaat de certificaataanvraag opnieuw probeert nadat u de aanvraag goedkeurt. Als u echter beheergoedkeuring op een productienetwerk gebruikt, zult u waarschijnlijk een hogere waarde willen opgeven om voldoende tijd te geven aan de CA-beheerder om aangevraagde goedkeuringen toe te staan of te weigeren.  

 -   **Drempelwaarde voor verlenging (%)**: Geef het percentage van de levensduur van het certificaat dat voordat het apparaat verlenging van het certificaat aanvraagt resteert.  

 -   **Sleutelarchiefprovider (KSP)**: Geef op waar de sleutel voor het certificaat moet worden opgeslagen. Kies een van de volgende waarden:  

   -   **Installeren in Trusted Platform Module (TPM), indien aanwezig**: De sleutel in de TPM geïnstalleerd. Als de TPM niet aanwezig is, wordt de sleutel geïnstalleerd in de archiefprovider voor de softwaresleutel.  

   -   **Installeren in Trusted Platform Module (TPM), anders niet**: De sleutel in de TPM geïnstalleerd. De installatie mislukt als de TPM-module niet aanwezig is.  

   -   **Installatie op Windows Hello voor zakelijke anders niet**: Deze optie is beschikbaar voor Windows 10 Desktop en Mobile-apparaten. De sleutel tot het geregistreerde **Windows Hello voor bedrijven**, beschreven in de [Windows Hello voor Business-instellingen in System Center Configuration Manager](../../protect/deploy-use/windows-hello-for-business-settings.md). Met deze optie kunt u ook opgeven dat **Meervoudige verificatie vereisen** geldt tijdens de registratie van apparaten voordat certificaten naar die apparaten worden uitgegeven. Zie [Windows-apparaten beveiligen met meervoudige verificatie](https://technet.microsoft.com/library/dn889751.aspx) voor meer informatie.

   > [!NOTE]  
   > 
   > Wanneer een gebruiker een Windows Hello voor zakelijke PINCODE maakt, stuurt Windows een melding dat Configuration Manager voor luistert. Hiermee wordt Configuration Manager om te snel worden op de hoogte van welke gebruikers een Windows Hello PINCODE hebt gemaakt. Configuration Manager kunnen vervolgens ook nieuwe certificaten uitgeven voor deze gebruikers als Windows Hello wordt gebruikt als de opslagprovider sleutel in een certificaatprofiel.  

   -   **Installeren naar Sleutelarchiefprovider van Software**: De sleutel wordt in de archiefprovider voor de softwaresleutel geïnstalleerd.  

 -   **Apparaten voor certificaatinschrijving**: Als het certificaatprofiel wordt geïmplementeerd op een Gebruikersverzameling, selecteren of toegestaan om certificaatregistratie alleen de gebruiker het primaire apparaat of op alle apparaten waarop de gebruiker zich aanmeldt. Als het certificaatprofiel wordt geïmplementeerd naar een apparaatsverzameling, dient u te selecteren of het is toegestaan om certificaatregistratie alleen voor de primaire gebruiker of voor alle gebruikers van het apparaat uit te voeren.  

3.  Geef op de pagina **Certificaateigenschappen** van de wizard Certificaatprofiel maken de volgende informatie op:  

 -   **Certificaatsjabloonnaam**: Klik op **Bladeren** om de naam van een certificaatsjabloon die de Network Device Enrollment Service is geconfigureerd om te gebruiken en die is toegevoegd aan een verlenende CA te selecteren. Om te kunnen bladeren voor certificaatsjablonen te beschikken, moet de gebruikersaccount die u gebruikt voor het uitvoeren van de System Center Configuration Manager-console de machtiging lezen voor de certificaatsjabloon hebben. Als u **Bladeren**echter niet kunt gebruiken, typ dan de naam van het certificaatsjabloon.  

 > [!IMPORTANT]
 >   
 >  Het certificaat zal niet worden geïmplementeerd als de naam van het certificaatsjabloon niet-ASCII-tekens bevat (bijvoorbeeld teken van het Chinese alfabet). U kunt ervoor zorgen dat het certificaat wordt geïmplementeerd door eerst een kopie te maken van het certificaatsjabloon op de CA en de kopie een nieuwe naam te geven met alleen ASCII-tekens.  

   Let op het volgende, afhankelijk of u bladert naar het certificaatsjabloon of u de certificaatnaam invoert:  

 -   Als u bladert om de naam van het certificaatsjabloon te selecteren, worden sommige velden op de pagina automatisch vanaf het certificaatsjabloon ingevuld. In sommige gevallen is het niet mogelijk deze waarden te wijzigen, tenzij u een ander certificaatsjabloon selecteert.  

 -   Als u de naam van het certificaatsjabloon invoert, dient u ervoor te zorgen dat de naam exact overeenkomt met een van de certificaatsjablonen die zijn vermeld in het register van de server waarop de registratieservice van netwerkapparaten wordt uitgevoerd. Zorg ervoor dat u de naam opgeeft van het certificaatsjabloon en niet de weergavenaam van het certificaatsjabloon.  

   Om de namen van certificaatsjablonen hebt gevonden, bladert u naar de volgende registersleutel: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. De certificaatsjablonen worden hier vermeld als de waarden voor **EncryptionTemplate**, **GeneralPurposeTemplate**en **SignatureTemplate**. Standaard is **IPSECIntermediateOffline**de waarde voor deze drie certificaatsjablonen. Dit verwijst naar de sjabloonweergavenaam **IPSec (Offline-aanvraag)**.  

   > [!WARNING]  
   > 
   >  Omdat de System Center Configuration Manager kan de inhoud van het certificaatsjabloon niet verifiëren als u de naam van de certificaatsjabloon in plaats van bladeren invoert, kunt u mogelijk opties selecteren die het certificaatsjabloon biedt geen ondersteuning voor en dat resulteert in een mislukte certificaataanvraag. Als dit gebeurt, ziet u een foutmelding voor w3wp.exe in het bestand CPR.log met het bericht dat de sjabloonnaam van het Certificate Signing Request (CSR) en de invoer niet overeenkomen.  
   >   
   >  Als u de naam van het certificaatsjabloon invoert dat is opgegeven voor de waarde **GeneralPurposeTemplate** , dient u de opties **Sleutelcodering** en de **Digitale handtekening** voor dit certificaatprofiel te selecteren. Als u echter alleen de optie **Sleutelcodering** in dit certificaatprofiel wilt inschakelen, dient u de naam van het certificaatsjabloon op te geven voor de sleutel **EncryptionTemplate** . Op dezelfde manier dient u, als u alleen de optie **Digitale handtekening** in dit certificaatprofiel wilt inschakelen, de naam van het certificaatsjabloon op te geven voor de sleutel **SignatureTemplate** .  

 -   **Certificaattype**: Selecteer of het certificaat zal worden geïmplementeerd naar een apparaat of een gebruiker.  
 -   **Indeling van de onderwerpnaam**: Selecteer in de lijst hoe System Center Configuration Manager automatisch de onderwerpnaam in de certificaataanvraag maakt. Als het certificaat voor een gebruiker is, kunt u ook het e-mailadres van de gebruiker in de onderwerpnaam opnemen. 
    
   > [!NOTE]  
   > 
   > Selecteren **IMEI-nummer** of **serienummer** kunt u onderscheid maken tussen verschillende apparaten die eigendom zijn van dezelfde gebruiker. Deze apparaten kunnen bijvoorbeeld een algemene naam, maar geen IMEI-nummer of het serienummer van delen. Als het apparaat niet een IMEI-nummer of een serienummer rapporteert, wordt het certificaat afgegeven met de algemene naam.

 -   **Alternatieve onderwerpnaam**: Geef op hoe System Center Configuration Manager automatisch de waarden voor de alternatieve naam voor onderwerp (SAN) in de certificaataanvraag maakt. Als u bijvoorbeeld een gebruikerscertificaattype selecteerde, kunt u de User Principal Name (UPN) gebruiken in de alternatieve naam van het onderwerp.  Als het clientcertificaat zal worden gebruikt om een Network Policy Server te verifiëren, dient u de alternatieve naam van het onderwerp op de UPN in te stellen.  

   > [!NOTE]  
   >  - iOS-apparaten ondersteunen slechts een beperkt aantal indelingen van onderwerpnamen en alternatieve namen van onderwerpen in SCEP-certificaten. Als u een indeling opgeeft die niet wordt ondersteund, zullen er geen certificaten op iOS-apparaten worden geregistreerd. Gebruik de **Algemene naam** voor de **Indeling van de onderwerpnaam**, en de **DNS-naam**, **E-mailadres** of **UPN** voor de **Alternatieve naam voor het onderwerp**als u een SCEP-certificaatprofiel configureert voor implementatie op iOS-apparaten.  

 -   **Geldigheidsduur van certificaat**: Als u hebt de certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE opdracht op de verlenende CA, waarop een aangepaste geldigheidsperiode mogelijk is, kunt u de hoeveelheid resterende tijd voordat het certificaat is verlopen. Zie voor meer informatie over deze opdracht [certificaatinfrastructuur in System Center Configuration Manager](../../protect/deploy-use/certificate-infrastructure.md) onderwerp.  

   U kunt een waarde opgeven die lager is dan de geldigheidsperiode in het opgegeven certificaatsjabloon, maar niet hoger. Als de geldigheidsperiode van het certificaat in het certificaatsjabloon bijvoorbeeld twee jaar is, kunt u wel één jaar, maar niet vijf jaar opgeven. De waarde moet ook lager is dan de resterende geldigheidsperiode van de verlenende CA-certificaat.  

 -   **Sleutelgebruik**: Geef sleutelgebruikopties voor het certificaat. U kunt kiezen uit de volgende opties:  

        -   **Sleutelcodering**: Sta sleuteluitwisseling toe alleen als de sleutel is gecodeerd.  

        -   **Digitale handtekening**: Sleuteluitwisseling Sta alleen toe als een digitale handtekening de sleutel helpt beveiligen.  

   Als u een certificaatsjabloon selecteerde door gebruik te maken van **Bladeren**, is het mogelijk dat u deze instellingen niet kunt wijzigen tenzij u een ander certificaatsjabloon selecteert.  

   De certificaatsjabloon die u hebt geselecteerd, moet zijn geconfigureerd met één of beide van de hiervoor vermelde opties voor sleutelgebruik. Als dat niet het geval is, wordt in het logbestand **Crp.log** van het certificaatregistratiepunt vermeld dat het **sleutelgebruik in CSR en de vraag niet overeenkomen**.  


   -   **Sleutelgrootte (bits)**: Selecteer in bits de grootte van de sleutel.  

   -   **Uitgebreide-sleutelgebruik**: Klik op **Selecteer** om toe te voegen waarden voor het certificaat voor het beoogde gebruik van. In de meeste gevallen vereist het certificaat **Clientverificatie** zodat de gebruiker of het apparaat bij een server kan worden geverifieerd. U kunt echter zo nodig andere sleutelgebruiken toevoegen.  


   -   **Hash-algoritme**: Selecteer een van de typen beschikbare hash-algoritme om met dit certificaat te gebruiken. Selecteer het sterkste beveiligingsniveau dat door de verbindende apparaten wordt ondersteund.  

   > [!NOTE]  
   > 
   >  **SHA-2** ondersteunt SHA-256, SHA-384 en SHA-512. **SHA-3** ondersteunt alleen SHA-3.  

   -   **Basis-CA-certificaat**: Klik op **selecteren** kiezen van een basis-CA-certificaatprofiel die u eerder hebt geconfigureerd en geïmplementeerd voor de gebruiker of apparaat. Dit CA-certificaat moet het basiscertificaat zijn voor de CA die het certificaat verleent dat u in dit certificaatprofiel gaat configureren.  

   > [!IMPORTANT]  
   >  Als u een basis-CA-certificaat dat niet is geïmplementeerd voor de gebruiker of apparaat opgeeft, zal de certificaataanvraag die u in dit certificaatprofiel gaat configureren het System Center Configuration Manager niet starten.  


###  <a name="specify-supported-platforms-for-the-certificate-profile"></a>Ondersteunde platforms voor het certificaatprofiel opgeven  

1. Selecteer op de pagina **Ondersteunde platforms** van de wizard Certificaatprofiel maken de besturingssystemen waarvoor u het certificaatprofiel wilt installeren of klik op **Alles selecteren** als u het certificaatprofiel wilt installeren voor alle beschikbare besturingssystemen.
2. Controleer de **samenvatting** pagina van de wizard en kies **voltooien**. 
 
 
Het nieuwe certificaatprofiel wordt weergegeven in de **Certificaatprofielen** knooppunt in de **activa en naleving** werkruimte en is gereed om te worden geïmplementeerd voor gebruikers of apparaten, zoals beschreven in [profielen in System Center Configuration Manager implementeren](deploy-wifi-vpn-email-cert-profiles.md).  
