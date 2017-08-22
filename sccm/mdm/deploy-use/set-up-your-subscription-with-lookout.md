---
title: Instellen van uw abonnement met Lookout | System Center Configuration Manager
description: In dit onderwerp bevat informatie over het configureren van Lookout device threat protection.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: b777140c753e709f4048a30e63d8ae730d3e8723
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="set-up-your-subscription-for--lookout-device-threat-protection"></a>Instellen van uw abonnement voor Lookout device threat protection

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Om uw abonnement gereed is voor de Lookout ondersteuning van de Lookout device threat protection service (enterprisesupport@lookout.com) moet de volgende informatie over uw abonnement Azure Active Directory (Azure AD). Uw tenant Lookout Mobility Endpoint Security worden gekoppeld aan uw abonnement Azure AD Lookout integreren met Intune. 

* **Azure AD-Tenant-ID**
* **Object-ID van Azure AD-groep** voor **volledige** Lookout console-toegang
* **Object-ID van Azure AD-groep** voor **beperkte** Lookout toegang tot de console (optioneel)

> [!IMPORTANT]
> Een bestaande Lookout Mobile Endpoint Security-tenant die nog niet is gekoppeld aan uw Azure AD-tenant kan niet worden gebruikt voor de integratie met Azure AD en Intune. Neem contact op met Lookout ondersteuning voor het maken van een nieuwe Lookout Mobile Endpoint Security-tenant. Gebruik de nieuwe tenant om vrij te geven van uw Azure AD-gebruikers.

Gebruik de volgende sectie voor het verzamelen van informatie die u nodig hebt om te geven tot het ondersteuningsteam Lookout.  

## <a name="get-your-azure-ad-information"></a>Uw Azure AD-gegevens ophalen
### <a name="azure-ad-tenant-id"></a>Azure AD-tenant-ID
Aanmelden bij de [Azure AD-beheerportal](https://manage.windowsazure.com) en uw abonnement te selecteren. 

![Schermafbeelding van de Azure AD-pagina met de naam van de tenant](media/aad_tenant_name.png) wanneer u de naam van uw abonnement kiest, de resulterende URL bevat de abonnement-ID.  Als u eventuele problemen die uw abonnements-ID vinden, raadpleegt u dit [Microsoft support-artikel](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US) voor tips voor het zoeken van uw abonnement-ID.   
### <a name="azure-ad-group-id"></a>Azure AD-groep-ID
De console Lookout ondersteunt 2 toegangsniveaus:  
* **Volledige toegang:** De Azure AD-beheerder kan een groep maken voor gebruikers die hebben volledige toegang en eventueel een groep maken voor gebruikers met beperkte toegang.  Alleen gebruikers in deze groepen kunt u zich aanmelden bij de **Lookout console**.
* **Beperkte toegang:** De gebruikers in deze groep hebben geen toegang tot verschillende configuratie en inschrijving gerelateerde modules van de console Lookout en alleen-lezen toegang hebben tot de **beveiligingsbeleid** module van de console Lookout.  

Voor meer informatie over de machtigingen lezen [in dit artikel](https://personal.support.lookout.com/hc/en-us/articles/114094105653) op de website Lookout.

De **groep Object-ID** is op de **eigenschappen** pagina van de groep in de **Azure AD-beheerconsole**.

![Schermafbeelding van de eigenschappenpagina met groeps-id-veld gemarkeerd](media/aad_group_object_id.png)

Zodra u deze informatie hebt verzameld, contact op met ondersteuning voor Lookout (e-mailadres: enterprisesupport@lookout.com).

Lookout ondersteuning zal werken met uw primaire contactpersoon om vrij te geven van uw abonnement en uw account Lookout Enterprise worden gemaakt met de informatie die u hebt verzameld.


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>Configureer uw abonnement met Lookout device threat protection
### <a name="step-1-set-up-your-device-threat-protection"></a>Stap 1: Instellen van uw apparaat threat protection
Nadat Lookout ondersteuning uw Lookout Enterprise-account maakt, kunt u zich aanmeldt bij de Lookout-console.   Een e-mailbericht van Lookout is verzonden naar de primaire contactpersoon voor uw bedrijf met een koppeling naar de aanmeldings-url: https://aad.lookout.com/les?action=consent

Wanneer u zich eerst de console Lookout omdat Lookout deze informatie om te registreren van uw Azure AD-tenant vereist, moet u een gebruikersaccount met de Azure AD-rol van globale beheerder.   Volgende aanmelding wordt niet vereist dat de gebruiker dit niveau van Azure AD-bevoegdheden hebben.  In deze eerste aanmelding wordt een pagina toestemming weergegeven. Kies **accepteren** om de inschrijving te voltooien.

![Schermafbeelding van de eerste keer aanmeldingspagina van de console Lookout](media/lookout-initial-login.png)

Zodra u hebt geaccepteerd en ingestemd, wordt u omgeleid naar de Console Lookout. Toekomstige aanmeldingen nadat de initiële registratie kan worden gedaan met behulp van de URL: https://aad.lookout.com

Zie de [probleemoplossing artikel]() als u problemen met aanmelden.

De volgende stappen wordt uitgelegd taken die u uitvoeren moet voor het voltooien van de Lookout ingesteld binnen de [Lookout Console](https://aad.lookout.com).

### <a name="step-2-configure-the-intune-connector"></a>Stap 2: De Intune-connector configureren

1.  In de console Lookout van de **System** -module, kies de **Connectors** tabblad en selecteer **Intune**.

  ![Schermafbeelding van de console op het tabblad connectors open Lookout en Intune optie gemarkeerd](media/lookout-setup-intune-connector.png)

2.  In de verbindingsoptie-instellingen configureert u de frequentie van heartbeat in minuten.  Uw Intune-connector is nu klaar.  

  ![schermopname van het tabblad verbinding-instellingen met het weergeven van de frequentie van de heartbeat is geconfigureerd](media/lookout-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>Stap 3: Inschrijving van groepen configureren
Op de **inschrijving Management** optie, het definiëren van een set gebruikers wiens apparaten moeten worden geregistreerd bij Lookout. De aanbevolen procedure is om te beginnen met een kleine groep gebruikers om te testen en vertrouwd raken met de werking van de integratie.  Wanneer u tevreden met de testresultaten bent, kunt u de inschrijving uitbreiden op extra groepen van gebruikers.

Om te beginnen met groepen van inschrijvingen moet u eerst een Azure AD-beveiligingsgroep die een goede eerste set van gebruikers om te schrijven in Lookout device threat protection definiëren. Zodra u de groep gemaakt in Azure hebt, AD, in de Console Lookout gaat u naar de **inschrijving Management** optie en de Azure AD-beveiligingsgroep toevoegen **weergavenamen** voor inschrijving.

Wanneer een gebruiker in een inschrijvingsgroep voor is, wordt geen van hun apparaten die zijn geïdentificeerd en worden ondersteund in Azure AD zijn ingeschreven en in aanmerking komen voor activering in Lookout device threat protection.  De eerste keer dat ze de Lookout for Work-app op hun ondersteund apparaat opent u wordt het apparaat geactiveerd in Lookout.

![Schermafbeelding van de Intune-connector inschrijving pagina](media/lookout-enrollment.png)

De aanbevolen procedure is het gebruik van de standaardwaarde (5 minuten) voor de tijdsperiode om te controleren op nieuwe apparaten.

>[!IMPORTANT]
> De weergegeven naam is hoofdlettergevoelig.  Gebruik de **weergavenaam** zoals de in de **eigenschappen** pagina van de beveiligingsgroep in de Azure-portal. Let op de afbeelding hieronder die de **eigenschappen** pagina van de beveiligingsgroep, de weergavenaam is kamelen.  De titel wordt weergegeven in alle kleine letters echter en mag niet worden gebruikt in de console Lookout in te voeren.
>![schermopname van het Azure-portal, Azure Active Directory-service, de eigenschappenpagina](media/aad-group-display-name.png)

De huidige release heeft de volgende beperkingen:  
* Er is geen validatie voor namen voor de weergave.  Controleer of u de waarde in de **WEERGAVENAAM** veld wordt weergegeven in de Azure-portal voor de Azure AD-beveiligingsgroep.
* Maken van groepen in groepen wordt momenteel niet ondersteund.  Azure AD-beveiligingsgroepen opgegeven mag alleen gebruikers en geen geneste groepen bevatten.


### <a name="step-4-configure-state-sync"></a>Stap 4: Status synchronisatie configureren
In de **status synchronisatie** optie, geeft u het type gegevens die moeten worden verzonden naar Intune.  U moet op dit moment inschakelen Apparaatstatus zowel threat status om de Lookout Intune-integratie juist werkt.  Deze zijn standaard ingeschakeld.
### <a name="step-5-configure-error-report-email-recipient-information"></a>Stap 5: Fout rapport e ontvangersinformatie configureren
In de **fout Management** optie, voert u het e-mailadres dat de foutrapporten moet ontvangen.

![Schermafbeelding van de Intune-connector foutpagina management](media/lookout-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>Stap 6. Inschrijvingsinstellingen configureren
In de **System** module op de **Connectors** pagina, geeft u het aantal dagen voordat een apparaat wordt beschouwd als de verbinding verbroken.  Niet-verbonden apparaten beschouwd als niet-compatibel en toegang tot de bedrijfstoepassingen van uw op basis van de SCCM-beleid voor voorwaardelijke toegang wordt geblokkeerd. U kunt waarden tussen 1 en 90 dagen opgeven.

![](media/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>Stap 7: E-mailmeldingen configureren
Als u ontvangen van e-mailwaarschuwingen voor bedreigingen wilt, meld u bij de [Lookout console](https://aad.lookout.com) met het gebruikersaccount dat de meldingen moet ontvangen. Op de **voorkeuren** tabblad van de **System** -module, kies de gewenste meldingen en ze ingesteld op **ON**. Sla de wijzigingen.

![Schermafbeelding van de pagina Voorkeuren aan het gebruikersaccount weergegeven](media/lookout-email-notifications.png) als u niet meer ontvangen van e-mailmeldingen wilt, stelt u de meldingen op **OFF** en sla de wijzigingen.
### <a name="step-8-configure-threat-classification"></a>Stap 8: Bedreigingsclassificatie configureren
Lookout device threat protection classificeert mobiele bedreigingen van verschillende typen. De [Lookout threat classificaties](http://personal.support.lookout.com/hc/en-us/articles/114094130693) hebben standaard risiconiveaus gekoppeld. Deze kunnen worden gewijzigd op elk gewenst moment Suite vereisten van uw bedrijf.

![Schermafbeelding van de pagina beleid dreiging en classificaties weergeven](media/lookout-threat-classification.png)

>[!IMPORTANT]
> De risiconiveaus opgegeven dat hier zijn een belangrijk aspect van device threat protection omdat de Intune-integratie apparaatcompatibiliteit volgens deze risiconiveaus tijdens runtime berekent. Met andere woorden, de Intune-beheerder stelt een regel in het beleid voor de identificatie van een apparaat als niet-compatibel als het apparaat een actieve bedreigingen met een minimum heeft van niveau: hoog, Gemiddeld of laag. Het beleid van de classificatie threat in Lookout device threat protection schijven rechtstreeks de berekening van de naleving apparaat in Intune.

## <a name="watching-enrollment"></a>Volg de inschrijving
Zodra de installatie voltooid is, start Lookout device threat protection voor het pollen van Azure AD voor apparaten die met de opgegeven registratie-groepen overeenkomen.  U vindt meer informatie over de apparaten die zijn geregistreerd voor de module apparaten.  De initiële status voor apparaten weergegeven als in behandeling.  Het apparaat wordt gewijzigd nadat de Lookout for Work-app is geïnstalleerd, geopend en wordt geactiveerd op het apparaat.  Zie voor meer informatie over het verkrijgen van de Lookout voor werk app naar het apparaat gepusht de [configureren en implementeren van Lookout voor zakelijke apps](configure-and-deploy-lookout-for-work-apps.md) onderwerp.
## <a name="next-steps"></a>Volgende stappen
[Lookout MTP verbinding met Intune inschakelen](enable-lookout-connection-in-intune.md)
