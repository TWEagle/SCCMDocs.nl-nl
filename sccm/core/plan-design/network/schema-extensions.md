---
title: Schema-uitbreidingen | Microsoft-documenten
description: Breid het Active Directory-schema voor ondersteuning van System Center Configuration Manager.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95c13c00-909f-4fbb-bbaa-1eba9d54d8c5
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7479e54b5db2eff893bf9fbaf52c104836cda519
ms.openlocfilehash: 5b5540c35c02df6e3d06e4aa9269b8da3238233e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="schema-extensions-for-system-center-configuration-manager"></a>Schema-extensies voor System Center Configuration

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt het Active Directory-schema voor ondersteuning van Configuration Manager uitbreiden. Dit bewerkt Active Directory-schema van een forest als een nieuwe-container en verschillende kenmerken die gebruikmaken van Configuration Manager-sites sleutel om informatie te publiceren in Active Directory waar clients kunnen veilig worden gebruikt wilt toevoegen. Deze informatie kunt vereenvoudigen de implementatie en configuratie van clients voor clients en helpt bij het zoeken naar sitebronnen zoals servers met geïmplementeerde inhoud of die andere services aan clients leveren.  

-   Het is verstandig om het Active Directory-schema uitbreiden, maar het is niet vereist.  

Voordat u het [Active Directory-schema uitbreidt](https://msdnstage.redmond.corp.microsoft.com/en-US/library/mt345589\(TechNet.10\).aspx), dient u bekend te zijn met Active Directory Domain Services en te weten hoe u [het Active Directory-schema wijzigt](https://technet.microsoft.com/library/cc759402\(v=ws.10\).aspx).  

## <a name="considerations-for-extending-the-active-directory-schema-for-configuration-manager"></a>Overwegingen voor uitbreiding van het Active Directory-schema voor Configuration Manager  

-   De Active Directory-schema-uitbreidingen voor System Center Configuration Manager zijn ongewijzigd voor degene die Configuration Manager 2007 en Configuration Manager 2012 gebruiken. Als u het schema al eens hebt uitgebreid voor een van de versies, hoeft u het schema niet nogmaals uit te breiden.  

-   Uitbreiding van het schema is een actie hele forest, eenmalige, niet ongedaan worden gemaakt.  

-   Alleen een gebruiker die lid zijn van de groep Schema-Administrators of aan wie heeft voldoende machtigingen zijn gedelegeerd om te wijzigen van het schema kan het schema uitbreiden.  

-   Hoewel u het schema voordat uitbreiden kunt of nadat u het installatieprogramma van Configuration Manager uitvoert, het een goed idee is om het schema uitbreidt voordat u begint met het configureren van uw sites en hiërarchie-instellingen. Zodoende kunt u veel van de latere configuratiestappen vereenvoudigen.  

-   Nadat u het schema uitbreidt, worden de globale catalogus van Active Directory wordt gerepliceerd in het hele forest. Plan daarom het schema uitbreiden wanneer andere processen die afhankelijk zijn van het netwerk geen belemmering voor het replicatieverkeer vormt wordt:  

    -   In Windows 2000-forests veroorzaakt uitbreiding van het schema een volledige synchronisatie van de hele globale catalogus.  

    -   Vanaf Windows 2003-forests worden alleen de nieuw toegevoegde kenmerken gerepliceerd.  

**Apparaten en clients die geen Active Directory-schema gebruiken:**  

-   Mobiele apparaten die worden beheerd door de Exchange Server-connector  

-   De client voor Mac-computers  

-   De client voor Linux- en UNIX-servers  

-   Mobiele apparaten die zijn ingeschreven door Configuration Manager  

-   Mobiele apparaten die zijn geregistreerd door Microsoft Intune  

-   Verouderde clients van mobiele apparaten  

-   Windows-clients die zijn geconfigureerd voor clientbeheer uitsluitend op Internet  

-   Windows-clients die worden gedetecteerd door Configuration Manager op het Internet  

## <a name="capabilities-that-benefit-from-extending-the-schema"></a>Mogelijkheden die profiteren van de uitbreiding van het schema  
**Client-computer clientinstallatie en sitetoewijzing** -wanneer een Windows-computer een nieuwe client installeert, de client zoekt naar Active Directory Domain Services naar installatie-eigenschappen.  

-   **Tijdelijke oplossingen:** Als u het schema niet uitbreidt, kunt u een van de volgende opties om op te geven informatie over de configuratie die moeten worden geïnstalleerd op computers gebruiken:  

    -   **Gebruik client-pushinstallatie**. Voordat u een installatiemethode voor clients gebruiken, zorg ervoor dat alle vereisten wordt voldaan. Zie voor meer informatie de sectie 'Afhankelijkheden bij installatiemethoden' in [vereisten voor de implementatie van clients op Windows-computers](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers).  

    -   **Installeer clients handmatig** en geef eigenschappen voor de installatie met behulp van opdrachtregeleigenschappen van CCMSetup-installatie. Dit moet het volgende omvatten:  

        -   Geef een beheerpunt of bronpad van waaruit de computer de installatiebestanden downloaden kan met behulp van de CCMSetup-eigenschap **/mp: =&lt;beheerpunt naam computernaam\>**  of **/source:&lt;pad naar de clientbronbestanden\> ** op de CCMSetup-opdrachtregel tijdens de clientinstallatie.  

        -   Geef een lijst met eerste beheerpunten op de client moet gebruiken, zodat deze kan aan de site toewijzen en download vervolgens clientbeleid en site-instellingen. Gebruik hiervoor de Client.msi- eigenschap SMSMP van CCMSetup.  

    -   **Publiceer het beheerpunt in DNS of WINS** en configureer clients voor het gebruik van deze servicelocatiemethode.  

**Poortconfiguratie voor de communicatie van client-naar-server** - wanneer een client wordt geïnstalleerd, wordt deze geconfigureerd met poortinformatie opgeslagen in Active Directory. Als u later de communicatiepoort van client-naar-server voor een site wijzigt, kan een client deze nieuwe poortinstelling krijgen van Active Directory Domain Services.  

-   **Tijdelijke oplossingen:** Als u het schema niet uitbreidt, kunt u een van de volgende opties om nieuwe poortconfiguraties voor bestaande clients gebruiken:  

    -   **Clients opnieuw installeren** met behulp van de opties die door de nieuwe poort configureren.  

    -   **Implementeer op clients een aangepast script om de poortinformatie bij te werken**. Als clients met een site wegens een poortwijziging communiceren kunnen, kunt u Configuration Manager niet gebruiken voor dit script wilt implementeren. U kunt bijvoorbeeld een groepsbeleid gebruiken.  

**Implementatiescenario's inhoud** - wanneer u inhoud op een site maakt en vervolgens implementeren dat inhoud naar een andere site in de hiërarchie, de ontvangende site moet de handtekening van de ondertekende inhoudsgegevens kunnen verifiëren. Hiervoor is toegang vereist tot de openbare sleutel van de bronsite waar u deze gegevens maakt. Wanneer u het Active Directory-schema voor Configuration Manager uitbreidt, is de openbare sleutel van een site beschikbaar voor alle sites in de hiërarchie.  

-   **Tijdelijke oplossing:** Als u het schema niet uitbreidt, gebruikt u de hierarchy maintenance tool **preinst.exe**, voor het uitwisselen van de informatie over beveiligingssleutel tussen sites.  

     Bijvoorbeeld, als u inhoud maakt op een primaire site en die inhoud implementeren voor een secundaire site onder een andere primaire site plant, moet ofwel breidt u het Active Directory-schema, zodat de secundaire site ophalen van de primaire bronsite van de openbare sleutel, of u preinst.exe gebruiken om sleutels tussen de twee sites rechtstreeks te delen.  

## <a name="active-directory-attributes-and-classes"></a>Active Directory-kenmerken en klassen  
Wanneer u het schema voor System Center Configuration Manager uitbreidt, worden de volgende klassen en kenmerken toegevoegd aan het schema en beschikbaar zijn voor alle Configuration Manager-sites in die Active Directory-forest.  

-   Kenmerken:  

    -   CN = mS-SMS-toewijzing-Site-Code  

    -   CN = mS-SMS-mogelijkheden  

    -   CN = MS-SMS-standaard-MP  

    -   CN = mS-SMS---Apparaatbeheerpunt  

    -   CN = mS-SMS--status  

    -   CN = MS-SMS-MP-adres  

    -   CN = MS-SMS-MP-naam  

    -   CN = MS-SMS-varieerde-IP-hoog  

    -   CN = MS-SMS-varieerde-IP-laag  

    -   CN = MS-SMS-Roaming-grenzen  
        op  

    -   CN = MS-SMS-Site-grenzen  

    -   CN = MS-SMS-Site-Code  

    -   CN = mS-SMS-bron-Forest  

    -   CN = mS-SMS-versie  

-   Klassen:  

    -   CN = MS-SMS-Management-punt  

    -   CN = MS-SMS-Roaming-grens-bereik  

    -   CN = MS-SMS-Server-Locator-punt  

    -   CN = MS-SMS-Site  

> [!NOTE]  

>  De schemauitbreidingen bevatten mogelijk kenmerken en klassen die zijn overgebracht uit eerdere versies van het product maar niet gebruikt door System Center Configuration Manager. Bijvoorbeeld:  

>   
>  -   Kenmerk: cn = MS-SMS-Site-grenzen  
> -   Klasse: cn = MS-SMS-Server-Locator-punt  

U kunt ervoor te zorgen de voorgaande lijsten huidige via de **ConfigMgr_ad_schema. LDF** -bestand uit de **\SMSSETUP\BIN\x64** map van de System Center Configuration Manager-installatiemedia.  

