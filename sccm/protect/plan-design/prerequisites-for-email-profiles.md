---
title: Vereisten voor e-mailprofielen | Microsoft-documenten
description: Meer informatie over e-mailprofielen in System Center Configuration Manager en de bijbehorende afhankelijkheden zowel extern als binnen het product.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dccf0b73-43bd-4545-8914-114168ebad36
caps.latest.revision: 5
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: 451317db1d7aab888c03d1a099b9ce25311e06d0
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="email-profile-prerequisites"></a>E-mailprofiel vereisten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

E-mailprofielen in System Center Configuration Manager hebben zowel extern als binnen het product afhankelijkheden.  

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Er moeten specifieke beveiligingsmachtigingen worden verleend om e-mailprofielen te beheren|U hebt de volgende beveiligingsmachtigingen nodig voor het beheren van toegangsinstellingen voor bedrijfsbronnen, zoals e-mailprofielen:<br /><br /> -Te bekijken en beheren van waarschuwingen en rapporten voor e-mailprofielen: **Maak**, **verwijderen**, **wijzigen**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** machtigingen voor de **waarschuwingen** object.<br /><br /> -Voor het maken en beheren van certificaatprofielen: **Auteursbeleid**, **rapport wijzigen**, **lezen** en **rapport uitvoeren** machtigingen voor de **Certificaatprofiel** object.<br /><br /> -Voor het e-mailprofielimplementaties beheren: **Configuratiebeleid toepassen**, **waarschuwing voor wijzigen clientstatus**, **lezen**, en **Resource lezen** machtigingen voor de **verzameling** object.<br /><br /> -Voor alle configuratiebeleidsregels beheren: **Maak**, **verwijderen**, **wijzigen**, **lezen** en **beveiligingsbereik instellen** machtigingen voor de **configuratiebeleid** object.<br /><br /> -Voor query's uitvoeren die gerelateerd zijn aan e-mailprofielen: **Lees** machtiging voor het **Query** object.<br /><br /> -E-mailprofielen u informatie wilt weergeven in de System Center Configuration Manager-console: **Lees** machtiging voor het **Site** object.<br /><br /> -Voor statusberichten voor e-mailprofielen weergeven: **Lees** machtiging voor het **statusberichten** object.<br /><br /> -Te maken en beheren van e-mailprofielen: **Auteursbeleid**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** machtigingen voor de **profiel communicatie-inrichting** object.<br /><br /> De **toegang tot bedrijfsbronnen** beveiligingsrol bevat deze machtigingen die vereist zijn voor het beheren van e-mailprofielen in System Center Configuration Manager. Zie [Beveiliging configureren in System Center Configuration Manager](../../core/plan-design/security/configure-security.md) voor meer informatie.|  
|Kenmerk mail in Active Directory|Als u wilt genereren gebruikers e-mailadres in een e-mailprofiel met behulp van het primaire SMTP-adres van de gebruiker, System Center Configuration Manager-gebruikersdetectie moet worden geconfigureerd voor het detecteren van de **e** kenmerk uit Active Directory (dit is standaard geconfigureerd).|  

## <a name="external-dependencies"></a>Externe afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Kenmerk mail in Active Directory|Als u wilt dat voor het genereren van de gebruikers e-mailadres in een e-mailprofiel met behulp van het primaire SMTP-adres van de gebruiker, moet dit adres aanwezig de **e** kenmerk in Active Directory.<br /><br /> Raadpleeg de Windows Server-documentatie voor meer informatie.|

