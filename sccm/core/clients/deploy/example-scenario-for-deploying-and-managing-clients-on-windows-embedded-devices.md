---
title: Voorbeeldscenario - Windows Embedded-clients implementeren | Microsoft Docs
description: Zie een voorbeeldscenario voor het implementeren en beheren van System Center Configuration Manager-clients op Windows Embedded-apparaten.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10049c89-b37c-472b-b317-ce4f56cd4be7
caps.latest.revision: "8"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: c535bc62497b5ff0b60ca266c28630d890af3604
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="example-scenario-for-deploying-and-managing-system-center-configuration-manager-clients-on-windows-embedded-devices"></a>Voorbeeldscenario voor het implementeren en beheren van System Center Configuration Manager-clients op Windows Embedded-apparaten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit scenario wordt uitgelegd hoe u Windows Embedded write filter ingeschakeld kunt beheren apparaten met Configuration Manager.If uw ingesloten apparaten bieden geen ondersteuning voor schrijven van filters, functioneren zij als standaard Configuration Manager-clients en deze procedures zijn niet van toepassing.  

Coho Vineyard & Winery opent een bezoekerscentrum en moet de kiosken met Windows Embedded om interactieve presentaties worden uitgevoerd. Het gebouw voor het nieuwe bezoekerscentrum is geen dicht bij de IT-afdeling de kiosken moeten extern worden beheerd. Naast de software die de presentaties uitvoert, moeten deze apparaten uitgevoerd nieuwste antimalwaresoftware om te voldoen aan het beveiligingsbeleid van het bedrijf. De moeten kiosken 7 dagen per week, zonder uitvaltijd terwijl het Bezoekerscentrum open is.  

 Coho wordt al uitgevoerd voor Configuration Manager om apparaten op hun netwerk te beheren. Configuration Manager is geconfigureerd dat Endpoint Protection wordt uitgevoerd en software-updates en toepassingen worden geïnstalleerd. Echter, omdat het IT-team heeft Windows Embedded-apparaten niet wordt beheerd, aNs, de Configuration Manager-beheerder, een proefprogramma om twee kiosken in de HAL ontvangst beheren.   

 Voor het beheren van de Windows Embedded-apparaten met write filter is ingeschakeld, voert ANS de volgende stappen voor het installeren van Configuration Manager-client, de client te beschermen via Endpoint Protection en de interactieve presentatiesoftware te installeren.  

1.  ANS leest hoe Windows Embedded-apparaten maakt gebruik van schrijven van filters en hoe Configuration Manager dit eenvoudiger kan maken door automatisch uit te schakelen en opnieuw inschakelen van de schrijver filters voor het persistent maken van een software-installatie.  

     Zie voor meer informatie [Planning voor clientimplementatie op Windows Embedded-apparaten in System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

2.  Voordat ze de Configuration Manager-client hebt geïnstalleerd, maakt ANS een nieuwe query's gebaseerde apparaatverzameling voor de Windows Embedded-apparaten. Omdat het bedrijf standaardconventies voor namen gebruikt om hun computers te identificeren, kan ANS identificeren Windows Embedded-apparaten door de eerste zes letters van de computernaam: **WEMDVC**. Ze gebruikt de volgende WQL-query om deze verzameling te maken: **select SMS_R_System.NetbiosName from SMS_R_System where SMS_R_System.NetbiosName like "WEMDVC%"**  

     Met deze verzameling kan ze de Windows Embedded-apparaten beheren met verschillende configuratieopties van de andere apparaten. Ze gebruikt deze verzameling om processen voor het opnieuw starten te beheren, Endpoint Protection te implementeren met clientinstellingen en de interactieve presentatietoepassing te implementeren.  

     Zie [verzamelingen maken in System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

3.  Ans configureert de verzameling voor een onderhoudsvenster om er voor te zorgen dat opnieuw starten, dat nodig kan zijn voor de installatie van de presentatietoepassing en eventuele upgrades, niet wordt uitgevoerd tijdens openingstijden van het bezoekerscentrum. De openingstijden zijn van 09:00 tot 18:00 uur, maandag tot zondag. Ze configureert het onderhoudsvenster voor iedere dag, van 18:30 tot 06:00 uur.  

4.  Zie voor meer informatie [het gebruik van onderhoudsvensters in System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md).  

5.  Ans configureert vervolgens een aangepaste apparaatclientinstelling om de Endpoint Protection-client te installeren door **Ja** te selecteren voor de volgende instellingen en implementeert dan de aangepaste apparaatclientinstelling op de verzameling Windows Embedded-apparaten:  

    -   **Endpoint Protection-client op clientcomputers installeren**  

    -   **Voor Windows Embedded-apparaten met schrijffilters voert u de installatie van de Endpoint Protection-client door (computer moet opnieuw worden opgestart)**  

    -   **Installatie van Endpoint Protection-client en herstart buiten onderhoudsvensters toestaan**  

     Wanneer de Configuration Manager-client is geïnstalleerd, worden deze instellingen de Endpoint Protection-client installeert en ervoor te zorgen dat deze wordt doorgevoerd in het besturingssysteem als onderdeel van de installatie, in plaats van alleen naar de overlay worden geschreven. Het beveiligingsbeleid van het bedrijf schrijft voor dat antimalwaresoftware altijd moet zijn geïnstalleerd en Ans wil niet het risico lopen dat de kiosken ook maar voor even onbeschermd blijven als ze opnieuw worden gestart.  

    > [!NOTE]  
    >  Het opstarten dat nodig is voor de installatie van de Endpoint Protection-client gebeurt eenmaal, en wel tijdens de installatieperiode voor de apparaten en voordat het bezoekerscentrum in bedrijf gaat. In tegenstelling tot de periodieke implementatie van toepassingen of updates van softwaredefinities worden de volgende keer dat de Endpoint Protection-client is geïnstalleerd op hetzelfde apparaat waarschijnlijk wanneer het bedrijf een upgrade naar de volgende versie van Configuration Manager uitvoert.  

     Zie voor meer informatie [Endpoint Protection configureren in System Center Configuration Manager](../../../protect/deploy-use/configure-endpoint-protection.md).  

6.  De configuratie-instellingen voor de client in plaats nu bereidt ANS de Configuration Manager-clients installeert. Voordat ze de clients kan installeren moet ze eerst de schrijffilter op de Windows Embedded-apparaten handmatig uitschakelen. Ze leest de OEM-documentatie bij de kiosken en volgt de instructies op om de schrijffilters uit te schakelen.  

     ANS wijzigt de naam van het apparaat zodat het bedrijf standaard naamconventie indeling gebruikt en de client handmatig installeert door CCMSetup uitgevoerd met de volgende opdracht vanaf een toegewezen station met daarop de bronbestanden van de client: **/MP:mpserver.cohovineyardandwinery.com CCMSetup.exe SMSSITECODE = CO1**  

     Met deze opdracht wordt de client geïnstalleerd en toegewezen aan het beheerpunt dat het intranet FQDN bevat van **mpserver.cohovineyardandwinery.com**en wordt de client toegewezen aan de primaire site die **CO1**wordt genoemd.  

     Ans weet dat het altijd even duurt voordat clients zijn geïnstalleerd en hun status naar de site retourneren. Ze wacht dus voordat ze bevestigt dat de clients zijn geïnstalleerd, zijn toegewezen aan de site en als clients worden weergegeven in de verzameling die ze heeft gemaakt voor Windows Embedded-apparaten.  

     Als extra bevestiging controleert de eigenschappen van Configuration Manager in het Configuratiescherm op de apparaten ze en vergelijkt ze met de standaard Windows-computers die worden beheerd door de site. Op het tabblad **Onderdelen** wordt bij de **Agent voor hardware-inventarisatie** **Ingeschakeld**weergegeven en op het tabblad **Acties** zijn 11 acties beschikbaar, waaronder **Evaluatiecyclus voor installatie van toepassingen** en **Verzamelfase zoekgegevens**.  

     Wanneer Ans zeker weet dat de clients zijn geïnstalleerd, toegewezen en clientbeleid ontvangen van het beheerpunt, schakelt ze handmatig de schrijffilters in aan de hand van de OEM-instructies.  

     Zie voor meer informatie:  

    -   [Clients implementeren op Windows-computers in System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

    -   [Clients toewijzen aan een site in System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md)  

7.  Nu dat de Configuration Manager-client is geïnstalleerd op Windows Embedded-apparaten, bevestigt ANS dat ze deze op dezelfde manier beheren kan als de standaard Windows-clients. Bijvoorbeeld, vanuit de Configuration Manager-console kan ze op afstand deze beheren met behulp van beheer op afstand, clientbeleid voor en hun eigenschappen en hardware-inventaris van client weergeven.  

     Deze apparaten worden samengebracht in een Active Directory-domein, worden ze heeft geen handmatig goed te keuren als vertrouwde clients en bevestigt via de Configuration Manager-console dat ze zijn goedgekeurd.  

     Zie [How to manage clients in System Center Configuration Manager](../../../core/clients/manage/manage-clients.md) (Clients beheren in System Center Configuration Manager) voor meer informatie.  

8.  Voor de installatie van de interactieve presentatiesoftware voert Ans de **wizard Software implementeren** uit en configureert een verplichte toepassing. Op de pagina **Gebruikerservaring** van de wizard, in de rubriek **Verwerking van schrijffilters voor Windows Embedded-apparaten** , accepteert ze de standaardoptie voor het selecteren van **Wijzigingen doorvoeren bij deadline of tijdens onderhoud (opnieuw opstarten noodzakelijk)**.  

     Ans behoudt deze standaardoptie voor schrijffilters om er zeker van te zijn dat de toepassing blijft draaien na opnieuw opstarten zodat deze altijd beschikbaar is voor de bezoekers die de kiosken gebruiken. Het dagelijkse onderhoudsvenster biedt een opslagperiode waarin het opstarten voor installaties en updates kan plaatsvinden.  

     Ans implementeert de toepassing op de verzameling met Windows Embedded-apparaten.  

     Zie [Toepassingen implementeren met System Center Configuration Manager](../../../apps/deploy-use/deploy-applications.md) voor meer informatie.  

9. Voor de configuratie van definitie-updates voor Endpoint Protection, gebruikt Ans softwareupdates en voert de wizard Regel voor automatische implementatie maken uit. Ze selecteert het sjabloon **Definition-updates** om de wizard vooraf in te vullen met voor Endpoint Protection compatibele instellingen.  

     Dit zijn onder andere de volgende instellingen op de pagina **Gebruikerservaring** :  

    -   **Deadlinegedrag**: De **Software-installatie** selectievakje niet is ingeschakeld.  

    -   **Schrijffilters voor Windows Embedded-apparaten**: De **wijzigingen doorvoeren bij deadline of tijdens onderhoud (opnieuw opstarten noodzakelijk)** selectievakje niet is ingeschakeld.  

     Ans houdt deze standaardinstellingen. Met deze twee opties en deze configuratie kunnen alle software-updatedefinities voor Endpoint Protection overdag worden geïnstalleerd in de overlay en hoeven de installatie en het doorvoeren ervan niet te worden uitgesteld voor tijdens het onderhoudsvenster. Deze configuratie komt het beste overeen met het beveiligingsbeleid van het bedrijf voor computers om bijgewerkte antimalware te gebruiken.  

    > [!NOTE]  
    >  In tegenstelling tot software-installaties voor toepassingen kunnen software-updatedefinities voor Endpoint Protection heel vaak gebeuren, zelfs meerdere keren per dag. Het gaat vaak om kleine bestanden. Voor dit soort beveiligingsimplementaties kan het vaak nuttig zijn altijd naar de overlay te installeren in plaats van te wachten op het onderhoudsvenster. Configuration Manager-client installeert opnieuw snel de definitie-updates voor software als het apparaat opnieuw wordt opgestart omdat deze actie een evaluatie-controle initieert en niet wacht totdat de geplande evaluatie.  

     Ans selecteert de verzameling met Windows Embedded-apparaten voor de automatisch implementatieregel.  

     Zie voor meer informatie.  
                  Stap 3: Software-Updates voor het leveren van definitie-Updates aan clientcomputers in Configuration Manager configureren [Endpoint Protection configureren in System Center Configuration Manager](../../../protect/deploy-use/configure-endpoint-protection.md)  

10. Ans besluit een onderhoudstaak te configureren die regelmatig alle wijzigingen doorvoert op de overlay. Deze taak is de ondersteuning van de implementatie van software-updatedefinities om het aantal updates te verminderen dat toeneemt en iedere keer wanneer het apparaat opnieuw wordt gestart opnieuw geïnstalleerd moet worden. Zij heeft ondervonden dat hierdoor de antimalware-programma's efficiënter worden uitgevoerd.  

    > [!NOTE]  
    >  Deze software-updatedefinities zouden automatisch worden doorgevoerd naar de installatiekopie als de ingesloten apparaten een andere beheertaak uitvoerden voor het doorvoeren van de wijzigingen. Door de installatie van een nieuwe versie van de interactieve presentatiesoftware zouden bijvoorbeeld ook de wijzigingen voor software-updatedefinities worden doorgevoerd. Of door de installatie van standaardsoftware-updates iedere maand tijdens het onderhoudsvenster zouden ook de wijzigingen voor software-updatedefinities worden doorgevoerd. In dit scenario, waarin standaardsoftware-updates niet worden uitgevoerd en de interactieve presentatiesoftware naar alle waarschijnlijkheid niet vaak wordt bijgewerkt, kan het maanden duren voordat de software-definitieupdates automatisch worden doorgevoerd naar de installatiekopie.  

     Ans maakt eerst een aangepaste takenreeks zonder instellingen en met alleen de naam. Zij voert de wizard Takenreeks maken uit:  

    1.  Op de pagina **Nieuwe takenreeks maken** selecteert ze **Nieuwe aangepaste takenreeks maken**en klikt vervolgens op **Volgende**.  

    2.  Op de pagina **Takenreeksinformatie** voert ze **Maintenance task to commit changes on embedded devices** in voor de naam van de takenreeks en klikt vervolgens op **Volgende**.  

    3.  Op de pagina **Samenvatting** selecteert ze **Volgende**en voltooit de wizard.  

     Ans implementeert vervolgens de aangepaste takenreeks op de verzameling met de Windows Embedded-apparaten en stelt de planning in op iedere maand uitvoeren. Ze schakelt het selectievakje **Wijzigingen doorvoeren bij deadline of tijdens onderhoud (opnieuw opstarten noodzakelijk)** in als onderdeel van de implementatie-instellingen om de wijzigingen na het opnieuw opstarten te behouden. Voor de configuratie van deze implementatie selecteert Ans de aangepaste takenreeks die ze zojuist heeft gemaakt en klikt vervolgens op het tabblad **Start** in de **Implementatie** -groep op **Implementeren** om de wizard Software implementeren te starten:  

    1.  Op de pagina **Algemeen** selecteert ze de verzameling met de Windows Embedded-apparaten en klikt vervolgens op **Volgende**.  

    2.  Op de pagina **Implementatie-instellingen** selecteert ze het **Doel** van **Vereist**en klikt vervolgens op **Volgende**.  

    3.  Op de pagina **Planning** klikt ze op **Nieuw** om een wekelijkse planning te specificeren tijdens het onderhoudsvenster en klikt vervolgens op **Volgende**.  

    4.  Ze voltooit de wizard zonder verdere wijzigingen aan te brengen.  

     Zie voor meer informatie.  
                  [Takenreeksen beheren om te automatiseren in System Center Configuration Manager](../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md).  

11. Voor automatische uitvoering van de kiosken, schrijft Ans een script om de apparaten te configureren voor de volgende instellingen:  

    -   Automatisch aanmelden met behulp van een gastaccount zonder wachtwoord.  

    -   Voer de interactieve presentatiesoftware automatisch uit bij het opstarten.  

     Jane gebruikt pakketten en programma's om dit script te implementeren voor de in Windows ingesloten apparaatverzameling. Wanneer ze de wizard software implementeren uitvoert, selecteert ze opnieuw het selectievakje **Wijzigingen doorvoeren bij deadline of tijdens het onderhoud (vereist opnieuw opstarten)** om de wijzigingen vast te leggen na een opnieuw opstarten.  

     Zie [Pakketten en programma's in System Center Configuration Manager](../../../apps/deploy-use/packages-and-programs.md) voor meer informatie.  

12. De volgende ochtend controleert Jane de in Windows ingesloten apparaten. Ze bevestigt de volgende opties:  

    -   De kiosk wordt automatisch aangemeld met de gastaccount.  

    -   De interactieve presentatiesoftware wordt uitgevoerd.  

    -   De Endpoint Protection-client wordt geïnstalleerd en heeft de laatste software-update.  

    -   Dat het apparaat opnieuw opstartte tijdens het onderhoudsvenster.  

     Zie voor meer informatie:  

    -   [Endpoint Protection in System Center Configuration Manager controleren](../../../protect/deploy-use/monitor-endpoint-protection.md)  

    -   [Toepassingen bewaken met System Center Configuration Manager](/sccm/apps/deploy-use/monitor-applications-from-the-console)  

13. Jane bewaakt de kiosken en rapporteert het succesvol beheer ervan aan haar manager. Als gevolg hiervan worden 20 kiosken besteld voor het bezoekerscentrum.  

     Om te voorkomen dat de handmatige installatie van de Configuration Manager-client, die handmatig uit te schakelen en vervolgens het inschakelen van de schrijffilters vereist, zorgt Jane ervoor dat de bestelling een aangepaste installatiekopie die reeds de installatie en sitetoewijzing van Configuration Manager-client bevat bevat. Bovendien krijgen de apparaten een naam volgens het naamformaat van het bedrijf.  

     De kiosken worden geleverd aan het bezoekerscentrum een week voor het opent. Gedurende die tijd zijn de kiosken verbonden met het netwerk, alle apparaatbeheer ervoor is automatisch en er is geen lokale beheerder vereist. Jane bevestigt dat de kiosken werken zoals vereist:  

    -   De clients op de kiosken vervolledigen sitetoewijzing en downloaden de vertrouwde basissleutel van Active Directory Domain Services.  

    -   De clients op de kiosken worden automatisch toegevoegd aan de in Windows ingesloten apparaatverzameling en geconfigureerd met het onderhoudsvenster.  

    -   De Endpoint Protection-client wordt geïnstalleerd en heeft de laatste software-update definities voor antimalware bescherming.  

    -   De interactieve presentatiesoftware is geïnstalleerd en draait automatisch, klaar voor gebruikers.  

14. Na de initiële installatie, kan opnieuw opstarten, wat vereist kan zijn voor updates, alleen gebeuren als het bezoekerscentrum gesloten is;  
