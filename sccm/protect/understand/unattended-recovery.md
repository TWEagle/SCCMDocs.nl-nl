---
title: Herstel zonder toezicht
titleSuffix: Configuration Manager
description: Een script gebruiken voor het herstellen van uw sites in System Center Configuration Manager.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828c31d1-3d70-4412-b1a8-c92e7e504d39
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: fc6325d00e048fbbf54d740a89f78070fac6b0cb
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="unattended-site-recovery-for-configuration-manager"></a>Herstel van sites zonder toezicht voor Configuration Manager   

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

 Om uit te voeren een [herstel zonder toezicht](/sccm/protect/understand/recover-sites#site-recovery-procedures) van een Configuration Manager-centrale beheersite of primaire site, kunt u een installatiescript zonder toezicht maken en vervolgens setup gebruiken met de **/script** opdracht optie. Het script geeft hetzelfde type informatie die de installatiewizard vraagt, behalve dat er geen standaardinstellingen. Alle waarden moeten worden gespecificeerd voor de installatiesleutels die van toepassing zijn op het type herstel dat u gebruikt.

 Als u wilt de installatieopdrachtregeloptie gebruiken, moet u een initialisatiebestand maken. Vervolgens deze bestandsnaam opgeven na de optie/script. De naam van het bestand is niet belangrijk zolang deze heeft de **.ini** bestandsnaamextensie. Wanneer u verwijst naar het installatie-initialisatiebestand van de opdrachtregel, moet u het volledige pad naar het bestand geven. Als de naam van uw installatie-initialisatiebestand bijvoorbeeld *setup.ini*, en deze is opgeslagen de *map C:\setup*, zou uw opdrachtregel:

 `setup /script c:\setup\setup.ini`

> [!IMPORTANT]  
>  U moet beheerdersrechten setup uit te voeren. Wanneer u setup met het script zonder toezicht uitvoert, start u de opdrachtprompt in een beheerderscontext met behulp van **als administrator uitvoeren**.

 Het script bevat sectienamen, sleutelnamen en waarden. Vereiste sectiesleutelnamen variëren afhankelijk van het hersteltype waarvoor u een script schrijft. De volgorde van de sleutels binnen secties en de volgorde van secties binnen het bestand zijn niet belangrijk. De sleutels zijn niet hoofdlettergevoelig. Wanneer u waarden voor sleutels opgeeft, moet de naam van de sleutel worden gevolgd door een gelijkteken (=) en de waarde voor de sleutel.

 Gebruik de volgende secties om u te helpen uw script te maken voor herstel van sites zonder toezicht. De tabellen geven een lijst van de beschikbare installatiescriptsleutels, de overeenkomstige waarden ervan, of ze al dan niet vereist zijn, voor welk type installatie ze worden gebruikt en een korte beschrijving voor de sleutel.

## <a name="recover-a-central-administration-site-unattended"></a>Herstellen van een centrale beheersite zonder toezicht
 Gebruik de volgende informatie voor het configureren van een scriptbestand voor installatie zonder toezicht om een centrale beheersite te herstellen.

 **Identificatie**

-   **Naam sleutel:** Actie

    -   **Vereist:** Ja
    -   **Waarden:** RecoverCCAR
    -   **Details:** Hiermee herstelt u een centrale beheersite


-   **Naam sleutel:** CDLatest

    -   **Vereist:** Ja, alleen bij gebruik van media vanaf de CD. Meest recente map.
    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.
    -   **Details:** Wanneer u setup vanaf media in een CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite herstelt. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**RecoveryOptions**   
-   **Naam sleutel:** ServerRecoveryOptions   

    -   **Vereist:** Ja
    -   **Waarden:** 1, 2 of 4  
         1 = Siteserver en SQL-server herstellen.   
         2 = Alleen siteserver herstellen.  
         4 = Alleen SQL Server herstellen.
    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide wordt hersteld. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instelt voor de instelling ServerRecoveryOptions:  
        -   **Waarde = 1** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.

             De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.

        -   **Waarde = 2** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.

        -   **Waarde = 4** de sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.

-   **Naam sleutel:** DatabaseRecoveryOptions

    -   **Vereist:** Maybe
    -   **Waarden:**   
         - **10** = de sitedatabase van back-up herstellen.  
         - **20** = gebruik een sitedatabase die handmatig is hersteld met een andere methode.   
         - **40** = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  
         - **80** = databaseherstel overslaan.
    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door setup wordt hersteld. Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.


-   **Naam sleutel:** ReferenceSite  

    -   **Vereist:** Maybe
    -   **Waarden:** &lt;ReferenceSiteFQDN\>
    -   **Details:** Hiermee geeft u de primaire referentiesite. Als de databaseback-up ouder is dan de bewaarperiode voor bijhouden of als u een site zonder een back-up herstelt, gebruikt de centrale beheersite de referentiesite globale gegevens herstelt.

         Wanneer u geen referentiesite opgeeft en de back-up ouder is dan de bewaarperiode voor bijhouden, worden alle primaire sites opnieuw geïnitialiseerd met de herstelde gegevens van de centrale beheersite.

         Wanneer u geen referentiesite opgeeft en de back-up valt binnen de bewaarperiode voor bijhouden, worden enkel wijzigingen sinds de back-up gerepliceerd van primaire sites. Wanneer er conflicterende wijzigingen van verschillende primaire sites zijn, gebruikt de centrale beheersite de eerste die het ontvangt.

         Deze sleutel is vereist wanneer de instelling **DatabaseRecoveryOptions** een waarde heeft van **40**.

-   **Naam sleutel:** SiteServerBackupLocation

    -   **Vereist:** Nee
    -   **Waarden:** &lt;PathToSiteServerBackupSet\>
    -   **Details:** Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.


-   **Naam sleutel:** Back-uplocatie

    -   **Vereist:** Maybe
    -   **Waarden:** &lt;PathToSiteDatabaseBackupSet\>
    -   **Details:** Hiermee geeft u het pad naar back-upset van de sitedatabase. De sleutel **BackupLocation** is vereist wanneer u een waarde van **1** of **4** configureert voor de sleutel **ServerRecoveryOptions** en een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** .


**Opties**

-   **Naam sleutel:** Product-id
    -   **Vereist:** Ja
    -   **Waarden:**   
         - xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
         - Eval
    -   **Details:** De Configuration Manager installatieproductcode, inclusief de streepjes. Voer **Eval** de evaluatieversie van Configuration Manager kunt installeren.  


-   **Naam sleutel:** SiteCode

    -   **Vereist:** Ja
    -   **Waarden:** &lt;Sitecode\>
    -   **Details:** Drie alfanumerieke tekens die de site in uw hiërarchie identificeren. De sitecode opgeven die werd gebruikt door de site vóór de fout.


-   **Naam sleutel:** SiteName

    -   **Vereist:** Ja
    -   **Waarden:** SiteName
    -   **Details:** Beschrijving voor deze site.


-   **Naam sleutel:** SMSInstallDir

    -   **Vereist:** Ja
    -   **Waarden:** &lt;*ConfigMgrInstallationPath*>
    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.
        > [!NOTE]   
        >  U kunt het oorspronkelijke pad of een nieuw pad wilt gebruiken voor de Configuration Manager-installatie opgeven.

-   **Naam sleutel:** SDKServer

    -   **Vereist:** Ja
    -   **Waarden:** &lt;*FQDN van SMS-Provider*>
    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als host fungeert voor de SMS-Provider. Geef op de server die als host van de SMS-Provider voorafgaand aan de fout.

         U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.

-   **Naam sleutel:** PrerequisiteComp

    -   **Vereist:** Ja
    -   **Waarden:** 0 of 1  
         0 = downloaden   
         1 = reeds gedownload
    -   **Details:** Hiermee geeft u op of setup vereiste bestanden al zijn gedownload. Als u de waarde 0 gebruikt, downloadt setup de bestanden.  


-   **Naam sleutel:** PrerequisitePath

    -   **Vereist:** Ja
    -   **Waarden:** &lt;*PathToSetupPrerequisiteFiles*>
    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor setup. Afhankelijk van de **PrerequisiteComp** waarde, gebruikt het installatieprogramma dit pad gedownloade bestanden wilt opslaan of vinden eerder gedownloade bestanden.

-   **Naam sleutel:** AdminConsole

    -   **Vereist:** Maybe
    -   **Waarden:** 0 of 1 0 = niet installeert   
         1 = installeren
    -   **Details:** Geeft aan of de Configuration Manager-console te installeren. Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.


-   **Naam sleutel:** JoinCEIP   
    > [!Note]  
    > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.

    -   **Vereist:** Ja
    -   **Waarden:** 0 of 1  
         0 = niet aanmelden  
         1 = aanmelden
    -   **Details:** Hiermee geeft u op of u deelneemt aan het programma voor kwaliteitsverbetering.

**SQLConfigOptions**

-   **Naam sleutel:** SQLServerName

    -   **Vereist:** Ja
    -   **Waarden:** *&lt;SQLServerName\>*
    -   **Details:** De naam van de server of de naam van de geclusterde instantie, met SQL Server die als host fungeert voor de sitedatabase. Geef op dezelfde server die de sitedatabase voorafgaand aan de fout wordt gehost.


-   **Naam sleutel:** DatabaseName

    -   **Vereist:** Ja
    -   **Waarden:** *&lt;SiteDatabaseName\>*  of  *&lt;InstanceName\>*\\*&lt;SiteDatabaseName\>*
    -   **Details:** De naam van de SQL Server-database maken of gebruiken voor het installeren van de database van centrale beheersite. De dezelfde databasenaam opgeven die werd gebruikt vóór de fout.

        > [!IMPORTANT]  
        >  Als u het standaardexemplaar niet gebruikt, moet u de exemplaarnaam en de naam van de sitedatabase opgeven.

-   **Naam sleutel:** SQLSSBPort

    -   **Vereist:** Nee
    -   **Waarden:** &lt;*SSBPortNumber*>
    -   **Details:** Geef de SQL Server Service Broker (SSB)-poort die wordt gebruikt door SQL Server. Doorgaans is SSB geconfigureerd om TCP-poort 4022 te gebruiken, maar andere poorten worden ondersteund. Geef dezelfde SSB-poort die werd gebruikt vóór de fout.

## <a name="recover-a-primary-site-unattended"></a>Herstellen van een primaire site zonder toezicht
 Gebruik de volgende informatie voor het configureren van een scriptbestand voor installatie zonder toezicht om een centrale beheersite te herstellen.

 **Identificatie**

-   **Naam sleutel:** Actie

    -   **Vereist:** Ja
    -   **Waarden:** RecoverPrimarySite
    -   **Details:** Hiermee herstelt u een primaire site


-   **Naam sleutel:** CDLatest

    -   **Vereist:** Ja, alleen bij gebruik van media vanaf de CD. Meest recente map.
    -   **Waarden:** 1 een andere waarde dan 1 wordt beschouwd als CD niet worden gebruikt. Meest recente.
    -   **Details:** Wanneer u setup vanaf media in een CD uitvoert moet uw script deze sleutel en waarde bevatten. Meest recente map voor het installeren van een primaire of centrale beheersite of een primaire of centrale beheersite herstelt. Deze waarde informeert setup dat media CD vormen. Meest recente wordt gebruikt.

**RecoveryOptions**

-   **Naam sleutel:** ServerRecoveryOptions

    -   **Vereist:** Ja
    -   **Waarden:** 1, 2 of 4    
         1 = Siteserver en SQL-server herstellen.   
         2 = Alleen siteserver herstellen.  
         4 = Alleen SQL Server herstellen.
    -   **Details:** Hiermee geeft u op of het installatieprogramma de siteserver, SQL Server of beide wordt hersteld. De gekoppelde sleutels zijn vereist wanneer u de volgende waarde instelt voor de instelling ServerRecoveryOptions:

        -   **Waarde = 1** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.

             De sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.

        -   **Waarde = 2** u hebt de mogelijkheid een waarde op te geven voor de sleutel **SiteServerBackupLocation** om de site te herstellen met een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.

        -   **Waarde = 4** de sleutel **BackupLocation** is vereist wanneer u een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** . Hiermee wordt de sitedatabase uit de back-up hersteld.

-   **Naam sleutel:** DatabaseRecoveryOptions

    -   **Vereist:** Maybe
    -   **Waarden:**   
         - **10** = de sitedatabase van back-up herstellen.  
         - **20** = gebruik een sitedatabase die handmatig is hersteld met een andere methode.     
         - **40** = Maak een nieuwe database voor de site. Gebruik deze optie wanneer er geen back-up van de sitedatabase beschikbaar is. Globale en sitegegevens worden hersteld via replicatie vanaf andere sites.  
         - **80** = databaseherstel overslaan.
    -   **Details:** Hiermee geeft u op hoe de sitedatabase in SQL Server door setup wordt hersteld. Deze sleutel is vereist wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **4**.


-   **Naam sleutel:** SiteServerBackupLocation

    -   **Vereist:** Nee
    -   **Waarden:** &lt;PathToSiteServerBackupSet\>
    -   **Details:** Hiermee geeft u het pad naar de back-upset van de siteserver. Deze sleutel is optioneel wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **1** of **2**. Geef een waarde op voor de sleutel **SiteServerBackupLocation** om de site te herstellen met behulp van een siteback-up. Als u geen waarde opgeeft, wordt de site opnieuw geïnstalleerd zonder dat deze wordt hersteld uit een back-upset.     


-   **Naam sleutel:** Back-uplocatie

    -   **Vereist:** Maybe
    -   **Waarden:** &lt;PathToSiteDatabaseBackupSet\>
    -   **Details:** Hiermee geeft u het pad naar back-upset van de sitedatabase. De sleutel **BackupLocation** is vereist wanneer u een waarde van **1** of **4** configureert voor de sleutel **ServerRecoveryOptions** en een waarde van **10** configureert voor de sleutel **DatabaseRecoveryOptions** .

**Opties**

-   **Naam sleutel:** Product-id

    -   **Vereist:** Ja
    -   **Waarden:**     
         - xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
         - Eval     
    -   **Details:** De Configuration Manager installatieproductcode, inclusief de streepjes. Voer **Eval** de evaluatieversie van Configuration Manager kunt installeren.  


-   **Naam sleutel:** SiteCode

    -   **Vereist:** Ja
    -   **Waarden:** &lt;Sitecode\>
    -   **Details:** Drie alfanumerieke tekens die de site in uw hiërarchie identificeren. De sitecode opgeven die werd gebruikt door de site vóór de fout.


-   **Naam sleutel:** SiteName

    -   **Vereist:** Ja
    -   **Waarden:** SiteName
    -   **Details:** Beschrijving voor deze site.


-   **Naam sleutel:** SMSInstallDir

    -   **Vereist:** Ja
    -   **Waarden:** &lt;*ConfigMgrInstallationPath*>
    -   **Details:** Hiermee geeft u de installatiemap voor de programmabestanden van Configuration Manager.

        > [!NOTE]   
        >  U kunt het oorspronkelijke pad of een nieuw pad wilt gebruiken voor de Configuration Manager-installatie opgeven.

-   **Naam sleutel:** SDKServer

    -   **Vereist:** Ja
    -   **Waarden:** &lt;*FQDN van SMS-Provider*>
    -   **Details:** Hiermee geeft u de FQDN-naam voor de server die als host fungeert voor de SMS-Provider. Geef op de server die als host van de SMS-Provider voorafgaand aan de fout.

         U kunt bijkomende SMS-providers voor de site configureren na de eerste installatie.

-   **Naam sleutel:** PrerequisiteComp

    -   **Vereist:** Ja
    -   **Waarden:** 0 of 1    
         0 = downloaden   
         1 = reeds gedownload   
    -   **Details:** Hiermee geeft u op of setup vereiste bestanden al zijn gedownload. Als u de waarde 0 gebruikt, downloadt setup de bestanden.


-   **Naam sleutel:** PrerequisitePath

    -   **Vereist:** Ja
    -   **Waarden:** &lt;*PathToSetupPrerequisiteFiles*>
    -   **Details:** Hiermee geeft u het pad naar de vereiste bestanden voor setup. Afhankelijk van de **PrerequisiteComp** waarde, gebruikt het installatieprogramma dit pad gedownloade bestanden wilt opslaan of vinden eerder gedownloade bestanden.


-   **Naam sleutel:** AdminConsole

    -   **Vereist:** Maybe
    -   **Waarden:** 0 of 1  
         0 = niet installeren   
         1 = installeren  
    -   **Details:** Geeft aan of de Configuration Manager-console te installeren. Deze sleutel is vereist, behalve wanneer de instelling **ServerRecoveryOptions** een waarde heeft van **4**.

-   **Naam sleutel:** JoinCEIP  
    > [!Note]  
    > Starten van de functie programma voor Kwaliteitsverbetering in Configuration Manager versie 1802 is verwijderd uit het product.

    -   **Vereist:** Ja
    -   **Waarden:** 0 of 1    
         0 = niet aanmelden  
         1 = aanmelden
    -   **Details:** Hiermee geeft u op of u deelneemt aan het programma voor kwaliteitsverbetering.


**SQLConfigOptions**

-   **Naam sleutel:** SQLServerName

    -   **Vereist:** Ja
    -   **Waarden:** *&lt;SQLServerName\>*
    -   **Details:** De naam van de server of de naam van de geclusterde instantie, met SQL Server die als host fungeert voor de sitedatabase. Geef op dezelfde server die de sitedatabase voorafgaand aan de fout wordt gehost.


-   **Naam sleutel:** DatabaseName

    -   **Vereist:** Ja
    -   **Waarden:** *&lt;SiteDatabaseName\>*  of  *&lt;InstanceName\>*\\*&lt;SiteDatabaseName\>*
    -   **Details:** De naam van de SQL Server-database maken of gebruiken voor het installeren van de database van centrale beheersite. De dezelfde databasenaam opgeven die werd gebruikt vóór de fout.

        > [!IMPORTANT]    
        >  Als u het standaardexemplaar niet gebruikt, moet u de exemplaarnaam en de naam van de sitedatabase opgeven.

-   **Naam sleutel:** SQLSSBPort

    -   **Vereist:** Nee
    -   **Waarden:** &lt;*SSBPortNumber*>
    -   **Details:** Geef de SQL Server Service Broker (SSB)-poort die wordt gebruikt door SQL Server. Doorgaans is SSB geconfigureerd om TCP-poort 4022 te gebruiken, maar andere poorten worden ondersteund. Geef dezelfde SSB-poort die werd gebruikt vóór de fout.

**Optie voor hiërarchie-uitbreiding**

-   **Naam sleutel:** CCARSiteServer

    -   **Vereist:** Maybe
    -   **Waarden:** &lt;*SiteCodeForCentralAdministrationSite*>
    -   **Details:** Hiermee geeft u de centrale beheersite die een primaire site wordt gekoppeld aan als lid van de Configuration Manager-hiërarchie. Deze instelling is vereist als de primaire site was gekoppeld aan een centrale beheersite vóór de fout. De sitecode opgeven die werd gebruikt voor de centrale beheersite vóór de fout.

-   **Naam sleutel:** CASRetryInterval

    -   **Vereist:** Nee
    -   **Waarden:** &lt;*Interval*>
    -   **Details:** Hiermee geeft u het interval (in minuten) waarna wordt geprobeerd een verbinding met de centrale beheersite nadat de verbinding is verbroken. Bijvoorbeeld, als de verbinding met de centrale beheersite mislukt, de primaire site wacht gedurende het aantal minuten dat u voor CASRetryInterval opgeeft, en vervolgens reattempts de verbinding.


-   **Naam sleutel:** WaitForCASTimeout

    -   **Vereist:** Nee
    -   **Waarden:** &lt;*Timeout*>
    -   **Details:** Hiermee geeft u de maximum time-outwaarde (in minuten) voor een primaire site verbinding maken met de centrale beheersite. Als een primaire site bijvoorbeeld geen verbinding kan maken met een centrale beheersite, probeert de primaire site opnieuw de verbinding met de centrale beheersite te maken op basis van het CASRetryInterval tot de WaitForCASTTimeout-periode is bereikt. U kunt een waarde opgeven van 0 tot 100.
