---
title: "Installatiekopieën van besturingssystemen beheren | Microsoft-documenten"
description: "In Configuration Manager, informatie over de methoden die u gebruiken kunt voor het beheren van installatiekopieën van besturingssystemen die zijn opgeslagen in de Windows Imaging (WIM)-bestanden."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fab13949-371c-4a4c-978e-471db1e54966
caps.latest.revision: 17
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 03722ff4f480cd26842e395fe1f7ec8359e2b33e
ms.openlocfilehash: 6953c3834ca303b949f22436010a87b3da9688dc
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-operating-system-images-with-system-center-configuration-manager"></a>Installatiekopieën van een besturingssysteem beheren met System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Installatiekopieën van besturingssystemen in Configuration Manager worden opgeslagen met de WIM-bestandsindeling (Windows Imaging). Ze omvatten een gecomprimeerde verzameling referentiebestanden en -mappen die zijn vereist om een besturingssysteem correct te installeren en te configureren op een computer. Alle implementatiescenario's voor besturingssystemen vereisen dat u een installatiekopie van een besturingssysteem selecteert.   U kunt de standaardinstallatiekopie van een besturingssysteem gebruiken of een installatiekopie maken van het besturingssysteem van een referentiecomputer die u configureert. Als u de referentiecomputer bouwen, kunt u besturingssysteembestanden, stuurprogramma's, ondersteuningsbestanden, software-updates, hulpprogramma's en andere softwaretoepassingen aan het besturingssysteem toevoegen voordat u het vastlegt om het installatiekopiebestand te maken. Het volgende gedeelte bevat informatie over elke methode.  

 **Standaard-installatiekopie**  

 De standaardinstallatiekopie van het besturingssysteem (install.wim) is opgenomen in de installatiebestanden van het Windows-besturingssysteem. Deze installatiekopie is een basisinstallatiekopie van het besturingssysteem die een standaardset stuurprogramma's bevat. Wanneer u de standaardinstallatiekopie van het besturingssysteem gebruikt, kunt u apps installeren en andere configuraties uitvoeren nadat het besturingssysteem aan de hand van takenreeksstappen is geïnstalleerd.  De standaardinstallatiekopie van het besturingssysteem bevindt zich in <*bronpad van het besturingssysteem*>\Sources\install.wim.  

-   **Voordelen**  

    -   De grootte van de installatiekopie is kleiner dan die van een vastgelegde installatiekopie.  

    -   Takenreeksstappen zorgen ervoor dat apps en configuratie op een meer dynamische wijze kunnen worden geïnstalleerd. U kunt bijvoorbeeld wijzigen welk apps worden geïnstalleerd, hoe de takenreeks wordt geconfigureerd en aangeven dat het besturingssysteem niet hoeft worden hersteld met een installatiekopie.  

-   **Nadelen**  

    -   De installatie van een besturingssysteem kan meer tijd vergen, omdat de installatie van de app en andere configuraties worden uitgevoerd nadat de installatie van het besturingssysteem is voltooid.  

 **Vastgelegde installatiekopie**  

 Als u een aangepaste installatiekopie van een besturingssysteem wilt maken, bouwt u een referentiecomputer met het gewenste besturingssysteem en installeert u apps, configureert u instellingen, enzovoort. Vervolgens legt u de installatiekopie van het besturingssysteem van de referentiecomputer vast om het WIM-bestand te maken. U kunt de referentiecomputer handmatig samenstellen of een takenreeks gebruiken om enkele of alle stappen van de samenstelling te automatiseren.   
Zie voor de stappen voor het maken van een aangepaste installatiekopie [installatiekopieën van besturingssystemen aanpassen](customize-operating-system-images.md).  

-   **Voordelen**  

    -   De installatie verloopt waarschijnlijk sneller dan wanneer u de standaardinstallatiekopie gebruikt. Apps kunnen met de vastgelegde installatiekopie van het besturingssysteem bijvoorbeeld vooraf worden geïnstalleerd, zodat u achteraf geen apps meer via takenreeksstappen hoeft te installeren.  

-   **Nadelen**  

    -   De installatie van een besturingssysteem kan meer tijd vergen, omdat de installatie van de app en andere configuraties worden uitgevoerd nadat de installatie van het besturingssysteem is voltooid.  


##  <a name="BKMK_AddOSImages"></a>Installatiekopieën van besturingssysteem toevoegen aan Configuration Manager  
 Voordat u een installatiekopie gebruiken kunt, moet u de installatiekopie toevoegen aan een Configuration Manager-site. Gebruik de volgende procedure om een installatiekopie van een besturingssysteem toe te voegen aan een site.  

#### <a name="to-add-an-operating-system-image-to-a-site"></a>Een installatiekopie van een besturingssysteem aan een site toevoegen  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** de optie **Besturingssystemen** uit en klik vervolgens op **Installatiekopieën van besturingssysteem**.  

3.  Klik in de groep **Maken** op het tabblad **Start** op **Installatiekopie van besturingssysteem toevoegen** om de wizard Installatiekopie van het besturingssysteem toevoegen te starten.  

4.  Geef op de pagina **Gegevensbron** het netwerkpad op naar de installatiekopie van het besturingssysteem. Geef bijvoorbeeld **\\\server\path\OS. WIM** op.  

5.  Geef op de pagina **Algemeen** de volgende informatie op en klik op **Volgende**. Deze informatie is nuttig om een installatiekopie te kunnen identificeren wanneer u meerdere installatiekopieën van een besturingssysteem toevoegt aan dezelfde site.  

    -   **Naam**: Geef de naam van de afbeelding. De naam van de installatiekopie wordt standaard overgenomen uit het WIM-bestand.  

    -   **Versie**: Geef de versie van de afbeelding.  

    -   **Opmerking**: Geef een korte beschrijving van de afbeelding.  

6.  Voltooi de wizard.  

 U kunt de installatiekopie van het besturingssysteem nu distribueren naar distributiepunten.  

##  <a name="BKMK_DistributeBootImages"></a>Installatiekopieën van besturingssystemen naar distributiepunten distribueren  
 Installatiekopieën van het besturingssysteem worden op dezelfde manier naar distributiepunten gedistribueerd als andere inhoud. In de meeste gevallen moet u het besturingssysteem naar ten minste één distributiepunt distribueren voordat u het besturingssysteem implementeert. Zie [Inhoud distribueren](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content) voor stappen om een installatiekopie van een besturingssysteem te distribueren.  

##  <a name="BKMK_OSImagesApplyUpdates"></a>Softwareupdates toepassen op een installatiekopie van besturingssysteem  
 Van tijd tot tijd verschijnen er nieuwe software-updates die van toepassing zijn op het besturingssysteem in uw installatiekopie. Voordat u software-updates op een installatiekopie toepassen kunt hebt u uw software-updates-infrastructuur in plaatsen, software-updates zijn gesynchroniseerd en de updates worden gedownload naar de Inhoudsbibliotheek op de siteserver. Zie voor meer informatie [software-updates implementeren](../../sum/deploy-use/deploy-software-updates.md).  

 U kunt toepasselijke software-updates volgens een opgegeven schema toepassen op een installatiekopie. Volgens de planning die u opgeeft, Configuration Manager is van toepassing de software-updates die u selecteert op de besturingssysteemkopie en vervolgens wordt de bijgewerkte installatiekopie naar distributiepunten optioneel gedistribueerd. Informatie over de installatiekopie van het besturingssysteem wordt opgeslagen in de sitedatabase, inclusief de software-updates die tijdens het importeren zijn toegepast. Software-updates die op de installatiekopie zijn toegepast sinds de kopie voor het eerst werd toegevoegd, worden ook opgeslagen in de sitedatabase. Wanneer u de wizard start om software-updates toe te passen op de installatiekopie van het besturingssysteem, wordt er een lijst opgehaald met toepasselijke software-updates die nog niet zijn toegepast op de installatiekopie. U kunt dan een selectie maken uit deze lijst. Configuration Manager opgehaald van de software-updates uit de Inhoudsbibliotheek op de siteserver en de software-updates van toepassing is op de installatiekopie van het besturingssysteem.  

 Gebruik de volgende procedure om software-updates toe te passen op een installatiekopie van een besturingssysteem.  

#### <a name="to-apply-software-updates-to-an-operating-system-image"></a>Software-updates toepassen op een installatiekopie van een besturingssysteem  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** de optie **Besturingssystemen** uit en klik vervolgens op **Installatiekopieën van besturingssysteem**.  

3.  Selecteer de installatiekopie waarop u software-updates wilt toepassen.  

4.  Klik op het tabblad **Start** in de groep **Installatiekopie van het besturingssysteem** op **Updates plannen** om de wizard te starten.  

5.  Selecteer op de pagina **Updates kiezen** de software-updates die moeten worden toegepast op de installatiekopie van het besturingssysteem en klik vervolgens op **Volgende**.  

6.  Geef, op de pagina **Schema instellen** , de volgende instellingen op, en klik vervolgens op **Volgende**.  

    1.  **Planning**: Geef het schema voor wanneer de software-updates worden toegepast op de installatiekopie van het besturingssysteem.  

    2.  **Doorgaan bij fout**:  Selecteer deze optie om door te gaan naar het software-updates toepassen op de installatiekopie, zelfs wanneer er een fout is opgetreden.  

    3.  **De installatiekopie distribueren naar distributiepunten**: Selecteer deze optie om de installatiekopie van het besturingssysteem op distributiepunten werken nadat de software-updates zijn toegepast.  

7.  Verifieer de informatie op de pagina **Samenvatting** en klik vervolgens op **Volgende**.  

8.  Verifieer op de pagina **Voltooiing** dat de software-updates met succes zijn toegepast op de installatiekopie van het besturingssysteem.  

##  <a name="BKMK_OSImageMulticast"></a>Voorbereiden van de installatiekopie van het besturingssysteem voor multicast-implementaties  
 Gebruik multicast-implementaties om toe te staan dat meerdere computers tegelijkertijd de installatiekopie van een besturingssysteem downloaden. Het distributiepunt bezorgt de installatiekopie via multicast bij clients. Het distributiepunt verzendt dus geen kopie van de installatiekopie naar elke client via een aparte verbinding. Als u zich de [gebruik multicast om Windows te implementeren via het netwerk](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md) system implementatiemethode werkt, moet u het installatiekopiepakket van het besturingssysteem voor multicast-ondersteuning voordat u de installatiekopie van het besturingssysteem naar een multicast-distributiepunt distribueren. Gebruik de volgende procedure om de multicast-opties in te stellen voor een bestaand installatiekopiepakket van een besturingssysteem.  

#### <a name="to-modify-an-operating-system-image-package-to-use-multicast"></a>Een installatiekopiepakket van een besturingssysteem wijzigen voor het gebruik van multicast  

1.  Klik in de Configuration Manager-console op **Softwarebibliotheek**.  

2.  Vouw in de werkruimte **Softwarebibliotheek** de optie **Besturingssystemen** uit en klik vervolgens op **Installatiekopieën van besturingssysteem**.  

3.  Selecteer de installatiekopie van het besturingssysteem die u op het multicast-distributiepunt wilt distribueren.  

4.  Klik op het tabblad **Start** in de groep **Eigenschappen** op **Eigenschappen**.  

5.  Selecteer het tabblad **Distributie-instellingen** en configureer de volgende opties:  

    -   **Toestaan dat dit pakket kan worden overgedragen via multicast (alleen WinPE)**: U moet deze optie voor Configuration Manager voor het implementeren van installatiekopieën van besturingssystemen tegelijkertijd selecteren.  

    -   **Multicast-pakketten versleutelen**: Geef op of de installatiekopie wordt versleuteld voordat deze wordt verzonden naar het distributiepunt. Gebruik deze optie als het pakket gevoelige informatie bevat. Als de installatiekopie niet wordt versleuteld, is de inhoud van het pakket als niet-versleutelde tekst zichtbaar in het netwerk en wordt daar mogelijk gelezen door onbevoegde gebruikers.  

    -   **Dit pakket alleen overdragen via multicast**: Opgeven of u wilt dat het distributiepunt om de installatiekopie alleen tijdens een multicast-sessie.  

         Als u **Dit pakket alleen overdragen via multicast** selecteert, moet u ook **De inhoud lokaal downloaden wanneer deze nodig is voor de takenreeks die wordt uitgevoerd** opgeven als implementatieoptie voor de installatiekopie van het besturingssysteem. U kunt de implementatieopties voor de installatiekopie opgeven wanneer u de installatiekopie van het besturingssysteem implementeert, of u kunt ze later opgeven door de eigenschappen van de implementatie te bewerken. De implementatieopties zijn te vinden op het tabblad **Distributiepunten** van de pagina **Eigenschappen** voor het implementatieobject.  

6.  Klik op **OK**.  

