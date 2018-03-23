---
title: CO-beheer voor Windows 10-apparaten
titleSuffix: Configuration Manager
description: Informatie over het beheren van Windows 10-apparaten gelijktijdig met behulp van zowel Configuration Manager en Microsoft Intune.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology: ''
ms.assetid: d6bbc787-83a5-44b4-ad64-016e5da7413f
ms.openlocfilehash: e4b8bd58d30cd87ffc461289edbfc5da9a684cda
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="co-management-for-windows-10-devices"></a>CO-beheer voor Windows 10-apparaten    
<!-- 1350871 -->
Veel klanten willen beheren van Windows 10-apparaten op dezelfde manier beheren van mobiele apparaten met behulp van een vereenvoudigde en lagere kosten, cloud-gebaseerde oplossing. Echter, het overschakelen van traditionele management naar moderne management kan lastig zijn. In de eerdere Windows 10-updates, kunt u al een Windows 10-apparaat toevoegen met on-premises Active Directory (AD) en Azure AD cloud-gebaseerd op hetzelfde moment (hybride Azure AD). Beginnen met Configuration Manager versie 1710, mede management maakt gebruik van deze verbetering en kunt u gelijktijdig Windows 10 versie 1709 (ook wel bekend als de vallen auteurs Update) om apparaten te beheren met behulp van zowel Configuration Manager en Intune. Het is een oplossing waarmee een verbinding met traditionele naar moderne management biedt en u een pad voor de overgang met behulp van een gefaseerde benadering. 

Er zijn twee belangrijkste paden naar CO management bereiken.  Een is Configuration Manager ingerichte mede management waarbij Windows 10-apparaten worden beheerd door Configuration Manager en hybride Azure AD lid ophalen ingeschreven bij Intune. De andere is Intune ingericht op apparaten die zijn ingeschreven bij Intune en vervolgens worden geïnstalleerd met het bereik van de client Configuration Manager een CO-management-status.

## <a name="prerequisites"></a>Vereisten
U moet beschikken over de volgende vereisten voordat u kunt CO-beheer inschakelen. Er zijn algemene vereisten en andere vereisten gelden voor apparaten met Configuration Manager-client en apparaten die geen van de client is geïnstalleerd.

> [!IMPORTANT]
> Windows 10 mobile-apparaten bieden geen ondersteuning voor CO-beheer.

### <a name="general-prerequisites"></a>Algemene vereisten
Hieronder vindt u algemene vereisten voor het inschakelen van CO-beheer:  

- Configuration Manager versie 1710 of hoger
- Azure AD
- Intune- of EMS-licentie voor alle gebruikers
- [Azure AD automatische inschrijving](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) ingeschakeld
- Intune-abonnement &#40;MDM-instantie in Intune wordt ingesteld op **Intune**&#41;


   > [!Note]  
   > Als u een hybride MDM-omgeving (Intune geïntegreerd met Configuration Manager) hebt, kunt u mede management niet inschakelen. Als u geïnteresseerd bent in migreren naar de zelfstandige versie van Intune, raadpleegt u [beginnen met het migreren van hybride MDM zelfstandige versie van Intune](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="additional-prerequisites-for-devices-with-the-configuration-manager-client"></a>Aanvullende vereisten voor apparaten met Configuration Manager-client
- Windows 10 versie 1709 (ook wel bekend als de vallen auteurs Update) en hoger
- [Hybride Azure AD lid](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) (lid is van AD en Azure AD)

### <a name="additional-prerequisites-for-devices-without-the-configuration-manager-client"></a>Aanvullende vereisten voor apparaten zonder de Configuration Manager-client
- Windows 10 versie 1709 (ook wel bekend als de vallen auteurs Update) en hoger
- [Management Gateway cloud](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) in Configuration Manager (als u Intune gebruikt voor het installeren van Configuration Manager-client)

## <a name="workloads-you-can-switch-to-intune"></a>Werkbelastingen die u kunt overschakelen naar Intune
Nadat u mede-beheer inschakelen, blijft de Configuration Manager voor het beheren van alle werkbelastingen. Als u besluit dat u klaar bent, kunt u beginnen met beheer van beschikbare werklasten Intune kunt hebben. U kunt Intune beheren van de volgende werkbelastingen hebben:   

### <a name="compliance-policies"></a>Nalevingsbeleid
Het nalevingsbeleid bevat de regels en instellingen waaraan een apparaat voldoen moet om te worden beschouwd als het beleid voldoen aan het beleid voor voorwaardelijke toegang. U kunt ook nalevingsbeleid gebruiken om nalevingsproblemen met apparaten te bewaken en onafhankelijk van voorwaardelijke toegang op te lossen. Zie voor meer informatie [nalevingsbeleid voor apparaten](/sccm/mdm/deploy-use/device-compliance-policies).  

### <a name="windows-update-for-business-policies"></a>Windows Update voor bedrijven-beleid
Windows Update voor bedrijven-beleid kunt u beleidsregels voor uitgestelde voor functie-updates voor Windows 10 of kwaliteit voor Windows 10-apparaten rechtstreeks beheerd door Windows Update voor bedrijven configureren. Zie voor meer informatie [Windows Update configureren voor uitgestelde bedrijfsbeleid](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies).  

### <a name="resource-access-policies"></a>Resource-beleid
Resourcetoegangsbeleid configureren VPN, Wi-Fi, e-mail en instellingen van het certificaat op apparaten. Zie voor meer informatie [resourcetoegangsprofielen implementeren](/sccm/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles).

### <a name="endpoint-protection"></a>Endpoint Protection 
<!-- 1357365 -->
U start in Configuration Manager 1802, worden de werkbelasting van de Endpoint Protection overgegaan naar Intune. Zie voor meer informatie [werkbelastingen kunnen worden overgezet naar Intune](/sccm/core/clients/manage/co-management-switch-workloads.md#Workloads-able-to-be-transitioned-to-Intune) en [Endpoint Protection in Configuration Manager](/sccm/protect/deploy-use/endpoint-protection).

## <a name="architectural-overview-for-co-management"></a>Overzicht van de architectuur voor CO-management
Het volgende diagram biedt een overzicht van de architectuur van CO-beheer en hoe deze in de bestaande infrastructuur voor configuratie en Intune past.

![Architectuurdiagram van CO-management](./media/co-management-arch.svg)

## <a name="scenarios-to-enable-co-management"></a>Scenario's voor CO-beheer inschakelen  
U kunt CO-beheer voor zowel Windows 10-apparaten zijn ingeschreven bij Microsoft Intune en de bestaande Windows 10 Configuration Manager-clients inschakelen. Beide scenario's resulteren in Windows 10-apparaten gelijktijdig worden beheerd door Configuration Manager en Intune, evenals toegevoegd aan AD en Azure AD.  

### <a name="devices-enrolled-in-intune"></a>Apparaten die zijn ingeschreven in Intune  
Wanneer Windows 10-apparaten zijn ingeschreven bij Intune, kunt u de Configuration Manager-client installeren op de apparaten (met behulp van een specifieke opdrachtregelargument) de clients om voor te bereiden mede management. Schakel vervolgens mede beheer vanuit de Configuration Manager-console starten specifieke werkbelastingen verplaatsen naar Intune voor specifieke Windows 10-apparaten.  

Voor Windows 10-apparaten die nog niet zijn ingeschreven in Intune, kunt u automatische inschrijving in Azure gebruiken om de apparaten te registreren. Voor de nieuwe Windows 10-apparaten, kunt u [Windows Automatische piloot](https://docs.microsoft.com/intune/enrollment-autopilot) voor het configureren van de Out of Box Experience (OOBE), waaronder automatische inschrijving dat apparaten in Intune inschrijft.  

### <a name="configuration-manager-clients"></a>Configuration Manager-clients
Wanneer u Windows 10-apparaten die Configuration Manager-clients hebt, kunt u deze apparaten registreren en collega beheer vanuit de Configuration Manager-console. Configuration Manager-triggers automatische inschrijving bij Intune op basis van de Azure AD-tenant informatie.  


## <a name="remote-actions-available-in-intune-on-azure-for-co-managed-devices"></a>Externe acties beschikbaar zijn in Intune in Azure voor naast beheerde apparaten
Wanneer een apparaat met Windows 10 is ingeschakeld voor het beheer van CO, hebt u de volgende acties op afstand beschikbaar voor u uit Intune in Azure:  
- [Fabrieksinstellingen terugzetten](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
- [Selectief wissen](https://docs.microsoft.com/intune/apps-selective-wipe)
- [Apparaten verwijderen](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
- [Opnieuw opstarten van apparaat](https://docs.microsoft.com/intune/device-restart)
- [Nieuwe start](https://docs.microsoft.com/intune/device-fresh-start)

## <a name="next-steps"></a>Volgende stappen
[Windows 10-apparaten voorbereiden op co-beheer](co-management-prepare.md)