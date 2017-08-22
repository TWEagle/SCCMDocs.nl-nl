---
title: Verzamelingen beheren | Microsoft Docs
description: Voer algemene verzamelingen beheertaken in System Center Configuration Manager.
ms.custom: na
ms.date: 4/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e102fd1a-76df-4d8e-b1b0-10ee18318f67
caps.latest.revision: "8"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 4d44f98eb0755619cdd2101203a13725186b835b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-manage-collections-in-system-center-configuration-manager"></a>Verzamelingen in System Center Configuration Manager beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit onderwerp om u te helpen bij het uitvoeren van beheertaken voor verzamelingen in System Center Configuration Manager.  

> [!NOTE]  
>  Zie voor meer informatie over het maken van Configuration Manager-verzamelingen [verzamelingen maken in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).  

## <a name="how-to-manage-device-collections"></a>Apparaatverzamelingen beheren  
 In de werkruimte **Activa en naleving** selecteert u **Apparaatverzamelingen**, selecteert u de te beheren verzameling en selecteert u vervolgens een beheertaak.  

 Gebruik de volgende tabel voor meer informatie over de beheertaken waarvoor u mogelijk meer uitleg nodigt hebt voordat u ze selecteert.  

|Beheertaak|Details|Meer informatie|  
|---------------------|-------------|----------------------|  
|**Leden weergeven**|Hiermee worden alle resources die lid zijn van de geselecteerde verzameling weergegeven in een tijdelijk knooppunt onder het knooppunt **Apparaten** .|Geen aanvullende informatie.|  
|**Geselecteerde items toevoegen**|Biedt de volgende opties om een van de volgende acties uit te voeren:<br /><br /> - <br />                    **Geselecteerde Items toevoegen aan bestaande verzameling apparaten** -Hiermee opent u de **verzameling selecteren** in het dialoogvenster waarin u de verzameling waarnaar u wilt toevoegen van de leden van de geselecteerde verzameling kunt selecteren. De geselecteerde verzameling is opgenomen in deze verzameling met behulp van de lidmaatschapsregel **Verzamelingen opnemen** .<br /><br /> - **Geselecteerde Items toevoegen aan de nieuwe verzameling apparaten** -Hiermee opent u de **Wizard Apparaatverzameling maken** waarin u een nieuwe verzameling kunt maken. De geselecteerde verzameling is opgenomen in deze verzameling met behulp van de lidmaatschapsregel **Verzamelingen opnemen** .|[Verzamelingen maken in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md)|  
|**Client installeren**|Hiermee opent u de **Wizard Client installeren** waarin push-clientinstallatie naar een Configuration Manager-client installeren op alle computers in de geselecteerde verzameling.|[Clients implementeren op Windows-computers](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)|  
|**Affiniteitsaanvragen beheren**|Hiermee opent u het dialoogvenster **Affiniteitsaanvragen van gebruikersapparaten beheren** waarin u openstaande aanvragen voor het instellen van affiniteit van gebruikersapparaten kunt goedkeuren of afwijzen voor apparaten in de geselecteerde verzameling.|[Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**Vereiste PXE-implementaties wissen**|Hiermee wist u alle vereiste PXE-opstartimplementaties van alle leden van de geselecteerde verzameling.|[Inleiding tot besturingssysteemimplementaties](../../../../osd/understand/introduction-to-operating-system-deployment.md)|  
|**Lidmaatschap bijwerken**|Hiermee evalueert u het lidmaatschap voor de geselecteerde verzameling. Voor verzamelingen met veel leden kan deze update even duren. Gebruik de actie **Vernieuwen** om de weergave bij te werken met de nieuwe leden van de verzamelingen nadat de update is voltooid.|Geen aanvullende informatie.|  
|**Resources toevoegen**|Hiermee opent u het dialoogvenster **Resources toevoegen aan de verzameling** waarin u nieuwe resources kunt zoeken om toe te voegen aan de geselecteerde verzameling.<br /><br /> Het pictogram voor de geselecteerde verzameling wordt een zandlopersymbool weergegeven weergegeven terwijl de update uitgevoerd wordt.|Geen aanvullende informatie.|  
|**Clientmeldingen**|Hiermee instrueert u alle clients in de geselecteerde apparaatverzameling om computer- of gebruikersbeleid te downloaden.|Geen aanvullende informatie.|  
|**Endpoint Protection**|Hiermee wordt een volledige of snelle antimalwarescan uitgevoerd of worden de meest recente antimalwaredefinities gedownload op computers in de geselecteerde verzameling.|[Endpoint Protection in System Center Configuration Manager](../../../../protect/deploy-use/endpoint-protection.md)|  
|**Exportereneren**|Hiermee opent u de **Wizard verzameling exporteren** kunt u deze verzameling exporteren naar een Managed Object Format (MOF) bestand dat kunnen vervolgens worden gearchiveerd of gebruikt op een andere Configuration Manager-site.<br /><br /> Wanneer u een verzameling exporteert, worden verzamelingen waarnaar wordt verwezen door de geselecteerde verzameling via een **opname** - of **uitsluiting** sregel niet geëxporteerd.|Geen aanvullende informatie.|  
|**Kopiëren**|Hiermee wordt een kopie gemaakt van de geselecteerde verzameling. De nieuwe verzameling gebruikt de geselecteerde verzameling als een beperkende verzameling.|Geen aanvullende informatie.|  
|**Verwijderen**|Hiermee verwijdert u de geselecteerde verzameling. U kunt ook alle resources in de verzameling verwijderen uit de sitedatabase.<br /><br /> U kunt de verzamelingen die zijn ingebouwd in Configuration Manager niet verwijderen.|Zie voor een lijst van de ingebouwde verzamelingen [inleiding op verzamelingen in System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md).|  
|**Implementatie simuleren**|Hiermee wordt de **Wizard Implementatie van toepassing simuleren** geopend, waarin u de resultaten van een toepassingsimplementatie kunt testen zonder de toepassing daadwerkelijk te installeren of verwijderen.|[Implementaties van toepassingen met System Center Configuration Manager simuleren](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**Implementeren**|De opties zijn als volgt:<br /><br /> - <br />                    **Toepassing** -Hiermee opent u de **Wizard Software implementeren** waar u kunt selecteren en configureren van een toepassingsimplementatie op de geselecteerde verzameling.<br /><br /> - <br />                    **Programma** – Hiermee opent u de **Wizard Software implementeren** waarin u een pakket- en programma-implementatie kunt selecteren en configureren voor de geselecteerde verzameling.<br /><br /> - **Configuratiebasislijn** -Hiermee opent u de **Configuratiebasislijnen implementeren** in het dialoogvenster waarin u de implementatie van een of meer configuratiebasislijnen voor de geselecteerde verzameling kunt configureren.<br /><br /> - <br />                    **Takenreeks** – Hiermee opent u de **Wizard Software implementeren** waarin u een takenreeksimplementatie kunt selecteren en configureren voor de geselecteerde verzameling.<br /><br /> - <br />                    **Software-Updates** -Hiermee opent u de **Wizard voor Software-Updates implementeren** waar u de implementatie van softwareupdates voor resources in de geselecteerde verzameling kunt configureren.|[Het implementeren van toepassingen met System Center Configuration Manager](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [Pakketten en programma's in System Center Configuration Manager](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [Het implementeren van configuratiebasislijnen in System Center Configuration Manager](../../../../compliance/deploy-use/deploy-configuration-baselines.md)<br /><br /> [Takenreeksen beheren om te automatiseren in System Center Configuration Manager](../../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md)<br /><br /> [Software-updates in System Center Configuration Manager beheren](/sccm/sum/understand/software-updates-introduction)|  

## <a name="how-to-manage-user-collections"></a>Gebruikersverzamelingen beheren  
 In de werkruimte **Activa en naleving** selecteert u **Gebruikersverzamelingen**, selecteert u de te beheren verzameling en selecteert u vervolgens een beheertaak.  

 Gebruik de volgende tabel voor meer informatie over de beheertaken waarvoor u mogelijk meer uitleg nodigt hebt voordat u ze selecteert.  

|Beheertaak|Details|Meer informatie|  
|---------------------|-------------|----------------------|  
|**Leden weergeven**|Hiermee worden alle resources die lid zijn van de geselecteerde verzameling weergegeven in een tijdelijk knooppunt onder het knooppunt **Gebruikers** .|Geen aanvullende informatie.|  
|**Geselecteerde items toevoegen**|Met deze optie kunt u een van de volgende acties uitvoeren:<br /><br /> - <br />                    **Geselecteerde Items toevoegen aan bestaande verzameling apparaten** -Hiermee opent u de **verzameling selecteren** in het dialoogvenster waarin u de verzameling waarnaar u wilt toevoegen van de leden van de geselecteerde verzameling kunt selecteren. De geselecteerde verzameling is opgenomen in deze verzameling met behulp van de lidmaatschapsregel **Verzamelingen opnemen** .<br /><br /> - **Geselecteerde Items toevoegen aan de verzameling nieuwe gebruikers** -Hiermee opent u de **Wizard Gebruikersverzameling maken** waarin u een nieuwe verzameling kunt maken. De geselecteerde verzameling is opgenomen in deze verzameling met behulp van de lidmaatschapsregel **Verzamelingen opnemen** .|[Verzamelingen maken in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md)|  
|**Affiniteitsaanvragen beheren**|Hiermee opent u het dialoogvenster **Affiniteitsaanvragen van gebruikersapparaten beheren** waarin u openstaande aanvragen voor het instellen van affiniteit van gebruikersapparaten kunt goedkeuren of afwijzen voor gebruikers in de geselecteerde verzameling.|[Gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten in System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**Lidmaatschap bijwerken**|Hiermee evalueert u het lidmaatschap voor de geselecteerde verzameling. Voor verzamelingen met veel leden kan deze update even duren. Gebruik de actie **Vernieuwen** om de weergave bij te werken met de nieuwe leden van de verzamelingen nadat de update is voltooid.<br /><br /> Het pictogram voor de geselecteerde verzameling wordt een zandlopersymbool weergegeven weergegeven terwijl de update uitgevoerd wordt.|Geen aanvullende informatie.|  
|**Resources toevoegen**|Hiermee opent u het dialoogvenster **Resources toevoegen aan de verzameling** waarin u nieuwe resources kunt zoeken om toe te voegen aan de geselecteerde verzameling.|Geen aanvullende informatie.|  
|**Exportereneren**|Hiermee opent u de **Wizard verzameling exporteren** waarmee u deze verzameling kunt exporteren naar een Managed Object Format (MOF) bestand dat vervolgens kan worden gearchiveerd of gebruikt op een andere Configuration Manager-site.<br /><br /> Wanneer u een verzameling exporteert, worden verzamelingen waarnaar wordt verwezen door de geselecteerde verzameling via een **opname** - of **uitsluiting** sregel niet geëxporteerd.|Geen aanvullende informatie.|  
|**Kopiëren**|Hiermee wordt een kopie gemaakt van de geselecteerde verzameling. De nieuwe verzameling gebruikt de geselecteerde verzameling als een beperkende verzameling.|Geen aanvullende informatie.|  
|**Verwijderen**|Hiermee verwijdert u de geselecteerde verzameling. U kunt ook alle resources in de verzameling verwijderen uit de sitedatabase.<br /><br /> U kunt de verzamelingen die zijn ingebouwd in Configuration Manager niet verwijderen.|Zie voor een lijst van de ingebouwde verzamelingen [inleiding op verzamelingen in System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md).|  
|**Implementatie simuleren**|Hiermee wordt de **Wizard Implementatie van toepassing simuleren** geopend, waarin u de resultaten van een toepassingsimplementatie kunt testen zonder de toepassing daadwerkelijk te installeren of verwijderen.|[Implementaties van toepassingen met System Center Configuration Manager simuleren](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**Implementeren**|De opties zijn als volgt:<br /><br /> - **Toepassing** -Hiermee opent u de **Wizard Software implementeren** waar u kunt selecteren en configureren van een toepassingsimplementatie op de geselecteerde verzameling.<br /><br /> - <br />                    **Programma** – Hiermee opent u de **Wizard Software implementeren** waarin u een pakket- en programma-implementatie kunt selecteren en configureren voor de geselecteerde verzameling.<br /><br /> - **Configuratiebasislijn** -Hiermee opent u de **Configuratiebasislijnen implementeren** in het dialoogvenster waarin u de implementatie van een of meer configuratiebasislijnen voor de geselecteerde verzameling kunt configureren.|[Het implementeren van toepassingen met System Center Configuration Manager](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [Pakketten en programma's in System Center Configuration Manager](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [Het implementeren van configuratiebasislijnen in System Center Configuration Manager](../../../../compliance/deploy-use/deploy-configuration-baselines.md)|  

##  <a name="BKMK_CollProp"></a> Verzamelingseigenschappen  
 Wanneer u het dialoogvenster **Eigenschappen** opent voor een verzameling, kunt u de volgende eigenschappen voor een verzameling bekijken en configureren.  

|Tabbladnaam|Meer informatie|  
|--------------|----------------------|  
|**Algemeen**|Hiermee kunt u algemene informatie weergeven en configureren over de geselecteerde verzameling, met inbegrip van de naam van de verzameling en de beperkende verzameling.|  
|**Lidmaatschapsregels**|Hiermee kunt u de lidmaatschapsregels configureren waarmee het lidmaatschap van deze verzameling wordt gedefinieerd. Zie voor meer informatie [verzamelingen maken in System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).|  
|**Energiebeheer**|Hiermee kunt u energieschema's configureren die zijn toegewezen aan computers in de geselecteerde verzameling. Zie voor meer informatie [inleiding op Energiebeheer](../../../../core/clients/manage/power/introduction-to-power-management.md).|  
|**Implementaties**|Hiermee wordt software weergegeven die is geïmplementeerd op leden van de geselecteerde verzameling.|  
|**Onderhoudsvensters**|U kunt onderhoudsvensters weergeven en configureren die worden toegepast op leden van de geselecteerde verzameling. Zie voor meer informatie [het gebruik van onderhoudsvensters in System Center Configuration Manager](../../../../core/clients/manage/collections/use-maintenance-windows.md).|  
|**Verzamelingsvariabelen**|Hiermee kunt u variabelen configureren die gelden voor deze verzameling en die kunnen worden gebruikt door takenreeksen. Zie voor meer informatie [Takenreeksvariabelen ingebouwde](../../../../osd/understand/task-sequence-built-in-variables.md).|  
|**Distributiepuntgroepen**|Hiermee kunt u een of meer distributiepuntengroepen koppelen aan leden van de geselecteerde verzameling. Zie voor meer informatie [inhoud en infrastructuur voor System Center Configuration Manager beheren](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Beveiliging**|Hiermee worden de gebruikers met beheerdersrechten weergegeven die beschikken over machtigingen voor de geselecteerde verzameling via bijbehorende rollen en beveiligingsbereiken.|  
|**Monitor**|Hiermee kunt u configureren wanneer waarschuwingen worden gegenereerd voor de clientstatus en Endpoint Protection. Zie voor meer informatie [clientstatus configureren in System Center Configuration Manager](../../../../core/clients/deploy/configure-client-status.md) en [Endpoint Protection in System Center Configuration Manager controleren](../../../../protect/deploy-use/monitor-endpoint-protection.md).|  
