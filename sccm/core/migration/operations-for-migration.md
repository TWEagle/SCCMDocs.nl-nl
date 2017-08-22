---
title: Migratiebewerkingen | Microsoft Docs
description: Maken en uitvoeren van taken voor het migreren van gegevens en clients voor System Center Configuration Manager.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c28e3492-851a-40fc-ba13-67ebc2d8b41a
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: fb8a292c4fecbe5744e2cd09bc1442fab11046bc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="operations-for-migrating-to-system-center-configuration-manager"></a>Bewerkingen voor de migratie naar System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Migratie in System Center Configuration Manager, kunt u gegevens en clients migreren wanneer u gegevens hebt verzameld van een bronsite in een ondersteunde bronhiërarchie. Gebruik de informatie in de volgende secties voor het maken en migratietaken voor het migreren van gegevens en clients uitvoeren en vervolgens het migratieproces voltooien.  

-   [Migratietaken maken en bewerken](#Create_Edit_migration_Jobs)  

-   [Migratietaken uitvoeren](#Run_Migration_Jobs)  

-   [Een gedeeld distributiepunt bijwerken of opnieuw toewijzen](#BKMK_ProcUpgrdSS)  

-   [Migratieactiviteiten in de werkruimte Migratie bewaken](#Monitor_MIgration)  

-   [Clients migreren](#BKMK_MigrateClients)  

-   [Migratie voltooien](#Complete_Migration)  

##  <a name="Create_Edit_migration_Jobs"></a> Migratietaken maken en bewerken  
 Gebruik de volgende procedures om gegevens migratietaken maakt, de uitsluitingenlijst voor migratie op basis van een verzameling taken bewerken, instellen van gedeelde distributiepunten en planningen voor migratietaken te bewerken.  

> [!NOTE]  
>  De volgende procedure voor het maken van een migratietaak die op basis van verzamelingen gemigreerd geldt alleen voor bronhiërarchieën waarop een ondersteunde versie van Configuration Manager 2007. Het type migratietaak op basis van een verzameling is niet beschikbaar wanneer u vanaf een bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager migreert.  

#### <a name="create-a-migration-job-to-migrate-by-collections"></a>Een migratietaak maken om te migreren met verzamelingen  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **migratietaken**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **migratietaak maken**.  

4.  Op de **algemene** pagina van de wizard migratietaak maken, instellen van de volgende en kies vervolgens **OK**:  

    -   Geef een naam op voor de migratietaak.  

    -   Selecteer **Verzamelingmigratie** in de vervolgkeuzelijst **Type taak**.  

5.  Op de **verzamelingen selecteren** pagina, stel het volgende en kies vervolgens **volgende**:  

    -   Selecteer de verzamelingen die u wilt migreren.  

    -   Als u wilt migreren alleen verzamelingen en niet de objecten die gekoppeld aan deze verzamelingen zijn, schakel het selectievakje **objecten migreren die gekoppeld aan de gespecificeerde verzamelingen zijn**. Als u deze optie uitschakelt, wordt er geen bijbehorende objecten worden gemigreerd in deze taak en kunt u stap 6 en 7 overslaan.  

6.  Op de **objecten selecteren** pagina, schakel het selectievakje alle objecttypen of specifieke beschikbare objecten die u niet wilt migreren. Standaard worden alle gekoppelde objecttypen en beschikbare objecten geselecteerd. Kies **volgende**.  

7.  Op de **Inhoudeigendom** pagina en kies vervolgens het eigendom van de inhoud van elke vermelde bronsite toewijzen aan een site in de doelhiërarchie **volgende**.  

8.  Op de **beveiligingsbereik** pagina, selecteert u een of meer op rollen gebaseerde beheerbeveiligingsbereiken om toe te wijzen aan de objecten gemigreerd in deze migratietaak en klik vervolgens op **volgende**.  

9. Op de **beperkende verzameling** pagina, instellen van een verzameling vanuit de doelhiërarchie om het bereik van elke vermelde verzameling te beperken en kies vervolgens **volgende**. Als er geen verzamelingen worden vermeld, kiest u **volgende**.  

10. Op de **vervanging van Sitecodes** pagina, wijst u een sitecode uit de doelhiërarchie de Configuration Manager 2007-sitecode voor elke vermelde verzameling te vervangen en klik vervolgens op **volgende**. Als er geen verzamelingen worden vermeld, kiest u **volgende**.  

11. Op de **gegevens bekijken** pagina **opslaan in bestand** om op te slaan van de weergegeven informatie voor later kunt bekijken. Wanneer u klaar om door te gaan bent, kies **volgende**.  

12. Op de **instellingen** pagina instellen wanneer de migratietaak wordt uitgevoerd, geef de overige instellingen die u nodig hebt voor deze migratietaak kiezen en kies vervolgens **volgende**.  

13. Bevestig de instellingen en voltooi de wizard.  

#### <a name="create-a-migration-job-to-migrate-by-objects"></a>Een migratietaak voor het migreren van objecten maken  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **migratietaken**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **migratietaak maken**.  

4.  Op de **algemene** pagina van de wizard migratietaak maken, instellen van de volgende en kies vervolgens **volgende**:  

    -   Geef een naam op voor de migratietaak.  

    -   Selecteer **Objectmigratie** in de vervolgkeuzelijst **Type taak**.  

5.  Selecteer op de pagina **Objecten selecteren** de objecttypen die u wilt migreren. Standaard worden alle beschikbare objecten geselecteerd voor elk objecttype dat u selecteert.  

6.  Op de **Inhoudeigendom** pagina en kies vervolgens het eigendom van de inhoud van elke vermelde bronsite toewijzen aan een site in de doelhiërarchie **volgende**. Als er geen bronsites worden vermeld, kiest u **volgende**.  

7.  Op de **beveiligingsbereik** pagina, selecteert u een of meer op rollen gebaseerde beheerbeveiligingsbereiken toewijzen aan de objecten in deze migratietaak en klik vervolgens op **volgende**.  

8.  Op de **gegevens bekijken** pagina **opslaan in bestand** om op te slaan van de weergegeven informatie voor later kunt bekijken. Wanneer u klaar om door te gaan bent, kies **volgende**.  

9. Op de **instellingen** pagina wanneer de migratietaak wordt uitgevoerd en kies desgewenst aanvullende instellingen die u nodig hebt voor deze migratietaak instellen. Kies vervolgens **volgende**.  

10. Bevestig de instellingen en voltooi de wizard.  

#### <a name="create-a-migration-job-to-migrate-changed-objects"></a>Maken van een migratietaak om gewijzigde objecten te migreren  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **migratietaken**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **migratietaak maken**.  

4.  Op de **algemene** pagina van de wizard migratietaak maken, instellen van de volgende en kies vervolgens **volgende**:  

    -   Geef een naam op voor de migratietaak.  

    -   In de **taaktype** vervolgkeuzelijst, selecteer **objecten gewijzigd na migratie**.  

5.  Selecteer op de pagina **Objecten selecteren** de objecttypen die u wilt migreren. Standaard worden alle beschikbare objecten geselecteerd voor elk objecttype dat u selecteert.  

6.  Op de **Inhoudeigendom** pagina en kies vervolgens het eigendom van de inhoud van elke vermelde bronsite toewijzen aan een site in de doelhiërarchie **volgende**. Als er geen bronsites worden vermeld, kiest u **volgende**.  

7.  Op de **beveiligingsbereik** pagina, selecteert u een of meer op rollen gebaseerde beheerbeveiligingsbereiken toewijzen aan de objecten in deze migratietaak en klik vervolgens op **volgende**.  

8.  Op de **gegevens bekijken** pagina **opslaan in bestand** om op te slaan van de weergegeven informatie voor later kunt bekijken. Wanneer u klaar om door te gaan bent, kies **volgende**.  

9. Op de **instellingen** pagina wanneer de migratietaak wordt uitgevoerd en kies desgewenst aanvullende instellingen die u nodig voor deze migratietaak hebt instellen. In tegenstelling tot de andere typen, moet deze migratietaak de eerder gemigreerde objecten in de System Center Configuration Manager-database overschrijven. Kies **volgende**.  

10. Bevestig de instellingen en voltooi de wizard.  

###  <a name="BKMK_Modify_Exclusion_List"></a>De uitsluitingenlijst voor migratie wijzigen  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte, kiest u **migratie** toegang te krijgen tot de uitsluitingslijst. U kunt de uitsluitingenlijst ook openen vanuit het knooppunt **Bronhiërarchie** of **Migratietaken** .  

3.  Op de **Start** tabblad, in de **migratie** groep, kiest u **Uitsluitingenlijst bewerken**.  

4.  In de **Uitsluitingenlijst bewerken** dialoogvenster Selecteer het uitgesloten object dat u wilt verwijderen uit de uitsluitingslijst en kies vervolgens **verwijderen**.  

5.  Kies **OK** de wijzigingen opslaan en de bewerking te voltooien. Om de huidige wijzigingen annuleren en herstellen van de objecten die u hebt verwijderd, kiest u **annuleren**, en kies vervolgens **Nee**. Op deze manier maakt u de verwijdering van de objecten ongedaan en sluit u het dialoogvenster **Uitsluitingenlijst bewerken** .  

#### <a name="share-distribution-points-from-the-source-hierarchy"></a>Distributiepunten uit de bronhiërarchie delen  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, kies **bronhiërarchie**, en selecteer vervolgens de bronsite die u wilt instellen.  

3.  Op de **Start** tabblad, in de **bronsite** groep, kiest u **configureren**.  

4.  Op de **Bronsitereferenties** dialoogvenster, **inschakelen voor de bronsiteserver deling van distributiepunt**, en kies vervolgens **OK**.  

5.  Wanneer de gegevens zijn verzameld, optie **sluiten**.  

#### <a name="change-the-schedule-of-a-migration-job"></a>De planning van een migratietaak wijzigen  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **migratietaken**.  

3.  Kies de migratietaak die u wilt wijzigen. Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

4.  Selecteer in de eigenschappen van de migratietaak is de **instellingen** tabblad, wijzig de uitvoeringstijd voor de migratietaak en kies vervolgens **OK**.  

##  <a name="Run_Migration_Jobs"></a> Migratietaken uitvoeren  
 Gebruik de volgende procedure om een migratietaak uit te voeren die nog niet is gestart.  


1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **migratietaken**.  

3.  Kies de migratietaak die u wilt uitvoeren. Op de **Start** tabblad, in de **migratietaak** groep, kiest u **Start**.  

4.  Kies **Ja** om de migratietaak te starten.  

##  <a name="BKMK_ProcUpgrdSS"></a> Een gedeeld distributiepunt bijwerken of opnieuw toewijzen  
 U kunt een ondersteund distributiepunt dat wordt gedeeld via een Configuration Manager 2007-bronsite bijwerken (of een ondersteund distributiepunt dat wordt gedeeld via een System Center Configuration Manager-bronsite opnieuw toewijzen) aan een distributiepunt in de doelhiërarchie.  

> [!IMPORTANT]  
>  Voordat u een Configuration Manager 2007-vertakkingsdistributiepunt bijwerkt, moet u de Configuration Manager 2007-clientsoftware van de vertakking distributiepuntcomputer verwijderen. Als de Configuration Manager 2007-clientsoftware wordt geïnstalleerd wanneer u probeert bij te werken van het distributiepunt, wordt de upgrade mislukt en wordt inhoud die eerder was geïmplementeerd op het vertakkingsdistributiepunt verwijderd van de computer.  

> [!CAUTION]  
>  Wanneer u een upgrade of een gedeeld distributiepunt opnieuw toewijst, worden de site system rol en de site system distributiepuntcomputer verwijderd uit de bronsite en als een distributiepunt toegevoegd aan de site in de doelhiërarchie die u selecteert.  

#### <a name="upgrade-or-reassign-a-shared-distribution-point"></a>Bijwerken of opnieuw toewijzen van een gedeeld distributiepunt  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **bronhiërarchie**.  

3.  Selecteer de site die het distributiepunt dat u wilt upgraden bezit, kies de **gedeelde distributiepunten** tabblad en selecteer het distributiepunt die u wilt bijwerken of opnieuw toewijzen.  

4.  Op de **distributiepunt** tabblad, in de **distributiepunt** groep, kiest u **toewijzen**.  

5.  Als u een nieuw distributiepunt voor de doelhiërarchie, met de volgende toevoeging installeert, kunt u instellingen opgeven in de wizard opnieuw toewijzen van gedeelde distributiepunt:  

    -   Op de **Inhoudsconversie** controleert u de informatie over de ruimte die nodig zijn om de bestaande inhoud te converteren. Klik op de **Stationsinstellingen** pagina van de wizard, Controleer of het station van de distributiepuntcomputer die u hebt geselecteerd de vereiste hoeveelheid vrije schijfruimte heeft.  

6.  Bevestig de instellingen en voltooi de wizard.  

##  <a name="Monitor_MIgration"></a> Migratieactiviteiten in de werkruimte Migratie bewaken  
 De Configuration Manager-console gebruiken om migraties te bewaken.  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **migratietaken**.  

3.  Kies de migratietaak die u wilt bewaken.  

4.  Bekijk de details over en status van de geselecteerde migratietaak op de tabbladen voor **Samenvatting** en **Objecten in taak**.  

##  <a name="BKMK_MigrateClients"></a> Clients migreren  
 Nadat u gegevens van clients tussen hiërarchieën migreren maar voordat u de migratie hebt voltooid, moet u wilt migreren van clients naar de doelhiërarchie. De migratie van clients tussen hiërarchieën omvat het verwijderen van de Configuration Manager-clientsoftware van computers die zijn toegewezen aan de bronhiërarchie, en vervolgens de Configuration Manager-clientsoftware te installeren vanuit de doelhiërarchie. Wanneer u de client vanuit de doelhiërarchie installeert, wijst u de client ook aan een primaire site in die hiërarchie toe. Voor meer informatie over het migreren van clients, Zie [een strategie voor clientmigratie in System Center Configuration Manager plannen](../../core/migration/planning-a-client-migration-strategy.md).  

##  <a name="Complete_Migration"></a>Migratie voltooien  
 Gebruik deze procedure voor het voltooien van de migratie van de bronhiërarchie.  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **migratie**, en kies vervolgens **bronhiërarchie**.  

3.  Voor een Configuration Manager 2007-bronhiërarchie selecteert u een bronsite op het laagste niveau van de bronhiërarchie. Voor een System Center 2012 Configuration Manager of System Center Configuration Manager-bronhiërarchie selecteert u de beschikbare bronsite.  

4.  Op de **Start** tabblad, in de **opschonen** groep, kiest u **geen gegevens meer verzamelen**.  

5.  Kies **Ja** de actie te bevestigen.  

6.  Herhaal stap 3, 4 en 5 voor een bronhiërarchie Configuration Manager 2007 voordat u met de volgende stap doorgaat. Deze stappen op elke site in de hiërarchie, van de onderkant van de hiërarchie boven doorlopen. Voor een bronhiërarchie System Center 2012 Configuration Manager of System Center Configuration Manager, blijven de volgende stap.  

7.  Op de **Start** tabblad, in de **opschonen** groep, kiest u **migratiegegevens opruimen**.  

8.  Op de **migratiegegevens opruimen** in het dialoogvenster van de **bronhiërarchie** vervolgkeuzelijst, selecteer de sitecode en siteserver van het hoogste niveau van de bronhiërarchie, en kies vervolgens **OK**.  

9. Kies **Ja** voor het voltooien van het migratieproces voor de bronhiërarchie.  
