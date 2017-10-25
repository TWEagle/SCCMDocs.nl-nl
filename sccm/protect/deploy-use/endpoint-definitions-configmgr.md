---
title: Endpoint Protection-malwaredefinities | Microsoft Docs
description: Informatie over het configureren van Configuration Manager software-updates voor het leveren van definitie-updates aan clientcomputers.
ms.custom: na
ms.date: 10/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3b9c4027-a98b-406b-935c-ccabcfe713df
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: d2c29ea4c2b49142c6e63e2b5e829271098eac70
ms.sourcegitcommit: 8ac9c2c9ba1fdcbb7cc8d5be898586865fcf67c0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2017
---
#  <a name="using-configuration-manager-software-updates-to-deliver-definition-updates"></a>Met behulp van Configuration Manager Software-Updates te leveren van definitie-Updates

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 U kunt software-updates voor Configuration Manager voor het leveren van definitie-updates aan clientcomputers configureren. Dit doet u door regels voor automatische implementatie te configureren. Zorg voordat u begint met het maken van regels voor automatische implementatie, dat u software-updates voor Configuration Manager hebt geconfigureerd. Zie voor meer informatie [Inleiding tot software-updates in System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction).

> [!NOTE]
>  Deze procedure geldt alleen voor de items die specifiek voor Endpoint Protection moeten worden geconfigureerd. Zie voor meer informatie over de Wizard regel voor automatische implementatie maken [softwareupdates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="to-configure-an-automatic-deployment-rule-to-deliver-definition-updates"></a>Een regel voor automatische implementatie configureren voor het leveren van definitie-updates

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.

2.  Vouw **Software-updates** uit in de werkruimte **Softwarebibliotheek**en klik op **Regels voor automatische implementatie**.

3.  Klik op het tabblad **Start** in de groep **Maken** op **Regel voor automatische implementatie maken**.

4.  Geef op de pagina **Algemeen** van de **wizard Regel voor automatische implementatie maken**de volgende gegevens op:

    -   **Naam**: Voer een unieke naam voor de regel voor automatische implementatie.

    -   **Verzameling**: Selecteer de verzameling van clientcomputers die u wilt implementeren definitie-updates.

        > [!NOTE]
        >  U kunt geen definitie-updates implementeren voor een verzameling gebruikers.

5.  Klik op **Toevoegen aan bestaande software-updategroep**.

6.  Controleer of het selectievakje  **De implementatie inschakelen nadat deze regel is uitgevoerd** is ingeschakeld en klik vervolgens op **Volgende**.

7.  Selecteer op de pagina **Implementatie-instellingen** van de wizard, in de lijst **Detailniveau** de optie **Minimaal**en klik vervolgens op **Volgende**.

    > [!NOTE]
    >  Van de **detailniveau** selecteert **minimale** (Configuration Manager zonder servicepack) of **alleen foutberichten** (Configuration Manager). Zo beperkt u het aantal statusberichten dat wordt geretourneerd door de definitie-implementatie. Deze configuratie vermindert het CPU-gebruik voor verwerking op de Configuration Manager-servers.

8.  Schakel in de lijst **Eigenschapsfilters** het selectievakje **Updateclassificatie** in.

9. In de **zoekcriteria** lijst, klikt u op **< te zoeken items\>**. Selecteer vervolgens in het dialoogvenster **Zoekcriteria** in de lijst **Geef de te zoeken waarde op** de optie **Definitie-updates**.

10. Klik op **OK** om het dialoogvenster **Zoekcriteria** te sluiten.

11. Schakel in de lijst **Eigenschapsfilters** het selectievakje **Product** in.

12. In de **zoekcriteria** lijst, klikt u op **< te zoeken items\>**. Selecteer vervolgens in het dialoogvenster **Zoekcriteria** in de lijst **Geef de te zoeken waarde op** de optie **Forefront Endpoint Protection 2010** voor Windows 8.1 en oudere versies of **Windows Defender** voor Windows 10 en hoger.

13. Klik op **OK** om het dialoogvenster **Zoekcriteria** te sluiten en klik vervolgens op **Volgende**.

14. U kunt eventueel filteren vervangen updates.   Te doen:
  1.  Schakel in de lijst **Eigenschapsfilters** het selectievakje **Vervangen** in.
  2.  In de **zoekcriteria** lijst, klikt u op **< te zoeken items\>**. Selecteer vervolgens in het dialoogvenster **Zoekcriteria** in de lijst **Geef de te zoeken waarde op** de optie **Geen**.  <br><br>

15. Klik op **OK** om het dialoogvenster **Zoekcriteria** te sluiten en klik vervolgens op **Volgende**.

16. Selecteer op de pagina **Evaluatieschema** van de wizard de optie **De regel inschakelen zodat deze volgens een schema wordt uitgevoerd**en configureer vervolgens het schema volgens welke de definitie-updates moeten worden gedownload. Stel de regel zo in dat deze minimaal twee uur na de synchronisatie van elk software-updatepunt wordt uitgevoerd. Klik op **Volgende**.

17. Configureer op de pagina **Implementatieplanning** van de wizard de volgende instellingen:

    -   **Tijd is gebaseerd op**: Selecteer **UTC** als u wilt dat alle clients in de hiërarchie voor het installeren van de meest recente definities op hetzelfde moment. Het daadwerkelijke tijdstip kan maximaal twee uur variëren. Deze instelling wordt aanbevolen.

    -   **Tijd software beschikbaar**: Geef de beschikbare tijd voor de implementatie die door deze regel wordt gemaakt. Het opgegeven tijdstip moet ten minste één uur na de uitvoering van de regel voor automatische implementatie plaatsvinden. Dit zorgt ervoor dat er voldoende tijd is om de inhoud te repliceren naar de distributiepunten in uw hiërarchie. Sommige definitie-updates kunnen ook engine-updates voor anti-malware bevatten, waardoor het langer kan duren voordat de distributiepunten worden bereikt.

    -   **Installatiedeadline**: Selecteer **zo snel mogelijk**.

        > [!NOTE]
        >  Deadlines voor software-updates vinden verspreid over een periode van twee uur plaats zodat wordt voorkomen dat alle clients op hetzelfde moment een update aanvragen.

18. Klik op **Volgende**.

19. Selecteer op de pagina **Gebruikerservaring** van de wizard, in de lijst **Gebruikersmeldingen** , de optie **Verbergen in Software Center en alle meldingen**.   Dit zorgt ervoor dat de definitie-updates op de achtergrond worden geïnstalleerd. Klik op **Volgende**.

20. U hoeft op de pagina **Waarschuwingen** van de wizard geen waarschuwingen te configureren. Endpoint Protection in Configuration Manager genereert waarschuwingen die mogelijk vereist. Klik op **Volgende**.

21. Selecteer op de pagina **Downloadinstellingen** van de wizard de wijze waarop de benodigde software-updates moeten worden gedownload en klik vervolgens op **Volgende**.

22. Selecteer op de pagina **Implementatiepakket** van de wizard een bestaand implementatiepakket of maak een nieuw implementatiepakket dat de software-updatebestanden bevat die aan de regel zijn gekoppeld.

    > [!NOTE]
    >  U kunt de definitie-updates het beste in een pakket opnemen dat geen andere software-updates bevat. Op die manier blijft de grootte van het definitie-updatepakket beperkt, waardoor het pakket sneller naar de distributiepunten kan worden gerepliceerd.

23. Selecteer op de pagina **Distributiepunten** van de wizard een of meer distributiepunten waarnaar u de inhoud voor dit pakket wilt kopiëren en klik vervolgens op **Volgende**.

24. Selecteer op de pagina **Downloadlocatie** van de wizard de optie **Software-updates downloaden vanaf internet**en klik vervolgens op **Volgende**.

25. Selecteer op de pagina **Taalselectie** van de wizard elke taalversie van de updates die moet worden gedownload en klik vervolgens op **Volgende**.

26. Voltooi de wizard Regel voor automatische implementaties maken.

27. Controleer of de nieuwe regel wordt weergegeven de **regels voor automatische implementatie** knooppunt van de Configuration Manager-console.


> [!div class="button"]
[Volgende stap >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Terug >](endpoint-configure-alerts.md)
