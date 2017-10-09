---
title: Gegevens beschermen met wissen op afstand, vergrendelen of opnieuw instellen met behulp van System Center Configuration Manager van wachtwoordcode | Microsoft Docs
description: Apparaatgegevens beveiligen met volledig wissen, selectief wissen, vergrendelen op afstand en wachtwoordcode opnieuw instellen met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 09/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: ea92d7b4656a04f312f04c19cac6b17df931c9c5
ms.sourcegitcommit: db079cd7322e7d4926b2df0ccb37e752c570d902
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/28/2017
---
# <a name="protect-data-with-remote-wipe-lock-or-passcode-reset-by-using-system-center-configuration-manager"></a>Gegevens beschermen met wissen op afstand, vergrendelen of de wachtwoordcode opnieuw instellen met behulp van System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager biedt selectief wissen, volledig wissen, vergrendelen op afstand en wachtwoordcode opnieuw instellen van mogelijkheden. Op mobiele apparaten kunnen gevoelige bedrijfsgegevens worden opgeslagen en deze apparaten kunnen toegang geven tot talloze bedrijfsresources. Om apparaten te beveiligen, kunt u het volgende uitgeven:  

- volledig wissen om het apparaat terug te zetten op de fabrieksinstellingen;  

- selectief wissen om alleen bedrijfsgegevens te verwijderen;  

- een vergrendeling op afstand om een apparaat te beveiligen dat mogelijk zoek is;  

- Opnieuw instellen van wachtwoordcode van het apparaat.  

## <a name="full-wipe"></a>Volledig wissen  
U kunt een wisopdracht geven aan een apparaat wanneer u een vermist apparaat wilt beveiligen of wanneer u een apparaat buiten actief gebruik wilt stellen.  

Geef opdracht tot **volledig wissen** van een apparaat om het apparaat terug te zetten op de fabrieksinstellingen. Hiermee verwijdert u alle bedrijfs- en gebruikersgegevens en -instellingen. U kunt volledig wissen op Windows Phone, iOS, Android en Windows 10-apparaten kunt doen.  

> [!NOTE]
> Wissen van Windows 10-apparaten in versies eerder dan versie 1511 met minder dan 4 GB RAM-geheugen, blijft het apparaat niet reageert. [Meer informatie](https://technet.microsoft.com/library/mt592024.aspx#full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram).

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Op afstand wissen vanuit de Configuration Manager-console  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en een verzameling selecteren.  

2. Selecteer het apparaat dat u buiten gebruik wilt stellen of wilt wissen.  

3. Kies **acties extern apparaat** in **apparaatgroep**, en kies vervolgens **buiten gebruik stellen/wissen**.  

## <a name="selective-wipe"></a>Selectief wissen  
Geef een opdracht tot **selectief wissen** van een apparaat om alleen bedrijfsgegevens te verwijderen. De volgende tabel beschrijft per platform, welke gegevens worden verwijderd en de gevolgen zijn voor gegevens die op het apparaat na selectief wissen achterblijven.  

**iOS**  

|Inhoud verwijderd wanneer u buiten gebruik van een apparaat stellen bent|iOS|  
|--------------------------------------------|---------|  
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|Apps worden verwijderd. Gegevens van bedrijfs-apps worden verwijderd.|  
|VPN- en Wi-Fi-profielen|Verwijderd.|  
|Certificaten|Verwijderd en ingetrokken.|  
|Instellingen|Verwijderd, behalve voor: **Spraakroaming toestaan**, **gegevensroaming toestaan**, en **automatische synchronisatie tijdens roamen toestaan**.|  
|Beheeragent|Beheerprofiel wordt verwijderd.|  
|E-mailprofielen|Voor e-mailprofielen die zijn ingesteld door Intune, worden het e-mailaccount en e-mail verwijderd.|  

**Android- en Android Samsung KNOX Standard**  

|Inhoud verwijderd wanneer u buiten gebruik van een apparaat stellen bent|Android|Samsung KNOX Standard|  
|--------------------------------------------|-------------|------------------|  
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|Apps en gegevens blijven geïnstalleerd.|Apps worden verwijderd.|  
|VPN- en Wi-Fi-profielen|Verwijderd.|Verwijderd.|  
|Certificaten|Ingetrokken.|Ingetrokken.|  
|Instellingen|Vereisten worden verwijderd.|Vereisten worden verwijderd.|  
|Beheeragent|Administratorbevoegdheden voor apparaat worden ingetrokken.|Administratorbevoegdheden voor apparaat worden ingetrokken.|  
|E-mailprofielen|Niet van toepassing.|Voor e-mailprofielen die zijn ingesteld door Intune, worden het e-mailaccount en e-mail verwijderd.|  

**Android for Work**

Selectief wissen op een Android-apparaat werk te doen, verwijdert het profiel werk samen met alle gegevens, apps en instellingen in de work-profiel op dat apparaat. Deze beheerder het apparaat uit beheer met Configuration Manager en Intune. Volledig wissen wordt niet ondersteund voor Android for Work.

 **Windows 10, Windows 8.1, Windows RT 8.1 en Windows RT**  

|Inhoud verwijderd wanneer u buiten gebruik van een apparaat stellen bent|Windows 10, Windows 8.1 en Windows RT 8.1|  
|---------------------------------|-------------|
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|De installatie van apps wordt ongedaan gemaakt en sideloading-codes worden verwijderd. Apps die gebruikmaken van Windows selectief wissen heeft de versleutelingscode ingetrokken en gegevens niet langer toegankelijk.|  
|VPN- en Wi-Fi-profielen|Verwijderd.|  
|Certificaten|Verwijderd en ingetrokken.|  
|Instellingen|Vereisten worden verwijderd.|
|Beheeragent|Niet van toepassing. Beheeragent is ingebouwd in.|  
|E-mailprofielen|E-mail waarvoor EFS is ingeschakeld wordt verwijderd, waaronder de e-mailapp voor Windows-e-mail en bijlagen.|  

 **Windows 10 Mobile, Windows Phone 8.0 en Windows Phone 8.1**

|Inhoud verwijderd wanneer u buiten gebruik van een apparaat stellen bent|Windows 10 Mobile, Windows Phone 8 en Windows Phone 8.1|  
|-|-|
|Bedrijfs-apps en de bijbehorende gegevens die zijn geïnstalleerd met behulp van Configuration Manager en Intune|Apps worden verwijderd. Gegevens van bedrijfs-apps worden verwijderd.|  
|VPN- en Wi-Fi-profielen|Voor Windows 10 Mobile en Windows Phone 8.1 verwijderd.|  
|Certificaten|Voor Windows Phone 8.1 verwijderd.|  
|Beheeragent|Niet van toepassing. Beheeragent is ingebouwd in.|  
|E-mailprofielen|Verwijderd (met uitzondering van Windows Phone 8.0).|  

De volgende instellingen worden ook verwijderd uit Windows 10 Mobile en Windows Phone 8.1-apparaten:  

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
- **Rapportage van Wi-Fi-hotspots toestaan**  
- **Fabrieksinstellingen terugzetten toestaan**
- **Bluetooth toestaan**  
- **NFC toestaan**
- **Wi-Fi toestaan**

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Op afstand wissen vanuit de Configuration Manager-console  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en een verzameling selecteren.  

2. Selecteer het apparaat dat u buiten gebruik wilt stellen of wilt wissen.  

3. Kies **acties extern apparaat** in **apparaatgroep**, en kies vervolgens **buiten gebruik stellen/wissen**.  

## <a name="wiping-efs-enabled-content"></a>EFS inhoud wissen  
Windows 8.1 en Windows RT 8.1 ondersteuning voor selectief wissen van EFS Encrypting File System-gecodeerde inhoud. Het volgende is van toepassing op selectief wissen van EFS-inhoud:  

- Alleen apps en gegevens die zijn beveiligd door EFS via hetzelfde internetdomein als de Intune-account, worden selectief gewist. Zie [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx)voor meer informatie.  

- Als er wijzigingen zijn aangebracht aan het domein dat is gekoppeld aan EFS, de wijzigingen kunnen maximaal 48 uur duren voordat apps en gegevens die gebruikmaken van het nieuwe domein, selectief kunnen worden gewist.  

- Elk domein dat is geregistreerd bij Intune is het domein dat zal worden gewist.  

De gegevens en apps EFS selectief wissen op dit moment ondersteunt zijn:  

- E-mailapp voor Windows.  

- Werkmappen.

- Bestanden en mappen die zijn gecodeerd met EFS. Zie [Aanbevolen procedures voor het Encrypting File System](http://support.microsoft.com/kb/223316)voor meer informatie.  

### <a name="best-practices-for-selective-wipe"></a>Best practices voor selectief wissen  

- Voor een het wissen van e-mail, stelt u het e-mailprofielen op iOS- en Windows Phone 8.1-apparaten.  

- Zorg dat de apps zijn gedistribueerd via beheer van Apps voor mobiele apparaten voor een het wissen van apps.  

- Voor iOS configureert u de instelling **back-up naar iCloud toestaan** naar **Disallow** zodat gebruikers inhoud kunnen niet herstellen met behulp van iCloud.  

- Als een account is gedeactiveerd, vervolgens na één jaar Intune wordt buiten gebruik stellen van het account en selectief wissen wordt uitgevoerd.  

##  <a name="passcode-reset"></a>Wachtwoordcode opnieuw instellen  
Als een gebruiker de wachtwoordcode vergeet, kunt u helpen door de wachtwoordcode van een apparaat te verwijderen of door een nieuwe en tijdelijke wachtwoordcode op een apparaat af te dwingen. De volgende tabel geeft een lijst hoe de wachtwoordcode opnieuw werkt op verschillende mobiele platforms.  

|Platform|Wachtwoordcode opnieuw instellen|  
|--------------|--------------------|  
|iOS|Wordt ondersteund voor het wissen van de wachtwoordcode van een apparaat. Maakt geen nieuwe tijdelijke wachtwoordcode aan.|
|Mac OS| Niet ondersteund.|
|Android|Ondersteund, en een tijdelijke wachtwoordcode aangemaakt.|
|Android for Work | Niet ondersteund.|
|Windows 10-pc 's|Niet ondersteund.|  
|Windows 10 mobile|Ondersteund, met uitzondering van Azure AD lid zijn van apparaten.|
|Windows Phone 8,1|Ondersteund.|  
|Windows RT 8.1 |Niet ondersteund.|  
|Windows 8.1-pc 's |Niet ondersteund.|  

> [!Note]    
> U moet de wachtwoordcode opnieuw instellen van actie uitvoeren vanaf de site op het hoogste niveau in uw omgeving. Bijvoorbeeld, als u een centrale beheersite gebruikt, kunt u alleen de actie uitvoeren op die site. Als u een zelfstandige primaire site, kunt u de actie alleen uitvoeren op die site.

#### <a name="to-reset-the-passcode-on-a-mobile-device-remotely-in-configuration-manager"></a>Vanuit Configuration Manager op afstand de wachtwoordcode opnieuw instellen op een mobiel apparaat  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en een verzameling selecteren.  

2. Selecteer het apparaat of de apparaten waarop u de wachtwoordcode opnieuw wilt instellen.  

3. Kies **acties extern apparaat** in **apparaatgroep**, en kies vervolgens **wachtwoordcode opnieuw instellen**.  

#### <a name="to-show-the-state-of-the-passcode-reset"></a>De status van het opnieuw instellen van de wachtwoordcode weergeven  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en een verzameling selecteren.  

2. Selecteer het apparaat of de apparaten waarop u de status van het opnieuw instellen van de wachtwoordcode wilt weergeven.  

3. Kies **acties extern apparaat** in **apparaatgroep**, en kies vervolgens **status van wachtwoordcode weergeven**.  

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

> [!Note]    
> U moet de actie vergrendelen op afstand uitvoeren van de site op het hoogste niveau in uw omgeving. Bijvoorbeeld, als u een centrale beheersite gebruikt, kunt u alleen de actie uitvoeren op die site. Als u een zelfstandige primaire site, kunt u de actie alleen uitvoeren op die site.

#### <a name="to-lock-a-mobile-device-remotely-through-the-configuration-manager-console"></a>Een mobiel apparaat op afstand vanuit de Configuration Manager-console vergrendelen  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en een verzameling selecteren.  

2. Selecteer het apparaat dat of de apparaten die u wilt vergrendelen.  

3. Kies **acties extern apparaat** in **apparaatgroep**, en kies vervolgens **vergrendelen op afstand**.  

#### <a name="to-show-the-state-of-the-remote-lock"></a>De status van de externe vergrendeling weergeven  

1. Kies in de Configuration Manager-console **activa en naleving** en kies **apparaten**. U kunt ook kiezen **Apparaatverzamelingen** en een verzameling selecteren.  

2. Selecteer het apparaat waarop u de status van de externe vergrendeling wilt weergeven.  

3. Kies **acties extern apparaat** in **apparaatgroep**, en kies vervolgens **status van externe vergrendeling weergeven**.  

### <a name="see-also"></a>Zie tevens  
[Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx)   
