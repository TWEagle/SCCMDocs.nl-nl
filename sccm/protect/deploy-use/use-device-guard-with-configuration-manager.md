---
title: Het beheren van beveiliging voor Windows-apparaat | Microsoft-documenten
description: Informatie over het System Center Configuration Manager gebruiken voor het beheren van beveiliging voor Windows-apparaat.
ms.custom: na
ms.date: 04/14/2017
ms.prod: configuration-manager
ms.reviewer: dudeso
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5e5d854c-9cc1-4dd8-b33f-0fcac675b395
caps.latest.revision: 13
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 49599f529bb409f40caf9057989762e759f1c0ac
ms.openlocfilehash: 113dddb2939fedf24e8d489ff4443bd5e3e72c65
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---


# <a name="device-guard-management-with-configuration-manager"></a>Beveiliging Apparaatbeheer met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

## <a name="introduction"></a>Inleiding
Beveiliging van Windows-apparaat is een groep van Windows 10-functies die zijn ontworpen om pc's beschermen tegen malware en andere niet-vertrouwde software. Dit voorkomt dat schadelijke code die wordt uitgevoerd door ervoor te zorgen dat alleen goedgekeurde code, die u kent, kan worden uitgevoerd.

Apparaat-beveiliging omvat software en hardware op basis van functie voor beveiliging. Configureerbare code-integriteitsbeleidsbestand is een beveiligingslaag die een expliciete lijst van software die kan dwingt worden uitgevoerd op een PC op basis van software. Op een eigen, configureerbare code heeft integriteit geen vereisten voor hardware- of firmware. Een configureerbare code-integriteitsbeleid op pc's in de betreffende verzamelingen die voldoen aan de minimale versie van Windows en de SKU-vereisten die hieronder worden vermeld inschakelen beveiligingsmethode voor apparaatfuncties geïmplementeerd met Configuration Manager Eventueel hypervisor beveiliging van beleid dat is geïmplementeerd via Configuration Manager kunnen worden ingeschakeld via Groepsbeleid op geschikte hardware-code-integriteitsbeleidsbestand gebaseerd.

Lees voor meer informatie over apparaat-beveiliging, [apparaat beveiligingsmethode Implementatiehandleiding](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide).

U kunt de Configuration Manager gebruiken voor het implementeren van een apparaat beveiligingsmethode beleid waarmee u de modus waarin apparaat beveiliging wordt uitgevoerd op computers in een verzameling configureren. 

U kunt een van de volgende modi configureren:

1.    **Afdwinging ingeschakeld** - enkel vertrouwde uitvoerbare bestanden mogen worden uitgevoerd.
2.    **Alleen controle** - toestaan dat alle uitvoerbare bestanden om uit te voeren, maar log uitvoerbare bestanden die worden uitgevoerd in het gebeurtenislogboek van de lokale client niet vertrouwd.

>[!TIP]
>Apparaat-beveiliging is in deze versie van Configuration Manager, een voorlopige versie-functie. Als u wilt inschakelen, Zie [voorlopige functies in System Center Configuration Manager](/sccm/core/servers/manage/pre-release-features).

### <a name="what-can-run-when-you-deploy-a-device-guard-policy"></a>Wat kunnen uitvoeren wanneer u een apparaat beveiligingsmethode beleid implementeren?

Beveiliging van Windows-apparaten kunt u ten zeerste bepalen wat kan worden uitgevoerd op pc's die u beheert. Dit is bijzonder nuttig voor pc's sterk beveiligde afdelingen, waarbij het belangrijk is om ongewenste software is niet toegestaan om te worden uitgevoerd.

Wanneer u een beleid implementeert normaal gesproken worden de volgende uitvoerbare bestanden kunnen uitgevoerd:

- Onderdelen van Windows-besturingssysteem
- Hardware Dev Center-stuurprogramma's (met Windows Hardware Quality Labs handtekeningen)
- Windows Store-apps
- De Configuration Manager-client 
- Alle software geïmplementeerd via Configuration Manager dat de pc's installeren nadat het apparaat beveiligingsmethode beleid is verwerkt. 
- Updates voor windows-onderdelen uit:
    - Windows Update
    - Windows Update voor bedrijven
    - Windows Server updateservices
    - Configuration Manager

>[!IMPORTANT]
>Deze bevatten niet alle software die is **niet** ingebouwd in Windows die automatisch worden bijgewerkt via het internet of een derde partij software-updates of ze zijn geïnstalleerd via een van de update-mechanismen genoemde, van het internet. Alleen de softwarewijzigingen die zijn geïmplementeerd via Configuration Manager-client mag worden uitgevoerd.

## <a name="before-you-start"></a>Voordat u begint

Voordat u configureren of implementeren van beleid voor apparaat-beveiliging, raadpleegt u de volgende informatie:

- Beveiliging van Apparaatbeheer is een voorlopige versie-functie voor Configuratiebeheer en kan worden gewijzigd.
- Voor het gebruik van apparaat-beveiliging, moeten op pc's die u beheert, de Windows 10 Enterprise met de Update beveiligingsbeheerder of hoger worden uitgevoerd.
- Nadat een beleid met succes is verwerkt op een client-PC, Configuration Manager is geconfigureerd als een beheerde-installatieprogramma op de client en software geïmplementeerd via SCCM nadat het beleid is verwerkt, wordt automatisch vertrouwd. Software die is geïnstalleerd door Configuration beheerd voordat het apparaat beveiligingsmethode beleid wordt verwerkt, wordt niet automatisch vertrouwd.
- In deze voorlopige versie als een client-PC een implementatie van een beleid apparaat-beveiliging, ontvangt deze wordt willekeurig maken de verwerkingstijd van dit beleid gedurende een periode van twee uur. 
- Client-pc's moeten hebben verbinding met de domeincontroller voor een apparaat beveiligingsmethode beleid om te worden verwerkt.
- De planning voor nalevingsevaluatie standaard voor apparaat beveiligingsmethode-beleid kunnen worden geconfigureerd tijdens de implementatie, wordt elke dag. Als er problemen bij de verwerking van beleid zijn waargenomen, kan het nuttig zijn voor het configureren van de planning voor nalevingsevaluatie worden uitgevoerd, bijvoorbeeld elk uur zijn. Dit schema bepaalt hoe vaak clients opnieuw proberen voor het verwerken van een apparaat beveiligingsmethode beleid in het geval van een storing optreedt.
- Ongeacht de modus voor uitvoering die u selecteert wanneer u een apparaat beveiligingsmethode beleid implementeert, client pc's kan niet worden HTML-toepassingen met de extensie HTA uitvoeren.

## <a name="how-to-create-a-device-guard-policy"></a>Het maken van een beleid apparaat-beveiliging
1.    Klik op **Activa en naleving**op de Configuration Manager-console.
2.    In de **activa en naleving** werkruimte Vouw **Endpoint Protection**, en klik vervolgens op **-beveiliging voor apparaatfuncties**.
3.    Op de **Start** tabblad, in de **maken** groep, klikt u op **apparaatbeleid beveiligingsmethode maken**.
4.    Op de **algemeen** pagina van de **maken apparaat beveiligingsmethode Wizard beleid voor**, geeft u de volgende:
    - **Naam** -Geef een unieke naam voor dit beleid apparaat-beveiliging. 
    - **Beschrijving** - eventueel een beschrijving invoeren voor het beleid waarmee u geïdentificeerd in de Configuration Manager-console.
    - **Modus voor uitvoering** -kiest een van de volgende methoden afdwinging voor apparaat-beveiliging op de client PC.
        - **Afdwinging ingeschakeld** - alleen toestaan vertrouwde uitvoerbare bestanden mogen worden uitgevoerd.
        - **Alleen controle** - toestaan dat alle uitvoerbare bestanden om uit te voeren, maar log uitvoerbare bestanden die worden uitgevoerd in het gebeurtenislogboek van de lokale client niet vertrouwd.
5.    Klik op **volgende**, voltooi de wizard.

## <a name="how-to-deploy-a-device-guard-policy"></a>Het implementeren van beleid voor een apparaat-beveiliging
1.    Klik op **Activa en naleving**op de Configuration Manager-console.
2.    In de **activa en naleving** werkruimte Vouw **Endpoint Protection**, en klik vervolgens op **-beveiliging voor apparaatfuncties**.
3.    In de lijst met beleidsregels, selecteer de website die u wilt implementeren, en klik vervolgens op de **Start** tabblad, in de **implementatie** groep, klikt u op **implementeren**.
4.    In de **apparaatbeleid beveiliging implementeren** in het dialoogvenster, selecteer de verzameling waarnaar u wilt implementeren als het beleid, configureer een planning voor wanneer clients de beleid evalueren en ten slotte, selecteert u of de client het beleid buiten de geconfigureerde onderhoudsvensters kunt beoordelen.
5.    Wanneer u klaar bent, klikt u op **OK** het beleid implementeren. 

Nadat het beleid is verwerkt op een client-PC, opnieuw opstarten wordt gepland op basis van client de **clientinstellingen** voor **Computer opnieuw worden opgestart**.
**Totdat u de client PC opnieuw opstart, wordt het beleid pas van kracht.**

## <a name="how-to-monitor-a-device-guard-policy"></a>Het bewaken van een beleid apparaat-beveiliging

Gebruik de informatie in de [instellingen voor naleving controleren](/sccm/compliance/deploy-use/monitor-compliance-settings) onderwerp om te controleren van het geïmplementeerde beleid zodat deze is toegepast op alle computers correct.

Gebruik het volgende logboekbestand op client pc's voor het bewaken van de verwerking van beleid voor een apparaat-beveiliging:

**%WINDIR%\CCM\Logs\DeviceGuardHandler.log**

Om te controleren of de specifieke software worden geblokkeerd of worden gecontroleerd, Zie de gebeurtenislogboeken van de volgende lokale client. In Logboeken zijn de relevante logboeken als volgt:

1.    Gebruik voor blokkeren en controle van de uitvoerbare bestanden **logboeken toepassingen en Services** > **Microsoft** > **Windows** > **Code-Integriteitsbeleidsbestand** > **operationele**.
2.    Gebruik voor blokkeren en controle van Windows Installer en scriptbestanden **logboeken toepassingen en Services** > **Microsoft** > **Windows** > **AppLocker** > **MSI en Script**.

## <a name="security-and-privacy-information-for-device-guard"></a>Beveiliging en privacy-informatie voor apparaat-beveiliging

- In deze voorlopige versie implementeert geen beleidsregels voor apparaat-beveiliging met de modus voor uitvoering **Audit alleen** in een productieomgeving. In deze modus is bedoeld om te testen in een testomgeving alleen instellen.
- Apparaten waarop een beleid is geïmplementeerd, kunnen in **Audit alleen** -modus of apparaten waarop een beleid is geïmplementeerd, kunnen in **afdwinging ingeschakeld** modus die nog niet opnieuw opgestart als u wilt afdwingen van het beleid zijn kwetsbaar voor een niet-vertrouwde software wordt geïnstalleerd.
In dit geval de software kan doorgaan met het mag worden uitgevoerd, zelfs als het apparaat opnieuw wordt opgestart, of ontvangt u een beleid in **afdwinging ingeschakeld** modus.
- Zorg ervoor dat het apparaat beveiligingsmethode beleid wordt door het apparaat in een testomgeving voorbereiden gaat implementeren de **afdwinging ingeschakeld** beleid vervolgens opnieuw opstarten van het apparaat voordat u het apparaat voor een eindgebruiker geven.
- Implementeer een beleid met geen **afdwinging ingeschakeld**, en vervolgens een beleid met later implementeren **Audit alleen** op hetzelfde apparaat. Dit kan leiden tot niet-vertrouwde software uit te voeren.
- Wanneer u Configuration Manager gebruiken voor de integriteit van de configureerbare code op client pc's met beleid voor apparaat-beveiliging inschakelen, houd er rekening mee dat het beleid **heeft geen** te voorkomen dat gebruikers met lokale beheerdersrechten uit het beleid apparaat beveiliging te omzeilen of niet-vertrouwde software anders wordt uitgevoerd. 
- De enige manier om te voorkomen dat gebruikers met lokale beheerdersrechten uitschakelen configureerbare code-integriteitsbeleidsbestand is voor het implementeren van een ondertekende binaire beleid dat is mogelijk via Groepsbeleid, maar momenteel niet ondersteund in Configuration Manager.
- AppLocker-beleid maakt gebruik van Configuration Manager instellen als een beheerd Installer op client-pc's. AppLocker wordt alleen gebruikt om te identificeren installatieprogramma's van Managed en alle afdwinging gebeurt met de integriteit van de configureerbare code. 





