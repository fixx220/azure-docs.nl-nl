---
title: Verkeer van web-apps in Azure beheren met Traffic Manager
description: Dit artikel bevat samenvattingsinformatie voor Azure Traffic Manager, omdat deze zich tot Azure-web-apps verhoudt.
services: app-service\web
documentationcenter: 
author: cephalin
writer: cephalin
manager: erikre
editor: mollybos
ms.assetid: dabda633-e72f-4dd4-bf1c-6e945da456fd
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/25/2016
ms.author: cephalin
ms.openlocfilehash: 93645aa5765d533b45fe2266f061ad61c0bf45d7
ms.sourcegitcommit: a7c01dbb03870adcb04ca34745ef256414dfc0b3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2017
---
# <a name="controlling-azure-web-app-traffic-with-azure-traffic-manager"></a>Verkeer van web-apps in Azure beheren met Traffic Manager
> [!NOTE]
> Dit artikel bevat samenvattingsinformatie voor Microsoft Azure Traffic Manager, omdat deze zich tot Azure Web Apps verhoudt. Via de koppelingen aan het einde van dit artikel vindt meer informatie over Azure Traffic Manager zelf.
> 
> 

## <a name="introduction"></a>Inleiding
U kunt Azure Traffic Manager gebruiken om te bepalen hoe aanvragen van de webserver en webclients worden gedistribueerd naar de web-apps in Azure App Service. Als eindpunten voor web-app worden toegevoegd aan een Azure Traffic Manager-profiel, Azure Traffic Manager houdt van de status van uw web-apps (actief, gestopt of verwijderd) zodat u deze kunt bepalen welke van deze eindpunten verkeer ontvangt.

## <a name="routing-methods"></a>methoden voor het doorsturen
Azure Traffic Manager maakt gebruik van drie verschillende methoden voor het doorsturen. Deze methoden worden beschreven in de volgende lijst zoals ze betrekking op Azure-web-apps hebben.

* **[Prioriteit](#priority):** gebruik van een primaire web-app voor al het verkeer en back-ups bieden voor het geval de primaire of de back-web-apps niet beschikbaar zijn.
* **[Gewogen](#weighted):** verkeer verdelen over een reeks web-apps, gelijkmatig of volgens het gewicht, die u definieert.
* **[Prestaties](#performance):** wanneer u web-apps in verschillende geografische locaties hebt, gebruikt u de 'dichtstbijzijnde' web-app in termen van de laagste netwerklatentie.
* **[Geografische](#geographic):** direct gebruikers aan specifieke web-apps op basis van welke geografische locatie hun DNS-query is afkomstig uit. 

Zie voor meer informatie [methoden voor het doorsturen van Traffic Manager](../traffic-manager/traffic-manager-routing-methods.md).

## <a name="web-apps-and-traffic-manager-profiles"></a>Web-Apps en Traffic Manager-profielen
Een profiel maken in Azure Traffic Manager dat wordt gebruikt een van de drie taakverdeling methoden die hierboven is beschreven laden voor het configureren van het besturingselement van het verkeer van web-app en voegt u de eindpunten (in dit geval web-apps) waarvoor u wilt beheren van verkeer naar het profiel. De status van uw web-app (actief, gestopt of verwijderd) regelmatig wordt gecommuniceerd aan het profiel zodat Azure Traffic Manager kunt dienovereenkomstig verkeer omleiden.

Als u Azure Traffic Manager met Azure, houd er rekening mee houden de volgende punten:

* Voor web-app-implementaties binnen dezelfde regio biedt Web-Apps al failover- en round-robin functionaliteit zonder rekening te houden modus voor web-app.
* Voor implementaties in dezelfde regio die Web-Apps in combinatie met een andere Azure-cloudservice gebruiken, kunt u beide typen eindpunten hybride scenario's te maken kunt combineren.
* U kunt slechts één eindpunt van web-app per regio opgeven in een profiel. Wanneer u een web-app als een eindpunt voor één regio selecteert, worden de resterende web-apps in deze regio niet beschikbaar voor selectie voor dit profiel.
* De web-app-eindpunten die u opgeeft in een Azure Traffic Manager-profiel wordt weergegeven onder de **domeinnamen** sectie op de pagina configureren voor de web-app in het profiel, maar kan niet worden geconfigureerd er.
* Nadat u een web-app aan een profiel toevoegen, de **Site-URL** op het Dashboard van het web van app-portalpagina aangepaste domein wordt de URL weergegeven van de web-app als u een hebt ingesteld. Anders wordt de Traffic Manager-profiel-URL (bijvoorbeeld `contoso.trafficmgr.com`). Zowel de directe domeinnaam van de web-app en de Traffic Manager-URL worden weergegeven op de pagina van de web-app configureren onder de **domeinnamen** sectie.
* Uw aangepaste domeinnamen werkt zoals verwacht, maar naast deze toevoegt aan uw web-apps, moet u ook de DNS-kaart om te verwijzen naar de Traffic Manager-URL configureren. Zie voor informatie over het instellen van een aangepast domein voor een Azure-web-app, [configureren van een aangepaste domeinnaam voor een Azure-website](app-service-web-tutorial-custom-domain.md).
* U kunt alleen web-apps die in de modus standard of premium aan een Azure Traffic Manager-profiel toevoegen.

## <a name="next-steps"></a>Volgende stappen
Zie voor een conceptuele en technisch overzicht van Azure Traffic Manager, [Traffic Manager-overzicht](../traffic-manager/traffic-manager-overview.md).

Zie voor meer informatie over het gebruik van Traffic Manager met Web-Apps, de blogberichten [met behulp van Azure Traffic Manager met Azure websites](http://blogs.msdn.com/b/waws/archive/2014/03/18/using-windows-azure-traffic-manager-with-waws.aspx) en [Azure Traffic Manager kan nu worden geïntegreerd met Azure websites](https://azure.microsoft.com/blog/2014/03/27/azure-traffic-manager-can-now-integrate-with-azure-web-sites/).

