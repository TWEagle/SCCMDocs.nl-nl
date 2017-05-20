---
title: Configureer uw Intune-abonnement met behulp van System Center Configuration Manager | Microsoft-documenten
description: Configureer uw Intune-abonnement met behulp van System Center Configuration Manager.
ms.custom: na
ms.date: 03/05/2017
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
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 10cc64ae7e4d91f53201c2896b359e77ef04d32d
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="configure-your-intune-subscription-with-system-center-configuration-manager-and-microsoft-intune"></a>Uw Intune-abonnement met System Center Configuration Manager en Microsoft Intune configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De Intune-abonnement kunt u apparaten beheren via het internet. Dit omvat opgeven welke Gebruikersverzameling apparaten kan registreren en het definiëren van gegevens die worden weergegeven voor gebruikers. U kunt ook bedrijf huisstijl naar de Intune bedrijfsportal met uw bedrijfslogo en aangepaste kleur van de schema's bij het maken van de Intune-abonnement toevoegen.

Het Intune-abonnement voert de volgende taken uit:

-   haalt het certificaat op dat voor het serviceaansluitpunt is vereist om verbinding te maken met de Intune-service
-   bepaalt de gebruikersverzameling waarmee de gebruikers mobiele apparaten kunnen registreren
-   bepaalt en configureert de mobiele platformen die u wilt ondersteunen

> [!IMPORTANT]
>  Maken van een abonnement voor Microsoft Intune in Configuration Manager zullen uw site het service connection point in zetten "onlinemodus." Zie [Informatie over het serviceaansluitpunt in System Center Configuration Manager](../../core/servers/deploy/configure/about-the-service-connection-point.md).

## <a name="to-create-the-microsoft-intune-subscription"></a>Het Microsoft Intune-abonnement maken

1.  Meld u via [Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=258216) aan voor een Microsoft Intune-account als u dat nog niet hebt gedaan.  U hoeft na het maken van uw Intune-account kan niet alle gebruikers toevoegen aan de Intune-account of aanvullende instellingen configuraties uit te voeren.

2.  Klik op **Beheer**in de Configuration Manager-console.

3.  Vouw in de werkruimte **Beheer** het knooppunt **Cloud Services** uit en klik op **Microsoft Intune-abonnementen**. Klik op het tabblad **Start** op **Microsoft Intune-abonnement toevoegen**.

![Intune-abonnement maken](../media/mdm-set-intune.png)

4.  Bekijk de tekst op de pagina **Inleiding** van de Wizard Microsoft Intune-abonnement maken en klik op **Volgende**.

5.  Klik op de pagina **Abonnement** op **Aanmelden** en meld u aan met behulp van uw werk- of schoolaccount. In de **stellen de Mobile Device Management-instantie** dialoogvenster, selecteer het selectievakje in om alleen mobiele apparaten beheren met Configuration Manager via de Configuration Manager-console. U moet deze optie selecteren om door te gaan met uw abonnement.

    > [!IMPORTANT]
    >  Als u als uw instantie voor beheer van Configuration Manager selecteren, kan u wijzigen de instantie voor beheer van Microsoft Intune in de toekomst.

6.  Klik op de privacykoppelingen om deze te bekijken en klik op **Volgende**.

7.  Geef op de pagina **Algemeen** de volgende opties op en klik op **Volgende**.

  -   **Verzameling**: Een Gebruikersverzameling opgeven die gebruikers bevat die hun mobiele apparaten gaan registreren.

      > [!NOTE]
      >  Als een gebruiker wordt verwijderd uit de verzameling, blijft apparaat van de gebruiker tot 24 uur, wanneer de gebruiker wordt verwijderd uit de database worden beheerd.

  -   **Bedrijfsnaam**: Geef de naam van uw bedrijf.

  -   **URL naar privacydocumentatie**: Als u uw bedrijf privacy-informatie naar een koppeling die via Internet toegankelijk is publiceert, geeft u een koppeling waarmee gebruikers toegankelijk via de bedrijfsportal, bijvoorbeeld http://www.contoso.com/CP_privacy.html. Privacyinformatie kan verduidelijken welke informatie gebruikers met uw bedrijf delen.

  -   **Kleurenschema voor bedrijfsportal**: Wijzig eventueel de blauwe standaardkleur voor de bedrijfsportals.

  -   **Configuration Manager sitecode**: Geef een sitecode voor een primaire site voor het beheren van mobiele apparaten.

    > [!NOTE]
    >  Het wijzigen van de sitecode heeft enkel een weerslag op nieuwe registraties en niet op bestaande geregistreerde apparaten.

8.  Op de **contactgegevens van bedrijf** pagina, geeft u de contactgegevens van bedrijf wordt weergegeven voor gebruikers onder **contact opnemen met IT** in de bedrijfsportal-app. Geef de contactgegevens voor uw bedrijf en klik op **volgende**.

9. Op de **bedrijfslogo** pagina kunt u kiezen of logo's worden weergegeven in de bedrijfsportal en klik vervolgens op **volgende**.

10. Voltooi de wizard.

> [!div class="button"]
[< Vorige stap](confirm-dns.md)[volgende stap >  ](terms-and-conditions.md)

