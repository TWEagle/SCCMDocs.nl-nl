---
title: Algemene taken voor configuratiebasislijnen - Configuration Manager | Microsoft-documenten
description: Meer informatie over het maken en implementeren van configuratiebasislijnen System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bb6afeb-d267-4f9b-ade2-26e5400c223b
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 991eff171dce95590a7f050e0d3b07f98c0224b3
ms.openlocfilehash: 5682cacb43af5bf9248446f1c35b08f137bdae9d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="common-tasks-for-creating-and-deploying-configuration-baselines-with-system-center-configuration-manager"></a>Algemene taken voor het maken en implementeren van configuratiebasislijnen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat algemene scenario's voor meer informatie over het maken en implementeren van configuratiebasislijnen System Center Configuration Manager.  

 Als u al bekend met instellingen voor naleving bent, gedetailleerde documentatie over functies die u gebruikt kan worden gevonden in de [configuratiebasislijnen maken](../../compliance/deploy-use/create-configuration-baselines.md) en [configuratiebasislijnen implementeren](../../compliance/deploy-use/deploy-configuration-baselines.md) onderwerpen.  

 Lees voordat u begint [aan de slag met instellingen voor naleving in System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md) sommige basisbegrippen over compatibiliteitsinstellingen en ook lezen [plannen en configureren van instellingen voor naleving](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) voor het implementeren van alle vereiste onderdelen.  

## <a name="create-a-configuration-baseline"></a>Een configuratiebasislijn maken  
 In dit voorbeeld hebt u een configuratie-item gemaakt voor alleen Windows 10-computers waarop de Configuration Manager-client wordt uitgevoerd.  

 Dit configuratie-item dwingt een vereist wachtwoord op Windows 10-computers af van ten minste 6 tekens. De naam van het configuratie-item is **Windows 10-wachtwoordafdwinging**.  

In de volgende procedure wordt uitgelegd hoe u dit configuratie-item toevoegt aan een configuratiebasislijn om dit voor te bereiden op implementatie.  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **compatibiliteitsinstellingen** > **Configuratiebasislijnen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratiebasislijn maken**.  

4.  Configureer het volgende in het dialoogvenster **Configuratiebasislijn maken** :  

    -   **Naam** : voer **Windows 10-wachtwoorden** (of een andere naam van uw keuze) in  

5.  Klik op **Toevoegen** > **Configuratie-items**.  

6.  Selecteer in het dialoogvenster **Configuratie-items toevoegen** het configuratie-item **Windows 10-wachtwoordafdwinging** dat u eerder hebt gemaakt en klik op **Toevoegen**.  

7.  Klik op OK om het dialoogvenster **Configuratie-items toevoegen** te sluiten en keer terug naar het dialoogvenster **Configuratiebasislijn maken** , dat op deze schermafbeelding lijkt:  

     ![Dialoogvenster Configuratiebasislijn maken](/sccm/compliance/plan-design/media/Create-Configuration-Baseline.png)  

8.  Klik op **OK** om het dialoogvenster **Configuratiebasislijn maken** te sluiten.  

 Nu ziet u de configuratiebasislijn die u zojuist hebt gemaakt in de **Configuratiebasislijnen** knooppunt van de Configuration Manager-console.  

## <a name="deploy-the-configuration-baseline"></a>Implementeer de configuratiebasislijn  
 In dit voorbeeld implementeert u de configuratiebasislijn bij een verzameling computers die u in de vorige procedure hebt gemaakt.  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **compatibiliteitsinstellingen** > **Configuratiebasislijnen**.  

3.  Selecteer **Windows 10-wachtwoorden**in de lijst met configuratiebasislijnen.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

5.  Configureer het volgende in het dialoogvenster **Configuratiebasislijnen implementeren** :  

    -   **Geselecteerd configuratiebasislijnen** : zorg ervoor dat de configuratiebasislijn **Windows 10-wachtwoorden** automatisch aan deze lijst is toegevoegd.  

    -   **Herstellen van niet-compatibele regels, waar ondersteund** - Controleer dit selectievakje in om ervoor te zorgen dat, als de juiste instellingen zijn niet aanwezig op de apparaten uit de doelgroep en ze worden hersteld door Configuration Manager.  

    -   **Verzameling** : klik op **Bladeren** om de verzameling computers te kiezen waarop de configuratiebasislijn wordt beoordeeld of in verband met naleving wordt hersteld. In dit voorbeeld is de configuratiebasislijn geïmplementeerd in de ingebouwde verzameling **Alle desktop- en serverclients** .  

        > [!TIP]  
        >  Het is niet erg als uw verzameling computers of apparaten bevat waarop Windows 10 niet is geïnstalleerd. Zolang u ondersteunde platforms hebt geconfigureerd in het configuratie-item dat u hebt gemaakt, worden alleen Windows 10-computers op naleving beoordeeld.  

    -   Configureer indien dit is vereist het schema op basis waarvan de configuratiebasislijn wordt beoordeeld. Gebruik anders de standaardwaarde **7 dagen**.  

6.  Het dialoogvenster ziet er nu ongeveer als volgt uit:  

     ![Dialoogvenster configuratie van basislijnen implementeren](/sccm/compliance/plan-design/media/Deploy-configuration-baselines.png)  

7.  Klik op **OK** om het dialoogvenster **Configuratiebasislijnen implementeren** te sluiten en implementatie te maken.  

 Als u een beknopt overzicht van de nalevingsstatistieken voor deze implementatie wilt bekijken, klikt u in de werkruimte **Bewaking** op **Implementaties**. Onderaan in het scherm ziet u een grafiek met **nalevingsstatistieken** .  

 Zie voor meer informatie over het bewaken van configuratiebasislijnen, [instellingen voor naleving controleren](../../compliance/deploy-use/monitor-compliance-settings.md)  

