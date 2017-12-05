---
title: Sitesysteemrollen installeren
titleSuffix: Configuration Manager
description: Wizards helpen u sitesysteemrollen toevoegen aan een bestaande of nieuwe sitesysteemserver in de site.
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61f5c774-7667-44ae-b8e4-a4951318b183
caps.latest.revision: "4"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 82be333fcca636dfd68763cdfa7e97d0eaf14915
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2017
---
# <a name="install-site-system-roles-for-system-center-configuration-manager"></a>Sitesysteemrollen voor System Center Configuration Manager installeren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De System Center Configuration Manager-console heeft twee wizards die kunt u sitesysteemrollen installeren:  

-   **Wizard sitesysteemrollen toevoegen**: Gebruik deze wizard sitesysteemrollen toevoegen aan een bestaande sitesysteemserver in de site.  

-   **Wizard Sitesysteemserver maken**: Met deze wizard kunt u een nieuwe server specificeren als een sitesysteemserver en installeer vervolgens een of meer sitesysteemrollen op de server. Deze wizard is hetzelfde als de **toevoegen Wizard sitesysteemrollen**, behalve dat op de eerste pagina, moet u de naam van de server moet gebruiken en de site waarin u wilt installeren.  

Wanneer u een sitesysteemrol installeert op een externe computer (met inbegrip van een exemplaar van de SMS-Provider), wordt het computeraccount van de externe computer toegevoegd aan een lokale groep op de siteserver. Wanneer de site is geïnstalleerd op een domeincontroller, is de groep op de siteserver een domeingroep in plaats van een lokale groep. De externe sitesysteemrol is in dit geval niet operationeel totdat de site system rol computer opnieuw wordt opgestart of het Kerberos-ticket voor de account van de externe computer is vernieuwd. Zie [Accounts die worden gebruikt System Center Configuration Manager](../../../../core/plan-design/hierarchy/accounts.md) voor meer informatie.  

Voorafgaand aan de sitesysteemrol installeert, controleert Configuration Manager de doelcomputer om te controleren of deze voldoet aan de vereisten voor de sitesysteemrollen die u hebt geselecteerd. Inzicht in het volgende over het installeren van sitesysteemrollen:  

-   Standaard wanneer Configuration Manager een sitesysteemrol installeert de installatiebestanden geïnstalleerd op de eerst beschikbare NTFS-geformatteerde schijfstation dat de meeste vrije schijfruimte beschikbaar is. Om te voorkomen dat Configuration Manager op specifieke stations installeert, maakt u een leeg bestand met de naam **no_sms_on_drive.sms**. Kopieer deze naar de hoofdmap van het station voordat u de sitesysteemserver installeert.  

-   Configuration Manager gebruikt de **Installatieaccount** voor het installeren van sitesysteemrollen. U geeft dit account wanneer u de betreffende wizard een nieuwe sitesysteemserver maken of sitesysteemrollen toevoegen aan een bestaande sitesysteemserver uitvoert. Standaard is dit account is het lokale systeemaccount van de site server-computer, maar kunt u een domeingebruikersaccount voor gebruik als de Account voor de installatie van de Site. Zie [Accounts die worden gebruikt System Center Configuration Manager](../../../../core/plan-design/hierarchy/accounts.md) voor meer informatie.  

##  <a name="bkmk_Install"></a>Sitesysteemrollen installeren op een bestaande sitesysteemserver  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Servers en sitesysteemrollen**. Selecteer vervolgens de server die u wilt gebruiken voor de nieuwe sitesysteemrollen.  

3.  Klik op **Sitesysteemrollen toevoegen** in het tabblad **Start** , in de groep **Server**.  

4.  Op de **algemene** pagina, controleert u de instellingen en klik vervolgens op **volgende**.  

    > [!TIP]  
    >  Voor toegang tot de sitesysteemrol van het Internet, zorg ervoor dat u opgeeft dat een volledig gekwalificeerde domeinnaam (FQDN) van Internet.  

5.  Op de **Proxy** pagina, instellingen opgeven voor een proxyserver indien sitesysteemrollen die worden uitgevoerd op deze sitesysteemserver een proxyserver verbinding maken met locaties op het Internet nodig. Klik op **Volgende**.  

6.  Op de **Systeemrolselectie** pagina, selecteert u de sitesysteemrollen die u wilt toevoegen en klik vervolgens op **volgende**.  

7.  Voltooi de wizard.  

> [!TIP]  
>  De Windows PowerShell-cmdlet New-CMSiteSystemServer, voert dezelfde functie uit als deze procedure. Zie voor meer informatie [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) in de System Center 2012 Configuration Manager SP1 Cmdlet-Reference-documentatie.  

## <a name="to-install-site-system-roles-on-a-new-site-system-server"></a>Sitesysteemrollen installeren op een nieuwe sitesysteemserver  

1.  Klik op **Beheer**in de Configuration Manager-console.  

2.  Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Servers en sitesysteemrollen**.  

3.  Klik in het tabblad **Start** op **Sitesysteemserver maken** in de groep **Maken**.  

4.  Configureer de algemene instellingen voor het sitesysteem op de pagina **Algemeen** en klik vervolgens op **Volgende**.  

    > [!TIP]  
    >  Zorg ervoor dat u een Internet-FQDN opgeven voor toegang tot de nieuwe sitesysteemrol vanaf het Internet.  

5.  Op de **Proxy** pagina, instellingen opgeven voor een proxyserver indien sitesysteemrollen die worden uitgevoerd op deze sitesysteemserver een proxyserver verbinding maken met locaties op het Internet nodig. Klik op **Volgende**.  

6.  Op de **Systeemrolselectie** pagina, selecteert u de sitesysteemrollen die u wilt toevoegen en klik vervolgens op **volgende**.  

7.  Voltooi de wizard.  

> [!TIP]  
>  De Windows PowerShell-cmdlet New-CMSiteSystemServer, voert dezelfde functie uit als deze procedure. Zie voor meer informatie [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) in de System Center 2012 Configuration Manager SP1 Cmdlet-Reference-documentatie.  
