---
title: Beheer op afstand beveiliging privacy | Microsoft Docs
description: Beveiliging en privacy-informatie ophalen voor beheer op afstand in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 272ee86b-d3d9-4fd9-b5c4-73e490e1a1e4
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 03b8ede7fa4f4c02ffb551bb28fe2db234d39b12
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-remote-control-in-system-center-configuration-manager"></a>Beveiliging en privacy voor beheer op afstand in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp bevat beveiligings- en privacy-informatie voor beheer op afstand in System Center 2012 Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a> Aanbevolen procedures voor beveiliging voor beheer op afstand  
 Gebruik de volgende aanbevolen procedures voor beveiliging wanneer u clientcomputers beheert via beheer op afstand.  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Als u verbinding wilt maken met een externe computer, moet u stoppen als NTLM-verificatie wordt gebruikt in plaats van Kerberos-verificatie.|Als Configuration Manager detecteert dat de sessie voor extern beheer met behulp van NTLM in plaats van Kerberos is geverifieerd, ziet u een opdrachtprompt met een waarschuwing dat de identiteit van de externe computer kan niet worden geverifieerd. Ga niet verder met de sessie voor beheer op afstand. NTLM-verificatie is een zwakker verificatieprotocol dan Kerberos en is kwetsbaar voor opnieuw afspelen en imitatie.|  
|Activeer Klembord delen niet in de viewer voor beheer op afstand.|Het Klembord ondersteunt objecten, zoals uitvoerbare bestanden en tekst, en kan door de gebruiker op de hostcomputer tijdens de sessie voor beheer op afstand worden gebruikt om een programma uit te voeren op de oorspronkelijke computer.|  
|Geef geen wachtwoorden voor bevoegde accounts op wanneer u een computer op afstand beheert.|Het wachtwoord kan worden vastgelegd door software waarmee toetsenbordinvoer kan worden geregistreerd. Het wachtwoord kan ook worden vastgelegd als het programma dat wordt uitgevoerd op de clientcomputer niet het programma is dat de gebruiker van beheer op afstand denkt. Wanneer accounts en wachtwoorden vereist zijn, moet de eindgebruiker deze invoeren.|  
|Vergrendel het toetsenbord en de muis tijdens een sessie voor beheer op afstand.|Als Configuration Manager detecteert dat de beheer op afstand verbinding is verbroken, wordt het toetsenbord en muis door Configuration Manager vergrendeld, zodat een gebruiker kan niet van de sessie voor beheer op afstand overnemen. Deze detectie vindt mogelijk echter niet direct plaats en vindt niet plaats als de service voor beheer op afstand is beëindigd.<br /><br /> Selecteer de actie **Extern toetsenbord en muis vergrendelen** in het venster **Afstandbediening ConfigMgr** .|  
|Laat gebruikers geen instellingen voor beheer op afstand configureren in Software Center.|Schakel de clientinstelling **Gebruikers kunnen instellingen voor beleid of meldingen wijzigen in Software Center** niet in om te voorkomen dat gebruikers worden bespioneerd.<br /><br /> Deze instelling is voor de computer, niet voor de aangemelde gebruiker.|  
|Schakel het Windows Firewall-profiel **Domein** in.|Schakel de clientinstelling **Beheer op afstand inschakelen op clients Firewall-uitzonderingsprofielen** in en selecteer vervolgens het Windows Firewall-profiel **Domein** voor intranetcomputers.|  
|Als u zich afmeldt tijdens een sessie voor beheer op afstand en u zich vervolgens aanmeldt als een andere gebruiker, moet u zich weer afmelden voordat u de sessie voor beheer op afstand beëindigt.|Als u zich niet afmeldt in dit scenario, blijft de sessie geopend.|  
|Geef gebruikers geen lokale beheerdersrechten.|Wanneer u gebruikers lokale beheerdersrechten geeft, kunnen ze uw sessie voor beheer op afstand mogelijk overnemen of met uw referenties knoeien.|  
|Groepsbeleid of Configuration Manager gebruiken voor het configureren van instellingen voor hulp op afstand, maar niet beide.|U kunt de Configuration Manager en Groepsbeleid configuratiewijzigingen aanbrengen in de instellingen van Hulp op afstand gebruiken. Wanneer Groepsbeleid wordt vernieuwd op de client, wordt het proces standaard geoptimaliseerd door alleen de beleidsregels te wijzigen die zijn gewijzigd op de server. Configuration Manager wijzigt de instellingen in het lokale beveiligingsbeleid, kan niet worden overschreven, tenzij de Groepsbeleid-update wordt geforceerd.<br /><br /> Wanneer u op beide plaatsen beleid instelt, kan dit leiden tot inconsistente resultaten. Kies een van deze methoden om uw instellingen voor Hulp op afstand te configureren.|  
|Schakel de clientinstelling **Gebruikers vragen naar machtiging voor Beheer op afstand**in.|Hoewel er manieren zijn om deze clientinstelling, waarbij een gebruiker wordt gevraagd een sessie voor beheer op afstand te bevestigen, te omzeilen, kunt u deze instelling inschakelen om het risico te beperken dat gebruikers worden bespioneerd terwijl ze aan vertrouwelijke taken werken.<br /><br /> Leer gebruikers daarnaast om de accountnaam te controleren die tijdens de sessie voor beheer op afstand wordt weergegeven en de sessie te beëindigen als ze vermoeden dat het account niet is geautoriseerd.|  
|Beperk de lijst van toegestane viewers.|Een gebruiker heeft geen lokale beheerdersrechten nodig om beheer op afstand te kunnen gebruiken.|  

### <a name="security-issues-for-remote-control"></a>Beveiligingsproblemen voor beheer op afstand  
 Bij het beheren van clientcomputers via beheer op afstand kunnen de volgende beveiligingsproblemen optreden:  

-   Beschouw controleberichten voor beheer op afstand niet als betrouwbaar.  

     Als u een sessie voor beheer op afstand start en u zich vervolgens aanmeldt met alternatieve referenties, worden de controleberichten verzonden voor het oorspronkelijke account, niet het account dat de alternatieve referenties gebruikte.  

     Controleberichten worden niet verzonden als u de binaire bestanden voor beheer op afstand kopieert in plaats van de Configuration Manager-console installeren en voer vervolgens extern beheer bij de opdrachtprompt.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Privacy-informatie voor beheer op afstand  
 Beheer op afstand kunt u actieve sessies op Configuration Manager-clientcomputers bekijken en mogelijk de gegevens opgeslagen op deze computers bekijken. Beheer op afstand is standaard niet ingeschakeld.  

 Hoewel u beheer op afstand zo kunt configureren dat er opvallende meldingen worden weergegeven en er toestemming moet worden verkregen van een gebruiker voordat een sessie voor beheer op afstand begint, kunnen deze gebruikers ook zonder hun toestemming of medeweten worden gevolgd. U kunt het toegangsniveau Alleen weergeven, zodat niets kan worden gewijzigd tijdens de sessie voor beheer op afstand, of Volledig beheer configureren. Het account van de beheerder van de verbinding wordt weergegeven in de sessie voor extern beheer, zodat gebruikers kunnen zien wie er verbinding maakt met hun computer.  

 Standaard verleent Configuration Manager de lokale beheerders groepsmachtigingen voor beheer op afstand.  

 Houd rekening met uw privacyvereisten voordat u beheer op afstand configureert.  
