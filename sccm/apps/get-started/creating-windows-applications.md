---
title: Windows-toepassingen maken | Microsoft-documenten
description: Zie welke overwegingen die u moet ondernemen in rekening wanneer u toepassingen maken en voor Windows-apparaten implementeren.
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
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 557888d1f1f899e3198c430bbe5ccdd44178f824
ms.openlocfilehash: 9c80cc42f9ce6775067a89a9f5a63c1bf4a0c7ca
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="create-windows-applications-with-system-center-configuration-manager"></a>Windows-toepassingen maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Naast de andere vereisten voor System Center Configuration Manager en procedures voor het maken van een toepassing, moet u ook rekening met het volgende in aanmerking nemen wanneer u toepassingen maken en voor Windows-apparaten implementeren.  

## <a name="general-considerations"></a>Algemene overwegingen  
 Configuration Manager ondersteunt de volgende bestandstypen app implementeren:  

|Apparaattype|Ondersteunde bestandstypen|  
|-----------------|---------------------|  
|Windows RT en Windows RT 8.1|*.appx, \*.appxbundle|  
|Windows 8.1 en later ingeschreven als een mobiel apparaat|*.appx, \*.appxbundle|  

 De volgende implementatieacties worden ondersteund:  

|Apparaattype|Ondersteunde bewerkingen|  
|-----------------|-----------------------|  
|Windows 8.1 en hoger|beschikbaar is, vereist, verwijderen|  
|Windows RT|beschikbaar is, vereist, verwijderen|  

## <a name="support-for-universal-windows-platform-uwp-apps"></a>Ondersteuning voor UWP-apps  
 Windows 10-apparaten hoeven niet een sideloadsleutel om line-of-business-apps te installeren. Voor sideloading worden ingeschakeld, maar de registersleutel **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** moet een waarde van 1 hebben.  

 Als deze registersleutel is niet geconfigureerd, Configuration Manager deze waarde automatisch ingesteld op **1** de eerste keer dat u een app implementeert op het apparaat. Als u deze waarde hebt ingesteld op **0**Configuration Manager automatisch de waarde niet wijzigen en mislukt de implementatie van line-of-business-apps.  

 Universele Windows-Platform line-of-business-apps moeten zijn ondertekend met een certificaat voor ondertekening van programmacode dat wordt vertrouwd op elk apparaat waarop de app is geïmplementeerd. U kunt certificaten gebruiken van een interne PKI-infrastructuur of een certificaat van een openbaar basiscertificaat van derden dat op het apparaat is geïnstalleerd.  

 Op Windows 10 Mobile-apparaten kunt u een certificaat voor de ondertekening van de programmacode van andere producenten dan Symantec gebruiken voor de ondertekening van universele **.appx** -apps. Voor **.xap** -apps en **.appx** -pakketten die zijn gemaakt voor Windows Phone 8.1 en die u op Windows 10 Mobile-apparaten wilt installeren, moet u een certificaat voor de ondertekening van de programmacode van Symantec gebruiken.  

## <a name="deploy-windows-installer-apps-to-enrolled-windows-10-pcs"></a>Windows Installer-apps implementeren op ingeschreven Windows 10-computers  
 De **Windows Installer via MDM (\*.msi)** type installatieprogramma kunt u maken en implementeren van Windows Installer gebaseerde apps voor geregistreerde computers met Windows 10.  

 De volgende punten zijn van toepassing wanneer u dit type installatieprogramma gebruikt:  

-   U kunt slechts één bestand met de extensie .msi uploaden.  

-   De productcode en -versie van het bestand worden gebruikt voor detectie van de app.  

-   Het standaardgedrag van opnieuw opstarten van de app wordt gebruikt. Configuration Manager heeft dit geen controle.  

-   Pakketten worden per gebruiker MSI voor één gebruiker geïnstalleerd.  

-   MSI-pakketten zijn per computer voor alle gebruikers op het apparaat geïnstalleerd.  

-   App-updates worden ondersteund wanneer de MSI-productcode van elke versie dezelfde is.  

