---
title: Mogelijkheden in Technical Preview 1610 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1610.
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 59633ce68e2bb2d722900215751f345d6d098721
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>Mogelijkheden in Technical Preview 1610 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (technische Preview)*



Dit artikel worden de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1610 zijn geïntroduceerd. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw technische preview van Configuration Manager site installeren.      Voordat u deze versie van de technische preview installeert, leest u de inleidende onderwerp [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om meer vertrouwd raken met algemene vereisten en beperkingen voor het gebruik van een technische preview hoe tussen versies en hoe u feedback geven over de functies in een technische preview bijwerken.    


**De volgende zijn nieuwe functies die u met deze versie kunt uitproberen.**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filteren op de omvang van de inhoud in de regels voor automatische implementatie
Nu kunt u filteren op de grootte van de inhoud voor software-updates in de regels voor automatische implementatie. Bijvoorbeeld, u kunt instellen de **inhoud grootte (KB)** filteren op **< 2048** alleen softwareupdates te downloaden die kleiner dan 2 MB zijn. Met dit filter voorkomt grote software-updates automatisch downloaden naar betere ondersteuning vereenvoudigd Windows downlevel onderhoud als netwerkbandbreedte beperkt is. Zie voor meer informatie, [Configuration Manager en Windows vereenvoudigd onderhoud op omlaag niveau besturingssystemen](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

#### <a name="to-configure-the-content-size-field"></a>Het veld omvang van de inhoud configureren
Configureren van de **inhoud grootte (KB)** veld, Ga naar de **Software-Updates** pagina in de Wizard automatische implementatie maken regel wanneer u een ADR maakt of gaat u naar de **Software-Updates** tabblad in de eigenschappen voor een bestaande ADR.

![Inhoudsgrootte veld](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>Verbeterde functionaliteit voor vereiste software dialoogvensters
Wanneer een gebruiker de vereiste software ontvangt van het **uitstellen en Help me herinneren:** stellen, kunnen ze selecteren uit de volgende lijst vervolgkeuzelijst met waarden:
- Later: Hiermee geeft u de meldingen zijn gepland op basis van de instellingen voor meldingen geconfigureerd in de instellingen voor Clientagent.
- Vaste tijd: geeft aan dat de melding wordt gepland om opnieuw na de geselecteerde periode weer te geven. Als de gebruiker 30 minuten kiest, kunt u voor de melding, wordt weergegeven in 30 minuten opnieuw.

![Agent-pagina in de clientagentinstellingen computer](media/computeragentsettings.png)

De maximale uitstellen tijd is altijd gebaseerd op de melding ingestelde waarden in de clientagentinstellingen op elk moment langs de tijdlijn voor implementatie. Bijvoorbeeld, als de **groter is dan 24 uur deadline voor implementatie, gebruikers herinneren elke (uur)** instellen op de Computer Agent pagina is geconfigureerd voor 10 uur en meer dan 24 uur vóór de deadline wanneer het dialoogvenster wordt gestart, de gebruiker zou worden gepresenteerd met een set opties uitstellen tot maar nooit meer dan 10 uur. Als de deadline nadert, wordt het dialoogvenster minder opties consistent zijn met de relevante clientagentinstellingen voor elk onderdeel van de implementatie-tijdlijn weergegeven.

Daarnaast voor een hoog risico implementatie, zoals een takenreeks die een besturingssysteem implementeert is de gebruikerservaring van de melding nu ingrijpender. In plaats van een tijdelijke taakbalk melding, telkens wanneer de gebruiker wordt geïnformeerd dat essentieel softwareonderhoud vereist is, een dialoogvenster zoals het volgende wordt weergegeven op de computer van de gebruiker:

![Dialoogvenster voor vereiste Software](media/requiredsoftwaredialog.png)


Voor meer informatie:
- [Instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Het configureren van clientinstellingen](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>Eerder goedgekeurde toepassingsaanvragen weigeren

Als beheerder kunt u nu een eerder goedgekeurde toepassingsaanvraag weigeren. Eenmaal is geweigerd voor het installeren van deze toepassing hoger gebruikers moeten een aanvraag opnieuw indienen. Denial-of worden niet verwijderd door de toepassing. in plaats daarvan wordt het goedkeuren van een nieuwe aanvraag voor die toepassing van die gebruiker. Eerder is weigeren van aanvraag van toepassing alleen beschikbaar voor aanvragen die niet zijn goedgekeurd.

#### <a name="try-it-out"></a>Probeer het nu
Een toepassing weigeren aanvraag goedgekeurd:

1.    In de Configuration Manager-console [maken en implementeren van een toepassing](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/create-applications) die moet worden goedgekeurd.
2.    Software Center wordt geopend en een aanvraag indienen voor de toepassing op een clientcomputer.
3.    Goedkeuren in de Configuration Manager-console de toepassingsaanvraag.
4.    De toepassingsaanvraag goedgekeurde weigeren: Navigeer in de Configuration Manager-console **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **goedkeuringsaanvragen** en selecteer de toepassingsaanvraag die u wilt weigeren.  Klik in het lint op **weigeren**.

## <a name="exclude-clients-from-automatic-upgrade"></a>Clients uitsluiten voor automatische upgrade
Technische Preview 1610 introduceert een nieuwe instelling die kunt u een verzameling van clients uitsluiten van automatisch versies van de bijgewerkte client te installeren.  Dit geldt voor automatische upgrade, evenals andere methoden zoals het bijwerken van de software update-gebaseerde, aanmeldingsscripts en Groepsbeleid. Dit kan worden gebruikt voor een verzameling van computers die groter voorzichtig moeten bij het upgraden van de client. Een client die zich in een verzameling uitgesloten negeert aanvragen om bijgewerkte clientsoftware te installeren.

### <a name="configure-exclusion-from-automatic-upgrade"></a>Uitsluiting van Automatische upgrade configureren
Automatische upgrade uitsluitingen configureren:
1.    In de Configuration Manager-console openen **hiërarchie-instellingen** onder **beheer > siteconfiguratie > Sites**, en selecteer vervolgens de **Clientupgrade** tabblad.
2.    Schakel het selectievakje voor **uitsluiten opgegeven clients upgrade**, en vervolgens voor **uitsluiting verzameling**, selecteer de verzameling die u wilt uitsluiten. U kunt slechts één verzameling voor uitsluiting selecteren.
3.    Klik op **OK** om te sluiten en de configuratie op te slaan. Klik, nadat clients beleid bijwerken, clients in de verzameling uitgesloten wordt niet langer automatisch updates installeren voor de clientsoftware.

  ![Instellingen voor automatische upgrade uitsluiting](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> Hoewel de gebruikersinterface wordt aangegeven dat clients niet worden bijgewerkt via een van deze methoden, zijn er twee methoden die u kunt deze instellingen overschrijven. Client-pushinstallatie en een handmatige clientinstallatie kunnen worden gebruikt om deze configuratie te onderdrukken. Zie de volgende sectie voor meer informatie.

### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Het bijwerken van een client die zich in een verzameling uitgesloten
Zolang op een verzameling wordt geconfigureerd om te worden uitgesloten, hebben leden van deze verzameling alleen de clientsoftware op een van twee manieren heffen uitsluiting bijgewerkt:
 - **Push-clientinstallatie** – u kunt push-clientinstallatie naar een client bijwerkt die zich in een verzameling met de uitgesloten. Dit is toegestaan omdat deze wordt beschouwd als het uw bedoeling van de beheerder en maakt u om clients te upgraden zonder te verwijderen van de volledige verzameling van uitsluiting.       
 - **Handmatige clientinstallatie** – u kunt clients die zich in een verzameling met de uitgesloten als u de volgende opdrachtregelparameter met ccmsetup handmatig bijwerken: ***/ignoreskipupgrade***

  Als u probeert bij te werken handmatig een client die lid is van de uitgesloten verzameling en gebruik deze switch, zal de client de nieuwe clientsoftware niet installeren. Zie voor meer informatie [handmatig Configuration Manager Clients installeren](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually).

Zie voor meer informatie over installatiemethoden voor clients [het implementeren van clients op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

## <a name="windows-defender-configuration-settings"></a>Configuratie-instellingen voor Windows Defender

Nu kunt u clientinstellingen voor Windows Defender op Intune zijn ingeschreven Windows 10-computers met configuratie-items in de Configuration Manager-console.

U kunt wat betreft de volgende Windows Defender-instellingen configureren:
- Realtime-controle toestaan
- Bewaking van gedrag toestaan
- Systeem voor netwerkinspectie inschakelen
- Alle downloads scannen
- Scannen van scripts toestaan
- Bestands- en programma-activiteit controleren
  - Bewaakte bestanden
- Dagen tot opgeloste malware bijhouden
- Toegang tot gebruikersinterface voor client toestaan
- Een systeemscan plannen
  - Geplande dag
  - Geplande tijd
- Een dagelijkse snelle scan plannen
  - Geplande tijd
- Limiet CPU-gebruik % tijdens een scan Scan bestanden te archiveren
- E-mailberichten scannen
- Verwisselbare stations scannen
- Toegewezen stations scannen
- Bestanden die zijn geopend vanuit net shares scannen
- Handtekening-update-interval
- Cloudbeveiliging toestaan
- Gebruikers vragen voorbeelden
- Potentieel ongewenste toepassing detectie
- Uitgesloten bestanden/mappen
- Uitgesloten bestandsextensies
- Uitgesloten processen

> [!NOTE]
> Deze instellingen kunnen alleen worden geconfigureerd op clientcomputers met Windows 10 November Update (1511) en hoger.

### <a name="try-it-out"></a>Probeer het nu!

1.    Ga in de Configuration Manager-console **activa en naleving** > **overzicht** > **compatibiliteitsinstellingen** > **configuratie-Items**, en maakt u een nieuwe **configuratie-Item**.
2.    Voer een naam in en selecteer vervolgens **Windows 8.1 en Windows 10** onder **-instellingen voor apparaten beheerd zonder dat de Configuration Manager-client** en klikt u op **volgende**.
3.    Zorg ervoor dat **alle Windows 10 (64-bits)** en **alle Windows 10 (32-bits)** zijn geselecteerd op de **ondersteunde Platforms** pagina en klik vervolgens op **volgende**.
4.    Selecteer de **Windows Defender** stellen groep, klikt u vervolgens op **volgende**.
5.    Configureer de gewenste instellingen op deze pagina en klik vervolgens op **volgende**.
6.    Voltooi de wizard.
7.    Dit configuratie-item toevoegen aan een configuratiebasislijn en implementeer deze basislijn op computers met Windows 10 November Update (1511) of hoger.

> [!NOTE]
> Vergeet niet om te controleren de **niet-compatibele instellingen herstellen** selectievakje in bij het implementeren van de configuratiebasislijn.

## <a name="request-policy-sync-from-administrator-console"></a>Aanvraag beleid synchronisatie van de administrator-console

U kunt nu een synchronisatie met beleid voor een mobiel apparaat van de Configuration Manager-console in plaats van dat nodig is om aan te vragen van een synchronisatie van het apparaat zelf aanvragen. Informatie over de status van de synchronisatie-aanvraag is beschikbaar als een nieuwe kolom in de apparaat-weergaven kunt genoemd **afstand synchronisatiestatus**. De status wordt ook weergegeven in de **detectiegegevens** sectie van de **eigenschappen** dialoogvenster voor elk mobiel apparaat.

### <a name="try-it-out"></a>Probeer het nu!

1.    Ga in de Configuration Manager-console **activa en naleving** > **overzicht** > apparaten.
2.    In de **externe apparaat acties** selecteert u **Sync aanvraag verzenden**.

Synchronisatie kan vijf tot tien minuten duren. Wijzigingen in het beleid zijn gesynchroniseerd met het apparaat. U kunt de status van de synchronisatieaanvraag in volgen de **afstand synchronisatiestatus** kolom in de **apparaten** weergave, of op het apparaat **eigenschappen** dialoogvenster.

## <a name="additional-security-role-support"></a>Ondersteuning voor extra beveiliging rol

Naast het volledige beheerder hebben de volgende ingebouwde beveiligingsrollen nu volledige toegang tot items in de **alle apparaten in Bedrijfseigendom** knooppunt, met inbegrip van **Predeclared apparaten**, **iOS Inschrijvingsprofielen**, en **Windows-Inschrijvingsprofielen**: • **Asset Intelligence-beheerder** • **toegang tot bedrijfsbronnen**

Alleen-lezen toegang tot deze gebieden van de Configuration Manager-console nog steeds te krijgen tot de **alleen-Lezenanalist** rol.

## <a name="conditional-access-for-windows-10-vpn-profiles"></a>Voorwaardelijke toegang voor Windows 10 VPN-profielen

U kunt nu vereisen Windows 10 apparaten geregistreerd in Azure Active Directory aan het beleid voldoen om VPN-toegang hebben via Windows 10 VPN-profielen die zijn gemaakt in de Configuration Manager-console. Dit is mogelijk via het nieuwe **voorwaardelijke toegang inschakelen voor deze VPN-verbinding** selectievakje aan de **verificatiemethode** pagina in de wizard VPN-profiel en de eigenschappen van VPN-profiel voor Windows 10 VPN-profielen. U kunt ook een afzonderlijke certificaat voor verificatie voor eenmalige aanmelding opgeven als u voorwaardelijke toegang voor het profiel inschakelen.

## <a name="see-also"></a>Zie ook
[Technische Preview van System Center Configuration Manager](../../core/get-started/technical-preview.md)

