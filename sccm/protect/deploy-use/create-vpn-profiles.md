---
title: Het maken van VPN-profielen in System Center Configuration Manager | Microsoft-documenten
description: Informatie over het VPN-profielen maken in System Center Configuration Manager.
ms.custom: 
ms.date: 4/19/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
caps.latest.revision: 15
author: lleonard-msft
caps.handback.revision: 0
ms.author: alleonar
ms.manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7a6c89254d01f4074e5c170b20338686178ebdd3
ms.openlocfilehash: 359fcfd9754fb5c81763bc44cac45376ea3ab0b8
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-vpn-profiles-in-system-center-configuration-manager"></a>VPN-profielen maken in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De verbinding die beschikbaar zijn voor de verschillende apparaatplatforms worden beschreven in [VPN-profielen in System Center Configuration Manager](../../protect/deploy-use/vpn-profiles.md).  

Distribueer de VPN-app voordat u het VPN-profiel implementeert voor de VPN-verbindingen van derden. Als u niet de app implementeert, worden gebruikers gevraagd te doen als ze proberen verbinding maken met de VPN-verbinding. Zie voor meer informatie over het implementeren van apps, [implementeren van toepassingen met System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

### <a name="create-a-vpn-profile"></a>Een VPN-profiel maken   

1.  Kies in de Configuration Manager-console **activa en naleving** > **compatibiliteitsinstellingen** > **toegang tot bedrijfsbronnen** > **VPN-profielen**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **VPN-profiel maken**.  


1.  Voltooi de **algemeen** pagina. Houd rekening met het volgende:  

       - Gebruik niet de tekens \\/ :*?&lt; > &#124; of een spatie in de naam van VPN-profiel. Deze tekens worden niet ondersteund door de Windows Server-VPN-profiel.  

       -   Selecteer **een bestaand VPN-profielitem uit een bestand importeren** voor VPN-profielgegevens importeren die werd geëxporteerd naar een XML-bestand (Windows 8.1 en Windows RT alleen).  

1.  Op de **verbinding** pagina:  

    -   **Verbindingstype**: Kies het type VPN-verbinding. U kunt kiezen uit de verbindingtypen in de volgende tabel.  

    -   **Lijst met servers**: Een nieuwe server moet worden gebruikt voor de VPN-verbinding toevoegen. Afhankelijk van het verbindingstype, kunt u een of meer VPN-servers toevoegen en de standaard-server opgeven.  

        > [!NOTE]  
        >  iOS-apparaten bieden geen ondersteuning voor het gebruik van meerdere VPN-servers. Als u meerdere VPN-servers configureert en vervolgens het VPN-profiel implementeert op een iOS-apparaat, wordt alleen de standaardserver gebruikt.  

     Deze tabel bevat opties voor verbindingstypen. Raadpleeg de documentatie van de VPN-server voor meer informatie.

| &nbsp;&nbsp;Optie&nbsp;&nbsp; | Meer informatie | &nbsp;&nbsp;Verbinding&nbsp;type&nbsp;&nbsp; |  
|----------------|----------------------|---------------------|  
|**Realm**     |De verificatierealm die u wilt gebruiken. Een verificatierealm is een groepering van verificatiebronnen die worden gebruikt door het verbindingstype Pulse Secure.|Pulse Secure|    
|**Rol**        |De gebruikersrol die toegang tot deze verbinding heeft. |Pulse Secure|  
|**Aanmeldingsgroep of -domein** |De naam van de aanmeldingsgroep of het aanmeldingsdomein waarmee u verbinding wilt maken.|Dell SonicWALL Mobile Connect|  
|**Vingerafdruk**  |Een tekenreeks, bijvoorbeeld 'Contoso-Vingerafdrukcode' die wordt gebruikt om te controleren of de VPN-server kan worden vertrouwd.<br /><br /> Een vingerafdruk kan:<br /><br /> - Worden verzonden naar de client zodat deze alle servers vertrouwt die dezelfde vingerafdruk presenteren bij het maken van verbinding.<br /><br /> -Als het apparaat nog niet de vingerafdruk beschikt, vertrouwt de VPN-server waarmee ze verbinding maakt terwijl de vingerafdruk wordt weergegeven van de gebruiker wordt gevraagd (de gebruiker controleert de vingerafdruk handmatig en kiest **vertrouwensrelatie** verbinding maken).|Check Point Mobile VPN|  
|**Alle netwerkverkeer via de VPN-verbinding verzenden** |Als deze optie niet is ingeschakeld, kunt u aanvullende routes voor verbinding opgeven (voor de verbindingstypen **Microsoft SSL (SSTP)**, **Microsoft Automatic**, **IKEv2**, **PPTP** en **L2TP** ). Dit wordt wel split- of VPN-tunneling genoemd.<br /><br /> Alleen verbindingen met het bedrijfsnetwerk worden verzonden via een VPN-tunnel. VPN-tunneling wordt niet gebruikt wanneer u verbinding maakt met resources op internet. |Alle|  
|**Verbindingsspecifiek DNS-achtervoegsel** |De verbindingsspecifieke Domain Name System (DNS)-achtervoegsel voor de verbinding.|- Microsoft SSL (SSTP)<br /><br /> - Microsoft Automatic<br /><br /> - IKEv2<br /><br /> - PPTP<br /><br /> - L2TP|  
|**VPN overslaan bij verbinding met Wi-Fi-bedrijfsnetwerk**  |De VPN-verbinding worden niet gebruikt wanneer het apparaat is verbonden met het Wi-Fi-bedrijfsnetwerk.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - Check Point Mobile VPN<br /><br /> - Microsoft SSL (SSTP)<br /><br /> - Microsoft Automatic<br /><br /> - IKEv2<br /><br /> - L2TP|  
|**VPN overslaan bij verbinding met Wi-Fi-thuisnetwerk**  |De VPN-verbinding worden niet gebruikt wanneer het apparaat is verbonden met een Wi-Fi-netwerk thuis.|Alle|  
|**Per app-VPN (iOS 7 en hoger, Mac OS X 10.9 en hoger)** |Deze VPN-verbinding koppelen aan een iOS-app zodat de verbinding wordt geopend wanneer de app wordt uitgevoerd. U kunt het VPN-profiel aan een app koppelen bij het implementeren.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - Check Point Mobile VPN|  
|**Aangepaste XML (optioneel)** |Aangepaste XML-opdrachten opgeven waarmee de VPN-verbinding configureren.<br /><br /> Voorbeelden:<br /><br /> Voor **Pulse Secure**:<br /><br /> **&lt;Pulse schema ><br /> &nbsp; &lt;isSingleSignOnCredential > waar&lt;/isSingleSignOnCredential\><br />&lt;/pulse-schema >**<br /><br /> Voor **CheckPoint Mobile VPN**:<br /><br /> **&lt;CheckPointVPN <br /> &nbsp; poort = "443" name = "CheckPointSelfhost" <br /> &nbsp; sso = "true" <br /> &nbsp; debug = "3"<br />/>**<br /><br /> Voor **Dell SonicWALL Mobile Connect**:<br /><br /> **&lt;MobileConnect\> <br /> &nbsp; &nbsp; &lt;compressie\>false&lt;/Compression\> <br /> &nbsp; &nbsp; &lt;debugLogging\>waar&lt;/debugLogging\> <br /> &nbsp; &nbsp; &lt;packetCapture\>False&lt;/packetCapture\><br />&lt;/MobileConnect\>**<br /><br /> Voor **F5 Edge Client**:<br /><br /> **&lt;F5-vpn-conf >&lt;één teken op referentie >&lt;/f5-vpn-conf >**<br /><br /> Raadpleeg de VPN-documentatie van elke fabrikant voor meer informatie over het schrijven van aangepaste XML-opdrachten.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - Check Point Mobile VPN|  

> [!NOTE]  
>  Zie voor specifieke informatie voor VPN-profielen maken voor mobiele apparaten, [VPN-profielen maken](../../mdm/deploy-use/create-vpn-profiles.md)  

Voltooi de wizard. Het nieuwe VPN-profiel wordt weergegeven in het knooppunt **VPN-profielen** van de werkruimte **Activa en naleving** .

### <a name="next-steps"></a>Volgende stappen

- Distribueer de VPN-app voordat u het VPN-profiel implementeert voor de VPN-verbindingen van derden. Als u niet de app implementeert, worden gebruikers gevraagd te doen als ze proberen verbinding maken met de VPN-verbinding. Zie voor meer informatie over het implementeren van apps, [implementeren van toepassingen met System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).

- Implementeer het VPN-profiel, zoals beschreven in [profielen in System Center Configuration Manager implementeren](deploy-wifi-vpn-email-cert-profiles.md).  
