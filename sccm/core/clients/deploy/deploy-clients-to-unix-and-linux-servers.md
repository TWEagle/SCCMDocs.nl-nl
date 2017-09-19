---
title: UNIX/Linux-clients implementeren | Microsoft Docs
description: Informatie over het implementeren van een client op een UNIX- of Linux-server in System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 15a4e323-9f42-4fea-bb14-f2b905d1f77c
caps.latest.revision: "9"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 1741506f390430c85dab9a5b8e8cc26dda7b57e3
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-deploy-clients-to-unix-and-linux-servers-in-system-center-configuration-manager"></a>Clients implementeren op UNIX- en Linux-servers in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Voordat u een Linux- of UNIX-server met System Center Configuration Manager beheren kunt, moet u de Configuration Manager-client voor Linux en UNIX installeren op elke Linux- of UNIX-server. U kunt de installatie van de client handmatig op elke computer uitvoeren of een shell-script gebruiken waarmee de client op afstand wordt geïnstalleerd. Configuration Manager biedt geen ondersteuning voor het gebruik van de push-clientinstallatie voor Linux of UNIX-servers. U kunt eventueel een runbook voor System Center Orchestrator configureren om de installatie van de client op de Linux-of UNIX-server te automatiseren.  

 Welke installatiemethode u ook gebruikt, het installatieproces vereist het gebruik van een script met de naam **install** om het installatieproces te beheren. Dit script is opgenomen in de download voor de client voor Linux en UNIX.  

 Het installatiescript voor de Configuration Manager-client voor Linux en UNIX ondersteunt opdrachtregeleigenschappen. Bepaalde opdrachtregeleigenschappen zijn vereist, terwijl andere optioneel zijn. Als u bijvoorbeeld de client installeert, moet u een beheerpunt opgeven via de site die door de Linux- of UNIX-server wordt gebruikt voor het eerste contact met de site. Zie [Eigenschappen van de opdrachtregel voor het installeren van de Client op Linux- en UNIX-Servers](#BKMK_CmdLineInstallLnUClient)voor de volledige lijst met opdrachtregeleigenschappen.  

 Nadat u de client hebt geïnstalleerd, kunt u clientinstellingen opgeven in de Configuration Manager-console voor het configureren van de clientagent op dezelfde manier als die u Windows gebaseerde clients zou doen. Zie [Clientinstellingen voor Linux- en UNIX-servers](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ClientSettingsforLnU) voor meer informatie.  

##  <a name="BKMK_AboutInstallPackages"></a> Over clientinstallatiepakketten en de universele agent  
 Als u de client voor Linux en UNIX op een bepaald platform wilt installeren, moet u het desbetreffende clientinstallatiepakket gebruiken voor de computer waarop u de client installeert. Elke clientdownload uit het [Microsoft Downloadcentrum](http://go.microsoft.com/fwlink/?LinkID=525184)bevat de betreffende clientinstallatiepakketten. Naast de clientinstallatiepakketten bevat de clientdownload het **installatie** script waarmee de installatie van de client op elke computer wordt beheerd.  

 Wanneer u een client installeert, kunt u dezelfde eigenschappen voor het proces en de opdrachtregel gebruiken, ongeacht welk clientinstallatiepakket u gebruikt.  

 Zie voor informatie over de besturingssystemen, platforms en clientinstallatiepakketten die door elke release van Configuration Manager-client voor Linux en UNIX worden ondersteund, [Linux en UNIX-servers](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#linux-and-unix-servers).  

##  <a name="BKMK_InstallLnUClient"></a> De client op Linux- en UNIX-servers installeren  
 Als u de client voor Linux en UNIX wilt installeren, voert u op elke Linux- of UNIX-computer een script uit. Het script heeft de naam **install** en ondersteunt opdrachtregeleigenschappen die het installatiegedrag wijzigen en verwijzen naar het clientinstallatiepakket. Het installatiescript en clientinstallatiepakket moeten zich op de client bevinden. Het clientinstallatiepakket bevat de bestanden van de Configuration Manager-client voor een specifiek Linux of UNIX-besturingssysteem en platform.
Elk clientinstallatiepakket bevat alle benodigde bestanden om de clientinstallatie te voltooien en downloadt, in tegenstelling tot Windows-computers, geen aanvullende bestanden van een beheerpunt of andere bronlocatie.  

 Nadat u de Configuration Manager-client voor Linux en UNIX installeert, hoeft u niet de computer opnieuw opstarten. Zodra de software-installatie is voltooid, is de client operationeel. Als u de computer opnieuw opstart, wordt de Configuration Manager-client automatisch opnieuw gestart.  

 De geïnstalleerde client wordt uitgevoerd met hoofdreferenties. Hoofdreferenties zijn vereist om de hardware-inventaris te verzamelen en software-implementaties uit te voeren.  

 De opdracht heeft de volgende notatie:  

 **. / -mp installeren &lt;computer\> - sitecode &lt;sitecode\> &lt;eigenschap #1 > &lt;eigenschap #2 > &lt;clientinstallatiepakket\>**  

-   **install** is de naam van het scriptbestand waarmee de client voor Linux en UNIX wordt geïnstalleerd. Dit bestand wordt geleverd bij de clientsoftware.  

-   **-mp &lt;computer** specificeert het initiële beheerpunt dat wordt gebruikt door de client.  

     Voorbeeld: smsmp.contoso.com  

-   **-sitecode &lt;sitecode\> ** geeft de sitecode die de client is toegewezen aan.  

     Voorbeeld: S01  

-   &lt;eigenschap #1 > &lt;eigenschap #2 > Hiermee geeft u aan de opdrachtregeleigenschappen gebruiken met het script voor installatie.  

    > [!NOTE]  
    >  Zie [Eigenschappen van de opdrachtregel voor het installeren van de Client op Linux- en UNIX-Servers](#BKMK_CmdLineInstallLnUClient)voor meer informatie  

-   **clientinstallatiepakket** is de naam van het TAR-clientinstallatiepakket voor het besturingssysteem, de versie en de CPU-architectuur van deze computer. Het TAR-bestand voor de clientinstallatie moet als laatste worden opgegeven.  

     Voorbeeld: ccm-Universal-x64. &lt;bouwen\>tar  

###  <a name="BKMK_ToInstallLnUClinent"></a> De Configuration Manager-client installeren op Linux- en UNIX-servers  

1.  Op een Windows-computer: [download het betreffende clientbestand voor de Linux- of UNIX-server](http://go.microsoft.com/fwlink/?LinkID=525184) die u wilt beheren.  

2.  Voer het zelfuitpakkende .exe-bestand uit op de Windows-computer om het installatiescript en het .tar-bestand voor de clientinstallatie uit te pakken.  

3.  Kopieer het **installatie** script en het .tar-bestand naar een map op de server die u wilt beheren.  

4.  Voer op de UNIX- of Linux-server de volgende opdracht uit om het script uit te voeren als een programma: **chmod +x install**  

    > [!IMPORTANT]  
    >  U moet hoofdreferenties gebruiken om de client te installeren.  

5.  Voer vervolgens de volgende opdracht om de Configuration Manager-client te installeren: **. / -mp installeren &lt;hostnaam\> - sitecode &lt;code\> ccm-Universal-x64.&lt; bouwen\>tar**  

     Wanneer u deze opdracht opgeeft, gebruikt u aanvullende opdrachtregeleigenschappen die u nodig hebt.  Zie [Eigenschappen van de opdrachtregel voor het installeren van de Client op Linux- en UNIX-Servers](#BKMK_CmdLineInstallLnUClient)voor de lijst van opdrachtregeleigenschappen.  

6.  Nadat het script is uitgevoerd, valideert u de installatie door het bestand **/var/opt/microsoft/scxcm.log** te controleren. Bovendien kunt u bevestigen dat de client is geïnstalleerd en communiceert met de site door details weergeven voor de client in de **apparaten** knooppunt van de **activa en naleving** werkruimte in de Configuration Manager-console.  

###  <a name="BKMK_CmdLineInstallLnUClient"></a> Eigenschappen van de opdrachtregel voor het installeren van de Client op Linux- en UNIX-Servers  
 De volgende eigenschappen zijn beschikbaar voor het aanpassen van het gedrag van het installatiescript:  

> [!NOTE]  
>  Gebruik de eigenschap **-h** om deze lijst met ondersteunde eigenschappen weer te geven.  

-   **-mp &lt;FQDN-naam server\>**  

     Vereist. Hiermee geeft u met de FQDN-naam de beheerpuntserver op die door de client wordt gebruikt als een eerste contactpunt.  

    > [!IMPORTANT]  
    >  Deze eigenschap specificeert niet het beheerpunt waaraan de client na de installatie wordt toegewezen.  

    > [!NOTE]  
    >  Wanneer u de eigenschap **-mp** gebruikt om een beheerpunt op te geven die alleen HTTPS-clientverbindingen accepteert, dient u ook de eigenschap **-UsePKICert** te gebruiken.  

-   **-sitecode &lt;sitecode\>**  

     Vereist. Hiermee geeft u de primaire site van Configuration Manager als u wilt toewijzen aan Configuration Manager-client.  

     Voorbeeld: -sitecode S01  

-   **-fsp &lt;server_FQDN >**  

     Optioneel. Hiermee geeft u met FQDN-naam de server van het terugvalstatuspunt op dat door de client wordt gebruikt om statusberichten te verzenden.  

     Zie [Bepalen of u een terugvalstatuspunt nodig hebt](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients#determine-if-you-need-a-fallback-status-point) voor meer informatie over het terugvalstatuspunt.  


-   **-dir &lt;directory\>**  

     Optioneel. Hiermee geeft u een alternatieve locatie voor het installeren van de bestanden van de Configuration Manager-client.  

     De client installeert de bestanden standaard op de volgende locatie: **/opt/microsoft**.  

-   **-nostart**  

     Optioneel. Voorkomt dat het automatisch starten van de Configuration Manager clientservice, **ccmexec.bin**, nadat de installatie van de client is voltooid.  

     Nadat de client is geïnstalleerd, moet u de clientservice handmatig starten.  

     Standaard wordt de clientservice gestart nadat de clientinstallatie is voltooid en telkens wanneer de computer opnieuw wordt opgestart.  

-   **-clean**  

     Optioneel. Hiermee geeft u aan dat alle clientbestanden en -gegevens van een eerder geïnstalleerde client voor Linux en UNIX moeten worden verwijderd voordat de nieuwe installatie wordt gestart. Hiermee verwijdert u de database van de client en het certificaatarchief.  

-   **-keepdb**  

     Optioneel. Hiermee geeft u aan dat u de lokale clientdatabase wilt behouden en wilt gebruiken wanneer u een client opnieuw installeert. Standaard wordt deze database verwijderd wanneer u een client opnieuw installeert.  

-   **-UsePKICert &lt;parameter\>**  

     Optioneel. Hiermee geeft u het volledige pad naar en de bestandsnaam van een X.509 PKI-certificaat in de PKCS#12-notatie (Public Key Certificate Standard) op. Dit certificaat word gebruikt om de client te verifiëren. Als er tijdens de installatie geen certificaat is opgegeven en u een certificaat moet toevoegen of wijzigen, gebruikt u het hulpprogramma **certutil** . Zie [Certificaten beheren op de client voor Linux en UNIX](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts) voor informatie over certutil.  

     Als u **-UsePKICert**gebruikt, dient u de opdrachtregelparameter **-certpw** te gebruiken om het wachtwoord op te geven dat aan het PKCS#12-bestand is gekoppeld.  

     Als u deze eigenschap niet gebruikt om een PKI-certificaat op te geven, gebruikt de client een zelfondertekend certificaat en vindt alle communicatie naar sitesystemen plaats via HTTP.  

     Als u een ongeldig certificaat opgeeft op de opdrachtregel voor het installeren van de client, worden er geen fouten geretourneerd. Dit komt doordat het certificaat pas wordt gevalideerd nadat de client is geïnstalleerd. Wanneer de client wordt gestart, certificaten worden gevalideerd met het beheerpunt en als een certificaat niet kan worden gevalideerd door het volgende bericht wordt weergegeven in **scxcm.log**, het logboekbestand Unix en Linux Configuration Manager-client: **Kan het certificaat voor beheerpunt valideren**. De standaardlocatie van het logboek is  **/var/opt/microsoft/scxcm.log**.  

    > [!NOTE]  
    >  U moet deze eigenschap opgeven wanneer u een client installeert en de eigenschap **-mp** gebruikt om een beheerpunt op te geven dat zodanig is geconfigureerd dat alleen HTTPS-clientverbindingen worden geaccepteerd.  

     Voorbeeld: - UsePKICert &lt;volledige pad en bestandsnaam\> - certpw &lt;wachtwoord\>  

-   **-certpw &lt;parameter\>**  

     Optioneel. Hiermee geeft u het wachtwoord op dat is gekoppeld aan het PKCS #12-bestand dat u hebt opgegeven met de eigenschap **- UsePKICert** .  

     Voorbeeld: - UsePKICert &lt;volledige pad en bestandsnaam\> - certpw &lt;wachtwoord\>  

-   **-NoCRLCheck**  

     Optioneel. Hiermee geeft u aan dat een client de certificaatintrekkingslijst (CRL) niet moet controleren wanneer deze middels een PKI-certificaat via HTTPS communiceert. Als deze optie niet is opgegeven, controleert de client de CRL voordat er een HTTPS-verbinding via PKI-certificaten wordt gemaakt. Zie 'Planning voor PKI-certificaatintrekking' voor meer informatie over de CRL-controle voor clients.  

     Voorbeeld: - UsePKICert &lt;volledige pad en bestandsnaam\> - certpw &lt;wachtwoord\> - NoCRLCheck  

-   **-rootkeypath &lt;bestandslocatie\>**  

     Optioneel. Hiermee geeft u het volledige pad en bestandsnaam van de vertrouwde basissleutel van Configuration Manager. De Configuration Manager vertrouwde basissleutel biedt een mechanisme die Linux en UNIX-clients gebruiken om te controleren of ze zijn verbonden met een sitesysteem dat de juiste hiërarchie hoort.  

     Als u geen vertrouwde basissleutel opgeeft op de opdrachtregel, vertrouwt de client het eerste beheerpunt waarmee wordt gecommuniceerd en wordt automatisch de vertrouwde basissleutel opgehaald van dat beheerpunt.  

     Zie [Planning voor de vertrouwde basissleutel](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) voor meer informatie.  

     Voorbeeld: - rootkeypath &lt;volledige pad en bestandsnaam\>  

-   **-httpport &lt;poort\>**  

     Optioneel. Hiermee geeft u de poort op die is geconfigureerd op beheerpunten die de client gebruikt voor de communicatie met beheerpunten via HTTP. Als er geen poort is opgegeven, wordt de standaardwaarde 80 gebruikt.  

     Voorbeeld: -httpport 80  

-   **-httpsport &lt;poort\>**  

     Optioneel. Hiermee geeft u de poort op die is geconfigureerd op beheerpunten die de client gebruikt voor de communicatie met beheerpunten via HTTPS. Als er geen poort is opgegeven, wordt de standaardwaarde 443 gebruikt.  

     Voorbeeld: - UsePKICert &lt;volledige pad en de certificaat-naam\> - httpsport 443  

-   **-ignoreSHA256validation**  

     Optioneel. Hiermee geeft u op dat de clientinstallatie de SHA-256-validatie overslaat. Gebruik deze optie wanneer u de client installeert op besturingssystemen die zijn gepubliceerd zonder een versie van OpenSSL met ondersteuning voor SHA-256. Zie [Informatie over Linux- en UNIX besturingssystemen zonder ondersteuning voor SHA-256](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_NoSHA-256) voor meer informatie.  

-   **-signcertpath &lt;bestandslocatie\>**  

     Optioneel. Geeft het volledige pad en de **CER** -bestandsnaam van het geëxporteerde zelfondertekende certificaat op de siteserver. Als u geen PKI-certificaten beschikbaar zijn, genereert de Configuration Manager-siteserver automatisch zelfondertekende certificaten.  

     Deze certificaten worden gebruikt om te valideren dat het clientbeleid dat via het beheerpunt is gedownload, is verzonden vanaf de gewenste site. Als er tijdens de installatie geen zelfondertekend bestand is opgegeven of u het certificaat moet wijzigen, gebruikt u het hulpprogramma **certutil** . Zie [Certificaten beheren op de client voor Linux en UNIX](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts) voor informatie over certutil.  

     Dit certificaat kan worden opgehaald via het **SMS** -certificaatarchief en heeft de objectnaam **Site Server** en de beschrijvende naam **Site Server Signing Certificate**.  

     Als deze optie niet tijdens de installatie wordt opgegeven, vertrouwen Linux- en UNIX-clients het eerste beheerpunt waarmee ze communiceren en halen ze automatisch het handtekeningcertificaat van dit beheerpunt op.  

     Voorbeeld: - signcertpath &lt;volledig pad en de naam\>  

-   **-rootcerts**  

     Optioneel. Hiermee geeft u aan welke aanvullende PKI-certificaten moeten worden geïmporteerd die geen deel uitmaken van de CA-hiërarchie (certificeringsinstantie) van het beheerpunt. Als u meerdere certificaten op de opdrachtregel opgeeft, moeten ze worden gescheiden door komma's.  

     Gebruik deze optie als u PKI-clientcertificaten gebruikt die niet zijn gekoppeld aan het basis-CA-certificaat dat door de beheerpunten van uw sites wordt vertrouwd. Beheerpunten zullen de client weigeren als het clientcertificaat niet is gekoppeld aan een vertrouwd basiscertificaat in de lijst met certificaatverleners van de site.  

     Als u deze optie niet gebruikt, zal de client voor Linux en UNIX de vertrouwenshiërarchie alleen verifiëren met het certificaat in de optie **-UsePKICert** .  

     Voorbeeld: - rootcerts &lt;volledig pad en de naam\>,&lt;volledig pad en de naam\>  

###  <a name="BKMK_UninstallLnUClient"></a> De client van Linux- en UNIX-servers verwijderen  
 Verwijderen van Configuration Manager-client voor Linux en UNIX gebruikt van het hulpprogramma verwijderen **verwijderen**. Dit bestand bevindt zich standaard in de map **/opt/microsoft/configmgr/bin/** op de clientcomputer. Deze opdrachtregel voor verwijderen ondersteunt geen opdrachtregelparameters en verwijdert alle bestanden met betrekking tot de clientsoftware van de server.  

 Als u de client wilt verwijderen, gebruikt u de volgende opdrachtregel: **/opt/microsoft/configmgr/bin/uninstall**  

 U beschikt niet over de computer opnieuw opstarten na het verwijderen van Configuration Manager-client voor Linux en UNIX.  

##  <a name="BKMK_ConfigLnUClientCommuincations"></a> Aanvraagpoorten configureren voor de client voor Linux en UNIX  
 Net zoals bij op basis van Windows-clients, Configuration Manager-client voor Linux en UNIX gebruikt HTTP en HTTPS om te communiceren met sitesystemen van Configuration Manager. De poorten die Configuration Manager-client gebruikt om te communiceren, worden een aanvraagpoorten genoemd.  

 Wanneer u de Configuration Manager-client voor Linux en UNIX installeert, kunt u de standaardaanvraagpoorten wijzigen door op te geven de **- httpport** en **- httpsport** installatie-eigenschappen. Als u geen installatie-eigenschap en aangepaste waarde opgeeft, gebruikt de client de standaardwaarden. De standaardwaarde voor HTTP-verkeer is **80** en de standaardwaarde voor HTTPS-verkeer is **443** .  

 Nadat u de client hebt geïnstalleerd, kunt u de configuratie van de aanvraagpoort niet meer wijzigen. Als u de poortconfiguratie wilt wijzigen, moet u de client opnieuw installeren en de nieuwe poortconfiguratie opgeven. Wanneer u de client opnieuw installeert om de aanvraagpoortnummers te wijzigen, voert u de opdracht **install** uit, op dezelfde manier als voor de nieuwe clientinstallatie, maar gebruikt u de aanvullende opdrachtregeleigenschap **-keepdb**. Met deze schakeloptie geeft u aan dat de clientdatabase en -bestanden moeten worden behouden tijdens de installatie, inclusief de GUID en het certificaatarchief van de client.  

 Zie [Clientcommunicatiepoorten in System Center Configuration Manager configureren](../../../core/clients/deploy/configure-client-communication-ports.md) voor informatie over poortnummers voor clientcommunicatie.  

##  <a name="BKMK_ConfigClientMP"></a> De client voor Linux en UNIX configureren om beheerpunten te zoeken  
 Wanneer u de Configuration Manager-client voor Linux en UNIX installeert, moet u een beheerpunt om te gebruiken als een eerste contactpunt.  

 Configuration Manager-client voor Linux en UNIX maakt contact met dit beheerpunt op het moment dat de client is geïnstalleerd. Als de client geen contact kan maken met het beheerpunt, blijft de clientsoftware opnieuw proberen totdat er contact is gemaakt.  

 Zie [Zoeken naar beheerpunten](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points) voor meer informatie over hoe clients beheerpunten zoeken.
