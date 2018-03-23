---
title: Release-opmerkingen
titleSuffix: Configuration Manager
description: Meer informatie over urgente problemen die nog niet zijn opgelost in het product of in een Microsoft Knowledge Base-artikel besproken.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e22bc4818f10a1f60fdb2135eb705e46dbaa10a4
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="release-notes-for-system-center-configuration-manager"></a>Opmerkingen bij de release van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met Configuration Manager opmerkingen bij de productrelease zijn beperkt tot urgente problemen. Deze problemen worden niet nog vast in het product of worden uiteengezet in een Microsoft Knowledge Base-artikel.  

Functiespecifieke documentatie bevat informatie over bekende problemen die invloed hebben op de belangrijkste scenario's.  

> [!TIP]  
>  Dit onderwerp bevat opmerkingen bij de release voor de huidige vertakking van Configuration Manager. Zie voor informatie over de vertakking technical preview, [Technical Preview voor System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

Zie voor informatie over de nieuwe functies geïntroduceerd met verschillende versies, de volgende artikelen:
- [Wat is er nieuw in versie 1802](/sccm/core/plan-design/changes/whats-new-in-version-1802)
- [Wat is er nieuw in versie 1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)
- [Wat is er nieuw in versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)  



## <a name="setup-and-upgrade"></a>Installatie en upgrade  


### <a name="when-using-redistributable-files-from-the-cdlatest-folder-setup-fails-with-a-manifest-verification-error"></a>Als u de herdistribueerbare bestanden vanaf de CD. Meest recente map setup is mislukt met een manifest verificatiefout
<!-- 510080, 490569  -->

Wanneer u setup uitvoert vanaf de CD. Meest recente map gemaakt voor versie 1606 en herdistribueerbare bestanden die deel uitmaakt van deze CD gebruiken. Meest recente map, mislukt de installatie met de volgende fouten in het logboek van Setup van Configuration Manager:

  `ERROR: File hash check failed for defaultcategories.dll`  
  `ERROR: Manifest verification failed. Wrong version of manifest?`

#### <a name="workaround"></a>Tijdelijke oplossing
Gebruik een van de volgende opties:
 - Tijdens de installatie, kiezen voor het downloaden van de meest recente herdistribueerbare bestanden van Microsoft. Gebruik de meest recente herdistribueerbare bestanden in plaats van de bestanden in de CD. Meest recente map.
 - Verwijder handmatig de *cd.latest\redist\languagepack\zhh* map en voer vervolgens Setup opnieuw uit.


### <a name="setup-command-line-option-joinceip-must-be-specified"></a>Setup-opdrachtregeloptie die joinceip moet worden opgegeven.
<!--510806-->
*Van toepassing op: Configuration Manager versie 1802*

U start in Configuration Manager versie 1802, is de functie Customer Experience Improvement Program (CEIP) verwijderd uit het product. Wanneer [installatie automatiseren](/sccm/core/servers/deploy/install/command-line-options-for-setup) van een nieuwe site via een opdrachtregel of zonder toezicht script setup een foutmelding dat een vereiste parameter ontbreekt. 

#### <a name="workaround"></a>Tijdelijke oplossing
Hoewel deze geen effect op het resultaat van het installatieproces heeft, bevatten de **JoinCEIP** parameter in de setup-opdrachtregel.

 > [!Note]  
 > De parameter EnableSQM voor [console-setup](/sccm/core/servers/deploy/install/install-consoles) is niet vereist.



<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>Clientimplementatie en -upgrade

### <a name="azure-ad-enabled-clients-cant-communicate-with-management-point"></a>Clients met Azure AD-ondersteuning kunnen niet communiceren met het beheerpunt
<!--501089-->
*Van toepassing op: Configuration Manager versie 1706*
<!--also fixed in 1710 HFRU-->
In het scenario [installeren en toewijzen van Configuration Manager Windows 10-clients die gebruikmaken van Azure AD voor verificatie](/sccm/core/clients/deploy/deploy-clients-cmg-azure), communicatie van clients mislukt wanneer het HTTPS-beheerpunt gebruikt de referenties van de alternatieve database. 

#### <a name="workaround"></a>Tijdelijke oplossing
Dit probleem met een van de volgende acties beperken:
- Bijwerken van de site naar de nieuwste versie en de meest recente hotfix toepassen
- Wijzigt de aanmeldgegevens die gebruikmaakt van het beheerpunt.


<!-- ## Operating system deployment  -->



## <a name="software-updates"></a>Software-updates

### <a name="servicing-plans-create-many-duplicate-software-update-groups-and-deployments-by-default"></a>Onderhoudsplannen maken veel dubbele software-updategroepen en implementaties standaard  
<!-- 474326 -->
De wizard Onderhoudsplan maken wordt momenteel standaard uitgevoerd na elke synchronisatie van software-updates. Telkens wanneer de wizard wordt uitgevoerd, wordt er een nieuwe software-updategroep en -implementatie gemaakt. Als u een synchronisatieplanning voor software-updates die meerdere keren per dag wordt uitgevoerd hebt, maakt de wizard Onderhoudsplan maken meerdere software-updategroepen en implementaties elke dag.  

#### <a name="workaround"></a>Tijdelijke oplossing
 Nadat u een onderhoudsplan hebt gemaakt, opent u de eigenschappen voor het onderhoudsplan, gaat u naar de **Evaluatieplanning** tabblad **e regel uitvoeren volgens een schema**, klikt u op **aanpassen**, en maak een aangepaste planning. U kunt bijvoorbeeld instellen dat het onderhoudsplan elke 60 dagen wordt uitgevoerd.  



## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10"></a>U kunt niet langer Windows Phone 8.1 VPN-profielen implementeren op Windows 10
<!-- 503274  -->
*Van toepassing op: Configuration Manager versie 1710*

U kan niet een VPN-profiel maken met de Windows Phone 8.1 de werkstroom, dit is ook van toepassing op Windows 10-apparaten. Voor deze profielen ziet u de wizard maken niet langer de pagina ondersteunde Platforms. Windows Phone 8.1 wordt automatisch geselecteerd op de back-end. De pagina ondersteunde Platforms is beschikbaar in de eigenschappen van het profiel, maar de opties voor Windows 10 niet worden weergegeven.

#### <a name="workaround"></a>Tijdelijke oplossing
 Gebruik de werkstroom van Windows 10 VPN-profiel voor Windows 10-apparaten. Als deze optie niet haalbaar voor uw omgeving, moet u contact op met ondersteuning. Ondersteuning kunt u het doelitem voor Windows 10 kunt toevoegen.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
