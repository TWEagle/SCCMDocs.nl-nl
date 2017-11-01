---
title: Een aangepaste takenreeks maken
titleSuffix: Configuration Manager
description: Een aangepaste takenreeks in System Center Configuration Manager toevoegen van stappen aan de takenreeks bewerken.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9800a66-7541-47ca-8276-da8ef6cb6d1b
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: e25b60b64ae2ed75091c4f5b0ffa0f9eca4c6cac
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="create-a-custom-task-sequence-with-system-center-configuration-manager"></a>Een aangepaste takenreeks maken met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u een aangepaste takenreeks in System Center Configuration Manager maakt, bevat deze geen takenreeksstappen. Nadat u de takenreeks hebt gemaakt, moet u deze bewerken en de benodigde takenreeksstappen toevoegen.  

##  <a name="BKMK_CustomTS"></a> Een aangepaste takenreeks maken  
 Gebruik de volgende procedure om een aangepaste takenreeks te maken.  

#### <a name="to-create-a-custom-task-sequence"></a>Een aangepaste takenreeks maken  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw **Besturingssystemen** uit in de werkruimte **Softwarebibliotheek**en klik op **Takenreeksen**.  

3.  Klik op **Takenreeks maken** in het tabblad **Start** , in de groep **Maken** om de wizard Takenreeks maken te starten.  

4.  Selecteer **Nieuwe aangepaste takenreeks maken** op de pagina **Nieuwe takenreeks maken**.  

5.  Geef, op de pagina **Takenreeksinformatie** , een naam op voor de takenreeks, een beschrijving van de takenreeks en een optionele opstartinstallatiekopie voor gebruik door de takenreeks en voltooi vervolgens de wizard.  

 Nadat u de Wizard Takenreeks maken hebt voltooid, Configuration Manager de aangepaste takenreeks voegt de **Takenreeksen** knooppunt. U kunt deze takenreeks nu bewerken om er takenreeksstappen aan toe te voegen.  

 Zie voor een lijst met beschikbare takenreeksstappen [Takenreeksstappen](../understand/task-sequence-steps.md).  

 Zie voor meer informatie over het bewerken van een takenreeks [een takenreeks bewerken](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

 U zult takenreeksen meestal gebruiken om taken voor besturingssysteemimplementatie te automatiseren, maar u kunt een aangepaste takenreeks maken om een verscheidenheid aan taken te automatiseren. Zie voor meer informatie [een takenreeks maken voor niet - besturingssysteemimplementaties](create-a-task-sequence-for-non-operating-system-deployments.md).  

 ## <a name="next-steps"></a>Volgende stappen
 [De takenreeks implementeren](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)
