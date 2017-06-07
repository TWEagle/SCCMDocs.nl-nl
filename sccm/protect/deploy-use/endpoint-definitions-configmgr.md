---
title: Endpoint Protection-malware-definities | Microsoft-documenten
description: Informatie over het configureren van Configuration Manager-software-updates te leveren van definitie-updates op clientcomputers.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3b9c4027-a98b-406b-935c-ccabcfe713df
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: ca40c2c745ea516b56b637249b892cd44e570a9d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

#  <a name="using-configuration-manager-software-updates-to-deliver-definition-updates"></a>Met behulp van Configuration Manager-Software-Updates te leveren van definitie-Updates

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


 Hier kunt u Configuration Manager-software-updates te leveren van definitie-updates op clientcomputers. Dit doet u door regels voor automatische implementatie te configureren. Voordat u begint met het maken van regels voor automatische implementatie, zorg ervoor dat u Configuration Manager-software-updates hebt geconfigureerd. Zie voor meer informatie [Inleiding tot software-updates in System Center Configuration Manager](/sccm/sum/understand/software-updates-introduction).

> [!NOTE]
>  Deze procedure is alleen voor de items die specifiek voor Endpoint Protection moeten worden geconfigureerd. Zie voor meer informatie over de Wizard regel voor automatische implementatie maken [software-updates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="to-configure-an-automatic-deployment-rule-to-deliver-definition-updates"></a>Een regel voor automatische implementatie configureren voor het leveren van definitie-updates

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.

2.  Vouw **Software-updates** uit in de werkruimte **Softwarebibliotheek**en klik op **Regels voor automatische implementatie**.

3.  Klik op het tabblad **Start** in de groep **Maken** op **Regel voor automatische implementatie maken**.

4.  Geef op de pagina **Algemeen** van de **wizard Regel voor automatische implementatie maken**de volgende gegevens op:

    -   **Naam**: Geef een unieke naam voor de regel voor automatische implementatie.

    -   **Verzameling**: Selecteer de verzameling van clientcomputers die u wilt implementeren definitie-updates.

        > [!NOTE]
        >  U kunt geen definitie-updates implementeren voor een verzameling gebruikers.

5.  Klik op **Toevoegen aan bestaande software-updategroep**.

6.  Controleer of het selectievakje  **De implementatie inschakelen nadat deze regel is uitgevoerd** is ingeschakeld en klik vervolgens op **Volgende**.

7.  Selecteer op de pagina **Implementatie-instellingen** van de wizard, in de lijst **Detailniveau** de optie **Minimaal**en klik vervolgens op **Volgende**.

    > [!NOTE]
    >  Van de **detailniveau** selecteert **minimale** (Configuration Manager zonder servicepack) of **alleen foutberichten** (Configuration Manager). Zo beperkt u het aantal statusberichten dat wordt geretourneerd door de definitie-implementatie. Deze configuratie vermindert het CPU-gebruik voor verwerking op de Configuration Manager-servers.

8.  Schakel in de lijst **Eigenschapsfilters** het selectievakje **Updateclassificatie** in.

9. In de **zoekcriteria** weergeven, klikt u op **< items vinden\>**. Selecteer vervolgens in het dialoogvenster **Zoekcriteria** in de lijst **Geef de te zoeken waarde op** de optie **Definitie-updates**.

10. Klik op **OK** om het dialoogvenster **Zoekcriteria** te sluiten.

11. Schakel in de lijst **Eigenschapsfilters** het selectievakje **Product** in.

12. In de **zoekcriteria** weergeven, klikt u op **< items vinden\>**. Selecteer vervolgens in het dialoogvenster **Zoekcriteria** in de lijst **Geef de te zoeken waarde op** de optie **Forefront Endpoint Protection 2010** voor Windows 8.1 en oudere versies of **Windows Defender** voor Windows 10 en hoger.

13. Klik op **OK** om het dialoogvenster **Zoekcriteria** te sluiten en klik vervolgens op **Volgende**.

14. Schakel in de lijst **Eigenschapsfilters** het selectievakje **Vervangen** in.

15. In de **zoekcriteria** weergeven, klikt u op **< items vinden\>**. Selecteer vervolgens in het dialoogvenster **Zoekcriteria** in de lijst **Geef de te zoeken waarde op** de optie **Geen**.

16. Klik op **OK** om het dialoogvenster **Zoekcriteria** te sluiten en klik vervolgens op **Volgende**.

17. Selecteer op de pagina **Evaluatieschema** van de wizard de optie **De regel inschakelen zodat deze volgens een schema wordt uitgevoerd**en configureer vervolgens het schema volgens welke de definitie-updates moeten worden gedownload. Stel de regel zo in dat deze minimaal twee uur na de synchronisatie van elk software-updatepunt wordt uitgevoerd. Klik op **Volgende**.

18. Configureer op de pagina **Implementatieplanning** van de wizard de volgende instellingen:

    -   **Tijd op basis van**: Selecteer **UTC** als u wilt dat alle clients in de hiërarchie voor het installeren van de meest recente definities op hetzelfde moment. Het daadwerkelijke tijdstip kan maximaal twee uur variëren. Deze instelling wordt aanbevolen.

    -   **Tijd software beschikbaar**: Geef de beschikbare tijd voor de implementatie die door deze regel wordt gemaakt. Het opgegeven tijdstip moet ten minste één uur na de uitvoering van de regel voor automatische implementatie plaatsvinden. Dit zorgt ervoor dat er voldoende tijd is om de inhoud te repliceren naar de distributiepunten in uw hiërarchie. Sommige definitie-updates kunnen ook engine-updates voor anti-malware bevatten, waardoor het langer kan duren voordat de distributiepunten worden bereikt.

    -   **Installatiedeadline**: Selecteer **zo snel mogelijk**.

        > [!NOTE]
        >  Deadlines voor software-updates vinden verspreid over een periode van twee uur plaats zodat wordt voorkomen dat alle clients op hetzelfde moment een update aanvragen.

19. Klik op **Volgende**.

20. Selecteer op de pagina **Gebruikerservaring** van de wizard, in de lijst **Gebruikersmeldingen** , de optie **Verbergen in Software Center en alle meldingen**.   Dit zorgt ervoor dat de definitie-updates op de achtergrond worden geïnstalleerd. Klik op **Volgende**.

21. U hoeft op de pagina **Waarschuwingen** van de wizard geen waarschuwingen te configureren. Endpoint Protection in Configuration Manager genereert waarschuwingen die vereist zijn mogelijk. Klik op **Volgende**.

22. Selecteer op de pagina **Downloadinstellingen** van de wizard de wijze waarop de benodigde software-updates moeten worden gedownload en klik vervolgens op **Volgende**.

23. Selecteer op de pagina **Implementatiepakket** van de wizard een bestaand implementatiepakket of maak een nieuw implementatiepakket dat de software-updatebestanden bevat die aan de regel zijn gekoppeld.

    > [!NOTE]
    >  U kunt de definitie-updates het beste in een pakket opnemen dat geen andere software-updates bevat. Op die manier blijft de grootte van het definitie-updatepakket beperkt, waardoor het pakket sneller naar de distributiepunten kan worden gerepliceerd.

24. Selecteer op de pagina **Distributiepunten** van de wizard een of meer distributiepunten waarnaar u de inhoud voor dit pakket wilt kopiëren en klik vervolgens op **Volgende**.

25. Selecteer op de pagina **Downloadlocatie** van de wizard de optie **Software-updates downloaden vanaf internet**en klik vervolgens op **Volgende**.

26. Selecteer op de pagina **Taalselectie** van de wizard elke taalversie van de updates die moet worden gedownload en klik vervolgens op **Volgende**.

27. Voltooi de wizard Regel voor automatische implementaties maken.

28. Controleer of de nieuwe regel wordt weergegeven de **regels voor automatische implementatie** knooppunt van de Configuration Manager-console.


> [!div class="button"]
[Volgende stap >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Terug >](endpoint-configure-alerts.md)
