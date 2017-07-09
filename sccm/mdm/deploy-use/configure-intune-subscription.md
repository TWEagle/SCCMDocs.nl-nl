---
title: Uw Intune-abonnement met System Center Configuration Manager configureren | Microsoft Docs
description: Configureer uw Intune-abonnement met System Center Configuration Manager.
ms.custom: na
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99de8fe7-560e-401a-8ab2-6d87d091be17
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 662901e850566756759fcfc61c58f3c0e56bc5aa
ms.openlocfilehash: 22d890c972d3166f9c7b583d8d3fa917c1897880
ms.contentlocale: nl-nl
ms.lasthandoff: 06/03/2017

---
# <a name="configure-your-intune-subscription-with-system-center-configuration-manager-and-microsoft-intune"></a>Configureren van uw Intune-abonnement met System Center Configuration Manager en Microsoft Intune

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Het Intune-abonnement kunt u apparaten beheren via het internet. Dit omvat opgeven welke Gebruikersverzameling apparaten kan registreren en gegevens weergegeven voor gebruikers definiëren. U kunt ook huisstijl Intune bedrijfsportal-App met uw bedrijfslogo en kleurenschema voor schema's tijdens het maken van het Intune-abonnement toevoegen.

Het Intune-abonnement voert de volgende taken uit:

-   haalt het certificaat op dat voor het serviceaansluitpunt is vereist om verbinding te maken met de Intune-service
-   bepaalt de gebruikersverzameling waarmee de gebruikers mobiele apparaten kunnen registreren
-   bepaalt en configureert de mobiele platformen die u wilt ondersteunen

> [!IMPORTANT]
>  Een abonnement voor Microsoft Intune in Configuration Manager maakt wordt van uw site het service connection point geplaatst in 'online modus'. Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../core/servers/deploy/configure/about-the-service-connection-point.md).

## <a name="to-create-the-microsoft-intune-subscription"></a>Het Microsoft Intune-abonnement maken

1.  Meld u via [Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=258216) aan voor een Microsoft Intune-account als u dat nog niet hebt gedaan.  Nadat uw Intune-account is gemaakt, hoeft u geen gebruikers toevoegen aan het Intune-account of extra instellingen configuraties uitvoeren.

2.  Klik op **Beheer**in de Configuration Manager-console.

3.  Vouw in de werkruimte **Beheer** het knooppunt **Cloud Services** uit en klik op **Microsoft Intune-abonnementen**. Klik op het tabblad **Start** op **Microsoft Intune-abonnement toevoegen**.

![Een Intune-abonnement maken](../media/mdm-set-intune.png)

4.  Bekijk de tekst op de pagina **Inleiding** van de Wizard Microsoft Intune-abonnement maken en klik op **Volgende**.

5.  Klik op de pagina **Abonnement** op **Aanmelden** en meld u aan met behulp van uw werk- of schoolaccount. In de **de instantie voor Mobile Device Management instellen** dialoogvenster, selecteer het selectievakje in om alleen mobiele apparaten beheren met Configuration Manager via de Configuration Manager-console. U moet deze optie selecteren om door te gaan met uw abonnement.

    > [!IMPORTANT]
    >  Wanneer u Configuration Manager als uw instantie voor beheer selecteert, kunt u alleen uw instantie voor beheer van Microsoft Intune in Configuration Manager versie 1610 of hoger en Microsoft Intune version 1705 wijzigen zonder contact opnemen met Microsoft Support en zonder de registratie ongedaan maken en registreren van uw bestaande beheerde apparaten. Zie voor meer informatie [wijzigen van uw MDM-instantie](/sccm/mdm/deploy-use/change-mdm-authority).

6.  Klik op de privacykoppelingen om deze te bekijken en klik op **Volgende**.

7.  Geef op de pagina **Algemeen** de volgende opties op en klik op **Volgende**.

  -   **Verzameling**: Een Gebruikersverzameling opgeven die gebruikers bevat die hun mobiele apparaten gaan registreren.

      > [!NOTE]
      >  Als een gebruiker wordt verwijderd uit de verzameling, blijft het apparaat van de gebruiker tot 24 uur wanneer de gebruiker wordt verwijderd uit de database worden beheerd.

  -   **Bedrijfsnaam**: Geef de naam van uw bedrijf.

  -   **URL naar privacydocumentatie van bedrijf**: Als u uw bedrijf privacy-informatie naar een koppeling die via Internet toegankelijk is publiceert, geeft u een koppeling waarop gebruikers kunnen via de bedrijfsportal, bijvoorbeeld http://www.contoso.com/CP_privacy.html. Privacyinformatie kan verduidelijken welke informatie gebruikers met uw bedrijf delen.

  -   **Kleurenschema voor bedrijfsportal**: Wijzig eventueel de blauwe standaardkleur voor de bedrijfsportals.

  -   **Configuration Manager-sitecode**: Geef een sitecode voor een primaire site om de mobiele apparaten te beheren.

    > [!NOTE]
    >  Het wijzigen van de sitecode heeft enkel een weerslag op nieuwe registraties en niet op bestaande geregistreerde apparaten.

8.  Op de **contactgegevens van bedrijf** pagina, geeft u de contactgegevens van bedrijf die wordt weergegeven voor gebruikers onder **contact opnemen met IT** in de bedrijfsportal-app. Contactgegevens voor uw bedrijf bevatten, en klik vervolgens op **volgende**.

9. Op de **bedrijfslogo** pagina kunt u kiezen of logo's weergegeven in de bedrijfsportal en klik vervolgens op **volgende**.

10. Voltooi de wizard.

> [!div class="button"]
[< Vorige stap](confirm-dns.md)[volgende stap >  ](terms-and-conditions.md)

