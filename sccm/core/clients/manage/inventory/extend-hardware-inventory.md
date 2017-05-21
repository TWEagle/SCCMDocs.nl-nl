---
title: Hardware-inventaris uitbreiden | Microsoft-documenten
description: Meer manieren om uit te breiden hardware-inventaris in System Center Configuration Manager.
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5bfab4f-c55e-4545-877c-5c8db8bc1891
caps.latest.revision: 10
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 10c1d11a5cf06f3587fb6066801c0eab802dcf9a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-extend-hardware-inventory-in-system-center-configuration-manager"></a>Hardware-inventarisatie uitbreiden in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hardware-inventaris leest gegevens uit de Windows-pc's met behulp van Windows Management Instrumentation (WMI). WMI is de Microsoft-implementatie van webtoepassingen Enterprise Management (WBEM), een industriestandaard voor het van beheergegevens in een onderneming te openen. In eerdere versies van Configuration Manager kan u hardware-inventaris uitbreiden door het wijzigen van het bestand sms_def.mof op de siteserver. Dit bestand bevat een lijst van WMI-klassen die door de hardware-inventaris kan worden gelezen. Als u dit bestand had bewerkt, kon u bestaande klassen inschakelen en uitschakelen, en kon u ook nieuwe klassen voor de inventaris maken.  

Het bestand Configuration.mof wordt gebruikt voor het definiëren van de gegevensklassen die moeten worden geïnventariseerd op hardware-inventaris op de client en is ongewijzigd ten opzichte van Configuration Manager 2012. U kunt gegevensklassen maken voor het inventariseren van bestaande of aangepaste gegevensklassen voor WMI-opslagplaatsen of registersleutels aanwezig op clientsystemen.  

 Het bestand Configuration.mof bepaalt en registreert ook de WMI-providers die toegang hebben tot informatie over apparaten tijdens hardware-inventarisatie. Registreren van providers definieert het type provider dat moet worden gebruikt en de klassen die de provider ondersteunt.  

 Wanneer Configuration Manager-clients beleid aanvragen, bijvoorbeeld is tijdens hun standaard pollinginterval voor clientbeleid, de Configuration.mof gekoppeld aan de beleidhoofdtekst van het. Dit bestand wordt vervolgens gedownload en gecompileerd door clients. Wanneer u gegevensklassen uit het bestand Configuration.mof toevoegt, wijzigt of verwijdert, compileren clients automatisch deze wijzigingen die zijn aangebracht in de gegevensklassen gerelateerd aan inventaris. Er is geen verdere actie is noodzakelijk om nieuwe of gewijzigde gegevens inventarisklassen op Configuration Manager-clients. Dit bestand bevindt zich in **<CMInstallLocation\>\Inboxes\clifiles.src\hinv\\** op primaire siteservers.  

 In Configuration Manager, u niet langer bewerken het bestand sms_def.mof net als in Configuration Manager 2007. U kunt in plaats daarvan WMI-klassen inschakelen en uitschakelen, en u kunt nieuwe klassen toevoegen voor het verzamelen van hardware-inventaris met clientinstellingen. Configuration Manager biedt de volgende methoden om de hardware-inventaris uitbreiden.  

> [!NOTE]  
>  Als u het bestand Configuration.mof om toe te voegen aangepaste inventarisklassen handmatig hebt gewijzigd, worden deze wijzigingen overschreven wanneer u naar versie 1602 bijwerkt. Als u wilt blijven aangepaste klassen gebruiken na het bijwerken, moet u deze in de sectie "Toegevoegde extensions" van het bestand Configuration.mof toevoegen na het bijwerken van 1602.  
> Echter, moet u niet wijzigen iets hierboven in deze sectie als deze secties zijn gereserveerd voor de wijziging door Configuration Manager. U kunt een back-up van uw aangepaste Configuration.mof-bestand vinden in:  
> **<CM Install dir\>\data\hinvarchive\\**.  

|Methode|Meer informatie|  
|------------|----------------------|  
|Bestaande inventarisklassen in- of uitschakelen|Inschakelen of uitschakelen van de standaard-inventarisklassen of aangepaste clientinstellingen maken waarmee u voor het verzamelen van verschillende hardware-inventarisklassen van bepaalde verzamelingen van clients. Zie de [-of uitschakelen van bestaande inventarisklassen](#BKMK_Enable) procedure in dit onderwerp.|  
|Een nieuwe inventarisklasse toevoegen|Een nieuwe inventarisklasse van de WMI-naamruimte van een ander apparaat toevoegen. Zie de [toevoegen van een nieuwe inventarisklasse](#BKMK_Add) procedure in dit onderwerp.|  
|Hardware-inventarisklassen importeren en exporteren|Importeren en exporteren van Managed Object Format (MOF)-bestanden met inventarisklasse via de Configuration Manager-console. Zie de [voor het importeren van hardware-inventarisklassen](#BKMK_Import) en [exporteren hardware-inventarisklassen](#BKMK_Export) procedures in dit onderwerp.|  
|NOIDMIF-bestanden maken|NOIDMIF-bestanden gebruiken voor het verzamelen van informatie over clientapparaten die door Configuration Manager kan niet worden geïnventariseerd. Het is bijvoorbeeld mogelijk dat u informatie wilt verzamelen over het activumnummer van een apparaat, dat alleen als label bestaat op het apparaat. NOIDMIF-inventarisatie is automatisch gekoppeld aan het clientapparaat waarvan deze is verzameld. Zie [NOIDMIF-bestanden maken](#BKMK_NOIDMIF) in dit onderwerp.|  
|IDMIF-bestanden maken|IDMIF-bestanden voor het verzamelen van informatie over activa in uw organisatie die zijn gekoppeld aan een Configuration Manager-client, bijvoorbeeld, projectors, fotokopieerapparaten en netwerkprinters gebruiken. Zie [IDMIF-bestanden maken](#BKMK_IDMIF) in dit onderwerp.|  

## <a name="procedures-to-extend-hardware-inventory"></a>Procedures voor het uitbreiden van hardware-inventaris  
Deze procedures helpen u de standaardclientinstellingen voor hardware-inventaris te configureren en ze zijn van toepassing op alle clients in uw hiërarchie. Als u deze instellingen wilt toepassen op alleen bepaalde clients, maak een aangepaste clientapparaatinstelling en wijs deze toe aan een verzameling van specifieke clients. Zie [clientinstellingen configureren in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

###  <a name="BKMK_Enable"></a> Bestaande inventarisklassen in- of uitschakelen  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  Klik in de lijst **Apparaatinstellingen** op **Klassen instellen**.  

7.  In het dialoogvenster **Hardware-inventarisklassen** selecteert of wist u de klassen en klasse-eigenschappen die moeten worden verzameld door hardware-inventarisatie. U kunt klassen uitbreiden om afzonderlijke eigenschappen in een klasse te selecteren of te wissen. Gebruik het veld **Zoeken naar inventarisklassen** om te zoeken naar afzonderlijke klassen.  

    > [!IMPORTANT]  
    >  Wanneer u nieuwe klassen aan de hardware-inventaris van Configuration Manager toevoegen, wordt de grootte van de inventarisatiebestand die worden verzameld en naar de siteserver gezonden verhoogd. Dit kan de prestaties van uw netwerk en Configuration Manager-siteserver negatief beïnvloeden. Schakel de inventarisklassen in die u wilt verzamelen.  


###  <a name="BKMK_Add"></a> Een nieuwe inventarisklasse toevoegen  

U kunt alleen inventarisklassen toevoegen vanaf de server van het hoogste niveau in de hiërarchie en door de standaardclientinstellingen te wijzigen. Deze optie is niet beschikbaar bij het maken van aangepaste apparaatinstellingen.

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  In de **apparaatinstellingen** Kies **klassen instellen**.  

7.  In de **Hardware-Inventarisklassen** dialoogvenster Kies **toevoegen**.  

8.  Klik in het dialoogvenster **Hardware-inventarisklasse toevoegen** op **Verbinding maken**.  

9. Geef in het dialoogvenster **Verbinding maken met WMI (Windows Management Instrumentation)** de naam op van de computer waarvan u de WMI-klassen en de WMI-naamruimte ophaalt die u wilt gebruiken voor het ophalen van de klassen. Als u alle klassen wilt ophalen onder de WMI-naamruimte die u hebt opgegeven, klikt u op **Recursief**. Als de computer waarmee u verbinding maakt niet de lokale computer is, geeft u aanmeldingsreferenties voor een account op dat toegang heeft tot WMI op de externe computer.  

10. Kies **verbinding**.  

11. In de **Hardware-Inventarisklasse toevoegen** het dialoogvenster de **klassen inventariseren** , selecteert u de WMI-klassen die u wilt toevoegen aan de hardware-inventaris van Configuration Manager.  

12. Als u informatie over de geselecteerde WMI-klasse kiest **bewerken**, en in de **klasse kwalificaties** dialoogvenster, de volgende informatie:  

    -   **Weergavenaam** -dit wordt weergegeven in de Resource Explorer.  

    -   **Eigenschappen** -Geef de eenheden waarin elke eigenschap van de WMI klasse worden weergegeven.  

     U kunt ook eigenschappen aanwijzen als sleuteleigenschap om elke instantie van de klasse uniek te identificeren. Als er geen sleutel is gedefinieerd voor de klasse en meerdere exemplaren van de klasse worden gerapporteerd door de client, wordt alleen de laatste gevonden instantie in de database opgeslagen.  

     Wanneer u klaar bent met de eigenschappen te configureren, klikt u op **OK** sluit de **klasse kwalificaties** in het dialoogvenster en de andere dialoogvensters openen. 


###  <a name="BKMK_Import"></a> Hardware-inventarisklassen importeren  

U kunt alleen inventarisklassen importeren wanneer u de standaardclientinstellingen wijzigt. U kunt echter aangepaste clientinstellingen gebruiken voor het importeren van gegevens die geen schemawijziging bevatten, zoals het wijzigen van de eigenschap van een bestaande klasse van **Waar** in **Onwaar**.  

1.  Kies in de Configuration Manager-console **beheer** >  **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  In de **apparaatinstellingen** Kies **klassen instellen**.  

7.  In de **Hardware-Inventarisklassen** dialoogvenster Kies **importeren**.  

8.  In de **importeren** in het dialoogvenster, selecteer het Managed Object Format (MOF) bestand dat u wilt importeren en kies vervolgens **OK**. Controleer de items die worden geïmporteerd en klik vervolgens op **importeren**.  

###  <a name="BKMK_Export"></a> Hardware-inventarisklassen exporteren  

1.  Kies in de Configuration Manager-console **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  In de **Standaardclientinstellingen** dialoogvenster Kies **Hardware-inventaris**.  

6.  In de **apparaatinstellingen** Kies **klassen instellen**.  

7.  In de **Hardware-Inventarisklassen** dialoogvenster Kies **exporteren**.  

    > [!NOTE]  
    >  Als u klassen exporteert, worden alle geselecteerde klassen worden geëxporteerd.  

8.  In de **exporteren** dialoogvenster Geef het Managed Object Format (MOF) bestand dat u wilt exporteren van de klassen en kies vervolgens **opslaan**.  

## <a name="how-to-use-management-information-files-mif-files-to-extend-hardware-inventory"></a>MIF-bestanden (Management Information Format) gebruiken voor uitbreiding van hardware-inventaris  
 Gebruik Management Information Format (MIF)-bestanden uit te breiden hardware-inventaris verzameld van clients door Configuration Manager. Tijdens de hardware-inventaris wordt de in MIF-bestanden opgeslagen informatie toegevoegd aan het clientinventarisrapport en opgeslagen in de sitedatabase, waar u de gegevens op dezelfde manier kunt gebruiken als standaard clientinventarisgegevens. Er zijn twee soorten MIF-bestanden: NOIDMIF en IDMIF.

> [!IMPORTANT]  
>  Voordat u de informatie van MIF-bestanden aan de Configuration Manager-database toevoegen kunt, moet u maken of importeren van klassegegevens voor deze. Zie de secties [Een nieuwe inventarisklasse toevoegen](#BKMK_Add) en [Hardware-inventarisklassen importeren](#BKMK_Import) in dit onderwerp voor meer informatie.  

###  <a name="BKMK_NOIDMIF"></a> NOIDMIF-bestanden maken  
 NOIDMIF-bestanden kan worden gebruikt voor het toevoegen van gegevens aan een client hardware-inventaris die normaal gesproken kan niet worden verzameld door Configuration Manager en is gekoppeld aan een bepaalde client-apparaat. Bijvoorbeeld veel bedrijven labelen van elke computer in de organisatie met een activumnummer en deze handmatig catalogus. Wanneer u een NOIDMIF-bestand maakt, wordt deze informatie kan worden toegevoegd aan de Configuration Manager-database en worden gebruikt voor query's en rapportering. Zie de Configuration Manager SDK-documentatie voor meer informatie over het maken van NOIDMIF-bestanden.  

> [!IMPORTANT]  
>  Bij het maken van een NOIDMIF-bestand moet het worden opgeslagen in een gecodeerde ANSI-indeling. NOIDMIF-bestanden opgeslagen in de UTF-8 gecodeerde indeling kunnen niet worden gelezen door Configuration Manager.  

 Nadat u een NOIDMIF-bestand maken, opslaan in de *% Windir %***\System32\CCM\Inventory\Noidmifs** map op elke client. Configuration Manager verzamelt informatie van de bestanden in deze map NODMIF tijdens de volgende geplande hardware-inventarisatiefase.  

###  <a name="BKMK_IDMIF"></a> IDMIF-bestanden maken  
 IDMIF-bestanden kunnen worden gebruikt met informatie over activa dat kan niet normaal gesproken worden geïnventariseerd door Configuration Manager en is niet gekoppeld aan een bepaalde client-apparaat, met de Configuration Manager-database. U kunt bijvoorbeeld IDMIFS gebruiken voor het verzamelen van informatie over projectors, DVD-spelers, fotokopieerapparaten of andere apparatuur die geen Configuration Manager-client. Zie de Configuration Manager SDK-documentatie voor meer informatie over het maken van IDMIF-bestanden.  

 Nadat u een IDMIF-bestand maken, opslaan in de *% Windir %***\System32\CCM\Inventory\Idmifs** map op clientcomputers. Configuration Manager verzamelt informatie uit dit bestand tijdens de volgende geplande hardware-inventarisatiefase. U moet nieuwe klassen declareren voor gegevens in het bestand door deze toe te voegen of te importeren.  

> [!NOTE]
> MIF-bestanden kunnen grote hoeveelheden gegevens bevatten en de verzameling van deze gegevens kan een negatieve invloed hebben op de prestaties van uw site. MIF-verzameling alleen indien nodig inschakelen en configureren van de optie **aangepast MIF-bestand maximumgrootte (KB)** in de instellingen voor hardware-inventaris. Zie voor meer informatie [Inleiding tot de hardware-inventaris in System Center Configuration Manager](introduction-to-hardware-inventory.md).

