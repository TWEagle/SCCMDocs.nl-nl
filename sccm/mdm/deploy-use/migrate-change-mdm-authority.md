---
title: Wijzigen van uw MDM-instantie aan Intune
titleSuffix: Configuration Manager
description: Informatie over het wijzigen van de MDM-instantie van Configuration Manager (hybride) zelfstandige versie van Intune.
keywords: 
author: dougeby
manager: angrobe
ms.date: 12/05/2017
ms.topic: article
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.assetid: be503ec9-5324-4f7c-bcf5-77204328e99c
ms.openlocfilehash: 8884883c6e4e82cf38d83b9b7843002be3742bf1
ms.sourcegitcommit: 8c6e9355846ff6a73c534c079e3cdae09cf13c45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/06/2017
---
# <a name="change-your-mdm-authority-to-intune-standalone"></a>Wijzigen van uw MDM-instantie zelfstandige versie van Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*    

U kunt een bestaande Microsoft Intune-tenant geconfigureerd via de Configuration Manager-console (hybride MDM) zelfstandige versie van Intune kunt wijzigen. Wijzigen van de MDM-instantie op tenantniveau in Intune is de laatste fase in het proces om [hybride MDM-gebruikers en apparaten migreren naar Intune standalone](migrate-hybridmdm-to-intunesa.md) in de cloudconfiguratie.    

> [!Important]    
> Zie voor informatie over het wijzigen van uw MDM-instantie zonder eerste migratie hybride MDM van gebruikers met Intune [wijzigen van uw MDM-instantie](change-mdm-authority.md).

Dit artikel bevat informatie over het wijzigen van een bestaande Microsoft Intune-tenant geconfigureerd via de Configuration Manager-console (hybride) zelfstandige versie van Intune en wordt ervan uitgegaan dat u de volgende stappen al hebt voltooid:
- Gebruikt de [Intune gegevensimport-hulpprogramma](migrate-import-data.md) Configuration Manager-objecten importeren in Intune. 
- [Intune voorbereid voor gebruikersmigratie](migrate-prepare-intune.md) zodat gebruikers en hun apparaten beheerd blijven nadat deze zijn gemigreerd.
- [De MDM-instantie voor specifieke gebruikers (gemengd MDM-instantie) gewijzigd](migrate-mixed-authority.md) om te beginnen met het beheren van apparaten van gebruikers van de Azure-portal.


## <a name="users-and-devices-that-have-not-been-migrated"></a>Gebruikers en apparaten die niet zijn gemigreerd
U hebt al veel gebruikers wordt gemigreerd en getest Intune-functionaliteit om ervoor te zorgen dingen werkt zoals verwacht. Daarom uw beleid, profielen, apps, etc. zijn geconfigureerd in Intune en u de objecten op apparaten grondig hebt getest. Er mag geen nieuwe configuraties die vereist zijn voor uw beleid op tenantniveau wanneer de wijziging in de MDM-instantie. Controleer echter de volgende informatie over wat ze kunnen verwachten als de wijziging in de MDM-instantie voor gebruikers en apparaten die niet eerder is gemigreerd:    
- Er is waarschijnlijk een overgang tijd (maximaal acht uur) voordat het apparaat wordt ingecheckt en synchroniseert met de service.
- Uw apparaten moeten verbinding maken met de service na de wijziging zodat de instellingen van de nieuwe MDM-instantie (Intune zelfstandig) de bestaande instellingen op het apparaat vervangt.
- Sommige van de algemene instellingen (zoals profielen) uit de vorige MDM-instantie (hybride) blijven op het apparaat gedurende zeven dagen. 
- Apparaten waarvoor geen bijbehorende gebruikers (meestal wanneer u hebt iOS Device Enrollment Program of bulksgewijs inschrijven scenario's) worden niet gemigreerd naar de nieuwe MDM-instantie. Voor deze apparaten moet u contact op met ondersteuning voor hulp naar de nieuwe MDM-instantie.

## <a name="prerequisites"></a>Vereisten
Controleer de volgende informatie om voor te bereiden voor de wijziging van de MDM-instantie:
- U moet Configuration Manager versie 1610 of hoger om de optie voor het wijzigen van de MDM-instantie beschikbaar hebben.
- Zorg ervoor dat alle gebruikers die momenteel worden beheerd door hybride MDM hebben een Intune/EMS-licentie toegewezen voordat de wijziging in de MDM-instantie. Met de licentievoorwaarden, zorgt u ervoor dat de gebruiker en hun apparaten worden beheerd door Intune standalone die na de wijziging in de MDM-instantie. Zie voor meer informatie [toewijzen Intune-licenties aan uw gebruikersaccounts](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).
- Zorg ervoor dat het beheerdersaccount van de gebruiker een Intune/EMS-licentie toegewezen heeft.

## <a name="change-the-mdm-authority-to-intune"></a>Wijzigen van de MDM-instantie aan Intune
Gebruik de volgende procedure om te wijzigen van de MDM-instantie op tenantniveau in Intune.

1.  Ga in de Configuration Manager-console naar **beheer** &gt; **overzicht** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en uw bestaande Intune-abonnement verwijderen.
2.  Selecteer **wijziging MDM-instantie op Microsoft Intune**, en klik vervolgens op **volgende**.

    ![Dialoogvenster voor Microsoft Intune-abonnement verwijderen](media/mdm-change-delete-subscription.png)
3.  Aanmelden bij de Intune-tenant die u oorspronkelijk hebt gebruikt bij het instellen van de MDM-instantie in Configuration Manager.
4.  Klik op **Volgende** en voltooi de wizard.
5.  De MDM-instantie wordt nu opnieuw ingesteld. Het Intune-abonnement is niet meer weergegeven in het knooppunt van de Microsoft Intune-abonnementen van de Configuration Manager-console.
6.  Meld u aan bij de [Intune in de Azure portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) met dezelfde Intune-tenant die u eerder hebt gebruikt.    

  > [!Important]    
  > Gebruik niet de klassieke Intune-beheerconsole. U moet aanmelden bij Intune in de Azure portal.
7.  Bevestig dat de MDM-instantie is gewijzigd in **Microsoft Intune**. 

## <a name="next-steps"></a>Volgende stappen
Nadat de wijziging in de MDM-instantie voltooid is, controleert u de volgende informatie:
- Er mag geen merkbare invloed hebben op eindgebruikers tijdens de wijziging in de MDM-instantie. 
- U beschikt niet over op tenantniveau beleid opnieuw configureren. 
- U kunt op tenantniveau-beleidsregels uit Intune in de Azure portal bewerken na de wijziging in de MDM-instantie.
-  Nadat u de MDM-instantie hebt gewijzigd, moet u de volgende stappen voor het valideren van nieuwe apparaten met succes zijn geregistreerd bij de nieuwe instantie uitvoeren:   
    - Een nieuw apparaat registreren
    - Zorg ervoor dat het nieuw ingeschreven apparaat wordt weergegeven in Intune.
    - Een actie uitgevoerd, zoals vergrendelen op afstand van de beheerconsole voor het apparaat. Als dat lukt, wordt het apparaat wordt beheerd door de nieuwe MDM-instantie.
- Als u problemen met specifieke apparaten hebt, kunt u registratie ongedaan maken en registreren van de apparaten om op te halen ze verbonden met de nieuwe instantie van en worden beheerd zo snel mogelijk.
- Voor gebruikers en apparaten die niet eerder is gemigreerd:
    - Controleer of de apparaten worden nu weergegeven de **apparaten** blade als beheerde apparaten. Deze apparaten moeten inchecken en synchroniseren met de service nadat de wijziging in de MDM-instantie voordat ze worden weergegeven. 
    - Als de Intune-service detecteert dat een tenant MDM-instantie is gewijzigd, verstuurt een melding op alle geregistreerde apparaten in te checken synchroniseren met de service (buiten de geplande periodieke controle-in). Daarom nadat de MDM-instantie voor de tenant is gewijzigd van hybride zelfstandige versie van Intune, alle apparaten die zijn ingeschakeld en online verbinding maken met de service, wordt de nieuwe MDM-instantie en worden beheerd door Intune standalone op. Er is geen gevolgen heeft voor het beheer en beveiliging van deze apparaten.
    - Apparaten die uitgeschakeld of offline zijn tijdens (of kort na) de wijziging in de MDM-instantie verbinding maken met en synchroniseren met de service onder de nieuwe MDM-instantie wanneer ze zijn ingeschakeld en online.  
    - Gebruikers kunnen snel aan de nieuwe MDM-instantie wijzigen door het handmatig starten van een selectievakje in van het apparaat naar de service. Gebruikers kunnen eenvoudig inchecken door via de bedrijfsportal-app en het starten van een apparaatgeschiktheidscontrole is.
    - Er is een tussentijdse periode wanneer een apparaat offline gedurende de wijziging in de MDM-instantie en is als dat het apparaat wordt ingecheckt met de service. Om ervoor te zorgen dat het apparaat beveiligd en in werking tijdens deze periode tussentijdse blijft, blijven de volgende profielen op het apparaat gedurende zeven dagen (of totdat het apparaat verbinding met de nieuwe MDM-instantie maakt en ontvangt van de nieuwe instellingen waarmee de bestaande overschrijven toepassingsgroepen):
        - E-mailprofiel
        - VPN-profiel
        - Certificaat-profiel
        - Wi-Fi-profiel
        - Configuratieprofielen
    - Contact op met ondersteuning om te helpen de MDM-instantie voor apparaten die niet gekoppeld aan een gebruiker zijn wijzigen. 
