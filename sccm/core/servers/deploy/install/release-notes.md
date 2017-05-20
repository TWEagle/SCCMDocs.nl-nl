---
title: Release-opmerkingen - Configuration Manager | Microsoft-documenten
description: Raadpleeg deze opmerkingen voor urgente problemen die nog niet zijn opgelost in het product of in een Microsoft Knowledge Base-artikel besproken.
ms.custom: na
ms.date: 05/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 41
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: 9da6f9678a7fb5c76f365a3522f5e5e0fdfec037
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="release-notes-for-system-center-configuration-manager"></a>Opmerkingen bij de release van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager product release-opmerkingen mogen maximaal urgente problemen die nog niet zijn opgelost in het product (beschikbaar via een update in de console) of uiteengezet in de Microsoft Knowledge Base-artikel.  

 In het geval van bekende problemen die van invloed zijn op belangrijke scenario's, worden deze gegevens vermeld in de onlineproductdocumentatie in de documentatiebibliotheek van System Center Configuration Manager.  

> [!TIP]  
>  Dit onderwerp bevat de releaseopmerkingen voor de huidige vertakking van System Center Configuration Manager. Zie voor technische Preview van System Center Configuration Manager [Technical Preview voor System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

## <a name="setup-and-upgrade"></a>Installatie en upgrade  

### <a name="after-you-update-a-configuration-manager-console-using-consolesetupexe-from-the-site-server-folder-recent-language-pack-changes-are-not-available"></a>Na het bijwerken van een Configuration Manager-console met behulp van ConsoleSetup.exe vanaf de site server-map zijn recente taalpakketwijzigingen niet beschikbaar
<!--  SMS 486420  Applicability should be 1610 and 1702.  -->
Nadat u een InPlace-update uitgevoerd naar een console met behulp van ConsoleSetup.exe uit de installatiemap van een site-servers, kunnen er niet in onlangs geïnstalleerde taal packs zijn. Dit gebeurt wanneer:
- Uw site uitvoert versie 1610 of 1702.
- De console wordt bijgewerkt ter plekke via ConsoleSetup.exe uit de installatiemap van de site-server.

Als dit probleem optreedt, gebruikt de opnieuw geïnstalleerde console niet de meest recente set taalpakketten die zijn geconfigureerd. Er zijn geen fouten worden geretourneerd, maar language packs avaialble naar de console wordt niet gewijzigd.  

**Tijdelijke oplossing:** Verwijderen van de huidige console en de console als een nieuwe installatie vervolgens opnieuw te installeren. U kunt ConsoleSetup.exe uit de installatiemap van de site-servers. Zorg dat u selecteert u het taalpakket dat u wilt gebruiken tijdens de installatie.


### <a name="with-version-1702-the-default-site-boundary-group-is-configured-for-use-for-site-assignment"></a>Met versie 1702 is de standaardgroep voor de grens van site geconfigureerd voor het gebruik van site-toewijzing
<!--  SMS 486380   Applicability should only be to 1702. -->
Met versie 1702 standaard site grens groepen verwijzing naar dit tabblad bevat een selectievakje voor **deze grensgroep gebruiken voor sitetoewijzing**, geeft een lijst van de site als de **toegewezen site**, en is niet beschikbaar, zodat de configuratie kan niet worden bewerkt of verwijderd.

**Tijdelijke oplossing:** Geen. U kunt deze instelling negeren. Hoewel de groep voor sitetoewijzing is ingeschakeld, wordt de standaard-sitegrensgroep niet gebruikt voor sitetoewijzing. Met 1702 zorgt deze configuratie dat de standaardgroep voor de grens van site is gekoppeld aan de juiste site.



### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Als u een versie 1606 langetermijndoelen Service vertakking-site installeert, is een vertakking van huidige site geïnstalleerd
<!-- Consider move to core content  -->
Wanneer u de media versie 1606 basislijn sinds de release van oktober 2016 gebruikt om een site langetermijndoelen onderhoud vertakking (LTSB) te installeren, installeert Setup in plaats daarvan een vertakking van huidige site. Dit gebeurt omdat de optie voor het installeren van een service connection point met de installatie van de site niet is ingeschakeld.

 - Hoewel een serviceverbindingspunt niet vereist is, moet het worden geselecteerd om te installeren tijdens de installatie van een site LTSB wilt installeren.

U kunt de service connection point verwijderen nadat Setup is voltooid.  U moet echter een serviceverbinding punt in de offline- of -modus in te dienen telemetriegegevens en beveiligingsupdates ophalen voor de huidige vertakking en LTSB sites hebben.

Als uw site hebt geïnstalleerd als een vertakking van huidige site, maar u de LTSB installeren wilt, kunt u de site verwijderen en opnieuw installeren. U kunt ook contact opnemen [Microsoft Help en ondersteuning](http://go.microsoft.com/fwlink/?LinkId=243064) voor hulp.  

Om te bevestigen welke vertakking geïnstalleerd in de console op **beheer** > **siteconfiguratie** > **Sites**, en open **hiërarchie-instellingen**. De optie voor het converteren van de site aan een site huidige vertakking is alleen beschikbaar wanneer de site de LTSB wordt uitgevoerd.  

**Tijdelijke oplossing:**  Geen.   



### <a name="the--sql-server-backup-model-in-use-by-configuration-manager-can-change-from-full-to-simple"></a>Het SQL Server-back-upmodel dat wordt gebruikt door Configuration Manager kan worden gewijzigd van volledig in eenvoudig  
<!-- Confirm applicability for upgrade to later baselines. 1511 is out of support. 1606 is minmum supported baseline  -->

 Wanneer u bijwerkt naar System Center Configuration Manager versie 1511, kan het SQL Server-back-upmodel dat door Configuration Manager wordt gebruikt, worden gewijzigd van volledig in eenvoudig.  

-   Als u een aangepaste SQL Server-back-uptaak voor het volledige back-upmodel gebruikt (in plaats van de ingebouwde back-uptaak voor Configuration Manager), is het mogelijk dat het volledige back-upmodel met de upgrade wordt gewijzigd in een eenvoudig back-upmodel.  

**Tijdelijke oplossing**: Na de upgrade naar versie 1511 Controleer uw SQL Server-configuratie en zet u het volledige indien nodig.  



### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Een update is vastgelopen met een status Downloaden in het knooppunt Updates en onderhoud van de Configuration Manager-console  
<!-- Source bug pending. Consider move to core content.  -->
Tijdens de automatische download van updates via een onlineserviceaansluitpunt kan een update zijn vastgelopen met een status Downloaden. Wanneer het downloaden van een update is vastgelopen, worden in de aangegeven logboekbestanden vermeldingen weergegeven die lijken op het volgende:  

Logboek van DMPdownloader:  

-   FOUT: Kan niet worden gedownload redist voor 037cd17e-4d7b-40e1-802b-14bb682364c7 met de opdracht /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 /LnManifestUrl http://go.microsoft.com/fwlink/?LinkID=724434 RedistVersion 112015/noui gebruikt "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"  

ConfigMgrSetup.log:  

-   Fout: Verifiëren van Authenticode-ondertekening d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi is mislukt.  

-   Fout: file signature check failed for d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi (Controle van bestandshandtekening is mislukt voor d:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi)  

**Tijdelijke oplossing**: Wijzig de volgende registersleutel overeen met het volgende en vervolgens de SMS Executive-service opnieuw starten of wachten tot 24 uur voor de volgende cyclus automatisch downloaden op de siteserver.  

-   **Sleutel bewerken**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software publiceren  

-   **Waarde voor de status**:  Ingesteld op **146944** decimale of **0x00023e00** hexadecimale  


###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>Wanneer u bestanden redist vanaf de CD mislukt de installatie. Meest recente map met een manifest verificatiefout
<!-- Source bug pending  -->

Wanneer u Setup uitvoert vanaf een CD. Meest recente map gemaakt voor versie 1606 en de bestanden redist bij die CD gebruiken. Meest recente map Setup is mislukt met de volgende fouten in het installatielogboek van Configuration Manager:

  - FOUT: Bestand hash-controle is mislukt voor defaultcategories.dll
  - FOUT: Manifest verificatie is mislukt. Verkeerde versie van het manifest?

**Tijdelijke oplossing:**  Gebruik een van de volgende:
 - Kies tijdens de installatie van de meest recente redist om bestanden te downloaden van Microsoft gebruiken in plaats van deze die zijn opgenomen in de CD. Meest recente map.
 - Verwijder handmatig de *cd.latest\redist\languagepack\zhh* map en voer Setup opnieuw.

### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>Hulpprogramma voor service verbinding er een uitzondering gegenereerd wanneer SQL server extern is, of wanneer Shared Memory is uitgeschakeld
Vanaf versie 1606, het hulpprogramma service verbinding een uitzondering gegenereerd wanneer een van de volgende omstandigheden:  
 -    Uw sitedatabase is extern van de computer die als host fungeert voor de service connection point en gebruikt een niet-standaardpoort (een andere poort dan 1433)
 -     De sitedatabase zich op dezelfde server als het serviceverbindingspunt maar het SQL-protocol **Shared Memory** is uitgeschakeld

De uitzondering is vergelijkbaar met het volgende:
 - *Niet-verwerkte uitzondering: System.Data.SqlClient.SqlException: Een netwerk gerelateerde of met exemplaar-specifieke fout opgetreden tijdens het maken van een verbinding met SQL Server. De server is niet gevonden of is niet toegankelijk. Controleer of de exemplaarnaam juist is en dat SQL Server is geconfigureerd voor het toestaan van externe verbindingen. (provider: Named Pipes-Provider, fout: 40 - kan niet worden geopend een verbinding met SQL Server)--*

**Tijdelijke oplossing**: Tijdens het gebruik van het hulpprogramma, moet u het register van de server die als host fungeert voor de service connection point met informatie over de SQL-serverpoort wijzigen:

   1.    Voordat u het hulpprogramma gebruikt, bewerkt u de volgende registersleutel en het nummer van de poort die wordt gebruikt met de naam van de SQL-Server toevoegen:
    - Sleutel:   HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - Waarde: &lt;Naam van SQL Server >
    - Toevoegen: **,&lt;poort >**

    Bijvoorbeeld poort *15001* naar een server met de naam *testserver.test.net*, moet de resulterende sleutel: ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.NET,15001***

   2.    Na het toevoegen van de poort in het register, moet het hulpprogramma normaal functioneren.  

   3.    Nadat uw gebruik van het hulpprogramma voltooid voor zowel is de **-verbinding** en **-importeren** stappen, wijzigt u de registersleutel terug naar de oorspronkelijke waarde.  




<!-- No current Backup and Recovery relenotes
## Backup and recovery
-->



## <a name="client-deployment-and-upgrade"></a>Clientimplementatie en -upgrade  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Installatie van de client mislukt met foutcode 0x8007064c
<!--- SMS 486973 -->

Wanneer u de client op Windows-computers implementeert, mislukt de installatie. Het ccmsetup.log-bestand bevat een item "bestand 'C:\WINDOWS\ccmsetup\Silverlight.exe' afsluitcode 1612 geretourneerd. Mislukt de installatie"gevolgd door"0x8007064c InstallFromManifest mislukt".

**Tijdelijke oplossing** dit wordt veroorzaakt door een beschadigde, eerder geïnstalleerde versie van Silverlight. U kunt proberen het volgende programma wordt uitgevoerd op de geïnfecteerde computer te verhelpen: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed) 




## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

### <a name="issue-with-the-windows-adk-for-windows-10-version-1511"></a>Probleem met Windows ADK voor Windows 10 versie 1511  
Wanneer u een takenreeks vanuit Software Center die gebruikmaakt van een opstartinstallatiekopie van Windows PE v.10.0.10586 van de Windows ADK-10 versie 1511 uitvoert, wanneer de computer wordt opnieuw in Windows PE opgestart, mislukken deze Apps wanneer "Tijdens de initialisatie van hardwareapparaten" met de fout: **Windows PE-initialisatie is mislukt met foutcode 0x80220014**  

**Tijdelijke oplossing**: Gebruik de oorspronkelijke Windows 10 ADK. Zie voor meer informatie de volgende System Center Configuration Manager-teamblog: [Probleem met de Windows ADK voor Windows 10](http://blogs.technet.com/b/configmgrteam/archive/2015/11/20/issue-with-the-windows-adk-for-windows-10-version-1511.aspx)  

### <a name="dynamic-application-installation-fails-during-task-sequence-which-successfully-completes"></a>Installatie van dynamische toepassing mislukt tijdens de takenreeks die wordt voltooid  
Wanneer u een takenreeks implementeert die gebruikmaakt van de optie **Toepassingen installeren volgens de dynamische variabelenlijst** en een van de toepassingen wordt om een bepaalde reden niet geïnstalleerd, wordt door de takenreeks gerapporteerd dat de actie is geslaagd. Dit gebeurt ongeacht de manier waarop u de volgende opties configureert:  

-   **Doorgaan bij fout** (op het tabblad Opties van de stap Toepassing installeren)  

-   **Als de installatie van een toepassing mislukt, doorgaan met de installatie van andere toepassingen in de lijst** (op het tabblad Eigenschappen van de stap Toepassing installeren)  

U kunt het bestand smsts.log bekijken om te bepalen of de installatie van een toepassing is mislukt.  

**Tijdelijke oplossing**: Gebruik de **_TSAppInstallStatus** variabele voorwaarde op een latere stappen in een takenreeks met een voorwaarde voor het mislukken van de takenreeks als er een fout opgetreden bij een van de dynamische toepassingen is.  

### <a name="smb-might-not-work-properly-after-you-use-a-task-sequence-to-install-windows-10"></a>SMB werkt mogelijk niet goed nadat u een takenreeks hebt gebruikt voor het installeren van Windows 10  
Wanneer u een takenreeks gebruikt om een installatiekopie van Windows 10 te installeren, werkt SMB mogelijk niet goed nadat de Configuration Manager-client is geïnstalleerd. Zo kunnen de volgende takenreeksstappen mislukken:  

-   Gebruikersstatus herstellen na gebruik met een statusmigratiepunt  

-   Verbinding maken met netwerkmap  

Vanaf een opdrachtprompt met administratormachtigingen in de veilige modus kunt u bijvoorbeeld wel een PING-opdracht naar de computer verzenden, maar SMB-netwerkverkeer (zoals NET USE vanaf een opdrachtprompt) mislukt mogelijk met fout 1231: Kan de netwerklocatie niet bereiken.  

**Tijdelijke oplossing**:  
Voeg een takenreeksstap van opdrachtregel uitvoeren na de Windows en ConfigMgr installeren takenreeksstap te stoppen en start vervolgens de Workstation-service:    
**net stop werkstation /y & net start werkstation**  

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>Onderhoudsplannen maken standaard veel dubbele software-updategroepen en -implementaties  
De wizard Onderhoudsplan maken wordt momenteel standaard uitgevoerd na elke synchronisatie van software-updates. Telkens wanneer de wizard wordt uitgevoerd, wordt er een nieuwe software-updategroep en -implementatie gemaakt. Als u een synchronisatieplanning voor software-updates hebt die bijvoorbeeld meerdere keren per dag wordt uitgevoerd, maakt de wizard Onderhoudsplan maken elke dag meerdere, waarschijnlijk identieke software-updategroepen en -implementaties.  

**Tijdelijke oplossing**:    
Nadat u een plan portie maken, opent u de eigenschappen voor het onderhoud plan, gaat u naar de **Evaluatieschema** tabblad **de regel volgens een schema uitgevoerd**, klikt u op **aanpassen**, en een aangepaste planning te maken. U kunt bijvoorbeeld instellen dat het onderhoudsplan elke 60 dagen wordt uitgevoerd.  

### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>Wanneer een dialoogvenster met een hoog risico implementatie zichtbaar voor een gebruiker is, worden daaropvolgende met een hoog risico dialogen met een deadline voordat de niet weergegeven
Nadat u maken en implementeren van een implementatie met een hoog risico taak voor gebruikers, wordt een dialoogvenster met een hoog risico voor de gebruiker weergegeven. Als de gebruiker komt niet in het dialoogvenster sluiten, u maken en implementeren van een andere met een hoog risico implementatie met een voordat de deadline van de eerste, ontvangt de gebruiker niet een bijgewerkte dialoogvenster totdat ze de oorspronkelijke dialoogvenster hebt gesloten. Implementaties worden nog steeds uitgevoerd op de geconfigureerde deadlines.

**Tijdelijke oplossing**:  
De gebruiker moet in het dialoogvenster voor de eerste met een hoog risico implementatie om te zien in het dialoogvenster voor de volgende implementatie met een hoog risico sluiten.

## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="cannot-create-an-enrollment-profile-on-a-primary-site"></a>Er kan geen inschrijvingsprofiel worden gemaakt op een primaire site  
Een beheerder kan geen inschrijvingsprofiel maken in de System Center Configuration Manager-beheerconsole die verbinding maakt met een primaire site. Wanneer u probeert om in te schrijven, wordt de beheerder er een fout "DEP-token is niet bijgewerkt. Upload een DEP-token' in de wizard inschrijving profiel. Deze fout treedt op hoewel er een geldig DEP-token naar de centrale beheersite is geüpload.  

**Tijdelijke oplossing**: Een inschrijvingsprofiel maken in de System Center Configuration Manager-console die verbinding met de centrale beheersite maakt.  

### <a name="dep-cannot-use-non-alpha-numeric-characters-in-enrollment-profiles"></a>DEP kan geen gebruikmaken van niet-alfanumerieke tekens in inschrijvingsprofielen  
Inschrijvingsprofielen die zijn gekoppeld aan het Device Enrollment Profile (DEP) van Apple kunnen geen gebruikmaken van niet-alfanumerieke tekens in de velden **Naam**, **Beschrijving**, **Afdeling** en **Telefoonnummer** voor het inschrijvingsprofiel wanneer DEP is ingeschakeld. Wanneer u niet-alfanumerieke tekens in deze velden gebruikt, kunt u wel een inschrijvingsprofiel maken maar het profiel kan niet naar Apple worden geüpload. Er wordt geen foutbericht of waarschuwing verzonden door de Apple-server en de profielen worden niet geïmplementeerd voor apparaten die met DEP worden beheerd.  

**Tijdelijke oplossing**: Geen.

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Met Volledig wissen worden Windows 10-apparaten met minder dan 4 GB RAM uitgeschakeld

Nadat de functie Volledig wissen is uitgevoerd op een Windows 10 RTM-apparaat (versies vóór versie 1511) met minder dan 4 GB RAM, is het apparaat mogelijk niet meer bruikbaar. Na een poging om het apparaat te wissen, kan het niet meer worden opgestart of reageert het niet meer.

**Tijdelijke oplossing**: Zorg ervoor dat Windows 10 RTM-pc's hebben ten minste 4 GB aan RAM-geheugen beschikbaar voor het uitvoeren van een volledig wissen op het apparaat. Voer 'winver' achter de opdrachtprompt in als u het versienummer van Windows 10-apparaten wilt bekijken. Als het apparaat al is gewist en niet meer reageert, gebruikt u een opstartbaar Windows 10 USB-station om te starten en toegang tot het apparaat te herstellen.

### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Wanneer een gebruiker tot twee of meer gebruikersverzamelingen behoort waarvoor een voorwaardenbeleid is geïmplementeerd, krijgt deze meerdere reeksen met dezelfde voorwaarden te zien  

Wanneer een beheerder een reeks voorwaarden implementeert voor meerdere gebruikersverzamelingen, en een gebruiker is lid van meer dan één van deze verzamelingen, krijgt die gebruiker meerdere exemplaren van dezelfde voorwaarden te zien wanneer deze de bedrijfsportal opent.  Bijvoorbeeld, als een gebruiker met de naam "Voorbeeldgebruiker" een lid is van twee verschillende gebruikersverzamelingen is, een aangeroepen "CompanyEmployeesFTE" en "CompanyEmployeesNA", "en"CompanyTerms"genoemd voorwaarden CompanyEmployeesFTE en CompanyEmployeesNA is geïmplementeerd, voorbeeldgebruiker, ziet u twee identieke sets met CompanyTerms op de pagina voorwaarden accepteren. Omdat gebruikers alleen alle voorwaarden kunnen accepteren of weigeren, is er geen gevaar voor een dubbelzinnige acceptatiestatus waarbij de gebruiker de voorwaarden zowel heeft geaccepteerd als geweigerd. Het rapport Acceptatie van voorwaarden bevat slechts één rij voor elke set voorwaarden voor elke gebruiker. Het rapport bevat dus geen fouten. Het enige effect is dat de gebruiker op de pagina voor het accepteren van de voorwaarden twee reeksen voorwaarden te zien krijgt.  

**Tijdelijke oplossing**: Zorg ervoor dat elke gebruiker is alleen opgenomen in een verzameling die de voorwaarden worden geïmplementeerd.  

### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android voor werk e-mailprofielen die gebruikmaken van verificatie via certificaat worden niet toegepast op apparaten
<!--  487657 -->
Wanneer u een Android werk e-mailprofiel maakt, zijn er twee opties voor verificatie. Een gebruikersnaam en het wachtwoord is, en de andere certificaten. Op dit moment werkt de optie certificaten niet. Als het profiel is gemaakt met de verificatiemethode die wordt ingesteld op **certificaten**, het profiel wordt niet toegepast op het apparaat en de gebruiker wordt gevraagd de e-mailaccountdetails handmatig invoeren.

**TIJDELIJKE OPLOSSING**: Geen. Beheerders moet gebruiken de **gebruikersnaam en wachtwoord** optie of wacht u totdat dit probleem is opgelost.

## <a name="reports-and-monitoring"></a>Rapporten en controle  

### <a name="the-health-attestation-report-is-empty-even-though-health-attestation-data-was-previously-collected"></a>Het Health Attestation-rapport is leeg, hoewel er wel Health Attestation-gegevens zijn verzameld  
Wanneer een gebruiker met beheerdersrechten die een beveiligingsrol met een **Leesmachtiging** voor de machtigingsgroep **Apparaatstatusverklaring** heeft, het Health Attestation-rapport weergeeft, is het rapport leeg en worden de gegevens niet weergegeven. Dit komt doordat de machtigingen om gegevens weer te geven in het Health Attestation-rapport, zijn gekoppeld aan de machtigingsgroep **Gebruikersaffiniteit apparaat** in plaats van de machtigingsgroep Health Attestation.  

Dit probleem is van invloed op de System Center Configuration Manager met update 1602 en kunnen worden omgezet in een toekomstige update wordt verwacht.  

**Tijdelijke oplossing**: Een beveiligingsgroep met de gebruiker met beheerdersrechten toewijzen de **lezen** machtiging voor het **affiniteiten van gebruikersapparaat** machtigingsgroep.  

### <a name="conditional-access"></a>Voorwaardelijke toegang  

#### <a name="the-same-user-collection-is-not-blocked-from-being-added-to-both-exempted-and-targeted-collections"></a>Het toevoegen van deze gebruikersverzameling aan vrijgestelde en doelverzamelingen wordt niet geblokkeerd.  
Dit gebeurt alleen als u deze **gebruikersverzameling** toevoegt aan de pagina **Vrijgestelde verzameling** **voordat** u deze toevoegt aan de pagina **Doelverzameling**.  Als u eerst een **gebruikersverzameling** toevoegt aan de pagina **Doelverzamelingen** en dezelfde **gebruikersverzameling** vervolgens probeert toe te voegen aan de pagina **Vrijgestelde verzameling**, wordt het normale blokkeerbericht weergegeven.  

Dit probleem ondervindt voorwaardelijke toegang voor System Center Configuration Manager **Exchange On-Premises** bijwerken met 1602 en kunnen worden omgezet in een toekomstige update wordt verwacht.  

**Tijdelijke oplossing:** Toevoegen de **Gebruikersverzameling** naar **verzamelingen gericht** pagina voordat u selecteert **Gebruikersverzameling** op de **verzameling uitgesloten** pagina of zorg ervoor dat u dezelfde niet toevoegt **Gebruikersverzameling** doel en uitgesloten verzamelingen.

## <a name="endpoint-protection"></a>Endpoint Protection
<!--  Product Studio bug 485370 added by Nathbarn 04 19 2017 -->
### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Antimalware-beleid niet van toepassing op Windows Server 2016 Core
Beleidsregel kan niet van toepassing op Windows Server 2016 Core.  De foutcode is 0x80070002.  Er is een ontbrekende afhankelijkheid voor ConfigSecurityPolicy.exe.

**Tijdelijke oplossing:**  Dit probleem is opgelost door [Knowledge Base-artikel 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) 9 mei 2017 gedistribueerd. 

