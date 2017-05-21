---
title: Privacyverklaring voor System Center Configuration Manager - aanvullende informatie | Microsoft-documenten
description: Meer informatie over hoe Microsoft verzamelt en gegevens uit een System Center Configuration Manager-implementatie gebruikt.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fcc921f-085f-4b0b-9c53-1e0707211076
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translation.priority.ht:
- cs-cz
- de-de
- en-gb
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 47d473b3884c3cd2ff7516629a7c32d4e52ac39b
ms.openlocfilehash: ef7b3656f9b4a31e07227aa4e864448d0dd1fcdc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="additional-information-about-privacy-for-system-center-configuration-manager"></a>Aanvullende informatie over de privacy voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="updates-and-servicing"></a>Updates en onderhoud
System Center Configuration Manager introduceert een nieuwe updatemodel waarmee de Configuration Manager-implementatie houden met de meest recente updates en functies. Wanneer is geïnstalleerd, voegt deze functie een nieuwe sitesysteemrol die de service connection point is aangeroepen op een siteserver die een beheerder kiest. Zie de sectie voor gebruik van gegevens in dit artikel voor meer informatie over de verzamelde gegevens en hoe deze worden gebruikt.


## <a name="usage-data"></a>Gebruiksgegevens
System Center Configuration Manager verzamelt informatie over diagnostische en gebruiksgegevens over zelf, dat gebruikmaakt van Microsoft voor het verbeteren van de installatie-ervaring, kwaliteit en beveiliging van toekomstige releases.
Diagnostische en gebruiksgegevens is ingeschakeld voor elke System Center Configuration Manager-hiërarchie. Het bestaat uit SQL Server-query's die worden uitgevoerd op een wekelijks uit te voeren op elke primaire site en op de centrale beheersite. Als de hiërarchie een centrale beheersite gebruikt, worden de gegevens vervolgens vanaf de primaire sites gerepliceerd naar die site. De service connection point verzendt deze gegevens op de site op het hoogste niveau van uw hiërarchie wanneer er wordt gecontroleerd op updates. Als het serviceverbindingspunt zich in de offlinemodus bevindt, wordt de informatie overgedragen met het hulpprogramma voor serviceverbindingen.

Configuration Manager verzamelt gegevens van SQL server-database van de site alleen en verzamelt geen gegevens rechtstreeks van clients of siteservers.

Beheerders kunnen wijzigen van het niveau van de gegevens die worden verzameld door te gaan naar de **gebruiksgegevens** sectie van de Configuration Manager-console.

Zie voor meer informatie de "Meer informatie" artikelen over gebruik hebben en instellingen in de [diagnostische en gebruiksgegevens voor System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626566) artikel.


## <a name="customer-experience-improvement-program"></a>Programma voor verbetering van de gebruikerservaring
De klant van de gebruikerservaring programma kwaliteitsverbetering (CEIP) worden standaardgegevens verzameld van de Configuration Manager-console over uw hardwareconfiguratie en hoe u onze software en services gebruiken om trends en gebruikspatronen identificeren. Programma voor Kwaliteitsverbetering verzamelt tevens informatie over het type en aantal fouten dat u tegenkomt, software- en hardwareprestaties en de snelheid van services. Er worden geen uw naam, adres of andere contactgegevens verzameld. Er worden geen gegevens van het Programma voor verbetering van de gebruikerservaring verzameld van clientcomputers.

We gebruiken deze gegevens om de kwaliteit, betrouwbaarheid en prestaties van de software en services van Microsoft te verbeteren.

Zie voor meer informatie over de informatie die is verzameld, verwerkt of verzonden door CEIP, de [CEIP privacyverklaring](http://go.microsoft.com/fwlink/?LinkID=525211).

## <a name="operations-management-suite-connector"></a>Connector Operations Management-Suite
De Connector van de Microsoft Operations Management-pakket wordt gesynchroniseerd gegevens, zoals verzamelingen, van System Center Configuration Manager naar Microsoft Operations Management-pakket. De Microsoft Azure-abonnements-ID en een geheime sleutel zijn opgeslagen in de Configuration Manager-database wanneer een beheerder de functie configureert. De geheime sleutel die Azure Active Directory-client en de Microsoft Operations Management Suite werkruimte gedeelde sleutel worden in de lokale System Center Configuration Manager-database opgeslagen. Alle communicatie tussen de System Center Configuration Manager en Microsoft Operations Management Suite gebruik van HTTPS. Geen aanvullende informatie over de verzamelingen is buiten willekeurige telemetriegegevens aan Microsoft verstrekt. Zie voor meer informatie over de gegevens die Microsoft Operations Management Suite verzamelt [logboek analytics](http://go.microsoft.com/fwlink/?LinkId=823545).

## <a name="asset-intelligence"></a>Asset Intelligence
Asset Intelligence kunnen IT-beheerders definiëren, traceren en proactief beheren conformiteit met configuratiestandaarden. Meten van en rapporteren over de implementatie en het gebruik van zowel fysieke als virtuele toepassingen helpt organisaties om betere zakelijke beslissingen te nemen met betrekking tot softwarelicenties en het behouden van compatibiliteit met licentieovereenkomsten. Na het verzamelen van gebruiksgegevens van Configuration Manager-clients kunnen beheerders verschillende functies gebruiken om de gegevens, met inbegrip van verzamelingen, query's en rapportering weer te geven.

Tijdens elke synchronisatie een catalogus van gekende software gedownload van Microsoft. IT-beheerders kunnen kiezen om Microsoft informatie over niet gecategoriseerde softwaretitels die zijn gedetecteerd binnen hun organisatie te zoeken en toegevoegd aan de catalogus te verzenden. Voorafgaand aan het uploaden van deze informatie toont een dialoogvenster gegevens die zullen worden geüpload. Geüploade gegevens kunnen niet worden ingetrokken. Asset Intelligence verzendt geen informatie over gebruikers en computers of licentiegebruik naar Microsoft.

Nadat een softwaretitel is geüpload, Microsoft-onderzoekers identificeren categoriseren en maken dan deze kennis beschikbaar voor alle klanten die gebruikmaken van deze functie en andere gebruikers van de catalogus. Een geüploade softwaretitel wordt openbaar. De toepassing en haar categorisatie deel worden van de catalogus en kunnen vervolgens worden gedownload naar andere gebruikers van de catalogus. Neem kennis van de privacyverklaring van uw organisatie vóór u Asset Intelligence gegevensverzameling configureert en beslist of informatie dient verzonden te worden naar Microsoft.

Asset Intelligence is in System Center Configuration Manager niet standaard ingeschakeld. Het uploaden van niet-gecategoriseerde titels gebeurt nooit automatisch en het systeem is niet ontworpen om deze taak te automatiseren. U moet het uploaden van elke softwaretitel handmatig selecteren en goedkeuren.

## <a name="endpoint-protection"></a>Endpoint Protection
Microsoft-Cloudservice beveiliging was voorheen bekend als Microsoft Active Protection Service of -kaarten.
De producten zijn System Center Endpoint Protection en de Endpoint Protection-functie van System Center Configuration Manager (System Center Endpoint Protection en Windows Defender voor Windows 10). Deze functie is niet geïmplementeerd voor System Center Endpoint Protection voor Linux of System Center Endpoint Protection voor Mac.

De Microsoft-Cloudservice beveiliging antimalware-community is een vrijwillige wereldwijde onlinecommunity waar ook gebruikers van System Center Endpoint Protection. Wanneer u Microsoft Cloud Protection Service toevoegt, verzonden System Center Endpoint Protection automatisch gegevens naar Microsoft. Microsoft gebruikt de informatie voor het bepalen van de software moet worden gecontroleerd op potentiële dreigingen en de effectiviteit van System Center Endpoint Protection verbeteren. Deze community helpt bij het tegengaan van de verspreiding van nieuwe schadelijke software. Als een Cloudservice van Microsoft voor beveiliging rapport details over malware of potentieel ongewenste software die de Endpoint Protection client zou kunnen bevat verwijderen, downloadt Microsoft Cloud Protection Service de meest recente handtekening los deze problemen. Microsoft-Cloudservice beveiliging vindt ook 'valse positieven' (waarbij iets in eerste instantie als schadelijke software wordt aangemerkt blijkt niet) en corrigeren.

Microsoft-Cloudservice beveiliging rapporten bevatten informatie over mogelijke malware-bestanden, zoals bestandsnamen, cryptografische hash, leverancier, grootte en datumstempels. Bovendien kunnen door Microsoft Cloud beveiligingsservice volledige URL's voor het aangeven van de oorsprong van het bestand verzameld. Deze URL's wellicht van tijd tot tijd persoonlijke gegevens, zoals zoektermen of gegevens die in formulieren is ingevoerd. Rapporten kunnen ook acties bevatten die u hebt ondernomen wanneer Endpoint Protection u ongewenste software hoogte. Microsoft-Cloudservice beveiliging rapporten bevatten deze informatie helpt Microsoft bij het efficiënt Endpoint Protection kan detecteren en verwijderen schadelijke software en mogelijk ongewenste software te meten en om te identificeren van nieuwe schadelijke software.

U kunt deelnemen aan Microsoft Cloud Protection Service als u een basis- of geavanceerde lidmaatschap. Rapporten hebben de eerder beschreven informatie. Uitgebreid lidmaatschap zijn de rapporten uitgebreider en bevatten mogelijk aanvullende informatie over de software die door Endpoint Protection wordt gedetecteerd, zoals de locatie van de software, bestandsnamen, hoe de software werkt en hoe deze uw computer heeft beïnvloed. Deze rapporten en rapporten van andere Endpoint Protection-gebruikers die deel uitmaken van Microsoft-Cloudservice beveiliging help Microsoft-onderzoekers detecteren nieuwe dreigingen sneller opsporen. Vervolgens worden er definities van schadelijke software gemaakt voor programma's die voldoen aan de analysecriteria, en de bijgewerkte definities beschikbaar zijn gesteld aan alle gebruikers via Microsoft Update.

Om te helpen detecteren en bepaalde soorten malware-infecties te herstellen, zendt het product regelmatig Microsoft Cloud Protection Service informatie over de veiligheidstoestand van uw PC. Deze informatie omvat informatie over de beveiligingsinstellingen van uw PC en logbestanden die de stuurprogramma's te beschrijven en andere software laden terwijl uw PC opstart.
Een getal dat uw PC op unieke wijze identificeert wordt ook gezonden. Microsoft-Cloudservice beveiliging kunnen ook de IP-adressen die de potentiële malware bestanden verbinding met maken verzamelen.

Microsoft-Cloudservice beveiliging rapporten worden gebruikt om Microsoft-software en services te verbeteren. De rapporten kunnen ook worden gebruikt voor statistische of andere testdoeleinden of analysedoeleinden, en voor het genereren van definities. Alleen Microsoft-werknemers, aannemers, partners en leveranciers die de rapporten nodig hebben voor zakelijke hebben toegang tot deze.

Microsoft-Cloudservice beveiliging verzameld niet met opzet persoonlijke gegevens. Voor zover dit Microsoft-Cloudservice beveiliging persoonlijke gegevens worden verzameld, gebruikt Microsoft de gegevens niet geïdentificeerd of contact met u opnemen.

Aanvullende informatie over de verzamelde gegevens vindt u in de productdocumentatie op [Endpoint Protection in System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=823547).

## <a name="site-hierarchy--geographical-view-with-bing-maps"></a>Sitehiërarchie – geografische weergave met Bing-kaarten
Sitehiërarchie - geografische weergave kunt u gebruiken van kaarten waarmee Microsoft Bing-kaarten om weer te geven van uw fysieke Servertopologie van Configuration Manager. Om deze functie inschakelt, locatie-informatie die u biedt verzonden van uw server naar de Bing Maps-webservice.

Microsoft gebruikt de informatie voor de werking van Microsoft Bing Maps en voor de verbetering van de werking hiervan en voor andere Microsoft-sites en -diensten. Zie voor meer informatie de [privacyverklaring van Microsoft](http://go.microsoft.com/fwlink/?LinkId=823548).
U kunt kiezen om de geografische weergave voor de sitehiërarchie niet te gebruiken. De diagramweergave hiërarchie kunt u de hiërarchie zien en gebruikt de Bing Maps-service niet.

## <a name="microsoft-intune-subscription"></a>Microsoft Intune-abonnement
Klanten die een abonnement op Microsoft Intune hebt gekocht kunnen Configuration Manager gebruiken voor het beheren van hun mobiele apparaten die via Microsoft Intune verbonden zijn. [Privacyverklaring van Microsoft Online Services](http://go.microsoft.com/fwlink/?LinkId=262214) is van toepassing op de Microsoft online services, waaronder Microsoft Intune. Als klanten ook een Microsoft Intune-abonnement, het [privacyverklaring van Microsoft Online Services](http://go.microsoft.com/fwlink/?LinkId=262214) moet worden gelezen in combinatie met deze privacyverklaring.

Alle communicatie met Microsoft Intune gebruikt HTTPS. De Microsoft Intune-abonnement configureren en te downloaden van het Certificate Signing Request (CSR) die nodig is voor het configureren van iOS-ondersteuning, een beheerder moet zich aanmelden bij Microsoft Intune met behulp van een organisatie-account en wachtwoord. Deze referenties worden niet opgeslagen in Configuration Manager. Alle andere communicatie met Microsoft Intune wordt geverifieerd met behulp van PKI-certificaten die door Microsoft Intune wordt automatisch gegenereerd.

Voor het beheren van apparaten die zijn verbonden met Microsoft Intune wordt bepaalde informatie verzonden naar en ontvangen van Microsoft Intune. Deze informatie bevat de User Principal Name (UPN) van alle gebruikers die zijn toegewezen aan de dienst en Inventarisinformatie voor de apparaten die worden beheerd door Microsoft Intune. Metagegevens, wordt zoals toepassingsnaam, uitgever en versie, voor inhoud die toegekend is aan Manage.Microsoft.com distributiepunten verzonden naar Microsoft Intune. De werkelijke binaire inhoud die toegewezen aan een Manage.Microsoft.com distributiepunt is versleuteld vóór deze geüpload wordt naar Microsoft Intune.

Deze functie is niet standaard geconfigureerd. Beheerders beheren de inhoud die overgebracht wordt naar het Manage.Microsoft.com-distributiepunt en de gebruikers die zijn toegewezen aan de service. De functie kan steeds worden verwijderd.

