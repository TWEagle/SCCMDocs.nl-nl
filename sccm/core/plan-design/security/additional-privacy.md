---
title: Privacyverklaring voor System Center Configuration Manager - aanvullende informatie
description: Meer informatie over hoe Microsoft worden verzameld en gebruikt gegevens uit een System Center Configuration Manager-implementatie.
ms.custom: na
ms.date: 10/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fcc921f-085f-4b0b-9c53-1e0707211076
caps.latest.revision: "5"
caps.handback.revision: "0"
author: aaroncz
ms.author: aaroncz
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
ms.openlocfilehash: 3cf73a424d9e8ad9e339b24d89a3a2afac0165b7
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="additional-information-about-privacy-for-system-center-configuration-manager"></a>Meer informatie over privacy voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="updates-and-servicing"></a>Updates en onderhoud
System Center Configuration Manager introduceert een nieuw updatemodel waarmee u uw Configuration Manager-implementatie up-to-date met de meest recente updates en functies. Wanneer geïnstalleerd, wordt een nieuwe sitesysteemrol die het serviceverbindingspunt wordt gehost op een siteserver die een beheerder kiest is aangeroepen door deze functie toegevoegd. Zie de sectie met gebruik van gegevens in dit artikel voor meer informatie over de verzamelde gegevens en hoe deze wordt gebruikt.


## <a name="usage-data"></a>Gebruiksgegevens
System Center Configuration Manager verzamelt diagnostische gegevens en gebruiksgegevens over zichzelf die Microsoft gebruikt voor het verbeteren van de installatie-ervaring, kwaliteit en beveiliging van toekomstige releases.
Diagnostische gegevens en gebruiksgegevens is ingeschakeld voor elke System Center Configuration Manager-hiërarchie. Bestaat uit SQL Server-query's die wekelijks worden uitgevoerd op elke primaire site en op de centrale beheersite. Als de hiërarchie een centrale beheersite gebruikt, worden de gegevens vervolgens vanaf de primaire sites gerepliceerd naar die site. Op het hoogste niveau van uw hiërarchie, het service connection point deze informatie wordt verzonden wanneer op updates wordt gecontroleerd. Als het serviceverbindingspunt zich in de offlinemodus bevindt, wordt de informatie overgedragen met het hulpprogramma voor serviceverbindingen.

Configuration Manager verzamelt gegevens uit SQL server-database van de site alleen en verzamelt geen gegevens rechtstreeks bij clients of siteservers.

Beheerders kunnen het niveau wijzigen van gegevens die worden verzameld door te gaan naar de **gebruiksgegevens** gedeelte van de Configuration Manager-console.

Zie voor meer informatie de 'Meer informatie' artikelen over Gebruiksgegevensniveaus en instellingen in de [diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626566) artikel.


## <a name="customer-experience-improvement-program"></a>Programma voor verbetering van de gebruikerservaring
Customer Experience Improvement Program (CEIP) verzamelt basisinformatie van de Configuration Manager-console over uw hardwareconfiguratie en hoe u onze software en services gebruiken om trends en gebruikspatronen te identificeren. Programma voor Kwaliteitsverbetering verzamelt ook het type en aantal fouten die u tegenkomt, software en hardwareprestaties en de snelheid van services. Er worden niet uw naam, adres of andere contactgegevens verzameld. Er worden geen gegevens van het Programma voor verbetering van de gebruikerservaring verzameld van clientcomputers.

We gebruiken deze gegevens om de kwaliteit, betrouwbaarheid en prestaties van de software en services van Microsoft te verbeteren.

Zie voor meer informatie over de informatie die is verzameld, verwerkt of verzonden door CEIP, de [CEIP-privacyverklaring](http://go.microsoft.com/fwlink/?LinkID=525211).

## <a name="operations-management-suite-connector"></a>Operations Management Suite-Connector
De Microsoft Operations Management Suite-Connector wordt gesynchroniseerd gegevens, zoals verzamelingen, van System Center Configuration Manager en Microsoft Operations Management Suite. De Microsoft Azure-abonnements-ID en een geheime sleutel worden opgeslagen in de Configuration Manager-database wanneer een beheerder de functie configureert. Zowel de Azure Active Directory-clientgeheim en de Microsoft Operations Management Suite-werkruimte gedeelde sleutel worden opgeslagen in de lokale System Center Configuration Manager-database. Alle communicatie tussen System Center Configuration Manager en Microsoft Operations Management Suite HTTPS gebruiken. Geen aanvullende informatie over de verzamelingen wordt geleverd aan Microsoft buiten willekeurige telemetrische gegevens. Zie voor meer informatie over de gegevens die Microsoft Operations Management Suite verzamelt [logboek analytics](http://go.microsoft.com/fwlink/?LinkId=823545).

## <a name="asset-intelligence"></a>Asset Intelligence
Asset Intelligence kunnen IT-beheerders definiëren, traceren en proactief beheren conformiteit met configuratiestandaarden. Meten van en rapporteren over de implementatie en het gebruik van zowel fysieke als virtuele toepassingen helpt organisaties om betere zakelijke beslissingen te nemen met betrekking tot softwarelicenties en het behouden van compatibiliteit met licentieovereenkomsten. Na het verzamelen van gegevens over het gebruik van Configuration Manager-clients, kunnen beheerders verschillende functies gebruiken om weer te geven van de gegevens, met inbegrip van verzamelingen, query's en rapportage.

Een catalogus van gekende software wordt gedownload tijdens elke synchronisatie van Microsoft. IT-beheerders kunnen kiezen Microsoft informatie over niet-gecategoriseerde softwaretitels die zijn gedetecteerd binnen hun organisatie kunnen worden opgezocht en toegevoegd aan de catalogus te verzenden. Voorafgaand aan het uploaden van deze informatie toont een dialoogvenster gegevens die u wilt worden geüpload. Geüploade gegevens kunnen niet worden ingetrokken. Asset Intelligence verzendt geen informatie over gebruikers en computers of licentiegebruik naar Microsoft.

Nadat een softwaretitel is geüpload, Microsoft-onderzoekers identificeren categoriseren en maakt deze kennis beschikbaar voor alle klanten die gebruikmaken van deze functie en andere gebruikers van de catalogus. Een geüploade softwaretitel wordt openbaar. De toepassing en haar categorisatie deel worden van de catalogus en kunnen vervolgens worden gedownload naar andere gebruikers van de catalogus. Neem kennis van de privacyverklaring van uw organisatie vóór u Asset Intelligence gegevensverzameling configureert en beslist of informatie dient verzonden te worden naar Microsoft.

Asset Intelligence is in System Center Configuration Manager niet standaard ingeschakeld. Het uploaden van niet-gecategoriseerde titels gebeurt nooit automatisch en het systeem is niet ontworpen om deze taak te automatiseren. U moet het uploaden van elke softwaretitel handmatig selecteren en goedkeuren.

## <a name="endpoint-protection"></a>Endpoint Protection
Microsoft-Cloudservice beveiliging was voorheen bekend als Microsoft Active Protection Service of MAPS.
De van toepassing zijnde producten zijn System Center Endpoint Protection en de Endpoint Protection-functie van System Center Configuration Manager (voor het beheren van System Center Endpoint Protection en Windows Defender voor Windows 10). Deze functie is niet geïmplementeerd voor System Center Endpoint Protection voor Linux of System Center Endpoint Protection voor Mac.

De Cloudservice van Microsoft voor beveiliging antimalware-community is een vrijwillig wereldwijde onlinecommunity waar ook gebruikers van de System Center Endpoint Protection. Wanneer u een Cloudservice van Microsoft voor beveiliging koppelt, verzonden System Center Endpoint Protection automatisch gegevens naar Microsoft. Microsoft gebruikt de informatie om te bepalen van de software moet worden gecontroleerd op potentiële dreigingen en de effectiviteit van System Center Endpoint Protection verbeteren. Deze community helpt bij de verspreiding van nieuwe schadelijke software-infecties te stoppen. Als een Cloudservice van Microsoft voor beveiliging-rapport details over malware of mogelijk ongewenste software die mogelijk is de Endpoint Protection-client kunnen verwijderen bevat, downloadt Microsoft-Cloudservice Protection de meest recente handtekening om deze op te lossen. Microsoft-Cloudservice beveiliging vindt ook 'valse positieven' (waarbij iets oorspronkelijk is geïdentificeerd als malware blijkt niet) en corrigeren.

Microsoft Cloud Protection Service-rapporten bevatten informatie over malwarebestanden, zoals bestandsnamen, cryptografische hash, leverancier, grootte en datumstempels. Cloudservice van Microsoft voor beveiliging kan bovendien de volledige URL's om aan te geven van de oorsprong van het bestand verzamelen. Deze URL's wellicht van tijd tot tijd persoonlijke gegevens, zoals zoektermen of gegevens die in formulieren is ingevoerd. Rapporten bevatten mogelijk ook de acties die u hebt ondernomen wanneer Endpoint Protection op de hoogte u ongewenste software. Microsoft Cloud Protection Service-rapporten bevatten deze informatie om te meten hoe effectief Endpoint Protection kan detecteren en verwijder schadelijke software en mogelijk ongewenste software Microsoft en om te identificeren van nieuwe schadelijke software.

Als u een standaard of Geavanceerd lidmaatschap hebt, kunt u Microsoft-Cloudservice beveiliging koppelen. Rapporten van basisleden zijn de gegevens die hierboven is beschreven. Geavanceerde lid rapporten uitgebreider en bevatten mogelijk aanvullende informatie over de software die door Endpoint Protection wordt gedetecteerd, zoals de locatie van de software, bestandsnamen, hoe de software werkt en hoe deze uw computer heeft beïnvloed. Ontdek nieuwe dreigingen sneller deze rapporten en rapporten van andere Endpoint Protection-gebruikers die deel uitmaken van Microsoft-Cloudservice beveiliging help Microsoft-onderzoekers. Definities van schadelijke software vervolgens worden gemaakt voor programma's die voldoen aan de analysecriteria, en de bijgewerkte definities worden beschikbaar gesteld voor alle gebruikers via Microsoft Update.

Om te detecteren en oplossen van bepaalde soorten malware-infecties, verzendt het product regelmatig Microsoft Cloud Protection Service informatie over de beveiligingsstatus van uw PC. Deze informatie omvat informatie over de beveiligingsinstellingen van uw PC en logboekbestanden die worden beschreven de stuurprogramma's en andere software laden terwijl uw PC opstart.
Een getal dat een unieke identificatie van uw PC ook wordt verzonden. Cloudservice van Microsoft voor beveiliging kan ook de IP-adressen die de malwarebestanden verbinding met maken verzamelen.

Rapporten van de Cloudservice van Microsoft voor beveiliging worden gebruikt om Microsoft-software en services te verbeteren. De rapporten kunnen ook worden gebruikt voor statistische of andere testdoeleinden of analysedoeleinden, en voor het genereren van definities. Alleen Microsoft-werknemers, contractanten, partners en leveranciers die de rapporten nodig hebben voor zakelijke hebben toegang tot deze.

Microsoft-Cloudservice beveiliging verzameld niet opzettelijk persoonlijke gegevens. Voor zover dit Microsoft-Cloudservice beveiliging geen persoonlijke gegevens verzamelt, gebruikt Microsoft de gegevens niet naar u te identificeren of contact met u opnemen.

Aanvullende informatie over de verzamelde gegevens vindt u in de productdocumentatie op [Endpoint Protection in System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=823547).

## <a name="site-hierarchy--geographical-view-with-bing-maps"></a>Sitehiërarchie – geografische weergave met Bing kaarten
Sitehiërarchie - geografische weergave kunt u gebruiken van kaarten die Microsoft Bing Maps biedt om uw fysieke Servertopologie van Configuration Manager weer te geven. Om deze functie inschakelt, locatie-informatie die u verstrekt verzonden van uw server met de Bing Maps-webservice.

Microsoft gebruikt de informatie voor de werking van Microsoft Bing Maps en voor de verbetering van de werking hiervan en voor andere Microsoft-sites en -diensten. Zie voor meer informatie de [privacyverklaring van Microsoft](http://go.microsoft.com/fwlink/?LinkId=823548).
U kunt kiezen om de geografische weergave voor de sitehiërarchie niet te gebruiken. De diagramweergave hiërarchie kunt u de hiërarchie zien en gebruikt de Bing Maps-service niet.

## <a name="microsoft-intune-subscription"></a>Microsoft Intune-abonnement
Klanten die een abonnement op Microsoft Intune hebt aangeschaft kunnen Configuration Manager gebruiken voor het beheren van hun mobiele apparaten die via Microsoft Intune verbonden zijn. [Privacyverklaring van Microsoft Online Services](http://go.microsoft.com/fwlink/?LinkId=262214) geldt voor de Microsoft online services, waaronder Microsoft Intune. Als klanten ook een Microsoft Intune-abonnement hebt, de [privacyverklaring van Microsoft Online Services](http://go.microsoft.com/fwlink/?LinkId=262214) moet worden gelezen in combinatie met deze privacyverklaring.

Alle communicatie met Microsoft Intune gebruiken HTTPS. De Microsoft Intune-abonnement configureren en om te downloaden van het Certificate Signing Request (CSR) die nodig is voor het configureren van iOS-ondersteuning, een beheerder moet zich aanmelden bij Microsoft Intune met werkaccount en wachtwoord. Deze referenties worden niet opgeslagen in Configuration Manager. Alle andere communicaties met Microsoft Intune worden geverifieerd door gebruikmaking van PKI-certificaten die door Microsoft Intune wordt automatisch gegenereerd.

Om apparaten te beheren die zijn verbonden met Microsoft Intune, wordt bepaalde informatie verzonden naar en ontvangen van Microsoft Intune. Deze informatie bevat de User Principal Name (UPN) van alle gebruikers die zijn toegewezen aan de dienst en Inventarisinformatie voor de apparaten die worden beheerd door Microsoft Intune. Metagegevens, zoals de toepassingsnaam, uitgever en versie worden, voor inhoud die is toegekend aan Manage.Microsoft.com-distributiepunten, verzonden naar Microsoft Intune. De werkelijke binaire inhoud die toegewezen aan een Manage.Microsoft.com-distributiepunt is versleuteld vóór deze geüpload wordt naar Microsoft Intune.

Deze functie is niet standaard geconfigureerd. Beheerders beheren de inhoud die overgebracht wordt naar het Manage.Microsoft.com-distributiepunt en de gebruikers die zijn toegewezen aan de service. De functie kan steeds worden verwijderd.
