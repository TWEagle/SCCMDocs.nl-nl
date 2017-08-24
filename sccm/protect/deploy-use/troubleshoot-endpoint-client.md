---
title: Troubleshooting Windows Defender of Endpoint Protection-client | Microsoft Docs
description: Informatie over het oplossen van problemen met Windows Defender- en Endpoint Protection.
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d837253e-fcc2-422a-9e2c-c78b938dfd8c
caps.latest.revision: "7"
caps.handback.revision: "0"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 1b096e71f5131214fb4e235e84d0b7f63e566831
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="troubleshooting-windows-defender-or-endpoint-protection-client"></a>Problemen met Windows Defender of Endpoint Protection-client oplossen

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Als u problemen ondervindt met Windows Defender of Endpoint Protection, neemt u contact op met uw beveiligingsadministrator voor ondersteuning. De volgende problemen kunt u ook zelf oplossen:  

-   [Windows Defender of Endpoint Protection bijwerken](#update-windows-defender-or-endpoint-protection)  
-   [Windows Defender of Endpoint Protection-service wordt gestart](#starting-windows-defender-or-endpoint-protection-service)  
-   [Problemen met de internetverbinding](#internet-connection-issues)  
-   [Gedetecteerde bedreiging kan niet worden hersteld.](#detected-threat-cant-be-remediated)  
-   [De Endpoint Protection-client installeren](#install-the-endpoint-protection-client)  

##  <a name="update-windows-defender-or-endpoint-protection"></a>Windows Defender of Endpoint Protection bijwerken  
 Windows Defender of Endpoint Protection werkt automatisch met Microsoft Update om ervoor te zorgen dat uw definities van virussen en spyware up-to-date worden gehouden.  

 **Symptomen**  

 In dit artikel worden veelvoorkomende problemen met automatische updates behandeld, waaronder de volgende situaties:  

-   U ziet foutberichten die aangeven dat er updates zijn mislukt.  

-   Wanneer u op updates wilt controleren, krijgt u een foutbericht dat de updates van de virus- en spywaredefinities niet kunnen worden gecontroleerd, gedownload of geïnstalleerd.  

-   Hoewel u met internet verbonden bent, mislukken de updates.  

-   Updates worden niet automatisch volgens de planning geïnstalleerd.  

 **Oorzaak**  

 De meest voorkomende oorzaken voor problemen met updates zijn problemen met de internetverbinding. Als u weet dat u bent verbonden met internet omdat u naar andere websites kunt bladeren, kan het probleem worden veroorzaakt door foutieve instellingen in Windows Internet Explorer.  

> [!IMPORTANT]  
>  U moet Internet Explorer afsluiten om deze stappen te voltooien. Druk ze daarom af, schrijf ze op of kopieer ze naar een ander bestand en maak vervolgens een bladwijzer aan voor dit onderwerp om later te gebruiken.  

### <a name="step-1-reset-your-internet-explorer-settings"></a>Stap 1: Instellingen van Internet Explorer opnieuw instellen  

1.  Sluit alle geopende programma's af, ook Internet Explorer.  

    > [!NOTE]  
    >  Als u deze instellingen in Internet Explorer opnieuw instelt, worden de tijdelijke bestanden, cookies, browsegeschiedenis en online wachtwoorden verwijderd. Uw Favorieten worden echter niet verwijderd.  

2.  Klik op **Start** , zoek naar **inetcpl.cpl**en druk vervolgens op **Enter**.  

3.  Klik in het dialoogvenster **Internetopties** op het tabblad **Geavanceerd** .  

4.  Klik onder **Instellingen voor Internet Explorer opnieuw instellen**op **Opnieuw instellen**en klik vervolgens nogmaals op **Opnieuw instellen** .  

5.  Wacht tot de instellingen in Internet Explorer opnieuw zijn ingesteld en klik vervolgens op **OK**.  

6.  Open Internet Explorer.  

7.  Open Microsoft Security Essentials, klik op het tabblad **Bijwerken** en klik vervolgens op **Bijwerken**.  

8.  Als het probleem zich blijft voordoen, gaat u verder met de volgende stap.  

### <a name="step-2-set-internet-explorer-as-the-default-browser"></a>Stap 2: Internet Explorer instellen als standaardbrowser  

1.  Sluit alle geopende programma's af, ook Internet Explorer.  

2.  Klik op **Start** , zoek naar **inetcpl.cpl**en druk vervolgens op **Enter**.  

3.  Klik in het dialoogvenster **Internetopties** op het tabblad **Programma's** .  

4.  Klik onder **Standaardwebbrowser**op **Als standaard instellen**.  

5.  Klik op **OK**.  

6.  Open Windows Defender of Endpoint Protection. Klik op het tabblad **Bijwerken** en klik vervolgens op **Bijwerken**.  

7.  Als het probleem zich blijft voordoen, gaat u verder met de volgende stap.  

### <a name="step-3-ensure-that-the-date-and-time-are-set-correctly-on-your-computer"></a>Stap 3: Controleren of de datum en tijd correct zijn ingesteld op uw computer  

1.  Open Windows Defender of Endpoint Protection.  

2.  Als het foutbericht dat u hebt ontvangen de code 0x80072f8f bevat, wordt het probleem waarschijnlijk veroorzaakt door een onjuiste instelling van de datum of tijd op uw computer.  

3.  Als u de datum- of tijdinstelling opnieuw wilt instellen, volgt u de stappen in [Verbroken snelkoppelingen op het bureaublad en veelvoorkomende onderhoudstaken corrigeren](http://go.microsoft.com/fwlink/?LinkId=155579) (http://go.microsoft.com/fwlink/?LinkId=155579).  

### <a name="step-4-rename-the-software-distribution-folder-on-your-computer"></a>Stap 4: Wijzig de naam van de map softwaredistributie op uw computer  

1. De service Automatische updates stoppen  

    1.  Klik op **Start** , zoek naar **services.msc**en druk vervolgens op **OK**.  

    2.  Klik met de rechtermuisknop op **Automatische updates-service**en klik vervolgens op **Stoppen**.  

    3.  Minimaliseer de module Services.  

2.  Wijzig de naam van de adreslijst **SoftwareDistribution** als volgt:  

    1.  Klik op **Start** , zoek naar  **cmd**en druk vervolgens op **OK**.  

    2.  Typ **cd %windir%**en druk op **Enter**.  

    3.  Typ **ren SoftwareDistribution SDTemp**en druk op **Enter**.  

    4.  Typ **exit**en druk op **Enter**.  

3.  Start de service Automatische updates als volgt:  

    1.  Maximaliseer de module Services.  

    2.  Klik met de rechtermuisknop op **Automatische updates-service**en klik vervolgens op **Starten**.  

    3.  Sluit het venster van de module Services.  

### <a name="step-5-reset-the-microsoft-antivirus-update-engine-on-your-computer"></a>Stap 5: De engine voor het bijwerken van antivirussoftware van Microsoft op de computer opnieuw instellen  

1.  Klik op **Start** , zoek naar  **cmd**en klik vervolgens op **OK**. Klik met de rechtermuisknop op **Opdrachtprompt**en selecteer vervolgens **Als administrator uitvoeren**.  

2.  Typ in het venster **Opdrachtprompt** de volgende opdrachten en druk na elke opdracht op **Enter** :  

     **Cd\\**  

     **Cd programma files\windows defender**  

     **MpCmdRun - RemoveDefinitions-alle**  

     **Afsluiten**  

3.  De computer opnieuw opstarten  

4.  Open Windows Defender of  
          Endpoint Protection, klikt u op de **Update** tabblad en klik vervolgens op **Update**.  

5.  Als het probleem zich blijft voordoen, gaat u verder met de volgende stap.  

### <a name="step-6-manually-install-the-virus-and-spyware-definition-updates"></a>Stap 6: Definitie-updates van virus- en spywaredefinities handmatig installeren  

-   Als u een 32-bits Windows-besturingssysteem hebt, kunt u de nieuwste updates handmatig downloaden op [http://go.microsoft.com/fwlink/?LinkID=87342](http://go.microsoft.com/fwlink/?LinkID=87342) (http://go.microsoft.com/fwlink/?LinkID=87342).  

-   Als u een 64-bits Windows-besturingssysteem hebt, kunt u de nieuwste updates handmatig downloaden op [http://go.microsoft.com/fwlink/?LinkID=87341](http://go.microsoft.com/fwlink/?LinkID=87341) (http://go.microsoft.com/fwlink/?LinkID=87341).  

-   Klik op **Uitvoeren**. De meest recente updates worden handmatig op uw computer geïnstalleerd.  


### <a name="step-7-contact-support"></a>Stap 7: Neem contact op met ondersteuning  

-   Als u met de stappen het probleem niet hebt opgelost, kunt u contact opnemen met de ondersteuning. Zie [Klantondersteuning](http://go.microsoft.com/fwlink/?LinkID=196174) (http://go.microsoft.com/fwlink/?LinkID=196174) voor meer informatie.  

##  <a name="starting-windows-defender-or-endpoint-protection-service"></a>Windows Defender of Endpoint Protection-service wordt gestart  
 **Symptoom**  

 U ontvangt een bericht met de mededeling dat **Windows Defender of Endpoint Protection is niet de bewaking van uw computer omdat de service van het programma is gestopt. U start het.** 

 **Oplossing**  

### <a name="step-1-restart-your-computer"></a>Stap 1: De computer opnieuw opstarten  

-   Sluit alle toepassingen en start de computer opnieuw op.  

### <a name="step-2-make-sure-the-windows-defender-or-endpoint-protection-service-is-set-to-automatic-and-is-started"></a>Stap 2: Zorg ervoor dat de 'Windows Defender' of 'Endpoint Protection-service' is ingesteld op automatisch en wordt gestart  

1.  Klik op **Start** , zoek naar **services.msc**en druk vervolgens op **Enter**.  

2.  Zoek naar **Microsoft Antimalwareservice**. Klik er met de rechtermuisknop op en selecteer **Eigenschappen** of dubbelklik erop om de service te openen.  

3.  Controleer of**Opstarttype**is ingesteld op**Automatisch**.  

4.  Klik op de knop **Starten** om de service te starten. Als de knop **Starten** niet beschikbaar is, klikt u op de knop **Stoppen** en vervolgens op de knop **Starten** om de service opnieuw te starten.  

5.  Noteer eventuele fouten die tijdens dit proces optreden. Meld dit in zo’n geval online en vermeld de gegevens over de fout erbij.  

### <a name="step-3-remove-any-existing-internet-security-programs"></a>Stap 3: Alle bestaande internetbeveiligingsprogramma's verwijderen  

1.  Klik op **Start** , zoek naar **appwiz.cpl**en druk vervolgens op **Enter**.  

2.  Verwijder uit de lijst met geïnstalleerde programma's eventuele internetbeveiligingsprogramma’s van derden.*  

3.  Start uw computer opnieuw op en probeer het installeren van Windows Defender of  
          Endpoint Protection opnieuw.  

> [!NOTE]  
>  Sommige internetbeveiligingstoepassingen kunnen niet volledig worden verwijderd. Mogelijk moet u voor de vorige beveiligingstoepassing een opschoonprogramma downloaden en uitvoeren om deze volledig te kunnen verwijderen.  

> [!CAUTION]  
>  Wanneer u internetbeveiligingsprogramma's verwijdert, is de computer niet beveiligd. Als u problemen ondervindt installeren   
>       Endpoint Protection na het verwijderen van bestaande internetbeveiligingsprogramma's, neem contact op met de Windows Defender of  
>       Endpoint Protection ondersteuning door het probleem online te dienen (Zie voor meer informatie [hoe problemen Online indienen](http://www.microsoft.com/en-ph/security_essentials/Support/8c9074b6-1558-4d14-bc39-d294ced11096.aspx)).  

### <a name="step-4-uninstallreinstall-endpoint-protection"></a>Stap 4: Endpoint Protection verwijderen/opnieuw installeren  

1.  Klik op **Start** , zoek naar **appwiz.cpl**en druk vervolgens op **Enter**.  

2.  Klik in de lijst met geïnstalleerde programma's op **Endpoint Protection**en verwijder dit.  

3.  Start uw computer opnieuw op als daarom wordt gevraagd en installeer vervolgens Endpoint Protection opnieuw.  

##  <a name="internet-connection-issues"></a>Problemen met de internetverbinding  
 Om ervoor te zorgen dat de computer de meest recente updates via Windows Update ontvangt, moet u verbonden zijn met internet.  

### <a name="step-1-verify-that-your-computer-is-connected-to-the-internet"></a>Stap 1: Controleren of uw computer is verbonden met Internet  

1.  Klik op **Start**, zoek naar **ncpa.cpl**en druk vervolgens op **Enter**.  

2.  Klik met de rechtermuisknop op de naam van de verbinding en klik vervolgens op **Status**.  

3.  Als de computer verbinding heeft, wordt in Windows XP de status van de verbinding weergegeven als **Verbonden**, **Ingeschakeld**of **Verificatie** geslaagd. In Windows Vista en Windows 7 wordt de **IPv4** -status weergegeven als **Internet**.  

4.  Als de computer geen verbinding heeft, klikt u met de rechtermuisknop op de naam van de verbinding en klikt u vervolgens op **Verbinden**, **Inschakelen**, **Verifiëren**of **Herstellen**.  

### <a name="step-3-restart-your-computer"></a>Stap 3: De computer opnieuw opstarten  

-   Sluit alle geopende programma's en start de computer opnieuw op.  

### <a name="step-4-if-you-still-cant-connect-to-the-internet-check-your-connections"></a>Stap 4: Als u nog steeds geen verbinding met Internet kunt maken, de verbindingen controleren  

1.  Als u een inbelverbinding gebruikt, controleert u of de telefoonkabel goed is aangesloten op de wandcontactdoos en op het modem.  

2.  Als u een kabelmodem gebruikt, controleert u of de kabelverbinding met het modem en de verbinding van het modem naar de computer goed is aangesloten.  

3.  Als u een kabelmodem of DSL-router, controleert u of de verbindingen met de router en die met de computer goed zijn aangesloten. Koppel de router en het modem los en schakel ze uit. Wacht enkele minuten, sluit het modem eerst aan, wacht opnieuw een minuut en sluit vervolgens de router aan. Start daarna de computer opnieuw op.  

##  <a name="detected-threat-cant-be-remediated"></a>Gedetecteerde bedreiging kan niet worden hersteld.  
 Wanneer Windows Defender of  
      Endpoint Protection een mogelijke bedreiging die verborgen in een gecomprimeerd bestand met de extensie .zip of binnen een netwerkshare detecteert, wordt geprobeerd om te gaan met de bedreiging door in quarantaine plaatsen of te verwijderen.  

### <a name="remove-or-scan-the-file"></a>Het bestand verwijderen of scannen  

-   Als de gedetecteerde bedreiging zich in een zip-bestand bevindt, bladert u naar het zip-bestand en verwijdert u vervolgens het bestand of scant u dit door met de rechtermuisknop op het bestand te klikken en **Scannen met Windows Defender** of **Scannen met Endpoint Protection**te selecteren. Als Windows Defender of Endpoint Protection meer bedreigingen in het bestand detecteert, ontvangt u een melding over deze bedreigingen en kunt u geschikte actie ondernemen.  

-   Als de gedetecteerde bedreiging zich in een netwerkshare bevindt, bladert u naar de netwerkshare en scant u dit door met de rechtermuisknop op het bestand te klikken en **Scannen met Windows Defender** of **Scannen met Endpoint Protection**te selecteren. Als Windows Defender of Endpoint Protection meer bedreigingen in de netwerkshare detecteert, ontvangt u een melding over deze bedreigingen en kunt u geschikte actie ondernemen.  

-   Als u niet zeker bent van de oorsprong van het bestand, kunt u het beste een volledige scan uitvoeren op uw computer. Een volledige scan kan enige tijd duren, maar maakt het mogelijk voor Windows Defender of Endpoint Protection om de bron van de infectie te vinden en deze op te schonen.  

##  <a name="install-the-endpoint-protection-client"></a>De Endpoint Protection-client installeren  

> [!NOTE]  
>  Windows Defender wordt op Windows 10-pc’s samen met het besturingssysteem geïnstalleerd.  

 **Symptomen**  

 Installatie mislukt om een onbekende reden, of u krijgt een foutbericht met een foutcode zoals 0x80070643, 0X8007064A, 0x8004FF2E, 0x8004FF01, 0x8004FF07, 0x80070002, 0x8007064C, 0x8004FF00, 0x80070001, 0x80070656, 0x8004FF40, 0xC0000156, 0x8004FF41 0x8004FF0B, 0x8004FF11, 0x80240022, 0x8004FF04, 0x80070660, 0x800106B5, 0x80070715, 0x80070005, 0x8004EE00, 0x8007003, 0x800B0100, 0x8007064E of 0x8007007E.  

 Als u een computer hebt met Windows XP Service Pack 2 (SP2) ziet u mogelijk een of meer van de volgende foutberichten:  

-   Een updatepakket voor filterbeheer ontbreekt, waardoor de installatiewizard de installatie niet kan voltooien.  

-   KB914882 Setup-fout, Setup kan de Windows XP-bestanden niet bijwerken omdat de op het systeem geïnstalleerde taal niet overeenkomt met de taal van de update.  

 **Oorzaak**  

 Endpoint Protection kan niet worden geïnstalleerd op een computer met andere beveiligingsprogramma's. Soms worden ze niet volledig verwijderd, zelfs niet als u andere beveiligingsprogramma's verwijdert. U moet een legitieme versie uitvoeren van het Windows-besturingssysteem om Endpoint Protection te kunnen installeren.  

 **Oplossing**  

> [!IMPORTANT]  
>  U moet de computer opnieuw opstarten tijdens het oplossen van dit probleem. Maak een bladwijzer voor deze pagina (markeren als favoriet) zodat u dit onderwerp makkelijker opnieuw kunt vinden of druk de pagina af om het snel te kunnen nazoeken.  

### <a name="step-1-remove-any-existing-security-programs"></a>Stap 1: Bestaande beveiligingsprogramma's verwijderen  
**Endpoint Protection alleen**

1.  Verwijder alle bestaande internetbeveiligingsprogramma's volledig.  

2.  De computer opnieuw opstarten  

3.  Installeer Endpoint Protection opnieuw. Als het probleem hiermee niet is opgelost, gaat u verder met de volgende stap.  

### <a name="step-2-ensure-that-the-windows-installer-service-is-running"></a>Stap 2: Controleer of de Windows Installer-service wordt uitgevoerd  

1.  Klik op **Start** , zoek naar **services.msc**en druk vervolgens op **Enter**.  

2.  Klik met de rechtermuisknop op **Windows Installer**en klik vervolgens op **Starten**. Als **Starten** niet beschikbaar is en de opties **Stoppen** en **Opnieuw starten** wel beschikbaar zijn, dan weet u dat de service al is gestart.  

3.  Klik op de pagina **Services** , in het menu **Bestand** , op **Afsluiten**.  

4.  Klik op **Start** en zoek naar **opdrachtprompt**. Klik met de rechtermuisknop op **Opdrachtprompt**en klik vervolgens op **Als administrator uitvoeren**.  

5.  Type **MSIEXEC/REGSERVER**en druk vervolgens op **Enter**.  

    > [!NOTE]  
    >  Er is geen aanwijzing dat deze opdracht is geslaagd of mislukt.  

6.  Installeer Endpoint Protection opnieuw. Als het probleem hiermee niet is opgelost, gaat u verder met de volgende stap.  

### <a name="step-3-start-windows-in-selective-startup-mode"></a>Stap 3: Windows starten in de modus Selectief opstarten  

1.  Klik op **Start** , zoek naar **msconfig**en druk vervolgens op **Enter**.  

2.  Klik op het tabblad **Algemeen** op **Selectief opstarten**en schakel vervolgens het selectievakje **Opstartonderdelen laden** uit.  

3.  Schakel op het tabblad **Services** het selectievakje **Alle Microsoft-services verbergen** in en schakel alle selectievakjes uit voor de services die nog in de lijst staan.  

4.  Klik op **OK**en klik vervolgens op **Opnieuw opstarten** om de computer opnieuw op te starten.  

5.  Installeer Endpoint Protection opnieuw.  



### <a name="see-also"></a>Zie tevens  
 [Veelgestelde vragen over de Endpoint Protection-client](../../protect/deploy-use/endpoint-protection-client-faq.md)   

 [Endpoint Protection Client Help](../../protect/deploy-use/endpoint-protection-client-help.md)
