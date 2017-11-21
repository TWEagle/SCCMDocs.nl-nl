---
title: Overzicht van de CNG-certificaten
titleSuffix: Configuration Manager
description: Een overzicht van de CNG-certificaten in Configuration Manager
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.openlocfilehash: f5f5138270d4f14b76b2c41e41ec034a0c12a932
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="cng-certificates-overview"></a>Overzicht van de CNG-certificaten
<!-- 1356191 --> 

Configuration Manager biedt beperkte ondersteuning voor cryptografie: Volgende Generation (CNG)-certificaten. Configuration Manager-clients kunnen PKI-clientverificatiecertificaat met persoonlijke sleutel in CNG Sleutelarchiefprovider (KSP) gebruiken. Met ondersteuning voor KSP ondersteuning Configuration Manager-clients voor op hardware gebaseerde persoonlijke sleutel, zoals TPM KSP voor PKI-verificatie van clientcertificaten.

## <a name="supported-scenarios"></a>Ondersteunde scenario's
U kunt [Cryptography API: Next Generation (CNG)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) certificaatsjablonen voor de volgende scenario's:

- Clientregistratie en -communicatie met een HTTPS-beheerpunt.   
- Software distributie en het application-implementatie met een HTTPS-distributiepunt.   
- Implementatie van besturingssysteem.  
- Messaging-SDK (met de laatste update) en ISV-Proxy-client.   
- Cloud Management Gateway-configuratie.  

> [!NOTE]
> CNG is achterwaarts compatibel met de Crypto-API (CAPI). CAPI certificaten nog steeds worden ondersteund, zelfs wanneer de CNG-ondersteuning is ingeschakeld op de client.

## <a name="unsupported-scenarios"></a>Niet-ondersteunde scenario's

De volgende scenario's worden momenteel niet ondersteund:

- Application Catalog-webservice, Application Catalog-website, inschrijvingspunt en inschrijvingsproxypunt Wijs rollen is niet operationeel wanneer geïnstalleerd in de modus van HTTPS met een CNG-certificaat dat is gebonden aan de website in Internet Information Services (IIS). Toepassingen en pakketten als beschikbaar die zijn geïmplementeerd voor gebruiker of groep gebruikersverzamelingen weergegeven software Center niet.

- Statusmigratiepunt is niet operationeel bij installatie in HTTPS-modus met een CNG-certificaat dat is gebonden aan de website in IIS.

- CNG-certificaten gebruiken voor het maken van een Clouddistributiepunt.

- NDES Policy Module certificaat registratie punt (CRP) communicatie tussen mislukt als de NDES Policy Module maakt gebruik van een CNG-certificaat voor het certificaat voor clientverificatie.

- Maken van de taak media mislukt voor het maken van opstartbare media als een CNG-certificaat is opgegeven.

## <a name="to-use-cng-certificates"></a>CNG-certificaten te gebruiken

CNG om certificaten te gebruiken, moet uw certificeringsinstantie (CA) voor de certificaatsjablonen CNG voor target-machines. Sjabloondetails variëren afhankelijk van het scenario; de volgende eigenschappen zijn echter vereist:

- **Compatibiliteit** tabblad

    - **Certificeringsinstantie** moet WindowsServer 2008 of hoger. (Windows Server 2012 wordt aanbevolen).

    - **Ontvanger van certificaat** moet Windows Vista of de Server 2008 of hoger. (Windows 8 of Windows Server 2012 wordt aanbevolen).

- **Cryptografie** tabblad

    - **Providercategorie** moet **Key Storage Provider**. (vereist)

> [!NOTE]
> De vereisten voor uw omgeving of organisatie zijn anders. Neem contact op met uw expert PKI. Het belangrijkste in overweging moet nemen is dat een certificaatsjabloon moet een Key Storage Provider gebruiken om te profiteren van de CNG.

U wordt aangeraden het bouwen van de onderwerpnaam van Active Directory-informatie voor de beste resultaten. DNS-naam gebruiken voor **indeling van de onderwerpnaam** en de DNS-naam in de alternatieve onderwerpnaam opnemen. Anders moet u deze informatie opgeven wanneer het apparaat wordt ingeschreven in het certificaatprofiel.