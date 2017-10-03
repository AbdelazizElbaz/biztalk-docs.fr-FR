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
# <a name="the-esb-dispatcher-disassemble-component"></a>Le répartiteur ESB désassembler composant
Le composant de désassemblage de répartiteur ESB peut définir dynamiquement les propriétés d’emplacement de point de terminaison pour les messages sortants de la même façon pour le composant de répartiteur. Ce composant de pipeline combine le message de Microsoft BizTalk des fonctionnalités de traitement par lot (en héritant de la classe du désassembleur XML nommé **XmlDasmComp**) avec le message de la distribution de mécanisme qui peut exécuter l’itinéraire d’ESB services de messagerie dans un pipeline BizTalk.