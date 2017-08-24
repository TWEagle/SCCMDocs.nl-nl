---
title: Voorbeeldscenario voor het implementeren en bewaken van beveiligingsupdates | Microsoft Docs
description: Gebruik dit voorbeeldscenario van het software-updates in Configuration Manager gebruiken om te implementeren en software-updates voor Microsoft maandelijkse releases beveiliging controleren.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.service: 
ms.assetid: c32f757a-02da-43f2-b055-5cfd097d8c43
ms.openlocfilehash: 0e6e2b3a9455bb6eda437eb1325aaaadb3d83420
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="example-scenario-for-using-system-center-configuration-manager-to-deploy-and-monitor-the-security-software-updates-released-monthly-by-microsoft"></a>Voorbeeldscenario voor het gebruik van System Center Configuration Manager implementeren en controleren van de updates van beveiligingssoftware per maand door Microsoft

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat een voorbeeldscenario voor hoe u software-updates in System Center Configuration Manager kunt implementeren en controleren van de beveiligingsupdates die elke maand door Microsoft worden uitgegeven.  

 In dit scenario is Jeroen de Configuration Manager-beheerder bij Woodgrove Bank. Hij moet een implementatiestrategie voor software-updates maken met de volgende voorwaarden en vereisten:  

-   Actieve implementatie van software-updates vindt plaats één week nadat Microsoft de beveiligingsupdates publiceert op de tweede dinsdag van elke maand, de welbekende 'patchdinsdag'.  

-   Software-updates worden gedownload en voorbereid op distributiepunten. Vervolgens wordt een implementatie getest op een subset met clients voordat Jeroen de software-updates volledig implementeert in zijn productieomgeving.  

-   Jeroen moet de naleving van de software-updates kunnen bewaken op maand of op jaar.  

 In dit scenario wordt aangenomen dat de infrastructuur van het software-updatepunt al is geïmplementeerd. Gebruik de volgende informatie plannen en configureren van software-updates in Configuration Manager.  

|Proces|Verwijzing|  
|-------------|---------------|  
|De belangrijkste concepten voor software-updates doornemen.|[Inleiding tot software-updates](../understand/software-updates-introduction.md)|  
|Software-updates plannen. Met deze informatie kunt u rekening houden met capaciteitsoverwegingen, de infrastructuur van het software-updatepunt, de installatie van het software-updatepunt, synchronisatie-instellingen en clientinstellingen voor software-updates bij het maken van een planning.|[Software-updates plannen](../plan-design/plan-for-software-updates.md)|  
|Software-updates configureren. Met deze informatie kunt u software-updatepunten in uw hiërarchie installeren en configureren, en kunt u software-updates configureren en synchroniseren.<br /><br /> In dit scenario is configureert Jeroen de synchronisatieplanning voor software-updates om te worden uitgevoerd op de tweede woensdag van elke maand om ervoor te zorgen dat hij de meest recente beveiligingsupdates van Microsoft haalt.|[Software-updates synchroniseren](../get-started/synchronize-software-updates.md)|  

 De volgende secties in dit onderwerp bevatten voorbeelden van stappen om te implementeren en controleren van de updates van Configuration Manager in uw organisatie.

##  <a name="BKMK_Step1"></a>Stap 1: Een software-updategroep voor jaarlijkse naleving maken  
 Jeroen maakt een software-updategroep die hij gebruiken kan voor het bewaken van naleving voor alle beveiligingsupdates die hij in 2016 uitgeeft. Hij voert de stappen in de volgende tabel uit.  

|Proces|Verwijzing|  
|-------------|---------------|  
|Van de **alle Software-Updates** knooppunt in de Configuration Manager-console John voegt criteria om alleen beveiligingsupdates die zijn uitgegeven of aangepast in het jaar 2015 weer te geven die voldoen aan de volgende criteria:<br /><br /><ul><li>**Criteria**: Datum van publicatie- of revisiedatum</li><li>**Voorwaarde**: is groter dan of gelijk aan een specifieke datum<br />**Waarde**: 1/1/2015</li><li>**Criteria**: Updateclassificatie<br />**Waarde**: Beveiligingsupdates</li><li>**Criteria**: Verlopen <br />**Waarde**: Nee</li></ul>|Geen aanvullende informatie|
|Jeroen voegt alle gefilterde software-updates toe aan een nieuwe software-updategroep met de volgende vereisten:<br /><br /><ul><li>**Naam**: Nalevingsgroep - Microsoft-beveiligingsupdates 2015-Updates</li><li>**Beschrijving**: Software-updates|[Software-updates toevoegen aan een updategroep](add-software-updates-to-an-update-group.md)|  

##  <a name="BKMK_Step2"></a>Stap 2: Een regel voor automatische implementatie maken voor de huidige maand  
 Jeroen maakt een regel voor automatische implementatie voor de beveiligingsupdates die door Microsoft worden uitgegeven voor de huidige maand. Hij voert de stappen in de volgende tabel uit.  

|Proces|Verwijzing|  
|-------------|---------------|  
|Jeroen maakt een regel voor automatische implementatie met de volgende vereisten:<br /><br /><ol><li>Op het tabblad **Algemeen** configureert Jeroen het volgende:<br /> <ul><li>Hiermee geeft u **maandelijkse beveiligingsupdates** voor de naam.</li><li>Selecteert een testverzameling met beperkte clients.</li><li>Hiermee selecteert u **maken van een nieuwe Software-Updategroep**.</li><li>Hiermee wordt gecontroleerd of **de implementatie inschakelen nadat deze regel is uitgevoerd** niet is ingeschakeld.</li></ul></li><li>Op het tabblad **Implementatie-instellingen** selecteert Jeroen de standaardinstellingen.</li><li>Op de **Software-Updates** pagina Jeroen configureert de volgende eigenschapfilters en zoekcriteria:<br /><ul><li>Publicatie- of revisiedatum **Afgelopen maand**.</li><li>Updateclassificatie **Beveiligingsupdates**.</li></ul></li><li>Op de **evaluatie** pagina Jeroen in dat de regel wilt uitvoeren op een planning voor de **tweede donderdag** van elke **maand**. Hij controleert ook of of zijn Synchronisatieplanning is ingesteld op uitvoeren op de **tweede woensdag** van elke **maand**.</li><li>Jeroen gebruikt de standaardinstellingen op de pagina's Implementatieplanning, Gebruikerservaring, Meldingen en Instellingen voor downloaden.</li><li>Op de **implementatiepakket** pagina John Hiermee geeft u een nieuw implementatiepakket.</li><li>Jeroen gebruikt de standaardinstellingen op de pagina's Downloadlocatie en Taal selecteren.</li></ol>|[Software-updates automatisch implementeren](automatically-deploy-software-updates.md)|  

##  <a name="BKMK_Step3"></a>Stap 3: Controleer of software-updates zijn gereed om te implementeren  
 Op de tweede donderdag van elke maand controleert Jeroen of de software-updates gereed zijn voor implementatie. Hij voert de volgende stap.  

|Proces|Verwijzing|  
|-------------|---------------|  
|Jeroen controleert of de synchronisatie van software-updates correct is voltooid.|[Synchronisatiestatus van software-updates](monitor-software-updates.md#BKMK_SUSyncStatus)|  

##  <a name="BKMK_Step4"></a>Stap 4: De software-updategroep implementeren  
 Nadat Jeroen heeft gecontroleerd of de software-updates gereed zijn voor implementatie, implementeert hij ze. Hij voert de stappen in de volgende tabel uit.  

|Proces|Verwijzing|  
|-------------|---------------|  
|Jeroen maakt twee testimplementaties voor de nieuwe software-updategroep. Hij overweegt de volgende omgevingen voor elke implementatie:<br /><br /> **Testimplementatie werkstation**: Jeroen overweegt het volgende voor de testimplementatie werkstation:<br /><br /><ul><li>Geeft een implementatieverzameling op die een subset met werkstationclients om te controleren of de implementatie bevat.</li><li>Hiermee configureert u de implementatie-instellingen die geschikt voor de werkstationclients in zijn omgeving zijn.</li></ul><br />**Testimplementatie server**: Jeroen overweegt het volgende voor de testimplementatie op servers:<br /><br /><ul><li>Geeft een implementatieverzameling op die een subset met serverclients om te controleren of de implementatie bevat.</li><li>Hiermee configureert u de implementatie-instellingen die geschikt voor de serverclients in zijn omgeving zijn.</li></ul>|[Software-updates implementeren](deploy-software-updates.md)|  
|Jeroen controleert of de testimplementaties correct zijn uitgevoerd.|[Implementatiestatus van software-updates](monitor-software-updates.md#BKMK_SUDeployStatus)|  
|Jeroen werkt de twee implementaties bij met nieuwe verzamelingen die zijn productiewerkstations en -servers bevatten.|Geen aanvullende informatie|  

##  <a name="BKMK_Step5"></a>Stap 5: Naleving bewaken voor geïmplementeerde software-updates  
 Jeroen bewaakt de naleving van zijn software-update-implementaties. Hij voert de stap in de volgende tabel uit.  

|Proces|Verwijzing|  
|-------------|---------------|  
|Jeroen bewaakt de implementatiestatus van software-updates in de Configuration Manager-console en controleert de software-implementatie-updaterapporten beschikbaar zijn via de console.|[Software-updates in System Center Configuration Manager controleren](../../sum/deploy-use/monitor-software-updates.md)|  

##  <a name="BKMK_Step6"></a>Stap 6: Maandelijkse softwareupdates toevoegen aan de groep voor jaarlijkse updates  
 Jeroen voegt de software-updates uit de groep voor maandelijkse software-updates toe aan de groep voor jaarlijkse software-updates. Hij voert de stap in de volgende tabel uit.  

|Proces|Verwijzing|  
|-------------|---------------|  
|Jeroen selecteert de software-updates in de groep met maandelijkse software-updates en voegt ze toe aan de groep met software-updates die hij heeft gemaakt voor jaarlijkse naleving. Hij houdt de naleving van software-updates bij en maakt diverse rapporten voor zijn beheeractiviteiten.|[Software-updates toevoegen aan een geïmplementeerde updategroep](add-software-updates-to-an-update-group.md)|  

Jeroen heeft zijn maandelijkse implementatie voor beveiligingsupdates correct voltooid. Hij blijft de naleving van software-updates bewaken en rapporteren om te waarborgen dat de clients in zijn omgeving binnen acceptabele nalevingsniveaus vallen.  

##  <a name="BKMK_MonthlyProcess"></a>Terugkerend maandelijks proces voor het implementeren van software-updates  
 Na de eerste maand dat Jeroen software-updates implementeert, voert hij stap drie tot en met zes uit om de maandelijkse beveiligingsupdates van Microsoft te implementeren.  
