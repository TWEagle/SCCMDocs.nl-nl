---
title: ARTIKELTITEL | Microsoft Docs
description: 
keywords: 
author: GITHUB USERNAME
manager: ALIAS
ms.date: 10/06/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: GET ONE FROM guidgenerator.com
ms.openlocfilehash: a218011ded1ff3acc1dbd24471119b701f2cce23
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="metadata-and-markdown-template"></a>Metagegevens en Markdown-sjabloon

Deze docs.ms-sjabloon bevat voorbeelden van markdown-syntaxis, evenals richtlijnen voor het instellen van de metagegevens. Is beschikbaar in de hoofdmap van elke EM-testopslagplaats (bijvoorbeeld ~/Azure-RMSDocs-PR ~/Azure-rmsdocs-PR/template.MD) en is bedoeld om te lezen als markdown-bestand, maar u naar verwijzen kunt [de gepubliceerde versie](https://stage.docs.microsoft.com/en-us/rights-management/template) om te zien hoe de markdown-voorbeelden worden weergegeven.

Bij het maken van een markdown-bestand moet u de sjabloon kopiëren naar een nieuw bestand, de metagegevens invullen zoals hieronder aangegeven, de H1-kop boven aan de titel van het artikel en verwijder de inhoud.


## <a name="metadata"></a>Metagegevens

Het volledige metagegevensblok staat hierboven, onderverdeeld in verplichte en optionele velden; Zie de [OPS-referentieoverzicht voor metagegevens](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data) voor meer informatie. Een aantal belangrijke opmerkingen:

- U **moet** een ruimte tussen de dubbele punt (:) en de waarde voor een metagegevenselement hebben.
- Als een optioneel metagegevenselement geen waarde uitcommentariëren aan het element met een # (laat deze leeg en gebruik niet 'n.v.t.'); Als u een waarde aan een element dat is als commentaar toevoegt, moet u # verwijderen.
- Dubbele punten in een waarde (bijvoorbeeld een titel) wordt de metagegevensparser verbroken. Gebruik in plaats van de HTML-codering van &#58; (bijvoorbeeld ' titel: Azure Rights Management &#58; de basisbeginselen | Azure RMS').
- **titel**: Deze titel wordt weergegeven in zoekmachineresultaten. De titel moet eindigen met een sluisteken (|), gevolgd door de naam van de service (bv. Zie hierboven). De titel niet nodig (en waarschijnlijk beter niet) gelijk zijn aan de titel in de H1-kop. Titel moet ongeveer 65 tekens (inclusief | SERVICENAAM)
- **auteur**, **manager**, **revisor**: Het veld auteur moet bevatten de **Github-gebruikersnaam** van de auteur, niet zijn alias.  De velden "manager" en 'revisor' aan de andere kant moeten aliassen bevatten. MS.Reviewer geeft de naam van de Projectmanager die is gekoppeld aan het artikel of de service.
- **MS.AssetID**: Dit is de GUID van het artikel van CAPS. Wanneer u een nieuw markdown-bestand maakt, krijgen een GUID van [https://www.guidgenerator.com](https://www.guidgenerator.com).
- **MS.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: Mogelijke waarden voor deze elementen vindt [hier](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default).

## <a name="basic-markdown-and-gfm"></a>Basis-Markdown en GFM

Alle basis- en vleugje Github markdown wordt ondersteund. Zie voor meer informatie over deze:

- [Basislijn markdown-syntaxis](https://daringfireball.net/projects/markdown/syntax)
- [Vleugje Github over markdown-documentatie](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>Koppen

Voorbeelden van koppen op het eerste en tweede niveau staan hierboven.

Er **moet** worden slechts één kop van het eerste niveau in uw onderwerp, dat wordt weergegeven als de titel op de pagina.  

Koppen op het tweede niveau genereert de inhoudsopgave op de pagina die wordt weergegeven in de sectie 'In dit artikel' onder de titel op de pagina.

### <a name="third-level-heading"></a>Kop op derde niveau
#### <a name="fourth-level-heading"></a>Kop op vierde niveau
##### <a name="fifth-level-heading"></a>Kop op vijfde niveau
###### <a name="sixth-level-heading"></a>Kop op zesde niveau

## <a name="text-styling"></a>Tekstopmaak

*Cursief*

**Bold**

~~Doorhalen~~



## <a name="links"></a>Koppelingen

Als een koppeling naar een bestand in dezelfde repo, gebruikt [relatieve koppelingen](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2).

- Voorbeeld: [Wat is Azure Rights Management](./understand-explore/what-is-azure-rights-management.md)

Als u wilt koppelen naar een kop in hetzelfde markdown-bestand, de bron van het gepubliceerde artikel weergeven, de id van de kop gevonden (bijvoorbeeld `id="blockquote"`, en een koppeling met # + id (bijvoorbeeld `#blockquote`).

- Voorbeeld: [Blockquotes](#blockquote)

Als een koppeling naar een kop in een markdown-bestand in dezelfde repo, gebruikt u relatieve koppeling + hashtagkoppeling.

- Voorbeeld: [technisch overzicht van het aanmeldingsproces](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

Als koppeling naar een extern bestand, gebruikt u de volledige URL als koppeling.

- Voorbeeld: [Github](http://www.github.com)

Als een URL wordt weergegeven in een markdown-bestand, wordt deze omgezet in een aanklikbare koppeling.

- Voorbeeld: http://www.github.com

## <a name="lists"></a>een lijst met

### <a name="ordered-lists"></a>Geordende lijsten

1. Dit
1. Is
1. een
1. besteld
1. Lijst  


#### <a name="ordered-list-with-an-embedded-list"></a>Geordende lijst met een ingesloten lijst

1. Hier
1. wordt geleverd
1. een
1. ingesloten
    1. Mevr. Scarlett
    1. Docent paars
1. besteld
1. lijst


### <a name="unordered-lists"></a>Niet-geordende lijsten

- Dit
- is
- een
- lijst met opsommingstekens
- lijst


##### <a name="unordered-list-with-an-embedded-lists"></a>Niet-geordende lijst met een ingesloten lijst

- Dit
- lijst met opsommingstekens
- lijst
    - Mevr. Peacock
    - Dhr. Green
- Bevat  
- Andere
    1. Kolonel Mustard
    1. Mevr. White
- een lijst met


## <a name="horizontal-rule"></a>Horizontale lijn

---

## <a name="tables"></a>Tabellen

| Tabellen        | Zijn           | Cool  |
| ------------- |:-------------:| -----:|
| Kol. 3 is      | rechts uitgelijnd | $1600 |
| Kol. 2 is      | gecentreerd      |   $12 |
| Kol. 1 is standaard | links uitgelijnd     |    $1 |


## <a name="code"></a>Code

### <a name="codeblock"></a>Codeblock

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>Inlinecode

Dit is een voorbeeld van `in-line code`.

## <a name="blockquotes"></a>Blockquotes

> De droogte had geduurd nu tien miljoen jaar en de heerschappij van de verschrikkelijke hagedissen was allang een einde gekomen. Hier op de evenaar, op het continent dat zou een dag bekend staan als Afrika, had de strijd om bestaan bereikte een nieuw hoogtepunt van wreedheid en wie de is nog niet bekend. In dit barre en dorre land kan alleen kleine snelle of dappere gedijen of wezens overleven.

## <a name="images"></a>Installatiekopieën

### <a name="static-image"></a>Statische afbeelding

![Dit is de alt-tekst](./media/AzRMS_elements.png)

### <a name="linked-image"></a>Gekoppelde afbeelding

[![alternatieve tekst voor gekoppelde afbeelding](./media/AzRMS_elements.png)](https://azure.microsoft.com)

### <a name="animated-gif"></a>gif-animatie

![gif-animatie](./media/hololens.gif)

## <a name="alerts"></a>Waarschuwingen

### <a name="note"></a>Opmerking

> [!NOTE]
> Dit is een opmerking

### <a name="warning"></a>Waarschuwing

> [!WARNING]
> Dit is een waarschuwing

### <a name="tip"></a>Tip

> [!TIP]
> Dit is een TIP

### <a name="important"></a>Belangrijk

> [!IMPORTANT]
> Dit is belangrijk

## <a name="videos"></a>Video's

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>Docs.MS-uitbreidingen

### <a name="button"></a>Knop

> [!div class="button"]
[knop voor koppelingen](/rights-management)

### <a name="selector"></a>Selector

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [balk](/rights-management/scratch.md)

### <a name="step-by-step"></a>Stapsgewijze

>[!div class="step-by-step"]
[Vooraf](https://www.example.com)
[volgende](https://www.example.com)
