---
title: Mac OS - Configuration Manager-clients bijwerken | Microsoft-documenten
description: Clients op Mac-computers in System Center Configuration Manager upgraden.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74c60941-5eae-4905-9e58-252bdb39df96
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 502116b66fc14914ca0606ae416e82202824de7a
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-upgrade-clients-on-mac-computers-in-system-center-configuration-manager"></a>Clients op Mac-computers bijwerken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Volg de stappen op hoog niveau hieronder beschreven in de client voor Mac-computers upgraden met behulp van een System Center Configuration Manager-toepassing. U kunt het installatiebestand van de Mac-client ook downloaden, kopiëren naar een gedeelde netwerklocatie of een lokale map op de Mac-computer en vervolgens de gebruikers de opdracht geven de installatie handmatig uit te voeren.  

> [!NOTE]  
>  Voordat u deze stappen uitvoert, moet u nagaan of uw Mac-computer voldoet aan de vereisten. Zie [ondersteunde besturingssystemen voor Mac-computers](../../../plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mac-computers).  

## <a name="step-1-download-the-latest-mac-client-installation-file-from-the-microsoft-download-center"></a>Stap 1: De meest recente installatiebestand van de Mac-client downloaden via het Microsoft Download Center  
 De Mac-client voor Configuration Manager wordt niet geleverd op de installatiemedia van Configuration Manager en moet worden gedownload vanaf het Microsoft Download Center. De installatiebestanden van de Mac-client staan in een Windows installatiebestand met als naam ConfigmgrMacClient.msi.  

 U kunt dit bestand downloaden via het [Microsoft Downloadcentrum](http://go.microsoft.com/fwlink/p/?LinkId=525184).  

## <a name="step-2-run-the-downloaded-installation-file-to-create-the-mac-client-installation-file"></a>Stap 2: Het gedownloade installatiebestand voor het maken van het installatiebestand van de Mac-client uitvoeren  
 Voer op een computer met Windows het door u gedownloade bestand **ConfigmgrMacClient.msi** uit om het installatiebestand van de Mac-client met de naam **Macclient.dmg**uit te pakken. Dit bestand is standaard in de map **C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client** te vinden op de Windows-computer wanneer u de bestanden hebt uitgepakt.  

## <a name="step-3-extract-the-client-installation-files"></a>Stap 3: Pak de installatiebestanden van client  
 Kopieer het Macclient.dmg-bestand naar een netwerkshare of een lokale map op een Mac-computer. Koppel vervolgens vanaf de Mac-computer het Macclient.dmg-bestand, open het en kopieer de bestanden naar een map op de Mac-computer.  

## <a name="step-4-create-a-cmmac-file-that-can-be-used-to-create-an-application"></a>Stap 4: Maak een cmmac-bestand dat kan worden gebruikt voor het maken van een toepassing  

1.  Maak met behulp van het hulpprogramma **CMAppUtil** (te vinden in de map **Extra** van de installatiebestanden van de Mac client) een CMMAC-bestand uit het clientinstallatiepakket. Dit bestand wordt gebruikt voor het maken van de toepassing Configuration Manager.  

2.  Kopieer het nieuwe bestand **CMClient.pkg.cmmac** naar een locatie die beschikbaar is voor de computer waarop de Configuration Manager-console.  

 Zie voor meer informatie de [aanvullende procedures voor het maken en implementeren van toepassingen voor Mac-computers](/sccm/apps/get-started/creating-mac-computer-applications#supplemental-procedures-to-create-and-deploy-applications-for-mac-computers).  

## <a name="step-5-create-and-deploy-an-application-containing-the-mac-client-files"></a>**Stap 5:** Maken en implementeren van een toepassing met de Mac-clientbestanden  

1.  In de Configuration Manager-console maken van een toepassing van de **CMClient.pkg.cmmac** -bestand met de clientinstallatiebestanden.  

2.  Implementeer deze toepassing op Mac-computers in uw hiërarchie.  

 Zie voor meer informatie [maken van Mac-computertoepassingen met System Center Configuration Manager](../../../../apps/get-started/creating-mac-computer-applications.md).  

## <a name="step-6-users-install-the-latest-client"></a>Stap 6: Gebruikers installeren de nieuwste client  
 Gebruikers van Mac-clients wordt gevraagd dat een update van de Configuration Manager-client beschikbaar is en moet worden geïnstalleerd. Na installatie van de client moeten gebruikers hun Mac-computer opnieuw opstarten.  

 Wanneer de computer opnieuw is opgestart, wordt automatisch de wizard Inschrijving computer uitgevoerd voor de aanvraag van een nieuw gebruikerscertificaat.  

 Als u niet Configuration Manager-inschrijving gebruikt maar het clientcertificaat onafhankelijk van Configuration Manager installeert, Zie [de bijgewerkte client voor het gebruik van een bestaand certificaat configureren](#BKMK_UpgradingClient_MachineEnrollment).  

##  <a name="BKMK_UpgradingClient_MachineEnrollment"></a> cmshort  
 Voer de volgende procedure uit om te voorkomen dat de wizard Inschrijving computer wordt uitgevoerd en om de bijgewerkte client te configureren voor het gebruik van een bestaand clientcertificaat.  

-   Maak in de Configuration Manager-console een configuratie-item van het type **Mac OS X**.  

-   Voeg een instelling toe aan dit configuratie-item met het instellingstype **Script**.  

-   Voeg het volgende script toe aan de instelling:  

    ```  
    #!/bin/sh  
    echo "Starting script\n"  
    echo "Changing directory to MAC Client\n"  
    cd /Users/Administrator/Desktop/'MAC Client'/  
    echo "Import root cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/Root.pfx -A -k /Library/Keychains/System.Keychain -P ROOT  
    echo "Using openssl to convert pfx to a crt\n"  
    /usr/bin/sudo openssl pkcs12 -in /Users/Administrator/Desktop/'MAC Client'/Root.pfx -out Root1.crt -nokeys -clcerts -passin pass:ROOT  
    echo "Adding trust to root cert\n"  
    /usr/bin/sudo /usr/bin/security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.Keychain Root1.crt  
    echo "Import client cert\n"  
    /usr/bin/sudo /usr/bin/security import /Users/Administrator/Desktop/'MAC Client'/MacClient.pfx -A -k /Library/Keychains/System.Keychain -P MAC  
    echo "Executing ccmclient with MP\n"  
    sudo ./ccmsetup -MP https://SCCM34387.SCCM34387DOM.NET/omadm/cimhandler.ashx  
    echo "Editing Plist file\n"  
    sudo /usr/libexec/Plistbuddy -c 'Add:SubjectName string CMMAC003L' /Library/'Application Support'/Microsoft/CCM/ccmclient.plist  
    echo "Changing directory to CCM\n"  
    cd /Library/'Application Support'/Microsoft/CCM/  
    echo "Making connection to the server\n"  
    sudo open ./CCMClient  
    echo "Ending Script\n"  
    exit  

    ```  

-   Het configuratie-item toevoegen aan een configuratiebasislijn en implementeer de configuratiebasislijn op alle Mac-computers waarop een certificaat onafhankelijk van Configuration Manager installeren.  

 Zie voor meer informatie over het maken en implementeren van configuratie-items voor Mac-computers [het maken van configuratie-items voor Mac OS X-apparaten die worden beheerd door de System Center Configuration Manager-client](../../../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md) en [het implementeren van configuratiebasislijnen in System Center Configuration Manager](../../../../compliance/deploy-use/deploy-configuration-baselines.md).  

