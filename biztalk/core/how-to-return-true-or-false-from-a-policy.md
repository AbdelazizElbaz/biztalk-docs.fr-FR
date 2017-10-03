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
# <a name="how-to-return-true-or-false-from-a-policy"></a><span data-ttu-id="8f264-102">Retour d'une valeur True ou False pour une stratégie</span><span class="sxs-lookup"><span data-stu-id="8f264-102">How to Return True or False from a Policy</span></span>
<span data-ttu-id="8f264-103">Vous ne pouvez pas directement indiquer un type de retour pour une stratégie.</span><span class="sxs-lookup"><span data-stu-id="8f264-103">You cannot specify a return type for a policy directly.</span></span> <span data-ttu-id="8f264-104">Vous pouvez cependant transmettre un des types de faits suivants à la stratégie, faire en sorte que la stratégie modifie la valeur du fait en `true` ou en `false`, puis vérifier la valeur de la propriété/de l'élément/de la colonne après l'exécution de la stratégie :</span><span class="sxs-lookup"><span data-stu-id="8f264-104">However, you can pass one of the following types of facts to the policy, have the policy change the value of the fact to `true` or `false`, and then check the value of the property/element/column after the policy is executed:</span></span>  
  
-   <span data-ttu-id="8f264-105">Un objet .NET avec une propriété de type `Boolean`</span><span class="sxs-lookup"><span data-stu-id="8f264-105">A .NET object with a property of type `Boolean`</span></span>  
  
-   <span data-ttu-id="8f264-106">Un document XML avec un élément de type `Boolean`</span><span class="sxs-lookup"><span data-stu-id="8f264-106">An XML document with an element of type `Boolean`</span></span>  
  
-   <span data-ttu-id="8f264-107">Une table de base de données avec une colonne de type `Boolean`</span><span class="sxs-lookup"><span data-stu-id="8f264-107">A database table with a column of type `Boolean`</span></span>