---
title: 'Apparaatinschrijving instellen '
titleSuffix: Configuration Manager
description: Gebruikers toestaan hun apparaten kunnen inschrijven voor On-premises Mobile Device Management in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ffaea91-1379-4b86-9953-b25e152f56a9
caps.latest.revision: "10"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 50aef3a2e523353d488a53eed0b346ddfef42478
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="set-up-device-enrollment-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Apparaatinschrijving instellen voor on-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hierdoor kunnen gebruikers hun apparaten kunnen inschrijven voor System Center Configuration Manager op\-premises Mobile Device Management, moet u hen daarvoor toestemming verleend. Als u wilt machtigen gebruikers apparaten inschrijven, voer de volgende taken.

-   [Een inschrijvingsprofiel maken waarmee gebruikers moderne apparaten kunnen registreren](#bkmk_createProf)  

-   [Aanvullende instellingen voor geregistreerde apparaten instellen](#bkmk_addClient)  

-   [Gebruikers in staat stellen het inschrijvingsprofiel voor moderne apparaten te ontvangen](#bkmk_enableUsers)  

-   [Het basiscertificaat opslaan op apparaten die moeten worden ingeschreven](#bkmk_storeCert)  

##  <a name="bkmk_createProf"></a> Een inschrijvingsprofiel maken waarmee gebruikers moderne apparaten kunnen registreren  
 Voor het pushen van de instellingen die vereist dat gebruikers moderne apparaten te registreren, kunt u toevoegen een nieuw inschrijvingsprofiel aan de standaardclientinstellingen dat wordt toegepast op alle gedetecteerde gebruikers in de Configuration Manager-site.  

1.  Klik in de Configuration Manager-console op **beheer** > **overzicht** > **clientinstellingen**Open **Standaardclientinstellingen** en selecteer **inschrijving**.  

2.  Geef onder Apparaatinstellingen het polling-interval voor moderne apparaten op.  

3.  Selecteer onder Gebruikersinstellingen **Ja** voor **Gebruikers toestaan moderne apparaten te registreren**.  

4.  Naast **inschrijvingsprofiel voor moderne apparaten**, klikt u op **profiel instellen...**  en klik vervolgens op **maken...**  

5.  Typ in Inschrijvingsprofiel maken een naam voor het inschrijvingsprofiel en kies de code van de beheersite die gebruikers met het inschrijvingsprofiel moeten gebruiken. Klik meerdere keren op **OK** om de pagina Standaardinstellingen af te sluiten.  

> [!NOTE]  
>  Als u het inschrijvingsprofiel wilt implementeren voor een subset van de gedetecteerde gebruikers, kunt u een gebruikersverzameling gebruiken en aangepaste clientinstellingen maken die voor deze verzameling worden geïmplementeerd. Zie [Clientinstellingen in System Center Configuration Manager configureren](../../core/clients/deploy/configure-client-settings.md) voor informatie over het maken van aangepaste clientinstellingen.  

##  <a name="bkmk_addClient"></a> Aanvullende instellingen voor geregistreerde apparaten instellen  
 Naast het instellen van het inschrijvingsprofiel voor moderne apparaten, kunt u aanvullende clientinstellingen instellen voor het configureren van apparaten wanneer deze zijn ingeschreven.  Zie [Clientinstellingen in System Center Configuration Manager configureren](../../core/clients/deploy/configure-client-settings.md) voor informatie over het instellen van clientinstellingen.  

 Niet alle clientinstellingen zijn beschikbaar voor op\-premises Mobile Device Management. De huidige vertakking van Configuration Manager ondersteunt de volgende clientinstellingen voor op\-premises Mobile Device Management:  

-   Registratie: Met deze instellingen bepaalt u het inschrijvingsprofiel voor beheerde apparaten. Zie [Een inschrijvingsprofiel maken waarmee gebruikers moderne apparaten kunnen registreren](#bkmk_createProf)voor meer informatie over het instellen van een inschrijvingsprofiel.  

-   Clientbeleid: Met deze instelling bepaalt u de frequentie voor het downloaden van clientbeleid op het apparaat. U kunt ook instellingen inschakelen voor specifieke gebruikers met polling voor gebruikersbeleid. Voor meer informatie over client-beleidsinstellingen raadpleegt u de sectie Clientbeleid in [Clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).  

-   Implementatie van software: Met deze instelling bepaalt u het interval voor het evalueren van clientapparaten voor software-implementaties. Voor meer informatie over software-beleidsinstellingen raadpleegt u de sectie Software-implementatie in [Clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md)  

    > [!NOTE]  
    >  Voor op\-premises Mobile Device Management, software-implementatie instellingen kunnen alleen worden gebruikt als standaardclientinstellingen. Instellingen voor software-implementatie kunnen niet worden gebruikt met aangepaste clientinstellingen in de huidige vertakking van Configuration Manager.  

##  <a name="bkmk_enableUsers"></a> Gebruikers in staat stellen het inschrijvingsprofiel voor moderne apparaten te ontvangen  
 Voor gebruikers voor het ontvangen van het inschrijvingsprofiel voor de gewijzigde clientinstellingen op\-premises Mobile Device Management, moeten zij worden gedetecteerd via de Active Directory-detectiemethode. Voer detectie voor Active Directory-gebruikers om te zorgen dat iedereen die het inschrijvingsprofiel nodig heeft, het ontvangt. Zie [Detectie uitvoeren voor System Center Configuration Manager](../../core/servers/deploy/configure/run-discovery.md) voor instructies voor het detecteren van gebruikers.  

##  <a name="bkmk_storeCert"></a> Het basiscertificaat opslaan op apparaten die moeten worden ingeschreven  
 Gebruikers met apparaten die lid zijn van een domein, hebben waarschijnlijk al het vereiste basiscertificaat voor vertrouwde communicatie met de servers die als host dienen voor de sitesysteemrollen, omdat het basiscertificaat is uitgegeven als onderdeel van het proces om lid te worden van een domein met Active Directory. Op computers en mobiele apparaten die geen lid zijn van een domein, moet het basiscertificaat handmatig op het apparaat worden geïnstalleerd om inschrijving toe te staan. Deze apparaten beschikken niet automatisch over het vereiste basiscertificaat.  

 Het geëxporteerde certificaatbestand moet aan het apparaat worden verschaft voor handmatige installatie. U kunt dit doen met e-mail, OneDrive, SD-kaart, USB-station of een andere methode die aan uw behoeften voldoet.  

 Het basiscertificaat dat u op de apparaten wilt gebruiken, is het certificaat dat u hebt geëxporteerd in [Het certificaat met dezelfde basis als het webservercertificaat exporteren](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert).  

1.  Ga op het apparaat dat moet worden ingeschreven naar het bestand voor het basiscertificaat en dubbelklik hierop.  

2.  Klik in het dialoogvenster certificaat **certificaat installeren...**  

3.  Selecteer in de wizard Certificaat importeren de optie **Lokale computer**en klik op **Volgende**.  

4.  Klik op in het venster Gebruikersaccountbeheer op **Ja**.  

5.  Selecteer **Alle certificaten in het onderstaande archief opslaan**en klik op **Bladeren**.  

6.  Klik op **Vertrouwde basiscertificeringsinstanties**, klik op **OK**en klik op **Volgende**.  

7.  Klik op **Voltooien**.  
