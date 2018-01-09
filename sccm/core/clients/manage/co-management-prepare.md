---
title: Windows 10-apparaten voor het beheer van CO voorbereiden
description: Informatie over het voorbereiden van uw Windows 10-apparaten voor CO-beheer.
keywords: 
author: dougeby
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: 
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.openlocfilehash: d605dd4770be6878b08f4ac61da6ab27e3b6d61f
ms.sourcegitcommit: ac9268e31440ffe91b133c2ba8405d885248d404
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2018
---
# <a name="prepare-windows-10-devices-for-co-management"></a>Windows 10-apparaten voor het beheer van CO voorbereiden
U kunt CO-beheer op Windows 10-apparaten die zijn toegevoegd aan AD en Azure AD en ingeschreven in Intune en een client in Configuration Manager inschakelen. Voor de nieuwe Windows 10-apparaten, en voor apparaten die al zijn ingeschreven in Intune, de Configuration Manager-client installeren voordat ze samen beheerd worden kunnen. Voor Windows 10-apparaten die al Configuration Manager-clients, kunt u de apparaten inschrijven bij Intune en mede-beheer in de Configuration Manager-console inschakelen.

## <a name="command-line-to-install-configuration-manager-client"></a>Vanaf de opdrachtregel voor het installeren van Configuration Manager-client
U moet een app maken in Intune voor Windows 10-apparaten die nog geen Configuration Manager-clients. Wanneer u de app in de volgende secties maakt, gebruikt u de volgende opdrachtregel:

ccmsetup.msi CCMSETUPCMD = "/ mp: &#60; *URL van een cloudeindpunt management gateway wederzijdse verificatie*&#62; / CCMHOSTNAME = &#60; *URL van een cloudeindpunt management gateway wederzijdse verificatie*&#62; SMSSiteCode = &#60; *Sitecode*&#62; SMSMP = https: &#47; / &#60; *FQDN-naam van MP*&#62; AADTENANTID = &#60; *AAD-tenant-ID*&#62; AADTENANTNAME = &#60; *Tenantnaam*&#62; AADCLIENTAPPID = &#60; *Server AppID voor AAD-integratie*&#62; AADRESOURCEURI = https: &#47; / &#60; *Resource-ID*&#62; "

Bijvoorbeeld, als u had de volgende waarden:

- **URL van een cloudeindpunt management gateway wederzijdse verificatie**: https:/ &#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100    

   >[!Note]    
   >Gebruik de **MutualAuthPath** waarde in de **vProxy_Roles** SQL-weergave voor de **URL van een cloudeindpunt management gateway wederzijdse verificatie** waarde.

- **FQDN van beheerpunt (MP)**: sccmmp.corp.contoso.com    
- **Sitecode**: PS1    
- **Azure AD-tenant-ID**: 72F988BF-86F1-41AF-91AB-2D7CD011XXXX    
- **Naam van een Azure AD-tenant**: contoso    
- **Azure AD client app-ID**: bef323b3-042f-41a6-907a-f9faf0d1XXXX     
- **AAD Resource-ID-URI**: ConfigMgrServer    

  > [!Note]    
  > Gebruik de **IdentifierUri** waarde gevonden in de **vSMS_AAD_Application_Ex** SQL-weergave voor de **AAD Resource-ID-URI** waarde.

Gebruikt u de volgende opdrachtregel:

ccmsetup.msi CCMSETUPCMD = "/ mp:https: / &#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 SMSSiteCode = PS1 SMSMP = https: / &#47; sccmmp.corp.contoso.com AADTENANTID = 72F988BF-86F1-41AF-91AB-2D7CD011XXXX AADTENANTNAME = contoso AADCLIENTAPPID = bef323b3-042f-41a6-907a-f9faf0d1XXXX AADRESOURCEURI = https: / &#47; ConfigMgrServer'

> [!Tip]
> U vindt de opdrachtregelparameters voor uw site met behulp van de volgende stappen uit:     
> 1. Ga in de Configuration Manager-console naar **beheer** > **overzicht** > **Cloudservices**  >  **Mede management**.  
> 2. Kies op het tabblad Start in de groep beheren **mede management configureren** openen van de Wizard mede management voorbereiden.    
> 3. Klik op de pagina abonnement **aanmelden** aanmelden bij uw Intune-tenant en klik vervolgens op **volgende**.    
> 4. Klik op de pagina stuk **kopie** in de **apparaten zijn ingeschreven in Intune** sectie voor de opdrachtregel naar het Klembord kopiëren en sla de opdrachtregel om te gebruiken in de procedure om de app te maken.  
> 5. Klik op **annuleren** de wizard wilt afsluiten.

> [!Important]    
> Als u de opdrachtregel voor het installeren van Configuration Manager-client wilt aanpassen, moet u dat de opdrachtregel niet langer zijn dan 1024 tekens. Wanneer de opdrachtregel groter dan 1024 tekens is, mislukt de installatie van de client.


## <a name="new-windows-10-devices"></a>Nieuwe Windows 10-apparaten
Voor de nieuwe Windows 10-apparaten, kunt u de service Automatische piloot voor het configureren van de buiten-vak ervaring, waaronder het apparaat toevoegen aan AD en Azure AD, evenals het apparaat in Intune inschrijven. Vervolgens maakt u een app in Intune voor het implementeren van Configuration Manager-client.  
1. Schakel automatische piloot voor de nieuwe Windows 10-apparaten. Zie voor meer informatie [overzicht Windows Automatische piloot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot).  
2. Automatische inschrijving configureren in Azure AD voor uw apparaten automatisch worden geregistreerd bij Intune. Zie voor meer informatie [inschrijven Windows-apparaten voor Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).
3. Een app maken in Intune met het clientpakket voor Configuration Manager en de app implementeren op Windows 10-apparaten die u wilt CO beheren. Gebruik de [vanaf de opdrachtregel voor het installeren van Configuration Manager-client](#command-line-to-install-configuration-manager-client) wanneer u de stappen voor het doorloopt [-clients installeren vanaf het Internet met behulp van Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).   

## <a name="windows-10-devices-not-enrolled-in-intune-or-a-configuration-manager-client"></a>Windows 10-apparaten die niet zijn ingeschreven in Intune of Configuration Manager-client
Voor Windows 10-apparaten die niet zijn ingeschreven in Intune of Configuration Manager-client hebt, kunt u automatische inschrijving op het apparaat inschrijven bij Intune. Vervolgens maakt u een app in Intune voor het implementeren van Configuration Manager-client.
1. Automatische inschrijving configureren in Azure AD voor uw apparaten automatisch worden geregistreerd bij Intune. Zie voor meer informatie [inschrijven Windows-apparaten voor Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).  
2. Een app maken in Intune met het clientpakket voor Configuration Manager en de app implementeren op Windows 10-apparaten die u wilt CO beheren. Gebruik de [vanaf de opdrachtregel voor het installeren van Configuration Manager-client](#command-line-to-install-configuration-manager-client) wanneer u de stappen voor het doorloopt [-clients installeren vanaf het Internet met behulp van Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).

## <a name="windows-10-devices-enrolled-in-intune"></a>Windows 10-apparaten die zijn ingeschreven bij Intune
Voor Windows 10-apparaten die al zijn ingeschreven in Intune, moet u een app maken in Intune voor het implementeren van Configuration Manager-client. Gebruik de [vanaf de opdrachtregel voor het installeren van Configuration Manager-client](#command-line-to-install-configuration-manager-client) wanneer u de stappen voor het doorloopt [-clients installeren vanaf het Internet met behulp van Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).  

## <a name="next-steps"></a>Volgende stappen
[Configuration Manager-workloads overschakelen naar Intune](co-management-switch-workloads.md)