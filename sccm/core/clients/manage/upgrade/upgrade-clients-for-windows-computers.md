---
title: Clients bijwerken
titleSuffix: Configuration Manager
description: Clients op Windows-computers in System Center Configuration Manager upgraden.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6143fd47-48ec-4bca-b53b-5b9b9f067bc3
caps.latest.revision: "11"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 7e2319aaf8f1195118211493eeecb9f6d1872d2d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-upgrade-clients-for-windows-computers-in-system-center-configuration-manager"></a>Clients voor Windows-computers bijwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt de client op Windows-computers met clientinstallatiemethoden of de functies voor automatische Clientupgrade in Configuration Manager bijwerken. De volgende clientinstallatiemethoden zijn geldige manieren om de clientsoftware op Windows-computers bij te werken:  

-   Installatie van Groepsbeleid  

-   Aanmeldingscriptinstallatie  

-   Handmatige installatie  

-   Upgrade-installatie  

 Als u geïnteresseerd bent in het bijwerken van de client met een clientinstallatiemethode, meer informatie over het gebruik van deze methoden [clients implementeren op Windows-computers in System Center Configuration Manager](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md).

 Vanaf versie 1610, kunt u clients uitsluiten van wordt bijgewerkt door te geven van een groep voor uitsluiting. Zie voor meer informatie [upgraden clients voor Windows-computers uitsluiten](exclude-clients-windows.md).  


> [!TIP]  
>  Als u een upgrade van uw serverinfrastructuur uitvoert vanaf een eerdere versie van Configuration Manager \(zoals Configuration Manager 2007 of System Center 2012 Configuration Manager\), wordt u aangeraden de serverupgrades, inclusief alle updates van Current Branch, uit te voeren voordat u een upgrade uitvoert van de Configuration Manager-clients.   De nieuwste update van Current Branch bevat de meest recente versie van de client, zodat u de clientupgrades het best kunt uitvoeren nadat u alle Configuration Manager-updates hebt geïnstalleerd die u wilt gebruiken.

> [!NOTE]
> Als u van plan bent om de site opnieuw toewijzen voor de clients tijdens de upgrade, kunt u de nieuwe site met de client.msi-eigenschap SMSSITECODE opgeven. Als u automatisch voor de SMSSITECODE gebruikt, moet u ook opgeven SITEREASSIGN = TRUE om toe te staan van automatische site opnieuw toewijzen plaatsvindt tijdens de upgrade. Zie voor meer informatie [SMSSITECODE](../../deploy/about-client-installation-properties.md#smssitecode).

## <a name="use-automatic-client-upgrade"></a>Automatische clientupgrade gebruiken  
 U kunt ook de Configuration Manager om de clientsoftware automatisch wordt bijgewerkt naar de meest recente clientversie van de Configuration Manager-als Configuration Manager identificeert die een client die is aan de Configuration Manager-hiërarchie toegewezen lager dan de versie die wordt gebruikt in de hiërarchie is configureren. Dit scenario omvat het bijwerken van de client naar de nieuwste versie bij toewijzing aan een Configuration Manager-site.  

 Een client kan automatisch worden bijgewerkt in de volgende scenario's:  

-   De clientversie is lager dan de versie die in de hiërarchie wordt gebruikt.  

-   Op de client op de centrale beheersite is een taalpakket geïnstalleerd en de bestaande client heeft dit niet.  

-   Een vereiste voor een client in de hiërarchie heeft een verschillende versie dan de op de client geïnstalleerde.  

-   Een of meer clientinstallatiebestanden hebben een verschillende versie.  

> [!NOTE]  
>  U kunt het rapport uitvoeren **telling van Configuration Manager-clients op clientversies** in de rapportmap **Site - clientinformatie** voor het identificeren van de verschillende versies van Configuration Manager-client in uw hiërarchie.  

 Configuration Manager maakt een upgradepakket voor het standaard dat automatisch wordt verzonden naar alle distributiepunten in de hiërarchie. Als u wijzigingen in het clientpakket op de centrale beheersite aanbrengt, bijvoorbeeld een clienttaalpakket toevoegen Configuration Manager automatisch updates van het pakket en distribueert het naar alle distributiepunten in de hiërarchie. Als de automatische clientupgrade is ingeschakeld, zal het nieuwe clienttaalpakket automatisch op elke client worden geïnstalleerd.  

> [!NOTE]  
>  Configuration Manager de clientupgrade wordt niet automatisch verzenden pakket naar Configuration Manager cloud-gebaseerde distributiepunten.  

 Het is raadzaam dat u automatische clientupgrades tussen uw hiërarchie inschakelen. Hiermee voorkomt u dat uw clients bijgewerkt met een minimale administratieve overhead.  

 De volgende procedure gebruiken om automatische clientupgrade te configureren. Automatische clientupgrade moet op een centrale beheersite worden geconfigureerd en deze configuratie is van toepassing op alle clients in de hiërarchie.  

### <a name="to-configure-automatic-client-upgrades"></a>Automatische clientupgrades configureren  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Sites**.  

3.  Klik op **Hiërarchie-instellingen** op het tabblad **Start** , in de groep **Sites**.  

4.  Controleer op het tabblad **Clientupgrade** van het dialoogvenster **Eigenschappen van hiërarchie-instellingen** de versie en datum van de productieclient en zorg ervoor dat dit de versie is die u wilt gebruiken voor het bijwerken van Windows-computers.  Als niet de verwachte clientversie wordt weergegeven, moet u het niveau van de pre-productieclient mogelijk verhogen naar productie. Zie voor meer informatie [clientupgrades testen in pre-productieverzameling in System Center Configuration Manager](../../../../core/clients/manage/upgrade/test-client-upgrades.md).  

5.  Klik op **Upgrade uitvoeren voor alle clients in de hiërarchie met gebruik van productieversie van client** en klik in het bevestigingsdialoogvenster op **OK** .  

6.  Als u niet wilt dat clientupgrades worden toegepast op servers, klikt u op **Geen upgrade op servers uitvoeren**.  

7.  Geef het aantal dagen op waarin computers de client moeten upgraden na het ontvangen van het clientbeleid. De client wordt bijgewerkt aan een random interval binnen dit aantal dagen. Dit voorkomt dat scenario's met een groot aantal clientcomputers gelijktijdig worden bijgewerkt.

    > [!NOTE]
    > Een computer moet worden uitgevoerd om de upgrade van de client. Als een computer wordt niet uitgevoerd als deze is gepland voor het ontvangen van de upgrade, wordt de upgrade wordt niet uitgevoerd. In plaats daarvan wanneer de computer opnieuw wordt opgestart, nog een upgrade is gepland voor een willekeurige tijd binnen het aantal dagen toegestaan. Als dit gebeurt nadat het aantal dagen om bij te werken is verlopen, wordt de upgrade worden gepland om te worden uitgevoerd op een willekeurig tijdstip binnen 24 uur nadat de computer opnieuw is opgestart.
    >     
    > Vanwege dit gedrag computers die regelmatig worden afgesloten aan het einde van de werkdag kunnen duren voordat een langer dan verwacht als het willekeurig geplande tijd voor de upgrade niet binnen de normale werkuren bijwerken.

7. Vanaf versie 1610, als u uitsluiten van clients wordt bijgewerkt wilt, klikt u op **uitsluiten opgegeven clients upgrade** en geef de verzameling moeten worden uitgesloten.

8.  Als u de clientinstallatiepakketten wilt kopiëren naar distributiepunten die geschikt zijn voor voorbereide inhoud, klikt u op **Clientinstallatiepakketten automatisch distribueren naar distributiepunten die zijn ingeschakeld voor voorbereide inhoud**.  

9. Klik op **OK** om de instellingen op te slaan en het dialoogvenster **Eigenschappen van hiërarchie-instellingen** te sluiten. Clients ontvangen deze instellingen wanneer ze de volgende keer het beleid downloaden.

>[!NOTE]
>Clientupgrades voldoen aan de Configuration Manager-onderhoudsvensters die u hebt geconfigureerd.
