---
title: "Tool hiërarchie-onderhoud"
titleSuffix: Configuration Manager
description: Begrijpen wat de Hierarchy Maintenance Tool doet en waarom u deze kunt gebruiken. Bevat de verwijzing naar de opdrachtregelopties.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cead6825-6113-4ba5-a381-ac3598dfee86
caps.latest.revision: "7"
caps.handback.revision: "0"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 641dccd321bf9e48f1229e7023b8958896d0a19e
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2017
---
# <a name="hierarchy-maintenance-tool-preinstexe-for-system-center-configuration-manager"></a>De tool Hiërarchie-onderhoud (Preinst.exe) voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De tool hiërarchie-onderhoud (Preinst.exe) geeft opdrachten door naar de System Center Configuration Manager hiërarchie Manager terwijl de Hiërarchiebeheerder-Services wordt uitgevoerd. Het hiërarchie-onderhoud-hulpprogramma wordt automatisch geïnstalleerd wanneer u een Configuration Manager-site installeert. U kunt Preinst.exe vinden in de \\ &lt; *SiteServerName*> \SMS_&lt;*SiteCode*\bin\X64\00000409 gedeelde map op de siteserver.  

 U kan het hiërarchieonderhoud-hulpprogramma gebruiken in de volgende scenario's:  

-   Wanneer uitwisseling van een beveiligde sleutel vereist is, zijn er situaties waarin u handmatig de initiële uitwisseling van de openbare sleutel tussen sites moet uitvoeren. Zie [Handmatig uitwisselen van openbare sleutels tussen sites](#BKMK_ManuallyExchangeKeys) in dit onderwerp voor meer informatie.  

-   Om actieve jobs te verwijderen die voor een doelsite zijn die niet langer beschikbaar is.  

-   Verwijderen van de Configuration Manager-console een siteserver wanneer u niet verwijderen van de site bent met Setup. Als u een Configuration Manager-site zonder eerst Setup uit te voeren voor het verwijderen van de site fysiek verwijdert, zal de informatie van de site nog bestaan in de database van de bovenliggende site en de bovenliggende site zal blijven proberen om te communiceren met de onderliggende site. U lost dit probleem, moet u het Hiërarchieonderhoud-hulpprogramma uitvoeren en de onderliggende site handmatig verwijderen uit de database van de bovenliggende site.  

-   Alle services te stoppen Configuration Manager op een site zonder de services afzonderlijk te stoppen.  

-   Wanneer u een site herstelt, kunt u de CHILDKEYS-optie gebruiken om de openbare sleutels te verdelen van meerdere onderliggende site naar de herstellende site.  

Om het hiërarchieonderhoud-hulpprogramma uit te voeren, moet de huidige gebruiker beheerderrechten hebben op de lokale computer. De gebruiker moet ook expliciet het sitebeheerderrecht hebben; het is niet voldoende dat de gebruiker dit recht erft door een lid te zijn van een groep die deze machtiging heeft.  

## <a name="hierarchy-maintenance-tool-command-line-options"></a>Opdrachtregelopties voor het hiërarchieonderhoud-hulpprogramma  
Wanneer u het hiërarchieonderhoud-hulpprogramma gebruikt, moet u het lokaal uitvoeren op de centrale beheersite, de primaire site of de secundaire siteserver.  

Wanneer u het Hiërarchieonderhoud-hulpprogramma uitvoert, moet u de volgende syntaxis gebruiken: preinst.exe /&lt;optie\>. Hieronder vindt u de opdrachtregelopties.  

 **/ DELJOB &lt;* SiteCode*> **-Gebruik deze optie op een site om te wissen van alle taken of opdrachten vanaf de huidige site tot de gespecificeerde doelsite.  

 **/ DELSITE &lt;* ChildSiteCodeToRemove*> **-Gebruik deze optie op een bovenliggende site te verwijderen van de gegevens voor de onderliggende sites uit de sitedatabase van de bovenliggende site. U gebruikt deze optie typisch als een siteservercomputer buiten bedrijf gesteld wordt vóór u de site ervan verwijdert.  

> [!NOTE]  
>  De /DELSITE-optie maakt de installatie van de site op de computer, opgegeven door de ChildSiteCodeToRemove-parameter, niet ongedaan. Deze optie verwijdert alleen de site-informatie uit de Configuration Manager-sitedatabase.  

**/ DUMP &lt;* SiteCode*> **-Gebruik deze optie op de lokale siteserver om sitebeheerinstallatiekopieën te schrijven naar de hoofdmap van het station waarop de site is geïnstalleerd. U kunt een specifieke sitebeheerinstallatiekopie schrijven naar de map of naar alle sitebeheerbestanden in de hiërarchie schrijven.  

-   / DUMP &lt; *SiteCode*> schrijft de sitebeheerinstallatiekopie alleen voor de opgegeven site.  

-   /DUMP schrijft de sitebesturingsbestanden voor alle sites.  

Een installatiekopie is een binaire voorstelling van het sitebeheerbestand, dat is opgeslagen in de Configuration Manager-sitedatabase. De gedumpte installatiekopie van het sitebeheerbestand is een som van de basisinstallatiekopie plus de hangende installatiekopieën van de verschillen.  

Na het dumpen van een installatiekopie van het bestand met het hulpprogramma voor hiërarchie-onderhoud, de bestandsnaam is in de opmaak sitectrl_&lt;*SiteCode*> .ct0.  

**/ STOPSITE** -Gebruik deze optie op de lokale siteserver om een afsluitcyclus voor de Configuration Manager Site Component Manager-service, die de site gedeeltelijk terugzet te initiëren. Wanneer deze afsluitcyclus uitgevoerd wordt, worden sommige Configuration Manager-services op een siteserver en zijn externe sitesystemen gestopt. Deze services zijn gemarkeerd voor opnieuw installeren. Tengevolge van deze afsluitcyclus, worden sommige wachtwoorden automatisch gewijzigd wanneer de services worden geïnstalleerd.  

> [!NOTE]  
>  Indien u een registratie wilt zien van afsluiten, herinstallatie en wachtwoordwijzigingen voor beheer van siteonderdelen, schakel dan de logboekregistratie in voor dit onderdeel door deze opdrachtregeloptie te gebruiken.  

Nadat de afsluitcyclus gestart is, loopt hij automatisch, waarbij hij niet-reagerende componenten of computers overslaat. Als de Beheer-van-siteonderdelen-service evenwel geen toegang kan krijgen tot een extern sitesysteem tijdens de afsluitcyclus, worden de onderdelen die zijn geïnstalleerd op het externe sitesysteem opnieuw geïnstalleerd wanneer de Beheer-van-de-siteonderdelen-service is gestart. Wanneer hij gestart is, probeert de Beheer-van-siteonderdelen-service herhaaldelijk de herinstallatie van alle services die gemarkeerd zijn voor herinstallatie, totdat hij erin slaagt.  

U kunt de Beheer-van-siteonderdelen-service opnieuw starten door gebruik te maken van sitebeheer. Nadat hij opnieuw gestart is, worden alle beïnvloede services verwijderd, opnieuw geïnstalleerd en opnieuw opgestart. Nadat u de /STOPSITE-optie gebruikt om de afsluitcyclus te initiëren, kunt u de cycli voor herinstallatie niet vermijden nadat de Beheer-van-siteonderdelen-service opnieuw gestart is.  

**/KEYFORPARENT**: gebruik deze optie op een site om de openbare sleutel van de site te distribueren naar een bovenliggende site.  

De/keyforparent-optie plaatst de openbare sleutel van de site in het bestand &lt; *SiteCode*>. Station met programmabestanden CT4 in de hoofdmap van het programma. Nadat u preinst.exe hebt uitgevoerd met deze optie, kopieert u handmatig de &lt; *SiteCode*>. CT4-bestand naar de map...\Inboxes\hman.box voor de bovenliggende site (niet hman.box\pubkey).  

**/KEYFORCHILD**: gebruik deze optie op een site om de openbare sleutel van de site te verdelen naar een onderliggende site.  

De/keyforparent-optie plaatst de openbare sleutel van de site in het bestand &lt; *SiteCode*>. Station met programmabestanden CT5 in de hoofdmap van het programma. Nadat u preinst.exe hebt uitgevoerd met deze optie, kopieert u handmatig de &lt; *SiteCode*>. CT5-bestand naar de map...\Inboxes\hman.box voor de onderliggende site (niet hman.box\pubkey).  

**/CHILDKEYS**: u kunt deze optie gebruiken op de onderliggende sites van een site die u herstelt. Gebruik deze optie om publieke sleutels te verdelen van meerdere onderliggende sites naar de herstellende site.  

De childkeys-optie plaatst de sleutel van de site waar u de optie uitvoert, en alle van de onderliggende sites van openbare sleutels in het bestand &lt; *SiteCode*>. CT6.  

Nadat u preinst.exe hebt uitgevoerd met deze optie, kopieert u handmatig de &lt; *SiteCode*>. CT6-bestand naar de herstellende site...\Inboxes\hman.box map (niet hman.box\pubkey).  

**/PARENTKEYS**: u kunt deze optie gebruiken op de bovenliggende sites van een site die u herstelt. Gebruik deze optie om publieke sleutels te verdelen van meerdere bovenliggende sites naar de herstellende site.  

De parentkeys-optie plaatst de sleutel van de site waar u de optie uitvoert, en de sleutels van elke bovenliggende site van die site in het bestand &lt;SiteCode\>. CT7.  

Nadat u preinst.exe hebt uitgevoerd met deze optie, kopieert u handmatig de &lt; *SiteCode*>. CT7-bestand naar de herstellende site...\Inboxes\hman.box map (niet hman.box\pubkey).  

##  <a name="BKMK_ManuallyExchangeKeys"></a>Handmatig uitwisselen van openbare sleutels tussen Sites  
Standaard de **verzoek om beveiligde sleuteluitwisseling** optie is ingeschakeld voor Configuration Manager-sites. Wanneer uitwisseling van een beveiligde sleutel vereist is, zijn er twee situaties waarin u handmatig de initiële uitwisseling van de openbare sleutel tussen sites moet uitvoeren:  

-   Indien het Active Directory-schema niet uitgebreid voor Configuration Manager  

-   Configuration Manager-sites die geen sitegegevens publiceren naar Active Directory  

U kunt het hiërarchieonderhoud-hulpprogramma gebruiken om de openbare sleutels te exporteren voor elke site. Eenmaal ze geëxporteerd werden, moet u handmatig de sleutels tussen de sites uitwisselen.  

> [!NOTE]  
>  Nadat de openbare sleutels handmatig zijn uitgewisseld, kunt u het logboekbestand **hman.log** controleren, dat siteconfiguratiewijzigingen registreert en sitegegevens publiceert naar Active Directory Domain Services, op de bovenliggende siteserver om te controleren of de primaire site de nieuwe openbare sleutel heeft verwerkt.  

#### <a name="to-manually-transfer-the-child-site-public-key-to-the-parent-site"></a>Handmatig de openbare sleutel van de onderliggende site overdragen naar de bovenliggende site  

1.  Zorg dat u bent aangemeld bij de onderliggende site, open een opdrachtregel en navigeer naar de locatie van **Preinst.exe**.  

2.  Typ het volgende als u wilt de openbare sleutel van de onderliggende site exporteren: **Preinst/keyforparent**  

3.  De/keyforparent-optie plaatst de openbare sleutel van de onderliggende site in de  **&lt;sitecode\>. CT4** bestand in de hoofdmap van het systeemstation.  

4.  Verplaats de  **&lt;sitecode\>. CT4** bestand naar de bovenliggende site  **&lt;installatiemap\>\inboxes\hman.box** map.  

#### <a name="to-manually-transfer-the-parent-site-public-key-to-the-child-site"></a>Handmatig de openbare sleutel van de bovenliggende site overdragen naar de onderliggende site  

1.  Zorg dat u bent aangemeld bij de bovenliggende site, open een opdrachtregel en navigeer naar de locatie van **Preinst.exe**.  

2.  Typ het volgende om de openbare sleutel van de bovenliggende site te exporteren: **Preinst / keyforchild**.  

3.  De/keyforparent-optie plaatst de openbare sleutel van de bovenliggende site in de  **&lt;sitecode\>. CT5** bestand in de hoofdmap van het systeemstation.  

4.  Verplaats de  **&lt;sitecode\>. CT5** van het bestand in de  **&lt;installatiemap\>\inboxes\hman.box** map op de onderliggende site.  
