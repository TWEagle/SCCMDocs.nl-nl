---
title: Best practices voor implementatie van clients | Microsoft Docs
description: Aanbevolen procedures voor clientimplementatie in System Center Configuration Manager worden opgehaald.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a933d69c-5feb-4b2b-84e8-56b3b64d5947
caps.latest.revision: "11"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 979c21c436429cad03a61671b707a99817146d95
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="best-practices-for-client-deployment-in-system-center-configuration-manager"></a>Aanbevolen procedures voor de implementatie van clients in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*


## <a name="use-software-update-based-client-installation-for-active-directory-computers"></a>Gebruik software-update-gebaseerde clientinstallatie voor Active Directory-computers  
 Deze client-implementatiemethode bestaande Windows-technologieën gebruikt, kan worden geïntegreerd met uw Active Directory-infrastructuur, is de minimale configuratie in Configuration Manager vereist, is het eenvoudigst te configureren voor firewalls en is de veiligste. Met behulp van beveiligingsgroepen en WMI-filtering Groepsbeleid-configuratie, hebt u ook veel flexibiliteit om te controleren welke computers de Configuration Manager-client installeren.  

 Zie [Configuration Manager-clients installeren met behulp van installatie op basis van software-updates](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP) voor meer informatie.  

## <a name="extend-the-active-directory-schema-and-publish-the-site-so-that-you-can-run-ccmsetup-without-command-line-options"></a>Breid het Active Directory-schema uit en publiceer de site zodat u CCMSetup kunt uitvoeren zonder opdrachtregelopties  
 Wanneer u het Active Directory-schema voor Configuration Manager uitbreiden en de site is gepubliceerd naar Active Directory Domain Services, worden veel clientinstallatie-eigenschappen gepubliceerd op Active Directory Domain Services. Als een computer deze clientinstallatie-eigenschappen localiseren kan, kan hij ze gebruiken tijdens de clientimplementatie van de Configuration Manager. Omdat deze informatie automatisch gegenereerd wordt, wordt het risico van menselijke fout, gekoppeld met het handmatig invoeren van installatie-eigenschappen, geëlimineerd.  

 Zie [About client installation properties published to Active Directory Domain Services in System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md) (Informatie over eigenschappen van clientinstallaties die zijn gepubliceerd naar Active Directory Domain Services in System Center Configuration Manager) voor meer informatie.  

## <a name="use-a-phased-rollout-to-manage-cpu-usage"></a>Een gefaseerde implementatie gebruiken voor het beheren van CPU-gebruik  
 Minimaliseer het effect van de vereisten voor CPU-verwerking op de siteserver met behulp van een gefaseerde implementatie van clients. Implementeer clients buiten werkuren zodat andere services meer beschikbare bandbreedte tijdens de dag hebben en gebruikers niet verstoord zijn doordat hun computer traag wordt of opnieuw worden opgestart.  

## <a name="enable-automatic-upgrade-after-your-main-client-deployment-has-finished"></a>Automatische upgrade inschakelen nadat de belangrijkste clientimplementatie is voltooid  
 [Automatische clientupgrades](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md) zijn handig als u upgraden van een beperkt aantal clientcomputers die ontbreken door uw belangrijkste clientinstallatiemethode, mogelijk wilt kunnen omdat deze offline was. 

> [!NOTE]  
>  Prestatieverbeteringen in Configuration Manager kunt u automatische updates gebruiken als een primaire clientupgrademethode. Prestatie zal evenwel afhangen van uw hiërarchie-infrastructuur, zoals het aantal clients.  


## <a name="use-smsmp-and-fsp-if-you-install-the-client-with-clientmsi-properties"></a>Gebruik SMSMP en FSP als u de client installeert met client.msi-eigenschappen.  
 De SMSMP-eigenschap specificeert het initiële beheerpunt waarmee de client dient te communiceren en elimineert de afhankelijkheid van plaats in oplossingen zoals Active Directory Domain Services, DNS en WINS.  

 Gebruik de FSP-eigenschap en installeer een terugvalstatuspunt zodat u clientinstallatie en -toewijzing kunt controleren en identificeer communicatieproblemen.  

 Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie over deze opties.  

## <a name="install-client-language-packs-before-you-install-the-clients"></a>Client-taalpakketten te installeren voordat u de clients installeert  
Het is raadzaam om client-taalpakketten te installeren voordat de client implementeren. Als u installeert [clienttaalpakketten](../../../../core/servers/deploy/install/language-packs.md) (om extra talen) op een site nadat u clients, installeert u moet de clients opnieuw installeren voordat deze talen kan worden gebruikt. Voor clients van mobiele apparaten, moet u het mobiele apparaat wissen en opnieuw inschrijven.  

## <a name="prepare-required-pki-certificates-in-advance"></a>Bereid vereiste PKI-certificaten op voorhand voor  
 Om apparaten op het internet, geregistreerde mobiele apparaten en Mac-computers te beheren, moet u PKI-certificaten hebben op sitesystemen (beheerpunten en distributiepunten) en de clientapparaten. U kunt op productienetwerken goedkeuring nodig hebben om nieuwe certificaten te gebruiken, systeemservers van de site te herstarten of gebruikers kunnen zich moeten afmelden en aanmelden voor nieuw groepslidmaatschap. Bovendien kan het zijn dat u voldoende replicatietijd voor de beveiligingsmachtigingen en voor alle nieuwe certificaatsjablonen moet voorzien.  

 Zie voor meer informatie over de vereiste PKI-certificaten, [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

## <a name="before-you-install-clients-configure-any-required-client-settings-and-maintenance-windows"></a>Configureer, vóór u clients installeert, nodige clientinstellingen en onderhoudsvensters.  
 Weliswaar u kunt [clientinstellingen configureren](../../../../core/clients/deploy/configure-client-settings.md) en onderhoudsvensters voordat of nadat clients zijn geïnstalleerd, is het beter is vereist om instellingen te configureren voordat u clients installeert, zodat ze worden gebruikt als de client is geïnstalleerd. 

 Onderhoudsvensters voor servers en voor Windows Embedded-apparaten om de bedrijfscontinuïteit voor apparaten configureren. Onderhoudsvensters zorgt ervoor dat vereiste software-updates en antimalware-software niet opnieuw de computer tijdens de kantooruren opstarten.  

> [!IMPORTANT]  
>  Voor Windows 10-computers die u wilt beveiligen met Unified Write Filter (UWF), moet u het apparaat voor UWF configureren voordat u de client installeert. Hierdoor is Configuration Manager de client installeren met een aangepaste Referentieprovider die gebruikers met beperkte rechten tijdens de onderhoudsmodus aanmelden op het apparaat vergrendeld.  

## <a name="plan-your-user-enrollment-experience-for-mac-computers-and-mobile-devices"></a>Plan uw gebruikersregistratie-ervaring voor Mac-computers en mobiele apparaten   
 Als gebruikers hun eigen Mac-computers en mobiele apparaten met Configuration Manager registreren zullen, plant u de gebruikerservaring. U kunt bijvoorbeeld de installatie en het registratieproces script met behulp van een webpagina, zodat gebruikers de minimale hoeveelheid gegevens die nodig zijn invoeren, en instructies met een koppeling per e-mail verzenden.  

## <a name="use-file-based-write-filters-for-windows-embedded-devices"></a>Gebruik van File Based Write Filters voor Windows Embedded-apparaten 
 Ingesloten apparaten die Verbeterde schrijffilters (EWF) gebruiken, hebben grote kans om Hersynchronisaties te ondergaan van de statusmelding. Indien u slechts enkele ingesloten apparaten hebt, die Verbeterde schrijffilters gebruiken, kan het zijn dat u daar niets van merkt. Indien u daarentegen veel ingesloten apparaten hebt die hun informatie hersynchroniseren, zoals het zenden van een volledige inventaris in plaats van een inventaris voor verschillen, kan dit een merkbare toename genereren van netwerkpakketten en een grotere CPU-verwerking op de siteserver.  

 Wanneer u een keuze van het type schrijffilter om in te schakelen, kies bestand gebaseerde schrijffilters en configureer uitzonderingen om clientstatus en inventarisgegevens tussen het herstarten van apparaten voor netwerk- en CPU-efficiëntie op de Configuration Manager-client te behouden. Zie [Clientimplementatie op Windows Embedded-apparaten in System Center Configuration Manager plannen](../../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md) voor meer informatie over schrijffilters.  

 Zie [Ondersteunde besturingssystemen voor clients en apparaten](../../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md) voor meer informatie over het maximum aantal Windows Embedded-clients dat een primaire site kan ondersteunen.  
