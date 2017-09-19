---
title: Clients op het Internet - Configuration Manager beheren | Microsoft Docs
description: Meer informatie over het beheren van clients met cloud management gateway en clientbeheer op Internet gebaseerde in Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: d9dbe4e7242e2506d25b47a31982c815209c68a1
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2017
---
# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Clients op het Internet met Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In Configuration Manager de meeste computers en servers die worden beheerd zijn meestal fysiek op hetzelfde interne persoonlijke of zakelijke netwerk als de sitesysteemservers die beheerfuncties uitvoeren. U kunt echter clientcomputers buiten uw bedrijfsnetwerk beheren als ze zijn verbonden met Internet zonder dat de clients verbinding maken via virtuele particuliere netwerken systeemservers van de site bereiken.

Configuration Manager biedt twee manieren om verbonden met Internet-clients te beheren:

-   Beheergateway cloud

-   Clientbeheer via internet

## <a name="cloud-management-gateway"></a>Beheergateway cloud

Vanaf versie 1610, introduceert Configuration Manager cloud management gateway. Deze nieuwe methode biedt een manier voor het beheren van clients op Internet met een combinatie van een cloudservice die is geïmplementeerd voor Microsoft Azure en een nieuwe sitesysteemrol die met die service communiceert. De service clients vervolgens gebruiken om te communiceren met Configuration Manager.

Voordelen:

-   Er zijn geen extra infrastructuur investeringen vereist.

-   Maakt de on-premises infrastructuur met het Internet niet beschikbaar.

-   Cloud virtuele machines die worden uitgevoerd van de service volledig door Azure worden beheerd en geen onderhoud nodig.

-   Eenvoudig instellen en geconfigureerd in de Configuration Manager-console.

Nadelen:

-   Kosten voor een cloud.

-   Beheergegevens via cloudservice verzonden.

Zie voor meer informatie [plannen voor cloud-beheergateway](plan-cloud-management-gateway.md).

## <a name="internet-based-client-management"></a>Clientbeheer via internet

Deze methode is gebaseerd op Internet gerichte sitesysteemservers waarop clients voor beheerdoeleinden communiceren. Deze methode is vereist voor clients en sitesysteemservers worden geconfigureerd voor Internet-gebaseerd beheerpunt.

Voordelen:

-   Er is geen cloud service-afhankelijkheid.

-   Kan zonder extra kosten die zijn gekoppeld aan een cloud-abonnement.

-   Volledig beheer van servers en functies die de service levert.

Nadelen:

-   Vereist extra infrastructuur investering.

-   Overhead en operationele kosten van extra infrastructuur.

-   Infrastructuur moet worden blootgesteld aan Internet.

Zie voor meer informatie [plannen voor clientbeheer op Internet](plan-internet-based-client-management.md).
