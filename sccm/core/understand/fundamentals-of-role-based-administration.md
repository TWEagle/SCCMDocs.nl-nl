---
title: Grondbeginselen van op rollen gebaseerd beheer | Microsoft-documenten
description: Op rollen gebaseerd beheer gebruikt voor het beheren van administratieve toegang tot de Configuration Manager en de objecten die u beheert.
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a2d6c3f-a4e4-4c19-b087-3caada480de9
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: ddf2ad1cae51c1e36df5a6d86822e2b9abe604e2
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-role-based-administration-for-system-center-configuration-manager"></a>De grondbeginselen van op rollen gebaseerd beheer voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager kunt u op rollen gebaseerd beheer de toegang dat nodig is voor het beheren van Configuration Manager beveiligen. Bovendien voor beveiliging van toegang tot de objecten die u, zoals verzamelingen, implementatie en sites beheert. Nadat u de basisbegrippen geïntroduceerd in dit onderwerp, kunt u [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../core/servers/deploy/configure/configure-role-based-administration.md).  

 De op rollen gebaseerd beheermodel definieert centraal en hiërarchie-brede beveiligingtoegangsinstellingen voor alle sites en site-instellingen beheert door het volgende:  

-   *Beveiligingsrollen* zijn toegewezen aan gebruikers met beheerdersrechten om op te geven die gebruikers (of groepen van gebruikers) tot verschillende objecten van Configuration Manager. Bijvoorbeeld: machtiging voor het maken of wijzigen van de clientinstellingen.  

-   *Beveiligingsbereiken* worden gebruikt om te groeperen specifieke exemplaren van objecten waarover een gebruiker met beheerdersrechten te beheren, zoals een toepassing waarmee Microsoft Office 2010 wordt geïnstalleerd.  

-   *Verzamelingen* worden gebruikt om op te geven van groepen van gebruikers- en resources waarmee de gebruiker met beheerdersrechten kan worden beheerd.  

 Met de combinatie van beveiligingsrollen, beveiligingsbereiken en verzamelingen, moet u de administratieve toewijzingen die voldoen aan de behoeften van uw organisatie scheiden. Samen gebruikt bepalen ze het beheerbereik van een gebruiker, is wat die gebruiker kan weergeven en beheren in uw Configuration Manager-implementatie.  

## <a name="benefits-of-role-based-administration"></a>Voordelen van op rollen gebaseerd beheer  

-   Sites worden niet gebruikt als administratieve grenzen.  

-   U creëert gebruikers met beheerdersrechten voor een hiërarchie en alleen moet kent één keer beveiliging toe.  

-   Alle beveiligingstoewijzingen zijn gerepliceerd en beschikbaar in de hiërarchie.  

-   Er zijn ingebouwde beveiligingsrollen die worden gebruikt voor het toewijzen van de typische beheertaken. Maak uw eigen aangepaste beveiligingsrollen ter ondersteuning van uw specifieke bedrijfsvereisten.  

-   Gebruikers met beheerdersrechten zien enkel de objecten waarvoor ze machtigingen voor het beheren van hebben.  

-   U kunt acties administratieve beveiliging controleren.  

Bij het ontwerpen en implementeren van administratieve beveiliging voor Configuration Manager, de volgende maakt u een *beheerbereik* voor een gebruiker met beheerdersrechten:  

-   [Beveiligingsrollen](#bkmk_Planroles)  

-   [Verzamelingen](#bkmk_planCol)  

-   [Beveiligingsbereiken](#bkmk_PlanScope)  


 Het beheerbereik bepaalt de objecten die een gebruiker met beheerdersrechten weergaven in de Configuration Manager-console, en bepaalt de machtigingen die een gebruiker voor die objecten heeft. De configuraties voor rolgebaseerd beheer worden op elke site in de hiërarchie gerepliceerd als globale gegevens, en vervolgens toegepast op alle beheerverbindingen.  

> [!IMPORTANT]  
>  Door vertragingen in de replicatie van de ene site naar de andere is het mogelijk dat een site geen wijzigingen ontvangt voor rolgebaseerd beheer. Zie voor meer informatie over het bewaken van databasereplicatie tussen sites de [gegevensoverdracht tussen sites in System Center Configuration Manager](../../core/servers/manage/data-transfers-between-sites.md) onderwerp.  

##  <a name="bkmk_Planroles"></a> Beveiligingsrollen  
 Gebruik beveiligingsrollen voor het verlenen van beveiligingsmachtigingen aan gebruikers met beheerdersrechten. Beveiligingsrollen zijn groepen van beveiligingsmachtigingen die u toekent aan gebruikers met beheerdersrechten zodat zij hun beheertaken kunnen uitvoeren. Deze beveiligingsmachtigingen bepalen de beheeracties die een gebruiker met beheerdersrechten kan uitvoeren en de machtigingen die voor bepaalde objecttypes worden verleend. Aanbevolen wordt om de beveiligingsrollen toe te kennen waaraan de minste machtigingen zijn verbonden.  

 Configuration Manager heeft diverse ingebouwde beveiligingsrollen ter ondersteuning van typische groepen van beheertaken, en kunt u uw eigen aangepaste beveiligingsrollen ter ondersteuning van uw specifieke bedrijfsvereisten. Voorbeelden van ingebouwde beveiligingsrollen:  

-   *Volledige beheerder* verleent alle machtigingen in Configuration Manager.  

-   *Asset Intelligence-beheerder* verleent machtigingen voor het beheren van de Asset Intelligence-synchronisatiepunt, Asset Intelligence-rapportageklassen, software-inventaris, hardware-inventaris en meetregels.  

-   *Software-updatebeheer* verleent machtigingen voor het definiëren en implementeren van software-updates. Gebruikers met beheerdersrechten die gekoppeld aan deze rol zijn kunnen verzamelingen, software-updategroepen, implementaties en sjablonen maken.  

> [!TIP]  
>  U kunt de lijst met ingebouwde beveiligingsrollen en aangepaste beveiligingsrollen die u hebt gemaakt, inclusief bijbehorende beschrijvingen, in de Configuration Manager-console weergeven. De rollen weergeven in de **beheer** werkruimte Vouw **beveiliging**, en selecteer vervolgens **beveiligingsrollen**.  

 Elke beveiligingsrol heeft specifieke machtigingen voor verschillende objecttypen. Bijvoorbeeld, de *Toepassingsauteur* beveiligingsrol heeft de volgende machtigingen voor toepassingen: Goedkeuren, maken, verwijderen, wijzigen, map wijzigen verplaatsen Object, lezen, rapport en beveiligingsbereik instellen.

 U kunt de machtigingen voor de ingebouwde beveiligingsrollen niet wijzigen, maar u kunt de rol wel kopiëren, wijzigingen aanbrengen en vervolgens deze wijzigingen opslaan als een nieuwe aangepaste beveiligingsrol. U kunt ook beveiligingsrollen importeren die u hebt geëxporteerd uit een andere hiërarchie bijvoorbeeld uit een testnetwerk. Bekijk de beveiligingsrollen en de bijbehorende machtigingen om te bepalen of u de ingebouwde beveiligingsrollen gaat gebruiken of of u moet uw eigen aangepaste beveiligingsrollen maken.  

 ### <a name="to-help-you-plan-for-security-roles"></a>Om te plannen voor beveiligingsrollen  

1.  Identificeer de taken die de gebruikers met beheerdersrechten in Configuration Manager uitvoeren. Deze rollen kunnen betrekking hebben op één of meer groepen van beheertaken, zoals implementatie van toepassingen en pakketten, implementatie van besturingssystemen en instellingen voor naleving, controle, externe bediening van computers, en verzameling van inventarisgegevens.  

2.  Wijs deze administratieve taken toe aan één of meer van de ingebouwde beveiligingsrollen.  

3.  Als een aantal van de gebruikers met beheerdersrechten de taken van meerdere beveiligingsrollen uitvoert, ken de meerdere beveiligingsrollen dan toe aan deze gebruikers met beheerdersrechten in plaats van een nieuwe beveiligingsrol te maken die de taken combineert.  

4.  Als de taken die u hebt geïdentificeerd niet zijn toegewezen aan de ingebouwde beveiligingsrollen, maak dan nieuwe beveiligingsrollen en test ze.  

Zie voor meer informatie over het maken en configureren van beveiligingsrollen voor op rollen gebaseerd beheer [aangepaste beveiligingsrollen maken](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole) en [configureren van beveiligingsrollen](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole) in de [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../core/servers/deploy/configure/configure-role-based-administration.md) onderwerp.  

##  <a name="bkmk_planCol"></a> Verzamelingen  
 Verzamelingen specificeren de gebruiker en computerbronnen die een gebruiker met beheerdersrechten kan bekijken of beheren. Bijvoorbeeld, als een gebruiker met beheerdersrechten toepassingen wil kunnen implementeren of een computer extern wil kunnen bedienen, moet er een beveiligingsrol aan hem zijn toegewezen die hem toegang verleent tot een verzameling die deze bronnen bevat. U kunt verzamelingen van gebruikers of apparaten selecteren.  

 Zie voor meer informatie over verzamelingen, [Inleiding tot verzamelingen in System Center Configuration Manager](../../core/clients/manage/collections/introduction-to-collections.md).  

 Controleer, voordat u rolgebaseerd beheer gaat configureren, of u nieuwe verzamelingen moet maken om een van de volgende redenen:  

-   Functionele organisatie. Bijvoorbeeld: afzonderlijke verzamelingen van servers en werkstations.  

-   Geografische uitlijning. Bijvoorbeeld: afzonderlijke verzamelingen voor Noord-Amerika en Europa.  

-   Beveiligingvereisten en bedrijfsprocessen. Bijvoorbeeld: afzonderlijke verzamelingen voor productie en testcomputers.  

-   Uitlijning per organisatie. Bijvoorbeeld, afzonderlijke verzamelingen voor elk bedrijfsonderdeel.  

Zie voor meer informatie over het configureren van verzamelingen voor Rolgebaseerd beheer [verzamelingen voor het beheren van beveiliging configureren](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl) in de [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../core/servers/deploy/configure/configure-role-based-administration.md) onderwerp.  

##  <a name="bkmk_PlanScope"></a> Beveiligingsbereiken  
 Gebruik beveiligingsrollen om gebruikers met beheerdersrechten toegang te geven tot beveiligbare objecten. Een beveiligingsbereik is een benoemde set van beveiligbare objecten die zijn toegewezen aan gebruikers met beheerdersrechten als groep. Alle beveiligbare objecten moeten aan één of meer beveiligingsbereiken zijn toegewezen. Configuration Manager heeft twee ingebouwde beveiligingsbereiken:  

-   De *alle* ingebouwde beveiligingsbereik verleent toegang tot alle bereiken. U kunt geen objecten toewijzen aan dit beveiligingsbereik.  

-   De *standaard* ingebouwde beveiligingsbereik wordt standaard gebruikt voor alle objecten. Wanneer u Configuration Manager voor het eerst installeert, worden alle objecten aan dit beveiligingsbereik toegewezen.  

Als u de objecten die gebruikers met beheerdersrechten kunnen zien en beheren wilt beperken, moet u uw eigen aangepaste beveiligingsbereiken maken en gebruiken. Beveiligingsbereiken bieden geen ondersteuning aan een hiërarchische structuur en kunnen niet worden genest. Beveiligingsbereiken kunnen één of meer objecttypen bevatten, waaronder de volgende:  

-   Waarschuwingsabonnementen  

-   Toepassingen  

-   Installatiekopieën  

-   Grensgroepen  

-   Configuratie-items  

-   Aangepaste clientinstellingen  

-   Distributiepunten en distributiepuntengroepen  

-   Driverpakketten  

-   Globale voorwaarden  

-   Migratietaken  

-   Installatiekopieën van besturingssysteem  

-   Installatiepakketten besturingssysteem  

-   Pakketten  

-   Query's  

-   Sites  

-   Regels voor softwarelicentiecontrole  

-   Software-updategroepen  

-   Software-updatepakketten  

-   Takenreekspakketten  

-   Windows CE apparaatinstellingsitems en pakketten  

Er zijn ook een aantal objecten die u niet in een beveiligingsbereik kunt opnemen omdat ze alleen door beveiligingsrollen beveiligd zijn. Beheerderstoegang tot deze objecten kan niet beperkt tot een deelverzameling van de beschikbare objecten zijn. Bijvoorbeeld, u heeft een gebruiker met beheerdersrechten die grensgroepen maakt welke gebruikt worden voor een specifieke site. Aangezien het grensobject geen beveiligingsbereiken ondersteunt, kunt u geen beveiligingsbereik aan deze gebruiker toewijzen dat toegang geeft tot alleen de grenzen die gekoppeld kunnen zijn aan die site. Aangezien een grensobject niet gekoppeld kan zijn aan een beveiligingsbereik, heeft die gebruiker, wanneer u een beveiligingsrol die toegang geeft tot grensobjecten toewijst aan een gebruiker, toegang tot elke grens in de hiërarchie.  

Objecten die niet beperkt zijn door beveiligingsbereiken zijn de volgende:  

-   Active Directory-forests  

-   Gebruikers met beheerdersrechten  

-   Waarschuwingen  

-   Antimalware-beleidsregels  

-   Grenzen  

-   Computerkoppelingen  

-   Standaardclientinstellingen  

-   Implementatiesjablonen  

-   Apparaatstuurprogramma 's  

-   Exchange Server-connector  

-   Toewijzingen tussen sites van migratie  

-   Inschrijvingsprofielen voor mobiele apparaten  

-   Beveiligingsrollen  

-   Beveiligingsbereiken  

-   Siteadressen  

-   Sitesysteemrollen  

-   Softwaretitels  

-   Software-updates  

-   Statusberichten  

-   Gebruikersaffiniteiten apparaat  

Maak beveiligingsbereiken wanneer u toegang tot afzonderlijke instanties van objecten wilt beperken. Bijvoorbeeld:  

-   U hebt een groep van gebruikers met beheerdersrechten die productietoepassingen moeten kunnen zien en geen testtoepassingen. Maak één beveiligingsbereik voor productietoepassingen en nog één voor de testtoepassingen.  

-   Gebruikers met verschillende beheerdersrechten hebben verschillende toegangsrechten nodig voor bepaalde instanties van een objecttype. Bijvoorbeeld, een groep gebruikers met beheerdersrechten vereist de machtiging Lezen aan specifieke software-updategroepen en een andere groep gebruikers met beheerdersrechten wijzigen en verwijderen-machtigingen nodig voor andere software-updategroepen. Maak verschillende beveiligingsbereiken voor deze software-updategroepen.  

Zie voor meer informatie over het configureren van beveiligingsbereiken voor Rolgebaseerd beheer de [configureren van beveiligingsbereiken voor een object](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope) in de [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../core/servers/deploy/configure/configure-role-based-administration.md) onderwerp.  

