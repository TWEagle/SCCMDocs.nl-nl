---
title: Technische Preview 1712 | Microsoft Docs
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1712 voor System Center Configuration Manager.
ms.custom: na
ms.date: 12/15/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ce372d6-bd93-4d4d-b612-5303f89c36f0
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 85f0b22b3dc067f6f07816ad36d23a090885f355
ms.sourcegitcommit: ed8b2438ef85c9160741ef61f9171be41dd1ae0a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/17/2017
---
# <a name="capabilities-in-technical-preview-1712-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1712 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1712 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. 

Bekijk [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview) voordat u deze versie van de technical preview installeert. Dit artikel familiarizes u met de algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.     


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
<!--sms489412-->


**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Section Template
##  FEATURE
<-- TFS ID - need to fix comment md here
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="do-not-automatically-upgrade-superseded-applications"></a>Vervangen van toepassingen niet automatisch bijgewerkt
<!-- 1351266 -->
Op basis van uw [feedback van gebruikers stem](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/11532669-fix-supercedence-behavior), in deze release die u hebt de optie voor het configureren van de implementatie van een toepassing om bij te werken niet automatisch elke vervangen versie. Nu bij het maken van de implementatie op de **implementatie-instellingen** pagina van de **Wizard Software implementeren**, voor **beschikbaar** of **vereist**doel, installeert u kunt inschakelen of uitschakelen van de optie voor het **automatisch upgraden een vervangen versies van deze toepassing**.


## <a name="install-multiple-applications-in-software-center"></a>Meerdere toepassingen in Software Center installeren
<!-- 1357126 -->
Als een eindgebruiker of bureaublad technicus moet meerdere toepassingen installeren op een apparaat, Software Center biedt nu ondersteuning voor het installeren van meerdere geselecteerde toepassingen. Dit kan de gebruiker tijdens het wachten geen één installatie is voltooid voordat u begint de volgende efficiënter zijn.

Bij gebruik van meervoudige selectie modus in de **toepassingen** tabblad en de volgende criteria bepalen welke Software Center wordt ingeschakeld voor meervoudige selectie apps:
 - De app is zichtbaar voor de gebruiker
 - De app is niet al geïnstalleerd
 - Goedkeuring door beheerder is niet vereist, of is al verleend
 - De status van de app is beschikbaar (bijvoorbeeld als u nog niet downloaden van inhoud)

### <a name="try-it-out"></a>Probeer het nu!
**In de Configuration Manager-console:** Meerdere toepassingen voor de installatie als beschikbaar of vereist (met de deadline in de toekomst) voor een gebruiker of apparaat implementeren. Goedkeuring door beheerder geen nodig. Zie voor meer informatie [toepassingen implementeren](/sccm/apps/deploy-use/deploy-applications).

**In Software Center:**
 1. De **toepassingen** tabblad Standaard wordt geopend. 
 2. Om de modus voor meervoudige selectie in de lijstweergave opgeven, klikt u op het pictogram Nieuw ![Pictogram voor meervoudige selectie van software Center](media/software-center-multi-select-apps.png) in de rechterbovenhoek.
 3. Twee of meer apps te installeren door te klikken op het selectievakje links van de apps in de lijst selecteren.
 4. Klik op de **installeren geselecteerd** knop.

De apps installeren die normaal werken nu alleen achter.


## <a name="client-based-pxe-responder-service"></a>PXE-responder-service op basis van client
<!-- 1357148 -->
Een algemene uitdaging voor klanten is het PXE-services op afstand/filialen met weinig of geen serverinfrastructuur bieden. De verdeling wijst de rol ondersteunt client-besturingssystemen, maar kan niet worden ingeschakeld voor PXE vanwege de afhankelijkheid van Windows Deployment Services.

Nieuwe clientinstellingen zijn nu beschikbaar voor het inschakelen van een PXE-responder-service op de Configuration Manager-clients. Een opstartinstallatiekopie met PXE-functionaliteit moet zich bevinden in de PXE-responder-clientcache.

### <a name="try-it-out"></a>Probeer het nu!
Zorg ervoor dat er geen bestaande PXE-ingeschakelde distributiepunten of andere PXE-servers in de testomgeving die met deze client PXE responder conflicteren mogelijk.

In de Configuration Manager-console:
 1. In de **softwarebibliotheek** werkruimte **besturingssystemen**, **Takenreeksen**: Maak een takenreeks met behulp van de aangepaste sjabloon.
    1. Klik op **toevoegen**, selecteer **algemene**, en vervolgens de **Takenreeksvariabele instellen** stap. Voer **SMSTSPersistContent** als de takenreeksvariabele en voer de waarde **TRUE**.
    1. Klik op **toevoegen**, selecteer **Software**, en vervolgens de **pakketinhoud downloaden** stap. Klik op het sterretje gold en selecteer vervolgens een opstartinstallatiekopie met PXE-functionaliteit. X86- en x64 installatiekopieën bevatten. Configureren van de stap voor het plaatsen in de **Configuration Manager-clientcache**.
    1. Klik op **toevoegen**, selecteer **algemene**, en vervolgens de **Takenreeksvariabele instellen** stap. Voer **SMSTSPreserveContent** als de takenreeksvariabele en voer de waarde **TRUE**.
 2. In de **beheer** werkruimte **clientinstellingen**: Maak een aangepast clientinstellingenbeleid apparaat.
    1. Selecteer de **clientcache-instellingen** groep.
  1. Stel de **inschakelen Configuration Manager-client in volledige OS in staat om inhoud te delen** instelt op **Ja**.
    1. Stel de **PXE inschakelen responder service** instelt op **Ja**.
  1. Voor de **maken van een zelfondertekend certificaat of importeer een PKI-clientcertificaat** instellen, klikt u op **certificaat**. Selecteer **certificaat importeren** als uw testomgeving PKI heeft, of klik anders op **OK** een zelfondertekend certificaat maken. 
    1. De overige instellingen configureren die nodig zijn voor uw testomgeving. (De standaardinstellingen te werken tenzij er specifieke netwerk- of beveiligingsvereisten zijn.)
 3. Implementeer de takenreeks en aangepaste clientinstellingen aan een verzameling van doelclients PXE-responders. Wachten op het beleid toe te passen en de takenreeks wordt uitgevoerd.
 4. Start een andere client in hetzelfde subnet als normaal opstarten vanaf het PXE/netwerk.

### <a name="known-issues"></a>Bekende problemen
 - De editor voor takenreeksen geeft een rode foutpictogram voor de **pakketinhoud downloaden** stap als u een opstartinstallatiekopie toevoegt, maar de takenreeks opgeslagen. Deze takenreeks opnieuw te openen in de editor toont ook een onschadelijke waarschuwing dat verwijst naar objecten kan niet worden gevonden. <!-- sms427542 -->
 - De installatiekopie van de pakketinhoud downloaden stap wordt niet weergegeven in de aangepaste takenreeks lijst met verwijzingen. Ook de **inhoud distribueren** actie is niet beschikbaar. <!-- sms504017 -->


## <a name="change-in-the-configuration-manager-client-install"></a>Wijziging in de Configuration Manager-client installeren  
Als gevolg van uw stem feedback van gebruikers, [Silverlight wordt niet meer op clients automatisch geïnstalleerd.](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/10886427-please-do-not-install-silverlight-by-default-in-v) <!--1356195-->
  

## <a name="change-to-the-surface-device-dashboard"></a>Wijzig in het dashboard Surface apparaat
Het oppervlak dashboard wordt nu weergegeven firmware-versies voor apparaten die Surface in plaats van de versie van besturingssysteem. Ga in de console naar **bewaking** > **oppervlak apparaten**. U kunt de volgende items weergeven:
- percentage van het oppervlak
- percentage van het oppervlak modellen
- Top 5 firmware-versies
 <!--1355788-->


## <a name="improvements-to-office-365-client-management-dashboard"></a>Verbeteringen aan beheer van Office 365 Client-dashboard 
Het dashboard voor beheer van Office 365-Client wordt nu een lijst met relevante apparaten weergegeven wanneer grafiek secties worden geselecteerd. Ga in de console naar **softwarebibliotheek** >**overzicht** >**Office 365-clientbeheer**. Het dashboard wordt weergegeven aan de rechterkant. Criteria selecteren in de grafiek toont een lijst met apparaten.  
<!--1357281-->


## <a name="improvements-to-the-configuration-manager-console"></a>Verbeteringen in de Configuration Manager-console 
We hebben de volgende verbeteringen aangebracht in de Configuration Manager-console die een resultaat van uw feedback van gebruikers stem waren aangebracht.

- [Lijst met apparaten geeft de primaire gebruiker](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8782225-enable-a-column-for-primary-user): De primaire gebruiker weergegeven apparatenlijsten onder activa en naleving, apparaten, nu standaard. De laatste aangemelde gebruiker kan ook worden toegevoegd als een optionele kolom. <!-- 1357280 -->
- [Hernoemde verzamelingen weergegeven in de bestaande verzameling lidmaatschapsregels](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/20125567-fix-the-renaming-of-collections): Als een verzameling lid van een andere verzameling is en de naam wordt gewijzigd, wordt de nieuwe naam onder lidmaatschapsregels bijgewerkt.<!--1357282--> 


## <a name="improvements-to-operating-system-deployment"></a>Verbeteringen in de implementatie van besturingssysteem
We de volgende verbeteringen voor de implementatie van besturingssystemen, werd het resultaat van uw feedback van gebruikers stem aangebracht.
 - [Standaard-Logboeken in opstartinstallatiekopie](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/19269823-stop-cmtrace-from-asking-us-if-we-want-to-use-it-a): In Windows PE, tijdens het starten van cmtrace.exe, u niet langer gevraagd te kiezen of maken van dit programma van de standaard-viewer voor logboekbestanden. <!-- SMS 500897 -->
 - Downloaden van pakketinhoud stap: U kunt nu opstartinstallatiekopieën toevoegen aan deze takenreeksstap.


## <a name="windows-10-feedback-hub-app-integration"></a>App-integratie voor Windows 10 Feedback Hub

We graag feedback dus veel dat we nu feedback via inschakelen bent de [Feedback Hub app](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) ingebouwd in Windows 10. Wanneer u **toevoegen van nieuwe feedback**, selecteer de **Enterprise Management** categorie, en kies vervolgens een van de volgende subcategorieën:
 - Configuration Manager-Client
 - Configuration Manager-Console
 - Implementatie van het besturingssysteem van de Configuration Manager
 - Configuration Manager-Server

Blijven gebruiken onze [stem gebruikerspagina](http://configurationmanager.uservoice.com/) wilt stemmen over ideeën voor nieuwe functies in Configuration Manager.


<!-- When we have another H2 in this topic, Add this Next Steps section back in.  -->

## <a name="next-steps"></a>Volgende stappen
Zie voor meer informatie over het installeren of bijwerken van de technical preview vertakking [Technical Preview voor System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
