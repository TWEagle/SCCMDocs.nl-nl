---

title: Configureren van Endpoint Protection | Microsoft-documenten
description: Informatie over het selecteren en configureren van methoden met Endpoint Protection in System Center Configuration Manager naar definities van schadelijke software up-to-date te houden op clientcomputers.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 537dd2a7-4e44-4877-b8dd-5e1499407f8d
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: b5da7900a4f8e2f330c4dcb2cac00b45099bd909
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017



---

#  <a name="configure-definition-updates-for-endpoint-protection"></a>Configuratie van definitie-Updates voor Endpoint Protection  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Met Endpoint Protection in System Center Configuration Manager, kunt u een van de verschillende beschikbare methoden voor definities van schadelijke software up-to-date te houden op clientcomputers in uw hiërarchie. U kunt deze methoden aan de hand van de informatie in dit onderwerp selecteren en configureren.

 Als u anti-malwaredefinities wilt bijwerken, kunt u een of meer van de volgende methoden gebruiken:

-   [Updates gedistribueerd van Configuration Manager](endpoint-definitions-configmgr.md) -deze methode maakt gebruik van Configuration Manager-software-updates definitie en engine-updates te leveren voor computers in uw hiërarchie.

-   [Updates gedistribueerd van Windows Server Update Services (WSUS)](endpoint-definitions-wsus.md) -deze methode maakt gebruik van uw WSUS-infrastructuur definitie en engine-updates te leveren op computers.

-   [Gedistribueerde updates van Microsoft Update](endpoint-definitions-microsoft-updates.md) -deze methode kan computers rechtstreeks verbinding maken met Microsoft Update om te downloaden van definitie en engine-updates. Deze methode kan nuttig zijn voor computers die niet vaak verbinding maken met het bedrijfsnetwerk.

-   [Gedistribueerde updates van Microsoft Malware Protection Center](endpoint-definitions-protection-center.md) -deze methode wordt definitie-updates downloaden van het Microsoft Malware Protection Center.

-   [Updates van UNC-bestandsshares](endpoint-definitions-network.md) -met deze methode kunt u de meest recente definitie en engine-updates opslaan naar een share op het netwerk. Clients krijgen vervolgens toegang tot het netwerk om de updates te installeren.

 U kunt meerdere definitie-updatebronnen configureren en de volgorde bepalen waarin deze worden beoordeeld en toegepast. Dit doet u in het dialoogvenster **Definitie-updatebronnen configureren** wanneer u een anti-malwarebeleid maakt.

> [!IMPORTANT]
>  Voor Windows 10-computers, moet u Endpoint Protection voor het bijwerken van definities van schadelijke software voor Windows Defender configureren.

## <a name="how-to-configure-definition-update-sources"></a>Definitie-updatebronnen configureren
 Gebruik de volgende procedure voor het configureren van de definitie-updatebronnen zodat deze kunnen worden gebruikt voor elk anti-malwarebeleid.

1.  Klik op **Activa en naleving**op de Configuration Manager-console.

2.  Vouw **Endpoint Protection** uit in de werkruimte **Activa en naleving**en klik vervolgens op **Anti-malwarebeleidsregels**.

3.  Open de eigenschappenpagina van het **standaard toegepaste anti-malwarebeleid** of maak een nieuw anti-malwarebeleid. Zie voor meer informatie over het maken van regels voor antimalwarebeleid [maken en implementeren van antimalware-beleidsregels voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).

4.  Klik in de sectie **Definitie-updates** van het dialoogvenster Eigenschappen anti-malware op **Bron instellen**.

5.  Selecteer in het dialoogvenster **Definitie-updatebronnen configureren** de bronnen die moeten worden gebruikt voor de definitie-updates. U kunt op **Omhoog** of **Omlaag** klikken om de volgorde waarin deze bronnen worden gebruikt te wijzigen.

6.  Klik op **OK** om het dialoogvenster **Definitie-updatebronnen configureren** te sluiten.

## <a name="configure-endpoint-protection-definitions"></a>Endpoint Protection-definities configureren

-   [Updates gedistribueerd van Configuration Manager](endpoint-definitions-configmgr.md) -deze methode maakt gebruik van Configuration Manager-software-updates definitie en engine-updates te leveren voor computers in uw hiërarchie.

-   [Updates gedistribueerd van Windows Server Update Services (WSUS)](endpoint-definitions-wsus.md) -deze methode maakt gebruik van uw WSUS-infrastructuur definitie en engine-updates te leveren op computers.

-   [Gedistribueerde updates van Microsoft Update](endpoint-definitions-microsoft-updates.md) -deze methode kan computers rechtstreeks verbinding maken met Microsoft Update om te downloaden van definitie en engine-updates. Deze methode kan nuttig zijn voor computers die niet vaak verbinding maken met het bedrijfsnetwerk.

-   Gedistribueerde updates van Microsoft Malware Protection Center - met deze methode wordt definitie-updates downloaden vanaf het Microsoft Malware Protection Center.

-   [Updates van UNC-bestandsshares](endpoint-definitions-network.md) -met deze methode kunt u de meest recente definitie en engine-updates opslaan naar een share op het netwerk. Clients krijgen vervolgens toegang tot het netwerk om de updates te installeren.

