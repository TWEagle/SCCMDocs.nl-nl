---
title: Certificaten en beveiliging | Microsoft Docs
description: Certificaten en beveiliging beheren voor System Center Updates Publisher
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7f91e63-4750-402e-9970-dd14be7f76a3
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: c43af95a539a9284e4e49822b284783e02f9fa21
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-certificates-and-security-for-updates-publisher"></a>Beheren van certificaten en beveiliging voor Updates Publisher

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende procedures kunt u het certificaatarchief op de updateserver configureren, het configureren van een zelf-ondertekend certificaat op de clientcomputer en gepubliceerd voor het configureren van het groepsbeleid zodat de Windows Update Agent op computers om te scannen op updates.

## <a name="configure-the-certificate-store-on-the-update-server"></a>Het certificaatarchief op de updateserver configureren
 Een digitaal certificaat updates Publisher gebruikt voor het ondertekenen van de updates in de catalogus die wordt gepubliceerd. Voordat een catalogus kan worden gepubliceerd naar de updateserver, moet dat certificaat in het certificaatarchief op de updateserver en in het certificaatarchief van de computer Updates Publisher als de computer extern van de update-server.

De volgende procedure is een van de verschillende manieren het certificaat in het certificaatarchief op de updateserver toevoegen.

### <a name="to-configure-the-certificate-store"></a>Het certificaatarchief configureren
1.  Klik op een computer die toegang zowel de computer Updates Publisher en de update-server tot, **Start**, klikt u op **uitvoeren**, type **MMC** in het tekstvak en klik vervolgens op **OK** Microsoft Management Console (MMC) openen.

2.  Klik op **bestand**, klikt u op **module toevoegen/verwijderen**, klikt u op **toevoegen**, klikt u op **certificaten**, klikt u op **toevoegen**, selecteer **computeraccount**, en klik vervolgens op **volgende**.

3.  Selecteer **een andere computer**, typ de naam van de update-server of klik op **Bladeren** voor de update server-computer, klikt u **voltooien**, klikt u op **sluiten**, en klik vervolgens op **OK**.

4.  Vouw  **certificaten (*update servernaam*) **, vouw **WSUS**, en klik vervolgens op **certificaten**.

5.  In het deelvenster met resultaten met de rechtermuisknop op het gewenste certificaat, klikt u op **alle taken**, en klik vervolgens op **exporteren**.

6.  Gebruik de standaardinstellingen voor het maken van een exportbestand met de naam en locatie die is opgegeven in de wizard in de Wizard Certificaat exporteren. Dit bestand moet beschikbaar zijn voor de update-server voordat u doorgaat met de volgende stap.

7.  Met de rechtermuisknop op **vertrouwde uitgevers**, klikt u op **alle taken**, en klik vervolgens op **importeren**. Voltooi de Wizard Certificaat importeren met behulp van het geëxporteerde bestand uit stap 6.

8.  Als u een zelfondertekend certificaat gebruikt, zoals **WSUS Publishers Self-signed**, met de rechtermuisknop op **Trusted Root Certification Authorities**, klikt u op **alle taken**, en klik vervolgens op **importeren**. Voltooi de Wizard Certificaat importeren met behulp van het geëxporteerde bestand uit stap 6.

9.  Met de rechtermuisknop op  **certificaten (*update servernaam*) **, klikt u op **verbinding maken met een andere computer**, voer de computernaam voor de computer Updates Publisher en op **OK**.

10. Als Updates Publisher extern van de update-server is, herhaalt u stap 7 tot en met 9 voor het importeren van het certificaat naar het certificaatarchief op de computer Updates Publisher.



## <a name="configure-a-self-signing-certificate-on-client-computers"></a>Een zelf-ondertekend certificaat configureren op clientcomputers
Op clientcomputers scant de Windows Update Agent (WUA) voor de updates van de catalogus. Dit proces mislukt om updates te installeren wanneer de agent dat digitale certificaat niet in het archief met vertrouwde uitgevers op de lokale computer vinden kan. Als een zelfondertekend certificaat is gebruikt voor het publiceren van de updates catalogus zoals **WSUS Publishers Self-signed**, moet het certificaat ook in het certificaatarchief van vertrouwde basiscertificeringsinstanties op de lokale computer zodat de agent kan controleren of de geldigheid van het certificaat.

U kunt een van de verschillende methoden gebruiken voor het configureren van certificaten op clientcomputers, zoals het gebruik van Groepsbeleid en de **Wizard Certificaat importeren** of met behulp van de Certutil-hulpprogramma en softwaredistributie.

Het volgende is opgegeven als een voorbeeld van het handtekeningcertificaat configureren op clientcomputers.

### <a name="to-configure-a-self-signing-certificate-on-client-computers"></a>Een zelf-ondertekende certificaat configureren op clientcomputers
1.  Klik op een computer met toegang tot de updateserver **Start**, klikt u op **uitvoeren**, type **MMC** in het tekstvak en klik vervolgens op **OK** Microsoft Management Console (MMC) openen.

2.  Klik op **bestand**, klikt u op **module toevoegen/verwijderen**, klikt u op **toevoegen**, klikt u op **certificaten**, klikt u op **toevoegen**, selecteer **computeraccount**, en klik vervolgens op **volgende**.

3.  Selecteer **een andere computer**, typ de naam van de update-server of klik op **Bladeren** voor de update server-computer, klikt u **voltooien**, klikt u op **sluiten**, en klik vervolgens op **OK**.

4.  Vouw  **certificaten (*update servernaam*) **, vouw **WSUS**, en klik vervolgens op **certificaten**.

5.  Met de rechtermuisknop op het certificaat in het deelvenster met resultaten, klikt u op **alle taken**, en klik vervolgens op **exporteren**. Voltooi de **Wizard Certificaat exporteren** met de standaardinstellingen voor het maken van een exportbestand van het certificaat met de naam en locatie die is opgegeven in de wizard.

6.  Gebruik een van de volgende methoden om het certificaat dat wordt gebruikt voor het ondertekenen van de updatecatalogus naar elke clientcomputer die WUA gebruiken om te scannen voor de updates in de catalogus toevoegen. Het certificaat op de clientcomputer als volgt toevoegen:

    -   Voor zelf-ondertekende certificaten: Het certificaat toevoegen aan de **Trusted Root Certification Authorities** en **vertrouwde uitgevers** certificaatarchieven.

    -   Voor de certificeringsinstantie (CA) van uitgegeven certificaten: Het certificaat toevoegen aan de **vertrouwde uitgevers** certificaatarchief.

    > [!NOTE]
    > De WUA controleert ook of de **ondertekende inhoud toestaan in de locatie van Microsoft update intranet** instelling voor Groepsbeleid is ingeschakeld op de lokale computer. Deze beleidsinstelling moet worden ingeschakeld voor WUA om te scannen naar de updates die zijn gemaakt en gepubliceerd met Updates Publisher. Zie voor meer informatie over het inschakelen van deze groepsbeleidsinstelling [het configureren van het groepsbeleid op clientcomputers] (https://technet.microsoft.com/library/bb530967.aspx(d=robot).



## <a name="configuring-group-policy-to-allow-wua-on-computers-to-scan-for-published-updates"></a>Groepsbeleid WUA toestaan op computers die u wilt zoeken naar gepubliceerde updates configureren
Voordat de Windows Update Agent (WUA) op computers op updates die zijn gemaakt en gepubliceerd met Updates Publisher scannen gaat, moet u een beleidsinstelling ingeschakeld om toe te staan ondertekende inhoud van een intranetlocatie Microsoft update-service. Als de beleidsinstelling is ingeschakeld, accepteert WUA via een intranetlocatie ontvangen als de updates zijn ondertekend in updates de **vertrouwde uitgevers** certificaatarchief op de lokale computer. Er zijn verschillende methoden voor het configureren van Groepsbeleid op computers in de omgeving.

Voor computers die zich niet in het domein, kunt u een registersleutelinstelling geconfigureerd waarmee ondertekende inhoud van de locatie van Microsoft-updateservice in intranet.

De volgende procedures bevatten de basisstappen die kunnen worden gebruikt om Groepsbeleid te configureren voor computers in het domein en een registersleutelwaarde op computers die zich niet op het domein.

### <a name="to-configure-group-policy-to-allow-wua-to-scan-for-published-updates"></a>Gepubliceerd voor het configureren van Groepsbeleid om toe te staan WUA om te scannen op updates
1.  Open de module Group Policy Object Editor Microsoft Management Console (MMC) met een gebruiker met de juiste beveiligingsrechten om Groepsbeleid te configureren.

2.  Klik op **Bladeren** en selecteer het domein, organisatie-eenheid of GPO's die zijn gekoppeld aan de site waar het geconfigureerde Groepsbeleid worden doorgegeven aan de gewenste clientcomputers. Klik op **OK**, klikt u op **voltooien**, klikt u op **sluiten**, en klik vervolgens op **OK**.

3.  Vouw de geselecteerde instelling in de consolestructuur uit, vouw **Computerconfiguratie**, vouw **Beheersjablonen**, vouw **Windows-onderdelen**, en klik vervolgens op **Windows Update**.

4.  In het deelvenster met resultaten met de rechtermuisknop op **ondertekende inhoud toestaan in de locatie van Microsoft update intranet**, klikt u op **eigenschappen**, klikt u op **ingeschakeld**, en klik vervolgens op **OK**.
