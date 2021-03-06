---
title: Voorbereiden van Windows 10 voor CO-management
titleSuffix: Configuration Manager
description: Informatie over het voorbereiden van uw Windows 10-apparaten voor CO-beheer.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology: ''
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.openlocfilehash: a45ded0f3824c148f64f9578e51cc112c05d9f78
ms.sourcegitcommit: aed99ba3c5e9482199cb3fc5c92f6f3a160cb181
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2018
---
# <a name="prepare-windows-10-devices-for-co-management"></a>Windows 10-apparaten voor het beheer van CO voorbereiden
U kunt CO-beheer op Windows 10-apparaten die zijn toegevoegd aan AD en Azure AD en ingeschreven bij Microsoft Intune en een client in Configuration Manager inschakelen. Voor de nieuwe Windows 10-apparaten, en voor apparaten die al zijn ingeschreven in Intune, de Configuration Manager-client installeren voordat ze samen beheerd worden kunnen. Voor Windows 10-apparaten die al Configuration Manager-clients, kunt u de apparaten inschrijven bij Intune en mede-beheer in de Configuration Manager-console inschakelen.

> [!IMPORTANT]
> Windows 10 mobile-apparaten bieden geen ondersteuning voor CO-beheer.



## <a name="command-line-to-install-configuration-manager-client"></a>Vanaf de opdrachtregel voor het installeren van Configuration Manager-client
Een app maken in Intune voor Windows 10-apparaten die nog geen Configuration Manager-clients. Wanneer u de app in de volgende secties maakt, gebruikt u de volgende opdrachtregel:

`ccmsetup.msi CCMSETUPCMD="/mp:<URL of cloud management gateway mutual auth endpoint> CCMHOSTNAME=<URL of cloud management gateway mutual auth endpoint> SMSSiteCode=<Sitecode> SMSMP=https://<FQDN of MP> AADTENANTID=<AAD tenant ID> AADCLIENTAPPID=<Server AppID for AAD Integration> AADRESOURCEURI=https://<Resource ID>"`

Bijvoorbeeld, als u had de volgende waarden:

- **URL van een cloudeindpunt management gateway wederzijdse verificatie**: https:/&#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500    

   >[!Note]    
   >Gebruik de **MutualAuthPath** waarde in de **vProxy_Roles** SQL-weergave voor de **URL van een cloudeindpunt management gateway wederzijdse verificatie** waarde.

- **FQDN van beheerpunt (MP)**: mp1.contoso.com    
- **Sitecode**: PS1    
- **Azure AD-tenant-ID**: daf4a1c2-3a0c-401b-966f-0b855d3abd1a    
- **Azure AD client app-ID**: 7506ee10-f7ec-415a-b415-cd3d58790d97     
- **AAD Resource-ID-URI**: ConfigMgrServer    

  > [!Note]    
  > Gebruik de **IdentifierUri** waarde gevonden in de **vSMS_AAD_Application_Ex** SQL-weergave voor de **AAD Resource-ID-URI** waarde.

Gebruikt u de volgende opdrachtregel:

`ccmsetup.msi CCMSETUPCMD="/mp:https://contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500    CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=PS1 SMSMP=https://mp1.contoso.com AADTENANTID=daf4a1c2-3a0c-401b-966f-0b855d3abd1a AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://ConfigMgrServer"`

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

   > [!NOTE]   
   > Vanaf versie 1802, Configuration Manager gebruiken voor het verzamelen en rapporteren de apparaatgegevens vereist door de Microsoft Store voor bedrijven en Education. Deze informatie omvat het serienummer van het apparaat, Windows-product-id en een hardware-id. In de Configuration Manager-console **bewaking** werkruimte, vouw de **rapportage** knooppunt uitvouwen **rapporten**, en selecteer de **Hardware - algemeen**  knooppunt. Voer het nieuwe rapport **Windows Automatische piloot apparaatgegevens** en bekijk de resultaten. Klik in de rapportviewer de **exporteren** pictogram en selecteer de **CSV (door komma's gescheiden)** optie. Nadat het bestand is opgeslagen, moet u de gegevens uploaden naar de Microsoft Store voor bedrijven en Education. Zie voor meer informatie [apparaten toevoegen in Microsoft Store voor bedrijven en Education](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile).

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