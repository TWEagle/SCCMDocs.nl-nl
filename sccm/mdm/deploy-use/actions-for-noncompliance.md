---
title: Acties voor niet-compatibele
titleSuffix: Configuration Manager
description: Meer informatie over het instellen van acties voor niet-compatibele met Configuration Manager
ms.custom: na
ms.date: 11/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
caps.latest.revision: "18"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 1dd10d9452fae85f2ecc3d3077fba420454ef337
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2017
---
# <a name="set-up-actions-for-non-compliance"></a>Acties voor niet-naleving instellen

De **acties voor niet-naleving** kunt configureren van een tijd besteld reeks acties die worden toegepast op apparaten die niet compatibel. Bijvoorbeeld, u kunt e-mailberichten verzenden naar de eindgebruiker van niet-compatibele apparaten en/of die apparaten niet-compatibele markeren.

## <a name="before-you-begin"></a>Voordat u begint

> [!IMPORTANT]
> U moet ten minste één apparaat nalevingsbeleid gemaakt om acties voor niet-naleving in te stellen.

Dit zijn de ondersteunde acties voor niet-naleving:

- E-mail verzenden naar de eindgebruiker
- Apparaten niet-compatibele markeren

### <a name="send-e-mail-to-end-user"></a>E-mail verzenden naar de eindgebruiker

U kunt kiezen uit vooraf gemaakte standaard e-mailsjablonen of een volledig aangepast e-mailmeldingen maken. Configuration Manager biedt aanpassing van het onderwerp, berichttekst, met inbegrip van bedrijfslogo, contactgegevens en extra ontvangers.

### <a name="mark-devices-non-compliant"></a>Apparaten niet-compatibele markeren

U kunt een planning bepalen in aantal dagen dat het apparaat moet worden geblokkeerd van de toegang tot bedrijfsbronnen. Dit onmiddellijk kan zijn, maar u kunt ook geven de gebruiker een respijtperiode te voldoen aan het nalevingsbeleid voor apparaten.

### <a name="supported-platforms"></a>Ondersteunde platforms

Ondersteund door [alle platforms die worden beheerd via Intune](https://docs.microsoft.com/intune/supported-devices-browsers).

## <a name="to-add-an-email-template"></a>Toevoegen van een e-mailsjabloon

Configuration Manager biedt e-mailsjablonen, maar u kunt ook uw eigen maken. De e-mailsjabloon wordt later gebruikt bij het maken van acties voor niet-naleving te communiceren met gebruikers.

1. Kies in de Configuration Manager-console **activa en naleving**.

2. In de **activa en naleving** werkruimte Vouw **instellingen voor naleving**, en kies vervolgens **naleving meldingssjablonen**.

3. Op de **Start** tabblad, in de **naleving meldingssjabloon maken**.

4. Moet u de volgende informatie: een. Naam: Naam van de sjabloon e-mailbericht.
    b. Van: E-mailadres in de e-mailmelding verzenden.
    c. Onderwerp: Een onderwerp met uitleg over de e-mailmelding wordt verzonden.
    d. Hoofdtekst van bericht: Meer informatie over de e-mailmelding.

    > [!TIP] 
    > U kunt ook opnemen **e-mailkop** met uw bedrijfslogo en E-mail voettekst die u kunt opnemen bedrijfsnaam en contactgegevens. Dit kan ook worden bewerkt in de eigenschappen van u Intune-abonnement.

5. Klik op **OK** om op te slaan van de nieuwe e-mailsjabloon.

6. Op de **actie toevoegen** pagina kunt u een nieuw e-mailsjabloon maken in de lijst.

7. Nadat u uw e-mailsjabloon selecteert, klikt u op **OK**.

## <a name="to-create-actions-for-non-compliance"></a>Acties voor niet-naleving maken

1. Kies in de Configuration Manager-console **activa en naleving**.

2. In de **activa en naleving** werkruimte Vouw **instellingen voor naleving**, en kies vervolgens **nalevingsbeleid**.

3. Op de **Start** tabblad, in de **maken** groep, kiest u **nalevingsbeleid maken**.

4. Selecteer de **ondersteunde Platforms** u wilt en klik vervolgens op **volgende** twee keer. U kunt doorgaan de **regels** pagina.

5. Op de **niet-compatibele acties** pagina definiëren wat er gebeurt wanneer een apparaat niet voldoen aan het beleid wordt, klikt u **nieuw**.
6. U kunt twee opties kiezen: **E-mail verzenden naar eindgebruikers** of **markeren apparaat niet-compatibele**.

7. Als het selecteren van **e-mail verzenden naar eindgebruikers**, moet u het volgende invoeren: een. **Respijtperiode (in dagen):** U kunt invoeren 0 365 dagen.
    b. **Extra ontvangers (via e-mail)** c. **Selecteer de berichtsjabloon:** U kunt de standaard e-mailsjablonen of de aangepaste items die u hebt toegevoegd.
    
    > [!TIP] 
    > U kunt ook een nieuw e-mailsjabloon toevoegen bij het toevoegen van de **e-mail verzenden naar eindgebruikers** actie door te klikken op **nieuw:** van **actie toevoegen** pagina.

8. Als het selecteren van **markeren apparaat niet-compatibele**, moet u het volgende invoeren: een. **Respijtperiode (in dagen):** U kunt invoeren 0 365 dagen.

9. Nadat u hebt ervoor de actie gekozen en de instellingen voor deze ingevoerd, klikt u op **volgende** tweemaal vervolgens **sluiten**.


