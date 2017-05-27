---
title: Endpoint Protection-waarschuwingen configureren | Microsoft-documenten
description: Informatie over het configureren van Endpoint Protection waarschuwingen in System Center Configuration Manager.
ms.custom: na
ms.date: 03/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f504de3e-4caf-455c-80d7-a63f13f4c5d9
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 7f4329b289b606dee5bf31aad8207de52667229f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

#  <a name="configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Waarschuwingen voor Endpoint Protection in Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 U kunt Endpoint Protection waarschuwingen configureren in Microsoft System Center Configuration Manager gebruikers met beheerdersrechten te waarschuwen wanneer specifieke gebeurtenissen, zoals een malware-infectie in uw hiërarchie plaatsvinden. Meldingen weergeven in het dashboard Endpoint Protection in de Configuration Manager-console in de **waarschuwingen** knooppunt van de **bewaking** werkruimte of via e-mail kan worden verzonden naar opgegeven gebruikers.

 Gebruik de volgende stappen en de aanvullende procedures in dit onderwerp waarschuwingen voor Endpoint Protection in Configuration Manager configureren.

> [!IMPORTANT]
>  U moet hebben de **beveiliging afdwingen** machtiging voor verzamelingen Endpoint Protection-mailwaarschuwingen te configureren.

## <a name="steps-to-configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Stappen voor het configureren van waarschuwingen voor Endpoint Protection in Configuration Manager

1.  Klik op **Activa en naleving**op de Configuration Manager-console.

2.  Klik op **Apparaatverzamelingen** in de werkruimte **Activa en naleving**.

3.  Selecteer in de lijst **Apparaatverzamelingen** de verzameling waarvoor u waarschuwingen wilt configureren en klik vervolgens op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.

    > [!NOTE]
    >  U kunt geen waarschuwingen voor gebruikersverzamelingen configureren.

4.  Op de **waarschuwingen** tabblad van het *< Collectienaam\>***eigenschappen** in het dialoogvenster Selecteer **deze verzameling weergeven in het dashboard Endpoint Protection** als u wilt weergeven van informatie over antimalware-bewerkingen voor deze verzameling in de **bewaking** werkruimte van de Configuration Manager-console.

    > [!NOTE]
    >  Deze optie is niet beschikbaar voor de verzameling **Alle systemen** .

5.  Op de **waarschuwingen** tabblad van het *< Collectienaam\>***eigenschappen** in het dialoogvenster, klikt u op **toevoegen**.

6.  In de **nieuwe Verzamelingmeldingen toevoegen** het dialoogvenster de **een waarschuwing gegenereerd wanneer deze voorwaarden van toepassing** sectie, selecteert u de gewenste Configuration Manager worden gegenereerd wanneer de opgegeven Endpoint Protection-gebeurtenissen optreden en klik vervolgens op waarschuwingen **OK**.

7.  In de **voorwaarden** lijst met de **waarschuwingen** tabblad elke waarschuwing van Endpoint Protection, en selecteer vervolgens de volgende informatie opgeven:

    -   **Naam melding** : Accepteer de standaardnaam of voer een nieuwe naam voor de waarschuwing.

    -   **Ernst melding** - In de lijst selecteert u de ernst om weer te geven in de Configuration Manager-console.

8.  Afhankelijk van de waarschuwing die u selecteert, geef de volgende aanvullende informatie:

    -   **Detectie van malware** -deze waarschuwing wordt gegenereerd als er malware wordt gedetecteerd op een computer in de verzameling die u wilt bewaken. De **drempelwaarde voor detectie van Malware** Hiermee geeft u de detectie van malware niveaus op deze waarschuwing wordt gegenereerd:

        -   **Hoge - alle detecties** -de waarschuwing wordt gegenereerd wanneer er een of meer computers in de opgegeven verzameling waarop schadelijke software is gedetecteerd, ongeacht welke actie wordt de Endpoint Protection-client.

        -   **Gemiddelde - gedetecteerde in behandeling zijnde actie** - de waarschuwing wordt gegenereerd wanneer er een of meer computers in de opgegeven verzameling waarop schadelijke software wordt gedetecteerd en moet u handmatig de malware verwijderen.

        -   **Lage - gedetecteerde, nog steeds actief** -de waarschuwing wordt gegenereerd wanneer er een of meer computers in de opgegeven verzameling op welke schadelijke software wordt gedetecteerd en nog steeds actief is.

    -   **Uitbraak van malware** -deze waarschuwing wordt gegenereerd als de opgegeven is malware gedetecteerd op een gespecificeerd percentage van computers in de verzameling die u wilt bewaken.

        -   **Percentage van computers waarop malware is aangetroffen** -de waarschuwing wordt gegenereerd wanneer het percentage van computers met malware die in de verzameling wordt gedetecteerd die u opgeeft voor het percentage overschrijdt. Geef een percentage van **1** tot en met **99**op.

            > [!NOTE]
            >  De waarde voor het percentage is gebaseerd op het aantal computers in de verzameling, maar sluit u de computers waarop geen Configuration Manager-client geïnstalleerd. Het bevat computers die u nog geen de Endpoint Protection-client is geïnstalleerd hebt.

    -   **Herhaalde detectie van malware** -deze waarschuwing wordt gegenereerd als specifieke malware is aangetroffen, meer dan een opgegeven aantal keren gedurende een opgegeven aantal uren op de computers in de verzameling die u wilt bewaken. Geef de volgende gegevens op om deze waarschuwing te configureren:

        -   **Aantal keer dat de malware is gedetecteerd:** de waarschuwing wordt gegenereerd wanneer dezelfde malware meer dan het opgegeven aantal keren op computers in de verzameling wordt gedetecteerd. Geef een getal op van **2** tot en met **32**.

        -   **Interval voor detectie (uur):** Geef het detectie-interval (in uren) in het aantal malware-detectie moet plaatsvinden. Geef een getal op van **1** tot en met **168**.

    -   **Detectie van verschillende malware** : deze waarschuwing wordt gegenereerd als meer dan een opgegeven aantal typen schadelijke software worden gedetecteerd via een opgegeven aantal uren op computers in de verzameling die u wilt bewaken. Geef de volgende gegevens op om deze waarschuwing te configureren:

        -   **Het aantal gedetecteerde malwaretypen:** De waarschuwing wordt gegenereerd wanneer het opgegeven aantal malwaretypen van verschillende gedetecteerd op computers in de verzameling. Geef een getal op van **2** tot en met **32**.

        -   **Interval voor detectie (uur):** Geef de detectie-interval, in uren, waarin het aantal malware-detectie moet plaatsvinden. Geef een getal op van **1** tot en met **168**.

9. Klik op **OK** sluit de *< Collectienaam\>***eigenschappen** in het dialoogvenster.  

## <a name="alert-for-outdated-malware-client"></a>Waarschuwing voor verouderde malware-client

Beginnend met Configuration Manager versie 1702, kunt u een waarschuwing om ervoor te zorgen Endpoint Protection-clients niet verouderd zijn. U kunt nu weergeven **Antimalware-clientversie** en **Status van Endpoint Protection-implementatie** door te gaan **activa en naleving** > **overzicht** > **apparaten** > **alle bureaubladen en Clients bedienen**. Weergeven om te controleren of er een waarschuwing, **waarschuwingen** in de **bewaking** werkruimte. Als meer dan 20% van beheerde clients worden met een verlopen versie van antimalware-software, de versie van de client anti-malware is verouderd waarschuwing wordt weergegeven. Deze waarschuwing niet wordt weergegeven in de **bewaking** > **overzicht** tabblad. Inschakelen voor het bijwerken van verlopen antimalware-clients, software-updates voor antimalware-clients.

Om te configureren voor het percentage waarmee de waarschuwing is gegenereerd, vouw **bewaking** > **waarschuwingen** > **alle waarschuwingen**, dubbelklikt u op **Antimalware clients verouderd** en wijzig de **waarschuwing activeren als percentage van de beheerde clients met een verouderde versie van de client antimalware is meer dan** optie.

> [!div class="button"]
[Volgende stap >](endpoint-definition-updates.md)

> [!div class="button"]
[Terug >](endpoint-protection-site-role.md)

