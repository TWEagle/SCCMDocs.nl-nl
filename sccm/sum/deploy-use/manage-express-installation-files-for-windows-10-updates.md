---
title: Installatiebestanden Express voor Windows 10-updates beheren | Microsoft-documenten
description: Configuration Manager ondersteunt bestanden voor snelle installatie voor Windows 10 waarmee downloads kleiner en sneller installatietijden op clients.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
ms.translationtype: Machine Translation
ms.sourcegitcommit: d7b13f3dea5a3ae413ca6b8150ec24e1632a4d4d
ms.openlocfilehash: fcdcbcde61402b47871d51deba32d23867a78370
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

## <a name="manage-express-installation-files-for-windows-10-updates"></a>De installatiebestanden Express voor Windows 10-updates beheren
Beginnend in Configuration Manager versie 1702, ondersteunt Configuration Manager bestanden voor snelle installatie voor Windows 10-updates. Wanneer u een ondersteunde versie van Windows 10 gebruikt, kunt u Configuration Manager-instellingen worden alleen de wijzigingen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update gedownload. Zonder bestanden voor snelle installatie Configuration Manager de volledige Windows 10 cumulatieve Update (met inbegrip van alle updates van vorige maanden) downloadt elke maand. Gebruik van bestanden voor snelle installatie zorgt voor downloads kleiner en sneller installatietijden op clients.

> [!IMPORTANT]
> Tijdens de instellingen voor de ondersteuning van het gebruik van bestanden voor snelle installatie beschikbaar is in Configuration Manager versie 1702 de client besturingssysteemondersteuning is beschikbaar in Windows 10 versie 1607 met een Windows Update Agent-update. Deze update is opgenomen in de updates zijn uitgebracht op 11 April 2017 (Patch-dinsdag). Zie voor meer informatie over deze updates [artikel 4015217](http://support.microsoft.com/kb/4015217). Toekomstige updates zal gebruikmaken van snelle voor kleinere downloads. Windows 10 1607 zonder de update versie en eerdere versies bieden geen ondersteuning voor bestanden voor snelle installatie.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>Het downloaden van bestanden voor snelle installatie voor Windows 10-updates op de server inschakelen
Om te beginnen met het synchroniseren van de metagegevens voor Windows 10-bestanden voor snelle installatie, moet u ze inschakelen in de eigenschappen van Software-updatepunt.
1.    Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.
2.    Selecteer de centrale beheersite of de zelfstandige primaire site.
3.    Klik op het tabblad **Start** in de groep **Instellingen** op **Sitecomponenten configureren**en klik op **Software-updatepunt**. Op de **updatebestanden** tabblad **volledige bestanden voor alle goedgekeurde updates downloaden en installatiebestanden express voor Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Ondersteuning voor clients downloaden en installeren van de bestanden voor snelle installatie inschakelen
Snelle installatie bestanden als ondersteuning wilt inschakelen op clients, moet u de bestanden voor snelle installatie op clients in de sectie Software-Updates van clientinstellingen inschakelen. Hiermee maakt u een nieuwe HTTP-listener naar aanvragen luistert voor het downloaden van bestanden voor snelle installatie op de poort die u opgeeft. Als u clientinstellingen voor deze functionaliteit op de client implementeert, wordt geprobeerd de verschillen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update downloaden (clients moeten een versie van Windows 10 dat express ondersteunt installatiebestanden uitvoeren).
1.    Ondersteuning voor bestanden voor snelle installatie in de eigenschappen van onderdeel Software-updatepunt (vorige procedure) inschakelen.
2.    Navigeer in de Configuration Manager-console naar **beheer** > **clientinstellingen**.
3.    Selecteer de juiste clientinstellingen vervolgens op de **Start** tabblad **eigenschappen**.
4.    Selecteer de **Software-Updates** pagina, configureert u **Ja** voor de **installatie van de Express-Updates op clients inschakelen** instellen en configureren van de poort die wordt gebruikt door de HTTP-listener op de client voor de **poort wordt gebruikt om inhoud te downloaden voor Updates Express** instelling.

