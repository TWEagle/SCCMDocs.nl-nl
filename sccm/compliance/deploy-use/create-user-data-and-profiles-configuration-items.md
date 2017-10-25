---
title: Gebruikersgegevens en profielen configuratie-items maken | Microsoft Docs
description: Configuratie-items en -profielen in System Center Configuration Manager voor het beheren van Mapomleiding, offlinebestanden en zwervende profielen gebruiken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9fcbcc81-cd6f-496e-b075-ef1afa2b8ccc
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 1b3b42fe0a39e5adfddebf73f4683e5a6c71cb1c
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="create-user-data-and-profiles-configuration-items-in-system-center-configuration-manager"></a>Gebruikersgegevens en profielen configuratie-items maken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruiker en -profielen configuratie-items in System Center Configuration Manager bevatten instellingen die u beheren kunnen, Mapomleiding, offlinebestanden en zwervende profielen op computers met Windows 8 en hoger voor gebruikers in uw hiërarchie. U kunt bijvoorbeeld:  

-   Leid de map Documenten van een gebruiker om naar een netwerkshare.  

-   Zorg ervoor dat opgegeven bestanden op het netwerk beschikbaar zijn op de computer van een gebruiker wanneer er geen netwerkverbinding beschikbaar is.  

-   Configureer welke bestanden in het zwervende profiel van een gebruiker worden gesynchroniseerd met een netwerkshare wanneer de gebruiker zich aan- of afmeldt.  

 In tegenstelling tot andere configuratie-items in Configuration Manager niet gebruikersgegevens toevoegen en configuratie-items aan een configuratiebasislijn dat u vervolgens implementeert profiel. In plaats daarvan implementeert u het configuratie-item rechtstreeks via het dialoogvenster **Configuratie-item voor gebruikersgegevens en -profielen implementeren** .  

> [!IMPORTANT]  
>  U kunt alleen configuratie-items voor gebruikersgegevens en -profielen implementeren naar gebruikersverzamelingen.  

## <a name="enable-user-data-and-profiles-for-compliance-settings"></a>Gebruikersgegevens en -profielen inschakelen voor instellingen voor naleving  
 Gebruik de volgende procedure om de standaardclientinstelling te configureren voor de instellingen voor de naleving van gebruikersgegevens en -profielen en die van toepassing zijn op alle computers in uw hiërarchie. Als u deze instellingen alleen wilt toepassen op bepaalde computers, maakt u een aangepaste apparaatclientinstelling en wijst u deze toe aan een verzameling waartoe de computers behoren waarvoor u de instellingen voor de naleving van de gebruikersgegeven en -profielen wilt gebruiken. Zie voor meer informatie over het maken van aangepaste apparaatinstellingen [het configureren van clientinstellingen](../../core/clients/deploy/configure-client-settings.md).  

1.  Klik in de Configuration Manager-console op **beheer** > **clientinstellingen** > **standaardinstellingen**.  

4.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  

5.  Klik in het dialoogvenster **Standaardinstellingen** op **Instellingen voor naleving**.  

6.  Selecteer in de vervolgkeuzelijst **Gebruikersgegevens en -profielen inschakelen** de optie **Ja**.  

7.  Klik op **OK** om het dialoogvenster **Standaardinstellingen** te sluiten.  

## <a name="create-a-user-data-and-profiles-configuration-item"></a>Maken van een item voor gebruikersgegevens en profielen configuratie  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **gebruikersgegevens en -profielen**.  

3.  Op het tabblad **Start** in de groep **Maken** klikt u op **Configuratie-item voor gebruikersgegevens en -profielen maken**.  

4.  Geef op de pagina **Algemeen** van de wizard **Configuratie-item voor gebruikersgegevens en -profielen maken**de volgende informatie op:  

    -   **Naam:** Voer een unieke naam voor het configuratie-item. U kunt maximaal 256 tekens gebruiken.  

    -   **Beschrijving:** Geef een beschrijving met een van de configuratie-item en andere relevante informatie die helpt overzicht bij het identificeren ervan in de Configuration Manager-console. U kunt maximaal 256 tekens gebruiken.  

    -   **Mapomleiding:** Schakel dit selectievakje in als u instellingen wilt configureren voor Mapomleiding voor dit configuratie-item.  

    -   **Offlinebestanden:** Schakel dit selectievakje in als u instellingen wilt configureren voor offlinebestanden voor dit configuratie-item.  

    -   **Zwervende gebruikersprofielen:** Schakel dit selectievakje in als u instellingen wilt configureren voor zwervende gebruikersprofielen voor dit configuratie-item.  

5.  Op de pagina **Mapomleiding** van de wizard **Configuratie-item voor gebruikersgegevens en -profielen maken**geeft u op hoe u Mapomleiding wilt beheren op clientcomputers van gebruikers die dit configuratie-item ontvangen. U kunt instellingen configureren voor elk apparaat waarbij de gebruiker zich aanmeldt of alleen voor de primaire apparaten van de gebruiker. Raadpleeg de Windows Server-documentatie voor meer informatie over mapomleiding.  

    > [!NOTE]  
    >  Deze pagina wordt alleen weergegeven als u dit selectievakje inschakelt **Mapomleiding** op de **algemene** pagina van de wizard.  

6.  Op de pagina **Offlinebestanden** van de wizard **Configuratie-item voor gebruikersgegevens en -profielen maken**kunt u offlinebestanden in- of uitschakelen voor gebruikers die dit configuratie-item ontvangen en kunt u instellingen configureren voor het gedrag van offlinebestanden. U kunt ook offlinebestanden opgeven die altijd beschikbaar zijn op een computer waarbij de gebruiker zich aanmeldt. Raadpleeg de Windows Server-documentatie voor meer informatie over offlinebestanden.  

    > [!NOTE]  
    >  Deze pagina wordt alleen weergegeven als u het selectievakje aangevinkt **offlinebestanden** op de **algemene** pagina van de wizard.  

7.  Op de pagina **Zwervende profielen** van de wizard **Configuratie-item voor gebruikersgegevens en -profielen maken**kunt u configureren of zwervende profielen beschikbaar zijn op computers waarbij de gebruiker zich aanmeldt en kunt u ook meer informatie configureren over de werking van deze profielen. Raadpleeg de Windows Server-documentatie voor meer informatie over zwervende profielen.  

    > [!NOTE]  
    >  Deze pagina wordt alleen weergegeven als u het selectievakje aangevinkt **zwervende gebruikersprofielen** op de **algemene** pagina van de wizard.  

8.  Voltooi de wizard.  

 Het nieuwe configuratie-item voor gebruikersgegevens en -profielen wordt weergegeven in het knooppunt **Gebruikersgegevens en -profielen** van de werkruimte **Activa en naleving** .  

## <a name="deploy-a-user-data-and-profiles-configuration-item"></a>Implementeren van een item voor gebruikersgegevens en profielen configuratie  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **gebruikersgegevens en -profielen**.  

3.  Selecteer het configuratie-item voor gebruikersgegevens en -profielen dat u wilt implementeren en klik vervolgens op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

4.  Geef in het dialoogvenster **Configuratie-item voor gebruikersgegevens en -profielen implementeren** de volgende informatie op.  

    -   **Verzameling** : klik op **Bladeren** om de gebruikersverzameling te selecteren waarvoor u het configuratie-item wilt implementeren.  

        > [!IMPORTANT]  
        >  U kunt alleen configuratie-items voor gebruikersgegevens en -profielen implementeren naar gebruikersverzamelingen.  

    -   **Regels die niet compliant zijn herstellen, waar ondersteund** : schakel deze optie in om automatisch regels te herstellen die als niet-compatibel op clientcomputers worden geëvalueerd.  

    -   **Herstel toestaan buiten het onderhoudsvenster** : Als er een onderhoudsvenster is geconfigureerd voor de verzameling waarnaar u het configuratie-item implementeert, schakelt u deze optie in om de waarde buiten het onderhoudsvenster te laten herstellen met de instellingen voor naleving. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Waarschuwing genereren** : Schakel deze optie in om een waarschuwing te configureren die wordt gegenereerd als de naleving van het configuratie-item op een opgegeven datum en tijd minder is dan een opgegeven percentage. U kunt tevens opgeven of u een melding naar System Center Operations Manager wilt verzenden.  

    -   **Geef het evaluatieschema voor compatibiliteit op voor dit configuratie-item** : Geef de planning op waarmee het geïmplementeerde configuratie-item wordt geëvalueerd op clientcomputers. U kunt een eenvoudige of een aangepaste planning opgeven.  

5.  Klik op **OK** om het dialoogvenster **Configuratie-item voor gebruikersgegevens en -profielen implementeren** te sluiten en de implementatie te maken.  

## <a name="monitor-a-user-data-and-profiles-configuration-item"></a>Een configuratie-item voor gebruikersgegevens en -profielen bewaken  
 U kunt dit type configuratie-item controleren op dezelfde manier als dat u andere instellingen voor naleving bewaken.  

 Zie voor meer informatie [instellingen voor naleving bewaken](../../compliance/deploy-use/monitor-compliance-settings.md).  
