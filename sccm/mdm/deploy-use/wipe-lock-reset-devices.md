---
title: Gegevens beschermen met wissen op afstand, vergrendelen op afstand of wachtwoordcode opnieuw instellen met behulp van System Center Configuration Manager | Microsoft-documenten
description: Apparaatgegevens beschermen met volledig wissen, selectief wissen, vergrendelen op afstand en wachtwoordcode opnieuw instellen met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
caps.latest.revision: 18
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 351fdc6328dd0859d60e00b128963df738e69f81
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="protect-data-with-remote-wipe-lock-or-passcode-reset-by-using-system-center-configuration-manager"></a>Gegevens beschermen met wissen op afstand, vergrendelen op afstand of wachtwoordcode opnieuw instellen met behulp van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager biedt selectief wissen, volledig wissen, vergrendelen op afstand en wachtwoordcode opnieuw instellen op mogelijkheden. Op mobiele apparaten kunnen gevoelige bedrijfsgegevens worden opgeslagen en deze apparaten kunnen toegang geven tot talloze bedrijfsresources. Ter bescherming van apparaten, kunt u opdracht geven:  

- volledig wissen om het apparaat terug te zetten op de fabrieksinstellingen;  

- selectief wissen om alleen bedrijfsgegevens te verwijderen;  

- een vergrendeling op afstand om een apparaat te beveiligen dat mogelijk zoek is;  

- Opnieuw instellen van wachtwoordcode van het apparaat.  

## <a name="full-wipe"></a>Volledig wissen  
U kunt een wisopdracht geven aan een apparaat wanneer u een vermist apparaat wilt beveiligen of wanneer u een apparaat buiten actief gebruik wilt stellen.  

Geef opdracht tot **volledig wissen** van een apparaat om het apparaat terug te zetten op de fabrieksinstellingen. Hiermee verwijdert u alle bedrijfs- en gebruikersgegevens en -instellingen. U kunt volledig wissen op Windows Phone, iOS, Android en Windows 10-apparaten kunt doen.  

> [!NOTE]
> Wissen van Windows 10-apparaten-versies ouder dan versie 1511 met minder dan 4 GB aan RAM-geheugen mogelijk laat u het apparaat reageert niet. [Meer informatie](https://technet.microsoft.com/library/mt592024.aspx#full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram).

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Op afstand wissen vanuit de Configuration Manager-console  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en selecteer een verzameling.  

2. Selecteer het apparaat dat u buiten gebruik wilt stellen of wilt wissen.  

3. Kies **externe apparaat acties** in **apparaatgroep**, en kies vervolgens **buiten gebruik stellen/wissen**.  

## <a name="selective-wipe"></a>Selectief wissen  
Geef een opdracht tot **selectief wissen** van een apparaat om alleen bedrijfsgegevens te verwijderen. De volgende tabel beschrijft platform, welke gegevens worden verwijderd en de invloed van de gegevens die op het apparaat na selectief wissen blijft.  

**iOS**  

|Inhoud die wordt verwijderd wanneer u buiten gebruik van een apparaat stellen bent|iOS|  
|--------------------------------------------|---------|  
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|Apps worden verwijderd. Gegevens van bedrijfs-apps worden verwijderd.|  
|VPN- en Wi-Fi-profielen|Verwijderd.|  
|Certificaten|Verwijderd en ingetrokken.|  
|Instellingen|Verwijderd, behalve voor: **Spraakroaming toestaan**, **gegevensroaming toestaan**, en **automatische synchronisatie tijdens roamen toestaan**.|  
|Beheeragent|Beheerprofiel wordt verwijderd.|  
|E-mailprofielen|Voor e-mailprofielen instellen door Intune, het e-mailaccount en e-mail verwijderd.|  

**Android- en Android Samsung KNOX Standard**  

|Inhoud die wordt verwijderd wanneer u buiten gebruik van een apparaat stellen bent|Android|Samsung KNOX Standard|  
|--------------------------------------------|-------------|------------------|  
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|Apps en gegevens blijven geïnstalleerd.|Apps worden verwijderd.|  
|VPN- en Wi-Fi-profielen|Verwijderd.|Verwijderd.|  
|Certificaten|Ingetrokken.|Ingetrokken.|  
|Instellingen|Vereisten zijn verwijderd.|Vereisten zijn verwijderd.|  
|Beheeragent|Administratorbevoegdheden voor apparaat worden ingetrokken.|Administratorbevoegdheden voor apparaat worden ingetrokken.|  
|E-mailprofielen|Niet van toepassing.|Voor e-mailprofielen instellen door Intune, het e-mailaccount en e-mail verwijderd.|  

**Android for Work**

Tijdens het doorzoeken van selectief wissen op een Android voor werk apparaat, verwijdert het werkprofiel samen met alle gegevens, apps en instellingen in de werkprofiel op het apparaat. Dit het apparaat uit het beheer met Configuration Manager en Intune gehaald. Volledig wissen wordt niet ondersteund voor Android voor werk.

 **Windows 10, Windows 8.1, Windows RT 8.1 en Windows RT**  

|Inhoud die wordt verwijderd wanneer u buiten gebruik van een apparaat stellen bent|Windows 10-, Windows 8.1 en Windows RT 8.1|  
|---------------------------------|-------------|
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|De installatie van apps wordt ongedaan gemaakt en sideloading-codes worden verwijderd. Apps die gebruikmaken van Windows selectief wissen heeft de versleutelingscode ingetrokken en gegevens niet langer toegankelijk.|  
|VPN- en Wi-Fi-profielen|Verwijderd.|  
|Certificaten|Verwijderd en ingetrokken.|  
|Instellingen|Vereisten zijn verwijderd.|
|Beheeragent|Niet van toepassing. Beheeragent is ingebouwd in.|  
|E-mailprofielen|E-mail waarvoor EFS is ingeschakeld wordt verwijderd, waaronder de e-mailapp voor Windows-e-mail en bijlagen.|  

 **Windows 10 Mobile, Windows Phone 8.0 en Windows Phone 8.1**

|Inhoud die wordt verwijderd wanneer u buiten gebruik van een apparaat stellen bent|Windows 10 Mobile, Windows Phone 8 en Windows Phone 8.1|  
|-|-|
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|Apps worden verwijderd. Gegevens van bedrijfs-apps worden verwijderd.|  
|VPN- en Wi-Fi-profielen|Voor Windows 10 Mobile- en Windows Phone 8.1 verwijderd.|  
|Certificaten|Voor Windows Phone 8.1 verwijderd.|  
|Beheeragent|Niet van toepassing. Beheeragent is ingebouwd in.|  
|E-mailprofielen|Verwijderd (met uitzondering van Windows Phone 8.0).|  

De volgende instellingen worden ook verwijderd uit Windows 10 Mobile- en Windows Phone 8.1-apparaten:  

- **Wachtwoord vereisen voor het ontgrendelen van mobiele apparaten**  
- **Eenvoudige wachtwoorden toestaan**  
- **Minimale wachtwoordlengte**  
- **Vereist Wachtwoordtype**
- **Wachtwoord verloopt (dagen)**  
- **Wachtwoordgeschiedenis onthouden**  
- **Aantal herhaalde, mislukte aanmeldingen dat is toegestaan voordat het apparaat wordt gewist**  
- **Minuten van inactiviteit voordat wachtwoord vereist is**  
- **Vereist Wachtwoordtype – minimumaantal tekensets**  
- **Camera toestaan**
- **Versleuteling vereisen op mobiele apparaten**  
- **Verwisselbare opslag toestaan**  
- **Webbrowser toestaan**  
- **Toepassingsarchief toestaan**  
- **Schermafbeelding toestaan**  
- **Geolocatie toestaan**  
- **Microsoft-Account toestaan**  
- **Kopiëren en plakken toestaan**  
- **Wi-Fi-tethering toestaan**  
- **Automatische verbinding met gratis Wi-Fi-hotspots toestaan**  
- **Wi-Fi-hotspots toestaan**  
- **Fabrieksinstellingen terugzetten toestaan**
- **Bluetooth toestaan**  
- **NFC toestaan**
- **Wi-Fi toestaan**

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Op afstand wissen vanuit de Configuration Manager-console  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en selecteer een verzameling.  

2. Selecteer het apparaat dat u buiten gebruik wilt stellen of wilt wissen.  

3. Kies **externe apparaat acties** in **apparaatgroep**, en kies vervolgens **buiten gebruik stellen/wissen**.  

## <a name="wiping-efs-enabled-content"></a>EFS inhoud wissen  
Windows 8.1 en Windows RT 8.1 ondersteuning voor selectief wissen van EFS Encrypting File System-gecodeerde inhoud. Het volgende is van toepassing op selectief wissen van EFS-inhoud:  

- Alleen apps en gegevens die worden beveiligd door EFS met hetzelfde internetdomein als de Intune-account, worden selectief gewist. Zie [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx)voor meer informatie.  

- Als er wijzigingen zijn aangebracht aan het domein dat is gekoppeld aan EFS, de wijzigingen kunnen maximaal 48 uur duren voordat apps en gegevens die gebruikmaken van het nieuwe domein, selectief kunnen worden gewist.  

- Elk domein dat is geregistreerd bij Intune is het domein dat zal worden gewist.  

De gegevens en apps EFS selectief wissen momenteel ondersteunt zijn:  

- E-mailapp voor Windows.  

- Werkmappen.

- Bestanden en mappen die zijn gecodeerd met EFS. Zie [Aanbevolen procedures voor het Encrypting File System](http://support.microsoft.com/kb/223316)voor meer informatie.  

### <a name="best-practices-for-selective-wipe"></a>Best practices voor selectief wissen  

- Instellen van e-mailprofielen op iOS- en Windows Phone 8.1-apparaten voor een geslaagde wissen van e-mail.  

- Zorg dat de apps zijn gedistribueerd via beheer van mobiele apparaten app voor een het wissen van apps.  

- Voor iOS configureert u de instelling **back-up naar iCloud toestaan** naar **toestaan** zodat gebruikers inhoud niet kunnen terugzetten met behulp van iCloud.  

- Als een account is gedeactiveerd, vervolgens na één jaar Intune vervalt het account en wordt selectief wissen uitgevoerd.  

##  <a name="passcode-reset"></a>Wachtwoordcode opnieuw instellen  
Als een gebruiker de wachtwoordcode vergeet, kunt u helpen door de wachtwoordcode van een apparaat te verwijderen of door een nieuwe en tijdelijke wachtwoordcode op een apparaat af te dwingen. De volgende tabel geeft een lijst hoe wachtwoordcode opnieuw moet worden ingesteld op verschillende mobiele platforms.  

|Platform|Wachtwoordcode opnieuw instellen|  
|--------------|--------------------|  
|iOS|Wordt ondersteund voor het wissen van de wachtwoordcode van een apparaat. Maakt geen nieuwe tijdelijke wachtwoordcode aan.|
|Mac OS| Niet ondersteund.|
|Android|Ondersteund, en een tijdelijke wachtwoordcode aangemaakt.|
|Android for Work | Niet ondersteund.|
|Windows 10-computers|Niet ondersteund.|  
|Windows 10 mobile|Ondersteund, lid met uitzondering van Azure AD zijn van apparaten.|
|Windows Phone 8,1|Ondersteund.|  
|Windows RT 8.1 |Niet ondersteund.|  
|Windows 8.1-pc 's |Niet ondersteund.|  

#### <a name="to-reset-the-passcode-on-a-mobile-device-remotely-in-configuration-manager"></a>Vanuit Configuration Manager op afstand de wachtwoordcode opnieuw instellen op een mobiel apparaat  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en selecteer een verzameling.  

2. Selecteer het apparaat of de apparaten waarop u de wachtwoordcode opnieuw wilt instellen.  

3. Kies **externe apparaat acties** in **apparaatgroep**, en kies vervolgens **wachtwoordcode opnieuw instellen**.  

#### <a name="to-show-the-state-of-the-passcode-reset"></a>De status van het opnieuw instellen van de wachtwoordcode weergeven  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en selecteer een verzameling.  

2. Selecteer het apparaat of de apparaten waarop u de status van het opnieuw instellen van de wachtwoordcode wilt weergeven.  

3. Kies **externe apparaat acties** in **apparaatgroep**, en kies vervolgens **wachtwoordcode weergavestatus**.  

## <a name="remote-lock"></a>Vergrendelen op afstand  
Als een gebruiker het apparaat verliest, kunt u het apparaat op afstand vergrendelen. In de volgende tabel wordt vermeld hoe vergrendelen op afstand werkt op verschillende mobiele platforms.  

|Platform|Vergrendelen op afstand|  
|--------------|-----------------|  
|iOS|Ondersteund.|  
|Android|Ondersteund.|  
|Windows 10|Wordt momenteel niet ondersteund.|  
|Windows Phone 8 en Windows Phone 8.1|Ondersteund.|  
|Windows RT 8.1 |Ondersteund als de huidige gebruiker van het apparaat dezelfde gebruiker is die het apparaat heeft geregistreerd.|  
|Windows 8.1|Ondersteund als de huidige gebruiker van het apparaat dezelfde gebruiker is die het apparaat heeft geregistreerd.|  

#### <a name="to-lock-a-mobile-device-remotely-through-the-configuration-manager-console"></a>Een mobiel apparaat op afstand vanuit de Configuration Manager-console vergrendelen  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en selecteer een verzameling.  

2. Selecteer het apparaat dat of de apparaten die u wilt vergrendelen.  

3. Kies **externe apparaat acties** in **apparaatgroep**, en kies vervolgens **vergrendelen op afstand**.  

#### <a name="to-show-the-state-of-the-remote-lock"></a>De status van de externe vergrendeling weergeven  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en selecteer een verzameling.  

2. Selecteer het apparaat waarop u de status van de externe vergrendeling wilt weergeven.  

3. Kies **externe apparaat acties** in **apparaatgroep**, en kies vervolgens **status van externe vergrendeling weergeven**.  

### <a name="see-also"></a>Zie tevens  
[Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx)   

