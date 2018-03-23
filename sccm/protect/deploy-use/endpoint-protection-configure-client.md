---
title: Endpoint Protection-Client configureren
titleSuffix: Configuration Manager
description: Informatie over het configureren van aangepaste clientinstellingen voor Endpoint Protection die kan worden geïmplementeerd naar verzamelingen van computers in uw hiërarchie.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 22c56bac25cc6e3129f2e8478bbae9fa8782de9f
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-custom-client-settings-for-endpoint-protection"></a>Aangepaste clientinstellingen voor Endpoint Protection configureren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

Deze procedure configureert u aangepaste clientinstellingen voor Endpoint Protection, die kunnen worden geïmplementeerd op verzamelingen van computers in uw hiërarchie.

> [!IMPORTANT]
>  Alleen de standaardinstellingen van de Endpoint Protection-client configureren als u zeker dat u ze toepassen op alle computers in uw hiërarchie wilt. 

## <a name="to-enable-endpoint-protection-and-configure-custom-client-settings"></a>Endpoint Protection inschakelen en aangepaste clientinstellingen configureren

1.  Klik op **Beheer**in de Configuration Manager-console.

2.  Klik in de werkruimte **Beheer** op **Clientinstellingen**.

3.  Klik op het tabblad **Start** in de groep **Maken** op **Aangepaste clientapparaatinstellingen maken**.

4.  Geef in het dialoogvenster **Aangepaste clientapparaatinstellingen maken** een naam en een beschrijving op voor de groep instellingen en selecteer vervolgens **Endpoint Protection**.

5.  Configureer de Endpoint Protection-clientinstellingen die u nodig hebt. Voor een volledige lijst met Endpoint Protection-clientinstellingen die u kunt configureren, Zie de sectie Endpoint Protection in [over clientinstellingen in System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).

   > [!IMPORTANT]
   >  Voordat u clientinstellingen voor Endpoint Protection kunt configureren, moet u de Endpoint Protection-sitesysteemrol installeren.

6.  Klik op **OK** om het dialoogvenster **Aangepaste clientapparaatinstellingen maken** te sluiten. De nieuwe clientinstellingen worden weergegeven in het knooppunt **Clientinstellingen** van de werkruimte **Beheer** .

7.  Voordat u de aangepaste clientinstellingen kunt gebruiken, moet u ze in een verzameling implementeren. Selecteer de aangepaste clientinstellingen die u wilt implementeren en klik vervolgens op het tabblad **Start** in de groep **Clientinstellingen** op **Implementeren**.

8.  Kies in het dialoogvenster **Verzameling selecteren** de verzameling waarin u de clientinstellingen wilt implementeren en klik vervolgens op **OK**. De nieuwe implementatie wordt weergegeven op het tabblad **Implementaties** van het detailvenster.

Clientcomputers zullen worden geconfigureerd met deze instellingen wanneer ze de volgende keer het clientbeleid downloaden. Zie voor het ophalen van beleid voor één client initiëren, het ophalen van de beleid initiëren voor een Configuration Manager-Client in [clients in System Center Configuration Manager beheren](../../core/clients/manage/manage-clients.md).

## <a name="how-to-provision-the-endpoint-protection-client-in-a-disk-image-in-configuration-manager"></a>De Endpoint Protection-client in een schijfinstallatiekopie inrichten in Configuration Manager
U kunt de Endpoint Protection-client installeren op een computer die u wilt gebruiken als bron voor schijfinstallatiekopieën voor besturingssysteemimplementatie van Configuration Manager. Deze computer wordt doorgaans de referentiecomputer genoemd. Nadat u de installatiekopie van het besturingssysteem hebt gemaakt, kunt u kunt vervolgens besturingssysteemimplementatie van Configuration Manager gebruiken om de installatiekopie die softwarepakketten, met inbegrip van Endpoint Protection op de clientcomputers kan bevatten.

Gebruik de procedures in dit artikel voor hulp bij het installeren en configureren van de Endpoint Protection-client op een referentiecomputer

### <a name="prerequisites-for-installing-the-endpoint-protection-client-on-the-reference-computer"></a>Vereisten voor het installeren van de Endpoint Protection-client op de referentiecomputer
De volgende lijst bevat de vereisten voor het installeren van de Endpoint Protection-clientsoftware op een referentiecomputer.

-   U moet toegang hebben tot het clientinstallatiepakket van de Endpoint Protection **scepinstall.exe**. Dit pakket kan worden gevonden in de **Client** map van de Microsoft System Center Configuration Manager-installatiemap op de siteserver. Windows 10 en Windows Server 2016 hebt Windows Defender is geïnstalleerd. 

-   Om te controleren of de Endpoint Protection client wordt geïmplementeerd met de configuratie die is in uw organisatie vereist, maakt u een antimalwarebeleid en exporteert u dat beleid. Vervolgens kunt u het antimalwarebeleid moet worden gebruikt wanneer u de Endpoint Protection-client handmatig installeert. Zie voor meer informatie [maken en implementeren van antimalwarebeleid voor Endpoint Protection in System Center Configuration Manager](endpoint-antimalware-policies.md).

   > [!NOTE]
   >  De **standaard Antimalwarebeleid Client** kan niet worden geëxporteerd.

-   Als u de Endpoint Protection-client installeren met de meest recente definities wilt, u moet deze downloaden vanuit de [Microsoft Malware Protection Center](http://go.microsoft.com/fwlink/?LinkID=200965).

>[!NOTE]
> Vanaf Configuration Manager 1802, hoeft Windows 10-apparaten niet te hebben van de Endpoint Protection agent (SCEPInstall) is geïnstalleerd. Als deze al is geïnstalleerd op Windows 10-apparaten, wordt Configuration Manager niet verwijderd. Beheerders kunnen de Endpoint Protection-agent op Windows 10-apparaten die met ten minste de clientversie 1802 verwijderen. SCEPInstall.exe mogelijk nog steeds in C:\Windows\ccmsetup op sommige computers aanwezig, maar niet moeten worden gedownload op de nieuwe clientinstallaties. <!--503654-->
### <a name="how-to-install-the-endpoint-protection-client-software-on-the-reference-computer"></a>De Endpoint Protection-clientsoftware installeren op de referentiecomputer
U kunt de Endpoint Protection-client lokaal installeren op de referentiecomputer vanaf een opdrachtprompt. Hiervoor hebt u het installatiebestand **scepinstall.exe**nodig. U kunt de client ook installeren met een vooraf geconfigureerd antimalwarebeleid of met een antimalwarebeleid dat u eerder hebt geëxporteerd.

## <a name="to-install-the-endpoint-protection-client-from-a-command-prompt"></a>De Endpoint Protection-client installeren via een opdrachtprompt

1.  Kopiëren **scepinstall.exe** van de **Client** map op de installatiemedia van System Center Configuration Manager op de computer waarop u wilt de Endpoint Protection-clientsoftware installeren.

2.  Open een opdrachtprompt met beheerdersbevoegdheden, navigeer naar de map waar **scepinstall.exe** zich bevindt en voer de volgende opdracht, toe te voegen eventuele aanvullende opdrachtregeleigenschappen die u nodig hebt:

   ```
   scepinstall.exe
   ```

    U kunt een van de volgende opdrachtregeleigenschappen opgeven:

   |Eigenschap|Beschrijving|
   |--------------|-----------------|
   |/s|Hiermee geeft u op dat een installatie op de achtergrond moet worden uitgevoerd.|
   |/q|Hiermee geeft u op dat de installatiebestanden op de achtergrond moeten worden uitgepakt.|
   |/i|Hiermee geeft u op dat een normale installatie moet worden uitgevoerd.|
   |/noreplace|Hiermee geeft u op dat antimalwaresoftware van derden niet moet worden verwijderd tijdens de installatie.|
   |/policy|Hiermee geeft u een bestand voor antimalwarebeleid op waarmee de client tijdens de installatie moet worden geconfigureerd.|
   |/sqmoptin|Hiermee geeft u op dat deze clientsoftware-installatie moet worden aangemeld bij het Microsoft-programma voor kwaliteitsverbetering.|

3.  Volg de instructies om de clientinstallatie te voltooien.

4.  Als u het meest recente pakket met updatedefinities hebt gedownload, kopieert u dit pakket naar de clientcomputer en dubbelklikt u op het pakket om het te installeren.

   > [!NOTE]
   >  Nadat de installatie van de Endpoint Protection-client is voltooid, wordt de client automatisch een definitie-update-controle uitvoert. Als deze update beschikbaar is, hebt u niet de meest recente definitie-updatepakket handmatig installeren.

## <a name="to-install-the-client-software-with-an-antimalware-policy-from-the-command-prompt"></a>De clientsoftware met een antimalwarebeleid installeren via de opdrachtprompt

1.  Kopiëren **scepinstall.exe** en het geëxporteerde of vooraf geconfigureerde antimalwarebeleid naar de computer waarop u wilt de Endpoint Protection-clientsoftware installeren.

2.  Open een opdrachtprompt met beheerdersbevoegdheden, navigeer naar de map waarin **scepinstall.exe** en het antimalwarebeleid zijn opgenomen en voer de volgende opdracht uit, inclusief eventuele aanvullende opdrachtregeleigenschappen:

   ```
   scepinstall.exe /policy <full path>\<policy file>
   ```

3.  Volg de instructies om de clientinstallatie te voltooien.

4.  Als u het meest recente pakket met definities hebt gedownload, kopieert u dit pakket naar de clientcomputer en dubbelklikt u op het pakket om het te installeren.

   > [!NOTE]
   >  Nadat de installatie van de Endpoint Protection-client is voltooid, wordt de client automatisch een definitie-update-controle uitvoert. Als deze update beschikbaar is, hebt u niet de meest recente definitie-updatepakket handmatig installeren.

## <a name="verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Controleren of de Endpoint Protection-client correct is geïnstalleerd
Nadat u de Endpoint Protection-client op uw referentiecomputer hebt geïnstalleerd, moet u controleren of de client correct werkt.

### <a name="to-verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Controleren of de Endpoint Protection-client correct is geïnstalleerd

1.  Open op de referentiecomputer **System Center Endpoint Protection** vanuit het Windows-systeemvak.

2.  Op de **Start** tabblad van de **System Center Endpoint Protection** dialoogvenster Controleer **real-timebeveiliging** is ingesteld op **op**.

3.  Controleer **Up-to-date** wordt weergegeven voor **definities van virussen en spyware**.

4.  Selecteer onder **Opties voor scan**de optie **Volledig**en klik vervolgens op **Nu scannen**om ervoor te zorgen dat uw referentiecomputer gereed is voor imaging.

### <a name="how-to-prepare-the-endpoint-protection-client-for-imaging"></a>De Endpoint Protection-client voorbereiden voor imaging
Nadat u hebt gecontroleerd of de Endpoint Protection-client correct is geïnstalleerd op de referentiecomputer, kunt u de computer voorbereiden voor imaging. Voer de volgende stappen uit om de Endpoint Protection-client voorbereiden voor imaging.


Zie voor meer informatie over de implementatie van besturingssystemen in Configuration Manager [installatiekopieën van besturingssystemen met System Center Configuration Manager beheren](/sccm/osd/get-started/manage-operating-system-images).

### <a name="to-prepare-the-endpoint-protection-client-for-imaging"></a>De Endpoint Protection-client voorbereiden voor imaging

1.  Meld u op de referentiecomputer aan als een gebruiker met beheerdersrechten.

2.  Download en installeer **PsTools** van de site [Windows SysInternals](http://go.microsoft.com/fwlink/?LinkId=215263) op TechNet.

3.  Open een opdrachtprompt met verhoogde bevoegdheid, navigeer naar de map waarin u PsTools hebt geïnstalleerd en typ de volgende opdracht

   ```
   Psexec.exe -s -i regedit.exe
   ```

   > [!IMPORTANT]
   >  Wees voorzichtig wanneer u de Register-Editor op deze manier uitvoert; de optie -s in PsExec.exe wordt Register-Editor met LocalSystem-bevoegdheden uitgevoerd.

4.  Navigeer in Register-editor naar elk van de volgende registersleutels en verwijder deze.

   > [!IMPORTANT]
   >  U moet de registersleutels verwijderen als laatste stap voordat u een installatiekopie van de referentiecomputer maakt. De registersleutels worden opnieuw gemaakt wanneer de Endpoint Protection-client wordt gestart. Als u de referentiecomputer opnieuw opstart, moet u de registersleutels opnieuw verwijderen.

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\InstallTime**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanRun**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanType**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastQuickScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastFullScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RemovalTools\MRT\GUID**

Wanneer u de voorgaande stappen hebt uitgevoerd, kunt u de referentiecomputer voorbereiden voor imaging. Zie voor meer informatie over de implementatie van besturingssystemen in Configuration Manager [installatiekopieën van besturingssystemen met System Center Configuration Manager beheren](/sccm/osd/get-started/manage-operating-system-images).

Wanneer een installatiekopie met de Endpoint Protection-clientsoftware wordt geïmplementeerd, rapporteert de Endpoint Protection-client automatisch informatie aan de Configuration Manager-site waaraan de computer is toegewezen, en beleid van toepassing op de clientcomputer gedownload en toegepast.
