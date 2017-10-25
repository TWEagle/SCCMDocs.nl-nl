---
title: Maken van profielen voor externe verbindingen | Microsoft Docs
description: Gebruik profielen voor externe verbindingen van System Center Configuration Manager om uw gebruikers op afstand verbinding met werkcomputers.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c6eabc4-5dda-4682-b03e-3a450e6ef65a
caps.latest.revision: "8"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: d12faf657ca99dd572f1b28eb398783426fcdf8c
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2017
---
# <a name="remote-connection-profiles-in-system-center-configuration-manager"></a>Profielen voor externe verbindingen in System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Gebruik System Center Configuration Manager externe verbindingsprofielen kunnen uw gebruikers op afstand verbinding met werkcomputers wanneer ze niet zijn verbonden met het domein of als hun persoonlijke computers zijn verbonden via Internet.  

 Gebruikers kunnen verbinding maken met hun werk-pc vanaf de volgende typen apparaten:  

-   Computers met Microsoft Windows  

-   Apparaten met iOS  

-   Apparaten met Android  

Profielen voor externe verbindingen kunnen u instellingen voor verbinding met extern bureaublad implementeren voor gebruikers in uw Configuration Manager-hiërarchie. Gebruikers kunnen vervolgens de bedrijfsportal gebruiken om via het externe bureaublad toegang te krijgen tot een van hun primaire werkcomputers, op basis van de instellingen voor Verbinding met extern bureaublad van de bedrijfsportal.  

Microsoft Intune is vereist als u wilt dat gebruikers via de bedrijfsportal verbinding maken met hun werkcomputers. Als u Intune niet gebruikt, kunnen gebruikers de gegevens van het profiel voor externe verbindingen nog steeds gebruiken om via een VPN-verbinding met hun werkcomputers te maken met Extern bureaublad.  

> [!IMPORTANT]  
>  Wanneer u instellingen van profiel voor externe verbindingen opgeeft via de Configuration Manager-console, worden de instellingen opgeslagen in het lokale beleid van de clientcomputer. Deze instellingen overschrijven mogelijk de instellingen voor Extern bureaublad die zijn geconfigureerd door een andere toepassing. Bovendien, als u Windows-groepsbeleid gebruiken voor het configureren van instellingen voor extern bureaublad, de instellingen die zijn opgegeven in het groepsbeleid overschrijven die zijn geconfigureerd met behulp van Configuration Manager.  

 Tijdens de installatie van Configuration Manager, een nieuwe beveiligingsgroep **Remote PC Connect**, wordt gemaakt. Deze groep wordt gevuld wanneer u een profiel voor externe verbindingen implementeert dat de primaire gebruikers bevat van de computer waarop u het profiel implementeert. Hoewel een lokale beheerder gebruikersnamen kan toevoegen aan deze groep, worden deze verwijderd bij de volgende compatibiliteitsevaluatie van geïmplementeerde profielen voor externe verbindingen.  

 Als u handmatig een gebruiker toevoegt aan deze groep, kan de gebruiker externe verbindingen initiëren, maar de verbindingsgegevens worden niet gepubliceerd in de bedrijfsportal.  

 Als u handmatig uit de groep een gebruiker die is toegevoegd door Configuration Manager verwijderen, Configuration Manager worden automatisch hersteld door deze wijziging door de gebruiker toe te voegen als het profiel voor externe verbindingen is het volgende terug op compatibiliteit geëvalueerd.  

> [!IMPORTANT]  
>  Als de affiniteitsrelatie tussen een gebruiker en apparaat (bijvoorbeeld, de computer waarmee een gebruiker verbinding maakt niet meer een primair apparaat van de gebruiker, Configuration Manager wordt uitgeschakeld in het profiel voor externe verbindingen en Windows Firewall-instellingen verandert om te voorkomen dat de verbindingen met de computer.  

## <a name="prerequisites"></a>Vereisten  

### <a name="external-dependencies"></a>Externe afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Extern bureaublad-gatewayserver|Indien u gebruikers wilt inschakelen op het internet van buitenaf het bedrijfsdomein, moet u Extern bureaublad-gatewayserver installeren en configureren.<br /><br /> Indien Extern bureaublad of instellingen voor Terminal Services beheerd zijn door een andere toepassing of groepsbeleidinstellingen, kan het zijn dat externe verbindingsprofielen niet juist werken. Wanneer u externe verbindingsprofielen vanuit de Configuration Manager-console implementeert, worden zijn instellingen opgeslagen in het lokale beleid van de clientcomputer. Deze instellingen kunnen de instellingen van het extern bureaublad, die geconfigureerd zijn door een andere toepassing, overschrijven. Bijkomend, als u instellingen voor Groepsbeleid gebruikt om extern bureaublad-instellingen te configureren, overschrijven de instellingen die zijn opgegeven in de instellingen voor Groepsbeleid de instellingen die zijn geconfigureerd door Configuration Manager.<br /><br /> Voor meer informatie over hoe Extern bureaublad-gatewayserver te installeren en te configureren, zie de Windows Server-documentatie.|  
|Indien clientcomputers een op een host gebaseerde firewall uitvoeren, moeten ze het Mstsc.exe-programma inschakelen.|Wanneer u een extern verbindingsprofiel configureert, moet u de instelling **Windows Firewall-uitzondering toestaan voor verbindingen in Windows-domeinen en particuliere netwerken** inschakelen. Wanneer deze instelling is ingeschakeld, wordt Windows Firewall zodat het Mstsc.exe-programma automatisch geconfigureerd door Configuration Manager. Indien evenwel clientcomputers een andere, op een host gebaseerde, firewall uitvoeren, moet u handmatig deze firewall-afhankelijkheid configureren.<br /><br /> Met de groepsbeleidinstellingen voor het configureren van Windows Firewall kunt u de configuratie die u instelt in Configuration Manager overschrijven. Indien u groepsbeleid gebruikt om Windows Firewall te configureren, let er dan op dat groepsbeleidinstellingen het Mstsc.exe-programma niet blokkeren.|  

### <a name="configuration-manager-dependencies"></a>Configuration Manager-afhankelijkheden  

|Afhankelijkheid|Meer informatie|  
|----------------|----------------------|  
|Configuration Manager moet worden verbonden met Microsoft Intune (ook wel een hybride configuratie genoemd).|Zie voor meer informatie over het aansluiten van Configuration Manager op Microsoft Intune mobiele apparaten beheren met Configuration Manager en Microsoft Intune.|  
|Om een gebruiker te laten verbinding maken met een bedrijfscomputer, moet deze computer een primair apparaat zijn van de gebruiker.|Zie voor meer informatie over gebruikersapparaataffiniteit [gebruikers en apparaten koppelen met affiniteit tussen gebruikers en apparaten](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity).|  
|Specifieke beveiligingsmachtigingen moeten toegestaan zijn om externe verbindingsprofielen te beheren.|De beveiligingsrol **Beheerder van instellingen voor naleving** bevat de machtigingen die zijn vereist voor het beheren van externe verbindingsprofielen. Zie voor meer informatie. <br />[Beheer op basis van rollen configureren](/sccm/core/servers/deploy/configure/configure-role-based-administration).|  

## <a name="security-and-privacy-considerations-for-remote-connection-profiles"></a>Overwegingen voor beveiliging en privacy voor profielen voor externe verbindingen  

### <a name="security-considerations"></a>Beveiligingsoverwegingen  

|Aanbevolen beveiligingsprocedure|Meer informatie|  
|----------------------------|----------------------|  
|Geef handmatig de gebruikersaffiniteit met apparaat op in plaats van gebruikers toe te staan hun primaire apparaat te identificeren. Zorg daarnaast dat op gebruik gebaseerde configuratie niet is ingeschakeld.|Specificeer altijd handmatig de gebruikersaffiniteit van het apparaat, omdat u **Alle primaire gebruikers van de werkcomputer in staat stellen extern verbinding te maken** moet inschakelen vóór u een extern verbindingsprofiel kunt implementeren. Beschouw de informatie die verzameld wordt van gebruikers of van het apparaat niet als gezaghebbend. Indien u externe verbindingsprofielen implementeert en een vertrouwde gebruiker met beheerrechten geen gebruikersaffiniteit apparaat opgeeft, kunnen niet-bevoegde gebruikers hogere bevoegdheden krijgen en dan in staat zijn om met computers te verbinden.<br /><br /> Als u op gebruik gebaseerde configuratie inschakelt toch, wordt deze informatie verzameld via statusmeldingen waarvoor Configuration Manager geen beveiliging voorziet. Gebruik, om te helpen deze bedreiging af te zwakken, Server Message Block (SMB) ondertekening of Internet protocolbeveiliging (IPsec) tussen clientcomputers en het beheerpunt.|  
|Beperk lokale beheerrechten op de siteservercomputer.|Een gebruiker met lokale beheerdersrechten op de siteserver kan handmatig leden toevoegen aan de Remote PC Connect beveiligingsgroep die Configuration Manager automatisch maakt en onderhoudt. Dit kan een verhoging van bevoegdheden veroorzaken omdat leden die toegevoegd worden tot deze groep Extern bureaubladmachtigingen krijgen.|  

### <a name="privacy-considerations"></a>Privacyoverwegingen  

-   Indien een gebruiker een verbinding initieert naar een computer van het bedrijfsportaal, wordt een bestand met een .rdp- of .wsrdp-extensie gedownload, die de apparaatsnaam en de naam van de gatewayserver van het extern bureaublad bevat, die vereist is om de sessie met het extern bureaublad te initiëren. De bestandsextensie hangt af van het besturingssysteem van het apparaat. De Windows 7- en Windows 8-besturingssystemen maken gebruik van bijvoorbeeld een .rdp-bestand en Windows 8.1 maakt gebruik van een .wsrdp-bestand.  

-   De gebruiker kan kiezen om het .rdp-bestand te openen of op te slaan. Indien de gebruiker kiest om het .rdp-bestand te openen, kan het bestand worden opgeslagen in de cache voor de webbrowser, afhankelijk van de retentie-instellingen die geconfigureerd zijn voor de browser. Indien de gebruiker kiest om het bestand te bewaren, wordt het bestand niet opgeslagen in de browser-cache. Het bestand wordt opgeslagen, tenzij de gebruiker het handmatig verwijdert.  

-   Het bestand .wsrdp wordt gedownload en automatisch lokaal opgeslagen. Dit bestand wordt overschreven de volgende keer dat de gebruiker een sessie met een extern bureaublad uitvoert.  

-   Hou rekening met uw privacy-vereisten, voordat u profielen voor externe verbindingen configureert.  


## <a name="create-a-remote-connection-profile"></a>Een profiel voor externe verbinding maken

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **profielen voor externe verbinding**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Profiel voor externe verbinding maken**.  

4.  Geef op de pagina **Algemeen** van de **Wizard Profiel voor externe verbinding maken**een naam en optionele beschrijving van maximaal 256 tekens op voor elk profiel.  

5.  Op de **profiel** instellingenpagina van de volgende instellingen opgeven voor het profiel voor externe verbindingen:  

    -   **Volledige naam en poort van de Extern bureaublad-gatewayserver (optioneel):** : geef de naam op van de Extern bureaublad-gatewayserver die moet worden gebruikt voor verbindingen.  

        > [!NOTE]  
        >  Configuration Manager biedt geen ondersteuning voor een geïnternationaliseerde domeinnaam moet worden gebruikt om op te geven van een server in dit vak.  
        >   
        >  De servernaam mag niet langer zijn dan 256 tekens en mag bestaan uit hoofdletters, kleine letters, numerieke tekens en de tekens **–** en **_** , die met punten worden gescheiden.  

    -   **Alleen verbindingen toestaan vanaf computers waarop Extern bureaublad wordt uitgevoerd met verificatie op netwerkniveau**  

6.  Selecteer **Ingeschakeld** of **Uitgeschakeld** voor elk van de volgende verbindingsinstellingen:  

    -   **Externe verbindingen met werkcomputers toestaan**  

    -   **Alle primaire gebruikers van de werkcomputer toestaan om extern verbinding te maken**  

    -   **Windows Firewall-uitzondering toestaan voor verbindingen in Windows-domeinen en in particuliere netwerken**  

    > [!IMPORTANT]  
    >  Alle drie de instellingen moeten hetzelfde zijn voordat u kunt doorgaan met de volgende pagina van de wizard.  

7.  Op de **samenvatting** pagina, controleert u de acties worden ondernomen en voltooi de wizard.  

 Het nieuwe profiel voor externe verbinding wordt weergegeven in het knooppunt **Profielen voor externe verbinding** van de werkruimte **Activa en naleving** .  

Een profiel voor externe verbinding implementeren  

1.  Klik in de Configuration Manager-console op **activa en naleving** > **instellingen voor naleving** > **profielen voor externe verbinding**.  

3.  Selecteer in de lijst **Profielen voor externe verbinding** het profiel voor externe verbinding dat u wilt implementeren en klik vervolgens op het tabblad **Start** in de groep **Implementatie** op **Implementeren**.  

4.  Geef de volgende informatie op in het dialoogvenster **Profiel voor externe verbinding implementeren** :  

    -   **Verzameling** - Klik op **Bladeren** om de apparaatverzameling te selecteren waar u het profiel voor externe verbinding wilt implementeren.  

    -   **Herstellen, waar ondersteund** -Schakel deze optie in het profiel voor externe verbinding automatisch herstellen wanneer blijkt dat het niet compatibel is op een apparaat, bijvoorbeeld wanneer het is niet aanwezig is.  

    -   **Herstel toestaan buiten het onderhoudsvenster** - als een onderhoudsvenster is geconfigureerd voor de verzameling waarnaar u het profiel voor externe verbinding implementeert, schakel deze optie om Configuration Manager oplossen van het profiel voor externe verbindingen buiten het onderhoudsvenster. Zie voor meer informatie over onderhoudsvensters [het gebruik van onderhoudsvensters](/sccm/core/clients/manage/collections/use-maintenance-windows).  

    -   **Waarschuwing genereren** - Schakel deze optie in om een waarschuwing te configureren die wordt gegenereerd als de compatibiliteit van een profiel voor externe verbinding op een opgegeven datum en tijd minder is dan een opgegeven percentage. U kunt tevens opgeven of u een melding naar System Center Operations Manager wilt verzenden.  

    -   **Specificeer de compliantie-evaluatieplanning voor deze configuratiebasislijn** : geef de planning op waarmee het geïmplementeerde profiel voor externe verbindingen wordt beoordeeld op apparaten. U kunt een eenvoudige of een aangepaste planning opgeven.  

    > [!TIP]  
    >  Als een apparaat wordt verwijderd uit een verzameling waarnaar een profiel voor externe verbinding is geïmplementeerd, worden de instellingen van het profiel voor externe verbinding uitgeschakeld op het apparaat. Dit proces kan echter alleen correct plaatsvinden als u al minstens één configuratie-item of configuratiebasislijn hebt geïmplementeerd die een configuratie-item van uw site bevat.  
    >   
    >  Het profiel wordt beoordeeld door apparaten wanneer de gebruiker zich aanmeldt.  
    >   
    >  Als twee profielen voor externe verbindingen worden geïmplementeerd in dezelfde apparaatverzameling, waarbij in het ene profiel **Regels die niet compliant zijn herstellen, waar ondersteund** is ingeschakeld en in het andere profiel dezelfde optie is uitgeschakeld, en de twee profielen voor externe verbindingen verschillende verbindingsinstellingen bevatten, overschrijft het profiel waarin de optie is uitgeschakeld, mogelijk de instellingen in het andere profiel. Dit type implementatie van een verbinding met extern profiel wordt niet ondersteund door Configuration Manager.  

5.  Klik op **OK** om het dialoogvenster **Profiel voor externe verbinding implementeren** te sluiten en de implementatie uit te voeren.  

## <a name="monitor-a-remote-connection-profile"></a>Een profiel voor externe verbindingen bewaken  

### <a name="view-compliance-results-in-the-configuration-manager-console"></a>Nalevingsresultaten weergeven in de Configuration Manager-console  

1.  Klik in de Configuration Manager-console op **bewaking** > **implementaties**.  

3.  Selecteer in de lijst **Implementaties** de implementatie van het profiel voor externe verbindingen waarvoor u compatibiliteitsinformatie wilt bekijken.  

4.  U kunt samenvattingsgegevens over de compatibiliteit van de implementatie van het profiel voor externe verbindingen bekijken op de hoofdpagina. Als u meer gedetailleerde gegevens wilt weergeven, selecteert u de implementatie van het profiel voor externe verbindingen en klikt u op het tabblad **Start** in de groep **Implementatie** op **Status weergeven** om de pagina **Implementatiestatus** te openen.  

     De pagina **Implementatiestatus** bevat de volgende tabbladen:  

    -   **Compatibel:** Geeft de naleving van het profiel voor externe verbindingen op basis van het aantal activa dat is beïnvloed. U kunt op een regel dubbelklikken om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** in de werkruimte **Activa en naleving** . Dit knooppunt bevat alle apparaten die compatibel zijn met het profiel voor externe verbindingen. In het deelvenster **Activumgegevens** worden daarnaast de apparaten weergegeven die compatibel zijn met dit profiel. Dubbelklik op een apparaat in de lijst om extra informatie weer te geven.  

        > [!IMPORTANT]  
        >  Een profiel voor externe verbindingen wordt niet geëvalueerd als het niet van toepassing is op een clientapparaat. Het wordt in dat geval echter wel geretourneerd als compatibel.  

    -   **Fout:** Geeft een lijst met alle fouten voor de implementatie van het geselecteerde verbinding met extern-profiel op basis van het aantal activa dat is beïnvloed. U kunt dubbelklikken op een regel om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** van de werkruimte **Activa en naleving** . Dit knooppunt bevat alle apparaten waarvoor fouten zijn gegenereerd met dit profiel. Wanneer u een apparaat selecteert, worden in het deelvenster **Activumgegevens** de apparaten weergegeven waarop het geselecteerde probleem van invloed is. Dubbelklik op een apparaat in de lijst om extra informatie over het probleem weer te geven.  

    -   **Niet-compatibele:** Geeft een lijst met alle niet-compatibele regels binnen het profiel voor externe verbindingen op basis van het aantal activa dat is beïnvloed. U kunt dubbelklikken op een regel om een tijdelijk knooppunt te maken onder het knooppunt **Gebruikers** van de werkruimte **Activa en naleving** . Dit knooppunt bevat alle apparaten die niet compatibel zijn met dit profiel. Wanneer u een apparaat selecteert, worden in het deelvenster **Activumgegevens** de apparaten weergegeven waarop het geselecteerde probleem van invloed is. Dubbelklik op een apparaat in de lijst om extra informatie over het probleem weer te geven.  

    -   **Onbekend:** Geeft een lijst van alle apparaten waarop geen compatibiliteitsstatus is gerapporteerd voor de geselecteerde implementatie externe verbindingen profiel, samen met de huidige clientstatus van apparaten.  

5.  Op de pagina **Implementatiestatus** kunt u gedetailleerde informatie over de compatibiliteit van het geïmplementeerde profiel voor externe verbindingen weergeven. Een tijdelijk knooppunt wordt gemaakt onder het knooppunt **Implementaties** waarmee u deze informatie snel kunt terugvinden.  

### <a name="view-compliance-results-with-reports"></a>Nalevingsresultaten weergeven met rapporten  
 Configuration Manager bevat ingebouwde rapporten die u gebruiken kunt om gegevens over profielen voor externe verbindingen te controleren. Deze rapporten hebben de rapportcategorie van **Compatibiliteit en instellingen beheren**.  

> [!IMPORTANT]  
>  U moet een jokerteken (%) gebruiken wanneer u de parameters **Apparaatfilter** en **Gebruikersfilter** gebruikt in de rapporten voor compatibiliteitsinstellingen.  

 Zie voor meer informatie over het configureren van rapportage in Configuration Manager [rapportage in System Center Configuration Manager](/sccm/core/servers/manage/reporting).  
