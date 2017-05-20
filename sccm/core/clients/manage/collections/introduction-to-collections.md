---
title: Verzamelingen Inleiding | Microsoft-documenten
description: Een inleiding tot het gebruik van verzamelingen in System Center Configuration Manager opgehaald.
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d17e1188-d277-438f-9236-db9cd213b421
caps.latest.revision: 8
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 547d231d48ccbc8241e9f1f8f71e3750b266b73e
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-collections-in-system-center-configuration-manager"></a>Inleiding op verzamelingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Verzamelingen kunnen u resources indelen in eenheden. Kunt u verzamelingen aan de behoeften van uw client management en bewerkingen van meerdere resources in één keer uitvoeren. 

De meeste beheertaken zijn afhankelijk van of vereist een of meer verzamelingen. Hoewel u de ingebouwde verzameling alle systemen gebruiken kunt, wordt het niet aanbevolen voor beheertaken. Aangepaste verzamelingen zodanig meer identificeert de apparaten of gebruikers voor een taak maken.  

 Ingebouwde en aangepaste verzamelingen worden weergegeven in de **Gebruikersverzamelingen** en **Apparaatverzamelingen** knooppunten in de **activa en naleving** werkruimte in de Configuration Manager-console.  

 Verzamelingen die u onlangs hebt bekeken worden weergegeven in de **gebruikers** knooppunt en klik in de **apparaten** knooppunt in de **activa en naleving** werkruimte.  

Hier volgen enkele voorbeelden van het gebruik van de verzameling:  

|Bewerking|Voorbeeld|  
|---------|-------|  
|Groeperen van resources|U kunt verzamelingen die groep resources op basis van de hiërarchie van uw organisatie kunt maken.<br /><br /> Bijvoorbeeld, kunt u maken een verzameling van alle computers in de "Londen hoofdkantoor" Active Directory organisatie-eenheid (OE). Zie voor meer informatie over het maken van dit type verzameling [het maken van verzamelingen in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).<br /><br /> U kunt deze verzameling voor bewerkingen zoals het Endpoint Protection-instellingen configureren, het configureren van instellingen voor energiebeheer apparaat of de Configuration Manager-client installeert.|  
|[Toepassingsimplementatie]|U kunt een verzameling van alle computers die niet zijn van Microsoft Office 2013 is geïnstalleerd en vervolgens implementeren op alle computers in die verzameling kunt maken.<br /><br /> U kunt ook toepassingsvereisten gebruiken om deze taak uit te voeren. Zie [Toepassingen maken met System Center Configuration Manager](../../../../apps/deploy-use/create-applications.md) voor meer informatie.|  
|[Clientinstellingen beheren](../../../../core/clients/deploy/about-client-settings.md)|Hoewel de standaardclientinstellingen in Configuration Manager van toepassing zijn op alle apparaten en gebruikers, kunt u aangepaste clientinstellingen maken die van toepassing zijn op een verzameling apparaten of een verzameling gebruikers.<br /><br /> Als u extern beheer alleen beschikbaar op alle maar enkele apparaten wilt, bijvoorbeeld de standaardclientinstellingen voor extern beheer toestaan en configureer vervolgens de aangepaste clientinstellingen die niet extern beheer toestaan en implementeren die aan de verzameling van uitzonderlijke clients configureren. |  
|[Energiebeheer](../power/introduction-to-power-management.md)|U kunt specifieke energie-instellingen per verzameling configureren.|  
|[Op rollen gebaseerd beheer](../../../../core/servers/deploy/configure/configure-role-based-administration.md)|Gebruik verzamelingen om te bepalen welke groepen van gebruikers toegang tot verschillende functies in de Configuration Manager-console hebben.|  
|[Onderhoudsvensters](../../../../core/clients/manage/collections/use-maintenance-windows.md)|U kunt een bepaalde periode wanneer verschillende bewerkingen in Configuration Manager kunnen worden uitgevoerd op leden van een apparatenverzameling definiëren met onderhoudsvensters. |  


## <a name="collection-types-in-configuration-manager"></a>Verzamelingtypen in Configuration Manager  
 Configuration Manager beschikt over ingebouwde verzamelingen voor algemene bewerkingen en u kunt ook aangepaste verzamelingen maken.   

### <a name="built-in-collections"></a>Ingebouwde verzamelingen  
 Configuration Manager omvat standaard de volgende verzamelingen die niet kunnen worden gewijzigd.  

|**Naam van verzameling**|Beschrijving|  
|-------------------------|-----------------|  
|**Alle gebruikersgroepen**|Bevat de gebruikersgroepen die zijn gedetecteerd via detectie van Active Directory-beveiligingsgroepen.|  
|**Alle gebruikers**|Bevat de gebruikers die zijn gedetecteerd via detectie van Active Directory-gebruikers.|  
|**Alle gebruikers en gebruikersgroepen**|Bevat de verzamelingen Alle gebruikers en Alle gebruikersgroepen. Deze verzameling bevat de grootste bereik van de gebruiker en groep Gebruikersbronnen.|  
|**Alle Desktop- en Serverclients**|De server en op het bureaublad apparaten bevat die de Configuration Manager-client is geïnstalleerd. Het lidmaatschap wordt beheerd door Heartbeat-detectie.|  
|**Alle mobiele apparaten**|Bevat de mobiele apparaten die worden beheerd door Configuration Manager. Het lidmaatschap is beperkt tot de mobiele apparaten die zijn toegewezen aan een site of die zijn gedetecteerd door de Exchange Server-connector.|  
|**Alle systemen**|Bevat alle Desktop en serverclients de alle mobiele apparaten, en de verzamelingen op alle onbekende Computers en alle mobiele apparaten die zijn geregistreerd door Microsoft Intune. Deze verzameling bevat de grootste bereik van apparaatbronnen.|  
|**Alle onbekende computers**|Bevat algemene computerrecords voor meerdere computerplatforms. U kunt deze verzameling gebruiken voor het implementeren van een besturingssysteem met behulp van een takenreeks en PXE-opstartbewerking, opstartbare media of voorbereide media.|  

### <a name="custom-collections"></a>Aangepaste verzamelingen  
 Wanneer u een aangepaste verzameling in Configuration Manager maakt, het lidmaatschap van deze verzameling wordt bepaald door een of meer regels, zoals beschreven in [het maken van verzamelingen in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md). 


