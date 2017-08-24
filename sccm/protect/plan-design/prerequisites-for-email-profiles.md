---
title: Vereisten voor e-mailprofielen | Microsoft Docs
description: Meer informatie over e-mailprofielen in System Center Configuration Manager en de bijbehorende afhankelijkheden zowel extern als binnen het product.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dccf0b73-43bd-4545-8914-114168ebad36
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 451317db1d7aab888c03d1a099b9ce25311e06d0
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="email-profile-prerequisites"></a>E-mailprofiel vereisten

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

E-mailprofielen in System Center Configuration Manager hebben zowel extern als binnen het product afhankelijkheden.  

## <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Er moeten specifieke beveiligingsmachtigingen worden verleend om e-mailprofielen te beheren|U hebt de volgende beveiligingsmachtigingen nodig voor het beheren van toegangsinstellingen voor bedrijfsbronnen, zoals e-mailprofielen:<br /><br /> -Om te bekijken en beheren van waarschuwingen en rapporten voor e-mailprofielen: **Maak**, **verwijderen**, **wijzigen**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** machtigingen voor de **waarschuwingen** object.<br /><br /> -Te maken en beheren van certificaatprofielen: **Auteursbeleid**, **rapport wijzigen**, **lezen** en **rapport uitvoeren** machtigingen voor de **Certificaatprofiel** object.<br /><br /> -Voor het e-mailprofielimplementaties beheren: **Configuratiebeleid toepassen**, **waarschuwing voor wijzigen clientstatus**, **lezen**, en **Resource lezen** machtigingen voor de **verzameling** object.<br /><br /> -Voor alle configuratiebeleidsregels beheren: **Maak**, **verwijderen**, **wijzigen**, **lezen** en **beveiligingsbereik instellen** machtigingen voor de **configuratiebeleid** object.<br /><br /> -Query's worden uitgevoerd die zijn gerelateerd aan het e-mailprofielen: **Lees** machtiging voor de **Query** object.<br /><br /> -E-mailprofielen om informatie te bekijken in de System Center Configuration Manager-console: **Lees** machtiging voor de **Site** object.<br /><br /> -Voor de statusberichten voor e-mailprofielen weergeven: **Lees** machtiging voor de **statusberichten** object.<br /><br /> -Te maken en beheren van e-mailprofielen: **Auteursbeleid**, **rapport wijzigen**, **lezen**, en **rapport uitvoeren** machtigingen voor de **profiel communicatie-inrichting** object.<br /><br /> De **toegang tot bedrijfsbronnen** beveiligingsrol bevat deze machtigingen die vereist zijn voor het beheren van e-mailprofielen in System Center Configuration Manager. Zie [Beveiliging configureren in System Center Configuration Manager](../../core/plan-design/security/configure-security.md) voor meer informatie.|  
|Kenmerk mail in Active Directory|Als u wilt genereren de gebruikers e-mailadres in een e-mailprofiel met behulp van het primaire SMTP-adres van de gebruiker, detectie van System Center Configuration Manager-gebruiker moet worden geconfigureerd voor het detecteren van de **mail** kenmerk uit Active Directory (dit is standaard geconfigureerd).|  

## <a name="external-dependencies"></a>Externe afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Kenmerk mail in Active Directory|Als u wilt genereren op de gebruikers e-mailadres in een e-mailprofiel met behulp van het primaire SMTP-adres van de gebruiker, moet dit adres aanwezig de **mail** kenmerk in Active Directory.<br /><br /> Raadpleeg de Windows Server-documentatie voor meer informatie.|
