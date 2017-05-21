---
title: Plannen voor Endpoint Protection | Microsoft-documenten
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7610bbd3-a67f-4a09-8115-e35d40d43b42
caps.latest.revision: 16
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 6c4273dae99ec8db2cf827f463b973e876d0d35b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-endpoint-protection-in-system-center-configuration-manager"></a>Planning voor Endpoint Protection in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Endpoint Protection in System Center Configuration Manager kunt u voor het beheren van beleidsregels voor antimalware en Windows Firewall-beveiliging voor clientcomputers in uw Configuration Manager-hiërarchie.  

> [!IMPORTANT]  
>  U moet een licentie voor het gebruik van Endpoint Protection voor het beheren van clients in de Configuration Manager-hiërarchie.  

Wanneer u Endpoint Protection met Configuration Manager gebruikt, hebt u de volgende voordelen:  

-   Antimalware-beleidsregels, Windows Firewall-instellingen configureren en beheren van Windows Defender geavanceerde bedreiging beveiliging op geselecteerde computergroepen  

-   Gebruik Configuration Manager-software-updates te downloaden van de meest recente definitiebestanden up-to-date te houden clientcomputers  

-   Verzend e-mailmeldingen, gebruik in-console bewaking en geef rapporten weer om gebruikers met beheerdersrechten op de hoogte te houden wanneer er malware op clientcomputers is gedetecteerd.  

Windows 10-computers nodig geen voor elke extra client voor het beheer van endpoint protection. Endpoint Protection installeert op Windows 8.1 en oudere computers zijn eigen client naast de Configuration Manager-client. De Endpoint Protection-client biedt de volgende mogelijkheden:  

-   Detecteren en herstellen van malware en spyware  

-   Rootkitdetectie en herstel  

-   Evalueren van kritieke beveiligingsproblemen en automatische definitie en engine-updates  

-   Detecteren van kwetsbare plekken in het netwerk via het netwerkinspectiesysteem  

-   Integratie met Cloud-beveiligingsservice malware melden aan Microsoft. Wanneer u deze service toevoegt, kan Windows Defender of de Endpoint Protection-client downloaden de meest recente definities van Malware Protection Center wanneer is onbekend malware gedetecteerd op een computer.  

> [!NOTE]  
>  De Endpoint Protection-client kan worden geïnstalleerd op een server waarop Hyper-V wordt uitgevoerd en op virtuele machines voor gasten met ondersteunde besturingssystemen. Acties voor Endpoint Protection hebben om te voorkomen dat buitensporig CPU-gebruik, een ingebouwde, willekeurige vertraging zodat services niet tegelijkertijd uitvoeren.  

  Bovendien kunt Endpoint Protection in Configuration Manager u voor het beheren van Windows Firewall-instellingen in de Configuration Manager-console.  

 [Voorbeeldscenario: System Center Endpoint Protection gebruiken om computers te beveiligen tegen schadelijke software in System Center Configuration Manager](../deploy-use/scenarios-endpoint-protection.md) ziet u hoe u kunt configureren en beheren van Endpoint Protection en de Windows Firewall.  

## <a name="managing-malware-with-endpoint-protection"></a>Malware beheren met Endpoint Protection  

Endpoint Protection in Configuration Manager kunt u beleidsregels voor antimalware die instellingen voor Endpoint Protection clientconfiguraties bevatten te maken. U kunt vervolgens deze antimalware-beleidsregels op clientcomputers implementeren en controleren ze op in de **Status van Endpoint Protection** knooppunt in de **bewaking** werkruimte of met behulp van Configuration Manager-rapporten.  

 Extra informatie:  

-   [Maken en implementeren van antimalware-beleidsregels voor Endpoint Protection in System Center Configuration Manager](../deploy-use/endpoint-antimalware-policies.md) - maken, implementeren en bewaken van anti-malwarebeleid van een lijst met de instellingen die u kunt configureren  

-   [Endpoint Protection in System Center Configuration Manager controleren](../deploy-use/monitor-endpoint-protection.md) -bewaking Activiteitenoverzichten en geïnfecteerde clientcomputers.   

-   [Beheren van beleidsregels voor antimalware en firewall-instellingen voor Endpoint Protection in System Center Configuration Manager](../deploy-use/endpoint-antimalware-firewall.md) -kunt u de prioriteit van beleid voor [antimalware](../deploy-use/endpoint-antimalware-firewall.md#manage-antimalware-policies) of [firewall](../deploy-use/endpoint-antimalware-firewall.md#manage-windows-firewall-policies), [herstellen malware op clientcomputers](../deploy-use/endpoint-antimalware-firewall.md#remediate-detected-malware), en andere taken

## <a name="managing-windows-firewall-with-endpoint-protection"></a>Windows Firewall beheren met Endpoint Protection  
 Endpoint Protection in Configuration Manager biedt algemene beheer van Windows Firewall op clientcomputers. Voor elk netwerkprofiel kunt u de volgende instellingen configureren:  

-   Windows Firewall in- of uitschakelen.  

-   Blokkeer binnenkomende verbindingen, inclusief verbindingen in de lijst met toegestane programma's.  

-   Waarschuw de gebruiker wanneer een nieuw programma door Windows Firewall wordt geblokkeerd.  

> [!NOTE]  
>  Endpoint Protection biedt alleen ondersteuning voor het beheren van Windows Firewall.  

  Zie voor meer informatie over het maken en implementeren van Windows Firewall-beleid voor Endpoint Protection [maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager](../deploy-use/create-windows-firewall-policies.md).  

## <a name="windows-defender-advanced-threat-protection"></a>Windows Defender geavanceerde bedreiging beveiliging

Vanaf versie 1606 van Configuration Manager (huidige vertakking), kunt Endpoint Protection beheren en controleren van Windows Defender geavanceerde bedreiging beveiliging (vrije). Windows Defender vrije is een nieuwe service waarmee ondernemingen om te detecteren, te onderzoeken en reageren op geavanceerde aanvallen op hun netwerken. Zie [Windows Defender dreigingen geavanceerde](../deploy-use/windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Endpoint Protection-werkstroom  
 Gebruik het volgende diagram voor hulp bij het begrijpen van de werkstroom voor het implementeren van Endpoint Protection in uw Configuration Manager-hiërarchie.  

 ![Endpoint Protection-werkstroom](../media/Endpoint-Protection-Workflow.gif)

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Endpoint Protection-client voor Mac-computers en Linux-servers  
 System Center bevat een Endpoint Protection-client voor Linux en Mac-computers. Deze clients zijn niet verstrekt met Configuration Manager. in plaats daarvan moet u de volgende producten vanuit downloaden de [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

> [!IMPORTANT]  
>  U moet klant van Microsoft Volume License zijn om de Endpoint Protection-installatiebestanden voor Linux en de Mac te kunnen downloaden.  

 Deze producten kunnen niet worden beheerd vanuit de Configuration Manager-console. Er wordt echter System Center Operations Manager-beheerpakket ij de installatiebestanden geleverd waarmee u de client voor Linux kunt beheren met Operations Manager.  

 Voor meer informatie over het installeren en beheren van Endpoint Protection-clients voor Linux- en Mac-computers gebruikt u de documentatie bij deze producten. De documentatie bevindt zich in de map **Documentatie** .

## <a name="best-practices-for-endpoint-protection-in-configuration-manager"></a>Aanbevolen procedures voor Endpoint Protection in Configuration Manager  
 Gebruik de volgende aanbevolen procedures voor Endpoint Protection in System Center 2012 Configuration Manager.  

### <a name="configure-custom-client-settings-for-endpoint-protection"></a>Aangepaste clientinstellingen voor Endpoint Protection configureren  
 Wanneer u clientinstellingen voor Endpoint Protection configureert, gebruikt u niet de standaardclientinstellingen ze instellingen niet toepassen op alle computers in uw hiërarchie. Configureer in plaats daarvan aangepaste clientinstellingen en wijs deze instellingen toe aan verzamelingen computers in uw hiërarchie.  

 Als u aangepaste clientinstellingen configureert, kunt u het volgende doen:  

-   Antimalware- en beveiligingsinstellingen aanpassen voor verschillende onderdelen van uw organisatie.  
-   Test de effecten van het Endpoint Protection uitvoeren op een kleine groep computers voordat u deze op de gehele hiërarchie implementeren.  
-   Meer clients toevoegen aan de verzameling gedurende een bepaalde periode fase van uw implementatie van de Endpoint Protection-client.  

### <a name="distributing-definition-updates-by-using-software-updates"></a>Definitie-updates distribueren via software-updates  
 Als u van Configuration Manager-software-updates gebruikmaakt voor definitie-updates distribueren, moet u het plaatsen van definitie-updates in een pakket bevat geen andere software-updates. Zodoende houdt u de grootte van het definitie-updatepakket beperkt, waardoor ze sneller naar distributiepunten worden gerepliceerd.

