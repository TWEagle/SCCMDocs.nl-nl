---
title: Instellen van uw abonnement met dan | System Center Configuration Manager
description: In dit onderwerp biedt gedetailleerde informatie over hoe zoek apparaat bedreiging beveiliging configureren.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: b777140c753e709f4048a30e63d8ae730d3e8723
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-your-subscription-for--lookout-device-threat-protection"></a>Instellen van uw abonnement voor dan apparaat bedreiging beveiliging

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Uw abonnement gereed is voor de beveiligingsservice voor dan apparaat bedreiging, dan ondersteuning ophalen (enterprisesupport@lookout.com) moet de volgende informatie over uw abonnement Azure Active Directory (Azure AD). Uw tenant dan Mobility Endpoint Security worden gekoppeld aan uw abonnement Azure AD altijd integreren met Intune. 

* **Azure AD-Tenant-ID**
* **Object-ID van Azure AD-groep** voor **volledige** altijd toegang tot de console
* **Object-ID van Azure AD-groep** voor **beperkte** altijd toegang tot de console (optioneel)

> [!IMPORTANT]
> Een bestaande altijd mobiele Endpoint Security tenant die nog niet is gekoppeld aan uw Azure AD-tenant kan niet worden gebruikt voor de integratie met Azure AD en Intune. Neem contact op met ondersteuning voor het maken van een nieuwe tenant dan mobiele Endpoint Security altijd. Gebruik de nieuwe tenant om vrij te geven uw Azure AD-gebruikers.

Gebruik de volgende sectie voor het verzamelen van informatie die u nodig hebt om aan te geven tot het ondersteuningsteam altijd.  

## <a name="get-your-azure-ad-information"></a>Uw Azure AD-informatie
### <a name="azure-ad-tenant-id"></a>Azure AD-tenant-ID
Meld u aan bij de [Azure AD-beheerportal](https://manage.windowsazure.com) en selecteert u uw abonnement. 

![Schermafbeelding van de Azure AD-pagina met de naam van de tenant](media/aad_tenant_name.png) als u de naam van uw abonnement, de resulterende URL bevat de abonnement-ID.  Als u eventuele problemen die uw abonnement-ID vinden, raadpleegt u dit [Microsoft ondersteuning-artikel](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) voor tips voor het zoeken van uw abonnement-ID.   
### <a name="azure-ad-group-id"></a>Azure AD-groep-ID
De console dan ondersteunt 2 toegangsniveaus:  
* **Volledige toegang:** De Azure AD-beheerder kan een groep maken voor gebruikers die hebben volledige toegang en optioneel een groep maken voor gebruikers met beperkte toegang.  Alleen gebruikers in deze groepen kunt u zich kunt aanmelden bij de **altijd console**.
* **Beperkte toegang:** De gebruikers in deze groep hebben geen toegang tot verschillende configuratie en registratie van modules van de console altijd gerelateerd en alleen-lezen toegang hebben tot de **beveiligingsbeleid** module van de console altijd.  

Voor meer informatie over de machtigingen lezen [in dit artikel](https://personal.support.lookout.com/hc/en-us/articles/114094105653) op de website altijd.

De **groep Object-ID** is op de **eigenschappen** pagina van de groep in de **Azure AD-beheerconsole**.

![Schermafdruk van de eigenschappenpagina met groeps-id-veld gemarkeerd](media/aad_group_object_id.png)

Als u deze informatie hebt verzameld, contact op met ondersteuning voor altijd (e-mailadres: enterprisesupport@lookout.com).

Zoek ondersteuning zal werken met de primaire contactpersoon om vrij te geven van uw abonnement en uw account dan Enterprise worden gemaakt met behulp van de gegevens die u hebt verzameld.


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>Uw abonnement met altijd apparaat bedreiging beveiliging configureren
### <a name="step-1-set-up-your-device-threat-protection"></a>Stap 1: De beveiliging van uw apparaat bedreiging instellen
Wanneer dan ondersteuning uw dan Enterprise-mailaccount maakt, kunt u zich aanmelden bij de console altijd.   Een e-mailbericht van altijd verzonden naar de primaire contactpersoon voor uw bedrijf met een koppeling naar de aanmeldings-url: https://aad.lookout.com/les?action=consent

U moet een gebruikersaccount met de Azure AD-rol van globale beheerder gebruiken wanneer u eerst bij de console altijd aanmelden omdat altijd vereist dat deze gegevens naar uw Azure AD-tenant te registreren.   Volgende melden zich aan nodig de gebruiker dit niveau van Azure AD-bevoegdheden niet.  In deze eerste aanmelding, wordt een pagina toestemming weergegeven. Kies **accepteren** om de inschrijving te voltooien.

![Schermafdruk van de eerste pagina van de aanmelding tijd van de console altijd](media/lookout-initial-login.png)

Nadat u hebt geaccepteerd en toestemming gegeven, wordt u omgeleid naar de Console altijd. Volgende aanmeldingen nadat de eerste registratie kan worden gedaan via de URL: https://aad.lookout.com

Zie de [probleemoplossing artikel]() als u problemen met aanmelden.

De volgende stappen wordt beschreven hoe de taken die u doen moet om te voltooien altijd ingesteld binnen de [altijd Console](https://aad.lookout.com).

### <a name="step-2-configure-the-intune-connector"></a>Stap 2: De Intune-connector configureren

1.  In de console dan van de **System** module, kies de **Connectors** tabblad en selecteer **Intune**.

  ![schermopname van de console altijd met het tabblad connectors openen en de Intune-optie gemarkeerd](media/lookout-setup-intune-connector.png)

2.  In de optie verbinding instellingen configureert u de frequentie van heartbeat in minuten.  Uw Intune-connector is nu gereed.  

  ![Schermafdruk van het tabblad verbinding instellingen met het weergeven van heartbeat-frequentie geconfigureerd](media/lookout-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>Stap 3: Inschrijving van groepen configureren
Op de **inschrijving Management** optie, definieert u een set gebruikers wiens apparaten moeten worden ingeschreven bij altijd. De aanbevolen procedure is om te beginnen met een kleine groep gebruikers om te testen en meer vertrouwd raken met de werking van de integratie.  Als u tevreden met de testresultaten bent, kunt u de inschrijving uitbreiden op extra groepen van gebruikers.

Om te beginnen met inschrijvingen groepen, definieert u eerst een Azure AD-beveiligingsgroep die een goede eerste set van gebruikers om te schrijven in dan apparaat bedreiging beveiliging. Zodra u de groep hebt gemaakt in Azure, AD, in de Console dan gaat u naar de **inschrijving Management** optie en voeg de beveiligingsgroep Azure AD **weergavenamen voor** voor de inschrijving.

Wanneer een gebruiker zich in een inschrijvingsgroep, zijn hun apparaten die worden geïdentificeerd en ondersteund in Azure AD geregistreerd en in aanmerking komen voor activering in dan apparaat bedreiging beveiliging.  De eerste keer dat ze altijd werk app op hun apparaat ondersteunde openen wordt het apparaat geactiveerd in dan.

![Schermafbeelding van de Intune-connector inschrijving pagina](media/lookout-enrollment.png)

De aanbevolen procedure is met de standaardwaarde (5 minuten) voor de toename van de tijd om te controleren op nieuwe apparaten.

>[!IMPORTANT]
> De weergavenaam is hoofdlettergevoelig.  Gebruik de **weergavenaam** zoals de in de **eigenschappen** pagina van de beveiligingsgroep in de Azure-portal. Opmerking in de afbeelding hieronder die de **eigenschappen** pagina van de beveiligingsgroep, de weergavenaam is kamelen geval.  De titel echter wordt weergegeven in alle kleine letters en mag niet worden gebruikt in de console altijd in te voeren.
>![Schermafdruk van het Azure-portal, Azure Active Directory-service, eigenschappenpagina](media/aad-group-display-name.png)

De huidige versie heeft de volgende beperkingen:  
* Er is geen validatie beschikbaar voor namen voor de weergave.  Controleer of u de waarde in de **WEERGAVENAAM** veld weergegeven in de Azure-portal voor de beveiligingsgroep Azure AD.
* Het maken van groepen binnen groepen wordt momenteel niet ondersteund.  Azure AD-beveiligingsgroepen opgegeven mag alleen gebruikers en geen geneste groepen bevatten.


### <a name="step-4-configure-state-sync"></a>Stap 4: Status synchronisatie configureren
In de **status synchronisatie** optie, geeft u het type gegevens dat moet worden verzonden naar Intune.  U moet op dit moment kunnen inschakelen Apparaatstatus en bedreiging status voor de integratie Intune altijd goed te laten werken.  Deze zijn standaard ingeschakeld.
### <a name="step-5-configure-error-report-email-recipient-information"></a>Stap 5: Rapport e geadresseerde foutgegevens configureren
In de **fout Management** optie, de foutrapporten ontvangt e-mailadres invoeren.

![Schermafdruk van de Intune-connector foutpagina management](media/lookout-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>Stap 6. Instellingen voor de inschrijving configureren
In de **System** module op de **Connectors** pagina, geeft u het aantal dagen voordat een apparaat wordt beschouwd als de verbinding verbroken.  Niet-verbonden apparaten als niet-compatibel worden beschouwd en wordt toegang krijgen tot uw bedrijfstoepassingen op basis van de SCCM-beleidsregels voor voorwaardelijke toegang. U kunt waarden tussen 1 en 90 dagen opgeven.

![](media/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>Stap 7: E-mailmeldingen configureren
Als u ontvangen van e-mailwaarschuwingen voor bedreigingen wilt, aanmelden bij de [altijd console](https://aad.lookout.com) met het gebruikersaccount dat de meldingen moet ontvangen. Op de **voorkeuren** tabblad van het **System** module, kies de gewenste meldingen en stel deze op **ON**. Sla de wijzigingen.

![Schermafdruk van de pagina Voorkeuren met gebruikersaccount weergegeven](media/lookout-email-notifications.png) als u niet meer ontvangen van e-mailmeldingen wilt, stelt u de meldingen op **OFF** en sla de wijzigingen.
### <a name="step-8-configure-threat-classification"></a>Stap 8: Bedreiging classificatie configureren
Zoek apparaat bedreiging beveiliging deelt mobiele bedreigingen van verschillende typen. De [altijd bedreiging classificaties](http://personal.support.lookout.com/hc/en-us/articles/114094130693) standaard risico niveaus ermee hebben gekoppeld. Dit kunnen worden gewijzigd op elk gewenst moment in suite vereisten van uw bedrijf.

![Schermafdruk van de pagina beleid met dreiging en classificaties](media/lookout-threat-classification.png)

>[!IMPORTANT]
> De risico's die zijn opgegeven dat hier zijn een belangrijk aspect van apparaat bedreiging beveiliging, omdat de Intune-integratie apparaatcompatibiliteit volgens deze niveaus risico tijdens runtime berekent. Met andere woorden, de Intune-beheerder stelt een regel in het beleid voor de identificatie van een apparaat als niet-compatibel als het apparaat een actieve dreiging met een minimum heeft van niveau: hoog, Gemiddeld of laag. Het beleid bedreiging classificatie dan apparaat bedreiging beveiliging stations rechtstreeks de berekening van de naleving van apparaten in Intune.

## <a name="watching-enrollment"></a>Inschrijving wordt gevolgd
Nadat de installatie voltooid is, start dan apparaat bedreiging beveiliging voor het pollen van Azure AD voor apparaten die met de opgegeven inschrijving groepen overeenkomen.  U vindt informatie over de apparaten die zijn geregistreerd in de module apparaten.  De initiële status van apparaten wordt weergegeven als in behandeling.  Het apparaat wordt gewijzigd nadat altijd werk app is geïnstalleerd, geopend en wordt geactiveerd op het apparaat.  Zie voor meer informatie over het ophalen van altijd voor werk app naar het apparaat gepusht de [configureren en dan implementeert voor zakelijke apps](configure-and-deploy-lookout-for-work-apps.md) onderwerp.
## <a name="next-steps"></a>Volgende stappen
[Zoek MTP verbinding Intune inschakelen](enable-lookout-connection-in-intune.md)

