---
title: Beheren van clients op het internet
titleSuffix: Configuration Manager
description: Meer informatie over het beheren van clients met cloud management gateway en clientbeheer op internet gebaseerde in Configuration Manager.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 31d43d855c1e7062e62a3d15fa5a79c4e4de915f
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Clients op het internet met Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In Configuration Manager de meeste beheerde computers en servers zijn meestal fysiek op hetzelfde interne netwerk bevinden als de sitesysteemservers die beheerfuncties uitvoeren. U kunt echter clients buiten uw interne netwerk beheren wanneer ze zijn verbonden met internet. Deze mogelijkheid nodig niet de clients verbinding maken via VPN te bereiken van de site systeemservers.

Configuration Manager biedt twee manieren om internet verbonden clients te beheren:

-   Beheergateway cloud

-   Clientbeheer via internet


## <a name="cloud-management-gateway"></a>Beheergateway cloud

De cloudgateway management biedt beheer van clients op internet. Wordt een combinatie van een cloudservice van Microsoft Azure en een nieuwe sitesysteemrol die communiceert met die service. Internet-clients gebruiken de cloudservice om te communiceren met de lokale Configuration Manager.

#### <a name="advantages"></a>Voordelen  

-   Er zijn geen extra infrastructuur investeringen vereist.  

-   Maakt de on-premises infrastructuur met het internet niet beschikbaar.  

-   Cloud virtuele machines die worden uitgevoerd van de service volledig door Azure worden beheerd en geen onderhoud nodig.  

-   Eenvoudig instellen en geconfigureerd in de Configuration Manager-console.  

#### <a name="disadvantages"></a>Nadelen  

-   Kosten voor een cloud.  

-   Beheergegevens via cloudservice verzonden.  

Zie voor meer informatie [plannen voor cloud-beheergateway](plan-cloud-management-gateway.md).  



## <a name="internet-based-client-management"></a>Clientbeheer via internet

Deze methode is gebaseerd op internet gerichte sitesysteemservers waarop clients voor beheerdoeleinden communiceren. Dit is vereist voor clients en sitesysteemservers worden geconfigureerd voor internet-gebaseerd beheerpunt.

#### <a name="advantages"></a>Voordelen  

-   Er is geen cloud service-afhankelijkheid.  

-   Kan zonder extra kosten die zijn gekoppeld aan een cloud-abonnement.  

-   Volledig beheer van servers en functies die de service levert.  

#### <a name="disadvantages"></a>Nadelen  

-   Vereist extra infrastructuur investering.  

-   Overhead en operationele kosten van extra infrastructuur.  

-   Infrastructuur moet worden blootgesteld aan internet.  

Zie voor meer informatie [plannen voor clientbeheer op internet](plan-internet-based-client-management.md).  
