---
title: "Validation avec des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, process management solutions
- process management solution tutorial, validating
- business rules, validating
- process management solution tutorial, business rules
ms.assetid: a67f3781-629a-4157-9a27-3b73d7a5a3a8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8926cf8bd95c2b90c7d16151b47f8893120b812e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validation-with-business-rules"></a><span data-ttu-id="85440-102">Validation avec des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="85440-102">Validation with Business Rules</span></span>
<span data-ttu-id="85440-103">Une méthode courante pour effectuer une validation consiste à créer un ensemble de règles d'entreprise à l'aide de l'infrastructure des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="85440-103">A common way to do validation is to construct a set of business rules using the Business Rules Framework.</span></span> <span data-ttu-id="85440-104">Vous pouvez ensuite utiliser la forme Appeler règles dans l'orchestration où vous voulez effectuer la validation.</span><span class="sxs-lookup"><span data-stu-id="85440-104">Then you use the Call Rules shape in the orchestration where you want to perform validation.</span></span>  
  
 <span data-ttu-id="85440-105">Dans l’application de gestion des processus métier, les **Validation** orchestration utilise des règles d’entreprise pour tester la validité de la commande.</span><span class="sxs-lookup"><span data-stu-id="85440-105">In the business process management application, the **Validation** orchestration uses business rules to test the validity of the order.</span></span>  
  
 <span data-ttu-id="85440-106">À l’aide de l’infrastructure des règles d’entreprise permet de modifier les règles sans avoir à recompiler et redéployer le **Validation** orchestration.</span><span class="sxs-lookup"><span data-stu-id="85440-106">Using the Business Rules Framework enables you to change the rules without recompiling and redeploying the **Validation** orchestration.</span></span> <span data-ttu-id="85440-107">Le compromis est que, pour les ensembles de règles simples, vous pouvez être en mesure d'enregistrer la durée de traitement en codant la logique dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="85440-107">The trade-off is that for simple sets of rules, you may be able to save processing time by coding the logic in the orchestration.</span></span>  
  
 <span data-ttu-id="85440-108">Pour plus d’informations sur l’utilisation de l’infrastructure des règles d’entreprise, consultez [création et à l’aide des règles d’entreprise](../core/creating-and-using-business-rules.md).</span><span class="sxs-lookup"><span data-stu-id="85440-108">For more information about using the Business Rules Framework, see [Creating and Using Business Rules](../core/creating-and-using-business-rules.md).</span></span> <span data-ttu-id="85440-109">Pour plus d’informations sur la forme Appeler règles, consultez [l’utilisation de la forme de règles d’appeler](../core/how-to-use-the-call-rules-shape.md).</span><span class="sxs-lookup"><span data-stu-id="85440-109">For more information about the Call Rules shape, see [How to Use the Call Rules Shape](../core/how-to-use-the-call-rules-shape.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85440-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85440-110">See Also</span></span>  
 <span data-ttu-id="85440-111">[Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="85440-111">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="85440-112">Logique du Gestionnaire de processus</span><span class="sxs-lookup"><span data-stu-id="85440-112">Process Manager Logic</span></span>](../core/process-manager-logic.md)