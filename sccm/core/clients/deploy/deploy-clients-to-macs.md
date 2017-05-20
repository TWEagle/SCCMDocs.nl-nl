---
title: Mac-clients implementeren | Microsoft-documenten
description: Informatie over het implementeren van clients op Mac-computers in System Center Configuration Manager.
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e46ad501-5d73-44ac-92de-0de14ef72b83
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6a6137fa978e1ea28aefea2aea4e29ba661efd6
ms.openlocfilehash: 6ce212c6745b70a47553891e5dbc124b4c4e50fa
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-clients-to-macs"></a>Clients implementeren in Macs

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit onderwerp wordt beschreven hoe u kunt implementeren en onderhouden van de Configuration Manager-client op Mac-computers. Zie voor meer informatie over wat u configureren moet voordat u clients implementeert op Mac-computers, [implementatie van clientsoftware op Macs voorbereiden](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients).

Wanneer u een nieuwe client voor Mac-computers installeert, moet u wellicht ook updates van Configuration Manager naar aanleiding van de nieuwe clientinformatie in de Configuration Manager-console installeren.

In deze procedures hebt u twee opties voor het installeren van clientcertificaten. Meer informatie over clientcertificaten voor Macs in [implementatie van clientsoftware op Macs voorbereiden](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#certificate-requirements).  

-   Gebruik Configuration Manager-inschrijving door het [CMEnroll-hulpprogramma](#install-the-client-and-then-enroll-the-client-certificate-on-the-mac). Het inschrijvingsproces ondersteunt geen automatische certificaatsvernieuwing, daarom moet u Mac-computers opnieuw inschrijven voordat het geïnstalleerde certificaat verlopen is.    

-   [Gebruik een certificaat aanvragen en -installatiemethode die onafhankelijk is van Configuration Manager](#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager). 

>[!IMPORTANT]
>  Voor het implementeren van de client op Mac OS Sierra-apparaten, moet de onderwerpnaam van het certificaat worden correct geconfigureerd, bijvoorbeeld met behulp van de FQDN-naam van de beheerpuntserver.


## <a name="configure-client-settings-for-enrollment"></a>Configureren van clientinstellingen voor inschrijving  
 U moet gebruiken de [standaardclientinstellingen](../../../core/clients/deploy/about-client-settings.md) configureren van inschrijving voor Mac-computers; u kunt geen aangepaste clientinstellingen gebruiken.  

 Dit is vereist voor Configuratiebeheer aanvragen en installeer het certificaat op de Mac.  

### <a name="to-configure-the-default-client-settings-for-configuration-manager-to-enroll-certificates-for-macs"></a>De standaardclientinstellingen voor Configuration Manager om certificaten te schrijven voor Macs configureren  

1.  Kies in de Configuration Manager-console **beheer** >  **clientinstellingen** > **Standaardclientinstellingen**.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  Selecteer de **inschrijving** uit en configureert u deze instellingen:  

    1.  **Gebruikers toestaan te schrijven mobiele apparaten en Mac-computers: Ja**  

    2.  **Inschrijvingsprofiel:** Kies **profiel instellen**.  

6.  In de **Inschrijvingsprofiel voor mobiele apparaten** dialoogvenster Kies **maken**.  

7.  Geef in het dialoogvenster **Inschrijvingsprofiel maken** een naam in voor dit inschrijvingsprofiel en configureer dan de **Beheersitecode**. Selecteer de primaire Configuration Manager-site die de beheerpunten bevat die de Mac-computers zullen beheren.  

    > [!NOTE]  
    >  Als u de site niet kunt selecteren, controleer dan dat ten minste één beheerpunt in de site is geconfigureerd om mobiele apparaten te ondersteunen.  

8.  Kies **toevoegen**.  

9. In de **certificeringsinstantie voor mobiele apparaten toevoegen** dialoogvenster Selecteer de server van de certificeringsinstantie (certificeringsinstantie) die certificaten voor Mac-computers uitgeeft.  

10. In de **Inschrijvingsprofiel maken** in het dialoogvenster Selecteer sjabloon die u hebt gemaakt in stap 3 van de Mac-computer het certificaat.  

11. Klik op **OK** sluit de **Inschrijvingsprofiel** in het dialoogvenster en vervolgens de **Standaardclientinstellingen** in het dialoogvenster.  

    > [!TIP]  
    >  Als u wijzigen van het interval voor clientbeleid wilt, gebruikt u **pollinginterval voor clientbeleid** in de **clientbeleid** groep voor client-instelling.  

 Alle gebruikers zullen worden geconfigureerd met deze instellingen de volgende keer dat deze clientbeleid downloaden. Zie voor het initiëren van ophaalbeleid voor één client [ophalen van beleid initiëren voor een Configuration Manager-Client](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval).  

 Naast de inschrijvingsclientinstellingen dient ervoor te zorgen dat u de volgende clientapparaatinstellingen hebt geconfigureerd:  

-   **Hardware-inventaris**: Schakel en configureer deze als u wilt verzamelen van hardware-inventaris van Mac- en Windows clientcomputers. Zie voor meer informatie [het uitbreiden van hardware-inventaris in System Center Configuration Manager](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

-   **Instellingen voor naleving**: Schakel en configureer deze als u wilt evalueren en herstellen van instellingen op Mac- en Windows-clientcomputers. Zie voor meer informatie [plannen en configureren van instellingen voor naleving](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md).  

> [!NOTE]  
>  Zie voor meer informatie over Configuration Manager-clientinstellingen [clientinstellingen configureren in System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).  

## <a name="download-the-client-source-files-for-macs"></a>Download de clientbronbestanden voor Macs  

1.  Download het bestandspakket voor Mac OS X-clients, **ConfigmgrMacClient.msi**, en sla het op een computer op waarop Windows wordt uitgevoerd.  

     Dit bestand wordt niet geleverd op de installatiemedia van Configuration Manager. U kunt dit bestand downloaden via het [Microsoft Downloadcentrum](http://go.microsoft.com/fwlink/?LinkID=525184).  

2.  Voer op de Windows-computer **ConfigmgrMacClient.msi** om op te halen van de Mac-clientpakket, Macclient.dmg naar een map op de lokale schijf (standaard **C:\Program Files (x86) \Microsoft\System Center 2012 Configuration Manager Mac Client\\**).  

3.  Kopieer het bestand Macclient.dmg naar een map op de Mac-computer.  

4.  Voer op de Mac-computer het Macclient.dmg-bestand om de bestanden naar een map op de lokale schijf te pakken.  

5.  Zorg er in de map voor dat de bestanden Ccmsetup en CMClient.pkg zijn uitgepakt en dat er een map met als naam Hulpprogramma's wordt aangemaakt die de hulpprogramma's CMDiagnostics,  CMUninstall, CMAppUtil en CMEnroll bevat.

    -  **Ccmsetup**: De Configuration Manager-client installeert op uw Mac-computers.  

    -   **CMDiagnostics**: Verzamelt diagnostische informatie met betrekking tot de Configuration Manager-client op uw Mac-computers.  

    -   **CMUninstall**: Hiermee verwijdert u de client van Mac-computers.  

    -   **CMAppUtil**: Apple-toepassingspakketten converteert naar een formaat dat kan worden geïmplementeerd als een Configuration Manager-toepassing.  

    -   **CMEnroll**: Vraagt en installeert het clientcertificaat voor Mac-computer zodat u kunt dan de Configuration Manager-client installeren.   

## <a name="install-the-client-and-then-enroll-the-client-certificate-on-the-mac"></a>Installeer de client en schrijf het clientcertificaat op de Mac  

U kunt afzonderlijke clients inschrijven met de [Inschrijvingswizard voor Mac-Computer](#enroll-the-client-with-the-mac-computer-enrollment-wizard).

Gebruik voor automatisering die kan worden ingeschreven van veel clients, de [CMEnroll-hulpprogramma](#client-and-certificate-automation-with-cmenroll).   


###  <a name="enroll-the-client-with-the-mac-computer-enrollment-wizard"></a>De client met de Inschrijvingswizard voor Mac-Computer inschrijven  

1.  Nadat u klaar bent met het installeren van de client, wordt de wizard inschrijving Computer wordt geopend. Als de wizard niet wordt geopend, of als u deze per ongeluk hebt gesloten, klikt u op **inschrijven** van de **Configuration Manager** voorkeurspagina om deze te openen.  

2.  Geef op de tweede pagina van de wizard:  

    -   **Gebruikersnaam** - De gebruikersnaam kan in de volgende formaten staan:  

        -   'DOMEIN\naam'. Voorbeeld: 'contoso\mnorth'  

        -   'user@domain'. Bijvoorbeeld: 'mnorth@contoso.com'  

            > [!IMPORTANT]  
            >  Wanneer u een e-mailadres gebruiken om in te vullen de **gebruikersnaam** veld Configuration Manager automatisch maakt gebruik van de domeinnaam van het e-mailadres en de standaardnaam van de server van het inschrijvingsproxypunt om in te vullen de **servernaam** veld. Als deze domeinnaam en servernaam niet overeenkomt met de naam van de server van het inschrijvingsproxypunt, laat u uw gebruikers de juiste naam moet worden gebruikt tijdens de inschrijving van hun Mac-computers.  

         De gebruikersnaam en het overeenkomstige wachtwoord moeten overeenkomen met een Active Directory-gebruikersaccount waaraan de machtigingen Lezen en Inschrijven zijn toegekend op het certificaatsjabloon voor de Mac-client.  

    -   **Wachtwoord** -Geef een overeenkomstig wachtwoord in voor de opgegeven gebruikersnaam.  

    -   **Servernaam** -Geef de naam van de server van het inschrijvingsproxypunt.  


### <a name="client-and-certificate-automation-with-cmenroll"></a>Automatisering van client en het certificaat met CMEnroll  

Gebruik deze procedure voor automatisering van de client en installatie aanvragen en de inschrijving van clientcertificaten met het CMEnroll-hulpprogramma. U moet een Active Directory-gebruikersaccount hebben om het hulpprogramma uit.

1.  Navigeer op de Mac-computer naar de map waar u de inhoud van het Macclient.dmg-bestand hebt uitgepakt.  

2.  Voer de volgende opdrachtregel in: **sudo ./ccmsetup**  

3.  Wacht tot u de boodschap **Installatie voltooid** ziet. Hoewel het installatieprogramma een boodschap toont dat u nu opnieuw moet opstarten, niet opnieuw opstarten en doorgaan met de volgende stap.  

4.  In de map hulpprogramma's op de Mac-computer, typt u het volgende: **sudo. / CMEnroll -s &lt;enrollment_proxy_server_name > - ignorecertchainvalidation -u &lt;gebruikersnaam ' >**  

    Nadat de client is geïnstalleerd, wordt de wizard Inschrijving voor Mac-computers geopend waarmee u de Mac-computer kunt inschrijven. Als u de client op deze wijze wilt inschrijven, raadpleegt u [To enroll the client by using the Mac Computer Enrollment Wizard](#BKMK_EnrollR2) in dit onderwerp.  

5. Typ het wachtwoord voor het Active Directory-gebruikersaccount.  Als u deze opdracht ingeeft, wordt u gevraagd twee wachtwoorden: De eerste vraag is voor de supergebruikersaccount de opdracht uit te voeren. De tweede vraag is voor de Active Directory-gebruikersaccount. De vragen zien er identiek uit, zorg er dus voor dat u ze in de juiste volgorde ingeeft.  

    De gebruikersnaam kan in de volgende formaten staan:  

    -   'DOMEIN\naam'. Voorbeeld: 'contoso\mnorth'  

    -   'user@domain'. Bijvoorbeeld: 'mnorth@contoso.com'  

     De gebruikersnaam en het overeenkomstige wachtwoord moeten overeenkomen met een Active Directory-gebruikersaccount waaraan de machtigingen Lezen en Inschrijven zijn toegekend op het certificaatsjabloon voor de Mac-client.  

     Voorbeeld: Als de naam van de server van het inschrijvingsproxypunt **server02.contoso.com**, en een gebruikersnaam van **contoso\mnorth** is machtigingen verleend voor de certificaatsjabloon voor Mac-client, typ het volgende: **sudo. / CMEnroll -s server02.contoso.com - ignorecertchainvalidation -u 'contoso\mnorth'**  

    > [!NOTE]  
    >  Als de gebruikersnaam een van de tekens bevat  **&lt;> "+=,** , mislukt de registratie. Een out-of-band-certificaat verkrijgen met een gebruikersnaam die deze tekens niet bevat.  
    >  
    >  Voor een vlotte gebruikerservaring kunt u een script schrijven voor de installatie en opdrachten zodat gebruikers enkel hun gebruikersnaam en wachtwoord moeten ingeven.  

5.  Wacht tot u de boodschap **Inschrijving geslaagd** ziet.  

6.  Open een terminalvenster en breng de volgende wijzigingen om te beperken van het ingeschreven certificaat voor Configuration Manager op de Mac-computer:  

    a.  Voer de opdracht **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**in  

    b.  In de **toegang tot sleutelhanger** het dialoogvenster de **sleutelhangers** sectie, kiest u **System**, en klik in de **categorie** sectie, kiest u **sleutels**.  

    c.  Vouw de sleutels uit om de clientcertificaten weer te geven. Wanneer u het certificaat met een persoonlijke sleutel hebt geïdentificeerd dat u zojuist hebt geïnstalleerd, dubbelklikt u op de sleutel.  

    d.  Op de **toegangsbeheer** Kies **bevestigen alvorens toegang toe te staan**.  

    e.  Blader naar **/Library/Application Support/Microsoft/CCM**, selecteer **CCMClient**, en kies vervolgens **toevoegen**.  

    f.  Kies **wijzigingen opslaan** en sluit de **toegang tot sleutelhanger** in het dialoogvenster.  

7.  Start de Mac-computer opnieuw op.  

 Controleer of de clientinstallatie is gelukt, door het item **Configuration Manager** in **Systeemvoorkeuren** op de Mac-computer te openen. U kunt de verzameling **Alle Systemen** ook bijwerken en bekijken om te bevestigen dat de Mac-computer nu in deze verzameling staat als een beheerde client.  

> [!TIP]  
>  Om te helpen de Mac-client oplossen, kunt u het programma CMDiagnostics die is opgenomen in het Mac OS X-clientpakket voor het verzamelen van de volgende diagnostische informatie:  
>   
>  -   Een lijst met actieve processen  
> -   De versie van Mac OS X als besturingssysteem  
> -   Mac OS X-crashrapporten met betrekking tot de Configuration Manager-client waaronder **CCM\*.crash** en **System Preference.crash**.  
> -   Het bestand Bill of Materials (BOM) en het bestand eigenschappenlijst (.plist) gemaakt door de installatie van de Configuration Manager-client.  
> -   De inhoud van de map  /Library/Application Support/Microsoft/CCM/Logs.  
>   
>  De informatie die verzameld door CmDiagnostics wordt toegevoegd aan een zip-bestand dat is opgeslagen op het bureaublad van de computer en cmdiag -*< hostnaam\>***-***&gt;datum en tijd\>*. zip.* **


##  <a name="use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager"></a>Gebruik een certificaat aanvragen en -installatiemethode die onafhankelijk is van Configuration Manager  

Eerst deze specifieke taken uitvoeren vanuit [implementatie van clientsoftware op Macs voorbereiden](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients):

1. [Implementeer een Webservercertificaat op sitesysteemservers](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-web-server-certificate-to-site-system-servers)

2. [Implementeer een certificaat voor clientverificatie op sitesysteemservers](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-client-authentication-certificate-to-site-system-servers)

3. [Configureer het beheerpunt en distributiepunt](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#configure-the-management-point-and-distribution-point)

4. [Optioneel: Installeer het reporting servicepunt](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#install-the-reporting-services-point)

Vervolgens kunt u deze taken uitvoeren:

5. [Download de clientbronbestanden voor Macs](#download-the-client-source-files-for-macs) .  
6. Volg de instructies die bij uw implementatiemethode gekozen certificaat aanvragen en installeren van het clientcertificaat op de Mac-computer worden geleverd.  
7.  Navigeer naar de map waar u de inhoud van het macclient.dmg-bestand hebt uitgepakt dat u uit het Microsoft Downloadcentrum hebt gedownload.  

3.  Voer de volgende opdrachtregel: **sudo. / ccmsetup -MP < beheerpunt op Internet-FQDN\> - SubjectName < onderwerpwaarde van het certificaat\>**.  De certificaatonderwerpwaarde is hoofdlettergevoelig; typ dit dus exact in zoals deze in de certificaatdetails wordt weergegeven.  

     Voorbeeld: Als de Internet-FQDN in de sitesysteemeigenschappen is **server03.contoso.com** en het Mac-clientcertificaat de FQDN heeft van **mac12.contoso.com** Typ als algemene naam in het certificaatonderwerp: **sudo. / ccmsetup -MP server03.contoso.com - SubjectName mac12.contoso.com**  

4.  Wacht tot u het bericht **Installatie voltooid** ziet en start vervolgens de computer opnieuw op.  

5.  Open een terminalvenster en breng deze wijzigingen om ervoor te zorgen dat dit certificaat toegankelijk voor Configuration Manager op de Mac-computer is:  

    a.  Voer de opdracht **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**in  

    b.  In de **toegang tot sleutelhanger** het dialoogvenster de **sleutelhangers** sectie, kiest u **System**, en klik in de **categorie** sectie, kiest u **sleutels**.  

    c.  Vouw de sleutels uit om de clientcertificaten weer te geven. Wanneer u het certificaat met een persoonlijke sleutel hebt geïdentificeerd dat u zojuist hebt geïnstalleerd, dubbelklikt u op de sleutel.  

    d.  Op de **toegangsbeheer** Kies **bevestigen alvorens toegang toe te staan**.  

    e.  Blader naar **/Library/Application Support/Microsoft/CCM**, selecteer **CCMClient**, en kies vervolgens **toevoegen**.  

    f.  Kies **wijzigingen opslaan** en sluit de **toegang tot sleutelhanger** in het dialoogvenster.  

6.  Als u meer dan één certificaat met dezelfde onderwerpwaarde beschikt, moet u het serienummer van het certificaat om het certificaat dat u wilt gebruiken voor de Configuration Manager-client te identificeren. U doet dit door de volgende opdracht gebruiken: **sudo standaard schrijven com.microsoft.ccmclient SerialNumber-gegevens "< serienummer\>"**.  

     Bijvoorbeeld: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

 Controleer of de clientinstallatie is gelukt door het openen van de **Configuration Manager** item in **Systeemvoorkeuren** op de Mac. U kunt ook bijwerken en bekijken de **alle systemen** verzameling om te bevestigen dat het Mac in deze verzameling als een beheerde client staat.  

## <a name="renewing-the-mac-client-certificate"></a>Het certificaat van de Mac-client vernieuwen  
 Gebruik de volgende procedure voordat u het computercertificaat op Mac-computers vernieuwt.  

 Deze procedure verwijdert de SMSID, die de client nodig heeft om een nieuw of vernieuwd certificaat op de Mac-computer te gebruiken.  

> [!IMPORTANT]  
>  Wanneer u verwijdert en de client-SMSID terugplaatst, wordt de opgeslagen clientgeschiedenis als inventaris gewist nadat verwijderen van de client vanuit de Configuration Manager-console.  

### <a name="to-renew-the-mac-client-certificate"></a>Het Mac-clientcertificaat vernieuwen  

1.  U maakt en vult een apparaatverzameling voor de Mac-computers die u moet het computercertificaat vernieuwd.  

2.  Start in de werkruimte **Activa en naleving** de wizard **Configuratie-item maken**.  

3.  Geef op de pagina **Algemeen** van de wizard de volgende instellingen op:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Type:Mac OS X**  

4.  Zorg er, op de pagina **Ondersteunde Platforms** van de wizard, voor dat alle Mac OS X-versies zijn geselecteerd.  

5.  Klik, op de pagina **Instellingen** van de wizard, op **Nieuw** en geef dan in het dialoogvenster **Instelling aanmaken** de volgende informatie:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Instellingstype:script**  

    -   **Gegevenstype:tekenreeks**  

6.  Klik in het dialoogvenster **Instelling maken** , voor **Detectiescript**, op **Script toevoegen** om een script op te geven dat Mac-computers met een geconfigureerde SMSID detecteert.  

7.  Geef in het dialoogvenster **Detectiescript bewerken** het volgende Shellscript in:  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  Kies **OK** sluit de **detectiescript bewerken** in het dialoogvenster.  

9. In de **instelling maken** in het dialoogvenster voor **herstelscript (optioneel)**, kies **script toevoegen** om op te geven van een script dat de SMSID verwijdert wanneer deze op Mac-computers wordt aangetroffen.  

10. Geef in het dialoogvenster **Herstelscript maken** het volgende Shellscript in:  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. Kies **OK** sluit de **Herstelscript maken** in het dialoogvenster.  

12. Op de **Compliantieregels** pagina van de wizard kiezen **New**, en klik vervolgens in de **Create Rule** dialoogvenster, geeft u de volgende informatie:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Geselecteerde instelling:** Kies **Bladeren** en selecteer vervolgens het detectiescript dat u eerder hebt opgegeven.  

    -   Typ in **het volgende waarden** veld de waarde **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Schakel de optie **Het opgegeven herstelscript uitvoeren wanneer deze instelling niet compatibel is**.  

13. Voer de wizard Configuratie-item maken uit.  

14. Maak een configuratiebasislijn die het configuratie-item bevat dat u zojuist hebt gemaakt en implementeer dit op de apparaatverzameling die u in stap 1 hebt gemaakt.  

     Zie voor meer informatie over het maken en implementeren van configuratiebasislijnen [configuratiebasislijnen maken in System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-baselines.md).  

15. Wanneer u een nieuw certificaat hebt geïnstalleerd op Mac-computers waarbij de SMSID is verwijderd, voert u de volgende opdracht uit om de client te configureren voor het gebruik van het nieuwe certificaat:  

    ```  
    sudo defaults write com.microsoft.ccmclient SubjectName -string <Subject_Name_of_New_Certificate>  
    ```  

16. Als u meer dan één certificaat met dezelfde onderwerpwaarde beschikt, moet u vervolgens het serienummer van het certificaat om het certificaat dat u wilt gebruiken voor de Configuration Manager-client te identificeren. U doet dit door de volgende opdracht gebruiken: **sudo standaard schrijven com.microsoft.ccmclient SerialNumber-gegevens "< serienummer\>"**.  

     Bijvoorbeeld: **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

17. Opnieuw opstarten.  


## <a name="see-also"></a>Zie tevens

[Mac-clients beheren](/sccm/core/clients/manage/maintain-mac-clients)

