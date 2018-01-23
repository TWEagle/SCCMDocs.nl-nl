---
title: Technische Preview 1801 | Microsoft Docs
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1801 voor System Center Configuration Manager.
ms.custom: na
ms.date: 01/19/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a352ae0-355f-4fcf-b863-fb0654f51c52
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f4be3ffe817392bf8fefdcf4e481c739778025ff
ms.sourcegitcommit: db9978135d7a6455d83dbe4a5175af2bdeaeafd8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/22/2018
---
# <a name="capabilities-in-technical-preview-1801-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1801 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1801 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. 

Bekijk [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview) voordat u deze versie van de technical preview installeert. Dit artikel familiarizes u met de algemene vereisten en beperkingen voor het gebruik van een technical preview hoe tussen versies en hoe u feedback kunt bijwerken.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
**Known Issues in this Technical Preview:**
-->
**Bekende problemen in deze Technical Preview:**
-   **Bijwerken naar een nieuwe preview-versie mislukt wanneer u een siteserver in de passieve modus hebt**. Als u hebt een [primaire siteserver in de passieve modus](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), en vervolgens u de passieve modus siteserver verwijderen moet voordat u bijwerkt naar deze nieuwe preview-versie. Nadat de site de update is voltooid, kunt u de passieve modus siteserver opnieuw installeren.

  Verwijderen van de siteserver van de passieve modus:
  1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **siteconfiguratie**  >  **Servers en sitesysteemrollen**, en selecteer vervolgens de passieve modus-siteserver.
  2. In de **sitesysteemrollen** deelvenster met de rechtermuisknop op de **siteserver** rol, en kies vervolgens **rol verwijderen**.
  3. Met de rechtermuisknop op de siteserver van de passieve modus, en kies vervolgens **verwijderen**.
  4. Nadat de siteserver verwijdert, op de primaire siteserver van de actieve service opnieuw starten de **CONFIGURATION_MANAGER_UPDATE**.
<!--sms 489412-->


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Section Template
##  FEATURE
<-- TFS ID - need to fix comment md here
### Procedure 1
### Try it out!  
 Try to complete the tasks. Then send **Feedback** from the **Home** tab of the ribbon letting us know how it worked.
 -  Task 1
 -  Task 2              
-->



## <a name="create-phased-deployments"></a>Gefaseerde implementaties maken
<!-- 1357405 -->
Gefaseerde implementaties automatiseren een gecoördineerde, geordende rollout van software zonder dat er meerdere implementaties. In deze Technical Preview-versie, kan de wizard gefaseerde implementatie worden uitgevoerd voor takenreeksen in de beheerconsole. Implementaties worden echter niet gemaakt. 

### <a name="try-it-out"></a>Probeer het nu!  
  Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.
 
**Een gefaseerde implementatie voor een takenreeks maken** </br>
1. In de **softwarebibliotheek** werkruimte Vouw **besturingssystemen**, en selecteer **Takenreeksen**.
2. Met de rechtermuisknop op een bestaande takenreeks en selecteert u **gefaseerde implementatie maken**. 
3. Op de **algemene** tabblad, geef de gefaseerde implementatie een naam, beschrijving (optioneel) en selecteer **automatisch maken standaard test en productie fasen**. 
4. Vul de **verzameling testfase** en **Productieverzameling** velden. Selecteer **volgende**.
5. Op de **instellingen** tabblad, kiest u een optie voor elk van de schema-instellingen en selecteer **volgende** wanneer u klaar. 
6. Op de **fasen** tabblad, een van de fasen Bewerk indien nodig en klik vervolgens op **volgende**.
7. Bevestig uw selecties op de **samenvatting** tabblad en klik vervolgens op **volgende** om door te gaan.

## <a name="co-management-reporting"></a>Mede management reporting
<!-- 1356648 -->
Als u de [mede management](/sccm/core/clients/manage/co-management-overview) mogelijkheden, kunt u nu een dashboard met informatie over het beheer van CO weergeven in uw omgeving. Navigeer in de Configuration Manager-console naar de **bewaking** werkruimte Vouw **gereedheid voor Upgrade**, en selecteer de **mede management** dashboard. Het dashboard bevat de volgende tegels:
- **Naast beheerde apparaten**: het percentage apparaten in uw omgeving die u hebt ingeschakeld voor het beheer van CO
- **OS-distributie**: de uitsplitsing van besturingssystemen (OS) door versie. Dit diagram maakt gebruik van de volgende groepen:
   - Windows 7 & 8.x
   - Windows 10 lager is dan 1709
   - Windows 10 1709 en hoger
  > [!NOTE] 
  > Windows 10 versie 1709 en hoger, is een vereiste voor CO-management
- **Mede Beheerstatus**: de uitsplitsing van apparaat slagen of mislukken in de volgende categorieën:
   - Geslaagd, hybride Azure AD join
   - Geslaagd, Azure AD die lid zijn van
   - Fout: Automatische inschrijving is mislukt
- **Overgang van de werkbelasting**: een staafdiagram waarin het aantal apparaten dat u is overgegaan naar Microsoft Intune voor de drie beschikbare werkbelastingen: 
   - Nalevingsbeleid
   - Toegang tot bedrijfsbronnen
   - Windows Update voor bedrijven

### <a name="prerequisites"></a>Vereisten
- De computer waarop de Configuration Manager-console moet Internet Explorer 9 of hoger.



## <a name="improvements-to-automatic-deployment-rule-evaluation-schedule"></a>Verbeteringen aan automatische implementatie regel evaluatieplanning
<!-- 1357133 -->
Op basis van uw [feedback van gebruikers stem](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8819518-software-update-patch-tuesday-scheduling), kunt u nu automatische implementatie (ADR) Regeltoepassing verschoven ten opzichte van een base dag plannen. Een offset van twee dagen na de tweede dinsdag van de maand wordt de regel bijvoorbeeld geëvalueerd op donderdag. 

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan. <br/>

**Een aangepaste planning die wordt geëvalueerd en ADR offset maken van een base dag** </br>
1.  In de **softwarebibliotheek** werkruimte Vouw **Software-Updates**, en selecteer **regels voor automatische implementatie**.
2. Met de rechtermuisknop op **regels voor automatische implementatie** en kies **regel voor automatische implementatie maken**. 
3. Volg de aanwijzingen voor het voltooien de **algemene**, **implementatie-instellingen**, en **Software-Updates** tabbladen. 
4. Op de **Evaluatieplanning** tabblad **e regel uitvoeren volgens een schema** en **aanpassen**.
5. Selecteer voor de aangepaste planning **maandelijkse** en in een base dag, zoals de tweede dinsdag plaatsen. 
6. Controleer **Offset (dagen)** en het aantal dagen voor de verschuiving vervolgens **OK** na voltooiing.  
7. Voltooi de rest van de **Wizard automatische implementatie maken regel**. 



## <a name="reassign-distribution-point"></a>Opnieuw toewijzen van distributiepunt
<!-- 1306937 -->
Veel klanten hebben grote Configuration Manager-infrastructuur en vermindert primaire of secundaire sites voor het vereenvoudigen van hun omgeving. Nog steeds behouden moeten blijven distributiepunten op filialen inhoud voor beheerde clients bedienen. Deze distributiepunten bevatten vaak meerdere terabytes of meer van de inhoud. Deze inhoud is kost het veel tijd en netwerkbandbreedte te distribueren naar deze externe servers. 

Deze functie kunt u een distributiepunt naar een andere primaire site opnieuw toewijzen zonder de inhoud opnieuw distribueren. Met deze actie werkt de sitetoewijzing van het systeem tijdens het persistent maken van alle inhoud op de server. Als u meerdere distributiepunten opnieuw toewijzen wilt, eerst deze actie niet uitvoeren op één distributiepunt en vervolgens doorgaan met de extra servers met één op een tijdstip.

> [!IMPORTANT]
> De sitesysteemserver kan alleen de distributiepuntrol hosten. U kunt het distributiepunt niet toewijzen als de sitesysteemserver als host fungeert voor een andere Configuration Manager serverrol, zoals het statusmigratiepunt. U kunt een clouddistributiepunt niet toewijzen. 

Deze optie werkt niet met deze release vanwege de Technical Preview-limiet van een enkele primaire site. Het scenario en verzend **Feedback** van de **Start** tabblad van het lint, met betrekking tot de mogelijkheden van deze actie.
1. Ga in de Configuration Manager-console naar de **beheer** werkruimte en selecteer de **distributiepunten** knooppunt.
2. Met de rechtermuisknop op het distributiepunt doel en selecteer **opnieuw toewijzen van distributiepunt**. 
  ![Opnieuw toewijzen van distributiepunt](media/1306937-reassign-dp.png)
3. Selecteer de siteserver en de sitecode die u wilt dit distributiepunt opnieuw toewijst. 
  ![Selecteer een siteserver](media/1306937-select-site.png)



## <a name="improvements-to-hardware-inventory"></a>Verbeteringen in de hardware-inventaris
<!-- 1357389 -->
Voor toegevoegde klassen kunnen string-lengte groter is dan 255 tekens voor hardware-inventarisatie-eigenschappen die geen sleutels worden opgegeven.

### <a name="try-it-out"></a>Probeer het nu!  
Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.<br/>

1. In de **beheer** werkruimte, klik op **clientinstellingen** markeren van een clientapparaat instellen om te bewerken, klik met de rechtermuisknop en selecteer vervolgens **eigenschappen**. 
2. Selecteer **Hardware-inventaris**, klikt u vervolgens **klassen instellen**, en **toevoegen**.
3. Klik op de **Connect** knop.
4. Vul **computernaam**, **WMI-naamruimte**, selecteer **recursieve** indien nodig. Geef referenties op om te verbinden. Klik op **Connect** om weer te geven van de naamruimteklassen.
5. Selecteer een nieuwe klasse en klik vervolgens op **bewerken**.
6. Wijzig de **lengte** van ten minste één eigenschap die is een tekenreeks, dan de sleutel moet groter zijn dan 255. Klik op **OK**. 
7. Controleer of de eigenschap bewerkte is geselecteerd voor **Hardware-Inventarisklassen** en klik op **OK**. 
8. Hardware-inventaris verzamelen met de nieuwe klasse met een eigenschap die groter zijn dan 255 tekens. 



## <a name="improvements-to-client-settings-for-software-center"></a>Verbeteringen in de clientinstellingen voor Software Center
<!-- 1351224 & 1355146 -->
In deze versie van de Technical Preview zijn verbeteringen aangebracht voor aanpassing van het Software Center onder de clientinstellingen. 

1. De clientinstellingen voor Software Center hebt nu een **aanpassen** knop.
2. Een voorbeeld is toegevoegd om weer te geven hoe de Software Center banner eruit ziet.<!--1351224-->
    - Als een logo dat niet is ingeschakeld, wordt het voorbeeld ziet de bedrijfsnaam toe als tekst en de kleur.
    - Als een logo dat is geselecteerd, wordt de Preview-versie het logo en bedrijf naam tekst.  
3.  **Niet-goedgekeurde toepassingen in Software Center verbergen** is een nieuwe instelling voor Software Center. Wanneer deze optie is ingeschakeld, worden de beschikbare toepassingen die moeten worden goedgekeurd verborgen in Software Center.<!--1355146-->

### <a name="try-it-out"></a>Probeer het nu!  
 Probeer de taken uitvoeren. Verzend **Feedback** van de **Start** tabblad van het lint laat ons weten hoe het is gegaan.

1. In de **beheer** werkruimte, klik op **clientinstellingen**. Selecteer een clientapparaatinstelling om te bewerken. Selecteer vervolgens met de rechtermuisknop op het **eigenschappen** vervolgens **Software Center**.
2.  Klik op de **aanpassen** knop. Probeer andere aanpassingen van de instellingen met inbegrip van de Preview-versie.
3. Schakel de instelling **verbergen van niet-goedgekeurde toepassingen in Software Center**. Bekijk de wijzigingen in Software Center. 



## <a name="new-settings-for-windows-defender-application-guard"></a>Nieuwe instellingen voor Windows Defender toepassing Guard
<!-- 1356256 -->
Voor Windows 10 versie 1709 en hogere apparaten er zijn twee nieuwe host interactie van de instellingen voor [Windows Defender toepassing Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy). 
1. Websites kunnen toegang krijgen tot virtuele graphics-processor van de host. 
2. Bestanden gedownload in de container kunnen persistent worden gemaakt op de host. </br>



## <a name="improvements-to-run-scripts"></a>Verbeteringen aan het uitvoeren van Scripts
<!-- 1236459 -->
De [ **Scripts uitvoeren** functie](/sccm/apps/deploy-use/create-deploy-scripts) nu kunt u om te importeren en ondertekende PowerShell-scripts uitvoeren. 
- Als u wilt behouden in de script-integriteit, moeten ondertekende scripts worden geïmporteerd, in plaats van kopiëren en plakken. 
- Geïmporteerde ondertekende scripts kunnen niet worden bewerkt na het importeren.
    
>[!IMPORTANT]
>Er zijn twee tijdelijke beperkingen in deze Technical Preview.
>- Scripts kunnen alleen worden geïmporteerd in de functie Scripts uitvoeren en rechtstreeks vanuit de console kunnen niet worden bewerkt.
>- Scripts met een niet-Unicode-codering geïmporteerd mogelijk niet goed weergegeven in de console. Het script wordt nog steeds uitgevoerd als oorspronkelijk is geschreven.





## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
