---
title: Azure Service Bus-verificatie en autorisatie | Microsoft Docs
description: "Verifiëren met Service Bus-apps met Shared Access Signature (SAS)-verificatie."
services: service-bus-messaging
documentationcenter: na
author: sethmanheim
manager: timlt
editor: 
ms.assetid: 18bad0ed-1cee-4a5c-a377-facc4785c8c9
ms.service: service-bus-messaging
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/09/2017
ms.author: sethm
ms.openlocfilehash: b4b9d5d272bdb172f1d40db379a519a4f617550a
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/11/2017
---
# <a name="service-bus-authentication-and-authorization"></a>Vereenvoudigde Service Bus-verificatie en -autorisatie

Toepassingen toegang krijgen tot Azure Service Bus-functies met Shared Access Signature (SAS)-token verificatie. Met SAS, toepassingen een token voor Service Bus dat is ondertekend met een symmetrische sleutel bekend zowel voor de token verlener en Service Bus ('gedeeld') en deze sleutel rechtstreeks is gekoppeld aan een regel voor het verlenen van specifieke rechten, zoals de machtiging voor het ontvangen van / luisteren of berichten verzenden. SAS-regels zijn dat ofwel geconfigureerd op de naamruimte, of rechtstreeks op entiteiten, zoals een wachtrij of onderwerp, waardoor het fijnmazige toegangsbeheer.

SAS-tokens kunnen worden gegenereerd door een Service Bus-client rechtstreeks of ze kunnen worden gegenereerd door een aantal tussenliggende token eindpunt uitgeven die de client met communiceert. Bijvoorbeeld, een systeem kan de client aan te roepen, een Active Directory autorisatie beveiligd web service-eindpunt om te bewijzen dat de identiteits- en toegangsrechten nodig en het juiste Service Bus-token wordt vervolgens geretourneerd door de webservice. Deze SAS-token kan eenvoudig worden gegenereerd met behulp van de Service Bus-tokenprovider opgenomen in de SDK. 

> [!IMPORTANT]
> Als u van Azure Active Directory-toegangsbeheer (ook wel bekend als Access Control Service of ACS) in combinatie met Service Bus gebruikmaakt, houd er rekening mee dat de ondersteuning voor deze methode is nu beperkt en u moet uw toepassing via SAS migreren. Zie voor meer informatie [dit blogbericht](https://blogs.msdn.microsoft.com/servicebus/2017/06/01/upcoming-changes-to-acs-enabled-namespaces/).

## <a name="shared-access-signature-authentication"></a>Shared Access Signature-verificatie

[SAS verificatie](service-bus-sas.md) kunt u een gebruikerstoegang tot de Service Bus-resources met specifieke rechten verlenen. SAS-verificatie in Service Bus omvat de configuratie van een cryptografische sleutel met de gekoppelde rechten van een Service Bus-resource. Clients vervolgens toegang kunnen krijgen tot deze resource in de vorm van een SAS-token, die bestaat uit de bron-URI wordt geopend en een verloopdatum die zijn ondertekend met de geconfigureerde sleutel.

U kunt de sleutels voor SA's configureren voor een Service Bus-naamruimte. De sleutel is van toepassing op alle berichtentiteiten in waarmee de naamruimte. U kunt ook sleutels configureren over Service Bus-wachtrijen en onderwerpen. SAS wordt ook ondersteund op [Azure Relay](../service-bus-relay/relay-authentication-and-authorization.md).

U kunt configureren voor het gebruik van SAS, een [SharedAccessAuthorizationRule](/dotnet/api/microsoft.servicebus.messaging.sharedaccessauthorizationrule) object op een naamruimte, wachtrij of onderwerp. Deze regel bestaat uit de volgende elementen:

* *KeyName* waarin de regel.
* *PrimaryKey* is een cryptografische sleutel gebruikt aanmelding/SAS om tokens te valideren.
* *Secundaire sleutel* is een cryptografische sleutel gebruikt aanmelding/SAS om tokens te valideren.
* *Rechten* die vertegenwoordigt de verzameling van luisteren, verzenden of beheren van rechten verleend.

Autorisatieregels geconfigureerd op het niveau van de naamruimte kunnen toegang verlenen tot alle entiteiten in een naamruimte voor clients met tokens die zijn ondertekend met de bijbehorende sleutel. Maximaal 12 toestemming kunnen regels worden geconfigureerd op een Service Bus-naamruimte, wachtrij of onderwerp. Standaard een [SharedAccessAuthorizationRule](/dotnet/api/microsoft.servicebus.messaging.sharedaccessauthorizationrule) met alle rechten is geconfigureerd voor elke naamruimte als het eerst is ingericht.

Voor toegang tot een entiteit moet de client vereist dat een SAS-token dat is gegenereerd met een specifieke [SharedAccessAuthorizationRule](/dotnet/api/microsoft.servicebus.messaging.sharedaccessauthorizationrule). De SAS-token wordt gegenereerd op basis van het HMAC-SHA256 van een resourcetekenreeks die bestaat uit de resource-URI waartoe toegang is aangevraagd en een verloopbewerking met een cryptografische sleutel die is gekoppeld aan de autorisatieregel.

Ondersteuning van de SAS-verificatie voor Service Bus is opgenomen in de Azure .NET SDK-versies 2.0 en hoger. SAS biedt ondersteuning voor een [SharedAccessAuthorizationRule](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.messaging.sharedaccessauthorizationrule). Alle API's die een verbindingsreeks als een parameter accepteren onder meer ondersteuning voor SAS-verbindingsreeksen.

## <a name="next-steps"></a>Volgende stappen

- Blijven lezen [Service Bus-verificatie met Shared Access Signatures](service-bus-sas.md) voor meer informatie over SAS.
- [Wijzigingen aan ACS ingeschakeld naamruimten.](https://blogs.msdn.microsoft.com/servicebus/2017/06/01/upcoming-changes-to-acs-enabled-namespaces/)
- Zie voor de bijbehorende informatie over Azure Relay-verificatie en autorisatie, [Azure Relay-verificatie en autorisatie](../service-bus-relay/relay-authentication-and-authorization.md). 

