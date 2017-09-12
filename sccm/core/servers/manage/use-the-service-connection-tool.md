---
title: Service-hulpprogramma voor serviceverbindingen | Microsoft Docs
description: Meer informatie over dit hulpprogramma waarmee u verbinding maken met de Configuration Manager-cloudservice handmatig om gebruiksgegevens te uploaden.
ms.custom: na
ms.date: 09/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e4964c5-43cb-4372-9a89-b62ae6a4775c
caps.latest.revision: "11"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8039ee0c704bbe570ec3e45ba648f779923087c6
ms.sourcegitcommit: 2a1328da3facb20b0c78f3b12adbb5fdbe0dcc11
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="use-the-service-connection-tool-for-system-center-configuration-manager"></a>Het hulpprogramma voor serviceverbindingen in System Center Configuration Manager gebruiken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de **hulpprogramma voor serviceverbindingen** wanneer uw serviceverbindingspunt zich in de offlinemodus bevindt, of wanneer uw Configuration Manager-sitesysteemservers niet zijn verbonden met Internet. Het hulpprogramma kunt u uw site up-to-date houden met de meest recente updates voor Configuration Manager.  

Wanneer uitvoert, wordt het hulpprogramma handmatig maakt verbinding met de Configuration Manager-cloudservice om gebruiksgegevens voor uw hiërarchie te uploaden en om updates te downloaden. Het uploaden van gebruiksgegevens is noodzakelijk om ervoor te zorgen dat de cloudservice de juiste updates voor uw implementatie kan leveren.  

## <a name="prerequisites-for-using-the-service-connection-tool"></a>Vereisten voor het gebruik van het hulpprogramma voor serviceverbindingen
De volgende zijn vereisten en bekende problemen.

**Vereisten:**

-   U hebt een serviceverbindingspunt geïnstalleerd dat is ingesteld op **Offline, verbinding op aanvraag**.  

-   Het hulpprogramma moet worden uitgevoerd vanaf een opdrachtprompt.  

-   Elke computer waarop het hulpprogramma wordt uitgevoerd (de computer met het serviceaansluitpunt en de computer die is verbonden met internet), moet een x64 bitssysteem zijn waarop het volgende moet zijn geïnstalleerd:  

    -   De x86- en x64-bestanden van **Visual C++ Redistributable** .   Configuration Manager installeert standaard de x64 versie op de computer die als host fungeert voor het serviceverbindingspunt wordt gehost.  

         Als u een kopie van de Visual C++-bestanden wilt downloaden, gaat u naar [Visual C++ Redistributable Packages for Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=40784) in het Microsoft Downloadcentrum.  

    -   .NET Framework 4.5.2 of hoger.  

-   Het account waarmee u het hulpprogramma uitvoert, moet beschikken over:
    -   **Lokale beheerdersmachtigingen** op de computer waarop het serviceverbindingspunt wordt gehost (waarop het hulpprogramma wordt uitgevoerd).
    -   **Lezen** -machtigingen voor de sitedatabase.  



-   U hebt een USB-station met voldoende beschikbare ruimte voor het opslaan van bestanden en updates of een andere methode nodige om bestanden over te dragen tussen de serviceverbindingspuntcomputer en de computer met toegang tot internet. (Dit scenario veronderstelt dat uw site en de beheerde computers geen directe verbinding met internet hebben.)  



## <a name="use-the-service-connection-tool"></a>Het hulpprogramma voor serviceverbindingen gebruiken  

 U vindt het hulpprogramma voor serviceverbindingen (**serviceconnectiontool.exe**), in de installatiemedia van Configuration Manager **%path%\smssetup\tools\ServiceConnectionTool** map. Gebruik altijd het hulpprogramma voor serviceverbindingen die overeenkomt met de versie van Configuration Manager die u gebruikt.


 In deze procedure worden de volgende bestandsnamen en maplocaties in de voorbeelden van de opdrachtregels gebruikt (u hoeft deze paden en bestandsnamen en kunt in plaats daarvan alternatieven gebruiken die overeenkomen met uw omgeving en voorkeuren):  

-   Het pad naar een USB-Stick waarop gegevens worden opgeslagen voor de overdracht tussen servers:  **D:\USB\\**  

-   De naam van het CAB-bestand dat gegevens die zijn geëxporteerd van uw site bevat: **UsageData.cab**  

-   De naam van de lege map waar de gedownloade updates voor Configuration Manager wordt opgeslagen voor de overdracht tussen servers: **UpdatePacks**  

Op de computer die het serviceverbindingspunt host:  

-   Open een opdrachtprompt met beheerdersbevoegdheden en wijzig vervolgens de mappen in de locatie waarin **serviceconnectiontool.exe**zich bevindt.  

     Standaard kunt u dit hulpprogramma vinden in de installatiemedia van Configuration Manager **%path%\smssetup\tools\ServiceConnectionTool** map. Alle bestanden in deze map moeten in dezelfde map staan. Als dit niet het geval is, werkt het hulpprogramma voor serviceverbindingen niet.  

Wanneer u de volgende opdracht uitvoert, bereidt het hulpprogramma een CAB-bestand voor met gebruiksgegevens en kopieert dit naar een locatie die u opgeeft. De gegevens in het CAB-bestand zijn gebaseerd op het niveau van het verzamelen van diagnostische gebruiksgegevens waarvoor uw site is geconfigureerd. (zie [Diagnostische gegevens en gebruiksgegevens voor System Center Configuration Manager](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)).  Voer de volgende opdracht uit om het CAB-bestand maken:  

-   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

U moet ook de map ServiceConnectionTool inclusief alle inhoud kopiëren naar het USB-station of op een andere wijze beschikbaar maken op de computer die u wilt gebruiken voor stap 3 en 4.  

### <a name="overview"></a>Overzicht
#### <a name="there-are-three-primary-steps-to-using-the-service-connection-tool"></a>Er zijn drie primaire stappen voor het hulpprogramma voor serviceverbindingen gebruiken  

1.  **Voorbereiden**:  Deze stap wordt uitgevoerd op de computer die als host fungeert voor het serviceverbindingspunt wordt gehost. Wanneer het hulpprogramma wordt uitgevoerd het plaatst de gebruiksgegevens in een CAB-bestand en slaat deze op een USB-station (of alternatieve transferlocatie die u opgeeft).  

2.  **Verbinding maken met**: Voor deze stap kunt u het hulpprogramma uitvoeren op een externe computer die is verbonden met Internet, zodat u kunt de gebruiksgegevens te uploaden en vervolgens de updates downloaden.  

3.  **Importeren**: Deze stap wordt uitgevoerd op de computer die als host fungeert voor het serviceverbindingspunt wordt gehost. Wanneer uitvoert, wordt het hulpprogramma importeert u gedownload en voegt u deze toe aan uw site zodat u kunt vervolgens bekijken en deze updates vanuit de Configuration Manager-console installeren.  

Wanneer u vanaf versie 1606 verbinding maakt met Microsoft, kunt u meerdere CAB-bestanden tegelijk uploaden (elk uit een andere hiërarchie) en een proxyserver en gebruiker voor de proxyserver opgeven.   

#### <a name="to-upload-multiple-cab-files"></a>Om meerdere CAB-bestanden te uploaden
 -  Zet alle CAB-bestanden die u uit verschillende hiërarchieën exporteert in dezelfde map. De naam van elk bestand moet uniek zijn. Zo nodig kunt u de naam handmatig wijzigen.
 -  Wanneer u vervolgens de opdracht voor het uploaden van gegevens naar Microsoft uitvoert, geeft u de naam op van de map met de CAB-bestanden. (Vóór update 1606 kon u alleen gegevens uit één hiërarchie tegelijk uploaden en voor het hulpprogramma was het nodig dat u de naam van het CAB-bestand in de map opgaf.)
 -  Wanneer u vervolgens de importtaak voor het serviceverbindingspunt van een hiërarchie uitvoert, importeert het hulpprogramma automatisch alleen de gegevens voor die hiërarchie.  

#### <a name="to-specify-a-proxy-server"></a>Een proxyserver opgeven
U kunt de volgende optionele parameters gebruiken om een proxyserver op te geven (meer informatie over het gebruik van deze parameters vindt u in de sectie Opdrachtregelparameters van dit onderwerp):
  - **-proxyserveruri [FQDN_van_proxyserver]**  Gebruik deze parameter om de proxyserver voor deze verbinding op te geven.
  -  **-proxyusername [gebruikersnaam]**  Gebruik deze parameter als u een gebruiker voor de proxyserver moet opgeven.

#### <a name="specify-the-type-of-updates-to-download"></a>Geef het type van de updates te downloaden
Vanaf versie 1706, het downloadgedrag van hulpprogramma's standaard is gewijzigd en het hulpprogramma ondersteunt opties om te bepalen welke bestanden die u hebt gedownload.
-   Standaard wordt met het hulpprogramma alleen de meest recente beschikbare update die voor de versie van uw site geldt downloadt. Deze downloadt hotfixes.

Om dit gedrag wijzigen, gebruikt u een van de volgende parameters te wijzigen welke bestanden worden gedownload. De versie van uw site wordt bepaald door de gegevens in het CAB-bestand dat is geüpload wanneer het hulpprogramma wordt uitgevoerd.
-   **-downloadall** downloadt u deze optie Alles, met inbegrip van updates en hotfixes, ongeacht de versie van uw site.
-   **-downloadhotfix** deze optie alle hotfixes ongeacht de versie van uw site downloadt.
-   **-downloadsiteversion** deze optie downloadt de updates en hotfixes die u hebt een versie die hoger is dan de versie van uw site.

Voorbeeld van de opdrachtregel die gebruikmaakt van *- downloadsiteversion*:
- **serviceconnectiontool.exe-verbinding *- downloadsiteversion* - usagedatasrc D:\USB - updatepackdest D:\USB\UpdatePacks**




### <a name="to-use-the-service-connection-tool"></a>Het hulpprogramma voor serviceverbindingen gebruiken  

1.  Op de computer die het serviceverbindingspunt host:  

    -   Open een opdrachtprompt met beheerdersbevoegdheden en wijzig vervolgens de mappen in de locatie waarin **serviceconnectiontool.exe**zich bevindt.   

2.  Voer de volgende opdracht zodat het hulpprogramma een CAB-bestand met gebruiksgegevens voorbereidt en dat kopieert naar een locatie die u opgeeft:  

    -   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

    Als u CAB-bestanden uit meer dan één hiërarchie tegelijk uploadt, moet elk CAB-bestand in de map een unieke naam hebben. Bestanden die u aan de map toevoegt, kunt u handmatig wijzigen.

    Als u de gebruiksgegevens wilt weergeven die worden verzameld voor het uploaden naar de cloudservice van Configuration Manager, voert u de volgende opdracht uit voor het exporteren van dezelfde gegevens als CSV-bestand. Dit bestand kunt u vervolgens bekijken met behulp van een toepassing zoals Excel:  

    -   **serviceconnectiontool.exe -export -dest D:\USB\UsageData.csv**  

3.  Nadat de voorbereidingsstap is voltooid, verplaatst u het USB-station (of draagt u de geëxporteerde gegevens via een andere methode over) naar een computer die toegang heeft tot internet.  

4.  Open een opdrachtprompt met beheerdersbevoegdheden op de computer met internettoegang en wijzig de mappen in de locatie met een kopie van het hulpprogramma  **serviceconnectiontool.exe** en de aanvullende bestanden uit die map.  

5.  Voer de volgende opdracht uit om de gebruiksgegevens te uploaden en de updates voor Configuration Manager te downloaden:  

    -   **serviceconnectiontool.exe-connect - usagedatasrc D:\USB - updatepackdest D:\USB\UpdatePacks**

    Zie de sectie [Opdrachtregelopties](../../../core/servers/manage/use-the-service-connection-tool.md#bkmk_cmd) verderop in dit onderwerp voor meer voorbeelden van deze opdrachtregel.

    > [!NOTE]  
    >  Wanneer u de opdrachtregel uitvoert om verbinding met de Configuration Manager-cloudservice te maken, wordt er mogelijk een foutbericht weergegeven dat vergelijkbaar is met het volgende bericht:  
    >   
    >  -   Niet-verwerkte uitzondering: System.UnauthorizedAccessException:  
    >   
    >      Toegang tot het pad ' C:\  
    >     Users\br\AppData\Local\Temp\extractmanifestcab\95F8A562.sql' wordt geweigerd.  
    >   
    > Deze fout kan worden genegeerd en u kunt het foutvenster sluiten en doorgaan.  

6.  Nadat de updates voor Configuration Manager zijn gedownload, verplaatst u het USB-station (of draagt u de geëxporteerde gegevens via een andere methode over) naar de computer die het serviceverbindingspunt host.  

7.  Open op de computer waarop het serviceverbindingspunt wordt gehost, een opdrachtprompt met beheerdersbevoegdheden, wijzig de mappen in de locatie waarin **serviceconnectiontool.exe**zich bevindt en voer de volgende opdracht uit:  

    -   **serviceconnectiontool.exe -import -updatepacksrc D:\USB\UpdatePacks**  

8.  Nadat het importeren is voltooid, kunt u de opdrachtprompt sluiten. (Alleen updates voor de van toepassing zijnde hiërarchie worden geïmporteerd).  

9. Open de Configuration Manager-console en Ga naar **beheer** > **Updates en onderhoud**. De geïmporteerde updates kunnen nu worden geïnstalleerd. (Voorafgaand aan versie 1702, Updates en onderhoud is onder **beheer** > **Cloudservices**.)

 Zie [Updates binnen de console installeren voor System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md) voor informatie over het installeren van updates.  

## <a name="bkmk_cmd"></a> Opdrachtregelopties  
 Als u Help-informatie voor het hulpprogramma voor serviceverbindingspunten wilt weergeven, opent u via de opdrachtprompt de map waarin het hulpprogramma zich bevindt en voert u de volgende opdracht uit:  **serviceconnectiontool.exe**.  

|Opdrachtregelopties|Details|  
|---------------------------|-------------|  
|**-prepare -usagedatadest [station:][pad][bestandsnaam.cab]**|Met deze opdracht worden de huidige gebruiksgegevens opgeslagen in een CAB-bestand.<br /><br /> Voer deze opdracht uit als **lokale beheerder** op de server waarop het serviceverbindingspunt wordt gehost.<br /><br /> Voorbeeld:   **-prepare -usagedatadest D:\USB\Usagedata.cab**|    
|**-connect -usagedatasrc [station:][pad] -updatepackdest [station:][pad] -proxyserveruri [FQDN van proxyserver] -proxyusername [gebruikersnaam]** <br /> <br /> Als u voor Configuration Manager een eerdere versie dan 1606 gebruikt, moet u de naam van het CAB-bestand opgeven en kunt u niet de opties voor een proxyserver gebruiken.  De ondersteunde opdrachtparameters zijn: <br /> **-connect -usagedatasrc [station:][pad][bestandsnaam] -updatepackdest [station:][pad]** |Deze opdracht maakt verbinding met de Configuration Manager-cloudservice om de CAB-bestanden met gebruiksgegevens te uploaden vanaf de opgegeven locatie en om beschikbare updatepakketten en console-inhoud te downloaden. De opties voor proxyservers zijn optioneel.<br /><br /> Voer deze opdracht uit als **lokale beheerder** op een computer die verbinding met internet kan maken.<br /><br /> Voorbeeld van verbinding maken zonder proxyserver: **-connect -usagedatasrc D:\USB\ -updatepackdest D:\USB\UpdatePacks** <br /><br /> Voorbeeld van verbinding maken wanneer u een proxyserver gebruikt: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks -proxyserveruri itgproxy.redmond.corp.microsoft.com -proxyusername Meg** <br /><br /> Als u een eerdere versie dan 1606 gebruikt, moet u een bestandsnaam opgeven voor het CAB-bestand en kunt u geen proxyserver opgeven. Gebruik daarbij het volgende voorbeeld voor een opdrachtregel: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks**|      
|**-import -updatepacksrc [station:][pad]**|Met deze opdracht worden de updatepakketten en de inhoud van de console geïmporteerd die u eerder hebt gedownload naar de Configuration Manager-console.<br /><br /> Voer deze opdracht uit als **lokale beheerder** op de server waarop het serviceverbindingspunt wordt gehost.<br /><br /> Voorbeeld:  **-import -updatepacksrc D:\USB\UpdatePacks**|  
|**-export -dest [station:][pad][bestandsnaam.csv]**|Met deze opdracht exporteert u de gebruiksgegevens naar een CSV-bestand, dat u vervolgens kunt weergeven.<br /><br /> Voer deze opdracht uit als **lokale beheerder** op de server waarop het serviceverbindingspunt wordt gehost.<br /><br /> Voorbeeld: **-export -dest D:\USB\usagedata.csv**|  
