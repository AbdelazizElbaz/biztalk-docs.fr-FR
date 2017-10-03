---
title: "Erreur : fonctoid Index avec trop d’index | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.indexFunctoidHasTooManyIndices
ms.assetid: 5dd2d5b4-3f7a-45be-b6f4-708b0a76805a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4899ec5f03e3474e61e4272ffd0612c77c90ea32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---index-functoid-has-too-many-indexes"></a>Erreur : fonctoid Index avec trop d’index
**Code d’erreur**  
  
 btm1016  
  
 **Explication**  
  
 Le fonctoid **Index** le fonctoid ne comporte trop de paramètres d’entrée d’index spécifiées. Le nombre de paramètres d’entrée d’index ne doit pas dépasser le nombre de boucle **enregistrement** nœuds au sein de laquelle le **champ** le nœud spécifié comme le premier paramètre d’entrée est imbriqué.  
  
 **Action de l’utilisateur**  
  
 Sélectionnez le **Index** fonctoid, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis, dans le **configurer \<fonctoid > fonctoid** boîte de dialogue, supprimez l’index en trop de paramètres d’entrée en sélectionnant et en cliquant sur le ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") bouton pour chacun d’eux.