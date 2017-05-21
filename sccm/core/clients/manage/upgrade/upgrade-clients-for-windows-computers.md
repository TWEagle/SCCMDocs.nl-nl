---
title: Clients upgraden | Microsoft-documenten
description: Clients op Windows-computers in System Center Configuration Manager upgraden.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6143fd47-48ec-4bca-b53b-5b9b9f067bc3
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 98b8c92e4dad3cef1ed3701b9c0f9111eb9941ea
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-upgrade-clients-for-windows-computers-in-system-center-configuration-manager"></a>Clients voor Windows-computers bijwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de client op Windows-computers met installatiemethoden voor clients of de automatische upgrade clientfuncties in Configuration Manager bijwerken. De volgende clientinstallatiemethoden zijn geldige manieren om de clientsoftware op Windows-computers bij te werken:  

-   Installatie van Groepsbeleid  

-   Aanmeldingscriptinstallatie  

-   Handmatige installatie  

-   Upgrade-installatie  

 Als u geïnteresseerd bent in een upgrade van de client met behulp van een methode voor clientinstallatie, meer informatie over het gebruik van deze methoden in [het implementeren van clients op Windows-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).

 Vanaf versie 1610, kunt u clients uitsluiten van wordt bijgewerkt door het opgeven van een groep uitsluiting. Zie voor meer informatie [het upgraden van clients voor Windows-computers uitsluiten](exclude-clients-windows.md).  


> [!TIP]  
>  Als u een upgrade van uw serverinfrastructuur uitvoert vanaf een eerdere versie van Configuration Manager \(zoals Configuration Manager 2007 of System Center 2012 Configuration Manager\), wordt u aangeraden de serverupgrades, inclusief alle updates van Current Branch, uit te voeren voordat u een upgrade uitvoert van de Configuration Manager-clients.   De nieuwste update van Current Branch bevat de meest recente versie van de client, zodat u de clientupgrades het best kunt uitvoeren nadat u alle Configuration Manager-updates hebt geïnstalleerd die u wilt gebruiken.

> [!NOTE]
> Als u van plan bent om de site opnieuw toewijzen voor de clients tijdens de upgrade, kunt u de nieuwe site met de client.msi-eigenschap SMSSITECODE opgeven. Als u automatisch voor de SMSSITECODE gebruikt, moet u ook opgeven SITEREASSIGN = TRUE zodat automatische site opnieuw toewijzen aan optreden tijdens de upgrade. Zie voor meer informatie [SMSSITECODE](../../deploy/about-client-installation-properties.md#smssitecode).

## <a name="use-automatic-client-upgrade"></a>Automatische clientupgrade gebruiken  
 U kunt ook de Configuration Manager voor de clientsoftware automatisch bijwerken naar de nieuwste clientversie van de Configuration Manager-als Configuration Manager identificeert die een client die is toegewezen aan de Configuration Manager-hiërarchie lager dan de versie die wordt gebruikt in de hiërarchie is configureren. Dit scenario omvat het bijwerken van de client naar de nieuwste versie wanneer wordt geprobeerd om toe te wijzen aan een Configuration Manager-site.  

 Een client kan automatisch worden bijgewerkt in de volgende scenario's:  

-   De clientversie is lager dan de versie die in de hiërarchie wordt gebruikt.  

-   Op de client op de centrale beheersite is een taalpakket geïnstalleerd en de bestaande client heeft dit niet.  

-   Een vereiste voor een client in de hiërarchie heeft een verschillende versie dan de op de client geïnstalleerde.  

-   Een of meer clientinstallatiebestanden hebben een verschillende versie.  

> [!NOTE]  
>  U kunt het rapport uitvoert **telling van Configuration Manager-clients op clientversies** in de rapportmap **Site - clientgegevens** de verschillende versies van Configuration Manager-clients in uw hiërarchie identificeren.  

 Configuration Manager maakt een upgradepakket standaard dat automatisch wordt verzonden naar alle distributiepunten in de hiërarchie. Als u wijzigingen in het clientpakket op de centrale beheersite aanbrengt, bijvoorbeeld een clienttaalpakket toevoegt Configuration Manager automatisch updates van het pakket en distribueert het naar alle distributiepunten in de hiërarchie. Als de automatische clientupgrade is ingeschakeld, zal het nieuwe clienttaalpakket automatisch op elke client worden geïnstalleerd.  

> [!NOTE]  
>  Configuration Manager de client-update niet automatisch verzonden pakket naar Configuration Manager cloud-gebaseerde distributiepunten.  

 Het is raadzaam om automatische Clientupgrade over uw hiërarchie in te schakelen. Dit houdt uw clients bijgewerkt met een minimale administratieve overhead.  

 De volgende procedure gebruiken om automatische clientupgrade te configureren. Automatische clientupgrade moet op een centrale beheersite worden geconfigureerd en deze configuratie is van toepassing op alle clients in de hiërarchie.  

### <a name="to-configure-automatic-client-upgrades"></a>Automatische clientupgrades configureren  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Sites**.  

3.  Klik op **Hiërarchie-instellingen** op het tabblad **Start** , in de groep **Sites**.  

4.  Controleer op het tabblad **Clientupgrade** van het dialoogvenster **Eigenschappen van hiërarchie-instellingen** de versie en datum van de productieclient en zorg ervoor dat dit de versie is die u wilt gebruiken voor het bijwerken van Windows-computers.  Als niet de verwachte clientversie wordt weergegeven, moet u het niveau van de pre-productieclient mogelijk verhogen naar productie. Zie voor meer informatie [clientupgrades testen in een pre-productieverzameling in System Center Configuration Manager](../../../../core/clients/manage/upgrade/test-client-upgrades.md).  

5.  Klik op **Upgrade uitvoeren voor alle clients in de hiërarchie met gebruik van productieversie van client** en klik in het bevestigingsdialoogvenster op **OK** .  

6.  Als u niet wilt dat clientupgrades worden toegepast op servers, klikt u op **Geen upgrade op servers uitvoeren**.  

7.  Geef het aantal dagen op waarin computers de client moeten upgraden na het ontvangen van het clientbeleid. De client wordt bijgewerkt aan een random interval binnen dit aantal dagen. Dit voorkomt dat scenario's met een groot aantal clientcomputers gelijktijdig worden bijgewerkt.

    > [!NOTE]
    > Een computer moet worden uitgevoerd om de upgrade van de client. Als een computer niet wordt uitgevoerd wanneer deze is gepland voor het ontvangen van de upgrade, wordt de upgrade niet uitgevoerd. In plaats daarvan wanneer de computer opnieuw is opgestart, nog een upgrade is gepland voor een willekeurige tijd binnen het aantal dagen toegestaan. Als dit gebeurt wanneer het aantal dagen om bij te werken is verlopen, wordt de upgrade gepland vervalt op een willekeurig tijdstip binnen 24 uur nadat de computer opnieuw is opgestart.
    >     
    > Vanwege dit probleem computers die regelmatig worden afgesloten aan het einde van de werkdag een langer duren dan verwacht als de upgrade willekeurig geplande tijd binnen de normale werktijden niet bijwerken.

7. Begin in versie 1610, als u uitsluiten van clients wilt van de upgrade wordt uitgevoerd, klikt u op **uitsluiten opgegeven clients upgrade** en geef de verzameling moeten worden uitgesloten.

8.  Als u de clientinstallatiepakketten wilt kopiëren naar distributiepunten die geschikt zijn voor voorbereide inhoud, klikt u op **Clientinstallatiepakketten automatisch distribueren naar distributiepunten die zijn ingeschakeld voor voorbereide inhoud**.  

9. Klik op **OK** om de instellingen op te slaan en het dialoogvenster **Eigenschappen van hiërarchie-instellingen** te sluiten. Clients ontvangen deze instellingen wanneer ze de volgende keer het beleid downloaden.

>[!NOTE]
>Clientupdates gehandhaafd de Configuration Manager-onderhoudsvensters die u hebt geconfigureerd.

