---
title: Hardware-inventarisatie uitbreiden
titleSuffix: Configuration Manager
description: Meer manieren om de hardware-inventarisatie in System Center Configuration Manager uitbreiden.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5bfab4f-c55e-4545-877c-5c8db8bc1891
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: e72d1b866211aeab1aeabe34dfc765ed969cdcb6
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-extend-hardware-inventory-in-system-center-configuration-manager"></a>Hardware-inventarisatie uitbreiden in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hardware-inventaris leest informatie van Windows-pc's met behulp van Windows Management Instrumentation (WMI). WMI is de Microsoft-implementatie van web gebaseerde Enterprise Management (WBEM), een industriestandaard voor het werken met beheerinformatie in een onderneming. In eerdere versies van Configuration Manager, kunt u hardware-inventaris uitgebreid doordat het bestand sms_def.mof op de siteserver. Dit bestand bevatte een lijst met WMI-klassen die konden worden gelezen door de hardware-inventaris. Dit bestand bewerkt, kan u inschakelen en uitschakelen van bestaande klassen en ook nieuwe klassen voor de inventaris maken.  

Het bestand Configuration.mof wordt gebruikt voor het definiëren van de gegevensklassen die moeten worden geïnventariseerd door hardware-inventaris op de client en is ongewijzigd ten opzichte van Configuration Manager 2012. U kunt gegevensklassen maken voor het inventariseren van bestaande of aangepaste gegevensklassen voor WMI-opslagplaatsen of registersleutels aanwezig op clientsystemen.  

 Het bestand Configuration.mof bepaalt en registreert ook de WMI-providers die toegang hebben tot informatie over apparaten tijdens hardware-inventarisatie. Registreren van providers definieert het type provider dat moet worden gebruikt en de klassen die de provider ondersteunt.  

 Wanneer de Configuration Manager-clients beleid aanvragen, wordt het bestand Configuration.mof gekoppeld aan de beleidstekst. Dit bestand wordt vervolgens gedownload en gecompileerd door clients. Wanneer u gegevensklassen uit het bestand Configuration.mof toevoegt, wijzigt of verwijdert, compileren clients automatisch deze wijzigingen die zijn aangebracht in de gegevensklassen gerelateerd aan inventaris. Er is geen verdere actie nodig voor inventarisatie nieuwe of gewijzigde gegevensklassen op Configuration Manager-clients. Dit bestand bevindt zich in **<CMInstallLocation\>\Inboxes\clifiles.src\hinv\\** op primaire siteservers.  

 In Configuration Manager, u niet meer bewerken het bestand sms_def.mof net als bij Configuration Manager 2007. U kunt in plaats daarvan WMI-klassen inschakelen en uitschakelen, en u kunt nieuwe klassen toevoegen voor het verzamelen van hardware-inventaris met clientinstellingen. Configuration Manager biedt de volgende methoden om hardware-inventaris uitbreiden.  

> [!NOTE]  
>  Als u handmatig het bestand Configuration.mof om aangepaste inventarisklassen toevoegen hebt gewijzigd, worden deze wijzigingen overschreven wanneer u naar versie 1602 bijwerkt. Als u wilt blijven aangepaste klassen gebruiken, nadat u hebt bijgewerkt, moet u ze toevoegen aan de sectie 'Toegevoegde extensies' van het bestand Configuration.mof nadat u hebt bijgewerkt naar 1602.  
> Echter, moet u niet wijzigen niets boven dit gedeelte omdat deze secties worden bewerkt door Configuration Manager. U kunt een back-up van uw aangepaste Configuration.mof-bestand vinden in:  
> **<CM Install dir\>\data\hinvarchive\\**.  

|Methode|Meer informatie|  
|------------|----------------------|  
|Bestaande inventarisklassen in- of uitschakelen|Inschakelen of uitschakelen van de standaard-inventarisklassen of aangepaste clientinstellingen maken waarmee u verschillende hardware-inventarisklassen verzamelen van opgegeven verzamelingen clients. Zie de [-of uitschakelen van bestaande inventarisklassen](#BKMK_Enable) procedure in dit artikel.|  
|Een nieuwe inventarisklasse toevoegen|Een nieuwe inventarisklasse toevoegen via de WMI-naamruimte van een ander apparaat. Zie de [een nieuwe inventarisklasse toevoegen](#BKMK_Add) procedure in dit artikel.|  
|Hardware-inventarisklassen importeren en exporteren|Bestanden importeren en exporteren Managed Object Format (MOF) met uit de Configuration Manager-console inventarisklassen. Zie de [hardware-inventarisklassen importeren](#BKMK_Import) en [hardware-inventarisklassen exporteren](#BKMK_Export) procedures in dit artikel.|  
|NOIDMIF-bestanden maken|Gebruik NOIDMIF-bestanden voor het verzamelen van informatie over clientapparaten die niet kunnen worden geïnventariseerd door Configuration Manager. Het is bijvoorbeeld mogelijk dat u informatie wilt verzamelen over het activumnummer van een apparaat, dat alleen als label bestaat op het apparaat. NOIDMIF-inventarisatie is automatisch gekoppeld aan het clientapparaat waarvan deze is verzameld. Zie [voor het maken van NOIDMIF-bestanden](#BKMK_NOIDMIF) in dit artikel.|  
|IDMIF-bestanden maken|Gebruik IDMIF-bestanden voor het verzamelen van informatie over activa in uw organisatie die niet zo zijn gekoppeld aan een Configuration Manager-client, projectors, fotokopieerapparaten en netwerkprinters. Zie [IDMIF-bestanden maken](#BKMK_IDMIF) in dit artikel.|  

## <a name="procedures-to-extend-hardware-inventory"></a>Procedures voor het uitbreiden van hardware-inventaris  
Deze procedures helpen u de standaardclientinstellingen voor hardware-inventaris te configureren en ze zijn van toepassing op alle clients in uw hiërarchie. Als u deze instellingen wilt toepassen op alleen enkele clients, maakt een aangepaste clientapparaatinstelling en wijst u deze toe aan een verzameling van specifieke clients. Zie [het configureren van clientinstellingen in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

###  <a name="BKMK_Enable"></a> Bestaande inventarisklassen in- of uitschakelen  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  Klik in de lijst **Apparaatinstellingen** op **Klassen instellen**.  

7.  In het dialoogvenster **Hardware-inventarisklassen** selecteert of wist u de klassen en klasse-eigenschappen die moeten worden verzameld door hardware-inventarisatie. U kunt klassen uitbreiden om afzonderlijke eigenschappen in een klasse te selecteren of te wissen. Gebruik het veld **Zoeken naar inventarisklassen** om te zoeken naar afzonderlijke klassen.  

    > [!IMPORTANT]  
    >  Wanneer u nieuwe klassen aan de hardware-inventaris van Configuration Manager toevoegt, verhoogd de grootte van het inventarisatiebestand dat wordt verzameld en verzonden naar de siteserver. Dit mogelijk negatieve invloed hebben op de prestaties van uw netwerk en Configuration Manager-site. Schakel de inventarisklassen in die u wilt verzamelen.  


###  <a name="BKMK_Add"></a> Een nieuwe inventarisklasse toevoegen  

U kunt alleen inventarisklassen toevoegen van de hiërarchie van de bovenste niveau server door het wijzigen van de standaardclientinstellingen. Deze optie is niet beschikbaar bij het maken van aangepaste apparaatinstellingen.

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  In de **apparaatinstellingen** Kies **klassen instellen**.  

7.  In de **Hardware-Inventarisklassen** dialoogvenster Kies **toevoegen**.  

8.  Klik in het dialoogvenster **Hardware-inventarisklasse toevoegen** op **Verbinding maken**.  

9. Geef in het dialoogvenster **Verbinding maken met WMI (Windows Management Instrumentation)** de naam op van de computer waarvan u de WMI-klassen en de WMI-naamruimte ophaalt die u wilt gebruiken voor het ophalen van de klassen. Als u alle klassen wilt ophalen onder de WMI-naamruimte die u hebt opgegeven, klikt u op **Recursief**. Als de computer waarmee u verbinding maakt niet de lokale computer is, geeft u aanmeldingsreferenties voor een account op dat toegang heeft tot WMI op de externe computer.  

10. Kies **verbinding**.  

11. In de **Hardware-Inventarisklassen** het dialoogvenster de **Inventarisklassen** , selecteert u de WMI-klassen die u wilt toevoegen aan de hardware-inventaris van Configuration Manager.  

12. Als u bewerken over de geselecteerde WMI-klasse wilt, kiest u **bewerken**, en in de **Klassekwalificaties** dialoogvenster Geef de volgende informatie:  

    -   **Weergavenaam** -deze naam wordt weergegeven in Resource Explorer.  

    -   **Eigenschappen** -Geef de eenheden op waarin elke eigenschap van de WMI-klasse wordt weergegeven.  

     U kunt ook eigenschappen aanwijzen als sleuteleigenschap om elke instantie van de klasse uniek te identificeren. Als er geen sleutel is gedefinieerd voor de klasse en meerdere exemplaren van de klasse worden gerapporteerd door de client, wordt alleen de laatste gevonden instantie in de database opgeslagen.  

     Wanneer u klaar bent met het configureren van de eigenschappen, klikt u op **OK** sluiten de **Klassekwalificaties** in het dialoogvenster en de overige dialoogvensters openen. 

###  <a name="BKMK_Import"></a> Hardware-inventarisklassen importeren  

U kunt alleen inventarisklassen importeren wanneer u de standaardclientinstellingen wijzigt. U kunt echter aangepaste clientinstellingen gebruiken voor het importeren van gegevens die geen schemawijziging, zoals het wijzigen van de eigenschap van een bestaande klasse van **True** naar **False**.  

1.  Kies in de Configuration Manager-console **beheer** >  **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  In de **apparaatinstellingen** Kies **klassen instellen**.  

7.  In de **Hardware-Inventarisklassen** dialoogvenster Kies **importeren**.  

8.  In de **importeren** dialoogvenster, selecteer het Managed Object Format (MOF) bestand dat u wilt importeren, en kies vervolgens **OK**. Controleer de items die moeten worden geïmporteerd en klik vervolgens op **importeren**.  

###  <a name="BKMK_Export"></a> Hardware-inventarisklassen exporteren  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  In de **apparaatinstellingen** Kies **klassen instellen**.  

7.  In de **Hardware-Inventarisklassen** dialoogvenster Kies **exporteren**.  

    > [!NOTE]  
    >  Als u klassen exporteert, worden alle geselecteerde klassen worden geëxporteerd.  

8.  In de **exporteren** dialoogvenster Geef het Managed Object Format (MOF) bestand dat u wilt exporteren van de klassen en kies vervolgens **opslaan**.  

### <a name="bkmk_GreaterThan255"></a> Configureren van hardware-inventaris voor het verzamelen van tekenreeksen die groter is dan 255 tekens
Vanaf Configuration Manager 1802, kunt u de lengte van tekenreeksen moet groter zijn dan 255 tekens voor hardware-inventarisatie-eigenschappen opgeven. Deze wijziging geldt alleen voor toegevoegde klassen en voor hardware-inventarisatie-eigenschappen die niet van sleutels. <!-- 1357389 -->

1. In de **beheer** werkruimte, klik op **clientinstellingen** markeren van een clientapparaat instellen om te bewerken, klik met de rechtermuisknop en selecteer vervolgens **eigenschappen**.

2. Selecteer **Hardware-inventaris**, klikt u vervolgens **klassen instellen**, en **toevoegen**.

3. Klik op de **Connect** knop.

4. Vul **computernaam**, **WMI-naamruimte**, selecteer **recursieve** indien nodig. Geef referenties op om te verbinden. Klik op **Connect** om weer te geven van de naamruimteklassen.

5. Selecteer een nieuwe klasse en klik vervolgens op **bewerken**.

6. Wijzig de **lengte** van de eigenschap die is een tekenreeks, dan de sleutel moet groter zijn dan 255. Klik op **OK**. 

7. Controleer of de eigenschap bewerkte is geselecteerd voor **Hardware-Inventarisklassen** en klik op **OK**. 


## <a name="how-to-use-management-information-files-mif-files-to-extend-hardware-inventory"></a>MIF-bestanden (Management Information Format) gebruiken voor uitbreiding van hardware-inventaris  
 Gebruik Management Information Format (MIF) bestanden voor het uitbreiden van hardware-inventarisatiegegevens die van clients is verzameld door Configuration Manager. Tijdens de hardware-inventaris wordt de in MIF-bestanden opgeslagen informatie toegevoegd aan het clientinventarisrapport en opgeslagen in de sitedatabase, waar u de gegevens op dezelfde manier kunt gebruiken als standaard clientinventarisgegevens. Er zijn twee soorten MIF-bestanden, NOIDMIF en IDMIF.

> [!IMPORTANT]  
>  Voordat u gegevens van MIF-bestanden aan Configuration Manager-database toevoegen kunt, moet u maken of importeren van klassegegevens voor deze. Zie de secties voor meer informatie [een nieuwe inventarisklasse toevoegen](#BKMK_Add) en [hardware-inventarisklassen importeren](#BKMK_Import) in dit artikel.  

###  <a name="BKMK_NOIDMIF"></a> NOIDMIF-bestanden maken  
 NOIDMIF-bestanden kunnen worden gebruikt voor het toevoegen van gegevens aan een clienthardware-inventaris die normaal gesproken kan niet worden verzameld door Configuration Manager en is gekoppeld aan een bepaald clientapparaat. Bijvoorbeeld: veel bedrijven labelen elke computer in de organisatie met een activumnummer en catalogiseren deze getallen vervolgens handmatig. Wanneer u een NOIDMIF-bestand maakt, wordt deze informatie kan worden toegevoegd aan de Configuration Manager-database en worden gebruikt voor query's en rapportage. Zie de Configuration Manager SDK-documentatie voor informatie over het maken van NOIDMIF-bestanden.  

> [!IMPORTANT]  
>  Wanneer u een NOIDMIF-bestand maakt, moet deze worden opgeslagen in een indeling met ANSI-codering. NOIDMIF-bestanden in UTF-8-indeling kunnen niet worden gelezen door Configuration Manager.  

 Nadat u een NOIDMIF-bestand hebt gemaakt, opslaan in de *%Windir%***\CCM\Inventory\Noidmifs** op elke client. Configuration Manager verzamelt gegevens van NODMIF bestanden in deze map tijdens de volgende geplande hardware-inventarisatiefase.  

###  <a name="BKMK_IDMIF"></a> IDMIF-bestanden maken  
 IDMIF-bestanden kunnen worden gebruikt voor het toevoegen van gegevens over activa die normaal gesproken kan niet worden geïnventariseerd door Configuration Manager en is niet gekoppeld aan een bepaald clientapparaat met de Configuration Manager-database. U kunt bijvoorbeeld IDMIFS informatie verzamelen over projectors, DVD-spelers, kopieerapparaten of andere apparatuur die geen Configuration Manager-client. Zie de Configuration Manager SDK-documentatie voor informatie over het maken van IDMIF-bestanden.  

 Nadat u een IDMIF-bestand hebt gemaakt, opslaan in de *%Windir%***\CCM\Inventory\Idmifs** map op clientcomputers. Configuration Manager verzamelt gegevens van dit bestand tijdens de volgende geplande hardware-inventarisatiefase. U moet nieuwe klassen declareren voor gegevens in het bestand door deze toe te voegen of te importeren.  

> [!NOTE]
> MIF-bestanden kunnen grote hoeveelheden gegevens bevatten en de verzameling van deze gegevens kan een negatieve invloed hebben op de prestaties van uw site. MIF-verzameling alleen indien nodig inschakelen en configureren van de optie **aangepast MIF-bestand maximumgrootte (KB)** in de instellingen voor hardware-inventaris. Zie voor meer informatie [inleiding op hardware-inventarisatie in System Center Configuration Manager](introduction-to-hardware-inventory.md).
