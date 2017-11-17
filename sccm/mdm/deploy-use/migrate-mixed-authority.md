---
title: Wijzigen van de MDM-instantie voor specifieke gebruikers (gemengd MDM-instantie)
titleSuffix: Configuration Manager
description: Informatie over het wijzigen van de MDM-instantie van hybride MDM in zelfstandige versie van Intune voor sommige gebruikers.
keywords: 
author: dougeby
manager: dougeby
ms.date: 09/14/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: 6f0201d7-5714-4ba0-b2bf-d1acd0203e9a
ms.openlocfilehash: 31d1d84c225d041f644669f0d3279e6bcd3f75ba
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2017
---
# <a name="change-the-mdm-authority-for-specific-users-mixed-mdm-authority"></a>Wijzigen van de MDM-instantie voor specifieke gebruikers (gemengd MDM-instantie) 

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*    

U kunt een gemengde MDM-instantie in dezelfde tenant configureren door het selecteren van sommige gebruikers moeten worden beheerd in Intune en andere gebruikers te worden beheerd met hybride MDM (Intune geïntegreerd met Configuration Manager). Dit onderwerp bevat informatie over het verplaatsen van gebruikers naar de zelfstandige versie van Intune start en wordt ervan uitgegaan dat u de volgende stappen hebt voltooid:
- Gebruikt het hulpprogramma voor het importeren van gegevens naar [Configuration Manager-objecten importeren in Intune](migrate-import-data.md) (optioneel).
- [Intune voorbereid voor gebruikersmigratie](migrate-prepare-intune.md) zodat gebruikers en hun apparaten beheerd blijven nadat deze zijn gemigreerd.

> [!Note]    
> Als u besluit dat u wilt een volledige opnieuw instellen van uw tenant, zodat alle beleidsregels, apps en apparaatinschrijvingen wordt worden verwijderd, contact op met ondersteuning voor hulp.

Gemigreerde gebruikers en hun apparaten in Intune worden beheerd en andere apparaten worden nog worden beheerd in Configuration Manager. U begint met een kleine testgroep van gebruikers om te controleren of alles werkt zoals verwacht. Vervolgens wordt u extra groepen gebruikers geleidelijk migreren totdat u klaar bent voor de tenantniveau MDM-instantie van Configuration Manager zelfstandige versie van Intune. 

## <a name="things-to-know-before-you-migrate-users"></a>Zaken die u moet weten voordat u gebruikers migreert
- Tijdens de gefaseerde migratie blijven eventuele bestaande MDM-beleidsregels of toepassingen in Configuration Manager toepassen op hybride MDM-apparaten.
- Gebruikers worden toegevoegd aan een AAD-groep die u als uw migratie-groep aanwijst. Alle apparaten die zijn gekoppeld aan gebruikers in de groep migratie worden in Intune beheerd.
- Als apparaten zijn toegevoegd aan de AAD-groep, worden deze genegeerd tenzij ze een apparaat zonder een gekoppelde gebruiker.
- Gebruikers die niet in een AAD-groep die is gemarkeerd voor migratie automatisch overnemen op tenantniveau MDM-instantie (Configuration Manager).
- Wanneer u een gebruiker naar Intune migreren, wordt de gebruikers en apparaten weergegeven in de Intune in Azure portal na ongeveer 15 minuten.  
- Wanneer u gebruikers zelfstandige versie van Intune migreert, blijven de volgende instellingen van Configuration Manager beheren voor zowel Intune standalone en hybride MDM-apparaten:
    - [Certificaat voor Apple Push Notification service (APNs)](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)
    - [Device Enrollment Program](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)
    - Inschrijvingsprofielen
    - [Volume-aankoopprogramma (VPP) van licenties](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)
    - Bedrijfs-id 's 
    - [Certificaten voor ondertekening van programmacode](/sccm/mdm/deploy-use/enroll-hybrid-windows)
    - [Categorieën voor apparaatstuurprogramma](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections)
    - [Rol van apparaatinschrijvingsmanager](/sccm/mdm/plan-design/device-enrollment-methods)
    - Voorwaarden
    - Windows SLKs
    - Company Portal huisstijl    
      
> [!Important]    
  > Doorgaan met het bewerken van het beleid op tenantniveau is met de Configuration Manager-console. Nadat u [wijzigen van uw MDM-instantie op tenantniveau](change-mdm-authority.md) aan Intune, vervolgens beheert u dit beleid in Intune in Azure. 
- Het is raadzaam dat u alle gebruikersaccounts die zijn toegevoegd als apparaatinschrijvingsmanagers in Configuration Manager niet migreert. Later, wanneer u uw MDM-instantie op tenantniveau in Intune wijzigt, worden deze gebruikersaccounts gemigreerd correct. Als u beheerdersaccount voor apparaatinschrijving gebruiker voordat de wijziging op tenantniveau MDM-instantie migreert, moet u handmatig de gebruiker toevoegen als een beheerfunctie voor apparaatregistratie in Intune in Azure. Echter, apparaten die zijn geregistreerd met behulp van een apparaatinschrijvingsbeheerder kunnen niet worden gemigreerd met succes. U moet contact op met ondersteuning voor het migreren van deze apparaten. Zie voor meer informatie [een apparaatinschrijvingsmanager toevoegt](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll#add-a-device-enrollment-manager).
- Apparaten die zijn geregistreerd met behulp van een apparaatinschrijvingsbeheerder en apparaten waarvoor geen bijbehorende gebruikers worden niet gemigreerd naar de nieuwe MDM-instantie. Voor deze apparaten moet u contact op met ondersteuning om u te helpen met de afzonderlijke apparaten. Geen ondersteuning voor een MDM-instantie reset uitvoeren of deze wordt de gegevens wissen in Intune. U moet [wijzigen van uw MDM-instantie](migrate-change-mdm-authority.md) uit de Configuration Manager-console.

## <a name="migrate-users-to-intune"></a>Gebruikers migreren naar Intune
Als u wilt testen dat uw Intune-configuraties werken zoals verwacht, moet u eerst een klein aantal gebruikers en hun apparaten migreren. Vervolgens, nadat u dingen werkt bevestigt zoals verwacht, kunt u beginnen meer AAD groepen met meer gebruikers en hun apparaten te migreren.

## <a name="migrate-a-test-group-of-users-to-intune-standalone"></a>Een testgroep gebruikers migreren naar Intune standalone
Hybride MDM kunnen inschrijven voor de apparaten voor de gebruikers in de verzameling die is gekoppeld aan het Intune-abonnement Wanneer u een gebruiker uit de verzameling verwijdert, worden de ingeschreven apparaten worden gemigreerd naar de zelfstandige versie van Intune als de gebruiker een toegewezen licentie voor Intune heeft. Als u nog niet is toegewezen licenties aan gebruikers die u wilt migreren, Zie [toewijzen Intune-licenties aan uw gebruikersaccounts](https://docs.microsoft.com/intune/licenses-assign). U kunt verzamelingen van gebruikers in de verzameling voor de Intune-abonnement uitsluiten van uw belangrijkste verzameling voor het migreren van de gebruikers in de uitgesloten verzameling. 

In het volgende voorbeeld bevat de gebruikers hybride verzameling alle leden uit de verzameling alle gebruikers. Dit kan elke gebruiker een apparaat registreren bij hybride MDM Als u wilt migreren gebruikers zelfstandige versie van Intune, die u kunt verzamelingen uitsluiten selecteren en toevoegen van een verzameling met de gebruikers te migreren. Wanneer u klaar bent om meer gebruikers, kunt u extra uitgesloten verzamelingen met deze gebruikers kunt toevoegen. 

![Verzamelingen uitsluiten](../media/migrate-excludecollections.png)

> [!Note] 
> Wanneer u hebt de **alle gebruikers** verzameling voor de Intune-abonnement hebt geselecteerd, u zijn niet toegestaan een regel als u wilt uitsluiten van verzamelingen toevoegen. Maak een nieuwe verzameling op basis van de **alle gebruikers** verzameling, Controleer of de verzameling bevat de gebruikers die u verwacht en bewerk vervolgens de Intune-abonnement voor het gebruik van de nieuwe verzameling. U kunt verzamelingen van gebruikers uitsluiten van de nieuwe verzameling om gebruikers te migreren. 

Maken van een Gebruikersverzameling die de gebruikers voor het migreren van bevatten voor het migreren van een testgroep van gebruikers met Intune, en vervolgens de Gebruikersverzameling uitsluiten van de verzameling gebruikt voor het Intune-abonnement.   

Het volgende diagram biedt een overzicht van de werking van de gebruikersmigratie van de.

 ![Overzicht van gemengde autoriteit](../media/migrate-mixedauthority.svg)

1. Controleer of de gebruiker een licentie voor Intune/EMS. 
2. Een verzameling uitsluiten van de verzameling voor de Intune-abonnement maken. In dit voorbeeld wordt de **alle hybride gebruikers** verzameling bevat een regel om te voorkomen dat gebruikers in de **migratie test** verzameling. **Gebruiker1** lid is van de **migratie test** verzameling en wordt uitgesloten van de **alle hybride gebruikers** verzameling. 
3. **Gebruiker1**van apparaten nu bij Intune worden beheerd in de Azure portal. 
4. Alle andere apparaten blijven worden beheerd vanuit de Configuration Manager-console. 

## <a name="verify-intune-standalone-functionality"></a>Controleer de functionaliteit van Intune standalone
Nadat u een klein aantal gebruikers hebt gemigreerd, moet u controleren dat de apparaten van de gebruiker worden vermeld in Intune. Ga naar de **apparaten** blade en selecteer **alle apparaten**. 

Controleer of uw beleid, profielen, apps, enz. werken zoals verwacht op de apparaten van gebruikers.

## <a name="migrate-additional-users"></a>Extra gebruikers migreren
Nadat u hebt gecontroleerd of de zelfstandige versie van Intune werkt zoals verwacht, kunt u beginnen met het migreren van extra gebruikers. Net zoals u een verzameling met een reeks testgebruikers gemaakt, verzamelingen maken die gebruikers wilt migreren en wilt uitsluiten van deze verzamelingen uit de verzameling die is gekoppeld aan het Intune-abonnement bevatten. Zie voor meer informatie [verzameling die is gekoppeld aan uw Intune-abonnement](#collection-associated-with-your-intune-subscription).

## <a name="next-steps"></a>Volgende stappen
Nadat u hebt gemigreerd van gebruikers en getest Intune-functionaliteit, moet u overwegen of u bent klaar om [wijzigen van de MDM-instantie](migrate-change-mdm-authority.md) van uw Intune-tenant van Configuration Manager met Intune. 