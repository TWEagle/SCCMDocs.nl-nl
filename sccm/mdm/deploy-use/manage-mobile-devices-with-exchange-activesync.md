---
title: 'Beheer van mobiele apparaten '
titleSuffix: Configuration Manager
description: Mobiele apparaten beheren met behulp van de Exchange Server-connector in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: aba688d9-fd5b-4c42-8cb4-f7e1b161ef50
caps.latest.revision: "8"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: d8f3a963d0fccb3469e751e1ca3319368ae92506
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-mobile-devices-with-system-center-configuration-manager-and-exchange"></a>Mobiele apparaten beheren met System Center Configuration Manager en Exchange

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Exchange Server-connector gebruiken in System Center Configuration Manager als u wilt beheren van mobiele apparaten die verbinding met Exchange Server maken (lokaal of online) via het Microsoft Exchange ActiveSync-protocol en u ze niet kunt registreren met Configuration Manager. U kunt Exchange functies voor mobiele apparaten, zoals het wissen van het externe apparaat en instellingen voor meerdere Exchange-servers, vanuit de Configuration Manager-console configureren.  

 ![Configuration Manager &#45; met &#45; exchange](../../mdm/deploy-use/media/configmgr-with-exchange.png "Configuration Manager met exchange")  

 Wanneer u mobiele apparaten beheren met behulp van de Exchange Server-connector, wordt dit Configuration Manager-client niet geïnstalleerd op de mobiele apparaten. Sommige beheerfuncties zijn daarom beperkt. U kunt bijvoorbeeld geen software installeren op deze apparaten of configuratie-items gebruiken om deze apparaten te configureren. Zie voor meer informatie over de verschillende beheermogelijkheden die u met Configuration Manager voor mobiele apparaten gebruiken kunt, [een oplossing voor Apparaatbeheer kiezen voor System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md).  

> [!IMPORTANT]  
>  Voordat u de Exchange Server-connector installeert, moet u nagaan of Configuration Manager ondersteunt de versie van Microsoft Exchange die u gebruikt. Zie voor meer informatie 'Exchange Server-connector' in [ondersteunde besturingssystemen voor sites en clients voor System Center Configuration Manager](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  

 Wanneer u de Exchange Server-connector gebruikt, kunnen de mobiele apparaten worden beheerd door de instellingen die u in Configuration Manager configureren in plaats van dat wordt beheerd door de standaardbeleidsregels voor Exchange ActiveSync-postvak. Definieer de instellingen die u wilt gebruiken in de volgende instellingen: **Algemene**, **wachtwoord**, **e-mailbeheer**, **beveiliging**, en **toepassing**. U kunt bijvoorbeeld in de groepsinstelling **Wachtwoord** configureren of mobiele apparaten een wachtwoord nodig hebben, de minimale wachtwoordlengte, wachtwoordcomplexiteit en of wachtwoordherstel is toegestaan.  

 Wanneer u ten minste één instelling in de groep configureert, wordt in Configuration Manager alle instellingen in de groep voor mobiele apparaten beheert. Als u geen instellingen in een groep configureert, blijft Exchange de mobiele apparaten voor die instellingen beheren. Al het beleid voor Exchange ActiveSync-postvakken dat wordt geconfigureerd op de Exchange Server en wordt toegewezen aan gebruikers is nog steeds van toepassing.  

 U kunt de Exchange Server-connector ook configureren om de toegangsregels voor Exchange te beheren en mobiele apparaten toe te staan, te blokkeren of in quarantaine te plaatsen. U kunt mobiele apparaten op afstand wissen via de Configuration Manager-console en gebruikers kunnen hun mobiele apparaten op afstand wissen via de Application Catalog.  

 Het mobiele apparaat van een gebruiker automatisch in de Toepassingscatalogus wordt weergegeven wanneer de Exchange Server-connector wordt beheerd en de Exchange-Server lokaal is. Wanneer u de Exchange Server-connector voor Microsoft Exchange Online configureert, moet u handmatig gebruikersapparaataffiniteit voor mobiele apparaten van de gebruiker worden weergegeven in de Application Catalog te configureren. Zie voor meer informatie over het handmatig configureren van affiniteit van gebruikersapparaat [gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

> [!TIP]  
>  Als u een mobiel apparaat beheert via de Exchange Server-connector en het mobiele apparaat wordt overgedragen aan een andere gebruiker, moet u het mobiele apparaat uit de Configuration Manager-console verwijderen voordat de nieuwe eigenaar van het mobiele apparaat, configureert u zijn of haar Exchange-account op dit mobiele apparaat overgedragen.  

## <a name="required-security-permissions"></a>Vereiste beveiligingsrechten  
 U moet beschikken over de volgende beveiligingsrechten om de Exchange Server-connector te configureren:  

-   Als u wilt toevoegen, wijzigen en verwijderen van de Exchange Server-connector: **Wijzig** machtiging voor de **Site** object.  

-   Instellingen voor mobiele apparaten configureren: **ModifyConnectorPolicy** machtiging voor de **Site** object.  

 De beveiligingsrol **Volledige beheerder** bevat de vereiste machtigingen om de Exchange Server-connector te configureren.  

 U moet over de volgende beveiligingsmachtigingen beschikken om mobiele apparaten te beheren:  

-   Wissen van een mobiel apparaat: **Bron verwijderen** voor de **verzameling** object.  

-   Een wisopdracht annuleren: **Wijzig bron** voor de **verzameling** object.  

-   Toestaan en blokkeren van mobiele apparaten: **Wijzig bron** voor de **verzameling** object.  

 De beveiligingsrol **Bewerkingenbeheerder** bevat de vereiste machtigingen om mobiele apparaten te beheren met de Exchange Server-connector.  

 Zie voor meer informatie over het configureren van beveiligingsmachtigingen [beheer op basis van rollen voor System Center Configuration Manager configureren](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="installing-and-configuring-an-exchange-server-connector"></a>Installeren en configureren van een Exchange Server-Connector  
 Gebruik de volgende procedure om een Exchange Server-connector te installeren en te configureren om mobiele apparaten te beheren. Configuration Manager ondersteunt slechts één connector binnen een Exchange-organisatie. Na voltooiing van deze stappen kunt u de mobiele apparaten volgen die door de connector worden gevonden en beheerd wanneer u de verzamelingen bekijkt die mobiele apparaten weergeven en door gebruik van de rapporten voor mobiele apparaten.  

> [!NOTE]  
>  Configuration Manager genereert namen voor de mobiele apparaten die worden gevonden in de indeling *gebruikersnaam*_*DeviceType*. Als een gebruiker meer dan één mobiel apparaat heeft van hetzelfde apparaattype heeft, wordt dezelfde naam voor deze mobiele apparaten in de Configuration Manager weergeeft in de console en in rapporten.  

#### <a name="to-install-and-configure-an-exchange-server-connector"></a>Installeren en configureren van een Exchange Server-connector  

1.  Besluit welk account u wilt verbinden met de Exchange Client Access-server om mobiele apparaten te beheren. Het account kan een computeraccount van de siteserver zijn of een Windows-gebruikersaccount. Configureer vervolgens dit account voor uitvoering van de volgende Exchange Server-cmdlets:  

    -   **Clear-ActiveSyncDevice**  

    -   **Get-ActiveSyncDevice**  

    -   **Get-ActiveSyncDeviceAccessRule**  

    -   **Get-ActiveSyncDeviceStatistics**  

    -   **Get-ActiveSyncMailboxPolicy**  

    -   **Get-ActiveSyncOrganizationSettings**  

    -   **Get-Exchange**  

    -   **Get-ontvanger**  

    -   **Set-ADServerSettings**  

    -   **Set-ActiveSyncDeviceAccessRule**  

    -   **Set-ActiveSyncMailboxPolicy**  

    -   **Set-CASMailbox**  

    -   **Nieuwe ActiveSyncDeviceAccessRule**  

    -   **Nieuwe ActiveSyncMailboxPolicy**  

    -   **Remove-ActiveSyncDevice**  

    > [!NOTE]  
    >  De volgende Exchange Server-beheerrollen bevatten deze cmdlets: Recipient Management, View-Only Organization Management en Serverbeheer. Zie [Understanding Management Role Groups (Uitleg van beheerrolgroepen)](http://go.microsoft.com/fwlink/p/?LinkId=212914)voor meer informatie over beheerrolgroepen in Microsoft Exchange Server 2010.  

    > [!TIP]  
    >  Als u de Exchange Server-connector probeert te installeren of te gebruiken zonder de vereiste cmdlets, ziet u de foutmelding `Invoking cmdlet <cmdlet> failed` in het EasDisc.log-bestand op de siteservercomputer.  

2.  Klik op **Beheer**in de Configuration Manager-console.  

3.  Vouw in de werkruimte **Beheer** **Hiërarchieconfiguratie**uit en klik vervolgens op **Exchange Server-connectors**.  

4.  Klik op **Exchange Server toevoegen** in het tabblad **Start** in de groep **Maken**.  

5.  Voltooi de wizard Exchange Server toevoegen:  

    -   Als u een lokaal Exchange Server-exemplaar gebruikt en een Client Access Server specificeert, kunt u een enkele server of een Client Access Server-matrix specificeren voor iedere Active Directory-site. Als de server of matrix offline is, probeert de Configuration Manager voor het detecteren van een Client Access Server te gebruiken. Als dat mislukt, valt Configuration Manager terug op het gebruik van een postvakserver verbinding te maken met een Client Access Server. Nieuwe pogingen worden geregistreerd als waarschuwingen in het EasDisc.log-bestand op de siteservercomputer. Bijvoorbeeld zoeken naar `Failed to open runspace for site <site_name>`.  

    -   Specificeer voor het Exchange Server Connector-account het account dat u hebt geconfigureerd in stap 1.  

    -   Als u ook mobiele apparaten registreert met behulp van Configuration Manager, schakelt u de optie **beheer op afstand mobiele apparaten** om ervoor te zorgen dat deze mobiele apparaten e-mails ontvangen van Exchange blijven nadat Configuration Manager ze heeft geregistreerd.  

    -   Op de **Account** pagina van de wizard kunt u het account dat wordt gebruikt voor het e-mailmeldingen te verzenden naar clients die zijn geblokkeerd door voorwaardelijke toegang van Configuration Manager configureren. Het account dat u opgeeft, moet een geldig postvak op de Exchange-server hebben.  

         Zie voor meer informatie [toegang tot services in System Center Configuration Manager beheren](../../protect/deploy-use/manage-access-to-services.md).  

6.  U kunt de installatie van de Exchange Server-connector controleren door statusberichten te gebruiken en de logboekbestanden te controleren:  

    -   Om te bevestigen dat Site Component Manager de Exchange Server-connector heeft geïnstalleerd, zoekt u naar de status-id **1015** voor het **SMS_EXCHANGE_CONNECTOR** -onderdeel. Als Configuration Manager kan niet de connector installeren (bijvoorbeeld omdat de opgegeven Client Access Server-computer offline is), Configuration Manager probeert opnieuw, voor de installatie om de 60 minuten totdat de installatie is geslaagd of u de Exchange Server-connector verwijderen.  

    -   Zoek op de siteservercomputer naar het SiteComp.log-bestand en zoek vervolgens in het logboekbestand naar `Component SMS_EXCHANGE_CONNECTOR flagged for installation`. Een geslaagde installatie word vervolgens geregistreerd met de volgende tekst: `STATMSG: ID=1015`.  
