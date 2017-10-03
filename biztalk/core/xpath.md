---
title: XPath | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444b5eb9-0c00-4225-918e-b973532c67d0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ee46838596a55512df5d1476f2c3ba34b1f5cb9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xpath"></a><span data-ttu-id="c79cc-102">XPath</span><span class="sxs-lookup"><span data-stu-id="c79cc-102">XPath</span></span>
<span data-ttu-id="c79cc-103">Transmet la valeur indiquée par une instruction XPath.</span><span class="sxs-lookup"><span data-stu-id="c79cc-103">Pushes the value indicated by an XPath statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c79cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c79cc-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="XPath">  
  <wcf:Argument>//po:POID</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c79cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c79cc-105">Parameters</span></span>  
 <span data-ttu-id="c79cc-106">Instruction XPath valide.</span><span class="sxs-lookup"><span data-stu-id="c79cc-106">Valid XPath statement.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="c79cc-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="c79cc-107">Pushed Value</span></span>  
 <span data-ttu-id="c79cc-108">Valeur de chaîne du résultat obtenu en exécutant l'instruction XPath.</span><span class="sxs-lookup"><span data-stu-id="c79cc-108">String value of the result found by executing the XPath statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c79cc-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c79cc-109">Remarks</span></span>  
 <span data-ttu-id="c79cc-110">Vous devez utiliser une instruction XPath valide.</span><span class="sxs-lookup"><span data-stu-id="c79cc-110">You must use a valid XPath statement.</span></span>  
  
 <span data-ttu-id="c79cc-111">Si plusieurs correspondances sont trouvées, seule la première est utilisée.</span><span class="sxs-lookup"><span data-stu-id="c79cc-111">In the case of multiple matches, only the first match is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c79cc-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c79cc-112">Example</span></span>  
 <span data-ttu-id="c79cc-113">L'exemple d'expression suivant construit une valeur de corrélation par la concaténation d'une constante « C_ » avec l'ID de bon de commande du message actuel.</span><span class="sxs-lookup"><span data-stu-id="c79cc-113">The following example expression constructs a correlation value by concatenating a constant "C_" with the purchase order ID from the current message.</span></span> <span data-ttu-id="c79cc-114">L'ID de bon de commande est récupéré via l'opération XPath.</span><span class="sxs-lookup"><span data-stu-id="c79cc-114">The purchase order ID is retrieved by using the XPath operation.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>C_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//po:POID</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c79cc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c79cc-115">See Also</span></span>  
 [<span data-ttu-id="c79cc-116">Opérations dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c79cc-116">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)