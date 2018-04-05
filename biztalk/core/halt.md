---
title: Arrêter | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Halt function [Business Rules Engine]
ms.assetid: 468ba6dd-2bb2-4787-a824-1f5455508efd
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07ca8091d4ff4405704314d72939758c7600a71a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="halt"></a><span data-ttu-id="58823-102">Interrompre</span><span class="sxs-lookup"><span data-stu-id="58823-102">Halt</span></span>
<span data-ttu-id="58823-103">Vous pouvez utiliser la **arrêter** fonction pour arrêter l’exécution du moteur de règles en cours.</span><span class="sxs-lookup"><span data-stu-id="58823-103">You can use the **Halt** function to halt the current rule engine execution.</span></span> <span data-ttu-id="58823-104">Le **arrêter** fonction prend un paramètre de type `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="58823-104">The **Halt** function takes one parameter of type `Boolean`.</span></span> <span data-ttu-id="58823-105">Si vous spécifiez la valeur `true` pour le paramètre, le moteur de règles efface également l'agenda contenant les règles candidates en attente.</span><span class="sxs-lookup"><span data-stu-id="58823-105">If you specify the value for the parameter as `true`, the rule engine also clears the agenda that contains the pending candidate rules.</span></span>  
  
 <span data-ttu-id="58823-106">Le **Policy.Execute** (méthode) est essentiellement un wrapper autour de le **RuleEngine.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="58823-106">The **Policy.Execute** method is basically a wrapper around the **RuleEngine.Execute** method.</span></span> <span data-ttu-id="58823-107">Son code est similaire au code suivant :</span><span class="sxs-lookup"><span data-stu-id="58823-107">It has code similar to the following code:</span></span>  
  
```  
RuleEngine.Assert(facts);   
RuleEngine.Execute();   
RuleEngine.Retract(facts);  
```  
  
 <span data-ttu-id="58823-108">Si vous utilisez la **Policy.Execute** méthode pour exécuter une stratégie, le moteur de règles rend le contrôle à la **Policy.Execute** (méthode) lorsque le **arrêter** fonction est exécutée.</span><span class="sxs-lookup"><span data-stu-id="58823-108">If you use the **Policy.Execute** method to execute a policy, the rule engine returns control to the **Policy.Execute** method when the **Halt** function is executed.</span></span> <span data-ttu-id="58823-109">Le **Policy.Execute** méthode retire les faits et retourne le contrôle à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="58823-109">The **Policy.Execute** method retracts the facts and returns control to the caller.</span></span> <span data-ttu-id="58823-110">Dans ce cas, l'exécution interrompue de la stratégie ne peut être reprise.</span><span class="sxs-lookup"><span data-stu-id="58823-110">Therefore, the halted policy execution cannot be resumed in this case.</span></span> <span data-ttu-id="58823-111">La même chose se produit lorsque vous utilisez la **appeler règles** forme pour appeler la stratégie.</span><span class="sxs-lookup"><span data-stu-id="58823-111">The same thing happens when you use the **Call Rules** shape to invoke the policy.</span></span>  
  
 <span data-ttu-id="58823-112">Toutefois, si vous utilisez la **RuleEngine.Execute** (méthode) directement pour exécuter la stratégie, vous pouvez reprendre l’exécution interrompue de la stratégie avec la prochaine en attente de l’activation de la règle en appelant simplement **RuleEngine.Execute** Nouveau (à condition que vous ne pas qu’aucun objet nécessaire entre les deux appels).</span><span class="sxs-lookup"><span data-stu-id="58823-112">However, if you use the **RuleEngine.Execute** method directly to execute the policy, you can resume the halted policy execution with the next pending rule firing by simply calling **RuleEngine.Execute** again (provided you did not retract any objects needed between the two calls).</span></span> <span data-ttu-id="58823-113">Voici l'exemple de code permettant de reprendre l'exécution interrompue de la stratégie :</span><span class="sxs-lookup"><span data-stu-id="58823-113">The sample code for resuming the halted policy execution is as follows:</span></span>  
  
```  
//assert facts into working memory of the rule engine instance  
RuleEngine.Assert(facts);   
//execute the policy  
RuleEngine.Execute();   
//policy invokes the Halt method when executing actions.   
//control is returned to here when the Halt method is invoked  
  
//when engine is halted do the following  
//Add your code here  
  
//To resume the halted rule engine execution  
RuleEngine.Execute();  
//retract or remove facts frm the working memory of the rule engine  
RuleEngine.Retract(facts);  
```  
  
 <span data-ttu-id="58823-114">Notez que la **Policy.Execute** méthode met en cache les instances du moteur de règles pour de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="58823-114">Note that the **Policy.Execute** method caches the rule engine instances for better performance.</span></span> <span data-ttu-id="58823-115">Lorsque vous utilisez la **RuleEngine.Execute** directement la méthode, le moteur de règles instances ne sont pas mises en cache.</span><span class="sxs-lookup"><span data-stu-id="58823-115">When you use the **RuleEngine.Execute** method directly, the rule engine instances are not cached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58823-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58823-116">See Also</span></span>  
 [<span data-ttu-id="58823-117">Fonctions de contrôle du moteur</span><span class="sxs-lookup"><span data-stu-id="58823-117">Engine Control Functions</span></span>](../core/engine-control-functions.md)