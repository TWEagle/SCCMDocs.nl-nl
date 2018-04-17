---
title: Instellingen voor Windows Hello voor Bedrijven
titleSuffix: Configuration Manager
description: Informatie over het integreren van Windows Hello voor bedrijven met System Center Configuration Manager.
ms.custom: na
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
caps.latest.revision: 17
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0d5e0f5e1d47441bd105fb5cae2e8f3f313dfa54
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>Windows Hello voor bedrijven-instellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

<!--1245704-->
System Center Configuration Manager kunt u de integratie met Windows Hello voor bedrijven (voorheen Microsoft Passport for Windows), een alternatieve aanmeldingsmethode voor Windows 10-apparaten is. Hello voor Bedrijven maakt gebruik van Active Directory of een Azure Active Directory-account om een wachtwoord, smartcard of virtuele smartcard te vervangen.  

Hello voor bedrijven kunt u gebruiken een **gebaar van de gebruiker** aan te melden, in plaats van een wachtwoord. Het gebaar van een gebruiker kan een eenvoudige pincode zijn, biometrische verificatie of een extern apparaat zoals een vingerafdruklezer.

Zie voor meer informatie [Windows Hello voor bedrijven](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification).


> [!Note]  
> Configuration Manager deze optionele functie standaard niet ingeschakeld. Voordat u deze gebruikt, moet u deze functie inschakelen. Zie voor meer informatie [optionele functies van updates inschakelen](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


 Configuration Manager geïntegreerd met Windows Hello voor bedrijven op twee manieren:  

-   U kunt de Configuration Manager gebruiken om te bepalen welke gebaren gebruikers wel en niet gebruiken om aan te melden.  

-   U kunt verificatiecertificaten opslaan in de sleutelarchiefprovider (KSP) van Windows Hello voor Bedrijven. Zie voor meer informatie [Certificaatprofielen](introduction-to-certificate-profiles.md).  

- U kunt Windows Hello voor bedrijven-beleid voor het domein Windows 10-apparaten waarop de Configuration Manager-client wordt uitgevoerd. Deze configuratie wordt beschreven in de [configureren Windows Hello voor bedrijven op Windows 10-apparaten domein](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices) sectie. Wanneer u Configuration Manager met Microsoft Intune (hybride) gebruikt, kunt u deze instellingen kunt configureren op Windows 10 en Windows 10 Mobile-apparaten. Zie voor meer informatie [configureren Windows Hello voor bedrijven instellingen (hybride)](../../mdm/deploy-use/windows-hello-for-business-settings.md).

## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>Windows Hello voor bedrijven op domein Windows 10-apparaten configureren
U kunt beheren Windows Hello voor bedrijven-instellingen op Windows 10-apparaten domein maken en implementeren van een Windows Hello voor bedrijven-profiel. Deze aanpak wordt aanbevolen.


Als u verificatie op basis van certificaten gebruikt, moet u een certificaatprofiel ook implementeren zoals beschreven in [een certificaatprofiel configureren](#configure-a-certificate-profile). Als u verificatie op basis van een sleutel gebruikt, hoeft u niet voor het implementeren van een certificaatprofiel.

## <a name="configure-a-windows-hello-for-business-profile"></a>Een Windows Hello voor bedrijven-profiel configureren  

In de Configuration Manager-console onder **toegang tot bedrijfsbronnen**, met de rechtermuisknop op **Windows Hello voor bedrijven-profielen** en kies **nieuw** om de profielwizard te starten. Geef de instellingen die zijn aangevraagd door de wizard, Controleer en Bevestig de instellingen op de laatste pagina en klik op **sluiten**. Hier volgt een voorbeeld van wat uw instellingen als volgt uitzien:  

![Windows Hello voor bedrijven-beleid wizard waarin de lijst met beschikbare instellingen](../media/Hello-for-Business-settings.png)

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Een certificaatprofiel configureren om het Windows Hello voor Bedrijven-inschrijvingscertificaat in te schrijven in Configuration Manager  
 Als u gebruiken Windows Hello voor bedrijven-aanmelding op basis van certificaten wilt, configureert u de volgende onderdelen:  

-   Een certificaatprofiel in Configuration Manager.  

-   Selecteer een sjabloon dat smartcardaanmeldings-EKU gebruikt in het certificaatprofiel.  

-   Als u van plan bent voor het opslaan van certificaatprofielen in het Windows Hello voor bedrijven-sleutelcontainer en gebruikt het certificaatprofiel de **smartcardaanmelding** EKU, moet u de volgende machtigingen voor de sleutel registratie om te controleren of het certificaat op de juiste wijze gevalideerd.
U moet eerst hebt gemaakt de **sleutel Admins** groep en alle Configuration Manager beheerpuntcomputers als leden aan deze groep toegevoegd.

Sommige configuraties mogelijk niet nodig hebt u machtigingen kunt configureren, of mogelijk verder configuraties. Raadpleeg de volgende tabel voor meer informatie:

|Versie van Windows-client|Configuration Manager 1602 of 1606|Configuration Manager 1610|Configuration Manager 1702 of hoger|
|-|-|-|-|
|Windows 10 Verjaardag Update|Er is geen hotfix is vereist<br><br>Er zijn geen machtigingen die vereist zijn<br><br>Er is geen schema-update van Windows vereist|Er is geen hotfix is vereist (Zie **waarschuwing**)<br><br>Er zijn geen machtigingen die vereist zijn<br><br>Er is geen schema-update van Windows vereist|Machtigingen configureren<br><br>Windows Server 2016-schema hebt toegepast met Active Directory|
|Auteurs Update van Windows 10 of hoger|Niet ondersteund|Installeer [deze hotfix](https://support.microsoft.com/help/4010155/update-rollup-for-system-center-configuration-manager-current-branch-v)<br><br>Machtigingen configureren<br><br>Windows Server 2016-schema hebt toegepast met Active Directory|Machtigingen configureren<br><br>Windows Server 2016-schema hebt toegepast met Active Directory|

> [!WARNING]
> Terwijl [de hotfix](https://support.microsoft.com/help/4010155/update-rollup-for-system-center-configuration-manager-current-branch-v) is niet vereist voor Configuration Manager 1610 en Windows 10 Verjaardag Update, deze kan worden geïnstalleerd.  Als de hotfix is geïnstalleerd, moet u machtigingen configureren en toepassen van Windows Server 2016-schema in Active Directory.

## <a name="to-configure-permissions"></a>Om machtigingen te configureren

1.  Aanmelden bij een domeincontroller of beheerwerkstations met de groep Domeinadministrators of gelijkwaardige referenties.
2.  Open **Active Directory-gebruikers en Computers**.
3.  In het navigatiedeelvenster met de rechtermuisknop op uw domeinnaam en klik vervolgens op **eigenschappen**.
4.  Op de **beveiliging** tabblad van de *<domain name>* **eigenschappen** in het dialoogvenster, klikt u op **Geavanceerd**. Als de **beveiliging** tabblad niet wordt weergegeven, schakelt u **geavanceerde functies** van de **weergave** menu van **Active Directory: gebruikers en Computers**.
5.  Klik op **Toevoegen**.
6.  In de **Machtigingsvermelding voor** *<domain name>* in het dialoogvenster, klikt u op **een principal selecteren**.
7.  In de **Selecteer gebruiker, Computer, serviceaccount of groep** in het dialoogvenster, type **sleutel Admins** in de **Voer de naam van het object te selecteren** in het tekstvak. Klik op **OK**.
8.  Van de **is van toepassing op** selecteert **Descendant gebruikersobjecten**.
9.  Ga naar de onderkant van de pagina en klik op **Alles wissen**.
10. In de **eigenschappen** sectie **lezen msDS-KeyCredentialLink**.
11. Klik op **OK** drie keer om de taak te voltooien.


## <a name="next-steps"></a>Volgende stappen

Zie voor meer informatie [Certificaatprofielen](introduction-to-certificate-profiles.md).  




