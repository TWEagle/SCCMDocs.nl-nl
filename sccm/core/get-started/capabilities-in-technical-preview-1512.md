---
title: Mogelijkheden van Technical Preview 1512
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1512.
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4d9e414-1346-4ed4-85d0-64d602b68731
caps.latest.revision: "6"
author: erikje
ms.author: erikje
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: e107b24a821ebbd575db9c00a817938d50931344
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1512-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1512 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1512 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.  

 Hier volgen nieuwe functies die u met deze versie kunt uitproberen.  

##  <a name="bkmk_devicehealth"></a> Health Attestation van apparaten  
 Vanaf Technical Preview 1512 kunnen bekijken beheerders de status van Windows 10 Health Attestation van apparaten in de Configuration Manager-console.  Deze functionaliteit is beschikbaar voor Configuration Manager en Configuration Manager met Microsoft Intune. Health attestation van apparaten kan de beheerder zorgen dat clientcomputers over betrouwbare configuraties van BIOS, TPM en opstartsoftware van softwareconfiguraties. Ter ondersteuning van health attestation van apparaten, moeten op clientapparaten Win10 met TPM 2 ingeschakeld worden uitgevoerd. Health attestation van apparaten wordt het aantal apparaten dat is ingeschakeld voor elk van de volgende weergegeven:  

-   Early launch antimalware  

-   BitLocker  

-   Beveiligd opstarten  

-   Code-integriteit  

De console worden ook de bovenste ontbrekende instellingenvoor health attestation met het aantal apparaten weergegeven.  

Om de weergave voor de health attestation van apparaten bekijken, in de Configuration Manager-console gaat u naar de **bewaking** werkruimte van Klik **beveiliging** knooppunt en klik vervolgens op **Health Attestation**.  

##  <a name="bkmk_viewterms"></a>In de console voor voorwaarden bewaken  
Vanaf Technical Preview 1512, wanneer u Configuration Manager met Microsoft Intune integreert, kunt u de Configuration Manager-console om weer te geven welke gebruikers de voorwaarden en bepalingen die zijn geconfigureerd door uw IT-afdeling hebben geaccepteerd en welke gebruikers niet hebben.  

**Samenvattingsinformatie weergeven:**  

-   Ga in de Configuration Manager-console naar **bewaking** > **overzicht** > **implementaties** en selecteer de voorwaarden en bepalingen implementatie die u wilt weergeven.  

**Gedetailleerde gegevens bekijken:**  

1.  Ga in de Configuration Manager-console naar **activa en naleving** > **overzicht** > **instellingen voor naleving** > **voorwaarden en bepalingen**, en selecteer vervolgens de voorwaarden die u wilt weergeven.  

2.  Aan de onderkant van de console, selecteert u de **implementaties** tabblad, selecteert u de implementatie en klik vervolgens op **Status weergeven.**  

##  <a name="bkmk_EPpolicy"></a>Verbeteringen in Endpoint Protection-beleidsinstellingen  
In de 1512 Technical Preview hebben we de volgende nieuwe instellingen in het antimalwarebeleid van Endpoint Protection toegevoegd:  

-   Realtime-beveiliging: **Potentieel ongewenste toepassingen blokkeren tijdens downloaden en voorafgaand aan installatie**  

    -   Potentieel ongewenste toepassingen (PUA’s) is een bedreigingsclassificatie op basis van reputatie en op onderzoek gebaseerde identificatie. Meestal betreft dit partijen die ongewenste toepassingen bundelen of hun gebundelde toepassingen.  

    -   De instelling voor beveiliging is standaard ingeschakeld (ingesteld op "Ja"). Wanneer deze optie is ingeschakeld, worden PUA’s geblokkeerd tijdens downloaden en installeren. U kunt echter specifieke bestanden of mappen om te voldoen aan de specifieke behoeften van uw omgeving uitsluiten.  

-   Scaninstellingen: **Toegewezen netwerkstations scannen bij uitvoeren van een volledige scan**  

    -   Deze instelling biedt meer verfijning voor de beheerder om toe te staan scans op aanvraag van netwerkbestanden zonder het risico altijd worden gescand toegewezen netwerkstations tijdens een geplande volledige scan.  

    -   De instelling **netwerkbestanden scannen** moet eerst worden ingeschakeld ('Ja') voor deze instelling kunt configureren.  

    -   Standaard is deze instelling 'Nee' zin dat een volledige scan geen toegang krijgen toegewezen netwerkstations tot.  

-   Verzending van instellingen voor automatisch voorbeeldbestanden:  

     De antimalware-engine aanvragen dat voorbeeldbestanden voor verdere analyse naar Microsoft worden verzonden. Standaard wordt altijd om bevestiging gevraagd voordat dergelijke voorbeeldbestanden worden verzonden. Beheerders kunnen nu de volgende instellingen beheren om dit gedrag te configureren:  

    -   Geavanceerd: **Schakel automatisch verzenden van voorbeeldbestanden zodat Microsoft kan bepalen of bepaalde gedetecteerde items kwaadaardig zijn**:  Deze instelling op 'Ja' om in te schakelen automatisch verzenden van voorbeeldbestanden wijzigen. Deze instelling is standaard Nee"Dit betekent dat automatisch verzenden van voorbeeldbestanden is uitgeschakeld en wordt gebruikers gevraagd voordat voorbeeldbestanden worden verzonden.   (Deze instelling is geïntroduceerd in System Center 2012 R2 Configuration Manager SP1)  

    -   Geavanceerd: **Toestaan dat gebruikers instellingen automatisch verzenden van voorbeeldbestanden wijzigen**: Deze instelling bepaalt of een gebruiker met lokale beheerdersrechten op een apparaat de automatische instelling verzenden van voorbeeldbestanden in de clientinterface kan wijzigen. Deze instelling is standaard Nee"Dit betekent dat de instellingen kunnen alleen worden gewijzigd in de Configuration Manager-console en lokale beheerders op een apparaat deze configuratie niet wijzigen.  

         Hieronder ziet u bijvoorbeeld de Windows Defender-instelling in Windows 10 door de beheerder ingestelde ingeschakeld en de gebruiker is niet toegestaan om deze te wijzigen:  

         ![TechRef &#95; WinDefender](../../core/get-started/media/TechRef_WinDefender.png "TechRef_WinDefender")  

    Bovendien de bestaande **bestanden en mappen uitsluiten** instellen in de sectie 'Uitsluitingsinstellingen' antimalwarebeleid van endpoint protection verbeterd zodat apparaten kunnen worden uitgesloten. U kunt nu bijvoorbeeld het volgende opgeven als een uitsluiting: **\device\mvfs** (voor Multiversion-bestandssysteem). Het pad naar de; wordt niet gevalideerd door het beleid het endpoint protection-beleid wordt geleverd aan de antimalware-engine op de client moet kunnen interpreteren van de tekenreeks van het apparaat.  

**Vereisten voor het gebruik van Endpoint Protection-beleid:**  

Voordat u Endpoint Protection-beleid kunt gebruiken moet u het installeren en beheren van de Endpoint Protection-client met behulp van de instellingen van de Endpoint Protection-client. Dit wordt gedaan met behulp van de System Center Endpoint Protection-client voor Windows 7, Windows 8, Windows 8.1 of beheerde Windows Defender voor Windows 10. Zie [Endpoint Protection in System Center Configuration Manager](../../protect/deploy-use/endpoint-protection.md).  
