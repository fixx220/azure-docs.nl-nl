---
title: Update 5 StorSimple 8000 series apparaat klassieke portal installeren | Microsoft Docs
description: Legt uit hoe StorSimple 8000 Series Update 5 op uw StorSimple 8000 serie-apparaat in de klassieke portal installeert.
services: storsimple
documentationcenter: NA
author: alkohli
manager: timlt
editor: 
ms.assetid: 
ms.service: storsimple
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: TBD
ms.date: 10/10/2017
ms.author: alkohli
ms.openlocfilehash: 9d8dc7aebbeea7ad428be4af66e4e991f60c8301
ms.sourcegitcommit: d03907a25fb7f22bec6a33c9c91b877897e96197
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/12/2017
---
# <a name="install-update-5-on-your-storsimple-device"></a>Update 5 installeren op uw StorSimple-apparaat

## <a name="overview"></a>Overzicht

Deze zelfstudie wordt uitgelegd hoe Update 5 installeren op een StorSimple-apparaat waarop een eerdere softwareversie wordt uitgevoerd via de klassieke Azure portal en het gebruik van de hotfix-methode. De hotfix-methode wordt gebruikt wanneer u probeert te installeren Update 5 op een apparaat met 3 versies vóór het bijwerken. De hotfix-methode wordt ook gebruikt als een gateway is geconfigureerd op een andere netwerkinterface dan DATA 0 van de StorSimple-apparaat en u probeert bij te werken vanaf een versie 1 vóór het bijwerken.

Update 5 omvat software van apparaten, Storport en Spaceport, OS beveiligingsupdates en updates voor het besturingssysteem en schijf firmware-updates.  Software van het apparaat, Spaceport Storport, beveiliging en andere updates OS ononderbroken updates beschikbaar zijn. De ononderbroken of regelmatige updates kunnen worden toegepast via de klassieke Azure portal of de hotfix-methode. De schijf firmware-updates verstoren updates beschikbaar zijn en worden toegepast wanneer het apparaat in de onderhoudsmodus via de hotfix-methode met de Windows PowerShell-interface van het apparaat.

> [!IMPORTANT]
> * Een aantal handmatige en automatische eerste controles worden uitgevoerd voordat de installatie om te bepalen van de apparaatstatus in termen van hardware-staat en de netwerkverbinding. Deze controles vooraf worden alleen uitgevoerd als u de updates vanuit de Azure-portal toepassen.
> * Als u een eerdere versie dan Update 3 uitvoert, wordt aangeraden dat u Update 5 via de hotfix-methode installeert. Om te leiden u door de update ondersteuning [Meld een ondersteuningsticket](storsimple-8000-contact-microsoft-support.md).
> * Als u werkt met Update 3 en hoger, wordt aangeraden dat u de software en andere regelmatig updates via de klassieke Azure portal installeert. Afhankelijk van de versie die u bijwerkt, de updates kunnen 4 uur duren (of hoger) te installeren. De updates van de modus onderhoud moeten worden geïnstalleerd via de Windows PowerShell-interface van het apparaat. Als u onderhoud modus updates verstoren updates beschikbaar zijn, wordt deze leiden tot een uitvaltijd voor uw apparaat.
> * Als de optionele StorSimple Snapshot Manager wordt uitgevoerd, zorg ervoor dat u uw Snapshot Manager-versie hebt bijgewerkt naar Update 5 vóór het bijwerken van het apparaat.


[!INCLUDE [storsimple-preparing-for-update](../../includes/storsimple-preparing-for-updates.md)]

## <a name="install-update-5-via-the-azure-classic-portal"></a>Update 5 installeren via de klassieke Azure portal
Voer de volgende stappen uit voor het bijwerken van uw apparaat om te [Update 5](storsimple-update5-release-notes.md).

> [!NOTE]
> Microsoft haalt aanvullende diagnostische gegevens van het apparaat. Als gevolg hiervan als onze teamleden identificeert de apparaten die problemen ondervindt, zijn wij beter ingericht voor het verzamelen van informatie van het apparaat en problemen diagnosticeren.

[!INCLUDE [storsimple-install-update2-via-portal](../../includes/storsimple-install-update2-via-portal.md)]

Controleren of uw apparaat wordt uitgevoerd **StorSimple 8000 Series Update 5 (6.3.9600.17845)**. De **datum laatst bijgewerkt** moet worden gewijzigd.

* U ziet nu de onderhoud modus updates zijn beschikbaar (dit bericht kan nog wel weergegeven tot 24 uur nadat u de updates hebt geïnstalleerd). Onderhoud modus updates zijn verstoren updates die leiden tot uitvaltijd apparaat en kunnen alleen worden toegepast via de Windows PowerShell-interface van uw apparaat.

* De modus onderhoud updates downloaden met behulp van de stappen in [downloaden hotfixes](#to-download-hotfixes) zoeken naar en downloaden van KB4037263, welke schijf firmware-updates zijn geïnstalleerd (de andere updates al is geïnstalleerd door nu). Volg de stappen die worden vermeld in [installeren en testen van onderhoud modus hotfixes](#to-install-and-verify-maintenance-mode-hotfixes) updates voor het installeren van de onderhoudsmodus.

## <a name="install-update-5-as-a-hotfix"></a>Update 5 als een hotfix installeren


De softwareversies die kunnen worden bijgewerkt met de hotfix-methode zijn:

* Update 0.1, 0,2, 0,3
* Update 1, 1.1, 1.2
* 2, 2.1, 2.2 bijwerken
* Update 3, 3.1
* Update 4

> [!NOTE]
> De aanbevolen methode voor het installeren van Update 5 is via de klassieke Azure portal. Echter, als u een eerdere versie dan Update 3 uitvoert, wordt aangeraden dat u deze methode gebruikt voor het installeren van Update 5. U moet deze procedure ook gebruiken als u de controle van de gateway niet bij het installeren van de updates via de klassieke Azure portal. De controle mislukt wanneer u een gateway die is toegewezen aan een niet-DATA 0-netwerkinterface en uw apparaat een softwareversie ouder is dan Update 1 wordt uitgevoerd.

De hotfix-methode omvat de volgende drie stappen:

1. De hotfixes downloaden vanaf Microsoft Update-catalogus.
2. Installeren en controleer of de hotfixes normale modus.
3. Installeren en controleer of de hotfix onderhoud-modus.

#### <a name="download-updates-for-your-device"></a>Updates voor uw apparaat downloaden

U moet downloaden en installeren van de volgende hotfixes in de aangegeven volgorde en de voorgestelde mappen:

| Volgorde | KB | Beschrijving | Updatetype | Installatietijd |Installeren in map|
| --- | --- | --- | --- | --- | --- |
| 1. |KB4037264 |Software-update<br> Download beide _HcsSfotwareUpdate.exe_ en _CisMSDAgent.exe_ |Reguliere <br></br>Niet-verstoren |~ 25 minuten |FirstOrderUpdate|

Als u bijwerkt vanaf een apparaat met Update 4, hoeft u alleen de cumulatieve updates voor het besturingssysteem als tweede volgorde updates installeren.

| Volgorde | KB | Beschrijving | Updatetype | Installatietijd |Installeren in map|
| --- | --- | --- | --- | --- | --- |
| 2A. |KB4025336 |OS cumulatieve updates pakket <br> Versie van Windows Server 2012 R2 downloaden |Reguliere <br></br>Niet-verstoren |- |SecondOrderUpdate|

Als installeren vanaf een apparaat met Update 3 of ouder, installeert u de volgende naast de cumulatieve updates.

| Volgorde | KB | Beschrijving | Updatetype | Installatietijd |Installeren in map|
| --- | --- | --- | --- | --- | --- |
| 2B. |KB4011841 <br> KB4011842 |LSI stuurprogramma's en firmware-updates <br> USM firmware-update (versie 3.38) |Reguliere <br></br>Niet-verstoren |~ 3 uur <br> (inclusief 2A. + 2B. (+ 2 C.)|SecondOrderUpdate|
| 2C. |KB3139398 <br> KB3142030 <br> KB3108381 <br> KB3153704 <br> KB3174644 <br> KB3139914   |OS-beveiligingspakket updates <br> Versie van Windows Server 2012 R2 downloaden |Reguliere <br></br>Niet-verstoren |- |SecondOrderUpdate|
| 2D. |KB3146621 <br> KB3103616 <br> KB3121261 <br> KB3123538 |OS-updates-pakket <br> Versie van Windows Server 2012 R2 downloaden |Reguliere <br></br>Niet-verstoren |- |SecondOrderUpdate|


U moet mogelijk ook installeren schijf firmware-updates boven op de updates die zijn aangegeven in de voorgaande tabellen. U kunt controleren of u de schijf firmware-updates door het uitvoeren van moet de `Get-HcsFirmwareVersion` cmdlet. Als u deze firmwareversies: `XMGJ`, `XGEG`, `KZ50`, `F6C2`, `VR08`, `N003`, `0107`, en u niet wilt dat deze updates te installeren.

| Volgorde | KB | Beschrijving | Updatetype | Installatietijd | Installeren in map|
| --- | --- | --- | --- | --- | --- |
| 3. |KB4037263 |Schijf-firmware |Onderhoud <br></br>Verstoren |~ 30 minuten | ThirdOrderUpdate |

<br></br>

> [!IMPORTANT]
> * Als het bijwerken van de Update 4, is de totale installatietijd bijna 4 uur.
> * Voordat u deze procedure de update toe te passen, zorg ervoor dat zowel de apparaatcontrollers online zijn en alle hardwareonderdelen zijn in orde.

De volgende stappen uitvoeren om te downloaden en installeren van hotfixes.

[!INCLUDE [storsimple-install-update5-hotfix](../../includes/storsimple-install-update5-hotfix.md)]

[!INCLUDE [storsimple-install-troubleshooting](../../includes/storsimple-install-troubleshooting.md)]

## <a name="next-steps"></a>Volgende stappen
Meer informatie over de [Update 5 release](storsimple-update5-release-notes.md).

