---
title: Een servergroep service | Microsoft-documenten
description: De System Center Configuration Manager-console geeft waarschuwingen en statussen voor het bewaken van updates en naleving.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 304a83ea-0f72-437d-9688-2e6e0c7526dd
ms.translationtype: Machine Translation
ms.sourcegitcommit: af5f58dd5fe1f19d7a70cb9516af159c6682d194
ms.openlocfilehash: ae09a02dd5d67113b9a7e2ce146c844efa4caf55
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
>[!IMPORTANT]
>Dit is een voorlopige versie functie is beschikbaar in de Configuration Manager versie 1606 en versie 1610. Functies van evaluatieversies zijn opgenomen in het product voor vroege testdoeleinden in een productieomgeving, maar mogen niet worden beschouwd als gereed voor productie. U moet deze functie voor beschikbaar wilt inschakelen. Zie [Use pre-release features from updates](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease) (Functies van evaluatieversies gebruiken) voor meer informatie.


# <a name="service-a-server-group"></a>Een servergroep onderhouden

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U start in System Center Configuration Manager versie 1606, kunt u instellingen voor een verzameling om te bepalen hoeveel, welk percentage of in welke volgorde computers in de verzameling de software-updates wordt geïnstalleerd. Ook kunt u voorafgaand aan de implementatie en post-implementatie PowerShell-scripts om aangepaste acties worden uitgevoerd.

Wanneer u software-updates op een verzameling met groep-instellingen die zijn geconfigureerd implementeert, wordt de Configuration Manager bepaalt hoeveel computers in de verzameling de software-updates op elk moment kunt installeren en hetzelfde aantal implementatie vergrendelingen beschikbaar. Alleen de computers die implementatie vergrendelen wordt software-update-installatie gestart. Wanneer een implementatievergrendeling op beschikbaar is, een computer opgehaald van de implementatievergrendeling, installeert de software-updates, en vervolgens de vergrendeling implementatie als installatie van software-updates is voltooid. De implementatievergrendeling wordt vervolgens beschikbaar voor andere computers. Als een computer kan geen vergrendeling van een implementatie, kunt u handmatig alle server groep implementatie vergrendelingen voor de verzameling vrijgeven.

>[!IMPORTANT]
>Alle computers in de verzameling moet worden toegewezen aan dezelfde site.

#### <a name="to-create-a-collection-for-a-server-group"></a>Een verzameling voor een servergroep maken  
De instellingen van de server worden geconfigureerd in de eigenschappen voor een apparatenverzameling. Een groep van server-service, moeten alle leden in de verzameling worden toegewezen aan dezelfde site. Gebruik de volgende stappen uit een verzameling maken en configureren van de instellingen van de server:
1.  [Maak een apparaatverzameling](../../core/clients/manage/collections/create-collections.md) die de computers in de servergroep bevat.  

2.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**met de rechtermuisknop op de verzameling die de computers in de servergroep bevat en klik vervolgens op **eigenschappen**.  

3.  Op de **algemeen** tabblad **alle apparaten deel uitmaken van dezelfde servergroep**, en klik vervolgens op **instellingen**.  

4.  Op de **instellingen** pagina, geeft u een van de volgende instellingen:  

    -   **Toestaan dat een percentage van virtuele machines tegelijk worden bijgewerkt**: Hiermee geeft u op dat alleen een bepaald percentage van clients op elk gewenst moment worden bijgewerkt. Als bijvoorbeeld de verzameling 10 clients is en de verzameling is geconfigureerd voor het bijwerken van 30% van clients op hetzelfde moment wordt slechts 3 clients software-updates op een bepaald moment installeren.  

    -   **Toestaan dat een aantal machines tegelijk worden bijgewerkt**: Hiermee geeft u op dat alleen een bepaald aantal clients op elk gewenst moment worden bijgewerkt.  

    -   **Geef de volgorde onderhoud**: Hiermee geeft u de clients in de verzameling worden bijgewerkte één voor één opnieuw in de volgorde die u configureert. Een client installeert software-updates alleen nadat de installatie van de software-updates van de client wordt dan deze in de lijst is voltooid.  

5.  Geef op of een script vóór implementatie (knooppunt verwerkingsstop) of na de implementatie (knooppunt hervatten) script gebruiken.  

    > [!WARNING]
    > Aangepaste scripts die zijn niet door Microsoft ondertekend. Het is uw verantwoordelijkheid de integriteit van deze scripts.

    > [!TIP]  
    > Hier volgen voorbeelden dat u gebruiken kunt voor voorafgaand aan de implementatie testen en na de implementatie scripts die de huidige tijd naar een tekstbestand schrijven:  
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
    >  **Post-implementatie**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

## <a name="deploy-software-updates-to-the-server-group-and-monitor-status"></a>Software-updates implementeren voor de groep en de monitor status van de server  
U implementeren software-updates aan de verzameling van de groep server met behulp van de typische implementatieproces. Nadat u de software-updates implementeert, kunt u de implementatie van software-update in de Configuration Manager-console bewaken.
1.  [Software-updates implementeren](manually-deploy-software-updates.md) aan de verzameling van de groep server.   

2.  [De implementatie van software-update controleren](monitor-software-updates.md). Naast de standaard monitoring-weergaven voor de implementatie van software-updates, de **wachten vergrendeling** status wordt weergegeven wanneer een client wacht op zijn beurt de softwareupdates te installeren. U kunt het bestand UpdatesDeployment.log voor meer informatie bekijken.


## <a name="clear-the-deployment-locks-for-computers-in-a-server-group"></a>De vergrendelingen implementatie voor computers in een servergroep wissen  
Wanneer een computer, mislukt de vergrendeling van een implementatie, kunt u handmatig vergrendelingen alle server groep implementatie voor de verzameling. Vergrendelingen te wissen wanneer een implementatie is vastgelopen met het bijwerken van computers in de verzameling en er zijn computers die nog niet compatibel zijn.  
1.  In de **activa en naleving** werkruimte, klikt u op **Apparaatverzamelingen**, en klik op de verzameling Schakel implementatie vergrendeld.  

2.  Op de **Start** tabblad, in de **implementatie** groep, klikt u op **wissen Server groep implementatie vergrendeld**. Wanneer clients installatie van de software-updates is mislukt en voorkomen dat andere clients hun software-updates installeren, kunnen de implementatie-vergrendelingen handmatig worden gewist.  

