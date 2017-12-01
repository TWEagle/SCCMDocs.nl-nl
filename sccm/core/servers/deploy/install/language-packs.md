---
title: Taalpakketten
titleSuffix: Configuration Manager
description: Meer informatie over de ondersteuning voor talen die beschikbaar is in System Center Configuration Manager.
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd74e5f5-33f6-4566-8c9d-d6a93bfe71ed
caps.latest.revision: "10"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 66053ee03e118900fa4cd92e20d542a211f16856
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="language-packs-in-system-center-configuration-manager"></a>Taalpakketten in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp vindt u technische gegevens over taalondersteuning in System Center Configuration Manager.  

## <a name="BKMK_SupLanguagePacks"></a>Ondersteund besturingssysteemtalen  
 U kunt ondersteuning voor de Weergavetalen installeren in de volgende tabellen door het installeren van **servertaalpakketten** of **clienttaalpakketten** op een centrale beheersite en op primaire sites. U selecteren de server en clienttalen ter ondersteuning van op een site uit de beschikbare taalpakketbestanden tijdens het installatieproces van de site.

 Taalpakketbestanden worden gedownload wanneer u Setup als onderdeel van de vereisten en herdistribueerbare bestand downloaden uitvoert. U kunt ook gebruiken [Setup Downloader](setup-downloader.md) deze om bestanden te downloaden voordat u Setup uitvoert.   

 Gebruik de volgende tabel een landinstellingen-ID toewijzen aan een taal die u wilt ondersteunen op servers of clientcomputers. Zie voor meer informatie over landinstellingen-id [landinstellingen-id's toegewezen door Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=252609).  

### <a name="server-languages"></a>Servertalen  

|Servertaal|Landinstellingen-id (LCID)|Drieletterige code|  
|---------------------|------------------------|-----------------------|  
|Engels (standaard)|0409|ENU|  
|Chinees (Traditioneel, Hongkong SAR)|0c04|ZHH|  
|Chinees (Vereenvoudigd)|0804|CHS|  
|Chinees (Traditioneel, Taiwan)|0404|CHT|  
|Tsjechisch|0405|CSY|  
|Nederlands - Nederland|0413|NLD|  
|Frans|040c|FRA|  
|Duits|0407|DEU|  
|Hongaars|040e|HUN|  
|Italiaans - Italië|0410|ITA|  
|Japans|0411|JPN|  
|Koreaans|0412|KOR|  
|Pools|0415|PLK|  
|Portugees - Brazilië|0416|PTB|  
|Portugees - Portugal|0816|PTG|  
|Russisch|0419|RUS|  
|Spaans – Spanje|0c0a|ESN|  
|Zweeds|041d|SVE|  
|Turks|041f|TRK|  

### <a name="client-languages"></a>Clienttalen  

|Clienttaal|Landinstellingen-id (LCID)|Drieletterige code|  
|---------------------|------------------------|-----------------------|  
|Engels (standaard)|0409|ENG|  
|Chinees (Traditioneel, Hongkong SAR)|0c04|ZHH|  
|Chinees - Vereenvoudigd|0804|CHS|  
|Chinees (Traditioneel, Taiwan)|0404|CHT|  
|Tsjechisch|0405|CSY|  
|Deens|0406|DAN|  
|Nederlands - Nederland|0413|NLD|  
|Fins|040b|FIN|  
|Frans|040c|FRA|  
|Duits|0407|DEU|  
|Grieks|0408|ELL|  
|Hongaars|040e|HUN|  
|Italiaans - Italië|0410|ITA|  
|Japans|0411|JPN|  
|Koreaans|0412|KOR|  
|Noors|0414|NOR|  
|Pools|0415|PLK|  
|Portugees (Brazilië)|0416|PTB|  
|Portugees (Portugal)|0816|PTG|  
|Russisch|0419|RUS|  
|Spaans – Spanje|0c0a|ESN|  
|Zweeds|041d|SVE|  
|Turks|041f|TRK|  

### <a name="mobile-device-client-languages"></a>Clienttalen voor mobiele apparaten  
 Wanneer u ondersteuning voor talen voor mobiele apparaten toevoegt, worden alle clienttalen voor ondersteunde mobiele apparaten opgenomen. U kunt geen afzonderlijke taalpakketten selecteren voor ondersteuning op mobiele apparaten.  

### <a name="identify-installed-language-packs"></a>Geïnstalleerde taalpakketten identificeren  
Als u de taalpakketten die zijn geïnstalleerd op een computer waarop de Configuration Manager-client, kijkt u voor de landinstelling-ID (LCID) van de geïnstalleerde taalpakketten in het register van computer. Deze informatie is beschikbaar op:

 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs**  

U kunt hardware-inventarisatie gebruiken om deze informatie te verzamelen en dit vervolgens een aangepast rapport om de taaldetails te bekijken. Zie voor meer informatie over het verzamelen van aangepaste hardware-inventaris [hardware-inventaris configureren in System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md). Zie voor informatie over het maken van rapporten, de [beheren van Configuration Manager-rapporten](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md#BKMK_ManageReports) sectie het [bewerkingen en onderhoud voor rapportage in System Center Configuration Manager](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md) onderwerp.  
