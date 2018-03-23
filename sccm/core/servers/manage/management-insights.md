---
titleSuffix: Configuration Manager
description: Meer informatie over Management Insights functionaliteit die beschikbaar is in de Configuration Manager-console.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a79f83be-884c-48e6-94d6-ed0a68c22e2f
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: d2d6a58bd5aba873ea35c5bcf511a3cc22514b51
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="management-insights-in-system-center-configuration-manager"></a>Insights Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Insights Management in System Center Configuration Manager bieden informatie over de huidige status van uw omgeving. De informatie is gebaseerd op de analyse van gegevens uit de sitedatabase. Insights kunnen u beter inzicht in uw omgeving en Neem maatregelen op basis van het inzicht. Deze functie werd uitgebracht in Configuration Manager versie 1802. <!--1353967-->

## <a name="review-management-insights-in-the-configuration-manager-console"></a>Bekijk Management inzicht in de Configuration Manager-console 
De **site lezen** machtiging is vereist om de regels weer te geven.

1. Open de Configuration Manager-Console. 
2. Ga naar de **beheer** knooppunt en klik op **Management Insights**.
3. Selecteer **alle Insights**
4. Dubbelklik op de **naam beheergroep inzicht** u wilt bekijken. U kunt ook selecteren en klik op **Insights weergeven** in het lint. 
5. Er zijn vier tabbladen beschikbaar is voor controle samen met de vereisten die nodig zijn voor de regel wordt uitgevoerd. 
    - **Alle regels**: Geeft de volledige lijst met regels voor de beheergroep inzicht gekozen.
    - **Volledige**:  Een lijst met regels waarbij geen actie is vereist. 
    - **Bezig**: Bevat regels waar sommige, maar niet alle vereisten is voldaan.
    - **Actie vereist**: Regels uitgevoerde acties die worden weergegeven. Met de rechtermuisknop en selecteer **meer Details** voor het ophalen van specifieke items waarop actie is vereist. 
    - **Vereisten**: Als een regel items voltooid moet voordat ze kunnen worden uitgevoerd, wordt de vereiste items worden hier vermeld.   
    
    **Alle regels en vereisten voor de groep cloud services** ![Management insights-alle regels en vereisten voor cloud services-groep](./media/Management-insights-all-cloud-rules.png)

## <a name="management-insights-reevaluation-and-logging"></a>Management insights herevaluatie en logboekregistratie
De regels voor poortbeheer inzicht Herzie hun toepasbaarheid op een wekelijkse planning. U kunt een regel op aanvraag opnieuw evalueren met de rechtermuisknop op de regel selecteren **opnieuw evalueren**.

**Logboekbestand voor regels voor poortbeheer inzicht**: SMS_DataEngine.log
## <a name="management-insights-groups-and-rules"></a>Insights beheergroepen en regels
Regels worden ingedeeld in verschillende inzicht beheergroepen. Wanneer regels en groepen worden toegevoegd, moeten deze worden toegevoegd aan de volgende lijst:

**Toepassingen**: Als u inzichten voor uw Toepassingsbeheer.

- **Toepassingen zonder implementaties** -geeft een lijst van de toepassingen in uw omgeving die u geen actieve implementaties hebt. Deze regel kunt u vinden en verwijderen van ongebruikte toepassingen voor het vereenvoudigen van de lijst met toepassingen die worden weergegeven in de console. 

**Cloudservices**: Helpt die u met veel cloudservices integreert; inschakelen van moderne beheer van uw apparaten. 
 - **Beoordeling van gereedheid van de CO management** -helpt u begrijpen welke stappen nodig zijn voor CO-beheer inschakelen. Deze regel bevat de vereisten. 
 - **Inschakelen van uw apparaten worden hybride die lid zijn van Azure Active Directory** -Azure AD-die lid zijn van apparaten kunnen gebruikers zich aanmelden met hun domeinreferenties terwijl de apparaten voldoen aan de normen beveiliging en naleving van de organisatie. 
 - **Uw infrastructuur identiteits- en toegangsbeheer moderniseren** -Azure AD-cloudservice met geïntegreerde meervoudige verificatie beveiligt gevoelige gegevens en toepassingen zowel on-premises en in de cloud. 
 - **Upgrade uitvoeren voor uw clients op Windows 10 versie 1709 of hoger** -1709 versie van Windows 10 of hoger wordt verbeterd en moderniseert de computergebruik van uw gebruikers. 


**Verzamelingen**: Inzichten die helpen bij het beheer vereenvoudigen door opruimen en opnieuw configureren van verzamelingen.
   - **Lege verzamelingen** -geeft een lijst van verzamelingen in uw omgeving die geen leden hebben. 

**Het beheer vereenvoudigd**: Inzichten die u helpen bij het vereenvoudigen van het dagelijkse beheer van uw omgeving. 
   - **Verouderde clientversies** -geeft een lijst van alle clients waarvan de versie ouder dan twee jaar zijn. 

**Software Center**: Als u inzichten voor het beheren van Software Center. 
   - **Gebruikers verwijzen naar Software Center in plaats van Application Catalog** -Controleer of gebruikers hebben geïnstalleerd of toepassingen uit de Application Catalog aangevraagd in de afgelopen 14 dagen. De primaire functionaliteit van Toepassingscatalogus is nu opgenomen in Software Center. Ondersteuning voor het einde van de Application Catalog-website met de eerste update die na 1 juni 2018 wordt uitgebracht
   - **De nieuwe versie van het Software Center** -de vorige versie van het Software Center wordt niet meer ondersteund. Clients instellen voor gebruik van het nieuwe Software Center doordat de client-instelling **Computeragent** >**nieuwe Software Center gebruiken**.

**Windows 10**: Inzichten met betrekking tot de implementatie en het onderhoud van Windows 10. De Windows 10-inzicht beheergroep is beschikbaar wanneer er meer dan de helft van clients Windows 7, Windows 8 of Windows 8.1 worden uitgevoerd.
   - **Configureer Windows Telemetrie en commerciële ID sleutel** -voor het gebruik van gegevens van de gereedheid voor Upgrade apparaten moeten worden geconfigureerd met een commerciële ID-sleutel en telemetrie is ingeschakeld. Windows 10-apparaten moeten worden ingesteld op het niveau van de telemetrie uitgebreid (beperkt) of hoger.
   - **Configuration Manager verbinding met gereedheid voor Upgrade** -gebruiken voor de gereedheid voor Upgrade voor uw Windows 10-implementaties snellere voordat Windows 7 niet worden ondersteund wordt. **Configureer Windows Telemetrie en commerciële ID sleutel** is een vereiste.

     **Windows 10 insights regels**
    ![insights-regels voor Windows 10](./media/Windows-10-insights-group.png)
    