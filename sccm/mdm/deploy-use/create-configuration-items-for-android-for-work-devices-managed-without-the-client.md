---
title: Configuratie-items maken voor Android voor werk apparaten die worden beheerd met Intune
ms.custom: na
ms.date: 2017-07-31
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab6784fd-8c57-4be9-858f-50fe39f2ff5f
caps.latest.revision: "17"
caps.handback.revision: "0"
author: robstackmsft
translation.priority.ht:
- cs-cz
- de-de
- en-gb
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 87b34f0a3cce87f6e2ba813957a69b743648c1ca
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-configuration-items-for-android-for-work-devices-managed-with-intune"></a>Configuratie-items maken voor Android voor werk apparaten die worden beheerd met Intune

 De System Center Configuration Manager gebruiken **Android for Work** configuratie-item voor het beheren van instellingen voor Android voor Work-apparaten die zijn geregistreerd bij Microsoft Intune of on-premises worden beheerd door Configuration Manager.  

### <a name="to-create-an-android-for-work-configuration-item"></a>Maken van een Android voor configuratie van werkitem  

1.  Klik in de Configuration Manager-console op **activa en naleving**.  

2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  

3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  

4.  Geef op de pagina **Algemeen** van de wizard **Configuratie-item maken**een naam en een optionele beschrijving voor het configuratie-item op.  

5.  Onder **Geef het type configuratie-item dat u wilt maken**, selecteer **Android for Work**.  

6.  Kies **categorieën** als u categorieën maakt en toewijst om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  

  Klik op **Volgende**.

7.  Op de **apparaatinstellingen** pagina van de wizard, selecteert u de voor Instellingengroepen die u wilt configureren. Zie [Android for Work-instellingen voor configuratie-item](#android-for-work-configuration-item-settings-reference) voor meer informatie en klik vervolgens op **volgende**.  

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

##  <a name="android-for-work-configuration-item-settings-reference"></a>Android voor Work-verwijzing voor instellingen van configuratie-item  

### <a name="password"></a>Wachtwoord  

|Instelling|Details|  
|-------------|-------------|  
|**Wachtwoordinstellingen vereisen op mobiele apparaten**|Hiermee vereist u een wachtwoord op ondersteunde apparaten.|  
|**Minimale wachtwoordlengte (tekens)**|De minimale lengte van het wachtwoord.|  
|**Wachtwoordverlooptijd in dagen**|Het aantal dagen waarna een wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Voorkomt dat hergebruik van recente gebruikte wachtwoorden.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Wist de gegevens op het apparaat als dit aantal aanmeldingspogingen mislukt.|  
|**Niet-actieve periode waarna apparaat wordt vergrendeld**|Selecteer de hoeveelheid tijd die het apparaat niet gebruikt wordt voordat het wordt vergrendeld.|
|**Wachtwoordkwaliteit**|Hiermee selecteert u het complexiteitsniveau voor het wachtwoord en geeft u ook aan of biometrische apparaten kunnen worden gebruikt.|  
|**Smart Lock en andere vertrouwde agents toestaan**|Hiermee kunt u de functie Smart Lock beheren op compatibele Android-apparaten. Met deze telefoonmogelijkheid, soms ook wel vertrouwde agents kunt u uitschakelen of het wachtwoord van het apparaat vergrendelen scherm overslaan als het apparaat zich in een vertrouwde locatie bevindt, zoals wanneer deze is verbonden met een bepaald Bluetooth-apparaat, of wanneer het zich in de buurt van een NFC-tag bevindt. U kunt deze instelling gebruiken om te voorkomen dat eindgebruikers Smart Lock configureren.|
|**Vingerafdruk voor ontgrendelen**|&nbsp;|

###  <a name="work-profile"></a>Work-profiel  
 Deze instellingen gelden alleen voor Samsung KNOX-apparaten.  

|Naam van de instelling|Details|  
|------------------|-------------|  
|**Gegevens delen tussen werk en persoonlijke profielen toestaan**|U kunt kiezen uit:<br>- **Niet geconfigureerd**<br>- **Standaard-mediumgebruik**<br>- **Apps in work-profiel kunnen verwerken aanvraag van persoonlijk profiel**<br>- **Apps in persoonlijk profiel kunnen aanvraag van work-profiel verwerken**<br><br>(Zie ook [kopiëren en plakken instellingen](#copy-paste-configuration-item-settings) met behulp van aangepaste URI)|  
|**Werk profiel meldingen verbergen wanneer het apparaat is vergrendeld (Android 6.0 en hoger)**||
|**Set app machtiging standaardbeleid (Android 6.0 en hoger)**|U kunt kiezen uit:<br>- **Niet geconfigureerd**<br>- **Altijd vragen**<br>- **Automatisch verlenen**<br>- **Automatisch weigeren**|

### <a name="copy-paste-configuration-item-settings"></a>Configuratie-iteminstellingen voor kopiëren en plakken
Geen van de **gegevens delen tussen werk en persoonlijke profielen toestaan** opties kopiëren en plakken voorkomen. Gebruik een aangepaste instelling die kan worden geconfigureerd om te kopiëren en plakken voorkomen. Dit kan worden ingesteld via aangepaste URI.

- OMA-URI: ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste
- Waardetype: Boolean-waarde

DisallowCrossProfileCopyPaste instellen op waar wordt voorkomen dat gedrag kopiëren en plakken tussen Android for Work persoonlijke en zakelijke profielen.

## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd zonder de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
