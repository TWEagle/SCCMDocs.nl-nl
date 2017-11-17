---
title: Een servergroep onderhouden
titleSuffix: Configuration Manager
description: De System Center Configuration Manager-console biedt waarschuwingen en statussen voor het bewaken van updates en naleving.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 304a83ea-0f72-437d-9688-2e6e0c7526dd
ms.openlocfilehash: 12382015f2b673103c3c0d8fc9c0cbf29511a434
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2017
---
# <a name="service-a-server-group"></a>Een servergroep onderhouden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

>[!IMPORTANT]
>Functies van evaluatieversies zijn functies die zich in de huidige vertakking voor vroege testdoeleinden in een productieomgeving. Deze functies worden volledig ondersteund maar nog in ontwikkeling actief zijn en wijzigingen mogelijk ontvangen totdat ze worden verplaatst buiten de categorie van de voorlopige versie. U moet deze functie voor beschikbaar wilt inschakelen. Zie [Use pre-release features from updates](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease) (Functies van evaluatieversies gebruiken) voor meer informatie.

U start in System Center Configuration Manager versie 1606, kunt u instellingen servergroep voor een verzameling om te bepalen hoeveel, welk percentage of in welke volgorde computers in de verzameling de software-updates worden geïnstalleerd. U kunt ook PowerShell-scripts voor vóór en na de implementatie om aangepaste acties worden uitgevoerd.

Wanneer u software-updates op een verzameling met groep-instellingen die zijn geconfigureerd implementeert, wordt Configuration Manager bepaalt hoeveel computers in de verzameling de software-updates op elk moment kunt installeren en hetzelfde aantal vergrendelingen van servergroepimplementaties beschikbaar stelt. Alleen computers die implementatie vergrendelen wordt installatie software-update gestart. Wanneer een implementatievergrendeling beschikbaar is, een computer opgehaald van de implementatievergrendeling, installeert de software-updates, en vervolgens de vergrendeling implementatie wanneer de installatie van de software-updates is voltooid. De implementatievergrendeling wordt vervolgens beschikbaar voor andere computers. Als een computer kan geen vergrendeling van een implementatie, kunt u handmatig alle server vergrendelingen van servergroepimplementaties voor de verzameling vrijgeven.

>[!IMPORTANT]
>Alle computers in de verzameling moet worden toegewezen aan dezelfde site.

#### <a name="to-create-a-collection-for-a-server-group"></a>Een verzameling van een servergroep maken  
De instellingen van de server zijn geconfigureerd in de eigenschappen voor een apparatenverzameling. Als u wilt een servergroep onderhouden, moeten alle leden in de verzameling worden toegewezen aan dezelfde site. Gebruik de volgende stappen uit een verzameling maken en configureren van instellingen voor de server:
1.  [Maak een apparaatverzameling](../../core/clients/manage/collections/create-collections.md) die de computers in de servergroep bevat.  

2.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**, met de rechtermuisknop op de verzameling waartoe de computers in de servergroep en klik vervolgens op **eigenschappen**.  

3.  Op de **algemene** tabblad **alle apparaten zijn onderdeel van de servergroep met dezelfde**, en klik vervolgens op **instellingen**.  

4.  Op de **instellingen servergroep** pagina, geeft u een van de volgende instellingen:  

    -   **Toestaan dat een percentage van de machines tegelijk wordt bijgewerkt**: Hiermee geeft u op dat alleen een bepaald percentage van clients op elk gewenst moment worden bijgewerkt. Als bijvoorbeeld de verzameling 10 clients heeft en de verzameling is geconfigureerd voor het bijwerken van 30% bedraagt van clients op hetzelfde moment wordt alleen 3 clients software-updates op elk moment installeren.  

    -   **Toestaan dat een aantal machines tegelijk wordt bijgewerkt**: Hiermee geeft u op dat alleen een bepaald aantal clients op elk gewenst moment worden bijgewerkt.  

    -   **Geef de reeks onderhoud**: Geeft aan dat de clients in de verzameling wordt bijgewerkt één op een tijdstip in de volgorde die u configureert. Een client wordt alleen software-updates installeren nadat de installatie van de software-updates van de client wordt dan deze in de lijst is voltooid.  

5.  Geef op of een script vóór implementatie (knooppuntcorrectie) of een script ná implementatie (knooppunthervatting) wilt gebruiken.  

    > [!WARNING]
    > Aangepaste scripts niet zijn ondertekend door Microsoft. Het is uw verantwoordelijkheid om de integriteit van deze scripts te behouden.

    > [!TIP]  
    > Hier volgen voorbeelden die u gebruiken kunt bij het testen voorafgaand aan de implementatie en na de implementatie scripts die de huidige tijd naar een tekstbestand schrijven:  
    >   
    >  **Voorafgaand aan de implementatie**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Na de implementatie**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

## <a name="deploy-software-updates-to-the-server-group-and-monitor-status"></a>Software-updates implementeren voor de groep en de monitor status van de server  
U implementeren software-updates aan de verzameling van de groep server met behulp van de normale implementatie-proces. Nadat u de software-updates implementeert, kunt u de implementatie van software-update in de Configuration Manager-console kunt bewaken.
1.  [Software-updates implementeren](manually-deploy-software-updates.md) aan de verzameling van de groep server.   

2.  [De implementatie van de software-update controleren](monitor-software-updates.md). Naast de standaard monitoring-weergaven voor software-updates implementatie, de **wachten vergrendeling** status wordt weergegeven wanneer een client wacht op zijn beurt de softwareupdates te installeren. U kunt het bestand updatesdeployment.log voor meer informatie kunt bekijken.


## <a name="clear-the-deployment-locks-for-computers-in-a-server-group"></a>De implementatievergrendeling voor computers in een servergroep gewist  
Wanneer een computer, mislukt de vergrendeling van een implementatie, kunt u handmatig alle server vergrendelingen van servergroepimplementaties voor de verzameling vrijgeven. Vergrendelingen wissen wanneer een implementatie is vastgelopen met het bijwerken van computers in de verzameling en er zijn computers die nog niet compatibel zijn.  
1.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**, en klik op de verzameling om vergrendelingen van servergroepimplementaties wissen.  

2.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **wissen Server groep implementatie vergrendeld**. Wanneer clients installatie van de software-updates is mislukt en worden zo wordt voorkomen dat andere clients hun software-updates installeren, kunnen de implementatievergrendeling handmatig worden gewist.  
