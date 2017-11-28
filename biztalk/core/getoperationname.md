---
title: GetOperationName | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f858269c-d412-43e3-85e1-398afa9375ab
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e22020add39840b0d2fe4c2fd88156321a18c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getoperationname"></a><span data-ttu-id="09b8b-102">GetOperationName</span><span class="sxs-lookup"><span data-stu-id="09b8b-102">GetOperationName</span></span>
<span data-ttu-id="09b8b-103">Transmet le nom de l'opération actuelle sur la pile.</span><span class="sxs-lookup"><span data-stu-id="09b8b-103">Pushes the name of the current operation onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09b8b-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="GetOperationName" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09b8b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09b8b-105">Parameters</span></span>  
 <span data-ttu-id="09b8b-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="09b8b-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="09b8b-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="09b8b-107">Pushed Value</span></span>  
 <span data-ttu-id="09b8b-108">Chaîne contenant le nom de l'opération actuelle.</span><span class="sxs-lookup"><span data-stu-id="09b8b-108">String containing the name of the current operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09b8b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="09b8b-109">Remarks</span></span>  
 <span data-ttu-id="09b8b-110">Lors de l'utilisation de GetOperationName, veillez à comparer le nom de l'opération tel qu'il est appelé par votre application.</span><span class="sxs-lookup"><span data-stu-id="09b8b-110">When using GetOperationName, make sure you compare the operation name as it is invoked by your application.</span></span> <span data-ttu-id="09b8b-111">Par exemple, si vous utilisez l'attribut de nom d'un contrat de service pour affecter un nom personnalisé, le serveur proxy par défaut du client se verra attribuer le nom personnalisé de la méthode.</span><span class="sxs-lookup"><span data-stu-id="09b8b-111">For example, if you use the name attribute on a service contract to assign a custom name, the client will have its default proxy generated with the custom name for the method.</span></span> <span data-ttu-id="09b8b-112">Toutefois, l'application serveur utilisera les noms de méthodes réels des opérations correspondantes, et non ceux spécifiés dans l'attribut de nom.</span><span class="sxs-lookup"><span data-stu-id="09b8b-112">However, the server application will use the actual method names for the corresponding operations and not the one specified in the name attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09b8b-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="09b8b-113">Example</span></span>  
 <span data-ttu-id="09b8b-114">Dans l'exemple suivant, `GetOperationName` permet de créer une expression qui effectue un filtre sur l'opération nommée « AuthorizePayment ».</span><span class="sxs-lookup"><span data-stu-id="09b8b-114">In the following sample, `GetOperationName` is used to build an expression that filters for the operation named "AuthorizePayment".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>AuthorizePayment</ic:Argument>  
    </ic:Operation>  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09b8b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09b8b-115">See Also</span></span>  
 [<span data-ttu-id="09b8b-116">Opérations dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="09b8b-116">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)