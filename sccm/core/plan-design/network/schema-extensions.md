---
title: Schema-uitbreidingen | Microsoft Docs
description: Het Active Directory-schema ter ondersteuning van System Center Configuration Manager uitbreiden.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95c13c00-909f-4fbb-bbaa-1eba9d54d8c5
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
ms.openlocfilehash: 5ec1e9368e836382b143d7b2bf9d1a6a7bc2fa22
ms.sourcegitcommit: 96b79fa091f44e8e6ac5652f6cbbb4b873a8bad9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/09/2017
---
# <a name="schema-extensions-for-system-center-configuration-manager"></a>Schema-extensies voor System Center Configuration

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de Active Directory-schema ter ondersteuning van Configuration Manager uitbreiden. Hiermee bewerkt u het Active Directory-schema van het forest als een nieuwe container en verschillende kenmerken die Configuration Manager-sites gebruiken voor het publiceren van belangrijke informatie in Active Directory waar clients kunnen veilig worden gebruikt wilt toevoegen. Deze informatie vereenvoudigt de implementatie en configuratie van clients en helpt clients sitebronnen vinden, zoals servers met geïmplementeerde inhoud of die verschillende services aan clients leveren.  

-   Is het een goed idee om uit te breiden Active Directory-schema, maar dit is niet vereist.  

Voordat u het [Active Directory-schema uitbreidt](https://docs.microsoft.com/en-us/sccm/core/plan-design/network/extend-the-active-directory-schema), dient u bekend te zijn met Active Directory Domain Services en te weten hoe u [het Active Directory-schema wijzigt](https://technet.microsoft.com/library/cc759402\(v=ws.10\).aspx).  

## <a name="considerations-for-extending-the-active-directory-schema-for-configuration-manager"></a>Overwegingen voor het uitbreiden van het Active Directory-schema voor Configuration Manager  

-   De Active Directory-schema-uitbreidingen voor System Center Configuration Manager zijn ongewijzigd ten opzichte van die Configuration Manager 2007 en Configuration Manager 2012 gebruiken. Als u het schema al eens hebt uitgebreid voor een van de versies, hoeft u het schema niet nogmaals uit te breiden.  

-   Het schema uitbreiden is een hele forest eenmalige, onomkeerbare actie.  

-   Alleen een gebruiker die lid zijn van de groep Schema-Administrators of aan wie voldoende machtigingen ontvangen voor het wijzigen van het schema zijn kunt het schema uitbreiden.  

-   Hoewel u het schema voordat uitbreiden kunt of nadat u de installatie van Configuration Manager uitvoert, is het een goed idee om het schema uitbreiden voordat u uw sites en hiërarchie-instellingen configureren. Zodoende kunt u veel van de latere configuratiestappen vereenvoudigen.  

-   Nadat u het schema uitbreidt, wordt de globale catalogus van Active Directory in het hele forest gerepliceerd. Plan daarom het schema uitbreiden wanneer het replicatieverkeer wordt geen nadelige invloed op het andere processen die afhankelijk zijn van het netwerk:  

    -   In Windows 2000-forests veroorzaakt uitbreiding van het schema een volledige synchronisatie van de hele globale catalogus.  

    -   Vanaf Windows 2003-forests worden alleen de nieuw toegevoegde kenmerken gerepliceerd.  

**Apparaten en clients die geen van Active Directory-schema gebruikmaken:**  

-   Mobiele apparaten die worden beheerd door de Exchange Server-connector  

-   De client voor Mac-computers  

-   De client voor Linux- en UNIX-servers  

-   Mobiele apparaten die zijn ingeschreven door Configuration Manager  

-   Mobiele apparaten die zijn geregistreerd door Microsoft Intune  

-   Verouderde clients van mobiele apparaten  

-   Windows-clients die zijn geconfigureerd voor clientbeheer alleen op Internet  

-   Windows-clients die worden gedetecteerd door Configuration Manager op het Internet  

## <a name="capabilities-that-benefit-from-extending-the-schema"></a>Mogelijkheden die profiteren van de uitbreiding van het schema  
**Client-computer installatie en sitetoewijzing** -wanneer een Windows-computer een nieuwe client installeert, zoekt de client in Active Directory Domain Services naar installatie-eigenschappen.  

-   **Tijdelijke oplossingen:** Als u het schema niet uitbreidt, kunt u een van de volgende opties om configuratiedetails die moeten worden geïnstalleerd op computers gebruiken:  

    -   **Gebruik client-pushinstallatie**. Voordat u een clientinstallatiemethode gebruikt, zorg dat alle vereisten wordt voldaan. Zie voor meer informatie de sectie 'Afhankelijkheden bij installatiemethoden' in [vereisten voor het implementeren van clients op Windows-computers](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers).  

    -   **Installeer clients handmatig** en geef eigenschappen voor de installatie met behulp van opdrachtregeleigenschappen van CCMSetup-installatie. Dit moet het volgende omvatten:  

        -   Geef een management beheerpunt of bronpad pad op van waaruit de computer de installatiebestanden downloaden met behulp van de CCMSetup-eigenschap **/mp: =&lt;beheerpunt naam computernaam\>**  of **/source:&lt;pad naar de bronbestanden van de client\>**  op de CCMSetup-opdrachtregel tijdens de clientinstallatie.  

        -   Geef een lijst met eerste beheerpunten op de client zodat deze kan aan de site toewijzen en downloadt de client en site-instellingen gebruiken. Gebruik hiervoor de Client.msi- eigenschap SMSMP van CCMSetup.  

    -   **Publiceer het beheerpunt in DNS of WINS** en configureer clients voor het gebruik van deze servicelocatiemethode.  

**Poortconfiguratie voor de communicatie van client-naar-server** : wanneer een client wordt geïnstalleerd, wordt deze geconfigureerd met poortinformatie die is opgeslagen in Active Directory. Als u later de communicatiepoort van client-naar-server voor een site wijzigt, kan een client deze nieuwe poortinstelling verkrijgen van Active Directory Domain Services.  

-   **Tijdelijke oplossingen:** Als u het schema niet uitbreidt, gebruikt u een van de volgende opties voor een nieuwe poortconfiguraties met bestaande clients:  

    -   **Clients opnieuw installeren** met behulp van de opties die de nieuwe poort configureren.  

    -   **Implementeer op clients een aangepast script om de poortinformatie bij te werken**. Als clients met een site wegens de poortwijziging communiceren kunnen, kunt u Configuration Manager niet gebruiken voor het implementeren van dit script. U kunt bijvoorbeeld een groepsbeleid gebruiken.  

**Implementatiescenario's van inhoud** : wanneer u inhoud op een site maakt en implementeert u dat inhoud naar een andere site in de hiërarchie, de ontvangende site moet de handtekening van de ondertekende inhoudsgegevens kunnen verifiëren. Hiervoor is toegang vereist tot de openbare sleutel van de bronsite waar u deze gegevens maakt. Wanneer u het Active Directory-schema voor Configuration Manager uitbreidt, is de openbare sleutel van een site beschikbaar voor alle sites in de hiërarchie.  

-   **Tijdelijke oplossing:** Als u het schema niet uitbreidt, gebruikt u de hierarchy maintenance tool **preinst.exe**, voor het uitwisselen van gegevens van de beveiligde sleutel tussen sites.  

     Als u inhoud op een primaire site maken en implementeren van die inhoud naar een secundaire site onder een andere primaire site plant, moet u bijvoorbeeld ofwel Active Directory-schema voor de secundaire site de primaire bronsite van de openbare sleutel, of gebruik van preinst.exe voor sleutels tussen de twee sites rechtstreeks kunnen worden gedeeld, kunnen uitbreiden.  

## <a name="active-directory-attributes-and-classes"></a>Active Directory-kenmerken en klassen  
Wanneer u het schema voor System Center Configuration Manager uitbreidt, worden de volgende klassen en kenmerken toegevoegd aan het schema en beschikbaar zijn voor alle Configuration Manager-sites in die Active Directory-forest.  

-   Kenmerken:  

    -   CN = mS-SMS-toewijzing-Site-Code  

    -   CN = mS-SMS-mogelijkheden  

    -   CN = MS-SMS-standaard-MP  

    -   CN = mS-SMS-Device-Management-punt  

    -   CN = mS-SMS-Health-status  

    -   CN = MS-SMS-MP-adres  

    -   CN = MS-SMS-MP-Name  

    -   CN = MS-SMS-varieerde-IP-hoog  

    -   CN = MS-SMS-varieerde-IP-laag  

    -   CN = MS-SMS-Roaming-grenzen  
        op  

    -   CN = MS-SMS-Site-grenzen  

    -   CN = MS-SMS-Site-Code  

    -   CN = mS-SMS-bron-Forest  

    -   CN = SMS-mS-versie  

-   Klassen:  

    -   CN = MS-SMS-Management-punt  

    -   CN = MS-SMS-Roaming-grens-bereik  

    -   CN = MS-SMS-Server-Locator-punt  

    -   CN = MS-SMS-Site  

> [!NOTE]  

>  De schema-uitbreidingen mogelijk bevatten kenmerken en klassen die zijn overgebracht uit eerdere versies van het product maar niet gebruikt door System Center Configuration Manager. Bijvoorbeeld:  

>   
>  -   Kenmerk: cn = MS-SMS-Site-grenzen  
> -   Klasse: cn = MS-SMS-Server-Locator-punt  

U kunt controleren of de voorgaande lijsten actueel zijn door zijn de **ConfigMgr_ad_schema. LDF** bestand van de **\SMSSETUP\BIN\x64** map van de System Center Configuration Manager-installatiemedia.  
