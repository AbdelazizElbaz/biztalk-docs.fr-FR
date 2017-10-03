---
title: GetServiceContractCallPoint | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be03d100-0cba-4b80-8056-b582a2cd74ce
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e291bcf733129991f6d3b5000ca8e9bc1353057
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getservicecontractcallpoint"></a><span data-ttu-id="a4ec0-102">GetServiceContractCallPoint</span><span class="sxs-lookup"><span data-stu-id="a4ec0-102">GetServiceContractCallPoint</span></span>
<span data-ttu-id="a4ec0-103">Transmet le nom du point d'appel de contrat de service actuel sur la pile.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-103">Pushes the name of the current service contract call point onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ec0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4ec0-104">Syntax</span></span>  
  
```  
  
<wcf:Operation Name="GetServiceContractCallPoint" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4ec0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4ec0-105">Parameters</span></span>  
 <span data-ttu-id="a4ec0-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="a4ec0-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="a4ec0-107">Pushed Value</span></span>  
 <span data-ttu-id="a4ec0-108">Chaîne contenant le point d'appel de contrat actuel.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-108">String containing the current contract call point.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4ec0-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a4ec0-109">Remarks</span></span>  
 <span data-ttu-id="a4ec0-110">Un service Windows Communication Framework peut être intercepté à différents points pendant la durée de vie du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-110">A Windows Communication Framework service can be intercepted at different points in the lifetime of the service contract.</span></span> <span data-ttu-id="a4ec0-111">Ces emplacements sont définis par l'énumération `System.BizTalk.Bam.Interceptors.Wcf.ContractCallPoint` :</span><span class="sxs-lookup"><span data-stu-id="a4ec0-111">These locations are defined by the `System.BizTalk.Bam.Interceptors.Wcf.ContractCallPoint` enumeration:</span></span>  
  
|<span data-ttu-id="a4ec0-112">Point d'appel de contrat</span><span class="sxs-lookup"><span data-stu-id="a4ec0-112">Contract call point</span></span>|<span data-ttu-id="a4ec0-113">Description</span><span class="sxs-lookup"><span data-stu-id="a4ec0-113">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="a4ec0-114">ClientReply</span><span class="sxs-lookup"><span data-stu-id="a4ec0-114">ClientReply</span></span>|<span data-ttu-id="a4ec0-115">Point d'appel de réponse client.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-115">Client reply call point.</span></span>|  
|<span data-ttu-id="a4ec0-116">ClientRequest</span><span class="sxs-lookup"><span data-stu-id="a4ec0-116">ClientRequest</span></span>|<span data-ttu-id="a4ec0-117">Point d'appel de demande client.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-117">Client request call point.</span></span>|  
|<span data-ttu-id="a4ec0-118">ClientFault</span><span class="sxs-lookup"><span data-stu-id="a4ec0-118">ClientFault</span></span>|<span data-ttu-id="a4ec0-119">Point d'erreur client.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-119">Client fault point.</span></span>|  
|<span data-ttu-id="a4ec0-120">ServiceReply</span><span class="sxs-lookup"><span data-stu-id="a4ec0-120">ServiceReply</span></span>|<span data-ttu-id="a4ec0-121">Point d'appel de réponse de service.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-121">Service reply call point.</span></span>|  
|<span data-ttu-id="a4ec0-122">ServiceRequest</span><span class="sxs-lookup"><span data-stu-id="a4ec0-122">ServiceRequest</span></span>|<span data-ttu-id="a4ec0-123">Point d'appel de demande de service.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-123">Service request call point.</span></span>|  
|<span data-ttu-id="a4ec0-124">ServiceFault</span><span class="sxs-lookup"><span data-stu-id="a4ec0-124">ServiceFault</span></span>|<span data-ttu-id="a4ec0-125">Point d'erreur de service.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-125">Service fault point.</span></span>|  
|<span data-ttu-id="a4ec0-126">CallbackRequest</span><span class="sxs-lookup"><span data-stu-id="a4ec0-126">CallbackRequest</span></span>|<span data-ttu-id="a4ec0-127">Point d'appel de demande de rappel.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-127">Callback request call point.</span></span>|  
|<span data-ttu-id="a4ec0-128">CallbackReply</span><span class="sxs-lookup"><span data-stu-id="a4ec0-128">CallbackReply</span></span>|<span data-ttu-id="a4ec0-129">Point d'appel de réponse de rappel.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-129">Callback reply call point.</span></span>|  
|<span data-ttu-id="a4ec0-130">CallbackFault</span><span class="sxs-lookup"><span data-stu-id="a4ec0-130">CallbackFault</span></span>|<span data-ttu-id="a4ec0-131">Point d'erreur de rappel.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-131">Callback fault point.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4ec0-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="a4ec0-132">Example</span></span>  
 <span data-ttu-id="a4ec0-133">L'exemple suivant contient une expression de filtre d'événements configurée pour rechercher une opération spécifique (« Réception ») dans l'état de réponse client</span><span class="sxs-lookup"><span data-stu-id="a4ec0-133">The following sample contains an event filter expression configured to find a specific operation ("Receive") in the client reply state.</span></span> <span data-ttu-id="a4ec0-134">à l'aide d'une combinaison d'opérations comprenant `GetOperationName`, `GetServiceContractCallPoint` ainsi que des opérations logiques.</span><span class="sxs-lookup"><span data-stu-id="a4ec0-134">This is done by using a combination of operations including `GetOperationName`, `GetServiceContractCallPoint`, and logical operations.</span></span>  
  
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
      <ic:Argument>ClientReply</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4ec0-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4ec0-135">See Also</span></span>  
 [<span data-ttu-id="a4ec0-136">Opérations dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a4ec0-136">Operations in Windows Communication Foundation</span></span>](../core/operations-in-windows-communication-foundation.md)