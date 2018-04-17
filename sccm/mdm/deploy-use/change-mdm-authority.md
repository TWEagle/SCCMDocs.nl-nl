---
title: Wijzigen van uw MDM-instantie
titleSuffix: Configuration Manager
description: Informatie over het wijzigen van de MDM-instantie van Configuration Manager (hybride) zelfstandige versie van Intune
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 04/11/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.assetid: cc397ab5-125f-4f17-905b-fab980194f49
ms.openlocfilehash: 88380c0db38b1226734d9e60266beb9c702e5a1c
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="change-your-mdm-authority"></a>Wijzigen van uw MDM-instantie
U kunt uw MDM-instantie wijzigen zonder contact opnemen met Microsoft Support en zonder de registratie ongedaan maken en registreren van uw bestaande beheerde apparaten. Dit artikel bevat de stappen voor het wijzigen van een bestaande Microsoft Intune-tenant geconfigureerd via de Configuration Manager-console (hybride) zelfstandige versie van Intune. Wanneer u de stappen in dit artikel hebt voltooid, apparaten worden beheerd door Microsoft Intune in de [Azure-portal](https://portal.azure.com). 

> [!Note]    
> Als u wilt wijzigen van een bestaande Microsoft Intune-tenant met de MDM-instantie is ingesteld op Intune, Configuration Manager (hybride), Zie [wijzigen van de MDM-instantie](https://docs.microsoft.com/intune-classic/deploy-use/change-mdm-authority).

> [!Important]    
> In dit artikel wordt uw MDM-instantie wordt gewijzigd wanneer u gebruikers niet eerder hebt gemigreerd. Uw MDM-instantie wijzigen nadat u hebt [gemigreerd van een subset van gebruikers](migrate-hybridmdm-to-intunesa.md), Zie [wijzigen van uw MDM-instantie](migrate-change-mdm-authority.md).

## <a name="key-considerations"></a>Belangrijke aandachtspunten
Nadat u de MDM-instantie hebt gewijzigd, verwacht een overgangsduur van acht uur. Het kan dit lang duren voordat het apparaat wordt ingecheckt en met de service synchroniseert. Om ervoor te zorgen blijven ingeschreven apparaten worden beheerd en beveiligd wanneer de wijziging, instellingen rechtstreeks in Intune te configureren. Houd rekening met de volgende overwegingen:
- Apparaten moeten verbinding maken met de service na de wijziging zodat de instellingen van de nieuwe MDM-instantie (Intune zelfstandig) de bestaande instellingen op het apparaat vervangt.
- Nadat u de MDM-instantie hebt gewijzigd, blijven sommige van de algemene instellingen (zoals profielen) uit de vorige MDM-instantie (hybride) op het apparaat gedurende zeven dagen. Het verdient aanbeveling dat u apps en instellingen (beleid, profielen, apps, enzovoort) in de nieuwe MDM-instantie zo snel mogelijk configureren. Bovendien moet u de instellingen implementeren voor de gebruikersgroepen die gebruikers die beschikken over bestaande geregistreerde apparaten bevatten. Wanneer een apparaat verbinding met de service na de wijziging in de MDM-instantie maakt, ontvangt deze nieuwe instellingen van de nieuwe MDM-instantie. Een nieuw gerichte beleid voorrang op bestaande beleidsregels op het apparaat.
- Nadat u op de nieuwe MDM-instantie, de gegevens in de [Azure-portal](https://portal.azure.com) een week tot nauwkeurig rapport kan duren. De nalevingsstatussen in Azure Active Directory en op het apparaat zijn echter nauwkeurig. Het apparaat nog steeds beveiligd.
- Apparaten waarvoor geen bijbehorende gebruikers worden niet gemigreerd naar de nieuwe MDM-instantie. Dit gedrag is doorgaans wanneer u hebt iOS Device Enrollment Program of bulksgewijs inschrijven scenario's. Voor deze apparaten contact op met ondersteuning voor hulp naar de nieuwe MDM-instantie.

## <a name="prepare-to-change-the-mdm-authority-to-intune-standalone"></a>Voorbereiden om te wijzigen van de MDM-instantie in zelfstandige versie van Intune
Controleer de volgende informatie om voor te bereiden voor de wijziging van de MDM-instantie:
- Het kan tot acht uur voor een apparaat verbinding maken met de service na wijziging van de nieuwe MDM-instantie duren.
- Zorg ervoor dat alle gebruikers die momenteel worden beheerd door hybride hebben een Intune/EMS-licentie toegewezen voordat de wijziging in de MDM-instantie. Deze licentie zorgt ervoor dat de gebruiker en hun apparaten worden beheerd door Intune standalone die na de wijziging in de MDM-instantie. Zie voor meer informatie [toewijzen Intune-licenties aan uw gebruikersaccounts](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).
- Zorg ervoor dat het beheerdersaccount van de gebruiker een Intune/EMS-licentie toegewezen heeft. Bevestig dat het beheerdersaccount van de gebruiker bij Intune voordat de wijziging van de MDM-instantie aanmelden zich. De MDM-instantie moet worden weergegeven **Configuration Manager ingesteld als** (hybride tenant) in Intune in de [Azure-portal](https://portal.azure.com) vóór de wijziging in de MDM-instantie.
- Er mag geen merkbare invloed hebben op eindgebruikers tijdens de wijziging in de MDM-instantie. 

## <a name="change-the-mdm-authority-to-intune-standalone"></a>Wijzig de MDM-instantie in zelfstandige versie van Intune
Het proces voor het wijzigen van de MDM-instantie zelfstandige versie van Intune bevat de volgende geavanceerde stappen:  
- In de Configuration Manager-console, gebruiken de **wijziging MDM-instantie op Microsoft Intune** optie voor het verwijderen van de bestaande Microsoft Intune-abonnement.
- In Intune in de [Azure-portal](https://portal.azure.com), configureren en implementeren van nieuwe instellingen en apps op de nieuwe MDM-instantie (Intune).
- De volgende keer apparaten verbinding met de service, automatisch gesynchroniseerd en ontvangen van de nieuwe instellingen van de nieuwe MDM-instantie.

#### <a name="to-change-the-mdm-authority-to-intune-standalone"></a>Wijzigen van de MDM-instantie in zelfstandige versie van Intune
1. Ga in de Configuration Manager-console naar **beheer** &gt; **overzicht** &gt; **Cloudservices** &gt; **Microsoft Intune-abonnement**, en uw bestaande Intune-abonnement verwijderen.
2. Selecteer **wijziging MDM-instantie op Microsoft Intune**, en klik vervolgens op **volgende**.
   ![Wizard Microsoft Intune-abonnement introductiepagina verwijderen](./media/mdm-change-delete-subscription.png)
3. Aanmelden bij de Intune-tenant die u oorspronkelijk hebt gebruikt bij het instellen van de MDM-instantie in Configuration Manager.
4. Klik op **Volgende** en voltooi de wizard.
5. De MDM-instantie is nu ingesteld op **Microsoft Intune**. Het Intune-abonnement wordt niet weergegeven in het knooppunt van de Microsoft Intune-abonnementen van de Configuration Manager-console. 
6. Om te controleren of de MDM-instantie is ingesteld, voert u de volgende stappen uit: een. Aanmelden bij de [Azure-portal](https://portal.azure.com) met behulp van de Intune-tenant die u eerder hebt gebruikt. 
    b. Kies **meer Services** > **bewaking + Management** > **Intune** > **apparaatinschrijving**. De MDM-instantie wordt weergegeven in de sectie rechtsboven van de **overzicht** blade. 

## <a name="next-steps"></a>Volgende stappen
Nadat de wijziging in de MDM-instantie voltooid is, controleert u de volgende stappen uit:
- Als de Intune-service detecteert dat een tenant MDM-instantie is gewijzigd, verstuurt een melding op alle geregistreerde apparaten in te checken synchroniseren met de service. Dit gedrag is buiten de regelmatig geplande controle in. Daarom nadat u de MDM-instantie voor de tenant van hybride zelfstandige versie van Intune hebt gewijzigd, alle apparaten die zijn ingeschakeld en online verbinding maken met de service, wordt de nieuwe MDM-instantie en worden beheerd door Intune standalone. Er is geen gevolgen heeft voor het beheer en beveiliging van deze apparaten.
- Apparaten die uitgeschakeld of offline zijn tijdens (of kort na) de wijziging in de MDM-instantie verbinding maken met en synchroniseren met de service onder de nieuwe MDM-instantie wanneer ze zijn ingeschakeld en online.  
- Gebruikers kunnen snel aan de nieuwe MDM-instantie wijzigen door het handmatig starten van een selectievakje in van het apparaat naar de service. Gebruikers kunnen deze actie eenvoudig doen met behulp van de bedrijfsportal-app en een apparaatgeschiktheidscontrole is gestart.
- Om te valideren of dingen goed werken nadat apparaten hebt ingecheckt en gesynchroniseerd met de service na de wijziging in de MDM-instantie, zoekt u de apparaten in de [Azure-portal](https://portal.azure.com). De apparaten die eerder zijn beheerd door Configuration Manager (hybride) nu weergeven als beheerde apparaten in Intune.    
- Er is een tussentijdse periode wanneer een apparaat offline gedurende de wijziging in de MDM-instantie en is als dat het apparaat wordt ingecheckt met de service. Om ervoor te zorgen dat het apparaat beveiligd en in werking tijdens deze periode tussentijdse blijft, blijven de volgende profielen op het apparaat gedurende zeven dagen (of totdat het apparaat verbinding met de nieuwe MDM-instantie maakt en ontvangt van de nieuwe instellingen waarmee de bestaande overschrijven toepassingsgroepen):
    - E-mailprofiel
    - VPN-profiel
    - Certificaat-profiel
    - Wi-Fi-profiel
    - Configuratieprofielen
- Voor het overschrijven van de oude instellingen, zorg dat de nieuwe instellingen die zijn bedoeld om de bestaande instellingen overschreven door dezelfde naam als de vorige waarden. Anders wordt kunnen de apparaten eindigen met redundant profielen en beleidsregels.    

  > [!TIP]   
  > Als een best practice moet u alle instellingen en configuraties, evenals implementaties, kort nadat de wijziging van de MDM-instantie is voltooid. Dit zorgt ervoor dat apparaten zijn beveiligd en dat actief wordt beheerd in de tijdelijke periode.   
-  Nadat u de MDM-instantie hebt gewijzigd, moet u de volgende stappen voor het valideren van nieuwe apparaten met succes zijn geregistreerd bij de nieuwe instantie uitvoeren:   
    - Een nieuw apparaat registreren
    - Zorg ervoor dat het nieuw ingeschreven apparaat wordt weergegeven in de [Azure-portal](https://portal.azure.com).
    - Een actie uitgevoerd, zoals vergrendelen op afstand van de [Azure-portal](https://portal.azure.com) op het apparaat. Als dat lukt, wordt het apparaat wordt beheerd door de nieuwe MDM-instantie.
- Als er problemen met specifieke apparaten, registratie ongedaan maken en de apparaten te registreren. Deze bewerking maakt verbinding met de nieuwe instantie van en zo snel mogelijk worden beheerd.
- Als u al ingeschakeld [Android for Work](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client) als een hybride-tenant en Migreer uw tenant zelfstandige versie van Intune, de Android voor werk instelling onder de beperkingen van de inschrijving mogelijk weergegeven als geblokkeerd in plaats van toestaan. Handmatig instellen op **toestaan** Android opnieuw inschakelen voor de inschrijving van het werk.<!--512117-->