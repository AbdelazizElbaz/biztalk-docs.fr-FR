---
title: "Le répartiteur ESB désassembler composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1f5e46b-8f41-47f8-b22b-b9e9eaac6475
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c846ca716aef72d43e4f4a6ed75a2b20a81c351a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-dispatcher-disassemble-component"></a><span data-ttu-id="c1141-102">Le répartiteur ESB désassembler composant</span><span class="sxs-lookup"><span data-stu-id="c1141-102">The ESB Dispatcher Disassemble Component</span></span>
<span data-ttu-id="c1141-103">Le composant de désassemblage de répartiteur ESB peut définir dynamiquement les propriétés d’emplacement de point de terminaison pour les messages sortants de la même façon pour le composant de répartiteur.</span><span class="sxs-lookup"><span data-stu-id="c1141-103">The ESB Dispatcher Disassemble component can dynamically set endpoint location properties for outbound messages in a similar way to the Dispatcher component.</span></span> <span data-ttu-id="c1141-104">Ce composant de pipeline combine le message de Microsoft BizTalk des fonctionnalités de traitement par lot (en héritant de la classe du désassembleur XML nommé **XmlDasmComp**) avec le message de la distribution de mécanisme qui peut exécuter l’itinéraire d’ESB services de messagerie dans un pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c1141-104">This pipeline component combines Microsoft BizTalk message de-batching functionality (by inheriting from the XML disassembler class named **XmlDasmComp**) with the message dispatching mechanism that can execute ESB itinerary messaging services in a BizTalk pipeline.</span></span>