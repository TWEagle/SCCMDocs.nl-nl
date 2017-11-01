---
title: Sites verwijderen
titleSuffix: Configuration Manager
description: Gebruik deze informatie als richtlijn om een System Center Configuration Manager-site te verwijderen.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d466edd2-97f0-44c1-a73e-d71abbdbf4a8
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8a8571e844be796c7f87f7742dce6c311d7195ea
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="uninstall-sites-and-hierarchies-in-system-center-configuration-manager"></a>Sites en hiërarchieën verwijderen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de volgende informatie als richtlijn als u nodig hebt om een System Center Configuration Manager-site te verwijderen.  

Buiten gebruik stellen een hiërarchie met meerdere sites, de volgorde van de verwijdering is belangrijk. Begin met het verwijderen van de sites aan de onderkant van de hiërarchie en vervolgens omhoog:  

1.  Verwijder secundaire sites gekoppeld aan primaire sites.  
2.  Primaire sites verwijderen.
3.  Nadat alle primaire sites zijn verwijderd, kunt u de centrale beheersite verwijderen.  


##  <a name="BKMK_RemoveSecondarysite"></a> Een secundaire site uit een hiërarchie verwijderen  
U kunt verplaatsen van een secundaire site of opnieuw toewijzen van een secundaire site naar een nieuwe bovenliggende primaire site. Om te worden verwijderd uit een hiërarchie, moet een secundaire site worden verwijderd uit de direct bovenliggende site. Gebruik de Wizard secundaire Site verwijderen uit de Configuration Manager-console om een secundaire site te verwijderen. Wanneer u een secundaire site verwijdert, moet u kiezen of u wilt verwijderen of deze verwijderen:  

-   **De secundaire site verwijderen**. Gebruik deze optie om het verwijderen van een functionele secundaire site die toegankelijk is vanaf het netwerk. Deze optie verwijdert Configuration Manager van de secundaire siteserver en verwijdert vervolgens alle informatie over de site en de daarbij behorende bronnen uit de sitehiërarchie van Configuration Manager. Als Configuration Manager SQL Server Express als onderdeel van de secundaire site-installatie installeerde, Configuration Manager wordt SQL Express deïnstalleren wanneer het de secundaire site deïnstalleert. Als SQL Server Express is geïnstalleerd voordat u de secundaire site hebt geïnstalleerd, verwijdert Configuration Manager niet SQL Server Express.  

-   **De secundaire site verwijderen**. Gebruik deze optie als u een van de volgende wordt voldaan:  

    -   Een secundaire site kan niet installeren  
    -   De secundaire site blijft in de Configuration Manager-console worden weergegeven nadat u deze eerst verwijderen

    Deze optie verwijdert alle informatie over de site en de daarbij behorende bronnen uit de Configuration Manager-hiërarchie, maar blijft Configuration Manager geïnstalleerd op de secundaire siteserver.  

    > [!NOTE]  
    >  Ook kunt u de Hierarchy Maintenance Tool en de **/delsite** optie om een secundaire site te verwijderen. Zie [Hierarchy Maintenance Tool (Preinst.exe) voor System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md) voor meer informatie.  

#### <a name="to-uninstall-or-delete-a-secondary-site"></a>Een secundaire site deïnstalleren of verwijderen  

1.  Controleer of de gebruiker met beheerdersrechten die het installatieprogramma uitvoert beschikt over de volgende beveiligingsrechten:  

    -   Beheerrechten op de secundaire sitecomputer  
    -   Lokale beheerdersrechten op de externe Sitedatabaseserver voor de primaire site als deze extern  
    -   Beveiligingsrol infrastructuurbeheerder of volledige beheerder op de bovenliggende primaire site  
    -   Sysadmin-rechten op de sitedatabase van de secundaire site  

2.  Selecteer in de Configuration Manager-console **beheer**.  
3.  In de **beheer** werkruimte Vouw **siteconfiguratie**, en selecteer vervolgens **Sites**.  
4.  Selecteer de secundaire siteserver die u wilt verwijderen.  
5.  Op de **Start** tabblad, in de **Site** Selecteer **verwijderen**.  
6.  Selecteer op de pagina **Algemeen** of u de secundaire site wilt deïnstalleren of verwijderen, en klik vervolgens op **Volgende**.  
7.  Op de **samenvatting** pagina, Controleer de instellingen en selecteer vervolgens **volgende**.  
8.  Op de **voltooiing** pagina **sluiten** de wizard wilt afsluiten.  

##  <a name="BKMK_UninstallPrimary"></a> Een primaire site verwijderen  
U kunt de installatie van Configuration Manager voor het verwijderen van een primaire site die geen secundaire site aan gekoppeld uitvoeren. Voordat u een primaire site deïnstalleert, moet u het volgende overwegen:  

-   Configuration Manager-clients zich binnen de grenzen die zijn geconfigureerd op de site, en de primaire site deel uitmaakt van een Configuration Manager-hiërarchie, overweeg bij de grenzen aan een andere primaire site in de hiërarchie voordat u de primaire site verwijderen.  
-   Wanneer de primaire siteserver niet langer beschikbaar is, moet u de Hierarchy Maintenance Tool op de centrale beheersite gebruiken om de primaire site uit de sitedatabase te verwijderen. Zie [Hierarchy Maintenance Tool (Preinst.exe) voor System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md) voor meer informatie.  

Gebruik de volgende procedure gebruiken om een primaire site te deïnstalleren.  

#### <a name="to-uninstall-a-primary-site"></a>Een primaire site deïnstalleren  

1.  Controleer of de gebruiker met beheerdersrechten die het installatieprogramma uitvoert beschikt over de volgende beveiligingsrechten:  

    -   Lokale beheerdersrechten op de server van centrale beheersite  
    -   Lokale beheerdersrechten op de externe Sitedatabaseserver voor de centrale beheersite, als deze extern
    -   Sysadmin-rechten op de sitedatabase van de centrale beheersite  
    -   Lokale beheerdersrechten op de computer van de primaire site  
    -   Lokale beheerdersrechten op de externe Sitedatabaseserver voor de primaire site als deze extern  
    -   De naam van een gebruiker die is gekoppeld aan de beveiligingsrol infrastructuurbeheerder of volledige beheerder op de centrale beheersite  

2.  Configuration Manager Setup starten op de primaire siteserver door middel van een van de volgende methoden:  

    -   Op **Start**, selecteer **Setup van Configuration Manager**.  
    -   Open Setup.exe vanuit &lt; *ConfigMgrInstallationMedia*> \SMSSETUP\BIN\X64.  
    -   Open Setup.exe vanuit &lt; *ConfigMgrInstallationPath*> \BIN\X64.  

3.  Op de **voordat u begint** pagina **volgende**.  
4.  Op de **aan de slag** pagina **een Configuration Manager-site verwijderen**, en selecteer vervolgens **volgende**.  
5.  Op de **verwijderen van de Configuration Manager-Site**, opgeven of de sitedatabase verwijderen uit de primaire siteserver en of u wilt verwijderen van de Configuration Manager-console. Standaard verwijdert het installatieprogramma beide items.  

    > [!IMPORTANT]  
    >  Als er een secundaire site aan de primaire site gekoppeld is, moet u eerst de secundaire site verwijderen voordat u de primaire site kunt deïnstalleren.  

6.  Selecteer **Ja** om te bevestigen dat de verwijdering van de primaire site van Configuration Manager.  

##  <a name="BKMK_UninstallPrimaryDistViews"></a> Een primaire site verwijderen die is geconfigureerd met gedistribueerde weergaven  
 Voordat u een onderliggende primaire site die weergaven ingeschakeld voor de centrale beheersite de replicatiekoppeling gedistribueerde verwijdert, moet u gedistribueerde weergaven uitschakelen in uw hiërarchie. Gebruik de volgende informatie gedistribueerde weergaven uitschakelen voordat u een primaire site verwijderen.  

#### <a name="to-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a>Een primaire site deïnstalleren die geconfigureerd is met gedistribueerde weergaven  

1.  Voordat u een primaire site verwijdert, moet u gedistribueerde weergaven op elke koppeling in de hiërarchie tussen de centrale beheersite en een primaire site uitschakelen.  
2.  Nadat u gedistribueerde weergaven op elke koppeling hebt uitgeschakeld, moet u bevestigen dat de gegevens van de primaire site wordt op de centrale beheersite opnieuw. Voor het bewaken van de initialisatie van gegevens in de Configuration Manager-console in de **bewaking** werkruimte bekijken van de koppeling op de **databasereplicatie** knooppunt.  
3.  Nadat de gegevens succesvol geherinitialiseerd zijn op de centrale beheersite, kunt u de primaire site deïnstalleren. Zie voor het verwijderen van een primaire site [een primaire site deïnstalleren](#BKMK_UninstallPrimary).  
4.  Wanneer de primaire site volledig gedeïnstalleerd is, kunt u gedistribueerde weergaven op koppelingen naar primaire sites opnieuw configureren.  

    > [!IMPORTANT]  
    >  Als u de primaire site verwijderen voordat u gedistribueerde weergaven op elke site uitschakelt, of voordat de gegevens van de primaire site succesvol geherinitialiseerd zijn op de centrale beheersite, kan de replicatie van gegevens tussen primaire sites en de centrale beheersite mislukken. In dit scenario moet u gedistribueerde weergaven voor elke koppeling in de sitehiërarchie uitschakelen en vervolgens, nadat de gegevens succesvol geherinitialiseerd zijn op de centrale beheersite, u kunt gedistribueerde weergaven opnieuw configureren.  

##  <a name="BKMK_UninstallCAS"></a> De centrale beheersite verwijderen  
 U kunt de installatie van Configuration Manager voor het verwijderen van een centrale beheersite die geen onderliggende primaire sites uitvoeren. Gebruik de volgende procedure om de centrale beheersite te deïnstalleren.  

#### <a name="to-uninstall-a-central-administration-site"></a>Verwijderen van een centrale beheersite  

1.  Controleer of de gebruiker met beheerdersrechten die het installatieprogramma uitvoert beschikt over de volgende beveiligingsrechten:  

    -   Lokale beheerdersrechten op de server van centrale beheersite  
    -   Lokale beheerdersrechten op de Sitedatabaseserver voor de centrale beheersite als de Sitedatabaseserver is niet geïnstalleerd op de siteserver 

2.  Configuration Manager Setup starten op de server van centrale beheersite met behulp van een van de volgende methoden:  

    -   Klik op **Start**op **Configuration Manager Setup**.  
    -   Open Setup.exe vanuit &lt; *ConfigMgrInstallationMedia*> \SMSSETUP\BIN\X64.  
    -   Open Setup.exe vanuit &lt; *ConfigMgrInstallationPath*> \BIN\X64.  

3.  Op de **voordat u begint** pagina **volgende**.  
4.  Op de **aan de slag** pagina **een Configuration Manager-site verwijderen**, en selecteer vervolgens **volgende**.  
5.  Op de **verwijderen van de Configuration Manager-Site**, opgeven of de sitedatabase verwijderen uit de centrale beheersiteserver en of u wilt verwijderen van de Configuration Manager-console. Standaard verwijdert het installatieprogramma beide items.  

    > [!IMPORTANT]  
    >  Als er een primaire site aan de centrale beheersite gekoppeld is, moet u eerst de primaire site verwijderen voordat u de centrale beheersite kunt deïnstalleren.  

6.  Selecteer **Ja** om te bevestigen dat het verwijderen van de centrale beheersite van Configuration Manager.  
