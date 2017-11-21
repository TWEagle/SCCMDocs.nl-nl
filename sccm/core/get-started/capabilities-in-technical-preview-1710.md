---
title: Technische Preview 1710 | Microsoft Docs
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1710 voor System Center Configuration Manager.
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4706a58-1f11-4eab-b1eb-3d1a0da02d0f
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 309d677c0b8c692548d649346bb35bfa9d2a81f3
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="capabilities-in-technical-preview-1710-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1710 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1710 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md) om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Bekende problemen in deze Technical Preview:**
-   **Ondersteuning voor Windows 10 versie 1709 (ook wel bekend als de vallen auteurs Update)**.  Vanaf deze versie van Windows, bevat Windows media meerdere edities. Bij het configureren van een takenreeks om een upgradepakket voor besturingssysteem of de installatiekopie van besturingssysteem te gebruiken, moet u selecteren een [-editie die wordt ondersteund voor gebruik door Configuration Manager](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).
-   **Bijwerken naar een nieuwe preview-versie mislukt wanneer u een siteserver in de passieve modus hebt**. Wanneer u een preview-versie uitvoert die heeft een [primaire siteserver in de passieve modus](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), moet u de passieve modus siteserver verwijderen voordat u de preview-site met succes naar deze nieuwe preview-versie bijwerken kunt. Nadat de site de update is voltooid, kunt u de passieve modus siteserver opnieuw installeren.

  Verwijderen van de siteserver van de passieve modus:
  1. Ga in de console naar **beheer** > **overzicht** > **siteconfiguratie** > **Servers en sitesysteemrollen**, en selecteer vervolgens de passieve modus-siteserver.
  2. In de **sitesysteemrollen** deelvenster, rechts Klik op de **siteserver** rol, en kies vervolgens **rol verwijderen**.
  3. Met de rechtermuisknop op de siteserver van de passieve modus, en kies vervolgens **verwijderen**.
  4. Nadat de siteserver verwijdert, op de primaire siteserver van de actieve service opnieuw starten de **CONFIGURATION_MANAGER_UPDATE**.

**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Section Template
##  FEATURE
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-for-deploying-powershell-scripts-from-configuration-manager"></a>Verbeteringen voor het implementeren van PowerShell-Scripts uit Configuration Manager
Met deze release ondersteuning PowerShell-scripts die u implementeert nu voor gebruik van de volgende verbeteringen: 
- **Beveiligingsbereiken**.  Scripts gebruiken nu beveiligingsbereiken control-scripts schrijven en uitvoeren. Dit wordt gedaan via het toewijzen van de labels die gebruikersgroepen vertegenwoordigen. Zie voor meer informatie over het gebruik van beveiligingsbereiken [beheer op basis van rollen voor System Center Configuration Manager configureren](../../core/servers/deploy/configure/configure-role-based-administration.md).
- **Realtime-controle**. Wanneer u de uitvoering van een script bewaken, het is nu in realtime als het script wordt uitgevoerd.
- **Validatie van de parameter**. Elke parameter in het script heeft een **Script parametereigenschappen** dialoogvenster u validatie voor deze parameter. Na het toevoegen van validatie moet er treden fouten als u een waarde opgeeft voor een parameter die niet aan de validatie voldoet.

Implementatie van de PowerShell-scripts is geïntroduceerd in Technical Preview [technische Preview 1706](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console). Aanvullende verbeteringen zijn geleverd bij [technische Preview 1707](/sccm/core/get-started/capabilities-in-technical-preview-1707#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager) en vervolgens [technische Preview 1708](/sccm/core/get-started/capabilities-in-technical-preview-1708#improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager).


### <a name="try-it-out"></a>Probeer het nu!

Als u wilt uitproberen met de functie Scripts uitvoeren, Zie [maken en uitvoeren van scripts](../../apps/deploy-use/create-deploy-scripts.md).



## <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Windows 10 verbeterde telemetrie alleen om gegevens te verzenden relevant zijn voor Windows Analytics Apparaatstatus beperken
<!-- 1356148 -->

Met deze release kunt u nu instellen de gegevensverzameling voor Windows 10-telemetrie op **uitgebreid (beperkt)**. Deze instelling kunt u actie worden uitgevoerd om inzicht te krijgen over de apparaten in uw omgeving zonder apparaten rapportage van de gegevens in de **uitgebreid** telemetrie niveau met Windows 10 versie 1709 of hoger.

Het niveau uitgebreid (beperkt) telemetrie bevat metrische gegevens van het niveau basis, evenals een subset van gegevens verzameld van de **uitgebreid** niveau relevant zijn voor Windows Analytics. Zie voor meer informatie over telemetrie niveaus [telemetrie niveaus](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization#telemetry-levels).

### <a name="try-it-out"></a>Probeer het nu!
Zie voor meer informatie over het configureren van verzamelen van telemetriegegevens in Windows 10 op clients [het configureren van clientinstellingen](/sccm/core/clients/deploy/configure-client-settings). Open de **Cloudservices** venster en Windows 10 telemetrie ingesteld op **uitgebreid**.


## <a name="software-center-no-longer-distorts-icons-larger-than-250x250"></a>Software Center niet meer mogelijk vervormd pictogrammen groter is dan 250 x 250  
<!-- 1356194 -->

Software Center wordt met deze release niet meer vervormd pictogrammen die groter dan 250 x 250 zijn. Software Center gedaan deze pictogrammen fuzzy zoeken. U kunt nu een pictogram met een afmetingen in pixels van maximaal 512 x 512 instellen en zonder vervormd wordt weergegeven.

### <a name="try-it-out"></a>Probeer het nu!
Een pictogram voor uw app toevoegen in Software Center. Uitproberen Zie [toepassingen maken](/sccm/apps/deploy-use/create-applications).


## <a name="check-compliance-from-software-center-for-co-managed-devices"></a>Controleren op naleving van Software Center voor naast beheerde apparaten
<!-- 1356374 -->
In deze release, kunnen gebruikers Software Center gebruiken om te controleren van de compatibiliteit van hun CO beheerde Windows 10-apparaten, zelfs wanneer voorwaardelijke toegang wordt beheerd door Intune. Zie voor meer informatie [mede management voor Windows 10-apparaten](./capabilities-in-technical-preview-1709.md#co-management-for-windows-10-devices).


## <a name="support-for-exploit-guard"></a>Ondersteuning voor misbruik Guard
Deze release voegt ondersteuning toe voor Windows Defender Exploit-beveiliging. U kunt configureren en implementeren van beleid dat alle vier onderdelen van afscherming misbruiken beheren. Deze onderdelen zijn onder andere:
-   Aanval beperken
-   Beheerde toegang tot de map
-   Exploit-beveiliging
-   Netwerkbeveiliging

Compatibiliteitsgegevens voor implementatie van het beleid ter voorkoming van misbruik is beschikbaar vanuit de Configuration Manager-console.

Zie voor meer informatie over Guard misbruiken en specifieke onderdelen en regels [Windows Defender misbruiken Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) in de Documentatiebibliotheek van Windows.

### <a name="prerequisites"></a>Vereisten
Beheerde apparaten Windows 10 1709 vallen auteurs Update moeten worden uitgevoerd of hoger en voldoen aan de volgende vereisten zijn afhankelijk van de onderdelen en de regels die zijn geconfigureerd:

|Misbruik Guard onderdeel |Aanvullende vereisten|
|------------------------|------------------------|
| Aanval beperken  | Apparaten moeten hebben [real-timebeveiliging van Windows Defender AV]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) ingeschakeld.  |
| Beheerde toegang tot de map  | Apparaten moeten hebben [real-timebeveiliging van Windows Defender AV]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) ingeschakeld.   |
| Exploit-beveiliging  | Geen  |
| Netwerkbeveiliging  |  Apparaten moeten hebben [real-timebeveiliging van Windows Defender AV]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) ingeschakeld.  |

### <a name="create-an-exploit-guard-policy----1355468---"></a>Een beleid ter voorkoming van misbruik maken<!--1355468 -->
1.  Ga in de Configuration Manager-console naar **activa en naleving** > **Endpoint Protection**, en klik vervolgens op **Windows Defender misbruiken Guard**.
2.  Op de **Start** tabblad, in de **maken** groep, klikt u op **Exploit-beleid maken**.
3.  Geef op de pagina **Algemeen** van de wizard **Configuratie-item maken**een naam en een optionele beschrijving voor het configuratie-item op.
4.  Selecteer vervolgens de Guard Exploit-onderdelen die u wilt beheren met dit beleid. Voor elk onderdeel dat u selecteert, kunt u aanvullende details vervolgens configureren.
  - **Aanval beperken:** De Office-bedreiging, scripting bedreigingen en e-mailbericht bedreigingen die u wilt controleren of blokkeren configureren. U kunt ook specifieke bestanden of mappen uitsluiten van deze regel.
  - **Toegang tot map beheerd:** Controle of blokkeren configureren en voeg vervolgens de Apps die dit beleid kunnen omzeilen.  U kunt ook andere mappen die niet zijn beveiligd door standaard opgeven.
  - **Exploit-beveiliging:**  Geef een XML-bestand met instellingen voor het oplossen van misbruik van systeemprocessen en apps. U kunt deze instellingen exporteren van de Windows Defender Security Center-app op een apparaat met Windows 10.
  - **Netwerkbeveiliging:** Netwerkbeveiliging ingesteld op blokkeren of audit toegang tot verdachte domeinen.
5.  Voltooi de wizard voor het maken van het beleid, u later op apparaten implementeren kunt.

### <a name="deploy-an-exploit-guard-policy"></a>Een beleid ter voorkoming van misbruik implementeren     
Nadat u beleid ter voorkoming van misbruik gemaakt, gebruikt u de wizard misbruiken Guard-beleid implementeren voor de implementatie ervan. Om dit te doen, opent u de Configuration Manager-console naar **activa en naleving** > **Endpoint Protection**, en klik vervolgens op **misbruiken Guard-beleid implementeren**.

## <a name="limited-support-for-cng-certificates"></a>Beperkte ondersteuning voor CNG-certificaten
<!-- 1356191 -->
Vanaf deze release kunt u nu kunt [Cryptography API: Next Generation (CNG)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) certificaatsjablonen voor de volgende scenario's:

- Clientregistratie en -communicatie met een HTTPS-beheerpunt.   
- Software distributie en het application-implementatie met een HTTPS-distributiepunt.   
- Implementatie van besturingssysteem.  
- Messaging-SDK (met de laatste update) en ISV-Proxy-client.   
- Cloud Management Gateway-configuratie.  

CNG om certificaten te gebruiken, moet uw certificeringsinstantie (CA) voor de certificaatsjablonen CNG voor target-machines.  Sjabloondetails variëren afhankelijk van het scenario; de volgende eigenschappen zijn echter vereist:

- **Compatibiliteit** tabblad

    - **Certificeringsinstantie** moet WindowsServer 2008 of hoger. (Windows Server 2012 wordt aanbevolen).

    - **Ontvanger van certificaat** moet Windows Vista of de Server 2008 of hoger. (Windows 8 of Windows Server 2012 wordt aanbevolen).

- **Cryptografie** tabblad

    - **Providercategorie** moet **Key Storage Provider**.  (Vereist)

U wordt aangeraden het bouwen van de onderwerpnaam van Active Directory-informatie voor de beste resultaten.  DNS-naam gebruiken voor **indeling van de onderwerpnaam** en de DNS-naam in de alternatieve onderwerpnaam opnemen.  Anders moet u deze informatie verstrekken zodra het apparaat wordt ingeschreven in het certificaatprofiel.


## <a name="improved-descriptions-for-pending-computer-restarts-----1356283---"></a>Verbeterde beschrijvingen van in afwachting van opnieuw opstarten<!--1356283 -->
In [technical preview 1708](/sccm/core/get-started/capabilities-in-technical-preview-1708#restart-computers-from-the-configuration-manager-console), hebben we de mogelijkheid om u te identificeren van apparaten die door een herstart van de Configuration Manager-console zijn toegevoegd.

Vanaf deze technical preview is aanvullende informatie die informatie geven over het proces of de actie die het opstarten is aangevraagd door de console worden weergegeven.

## <a name="device-guard-policy-changes----1355092---"></a>Device Guard beleidswijzigingen<!-- 1355092 -->
Met de 1710 Technical Preview-build zijn de volgende drie wijzigingen aangebracht ten opzichte van Device Guard beleid:

### <a name="device-guard-policies-renamed-to-windows-defender-application-control-policies"></a>Beleidsregels voor apparaten Guard gewijzigd in het beleid voor toepassingsbeheer voor Windows Defender
Device Guard beleidsregels is hernoemd aan beleidsregels voor toepassingsbeheer voor Windows Defender. Zo is, bijvoorbeeld de **wizard beleid voor Device Guard maken** heet nu **wizard beleid voor Windows Defender Toepassingsbeheer maken**.

### <a name="restart-is-not-required-to-apply-policies"></a>Opnieuw opstarten is niet vereist voor het beleid toepassen
Beginnen met het vallen auteurs Update voor Windows versie 1709, opnieuw apparaten met behulp van de nieuwe versie van Windows niet starten om toe te passen van het beleid voor toepassingsbeheer voor Windows Defender.

Opnieuw opstarten is de standaardinstelling.

#### <a name="try-it-out"></a>Probeer het nu!  

Als u uitschakelen opnieuw wordt opgestart wilt, voert u deze stappen:

1.  Open de **maken Windows Defender Toepassingsbeheerbeleid** wizard.
2.  Op de **algemene** pagina, schakel het selectievakje voor **afdwingen van het opnieuw opstarten van apparaten, zodat dit beleid kan worden afgedwongen voor alle processen**.
3.  Klik op **volgende** totdat de wizard is voltooid.

Een geautomatiseerde opnieuw opstarten wordt nog steeds afgedwongen voor oudere versies van Windows.

### <a name="automatically-run-software-trusted-by-the-intelligent-security-graph"></a>Software die wordt vertrouwd door de intelligente beveiliging grafiek automatisch wordt uitgevoerd

Beheerders hebben nu de optie vergrendelde apparaten uit te voeren van vertrouwde software met een goede reputatie zoals wordt bepaald door de Microsoft Intelligent beveiliging grafiek (ISG) toe te staan. De ISG bestaat uit de Windows Defender SmartScreen en andere Microsoft-services.

De apparaten moeten worden uitgevoerd als Windows Defender SmartScreen voor de software om te worden vertrouwd.

#### <a name="try-it-out"></a>Probeer het nu!  

Volg deze stappen zodat een apparaat met Windows Defender SmartScreen vertrouwde software uitvoert:

1.  Open de **maken Windows Defender Toepassingsbeheerbeleid wizard**.
2.  Op de **insluitingen** pagina, schakel het selectievakje voor **software die wordt vertrouwd door de intelligente beveiliging grafiek autoriseren**.
3.  In de **vertrouwde bestanden of map** Voeg de bestanden en mappen die u wilt worden vertrouwd.
4.  Klik op **volgende** totdat de wizard is voltooid.

## <a name="configure-and-deploy-windows-defender-application-guard-policies----1351960---"></a>Windows Defender toepassing Guard beleid configureren en implementeren<!-- 1351960 -->

[Windows Defender toepassing Guard](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97) is een nieuwe Windows-functie die voorkomen dat uw gebruikers via niet-vertrouwde websites in een beveiligde geïsoleerde container die is niet toegankelijk voor andere onderdelen van het besturingssysteem. In deze technical preview ondersteuning voor het configureren van deze functie met Configuration Manager-instellingen voor naleving die u configureert en vervolgens implementeert op een verzameling toegevoegd. Deze functie worden uitgebracht Preview-versie voor de 64-bits versie van de Windows 10-Creator Update (codename: RS2). Als u wilt testen van dit onderdeel nu moet u een preview-versie van deze update.

### <a name="before-you-start"></a>Voordat u begint
Voor het maken en implementeren van beleid voor Windows Defender toepassing Guard, moeten de Windows 10-apparaten waarop u het beleid implementeert worden geconfigureerd met een beleid voor het isoleren van netwerken. Zie de blog post waarnaar wordt verwezen later voor meer informatie. Deze functie werkt alleen met huidige Insider voor Windows 10-builds. Als u wilt testen, moeten uw clients worden uitgevoerd een recente Windows 10 Insider niet maken.

### <a name="try-it-out"></a>Probeer het nu!

Als u wilt de basisbeginselen over Windows Defender toepassing Guard lezen [het blogbericht](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97).

Een beleid maken en om te bladeren, de beschikbare instellingen:
1. In de **Configuration Manager** console, kiest u **activa en naleving**.
2. In de **activa en naleving** werkruimte, kiest u **overzicht** > **Endpoint Protection** > **Windows Defender toepassing Guard**.
3. In de **Start** tabblad, in de **maken** groep, klikt u op **maken Windows Defender Guard toepassingsbeleid**.
4. Met behulp van de blogbericht als uitgangspunt, kunt u bladeren en configureer de beschikbare instellingen voor de functie uitproberen.
5. In deze release toegevoegd de nieuwe Netwerkdefinitie pagina bij de wizard. Geef hier de zakelijke identiteit en definieer de grens van uw bedrijfsnetwerk.

    > [!NOTE]
    > Windows 10-computers opslaan slechts één netwerk isolatie lijst op de client. In deze release kunt u twee soorten netwerk isolatie lijsten (vanaf Windows Information Protection en vanaf Windows Defender toepassing Guard) maken en implementeren naar de client. Als u beide beleidsregels implementeren, moeten deze netwerk isolatie lijsten overeenkomen. Als u lijsten die niet met dezelfde client overeenkomen implementeert, mislukt de implementatie.

    U vindt meer informatie over het opgeven van netwerkdefinities in het [documentatie van Windows-gegevensbeveiliging](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).

6. Wanneer u klaar bent, voltooi de wizard en implementeer het beleid voor een of meer Windows 10-apparaten.

### <a name="further-reading"></a>Lees hier meer over

Voor meer informatie over Windows Defender toepassing Guard, Zie [dit blogbericht](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Zie ook voor meer informatie over Windows Defender toepassing Guard zelfstandige modus, [dit blogbericht](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).

## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
