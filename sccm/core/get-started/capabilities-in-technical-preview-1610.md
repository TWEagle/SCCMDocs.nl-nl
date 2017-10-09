---
title: Mogelijkheden in Technical Preview 1610 Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview voor System Center Configuration Manager, versie 1610.
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: "2"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b164b6a177b8b4d1eebd0bbd54e67e90376929be
ms.sourcegitcommit: c145e515843a0f37c2e5ca5dbd22072a219d06b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/03/2017
---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1610 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*



Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1610 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren.      Controleer voordat u deze versie van de technical preview installeert, de inleidende informatie [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md), om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.    


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filteren op Inhoudsgrootte in regels voor automatische implementatie
U kunt nu filteren op de grootte van de inhoud voor software-updates in de regels voor automatische implementatie. U kunt bijvoorbeeld instellen de **inhoud grootte (KB)** filteren op **< 2048** alleen softwareupdates te downloaden die kleiner dan 2 MB zijn. Met dit filter voorkomt dat grote software-updates automatisch downloaden naar betere ondersteuning vereenvoudigd Windows downlevel-onderhoud als de netwerkbandbreedte beperkt is. Zie voor meer informatie [Configuration Manager en vereenvoudigd onderhoud van Windows op omlaag niveau besturingssystemen](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

#### <a name="to-configure-the-content-size-field"></a>Het veld Inhoudsgrootte configureren
Voor het configureren van de **inhoud grootte (KB)** veld, gaat u naar de **Software-Updates** pagina in de Wizard automatische implementatie maken regel wanneer u een ADR maken of Ga naar de **Software-Updates** tabblad in de eigenschappen voor een bestaande ADR.

![Inhoudsgrootte veld](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>Verbeterde functionaliteit voor vereiste software-dialoogvensters
Wanneer een gebruiker de vereiste software ontvangt van de **uitstellen en Help me herinneren:** instelt, kunnen ze selecteren in de volgende lijst in de vervolgkeuzelijst van waarden:
- Later: geeft aan dat meldingen worden gepland op basis van de instellingen voor meldingen geconfigureerd in de clientagentinstellingen.
- Vaste tijd: geeft aan dat de melding wordt gepland om opnieuw op de geselecteerde tijd weer te geven. Bijvoorbeeld, als een gebruiker 30 minuten selecteert, weergegeven de melding over 30 minuten opnieuw.

![Computer Agent pagina in de clientagentinstellingen](media/computeragentsettings.png)

De maximale uitstellen is altijd op basis van tijd op de melding ingestelde waarden in de clientagentinstellingen op elk moment langs de tijdlijn voor implementatie. Bijvoorbeeld, als de **langer dan 24 uur deadline voor implementatie, gebruikers herinneren elke (uur)** instellen op de Computer Agent pagina is geconfigureerd voor 10 uur en meer dan 24 uur vóór de deadline is wanneer het dialoogvenster wordt gestart, de gebruiker zou worden gepresenteerd met een set opties voor bewerkingen worden uitgesteld tot maar nooit meer dan 10 uur. Als de deadline nadert, wordt het dialoogvenster minder mogelijkheden consistent zijn met de relevante instellingen voor Clientagent voor elk onderdeel van de implementatie-tijdlijn weergegeven.

Daarnaast voor een implementatie met hoog risico, zoals een takenreeks die een besturingssysteem implementeert is de eindgebruikerservaring voor melding nu ingrijpender. In plaats van een melding van tijdelijke taakbalk, elke keer dat de gebruiker wordt geïnformeerd dat essentieel softwareonderhoud vereist is, een dialoogvenster zoals de volgende wordt weergegeven op de computer van de gebruiker:

![Dialoogvenster voor vereiste Software](media/requiredsoftwaredialog.png)


Voor meer informatie:
- [Instellingen voor het beheren van implementaties met een hoog risico](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Clientinstellingen configureren](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>Eerder goedgekeurde toepassingsaanvragen weigeren

Als beheerder kunt u nu een eerder goedgekeurde toepassingsaanvraag weigeren. Eenmaal is geweigerd voor het installeren van deze toepassing later gebruikers moeten een aanvraag opnieuw indienen. Denial-of verwijderd de toepassing; niet in plaats daarvan wordt opnieuw goedkeuren voor een nieuw verzoek voor die toepassing bij die gebruiker gedwongen. Weigeren van de toepassing-aanvraag was eerder alleen beschikbaar voor aanvragen van toepassingen die niet zijn goedgekeurd.

#### <a name="try-it-out"></a>Try it out in
Voor het weigeren van een toepassing heeft een verzoek goedgekeurd:

1.  In de Configuration Manager-console [maken en implementeren van een toepassing](https://docs.microsoft.com/sccm/apps/deploy-use/create-applications) waarvoor goedkeuring is vereist.
2.  Software Center te openen en een aanvraag indienen voor de toepassing op een clientcomputer.
3.  In de Configuration Manager-console, moet u de toepassingsaanvraag goedkeuren.
4.  De goedgekeurde toepassingsaanvraag weigeren: Navigeer in de Configuration Manager-console **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **goedkeuringsaanvragen** en selecteer de toepassingsaanvraag die u wilt weigeren.  Klik in het lint op **weigeren**.

## <a name="exclude-clients-from-automatic-upgrade"></a>Clients uitsluiten van Automatische upgrade
Technische Preview 1610 introduceert een nieuwe instelling die u gebruiken kunt voor het uitsluiten van een verzameling van clients van de versies van de bijgewerkte client automatisch worden geïnstalleerd.  Dit geldt voor de automatische upgrade, evenals andere methoden, zoals software-update-gebaseerde upgrade aanmeldingsscripts en Groepsbeleid. Dit kan worden gebruikt voor een verzameling van computers die moeten worden groter voorzichtig bij het upgraden van de client. Een client die zich in een uitgesloten verzameling negeert aanvragen om bijgewerkte clientsoftware te installeren.

### <a name="configure-exclusion-from-automatic-upgrade"></a>Uitsluiting van Automatische upgrade configureren
Automatische upgrade uitsluitingen configureren:
1.  In de Configuration Manager-console openen **hiërarchie-instellingen** onder **beheer > siteconfiguratie > Sites**, en selecteer vervolgens de **Clientupgrade** tabblad.
2.  Schakel het selectievakje voor **uitsluiten opgegeven clients upgrade**, en vervolgens voor **uitsluiting verzameling**, selecteer de verzameling die u wilt uitsluiten. U kunt slechts één verzameling voor uitsluiting selecteren.
3.  Klik op **OK** te sluiten en de configuratie op te slaan. Vervolgens, nadat clients beleid bijwerken, clients in de uitgesloten verzameling wordt niet langer automatisch updates installeren voor de clientsoftware.

  ![Instellingen voor uitsluiting van Automatische upgrade](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> Hoewel de gebruikersinterface wordt aangegeven dat clients niet worden bijgewerkt via een van deze methoden, zijn er twee methoden die u kunt deze instellingen overschrijven. Client-pushinstallatie en een handmatige clientinstallatie kunnen worden gebruikt voor het onderdrukken van deze configuratie. Zie de volgende sectie voor meer informatie.

### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Een client die zich in een uitgesloten verzameling bijwerken
Zolang een verzameling is geconfigureerd om te worden uitgesloten, kunnen leden van de verzameling alleen hun bijgewerkt door een van twee methoden, deze de uitsluiting van de heffen clientsoftware hebben:
 - **Push-clientinstallatie** – u kunt push-clientinstallatie naar een client bijwerkt die zich in een uitgesloten verzameling. Dit is toegestaan als het wordt beschouwd als de bedoeling van de beheerder en kunt u clients bijwerken zonder de volledige verzameling worden verwijderd uit uitsluiting.       
 - **Handmatige clientinstallatie** – u kunt clients die zich in een uitgesloten verzameling als u de volgende opdrachtregel-switch met ccmsetup handmatig bijwerken: ***/ignoreskipupgrade***

  Als u probeert bij te werken handmatig een client die lid is van de uitgesloten verzameling en gebruik deze schakeloptie niet, wordt de client de nieuwe clientsoftware niet installeren. Zie voor meer informatie [Configuration Manager-Clients handmatig installeren](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually).

Zie voor meer informatie over clientinstallatiemethoden [clients implementeren op Windows-computers in System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

## <a name="windows-defender-configuration-settings"></a>Configuratie-instellingen voor Windows Defender

U kunt nu instellingen voor Windows Defender-client configureren op Intune ingeschreven Windows 10-computers met configuratie-items in de Configuration Manager-console.

U kunt in het bijzonder de volgende Windows Defender-instellingen configureren:
- Real-timecontrole toestaan
- Gedragscontrole toestaan
- Systeem voor netwerkinspectie inschakelen
- Alle downloads scannen
- Scannen van scripts toestaan
- Bestands- en programma-activiteit controleren
  - Bewaakte bestanden
- Dagen opgeloste malware bijhouden
- Toegang tot de gebruikersinterface van client toestaan
- Een systeemscan plannen
  - Geplande dag
  - Geplande tijd
- Een dagelijkse snelle scan plannen
  - Geplande tijd
- % Van de limiet CPU-gebruik tijdens een scan Scan bestanden te archiveren
- E-mailberichten scannen
- Verwisselbare stations scannen
- Netwerkstations scannen
- Bestanden die zijn geopend vanuit net shares scannen
- Update-interval voor handtekeningen
- Cloudbeveiliging toestaan
- Gebruikers vragen voorbeelden
- Detectie van mogelijk ongewenste toepassingen
- Uitgesloten bestanden/mappen
- Uitgesloten bestandsextensies
- Uitgesloten processen

> [!NOTE]
> Deze instellingen kunnen alleen worden geconfigureerd op clientcomputers met Windows 10 November Update (1511) en hoger.

### <a name="try-it-out"></a>Probeer het nu!

1.  Ga in de Configuration Manager-console **activa en naleving** > **overzicht** > **instellingen voor naleving** > **configuratie-Items**, en maak een nieuwe **configuratie-Item**.
2.  Voer een naam in en selecteer vervolgens **Windows 8.1 en Windows 10** onder **instellingen voor apparaten die worden beheerd zonder Configuration Manager-client** en klik op **volgende**.
3.  Zorg ervoor dat **alle Windows 10 (64-bits)** en **alle Windows 10 (32-bits)** zijn geselecteerd op de **ondersteunde Platforms** pagina en klik vervolgens op **volgende**.
4.  Selecteer de **Windows Defender** instelling groep, klikt u vervolgens op **volgende**.
5.  Configureer de gewenste instellingen op deze pagina en klik vervolgens op **volgende**.
6.  Voltooi de wizard.
7.  Dit configuratie-item toevoegen aan een configuratiebasislijn en implementeren van deze basislijn op computers met Windows 10 November Update (1511) of hoger.

> [!NOTE]
> Vergeet niet om te controleren de **niet-compatibele instellingen herstellen** selectievakje bij het implementeren van de configuratiebasislijn.

## <a name="request-policy-sync-from-administrator-console"></a>Aanvraag beleid synchroniseren vanuit de administrator-console

U kunt nu een synchronisatie met beleid voor een mobiel apparaat aanvragen via de Configuration Manager-console, in plaats van hoeven aan te vragen een synchronisatie van het apparaat zelf. Informatie over de status van de synchronisatie-aanvraag is beschikbaar als een nieuwe kolom in de apparaat-weergaven, aangeroepen **status van externe synchronisatie**. Status wordt ook weergegeven in de **detectiegegevens** sectie van de **eigenschappen** dialoogvenster voor elk mobiele apparaat.

### <a name="try-it-out"></a>Probeer het nu!

1.  Ga in de Configuration Manager-console **activa en naleving** > **overzicht** > apparaten.
2.  In de **acties extern apparaat** selecteert u **synchronisatie-aanvraag verzenden**.

Synchronisatie kan vijf tot tien minuten duren. Eventuele wijzigingen in het beleid worden gesynchroniseerd met het apparaat. U kunt de status van de synchronisatieaanvraag in volgen de **Sync-status van externe** kolom in de **apparaten** weergave, of het apparaat **eigenschappen** dialoogvenster.

## <a name="additional-security-role-support"></a>Ondersteuning voor extra beveiliging rol

Naast de volledige beheerder hebben de volgende ingebouwde beveiligingsrollen nu volledige toegang tot de items in de **alle apparaten in Bedrijfseigendom** knooppunt, met inbegrip van **Predeclared apparaten**, **iOS-Inschrijvingsprofielen**, en **Windows-Inschrijvingsprofielen**: • **Asset Manager** • **toegang tot bedrijfsbronnen**

Alleen-lezen toegang tot deze gebieden van de Configuration Manager-console nog steeds te krijgen tot de **alleen-Lezenanalist** rol.

## <a name="conditional-access-for-windows-10-vpn-profiles"></a>Voorwaardelijke toegang voor Windows 10 VPN-profielen

U kunt nu Windows 10 vereisen apparaten zijn ingeschreven in Azure Active Directory aan het beleid voldoen om VPN-toegang tot en met Windows 10 VPN-profielen die zijn gemaakt in de Configuration Manager-console. Dit is mogelijk via de nieuwe **voorwaardelijke toegang inschakelen voor deze VPN-verbinding** selectievakje op het **verificatiemethode** pagina in de wizard VPN-profiel en de eigenschappen van de VPN-profiel voor Windows 10 VPN-profielen. U kunt ook een apart certificaat voor eenmalige aanmelding verificatie opgeven als u voorwaardelijke toegang voor het profiel inschakelen.

## <a name="see-also"></a>Zie ook
[Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md)
