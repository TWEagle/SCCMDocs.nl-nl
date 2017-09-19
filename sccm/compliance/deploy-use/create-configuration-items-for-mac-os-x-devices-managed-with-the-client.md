---
title: Configuratie-items maken voor beheerde client Macs - Configuration Manager | Microsoft Docs
description: Gebruik de System Center Configuration Manager Mac OS X-configuratie-item voor het beheren van instellingen voor Mac OS X-apparaten.
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 722d5bf5-bedc-4dfc-b324-6eeb773874e9
caps.latest.revision: "8"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 6910710badd0937cbdf1471e4f3f050590e2e769
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-create-configuration-items-for-mac-os-x-devices-managed-with-the-system-center-configuration-manager-client"></a>Configuratie-items maken voor Mac OS X-apparaten die worden beheerd door de System Center Configuration Manager-client
De System Center Configuration Manager gebruiken**Mac OS X (aangepast)** configuratie-item voor het beheren van instellingen voor Mac OS X-apparaten die worden beheerd door Configuration Manager-client.  
  
 Het Mac OS X-besturingssysteem gebruikt eigenschappenlijstbestanden (of plist-bestanden) om toepassingsinstellingen op te slaan. Gebruik nalevingsinstellingen om instellingen in een eigenschappenlijstbestand te beoordelen en herstellen. U kunt ook Mac OS X-instellingen beheren door een shellscript te schrijven dat een waarde retourneert die u voor nalevingsdoeleinden kunt beoordelen en herstellen.  
  
### <a name="to-create-a-custom-mac-os-x-configuration-item"></a>Een aangepast Mac OS X-configuratie-item maken  
  
1.  Klik in de Configuration Manager-console op **activa en naleving**.  
  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  
  
3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  
  
4.  Geef op de pagina **Algemeen** van de **Wizard Configuratie-item maken** een naam en een optionele beschrijving voor het configuratie-item op.  
  
5.  Selecteer onder **Geef het type configuratie-item op dat u wilt maken** de optie **Mac OS X (aangepast)**.  
  
6.  Klik op **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  
  
7.  Selecteer op de pagina **Ondersteunde platforms** van de wizard de specifieke Mac OS X-versies die het configuratie-item beoordelen.  
  
8.  Op de pagina **Instellingen** van de wizard geeft u nieuwe instellingen op die worden beoordeeld op naleving op Mac-computers. Klik op **Nieuw** om het dialoogvenster **Instelling maken** te openen.  
  
9. Geef in het dialoogvenster **Instelling maken** een unieke naam en een beschrijving voor de instelling op.  
  
10. Kies het **Instellingstype** dat u wilt en geef de vereiste gegevens op, zoals weergegeven in de volgende tabel:  
  
    -   **Mac OS X-voorkeuren** -  
  
        -   **Toepassings-id**: geef de toepassings-id van het eigenschappenlijstbestand op vanwaaruit u een sleutel op naleving wilt beoordelen.  
  
             Bijvoorbeeld, als u instellingen voor de Safari-webbrowser wilt bewerken, kunt u **com.apple.Safari.plist** gebruiken.  
  
        -   **Sleutel**: Geef de naam van de sleutel op die u wilt beoordelen op naleving op Mac-computers. Gebruik de volgende syntaxis: */<woordenlijst\>/<sleutelnaam\>*.  
  
            > [!IMPORTANT]  
            >  De sleutelnaam is hoofdlettergevoelig en wordt niet beoordeeld als deze anders is dan de sleutelnaam op de Mac-computer. Bovendien kunt u de sleutelnaam niet bewerken nadat u die hebt opgegeven. Als u de sleutelnaam wilt bewerken, moet u de instelling verwijderen en vervolgens opnieuw maken.  
  
    -   **Script** -  
  
        -   **Detectiescript**: Klik op **Script toevoegen** en voer vervolgens een shellscript in om voor nalevingsdoeleinden toegang te krijgen tot instellingen op de Mac-computer. Gebruik de **echo** opdracht in het shellscript om waarden te retourneren naar Configuration Manager om te voldoen. Configuration Manager gebruikt de resultaten in **STDOUT** evalueren van naleving.  
  
            > [!IMPORTANT]  
            >  Neem de opdracht **reboot** niet op in het detectiescript. Omdat het detectiescript elke keer wordt uitgevoerd wanneer de client opnieuw wordt opgestart, zorgt dit ervoor dat de Mac-computer doorlopend opnieuw wordt opgestart.  
  
        -   **Herstelscript (optioneel)**: Klik desgewenst op **Script toevoegen** en voer vervolgens een shellscript in dat wordt gebruikt voor het herstellen van niet-compatibele instellingen die op Mac-clientcomputers worden gevonden.  
  
            > [!IMPORTANT]  
            >  Om ervoor te zorgen dat u geen opmaaktekens introduceert die de Mac-computer niet kan interpreteren, moet u het script niet kopiëren en plakken maar zelf typen.  
  
11. Kies het **gegevenstype**. Dit heeft de indeling waarin de voorwaarde de gegevens retourneert voordat deze worden gebruikt om de instelling te beoordelen.  
  
    > [!NOTE]  
    >  Het gegevenstype **Drijvende komma** ondersteunt alleen 3 cijfers na het decimaalteken.  
    >   
    >  Configuration Manager biedt geen ondersteuning met behulp van de **Booleaanse** gegevenstype voor scriptinstellingen voor Mac-configuratie-item. Stel in plaats daarvan het gegevenstype in op **Geheel getal** en zorg ervoor dat het script een geheel getal retourneert.  
  
12. Klik op **OK** om de instellingen op te slaan, sluit het dialoogvenster **Instelling maken**, en ga vervolgens door met het toevoegen van de instellingen die u nodig hebt.  
  
13. Op de pagina **Compliantieregels** van de wizard dient u de voorwaarden op te geven voor naleving van een configuratie-item. Voordat een instelling kan worden beoordeeld op naleving, moet de instelling minimaal één compliantieregel hebben. Klik op **Nieuw** om een nieuwe regel toe te voegen.  
  
14. Geef in het dialoogvenster **Regel maken** de volgende informatie op:  
  
    -   **Naam:** Voer een naam voor de compliantieregel.  
  
    -   **Beschrijving:** Voer een beschrijving voor de compliantieregel.  
  
    -   **Geselecteerde instelling:** Klik op **Bladeren** openen de **instelling selecteren** in het dialoogvenster. Selecteer de instelling waarvoor u een regel wilt definiëren of klik op **Nieuwe instelling**. Klik op **Selecteren** als u klaar bent.  
  
        > [!TIP]  
        >  U kunt ook klikken op **Eigenschappen** om informatie over de geselecteerde instelling weer te geven.  
  
    -   **Regeltype:** Selecteer het type compliantieregel dat u wilt gebruiken:  
  
        -   **Waarde:** Maak een regel die de waarde die is geretourneerd door de configuratie-item met een waarde die u opgeeft.  
  
        -   **Existentieel:** Maak een regel die de instelling beoordeelt, afhankelijk van of deze op een apparaat bestaat.  
  
    -   Geef voor het regeltype **Waarde** de volgende informatie op:  
  
        -   De instelling moet voldoen aan de volgende regel: selecteer een operator en een waarde die worden beoordeeld op naleving van de geselecteerde instelling. U kunt de volgende operatoren gebruiken:  
  
            -   **Is gelijk aan**  
  
            -   **Is niet gelijk aan**  
  
            -   **Groter dan**  
  
            -   **Kleiner dan**  
  
            -   **Tussen**  
  
            -   **Groter dan of gelijk aan**  
  
            -   **Kleiner dan of gelijk aan**  
  
            -   **Een van**: geef in het tekstvak één vermelding per regel op.  
  
            -   **Geen van**: geef in het tekstvak één vermelding per regel op.  
  
        -   **Regels die niet compliant zijn herstellen, waar ondersteund**: Selecteer deze optie als u wilt dat Configuration Manager automatisch niet-compatibele regels oplost.  
  
            > [!IMPORTANT]  
            >  U kunt niet-compatibele regels alleen herstellen als de regeloperator is ingesteld op **Is gelijk aan**.  
  
        -   **Niet-compliantie melden als deze instellingsexemplaar niet wordt gevonden**: het configuratie-item rapporteert niet-naleving als deze instelling niet op de Mac-computer is gevonden.  
  
    -   **Ernst van niet-compliantie voor rapporten**: Geef de ernst op die moet worden gerapporteerd als deze compliantieregel mislukt. De beschikbare ernstniveaus zijn als volgt:  
  
        -   **Geen** -Computers die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
        -   **Informatie** -Computers die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
        -   **Waarschuwing** -Computers die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
        -   **Kritieke** -Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
        -   **Kritiek met gebeurtenis** -Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd door de Mac-clientcomputer.  
  
    -   Geef voor het regeltype **Existentieel** de volgende informatie op:  
  
        -   Kies een van de volgende mogelijkheden:  
  
            -   **De instelling moet bestaan op clientapparaten**  
  
            -   **De instelling mag niet bestaan op clientapparaten**  
  
        -   **Niet-nageleefd ernst voor rapporten:** Geef de ernst op die worden gerapporteerd als deze compliantieregel mislukt. De beschikbare ernstniveaus zijn als volgt:  
  
            -   **Geen** -Computers die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
            -   **Informatie** -Computers die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
            -   **Waarschuwing** -Computers die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
            -   **Kritieke** -Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
            -   **Kritiek met gebeurtenis** -Computers die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd door de Mac-clientcomputer.  
  
        > [!NOTE]  
        >  Welke opties worden weergegeven, hangt af van het instellingstype waarvoor u een regel configureert.  
  
    -   Klik op **OK** om het dialoogvenster **Regel maken** te sluiten.  
  
15. Bevestig de instellingen voor het nieuwe configuratie-item op de pagina **Samenvatting** en voltooi vervolgens de wizard.  
  
 Het nieuwe configuratie-item wordt weergegeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving**.  
  
 Zie [Configuratiebasislijnen maken in System Center Configuration Manager](../../compliance/deploy-use/create-configuration-baselines.md) als u dit configuratie-item nu wilt toevoegen aan een configuratiebasislijn.  
  
## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd met de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md)
