---
title: Certificaten en beveiliging | Microsoft-documenten
description: Certificaten en beveiliging voor System Center Updates Publisher beheren
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7f91e63-4750-402e-9970-dd14be7f76a3
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: c43af95a539a9284e4e49822b284783e02f9fa21
ms.contentlocale: nl-nl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-certificates-and-security-for-updates-publisher"></a>Certificaten en beveiliging voor Updates Publisher beheren

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

De volgende procedures kunt u het certificaatarchief configureren op de updateserver, een zelf-ondertekend certificaat configureren op de clientcomputer en configureren van het groepsbeleid zodat de Windows Update Agent op computers om te scannen op gepubliceerd updates.

## <a name="configure-the-certificate-store-on-the-update-server"></a>Het certificaatarchief op de updateserver configureren
 Updates Publisher gebruikt een digitaal certificaat voor ondertekenen van de updates in de catalogus die wordt gepubliceerd. Voordat een catalogus kan worden gepubliceerd naar de updateserver, moet dat certificaat zich in het certificaatarchief op de updateserver en in het certificaatarchief van de Updates Publisher-computer als de computer extern is van de update-server.

De volgende procedure is een van de verschillende manieren naar het certificaat in het certificaatarchief op de updateserver toe te voegen.

### <a name="to-configure-the-certificate-store"></a>Het certificaatarchief configureren
1.  Klik op een computer die toegang hebben tot de computer met Updates Publisher en de updateserver **Start**, klikt u op **uitvoeren**, type **MMC** in het tekstvak in en klik vervolgens op **OK** openen van de Microsoft Management Console (MMC).

2.  Klik op **bestand**, klikt u op **module toevoegen/verwijderen**, klikt u op **toevoegen**, klikt u op **certificaten**, klikt u op **toevoegen**, selecteer **computeraccount**, en klik vervolgens op **volgende**.

3.  Selecteer **een andere computer**, typ de naam van de update-server of klik op **Bladeren** voor de update server-computer, klikt u op **voltooien**, klikt u op **sluiten**, en klik vervolgens op **OK**.

4.  Vouw  **certificaten (*update servernaam*) **, vouw **WSUS**, en klik vervolgens op **certificaten**.

5.  In het resultatenvenster met de rechtermuisknop op het gewenste certificaat, klikt u op **alle taken**, en klik vervolgens op **exporteren**.

6.  Gebruik de standaardinstellingen voor het maken van een bestand exporteren met de naam en locatie die is opgegeven in de wizard in de Wizard Certificaat exporteren. Dit bestand moet beschikbaar zijn voor de update-server voordat u doorgaat met de volgende stap.

7.  Met de rechtermuisknop op **vertrouwde uitgevers**, klikt u op **alle taken**, en klik vervolgens op **importeren**. Voltooi de Wizard Certificaat importeren met behulp van het geëxporteerde bestand uit stap 6.

8.  Als u een zelfondertekend certificaat gebruikt, zoals **WSUS Publishers Self-signed**, met de rechtermuisknop op **Trusted Root Certification Authorities**, klikt u op **alle taken**, en klik vervolgens op **importeren**. Voltooi de Wizard Certificaat importeren met behulp van het geëxporteerde bestand uit stap 6.

9.  Met de rechtermuisknop op  **certificaten (*update servernaam*) **, klikt u op **verbinding maken met een andere computer**, geef de computernaam voor de Updates Publisher-computer en klikt u op **OK**.

10. Als Updates Publisher extern van de updateserver is, herhaalt u stap 7 en 9 certificaat te importeren in het certificaatarchief op de computer met Updates Publisher.



## <a name="configure-a-self-signing-certificate-on-client-computers"></a>Een handtekeningcertificaat zelf op clientcomputers configureren
Op clientcomputers scant de Windows Update Agent (WUA) naar de updates uit de catalogus. Dit proces mislukt om updates te installeren wanneer de agent dat digitale certificaat niet in het archief Vertrouwde uitgevers op de lokale computer vinden kan. Als een zelfondertekend certificaat is gebruikt voor de publicatie van de updates catalogus zoals **WSUS Publishers Self-signed**, moet het certificaat ook zijn in het certificaatarchief van vertrouwde basiscertificeringsinstanties op de lokale computer zodat de agent kan de geldigheid van het certificaat.

U kunt een van de verschillende methoden gebruiken voor het configureren van certificaten op clientcomputers, zoals met behulp van Groepsbeleid en het **Wizard Certificaat importeren** of met behulp van de Certutil hulpprogramma en softwaredistributie.

Het volgende weergegeven als een voorbeeld van het configureren van het handtekeningcertificaat op clientcomputers.

### <a name="to-configure-a-self-signing-certificate-on-client-computers"></a>Een zelf-ondertekend certificaat configureren op clientcomputers
1.  Klik op een computer met toegang tot de updateserver **Start**, klikt u op **uitvoeren**, type **MMC** in het tekstvak in en klik vervolgens op **OK** openen van de Microsoft Management Console (MMC).

2.  Klik op **bestand**, klikt u op **module toevoegen/verwijderen**, klikt u op **toevoegen**, klikt u op **certificaten**, klikt u op **toevoegen**, selecteer **computeraccount**, en klik vervolgens op **volgende**.

3.  Selecteer **een andere computer**, typ de naam van de update-server of klik op **Bladeren** voor de update server-computer, klikt u op **voltooien**, klikt u op **sluiten**, en klik vervolgens op **OK**.

4.  Vouw  **certificaten (*update servernaam*) **, vouw **WSUS**, en klik vervolgens op **certificaten**.

5.  Met de rechtermuisknop op het certificaat in het resultaatvenster, klikt u op **alle taken**, en klik vervolgens op **exporteren**. Voltooi de **Wizard Certificaat exporteren** de standaardinstellingen gebruiken voor het maken van een exportbestand certificaat met de naam en locatie die is opgegeven in de wizard.

6.  Gebruik een van de volgende methoden om het certificaat dat wordt gebruikt voor het ondertekenen van de updatecatalogus aan elke clientcomputer die WUA gebruiken om te scannen voor de updates in de catalogus worden toegevoegd. Voeg het certificaat op de clientcomputer toe:

    -   Voor zelf-ondertekende certificaten: Het certificaat toevoegen aan de **Trusted Root Certification Authorities** en **vertrouwde uitgevers** certificaatarchieven.

    -   Voor de certificeringsinstantie (CA) uitgegeven certificaten: Het certificaat toevoegen aan de **vertrouwde uitgevers** certificaatarchief.

    > [!NOTE]
    > De WUA controleert ook of de **ondertekende inhoud van de locatie van Microsoft update intranet toestaan** instelling voor Groepsbeleid is ingeschakeld op de lokale computer. Deze beleidsinstelling moet worden ingeschakeld voor WUA om te scannen naar de updates die zijn gemaakt en gepubliceerd met Updates Publisher. Zie voor meer informatie over het inschakelen van deze groepsbeleidinstelling [het configureren van het groepsbeleid op clientcomputers] (https://technet.microsoft.com/library/bb530967.aspx(d=robot).



## <a name="configuring-group-policy-to-allow-wua-on-computers-to-scan-for-published-updates"></a>Groepsbeleid WUA op computers die u wilt zoeken naar gepubliceerde updates toestaan configureren
Voordat u de Windows Update Agent (WUA) op computers gaat scannen op updates die zijn gemaakt en gepubliceerd met Updates Publisher, moet u een beleidsinstelling ingeschakeld ondertekende inhoud van een intranetlocatie Microsoft update-service. Als de beleidsinstelling is ingeschakeld, accepteert WUA updates via een intranetlocatie ontvangen als de updates zijn ondertekend in het **vertrouwde uitgevers** certificaatarchief op de lokale computer. Er zijn verschillende methoden voor het configureren van Groepsbeleid op computers in de omgeving.

Voor computers die zich niet op het domein, kan op een registersleutelinstelling waarmee ondertekende inhoud van de locatie van Microsoft-updateservice in intranet worden geconfigureerd.

De volgende procedures bevatten de eenvoudige stappen waarmee u Groepsbeleid configureren voor computers in het domein en een registersleutelwaarde op computers die zich niet op het domein.

### <a name="to-configure-group-policy-to-allow-wua-to-scan-for-published-updates"></a>Als u wilt configureren, Groepsbeleid zodat WUA om te scannen voor gepubliceerde updates
1.  Open de module Group Policy Object Editor Microsoft Management Console (MMC) met een gebruiker met de juiste beveiligingsrechten Groepsbeleid configureren.

2.  Klik op **Bladeren** en selecteert u het domein, organisatie-eenheid of GPO's die zijn gekoppeld aan de site waar het geconfigureerde Groepsbeleid worden doorgegeven aan de gewenste clientcomputers. Klik op **OK**, klikt u op **voltooien**, klikt u op **sluiten**, en klik vervolgens op **OK**.

3.  Vouw de geselecteerde instelling is ingeschakeld in de consolestructuur uit, vouw **Computerconfiguratie**, vouw **Beheersjablonen**, vouw **Windows-onderdelen**, en klik vervolgens op **Windows Update**.

4.  In het resultatenvenster met de rechtermuisknop op **ondertekende inhoud van de locatie van Microsoft update intranet toestaan**, klikt u op **eigenschappen**, klikt u op **ingeschakeld**, en klik vervolgens op **OK**.

