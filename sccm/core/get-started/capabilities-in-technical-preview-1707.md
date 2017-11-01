---
title: Technische Preview 1707
titleSuffix: Configuration Manager
description: Meer informatie over functies die beschikbaar zijn in de Technical Preview-versie 1707 voor System Center Configuration Manager.
ms.custom: na
ms.date: 08/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb405ba0-8792-4ab7-988b-2f835f3a9550
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: bde9ed30ca5e52910a47c35cdb3d5b2f4475b18f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1707-for-system-center-configuration-manager"></a>Mogelijkheden van Technical Preview 1707 voor System Center Configuration Manager

*Van toepassing op: System Center Configuration Manager (Technical Preview)*

Dit artikel bevat de functies die beschikbaar in de Technical Preview voor System Center Configuration Manager, versie 1707 zijn. U kunt deze versie om te werken en nieuwe mogelijkheden toevoegen aan uw Configuration Manager technical preview-site installeren. Controleer voordat u deze versie van de technical preview installeert, [Technical Preview voor System Center Configuration Manager](../../core/get-started/technical-preview.md) om vertrouwd te raken met algemene vereisten en beperkingen voor het gebruik van een technical preview hoe bijwerken tussen versies en hoe u feedback over de functies in een technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->

**Bekende problemen in deze Technical Preview:**
-   **Update voor de preview-versie 1707 mislukt wanneer u een siteserver in de passieve modus hebt**. Als u de preview-versie 1706 uitvoeren en hebben een [primaire siteserver in de passieve modus](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), moet u de passieve modus siteserver verwijderen voordat u de preview-site met succes naar versie 1707 bijwerken kunt. Nadat u uw site versie 1707 wordt uitgevoerd, kunt u de passieve modus siteserver opnieuw installeren.

  Verwijderen van de siteserver van de passieve modus:
  1. Ga in de console naar **beheer** > **overzicht** > **siteconfiguratie** > **Servers en sitesysteemrollen**, en selecteer vervolgens de passieve modus-siteserver.
  2. In de **sitesysteemrollen** deelvenster, rechts Klik op de **siteserver** rol, en kies vervolgens **rol verwijderen**.
  3. Met de rechtermuisknop op de siteserver van de passieve modus, en kies vervolgens **verwijderen**.
  4. Nadat de siteserver verwijdert, op de primaire siteserver van de actieve service opnieuw starten de **CONFIGURATION_MANAGER_UPDATE**.



**Hier volgen nieuwe functies die u met deze versie kunt uitproberen.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365"></a>Client-Peer-Cache-ondersteuning voor bestanden voor snelle installatie voor Windows 10 en Office 365
<!-- 1352486 -->
Peer-Cache ondersteunt vanaf deze release distributie van inhoud snelle installatiebestanden voor Windows 10 en van updatebestanden voor Office 365. Er zijn geen extra configuraties vereist.

## <a name="surface-device-dashboard"></a>Surface apparaat dashboard
<!--1355788-->
Het dashboard oppervlak apparaat bevat informatie over de apparaten die Surface gevonden in uw omgeving. Ga in de console naar **bewaking** > **oppervlak apparaten**. U kunt het volgende bekijken:
- percentage van het oppervlak
- percentage van het oppervlak modellen
- Top vijf besturingssysteemversies

Klik op een gedeelte van de **oppervlak modellen** diagram voor een volledige lijst van de apparaten.  

## <a name="configure-and-deploy-windows-defender-application-guard-policies"></a>Windows Defender toepassing Guard beleid configureren en implementeren
<!-- 1351960 -->

[Windows Defender toepassing Guard](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97) is een nieuwe Windows-functie die voorkomen dat uw gebruikers via niet-vertrouwde websites in een beveiligde geïsoleerde container die is niet toegankelijk voor andere onderdelen van het besturingssysteem. In deze technical preview ondersteuning voor het configureren van deze functie met Configuration Manager-instellingen voor naleving die u configureert en vervolgens implementeert op een verzameling toegevoegd. Deze functie worden uitgebracht Preview-versie voor de 64-bits versie van de Windows 10 vallen Creator Update (codename: RS3). Als u wilt testen van dit onderdeel nu moet u een preview-versie van deze update.

### <a name="before-you-start"></a>Voordat u begint

Voor het maken en implementeren van beleid voor Windows Defender toepassing Guard, moeten de Windows 10-apparaten waarop u het beleid implementeert worden geconfigureerd met een beleid voor het isoleren van netwerken. Zie voor meer informatie [dit blogbericht](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Deze functie werkt alleen met huidige Insider voor Windows 10-builds. Als u wilt testen, moeten uw clients worden uitgevoerd een recente Windows 10 Insider niet maken.

### <a name="try-it-out"></a>Probeer het nu!

#### <a name="to-create-a-policy-and-to-browse-the-available-settings"></a>Een beleid maken en om te bladeren, de beschikbare instellingen:

1. Kies in de Configuration Manager-console **activa en naleving**.
2. In de **activa en naleving** werkruimte, kiest u **overzicht** > **Endpoint Protection** > **Windows Defender toepassing Guard**.
3. In de **Start** tabblad, in de **maken** groep, klikt u op **maken Windows Defender Guard toepassingsbeleid**.
4. Met behulp van de blogbericht als uitgangspunt, kunt u bladeren en configureer de beschikbare instellingen voor de functie uitproberen.
5. In deze release toegevoegd de nieuwe **Netwerkdefinitie** pagina bij de wizard. Op deze pagina de zakelijke identiteit opgeven en definieer de grens van uw bedrijfsnetwerk.<br>Windows 10-computers opslaan slechts één netwerk isolatie lijst op de client. In deze release kunt u twee soorten netwerk isolatie lijsten (vanaf Windows Information Protection en vanaf Windows Defender toepassing Guard) maken en implementeren naar de client. Als u beide beleidsregels implementeren, moeten deze netwerk isolatie lijsten overeenkomen. Als u lijsten die niet met dezelfde client overeenkomen implementeert, mislukt de implementatie.
U vindt meer informatie over het opgeven van netwerkdefinities in het [documentatie van Windows-gegevensbeveiliging](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm).
6. Wanneer u klaar bent, voltooi de wizard en implementeer het beleid voor een of meer Windows 10-apparaten.

### <a name="further-reading"></a>Lees hier meer over
Voor meer informatie over Windows Defender toepassing Guard, Zie [dit blogbericht](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97). Zie ook voor meer informatie over Windows Defender toepassing Guard zelfstandige modus, [dit blogbericht](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903).

## <a name="add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager"></a>Parameters toevoegen bij het implementeren van PowerShell-scripts uit Configuration Manager

<!-- 1236459 --->

In de laatste Technical Preview we een nieuwe functie waarmee u geïntroduceerd [maken en uitvoeren van PowerShell-scripts uit de Configuration Manager-console](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console).
In deze Technical Preview hebben we uitgebreid op deze mogelijkheid. Configuration Manager nu het PowerShell-script worden gelezen en parameters weergegeven in de Wizard Script maken. U kunt opgeven dat een waarde voor de parameter in de wizard die wordt gebruikt wanneer het script wordt uitgevoerd. U kunt ook kunt u de parameter leeg laten. Als u dit doet, moet u een waarde voor de parameter opgeven wanneer u het script uitvoeren.
In deze technical preview, moet u de parameters die vereist dat een script opgeven. We zullen levert scriptparameters optioneel maken in een toekomstige release.

### <a name="try-it-out"></a>Probeer het nu!

1. Volg de instructies voor [maken en uitvoeren van PowerShell-scripts uit de Configuration Manager-console](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console).
2. Op de nieuwe **scriptparameters** pagina van de **Wizard Script maken**, kiest u een parameter en klik vervolgens op **bewerken**.
3. Geef een parameterwaarde voor de geselecteerde parameter en klik vervolgens op **OK**.
4. Voltooi de wizard.

Wanneer het script wordt uitgevoerd, wordt u ingestelde parameterwaarden gebruikt.
