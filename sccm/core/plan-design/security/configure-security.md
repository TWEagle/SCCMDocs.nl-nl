---
title: Beveiliging configureren in System Center Configuration Manager | Microsoft-documenten
description: Configureer de beveiligingsopties voor System Center Configuration Manager.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 552e7e3d-e584-4a7c-9155-0f796a14b678
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cf29123923436ed4cefc17c69630fc39989caeb4
ms.openlocfilehash: 0034381a7a388ddc3eda5e774f3c63d741336301
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-security-in-system-center-configuration-manager"></a>Beveiliging configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik de informatie in dit artikel bij het instellen van beveiligingsopties voor System Center Configuration Manager.  

##  <a name="BKMK_ConfigureClientPKI"></a> Instellingen configureren voor PKI-clientcertificaten  
Indien u wilt de openbare-sleutelinfrastructuur (PKI)-certificaten te gebruiken voor clientverbindingen naar sitesystemen die Internet Information Services (IIS) gebruiken, gebruik dan de volgende procedure om instellingen te configureren voor deze instellingen.  

#### <a name="to-configure-client-pki-certificate-settings"></a>Clientinstellingen PKI-certificaat configureren  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, kies **Sites**, en selecteer vervolgens de primaire site configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**, en selecteer vervolgens de **Clientcomputercommunicatie** tabblad.  

    Dit tabblad is enkel beschikbaar op een primaire site. Indien u het tabblad **Communicatie clientcomputer** niet ziet, controleer dan dat u niet verbonden bent met een centrale beheersite of een secundaire site.  

4.  Kies **alleen HTTPS** wanneer u clients wilt die aan de site toegewezen zijn altijd een client PKI-certificaat gebruiken wanneer ze verbinden met sitesystemen die IIS gebruiken. Of kies **HTTPS of HTTP** wanneer u geen clients gebruiken PKI-certificaten vereist.  

5.  Als u hebt gekozen **HTTPS of HTTP**, kies **gebruik client PKI-certificaat (mogelijkheid tot clientverificatie) indien beschikbaar** wanneer u wilt een PKI-certificaat gebruiken voor HTTP-verbindingen. De client gebruikt dit certificaat in plaats van een zelfondertekend certificaat om zichzelf te laten verifiëren door sitesystemen. Deze optie wordt automatisch gekozen als u ervoor kiest **alleen HTTPS**.  

    Wanneer clients gedetecteerd zijn op het Internet, of wanneer ze geconfigureerd zijn voor clientbeheer enkel voor Internet, gebruiken ze altijd een client PKI-certificaat.  

6.  Kies **wijzigen** selectiemethode voor uw gekozen client configureren voor wanneer meer dan één geldig PKI-clientcertificaat beschikbaar is op een client en kies vervolgens **OK**.  

    Zie voor meer informatie over de selectiemethode voor clientcertificaat, [Planning voor selectie van PKI-clientcertificaten](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection).  

7.  Selecteer of wis het selectievakje voor clients om de lijst van certificaatintrekking (CRL) te controleren.  

    Voor meer informatie over CRL-controle voor clients, Zie [Planning voor intrekking PKI-certificaat](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs).  

8.  Als u vertrouwde basiscertificaten certification authority (CA) voor clients opgeven moet, kiest u **stellen**, importeer de basis-CA-certificaatbestanden en kies vervolgens **OK**.  

    Zie voor meer informatie over deze instelling [Planning voor de PKI vertrouwde basiscertificaten en de lijst met certificaatverleners](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRootCAs).  

9. Kies **OK** sluit het dialoogvenster Eigenschappen voor de site.  

Herhaal deze procedure voor alle primaire sites in de hiërarchie.  

##  <a name="BKMK_ConfigureSigningEncryption"></a>Ondertekening en versleuteling configureren  
Configureer de meest beveiligde ondertekenings- en versleutelingsinstellingen voor sitesystemen die alle clients in de site kunnen ondersteunen. Deze instellingen zijn in het bijzonder belangrijk wanneer u clients laat communiceren met sitesystemen door gebruik te maken van zelfondertekende certificaten via HTTP.  

#### <a name="to-configure-signing-and-encryption-for-a-site"></a>Ondertekening en versleuteling voor een site configureren  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **siteconfiguratie**, kies **Sites**, en selecteer vervolgens de primaire site configureren.  

3.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**, en selecteer vervolgens de **ondertekening en versleuteling** tabblad.  

    Dit tabblad is enkel beschikbaar op een primaire site. Indien u het tabblad **Ondertekening en versleuteling** niet ziet, controleer dan dat u niet verbonden bent met een centrale beheersite of een secundaire site.  

4.  Configureer de ondertekening en versleuteling opties die u wilt en kies vervolgens **OK**.  

    > [!WARNING]  
    >  Kies niet **Vereis SHA-256** zonder eerst controleren die door alle clients die zijn aan de site toegewezen kunnen worden ondersteund dit hash-algoritme of dat ze een geldig PKI-clientverificatiecertificaat hebben. U dient eventueel updates of hotfixes te installeren op clients om SHA-256 te ondersteunen. Zo moeten computers die Windows Server 2003 SP2 uitvoeren bijvoorbeeld een hotfix installeren waarnaar gerefereerd wordt in het [KB-artikel 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666).  
    >   
    >  Als u deze optie kiest en clients kunnen SHA-256 ondersteunen en gebruiken zelfondertekende certificaten, weigert Configuration Manager ze. In dit scenario maakt het onderdeel SMS_MP_CONTROL_MANAGER melding van het bericht ID 5443.  

5.  Kies **OK** sluit de **eigenschappen** in het dialoogvenster voor de site.  

Herhaal deze procedure voor alle primaire sites in de hiërarchie.  

##  <a name="BKMK_ConfigureRBA"></a> Beheer op basis van rollen configureren  
Beheer op basis van rollen combineert beveiligingsrollen, beveiligingsbereiken en toegewezen verzamelingen om het beheerbereik te definiëren voor elke gebruiker met beheerdersrechten. Een beheerbereik bevat de objecten die een gebruiker met beheerdersrechten kan bekijken in de Configuration Manager-console en de taken gerelateerd aan deze objecten die de gebruiker met beheerdersrechten gemachtigd is. Configuraties voor beheer op basis van rollen worden toegepast op elke site in een hiërarchie.  

De volgende koppelingen kunt u naar de betreffende secties van de [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../../core/servers/deploy/configure/configure-role-based-administration.md) artikel:  

-   [Aangepaste beveiligingsrollen maken](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole)  

-   [Configureer beveiligingsrollen](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole)  

-   [Beveiligingsbereiken voor een object configureren](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope)  

-   [Verzamelingen voor het beheren van beveiliging configureren](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl)  

-   [Maak een nieuwe gebruiker met beheerdersrechten](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_Create_AdminUser)  

-   [Het beheerbereik van een gebruiker met beheerdersrechten wijzigen](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ModAdminUser)  

> [!IMPORTANT]  
>  Uw eigen beheerdersbereik definieert de objecten en instellingen die u kunt toewijzen wanneer u beheer op basis van rollen configureert voor een andere gebruiker met beheerdersrechten. Zie voor informatie over de planning voor op rollen gebaseerd beheer [grondbeginselen van op rollen gebaseerd beheer voor System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md).  

##  <a name="BKMK_ManageAccounts"></a> Accounts beheren die worden gebruikt door Configuration Manager  
Configuration Manager ondersteunt Windows-accounts voor allerlei taken en gebruiken.  

Gebruik de volgende procedure om de weergave-accounts die geconfigureerd zijn voor de verschillende taken en voor het beheren van het wachtwoord dat voor elk account Configuration Manager gebruikt.  

#### <a name="to-manage-accounts-that-are-used-by-configuration-manager"></a>Accounts beheren die worden gebruikt door Configuration Manager  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **Accounts** om de accounts die geconfigureerd zijn voor Configuration Manager weer te geven.  

3.  Kies het account voor wijzigen van het wachtwoord voor een account dat is geconfigureerd voor Configuration Manager.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  Kies **stellen** openen de **Windows-gebruikersaccount** dialoogvenster en geef het nieuwe wachtwoord voor Configuration Manager moet worden gebruikt voor het account.  

    > [!NOTE]  
    >  Het wachtwoord dat u specificeert moet overeenkomen met het wachtwoord dat voor het account gespecificeerd is in Active Directory: gebruikers en computers.  

6.  Kies **OK** om de procedure te voltooien.  

