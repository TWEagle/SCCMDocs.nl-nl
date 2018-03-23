---
title: Een gefaseerde implementatie voor een takenreeks maken
titleSuffix: System Center Configuration Manager
description: Gefaseerde implementaties voor takenreeksen maken
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b634ff68-b909-48d2-9e2c-0933486673c5
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 130d1f68638427e6ee71c5c8c9686e9050bff401
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="create-phased-deployments-for-a-task-sequence-with-system-center-configuration-manager"></a>Gefaseerde implementaties voor een takenreeks maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gefaseerde implementaties automatiseren een gecoördineerde, geordende rollout van een takenreeks in meerdere verzamelingen. U kunt gefaseerde implementaties maken met de standaardwaarde van twee fasen, of handmatig configureren van meerdere fasen. Gefaseerde implementatie van takenreeksen biedt geen ondersteuning voor PXE of media-installatie. 

>[!NOTE]
> Gefaseerde implementaties is een voorlopige versie-functie die is geïntroduceerd in Configuration Manager 1802. <!--1356837-->

## <a name="security-scope-and-log-file-information"></a>Bestandsgegevens beveiligingsbereik en logboekbestanden

**Beveiligingsbereik**:</br>
Implementaties die zijn gemaakt door gefaseerde implementaties zijn niet zichtbaar is voor iedereen die geen heeft de **alle** beveiligingsbereik.

**Logboekbestanden**: </br>
SMS_PhasedDeployment.log

## <a name="create-a-default-two-phased-deployment-for-a-task-sequence"></a>Een standaard twee fasen implementatie voor een takenreeks maken

Gebruik de volgende instructies voor het maken van een gefaseerde implementatie. 

1. In de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.

2. Met de rechtermuisknop op een bestaande takenreeks en selecteert u **gefaseerde implementatie maken**. 

3. Op de **algemene** tabblad, geef de gefaseerde implementatie een naam, beschrijving (optioneel) en selecteer **automatisch maken van een standaard twee fase implementatie**. 

4. Vul de **eerste verzameling** en **tweede collectie** velden. Selecteer **volgende**.

5. Op de **instellingen** tabblad, kiest u een optie voor elk van de schema-instellingen en selecteer **volgende** wanneer u klaar. 
    - **Criteria voor succes van de eerste fase.** 
        - **Verwerkingsfrequentie voor implementatie** -percentage van de apparaten die het proces voor de implementatie voor de criteria voor succes fase opgeven. 
    - **Voorwaarden voor de tweede fase van de implementatie na geslaagde van de eerste fase vanaf** (Kies een):
        - **In deze fase na een uitgestelde periode (in dagen) automatisch gestart** -het aantal dagen moet worden gewacht voordat u begint met de tweede fase na het succes van de eerste kiezen. 
        - **Handmatig starten van de tweede fase van de implementatie van** -tweede fase automatisch na succes van de eerste niet starten. Verlangen dat deze handmatig worden gestart. 
    - **De software te installeren wanneer een apparaat is gericht,** (Kies een):
        - **Zo spoedig mogelijk** -Hiermee stelt u de deadline voor installatie op het apparaat, zodra het apparaat is gericht.
        - **Tijd (ten opzichte van de tijd dat apparaat is gericht) deadline** -Sets vóór de deadline voor de installatie van een bepaald aantal dagen nadat het apparaat is gericht. 

6. Op de **fasen** en klik op de eerste fase vervolgens **bewerken**.  Geef **gebruikerservaring** zoals **gebruikersmeldingen** en **verwerking voor Windows Embedded-apparaten schrijffilters**. Klik op **Toepassen**.

7. Geef **distributiepunten** instellingen voor de hoofdactiviteit op de **distributiepunten** tabblad. Klik op **toepassen** en **OK**.        

8. Op de **fasen** tabblad, het bewerken van de tweede fase vormt voor **gebruikerservaring** en **distributiepunten**. Klik op **toepassen** en **OK**.

9. Bevestig uw selecties op de **samenvatting** tabblad en klik vervolgens op **volgende** en gaan via de wizard.

>[!WARNING]
>Gefaseerde implementaties krijgt u geen melding als een takenreeksimplementatie [met een hoog risico](/sccm/protect/understand/settings-to-manage-high-risk-deployments.md). 


## <a name="suspend-and-resume-phases-or-move-to-the-next-phase"></a>Onderbreken en hervatten fasen of verplaatsen naar de volgende fase
U moet soms handmatig een gefaseerde implementatie onderbreken, hervatten een onderbroken gefaseerde implementatie of verplaatsen naar de volgende fase. 

### <a name="move-to-the-next-phase"></a>Verplaatsen naar de volgende fase
Wanneer u de instelling selecteert **handmatig starten van de tweede fase van de implementatie van**, moet u de tweede fase start. Gebruik de volgende instructies voor het verplaatsen naar de tweede fase: 

1. Selecteer in de Configuration Manager-console **softwarebibliotheek**, vouw **besturingssystemen**, en klik op **Takenreeksen**.
2. Markeer de takenreeks wordt uitgevoerd.
3. Klik op de **gefaseerde implementatie** tabblad aan de onderkant van de console. 
4. Met de rechtermuisknop op de gefaseerde implementatie en selecteer **verplaatsen naar de volgende fase**.
![Onderbreken, hervatten of verplaatsen naar de volgende fase](media/Suspend-phased-deployment.PNG)

### <a name="suspend-or-resume-a-phased-deployment"></a>Onderbreken of hervatten van een gefaseerde implementatie
1. Selecteer in de Configuration Manager-console **softwarebibliotheek**, vouw **besturingssystemen**, en klik op **Takenreeksen**.
2. Markeer de takenreeks en klik op de **gefaseerde implementatie** tabblad aan de onderkant van de console. 
3. Selecteer de gefaseerde implementatie en klik op **onderbreken** of **hervatten** in het lint.

## <a name="next-steps"></a>Volgende stappen
[Een aangepaste takenreeks maken](create-a-custom-task-sequence.md) </br>
[Een takenreeks maken voor niet - besturingssysteemimplementaties](create-a-task-sequence-for-non-operating-system-deployments.md). 








