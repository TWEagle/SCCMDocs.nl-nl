---
title: Endpoint Protection-waarschuwingen configureren
titleSuffix: Configuration Manager
description: Informatie over het configureren van Endpoint Protection-waarschuwingen in System Center Configuration Manager.
ms.custom: na
ms.date: 03/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f504de3e-4caf-455c-80d7-a63f13f4c5d9
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 91df245565cfe99f79a18618d62c00f0cea579d2
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
#  <a name="configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Waarschuwingen voor Endpoint Protection in Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt Endpoint Protection-waarschuwingen configureren in Microsoft System Center Configuration Manager aan gebruikers met beheerdersrechten waarschuwen wanneer specifieke gebeurtenissen, zoals een malware-infectie in uw hiërarchie plaatsvinden. Meldingen worden weergeven in het dashboard Endpoint Protection in Configuration Manager-console in de **waarschuwingen** knooppunt van de **bewaking** werkruimte of kunnen worden verzonden naar de opgegeven gebruikers.

 Gebruik de volgende stappen en de aanvullende procedures in dit onderwerp om waarschuwingen te configureren voor Endpoint Protection in Configuration Manager.

> [!IMPORTANT]
>  U moet hebben de **beveiliging afdwingen** machtiging voor verzamelingen voor het configureren van Endpoint Protection-waarschuwingen.

## <a name="steps-to-configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Stappen voor het configureren van waarschuwingen voor Endpoint Protection in Configuration Manager

1.  Klik op **Activa en naleving**op de Configuration Manager-console.

2.  Klik op **Apparaatverzamelingen** in de werkruimte **Activa en naleving**.

3.  Selecteer in de lijst **Apparaatverzamelingen** de verzameling waarvoor u waarschuwingen wilt configureren en klik vervolgens op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.

    > [!NOTE]
    >  U kunt geen waarschuwingen voor gebruikersverzamelingen configureren.

4.  Op de **waarschuwingen** tabblad van de *< verzamelingsnaam\>***eigenschappen** dialoogvenster, **deze verzameling weergeven op het dashboard Endpoint Protection** als u details wilt bekijken over de anti-malwarebewerkingen voor deze verzameling in de **bewaking** werkruimte van de Configuration Manager-console.

    > [!NOTE]
    >  Deze optie is niet beschikbaar voor de verzameling **Alle systemen** .

5.  Op de **waarschuwingen** tabblad van de *< verzamelingsnaam\>***eigenschappen** in het dialoogvenster, klikt u op **toevoegen**.

6.  In de **nieuwe Verzamelingmeldingen toevoegen** het dialoogvenster de **een waarschuwing gegenereerd wanneer deze voorwaarden van toepassing** sectie, selecteert u de gewenste Configuration Manager worden gegenereerd wanneer de opgegeven Endpoint Protection-gebeurtenissen optreden en klik vervolgens op waarschuwingen **OK**.

7.  In de **voorwaarden** lijst met de **waarschuwingen** tabblad, selecteert u elke waarschuwing van Endpoint Protection en geef vervolgens de volgende gegevens:

    -   **Naam melding** : Accepteer de standaardnaam of voer een nieuwe naam voor de waarschuwing.

    -   **Ernst melding** - In de lijst, selecteert u het waarschuwingsniveau moet worden weergegeven in de Configuration Manager-console.

8.  Afhankelijk van de waarschuwing die u selecteert, geef de volgende aanvullende informatie:

    -   **Detectie van malware** -deze waarschuwing wordt gegenereerd als er malware wordt gedetecteerd op elke computer in de verzameling die u controleert. De **drempelwaarde voor de malwaredetectie** Hiermee geeft u de malwaredetectieniveaus aan deze waarschuwing wordt gegenereerd:

        -   **Hoge - alle detecties** -de waarschuwing wordt gegenereerd wanneer er een of meer computers in de opgegeven verzameling waarop eventueel malware is gedetecteerd, ongeacht welke actie nodig is de Endpoint Protection-client.

        -   **Gemiddeld: gedetecteerd, in behandeling zijnde actie** - de waarschuwing wordt gegenereerd wanneer er een of meer computers in de opgegeven verzameling waarop malware wordt gedetecteerd en moet u handmatig de malware verwijderen.

        -   **Laag: gedetecteerd, nog steeds actief** -de waarschuwing wordt gegenereerd wanneer er een of meer computers in de opgegeven verzameling malware wordt gedetecteerd en nog steeds actief is.

    -   **Uitbraak van malware** -deze waarschuwing wordt gegenereerd als de opgegeven malware wordt aangetroffen op een opgegeven percentage van computers in de verzameling die u controleert.

        -   **Percentage van computers waarop malware is gedetecteerd** -de waarschuwing wordt gegenereerd wanneer het percentage van computers met schadelijke software die is gedetecteerd in de verzameling die u opgeeft voor het percentage overschrijdt. Geef een percentage van **1** tot en met **99**op.

            > [!NOTE]
            >  Waarde voor het percentage is gebaseerd op het aantal computers in de verzameling, maar worden uitgesloten van computers waarop geen Configuration Manager-client is geïnstalleerd. Het percentage betreft computers waarop nog geen de Endpoint Protection-client is geïnstalleerd.

    -   **Herhaalde detectie van malware** -deze waarschuwing wordt gegenereerd als specifieke malware meer dan een opgegeven aantal keren gedurende een opgegeven aantal uren op de computers in de verzameling die u controleert wordt gedetecteerd. Geef de volgende gegevens op om deze waarschuwing te configureren:

        -   **Aantal keer dat de malware is gedetecteerd:** de waarschuwing wordt gegenereerd wanneer dezelfde malware meer dan het opgegeven aantal keren op computers in de verzameling wordt gedetecteerd. Geef een getal op van **2** tot en met **32**.

        -   **Interval voor detectie (uren):** Geef het detectie-interval (in uren) in het aantal malwaredetecties moet plaatsvinden. Geef een getal op van **1** tot en met **168**.

    -   **Meervoudige malwaredetectie** : deze waarschuwing wordt gegenereerd als meer dan een opgegeven aantal malwaretypen wordt gedetecteerd gedurende een opgegeven aantal uren op computers in de verzameling die u controleert. Geef de volgende gegevens op om deze waarschuwing te configureren:

        -   **Het aantal malwaretypen gedetecteerd:** De waarschuwing wordt gegenereerd wanneer het opgegeven aantal verschillende malwaretypen op computers in de verzameling worden gedetecteerd. Geef een getal op van **2** tot en met **32**.

        -   **Interval voor detectie (uren):** Geef het detectie-interval, in uren, waarin het aantal malwaredetecties moet plaatsvinden. Geef een getal op van **1** tot en met **168**.

9. Klik op **OK** sluiten de *< verzamelingsnaam\>***eigenschappen** in het dialoogvenster.  

## <a name="alert-for-outdated-malware-client"></a>Waarschuwing voor verouderde malware-client

U kunt een waarschuwing om ervoor te zorgen Endpoint Protection-clients zijn niet verouderde vanaf Configuration Manager versie 1702 kunt configureren. U kunt nu weergeven **Antimalware-clientversie** en **Status van Endpoint Protection-implementatie** door te gaan **activa en naleving** > **overzicht** > **apparaten** > **alle bureaubladen en Clients bedienen**. Bekijken om te controleren of een waarschuwing, **waarschuwingen** in de **bewaking** werkruimte. Als meer dan 20% van beheerde clients een verlopen versie van de antimalware-software, de versie van de Antimalware-client is verouderd waarschuwing wordt weergegeven. Deze waarschuwing niet wordt weergegeven op de **bewaking** > **overzicht** tabblad. Voor het bijwerken van verlopen antimalware-clients, moet u software-updates inschakelen voor anti-malware-clients.

Als u wilt configureren voor het percentage waarmee de waarschuwing wordt gegenereerd, vouw **bewaking** > **waarschuwingen** > **alle waarschuwingen**, dubbelklikt u op **Antimalware clients verouderd** en wijzig de **waarschuwing activeren als percentage van de beheerde clients met een verouderde versie van de antimalware-client is meer dan** optie.

> [!div class="button"]
[Volgende stap >](endpoint-definition-updates.md)

> [!div class="button"]
[Terug >](endpoint-protection-site-role.md)
