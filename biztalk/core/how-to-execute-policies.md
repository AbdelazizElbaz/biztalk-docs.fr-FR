---
title: "L’exécution de stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, policies
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: 90d28d9d-0204-47de-a927-26e284c886e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0aa834150f0d5c84ebb4c757769a2be38f3942
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-execute-policies"></a><span data-ttu-id="295b7-102">L’exécution des stratégies</span><span class="sxs-lookup"><span data-stu-id="295b7-102">How to Execute Policies</span></span>
<span data-ttu-id="295b7-103">L’exemple de code suivant montre comment appeler le moteur de règles pour une stratégie d’exécution par programme à l’aide de la **stratégie** classe dans le **Microsoft.RuleEngine** assembly.</span><span class="sxs-lookup"><span data-stu-id="295b7-103">The following sample code shows how to invoke the rule engine to execute a policy programmatically by using the **Policy** class in the **Microsoft.RuleEngine** assembly.</span></span>  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```  
  
## <a name="important-methods-of-the-policy-class"></a><span data-ttu-id="295b7-104">Méthodes importantes de la classe Stratégie</span><span class="sxs-lookup"><span data-stu-id="295b7-104">Important methods of the Policy class</span></span>  
 <span data-ttu-id="295b7-105">Le tableau suivant présente les méthodes importantes de la classe Stratégie et leurs descriptions.</span><span class="sxs-lookup"><span data-stu-id="295b7-105">Here are the important methods of the Policy class and their descriptions.</span></span>  
  
|<span data-ttu-id="295b7-106">Méthode de la classe Stratégie</span><span class="sxs-lookup"><span data-stu-id="295b7-106">Method in the Policy class</span></span>|<span data-ttu-id="295b7-107"> Description</span><span class="sxs-lookup"><span data-stu-id="295b7-107">Description</span></span>|  
|--------------------------------|-----------------|  
|<span data-ttu-id="295b7-108">Execute</span><span class="sxs-lookup"><span data-stu-id="295b7-108">Execute</span></span>|<span data-ttu-id="295b7-109">Ajoute les faits à court terme spécifiés dans la mémoire de travail du moteur de règles et exécute la stratégie à l'aide de l'algorithme correspondance-résolution des conflits-action.</span><span class="sxs-lookup"><span data-stu-id="295b7-109">Adds the specified short-term facts into the rule engine's working memory and executes the policy using Match-Conflict Resolution-Action algorithm.</span></span> <span data-ttu-id="295b7-110">Pour plus d’informations sur l’algorithme de l’Action de résolution de conflit de correspondance, consultez [évaluation de Condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md) .</span><span class="sxs-lookup"><span data-stu-id="295b7-110">For more information on Match-Conflict Resolution-Action algorithm, see [Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) .</span></span>|  
|<span data-ttu-id="295b7-111">Dispose</span><span class="sxs-lookup"><span data-stu-id="295b7-111">Dispose</span></span>|<span data-ttu-id="295b7-112">Libère les ressources utilisées par le moteur de règles pour l'exécution de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="295b7-112">Releases the resources used by the rule engine for executing the policy.</span></span>|  
|<span data-ttu-id="295b7-113">Désactiver</span><span class="sxs-lookup"><span data-stu-id="295b7-113">Clear</span></span>|<span data-ttu-id="295b7-114">Efface ou réinitialise la mémoire de travail et l'agenda de l'instance de moteur de règles créée pour l'exécution de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="295b7-114">Clears or resets the working memory and the agenda of the rule engine instance created for executing the policy.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="295b7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="295b7-115">See Also</span></span>  
 [<span data-ttu-id="295b7-116">Méthode Policy.Dispose</span><span class="sxs-lookup"><span data-stu-id="295b7-116">Policy.Dispose Method</span></span>](../core/policy-dispose-method.md)