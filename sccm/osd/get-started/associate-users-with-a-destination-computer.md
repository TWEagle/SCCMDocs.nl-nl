---
title: Gebruikers koppelen aan een doelcomputer
titleSuffix: Configuration Manager
description: System Center Configuration Manager als u gebruikers koppelen aan doelcomputers bij het implementeren van besturingssystemen wilt configureren.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07c3c6d9-f056-4c4d-bc70-ede5ca933807
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 4c0231057c2ac154b050cc7020eb1fbb4ed93228
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="associate-users-with-a-destination-computer-in-system-center-configuration-manager"></a>Gebruikers aan een doelcomputer koppelen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u System Center Configuration Manager gebruikt om besturingssysteem te implementeren, kunt u gebruikers kunt koppelen aan de doelcomputer waarop het besturingssysteem wordt geïmplementeerd. Deze configuratie omvat onder andere het volgende:  

-   Dat een enkele gebruiker de primaire gebruiker van de doelcomputer is.  

-   Dat meerdere gebruikers de primaire gebruikers van de doelcomputer zijn.  

 De gebruikersaffiniteit van apparaten biedt ondersteuning voor op de gebruiker gericht beheer wanneer u toepassingen implementeert. Als u een gebruiker koppelt aan de doelcomputer waarop een besturingssysteem moet worden geïnstalleerd, kunt u later toepassingen voor die gebruiker implementeren en worden de toepassingen automatisch op de doelcomputer geïnstalleerd. Hoewel u ondersteuning voor de gebruikersaffiniteit van apparaten kunt configureren wanneer u besturingssystemen implementeert, kunt u de gebruikersaffiniteit van apparaten echter niet gebruiken om besturingssystemen te implementeren.  

 Zie voor meer informatie over gebruikersapparaataffiniteit [gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

## <a name="how-to-specify-a-user-when-you-deploy-operating-systems"></a>Een gebruiker opgeven wanneer u besturingssystemen implementeert  
 In de volgende tabel ziet u de acties die u kunt ondernemen om de gebruikersaffiniteit van apparaten te integreren in implementaties van besturingssystemen. U kunt de gebruikersaffiniteit van apparaten integreren in PXE-implementaties, implementaties met opstartbare media en implementaties met voorgefaseerde media.  

|Actie|Meer informatie|  
|------------|----------------------|  
|Een takenreeks maken die de variabele **SMSTSAssignUsersMode** bevat|Voeg de variabele **SMSTSAssignUsersMode** toe aan het begin van de takenreeks met behulp van de stap [Takenreeksvariabele instellen](../../osd/understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable) in de takenreeks. Met deze variabele geeft u op hoe de takenreeks omgaat met de gebruikersinformatie.<br /><br /> Stel de variabele in op een van de volgende waarden:<br /><br /> <br /><br /> **Automatische**: De takenreeks maakt automatisch een relatie tussen de gebruiker en de doelcomputer computer en het besturingssysteem implementeert.<br /><br /> **In behandeling**: De takenreeks brengt een relatie tussen de gebruiker en de doelcomputer, maar wordt gewacht op goedkeuring van de gebruiker met beheerdersrechten voordat het besturingssysteem wordt geïmplementeerd.<br /><br /> **Uitgeschakelde**: De takenreeks koppelt geen gebruiker aan de doelcomputer en implementatie van het besturingssysteem wordt voortgezet.<br /><br /> <br /><br /> Deze variabele kan ook worden ingesteld voor een computer of verzameling. Zie voor meer informatie over de ingebouwde variabelen [Takenreeksvariabelen ingebouwde](../../osd/understand/task-sequence-built-in-variables.md).|  
|Een prestart-opdracht maken waarmee de gebruikersinformatie worden verzameld|De prestart-opdracht kan een VB-script (Visual Basic) met een invoervak zijn, of kan een HTML-toepassing (HTA) zijn waarmee de opgegeven gebruikersgegevens worden gevalideerd.<br /><br /> Met de prestart-opdracht moet de variabele **SMSTSUdaUsers** worden ingesteld die wordt gebruikt wanneer de takenreeks wordt uitgevoerd. Deze variabele kan worden ingesteld voor een computer, een verzameling of een variabele in een takenreeks. Gebruik de volgende indeling als u meerdere gebruikers toevoegt: *domein\gebruiker1, domein\gebruiker2, domein\gebruiker3*.|  
|Configureren hoe distributiepunten en media de gebruiker koppelen aan de doelcomputer|Wanneer u [een distributiepunt configureert voor de acceptatie van PXE-opstartaanvragen](https://technet.microsoft.com/library/mt627944\(TechNet.10\).aspx#BKMK_PXEDistributionPoint) en wanneer u [opstartbare media](http://technet.microsoft.com/library/mt627921\(TechNet.10\).aspx) of [voorgefaseerde media](https://technet.microsoft.com/library/mt627922\(TechNet.10\).aspx) maakt met de wizard Takenreeksmedia maken, kunt u opgeven hoe het distributiepunt of de media ondersteuning biedt voor het koppelen van gebruikers aan de doelcomputer waarop het besturingssysteem wordt geïmplementeerd.<br /><br /> Er bestaat geen ingebouwde methode om de gebruikersidentiteit te valideren wanneer u de ondersteuning van de gebruikersaffiniteit configureert voor apparaten. Dit kan belangrijk zijn wanneer een technicus die de computer inricht, informatie namens de gebruiker opgeeft. Door deze opties te configureren op het distributiepunt en in de media wordt niet alleen ingesteld hoe de gebruikersinformatie door de takenreeks wordt verwerkt, maar wordt tevens de mogelijkheid geboden om implementaties te beperken die worden gestart via een PXE-opstartbewerking of vanaf een specifiek type media.|  
