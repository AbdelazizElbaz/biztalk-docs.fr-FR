---
title: Erreur - entrées au fonctoid cumulé à partir de différents enregistrements parents | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.inputsToCumulativeFromDiffParents
ms.assetid: a2dcfe6f-0cd4-41ed-a69f-e510a74760a9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3c919001e05ca99383ffce72c8d450f6d04624b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---inputs-to-cumulative-functoid-from-different-parent-records"></a>Erreur : les entrées du fonctoid cumulé proviennent différents enregistrements parents.
**Code d’erreur**  
  
 btm1032  
  
 **Explication**  
  
 Pour le fonctoid **Cumulative** fonctoid, le deuxième paramètre d’entrée (étendue d’accumulation) provient d’une autre partie du schéma source que le nœud agissant comme le premier paramètre d’entrée (nœud à cumuler).  
  
 **Action de l’utilisateur**  
  
 Assurez-vous que les deux paramètres d’entrée aux indiqué **Cumulative** fonctoid partagent le même enregistrement parent, ou que le deuxième paramètre d’entrée (étendue d’accumulation) comporte un paramètre d’entrée constant.