---
title: Beheer op basis van rollen configureren | Microsoft Docs
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 57413dd3-b2f8-4a5f-b27f-8464d357caff
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3eea3a6e5f23808570ded4be3bd7412954518b96
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2017
---
# <a name="configure-role-based-administration-for-system-center-configuration-manager"></a>Beheer op basis van rollen voor System Center Configuration Manager configureren   

*Van toepassing op: System Center Configuration Manager (huidige vertakking)*

In System Center Configuration Manager beheer op basis van rollen combineert beveiligingsrollen, beveiligingsbereiken en toegewezen verzamelingen om het beheerbereik voor elke gebruiker met beheerdersrechten te definiëren. Een beheerbereik bevat de objecten die een gebruiker met beheerdersrechten in de Configuration Manager-console en de taken gerelateerd aan die objecten bekijken kan dat de gebruiker met beheerdersrechten is gemachtigd om uit te voeren. Configuraties voor beheer op basis van rollen worden toegepast op elke site in een hiërarchie.  

 Als u niet nog bekend met concepten voor beheer op basis van rollen bent, Zie [basisprincipes van beheer op basis van rollen voor System Center Configuration Manager](../../../../core/understand/fundamentals-of-role-based-administration.md).  

 De informatie in de volgende procedures kunt u maken en configureren van beheer op basis van rollen en overeenkomstige beveiligingsinstellingen:  

-   [Aangepaste beveiligingsrollen maken](#BKMK_CreateSecRole)  

-   [Beveiligingsrollen configureren](#BKMK_ConfigSecRole)  

-   [Beveiligingsbereiken voor een object configureren](#BKMK_ConfigSecScope)  

-   [Verzamelingen voor het beheren van beveiliging configureren](#BKMK_ConfigColl)  

-   [Een nieuwe gebruiker met beheerdersrechten maken](#BKMK_Create_AdminUser)  

-   [Het beheerbereik van een gebruiker met beheerdersrechten wijzigen](#BKMK_ModAdminUser)  

##  <a name="BKMK_CreateSecRole"></a> Aangepaste beveiligingsrollen maken  
 Configuration Manager biedt diverse ingebouwde beveiligingsrollen. Indien u bijkomende beveiligingsrollen nodig hebt, kunt u een aangepaste beveiligingsrol maken door een kopie te maken van een bestaande beveiligingsrol en dan de kopie te wijzigen. U kunt een aangepaste beveiligingsrol voor het verlenen van gebruikers met beheerdersrechten de bijkomende beveiligingsmachtigingen die ze nodig hebben die niet zijn opgenomen in een huidige, toegewezen beveiligingsrol maken. Door een aangepaste beveiligingsrol te gebruiken, verleent u hen enkel de machtigingen die ze nodig hebben, en vermijdt u een beveiligingsrol toe te wijzen die meer machtigingen verleent dan ze nodig hebben.  

 Gebruik de volgende procedure om een nieuwe beveiligingsrol te maken door gebruik te maken van een bestaande beveiligingsrol als sjabloon.  

#### <a name="to-create-custom-security-roles"></a>Aangepaste beveiligingsrollen maken  

1.  Ga in de Configuration Manager-console naar **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **beveiligingsrollen**.  

     Gebruik één van de volgende processen om de nieuwe beveiligingsrol te maken:  

    -   Voer de volgende acties uit om een aangepaste beveiligingsrol te maken:  

        1.  Selecteer een bestaande beveiligingsrol om die te gebruiken voor de nieuwe beveiligingsrol.  

        2.  Op de **Start** tabblad, in de **beveiligingsrol** groep, kiest u **kopie**. Hiermee maakt u een kopie van de bronbeveiligingsrol.  

        3.  Geef in de wizard Beveiligingsrol kopiëren een **Naam** op voor de nieuwe aangepaste beveiligingsrol.  

        4.  Vouw in **Toewijzingen beveiligingsbewerking**het knooppunt **Beveiligingsbewerkingen** uit om de beschikbare acties weer te geven.  

        5.  U wijzigt de instelling voor een beveiligingsbewerking, kies de pijl omlaag in de **waarde** kolom en kiest u **Ja** of **Nee**.  

            > [!CAUTION]  
            >  Wanneer u een aangepaste beveiligingsrol configureert, moet u ervoor zorgen dat u geen machtigingen die niet zijn vereist voor gebruikers met beheerdersrechten die gekoppeld aan de nieuwe beveiligingsrol zijn. Bijvoorbeeld, de **wijzigen** waarde voor de **beveiligingsrollen** beveiligingsbewerking gebruikers met beheerdersrechten verleent machtigingen om te bewerken van een beschikbare beveiligingsrol – zelfs als ze niet gekoppeld aan deze beveiligingsrol zijn.  

        6.  Nadat u de machtigingen configureren, kiest u **OK** om op te slaan van de nieuwe beveiligingsrol.  

    -   Als u wilt importeren in een beveiligingsrol die is geëxporteerd uit een andere Configuration Manager-hiërarchie, kunt u de volgende acties uitvoeren:  

        1.  Op de **Start** tabblad, in de **maken** groep, kiest u **beveiligingsrol importeren**.  

        2.  Geef het .xml-bestand met de configuratie van de beveiligingsrol die u wilt importeren. Kies **Open** voert u de procedure en opslaan van de beveiligingsrol.  

            > [!NOTE]  
            >  Nadat u een beveiligingsrol importeert, kunt u de eigenschappen van de beveiligingsrol bewerken om de objectmachtigingen te wijzigen die zijn gekoppeld aan de beveiligingsrol.  

##  <a name="BKMK_ConfigSecRole"></a> Beveiligingsrollen configureren  
 De groepen van beveiligingsmachtiging die gedefinieerd zijn voor een beveiligingsmachtigingen worden beveiligingsbewerkingstoewijzingen genoemd. Beveiligingsbewerkingstoewijzingen vertegenwoordigen een combinatie van objecttypes en -acties die beschikbaar zijn voor elk type object. U kunt wijzigen welke beveiligingsbewerkingen beschikbaar zijn voor een aangepaste beveiligingsrol, maar u kunt de ingebouwde beveiligingsrollen waarmee Configuration Manager niet wijzigen.  

 Gebruik de volgende procedure om de beveiligingsbewerkingen te wijzigen voor een beveiligingsrol.  

#### <a name="to-modify-security-roles"></a>Beveiligingsrollen wijzigen  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **beveiligingsrollen**.  

3.  Selecteer de aangepaste beveiligingsrol die u wilt wijzigen.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  Kies de **machtigingen** tabblad.  

6.  Vouw in **Toewijzingen beveiligingsbewerking**het knooppunt **Beveiligingsbewerkingen** uit om de beschikbare acties weer te geven.  

7.  U wijzigt de instelling voor een beveiligingsbewerking, kies de pijl omlaag in de **waarde** kolom, en kies vervolgens een **Ja** of **Nee**.  

    > [!CAUTION]  
    >  Wanneer u een aangepaste beveiligingsrol configureert, moet u ervoor zorgen dat u geen machtigingen die niet zijn vereist voor gebruikers met beheerdersrechten die gekoppeld aan de nieuwe beveiligingsrol zijn. Bijvoorbeeld, de **wijzigen** waarde voor de **beveiligingsrollen** beveiligingsbewerking gebruikers met beheerdersrechten verleent machtigingen om te bewerken van een beschikbare beveiligingsrol – zelfs als ze niet gekoppeld aan deze beveiligingsrol zijn.  

8.  Wanneer u klaar bent met het configureren van beveiligingsbewerkingstoewijzingen, kiezen **OK** om op te slaan van de nieuwe beveiligingsrol.  

##  <a name="BKMK_ConfigSecScope"></a> Beveiligingsbereiken voor een object configureren  
 Bij het beheren van de koppeling van een beveiligingsbereik voor een object van het object: niet van het beveiligingsbereik. De enige directe configuraties die beveiligingsbereiken ondersteunen zijn wijzigingen aan zijn naam en beschrijving. Om de naam en beschrijving van een beveiligingsbereik te wijzigen wanneer u de eigenschappen van het beveiligingsbereik ziet, moet u de **Wijzig** -machtiging hebben voor het met **Beveiligingsbereiken** te beveiligen object.  

 Wanneer u een nieuw object in Configuration Manager maakt, het nieuwe object is gekoppeld aan elke beveiligingsrol die is gekoppeld aan de beveiligingsrollen van de account die wordt gebruikt voor het maken van het object – wanneer deze beveiligingsrollen bieden de **maken** machtiging of **beveiligingsbereik instellen** machtiging. De beveiligingsbereiken die het object is gekoppeld aan nadat deze gemaakt, kunt u alleen wijzigen.  

 Als u bijvoorbeeld krijgt u een beveiligingsrol die u machtiging verleent voor het maken van een nieuwe grensgroep. Wanneer u een nieuwe grensgroep maakt, hebt u geen optie die u kunt specifieke beveiligingsbereiken toewijzen. In plaats daarvan worden de beveiligingsbereiken die beschikbaar zijn vanuit de beveiligingsrollen die zijn gekoppeld, automatisch toegewezen aan de nieuwe grensgroep. Nadat u de nieuwe grensgroep opslaat, kunt u de beveiligingsbereiken die gekoppeld aan de nieuwe grensgroep zijn bewerken.  

 Gebruik de volgende procedure voor het configureren van de beveiligingsbereiken die zijn toegewezen aan een object.  

#### <a name="to-configure-security-scopes-for-an-object"></a>Beveiligingsbereiken voor een object configureren  

1.  Selecteer een object dat wordt toegewezen aan een beveiligingsbereik ondersteunt in de Configuration Manager-console.  

2.  Op de **Start** tabblad, in de **classificeren** groep, kiest u **Beveiligingsbereiken instellen**.  

3.  Selecteer of wis de beveiligingsbereiken waarmee dit object is gekoppeld in het dialoogvenster **Beveiligingsbereiken instellen** . Elk object dat beveiligingsbereiken ondersteunt, moet toegewezen zijn aan minstens één beveiligingsbereik.  

4.  Kies **OK** om op te slaan van de toegewezen beveiligingsbereiken.  

    > [!NOTE]  
    >  Wanneer u een nieuw object maakt, moet u het object toewijzen aan verschillende beveiligingsbereiken. Voor het wijzigen van het aantal beveiligingsbereiken die gekoppeld aan het object zijn, moet u deze toewijzing wijzigen nadat het object is gemaakt.  

##  <a name="BKMK_ConfigColl"></a> Verzamelingen voor het beheren van beveiliging configureren  
 Er zijn geen procedures voor het configureren van verzamelingen voor rolgebaseerd beheer. Verzamelingen beschikt niet over de configuratie van een op rollen gebaseerd beheer. In plaats daarvan, wijst u verzamelingen aan een gebruiker met beheerdersrechten bij het configureren van de gebruiker met beheerdersrechten. De verzameling beveiligingsbewerkingen die zijn ingeschakeld op de gebruiker toegewezen beveiligingsrollen bepalen de machtigingen die een gebruiker met beheerdersrechten voor verzamelingen en verzamelingbronnen (verzamelingsleden heeft).  

 Wanneer een gebruiker met beheerdersrechten machtigingen heeft voor een verzameling, heeft hij ook machtigingen voor verzamelingen die beperkt zijn tot deze verzameling. Als u bijvoorbeeld uw organisatie gebruikmaakt van een verzameling met de naam alle bureaubladen en er is een verzameling met de naam alle bureaubladen van Noord-Amerika die is beperkt tot de verzameling alle bureaubladen. Indien een gebruiker met beheerdersrechten machtigingen heeft tot Alle bureaubladen, hebben ze ook dezelfde machtigingen tot de verzameling Alle bureaubladen van Noord-Amerika.

 Bovendien een gebruiker met beheerdersrechten kan niet via de **verwijderen** of **wijzigen** toegang tot een verzameling die rechtstreeks aan hen is toegewezen. Maar ze kunnen deze machtigingen gebruiken op de verzamelingen die beperkt tot deze verzameling zijn. In het vorige voorbeeld wordt de gebruiker met beheerdersrechten kunt verwijderen of wijzigen van de verzameling alle bureaubladen van Noord-Amerika, maar ze niet verwijderen of wijzigen van de verzameling alle bureaubladen.  

##  <a name="BKMK_Create_AdminUser"></a> Een nieuwe gebruiker met beheerdersrechten maken  
 Maken van een gebruiker met beheerdersrechten in Configuration Manager wilt verlenen aan individuen of leden van een groep beveiligingstoegang voor het beheren van Configuration Manager, en geef de Windows-account van de gebruiker of gebruikersgroep. Elke gebruiker met beheerdersrechten in Configuration Manager moet ten minste één beveiligingsrol en één beveiligingsbereik worden toegewezen. U kunt tevens verzamelingen toewijzen om het beheerbereik van de gebruiker met beheerdersrechten te beperken.  

 Gebruik de volgende procedures om nieuwe gebruikers met beheerdersrechten te maken.  

#### <a name="to-create-a-new-administrative-user"></a>Maken van een nieuwe gebruiker met beheerdersrechten  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **gebruikers met beheerdersrechten**.  

3.  Op de **Start** tabblad, in de **maken** groep, kiest u **gebruiker of groep toevoegen**.  

4.  Kies **Bladeren**, en selecteer vervolgens het gebruikersaccount of de groep voor deze nieuwe gebruiker met beheerdersrechten.  

    > [!NOTE]  
    >  Bij beheer via de console kunnen alleen domeingebruikers of beveiligingsgroepen worden gespecificeerd als een gebruiker met beheerdersrechten.  

5.  Voor **beveiligingsrollen die zijn gekoppeld**, kies **toevoegen** voor een lijst van de beschikbare beveiligingsrollen, schakel het selectievakje voor een of meer beveiligingsrollen en kies vervolgens **OK**.  

6.  Kies een van de volgende twee opties voor het definiëren van het gedrag van het beveiligbare object voor de nieuwe gebruiker:  

    -   **Alle beveiligbare objecten die relevant voor hun gekoppelde beveiligingsrollen zijn**: Deze optie koppelt de gebruiker met beheerdersrechten de **alle** beveiligingsbereik en de op basisniveau ingebouwde verzamelingen voor **alle systemen** en **alle gebruikers en gebruikersgroepen**. De aan de gebruiker toegewezen beveiligingsrollen definiëren de toegang tot objecten. Nieuwe objecten die door deze gebruiker met beheerdersrechten worden gemaakt, worden toegewezen aan het beveiligingsbereik **Standaard** .  

    -   **Alleen beveiligbare objecten in gespecificeerde beveiligingsbereiken of verzamelingen**: Standaard deze optie koppelt de gebruiker met beheerdersrechten de **standaard** beveiligingsbereik, en de **alle systemen** en **alle gebruikers en gebruikersgroepen** verzamelingen. De werkelijke beveiligingsbereiken en verzamelingen zijn echter beperkt tot die welke gekoppeld zijn aan het account dat u hebt gebruikt om de nieuwe gebruiker met beheerdersrechten te maken. Deze optie ondersteunt het toevoegen of verwijderen van beveiligingsbereiken en verzamelingen om het beheerbereik van de gebruiker met beheerdersrechten aan te passen.  

    > [!IMPORTANT]  
    >  De voorgaande opties koppelen elk toegewezen beveiligingsbereik en verzameling aan elke beveiligingsrol die is toegewezen aan de gebruiker met beheerdersrechten. U kunt een derde optie **alleen beveiligbare objecten zoals bepaald door de beveiligingsrollen van de gebruiker met beheerdersrechten**, om individuele beveiligingsrollen aan specifieke beveiligingsbereiken en verzamelingen te koppelen. Deze derde optie is beschikbaar nadat u de nieuwe gebruiker met beheerdersrechten maakt, wanneer u de gebruiker met beheerdersrechten wijzigt.  

7.  Voer, afhankelijk van uw selectie in stap 6, de volgende handeling uit:  

    -   Als u hebt geselecteerd **alle beveiligbare objecten die relevant voor hun gekoppelde beveiligingsrollen zijn**, kies **OK** om deze procedure te voltooien.  

    -   Als u hebt geselecteerd **alleen beveiligbare objecten in gespecificeerde beveiligingsbereiken of verzamelingen**, kunt u **toevoegen** aanvullende verzamelingen en beveiligingsrollen te selecteren. Of Selecteer een of meer objecten in de lijst en kies vervolgens **verwijderen** om ze te verwijderen. Kies **OK** om deze procedure te voltooien.  

##  <a name="BKMK_ModAdminUser"></a> Het beheerbereik van een gebruiker met beheerdersrechten wijzigen  
 U kunt het beheerbereik van een gebruiker met beheerdersrechten wijzigen door beveiligingsrollen, beveiligingsbereiken, en verzamelingen die aan de gebruiker gekoppeld zijn, toe te voegen of te verwijderen. Aan elke gebruiker met beheerdersrechten moet minimaal één beveiligingsrol en één beveiligingsbereik zijn gekoppeld. Mogelijk moet u één of meer verzamelingen aan het beheerbereik van de gebruiker toewijzen. De meeste beveiligingsrollen communiceren met verzamelingen en werken goed zonder een toegewezen verzameling niet.  

 Wanneer u een gebruiker met beheerdersrechten wijzigt, kunt u het gedrag wijzigen voor hoe beveiligbare objecten zijn gekoppeld aan de toegewezen beveiligingsrollen. Dit zijn de drie soorten gedrag die u kunt selecteren:  

-   **Alle beveiligbare objecten die relevant voor hun gekoppelde beveiligingsrollen zijn**: Deze optie koppelt de gebruiker met beheerdersrechten de **alle** bereik en de op basisniveau ingebouwde verzamelingen voor niveau **alle systemen** en **alle gebruikers en gebruikersgroepen**. De aan de gebruiker toegewezen beveiligingsrollen definiëren de toegang tot objecten.  

-   **Alleen beveiligbare objecten in gespecificeerde beveiligingsbereiken of verzamelingen**: Deze optie koppelt de gebruiker met beheerdersrechten aan dezelfde beveiligingsbereiken en verzamelingen die gekoppeld aan het account dat u gebruikt zijn voor het configureren van de gebruiker met beheerdersrechten. Deze optie ondersteunt het toevoegen of verwijderen van beveiligingsrollen en verzamelingen om het beheerbereik van de gebruiker met beheerdersrechten aan te passen.  

-   **Alleen beveiligbare objecten zoals bepaald door de beveiligingsrollen van de gebruiker met beheerdersrechten**: Deze optie kunt u specifieke koppelingen tussen individuele beveiligingsrollen en specifieke beveiligingsbereiken en verzamelingen voor de gebruiker.  

    > [!NOTE]  
    >  Deze optie is alleen beschikbaar wanneer u de eigenschappen van een gebruiker met beheerdersrechten wijzigt.  

De huidige configuratie voor het gedrag van het beveiligbare object verandert het proces dat u gebruikt om aanvullende beveiligingsrollen toe te wijzen. Gebruik de volgende procedures die gebaseerd zijn op de verschillende opties voor beveiligbare objecten om u te helpen een gebruiker met beheerdersrechten te beheren.  

Gebruik de volgende procedure om te bekijken en beheren van de configuratie voor beveiligbare objecten voor een gebruiker met beheerdersrechten.  

#### <a name="to-view-and-manage-the-securable-object-behavior-for-an-administrative-user"></a>Bekijken en beheren van het gedrag van een beveiligbaar object voor een gebruiker met beheerdersrechten  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **gebruikers met beheerdersrechten**.  

3.  Selecteer de gebruiker met beheerdersrechten die u wilt wijzigen.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  Kies de **Beveiligingsbereiken** tabblad om de huidige configuratie voor beveiligbare objecten voor deze gebruiker met beheerdersrechten.  

6.  Om het gedrag van een beveiligbaar object te wijzigen, selecteert u een nieuwe optie voor het gedrag van een beveiligbaar object. Nadat u deze configuratie wijzigen, raadpleegt u de juiste procedure voor verdere richtlijnen voor het configureren van beveiligingsbereiken en verzamelingen en beveiligingsrollen voor deze gebruiker met beheerdersrechten.  

7.  Kies **OK** om de procedure te voltooien.  

De volgende procedure gebruiken om te wijzigen van een gebruiker met beheerdersrechten die het gedrag van het beveiligbare object ingesteld op heeft **alle beveiligbare objecten die relevant voor hun gekoppelde beveiligingsrollen zijn**.  

#### <a name="for-option-all-securable-objects-that-are-relevant-to-their-associated-security-roles"></a>Voor de optie: Alle beveiligbare objecten die relevant voor hun gekoppelde beveiligingsrollen zijn  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **gebruikers met beheerdersrechten**.  

3.  Selecteer de gebruiker met beheerdersrechten die u wilt wijzigen.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  Kies de **Beveiligingsbereiken** tab om te bevestigen dat de gebruiker met beheerdersrechten geconfigureerd is voor **alle beveiligbare objecten die relevant voor hun gekoppelde beveiligingsrollen zijn**.  

6.  Voor het wijzigen van de toegewezen beveiligingsrollen, kies de **beveiligingsrollen** tabblad.  

    -   Om aanvullende beveiligingsrollen aan deze gebruiker met beheerdersrechten toewijzen, kies **toevoegen**, schakel het selectievakje voor elke aanvullende beveiligingsrol die u wilt toewijzen, en kies vervolgens **OK**.  

    -   Om beveiligingsrollen te verwijderen, selecteert u een of meer beveiligingsrollen uit de lijst en kies vervolgens **verwijderen**.  

7.  Voor het wijzigen van het gedrag van het beveiligbare object, kies de **Beveiligingsbereiken** tabblad en kiest u een nieuwe optie voor het gedrag van het beveiligbare object. Nadat u deze configuratie wijzigen, raadpleegt u de juiste procedure voor verdere richtlijnen voor het configureren van beveiligingsbereiken en verzamelingen en beveiligingsrollen voor deze gebruiker met beheerdersrechten.  

    > [!NOTE]  
    >  Wanneer het gedrag van het beveiligbare object is ingesteld op **alle beveiligbare objecten die relevant voor hun gekoppelde beveiligingsrollen zijn**, kunt u toevoegen of verwijderen van specifieke beveiligingsbereiken en verzamelingen.  

8.  Kies **OK** om deze procedure te voltooien.  

Gebruik de volgende procedure om een gebruiker met beheerdersrechten te wijzigen voor wie het gedrag van beveiligbare objecten op **Alleen beveiligbare objecten in gespecificeerde beveiligingsbereiken of verzamelingen**is ingesteld:  

#### <a name="for-option-only-securable-objects-in-specified-security-scopes-or-collections"></a>Voor de optie: Alleen beveiligbare objecten in gespecificeerde beveiligingsbereiken of verzamelingen  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **gebruikers met beheerdersrechten**.  

3.  Selecteer de gebruiker met beheerdersrechten die u wilt wijzigen.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  Kies de **Beveiligingsbereiken** tabblad om te bevestigen dat de gebruiker is geconfigureerd voor **alleen beveiligbare objecten in gespecificeerde beveiligingsbereiken of verzamelingen**.  

6.  Voor het wijzigen van de toegewezen beveiligingsrollen, kies de **beveiligingsrollen** tabblad.  

    -   Om aanvullende beveiligingsrollen aan deze gebruiker toewijst, kies **toevoegen**, schakel het selectievakje voor elke aanvullende beveiligingsrol die u wilt toewijzen, en kies vervolgens **OK**.  

    -   Om beveiligingsrollen te verwijderen, selecteert u een of meer beveiligingsrollen uit de lijst en kies vervolgens **verwijderen**.  

7.  Voor het wijzigen van de beveiligingsbereiken en verzamelingen die gekoppeld aan beveiligingsrollen zijn, kies de **Beveiligingsbereiken** tabblad.  

    -   Om nieuwe beveiligingsbereiken of verzamelingen koppelen aan alle beveiligingsrollen die zijn toegewezen aan deze gebruiker met beheerdersrechten, kies **toevoegen** en selecteer een van de vier opties. Als u selecteert **beveiligingsbereik** of **verzameling**, schakel het selectievakje voor een of meer objecten die selectie te voltooien en klik vervolgens op **OK**.  

    -   Als u wilt een beveiligingsbereik of verzameling verwijderen, kiest u het object en kies vervolgens **verwijderen**.  

8.  Kies **OK** om deze procedure te voltooien.  

Gebruik de volgende procedure om een gebruiker met beheerdersrechten te wijzigen voor wie het gedrag van beveiligbare objecten op **Alleen beveiligbare objecten zoals bepaald door de beveiligingsrollen van de gebruiker met beheerdersrechten**is ingesteld:  

#### <a name="for-option-only-securable-objects-as-determined-by-the-security-roles-of-the-administrative-user"></a>Voor de optie: Alleen beveiligbare objecten zoals bepaald door de beveiligingsrollen van de gebruiker met beheerdersrechten  

1.  Kies in de Configuration Manager-console **beheer**.  

2.  In de **beheer** werkruimte Vouw **beveiliging**, en kies vervolgens **gebruikers met beheerdersrechten**.  

3.  Selecteer de gebruiker met beheerdersrechten die u wilt wijzigen.  

4.  Op de **Start** tabblad, in de **eigenschappen** groep, kiest u **eigenschappen**.  

5.  Kies de **Beveiligingsbereiken** tab om te bevestigen dat de gebruiker met beheerdersrechten geconfigureerd is voor **alleen beveiligbare objecten in gespecificeerde beveiligingsbereiken of verzamelingen**.  

6.  Voor het wijzigen van de toegewezen beveiligingsrollen, kies de **beveiligingsrollen** tabblad.  

    -   Om aanvullende beveiligingsrollen aan deze gebruiker met beheerdersrechten toewijzen, kies **toevoegen**. Op de **beveiligingsrol toevoegen** in het dialoogvenster, selecteer een of meer beschikbare beveiligingsrollen, kies **toevoegen**, en selecteer een object dat aan de geselecteerde beveiligingsrollen wilt koppelen. Als u selecteert **beveiligingsbereik** of **verzameling**, schakel het selectievakje voor een of meer objecten die selectie te voltooien en klik vervolgens op **OK**.  

        > [!NOTE]  
        >  U moet minimaal één beveiligingsbereik configureren voordat de geselecteerde beveiligingsrollen aan de gebruiker met beheerdersrechten kunnen worden toegewezen. Wanneer u meerdere beveiligingsrollen selecteert, wordt elk beveiligingsbereik en elke verzameling die u configureert gekoppeld aan elk van deze geselecteerde beveiligingsrollen.  

    -   Om beveiligingsrollen te verwijderen, selecteert u een of meer beveiligingsrollen uit de lijst en kies vervolgens **verwijderen**.  

7.  Voor het wijzigen van de beveiligingsbereiken en verzamelingen die gekoppeld aan een specifieke beveiligingsrol zijn, kies de **Beveiligingsbereiken** tabblad, selecteert u de beveiligingsrol en kies vervolgens **bewerken**.  

    -   Kies nieuwe om objecten te koppelen aan deze beveiligingsrol, **toevoegen**, en selecteer een object dat aan de geselecteerde beveiligingsrollen wilt koppelen. Als u selecteert **beveiligingsbereik** of **verzameling**, schakel het selectievakje voor een of meer objecten die selectie te voltooien en klik vervolgens op **OK**.  

        > [!NOTE]  
        >  U moet ten minste één beveiligingsbereik configureren.  

    -   Als u wilt verwijderen een beveiligingsbereik of verzameling die is gekoppeld aan deze beveiligingsrol is toegekend, selecteert u het object en kies vervolgens **verwijderen**.  

    -   Wanneer u klaar bent met het wijzigen van de gekoppelde objecten, kiezen **OK**.  

8.  Kies **OK** om deze procedure te voltooien.  

    > [!CAUTION]  
    >  Wanneer een beveiligingsrol gebruikers met beheerdersrechten de machtiging voor het implementeren van verzamelingen verleent, kunnen die gebruikers met beheerdersrechten objecten distribueren uit elk beveiligingsbereik waarvoor ze een **leesmachtiging** hebben, ook als dat beveiligingsbereik gekoppeld is aan een andere beveiligingsrol.  
