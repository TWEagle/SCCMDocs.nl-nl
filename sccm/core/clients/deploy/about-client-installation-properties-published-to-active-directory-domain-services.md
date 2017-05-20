---
title: Eigenschappen van clientinstallatie in Active Directory Domain Services | Microsoft-documenten
description: Clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services in System Center Configuration Manager gebruiken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 101d7d4d-92db-419d-b2ae-3c1c1dea68e9
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 744bc3792a02f13d3cf940cd1a4f2fd8749ee2f4
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="about-client-installation-properties-published-to-active-directory-domain-services"></a>Eigenschappen van clientinstallaties naar Active Directory Domain Services gepubliceerd

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u het Active Directory-schema voor System Center Configuration Manager uitbreidt en de site wordt gepubliceerd naar Active Directory Domain Services, worden veel clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services. Als een computer deze clientinstallatie-eigenschappen localiseren kan, kan hij ze gebruiken tijdens de implementatie van Configuration Manager-client.  

 De voordelen van het gebruik van Active Directory Domain Services om eigenschappen van clientinstallatie te publiceren omvatten het volgende:  

-   Software-update-gebaseerde clientinstallaties en Groepsbeleid-clientinstallaties vereisen geen setup-parameters worden ingesteld op elke computer.  

-   Omdat deze informatie automatisch gegenereerd wordt, wordt het risico van menselijke fout, gekoppeld met het handmatig invoeren van installatie-eigenschappen, geëlimineerd.  

> [!NOTE]  
>  Zie voor meer informatie over het uitbreiden van het Active Directory-schema voor Configuration Manager en het publiceren van een site [voor System Center Configuration Manager-Schema-uitbreidingen](../../plan-design/network/schema-extensions.md).  

## <a name="client-installation-properties-published-to-active-directory-domain-services"></a>Clientinstallatie-eigenschappen gepubliceerd naar Active Directory Domain Services  
Hier volgt een lijst met eigenschappen van clientinstallatie. Zie voor meer informatie over elk onderwerp hieronder vermelde [over eigenschappen van clientinstallatie in System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

-   De code van de Configuration Manager-site.  

-   Het server handtekeningcertificaat van de siteserver.  

-   De vertrouwde basissleutel.  

-   De client-communicatiepoorten voor HTTP en HTTPS.  

-   Het terugvalstatuspunt. Als de site meerdere terugvalstatuspunten heeft, wordt alleen het eerste beheerpunt dat geïnstalleerd was gepubliceerd naar Active Directory Domain Services.  

-   Een instelling om aan te geven dat de client moet communiceren door enkel HTTPS te gebruiken.  

-   Instellingen voor PKI-certificaten:  

   -   Of u moet een PKI-clientcertificaat gebruiken.  

   -   De selectiecriteria voor certificaatselectie. Dit kan nodig zijn, omdat de client meer dan één geldig PKI-certificaat kan worden gebruikt voor Configuration Manager.  

   -   Een instelling om te bepalen welk certificaat dient gebruikt te worden als de client meerdere geldige certificaten heeft na het proces van certificaatselectie.  

   -   De lijst van uitgevers van certificaten die een lijst bevat van vertrouwde CA basiscertificaten.  

-   Client.msi installatie-eigenschappen die gespecificeerd zijn in het tabblad **Client** van het dialoogvenster **Clientpushinstallatie-eigenschappen** .

Clientinstallatie (CCMSetup) gebruikt de eigenschappen die worden gepubliceerd naar Active Directory Domain Services enkel indien geen andere eigenschappen gespecificeerd zijn met behulp van een van de volgende:  

-   De handmatige installatie-methode (beschreven in dit artikel)

-   De Groepsbeleid-installatiemethode (beschreven in dit artikel)

> [!NOTE]  
>  De eigenschappen van clientinstallatie worden gebruikt om de client te installeren. Deze eigenschappen kunnen worden overschreven door nieuwe instellingen vanuit zijn toegewezen site nadat de client is geïnstalleerd en correct is toegewezen aan een Configuration Manager-site.  

 Gebruik de informatie in de volgende secties om te bepalen welke Configuration Manager-installatiemethoden voor clients gebruiken Active Directory Domain Services naar installatie-eigenschappen verkrijgen.  

## <a name="client-push-installation"></a>Clientpushinstallatie  
 Clientpushinstallatie gebruikt geen Active Directory Domain Services om installatie-eigenschappen te verkrijgen.  

 In plaats daarvan kunt u eigenschappen van clientinstallatie in de **Client** tabblad van het **Clientpushinstallatie-eigenschappen** in het dialoogvenster. Deze opties en client-gerelateerde site-instellingen worden opgeslagen in een bestand dat de client leest tijdens clientinstallatie.  

> [!NOTE]  
>  U moet geen CCMSetup-eigenschappen opgeven voor clientpushinstallatie, of het terugvalstatuspunt, of de vertrouwde basissleutel in het tabblad **Client** . Deze instellingen worden automatisch aan clients geleverd wanneer ze worden geïnstalleerd door gebruik te maken van clientpushinstallatie.  

 De eigenschappen die u opgeeft in de **Client** tabblad worden gepubliceerd naar Active Directory Domain Services of de site wordt gepubliceerd op Active Directory Domain Services. Deze instellingen worden gelezen door clientinstallaties waar CCMSetup uitgevoerd wordt zonder installatie-eigenschappen.  

## <a name="software-update-point-based-installation"></a>Installatie op basis van software-updatepunten  
 De installatiemethode op basis van software-updatepunten ondersteunt niet de toevoeging van installatie-eigenschappen aan de CCMSetup-opdrachtregel.  

 Indien er geen opdrachtregels werden ingesteld op de clientcomputer door gebruik te maken van groepsbeleid, zoekt CCMSetup op Active Directory Services naar installatie-eigenschappen.  

## <a name="group-policy-installation"></a>Installatie van Groepsbeleid  
 De groepsbeleid-installatiemethode ondersteunt niet de toevoeging van installatie-eigenschappen aan de CCMSetup-opdrachtregel.  

 Indien er geen opdrachtregels werden ingesteld op de clientcomputer, zoekt CCMSetup op Active Directory Services naar installatie-eigenschappen.  

## <a name="manual-installation"></a>Handmatige installatie  
 CCMSetup zoekt onder de volgende omstandigheden in Active Directory Domain Services naar installatie-eigenschappen:  

-   Er zijn na de opdracht CCMSetup.exe geen eigenschappen vanaf de opdrachtregel opgegeven.  

-   De computer is niet via Groepsbeleid ingericht met installatie-eigenschappen.  

## <a name="logon-script-installation"></a>Aanmeldingscriptinstallatie  
 CCMSetup zoekt onder de volgende omstandigheden in Active Directory Domain Services naar installatie-eigenschappen:  

-   Er zijn na de opdracht CCMSetup.exe geen eigenschappen vanaf de opdrachtregel opgegeven.  

-   De computer is niet via Groepsbeleid ingericht met installatie-eigenschappen.  

## <a name="software-distribution-installation"></a>Installatie van softwaredistributie  
 CCMSetup zoekt onder de volgende omstandigheden in Active Directory Domain Services naar installatie-eigenschappen:  

-   Er zijn na de opdracht CCMSetup.exe geen eigenschappen vanaf de opdrachtregel opgegeven.  

-   De computer is niet via Groepsbeleid ingericht met installatie-eigenschappen.  

## <a name="installations-for-clients-that-cannot-access-active-directory-domain-services"></a>Installaties voor clients die geen toegang Active Directory Domain Services tot  
Deze clientcomputers niet lezen of toegang tot de gepubliceerde installatie-eigenschappen van Active Directory Domain Services.

 Deze clients zijn onder andere:  

-   Computers in werkgroepen.  

-   Clients die zijn toegewezen aan een Configuration Manager-site die niet is gepubliceerd naar Active Directory Domain Services.  

-   Clients die zijn geïnstalleerd als ze op het Internet.  

