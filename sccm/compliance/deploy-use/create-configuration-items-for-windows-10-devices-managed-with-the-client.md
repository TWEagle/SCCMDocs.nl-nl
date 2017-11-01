---
title: 'Configuratie-items maken voor Windows 10-client worden beheerd '
titleSuffix: Configuration Manager
description: Gebruik het configuratie-item voor System Center Configuration Manager Windows 10 om instellingen voor Windows 10-computers die worden beheerd door Configuration Manager-client te beheren.
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14226fbe-dd07-4432-910b-130790624a4e
caps.latest.revision: "17"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 4f22ab22ec666c55962231bf92a42b25c4a7c127
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-create-configuration-items-for-windows-10-devices-managed-with-the-system-center-configuration-manager-client"></a>Het maken van configuratie-items voor Windows 10-apparaten die worden beheerd door System Center Configuration Manager-Client
De System Center Configuration Manager gebruiken **Windows 10** configuratie-item voor het beheren van instellingen voor Windows 10-computers die worden beheerd door Configuration Manager-client.  
  
> [!IMPORTANT]  
>  In deze release, als u hebt gemaakt een **wachtwoord** instellen als onderdeel van een configuratie-item van het type **Windows 10** (voor een apparaat beheerd met de Configuration Manager-client), klikt u vervolgens als de instelling niet bestaat nog of is niet geconfigureerd op het Windows 10-apparaat, het wordt ten onrechte geëvalueerd als compliant.  
>   
>  Wanneer u een instelling voor deze apparaten maakt, kunt u er als tijdelijke oplossing voor zorgen dat **Niet-compliante instellingen herstellen** is geselecteerd op de pagina's met instellingen van de wizard Configuratie-item maken. Wanneer u een configuratiebasislijn met een Windows 10-configuratie-item met wachtwoordinstellingen implementeert, selecteert u **Regels die niet compliant zijn herstellen, waar ondersteund** in het dialoogvenster Configuratiebasislijnen implementeren. Met deze tijdelijke oplossing wordt de instelling bewaakt en zo nodig hersteld. Na het herstellen wordt de instelling correct gerapporteerd als **Compatibel** (tenzij er een probleem is opgetreden; in dat geval wordt de instelling gerapporteerd als **Fout**).  
  
### <a name="to-create-a-windows-10-configuration-item"></a>Een Windows 10-configuratie-item maken  
  
1.  Klik op **Activa en naleving**op de Configuration Manager-console.  
  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  
  
3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  
  
4.  Geef op de pagina **Algemeen** van de wizard **Configuratie-item maken**een naam en een optionele beschrijving voor het configuratie-item op.  
  
5.  Selecteer onder **Geef het type configuratie-item op dat u wilt maken**de optie **Windows 10**.  
  
6.  Klik op **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  
  
7.  Selecteer op de pagina **Ondersteunde platforms** van de wizard de specifieke Windows 10-platforms die het configuratie-item evalueren.  
  
8.  Op de pagina **Apparaatinstellingen** van de wizard selecteert u de instellingengroep die u wilt configureren. Zie [Windows 10 configuration item settings reference](#BKMK_Ref) in dit onderwerp voor meer informatie en klik vervolgens op **Volgende**.  
  
    > [!TIP]  
    >  Als de gewenste instelling niet wordt weergegeven, schakelt u het selectievakje **Extra instellingen configureren die niet zijn opgenomen in de standaardinstellingsgroepen**in.  
  
9. Op elke instellingenpagina configureert u de instellingen die u nodig hebt en geeft u aan of u deze wilt corrigeren wanneer ze niet compliant zijn op apparaten (wanneer dit wordt ondersteund).  
  
10. U kunt voor elke instellingengroep ook de ernst configureren die wordt gerapporteerd als wordt geconstateerd dat een configuratie-item niet compliant is:  
  
    -   **Geen** -apparaten die niet voldoen aan deze compliantieregel niet rapporteren ernst voor Configuration Manager-rapporten.  
  
    -   **Informatie** -apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
    -   **Waarschuwing** -apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
    -   **Kritieke** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
    -   **Kritiek met gebeurtenis** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  
  
11. Op de pagina **Platformtoepasbaarheid** van de wizard controleert u alle instellingen die niet compatibel zijn met de ondersteunde platforms die u eerder hebt geselecteerd. U kunt teruggaan en deze instellingen verwijderen of u kunt doorgaan.  
  
    > [!TIP]  
    >  Niet-ondersteunde instellingen worden niet beoordeeld op compliantie.  
  
12. Voltooi de wizard.  
  
 U kunt het nieuwe configuratie-item weergeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving** .  
  
##  <a name="windows-10-configuration-item-settings-reference"></a>Naslaginformatie voor Windows 10-configuratie-item  
  
### <a name="password"></a>Wachtwoord  
  
|Instelling|Details|  
|-------------|-------------|  
|**Wachtwoordinstellingen vereisen op mobiele apparaten**|Hiermee vereist u een wachtwoord op ondersteunde apparaten.|  
|**Minimale wachtwoordlengte (tekens)**|Het minimum aantal tekens voor het wachtwoord.|  
|**Wachtwoordverlooptijd in dagen**|Het aantal dagen voordat het wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Hiermee voorkomt u dat eerder gebruikte wachtwoorden opnieuw worden gebruikt.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Hiermee worden de gegevens op het apparaat gewist als het aanmelden dit aantal keren mislukt.|  
|**Niet-actieve periode waarna apparaat wordt vergrendeld**|Hier geeft u op hoeveel minuten het apparaat inactief moet zijn voordat het automatisch wordt vergrendeld.|  
|**Wachtwoordcomplexiteit**|Hiermee kunt u opgeven of u een pincode, zoals '1234', wilt gebruiken of dat er een sterk wachtwoord moet worden opgegeven.|
|**Aantal complexe tekens vereist in wachtwoord ingesteld**|Als u hebt geselecteerd een **sterke** wachtwoorden en gebruik deze instelling voor het configureren van het aantal complexe tekens vereist. Voor een sterk wachtwoord; dit moet worden ingesteld op ten minste **3** wat betekent dat zowel letters en cijfers zijn vereist. Selecteer **4** als u wilt afdwingen van een wachtwoord dat ook speciale tekens bevatten zoals vereist **(% $**.<br>(Alleen Windows 10)  |
  
###  <a name="device"></a>Apparaat  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Bluetooth**|Staat het gebruik van de Bluetooth-functie op het apparaat toe.|  
  
### <a name="cloud"></a>Cloud  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Synchronisatie van instellingen**|De synchronisatie van instellingen tussen apparaten toestaan.|  
|**Synchronisatie van referenties**|De synchronisatie van referenties tussen apparaten toestaan.|  
|**Synchronisatie van instellingen via verbindingen met een datalimiet**|Toestaan dat instellingen worden gesynchroniseerd wanneer er voor de internetverbinding een datalimiet geldt.|  
  
### <a name="roaming"></a>Roaming  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Gegevensroaming**|Roaming tussen netwerken toestaan tijdens het ophalen van gegevens.|  
  
### <a name="encryption"></a>Versleuteling  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Bestandsversleuteling op apparaat**|Vereist dat bestanden op het apparaat zijn versleuteld.|  
  
### <a name="system-security"></a>Systeembeveiliging  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Gebruikersaccountbeheer**|Hiermee configureert u hoe Windows Gebruikersaccountbeheer werkt op het apparaat.<br />U kunt het bijvoorbeeld uitschakelen of het niveau instellen waarbij u een melding moet ontvangen.|  
|**Netwerkfirewall**|Schakelt de Windows-firewall in of uit.|  
|**SmartScreen**|Schakel Windows SmartScreen in of uit.|  
|**Virusbeveiliging**|Hiermee vereist u dat antivirussoftware wordt geïnstalleerd en geconfigureerd.|  
|**Handtekeningen voor virusbeveiliging zijn bijgewerkt**|Vereist dat de handtekeningbestanden voor de antivirussoftware op het apparaat moeten up-to-date te houden.|  
  
### <a name="windows-information-protection-wip"></a>Windows-gegevensbeveiliging (OHW)

Met de toename van apparaten in de onderneming die het eigendom zijn van werknemers, is ook het risico toegenomen op het onbedoeld lekken van gegevens via apps en services, zoals e-mail, sociale media en de openbare cloud, die zich buiten de invloedssfeer van de onderneming bevinden. Bijvoorbeeld in het geval dat een werknemer de laatste nieuwe afbeeldingen van een technologieproject via zijn of haar persoonlijk e-mailaccount verstuurt, productinformatie in een tweet kopieert en plakt, of een voorlopig verkooprapport in de openbare cloudopslag opslaat.

Windows Information Protection (voorheen ondernemingsgegevensbescherming) helpt te beschermen tegen deze potentiële gegevenslekken zonder dat de gebruikerservaring van werknemers Hierdoor wordt beïnvloed. OHW helpt ook bij het beveiligen van zakelijke apps en gegevens tegen onbedoelde gegevenslekken op apparaten die eigendom zijn van enterprise- en persoonlijke apparaten die werknemers meenemen naar het werk zonder wijzigingen aan uw omgeving of andere apps.

 Configuration Manager Windows Information Protection-configuratie-items beheren de lijst met apps die zijn beveiligd door OHW, bedrijfsnetwerklocaties, beveiligingsniveau en de versleutelingsinstellingen.
  

Zie voor meer informatie over het configureren van Windows Information protection met Configuration Manager [uw Ondernemingsgegevens beveiligen met Windows-beveiliging (OHW)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
  
## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd met de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md)
