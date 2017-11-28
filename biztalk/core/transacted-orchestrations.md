---
title: Transactionnel Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, compensations
- orchestrations, transactional
- Transaction Type property
ms.assetid: c4f0b6ca-d939-4d3a-b7ef-53c6aafdea9c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c6fb466e0c3cc5cae4a076237d1dbc970b5794
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transacted-orchestrations"></a><span data-ttu-id="6d69a-102">Orchestrations traitées</span><span class="sxs-lookup"><span data-stu-id="6d69a-102">Transacted Orchestrations</span></span>
<span data-ttu-id="6d69a-103">Au même titre que les étendues, les orchestrations peuvent être transactionnelles.</span><span class="sxs-lookup"><span data-stu-id="6d69a-103">Orchestrations can be transactional, just like scopes.</span></span> <span data-ttu-id="6d69a-104">En fait, une orchestration peut être considérée comme une étendue.</span><span class="sxs-lookup"><span data-stu-id="6d69a-104">In fact, an orchestration can itself be considered a scope.</span></span> <span data-ttu-id="6d69a-105">En général, les mêmes règles s'appliquent pour les orchestrations traitées et les étendues traitées.</span><span class="sxs-lookup"><span data-stu-id="6d69a-105">In general, the same rules apply for transacted orchestrations as for transacted scopes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d69a-106">L'une des différences existant entre les orchestrations et les étendues est que les premières ne disposent pas de gestionnaires d'exception.</span><span class="sxs-lookup"><span data-stu-id="6d69a-106">One difference between orchestrations and other scopes is that orchestrations do not have exception handlers.</span></span>  
  
## <a name="orchestration-compensation"></a><span data-ttu-id="6d69a-107">Compensation d'orchestration</span><span class="sxs-lookup"><span data-stu-id="6d69a-107">Orchestration compensation</span></span>  
 <span data-ttu-id="6d69a-108">Si le **Type de Transaction** propriété de l’orchestration est définie à long terme ou atomique, vous pouvez également sélectionner une valeur pour le **Compensation** propriété, qui peut être par défaut ou personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6d69a-108">If the **Transaction Type** property for your orchestration is set to long-running or atomic, you can also select a value for the **Compensation** property, which can be Default or Custom.</span></span>  
  
 <span data-ttu-id="6d69a-109">Si vous sélectionnez **personnalisé** pour la compensation, un **Compensation** onglet s’affiche à côté de l’aire de conception d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="6d69a-109">If you select **Custom** for the compensation, a **Compensation** tab will appear alongside the Orchestration Design Surface.</span></span> <span data-ttu-id="6d69a-110">Cette surface aura la même apparence que la surface de conception de l'orchestration et vous pourrez y ajouter des formes et des ports de la même manière.</span><span class="sxs-lookup"><span data-stu-id="6d69a-110">It will look the same as the Orchestration Design Surface, and you can add shapes and ports to it in the same way.</span></span>  
  
 <span data-ttu-id="6d69a-111">Les compensations n'ont lieu que sur les orchestrations appelées par d'autres orchestrations.</span><span class="sxs-lookup"><span data-stu-id="6d69a-111">Compensations only take place on orchestrations that are called by other orchestrations.</span></span> <span data-ttu-id="6d69a-112">Vous pouvez compenser une instance d’orchestration spécifique à l’aide de la **identificateur** propriété sur le **appeler Orchestration** forme.</span><span class="sxs-lookup"><span data-stu-id="6d69a-112">You can compensate a specific orchestration instance by using the **Identifier** property on the **Call Orchestration** shape.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d69a-113">Si une compensation existe sur une orchestration de niveau supérieur, elle sera ignorée par le moteur d'exécution.</span><span class="sxs-lookup"><span data-stu-id="6d69a-113">If a compensation exists on a top-level orchestration, it will be ignored by the runtime engine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d69a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d69a-114">See Also</span></span>  
 <span data-ttu-id="6d69a-115">[Rendre les Orchestrations transactionnelles](../core/making-orchestrations-transactional.md) </span><span class="sxs-lookup"><span data-stu-id="6d69a-115">[Making Orchestrations Transactional](../core/making-orchestrations-transactional.md) </span></span>  
 [<span data-ttu-id="6d69a-116">L’utilisation de Transactions et la gestion des Exceptions</span><span class="sxs-lookup"><span data-stu-id="6d69a-116">Using Transactions and Handling Exceptions</span></span>](../core/using-transactions-and-handling-exceptions.md)