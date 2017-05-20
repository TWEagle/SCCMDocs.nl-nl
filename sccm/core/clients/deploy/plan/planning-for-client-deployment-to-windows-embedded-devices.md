---
title: Planningimplementatie van client voor Windows Embedded-apparaten | Microsoft-documenten
description: Plan voor de implementatie van clients op Windows Embedded-apparaten in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 038e61f9-f49d-41d1-9a9f-87bec9e00d5d
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: f7ef476a2ebcf0161ebb70d8a3d95f77806aa05e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-client-deployment-to-windows-embedded-devices-in-system-center-configuration-manager"></a>Planning voor clientimplementatie op Windows Embedded-apparaten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

<a name="BKMK_DeployClientEmbedded"></a>Als uw Windows Embedded-apparaat de System Center Configuration Manager-client niet opgeeft heeft, kunt u een van de methode voor clientinstallatie gebruiken als het apparaat voldoet aan de vereiste afhankelijkheden. Als het Embedded-apparaat schrijffilters ondersteunt, moet u deze filters uitschakelen voordat u de client installeert, en de filters vervolgens opnieuw inschakelen nadat de client is geïnstalleerd en is toegewezen aan een site.  

 Wanneer u de filters uitschakelt, moet u ervoor zorgen dat u niet de stuurprogramma's voor het filter uitschakelt. Deze stuurprogramma's worden doorgaans automatisch gestart wanneer de computer wordt gestart. Als u de stuurprogramma's uitschakelt, wordt de installatie van de client verhinderd of wordt de indelingstaak voor schrijffilters verstoord, waardoor de clientbewerkingen mislukken. Hieronder ziet u de services die zijn gekoppeld aan elk type schrijffilter dat actief moet blijven:  

|Type schrijffilter|Stuurprogramma|Type|Beschrijving|  
|-----------------------|------------|----------|-----------------|  
|EWF|EWF|Kernel|Implementeert I/O-omleiding op sectorniveau op beveiligde volumes.|  
|FBWF|FBWF|Bestandssysteem|Implementeert I/O-omleiding op bestandsniveau op beveiligde volumes.|  
|UWF|uwfreg|Kernel|Redirector UWF-register|  
|UWF|uwfs|Bestandssysteem|Redirector UWF-bestand|  
|UWF|uwfvol|Kernel|UWF-volumebeheer|  

 Schrijffilters beheren hoe het besturingssysteem op het Embedded-apparaat wordt bijgewerkt wanneer u wijzigingen aanbrengt, zoals wanneer u software installeert. Wanneer schrijffilters zijn ingeschakeld, worden de wijzigingen niet rechtstreeks in het besturingssysteem aangebracht, maar worden ze in plaats daarvan doorgestuurd naar een tijdelijke overlay. Als de wijzigingen enkel naar de overlay worden geschreven, gaan ze verloren wanneer het Embedded-apparaat wordt uitgeschakeld. Als de schrijffilters echter tijdelijk worden uitgeschakeld, kunnen de wijzigingen permanent gemaakt worden zodat u de wijzigingen niet opnieuw moet aanbrengen (of de software niet opnieuw moet installeren) telkens het Embedded-apparaat opnieuw wordt opgestart. Het tijdelijk uitschakelen en vervolgens opnieuw inschakelen van de schrijffilters vereist echter dat de computer een of meerdere keren opnieuw wordt opgestart; u beheert dit daarom best wanneer het gebeurt door onderhoudsvensters te configureren zodat de computer opnieuw wordt opgestart buiten de werkuren.  

 U kunt opties configureren om de schrijffilters automatisch uit te schakelen en opnieuw in te schakelen wanneer u software implementeert zoals toepassingen, takenreeksen, software-updates en de Endpoint Protection-client. De uitzondering is voor configuratiebasislijnen met configuratie-items die automatisch herstel gebruiken. In dit scenario vindt het herstel steeds plaats in de overlay zodat het enkel beschikbaar is wanneer het apparaat opnieuw wordt opgestart. Het herstel wordt opnieuw toegepast bij de volgende evaluatiecyclus, maar enkel op de overlay, die wordt gewist bij het opnieuw opstarten. Als u wilt afdwingen Configuration Manager de wijzigingen doorvoeren, kunt u de configuratiebasislijn en dan een andere software-implementatie die de toepassing van de wijziging zo snel mogelijk ondersteunt implementeren.  

 Als de schrijffilters zijn uitgeschakeld, kunt u software op Windows Embedded-apparaten installeren met behulp van Software Center. Als de schrijffilters zijn ingeschakeld, mislukt de installatie en Configuration Manager een foutboodschap dat u hebt onvoldoende machtigingen om de toepassing te installeren.  

> [!WARNING]  
>  Zelfs als u de opties voor Configuration Manager de wijzigingen doorvoeren niet selecteert, de wijzigingen worden toegepast als een andere software-installatie of wijziging wordt doorgevoerd die wijzigingen toepast. In dit scenario zullen de oorspronkelijke wijzigingen worden toegepast naast de nieuwe wijzigingen.  

 Wanneer Configuration Manager de schrijffilters wijzigingen permanent maken uitschakelt, kunnen alleen gebruikers die lokale beheerdersrechten hebben aanmelden en het embedded-apparaat gebruiken. Tijdens deze periode worden gebruikers met weinig rechten vergrendeld en zien ze een boodschap dat de computer niet beschikbaar is omdat hij wordt onderhouden. Dit helpt het apparaat te beschermen terwijl het in een status is waarin wijzigingen permanent kunnen worden toegepast, en dit vergrendelgedrag in de onderhoudsmodus is een andere reden om een onderhoudsvenster te configureren op een moment waarop gebruikers zich niet kunnen aanmelden op deze apparaten.  

 Configuration Manager ondersteunt het beheer van de volgende types schrijffilters:  

-   File-Based Write Filter (FBWF) - voor meer informatie, Zie [File-Based Write Filter](http://go.microsoft.com/fwlink/?LinkID=204717).  

-   Enhanced Write Filter (EWF) RAM - voor meer informatie, Zie [Enhanced Write Filter](http://go.microsoft.com/fwlink/?LinkId=204718).  

-   Unified Write Filter (UWF) - voor meer informatie, Zie [Unified Write Filter](http://go.microsoft.com/fwlink/?LinkId=309236).  

 Configuration Manager heeft geen schrijffilterbewerkingen wanneer het Windows Embedded-apparaat in EWF RAM Reg-modus.  

> [!IMPORTANT]  
>  Als u de keuze hebt, bestand gebaseerde schrijffilters (FBWF) met Configuration Manager gebruiken voor een verhoogde efficiëntie en een hogere schaalbaarheid.
>
> **Voor apparaten die alleen FBWF gebruiken:** Configureer de volgende uitzonderingen om clientstatus en inventarisgegevens tussen heropstarten van het apparaat te behouden.  
>   
>  -   CCMINSTALLDIR\\*.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
>  Apparaten waarop Windows Embedded 8.0 of hoger wordt uitgevoerd, bieden geen ondersteuning voor uitsluitingen die jokertekens bevatten. Op deze apparaten moet u de volgende uitsluitingen afzonderlijk configureren:  
>   
>  -   Alle bestanden in CCMINSTALLDIR met de extensie .sdf. Doorgaans zijn dit:  
>   
>     -   UserAffinityStore.sdf  
>     -   InventoryStore.sdf  
>     -   CcmStore.sdf  
>     -   StateMessageStore.sdf  
>     -   CertEnrollmentStore.sdf  
> -   CCMINSTALLDIR\ServiceData  
> -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem  
>   
> **Voor apparaten die alleen FBWF en UWF gebruiken:** Wanneer clients in een werkgroep-certificaten voor verificatie naar beheerpunten gebruiken, moet u ook de persoonlijke sleutel om ervoor te zorgen blijft de client om te communiceren met het beheerpunt uitsluiten. Configureer de volgende uitzonderingen op deze apparaten:  
>   
>  -   c:\Windows\System32\Microsoft\Protect  
> -   c:\ProgramData\Microsoft\Crypto  
> -   HKEY_LOCAL_MACHINE\Software\Microsoft\SystemCertificates\SMS\Certificates  

 Zie voor een voorbeeldscenario voor het implementeren en beheren van Windows Embedded write filter ingeschakeld apparaten in Configuration Manager [voorbeeldscenario voor het implementeren en beheren van System Center Configuration Manager-clients op Windows Embedded-apparaten](../../../../core/clients/deploy/example-scenario-for-deploying-and-managing-clients-on-windows-embedded-devices.md).  

 Voor meer informatie over het maken van installatiekopieën voor Windows Embedded-apparaten en het configureren van schrijffilters, zie uw Windows Embedded-documentatie, of neem contact op met uw OEM.  

> [!NOTE]  
>  Wanneer u de toepasselijke platforms voor software-implementaties en configuratie-items selecteert, tonen deze de Windows Embedded-families eerder dan specifieke versies. Gebruik de volgende lijst om de specifieke versie van Windows Embedded toe te wijzen aan de opties in het lijstvak:  
>   
>  -   **Embedded-besturingssystemen op basis van Windows XP (32-bit)** omvat het volgende:  
>   
>      -   Windows XP Embedded  
>     -   Windows Embedded voor point-of-service  
>     -   Windows Embedded Standard 2009  
>     -   Windows Embedded POSReady 2009  
> -   **Embedded-besturingssystemen op basis van Windows 7 (32-bit)** omvat het volgende:  
>   
>      -   Windows Embedded Standard 7 (32-bit)  
>     -   Windows Embedded POSReady 7 (32-bit)  
>     -   Windows ThinPC  
> -   **Embedded-besturingssystemen op basis van Windows 7 (64-bit)** omvat het volgende:  
>   
>      -   Windows Embedded Standard 7 (64-bit)  
>     -   Windows Embedded POSReady 7 (64-bit)

