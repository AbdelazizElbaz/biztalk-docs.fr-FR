---
title: "Comment retourner True ou False à partir d’une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7bb9b2-14aa-44e7-a290-e49bf53bc594
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 281d5ab7648545f2e0616095f3c535d7d109136f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-return-true-or-false-from-a-policy"></a>Retour d'une valeur True ou False pour une stratégie
Vous ne pouvez pas directement indiquer un type de retour pour une stratégie. Vous pouvez cependant transmettre un des types de faits suivants à la stratégie, faire en sorte que la stratégie modifie la valeur du fait en `true` ou en `false`, puis vérifier la valeur de la propriété/de l'élément/de la colonne après l'exécution de la stratégie :  
  
-   Un objet .NET avec une propriété de type `Boolean`  
  
-   Un document XML avec un élément de type `Boolean`  
  
-   Une table de base de données avec une colonne de type `Boolean`