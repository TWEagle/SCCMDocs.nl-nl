---
title: Sitegegevens publiceren | Microsoft-documenten
description: Leer hoe u Configuration Manager-sites publiceren naar Active Directory Domain Services.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 17cf034f-eaff-43ce-bc8e-917213c1db74
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e7629fdf7fdf615fa27894158c3d101432c95a04
ms.openlocfilehash: bcfb002c503485f03ba27d7346acb61d0d3c6087
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="publish-site-data-for-system-center-configuration-manager"></a>Sitegegevens publiceren voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Nadat u het Active Directory-schema voor System Center Configuration Manager uitbreidt, kunt u Configuration Manager-sites publiceren naar Active Directory Domain Services (AD DS). Hiermee kunt Active Directory computers veilig site-informatie ophalen van een vertrouwde bron. Hoewel sitegegevens publiceren naar AD DS niet vereist voor de basisfunctionaliteit van Configuration Manager is, kan deze administratieve overhead om dit te doen verminderen.  

-   **Wanneer een site is geconfigureerd om te publiceren naar AD DS**, Configuration Manager-clients kunnen automatisch beheerpunten vinden via Active Directory-publicatie. Ze gebruiken een LDAP-query naar een globale catalogusserver te gebruiken.  

-   **Wanneer een site niet naar AD DS publiceert**, moeten clients over een alternatief mechanisme beschikken om hun standaardbeheerpunt te zoeken.  

Zie voor meer informatie over hoe clients een beheerpunt vinden [begrijpen hoe clients vinden sitebronnen en services voor System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

## <a name="configure-sites-to-publish-to-ad-ds"></a>Sites configureren om naar AD DS te publiceren  
 Hier volgen de hoofdstappen:  

-   U moet [het Active Directory-schema uitbreidt voor System Center Configuration Manager](../../../../core/plan-design/network/extend-the-active-directory-schema.md) in elke forest waar u sitegegevens zult publiceren. Zorg er ook voor de **Systeembeheer** container aanwezig is.  

-   U moet de computeraccount van elke primaire site die gegevens zal publiceren verlenen **volledig beheer** naar de **Systeembeheer** container en alle onderliggende objecten.  

### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-active-directory-forest"></a>Om in te schakelen van een Configuration Manager-site naar site-informatie publiceren naar Active Directory-forest

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, en klikt u op **Sites**. Selecteer de site die u wilt publiceren sitegegevens. Klik vervolgens op de **Start** tabblad, in de **eigenschappen** groep, klikt u op **eigenschappen**.  

3.  Op de **Publishing** tabblad Eigenschappen van de site, selecteer de forests waarnaar deze site sitegegevens gaat publiceren.  

4.  Klik op **OK** om de configuratie op te slaan.  

### <a name="to-set-up-active-directory-forests-for-publishing"></a>Voor het instellen van Active Directory-forests voor publicatie  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Klik op **Active Directory-forests** in de werkruimte **Beheer**. Als Active Directory-forestdetectie eerder is uitgevoerd, ziet u iedere gedetecteerde forest in het resultatenvenster. De lokale forest en vertrouwde forests worden gedetecteerd wanneer Active Directory-forestdetectie wordt uitgevoerd. U kunt niet-vertrouwde forests alleen handmatig toevoegen.  

    -   Als u een eerder gedetecteerd forest instelt, selecteert u het forest in het deelvenster met resultaten. Klik vervolgens op de **Start** tabblad, in de **eigenschappen** groep, klikt u op **eigenschappen** om de foresteigenschappen te openen. Ga door met stap 3.  

    -   Voor het instellen van een nieuw forest die niet wordt vermeld, op de **Start** tabblad, in de **maken** groep, klikt u op **Forest toevoegen** openen van de **Forests toevoegen** in het dialoogvenster. Ga door met stap 3.  

3.  Op de **algemeen** tabblad voltooid configuraties voor het forest dat u wilt detecteren, en geef de **Active Directory-Forestaccount**.  

    > [!NOTE]  
    >  Voor Active Directory-forestdetectie is een globaal account nodig om niet-vertrouwde forests te detecteren en ernaar te publiceren. Als u geen computeraccount van de siteserver gebruikt, kunt alleen een globaal account selecteren.  

4.  Als u van plan bent om sites sitegegevens te laten publiceren naar dit forest, vult u op het tabblad **Publiceren** de configuraties in voor publicatie naar dit forest.  

    > [!NOTE]  
    >  Als u inschakelt dat sites kunnen publiceren naar een forest, moet u het Active Directory-schema van dit forest uitbreiden voor Configuratiebeheer. De Active Directory-Forestaccount moet machtigingen voor volledig beheer voor de systeemcontainer in dat forest hebben.  

5.  Na voltooiing van de configuratie van deze forest voor Active Directory-forestdetectie, klikt u op **OK** om de configuratie op te slaan.  

