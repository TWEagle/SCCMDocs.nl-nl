---
title: 'Certificaten instellen '
titleSuffix: Configuration Manager
description: Certificaten voor vertrouwde communicatie voor On-premises Mobile Device Management in System Center Configuration Manager instellen.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2a7d7170-1933-40e9-96d6-74a6eb7278e2
caps.latest.revision: "27"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 860f6e3f418a15ecfb79e9cbac5e6a09e17feb1a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="set-up-certificates-for-trusted-communications-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Certificaten voor vertrouwde communicatie instellen voor On-premises Mobile Device Management in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

System Center Configuration Manager op\-premises Mobile Device Management vereist het inschrijvingspunt, proxypunt voor inschrijving, distributiepunt en Apparaatbeheer sitesysteemrollen worden ingesteld voor vertrouwde communicatie met beheerde apparaten. Elke sitesysteemserver die als host fungeert voor een of meer van deze rollen moet een uniek PKI-certificaat hebben dat is gebonden aan de webserver op dat systeem. Een certificaat met dezelfde basis als het certificaat op de servers moet ook worden opgeslagen op beheerde apparaten om onderlinge vertrouwde communicatie mogelijk te maken.  

 Voor apparaten die lid zijn van het domein installeert Active Directory Certificate Services het benodigde certificaat met de vertrouwde basis automatisch op alle apparaten. Voor apparaten die niet lid zijn van het domein moet u op een andere manier een geldig certificaat met een vertrouwde basis verkrijgen. Als u de certificeringsinstantie van de site als de vertrouwde basis gebruikt (dezelfde die Active Directory gebruikt voor apparaten die lid zijn van het domein), moet er een certificaat dat is uitgegeven door die certificeringsinstantie gebonden zijn aan de sitesysteemservers voor het inschrijvingspunt en het proxypunt voor inschrijving.  

 Op elk apparaat dat wordt beheerd, moet ook een certificaat met dezelfde basis zijn geïnstalleerd ter ondersteuning van vertrouwde communicatie met de sitesysteemrollen. Voor bulksgewijs ingeschreven apparaten kunt u het certificaat wanneer het apparaat voor het eerst door een gebruiker wordt gestart, opnemen in het inschrijvingspakket dat voor inschrijving aan het apparaat wordt toegevoegd. Voor apparaten die door de gebruiker worden ingeschreven, moet u het certificaat via e-mail, webdownload of een andere methode toevoegen.  

 Als alternatief voor apparaten die niet lid zijn van het domein, kunt u de basis van een bekende openbare certificeringsinstantie (zoals Verisign of GoDaddy) gebruiken om het servercertificaat uit te geven. Zo voorkomt u dat u een certificaat handmatig op het apparaat moet installeren, omdat de meeste apparaten verbindingen met servers die gebruikmaken van dezelfde basis als de openbare certificeringsinstantie, vertrouwen. Dit is een handig alternatief voor door de gebruiker ingeschreven apparaten waarin het niet haalbaar is om op elk apparaat de certificaten te installeren die via de certificeringsinstantie van de site worden vertrouwd.  

> [!IMPORTANT]  
>  Er zijn veel manieren voor het instellen van de certificaten voor vertrouwde communicatie tussen apparaten en de sitesysteemservers voor op\-premises Mobile Device Management. De informatie in dit artikel wordt weergegeven als een voorbeeld van een van de mogelijke manieren. Voor deze methode moet u een server op uw site uitvoeren met Active Directory Certificate Services-rol en moeten de rolservices voor de certificeringsinstantie en internetregistratie van de certificeringsinstantie zijn geïnstalleerd. Zie [Active Directory Certificate Services](http://go.microsoft.com/fwlink/p/?LinkId=115018) voor meer informatie over en richtlijnen voor deze Windows Server-rol.  

 Voor het instellen van de Configuration Manager-site voor de SSL-communicatie vereist voor op\-premises Mobile Device Management, volg deze stappen op hoog niveau:  

-   [De certificeringsinstantie (CA) configureren voor het uitgeven van CRL 's](#bkmk_configCa)  

-   [De sjabloon voor het webservercertificaat maken op de CA](#bkmk_certTempl)  

-   [Het Webservercertificaat voor elke sitesysteemrol aanvragen](#bkmk_requestCert)  

-   [Het certificaat binden aan de webserver](#bkmk_bindCert)  

-   [Exporteer het certificaat met dezelfde basis als het webservercertificaat](#bkmk_exportCert)  

##  <a name="bkmk_configCa"></a>De certificeringsinstantie (CA) configureren voor het uitgeven van CRL 's  
 De certificeringsinstantie (CA) gebruikt standaard LDAP-gebaseerde certificaatintrekkingslijsten (CRL's) waarmee verbinding kan worden gemaakt met apparaten die lid zijn van het domein. U moet HTTP-gebaseerde CRL's toevoegen aan de certificeringsinstantie, zodat apparaten die niet lid zijn van het domein worden vertrouwd met uitgegeven certificaten van de certificeringsinstantie. Deze certificaten zijn vereist voor SSL-communicatie tussen de servers die als host fungeert voor de sitesysteemrollen van Configuration Manager en de apparaten die zijn geregistreerd voor op\-premises Mobile Device Management.  

 Voer de volgende stappen uit voor de configuratie van de certificeringsinstantie voor het automatisch publiceren van CRL-informatie voor het uitgeven van certificaten die vertrouwde verbindingen toestaan voor apparaten die wel lid zijn van het domein en apparaten die niet lid zijn van het domein:  

1.  Klik op de server met de certificeringsinstantie voor uw site op **Start** > **Systeembeheer** > **Certificeringsinstantie**.  

2.  Klik in de certificeringsinstantieconsole met de rechtermuisknop op **CertificateAuthority** en klik vervolgens op **Eigenschappen**.  

3.  Klik in de eigenschappen van CertificateAuthority op het tabblad **Extensies**. Zorg ervoor dat **Selecteer een extensie** is ingesteld op **CRL-distributiepunt (CDP)**.  

4.  Selecteer **http://<ServerDNSName\>/CertEnroll/<CAName\><CRLNameSuffix\><DeltaCRLAllowed\>.crl**. En de volgende drie opties:  

    -   **In CRL's opnemen. Clients gebruiken deze om locaties met Delta-CRL te vinden.**  

    -   **Opnemen in de CDP-uitbreiding van uitgegeven certificaten.**  

    -   **Opnemen in de IDP-uitbreiding van uitgegeven CRL 's**  

5.  Klik op de **uitgiftemodule** tabblad **eigenschappen...** , selecteer daarna **toestaan dat certificaten worden uitgegeven aan het bestandssysteem**.  

6.  Klik op **OK** wanneer wordt weergegeven dat Active Directory Certificate Services opnieuw moet worden gestart.  

7.  Klik met de rechtermuisknop op **Ingetrokken certificaten**, klik op **Alle taken** en klik vervolgens op **Publiceren**.  

8.  Selecteer in het dialoogvenster CRL publiceren de optie **Alleen een lijst met wijzigingen ten aanzien van ingetrokken certificaten** en klik vervolgens op **OK**.  

##  <a name="bkmk_certTempl"></a>De sjabloon voor het webservercertificaat maken op de CA  
 Na het publiceren van de nieuwe CRL op de certificeringsinstantie is de volgende stap het maken van een sjabloon voor het webservercertificaat. Deze sjabloon is vereist voor het uitgeven van certificaten voor de servers waarop het inschrijvingspunt, het proxypunt voor inschrijving, het distributiepunt en de sitesysteemrollen van het apparaatbeheerpunt worden gehost. Deze servers worden SSL-eindpunten voor vertrouwde communicatie tussen sitesysteemrollen en ingeschreven apparaten.    Voer de volgende stappen uit om de certificaatsjabloon te maken:  

1.  Maak een beveiligingsgroep met de naam **ConfigMgr MDM-servers** die de servers bevat waarop de sitesystemen worden uitgevoerd waarvoor vertrouwde communicatie met ingeschreven apparaten vereist is.  

2.  Klik in de certificeringsinstantieconsole met de rechtermuisknop op **Certificaatsjablonen** en klik op **Beheren** om de certificaatsjablonenconsole te laden.  

3.  Klik in het resultaatvenster met de rechtermuisknop op het item dat **Webserver** weergeeft in de kolom **Weergavenaam van sjabloon**, en klik vervolgens op **Sjabloon dupliceren**.  

4.  Zorg er in het dialoogvenster **Sjabloon dupliceren** voor dat Windows 2003 Server, **Enterprise Edition** geselecteerd, en klik vervolgens op **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren. Configuration Manager biedt geen ondersteuning voor Windows Server 2008-certificaatsjablonen voor vertrouwde communicatie via HTTPS.  

    > [!NOTE]  
    >  Als de certificeringsinstantie die u gebruikt zich op Windows Server 2012 bevindt, wordt u niet gevraagd naar de versie van de certificaatsjabloon wanneer u op **Sjabloon dupliceren** klikt. Geef dit dan als volgt op in het tabblad **Compatibiliteit** van de sjablooneigenschappen:  
    >   
    >  **Certificeringsinstantie (CA)**: **WindowsServer 2003**  
    >   
    >  **Ontvanger van certificaat**: **Windows XP / Server 2003**  

5.  Voer in het dialoogvenster **Eigenschappen van nieuwe sjabloon** op het tabblad **Algemeen** de naam van een sjabloon in om de webcertificaten te genereren die zullen worden gebruikt op Configuration Manager-sitesystemen, zoals **ConfigMgr MDM-webserver**.  

6.  Klik op het tabblad **Onderwerpnaam**, selecteer **Op basis van Active Directory-informatie samenstellen** en geef voor de indeling van de onderwerpnaam **DNS-naam** op. Schakel het selectievakje van de alternatieve onderwerpnaam uit als **Principal-naam van gebruiker (UPN-naam)** is geselecteerd.  

7.  Klik op het tabblad **Beveiliging** en verwijder de machtiging **Registratie** van de beveiligingsgroepen **Domeinadministrators** en **Ondernemingsadministrators**.  

8.  Klik op **Toevoegen**, voer **ConfigMgr IIS Servers** in het tekstvak in en klik op **OK**.  

9. Selecteer de machtiging **Inschrijving** voor deze groep en verwijder de machtiging **Lezen** niet.  

10. Klik op **OK** en sluit de certificaatsjablonen console.  

11. Klik in Certificeringsinstantie-console met de rechtermuisknop op **Certificaatsjablonen**, klik op **Nieuw** en vervolgens op **Te verlenen certificaatsjablonen**.  

12. Selecteer in het dialoogvenster **Certificaatsjablonen inschakelen** de nieuwe sjabloon die u net hebt gemaakt, **ConfigMgr MDM-webserver**, en klik op **OK**.  

##  <a name="bkmk_requestCert"></a>Het Webservercertificaat voor elke sitesysteemrol aanvragen  
 Apparaten die zijn geregistreerd voor op\-premises Mobile Device Management SSL-eindpunten die als host fungeert voor het inschrijvingspunt, proxypunt voor inschrijving, distributiepunt en apparaatbeheerpunt moeten vertrouwen.  In de volgende stappen leest u hoe u het webservercertificaat voor IIS aanvraagt. U moet dit doen voor elke server (SSL-eindpunt) een van de vereiste sitesysteemrollen voor het hosten op\-premises Mobile Device Management.  

1.  Open op de primaire siteserver de opdrachtprompt met beheerdersrechten, typ **MMC** en druk op **Enter**.  

2.  Klik in de MMC op **Bestand** > **Module toevoegen/verwijderen**.  

3.  Selecteer in de module Certificaten de optie **Certificaten**, klik op **Toevoegen**, selecteer **Computeraccount**, klik op **Volgende**, klik op **Voltooien** en klik vervolgens op **OK** om het venster Module toevoegen of verwijderen te sluiten.  

4.  Klik met de rechtermuisknop op **Persoonlijk** en klik vervolgens op **Alle taken** > **Nieuw certificaat aanvragen**.  

5.  Klik in de wizard Certificaatinschrijving op **Volgende**, selecteer **Active Directory Domain Services-inschrijvingsbeleid** en klik op **Volgende**.  

6.  Schakel het selectievakje naast het webservercertificaat (**ConfigMgr MDM-webserver**) in en klik vervolgens op **Inschrijven**.  

7.  Zodra het certificaat is ingeschreven, klikt u op **Voltooien**.  

 Omdat elke server een uniek Webservercertificaat moet, moet u dit proces herhalen voor elke server een van de vereiste sitesysteemrollen voor het hosten op\-premises Mobile Device Management.  Als één server als host fungeert voor alle sitesysteemrollen, hoeft u maar één webservercertificaat aan te vragen.  

##  <a name="bkmk_bindCert"></a>Het certificaat binden aan de webserver  
 Het nieuwe certificaat moet nu worden gekoppeld aan de webserver van elke sitesysteemserver die als host fungeert voor de vereiste sitesysteemrollen op\-premises Mobile Device Management. Voer de onderstaande stappen uit voor elke server die als host fungeert voor de sitesysteemrollen voor het inschrijvingspunt en het proxypunt voor inschrijving. Als één server als host fungeert voor alle sitesysteemrollen, hoeft u deze stappen maar één keer uit te voeren. U hoeft deze taak niet uit te voeren voor de sitesysteemrollen voor het distributiepunt en het apparaatbeheerpunt, aangezien deze het vereiste certificaat automatisch ontvangen tijdens de inschrijving.  

1.  Klik op de server met het inschrijvingspunt, het proxypunt voor inschrijving, het distributiepunt of het apparaatbeheerpunt en klik op **Start** > **Systeembeheer** > **IIS-beheer**.  

2.  Navigeer naar onder verbindingen en met de rechtermuisknop op **standaardwebsite**, en klik vervolgens op **bindingen bewerken...**  

3.  Klik in het dialoogvenster sitebindingen op **https**, en klik vervolgens op **bewerken...**  

4.  Selecteer in het dialoogvenster Sitebinding bewerken het certificaat dat u zojuist hebt ingeschreven voor het **SSL-certificaat**, klik op **OK** en klik vervolgens op **Sluiten**.  

5.  In IIS-beheerconsole selecteert u onder Verbindingen de webserver. Klik vervolgens in het deelvenster Acties aan de rechterkant op **Opnieuw opstarten**.  

##  <a name="bkmk_exportCert"></a>Exporteer het certificaat met dezelfde basis als het webservercertificaat  
 Active Directory Certificate Services installeert het vereiste certificaat van de certificeringsinstantie doorgaans op alle apparaten die lid zijn van een domein. Apparaten die niet lid zijn van het domein kunnen echter niet communiceren met de sitesysteemrollen zonder certificaat van de basiscertificeringsinstantie. Als u het vereiste certificaat voor apparaten om te communiceren met de sitesysteemrollen wilt ophalen, kunt u het exporteren van het certificaat dat is gebonden aan de webserver.  

 Voer deze stappen uit voor het exporteren van het basiscertificaat van het webservercertificaat.  

1.  Klik in de IIS-beheer **standaardwebsite**, en klik vervolgens in het rechter deelvenster actie op **bindingen...**  

2.  Klik in het dialoogvenster sitebindingen op **https**, en klik vervolgens op **bewerken...**  

3.  Zorg ervoor dat het webservercertificaat is geselecteerd en klik op **weergeven...**  

4.  Klik in de eigenschappen van het webservercertificaat op **Certificeringspad**, klik op de basis bovenaan in het certificeringspad en klik op **Certificaat weergeven**.  

5.  Klik in de eigenschappen van het basiscertificaat op **Details**, en klik vervolgens op **kopiëren naar bestand...**  

6.  Klik in de wizard Certificaat exporteren op **Volgende**.  

7.  Zorg ervoor dat **DER Encoded Binary X.509 (.CER)** is geselecteerd als indeling en klik op **Volgende**.  

8.  De bestandsnaam, klikt u op **bladeren...** , kies een locatie om het bestand een naam op te slaan van het certificaatbestand en klik op **opslaan**.  

     Apparaten die u wilt inschrijven, hebben toegang tot dit bestand nodig om het basiscertificaat te importeren. Kies daarom een algemene locatie waartoe de meeste computers en apparaten toegang hebben. U kunt het bestand nu ook opslaan op een handige locatie (bijvoorbeeld de C-schijf) en het later naar een algemene locatie verplaatsen.  

     Klik op **Volgende**.  

9. Controleer de instellingen en klik op **Voltooien**.  
