---
title: Integratie met Windows Update voor bedrijven in Windows 10
titleSuffix: Configuration Manager
description: Gebruik Windows Update voor bedrijven naar Windows 10-apparaten in uw organisatie up-to-date te houden voor apparaten die zijn verbonden met de service Windows Update.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
ms.openlocfilehash: e27e5f043af28b74369f21d19e5b20e19572213a
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Integratie met Windows Update voor bedrijven in Windows 10

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Windows Update voor bedrijven (WUfB) kunt u Windows 10-apparaten in uw organisatie altijd up-to-date houden met de meest recente beveiligingen en Windows-onderdelen wanneer deze apparaten rechtstreeks verbinding met de service Windows Update (WU maken). Configuration Manager kan onderscheid maken tussen Windows 10-computers die gebruikmaken van WUfB en WSUS voor het ophalen van software-updates.  

 Sommige functies van Configuration Manager zijn niet meer beschikbaar wanneer Configuration Manager-clients zijn geconfigureerd om updates te ontvangen van WU, waaronder WUfB of Windows Insiders:  

-   Windows Update-nalevingsrapportages:  

    -   Configuration Manager worden niet op de hoogte van de updates die WU worden gepubliceerd. De Configuration Manager-clients geconfigureerd updates ontvangen van WU, ziet u **onbekende** voor deze updates in de Configuration Manager-console.  

    -   Het oplossen van de algehele compatibiliteitsstatus is lastig omdat **onbekende** status is alleen voor clients waarvoor de status van de scan van WSUS hadn't gerapporteerd. Nu omvat het ook Configuration Manager-clients die updates van WU ontvangen.  

    -   Voorwaardelijke toegang (voor bedrijfsresources) op basis van status van de Updatevereisten werkt niet zoals verwacht voor clients die updates van WU ontvangen, omdat deze nooit voldoen aan de naleving van Configuration Manager.  

    -   Compatibiliteit met definitie-updates maakt deel uit van de algehele rapportage voor updatecompatibiliteit en werkt ook niet zoals verwacht.  Compatibiliteit met definitie-updates maakt ook deel uit van de evaluatie voor voorwaardelijke toegang  

-   Algehele retourneert rapportage van Endpoint Protection voor Defender op basis van status van de Updatevereisten geen nauwkeurige resultaten vanwege de ontbrekende Scangegevens.  

-   Configuration Manager niet worden Microsoft-updates, zoals Office, Internet Explorer en Visual Studio implementeert op clients die zijn verbonden met WUfB voor het ontvangen van updates.  

-   Configuration Manager zich niet kunnen worden geïmplementeerd 3e updates van derden die zijn gepubliceerd in WSUS en via Configuration Manager worden beheerd voor clients die zijn verbonden met WUfB voor het ontvangen van updates.  

-   Configuration Manager volledige clientimplementatie die gebruikmaakt van de infrastructuur van het software-updates, werkt niet voor clients die zijn verbonden met WUfB voor het ontvangen van updates.  

## <a name="identify-clients-that-use-wufb-for-windows-10-updates"></a>Clients identificeren die gebruikmaken van WUfB voor Windows 10-updates  
 Gebruik de volgende procedure om clients die gebruikmaken van WUfB voor Windows 10-updates en upgrades te identificeren. Vervolgens deze clients configureren voor WSUS niet meer gebruiken om updates te downloaden en implementeren van een clientagentinstelling voor het uitschakelen van de werkstroom voor software-updates voor deze clients.  

 **Vereisten**  

-   Clients met Windows 10 Desktop Pro of Windows 10 Enterprise Edition versie 1511 of hoger  

-   [Windows Update voor bedrijven](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) wordt geïmplementeerd en clients gebruiken WUfB om Windows 10-updates en -upgrades op te halen.  

#### <a name="to-identify-clients-that-use-wufb"></a>Clients identificeren die gebruikmaken van WUfB  

1.  De Windows Update Agent uitschakelen zodat deze niet bij WSUS scant, als dit eerder is ingeschakeld. De volgende registersleutel kan worden ingesteld om aan te geven of de computer bij WSUS of Windows Update scant.  Wanneer de waarde 2 is, wordt het niet gescand ten opzichte van WSUS.  
    - **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer**

2.  Er is een nieuw kenmerk **UseWUServer**onder de **Windows Update** knooppunt in de Configuration Manager Resource Explorer.  

3.  Maak een verzameling op basis van het **UseWUServer** -kenmerk voor alle computers die via WUfB zijn verbonden voor updates en upgrades.  

4.  Maak een clientagentinstelling voor het uitschakelen van de werkstroom voor software-updates. Implementeer de instelling aan de verzameling van computers die rechtstreeks zijn verbonden met WUfB.  

5.  De computers die via WUfB worden beheerd, ziet u **onbekende** in de compatibiliteitsstatus en worden niet geteld als onderdeel van het algehele compatibiliteitspercentage.  

## <a name="configure-windows-update-for-business-deferral-policies"></a>Windows Update voor bedrijven uitgestelde beleid configureren
<!-- 1290890 -->
Vanaf Configuration Manager versie 1706, kunt u uitgestelde beleidsregels voor Windows 10-functie-Updates of Quality-Updates voor Windows 10-apparaten rechtstreeks beheerd door Windows Update voor bedrijven configureren. U kunt de uitgestelde beleidsregels beheren in de nieuwe **Windows Update voor bedrijven-beleid** knooppunt onder **softwarebibliotheek** > **onderhoud van Windows 10**.

>[!NOTE] 
>U kunt vanaf Configuration Manager versie 1802 kan uitgestelde beleid instellen voor Windows insiders. <!--507201-->Zie voor meer informatie over het Windows Insider-programma [aan de slag met Windows Insider-programma voor bedrijven](https://docs.microsoft.com/windows/deployment/update/waas-windows-insider-for-business).

### <a name="prerequisites"></a>Vereisten
Windows 10-apparaten worden beheerd door Windows Update voor bedrijven moeten verbinding met Internet hebben.

#### <a name="to-create-a-windows-update-for-business-deferral-policy"></a>Een Windows Update voor bedrijven uitgestelde-beleid maken
1. In **softwarebibliotheek** > **onderhoud van Windows 10** > **Windows Update voor bedrijven-beleid**
2. Op de **Start** tabblad, in de **maken** Selecteer **Windows Update voor bedrijven-beleid maken** openen van de Update voor Windows maken voor Wizard beleid voor bedrijven.
3. Op de **algemene** pagina, Geef een naam en beschrijving voor het beleid.
4. Op de **uitgestelde beleid** pagina, configureren of uit te stellen of onderbreken van de functie-Updates. Functie-Updates zijn in het algemeen nieuwe functies voor Windows. Na het configureren van de **niveau van de gereedheid van de vertakking** instellen, kunt u opgeven of en hoe lang u wilt stellen functie-Updates na de beschikbaarheid van Microsoft ontvangen.
    - **Niveau van de gereedheid van de vertakking**: Stel de vertakking waarvoor u het apparaat ontvangt updates voor Windows (huidige vertakking of Current Branch for Business).
    - **Uitgestelde periode (dagen)**:  Geef het aantal dagen waarvoor de functie-Updates worden uitgesteld. Deze functie-Updates ontvangen voor een periode van 180 dagen na de release kan uit te stellen.
    - **Onderbreken functies Updates vanaf**: Selecteer of onderbreken apparaten functie-Updates ontvangen voor een periode van 60 dagen vanaf het moment dat u de updates wilt onderbreken. Nadat het maximum aantal dagen zijn verstreken, onderbreken functionaliteit verloopt automatisch en het apparaat Windows-Updates voor de betreffende updates scant. U kunt de updates opnieuw onderbreken na deze scan. U kunt de functie-Updates weer hervatten door het selectievakje uit te schakelen.   
5. Kies of u wilt stellen of onderbreken Quality-Updates. Quality-Updates zijn meestal oplossingen en verbeteringen in bestaande Windows-functionaliteit en normaal gesproken de eerste dinsdag van elke maand worden gepubliceerd, maar kunnen worden vrijgegeven op elk gewenst moment door Microsoft. U kunt definiëren als en hoe lang u wilt stellen Quality-Updates beschikbaar zijn na ontvangen.
    - **Uitgestelde periode (dagen)**: Geef het aantal dagen waarvoor de functie-Updates worden uitgesteld. Deze functie-Updates ontvangen voor een periode van 180 dagen na de release kan uit te stellen.
    - **Onderbreken Quality-Updates vanaf**: Selecteer of onderbreken van apparaten uit ontvangt Quality-Updates voor een periode van maximaal 35 dagen vanaf het moment dat u de updates wilt onderbreken. Nadat het maximum aantal dagen zijn verstreken, onderbreken functionaliteit verloopt automatisch en het apparaat Windows-Updates voor de betreffende updates scant. U kunt de updates opnieuw onderbreken na deze scan. U kunt Updates kwaliteit hervatten door het selectievakje uit te schakelen.
6. Selecteer **installeren van updates van andere Microsoft-Products** waarmee de instelling voor Groepsbeleid die uitgestelde instellingen van toepassing op Microsoft Update, evenals de Windows-Updates.
7. Selecteer **bevat de stuurprogramma's met Windows Update** automatisch bijwerken van stuurprogramma's van Windows-Updates. Als u deze instelling uitschakelt, worden updates voor stuurprogramma's niet uit de Windows-Updates gedownload.
8. Voltooi de wizard om de nieuwe uitgestelde-beleid te maken.

#### <a name="to-deploy-a-windows-update-for-business-deferral-policy"></a>Een Windows Update voor bedrijven uitgestelde beleid implementeren
1. In **softwarebibliotheek** > **onderhoud van Windows 10** > **Windows Update voor bedrijven-beleid**
2. Op de **Start** tabblad, in de **implementatie** Selecteer **Windows Update voor bedrijven-beleid implementeren**.
3. Configureer de volgende instellingen:
    - **Configuratiebeleid implementeren**: Selecteer de Windows Update voor bedrijven-beleid dat u wilt implementeren.
    - **Verzameling**: Klik op **Bladeren** om de verzameling waar u het beleid implementeren selecteren.
    - **Herstellen, waar ondersteund**: Selecteer alle regels die niet compatibel voor Windows Management Instrumentation (WMI), het register, scripts en alle instellingen voor mobiele apparaten die zijn ingeschreven door Configuration Manager zijn automatisch oplossen.
    - **Herstel toestaan buiten het onderhoudsvenster**: Als een onderhoudsvenster is geconfigureerd voor de verzameling waarnaar u het beleid implementeert, moet u deze optie zodat de instellingen voor naleving herstellen van de waarde buiten het onderhoudsvenster inschakelen. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](/sccm/core/clients/manage/collections/use-maintenance-windows).
    - **Waarschuwing genereren**: Hiermee configureert u een waarschuwing die wordt gegenereerd als de naleving van de configuratiebasislijn kleiner dan een opgegeven percentage voor een opgegeven datum en tijd is. U kunt tevens opgeven of u een melding naar System Center Operations Manager wilt verzenden.
    - **Willekeurige vertraging (uren)**: Hiermee geeft u een vertragingsvenster op om te voorkomen overmatige Network Device Enrollment Service. De standaardwaarde is 64 uur.
    - **Planning**: Geef het evaluatieschema voor compatibiliteit op waarmee het geïmplementeerde profiel wordt beoordeeld op clientcomputers. U kunt een eenvoudig of aangepast schema opgeven. Het profiel wordt door de clientcomputers beoordeeld wanneer de gebruiker zich aanmeldt.
4.  Voltooi de wizard voor het implementeren van het profiel.
