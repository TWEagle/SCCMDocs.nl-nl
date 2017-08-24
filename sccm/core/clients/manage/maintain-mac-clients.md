---
title: Mac-clients beheren | Microsoft Docs
description: Onderhoudstaken voor Configuration Manager Mac-clients.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf6337a2-700c-47f3-b6f8-5814f9b81e59
caps.latest.revision: "12"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 3bf6651f58dc0c2aa4773f77115c3fbcd4a33221
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="maintain-mac-clients"></a>Mac-clients beheren
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hier vindt u procedures voor het verwijderen van Mac-clients en voor het vernieuwen van hun certificaten.

##  <a name="uninstalling-the-mac-client"></a>De Mac-client verwijderen  

1.  Open op een Mac-computer een terminalvenster en navigeer naar de map met **macclient.dmg**.  

2.  Ga naar de map Hulpprogramma's en geef de volgende opdrachtregel in:  

     **. / CMUninstall - c**  

    > [!NOTE]  
    >  De **- c** eigenschap instrueert de client ook Logboeken crash-client verwijderen en logboekbestanden verwijderen. We raden u dit om verwarring te voorkomen als u later de client opnieuw installeert.  

3.  Indien nodig, handmatig verwijderen van het certificaat voor clientverificatie die het gebruik van Configuration Manager, of Trek het. CMUnistall verwijdert of trekt dit certificaat niet in.  

##  <a name="renewing-the-mac-client-certificate"></a>Het certificaat van de Mac-client vernieuwen  
 Gebruik een van de volgende methodes om het certificaat van de Mac-client te vernieuwen:  

-   [Certificaatwizard vernieuwen](#renew-certificate-wizard)  

-   [Certificaat handmatig vernieuwen](#renew-certificate-manually)  

###  <a name="renew-certificate-wizard"></a>Certificaatwizard vernieuwen  

1.  Configureer de volgende waarden als *tekenreeksen* in het ccmclient.plist-bestand die bepaalt wanneer de Wizard Certificaat vernieuwen wordt geopend:  

 -   **RenewalPeriod1** -geeft, in seconden, de eerste vernieuwingsperiode waarin gebruikers het certificaat kunnen vernieuwen. De standaardwaarde is 3.888.000 seconden (45 dagen). Niet een waarde die kleiner is dan 300 configureren zoals de periode wordt teruggezet op de standaardwaarde. 

 -   **RenewalPeriod2** -geeft, in seconden, de tweede vernieuwingsperiode waarin gebruikers het certificaat kunnen vernieuwen. De standaardwaarde is 259.200 seconden (3 dagen). Als deze waarde is geconfigureerd en groter dan of gelijk is aan 300 seconden is en kleiner is dan of gelijk zijn aan **RenewalPeriod1**, de waarde wordt gebruikt. Als de waarde voor **RenewalPeriod1** groter is dan 3 dagen, wordt een waarde van 3 dagen gebruikt voor **RenewalPeriod2**.  Als de waarde voor **RenewalPeriod1** kleiner is dan 3 dagen, wordt **RenewalPeriod2** vervolgens ingesteld op dezelfde waarde als **RenewalPeriod1**.  

 -   **RenewalReminderInterval1** -Hiermee geeft u in seconden, de frequentie waarmee de Wizard Certificaat vernieuwen zal worden getoond aan gebruikers tijdens de eerste vernieuwingsperiode. De standaardwaarde is 86.400 seconden (1 dag). Als **RenewalReminderInterval1** groter is dan 300 seconden en kleiner dan de waarde die is geconfigureerd voor **RenewalPeriod1**, dan zal de geconfigureerde waarde worden gebruikt. Anders wordt de standaardwaarde van 1 dag gebruikt.  

 -   **RenewalReminderInterval2** -Hiermee geeft u, in seconden, de frequentie waarmee de Wizard Certificaat vernieuwen zal worden getoond aan gebruikers tijdens de tweede vernieuwingsperiode. De standaardwaarde is 28.800 seconden (8 uur). Als de waarde voor **RenewalReminderInterval2** groter is dan 300 seconden, kleiner dan of gelijk aan **RenewalReminderInterval1** is en kleiner dan of gelijk aan **RenewalPeriod2**is, wordt de geconfigureerde waarde gebruikt. Anders wordt een waarde van 8 uur gebruikt.  

     **Voorbeeld:** Als de waarden als standaardwaarden worden gelaten, 45 dagen voordat het certificaat verloopt, de wizard elke 24 uur geopend.  Vanaf 3 dagen vóór het verlopen van het certificaat wordt de wizard elke 8 uur geopend.  

     **Voorbeeld:** De volgende opdrachtregel of een script gebruiken om in te stellen van de eerste vernieuwingsperiode op 20 dagen.  

     `sudo defaults write com.microsoft.ccmclient RenewalPeriod1 1728000`  

2.  Wanneer de Wizard Certificaat vernieuwen wordt geopend, de **gebruikersnaam** en **servernaam** velden gewoonlijk al ingevuld en moet de gebruiker kan alleen een wachtwoord invoeren voor het certificaat vernieuwen.  

    > [!NOTE]  
    >  Als de wizard niet wordt geopend, of als u de wizard onopzettelijk sluit, klik dan op **Vernieuwen** op de **Configuration Manager** -voorkeurspagina om de wizard te openen.  

###  <a name="renew-certificate-manually"></a>Certificaat handmatig vernieuwen  
 De geldigheidsperiode voor het Mac-clientcertificaat is doorgaans 1 jaar. Configuration Manager verlengt het gebruikerscertificaat dat het aanvraagt tijdens de inschrijving, zodat u de volgende procedure gebruiken moet om het certificaat handmatig vernieuwen niet automatisch.  

> [!IMPORTANT]  
>  Als het certificaat verloopt, moet u de Mac-client verwijderen, opnieuw installeren en vervolgens opnieuw inschrijven.  

 Deze procedure verwijdert de SMSID, die vereist is om een nieuw certificaat aan te vragen voor dezelfde Mac-computer. Wanneer u verwijdert en vervangt u de client-SMSID, wordt de opgeslagen clientgeschiedenis als inventaris gewist nadat verwijderen van de client uit de Configuration Manager-console.  

1.  U maakt en vult u een apparaatverzameling voor de Mac-computers die de gebruikerscertificaten moet vernieuwen.  

    > [!WARNING]  
    >  Configuration Manager controleert de geldigheidsperiode van het certificaat dat het inschrijft voor Mac-computers. U moet controleren dit onafhankelijk van Configuration Manager voor het identificeren van de Mac-computers toevoegen aan deze verzameling.  

2.  Start in de werkruimte **Activa en naleving** de wizard **Configuratie-item maken**.  

3.  Geef op de pagina **Algemeen** de volgende gegevens op:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Type:Mac OS X**  

4.  Op de **ondersteunde Platforms** pagina, zorg ervoor dat alle Mac OS X-versies zijn geselecteerd.  

5.  Op de **instellingen** pagina **nieuw** en klikt u op de **instelling maken** dialoogvenster geeft u de volgende informatie:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Instellingstype:script**  

    -   **Gegevenstype:tekenreeks**  

6.  In de **instelling maken** in het dialoogvenster voor **detectiescript**, kies **script toevoegen** om op te geven van een script dat Mac-computers met een geconfigureerde SMSID detecteert.  

7.  Geef in het dialoogvenster **Detectiescript bewerken** het volgende Shellscript in:  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  Kies **OK** sluiten de **detectiescript bewerken** in het dialoogvenster.  

9. In de **instelling maken** in het dialoogvenster voor **herstelscript (optioneel)**, kies **script toevoegen** om op te geven van een script dat de SMSID verwijdert wanneer deze op Mac-computers wordt aangetroffen.  

10. Geef in het dialoogvenster **Herstelscript maken** het volgende Shellscript in:  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. Kies **OK** sluiten de **Herstelscript maken** in het dialoogvenster.  

12. Klik, op de pagina **Compliantieregels** van de wizard, op **Nieuw**en geef dan in het dialoogvenster **Regel maken** de volgende informatie:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Geselecteerde instelling:** Kies **Bladeren** en selecteer vervolgens het detectiescript dat u eerder hebt opgegeven.  

    -   Typ in **het volgende waarden** veld de waarde **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Schakel de optie **Het opgegeven herstelscript uitvoeren wanneer deze instelling niet compatibel is**.  

13. Voer de wizard Configuratie-item maken uit.  

14. Maak een configuratiebasislijn met de configuratie-item dat u net hebt gemaakt en deze implementeren in de verzameling met apparaten die u in stap 1 hebt gemaakt.  

     Zie voor meer informatie over het maken en implementeren van configuratiebasislijnen [configuratiebasislijnen maken in System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-baselines.md) en [het implementeren van configuratiebasislijnen in System Center Configuration Manager](../../../compliance/deploy-use/deploy-configuration-baselines.md).  

15. Voer op Mac-computers waarvan de SMSID is verwijderd, de volgende opdracht uit om een nieuw certificaat te installeren.  

    ```  
    sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u <'user name'>  
    ```  

     Geef, wanneer dit wordt gevraagd, het wachtwoord voor de supergebruikersaccount om de opdracht uit te voeren en dan het wachtwoord voor de Active Directory-gebruikersaccount.  

16. Als u wilt beperken van het ingeschreven certificaat naar Configuration Manager op de Mac-computer, open een terminalvenster en breng de volgende wijzigingen:  

    a.  Voer de opdracht **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**in  

    b.  In de **toegang tot sleutelhanger** dialoogvenster in de **sleutelhangers** sectie **System**, en klikt u op de **categorie** sectie **sleutels**.  

    c.  Vouw de sleutels uit om de clientcertificaten weer te geven. Wanneer u het certificaat met een persoonlijke sleutel hebt geïdentificeerd dat u zojuist hebt geïnstalleerd, dubbelklikt u op de sleutel.  

    d.  Op de **toegangsbeheer** Kies **bevestigen alvorens toegang toe te staan**.  

    e.  Blader naar **Library/Application Support/Microsoft/CCM**, selecteer **CCMClient**, en kies vervolgens **toevoegen**.  

    f.  Kies **wijzigingen opslaan** en sluit de **Sleutelhangertoegang** in het dialoogvenster.  

17. Start de Mac-computer opnieuw op.  

