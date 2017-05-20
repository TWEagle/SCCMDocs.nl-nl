---
title: Beheren van updates voor Office 365 ProPlus | Microsoft-documenten
description: Configuration Manager worden gesynchroniseerd clientupdates van de WSUS-catalogus naar de siteserver beschikbaar om te implementeren op clients updates voor Office 365.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 016580dc6ee3c5268833db941d42416a976d201c
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-office-365-proplus-with-configuration-manager"></a>Beheren van Office 365 ProPlus met Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager gesynchroniseerd clientupdates voor Office 365 en maakt u ze beschikbaar om te implementeren op clients met Office 365 geïnstalleerd. Beginnend in Configuration Manager versie 1610, kunt u Office 365 clientinformatie vanuit het dashboard clientbeheer voor Office 365 controleren.

Beginnend in Configuration Manager versie 1602, beschikt Configuration Manager over de mogelijkheid voor het beheren van updates voor Office 365-clients met behulp van de werkstroom software-update. Wanneer Microsoft publiceert een nieuwe Office 365-clientupdate voor de Office-inhoud voor de levering van netwerk CDN (), publiceert Microsoft ook een updatepakket voor Windows Server Update Services (WSUS). Configuration Manager worden gesynchroniseerd met de Office 365 client-update van de WSUS-catalogus naar de siteserver, is de update beschikbaar om te implementeren op clients.

Vanaf versie 1702, kunt u het installatieprogramma van Office 365 starten vanuit het dashboard clientbeheer voor Office 365 om de initiële Office 365-App installeren ervaring gemakkelijker maken. De wizard laat u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud voor de levering van bedrijfsnetwerken (CDN), en maken en implementeren van een scripttoepassing met de inhoud.

## <a name="office-365-client-management-dashboard"></a>Office 365 clientbeheer dashboard  
U start in Configuration Manager versie 1610, is het dashboard clientbeheer voor Office 365 beschikbaar in de Configuration Manager-console. Het dashboard, Ga naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.

Het dashboard geeft grafieken voor het volgende weer:

- Aantal Office 365-clients
- Office 365-clientversies
- Clienttalen voor Office 365
- Office 365 client kanalen     
Zie voor meer informatie [overzicht van de update voor Office 365 ProPlus communicatiekanalen](https://technet.microsoft.com/library/mt455210.aspx).
<!--- - Automatic deployment rules with Office 365 apps (have Office 365 Client selected in the set of available products). --->

<!---You can take the following actions on the dashboard:
- --->

Aan de bovenkant van het dashboard, gebruiken de **verzameling** vervolgkeuzelijst instelling voor het filteren van dashboardgegevens door leden van een specifieke verzameling.

### <a name="display-data-in-the-office-365-client-management-dashboard"></a>Gegevens weergeven in het dashboard clientbeheer voor Office 365
De gegevens die worden weergegeven in het dashboard Office 365-clientbeheer afkomstig is van hardware-inventaris. Hardware-inventaris moet zijn ingeschakeld en moet u de **Office 365 ProPlus configuraties** hardware-inventarisklasse voordat gegevens worden weergegeven in het dashboard.
#### <a name="to-display-data-in-the-office-365-client-management-dashboard"></a>Gegevens weergeven in het dashboard clientbeheer voor Office 365
1. Hardware-inventaris inschakelen als deze nog niet is ingeschakeld. Zie voor meer informatie, [hardware-inventaris configureren](\sccm\core\clients\manage\configure-hardware-inventory).
2. Navigeer in de Configuration Manager-console naar **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  
3. Klik op **Eigenschappen** in het tabblad **Start** , in de groep **Eigenschappen**.  
4. Klik in het dialoogvenster **Standaardclientinstellingen** op **Hardware-inventarisatie**.  
5. Klik in de lijst **Apparaatinstellingen** op **Klassen instellen**.  
6. In de **Hardware-Inventarisklassen** in het dialoogvenster Selecteer **Office 365 ProPlus configuraties**.  
7.  Klik op **OK** om uw wijzigingen op te slaan en het dialoogvenster **Hardware-inventarisklassen** te sluiten.  
Het dashboard Office 365-clientbeheer start weergeven van gegevens, zoals hardware-inventaris wordt gerapporteerd.

## <a name="deploy-office-365-updates-with-configuration-manager"></a>Office 365-updates met Configuration Manager implementeren
Gebruik de volgende stappen voor het implementeren van updates voor Office 365 met Configuration Manager:

1.  [Controleer of de vereisten](https://technet.microsoft.com/library/mt628083.aspx) voor het gebruik van Configuration Manager voor het beheren van updates voor Office 365-clients in de **vereisten voor het beheren van updates voor Office 365-clients met behulp van Configuration Manager** gedeelte van het onderwerp.  

2.  [Configureren van software-updatepunten](../get-started/configure-classifications-and-products.md) synchroniseren van de client Office 365-updates. Stel **Updates** voor de classificatie en selecteer **Office 365 Client** voor het product. Mogelijk moet u ten minste één keer voordat het product Office 365-Client beschikbaar is voor u om te kiezen voor software-updates synchroniseren. U moet software-updates synchroniseren na het configureren van de software-updatepunten te gebruiken de **Updates** classificatie.
3.  Office 365 clients toestaat te ontvangen van updates van Configuration Manager. U kunt dit doen met Configuration Manager-clientinstellingen of Groepsbeleid gebruiken. Een van de volgende methoden gebruiken om de client inschakelt:  
    - Methode 1: Beginnend in Configuration Manager versie 1606, kunt u de instelling voor het beheren van de clientagent voor Office 365 Configuration Manager-client. Nadat u deze instelling niet configureren en implementeren van updates voor Office 365, wordt de Configuration Manager-clientagent communiceert met de clientagent voor Office 365 voor Office 365-updates downloaden van een distributiepunt en deze installeren. Configuration Manager-inventarisatie van Office 365 ProPlus Client-instellingen.
      1.  Klik in de Configuration Manager-console op **beheer** > **overzicht** > **clientinstellingen**.  

      2.  Open de juiste apparaatstuurprogramma-instellingen voor de clientagent. Zie voor meer informatie over de standaardbeleidsregels en aangepaste clientinstellingen [clientinstellingen configureren in System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

      3.  Klik op **Software-Updates** en selecteer **Ja** voor de **zodat het beheer van de Clientagent voor Office 365** instelling.  

    - Methode 2: [Office 365-clients kunnen de updates ontvangen](https://technet.microsoft.com/library/mt628083.aspx#BKMK_EnableClient) van Configuration Manager met behulp van de Office Deployment Tool of Groepsbeleid.  

4. [De Office 365-updates implementeert](deploy-software-updates.md) naar clients.   

> [!Important]
> Wanneer u een Office 365-client met meer dan één taal hebt en downloaden van updates voor minder talen, wordt de updates niet geïnstalleerd. Bijvoorbeeld, Stel dat u hebt een Office 365-client en-us en nl-nl. Op de siteserver, u dowload en implementeren van alleen en-us inhoud voor een Office 365-update van toepassing. Wanneer de gebruiker wordt de installatie voor deze update is gestart vanaf Software Center, wordt de update vastlopen tijdens het downloaden van de inhoud. U moet downloaden en implementeren van updates in dezelfde clienttalen als de Office 365-clients.  


## <a name="add-other-languages-for-office-365-update-downloads"></a>Downloads voor andere talen voor Office 365-updatebestanden toevoegen
U kunt ondersteuning voor Configuration Manager-updates voor alle talen die worden ondersteund door Office 365 ongeacht of ze worden ondersteund in Configuration Manager te downloaden vanaf in Configuration Manager versie 1610, toevoegen.
> [!IMPORTANT]  
> Configureren van extra talen voor Office 365-update is een instelling van de gehele site. Nadat u de talen die met behulp van de volgende procedure hebt toegevoegd, worden alle Office 365-updates worden gedownload in de desbetreffende talen, evenals de talen die u op de pagina taal selecteren in de wizards downloaden van Software-Updates of Software-Updates implementeren selecteert.

### <a name="to-add-support-to-download-updates-for-additional-languages"></a>Ondersteuning voor downloaden van updates voor extra talen toevoegen
Gebruik de volgende procedure op de centrale beheersite of zelfstandige primaire site waar de sitesysteemrol van software-update-punt is geïnstalleerd.
1. Vanaf een opdrachtprompt, typ *wbemtest* als een gebruiker met beheerdersrechten de Windows Management Instrumentation Tester te openen.
2. Klik op **Connect**, en typ vervolgens *root\sms\site_&lt;siteCode&gt;*.
3. Klik op **Query**, en voer de volgende query: *#42; & selecteren uit SMS_SCI_Component waar NaamOnderdeel = "SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![WMI-query](..\media\1-wmiquery.png)
4. Dubbelklik in het deelvenster met resultaten op het object met de sitecode voor de centrale beheersite of zelfstandige primaire site.
5. Selecteer de **eigenschappen** eigenschap, klikt u op **eigenschap bewerken**, en klik vervolgens op **weergave ingesloten**.
![Eigenschappeneditor](..\media\2-propeditor.png)
6. Elk object vanaf het eerste queryresultaat openen totdat u de categorie met **AdditionalUpdateLanguagesForO365** voor de **PropertyName** eigenschap.
7. Selecteer **Value2** en klikt u op **eigenschap bewerken**.  
![De eigenschap Value2 bewerken](..\media\3-queryresult.png)
8. Toevoegen van extra talen voor de **Value2** eigenschap en klik op **eigenschap opslaan**.  
Bijvoorbeeld, pt-pt (voor Portugees - Portugal), af-za (voor Afrikaans - Zuid-Afrika), nn Nee (voor Noors (Nynorsk) - Noorwegen), enz.  
![Talen in de eigenschap Editor toevoegen](..\media\4-props.png)  
9. Klik op **sluiten**, klikt u op **sluiten**, klikt u op **eigenschap opslaan**, klikt u op **Object opslaan** (als u op **sluiten** hier de waarden worden verwijderd), klikt u op **sluiten**, en klik vervolgens op **sluiten** om af te sluiten van de Windows Management Intstrumentation Tester.
10. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer** > **Updates voor Office 365**.
11. Als u Office 365-updates downloaden, wordt nu de updates gedownload in de taal die u in de wizard selecteert en de talen die u in deze procedure hebt geconfigureerd. Controleer of de updates in deze talen gedownload, gaat u naar de pakketbron voor de update en zoek naar bestanden met de taal in de bestandsnaam.  
![Bestandsnamen met extra talen](..\media\5-verification.png)


## <a name="change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager"></a>Het update-kanaal wijzigen nadat u Office 365-clients om updates te ontvangen van Configuration Manager inschakelen
Om het kanaal update wijzigen nadat u Office 365-clients om updates te ontvangen van Configuration Manager hebt ingeschakeld, kunt u Groepsbeleid gebruiken om te distribueren van een wijziging in het register sleutelwaarde op Office 365-clients. Wijzig de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration\CDNBaseUrl** registersleutel voor een van de volgende waarden:

- Huidige kanaal:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60

- Uitgestelde kanaal:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114

- De eerste versie voor huidige kanaal:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be

- De eerste versie voor uitgestelde Channel:  
  **CDNBaseUrl** = http &#58;//officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf

## <a name="deploy-office-365-apps"></a>Office 365-apps implementeren  
Vanaf versie 1702, kunt u het installatieprogramma van Office 365 starten vanuit het dashboard clientbeheer voor Office 365 om de installatie van de App voor Office 365 gemakkelijker problemen. De wizard laat u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud voor de levering van bedrijfsnetwerken (CDN), en maken en implementeren van de scripttoepassing van een voor de bestanden.

Dit is vooral nuttig zijn omdat Office 365-updates niet van toepassing op clients zonder Office 365 geïnstalleerd zijn. Vóór versie 1702 Office 365 om apps te installeren voor het eerst op clients, moet u handmatig download Office 365 Deployment Tool (ODT) en de Office 365 installatiebronbestanden, met inbegrip van alle de taalpakketten die u nodig hebt, en de Configuration.xml waarmee de juiste versie van Office en channel genereren. Vervolgens moet u maken en implementeren van een verouderde pakket of een scripttoepassing voor clients om de Office 365-apps te installeren.

> [!NOTE]
> - De computer die het Office 365-installatieprogramma uitvoert, moet toegang tot Internet hebben.  
> - De gebruiker die het Office 365-installatieprogramma uitvoert moet beschikken over **lezen** en **schrijven** toegang tot de locatie van inhoud share is opgegeven in de wizard.
> - Als u een foutmelding 404 downloaden ontvangt, Kopieer de volgende bestanden naar de map % temp % van de gebruiker:
>    - [releasehistory.XML](http://officecdn.microsoft.com.edgesuite.net/wsus/releasehistory.cab)
>    - [o365client_32bit.XML](http://officecdn.microsoft.com/pr/wsus/ofl.cab)  
> - Nadat u maken en implementeren van Office 365-toepassingen met behulp van het installatieprogramma van Office 365, beheren Configuration Manager de Office-updates standaard. Zie voor het inschakelen van Office 365-clients om updates te ontvangen van Configuration Manager [implementeren Office 365 bijgewerkt met Configuration Manager](#deploy-office-365-updates-with-configuration-manager).

### <a name="to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard"></a>Office 365-apps implementeren op clients via het dashboard clientbeheer voor Office 365
1. Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.
2. Klik op **Office 365 Installer** in het rechter deelvenster. De Wizard Office 365-clientinstallatie wordt geopend.
3. Op de **toepassingsinstellingen** pagina, Geef een naam en beschrijving in voor de app, voer de downloadlocatie voor de bestanden en klik vervolgens op **volgende**. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier &#92; &#92; *server*&#92; *delen*.
4. Op de **clientinstellingen importeren** pagina, kiezen of de clientinstellingen voor Office 365 importeren uit een bestaand XML-configuratiebestand of geef handmatig de instellingen en klik vervolgens op **volgende**.  

    Wanneer u een bestaand configuratiebestand hebt, geef de locatie voor het bestand en gaat u naar stap 7. Houd er rekening mee dat de locatie moet worden opgegeven in het formulier &#92; &#92; *server*&#92; *delen*&#92;* bestandsnaam*. XML.
5. Op de **clientproducten** pagina, selecteert u de Office 365-pakket dat u gebruikt, selecteer de toepassingen die u wilt opnemen, selecteert u extra Office-producten die moeten worden opgenomen en klik vervolgens op **volgende**.
6. Op de **clientinstellingen** pagina, kiest u de instellingen wilt opnemen en klik op **volgende**.
7. Op de **implementatie** pagina, kies of u de toepassing te implementeren en klik vervolgens op **volgende**.  
Als u ervoor kiest om niet te implementeren van het pakket in de wizard, gaat u naar stap 9.
8. Configureer de rest van de wizardpagina's zoals u zou voor een typische toepassingsimplementatie doen. Zie voor meer informatie, [maken en implementeren van een toepassing](/sccm/apps/get-started/create-and-deploy-an-application).
9. Voltooi de wizard.
10. U kunt implementeren of de toepassing te bewerken, net zoals u zou hebben met een andere toepassing in Configuration Manager uit **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**.   

> [!IMPORTANT]
> De Office 365-app die u maakt en implementeert met behulp van de Wizard toepassing van Office 365 in Configuration Manager wordt niet automatisch worden beheerd door Configuration Manager totdat u de **zodat het beheer van de Office 365-Client opnieuw** clientagent voor software-updates instellen. Zie voor meer informatie, [over clientinstellingen](/sccm/core/clients/deploy/about-client-settings).

>[!NOTE]
>Nadat u Office 365-apps implementeert, kunt u regels voor automatische implementatie voor het onderhouden van de apps maken. Voor het maken van een regel voor automatische implementatie voor Office 365-apps, klikt u op **maken van een ADR** van het dashboard voor Office 365-clientbeheer en selecteer **Office 365 Client** wanneer u het product. Zie voor meer informatie [software-updates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).

<!--- You can create an Office 365 app without using the Office 365 Installation Wizard. To do this, you use the Office 2016 Deployment Tool (ODT) to download Office installation source files to a network share, generate Configure.xml that specifies the correct Office version and channel, and so on. Then, create an app for the files using the normal app management process.
> [!Note]
> The Office 365 Installation Wizard was introduced in Configuration Manager version 1702 and provides an easy way to create Office 365 apps.

- [Download the Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center.  
- Review the [configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx).

You can create an application just as you would with any other application in Configuration Manager from **Software Library** > **Overview** > **Application Management** > **Applications**. For details, see [Create and deploy an application](/sccm/apps/get-started/create-and-deploy-an-application).
--->

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->

