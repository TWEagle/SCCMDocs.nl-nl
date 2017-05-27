---
title: Configureer de Asset Intelligence | Microsoft-documenten
description: Asset Intelligence in System Center Configuration Manager instellen.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08e0382d-de05-4a76-ba5c-7223173f7066
caps.latest.revision: 7
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: d2704e0f93ad9748f7eb06d714b3754463cb3bdb
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-asset-intelligence-in-system-center-configuration-manager"></a>Asset Intelligence in System Center Configuration Manager configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Asset Intelligence inventariseert en gebruik van softwarelicenties beheert.   

## <a name="steps-to-configure-asset-intelligence"></a>Stappen voor het configureren van Asset Intelligence  
   

- **Stap 1**: voor het verzamelen van de inventarisatiegegevens die nodig zijn voor Asset Intelligence-rapporten, moet u de clientagent voor hardware-inventaris inschakelen, zoals beschreven in [het uitbreiden van hardware-inventaris in System Center Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).
- **Stap 2**: [Asset Intelligence Hardware-inventarisatie inschakelen klassen](#BKMK_EnableAssetIntelligence).  
- **Stap 3**: [Een Asset Intelligence-synchronisatiepunt installeren](#BKMK_InstallAssetIntelligenceSynchronizationPoint)
- **Stap 4**: [Controle van geslaagde aanmeldingsgebeurtenissen inschakelen](#BKMK_EnableSuccessLogonEvents)  
- **Stap 5**: [Informatie over Software-licentie importeren](#BKMK_ImportSoftwareLicenseInformation)  
- **Stap 6**: [Asset Intelligence-onderhoudstaken configureren](#BKMK_ConfigureMaintenanceTasks) 


###  <a name="BKMK_EnableAssetIntelligence"></a> Enable Asset Intelligence hardware inventory reporting classes  
 U moet een of meer Asset Intelligence-hardware-inventaris rapportageklassen inschakelen zodat Asset Intelligence in Configuration Manager-sites. U kunt de klassen inschakelen op de startpagina **Asset Intelligence** of in de werkruimte **Beheer** , in het knooppunt **Clientinstellingen** in de eigenschappen voor clientinstellingen. Gebruik een van de volgende procedures.  

##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-the-asset-intelligence-home-page"></a>Asset Intelligence-rapportageklassen voor hardware-inventarisatie inschakelen via de startpagina Asset Intelligence  

1.  Kies in de Configuration Manager-console **activa en naleving** > **Asset Intelligence**.  

3.  Op de **Start** tabblad, in de **Asset Intelligence** groep, kiest u **Inventarisklassen bewerken**.   

4.  Als u Asset Intelligence reporting selecteert **alle Asset Intelligence-rapportageklassen inschakelen** of **alleen de geselecteerde Asset Intelligence-rapportageklassen inschakelen**, en selecteer ten minste één reporting klasse van de klassen weergegeven.  

    > [!NOTE]  
    >  Asset Intelligence-rapporten die afhankelijk zijn van de hardware-inventarisatieklassen die u inschakelt via deze procedure, bevatten pas gegevens als clients hebben gescand op hardware-inventaris en deze hebben geretourneerd.  


##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-client-settings-properties"></a>Asset Intelligence-rapportageklassen voor hardware-inventarisatie inschakelen via de eigenschappen voor clientinstellingen  

1.  Kies in de Configuration Manager-console **beheer** >  **clientinstellingen** > **standaard Clientagentinstellingen**. Als u aangepaste clientinstellingen-instellingen hebt gemaakt, kunt u deze in plaats daarvan.  

3.  Op de **Start** tabblad > **eigenschappen** groep, kiest u **eigenschappen**.   

4.  Kies **Hardware-inventaris** > **stellen klassen**. .  

5.  Kies **filteren op categorie** > **Asset Intelligence-Rapportageklassen**. De lijst met klassen wordt vernieuwd met alleen de Asset Intelligence-rapportageklassen voor hardware-inventarisatie.  

6.  Selecteer ten minste één reporting klasse in de lijst.  

    > [!NOTE]  
    >  Asset Intelligence-rapporten die afhankelijk zijn van de hardware-inventarisatieklassen die u inschakelt via deze procedure, bevatten pas gegevens als clients hebben gescand op hardware-inventaris en deze hebben geretourneerd.  
  

###  <a name="BKMK_InstallAssetIntelligenceSynchronizationPoint"></a> Install an Asset Intelligence Synchronization Point  

De Asset Intelligence synchronisatie sitesysteemrol wordt gebruikt voor Configuration Manager-sites met System Center Online om te synchroniseren van Asset Intelligence-catalogusinformatie verbinding. De Asset Intelligence-synchronisatiepunt kan alleen worden geïnstalleerd op een sitesysteem dat zich op de site op het hoogste niveau van de Configuration Manager-hiërarchie en vereist toegang tot het Internet om te synchroniseren met System Center Online via TCP-poort 443.

Via het Asset Intelligence-synchronisatiepunt kunnen nieuwe Asset Intelligence-catalogusgegevens worden gedownload en kan informatie over aangepaste softwaretitels voor categorisatie worden geüpload naar System Center Online. Microsoft beschouwt alle geüploade softwaretitels als openbare gegevens. Zorg ervoor dat uw aangepaste softwaretitels geen vertrouwelijke informatie bevatten. Zie voor meer informatie over het aanvragen van software titel categorisatie [aanvragen van een catalogusupdate voor niet-gecategoriseerde softwaretitels](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_RequestCatalogUpdate).  

##### <a name="to-install-an-asset-intelligence-synchronization-point-site-system-role"></a>Een sitesysteemrol Asset Intelligence-synchronisatiepunt installeren  

1.  Kies in de Configuration Manager-console **beheer**> **siteconfiguratie** > **Servers en sitesysteemrollen**.  

3.  De Asset Intelligence synchronisatie sitesysteemrol toevoegen aan een nieuwe of bestaande sitesysteemserver:  

    -  Voor een **nieuwe sitesysteemserver**: Op de **Start** tabblad, in de **maken** groep, kiest u **Sitesysteemserver maken** om de wizard te starten.   

        > [!NOTE]  
        >  Standaard, wanneer de Configuration Manager een sitesysteemrol installeert de installatiebestanden geïnstalleerd op de eerst beschikbare NTFS-geformatteerde vaste schijfstation met de meeste beschikbare vrije schijfruimte. Om te voorkomen dat Configuration Manager installeert op specifieke stations, maakt u een leeg bestand met de naam No_sms_on_drive.sms en kopieer het naar de hoofdmap van de schijf voordat u de sitesysteemserver installeert.  

    -  Voor een **bestaande sitesysteemserver**: Kies de server waarop u wilt de Asset Intelligence-synchronisatie-puntsitesysteemrol installeren. Als u een server, wordt een lijst van de sitesysteemrollen die al zijn geïnstalleerd op de server worden weergegeven in het detailvenster.  

         Op de **Start** tabblad, in de **Server** groep, kiest u **Sitesysteemrol toevoegen** om de wizard te starten.  

4.  Voltooi de **algemeen** pagina. Wanneer u de sitesysteemrol Asset Intelligence-synchronisatiepunt aan een bestaande sitesysteemserver wilt toevoegen, dient u de eerder geconfigureerde waarden te verifiëren.  

5.  Op de **Systeemrolselectie** optie **Asset Intelligence-synchronisatiepunt** uit de lijst met beschikbare rollen.  

6.  Op de **punt verbindingsinstellingen voor Asset Intelligence synchronisatie** pagina, kiest u **volgende**.  

     Standaard is de instelling **Dit Asset Intelligence-synchronisatiepunt gebruiken** geselecteerd en deze instelling kan niet worden gewijzigd op deze pagina. Omdat System Center Online alleen netwerkverkeer via TCP-poort 443 accepteert, kan de instelling **SSL-poortnummer** niet worden geconfigureerd op deze pagina van de wizard.  

7.  U kunt eventueel een pad naar het System Center Online verificatie certificaatbestand (.pfx) opgeven. Normaal gesproken geeft u geen pad voor het certificaat op omdat het verbindingscertificaat automatisch wordt geleverd tijdens de installatie van de siterol.  

8.  Op de **proxyserverinstellingen** of het Asset Intelligence-synchronisatiepunt wordt een proxyserver gebruiken wanneer u verbinding maakt met System Center Online om te synchroniseren van de catalogus, en of referenties om verbinding met de proxyserver te gebruiken.  

    > [!WARNING]  
    >  Als een proxyserver vereist is om verbinding te maken met System Center Online, kan het verbindingscertificaat ook worden verwijderd als het wachtwoord voor het geconfigureerde gebruikersaccount voor verificatie van de proxyserver verloopt.  

9. Geef op de pagina **Synchronisatieplanning** op of de Asset Intelligence-catalogus volgens een schema moet worden gesynchroniseerd. Als u de synchronisatieplanning inschakelt, kunt u een eenvoudig of aangepast synchronisatieschema opgeven. Tijdens de geplande synchronisatie maakt het Asset Intelligence-synchronisatiepunt verbinding met System Center Online om de meest recente Asset Intelligence-catalogus op te halen. De Asset Intelligence-catalogus in het knooppunt Asset Intelligence in Configuration Manager-console kunt u handmatig synchroniseren. Zie voor de stappen voor de Asset Intelligence-catalogus handmatig synchroniseren, de [de Asset Intelligence-catalogus handmatig synchroniseren](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ManuallySynchronizeCatalog) sectie het [bewerkingen voor Asset Intelligence in System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).  

10. Voltooi de wizard 

###  <a name="BKMK_EnableSuccessLogonEvents"></a> Enable auditing of success logon events  
 Vier Asset Intelligence-rapporten bevatten gegevens die zijn verzameld uit de Windows-beveiligingslogboeken op clientcomputers. Hier is het configureren van de computer aanmelden beveiligingsbeleidsinstellingen wilt geslaagd Aanmeldingsgebeurtenissen controleren.  

##### <a name="to-enable-success-logon-event-logging-by-using-a-local-security-policy"></a>De registratie van geslaagde aanmeldingsgebeurtenissen inschakelen op basis van lokaal beveiligingsbeleid  

1.  Op een clientcomputer Configuration Manager kiezen **Start** > **Systeembeheer** > **lokaal beveiligingsbeleid**.  

2.  In de **lokaal beveiligingsbeleid** dialoogvenster onder **beveiligingsinstellingen**, vouw **lokaal beleid**, en kies vervolgens **controlebeleid**.  

3.  Dubbelklik in het deelvenster met resultaten op **Aanmeldingsgebeurtenissen controleren**, zorg ervoor dat de **geslaagd** selectievakje is ingeschakeld en er vervolgens voor kiezen **OK**.  

##### <a name="to-enable-success-logon-event-logging-by-using-an-active-directory-domain-security-policy"></a>De registratie van geslaagde aanmeldingsgebeurtenissen inschakelen op basis van een Active Directory-domeinbeveiligingsbeleid  

1.  Op een domeincontroller kiezen **Start**, wijst u **Systeembeheer**, en kies vervolgens **beveiligingsbeleid voor domein**.  

2.  In de **lokaal beveiligingsbeleid** dialoogvenster onder **beveiligingsinstellingen**, vouw **lokaal beleid**, en kies vervolgens **controlebeleid**.  

3.  Dubbelklik in het deelvenster met resultaten op **Aanmeldingsgebeurtenissen controleren**, zorg ervoor dat de **geslaagd** selectievakje is ingeschakeld en er vervolgens voor kiezen **OK**.  

###  <a name="BKMK_ImportSoftwareLicenseInformation"></a> Import software license information  
 De volgende secties worden de procedures die nodig zijn voor het importeren van Microsoft en algemene software licentiegegevens in de Configuration Manager-sitedatabase met behulp van de Wizard Software-licentie importeren. Wanneer u softwarelicentiegegevens vanuit licentieverklaringsbestanden in de sitedatabase importeert, moet het siteservercomputeraccount over de machtiging **Volledig beheer** voor het NTFS-bestandssysteem beschikken voor de bestandsshare die wordt gebruikt voor het importeren van softwarelicentiegegevens.  

> [!IMPORTANT]  
>  Als softwarelicentiegegevens worden geïmporteerd in de sitedatabase, worden bestaande softwarelicentiegegevens overschreven. Het bestand met softwarelicentiegegevens dat u in de wizard Softwarelicentie importeren gebruikt, moet een volledige lijst met alle benodigde softwarelicentiegegevens bevatten.  

##### <a name="to-import-software-license-information-into-the-asset-intelligence-catalog"></a>Softwarelicentiegegevens importeren in de Asset Intelligence-catalogus  

1.  In de **activa en naleving** werkruimte kiezen **Asset Intelligence**.  

2.  Op de **Start** tabblad, in de **Asset Intelligence** groep, kiest u **softwarelicenties importeren**.   

4.  Geef op de pagina **Importeren** op of u een MVLS-bestand (.xml of .csv) of een algemene licentieverklaring (.csv) wilt importeren. Zie [Create a general license statement information file for import](#BKMK_CreateGeneralLicenseStatement) verderop in dit onderwerp voor meer informatie over het maken van een bestand met een algemene licentieverklaring.  

    > [!WARNING]  
    >  Ga naar het [Microsoft Volume Licensing Service Center](http://go.microsoft.com/fwlink/p/?LinkId=226547)als u een MVLS-bestand in de CSV-indeling wilt downloaden dat u kunt importeren in de Asset Intelligence-catalogus. U krijgt alleen toegang tot deze gegevens als u over een geregistreerd account op de website beschikt. Neem contact op met uw Microsoft-accountmedewerker voor informatie over het ontvangen van een MVLS-bestand in de XML-indeling.  

5.  Geef het UNC-pad naar het bestand met de licentie of kies **Bladeren** Selecteer een netwerk gedeelde mappen en bestanden.  

    > [!NOTE]  
    >  De gedeelde map moet correct zijn beveiligd om onbevoegde toegang tot het bestand met licentiegegevens te voorkomen. Daarnaast moet aan het computeraccount van de computer waarop de wizard wordt uitgevoerd de machtiging Volledig beheer zijn toegewezen voor de share met het licentie-importbestand.  

6. Voltooi de wizard.  

###  <a name="BKMK_CreateGeneralLicenseStatement"></a> Create a general license statement information file for import  
 Een algemene licentieverklaring kan ook in de Asset Intelligence-catalogus worden geïmporteerd via een handmatig gemaakt licentie-importbestand in een door komma’s gescheiden bestandsindeling (.csv).  

> [!NOTE]  
>  Hoewel alleen de velden **Name**, **Publisher**, **Version**en **EffectiveQuantity** gegevens moeten bevatten, moeten alle velden worden ingevoerd op de eerste rij van het licentie-importbestand. Alle velden moeten worden weergegeven in de volgende indeling: Maand per dag per jaar, bijvoorbeeld 04-08-2008.  

In Asset Intelligence worden de door u opgegeven producten in de algemene licentieverklaring vergeleken op basis van de productnaam en versie van het product, maar niet op basis van de naam van de uitgever. U moet in de algemene licentieverklaring een productnaam gebruiken die exact overeenkomt met de productnaam die is opgeslagen in de sitedatabase. Asset Intelligence neemt de **EffectiveQuantity** gegeven getal in het algemeen Licentieverklaring en vergelijkt het getal met het aantal geïnstalleerde producten in de inventaris van Configuration Manager gevonden.  

> [!TIP]  
>  Als u een volledige lijst van de productnamen opgeslagen in de sitedatabase van Configuration Manager, kunt u de volgende query uitvoeren op de sitedatabase: Selecteer ProductName0 van v_GS_INSTALLED_SOFTWARE.  

 U kunt exacte versies voor een product of een deel van de versie opgeven, bijvoorbeeld alleen de primaire versie. In de volgende voorbeelden worden de resulterende versieovereenkomsten voor de versie-invoer van een algemene licentieverklaring voor een specifiek product gegeven.  

|Invoer algemene licentieverklaring|Overeenkomende sitedatabase-items|  
|-------------------------------------|------------------------------------|  
|Naam: "MySoftware", ProductVersion0: "2"|ProductName0: "Mysoftware", ProductVersion0: "2.01.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.02.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.10.1234"|  
|Naam: "MySoftware", versie "2.05"|ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"|  
|Naam: "Mysoftware", versie "2"<br /><br /> Naam: "Mysoftware", versie "2.05"|Fout tijdens het importeren. Het importeren mislukt wanneer meerdere items overeenkomen met deze productversie.|  
  

##### <a name="to-create-a-general-license-statement-import-file-by-using-microsoft-excel"></a>Een importbestand voor een algemene licentieverklaring maken met Microsoft Excel  

1.  Open Microsoft Excel en maak een nieuw werkblad.  

2.  Voer op de eerste rij van het nieuwe werkblad alle veldnamen voor softwarelicentiegegevens in.  

3.  Voer op de tweede en volgende rijen van het nieuwe werkblad de vereiste softwarelicentiegegevens in. Zorg ervoor dat in elk geval alle vereiste velden voor softwarelicentiegegevens op de volgende rijen zijn ingevoerd voor elke softwarelicentie die moet worden geïmporteerd. De naam van de softwaretitel die in het werkblad wordt ingevoerd, moet gelijk zijn aan de softwaretitel die in Resource Explorer voor een client wordt weergegeven na het uitvoeren van een hardware-inventarisatie.  

4.  Sla het bestand in CSV-indeling.  

5.  Kopieer het CSV-bestand naar de bestandsshare die wordt gebruikt voor het importeren van softwarelicentiegegevens in de Asset Intelligence-catalogus.  

6.  Gebruik de Wizard Software-licentie importeren naar het nieuwe CSV-bestand importeren in de Configuration Manager-console.  

7.  Voer de Asset Intelligence **licentie 15A - afstemmingsrapport voor Software van derden** om te verifiëren dat de licentiegegevens geïmporteerd in de Asset Intelligence-catalogus zijn.  

> [!NOTE]  
>  Zie voor een voorbeeld van een algemene software-licentie-bestand dat u gebruiken kunt voor testdoeleinden [bestand importeren in System Center Configuration Manager voor algemene licentie voorbeeld Asset Intelligence](../../../../core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import.md).  

#### <a name="sample-table-to-describe-software-licenses"></a>Voorbeeldtabel voor beschrijving van softwarelicenties  
 Wanneer u een importbestand voor een algemene licentieverklaring maakt, kunt u de gegevens in de volgende tabel gebruiken om softwarelicenties te beschrijven die moeten worden geïmporteerd in de Asset Intelligence-catalogus.  

|Kolomnaam|Gegevenstype|Vereist|Voorbeeld|  
|-----------------|---------------|--------------|-------------|  
|Name|Maximaal 255 tekens|Ja|Softwaretitel|  
|Publisher|Maximaal 255 tekens|Ja|Software-uitgever|  
|Version|Maximaal 255 tekens|Ja|Versie softwaretitel|  
|Taal|Maximaal 255 tekens|Ja|Taal softwaretitel|  
|EffectiveQuantity|Geheel getal|Ja|Aantal aangeschafte licenties|  
|PONumber|Maximaal 255 tekens|Nee|Inkoopordergegevens|  
|ResellerName|Maximaal 255 tekens|Nee|Informatie van verkoper|  
|DateOfPurchase|Datumwaarde in de volgende indeling: DD-MM-JJJJ|Nee|Datum van aanschaf van licentie|  
|SupportPurchased|Waarde in bits|Nee|0 of 1: Voer voor Ja 0 of 1 voor Nee|  
|SupportExpirationDate|Datumwaarde in de volgende indeling: DD-MM-JJJJ|Nee|Einddatum van gekochte ondersteuning|  
|Opmerkingen|Maximaal 255 tekens|Nee|Optionele opmerkingen|  

###  <a name="BKMK_ConfigureMaintenanceTasks"></a> Configure Asset Intelligence maintenance tasks  
 De volgende onderhoudstaken zijn beschikbaar voor Asset Intelligence:  

-   **Titel van toepassing met Inventarisinformatie controleren**: Controleert of de softwaretitel die moet worden gerapporteerd in software-inventaris gerapporteerd, overeenkomt met de softwaretitel in de Asset Intelligence-catalogus wordt. Standaard is deze taak ingeschakeld en gepland voor uitvoering op zaterdag na 12:00 uur en voor 5:00 uur Deze onderhoudstaak is alleen beschikbaar op het hoogste niveau in uw Configuration Manager-hiërarchie.  

-   **Geïnstalleerde softwaregegevens samenvatten**: Bevat de informatie die wordt weergegeven in de **activa en naleving** werkruimte in de **geïnventariseerde Software** knooppunt onder de **Asset Intelligence** knooppunt. Wanneer de taak wordt uitgevoerd, wordt een telling van alle geïnventariseerde softwaretitels op de primaire site in Configuration Manager verzameld. Standaard is deze taak ingeschakeld en gepland voor uitvoering elke dag na 12:00 uur en voor 5:00 uur Deze onderhoudstaak is alleen beschikbaar in primaire sites.  

##### <a name="to-configure-asset-intelligence-maintenance-tasks"></a>Asset Intelligence-onderhoudstaken configureren  

1.  Kies in de Configuration Manager-console **beheer** > **siteconfiguratie** > **Sites**.  

3.  Selecteer de site waarop de Asset Intelligence-onderhoudstaak moet worden geconfigureerd.  

4.  Op de **Start** tabblad, in de **instellingen** groep, kiest u **siteonderhoud**. Selecteer een taak en kies **bewerken** de instellingen wijzigen. 

      Het is raadzaam dat u de periode op daluren van de site instellen. De periode is het tijdsinterval waarin de taak kan worden uitgevoerd. De periode wordt gedefinieerd op basis van de opgegeven waarden bij **Starten na** en **Laatste starttijd** in het dialoogvenster **Taakeigenschappen** .  

    U kunt de taak meteen starten door de huidige dag te selecteren en bij **Starten na** een tijd enkele minuten na de huidige tijd in te stellen.  

7.  Kies **OK** uw instellingen op te slaan. De taak wordt nu uitgevoerd volgens schema.  

    > [!NOTE]  
    >  Als een taak niet uitvoeren op de eerste poging, probeert Configuration Manager de taak opnieuw uitvoeren totdat de taak is uitgevoerd of de periode waarin de taak wordt uitgevoerd is verstreken.  

