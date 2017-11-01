---
title: Registreren van apparaten voor hybride implementaties van gebruikers
titleSuffix: Configuration Manager
description: Meer informatie over de verschillende methoden voor het inschrijven van apparaten die eigendom zijn van gebruiker voor hybride implementaties met Configuration Manager.
ms.custom: na
ms.date: 09/08/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bdaa8a7-6a64-4b0e-b617-309dcd912c45
caps.latest.revision: "13"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 9bc0e23680ff2c7a5099938e546e50e03f998f5e
ms.sourcegitcommit: 1132886e07d0c0a87dcc7eeef4577dd8d8840023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/01/2017
---
# <a name="enroll-user-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Gebruikers apparaten inschrijven voor hybride implementaties met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Apparaten van gebruikers kunnen worden gezet om te worden beheerd door deze te registreren, een proces vaak aangeduid als 'bring your own apparaten' of gewoon 'BYOD'. Gebruikers doen dit door de installatie van de bedrijfsportal-app en meldt u zich op het apparaat (iOS-, Mac OS- en Android) of door een werk of School-account toevoegen aan het apparaat en het toevoegen aan een domein (Windows). Dit proces het apparaat inschrijft bij Intune, zodat de gebruiker toegang krijgt tot bronnen worden beheerd door Intune en Intune voor het beheren van instellingen voor bepaalde apparaten, zoals het vereisen van een PINCODE te laten.

Brengt apparaten onder beheer, als beheerder u eerst moet [beheer van mobiele apparaten instellen](setup-hybrid-mdm.md) en [inschrijving inschakelen](enable-platform-enrollment.md). Zodra de inschrijving is ingeschakeld, kunnen gebruikers hun eigen apparaten kunnen inschrijven. Zie [hoe uw eindgebruikers over Microsoft Intune opleiden](https://docs.microsoft.com/intune/end-user-educate) voor overwegingen en stappen om te delen met uw gebruikers.

Bedrijven of onderwijsinstellingen die apparaten koopt profiteert van programma's waarmee u [apparaten in Bedrijfseigendom beheren](enroll-company-owned-devices.md).
