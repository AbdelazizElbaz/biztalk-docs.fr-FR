---
title: Objet Recaller | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recaller object
- Invoke method
- process management solution tutorial, Recaller object
- process management solution tutorial, errors
ms.assetid: b30ad1ae-475f-4913-b402-4d3263fcf072
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f7703eb9145b1249872902d0b867fe22622ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-recaller-object"></a><span data-ttu-id="f1cca-102">Objet Recaller</span><span class="sxs-lookup"><span data-stu-id="f1cca-102">The Recaller Object</span></span>
<span data-ttu-id="f1cca-103">La solution de gestion des processus d'entreprise fournit des appels de méthodes d'objet ayant échoué afin de réaliser, de façon générique, de nouvelles tentatives d'appels.</span><span class="sxs-lookup"><span data-stu-id="f1cca-103">The business process management solution provides for retrying, in a generic way, some failed object method calls.</span></span> <span data-ttu-id="f1cca-104">La solution procède par l’intermédiaire du **Recaller** de l’objet dans le **ExceptionHandler** orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1cca-104">The solution does this through the **Recaller** object in the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="f1cca-105">Le **ExceptionHandler** orchestration utilise l’objet de nouvelles tentatives d’appels de méthode d’objet.</span><span class="sxs-lookup"><span data-stu-id="f1cca-105">The **ExceptionHandler** orchestration uses the object to retry object method calls.</span></span> <span data-ttu-id="f1cca-106">Pour plus d’informations, consultez [l’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="f1cca-106">For more information, see [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md).</span></span>  
  
## <a name="the-invoke-method"></a><span data-ttu-id="f1cca-107">La méthode Invoke</span><span class="sxs-lookup"><span data-stu-id="f1cca-107">The Invoke Method</span></span>  
 <span data-ttu-id="f1cca-108">Le **Recaller** objet possède une méthode unique, statique, **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="f1cca-108">The **Recaller** object has a single, static method, **Invoke**.</span></span> <span data-ttu-id="f1cca-109">Car elle est statique, vous devez jamais créer une instance de la **Recaller** objet.</span><span class="sxs-lookup"><span data-stu-id="f1cca-109">Because it is static, you never need to create an instance of the **Recaller** object.</span></span> <span data-ttu-id="f1cca-110">Vous pouvez utiliser la **Invoke** méthode de trois façons : pour construire un objet, pour appeler une méthode statique pour un objet ou d’appeler une méthode non statique d’un objet.</span><span class="sxs-lookup"><span data-stu-id="f1cca-110">You can use the **Invoke** method in three ways: to construct an object, to call a static method for an object, or to call a non-static method for an object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1cca-111">Le **Invoke** méthode sert de wrapper pour le **Type.InvokeMember** méthode dans le [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="f1cca-111">The **Invoke** method serves as a wrapper for the **Type.InvokeMember** method in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Class Library.</span></span>  
  
### <a name="arguments-for-the-invoke-method"></a><span data-ttu-id="f1cca-112">Arguments pour la méthode Invoke</span><span class="sxs-lookup"><span data-stu-id="f1cca-112">Arguments for the Invoke Method</span></span>  
 <span data-ttu-id="f1cca-113">Le tableau suivant décrit les arguments pour le **Invoke** méthode :</span><span class="sxs-lookup"><span data-stu-id="f1cca-113">The following table describes arguments for the **Invoke** method:</span></span>  
  
|<span data-ttu-id="f1cca-114">Paramètre</span><span class="sxs-lookup"><span data-stu-id="f1cca-114">Parameter</span></span>|<span data-ttu-id="f1cca-115">Type</span><span class="sxs-lookup"><span data-stu-id="f1cca-115">Type</span></span>|<span data-ttu-id="f1cca-116"> Description</span><span class="sxs-lookup"><span data-stu-id="f1cca-116">Description</span></span>|  
|---------------|----------|-----------------|  
|<span data-ttu-id="f1cca-117">*t*</span><span class="sxs-lookup"><span data-stu-id="f1cca-117">*t*</span></span>|<span data-ttu-id="f1cca-118">**Type**</span><span class="sxs-lookup"><span data-stu-id="f1cca-118">**Type**</span></span>|<span data-ttu-id="f1cca-119">Type de l'objet à partir duquel appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="f1cca-119">The type of the object on which to call the method.</span></span>|  
|<span data-ttu-id="f1cca-120">*obj*</span><span class="sxs-lookup"><span data-stu-id="f1cca-120">*obj*</span></span>|<span data-ttu-id="f1cca-121">**Objet**</span><span class="sxs-lookup"><span data-stu-id="f1cca-121">**Object**</span></span>|<span data-ttu-id="f1cca-122">Instance de l'objet à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f1cca-122">The instance of the object to use.</span></span>|  
|<span data-ttu-id="f1cca-123">*methodName*</span><span class="sxs-lookup"><span data-stu-id="f1cca-123">*methodName*</span></span>|<span data-ttu-id="f1cca-124">**chaîne**</span><span class="sxs-lookup"><span data-stu-id="f1cca-124">**string**</span></span>|<span data-ttu-id="f1cca-125">Le nom de la méthode à appeler.</span><span class="sxs-lookup"><span data-stu-id="f1cca-125">The name of the method to invoke.</span></span>|  
|<span data-ttu-id="f1cca-126">*args*</span><span class="sxs-lookup"><span data-stu-id="f1cca-126">*args*</span></span>|<span data-ttu-id="f1cca-127">**Tableau**</span><span class="sxs-lookup"><span data-stu-id="f1cca-127">**Array**</span></span>|<span data-ttu-id="f1cca-128">Un tableau de type **objet** contenant les arguments de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f1cca-128">An array of type **Object** containing the method's arguments.</span></span>|  
  
 <span data-ttu-id="f1cca-129">Pour appeler le constructeur pour un objet, utilisez une chaîne vide (« ») ou **null** pour *methodName*.</span><span class="sxs-lookup"><span data-stu-id="f1cca-129">To call the constructor for an object, use an empty string ("") or **null** for *methodName*.</span></span>  
  
 <span data-ttu-id="f1cca-130">Pour appeler une méthode statique, utilisez **null** pour *obj*.</span><span class="sxs-lookup"><span data-stu-id="f1cca-130">To call a static method, use **null** for *obj*.</span></span>  
  
 <span data-ttu-id="f1cca-131">Pour appeler une méthode non statique, indiquez tous les arguments.</span><span class="sxs-lookup"><span data-stu-id="f1cca-131">To call a non-static method, supply all of the arguments.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1cca-132">À l’aide de **null** comme valeur de l’argument de Type *t*, entraîne **Invoke** pour lever une **ArgumentNullException** exception.</span><span class="sxs-lookup"><span data-stu-id="f1cca-132">Using **null** as the value of the Type argument, *t*, causes **Invoke** to throw an **ArgumentNullException** exception.</span></span> <span data-ttu-id="f1cca-133">L’argument *t* ne doit pas être null, car le **Invoke** utilise le **Type.InvokeMember** [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] (méthode).</span><span class="sxs-lookup"><span data-stu-id="f1cca-133">The argument *t* should not be null because the **Invoke** method uses the **Type.InvokeMember** [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] method.</span></span>  
  
## <a name="calling-invoke"></a><span data-ttu-id="f1cca-134">Appel de la méthode Invoke</span><span class="sxs-lookup"><span data-stu-id="f1cca-134">Calling Invoke</span></span>  
 <span data-ttu-id="f1cca-135">Dans la solution, seule la **ExceptionHandler** d’orchestration utilise la **Recaller** objet.</span><span class="sxs-lookup"><span data-stu-id="f1cca-135">In the solution, only the **ExceptionHandler** orchestration uses the **Recaller** object.</span></span> <span data-ttu-id="f1cca-136">Le **ExceptionHandler** est, à son tour, utilisés par d’autres orchestrations.</span><span class="sxs-lookup"><span data-stu-id="f1cca-136">The **ExceptionHandler** is, in turn, used by other orchestrations.</span></span> <span data-ttu-id="f1cca-137">Les valeurs passées à la **Invoke** méthode proviennent de ces autres orchestrations.</span><span class="sxs-lookup"><span data-stu-id="f1cca-137">The values passed to the **Invoke** method come from these other orchestrations.</span></span> <span data-ttu-id="f1cca-138">Par exemple, le code suivant s’affiche dans le **activer** orchestration dans le **InitialException** forme Expression :</span><span class="sxs-lookup"><span data-stu-id="f1cca-138">For example, the following code appears in the **Activate** orchestration in the **InitialException** Expression shape:</span></span>  
  
```  
Ex = CodeEx;  
ObjectType = orderHandler.GetType();  
CalledObject = orderHandler;  
Reason = "Standard Activate Failed";  
MethodName = "Activate";  
ParameterArray = System.Array.CreateInstance(typeof(System.Object),  
                                              3 );  
ParameterArray.SetValue(ServiceType, 0);  
ParameterArray.SetValue(OrderMsg.CustNum, 1);  
ParameterArray.SetValue(OrderMsg.OrderNum, 2);  
ReturnValue = null; // no return value expected  
  
```  
  
 <span data-ttu-id="f1cca-139">Notez comment le code crée un tableau à l’aide de **System.Array.CreateInstance** et utilise le **SetValue** méthode pour stocker les valeurs y.</span><span class="sxs-lookup"><span data-stu-id="f1cca-139">Notice how the code creates an array using **System.Array.CreateInstance** and uses the **SetValue** method to store the values used in it.</span></span>  
  
 <span data-ttu-id="f1cca-140">Après la forme Expression, l’orchestration appelle la **ExceptionHandler** orchestration.</span><span class="sxs-lookup"><span data-stu-id="f1cca-140">After the Expression shape, the Activate orchestration calls the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="f1cca-141">Le code suivant illustre la manière dont le Concepteur d'orchestration convertit la forme Appel :</span><span class="sxs-lookup"><span data-stu-id="f1cca-141">The following code shows how the orchestration designer translates the Call shape:</span></span>  
  
```  
call Microsoft.Samples.  
    BizTalk.SouthridgeVideo.  
        OrderManager.ExceptionHandlerOrch  
            (  
                Reason,  
                Ex,  
                CalledObject,  
                MethodName,   
                ParameterArray,   
                OrderCorrelation,   
                OrderMsg,   
                out ReturnValue,   
                ObjectType  
            );  
  
```  
  
 <span data-ttu-id="f1cca-142">Dans le **ExceptionHandler** orchestration, le code suivant s’affiche dans le **appeler le Code d’origine** forme Expression :</span><span class="sxs-lookup"><span data-stu-id="f1cca-142">In the **ExceptionHandler** orchestration, the following code appears in the **Call Original Code** Expression shape:</span></span>  
  
```  
ReturnValue =   
    Microsoft.Samples.  
        BizTalk.SouthridgeVideo.  
            Utilities.Recaller.  
                Invoke(  
                    ObjectType,  
                    CalledObject,  
                    MethodName,  
                    ParameterArray  
                );  
```  
  
 <span data-ttu-id="f1cca-143">En dépit du fait que les noms des arguments correspondent à ceux présents dans l'appel de l'orchestration Activate, vous remarquerez que, lors de l'appel d'orchestrations, les arguments sont filtrés par ordre et non pas par nom.</span><span class="sxs-lookup"><span data-stu-id="f1cca-143">Notice that, although the argument names match those in the Activate orchestration's call, arguments are matched by order and not by name when calling orchestrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1cca-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1cca-144">See Also</span></span>  
 <span data-ttu-id="f1cca-145">[Caractéristiques de l’implémentation de la Solution gestion des processus d’entreprise](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="f1cca-145">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="f1cca-146">L’Orchestration ExceptionHandler</span><span class="sxs-lookup"><span data-stu-id="f1cca-146">The ExceptionHandler Orchestration</span></span>](../core/the-exceptionhandler-orchestration.md)