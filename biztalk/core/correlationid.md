---
title: "ID de corrélation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4faf210-7e7f-450d-8bb1-84d3d31c3022
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1192de4a49c300220ce0b297bbc1ee02ce64c6dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlationid"></a><span data-ttu-id="5aa92-102">CorrelationID</span><span class="sxs-lookup"><span data-stu-id="5aa92-102">CorrelationID</span></span>
<span data-ttu-id="5aa92-103">L'élément `CorrelationID` permet de spécifier un ID de corrélation pour un message.</span><span class="sxs-lookup"><span data-stu-id="5aa92-103">The `CorrelationID` element is used to specify a correlation ID for a message.</span></span>  
  
## <a name="format"></a><span data-ttu-id="5aa92-104">Format</span><span class="sxs-lookup"><span data-stu-id="5aa92-104">Format</span></span>  
 <span data-ttu-id="5aa92-105">L'élément `CorrelationID` se compose d'un élément `Expression` qui fait appel à un ou plusieurs éléments `Operation` pour spécifier la chaîne à utiliser en tant qu'ID de corrélation.</span><span class="sxs-lookup"><span data-stu-id="5aa92-105">The `CorrelationID` element consists of an `Expression` element that uses one or more `Operation` elements to specify the string to use as the correlation ID.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="remarks"></a><span data-ttu-id="5aa92-106">Notes</span><span class="sxs-lookup"><span data-stu-id="5aa92-106">Remarks</span></span>  
 <span data-ttu-id="5aa92-107">Les opérations communes suivantes ne sont pas autorisées dans les expressions d'ID de corrélation :</span><span class="sxs-lookup"><span data-stu-id="5aa92-107">The following common operations are not allowed in correlation ID expressions:</span></span>  
  
-   <span data-ttu-id="5aa92-108">And</span><span class="sxs-lookup"><span data-stu-id="5aa92-108">And</span></span>  
  
-   <span data-ttu-id="5aa92-109">Égal à</span><span class="sxs-lookup"><span data-stu-id="5aa92-109">Equals</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aa92-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="5aa92-110">Example</span></span>  
 <span data-ttu-id="5aa92-111">Le bloc de configuration de l'exemple d'intercepteur WF (Workflow Foundation) suivant utilise « OrderNum » pour définir un ID de corrélation.</span><span class="sxs-lookup"><span data-stu-id="5aa92-111">The following Workflow Foundation (WF) interceptor sample configuration block uses "OrderNum" to establish a correlation ID.</span></span> <span data-ttu-id="5aa92-112">À l'aide de WF et d'opérations communes, vous pouvez créer des expressions d'une grande complexité afin de construire un ID de corrélation approprié à votre workflow.</span><span class="sxs-lookup"><span data-stu-id="5aa92-112">Using the WF and common operations, you can build sophisticated expressions to construct an appropriate correlation ID for your workflow.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>OrderNum</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 <span data-ttu-id="5aa92-113">Pour les applications WCF (Windows Communication Foundation), vous pouvez utiliser des opérations communes et d'autres spécifiques à WCF afin de construire un ID de corrélation.</span><span class="sxs-lookup"><span data-stu-id="5aa92-113">For Windows Communication Foundation (WCF) applications, you can use WCF-specific and common operations to construct a correlation ID.</span></span> <span data-ttu-id="5aa92-114">L’exemple suivant utilise le **XPath** opération et XPath pour récupérer un numéro de carte de crédit à partir d’un message pour une utilisation en tant qu’un ID de corrélation :</span><span class="sxs-lookup"><span data-stu-id="5aa92-114">The following sample uses the **XPath** operation and XPath to retrieve a credit card number from a message for use as a correlation ID:</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wcf:Operation Name ="XPath">  
      <wcf:Argument>//s:Body/creditCard:CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5aa92-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5aa92-115">See Also</span></span>  
 [<span data-ttu-id="5aa92-116">Élément OnEvent de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="5aa92-116">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)