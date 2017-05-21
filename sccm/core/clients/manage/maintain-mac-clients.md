---
title: Mac-clients onderhouden | Microsoft-documenten
description: Onderhoudstaken voor Configuration Manager Mac-clients.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf6337a2-700c-47f3-b6f8-5814f9b81e59
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3bf6651f58dc0c2aa4773f77115c3fbcd4a33221
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---

# <a name="maintain-mac-clients"></a>Mac-clients beheren
*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Hier vindt u procedures voor het verwijderen van Mac-clients en voor het vernieuwen van de bijbehorende certificaten.

##  <a name="uninstalling-the-mac-client"></a>De Mac-client verwijderen  

1.  Open op een Mac-computer een terminalvenster en navigeer naar de map met **macclient.dmg**.  

2.  Ga naar de map Hulpprogramma's en geef de volgende opdrachtregel in:  

     **. / CMUninstall - c**  

    > [!NOTE]  
    >  De **- c** eigenschap ontvangt de client de instructie verwijderd wanneer u ook Logboeken crashes-client verwijderen en logboekbestanden. We raden u dit naar verwarring te vermijden als u de client later opnieuw installeert.  

3.  Indien nodig, handmatig verwijderen van het certificaat voor clientverificatie dat het gebruik van Configuration Manager, of Trek het. CMUnistall verwijdert of trekt dit certificaat niet in.  

##  <a name="renewing-the-mac-client-certificate"></a>Het certificaat van de Mac-client vernieuwen  
 Gebruik een van de volgende methodes om het certificaat van de Mac-client te vernieuwen:  

-   [De certificaatwizard vernieuwen](#renew-certificate-wizard)  

-   [Certificaat handmatig vernieuwen](#renew-certificate-manually)  

###  <a name="renew-certificate-wizard"></a>De certificaatwizard vernieuwen  

1.  Configureer de volgende waarden als *tekenreeksen* in het ccmclient.plist-bestand die bepaalt wanneer de Wizard Certificaat vernieuwen wordt geopend:  

 -   **RenewalPeriod1** -geeft, in seconden, de eerste vernieuwingsperiode waarin gebruikers het certificaat kunnen vernieuwen. De standaardwaarde is 3.888.000 seconden (45 dagen). Geen een waarde die kleiner is dan 300, configureren zoals de tijd worden hersteld op de standaardwaarde. 

 -   **RenewalPeriod2** -geeft, in seconden, de tweede vernieuwingsperiode waarin gebruikers het certificaat kunnen vernieuwen. De standaardwaarde is 259.200 seconden (3 dagen). Als deze waarde is geconfigureerd en groter dan of gelijk is aan 300 seconden is en kleiner dan of gelijk zijn aan **RenewalPeriod1**, de waarde wordt gebruikt. Als de waarde voor **RenewalPeriod1** groter is dan 3 dagen, wordt een waarde van 3 dagen gebruikt voor **RenewalPeriod2**.  Als de waarde voor **RenewalPeriod1** kleiner is dan 3 dagen, wordt **RenewalPeriod2** vervolgens ingesteld op dezelfde waarde als **RenewalPeriod1**.  

 -   **RenewalReminderInterval1** -geeft, in seconden, de frequentie waarmee de Wizard Certificaat vernieuwen zal worden getoond aan gebruikers tijdens de eerste vernieuwingsperiode. De standaardwaarde is 86.400 seconden (1 dag). Als **RenewalReminderInterval1** groter is dan 300 seconden en kleiner dan de waarde die is geconfigureerd voor **RenewalPeriod1**, dan zal de geconfigureerde waarde worden gebruikt. Anders wordt de standaardwaarde van 1 dag gebruikt.  

 -   **RenewalReminderInterval2** -geeft, in seconden, de frequentie waarmee de Wizard Certificaat vernieuwen zal worden getoond aan gebruikers tijdens de tweede vernieuwingsperiode. De standaardwaarde is 28.800 seconden (8 uur). Als de waarde voor **RenewalReminderInterval2** groter is dan 300 seconden, kleiner dan of gelijk aan **RenewalReminderInterval1** is en kleiner dan of gelijk aan **RenewalPeriod2**is, wordt de geconfigureerde waarde gebruikt. Anders wordt een waarde van 8 uur gebruikt.  

     **Voorbeeld:** Als de waarden als standaardwaarden worden gelaten, wordt 45 dagen voordat het certificaat verloopt, de wizard geopend elke 24 uur.  Vanaf 3 dagen vóór het verlopen van het certificaat wordt de wizard elke 8 uur geopend.  

     **Voorbeeld:** Gebruik de volgende opdrachtregel of script in te stellen van de eerste vernieuwingsperiode op 20 dagen.  

     `sudo defaults write com.microsoft.ccmclient RenewalPeriod1 1728000`  

2.  Wanneer de Wizard Certificaat vernieuwen wordt geopend, de **gebruikersnaam** en **servernaam** velden gewoonlijk al ingevuld en moet de gebruiker kan alleen een wachtwoord in om het certificaat vernieuwen invoeren.  

    > [!NOTE]  
    >  Als de wizard niet wordt geopend, of als u de wizard onopzettelijk sluit, klik dan op **Vernieuwen** op de **Configuration Manager** -voorkeurspagina om de wizard te openen.  

###  <a name="renew-certificate-manually"></a>Certificaat handmatig vernieuwen  
 De geldigheidsperiode voor het Mac-clientcertificaat is doorgaans 1 jaar. Configuration Manager verlengt het gebruikerscertificaat dat het aanvraagt tijdens de registratie, zodat u de volgende procedure gebruiken moet om het certificaat handmatig vernieuwen niet automatisch.  

> [!IMPORTANT]  
>  Als het certificaat verloopt, moet u de Mac-client verwijderen, opnieuw installeren en vervolgens opnieuw inschrijven.  

 Deze procedure verwijdert de SMSID, die vereist is om een nieuw certificaat aan te vragen voor dezelfde Mac-computer. Wanneer u verwijdert en de client-SMSID terugplaatst, wordt de opgeslagen clientgeschiedenis als inventaris gewist nadat verwijderen van de client vanuit de Configuration Manager-console.  

1.  U maakt en vult een apparaatverzameling voor de Mac-computers die de gebruikerscertificaten moet vernieuwen.  

    > [!WARNING]  
    >  Configuration Manager controleert de geldigheidsperiode van het certificaat dat het inschrijft voor Mac-computers niet. U moet bewaken dit onafhankelijk van Configuration Manager om te identificeren van de Mac-computers toevoegen aan deze verzameling.  

2.  Start in de werkruimte **Activa en naleving** de wizard **Configuratie-item maken**.  

3.  Geef op de pagina **Algemeen** de volgende gegevens op:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Type:Mac OS X**  

4.  Op de **ondersteunde Platforms** pagina, zorg ervoor dat alle Mac OS X-versies zijn geselecteerd.  

5.  Op de **instellingen** pagina, kiest u **New** en klik in de **instelling maken** dialoogvenster, geeft u de volgende informatie:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Instellingstype:script**  

    -   **Gegevenstype:tekenreeks**  

6.  In de **instelling maken** in het dialoogvenster voor **detectiescript**, kies **script toevoegen** om op te geven van een script dat Mac-computers met een geconfigureerde SMSID detecteert.  

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

12. Klik, op de pagina **Compliantieregels** van de wizard, op **Nieuw**en geef dan in het dialoogvenster **Regel maken** de volgende informatie:  

    -   **Naam:Verwijder SMSID voor Mac**  

    -   **Geselecteerde instelling:** Kies **Bladeren** en selecteer vervolgens het detectiescript dat u eerder hebt opgegeven.  

    -   Typ in **het volgende waarden** veld de waarde **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**.  

    -   Schakel de optie **Het opgegeven herstelscript uitvoeren wanneer deze instelling niet compatibel is**.  

13. Voer de wizard Configuratie-item maken uit.  

14. Maak een configuratiebasislijn met de configuratie-item dat u net hebt gemaakt en deze implementeren in de apparaatverzameling die u in stap 1 hebt gemaakt.  

     Zie voor meer informatie over het maken en implementeren van configuratiebasislijnen [configuratiebasislijnen maken in System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-baselines.md) en [het implementeren van configuratiebasislijnen in System Center Configuration Manager](../../../compliance/deploy-use/deploy-configuration-baselines.md).  

15. Voer op Mac-computers waarvan de SMSID is verwijderd, de volgende opdracht uit om een nieuw certificaat te installeren.  

    ```  
    sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u <'user name'>  
    ```  

     Geef, wanneer dit wordt gevraagd, het wachtwoord voor de supergebruikersaccount om de opdracht uit te voeren en dan het wachtwoord voor de Active Directory-gebruikersaccount.  

16. Open een terminalvenster en breng de volgende wijzigingen om te beperken van het ingeschreven certificaat voor Configuration Manager op de Mac-computer:  

    a.  Voer de opdracht **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**in  

    b.  In de **toegang tot sleutelhanger** dialoogvenster in de **sleutelhangers** sectie, kiest u **System**, en klik in de **categorie** sectie, kiest u **sleutels**.  

    c.  Vouw de sleutels uit om de clientcertificaten weer te geven. Wanneer u het certificaat met een persoonlijke sleutel hebt geïdentificeerd dat u zojuist hebt geïnstalleerd, dubbelklikt u op de sleutel.  

    d.  Op de **toegangsbeheer** Kies **bevestigen alvorens toegang toe te staan**.  

    e.  Blader naar **/Library/Application Support/Microsoft/CCM**, selecteer **CCMClient**, en kies vervolgens **toevoegen**.  

    f.  Kies **wijzigingen opslaan** en sluit de **toegang tot sleutelhanger** in het dialoogvenster.  

17. Start de Mac-computer opnieuw op.  


