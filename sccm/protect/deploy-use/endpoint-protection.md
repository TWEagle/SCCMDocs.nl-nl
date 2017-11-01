---
title: Endpoint Protection
titleSuffix: Configuration Manager
description: "Informatie over het beheren van beleidsregels voor antimalware en Windows Firewall-beveiliging voor clientcomputers in uw Configuration Manager-hiërarchie."
ms.custom: na
ms.date: 02/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76c90f64-d729-456b-8304-01852cd66fb6
caps.latest.revision: "11"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 308c69f4631a1bcc28f7d8460a4aa3abb02f0650
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="endpoint-protection"></a>Endpoint Protection

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Endpoint Protection in System Center Configuration Manager kunt u voor het beheren van beleidsregels voor antimalware en Windows Firewall-beveiliging voor clientcomputers in uw Configuration Manager-hiërarchie.  

> [!IMPORTANT]  
>  U moet een licentie hebben voor het gebruik van Endpoint Protection voor het beheren van clients in uw Configuration Manager-hiërarchie.  

 Wanneer u Endpoint Protection met Configuration Manager gebruikt, hebt u de volgende voordelen:  

-   Beleidsregels voor antimalware, Windows Firewall-instellingen configureren en beheren van Windows Defender Advanced Threat Protection voor geselecteerde groepen computers  
-   Gebruik Configuration Manager software-updates te downloaden van de meest recente definitiebestanden clientcomputers om up-to-date te houden  
-   Verzend e-mailmeldingen, gebruik in-console bewaking en geef rapporten weer om gebruikers met beheerdersrechten op de hoogte te houden wanneer er malware op clientcomputers is gedetecteerd.  

Vanaf Windows 10 en Windows Server 2016 computers is is Windows Defender al geïnstalleerd. Een management-client voor Windows Defender is voor deze besturingssystemen geïnstalleerd wanneer de Configuration Manager-client wordt geïnstalleerd. De Endpoint Protection-client is geïnstalleerd op Windows 8.1 en oudere computers, met de Configuration Manager-client. Windows Defender en de Endpoint Protection-client hebt de volgende mogelijkheden:  

-   Detecteren en herstellen van malware en spyware  
-   Rootkitdetectie en herstel  
-   Evalueren van kritieke beveiligingsproblemen en automatische definitie en engine-updates  
-   Detecteren van kwetsbare plekken in het netwerk via het netwerkinspectiesysteem  
-   Integratie met Cloud Protection Service om malware aan Microsoft rapporteren. Wanneer u deze service toevoegt, kan de Endpoint Protection-client of Windows Defender de meest recente definities van Malware Protection Center downloaden wanneer onbekende malware op een computer wordt gedetecteerd.  

> [!NOTE]  
>  De Endpoint Protection-client kan worden geïnstalleerd op een server waarop Hyper-V wordt uitgevoerd en op virtuele gastmachines met ondersteunde besturingssystemen. Endpoint Protection-acties hebben een ingebouwde willekeurige vertraging te voorkomen dat buitensporig CPU-gebruik, zodat de beveiligingsservices niet tegelijkertijd worden uitgevoerd.  

 Bovendien kunt Endpoint Protection in Configuration Manager u voor het beheren van Windows Firewall-instellingen in de Configuration Manager-console.  

 [Voorbeeldscenario: System Center Endpoint Protection gebruiken om computers te beveiligen tegen schadelijke software in System Center Configuration Manager](scenarios-endpoint-protection.md) Endpoint Protection en Windows Firewall.  


## <a name="managing-malware-with-endpoint-protection"></a>Malware beheren met Endpoint Protection  
 Endpoint Protection in Configuration Manager kunt u antimalwarebeleidsregels maken die instellingen voor Endpoint Protection-clientconfiguraties bevatten. U kunt deze antimalwarebeleidsregels op clientcomputers implementeren en bewaken in de **Status van Endpoint Protection** knooppunt onder **beveiliging** in de **bewaking** werkruimte of met behulp van Configuration Manager-rapporten.  

 Extra informatie:  

-   [Het maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md) - maken, implementeren en controleren van antimalwarebeleidsregels met een lijst van de instellingen die u kunt configureren  

-   [Endpoint Protection in System Center Configuration Manager controleren](monitor-endpoint-protection.md) -bewaking activiteitenrapporten, geïnfecteerde clientcomputers en meer.  

-   [Het beheren van beleidsregels voor antimalware en firewall-instellingen voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-firewall.md) -malware op clientcomputers herstellen  


## <a name="managing-windows-firewall-with-endpoint-protection"></a>Windows Firewall beheren met Endpoint Protection  
 Endpoint Protection in Configuration Manager biedt basisfuncties voor het beheren van Windows Firewall op clientcomputers. Voor elk netwerkprofiel kunt u de volgende instellingen configureren:  

-   Windows Firewall in- of uitschakelen.  

-   Blokkeer binnenkomende verbindingen, inclusief verbindingen in de lijst met toegestane programma's.  

-   Waarschuw de gebruiker wanneer een nieuw programma door Windows Firewall wordt geblokkeerd.  

> [!NOTE]  
>  Endpoint Protection biedt alleen ondersteuning voor het beheren van Windows Firewall.  


 Zie voor meer informatie over het maken en implementeren van Windows Firewall-beleid voor Endpoint Protection [maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager](create-windows-firewall-policies.md).  


## <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

Vanaf versie 1606 van Configuration Manager (huidige vertakking), kunt Endpoint Protection beheren en controleren van Windows Defender Advanced Threat Protection (ATP). Windows Defender ATP is een nieuwe service waarmee ondernemingen te detecteren, onderzoeken en reageren op geavanceerde aanvallen in hun netwerken. Zie [Windows Defender Advanced Threat Protection](windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Endpoint Protection-werkstroom  
 Gebruik het volgende diagram om te begrijpen van de werkstroom voor het implementeren van Endpoint Protection in Configuration Manager-hiërarchie.  

 ![Endpoint Protection-werkstroom](../media/Endpoint-Protection-Workflow.gif)  

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Endpoint Protection-client voor Mac-computers en Linux-servers  
 System Center Endpoint Protection bevat een Endpoint Protection-client voor Linux en Mac-computers. Deze clients worden niet geleverd met Configuration Manager; in plaats daarvan moet u de volgende producten niet downloaden de [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

-   System Center Endpoint Protection voor Mac  

-   System Center Endpoint Protection voor Linux  


> [!IMPORTANT]  
>  U moet klant van Microsoft Volume License zijn om de Endpoint Protection-installatiebestanden voor Linux en de Mac te kunnen downloaden.  

 Deze producten kunnen niet worden beheerd vanuit de Configuration Manager-console. Er wordt echter System Center Operations Manager-beheerpakket ij de installatiebestanden geleverd waarmee u de client voor Linux kunt beheren met Operations Manager.  

### <a name="how-to-get-the-endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Het ophalen van de Endpoint Protection-client voor Mac-computers en Linux-servers

Gebruik de volgende stappen voor het downloaden van de installatiekopiebestand met de Endpoint Protection-clientsoftware en documentatie voor Mac-computers en Linux-servers.
1. Meld u aan bij de [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).
2. Selecteer de **downloadt en -sleutels** boven op het tabblad van de website.
3. Filter op product **System Center Endpoint Protection (huidige vertakking)**.
4. Klik op de koppeling naar **downloaden**
5. Klik op **Doorgaan**. Hier ziet u meerdere bestanden, waaronder een met de naam: **System Center Endpoint Protection (huidige vertakking - versie 1606) voor Linux-besturingssysteem en Macintosh OS meertalige 32/64-bits 1579 MB ISO**.
6. Klik op het pijlpictogram het bestand te downloaden. De bestandsnaam is **SW_DVD5_Sys_Ctr_Endpnt_Prtctn_1606_MultiLang_-2_EptProt_Lin_Mac_MLF_X21-44498. ISO**.

Deze juli 2017 update (X21 44498) omvat het volgende:

- System Center Endpoint Protection voor Mac 4.5.28.1 (installatie van het bijgewerkte certificaat)
- System Center Endpoint Protection voor Linux 4.5.18.0 (nieuwe taalpakketten)
- System Center Endpoint Protection voor Linux-documentatie (herziene hulp bij de realtime-beveiliging)

 Voor meer informatie over het installeren en beheren van Endpoint Protection-clients voor Linux- en Mac-computers gebruikt u de documentatie bij deze producten. De documentatie bevindt zich in de map **Documentatie** .
