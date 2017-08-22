---
title: Profiel voor beveiliging en privacy-certificaat | Microsoft Docs
description: Meer informatie over de beveiliging aanbevolen procedures voor het beheren van certificaatprofielen voor gebruikers en apparaten in System Center Configuration Manager.
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3393db41-900a-44c5-b950-2d46a35a198c
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: c51787ad3fa0bdb285017cfab1ca6931afba9ea6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-certificate-profiles-in-system-center-configuration-manager"></a>Beveiliging en privacy voor certificaatprofielen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


##  <a name="security-best-practices-for-certificate-profiles"></a>Aanbevolen beveiligingsprocedures voor certificaatprofielen  
 Gebruik de volgende aanbevolen beveiligingsprocedures wanneer u certificaatprofielen beheert voor gebruikers en apparaten.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Bepaal en volg alle aanbevolen beveiligingsprocedures voor de registratieservice voor netwerkapparaten, waaronder het configureren van de website van de Registratieservice voor netwerkapparaten in Internet Information Services (IIS) om SSL te vereisen en clientcertificaten te negeren.|Zie [Network Device Enrollment Service Guidance](http://go.microsoft.com/fwlink/p/?LinkId=309016) (Richtlijnen voor de Registratieservice van netwerkapparaten) in de bibliotheek Active Directory Certificate Services-bibliotheek op TechNet.|  
|Kies bij het configureren van SCEP-certificaatprofielen de veiligste opties die door de apparaten en uw infrastructuur worden ondersteund.|Bepaal, implementeer en volg alle 'best practice' beveiligingsprocedures die voor uw apparaten en infrastructuur worden aanbevolen.|  
|Geef handmatig de gebruikersaffiniteit met apparaat op in plaats van gebruikers toe te staan hun primaire apparaat te identificeren. Zorg daarnaast dat op gebruik gebaseerde configuratie niet is ingeschakeld.|Als u op de optie **Alleen certificaatinschrijving op het primaire apparaat van gebruikers toestaan** in een SCEP-certificaatprofiel klikt, moet u de informatie die van gebruikers of van het apparaat wordt verzameld niet als gezaghebbend beschouwen. Als u SCEP-certifcaatprofielen bij deze configuratie implementeert en een vertrouwde gebruiker met beheerdersrechten geeft de gebruikersaffiniteit met apparaat niet op, dan kunnen onbevoegde gebruikers verhoogde bevoegdheden krijgen en kunnen certificaten worden verleend voor verificatie.<br /><br /> **Opmerking:** Als u op gebruik gebaseerde configuratie inschakelt toch, wordt deze informatie verzameld via statusberichten die niet beveiligd zijn door System Center Configuration Manager. Gebruik om deze dreiging te voorkomen, SMB-ondertekening of IPsec tussen clientcomputers en het beheerpunt.|  
|Voeg geen lees- en registratiemachtigingen toe aan de certificaatsjablonen of configureer het certificaatregistratiepunt om de certificaatsjablooncontrole over te slaan.|Hoewel Configuration Manager de aanvullende controle ondersteunt als u de beveiligingsmachtigingen lezen en inschrijven voor gebruikers toevoegt en u dat het certificaatregistratiepunt configureren kunt voor deze controle overslaan als verificatie niet mogelijk is, is geen van beide configuraties aanbevolen beveiligingsprocedure. Voor meer informatie, zie [Certificaatsjabloonmachtigingen voor certificaatprofielen plannen in System Center Configuration Manager](../../protect/plan-design/planning-for-certificate-template-permissions.md).|  

## <a name="privacy-information-for-certificate-profiles"></a>Privacyinformatie voor certificaatprofielen  
 U kunt certificaatprofielen gebruiken om de basiscertificeringsinstantie (CA) en clientcertificaten te implementeren en om te evalueren of die apparaten compatibel zijn nadat de profielen zijn toegepast. Het beheerpunt compatibiliteitsinformatie wordt verzonden naar de siteserver en System Center Configuration Manager slaat die informatie in de sitedatabase. Compatibiliteitsinformatie omvat certificaateigenschappen zoals onderwerpnaam en vingerafdruk. De informatie wordt versleuteld wanneer apparaten deze naar het beheerpunt verzenden, maar deze wordt niet in een versleutelde indeling opgeslagen in de sitedatabase. De informatie wordt in de database behouden totdat deze door de siteonderhoudstaak **Verouderde gegevens van Configuration Manager verwijderen** na de standaardintervaltijd van 90 dagen wordt verwijderd. U kunt het verwijderingsinterval configureren. Er wordt geen compatibiliteitsinformatie naar Microsoft verzonden.  

 Certificaat certificaatprofielen gebruiken informatie die Configuration Manager worden verzameld met behulp van detectie. Zie de sectie **Privacyinformatie voor detectie** in [Beveiliging en privacy voor System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md)voor meer informatie over de detectie van privacygegevens.  

> [!NOTE]  
>  Aan gebruikers of apparaten uitgegeven certificaten staan mogelijk toegang toe tot vertrouwelijke informatie.  

 Standaard worden certificaatprofielen niet door apparaten geëvalueerd. Bovendien moet u de certificaatprofielen configureren en vervolgens implementeren voor gebruikers of apparaten.  

 Voordat u certificaatprofielen configureert, moet u nadenken over uw privacyvereisten.  
