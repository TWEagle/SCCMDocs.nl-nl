---
title: Office 365 ProPlus-updates beheren
titleSuffix: Configuration Manager
description: Configuration Manager worden gesynchroniseerd voor Office 365-clientupdates van de WSUS-catalogus naar de siteserver om updates beschikbaar om te implementeren op clients.
keywords: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 02/16/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.openlocfilehash: 2f765df84b94524cf56f6d1d9e051157f1a325ef
ms.sourcegitcommit: 45ff3ffa040eada5656b17f47dcabd3c637bdb60
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/23/2018
---
# <a name="manage-office-365-proplus-with-configuration-manager"></a>Beheren van Office 365 ProPlus met Configuration Manager

Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Configuration Manager kunt u Office 365 ProPlus-apps in de volgende manieren beheren:

- [Office 365 Client Management dashboard](#office-365-client-management-dashboard): Vanaf Configuration Manager versie 1610, kunt u informatie over Office 365 client vanuit het Office 365 Client Management dashboard bekijken.    

- [Office 365-apps implementeren](#deploy-office-365-apps): Vanaf versie 1702, kunt u het Office 365-installatieprogramma starten vanuit het dashboard beheer voor Office 365-Client om de initiële Office 365-App-installatie eenvoudiger ervaring. De wizard kunt u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud levering bedrijfsnetwerken (CDN), en maken en implementeren van de toepassing van een script met de inhoud.    

- [Office 365-updates implementeren](#deploy-office-365-updates): Vanaf versie 1602 van Configuration Manager, kunt u updates voor Office 365-clients beheren met behulp van de werkstroom voor software-update. Wanneer Microsoft publiceert een nieuwe Office 365-clientupdate voor de Office Content Delivery Network (CDN), publiceert Microsoft ook een updatepakket voor Windows Server Update Services (WSUS). Configuration Manager worden gesynchroniseerd met de Office 365-clientupdate van de WSUS-catalogus naar de siteserver, is de update beschikbaar om te implementeren op clients.    

- [Toevoegen van talen voor Office 365-updatebestanden downloads](#add-languages-for-office-365-update-downloads): U kunt ondersteuning voor Configuration Manager voor alle talen die worden ondersteund door Office 365-updates te downloaden vanaf Configuration Manager versie 1610 kan toevoegen. Betekenis Configuration Manager geen ondersteuning voor de taal als Office 365 biedt. U moet vóór de Configuration Manager versie 1610 downloaden en implementeren van updates in de dezelfde talen op Office 365-clients geconfigureerd. 

- [Wijzigen van het kanaal update](#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager): U kunt Groepsbeleid gebruiken voor het distribueren van een wijziging in het register sleutelwaarde op Office 365-clients om de update-kanaal te wijzigen.


## <a name="office-365-client-management-dashboard"></a>Dashboard voor Office 365-clientbeheer  
Het beheer van Office 365 Client dashboard biedt grafieken voor de volgende informatie:

- Aantal Office 365-clients
- Versies van Office 365-client
- Clienttalen voor Office 365
- Office 365 client kanalen     
  Zie voor meer informatie [overzicht van de update voor Office 365 ProPlus kanalen](https://technet.microsoft.com/library/mt455210.aspx).

Het beheer van Office 365 Client als dashboard wilt weergeven in de Configuration Manager-console, gaat u naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**. Aan de bovenkant van het dashboard gebruiken de **verzameling** Vervolgkeuze-instelling voor het filteren van de dashboardgegevens door leden van een specifieke verzameling.

### <a name="display-data-in-the-office-365-client-management-dashboard"></a>Gegevens weergeven in het dashboard voor Office 365-clientbeheer
De gegevens die wordt weergegeven in het dashboard voor beheer van Office 365 Client afkomstig van hardware-inventaris. Hardware-inventaris inschakelen en selecteer de **Office 365 ProPlus configuraties** hardware-inventarisklasse voor gegevens om weer te geven in het dashboard.
#### <a name="to-display-data-in-the-office-365-client-management-dashboard"></a>Gegevens weergeven in het dashboard voor Office 365-clientbeheer
1. Hardware-inventarisatie inschakelen als deze nog niet is ingeschakeld. Zie voor meer informatie [hardware-inventaris configureren](\sccm\core\clients\manage\configure-hardware-inventory).
2. Navigeer in de Configuration Manager-console naar **beheer** > **clientinstellingen** > **Standaardclientinstellingen**.  
3. Klik op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.  
4. Klik in het dialoogvenster **Standaardclientinstellingen** op **Hardware-inventarisatie**.  
5. Klik in de lijst **Apparaatinstellingen** op **Klassen instellen**.  
6. In de **Hardware-Inventarisklassen** dialoogvenster, **Office 365 ProPlus configuraties**.  
7.  Klik op **OK** om uw wijzigingen op te slaan en het dialoogvenster **Hardware-inventarisklassen** te sluiten. <br/>Het dashboard voor beheer van Office 365-Client wordt gestart om gegevens weer te geven als hardware-inventaris wordt gerapporteerd.

## <a name="deploy-office-365-apps"></a>Office 365-apps implementeren  
Vanaf versie 1702, start u het installatieprogramma van Office 365 vanuit het Office 365 Client Management dashboard voor de eerste installatie van de Office 365-App. De wizard kunt u Office 365-installatie-instellingen configureren, bestanden downloaden van inhoud levering bedrijfsnetwerken (CDN), en maken en implementeren van de toepassing van een script voor de bestanden. Nadat Office 365 is geïnstalleerd op clients, zijn Office 365-updates niet van toepassing.

Voor eerdere versies van Configuration Manager, moet u rekening houden met de volgende stappen voor het installeren van Office 365-apps voor het eerst op clients:
- Office 365 Deployment Tool (ODT) downloaden
- Download de bronbestanden voor de Office 365-installatie, inclusief alle van de taalpakketten die u nodig hebt.
- De Configuration.xml waarmee de juiste versie van Office en kanaal worden gegenereerd.
- Maak en implementeer een verouderde pakket of een scripttoepassing voor clients in de Office 365-apps te installeren.

### <a name="requirements"></a>Vereisten
- De computer die het Office 365-installatieprogramma uitvoert, moet toegang tot Internet hebben.  
- De gebruiker die het Office 365-installatieprogramma uitvoert moet beschikken over **lezen** en **schrijven** toegang tot de locatie van inhoud share is opgegeven in de wizard.
- Als er een fout bij het 404 downloaden, Kopieer de volgende bestanden naar de map % temp % van de gebruiker:
  - [releasehistory.xml](http://officecdn.microsoft.com/pr/wsus/releasehistory.cab)
  - [o365client_32bit.xml](http://officecdn.microsoft.com/pr/wsus/ofl.cab)  


### <a name="to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard"></a>Office 365-apps implementeren op clients vanuit het dashboard voor Office 365-clientbeheer
1. Navigeer in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer**.
2. Klik op **Office 365 Installer** in het deelvenster rechtsboven. De Wizard Client installeren van Office 365 wordt geopend.
3. Op de **toepassingsinstellingen** pagina, Geef een naam en beschrijving voor de app, voer de downloadlocatie voor de bestanden en klik vervolgens op **volgende**. De locatie moet worden opgegeven als &#92; &#92; *server*&#92; *delen*.
4. Op de **clientinstellingen importeren** pagina, kiest u of de Office 365 client-instellingen importeren van een bestaande XML-configuratiebestand of geef handmatig de instellingen en klik vervolgens op **volgende**.  

    Wanneer u een bestaand configuratiebestand hebt, voer de locatie voor het bestand en gaat u verder met stap 7. U moet de locatie opgeven in het formulier &#92; &#92; *server*&#92; *delen*&#92; *bestandsnaam*. XML.
    > [!IMPORTANT]    
    > Het XML-configuratiebestand alleen moet bevatten [talen die worden ondersteund door de Office 365 ProPlus-client](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx).

5. Op de **clientproducten** pagina, selecteert u het Office 365-pakket dat u gebruikt. Selecteer de toepassingen die u wilt opnemen. Selecteer Extra Office-producten dat moeten worden opgenomen en klik vervolgens op **volgende**.
6. Op de **clientinstellingen** pagina, kiest u de instellingen die u wilt opnemen en klik op **volgende**.
7. Op de **implementatie** pagina, kies of u de toepassing implementeren en klik vervolgens op **volgende**. <br/>Als u niet voor de implementatie van het pakket in de wizard kiest, gaat u naar stap 9.
8. De rest van de wizardpagina's configureren zoals u zou voor een typische implementatie doen. Zie voor meer informatie [maken en implementeren van een toepassing](/sccm/apps/get-started/create-and-deploy-an-application).
9. Voltooi de wizard.
10. U kunt implementeren of bewerken van de toepassing van **softwarebibliotheek** > **overzicht** > **Toepassingsbeheer** > **toepassingen**.    

Nadat u maken en implementeren van Office 365-toepassingen met behulp van het Office 365-installatieprogramma, beheert Configuration Manager de Office-updates niet standaard. Zie voor het inschakelen van Office 365-clients om updates te ontvangen van Configuration Manager [implementeren Office 365-updates met Configuration Manager](#deploy-office-365-updates-with-configuration-manager).

>[!NOTE]
>Nadat u Office 365-apps implementeert, kunt u regels voor automatische implementatie voor het onderhouden van de apps kunt maken. Klik op om een regel voor automatische implementatie voor Office 365-apps **een ADR maakt** vanuit het dashboard clientbeheer voor Office 365. Selecteer **Office 365 Client** wanneer u kiest voor het product. Zie voor meer informatie [softwareupdates automatisch implementeren](/sccm/sum/deploy-use/automatically-deploy-software-updates).


## <a name="deploy-office-365-updates"></a>Office 365-updates implementeren
Vanaf Configuration Manager versie 1706 Office 365-clientupdates hebt verplaatst naar de **Office 365-clientbeheer** >**Office 365-Updates** knooppunt. Dit heeft geen invloed op de configuratie van de regel voor automatische implementatie. 

Gebruik de volgende stappen voor het implementeren van updates voor Office 365 met Configuration Manager:

1.  [Controleer de vereisten](https://technet.microsoft.com/library/mt628083.aspx) voor het gebruik van Configuration Manager voor het beheren van updates voor Office 365-clients in de **vereisten voor het gebruik van Configuration Manager voor het beheren van Office 365-clientupdates** sectie van het artikel.  

2.  [Configureren van software-updatepunten](../get-started/configure-classifications-and-products.md) synchroniseren van de client Office 365-updates. Stel **Updates** voor de classificatie en selecteer **Office 365 Client** voor het product. Software-updates synchroniseren na het configureren van de software-updatepunten gebruiken de **Updates** classificatie.
3.  Office 365-clients om updates te ontvangen van Configuration Manager inschakelen. Gebruik Configuration Manager-clientinstellingen of Groepsbeleid om te zorgen dat de client.   

    **Methode 1**: Vanaf Configuration Manager versie 1606, kunt u de Configuration Manager-client instellen voor het beheren van de clientagent voor Office 365. Nadat u deze instelling configureren en implementeren van updates voor Office 365, wordt de clientagent voor Configuration Manager-communiceert met de Office 365-clientagent voor Office 365-updates vanaf een distributiepunt downloaden en te installeren. Configuration Manager-inventarisatie van Office 365 ProPlus-Client-instellingen.    

      1.  Klik in de Configuration Manager-console op **beheer** > **overzicht** > **clientinstellingen**.  

      2.  Open de juiste apparaatstuurprogramma-instellingen voor de clientagent. Zie voor meer informatie over standaard en aangepaste clientinstellingen [het configureren van clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

      3.  Klik op **Software-Updates** en selecteer **Ja** voor de **beheer van de Office 365-Clientagent inschakelen** instelling.  

    **Methode 2**: [Inschakelen voor Office 365-clients om updates te ontvangen](https://technet.microsoft.com/library/mt628083.aspx#BKMK_EnableClient) uit Configuration Manager met behulp van de Office Deployment Tool of Groepsbeleid.  

4. [De Office 365-updates implementeren](deploy-software-updates.md) aan clients.   

> [!Important]
> U moet vóór de Configuration Manager versie 1610 downloaden en implementeren van updates in de dezelfde talen op Office 365-clients geconfigureerd. Bijvoorbeeld, Stel dat u hebt een Office 365-client die is geconfigureerd met het en-us en nl-nl talen. Op de siteserver u downloaden en implementeren van alleen en-us inhoud voor een Office 365-update van toepassing. Wanneer de gebruiker wordt de installatie vanuit Software Center voor deze update is gestart, wordt de update tijdens het downloaden van de inhoud voor nl-nl vastloopt.   

## <a name="restart-behavior-and-client-notifications-for-office-365-updates"></a>Opnieuw opstarten van gedrag en client meldingen voor updates voor Office 365
Wanneer u een update op een Office 365-client implementeert, zijn de meldingen van gedrag en de client opnieuw opstarten verschillend afhankelijk van welke versie van Configuration Manager die u hebt. De volgende tabel bevat informatie over de eindgebruikerservaring wanneer de client een Office 365-update ontvangt:

|Versie van Configuration Manager |Eindgebruikerservaring|  
|----------------|---------------------|
|Voorafgaand aan 1610|Een opnieuw opstarten-vlag is ingesteld en de update is geïnstalleerd nadat de computer opnieuw is opgestart.|
|1610|Office 365-apps worden afgesloten zonder waarschuwing voordat u de update installeert|
|1610 met update <br/>1702|Een opnieuw opstarten-vlag is ingesteld en de update is geïnstalleerd nadat de computer opnieuw is opgestart.|
|1706|De client ontvangt een pop- en in-app-meldingen, evenals een dialoogvenster aftelling voordat u de update installeert.|

> [!Important]
> U start in Configuration Manager versie 1706, houd rekening met de volgende details:
>
>- Een pictogram wordt weergegeven in het systeemvak op de taakbalk voor vereiste apps waarbij de deadline binnen 48 uur in de toekomst en inhoud van de update is gedownload. 
>- Een dialoogvenster aftelling worden weergegeven voor vereiste apps waarbij de deadline binnen 7.5 uur in de toekomst en de update is gedownload. De gebruiker kan het dialoogvenster aftelling maximaal drie keer vóór de deadline uitstellen. Als uitgesteld, wordt de aftelling na twee uur opnieuw weergegeven. Als dat niet het uitgesteld, er een aftelling 30 minuten en update wordt geïnstalleerd wanneer de aftelling is verlopen.
>- Een pop-upbericht mogelijk niet weergegeven totdat de gebruiker op het pictogram in het systeemvak klikt. Bovendien, als het systeemvak minimale ruimte heeft, het meldingspictogram mogelijk niet meer zichtbaar tenzij de gebruiker opent of het systeemvak breidt. 
>- Het dialoogvenster melding en aftelling kan worden gestart terwijl de gebruiker is niet actief werk op het apparaat, bijvoorbeeld wanneer het apparaat is vergrendeld, 's nachts, zodat het mogelijk is de Office-apps die zijn uitgevoerd op het apparaat kunnen worden afgedwongen dicht bij de update te installeren. Voordat de app wordt gesloten, slaat Office app-gegevens om gegevensverlies te voorkomen. 
>- Als de deadline in de afgelopen of geconfigureerd is dat deze zo snel mogelijk worden gestart, kan waarop Office-apps geforceerd worden sluit zonder de meldingen. 
>- Als de gebruiker een Office-update vóór de deadline geïnstalleerd, wordt in Configuration Manager geverifieerd dat de update wordt geïnstalleerd wanneer de deadline wordt bereikt. Als de update niet op het apparaat gevonden is, wordt de update is geïnstalleerd. 
>- De melding in de app-balk niet wordt weergegeven op een Office-app die wordt uitgevoerd voordat de update wordt gedownload. Nadat de update is gedownload, de in-app-melding wordt weergegeven voor de zojuist geopende apps.
>- Voor Office-updates geactiveerd door een servicevenster of gepland voor buiten kantooruren, is het mogelijk dat Office-apps uitgevoerd wordt afgedwongen mogelijk dicht bij de update te installeren zonder meldingen. 



## <a name="add-languages-for-office-365-update-downloads"></a>Talen voor het downloaden van de Office 365-update toevoegen
U kunt ondersteuning voor Configuration Manager-updates voor de talen die worden ondersteund door Office 365, ongeacht of ze worden ondersteund in Configuration Manager te downloaden vanaf Configuration Manager versie 1610 kan toevoegen.    

> [!IMPORTANT]  
> Extra talen voor Office 365-updates configureren is een gehele site-instelling. Nadat u de talen die met de volgende procedure hebt toegevoegd, alle Office 365-updates worden gedownload in deze talen, evenals de talen die u selecteert op de **taalselectie** pagina in de wizards downloaden van Software-Updates of Software-Updates implementeren.

### <a name="to-add-support-to-download-updates-for-additional-languages"></a>Ondersteuning voor het downloaden van updates voor extra talen toevoegen
Gebruik de volgende procedure op het software-updatepunt op de centrale beheersite of zelfstandige primaire site.
1. Vanaf een opdrachtprompt, typ *wbemtest* als gebruiker met beheerdersrechten de Windows Management Instrumentation Tester te openen.
2. Klik op **Connect**, en typ vervolgens *root\sms\site_&lt;siteCode&gt;*.
3. Klik op **Query**, en voer de volgende query: *&#42; selecteren uit SMS_SCI_Component waar componentname = "SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![WMI-query](..\media\1-wmiquery.png)
4. Dubbelklik in het deelvenster met resultaten op het object met de sitecode voor de centrale beheersite of zelfstandige primaire site.
5. Selecteer de **eigenschappen** eigenschap, klikt u op **eigenschap bewerken**, en klik vervolgens op **weergave ingesloten**.
![Eigenschappeneditor](..\media\2-propeditor.png)
6. Elk object vanaf het eerste queryresultaat open totdat u de categorie met **AdditionalUpdateLanguagesForO365** voor de **PropertyName** eigenschap.
7. Selecteer **Value2** en klik op **eigenschap bewerken**.  
![De eigenschap Value2 bewerken](..\media\3-queryresult.png)
8. Toevoegen van extra talen voor de **Value2** eigenschap en klikt u op **eigenschap opslaan**. <br/> Bijvoorbeeld, pt-pt (voor Portugees - Portugal), af-za (voor Afrikaans - Zuid-Afrika), nn Nee (voor Noors (Nynorsk) - Noorwegen), enzovoort.  
![Talen in Eigenschappeneditor toevoegen](..\media\4-props.png)  
9. Klik op **sluiten**, klikt u op **sluiten**, klikt u op **eigenschap opslaan**, klikt u op **Object opslaan** (als u op **sluiten** hier de waarden worden verwijderd), klikt u op **sluiten**, en klik vervolgens op **sluiten** om af te sluiten van de Windows Management Instrumentation Tester.
10. Ga in de Configuration Manager-console naar **softwarebibliotheek** > **overzicht** > **Office 365-clientbeheer** > **Office 365-Updates**.
11. Wanneer u updates voor Office 365 hebt gedownload, worden de updates nu gedownload in de talen die u selecteert in de wizard en geconfigureerd in deze procedure. Om te controleren of de updates in de juiste talen downloaden, gaat u naar de pakketbron voor de update en naar bestanden met de taal in de bestandsnaam zoeken.  
![Bestandsnamen met extra talen](..\media\5-verification.png)


## <a name="change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager"></a>Het kanaal update niet wijzigen nadat u Office 365-clients om updates te ontvangen van Configuration Manager inschakelen
De update om kanaal te wijzigen nadat u Office 365-clients te ontvangen van updates van Configuration Manager, gebruikt u Groepsbeleid voor het distribueren van een registerwijziging sleutelwaarde Office 365-clients ingeschakeld. Wijzig de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration\CDNBaseUrl** registersleutel voor een van de volgende waarden:

- Maandelijks kanaal <br/>
<i>(voorheen huidige kanaal) </i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60

- Kanaal puntkomma per jaar <br/>
<i>(voorheen uitgesteld kanaal) </i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114

- Maandelijks kanaal (doel)<Br/>
 <i>(voorheen eerste Release voor huidige kanaal) </i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be

- Puntkomma per jaar kanaal (doel) <br/>
<i>(voorheen eerste Release voor uitgesteld kanaal) </i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf
<!--the channel names changed in Sept 2017- https://docs.microsoft.com/en-us/DeployOffice/overview-of-update-channels-for-office-365-proplus?ui=en-US&rs=en-US&ad=US>


<!--- You can create an Office 365 app without using the Office 365 Installation Wizard. To do this, you use the Office 2016 Deployment Tool (ODT) to download Office installation source files to a network share, generate Configure.xml that specifies the correct Office version and channel, and so on. Then, create an app for the files using the normal app management process.
> [!Note]
> The Office 365 Installation Wizard was introduced in Configuration Manager version 1702 and provides an easy way to create Office 365 apps.

- [Download the Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center.  
- Review the [configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx).

You can create an application just as you would with any other application in Configuration Manager from **Software Library** > **Overview** > **Application Management** > **Applications**. For details, see [Create and deploy an application](/sccm/apps/get-started/create-and-deploy-an-application).
--->

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->
