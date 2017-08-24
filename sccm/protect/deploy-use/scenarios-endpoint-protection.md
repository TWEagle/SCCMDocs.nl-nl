---
title: Scenario Endpoint Protection beschermt computers tegen schadelijke software | Microsoft Docs
description: Informatie over het implementeren van Endpoint Protection in Configuration Manager om computers te beveiligen tegen schadelijke software.
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 539c7a89-3c03-4571-9cb4-02d455064eeb
caps.latest.revision: "8"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: b98684d44874ff246e4d675039c6e443aee82a62
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="example-scenario-using-system-center-endpoint-protection-to-protect-computers-from-malware-in-system-center-configuration-manager"></a>Voorbeeldscenario: System Center Endpoint Protection gebruiken om computers te beveiligen tegen schadelijke software in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp biedt een voorbeeldscenario voor hoe u Endpoint Protection in Configuration Manager implementeren kunt om computers te beveiligen in een organisatie tegen schadelijke software.  

 John is de Configuration Manager-beheerder bij Woodgrove Bank. De bank gebruikt momenteel System Center Endpoint Protection om computers tegen malware-aanvallen te beveiligen. Daarnaast gebruikt de bank Windows-groepsbeleid om te zorgen dat Windows Firewall is ingeschakeld op alle computers in het bedrijf en dat gebruikers een melding krijgen wanneer Windows Firewall een nieuw programma blokkeert.  

 Johan is gevraagd de Woodgrove Bank antimalwaresoftware upgraden naar System Center Endpoint Protection, zodat de bank kan van de nieuwste functies voor anti-malware profiteren en kunnen de antimalwareoplossing centraal te beheren vanuit de Configuration Manager-console. Voor deze implementatie gelden de volgende vereisten:  

-   Configuration Manager gebruiken voor het beheren van de Windows Firewall-instellingen die al worden beheerd door Groepsbeleid.  

-   Gebruik Configuration Manager software-updates te downloaden van definities van schadelijke software op computers. Als geen software-updates beschikbaar zijn, bijvoorbeeld omdat de computer niet is verbonden met het bedrijfsnetwerk, moeten definitie-updates op computers worden gedownload vanaf Microsoft Update.  

-   Computers van gebruikers moeten dagelijks een snelle malwarescan uitvoeren. Op servers moet echter elke zaterdag om 01:00 uur, buiten werkuren, een volledige scan worden uitgevoerd  

-   Een waarschuwing per e-mail verzenden wanneer een van de volgende gebeurtenissen optreedt:  

    -   Er wordt malware gedetecteerd op een computer  

    -   Dezelfde malwarebedreiging wordt op meer dan 5 procent van de computers gedetecteerd  

    -   Dezelfde malwarebedreiging wordt binnen een periode van 24 uur meer dan 5 maal gedetecteerd  

    -   Meer dan 3 soorten malware worden binnen een periode van 24 uur gedetecteerd  

-   De bestaande antimalwareoplossing verwijderen.  

 Jeroen voert vervolgens de volgende stappen voor het implementeren van Endpoint Protection:  

##  <a name="steps-to-implement-endpoint-protection"></a>Stappen voor het implementeren van Endpoint Protection  

|Proces|Verwijzing|  
|-------------|---------------|  
|Johan bekijkt de beschikbare informatie over de basisconcepten voor Endpoint Protection in Configuration Manager.|Zie voor informatie over Endpoint Protection [Endpoint Protection in System Center Configuration Manager](endpoint-protection.md).|  
|Johan controleert en implementeert de vereisten voor het gebruik van Endpoint Protection.|Zie voor meer informatie over de vereisten voor Endpoint Protection [Planning voor Endpoint Protection](../plan-design/planning-for-endpoint-protection.md).|  
|Jeroen installeert de Endpoint Protection-sitesysteemrol op slechts één sitesysteemserver aan de bovenkant van de hiërarchie van Woodgrove Bank.|Zie voor meer informatie over het installeren van de Endpoint Protection-sitesysteemrol 'Vereisten' in [Endpoint Protection configureren](configure-endpoint-protection.md).|  
|Jeroen configureert de Configuration Manager voor het gebruik van een SMTP-server voor het verzenden van e-mailwaarschuwingen.<br /><br /> **Opmerking:** Alleen als u worden gewaarschuwd via e-mail wilt wanneer er een Endpoint Protection-waarschuwing wordt gegenereerd, moet u een SMTP-server configureren.|Zie voor meer informatie [waarschuwingen configureren in de Endpoint Protection](endpoint-configure-alerts.md).|  
|Jeroen maakt een apparaatverzameling met alle computers en servers om de Endpoint Protection-client te installeren. Hij noemt deze verzameling **alle Computers beveiligd door Endpoint Protection**.<br /><br /> **Tip:** U kunt geen waarschuwingen voor gebruikersverzamelingen configureren.|Zie voor meer informatie over het maken van verzamelingen [verzamelingen maken in System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Hij configureert de volgende waarschuwingen voor de verzameling: <br /><br />1) **Malware wordt gedetecteerd**: Jeroen configureert de ernst van een waarschuwing **Kritiek**. <br /><br />2) **hetzelfde type malware wordt gedetecteerd op een aantal computers** : Jeroen configureert de ernst van een waarschuwing **Kritiek** en geeft aan dat de waarschuwing wordt gegenereerd wanneer meer dan 5 procent van de computers malware is gedetecteerd. <br /><br />3) **hetzelfde type malware is herhaaldelijk gedetecteerd binnen het opgegeven interval op een computer**: Jeroen configureert de ernst van een waarschuwing **Kritiek** en geeft aan dat de waarschuwing wordt gegenereerd wanneer er malware is meer dan 5 maal gedetecteerd in een periode van 24 uur. <br /><br />4) **meerdere typen malware gedetecteerd op dezelfde computer binnen het opgegeven interval**: Jeroen configureert de ernst van een waarschuwing **Kritiek** en geeft aan dat de waarschuwing wordt gegenereerd wanneer er meer dan 3 typen malware worden gegenereerd in een periode van 24 uur.<br /><br /> De waarde voor **ernst van waarschuwing** geeft de ernst die moet worden weergegeven in de Configuration Manager-console en in waarschuwingen die hij in een e-mailbericht ontvangt.<br /><br /> Bovendien selecteert hij de optie **deze verzameling weergeven op het dashboard Endpoint Protection** zodat hij de waarschuwingen in de Configuration Manager-console kunt bewaken.|Zie 'Waarschuwingen configureren voor Endpoint Protection' [Endpoint Protection configureren in System Center Configuration Manager](endpoint-configure-alerts.md).|  
|Jeroen configureert de Configuration Manager software-updates te downloaden en implementeren van definitie-updates drie keer per dag met behulp van een regel voor automatische implementatie.|Zie voor meer informatie de sectie 'Met behulp van Configuration Manager Software-Updates te leveren definitie-Updates' in [gebruik Configuration Manager software-updates te leveren van definitie-updates](endpoint-definitions-configmgr.md).|  
|Jeroen onderzoekt de instellingen in het standaard-antimalwarebeleid. Dit bevat aanbevolen beveiligingsinstellingen van Microsoft. Hij wil dat op computers elke dag een snelle scan wordt uitgevoerd en verandert daarvoor de volgende instellingen:<br /><br /> 1) **een dagelijkse snelle scan uitvoeren op clientcomputers**: **Ja**.<br /><br /> 2) **tijd voor dagelijkse snelle scan plannen**:  **9:00 UUR**.<br /><br /> Jeroen ziet dat **Gedistribueerde updates van Microsoft Update** standaard is geselecteerd als bron voor definitie-updates. Hiermee wordt voldaan aan de vereiste van het bedrijf dat computers definities vanaf Microsoft Update downloaden wanneer ze de software-updates voor Configuration Manager kunnen niet ontvangen.|Zie [maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jeroen maakt een verzameling met de naam **Woodgrove Bank-servers**die alleen de Woodgrove Bank-servers bevat.|Zie [Verzamelingen maken in System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Jeroen maakt een aangepast antimalwarebeleid met de naam **Serverbeleid voor Woodgrove Bank**. Hij voegt alleen de instellingen voor **geplande scans** toe en brengt de volgende wijzigingen aan:<br /><br /> **Type scan**:  **Volledige**<br /><br /> **Scandag**:  **Zaterdag**<br /><br /> **Scantijd**: **1:00 UUR**<br /><br /> **Een dagelijkse snelle scan uitvoeren op clientcomputers**:  **Geen**.|Zie [maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jeroen implementeert het aangepaste antimalwarebeleid **Serverbeleid voor Woodgrove Bank** voor de verzameling **Woodgrove Bank-servers** .|Zie ' naar een antimalwarebeleid op clientcomputers implementeren' [maken en implementeren van antimalwarebeleid voor Endpoint Protection](endpoint-antimalware-policies.md) onderwerp.|  
|Jeroen maakt een nieuwe set aangepaste clientinstellingen apparaatinstellingen voor Endpoint Protection en de namen van deze **Endpoint Protection-instellingen van Woodgrove Bank**.<br /><br /> **Opmerking:** Als u niet wilt installeren en Endpoint Protection inschakelen op alle clients in uw hiërarchie, controleert u of de opties **beheren van Endpoint Protection-client op clientcomputers** en **installeren Endpoint Protection-client op clientcomputers** zijn geconfigureerd als **Nee** in de standaardinstellingen van de client.|Zie voor meer informatie [aangepaste Client-instellingen configureren voor Endpoint Protection](endpoint-protection-configure-client.md).|  
|Hij configureert de volgende instellingen voor Endpoint Protection:<br /><br /> **Endpoint Protection-client op clientcomputers beheren**:  **Ja**<br /><br /> Deze instelling en waarde zorgt ervoor dat elke bestaande Endpoint Protection-client die is geïnstalleerd door Configuration Manager wordt beheerd.<br /><br /> **Endpoint Protection-client installeren op clientcomputers**:  **Ja**.<br /><br /> **Automatisch eerder geïnstalleerde antimalwaresoftware verwijderen voordat Endpoint Protection wordt geïnstalleerd**:  **Ja**.<br /><br /> Deze instelling en waarde wordt voldaan aan de vereiste van het bedrijf dat de bestaande antimalwaresoftware wordt verwijderd voordat Endpoint Protection is geïnstalleerd en ingeschakeld.|Zie voor meer informatie [aangepaste Client-instellingen configureren voor Endpoint Protection](endpoint-protection-configure-client.md).|  
|Jeroen implementeert de **Endpoint Protection-instellingen van Woodgrove Bank** clientinstellingen voor de **alle Computers beveiligd door Endpoint Protection** verzameling.|Zie 'Aangepaste clientinstellingen voor Endpoint Protection configureren' [Endpoint Protection configureren in Configuration Manager](endpoint-antimalware-policies.md).|  
|Met de wizard Windows Firewall-beleid maken maakt Jeroen een beleid door de volgende instellingen te configureren voor het domeinprofiel:<br /><br /> 1) **Windows Firewall inschakelen**: **Ja**<br /><br /> 2)<br />                    **De gebruiker waarschuwen als Windows Firewall een nieuw programma blokkeert**: **Ja**|Zie [maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager](../../protect/deploy-use/create-windows-firewall-policies.md)|  
|Jeroen implementeert het nieuwe firewallbeleid op de verzameling **alle Computers beveiligd door Endpoint Protection** die hij eerder hebt gemaakt.|Zie ' Windows Firewall-beleid implementeren' in de [maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager](create-windows-firewall-policies.md)|  
|Jeroen gebruikt de beschikbare beheertaken voor Endpoint Protection antimalware- en Windows Firewall-beleid beheren, uitvoeren op aanvraag scannen van computers indien nodig, computers, de meest recente definities te downloaden en op te geven van alle verdere acties moeten worden ondernomen wanneer malware wordt gedetecteerd forceren.|Zie [het beheren van beleidsregels voor antimalware en firewall-instellingen voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-firewall.md)|  
|Jeroen gebruikt de volgende methoden voor het bewaken van de status van Endpoint Protection en de acties die worden uitgevoerd door Endpoint Protection:<br /><br /> 1) met behulp van de **Status van Endpoint Protection** knooppunt onder **beveiliging** in de **bewaking** werkruimte.<br /><br /> 2) met behulp van de **Endpoint Protection** knooppunt in de **activa en naleving** werkruimte.<br /><br /> 3) via de ingebouwde Configuration Manager-rapporten.|Zie [Endpoint Protection in System Center Configuration Manager controleren](monitor-endpoint-protection.md)|  

 Jeroen een succesvolle implementatie van Endpoint Protection rapporteert aan zijn manager en bevestigt dat de computers van Woodgrove Bank nu zijn beschermd tegen malware, volgens de vereisten van het bedrijf dat hij hebt opgegeven.
