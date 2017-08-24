---
title: Opties configureren | Microsoft Docs
description: Opties voor het gebruik van System Center Updates Publisher configureren
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e620080-5400-45bb-87c2-fbdbc8aeacac
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: b66ed0a5e1c87d8c82853da86e3d55b0e2c043bb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="configure-options-for-updates-publisher"></a>Opties voor Updates Publisher configureren

*Van toepassing op: System Center Updates Publisher*

Bekijk en configureer de opties en gerelateerde instellingen die invloed hebben op de werking van Updates Publisher.

Voor toegang tot de opties voor Updates Publisher, in de linkerbovenhoek van de console, klikt u op de **Updates Publisher** **eigenschappen** tabblad en kies vervolgens **opties**.

![Opties](media/properties1.png)   


Opties zijn onderverdeeld in het volgende:

-   Server bijwerken
-   Configuration Manager-Server
-   Proxy-instellingen
-   Vertrouwde uitgevers
-   Geavanceerde
-   Updates
-   Logboekregistratie

## <a name="update-server"></a>Server bijwerken
Moet u de Updates Publisher werken met updateserver zoals Windows Server Update Services (WSUS) voordat u kunt configureren [updates publiceren](/sccm/sum/tools/manage-updates-with-updates-publisher#publish-updates-and-bundles). Dit omvat opgeven van de server, methoden om verbinding met die server wanneer het zich op afstand vanuit de console en een certificaat wilt gebruiken om digitaal te ondertekenen-updates te publiceren.

-   **Configureer een updateserver**. Wanneer u een updateserver configureert, selecteert u de site op het hoogste WSUS-server (updateserver) in uw Configuration Manager-hiërarchie zodat alle onderliggende sites hebben toegang tot de updates die u publiceert.

  Als uw updateserver externe van uw server Updates Publisher is, geeft u de volledig gekwalificeerde domeinnaam (FQDN) van de server, en als u verbinding met SSL maken. Wanneer u verbinding met SSL maakt, verandert de standaardpoort 8530 in 8531. Zorg ervoor dat de poort die u instelt overeenkomt met wat wordt gebruikt door de updateserver.

    > [!TIP]  
    > Als een server niet is geconfigureerd, kunt u nog steeds Updates Publisher gebruiken om software-updates.

-   **Het handtekeningcertificaat configureren**. U moet configureren en verbinding maken met een server bijwerken voordat u het handtekeningcertificaat kunt configureren.

    Het handtekeningcertificaat updates Publisher gebruikt voor het ondertekenen van de software-updates die zijn gepubliceerd naar de updateserver. Publicatie mislukt als het digitale certificaat is niet beschikbaar in het certificaatarchief van de update-server of de computer waarop Updates Publisher wordt uitgevoerd.

    Zie voor meer informatie over het toevoegen van het certificaat in het certificaatarchief [certificaten en beveiliging voor Updates Publisher](/sccm/sum/tools/updates-publisher-security).

    Als een digitaal certificaat niet automatisch wordt gedetecteerd voor de update-server, een van de volgende opties kiezen:

    -   **Blader**: Bladeren is alleen beschikbaar wanneer de update-server is geïnstalleerd op de server waarop u de console uitvoert. Nadat u een certificaat selecteren moet u **maken** dat certificaat toevoegen aan de WSUS-certificaatarchief op de updateserver. Moet u de **.pfx** Bestandswachtwoord voor de certificaten die u door deze methode selecteert.

    -   **Maken:** Gebruik deze optie om een nieuw certificaat maken. Hiermee wordt het certificaat ook toegevoegd aan de WSUS-certificaatarchief op de updateserver.

    **Als u uw eigen handtekeningcertificaat maakt**, configureert u het volgende:

    -   Schakel de **persoonlijke sleutel exporteerbaar** optie.

    -   Stel **sleutelgebruik** aan digitale handtekening.

    -   Stel **minimale sleutelgrootte** op een waarde die gelijk is aan of groter is dan 2048 bits.

    Gebruik de **verwijderen** optie voor het verwijderen van een certificaat uit het certificaatarchief van WSUS. Deze optie is beschikbaar wanneer de updateserver is lokaal op de Updates Publisher-console die u gebruikt, of wanneer u gebruikt **SSL** verbinding maken met een externe update-server.

## <a name="configmgr-server"></a>Configuration Manager-Server
Gebruik deze opties wanneer u Configuration Manager met Updates Publisher gebruikt.

-   **Geef de Configuration Manager-server:** Nadat u ondersteuning voor Configuration Manager hebt ingeschakeld, geef de locatie van de bovenste siteserver van Configuration Manager-hiërarchie. Als deze server extern van de installatie van Updates Publisher is, geeft u de FQDN-naam van de siteserver. Kies **testverbinding** om te controleren of u verbinding kunt maken met de siteserver.

-   **Drempels configureren:** Drempelwaarden worden gebruikt wanneer u updates met een publicatietype van automatische publiceert. De drempelwaarden te bepalen wanneer de volledige inhoud voor een update in plaats van alleen de metagegevens wordt gepubliceerd. Zie voor meer meer publicatietypen [updates toewijzen aan een publicatie](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)

    U kunt een of beide van de volgende drempelwaarden:

    -   **Client-drempelwaarde voor aantal aangevraagd:** Hiermee definieert u hoeveel clients moeten een update aanvragen voordat de volledige set van inhoud voor deze update automatisch van Updates Publisher publiceren kan. Totdat het opgegeven aantal clients de update aanvraagt, wordt alleen de metagegevens van de updates gepubliceerd.

    -   **Pakket bron drempelwaarde voor databasegrootte (MB):** Dit voorkomt dat automatische publicatie van updates die groter is dan de grootte die u opgeeft. Als de grootte van de updates deze waarde overschrijdt, wordt alleen de metagegevens is gepubliceerd. Updates die kleiner is dan de opgegeven grootte hun volledige inhoud die wordt gepubliceerd hebben kan.

## <a name="proxy-settings"></a>Proxy-instellingen
Updates Publisher gebruikt de proxy-instellingen wanneer u software catalogussen vanaf Internet importeren of updates op Internet publiceren.

-   De FQDN of IP-adres van een proxyserver opgeven. IPv4 en IPv6 worden ondersteund.

-   Als de proxyserver verificatie van gebruikers voor toegang tot Internet, moet u de Windows-naam opgeven. Een universele principle name (UPN) wordt niet ondersteund.

## <a name="trusted-publishers"></a>Vertrouwde uitgevers
Als u een update-catalogus, de bron van die catalogus (op basis van het certificaat), importeert wordt toegevoegd als een vertrouwde uitgever. Wanneer u een update publiceert, wordt de bron van het certificaat updates op deze manier toegevoegd als een vertrouwde uitgever.

U kunt details van certificaat voor elke uitgever weergeven en verwijderen van een uitgever uit de lijst met vertrouwde uitgevers.

Inhoud van uitgevers die geen vertrouwde kan toebrengen clientcomputers wanneer de client naar updates zoekt. U moet accepteren alleen inhoud van uitgevers die u vertrouwt.

## <a name="advanced"></a>Geavanceerde
Geavanceerde opties omvatten het volgende:

-   **Locatie van de opslagplaats:** Weergeven en wijzigen van de locatie van het databasebestand **scupdb.sdf**. Dit bestand is de opslagplaats voor Updates Publisher.

-   **Tijdstempel:** Wanneer ingeschakeld, is een tijdstempel toegevoegd aan updates u zich aanmeldt, waarmee wordt aangegeven wanneer het is ondertekend. Een update die is ondertekend, terwijl een certificaat geldig is kan worden gebruikt na het verstrijken van dat certificaat voor ondertekening. Standaard kunnen niet software-updates worden geïmplementeerd nadat het certificaat voor ondertekening is verlopen.

-   **Controleren op updates voor geabonneerde catalogussen:** Elke keer Updates Publisher wordt gestart, kunnen automatisch wordt gecontroleerd op updates voor catalogussen waarop u bent geabonneerd. Wanneer een catalogusupdate is gevonden, details zijn beschikbaar als **recente waarschuwingen** in de **overzicht** venster van de **werkruimte Updates**.

-   **Intrekken van certificaten:** Selecteer deze optie om in te schakelen intrekkingscontroles certificaat.

-   **Publicatie van de lokale bron:** Updates Publisher kunt een lokale kopie van een update die u publiceren wilt voordat deze update downloaden vanaf Internet. De locatie moet een map op de computer waarop Updates Publisher wordt uitgevoerd. Deze locatie is standaard **mijn Documents\LocalSourcePublishing.** Gebruik deze optie als u eerder hebt gedownload van een of meer updates of aangebrachte wijzigingen in een update die u wilt implementeren.

-   **Wizard Software-Updates opschonen:** Start de wizard updates opruimen. De wizard verloopt updates die op de updateserver maar niet in de opslagplaats voor Updates Publisher. Zie [zonder updates verlopen](#expire-unreferenced-software-updates) voor meer informatie.

## <a name="updates"></a>Updates
 Updates Publisher kunt automatisch controleren op nieuwe updates elke keer dat deze wordt geopend. U kunt ook kiezen voor het ontvangen van de preview-versies van Updates Publisher.

Handmatig controleren op updates in de Updates Publisher-console klikt u op op ![eigenschappen](media/properties2.png)  
openen van de **eigenschappen van de Updates Publisher**, en kies vervolgens **controleren op updates**.

Nadat de Updates Publisher vindt een nieuwe update, geeft de **bijwerken beschikbaar** venster en vervolgens kunt u het te installeren. Als u wilt dat de update niet geïnstalleerd, wordt deze de volgende keer dat u de console opent aangeboden.

## <a name="logging"></a>Logboekregistratie
Updates Publisher logboeken basisinformatie over Updates Publisher  **&lt;* pad*&gt;\Windows\Temp\UpdatesPublisher.log**.

Gebruik Kladblok of **CMTrace** om het logboek weer te geven. CMTrace wordt het hulpprogramma Configuration Manager log-bestand en kunt u vinden in de **\SMSSetup\Tools** map van de Configuration Manager-bronmedia.

U kunt de grootte van het logboek en de mate van detail wijzigen.

Wanneer u database logboekregistratie inschakelt, wordt informatie over de query's die worden uitgevoerd voor de database Updates Publisher zijn opgenomen. Gebruik van databaselogboekregistratie kan leiden tot verminderde prestaties van de computer Updates Publisher.

U kunt het logboekbestand in de console op op ![eigenschappen](media/properties2.png) openen de **eigenschappen van de Updates Publisher**, en kies vervolgens **logboekbestand weergeven**.

## <a name="expire-unreferenced-software-updates"></a>Niet-gebruikte software-updates verlopen
U kunt uitvoeren de **opschonen-Wizard voor Software-Update** verlopen updates die op uw server bijwerken, maar niet in de opslagplaats voor Updates Publisher. Deze Configuration Manager die deze updates uit alle toekomstige implementaties verwijdert op de hoogte.

De handeling verloopt een update kan niet ongedaan worden gemaakt. Deze taak alleen uitvoeren als u zeker weet dat de software-updates die u selecteert niet langer voor uw organisatie vereist zijn.

### <a name="to-remove-expired-software-updates"></a>Verlopen software-updates verwijderen
1.  Klik in de Updates Publisher-console op ![eigenschappen](media/properties2.png) openen de **eigenschappen van de Updates Publisher**, en kies vervolgens **opties**.

2.  Kies **Geavanceerd**, en klik vervolgens onder **schone Wizard voor de Software-Update,** kiezen **Start**.

3.  Selecteer de software-updates die u wilt laten verlopen, en kies vervolgens **volgende**.

4.  Bekijk uw selecties hebt gekozen **volgende** te accepteren van de selecties en deze updates te laten verlopen.

5.  Nadat de wizard is voltooid, kiest u **sluiten** om de wizard te voltooien.
