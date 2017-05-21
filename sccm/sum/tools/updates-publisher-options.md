---
title: Configureer opties | Microsoft-documenten
description: Opties voor het gebruik van System Center Updates Publisher configureren
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e620080-5400-45bb-87c2-fbdbc8aeacac
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: b66ed0a5e1c87d8c82853da86e3d55b0e2c043bb
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="configure-options-for-updates-publisher"></a>Opties voor Updates Publisher configureren

*Van toepassing op: System Center Updates Publisher*

Bekijk en configureer de opties en daaraan gerelateerde instellingen die van invloed op de Updates Publisher.

Voor toegang tot de Updates Publisher-opties in de linkerbovenhoek van de console, klikt u op de **Updates Publisher** **eigenschappen** tabblad en kies vervolgens **opties**.

![Opties](media/properties1.png)   


Opties worden onderverdeeld in het volgende:

-   Server bijwerken
-   Configuration Manager-Server
-   Proxy-instellingen
-   Vertrouwde uitgevers
-   Geavanceerde
-   Updates
-   Logboekregistratie

## <a name="update-server"></a>Server bijwerken
U moet de Updates Publisher werken met updateserver zoals Windows Server Update Services (WSUS) voordat u kunt configureren [updates publiceren](/sccm/sum/tools/manage-updates-with-updates-publisher#publish-updates-and-bundles). Dit omvat opgeven van de server, methoden voor verbinding met die server wanneer het zich op afstand vanaf de console en een certificaat wilt gebruiken om digitaal te ondertekenen u werkt publiceert.

-   **Configureer een updateserver**. Als u een updateserver configureert, selecteert u de site op het hoogste WSUS-server (updateserver) in uw Configuration Manager-hiërarchie zodat alle onderliggende sites hebben toegang tot de updates die u publiceert.

  Als de updateserver extern van uw server Updates Publisher is, geef de volledig gekwalificeerde domeinnaam (FQDN) van de server, en als u verbinding met SSL maken. Als u verbinding met SSL maakt, verandert de standaardpoort 8530 in 8531. Zorg ervoor dat de poort die u instelt komt overeen met wat wordt gebruikt door de updateserver.

    > [!TIP]  
    > Als een update-server niet is geconfigureerd, kunt u nog steeds Updates Publisher gebruiken voor het ontwerpen van software-updates.

-   **Configureren van het handtekeningcertificaat**. U moet configureren en verbinding maken met een server bijwerken voordat u het handtekeningcertificaat kunt configureren.

    Handtekeningcertificaat van de updates Publisher gebruikt voor het ondertekenen van de software-updates die worden gepubliceerd naar de updateserver. Publicatie mislukt als het digitale certificaat is niet beschikbaar in het certificaatarchief van de update-server of de computer waarop Updates Publisher wordt uitgevoerd.

    Zie voor meer informatie over het toevoegen van het certificaat in het certificaatarchief [certificaten en beveiliging voor Updates Publisher](/sccm/sum/tools/updates-publisher-security).

    Als er een digitaal certificaat wordt niet automatisch gedetecteerd voor de update-server, kies een van de volgende opties:

    -   **Bladeren**: Bladeren is alleen beschikbaar wanneer de update-server is geïnstalleerd op de server waarop u de console uitvoert. Nadat u een certificaat selecteren moet u **maken** dat certificaat toevoegen aan de WSUS-certificaatarchief op de updateserver. Moet u de **pfx** Bestandswachtwoord voor certificaten die u door deze methode selecteert.

    -   **Maken:** Gebruik deze optie als u een nieuw certificaat maken. Het certificaat wordt ook toegevoegd aan de WSUS-certificaatarchief op de updateserver.

    **Als u uw eigen handtekeningcertificaat**, configureer dan het volgende:

    -   Schakel de **persoonlijke sleutel exporteerbaar** optie.

    -   Stel **sleutelgebruik** aan digitale handtekening.

    -   Stel **minimale sleutelgrootte** op een waarde die gelijk is aan of groter is dan 2048 bits.

    Gebruik de **verwijderen** optie voor het verwijderen van een certificaat uit het certificaatarchief van WSUS. Deze optie is beschikbaar wanneer de updateserver is lokaal op de Updates Publisher-console die u gebruikt, of wanneer u gebruikt **SSL** verbinding maken met een externe update-server.

## <a name="configmgr-server"></a>Configuration Manager-Server
Gebruik deze opties wanneer u Configuration Manager met Updates Publisher.

-   **Geef de Configuration Manager-server:** Nadat u ondersteuning voor Configuration Manager inschakelt, geef de locatie van de site op hoogste niveau van uw hiërarchie Configuration Manager-server. Als u die server extern is van de installatie van de Updates Publisher, geef de FQDN van de siteserver. Kies **testverbinding** zodat u kunt verbinding maken met de siteserver.

-   **Drempels configureren:** Drempelwaarden worden gebruikt wanneer u met een publicatietype van automatische updates publiceren. De drempelwaarden te bepalen wanneer de volledige inhoud voor een update in plaats van alleen de metagegevens wordt gepubliceerd. Zie voor meer informatie over meer publicatietypen, [updates toewijzen aan een publicatie](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)

    U kunt een of beide van de volgende drempelwaarden:

    -   **Drempelwaarde voor aantal client aangevraagd:** Hiermee definieert u hoeveel clients een update moeten aanvragen voordat de Updates Publisher publiceert u de volledige set van inhoud voor update automatisch. Totdat het opgegeven aantal clients de update vragen, wordt alleen de metagegevens van de updates gepubliceerd.

    -   **Pakket bron drempelwaarde voor databasegrootte (MB):** Dit voorkomt dat automatisch uitgeven van updates die groter is dan de grootte die u opgeeft. Als de grootte van de updates deze waarde overschrijdt, worden alleen de metagegevens is gepubliceerd. Updates die kleiner zijn dan de opgegeven grootte hun volledige inhoud die wordt gepubliceerd hebben kan.

## <a name="proxy-settings"></a>Proxy-instellingen
Updates Publisher gebruikt de proxy-instellingen wanneer u software catalogussen van het Internet importeren of updates naar het Internet publiceren.

-   Geef de FQDN-naam of IP-adres van een proxyserver. IPv4- als IPv6 worden ondersteund.

-   Als de proxyserver verifieert gebruikers voor toegang tot het Internet te gebruiken, moet u de Windows-naam opgeven. Een universele principe name (UPN) wordt niet ondersteund.

## <a name="trusted-publishers"></a>Vertrouwde uitgevers
Als u een update-catalogus, de bron van die catalogus (op basis van het certificaat) importeert wordt toegevoegd als een vertrouwde uitgever. Wanneer u een update publiceert, wordt de bron van het certificaat van de updates op deze manier toegevoegd als een vertrouwde uitgever.

U kunt zien certificaatdetails voor elke publisher en een publisher verwijderen uit de lijst met vertrouwde uitgevers.

Inhoud van uitgevers die niet worden vertrouwd kan toebrengen clientcomputers wanneer de client naar updates scant. U moet accepteren alleen inhoud van uitgevers die u vertrouwt.

## <a name="advanced"></a>Geavanceerde
Geavanceerde opties bevatten het volgende:

-   **Locatie van de opslagplaats:** Weergeven en wijzigen van de locatie van het databasebestand **scupdb.sdf**. Dit bestand is de opslagplaats voor Updates Publisher.

-   **Tijdstempel:** Wanneer dit is ingeschakeld, is een tijdstempel toegevoegd aan updates u zich waarmee wordt aangeduid als het is ondertekend. Een update die is ondertekend, terwijl een certificaat geldig is kan worden gebruikt als dat certificaat voor ondertekening is verlopen. Standaard kunnen niet na het verstrijken van hun handtekeningcertificaat software-updates worden geïmplementeerd.

-   **Controleren op updates voor geabonneerde catalogussen worden geïmporteerd:** Elke keer Updates Publisher wordt gestart, kan dit automatisch op updates controleren aan de catalogus waarop u bent geabonneerd. Wanneer een catalogusupdate is gevonden, worden details gegeven als **recente waarschuwingen** in de **overzicht** venster van de **Updates werkruimte**.

-   **Intrekken van certificaten:** Selecteer deze optie om in te schakelen certificaat intrekkingscontroles.

-   **Lokale bron publiceren:** Updates Publisher kunt een lokale kopie van een update die u publiceren wilt voordat de update downloaden van Internet gebruiken. De locatie moet een map op de computer waarop Updates Publisher wordt uitgevoerd. Deze locatie is standaard **mijn Documents\LocalSourcePublishing.** Gebruik deze optie als u een of meer updates al eerder hebt gedownload, of aangebrachte wijzigingen in een update die u wilt implementeren.

-   **Wizard Software-Updates opschonen:** Start de wizard updates opruimen. De wizard verloopt updates die uitgevoerd op de updateserver, maar geen deel uitmaken van de Updates Publisher-opslagplaats worden. Zie [zonder verwijzing updates verlopen](#expire-unreferenced-software-updates) voor meer informatie.

## <a name="updates"></a>Updates
 Updates Publisher kan automatisch controleren op nieuwe updates telkens wanneer die deze wordt geopend. U kunt ook kiezen voor het ontvangen van preview builds van Updates Publisher.

Naar handmatig controleren op updates in de Updates Publisher-console klikt u op ![eigenschappen](media/properties2.png)  
openen van de **Updates Publisher eigenschappen**, en kies vervolgens **controleren op updates**.

Nadat Updates Publisher vindt een nieuwe update, geeft de **bijwerken beschikbaar** venster en vervolgens kunt u deze toepassing te installeren. Als u de update niet installeren, wordt de volgende keer dat de console geopend die worden aangeboden.

## <a name="logging"></a>Logboekregistratie
Updates Publisher registreert basisinformatie over Updates Publisher  **&lt;* pad*&gt;\Windows\Temp\UpdatesPublisher.log**.

Gebruik Kladblok of **CMTrace** om het logboek weer te geven. CMTrace wordt de Configuration Manager-logboekbestandsprogramma en kunt u vinden in de **\SMSSetup\Tools** map van de Configuration Manager-bronmedia.

U kunt de grootte van het logboek en het detailniveau wijzigen.

Wanneer u een database logboekregistratie inschakelt, wordt informatie over de query's die worden uitgevoerd voor de database Updates Publisher zijn opgenomen. Gebruik van de databaselogboekregistratie kan leiden tot verminderde prestaties van de computer met Updates Publisher.

Als u wilt weergeven in het logboekbestand, in de console klikt u op ![eigenschappen](media/properties2.png) openen de **Updates Publisher eigenschappen**, en kies vervolgens **logboekbestand weergeven**.

## <a name="expire-unreferenced-software-updates"></a>Niet-gebruikte software-updates verlopen
U kunt uitvoeren de **opschonen-Wizard voor Software-Update** updates die op uw server bijwerken, maar niet in de opslagplaats Updates Publisher zijn verlopen. Dit verwittigt Configuration Manager die deze updates uit alle toekomstige implementaties verwijdert.

De handeling verlopen van een update kan niet ongedaan worden gemaakt. Deze taak alleen uitvoeren wanneer u zeker weet dat de software-updates die u selecteert niet langer voor uw organisatie vereist zijn.

### <a name="to-remove-expired-software-updates"></a>Verlopen software-updates verwijderen
1.  Klik in de console Updates Publisher op ![eigenschappen](media/properties2.png) openen de **Updates Publisher eigenschappen**, en kies vervolgens **opties**.

2.  Kies **Geavanceerd**, en klik vervolgens onder **Wizard Software-Update schone** kiezen **Start**.

3.  Selecteer de software-updates die u wilt vervalt, en kies vervolgens **volgende**.

4.  Bekijk uw selecties hebt gekozen **volgende** naar de selecties accepteren en deze updates te laten verlopen.

5.  Nadat de wizard is voltooid, kiest u **sluiten** om de wizard te voltooien.

