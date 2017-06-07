---
title: Beheren van clients op het Internet - Configuration Manager | Microsoft-documenten
description: Meer informatie over het beheren van clients met cloud management gateway en clientbeheer op Internet gebaseerde in Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 1b6752be448e1062c97a3225db4fa8af9f4832a6
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Clients op het Internet met Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In Configuration Manager, de meeste computers en servers die worden beheerd zijn meestal fysiek op dezelfde interne persoonlijke of zakelijke netwerk bevinden als de sitesysteemservers die beheerfuncties uitvoeren. U kunt echter clientcomputers buiten uw bedrijfsnetwerk beheren als ze met het Internet verbonden zijn zonder dat de clients via virtuele particuliere netwerken te bereiken van de site systeemservers te verbinden.

Configuration Manager biedt twee manieren om verbonden met Internet-clients te beheren:

-   Cloud management gateway

-   Clientbeheer via internet

## <a name="cloud-management-gateway"></a>Cloud management gateway

Vanaf versie 1610, introduceert Configuration Manager cloud management gateway. Deze nieuwe methode biedt een manier voor het beheren van clients via Internet met behulp van een combinatie van een cloudservice die is geïmplementeerd voor Microsoft Azure en een nieuwe sitesysteemrol die met de service communiceert. De service clients vervolgens gebruiken om te communiceren met Configuration Manager.

Voordelen:

-   Er zijn geen extra infrastructuur investeringen vereist.

-   Maakt de on-premises infrastructuur met het Internet niet beschikbaar.

-   Cloud virtuele machines die uitvoeren van de service volledig worden beheerd door Azure en vereisen geen onderhoud.

-   Eenvoudig installeren en configureren in de Configuration Manager-console.

Nadelen:

-   Cloud abonnement kosten.

-   Van beheergegevens die worden verzonden via cloudservice.

Zie voor meer informatie [plannen voor cloud management gateway](plan-cloud-management-gateway.md).

## <a name="internet-based-client-management"></a>Clientbeheer via internet

Deze methode is gebaseerd op Internet facing sitesysteemservers waarop clients voor beheer communiceren. Deze methode is vereist voor clients en sitesysteemservers worden geconfigureerd voor Internet-gebaseerd beheerpunt.

Voordelen:

-   Er is geen cloud service-afhankelijkheid.

-   Er zijn geen extra kosten die zijn gekoppeld aan een cloud-abonnement.

-   Volledig beheer over servers en functies die de service levert.

Nadelen:

-   Extra infrastructuur investering vereisen.

-   Overhead en operationele kosten van extra infrastructuur.

-   Infrastructuur moet worden weergegeven met het Internet.

Zie voor meer informatie [plannen voor clientbeheer via Internet](plan-internet-based-client-management.md).
