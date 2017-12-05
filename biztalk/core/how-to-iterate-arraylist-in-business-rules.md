---
title: "Comment effectuer une itération d’ArrayList dans les règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, ArrayList
- business rules, arrays
- Business Rules Framework, programming
ms.assetid: 935e8648-72dc-4128-986c-72b0487bc074
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9010907cfe9fb6d79a8d9fcead533376b014640e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-iterate-arraylist-in-business-rules"></a><span data-ttu-id="42c27-102">Comment effectuer une itération d’ArrayList dans les règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="42c27-102">How to Iterate ArrayList in Business Rules</span></span>
<span data-ttu-id="42c27-103">Cette section fournit un exemple d’itération sur les membres d’un **ArrayList** dans les règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="42c27-103">This section provides an example of iterating through members of an **ArrayList** in business rules.</span></span>  
  
 <span data-ttu-id="42c27-104">Supposons que vous avez un **ArrayList** avec une collection de **MyClass** objets.</span><span class="sxs-lookup"><span data-stu-id="42c27-104">Assume you have an **ArrayList** with a collection of **MyClass** objects.</span></span> <span data-ttu-id="42c27-105">Vos règles d'entreprise se présentent alors comme suit :</span><span class="sxs-lookup"><span data-stu-id="42c27-105">Your business rules would look like the following.</span></span>  
  
## <a name="rule-a"></a><span data-ttu-id="42c27-106">Règle A</span><span class="sxs-lookup"><span data-stu-id="42c27-106">Rule A</span></span>  
 <span data-ttu-id="42c27-107">IF 1==1</span><span class="sxs-lookup"><span data-stu-id="42c27-107">IF 1==1</span></span>  
  
 <span data-ttu-id="42c27-108">THEN Assert (ArrayList.GetEnumerator)</span><span class="sxs-lookup"><span data-stu-id="42c27-108">THEN Assert (ArrayList.GetEnumerator)</span></span>  
  
 <span data-ttu-id="42c27-109">Un **IEnumerator** type est déclaré dans la mémoire de travail, car la condition de règle (1 == 1) a toujours la valeur true.</span><span class="sxs-lookup"><span data-stu-id="42c27-109">An **IEnumerator** type is asserted into the working memory, because the rule condition (1==1) always evaluates to true.</span></span>  
  
## <a name="rule-b"></a><span data-ttu-id="42c27-110">Règle B</span><span class="sxs-lookup"><span data-stu-id="42c27-110">Rule B</span></span>  
 <span data-ttu-id="42c27-111">IF IEnumerator.MoveNext</span><span class="sxs-lookup"><span data-stu-id="42c27-111">IF IEnumerator.MoveNext</span></span>  
  
 <span data-ttu-id="42c27-112">THEN    Assert (IEnumerator.get_Current)</span><span class="sxs-lookup"><span data-stu-id="42c27-112">THEN    Assert (IEnumerator.get_Current)</span></span>  
  
 <span data-ttu-id="42c27-113">Update (IEnumerator)</span><span class="sxs-lookup"><span data-stu-id="42c27-113">Update (IEnumerator)</span></span>  
  
 <span data-ttu-id="42c27-114">Comme la règle effectue une itération dans les **ArrayList**, chaque **MyClass** objet dans la collection est déclaré dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="42c27-114">As the rule iterates through the **ArrayList**, each **MyClass** object in the collection is asserted into the working memory.</span></span>  
  
## <a name="rule-c"></a><span data-ttu-id="42c27-115">Règle C</span><span class="sxs-lookup"><span data-stu-id="42c27-115">Rule C</span></span>  
 <span data-ttu-id="42c27-116">IF MyClass.MyProperty==2</span><span class="sxs-lookup"><span data-stu-id="42c27-116">IF MyClass.MyProperty==2</span></span>  
  
 <span data-ttu-id="42c27-117">PUIS \<faire quelque chose...\></span><span class="sxs-lookup"><span data-stu-id="42c27-117">THEN \<Do Something...\></span></span>  
  
 <span data-ttu-id="42c27-118">Cette règle exécute une ou des actions lorsque la valeur de propriété de l'objet a une correspondance dans la condition.</span><span class="sxs-lookup"><span data-stu-id="42c27-118">This rule executes action(s) when the property value of the object is matched in the condition.</span></span>