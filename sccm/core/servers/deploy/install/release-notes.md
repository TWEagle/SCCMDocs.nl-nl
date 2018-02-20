---
title: 'Release-opmerkingen '
titleSuffix: Configuration Manager
description: Raadpleeg deze opmerkingen voor urgente problemen die nog niet zijn opgelost in het product of in een Microsoft Knowledge Base-artikel besproken.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 53685ef2647cfd87c2fcb603097186360f1c96a5
ms.sourcegitcommit: fbd4a9d2fa8ed4ddd3a0fecc4a2ec4fc0ccc3d0c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2018
---
# <a name="release-notes-for-system-center-configuration-manager"></a>Opmerkingen bij de release van System Center Configuration Manager

Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Met Configuration Manager opmerkingen bij de productrelease zijn beperkt tot urgente problemen. Deze problemen zijn nog niet opgelost in het product of worden uiteengezet in een Microsoft Knowledge Base-artikel.  

Functiespecifieke documentatie bevat informatie over bekende problemen die invloed hebben op de belangrijkste scenario's.  

> [!TIP]  
>  Dit onderwerp bevat opmerkingen bij de release voor de huidige vertakking van Configuration Manager. Zie voor informatie over de vertakking technical preview, [Technical Preview voor System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

Zie voor informatie over de nieuwe functies geïntroduceerd met verschillende versies, de volgende artikelen:
- [Wat is er nieuw in versie 1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)
- [Wat is er nieuw in versie 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)  
- [Wat is er nieuw in versie 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)



## <a name="setup-and-upgrade"></a>Installatie en upgrade  


### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Als u een Service-vertakking Long-Term site met versie 1606 installeert, is een Current Branch-site geïnstalleerd
<!-- Consider move to core content  -->
Wanneer u de media versie 1606 basislijn van de release van oktober 2016 gebruikt om een site Long-Term Servicing Branch (LTSB) te installeren, installeert Setup in plaats daarvan een Current Branch-site. Dit probleem treedt op omdat de optie voor het installeren van een service connection point met installeren van de site niet is ingeschakeld.

 - Hoewel een serviceverbindingspunt niet vereist is, moet het worden geselecteerd om te installeren tijdens de installatie van een site LTSB te installeren.

Nadat Setup is voltooid, kunt u het serviceverbindingspunt verwijderen. U moet echter een serviceaansluitpunt in de modus offline of online om te verzenden van telemetriegegevens en om beveiligingsupdates te krijgen voor zowel Current Branch en LTSB sites hebben.

Als uw site hebt geïnstalleerd als een Current Branch-site, maar u de LTSB installeren wilt, kunt u de site verwijderen en opnieuw installeren. U kunt ook aanroepen [Microsoft Help en ondersteuning](http://go.microsoft.com/fwlink/?LinkId=243064) voor hulp.  

Om te controleren welke vertakking geïnstalleerd in de console op **beheer** > **siteconfiguratie** > **Sites**, en open **hiërarchie-instellingen**. De optie voor het converteren van de site naar een Current Branch-site is alleen beschikbaar wanneer de site de LTSB wordt uitgevoerd.  

**Tijdelijke oplossing:** Geen.   


### <a name="an-update-persists-in-downloading-state-in-the-updates-and-servicing-node-of-the-console"></a>Een update zich blijft voordoen bij het downloaden van de status in de Updates en onderhoud van knooppunt van de console  
<!-- Source bug pending. Consider move to core content.  8/15 Seeking validation of issue from Dev.  -->
Tijdens de automatische download van updates via een onlineserviceaansluitpunt kan een update zijn vastgelopen met een status downloaden. Wanneer het downloaden van een update is vastgelopen, worden in de aangegeven logboekbestanden vermeldingen weergegeven die lijken op het volgende:  

Logboek van DMPdownloader:  
`ERROR: Failed to download redist for 037cd17e-4d7b-40e1-802b-14bb682364c7 with command  /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 /LnManifestUrl http://go.microsoft.com/fwlink/?LinkID=724434 /RedistVersion 112015 /NoUI  "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"`  

ConfigMgrSetup.log:  
`Error: failed to verify 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi' authenticode signature.`  
`Error: file signature check failed for 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi`  

**Tijdelijke oplossing**: Wijzig de volgende registersleutel, zodat deze overeenkomen met de volgende waarde op de siteserver:  

-   **Sleutel voor bewerking**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software Publishing  

-   **Waarde voor status**: Ingesteld op **146944** decimale of **0x00023e00** hexadecimale  

Vervolgens start de SMS_Executive-service opnieuw of wacht maximaal 24 uur totdat de volgende automatische download.

### <a name="when-using-redistributable-files-from-the-cdlatest-folder-setup-fails-with-a-manifest-verification-error"></a>Als u de herdistribueerbare bestanden vanaf de CD. Meest recente map setup is mislukt met een manifest verificatiefout
<!-- Source bug pending    8/15 Seeking validation of issue from Dev.   -->

Wanneer u Setup uitvoert vanaf de CD. Meest recente map gemaakt voor versie 1606 en herdistribueerbare bestanden die deel uitmaakt van deze CD gebruiken. Meest recente map, mislukt de installatie met de volgende fouten in het logboek van Setup van Configuration Manager:

  `ERROR: File hash check failed for defaultcategories.dll`  
  `ERROR: Manifest verification failed. Wrong version of manifest?`

**Tijdelijke oplossing:** Gebruik een van de volgende opties:
 - Tijdens de installatie, kiezen voor het downloaden van de meest recente herdistribueerbare bestanden van Microsoft. Gebruik de meest recente herdistribueerbare bestanden in plaats van de bestanden in de CD. Meest recente map.
 - Verwijder handmatig de *cd.latest\redist\languagepack\zhh* map en voer vervolgens Setup opnieuw uit.



<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>Clientimplementatie en -upgrade  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Installatie van de client mislukt met foutcode 0x8007064c
<!--- SMS 486973  applies 1606 to 1706. Not yet fixed. -->
*Het volgende probleem geldt voor alle actieve versies van Configuration Manager.*  

Wanneer u de client op Windows-computers te implementeren, mislukt de installatie. Het bestand ccmsetup.log bevat de volgende items: 

`File 'C:\WINDOWS\ccmsetup\Silverlight.exe' returned failure exit code 1612. Fail the installation`  
`InstallFromManifest failed 0x8007064c`

**Tijdelijke oplossing**: Dit probleem wordt veroorzaakt door een beschadigd, eerder geïnstalleerde versie van Silverlight. U kunt dit probleem oplossen door de volgende hulpprogramma op de desbetreffende computer worden uitgevoerd: [Problemen oplossen die blokkeren van programma's niet kan worden geïnstalleerd of verwijderd](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed).

## <a name="operating-system-deployment"></a>Implementatie van besturingssystemen  

### <a name="servicing-plans-create-many-duplicate-software-update-groups-and-deployments-by-default"></a>Onderhoudsplannen maken veel dubbele software-updategroepen en implementaties standaard  
De wizard Onderhoudsplan maken wordt momenteel standaard uitgevoerd na elke synchronisatie van software-updates. Telkens wanneer de wizard wordt uitgevoerd, wordt er een nieuwe software-updategroep en -implementatie gemaakt. Als u een synchronisatieplanning voor software-updates die meerdere keren per dag wordt uitgevoerd hebt, maakt de wizard Onderhoudsplan maken meerdere software-updategroepen en implementaties elke dag.  

**Tijdelijke oplossing**: Nadat u een onderhoudsplan hebt gemaakt, opent u de eigenschappen voor het onderhoudsplan, gaat u naar de **Evaluatieplanning** tabblad **e regel uitvoeren volgens een schema**, klikt u op **aanpassen**, en maak een aangepaste planning. U kunt bijvoorbeeld instellen dat het onderhoudsplan elke 60 dagen wordt uitgevoerd.  



## <a name="software-updates"></a>Software-updates

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Een Office 365 client-instellingen importeren vanuit een configuratiebestand mislukt wanneer het niet-ondersteunde talen bevat
<!-- 489258  Fixed in 1706  -->
*Het volgende probleem geldt voor versie 1702 en eerdere versies.*   

Wanneer u de instellingen van de Office 365 client uit een bestaande XML-configuratiebestand importeren, en het bestand bevat de talen die niet worden ondersteund door de Office 365 ProPlus-client, wordt er een fout optreedt. Zie voor meer informatie: [Office 365-apps implementeren op clients vanuit het Office 365 Client Management dashboard](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Tijdelijke oplossing**: Gebruik alleen de [talen die worden ondersteund door de Office 365 ProPlus-client](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) in het XML-configuratiebestand.  



## <a name="mobile-device-management"></a>Beheer van mobiele apparaten  

### <a name="beginning-with-version-1710-you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10------503274--should-be-fixed-by-1802-if-not-sooner---"></a>Vanaf versie 1710, u kunt niet langer Windows Phone 8.1 VPN-profielen implementeren op Windows 10   <!-- 503274  Should be fixed by 1802, if not sooner -->
In 1710 is het niet meer mogelijk te maken van een VPN-profiel met de Windows Phone 8.1-werkstroom die is ook van toepassing op Windows 10-apparaten. Voor deze profielen wordt de pagina ondersteunde Platforms niet meer weergegeven in de wizard maken. Windows Phone 8.1 wordt automatisch geselecteerd op de back-end. De pagina ondersteunde Platforms is beschikbaar in de eigenschappen van het profiel, maar de opties voor Windows 10 worden niet weergegeven.

**Tijdelijke oplossing**: Gebruik de werkstroom van Windows 10 VPN-profiel voor Windows 10-apparaten. Als deze optie niet haalbaar voor uw omgeving is, moet u contact op met ondersteuning. Ondersteuning kunt u het doelitem voor Windows 10 kunt toevoegen.


### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-of-memory"></a>Volledig wissen schakelt Windows 10-apparaten met minder dan 4 GB geheugen
Voor informatie over het uitvoeren van volledig wissen op apparaten met Windows 10 kan versie 1507, met minder dan 4 GB RAM-geheugen leiden dat het apparaat onbruikbaar. Na het wissen van het apparaat, deze kan niet worden gestart en reageert niet.

**Tijdelijke oplossing**: Zorg ervoor dat Windows 10-apparaten hebben ten minste 4 GB geheugen beschikbaar, voordat u een volledig wissen uitvoeren. Voer 'winver' achter de opdrachtprompt in als u het versienummer van Windows 10-apparaten wilt bekijken. Als u het apparaat al hebt gewist en niet meer reageren is, gebruikt u een opstartbaar Windows 10-USB-station te herstellen van het apparaat.


### <a name="when-a-user-belongs-to-two-or-more-user-collections-to-which-you-deploy-a-terms-and-conditions-policy-the-user-sees-multiple-sets-of-the-same-terms"></a>Wanneer een gebruiker tot twee of meer verzamelingen van gebruikers waarop u een beleid voor voorwaarden implementeert behoort, ziet de gebruiker meerdere sets met dezelfde voorwaarden  
<!-- 454394    -->
Als u een set voorwaarden naar meerdere gebruikersverzamelingen implementeert, en een gebruiker lid van meer dan één van deze verzamelingen is, ziet deze gebruiker meerdere exemplaren van dezelfde voorwaarden in de bedrijfsportal. Bijvoorbeeld:
- Een gebruiker met de naam 'Voorbeeldgebruiker' is lid van twee verschillende gebruikersverzamelingen, 'Bedrijfwerknemersft' als 'Bedrijfwerknemerspt'
- U implementeert de 'CompanyTerms' voorwaarden en bepalingen op zowel Bedrijfwerknemersft als Bedrijfwerknemerspt
- Voorbeeldgebruiker ziet twee identieke reeksen companyterms op de pagina van de acceptatie van voorwaarden in de bedrijfsportal. 

Gebruikers kunnen alleen Alles accepteren of weigeren van de voorwaarden. Het is dus geen gevaar voor een niet-eenduidige acceptatiestatus. (Deze onduidelijke status is waar de gebruiker accepteert en weigert van dezelfde voorwaarden). Het rapport van de acceptatie van voorwaarden bevat slechts één rij voor elke set voorwaarden per gebruiker, zodat er geen fout in het rapport is. Het enige effect is dat de gebruiker twee sets voorwaarden op de pagina acceptatie ziet.  

**Tijdelijke oplossing**: Zorg ervoor dat elke gebruiker is opgenomen in slechts één verzameling waarnaar u de voorwaarden zijn geïmplementeerd.  


<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
