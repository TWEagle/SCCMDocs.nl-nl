---
title: Publiceren en het Active Directory-schema | Microsoft-documenten
description: Breid het Active Directory-schema voor System Center Configuration Manager om het proces van implementatie en configuratie van clients te vereenvoudigen.
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bc15ee7e-4d0a-4463-ae2c-f72d8d45d65d
caps.latest.revision: 17
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 88649111ea3a38c027efb4952211546afd0bf27e
ms.openlocfilehash: 58beef440db8e019a06ce7c4c8eaabc8e85ce954
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-active-directory-for-site-publishing"></a>Active Directory voorbereiden voor sitepublicatie

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Wanneer u het Active Directory-schema voor System Center Configuration Manager uitbreidt, wordt het nieuwe structuren kennismaken met Active Directory die worden gebruikt door Configuration Manager-sites sleutel om informatie te publiceren op een veilige locatie waar clients deze gemakkelijk kunnen bereiken.  

Er is een goed idee voor gebruik van Configuration Manager met een uitgebreide Active Directory-schema bij het beheren van lokale clients. Een uitgebreide schema kan het proces voor het implementeren en het instellen van clients te vereenvoudigen. Een uitgebreide schema kan ook efficiënt Zoek bronnen zoals inhoudsservers en extra services waarmee de verschillende sitesysteemfuncties van Configuration Manager-clients.  

-   Als u niet vertrouwd bent met welke uitgebreide schema voor de implementatie van een Configuration Manager geeft, kunt u lezen over [voor System Center Configuration Manager-Schema-uitbreidingen](../../../core/plan-design/network/schema-extensions.md) bij het beste beslissing kunt nemen.  

-   Wanneer u een uitgebreide schema niet gebruikt, kunt u andere methoden, zoals DNS en WINS vinden, services en sitesysteemservers instellen. Voor deze methoden van servicelocatie zijn aanvullende configuraties vereist en de methoden hebben niet de voorkeur bij servicelocatie door clients. Lees voor meer informatie, [begrijpen hoe clients vinden sitebronnen en services voor System Center Configuration Manager](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md),  

-   Als uw Active Directory-schema is uitgebreid voor Configuration Manager 2007 of System Center 2012 Configuration Manager, moet u niet meer doen. De schema-uitbreidingen is zijn niet gewijzigd en al aanwezig.  

Het schema uitbreiden is een eenmalige bewerking voor elke forest. Als u wilt uitbreiden, en vervolgens de uitgebreide Active Directory-schema, als volgt te werk:  

## <a name="step-1-extend-the-schema"></a>Stap 1. Het schema uitbreiden  
Het schema voor Configuration Manager uitbreiden:  

-   Gebruik een account dat lid is van de beveiligingsgroep Schemabeheerders.  

-   Zijn aangemeld op de schemamaster-domeincontroller.  

-   Voer de **Extadsch.exe** hulpprogramma of gebruik het LDIFDE opdrachtregel-hulpprogramma met de **ConfigMgr_ad_schema.ldf** bestand. Het hulpprogramma en het bestand zich in de **SMSSETUP\BIN\X64** map op de installatiemedia van Configuration Manager.  

#### <a name="option-a-use-extadschexe"></a>Optie A: Extadsch.exe gebruiken  

1.  Voer **extadsch.exe** uit om nieuwe klassen en kenmerken aan het Active Directory-schema toe te voegen.  

    > [!TIP]  
    >  Voer dit hulpprogramma uit vanaf een opdrachtregel om feedback weer te geven terwijl het programma wordt uitgevoerd.  

2.  Controleer of de schemauitbreiding slaagde aan de hand van extadsch.log in de hoofdmap van het systeemstation.  

#### <a name="option-b-use-the-ldif-file"></a>Optie B: Gebruik het LDIF-bestand  

1.  Bewerk de **ConfigMgr_ad_schema.ldf** bestand om het Active Directory-hoofddomein dat u wilt uitbreiden te definiëren:  

    -   Alle instanties van de tekst vervangen **DC = x**, in het bestand met de volledige naam van het domein uit te breiden.  

    -   Bijvoorbeeld, als de volledige naam van de uit te breiden domein widgets.Microsoft.com is, wijzig dan alle instanties van DC = x in het bestand naar **DC = widgets, DC = microsoft, DC = com**.  

2.  Gebruik het LDIFDE opdrachtregel-hulpprogramma voor het importeren van de inhoud van de **ConfigMgr_ad_schema.ldf** -bestand naar Active Directory Domain Services:  

    -   Bijvoorbeeld, de volgende opdrachtregel de schema-uitbreidingen naar Active Directory Domain Services importeert u uitgebreide logboekregistratie inschakelen en een logboekbestand gemaakt tijdens het importeren: **ldifde -i -f ConfigMgr_ad_schema.ldf - v -j &lt;locatie voor het opslaan van logboekbestand\>**.  

3.  Om te bevestigen dat de schemauitbreiding slaagde, door een logboekbestand gemaakt door de opdrachtegel in de vorige stap te controleren.  

## <a name="step-2--create-the-system-management-container-and-grant-sites-permissions-to-the-container"></a>Stap 2.  De container Systeembeheer maken en sites machtigingen aan de container toekennen  
 Nadat u het schema uitbreidt, moet u een container met de naam **Systeembeheer** in Active Directory Domain Services (AD DS):  

-   U maakt deze container één keer in elk domein met een primaire of secundaire site die gegevens op Active Directory publiceren zal.  

-   Voor elke container toewijzen u machtigingen aan het computeraccount van elke primaire en secundaire site-server die gegevens met dat domein publiceren zal. Elk account moet **volledig beheer** voor de container met de machtiging geavanceerde **toepassen op**, gelijk zijn aan **dit object en alle onderliggende objecten**.  

#### <a name="to-add-the-container"></a>De container toevoegen  

1.  Gebruik een account dat beschikt over de machtiging **Alle onderliggende objecten maken** in de container **Systeem** in Active Directory Domain Services.  

2.  Voer **ADSI Edit** (adsiedit.msc)), en maak verbinding met het domein van de siteserver.  

3.  Maak de container:  

    -   Vouw **domein** &lt;computer volledig gekwalificeerde domeinnaam\>, vouw &lt;DN-naam\>, met de rechtermuisknop op **CN = systeem**, kies **New**, en kies vervolgens **Object**.  

    -   In de **Maak Object** dialoogvenster Kies **Container**, en kies vervolgens **volgende**.  

    -   In de **waarde** Voer **System Management**, en kies vervolgens **volgende**.  

4.  Wijs machtigingen toe:  

    > [!NOTE]  
    >  Als u wilt, kunt u andere hulpprogramma's zoals het administratief beheer Active Directory: gebruikers en Computers (dsa.msc) machtigingen toevoegen aan de container.  

    -   Met de rechtermuisknop op **CN = Systeembeheer**, en kies vervolgens **eigenschappen**.  

    -   Kies de **beveiliging** Kies **toevoegen**, en voeg de computeraccount van de siteserver met de **volledig beheer** machtiging.  

    -   Kies **Geavanceerd**, kiest u de computeraccount van de siteserver en kies vervolgens **bewerken**.  

    -   In de **toepassen op** Kies **dit object en alle onderliggende objecten**.  

5.  Kies **OK** de console sluiten en de configuratie op te slaan.  

## <a name="step-3-set-up-sites-to-publish-to-active-directory-domain-services"></a>Stap 3. Sites publiceren naar Active Directory Domain Services instellen  
 Nadat de container is ingesteld, machtigingen en u een primaire Configuration Manager-site hebt geïnstalleerd, kunt u die site instellen om gegevens te publiceren naar Active Directory.  

 Zie voor meer informatie over publiceren [sitegegevens publiceren voor System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md).  

