---
title: "Comment créer un créateur de faits | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetFactTypes method
- CreateFacts method
- IFactCreator interface
- Business Rules Framework, code samples
- Business Rules Framework, fact creator
- Business Rules Framework, programming
ms.assetid: 0589be8e-34d6-4e55-b678-c1f8436d1f61
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cba9c46a147d912ae22644a30ef65c0b0213202
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-fact-creator"></a><span data-ttu-id="2834a-102">Création d’un créateur de faits</span><span class="sxs-lookup"><span data-stu-id="2834a-102">How to Create a Fact Creator</span></span>
<span data-ttu-id="2834a-103">Vous pouvez écrire un créateur de faits pour créer des instances de vos faits.</span><span class="sxs-lookup"><span data-stu-id="2834a-103">You can write a fact creator to create instances of your facts.</span></span> <span data-ttu-id="2834a-104">Votre créateur de faits doit implémenter **IFactCreator** et son **CreateFacts** (méthode) et **GetFactTypes** (méthode).</span><span class="sxs-lookup"><span data-stu-id="2834a-104">Your fact creator must implement **IFactCreator** and its **CreateFacts** method and **GetFactTypes** method.</span></span> <span data-ttu-id="2834a-105">Une fois que vous avez créé votre dll de créateur de faits, vous pouvez y accéder depuis le testeur de stratégie.</span><span class="sxs-lookup"><span data-stu-id="2834a-105">After you have created your fact creator dll, you can browse to it from within the policy tester.</span></span> <span data-ttu-id="2834a-106">L’exemple suivant illustre une implémentation de créateur de faits.</span><span class="sxs-lookup"><span data-stu-id="2834a-106">The following is an example of a fact creator implementation.</span></span>  
  
```  
public class MyFactCreator : IFactCreator  
{  
   private object[] myFacts;  
   public MyFactCreator()  
   {  
   }  
   public object[] CreateFacts ( RuleSetInfo rulesetInfo )  
   {  
      myFacts = new object[1];  
      myFacts.SetValue(new MySampleBusinessObject(),0);  
      return myFacts;  
   }  
   public Type[] GetFactTypes (RuleSetInfo rulesetInfo)  
   {  
      return null;  
   }  
}  
```