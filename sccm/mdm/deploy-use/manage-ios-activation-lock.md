---
title: Beheren van iOS Activeringsvergrendeling | Microsoft-documenten
description: IOS Activeringsvergrendeling met System Center Configuration Manager beheren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2745bac-e1b4-4dac-8ac7-32f1c820bc9c
caps.latest.revision: 9
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 88bef04a52f716ae13afc21c25d33dea06a3fc9c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-ios-activation-lock-with-system-center-configuration-manager"></a>iOS-activeringsvergrendeling beheren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


System Center Configuration Manager kan u helpen bij het beheer van de activeringsvergrendeling voor iOS, een onderdeel van de app Zoek mijn iPhone voor apparaten met iOS 7.1 en hoger. Nadat de activeringsvergrendeling is ingeschakeld, moeten de Apple ID en het wachtwoord van de gebruiker worden ingevoerd voordat een van de volgende handelingen kan worden verricht:

- Zoek mijn iPhone uitschakelen
- Het apparaat wissen
- Het apparaat opnieuw activeren

Op apparaten **zonder supervisie** wordt de activeringsvergrendeling automatisch ingeschakeld wanneer de app Zoek mijn iPhone op een apparaat wordt gebruikt.

Op apparaten **met supervisie** moet u de activeringsvergrendeling activeren met behulp van de Configuration Manager-instellingen voor naleving.

> [!TIP]
> Met de supervisiemodus voor iOS-apparaten kunt u het hulpprogramma Apple Configurator gebruiken om de vergrendelingsfunctionaliteit te beperken tot bepaalde bedrijfsdoeleinden. De supervisiemodus wordt doorgaans alleen gebruikt voor apparaten in bedrijfseigendom.

Activeringsvergrendeling helpt iOS-apparaten te beveiligen en verbetert de kans op herstel wanneer de apparaten zoekraken of worden gestolen. Deze mogelijkheid kan voor u als IT-beheerder echter een aantal uitdagingen opleveren. Bijvoorbeeld:

- Een van uw gebruikers stelt activeringsvergrendeling in op een apparaat. De gebruiker verlaat vervolgens het bedrijf en levert het apparaat in. Zonder de Apple-id en het wachtwoord van de gebruiker is het niet mogelijk om het apparaat opnieuw te activeren zelfs als u er alles van verwijdert.
- U hebt een lijst nodig van alle apparaten waarop activeringsvergrendeling is ingeschakeld.
- Tijdens het vervangen van apparaten binnen uw organisatie, wilt u bepaalde apparaten aan een andere afdeling toewijzen. U kunt alleen apparaten toewijzen waarop de activeringsvergrendeling niet is ingeschakeld.


Voor het oplossen van deze problemen heeft Apple in iOS 7.1 de mogelijkheid geïntroduceerd om een bypass van de activeringsvergrendeling uit te voeren. Hiermee kunt u de activeringsvergrendeling van een apparaat onder supervisie verwijderen zonder dat u de Apple-id en het wachtwoord van de gebruiker nodig hebt. 0p apparaten onder supervisie kan een apparaatspecifieke bypass-code voor de activeringsvergrendeling worden gegenereerd, die wordt opgeslagen op de activeringsserver van Apple.

Meer informatie over de activeringsvergrendeling vindt u [hier](https://support.apple.com/HT201365).

## <a name="how-configuration-manager-helps-you-manage-activation-lock"></a>Hoe Configuration Manager u helpt met het beheer van activeringsvergrendeling

Configuration Manager kan u op twee manieren helpen met het beheer van de activeringsvergrendeling:

1. Door activeringsvergrendeling op apparaten met supervisie in te schakelen.
2. Door bypass van activeringsvergrendeling op apparaten met supervisie in te schakelen.

> [!IMPORTANT]
> U kunt bypass van activeringsvergrendeling niet inschakelen op apparaten zonder supervisie.

De zakelijk voordelen hiervan voor apparaten in bedrijfseigendom zijn:



- De gebruiker beschikt over de beveiligingsvoordelen van de app Zoek mijn iPhone
- De gebruiker kan werken en u weet ondertussen zeker dat u het apparaat buiten gebruik kunt stellen of kunt ontgrendelen wanneer het opnieuw moet worden toegewezen.


## <a name="enable-activation-lock-on-supervised-devices"></a>Activeringsvergrendeling op bewaakte apparaten inschakelen

U kunt de instellingen voor naleving van Configuration Manager gebruiken om een configuratie-item van het type **iOS en Mac OS X** te maken en implementeren om de activeringsvergrendeling op apparaten met supervisie in te schakelen:

1. Gebruik de informatie in het onderwerp [Configuratie-items maken voor iOS en Mac OS X-apparaten die worden beheerd zonder de System Center Configuration Manager-client](/sccm/compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client) voor het maken van een configuratie-item van het type **iOS en Mac OS X**.
2. Op de pagina **Systeembeveiliging** van de wizard Configuratie-item maken, stelt u de instelling **Activeringsvergrendeling toestaan (alleen in de modus Supervisie)** in op **Toegestaan**.
3. [Voeg het configuratie-item toe aan een configuratiebasislijn](/sccm/compliance/deploy-use/create-configuration-baselines).
4. [Implementeer deze configuratiebasislijn](/sccm/compliance/deploy-use/deploy-configuration-baselines) naar een verzameling die de iOS-apparaten bevat waarvoor u de activeringsvergrendeling wilt inschakelen.

> [!IMPORTANT]
> Zorg dat u het apparaat fysiek in bezit hebt voordat u deze procedure uitvoert. Als u dit niet doet, wordt de activeringsvergrendeling overgeslagen en heeft iedereen die in het bezit is van het apparaat, er volledige toegang toe, zodat ze Zoek mijn iPhone kunnen uitschakelen, het apparaat kunnen wissen of opnieuw activeren.

U kunt de activeringsvergrendeling alleen overslaan of de code voor het overslaan van de activeringsvergrendeling alleen ophalen op apparaten met supervisie. Als u probeert de activeringsvergrendeling over te slaan op een apparaat zonder supervisie of de code voor het overslaan van de activeringsvergrendeling wilt weergeven, treedt er een fout op.



## <a name="view-the-activation-lock-bypass-code"></a>De Activeringsvergrendeling bypass-code weergeven

1. Klik op **Activa en naleving**op de Configuration Manager-console.
2. Klik op **Apparaten** in de werkruimte **Activa en naleving**.
3. Selecteer een ingeschreven apparaat in de modus Supervisie waarop de activeringsvergrendeling is ingeschakeld.
4. Op het tabblad **Start** in de groep **Apparaat** klikt u op **Acties extern apparaat** > **De code voor het overslaan van de activeringsvergrendeling weergeven**.
5. In het dialoogvenster **Code voor het overslaan van de activeringsvergrendeling** wordt de code voor het overslaan van de activeringsvergrendeling voor het geselecteerde apparaat weergegeven.

## <a name="bypass-activation-lock"></a>Activeringsvergrendeling

1. Klik op **Activa en naleving**op de Configuration Manager-console.
2. Klik op **Apparaten** in de werkruimte **Activa en naleving**.
3. Selecteer een ingeschreven apparaat in de modus Supervisie waarop de activeringsvergrendeling is ingeschakeld.
3. Op het tabblad **Start** in de groep **Apparaat** klikt u op **Acties extern apparaat** > **Activeringsvergrendeling overslaan**.
5. Lees de waarschuwingen in het dialoogvenster en klik op **Ja** wanneer u klaar bent om door te gaan.
6. U kunt de status van de aanvraag tot ontgrendeling zien in:

    - De detectiegegevens voor het apparaat in het dialoogvenster met de eigenschappen van het apparaat.
    - De kolom **Status van het overslaan van de activeringsvergrendeling** kolom in de weergave **Apparaten** (deze kolom wordt standaard verborgen).
    - De sectie **Gegevens over acties extern apparaat** op het tabblad **Samenvatting** van het detailvenster (als er een apparaat is geselecteerd).

