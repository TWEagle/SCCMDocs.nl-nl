---
title: Windows Hello voor instellingen voor Business | Microsoft-documenten
description: Informatie over het integreren van Windows Hello voor bedrijven met System Center Configuration Manager.
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 699b79b68440b61904a9053e5004318a2a248bfd
ms.openlocfilehash: 75def95561feb35f2f060f0daa72291983324d4f
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>Windows Hello voor Business-instellingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager kunt u integratie met Windows Hello voor bedrijven (voorheen Microsoft Passport voor Windows), een alternatieve-toegestane aanmeldingsmethode voor Windows 10-apparaten. Hello voor Bedrijven maakt gebruik van Active Directory of een Azure Active Directory-account om een wachtwoord, smartcard of virtuele smartcard te vervangen.  

Met Hello voor Bedrijven kan voor aanmelding een **gebaar van de gebruiker** in plaats van een wachtwoord worden gebruikt. Het gebaar van een gebruiker kan een eenvoudige pincode zijn, biometrische verificatie of een extern apparaat zoals een vingerafdruklezer.

[Meer informatie over Windows Hello voor bedrijven](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification)

 Configuration Manager wordt geïntegreerd met Windows Hello voor bedrijven op twee manieren:  

-   U kunt de Configuration Manager gebruiken om te bepalen welke gebaren gebruikers kunnen en kunnen niet gebruiken om aan te melden.  

-   U kunt verificatiecertificaten opslaan in de sleutelarchiefprovider (KSP) van Windows Hello voor Bedrijven. Zie voor meer informatie [Certificaatprofielen](introduction-to-certificate-profiles.md).  

- U kunt implementeren Windows Hello voor Business-beleid voor het domein Windows 10-apparaten waarop de Configuration Manager-client wordt uitgevoerd. Deze configuratie wordt beschreven in [configureert Windows Hello voor bedrijven op apparaten met Windows 10 domein](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices), hieronder. Wanneer u gebruikmaakt van Configuration Manager met Intune (hybride), kunt u deze instellingen configureren op Windows 10 en Windows 10 Mobile-apparaten, maar niet op domein apparaten waarop de Configuration Manager-client wordt uitgevoerd. Zie [configureert Windows Hello voor bedrijven instellingen (hybride)](../../mdm/deploy-use/windows-hello-for-business-settings.md) voor meer informatie.

## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>Configureer Windows Hello voor bedrijven op domein Windows 10-apparaten
U kunt beheren Windows Hello voor Business-instellingen voor Windows 10-apparaten domein op drie manieren:

- U kunt maken en implementeren van een Windows Hello voor Business-profiel. Dit is de aanbevolen aanpak.
- U kunt Groepsbeleid gebruiken.  
- U kunt een PowerShell-script gebruiken.

Houd er rekening mee dat naast deze configuratie u ook een certificaatprofiel implementeert moet, zoals beschreven in [een certificaatprofiel configureren](#configure-a-certificate-profile).

## <a name="configure-a-windows-hello-for-business-profile"></a>Een Windows Hello voor Business-profiel configureren  

In de Configuration Manager-console onder **toegang tot bedrijfsbronnen**, met de rechtermuisknop op **Windows Hello voor zakelijke profielen** en kies **New** om de profielwizard te starten. Geef de instellingen die zijn aangevraagd door de wizard Controleer en Bevestig de instellingen op de laatste pagina en klik op **sluiten**. Hier volgt een voorbeeld van wat de instellingen als volgt uitzien:  

![Instellingen voor Windows Hello voor Bedrijven](../media/Hello-for-Business-settings.png)

## <a name="configure-windows-hello-for-business-with-group-policy-in-active-directory"></a>Windows Hello voor bedrijven met Groepsbeleid in Active Directory configureren  

U kunt een Active Directory-groepsbeleid gebruiken om uw Windows 10 domein apparaten inrichten gebruiker Hallo voor zakelijke referenties wanneer een gebruiker zich bij Windows aanmeldt:

1.  Open Serverbeheer op een computer met Windows Server en navigeer naar **extra** > **Groepsbeleidsbeheer**.    

2.  In de **Groepsbeleidsbeheer** dialoogvenster Vouw het domein waarin u wilt inschakelen automatische Workplace Join.    

3.  Met de rechtermuisknop op **groepsbeleidsobjecten**, en klik vervolgens op **New**.  

4.  In de **nieuw groepsbeleidsobject** dialoogvenster, voert u een naam voor het nieuwe Groepsbeleid-object, zoals **inschakelen Windows Hello voor bedrijven**, en klik vervolgens op **OK**.  

5.  In de **groepsbeleidsobjecten** knooppunt met de rechtermuisknop het object dat u zojuist hebt gemaakt en klik vervolgens op **bewerken**.  

6.  In de **Editor voor Groepsbeleidsbeheer** dialoogvenster vak, navigeert u naar **Computerconfiguratie** > **beleid** > **Beheersjablonen** > **Windows-onderdelen** > **Windows Hello voor bedrijven**.  

7.  Met de rechtermuisknop op **inschakelen Windows Hello voor bedrijven** en klik vervolgens op **bewerken**.   

8.  Selecteer **ingeschakeld**, klikt u op **toepassen**, en klik vervolgens op **OK**.

U kunt nu het groepsbeleidsobject dat u zojuist hebt gemaakt naar een locatie van uw keuze koppelen. Bijvoorbeeld:    

   Een specifieke organisatie-eenheid (OE) in AD waar Windows 10-computers voor domein geplaatst worden.    

   Een bepaalde beveiligingsgroep met Windows 10 domeincomputers die automatisch worden geregistreerd in Azure AD.    

## <a name="configure-windows-hello-for-business-by-deploying-a-powershell-script-with-configuration-manager"></a>Configureer Windows Hello voor bedrijven door het implementeren van een PowerShell-script met Configuration Manager    
U kunt maken en implementeren van de volgende PowerShell-script met behulp van Configuration Manager-Toepassingsbeheer.    

**PowerShell.exe - uitvoeringsbeleid Bypass - NoLogo - NoProfile-opdracht "& {nieuwe ItemProperty"HKLM:\Software\Policies\Microsoft\PassportForWork"-naam 'Enabled' - waarde 1 - PropertyType is"DWord"-Force}" ** 

Zie voor meer informatie over het toepassingsbeheer van de Configuration Manager [inleiding op Toepassingsbeheer in System Center Configuration Manager](/sccm/apps/understand/introduction-to-application-management).  

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Een certificaatprofiel configureren om het Windows Hello voor Bedrijven-inschrijvingscertificaat in te schrijven in Configuration Manager  
 Configureer het volgende als u aanmelding op basis van een Windows Hello voor Bedrijven-certificaat, oftewel Microsoft Hello, wilt gebruiken:  

-   Een certificaatprofiel van Configuration Manager.  

-   Selecteer een sjabloon dat smartcardaanmeldings-EKU gebruikt in het certificaatprofiel.  

-    Als u van plan bent voor het opslaan van certificaatprofielen in de Windows Hello voor zakelijke sleutelcontainer en het certificaatprofiel gebruikt de **smartcardaanmelding** EKU, moet u de volgende machtigingen voor de sleutel registratie zodat het certificaat correct wordt gevalideerd.
U moet eerst hebt gemaakt de **sleutel Admins** groep en alle Configuration Manager beheerpuntcomputers als leden aan deze groep worden toegevoegd.

    1.    Meld u aan een domein controller of management werkstations met domeinbeheerders of gelijkwaardige referenties.
    2.    Open **Active Directory: gebruikers en Computers**.
    3.    In het navigatiedeelvenster met de rechtermuisknop op de domeinnaam van uw en klik vervolgens op **eigenschappen**.
    4.    Op de **beveiliging** tabblad van het  *<domain name>*  **eigenschappen** in het dialoogvenster, klikt u op **Geavanceerd**. Als de **beveiliging** tabblad niet wordt weergegeven, schakelt u **geavanceerde functies** van de **weergave** optiemenu **Active Directory: gebruikers en Computers**.
    5.    Klik op **Toevoegen**.
    6.    In de **machtigingsvermelding**  *<domain name>*  in het dialoogvenster klikt u op **een principal selecteren**.
    7.    In de **gebruiker, Computer, Service-Account of groep** in het dialoogvenster, type **sleutel Admins** in de **Voer de naam van het object te selecteren** tekstvak.  Klik op **OK**.
    8.    Van de **is van toepassing op** selecteert **Descendant gebruikersobjecten**.
    9.    Ga naar de onderkant van de pagina en klik op **Alles wissen**.
    10.    In de **eigenschappen** sectie **lezen msDS-KeyCredentialLink**.
    11.    Klik op **OK** drie keer om de taak te voltooien.


 Zie voor meer informatie [Certificaatprofielen](introduction-to-certificate-profiles.md).  





