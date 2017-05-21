---
title: Scenario Endpoint Protection beveiligt computers tegen schadelijke software | Microsoft-documenten
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
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: af0aafb4b7209d840676d16723509f399c662aad
ms.openlocfilehash: b98684d44874ff246e4d675039c6e443aee82a62
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="example-scenario-using-system-center-endpoint-protection-to-protect-computers-from-malware-in-system-center-configuration-manager"></a>Voorbeeldscenario: System Center Endpoint Protection gebruiken om computers te beveiligen tegen schadelijke software in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat een voorbeeldscenario voor hoe u Endpoint Protection in Configuration Manager implementeren kunt om computers te beveiligen in een organisatie tegen schadelijke software.  

 Johan is de Configuration Manager-beheerder bij Woodgrove Bank. System Center Endpoint Protection de bank momenteel gebruikt om computers tegen malware-aanvallen te beveiligen. Daarnaast gebruikt de bank Windows-groepsbeleid om te zorgen dat Windows Firewall is ingeschakeld op alle computers in het bedrijf en dat gebruikers een melding krijgen wanneer Windows Firewall een nieuw programma blokkeert.  

 Johan is gevraagd de Woodgrove Bank antimalware-software bijwerken naar System Center Endpoint Protection, zodat de bank kunt van de nieuwste functies anti-malware profiteren en kunnen de antimalwareoplossing centraal beheren van de Configuration Manager-console. Voor deze implementatie gelden de volgende vereisten:  

-   Configuration Manager gebruiken voor het beheren van de Windows Firewall-instellingen die al worden beheerd door Groepsbeleid.  

-   Gebruik Configuration Manager-software-updates te downloaden van definities van schadelijke software op computers. Als geen software-updates beschikbaar zijn, bijvoorbeeld omdat de computer niet is verbonden met het bedrijfsnetwerk, moeten definitie-updates op computers worden gedownload vanaf Microsoft Update.  

-   Computers van gebruikers moeten een snelle scan op malware dagelijks uitvoeren. Op servers moet echter elke zaterdag om 01:00 uur, buiten werkuren, een volledige scan worden uitgevoerd  

-   Een waarschuwing per e-mail verzenden wanneer een van de volgende gebeurtenissen optreedt:  

    -   Er wordt malware gedetecteerd op een computer  

    -   Dezelfde malwarebedreiging wordt op meer dan 5 procent van de computers gedetecteerd  

    -   Dezelfde malwarebedreiging wordt binnen een periode van 24 uur meer dan 5 maal gedetecteerd  

    -   Meer dan 3 soorten malware worden binnen een periode van 24 uur gedetecteerd  

-   De bestaande antimalwareoplossing verwijderen.  

 John voert de volgende stappen uit als u wilt implementeren, Endpoint Protection:  

##  <a name="steps-to-implement-endpoint-protection"></a>Stappen voor het implementeren van Endpoint Protection  

|Proces|Verwijzing|  
|-------------|---------------|  
|Johan bekijkt de beschikbare informatie over de basisconcepten voor Endpoint Protection in Configuration Manager.|Zie voor informatie over Endpoint Protection [Endpoint Protection in System Center Configuration Manager](endpoint-protection.md).|  
|Johan controleert en implementeert de vereisten voor het gebruik van Endpoint Protection.|Zie voor meer informatie over de vereisten voor Endpoint Protection [Planning voor Endpoint Protection](../plan-design/planning-for-endpoint-protection.md).|  
|Jeroen installeert de Endpoint Protection-sitesysteemrol op slechts één sitesysteemserver aan de bovenkant van de hiërarchie van Woodgrove Bank.|Zie voor meer informatie over het installeren van de Endpoint Protection-sitesysteemrol "Vereisten" in [Endpoint Protection configureren](configure-endpoint-protection.md).|  
|Johan configureert Configuration Manager voor gebruik van een SMTP-server om de e-mailwaarschuwingen te sturen.<br /><br /> **Opmerking:** Alleen als u worden per e-mail verwittigd wilt als er een Endpoint Protection-waarschuwing wordt gegenereerd, moet u een SMTP-server configureren.|Zie voor meer informatie [waarschuwingen configureren in de Endpoint Protection](endpoint-configure-alerts.md).|  
|Johan maakt een apparaatverzameling met alle computers en servers om de Endpoint Protection-client te installeren. Hij noemt deze verzameling **alle Computers wordt beveiligd door Endpoint Protection**.<br /><br /> **Tip:** U kunt geen waarschuwingen voor gebruikersverzamelingen configureren.|Zie voor meer informatie over het maken van verzamelingen [het maken van verzamelingen in System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Hij configureert de volgende waarschuwingen voor de verzameling: <br /><br />(1) **is Malware gedetecteerd**: Johan configureert u de ernst van een waarschuwing van **kritieke**. <br /><br />(2) **hetzelfde type malware is aangetroffen op een aantal computers** : Johan configureert u de ernst van een waarschuwing van **kritieke** en geeft aan dat de waarschuwing worden gegenereerd wanneer meer dan 5 procent van de computers malware gedetecteerd. <br /><br />(3) **hetzelfde type malware herhaaldelijk wordt gedetecteerd binnen het gespecificeerde interval op een computer**: Johan configureert u de ernst van een waarschuwing van **kritieke** en geeft aan dat de waarschuwing worden gegenereerd wanneer schadelijke software is meer dan 5 maal gedetecteerd in een periode van 24 uur. <br /><br />(4) **meerdere typen malware gedetecteerd op dezelfde computer binnen het opgegeven interval**: Johan configureert u de ernst van een waarschuwing van **kritieke** en geeft aan dat de waarschuwing worden gegenereerd wanneer er meer dan 3 soorten schadelijke software worden gegenereerd in een periode van 24 uur.<br /><br /> De waarde voor **ernst van waarschuwing** geeft de ernst die moet worden weergegeven in de Configuration Manager-console en in waarschuwingen die hij in een e-mailbericht ontvangt.<br /><br /> Bovendien selecteert hij de optie **deze verzameling weergeven in het dashboard Endpoint Protection** zodat hij de waarschuwingen in de Configuration Manager-console kunt bewaken.|Zie "Op waarschuwingen configureren voor Endpoint Protection" [Endpoint Protection configureren in System Center Configuration Manager](endpoint-configure-alerts.md).|  
|Johan configureert Configuration Manager-software-updates te downloaden en implementeren van definitie-updates drie keer per dag met behulp van een regel voor automatische implementatie.|Zie voor meer informatie de sectie 'Met behulp van Configuration Manager Software-Updates te leveren definitie-Updates' in [gebruik Configuration Manager-software-updates te leveren van definitie-updates](endpoint-definitions-configmgr.md).|  
|Jeroen onderzoekt de instellingen in het standaard-antimalwarebeleid. Dit bevat aanbevolen beveiligingsinstellingen van Microsoft. Hij wil dat op computers elke dag een snelle scan wordt uitgevoerd en verandert daarvoor de volgende instellingen:<br /><br /> (1) **een dagelijkse snelle scan uitvoeren op clientcomputers**: **Yes**.<br /><br /> (2) **tijd voor dagelijkse snelle scan plannen**:  **09:00:00 UUR**.<br /><br /> Jeroen ziet dat **Gedistribueerde updates van Microsoft Update** standaard is geselecteerd als bron voor definitie-updates. Voldaan aan de zakelijke vereiste computers definities downloaden vanaf Microsoft Update als ze geen Configuration Manager-software-updates ontvangen.|Zie [maken en implementeren van antimalware-beleidsregels voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jeroen maakt een verzameling met de naam **Woodgrove Bank-servers**die alleen de Woodgrove Bank-servers bevat.|Zie [Verzamelingen maken in System Center Configuration Manager](../../core/clients/manage/collections/create-collections.md)|  
|Jeroen maakt een aangepast antimalwarebeleid met de naam **Serverbeleid voor Woodgrove Bank**. Hij voegt alleen de instellingen voor **geplande scans** toe en brengt de volgende wijzigingen aan:<br /><br /> **Type scan**:  **Volledige**<br /><br /> **Scannen van de dag**:  **Zaterdag**<br /><br /> **Scant**: **1:00 UUR**<br /><br /> **Een dagelijkse snelle scan uitvoeren op clientcomputers**:  **No**.|Zie [maken en implementeren van antimalware-beleidsregels voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).|  
|Jeroen implementeert het aangepaste antimalwarebeleid **Serverbeleid voor Woodgrove Bank** voor de verzameling **Woodgrove Bank-servers** .|Zie "naar een anti-malwarebeleid implementeert naar clientcomputers" [maken en implementeren van antimalware-beleidsregels voor Endpoint Protection](endpoint-antimalware-policies.md) onderwerp.|  
|Johan maakt een nieuwe set aangepaste clientinstellingen apparaatinstellingen voor Endpoint Protection en noemt deze **Woodgrove Bank Endpoint Protection-instellingen**.<br /><br /> **Opmerking:** Als u niet wilt installeren en Endpoint Protection inschakelen op alle clients in uw hiërarchie, zorg ervoor dat de opties **beheren Endpoint Protection-client op clientcomputers** en **installeren Endpoint Protection-client op clientcomputers** zijn geconfigureerd als **Nee** in de standaardinstellingen van de client.|Zie voor meer informatie [aangepaste Client-instellingen configureren voor Endpoint Protection](endpoint-protection-configure-client.md).|  
|Hij configureert de volgende instellingen voor Endpoint Protection:<br /><br /> **Endpoint Protection-client op clientcomputers beheren**:  **Ja**<br /><br /> Deze instelling en waarde zorgt ervoor dat eventuele bestaande Endpoint Protection-client is geïnstalleerd door Configuration Manager wordt beheerd.<br /><br /> **Endpoint Protection-client op clientcomputers installeren**:  **Yes**.<br /><br /> **Automatisch eerder geïnstalleerde antimalwaresoftware verwijderen voordat Endpoint Protection wordt geïnstalleerd**:  **Yes**.<br /><br /> Deze instelling en waarde voldoet aan de zakelijke vereiste dat de bestaande antimalwaresoftware is verwijderd voordat Endpoint Protection is geïnstalleerd en ingeschakeld.|Zie voor meer informatie [aangepaste Client-instellingen configureren voor Endpoint Protection](endpoint-protection-configure-client.md).|  
|Johan implementeert de **Woodgrove Bank Endpoint Protection-instellingen** clientinstellingen voor de **alle Computers wordt beveiligd door Endpoint Protection** verzameling.|Zie "Aangepaste clientinstellingen voor Endpoint Protection configureren" in [Endpoint Protection configureren in Configuration Manager](endpoint-antimalware-policies.md).|  
|Met de wizard Windows Firewall-beleid maken maakt Jeroen een beleid door de volgende instellingen te configureren voor het domeinprofiel:<br /><br /> (1) **Windows Firewall inschakelen**: **Ja**<br /><br /> 2)<br />                    **De gebruiker waarschuwen wanneer Windows Firewall een nieuw programma blokkeert**: **Ja**|Zie [maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager](../../protect/deploy-use/create-windows-firewall-policies.md)|  
|Johan implementeert de nieuw firewall-beleid op de verzameling **alle Computers wordt beveiligd door Endpoint Protection** die hij eerder hebt gemaakt.|Zie "Windows Firewall-beleid implementeren" in de [maken en implementeren van Windows Firewall-beleid voor Endpoint Protection in System Center Configuration Manager](create-windows-firewall-policies.md)|  
|Johan gebruikt de beschikbare beheertaken voor Endpoint Protection om te beheren antimalware en Windows Firewall-beleid, scans van computers wanneer dat nodig is op aanvraag uitvoeren, forceren computers het meest recente definities te downloaden, en op te geven van alle verdere te ondernemen acties wanneer schadelijke software wordt gedetecteerd.|Zie [het beheren van beleidsregels voor antimalware en firewall-instellingen voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-firewall.md)|  
|Johan gebruikt de volgende methoden voor het bewaken van de status van Endpoint Protection en de acties die worden uitgevoerd door Endpoint Protection:<br /><br /> (1) via de **Status van Endpoint Protection** knooppunt onder **beveiliging** in de **bewaking** werkruimte.<br /><br /> (2) via de **Endpoint Protection** knooppunt in de **activa en naleving** werkruimte.<br /><br /> (3) met behulp van de ingebouwde Configuration Manager-rapporten.|Zie [Endpoint Protection in System Center Configuration Manager controleren](monitor-endpoint-protection.md)|  

 Johan meldt een geslaagde implementatie van Endpoint Protection aan zijn manager en bevestigt dat de computers van Woodgrove Bank nu zijn beschermd tegen schadelijke software, volgens de vereisten van het bedrijf dat hij is gegeven.

