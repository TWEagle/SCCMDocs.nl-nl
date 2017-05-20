---
title: De grondbeginselen van het beheer van apparaten | Microsoft-documenten
description: Informatie over het gebruik van System Center Configuration Manager om apparaten te beheren.
ms.custom: na
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bca3db9-115a-451d-8c93-f073ceefe0c7
caps.latest.revision: 6
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 45d84122a86da880268c93ecd994250df6b76c8a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-managing-devices-with-system-center-configuration-manager"></a>Grondbeginselen van het beheer van apparaten met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager kunt twee soorten apparaten te beheren:

-   *Clients* zijn apparaten als werkstations, laptops, servers en mobiele apparaten waarop u de Configuration Manager-clientsoftware installeren. Sommige beheerfuncties, zoals hardware-inventaris, moeten deze clientsoftware.  

-   *Beheerde apparaten* kunt opnemen *clients*, maar meestal is een mobiel apparaat waarop de Configuration Manager-clientsoftware is geïnstalleerd. Op dit type apparaat beheren u met behulp van Intune of het beheer van de ingebouwde lokale mobiele apparaten in Configuration Manager.

U kunt ook groeperen en apparaten op basis van de gebruiker, niet alleen het clienttype identificeren.

## <a name="managing-devices-with-the-configuration-manager-client"></a>Apparaten met de Configuration Manager-client beheren

Er zijn twee manieren om de clientsoftware van Configuration Manager gebruiken voor het beheren van een apparaat. De eerste manier is het apparaat in uw netwerk te detecteren en de clientsoftware vervolgens implementeert op dit apparaat. De andere manier is voor de clientsoftware handmatig installeren op een nieuwe computer en vervolgens hebben die computer lid worden van uw site bij het samenvoegen van uw netwerk. Om apparaten te detecteren waarop de clientsoftware is geïnstalleerd, moet u een of meer van de ingebouwde detectiemethoden uitvoeren. Nadat een apparaat wordt gedetecteerd, gebruikt u een van de verschillende methoden om de clientsoftware te installeren. Zie [Detectie uitvoeren voor System Center Configuration Manager](../../core/servers/deploy/configure/run-discovery.md) voor informatie over detecteren.  

 Na het detecteren van de apparaten die worden ondersteund om uit te voeren van de Configuration Manager-clientsoftware, kunt u een van de verschillende methoden om de software te installeren. Nadat de software is geïnstalleerd en de client is toegewezen aan een primaire site, kunt u beginnen het apparaat te beheren.  Algemene installatiemethoden omvatten:

 - Push-clientinstallatie.

 - Software-update-gebaseerde installatie.

 - Groep beleid.

 - Handmatige installatie op een computer.
 - Met inbegrip van de client als onderdeel van een installatiekopie die u implementeert.  


 Nadat de client is geïnstalleerd, kunt u de taken voor het beheer van apparaten vereenvoudigen met behulp van verzamelingen. Verzamelingen zijn groepen van apparaten of gebruikers die u maakt zodat u ze als een groep kunt beheren. U wilt bijvoorbeeld een toepassing voor mobiele apparaten installeren op alle mobiele apparaten waarmee Configuration Manager. Als dit het geval is, kunt u de verzameling alle mobiele apparaten.  

 Zie de volgende onderwerpen voor meer informatie:  

-   [Kies een oplossing voor Apparaatbeheer voor System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md)  

-   [Installatiemethoden voor clients in System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md)  

-   [Inleiding tot verzamelingen in System Center Configuration Manager](../../core/clients/manage/collections/introduction-to-collections.md)  

### <a name="client-settings"></a>Clientinstellingen  
 Wanneer u Configuration Manager voor het eerst installeert, worden alle clients in de hiërarchie geconfigureerd met behulp van de standaardclientinstellingen die u kunt wijzigen. De clientinstellingen omvatten configuratieopties, deze:

 -  Hoe vaak de apparaten communiceren met de site.

 -  Of de client is ingesteld voor software-updates en andere beheerbewerkingen.

 -  Of gebruikers die hun mobiele apparaten kunnen inschrijven, zodat ze worden beheerd door Configuration Manager.  

U kunt aangepaste clientinstellingen maken en deze vervolgens toewijzen aan verzamelingen.  Leden van de verzameling zijn geconfigureerd met aangepaste instellingen en u kunt meerdere aangepaste clientinstellingen maken die worden toegepast in de volgorde die u opgeeft (met de numerieke volgorde).  Als er sprake is van conflicterende instellingen, overschrijft de instelling met het laagste volgordenummer de andere stellingen.  

Het volgende diagram toont een voorbeeld van hoe u maken en toepassen van aangepaste clientinstellingen.  

 ![Clientinstellingen](media/ClientSettings.gif)  

 Voor meer informatie over clientinstellingen, zie  
                [Clientinstellingen in System Center Configuration Manager configureren](../../core/clients/deploy/configure-client-settings.md) en [Clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).

## <a name="managing-devices-without-the-configuration-manager-client"></a>Apparaten zonder de Configuration Manager-client beheren  
 Configuration Manager ondersteunt het beheer van enkele apparaten die niet de clientsoftware hebt geïnstalleerd en niet worden beheerd door Intune. Zie voor meer informatie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) en [mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

## <a name="user-based-management"></a>Beheer op basis van gebruiker  
 Configuration Manager biedt ondersteuning voor verzamelingen van gebruikers van Active Directory Domain Services. Wanneer u een Gebruikersverzameling, kunt u software installeren op alle computers die leden van het gebruik van de verzameling. Instellen om ervoor te zorgen dat de software die u wilt implementeren enkel wordt geïnstalleerd op de apparaten die worden opgegeven als het primaire apparaat van een gebruiker, apparaataffiniteit van gebruikers. Een gebruiker kan één of meer primaire apparaten hebben.  

 Een van de manieren dat gebruikers hun ervaring van de implementatie van software kunnen bepalen is met de **Software Center** clientinterface. De **Software Center** wordt automatisch geïnstalleerd op clientcomputers wordt geïnstalleerd en wordt uitgevoerd vanaf de **Start** menu. De **Software Center** kiest, kunnen gebruikers hun eigen software beheren en de volgende taken uitvoeren:  

-   Software installeren.  

-   Automatisch software te installeren buiten kantooruren plannen.  

-   Configureren wanneer de Configuration Manager software kan installeren op een apparaat.  

-   De toegangsinstellingen voor extern beheer configureren als beheer op afstand is ingesteld in Configuration Manager.  

-   Opties voor energiebeheer configureren als een beheerder deze optie stelt.  


 Een koppeling in de **Software Center** kiest, kunnen gebruikers verbinding maken met de **Application Catalog**, waar ze kunnen bladeren voor installeren en software kunnen aanvragen. De **Application Catalog** wordt ook gebruikt voor voorkeursinstellingen configureren, mobiele apparaten wissen en wanneer deze ingesteld, geeft u een primair apparaat voor affiniteit tussen gebruikers en apparaten.   

 Gebruikers hebben ook toegang tot de **Application Catalog** via een browser intranet of Internet-sessie.  

