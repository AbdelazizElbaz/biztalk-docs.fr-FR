---
title: "Erreur - deuxième entrée du fonctoid cumulé n’est pas valide. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.secondInputToCumulativeNotValid
ms.assetid: e41a58a7-e0a2-4284-bd19-279578a8915d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a288bdaa9427cd26191571d180d39ad2dde9f9f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---second-input-to-cumulative-functoid-not-valid"></a>Erreur - deuxième entrée du fonctoid cumulé n’est pas valide.
**Code d’erreur**  
  
 btm1031  
  
 **Explication**  
  
 Le fonctoid **Cumulative** fonctoid a un deuxième paramètre d’entrée qui n’est pas valide. Lorsqu'il est associé à un fonctoid cumulé, celui-ci doit être un entier positif qui indique la plage du schéma source dans laquelle l'accumulation est effectuée.  
  
 **Action de l’utilisateur**  
  
 Sélectionnez le **Cumulative** fonctoid, cliquez sur le bouton de sélection (**...** ) associés à la **ordre les entrées de fonctoid** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis, dans le **configurer \<fonctoid > fonctoid** boîte de dialogue zone, vérifiez que le second paramètre d’entrée, le cas échéant, est un entier positif.