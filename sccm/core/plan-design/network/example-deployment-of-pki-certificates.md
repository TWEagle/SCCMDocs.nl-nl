---
title: Implementatie van PKI-certificaten | Microsoft-documenten
description: Ga als volgt een voorbeeld van stapsgewijze voor informatie over het maken en implementeren van PKI-certificaten die door System Center Configuration Manager gebruikt.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3417ff88-7177-4a0d-8967-ab21fe7eba17
caps.latest.revision: 11
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: b15f85b4483bbae2444d4e73d2e2aa0b3979d9ab
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="step-by-step-example-deployment-of-the-pki-certificates-for-system-center-configuration-manager-windows-server-2008-certification-authority"></a>Voorbeeld van stapsgewijze implementatie van de PKI-certificaten voor System Center Configuration Manager: Windows Server 2008-certificeringsinstantie

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze stapsgewijze Voorbeeldimplementatie, dat gebruikmaakt van een Windows Server 2008-certificeringsinstantie (CA), heeft de procedures die laten zien u hoe u maken en implementeren van de openbare-sleutelinfrastructuur (PKI)-certificaten die gebruikmaakt van System Center Configuration Manager. Bij deze procedures worden een bedrijfscertificeringsinstantie en certificaatsjablonen en gebruikt. De stappen zijn alleen geschikt voor een testnetwerk, voor het testen van het concept.  

 Er bestaan meerdere methoden van implementatie voor de vereiste certificaten, Raadpleeg daarom uw specifieke PKI-Implementatiedocumentatie voor de vereiste procedures en aanbevolen procedures voor het implementeren van de vereiste certificaten voor een productie-omgeving. Zie voor meer informatie over de certificaatvereisten [PKI-certificaatvereisten voor System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

> [!TIP]  
>  U kunt de instructies in dit onderwerp voor de besturingssystemen die niet wordt vermeld in de rubriek Testnetwerkvereisten aanpassen. Als u echter de verlenende certificeringsinstantie uitvoert op Windows Server 2012, wordt u niet gevraagd om de versie van het certificaatsjabloon. Geef dit op de **compatibiliteit** tabblad van de sjablooneigenschappen:  
>   
>  -   **Certificeringsinstantie (CA)**: **WindowsServer 2003**  
> -   **Ontvanger van certificaat**: **Windows XP / Server 2003**  

## <a name="in-this-section"></a>In deze sectie  
 De volgende rubrieken bevatten stapsgewijze Voorbeeldinstructies maken en implementeren van de volgende certificaten die kunnen worden gebruikt met System Center Configuration Manager:  

 [Testnetwerkvereisten](#BKMK_testnetworkenvironment)  

 [Overzicht van de certificaten](#BKMK_overview2008)  

 [Implementeer het Webservercertificaat voor sitesystemen die IIS uitvoeren](#BKMK_webserver2008_cm2012)  

 [Het servicecertificaat voor cloud-gebaseerde distributiepunten implementeren](#BKMK_clouddp2008_cm2012)  

 [Het clientcertificaat voor Windows-computers implementeren](#BKMK_client2008_cm2012)  

 [Het clientcertificaat voor distributiepunten implementeren](#BKMK_clientdistributionpoint2008_cm2012)  

 [Het certificaat voor inschrijving voor mobiele apparaten implementeren](#BKMK_mobiledevices2008_cm2012)  

 [De certificaten voor AMT implementeren](#BKMK_AMT2008_cm2012)  

 [De certificaat-client voor Mac-computers implementeren](#BKMK_MacClient_SP1)  

##  <a name="BKMK_testnetworkenvironment"></a>Testnetwerkvereisten  
 De stapsgewijze instructies hebben de volgende vereisten:  

-   Het testnetwerk voert Active Directory Domain Services uit met Windows Server 2008 en is geïnstalleerd als een enkel domein, enkel forest.  

-   U hebt een lidserver die Windows Server 2008 Enterprise Edition uitvoert waarop is waarop de Active Directory Certificate Services-rol geïnstalleerd en is ingesteld als een enterprise-basiscertificeringsinstantie (CA).  

-   U hebt één computer met Windows Server 2008 (Standard Edition of Enterprise Edition R2 of hoger) is geïnstalleerd, die computer is aangewezen als een lidserver en Internet Information Services (IIS) is geïnstalleerd. Deze computer worden de systeemserver van de System Center Configuration Manager-site die u met een intranet FQDN-naam (Fully Qualified Domain Name configureren gaat) voor de ondersteuning van clientverbindingen op het intranet en een Internet-FQDN als ondersteuning van mobiele apparaten die zijn geregistreerd door System Center Configuration Manager en clients op het Internet.  

-   U hebt een Windows Vista-client die het meest recente servicepack geïnstalleerd en deze computer is ingesteld met een computernaam die ASCII-tekens bevat en is gekoppeld aan het domein. Deze computer is een System Center Configuration Manager-clientcomputer.  

-   U kunt zich aanmelden met een beheerdersaccount voor hoofddomein of een beheerdersaccount voor ondernemingsdomein en dit account gebruiken voor alle procedures in deze voorbeeldimplementatie.  

##  <a name="BKMK_overview2008"></a>Overzicht van de certificaten  
 De volgende tabel bevat de soorten PKI-certificaten die mogelijk zijn vereist voor System Center Configuration Manager en wordt beschreven hoe ze worden gebruikt.  

|Certificaatvereiste|Certificaatbeschrijving|  
|-----------------------------|-----------------------------|  
|Webservercertificaat voor sitesystemen die IIS uitvoeren|Dit certificaat wordt gebruikt om gegevens te coderen en de server te verifiëren naar clients. Het moet extern worden geïnstalleerd van System Center Configuration Manager op sitesysteemservers waarop Internet Information Services (IIS) wordt uitgevoerd en die zijn ingesteld in System Center Configuration Manager voor gebruik van HTTPS.<br /><br /> Zie voor de stappen voor het instellen en installeren van dit certificaat, [implementeren van het Webservercertificaat voor sitesystemen die IIS uitvoeren](#BKMK_webserver2008_cm2012) in dit onderwerp.|  
|Servicecertificaat voor clients voor verbinding maken met cloud-gebaseerde distributiepunten|Zie voor de stappen voor het configureren en dit certificaat installeren [het servicecertificaat voor cloud-gebaseerde distributiepunten implementeren](#BKMK_clouddp2008_cm2012) in dit onderwerp.<br /><br /> **Belangrijk:** Dit certificaat wordt gebruikt in combinatie met de Windows Azure-beheercertificaat. Zie voor meer informatie over het beheercertificaat [het maken van een Beheercertificaat](http://go.microsoft.com/fwlink/p/?LinkId=220281) en [een Beheercertificaat toevoegen aan een Windows Azure-abonnement](http://go.microsoft.com/fwlink/?LinkId=241722) in de Windows Azure-platformgedeelte van de MSDN-bibliotheek.|  
|Clientcertificaat voor Windows-computers|Dit certificaat wordt gebruikt voor verificatie van System Center Configuration Manager-clientcomputers naar sitesystemen die zijn ingesteld voor gebruik van HTTPS. Het kan ook worden gebruikt voor beheerpunten en statusmigratiepunten om hun bedrijfsstatus te controleren wanneer ze zijn ingesteld voor gebruik van HTTPS. Het moet extern worden geïnstalleerd van System Center Configuration Manager op computers.<br /><br /> Zie voor de stappen voor het instellen en installeren van dit certificaat, [het clientcertificaat voor Windows-computers implementeren](#BKMK_client2008_cm2012) in dit onderwerp.|  
|Clientcertificaat voor distributiepunten|Dit certificaat heeft twee doeleinden:<br /><br /> Het certificaat wordt gebruikt om het distributiepunt naar een HTTPS-beheerpunt te verifiëren voordat het distributiepunt statusberichten verzendt.<br /><br /> Wanneer de distributiepuntoptie **PXE-ondersteuning voor clients inschakelen** is geselecteerd, wordt het certificaat verzonden naar computers die een PXE-opstartbewerking uitvoeren, zodat ze verbinding kunnen maken met een HTTPS-beheerpunt tijdens de implementatie van het besturingssysteem.<br /><br /> Zie voor de stappen voor het instellen en installeren van dit certificaat, [het clientcertificaat voor distributiepunten implementeren](#BKMK_clientdistributionpoint2008_cm2012) in dit onderwerp.|  
|Certificaat voor inschrijving voor mobiele apparaten|Dit certificaat wordt gebruikt voor verificatie van System Center Configuration Manager-clients voor mobiele apparaten naar sitesystemen die zijn ingesteld voor gebruik van HTTPS. Het moet worden geïnstalleerd als onderdeel van de inschrijving van mobiele apparaten in System Center Configuration Manager en u het geconfigureerde certificaatsjabloon als een mobiel apparaatclientinstelling kiezen.<br /><br /> Zie voor de stappen voor het instellen van dit certificaat [implementeert het certificaat voor inschrijving voor mobiele apparaten](#BKMK_mobiledevices2008_cm2012) in dit onderwerp.|  
|Certificaten voor Intel AMT|Drie certificaten met betrekking tot out-of-band beheer voor Intel AMT gebaseerde computers:<ul><li>Een certificaat voor de inrichting Active Management Technology (AMT)</li><li>Een AMT-Webservercertificaat</li><li>U kunt desgewenst een certificaat voor clientverificatie voor 802.1 X bekabelde of draadloze netwerken</li></ul>Het certificaat van AMT-inrichting moet extern worden geïnstalleerd van System Center Configuration Manager op de computer out-of-band-service en u ervoor kiezen het geïnstalleerde certificaat in de eigenschappen van out-of-band-service. De AMT-Webservercertificaat en het certificaat voor clientverificatie worden geïnstalleerd tijdens AMT-inrichting en beheer en u de geconfigureerde certificaatsjablonen in de onderdeeleigenschappen voor buiten-bandbeheer kiezen.<br /><br /> Zie voor de stappen voor het instellen van deze certificaten [de certificaten voor AMT implementeren](#BKMK_AMT2008_cm2012) in dit onderwerp.|  
|Clientcertificaat voor Mac-computers|U kunt aanvragen en dit certificaat installeren vanaf een Mac-computer wanneer u System Center Configuration Manager-inschrijving gebruikt en het geconfigureerde certificaatsjabloon als een mobiel apparaatclientinstelling kiezen.<br /><br /> Zie voor de stappen voor het instellen van dit certificaat [het clientcertificaat voor Mac-computers implementeren](#BKMK_MacClient_SP1) in dit onderwerp.|  

##  <a name="BKMK_webserver2008_cm2012"></a>Implementeer het Webservercertificaat voor sitesystemen die IIS uitvoeren  
 Deze certificaatimplementatie heeft de volgende procedures:  

-   Maken en uitgeven van het sjabloon Webservercertificaat bij de certificeringsinstantie (CA)  

-   Het webservercertificaat aanvragen  

-   Configureren van IIS voor gebruik van het webservercertificaat  

###  <a name="BKMK_webserver22008"></a>Maken en uitgeven van het sjabloon Webservercertificaat bij de certificeringsinstantie (CA)  
 Met deze procedure maakt u een certificaatsjabloon voor System Center Configuration Manager-sitesystemen en voegt deze toe aan de certificeringsinstantie (CA).  

##### <a name="to-create-and-issue-the-web-server-certificate-template-on-the-certification-authority"></a>Maken en publiceren van het sjabloon webservercertificaat bij de certificeringsinstantie  

1.  Maak een beveiligingsgroep met de naam **ConfigMgr IIS Servers** waarvoor de lidservers voor het installeren van System Center Configuration Manager-sitesystemen die IIS gaan uitvoeren.  

2.  Op de lidserver waarop certificaatservices zijn geïnstalleerd, in de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen** en kies vervolgens **beheren** laden van de **certificaatsjablonen** console.  

3.  In het resultatenvenster met de rechtermuisknop op het item met **webserver** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

4.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren.  

5.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr-Webservercertificaat**, om de webcertificaten die worden gebruikt op Configuration Manager-sitesystemen te genereren.  

6.  Kies de **onderwerpnaam** tabblad en zorg ervoor dat **met de aanvraag meeleveren** is geselecteerd.  

7.  Kies de **beveiliging** tabblad, en verwijder vervolgens de **inschrijven** toestemming van de **Domeinadministrators** en **Ondernemingsadministrators** beveiligingsgroepen.  

8.  Kies **toevoegen**, voer **ConfigMgr IIS Servers** in de tekst in het vak en kies vervolgens **OK**.  

9. Kies de **inschrijven** machtiging voor deze groep en verwijder de **lezen** machtiging.  

10. Kies **OK**, en sluit vervolgens de **Certificaatsjablonenconsole**.  

11. In de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

12. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr-Webservercertificaat**, en kies vervolgens **OK**.  

13. Als u niet wilt maken en uitgeven van certificaten meer sluit **certificeringsinstantie (CA)**.  

###  <a name="BKMK_webserver32008"></a>Het webservercertificaat aanvragen  
 Deze procedure kunt u opgeven van het intranet en Internet-FQDN-waarden die zullen worden ingesteld in de systeemservereigenschappen en installeert het webservercertificaat installeren op de lidserver waarop IIS wordt uitgevoerd.  

##### <a name="to-request-the-web-server-certificate"></a>Het webservercertificaat aanvragen  

1.  Start opnieuw op de lidserver waarop IIS om ervoor te zorgen dat de computer toegang heeft tot de certificaatsjabloon die u hebt gemaakt met behulp van de **lezen** en **inschrijven** machtigingen die u hebt geconfigureerd.  

2.  Kies **Start**, kies **uitvoeren**, en typ vervolgens **mmc.exe.** Kies in de lege console **bestand**, en kies vervolgens **module toevoegen/verwijderen**.  

3.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **certificaten** uit de lijst met **beschikbare modules**, en kies vervolgens **toevoegen**.  

4.  In de **certificaat-module** dialoogvenster Kies **computeraccount**, en kies vervolgens **volgende**.  

5.  In de **Computer selecteren** dialoogvenster vak, zorg ervoor dat **lokale computer: (de computer waarop deze console wordt uitgevoerd)** is geselecteerd en kies vervolgens **voltooien**.  

6.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **OK**.  

7.  Vouw in de console **certificaten (lokale Computer)**, en kies vervolgens **persoonlijke**.  

8.  Met de rechtermuisknop op **certificaten**, kies **alle taken**, en kies vervolgens **nieuw certificaat aanvragen**.  

9. Op de **voordat u begint** pagina, kiest u **volgende**.  

10. Als u ziet de **Certificaatinschrijvingsbeleid selecteren** pagina, kiest u **volgende**.  

11. Op de **certificaten aanvragen** pagina, identificeert u de **ConfigMgr-Webservercertificaat** uit de lijst met beschikbare certificaten en kies vervolgens **meer gegevens nodig voor inschrijving voor dit certificaat. Klik hier om instellingen te configureren**.  

12. In de **certificaateigenschappen** het dialoogvenster de **onderwerp** tabblad, maakt u wijzigingen in **onderwerpnaam**. Dit betekent dat het vak **Waarde** voor het gedeelte **Onderwerpnaam leeg** blijft. In plaats daarvan uit de **alternatieve naam voor het** sectie, kiest u de **Type** vervolgkeuzelijst lijst en kies vervolgens **DNS**.  

13. In de **waarde** , geeft u de FQDN-waarden die u opgeeft in de sitesysteemeigenschappen van System Center Configuration Manager en kies vervolgens **OK** sluit de **certificaateigenschappen** in het dialoogvenster.  

     Voorbeelden:  

    -   Als het sitesysteem alleen clientverbindingen via het Internet accepteert, en de intranet-FQDN van de sitesysteemserver is **server1.internal.contoso.com**, voer **server1.internal.contoso.com**, en kies vervolgens **toevoegen**.  

    -   Als het sitesysteem clientverbindingen accepteert van het intranet en van internet, en de intranet-FQDN van de sitesysteemserver is **server1.internal.contoso.com** en de internet-FQDN van de sitesysteemserver is **server.contoso.com**:  

        1.  Voer **server1.internal.contoso.com**, en kies vervolgens **toevoegen**.  

        2.  Voer **server.contoso.com**, en kies vervolgens **toevoegen**.  

        > [!NOTE]  
        >  U kunt de FQDN-namen opgeven voor System Center Configuration Manager in elke gewenste volgorde. Controleer wel dat alle apparaten die gebruikmaken van het certificaat, zoals mobiele apparaten en proxywebservers, wordt een certificaat alternatieve naam van het onderwerp (SAN) en meerdere waarde in de SAN gebruiken kunnen. Als apparaten beperkt worden ondersteund voor SAN-waarden in certificaten, moet u mogelijk de volgorde van de FQDN's wijzigen of de onderwerpwaarde gebruiken.  

14. Op de **certificaten aanvragen** pagina, kiest u **ConfigMgr-Webservercertificaat** uit de lijst met beschikbare certificaten en kies vervolgens **inschrijven**.  

15. Op de **certificaatinstallatie** pagina, wacht totdat het certificaat is geïnstalleerd en kies vervolgens **voltooien**.  

16. Sluit **Certificaten (lokale computer)**.  

###  <a name="BKMK_webserver42008"></a>Configureren van IIS voor gebruik van het webservercertificaat  
 Met deze procedure koppelt u het geïnstalleerde certificaat aan de **IIS-standaardwebsite**.  

##### <a name="to-set-up-iis-to-use-the-web-server-certificate"></a>Instellen van IIS voor gebruik van het webservercertificaat  

1.  Kies op de lidserver waarop IIS is geïnstalleerd, **Start**, kiezen **programma's**, kies **Systeembeheer**, en kies vervolgens **Internet Information Services (IIS) Manager**.  

2.  Vouw **Sites**, met de rechtermuisknop op **Default Web Site**, en kies vervolgens **bindingen bewerken**.  

3.  Kies de **https** -item, en kies vervolgens **bewerken**.  

4.  In de **sitebinding bewerken** in het dialoogvenster selecteert u het certificaat dat u hebt aangevraagd met behulp van de ConfigMgr-webservercertificatensjabloon en kies vervolgens **OK**.  

    > [!NOTE]  
    >  Als u niet zeker dat het juiste certificaat is weet, kiest u een en kies vervolgens **weergave**. Hiermee kunt u met de certificaten in de module Certificaten in de geselecteerde certificaatgegevens vergelijken. De module Certificaten ziet u bijvoorbeeld het certificaatsjabloon dat is gebruikt voor het certificaat aanvragen. U kunt vervolgens vergelijken met de vingerafdruk van het certificaat dat was aangevraagd met behulp van de ConfigMgr-webservercertificatensjabloon naar de vingerafdruk van het certificaat dat momenteel is geselecteerd in de **sitebinding bewerken** in het dialoogvenster.  

5.  Kies **OK** in de **sitebinding bewerken** dialoogvenster vak en kies vervolgens **sluiten**.  

6.  Sluit **IIS-beheer**.  

 De lidserver wordt nu ingesteld met een System Center Configuration Manager-Webservercertificaat.  

> [!IMPORTANT]  
>  Wanneer u de System Center Configuration Manager-sitesysteemserver op deze computer installeert, zorg ervoor dat u dezelfde FQDN's in de sitesysteemeigenschappen opgeeft als die u specificeerde wanneer u het certificaat aanvroeg.  

##  <a name="BKMK_clouddp2008_cm2012"></a>Het servicecertificaat voor cloud-gebaseerde distributiepunten implementeren  

Deze certificaatimplementatie heeft de volgende procedures:  

-   [Maken en uitgeven van een aangepaste sjabloon Webservercertificaat bij de certificeringsinstantie (CA)](#BKMK_clouddpcreating2008)  

-   [Het aangepaste webservercertificaat aanvragen](#BKMK_clouddprequesting2008)  

-   [Exporteren van het aangepaste Webservercertificaat voor cloud-gebaseerde distributiepunten](#BKMK_clouddpexporting2008)  

###  <a name="BKMK_clouddpcreating2008"></a>Maken en uitgeven van een aangepaste sjabloon Webservercertificaat bij de certificeringsinstantie (CA)  
 Deze procedure maakt u een aangepast certificaatsjabloon dat is gebaseerd op het webservercertificaatsjabloon. Het certificaat is voor System Center Configuration Manager cloud-gebaseerde distributiepunten en de persoonlijke sleutel moet exporteerbaar zijn. Na het maken van het certificaatsjabloon, wordt het toegevoegd aan de certificeringsinstantie.  

> [!NOTE]  
>  Deze procedure maakt gebruik van een ander certificaatsjabloon dan het webservercertificaatsjabloon dat u hebt gemaakt voor sitesystemen die IIS uitvoeren. Hoewel beide certificaten serververificatie nodig, het certificaat voor cloud-gebaseerde distributiepunten een aangepaste waarde moet invoeren voor de onderwerpnaam en de persoonlijke sleutel moet worden geëxporteerd. Als een best practice bij beveiliging komen niet certificaatsjablonen zo instellen dat de persoonlijke sleutel kan worden geëxporteerd, tenzij dit vereist is. Het cloud-gebaseerde distributiepunt hebt deze configuratie nodig omdat u moet het certificaat als een bestand importeren, in plaats van het kiezen uit het certificaatarchief.  
>   
>  Wanneer u een nieuw certificaatsjabloon voor dit certificaat maakt, kunt u de computers die u kunnen een certificaat waarvan de persoonlijke sleutel kan worden geëxporteerd aanvragen kunt beperken. U kunt op een productienetwerk ook overwegen de volgende wijzigingen voor dit certificaat toe te voegen:  
>   
>  -   Goedkeuring vereisen voor het installeren van het certificaat voor extra beveiliging.  
> -   Vergroten van de geldigheidsduur van het certificaat. Omdat u moet exporteren en importeren van het certificaat iedere keer voordat het verloopt, vermindert u een toename van de geldigheidsperiode hoe vaak moet u deze procedure herhalen. Echter, een toename van de geldigheidsperiode ook vermindert de beveiliging van het certificaat omdat het meer tijd voor een aanvaller de persoonlijke sleutel te decoderen en het certificaat te stelen biedt.  
> -   Gebruik een aangepaste waarde in de SAN (Subject Alternative Name) van het certificaat om dit certificaat te onderscheiden van standaardwebservercertificaten die u bij IIS gebruikt.  

##### <a name="to-create-and-issue-the-custom-web-server-certificate-template-on-the-certification-authority"></a>Maken en uitgeven van het aangepaste sjabloon Webservercertificaat bij de certificeringsinstantie (CA)  

1.  Maak een beveiligingsgroep met de naam **siteservers** die de lidservers voor het installeren van System Center Configuration Manager primaire siteservers die cloud-gebaseerde distributiepunten gaan beheren is.  

2.  Op de lidserver waarop de certificeringsinstantieconsole, met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** om de beheerconsole van certificaatsjablonen te laden.  

3.  In het resultatenvenster met de rechtermuisknop op het item met **webserver** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

4.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren.  

5.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr Cloud-gebaseerde Distributiepuntcertificaat**, voor het genereren van het Webservercertificaat voor cloud-gebaseerde distributiepunten.  

6.  Kies de **afhandeling van aanvragen** tabblad en kies vervolgens **persoonlijke sleutel exporteerbaar**.  

7.  Kies de **beveiliging** tabblad, en verwijder vervolgens de **inschrijven** toestemming van de **Ondernemingsadministrators** beveiligingsgroep.  

8.  Kies **toevoegen**, voer **siteservers** in de tekst vak en kies vervolgens **OK**.  

9. Selecteer de machtiging **Inschrijving** voor deze groep en verwijder de machtiging **Lezen** niet.  

10. Kies **OK**, en sluit vervolgens **Certificaatsjablonenconsole**.  

11. In de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

12. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr Cloud-gebaseerde Distributiepuntcertificaat**, en kies vervolgens **OK**.  

13. Als u geen moet maken en uitgeven van certificaten meer sluit **certificeringsinstantie (CA)**.  

###  <a name="BKMK_clouddprequesting2008"></a>Het aangepaste webservercertificaat aanvragen  
 Deze procedure vraagt en installeert het aangepaste Webservercertificaat op de lidserver die de siteserver gaat uitvoeren.  

##### <a name="to-request-the-custom-web-server-certificate"></a>Het aangepaste webservercertificaat aanvragen  

1.  Start de lidserver opnieuw op nadat u hebt gemaakt en configureer de **siteservers** beveiligingsgroep om ervoor te zorgen dat de computer toegang heeft tot de certificaatsjabloon die u hebt gemaakt met behulp van de **lezen** en **inschrijven** machtigingen die u hebt geconfigureerd.  

2.  Kies **Start**, kies **uitvoeren**, en voer vervolgens **mmc.exe.** Kies in de lege console **bestand**, en kies vervolgens **module toevoegen/verwijderen**.  

3.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **certificaten** uit de lijst met **beschikbare modules**, en kies vervolgens **toevoegen**.  

4.  In de **certificaat-module** dialoogvenster Kies **computeraccount**, en kies vervolgens **volgende**.  

5.  In de **Computer selecteren** dialoogvenster vak, zorg ervoor dat **lokale computer: (de computer waarop deze console wordt uitgevoerd)** is geselecteerd en kies vervolgens **voltooien**.  

6.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **OK**.  

7.  Vouw in de console **certificaten (lokale Computer)**, en kies vervolgens **persoonlijke**.  

8.  Met de rechtermuisknop op **certificaten**, kies **alle taken**, en kies vervolgens **nieuw certificaat aanvragen**.  

9. Op de **voordat u begint** pagina, kiest u **volgende**.  

10. Als u ziet de **Certificaatinschrijvingsbeleid selecteren** pagina, kiest u **volgende**.  

11. Op de **certificaten aanvragen** pagina, identificeert u de **ConfigMgr Cloud-gebaseerde Distributiepuntcertificaat** uit de lijst met beschikbare certificaten en kies vervolgens **informatie is vereist voor het inschrijven voor dit certificaat. hier om instellingen te configureren**.  

12. In de **certificaateigenschappen** het dialoogvenster de **onderwerp** tabblad voor de **onderwerpnaam**, kies **algemene naam** als de **Type**.  

13. Geef in het vak **Waarde** uw keuze op voor de servicenaam en uw domeinnaam met een FQDN-indeling. Bijvoorbeeld: **clouddp1.contoso.com**.  

    > [!NOTE]  
    >  Controleer de naam van de service uniek is in uw naamruimte. U gebruikt DNS om een alias (CNAME-record) te maken om deze servicenaam toe te wijzen aan een automatisch gegenereerd id (GUID) en een IP-adres van Windows Azure.  

14. Kies **toevoegen**, en kies vervolgens **OK** sluit de **certificaateigenschappen** in het dialoogvenster.  

15. Op de **certificaten aanvragen** pagina, kiest u **ConfigMgr Cloud-gebaseerde Distributiepuntcertificaat** uit de lijst met beschikbare certificaten en kies vervolgens **inschrijven**.  

16. Op de **certificaatinstallatie** pagina, wacht totdat het certificaat is geïnstalleerd en kies vervolgens **voltooien**.  

17. Sluit **Certificaten (lokale computer)**.  

###  <a name="BKMK_clouddpexporting2008"></a>Exporteren van het aangepaste Webservercertificaat voor cloud-gebaseerde distributiepunten  
 Met deze procedure exporteert u het aangepaste webservercertificaat naar een bestand zodat het kan worden geïmporteerd wanneer u het cloud-gebaseerde distributiepunt maakt.  

##### <a name="to-export-the-custom-web-server-certificate-for-cloud-based-distribution-points"></a>Exporteren van het aangepaste webservercertificaat voor cloud-gebaseerde distributiepunten  

1.  In de **certificaten (lokale Computer)** console, met de rechtermuisknop op het certificaat dat u zojuist hebt geïnstalleerd, kiest u **alle taken**, en kies vervolgens **exporteren**.  

2.  Kies in de Wizard certificaten exporteren **volgende**.  

3.  Op de **persoonlijke sleutel exporteren** pagina, kiest u **Ja, de persoonlijke sleutel exporteren**, en kies vervolgens **volgende**.  

    > [!NOTE]  
    >  Als deze optie niet beschikbaar is, is het certificaat gemaakt zonder de optie om de persoonlijke sleutel te exporteren. In dit scenario kunt u het certificaat niet exporteren in de vereiste indeling. U moet het certificaatsjabloon instellen zodat de persoonlijke sleutel kan worden geëxporteerd en het certificaat vervolgens opnieuw aanvragen.  

4.  Op de **bestandsindeling voor Export** pagina, zorg ervoor dat de **Personal Information Exchange - PKCS #12 (. (PFX)** optie is geselecteerd.  

5.  Op de **wachtwoord** pagina, geeft u een sterk wachtwoord in om het geëxporteerde certificaat te beschermen met de persoonlijke sleutel en kies vervolgens **volgende**.  

6.  Op de **te exporteren bestand** pagina, geeft u de naam van het bestand dat u wilt exporteren, en kies vervolgens **volgende**.  

7.  Sluit de wizard, kies **voltooien** in de **Wizard Certificaat exporteren** pagina en kies vervolgens **OK** in het bevestigingsvenster.  

8.  Sluit **Certificaten (lokale computer)**.  

9. Sla het bestand veilig op en zorg ervoor dat u deze vanaf de System Center Configuration Manager-console openen kunt.  

 Het certificaat kan nu worden geïmporteerd wanneer u een cloud-gebaseerd distributiepunt maakt.  

##  <a name="BKMK_client2008_cm2012"></a>Het clientcertificaat voor Windows-computers implementeren  
 Deze certificaatimplementatie heeft de volgende procedures:  

-   Maken en publiceren van het certificaatsjabloon voor verificatie van werkstation bij de certificeringsinstantie (CA)  

-   Configureren van automatische inschrijving van de sjabloon voor verificatie van werkstation met behulp van Groepsbeleid  

-   Automatisch inschrijven van het certificaat voor verificatie van werkstation en de installatie verifiëren op computers  

###  <a name="BKMK_client02008"></a>Maken en publiceren van het certificaatsjabloon voor verificatie van werkstation bij de certificeringsinstantie (CA)  
 Met deze procedure maakt u een certificaatsjabloon voor System Center Configuration Manager-client computers en voegt deze toe aan de certificeringsinstantie (CA).  

##### <a name="to-create-and-issue-the-workstation-authentication-certificate-template-on-the-certification-authority"></a>Maken en publiceren van het certificaatsjabloon voor verificatie van werkstation bij de certificeringsinstantie  

1.  Op de lidserver waarop de certificeringsinstantieconsole, met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** om de beheerconsole van certificaatsjablonen te laden.  

2.  In het resultatenvenster met de rechtermuisknop op het item met **verificatie van werkstation** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

3.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren.  

4.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr-clientcertificaat**, om de clientcertificaten die worden gebruikt op Configuration Manager-clientcomputers te genereren.  

5.  Kies de **beveiliging** tabblad de **Domeincomputers** groeperen en selecteer vervolgens de extra machtigingen voor **lezen** en **automatische inschrijving**. **Inschrijven**niet wissen.  

6.  Kies **OK**, en sluit vervolgens **Certificaatsjablonenconsole**.  

7.  In de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

8.  In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr-clientcertificaat**, en kies vervolgens **OK**.  

9. Als u niet wilt maken en uitgeven van certificaten meer sluit **certificeringsinstantie (CA)**.  

###  <a name="BKMK_client12008"></a>Configureren van automatische inschrijving van de sjabloon voor verificatie van werkstation met behulp van Groepsbeleid  
 Deze procedure stelt Groepsbeleid voor automatische inschrijving van het clientcertificaat op computers.  

##### <a name="to-set-up-autoenrollment-of-the-workstation-authentication-template-by-using-group-policy"></a>Instellen van automatische inschrijving van de sjabloon voor verificatie van werkstation met behulp van Groepsbeleid  

1.  Kies op de domeincontroller **Start**, kies **Systeembeheer**, en kies vervolgens **Groepsbeleidsbeheer**.  

2.  Ga naar uw domein met de rechtermuisknop op het domein en kies vervolgens **een groepsbeleidsobject in dit domein maken en hier een koppeling**.  

    > [!NOTE]  
    >  De aanbevolen werkwijze voor deze stap is nieuw groepsbeleid maken voor aangepaste instellingen in plaats van het standaardgroepsbeleid te bewerken dat is geïnstalleerd met Active Directory Domain Services. Als u dit groepsbeleid op domeinniveau toewijst, wordt u deze toepassen op alle computers in het domein. In een productieomgeving, kunt u automatische inschrijving wel zodanig beperken dat inschrijving op alleen de geselecteerde computers plaatsvindt. U kunt het groepsbeleid op het niveau van een organisatie-eenheid toewijzen of u kunt het domein Group Policy with een beveiligingsgroep filteren zodat het alleen van toepassing op de computers in de groep. Als u automatische inschrijving beperkt, vergeet dan niet de server die is ingesteld als het beheerpunt op te nemen.  

3.  In de **nieuw groepsbeleidsobject** dialoogvenster, voert u een naam, zoals **automatische inschrijvingscertificaten**, voor het nieuwe Groepsbeleid en kies vervolgens **OK**.  

4.  In het resultatenvenster op de **gekoppelde groepsbeleidsobjecten** tabblad, met de rechtermuisknop op het nieuwe Groepsbeleid en kies vervolgens **bewerken**.  

5.  In de **Editor voor Groepsbeleidsbeheer**, vouw **beleid** onder **Computerconfiguratie**, en ga vervolgens naar **Windows-instellingen** / **beveiligingsinstellingen** / **beleid voor openbare sleutels**.  

6.  Met de rechtermuisknop op het objecttype met de naam **Certificate Services-Client - automatisch inschrijven**, en kies vervolgens **eigenschappen**.  

7.  Van de **configuratiemodel** vervolgkeuzelijst Kies **ingeschakeld**, kies **verlopen certificaten vernieuwen, aangevraagde certificaten bijwerken, ingetrokken certificaten verwijderen**, kies **certificaten bijwerken die gebruikmaken van certificaatsjablonen**, en kies vervolgens **OK**.  

8.  Sluit **Groepsbeleidsbeheer**.  

###  <a name="BKMK_client22008"></a>Automatisch inschrijven van het certificaat voor verificatie van werkstation en de installatie verifiëren op computers  
 Met deze procedure installeert u het clientcertificaat op computers en verifieert u de installatie.  

##### <a name="to-automatically-enroll-the-workstation-authentication-certificate-and-verify-its-installation-on-the-client-computer"></a>Automatisch inschrijven van het certificaat voor verificatie van werkstation en de installatie verifiëren op de clientcomputer  

1.  Start de Werkstationcomputer opnieuw op en wacht enkele minuten duren voordat u zich aanmeldt.  

    > [!NOTE]  
    >  Opstarten van een computer is de betrouwbaarste methode voor een goed verloop van automatische inschrijving voor certificaten.  

2.  Meld u aan met een account met beheerdersbevoegdheden.  

3.  Voer in het zoekvak **mmc.exe.**, en druk vervolgens op **Enter**.  

4.  Kies in de lege beheerconsole **bestand**, en kies vervolgens **module toevoegen/verwijderen**.  

5.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **certificaten** uit de lijst met **beschikbare modules**, en kies vervolgens **toevoegen**.  

6.  In de **certificaat-module** dialoogvenster Kies **computeraccount**, en kies vervolgens **volgende**.  

7.  In de **Computer selecteren** dialoogvenster vak, zorg ervoor dat **lokale computer: (de computer waarop deze console wordt uitgevoerd)** is geselecteerd en kies vervolgens **voltooien**.  

8.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **OK**.  

9. Vouw in de console **certificaten (lokale Computer)**, vouw **persoonlijke**, en kies vervolgens **certificaten**.  

10. In het deelvenster met resultaten bevestigen dat een certificaat heeft **clientverificatie** in de **beoogd doeleinde** kolom en die **ConfigMgr-clientcertificaat** bevindt zich in de **certificaatsjabloon** kolom.  

11. Sluit **Certificaten (lokale computer)**.  

12. Herhaal de stappen 1 tot en met 11 voor de lidserver om te controleren of de server die zal worden ingesteld als het beheerpunt ook een clientcertificaat heeft.  

 De computer is nu ingesteld met een clientcertificaat voor System Center Configuration Manager.  

##  <a name="BKMK_clientdistributionpoint2008_cm2012"></a>Het clientcertificaat voor distributiepunten implementeren  

> [!NOTE]  
>  Dit certificaat kan ook worden gebruikt voor media-afbeeldingen die geen PXE-opstartapparaat gebruiken omdat de certificaatvereisten dezelfde zijn.  

 Deze certificaatimplementatie heeft de volgende procedures:  

-   Maken en publiceren van een aangepast certificaatsjabloon voor verificatie van werkstation bij de certificeringsinstantie  

-   Het aangepaste certificaat voor verificatie van werkstation aanvragen  

-   Het clientcertificaat voor distributiepunten exporteren  

###  <a name="BKMK_clientdistributionpoint02008"></a>Maken en publiceren van een aangepast certificaatsjabloon voor verificatie van werkstation bij de certificeringsinstantie  
 Deze procedure maakt u een aangepast certificaatsjabloon voor System Center Configuration Manager-distributiepunten de persoonlijke sleutel kan worden geëxporteerd en voegt u certificaatsjabloon toe aan de certificeringsinstantie.  

> [!NOTE]  
>  Deze procedure maakt gebruik van een ander certificaatsjabloon dan het certificaatsjabloon dat u hebt gemaakt voor clientcomputers. Hoewel beide certificaten clientverificatie nodig, is het certificaat voor distributiepunten dat de persoonlijke sleutel worden geëxporteerd. Als een best practice bij beveiliging kan niet worden ingesteld certificaatsjablonen zodat de persoonlijke sleutel kan worden geëxporteerd, tenzij dit vereist is. Het distributiepunt hebt deze configuratie nodig omdat u moet het certificaat als een bestand importeren in plaats van het kiezen uit het certificaatarchief.  
>   
>  Wanneer u een nieuw certificaatsjabloon voor dit certificaat maakt, kunt u de computers die u kunnen een certificaat waarvan de persoonlijke sleutel kan worden geëxporteerd aanvragen kunt beperken. In ons implementatievoorbeeld is dit de beveiligingsgroep die u eerder hebt gemaakt voor System Center Configuration Manager-sitesysteemservers die IIS uitvoeren. Overweeg een nieuwe beveiligingsgroep voor een productienetwerk dat de IIS-sitesysteemrollen distribueert voor de servers die distributiepunten uitvoeren zodat u het certificaat kunt beperken tot alleen deze sitesysteemservers. U kunt ook overwegen de volgende wijzigingen toe te voegen voor dit certificaat:  
>   
>  -   Goedkeuring vereisen voor het installeren van het certificaat voor extra beveiliging.  
> -   Vergroten van de geldigheidsduur van het certificaat. Omdat u moet exporteren en importeren van het certificaat iedere keer voordat het verloopt, vermindert u een toename van de geldigheidsperiode hoe vaak moet u deze procedure herhalen. Echter, een toename van de geldigheidsperiode ook vermindert de beveiliging van het certificaat omdat het meer tijd voor een aanvaller de persoonlijke sleutel te decoderen en het certificaat te stelen biedt.  
> -   Gebruik een aangepaste waarde in het veld Onderwerp of SAN (Subject Alternative Name) om dit certificaat te onderscheiden van standaardclientcertificaten. Dit kan vooral nuttig zijn als u hetzelfde certificaat gaat gebruiken voor meerdere distributiepunten.  

##### <a name="to-create-and-issue-the-custom-workstation-authentication-certificate-template-on-the-certification-authority"></a>Maken en publiceren van het aangepaste certificaatsjabloon voor verificatie van werkstation bij de certificeringsinstantie  

1.  Op de lidserver waarop de certificeringsinstantieconsole, met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** om de beheerconsole van certificaatsjablonen te laden.  

2.  In het resultatenvenster met de rechtermuisknop op het item met **verificatie van werkstation** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

3.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren.  

4.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr-Clientdistributiepuntcertificaat**, voor het genereren van het certificaat voor clientverificatie voor distributiepunten.  

5.  Kies de **afhandeling van aanvragen** tabblad en kies vervolgens **persoonlijke sleutel exporteerbaar**.  

6.  Kies de **beveiliging** tabblad, en verwijder vervolgens de **inschrijven** toestemming van de **Ondernemingsadministrators** beveiligingsgroep.  

7.  Kies **toevoegen**, voer **ConfigMgr IIS Servers** in de tekst in het vak en kies vervolgens **OK**.  

8.  Selecteer de machtiging **Inschrijving** voor deze groep en verwijder de machtiging **Lezen** niet.  

9. Kies **OK**, en sluit vervolgens **Certificaatsjablonenconsole**.  

10. In de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

11. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr-Clientdistributiepuntcertificaat**, en kies vervolgens **OK**.  

12. Als u geen moet maken en uitgeven van certificaten meer sluit **certificeringsinstantie (CA)**.  

###  <a name="BKMK_clientdistributionpoint12008"></a>Het aangepaste certificaat voor verificatie van werkstation aanvragen  
 Deze procedure vraagt en installeert u het aangepaste clientcertificaat installeren op de lidserver die IIS uitvoert en die wordt ingesteld als een distributiepunt.  

##### <a name="to-request-the-custom-workstation-authentication-certificate"></a>Het aangepaste certificaat voor verificatie van werkstation aanvragen  

1.  Kies **Start**, kies **uitvoeren**, en voer vervolgens **mmc.exe.** Kies in de lege console **bestand**, en kies vervolgens **module toevoegen/verwijderen**.  

2.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **certificaten** uit de lijst met **beschikbare modules**, en kies vervolgens **toevoegen**.  

3.  In de **certificaat-module** dialoogvenster Kies **computeraccount**, en kies vervolgens **volgende**.  

4.  In de **Computer selecteren** dialoogvenster vak, zorg ervoor dat **lokale computer: (de computer waarop deze console wordt uitgevoerd)** is geselecteerd en kies vervolgens **voltooien**.  

5.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **OK**.  

6.  Vouw in de console **certificaten (lokale Computer)**, en kies vervolgens **persoonlijke**.  

7.  Met de rechtermuisknop op **certificaten**, kies **alle taken**, en kies vervolgens **nieuw certificaat aanvragen**.  

8.  Op de **voordat u begint** pagina, kiest u **volgende**.  

9. Als u ziet de **Certificaatinschrijvingsbeleid selecteren** pagina, kiest u **volgende**.  

10. Op de **certificaten aanvragen** pagina, kiest u **ConfigMgr-Clientdistributiepuntcertificaat** uit de lijst met beschikbare certificaten en kies vervolgens **inschrijven**.  

11. Op de **certificaatinstallatie** pagina, wacht totdat het certificaat is geïnstalleerd en kies vervolgens **voltooien**.  

12. In het deelvenster met resultaten bevestigen dat een certificaat heeft **clientverificatie** in de **beoogd doeleinde** kolom en die **ConfigMgr-Clientdistributiepuntcertificaat** bevindt zich in de **certificaatsjabloon** kolom.  

13. **Certificaten (lokale computer)**niet sluiten.  

###  <a name="BKMK_exportclientdistributionpoint22008"></a>Het clientcertificaat voor distributiepunten exporteren  
 Deze procedure exporteert u het aangepaste certificaat voor verificatie van werkstation naar een bestand zodat het kan worden geïmporteerd in de eigenschappen van het distributiepunt.  

##### <a name="to-export-the-client-certificate-for-distribution-points"></a>Exporteren van het clientcertificaat voor distributiepunten  

1.  In de **certificaten (lokale Computer)** console, met de rechtermuisknop op het certificaat dat u zojuist hebt geïnstalleerd, kiest u **alle taken**, en kies vervolgens **exporteren**.  

2.  Kies in de Wizard certificaten exporteren **volgende**.  

3.  Op de **persoonlijke sleutel exporteren** pagina, kiest u **Ja, de persoonlijke sleutel exporteren**, en kies vervolgens **volgende**.  

    > [!NOTE]  
    >  Als deze optie niet beschikbaar is, is het certificaat gemaakt zonder de optie om de persoonlijke sleutel te exporteren. In dit scenario kunt u het certificaat niet exporteren in de vereiste indeling. U moet het certificaatsjabloon instellen zodat de persoonlijke sleutel kan worden geëxporteerd en het certificaat vervolgens opnieuw aanvragen.  

4.  Op de **bestandsindeling voor Export** pagina, zorg ervoor dat de **Personal Information Exchange - PKCS #12 (. (PFX)** optie is geselecteerd.  

5.  Op de **wachtwoord** pagina, geeft u een sterk wachtwoord in om het geëxporteerde certificaat te beschermen met de persoonlijke sleutel en kies vervolgens **volgende**.  

6.  Op de **te exporteren bestand** pagina, geeft u de naam van het bestand dat u wilt exporteren, en kies vervolgens **volgende**.  

7.  Sluit de wizard, kies **voltooien** op de **Wizard Certificaat exporteren** pagina en kies **OK** in het bevestigingsvenster.  

8.  Sluit **Certificaten (lokale computer)**.  

9. Sla het bestand veilig op en zorg ervoor dat u deze vanaf de System Center Configuration Manager-console openen kunt.  

 Het certificaat kan nu worden geïmporteerd bij het instellen van het distributiepunt.  

> [!TIP]  
>  U kunt hetzelfde certificaatbestand gebruiken bij het instellen van media-afbeeldingen voor de implementatie van een besturingssysteem waarbij geen PXE-opstartapparaat wordt gebruikt en de takenreeks om de installatiekopie te installeren moet contact maken met een beheerpunt waarvoor HTTPS-clientverbindingen.  

##  <a name="BKMK_mobiledevices2008_cm2012"></a>Het certificaat voor inschrijving voor mobiele apparaten implementeren  
 Voor deze certificaatimplementatie wordt een enkele procedure gebruikt om het certificaatsjabloon voor inschrijving te maken en het te publiceren bij de certificeringsinstantie.  

### <a name="create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>Maken en publiceren van het certificaatsjabloon voor inschrijving bij de certificeringsinstantie  
 Met deze procedure maakt u een certificaatsjabloon voor inschrijving voor System Center Configuration Manager mobiele apparaten en voegt deze toe aan de certificeringsinstantie (CA).  

##### <a name="to-create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>Maken en publiceren van het certificaatsjabloon voor inschrijving bij de certificeringsinstantie  

1.  Maak een beveiligingsgroep met gebruikers die in System Center Configuration Manager voor mobiele apparaten gaan registreren.  

2.  Op de lidserver waarop certificaatservices zijn geïnstalleerd, in de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** om de beheerconsole van certificaatsjablonen te laden.  

3.  In het resultatenvenster met de rechtermuisknop op het item met **geverifieerde sessie** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

4.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren.  

5.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr-certificaat in de inschrijving van mobiele apparaten**, voor het genereren van de inschrijving van certificaten voor mobiele apparaten worden beheerd door System Center Configuration Manager.  

6.  Kies de **onderwerpnaam** tabblad, zorg ervoor dat **basis van Active Directory-informatie samenstellen** is geselecteerd, selecteer **algemene naam** voor de **indeling van de onderwerpnaam:**, en schakel vervolgens **UPN (User Principal name)** van **deze informatie opnemen in alternatieve onderwerpnaam**.  

7.  Kies de **beveiliging** tabblad, kiest u de beveiligingsgroep die gebruikers met mobiele apparaten inschrijven en kies vervolgens de extra machtiging **inschrijven**. **Lezen**niet wissen.  

8.  Kies **OK**, en sluit vervolgens **Certificaatsjablonenconsole**.  

9. In de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

10. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr-certificaat in de inschrijving van mobiele apparaten**, en kies vervolgens **OK**.  

11. Als u niet nodig hebt om te maken en uitgeven van certificaten meer, sluit u de console certificeringsinstantie (CA).  

 Het certificaatsjabloon voor mobiele apparaten voor inschrijving is nu gereed om te worden geselecteerd bij het instellen van een inschrijvingsprofiel voor mobiele apparaten in de clientinstellingen.  

##  <a name="BKMK_AMT2008_cm2012"></a>De certificaten voor AMT implementeren  
 Deze certificaatimplementatie heeft de volgende procedures:  

-   Maken, uitgeven en installeren van de AMT-inrichtingscertificaat  

-   Maken en publiceren van het Webservercertificaat voor op AMT gebaseerde computers  

-   Maken en publiceren van de client-certificaten voor clientverificaties voor 802.1 X AMT-gebaseerde computers  

###  <a name="BKMK_AMTprovisioning2008"></a>Maken, uitgeven en installeren van de AMT-inrichtingscertificaat  
 Maak het inrichtingscertificaat met uw interne Certificeringsinstantie wanneer de AMT-gebaseerde computers worden ingesteld met de vingerafdruk van het certificaat van uw interne basiscertificeringsinstantie. Als dit niet het geval is en moet u een externe certificeringsinstantie gebruiken, gebruikt u de instructies van het bedrijf dat de AMT-inrichtingscertificaat, waarbij wordt vaak aanvragen van het certificaat van de openbare website van het bedrijf uitgegeven. U vindt ook uitgebreide instructies voor de door u gekozen externe Certificeringsinstantie in de [Intel vPro Expert Center: Microsoft vPro Manageability-website](http://go.microsoft.com/fwlink/?LinkId=132001).  

> [!IMPORTANT]  
>  Externe certificeringsinstanties ondersteunen mogelijk niet de AMT-inrichtingsobject-id van Intel. Wanneer dit het geval is, geef de **Intel(R) Clientinstallatiecertificaat** OE-kenmerk.  

 Wanneer u een AMT-inrichtingscertificaat van een externe Certificeringsinstantie aanvraagt, installeert u het certificaat in de Computer persoonlijke certificaatarchief op de server die als voor de out-of-band-servicepunt host fungeert.  

##### <a name="to-request-and-issue-the-amt-provisioning-certificate"></a>Aanvragen en uitgeven van het certificaat voor AMT-inrichting  

1.  Maak een beveiligingsgroep die de computeraccounts van sitesysteemservers waarop het out-of-band-servicepunt heeft.  

2.  Op de lidserver waarop certificaatservices zijn geïnstalleerd, in de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** laden van de **certificaatsjablonen** console.  

3.  In het resultatenvenster met de rechtermuisknop op het item met **webserver** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

4.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren.  

5.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr AMT-inrichting**, voor de certificaatsjabloon voor AMT-inrichting.  

6.  Kies de **onderwerpnaam** Kies **basis van Active Directory-informatie samenstellen**, en kies vervolgens **algemene naam**.  

7.  Kies de **extensies** tabblad, zorg ervoor dat **toepassingsbeleid** is geselecteerd en kies vervolgens **bewerken**.  

8.  In de **Toepassingenbeleidsuitbreiding bewerken** dialoogvenster Kies **toevoegen**.  

9. In de **Toepassingenbeleid toevoegen** dialoogvenster Kies **New**.  

10. In de **Nieuw toepassingenbeleid** dialoogvenster Voer **AMT-inrichting** in de **naam** veld en voer vervolgens het volgende nummer voor de **Object-id**: **2.16.840.1.113741.1.2.3**.  

11. Kies **OK**, en kies vervolgens **OK** in de **Toepassingenbeleid toevoegen** in het dialoogvenster.  

12. Kies **OK** in de **Toepassingenbeleidsuitbreiding bewerken** in het dialoogvenster.  

13. In de **eigenschappen van nieuwe sjabloon** in het dialoogvenster het volgende wordt vermeld als de **toepassingsbeleid** beschrijving: **Serververificatie** en **AMT-inrichting**.  

14. Kies de **beveiliging** tabblad, en verwijder vervolgens de **inschrijven** toestemming van de **Domeinadministrators** en **Ondernemingsadministrators** beveiligingsgroepen.  

15. Kies **toevoegen**, voer de naam van een beveiligingsgroep die het computeraccount voor de sitesysteemrol out-of-band-service heeft en kies vervolgens **OK**.  

16. Kies de **inschrijven** machtiging voor deze groep en verwijder de **lezen** machtiging...  

17. Kies **OK**, en sluit vervolgens de **certificaatsjablonen** console.  

18. In **certificeringsinstantie (CA)**, met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

19. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr AMT-inrichting**, en kies vervolgens **OK**.  

    > [!NOTE]  
    >  Als u de stappen 18 of 19 niet kunt voltooien, controleer dan of u de Enterprise Edition van Windows Server 2008 gebruikt. Hoewel u een sjabloon met Windows Server Standard Edition en Certificate Services instellen kunt, kunt u certificaten niet implementeren met behulp van gewijzigde certificaatsjablonen, tenzij u de Enterprise Edition van Windows Server 2008.  

20. **Certificeringsinstantie**niet sluiten.  

 Het certificaat voor AMT-inrichting van uw interne Certificeringsinstantie is nu gereed om te worden geïnstalleerd op de computer out-of-band-service.  

##### <a name="to-install-the-amt-provisioning-certificate"></a>Installeren van het certificaat voor AMT-inrichting  

1.  Start opnieuw op de lidserver waarop IIS om ervoor te zorgen dat deze met de ingestelde machtiging het certificaatsjabloon kan openen.  

2.  Kies **Start**, kies **uitvoeren**, en voer vervolgens **mmc.exe.** Kies in de lege console **bestand**, en kies vervolgens **module toevoegen/verwijderen**.  

3.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **certificaten** uit de lijst met **beschikbare modules**, en kies vervolgens **toevoegen**.  

4.  In de **certificaat-module** dialoogvenster Kies **computeraccount**, en kies vervolgens **volgende**.  

5.  In de **Computer selecteren** dialoogvenster vak, zorg ervoor dat **lokale computer: (de computer waarop deze console wordt uitgevoerd)** is geselecteerd en kies vervolgens **voltooien**.  

6.  In de **toevoegen of verwijderen van modules** dialoogvenster Kies **OK**.  

7.  Vouw in de console **certificaten (lokale Computer)**, en kies vervolgens **persoonlijke**.  

8.  Met de rechtermuisknop op **certificaten**, kies **alle taken**, en kies vervolgens **nieuw certificaat aanvragen**.  

9. Op de **voordat u begint** pagina, kiest u **volgende**.  

10. Als u ziet de **Certificaatinschrijvingsbeleid selecteren** pagina, kiest u **volgende**.  

11. Op de **certificaten aanvragen** optie **AMT-inrichting** uit de lijst met beschikbare certificaten en kies vervolgens **inschrijven**.  

12. Op de **certificaatinstallatie** pagina, wacht totdat het certificaat is geïnstalleerd en kies vervolgens **voltooien**.  

13. Sluit **Certificaten (lokale computer)**.  

 Het certificaat voor AMT-inrichting van uw interne Certificeringsinstantie is nu geïnstalleerd en is gereed om te worden geselecteerd in de eigenschappen van out-of-band-service.  

### <a name="create-and-issue-the-web-server-certificate-for-amt-based-computers"></a>Maken en publiceren van het Webservercertificaat voor op AMT gebaseerde computers  
 Gebruik de volgende procedure om de webservercertificaten voor op AMT-gebaseerde computers voor te bereiden.  

##### <a name="to-create-and-issue-the-web-server-certificate-template"></a>Maken en uitgeven van het certificaatsjabloon.  

1.  Maak een lege beveiligingsgroep met de AMT-computeraccounts die System Center Configuration Manager tijdens AMT-inrichting maakt.  

2.  Op de lidserver waarop certificaatservices zijn geïnstalleerd, in de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** laden van de **certificaatsjablonen** console.  

3.  In het resultatenvenster met de rechtermuisknop op het item met **webserver** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

4.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition.**  

5.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr AMT-Webservercertificaat**, om de webcertificaten die worden gebruikt voor out-of-band-beheer op AMT-computers te genereren.  

6.  Kies de **onderwerpnaam** Kies **basis van Active Directory-informatie samenstellen**, kies **algemene naam** voor de **indeling van de onderwerpnaam**, en schakel vervolgens **UPN (User Principal name)** voor de alternatieve onderwerpnaam.  

7.  Kies de **beveiliging** tabblad, en verwijder vervolgens de **inschrijven** toestemming van de **Domeinadministrators** en **Ondernemingsadministrators** beveiligingsgroepen.  

8.  Kies **toevoegen**, en voer de naam van de beveiligingsgroep die u hebt gemaakt voor AMT-inrichting en kies vervolgens **OK**.  

9. Kies de volgende **toestaan** machtigingen voor deze beveiligingsgroep: **Lees** en **inschrijven**.  

10. Kies **OK**, en sluit vervolgens de **certificaatsjablonen** console.  

11. In de **certificeringsinstantie (CA)** console, met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

12. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr AMT-Webservercertificaat**, en kies vervolgens **OK**.  

13. Als u geen moet maken en uitgeven van certificaten meer sluit **certificeringsinstantie (CA)**.  

 Het AMT-webserversjabloon is nu gereed voor het instellen van AMT-gebaseerde computers met webservercertificaten. Deze certificaatsjabloon selecteert in de onderdeeleigenschappen voor buiten-bandbeheer.  

### <a name="create-and-issue-the-client-authentication-certificates-for-8021x-amt-based-computers"></a>Maken en publiceren van de client-certificaten voor clientverificaties voor 802.1 X AMT-gebaseerde computers  
 Gebruik de volgende procedure als op AMT-gebaseerde computers clientcertificaten gaan gebruiken voor 802.1X-geverifieerde bekabelde en draadloze netwerken.  

##### <a name="to-create-and-issue-the-client-authentication-certificate-template-on-the-ca"></a>Maken en uitgeven van het certificaatsjabloon voor clientverificatie bij de certificeringsinstantie  

1.  Op de lidserver waarop certificaatservices zijn geïnstalleerd, in de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** laden van de **certificaatsjablonen** console.  

2.  In het resultatenvenster met de rechtermuisknop op het item met **verificatie van werkstation** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition.**  

3.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr AMT 802. 1 X-clientverificatiecertificaat**, om de clientcertificaten die worden gebruikt voor out-of-band-beheer op AMT-computers te genereren.  

4.  Kies de **onderwerpnaam** Kies **basis van Active Directory-informatie samenstellen**, en kies vervolgens **algemene naam** voor de **indeling van de onderwerpnaam**. Schakel **DNS-naam** voor de alternatieve onderwerpnaam naam en kies vervolgens **UPN (User Principal name)**.  

5.  Kies de **beveiliging** tabblad, en verwijder vervolgens de **inschrijven** toestemming van de **Domeinadministrators** en **Ondernemingsadministrators** beveiligingsgroepen.  

6.  Kies **toevoegen**, voer de naam van de beveiligingsgroep die u opgeeft in de onderdeeleigenschappen voor buiten-bandbeheer om de computeraccounts van de AMT-gebaseerde computers en kies vervolgens **OK**.  

7.  Selecteer de volgende **toestaan** machtigingen voor deze beveiligingsgroep: **Lees** en **inschrijven**.  

8.  Kies **OK**, en sluit vervolgens de **certificaatsjablonen** beheerconsole **certtmpl - [Certificaatsjablonen]**.  

9. In de **certificeringsinstantie (CA)** -beheerconsole, met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

10. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr AMT 802. 1 X-clientverificatiecertificaat**, en kies vervolgens **OK**.  

11. Als u niet wilt maken en uitgeven van certificaten meer sluit **certificeringsinstantie (CA)**.  

 U kunt het certificaatsjabloon voor clientverificatie nu gebruiken om certificaten te verlenen aan op AMT-gebaseerde computers die kunnen worden gebruikt voor 802.1X-clientverificatie. Deze certificaatsjabloon selecteert in de onderdeeleigenschappen voor buiten-bandbeheer.  

##  <a name="BKMK_MacClient_SP1"></a>Het clientcertificaat voor Mac-computers implementeren  

Voor deze certificaatimplementatie wordt een enkele procedure gebruikt om het certificaatsjabloon voor inschrijving te maken en het te publiceren bij de certificeringsinstantie.  

###  <a name="BKMK_MacClient_CreatingIssuing"></a>Maken en publiceren van een Mac-client sjabloon Webservercertificaat bij de certificeringsinstantie (CA)  
 Met deze procedure maakt u een aangepast certificaatsjabloon voor System Center Configuration Manager Mac-computers en voegt u certificaatsjabloon toe aan de certificeringsinstantie.  

> [!NOTE]  
>  Met deze procedure gebruikt u een ander certificaatsjabloon dan het certificaatsjabloon dat u mogelijk hebt gemaakt voor Windows-clientcomputers of voor distributiepunten.  
>   
>  Wanneer u een nieuw certificaatsjabloon voor dit certificaat maakt, kunt u certificaataanvragen beperken tot gemachtigde gebruikers.  

##### <a name="to-create-and-issue-the-mac-client-certificate-template-on-the-certification-authority"></a>De Mac-clientcertificaatsjabloon maken en bij de certificeringsinstantie indienen  

1.  Maak een beveiligingsgroep met gebruikersaccounts voor gebruikers met beheerdersrechten die het certificaat op de Mac-computer inschrijven zal met behulp van System Center Configuration Manager.  

2.  Op de lidserver waarop de certificeringsinstantieconsole, met de rechtermuisknop op **certificaatsjablonen**, en kies vervolgens **beheren** om de beheerconsole van certificaatsjablonen te laden.  

3.  Met de rechtermuisknop op het item dat wordt weergegeven in het deelvenster met resultaten **geverifieerde sessie** in de **weergavenaam van sjabloon** kolom en geef daarna aan **sjabloon dupliceren**.  

4.  In de **sjabloon dupliceren** dialoogvenster vak, zorg ervoor dat **Windows 2003 Server, Enterprise Edition** is geselecteerd en kies vervolgens **OK**.  

    > [!IMPORTANT]  
    >  **Windows 2008 Server, Enterprise Edition**niet selecteren.  

5.  In de **eigenschappen van nieuwe sjabloon** dialoogvenster op de **algemeen** tabblad, voert u de sjabloonnaam van een, zoals **ConfigMgr Mac-clientcertificaat**, om de Mac-clientcertificaat te genereren.  

6.  Kies de **onderwerpnaam** tabblad, zorg ervoor dat **basis van Active Directory-informatie samenstellen** is geselecteerd, kies **algemene naam** voor de **indeling van de onderwerpnaam:**, en schakel vervolgens **UPN (User Principal name)** van **deze informatie opnemen in alternatieve onderwerpnaam**.  

7.  Kies de **beveiliging** tabblad, en verwijder vervolgens de **inschrijven** toestemming van de **Domeinadministrators** en **Ondernemingsadministrators** beveiligingsgroepen.  

8.  Kies **toevoegen**, geef de beveiligingsgroep die u hebt gemaakt in stap 1 en kies vervolgens **OK**.  

9. Kies de **inschrijven** machtiging voor deze groep en verwijder de **lezen** machtiging.  

10. Kies **OK**, en sluit vervolgens **Certificaatsjablonenconsole**.  

11. In de certificeringsinstantieconsole met de rechtermuisknop op **certificaatsjablonen**, kies **New**, en kies vervolgens **te verlenen certificaatsjablonen**.  

12. In de **Certificaatsjablonen inschakelen** dialoogvenster kiest u het nieuwe sjabloon dat u zojuist hebt gemaakt, **ConfigMgr Mac-clientcertificaat**, en kies vervolgens **OK**.  

13. Als u geen moet maken en uitgeven van certificaten meer sluit **certificeringsinstantie (CA)**.  

 Het Mac-clientcertificaat is nu gereed om te worden geselecteerd bij het instellen van clientinstellingen voor inschrijving.

