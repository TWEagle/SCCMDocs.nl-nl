---
title: Grondbeginselen van het beheer van apparaten
titleSuffix: Configuration Manager
description: Informatie over het gebruik van System Center Configuration Manager om apparaten te beheren.
ms.custom: na
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bca3db9-115a-451d-8c93-f073ceefe0c7
caps.latest.revision: "6"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: b8859537bd213928df3b4388ccbedb871e43c336
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="fundamentals-of-managing-devices-with-system-center-configuration-manager"></a>Grondbeginselen van het beheer van apparaten met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager kunt beheren apparaten twee hoofdcategorieën:

-   *Clients* zijn apparaten als werkstations, laptops, servers en mobiele apparaten waarop u de Configuration Manager-clientsoftware installeert. Sommige beheerfuncties, zoals hardware-inventaris, vereist deze clientsoftware.  

-   *Beheerde apparaten* kunt opnemen *clients*, maar dit is meestal een mobiel apparaat waarop de Configuration Manager-clientsoftware niet is geïnstalleerd. Op dit type apparaat dat beheert u met behulp van Intune of het ingebouwde on-premises beheer voor mobiele apparaten in Configuration Manager.

U kunt ook groeperen en identificeren van apparaten op basis van de gebruiker, niet alleen het clienttype.

## <a name="managing-devices-with-the-configuration-manager-client"></a>Apparaten met de Configuration Manager-client beheren

Er zijn twee manieren om de clientsoftware van Configuration Manager gebruiken voor het beheren van een apparaat. De eerste manier is het apparaat in uw netwerk te detecteren en vervolgens de clientsoftware op dat apparaat implementeren. De andere manier is de clientsoftware handmatig installeren op een nieuwe computer en vervolgens moet op die computer verbinden met uw site wanneer deze lid wordt van uw netwerk. Voor het detecteren van apparaten waarop de clientsoftware niet is geïnstalleerd, moet u een of meer van de ingebouwde detectiemethoden uitvoeren. Nadat een apparaat wordt gedetecteerd, gebruikt u een van de verschillende methoden om de clientsoftware te installeren. Zie [Detectie uitvoeren voor System Center Configuration Manager](../../core/servers/deploy/configure/run-discovery.md) voor informatie over detecteren.  

 Na het detecteren van de apparaten die worden ondersteund voor de Configuration Manager-clientsoftware wordt uitgevoerd, kunt u een van de verschillende methoden gebruiken om de software te installeren. Nadat de software is geïnstalleerd en de client is toegewezen aan een primaire site, kunt u beginnen het apparaat te beheren.  Gebruikelijke installatiemethoden zijn:

 - Push-clientinstallatie.

 - Software-update-gebaseerde installatie.

 - Groep beleid.

 - Handmatige installatie op een computer.
 - Met inbegrip van de client als onderdeel van een besturingssysteeminstallatiekopie die u implementeert.  


 Nadat de client is geïnstalleerd, kunt u de taken voor het beheer van apparaten vereenvoudigen met behulp van verzamelingen. Verzamelingen zijn groepen van apparaten of gebruikers die u maakt zodat u ze als groep beheren kunt. U wilt bijvoorbeeld een toepassing mobiele apparaten installeren op alle mobiele apparaten waarmee Configuration Manager is ingeschreven. Als dit het geval is, kunt u de verzameling alle mobiele apparaten.  

 Zie de volgende onderwerpen voor meer informatie:  

-   [Kies een oplossing voor Apparaatbeheer voor System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md)  

-   [Clientinstallatiemethoden in System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md)  

-   [Inleiding op verzamelingen in System Center Configuration Manager](../../core/clients/manage/collections/introduction-to-collections.md)  

### <a name="client-settings"></a>Clientinstellingen  
 Wanneer u Configuration Manager voor het eerst installeert, worden alle clients in de hiërarchie geconfigureerd met behulp van de standaardclientinstellingen die u kunt wijzigen. De clientinstellingen omvatten configuratieopties, deze:

 -  Hoe vaak de apparaten communiceren met de site.

 -  Of de client is ingesteld voor software-updates en andere beheerbewerkingen.

 -  Hiermee wordt aangegeven of gebruikers die hun mobiele apparaten kunnen inschrijven, zodat ze wordt beheerd door Configuration Manager.  

U kunt aangepaste clientinstellingen maken en deze vervolgens toewijzen aan verzamelingen.  Leden van de verzameling zijn geconfigureerd met de aangepaste instellingen en u kunt meerdere aangepaste clientinstellingen maken die worden toegepast in de volgorde die u opgeeft (op numerieke volgorde).  Als er sprake is van conflicterende instellingen, overschrijft de instelling met het laagste volgordenummer de andere stellingen.  

Het volgende diagram toont een voorbeeld van hoe u maken en toepassen van aangepaste clientinstellingen.  

 ![Clientinstellingen](media/ClientSettings.gif)  

 Voor meer informatie over clientinstellingen, zie  
                [Clientinstellingen in System Center Configuration Manager configureren](../../core/clients/deploy/configure-client-settings.md) en [Clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).

## <a name="managing-devices-without-the-configuration-manager-client"></a>Apparaten zonder de Configuration Manager-client beheren  
 Configuration Manager ondersteunt het beheer van sommige apparaten die niet de clientsoftware hebt geïnstalleerd en niet door Intune worden beheerd. Zie voor meer informatie [mobiele apparaten beheren met on-premises infrastructuur in System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) en [mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

## <a name="user-based-management"></a>Beheer op basis van gebruiker  
 Configuration Manager ondersteunt verzamelingen van gebruikers van Active Directory Domain Services. Wanneer u een Gebruikersverzameling, kunt u software installeren op alle computers die leden van het gebruik van de verzameling. Instellen om ervoor te zorgen dat de software die u implementeert alleen worden geïnstalleerd op de apparaten die zijn opgegeven als het primaire apparaat van een gebruiker, apparaataffiniteit van gebruikers. Een gebruiker kan één of meer primaire apparaten hebben.  

 Een van de manieren dat gebruikers hun software-implementatie-ervaring kunnen beheren is via de **Software Center** clientinterface. De **Software Center** automatisch op clientcomputers wordt geïnstalleerd en wordt uitgevoerd vanaf de **Start** menu. De **Software Center** kunnen gebruikers hun eigen software beheren en de volgende taken uitvoeren:  

-   Software installeren.  

-   Automatisch software te installeren buiten kantooruren plannen.  

-   Configureren wanneer Configuration Manager software op een apparaat installeren kan.  

-   De toegangsinstellingen voor extern beheer configureren als extern beheer is ingesteld in Configuration Manager.  

-   Configureer de opties voor energiebeheer, als een beheerder deze optie stelt.  


 Een koppeling in de **Software Center** kunnen gebruikers verbinding maken met de **Application Catalog**, waar ze kunnen naar bladeren, installeren en software aanvragen. De **Application Catalog** wordt ook gebruikt voor voorkeursinstellingen configureren, mobiele apparaten wissen en wanneer deze ingesteld, geeft u een primair apparaat voor apparaataffiniteit van gebruikers.   

 Gebruikers hebben ook toegang tot de **Application Catalog** via een browser intranet of Internet-sessie.  
