---
title: VPN-profielen
titleSuffix: Configuration Manager
description: VPN-profielen op mobiele apparaten in System Center Configuration Manager.
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
caps.latest.revision: ''
caps.handback.revision: ''
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 1d98cd234b2444873f1ffa5819af74d507dfa9c1
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/27/2018
---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>VPN-profielen op mobiele apparaten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

VPN-profielen in System Center Configuration Manager voor het VPN-instellingen implementeren voor gebruikers van mobiele apparaten in uw organisatie gebruiken. Wanneer u deze instellingen implementeert, kunt u de eindgebruikersinspanningen die vereist zijn om verbinding met resources op het bedrijfsnetwerk te minimaliseren.  

 U wilt bijvoorbeeld alle apparaten waarop iOS-besturingssysteem wordt uitgevoerd met behulp van de instellingen die nodig zijn om verbinding maken met een bestandsshare op het bedrijfsnetwerk kunt instellen. U kunt een VPN-profiel met de benodigde instellingen verbinding maken met het bedrijfsnetwerk en vervolgens implementeert dit profiel voor alle gebruikers die hebben apparaten met iOS in uw hiërarchie maken. Gebruikers van iOS-apparaten zien de VPN-verbinding staan in de lijst met beschikbare netwerken en kunnen met minimale inspanningen verbinding maken met dit netwerk.  

 Wanneer u een VPN-profiel maakt, kunt u een groot aantal beveiligingsinstellingen opnemen. U kunt bijvoorbeeld opgeven dat certificaten voor servervalidatie en clientverificatie die zijn ingesteld met behulp van System Center Configuration Manager-certificaatprofielen. Zie voor meer informatie over certificaatprofielen [Certificaatprofielen in System Center Configuration Manager](../../protect/deploy-use/introduction-to-certificate-profiles.md).  

 ## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>VPN-profielen wanneer Configuration Manager samen met Intune

 Om profielen te implementeren op iOS, Android, Windows Phone en Windows 8.1-apparaten, moeten deze apparaten worden geregistreerd bij Microsoft Intune. Apparaten op andere platforms kunnen ook worden ingeschreven bij Intune. Zie voor meer informatie over het inschrijven [mobiele apparaten beheren met Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx). Deze tabel ziet u het verbindingstype dat wordt ondersteund voor elk apparaatplatform:  

 |Type verbinding|iOS en Mac OS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8,1|Windows 10 Desktop en Mobile|  
 |---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
 |Cisco AnyConnect|Ja|Ja|Nee|Nee|Nee|Nee|Nee|
 |Cisco (IPSec)|alleen voor iOS|Nee|Nee|Nee|Nee|Nee|Nee|  
 |Pulse Secure|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |F5 Edge Client|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |Dell SonicWALL Mobile Connect|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |Check Point Mobile VPN|Ja|Ja|Ja|Nee|Ja|Ja|Ja|  
 |Microsoft SSL (SSTP)|Nee|Nee|Ja|Ja|Ja|Nee|Nee|  
 |Microsoft Automatic|Nee|Nee|Ja|Ja|Ja|Nee|Ja|  
 |IKEv2|Ja (aangepast beleid, iOS 9 of hoger)|Nee|Ja|Ja|Ja|Ja|Ja|  
 |PPTP|Ja|Nee|Ja|Ja|Ja|Nee|Ja|  
 |L2TP|Ja|Nee|Ja|Ja|Ja|Nee|Ja (OMA-URI)|  

## <a name="create-vpn-profiles"></a>VPN-profielen maken
[Het VPN-profielen maken in System Center Configuration Manager](../../protect/deploy-use/create-vpn-profiles.md) bevat algemene informatie over het maken van VPN-profielen.

## <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Windows 10 VPN-functies die beschikbaar zijn wanneer u Configuration Manager met Intune  


> [!NOTE]  
> De naam van een VPN-profiel dat gebruikmaakt van Windows 10 VPN-functies kan Unicode- of speciale tekens bevatten.


|Optie|Meer informatie|Type verbinding|  
    |------------|----------------------|---------------------|  
    |**VPN overslaan bij verbinding met Wi-Fi-bedrijfsnetwerk**|De VPN-verbinding niet gebruikt wanneer het apparaat is verbonden met het Wi-Fi-bedrijfsnetwerk. Voer de naam van het vertrouwde netwerk dat wordt gebruikt om te bepalen of het apparaat is verbonden met het bedrijfsnetwerk.|Alle|  
    |**Netwerkverkeersregels**|Stel de protocollen, de lokale poort, de externe poort en de adresbereiken die worden ingeschakeld voor de VPN-verbinding.<br /><br /> **Opmerking:** Als u geen een netwerkverkeersregel maakt, worden alle protocollen, poorten en adresbereiken ingeschakeld. Nadat u een regel maakt, worden alleen de protocollen, poorten en adresbereiken die u in die regel of in aanvullende regels opgeeft door de VPN-verbinding gebruikt.|Alle|  
    |**Routes**|Routes die door de VPN-verbinding wordt gebruikt. Houd er rekening mee dat het maken van meer dan 60 routes leiden het beleid tot kan mislukt. |Alle|  
    |**DNS-servers**|DNS-servers die worden gebruikt door de VPN-verbinding nadat de verbinding tot stand is gebracht.|Alle|  
    |**Apps die automatisch verbinding met de VPN-verbinding maken**|U kunt apps toevoegen of importeren van lijsten met apps die automatisch van de VPN-verbinding gebruikmaken. De app-id is afhankelijk van het type app. Geef het bestandspad van de app voor een bureaublad-app. Geef de familie pakketnaam (PFN) voor een universele app. Zie voor meer informatie over de PFN zoeken voor een app, [een package family name voor VPN per app zoeken](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md). |Alle|

> [!IMPORTANT]
> Het is raadzaam dat u alle lijsten met gekoppelde apps die u voor gebruik in de configuratie van per-app VPN compileert, beveiligt. Als een onbevoegde gebruiker uw lijst wijzigt en u deze naar de app-lijst per app VPN importeren, wordt u mogelijk machtigt u VPN-toegang tot apps die geen toegang mogen hebben. Er is een manier die u kunt een lijst met Apps beveiligen met behulp van een toegangsbeheerlijst (ACL).

1. Op de **ondersteunde Platforms** pagina van de **Wizard VPN-profiel**, selecteer de besturingssystemen waarop het VPN-profiel wordt geïnstalleerd of kies **Alles selecteren** voor het installeren van het VPN-profiel op alle beschikbare besturingssystemen.  
2.  Op de **verificatiemethode** pagina van de wizard opgeven:  

    -   **Verificatiemethode**: Selecteer de verificatiemethode die door de VPN-verbinding wordt gebruikt. Beschikbare methoden, is afhankelijk van het verbindingstype zoals weergegeven in deze tabel.  

        |Verificatiemethode|Ondersteund&nbsp;verbinding&nbsp;typen|  
        |---------------------------|--------------------------------|  
        |**Certificaten**<br /><br /> **Opmerkingen:**<ul><li>Als het clientcertificaat wordt geverifieerd met een RADIUS-server, zoals een Network Policy Server, moet de alternatieve naam voor onderwerp in het certificaat worden ingesteld op principalnaam van gebruiker.</li><li>Selecteer de EKU-id en certificaatverlener vingerafdruk van het hash-waarde voor Android-implementaties.  Het juiste certificaat moeten anders handmatig door gebruikers selecteren.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Gebruikersnaam en wachtwoord**|<ul><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> Check Point Mobile VPN</li></ul>|  
        |**Microsoft EAP-TTLS**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>IKEv2</li><li>L2TP</li></ul>|  
        |**Door Microsoft beveiligd EAP (PEAP)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Beveiligd Microsoft-wachtwoord (EAP-MSCHAP v2)**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Smartcard of ander certificaat**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**MSCHAP v2**|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**RSA SecurID** (alleen iOS)|<ul><li>Microsoft SSL (SSTP)</li><li>Microsoft Automatic</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Computercertificaten gebruiken**|<ul><li>IKEv2</li></ul>|  

         Afhankelijk van de geselecteerde opties, wordt u mogelijk gevraagd om op te geven van meer informatie, zoals:  

        -   **De gebruikersreferenties onthouden bij elke aanmelding**: Gebruikersreferenties worden onthouden zodat gebruikers hoeven geen ze telkens wanneer die ze verbinden invoeren.  

        -   **Selecteer een clientcertificaat voor clientverificatie**: Selecteer de eerder gemaakte client [SCEP-certificaat](create-pfx-certificate-profiles.md) die wordt gebruikt voor het verifiëren van de VPN-verbinding.   

            > [!NOTE]  
            >  Voor iOS-apparaten als de SCEP-profiel dat u selecteert in het VPN-profiel wordt ingesloten. Voor andere platforms wordt een toepassingsregel toegevoegd om ervoor te zorgen dat het VPN-profiel niet is geïnstalleerd als het certificaat niet aanwezig is of niet compatibel is.  
            >   
            >  Als de SCEP-certificaat dat u opgeeft, niet compatibel is of niet is geïmplementeerd, wordt wordt het VPN-profiel niet geïnstalleerd op het apparaat.
            >  
            >  Apparaten met iOS ondersteunen alleen RSA SecurID en MSCHAP v2 voor de methode voor verificatie wanneer het verbindingstype PPTP is. Voorkom melding van fouten door een afzonderlijk PPTP VPN-profiel te implementeren voor apparaten met iOS.  

        - **Voorwaardelijke toegang**
            - Kies **voorwaardelijke toegang inschakelen voor deze VPN-verbinding** om ervoor te zorgen dat apparaten die verbinding met de VPN-verbinding maken zijn getest voor naleving van voorwaardelijke toegang voordat u verbinding maakt. Beleidsregels voor nalevingsbeleid die worden beschreven in [nalevingsbeleid voor apparaten in System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/device-compliance-policies.md).
            - Kies **Schakel eenmalige aanmelding (SSO) met een alternatief certificaat** een certificaat dan het certificaat voor VPN-verificatie voor apparaatcompatibiliteit kiezen. Als u deze optie kiest, geeft u de **EKU** (door komma's gescheiden lijst) en **Hash voor de verlener**, voor het juiste certificaat de VPN-client te vinden.

         - Voor **Windows Information Protection**, bieden de centraal beheerde zakelijke identiteit, dat meestal het primaire domein van uw organisatie, bijvoorbeeld, *contoso.com*. U kunt meerdere domeinen die uw organisatie eigenaar is van door deze met elkaar te scheiden opgeven de ' | ' teken. Bijvoorbeeld: *contoso.com|newcontoso.com*.   
            Zie voor meer informatie over Windows Information Protection [maken van een Windows-beveiliging (OHW)-beleid met Microsoft Intune](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/create-wip-policy-using-intune).   

         ![Voorwaardelijke toegang voor VPN-verbinding configureren](media/vpn-conditional-access.png)

         Wanneer wordt ondersteund door de versie van Windows die wordt uitgevoerd van Configuration Manager _en_ de geselecteerde autorisatiemethode die u kunt kiezen **configureren** opent het dialoogvenster Eigenschappen van Windows en configureren van eigenschappen verificatiemethode.  Als **configureren** is uitgeschakeld, een andere methode gebruiken voor het configureren van eigenschappen verificatiemethode.

3.  Op de **Proxy-instellingen** pagina van de **Wizard VPN-profiel**, Controleer de **proxy-instellingen voor dit VPN-profiel configureren** vak als uw VPN-verbinding gebruikmaakt van een proxyserver. Vervolgens de proxy-serverinformatie opgeven. Raadpleeg de Windows Server-documentatie voor meer informatie.  

    > [!NOTE]  
    >  Op computers met Windows 8.1, wordt het VPN-profiel niet de proxy-informatie weergegeven totdat u een verbinding met de VPN-verbinding maken met behulp van die computer.  


4. Meer DNS-instellingen configureren (indien nodig).  

5. Sluit de wizard af. De **VPN-profielen** knooppunt in de **activa en naleving** werkruimte ziet u het nieuwe VPN-profiel.  


**Implementeer**: Zie [implementeren Wi-Fi, VPN, e-mail en certificaatprofielen](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) voor meer informatie over het implementeren van VPN-profielen.

## <a name="next-steps"></a>Volgende stappen  
 Gebruik de volgende onderwerpen voor hulp bij het plannen, instellen, te gebruiken en onderhouden van VPN-profielen in Configuration Manager.  

-   [Vereisten voor VPN-profielen in System Center Configuration Manager](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Beveiliging en privacy voor VPN-profielen in System Center Configuration Manager](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
