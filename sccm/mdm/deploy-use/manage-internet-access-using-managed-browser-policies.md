---
title: Internettoegang beheren met beheerde-browserbeleid | Microsoft Docs
description: Implementeer de Intune Managed Browser om te beheren en beperken van toegang tot Internet.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e25e00c-c9a8-473f-bcb7-ea989f6ca3c5
caps.latest.revision: "6"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: d2dd2c25a2714851ba1e71414cabcef38d3ce014
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-internet-access-using-managed-browser-policies-with-system-center-configuration-manager"></a>Internettoegang beheren met beleid voor beheerde browsers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager die u kunt de Intune Managed Browser (een toepassing voor websurfen) implementeren en de toepassing koppelen aan beleid voor beheerde browsers. Het beheerde-browserbeleid stelt u een lijst met toegestane of een lijst met websites, die gebruikers van de beheerde browser om te kunnen gaan.  

 Omdat dit een beheerde app is, kunt u ook mobile application management-beleid van toepassing op, zoals het gebruik van knippen, kopiëren en plakken. Dit voorkomt dat schermopnamen en zorgt er ook voor dat koppelingen naar inhoud alleen in andere beheerde apps openen. Zie voor meer informatie [apps beveiligen met mobile application management-beleid](protect-apps-using-mam-policies.md).  

> [!IMPORTANT]  
>  Als gebruikers de beheerde browser zelf installeren, wordt deze niet beheerd door andere beleidsregels die u opgeeft. Om ervoor te zorgen dat de browser wordt beheerd door Configuration Manager, moeten ze de app verwijderen voordat u deze voor ze als beheerde app implementeren kunt.  

 U kunt beheerde-browserbeleidsregels maken voor de volgende typen apparaten:  

-   Apparaten met Android 4 en hoger  

-   Apparaten met iOS 7 en hoger  

> [!NOTE]  
>  Zie voor meer informatie en de Intune Managed Browser-app te downloaden [iTunes](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) voor iOS en [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en) voor Android.  

## <a name="create-a-managed-browser-policy"></a>Een beheerde-browserbeleid maken  

1.  Kies in de Configuration Manager-console **softwarebibliotheek** > **Toepassingsbeheer** > **Application Management-beleid**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **beleid voor toepassingsbeheer maken**.  

4.  Op de **algemene** pagina, voer de naam en beschrijving voor het beleid en kies vervolgens **volgende**.  

5.  Op de **beleidstype** pagina, selecteer het platform, selecteert u **Managed Browser** voor het beleid, typ en kies vervolgens **volgende**.  

     Selecteer op de pagina **Managed Browser** een van de volgende opties:  

    -   **Toestaan dat de beheerde browser alleen de hieronder vermelde URL's opent**– Geef een lijst met URL's die de beheerde browser kan openen.  

    -   **De beheerde browser de onderstaande URL's opent**– Geef een lijst met URL's die de beheerde browser kan worden geopend.  

    > [!NOTE]  
    >  U kunt niet zowel toegestane als geblokkeerde URL's in hetzelfde beheerde-browserbeleid opnemen.  

     Voor meer informatie over de URL-indelingen die kunt u opgeven, Zie URL-indeling voor toegestane en geblokkeerde URL's in dit artikel.  

    > [!NOTE]  
    >  Het beleidstype algemeen kunt u de functionaliteit van apps die u implementeert om ervoor te zorgen dat ze in overeenstemming met uw bedrijf naleving en het beveiligingsbeleid te wijzigen. U kunt bijvoorbeeld bewerkingen zoals knippen, kopiëren en plakken binnen een beperkte app beperken. Zie voor meer informatie over het beleidstype algemeen [apps beveiligen met mobile application management-beleid](protect-apps-using-mam-policies.md).  

6.  Sluit de wizard af.  

Het nieuwe beleid wordt weergegeven in het knooppunt **Beleid voor toepassingsbeheer** van de werkruimte **Softwarebibliotheek** .  

## <a name="create-a-software-deployment-for-the-managed-browser-app"></a>Een software-implementatie voor de beheerde-browserapp maken  
 Nadat u het beleid voor beheerde browsers hebt gemaakt, kunt u vervolgens een software-implementatietype voor de beheerde browsertoepassing maken. U moet zowel een algemeen en de beheerde browser-beleid voor de beheerde browser-app koppelen.  

 Zie voor meer informatie [toepassingen maken](create-applications.md).  

## <a name="security-and-privacy-for-the-managed-browser"></a>Beveiliging en privacy voor de beheerde browser  

-   Op iOS-apparaten de websites die zijn verlopen of niet-vertrouwde certificaten kan niet worden geopend.  

-   Instellingen door gebruikers voor de ingebouwde browser op hun apparaten, worden niet gebruikt door de beheerde browser. De beheerde browser heeft geen toegang tot deze instellingen.  

-   Als u de opties ingesteld **eenvoudige PINCODE vereisen voor toegang tot** of **bedrijfsreferenties vereisen voor toegang tot** in een mobile application management-beleid die zijn gekoppeld aan de beheerde browser, een gebruiker kan Klik op Help op de pagina authenticatie en Ga naar eender welke site--zelfs een toegevoegd aan een lijst met geblokkeerde websites in het beleid voor beheerde browsers.  

-   De beheerde browser kan alleen toegang tot sites blokkeren wanneer de sites rechtstreeks worden geopend. De browser kan geen toegang blokkeren als er tussenliggende services (zoals een vertaalservice) worden gebruikt voor toegang tot de site.  

## <a name="reference-information"></a>Referentiegegevens  

###  <a name="url-format-for-allowed-and-blocked-urls"></a>URL-indeling voor toegestane en geblokkeerde URL´s  

Gebruik de volgende gegevens voor meer informatie over de toegestane indelingen en jokertekens die u kunt gebruiken bij het opgeven van URL's in de lijsten met toegestane en geblokkeerde websites.  

-   U kunt het jokerteken '**\***' gebruiken volgens de regels in de lijst met toegestane patronen hieronder.  

-   Zorg ervoor dat u alle URL's voorziet van het voorvoegsel **http** of **https** wanneer u ze in de lijst invoert.  

-   U kunt poortnummers in het adres opgeven. Als u geen poortnummer opgeeft, zijn de gebruikte waarden:  

    -   Poort 80 voor http  

    -   Poort 443 voor https  

     Het gebruik van jokertekens voor het poortnummer wordt niet ondersteund, bijvoorbeeld **http://www.contoso.com:\*** en **http://www.contoso.com: /\***  

-   Gebruik de volgende tabel voor meer informatie over de toegestane patronen die u kunt gebruiken wanneer u een URL opgeeft:  

    |URL|Komt overeen met|Komt niet overeen met|  
    |---------|-------------|--------------------|  
    |http://www.contoso.com<br /><br /> Komt overeen met één pagina|www.contoso.com|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> contoso.com/|  
    |http://contoso.com<br /><br /> Komt overeen met één pagina|contoso.com/|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com|  
    |http://www.contoso.com/*<br /><br /> Komt overeen met alle URL's die beginnen met www.contoso.com|www.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com/videos/tvshows|host.contoso.com<br /><br /> host.contoso.com/images|  
    |http://*.contoso.com/\*<br /><br /> Komt overeen met alle subdomeinen onder contoso.com|developer.contoso.com/resources<br /><br /> news.contoso.com/images<br /><br /> news.contoso.com/videos|contoso.host.com|  
    |http://www.contoso.com/images<br /><br /> Komt overeen met een afzonderlijke map|www.contoso.com/images|www.contoso.com/images/dogs|  
    |http://www.contoso.com:80<br /><br /> Komt overeen met één pagina, met gebruik van een poortnummer|http://www.contoso.com:80||  
    |https://www.contoso.com<br /><br /> Komt overeen met een enkele, beveiligde pagina|https://www.contoso.com|http://www.contoso.com|  
    |http://www.contoso.com/images/*<br /><br /> Komt overeen met een enkele map en alle submappen|www.contoso.com/images/dogs<br /><br /> www.contoso.com/images/cats|www.contoso.com/videos|  

-   Hier volgen enkele voorbeelden van een aantal invoerwaarden die u niet kunt opgeven:  

    -   *.com  

    -   *.contoso /\*  

    -   www.contoso.com/*images  

    -   www.contoso.com/*images\*pigs  

    -   www.contoso.com/page*  

    -   IP-adressen  

    -   https://*  

    -   http://*  

    -   http://www.contoso.com:*  

    -   http://www.contoso.com: /*  

> [!NOTE]  
>  *. microsoft.com is altijd toegestaan.  

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>Conflicten tussen de lijst met toegestane en de lijst met geblokkeerde websites oplossen  
 Als er meerdere beheerde-browserbeleidsregels zijn geïmplementeerd op een apparaat en de instellingen conflicteren, worden de modus (toestaan of blokkeren) en de URL-lijsten geëvalueerd op conflicten. Bij een conflict geldt het volgende gedrag:  

-   Als de modi in elke beleidsregel hetzelfde zijn maar de URL-lijsten verschillen, wordt de URL's niet afgedwongen op het apparaat.  

-   Als de modi in elke beleidsregel verschillen maar de URL-lijsten hetzelfde zijn, wordt de URL's niet afgedwongen op het apparaat.  

-   Als een apparaat voor de eerste keer beheerde-browserbeleidsregels ontvangt en twee beleidsregels conflicteren, worden de URL's niet afgedwongen op het apparaat. Gebruik het knooppunt **Conflicterende beleidsinstellingen** van de werkruimte **Beleid** om de conflicten weer te geven.  

-   Als een apparaat al een beheerde-browserbeleid heeft ontvangen en er een tweede beleid met conflicterende instellingen wordt geïmplementeerd, blijven de oorspronkelijke instellingen op het apparaat. Gebruik het knooppunt **Conflicterende beleidsinstellingen** van de werkruimte **Beleid** om de conflicten weer te geven.  
