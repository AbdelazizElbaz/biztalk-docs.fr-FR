---
title: "Persistance et le moteur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration engine, persistence
- persistence
- orchestration engine, serialization
ms.assetid: 088230ef-13b3-440b-9875-6449f29dd5c6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e9e1c8b158d313681a6e1374a586ca957b1aa15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="persistence-and-the-orchestration-engine"></a><span data-ttu-id="142d0-102">Persistance et moteur d'orchestration</span><span class="sxs-lookup"><span data-stu-id="142d0-102">Persistence and the Orchestration Engine</span></span>
<span data-ttu-id="142d0-103">La persistance d'état, sa gestion et sa restauration, sont au cœur de nombreuses fonctionnalités fondamentales du moteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="142d0-103">State persistence, its management and restoration form the basis of a lot of fundamental functionalities of the orchestration engine.</span></span> <span data-ttu-id="142d0-104">La persistance est particulièrement essentielle au fonctionnement correct de :</span><span class="sxs-lookup"><span data-stu-id="142d0-104">In particular, persistence is critical to the correct functioning of:</span></span>  
  
-   <span data-ttu-id="142d0-105">La mise en attente et la réactivation</span><span class="sxs-lookup"><span data-stu-id="142d0-105">Dehydration and rehydration</span></span>  
  
-   <span data-ttu-id="142d0-106">L'exécution et la réactivation indépendantes de l'ordinateur</span><span class="sxs-lookup"><span data-stu-id="142d0-106">Machine agnostic execution and rehydration</span></span>  
  
-   <span data-ttu-id="142d0-107">Le modèle de compensation</span><span class="sxs-lookup"><span data-stu-id="142d0-107">Compensation model</span></span>  
  
-   <span data-ttu-id="142d0-108">L'arrêt contrôlé du système</span><span class="sxs-lookup"><span data-stu-id="142d0-108">Controlled System Shutdown</span></span>  
  
-   <span data-ttu-id="142d0-109">Récupération</span><span class="sxs-lookup"><span data-stu-id="142d0-109">Recovery</span></span>  
  
 <span data-ttu-id="142d0-110">Le moteur d'orchestration enregistre dans un stockage permanent l'état global d'une instance d'orchestration en cours d'exécution à différents stades, de manière à pouvoir ultérieurement restaurer intégralement l'instance.</span><span class="sxs-lookup"><span data-stu-id="142d0-110">The orchestration engine saves to persistent storage the entire state of a running orchestration instance at various points, so that the instance can later be completely restored in memory.</span></span> <span data-ttu-id="142d0-111">L'état inclut :</span><span class="sxs-lookup"><span data-stu-id="142d0-111">The state includes:</span></span>  
  
-   <span data-ttu-id="142d0-112">l'état interne du moteur, y compris sa progression actuelle ;</span><span class="sxs-lookup"><span data-stu-id="142d0-112">The internal state of the engine, including its current progress.</span></span>  
  
-   <span data-ttu-id="142d0-113">l'état de tous les composants .NET qui contiennent des informations concernant l’état et qui sont utilisés par l'orchestration ;</span><span class="sxs-lookup"><span data-stu-id="142d0-113">The state of any .NET components that maintain state information and are being used by the orchestration.</span></span>  
  
-   <span data-ttu-id="142d0-114">les valeurs des messages et des variables.</span><span class="sxs-lookup"><span data-stu-id="142d0-114">Message and variable values.</span></span>  
  
## <a name="persistence-points"></a><span data-ttu-id="142d0-115">Points de persistance</span><span class="sxs-lookup"><span data-stu-id="142d0-115">Persistence Points</span></span>  
 <span data-ttu-id="142d0-116">Le moteur d'orchestration enregistre l'état d'une instance d'orchestration en cours d'exécution en différents points.</span><span class="sxs-lookup"><span data-stu-id="142d0-116">The orchestration engine saves the state of a running orchestration instance at various points.</span></span> <span data-ttu-id="142d0-117">S'il doit réalimenter l'instance d'orchestration, redémarrer après un arrêt contrôlé ou récupérer après un arrêt inattendu, il exécutera l'instance d'orchestration à partir du dernier point de persistance, comme si rien ne s’était produit.</span><span class="sxs-lookup"><span data-stu-id="142d0-117">If it needs to rehydrate the orchestration instance, start up from a controlled shutdown, or recover from an unexpected shutdown, it will run the orchestration instance from the last persistence point, as though nothing else had occurred.</span></span> <span data-ttu-id="142d0-118">Par exemple, si un message est reçu mais qu’un arrêt inattendu se produise avant que l'état puisse être enregistré, le moteur n'enregistre pas la réception du message et le reçoit de nouveau au redémarrage.</span><span class="sxs-lookup"><span data-stu-id="142d0-118">For example, if a message is received but there is an unexpected shutdown before state can be saved, the engine will not record that it has received the message, and will receive it again upon restarting.</span></span> <span data-ttu-id="142d0-119">Le moteur enregistre l'état d'une orchestration dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="142d0-119">The engine will save the state of an orchestration in the following circumstances:</span></span>  
  
-   <span data-ttu-id="142d0-120">La fin d'une étendue transactionnelle est atteinte.</span><span class="sxs-lookup"><span data-stu-id="142d0-120">The end of a transactional scope is reached.</span></span>  
  
    -   <span data-ttu-id="142d0-121">Le moteur enregistre l'état à la fin d'une étendue transactionnelle afin de définir sans ambiguïté le point à partir duquel reprendre l'orchestration et afin que la compensation puisse être effectuée correctement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="142d0-121">The engine saves state at the end of a transactional scope so that the point at which the orchestration should resume is defined unambiguously, and so that compensation can be carried out correctly if necessary.</span></span>  
  
    -   <span data-ttu-id="142d0-122">L'orchestration continuera à être exécutée à partir de la fin de l'étendue si la persistance a réussi ; autrement, le gestionnaire d'exceptions approprié sera appelé.</span><span class="sxs-lookup"><span data-stu-id="142d0-122">The orchestration will continue to run from the end of the scope if persistence was successful; otherwise, the appropriate exception handler will be invoked.</span></span>  
  
    -   <span data-ttu-id="142d0-123">Si l'étendue est transactionnelle et atomique, le moteur enregistre l'état à l'extrémité de l'étendue atomique lorsqu'il est validé.</span><span class="sxs-lookup"><span data-stu-id="142d0-123">If the scope is transactional and atomic, the engine will save state at the end of the atomic scope when it commits.</span></span>  
  
    -   <span data-ttu-id="142d0-124">Si l'étendue est transactionnelle et à long terme, le moteur génère une nouvelle transaction et conserve l'état complet de l’exécution lorsque l'étendue est complète.</span><span class="sxs-lookup"><span data-stu-id="142d0-124">If the scope is transactional and long-running, the engine will generate a new transaction and persist the complete state of the runtime when the scope completes.</span></span>  
  
-   <span data-ttu-id="142d0-125">Un point d'arrêt de débogage est atteint.</span><span class="sxs-lookup"><span data-stu-id="142d0-125">A debugging breakpoint is reached.</span></span>  
  
-   <span data-ttu-id="142d0-126">Un message est envoyé.</span><span class="sxs-lookup"><span data-stu-id="142d0-126">A message is sent.</span></span> <span data-ttu-id="142d0-127">La seule exception à cet état de fait se produit lorsqu' un message est envoyé depuis une étendue de transaction atomique.</span><span class="sxs-lookup"><span data-stu-id="142d0-127">The only exception to this is when a message is sent from within an atomic transaction scope.</span></span>  
  
-   <span data-ttu-id="142d0-128">L’orchestration démarre une autre orchestration de manière asynchrone, comme avec la **démarrer Orchestration** forme.</span><span class="sxs-lookup"><span data-stu-id="142d0-128">The orchestration starts another orchestration asynchronously, as with the **Start Orchestration** shape.</span></span>  
  
-   <span data-ttu-id="142d0-129">L'instance d'orchestration est suspendue.</span><span class="sxs-lookup"><span data-stu-id="142d0-129">The orchestration instance is suspended.</span></span>  
  
-   <span data-ttu-id="142d0-130">Lorsque le moteur d'orchestration est invité à s'arrêter, il tente d'enregistrer les informations de contrôle ainsi que l'état actuel de toutes les instances d'orchestration en cours d'exécution afin de pouvoir reprendre leur exécution lors de son redémarrage.</span><span class="sxs-lookup"><span data-stu-id="142d0-130">When the orchestration engine is asked to shut down, it will try to save control information as well as the current state of all running orchestration instances, so that it can resume running them when it is started again.</span></span> <span data-ttu-id="142d0-131">Si le moteur ne parvient pas à enregistrer l'état actuel, il reprendra à la prochaine exécution l'instance d'orchestration à partir du dernier point de persistance qui s'est produit avant l'arrêt.</span><span class="sxs-lookup"><span data-stu-id="142d0-131">If the engine is unsuccessful in saving the current state, the engine will resume the orchestration instance from the last persistence point that occurred before the shutdown.</span></span> <span data-ttu-id="142d0-132">Cela s'applique à l'arrêt contrôlé du système ainsi qu'à l'arrêt anormal.</span><span class="sxs-lookup"><span data-stu-id="142d0-132">This applies to the system shutdown in controlled condition as well as abnormal termination.</span></span>  
  
-   <span data-ttu-id="142d0-133">Le moteur détermine que l'instance doit être mise en attente.</span><span class="sxs-lookup"><span data-stu-id="142d0-133">The engine determines that the instance should be dehydrated.</span></span>  
  
-   <span data-ttu-id="142d0-134">L'instance d'orchestration est terminée.</span><span class="sxs-lookup"><span data-stu-id="142d0-134">The orchestration instance is finished.</span></span>  
  
## <a name="serialization"></a><span data-ttu-id="142d0-135">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="142d0-135">Serialization</span></span>  
 <span data-ttu-id="142d0-136">Toutes les instances d'objets auxquelles votre orchestration fait directement ou indirectement référence (par le biais d’autres objets) doivent être sérialisables pour que l'état de votre orchestration soit conservé.</span><span class="sxs-lookup"><span data-stu-id="142d0-136">All object instances that your orchestration refers to directly or indirectly (as through other objects) must be serializable for your orchestration state to be persisted.</span></span> <span data-ttu-id="142d0-137">Il existe deux exceptions à cela :</span><span class="sxs-lookup"><span data-stu-id="142d0-137">There are two exceptions:</span></span>  
  
-   <span data-ttu-id="142d0-138">Un objet non sérialisable peut être déclaré dans une transaction atomique.</span><span class="sxs-lookup"><span data-stu-id="142d0-138">You can have a nonserializable object declared inside an atomic transaction.</span></span> <span data-ttu-id="142d0-139">Cette situation est rendue possible, car les étendues atomiques ne contiennent pas de points de persistance.</span><span class="sxs-lookup"><span data-stu-id="142d0-139">You can do this because atomic scopes do not contain persistence points.</span></span>  
  
-   <span data-ttu-id="142d0-140">System.Xml.XmlDocument n'est pas une classe sérialisable ; il correspond à un cas particulier et peut être utilisé à n’importe quel endroit.</span><span class="sxs-lookup"><span data-stu-id="142d0-140">System.Xml.XmlDocument is not a serializable class; it is handled as a special case and can be used anywhere.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="142d0-141">Pour qu’un objet .NET soit conservé, il doit être marqué comme sérialisable.</span><span class="sxs-lookup"><span data-stu-id="142d0-141">In order for a .NET object to be persisted, it must be marked as serializable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="142d0-142">Les objets COM ne peuvent pas être conservés à l’aide des procédures de sérialisation .NET standard.</span><span class="sxs-lookup"><span data-stu-id="142d0-142">COM objects cannot be persisted using standard .NET serialization procedures.</span></span> <span data-ttu-id="142d0-143">Si vous voulez appeler un objet COM en dehors d'une transaction atomique, vous devez englober l'objet COM dans un objet .NET sérialisable et pouvant conserver et restaurer l’état de l’objet COM.</span><span class="sxs-lookup"><span data-stu-id="142d0-143">If you want to call a COM object outside of an atomic transaction, you must wrap the COM object in a .NET object that is .NET serializable and knows how to persist and restore the state of the COM object.</span></span>  
  
## <a name="system-shutdown"></a><span data-ttu-id="142d0-144">Arrêt du système</span><span class="sxs-lookup"><span data-stu-id="142d0-144">System Shutdown</span></span>  
 <span data-ttu-id="142d0-145">Lorsque le moteur d'orchestration est invité à s'arrêter, il tente d'enregistrer les informations de contrôle ainsi que l'état actuel de toutes les instances d'orchestration en cours d'exécution afin de pouvoir reprendre leur exécution lors de son redémarrage.</span><span class="sxs-lookup"><span data-stu-id="142d0-145">When the orchestration engine is asked to shut down, it will try to save control information as well as the current state of all running orchestration instances, so that it can resume running them when it is started again.</span></span> <span data-ttu-id="142d0-146">Si le moteur ne parvient pas à enregistrer l'état actuel, il reprendra à la prochaine exécution l'instance d'orchestration à partir du dernier point de persistance qui s'est produit avant l'arrêt.</span><span class="sxs-lookup"><span data-stu-id="142d0-146">If the engine is unsuccessful in saving the current state, the engine will resume the orchestration instance from the last persistence point that occurred before the shutdown.</span></span> <span data-ttu-id="142d0-147">Cela s'applique à l'arrêt contrôlé du système ainsi qu'à l'arrêt anormal.</span><span class="sxs-lookup"><span data-stu-id="142d0-147">This applies to the system shutdown in controlled condition as well as abnormal termination.</span></span>  
  
## <a name="recovery"></a><span data-ttu-id="142d0-148">Récupération</span><span class="sxs-lookup"><span data-stu-id="142d0-148">Recovery</span></span>  
 <span data-ttu-id="142d0-149">Le moteur enregistre régulièrement les informations d'état d'une instance d'orchestration dans un stockage permanent et enregistre également l'état en cas d'arrêt du système.</span><span class="sxs-lookup"><span data-stu-id="142d0-149">The engine regularly saves to persistent storage the state information of an orchestration instance, and it also saves state in the event of a system shutdown.</span></span>  
  
 <span data-ttu-id="142d0-150">Lorsqu'une instance d'orchestration échoue anormalement pour une raison ou une autre, elle peut être récupérée à partir du dernier état persistant et peut continuer à s'exécuter comme si aucune interruption n'avait eu lieu.</span><span class="sxs-lookup"><span data-stu-id="142d0-150">When an orchestration instance fails abnormally for whatever reason, the instance can be recovered from the last persisted state, and it can continue to run as if there were no interruption.</span></span> <span data-ttu-id="142d0-151">Cela sera le cas même si le serveur d'origine sur lequel s'est exécutée l'instance tombe en panne pour une raison quelconque ; l'instance peut simplement reprendre son exécution sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="142d0-151">This is true even if the original server that the instance ran on goes out of service for some reason; the instance can simply resume running on a separate machine.</span></span> <span data-ttu-id="142d0-152">En raison de ce modèle de récupération multi-serveur, vous n'avez plus besoin d'effectuer de mises en cluster.</span><span class="sxs-lookup"><span data-stu-id="142d0-152">Because of this multi-server recovery model, you no longer need clustering.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142d0-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="142d0-153">See Also</span></span>  
 [<span data-ttu-id="142d0-154">Mise en attente de l’orchestration et la réactivation</span><span class="sxs-lookup"><span data-stu-id="142d0-154">Orchestration Dehydration and Rehydration</span></span>](../core/orchestration-dehydration-and-rehydration.md)