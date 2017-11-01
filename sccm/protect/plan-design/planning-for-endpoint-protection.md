---
title: Plan voor Endpoint Protection
titleSuffix: Configuration Manager
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7610bbd3-a67f-4a09-8115-e35d40d43b42
caps.latest.revision: "16"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 3ffb112dc1aaf71162b0f706f5c07fb6d08e47f9
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="planning-for-endpoint-protection-in-system-center-configuration-manager"></a>Planning voor Endpoint Protection in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Endpoint Protection in System Center Configuration Manager kunt u voor het beheren van beleidsregels voor antimalware en Windows Firewall-beveiliging voor clientcomputers in uw Configuration Manager-hiërarchie.  

> [!IMPORTANT]  
>  U moet een licentie hebben voor het gebruik van Endpoint Protection voor het beheren van clients in uw Configuration Manager-hiërarchie.  

Wanneer u Endpoint Protection met Configuration Manager gebruikt, hebt u de volgende voordelen:  

-   Beleidsregels voor antimalware, Windows Firewall-instellingen configureren en beheren van Windows Defender Advanced Threat Protection voor geselecteerde groepen computers  

-   Gebruik Configuration Manager software-updates te downloaden van de meest recente definitiebestanden clientcomputers om up-to-date te houden  

-   Verzend e-mailmeldingen, gebruik in-console bewaking en geef rapporten weer om gebruikers met beheerdersrechten op de hoogte te houden wanneer er malware op clientcomputers is gedetecteerd.  

Windows 10-computers nodig geen extra clients voor endpoint protection-beheer. Op Windows 8.1 en oudere computers installeert Endpoint Protection naast de Configuration Manager-client ook een eigen client. De Endpoint Protection-client biedt de volgende mogelijkheden:  

-   Detecteren en herstellen van malware en spyware  

-   Rootkitdetectie en herstel  

-   Evalueren van kritieke beveiligingsproblemen en automatische definitie en engine-updates  

-   Detecteren van kwetsbare plekken in het netwerk via het netwerkinspectiesysteem  

-   Integratie met Cloud Protection Service om malware aan Microsoft rapporteren. Wanneer u deze service toevoegt, kan Windows Defender of Endpoint Protection-client downloaden de meest recente definities van Malware Protection Center wanneer onbekende malware wordt gedetecteerd op een computer.  

> [!NOTE]  
>  De Endpoint Protection-client kan worden geïnstalleerd op een server waarop Hyper-V wordt uitgevoerd en op virtuele gastmachines met ondersteunde besturingssystemen. Endpoint Protection-acties hebben een ingebouwde, op willekeurige vertraging te voorkomen dat buitensporig CPU-gebruik, zodat de services niet tegelijkertijd worden uitgevoerd.  

  Bovendien kunt Endpoint Protection in Configuration Manager u voor het beheren van Windows Firewall-instellingen in de Configuration Manager-console.  

 [Voorbeeldscenario: System Center Endpoint Protection gebruiken om computers te beveiligen tegen schadelijke software in System Center Configuration Manager](../deploy-use/scenarios-endpoint-protection.md) ziet u hoe u kunt configureren en beheren van Endpoint Protection en Windows Firewall.  

## <a name="managing-malware-with-endpoint-protection"></a>Malware beheren met Endpoint Protection  

Endpoint Protection in Configuration Manager kunt u antimalwarebeleidsregels maken die instellingen voor Endpoint Protection-clientconfiguraties bevatten. U kunt deze antimalwarebeleidsregels op clientcomputers implementeren en bewaken in de **Status van Endpoint Protection** knooppunt in de **bewaking** werkruimte of met behulp van Configuration Manager-rapporten.  

 Extra informatie:  

-   [Maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](../deploy-use/endpoint-antimalware-policies.md) - maken, implementeren en controleren van antimalwarebeleidsregels met een lijst van de instellingen die u kunt configureren  

-   [Endpoint Protection in System Center Configuration Manager controleren](../deploy-use/monitor-endpoint-protection.md) -bewaking activiteitenrapporten, geïnfecteerde clientcomputers en meer.   

-   [Beheren van beleidsregels voor antimalware en firewall-instellingen voor Endpoint Protection in System Center Configuration Manager](../deploy-use/endpoint-antimalware-firewall.md) -kunt u beleid prioriteit voor [antimalware](../deploy-use/endpoint-antimalware-firewall.md#manage-antimalware-policies) of [firewall](../deploy-use/endpoint-antimalware-firewall.md#manage-windows-firewall-policies), [malware op clientcomputers herstellen](../deploy-use/endpoint-antimalware-firewall.md#remediate-detected-malware), en andere taken

## <a name="managing-windows-firewall-with-endpoint-protection"></a>Windows Firewall beheren met Endpoint Protection  
 Endpoint Protection in Configuration Manager biedt basisfuncties voor het beheren van Windows Firewall op clientcomputers. Voor elk netwerkprofiel kunt u de volgende instellingen configureren:  

-   Windows Firewall in- of uitschakelen.  

-   Blokkeer binnenkomende verbindingen, inclusief verbindingen in de lijst met toegestane programma's.  

-   Waarschuw de gebruiker wanneer een nieuw programma door Windows Firewall wordt geblokkeerd.  

> [!NOTE]  
>  Endpoint Protection biedt alleen ondersteuning voor het beheren van Windows Firewall.  

  Zie voor meer informatie over het maken en implementeren van Windows Firewall-beleid voor Endpoint Protection [maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager](../deploy-use/create-windows-firewall-policies.md).  

## <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

Vanaf versie 1606 van Configuration Manager (huidige vertakking), kunt Endpoint Protection beheren en controleren van Windows Defender Advanced Threat Protection (ATP). Windows Defender ATP is een nieuwe service waarmee ondernemingen te detecteren, onderzoeken en reageren op geavanceerde aanvallen in hun netwerken. Zie [Windows Defender Advanced Threat Protection](../deploy-use/windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Endpoint Protection-werkstroom  
 Gebruik het volgende diagram om te begrijpen van de werkstroom voor het implementeren van Endpoint Protection in Configuration Manager-hiërarchie.  

 ![Endpoint Protection-werkstroom](../media/Endpoint-Protection-Workflow.gif)

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Endpoint Protection-client voor Mac-computers en Linux-servers  
 System Center bevat een Endpoint Protection-client voor Linux en Mac-computers. Deze clients worden niet geleverd met Configuration Manager; in plaats daarvan moet u de volgende producten niet downloaden de [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

> [!IMPORTANT]  
>  U moet klant van Microsoft Volume License zijn om de Endpoint Protection-installatiebestanden voor Linux en de Mac te kunnen downloaden.  

 Deze producten kunnen niet worden beheerd vanuit de Configuration Manager-console. Er wordt echter System Center Operations Manager-beheerpakket ij de installatiebestanden geleverd waarmee u de client voor Linux kunt beheren met Operations Manager.  

 Voor meer informatie over het installeren en beheren van Endpoint Protection-clients voor Linux- en Mac-computers gebruikt u de documentatie bij deze producten. De documentatie bevindt zich in de map **Documentatie** .

## <a name="best-practices-for-endpoint-protection-in-configuration-manager"></a>Aanbevolen procedures voor Endpoint Protection in Configuration Manager  
 Gebruik de volgende aanbevolen procedures voor Endpoint Protection in System Center 2012 Configuration Manager.  

### <a name="configure-custom-client-settings-for-endpoint-protection"></a>Aangepaste clientinstellingen voor Endpoint Protection configureren  
 Wanneer u clientinstellingen voor Endpoint Protection configureert, gebruik niet de standaardclientinstellingen omdat ze instellingen op alle computers in uw hiërarchie toepassen. Configureer in plaats daarvan aangepaste clientinstellingen en wijs deze instellingen toe aan verzamelingen computers in uw hiërarchie.  

 Als u aangepaste clientinstellingen configureert, kunt u het volgende doen:  

-   Antimalware- en beveiligingsinstellingen aanpassen voor verschillende onderdelen van uw organisatie.  
-   Test de effecten van Endpoint Protection worden uitgevoerd op een kleine groep computers voordat u deze op de gehele hiërarchie implementeren.  
-   Meer clients toevoegen aan de verzameling gedurende een bepaalde periode fase van uw implementatie van de Endpoint Protection-client.  

### <a name="distributing-definition-updates-by-using-software-updates"></a>Definitie-updates distribueren via software-updates  
 Als u software-updates voor Configuration Manager gebruikt voor het distribueren van definitie-updates, kunt u overwegen het plaatsen van definitie-updates in een pakket dat geen andere software-updates bevat. Zodoende houdt u de grootte van het definitie-updatepakket beperkt, waardoor ze sneller naar distributiepunten worden gerepliceerd.
