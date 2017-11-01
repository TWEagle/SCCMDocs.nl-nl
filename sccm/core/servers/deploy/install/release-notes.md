---
title: 'Release-opmerkingen '
titleSuffix: Configuration Manager
description: Raadpleeg deze opmerkingen voor urgente problemen die nog niet zijn opgelost in het product of in een Microsoft Knowledge Base-artikel besproken.
ms.custom: na
ms.date: 08/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: "41"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 2571cfbff1373db05279918af776d8be81a5c322
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="release-notes-for-system-center-configuration-manager"></a>Opmerkingen bij de release van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager opmerkingen bij de productrelease zijn beperkt tot urgente problemen die nog niet zijn opgelost in het product (beschikbaar via een update in de console) of uiteengezet in een Microsoft Knowledge Base-artikel.  

Informatie over bekende problemen die invloed hebben op de belangrijkste scenario's wordt overgebracht in de onlinemodus productdocumentatie in de Documentatiebibliotheek van System Center Configuration Manager.  

> [!TIP]  
>  Dit onderwerp bevat opmerkingen bij de release voor de huidige vertakking van System Center Configuration Manager. Zie voor de Technical Preview voor System Center Configuration Manager [Technical Preview voor System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

Zie de volgende onderwerpen voor informatie over de nieuwe functies geïntroduceerd met verschillende versies:
- [Wat is er nieuw in versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)  
- [Wat is er nieuw in versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)
- [Wat is er nieuw in versie 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)
   


## <a name="setup-and-upgrade"></a>Installatie en upgrade  

### <a name="after-you-update-a-configuration-manager-console-using-consolesetupexe-from-the-site-server-folder-recent-language-pack-changes-are-not-available"></a>Na het bijwerken van een Configuration Manager-console met behulp van ConsoleSetup.exe vanaf de site server-map zijn recente language pack wijzigingen niet beschikbaar
<!--  SMS 486420  Applicability should be 1610 and 1702.  -->
*De volgende van toepassing op versie 1610 en 1702.*   
Nadat u een update in-place uitgevoerd naar een console via ConsoleSetup.exe uit de installatiemap van een site-servers, onlangs geïnstalleerde taalpakketten mogelijk niet beschikbaar. Dit gebeurt wanneer:
- Uw site versie 1610 of 1702 wordt uitgevoerd.
- De console wordt bijgewerkt in-place via ConsoleSetup.exe uit de installatiemap van de site server.

Als dit probleem optreedt, gebruikt de opnieuw geïnstalleerde console niet de meest recente set van taalpakketten die zijn geconfigureerd. Geen fouten zijn geretourneerd, maar de taalpakketten die beschikbaar zijn voor de console wordt niet gewijzigd.  

**Tijdelijke oplossing:** Verwijder de huidige console en vervolgens opnieuw installeren als een nieuwe installatie van de console. U kunt ConsoleSetup.exe gebruiken uit de installatiemap van de site-servers. Zorg dat u selecteert de language pack-bestanden die u wilt gebruiken tijdens de installatie.


### <a name="with-version-1702-the-default-site-boundary-group-is-configured-for-use-for-site-assignment"></a>Met versie 1702, is de standaardgroep voor de grens van site geconfigureerd voor gebruik voor sitetoewijzing
<!--  SMS 486380   Applicability should only be to 1702. -->
*De volgende van toepassing op versie 1702.*  
Het tabblad standaard site grens groepen verwijzing is een controle voor de **deze grensgroep gebruiken voor sitetoewijzing**, geeft een lijst van de site als de **toegewezen site**, en lichter gekleurd weergegeven zodat de configuratie kan niet worden bewerkt of verwijderd.

**Tijdelijke oplossing:** Geen. U kunt deze instelling negeren. Hoewel de groep voor sitetoewijzing is ingeschakeld, wordt de standaard sitegrensgroep niet gebruikt voor sitetoewijzing. Met 1702, deze configuratie zorgt ervoor dat de standaard site-grensgroep is gekoppeld aan de juiste site.



### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Als u een Service-vertakking Long-Term site met versie 1606 installeert, is een Current Branch-site geïnstalleerd
<!-- Consider move to core content  -->
Wanneer u de media versie 1606 basislijn van de release van oktober 2016 gebruikt om een site Long-Term Servicing Branch (LTSB) te installeren, installeert Setup in plaats daarvan een Current Branch-site. Dit gebeurt omdat de optie voor het installeren van een service connection point met installeren van de site niet is ingeschakeld.

 - Hoewel een serviceverbindingspunt niet vereist is, moet het worden geselecteerd om te installeren tijdens de installatie van een site LTSB te installeren.

Nadat Setup is voltooid, kunt u het serviceverbindingspunt verwijderen.  U moet echter een serviceaansluitpunt in de modus offline of online om te verzenden van telemetriegegevens en om beveiligingsupdates te krijgen voor zowel Current Branch en LTSB sites hebben.

Als uw site hebt geïnstalleerd als een Current Branch-site, maar u de LTSB installeren wilt, kunt u de site verwijderen en opnieuw installeren. U kunt ook aanroepen [Microsoft Help en ondersteuning](http://go.microsoft.com/fwlink/?LinkId=243064) voor hulp.  

Om te controleren welke vertakking geïnstalleerd in de console op **beheer** > **siteconfiguratie** > **Sites**, en open **hiërarchie-instellingen**. De optie voor het converteren van de site naar een Current Branch-site is alleen beschikbaar wanneer de site de LTSB wordt uitgevoerd.  

**Tijdelijke oplossing:**  Geen.   


### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Een update is vastgelopen met een status Downloaden in het knooppunt Updates en onderhoud van de Configuration Manager-console  
<!-- Source bug pending. Consider move to core content.  8/15 Seeking validation of issue from Dev.  -->
Tijdens de automatische download van updates via een onlineserviceaansluitpunt kan een update zijn vastgelopen met een status Downloaden. Wanneer het downloaden van een update is vastgelopen, worden in de aangegeven logboekbestanden vermeldingen weergegeven die lijken op het volgende:  

Logboek van DMPdownloader:  

-   FOUT: Kan niet worden gedownload redist voor 037cd17e-4d7b-40e1-802b-14bb682364c7 met de opdracht /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 http://go.microsoft.com/fwlink/?LinkID=724434 Lnmanifesturl 112015/noui "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"  

ConfigMgrSetup.log:  

-   Fout: Verifiëren van Authenticode-ondertekening d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi is mislukt.  

-   Fout: file signature check failed for d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi (Controle van bestandshandtekening is mislukt voor d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi)  

**Tijdelijke oplossing**: Wijzig de volgende registersleutel voor het overeenkomt met het volgende en vervolgens de SMS_Executive-service opnieuw start, of wacht maximaal 24 uur totdat de volgende automatische download op de siteserver.  

-   **Sleutel voor bewerking**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software Publishing  

-   **Waarde voor status**:  Ingesteld op **146944** decimale of **0x00023e00** hexadecimale  


###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>Wanneer u redist bestanden vanaf de CD mislukt de installatie. Meest recente map met een manifest verificatiefout
<!-- Source bug pending    8/15 Seeking validation of issue from Dev.   -->

Wanneer u Setup uitvoert vanaf een CD. Meest recente map gemaakt voor versie 1606 en opgenomen in die CD redist bestanden gebruiken. Meest recente map, mislukt de installatie met de volgende fouten in het logboek van Setup van Configuration Manager:

  - FOUT: Er is een bestand hash-controle mislukt voor defaultcategories.dll
  - FOUT: Manifest verificatie is mislukt. Verkeerde versie van het manifest?

**Tijdelijke oplossing:**  Gebruik een van de volgende opties:
 - Kies tijdens de installatie van de meest recente redist om bestanden te downloaden van Microsoft te gebruiken in plaats van deze die zijn opgenomen in de CD. Meest recente map.
 - Verwijder handmatig de *cd.latest\redist\languagepack\zhh* map en voer vervolgens Setup opnieuw uit.


### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>Hulpprogramma voor serviceverbindingen er een uitzondering gegenereerd als SQL server staat, of wanneer het gedeelde geheugen is uitgeschakeld
<!-- 479223   Fixed in 1702 and later   -->
*De volgende van toepassing op versie 1610 en eerdere versies.*  
Het hulpprogramma voor serviceverbindingen wordt een uitzondering gegenereerd wanneer een van de volgende ingesteld op true is:  
 -  De sitedatabase zich op afstand van de computer die als host fungeert voor het service connection point en gebruikt een niet-standaardpoort (een andere poort dan 1433)
 -  De sitedatabase zich op dezelfde server als het serviceverbindingspunt wordt gehost, maar SQL-protocol **Shared Memory** is uitgeschakeld

De uitzondering is vergelijkbaar met het volgende:
 - *Niet-verwerkte uitzondering: System.Data.SqlClient.SqlException: Er is een netwerkgerelateerde of exemplaarspecifieke fout opgetreden tijdens het maken van een verbinding met SQL Server. De server is niet gevonden of is niet toegankelijk. Controleer of dat de exemplaarnaam juist is en dat SQL Server is geconfigureerd voor externe verbindingen. (provider: Named Pipes-Provider, fout: 40 - kan geen verbinding openen met SQL Server)--*

**Tijdelijke oplossing**: Tijdens het gebruik van het hulpprogramma moet u het register van de server die als host fungeert voor het service connection point met informatie over de SQL Server-poort wijzigen:

   1.   De volgende registersleutel bewerken voordat u het hulpprogramma gebruikt, en het nummer van de poort die wordt gebruikt op de naam van de SQL-Server toevoegen:
    - Sleutel:   HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - Waarde: &lt;SQL-servernaam >
    - Toevoegen: **,&lt;poort >**

    Bijvoorbeeld poort *15001* naar een server met de naam *testserver.test.net*, zou de resulterende sleutel: ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.NET,15001***

   2.   Na het toevoegen van de poort in het register, moet het hulpprogramma normaal functioneren.  

   3.   Nadat uw gebruik van het hulpprogramma voltooid voor zowel is de **-verbinding** en **-importeren** stappen, wijzigt u de registersleutel terug naar de oorspronkelijke waarde.  


<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>Clientimplementatie en -upgrade  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Installatie van de client mislukt met foutcode 0x8007064c
<!--- SMS 486973  applies 1606 to 1706. Not yet fixed. -->
*Het volgende geldt voor alle actieve versies van Configuration Manager.*   
Met alle actieve versies van wanneer u de client op Windows-computers te implementeren, mislukt de installatie. Het bestand ccmsetup.log bevat een item ' File 'C:\WINDOWS\ccmsetup\Silverlight.exe' afsluitcode 1612 geretourneerd. Mislukt de installatie' gevolgd door 'InstallFromManifest is mislukt 0x8007064c'.

**Tijdelijke oplossing** dit wordt veroorzaakt door een beschadigd, eerder geïnstalleerde versie van Silverlight. U kunt het volgende programma wordt uitgevoerd op de desbetreffende computer om dit te corrigeren: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed)

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>Onderhoudsplannen maken standaard veel dubbele software-updategroepen en -implementaties  
De wizard Onderhoudsplan maken wordt momenteel standaard uitgevoerd na elke synchronisatie van software-updates. Telkens wanneer de wizard wordt uitgevoerd, wordt er een nieuwe software-updategroep en -implementatie gemaakt. Als u een synchronisatieplanning voor software-updates hebt die bijvoorbeeld meerdere keren per dag wordt uitgevoerd, maakt de wizard Onderhoudsplan maken elke dag meerdere, waarschijnlijk identieke software-updategroepen en -implementaties.  

**Tijdelijke oplossing**:    
Nadat u een onderhoudsplan hebt gemaakt, opent u de eigenschappen voor het onderhoudsplan, gaat u naar de **Evaluatieplanning** tabblad **e regel uitvoeren volgens een schema**, klikt u op **aanpassen**, en maak een aangepaste planning. U kunt bijvoorbeeld instellen dat het onderhoudsplan elke 60 dagen wordt uitgevoerd.  


### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>Wanneer een implementatie met hoog risico dialoogvenster zichtbaar voor een gebruiker is, worden daaropvolgende met een hoog risico dialoogvensters met een deadline vroeger niet weergegeven
<!-- Fixed in 1702 and later -->
*De volgende van toepassing op versie 1610 en eerdere versies.*   
Nadat u maken en implementeren van een implementatie met een hoog risico taak voor gebruikers, wordt een dialoogvenster met een hoog risico voor de gebruiker weergegeven. Als de gebruiker komt niet in het dialoogvenster sluiten en u maakt en implementeert een andere implementatie met hoog risico met een deadline vroeger dan de eerste, ontvangt de gebruiker niet een bijgewerkte dialoogvenster totdat ze de oorspronkelijke dialoogvenster hebt gesloten. De implementaties zullen nog steeds uitgevoerd op de geconfigureerde deadlines.

**Tijdelijke oplossing**:  
De gebruiker moet in het dialoogvenster voor de eerste implementatie met hoog risico om te zien in het dialoogvenster voor de volgende implementatie met hoog risico sluiten.



## <a name="software-updates"></a>Software-updates

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Een Office 365 client-instellingen importeren vanuit een configuratiebestand mislukt wanneer het niet-ondersteunde talen bevat
<!-- 489258  Fixed in 1706  -->
*De volgende van toepassing op versie 1702 en eerdere versies.*   
Wanneer u de instellingen van de Office 365 client uit een bestaande XML-configuratiebestand importeren, en het bestand bevat de talen die niet worden ondersteund door de Office 365 ProPlus-client, wordt er een fout optreden. Zie voor meer informatie [Office 365-apps implementeren op clients vanuit het Office 365 Client Management dashboard](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Tijdelijke oplossing**:    
Gebruik alleen de [talen die worden ondersteund door de Office 365 ProPlus-client](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) in het XML-configuratiebestand.  



## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Met Volledig wissen worden Windows 10-apparaten met minder dan 4 GB RAM uitgeschakeld
Nadat de functie Volledig wissen is uitgevoerd op een Windows 10 RTM-apparaat (versies vóór versie 1511) met minder dan 4 GB RAM, is het apparaat mogelijk niet meer bruikbaar. Na een poging om het apparaat te wissen, kan het niet meer worden opgestart of reageert het niet meer.

**Tijdelijke oplossing**: Zorg ervoor dat Windows 10 RTM-pc's hebben ten minste 4 GB RAM-geheugen beschikbaar voor het uitvoeren van een volledig wissen op het apparaat. Voer 'winver' achter de opdrachtprompt in als u het versienummer van Windows 10-apparaten wilt bekijken. Als het apparaat al is gewist en niet meer reageert, gebruikt u een opstartbaar Windows 10 USB-station om te starten en toegang tot het apparaat te herstellen.


### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Wanneer een gebruiker tot twee of meer gebruikersverzamelingen behoort waarvoor een voorwaardenbeleid is geïmplementeerd, krijgt deze meerdere reeksen met dezelfde voorwaarden te zien  
<!-- 454394    -->
Wanneer een beheerder een reeks voorwaarden implementeert voor meerdere gebruikersverzamelingen, en een gebruiker is lid van meer dan één van deze verzamelingen, krijgt die gebruiker meerdere exemplaren van dezelfde voorwaarden te zien wanneer deze de bedrijfsportal opent.  Bijvoorbeeld, als een gebruiker met de naam 'Voorbeeldgebruiker' een lid is van twee verschillende gebruikersverzamelingen is, één met de naam 'Bedrijfwerknemersft' als 'Bedrijfwerknemerspt', ' en de voorwaarden en bepalingen genaamd 'CompanyTerms' wordt geïmplementeerd op zowel Bedrijfwerknemersft als Bedrijfwerknemerspt, krijgt voorbeeldgebruiker twee identieke reeksen companyterms op de pagina van de acceptatie van voorwaarden. Omdat gebruikers alleen alle voorwaarden kunnen accepteren of weigeren, is er geen gevaar voor een dubbelzinnige acceptatiestatus waarbij de gebruiker de voorwaarden zowel heeft geaccepteerd als geweigerd. Het rapport Acceptatie van voorwaarden bevat slechts één rij voor elke set voorwaarden voor elke gebruiker. Het rapport bevat dus geen fouten. Het enige effect is dat de gebruiker op de pagina voor het accepteren van de voorwaarden twee reeksen voorwaarden te zien krijgt.  

**Tijdelijke oplossing**: Zorg ervoor dat elke gebruiker is opgenomen in slechts één verzameling waarnaar u de voorwaarden zijn geïmplementeerd.  


### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android voor werk-e-mailprofielen die gebruikmaken van verificatie via certificaat worden niet toegepast op apparaten
<!--  487657      -->
Wanneer u een Android voor werk-e-mailprofiel maakt, zijn er twee opties voor verificatie. Een gebruikersnaam en het wachtwoord is, en de andere certificaten. Op dit moment is werkt de optie certificaten niet. Als het profiel is gemaakt met de verificatiemethode die is ingesteld op **certificaten**, het profiel wordt niet toegepast op het apparaat en de gebruiker wordt gevraagd de accountdetails e handmatig invoeren.

**TIJDELIJKE OPLOSSING**: Geen. Beheerders moet gebruiken de **gebruikersnaam en wachtwoord** optie of wacht totdat dit probleem is opgelost.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->


## <a name="endpoint-protection"></a>Endpoint Protection

### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Antimalware-beleid mislukt toepassen op Windows Server 2016 Core
<!--  Product Studio bug 485370 added 04 19 2017   Fixed in 1702 -->
*De volgende van toepassing op versie 1610 en eerdere versies.*  
Antimalwarebeleid mislukt op Windows Server 2016 Core toe te passen.  De foutcode is 0x80070002.  Er is een ontbrekende afhankelijkheid voor ConfigSecurityPolicy.exe.

**Tijdelijke oplossing:**  Dit probleem is opgelost door [Knowledge Base-artikel 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) 9 mei 2017 gedistribueerd.


### <a name="windows-defender-advanced-threat-protection-policies-fail-on-older-client-agents"></a>Windows Defender Advanced Threat Protection-beleid niet op oudere clientagents
<!-- Product Studio bug 462286 added  05 25 2017 and valid until July 2017 GA release      Fixed in 1610 -->
Windows Defender Advanced Threat Protection-beleid wordt gemaakt van een Configuration Manager versie 1610 of hoger siteserver mislukken wilt toepassen op Configuration Manager versie 1606 en oudere clients.  De clients zijn niet geïntegreerde en de evaluatie van het beleid een fout gemeld. De **Implementatiestatus** ziet u in de configuratie van Windows Defender Advanced Threat Protection **fout**.

**TIJDELIJKE OPLOSSING**: Configuration Manager-client bijwerken naar versie 1610 of hoger.
