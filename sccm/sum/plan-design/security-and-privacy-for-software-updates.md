---
title: Beveiliging en privacy voor software-updates | Microsoft Docs
description: Volg deze best practices voor beveiliging voor software-updates en meer informatie over hoe Configuration Manager privacy-informatie verwerkt.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 41d6d5d8-ba84-4efb-b105-4d1eed239824
ms.openlocfilehash: 4b4f045138abc14b6e93b3b990c5f3a8b4f2f952
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-software-updates-in-system-center-configuration-manager"></a>Beveiliging en privacy voor software-updates in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat beveiligings- en privacy-informatie voor software-updates in System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Aanbevolen beveiligingsprocedures voor software-updates  
 Gebruik de volgende aanbevolen beveiligingsprocedures wanneer u software-updates implementeert op clients:  

-   Zorg dat u de standaardmachtigingen voor software-updatepakketten niet wijzigt.  

     Software-updatepakketten worden standaard zodanig ingesteld dat beheerders **Volledig beheer** hebben en gebruikers de toegang **Lezen** hebben. Als u deze machtigingen wijzigt, kunnen kwaadwillende personen hierdoor mogelijk software-updates toevoegen of verwijderen.  

-   Beheer de toegang tot de downloadlocatie voor software-updates.  

     De computeraccounts voor de SMS-provider, de siteserver en de gebruiker met beheerdersrechten die de software-updates daadwerkelijk downloadt naar de downloadlocatie, hebben de toegang **Schrijven** nodig voor de downloadlocatie. Beperk de toegang tot de downloadlocatie om het risico te beperken dat kwaadwillende personen knoeien met de bronbestanden van software-updates op de downloadlocatie.  

     Als u bovendien een UNC-share gebruikt voor de downloadlocatie, beveiligt u het netwerkkanaal door IPsec of SMB-ondertekening te gebruiken om te voorkomen dat er wordt geknoeid met de bronbestanden van software-updates wanneer deze via het netwerk worden overgedragen.  

-   Gebruik UTC om implementatietijden te evalueren.  

     Als u de lokale tijd gebruikt in plaats van UTC, kunnen gebruikers mogelijk de installatie van software-updates vertragen door de tijdzone op hun computers te wijzigen.  

-   Schakel SSL op Windows Server Update Services (WSUS) in en volg de aanbevolen procedures om WSUS te beveiligen.  

     Bepaal en volg de aanbevolen beveiligingsprocedures voor de versie van WSUS die u met Configuration Manager gebruiken.  

    > [!IMPORTANT]  
    >  Als u het software-updatepunt zodanig configureert dat SSL-communicatie voor de WSUS-server wordt ingeschakeld, moet u virtuele roots voor SSL configureren op de WSUS-server.  

-   Schakel CRL-controle in.  

     Configuration Manager controleert standaard niet de certificaatintrekkingslijst (CRL) om te controleren of de handtekening van software-updates voordat ze worden geïmplementeerd op computers. Door de CRL te raadplegen elke keer dat er een certificaat wordt gebruikt, bent u beter beschermd tegen het gebruik van een ingetrokken certificaat. Hierdoor ontstaat echter ook een vertraging in de verbinding en vinden er extra verwerkingsactiviteiten plaats op de computer die de CRL-controle uitvoert.  

     Voor meer informatie over het inschakelen van CRL-controle voor software-updates, Zie [het inschakelen van CRL-controle voor software-updates in System Center Configuration Manager](../get-started/manage-settings-for-software-updates.md#crl-checking-for-software-updates).  

-   Configureer WSUS voor het gebruik van een aangepaste website.  

     Wanneer u WSUS installeert op het software-updatepunt, kunt u kiezen of u de bestaande standaardwebsite van IIS wilt gebruiken of een aangepaste WSUS-website wilt maken. Maak een aangepaste website voor WSUS, zodat de WSUS-services in een speciale virtuele website in plaats van dezelfde website die wordt gebruikt door de andere Configuration Manager-sitesystemen of andere toepassingen delen door IIS worden gehost.  

     Zie voor meer informatie [WSUS configureren voor gebruik van een aangepaste website](plan-for-software-updates.md#BKMK_CustomWebSite).  

##  <a name="BKMK_Privacy_HardwareInventory"></a>Privacy-informatie voor software-updates  
 Bij software-updates worden uw clientcomputers gescand om te bepalen welke updates u nodig hebt. Vervolgens wordt die informatie teruggestuurd naar de sitedatabase. Tijdens het software-updates wordt kan Configuration Manager informatie verzenden tussen clients en servers die de computer en het aanmeldingsaccount identificeren.  

 Configuration Manager houdt de statusinformatie over de software-implementatieproces. Statusinformatie wordt niet versleuteld tijdens de overdracht of opslag. Statusinformatie wordt opgeslagen in de Configuration Manager-database en wordt deze verwijderd door de onderhoudstaken van de database. Er wordt geen statusinformatie verzonden naar Microsoft.  

 Het gebruik van Configuration Manager software-updates voor het installeren van software-updates op clientcomputers mogelijk onderworpen aan softwarelicentievoorwaarden voor die updates dat is gescheiden van de gebruiksrechtovereenkomst voor System Center Configuration Manager. Controleer altijd of u akkoord gaat met de licentievoorwaarden voor Software voordat u de software-updates installeert met behulp van Configuration Manager.  

 Configuration Manager software-updates niet standaard geïmplementeerd en vereist verschillende configuratiestappen voordat gegevens worden verzameld.  

 Voordat u software-updates configureert, moet u nadenken over uw privacyvereisten.  
