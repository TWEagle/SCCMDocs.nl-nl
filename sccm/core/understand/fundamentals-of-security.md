---
title: Basisprincipes van beveiliging | Microsoft Docs
description: Meer informatie over de lagen van de beveiliging voor System Center Configuration Manager.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 035b7f73-8b78-4ed1-835e-a31f9a5c4a02
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: df3198885259b1db4a1aadee0db6512a1a2d4911
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="fundamentals-of-security-for-system-center-configuration-manager"></a>Basisprincipes van beveiliging voor System Center Configuration Manager.

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Beveiliging voor System Center Configuration Manager bestaat uit meerdere lagen. De eerste laag wordt geleverd door Windows-beveiligingsfuncties voor zowel het besturingssysteem en het netwerk en omvat:  

-   Bestand delen voor bestandsoverdracht tussen Configuration Manager-onderdelen.  

-   Toegangsbeheerlijsten (ACL's) voor het beveiligde bestanden en registersleutels.  

-   Internet Protocol Security (IPsec) om u te helpen beveiligde communicatie.  

-   Groepsbeleid instellen van beveiligingsbeleid.  

-   Distributed Component Object Model (DCOM) machtigingen voor gedistribueerde toepassingen, zoals de Configuration Manager-console.  

-   Active Directory Domain Services voor het opslaan van beveiligings-principals.  

-   Windows-accountbeveiliging, inclusief bepaalde groepen die zijn gemaakt tijdens de installatie van Configuration Manager.  

Vervolgens zorgt extra beveiligingsonderdelen, zoals firewalls en inbraakdetectie, voor beveiliging voor de hele omgeving. Certificaten die door de bedrijfstak standaard openbare-sleutelinfrastructuur (PKI)-implementaties te bieden voor authenticatie, ondertekening en versleuteling.  

Naast de beveiliging van de Windows server en de netwerkinfrastructuur, controleert Configuration Manager de toegang tot de Configuration Manager-console en de bijbehorende bronnen op verschillende manieren. Standaard beschikken alleen lokale beheerders over rechten op de bestanden en registersleutels die nodig zijn voor het uitvoeren van de Configuration Manager-console op computers waarop deze is geïnstalleerd.  

De volgende beveiligingslaag is gebaseerd op toegang via WMI (Windows Management Instrumentation), in het bijzonder de SMS-provider. De SMS-Provider is een Configuration Manager-onderdeel waarmee een gebruiker toegang krijgt om op te vragen van de sitedatabase voor meer informatie. Toegang tot de provider is standaard beperkt tot leden van de lokale groep SMS Admins. Deze groep bevat eerst alleen de gebruiker die Configuration Manager hebt geïnstalleerd. Als u andere account wilt machtigen voor de CIM-opslagplaats (CIM: Common Information Model) en de SMS-provider, voegt u de andere accounts toe aan de groep SMS Admins.  

De laatste beveiligingslaag is gebaseerd op machtigingen voor objecten in de sitedatabase. Standaard beheren het lokale systeemaccount en de gebruikersaccount die u gebruikt voor het installeren van Configuration Manager alle objecten in de database. U kunt verlenen en beperken van machtigingen aan extra gebruikers met beheerdersrechten in de Configuration Manager-console met behulp van op rollen gebaseerd beheer.  



## <a name="role-based-administration"></a>Op rollen gebaseerd beheer  
 Configuration Manager gebruikt op rollen gebaseerd beheer om objecten te beveiligen zoals verzamelingen, implementaties en sites. Dit beheermodel definieert en beheert centraal instellingen voor beveiligingstoegang van alle sites in de hiërarchie en site-instellingen. Beveiligingsrollen zijn toegewezen aan gebruikers met beheerdersrechten en groepsmachtigingen. De machtigingen zijn verbonden met andere Configuration Manager-objecttypen, zoals de machtigingen die worden gebruikt voor het maken of wijzigen van clientinstellingen. Beveiligingsbereiken de groeperen specifieke exemplaren van objecten die een gebruiker met beheerdersrechten moeten worden beheerd, zoals een toepassing die Microsoft Office installeert. De combinatie van beveiligingsrollen, beveiligingsbereiken en verzamelingen definiëren de objecten die een gebruiker met beheerdersrechten kan weergeven en beheren. Configuration Manager installeert sommige standaardbeveiligingsrollen voor veelvoorkomende beheertaken. Maar kunt u uw eigen beveiligingsrollen ter ondersteuning van uw specifieke bedrijfsvereisten.  

 Zie voor meer informatie [beheer op basis van rollen voor System Center Configuration Manager configureren](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="securing-client-endpoints"></a>Clienteindpunten beveiligen  
 Communicatie van clients met sitesysteemrollen wordt beveiligd door de zelfondertekende certificaten, of met behulp van PKI-certificaten. U moet een PKI-certificaat gebruikt voor de computerclients die door Configuration Manager is gedetecteerd op Internet, en voor clients van mobiele apparaten. Het PKI-certificaat maakt gebruik van HTTPS voor het beveiligen van eindpunten voor de client. De sitesysteemrollen waarmee clients zijn verbonden, kunnen voor HTTPS- of HTTP-clientcommunicatie worden geconfigureerd. Clientcomputers communiceren altijd met behulp van de meest beveiligde methode die beschikbaar is. Clientcomputers vallen alleen terug op de minder veilige communicatiemiddel HTTP op het intranet gebruiken als u beschikt over sitesystemen beschikt die HTTP-communicatie toestaan.  

 Zie voor meer informatie [cryptografische besturingselementen technische documentatie voor System Center Configuration Manager](../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

## <a name="configuration-manager-accounts-and-groups"></a>Configuration Manager-accounts en -groepen  
 Configuration Manager gebruikt het lokale systeemaccount voor de meeste sitebewerkingen. Bepaalde beheertaken uitvoeren moet u mogelijk maken en beheren van extra accounts. Verschillende standaardgroepen en SQL Server-rollen worden gemaakt tijdens de installatie. Mogelijk moet handmatig computer- of gebruikersaccounts toevoegen aan de volgende standaardgroepen en SQL Server-rollen.  

 Zie [Accounts die worden gebruikt System Center Configuration Manager](../../core/plan-design/hierarchy/accounts.md) voor meer informatie.  

## <a name="privacy"></a>Privacy  
 Bedrijfsbeheerproducten bieden veel voordelen omdat ze u in staat stellen tal van clients effectief te beheren. Houd er echter wel rekening mee dat deze software van invloed kan zijn op de privacy van gebruikers in uw organisatie. System Center Configuration Manager bevat veel hulpprogramma's voor het verzamelen van gegevens en apparaten te controleren. Sommige hulpprogramma's mogelijk privacyproblemen verhogen.  

 Wanneer u de Configuration Manager-client installeert, zijn bijvoorbeeld veel beheerinstellingen standaard ingeschakeld. Dit zorgt ervoor dat de clientsoftware informatie naar de Configuration Manager-site te verzenden. Clientinformatie wordt opgeslagen in de Configuration Manager-database en de informatie wordt niet naar Microsoft verzonden. Bedenk wat uw privacyvereisten voordat u System Center Configuration Manager implementeert.  
