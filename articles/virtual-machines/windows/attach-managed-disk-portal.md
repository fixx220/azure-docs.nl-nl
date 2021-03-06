---
title: Een beheerde gegevensschijf koppelen aan een virtuele machine van Windows - Azure | Microsoft Docs
description: Klik hier voor meer informatie over het nieuwe beheerde gegevensschijf koppelen aan een virtuele machine van Windows in de Azure portal met het implementatiemodel van Resource Manager.
services: virtual-machines-windows
documentationcenter: 
author: cynthn
manager: timlt
editor: 
tags: azure-resource-manager
ms.assetid: 
ms.service: virtual-machines-windows
ms.workload: infrastructure-services
ms.tgt_pltfrm: vm-windows
ms.devlang: na
ms.topic: article
ms.date: 05/09/2017
ms.author: cynthn
ms.openlocfilehash: f0cf88a06c5470ef173b22e7213419a6c8760723
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/11/2017
---
# <a name="how-to-attach-a-managed-data-disk-to-a-windows-vm-in-the-azure-portal"></a>Hoe u een beheerde gegevensschijf koppelen aan een virtuele machine van Windows in de Azure portal

In dit artikel leest u hoe een nieuwe beheerde gegevensschijf koppelen aan Windows virtuele machines via de Azure-portal. Voordat u dit doet, controleert u de volgende tips:

* De omvang van de virtuele machine bepaalt hoeveel gegevensschijven die u kunt koppelen. Zie voor meer informatie [grootten voor virtuele machines](sizes.md).
* Voor een nieuwe schijf hoeft u niet eerst maken omdat Azure gemaakt wanneer u dit aansluit.

U kunt ook [een gegevensschijf met behulp van Powershell koppelen](attach-disk-ps.md).



## <a name="add-a-data-disk"></a>Een gegevensschijf toevoegen
1. Klik in het menu aan de linkerkant op **virtuele Machines**.
2. Selecteer de virtuele machine in de lijst.
3. Klik op de virtuele machineblade **schijven**.
   4. Op de **schijven** blade, klikt u op **+ gegevensschijf toevoegen**.
5. Selecteer in de vervolgkeuzelijst voor de nieuwe schijf, **maken leeg**.
6. In de **-beheerde schijven maken** blade, typ een naam voor de schijf en pas deze zo nodig de overige instellingen. Wanneer u klaar bent, klikt u op **maken**.
7. In de **schijven** blade, klik op Opslaan om de schijfconfiguratie van de nieuwe voor de virtuele machine op te slaan.
6. Nadat Azure de schijf wordt gemaakt en gekoppeld aan de virtuele machine, de nieuwe schijf wordt weergegeven in de instellingen voor de schijf van de virtuele machine onder **gegevensschijven**.


## <a name="initialize-a-new-data-disk"></a>Initialiseer de gegevensschijf van een nieuwe

1. Verbinding maken met de virtuele machine.
1. Klik op het startmenu in de virtuele machine en het type **diskmgmt.msc** en treffers **Enter**. Hiermee wordt de module Schijfbeheer gestart.
2. Schijfbeheer constateert dat er een nieuwe, niet-geïnitialiseerde schijf en de schijf initialiseren-venster.
3. Zorg ervoor dat de nieuwe schijf is geselecteerd en klik op **OK** voor het initialiseren.
4. De nieuwe schijf wordt nu weergegeven als **niet-toegewezen**. Klik met de rechtermuisknop op de schijf en selecteer **Nieuw eenvoudig volume**. De **Wizard Nieuw eenvoudig Volume** wordt gestart.
5. Doorloop de wizard, alle standaardinstellingen, houden wanneer u klaar bent Selecteer **voltooien**.
6. Sluit de module Schijfbeheer.
7. U ontvangt een pop-upvenster die u de nieuwe schijf formatteren moet voordat u deze kunt gebruiken. Klik op **schijf formatteren**.
8. In de **nieuwe schijf formatteren** dialoogvenster, Controleer de instellingen en klik vervolgens op **Start**.
9. U ontvangt een waarschuwing dat de schijven formatteren worden alle gegevens wilt wissen, klikt u op **OK**.
10. Wanneer de indeling voltooid is, klikt u op **OK**.

## <a name="use-trim-with-standard-storage"></a>Gebruik TRIM met standard-opslag

Als u een standard-opslag (HDD) gebruikt, moet u TRIM inschakelen. TRIM worden niet-gebruikte blokken op de schijf verwijderd, zodat u wordt alleen gefactureerd voor opslag die u daadwerkelijk gebruikt. Dit kunt besparen op kosten als u grote bestanden maken en deze vervolgens te verwijderen. 

U kunt deze opdracht om te controleren van de beperkende instelling uitvoeren. Open een opdrachtprompt op de virtuele machine van Windows en typ:

```
fsutil behavior query DisableDeleteNotify
```

Als de opdracht 0 retourneert, wordt ' trim ' correct ingeschakeld. Als deze 1 retourneert, voert u de volgende opdracht voor het vrijmaken van opslagruimte inschakelen:
```
fsutil behavior set DisableDeleteNotify 0
```

Na het verwijderen van gegevens van de schijf, kunt u ervoor zorgen dat de beperkende leegmaken goed door het uitvoeren van bewerkingen met ' trim ' defragmentatie:

```
defrag.exe <volume:> -l
```

U kunt er ook voor zorgen dat het hele volume wordt verkleind door het formatteren van het volume.

## <a name="next-steps"></a>Volgende stappen
Als u een toepassing gebruikt de D: station voor het opslaan van gegevens, kunt u [wijzigen van de stationsletter van de tijdelijke schijf Windows](change-drive-letter.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json).
