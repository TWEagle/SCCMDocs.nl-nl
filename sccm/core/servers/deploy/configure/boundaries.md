---
title: "Grenzen definiëren"
titleSuffix: Configuration Manager
description: "Begrijpen hoe netwerklocaties op uw intranet die u wilt beheren apparaten kan bevatten definiëren."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 4a9dc4d9-e114-42ec-ae2b-73bee14ab04f
caps.latest.revision: "10"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 224e91ebb3ff6ccfa94c3e2022066ad6d27c3afb
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="define-network-locations-as-boundaries-for-system-center-configuration-manager"></a>Definieer netwerklocaties als grenzen voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager grenzen zijn locaties op uw netwerk die apparaten bevatten die u wilt beheren. De grens van die een apparaat ingeschakeld is, is gelijk aan de Active Directory-site of een netwerk-IP-adres dat wordt geïdentificeerd door de Configuratoin Manager-client die op het apparaat is geïnstalleerd.
 - U kunt handmatig afzonderlijke grenzen maken. Configuration Manager biedt echter geen ondersteuning voor de rechtstreekse invoer van een supernet als grens. Gebruik in plaats daarvan het grenstype IP-adresbereik.
 - U kunt de [Active Directory Forest Discovery](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutForest) methode voor het automatisch detecteren en grenzen maken voor elk IP-subnetten en Active Directory-sites. Wanneer Active Directory-Forestdetectie een supernet dat is toegewezen aan een Active Directory-site identificeert, wordt dit supernet door Configuration Manager in een grens van IP-adresbereik.  

Het is niet ongewoon is voor het gebruik van een IP-adres dat de Configuration Manager-beheerder niet bekend met is een apparaat. Wanneer de netwerklocatie van een apparaat onzeker is, controleert u wat het apparaat meldt als de locatie met behulp van de **IPCONFIG** opdracht op het apparaat.  

Wanneer u een grens maakt, krijgt deze automatisch een naam die is gebaseerd op het type en bereik van de grens. U kunt deze naam niet wijzigen. In plaats daarvan kunt u een beschrijving die de grens in de Configuration Manager-console te identificeren.  

Elke grens is beschikbaar voor gebruik door elke site in uw hiërarchie. Nadat u een grens hebt gemaakt, kunt u de eigenschappen als volgt wijzigen:  
-   De grens toevoegen aan een of meer grensgroepen.  
-   Het type of bereik van de grens wijzigen.  
-   Ga naar het tabblad **Sitesystemen** voor de grenzen om te zien welke sitesysteemservers (distributiepunten, statusmigratiepunten en beheerpunten) aan de grens zijn gekoppeld.  

## <a name="to-create-a-boundary"></a>Een grens maken  

1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** > **grenzen**  

2.  Klik op het tabblad **Start** in de groep **Maken** op **Maken Boundary**.  

3.  Op het tabblad **Algemeen** van het dialoogvenster Grens maken kunt u bij **Beschrijving** een beschrijving opgeven om de grens aan te duiden met een beschrijvende naam of verwijzing.  

4.  Selecteer een **type** voor deze grens:  

    -   Als u **IP-subnet**selecteert, moet u bij **Subnet-id** een subnet-id voor deze grens opgeven.  
        > [!TIP]  
        >  Als u het **netwerk** en **subnetmasker** opgeeft, wordt de **subnet-id** automatisch opgegeven. Wanneer u de grens opslaat, wordt alleen de subnet-id opgeslagen.  

    -   Als u **Active Directory-site**selecteert, moet u een Active Directory-site in het lokale forest van de siteserver opgeven of **Bladeren** selecteren.  

        > [!IMPORTANT]  
        >  Wanneer u een Active Directory-site voor een grens opgeeft, bevat de grens alle IP-subnetten die lid zijn van die Active Directory-site. Als de configuratie van de Active Directory-site wordt gewijzigd in Active Directory, worden de netwerklocaties die zijn opgenomen in deze grens ook gewijzigd.  

    -   Als u **IPv6-voorvoegsel**selecteert, moet u een **voorvoegsel** in de IPv6-voorvoegselindeling opgeven.  

    -   Als u **IP-adresbereik**selecteert, moet u een **IP-beginadres** en **IP-eindadres** opgeven die een deel van een IP-subnet of meerdere IP-subnetten bevatten.    

5.  Klik op **OK** om de nieuwe grens op te slaan.  

## <a name="to-configure-a-boundary"></a>Een grens configureren  

1.  Klik in de Configuration Manager-console op **beheer** > **Hiërarchieconfiguratie** > **grenzen**  

2.  Selecteer de grens die u wilt wijzigen.  

3.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

4.  Selecteer in het dialoogvenster **Eigenschappen** voor de grens het tabblad **Algemeen** om de **beschrijving** of het **type** voor de grens te bewerken. U kunt ook het bereik van een grens wijzigen door de netwerklocaties voor de grens te bewerken. Voor een grens van het type Active Directory-site kunt u bijvoorbeeld een nieuwe naam opgeven.  

5.  Selecteer het tabblad **Sitesystemen** om de sitesystemen weer te geven die zijn gekoppeld aan deze grens. U kunt deze configuratie niet wijzigen vanuit de eigenschappen van een grens.  

    > [!TIP]  
    >  Een sitesysteemserver wordt als een sitesysteem voor een grens weergegeven als de sitesysteemserver is gekoppeld aan een sitesysteemserver voor minstens één grensgroep waarin deze grens is opgenomen. Deze wordt geconfigureerd op het tabblad **Verwijzingen** van een grensgroep.  

6.  Selecteer het tabblad **Grensgroepen** om het lidmaatschap van grensgroepen voor deze grens te wijzigen:  

    -   Als u deze grens aan een of meer grensgroepen wilt toevoegen, klikt u op **Toevoegen**, schakelt u het selectievakje voor een of meer grensgroepen in en klikt u op **OK**.  

    -   Als u deze grens uit een grensgroep wilt verwijderen, selecteert u de grensgroep en klikt u op **Verwijderen**.  

7.  Klik op **OK** om de grenseigenschappen te sluiten en de configuratie op te slaan.  
