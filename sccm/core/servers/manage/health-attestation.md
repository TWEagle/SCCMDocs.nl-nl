---
title: Status attestation | Microsoft-documenten
description: Meer informatie over de functionaliteit apparaat Health Attestation zichtbaar zijn in de Configuration Manager-console.
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91f9de33-b277-4500-acd6-e7d90a2947c9
caps.latest.revision: 17
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 54b3433a002b8ef29059bab04458138348f95d66
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="health-attestation-for-system-center-configuration-manager"></a>Health Attestation voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beheerders kunnen de status van[ Windows 10 Health Attestation](https://technet.microsoft.com/library/mt592023.aspx) van apparaten bekijken in de Configuration Manager-console.  Met Health Attestation van apparaten kan de beheerder ervoor zorgen dat clientcomputers over de volgende betrouwbare configuraties van BIOS, TPM en opstartsoftware beschikken:  

-   Early Launch Antimalware: Early Launch Antimalware (ELAM) beschermt uw computer wanneer deze wordt gestart en voordat de stuurprogramma's van derden worden geïnitialiseerd. [ELAM inschakelen](https://gallery.technet.microsoft.com/How-to-turn-on-Early-84552ec5)  
-   BitLocker: Windows BitLocker-stationsversleuteling is software waarmee u alle gegevens kunt versleutelen die zijn opgeslagen op het Windows-besturingssysteemvolume.  [Het inschakelen van BitLocker](https://gallery.technet.microsoft.com/How-to-turn-on-BitLocker-34294d3d)  
-   Beveiligd opstarten: beveiligd opstarten is een standaard die is ontwikkeld door leden van de pc-industrie om ervoor te zorgen dat uw pc opstart met alleen de software die wordt vertrouwd door de fabrikant van de computer. [Meer informatie over beveiligd opstarten](https://technet.microsoft.com/library/hh824987.aspx)  
-   Code-integriteit: code-integriteit is een functie die de beveiliging van het besturingssysteem verbetert door de integriteit van een stuurprogramma of systeembestand te valideren elke keer wanneer dit in het geheugen wordt geladen. [Meer informatie over code-integriteit](https://technet.microsoft.com/library/dd348642.aspx)  

Deze functionaliteit is beschikbaar voor pc's en on-premises bronnen die worden beheerd door Configuration Manager en mobiele apparaten die met behulp van Microsoft Intune worden beheerd. Beheerders kunnen opgeven of rapportage plaatsvindt via de cloud of on-premises infrastructuur. Lokale apparaat health verklaring monitoring schakelt-beheerder om te controleren van de client pc's zonder toegang tot het internet.

## <a name="enable-health-attestation"></a>Status Attestation inschakelen

 **Vereisten:**  

-   Clientapparaten met Windows 10 1607 of Windows Server 2016 versie 1607 met [apparaat Health Attestation ingeschakeld](https://technet.microsoft.com/windows-server-docs/security/device-health-attestation)
-    TPM 1.2 of TPM 2 apparaten ingeschakeld
-   Communicatie tussen de clientagent van Configuration Manager en has.spserv.microsoft.com (poort 443) Attestation-Health-service (cloud-beheer) of met de status attestation-functionaliteit apparaatbeheerpunt (lokaal)

### <a name="how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Health Attestation-servicecommunicatie inschakelen op Configuration Manager-clientcomputers

Gebruik deze procedure om in te schakelen apparaat attestation Statuscontrole voor apparaten die verbinding met het internet maken.

1.  Kies in de Configuration Manager-console **Beheer** > **Overzicht** > **Clientinstellingen**.  Kies het tabblad voor **Computeragent** -instellingen.  
2.  Selecteer in het dialoogvenster **Standaardinstellingen** de optie **Computeragent** en schuif vervolgens omlaag naar **Communicatie met de Health Attestation-service inschakelen**  
3.  Stel de optie **Communicatie met de Health Attestation-Service inschakelen** in op **Ja**en klik vervolgens op **OK**.  
4. Gericht zijn op verzamelingen van apparaten die Apparaatstatus moeten rapporteren.

### <a name="how-to-enable-on-premises-health-attestation-service-communication-on-configuration-manager-client-computers"></a>On-premises Health Attestation-servicecommunicatie inschakelen op Configuration Manager-clientcomputers
Gebruik deze procedure om in te schakelen apparaat attestation Statuscontrole voor lokale apparaten die geen verbinding met internet maken.

Beginnen met Configuration Manager 1702, worden lokale apparaat health attestation-URL van de service geconfigureerd op het beheerpunt om clientapparaten zonder toegang tot het internet te ondersteunen.

1. Navigeer in de Configuration Manager-console **beheer** > **overzicht** > **siteconfiguratie** > **Sites**.
2. Met de rechtermuisknop op de primaire of secundaire site met het beheerpunt dat op het lokale apparaat health attestation clients ondersteunen, en selecteer **configureert Siteonderdelen** > **beheerpunt**. De **Onderdelenkenmerken** pagina wordt geopend.
3. Op de **geavanceerde opties** tabblad **toevoegen** en geef een geldige lokale apparaat health attestation-URL. U kunt meerdere URL's toevoegen. Als meerdere lokale URL's zijn opgegeven, clients de volledige set ontvangen en willekeurig kiezen die wordt gebruikt.
4.  Kies in de Configuration Manager-console **Beheer** > **Overzicht** > **Clientinstellingen**.  Kies het tabblad voor **Computeragent** -instellingen.  
5.  In de **standaardinstellingen** in het dialoogvenster Selecteer **Computeragent** en schuif vervolgens omlaag naar **Gebruik lokale statusservice Attestaion**, en stel op **Ja**.
6. Gericht zijn op verzamelingen van apparaten die Apparaatstatus met de instellingen voor clientagent inschakelen apparaat health attestation reporting moeten rapporteren.

U kunt ook **bewerken** of **verwijderen** apparaat health attestation-URL's.

> [!NOTE]
> Als u apparaat health attestation vóór de upgrade naar Configuration Manager 1702, de lokale URL's opgegeven in de instellingen voor clientagent is vooraf in te vullen in de beheerpunteigenschappen tijdens de upgrade. Lokale clients blijft de URL die is opgegeven in de clientagentinstellingen totdat ze zijn bijgewerkt. Ze zullen vervolgens overschakelen naar een van de URL die is opgegeven op het beheerpunt.

## <a name="monitor-device-health-attestation"></a>Apparaat health attestation bewaken

1.  Als u de Health Attestation van apparaten wilt weergeven, doet u het volgende: ga in de Configuration Manager-console naar de werkruimte **Bewaking** , klik op het knooppunt **Beveiliging** en klik vervolgens op **Health Attestation**.  
2.  Health Attestation van apparaten wordt weergegeven.  

In Configuration Manager Health Attestation van apparaten wordt het volgende weergegeven:  

-   **Status Health Attestation** : geeft het aantal apparaten weer met een compatibele, niet-compatibele, onjuiste of onbekende status  
-   **Health Attestation-apparaatrapportage** : geeft het aantal apparaten weer waarvan de Health Attestation-status is gerapporteerd  
-   **Niet-compatibele apparaten op clienttype** : geeft het aantal mobiele apparaten en computers weer die niet compatibel zijn  
-   **Instellingen voor bovenste ontbrekende Health Attestation** : geeft het aantal apparaten weer waarvan de Health Attestation-instelling ontbreekt, weergegeven per instelling

Status van de client Health Attestation-apparaat kan worden gebruikt om regels te definiëren voor voorwaardelijke toegang in nalevingsbeleid voor apparaten die worden beheerd door Configuration Manager met Microsoft Intune. Zie [Beleidsregels voor naleving beheren in System Center Configuration Manager](/sccm/protect/deploy-use/device-compliance-policies) voor informatie.  

