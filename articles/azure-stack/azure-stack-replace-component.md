---
title: Vervangen van een hardware-onderdeel op een Azure-Stack scale unit knooppunt | Microsoft Docs
description: "Informatie over het vervangen van een hardware-onderdeel op een Azure-Stack geïntegreerd-systeem."
services: azure-stack
documentationcenter: 
author: troettinger
manager: byronr
editor: 
ms.assetid: c6e036bf-8c80-48b5-b2d2-aa7390c1b7c9
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 10/20/2017
ms.author: twooley
ms.openlocfilehash: 430274025bc6cd657a733fb80feb6cd7b39a36f3
ms.sourcegitcommit: cf4c0ad6a628dfcbf5b841896ab3c78b97d4eafd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2017
---
# <a name="replace-a-hardware-component-on-an-azure-stack-scale-unit-node"></a>Vervangen van een hardware-onderdeel op een Azure-Stack scale unit-knooppunt

*Van toepassing op: Azure Stack geïntegreerd systemen*

In dit artikel beschrijft het algemene proces ter vervanging van hardwareonderdelen die niet hot-verwisselbare zijn. Werkelijke vervanging stappen varieert gebaseerd op uw hardwareleverancier oorspronkelijke leveranciers (OEM). Raadpleeg uw leverancier veld FRU (replaceable unit)-documentatie voor gedetailleerde stappen die specifiek voor uw Azure-Stack geïntegreerd systeem zijn.

Niet hot-verwisselbare onderdelen omvatten het volgende:

- CPU *
- Geheugen *
- Moederbord/baseboard management controller (BMC) / video kaart
- Schijf controller/hostbusadapter (HBA) / backplane
- Netwerkadapter (NIC)
- Besturingssysteem schijf *
- Schijven (stations die niet, hot wisselen, bijvoorbeeld PCI-e-insteekkaarten ondersteunen) *

* Deze onderdelen hot swap kunnen ondersteunen, maar kunnen variëren, afhankelijk van de implementatie van de leverancier. Zie de documentatie van de leverancier van uw OEM FRU voor gedetailleerde stappen.

Het volgende stroomdiagram ziet u het algemene proces FRU niet hot-verwisselbare computerhardware.

![Stroomdiagram dat toont onderdeel vervanging stroom](media/azure-stack-replace-component/ReplaceComponentFlow.PNG)

* Deze actie kan niet vereist op basis van de fysieke toestand van de hardware.

** Of de leverancier van de OEM-hardware voert de vervangende onderdeel en de firmware-updates kan verschillen, op het ondersteunen van contract.

## <a name="review-alert-information"></a>Bekijk informatie over waarschuwingen

De status van de Azure-Stack en het bewakingssysteem controleert de status van netwerkadapters en de schijven die worden beheerd door opslagruimten Direct. Andere hardwareonderdelen bewaakt niet. Waarschuwingen worden gegenereerd voor alle andere hardwareonderdelen in de leverancierspecifieke hardware bewakingsoplossing die wordt uitgevoerd op de host van de levenscyclus van hardware.

## <a name="component-replacement-process"></a>Proces voor het onderdeel vervangen

De volgende stappen zijn opgegeven als een overzicht van het proces voor het onderdeel vervangen. Volg deze stappen niet zonder te verwijzen naar de OEM geleverde FRU-documentatie.

1. Gebruik de [leegmaakt](azure-stack-node-actions.md#scale-unit-node-actions) actie het scale unit-knooppunt in onderhoudsmodus te plaatsen. Deze actie kan niet vereist op basis van de fysieke toestand van de hardware.
2. Nadat het scale unit-knooppunt in de onderhoudsmodus bevindt is, gebruikt u de [uitschakelen](azure-stack-node-actions.md#scale-unit-node-actions) in te grijpen. Deze actie kan niet vereist op basis van de fysieke toestand van de hardware.
 
   > [!NOTE]
   > In het onwaarschijnlijke geval dat het uitschakelen van de actie niet werkt, gebruikt u de baseboard management controller (BMC) webinterface.

3. Vervang de beschadigde hardware-onderdeel. Of de leverancier van de OEM-hardware de vervangende onderdeel uitvoert kan variëren, afhankelijk van uw support-contract.  
4. Werk de firmware. Doe uw leverancierspecifieke firmware-update met behulp van de host van de levenscyclus van hardware om ervoor te zorgen dat de vervangen hardwareonderdeel heeft de goedgekeurde firmware toegepast. Of de leverancier van de OEM-hardware in deze stap uitvoert kan variëren, afhankelijk van uw support-contract.  
5. Gebruik de [reparatie](azure-stack-node-actions.md#scale-unit-node-actions) actie voor het scale unit knooppunt terugbrengen in de schaaleenheid.
6. Gebruik van de bevoegde eindpunt [Controleer de status van de virtuele schijf repareren](azure-stack-replace-disk.md#check-the-status-of-virtual-disk-repair). Met nieuwe gegevensstations, een volledig herstel van de opslagtaak kan meerdere uren, afhankelijk van de systeembelasting duren en ruimte verbruikt.
7. Nadat de herstelactie is voltooid, valideert u dat alle actieve waarschuwingen automatisch is gesloten.

## <a name="next-steps"></a>Volgende stappen

- Zie voor meer informatie over het vervangen van een fysieke hot verwisselbare schijf [een schijf vervangen](azure-stack-replace-disk.md).
- Zie voor meer informatie over het vervangen van een fysiek knooppunt [vervangen van een scale unit knooppunt](azure-stack-replace-node.md). 