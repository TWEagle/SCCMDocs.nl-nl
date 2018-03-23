---
title: Microsoft Edge-instellingen configureren
titleSuffix: Configuration Manager
description: Instellingen voor de webbrowser Microsoft Edge configureren op Windows 10-clients
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 76477b4d-df41-4b25-8318-7d18d46ca2c6
ms.openlocfilehash: 57393c00faa0cc26d785d91ad1c6ecb9407ba5da
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-microsoft-edge-settings-in-system-center-configuration-manager"></a>Microsoft Edge-instellingen configureren in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

<!-- 1357310 -->
Vanaf versie 1802, voor klanten die gebruikmaken van de [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) web browser op Windows 10-clients, maakt u een nalevingsbeleid voor Configuration Manager-instellingen voor verschillende instellingen voor Microsoft Edge configureren. 



## <a name="policy-settings"></a>Beleidsinstellingen
Dit beleid bevat momenteel de volgende instellingen:
- **De Microsoft Edge-browser ingesteld als standaard**: Hiermee configureert u de Windows 10-app-instelling voor standaard voor webbrowser Microsoft Edge
- **De adresbalk toestaan vervolgkeuzelijst**: Windows 10 versie 1703 of hoger vereist. Zie voor meer informatie [AllowAddressBarDropdown browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowaddressbardropdown).
- **Favorieten synchronisatie tussen Microsoft browsers toestaan**: Windows 10 versie 1703 of hoger vereist. Zie voor meer informatie [SyncFavoritesBetweenIEAndMicrosoftEdge browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-syncfavoritesbetweenieandmicrosoftedge).
- **Schakel bladeren door gegevens bij afsluiten toestaan**: Windows 10 versie 1703 of hoger vereist. Zie voor meer informatie [ClearBrowsingDataOnExit browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-clearbrowsingdataonexit).
- **Toestaan dat Do Not Track-headers**: Zie voor meer informatie [AllowDoNotTrack browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowdonottrack).
- **Automatisch invullen toestaan**: Zie voor meer informatie [AllowAutofill browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowautofill).
- **Cookies toestaan**: Zie voor meer informatie [AllowCookies browser-beleid](/windows/client-management/mdm/policy-csp-browser#browser-allowcookies).
- **Pop-upblokkering toestaan**: Zie voor meer informatie [AllowPopups browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowpopups).
- **Zoeksuggesties in de adresbalk toestaan**: Zie voor meer informatie [AllowSearchSuggestionsinAddressBar browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowsearchsuggestionsinaddressbar).
- **Verzenden van intranetverkeer naar Internet Explorer toestaan**: Zie voor meer informatie [SendIntranetTraffictoInternetExplorer browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-sendintranettraffictointernetexplorer).
- **Wachtwoord toestaan manager**: Zie voor meer informatie [AllowPasswordManager browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager).
- **Hulpprogramma's voor ontwikkelaars toestaan**: Zie voor meer informatie [AllowDeveloperTools browserbeleid](/windows/client-management/mdm/policy-csp-browser#browser-allowdevelopertools).
- **Toestaan dat extensies**: Zie voor meer informatie [AllowExtensions browser-beleid](/windows/client-management/mdm/policy-csp-browser#browser-allowextensions).



## <a name="create-the-microsoft-edge-browser-profile"></a>De Microsoft Edge-browser-profiel maken

1. Ga in de Configuration Manager-console naar de **activa en naleving** werkruimte. Vouw **instellingen voor naleving** en selecteer de nieuwe **Microsoft Edge-Browser-profielen** knooppunt. Klik op de optie lint **Microsoft Edge Browser-beleid maken**.
2. Geef een **naam** voor het beleid (optioneel) Voer een **beschrijving**, en klik op **volgende**.
3. Op de **instellingen** pagina, wijzig de waarde in **geconfigureerde** voor de instellingen voor opname in dit beleid en klik op **volgende**.
4. Op de **ondersteunde Platforms** pagina, selecteert u de versies van besturingssystemen en architecturen waarop dit beleid van toepassing is en op **volgende**. 
5. Voltooi de wizard.



## <a name="deploy-the-policy"></a>Het beleid implementeren

1. Selecteer uw beleid en klik op de optie lint **implementeren**.
2. Klik op **Bladeren** selecteren van de verzameling gebruikers of apparaten waarop het beleid te implementeren. 
3. Selecteer extra opties indien nodig. 
    a. Waarschuwingen genereren wanneer het beleid niet compatibel is. 
    b. Stel de planning op waarmee de client de apparaatcompatibiliteit met dit beleid evalueert.
4. Klik op **OK** de implementatie te maken.



## <a name="next-steps"></a>Volgende stappen

Net als alle instellingen voor nalevingsbeleid herstelt de client de instellingen op de planning die u opgeeft. [Bewaken en rapporteren over apparaatcompatibiliteit](/sccm/compliance/deploy-use/monitor-compliance-settings) in de Configuration Manager-console.
