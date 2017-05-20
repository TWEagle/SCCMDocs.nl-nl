---
title: Configureren certificaatinfrastructuur | Microsoft-documenten
description: Informatie over het configureren van certificaatinschrijving in System Center Configuration Manager.
ms.custom: na
ms.date: 03/28/2017
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
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 859a8da10f55e314b205b7a4a415a1d2a60a920a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="certificate-infrastructure"></a>Certificaatinfrastructuur

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hier worden de stappen, details en meer informatie over het configureren van certificaten in System Center Configuration Manager. Controleer, voordat u begint, de vereisten die worden vermeld in [Vereisten voor certificaatprofielen in System Center Configuration Manager](../../protect/plan-design/prerequisites-for-certificate-profiles.md).  

Ga als volgt uw infrastructuur configureren voor SCEP, of PFX-certificaten.

## <a name="step-1---install-and-configure-the-network-device-enrollment-service-and-dependencies-for-scep-certificates-only"></a>Stap 1 - installeren en configureren van de registratieservice en afhankelijkheden (alleen voor SCEP-certificaten)

 U moet de rolservice registratieservice voor netwerkapparaten voor Active Directory Certificate Services (AD CS) installeren en configureren, de beveiligingsmachtigingen op de certificaatsjablonen wijzigen, een PKI (Public Key Infrastructure) verificatievergadering implementeren en het register bewerken om de standaard URL-groottelimiet van Internet Information Services (IIS) te verhogen. Indien nodig moet u ook de uitgevende certificeringsinstantie (CA) configureren om een aangepaste geldigheidsperiode toe te staan.  

> [!IMPORTANT]  
>  Voordat u System Center Configuration Manager voor gebruik met de Network Device Enrollment Service configureert, controleert u de installatie en configuratie van de Network Device Enrollment Service. Als deze afhankelijkheden niet correct werken, zult u moeilijkheden certificaatinschrijving oplossen met behulp van System Center Configuration Manager.  

### <a name="to-install-and-configure-the-network-device-enrollment-service-and-dependencies"></a>De registratieservice en afhankelijkheden voor netwerkapparaten installeren en configureren  

1.  Installeer en configureer op een server met Windows Server 2012 R2 de rolservice Registratieservice voor netwerkapparaten voor de serverrol Active Directory Certificate Services. Zie [Network Device Enrollment Service Guidance](http://go.microsoft.com/fwlink/p/?LinkId=309016) (Richtlijnen voor de Registratieservice van netwerkapparaten) in de bibliotheek Active Directory Certificate Services op TechNet voor meer informatie.  

2.  Controleer en wijzig indien nodig de beveiligingsmachtigingen voor de certificaatsjablonen die worden gebruikt door de registratieservice voor netwerkapparaten:  

    -   Voor het account dat de System Center Configuration Manager-console wordt uitgevoerd: **Lees** machtiging.  

         Deze machtiging is vereist voor het uitvoeren van de wizard Certificaatprofiel maken, u kunt bladeren om het certificaatsjabloon te selecteren dat u wilt gebruiken wanneer u een SCEP- instellingenprofiel maakt. Bij het selecteren van een certificaatsjabloon worden bepaalde instellingen in de wizard automatisch ingevuld, zodat u minder moet configureren en er minder kans bestaat om instellingen te selecteren die niet compatibel zijn met de certificaatsjablonen die de registratieservice voor netwerkapparaten gebruikt.  

    -   Voor het SCEP-serviceaccount die gebruikmaakt van de Network Device Enrollment Service groep van toepassingen: **Lees** en **inschrijven** machtigingen.  

         Deze vereiste is niet specifiek voor System Center Configuration Manager, maar maakt deel uit van de configuratie van de Network Device Enrollment Service. Zie [Network Device Enrollment Service Guidance](http://go.microsoft.com/fwlink/p/?LinkId=309016) (Richtlijnen voor de Registratieservice van netwerkapparaten) in de bibliotheek Active Directory Certificate Services op TechNet voor meer informatie.  

    > [!TIP]  
    >  Weergeven om te identificeren welke sjablonen de Network Device Enrollment Service wordt gebruikt, de volgende registersleutel op de server waarop de Network Device Enrollment Service wordt uitgevoerd: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP.  

    > [!NOTE]  
    >  Dit zijn de standaardbeveiligingsmachtigingen die geschikt zijn voor de meeste omgevingen. U kunt echter een alternatieve beveiligingsconfiguratie gebruiken. Voor meer informatie, zie [Certificaatsjabloonmachtigingen voor certificaatprofielen plannen in System Center Configuration Manager](../../protect/plan-design/planning-for-certificate-template-permissions.md).  

3.  Een PKI-certificaat dat clientverificatie ondersteunt naar deze server implementeren. Mogelijk hebt u al een geschikt certificaat geïnstalleerd op de computer dat u kunt gebruiken, of mogelijk moet u (of verkiest u) speciaal voor dit doel een certificaat te implementeren. Voor meer informatie over de vereisten voor dit certificaat raadpleegt u de details voor Servers waarop de Configuration Manager-beleidsmodule uitgevoerd met de functieservice Network Device Enrollment Service in de ** PKI-certificaten voor Servers ** sectie het [PKI-certificaatvereisten voor System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md) onderwerp.  

    > [!TIP]  
    >  Als u ondersteuning bij het implementeren van dit certificaat, kunt u de instructies voor het [het clientcertificaat voor distributiepunten implementeren](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clientdistributionpoint2008_cm2012), omdat de certificaatvereisten dezelfde met één uitzondering zijn:  
    >   
    >  -   Het selectievakje **De persoonlijke sleutel exporteerbaar maken** niet selecteren op tabblad **Afhandeling van aanvragen** van de eigenschappen voor de certificaatsjabloon.  
    >   
    >  U hoeft niet te exporteren van dit certificaat met de persoonlijke sleutel omdat u zich kunt bladeren naar het archief van de lokale Computer en dit selecteren wanneer u de System Center Configuration Manager-beleidsmodule configureert.  

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

7.  Als u wilt dat een certificaat aanvragen dat een kortere geldigheidsperiode dan de certificaatsjabloon die u gebruikt: Deze configuratie is standaard uitgeschakeld voor een ondernemings-CA. Het opdrachtregelprogramma Certutil gebruiken, vervolgens de certificaatservice stopzetten en opnieuw opstarten met behulp de volgende opdrachten, om deze optie op een ondernemings-CA in te schakelen:  

    1.  **certutil - setreg Policy\EditFlags + EDITF_ATTRIBUTEENDDATE**  

    2.  **net stop certsvc**  

    3.  **net start certsvc**  

     Zie [Certificate Services Tools and Settings](http://go.microsoft.com/fwlink/p/?LinkId=309015) (Certificate Services: hulpprogramma's en instellingen) in de PKI-technologiebibliotheek op Technet voor meer informatie.  

8.  Controleer of de registratieservice voor netwerkapparaten werkt door de volgende koppeling als voorbeeld te gebruiken: **https://server.contoso.com/certsrv/mscep/mscep.dll**. U zou de ingebouwde webpagina van de registratieservice voor netwerkapparaten moeten zien. Deze webpagina legt uit waaruit de service bestaat en legt uit dat netwerkapparaten de URL gebruiken om certificaataanvragen te verzenden.  

 Nu dat de registratieservice voor netwerkapparaten en afhankelijkheden zijn geconfigureerd, bent u klaar om het certificaatregistratiepunt nu te installeren en configureren.


## <a name="step-2---install-and-configure-the-certificate-registration-point"></a>Stap 2 - installeren en configureren van het certificaatregistratiepunt.

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

8. Op de **registratiemodus certificaat** te selecteren of u wilt dat deze certificaatregistratiepunt met **proces SCEP certificaataanvragen met zich mee**, of **proces PFX certificaataanvragen met zich mee**. Beide soorten aanvragen door een certificaatregistratiepunt kan niet worden verwerkt, maar u kunt meerdere certificaat maken registratiepunten als u met beide typen certificaten werkt.

7.  Op de **wijst certificaatinstellingen registratie** pagina, de instellingen die u afhankelijk van het type van het certificaat wordt verwerkt, het certificaatregistratiepunt:
    -   Als u hebt geselecteerd **proces SCEP certificaataanvragen met zich mee**, configureer dan het volgende:
        -   **De naam van website**, **HTTPS-poortnummer**, en **virtuele toepassingsnaam** voor het certificaatregistratiepunt. Deze velden worden automatisch ingevuld met standaardwaarden. 
        -   **URL voor de registratieservice voor netwerkapparaten en basis-CA-certificaat** -Klik op **toevoegen**, klik dan in de **toevoegen URL en CA-basiscertificaat** dialoogvenster, geeft u het volgende:
            - **URL voor de Network Device Enrollment Service**: Geef de URL in de volgende indeling: https://*< server_FQDN >*/certsrv/mscep/mscep.dll. Als bijvoorbeeld de FQDN van uw server waarop de registratieservice voor netwerkapparaten wordt uitgevoerd server1.contoso.com is, typt u **https://server1.contoso.com/certsrv/mscep/mscep.dll**.
            - **Basis-CA-certificaat**: Blader naar en selecteer het certificaat (.cer)-bestand dat u maakte en opsloeg in **stap 1: Installeer en configureer de registratieservice en afhankelijkheden**. Dit CA-basiscertificaat kan het certificaatregistratiepunt voor het valideren van de client certificaat voor clientverificatie dat door de System Center Configuration Manager-beleidsmodule wordt gebruikt.  
    - Als u hebt geselecteerd **proces PFX certificaataanvragen met zich mee**, configureer dan het volgende:
        - **Certificeringsinstantie certificeringsinstanties (CA) en de account die nodig zijn voor conenct aan elke Certificeringsinstantie** -Klik op **toevoegen** vervolgens in de **toevoegen van een certificeringsinstantie en de Account** dialoogvenster, geeft u het volgende:
            - **Naam van de instantie van het certificaat** -Geef de naam van uw certificaat CA-server.
            - **Autoriteit Account certificaat** -klikt u op **stellen** selecteren of maken van het account dat machtigingen heeft om te registreren in de sjablonen op de certificeringsinstantie (CA).
        - **Verbindingsaccount registratie van het certificaat** : Selecteer of maak de account die het certificaatregistratiepunt met de Configuration Manager-database verbindt. Alteratively, kunt u het lokale computeraccount van de computer waarop het certificaatregistratiepunt.
        - **Active Directory Certificate publicatieaccount** : Selecteer een account of maak een nieuw account waarmee u certificaten uitgeven naar objecten in Active Directory.
8.  Geef in het dialoogvenster **URL en CA-basiscertificaat toevoegen** het volgende op en klik op **OK**:  

9. Klik op **Volgende** en voltooi de wizard.  

10. Wacht enkele minuten zodat de installatie kan worden voltooid en controleer vervolgens dat het certificaatregistratiepunt geïnstalleerd is aan de hand van een van de volgende methodes:  

    -   Vouw in de werkruimte **Bewaking****Systeemstatus**, klik op **Onderdeelstatus** en zoek naar statusberichten van het onderdeel **SMS_CERTIFICATE_REGISTRATION_POINT**.  

    -   Gebruik op de sitesysteemserver de bestanden *<Installatiepad Configuration Manager\>*\Logs\crpsetup.log en *<Installatiepad Configuration Manager\>*\Logs\crpmsi.log. Een geslaagde installatie retourneert een afsluitcode 0.  

    -   Controleer via een browser dat u verbinding met de URL van het certificaat voor registratie pointâ maken kunt €"bijvoorbeeld: https://server1.contoso.com/CMCertificateRegistration. U moet een **Serverfout**-pagina zien voor de toepassingsnaam, met een HTTP 404-beschrijving.  

11. Zoek het geëxporteerde certificaatbestand voor de basis-CA dat het certificaatregistratiepunt automatisch in de volgende map op de primaire siteservercomputer heeft gemaakt: *<Installatiepad ConfigMgr\>*\inboxes\certmgr.box. Dit bestand opslaan een veilige locatie met veilige toegang wanneer u later de System Center Configuration Manager-beleidsmodule installeert op de server waarop de Network Device Enrollment Service wordt uitgevoerd.  

    > [!TIP]  
    >  Dit certificaat is niet onmiddellijk beschikbaar in deze map. Mogelijk moet u wachten voordat (bijvoorbeeld half uur) voordat System Center Configuration Manager het bestand naar deze locatie kopieert.  


## <a name="step-3----install-the-system-center-configuration-manager-policy-module-for-scep-certificates-only"></a>Stap 3: Installeer System Center Configuration Manager beleidsmodule (voor alleen voor SCEP-certificaten).

U moet installeren en configureren van de System Center Configuration Manager-beleidsmodule op elke server die u hebt opgegeven in **stap 2: Installeer en configureer het certificaatregistratiepunt** als **URL voor de Network Device Enrollment Service** in de eigenschappen voor het certificaatregistratiepunt.  

##### <a name="to-install-the-policy-module"></a>De beleidsmodule installeren  

1.  Op de server die de Network Device Enrollment Service uitvoert, meld u aan als een domeinbeheerder en kopieert u de volgende bestanden van de < ConfigMgrInstallationMedia\>\SMSSETUP\POLICYMODULE\X64 map op de installatiemedia van System Center Configuration Manager naar een tijdelijke map:  

    -   PolicyModule.msi  

    -   PolicyModuleSetup.exe  

    Als u een taalpakketmap hebt op de installatiemedia, kopieert u bovendien deze map en de inhoud hiervan.  

2.  PolicyModuleSetup.exe voor het starten van de System Center Configuration Manager beleidsmodule-installatiewizard van de tijdelijke map uitvoeren.  

3.  Klik op de eerste pagina van de wizard op **Volgende**, aanvaard de licentievoorwaarden en klik vervolgens op **Volgende**.  

4.  Op de pagina **Installatiemap**, aanvaardt u de standaardinstallatiemap voor de beleidsmodule of geeft u een alternatieve map op. Klik vervolgens op **Volgende**.  

5.  Geef op de pagina **Certificaatregistratiepunt** de URL van het certificaatregistratiepunt op met behulp van de FQDN van de sitesysteemserver en de virtuele toepassingsnaam die is opgegeven in de eigenschappen voor het certificaatregistratiepunt. De standaardnaam van de virtuele toepassing is CMCertificateRegistration. Als bijvoorbeeld de sitesysteemserver een FQDN van server1.contoso.com heeft en u de standaardnaam van de virtuele toepassing gebruikte, geeft u **https://server1.contoso.com/CMCertificateRegistration** op.  

6.  Aanvaard de standaardpoort **443** of geef het alternatieve poortnummer op dat door certificaatregistratiepunt wordt gebruikt en klik vervolgens op **Volgende**.  

7.  Op de **clientcertificaat voor de beleidsmodule**bladeren en geef het certificaat voor clientverificatie dat u implementeerde in **stap 1: Installeer en configureer de registratieservice en afhankelijkheden**, en klik vervolgens op **volgende**.  

8.  Op de **Certificaatregistratiepunt** pagina, klikt u op **Bladeren** selecteren voor de basis-CA die u hebt gezocht en opgeslagen op het eind van het geëxporteerde certificaatbestand **stap 2: Installeer en configureer het certificaatregistratiepunt**.  

    > [!NOTE]  
    >  Als u dit certificaatbestand nog niet hebt opgeslagen, bevindt het zich in <Installatiepad Configuration Manager\>\inboxes\certmgr.box op de siteservercomputer.  

9. Klik op **Volgende** en voltooi de wizard.  

 Als u verwijderen van de System Center Configuration Manager-beleidsmodule wilt, gebruikt u **programma's en onderdelen** in het Configuratiescherm. 

 
Nu dat u de configuratiestappen hebt voltooid, bent u klaar om certificaten te implementeren voor gebruikers en apparaten door te maken en implementeren van certificaatprofielen. Zie [Certificaatprofielen in System Center Configuration Manager](../../protect/deploy-use/create-certificate-profiles.md) voor meer informatie over het gebruik van certificaatprofielen.  

