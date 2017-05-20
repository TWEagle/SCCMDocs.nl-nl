---
title: Inleiding tot certificaatprofielen | Microsoft-documenten
description: Informatie over de werking van certificaatprofielen in System Center Configuration Manager met Active Directory Certificate Services.
ms.custom: na
ms.date: 03/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
caps.latest.revision: 7
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: aa8924a013ebdbee888cab33001fddbe7ad2d67e
ms.openlocfilehash: 1864f814152233d3c67bd83a96623e4a6e051569
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="introduction-to-certificate-profiles-in-system-center-configuration-manager"></a>Inleiding tot certificaatprofielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Certificaatprofielen werken met Active Directory Certificate Services en de Network Device Enrollment Service-rol om verificatiecertificaten te richten voor beheerde apparaten, zodat gebruikers naadloos toegang krijgen bedrijfsbronnen tot. Zo kunt u bijvoorbeeld certificaatprofielen maken en implementeren om gebruikers de benodigde certificaten te geven om VPN-verbindingen en draadloze verbindingen te initiëren. 

Met certificaatprofielen kunnen gebruikersapparaten automatisch worden geconfigureerd, zodat bedrijfsbronnen zoals Wi-Fi-netwerken en VPN-servers toegankelijk zijn zonder handmatig certificaten te hoeven installeren of een buiten-bandproces te hoeven gebruiken. Certificaatprofielen kunnen ook helpen om bedrijfsbronnen veilig te houden, aangezien u veiligere instellingen kunt gebruiken die worden ondersteund door uw zakelijke PKI (Public Key Infrastructure). U kunt bijvoorbeeld serververificatie vereisen voor alle Wi-Fi- en VPN-verbindingen omdat u de vereiste certificaten hebt ingericht op de beheerde apparaten.   

Certificaatprofielen bieden de volgende beheermogelijkheden:  

-   Certificaatregistratie en -vernieuwing vanuit een bedrijfscertificeringsinstantie (CA) voor apparaten waarop iOS, Windows 8.1, Windows RT 8.1, Windows 10 Desktop en Mobile en Android wordt uitgevoerd. Deze certificaten kunnen vervolgens worden gebruikt voor Wi-Fi en VPN-verbindingen.  

-   Implementatie van certificaten van vertrouwde basiscertificeringsinstanties en tussenliggende certificeringsinstanties voor de configuratie van een vertrouwensketen op apparaten voor VPN- en Wi-Fi-verbindingen wanneer serververificatie vereist is.  

-   De geïnstalleerde certificaten bewaken en hierover rapporteren.  

**Voorbeeld:** Alle werknemers moeten verbinding kunnen maken met Wi-Fi-hotspots op meerdere zakelijke locaties. Implementeren van de certificaten die nodig zijn voor het verbinding maken met Wi-Fi- en Wi-Fi-profielen implementeren die verwijzen naar het certificaat zodat naadloos gebruikersverbinding wordt gemaakt.  

**Voorbeeld:** U bent klaar een PKI en wilt overstappen op een flexibelere en veiligere methode voor het leveren van certificaten waarmee gebruikers toegang tot bedrijfsbronnen krijgen vanaf hun persoonlijke apparaten zonder beveiligingsrisico's. Certificaatprofielen configureren met instellingen en protocollen die worden ondersteund voor het specifieke apparaatplatform. De apparaten kunnen deze certificaten vervolgens automatisch aanvragen van een inschrijvingsserver op internet. Configureer vervolgens de VPN-profielen voor het gebruik van deze certificaten zodat het apparaat toegang bedrijfsbronnen tot.  

## <a name="types-of-certificate-profiles"></a>Typen certificaatprofielen  
 Er zijn drie soorten certificaatprofielen:  

-   **Vertrouwd CA-certificaat** -kunt u bij de implementatie van een vertrouwde basiscertificeringsinstantie of een tussenliggende CA-certificaat om een certificaatvertrouwensketen in te richten voor wanneer het apparaat een server moet verifiëren.  

-   **Simple Certificate Enrollment Protocol (SCEP)** -kunt u een certificaat voor een apparaat of gebruiker aanvragen door het SCEP-protocol en de Network Device Enrollment Service op een server met Windows Server 2012 R2.
-   **Persoonlijke gegevens exchange (.pfx)** -kunt u een certificaat pfx (ook wel bekend als PKCS #12) voor een apparaat of gebruiker aanvragen.

    > [!NOTE]  
    >  U moet een certificaatprofiel van het type maken **vertrouwde CA-certificaat** voordat u kunt een **Simple Certificate Enrollment Protocol (SCEP)** profiel van het certificaat.  

## <a name="requirements-and-supported-platforms"></a>Vereisten en ondersteunde platforms  
 Voor het implementeren van certificaatprofielen met SCEP gebruiken, moet u het certificaatregistratiepunt installeren op een sitesysteemserver in de centrale beheersite of in een primaire site. U moet ook een beleidsmodule voor NDES, de Configuration Manager-beleidsmodule op een server waarop Windows Server 2012 R2 met de rol Active Directory Certificate Services en een werkende NDES die toegankelijk is voor de apparaten die de certificaten nodig hebben installeren. Hiervoor moet de NDES moet toegankelijk zijn vanaf Internet, bijvoorbeeld in een afgeschermd subnet (ook wel een DMZ genoemd) voor de apparaten die zijn geregistreerd door Microsoft Intune.  

 Zie voor meer informatie over hoe de Network Device Enrollment Service ondersteuning biedt voor een beleidsmodule zodat dat Configuration Manager certificaten kunt implementeren, [een beleidsmodule gebruiken met de Network Device Enrollment Service](http://go.microsoft.com/fwlink/p/?LinkId=328657).  

 Configuration Manager ondersteunt de implementatie van certificaten in verschillende certificaatarchieven, afhankelijk van de vereisten, het apparaattype en besturingssysteem. De volgende apparaten en besturingssystemen worden ondersteund:  

-   Windows RT 8.1  

-   Windows 8.1  

-   Windows Phone 8,1  

-   Windows 10 Desktop en Mobile  

-   iOS  

-   Android  

> [!IMPORTANT]  
>  Voor de implementatie van profielen voor Android, iOS, Windows Phone-en ingeschreven Windows 8.1 of hoger apparaten deze apparaten moeten [die zijn ingeschreven bij Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx).   

Een typisch scenario voor System Center Configuration Manager is het installeren van vertrouwde basiscertificeringsinstanties om Wi-Fi en VPN-servers wanneer de verbinding gebruikmaakt van EAP-TLS-, EAP-TTLS- en PEAP-verificatieprotocollen,- en IKEv2-, L2TP/IPsec- en Cisco IPsec VPN-tunnelprotocollen.  

U moet zorgen dat er een zakelijk certificaat van een vertrouwde basiscertificeringsinstantie is geïnstalleerd op het apparaat voordat het apparaat certificaten kan aanvragen door een SCEP-certificaatprofiel te gebruiken.  

U kunt in een SCEP-certificaatprofiel diverse instellingen opgeven om aangepaste certificaten aan te vragen voor verschillende omgevingen of connectiviteitsvereisten. De **wizard Certificaatprofiel maken** bevat twee pagina's voor registratieparameters. De eerste pagina, **SCEP-registratie**, bevat instellingen voor de registratieaanvraag en voor de installatielocatie van het certificaat. Op de tweede pagina, **Certificaateigenschappen**, wordt het aangevraagde certificaat zelf beschreven.  

## <a name="deploying-certificate-profiles"></a>Certificaatprofielen implementeren  
 Wanneer u een certificaatprofiel implementeert, worden de certificaatbestanden binnen het profiel geïnstalleerd op clientapparaten. Ook eventuele SCEP-parameters worden geïmplementeerd, en de SCEP-aanvragen worden verwerkt op het clientapparaat. U kunt certificaatprofielen implementeren voor gebruikers- of apparaatverzamelingen en het doelarchief voor elk certificaat opgeven. Aan de hand van regels voor toepasselijkheid wordt bepaald of de certificaten kunnen worden geïnstalleerd op het apparaat. Wanneer certificaatprofielen worden geïmplementeerd in gebruikersverzamelingen, bepaalt gebruikersapparaataffiniteit welke van de Gebruikersapparaten de certificaten. Wanneer certificaatprofielen die gebruikerscertificaten bevatten standaard worden geïmplementeerd in apparaatverzamelingen, worden de certificaten op elke primaire apparaten van de gebruikers worden geïnstalleerd. U kunt dit gedrag wijzigen zodat het certificaat op een van de Gebruikersapparaten installeren op de **SCEP-registratie** pagina van de **Wizard Certificaatprofiel maken**. Verder worden gebruikerscertificaten niet geïmplementeerd op apparaten als dit werkgroepcomputers zijn.  

## <a name="monitoring-certificate-profiles"></a>Certificaatprofielen bewaken  

U kunt de implementatie van certificaatprofielen bewaken door compatibiliteitsresultaten of rapporten te bekijken. Deze methoden worden beschreven in [certificaatprofielen bewaken](/sccm/protect/deploy-use/monitor-certificate-profiles).


## <a name="automatic-revocation-of-certificates"></a>Automatische intrekking van certificaten  
 System Center Configuration Manager trekt automatisch gebruikers- en computercertificaten die zijn geïmplementeerd met behulp van certificaatprofielen in de volgende omstandigheden:  

-   Het apparaat buiten gebruik is gesteld van System Center Configuration Manager-beheer.  

-   Het apparaat wordt selectief gewist.  

-   Het apparaat wordt geblokkeerd vanuit de System Center Configuration Manager-hiërarchie.  

 Om de certificaten in te trekken, wordt er vanaf de siteserver een intrekkingsopdracht verzonden naar de uitgevende certificeringsinstantie. De reden voor de intrekking is **Activiteit gestaakt**.  
