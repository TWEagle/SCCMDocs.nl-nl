---
title: Het beheren van Windows Device Guard
titleSuffix: Configuration Manager
description: Informatie over het System Center Configuration Manager gebruiken voor het beheren van Windows Device Guard.
ms.custom: na
ms.date: 10/20/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
caps.latest.revision: "13"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 8d84d0d65db7668baa7be9bbf0ad1df869b37919
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="device-guard-management-with-configuration-manager"></a>Guard Apparaatbeheer met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

## <a name="introduction"></a>Inleiding
Device Guard is een groep van Windows 10-functies die zijn ontworpen voor pc's beschermen tegen malware en andere niet-vertrouwde software. Dit voorkomt dat schadelijke code die wordt uitgevoerd door ervoor te zorgen dat alleen goedgekeurde code, die u kent, kan worden uitgevoerd.

Device Guard omvat zowel software en hardware gebaseerde beveiligingsfuncties. Configureerbare code-integriteit is een laag voor beveiliging op basis van software die een expliciete lijst met software die mag worden uitgevoerd op een PC wordt afgedwongen. Op een eigen, configureerbare code heeft integriteit geen vereisten voor hardware of firmware. Windows Defender Toepassingsbeheer beleid dat is geïmplementeerd met Configuration Manager inschakelen een configureerbare code-integriteitsbeleid op pc's in Doelverzamelingen die voldoen aan de minimale versie van Windows en de SKU-vereisten die worden beschreven in dit artikel. Beveiliging op basis van het hypervisor van code-integriteitsbeleidsregels is geïmplementeerd via Configuration Manager kan eventueel worden ingeschakeld via Groepsbeleid op geschikte hardware.

Lees voor meer informatie over Device Guard, de [Device Guard Implementatiehandleiding](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide).

## <a name="using-device-guard-with-configuration-manager"></a>Gebruik Device Guard met Configuration Manager

U kunt de Configuration Manager gebruiken voor het implementeren van een beleid voor toepassingsbeheer voor Windows Defender waarmee u de modus waarin Device Guard wordt uitgevoerd op computers in een verzameling configureren. 

U kunt een van de volgende modi configureren:

1.  **Afdwinging ingeschakeld** - enkel vertrouwde uitvoerbare bestanden mogen worden uitgevoerd.
2.  **Alleen controle** - toestaan alle uitvoerbare bestanden worden uitgevoerd, maar log uitvoerbare bestanden die worden uitgevoerd in het gebeurtenislogboek van de lokale client niet vertrouwd.

>[!TIP]
>In deze versie van Configuration Manager is Device Guard een voorlopige versie-functie. Als u wilt inschakelen, Zie [pre-release functies in System Center Configuration Manager](/sccm/core/servers/manage/pre-release-features).

## <a name="what-can-run-when-you-deploy-a-windows-defender-application-control-policy"></a>Wat kan worden uitgevoerd als u een beleid voor toepassingsbeheer voor Windows Defender implementeren?

Windows Device Guard kunt u ten zeerste bepalen wat kan worden uitgevoerd op pc's die u beheert. Deze functie kan nuttig zijn voor pc's in hoogwaardige beveiliging afdelingen, waar is het essentieel dat ongewenste software kan niet worden uitgevoerd.

Wanneer u een beleid implementeert gewoonlijk kunt het volgende uitvoerbare programma's uitvoeren:

- Onderdelen van Windows-besturingssysteem
- Hardware Dev Center-stuurprogramma's (die Windows Hardware Quality Labs handtekeningen hebben)
- Windows Store-apps
- Configuration Manager-client 
- Alle software geïmplementeerd via Configuration Manager dat pc's worden geïnstalleerd nadat het beleid voor toepassingsbeheer voor Windows Defender is verwerkt. 
- Updates voor windows-onderdelen uit:
    - Windows Update
    - Windows Update voor bedrijven
    - Windows Server updateservices
    - Configuration Manager

>[!IMPORTANT]
>Deze items omvatten alle software die is geen *niet* ingebouwd in Windows die automatisch worden bijgewerkt vanaf het internet of een derde partij software-updates of ze zijn geïnstalleerd via een van de update-mechanismen die eerder is vermeld, of via internet. Alleen softwarewijzigingen die zijn geïmplementeerd via Configuration Manager-client kunt uitvoeren.

## <a name="before-you-start"></a>Voordat u begint

Voordat u configureren of implementeren van beleid voor toepassingsbeheer voor Windows Defender, lees de volgende informatie:

- Guard Apparaatbeheer is een voorlopige versie-functie voor Configuration Manager en kan worden gewijzigd.
- Als u wilt gebruiken Device Guard met Configuration Manager, moeten op pc's die u beheert, de versie van Windows 10 Enterprise 1703 of hoger worden uitgevoerd.
- Wanneer een beleid met succes is verwerkt op een client-PC, Configuration Manager is geconfigureerd als een beheerd installatieprogramma op deze client en software die is geïmplementeerd via SCCM na de processen van het beleid wordt automatisch vertrouwd. Software die door Configuration beheerd zijn geïnstalleerd voordat de processen van de beleid voor toepassingsbeheer voor Windows Defender wordt niet automatisch vertrouwd.
- Client-pc's moeten hebben connectiviteit met de domeincontroller voor een beleid voor toepassingsbeheer voor Windows Defender om te worden verwerkt.
- De planning voor nalevingsevaluatie standaard voor toepassingsbeheer voor Windows Defender-beleid worden geconfigureerd tijdens de implementatie is elke dag. Als u problemen bij de beleidsverwerking worden waargenomen, kan het nuttig voor het configureren van de planning voor nalevingsevaluatie moet minder zijn, bijvoorbeeld elk uur zijn. Dit schema bepaalt hoe vaak clients probeert om een beleid voor toepassingsbeheer voor Windows Defender wanneer een fout te verwerken.
- Ongeacht de afdwingingsmodus selecteert u, wanneer u een beleid voor toepassingsbeheer voor Windows Defender, client-pc's HTML-toepassingen kunnen niet worden uitgevoerd met de extensie HTA implementeert.

## <a name="how-to-create-a-windows-defender-application-control-policy"></a>Het maken van een beleid voor toepassingsbeheer voor Windows Defender
1.  Klik op **Activa en naleving**op de Configuration Manager-console.
2.  In de **activa en naleving** werkruimte Vouw **Endpoint Protection**, en klik vervolgens op **beleid voor toepassingsbeheer voor Windows Defender**.
3.  Op de **Start** tabblad, in de **maken** groep, klikt u op **beleid Windows Defender Toepassingsbeheer maken**.
4.  Op de **algemene** pagina van de **Windows Defender Toepassingsbeheer maken beleid Wizard**, geef de volgende instellingen:
    - **Naam** -Voer een unieke naam voor dit beleid voor toepassingsbeheer voor Windows Defender. 
    - **Beschrijving** - eventueel een beschrijving invoeren voor het beleid dat u het kunt herkennen in de Configuration Manager-console.
    - **Afdwingingsmodus** -Kies een van de volgende methoden voor het afdwingen voor Device Guard op de client-PC.
        - **Afdwinging ingeschakeld** - alleen toestaan vertrouwde uitvoerbare bestanden mogen worden uitgevoerd.
        - **Alleen controle** - toestaan alle uitvoerbare bestanden worden uitgevoerd, maar log uitvoerbare bestanden die worden uitgevoerd in het gebeurtenislogboek van de lokale client niet vertrouwd.
5.  Op de **insluitingen** tabblad van de **Windows Defender Toepassingsbeheer maken beleid Wizard**, klikt u op **toevoegen** als u wilt toevoegen (optioneel) vertrouwen voor specifieke bestanden of mappen op pc's. 
6.  In de **vertrouwde bestand toevoegen of map** dialoogvenster geeft u de informatie over het bestand of map die u wilt vertrouwen. U kunt een lokaal bestand of map pad opgeven of u kunt verbinding maken met een extern apparaat waarvoor u gemachtigd bent om te koppelen en geef een bestand of map pad op dat apparaat.
Wanneer u vertrouwen voor specifieke bestanden of mappen in een beleid voor toepassingsbeheer voor Windows Defender toevoegt, kunt u het volgende doen:
    - Problemen oplossen met beheerd installatieprogramma gedrag
    - Vertrouwensrelatie van LOB-apps die met Configuration Manager kunnen niet worden geïmplementeerd
    - Apps die zijn opgenomen in de installatiekopie van een besturingssysteem-implementatie, vertrouwen. 
7.  Klik op **volgende**, voltooi de wizard.

>[!IMPORTANT]
>Het opnemen van vertrouwde bestanden of mappen wordt alleen ondersteund op client-pc's met versie 1706 of hoger van de Configuration Manager-client. Als een insluitingsregels zijn opgenomen in een beleid voor toepassingsbeheer voor Windows Defender en het beleid wordt geïmplementeerd op een client-PC met een ouder besturingssysteem op de Configuration Manager-client, mislukt het beleid moet worden toegepast. Een upgrade van deze oudere clients, wordt dit probleem oplossen. Beleidsregels die geen eventuele insluitingsregels bevatten mogelijk nog steeds worden toegepast op oudere versies van Configuration Manager-client.

## <a name="how-to-deploy-a-windows-defender-application-control-policy"></a>Het implementeren van een beleid voor toepassingsbeheer voor Windows Defender
1.  Klik op **Activa en naleving**op de Configuration Manager-console.
2.  In de **activa en naleving** werkruimte Vouw **Endpoint Protection**, en klik vervolgens op **beleid voor toepassingsbeheer voor Windows Defender**.
3.  In de lijst met beleidsregels, selecteer de website die u wilt implementeren, en klik vervolgens op de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.
4.  In de **Windows Defender Toepassingsbeheer implementeren beleid** dialoogvenster Selecteer de verzameling waarnaar u wilt het beleid implementeren. Configureer vervolgens een planning voor wanneer clients evalueren voor het beleid. Selecteer ten slotte of de client het beleid buiten de geconfigureerde onderhoudsvensters kunt evalueren.
5.  Wanneer u klaar bent, klikt u op **OK** het beleid te implementeren. 

### <a name="restarting-the-device-after-deploying-the-policy"></a>Het apparaat opnieuw te starten nadat het beleid is geïmplementeerd

Nadat het beleid op een client-PC wordt verwerkt, opnieuw opstarten is gepland op dat de client volgens de **clientinstellingen** voor **Computer opnieuw wordt opgestart**. Opnieuw opstarten is niet vereist voor het beleid wilt toepassen, maar dit is de standaardinstelling. Als u uitschakelen opnieuw wordt opgestart wilt, voert u deze stappen:

1. Open de **Windows Defender toepassingsbeleid maken** wizard.
2. Op de **algemene** pagina, schakel het selectievakje voor **afdwingen van het opnieuw opstarten van apparaten, zodat dit beleid kan worden afgedwongen voor alle processen**.
3. Klik op **volgende** totdat de wizard is voltooid.



## <a name="how-to-monitor-a-windows-defender-application-control-policy"></a>Hoe u een beleid voor toepassingsbeheer voor Windows Defender bewaken

Gebruik de informatie in de [instellingen voor naleving bewaken](/sccm/compliance/deploy-use/monitor-compliance-settings) artikel om te controleren of de geïmplementeerde beleid is toegepast op alle pc's correct.

Voor het bewaken van de verwerking van een beleid voor toepassingsbeheer voor Windows Defender, het volgende logboekbestand op client-pc's te gebruiken:

**%WINDIR%\CCM\Logs\DeviceGuardHandler.log**

Controleer of de specifieke software die worden geblokkeerd of gecontroleerd, Zie de volgende lokale client-gebeurtenislogboeken:

1.  Gebruik voor het blokkeren van en controle van de uitvoerbare bestanden, **logboeken toepassingen en Services** > **Microsoft** > **Windows** > **Code-integriteit** > **operationele**.
2.  Gebruik voor blokkeren en de controle van Windows Installer en scriptbestanden **logboeken toepassingen en Services** > **Microsoft** > **Windows** > **AppLocker** > **MSI en het Script**.

## <a name="automatically-let-software-run-if-it-is-trusted-by-intelligent-security-graph"></a>Automatisch laten uitvoeren als deze wordt vertrouwd door intelligente beveiliging grafiek software

U kunt de software vergrendelde apparaten uitgevoerd met een goede reputatie zoals wordt bepaald door de Microsoft Intelligent beveiliging grafiek (ISG). Bevat de ISG [Windows Defender SmartScreen](https://docs.microsoft.com/windows/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview) en andere Microsoft-services. De apparaten moeten worden uitgevoerd als Windows Defender Smartscreen voor deze software om te worden vertrouwd.

1. Open de **Windows Defender toepassingsbeleid maken** wizard.
2. Op de **insluitingen** pagina, schakel het selectievakje voor **software die wordt vertrouwd door de intelligente beveiliging grafiek autoriseren**.
3. Vak toevoegen in de vertrouwde bestanden of mappen, bestanden en mappen die u wilt worden vertrouwd.
4. Klik op **volgende** totdat de wizard is voltooid.



## <a name="security-and-privacy-information-for-device-guard"></a>Beveiliging en privacy-informatie voor Device Guard

- In deze voorlopige versie, implementeert geen beleidsregels voor toepassingsbeheer voor Windows Defender met de afdwingingsmodus **Audit alleen** in een productieomgeving. Deze modus is bedoeld om te testen in een testomgeving alleen instellen.
- Apparaten waarvoor een beleid is geïmplementeerd, kunnen in **Audit alleen** of **afdwinging ingeschakeld** modus, die niet opnieuw is opgestart om af te dwingen van het beleid zijn kwetsbaar voor niet-vertrouwde software wordt geïnstalleerd.
In dit geval kan de software kan doorgaan met het mag worden uitgevoerd, zelfs als het apparaat opnieuw wordt opgestart, of ontvangt u een beleid in **afdwinging ingeschakeld** modus.
- Om ervoor te zorgen dat het beleid voor toepassingsbeheer voor Windows Defender effectief is, moet u het apparaat in een testomgeving voorbereiden. Vervolgens implementeert de **afdwinging ingeschakeld** beleid, en ten slotte het apparaat opnieuw starten voordat u het apparaat aan een eindgebruiker geven.
- Implementeer een beleid met geen **afdwinging ingeschakeld**, en vervolgens later implementeert een beleid met **Audit alleen** op hetzelfde apparaat. Deze configuratie kan leiden tot niet-vertrouwde software uit te voeren.
- Wanneer u Configuration Manager gebruikt om in te schakelen configureerbare code-integriteit op client-pc's met beleid voor toepassingsbeheer voor Windows Defender, het beleid niet voorkomen dat gebruikers met lokale beheerdersrechten uit het omzeilen van de Windows Defender-toepassing Beleid voor toegangsbeheer of niet-vertrouwde software anders wordt uitgevoerd. 
- De enige manier om te voorkomen dat gebruikers met lokale beheerdersrechten uitschakelen configureerbare code-integriteit is een ondertekende binaire beleid implementeren. Deze implementatie is mogelijk via Groepsbeleid, maar niet op dit moment ondersteund in Configuration Manager.
- AppLocker-beleid maakt gebruik van Configuration Manager in te stellen als een beheerd installatieprogramma op client-pc's. AppLocker wordt alleen gebruikt om te worden beheerd installatieprogramma's identificeren en afdwingen van alle gebeurt met configureerbare code-integriteit. 




