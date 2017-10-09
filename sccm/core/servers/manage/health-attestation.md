---
title: Health attestation | Microsoft Docs
description: Meer informatie over de functionaliteit Health Attestation van apparaten die kunnen worden weergegeven in de Configuration Manager-console.
ms.custom: na
ms.date: 10/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91f9de33-b277-4500-acd6-e7d90a2947c9
caps.latest.revision: "17"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 11d58237ea1e88785f6991450b3e898562b23918
ms.sourcegitcommit: a17f5dece340a70cedbec03d19938dab90ae60b1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2017
---
# <a name="health-attestation-for-system-center-configuration-manager"></a>Health Attestation voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheerders kunnen de status van[ Windows 10 Health Attestation](https://technet.microsoft.com/library/mt592023.aspx) van apparaten bekijken in de Configuration Manager-console.  Met Health Attestation van apparaten kan de beheerder ervoor zorgen dat clientcomputers over de volgende betrouwbare configuraties van BIOS, TPM en opstartsoftware beschikken:  

-   Early Launch Antimalware: Early Launch Antimalware (ELAM) beschermt uw computer wanneer deze wordt gestart en voordat de stuurprogramma's van derden worden geïnitialiseerd. [ELAM inschakelen](https://gallery.technet.microsoft.com/How-to-turn-on-Early-84552ec5)  
-   BitLocker: Windows BitLocker-stationsversleuteling is software waarmee u alle gegevens kunt versleutelen die zijn opgeslagen op het Windows-besturingssysteemvolume.  [Het inschakelen van BitLocker](https://gallery.technet.microsoft.com/How-to-turn-on-BitLocker-34294d3d)  
-   Beveiligd opstarten: beveiligd opstarten is een standaard die is ontwikkeld door leden van de pc-industrie om ervoor te zorgen dat uw pc opstart met alleen de software die wordt vertrouwd door de fabrikant van de computer. [Meer informatie over beveiligd opstarten](https://technet.microsoft.com/library/hh824987.aspx)  
-   Code-integriteit: code-integriteit is een functie die de beveiliging van het besturingssysteem verbetert door de integriteit van een stuurprogramma of systeembestand te valideren elke keer wanneer dit in het geheugen wordt geladen. [Meer informatie over code-integriteit](https://technet.microsoft.com/library/dd348642.aspx)  

Deze functionaliteit is beschikbaar voor pc's en on-premises bronnen die worden beheerd door Configuration Manager en mobiele apparaten die met behulp van Microsoft Intune worden beheerd. Beheerders kunnen opgeven of rapportage plaatsvindt via de cloud of on-premises infrastructuur. Een on-premises health attestation van apparaten controleren schakelt-beheerder om te controleren van de client-pc's zonder internettoegang.

## <a name="enable-health-attestation"></a>Statusverklaringen inschakelen

 **Vereisten:**  

-   Clientapparaten met Windows 10 versie 1607 of Windows Server 2016-versie 1607 met [Health Attestation van apparaten ingeschakeld](https://technet.microsoft.com/windows-server-docs/security/device-health-attestation).
-   TPM 1.2 of TPM 2 ingeschakeld apparaten.
-   Wanneer u cloudbeheer, wijst u communicatie tussen de clientagent voor Configuration Manager en het beheer met *has.spserv.microsoft.com* (poort 443) Health Attestation-service (cloud management). Wanneer op locatie, de client moet communiceren met health attestation-functionaliteit apparaatbeheerpunt.

### <a name="how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Health Attestation-servicecommunicatie inschakelen op Configuration Manager-clientcomputers

Gebruik deze procedure apparaat health attestation bewaking voor apparaten die verbinding met het internet maken wilt inschakelen.

1.  Kies in de Configuration Manager-console **Beheer** > **Overzicht** > **Clientinstellingen**.  Kies het tabblad voor **Computeragent** -instellingen.  
2.  Selecteer in het dialoogvenster **Standaardinstellingen** de optie **Computeragent** en schuif vervolgens omlaag naar **Communicatie met de Health Attestation-service inschakelen**  
3.  Stel de optie **Communicatie met de Health Attestation-Service inschakelen** in op **Ja**en klik vervolgens op **OK**.  
4. Gericht zijn op verzamelingen van apparaten die Apparaatstatus rapporteren moeten.

### <a name="how-to-enable-on-premises-health-attestation-service-communication-on-configuration-manager-client-computers"></a>On-premises Health Attestation-servicecommunicatie inschakelen op Configuration Manager-clientcomputers
Gebruik deze procedure apparaat health attestation bewaking voor on-premises apparaten die geen verbinding met het internet maken wilt inschakelen.

Beginnen met Configuration Manager 1702, worden het lokale apparaat health attestation service-URL geconfigureerd op het beheerpunt om clientapparaten zonder toegang tot internet te ondersteunen.

1. Navigeer in de Configuration Manager-console **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.
2. Met de rechtermuisknop op de primaire of secundaire site met het beheerpunt dat ondersteuning voor clients health attestation van lokale apparaten en selecteer **Siteonderdelen configureren** > **beheerpunt**. De **eigenschappen van Beheerpuntonderdeel** pagina wordt geopend.
3. Op de **geavanceerde opties** tabblad **toevoegen** en geef een geldige lokale apparaat health attestation-service-URL. U kunt meerdere URL's toevoegen. Als meerdere lokale URL's zijn opgegeven, kunnen clients de volledige set ontvangen en willekeurig kiezen die wordt gebruikt.
4.  Kies in de Configuration Manager-console **Beheer** > **Overzicht** > **Clientinstellingen**.  Kies het tabblad voor **Computeragent** -instellingen.  
5.  In de **standaardinstellingen** dialoogvenster, **Computeragent** en schuif vervolgens omlaag naar **on-premises gebruiken statusservice Attestaion**, en ingesteld op **Ja**.
6. Gericht zijn op verzamelingen van apparaten die moeten rapporteren Apparaatstatus met de clientagentinstellingen statusverklaringen apparaat inschakelen.

U kunt ook **bewerken** of **verwijderen** apparaat health attestation-service-URL's.

> [!NOTE]
> Als u gebruikt health attestation van apparaten voordat u een upgrade naar wordt Configuration Manager 1702, de lokale URL's opgegeven in de clientagentinstellingen vooraf ingevuld in de beheerpunteigenschappen tijdens de upgrade. Lokale clients blijven gebruikt u de URL die is opgegeven in de clientagentinstellingen totdat ze zijn bijgewerkt. Deze wordt vervolgens overschakelen naar een van de URL die is opgegeven op het beheerpunt.

## <a name="monitor-device-health-attestation"></a>Health attestation van apparaten controleren

1.  Als u de Health Attestation van apparaten wilt weergeven, doet u het volgende: ga in de Configuration Manager-console naar de werkruimte **Bewaking** , klik op het knooppunt **Beveiliging** en klik vervolgens op **Health Attestation**.  
2.  Health Attestation van apparaten wordt weergegeven.  

In Configuration Manager Health Attestation van apparaten wordt het volgende weergegeven:  

-   **Status Health Attestation** : geeft het aantal apparaten weer met een compatibele, niet-compatibele, onjuiste of onbekende status  
-   **Health Attestation-apparaatrapportage** : geeft het aantal apparaten weer waarvan de Health Attestation-status is gerapporteerd  
-   **Niet-compatibele apparaten op clienttype** : geeft het aantal mobiele apparaten en computers weer die niet compatibel zijn  
-   **Instellingen voor bovenste ontbrekende Health Attestation** : geeft het aantal apparaten weer waarvan de Health Attestation-instelling ontbreekt, weergegeven per instelling

Status van de client Health Attestation van apparaten kan worden gebruikt voor het definiëren van regels voor voorwaardelijke toegang in nalevingsbeleid voor apparaten die worden beheerd door Configuration Manager met Microsoft Intune. Zie [Beleidsregels voor naleving beheren in System Center Configuration Manager](/sccm/protect/deploy-use/device-compliance-policies) voor informatie.  
