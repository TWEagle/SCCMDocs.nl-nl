---
title: Configuratie-items voor Windows 8.1 en Windows 10-apparaten die worden beheerd door Intune maken | Microsoft-documenten
description: Gebruik de System Center Configuration Manager Windows 10 configuratie-item voor het beheren van instellingen voor Windows 10-computers.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23e1e4dc-623a-4521-ad04-ae9482927097
caps.latest.revision: 20
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: f75bac7887772119f30654fe15c16a8f993cad75
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-windows-81-and-windows-10-devices-managed-without-the-system-center-configuration-manager-client"></a>Configuratie-items maken voor Windows 8.1- en Windows 10-apparaten die worden beheerd zonder de System Center Configuration Manager-client
||  
|-|  
|Dit artikel bevat informatie over [nieuwe functionaliteit die is geïntroduceerd in versie 1602](https://technet.microsoft.com/library/mt622084.aspx) van System Center Configuration Manager \(huidige vertakking\). Als u de nieuwe functionaliteit wilt gebruiken, moet u [update 1602 installeren](https://technet.microsoft.com/library/mt607046.aspx). Als u niet hebt bijgewerkt naar de meest recente versie van Configuration Manager, kunt u [downloaden van de documentatie voor de versie die u gebruikt](https://gallery.technet.microsoft.com/Documentation-for-System-ea90eaf1) in de TechNet-galerie.|  
  
 Gebruik de System Center Configuration Manager**Windows 8.1 en Windows 10** configuratie-item voor het beheren van instellingen voor Windows 8.1 en Windows 10-apparaten die zijn ingeschreven bij Microsoft Intune of beheerde on-premises door Configuration Manager.  
  
### <a name="to-create-a-windows-81-and-windows-10-configuration-item"></a>Een configuratie-item voor Windows 8.1 en Windows 10 maken  
  
1.  Klik in de Configuration Manager-console op **activa en naleving**.  
  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  
  
3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  
  
4.  Geef op de pagina **Algemeen** van de **Wizard Configuratie-item maken** een naam en een optionele beschrijving voor het configuratie-item op.  
  
5.  Selecteer onder **Geef het type configuratie-item op dat u wilt maken** de optie **Windows 8.1 en Windows 10**.  
  
6.  Klik op **categorieën** als u maken en toewijzen van categorieën om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  
  
7.  Selecteer op de pagina **Ondersteunde platforms** van de wizard de specifieke Windows-platforms die het configuratie-item evalueren.  
  
8.  Op de pagina **Apparaatinstellingen** van de wizard selecteert u de instellingengroep die u wilt configureren. Zie [Naslaginformatie voor het configuratie-item voor Windows 8.1 en Windows 10](#BKMK_Setref) in dit onderwerp voor meer informatie en klik daarna op **Volgende**.  
  
    > [!TIP]  
    >  Als de gewenste instelling niet wordt weergegeven, schakelt u het selectievakje **Extra instellingen configureren die niet zijn opgenomen in de standaardinstellingsgroepen** in.  
  
9. Op elke instellingenpagina configureert u de instellingen die u nodig hebt en geeft u aan of u deze wilt corrigeren wanneer ze niet compliant zijn op apparaten (wanneer dit wordt ondersteund).  
  
10. U kunt voor elke instellingengroep ook de ernst configureren die wordt gerapporteerd als wordt geconstateerd dat een configuratie-item niet compliant is:  
  
    -   **Geen** -apparaten die niet voldoen aan deze compliantieregel doen geen fouternst voor Configuration Manager-rapporten.  
  
    -   **Informatie** -apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
    -   **Waarschuwing** -apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
    -   **Kritieke** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
    -   **Kritiek met gebeurtenis** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  
  
11. Op de pagina **Platformtoepasbaarheid** van de wizard controleert u alle instellingen die niet compatibel zijn met de ondersteunde platforms die u eerder hebt geselecteerd. U kunt teruggaan en deze instellingen verwijderen of u kunt doorgaan.  
  
    > [!TIP]  
    >  Niet-ondersteunde instellingen worden niet beoordeeld op compliantie.  
  
12. Voltooi de wizard.  
  
 U kunt het nieuwe configuratie-item weergeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving**.  
  
##  <a name="windows-81-and-windows-10-configuration-item-settings-reference"></a>Naslaginformatie voor het configuratie-item voor Windows 8.1 en Windows 10  
  
### <a name="password"></a>Wachtwoord  
 Deze instellingen zijn alleen voor apparaten met Windows 10 en hoger.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Wachtwoordinstellingen vereisen op mobiele apparaten**|Hiermee vereist u een wachtwoord op ondersteunde apparaten.|  
|**Minimale wachtwoordlengte (tekens)**|De minimale lengte van het wachtwoord.|  
|**Wachtwoordverlooptijd in dagen**|Het aantal dagen waarna een wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Voorkomt dat eerder gebruikte wachtwoorden opnieuw worden gebruikt.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Wist de gegevens op het apparaat als dit aantal aanmeldingspogingen mislukt.|  
|**Niet-actieve tijd voordat het apparaat wordt vergrendeld**|Geef aan hoe lang een apparaat inactief mag zijn (geen gebruikersinvoer heeft) voordat deze wordt vergrendeld.|  
|**Wachtwoordcomplexiteit**|Hiermee kunt u opgeven of u een pincode, zoals '1234', wilt gebruiken of dat er een sterk wachtwoord moet worden opgegeven.|  
|**Wachtwoordkwaliteit**|Hiermee selecteert u het complexiteitsniveau voor het wachtwoord en geeft u ook aan of biometrische apparaten kunnen worden gebruikt.|  
|**Pincode voor wachtwoordherstel verzenden naar Exchange Server**||  
  
###  <a name="device"></a>Apparaat  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Schermopname**|Staat het maken van een beeldschermopname voor het apparaat toe.<br /><br /> (Alleen Windows 10)|  
|**Verzending van diagnostische gegevens**|Staat het verzenden van app- logboekbestanden toe.<br /><br /> (Alleen Windows 8.1)|  
|**Verzending van diagnostische gegevens (Windows 10)**|Staat het verzenden van app- logboekbestanden toe.<br /><br /> (Alleen Windows 10)|  
|**Geolocatie**|Staat toe dat het apparaat gegevens van locatieservices gebruikt.<br /><br /> (Alleen Windows 10)|  
|**Kopiëren en plakken**|Kopiëren en plakken gebruiken om gegevens te verplaatsen tussen apps.<br /><br /> (Alleen Windows 10)|
|**Fabrieksinstellingen terugzetten**|Hiermee kunt de gebruiker het apparaat opnieuw instellen naar de oorspronkelijke instellingen.<br /><br /> (Alleen Windows 10)|  
|**Bluetooth**|Gebruik van de Bluetooth-mogelijkheden van het apparaat toestaan.|  
|**Modus voor Bluetooth-detectie**|Toestaan dat het apparaat door andere Bluetooth-apparaten wordt gedetecteerd.<br /><br /> (Alleen Windows 10)|  
|**Bluetooth-advertenties**|Het gebruik van Bluetooth-promotie toestaan.<br /><br /> (Alleen Windows 10)|  
|**Spraakopname**|Het gebruik van de spraakopnamefuncties van het apparaat toestaan.<br /><br /> (Alleen Windows 10)|
|**Cortana**|Het gebruik van de Cortana spraakassistent toestaan.<br /><br /> (Alleen Windows 10)|
|**Meldingen van Onderhoudscentrum**|In- of uitschakelen van het deelvenster melding in Windows 10. <br /><br /> (Alleen Windows 10)|
  
### <a name="email-management"></a>E-mailbeheer  
 Deze instellingen zijn voor apparaten met Windows 8.1 en Windows 10.  
  
|Instelling|Details|  
|-------------|-------------|  
|**POP- en IMAP-e-mail**|Staat verbinding met e-mailaccounts die gebruikmaken van de POP- en IMAP-standaarden toe.|  
|**Maximumtijd voor bewaren van e-mail**|De periode dat e-mail wordt bewaard voordat deze van de server wordt verwijderd.|  
|**Toegestane berichtindelingen**|U kunt opgeven of de e-mails van de gebruiker de HTML-indeling kunnen hebben of dat die alleen uit tekst zonder opmaak mogen bestaan.|  
|**Maximale grootte voor e-mail in tekst zonder opmaak (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail in tekst zonder opmaak wanneer deze automatisch wordt gedownload.|  
|**Maximumgrootte voor HTML-e-mail (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail in HTML-indeling wanneer deze automatisch wordt gedownload.|  
|**Maximale grootte van bijlage (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail wanneer deze automatisch wordt gedownload.|  
|**Agendasynchronisatie**|Synchronisatie van agenda's op het apparaat toestaan.|  
|**Aangepast e-mailaccount**|Staat het gebruik van een niet-Microsoft-account op het apparaat toe.|  
|**Het Microsoft-account optioneel maken in de Windows Mail-app**|Configureer deze instelling als u de vereiste voor een Microsoft-account in Windows Mail wilt verwijderen.|  
  
### <a name="store"></a>Opslaan  
 Deze instellingen zijn alleen voor apparaten met Windows 10 en hoger.  
  
|Instelling|Details|  
|-------------|-------------|  
|**App Store**|Staat toegang tot de App Store op het apparaat toe.|  
|**Een wachtwoord invoeren voor toegang tot de App Store**|Gebruikers moeten een wachtwoord invoeren voor toegang tot de App Store.|  
|**Aankopen vanuit app**|Staat gebruikers toe om aankopen te doen vanuit apps.|  
  
### <a name="browser"></a>Browser  
 Deze instellingen zijn voor apparaten met Windows 8.1 en Windows 10.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Webbrowser toestaan**|Het gebruik van de webbrowser op het apparaat toestaan.|  
|**Automatisch doorvoeren**|Gebruiker kan de instellingen voor automatisch aanvullen in de browser wijzigen.|  
|**Active Scripting**|Browser kan scripts, zoals Active X-scripts, uitvoeren.|  
|**Invoegtoepassingen**|Gebruiker kan invoegtoepassingen toevoegen aan Internet Explorer.|  
|**Pop-upblokkering**|Hiermee schakelt u de pop-upblokkering voor browsers in of uit.|  
|**Cookies**|Toestaan dat cookies op het apparaat worden opgeslagen.|  
|**Fraudewaarschuwing**|Hiermee schakelt u de waarschuwingen voor mogelijke frauduleuze websites in of uit.|  
  
###  <a name="internet-explorer"></a>Internet Explorer  
 Deze instellingen zijn voor apparaten met Windows 8.1 en Windows 10.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Altijd Niet Volgen-header verzenden**|Hiermee voorkomt u dat browsergegevens naar sites van derden worden verzonden.|  
|**Beveiligingszone intranet**|Een beveiligingsniveau toewijzen aan de beveiligingszone Intranet.|  
|**Beveiliging hendel voor internetzone**|Hiermee stelt u het beveiligingsniveau voor de internetzone in.|  
|**Beveiligingsniveau voor intranetzone**|Hiermee stelt u het beveiligingsniveau voor de intranetzone in.|  
|**Beveiligingsniveau voor zone met vertrouwde sites**|Hiermee stelt u het beveiligingsniveau in voor de zone voor vertrouwde sites.|  
|**Beveiligingsniveau voor zone Websites met beperkte toegang**|Hiermee stelt u het beveiligingsniveau in voor de zone voor websites met beperkte toegang.|  
|**Naamruimten voor de intranetzone**|Websites configureren die worden toegevoegd aan of verwijderd uit de intranetzone.|  
|**Naar een intranetsite gaan voor invoer van één woord**|Hiermee schakelt u de instelling in of uit waarmee Internet Explorer wordt toegestaan om automatisch naar een intranetsite te gaan als een geldige sitenaam wordt opgegeven zonder het voorgaande 'HTTP:'|  
|**Menuoptie ondernemingsmodus**|Gebruikers toestaan om Bedrijfsmodus te activeren en deactiveren vanuit het menu **Extra** in Internet Explorer.|  
|**Locatie van registratierapport (URL)**|U kunt een URL opgeven waar bezochte websites worden geregistreerd als Bedrijfsmodus actief is.|  
|**Locatie van de lijst met websites van Bedrijfsmodus (URL)**|U kunt de locatie van de lijst met websites opgeven die door Bedrijfsmodus wordt gebruikt als het actief is.|  
  
###  <a name="cloud"></a>Cloud  
 Deze instellingen zijn voor apparaten met Windows 8.1 en Windows 10.  
  
|Naam van de instelling|Details|Windows 8.1|Windows 10|  
|------------------|-------------|-----------------|----------------|  
|**Synchronisatie van instellingen**|De synchronisatie van instellingen tussen apparaten toestaan.|Ja|Ja|  
|**Synchronisatie van referenties**|De synchronisatie van referenties tussen apparaten toestaan.|Ja|Ja|  
|**Microsoft-account**|Het gebruik van een Microsoft-account op het apparaat toestaan.|Ja|Ja|  
|**Synchronisatie van instellingen via verbindingen met een datalimiet**|Toestaan dat instellingen worden gesynchroniseerd wanneer er voor de internetverbinding een datalimiet geldt.|Ja|Ja|  
  
###  <a name="security"></a>Beveiliging  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Installatie van niet-ondertekend bestand**|Staat het laden van niet-ondertekende bestanden toe.<br /><br /> (Alleen Windows 10)|  
|**Niet-ondertekende toepassingen**|Staat het laden van niet-ondertekende apps toe.<br /><br /> (Alleen Windows 10)|  
|**SMS- en MMS-berichten**|Toestaan dat met het apparaat SMS- en MMS-berichten worden verzonden.<br /><br /> (Alleen Windows 10)|  
|**Verwisselbare opslag**|Het gebruik van verwisselbare opslag, zoals een SD-kaart, op het apparaat toestaan.<br /><br /> (Alleen Windows 10)|  
|**Camera**|Gebruik van de camera op het apparaat toestaan.<br /><br /> (Alleen Windows 10)|  
|**Near Field Communication (NFC)**|Communicatie via NFC op het apparaat toestaan.<br /><br /> (Alleen Windows 10)|  
|**Antidiefstalmodus**|Hiermee bepaalt u of de antidiefstalmodus van Windows 10 is ingeschakeld.<br /><br /> (Alleen Windows 10)|  
|**USB-verbinding toestaan**|Hiermee kunt apparaten verbinding maken met dit apparaat met een USB-verbinding.<br /><br /> (Alleen Windows 10)|
|**Bestand voor het profiel**|Voorziet in een VPN-profiel voor Windows RT-apparaten.<br /><br /> (Alleen Windows 8.1)|  
|**De naam van profiel**|Voorziet in een VPN-profiel voor Windows RT-apparaten.<br /><br /> (Alleen Windows 8.1)|  
|**Profiel voor alle gebruikers**|Voorziet in een VPN-profiel voor Windows RT-apparaten.<br /><br /> (Alleen Windows 8.1)|  
  
###  <a name="peak-synchronization"></a>Pieksynchronisatie  
 Deze instellingen zijn alleen voor apparaten met Windows 10 en hoger.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Piektijd opgeven**|De piektijden voor synchronisatie van apparaten configureren.|  
|**Synchronisatiefrequentie in piektijden**|Configureren hoe vaak synchronisatie plaatsvindt tijdens de piekuren die u hebt geconfigureerd.|  
|**Synchronisatiefrequentie buiten piektijden**|Configureren hoe vaak synchronisatie plaatsvindt buiten de piekuren die u hebt geconfigureerd.|  
  
###  <a name="roaming"></a>Roaming  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Beheer van apparaten tijdens roaming**|Kan het apparaat kan worden beheerd door Configuration Manager bij roaming.<br /><br /> (Alleen Windows 10)|  
|**Software downloaden tijdens roaming**|Staat toe dat apps en software tijdens het roamen worden gedownload.<br /><br /> (Alleen Windows 10)|  
|**E-mail downloaden tijdens roaming**|Staat toe dat e-mail tijdens het roamen wordt gedownload.<br /><br /> (Alleen Windows 10)|  
|**Gegevensroaming**|Roaming tussen netwerken toestaan tijdens het ophalen van gegevens.| 
|**VPN via mobiele verbinding**|Hiermee kunt de apparaat-VPN-verbindingen wanneer verbonden met een mobiel netwerk.<br /><br /> (Alleen Windows 10)|
|**VPN-roaming via mobiele verbinding**|Hiermee kunt de apparaat-VPN-verbindingen tijdens roaming op een mobiel netwerk.<br /><br /> (Alleen Windows 10)| 
  
###  <a name="encryption"></a>Versleuteling  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Versleuteling opslagkaart**|Vereist dat opslagkaarten die worden gebruikt met het apparaat zijn versleuteld.<br /><br /> (Alleen Windows 10)|  
|**Bestandsversleuteling op apparaat**|Vereist dat bestanden op het apparaat zijn versleuteld.|  
|**Ondertekening van e-mail vereisen**|Vereist dat e-mailberichten worden ondertekend voordat ze worden verzonden.|  
|**Handtekeningalgoritme**|Selecteer de ondertekeningsalgoritme voor ondertekende e-mailberichten.|  
|**E-mailversleuteling vereisen**|Vereist dat e-mailberichten worden versleuteld voordat ze worden verzonden.|  
|**Versleutelingsalgoritme**|Selecteer de algoritme voor het versleutelen van e-mailberichten.|  
  
###  <a name="wireless-communications"></a>Draadloze communicatie  
 Deze instellingen zijn alleen voor apparaten met Windows 10 en hoger.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Draadloze netwerkverbinding**|Wi-Fi-mogelijkheden van het apparaat in- of uitschakelen.|  
|**Wi-Fi-tethering**|Biedt gebruikers de mogelijkheid om hun apparaat te gebruiken als een mobiele hotspot.|  
|**Gegevens overdragen via Wi-Fi indien mogelijk**|Configureer deze optie als u het gebruik van de Wi-Fi-verbinding op het apparaat wilt gebruiken, indien mogelijk.|  
|**Wi-Fi-hotspots melden**||  
|**Handmatige Wi-Fi-configuratie**||  
  
#### <a name="to-configure-a-wireless-network-connection"></a>U kunt als volgt een draadloze netwerkverbinding configureren:  
  
1.  Klik op de pagina **Instellingen voor draadloze communicatie voor mobiele apparaten configureren** op **Toevoegen**.  
  
2.  Geef in het dialoogvenster **Draadloze netwerkverbinding** de volgende informatie op over de draadloze verbinding die wordt ingericht op mobiele apparaten:  
  
|Instelling|Meer informatie|  
|-------------|----------------------|  
|**Netwerknaam (SSID)**|Voer de naam in van het Wi-Fi-netwerk.|  
|**Netwerkverbinding**|Kies uit **Internet** of **Werk**.|  
|**Verificatie**|Selecteer de verificatiemethode voor de draadloze verbinding:<br /><br /> - **Open**<br /><br /> - **Gedeeld**<br /><br /> - **WPA**<br /><br /> - **WPA-VOORAF GEDEELDE SLEUTEL**<br /><br /> - **WPA2**<br /><br /> - **WPA2-VOORAF GEDEELDE SLEUTEL**|  
|**Gegevensversleuteling**|Kies de versleutelingsmethode die wordt gebruikt voor deze verbinding. De waarden die u selecteert, kunnen verschillen naargelang de **Verificatie**methode die u hebt geselecteerd:<br /><br /> - **Uitgeschakeld**<br /><br /> - **WEP**<br /><br /> - **TKIP**<br /><br /> - **AES**|  
|**Sleutelindex**|Selecteer een sleutelindex van **1** tot **4** die wordt gebruikt met een instelling voor **Gegevensversleuteling** van **WEP**.|  
|**Dit netwerk maakt verbinding met internet**|Selecteer deze optie als u proxyinstellingen wilt gebruiken zodat mobiele apparaten met een draadloze verbinding in staat worden gesteld om verbinding te maken met internet.|  
|**Proxyserverinstellingen**|Geef waar nodig de waarde voor **Server** - en **Poort** -instellingen voor **HTTP**, **WAP** en **Sockets**op.|  
|**802. 1 X-netwerktoegang inschakelen**|Selecteer deze optie als u de verbinding wilt beveiligen door een EAP-type op te geven.|  
|**EAP-type:**|Kies het EAP-type dat u wilt gebruiken:<br /><br /> - **PEAP**<br> - **Smartcard of certificaat**|  
  
  
  
### <a name="certificates"></a>Certificaten  
 Hiermee kunt u certificaten importeren die op mobiele apparaten worden geïnstalleerd.  
  
 Klik op **Importeren** en geef vervolgens de volgende waarden op:  
  
-   **Certificaatbestand**: klik op Bladeren en selecteer vervolgens het certificaatbestand met de extensie **.cer** dat u wilt importeren.  
  
-   **Doelarchief**: kies uit de volgende opties een of meer doelarchieven waaraan het geïmporteerde certificaat wordt toegevoegd op het mobiele apparaat:  
  
    -   **Hoofdmap**  
  
    -   **CA**  
  
    -   **Normaal**  
  
    -   **Beschermde**  
  
    -   **SPC**  
  
    -   **Peer**  
  
-   **Rol**: als **SPC** (Software Publisher Certificate) is geselecteerd als het doelarchief, kies dan uit de volgende opties de rol die aan het certificaat wordt gekoppeld:  
  
    -   **Mobiele Operator**  
  
    -   **Manager**  
  
    -   **Gebruiker geverifieerd**  
  
    -   **IT-beheerder**  
  
    -   **Niet-geverifieerde gebruiker**  
  
    -   **Vertrouwde Provisioning-Server**  
  
### <a name="system-security"></a>Systeembeveiliging  
  
|Instelling|Details|  
|-------------|-------------|  
|**Gebruikersaccountbeheer**|Schakelt Windows Gebruikersaccountbeheer op het apparaat in of uit.|  
|**Netwerkfirewall**|Schakelt de Windows-firewall in of uit.<br /><br /> (Alleen Windows 8.1)|  
|**Updates (Windows 8.1 en oudere versies)**|U kunt kiezen hoe Windows-software-updates naar computers worden gedownload. U kunt bijvoorbeeld updates automatisch laten downloaden, maar aan de gebruiker de keuze laten wanneer deze worden geïnstalleerd.|  
|**Minimale classificatie van updates**|U kunt de minimale classificatie selecteren van updates die naar Windows-computers worden gedownload. U kunt kiezen uit **Geen**, **Belangrijk**of **Aanbevolen**.|  
|**Updates (Windows 10)**|U kunt kiezen hoe Windows-software-updates naar computers worden gedownload. U kunt bijvoorbeeld updates automatisch laten downloaden, maar aan de gebruiker de keuze laten wanneer deze worden geïnstalleerd.<br /><br /> (Alleen Windows 10)|  
|**Dag installeren**|Kies de dag wanneer updates worden geïnstalleerd.<br /><br /> (Alleen Windows 10)|  
|**Installatietijd**|Kies de tijd waarop updates worden geïnstalleerd.<br /><br /> (Alleen Windows 10)|  
|**SmartScreen**|Windows Smart Screen in- of uitschakelen.|  
|**Virusbeveiliging**|Selecteer deze optie als u wilt dat antivirussoftware op het apparaat is geïnstalleerd.|  
|**Handtekeningen voor virusbeveiliging zijn bijgewerkt**|Selecteer deze optie om aan te geven dat de virusdefinities voor anti-virus zijn bijgewerkt.|  
|**Pre-release functies**|Staat Microsoft toe instellingen en functies van evaluatieversies te implementeren op het apparaat.<br /><br /> (Alleen Windows 10)|  
|**Handmatige installatie van basiscertificaat**|(Alleen Windows 10)| 
|**Handmatige unenrollment toestaan**|Kan de gebruiker zelf door een MDM-oplossing beheer van uitschrijven.| 
  
###  <a name="windows-server-work-folders"></a>Windows Server-werkmappen  
 Deze instellingen zijn voor apparaten met Windows 8.1 en Windows 10.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**URL voor werkmappen**|Hiermee configureert u de locatie van een Windows Server-werkmap waarmee gebruikers op hun apparaat verbinding kunnen maken.|  
  
### <a name="allowed-and-blocked-apps-windows-phone-only"></a>Toegestane en geblokkeerde apps (Windows Phone)  
 Hiermee kunt u een lijst opgeven van door Intune beheerde apps die in uw bedrijf compatibel of niet compatibel zijn. Windows Phone kan de installatie van deze apps toestaan of blokkeren.  
  
 U kunt niet zowel compatibele als niet-compatibele apps in hetzelfde configuratie-item opgeven.  
  
#### <a name="to-specify-apps-that-will-be-allowed-or-blocked"></a>Apps opgeven die worden toegestaan of geblokkeerd  
  
1.  Op de pagina **Lijst met toegestane en geblokkeerde apps** geeft u de volgende gegevens op:  
  
    |Instelling|Meer informatie|  
    |-------------|----------------------|  
    |**Lijst met geblokkeerde apps**|Selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers niet mogen installeren.|  
    |**Lijst met toegestane apps**|Selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers mogen installeren. Van alle andere apps wordt de installatie geblokkeerd.|  
    |**Toevoegen**|Hiermee voegt u een app toe aan de geselecteerde lijst. Geef een naam van uw keuze op, eventueel de uitgever van de app, en de URL van de app in de App Store.<br /><br /> Zoek in de Windows Store de app die u wilt gebruiken om de URL op te geven.<br /><br /> Open de pagina van de app en kopieer de URL naar het klembord. U kunt deze URL nu gebruiken in de lijst met toegestane apps of de lijst met geblokkeerde apps.<br /><br /> **Voorbeeld:** Zoek in de store naar de **Skype** app. De URL die u gebruikt, is **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.|  
    |**Bewerken**|Hiermee kunt u de naam, de uitgever en de URL van de geselecteerde app bewerken.|  
    |**Verwijderen**|Hiermee verwijdert u de geselecteerde app uit de lijst.|  
    |**Importereneren**|Hiermee importeert u een lijst met apps die u hebt opgegeven in een bestand met door komma's gescheiden waarden. Gebruik de notatie, toepassingsnaam, uitgever en app-URL in het bestand.|  
  
### <a name="windows-10-team"></a>Windows 10 Team  
 Deze instellingen zijn alleen voor apparaten met Windows 10 Team.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Scherm laten activeren automatisch wanneer sensoren iemand in de ruimte detecteren**|Hiermee kunt u het apparaat automatisch laten activeren als de sensor detecteert dat er iemand in de ruimte aanwezig is.|  
|**Vereiste PINCODE voor draadloze projectie**|Hiermee geeft u op of u een pincode moet invoeren voordat u de mogelijkheden voor draadloze projectie van het apparaat kunt gebruiken.|  
|**Onderhoudsvenster**|Hiermee configureert u het onderhoudsvenster waarbinnen updates op het apparaat kunnen worden uitgevoerd. U kunt de starttijd en de duur (van 1-5 uur) van het venster configureren.|
|**Azure Operational Insights**|Azure operationeel inzicht, onderdeel van de Microsoft Operations Manager-suite worden verzameld, worden opgeslagen en analyseert Logbestandsgegevens van Windows 10 Team-apparaten.<br>Als u wilt verbinden met Azure Operational insights, moet u een werkruimte-ID en een Werkruimtesleutel opgeven.| 
|**Miracast draadloze projectie**|Schakel deze optie als u dat de Windows 10 Team apparaat Miracast ingeschakeld apparaten wilt aan het project.<br>Als u deze optie van inschakelt **Miracast kiezen channel** selecteert u het Miracast-kanaal dat is gebruikt voor het project.|
|**Informatie over vergaderingen weergegeven op het welkomstscherm**|Als u deze optie inschakelt, kunt u de informatie die wordt weergegeven op de **vergaderingen** tegel van de **Welkom** scherm. U kunt het volgende doen:<br><br>- **Beheer en de tijd alleen weergeven**<br>- **Beheer, tijd en het onderwerp (subject verborgen voor privé-vergaderingen) weergeven**|
|**URL achtergrondafbeelding Lockscreen**|Gebruik deze instelling om een aangepaste achtergrond weergegeven op de **Welkom** scherm van Windows 10 Team-apparaten van de URL die u opgeeft.<br>De afbeelding moet PNG-indeling en de URL moet beginnen met **https://**.| 
  
### <a name="windows-information-protection"></a>Windows-gegevensbeveiliging  

Met de toename van apparaten in de onderneming die het eigendom zijn van werknemers, is ook het risico toegenomen op het onbedoeld lekken van gegevens via apps en services, zoals e-mail, sociale media en de openbare cloud, die zich buiten de invloedssfeer van de onderneming bevinden. Bijvoorbeeld in het geval dat een werknemer de laatste nieuwe afbeeldingen van een technologieproject via zijn of haar persoonlijk e-mailaccount verstuurt, productinformatie in een tweet kopieert en plakt, of een voorlopig verkooprapport in de openbare cloudopslag opslaat.

Windows-beveiliging (OHW) helpt te beschermen tegen deze mogelijke gegevens lekken zonder dat de ervaring van de werknemer anders worden verstoord. OHW helpt ook zakelijke apps en gegevens tegen het lekken van gegevens per ongeluk op apparaten die eigendom zijn van enterprise- en persoonlijke apparaten die werknemers werken zonder wijzigingen aan uw omgeving of andere apps te beschermen.

 Configuration Manager WIP configuratie-item instellingen beheren voor de lijst met apps die zijn beveiligd door EDP, enterprise-netwerklocaties beveiligingsniveau en versleutelingsinstellingen.

Zie voor meer informatie over het configureren van gegevensbeveiliging enterprise met Configuration Manager [uw Ondernemingsgegevens beveiligen via Windows-beveiliging (OHW)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


### <a name="microsoft-edge"></a>Microsoft Edge  
Deze instellingen zijn voor apparaten met Windows 10 en hoger.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Zoeksuggesties in de adresbalk toestaan**|Hiermee laat u uw zoekmachine sites voorstellen terwijl u zoektermen invoert.|  
|**Verzenden van intranetverkeer naar Internet Explorer toestaan**||  
|**Toestaan dat niet volgen**|Met de instellingen Do Not Track laat u aan websites weten dat u niet wilt dat uw bezoek aan de site wordt gevolgd.|  
|**SmartScreen inschakelen**|SmartScreen gebruiken om te controleren of bestanden die door gebruikers worden gedownload geen schadelijke code bevatten.|  
|**Pop-ups toestaan**|Pop-ups in browser toestaan of niet toestaan.|  
|**Cookies toestaan**|Cookies toestaan of niet toestaan.|  
|**Automatisch invullen toestaan**|Het gebruik van de functie automatisch doorvoeren van de browser Edge toestaan.|  
|**Wachtwoordbeheerder toestaan**|Het gebruik van de functie wachtwoordbeheer van de browser Edge toestaan.|  
|**Locatie van sitelijst ondernemingsmodus**|Geeft de plaats aan van de lijst met websites die in Bedrijfsmodus worden geopend. Gebruikers kunnen deze lijst niet bewerken.|  


### <a name="windows-defender"></a>Windows Defender
Deze instellingen zijn voor apparaten met Windows 10 en hoger.
 
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Realtime-controle toestaan**|U kunt real scannen op malware, spyware en andere ongewenste software.|
|**Bewaking van gedrag toestaan**|Hiermee kunt Defender controleren op bepaalde bekende patronen van verdachte activiteiten op apparaten.|
|**Systeem voor Netwerkinspectie inschakelen**|Het systeem voor Netwerkinspectie (NIS) helpt om apparaten te beveiligen tegen netwerk gebaseerde aanvallen met behulp van de handtekeningen van bekende beveiligingsproblemen van het Microsoft Endpoint Protection Center om u te helpen detecteren en schadelijke verkeer blokkeren.|
|**Alle downloads scannen**|Bepaalt of gescand alle bestanden die worden gedownload vanaf het Internet.|
|**Scannen van scripts toestaan**|Hiermee kunt scripts moet scannen die worden gebruikt in Internet Explorer Defender.|
|**Bestands- en programma-activiteit controleren**|Hiermee kunt Defender bestands- en programma-activiteit controleren op apparaten.
|**Dagen tot opgeloste malware bijhouden**|Hiermee kunt Defender blijven opgeloste malware bijhouden voor het aantal dagen die u opgeeft, zodat u kunt handmatig de selectievakje eerder apparaten beïnvloed. Als u het aantal dagen op 0 instelt, malware blijft in de map quarantaine en wordt niet automatisch verwijderd.|
|**Toegang tot gebruikersinterface voor client toestaan**|Bepaalt of de gebruikersinterface van Windows Defender is verborgen voor gebruikers.<br>Wanneer deze instelling wordt gewijzigd, deze van kracht zodra die de gebruiker PC opnieuw is opgestart.|
|**Een systeemscan plannen**|Hiermee kunt u bij het plannen van een volledige of snelle systeemscan die regelmatig wordt uitgevoerd op de dag en tijd die u selecteert.|
|**Een dagelijkse snelle scan plannen**|Hiermee kunt u een snelle scan dat dagelijks op het moment dat u selecteert plannen
|**CPU-gebruik tijdens een scan beperken**|U kunt de hoeveelheid CPU die scans mogen gebruiken (van 1 tot 100) beperken.|
|**Archiefbestanden scannen**|Hiermee kunt u Defender gearchiveerde bestanden zoals .zip- of CAB-bestanden te scannen.|
|**E-mailberichten scannen**|Hiermee kunt u Defender e-mailberichten scannen naarmate ze op het apparaat binnenkomen.|
|**Verwisselbare stations scannen**|Hiermee kunt Defender verwisselbare stations, zoals USB-sticks scannen.|
|**Toegewezen stations scannen**|Hiermee kunt bestanden op toegewezen netwerkstations scannen Defender.<br>Als de bestanden op de schijf alleen-lezen zijn, worden Defender kan niet worden verwijderd van eventuele gevonden in deze malware.|
|**Scannen van bestanden die zijn geopend vanuit gedeelde netwerkmappen**|Hiermee kunt Defender scannen bestanden op gedeelde stations (bijvoorbeeld, die toegankelijk is via een UNC-pad)<br>Als de bestanden op de schijf alleen-lezen zijn, worden Defender kan niet worden verwijderd van eventuele gevonden in deze malware.|
|**Handtekening-update-interval**|Hiermee geeft u het interval voor nieuwe handtekeningbestanden welke Defender controles.
|**Cloudbeveiliging toestaan**|Toegestaan of geblokkeerd van de Microsoft Active Protection Service van de ontvangende informatie over malware-activiteit van apparaten die u beheert. Deze informatie wordt gebruikt voor het verbeteren van de service in de toekomst.|
|**Gebruikers vragen voorbeelden te verzenden**|Bepaalt of bestanden die verder analysis door Microsoft moeten mogelijk of schadelijke zijn automatisch naar Microsoft worden verzonden.|
|**Detectie van een potentieel ongewenste toepassing**|Beveiligt ingeschreven Windows-bureaublad apparaten op actieve wordt geclassificeerd door Windows Defender als mogelijk ongewenste software. U kunt beschermen tegen deze toepassingen die worden uitgevoerd, of controlemodus rapport gebruiken wanneer een potentieel ongewenste toepassing wordt geïnstalleerd.|
|**Uitsluitingen van bestanden en mappen**|Een of meer bestanden en mappen zoals C:\Path of %ProgramFiles%\Path\filename.exe toegevoegd aan de lijst met uitzonderingen. Deze bestanden en mappen worden niet opgenomen in een realtime of geplande scans.|
|**Bestand extensie uitsluitingen**|Een of meer bestandsextensies zoals jpg- of txt toevoegen aan de lijst met uitzonderingen. Bestanden met de volgende extensies zijn niet opgenomen in een realtime of geplande scans.|
|**Proces uitsluitingen**|Een of meer processen van het type .exe, .com of .scr toegevoegd aan de lijst met uitzonderingen. Deze processen zijn niet opgenomen in een realtime of geplande scans.|

  
## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd zonder dat de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
