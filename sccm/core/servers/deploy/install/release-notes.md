---
title: 'Release-opmerkingen '
titleSuffix: Configuration Manager
description: Raadpleeg deze opmerkingen voor urgente problemen die nog niet zijn opgelost in het product of in een Microsoft Knowledge Base-artikel besproken.
ms.custom: na
ms.date: 11/28/2017
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
ms.openlocfilehash: b156cd7762be59092bb46f4a4a992badcbd9d74a
ms.sourcegitcommit: 1dd051d8548a19b724bb8f9e6a2278a4901ed916
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/28/2017
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



## <a name="software-updates"></a>Software-updates

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Een Office 365 client-instellingen importeren vanuit een configuratiebestand mislukt wanneer het niet-ondersteunde talen bevat
<!-- 489258  Fixed in 1706  -->
*De volgende van toepassing op versie 1702 en eerdere versies.*   
Wanneer u de instellingen van de Office 365 client uit een bestaande XML-configuratiebestand importeren, en het bestand bevat de talen die niet worden ondersteund door de Office 365 ProPlus-client, wordt er een fout optreden. Zie voor meer informatie [Office 365-apps implementeren op clients vanuit het Office 365 Client Management dashboard](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Tijdelijke oplossing**:    
Gebruik alleen de [talen die worden ondersteund door de Office 365 ProPlus-client](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) in het XML-configuratiebestand.  



## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="beginning-with-version-1710-you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10------503274--should-be-fixed-by-1802-if-not-sooner---"></a>Vanaf versie 1710, u kunt niet langer Windows Phone 8.1 VPN-profielen implementeren op Windows 10<!-- 503274  Should be fixed by 1802, if not sooner -->
In 1710 is het niet meer mogelijk te maken van een VPN-profiel met de Windows Phone 8.1-werkstroom die is ook van toepassing op Windows 10-apparaten. De pagina ondersteunde Platforms is niet meer weergegeven in de wizard maken voor deze profielen, en Windows Phone 8.1 wordt automatisch geselecteerd op de back-end; de pagina ondersteunde Platforms is beschikbaar in de eigenschappenpagina's, maar de opties voor Windows 10 worden niet weergegeven.

**Tijdelijke oplossing**: Gebruik de werkstroom van Windows 10 VPN-profiel voor Windows 10-apparaten. Als dit niet haalbaar voor uw omgeving, moet u contact op met ondersteuning. Ondersteuning kunt u toevoegen met de Windows 10 ontwikkelt, indien nodig.


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
<!-- ## Endpoint Protection -->
