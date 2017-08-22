---
title: E-mail, Wi-Fi en VPN-profielen controleren | Microsoft Docs
description: Informatie over het bewaken van de status van naleving van e-mail, Wi-Fi en VPN-profielen in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2315b8b-98bc-40e1-8ef9-bfb5e69ab109
caps.latest.revision: "4"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 73d941633d270cf9628f8be14e1e56f3c78624b6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="monitor-email-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>E-mail, Wi-Fi en VPN-profielen in System Center Configuration Manager controleren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u hebt System Center Configuration Manager E-mail, Wi-Fi of VPN-profielen geïmplementeerd voor gebruikers in uw hiërarchie, kunt u de volgende procedures om de compatibiliteitsstatus van het profiel te controleren:  

-   [Nalevingsresultaten weergeven in de Configuration Manager-console](#BKMK_console)  

-   [De nalevingsresultaten weergeven met behulp van rapporten](#BKMK_Reports)  

##  <a name="BKMK_console"></a> Nalevingsresultaten weergeven in de Configuration Manager-console  
 Gebruik deze procedure om details te bekijken over de naleving van geïmplementeerde profielen in de System Center Configuration Manager-console.  

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Nalevingsresultaten weergeven in de Configuration Manager-console  

1.  Klik in de System Center Configuration Manager-console op **bewaking**.  

2.  Klik in de werkruimte **Bewaking** op **Implementaties**.  

3.  In de **implementaties** , selecteert u de implementatie van het profiel waarvoor u wilt bekijken van informatie over de compatibiliteit.  

4.  U kunt samenvattingsinformatie controleren over de compatibiliteit van de implementatie van het profiel op de hoofdpagina. Voor meer gedetailleerde informatie weergeven, selecteert u de implementatie van het profiel, en klik vervolgens op de **Start** tabblad, in de **implementatie** groep, klikt u op **Status weergeven** openen de **Implementatiestatus** pagina.  

     De pagina **Implementatiestatus** bevat de volgende tabbladen:  

    -   **Compatibel:** Geeft de naleving van het profiel dat is gebaseerd op het aantal beïnvloede activa. U kunt dubbelklikken op een regel om een tijdelijk knooppunt te creëren onder het knooppunt **Gebruikers** in de werkruimte **Activa en naleving** , die alle gebruikers bevat die compatibel met dit profiel zijn. De **activumgegevens** deelvenster de gebruikers weergegeven die compatibel met het profiel zijn. Dubbelklik op een gebruiker in de lijst om extra informatie weer te geven.  

        > [!IMPORTANT]  
        >  Een profiel wordt niet beoordeeld als het is niet van toepassing op een clientapparaat; het wordt evenwel geretourneerd als compatibel.  

    -   **Fout:** Geeft een lijst met alle fouten voor de implementatie van het geselecteerde profiel dat gebaseerd is op het aantal beïnvloede activa. U kunt dubbelklikken op een regel om een tijdelijk knooppunt te creëren onder het knooppunt **Gebruikers** in de werkruimte **Activa en naleving** , die alle gebruikers bevat die fouten genereerden met dit profiel. Wanneer u een gebruiker selecteert, geeft het deelvenster **Activumgegevens** de gebruikers weer die met het geselecteerde probleem te maken krijgen. Dubbelklik op een gebruiker in de lijst om extra informatie weer te geven over het probleem.  

    -   **Niet-compatibele:** Geeft een lijst met alle niet-compatibele regels binnen het profiel dat is gebaseerd op het aantal beïnvloede activa. U kunt dubbelklikken op een regel om een tijdelijk knooppunt te creëren onder het knooppunt **Gebruikers** in de werkruimte **Activa en naleving** , die alle gebruikers bevat die niet conform dit profiel zijn. Wanneer u een gebruiker selecteert, geeft het deelvenster **Activumgegevens** de gebruikers weer die met het geselecteerde probleem te maken krijgen. Dubbelklik op een gebruiker in de lijst om verdere informatie weer te geven over het probleem.  

    -   **Onbekend:** Geeft een lijst van alle gebruikers die geen naleving voor het geselecteerde profiel, tezamen met de huidige clientstatus van de apparaten rapporteren.  

5.  Op de **Implementatiestatus** pagina kunt u gedetailleerde informatie over de naleving van het geïmplementeerde profiel bekijken. Een tijdelijk knooppunt wordt gemaakt onder het knooppunt **Implementaties** waarmee u deze informatie snel kunt terugvinden.  

##  <a name="BKMK_Reports"></a> De nalevingsresultaten weergeven met behulp van rapporten  
 Instellingen voor naleving, waaronder profielen in System Center Configuration Manager, bevatten ook een aantal van ingebouwde rapporten waarmee u informatie over profielen bewaken. Deze rapporten hebben de rapportcategorie van **Compatibiliteit en instellingen beheren**.  

> [!IMPORTANT]  
>  U moet een jokerteken (%) gebruiken wanneer u de parameters **Apparaatfilter** en **Gebruikerfilter** gebruikt in de rapporten van instellingen voor naleving.  

 Zie voor meer informatie over het configureren van rapportage in System Center Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).  
