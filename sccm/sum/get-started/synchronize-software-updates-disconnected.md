---
title: Updates synchroniseren met geen verbinding met Internet - Configuration Manager | Microsoft Docs
description: Synchronisatie van software-updates uitgevoerd op het hoogste niveau software-updatepunt dat niet is verbonden met Internet.
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 1a997c30-8e71-4be5-89ee-41efb2c8d199
ms.openlocfilehash: fd9c1e9418ff1956c6ef98753e23a293440179be
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="synchronize-software-updates-from-a-disconnected-software-update-point"></a>Software-updates vanaf een niet-verbonden software-updatepunt synchroniseren  

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Wanneer de verbinding van het software-updatepunt op de site op het hoogste niveau met het internet verbroken is, moet u de export- en importfuncties van het WSUSUtil-hulpprogramma gebruiken om metagegevens van software-updates te synchroniseren. U kunt een bestaande WSUS-server niet in uw Configuration Manager-hiërarchie als de synchronisatiebron. In dit onderwerp bevat informatie over hoe u de export- en importfuncties van het WSUSUtil-hulpprogramma.  

 Om metagegevens van software-updates te exporteren en te importeren moet u de metagegevens van de software-updates exporteren vanuit de WSUS-database op een gespecificeerde exportserver, vervolgens moet u de lokaal opgeslagen licentievoorwaardenbestanden kopiëren naar het niet-verbonden software-updatepunt, en dan moet u de metagegevens van de software-updates importeren in de WSUS-database op het niet-verbonden software-updatepunt.  

 Gebruik de volgende tabel om de exportserver te identificeren waarnaar de metagegevens van de software-updates moeten worden geëxporteerd.  

|Sitesysteemrollen toevoegen|Updatebron stroomopwaarts voor verbonden software-updatepunten|Exportserver voor een niet-verbonden software-updatepunt|  
|---------------------------|-----------------------------------------------------------------|------------------------------------------------------------|  
|Centrale beheersite|Microsoft Update (internet)<br /><br /> Bestaande WSUS-server|Kies een WSUS-server die is gesynchroniseed met Microsoft Update met behulp van de software-updateclassificaties, producten en talen die u nodig hebt in uw Configuration Manager-omgeving.|  
|Zelfstandige primaire site|Microsoft Update (internet)<br /><br /> Bestaande WSUS-server|Kies een WSUS-server die is gesynchroniseed met Microsoft Update met behulp van de software-updateclassificaties, producten en talen die u nodig hebt in uw Configuration Manager-omgeving.|  

 Voordat u het exportproces start, dient u te controleren of de synchronisatie van software-updates voltooid is op de geselecteerde exportserver om ervoor te zorgen dat de meest recente metagegevens van software-updates worden gesynchroniseerd. Volg de volgende procedure om te controleren of de synchronisatie van software-updates voltooid is.  

#### <a name="to-verify-that-software-updates-synchronization-has-completed-successfully-on-the-export-server"></a>Controleren of de synchronisatie van software-updates voltooid is op de exportserver.  

1.  Open de WSUS-beheerconsole en maak een verbinding met de WSUS-database op de exportserver.  

2.  Klik op **Synchronisatie**in de WSUS-beheerconsole. Er wordt een lijst van synchronisatiepogingen van software-updates getoond in het resultatenvenster.  

3.  In het resultatenvenster ziet u de laatste synchronisatiepoging van software-updates en kunt u controleren of het met succes voltooid was.  

> [!IMPORTANT]  
>  Het WSUSUtil-hulpprogramma moet lokaal op de exportserver worden uitgevoerd om de metagegevens van software-updates te exporteren, en het moet ook worden uitgevoerd op de niet-verbonden software-updatepuntserver om de metagegevens van software-updates te importeren. Daarnaast moet de gebruiker die het WSUSUtil-hulpprogramma uitvoert, lid zijn van de lokale groep Administrators op elke server.  

## <a name="export-process-for-software-updates"></a>Exportproces voor software-updates  
 Het exportproces voor software-updates bestaat uit twee belangrijke stappen: het kopiëren van de lokaal opgeslagen licentievoorwaardenbestanden naar het niet-verbonden software-updatepunt, en het exporteren van de metagegevens van software-updates vanuit de WSUS-database op de exportserver.  

 Volg de volgende procedure om de lokale licentievoorwaardenbestanden naar het niet-verbonden software-updatepunt te kopiëren.  

#### <a name="to-copy-local-files-from-the-export-server-to-the-disconnected-software-update-point-server"></a>Kopiëren van lokale bestanden vanuit de exportserver naar de niet-verbonden software-updatepuntserver  

1.  Op de exportserver bladert u naar de map waar software-updates en de licentievoorwaarden voor software-upates zijn opgeslagen. De WSUS-server slaat de bestanden standaard op in <*WSUSInstallationDrive*>\WSUS\WSUSContent\\, waar *WSUSInstallationDrive* het station is waarop WSUS is geïnstalleerd.  

2.  Kopieer alle bestanden en mappen van deze locatie naar de WSUSContent-map op de niet-verbonden software-updatepuntserver.  

 Volg de volgende procedure om de metagegevens van software-updates van de WSUS-database op de exportserver te exporteren.  

#### <a name="to-export-software-updates-metadata-from-the-wsus-database-on-the-export-server"></a>Metagegevens van software-updates vanuit de WSUS-database op de exportserver exporteren  

1.  Navigeer via de opdrachtprompt op de exportserver naar de map met WSUSutil.exe. Het hulpprogramma bevindt zich standaard op de volgende locatie: %*ProgramFiles*%\Update Services\Tools. Als het hulpprogramma zich op de standaardlocatie bevindt, typ dan bijvoorbeeld **cd %ProgramFiles%\Update Services\Tools**.  

2.  Typ het volgende om de metagegevens van software-updates naar een pakketbestand te exporteren:  

     **wsusutil.exe export**  *packagename*  *logfile*  

     Bijvoorbeeld:  

     **wsusutil.exe export export.cab export.log**  

     De notatie kan als volgt worden samengevat: WSUSutil.exe wordt gevolgd door de exportoptie, de naam van het cab-exportbestand dat is gemaakt tijdens de exportbewerking en de naam van een logbestand. WSUSutil.exe exporteert de metagegevens van de exportserver en maakt een logbestand van de bewerking.  

    > [!NOTE]  
    >  Het pakket (.cab-bestand) en de naam van het logbestand moeten uniek zijn in de huidige map.  

3.  Verplaats het exportpakket naar de map die WSUSUtil.exe bevat op de WSUS-importserver.  

    > [!NOTE]  
    >  Als u het pakket naar deze map verplaatst, kan de import eenvoudiger zijn. U kunt het pakket naar eender welke locatie verplaatsen die toegankelijk is voor de importserver, en dan de locatie opgeven wanneer u WSUSUtil.exe uitvoert.  

## <a name="import-software-updates-metadata"></a>Metagegevens van software-updates importeren  
 Volg de volgende procedure om metagegevens van software-updates te importeren vanuit de exporserver naar het niet-verbonden software-updatepunt.  

> [!IMPORTANT]  
>  Importeer nooit geëxporteerde gegevens vanuit een bron die u niet vertrouwt. Als u inhoud importeert vanuit een bron die u niet vertrouwt, kan het de beveiliging van uw WSUS-server mogelijk beschadigen.  

#### <a name="to-import-metadata-to-the-database-of-the-import-server"></a>Metagegevens importeren in de database van de importserver  

1.  Navigeer via de opdrachtprompt op de WSUS-importserver naar de map met WSUSutil.exe. Het hulpprogramma bevindt zich standaard op de volgende locatie: %*ProgramFiles*%\Update Services\Tools.  

2.  Typ het volgende:  

     **wsusutil.exe import**  *packagename*  *logfile*  

     Bijvoorbeeld:  

     **wsusutil.exe import export.cab import.log**  

     De notatie kan als volgt worden samengevat: WSUSutil.exe wordt gevolgd door de importopdracht, de naam van het pakketbestand (.cab) dat is gemaakt tijdens de exportbewerking, het pad naar het pakketbestand als het zich in een andere map en de naam van een logbestand. WSUSutil.exe importeert de metagegevens vanuit de exportserver en maakt een logbestand van de bewerking.  

## <a name="next-steps"></a>Volgende stappen
Nadat u software-updates voor het eerst synchroniseert, of nadat er nieuwe classificaties of producten beschikbaar zijn, u moet [de nieuwe classificaties en producten configureren](configure-classifications-and-products.md) softwareupdates te synchroniseren met de nieuwe criteria.

Nadat u de software-updates synchroniseren met de criteria die u nodig hebt, [instellingen beheren voor software-updates](manage-settings-for-software-updates.md).  
