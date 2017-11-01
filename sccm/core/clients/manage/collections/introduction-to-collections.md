---
title: Inleiding voor verzamelingen
titleSuffix: Configuration Manager
description: Maak kennis met behulp van verzamelingen in System Center Configuration Manager.
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d17e1188-d277-438f-9236-db9cd213b421
caps.latest.revision: "8"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 835fbbeaf64a16b46e5a600ccf89a2a885bbf21a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="introduction-to-collections-in-system-center-configuration-manager"></a>Inleiding op verzamelingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Verzamelingen kunnen u resources te organiseren in beheerbare eenheden. U kunt verzamelingen aan de behoeften van uw client-beheer en bewerkingen uit te voeren op meerdere resources tegelijk maken. 

De meeste beheertaken zijn afhankelijk van of moeten u een of meer verzamelingen. Hoewel u de ingebouwde verzameling alle systemen gebruiken kunt, is het niet aanbevolen voor beheertaken. Maak aangepaste verzamelingen om te identificeren meer specifiek de apparaten of gebruikers voor een taak.  

 Ingebouwde en aangepaste verzamelingen worden weergegeven in de **Gebruikersverzamelingen** en **Apparaatverzamelingen** knooppunten in de **activa en naleving** werkruimte in de Configuration Manager-console.  

 Verzamelingen die u onlangs hebt bekeken worden weergegeven in de **gebruikers** knooppunt en in de **apparaten** knooppunt in de **activa en naleving** werkruimte.  

Hier volgen enkele voorbeelden van het gebruik van de verzameling:  

|Bewerking|Voorbeeld|  
|---------|-------|  
|Groeperen van resources|U kunt verzamelingen maken die resources groeperen op basis van de hiërarchie van uw organisatie.<br /><br /> Bijvoorbeeld, kunt u maken een verzameling van alle computers in de 'Londen hoofdkantoor' Active Directory organisatie-eenheid (OE). Zie voor meer informatie over het maken van dit type verzameling [verzamelingen maken in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).<br /><br /> U kunt deze verzameling voor bewerkingen, zoals Endpoint Protection-instellingen configureren, configureren van instellingen voor energiebeheer apparaat of de Configuration Manager-client installeert.|  
|[Toepassingsimplementatie]|U kunt een verzameling van alle computers die geen Microsoft Office 2013 is geïnstalleerd en vervolgens implementeren op alle computers in die verzameling kunt maken.<br /><br /> U kunt ook toepassingsvereisten gebruiken om deze taak uit te voeren. Zie [Toepassingen maken met System Center Configuration Manager](../../../../apps/deploy-use/create-applications.md) voor meer informatie.|  
|[Clientinstellingen beheren](../../../../core/clients/deploy/about-client-settings.md)|Hoewel de standaardclientinstellingen in Configuration Manager van toepassing zijn op alle apparaten en gebruikers, kunt u aangepaste clientinstellingen maken die van toepassing zijn op een verzameling apparaten of een verzameling gebruikers.<br /><br /> Als u wilt dat extern beheer alleen beschikbaar op alle slechts een paar apparaten, bijvoorbeeld de standaardclientinstellingen voor het toestaan van beheer op afstand en configureer vervolgens aangepaste clientinstellingen die niet toestaan van beheer op afstand en implementeren in de verzameling van uitzonderlijke clients configureren. |  
|[Energiebeheer](../power/introduction-to-power-management.md)|U kunt specifieke energie-instellingen per verzameling configureren.|  
|[Op rollen gebaseerd beheer](../../../../core/servers/deploy/configure/configure-role-based-administration.md)|Gebruik verzamelingen om te bepalen welke groepen gebruikers toegang tot verschillende functies in de Configuration Manager-console hebben.|  
|[Onderhoudsvensters](../../../../core/clients/manage/collections/use-maintenance-windows.md)|U kunt een bepaalde periode wanneer verschillende Configuration Manager-bewerkingen kunnen worden uitgevoerd op leden van een apparatenverzameling definiëren met onderhoudsvensters. |  


## <a name="collection-types-in-configuration-manager"></a>Verzamelingtypen in Configuration Manager  
 Configuration Manager beschikt over ingebouwde verzamelingen voor algemene bewerkingen en u kunt ook aangepaste verzamelingen maken.   

### <a name="built-in-collections"></a>Ingebouwde verzamelingen  
 Configuration Manager omvat de volgende verzamelingen kunnen niet worden gewijzigd.  

|**Naam van verzameling**|Beschrijving|  
|-------------------------|-----------------|  
|**Alle gebruikersgroepen**|Bevat de gebruikersgroepen die zijn gedetecteerd via detectie van Active Directory-beveiligingsgroepen.|  
|**Alle gebruikers**|Bevat de gebruikers die zijn gedetecteerd via detectie van Active Directory-gebruikers.|  
|**Alle gebruikers en gebruikersgroepen**|Bevat de verzamelingen Alle gebruikers en Alle gebruikersgroepen. Deze verzameling bevat het grootste bereik van de gebruikers- en gebruikersgroepresources.|  
|**Alle Desktop- en Serverclients**|Bevat de server en bureaublad-apparaten waarop de Configuration Manager-client is geïnstalleerd. Het lidmaatschap wordt beheerd door Heartbeat-detectie.|  
|**Alle mobiele apparaten**|Bevat de mobiele apparaten die worden beheerd door Configuration Manager. Het lidmaatschap is beperkt tot de mobiele apparaten die zijn toegewezen aan een site of die zijn gedetecteerd door de Exchange Server-connector.|  
|**Alle systemen**|Bevat alle Desktop en serverclients, de alle mobiele apparaten en de verzamelingen alle onbekende Computers en alle mobiele apparaten die zijn geregistreerd door Microsoft Intune. Deze verzameling bevat het grootste bereik van apparaatresources.|  
|**Alle onbekende computers**|Bevat algemene computerrecords voor meerdere computerplatforms. U kunt deze verzameling gebruiken voor het implementeren van een besturingssysteem met behulp van een takenreeks en PXE-opstartbewerking, opstartbare media of voorbereide media.|  

### <a name="custom-collections"></a>Aangepaste verzamelingen  
 Wanneer u een aangepaste verzameling in Configuration Manager maken, het lidmaatschap van deze verzameling wordt bepaald door een of meer verzamelingsregels, zoals beschreven in [verzamelingen maken in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md). 

