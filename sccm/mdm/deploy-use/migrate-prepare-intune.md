---
title: Intune voorbereiden voor gebruikersmigratie van de
titleSuffix: Configuration Manager
description: Informatie over het voorbereiden van Intune in Azure voor gebruikersmigratie van hybride MDM
keywords: ''
author: dougeby
manager: dougeby
ms.date: 12/05/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: ''
ms.technology: ''
ms.assetid: db97ae9e-34f4-4e10-a282-cd211f612bb4
ms.openlocfilehash: 8d636f2c46f3fa14fbc76a605d2cf55a2c0375c6
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="prepare-intune-for-user-migration"></a>Intune voorbereiden voor gebruikersmigratie van de 

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*    

Voordat u gebruikers van hybride MDM (Intune geïntegreerd met Configuration Manager) voor zelfstandige versie van Intune migreert, moet u de stappen voor het voorbereiden van Intune uitvoeren. Deze stappen ervoor te zorgen dat de gemigreerde gebruikers en hun apparaten blijven worden beheerd. Wanneer u deze stappen hebt uitgevoerd en start de migratie naar Intune, moet het worden transparant voor uw gebruikers.  

## <a name="fix-issues-found-during-data-collection-and-import"></a>Los problemen gevonden tijdens het verzamelen van gegevens en importeren
Als u door het proces is een fout [Configuration Manager-gegevens importeren in Microsoft Intune](migrate-import-data.md), het hulpprogramma voor gegevensimport Intune bieden u een overzicht van alle objecten die was het niet importeren. Enkele typische problemen die u waarschijnlijk hebt uitgevoerd, en de stappen die u ondernemen kunt om los het probleem in Intune, worden vermeld in de volgende tabel: 

|Probleem  |Oplossen  |
|---------|---------|
|Verzamelingen op basis van direct lidmaatschap of op een complex worden niet automatisch worden gemigreerd.|U moet Azure Active Directory (AAD) groepen maken in Azure ter vervanging van de verzameling die niet zijn geïmporteerd. Vervolgens moet u het object toewijzen aan de groep.|
|Beleidsregels zijn niet importeerbare |U moet het beleid in Intune opnieuw maken.|
|Implementatie voor een object niet geïmporteerd|U moet het object toewijzen aan de groep. De groep moet dezelfde gebruikers uit de verzameling voor de implementatie bevatten.|

## <a name="create-intune-objects"></a>Intune-objecten maken 
Als u door het proces is een fout [Configuration Manager-gegevens importeren in Microsoft Intune](migrate-import-data.md) en problemen opgelost tijdens het importeren, moet u controleren of de geïmporteerde objecten correct zijn geconfigureerd. Bovendien maken eventuele aanvullende objecten (beleid, profielen, apps, enzovoort) in Intune die u nodig hebt in uw organisatie. 

## <a name="assign-intune-licenses-to-migrated-users"></a>Intune-licenties toewijzen aan gemigreerde gebruikers
In Configuration Manager u een verzameling toevoegen aan het Intune-abonnement en de leden van de verzameling zijn de mogelijkheid hun apparaten kunnen inschrijven. Terwijl een Intune-licentie is gereserveerd voor ingeschreven apparaten, zijn deze licenties niet specifiek gekoppeld aan de gebruiker of het apparaat. Bijvoorbeeld, wouldn't u een Intune-licentie vinden in AAD voor een gebruiker met een geregistreerd apparaat. U moet echter een Intune-licentie voor elke gebruiker configureren in de zelfstandige versie van Intune. U moet dit doen voordat u een gebruiker naar de zelfstandige versie van Intune migreert om ervoor te zorgen dat de gebruiker en hun apparaten worden beheerd door Intune die na de wijziging in de MDM-instantie. Zie voor meer informatie [toewijzen Intune-licenties aan uw gebruikersaccounts](https://docs.microsoft.com/intune/licenses-assign). 

## <a name="verify-intune-user-groups"></a>Controleer of de Intune-gebruikersgroepen
Uw gebruikers en groepen zijn waarschijnlijk al in AAD, omdat u directory-synchronisatie is geconfigureerd. Om ervoor te zorgen dat uw gebruikers deel van de juiste gebruikersgroep uitmaken, wordt u aangeraden u wordt aangeraden uw Intune-gebruikersgroepen. U richt de beleidsregels, profielen, apps, enz. aan deze groepen. Zorg ervoor dat de gebruikers die u kunt naar Intune standalone migreren deel uitmaken van de juiste groepen. 

## <a name="configure-role-based-administration-control-rbac"></a>Op rollen gebaseerd beheer toegangsbeheer (RBAC) configureren
Als onderdeel van de migratie alle benodigde RBAC-rollen configureren in Intune en gebruikers aan deze rollen toewijzen. Houd er rekening mee dat er verschillen tussen RBAC in Configuration Manager en Intune, zijn zoals het bereik van resources. Zie voor meer informatie [Rolgebaseerd beheer toegangsbeheer (RBAC) met Intune](https://docs.microsoft.com/intune/role-based-access-control).

## <a name="assign-apps-and-policies-to-aad-groups"></a>Apps en beleidsregels toewijzen aan AAD-groepen
Als u hebben doorlopen de [Import Configuration Manager-gegevens naar Microsoft Intune](migrate-import-data.md) fase van het migratieproces voor het migreren van andere Configuration Manager-objecten aan Intune, veel van de objecten mogelijk al worden toegewezen aan AAD-groepen. Echter, moet u controleren of alle objecten (apps, beleid, profielen, enz.) zijn toegewezen aan de juiste AAD-groepen. Als u objecten correct toewijst, worden de apparaten van gebruikers worden automatisch geconfigureerd nadat de gebruiker wordt gemigreerd en de migratie transparant voor gebruikers moet. Zie de volgende onderwerpen voor meer informatie over het toewijzen van de objecten aan een AAD-groep: 
- [Beleid toe te wijzen](https://docs.microsoft.com/intune/get-started-policies) 
- [Profielen toewijzen](https://docs.microsoft.com/intune/device-profile-assign) 
- [Toewijzen van apps](https://docs.microsoft.com/intune/get-started-apps) 

## <a name="terms-and-conditions-policy"></a>Voorwaarden
Net als andere beleidsregels op tenantniveau worden voorwaarden automatisch gemigreerd naar Intune zodra gemengde autoriteit is ingeschakeld voor uw tenant.  Echter, moet u de voorwaarden en voorwaarden voor een groep met gebruikers nauwkeurig rapporteren over acceptatie voor de gemigreerde gebruikers, en zorg ervoor dat de voorwaarden en bepalingen voor toekomstige bepalingen en voorwaarden updates of het apparaat goed zijn gericht gemigreerd inschrijvingen. Gebruikers geen opnieuw moeten accepteren de voorwaarden en bepalingen tenzij er wijzigingen aangebracht aan het beleid in de Configuration Manager-console zijn. Zie voor meer informatie [bepalingen en voorwaarden toewijzen](https://docs.microsoft.com/intune/terms-and-conditions-create#assign-terms-and-conditions).

## <a name="configure-the-exchange-connector"></a>De Exchange Connector configureren
Als u Exchange en hebt een lokale Exchange-Connector in Configuration Manager, moet u [configureren van de lokale Exchange-Connector in Intune](https://docs.microsoft.com/intune/exchange-connector-install). U kunt ook de informatie in de volgende secties voor hulp bij het migreren naar de Intune Exchange Connector en zodat voorwaardelijke toegang werk correct na de migratie.

### <a name="powershell-scripts-to-help-you-migrate-to-the-intune-exchange-connector"></a>PowerShell-scripts voor het migreren naar de Intune Exchange Connector 
PowerShell-scripts zijn beschikbaar om te helpen bij het voorbereiden voor de overgang van uw Exchange-apparaten van de Configuration Manager Exchange Connector met de Intune Exchange Connector. Deze scripts zijn optioneel, dat het is raadzaam dat u deze om te verwijderen van inactieve apparaten uit Exchange, die voorkomt dat Intune onnodige apparaten detecteren uitvoeren tijdens de uitvoering. De scripts ervoor te zorgen dat apparaten die zijn gedetecteerd via Exchange met apparaten die zijn ingeschreven bij Intune zo soepel mogelijk samenvoegen kunnen die wordt uitgevoerd. Voer deze scripts vóór het instellen van de Intune Exchange Connector. De PowerShell-scripts maken deel uit van de installatie van gegevensimport van Intune waarmee u [Configuration Manager-gegevens importeren in Microsoft Intune](migrate-import-data.md) in het volgende artikel. Voor meer informatie en de scripts downloaden, gaat u naar [Microsoft Intune-gegevensimport](https://github.com/ConfigMgrTools/Intune-Data-Importer) GitHub-pagina.

### <a name="steps-to-ensure-conditional-access-works-properly-after-user-migration"></a>Om ervoor te zorgen van voorwaardelijke toegang werkt goed in na de gebruikersmigratie
Voor voorwaardelijke toegang tot goed werken nadat het migreren van gebruikers, en om ervoor te zorgen dat uw gebruikers toegang hebben tot hun e-mailserver blijven, zorg ervoor dat de volgende voorwaarden wordt voldaan:
- Als de Exchange ActiveSync toegang niveau standaardinstelling (DefaultAccessLevel) is ingesteld op blokkeren of in quarantaine, kunnen apparaten toegang tot e-mail verliezen. 
- Als de Exchange-Connector in Configuration Manager is geïnstalleerd en de **toegangsniveau wanneer een mobiel apparaat niet wordt beheerd door een regel** instelling een waarde heeft van **toegang toestaan**, moet u de [ Lokale Exchange-connector](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access) in Intune voordat u gebruikers migreert. De standaardinstelling voor het niveau van toegang in Intune configureren op de **on-premises Exchange** blade in **geavanceerde Exchange ActiveSync-toegangsinstellingen**. Zie voor meer informatie [Exchange configureren lokale toegang](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access).
- Gebruik dezelfde configuratie voor beide connectors. De laatste connector die u configureert, overschrijft de eerder geschreven door de andere connector ActiveSync organisatie-instellingen. Als u de connectors anders is geconfigureerd, kan dit leiden tot onverwachte voorwaardelijke toegang wijzigingen.
- Gebruikers verwijderen uit de voorwaardelijke toegang in Configuration Manager als doel zodra ze worden gemigreerd naar de zelfstandige versie van Intune.

## <a name="configure-the-microsoft-intune-certificate-connector"></a>De Microsoft Intune-Certificaatconnector configureren
Als u NDES om certificaten te verlenen met behulp van SCEP gebruikt, moet u de Microsoft Intune-Certificaatconnector configureren. De computer die als host fungeert voor de NDES connector in Intune kan niet dezelfde computer die als host fungeert voor de NDES connector in Configuration Manager. Zie voor meer informatie [configureren en beheren van SCEP-certificaten met Intune](https://docs.microsoft.com/en-us/intune/certificates-scep-configure). 

> [!Important]    
> Nadat u de connector configureert, moet u de geïmporteerde SCEP-profielen om te verwijzen naar de URL van de nieuwe server wijzigen.

## <a name="next-step"></a>Volgende stap
Nadat u Intune voor migratie voorbereiden, bent u klaar bent om een reeks testgebruikers naar zelfstandige versie van Intune. Zie voor meer informatie [wijzigen van de MDM-instantie voor specifieke gebruikers (gemengd authority)](migrate-mixed-authority.md).


