---
title: Certificaatprofielen plannen
titleSuffix: Configuration Manager
description: Meer informatie over het plannen van de machtigingen die u nodig hebt voor het configureren van de certificaatsjablonen die gebruikmaakt van System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: eab0e09d-b09e-4c14-ab14-c5f87472522e
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: e5c748297b318e5256f2064811151ae96a55fccd
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="planning-for-certificate-template-permissions-for-certificate-profiles-in-system-center-configuration-manager"></a>Certificaatsjabloonmachtigingen voor certificaat voor certificaatprofielen in System Center Configuration Manager plannen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


De volgende informatie kunt u van plan bent voor het configureren van machtigingen voor de certificaatsjablonen die door System Center Configuration Manager gebruikt wanneer u certificaatprofielen implementeert.  

## <a name="default-security-permissions-and-considerations"></a>Standaardbeveiligingsmachtigingen en overwegingen hiervoor  
 De standaardbeveiligingsmachtigingen die vereist voor de certificaatsjablonen die System Center Configuration Manager gebruiken zijn voor het aanvragen van certificaten voor gebruikers en apparaten zijn als volgt:  

-   Lezen en Registreren voor het account waarvan de toepassingsgroep Registratieservice voor netwerkapparaten gebruik maakt  

-   Lezen voor het account dat de System Center Configuration Manager-console wordt uitgevoerd  

 Zie voor meer informatie over deze beveiligingsmachtigingen [certificaatinfrastructuur configureren](../deploy-use/certificate-infrastructure.md).  

 Wanneer u deze standaardconfiguratie gebruikt, kunnen gebruikers en apparaten niet rechtstreeks certificaten van de certificaatsjablonen aanvragen, en moeten alle aanvragen worden geïnitieerd door de registratieservice voor netwerkapparaten. Dit is een belangrijke beperking, omdat deze certificaatsjablonen moeten worden geconfigureerd met **Met de aanvraag meeleveren** voor het certificaat Onderwerp, wat betekent dat er een risico op imitatie bestaat als een kwaadwillende gebruiker of een apparaat waarmee is geknoeid, een certificaat aanvraagt. In de standaardconfiguratie moet een dergelijke aanvraag worden geïnitieerd door de registratieservice voor netwerkapparaten. Dit risico op imitatie blijft echter bestaan als er wordt geknoeid met de service waarop de registratieservice voor netwerkapparaten wordt uitgevoerd. Om dit risico te voorkomen, volgt u alle aanbevolen beveiligingsprocedures voor de registratieservice voor netwerkapparaten en voor de computer waarop deze rollenservice wordt uitgevoerd.  

 Als de standaardbeveiligingsmachtigingen niet in uw zakelijke vereisten voorzien, hebt u een andere optie om de beveiligingsmachtigingen voor de certificaatsjablonen te configureren: U kunt lezen en registreren toevoegen machtigingen voor gebruikers en computers.  

## <a name="adding-read-and-enroll-permissions-for-users-and-computers"></a>De machtigingen Lezen en Registreren toevoegen voor gebruikers en computers  
 Toevoegen van lees- en registratiemachtigingen voor gebruikers en computers kunnen uitkomen als een afzonderlijk team beheerd door uw team certification authority (CA)-infrastructuur en dat afzonderlijke team wil System Center Configuration Manager om te verifiëren dat gebruikers een geldige Active Directory Domain Services-account hebben voordat ze een certificaatprofiel om aan te vragen van het certificaat van een gebruiker worden verzonden. Voor deze configuratie moet u een of meer beveiligingsgroepen opgeven die de gebruikers bevatten, en vervolgens aan die groepen de machtigingen Lezen en Registreren verlenen voor de certificaatsjablonen. In dit scenario beheert de beheerder van de certificeringsinstantie de beveiligingscontrole.  

 U kunt op vergelijkbare wijze een of meer beveiligingsgroepen opgeven die computeraccounts bevatten, en aan deze groepen de machtigingen Lezen en Registreren verlenen voor de certificaatsjablonen. Als u een profiel voor een computercertificaat implementeert op een computer die lid is van een domein, moet aan het computeraccount van die computer de machtigingen Lezen en Registreren worden verleend. Deze machtigingen zijn niet vereist als de computer niet gelijk is aan een domein memberâ€ 'bijvoorbeeld, als een werkgroepcomputer of een persoonlijk mobiel apparaat.  

 Hoewel voor deze configuratie een extra beveiligingscontrole wordt gebruikt, is het niet raadzaam deze als aanbevolen procedure te gebruiken. De reden is dat de opgegeven gebruikers of eigenaren van de apparaten certificaten onafhankelijk van System Center Configuration Manager en geef waarden voor het certificaatonderwerp die kan worden gebruikt aanvragen kunnen voor een andere gebruiker of het apparaat te imiteren.  

 Als u bovendien accounts opgeeft die niet kunnen worden geverifieerd op het moment dat de certificaataanvraag plaatsvindt, zal de certificaataanvraag standaard mislukken. Zo mislukt de certificaataanvraag bijvoorbeeld als de server waarop de registratieservice voor netwerkapparaten wordt uitgevoerd, zich in een Active Directory-forest bevindt dat niet wordt vertrouwd door het forest dat de sitesysteemserver van het certificaatregistratiepunt bevat. U kunt het certificaatregistratiepunt zodanig configureren dat het doorgaat als een account niet kan worden geverifieerd omdat er geen reactie is van een domeincontroller. Dit is echter geen aanbevolen beveiligingsprocedure.  

 Als het certificaatregistratiepunt is geconfigureerd om accountmachtigingen te controleren en er een domeincontroller beschikbaar is die de verificatieaanvraag afwijst (bijvoorbeeld als het account is vergrendeld of verwijderd), mislukt de aanvraag voor certificaatregistratie.  

#### <a name="to-check-for-read-and-enroll-permissions-for-users-and-domain-member-computers"></a>De machtigingen Lezen en Registreren controleren voor gebruikers en computers die lid zijn van het domein  

1.  Maak de volgende DWORD-registersleutel voor een waarde van 0 op de sitesysteemserver die als host fungeert voor het certificaatregistratiepunt: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheck  

2.  Als een account niet kan worden geverifieerd omdat er geen reactie van een domeincontroller is, en u de machtigingscontrole wilt omzeilen:  

    -   Maak de volgende DWORD-registersleutel voor een waarde van 1 op de sitesysteemserver die als host fungeert voor het certificaatregistratiepunt: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheckOnlyIfAccountAccessDenied  

3.  Op de certificeringsinstantie die het certificaat verleent, voegt u op het tabblad **Beveiliging** bij de eigenschappen voor de certificaatsjabloon een of meer beveiligingsgroepen toe om de machtigingen Lezen en Registreren te verlenen aan de gebruiker of het apparaat.  
