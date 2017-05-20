---
title: Client-beveiliging en privacy | Microsoft-documenten
description: Meer informatie over beveiliging en privacy voor clients in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c1d71899-308f-49d5-adfa-3a3ec0163ed8
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 1d871b0e1a2897c236d17211a23c9c7d93e42313
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-clients-in-system-center-configuration-manager"></a>Beveiliging en privacy voor clients in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Dit artikel bevat beveiliging en privacy-informatie voor clients in System Center Configuration Manager en voor mobiele apparaten die worden beheerd door de Exchange Server-connector:  

##  <a name="BKMK_Security_Cliients"></a>Aanbevolen beveiligingsprocedures voor clients  
 Wanneer Configuration Manager gegevens van apparaten waarop de Configuration Manager-client wordt uitgevoerd accepteert, wordt hierdoor het risico dat de clients de site aanvallen. Ze kunnen bijvoorbeeld een ongeldige inventaris versturen of proberen om de sitesystemen te overbelasten. De Configuration Manager-client alleen implementeren op apparaten die u vertrouwt. Gebruik bovendien de volgende aanbevolen procedures voor beveiliging om de site te helpen beschermen tegen rogue of aangetaste apparaten:  

 **Openbare-sleutelinfrastructuur (PKI)-certificaten gebruiken voor clientcommunicatie met sitesystemen die IIS uitvoeren.**  

-   Configureer **Sitesysteeminstellingen** voor **alleen HTTPS** als een site-eigenschap.  

-   Clients met de CCMSetup-eigenschap **/UsePKICert** installeren  

-   Gebruik een certificaatintrekkingslijst (CRL) en zorg ervoor dat clients en communicerende servers er altijd toegang tot hebben.  

 Deze certificaten zijn vereist voor clients van mobiele apparaten en voor clientcomputerverbindingen op het internet en worden, met uitzondering van distributiepunten, aanbevolen voor alle clientverbindingen op het intranet.  

 Zie voor meer informatie over PKI-certificaatvereisten en hoe ze worden gebruikt om te helpen beschermen Configuration Manager [PKI-certificaatvereisten voor System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 **Automatisch goedkeuren van clientcomputers van vertrouwde domeinen en handmatig controleren en goedkeuren van andere computers**  

 U kunt de goedkeuring voor de hiërarchie configureren als handmatig, automatisch voor computers in vertrouwde domeinen of automatisch voor alle computers. De veiligste goedkeuringsmethode is het automatisch goedkeuren van clients die lid zijn van vertrouwde domeinen en het handmatig controleren en goedkeuren van alle andere computers. Het automatisch goedkeuren van alle clients wordt niet aanbevolen, tenzij u andere toegangscontroles hebt om onbetrouwbare computers de toegang tot uw netwerk te verhinderen.  

 Goedkeuring identificeert een computer die u vertrouwt om te worden beheerd door Configuration Manager wanneer u PKI-verificatie niet kunt gebruiken.  

 Zie [Clients beheren vanaf het knooppunt Apparaten](../../../../core/clients/manage/manage-clients.md#BKMK_ManagingClients_DevicesNode) voor meer informatie over het handmatig goedkeuren van computers.  

 **Vertrouw niet op blokkeren om te voorkomen dat clients toegang hebben tot de Configuration Manager-hiërarchie**  

 Geblokkeerde clients worden geweigerd door de Configuration Manager-infrastructuur zodat ze niet kunnen met sitesystemen om te downloaden communiceren, inventarisgegevens te uploaden of of statusberichten te verzenden. Echter, Vertrouw niet op blokkeren om te voorkomen dat de Configuration Manager-hiërarchie niet-vertrouwde computers wanneer de sitesystemen HTTP-clientverbindingen accepteren. In dit scenario kan een geblokkeerde client zich opnieuw aanmelden voor de site met een nieuw zelfondertekend certificaat en hardware-id. Blokkeren is ontworpen om te worden gebruikt om verloren of aangetaste opstartmedia te blokkeren wanneer u een besturingssysteem implementeert naar clients en wanneer alle sitesystemen HTTPS-clientverbindingen accepteren. Als u een PKI (Public Key Infrastructure) gebruikt die een certificaatintrekkingslijst (CRL) ondersteunt, dient u certificaatintrekking altijd te beschouwen als de primaire beveiliging tegen mogelijk aangetaste certificaten. Blokkeren van clients in Configuration Manager is een tweede verdediging om uw hiërarchie te beschermen.  

 Zie [Bepalen of clients worden geblokkeerd in System Center Configuration Manage](../../../../core/clients/deploy/plan/determine-whether-to-block-clients.md) voor meer informatie.  

 **Gebruik de veiligste clientinstallatiemethoden die praktisch voor uw omgeving zijn:**  

-   Voor domeincomputers zijn installatie van groepsbeleid van de client en installatie van de client via software-updates veiliger dan een clientpushinstallatie.  

-   Installatiekopieën en handmatige installatie kunnen heel veilig zijn als u toegangs- en wijzigingsbeheer toepast.  

 Van alle clientinstallatiemethoden is clientpushinstallatie het minst veilig omdat deze methode veel afhankelijkheden heeft. Deze omvatten lokale beheermachtigingen, de share Admin$ en veel firewalluitzonderingen. Deze afhankelijkheden verhogen uw kwetsbaarheid.  

 Zie [Clientinstallatiemethoden in System Center Configuration Manager](../../../../core/clients/deploy/plan/client-installation-methods.md) voor meer informatie over de verschillende clientinstallatiemethoden.  

 Bovendien, waar mogelijk, selecteer een installatiemethode voor clients die de minste beveiligingsmachtigingen in Configuration Manager vereist en beperk de gebruikers met beheerdersrechten die beveiligingsrollen met machtigingen die kunnen worden gebruikt voor andere doeleinden dan clientimplementatie zijn toegewezen. Voor automatische clientupgrades is bijvoorbeeld de beveiligingsrol **Volledige beheerder** vereist die een gebruiker met beheerdersrechten alle beveiligingsmachtigingen toekent.  

 Zie voor meer informatie over de afhankelijkheden en beveiligingsmachtigingen die voor elke clientinstallatiemethode zijn vereist, 'Afhankelijkheden bij installatiemethoden' in [vereisten voor computerclients](../../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md#BKMK_prereqs_computers).  

 **Als u push-clientinstallatie, moet u extra stappen nemen om het Clientpushinstallatieaccount te beveiligen**  

 Hoewel dit account lid zijn van de lokale moet **beheerders** groep op elke computer waarop de Configuration Manager-clientsoftware wordt geïnstalleerd toevoegen nooit het Clientpushinstallatieaccount naar de **Domeinadministrators** groep. Maak in plaats daarvan een globale groep aan en voeg die globale groep toe aan de lokale groep **Administrators** op uw clientcomputers. U kunt ook een groepsbeleidsobject maken om een beperkte groepsinstelling toe te voegen om het Clientpushinstallatieaccount toe te voegen aan de lokale groep **Administrators**.  

 Maak, voor extra beveiliging, meerdere Clientpushinstallatieaccounts aan, elk met beheerderstoegang voor een beperkt aantal computers. Als er zo één account wordt aangetast, zijn alleen de clientcomputers waarvoor dat account toegang heeft, aangetast.  

 **Verwijder certificaten voordat u installatiekopieën van de clientcomputer**  

 Als u clients plant te implementeren door gebruik te maken van technologie voor installatiekopieën, dient u altijd certificaten (zoals PKI-certificaten die clientverificatie en zelfondertekende certificaten omvatten) te verwijderen voordat u de installatiekopie vastlegt. Als u deze certificaten niet verwijdert, is het mogelijk dat clients elkaar imiteren. In dat geval kunt u de gegevens voor elke client niet verifiëren.  

 Zie de documentatie van uw Windows-implementatie voor meer informatie over het gebruik van Sysprep om een computer voor te bereiden om een installatiekopie vast te leggen.  

 **Zorg ervoor dat de Configuration Manager-computerclients een geautoriseerde kopie van deze certificaten ontvangen:**  

-   De vertrouwde basissleutel van Configuration Manager  

     Als u hebt het Active Directory-schema niet uitgebreid voor Configuration Manager en clients geen PKI-certificaten gebruiken wanneer ze met beheerpunten communiceren, worden clients vertrouwen op de Configuration Manager vertrouwde basissleutel om geldige beheerpunten te verifiëren. In dit scenario hebben clients geen manier om te verifiëren dat het beheerpunt een vertrouwd beheerpunt is voor de hiërarchie, tenzij ze de vertrouwde basissleutel gebruiken. Zonder de vertrouwde basissleutel kan een ervaren aanvaller clients omleiden naar een rogue beheerpunt.  

     Als clients kunnen niet de vertrouwde basissleutel van Configuration Manager downloaden van de globale catalogus of met behulp van PKI-certificaten, de clients vooraf inrichten met de vertrouwde basissleutel om ervoor te zorgen dat ze niet kunnen worden omgeleid naar een rogue beheerpunt. Zie [Planning voor de vertrouwde basissleutel](../../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) voor meer informatie.  

-   Het handtekeningcertificaat van de siteserver  

     Clients gebruiken het handtekeningcertificaat van de siteserver om te verifiëren of de siteserver het clientbeleid, dat ze downloaden van een beheerpunt, heeft ondertekend. Dit certificaat wordt zelfondertekend door de siteserver en gepubliceerd naar Active Directory Domain Services.  

     Clients downloaden het handtekeningcertificaat van de siteserver standaard van een beheerpunt als ze het niet kunnen downloaden van de globale catalogus. Wanneer het beheerpunt wordt blootgesteld aan een niet-vertrouwd netwerk (zoals het internet), installeert u het handtekeningcertificaat van de siteserver handmatig op clients om ervoor te zorgen dat ze geen clientbeleid kunnen uitvoeren waarmee is geknoeid vanuit een aangetast beheerpunt.  

     Gebruik de eigenschap **SMSSIGNCERT** van CCMSetup client.msi om het handtekeningcertificaat van de siteserver handmatig te installeren. Zie [Over de eigenschappen van clientinstallatie in System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md) voor meer informatie.  

 **Gebruik geen automatische sitetoewijzing als de client de vertrouwde basissleutel zal downloaden van het eerste beheerpunt waarmee het contact opneemt**  

 Deze aanbevolen procedure voor beveiliging is gekoppeld aan het voorgaande item. U kunt het risico vermijden dat een nieuwe client de vertrouwde basissleutel downloadt van een rogue beheerpunt; hiervoor dient u alleen automatische sitetoewijzing te gebruiken in de volgende scenario's:  

-   De client toegang tot site-informatie voor Configuration Manager die is gepubliceerd naar Active Directory Domain Services.  

-   U richt de client vooraf in met de vertrouwde basissleutel.  

-   U kunt PKI-certificaten gebruiken van een bedrijfscertificeringsinstantie om het vertrouwen tussen de client en het beheerpunt vast te leggen.  

 Zie [Planning voor de vertrouwde basissleutel](../../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) voor meer informatie over de vertrouwde basissleutel.  

 **Clientcomputers installeren met de CCMSetup Client.msi-optie SMSDIRECTORYLOOKUP = NoWINS**  

 Active Directory Domain Services gebruiken is de meest beveiligde servicelocatiemethode voor clients om sites en beheerpunten te vinden. Als dit niet mogelijk is, bijvoorbeeld, kunt omdat u de Active Directory-schema voor Configuration Manager niet kunt uitbreiden of omdat clients zich in een niet-vertrouwde forest of werkgroep bevinden, u DNS-publishing als een alternatieve servicelocatiemethode. Als deze twee methoden mislukken, kunnen clients terugvallen op het gebruik van WINS wanneer het beheerpunt niet voor HTTPS-clientverbindingen is geconfigureerd.  

 Omdat publishing naar WINS minder veilig is dan de andere publishingmethoden, dient u clientcomputers te configureren om niet terug te vallen om het gebruik van WINS door SMSDIRECTORYLOOKUP=NoWINS op te geven. Als u WINS voor servicelocatie gebruiken, gebruikt u SMSDIRECTORYLOOKUP = WINSSECURE (de standaardinstelling), waarbij de vertrouwde basissleutel van Configuration Manager gebruikt om te valideren van het zelfondertekende certificaat van het beheerpunt.  

> [!NOTE]  
>  Wanneer de client is geconfigureerd voor SMSDIRECTORYLOOKUP = WINSSECURE en een beheerpunt vindt van WINS, de client controleert zijn kopie van de vertrouwde basissleutel van Configuration Manager die in WMI. De handtekening op het certificaat overeenkomt met de kopie van de client van de vertrouwde basissleutel, het beheerpuntcertificaat wordt gevalideerd als de client communiceert met het beheerpunt dat het vond door WINS. Als de handtekening van het certificaat komt niet overeen met de kopie van de vertrouwde basissleutel van de client, wordt het certificaat is niet geldig en wordt de client zal vervolgens niet communiceren met het beheerpunt dat het vond door WINS.  

 **Zorg ervoor dat onderhoudsvensters groot genoeg is voor de kritieke software-updates implementeren**  

 Hier kunt u onderhoudsvensters voor apparaatverzamelingen om de tijdstippen dat Configuration Manager software op deze apparaten installeren kan te beperken. Als u het onderhoudsvenster te klein configureert, is het mogelijk dat de client kritieke software-updates niet kan installeren. Dit maakt de client kwetsbaar voor de aanval die wordt verholpen door de software-update.  

 **Voor Windows embedded-apparaten die schrijffilters hebben, bijkomende beveiligingsmaatregelen nemen om de kwetsbaarheid verlagen als Configuration Manager de schrijffilters uitschakelt om te software-installaties en -wijzigingen te behouden**  

 Wanneer schrijffilters ingeschakeld zijn op Windows Embedded-apparaten, worden software-installaties of -wijzigingen alleen aan de overlay toegevoegd en blijven ze niet behouden nadat het apparaat opnieuw wordt opgestart. Als u met Configuration Manager de schrijffilters om te software-installaties en -wijzigingen te behouden tijdens deze periode tijdelijk uitschakelen is het embedded-apparaat kwetsbaar voor wijzigingen aan alle volumes, wat ook gedeelde mappen omvat.  

 Hoewel Configuration Manager worden de computer tijdens deze periode vergrendelt zodat alleen lokale beheerders kunnen aanmelden, waar mogelijk, bijkomende beveiligingsmaatregelen nemen om bescherming van de computer. Schakel bijvoorbeeld bijkomende beperkingen in op de firewall en verbreek de netwerkverbinding van het apparaat.  

 Als u onderhoudsvensters gebruikt om wijzigingen te behouden, dient u deze vensters zorgvuldig te plannen om de tijd te minimaliseren waarop schrijffilters mogelijk uitgeschakeld kunnen zijn, maar de tijd moet lang genoeg zijn om software-installaties en het opnieuw opstarten van het apparaat mogelijk te maken.  

 **Als u software-update gebaseerde clientinstallatie gebruikt en een nieuwere versie van de client op de site installeert, werkt u de software-update die is gepubliceerd op het software-updatepunt zodat clients de nieuwste versie ontvangen**  

 Als u een nieuwere versie van de client op de site installeert als u bijvoorbeeld de site bijwerkt, wordt de software-update voor clientimplementatie die naar het software-updatepunt is gepubliceerd, niet automatisch bijgewerkt. U moet de Configuration Manager-client voor de software-updatepunt en klik op publiceren **Ja** om het versienummer te werken.  

 Voor meer informatie, Zie de procedure ' de Configuration Manager-client op het software-updatepunt publiceren' in [Configuration Manager-clients installeren met installatie](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP).  

 **Configureer het Computeragent client-apparaat instellen van BitLocker-pincode opschorten bij opnieuw opstarten worden altijd alleen bestemd voor computers die u vertrouwt en die beperkte fysieke toegang hebben**  

 Als u instelt dat apparaatclientinstelling op **altijd**, Configuration Manager kunt voltooit de installatie van software om te helpen om ervoor te zorgen dat kritieke software-updates zijn geïnstalleerd en dat de services worden hervat. Wanneer een kwaadwillend persoon het proces van het opnieuw opstarten onderschept, kan deze persoon de controle over de computer overnemen. Gebruik deze instelling alleen wanneer u de computer vertrouwt en wanneer fysieke toegang tot de computer beperkt is. Deze instelling is bijvoorbeeld mogelijk geschikt voor servers in een datacenter.  

 **Configureer de Computer Agent client Apparaatinstelling PowerShell-uitvoeringsbeleid wilt overslaan.**  

 Deze clientinstelling kan de Configuration Manager-client niet-ondertekende PowerShell-scripts, waardoor er schadelijke software uit te voeren op clientcomputers zou kunnen uitvoeren. Als u deze optie moet selecteren, moet u een aangepaste clientinstelling gebruiken en deze alleen toewijzen aan die clientcomputers die niet-ondertekende PowerShell-scripts moeten uitvoeren.  

##  <a name="bkmk_mobile"></a>Aanbevolen beveiligingsprocedures voor mobiele apparaten  
 **Voor mobiele apparaten die u registreren met Configuration Manager en wordt ondersteund op Internet: Installeer het proxypunt voor inschrijving in een perimeternetwerk en het inschrijvingspunt op het intranet**  

 Deze scheiding van rollen help om het proxypunt voor inschrijving te beveiligen tegen een aanval. Als het inschrijvingspunt in het geding komt, zou een kwaadwillend persoon certificaten voor verificatie kunnen verkrijgen en de referenties kunnen stelen van gebruikers die hun mobiele apparaten inschrijven.  

 **Voor mobiele apparaten: Configureer de wachtwoordinstellingen om mobiele apparaten te beveiliging tegen onbevoegde toegang**  

 Voor mobiele apparaten die zijn ingeschreven door Configuration Manager: Een configuratie-item voor mobiele apparaten gebruiken voor het configureren van de wachtwoordcomplexiteit PIN waarbij ten minste standaardlengte wordt vereist voor de minimale wachtwoordlengte.  

 Voor mobiele apparaten waarop geen Configuration Manager-client geïnstalleerd maar die worden beheerd door de Exchange Server-connector: Configureer de **wachtwoordinstellingen** voor Exchange Server-connector zo dat de wachtwoordcomplexiteit de PINCODE is waarbij ten minste de standaardlengte voor de minimale wachtwoordlengte.  

 **Voor mobiele apparaten: Help voorkoming van knoeien met Inventarisinformatie en statusinformatie doordat toepassingen worden uitgevoerd alleen wanneer deze zijn ondertekend door bedrijven die u vertrouwt en niet toe dat niet-ondertekende bestanden worden geïnstalleerd**  

 Voor mobiele apparaten die zijn ingeschreven door Configuration Manager: Een configuratie-item voor mobiele apparaten gebruiken voor het configureren van de beveiligingsinstelling **niet-ondertekende toepassingen** als **Prohibited** en configureer **niet-ondertekend bestand installaties** moet een vertrouwde bron.  

 Voor mobiele apparaten waarop geen Configuration Manager-client geïnstalleerd maar die worden beheerd door de Exchange Server-connector: Configureert de **toepassingsinstellingen** voor Exchange Server-connector zodat **niet-ondertekende bestandsinstallatie** en **niet-ondertekende toepassingen** zijn geconfigureerd als **Prohibited**.  

 **Voor mobiele apparaten: Aanval via verhoogde bevoegdheden voorkomen door het mobiele apparaat te vergrendelen wanneer dit niet wordt gebruikt**  

 Voor mobiele apparaten die zijn ingeschreven door Configuration Manager: Een configuratie-item voor mobiele apparaten gebruiken voor het configureren van de wachtwoordinstelling **niet-actieve tijd in minuten voordat het mobiele apparaat wordt vergrendeld**.  

 Voor mobiele apparaten waarop geen Configuration Manager-client geïnstalleerd maar die worden beheerd door de Exchange Server-connector: Configureer de **wachtwoordinstellingen** voor Exchange Server-connector configureren **niet-actieve tijd in minuten voordat het mobiele apparaat wordt vergrendeld**.  

 **Voor mobiele apparaten: Verhoging van bevoegdheden voorkomen door het beperken van de gebruikers hun mobiele apparaten kunnen registreren.**  

 Gebruik een aangepaste clientinstelling in plaats van standaardclientinstellingen om alleen geautoriseerde gebruikers toe te staan hun mobiele apparaten te registreren.  

 **Voor mobiele apparaten: Implementeer geen toepassingen voor gebruikers die mobiele apparaten geregistreerd via Configuration Manager of Microsoft Intune in de volgende scenario's hebben:**  

-   Wanneer het mobiele apparaat door meer dan één persoon wordt gebruikt.  

-   Wanneer het apparaat namens een gebruiker door een beheerder wordt geregistreerd.  

-   Wanneer het apparaat aan een andere persoon wordt overgedragen zonder het apparaat buiten gebruikt te stellen en vervolgens opnieuw te registreren.  

 Er wordt tijdens het inschrijven een relatie voor gebruikersapparaataffiniteit voor het gebruikersapparaat gemaakt, waarbij de gebruiker die de inschrijving uitvoert, aan het mobiele apparaat wordt toegewezen. Als een andere gebruiker het mobiele apparaat gebruik, kan deze de toepassingen uitvoeren die u voor de oorspronkelijke gebruiker implementeert. Dit kan leiden tot verhoogde bevoegdheden. Als een beheerder een mobiel apparaat voor een gebruiker registreert, worden toepassingen die voor de gebruiker worden geïmplementeerd, niet op het mobiele apparaat geïnstalleerd en worden er in plaats daarvan mogelijk toepassingen geïnstalleerd die voor de beheerder worden geïmplementeerd.  

 In tegenstelling tot bij gebruikersapparaataffiniteit voor Windows-computers definiëren niet u handmatig de informatie van affiniteit gebruikerapparaat voor mobiele apparaten die zijn geregistreerd door Microsoft Intune.  

 Als u het eigendom van een mobiel apparaat dat is geregistreerd door Intune overdraagt, het mobiele apparaat uit Intune verwijderen van de gebruikersaffiniteit van apparaten buiten gebruik stellen en vervolgens vraagt u de huidige gebruiker het apparaat om opnieuw te registreren.  

 **Voor mobiele apparaten: Zorg ervoor dat gebruikers hun eigen mobiele apparaten voor Microsoft Intune registreren**  

 Omdat er tijdens het inschrijven een affiniteitsrelatie voor het gebruikersapparaat wordt gemaakt, waarbij de gebruiker die de inschrijving uitvoert aan het mobiele apparaat wordt toegewezen, worden, als een beheerder een mobiel apparaat voor een gebruiker registreert, toepassingen die voor de gebruiker worden geïmplementeerd, niet op het mobiele apparaat geïnstalleerd en worden er in plaats daarvan mogelijk toepassingen geïnstalleerd die voor de beheerder worden geïmplementeerd.  

 **Voor Exchange Server-connector: Zorg ervoor dat de verbinding tussen de siteserver van Configuration Manager en de Exchange Server-computer is beveiligd**  

 Gebruik IPsec als het een on-premise Exchange Server-exemplaar betreft. Bij gehoste Exchange wordt de verbinding automatisch beveiligd via SSL.  

 **Voor Exchange Server-connector: Gebruik het principe van minimale bevoegdheden voor de connector**  

 Zie [Mobiele apparaten beheren met System Center Configuration Manager en Exchange](../../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) voor een lijst met de cmdlets die minimaal door de Exchanges Server-connector worden vereist.  

##  <a name="bkmk_macs"></a>Aanbevolen beveiligingsprocedures voor Macs  
 **Voor Mac-computers: Opslaan en toegang tot de bronbestanden van de client vanaf een veilige locatie.**  

 Configuration Manager controleert niet of deze clientbronbestanden is geknoeid voordat de client op Mac-computer geïnstalleerd of geregistreerd. Download deze bestanden vanaf een betrouwbare bron en sla deze op veilig op en benader ze op een veilige wijze.  

 **Voor Mac-computers: Onafhankelijk van Configuration Manager, controleren en te volgen van de geldigheidsperiode van het certificaat dat wordt geregistreerd voor gebruikers.**  

 Stel de bedrijfscontinuïteit veilig door de geldigheidsperiode van het certificaat dat voor Mac-computers wordt gebruikt, te controleren en te volgen. Configuration Manager geen ondersteuning voor automatische vernieuwing van dit certificaat of waarschuwen dat het certificaat is bijna verlopen. Een gebruikelijke geldigheidsduur is één jaar.  

 Zie [Het Mac-clientcertificaat vernieuwen](../../../../core/clients/deploy/deploy-clients-to-macs.md#renewing-the-mac-client-certificate) voor meer informatie over het vernieuwen van het certificaat.  

 **Voor Mac-computers: Houd rekening met het vertrouwde basis-CA-certificaat configureren zodat deze vertrouwd voor alleen het SSL-protocol wordt als extra beveiliging tegen verhoging van bevoegdheden.**  

 Als u Mac-computers inschrijven, wordt een gebruikerscertificaat voor het beheren van de Configuration Manager-client automatisch geïnstalleerd, samen met het vertrouwde basiscertificaat waaraan het gebruikerscertificaat wordt gekoppeld. Als u het vertrouwen met betrekking tot dit basiscertificaat wilt beperken tot uitsluitend het SSL-protocol, kunt u de volgende procedure gebruiken.  

 Nadat u deze procedure hebt voltooid, het basiscertificaat niet vertrouwd voor het valideren van andere protocollen dan SSL - bijvoorbeeld beveiligde E-mail (S/MIME), uitbreidbare verificatie (EAP) of handtekeningen bij programmacode.  

> [!NOTE]  
>  U kunt deze procedure ook gebruiken als u het clientcertificaat onafhankelijk van Configuration Manager geïnstalleerd.  

 Als u het basiscertificaat uitsluitend tot het SSL-protocol wilt beperken:  

1.  Open een terminalvenster op de Mac-computer.  

2.  Voer de opdracht **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access** in.  

3.  Klik in het dialoogvenster **Toegang tot sleutelhanger** in de sectie **Sleutelhangers** op **Systeem**, en klik vervolgens in de sectie **Categorie** op **Certificaten**.  

4.  Ga naar het basiscertificaat voor het Mac-clientcertificaat en dubbelklik op dit certificaat.  

5.  Vouw in het dialoogvenster voor het basis-CA-certificaat de sectie **Vertrouwen** uit en breng vervolgens de volgende wijzigingen aan:  

    1.  Wijzig bij de instelling voor **Wanneer dit certificaat wordt gebruikt** de standaardinstelling **Altijd vertrouwen** in de optie voor het **gebruik van de standaardwaarden van het systeem**.  

    2.  Wijzig bij de instelling **Secure Sockets Layer (SSL)** het item **geen waarde opgegeven** in **Altijd vertrouwen**.  

6.  Sluit het dialoogvenster en wanneer dat wordt gevraagd het beheerderswachtwoord in en klik vervolgens op **Update-instellingen**.  

##  <a name="BKMK_SecurityIssues_Clients"></a>Beveiligingsproblemen voor Configuration Manager-clients  
 Er zijn voor de volgende beveiligingsproblemen geen matigingsmaatregelen bekend:  

-   Statusberichten worden niet geverifieerd  

     Er wordt geen verificatie uitgevoerd voor statusberichten. Wanneer een beheerpunt HTTP-clientverbindingen accepteert, kan elk apparaat statusberichten naar het beheerpunt verzenden. Als het beheerpunt alleen HTTPS-clientverbindingen accepteert, moet een apparaat een geldig clientverificatiecertificaat verkrijgen van een certificeringsinstantie voor vertrouwde basiscertificaten, maar kan dit tevens welk statusbericht dan ook verzenden. Als een client een ongeldig statusbericht verzendt, wordt dit genegeerd.  

     Er is een aantal potentiële aanvallen via deze kwetsbaarheid mogelijk. Een kwaadwillend persoon zou een vals statusbericht kunnen verzenden om lidmaatschap van een verzameling te verkrijgen die is gebaseerd op statusberichtquery's. Elke client zou een DoS-aanval op het beheerpunt kunnen starten door dit met statusberichten te overspoelen. Als statusberichten acties in werking stellen via regels voor het statusberichtfilter, zou een kwaadwillend persoon deze regels in werking kunnen stellen. Een kwaadwillend persoon zou ook een statusbericht kunnen verzenden waardoor rapportage-informatie onnauwkeurig wordt.  

-   Beleid kan opnieuw worden afgestemd op clients waarop dit niet is gericht  

     Er zijn verschillende methoden die kwaadwillende personen zouden kunnen gebruiken om beleid dat op één client is gericht, toe te passen op een geheel andere client. Een kwaadwillend persoon zou via een vertrouwde client bijvoorbeeld valse inventaris- of detectie-informatie kunnen verzenden om de computer toe te voegen aan een verzameling waartoe deze niet behoort en zou vervolgens alle implementaties voor deze verzameling kunnen ontvangen. Hoewel er methoden bestaan om te voorkomen dat kwaadwillende personen beleid rechtstreeks kunnen aanpassen, zouden dergelijke personen bestaand beleid kunnen gebruiken voor het opnieuw indelen en implementeren van een besturingssysteem en om dit naar een andere computer te verzenden, zodat er een DoS-aanval ontstaat. Dit type aanvallen vereist een precieze timing en uitgebreide kennis van de Configuration Manager-infrastructuur.  

-   Clientlogboeken staan gebruikerstoegang toe  

     Alle clientlogbestanden staan gebruikers leestoegang en interactieve gebruikers schrijftoegang toe. Als u uitgebreide logboekregistratie inschakelt, kunnen kwaadwillende personen eventueel de logboekbestanden lezen op zoek naar informatie over kwetsbaarheden op het vlak van het systeem of compatibiliteit. Processen zoals software-installatie die binnen de context van een gebruiker worden uitgevoerd, moeten logboeken kunnen schrijven met een gebruikersaccount met een laag niveau aan rechten. Dit betekent dat een kwaadwillend persoon ook naar logboeken kan schrijven met een account met een laag niveau aan rechten.  

     Het meest ernstige risico hierbij is dat een kwaadwillend persoon informatie uit de logboekbestanden zou kunnen verwijderen die een beheerder mogelijk nodig heeft voor controledoeleinden en het detecteren van indringers.  

-   Een computer kan worden gebruikt voor het verkrijgen van een certificaat dat is ontworpen voor het inschrijven van een mobiel apparaat  

     Wanneer Configuration Manager een inschrijvingsaanvraag wordt verwerkt, kan deze niet verifiëren dat de aanvraag afkomstig van een mobiel apparaat in plaats van vanaf een computer is. Als de aanvraag afkomstig van een computer is, kan een PKI-certificaat kunt registreren met Configuration Manager worden geïnstalleerd. Met het oog op het in dit scenario voorkomen van een aanval via verhoogde bevoegdheden, is het raadzaam om alleen vertrouwde gebruikers toe te staan hun mobiele apparaten in te schrijven, waarbij de inschrijvingsactiviteiten nauwlettend moeten worden gecontroleerd.  

-   De verbinding van een client met een beheerpunt wordt niet verbroken als u een client blokkeert en de geblokkeerde client zou kunnen doorgaan met het naar het beheerpunt verzenden van meldingspakketten en keepalive-berichten  

     Wanneer u een client die u niet langer vertrouwt, blokkeert en heeft deze clientmeldingscommunicatie tot stand gebracht, wordt de sessie niet verbroken door Configuration Manager. De geblokkeerde client kan doorgaan met het verzenden van pakketten naar het beheerpunt, totdat de client de verbinding met het netwerk verbreekt. Deze pakketten betreffen slechts kleine keepalive-pakketten en deze clients kunnen niet worden beheerd door Configuration Manager totdat deze geblokkeerd zijn.  

-   Wanneer u Automatische clientupgrade gebruikt en de client naar een beheerpunt wordt omgeleid voor het downloaden van de clientbronbestanden, wordt niet gecontroleerd of het beheerpunt een vertrouwde bron is  

-   Wanneer gebruikers eerst Mac-computers inschrijven, zijn deze kwetsbaar voor aanvallen via DNS-vervalsing.  

     Wanneer de Mac-computer tijdens het inschrijven verbinding maakt met het proxypunt voor inschrijving, is het onwaarschijnlijk dat deze al over het CA-basiscertificaat beschikt. Op dit punt wordt de server door de Mac-computer niet vertrouwd en wordt de gebruiker gevraagd om door te gaan. Als de volledig gekwalificeerde naam van het proxypunt voor inschrijving door een malafide DNS-server wordt omgezet, zou deze de Mac-computer kunnen omleiden naar een malafide proxypunt voor inschrijving en certificaten vanuit een niet-vertrouwde bron kunnen installeren. Volg de aanbevolen procedures voor het vermijden van DNS-vervalsing in uw omgeving om dit risico te reduceren.  

-   Mac-inschrijving brengt geen beperking op het vlak van certificaataanvragen met zich mee  

     Telkens wanneer er een nieuw certificaat wordt aangevraagd, kunnen gebruikers hun Mac-computer opnieuw inschrijven. Configuration Manager wordt niet gecontroleerd voor meerdere aanvragen of beperkt het aantal aangevraagde certificaten vanaf één computer. Een malafide gebruiker zou een script kunnen uitvoeren waarin de inschrijvingsaanvraag vanaf de opdrachtregel wordt herhaald. Dit leidt tot een DoS-aanval op het netwerk of de uitgevende certificeringsinstantie. Controleer de uitgevende certificeringsinstantie nauwlettend op dit type verdacht gedrag om dit risico te reduceren. Een computer die blijk geeft van dit patroon van gedrag moet onmiddellijk worden geblokkeerd vanuit de Configuration Manager-hiërarchie.  

-   Een wisbevestiging controleert niet of het apparaat daadwerkelijk is gewist  

     Bij het starten van een wisactie voor een mobiel apparaat en Configuration Manager geeft de status wissen, de verificatie is bevestigd dat Configuration Manager verzonden bericht en niet dat het apparaat waarop deze. Daarnaast geldt voor mobiele apparaten die door de Exchange Server-connector worden beheerd, dat een wisbevestiging controleert of de opdracht door Exchange, en dus niet door het apparaat, is ontvangen.  

-   Als u de opties gebruikt om wijzigingen door te voeren op Windows Embedded-apparaten, is het mogelijk dat accounts vroeger dan verwacht worden vergrendeld.  

     Als de Windows Embedded-apparaat een besturingssysteem dat ouder is dan Windows 7 wordt uitgevoerd en een gebruiker wil zich aanmelden terwijl de schrijffilters zijn uitgeschakeld voor het doorvoeren van wijzigingen die zijn gemaakt door Configuration Manager, wordt het aantal pogingen voor onjuist aanmelden dat is toegestaan voordat het account is vergrendeld feite gehalveerd. Als bijvoorbeeld de **Drempel voor accountvergrendeling** als 6 wordt geconfigureerd en een gebruiker 3 keer een verkeerd wachtwoord invoert, wordt het account vergrendeld, waardoor in feite een DoS-situatie (Denial of Service) ontstaat.  Waarschuw, als gebruikers zich in dit scenario moeten aanmelden bij Embedded-apparaten, hen voor de mogelijkheid van een verlaagde vergrendelingsdrempel.  

##  <a name="BKMK_Privacy_Cliients"></a>Privacy-informatie voor Configuration Manager-clients  
 Wanneer u de Configuration Manager-client implementeert, schakelt u clientinstellingen zodat u Configuration Manager-functies kunt gebruiken. De instellingen die u gebruikt voor het configureren van de functies kunnen toepassen op alle clients in de Configuration Manager-hiërarchie, ongeacht of ze zijn rechtstreeks verbonden met het bedrijfsnetwerk bevinden, via een externe sessie of verbonden met Internet maar ondersteund door Configuration Manager.  

 Clientinformatie wordt opgeslagen in de Configuration Manager-database en wordt niet naar Microsoft verzonden. Informatie wordt in de database bewaard tot deze om de 90 dagen door de siteonderhoudstaken **Verouderde detectiegegevens verwijderen** wordt verwijderd. U kunt het verwijderingsinterval configureren.  

 Bedenk wat uw privacyvereisten voordat u de Configuration Manager-client configureert.  

### <a name="privacy-information-for-mobile-devices-that-are-enrolled-by-configuration-manager"></a>Privacygegevens voor mobiele apparaten die door Configuration Manager zijn geregistreerd  
 Zie voor privacygegevens wanneer u een mobiel apparaat door Configuration Manager registreert, [privacyverklaring voor System Center Configuration Manager - bijlage voor mobiele apparaten](../../../../core/misc/privacy/privacy-statement-mobile-device-addendum.md).  

### <a name="client-status"></a>Clientstatus  
 Configuration Manager controleert de activiteit van clients en periodiek evalueert en de Configuration Manager-client en de afhankelijkheden ervan kunt herstellen. Status van de client is standaard ingeschakeld en gebruikt serverzijde metrische gegevens voor de client clientactiviteit, en vanaf clientzijde acties voor zelfcontrole, herstel en voor de verzending van clientstatusgegevens informatie aan de Configuration Manager-site. De client voert de zelfcontroles uit volgens een door u te configureren planning. De client verzendt de resultaten van de controles naar de Configuration Manager-site. Deze gegevens zijn versleuteld tijdens de overdracht.  

 Informatie over de clientstatus wordt opgeslagen in de Configuration Manager-database en wordt niet naar Microsoft verzonden. De gegevens worden niet in een versleutelde indeling opgeslagen in de database van de site. Deze gegevens worden bewaard in de database tot deze worden verwijderd op basis van de waarde die voor de clientstatusinstelling **Historie van clientstatus bewaren gedurende het volgende aantal dagen** is geconfigureerd. De standaardwaarde voor deze instelling is elke 31 dagen.  

 Bedenk wat uw privacyvereisten voordat u de Configuration Manager-client met de clientstatus controleren installeert.  

##  <a name="BKMK_Privacy_ExchangeConnector"></a>Privacy-informatie voor mobiele apparaten die worden beheerd met de Exchange Server-Connector  
 De Exchange Server-connector zoekt en beheert apparaten die verbinding hebben met Exchange Server (op locatie of gehost) via het ActiveSync-protocol. De door de Exchange Server-Connector gevonden records worden opgeslagen in de Configuration Manager-database. De gegevens worden verzameld uit Exchange-Server. Deze bevatten geen extra informatie van wat de mobiele apparaten naar Exchange server verzenden.  

 De informatie van mobiele apparaten wordt niet naar Microsoft verzonden. De informatie van mobiele apparaten wordt opgeslagen in de Configuration Manager-database. Informatie wordt in de database bewaard tot deze om de 90 dagen door de siteonderhoudstaken **Verouderde detectiegegevens verwijderen** wordt verwijderd. U kunt het verwijderingsinterval configureren.  

 Denk na over uw privacyvereisten voordat u de Exchange Server-connector installeert en configureert.  

