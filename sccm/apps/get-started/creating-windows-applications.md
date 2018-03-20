---
title: Windows-toepassingen maken
titleSuffix: Configuration Manager
description: Zie welke overwegingen u moet rekening account wanneer u maken en implementeren van toepassingen voor Windows-apparaten.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9181c84e-d74f-44ea-9bb9-f7805eb465fc
caps.latest.revision: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 76e421571fa96d5e9ee808ac5d61361f52c6cbe3
ms.sourcegitcommit: 52080ef1b0f9a27c123711ef274ac3ffe070e8e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2018
---
# <a name="create-windows-applications-with-system-center-configuration-manager"></a>Windows-toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Naast de andere System Center Configuration Manager-vereisten en procedures voor het maken van een toepassing, u moet ook rekening houden met de volgende overwegingen wanneer u maken en implementeren van toepassingen voor Windows-apparaten.  

## <a name="general-considerations"></a>Algemene overwegingen  
 Configuration Manager ondersteunt de volgende typen van de app-bestanden implementeren:  

|Apparaattype|Ondersteunde bestandstypen|  
|-----------------|---------------------|  
|Windows RT en Windows RT 8.1|*.appx, \*.appxbundle|  
|Windows 8.1 en later ingeschreven als een mobiel apparaat|*.appx, \*.appxbundle|  

 De volgende implementatieacties worden ondersteund:  

|Apparaattype|Ondersteunde bewerkingen|  
|-----------------|-----------------------|  
|Windows 8.1 en hoger|beschikbaar, vereist, verwijderen|  
|Windows RT|beschikbaar, vereist, verwijderen|  

## <a name="support-for-universal-windows-platform-uwp-apps"></a>Ondersteuning voor UWP-apps  
 Windows 10-apparaten vereisen geen sideloadsleutel om line-of-business-apps te installeren. Voor sideloading worden ingeschakeld, maar de registersleutel **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** moet een waarde van 1 hebben.  

 Als deze registersleutel niet is geconfigureerd, Configuration Manager deze waarde automatisch ingesteld op **1** de eerste keer dat u een app implementeert op het apparaat. Als u deze waarde hebt ingesteld op **0**, Configuration Manager automatisch de waarde kan niet worden gewijzigd en mislukt de implementatie van line-of-business-apps.  

 Universele Windows-Platform line-of-business-apps moeten zijn ondertekend met een certificaat voor ondertekening van programmacode dat wordt vertrouwd op elk apparaat waarop de app is geïmplementeerd. U kunt certificaten gebruiken van een interne PKI-infrastructuur of een certificaat van een openbaar basiscertificaat van derden dat op het apparaat is geïnstalleerd.  

 Op Windows 10 Mobile-apparaten kunt u een certificaat voor de ondertekening van de programmacode van andere producenten dan Symantec gebruiken voor de ondertekening van universele **.appx** -apps. Voor **.xap** -apps en **.appx** -pakketten die zijn gemaakt voor Windows Phone 8.1 en die u op Windows 10 Mobile-apparaten wilt installeren, moet u een certificaat voor de ondertekening van de programmacode van Symantec gebruiken.  

## <a name="deploy-windows-installer-apps-to-enrolled-windows-10-pcs"></a>Windows Installer-apps implementeren op ingeschreven Windows 10-computers  
 De **Windows Installer via MDM (\*.msi)** installatieprogrammatype kunt u maken en de Windows Installer gebaseerde apps implementeren op ingeschreven pc's waarop Windows 10 wordt uitgevoerd.  

 De volgende punten zijn van toepassing wanneer u dit type installatieprogramma gebruikt:  

-   U kunt slechts één bestand met de extensie .msi uploaden.  

-   De productcode en -versie van het bestand worden gebruikt voor detectie van de app.  

-   Het standaardgedrag voor opnieuw opstarten van de app wordt gebruikt. Configuration Manager heeft hierop geen invloed.  

-   Pakketten per gebruiker MSI worden geïnstalleerd voor één gebruiker.  

-   MSI-pakketten per computer worden geïnstalleerd voor alle gebruikers op het apparaat.  

-   App-updates worden ondersteund wanneer de MSI-productcode van elke versie dezelfde is.  
