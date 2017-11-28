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
ms.openlocfilehash: 95896b63e5bb982a4778b05970900c989ebc66b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-iterate-arraylist-in-business-rules"></a><span data-ttu-id="8a5a0-102">Comment effectuer une itération d’ArrayList dans les règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="8a5a0-102">How to Iterate ArrayList in Business Rules</span></span>
<span data-ttu-id="8a5a0-103">Cette section fournit un exemple d’itération sur les membres d’un **ArrayList** dans les règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8a5a0-103">This section provides an example of iterating through members of an **ArrayList** in business rules.</span></span>  
  
 <span data-ttu-id="8a5a0-104">Supposons que vous avez un **ArrayList** avec une collection de **MyClass** objets.</span><span class="sxs-lookup"><span data-stu-id="8a5a0-104">Assume you have an **ArrayList** with a collection of **MyClass** objects.</span></span> <span data-ttu-id="8a5a0-105">Vos règles d'entreprise se présentent alors comme suit :</span><span class="sxs-lookup"><span data-stu-id="8a5a0-105">Your business rules would look like the following.</span></span>  
  
## <a name="rule-a"></a><span data-ttu-id="8a5a0-106">Règle A</span><span class="sxs-lookup"><span data-stu-id="8a5a0-106">Rule A</span></span>  
 <span data-ttu-id="8a5a0-107">IF 1==1</span><span class="sxs-lookup"><span data-stu-id="8a5a0-107">IF 1==1</span></span>  
  
 <span data-ttu-id="8a5a0-108">THEN Assert (ArrayList.GetEnumerator)</span><span class="sxs-lookup"><span data-stu-id="8a5a0-108">THEN Assert (ArrayList.GetEnumerator)</span></span>  
  
 <span data-ttu-id="8a5a0-109">Un **IEnumerator** type est déclaré dans la mémoire de travail, car la condition de règle (1 == 1) a toujours la valeur true.</span><span class="sxs-lookup"><span data-stu-id="8a5a0-109">An **IEnumerator** type is asserted into the working memory, because the rule condition (1==1) always evaluates to true.</span></span>  
  
## <a name="rule-b"></a><span data-ttu-id="8a5a0-110">Règle B</span><span class="sxs-lookup"><span data-stu-id="8a5a0-110">Rule B</span></span>  
 <span data-ttu-id="8a5a0-111">IF IEnumerator.MoveNext</span><span class="sxs-lookup"><span data-stu-id="8a5a0-111">IF IEnumerator.MoveNext</span></span>  
  
 <span data-ttu-id="8a5a0-112">THEN    Assert (IEnumerator.get_Current)</span><span class="sxs-lookup"><span data-stu-id="8a5a0-112">THEN    Assert (IEnumerator.get_Current)</span></span>  
  
 <span data-ttu-id="8a5a0-113">Update (IEnumerator)</span><span class="sxs-lookup"><span data-stu-id="8a5a0-113">Update (IEnumerator)</span></span>  
  
 <span data-ttu-id="8a5a0-114">Comme la règle effectue une itération dans les **ArrayList**, chaque **MyClass** objet dans la collection est déclaré dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="8a5a0-114">As the rule iterates through the **ArrayList**, each **MyClass** object in the collection is asserted into the working memory.</span></span>  
  
## <a name="rule-c"></a><span data-ttu-id="8a5a0-115">Règle C</span><span class="sxs-lookup"><span data-stu-id="8a5a0-115">Rule C</span></span>  
 <span data-ttu-id="8a5a0-116">IF MyClass.MyProperty==2</span><span class="sxs-lookup"><span data-stu-id="8a5a0-116">IF MyClass.MyProperty==2</span></span>  
  
 <span data-ttu-id="8a5a0-117">PUIS \<faire quelque chose... ></span><span class="sxs-lookup"><span data-stu-id="8a5a0-117">THEN \<Do Something...></span></span>  
  
 <span data-ttu-id="8a5a0-118">Cette règle exécute une ou des actions lorsque la valeur de propriété de l'objet a une correspondance dans la condition.</span><span class="sxs-lookup"><span data-stu-id="8a5a0-118">This rule executes action(s) when the property value of the object is matched in the condition.</span></span>