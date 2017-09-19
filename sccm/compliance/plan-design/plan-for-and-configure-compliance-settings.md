---
title: Plannen en configureren van instellingen voor naleving | Microsoft Docs
description: Meer informatie over de vereisten en configuratietaken voor het werken met instellingen voor naleving in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ea20b01-676a-4cc2-b328-0098a41b202e
caps.latest.revision: "8"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 603f82d9589f17fdbbdcd38baa236fb23424ef34
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="plan-for-and-configure-compliance-settings-in-system-center-configuration-manager"></a>De instellingen voor naleving plannen en configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u begint met het werken met System Center Configuration Manager-instellingen voor naleving, zijn er enkele vereisten die u wilt weten over en een aantal configuratietaken die u wilt uitvoeren.  

## <a name="prerequisites-for-compliance-settings"></a>Vereisten voor de nalevingsinstellingen  

|Vereiste|Meer informatie|  
|------------------|----------------------|  
|Windows Configuration Manager-clients moeten worden ingeschakeld en geconfigureerd voor de evaluatie van de naleving.|Hieronder vindt u de|  
|Als u rapporten uitvoeren wilt, moet u de rapportage voor uw site configureren.|[Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md)|  
|Vereiste machtigingen.|De **instellingen voor naleving** beveiligingsrol bevat de vereiste machtigingen voor het beheren van instellingen voor naleving, en -profielen configuratie-items voor gebruikersgegevens en profielen voor externe verbindingen.<br /><br /> [Beheer op basis van rollen configureren](../../core/servers/deploy/configure/configure-role-based-administration.md)|  

##  <a name="enable-and-configure-compliance-settings-for-windows-pcs-only"></a>Inschakelen en configureren van instellingen voor naleving (voor Windows-pc's alleen)  

Met deze procedure configureert u de standaardclientinstellingen voor de instellingen voor naleving en past u deze toe op alle computers in uw hiërarchie. Als u wilt dat deze instellingen alleen van toepassing zijn op enkele computers, maakt u een aangepaste apparaatclientinstelling en wijst u deze toe aan een verzameling die de computers bevat waarvoor u de instellingen voor naleving wilt gebruiken. Zie voor meer informatie over het maken van aangepaste apparaatinstellingen [het configureren van clientinstellingen](../../core/clients/deploy/configure-client-settings.md).  

> [!TIP]  
>  Andere typen apparaten vereisen geen specifieke configuratie om de instellingen voor naleving te evalueren.  

1.  Klik in de Configuration Manager-console op **beheer** > **clientinstellingen** > **standaardinstellingen**.  
2.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  
3.  Klik in het dialoogvenster **Standaardinstellingen** op **Instellingen voor naleving**.  
4.  Configureer de volgende nalevingsinstellingen voor clients:
    - **Compatibiliteitsevaluatie op clients** -ingesteld op **True** als u wilt evalueren van naleving op clientapparaten.
    - **Compatibiliteitsevaluatie plannen** -Klik op **planning** als u wilt wijzigen van de planning voor nalevingsevaluatie standaard op clientapparaten.
    - **Gebruikersgegevens en -profielen inschakelen** -Schakel deze optie als u wilt maken en implementeren van de items voor gebruikersgegevens en profielen configuratie op Windows-computers. Zie voor meer informatie [gebruikersgegevens en profielen configuratie-items maken](/sccm/compliance/deploy-use/create-remote-connection-profiles).
5. Klik op **OK** om het dialoogvenster **Standaardinstellingen** te sluiten.  

De volgende keer dat clientcomputers clientbeleid downloaden, worden deze geconfigureerd met deze instellingen.  
