---
title: VPN-profielen in System Center Configuration Manager | Microsoft-documenten
description: VPN-profielen op mobiele apparaten in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
caps.latest.revision: 18
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: aacd11708f9f9bd5b0a2d1b1cd6db3c60a7c0c28
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>VPN-profielen op mobiele apparaten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

VPN-profielen in System Center Configuration Manager naar het VPN-instellingen implementeren voor gebruikers van mobiele apparaten in uw organisatie gebruiken. Wanneer u deze instellingen implementeert, kunt u de eindgebruikersinspanningen die vereist zijn om verbinding met resources op het bedrijfsnetwerk te minimaliseren.  

 Bijvoorbeeld, wilt u alle apparaten waarop iOS-besturingssysteem wordt uitgevoerd met behulp van de instellingen die nodig zijn voor het verbinding maken met een bestandsshare op het bedrijfsnetwerk kunt instellen. U kunt een VPN-profiel met de benodigde instellingen verbinding maakt met het bedrijfsnetwerk en dit profiel vervolgens implementeren voor alle gebruikers die apparaten met iOS in uw hiërarchie. Gebruikers van iOS-apparaten zien de VPN-verbinding staan in de lijst met beschikbare netwerken en kunnen met minimale inspanningen verbinding maken met dit netwerk.  

 Wanneer u een VPN-profiel maakt, kunt u een groot aantal beveiligingsinstellingen opnemen. Bijvoorbeeld, kunt u certificaten voor servervalidatie en clientverificatie die zijn ingesteld met behulp van System Center Configuration Manager-certificaatprofielen. Zie voor meer informatie over certificaatprofielen [Certificaatprofielen in System Center Configuration Manager](../../protect/deploy-use/introduction-to-certificate-profiles.md).  

 ## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>VPN-profielen bij gebruik van Configuration Manager samen met Intune

 Voor de implementatie van profielen voor iOS, Android, Windows Phone-en Windows 8.1-apparaten, moeten deze apparaten zijn ingeschreven in Microsoft Intune. Apparaten op andere platforms kunnen ook worden ingeschreven in Intune. Zie voor meer informatie over het inschrijven [mobiele apparaten beheren met Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx). Deze tabel ziet u het verbindingstype dat wordt ondersteund voor elk apparaatplatform:  

 |Type verbinding|iOS- en Mac OS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8,1|Windows 10 Desktop en Mobile|  
 |---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
 |Cisco AnyConnect|Ja|Ja|Nee|Nee|Nee|Nee|Ja (OMA-URI)|  
 |Pulse Secure|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |F5 Edge Client|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |Dell SonicWALL Mobile Connect|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |Check Point Mobile VPN|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |Microsoft SSL (SSTP)|Nee|Nee|Ja|Ja|Ja|Nee|Nee|  
 |Microsoft Automatic|Nee|Nee|Ja|Ja|Ja|Nee|Ja (OMA-URI)|  
 |IKEv2|Ja (aangepast beleid)|Nee|Ja|Ja|Ja|Ja|Ja (OMA-URI)|  
 |PPTP|Ja|Nee|Ja|Ja|Ja|Nee|Ja (OMA-URI)|  
 |L2TP|Ja|Nee|Ja|Ja|Ja|Nee|Ja (OMA-URI)|  

## <a name="create-vpn-profiles"></a>VPN-profielen maken
[Het maken van VPN-profielen in System Center Configuration Manager](../../protect/deploy-use/create-vpn-profiles.md) bevat algemene informatie over het VPN-profielen maken.

###   <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Windows 10 VPN-functies die beschikbaar zijn bij gebruik van Configuration Manager met Intune  


> [!NOTE]  
> De naam van een VPN-profiel dat gebruikmaakt van Windows 10 VPN-functies kan Unicode- of speciale tekens bevatten.


|Optie|Meer informatie|Type verbinding|  
    |------------|----------------------|---------------------|  
    |**VPN overslaan bij verbinding met Wi-Fi-bedrijfsnetwerk**|De VPN-verbinding worden niet gebruikt wanneer het apparaat is verbonden met het Wi-Fi-bedrijfsnetwerk. Voer de naam van het vertrouwde netwerk die wordt gebruikt om te bepalen of het apparaat is verbonden met het bedrijfsnetwerk.|Alle|  
    |**Netwerkverkeersregels**|De protocollen, lokale poort, externe poort en -adresbereiken op die worden ingeschakeld voor de VPN-verbinding instellen.<br /><br /> **Opmerking:** Als u niet een verkeersregel netwerk maakt, worden alle protocollen, poorten en adresbereiken ingeschakeld. Nadat u een regel hebt gemaakt, wordt alleen de protocollen, poorten en -adresbereiken op die u in die regel of in aanvullende regels opgeeft worden gebruikt door de VPN-verbinding.|Alle|  
    |**Routes**|Routes die de VPN-verbinding gebruikt. Houd rekening met het maken van meer dan 60 routes dat mogelijk het beleid mislukt. |Alle|  
    |**DNS-servers**|DNS-servers die worden gebruikt door de VPN-verbinding nadat de verbinding tot stand is gebracht.|Alle|  
    |**Apps die automatisch verbinding met de VPN-verbinding maken**|U kunt apps toevoegen of importeren van een lijst met apps die automatisch voor de VPN-verbinding gebruikt worden. Het type van de app, bepalen de app-id. Geef het pad van de app voor een bureaubladapp. Geef de familienaam pakket (PFN) voor een universal app. Zie voor meer informatie over de PFN vinden voor een app, [een familienaam pakket niet vinden voor de per-app VPN](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md). |Alle|

> [!IMPORTANT]
> Het is raadzaam dat u alle lijsten met gekoppelde apps die u voor gebruik in de configuratie van per-app VPN compileren beveiligen. Als u het importeren in de lijst per app VPN-app onbevoegde gebruikers de lijst met wijzigingen u wordt mogelijk VPN-toegang verlenen aan apps die geen toegang heeft. Er is één manier kunt u een lijst met app beveiligen met behulp van een toegangsbeheerlijst (ACL).


1.  Op de **verificatiemethode** pagina van de wizard opgeven:  

    -   **Verificatiemethode**: Selecteer de verificatiemethode opgegeven die de VPN-verbinding gebruikt. Beschikbare methoden afhankelijk van het verbindingstype zoals in deze tabel.  

        |Verificatiemethode|Ondersteund&nbsp;verbinding&nbsp;typen|  
        |---------------------------|--------------------------------|  
        |**Certificaten**<br /><br /> **Opmerkingen:**<ul><li>Als het clientcertificaat wordt geverifieerd naar een RADIUS-server, zoals een Network Policy Server kan de alternatieve naam voor onderwerp in het certificaat moet worden ingesteld op principalnaam van gebruiker.</li><li>Selecteer de EKU-id en de waarde van het certificaat certificaatverlener vingerafdruk hash voor Android-implementaties.  Gebruikers moeten Selecteer anders het juiste certificaat handmatig.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Gebruikersnaam en wachtwoord**|<ul><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Microsoft EAP-TTLS**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>IKEv2</li><li>L2TP</li></ul>|  
        |**Door Microsoft beveiligd EAP (PEAP)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Beveiligd Microsoft-wachtwoord (EAP-MSCHAP v2)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Smartcard of ander certificaat**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**MSCHAP v2**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**RSA SecurID** (alleen iOS)|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Computercertificaten gebruiken**|<ul><li>IKEv2</li></ul>|  

         Afhankelijk van de geselecteerde opties, wordt u mogelijk gevraagd om op te geven meer informatie, zoals:  

        -   **De gebruikersreferenties onthouden bij elke aanmelding**: Gebruikersreferenties worden onthouden zodat gebruikers niet hebben ze invoeren telkens wanneer die ze verbinding maken.  

        -   **Selecteer een clientcertificaat voor clientverificatie**: Selecteer de eerder gemaakte client [SCEP-certificaat](create-pfx-certificate-profiles.md) dat wordt gebruikt om de VPN-verbinding te verifiëren.   

            > [!NOTE]  
            >  Voor iOS-apparaten worden, het SCEP-profiel dat u hebt geselecteerd in het VPN-profiel ingesloten. Een regel voor toepasselijkheid wordt voor andere platforms toegevoegd om ervoor te zorgen dat het VPN-profiel niet is geïnstalleerd als het certificaat niet aanwezig is of niet compatibel is.  
            >   
            >  Als het SCEP-certificaat dat u opgeeft, niet compatibel is of niet is geïmplementeerd, wordt wordt het VPN-profiel niet geïnstalleerd op het apparaat.
            >  
            >  Apparaten met iOS ondersteunen alleen RSA SecurID en MSCHAP v2 voor de verificatiemethode wanneer het verbindingstype PPTP. Voorkom melding van fouten door een afzonderlijk PPTP VPN-profiel te implementeren voor apparaten met iOS.  

        - **Voorwaardelijke toegang**
            - Kies **voorwaardelijke toegang inschakelen voor deze VPN-verbinding** om ervoor te zorgen dat de apparaten die verbinding met de VPN-verbinding maken worden getest voor voorwaardelijke toegang naleving voordat u verbinding maakt. Nalevingsbeleid worden beschreven in [nalevingsbeleid voor apparaten in System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/device-compliance-policies.md).
            - Kies **inschakelen eenmalige aanmelding (SSO) met alternatieve certificaat** kiezen van een certificaat dan het certificaat voor VPN-verificatie voor apparaat moet voldoen. Als u deze optie kiest, geeft u de **EKU** (door komma's gescheiden lijst) en **certificaatverlener Hash**, voor het juiste certificaat de VPN-client te vinden.

         - Voor **Windows Information Protection**, bieden de centraal beheerde bedrijfsidentiteit, dat doorgaans het primaire domein van uw organisatie, bijvoorbeeld, *contoso.com*. U kunt meerdere domeinen die uw organisatie eigenaar is van door deze met elkaar te scheiden opgeven de "|" teken. Bijvoorbeeld, *contoso.com|newcontoso.com*.   
              Zie voor meer informatie over Windows Information Protection [maken van een Windows-beveiliging (OHW)-beleid met Microsoft Intune](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/create-wip-policy-using-intune).   

         ![Voorwaardelijke toegang voor VPN configureren](media/vpn-conditional-access.png)

         Wanneer wordt ondersteund door de versie van Windows met Configuration Manager _en_ de geselecteerde autorisatie-methode kunt u **configureren** open het dialoogvenster Eigenschappen voor Windows en configureren van eigenschappen verificatiemethode.  Als **configureren** is uitgeschakeld, een andere methode gebruiken voor het configureren van eigenschappen verificatiemethode.

2.  Op de **Proxy-instellingen** pagina van de **Wizard VPN-profiel**, Controleer de **proxy-instellingen voor dit VPN-profiel configureren** vak als uw VPN-verbinding gebruikmaakt van een proxyserver. Geeft u vervolgens de proxy-servergegevens. Raadpleeg de Windows Server-documentatie voor meer informatie.  

    > [!NOTE]  
    >  Op computers met Windows 8.1, zal het VPN-profiel geen gegevens van de proxy weergeven totdat u verbinding met de VPN-verbinding maakt met behulp van die computer.  


3. Configureer de overige DNS-instellingen (indien nodig).  
 Op de **Configureer Automatische VPN-verbinding** pagina kunt u het volgende:  

    -   **VPN op aanvraag inschakelen**: Gebruik deze optie als u wilt meer DNS-instellingen configureren voor Windows Phone 8.1-apparaten. Deze instelling geldt alleen voor Windows Phone 8.1-apparaten en moet alleen worden ingeschakeld voor VPN-profielen die op Windows Phone 8.1-apparaten kunnen worden geïmplementeerd.

    -   **Lijst met DNS-achtervoegsel** (alleen Windows Phone 8.1-apparaten): Hiermee configureert u domeinen die een VPN-verbinding tot stand brengen. Voor elk domein dat u opgeeft, voegt u het DNS-achtervoegsel, DNS-serveradres en een van de volgende acties op aanvraag:  

        -   **Nooit tot stand brengen**: Open nooit een VPN-verbinding.  

        -   **Indien nodig stand**: Alleen een VPN-verbinding openen als het apparaat verbinding moet maken met resources.  

        -   **Altijd tot stand brengen**: Altijd de VPN-verbinding openen.  

    -   **Samenvoegen**: Kopieert alle DNS-achtervoegsels zijn die u hebt geconfigureerd voor de **lijst met vertrouwde netwerken**.  

    -   **Lijst met vertrouwde netwerken** (alleen Windows Phone 8.1-apparaten): Geef per regel één DNS-achtervoegsel. Als het apparaat zich in een vertrouwd netwerk bevindt, wordt de VPN-verbinding niet geopend.  

    -   **Zoeklijst voor achtervoegsels** (alleen Windows Phone 8.1-apparaten): Geef per regel één DNS-achtervoegsel. Elke DNS-achtervoegsel wordt doorzocht wanneer met behulp van een korte naam verbinding te maken met een website.  

     Bijvoorbeeld, het opgeven van de DNS-achtervoegsels **domain1.contoso.com** en **domain2.contoso.com**, en ga vervolgens naar de URL **http://mywebsite**. De volgende adressen worden doorzocht:  

    -   **http://mywebsite.domain1.contoso.com**  

    -   **http://mywebsite.domain2.contoso.com**  

    > [!NOTE]  
    >  Alleen voor apparaten met Windows Phone 8.1  
    >   
    >  Wanneer de *alle netwerkverkeer via de VPN-verbinding verzenden* optie is geselecteerd *en* de VPN-verbinding gebruikt volledige tunneling, de VPN-verbinding wordt automatisch geopend met behulp van het eerste apparaatprofiel. U opent een verbinding met een ander profiel door het gewenste profiel als standaard instellen.  
    >   
    >  Wanneer de *alle netwerkverkeer via de VPN-verbinding verzenden* optie *niet* geselecteerde *en* de VPN-verbinding gebruikt split tunneling, VPN-verbindingen voor geconfigureerde routes of verbindingsspecifieke DNS-achtervoegsels automatisch geopend.  


4. Op de **ondersteunde Platforms** pagina van de **Wizard VPN-profiel**, selecteer de besturingssystemen waarop het VPN-profiel wordt geïnstalleerd of kies **Alles selecteren** voor het installeren van het VPN-profiel op alle beschikbare besturingssystemen.  

5. Sluit de wizard af. De **VPN-profielen** knooppunt in de **activa en naleving** werkruimte ziet u het nieuwe VPN-profiel.  


**Implementeer**: Zie [implementeren Wi-Fi, VPN-, e-mail en certificaatprofielen](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) voor meer informatie over het implementeren van VPN-profielen.

### <a name="next-steps"></a>Volgende stappen  
 Gebruik de volgende onderwerpen om te plannen, instellen, gebruiken en onderhouden van VPN-profielen in Configuration Manager.  

-   [Vereisten voor VPN-profielen in System Center Configuration Manager](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Beveiliging en privacy voor VPN-profielen in System Center Configuration Manager](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)

