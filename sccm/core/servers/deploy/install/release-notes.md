---
title: Release-opmerkingen - Configuration Manager | Microsoft Docs
description: Raadpleeg deze opmerkingen voor urgente problemen die nog niet zijn opgelost in het product of in een Microsoft Knowledge Base-artikel besproken.
ms.custom: na
ms.date: 05/31/2017
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
ms.sourcegitcommit: dc221ddf547c43ab1f25ff83c3c9bb603297ece6
ms.openlocfilehash: 6113576ca38da27e9e8732b3930deee96db4ae2c
ms.contentlocale: nl-nl
ms.lasthandoff: 06/01/2017


---
# <a name="release-notes-for-system-center-configuration-manager"></a>Opmerkingen bij de release van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met System Center Configuration Manager opmerkingen bij de productrelease zijn beperkt tot urgente problemen die nog niet zijn opgelost in het product (beschikbaar via een update in de console) of uiteengezet in een Microsoft Knowledge Base-artikel.  

 In het geval van bekende problemen die van invloed zijn op belangrijke scenario's, worden deze gegevens vermeld in de onlineproductdocumentatie in de documentatiebibliotheek van System Center Configuration Manager.  

> [!TIP]  
>  Dit onderwerp bevat opmerkingen bij de release voor de huidige vertakking van System Center Configuration Manager. Zie voor de Technical Preview voor System Center Configuration Manager [Technical Preview voor System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

## <a name="setup-and-upgrade"></a>Installatie en upgrade  

### <a name="after-you-update-a-configuration-manager-console-using-consolesetupexe-from-the-site-server-folder-recent-language-pack-changes-are-not-available"></a>Na het bijwerken van een Configuration Manager-console met behulp van ConsoleSetup.exe vanaf de site server-map zijn recente language pack wijzigingen niet beschikbaar
<!--  SMS 486420  Applicability should be 1610 and 1702.  -->
Nadat u een update in-place uitgevoerd naar een console via ConsoleSetup.exe uit de installatiemap van een site-servers, is onlangs geïnstalleerde taal packs mogelijk niet beschikbaar. Dit gebeurt wanneer:
- Uw site versie 1610 of 1702 wordt uitgevoerd.
- De console wordt bijgewerkt in-place via ConsoleSetup.exe uit de installatiemap van de site server.

Als dit probleem optreedt, gebruikt de opnieuw geïnstalleerde console niet de meest recente set van taalpakketten die zijn geconfigureerd. Er zijn geen fouten geretourneerd, maar language packs beschikbare naar de console wordt niet gewijzigd.  

**Tijdelijke oplossing:** Verwijder de huidige console en vervolgens opnieuw installeren als een nieuwe installatie van de console. U kunt ConsoleSetup.exe gebruiken uit de installatiemap van de site-servers. Zorg dat u selecteert de language pack-bestanden die u wilt gebruiken tijdens de installatie.


### <a name="with-version-1702-the-default-site-boundary-group-is-configured-for-use-for-site-assignment"></a>Met versie 1702, is de standaardgroep voor de grens van site geconfigureerd voor gebruik voor sitetoewijzing
<!--  SMS 486380   Applicability should only be to 1702. -->
Met versie 1702, het tabblad standaard site grens groepen verwijzing is een controle voor de **deze grensgroep gebruiken voor sitetoewijzing**, geeft een lijst van de site als de **toegewezen site**, en lichter gekleurd weergegeven zodat de configuratie kan niet worden bewerkt of verwijderd.

**Tijdelijke oplossing:** Geen. U kunt deze instelling negeren. Hoewel de groep voor sitetoewijzing is ingeschakeld, wordt de standaard sitegrensgroep niet gebruikt voor sitetoewijzing. Met 1702, deze configuratie zorgt ervoor dat de standaard site-grensgroep is gekoppeld aan de juiste site.



### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Als u een Service-vertakking Long-Term site met versie 1606 installeert, is een Current Branch-site geïnstalleerd
<!-- Consider move to core content  -->
Wanneer u de media versie 1606 basislijn van de release van oktober 2016 gebruikt om een site Long-Term Servicing Branch (LTSB) te installeren, installeert Setup in plaats daarvan een Current Branch-site. Dit gebeurt omdat de optie voor het installeren van een service connection point met installeren van de site niet is ingeschakeld.

 - Hoewel een serviceverbindingspunt niet vereist is, moet het worden geselecteerd om te installeren tijdens de installatie van een site LTSB te installeren.

Nadat Setup is voltooid, kunt u het serviceverbindingspunt verwijderen.  U moet echter een serviceaansluitpunt in de modus offline of online om te verzenden van telemetriegegevens en om beveiligingsupdates te krijgen voor zowel Current Branch en LTSB sites hebben.

Als uw site hebt geïnstalleerd als een Current Branch-site, maar u de LTSB installeren wilt, kunt u de site verwijderen en opnieuw installeren. U kunt ook aanroepen [Microsoft Help en ondersteuning](http://go.microsoft.com/fwlink/?LinkId=243064) voor hulp.  

Om te controleren welke vertakking geïnstalleerd in de console op **beheer** > **siteconfiguratie** > **Sites**, en open **hiërarchie-instellingen**. De optie voor het converteren van de site naar een Current Branch-site is alleen beschikbaar wanneer de site de LTSB wordt uitgevoerd.  

**Tijdelijke oplossing:**  Geen.   



### <a name="the--sql-server-backup-model-in-use-by-configuration-manager-can-change-from-full-to-simple"></a>Het SQL Server-back-upmodel dat wordt gebruikt door Configuration Manager kan worden gewijzigd van volledig in eenvoudig  
<!-- Confirm applicability for upgrade to later baselines. 1511 is out of support. 1606 is minmum supported baseline  -->

 Wanneer u bijwerkt naar System Center Configuration Manager versie 1511, kan het SQL Server-back-upmodel dat door Configuration Manager wordt gebruikt, worden gewijzigd van volledig in eenvoudig.  

-   Als u een aangepaste SQL Server-back-uptaak voor het volledige back-upmodel gebruikt (in plaats van de ingebouwde back-uptaak voor Configuration Manager), is het mogelijk dat het volledige back-upmodel met de upgrade wordt gewijzigd in een eenvoudig back-upmodel.  

**Tijdelijke oplossing**: Na een upgrade naar versie 1511, controleert u uw SQL Server-configuratie en herstelt u deze indien nodig volledig.  



### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Een update is vastgelopen met een status Downloaden in het knooppunt Updates en onderhoud van de Configuration Manager-console  
<!-- Source bug pending. Consider move to core content.  -->
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
<!-- Source bug pending  -->

Wanneer u Setup uitvoert vanaf een CD. Meest recente map gemaakt voor versie 1606 en opgenomen in die CD redist bestanden gebruiken. Meest recente map, mislukt de installatie met de volgende fouten in het logboek van Setup van Configuration Manager:

  - FOUT: Er is een bestand hash-controle mislukt voor defaultcategories.dll
  - FOUT: Manifest verificatie is mislukt. Verkeerde versie van het manifest?

**Tijdelijke oplossing:**  Gebruik een van de volgende opties:
 - Kies tijdens de installatie van de meest recente redist om bestanden te downloaden van Microsoft te gebruiken in plaats van deze die zijn opgenomen in de CD. Meest recente map.
 - Verwijder handmatig de *cd.latest\redist\languagepack\zhh* map en voer vervolgens Setup opnieuw uit.

### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>Hulpprogramma voor serviceverbindingen er een uitzondering gegenereerd als SQL server staat, of wanneer het gedeelde geheugen is uitgeschakeld
Vanaf versie 1606, het hulpprogramma voor serviceverbindingen een uitzondering gegenereerd wanneer een van de volgende waar is:  
 -    De sitedatabase zich op afstand van de computer die als host fungeert voor het service connection point en gebruikt een niet-standaardpoort (een andere poort dan 1433)
 -     De sitedatabase zich op dezelfde server als het serviceverbindingspunt wordt gehost, maar SQL-protocol **Shared Memory** is uitgeschakeld

De uitzondering is vergelijkbaar met het volgende:
 - *Niet-verwerkte uitzondering: System.Data.SqlClient.SqlException: Er is een netwerkgerelateerde of exemplaarspecifieke fout opgetreden tijdens het maken van een verbinding met SQL Server. De server is niet gevonden of is niet toegankelijk. Controleer of dat de exemplaarnaam juist is en dat SQL Server is geconfigureerd voor externe verbindingen. (provider: Named Pipes-Provider, fout: 40 - kan geen verbinding openen met SQL Server)--*

**Tijdelijke oplossing**: Tijdens het gebruik van het hulpprogramma moet u het register van de server die als host fungeert voor het service connection point met informatie over de SQL Server-poort wijzigen:

   1.    De volgende registersleutel bewerken voordat u het hulpprogramma gebruikt, en het nummer van de poort die wordt gebruikt op de naam van de SQL-Server toevoegen:
    - Sleutel:   HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - Waarde: &lt;SQL-servernaam >
    - Toevoegen: **,&lt;poort >**

    Bijvoorbeeld poort *15001* naar een server met de naam *testserver.test.net*, zou de resulterende sleutel: ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.NET,15001***

   2.    Na het toevoegen van de poort in het register, moet het hulpprogramma normaal functioneren.  

   3.    Nadat uw gebruik van het hulpprogramma voltooid voor zowel is de **-verbinding** en **-importeren** stappen, wijzigt u de registersleutel terug naar de oorspronkelijke waarde.  




<!-- No current Backup and Recovery relenotes
## Backup and recovery
-->



## <a name="client-deployment-and-upgrade"></a>Clientimplementatie en -upgrade  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Installatie van de client mislukt met foutcode 0x8007064c
<!--- SMS 486973 -->

Wanneer u de client op Windows-computers te implementeren, mislukt de installatie. Het bestand ccmsetup.log bevat een item ' File 'C:\WINDOWS\ccmsetup\Silverlight.exe' afsluitcode 1612 geretourneerd. Mislukt de installatie' gevolgd door 'InstallFromManifest is mislukt 0x8007064c'.

**Tijdelijke oplossing** dit wordt veroorzaakt door een beschadigd, eerder geïnstalleerde versie van Silverlight. U kunt het volgende programma wordt uitgevoerd op de desbetreffende computer om dit te corrigeren: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed)




## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

### <a name="issue-with-the-windows-adk-for-windows-10-version-1511"></a>Probleem met Windows ADK voor Windows 10 versie 1511  
Wanneer u een takenreeks vanuit Software Center die gebruikmaakt van een Windows PE v.10.0.10586-opstartinstallatiekopie uit de Windows ADK 10 versie 1511 uitvoert, wanneer de computer opnieuw in Windows PE opgestart, zal mislukken bij 'Hardwareapparaten initialiseren' met de fout: **Windows PE-initialisatie is mislukt met foutcode 0x80220014**  

**Tijdelijke oplossing**: Gebruik de oorspronkelijke Windows 10 ADK. Zie voor meer informatie de volgende System Center Configuration Manager-teamblog: [Probleem met de Windows ADK voor Windows 10](http://blogs.technet.com/b/configmgrteam/archive/2015/11/20/issue-with-the-windows-adk-for-windows-10-version-1511.aspx)  

### <a name="dynamic-application-installation-fails-during-task-sequence-which-successfully-completes"></a>Installatie van dynamische toepassing mislukt tijdens de takenreeks die wordt voltooid  
Wanneer u een takenreeks implementeert die gebruikmaakt van de optie **Toepassingen installeren volgens de dynamische variabelenlijst** en een van de toepassingen wordt om een bepaalde reden niet geïnstalleerd, wordt door de takenreeks gerapporteerd dat de actie is geslaagd. Dit gebeurt ongeacht de manier waarop u de volgende opties configureert:  

-   **Doorgaan bij fout** (op het tabblad Opties van de stap Toepassing installeren)  

-   **Als de installatie van een toepassing mislukt, doorgaan met de installatie van andere toepassingen in de lijst** (op het tabblad Eigenschappen van de stap Toepassing installeren)  

U kunt het bestand smsts.log bekijken om te bepalen of de installatie van een toepassing is mislukt.  

**Tijdelijke oplossing**: Gebruik de **_TSAppInstallStatus** variabele als een voorwaarde voor de volgende stappen in een takenreeks met een voorwaarde voor de takenreeks mislukt als er een fout opgetreden bij een van de dynamische toepassingen.  

### <a name="smb-might-not-work-properly-after-you-use-a-task-sequence-to-install-windows-10"></a>SMB werkt mogelijk niet goed nadat u een takenreeks hebt gebruikt voor het installeren van Windows 10  
Wanneer u een takenreeks gebruikt om een installatiekopie van Windows 10 te installeren, werkt SMB mogelijk niet goed nadat de Configuration Manager-client is geïnstalleerd. Zo kunnen de volgende takenreeksstappen mislukken:  

-   Gebruikersstatus herstellen na gebruik met een statusmigratiepunt  

-   Verbinding maken met netwerkmap  

Vanaf een opdrachtprompt met administratormachtigingen in de veilige modus kunt u bijvoorbeeld wel een PING-opdracht naar de computer verzenden, maar SMB-netwerkverkeer (zoals NET USE vanaf een opdrachtprompt) mislukt mogelijk met fout 1231: Kan de netwerklocatie niet bereiken.  

**Tijdelijke oplossing**:  
Toevoegen van een takenreeksstap van opdrachtregel uitvoeren na de Windows en ConfigMgr installeren takenreeksstap te stoppen en start vervolgens de Workstation-service:    
**net stop werkstation /y & net start werkstation**  

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>Onderhoudsplannen maken standaard veel dubbele software-updategroepen en -implementaties  
De wizard Onderhoudsplan maken wordt momenteel standaard uitgevoerd na elke synchronisatie van software-updates. Telkens wanneer de wizard wordt uitgevoerd, wordt er een nieuwe software-updategroep en -implementatie gemaakt. Als u een synchronisatieplanning voor software-updates hebt die bijvoorbeeld meerdere keren per dag wordt uitgevoerd, maakt de wizard Onderhoudsplan maken elke dag meerdere, waarschijnlijk identieke software-updategroepen en -implementaties.  

**Tijdelijke oplossing**:    
Nadat u een onderhoudsplan hebt gemaakt, opent u de eigenschappen voor het onderhoudsplan, gaat u naar de **Evaluatieplanning** tabblad **e regel uitvoeren volgens een schema**, klikt u op **aanpassen**, en maak een aangepaste planning. U kunt bijvoorbeeld instellen dat het onderhoudsplan elke 60 dagen wordt uitgevoerd.  

### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>Wanneer een implementatie met hoog risico dialoogvenster zichtbaar voor een gebruiker is, worden daaropvolgende met een hoog risico dialoogvensters met een deadline vroeger niet weergegeven
Nadat u maken en implementeren van een implementatie met een hoog risico taak voor gebruikers, wordt een dialoogvenster met een hoog risico voor de gebruiker weergegeven. Als de gebruiker komt niet in het dialoogvenster sluiten en u maakt en implementeert een andere implementatie met hoog risico met een deadline vroeger dan de eerste, ontvangt de gebruiker niet een bijgewerkte dialoogvenster totdat ze de oorspronkelijke dialoogvenster hebt gesloten. De implementaties zullen nog steeds uitgevoerd op de geconfigureerde deadlines.

**Tijdelijke oplossing**:  
De gebruiker moet in het dialoogvenster voor de eerste implementatie met hoog risico om te zien in het dialoogvenster voor de volgende implementatie met hoog risico sluiten.

## <a name="software-updates"></a>Software-updates

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Een Office 365 client-instellingen importeren vanuit een configuratiebestand mislukt wanneer het niet-ondersteunde talen bevat
Wanneer u de instellingen van de Office 365 client uit een bestaande XML-configuratiebestand importeren, en het bestand bevat de talen die niet worden ondersteund door de Office 365 ProPlus-client, wordt er een fout optreden. Zie voor meer informatie [Office 365-apps implementeren op clients vanuit het Office 365 Client Management dashboard](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Tijdelijke oplossing**:    
Gebruik alleen de [talen die worden ondersteund door de Office 365 ProPlus-client](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) in het XML-configuratiebestand.  

## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="cannot-create-an-enrollment-profile-on-a-primary-site"></a>Er kan geen inschrijvingsprofiel worden gemaakt op een primaire site  
Een beheerder kan geen inschrijvingsprofiel maken in de System Center Configuration Manager-beheerconsole die verbinding maakt met een primaire site. Wanneer u probeert te registreren, wordt de beheerder er een fout 'DEP-token is niet bijgewerkt. Upload een DEP-token' in de wizard inschrijving profiel. Deze fout treedt op hoewel er een geldig DEP-token naar de centrale beheersite is geüpload.  

**Tijdelijke oplossing**: Een inschrijvingsprofiel maken in de System Center Configuration Manager-console die verbinding met de centrale beheersite maakt.  

### <a name="dep-cannot-use-non-alpha-numeric-characters-in-enrollment-profiles"></a>DEP kan geen gebruikmaken van niet-alfanumerieke tekens in inschrijvingsprofielen  
Inschrijvingsprofielen die zijn gekoppeld aan het Device Enrollment Profile (DEP) van Apple kunnen geen gebruikmaken van niet-alfanumerieke tekens in de velden **Naam**, **Beschrijving**, **Afdeling** en **Telefoonnummer** voor het inschrijvingsprofiel wanneer DEP is ingeschakeld. Wanneer u niet-alfanumerieke tekens in deze velden gebruikt, kunt u wel een inschrijvingsprofiel maken maar het profiel kan niet naar Apple worden geüpload. Er wordt geen foutbericht of waarschuwing verzonden door de Apple-server en de profielen worden niet geïmplementeerd voor apparaten die met DEP worden beheerd.  

**Tijdelijke oplossing**: Geen.

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Met Volledig wissen worden Windows 10-apparaten met minder dan 4 GB RAM uitgeschakeld

Nadat de functie Volledig wissen is uitgevoerd op een Windows 10 RTM-apparaat (versies vóór versie 1511) met minder dan 4 GB RAM, is het apparaat mogelijk niet meer bruikbaar. Na een poging om het apparaat te wissen, kan het niet meer worden opgestart of reageert het niet meer.

**Tijdelijke oplossing**: Zorg ervoor dat Windows 10 RTM-pc's hebben ten minste 4 GB RAM-geheugen beschikbaar voor het uitvoeren van een volledig wissen op het apparaat. Voer 'winver' achter de opdrachtprompt in als u het versienummer van Windows 10-apparaten wilt bekijken. Als het apparaat al is gewist en niet meer reageert, gebruikt u een opstartbaar Windows 10 USB-station om te starten en toegang tot het apparaat te herstellen.

### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Wanneer een gebruiker tot twee of meer gebruikersverzamelingen behoort waarvoor een voorwaardenbeleid is geïmplementeerd, krijgt deze meerdere reeksen met dezelfde voorwaarden te zien  

Wanneer een beheerder een reeks voorwaarden implementeert voor meerdere gebruikersverzamelingen, en een gebruiker is lid van meer dan één van deze verzamelingen, krijgt die gebruiker meerdere exemplaren van dezelfde voorwaarden te zien wanneer deze de bedrijfsportal opent.  Bijvoorbeeld, als een gebruiker met de naam 'Voorbeeldgebruiker' een lid is van twee verschillende gebruikersverzamelingen is, één met de naam 'Bedrijfwerknemersft' als 'Bedrijfwerknemerspt', ' en de voorwaarden en bepalingen genaamd 'CompanyTerms' wordt geïmplementeerd op zowel Bedrijfwerknemersft als Bedrijfwerknemerspt, krijgt voorbeeldgebruiker twee identieke reeksen companyterms op de pagina van de acceptatie van voorwaarden. Omdat gebruikers alleen alle voorwaarden kunnen accepteren of weigeren, is er geen gevaar voor een dubbelzinnige acceptatiestatus waarbij de gebruiker de voorwaarden zowel heeft geaccepteerd als geweigerd. Het rapport Acceptatie van voorwaarden bevat slechts één rij voor elke set voorwaarden voor elke gebruiker. Het rapport bevat dus geen fouten. Het enige effect is dat de gebruiker op de pagina voor het accepteren van de voorwaarden twee reeksen voorwaarden te zien krijgt.  

**Tijdelijke oplossing**: Zorg ervoor dat elke gebruiker is opgenomen in slechts één verzameling waarnaar u de voorwaarden zijn geïmplementeerd.  

### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android voor werk-e-mailprofielen die gebruikmaken van verificatie via certificaat worden niet toegepast op apparaten
<!--  487657 -->
Wanneer u een Android voor werk-e-mailprofiel maakt, zijn er twee opties voor verificatie. Een gebruikersnaam en het wachtwoord is, en de andere certificaten. Op dit moment is werkt de optie certificaten niet. Als het profiel is gemaakt met de verificatiemethode die is ingesteld op **certificaten**, het profiel wordt niet toegepast op het apparaat en de gebruiker wordt gevraagd de accountdetails e handmatig invoeren.

**TIJDELIJKE OPLOSSING**: Geen. Beheerders moet gebruiken de **gebruikersnaam en wachtwoord** optie of wacht totdat dit probleem is opgelost.

## <a name="reports-and-monitoring"></a>Rapporten en controle  

### <a name="the-health-attestation-report-is-empty-even-though-health-attestation-data-was-previously-collected"></a>Het Health Attestation-rapport is leeg, hoewel er wel Health Attestation-gegevens zijn verzameld  
Wanneer een gebruiker met beheerdersrechten die een beveiligingsrol met een **Leesmachtiging** voor de machtigingsgroep **Apparaatstatusverklaring** heeft, het Health Attestation-rapport weergeeft, is het rapport leeg en worden de gegevens niet weergegeven. Dit komt doordat de machtigingen om gegevens weer te geven in het Health Attestation-rapport, zijn gekoppeld aan de machtigingsgroep **Gebruikersaffiniteit apparaat** in plaats van de machtigingsgroep Health Attestation.  

Dit probleem is van invloed op de System Center Configuration Manager met update 1602 en wordt naar verwachting opgelost in een toekomstige update.  

**Tijdelijke oplossing**: Toewijzen van de gebruiker met beheerdersrechten een beveiligingsgroep met de **lezen** machtiging voor de **affiniteiten van gebruikersapparaat** machtigingsgroep.  

### <a name="conditional-access"></a>Voorwaardelijke toegang  

#### <a name="the-same-user-collection-is-not-blocked-from-being-added-to-both-exempted-and-targeted-collections"></a>Het toevoegen van deze gebruikersverzameling aan vrijgestelde en doelverzamelingen wordt niet geblokkeerd.  
Dit gebeurt alleen als u deze **gebruikersverzameling** toevoegt aan de pagina **Vrijgestelde verzameling** **voordat** u deze toevoegt aan de pagina **Doelverzameling**.  Als u eerst een **gebruikersverzameling** toevoegt aan de pagina **Doelverzamelingen** en dezelfde **gebruikersverzameling** vervolgens probeert toe te voegen aan de pagina **Vrijgestelde verzameling**, wordt het normale blokkeerbericht weergegeven.  

Dit probleem ondervindt voorwaardelijke toegang voor System Center Configuration Manager **Exchange On-Premises** met update 1602 en wordt naar verwachting opgelost in een toekomstige update.  

**Tijdelijke oplossing:** Toevoegen de **Gebruikersverzameling** naar **Doelverzamelingen** pagina voordat u selecteert **Gebruikersverzameling** op de **vrijgestelde verzameling** pagina, of zorg ervoor dat u dezelfde niet toevoegt **Gebruikersverzameling** voor zowel vrijgestelde en Doelverzamelingen.

## <a name="endpoint-protection"></a>Endpoint Protection
<!--  Product Studio bug 485370 added 04 19 2017 -->
### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Antimalware-beleid mislukt toepassen op Windows Server 2016 Core
Antimalwarebeleid mislukt op Windows Server 2016 Core toe te passen.  De foutcode is 0x80070002.  Er is een ontbrekende afhankelijkheid voor ConfigSecurityPolicy.exe.

**Tijdelijke oplossing:**  Dit probleem is opgelost door [Knowledge Base-artikel 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) 9 mei 2017 gedistribueerd.

<!-- Product Studio bug 462286 added  05 25 2017 and valid until July 2017 GA release -->
### <a name="windows-defender-advanced-threat-protection-policies-fail-on-older-client-agents"></a>Windows Defender Advanced Threat Protection-beleid niet op oudere clientagents

Windows Defender Advanced Threat Protection-beleid wordt gemaakt van een Configuration Manager versie 1610 of hoger siteserver mislukken wilt toepassen op Configuration Manager versie 1606 en oudere clients.  De clients zijn niet geïntegreerde en de evaluatie van het beleid een fout gemeld. De **Implementatiestatus** ziet u in de configuratie van Windows Defender Advanced Threat Protection **fout**.

**TIJDELIJKE OPLOSSING**: Configuration Manager-client bijwerken naar versie 1610 of hoger.

