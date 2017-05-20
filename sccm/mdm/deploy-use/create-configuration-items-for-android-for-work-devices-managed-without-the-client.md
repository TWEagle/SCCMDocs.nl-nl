---
title: Configuratie-items maken voor Android voor werk apparaten die worden beheerd met Intune
ms.custom: na
ms.date: 2017-03-28
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab6784fd-8c57-4be9-858f-50fe39f2ff5f
caps.latest.revision: 17
caps.handback.revision: 0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: e6170339b8f3354c549579f127a5c3c618833943
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-create-configuration-items-for-android-for-work-devices-managed-with-intune"></a>Configuratie-items maken voor Android voor werk apparaten die worden beheerd met Intune
  
 Gebruik de System Center Configuration Manager **Android for Work** configuratie-item voor het beheren van instellingen voor Android voor werk apparaten die zijn ingeschreven bij Microsoft Intune of beheerde on-premises door Configuration Manager.  
  
### <a name="to-create-an-android-for-work-configuration-item"></a>Maken van een Android voor configuratie van werkitem  
  
1.  Klik in de Configuration Manager-console op **activa en naleving**.  
  
2.  Vouw in de werkruimte **Activa en naleving** het gedeelte **Instellingen voor naleving**uit en klik vervolgens op **Configuratie-items**.  
  
3.  Klik op het tabblad **Start** in de groep **Maken** op **Configuratie-item maken**.  
  
4.  Geef op de pagina **Algemeen** van de wizard **Configuratie-item maken**een naam en een optionele beschrijving voor het configuratie-item op.  
  
5.  Onder **Geef het type configuratie-item dat u wilt maken**, selecteer **Android for Work**.  
  
6.  Klik op **categorieën** als u maken en toewijzen van categorieën om te zoeken en filteren van configuratie-items in de Configuration Manager-console.  
  
7.  Op de pagina **Apparaatinstellingen** van de wizard selecteert u de instellingengroep die u wilt configureren. Zie **Naslaginformatie voor configuratie-iteminstellingen voor Android en Samsung KNOX** in dit onderwerp voor meer informatie en klik daarna op **Volgende**.  
  
    > [!TIP]  
    >  Als de gewenste instelling niet wordt weergegeven, schakelt u het selectievakje **Extra instellingen configureren die niet zijn opgenomen in de standaardinstellingsgroepen** in.  
  
9. Op elke instellingenpagina configureert u de instellingen die u nodig hebt en geeft u aan of u deze wilt corrigeren wanneer ze niet compliant zijn op apparaten (wanneer dit wordt ondersteund).  
  
10. U kunt voor elke instellingengroep ook de ernst configureren die wordt gerapporteerd als wordt geconstateerd dat een configuratie-item niet compliant is:  
  
    -   **Geen** -apparaten die niet voldoen aan deze compliantieregel doen geen fouternst voor Configuration Manager-rapporten.  
  
    -   **Informatie** -apparaten die niet voldoen aan deze compliantieregel fouternst van **informatie** voor Configuration Manager-rapporten.  
  
    -   **Waarschuwing** -apparaten die niet voldoen aan deze compliantieregel fouternst van **waarschuwing** voor Configuration Manager-rapporten.  
  
    -   **Kritieke** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten.  
  
    -   **Kritiek met gebeurtenis** -apparaten die niet voldoen aan deze compliantieregel fouternst van **kritieke** voor Configuration Manager-rapporten. Dit ernstniveau wordt ook vastgelegd als een Windows-gebeurtenis in het logboek voor toepassingsgebeurtenissen.  
  
11. Op de pagina **Platformtoepasbaarheid** van de wizard controleert u alle instellingen die niet compatibel zijn met de ondersteunde platforms die u eerder hebt geselecteerd. U kunt teruggaan en deze instellingen verwijderen of u kunt doorgaan.  
  
    > [!TIP]  
    >  Niet-ondersteunde instellingen worden niet beoordeeld op compliantie.  
  
12. Voltooi de wizard.  
  
 U kunt het nieuwe configuratie-item weergeven in het knooppunt **Configuratie-items** van de werkruimte **Activa en naleving** .  
  
##  <a name="android-for-work-configuration-item-settings-reference"></a>Android voor werk-verwijzing voor instellingen van configuratie-item  
  
### <a name="password"></a>Wachtwoord  
   
|Instelling|Details|  
|-------------|-------------|  
|**Wachtwoordinstellingen vereisen op mobiele apparaten**|Hiermee vereist u een wachtwoord op ondersteunde apparaten.|  
|**Minimale wachtwoordlengte (tekens)**|De minimale lengte van het wachtwoord.|  
|**Wachtwoordverlooptijd in dagen**|Het aantal dagen waarna een wachtwoord moet worden gewijzigd.|  
|**Aantal onthouden wachtwoorden**|Voorkomt dat eerder gebruikte wachtwoorden opnieuw worden gebruikt.|  
|**Aantal mislukte aanmeldingspogingen voordat het apparaat wordt gewist**|Wist de gegevens op het apparaat als dit aantal aanmeldingspogingen mislukt.|  
|**Niet-actieve tijd voordat het apparaat wordt vergrendeld**|Selecteer de tijdsduur voordat het apparaat wordt vergrendeld als dit niet wordt gebruikt.|
|**Wachtwoordkwaliteit**|Hiermee selecteert u het complexiteitsniveau voor het wachtwoord en geeft u ook aan of biometrische apparaten kunnen worden gebruikt.|  
|**Smart vergrendelen en andere agents vertrouwensrelatie toestaan**|Hiermee kunt u de functie Smart Lock beheren op compatibele Android-apparaten. Met deze telefoonmogelijkheid (soms ook wel vertrouwde agent genoemd) kunt u het vergrendelingsschermwachtwoord op het apparaat uitschakelen of overslaan als het zich op een vertrouwde locatie bevindt, zoals wanneer het is verboden met een bepaald Bluetooth-apparaat, of wanneer het zich in de buurt bevindt van een NFC-tag. U kunt deze instelling gebruiken om te voorkomen dat eindgebruikers Smart Lock configureren.|
|**Vingerafdruk voor ontgrendelen**||
  
###  <a name="work-profile"></a>Werkprofiel  
 Deze instellingen gelden alleen voor Samsung KNOX-apparaten.  
  
|Naam van de instelling|Details|  
|------------------|-------------|  
|**Gegevens delen tussen werk en persoonlijke profielen toestaan**|U kunt kiezen uit:<br>- **Niet geconfigureerd**<br>- **Voorkomen dat eventuele worden gedeeld buiten de grenzen**<br>- **Apps in werkprofiel aankan aanvraag van persoonlijk profiel**<br>- **Er zijn geen beperkingen voor delen**<br>|  
|**Werk profiel meldingen verbergen wanneer het apparaat is vergrendeld (Android 6.0 +)**||
|**Set app machtiging standaardbeleid (Android 6.0 +)**|U kunt kiezen uit:<br>- **Niet geconfigureerd**<br>- **Altijd vragen**<br>- **Automatisch verlenen**<br>- **Automatisch weigeren**|
  
 
## <a name="see-also"></a>Zie ook  
 [Configuratie-items voor apparaten die worden beheerd zonder dat de System Center Configuration Manager-client](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
