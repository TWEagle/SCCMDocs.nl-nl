---
title: Apparaten automatisch categoriseren in verzamelingen | Microsoft Docs
description: Apparaten categoriseren in verzamelingen automatisch met System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98b038b4-1a13-4228-bdb8-a12194e32b0e
caps.latest.revision: "5"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 0de7a3d4183fb00f444a27c45d178141dc4e9375
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="automatically-categorize-devices-into-collections-with-system-center-configuration-manager"></a>Apparaten automatisch categoriseren in verzamelingen met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt apparaatcategorieën dat kunnen worden gebruikt voor apparaten worden automatisch op apparaatverzamelingen plaatsen wanneer u van Configuration Manager met Microsoft Intune gebruikmaakt kunt maken. Gebruikers hebben vervolgens naar een apparaatcategorie kiezen wanneer ze een apparaat bij Intune inschrijven. U kunt een apparaatcategorie wijzigen via de Configuration Manager-console.

> [!IMPORTANT]  
    >  Deze mogelijkheid werkt met de **juni 2016** bij de release van Microsoft Intune en later. Zorg ervoor dat u hebt bijgewerkt naar deze versie voordat u deze procedures.

## <a name="create-device-categories"></a>Categorieën voor apparaatstuurprogramma maken

1.  Ga naar **activa en naleving** > **overzicht** > **Apparaatverzamelingen**.
2.  Op de **Start** tabblad, in de **Apparaatverzamelingen** groep, kiest u **apparaatcategorieën beheren**.
3.  Maken, bewerken of verwijderen van categorieën.

## <a name="associate-a-collection-with-a-device-category"></a>Een verzameling koppelen aan een apparaatcategorie

Als u een verzameling met een apparaatcategorie koppelt, worden alle apparaten in die categorie worden toegevoegd aan de verzameling. U kunt een categorie apparaat regel niet toevoegen aan een ingebouwde verzameling zoals **alle systemen**.

1.  Op de **lidmaatschapsregels** tabblad van de **eigenschappen** in het dialoogvenster voor een apparatenverzameling kiezen **regel toevoegen** > **apparaat categorie regel**.
2.  In de **apparaatcategorieën Selecteer** in het dialoogvenster, selecteer een of meer categorieën voor apparaatstuurprogramma die worden toegepast op alle apparaten in de verzameling.

## <a name="change-the-category-of-a-device"></a>De categorie van een apparaat wijzigen

1.  In **activa en naleving** > **overzicht** > **apparaten**, selecteer een apparaat van de **apparaten** lijst.
2.  Op de **Start** tabblad, in de **apparaat** groep, kiest u **Wijzigingscategorie**.
3.  Kies een categorie en kies vervolgens **OK**.

## <a name="view-which-category-a-device-belongs-to"></a>Welke deel uitmaakt van een apparaat op categorie weergeven

In **activa en naleving** > **overzicht** > **apparaten**, in de **apparaten** lijst, de categorie wordt weergegeven in de **apparaatcategorie** kolom.

Als de **apparaatcategorie** kolom niet wordt weergegeven, met de rechtermuisknop op de kop van een van de kolommen in de **apparaten** lijst (zoals **naam**), selecteer daarna **apparaatcategorie**.

Als u een apparaat aan een categorie toewijzen en vervolgens verwijdert de categorie, het rapport **lijst van apparaten die per gebruiker in Microsoft Intune zijn ingeschreven** , ziet u een GUID in de **apparaatcategorie** kolom, in plaats van een categorienaam in.
