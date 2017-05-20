---
title: Beveiliging en privacy voor implementatie van besturingssysteem | Microsoft-documenten
description: Meer informatie over beveiliging en privacy aanbevolen procedures voor implementatie van besturingssystemen in System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ee5928f-3d72-4b00-8156-1e0d1030a96c
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 5632a753fc565312a80b2ed69ce438335b3fad50
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-operating-system-deployment-in-system-center-configuration-manager"></a>Beveiliging en privacy in System Center Configuration Manager voor besturingssysteemimplementatie

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat beveiligings- en privacy-informatie voor implementatie van besturingssystemen in System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a>Aanbevolen beveiligingsprocedures voor besturingssysteemimplementatie  
 Gebruik de volgende aanbevolen beveiligingsprocedures wanneer u implementeert besturingssystemen met Configuration Manager:  

-   **Toegangsbeheer implementeren om opstartbare media te beveiligen**  

     Als u opstartbare media maakt, dient u steeds een wachtwoord toe te wijzen om de media te helpen beveiligen. Zelfs met een wachtwoord worden alleen bestanden die gevoelige informatie bevatten, gecodeerd en kunnen alle bestanden overschreven worden.  

     Beheer de fysieke toegang tot de media door te voorkomen dat aanvallers cryptografische aanvallen kunnen gebruiken om het clientverificatiecertificaat te verkrijgen.  

     De inhoud wordt gehasht en moet worden gebruikt met het oorspronkelijke beleid. Zo wordt voorkomen dat een client inhoud of clientbeleid installeert waarmee is geknoeid.  De client zal de opstartbare media niet gebruiken als het hashen van de inhoud of de controle van de overeenkomst tussen de inhoud en het beleid mislukt. Alleen de inhoud wordt gehasht, niet het beleid. Het beleid wordt gecodeerd en beveiligd wanneer u een wachtwoord opgeeft. Dit maakt het moeilijker voor aanvallers om het beleid te wijzigen.  

-   **Gebruik een beveiligde locatie wanneer u media voor installatiekopieën van besturingssystemen maakt**  

     Onbevoegde gebruikers die toegang hebben tot de locatie, kunnen knoeien met de bestanden die u maakt en ze kunnen ook alle beschikbare schijfruimte innemen. Hierdoor mislukt het maken van de media.  

-   **Beveilig certificaatbestanden (.pfx) met een sterk wachtwoord en slaat u ze op het netwerk, het netwerkkanaal wanneer u ze in Configuration Manager importeert**  

     Wanneer u een wachtwoord vereist om het certificaat voor clientverificatie te importeren dat u gebruikt voor opstartbare media, helpt u hiermee het certificaat te beschermen tegen kwaadwillende personen.  

     Gebruik SMB-ondertekening of IPsec tussen de netwerklocatie en de siteserver om te voorkomen dat kwaadwillende personen knoeien met het certificaatbestand.  

-   **Als het clientcertificaat is geknoeid, Blokkeer het certificaat van de Configuration Manager en trekken als het een PKI-certificaat**  

     U moet beschikken over een clientverificatiecertificaat met een persoonlijke sleutel om een besturingssysteem te implementeren door gebruik te maken van opstartmedia en een PXE-opstartbewerking. Blokkeer het certificaat als ermee is geknoeid, in het knooppunt **Beveiliging** van de werkruimte **Beheer** in het knooppunt **Certificaten**.  

-   **Wanneer de SMS-Provider zich op een computer of andere computers dan de siteserver, Beveilig het communicatiekanaal omwille van opstartinstallatiekopieën**  

     De opstartinstallatiekopieën zijn kwetsbaar voor een aanval als er opstartkopieën worden gewijzigd en de SMS-provider wordt uitgevoerd op een andere server dan de siteserver. Beveilig het netwerkkanaal tussen deze computer door gebruik te maken van SMB-ondertekening of IPsec.  

-   **Schakel distributiepunten voor PXE-clientcommunicatie alleen op beveiligde netwerksegmenten**  

     Als een client een PXE-opstartaanvraag verstuurt, kunt u op geen enkele manier er zeker van zijn dat de aanvraag wordt uitgevoerd door een geldig distributiepunt met PXE-functionaliteit. Voor dit scenario gelden de volgende beveiligingsrisico's:  

    -   Een rogue distributiepunt dat antwoordt op PXE-aanvragen kan mogelijk een geknoeide installatiekopie aan clients bezorgen.  

    -   Een aanvaller zou een man-in-the-middle-aanval kunnen lanceren tegen het TFTP-protocol dat wordt gebruikt door PXE en schadelijke code verzendt samen met de bestanden van het besturingssysteem. Het is ook mogelijk dat er een rogue client wordt gemaakt om TFTP-aanvragen rechtstreeks naar het distributiepunt te maken.  

    -   Een aanvaller zou een schadelijke client kunnen gebruiken om een Denial of Service-aanval uit te voeren tegen het distributiepunt.  

     Gebruik verdediging in de diepte ter bescherming van de netwerksegmenten waar clients toegang zullen krijgen tot distributiepunten voor PXE-aanvragen.  

    > [!WARNING]  
    >  Door deze beveiligingsrisico's wordt het afgeraden om een distributiepunt in te schakelen voor PXE-communicatie wanneer het zich in een niet-vertrouwd netwerk, zoals een perimeternetwerk, bevindt.  

-   **Configureer distributiepunten met PXE-functionaliteit om te reageren op PXE-aanvragen alleen op gespecificeerde netwerkinterfaces**  

     Als u toestaat dat het distributiepunt antwoordt op PXE-aanvragen op alle netwerkinterfaces, is het mogelijk dat deze configuratie de PXE-service blootstelt aan niet-vertrouwde netwerken.  

-   **Wachtwoord vereisen voor PXE-opstartbewerking**  

     Wanneer u een wachtwoord voor PXE-opstartbewerking vereist, voegt deze configuratie een extra beveiligingsniveau toe aan het PXE-opstartproces te helpen beschermen tegen rogue clients die lid worden van de Configuration Manager-hiërarchie.  

-   **Neem geen line-of-business-toepassingen of software met gevoelige gegevens in een installatiekopie die wordt gebruikt voor PXE-opstartbewerkingen of multicast**  

     Er zijn inherente beveiligingsrisico's verbonden aan PXE-opstartbewerkingen en multicast; verminder daarom de kans dat rogue computers de installatiekopie van het besturingssysteem downloaden.  

-   **Neem geen line-of-business-toepassingen of software met gevoelige gegevens in softwarepakketten die zijn geïnstalleerd met behulp van takenreeksvariabelen**  

     Wanneer u softwarepakketten implementeert via takenreeksvariabelen, is het mogelijk dat er software wordt geïnstalleerd op computers en voor gebruikers die geen machtigingen hebben om die software te ontvangen.  

-   **Als u de gebruikersstatus migreert, Beveilig het netwerkkanaal tussen de client en het statusmigratiepunt via het SMB-ondertekening of IPsec**  

     Na de initiële verbinding via HTTP worden de statusmigratiegegevens overgedragen via SMB.  Een aanvaller kan deze gegevens mogelijk lezen en wijzigen als u het netwerkkanaal niet beveiligt.  

-   **Gebruik de meest recente versie van de gebruiker State Migration Tool (USMT) die ondersteuning biedt voor Configuration Manager**  

     De meest recente versie van USMT biedt beveiligingsverbeteringen en grotere controle voor wanneer u de gebruikersstatusgegevens migreert.  

-   **Verwijder mappen handmatig op statusmigratiepunt wanneer ze buiten werking worden gesteld**  

     Wanneer u een map van een statusmigratiepunt in de eigenschappen status van de Configuration Manager-console verwijdert, wordt de fysieke map niet verwijderd. U moet de netwerkshare handmatig verwijderen en de map wissen om de migratiegegevens over de gebruikersstatus te beschermen tegen openbaarmaking.  

-   **Configureer het verwijderingsbeleid Gebruikersstatus om onmiddellijk te verwijderen**  

     De gebruikersstatusgegevens worden onmiddellijk verwijderd als u het verwijderingsbeleid configureert op het statusmigratiepunt om gegevens te verwijderen die gemarkeerd zijn voor onmiddellijke verwijdering, en als een aanvaller erin slaagt om de gebruikersstatusgegevens op te halen vóór de geldige computer. Stel het interval **Verwijderen na** lang genoeg in om het succesvolle herstellen van gebruikersstatusgegevens te verifiëren.  

-   **Verwijder computerkoppelingen handmatig wanneer gegevens van de gebruikersstatusmigratie voltooid en geverifieerd is**  

     Configuration Manager verwijdert computerkoppelingen niet automatisch. Help bij het beschermen van de identiteit van de gebruikersstatusgegevens door de computerkoppelingen die niet langer zijn vereist, handmatig te verwijderen.  

-   **Handmatige back-up migratiegegevens van de gebruiker op het statusmigratiepunt**  

     Configuration Manager back-up bevat geen migratiegegevens van de gebruiker.  

-   **Houd er rekening mee BitLocker in te schakelen nadat het besturingssysteem is geïnstalleerd**  

     Als een computer BitLocker ondersteunt u het besturingssysteem zonder toezicht wilt installeren, moet u dit programma uitschakelen met een takenreeksstap. Configuration Manager schakelt BitLocker niet nadat het besturingssysteem is geïnstalleerd, zodat u BitLocker moet handmatig opnieuw inschakelen.  

-   **Implementeer toegangsbeheer om de voorbereide media te beveiligen**  

     Beheer de fysieke toegang tot de media door te voorkomen dat aanvallers cryptografische aanvallen kunnen gebruiken om het clientverificatiecertificaat en gevoelige gegevens te verkrijgen.  

-   **Implementeer toegangsbeheer om het installatiekopieproces referentiecomputer te beschermen**  

     Zorg ervoor dat de referentiecomputer die u gebruikt om de installatiekopieën van het besturingssysteem vast te leggen zich in een beveiligde omgeving bevindt met aangepast toegangsbeheer, zodat onverwachte of schadelijke software niet kan worden geïnstalleerd en onbedoeld opgenomen in de vastgelegde installatiekopie. Als u de installatiekopie vastlegt, dient u ervoor te zorgen dat de sharelocatie van het doelnetwerkbestand beveiligd is, zodat er niet met de installatiekopie kan worden geknoeid na het vastleggen ervan.  

-   **Installeer altijd de meest recente beveiligingsupdates op de referentiecomputer**  

     Wanneer de referentiecomputer actuele beveiligingsupdates heeft, helpt het om de kwetsbaarheid te verminderen voor nieuwe computers wanneer deze voor de eerste keer worden opgestart.  

-   **Als u besturingssystemen op een onbekende computer implementeren moet, dient toegangsbeheer om te voorkomen dat onbevoegde computers verbinding maken met het netwerk implementeren**  

     Hoewel het inrichten van onbekende computers een handige methode is om nieuwe computers op aanvraag te implementeren, is het mogelijk dat dit een aanvaller in staat stelt om op doeltreffende wijze een vertrouwde client op uw netwerk te worden. Beperk de fysieke toegang tot het netwerk en bewaak clients om onbevoegde computers te detecteren. Bovendien is het mogelijk dat alle gegevens van computers die op door PXE geïnitieerde besturingssysteemimplementaties reageren, worden vernietigd tijdens de implementatie van het besturingssysteem. Dit kan resulteren in een verlies van beschikbaarheid van systemen die onbedoeld opnieuw opgemaakt zijn.  

-   **Schakel versleuteling voor multicast-pakketten**  

     Voor elk implementatiepakket voor besturingssystemen hebt u de optie versleuteling inschakelen wanneer Configuration Manager het pakket via multicast overdraagt. Deze configuratie helpt om rogue computers te verhinderen om deel te nemen aan de multicast-sessie en het helpt bij het voorkomen dat aanvallers met de overdracht kunnen knoeien.  

-   **Bewaking voor onbevoegde distributiepunten met ingeschakelde multicast**  

     Als aanvallers toegang kunnen krijgen tot uw netwerk, kunnen ze rogue multicast-servers configureren om adresvervalsing te gebruiken voor de implementatie van besturingssystemen.  

-   **Wanneer u takenreeksen naar een netwerklocatie exporteert, Beveilig de locatie en Beveilig het netwerkkanaal**  

     Beperk wie toegang heeft tot de netwerkmap.  

     Gebruik SMB-ondertekening of IPsec tussen de netwerklocatie en de siteserver om te voorkomen dat kwaadwillende personen knoeien met de geëxporteerde takenreeks.  

-   **Beveilig het communicatiekanaal wanneer u een virtuele harde schijf naar Virtual Machine Manager uploadt.**  

     Gebruiken om te voorkomen dat knoeien met gegevens wanneer deze via het netwerk wordt overgedragen, Internet protocolbeveiliging (IPsec) of server message block (SMB) tussen de computer waarop de Configuration Manager-console en de computer die de Virtual Machine Manager.  

-   **Neem extra beveiligingsmaatregelen als u de Takenreeks Run As-Account gebruiken moet,**  

     Neem de volgende voorzorgsmaatregelen als u de takenreeks Run As-account gebruikt:  

    -   Gebruik een account met zo weinig mogelijk machtigingen.  

    -   Gebruik voor dit account geen netwerktoegangsaccount.  

    -   Maak nooit een domeinbeheerder van het account.  

     Daarnaast:  

    -   Configureer nooit zwervende profielen voor dit account. Wanneer de takenreeks wordt uitgevoerd, zal deze het zwervend profiel voor het account downloaden. Dit maakt het profiel kwetsbaar voor toegang op de lokale computer.  

    -   Beperk het bereik van het account. Maak bijvoorbeeld verschillende Run As-account-takenreeksen voor elke takenreeks, zodat, als er met één account is geknoeid, alleen de clientcomputers waarvoor dat account toegang heeft, worden getroffen. Als de opdrachtregel beheerderstoegang op de computer vereist, moet u overwegen om een lokaal beheerdersaccount te maken alleen voor de takenreeks Run As-account op alle computers die de takenreeks zullen uitvoeren. Wis dit account zodra het niet langer nodig is.  

-   **Beperk en bewaak de gebruikers met beheerdersrechten die de beveiligingsrol beheerder Besturingssysteemimplementatie krijgen**  

     Gebruikers met beheerdersrechten die de beveiligingsrol beheerder Besturingssysteemimplementatie krijgen kunnen zelfondertekende certificaten die vervolgens kunnen worden gebruikt om een client te imiteren en om clientbeleid van Configuration Manager maken.  

### <a name="security-issues-for-operating-system-deployment"></a>Beveiligingsproblemen voor besturingssysteemimplementatie  
 Hoewel besturingssysteemimplementatie een handige manier kan zijn om de meest beveiligde besturingssystemen en configuraties voor computers in uw netwerk te implementeren, zijn er toch volgende beveiligingsrisico's aan verbonden:  

-   Openbaarmaking van informatie en Denial of Service  

     Als een aanvaller controle over uw Configuration Manager-infrastructuur krijgen kan, kan deze eender welke takenreeks, waaronder het formatteren van de harde schijven van alle clientcomputers uitvoeren. Takenreeksen kunnen worden geconfigureerd om gevoelige informatie te bevatten, zoals accounts die machtigingen hebben om lid te worden van de domein- en volumelicentiesleutels.  

-   Imitatie en verhoging van bevoegdheden  

     Takenreeksen kunnen een computer toevoegen aan een domein, wat een rogue computer mogelijk geverifieerde netwerktoegang kan geven. Een andere belangrijke veiligheidsoverweging voor de implementatie van besturingssystemen is het beschermen van het clientverificatiecertificaat dat wordt gebruikt voor opstartbare takenreeksmedia en voor implementatie van PXE-opstartbewerkingen. Door het vastleggen van een clientverificatiecertificaat geeft u een aanvaller een kans om de persoonlijke sleutel in het certificaat te verkrijgen. Hiermee kan deze een geldige client op het netwerk imiteren.   

     Als een aanvaller het clientcertificaat dat voor opstartbare takenreeksmedia en voor implementatie van PXE-opstartbewerking wordt gebruikt krijgt, kan dit certificaat worden gebruikt om te imiteren een geldige client voor Configuration Manager. In dit scenario kan de malafide computer beleid downloaden dat gevoelige gegevens kan bevatten.  

     Als clients gebruik maken van het netwerktoegangsaccount om toegang te krijgen tot op het statusmigratiepunt opgeslagen gegevens, delen deze clients feitelijk dezelfde identiteit en hebben toegang tot statusmigratiegegevens van een andere client die het netwerktoegangsaccount gebruikt. De gegevens zijn versleuteld, zodat alleen de oorspronkelijke client deze kan lezen, maar met deze gegevens kan worden geknoeid en deze kunnen worden verwijderd.  

-   Clientverificatie naar het statusmigratiepunt wordt bereikt door middel van een Configuration Manager-token dat is uitgegeven door het beheerpunt.  

     Bovendien Configuration Manager niet beperken of beheren van de hoeveelheid gegevens die zijn opgeslagen op het statusmigratiepunt en een kwaadwillende persoon kan de beschikbare schijfruimte vol en een DOS kunnen veroorzaken.  

-   Als u verzamelingsvariabelen gebruikt, kunnen lokale beheerders potentieel gevoelige informatie lezen.  

     Hoewel verzamelingsvariabelen een flexibele methode bieden om besturingssystemen te implementeren, kan dit openbaarmaking van informatie tot gevolg hebben.  

##  <a name="BKMK_Privacy_HardwareInventory"></a>Privacy-informatie voor implementatie van besturingssysteem  
 Naast het implementeren van besturingssystemen op computers zonder besturingssysteem, kan Configuration Manager worden gebruikt voor het migreren van bestanden en instellingen van gebruikers van de ene computer naar een andere. De beheerder configureert welke informatie moet worden overgedragen, waaronder bestanden met persoonsgegevens, configuratie-instellingen en cookies van de browser.  

 De informatie wordt op een statusmigratiepunt opgeslagen en wordt tijdens de overdracht en opslag versleuteld. De informatie mag worden verkregen door de nieuwe computer die aan de statusinformatie is gekoppeld. Als de nieuwe computer de sleutel verliest voor het verkrijgen van de informatie, heeft een Configuration Manager-beheerder met het recht Herstelgegevens weergeven voor exemplaarobjecten voor computerkoppelingen toegang tot de informatie en kan deze aan een nieuwe computer koppelen. Wanneer de statusinformatie wordt hersteld op de nieuwe computer, worden de gegevens standaard na één dag verwijderd. U kunt configureren wanneer het statusmigratiepunt de voor verwijdering aangemerkte gegevens verwijdert. De statusmigratiegegevens worden niet in de sitedatabase opgeslagen en evenmin naar Microsoft verzonden.  

 Als u opstartmedia gebruikt voor het implementeren van besturingssystemen, dient u altijd de standaardoptie te gebruiken om de opstartmedia met een wachtwoord te beveiligen. Het wachtwoord versleutelt eventuele in de takenreeks opgeslagen variabelen, maar eventuele niet in een variabele opgeslagen informatie is mogelijk kwetsbaar voor openbaarmaking.  

 Tijdens het implementatieproces kan de implementatie van besturingssystemen gebruik maken van takenreeksen om veel verschillende taken uit te voeren, waaronder het installeren van toepassingen en software-updates. Wanneer u takenreeksen configureert, dient u zich bewust te zijn van de gevolgen van het installeren van software ten aanzien van privacy.  

 Als u een virtuele harde schijf naar Virtual Machine Manager uploadt zonder met behulp van Sysprep de installatiekopie op te schonen, kan de geüploade virtuele harde schijf persoonsgegevens bevatten van de originele installatiekopie.  

 Configuration Manager wordt de implementatie van besturingssysteem niet geïmplementeerd standaard en vereist verschillende configuratiestappen voordat u gebruikersstatusgegevens verzamelt of maken van takenreeksen of opstartinstallatiekopieën.  

 Bedenk wat uw privacyvereisten zijn voordat u de implementatie van besturingssystemen configureert.  

