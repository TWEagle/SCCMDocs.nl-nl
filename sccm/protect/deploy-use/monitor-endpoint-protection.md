---
title: Endpoint Protection-status bewaken | Microsoft-documenten
description: "Informatie over hoe Endpoint Protection controleren in de System Center Configuration Manager-hiërarchie."
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4a1335c-bb3d-493e-a124-83a32a107dc8
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: b5771f4faebc06076bdbf84727848c881fc1dfb4
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-endpoint-protection-status"></a>Het bewaken van Endpoint Protection-status

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

U kunt Endpoint Protection in uw Microsoft System Center Configuration Manager-hiërarchie controleren met behulp van de **Status van Endpoint Protection** knooppunt onder **beveiliging** in de **bewaking** werkruimte de **Endpoint Protection** knooppunt in de **activa en naleving** werkruimte en door rapporten te gebruiken.  

##  <a name="BKMK_1"></a>Endpoint Protection met behulp van het knooppunt Status van Endpoint Protection controleren  

1.  Klik in de Configuration Manager-console op **bewaking**.  

2.  In de **bewaking** werkruimte Vouw **beveiliging** en klik vervolgens op **Status van Endpoint Protection**.  

3.  In de **verzameling** , selecteert u de verzameling waarvoor u wilt statusinformatie wilt weergeven.  

    > [!IMPORTANT]  
    >  Verzamelingen zijn beschikbaar voor selectie in de volgende gevallen:  
    >   
    >  -   Wanneer u selecteert **deze verzameling weergeven in het dashboard Endpoint Protection** op de **waarschuwingen** tabblad van het *< Collectienaam\>***eigenschappen** in het dialoogvenster.  
    > -   Wanneer u een antimalwarebeleid Endpoint Protection implementeert voor de verzameling.  
    > -   Wanneer u inschakelen en instellingen van Endpoint Protection-clients implementeren voor de verzameling.  

4.  Lees de informatie die wordt weergegeven in de **Veiligheidstoestand** en **operationele status** secties. U kunt op elke statuskoppeling klikken om een tijdelijke verzameling te maken in het knooppunt **Apparaten** van de werkruimte **Activa en naleving** . De tijdelijke verzameling bevat de computers met de geselecteerde status.  

    > [!IMPORTANT]  
    >  Informatie die wordt weergegeven in de **Status van Endpoint Protection** knooppunt is gebaseerd op de laatste gegevens die uit de Configuration Manager-database is samengevat en kan niet worden huidige. Als u de meest recente gegevens wilt ophalen, klikt u op het tabblad **Start** op de optie **Samenvatting uitvoeren**of klikt u op **Overzicht plannen** om het interval voor overzichten aan te passen.  

##  <a name="BKMK_2"></a>Het bewaken van Endpoint Protection in de activa en naleving werkruimte  

1.  Klik op **Activa en naleving**op de Configuration Manager-console.  

2.  In de **activa en naleving** werkruimte, voer een van de volgende acties uit:  

    -   Klik op **apparaten**. Selecteer in de lijst **Apparaten** een computer en klik op het tabblad **Details van malware** .  

    -   Klik op **Apparaatverzamelingen**. Selecteer in de lijst **Apparaatverzamelingen** de verzameling met de computer die u wilt bewaken en klik vervolgens op het tabblad **Start** in de groep **Verzameling** op **Leden weergeven**.  

3.  In de *< Collectienaam\>*  lijst, selecteert u een computer en klik op de **Malware Detail** tabblad.  

##  <a name="BKMK_3"></a>Endpoint Protection controleren met behulp van rapporten  
 Gebruik de volgende rapporten als u informatie over Endpoint Protection weergeven in uw hiërarchie. U kunt deze rapporten ook gebruiken bij het oplossen van eventuele problemen met Endpoint Protection. Zie voor meer informatie over het configureren van rapportage in Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) en [in System Center Configuration Manager-logboekbestanden](../../core/plan-design/hierarchy/log-files.md). De Endpoint Protection-rapporten zijn in de map Endpoint Protection.  

|Rapportnaam|Beschrijving|  
|-----------------|-----------------|  
|**Activiteitenrapport voor anti-malware**|Geeft een overzicht van activiteiten met betrekking tot anti-malware voor een opgegeven verzameling.|  
|**Geïnfecteerde computers**|Geeft een lijst weer van computers waarop een opgegeven bedreiging is gedetecteerd.|  
|**Meest voorkomende gebruikers op bedreigingen**|Geeft een lijst weer met de gebruikers met het hoogste aantal gedetecteerde bedreigingen.|  
|**Lijst met bedreigingen voor gebruiker**|Geeft een lijst weer met bedreigingen die zijn gedetecteerd voor een opgegeven gebruikersaccount.|  

## <a name="malware-alert-levels"></a>Waarschuwing malware niveaus  
 Gebruik de volgende tabel om te identificeren van de andere Endpoint Protection-waarschuwingsniveaus die kunnen worden weergegeven in rapporten of in de Configuration Manager-console.  

|Waarschuwingsniveau|Beschrijving|  
|-----------------|-----------------|  
|**Mislukt**|Endpoint Protection is niet opgelost, de malware. Raadpleeg de logboeken voor meer informatie over de fout.<br /><br /> **Opmerking:** Voor een lijst van Configuration Manager en Endpoint Protection-logboekbestanden, Zie de sectie "Endpoint Protection" in de [in System Center Configuration Manager-logboekbestanden](../../core/plan-design/hierarchy/log-files.md) onderwerp.|  
|**Verwijderd**|Endpoint Protection verwijderd de malware.|  
|**In quarantaine**|Endpoint Protection de malware verplaatst naar een veilige locatie en deze niet kan worden uitgevoerd tot u deze verwijderen of toe te staan om uit te voeren.|  
|**Opgeruimd**|De malware is verwijderd uit het geïnfecteerde bestand.|  
|**Toegestaan**|Een gebruiker met beheerdersrechten heeft toegestaan om de software met de malware uit te voeren.|  
|**Geen actie**|Endpoint Protection heeft geen actie tegen de schadelijke software. Dit kan voorkomen als de computer opnieuw wordt opgestart nadat de malware is gedetecteerd en de malware niet meer wordt gedetecteerd. Het kan bijvoorbeeld gebeuren dat een toegewezen netwerkstation waarop malware wordt gedetecteerd niet opnieuw wordt aangesloten wanneer de computer opnieuw wordt opgestart.|  
|**Geblokkeerd**|Endpoint Protection geblokkeerd de schadelijke software niet kan worden uitgevoerd. Dit kan gebeuren als een proces op de computer malware blijkt te bevatten.|

