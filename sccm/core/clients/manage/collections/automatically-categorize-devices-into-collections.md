---
title: Apparaten automatisch categoriseren in verzamelingen | Microsoft-documenten
description: Apparaten categoriseren in verzamelingen automatisch met System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98b038b4-1a13-4228-bdb8-a12194e32b0e
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d1b79fb091a6ae4b967d63843ae7b45a0cbeb555
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="automatically-categorize-devices-into-collections-with-system-center-configuration-manager"></a>Apparaten automatisch categoriseren in verzamelingen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Categorieën voor apparaatstuurprogramma die kunnen worden gebruikt om apparaten automatisch plaats in apparaatverzamelingen als u de Configuration Manager met Microsoft Intune gebruikt, kunt u maken. Gebruikers hebben dan aan een apparaatcategorie kiezen wanneer ze een apparaat in Intune inschrijft. U kunt een apparaatcategorie wijzigen van de Configuration Manager-console.

> [!IMPORTANT]  
    >  Deze functie werkt met de **juni 2016** release van Microsoft Intune en hoger. Zorg ervoor dat u hebt bijgewerkt naar deze versie voordat u deze procedures uitproberen.

## <a name="create-device-categories"></a>Categorieën voor apparaatstuurprogramma maken

1.  Ga naar **activa en naleving** > **overzicht** > **Apparaatverzamelingen**.
2.  Op de **Start** tabblad, in de **Apparaatverzamelingen** groep, kiest u **categorieën voor apparaatstuurprogramma beheren**.
3.  Maken, bewerken of verwijderen van categorieën.

## <a name="associate-a-collection-with-a-device-category"></a>Een verzameling koppelen aan een apparaatcategorie

Wanneer u een verzameling aan een apparaatcategorie koppelen, worden alle apparaten in deze categorie wordt toegevoegd aan de verzameling. Kan u een apparaat categorie regel toevoegen aan een ingebouwde verzameling zoals **alle systemen**.

1.  Op de **lidmaatschapsregels** tabblad van het **eigenschappen** in het dialoogvenster kiezen voor een apparaatverzameling **regel toevoegen** > **apparaat categorie regel**.
2.  In de **categorieën voor apparaatstuurprogramma Selecteer** in het dialoogvenster Selecteer een of meer categorieën voor apparaatstuurprogramma die worden toegepast op alle apparaten in de verzameling.

## <a name="change-the-category-of-a-device"></a>De categorie van een apparaat wijzigen

1.  In **activa en naleving** > **overzicht** > **apparaten**, selecteer een apparaat van de **apparaten** lijst.
2.  Op de **Start** tabblad, in de **apparaat** groep, kiest u **Wijzigingscategorie**.
3.  Kies een categorie en kies vervolgens **OK**.

## <a name="view-which-category-a-device-belongs-to"></a>Welke deel uitmaakt van een apparaat op categorie weergeven

In **activa en naleving** > **overzicht** > **apparaten**in de **apparaten** lijst, de categorie wordt weergegeven in de **apparaatcategorie** kolom.

Als de **apparaatcategorie** kolom niet wordt weergegeven, met de rechtermuisknop op de kop van een van de kolommen in de **apparaten** lijst (zoals **naam**), en selecteer vervolgens **apparaatcategorie**.

Als u een apparaat aan een categorie toewijzen en vervolgens verwijdert de categorie, aan het rapport **lijst van apparaten die zijn geregistreerd per gebruiker in Microsoft Intune** , ziet u een GUID in de **apparaatcategorie** kolom, in plaats van een categorienaam in.

