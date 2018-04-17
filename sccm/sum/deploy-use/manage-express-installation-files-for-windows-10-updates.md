---
title: Bestanden voor snelle installatie voor Windows 10-updates beheren
titleSuffix: Configuration Manager
description: Configuration Manager ondersteunt bestanden voor snelle installatie voor Windows 10 waarmee kleinere downloads en sneller installatie op clients.
keywords: ''
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
ms.openlocfilehash: 80ff608ca0e8270fc004995f861a0ccb312a6f34
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="manage-express-installation-files-for-windows-10-updates"></a>Bestanden voor snelle installatie voor Windows 10-updates beheren
Vanaf Configuration Manager versie 1702 kan ondersteunt Configuration Manager voor de bestanden voor snelle installatie voor Windows 10-updates. Wanneer u een ondersteunde versie van Windows 10, kunt u instellingen voor Configuration Manager-client voor het configureren van de client voor het downloaden van alleen de wijzigingen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update. Zonder bestanden voor snelle installatie downloaden van Configuration Manager-clients de volledige 10 cumulatieve Update voor Windows (met inbegrip van alle updates van afgelopen maanden) elke maand. Het gebruik van bestanden voor snelle installatie biedt voor kleinere downloaden en installatie sneller op clients.

> [!IMPORTANT]
> Tijdens de instellingen voor de ondersteuning van het gebruik van bestanden voor snelle installatie is beschikbaar in Configuration Manager versie 1702, het besturingssysteem client-ondersteuning is beschikbaar in Windows 10 versie 1607 met een Windows Update Agent-update. Deze update is opgenomen met de updates die zijn uitgebracht op 11 April 2017 (Patch-dinsdag). Zie voor meer informatie over deze updates [artikel 4015217](http://support.microsoft.com/kb/4015217). Toekomstige updates wordt voor het downloaden van kleinere snelle gebruikmaken van. Windows 10 versie 1607 zonder de update en eerdere versies bieden geen ondersteuning voor bestanden voor snelle installatie.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates"></a>Het downloaden van bestanden voor snelle installatie voor Windows 10-updates inschakelen
Als u wilt synchroniseren van de metagegevens voor Windows 10-bestanden voor snelle installatie, moet u het inschakelen in de eigenschappen van Software-updatepunt.
1.  Navigeer in de Configuration Manager-console naar **beheer** > **siteconfiguratie** > **Sites**.
2.  Selecteer de centrale beheersite of de zelfstandige primaire site.
3.  Klik op het tabblad **Start** in de groep **Instellingen** op **Sitecomponenten configureren**en klik op **Software-updatepunt**. Op de **updatebestanden** tabblad **zowel volledige bestanden downloaden voor alle updates en bestanden voor snelle installatie voor Windows 10 goedgekeurde**.

> [!NOTE]    
> U kunt het onderdeel Software-updatepunt alleen snelle om updates te downloaden niet configureren.  Downloaden van de snelle installatie bestanden worden naast de volledige bestanden en dus wordt vergroot de hoeveelheid inhoud gedistribueerd naar en opgeslagen op uw distributiepunten.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Ondersteuning voor clients kunnen downloaden en installeren van bestanden voor snelle installatie inschakelen
Snelle installatie bestanden als ondersteuning wilt inschakelen op clients, moet u de bestanden voor snelle installatie in de sectie Software-Updates van clientinstellingen inschakelen. Hiermee maakt u een nieuwe HTTP-listener naar aanvragen luistert voor het downloaden van bestanden voor snelle installatie op de poort die u opgeeft.

> [!NOTE]    
> Dit is een lokale poort die clients gebruiken om te luisteren naar aanvragen van levering optimalisatie (Voer) of Background Intelligent Transfer Service (BITS) express om inhoud te downloaden vanaf het distributiepunt. U hoeft niet te openen van deze poort op firewalls, omdat alle verkeer op de lokale computer.

Wanneer u clientinstellingen zodat deze functionaliteit op de client implementeert, wordt geprobeerd de verschillen tussen de huidige maand Windows 10 cumulatieve Update en de vorige maand update downloaden (clients moeten een versie van Windows 10 dat ondersteunt bestanden voor snelle installatie uitvoeren).
1.  Schakel ondersteuning voor bestanden voor snelle installatie in de eigenschappen van onderdeel Software-updatepunt (vorige procedure).
2.  Navigeer in de Configuration Manager-console naar **beheer** > **clientinstellingen**.
3.  Selecteert u de juiste clientinstellingen, klik op de **Start** tabblad **eigenschappen**.
4.  Selecteer de **Software-Updates** pagina, configureert **Ja** voor de **installatie van de Express-Updates op clients inschakelen** instellen en configureren van de poort die wordt gebruikt door de HTTP-listener op de client voor de **poort wordt gebruikt om inhoud te downloaden voor Updates Express** instelling.
