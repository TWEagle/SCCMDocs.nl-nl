---
title: Publicatie- en Active Directory-schema
titleSuffix: Configuration Manager
description: Breid het Active Directory-schema voor System Center Configuration Manager en het proces van het implementeren en configureren van clients vereenvoudigen.
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: "17"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 747d194d8244d42d557bc442f09035808f6eb2f0
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="prepare-active-directory-for-site-publishing"></a>Active Directory voorbereiden voor het publiceren van site

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u het Active Directory-schema voor System Center Configuration Manager uitbreidt, kunt u nieuwe structuren introduceren in Active Directory die worden gebruikt door Configuration Manager-sites voor het publiceren van belangrijke gegevens op een veilige locatie waar eenvoudig toegankelijk is voor clients.  

Er is een goed idee Configuration Manager gebruiken met een uitgebreid Active Directory-schema bij het beheren van lokale clients. Een uitgebreid schema kan het proces van het implementeren en instellen van clients vereenvoudigen. Een uitgebreid schema kan ook clients die bronnen zoals inhoudsservers en aanvullende services die de verschillende sitesysteemrollen van Configuration Manager bieden efficiënt te zoeken.  

-   Als u niet bekend bent met welk uitgebreid schema voorziet in een Configuration Manager-implementatie, kunt u lezen over [Schema-uitbreidingen voor System Center Configuration Manager](../../../core/plan-design/network/schema-extensions.md) kunt u deze beslissing over.  

-   Wanneer u niet een uitgebreid schema gebruikt, kunt u andere methoden zoals DNS en WINS om services en sitesysteemservers te vinden instellen. Voor deze methoden van servicelocatie zijn aanvullende configuraties vereist en de methoden hebben niet de voorkeur bij servicelocatie door clients. Voor meer informatie lezen [begrijpen hoe clients siteresources en -services voor System Center Configuration Manager vinden](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md),  

-   Als uw Active Directory-schema is uitgebreid voor Configuration Manager 2007 of System Center 2012 Configuration Manager, moet u niet meer doen. De schema-uitbreidingen zijn ongewijzigd en zijn al aanwezig.  

Het schema uitbreiden is een eenmalige bewerking voor elk forest. Als u wilt uitbreiden en vervolgens met de uitgebreide Active Directory-schema, de volgende stappen uit:  

## <a name="step-1-extend-the-schema"></a>Stap 1. Het schema uitbreiden  
Het schema voor Configuration Manager uitbreiden:  

-   Gebruik een account dat lid is van de beveiligingsgroep Schemabeheerders.  

-   Worden aangemeld bij de schemamaster-domeincontroller.  

-   Voer de **Extadsch.exe** hulpprogramma of gebruik het opdrachtregelhulpprogramma LDIFDE met het **ConfigMgr_ad_schema.ldf** bestand. Het hulpprogramma en het bestand zich in de **SMSSETUP\BIN\X64** map op de installatiemedia van Configuration Manager.  

#### <a name="option-a-use-extadschexe"></a>Optie A: Gebruik Extadsch.exe  

1.  Voer **extadsch.exe** uit om nieuwe klassen en kenmerken aan het Active Directory-schema toe te voegen.  

    > [!TIP]  
    >  Voer dit hulpprogramma uit vanaf een opdrachtregel om feedback weer te geven terwijl het programma wordt uitgevoerd.  

2.  Controleren of de schema-uitbreiding gelukt is aan de hand van extadsch.log in de hoofdmap van het systeemstation.  

#### <a name="option-b-use-the-ldif-file"></a>Optie B: Gebruik het LDIF-bestand  

1.  Bewerk de **ConfigMgr_ad_schema.ldf** bestand voor het definiëren van het Active Directory-hoofddomein dat u wilt uitbreiden:  

    -   Vervang alle exemplaren van de tekst, **DC = x**, in het bestand met de volledige naam van het domein uit te breiden.  

    -   Bijvoorbeeld als de volledige naam van de uit te breiden domein widgets.microsoft.com naam, Wijzig alle instanties van DC = x in het bestand naar **DC = widgets, DC = microsoft, DC = com**.  

2.  Gebruik het opdrachtregelhulpprogramma LDIFDE om te importeren van de inhoud van de **ConfigMgr_ad_schema.ldf** bestand naar Active Directory Domain Services:  

    -   Bijvoorbeeld de volgende opdrachtregel de schema-uitbreidingen in Active Directory Domain Services geïmporteerd, wordt uitgebreide logboekregistratie ingeschakeld en wordt een logboekbestand gemaakt tijdens het importproces: **ldifde -i -f ConfigMgr_ad_schema.ldf - v -j &lt;locatie voor het opslaan van logboekbestand\>**.  

3.  Om te controleren of de schema-uitbreiding geslaagd is, bekijk een logboekbestand gemaakt door de opdrachtegel in de vorige stap.  

## <a name="step-2--create-the-system-management-container-and-grant-sites-permissions-to-the-container"></a>Stap 2.  De container Systeembeheer maken en sites machtigingen aan de container toekennen  
 Nadat u het schema uitbreidt, moet u een container met de naam **System Management** in Active Directory Domain Services (AD DS):  

-   U maakt deze container één keer in elk domein met een primaire of secundaire site die gegevens naar Active Directory publiceert.  

-   Voor elke container verlenen u machtigingen voor het computeraccount van elke primaire en secundaire siteserver die gegevens naar dat domein publiceert. Elk account moet **volledig beheer** aan de container met de geavanceerde machtiging **toepassen op**gelijk is aan **dit object en alle onderliggende objecten**.  

#### <a name="to-add-the-container"></a>De container toevoegen  

1.  Gebruik een account dat beschikt over de machtiging **Alle onderliggende objecten maken** in de container **Systeem** in Active Directory Domain Services.  

2.  Voer **ADSI Edit** (adsiedit.msc) uit en maak verbinding met het domein van de siteserver.  

3.  Maak de container:  

    -   Vouw **domein** &lt;computer volledig gekwalificeerde domeinnaam\>, vouw &lt;DN-naam\>, met de rechtermuisknop op **CN = systeem**, kies **nieuw**, en kies vervolgens **Object**.  

    -   In de **Object maken** dialoogvenster Kies **Container**, en kies vervolgens **volgende**.  

    -   In de **waarde** Voer **System Management**, en kies vervolgens **volgende**.  

4.  Wijs machtigingen toe:  

    > [!NOTE]  
    >  Als u liever, kunt u andere hulpprogramma's zoals de Active Directory: gebruikers en beheerhulpmiddelen voor Computers (dsa.msc) machtigingen toevoegen aan de container.  

    -   Met de rechtermuisknop op **CN = System Management**, en kies vervolgens **eigenschappen**.  

    -   Kies de **beveiliging** Kies **toevoegen**, en voeg de computeraccount van de siteserver met de **volledig beheer** machtiging.  

    -   Kies **Geavanceerd**, kiest u het computeraccount van de siteserver en kies vervolgens **bewerken**.  

    -   In de **toepassen op** Kies **dit object en alle onderliggende objecten**.  

5.  Kies **OK** naar de console sluiten en de configuratie op te slaan.  

## <a name="step-3-set-up-sites-to-publish-to-active-directory-domain-services"></a>Stap 3. Sites publiceren naar Active Directory Domain Services instellen  
 Nadat de container is ingesteld, machtigingen worden toegekend en u een primaire site van Configuration Manager hebt geïnstalleerd, kunt u die site instellen om gegevens te publiceren naar Active Directory.  

 Zie voor meer informatie over publiceren [sitegegevens voor System Center Configuration Manager publiceren](../../../core/servers/deploy/configure/publish-site-data.md).  
