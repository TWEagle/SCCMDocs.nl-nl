---
title: App-gebruik controleren met softwaremeter
titleSuffix: Configuration Manager
description: 
ms.custom: na
ms.date: 09/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1fdaee2-2816-4447-94cd-609f6948f215
caps.latest.revision: "8"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: c44d606efbbcd099bdcd6d5f83aad156525d9279
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="software-metering-in-system-center-configuration-manager"></a>Softwarelicentiecontrole in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In dit onderwerp bevat een verwijzing voor alle bewerkingen die u uitvoeren kunt wanneer u System Center Configuration Manager softwarelicentiecontrole.

> [!IMPORTANT]
>  Softwarelicentiecontrole wordt gebruikt om bureaublad-apps voor Windows-computers te bewaken die een bestandsnaam hebben die eindigt op **.exe**. Softwarelicentiecontrole controleert geen moderne Windows-apps (zoals die worden gebruikt door Windows 8).

##  <a name="prerequisites-for-software-metering"></a>Vereisten voor softwarelicentiecontrole
Softwarelicentiecontrole heeft geen externe afhankelijkheden, alleen afhankelijkheden binnen het product.

|Afhankelijkheid|Meer informatie|
|----------------|----------------------|
|Clientinstellingen voor softwarelicentiecontrole|Om softwarelicentiecontrole te gebruiken moet de clientinstelling **Softwaremeter op clients inschakelen** zijn ingeschakeld en geïmplementeerd op computers. U kunt instellingen voor softwarelicentiecontrole implementeren op alle computers in de hiërarchie of aangepaste instellingen implementeren op computergroepen. Zie **softwarelicentiecontrole configureren** in dit onderwerp.|
|Het reporting services-punt.|U moet een reporting services-punt configureren voordat u softwarelicentiecontrolerapporten kunt weergeven. Zie [Rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md) voor meer informatie.|

##  <a name="configure-software-metering"></a>Softwarelicentiecontrole configureren
 Met deze procedure configureert u de standaardclientinstellingen voor softwarelicentiecontrole en past u deze toe op alle computers in uw hiërarchie. Als u dat deze instellingen alleen op enkele computers wilt implementeren, maakt u een aangepaste apparaatclientinstelling en implementeert u deze in een verzameling waartoe de computers behoren die u voor softwarelicentiecontrole wilt gebruiken. Zie voor meer informatie over het maken van aangepaste apparaatinstellingen [clientinstellingen configureren](../../core/clients/deploy/configure-client-settings.md).

1.  Klik in de Configuration Manager-console op **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.

2.  Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.

3.  In het dialoogvenster **Standaardinstellingen** klikt u op **Softwarelicentiecontrole**.

4.  In de lijst **Apparaatinstellingen** configureert u dan het volgende:

    -   **Softwaremeter op clients inschakelen**: Selecteer **True** softwarelicentiecontrole inschakelen.

    -   **Planning gegevensverzameling**: Configureren hoe vaak gegevens van softwaremeter van clientcomputers worden verzameld. Gebruik de standaardwaarde van elke **7 dagen** of klik op **Planning** om een aangepaste planning op te geven.

5.  Klik op **OK** om het dialoogvenster **Standaardinstellingen** te sluiten.

 De volgende keer dat clientcomputers clientbeleid downloaden, worden deze geconfigureerd met deze instellingen. Zie voor het initiëren van het ophaalbeleid voor één client [clients beheren](../../core/clients/manage/manage-clients.md).

##  <a name="create-software-metering-rules"></a>Maken van regels voor softwarelicentiecontrole
 Gebruik de wizard Softwaremeterregel maken voor het maken van een nieuwe regel voor softwarelicentiecontrole voor uw Configuration Manager-site.

1.  Klik in de Configuration Manager-console op **activa en naleving** > **softwarelicentiecontrole**.

3.  Op het tabblad **Start** in de groep **Maken** klikt u op **Softwaremeterregel maken**.

4.  Op de **algemene** pagina van de wizard Softwaremeterregel maken, geeft u de volgende informatie:

    -   **Naam** : de naam van de softwaremeterregel. Deze moet uniek zijn en beschrijvend.

        > [!NOTE]
        >  Softwaremeterregels kunnen dezelfde naam hebben als de bestandsnaam in de regels anders is.

    -   **Bestandsnaam** : de naam van het programmabestand dat u wilt meten. U kunt klikken op **Bladeren** om het dialoogvenster **Openen** weer te geven, waarin u het te gebruiken programmabestand kunt selecteren.

        > [!NOTE]
        >  Als u de naam van het uitvoerbare bestand in het vak **Bestandsnaam** typt, worden er geen controles uitgevoerd om te bepalen of dit bestand bestaat, en of dit de benodigde berichtkopinformatie bevat. Klik indien mogelijk op **Bladeren** en selecteer het uitvoerbare bestand dat moet worden gemeten.
        >
        >  Jokertekens zijn niet toegestaan in de bestandsnaam.
        >
        >  Dit vak is optioneel als er een waarde voor **Originele bestandsnaam** is opgegeven.

    -   **Originele bestandsnaam** : de naam van het uitvoerbare bestand dat u wilt meten. Deze naam komt overeen met de informatie in de koptekst van het bestand, niet de bestandsnaam zelf, zodat dit nuttig kan zijn in gevallen waarin de naam van het uitvoerbare bestand is gewijzigd maar u het met zijn oorspronkelijke naam wilt meten.

        > [!NOTE]
        >  Jokertekens zijn niet toegestaan in de oorspronkelijke bestandsnaam.
        >
        >  Dit vak is optioneel als er een waarde voor **Bestandsnaam** is opgegeven.

    -   **Versie** : de versie van het uitvoerbare bestand dat u deze wilt meten. U kunt het jokerteken (&#42;) ter vertegenwoordiging van een reeks tekens of het jokerteken teken (?) ) een willekeurig teken vertegenwoordigt. Als u meten voor alle versies van een uitvoerbaar bestand wilt, gebruikt u de standaardwaarde (&#42;).

    -   **Taal** : de taal van het uitvoerbare bestand dat u wilt meten. De standaardwaarde is de huidige landinstelling van het besturingssysteem dat u gebruikt. Als u een uitvoerbaar bestand selecteert om te meten door te klikken op de knop **Bladeren** , wordt dit vak automatisch ingevuld als er taalinformatie in de koptekst van het bestand aanwezig is. Als u alle taalversies van een bestand wilt meten, selecteert u **Elke** in de vervolgkeuzelijst.

    -   **Beschrijving** : een optionele beschrijving voor de softwaremeterregel.

    -   **Deze softwaremeterregel toepassen op de volgende clients** : selecteer of u de softwaremeterregel wilt toepassen op alle clients in de hiërarchie of aan de clients die zijn toegewezen aan de site die is opgegeven in de lijst **Site** .

5.  Als u wilt doorgaan, klikt u op **Volgende**.

6.  Controleer en bevestig de instellingen en voltooi de wizard om de softwaremeterregel te maken. De nieuwe softwaremeterregel wordt weergegeven in het knooppunt **Softwarelicentiecontrole** in de werkruimte **Activa en naleving** .

##  <a name="configure-automatic-software-metering-rules"></a>Automatische softwaremeterregels configureren
 U kunt configureren in Configuration Manager voor het automatisch genereren van recente inventarisatiegegevens ondergebracht in de sitedatabase uitgeschakelde softwaremeterregels softwarelicentiecontrole. U kunt deze inventarisgegevens zodanig configureren dat er alleen softwaremeterregels worden gemaakt voor toepassingen die worden gebruikt met een opgegeven percentage computers. Ook kunt u het maximum aantal automatisch gegenereerde softwaremeterregels opgeven dat op de site is toegestaan.

> [!NOTE]
>  Softwaremeterregels die automatisch worden gemaakt, worden standaard uitgeschakeld. Voordat u kunt beginnen met het verzamelen van gegevens met deze regels, moet u deze inschakelen.

1.  Klik in de Configuration Manager-console op **activa en naleving** > **softwarelicentiecontrole**, en klikt u op de **Start** tabblad, in de **instellingen** groep, klikt u op **eigenschappen van Softwaremeter**.

3.  In het dialoogvenster **Eigenschappen van softwaremeter** configureert u het volgende:

    -   **Bewaren van gegevens (in dagen)** : geeft de tijd aan dat gegevens behouden blijven die door softwaremeterregels in de sitedatabase worden gegenereerd. De standaardwaarde is **90** dagen.

    -   Schakel de optie **Automatisch uitgeschakelde meterregels maken van inventarisgegevens over recent gebruik**in.

    -   **Geef op welk percentage van computers in de hiërarchie een programma moet gebruiken voordat automatisch een softwaremeterregel wordt gemaakt** : de standaardwaarde is **10** procent.

    -   **Geef het aantal softwaremeterregels op dat moet worden overschreden in de hiërarchie voordat het automatisch maken regels wordt uitgeschakeld** : de standaardwaarde is **100** regels.

4.  Klik op **OK** om het dialoogvenster **Eigenschappen van softwaremeter** te sluiten.

##  <a name="manage-software-metering-rules"></a>Softwaremeterregels beheren
 In de werkruimte **Activa en naleving** selecteert u **Softwarelicentiecontrole**, selecteert u de te beheren softwaremeterregel en selecteert u vervolgens een beheertaak.

 Gebruik de volgende tabel voor meer informatie over de beheertaken waarvoor u mogelijk meer uitleg nodigt hebt voordat u ze selecteert.

|Beheertaak|Details|
|---------------------|-------------|
|**Inschakelen**<br /><br /> **Uitschakelen**|Hiermee schakelt u een softwaremeterregel in of uit. Deze instelling wordt gedownload naar clientcomputers volgens de **Pollinginterval voor clientbeleid** in de sectie **Clientbeleid** van de clientinstellingen (standaard elke 60 minuten).<br /><br /> Zie [clientinstellingen configureren](../../core/clients/deploy/configure-client-settings.md) .|

##  <a name="monitor-software-metering"></a>Bewaak softwarelicentiecontrole
 Softwarelicentiecontrole in Configuration Manager bevat een aantal ingebouwde rapporten waarmee u informatie over software softwarelicentiecontrole bewerkingen kunt bewaken. Deze rapporten hebben de rapportcategorie **Softwaremeter**.

 Zie voor meer informatie over het configureren van rapportage in Configuration Manager [rapportage in System Center Configuration Manager](../../core/servers/manage/reporting.md).

 Bovendien kunt u query's en verzamelingen op basis van de gegevens die zijn opgeslagen in de Configuration Manager-database met softwaremeters.

 Zie voor meer informatie over verzamelingen in Configuration Manager [inleiding op verzamelingen](/sccm/core/clients/manage/collections/introduction-to-collections).

 Zie voor meer informatie over query's in Configuration Manager [inleiding op query's](/sccm/core/servers/manage/introduction-to-queries).

##  <a name="security-and-privacy-for-software-metering"></a>Beveiliging en privacy voor softwarelicentiecontrole

### <a name="security-issues-for-software-metering"></a>Beveiligingsproblemen voor softwarelicentiecontrole
 Een aanvaller kan ongeldige softwarelicentiecontrolegegevens naar Configuration Manager, die door het beheerpunt worden geaccepteerd, zelfs wanneer de clientinstelling voor softwarelicentiecontrole is uitgeschakeld verzenden. Dit kan leiden tot een groot aantal regels voor softwarelicentiecontrole die worden gerepliceerd in de gehele hiërarchie, waardoor een DoS-aanval op het netwerk en voor Configuration Manager-siteservers.

 Omdat een aanvaller ongeldige softwaremetergegevens kan maken, dient u softwaremetergegevens niet als gezaghebbend te beschouwen.

 Softwaremeter is standaard ingeschakeld als een clientinstelling.

###  <a name="privacy-information-for-software-metering"></a>Privacy-informatie voor softwarelicentiecontrole
 Softwaremeter bewaakt het gebruik van toepassingen op clientcomputers. Softwaremeter is standaard ingeschakeld. U moet configureren welke toepassingen moeten worden gemeten. Metergegevens worden opgeslagen in de Configuration Manager-database. De informatie wordt versleuteld tijdens de overdracht naar een beheerpunt, maar deze wordt niet opgeslagen in een versleutelde vorm in de Configuration Manager-database.

 Deze gegevens blijven in de database bewaard tot deze worden verwijderd door de siteonderhoudstaak **Verouderde gegevens van softwaremeter verwijderen** (elke vijf dagen) en **Verouderde samenvattingsgegevens van softwaremeter verwijderen** (elke 270 dagen). U kunt het verwijderingsinterval configureren. Er worden geen metergegevens naar Microsoft verzonden.

 Voordat u softwaremeter configureert, moet u nadenken over uw privacyvereisten.

## <a name="example-scenario-for-using-software-metering"></a>Voorbeeldscenario voor het gebruik van softwaremeter
 In deze sectie maakt u een voorbeeld van een softwaremeterregel waarmee u de volgende bedrijfsvereisten kunt oplossen:

-   Bepalen hoeveel exemplaren van een bepaalde app uw bedrijf heeft

-   Alle ongebruikte exemplaren van een app detecteren

-   Bepalen welke gebruikers een bepaalde app regelmatig gebruiken

 Woodgrove Bank heeft Microsoft Office 2010 geïmplementeerd als standaard Office-productiviteitssuite. Ter ondersteuning van een oudere toepassing, moet Microsoft Office Word 2003 op bepaalde computer worden uitgevoerd. De IT-afdeling wil ondersteuning en licentiekosten reduceren door deze exemplaren van Word 2003 te verwijderen als de oude toepassing niet meer wordt gebruikt. De helpdesk wil ook bepalen welke gebruikers de oude toepassing gebruiken.

 Johan is van Woodgrove Bank IT-systemen Manager die softwarelicentiecontrole in Configuration Manager gebruikt om deze zakelijke doelstellingen te bereiken. Hij voert de volgende acties:

- John controleert de vereisten voor de softwarelicentiecontrole en bevestigt dat het Reporting Services-punt geïnstalleerd en operationeel is.
- John configureert de standaardclientinstellingen voor de softwarelicentiecontrole:<br>Hij schakelt softwaremeter in en gebruikt het standaardschema (om de zeven dagen) om gegevens te verzamelen.<br>Hij configureert de software-inventarisatie om bestanden met de extensie .exe te inventariseren door de clientinstelling **Deze bestandstypen inventariseren**voor de software-inventarisatie te configureren.<br>Hij voegt een nieuwe softwaremeterregel, met de naam **woodgrove.exe**, om de oudere toepassing te bewaken.
- John wacht zeven dagen, waarna de clientcomputers gebruiksgegevens beginnen te rapporteren voor het uitvoerbare bestand **woodgrove.exe** .
- Johan gebruikt de Configuration Manager-rapport **installatiebasis voor alle programma's met gecontroleerde licenties** om te zien welke computers over de toepassing **woodgrove.exe** geladen.
- Na zes maanden voert John het rapport **Computers waarop een programma met gecontroleerde licentie is geïnstalleerd maar die het programma sinds een opgegeven datum niet hebben uitgevoerd**uit. Hij geeft hiervoor de softwaremeterregel en de datum van zes maanden terug op. Dit rapport identificeert 120 computers waarop het programma de afgelopen zes maanden niet is uitgevoerd.
- John voert nog een aantal controles uit om zich ervan te verzekeren dat de oudere toepassing niet is vereist op de geïdentificeerde computers. Hij verwijdert de oudere toepassing en het exemplaar van Word 2003 van deze computers.<br>John voert het rapport **Gebruikers die een specifiek programma met gecontroleerde licenties hebben uitgevoerd** uit om de helpdesk te voorzien van een lijst met gebruikers die oudere toepassing blijven gebruiken.
- John blijft de softwarelicentiecontrolerapporten wekelijks controleren en neemt indien nodig corrigerende maatregelen.

 Als gevolg van deze maatregel worden de toepassingen die niet meer nodig zijn, verwijderd en worden de IT-ondersteuning en licentiekosten gereduceerd. Daarnaast beschikt de helpdesk nu over de gewenste lijst met gebruikers die de oudere toepassing uitvoeren.
