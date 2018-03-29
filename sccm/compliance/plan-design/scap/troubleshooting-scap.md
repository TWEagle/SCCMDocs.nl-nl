---
title: SCAP oplossen
titleSuffix: System Center Configuration Manager
description: De instellingen voor de SCAP-naleving als configuratiebasislijnen importeren en exporteren van de resultaten
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27261853-1641-4826-98c6-afbb73a1209d
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 8270db5f0a43f1c94c876bdbd59e45ee2ca85ac6
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-the-scap-extensions-for-microsoft-system-center-configuration-manager"></a>De SCAP-extensies voor Microsoft System Center Configuration Manager oplossen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

> [!Tip]  
> Deze functie is geïntroduceerd in Technical Preview-versie 1803 als een [functie van de voorlopige versie](/sccm/core/servers/manage/pre-release-features). Deze voorlopige versie van de SCAP-extensies kan worden geïnstalleerd op alle ondersteunde versies van de huidige vertakking van Configuration Manager en LTSB 1606. Het installatiebestand bevindt zich op cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi vanaf technical preview 1803. 

SCAP Extensions voor Microsoft System Center Configuration Manager zijn ontworpen voor gebruik met de SCAP-gegevensstromen die bestemd zijn voor het door SCAP gevalideerde hulpprogramma met ACS-mogelijkheden ter ondersteuning van USGCB. Normaal gesproken won't u problemen ondervindt met deze USGCB SCAP-gegevensstromen die zijn gedownload van de NIST-website.

U kunt echter diagnosticeren en oplossen van problemen die kunnen optreden met de volgende methoden:

- Zorg ervoor dat de SCAP Extensions-client (scmdcm.msi)-onderdelen zijn geïnstalleerd op de doelcomputers.
- Controleer de logboekbestandsuitvoer van het hulpprogramma Microsoft.Sces.ScapToDcm.exe.
- Bekijk de veelvoorkomende problemen en oplossingen bij gebruik van SCAP-extensies.
- Neem contact op met Microsoft voor vragen of opmerkingen over SCAP-extensies.



## <a name="review-microsoftscesscaptodcmexe-tool-log"></a>Bekijk Microsoft.Sces.ScapToDcm.exe hulpprogramma logboek

Het hulpprogramma Microsoft.Sces.ScapToDcm.exe maakt met een aangepaste naam logboek wanneer het – logboek parameter wordt opgegeven. Het logboekbestand bevat informatie over de resultaten van het programma Microsoft.Sces.ScapToDcm.exe wordt uitgevoerd. Het logboekbestand heeft bijvoorbeeld het aantal items in het invoerbestand XCCDF/DataStream die zijn verwijderd of overgeslagen tijdens het uitvoeren van het hulpprogramma Microsoft.Sces.ScapToDcm.exe.

De volgende tabel bevat enkele van de informatie die wordt weergegeven in het logboekbestand en een beschrijving van elk type informatie.

### <a name="description-of-information-found-in-microsoftscesscaptodcmexe-log-files"></a>Beschrijving van de informatie in de logboekbestanden Microsoft.Sces.ScapToDcm.exe gevonden

| Informatie | Beschrijving |
| --- | --- |
| vervolgkeuzelijst | Een item kan worden verwijderd omdat het testtype geen ondersteund testtype is. |
| Overslaan |De definitie-ID OVAAL is voor een ongeldige platform. </br> </br> De definitie-ID OVAAL wordt niet verwezen door het invoerbestand XCCDF/DataStream.</br> </br> Test-ID OVAAL wordt niet verwezen door het invoerbestand XCCDF/DataStream. </br> </br> De profiel-ID XCCDF bevat geen @select instructies gelijk aan 1. </br> </br> De profiel-ID XCCDF bevat een abstract kenmerk dat is ingesteld op true. </br> </br> De profiel-ID XCCDF bevat geen een regel die in aanmerking komen.|

## <a name="common-problems-and-solutions"></a>Veelvoorkomende problemen en oplossingen

De volgende tabel bevat enkele veelvoorkomende problemen en oplossingen om u te helpen bij het oplossen.

Tabel 1.6 veelvoorkomende problemen en oplossingen

| Probleem | Mogelijke oplossing |
| --- | --- |
| Als er een **fout** of **onbekende** statussen van een basislijn en IE het rapport kunnen niet met succes wordt weergegeven. IE zegt &quot;het rapport is leeg of ongeldig&quot; | Selecteer de basislijn en klik op **Evaluate** de basislijn opnieuw uitvoeren en vervolgens wachten voor het bewaken van de **compatibele status**/**laatste evaluatie update**. Nadat de datum van laatste evaluatie is bijgewerkt naar de huidige datum/tijd (betekent dat deze de evaluatie voltooid), selecteert u de basislijn en het rapport opnieuw weergeven. Als er nog IE het rapport niet weergeven, kan dit betekenen dat de basislijn is te groot. Opnieuw genereren van de inhoud met een kleinere batchgrootte kleinere onderliggende basislijnen te maken. Als dit probleem er op de bovenliggende basislijnen gebeurt, kunt u in plaats daarvan de onderliggende basislijnen implementeren. |
| Ik heb groepsbeleidsobjecten (GPO's) die de voorgeschreven USGCB-instellingen zijn gemaakt en deze gekoppeld aan de organisatie-eenheden (OE's) die computers met Windows 7 bevatten, maar de compatibiliteitsrapporten geven echter aan enkele van de instellingen niet zijn geconfigureerd correct. | Het is mogelijk dat de machtigingen van het groepsbeleid onjuist zijn of dat ze niet zijn gekoppeld aan de juiste organisatie-eenheid. Het is echter waarschijnlijk dat de nieuwe instellingen zijn niet van kracht. Controleren op updates voor Groepsbeleid om de 90 minuten standaard Group Policy client-computers die deel uitmaken van een Active Directory-domein. Kan dit een reden waarom de instellingen niet zijn toegepast, worden zelfs als u de beleidsregels correct hebt geconfigureerd. Een andere factor te onthouden is dat veel instellingen van de computer opnieuw worden opgestart moeten voordat ze worden pas van kracht. Bijvoorbeeld, de instelling aangeroepen ** Systeemcryptografie: FIPS-algoritmen gebruiken voor versleuteling, hashing en ondertekening, moet u de computer opnieuw opstarten voordat Windows de opgegeven versleutelingsalgoritmen kan gebruiken. U kunt het interval voor vernieuwen van Groepsbeleid met de volgende opdracht bij een opdrachtprompt met beheerdersbevoegdheden overslaan: gpupdate/force na het groepsbeleid is vernieuwd, start opnieuw op de computer om ervoor te zorgen dat alle instellingen te treden laten. Zie voor meer informatie: [Een beschrijving van de groep het hulpprogramma voor updates](http://support.microsoft.com/kb/298444), Knowledge Base-artikel 298444. |
| Ik ondervind problemen met het verstrekken van de databaseverbinding bij mijn organisatiegegevens. | Zie voor informatie over het configureren van de verbindingsgegevens van uw database, de [installeren en configureren van SCAP](/sccm/compliance/plan-design/scap/install-configure-scap) artikel. 

## <a name="next-step"></a>Volgende stap
> [!div class="nextstepaction"]
> [Installeer en configureer SCAP-extensies](/sccm/compliance/plan-design/scap/install-configure-scap)