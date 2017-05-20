---
title: Wi-Fi-profielen maken | Microsoft-documenten
description: Informatie over het gebruik van Wi-Fi-profielen in System Center Configuration Manager instellingen voor draadloze netwerken implementeren voor gebruikers in uw organisatie.
ms.custom: na
ms.date: 12/11/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 321b19b2-a093-4b8f-995f-41f74b886eb5
caps.latest.revision: 13
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f1ae976899de1fd3efcbde0c7268f071a5d0218b
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="create-wi-fi-profiles"></a>Wi-Fi-profielen maken

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Gebruik Wi-Fi-profielen in System Center Configuration Manager instellingen voor draadloze netwerken implementeren voor gebruikers in uw organisatie. Deze instellingen implementeert, makkelijker u voor uw gebruikers verbinding maken met Wi-Fi.  

 U hebt bijvoorbeeld een Wi-Fi-netwerk dat u wilt inschakelen, alle iOS-apparaten verbinding moeten maken. Een Wi-Fi-profiel met de instellingen die nodig zijn om verbinding met het draadloze netwerk te maken. Implementeer vervolgens het profiel voor alle gebruikers met iOS-apparaten in uw hiërarchie. Gebruikers van iOS-apparaten zien het bedrijfsnetwerk in de lijst met draadloze netwerken en kunnen direct verbinding maken met dit netwerk.  

 U kunt de volgende typen apparaten configureren met Wi-Fi-profielen:  

-   Apparaten met Windows 8.1 32-bits  

-   Apparaten met Windows 8.1 64-bits  

-   Apparaten met Windows RT 8.1  

-   Apparaten met Windows 10 Desktop of Mobile  

[Wi-Fi-profielen voor mobiele apparaten maken](../../mdm/deploy-use/create-wifi-profiles.md) bevat informatie over het gebruik van Wi-Fi-profielen in Configuration Manager naar de instellingen voor draadloze netwerken implementeren voor gebruikers van mobiele apparaten. "

> [!IMPORTANT]  
>  Voor de implementatie van profielen voor Android, iOS, Windows Phone-en ingeschreven Windows 8.1 of hoger apparaten, moeten deze apparaten zijn ingeschreven in Microsoft Intune. Zie voor meer informatie over het ophalen van de apparaten die zijn geregistreerd [apparaten inschrijven voor beheer in Intune](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).  

 Wanneer u een Wi-Fi-profiel maakt, kunt u een grote verscheidenheid aan beveiligingsinstellingen opnemen. Bijvoorbeeld, certificaten voor servervalidatie en clientverificatie die zijn geactiveerd met behulp van Configuration Manager-certificaatprofielen. Zie [Certificaatprofielen in System Center Configuration Manager](introduction-to-certificate-profiles.md) voor meer informatie over certificaatprofielen.  

## <a name="create-a-wi-fi-profile"></a>Een Wi-Fi-profiel maken  

1.  Kies in de Configuration Manager-console **activa en naleving** > **compatibiliteitsinstellingen** >  **toegang tot bedrijfsbronnen** > **Wi-Fi-profielen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **Wi-Fi-profiel maken**.  

1.  Op de **algemeen** pagina, voer een unieke naam en een beschrijving voor het Wi-Fi-profiel.  Als u de instellingen van een andere Wi-Fi-profiel gebruiken wilt, selecteert u **en bestaand Wi-Fi-profielitem uit een bestand importeren**.  

    > [!IMPORTANT]  
    >  Zorg ervoor dat het Wi-Fi-profiel dat u importeert geldige XML bevat voor een Wi-Fi-profiel. Configuration Manager valideert niet het profiel als u het bestand importeert.  

3.  In **ernst van niet-compatibele voor rapporten**, geef de ernst op die moet worden gerapporteerd als is geconstateerd dat het Wi-Fi-profiel niet compliant is op clientapparaten (bijvoorbeeld, als de installatie van het profiel mislukt). U kunt kiezen uit de volgende beschikbaarheidsniveaus:  

    -   **Geen**: Computers die niet voldoen aan deze compliantieregel doen geen fouternst voor Configuration Manager-rapporten.  

    -   **Informatie**: Computers die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  

    -   **Waarschuwing**: Computers die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  

    -   **Kritieke**: Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  

    -   **Kritiek met gebeurtenis**: Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  

1.  Op de **Wi-Fi-profiel** pagina geeft u de naam die op apparaten wordt weergegeven als de netwerknaam.  

    > [!IMPORTANT]  
    >  Configuration Manager biedt geen ondersteuning voor het gebruik van de apostrof (**â €˜**) of komma (**,**) in de netwerknaam.  

2.  Geef de hoofdlettergevoelige **SSID**
3.  Kies de andere toepasselijke connectiviteitsopties, met inbegrip van.   **Verbinding maken als het netwerk is de naam (SSID) niet uitzendt**als het is mogelijk dat de SSID is verborgen  

4.  Op de **Beveiligingsconfiguratie** pagina, selecteer het beveiligingsprotocol dat het draadloze netwerk of selecteer **geen verificatie (Open)** als het netwerk niet beveiligd is.
    > [!IMPORTANT]  
    >  Als u een Wi-Fi-profiel maakt op\-lokale beheer van mobiele apparaten, de huidige vertakking van Configuration Manager biedt alleen ondersteuning voor de volgende configuraties voor Wi-Fi-beveiliging:  
    >   
    >  Beveiligingstypen: **WPA2-Enterprise** of **WPA2 Personal**  
    > Versleutelingstypen: **AES** of **TKIP**  
    > EAP-typen: **Smartcard of ander certificaat** of **PEAP**  

    > Voor Android-apparaten, de beveiligingstypen **WPA Personal**, **WPA2 persoonlijke** en **WEP** worden niet ondersteund.  

2.  selecteer de versleutelingsmethode die wordt gebruikt door het draadloze netwerk.  

3.  selecteer het EAP-type dat wordt gebruikt voor verificatie met het draadloze netwerk.  

     Alleen voor apparaten met Windows Phone: de EAP-typen **LEAP** en **EAP-FAST** worden niet ondersteund.  

4.  Klik op **Configureren** om meer eigenschappen voor het geselecteerde EAP-type op te geven. Deze optie is mogelijk niet beschikbaar voor alle geselecteerde EAP-typen.  

    > [!IMPORTANT]  
    >  Wanneer u op **Configureren** klikt, wordt er een Windows-dialoogvenster geopend. Als gevolg hiervan moet u moet ervoor zorgen dat het besturingssysteem van de computer met de Configuration Manager console ondersteunt het geselecteerde EAP-type.  
    >   
    >  Voor iOS-apparaten is het zo dat, als u een niet-EAP-methode kiest voor verificatie, MS-CHAP v2 wordt gebruikt voor de verbinding, ongeacht welke methode u dan wel kiest.  

5.  Als u gebruikersreferenties wilt opslaan zodat gebruikers deze niet bij elke aanmelding hoeven in te voeren, selecteert u **Gebruikersreferenties onthouden bij elke aanmelding**.  

6. **Voor iOS-apparaten:**  
 Configureer gegevens voor de certificaten die vereist zijn voor de Wi-Fi-verbinding. U moet het clientcertificaat en de naam van het certificaat van de vertrouwde server of het basiscertificaat als volgt configureren:  

    -   **Vertrouwde servercertificaatnamen**: Als de server die het apparaat met verbindt een certificaat voor serververificatie gebruikt om te bepalen van de server en het communicatiekanaal te beveiligen, voert u de naam of namen in die certificateâ€™ s onderwerpnaam of alternatieve naam voor onderwerp. De naam of namen zijn doorgaans de FQDN-naam van de server. Als het servercertificaat bijvoorbeeld de algemene naam srv1.contoso.com in het certificaatonderwerp bevat, voert u **srv1.contoso.com** in. Als voor het servercertificaat meerdere namen zijn opgegeven als alternatieve onderwerpnaam, voert u al deze namen gescheiden door puntkomma's in.  

    > [!TIP]  
    >  Als het door u geselecteerde clientcertificaat voor EAP of clientverificatie voor een iOS-apparaat wordt gebruikt voor verificatie voor een RADIUS-server (Remote Authentication Dial-In User Service), bijvoorbeeld als een server waarop Network Policy Server wordt uitgevoerd, moet u Alternatieve naam voor onderwerp instellen op Principalnaam van gebruiker.  

    -   **Basiscertificaten voor servervalidatie selecteren**: Als de server die het apparaat verbinding met maakt een certificaat voor clientverificatie dat het apparaat niet vertrouwt, selecteert u het certificaatprofiel met het basiscertificaat voor het Webservercertificaat voor het maken van een certificaatvertrouwensketen in te richten op het apparaat.  

    -   **Selecteer een clientcertificaat voor clientverificatie**: Als de server of het netwerkapparaat een clientcertificaat om het verbindende apparaat te verifiëren vereist, selecteert u het certificaatprofiel met het certificaat voor clientverificatie.  

    > [!NOTE]  
    >  Voordat u het basiscertificaat en clientcertificaat kunt selecteren, moet u deze als een certificaatprofiel configureren en implementeren. Zie [Certificaatprofielen in System Center Configuration Manager](introduction-to-certificate-profiles.md) voor meer informatie over certificaatprofielen.  

7.  Op de **geavanceerde instellingen** pagina, geavanceerde instellingen voor de Wi-Fi-profiel, zoals de verificatiemodus, opties voor eenmalige aanmelding en Federal Information Processing Standards naleving opgeven. Raadpleeg de Windows-documentatie voor meer informatie over deze opties. Geavanceerde instellingen zijn mogelijk niet beschikbaar, of kunnen afwijken, afhankelijk van de opties die u hebt geselecteerd op de pagina **Beveiligingsconfiguratie** van de wizard.  

1.  Op de **Proxy-instellingen** optie **proxy-instellingen voor dit Wi-Fi-profiel configureren** als uw draadloze netwerk gebruikmaakt van een proxyserver en geef vervolgens de configuratie-informatie.  

2. Op de **ondersteunde Platforms** pagina, selecteert u de besturingssystemen waarop u wilt installeren van het Wi-Fi-profiel. U kunt ook op **Alles selecteren** klikken om het Wi-Fi-profiel te installeren op alle beschikbare besturingssystemen.  

### <a name="next-steps"></a>Volgende stappen
 Voor meer informatie over het implementeren van het Wi-Fi-profiel, zie [Wi-Fi-profielen implementeren in System Center Configuration Manager](deploy-wifi-vpn-email-cert-profiles.md).  

