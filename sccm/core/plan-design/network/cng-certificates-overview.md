---
title: Overzicht van de CNG-certificaten
titleSuffix: Configuration Manager
description: Meer informatie over ondersteuning voor Cryptography Next Generation (CNG)-certificaten voor Configuration Manager-clients en servers.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 271cc0e2753f1a65740187a4faf6875c1a018014
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="cng-certificates-overview"></a>Overzicht van de CNG-certificaten
<!-- 1356191 --> 

Configuration Manager biedt beperkte ondersteuning voor cryptografie: Volgende Generation (CNG)-certificaten. Configuration Manager-clients kunnen PKI-clientverificatiecertificaat met persoonlijke sleutel in CNG Sleutelarchiefprovider (KSP) gebruiken. Met ondersteuning voor KSP ondersteuning Configuration Manager-clients voor op hardware gebaseerde persoonlijke sleutel, zoals TPM KSP voor PKI-verificatie van clientcertificaten.

## <a name="supported-scenarios"></a>Ondersteunde scenario's
U kunt [Cryptography API: Next Generation (CNG)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) certificaatsjablonen voor de volgende scenario's:

- Clientregistratie en -communicatie met een HTTPS-beheerpunt   
- Software distributie en het application-implementatie met een HTTPS-distributiepunt   
- Implementatie van besturingssystemen  
- Client messaging-SDK (met de laatste update) en ISV-Proxy   
- De configuratie voor cloud Management Gateway  

Vanaf versie 1802 CNG-certificaten gebruiken voor de volgende serverfuncties voor HTTPS-functionaliteit: <!-- 1357314 -->   
- Beheerpunt
- Distributiepunt
- Sitesysteemrollen toevoegen
- Statusmigratiepunt     

> [!NOTE]
> CNG is achterwaarts compatibel met de Crypto-API (CAPI). CAPI certificaten nog steeds worden ondersteund, zelfs wanneer de CNG-ondersteuning is ingeschakeld op de client.

## <a name="unsupported-scenarios"></a>Niet-ondersteunde scenario's

De volgende scenario's worden momenteel niet ondersteund:

- De volgende serverfuncties zijn niet operationele bij installatie in HTTPS-modus met een CNG-certificaat dat is gebonden aan de website in Internet Information Services (IIS): 
    - Application catalog-webservice
    - Application catalog-website
    - Inschrijvingspunt  
    - Proxypunt voor inschrijving  

- Toepassingen en pakketten als beschikbaar die zijn geïmplementeerd voor gebruiker of groep gebruikersverzamelingen weergegeven software Center niet.

- CNG-certificaten gebruiken voor het maken van een Clouddistributiepunt.

- Als de NDES policy module van een CNG-certificaat voor clientverificatie gebruikmaakt, mislukt de communicatie met het certificaatregistratiepunt.

- Als u een CNG-certificaat opgeven bij het maken van takenreeksmedia, mislukt de wizard voor het maken van opstartbare media.

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