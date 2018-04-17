---
title: Inleiding tot certificaatprofielen
titleSuffix: Configuration Manager
description: Meer informatie over de werking van certificaatprofielen in System Center Configuration Manager met Active Directory Certificate Services.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
caps.latest.revision: 7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0e82c9704c0505c8c7ed9ef3d04260ca74026999
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="introduction-to-certificate-profiles-in-system-center-configuration-manager"></a>Inleiding tot certificaatprofielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Certificaatprofielen werken met Active Directory Certificate Services en de functie Network Device Enrollment Service (NDES). Maak en implementeer verificatiecertificaten voor beheerde apparaten, zodat gebruikers eenvoudig toegang bedrijfsbronnen tot. U kunt bijvoorbeeld maken en implementeren van certificaatprofielen om de benodigde certificaten voor gebruikers verbinding maken met VPN- en draadloze verbindingen.

Certificaatprofielen kunnen Gebruikersapparaten automatisch geconfigureerd. Gebruikers toegang tot bedrijfsresources, zoals Wi-Fi-netwerken en VPN-servers zonder dat certificaten handmatig te installeren of via een out-of-band-proces. Certificaat profielen helpen om bedrijfsbronnen veilig omdat u veiligere instellingen die worden ondersteund door uw onderneming openbare-sleutelinfrastructuur (PKI) kunt gebruiken. Bijvoorbeeld serververificatie vereisen voor alle Wi-Fi en VPN-verbindingen, omdat u de vereiste certificaten op de beheerde apparaten hebt geïmplementeerd.   

Certificaatprofielen bieden de volgende beheermogelijkheden:  

-   Certificaatregistratie en -vernieuwing vanuit een bedrijfscertificeringsinstantie (CA) voor apparaten met iOS, Windows 8.1, Windows RT 8.1, Windows 10 Desktop en Mobile en Android. Deze certificaten kunnen vervolgens worden gebruikt voor Wi-Fi en VPN-verbindingen.  

-   Implementatie van certificaten van vertrouwde basiscertificeringsinstanties en tussenliggende CA-certificaten. Deze certificaten configureren een vertrouwensketen op apparaten voor VPN en Wi-Fi-verbindingen wanneer serververificatie vereist is.  

-   De geïnstalleerde certificaten bewaken en hierover rapporteren.  

**Voorbeeld:** Alle medewerkers moeten met Wi-Fi-hotspots op meerdere bedrijfslocaties verbinding kunnen maken. Om eenvoudig verbinding, moet u eerst de certificaten die nodig zijn voor het verbinding maken met Wi-Fi implementeren. Wi-Fi-profielen die verwijzen naar het certificaat vervolgens te implementeren.  

**Voorbeeld:** Hebt u een PKI. U wilt overstappen op een flexibelere en veiligere methode voor het implementeren van certificaten. Gebruikers moeten kunnen toegang krijgen tot bedrijfsbronnen vanaf hun persoonlijke apparaten zonder beveiligingsrisico. Certificaatprofielen configureren met instellingen en protocollen die worden ondersteund voor het specifieke apparaatplatform. De apparaten kunnen deze certificaten vervolgens automatisch aanvragen van een inschrijvingsserver op internet. Configureer vervolgens de VPN-profielen voor het gebruik van deze certificaten, zodat het apparaat toegang bedrijfsbronnen tot.  



## <a name="types-of-certificate-profiles"></a>Typen certificaatprofielen  
 Er zijn drie soorten certificaatprofielen:  

-   **Vertrouwd CA-certificaat** -implementeren van een vertrouwde basis-CA of een tussenliggende CA-certificaat. Deze certificaten vormen een vertrouwensketen wanneer het apparaat een server moet verifiëren.  

-   **Simple Certificate Enrollment Protocol (SCEP)** -een certificaat voor een apparaat of gebruiker aanvragen door het SCEP-protocol. Dit type is vereist voor de functie Network Device Enrollment Service (NDES) op een server met Windows Server 2012 R2 of hoger.

    Maken van een **Simple Certificate Enrollment Protocol (SCEP)** certificaatprofiel, maakt u eerst een **vertrouwde CA-certificaat** profiel.

-   **Personal information exchange (.pfx)** -geen pfx (ook wel bekend als PKCS #12) certificaten aanvragen voor een apparaat of gebruiker.<!--1321368-->  

    U kunt PFX-certificaatprofielen maken door een van beide [importeren referenties](/sccm/mdm/deploy-use/import-pfx-certificate-profiles) van bestaande certificaten gebruiken of door [definiëren van een certificaat](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) autoriteit voor het verwerken van aanvragen.

    > [!Note]  
    > Configuration Manager deze optionele functie standaard niet ingeschakeld. Voordat u deze gebruikt, moet u deze functie inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  

    Vanaf versie 1706, kunt u Microsoft of Entrust als certificeringsinstanties voor **Personal information exchange (.pfx)** certificaten.


## <a name="requirements-and-supported-platforms"></a>Vereisten en ondersteunde platforms  
Installeer het certificaatregistratiepunt wordt gehost op een sitesysteemserver voor het implementeren van certificaatprofielen met SCEP. Ook installeren van een beleidsmodule voor NDES, de Configuration Manager-beleidsmodule op een server met Windows Server 2012 R2 of hoger. Deze server moet de functie Active Directory Certificate Services en een werkende NDES die toegankelijk is voor de apparaten waarvoor de certificaten. Voor apparaten die zijn geregistreerd door Microsoft Intune, moet het NDES toegankelijk zijn vanaf Internet. Bijvoorbeeld in een afgeschermd subnet, ook wel een DMZ genoemd.  

PFX-certificaten moeten echter ook een certificaatregistratiepunt. Geef ook op de certificeringsinstantie (CA) voor het certificaat en de relevante-referenties. Vanaf versie 1706, kunt u Microsoft of Entrust opgeven als certificeringsinstanties.  

Zie voor meer informatie over de manier waarop de Network Device Enrollment Service een beleidsmodule ondersteunt zodat dat Configuration Manager certificaten kunt implementeren, [een beleidsmodule gebruiken met de Network Device Enrollment Service](http://go.microsoft.com/fwlink/p/?LinkId=328657).  

Afhankelijk van de vereisten, wordt met Configuration Manager implementeren certificaten in verschillende certificaatarchieven ondersteunt op verschillende typen apparaten en besturingssystemen. De volgende apparaten en besturingssystemen worden ondersteund:  

-   Windows RT 8.1  

-   Windows 8.1  

-   Windows Phone 8,1  

-   Windows 10 Desktop en Mobile  

-   iOS  

-   Android  

> [!IMPORTANT]  
>  Om profielen te implementeren naar Android, iOS, Windows Phone-en ingeschreven Windows 8.1 of hoger, deze apparaten moet [ingeschreven bij Microsoft Intune](/intune/device-enrollment).   

Een typisch scenario voor Configuration Manager is het installeren van de vertrouwde basis-CA-certificaten voor het verifiëren van Wi-Fi en VPN-servers wanneer de verbinding gebruik wordt gemaakt van EAP-TLS, EAP-TTLS en PEAP-verificatieprotocollen, en IKEv2-, L2TP/IPsec en Cisco IPsec VPN-tunneling protocollen.  

Een onderneming basis-CA-certificaat moet worden geïnstalleerd op het apparaat voordat het apparaat certificaten aanvragen kan met behulp van een SCEP-certificaatprofiel.  

U kunt instellingen opgeven in een SCEP-certificaatprofiel aangepaste certificaten voor verschillende omgevingen of connectiviteitsvereisten aanvragen. De **Wizard Certificaatprofiel maken** bevat twee pagina's voor registratieparameters. De eerste **SCEP-registratie**, bevat instellingen voor de registratieaanvraag en het certificaat te installeren. Op de tweede pagina, **Certificaateigenschappen**, wordt het aangevraagde certificaat zelf beschreven.  

## <a name="deploying-certificate-profiles"></a>Certificaatprofielen implementeren  
 Wanneer u een certificaatprofiel implementeert, worden de certificaatbestanden binnen het profiel geïnstalleerd op clientapparaten. Eventuele SCEP-parameters zijn ook geïmplementeerd en de SCEP-aanvragen worden verwerkt op het clientapparaat. U kunt certificaatprofielen implementeren voor gebruikers- of apparaatverzamelingen en het doelarchief voor elk certificaat opgeven. Aan de hand van regels voor toepasselijkheid wordt bepaald of de certificaten kunnen worden geïnstalleerd op het apparaat. Wanneer certificaatprofielen worden geïmplementeerd in gebruikersverzamelingen, bepaalt apparaataffiniteit van gebruikers die de Gebruikersapparaten de certificaten te installeren. Wanneer certificaatprofielen die gebruikerscertificaten bevatten op apparaatverzamelingen worden geïmplementeerd, standaard zijn de certificaten geïnstalleerd op elk van de primaire apparaten van de gebruikers. U kunt dit gedrag wijzigen zodat het certificaat op een van de apparaten van de gebruikers installeren op de **SCEP-registratie** pagina van de **Wizard Certificaatprofiel maken**. Als de apparaten werkgroepcomputers behoren, worden gebruikerscertificaten niet geïmplementeerd.  

## <a name="monitoring-certificate-profiles"></a>Certificaatprofielen bewaken  

U kunt de implementatie van certificaatprofielen bewaken door nalevingsresultaten of rapporten te bekijken. Deze methoden worden beschreven in [certificaatprofielen bewaken](/sccm/protect/deploy-use/monitor-certificate-profiles).


## <a name="automatic-revocation-of-certificates"></a>Automatische intrekking van certificaten  
 System Center Configuration Manager worden automatisch ingetrokken voor gebruikers- en computercertificaten die zijn geïmplementeerd met behulp van certificaatprofielen in de volgende omstandigheden:  

-   Het apparaat wordt buiten gebruik gesteld vanuit System Center Configuration Manager-beheer.  

-   Het apparaat wordt selectief gewist.  

-   Het apparaat wordt geblokkeerd vanuit de System Center Configuration Manager-hiërarchie.  

 Om de certificaten in te trekken, wordt er vanaf de siteserver een intrekkingsopdracht verzonden naar de uitgevende certificeringsinstantie. De reden voor de intrekking is **Activiteit gestaakt**.  
