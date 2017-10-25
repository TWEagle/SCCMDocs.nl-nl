---
title: Sitegegevens publiceren | Microsoft Docs
description: Informatie over het publiceren van Configuration Manager-sites naar Active Directory Domain Services.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 17cf034f-eaff-43ce-bc8e-917213c1db74
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: bcfb002c503485f03ba27d7346acb61d0d3c6087
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="publish-site-data-for-system-center-configuration-manager"></a>Sitegegevens publiceren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u het Active Directory-schema voor System Center Configuration Manager uitbreidt, kunt u Configuration Manager-sites publiceren naar Active Directory Domain Services (AD DS). Hiermee kunt Active Directory computers veilig site-informatie ophalen van een vertrouwde bron. Hoewel sitegegevens publiceren in AD DS niet vereist voor de basisfunctionaliteit van Configuration Manager is, kan deze administratieve overhead om dit te doen verminderen.  

-   **Wanneer een site is geconfigureerd voor publicatie naar AD DS**, Configuration Manager-clients automatisch beheerpunten via Active Directory-publicatie kunnen vinden. Ze gebruiken een LDAP-query naar een globale-catalogusserver.  

-   **Wanneer een site niet naar AD DS publiceert**, moeten clients over een alternatief mechanisme beschikken om hun standaardbeheerpunt te zoeken.  

Zie voor meer informatie over hoe clients een beheerpunt vinden [begrijpen hoe clients siteresources en -services voor System Center Configuration Manager vinden](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

## <a name="configure-sites-to-publish-to-ad-ds"></a>Sites configureren om naar AD DS te publiceren  
 Hier volgen de hoofdstappen:  

-   U moet [Active Directory-schema voor System Center Configuration Manager uitbreiden](../../../../core/plan-design/network/extend-the-active-directory-schema.md) in elk forest waar u sitegegevens gaat publiceren. Zorg er ook voor de **System Management** container aanwezig is.  

-   U moet het computeraccount van elke primaire site die gegevens publiceert verlenen **volledig beheer** naar de **System Management** container en alle onderliggende objecten.  

### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-active-directory-forest"></a>Een Configuration Manager-sites om sitegegevens te publiceren naar Active Directory-forest mogelijk

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, en klik op **Sites**. Selecteer de site die u wilt kunnen sitegegevens publiceren. Klik op de **Start** tabblad, in de **eigenschappen** groep, klikt u op **eigenschappen**.  

3.  Op de **Publishing** tabblad met eigenschappen van de site, selecteert u de forests waarnaar deze site sitegegevens gaat publiceren.  

4.  Klik op **OK** om de configuratie op te slaan.  

### <a name="to-set-up-active-directory-forests-for-publishing"></a>Voor het instellen van Active Directory-forests voor publicatie  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Klik op **Active Directory-forests** in de werkruimte **Beheer**. Als Active Directory-forestdetectie eerder is uitgevoerd, ziet u iedere gedetecteerde forest in het resultatenvenster. De lokale forest en vertrouwde forests worden gedetecteerd wanneer Active Directory-forestdetectie wordt uitgevoerd. U kunt niet-vertrouwde forests alleen handmatig toevoegen.  

    -   Als u een eerder gedetecteerd forest instelt, selecteert u het forest in het deelvenster met resultaten. Klik op de **Start** tabblad, in de **eigenschappen** groep, klikt u op **eigenschappen** om de foresteigenschappen te openen. Ga door met stap 3.  

    -   Voor het instellen van een nieuw forest dat niet wordt vermeld, op de **Start** tabblad, in de **maken** groep, klikt u op **Forest toevoegen** openen de **Forests toevoegen** in het dialoogvenster. Ga door met stap 3.  

3.  Op de **algemene** tabblad, voert u de configuraties voor de forest die u wilt detecteren en geeft de **Active Directory-Forestaccount**.  

    > [!NOTE]  
    >  Voor Active Directory-forestdetectie is een globaal account nodig om niet-vertrouwde forests te detecteren en ernaar te publiceren. Als u geen computeraccount van de siteserver gebruikt, kunt alleen een globaal account selecteren.  

4.  Als u van plan bent om sites sitegegevens te laten publiceren naar dit forest, vult u op het tabblad **Publiceren** de configuraties in voor publicatie naar dit forest.  

    > [!NOTE]  
    >  Als u inschakelt dat sites kunnen publiceren naar een forest, moet u het Active Directory-schema van dit forest uitbreiden voor Configuration Manager. De Active Directory-Forestaccount moet machtigingen voor volledig beheer voor de systeemcontainer in dat forest hebben.  

5.  Na voltooiing van de configuratie van deze forest voor Active Directory-forestdetectie, klikt u op **OK** om de configuratie op te slaan.  
