---
title: Windows Firewall-beleid voor Endpoint Protection | Microsoft Docs
description: Informatie over het maken en implementeren van de firewall-beleid voor Endpoint Protection in System Center 2012 Configuration Manager.
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ecdfad1-6305-45a8-ae75-3f33b967cb8f
caps.latest.revision: "5"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: acd75a8b22d050970b8c1176f725ddb4445633aa
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="create-and-deploy-windows-firewall-policies-for-endpoint-protection-in-system-center-configuration-manager"></a>Maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Firewallbeleid voor Endpoint Protection in System Center 2012 Configuration Manager kunt u eenvoudige Windows Firewall-configuratie en onderhoudstaken uitvoeren op clientcomputers in uw hiërarchie. U kunt met de Windows Firewall-beleidsregels de volgende taken uitvoeren:  

-   Bepalen of Windows Firewall is in- of uitgeschakeld.  

-   Bepalen of binnenkomende verbindingen naar clientcomputers zijn toegestaan.  

-   Bepalen of gebruikers een melding ontvangen wanneer Windows Firewall een nieuw programma blokkeert.  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  In de **activa en naleving** werkruimte Vouw **Endpoint Protection**, en klik vervolgens op **Windows Firewall-beleid**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Windows Firewall-beleid maken**.  

4.  Geef op de pagina **Algemeen** van de **wizard Windows Firewall-beleid maken**een naam en eventueel een beschrijving voor dit firewallbeleid op en klik vervolgens op **Volgende**.  

5.  Configureer op de pagina **Profielinstellingen** van de wizard de volgende instellingen voor elk netwerkprofiel:  

    > [!IMPORTANT]  
    >  Als u Windows Firewall-instellingen wilt implementeren op computers met Windows Server 2008 en Windows Vista Service Pack 1, moet u eerst [hotfix KB971800](http://go.microsoft.com/fwlink/p/?LinkId=231239) op deze computers installeren.  

    > [!NOTE]  
    >  Raadpleeg de Windows-documentatie voor meer informatie over netwerkprofielen.  

    -   **Windows Firewall inschakelen**  

        > [!NOTE]  
        >  Als **Windows Firewall inschakelen** niet is ingeschakeld, zijn de andere instellingen op deze pagina van de wizard niet beschikbaar.  

    -   **Alle binnenkomende verbindingen blokkeren, inclusief verbindingen in de lijst met toegestane programma's**  

    -   **De gebruiker waarschuwen wanneer een nieuw programma door Windows Firewall wordt geblokkeerd**  

6.  Controleer welke acties moeten worden ondernomen op de pagina **Overzicht** van de wizard en voltooi de wizard.  

7.  Controleer of de nieuwe Windows Firewall-beleid wordt weergegeven in de lijst **Windows Firewall-beleid** .  

##  <a name="BKMK_Assign"></a> Een Windows Firewall-beleid implementeren  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  In de **activa en naleving** werkruimte Vouw **Endpoint Protection**, en klik vervolgens op **Windows Firewall-beleid**.  

3.  Selecteer in de lijst **Windows Firewall-beleid** het Windows Firewall-beleid dat u wilt implementeren.  

4.  Klik op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

5.  Geef in het dialoogvenster **Windows Firewall-beleid implementeren** de verzameling op waaraan u dit Windows Firewall-beleid wilt toewijzen en geef een toewijzingsplanning op. Het Windows Firewall-beleid evalueert de naleving door gebruik te maken van dit schema en configureert de Windows Firewall-instellingen op clients opnieuw zodat wordt voldaan aan het Windows Firewall-beleid.  

6.  Klik op **OK** om het dialoogvenster **Windows Firewall-beleid implementeren** te sluiten en het Windows Firewall-beleid te implementeren.  

    > [!IMPORTANT]  
    >  Wanneer u een Windows Firewall-beleid voor een verzameling implementeert, wordt dit beleid gedurende een periode van twee uur in willekeurige volgorde toegepast op computers om te voorkomen dat het netwerk wordt overspoeld.
