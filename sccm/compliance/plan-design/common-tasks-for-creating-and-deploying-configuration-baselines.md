---
title: 'Algemene taken voor configuratiebasislijnen '
titleSuffix: Configuration Manager
description: Meer informatie over het maken en implementeren van configuratiebasislijnen voor System Center Configuration Manager.
ms.custom: na
ms.date: 07/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bb6afeb-d267-4f9b-ade2-26e5400c223b
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 50f7bdf4dc537f734864304d96566347e6341de6
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="common-tasks-for-creating-and-deploying-configuration-baselines-with-system-center-configuration-manager"></a>Algemene taken voor het maken en implementeren van configuratiebasislijnen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat algemene scenario's waarmee u meer informatie over het maken en implementeren van configuratiebasislijnen voor System Center Configuration Manager.  

 Als u al bekend met instellingen voor naleving bent, vindt u gedetailleerde informatie over de functies die u in de [configuratiebasislijnen maken](../../compliance/deploy-use/create-configuration-baselines.md) en [configuratiebasislijnen implementeren](../../compliance/deploy-use/deploy-configuration-baselines.md) onderwerpen.  

 Lees voordat u begint, [aan de slag met instellingen voor naleving in System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md) basisinformatie over de instellingen voor naleving en ook lezen [plannen en configureren van instellingen voor naleving](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) voor het implementeren van alle benodigde voorwaarden.  

## <a name="create-a-configuration-baseline"></a>Een configuratiebasislijn maken  
 In dit voorbeeld hebt u een configuratie-item gemaakt voor Windows 10-computers waarop de Configuration Manager-client wordt uitgevoerd.  

 Dit configuratie-item dwingt een vereist wachtwoord op Windows 10-computers af van ten minste 6 tekens. De naam van het configuratie-item is **Windows 10-wachtwoordafdwinging**.  

Gebruik de volgende procedure voor meer informatie over dit configuratie-item toevoegen aan een configuratiebasislijn te stellen voor implementatie.  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Configuratiebasislijnen**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratiebasislijn maken**.  

4.  In de **Configuratiebasislijn maken** dialoogvenster Configureer de volgende instellingen:  

    -   **Naam** : voer **Windows 10-wachtwoorden** (of een andere naam van uw keuze) in  

5.  Klik op **Toevoegen** > **Configuratie-items**.  

6.  Selecteer in het dialoogvenster **Configuratie-items toevoegen** het configuratie-item **Windows 10-wachtwoordafdwinging** dat u eerder hebt gemaakt en klik op **Toevoegen**.  

7.  Klik op OK voor sluiten de **configuratie-Items toevoegen** in het dialoogvenster en keer terug naar de **Configuratiebasislijn maken** in het dialoogvenster.

8.  Klik op **OK** om het dialoogvenster **Configuratiebasislijn maken** te sluiten.  

 U ziet nu de configuratiebasislijn in de **Configuratiebasislijnen** knooppunt van de Configuration Manager-console.  

## <a name="deploy-the-configuration-baseline"></a>Implementeer de configuratiebasislijn  
 In dit voorbeeld moet u de configuratiebasislijn die u hebt gemaakt in de vorige procedure om een verzameling computers te implementeren.  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **Configuratiebasislijnen**.  

3.  Selecteer **Windows 10-wachtwoorden**in de lijst met configuratiebasislijnen.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

5.  In de **Configuratiebasislijnen implementeren** dialoogvenster Configureer de volgende instellingen:  

    -   **Geselecteerd configuratiebasislijnen** : zorg ervoor dat de configuratiebasislijn **Windows 10-wachtwoorden** automatisch aan deze lijst is toegevoegd.  

    -   **Herstellen, waar ondersteund** : Schakel dit selectievakje in om ervoor te zorgen dat de juiste instellingen zijn niet aanwezig op de doelapparaten en klik vervolgens zij door Configuration Manager zijn hersteld.  

    -   **Verzameling** -Klik op **Bladeren** kiezen van de verzameling van computers waarop de configuratiebasislijn wordt geëvalueerd en hersteld op naleving. In dit voorbeeld is de configuratiebasislijn geïmplementeerd in de ingebouwde verzameling **Alle desktop- en serverclients** .  

        > [!TIP]  
        >  Het is niet erg als uw verzameling computers of apparaten bevat waarop Windows 10 niet is geïnstalleerd. Zolang u ondersteunde platforms hebt geconfigureerd in de configuratie-item dat u hebt gemaakt, worden alleen Windows 10-computers op compatibiliteit geëvalueerd.  

    -   Configureer zo nodig de planning op waarmee de configuratiebasislijn wordt geëvalueerd. Gebruik anders de standaardwaarde **7 dagen**.  

7.  Klik op **OK** om het dialoogvenster **Configuratiebasislijnen implementeren** te sluiten en implementatie te maken.  

 Als u een beknopt overzicht van de nalevingsstatistieken voor deze implementatie wilt bekijken, klikt u in de werkruimte **Bewaking** op **Implementaties**. Aan de onderkant van het scherm ziet u een **Nalevingsstatistieken** grafiek.  

## <a name="next-steps"></a>Volgende stappen 

Zie voor meer informatie over het bewaken van configuratiebasislijnen, [instellingen voor naleving bewaken](../../compliance/deploy-use/monitor-compliance-settings.md).  
