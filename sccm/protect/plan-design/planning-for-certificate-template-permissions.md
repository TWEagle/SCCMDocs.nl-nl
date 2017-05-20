---
title: Certificaatprofielen plannen | Microsoft-documenten
description: Meer informatie over het plannen van de machtigingen die u nodig hebt voor het configureren van de certificaatsjablonen die gebruikmaakt van System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: eab0e09d-b09e-4c14-ab14-c5f87472522e
caps.latest.revision: 5
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 832be8c9fda727804f57e83768cd8799db722c67
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-certificate-template-permissions-for-certificate-profiles-in-system-center-configuration-manager"></a>Certificaatsjabloonmachtigingen voor certificaat voor certificaatprofielen in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


De volgende informatie kunt u van plan bent voor het configureren van machtigingen voor de certificaatsjablonen die door System Center Configuration Manager gebruikt wanneer u certificaatprofielen implementeert.  

## <a name="default-security-permissions-and-considerations"></a>Standaardbeveiligingsmachtigingen en overwegingen hiervoor  
 De standaardbeveiligingsmachtigingen die vereist zijn voor de certificaatsjablonen die door System Center Configuration Manager gebruikt certificaten voor gebruikers en apparaten aanvragen zijn als volgt:  

-   Lezen en Registreren voor het account waarvan de toepassingsgroep Registratieservice voor netwerkapparaten gebruik maakt  

-   Lezen voor het account dat de System Center Configuration Manager-console wordt uitgevoerd  

 Zie voor meer informatie over deze beveiligingsmachtigingen [certificaatinfrastructuur configureren](../deploy-use/certificate-infrastructure.md).  

 Wanneer u deze standaardconfiguratie gebruikt, kunnen gebruikers en apparaten niet rechtstreeks certificaten van de certificaatsjablonen aanvragen, en moeten alle aanvragen worden geïnitieerd door de registratieservice voor netwerkapparaten. Dit is een belangrijke beperking, omdat deze certificaatsjablonen moeten worden geconfigureerd met **Met de aanvraag meeleveren** voor het certificaat Onderwerp, wat betekent dat er een risico op imitatie bestaat als een kwaadwillende gebruiker of een apparaat waarmee is geknoeid, een certificaat aanvraagt. In de standaardconfiguratie moet een dergelijke aanvraag worden geïnitieerd door de registratieservice voor netwerkapparaten. Dit risico op imitatie blijft echter bestaan als er wordt geknoeid met de service waarop de registratieservice voor netwerkapparaten wordt uitgevoerd. Om dit risico te voorkomen, volgt u alle aanbevolen beveiligingsprocedures voor de registratieservice voor netwerkapparaten en voor de computer waarop deze rollenservice wordt uitgevoerd.  

 Als de standaardbeveiligingsmachtigingen niet in uw zakelijke vereisten voorzien, hebt u een andere optie om de beveiligingsmachtigingen voor de certificaatsjablonen te configureren: U kunt toevoegen en lezen en machtigingen voor gebruikers en computers registreren.  

## <a name="adding-read-and-enroll-permissions-for-users-and-computers"></a>De machtigingen Lezen en Registreren toevoegen voor gebruikers en computers  
 Toe te voegen lezen en inschrijven machtigingen voor gebruikers en computers kunnen uitkomen als een afzonderlijke infrastructuur beheerd team uw certificeringsinstantie (certificeringsinstantie) en dat afzonderlijke team wil System Center Configuration Manager om te verifiëren dat gebruikers een geldig Active Directory Domain Services-account hebben voordat deze het profiel voor een certificaat om aan te vragen van een gebruikerscertificaat worden verzonden. Voor deze configuratie moet u een of meer beveiligingsgroepen opgeven die de gebruikers bevatten, en vervolgens aan die groepen de machtigingen Lezen en Registreren verlenen voor de certificaatsjablonen. In dit scenario beheert de beheerder van de certificeringsinstantie de beveiligingscontrole.  

 U kunt op vergelijkbare wijze een of meer beveiligingsgroepen opgeven die computeraccounts bevatten, en aan deze groepen de machtigingen Lezen en Registreren verlenen voor de certificaatsjablonen. Als u een profiel voor een computercertificaat implementeert op een computer die lid is van een domein, moet aan het computeraccount van die computer de machtigingen Lezen en Registreren worden verleend. Deze machtigingen zijn niet vereist als de computer niet een domein memberâ€ "bijvoorbeeld is, als een werkgroepcomputer of een persoonlijk mobiel apparaat.  

 Hoewel voor deze configuratie een extra beveiligingscontrole wordt gebruikt, is het niet raadzaam deze als aanbevolen procedure te gebruiken. De reden is dat de opgegeven gebruikers of eigenaren van de apparaten kunnen certificaten aanvragen onafhankelijk van System Center Configuration Manager en voeding waarden voor het certificaatonderwerp die kunnen worden gebruikt een andere gebruiker of het apparaat te imiteren.  

 Als u bovendien accounts opgeeft die niet kunnen worden geverifieerd op het moment dat de certificaataanvraag plaatsvindt, zal de certificaataanvraag standaard mislukken. Zo mislukt de certificaataanvraag bijvoorbeeld als de server waarop de registratieservice voor netwerkapparaten wordt uitgevoerd, zich in een Active Directory-forest bevindt dat niet wordt vertrouwd door het forest dat de sitesysteemserver van het certificaatregistratiepunt bevat. U kunt het certificaatregistratiepunt zodanig configureren dat het doorgaat als een account niet kan worden geverifieerd omdat er geen reactie is van een domeincontroller. Dit is echter geen aanbevolen beveiligingsprocedure.  

 Als het certificaatregistratiepunt is geconfigureerd om accountmachtigingen te controleren en er een domeincontroller beschikbaar is die de verificatieaanvraag afwijst (bijvoorbeeld als het account is vergrendeld of verwijderd), mislukt de aanvraag voor certificaatregistratie.  

#### <a name="to-check-for-read-and-enroll-permissions-for-users-and-domain-member-computers"></a>De machtigingen Lezen en Registreren controleren voor gebruikers en computers die lid zijn van het domein  

1.  Maak de volgende DWORD-registersleutel als u wilt dat de waarde 0 op de sitesysteemserver die als host fungeert voor het certificaatregistratiepunt: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheck  

2.  Als een account niet kan worden geverifieerd omdat er geen reactie van een domeincontroller is, en u de machtigingscontrole wilt omzeilen:  

    -   Maak de volgende DWORD-registersleutel als u een waarde van 1 op de sitesysteemserver die als host fungeert voor het certificaatregistratiepunt: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheckOnlyIfAccountAccessDenied  

3.  Op de certificeringsinstantie die het certificaat verleent, voegt u op het tabblad **Beveiliging** bij de eigenschappen voor de certificaatsjabloon een of meer beveiligingsgroepen toe om de machtigingen Lezen en Registreren te verlenen aan de gebruiker of het apparaat.  

