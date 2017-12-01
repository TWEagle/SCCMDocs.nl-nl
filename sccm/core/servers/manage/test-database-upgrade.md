---
title: Update van de database testen
titleSuffix: Configuration Manager
description: Test-upgrade de sitedatabase bij de installatie van updates voor Configuration Manager.
ms.custom: na
ms.date: 06/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: abb696f3-a816-4f12-a9f1-0503a81e1976
caps.latest.revision: "0"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 3187b8c7e9b95608092b11807974698f748360eb
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="test-the-database-upgrade-when-installing-an-update"></a>De database-upgrade testen wanneer u een update installeert

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De informatie in dit onderwerp kunt u een testdatabase-upgrade uitvoeren voordat u een update in de console voor de huidige vertakking van Configuration Manager installeert. Evenwel de test-upgrade is niet langer een vereiste of stap het beste tenzij uw database verdacht is of door de aanpassingen niet expliciet ondersteund door Configuration Manager wordt gewijzigd.

## <a name="do-i-need-to-run-a-test-upgrade"></a>Moet ik een testupgrade uitvoeren?
De afschaffing van deze upgrade test wordt mogelijk als gevolg van wijzigingen die zijn geïntroduceerd met System Center Configuration Manager uitgevoerd. Deze wijzigingen vereenvoudigen het proces en de snelheid waarmee een productie-omgeving kan worden bijgewerkt naar nieuwere versies. Dit nieuwe ontwerp is gedaan om te helpen bij klanten die de hoogte blijven met minder risico en minder operationele overhead bij het installeren van elke nieuwe update.

De wijzigingen zijn op hoe updates worden geïnstalleerd, met inbegrip van de logica die automatisch teruggedraaid in een mislukte update zonder de noodzaak om uit te voeren van een site is hersteld. Deze wijzigingen het gebruik van de console voor het beheren van de update-installaties inschakelen en een optie voor het opnemen [installatie van een mislukte update opnieuw uitvoeren](/sccm/core/servers/manage/install-in-console-updates#bkmk_retry).

> [!TIP]
> Wanneer u een naar System Center Configuration Manager van een ouder product, zoals System Center 2012 Configuration Manager upgrade [test database upgrades blijven een aanbevolen stap](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager#a-namebkmktesta-test-the-site-database-upgrade).

Als u nog steeds de upgrade van een sitedatabase testen wilt wanneer u een update in de console, de volgende informatie supplementen installeert de [richtlijnen over het installeren van een update in de console](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).

## <a name="prepare-to-run-a-test-database-upgrade"></a>Bereid de uitvoering van een testdatabase-upgrade  
Voordat u een nieuwe update in uw hiërarchie, zoals 1702 update installeert, kunt u de upgrade van uw sitedatabase testen.

Voor het uitvoeren van de upgrade test, gebruikt u de installatie van Configuration Manager van de bronbestanden van [de CD. Meest recente map](/sccm/core/servers/manage/the-cd.latest-folder) van een site die de versie van Configuration Manager die uitvoert u naar wilt bijwerken. Deze vereiste betekent dat de database-update voor de update naar 1702 testen:
-   U moet ten minste één site met versie 1702 hebben van dat u deze CD kunt ophalen. Meest recente map.
-   Als u een site waarop de vereiste versie niet hebt, Overweeg de installatie van een site in een testomgeving en vervolgens die site bijwerken naar de nieuwe versie. Hiermee maakt u de CD. Meest recente map met de juiste versie van de bronbestanden.

De upgradetest wordt op basis van een back-up van uw sitedatabase die u hebt hersteld naar een ander exemplaar van SQL Server uitgevoerd.  U Setup uitvoeren vanuit de **CD. Meest recente** map met de **testdbupgrade** opdrachtregeloptie om te testen die de kopie van de database hersteld. Nadat de test-upgrade is voltooid, wordt de bijgewerkte database verwijderd. Deze kan niet worden gebruikt door een Configuration Manager-site.

Als een update mislukt installeert, hoeft u niet de site te herstellen. In plaats daarvan kunt u de update-installatie van de console opnieuw proberen.

##  <a name="run-the-test-upgrade"></a>De test-upgrade uitvoeren    
1.  Gebruik Configuration Manager Setup en de bronbestanden van de **CD. Meest recente** map van een site waarop de versie die u wilt bijwerken.  

2.  Kopieer de **CD. Meest recente** map op een locatie op het SQL Server-exemplaar dat u gebruiken wilt voor het uitvoeren van de testupgrade van de database.

3.  Maak een back-up van de sitedatabase die u wilt de upgrade testen. Vervolgens herstelt een kopie van de database naar een exemplaar van SQL Server die niet als voor een Configuration Manager-site host. De SQL Server-exemplaar moet dezelfde versie van SQL Server gebruiken als uw sitedatabase.  

4.  Voer na het herstellen van de databasekopie **Setup** vanaf de CD. Meest recente map waarin de bronbestanden van de versie die u naar wilt bijwerken. Wanneer u Setup wilt uitvoeren, gebruikt u de opdrachtregeloptie **/TESTDBUPGRADE** . Als de SQL Server-exemplaar dat de databasekopie host niet het standaardexemplaar is, de opdrachtregelargumenten opgeven om te identificeren van het exemplaar dat de sitedatabasekopie.   

  Bijvoorbeeld: u hebt een sitedatabase met de naam van de database *sms_abc bij*. U herstelt een kopie van deze sitedatabase naar een ondersteund exemplaar van SQL Server met de exemplaarnaam *DBTest*. Als u wilt een upgrade van deze kopie van de sitedatabase testen, gebruikt u de volgende opdrachtregel: **/ Van Setup.exe/testdbupgrade DBtest\CM_ABC**.  

  U vindt Setup.exe op de volgende locatie op de bronmedia voor System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

5.  Controleren op het exemplaar van SQL Server waarop u de upgrade test, de *ConfigMgrSetup.log* in de hoofdmap van het systeemstation informatie over de voortgang en het slagen.  

     Als de testupgrade mislukt, los eventuele problemen die betrekking hebben op de site-database-upgrade mislukt. Vervolgens maakt u een nieuwe back-up van de sitedatabase en test u de upgrade van de nieuwe kopie van de database.  



## <a name="next-steps"></a>Volgende stappen
Nadat de update van de database testen voltooid is, verwijdert u de bijgewerkte database. Deze kan niet worden gebruikt door een Configuration Manager-site. Vervolgens kunt u terugkeren naar uw site actief en [begint met de installatie van update](/sccm/core/servers/manage/install-in-console-updates).
