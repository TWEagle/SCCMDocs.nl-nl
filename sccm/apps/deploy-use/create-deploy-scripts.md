---
title: Maken en scripts uitvoeren met Configuration Manager | Microsoft Docs
description: Maken en uitvoeren van scripts op clientapparaten met Configuration Manager.
ms.custom: na
ms.date: 08/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: 14
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: c0d94b8e6ca6ffd82e879b43097a9787e283eb6d
ms.openlocfilehash: 4dcda88d4e91347f6da97e8da04c38f9e65e07bc
ms.contentlocale: nl-nl
ms.lasthandoff: 08/02/2017

---

# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Maken en PowerShell-scripts uitvoeren vanaf de Configuration Manager-console

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In Configuration Manager, naast het gebruik van pakketten en programma's voor het implementeren van scripts, kunt u de volgende functionaliteit aan de volgende acties uitvoeren:

- PowerShell-Scripts importeren naar Configuration Manager
- De scripts van de Configuration Manager-console (voor niet-ondertekende scripts alleen) bewerken
- Scripts markeren als goedgekeurd of geweigerd, de beveiliging te verbeteren
- Scripts uitvoeren op verzamelingen van Windows client-pc's en lokale beheerde Windows-pc's. U kunt scripts niet implementeren, in plaats daarvan ze wel bijna onmiddellijk worden uitgevoerd op clientapparaten.
- Bekijk de resultaten geretourneerd door het script in de Configuration Manager-console.

>[!TIP]
>Scripts zijn in deze versie van Configuration Manager, een functie van de voorlopige versie. Zie voor het inschakelen van scripts [pre-release functies in System Center Configuration Manager](/sccm/core/servers/manage/pre-release-features).

## <a name="prerequisites"></a>Vereisten

Voor het PowerShell-scripts uitvoeren, moet op de client, PowerShell versie 3.0 of hoger worden uitgevoerd. Echter, als u het uitvoeren van een script bevat de functionaliteit van een nieuwere versie van PowerShell, de client waarop u het script uitvoert moet worden uitgevoerd die versie.

Configuration Manager-clients moeten de client uitgevoerd vanaf de release 1706 of later om te kunnen uitvoeren van scripts.

Gebruik van scripts, moet u lid zijn van de juiste Configuration Manager-beveiligingsrol.

- Om te importeren en scripts - auteur uw account moet hebben **maken** machtigingen voor **SMS Scripts** in de **instellingen voor naleving** beveiligingsrol.
- Goedkeuren of weigeren van scripts - uw account moet hebben **goedkeuren** machtigingen voor **SMS Scripts** in de **instellingen voor naleving** beveiligingsrol.
- Uitvoeren van scripts - uw account moet hebben **-Script uitvoeren** machtigingen voor **verzamelingen** in de **instellingen voor naleving** beveiligingsrol.

Zie voor meer informatie over beveiligingsrollen voor Configuration Manager [basisprincipes van beheer op basis van rollen](/sccm/core/understand/fundamentals-of-role-based-administration).

Standaard goedkeuren gebruikers niet van een script dat ze hebben gemaakt. Omdat scripts krachtige, veelzijdige zijn, en kunnen worden geïmplementeerd op veel apparaten, kunt u de rollen tussen de persoon die het script maakt en de persoon die het script goedkeurt scheiden. Deze functies bieden een extra beveiligingsniveau tegen het uitvoeren van een script zonder toezicht. U kunt deze secundaire goedkeuring, voor een eenvoudige testen uitschakelen.

## <a name="allow-users-to-approve-their-own-scripts"></a>Toestaan dat gebruikers hun eigen scripts goedkeuren

1. Klik op **Beheer**in de Configuration Manager-console.
2. Vouw **Siteconfiguratie** uit in de werkruimte **Beheer**en klik vervolgens op **Sites**.
3. Kies in de lijst met websites, uw site en klik op de **Start** tabblad, in de **Sites** groep, klikt u op **hiërarchie-instellingen**.
4. Op de **algemene** tabblad van de **eigenschappen van hiërarchie-instellingen** dialoogvenster vak, schakel het selectievakje uit **staan geen script auteurs goed te keuren van hun eigen scripts**.
Sites

## <a name="import-and-edit-a-script"></a>Importeren en bewerken van een script

1. Klik in de Configuration Manager-console op **Software Librar**y.
2. In de **softwarebibliotheek** werkruimte, klikt u op **Scripts**.
3. Op de **Start** tabblad, in de **maken** groep, klikt u op **Script maken**.
4. Op de **Script** pagina van de maken **Script** wizard de volgende instellingen configureren:
    - **De naam van een script** -Voer een naam voor het script. Hoewel u meerdere scripts met dezelfde naam maken kunt, maakt met dubbele namen het moeilijker te vinden van het script u moet in de Configuration Manager-console.
    - **Scripttaal** -momenteel alleen PowerShell-scripts worden ondersteund.
    - **Importeren** -importeren van een PowerShell-script in de console. Het script wordt weergegeven in de **Script** veld.
    - **Schakel** -het huidige script verwijdert uit het Script-veld.
    - **Script** -wordt het momenteel geïmporteerde script. U kunt het script in dit veld indien nodig bewerken.
5. Voltooi de wizard. Het nieuwe script wordt weergegeven in de **Script** lijst met de status van **wachten op goedkeuring**. Voordat u dit script op clientapparaten uitvoert kunt, moet u deze goedkeuren.

### <a name="script-examples"></a>Voorbeelden van scripts

Hier volgen enkele voorbeelden van scripts die u mogelijk wilt gebruiken met deze mogelijkheid.

#### <a name="create-a-folder"></a>Maak een map

*Nieuw Item 'c:\scripts'-type mapnaam* 
 
 
#### <a name="create-a-file"></a>Maak een bestand

*Nieuw Item c:\scripts\new_file.txt-type-bestandsnaam*


## <a name="approve-or-deny-a-script"></a>Goedkeuren of weigeren van een script

Voordat u een script uitvoeren kunt, moeten worden goedgekeurd. Goedkeuren van een script:

1. Klik in de Configuration Manager-console op **Softwarebibliotheek**.
2. In de **softwarebibliotheek** werkruimte, klikt u op **Scripts**.
3. In de **Script** kiest u het script dat u wilt goedkeuren of weigeren en klik op de **Start** tabblad, in de **Script** groep, klikt u op **goedkeuren/weigeren**.
4. In de **goedkeuren of weigeren** dialoogvenster script **goedkeuren**, of **weigeren** het script en voer eventueel een opmerking over uw beslissing. Als u een script weigeren, kan deze kan niet worden uitgevoerd op clientapparaten.
5. Voltooi de wizard. In de **Script** wilt weergeven, ziet u de **goedkeuring staat** kolom wijzigen, afhankelijk van de actie die u hebt gemaakt.

## <a name="run-a-script"></a>Een script uitvoeren
Nadat een script is goedgekeurd, kunt u deze kunt uitvoeren met een verzameling die u kiest.

1. Klik op **Activa en naleving**op de Configuration Manager-console.
2. In de activa en naleving werkruimte, klikt u op **Apparaatverzamelingen**.
3. In de **Apparaatverzamelingen** lijst, klikt u op de verzameling van apparaten waarop u wilt dat het script uit te voeren.
4. Op de **Start** tabblad, in de **alle systemen** groep, klikt u op **-Script uitvoeren**.
5. Op de **Script** pagina van de **-Script uitvoeren** wizard kiest u een script in de lijst. Alleen goedgekeurde scripts die worden weergegeven.
6. Klik op **volgende**, en voltooi de wizard.

>[!IMPORTANT]
>Het script krijgt een periode van één uur in waarop moet worden uitgevoerd. Als dat niet wordt uitgevoerd (bijvoorbeeld als de PC is uitgeschakeld) in deze periode, moet u het opnieuw uitvoeren.

## <a name="next-steps"></a>Volgende stappen

Nadat u hebt een script uitgevoerd op clientapparaten, moet u deze procedure gebruiken voor het bewaken van het succes van de bewerking.

1. Klik in de Configuration Manager-console op **bewaking**.
2. In de **bewaking** werkruimte, klikt u op **Script Status**.
3. In de **Script Status** wanneer u de resultaten voor elk script dat u hebt uitgevoerd op clientapparaten lijst bekijken. De afsluitcode van een script van **0** geeft meestal aan dat het script is uitgevoerd.

