---
title: Mogelijkheden in Technical Preview 1512 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1512.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4d9e414-1346-4ed4-85d0-64d602b68731
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 5cf8d54fbaa98a75ac2a875a23a43b1d3e5be0dd
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1512-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1512 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1512 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren. Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.  

 De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="bkmk_devicehealth"></a> Health Attestation van apparaten  
 Technische Preview 1512 vanaf weergeven beheerders de status van Windows 10 apparaat Health Attestation-bewerking in de Configuration Manager-console.  Deze functionaliteit is beschikbaar voor Configuration Manager en Configuration Manager met Microsoft Intune. Apparaat health attestation kan de beheerder ervoor te zorgen dat de client computers hebt betrouwbare BIOS, TPM en softwareconfiguraties worden opgestart. Ter ondersteuning van apparaat health attestation clientapparaten moeten beschikken over Win10 met TPM-2 ingeschakeld. Apparaat health attestation geeft het aantal apparaten is ingeschakeld voor elk van de volgende:  

-   Vroege starten antimalware  

-   BitLocker  

-   Beveiligd opstarten  

-   Code-Integriteitsbeleidsbestand  

De console worden ook de bovenste ontbrekende health attestation-instellingen met het aantal apparaten weergegeven.  

Om het voorbeeld van het apparaat health attestation bekijken, in de Configuration Manager-console gaat u naar de **bewaking** werkruimte van Klik **beveiliging** knooppunt en klik vervolgens op **Health Attestation**.  

##  <a name="bkmk_viewterms"></a>Console bewaking voor voorwaarden  
U kunt beginnen met technische Preview 1512 wanneer u Configuration Manager met Microsoft Intune integreren, de Configuration Manager-console gebruiken om te zien welke gebruikers de voorwaarden en bepalingen die zijn geconfigureerd door uw IT-afdeling hebben geaccepteerd en welke gebruikers niet hebben.  

**Samenvattende informatie weergeven:**  

-   Ga in de Configuration Manager-console naar **bewaking** > **overzicht** > **implementaties** en selecteert u de voorwaarden en bepalingen implementatie die u wilt weergeven.  

**Gedetailleerde gegevens bekijken:**  

1.  Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **compatibiliteitsinstellingen** > **voorwaarden en bepalingen**, en selecteer vervolgens de voorwaarden die u wilt weergeven.  

2.  Aan de onderkant van de console, selecteert u de **implementaties** tabblad, selecteert u de implementatie en klik vervolgens op **Status weergeven.**  

##  <a name="bkmk_EPpolicy"></a>Verbeteringen in de Endpoint Protection-beleidsinstellingen  
In de 1512 Technical Preview hebben we de volgende nieuwe instellingen in het antimalwarebeleid van Endpoint Protection in toegevoegd:  

-   Realtime-beveiliging: **Potentieel ongewenste toepassingen blokkeren tijdens downloaden en voorafgaand aan installatie**  

    -   Potentieel ongewenste toepassingen (PUA’s) is een bedreigingsclassificatie op basis van reputatie en op onderzoek gebaseerde identificatie. Meestal betreft dit partijen die ongewenste toepassingen bundelen of hun gebundelde toepassingen.  

    -   De instelling voor beveiliging is standaard ingeschakeld (ingesteld op "Ja"). Wanneer deze optie is ingeschakeld, worden PUA’s geblokkeerd tijdens downloaden en installeren. U kunt echter uitsluiten specifieke bestanden of mappen om te voldoen aan de specifieke vereisten van uw omgeving.  

-   Instellingen voor scanschema: **Toegewezen netwerkstations scannen bij het uitvoeren van een volledige scan**  

    -   Deze instelling biedt groter granulatie voor de beheerder zodat scans op aanvraag van netwerkbestanden zonder het risico van altijd scannen toegewezen netwerkstations tijdens een geplande volledige scan.  

    -   De instelling **scannen netwerkbestanden** moet eerst worden ingeschakeld ("Ja") voor deze instelling moet beschikbaar zijn om te configureren.  

    -   Standaard is deze instelling 'Nee' een volledige scan hebben geen toegang tot toegewezen netwerkstations betekenis.  

-   Instellingen voor automatisch voorbeeld bestand verzenden:  

     De antimalware-engine kan verzoeken voorbeeldbestanden voor verdere analyse naar Microsoft worden verzonden. Standaard wordt altijd om bevestiging gevraagd voordat dergelijke voorbeeldbestanden worden verzonden. Beheerders kunnen nu de volgende instellingen beheren om dit gedrag te configureren:  

    -   Geavanceerde: **Schakel automatisch verzenden van voorbeeldbestanden kan Microsoft bepalen of bepaalde gedetecteerde items kwaadaardig zijn**:  Deze instelling te wijzigen "Ja" automatisch verzenden van voorbeeldbestanden inschakelen. Deze instelling is standaard "Nee" wat betekent dat automatisch verzenden van voorbeeldbestanden is uitgeschakeld en gebruikers wordt gevraagd voordat het verzenden van voorbeelden.   (Deze instelling is geïntroduceerd in System Center 2012 R2 Configuration Manager SP1)  

    -   Geavanceerde: **Toestaan dat gebruikers automatisch voorbeeld bestand verzenden instellingen wijzigen**: Deze instelling bepaalt of een gebruiker met lokale beheerdersrechten op een apparaat de instelling voor automatisch voorbeeld bestand verzenden in de clientinterface kunt wijzigen. Deze instelling is standaard "Nee" wat betekent dat de instellingen kunnen alleen worden gewijzigd in de Configuration Manager-console en lokale beheerders op een apparaat deze configuratie niet wijzigen.  

         Bijvoorbeeld, ziet het volgende u de Windows Defender-instelling in Windows 10 ingesteld door de beheerder is ingeschakeld en de gebruiker is niet toegestaan om deze te wijzigen:  

         ![TechRef &#95; WinDefender](../../core/get-started/media/TechRef_WinDefender.png "TechRef_WinDefender")  

    Bovendien, de bestaande **bestanden en mappen uitsluiten** stellen in het gedeelte "Uitsluitingsinstellingen" van endpoint protection antimalware beleid is verbeterd zodat apparaat uitsluitingen. U kunt nu bijvoorbeeld het volgende opgeven als een uitsluiting: **\device\mvfs** (voor Multiversion-bestandssysteem). Het pad naar de; wordt niet gevalideerd door het beleid het endpoint protection-beleid wordt toegewezen aan de antimalware-engine op de client die de apparaat-tekenreeks interpreteren.  

**Vereisten voor het gebruik van Endpoint Protection-beleid:**  

U moet voordat u Endpoint Protection-beleid kunt installeren en beheren van de Endpoint Protection-client met behulp van de clientinstellingen voor Endpoint Protection. Dit wordt gedaan met behulp van de System Center Endpoint Protection-client voor Windows 7, Windows 8, Windows 8.1 of beheerde Windows Defender voor Windows 10. Zie [Endpoint Protection in System Center Configuration Manager](../../protect/deploy-use/endpoint-protection.md).  

