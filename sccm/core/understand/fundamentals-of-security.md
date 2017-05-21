---
title: Basisprincipes van beveiliging | Microsoft-documenten
description: Meer informatie over de lagen van beveiliging voor System Center Configuration Manager.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 035b7f73-8b78-4ed1-835e-a31f9a5c4a02
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d56c8a76e4770336d4a2ab519e776e48fec8ebcd
ms.openlocfilehash: df3198885259b1db4a1aadee0db6512a1a2d4911
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-security-for-system-center-configuration-manager"></a>Basisprincipes van beveiliging voor System Center Configuration Manager.

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beveiliging voor System Center Configuration Manager bestaat uit meerdere lagen. De eerste laag wordt verstrekt door de Windows-beveiligingsfuncties voor zowel het besturingssysteem en het netwerk en omvat:  

-   Bestanden delen voor bestandsoverdracht tussen Configuration Manager-onderdelen.  

-   Toegangsbeheerlijsten (ACLs) om bestanden en registersleutels veilig te.  

-   IP-beveiligingsbeleid (IPsec) voor communicatie te beveiligen.  

-   Groepsbeleid beveiligingsbeleid instellen.  

-   Distributed Component Object Model (DCOM) machtigingen voor gedistribueerde toepassingen, zoals de Configuration Manager-console.  

-   Active Directory Domain Services voor het opslaan van beveiligings-principals.  

-   Windows-accountbeveiliging, inclusief bepaalde groepen die zijn gemaakt tijdens de installatie van Configuration Manager.  

Onderdelen voor extra beveiliging, zoals firewalls en detecteren van indringers helpen vervolgens verdediging opgeven voor de hele omgeving. Certificaten uitgegeven door bedrijfstak standaard openbare-sleutelinfrastructuur (PKI)-implementaties voorzien verificatie, ondertekening en versleuteling.  

Naast de beveiliging van de Windows server en de netwerkinfrastructuur, controleert Configuration Manager de toegang tot de Configuration Manager-console en de daarbij behorende bronnen op verschillende manieren. Standaard beschikken alleen lokale beheerders over rechten op de bestanden en registersleutels die nodig zijn voor het uitvoeren van de Configuration Manager-console op computers waarop deze is geïnstalleerd.  

De volgende beveiligingslaag is gebaseerd op toegang via WMI (Windows Management Instrumentation), in het bijzonder de SMS-provider. De SMS-Provider is een onderdeel van Configuration Manager waarmee een gebruikerstoegang om op te vragen van de sitedatabase voor meer informatie. Toegang tot de provider is standaard beperkt tot leden van de lokale groep SMS Admins. Deze groep bevat eerst alleen de gebruiker die Configuration Manager geïnstalleerd. Als u andere account wilt machtigen voor de CIM-opslagplaats (CIM: Common Information Model) en de SMS-provider, voegt u de andere accounts toe aan de groep SMS Admins.  

De laatste beveiligingslaag is gebaseerd op machtigingen voor objecten in de sitedatabase. Standaard beheren het lokale systeemaccount en de gebruikersaccount die u gebruikt voor het installeren van Configuration Manager alle objecten in de database. U kunt machtigingen verlenen en inperken aan extra gebruikers met beheerdersrechten in de Configuration Manager-console door op rollen gebaseerd beheer.  



## <a name="role-based-administration"></a>Op rollen gebaseerd beheer  
 Configuration Manager maakt gebruik van op rollen gebaseerd beheer om objecten te beveiligen als verzamelingen, implementatie en sites. Dit beheermodel definieert en beheert centraal instellingen voor beveiligingstoegang van alle sites in de hiërarchie en site-instellingen. Beveiligingsrollen zijn toegewezen aan gebruikers met beheerdersrechten en groepsmachtigingen. De machtigingen zijn verbonden met andere Configuration Manager-objecttypen, zoals de machtigingen die worden gebruikt voor het maken of wijzigen van de clientinstellingen. Beveiligingsbereiken de groeperen specifieke exemplaren van objecten waarover een gebruiker met beheerdersrechten te beheren, zoals een toepassing die door Microsoft Office worden geïnstalleerd. De combinatie van beveiligingsrollen, beveiligingsbereiken en verzamelingen definiëren de objecten die een gebruiker met beheerdersrechten kan weergeven en beheren. Configuration Manager installeert enkele standaardbeveiligingsrollen voor typische beheertaken. Maar u kunt uw eigen beveiligingsrollen maken ter ondersteuning van uw specifieke bedrijfsvereisten.  

 Zie voor meer informatie [op rollen gebaseerd beheer voor System Center Configuration Manager configureert](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="securing-client-endpoints"></a>Clienteindpunten beveiligen  
 Communicatie van clients met sitesysteemrollen wordt beveiligd door het gebruik van zelfondertekende certificaten of met behulp van PKI-certificaten. U moet een PKI-certificaat gebruiken voor computerclients die Configuration Manager is gedetecteerd op het Internet en voor clients van mobiele apparaten. De PKI-certificaat maakt gebruik van HTTPS eindpunten voor de clientcomputers beveiligt. De sitesysteemrollen waarmee clients zijn verbonden, kunnen voor HTTPS- of HTTP-clientcommunicatie worden geconfigureerd. Clientcomputers communiceren altijd op de veiligste manier die beschikbaar is. Clientcomputers vallen alleen terug op het gebruik van de minder veilige communicatiemiddel HTTP op het intranet als u over sitesystemen beschikt die HTTP-communicatie toestaan.  

 Zie voor meer informatie [cryptografische besturingselementen technische naslaginformatie voor System Center Configuration Manager](../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

## <a name="configuration-manager-accounts-and-groups"></a>Configuration Manager-accounts en -groepen  
 Configuration Manager maakt gebruik van het lokale systeemaccount voor de meeste sitebewerkingen. Bepaalde beheertaken moet u mogelijk te maken en beheren van extra accounts. Verschillende standaardgroepen en SQL Server-rollen worden gemaakt tijdens de installatie. Mogelijk moet u handmatig computer- of gebruikersaccounts toevoegen aan de standaardgroepen en SQL Server.  

 Zie [Accounts die worden gebruikt System Center Configuration Manager](../../core/plan-design/hierarchy/accounts.md) voor meer informatie.  

## <a name="privacy"></a>Privacy  
 Bedrijfsbeheerproducten bieden veel voordelen omdat ze u in staat stellen tal van clients effectief te beheren. Houd er echter wel rekening mee dat deze software van invloed kan zijn op de privacy van gebruikers in uw organisatie. System Center Configuration Manager bevat veel hulpprogramma's voor het verzamelen van gegevens en bewaken van apparaten. Sommige hulpmiddelen voor privacyoverwegingen mogelijk verhogen.  

 Wanneer u de Configuration Manager-client installeert, zijn bijvoorbeeld veel beheerinstellingen standaard ingeschakeld. Dit zorgt ervoor dat de clientsoftware informatie te verzenden naar de Configuration Manager-site. Clientinformatie wordt opgeslagen in de Configuration Manager-database en de informatie wordt niet naar Microsoft verzonden. Bedenk wat uw privacyvereisten voordat u System Center Configuration Manager implementeert.  

