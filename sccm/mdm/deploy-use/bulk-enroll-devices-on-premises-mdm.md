---
title: Apparaten bulksgewijs inschrijven | Microsoft Docs | On-premises MDM
description: Apparaten bulksgewijs inschrijven in een automatische manier met On-premises Mobile Device Management in System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b36f5e4a-2b57-4d18-83f6-197081ac2a0a
caps.latest.revision: "13"
caps.handback.revision: "0"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: be9596537e9c80a6d78aa0685d33382bfd242afe
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-bulk-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Het bulksgewijs inschrijven van apparaten met On-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


Bulkinschrijving in System Center Configuration Manager On-premises Mobile Device Management is een meer geautomatiseerde manier voor het inschrijven van apparaten, in vergelijking met gebruikersregistratie, waarvoor gebruikers hun referenties voor het inschrijven van het apparaat in te voeren.  Voor bulkinschrijving wordt gebruikgemaakt van een inschrijvingspakket om het apparaat tijdens de inschrijving te verifiëren. Het pakket (een PPKG-bestand) bevat een certificaatprofiel en optioneel een Wi-Fi-profiel als het apparaat een intranetverbinding voor de inschrijving nodig heeft.  

> [!NOTE]  
>  De huidige vertakking van Configuration Manager ondersteunt de inschrijving in On-premises Mobile Device Management voor apparaten met de volgende besturingssystemen:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 IoT Enterprise   

De volgende taken wordt uitgelegd hoe u bulksgewijs inschrijven computers en apparaten voor op\-premises Mobile Device Management:  

-   [Een certificaatprofiel maken](#bkmk_createCert)  

-   [Een Wi-Fi-profiel maken](#CreateWifi)  

-   [Inschrijvingsprofielen maken](#bkmk_createEnroll)  

-   [Een inschrijvingspakketbestand (PPKG) maken](#bkmk_createPpkg)  

-   [Een pakket gebruiken om een apparaat bulksgewijs in te schrijven](#bkmk_getPpkg)  

-   [De registratie van het apparaat controleren](#bkmk_verifyEnroll)  

##  <a name="bkmk_createCert"></a> Een certificaatprofiel maken  
 Het belangrijkste onderdeel van het inschrijvingspakket is een certificaatprofiel, dat wordt gebruikt om automatisch een vertrouwd basiscertificaat in te richten op het apparaat dat wordt ingeschreven.  Dit basiscertificaat is vereist voor vertrouwde communicatie tussen de apparaten en de sitesysteemrollen op die nodig zijn voor\-premises Mobile Device Management. Zonder het basiscertificaat wordt het apparaat niet vertrouwd in HTTPS-verbindingen tussen het apparaat en de servers waarop het inschrijvingspunt, het proxypunt voor inschrijving, het distributiepunt en de sitesysteemrollen van het apparaatbeheerpunt worden gehost.  

 Als onderdeel van het systeem voor het voorbereiden op\-premises Mobile Device Management kunt u een basiscertificaat dat u in het inschrijvingspakket certificaatprofiel gebruiken kunt exporteren. Zie voor instructies over het verkrijgen van het vertrouwde basiscertificaat [exporteren van het certificaat met dezelfde basis als het webservercertificaat](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert).  

 Gebruikt het geëxporteerde basiscertificaat om een certificaatprofiel te maken. Zie voor instructies [het maken van certificaatprofielen in System Center Configuration Manager](../../protect/deploy-use/create-certificate-profiles.md).  

##  <a name="CreateWifi"></a> Een Wi-Fi-profiel maken  
 Het andere onderdeel van het pakket voor bulkinschrijving is een Wi-Fi-profiel. Sommige apparaten beschikken mogelijk niet over de netwerkverbinding die nodig is voor de inschrijving totdat de netwerkinstellingen zijn ingericht. Door een Wi-Fi-profiel op te nemen in het inschrijvingspakket biedt u een manier om een netwerkverbinding voor het apparaat tot stand te brengen.  

 Volg de instructies in voor het maken van een Wi-Fi-profiel in Configuration Manager, [Wi-Fi-profielen maken in System Center Configuration Manager](../../protect/deploy-use/create-wifi-profiles.md).  

> [!IMPORTANT]  
>Houd rekening met de volgende twee problemen bij het maken van een Wi-Fi-profiel voor bulkinschrijving:
>
> - De huidige vertakking van Configuration Manager ondersteunt alleen de volgende Wi-Fi-beveiligingsconfiguraties voor op\-premises Mobile Device Management:  
>   
>   - Beveiligingstypen: **WPA2-Enterprise** of **WPA2-Personal**  
>   - Versleutelingstypen: **AES** of **TKIP**  
>   - EAP-typen: **Smartcard of ander certificaat** of **PEAP**  
>
>
> - Hoewel Configuration Manager een instelling voor proxyservergegevens in het Wi-Fi-profiel heeft, configureert deze niet de proxy wanneer het apparaat is ingeschreven. Als u een proxyserver instellen met de ingeschreven apparaten moet, kunt u de instellingen met behulp van configuratie-items als apparaten zijn ingeschreven of maken van het tweede pakket implementeren aan zijkant het pakket voor bulksgewijs inschrijven met de installatiekopie van Windows en Configuration Designer (ICD) implementeren.

##  <a name="bkmk_createEnroll"></a> Inschrijvingsprofielen maken  
 Met het inschrijvingsprofiel kunt u de vereiste instellingen voor het inschrijven van apparaten opgeven, met inbegrip van een certificaatprofiel, waarmee op dynamische wijze een vertrouwd basiscertificaat voor het apparaat wordt ingericht, en een Wi-Fi-profiel, dat indien nodig de netwerkinstellingen inricht.  

 Voordat u een inschrijvingsprofiel maakt, moet u ervoor zorgen dat u een certificaat- en Wi-Fi-profiel (indien nodig) hebt gemaakt. Zie [Een certificaatprofiel maken](#bkmk_createCert) en [Een Wi-Fi-profiel maken](#CreateWifi)voor meer informatie.  

#### <a name="to-create-an-enrollment-profile"></a>Een inschrijvingsprofiel maken:  

1.  Klik in de Configuration Manager-console op **activa en naleving** >**overzicht** >**alle apparaten in Bedrijfseigendom** >**Windows** >**Inschrijvingsprofielen**.  

2.  Klik met de rechtermuisknop op **Inschrijvingsprofiel** en klik vervolgens op **Profiel maken**.  

3.  Voer in de wizard Inschrijvingsprofiel maken een naam in voor het profiel, zorg ervoor dat **On-premises** is geselecteerd voor **Instantie voor beheer**en klik vervolgens op **Volgende**.  

4.  Selecteer de sitecode en klik op **Volgende**.  

5.  Selecteer **Alleen intranet**, selecteer de proxypunten voor inschrijving die het apparaat gebruikt om het inschrijvingsproces te starten en klik vervolgens op **Volgende**.  

6.  Selecteer het certificaatprofiel met het vertrouwde basiscertificaat (dit is het profiel dat u hebt gemaakt in [Create a certificate profile](#bkmk_createCert)) en klik op **Volgende**.  

7.  Selecteer het Wi-Fi-profiel met de vereiste instellingen voor apparaten om verbinding maken met het intranet (dit is het profiel dat u hebt gemaakt in [Create a Wi-Fi profile](#CreateWifi)) en klik op **Volgende**.  

    > [!NOTE]  
    >  Als u geen Wi-Fi-profiel gebruikt voor uw inschrijvingspakket, moet u deze stap overslaan.  

8.  Bevestig de instellingen voor het inschrijvingsprofiel en klikt u op **volgende**. Klik op **Sluiten** om de wizard af te sluiten.  

##  <a name="bkmk_createPpkg"></a> Een inschrijvingspakketbestand (PPKG) maken  
 Het inschrijvingspakket is het bestand dat u bulksgewijs-apparaten inschrijven voor op\-premises Mobile Device Management.  Dit bestand moet worden gemaakt met Configuration Manager. U kunt vergelijkbare typen pakketten maken met Windows Image en Configuration Designer (ICD), maar alleen pakketten die u in Configuration Manager maakt kunnen worden gebruikt om apparaten te registreren voor op\-premises Mobile Device Management van begin tot eind. Pakketten die zijn gemaakt met Windows ICD leveren alleen de UPN (User Principal Name) die nodig is voor inschrijving, maar voeren het daadwerkelijk inschrijvingsproces niet uit.  

 Het proces voor het maken van het inschrijvingspakket vereist Windows Assessment and Deployment Toolkit (ADK) voor Windows 10.  Op de server waarop de Configuration Manager-console wordt uitgevoerd, moet u versie 1511 van Windows ADK is geïnstalleerd. Zie de ADK-sectie van [Download kits and tools for Windows 10](https://msdn.microsoft.com/windows/hardware/dn913721.aspx)(Kits en hulpprogramma's downloaden voor Windows 10) voor meer informatie.  

> [!TIP]  
>  Als u een inschrijvingspakket uit de Configuration Manager-console verwijdert, wordt deze niet gebruikt om apparaten te registreren. U kunt het pakket verwijderen als manier om pakketten te beheren die u niet meer wilt gebruiken voor het bulksgewijs inschrijven van apparaten.  

#### <a name="to-create-an-enrollment-package-ppkg-file"></a>Een inschrijvingspakketbestand (Ppkg) maken  

1.  Klik met de rechtermuisknop op het profiel dat u zojuist hebt gemaakt (in [Inschrijvingsprofielen maken](#bkmk_createEnroll)en klik op **Exporteren**.  

2.  Klik op **Bladeren**, ga naar de locatie waar u het ppkg-bestand wilt opslaan, voer een naam voor het pakket in en klik vervolgens op **Opslaan**.  

3.  Als u het pakket wilt beveiligen met een wachtwoord, schakelt u het selectievakje naast **Pakket versleutelen Package**in en klikt u op **Exporteren** . Wacht vervolgens ongeveerd tien seconden totdat de export is voltooid.  

    > [!NOTE]  
    >  Als u het pakket hebt versleuteld, biedt Configuration Manager een bericht met het versleutelde wachtwoord. Zorg ervoor dat u de wachtwoordgegevens opslaat. Deze hebt u namelijk nodig om het pakket op apparaten in te richten.  

4.  Klik op **OK**.  

##  <a name="bkmk_getPpkg"></a> Een pakket gebruiken om een apparaat bulksgewijs in te schrijven  
 U kunt een pakket gebruiken om apparaten in te schrijven voordat of nadat het apparaat is ingericht via het OOBE-proces (Out-Of-Box Experience).   Het inschrijvingspakket kan ook worden opgenomen als onderdeel van het inrichtingspakket van de OEM(Original Equipment Manufacturer).  

 Het pakket moet fysiek aan het apparaat wordt geleverd om het te kunnen gebruiken voor een bulkinschrijving. U kunt het inschrijvingspakket afhankelijk van uw behoeften op verschillende manieren aan het apparaat leveren:  

-   Kopiëren van het bestandssysteem  

-   Als bijlage bij een e-mail  

-   Kopiëren via een NFC-verbinding (Near Field Communication)  

-   Kopiëren van geheugenkaart  

-   Streepjescode scannen  

-   Kopiëren van een aangesloten apparaat  

-   Opnemen in het OEM-inrichtingspakket  

#### <a name="to-bulk-enroll-a-device"></a>Een apparaat bulksgewijs inschrijven:  

1.  Zoek het inschrijvingspakket (met de Verkenner) op het apparaat dat moet worden ingeschreven en dubbelklik op het PPKG-bestand.  

2.  Klik op **Ja** in het bericht van Gebruikersaccountbeheer.  

3.  In het dialoogvenster waarin u wordt gevraagd of het pakket afkomstig van een bron u is vertrouwt, klikt u op **Ja, voegt u deze**.  

     Het registratieproces wordt gestart en duur ongeveer vijf minuten.  

4.  Open **instellingen**.  

5.  Klik op  **Accounts** > **Toegang via het werknetwerk**. Als de registratie is geslaagd, ziet u een account onder **CompanyApps**  

6.  Klik op het account en klik vervolgens op **Sync**, Hiermee start u het beheer met Configuration Manager.  

##  <a name="bkmk_verifyEnroll"></a> De registratie van het apparaat controleren  
 U kunt controleren dat apparaten zijn geregistreerd in de Configuration Manager-console.  

-   Start de Configuration Manager-console.  

-   Klik op **Activa en naleving** > **Overzicht** > **Apparaten**. Het geregistreerde apparaat wordt weergegeven in de lijst.  
