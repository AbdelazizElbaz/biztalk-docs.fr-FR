---
title: 'Erreur : plusieurs nœuds équivalents même cible | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.multipleEquivNodeSameTarget
ms.assetid: d8ca9f94-1d87-41bb-9479-6a01a5b6702d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12df4f7a68bb1eceaa3211c6aad6e9a581f17a4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---multiple-equivalent-node-same-target"></a>Erreur : plusieurs nœuds équivalents même cible
**Code d’erreur**  
  
 btm1025  
  
 **Explication**  
  
 Les nœuds indiqués dans le schéma source, qui sont des nœuds enfants en conflit d’un **équivalent** nœud de groupe, sont liés au nœud indiqué dans le schéma de destination. Un seul de ces nœuds peut apparaître dans un message d'instance donné.  
  
 **Action de l’utilisateur**  
  
 Assurez-vous qu’un seul des enfants nœuds de la **équivalent** nœud de groupe est connecté à un nœud donné dans le schéma de destination.