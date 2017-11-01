---
title: Hardware-inventaris voor mobiele apparaten configureren
titleSuffix: Configuration Manager
description: Hardware-inventaris voor mobiele apparaten die zijn geregistreerd door Microsoft Intune en System Center Configuration Manager configureren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 78a0aecc-f775-451e-aa05-56377ec91b1f
caps.latest.revision: "7"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: c176955c3fcfe40f2089b84c50a982906b59f04d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-configure-hardware-inventory-for-mobile-devices-enrolled-by-microsoft-intune-and-system-center-configuration-manager"></a>Het configureren van hardware-inventaris voor mobiele apparaten die zijn geregistreerd door Microsoft Intune en System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In Configuration Manager kunt u de hardware-inventaris verzamelen op iOS, Android en Windows apparaten via de Microsoft Intune-connector. Zie voor meer informatie over het configureren van hardware-inventaris [hardware-inventarisatie in System Center Configuration Manager uitbreiden](../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 Zie voor meer informatie over het inschrijven van apparaten in Microsoft Intune [mobiele apparaten beheren met Microsoft Intune](https://technet.microsoft.com/en-us/library/dn646962.aspx).  

## <a name="hardware-inventory-for-mobile-devices"></a>Hardware-inventarisatie voor mobiele apparaten  
 De volgende tabellen worden de beschikbare inventarisklassen voor hardware-inventaris voor veelgebruikte mobiele platforms.  

 **iOS**  

|Hardware-inventarisklasse|iOS|  
|------------------------------|---------|  
|Naam|Device_ComputerSystem.DeviceName|  
|Unieke apparaat-ID|Device_ComputerSystem.UDID|  
|Serienummer|Device_ComputerSystem.SerialNumber|  
|E-mailadres|Device_Email.OwnerEmailAddress|  
|Type besturingssysteem|Niet van toepassing|  
|Versie van besturingssysteem|Device_OSInformation.OSVersion|  
|Buildversie|Niet van toepassing|  
|Primaire versie van servicepack|Niet van toepassing|  
|Secundaire versie van servicepack|Niet van toepassing|  
|Taal van besturingssysteem|Niet van toepassing|  
|Totale opslagruimte|Device_Memory.DeviceCapacity|  
|Beschikbare opslagruimte|Device_Memory.AvailableDeviceCapacity|  
|IMEI (International Mobile Equipment Identity)|Device_ComputerSystem.IMEI|  
|MEID (Mobile Equipment Identifier)|Device_ComputerSystem.MEID|  
|Fabrikant|Niet van toepassing|  
|Model|ModelName|  
|Telefoonnummer<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|Provider van abonnee|Device_ComputerSystem.SubscriberCarrierNetwork|  
|Mobiele telefoontechnologie|Device_ComputerSystem.CellularTechnology|  
|MAC-adres Wi-Fi|Device_WLAN.WiFiMAC|  

 **Android**  

> [!NOTE]  
>  **OPMERKING:** Android-inventarisklassen zijn beschikbaar wanneer de Android-bedrijfsportal-app.  

|Hardware-inventarisklasse|Android|  
|------------------------------|-------------|  
|Naam|Niet van toepassing|  
|Unieke apparaat-ID|Niet van toepassing|  
|Serienummer|Device_ComputerSystem.SerialNumber|  
|E-mailadres|Niet van toepassing|  
|Type besturingssysteem|Device_OSInformation.platform|  
|Versie van besturingssysteem|Device_OSInformation.Version|  
|Buildversie|Niet van toepassing|  
|Primaire versie van servicepack|Niet van toepassing|  
|Secundaire versie van servicepack|Niet van toepassing|  
|Taal van besturingssysteem|Niet van toepassing|  
|Totale opslagruimte|Device_Memory.StorageTotal|  
|Beschikbare opslagruimte|Device_Memory.StorageFree|  
|IMEI (International Mobile Equipment Identity)|Device_ComputerSystem.IMEI|  
|MEID (Mobile Equipment Identifier)|Niet van toepassing|  
|Fabrikant|Device_Info.Manufacturer|  
|Model|Device_Info.Model|  
|Telefoonnummer<sup>1</sup>|Device_ComputerSystem.PhoneNumber|  
|Provider van abonnee|Device_ComputerSystem.SubscriberCarrierNetwork|  
|Mobiele telefoontechnologie|Device_ComputerSystem.CellularTechnology|  
|MAC-adres Wi-Fi|Device_WLAN.WiFiMAC|  

 **Windows Phone 8/8.1**  

|Hardware-inventarisklasse|Windows Phone 8 en Windows Phone 8.1|  
|------------------------------|-------------------------------------------|  
|Naam|Device_ComputerSystem.DeviceName|  
|Unieke apparaat-ID|Device_ComputerSystem.DeviceClientID|  
|Serienummer|Niet van toepassing|  
|E-mailadres|Device_Email.OwnerEmailAddress|  
|Type besturingssysteem|Device_OSInformation.platform|  
|Versie van besturingssysteem|Device_ComputerSystem.SoftwareVersion|  
|Buildversie|Niet van toepassing|  
|Primaire versie van servicepack|Niet van toepassing|  
|Secundaire versie van servicepack|Niet van toepassing|  
|Taal van besturingssysteem|Device_OSInformation.Language|  
|Totale opslagruimte|Niet van toepassing|  
|Beschikbare opslagruimte|Niet van toepassing|  
|IMEI (International Mobile Equipment Identity)|Niet van toepassing|  
|MEID (Mobile Equipment Identifier)|Niet van toepassing|  
|Fabrikant|Device_ComputerSystem.DeviceManufacturer|  
|Model|Device_ComputerSystem.DeviceModel|  
|Telefoonnummer<sup>1</sup>|Niet van toepassing|  
|Provider van abonnee|Niet van toepassing|  
|Mobiele telefoontechnologie|Niet van toepassing|  
|MAC-adres Wi-Fi|Niet van toepassing|  

 **Windows RT**  

|Hardware-inventarisklasse|Windows RT|  
|------------------------------|----------------|  
|Naam|Device_ComputerSystem.DeviceName|  
|Unieke apparaat-ID|Device_ComputerSystem.DeviceName|  
|Serienummer|Niet van toepassing|  
|E-mailadres|Device_Email.OwnerEmailAddress|  
|Type besturingssysteem|CCM_OperatingSystem.SystemType|  
|Versie van besturingssysteem|Win32_OperatingSystem.Version|  
|Buildversie|Win32_OperatingSystem.BuildNumber|  
|Primaire versie van servicepack|Win32_OperatingSystem.ServicePackMajorVersion|  
|Secundaire versie van servicepack|Win32_OperatingSystem.ServicePackMinorVersion|  
|Taal van besturingssysteem|Niet van toepassing|  
|Totale opslagruimte|Win32_PhysicalMemory.Capacity|  
|Beschikbare opslagruimte|Win32_OperatingSystem.FreePhysicalMemory|  
|IMEI (International Mobile Equipment Identity)|Niet van toepassing|  
|MEID (Mobile Equipment Identifier)|Niet van toepassing|  
|Fabrikant|Win32_ComputerSystem.Manufacturer|  
|Model|Win32_ComputerSystem.Model|  
|Telefoonnummer<sup>1</sup>|Niet van toepassing|  
|Provider van abonnee|Niet van toepassing|  
|Mobiele telefoontechnologie|Niet van toepassing|  
|MAC-adres Wi-Fi|Win32_NetworkAdapter.MACAddress|  

 <sup>1</sup> Het telefoonnummer wordt gemaskeerd met * met uitzondering van de laatste 4 cijfers.  

 Het telefoonnummer kan alleen door de inventaris worden verzameld als er een SIM-kaart in het apparaat is geplaatst en er door de provider een telefoonnummer aan die SIM-kaart is gekoppeld.  
