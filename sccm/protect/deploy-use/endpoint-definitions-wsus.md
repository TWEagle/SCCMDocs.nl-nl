---
title: Endpoint Protection-malwaredefinities van WSUS
titleSuffix: Configuration Manager
definition: Learn how to configure Windows Server Updates Services to auto-approve definition updates.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a34d9401-83e4-471d-8e23-b8042fc11c90
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: fcc0e1909705fb1954c58c438438792a4866d3bf
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-windows-server-update-services-wsus-for-configuration-manager"></a>Endpoint Protection-malware-definities te downloaden van Windows Server Update Services (WSUS) voor Configuration Manager inschakelen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Als u WSUS gebruikt om de anti-malwaredefinities up-to-date te houden, kunt u deze zo configureren dat de definitie-updates automatisch worden goedgekeurd. Hoewel met behulp van Configuration Manager software-updates, de aanbevolen methode is om definities up-to-date te houden, kunt u ook WSUS configureren als een methode voor het toestaan dat gebruikers om definitie-updates handmatig te starten. Gebruik de volgende procedures om WSUS te configureren als een definitie-updatebron.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-configuration-manager-software-updates"></a>Endpoint Protection-definitie-updates in Configuration Manager software-updates synchroniseren

1.  Klik op **Beheer**in de Configuration Manager-console.

2.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Sites**.

3.  Selecteer de site die het software-updatepunt bevat. Klik in de groep **Instellingen** op **Siteonderdelen configureren**en klik vervolgens op **Software-updatepunt**.

4.  Schakel op het tabblad **Classificaties** van het dialoogvenster **Eigenschappen van software-updatepuntcomponenten** het selectievakje **Definitie-updates** in.

5.  Geef de **producten** op die zijn bijgewerkt met WSUS:

    -   Voor Windows 8.1 en oudere versies: schakel op het tabblad **Producten** van het dialoogvenster **Eigenschappen van software-updatepuntcomponenten** het selectievakje **Forefront Endpoint Protection 2010** in.

    -   Voor Windows 10 en hoger: schakel op het tabblad **Producten** van het dialoogvenster **Eigenschappen van software-updatepuntcomponenten** de selectievakjes **Windows Defender** en **Windows Technical Preview 2** in.

6.  Klik op **OK** om het dialoogvenster **Eigenschappen van software-updatepuntcomponenten** te sluiten.

 Gebruik de volgende procedure voor het configureren van Endpoint Protection-updates wanneer de WSUS-server niet is geïntegreerd in uw Configuration Manager-omgeving.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus"></a>Definitie-updates van Endpoint Protection synchroniseren in zelfstandige WSUS

1.  Vouw in de WSUS-beheerconsole het knooppunt **Computers**uit, klik op **Opties**en vervolgens op **Producten en classificaties**.

2.  Geef de **producten** op die zijn bijgewerkt met WSUS:

    -   Voor Windows 8.1 en oudere versies: schakel op het tabblad **Producten** van het dialoogvenster **Eigenschappen van software-updatepuntcomponenten** het selectievakje **Forefront Endpoint Protection 2010** in.

    -   Voor Windows 10 en hoger: schakel op het tabblad **Producten** van het dialoogvenster **Eigenschappen van software-updatepuntcomponenten** de selectievakjes **Windows Defender** en **Windows Technical Preview 2** in.

3.  Schakel op het tabblad **Classificaties** van het dialoogvenster **Producten en classificaties** de selectievakjes **Definitie-updates** en **Updates** in.

## <a name="approving-definition-updates"></a>Definitie-updates goedkeuren
 Definitie-updates voor Endpoint Protection moeten worden goedgekeurd en gedownload naar de WSUS-server voordat ze worden aangeboden aan clients die aanvragen van de lijst met beschikbare updates. Clients maken verbinding met de WSUS-server om te controleren op de benodigde updates en vragen vervolgens de meest recent goedgekeurde definitie-updates aan.

### <a name="to-approve-definitions-and-updates-in-wsus"></a>Definities en updates in WSUS goedkeuren

1.  Klik in de WSUS-beheerconsole op **Updates**, en klik vervolgens op **Alle updates** of de categorie van updates die u wilt goedkeuren.

2.  Klik in de lijst met updates met de rechtermuisknop op de update of updates die u wilt goedkeuren voor installatie en klik vervolgens op **Goedkeuren**.

3.  Selecteer in het dialoogvenster **Updates goedkeuren** de computergroep waarvoor u de updates wilt goedkeuren en klik vervolgens op **Goedgekeurd voor installatie**.

 Naast de handmatige goedkeuring kunt u ook een automatische goedkeuringsregel voor definitie-updates instellen en updates van Endpoint Protection. Dit wordt WSUS configureren voor Endpoint Protection-definitie-updates gedownload door WSUS, automatisch worden goedgekeurd.

### <a name="to-configure-an-automatic-approval-rule"></a>Een automatische goedkeuringsregel configureren

1.  Klik in de WSUS-beheerconsole op **Opties**en klik vervolgens op **Automatische goedkeuringen**.

2.  Klik op het tabblad **Updateregels** op de optie **Nieuwe regel**.

3.  In de **regel toevoegen** dialoogvenster onder **stap 1: Selecteer eigenschappen**, selecteer de **wanneer een update zich in een specifieke categorie** selectievakje.

4.  Onder **stap 2: De eigenschappen bewerken**, klikt u op **een classificatie**.

5.  Schakel alle selectievakjes behalve **Definitie-updates**uit en klik vervolgens op **OK**.

6.  In de **regel toevoegen** dialoogvenster onder **stap 1: Selecteer eigenschappen**, selecteer de **wanneer een update zich in een specifiek product** selectievakje.

7.  Onder **stap 2: De eigenschappen bewerken**, klikt u op **een product**.

8.  Schakel alle selectievakjes behalve **Forefront Endpoint Protection** voor Windows 8.1 en oudere versies of **Windows Defender** voor Windows 10 en hoger uit en klik vervolgens op **OK**.

9. Onder **stap 3: Geef een naam**, voer een naam voor de regel en klik vervolgens op **OK**.

10. Schakel in het dialoogvenster **Automatische goedkeuringen** het selectievakje voor de nieuwe regel in en klik op **Regel uitvoeren**.

> [!NOTE]
>  Weiger oude definitie-updates zodat de prestaties van uw WSUS-server en clientcomputers optimaal zijn. Als u wilt dat deze taak wordt uitgevoerd, kunt u automatische goedkeuring voor revisies en automatische weigering van verlopen updates configureren. Zie het [Microsoft Knowledge Base-artikel 938947](http://go.microsoft.com/fwlink/p/?LinkId=204078)voor meer informatie.

> [!div class="button"]
[Volgende stap >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Terug >](endpoint-configure-alerts.md)
