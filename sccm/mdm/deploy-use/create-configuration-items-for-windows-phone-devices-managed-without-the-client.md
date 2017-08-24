---
title: Het maken van configuratie-items voor Windows Phone-apparaten worden beheerd met Intune | Microsoft Docs
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df10dc4d-c9ff-4574-bb33-8d30eb14cfe3
caps.latest.revision: "13"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: bcb2d14ef097afc2915932fe09f6d83c968aecf9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-configuration-items-for-windows-phone-devices-managed-without-the-system-center-configuration-manager-client"></a>Configuratie-items maken voor Windows Phone-apparaten die worden beheerd zonder de System Center Configuration Manager-client
De System Center Configuration Manager gebruiken**Windows Phone** configuratie-item voor het beheren van instellingen voor Windows Phone-apparaten die zijn geregistreerd bij Microsoft Intune of on-premises worden beheerd door Configuration Manager.  
  
### <a name="to-create-a-windows-phone-configuration-item"></a>Een Windows Phone-configuratie-item maken  
  
1.  Klik in de Configuration Manager-console op **activa en naleving**.  
  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  
  
3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  
  
4.  Geef op de pagina **Algemeen** van de wizard **Configuratie-item maken**een naam en een optionele beschrijving voor het configuratie-item op.  
  
5.  Onder **Geef het type configuratie-item dat u wilt maken**, selecteer **Windows Phone**.  
  
6.  Klik op **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  
  
7.  Op de **ondersteunde Platforms** pagina van de wizard de specifieke Windows Phone-platforms selecteren die het configuratie-item evalueren.  
  
8.  Op de pagina **Apparaatinstellingen** van de wizard selecteert u de instellingengroep die u wilt configureren. Zie [Naslaginformatie voor configuratie-iteminstellingen voor Windows Phone](#BKMK_Setref) in dit onderwerp voor details en klik vervolgens op **Volgende**.  
  
    > [!TIP]  
    >  Als de gewenste instelling niet wordt weergegeven, schakelt u het selectievakje **Extra instellingen configureren die niet zijn opgenomen in de standaardinstellingsgroepen**in.  
  
9. Op elke instellingenpagina configureert u de instellingen die u nodig hebt en geeft u aan of u deze wilt corrigeren wanneer ze niet compliant zijn op apparaten (wanneer dit wordt ondersteund).  
  
10. U kunt voor elke instellingengroep ook de ernst configureren die wordt gerapporteerd als wordt geconstateerd dat een configuratie-item niet compliant is:  
  
    -   **Geen** -apparaten die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
    -   **Informatie** -apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
    -   **Waarschuwing** -apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
    -   **Kritieke** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
    -   **Kritiek met gebeurtenis** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  
  
11. Op de pagina **Platformtoepasbaarheid** van de wizard controleert u alle instellingen die niet compatibel zijn met de ondersteunde platforms die u eerder hebt geselecteerd. U kunt teruggaan en deze instellingen verwijderen of u kunt doorgaan.  
  
    > [!TIP]  
    >  Niet-ondersteunde instellingen worden niet beoordeeld op compliantie.  
  
12. Voltooi de wizard.  
  
 U kunt het nieuwe configuratie-item weergeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving** .  
  
##  <a name="windows-phone-configuration-item-settings-reference"></a>Naslaginformatie voor configuratie-iteminstellingen voor Windows Phone  
  
### <a name="password"></a>Wachtwoord  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Wachtwoordinstellingen vereisen op mobiele apparaten**|Hiermee vereist u een wachtwoord op ondersteunde apparaten.|  
|**Minimale wachtwoordlengte (tekens)**|De minimale lengte van het wachtwoord.|  
|**Wachtwoordverlooptijd in dagen**|Het aantal dagen waarna een wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Voorkomt dat eerder gebruikte wachtwoorden opnieuw worden gebruikt.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Wist de gegevens op het apparaat als dit aantal aanmeldingspogingen mislukt.|  
|**Wachtwoordcomplexiteit**|Hiermee kunt u opgeven of u een pincode, zoals '1234', wilt gebruiken of dat er een sterk wachtwoord moet worden opgegeven.|  
|**Pincode voor wachtwoordherstel verzenden naar Exchange Server**||  
  
### <a name="device"></a>Apparaat  
  
|Instelling|Details|  
|-------------|-------------|  
|**Schermopname**|De gebruiker te maken van een Beeldschermopname voor het apparaat toestaan.<br /><br /> (Alleen Windows Phone 8.1)|  
|**Verzending van diagnostische gegevens**|Staat het verzenden van app- logboekbestanden toe.|  
|**Geolocatie**|Staat toe dat het apparaat gegevens van locatieservices gebruikt.<br /><br /> (Alleen Windows Phone 8.1)|  
|**Kopiëren en plakken**|Kopiëren en plakken gebruiken om gegevens te verplaatsen tussen apps.<br /><br /> (Alleen Windows Phone 8.1)|  
|**Bluetooth**|Staat het gebruik van de Bluetooth-mogelijkheden van het apparaat toe.|  
  
### <a name="email-management"></a>E-mailbeheer  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**POP- en IMAP-e-mail**|Staat verbinding met e-mailaccounts die gebruikmaken van de POP- en IMAP-standaarden toe.|  
|**Maximumtijd voor bewaren van e-mail**|De periode dat e-mail wordt bewaard voordat deze van de server wordt verwijderd.|  
|**Toegestane berichtindelingen**|U kunt opgeven of de e-mails van de gebruiker de HTML-indeling kunnen hebben of dat die alleen uit tekst zonder opmaak mogen bestaan.|  
|**Maximale grootte voor e-mail in tekst zonder opmaak (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail in tekst zonder opmaak wanneer deze automatisch wordt gedownload.|  
|**Maximumgrootte voor HTML-e-mail (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail in HTML-indeling wanneer deze automatisch wordt gedownload.|  
|**Maximale grootte van bijlage (automatisch gedownload)**|Hiermee regelt u de maximale grootte voor e-mail wanneer deze automatisch wordt gedownload.|  
|**Agendasynchronisatie**||  
|**Aangepast e-mailaccount**|Staat het gebruik van een niet-Microsoft-account op het apparaat toe.|  
|**Het Microsoft-account optioneel maken in de Windows Mail-app**|Gebruik van een Microsoft-account voor aanmelding bij Windows Mail hebben geen nodig.|  
  
### <a name="store"></a>Opslaan  
 Deze instellingen gelden voor alleen Windows Phone 8.1-apparaten.  
  
|Instelling|Details|  
|-------------|-------------|  
|**App Store**|Staat toegang tot de App Store op het apparaat toe.|  
  
### <a name="browser"></a>Browser  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Webbrowser toestaan**|In- of uitschakelen van de standaard webbrowser.|  
|**Automatisch doorvoeren**|Gebruiker kan de instellingen voor automatisch aanvullen in de browser wijzigen.|  
|**Active Scripting**|Browser kan scripts, zoals Active X-scripts, uitvoeren.|  
|**Invoegtoepassingen**|Gebruiker kan invoegtoepassingen toevoegen aan Internet Explorer.|  
|**Pop-upblokkering**|Hiermee schakelt u de pop-upblokkering voor browsers in of uit.|  
|**Fraudewaarschuwing**|Hiermee schakelt u de waarschuwingen voor mogelijke frauduleuze websites in of uit.|  
  
### <a name="internet-explorer"></a>Internet Explorer  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Altijd Niet Volgen-header verzenden**|Hiermee voorkomt u dat browsergegevens naar sites van derden worden verzonden.|  
|**Beveiligingszone intranet**||  
|**Beveiligingsniveau voor internetzone**|Hiermee stelt u het beveiligingsniveau voor de internetzone in.|  
|**Beveiligingsniveau voor intranetzone**|Hiermee stelt u het beveiligingsniveau voor de intranetzone in.|  
|**Beveiligingsniveau voor zone met vertrouwde sites**|Hiermee stelt u het beveiligingsniveau in voor de zone voor vertrouwde sites.|  
|**Beveiligingsniveau voor zone Websites met beperkte toegang**|Hiermee stelt u het beveiligingsniveau in voor de zone voor websites met beperkte toegang.|  
|**Naamruimten voor de intranetzone**||  
|**Naar een intranetsite gaan voor invoer van één woord**|Hiermee schakelt u de instelling in of uit waarmee Internet Explorer wordt toegestaan om automatisch naar een intranetsite te gaan als een geldige sitenaam wordt opgegeven zonder het voorgaande 'HTTP:'|  
|**Menuoptie Bedrijfsmodus**|Gebruikers toestaan om Bedrijfsmodus te activeren en deactiveren vanuit het menu **Extra** in Internet Explorer.|  
|**Locatie van registratierapport (URL)**|U kunt een URL opgeven waar bezochte websites worden geregistreerd als Bedrijfsmodus actief is.|  
|**Locatie van de lijst met websites van Bedrijfsmodus (URL)**|U kunt de locatie van de lijst met websites opgeven die door Bedrijfsmodus wordt gebruikt als het actief is.|  
  
### <a name="cloud"></a>Cloud  
  
|Instelling|Details|  
|-------------|-------------|  
|**Synchronisatie van instellingen**|De synchronisatie van instellingen tussen apparaten toestaan.|  
|**Synchronisatie van referenties**|De synchronisatie van referenties tussen apparaten toestaan.|  
|**Microsoft-account**|Het gebruik van een Microsoft-account op het apparaat toestaan.<br /><br /> (Alleen Windows Phone 8.1)|  
|**Synchronisatie van instellingen via verbindingen met een datalimiet**|Toestaan dat instellingen worden gesynchroniseerd wanneer er voor de internetverbinding een datalimiet geldt.|  
  
### <a name="security"></a>Beveiliging  
  
|Instelling|Details|  
|-------------|-------------|  
|**Installatie van niet-ondertekend bestand**|Staat het laden van niet-ondertekende bestanden toe.|  
|**Niet-ondertekende toepassingen**|Staat het laden van niet-ondertekende apps toe.|  
|**SMS- en MMS-berichten**|Toestaan dat met het apparaat SMS- en MMS-berichten worden verzonden.|  
|**Verwisselbare opslag**|Het gebruik van verwisselbare opslag, zoals een SD-kaart, op het apparaat toestaan.|  
|**Camera**|Gebruik van de camera op het apparaat toestaan.|  
|**Near Field Communication (NFC)**|Communicatie via NFC op het apparaat toestaan.<br /><br /> (Alleen Windows Phone 8.1)|  
|**USB-verbinding toestaan**|Toestaan dat randapparatuur verbinding maken met dit apparaat via USB.|
  
### <a name="peak-synchronization"></a>Pieksynchronisatie  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Piektijd opgeven**|Geef een venster van de tijd die wordt gebruikt door de volgende twee instellingen.|  
|**Synchronisatiefrequentie in piektijden**|Kies hoe vaak het apparaat wordt gesynchroniseerd tijdens de piektijden die u hebt opgegeven.|  
|**Synchronisatiefrequentie buiten piektijden**|Kies hoe vaak het apparaat wordt gesynchroniseerd buiten de piektijden die u hebt opgegeven.|  
  
### <a name="roaming"></a>Roaming  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Beheer van apparaten tijdens roaming**|Staat toe dat het apparaat worden beheerd door Configuration Manager bij roaming.|  
|**Software downloaden tijdens roaming**|Staat toe dat apps en software tijdens het roamen worden gedownload.|  
|**E-mail downloaden tijdens roaming**|Staat toe dat e-mail tijdens het roamen wordt gedownload.|  
|**Gegevensroaming**|Roaming tussen netwerken toestaan tijdens het ophalen van gegevens.|  
  
### <a name="encryption"></a>Versleuteling  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Versleuteling opslagkaart**|Vereist dat opslagkaarten die worden gebruikt met het apparaat zijn versleuteld.|  
|**Bestandsversleuteling op apparaat**|Vereist dat bestanden op het mobiele apparaat zijn versleuteld.|  
|**Ondertekening van e-mail vereisen**|Vereis dat e-mailberichten worden ondertekend voordat ze worden verzonden.|  
|**Handtekeningalgoritme**|Selecteer het algoritme voor het ondertekenen van e-mailberichten.|  
|**E-mailversleuteling vereisen**|Vereis dat e-mailberichten worden versleuteld voordat ze worden verzonden.|  
|**Versleutelingsalgoritme**|Selecteer het algoritme voor het versleutelen van e-mailberichten.|  
  
###  <a name="wireless-communications"></a>Draadloze communicatie  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Draadloze netwerkverbinding**|Wi-Fi-mogelijkheden van het apparaat in- of uitschakelen.|  
|**Wi-Fi-tethering**|Biedt gebruikers de mogelijkheid om hun apparaat te gebruiken als een mobiele hotspot.|  
|**Gegevens overdragen via Wi-Fi indien mogelijk**||  
|**Wi-Fi-hotspots melden**||  
  
##### <a name="to-configure-a-wireless-network-connection"></a>U kunt als volgt een draadloze netwerkverbinding configureren:  
  
1.  Klik op de pagina **Instellingen voor draadloze communicatie voor mobiele apparaten configureren** op **Toevoegen**.  
  
2.  Geef in het dialoogvenster **Draadloze netwerkverbinding** de volgende informatie op over de draadloze verbinding die wordt ingericht op mobiele apparaten:  
  
|Instelling|Meer informatie|  
|-------------|----------------------|  
|**Netwerknaam (SSID)**||  
|**Netwerkverbinding**|Kies uit **Internet** of **Werk**.|  
|**Verificatie**|Selecteer de verificatiemethode voor de draadloze verbinding:<br><br> - **Open**<br> - **Gedeeld**<br> - **WPA**<br> - **WPA-PSK**<br> - **WPA2**<br> - **WPA2-PSK**|  
|**Gegevensversleuteling**|Kies de versleutelingsmethode die wordt gebruikt voor deze verbinding. De waarden die u selecteert, kunnen verschillen naargelang de **Verificatie**methode die u hebt geselecteerd:<br><br> - **Uitgeschakeld**<br> - **WEP**<br> - **TKIP**<br> - **AES**|  
|**Sleutelindex**|Selecteer een sleutelindex van **1** tot **4** die wordt gebruikt met een instelling voor **Gegevensversleuteling** van **WEP**.|  
|**Dit netwerk maakt verbinding met internet**|Selecteer deze optie als u proxyinstellingen wilt gebruiken zodat mobiele apparaten met een draadloze verbinding in staat worden gesteld om verbinding te maken met internet.|  
|**Proxyserverinstellingen**|Geef waar nodig de waarde voor **Server** - en **Poort** -instellingen voor **HTTP**, **WAP** en **Sockets**op.|  
|**802. 1 X-netwerktoegang inschakelen**|Selecteer deze optie als u de verbinding wilt beveiligen door een EAP-type op te geven.|  
|**EAP-type:**|Kies het EAP-type dat u wilt gebruiken:<br><br> - **PEAP**<br> - **Smartcard of certificaat**|  
    
  
###  <a name="certificates"></a>Certificaten  
 Hiermee kunt u certificaten importeren die op mobiele apparaten worden geïnstalleerd.  
  
 Klik op **Importeren** en geef vervolgens de volgende waarden op:  
  
-   **Certificaatbestand** : klik op **Bladeren** en selecteer vervolgens het certificaatbestand met de extensie **.cer** die u wilt importeren.  
  
-   **Doelarchief**: kies uit de volgende opties een of meer doelarchieven waaraan het geïmporteerde certificaat wordt toegevoegd op het mobiele apparaat:  
  
    -   **Hoofdmap**  
  
    -   **CA**  
  
    -   **Normaal**  
  
    -   **Bevoegdheden**  
  
    -   **SPC**  
  
    -   **Peer**  
  
-   **Rol**: als **SPC** (Software Publisher Certificate) is geselecteerd als het doelarchief, kies dan uit de volgende opties de rol die aan het certificaat wordt gekoppeld:  
  
    -   **Mobiele Operator**  
  
    -   **Manager**  
  
    -   **Door gebruiker geverifieerd**  
  
    -   **IT-beheerder**  
  
    -   **Niet-geverifieerde gebruiker**  
  
    -   **Vertrouwde inrichtingsserver**  
  
### <a name="system-security"></a>Systeembeveiliging  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**Gebruikersaccountbeheer**|Schakelt Windows Gebruikersaccountbeheer op het apparaat in of uit.|  
|**Netwerkfirewall**|Schakelt de Windows-firewall in of uit.|  
|**Updates**|U kunt kiezen hoe Windows-software-updates naar computers worden gedownload. U kunt bijvoorbeeld updates automatisch laten downloaden, maar aan de gebruiker de keuze laten wanneer deze worden geïnstalleerd.|  
|**Minimale classificatie van updates**|U kunt de minimale classificatie selecteren van updates die naar Windows-computers worden gedownload. U kunt kiezen uit **Geen**, **Belangrijk**of **Aanbevolen**.|  
|**SmartScreen**|Windows Smart Screen in- of uitschakelen.|  
|**Virusbeveiliging**|Zorg ervoor dat het apparaat wordt beveiligd door antivirussoftware.|  
|**Handtekeningen voor virusbeveiliging zijn bijgewerkt**|Selecteer deze optie om aan te geven dat de definities voor antivirussoftware zijn bijgewerkt.|
|**Handmatige uitschrijving toestaan**|De gebruiker verwijderen we hun apparaat uit MDM.|  
  
### <a name="windows-server-work-folders"></a>Windows Server-werkmappen  
 Deze instellingen gelden voor zowel Windows Phone 8 en Windows Phone 8.1.  
  
|Instelling|Details|  
|-------------|-------------|  
|**URL voor werkmappen**|Hiermee configureert u de locatie van een Windows Server-werkmap waarmee gebruikers op hun apparaat verbinding kunnen maken.|  
  
### <a name="allowed-and-blocked-apps-list-windows-phone-81-only"></a>Lijst met toegestane en geblokkeerde apps (alleen Windows Phone 8.1)  
 Hiermee kunt u een lijst opgeven met Windows Phone-apps in uw bedrijf die compatibel of niet compatibel zijn. Apps die u als geblokkeerd opgeeft, kunnen niet door gebruikers worden geïnstalleerd. Als u een lijst met toegestane apps opgeeft, kunnen gebruikers alleen apps uit die lijst installeren.  
  
 U opgeven niet zowel toegestane en geblokkeerde apps in hetzelfde configuratie-item.  
  
> [!IMPORTANT]  
>  Als u een lijst met toegestane apps opgeeft, moet u ervoor zorgen dat de bedrijfsportal-app en alle apps die u hebt geïmplementeerd op Windows Phone 8.1-apparaten voorkomen de **toegestane** lijst met apps.  
  
##### <a name="to-specify-an-allowed-or-blocked-apps-list"></a>Een lijst met toegestane of geblokkeerde apps opgeven  
  
1.  Op de **lijst met toegestane en geblokkeerde Apps (Windows Phone 8.1)** pagina, geeft u de volgende informatie:  
  
|||  
|-|-|  
|Instelling|Meer informatie|  
|**Lijst met geblokkeerde apps**|Selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers niet mogen installeren.|  
|**Lijst met toegestane apps**|Selecteer deze optie als u een lijst wilt opgeven met apps die gebruikers mogen installeren.|  
|**Toevoegen**|Hiermee voegt u een app toe aan de geselecteerde lijst. Geef een naam van uw keuze op, eventueel de uitgever van de app, en de URL van de app in de App Store.<br /><br /> Zoek op de Windows Phone Store-pagina de app die u wilt gebruiken om de URL op te geven.<br /><br /> **Voorbeeld:** Zoek in de store naar de **Skype** app. De URL die u gebruikt, is http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51.<br /><br /> U hebt voor de bedrijfsportal-app of line-of-business-apps, niet een volledige URL, maar alleen de GUID van de app op te geven.|  
|**Bewerken**|Hiermee kunt u de naam, de uitgever en de URL van de geselecteerde app bewerken.|  
|**Verwijderen**|Hiermee verwijdert u de geselecteerde app uit de lijst.|  
|**Importereneren**|Hiermee importeert u een lijst met apps die u hebt opgegeven in een bestand met door komma's gescheiden waarden. Gebruik de notatie, toepassingsnaam, uitgever en app-URL in het bestand.|  
  
## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)