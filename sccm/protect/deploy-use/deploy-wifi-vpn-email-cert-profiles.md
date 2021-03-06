---
title: Wi-Fi, VPN, e-mail en certificaatprofielen implementeren
titleSuffix: Configuration Manager
description: Informatie over het implementeren van Wi-Fi, VPN, e-mail en certificaatprofielen in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3753608d-b539-44dc-8e3f-b631319e7687
caps.latest.revision: "5"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 7e6b0038b5164a43a3198274a863d53750828776
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="deploy-profiles-in-system-center-configuration-manager"></a>In System Center Configuration Manager-profielen implementeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Profielen moeten voor een of meer verzamelingen worden geïmplementeerd voordat ze kunnen worden gebruikt.  

 Gebruik de **Wi-Fi-profiel implementeren**, **VPN-profiel implementeren**, **Exchange ActiveSync-profiel implementeren**, of **Certificaatprofiel implementeren** in het dialoogvenster om de implementatie van deze profielen te configureren. Als onderdeel van de configuratie definieert u de verzameling waarnaar het profiel worden geïmplementeerd en opgeven hoe vaak het profiel wordt beoordeeld op naleving.  

> [!NOTE]  
>  Als u meerdere toegangsprofielen voor bedrijfsbronnen voor dezelfde gebruiker implementeert, gebeurt het volgende:  
>   
>  -   Als een conflicterende instelling een optionele waarde bevat, wordt deze niet naar het apparaat verzonden.  
> -   Als een conflicterende instelling een verplichte waarde bevat, wordt de standaardwaarde verzonden naar het apparaat. Als er geen standaardwaarde is, mislukt het gehele toegangsprofiel tot de bedrijfsbron. Als u bijvoorbeeld twee e-mailprofielen implementeert voor dezelfde gebruiker en de opgegeven waarden voor **Exchange ActiveSync-host** of **E-mailadres** verschillend zijn, mislukken beide e-mailprofielen omdat de instellingen verplicht zijn.  

> -   Voordat u certificaatprofielen kunt implementeren, moet u de infrastructuur configureren en certificaatprofielen maken. Zie de volgende onderwerpen voor meer informatie:  
>   
>  -   [Certificaatinfrastructuur configureren in System Center Configuration Manager](certificate-infrastructure.md)  
> -   [Het maken van certificaatprofielen in System Center Configuration Manager](create-certificate-profiles.md)    

> [!IMPORTANT]  
>  Wanneer de implementatie van een VPN-profiel wordt verwijderd, wordt het niet verwijderd van clientapparaten. Als u het profiel wilt verwijderen van apparaten, moet u het handmatig verwijderen.
>   

## <a name="deploying--profiles"></a>Profielen implementeren  


1.  Kies in de System Center Configuration Manager-console **activa en naleving**.  

2.  In de **activa en naleving** werkruimte Vouw **instellingen voor naleving**, vouw **toegang tot bedrijfsbronnen**, en kies vervolgens het juiste profieltype, zoals **Wi-Fi-profielen**.  

3.  Selecteer in de lijst met profielen het profiel dat u implementeren wilt, en klik vervolgens in de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.  

4.  Geef in het dialoogvenster profiel implementeren de volgende informatie:  

    -   **Verzameling** -Klik op **Bladeren** om de verzameling waar u wilt implementeren van het profiel te selecteren.  

    -   **Waarschuwing genereren** -Schakel deze optie om een waarschuwing die wordt gegenereerd als de naleving van het profiel kleiner dan een opgegeven percentage voor een opgegeven datum en tijd is te configureren. U kunt tevens opgeven of u een melding naar System Center Operations Manager wilt verzenden.  

    -   -   **Willekeurige vertraging (uren)**: (Alleen voor certificaatprofielen met instellingen voor Simple Certificate Enrollment Protocol) Hiermee geeft u een vertragingsvenster op om te voorkomen overmatige Network Device Enrollment Service. De standaardwaarde is **64** uur.  

    -   **Geef het evaluatieschema voor compatibiliteit op voor dit <type> profiel** -Geef de planning op waarmee het geïmplementeerde profiel wordt geëvalueerd op clientcomputers. U kunt een eenvoudig of aangepast schema opgeven.  

        > [!NOTE]  
        >  Het profiel wordt door de clientcomputers beoordeeld wanneer de gebruiker zich aanmeldt.  

5.  Klik op **OK** om het dialoogvenster te sluiten en de implementatie te maken.

### <a name="see-also"></a>Zie tevens  

[Wi-Fi, VPN en e-mailprofielen in System Center Configuration Manager controleren](monitor-wifi-email-vpn-profiles.md)

[Certificaatprofielen in System Center Configuration Manager controleren](monitor-certificate-profiles.md)
