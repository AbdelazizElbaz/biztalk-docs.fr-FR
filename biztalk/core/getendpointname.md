---
title: GetEndpointName | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5a06850-ff6d-4fe4-9834-61d14b117391
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7e7a310c222cead89efd23e3f8202ade9eb47ab
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="getendpointname"></a><span data-ttu-id="999da-102">GetEndpointName</span><span class="sxs-lookup"><span data-stu-id="999da-102">GetEndpointName</span></span>
<span data-ttu-id="999da-103">Transmet le nom du point de terminaison d'interception en cours sur la pile.</span><span class="sxs-lookup"><span data-stu-id="999da-103">Pushes the name of the current interception endpoint onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="999da-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="GetEndpointName" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="999da-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="999da-105">Parameters</span></span>  
 <span data-ttu-id="999da-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="999da-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="999da-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="999da-107">Pushed Value</span></span>  
 <span data-ttu-id="999da-108">Chaîne contenant le nom du point de terminaison d'interception en cours.</span><span class="sxs-lookup"><span data-stu-id="999da-108">String containing the current interception endpoint name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="999da-109">Notes</span><span class="sxs-lookup"><span data-stu-id="999da-109">Remarks</span></span>  
 <span data-ttu-id="999da-110">Il est important de noter que les applications client et serveur renvoient des noms différents pour le point de terminaison spécifié dans les fichiers App.config.</span><span class="sxs-lookup"><span data-stu-id="999da-110">It is important to note that the client and server applications will return different names for the same endpoint name specified in the App.config files.</span></span>  
  
 <span data-ttu-id="999da-111">Pour les applications clientes, le nom du point de terminaison extrait par l'opération GetEndPointName est au format suivant : nom de liaison, suivi d'un trait de soulignement et du nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="999da-111">For client applications, the endpoint name retrieved by the GetEndPointName operation is the binding name followed by an underscore and the contract name.</span></span>  
  
 <span data-ttu-id="999da-112">Par exemple, si la propriété nom de ServiceEndpoint n’est pas définie, mais la liaison est définie, le nom défini \< *liaison*\>_\<*contrat* \>.</span><span class="sxs-lookup"><span data-stu-id="999da-112">For example, if the Name property on ServiceEndpoint is not set but the binding is set, the name will be set to \<*binding*\>_\<*contract*\>.</span></span>  
  
 <span data-ttu-id="999da-113">Si le nom et la liaison ne sont pas définies, la propriété Name est fixée \< *contrat*\>.</span><span class="sxs-lookup"><span data-stu-id="999da-113">If the name and binding are not set, the Name property will be set to \<*contract*\>.</span></span>  
  
 <span data-ttu-id="999da-114">Pour le service, le nom extrait correspond au nom du point de terminaison spécifié dans le fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="999da-114">For the service, the name retrieved is the endpoint name specified in the App.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="999da-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="999da-115">Example</span></span>  
 <span data-ttu-id="999da-116">L'exemple d'expression de filtre suivante définit une interception pour l'opération Réception pour le point d'appel de contrat ServiceRequest du point de terminaison PurchaseOrder_EP.</span><span class="sxs-lookup"><span data-stu-id="999da-116">The following example filter expression defines an interception for the Receive operation for the ServiceRequest contract call point for the PurchaseOrder_EP endpoint.</span></span> <span data-ttu-id="999da-117">La procédure à suivre est la suivante :</span><span class="sxs-lookup"><span data-stu-id="999da-117">This is done in the following logical steps:</span></span>  
  
1.  <span data-ttu-id="999da-118">Comparez le nom de l'opération en cours à « Réception » et transmettez le résultat (True ou False) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="999da-118">Compare the current operation name to "Receive" and push the result (true or false) onto the stack.</span></span>  
  
2.  <span data-ttu-id="999da-119">Comparez le point d'appel de contrat de service en cours à « ServiceRequest » et transmettez le résultat (True ou False) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="999da-119">Compare the current service contract call point to "ServiceRequest" and push the result (true or false) onto the stack.</span></span> <span data-ttu-id="999da-120">La pile inclut désormais deux valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="999da-120">There are now two Boolean values on the stack.</span></span>  
  
3.  <span data-ttu-id="999da-121">Comparez les résultats des étapes précédentes à l’aide d’une valeur booléenne **et** opération et transmettez le résultat dans la pile.</span><span class="sxs-lookup"><span data-stu-id="999da-121">Compare the results of the preceding steps using a Boolean **And** operation and push the result on the stack.</span></span> <span data-ttu-id="999da-122">La pile n'inclut désormais qu'une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="999da-122">This leaves one Boolean value on the stack.</span></span>  
  
4.  <span data-ttu-id="999da-123">Comparez le point de terminaison en cours à « PurchaseOrder_EP » et transmettez le résultat (True ou False) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="999da-123">Compare the current endpoint to "PurchaseOrder_EP" and push the result (true or false) onto the stack.</span></span> <span data-ttu-id="999da-124">La pile inclut désormais deux valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="999da-124">There are now two Boolean values on the stack.</span></span>  
  
5.  <span data-ttu-id="999da-125">Enfin, comparez les deux valeurs booléennes sur la pile à l’aide d’une valeur booléenne **et** opération et transmettez le résultat dans la pile.</span><span class="sxs-lookup"><span data-stu-id="999da-125">Finally, compare the two Boolean values on the stack using a Boolean **And** operation and push the result onto the stack.</span></span> <span data-ttu-id="999da-126">Ces opérations permettent de vérifier le résultat de la comparaison du point de terminaison par rapport à une valeur booléenne : True si le nom de l'opération et le point d'appel de contrat correspondent, False dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="999da-126">This checks the result of the endpoint comparison against a Boolean value, which is true if the operation name and contract call point successfully matched, and which is false otherwise.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ServiceRequest</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wcf:Operation Name="GetEndpointName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>PurchaseOrder_EP</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a><span data-ttu-id="999da-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="999da-127">See Also</span></span>  
 [<span data-ttu-id="999da-128">Opérations dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="999da-128">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)