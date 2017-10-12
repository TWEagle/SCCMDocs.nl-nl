---
title: Veelgestelde vragen over de Endpoint Protection-client | Microsoft Docs
description: Vind antwoorden op veelgestelde vragen over Windows Defender- en Endpoint Protection.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3aaa9d2-a40e-42b1-ad75-5a115351729e
caps.latest.revision: "15"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: b88bc5f734b85527b81e5848deb0617db4c8dfbc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="endpoint-protection-client-frequently-asked-questions"></a>Veelgestelde vragen over de Endpoint Protection-client

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Deze veelgestelde vragen zijn voor computergebruikers waarvan de IT-beheerder Windows Defender of Endpoint Protection heeft geïmplementeerd op de beheerde computer. De hier weergegeven inhoud mogelijk niet van toepassing op andere antimalwaresoftware. Microsoft System Center Endpoint Protection beheert Windows Defender voor Windows 10. Het kan ook implementeren en beheren van de Endpoint Protection-client op computers voordat u Windows 10. In dit artikel wordt Windows Defender beschreven, maar de informatie is ook van toepassing op Endpoint Protection.  

-   [Waarom heb ik software tegen virussen en spyware nodig?](#why-do-i-need-antivirus-and-antispyware-software)  
-   [Hoe kan ik zien of mijn computer is geïnfecteerd met schadelijke software?](#how-can-i-tell-if-my-computer-is-infected-with-malicious-software)
-   [Hoe vind ik de versie van Windows Defender?](#how-can-i-find-the-version-of-windows-defender)
-   [Wat moet ik doen als schadelijke software op mijn computer wordt gedetecteerd door Windows Defender of Endpoint Protection?](#what-should-i-do-if-windows-defender-or-endpoint-protection-detects-software-on-my-computer)  
-   [Wat is er een virus?](#what-is-a-virus)  
-   [Wat is spyware?](#what-is-spyware)  
-   [Wat is het verschil tussen virussen, spyware en andere mogelijk schadelijke software?](#hat-s-the-difference-between-viruses-spyware-and-other-potentially-harmful-software)  
-   [Waar komen virussen, spyware en andere mogelijk ongewenste software vandaan?](#where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from)  
-   [Kan ik schadelijke software krijgen zonder het te weten?](#can-i-get-malicious-software-without-knowing-it)  
-   [Waarom is het belangrijk om licentieovereenkomsten te lezen voordat u software installeert?](#why-is-it-important-to-review-license-agreements-before-installing-software)  
-   [Wat is het verschil tussen Endpoint Protection en Windows Defender?](#what-s-the-difference-between-endpoint-protection-and-windows-defender)  
-   [Waarom detecteert Windows Defender geen cookies](#why-doesn-t-windows-defender-detect-cookies)  
-   [Hoe kan ik voorkomen dat schadelijke software?](#how-can-i-prevent-malware)  
-   [Wat zijn virus-en spywaredefinities?](#what-are-virus-and-spyware-definitions)  
-   [Hoe houd ik virus-en spywaredefinities up-to-date?](#how-do-i-keep-virus-and-spyware-definitions-up-to-date)  
-   [Hoe ik items verwijderen of herstellen in quarantaine geplaatst door Windows Defender of Endpoint Protection?](#how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection)  
-   [Wat is realtime-beveiliging?](#what-is-real-time-protection)  
-   [Hoe weet ik of Windows Defender of Endpoint Protection op mijn computer wordt uitgevoerd?](#how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer)
-   [Hoe Windows Defender of Endpoint Protection-waarschuwingen instellen?](#how-to-set-up-windows-defender-or-endpoint-protection-alerts)  

##  <a name="why-do-i-need-antivirus-and-antispyware-software"></a>Waarom heb ik software tegen virussen en spyware nodig?  

 Het is essentieel dat u ervoor zorgt dat op uw computer software wordt uitgevoerd die beschermt tegen schadelijke software. Schadelijke software, inclusief virussen, spyware of andere mogelijk ongewenste software, kan op elk moment dat u verbinding hebt met internet proberen zich op uw computer te installeren. Uw computer kan ook worden geïnfecteerd wanneer u een programma installeert vanaf een cd, dvd of andere verwisselbare media. Schadelijke software kan ook zo worden geprogrammeerd dat deze niet tijdens de installatie, maar op een onverwacht moment daarna wordt uitgevoerd.  

 Windows Defender of Endpoint Protection biedt drie manieren om te voorkomen dat schadelijke software de computer infecteert:  

-   **Bij realtime-beveiliging** : realtime-beveiliging zorgt ervoor dat Windows Defender computer continu bewaakt en waarschuwingen u wanneer schadelijke software, inclusief virussen, spyware of andere mogelijk software ongewenste probeert zichzelf te installeren of uitvoeren op uw computer. Windows Defender onderbreekt vervolgens de software, zodat u de aanbeveling met betrekking tot de software kunt volgen of alternatieve actie kunt ondernemen.  

    |**Optie realtime-beveiliging** |**doel** |

    |-|-|  
    | Alle downloads scannen | Deze optie controleert bestanden en programma's die worden gedownload, inclusief bestanden die automatisch worden gedownload via Windows Internet Explorer en Microsoft Outlook Express®, zoals ActiveX® besturingselementen en software-installatieprogramma's. Deze bestanden kunnen door de browser worden gedownload, geïnstalleerd of uitgevoerd. Schadelijke software, inclusief virussen, spyware en andere mogelijk ongewenste software, kan worden opgenomen in deze bestanden en zonder uw medeweten worden geïnstalleerd.<br /><br /> Met de optie realtime-beveiliging bewaakt Windows Defender voortdurend de computer en controleert deze op mogelijke schadelijke bestanden of programma's die u hebt gedownload. Met deze controlefunctie betekent dat Windows Defender hoeven niet te vertragen websurfen of e-ervaring te controleren van alle bestanden en programma's u wilt downloaden. |  
    | Bestands- en programma-activiteit op de computer bewaken | Deze optie controleert wanneer bestanden en programma's worden gestart op uw computer uitgevoerd en waarschuwt u over alle acties die ze uitvoeren en de acties die hierop worden uitgevoerd. Dit is belangrijk, omdat schadelijke software gebruik kan maken van beveiligingslekken in programma's die u hebt geïnstalleerd om buiten uw medeweten schadelijke of ongewenste software uit te voeren. Spyware zichzelf bijvoorbeeld op de achtergrond uitvoeren wanneer u een programma start dat u vaak gebruikt. Windows Defender controleert uw programma's en waarschuwt u als er verdachte activiteit wordt gedetecteerd. |  
    | Gedragscontrole inschakelen | Deze optie controleert u verzamelingen gedragingen op verdachte patronen die mogelijk niet worden gedetecteerd door traditionele antivirusprogramma detectiemethoden. |  

    | Systeem voor Netwerkinspectie inschakelen | Deze optie kunt u uw computer beschermen tegen zero-day' exploits die gebruikmaken van bekende beveiligingsproblemen, verkort de tijd tussen het moment dat een beveiligingsprobleem wordt gedetecteerd en een update wordt toegepast. |  

-   **Opties voor scannen** -u kunt Windows Defender gebruiken om te scannen op mogelijke bedreigingen zoals virussen, spyware en andere schadelijke software die de computer mogelijk een risico. U kunt ook regelmatige scans plannen en schadelijke software verwijderen die tijdens een scan wordt gedetecteerd.  

-   **Microsoft Active Protection Service-community** -de onlinecommunity Microsoft Active Protection Service kunt u zien hoe anderen reageren op software waarvan de risico's nog niet zijn geclassificeerd. U kunt deze informatie gebruiken om te bepalen of u wilt toestaan dat deze software op uw computer wordt uitgevoerd. Als u deelneemt, worden uw keuzes toegevoegd aan de classificaties van de community om andere te helpen bepalen wat ze moeten doen.  

##  <a name="how-can-i-tell-if-my-computer-is-infected-with-malicious-software"></a>Hoe kan ik zien of mijn computer is geïnfecteerd met schadelijke software?  

 Mogelijk hebt u een vorm van schadelijke software, inclusief virussen, spyware of andere mogelijk ongewenste software op uw computer als:  

-   U nieuwe werkbalken, koppelingen of favorieten opmerkt die u niet bewust aan uw webbrowser hebt toegevoegd.  

-   Uw startpagina, muisaanwijzer of zoekprogramma onverwacht verandert.  

-   U het adres typt voor een bepaalde website, zoals een zoekmachine, maar zonder voorafgaande kennisgeving naar een andere website wordt doorgestuurd.  

-   Bestanden automatisch van uw computer worden verwijderd.  

-   Uw computer wordt gebruikt voor aanvallen op andere computers.  

-   U pop-ups ziet, ook als u geen gebruikmaakt van internet.  

-   Uw computer begint plotseling langzamer is dan normaal. Niet alle computerprestatieproblemen worden veroorzaakt door schadelijke software, maar schadelijke software, vooral spyware, kan merkbare veranderingen veroorzaken.  

Het is ook mogelijk dat zich op uw computer schadelijke software bevindt, zelfs als u hiervan geen symptomen opmerkt. Met dit type software kan zonder uw medeweten of toestemming informatie over u en uw computer worden verzameld. Ter bescherming van uw privacy en uw computer, moet u altijd Windows Defender of Endpoint Protection uitvoeren.  

## <a name="how-can-i-find-the-version-of-windows-defender"></a>Hoe vind ik de versie van Windows Defender?
 Als u wilt weergeven van de versie van Windows Defender op uw computer uitgevoerd, opent u Windows Defender (Klik op **Start** en zoek vervolgens naar **Windows Defender**), klikt u op **instellingen**, en Ga naar de onderkant van de Windows Defender-instellingen om te zoeken **versie-info**.

##  <a name="what-should-i-do-if-windows-defender-or-endpoint-protection-detects-malicious-software-on-my-computer"></a>Wat moet ik doen als schadelijke software op mijn computer wordt gedetecteerd door Windows Defender of Endpoint Protection?  

 Als Windows Defender schadelijke of mogelijk ongewenste software detecteert op de computer (bij controles van de realtime-beschermingsfunctie of na het uitvoeren van een scan), wordt rechtsonder in het scherm een waarschuwingsbericht weergegeven over het gedetecteerde item.  

 In dit waarschuwingsbericht bevindt zich een knop **Computer opschonen** en een koppeling **Details weergeven** waarmee meer informatie over het gedetecteerde item kan worden geraadpleegd. Klik op de koppeling **Details weergeven** om het venster **Details over de mogelijke dreiging** te openen. Dit venster bevat aanvullende informatie over het gedetecteerde item. Kies nu welke actie op het item moet worden toegepast of klik op **Computer opschonen**. Bij twijfel over de op het gedetecteerde item toe te passen actie is het aanbevolen het door Windows Defender toegewezen waarschuwingsniveau als uitgangspunt te gebruiken (zie Meer informatie over waarschuwingsniveaus voor meer informatie).  

 Waarschuwingsniveaus helpen bij de beslissing hoe gereageerd moet worden op virussen, spyware en andere mogelijk ongewenste software. Windows Defender beveelt aan dat alle virussen en spyware worden verwijderd, maar soms wordt gewaarschuwd voor software die niet werkelijk kwaadaardig of ongewenst is. Met behulp van de volgende informatie kan worden bepaald wat er gedaan moet worden als Windows Defender mogelijk ongewenste software op de computer detecteert.  

 U kunt een van de volgende acties kiezen om op het gedetecteerde item toe te passen, afhankelijk van het waarschuwingsniveau:  

-   **Verwijder** -deze actie worden de software permanent verwijderd van uw computer.  

-   **Quarantaine** -met deze actie de software quarantaine geplaatst zodat deze kan niet worden uitgevoerd. Als Windows Defender software in quarantaine plaatst, wordt deze software verplaatst naar een andere locatie. Er wordt voorkomen dat de software wordt uitgevoerd totdat de software wordt teruggezet of van de computer wordt verwijderd.  

-   **Toestaan dat** -met deze actie wordt de software toegevoegd aan de lijst met toegestane programma's in Windows Defender en kan worden uitgevoerd op uw computer. U wordt niet meer door Windows Defender gewaarschuwd over mogelijke risico's waaraan de software uw privacy of de computer kan blootstellen.  

 Als u **Toestaan** kiest voor een item, bijvoorbeeld software, krijgt u geen waarschuwingen van Windows Defender meer over de risico's die de software oplevert voor uw privacy of de computer. Voeg software alleen aan de lijst met toegestane items toe als de software vertrouwd is en afkomstig is van een vertrouwde uitgever.  

### <a name="how-to-remove-potentially-harmful-software"></a>Het verwijderen van schadelijke software

U kunt alle ongewenste of mogelijk schadelijke items die Windows Defender detecteert snel en eenvoudig verwijderen met de optie **Computer opschonen** .  

1.  Als u de melding ziet die wordt weergegeven in het systeemvak nadat mogelijke bedreigingen zijn gedetecteerd, klikt u op **Computer opschonen**.  

2.  Windows Defender verwijdert de mogelijke bedreiging (of bedreigingen) en geeft een melding wanneer het opschonen van de computer is voltooid.  

3.  Als u meer informatie wilt over de gedetecteerde bedreigingen, klikt u op het tabblad **Geschiedenis** en selecteert u vervolgens **Alle gedetecteerde items**.  

4.  Als u niet alle gedetecteerde items ziet, klikt u op **details weergeven**. Als u wordt gevraagd om een beheerderswachtwoord of een bevestiging, typt u het wachtwoord of bevestigt u de actie. Op systemen met Windows XP moet u wellicht als beheerder zijn aangemeld op de computer.  

> [!NOTE]  
>  Indien mogelijk verwijdert Windows Defender tijdens het opschonen van de computer alleen het geïnfecteerde deel van een bestand, niet het volledige bestand.  

##  <a name="what-is-a-virus"></a>Wat is er een virus?  
 Computervirussen zijn softwareprogramma's die zijn ontworpen om de werking van een computer te verstoren, om gegevens op te slaan, beschadigen of verwijderen, of om via internet andere computers te infecteren. Virussen zorgen vaak voor vertraging en veroorzaken ondertussen andere problemen.  

##  <a name="what-is-spyware"></a>Wat is spyware?  
 Spyware is software die zichzelf zonder uw toestemming, of zonder u hiervan op de hoogte te stellen of hierover controle te geven, op uw computer kan installeren of uitvoeren. Spyware veroorzaakt mogelijk geen symptomen nadat uw computer is geïnfecteerd, maar veel schadelijke of ongewenste programma's kunnen invloed hebben op de werking van uw computer. Spyware kan bijvoorbeeld uw onlinegedrag volgen of informatie over u verzamelen (met inbegrip van gegevens waarmee u kunt worden geïdentificeerd en andere gevoelige gegevens), instellingen wijzigen op uw computer of ervoor zorgen dat uw computer traag wordt.  

##  <a name="whats-the-difference-between-viruses-spyware-and-other-potentially-harmful-software"></a>Wat is het verschil tussen virussen, spyware en andere mogelijk schadelijke software?  
 Zowel virussen als spyware worden zonder uw medeweten geïnstalleerd op uw computer en beide kunnen destructieve gevolgen hebben. Ze hebben ook de mogelijkheid informatie op uw computer vast te leggen en deze informatie te beschadigen of verwijderen. Ze kunnen beide de prestaties van uw computer negatief beïnvloeden.  

 Het belangrijkste verschil tussen virussen en spyware is hoe ze zich gedragen op uw computer. Virussen willen, net zoals levende organismen, een computer infecteren, repliceren en zich vervolgens naar zo veel mogelijk andere computers verspreiden. Spyware, is echter meer op een mol - wil ' in ' uw computer verplaatst en blijven er zolang er mogelijk, verzenden waardevolle informatie over uw computer naar een externe bron, terwijl het is.  

##  <a name="where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from"></a>Waar komen virussen, spyware en andere mogelijk ongewenste software vandaan?  
 Ongewenste software zoals virussen, kan worden geïnstalleerd door websites of door programma's die u hebt gedownload of die u hebt geïnstalleerd met een cd, dvd, externe vaste schijf of apparaat. Spyware wordt meestal geïnstalleerd door gratis software, zoals delen van bestanden, schermbeveiligingen of zoekwerkbalken.  

##  <a name="can-i-get-malicious-software-without-knowing-it"></a>Kan ik schadelijke software krijgen zonder het te weten?  
 Ja, bepaalde schadelijke software kan worden geïnstalleerd vanaf een website via een ingesloten script of een programma in een webpagina. Voor de installatie van andere schadelijke software is uw hulp vereist. Deze software maakt gebruik van pop-ups in uw browser of gratis software waarvoor u een downloadbaar bestand accepteert. Als u Microsoft Windows ® up-to-date te houdt en de beveiligingsinstellingen niet verlaagt, kunt u de kans op een infectie minimaliseren.  

##  <a name="why-is-it-important-to-review-license-agreements-before-installing-software"></a>Waarom is het belangrijk om licentieovereenkomsten te lezen voordat u software installeert?  
 Wanneer u websites bezoekt, gaat niet automatisch akkoord met het downloaden van items die de site worden aangeboden. Lees zorgvuldig de gebruiksrechtovereenkomst van gratis software, zoals programma's voor het delen van bestanden of schermbeveiligers. Wees bedacht op zinnen waarin u wordt verplicht advertenties en pop-ups van het bedrijf te accepteren of waarin wordt aangegeven dat de software bepaalde gegevens verzendt naar de software-uitgever.  

##  <a name="whats-the-difference-between-endpoint-protection-and-windows-defender"></a>Wat is het verschil tussen Endpoint Protection en Windows Defender?  
 Endpoint Protection is antimalwaresoftware. Dit betekent dat de software is ontworpen om een breed scala aan schadelijke software, inclusief virussen, spyware en andere mogelijk ongewenste software te detecteren en uw computer hiertegen te beschermen. Windows Defender wordt automatisch samen met uw Windows-besturingssysteem geïnstalleerd en is software die spyware detecteert en stopt.  

##  <a name="why-doesnt-windows-defender-detect-cookies"></a>Waarom detecteert Windows Defender geen cookies  
 Cookies zijn kleine tekstbestanden die door websites op uw computer naar de store-informatie over u en uw voorkeuren plaatsen. Websites gebruikmaken van cookies om een persoonlijke ervaring en voor het verzamelen van informatie over het gebruik van de website. Windows Defender detecteert geen cookies omdat deze niet worden beschouwd als een bedreiging voor uw privacy of voor de beveiliging van uw computer. De meeste internetbrowsers kunt u om cookies te blokkeren.  

##  <a name="how-can-i-prevent-malware"></a>Hoe kan ik voorkomen dat schadelijke software?  
 Twee van de belangrijkste zorgen voor computergebruikers zijn tegenwoordig virussen en spyware. Hoewel beide een probleem kunnen vormen, kunt u zich hier door te plannen vrij eenvoudig tegen verdedigen:  

-   Software op uw computer actueel te houden en vergeet niet alle patches te installeren. Werk uw besturingssysteem regelmatig bij.  

-   Zorg ervoor dat uw antivirus- en antispywaresoftware, Windows Defender, de meest recente updates gebruikt tegen mogelijke bedreigingen (zie Hoe houd ik virus-en spywaredefinities up-to-date?). Zorg er ook voor dat u altijd de meest recente versie van Windows Defender gebruikt.  

-   Download updates alleen van betrouwbare bronnen. Ga voor Windows-besturingssystemen altijd naar [Microsoft Update](http://go.microsoft.com/fwlink/?LinkID=96304) (http://go.microsoft.com/fwlink/?LinkID=96304) en andere software altijd gebruik voor de websites van het bedrijf of de persoon die produceert.  

-   Als u een e-mailbericht met een bijlage ontvangt en de bron niet vertrouwt, verwijdert u dit onmiddellijk. Niet alle toepassingen of de bestanden downloaden van onbekende bronnen en wees voorzichtig wanneer u bestanden uitwisselt met andere gebruikers.  

-   Installeer en gebruik een firewall. Het wordt aanbevolen Windows Firewall in te schakelen.  

##  <a name="what-are-virus-and-spyware-definitions"></a>Wat zijn virus-en spywaredefinities?  
 Wanneer u Windows Defender of Endpoint Protection gebruikt, is het belangrijk ervoor te zorgen dat de virus- en spywaredefinities zijn bijgewerkt. Definities zijn bestanden die fungeren als een voortdurend groeiende encyclopedie met mogelijke softwarebedreigingen. Windows Defender of Endpoint Protection gebruikt definities om te bepalen of gedetecteerde software een virus, spyware of andere mogelijk ongewenste software is, en om u vervolgens te waarschuwen voor mogelijke risico's. Om ervoor te zorgen dat uw definities altijd zijn bijgewerkt, werkt Windows Defender of Endpoint Protection samen met Microsoft Update om nieuwe definities automatisch te installeren zodra ze worden vrijgegeven. Voordat u gaat scannen, kunt u ook met Windows Defender of Endpoint Protection online controleren of er bijgewerkte definities zijn.  

##  <a name="how-do-i-keep-virus-and-spyware-definitions-up-to-date"></a>Hoe houd ik virus-en spywaredefinities up-to-date?  
 Virus- en spywaredefinities zijn bestanden die fungeren als een encyclopedie van bekende schadelijke software, inclusief virussen, spyware en andere mogelijk ongewenste software. Omdat schadelijke software voortdurend wordt ontwikkeld, is Windows Defender of Endpoint Protection afhankelijk van bijgewerkte definities om te bepalen of software die wordt geïnstalleerd of uitgevoerd, of waarmee wordt geprobeerd instellingen op uw computer te wijzigen, een virus, spyware of andere mogelijk ongewenste software is.  

### <a name="to-automatically-check-for-new-definitions-before-scheduled-scans-recommended"></a>Automatisch controleren op nieuwe definities voor een geplande scan (aanbevolen)  

1.  Open de Windows Defender- of Endpoint Protection-client door op het pictogram in het systeemvak te klikken, of start de client vanuit het menu **Start** .  

2.  Klik op **Instellingen**en klik vervolgens op **Geplande scan**.  

3.  Controleer of het selectievakje **Zoeken naar de meest recente definities van virussen en spyware voordat een geplande scan wordt uitgevoerd** is ingeschakeld en klik vervolgens op **Wijzigingen opslaan**. Als u wordt gevraagd om een beheerderswachtwoord of een bevestiging, typt u het wachtwoord of bevestigt u de actie.  

### <a name="to-check-for-new-definitions-manually"></a>Om te controleren op nieuwe definities handmatig

 Windows Defender of Endpoint Protection werkt automatisch de virus- en spywaredefinities op uw computer bij. Als de definities niet zijn bijgewerkt voor meer dan zeven dagen (bijvoorbeeld als u op uw computer niet inschakelt voor een week), waarschuwt Windows Defender of Endpoint Protection u de definities zijn verouderd.  

1.  Open de Windows Defender- of Endpoint Protection-client door op het pictogram in het systeemvak te klikken, of start de client vanuit het menu **Start** .  

2.  Als u handmatig wilt controleren of er nieuwe definities zijn, klikt u op het tabblad **Bijwerken** en klikt u vervolgens op **Definities bijwerken**.  

##  <a name="how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>Hoe ik items verwijderen of herstellen in quarantaine geplaatst door Windows Defender of Endpoint Protection?  

 Als Windows Defender of Endpoint Protection software in quarantaine plaatst, wordt de software verplaatst naar een andere locatie. Er wordt voorkomen dat de software wordt uitgevoerd totdat de software wordt teruggezet of van de computer wordt verwijderd.  

 Voor alle stappen in deze procedure geldt het volgende: als u gevraagd om een beheerderswachtwoord of een bevestiging, typt u het wachtwoord of geeft u de bevestiging.  

###  <a name="to-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>Verwijderen of herstellen van items in quarantaine geplaatst door Windows Defender of Endpoint Protection


1.  Klik op het tabblad **Geschiedenis** , selecteer **Items in quarantaine**en selecteer vervolgens de optie **Items in quarantaine** .  

2.  Klik op **Details weergeven** om alle items te bekijken.  

3.  Bekijk elk item en klik voor elk item of u dit wilt **Verwijderen** of **Herstellen**. Als u alle items in quarantaine van uw computer wilt verwijderen, klikt u op **Alles verwijderen**.  

##  <a name="what-is-real-time-protection"></a>Wat is realtime-beveiliging?  

 Realtime-beveiliging zorgt ervoor dat Windows Defender de computer continu bewaakt en waarschuwt u wanneer mogelijke bedreigingen zoals virussen en spyware, probeert zichzelf te installeren of uit te voeren op uw computer. Omdat deze functie een belangrijk aspect vormt van de manier waarop Windows Defender uw computer beschermt, moet u ervoor zorgen dat realtime-beveiliging altijd is ingeschakeld. Als realtime-beveiliging uitgeschakeld, Windows Defender waarschuwt u en uw computer€ verandert™ â €œAt riskâ€ s status.  

 Wanneer met realtime-beveiliging een dreiging of mogelijke bedreiging wordt gedetecteerd, wordt door Windows Defender een melding weergegeven. U kunt nu kiezen uit de volgende opties:  

-   Klik op **Computer opschonen** om het gedetecteerde item te verwijderen. Windows Defender verwijdert het item automatisch van uw computer.  

-   Klik op de koppeling **Details weergeven** om het venster Details over de mogelijke dreiging weer te geven en kies vervolgens welke actie moeten worden uitgevoerd op het gedetecteerde item.  

 U kunt kiezen welke software en instellingen Windows Defender moet bewaken, maar het wordt aangeraden om realtime-beveiliging en alle opties voor realtime-beveiliging in te schakelen. In de volgende tabel worden de beschikbare opties verklaard.  

|||  
|-|-|  
|**Optie realtime-beveiliging**|**Doel**|  
|Alle downloads scannen|Deze optie controleert bestanden en programma's die worden gedownload, inclusief bestanden die automatisch worden gedownload via Windows Internet Explorer en Microsoft Outlook Express ®, zoals ® ActiveX-besturingselementen en software-installatieprogramma's. Deze bestanden kunnen door de browser worden gedownload, geïnstalleerd of uitgevoerd. Schadelijke software, inclusief virussen, spyware en andere mogelijk ongewenste software, kan worden opgenomen in deze bestanden en zonder uw medeweten worden geïnstalleerd.<br /><br /> Met de optie realtime-beveiliging bewaakt Windows Defender voortdurend de computer en controleert deze op mogelijke schadelijke bestanden of programma's die u hebt gedownload. Dankzij deze bewakingsfunctie hoeft Windows Defender uw browser- of e-mailervaring niet te vertragen om bestanden of programma's die u wilt downloaden te controleren.|  
|De activiteit van bestanden en programma's op de computer controleren|Deze optie houdt in de gaten wanneer bestanden en programma's op uw computer worden gestart en waarschuwt u over de acties die ze uitvoeren en over de acties die erop worden uitgevoerd. Dit is belangrijk, omdat schadelijke software gebruik kan maken van beveiligingslekken in programma's die u hebt geïnstalleerd om buiten uw medeweten schadelijke of ongewenste software uit te voeren. Spyware zichzelf bijvoorbeeld op de achtergrond uitvoeren wanneer u een programma start dat u vaak gebruikt. Windows Defender controleert uw programma's en waarschuwt u als er verdachte activiteiten worden gedetecteerd.|  
|Gedragscontrole inschakelen|Met deze optie controleert u verzamelingen gedragingen op verdachte patronen die door traditionele methoden voor antivirusdetectie niet zouden worden gedetecteerd.|  
|Systeem voor netwerkinspectie inschakelen|Deze optie kunt u uw computer beschermen tegen â €œzero dayâ€ exploits die gebruikmaken van bekende beveiligingsproblemen, verkort de tijd tussen het moment dat een beveiligingsprobleem wordt gedetecteerd en een update wordt toegepast.|  

### <a name="to-turn-off-real-time-protection"></a>Realtime-beveiliging uitschakelen  

1.  Klik op **Instellingen**en klik vervolgens op **Realtime-beveiliging.**  

2.  Wis de opties voor realtime-beveiliging die u wilt uitschakelen en klik vervolgens op **Wijzigingen opslaan**. Als u wordt gevraagd om een beheerderswachtwoord of een bevestiging, typt u het wachtwoord of bevestigt u de actie.  

##  <a name="how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer"></a>Hoe weet ik of Windows Defender of Endpoint Protection op mijn computer wordt uitgevoerd?  

 Nadat u Windows Defender op uw computer hebt geïnstalleerd, kunt u het hoofdvenster sluiten en Windows Defender op de achtergrond uitvoeren. Windows Defender wordt voortdurend op uw computer uitgevoerd om deze te beveiligen tegen bedreigingen.  

 U weet natuurlijk ook dat Windows Defender wordt uitgevoerd wanneer hierdoor in het systeemvak meldingen worden weergegeven. Met deze meldingen wordt u geattendeerd op mogelijke bedreigingen die door Windows Defender zijn gedetecteerd.  

 U ontvangt ook andere waarschuwingsmeldingen, bijvoorbeeld wanneer u realtime-beveiliging hebt uitgeschakeld, wanneer u de virus- en spywaredefinities een aantal dagen niet hebt bijgewerkt of wanneer er updates voor het programma beschikbaar zijn. Windows Defender geeft ook kort een melding weer om u erop te attenderen dat de computer wordt gescand.  

> [!TIP]  

>Als u de Windows Defender-pictogram in het systeemvak niet ziet, klikt u op de pijl in het systeemvak om verborgen pictogrammen, waaronder het pictogram Windows Defender weer te geven.  


 De kleur van het pictogram is afhankelijk van de huidige status van uw computer:  

-   Groen geeft aan dat de computerstatus Beschermd is.  

-   Geel geeft aan dat de computerstatus Mogelijk niet beschermd is.  

-   Groen geeft aan dat de computerstatus Risico is.  

##  <a name="how-to-set-up-windows-defender-or-endpoint-protection-alerts"></a>Hoe Windows Defender of Endpoint Protection-waarschuwingen instellen?  
 Wanneer Windows Defender op uw computer wordt uitgevoerd, wordt u automatisch gewaarschuwd als er een virus, spyware of andere mogelijk ongewenste software wordt gedetecteerd. U kunt Windows Defender ook zo instellen dat u wordt gewaarschuwd als u software uitvoert die nog niet is geanalyseerd en u kunt ervoor kiezen om te worden gewaarschuwd wanneer door software wijzigingen aan uw computer worden aangebracht.  

### <a name="to-set-up-alerts"></a>Waarschuwingen instellen  

1.  Klik op **Instellingen**en klik vervolgens op **Realtime-beveiliging.**  

2.  Zorg ervoor dat het selectievakje **Realtime-beveiliging inschakelen (aanbevolen)** is ingeschakeld.  

3.  Schakel de selectievakjes in naast de opties voor real-timebeveiliging die u wilt uitvoeren en klik vervolgens op **Wijzigingen opslaan**. Als u wordt gevraagd om een beheerderswachtwoord of een bevestiging, typt u het wachtwoord of bevestigt u de actie.  

### <a name="see-also"></a>Zie tevens  
 [Problemen met Windows Defender of Endpoint Protection-client oplossen](troubleshoot-endpoint-client.md)   

 [Endpoint Protection Client Help](endpoint-protection-client-help.md)
