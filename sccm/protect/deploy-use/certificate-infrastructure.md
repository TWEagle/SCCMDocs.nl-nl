---
title: Certificaatinfrastructuur configureren | Microsoft Docs
description: Informatie over het configureren van certificaatinschrijving in System Center Configuration Manager.
ms.custom: na
ms.date: 07/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 29ae59b7-2695-4a0f-a9ff-4f29222f28b3
caps.latest.revision: 7
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: c0d94b8e6ca6ffd82e879b43097a9787e283eb6d
ms.openlocfilehash: 640eb1df9d53fc83d93c39a7ecbaf2668e176805
ms.contentlocale: nl-nl
ms.lasthandoff: 08/02/2017

---

# <a name="configure-certificate-infrastructure"></a>Certificaatinfrastructuur configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Informatie over het certificaatinfrastructuur configureren in System Center Configuration Manager. Controleer, voordat u begint, de vereisten die worden vermeld in [Vereisten voor certificaatprofielen in System Center Configuration Manager](../../protect/plan-design/prerequisites-for-certificate-profiles.md).  

Volg deze stappen om uw infrastructuur configureren voor SCEP, of PFX-certificaten.

## <a name="step-1---install-and-configure-the-network-device-enrollment-service-and-dependencies-for-scep-certificates-only"></a>Stap 1 - afhankelijkheden en installeren en configureren van de Network Device Enrollment Service (alleen voor SCEP-certificaten)

 U moet de rolservice registratieservice voor netwerkapparaten voor Active Directory Certificate Services (AD CS) installeren en configureren, de beveiligingsmachtigingen op de certificaatsjablonen wijzigen, een PKI (Public Key Infrastructure) verificatievergadering implementeren en het register bewerken om de standaard URL-groottelimiet van Internet Information Services (IIS) te verhogen. Indien nodig moet u ook de uitgevende certificeringsinstantie (CA) configureren om een aangepaste geldigheidsperiode toe te staan.  

> [!IMPORTANT]  
>  Voordat u System Center Configuration Manager werken met de Network Device Enrollment Service configureert, controleert u of de installatie en configuratie van de Network Device Enrollment Service. Als deze afhankelijkheden niet correct werken, zult u moeilijkheden probleemoplossing certificaat inschrijven met behulp van System Center Configuration Manager.  

### <a name="to-install-and-configure-the-network-device-enrollment-service-and-dependencies"></a>De registratieservice en afhankelijkheden voor netwerkapparaten installeren en configureren  

1.  Installeer en configureer op een server met Windows Server 2012 R2 de rolservice Registratieservice voor netwerkapparaten voor de serverrol Active Directory Certificate Services. Zie [Network Device Enrollment Service Guidance](http://go.microsoft.com/fwlink/p/?LinkId=309016) (Richtlijnen voor de Registratieservice van netwerkapparaten) in de bibliotheek Active Directory Certificate Services op TechNet voor meer informatie.  

2.  Controleer en wijzig indien nodig de beveiligingsmachtigingen voor de certificaatsjablonen die worden gebruikt door de registratieservice voor netwerkapparaten:  

    -   Voor het account dat de System Center Configuration Manager-console wordt uitgevoerd: **Lees** machtiging.  

         Deze machtiging is vereist voor het uitvoeren van de wizard Certificaatprofiel maken, u kunt bladeren om het certificaatsjabloon te selecteren dat u wilt gebruiken wanneer u een SCEP- instellingenprofiel maakt. Bij het selecteren van een certificaatsjabloon worden bepaalde instellingen in de wizard automatisch ingevuld, zodat u minder moet configureren en er minder kans bestaat om instellingen te selecteren die niet compatibel zijn met de certificaatsjablonen die de registratieservice voor netwerkapparaten gebruikt.  

    -   Voor het SCEP-serviceaccount die gebruikmaakt van de toepassingsgroep registratieservice voor netwerkapparaten: **Lees** en **inschrijven** machtigingen.  

         Deze vereiste is niet specifiek voor System Center Configuration Manager, maar maakt deel uit van de configuratie van de Network Device Enrollment Service. Zie [Network Device Enrollment Service Guidance](http://go.microsoft.com/fwlink/p/?LinkId=309016) (Richtlijnen voor de Registratieservice van netwerkapparaten) in de bibliotheek Active Directory Certificate Services op TechNet voor meer informatie.  

    > [!TIP]  
    >  Weergeven om te identificeren welke sjablonen die het gebruik van de Network Device Enrollment Service, de volgende registersleutel op de server waarop de Network Device Enrollment Service wordt uitgevoerd: Hkey_local_machine\software\microsoft\cryptography\mscep bij te.  

    > [!NOTE]  
    >  Dit zijn de standaardbeveiligingsmachtigingen die geschikt zijn voor de meeste omgevingen. U kunt echter een alternatieve beveiligingsconfiguratie gebruiken. Voor meer informatie, zie [Certificaatsjabloonmachtigingen voor certificaatprofielen plannen in System Center Configuration Manager](../../protect/plan-design/planning-for-certificate-template-permissions.md).  

3.  Een PKI-certificaat dat clientverificatie ondersteunt naar deze server implementeren. Mogelijk hebt u al een geschikt certificaat geïnstalleerd op de computer dat u kunt gebruiken, of mogelijk moet u (of verkiest u) speciaal voor dit doel een certificaat te implementeren. Raadpleeg voor meer informatie over de vereisten voor dit certificaat de details voor de beleidsmodule van Configuration Manager-Servers met de functieservice registratieservice voor netwerkapparaten in het ** PKI-certificaten voor Servers ** sectie het [PKI-certificaatvereisten voor System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md) onderwerp.  

    > [!TIP]  
    >  Als u ondersteuning bij het implementeren van dit certificaat nodig hebt, kunt u de instructies voor het [het clientcertificaat voor distributiepunten implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clientdistributionpoint2008_cm2012), omdat de certificaatvereisten hetzelfde met één uitzondering:  
    >   
    >  -   Het selectievakje **De persoonlijke sleutel exporteerbaar maken** niet selecteren op tabblad **Afhandeling van aanvragen** van de eigenschappen voor de certificaatsjabloon.  
    >   
    >  U beschikt niet over dit certificaat exporteren met de persoonlijke sleutel omdat u kunt bladeren naar het lokale computerarchief en dit selecteren wanneer u de System Center Configuration Manager-beleidsmodule configureert.  

4.  Zoek het basiscertificaat waarnaar het clientverificatiecertificaat overeenkomt. Exporteer vervolgens dit basis-CA-certificaat naar een certificaat (.cer)-bestand. Dit bestand op een veilige locatie opslaan voor veilige toegang wanneer u later de sitesysteemserver voor het certificaatregistratiepunt installeert en configureert.  

5.  Gebruik op dezelfde server de register-editor om de standaard URL-groottelimiet voor IIS te verhogen, door de volgende DWORD-waarden voor de registersleutel HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP in te stellen op:  

    -   Stel de **MaxFieldLength**-sleutel in op **65534**.  

    -   Stel de **MaxRequestBytes-sleutel** in op **16777216**.  

     Zie voor meer informatie artikel [820129: HTTP.sys-registerinstellingen voor Windows](http://go.microsoft.com/fwlink/?LinkId=309013) in de Microsoft Knowledge Base.  

6.  Op dezelfde server, in IIS-beheerder (Internet Information Services), de instellingen voor aanvraagfiltering voor de toepassing /certsrv/mscep wijzigen en vervolgens de server opnieuw opstarten. In het dialoogvenster **Instellingen voor aanvraagfiltering bewerken** moeten de instellingen van **Aanvraaglimieten** de volgende zijn:  

    -   **Maximale toegestane inhoudslengte (Bytes)**: **30000000**  

    -   **Maximale URL-lengte (Bytes)**: **65534**  

    -   **Maximale queryreeks (Bytes)**: **65534**  

     Zie [Request Limits](http://go.microsoft.com/fwlink/?LinkId=309014) (Aanvraaglimieten) in de IIS-referentiebibliotheek, voor meer informatie over deze instellingen en over de configuratie ervan.  

7.  Als u wilt dat een certificaat aanvragen dat een kortere geldigheidsperiode dan de certificaatsjabloon die u gebruikt: Deze configuratie is voor een ondernemings-CA standaard uitgeschakeld. Het opdrachtregelprogramma Certutil gebruiken, vervolgens de certificaatservice stopzetten en opnieuw opstarten met behulp de volgende opdrachten, om deze optie op een ondernemings-CA in te schakelen:  

    1.  **certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**  

    2.  **net stop certsvc**  

    3.  **net start certsvc**  

     Zie [Certificate Services Tools and Settings](http://go.microsoft.com/fwlink/p/?LinkId=309015) (Certificate Services: hulpprogramma's en instellingen) in de PKI-technologiebibliotheek op Technet voor meer informatie.  

8.  Controleer of de registratieservice voor netwerkapparaten werkt door de volgende koppeling als voorbeeld te gebruiken: **https://server.contoso.com/certsrv/mscep/mscep.dll**. U zou de ingebouwde webpagina van de registratieservice voor netwerkapparaten moeten zien. Deze webpagina legt uit waaruit de service bestaat en legt uit dat netwerkapparaten de URL gebruiken om certificaataanvragen te verzenden.  

 Nu dat de registratieservice voor netwerkapparaten en afhankelijkheden zijn geconfigureerd, bent u klaar om het certificaatregistratiepunt nu te installeren en configureren.


## <a name="step-2---install-and-configure-the-certificate-registration-point"></a>Stap 2: Installeer en configureer het certificaatregistratiepunt.

U moet installeren en configureren van ten minste één certificaatregistratiepunt in de System Center Configuration Manager-hiërarchie en u kunt deze sitesysteemrol in de centrale beheersite of in een primaire site installeren.  

> [!IMPORTANT]  
>  Zie de sectie **Sitesysteemvereisten** in het onderwerp [Ondersteunde configuraties voor System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md) voor vereisten van besturingssystemen en afhankelijkheden voor het certificaatregistratiepunt, voordat u het certificaatregistratiepunt installeert.  

##### <a name="to-install-and-configure-the-certificate-registration-point"></a>Het certificaatregistratiepunt installeren en configureren  

1.  Klik in de System Center Configuration Manager-console op **beheer**.  

2.  Vouw in de werkruimte **Beheer**, **Siteconfiguratie** uit, klik op **Servers en sitesysteemrollen** en selecteer vervolgens de server die u wilt gebruiken voor het certificaatregistratiepunt.  

3.  Klik op **Sitesysteemrollen toevoegen** in het tabblad **Start** in de groep **Server**.  

4.  Configureer de algemene instellingen voor het sitesysteem op de pagina **Algemeen** en klik vervolgens op **Volgende**.  

5.  Klik op de pagina **Proxy** op **Volgende**. Het certificaatregistratiepunt gebruikt geen internetproxy-instellingen.  

6.  Selecteer **Certificaatregistratiepunt** uit de lijst beschikbare rollen op de pagina **Systeemrolselectie** en klik vervolgens op **Volgende**. 

7. Op de **certificaat registratiemodus** te selecteren of u wilt dat deze certificaatregistratiepunt met **proces SCEP-certificaataanvragen**, of **proces PFX-certificaataanvragen**. Een certificaatregistratiepunt beide soorten aanvragen kan niet worden verwerkt, maar u kunt meerdere certificaat maakt registratiepunten als u met beide typen certificaten werkt.

   Als verwerking PFX-certificaten, moet u een certificeringsinstantie, door Microsoft of Entrust kiezen.

8.  De **instellingen Certificaatregistratiepunt** pagina is afhankelijk van het certificaattype:
    -   Als u hebt geselecteerd **proces SCEP-certificaataanvragen**, configureer dan het volgende:
        -   **Websitenaam**, **HTTPS-poortnummer**, en **virtuele toepassingsnaam** voor het certificaatregistratiepunt. Deze velden worden automatisch ingevuld met standaardwaarden. 
        -   **URL voor registratieservice voor netwerkapparaten en basis-CA-certificaat** -Klik op **toevoegen**, klik dan in de **URL toevoegen en CA-basiscertificaat** dialoogvenster geeft u het volgende:
            - **URL voor de Network Device Enrollment Service**: Geef de URL in de volgende indeling: https://*< server_FQDN >*/certsrv/mscep/mscep.dll. Als bijvoorbeeld de FQDN van uw server waarop de registratieservice voor netwerkapparaten wordt uitgevoerd server1.contoso.com is, typt u **https://server1.contoso.com/certsrv/mscep/mscep.dll**.
            - **CA-basiscertificaat**: Blader naar en selecteer het certificaatbestand (.cer) dat u hebt gemaakt en opgeslagen in **stap 1: Installeer en configureer de registratieservice voor netwerkapparaten en afhankelijkheden**. Dit CA-basiscertificaat kan het certificaatregistratiepunt voor het valideren van de client certificaat voor clientverificatie die door de System Center Configuration Manager-beleidsmodule wordt gebruikt.  

    - Als u hebt geselecteerd **proces PFX-certificaataanvragen**, u de verbindingsgegevens en referenties voor de geselecteerde certificeringsinstantie configureren.

        - Voor het gebruik van Microsoft als de certificeringsinstantie, klikt u op **toevoegen** vervolgens in de **toevoegen van een certificeringsinstantie en de Account** dialoogvenster geeft u het volgende:
            - **Naam van de instantie van het certificaat** -Voer de naam van de certificaatserver autoriteit.
            - **Het certificaat van instantie van Account** -klikt u op **ingesteld** het account dat machtigingen heeft om te registreren in de sjablonen op de certificeringsinstantie maken of selecteren.
            - **Verbindingsaccount registratie van het certificaat** : Selecteer of het account dat het certificaatregistratiepunt met de Configuration Manager-database verbindt maken. Alteratively, kunt u het lokale computeraccount van de computer die als host fungeert voor het certificaatregistratiepunt.
            - **Active Directory Certificate publicatieaccount** : een account selecteren of een nieuw account maken dat wordt gebruikt om certificaten uitgeven naar gebruikersobjecten in Active Directory.

            - In de **URL voor de registratieservice voor netwerkapparaten en basis-CA-certificaat** in het dialoogvenster geeft u de volgende en klik vervolgens op **OK**:  

        - Als u wilt gebruiken Entrust als de certificeringsinstantie, opgeven:

           - De **MDM webservice-URL**
           - De gebruikersnaam en wachtwoord referenties voor de URL.

           Wanneer u de MDM-API voor het definiëren van de URL van de webservice Entrust gebruikt, moet u ten minste versie 9 van de API, zoals wordt weergegeven in het volgende voorbeeld:

           `https://entrust.contoso.com:19443/mdmws/services/AdminServiceV9`

           Eerdere versies van de API bieden geen ondersteuning voor Entrust.

9. Klik op **Volgende** en voltooi de wizard.  

10. Wacht enkele minuten zodat de installatie kan worden voltooid en controleer vervolgens dat het certificaatregistratiepunt geïnstalleerd is aan de hand van een van de volgende methodes:  

    -   Vouw in de werkruimte **Bewaking****Systeemstatus**, klik op **Onderdeelstatus** en zoek naar statusberichten van het onderdeel **SMS_CERTIFICATE_REGISTRATION_POINT**.  

    -   Gebruik op de sitesysteemserver de bestanden *<Installatiepad Configuration Manager\>*\Logs\crpsetup.log en *<Installatiepad Configuration Manager\>*\Logs\crpmsi.log. Een geslaagde installatie retourneert een afsluitcode 0.  

    -   Controleer of u verbinding kunt maken met de URL van het certificaat registratie pointâ€ via een browser "bijvoorbeeld: https://server1.contoso.com/CMCertificateRegistration. U moet een **Serverfout**-pagina zien voor de toepassingsnaam, met een HTTP 404-beschrijving.  

11. Zoek het geëxporteerde certificaatbestand voor de basis-CA dat het certificaatregistratiepunt automatisch in de volgende map op de primaire siteservercomputer heeft gemaakt: *<Installatiepad ConfigMgr\>*\inboxes\certmgr.box. Dit bestand opslaan in een veilige locatie met veilige toegang wanneer u later de System Center Configuration Manager-beleidsmodule installeert op de server waarop de Network Device Enrollment Service wordt uitgevoerd.  

    > [!TIP]  
    >  Dit certificaat is niet onmiddellijk beschikbaar in deze map. Mogelijk moet u wacht een tijdje (bijvoorbeeld half uur) voordat u System Center Configuration Manager het bestand naar deze locatie kopieert.  


## <a name="step-3----install-the-system-center-configuration-manager-policy-module-for-scep-certificates-only"></a>Stap 3: Installeer de System Center Configuration Manager-beleidsmodule (voor SCEP certificaten).

U moet installeren en configureren van de System Center Configuration Manager-beleidsmodule op elke server die u hebt opgegeven in **stap 2: Installeer en configureer het certificaatregistratiepunt** als **-URL voor de Network Device Enrollment Service** in de eigenschappen voor het certificaatregistratiepunt.  

##### <a name="to-install-the-policy-module"></a>De beleidsmodule installeren  

1.  Op de server waarop de Network Device Enrollment Service wordt uitgevoerd, meld u aan als een domeinbeheerder en kopieer de volgende bestanden uit de < ConfigMgrInstallationMedia\>\SMSSETUP\POLICYMODULE\X64 map op de installatiemedia van System Center Configuration Manager naar een tijdelijke map:  

    -   PolicyModule.msi  

    -   PolicyModuleSetup.exe  

    Als u een taalpakketmap hebt op de installatiemedia, kopieert u bovendien deze map en de inhoud hiervan.  

2.  PolicyModuleSetup.exe om de wizard System Center Configuration Manager Policy Module Setup te starten van de tijdelijke map uitvoeren.  

3.  Klik op de eerste pagina van de wizard op **Volgende**, aanvaard de licentievoorwaarden en klik vervolgens op **Volgende**.  

4.  Op de pagina **Installatiemap**, aanvaardt u de standaardinstallatiemap voor de beleidsmodule of geeft u een alternatieve map op. Klik vervolgens op **Volgende**.  

5.  Geef op de pagina **Certificaatregistratiepunt** de URL van het certificaatregistratiepunt op met behulp van de FQDN van de sitesysteemserver en de virtuele toepassingsnaam die is opgegeven in de eigenschappen voor het certificaatregistratiepunt. De standaardnaam van de virtuele toepassing is CMCertificateRegistration. Als bijvoorbeeld de sitesysteemserver een FQDN van server1.contoso.com heeft en u de standaardnaam van de virtuele toepassing gebruikte, geeft u **https://server1.contoso.com/CMCertificateRegistration** op.  

6.  Aanvaard de standaardpoort **443** of geef het alternatieve poortnummer op dat door certificaatregistratiepunt wordt gebruikt en klik vervolgens op **Volgende**.  

7.  Op de **clientcertificaat voor de beleidsmodule**pagina, blader naar en geef het certificaat voor clientverificatie die u hebt geïmplementeerd in **stap 1: Installeer en configureer de registratieservice voor netwerkapparaten en afhankelijkheden**, en klik vervolgens op **volgende**.  

8.  Op de **Certificaatregistratiepunt** pagina, klikt u op **Bladeren** selecteren voor de basis-CA die u hebt gezocht en opgeslagen aan het einde van het geëxporteerde certificaatbestand **stap 2: Installeer en configureer het certificaatregistratiepunt**.  

    > [!NOTE]  
    >  Als u dit certificaatbestand nog niet hebt opgeslagen, bevindt het zich in <Installatiepad Configuration Manager\>\inboxes\certmgr.box op de siteservercomputer.  

9. Klik op **Volgende** en voltooi de wizard.  

 Als u de System Center Configuration Manager-beleidsmodule verwijderen wilt, gebruikt u **programma's en onderdelen** in het Configuratiescherm. 

 
Nu dat u de configuratiestappen hebt voltooid, bent u klaar om certificaten te implementeren voor gebruikers en apparaten door het maken en implementeren van certificaatprofielen. Zie [Certificaatprofielen in System Center Configuration Manager](../../protect/deploy-use/create-certificate-profiles.md) voor meer informatie over het gebruik van certificaatprofielen.  

