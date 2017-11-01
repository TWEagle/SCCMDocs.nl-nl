---
title: Configuratie-items maken voor Windows 8.1 en Windows 10-apparaten worden beheerd door Intune
titleSuffix: Configuration Manager
description: Gebruik het configuratie-item voor System Center Configuration Manager Windows 10 om instellingen voor Windows 10-computers te beheren.
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23e1e4dc-623a-4521-ad04-ae9482927097
caps.latest.revision: "20"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 7f5a50ae6ea05af7e864cf94df3063d70bd737b4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-create-configuration-items-for-windows-81-and-windows-10-devices-managed-without-the-system-center-configuration-manager-client"></a>Configuratie-items maken voor Windows 8.1- en Windows 10-apparaten die worden beheerd zonder de System Center Configuration Manager-client

  
 De System Center Configuration Manager gebruiken**Windows 8.1 en Windows 10** configuratie-item voor het beheren van instellingen voor Windows 8.1 en Windows 10-apparaten die zijn ingeschreven bij Microsoft Intune of on-premises worden beheerd door Configuration Manager.  
  
### <a name="to-create-a-windows-81-and-windows-10-configuration-item"></a>Een configuratie-item voor Windows 8.1 en Windows 10 maken  
  
1.  Klik in de Configuration Manager-console op **activa en naleving**.  
  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  
  
3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  
  
4.  Geef op de pagina **Algemeen** van de **Wizard Configuratie-item maken** een naam en een optionele beschrijving voor het configuratie-item op.  
  
5.  Selecteer onder **Geef het type configuratie-item op dat u wilt maken** de optie **Windows 8.1 en Windows 10**.  
  
6.  Klik op **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  
  
7.  Op de **ondersteunde Platforms** pagina van de wizard, selecteert u de specifieke Windows-platforms die het configuratie-item evalueren.  
  
8.  Op de pagina **Apparaatinstellingen** van de wizard selecteert u de instellingengroep die u wilt configureren. Zie [Naslaginformatie voor het configuratie-item voor Windows 8.1 en Windows 10](#BKMK_Setref) in dit onderwerp voor meer informatie en klik daarna op **Volgende**.  
  
    > [!TIP]  
    >  Als de gewenste instelling niet wordt weergegeven, schakelt u het selectievakje **Extra instellingen configureren die niet zijn opgenomen in de standaardinstellingsgroepen** in.  
  
9. Op elke instellingenpagina configureert u de instellingen die u nodig hebt en geeft u aan of u deze wilt corrigeren wanneer ze niet compliant zijn op apparaten (wanneer dit wordt ondersteund).  
  
10. U kunt ook de ernst die moet worden gerapporteerd als een configuratie-item niet compliant is gevonden voor elke instellingengroep configureren:  
  
    -   **Geen** -apparaten die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
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
|**Aantal onthouden wachtwoorden**|Voorkomt dat het hergebruik van eerder gebruikte wachtwoorden op.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Wist de gegevens op het apparaat als dit aantal aanmeldingspogingen mislukt.|  
|**Niet-actieve periode waarna apparaat wordt vergrendeld**|Geef aan hoe lang een apparaat inactief mag zijn (geen gebruikersinvoer heeft) voordat deze wordt vergrendeld.|  
|**Wachtwoordcomplexiteit**|Hiermee kunt u opgeven of u een pincode, zoals '1234', wilt gebruiken of dat er een sterk wachtwoord moet worden opgegeven.|  
|**Wachtwoordkwaliteit**|Hiermee selecteert u het complexiteitsniveau voor het wachtwoord en geeft u ook aan of biometrische apparaten kunnen worden gebruikt.|  
|**Pincode voor wachtwoordherstel verzenden naar Exchange Server**|-|
|**Apparaatversleuteling**|Schakel versleuteling op doelapparaten.|  
  
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
|**Bluetooth-promotie**|Het gebruik van Bluetooth-promotie toestaan.<br /><br /> (Alleen Windows 10)|  
|**Spraakopname**|Het gebruik van de spraakopnamefuncties van het apparaat toestaan.<br /><br /> (Alleen Windows 10)|
|**Cortana**|Het gebruik van de spraakassistent Cortana toestaan.<br /><br /> (Alleen Windows 10)|
|**Meldingen van Onderhoudscentrum**|In- of uitschakelen van het meldingsvenster in Windows 10. <br /><br /> (Alleen Windows 10)|
|**Wijziging regio (alleen desktop)**|Hiermee voorkomt dat de eindgebruiker de regio-instellingen op het apparaat.|
|**Wijziging kracht en slaapstand (alleen desktop)**|Hiermee voorkomt dat de eindgebruiker kracht en slaapstand instellingen op het apparaat.|
|**Wijziging van de instellingen voor taal (alleen desktop)**|Hiermee voorkomt dat gebruikers de taal-instellingen op het apparaat.|
|**Aanpassing van het systeem tijd**|Hiermee voorkomt dat de eindgebruiker wijzigen van de datum en tijd.|
|**Naam wijzigt van apparaat**|Hiermee voorkomt dat de eindgebruiker wijzigen van de naam van het apparaat.|
  
### <a name="email-management"></a>E-mailbeheer  
 Deze instellingen zijn voor apparaten met Windows 8.1 en Windows 10.  
  
|Instelling|Details|  
|-------------|-------------|  
|**POP- en IMAP-e-mail**|Staat verbinding met e-mailaccounts die gebruikmaken van de POP- en IMAP-standaarden toe.|  
|**Maximumtijd voor bewaren van e-mail**|De periode dat e-mail wordt bewaard voordat deze van de server wordt verwijderd.|  
|**Toegestane berichtindelingen**|U kunt opgeven of de e-mails van de gebruiker de HTML-indeling kunnen hebben of dat die alleen uit tekst zonder opmaak mogen bestaan.|  
|**Maximale grootte voor e-mail in tekst zonder opmaak (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail in tekst zonder opmaak wanneer deze automatisch wordt gedownload.|  
|**Maximumgrootte voor HTML-e-mail (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail in HTML-indeling wanneer deze automatisch wordt gedownload.|  
|**Maximale grootte van bijlage (automatisch gedownload)**|Hiermee configureert u de maximale grootte voor e-mail die automatisch wordt gedownload.|  
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
|**Automatische updates store-apps**|Hiermee kunt apps die zijn geïnstalleerd vanuit de Windows Store automatisch worden bijgewerkt.|
|**Gebruik alleen persoonlijke archief**|Schakel deze optie alleen zodat eindgebruikers apps downloaden uit het persoonlijke archief.|
|**Starten van de oorsprong app Store**|Gebruikt voor het uitschakelen van alle apps die zijn vooraf zijn geïnstalleerd op het apparaat of gedownload vanuit de Windows Store.|
  
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
|**Beveiligingsniveau voor internetzone**|Hiermee stelt u het beveiligingsniveau voor de internetzone in.|  
|**Beveiligingsniveau voor intranetzone**|Hiermee stelt u het beveiligingsniveau voor de intranetzone in.|  
|**Beveiligingsniveau voor zone met vertrouwde sites**|Hiermee stelt u het beveiligingsniveau in voor de zone voor vertrouwde sites.|  
|**Beveiligingsniveau voor zone Websites met beperkte toegang**|Hiermee stelt u het beveiligingsniveau in voor de zone voor websites met beperkte toegang.|  
|**Naamruimten voor de intranetzone**|Websites configureren die worden toegevoegd of verwijderd uit de intranetzone.|  
|**Naar een intranetsite gaan voor invoer van één woord**|Hiermee schakelt u de instelling in of uit waarmee Internet Explorer wordt toegestaan om automatisch naar een intranetsite te gaan als een geldige sitenaam wordt opgegeven zonder het voorgaande 'HTTP:'|  
|**Menuoptie ondernemingsmodus**|Gebruikers toestaan om Bedrijfsmodus te activeren en deactiveren vanuit het menu **Extra** in Internet Explorer.|  
|**Locatie van registratierapport (URL)**|Geef een URL op waar bezochte websites worden geregistreerd als bedrijfsmodus actief is.|  
|**Locatie van de lijst met websites van Bedrijfsmodus (URL)**|Geef de locatie van de lijst met websites die ondernemingsmodus gebruikt als het actief.|  
  
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
|**Profielbestand**|Voorziet in een VPN-profiel voor Windows RT-apparaten.<br /><br /> (Alleen Windows 8.1)|  
|**Profielnaam**|Voorziet in een VPN-profiel voor Windows RT-apparaten.<br /><br /> (Alleen Windows 8.1)|  
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
|**Beheer van apparaten tijdens roaming**|Staat toe dat het apparaat worden beheerd door Configuration Manager bij roaming.<br /><br /> (Alleen Windows 10)|  
|**Software downloaden tijdens roaming**|Staat toe dat apps en software tijdens het roamen worden gedownload.<br /><br /> (Alleen Windows 10)|  
|**E-mail downloaden tijdens roaming**|Staat toe dat e-mail tijdens het roamen wordt gedownload.<br /><br /> (Alleen Windows 10)|  
|**Gegevensroaming**|Roaming tussen netwerken toestaan tijdens het ophalen van gegevens.| 
|**VPN via mobiele verbinding**|Hiermee kunt de apparaat-VPN-verbindingen tijdens verbinding met een mobiel netwerk.<br /><br /> (Alleen Windows 10)|
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
|**Wi-Fi-hotspots melden**|-|  
|**Handmatige Wi-Fi-configuratie**|-|  
  
#### <a name="to-configure-a-wireless-network-connection"></a>U kunt als volgt een draadloze netwerkverbinding configureren:  
  
1.  Klik op de pagina **Instellingen voor draadloze communicatie voor mobiele apparaten configureren** op **Toevoegen**.  
  
2.  In de **draadloze netwerkverbinding** dialoogvenster geeft u de volgende informatie over de draadloze verbinding die zijn ingericht op mobiele apparaten:  
  
|Instelling|Meer informatie|  
|-------------|----------------------|  
|**Netwerknaam (SSID)**|Voer de naam in van het Wi-Fi-netwerk.|  
|**Netwerkverbinding**|Kies uit **Internet** of **Werk**.|  
|**Verificatie**|Selecteer de verificatiemethode voor de draadloze verbinding:<br /><br /> - **Open**<br /><br /> - **Gedeeld**<br /><br /> - **WPA**<br /><br /> - **WPA-PSK**<br /><br /> - **WPA2**<br /><br /> - **WPA2-PSK**|  
|**Gegevensversleuteling**|Kies de versleutelingsmethode die wordt gebruikt voor deze verbinding. De waarden die u kunt selecteren, verschillen naargelang de **verificatie** methode die u hebt geselecteerd:<br /><br /> - **Uitgeschakeld**<br /><br /> - **WEP**<br /><br /> - **TKIP**<br /><br /> - **AES**|  
|**Sleutelindex**|Selecteer een sleutelindex van **1** naar **4** die wordt gebruikt met een **gegevensversleuteling** instellen van **WEP**.|  
|**Dit netwerk maakt verbinding met internet**|Selecteer deze optie als u proxyinstellingen wilt gebruiken zodat mobiele apparaten met een draadloze verbinding in staat worden gesteld om verbinding te maken met internet.|  
|**Proxyserverinstellingen**|Geef waar nodig de waarde voor **Server** - en **Poort** -instellingen voor **HTTP**, **WAP** en **Sockets**op.|  
|**802. 1 X-netwerktoegang inschakelen**|Selecteer deze optie als u de verbinding wilt beveiligen door een EAP-type op te geven.|  
|**EAP-type:**|Kies het EAP-type dat u wilt gebruiken:<br /><br /> - **PEAP**<br> - **Smartcard of certificaat**|  
  
  
  
### <a name="certificates"></a>Certificaten  
 Hiermee kunt u certificaten importeren die op mobiele apparaten worden geïnstalleerd.  
  
 Klik op **Importeren** en geef vervolgens de volgende waarden op:  
  
-   **Certificaatbestand**: klik op Bladeren en selecteer vervolgens het certificaatbestand met de extensie **.cer** dat u wilt importeren.  
  
-   **Doelarchief** – Kies een of meer doelarchieven waaraan het geïmporteerde certificaat is toegevoegd op het mobiele apparaat via:  
  
    -   **Hoofdmap**  
  
    -   **CA**  
  
    -   **Normaal**  
  
    -   **Bevoegdheden**  
  
    -   **SPC**  
  
    -   **Peer**  
  
-   **Rol** – als **SPC** (Software Publisher Certificate) is geselecteerd als het doelarchief, kies de rol die is gekoppeld aan het certificaat uit:  
  
    -   **Mobiele Operator**  
  
    -   **Manager**  
  
    -   **Door gebruiker geverifieerd**  
  
    -   **IT-beheerder**  
  
    -   **Niet-geverifieerde gebruiker**  
  
    -   **Vertrouwde inrichtingsserver**  
  
### <a name="system-security"></a>Systeembeveiliging  
  
|Instelling|Details|  
|-------------|-------------|  
|**Gebruikersaccountbeheer**|Schakelt Windows Gebruikersaccountbeheer op het apparaat in of uit.|  
|**Netwerkfirewall**|Schakelt de Windows-firewall in of uit.<br /><br /> (Alleen Windows 8.1)|  
|**Updates (Windows 8.1 en lager)**|Kiezen hoe Windows-software-updates naar computers worden gedownload. U kunt bijvoorbeeld updates automatisch laten downloaden, maar aan de gebruiker de keuze laten wanneer deze worden geïnstalleerd.|  
|**Minimale classificatie van updates**|Kies de minimale classificatie van updates die zijn gedownload naar de Windows-computers, **geen**, **belangrijk**, of **aanbevolen**.|  
|**Updates (Windows 10)**|Kiezen hoe Windows-software-updates naar computers worden gedownload. U kunt bijvoorbeeld updates automatisch laten downloaden, maar aan de gebruiker de keuze laten wanneer deze worden geïnstalleerd.<br /><br /> (Alleen Windows 10)|  
|**Installatiedag**|Kies de dag wanneer updates worden geïnstalleerd.<br /><br /> (Alleen Windows 10)|  
|**Installatietijd**|Kies de tijd waarop updates worden geïnstalleerd.<br /><br /> (Alleen Windows 10)|  
|**SmartScreen**|Windows Smart Screen in- of uitschakelen.|  
|**Virusbeveiliging**|Selecteer deze optie als u wilt dat antivirussoftware op het apparaat is geïnstalleerd.|  
|**Handtekeningen voor virusbeveiliging zijn bijgewerkt**|Selecteer deze optie om aan te geven dat de virusdefinities voor anti-virus zijn bijgewerkt.|  
|**Pre-release-functies**|Staat Microsoft toe instellingen en functies van evaluatieversies te implementeren op het apparaat.<br /><br /> (Alleen Windows 10)|  
|**Handmatige installatie van basiscertificaat**|(Alleen Windows 10)| 
|**Handmatige uitschrijving toestaan**|Kan de gebruiker zelf uitschrijven uit beheer door een MDM-oplossing.| 
  
###  <a name="windows-server-work-folders"></a>Windows Server-werkmappen  
 Deze instellingen zijn voor apparaten met Windows 8.1 en Windows 10.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**URL voor werkmappen**|Hiermee configureert u de locatie van een Windows Server-werkmap waarmee gebruikers op hun apparaat verbinding kunnen maken.|  
  
### <a name="allowed-and-blocked-apps-windows-phone-only"></a>Toegestane en geblokkeerde apps (Windows Phone)  
 Hiermee kunt u een lijst opgeven van door Intune beheerde apps die in uw bedrijf compatibel of niet compatibel zijn. Windows Phone kan de installatie van deze apps toestaan of blokkeren.  
  
 U kunt niet zowel compatibele als niet-compatibele apps in hetzelfde configuratie-item opgeven.  
  
#### <a name="to-specify-apps-that-are-allowed-or-blocked"></a>Apps opgeven die worden toegestaan of geblokkeerd  
  
Op de pagina **Lijst met toegestane en geblokkeerde apps** geeft u de volgende gegevens op:  
  
|Instelling|Meer informatie|  
    |-------------|----------------------|  
    |**Lijst met geblokkeerde apps**|Selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers niet mogen installeren.|  
    |**Lijst met toegestane apps**|Selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers mogen installeren. Alle andere apps worden geblokkeerd installeert.|  
    |**Toevoegen**|Hiermee voegt u een app toe aan de geselecteerde lijst. Geef een naam van uw keuze op, eventueel de uitgever van de app, en de URL van de app in de App Store.<br /><br /> Zoek in de Windows Store de app die u wilt gebruiken om de URL op te geven.<br /><br /> Open de pagina van de app en kopieer de URL naar het klembord. U kunt deze URL nu gebruiken in de lijst met toegestane apps of de lijst met geblokkeerde apps.<br /><br /> **Voorbeeld:** Zoek in de store naar de **Skype** app. De URL die u gebruikt is **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.|  
    |**Bewerken**|Hiermee kunt u de naam, de uitgever en de URL van de geselecteerde app bewerken.|  
    |**Verwijderen**|Hiermee verwijdert u de geselecteerde app uit de lijst.|  
    |**Importereneren**|Hiermee importeert u een lijst met apps die u hebt opgegeven in een bestand met door komma's gescheiden waarden. Gebruik de notatie, toepassingsnaam, uitgever en app-URL in het bestand.|  
  
### <a name="windows-10-team"></a>Windows 10 Team  
 Deze instellingen zijn alleen voor apparaten met Windows 10 Team.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Scherm automatisch activeren wanneer sensoren detecteren dat iemand in de ruimte bevindt**|Hiermee kunt u het apparaat automatisch laten activeren als de sensor detecteert dat er iemand in de ruimte aanwezig is.|  
|**Vereiste PINCODE voor draadloze projectie**|Hiermee geeft u op of u een pincode moet invoeren voordat u de mogelijkheden voor draadloze projectie van het apparaat kunt gebruiken.|  
|**Onderhoudsvenster**|Hiermee configureert u het onderhoudsvenster waarbinnen updates op het apparaat kunnen worden uitgevoerd. U kunt de starttijd en de duur (van 1-5 uur) van het venster configureren.|
|**Operationeel inzicht van Azure**|Azure operationeel inzicht is onderdeel van de Microsoft Operations Manager-suite, verzamelt, bewaart en analyseert logbestandgegevens van Windows 10 Team-apparaten.<br>Als u wilt verbinding maken met operationeel inzicht van Azure, moet u een werkruimte-ID en een Werkruimtesleutel opgeven.| 
|**Draadloze Miracast-projectie**|Schakel deze optie als u dat het Windows 10 Team-apparaat Miracast ingeschakeld apparaten gebruiken wilt om te projecteren.<br>Als u deze optie via inschakelen **Miracast-kanaal kiezen** selecteert u het Miracast-kanaal gebruikt om inhoud te projecteren.|
|**Vergaderingsinformatie wordt weergegeven op het welkomstscherm**|Als u deze optie inschakelt, kunt u de informatie die wordt weergegeven op de **vergaderingen** tegel van de **Welkom** scherm. U kunt het volgende doen:<br><br>- **Organisator en tijd alleen weergeven**<br>- **Organisator, tijd en onderwerp (onderwerp verborgen bij privévergaderingen) weergeven**|
|**URL naar de achtergrondafbeelding van het Vergrendelingsscherm**|Gebruik deze instelling om een aangepaste achtergrond weergegeven op de **Welkom** scherm van Windows 10 Team-apparaten van de URL die u opgeeft.<br>De afbeelding moet een PNG-indeling en de URL moet beginnen met **https://**.| 
  
### <a name="windows-information-protection"></a>Windows-gegevensbeveiliging  

Met de toename van apparaten in de onderneming die het eigendom zijn van werknemers, is ook het risico toegenomen op het onbedoeld lekken van gegevens via apps en services, zoals e-mail, sociale media en de openbare cloud, die zich buiten de invloedssfeer van de onderneming bevinden. Bijvoorbeeld in het geval dat een werknemer de laatste nieuwe afbeeldingen van een technologieproject via zijn of haar persoonlijk e-mailaccount verstuurt, productinformatie in een tweet kopieert en plakt, of een voorlopig verkooprapport in de openbare cloudopslag opslaat.

Windows-beveiliging (OHW) helpt te beschermen tegen deze potentiële gegevenslekken zonder dat de gebruikerservaring van werknemers Hierdoor wordt beïnvloed. OHW helpt ook bij het beveiligen van zakelijke apps en gegevens tegen onbedoelde gegevenslekken op apparaten die eigendom zijn van enterprise- en persoonlijke apparaten die werknemers meenemen naar het werk zonder wijzigingen aan uw omgeving of andere apps.

 Configuratie-iteminstellingen voor Configuration Manager WIP beheren de lijst met apps die zijn beveiligd door EDP, de bedrijfsnetwerklocaties, niveau van bescherming en versleutelingsinstellingen.

Zie voor meer informatie over het configureren van ondernemingsgegevensbescherming met Configuration Manager [uw Ondernemingsgegevens beveiligen met Windows-beveiliging (OHW)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


### <a name="microsoft-edge"></a>Microsoft Edge  
Deze instellingen zijn voor apparaten met Windows 10 en hoger.  
  
|Naam van de instelling|Details|  
|------------------|-------------| 
|Microsoft Edge|Het gebruik van de webbrowser Edge toestaan op het apparaat.| 
|**Zoeksuggesties in de adresbalk toestaan**|Hiermee laat u uw zoekmachine sites voorstellen terwijl u zoektermen invoert.|  
|**Verzenden van intranetverkeer naar Internet Explorer toestaan**||  
|**Toestaan dat niet volgen**|Met de instellingen Do Not Track laat u aan websites weten dat u niet wilt dat uw bezoek aan de site wordt gevolgd.|  
|**SmartScreen inschakelen**|SmartScreen gebruiken om te controleren of bestanden die door gebruikers worden gedownload geen schadelijke code bevatten.|  
|**Pop-ups toestaan**|Pop-ups in browser toestaan of niet toestaan.|  
|**Cookies toestaan**|Cookies toestaan of niet toestaan.|  
|**Automatisch invullen toestaan**|Het gebruik van de functie automatisch doorvoeren van de browser Edge toestaan.|  
|**Wachtwoordbeheer toestaan**|Het gebruik van de functie wachtwoordbeheer van de browser Edge toestaan.|  
|**Locatie van sitelijst voor ondernemingsmodus**|Geeft aan waar de lijst met websites die in bedrijfsmodus worden geopend. Gebruikers kunnen deze lijst niet bewerken.|
|**Toegang tot informatie over blokkeren: vlaggen**|Voorkomen dat de eindgebruiker toegang tot de over: vlaggen pagina in Edge dat ontwikkelaars en experimentele instellingen bevat.|
|**Het SmartScreen-prompt overschrijven**|Toestaan dat de eindgebruiker voor het overslaan van de SmartScreen-filter waarschuwingen over mogelijk schadelijke websites.|
|**Het SmartScreen-prompt overschrijven voor bestanden**|Toestaan dat de eindgebruiker voor het SmartScreen-filter waarschuwingen over het downloaden mogelijk schadelijke bestanden overslaan.|
|**WebRTC localhost-IP-adres**|De gebruikers localhost IP-adres wordt weergegeven als telefoongesprekken via het web RTC protocol blokkeren.|
|**Standaardzoekmachine**|Geef de standaardzoekmachine moet worden gebruikt. Eindgebruikers kunnen deze waarde op elk gewenst moment wijzigen.|
|**OpenSearch XML-URL**|U kunt een OpenSearch XML-bestand gebruiken voor het maken van een zoekservice voor Microsoft Edge.<br>Zie voor meer informatie [OpenSearch](https://msdn.microsoft.com/library/windows/desktop/dd940337).|
|**Startpagina's (alleen desktop)**|Voeg een lijst met sites die u wilt gebruiken als startpagina in de browser Edge (alleen desktop).|  


### <a name="windows-defender"></a>Windows Defender
Deze instellingen zijn voor apparaten met Windows 10 en hoger.
 
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Real-timecontrole toestaan**|Kan het real-time scannen op malware, spyware en andere ongewenste software.|
|**Gedragscontrole toestaan**|Hiermee kunt Defender laten controleren van bepaalde bekende patronen van verdachte activiteiten op apparaten.|
|**Systeem voor Netwerkinspectie inschakelen**|Het netwerk Netwerkinspectiesysteem (NIS) helpt om apparaten te beveiligen tegen op netwerk gebaseerde exploits met behulp van de handtekeningen van bekende beveiligingsproblemen van het Microsoft Endpoint Protection Center om u te helpen detecteren en blokkeren van schadelijk verkeer.|
|**Alle downloads scannen**|Hiermee bepaalt u of Windows Defender alle bestanden die worden gedownload vanaf Internet scannen.|
|**Scannen van scripts toestaan**|Hiermee kunt Defender scripts scannen die worden gebruikt in Internet Explorer.|
|**Bestands- en programma-activiteit controleren**|Hiermee kunt Defender monitor bestands- en programma-activiteit op apparaten.
|**Dagen opgeloste malware bijhouden**|Hiermee kunt Defender laten opgeloste malware bijhouden voor het aantal dagen dat u opgeeft dat u handmatig kunt eerder aangevallen apparaten controleren. Als u het aantal dagen op 0 instelt, wordt malware blijft in de map quarantaine en wordt niet automatisch verwijderd.|
|**Toegang tot de gebruikersinterface van client toestaan**|Hiermee bepaalt u of de gebruikersinterface van Windows Defender is verborgen voor gebruikers.<br>Wanneer deze instelling wordt gewijzigd, wordt het van kracht de volgende keer dat de PC van de gebruiker opnieuw wordt opgestart.|
|**Een systeemscan plannen**|Hiermee kunt u een met volledige of snelle systeemscan plannen die regelmatig wordt uitgevoerd op de dag en het moment dat u selecteert.|
|**Een dagelijkse snelle scan plannen**|Hiermee kunt u een snelle scan plannen die dagelijks wordt uitgevoerd op het moment dat u selecteert
|**CPU-gebruik tijdens een scan beperken**|U kunt de hoeveelheid CPU die scans mogen gebruiken (van 1 tot 100) te beperken.|
|**Archiefbestanden scannen**|Hiermee kunt u Defender gearchiveerde bestanden zoals .zip- of CAB-bestanden te scannen.|
|**E-mailberichten scannen**|Hiermee kunt u Defender e-mailberichten scannen zodra ze op het apparaat binnenkomen.|
|**Verwisselbare stations scannen**|Hiermee kunt Defender verwisselbare stations, zoals USB-sticks, laten scannen.|
|**Netwerkstations scannen**|Hiermee kunt Defender bestanden op toegewezen netwerkstations scannen.<br>Als de bestanden op het station alleen-lezen zijn, is Defender een gevonden malware niet verwijderen.|
|**Scannen van bestanden die zijn geopend vanuit gedeelde netwerkmappen**|Hiermee kunt u Defender bestanden op gedeelde stations (bijvoorbeeld, die toegankelijk is vanuit een UNC-pad) scannen<br>Als de bestanden op het station alleen-lezen zijn, is Defender een gevonden malware niet verwijderen.|
|**Update-interval voor handtekeningen**|Geeft het interval op welke Defender controleert op nieuwe handtekeningbestanden.
|**Cloudbeveiliging toestaan**|Wordt toegestaan of geblokkeerd van de Microsoft Active Protection Service informatie ontvangt over malware-activiteit op apparaten die u beheert. Deze informatie wordt gebruikt voor de service in de toekomst te verbeteren.|
|**Gebruikers vragen voorbeelden te verzenden**|Hiermee bepaalt u of bestanden waarvoor u mogelijk verdere analyse automatisch naar Microsoft verzonden worden om te bepalen of deze schadelijk zijn.|
|**Detectie van mogelijk ongewenste toepassingen**|Beveiligt ingeschreven Windows-desktopapparaten tegen het uitvoeren van software die wordt geclassificeerd door Windows Defender als mogelijk ongewenst is gedefinieerd. U kunt bescherming tegen deze toepassingen worden uitgevoerd of de controlemodus gebruiken om te rapport wanneer een mogelijk ongewenste toepassing wordt geïnstalleerd.|
|**Uitsluitingen van bestanden en mappen**|Hiermee voegt u een of meer bestanden en mappen toe, zoals C:\Path of %ProgramFiles%\Path\filename.exe toe aan de uitsluitingslijst. Deze bestanden en mappen worden niet opgenomen in een realtime of geplande scans.|
|**Bestand-extensie uitsluitingen**|Een of meer bestandsextensies zoals jpg- of txt toevoegen aan de uitsluitingslijst. Alle bestanden met deze extensies worden niet opgenomen in een realtime of geplande scans.|
|**Proces-uitsluitingen**|Hiermee voegt u een of meer processen van het type .exe, .com of .scr toe aan de uitsluitingslijst. Deze processen worden niet opgenomen in een realtime of geplande scans.|

  
## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)