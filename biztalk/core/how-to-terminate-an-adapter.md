---
title: "Comment arrêter un adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfba2b61-b89f-41cd-a014-4e96daec6516
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd2621e15803dd5f6e8f449de530e84df1bc1b9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-terminate-an-adapter"></a><span data-ttu-id="af0f7-102">Comment arrêter un adaptateur</span><span class="sxs-lookup"><span data-stu-id="af0f7-102">How to Terminate an Adapter</span></span>
<span data-ttu-id="af0f7-103">Les rubriques suivantes fournissent des instructions sur la façon appropriée d'arrêter un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="af0f7-103">The following topics provide guidance on the proper shutdown of an adapter.</span></span>  
  
## <a name="terminating-an-adapter"></a><span data-ttu-id="af0f7-104">Arrêt d'un adaptateur</span><span class="sxs-lookup"><span data-stu-id="af0f7-104">Terminating an Adapter</span></span>  
 <span data-ttu-id="af0f7-105">Lorsque le moteur de messagerie s’arrête, il appelle **IBTTransportControl**. **Arrêter** sur chaque adaptateur in-process.</span><span class="sxs-lookup"><span data-stu-id="af0f7-105">When the Messaging Engine is shutting down it calls **IBTTransportControl**.**Terminate** on each in-process adapter.</span></span> <span data-ttu-id="af0f7-106">Après le retour de la méthode, BizTalk Server détruit l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="af0f7-106">After this method returns BizTalk Server will destroy the adapter.</span></span> <span data-ttu-id="af0f7-107">Pour les adaptateurs natifs, cette destruction se produit immédiatement, tandis que pour les adaptateurs gérés, le moment précis de cette destruction est moins déterministe, en raison du processus de nettoyage de la mémoire .NET.</span><span class="sxs-lookup"><span data-stu-id="af0f7-107">For native adapters this occurs immediately, but for managed adapters exactly when this occurs is less deterministic due to the .NET garbage-collection process.</span></span> <span data-ttu-id="af0f7-108">L’adaptateur doit bloquer **Terminate** et effectuer tout travail de nettoyage jusqu'à ce qu’il est prêt à être détruit.</span><span class="sxs-lookup"><span data-stu-id="af0f7-108">The adapter should block in **Terminate** and do any necessary cleanup work until it is ready to be destroyed.</span></span>  
  
## <a name="terminating-isolated-receive-adapters"></a><span data-ttu-id="af0f7-109">Arrêt d'adaptateurs de réception isolés</span><span class="sxs-lookup"><span data-stu-id="af0f7-109">Terminating Isolated Receive Adapters</span></span>  
 <span data-ttu-id="af0f7-110">Isolé de réception cartes ne sont pas **Terminate** appelée sur ces derniers, car ils ne sont pas hébergés dans le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="af0f7-110">Isolated receive adapters do not have **Terminate** called on them because they are not hosted in the BizTalk service.</span></span> <span data-ttu-id="af0f7-111">Au lieu de cela, ils doivent appeler **IBTTransportProxy**. **TerminateIsolatedReceiver** pour informer le moteur de messagerie qu’ils sont sur le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="af0f7-111">Instead, they should call **IBTTransportProxy**.**TerminateIsolatedReceiver** to notify the Messaging Engine that they are about to shut down.</span></span>  
  
## <a name="clean-up-com-objects-by-using-marshalreleasecomobject"></a><span data-ttu-id="af0f7-112">Nettoyage d'objets COM à l'aide de Marshal.ReleaseComObject</span><span class="sxs-lookup"><span data-stu-id="af0f7-112">Clean Up COM Objects by Using Marshal.ReleaseComObject</span></span>  
 <span data-ttu-id="af0f7-113">Lors de la rédaction de code managé utilisant des objets COM, le CLR (Common Language Runtime) génère des objets proxy contenant les références aux objets COM.</span><span class="sxs-lookup"><span data-stu-id="af0f7-113">When writing managed code that uses COM objects, the common language runtime (CLR) generates proxy objects that hold the references to the COM objects.</span></span> <span data-ttu-id="af0f7-114">Les objets proxy sont des objets managés soumis aux règles habituelles du nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="af0f7-114">The proxy objects are managed objects and are subject to the usual rules of garbage collection.</span></span> <span data-ttu-id="af0f7-115">Le problème vient du fait que le garbage collector accède uniquement à la mémoire allouée par les modes d'exécution .NET et qu'il ne tient pas compte de l'objet COM.</span><span class="sxs-lookup"><span data-stu-id="af0f7-115">A problem arises in that the garbage collector only sees memory that the .NET runtimes allocated, and is not aware of the COM object.</span></span> <span data-ttu-id="af0f7-116">Étant donné que les objets proxy sont petits, un grand objet COM peut être oublié dans la mémoire, car le garbage collector CLR ne l'a pas pris en considération.</span><span class="sxs-lookup"><span data-stu-id="af0f7-116">Because the proxy objects are small, a large COM object might be left in memory because the CLR garbage collector is not aware of it.</span></span>  
  
 <span data-ttu-id="af0f7-117">Pour éviter ce problème, explicitement libérer des objets COM sous-jacents lorsque vous avez terminé avec eux, en particulier les **IBTTransportBatch** objets.</span><span class="sxs-lookup"><span data-stu-id="af0f7-117">To avoid this problem, explicitly release underlying COM objects when you are finished with them, particularly any **IBTTransportBatch** objects.</span></span> <span data-ttu-id="af0f7-118">Pour cela, vous devez appeler **marshaler**. **ReleaseComObject**.</span><span class="sxs-lookup"><span data-stu-id="af0f7-118">You do this by calling **Marshal**.**ReleaseComObject**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af0f7-119">**ReleaseComObject** retourne le nombre de références restantes et libère uniquement l’objet COM lorsque la valeur retournée est zéro.</span><span class="sxs-lookup"><span data-stu-id="af0f7-119">**ReleaseComObject** returns the number of remaining references and only releases the COM object when this returned value is zero.</span></span> <span data-ttu-id="af0f7-120">Souvent **ReleaseComObject** est appelée dans une boucle afin de garantir que l’objet est libéré.</span><span class="sxs-lookup"><span data-stu-id="af0f7-120">Often **ReleaseComObject** is called in a loop to ensure that the object is released.</span></span> <span data-ttu-id="af0f7-121">Une fois cette opération terminée, vous devez appeler **SuppressFinalize** sur cet objet, car il n’a rien à finaliser.</span><span class="sxs-lookup"><span data-stu-id="af0f7-121">After that is complete, you should call **SuppressFinalize** on this object because there is nothing to finalize.</span></span> <span data-ttu-id="af0f7-122">La dernière étape consiste à vérifier l'existence de l'objet COM.</span><span class="sxs-lookup"><span data-stu-id="af0f7-122">One last step is to check whether this really is a COM object.</span></span>  
  
 <span data-ttu-id="af0f7-123">Le code suivant présente le processus décrit ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="af0f7-123">The following code shows the process descrjbed above:</span></span>  
  
```  
if (Marshal.IsComObject (batch))  
(  
While (0 <Marshal.ReleaseComObject(batch)  
;  
GC.SuppressFinalize (batch);  
  
```  
  
 <span data-ttu-id="af0f7-124">Libérer explicitement les **IBTTransportBatch** objet retourné à partir de **GetBatch** peut apporter une amélioration significative des performances.</span><span class="sxs-lookup"><span data-stu-id="af0f7-124">Explicitly releasing the **IBTTransportBatch** object returned from **GetBatch** can make a significant improvement to performance.</span></span>  
  
## <a name="always-use-terminate-when-closing-an-adapter"></a><span data-ttu-id="af0f7-125">Utilisation systématique de Terminate lors de l'arrêt d'un adaptateur</span><span class="sxs-lookup"><span data-stu-id="af0f7-125">Always Use Terminate When Closing an Adapter</span></span>  
 <span data-ttu-id="af0f7-126">Pour que BizTalk Server reconnaisse votre code comme une carte, vous devez implémenter une interface appelée **IBTTransportControl**.</span><span class="sxs-lookup"><span data-stu-id="af0f7-126">For BizTalk Server to recognize your code as an adapter, you must implement an interface called **IBTTransportControl**.</span></span> <span data-ttu-id="af0f7-127">Cette interface détermine la façon dont BizTalk Server communique avec votre adaptateur. Elle est définie de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="af0f7-127">This interface defines how BizTalk Server communicates with your adapter, and is defined as follows:</span></span>  
  
```  
public interface IBTTransportControl   
{  
void Initialize(IBTTransportProxy transportProxy);  
void Terminate();  
}  
```  
  
 <span data-ttu-id="af0f7-128">L’interface contient deux méthodes, **initialiser** et **Terminate**.</span><span class="sxs-lookup"><span data-stu-id="af0f7-128">The interface contains two methods, **Initialize** and **Terminate**.</span></span>  
  
### <a name="initialize"></a><span data-ttu-id="af0f7-129">Initialiser</span><span class="sxs-lookup"><span data-stu-id="af0f7-129">Initialize</span></span>  
 <span data-ttu-id="af0f7-130">BizTalk Server appelle le **initialiser** méthode après avoir chargé l’assembly d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="af0f7-130">BizTalk Server calls the **Initialize** method after it loads the adapter assembly.</span></span> <span data-ttu-id="af0f7-131">Il procède ainsi pour transmettre le proxy de transport (le handle principal vers BizTalk Server) à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="af0f7-131">It does this to pass the transport proxy (the main handle to BizTalk Server) to the adapter.</span></span> <span data-ttu-id="af0f7-132">L’implémentation de **initialiser** stocke simplement le proxy de transport dans une variable membre.</span><span class="sxs-lookup"><span data-stu-id="af0f7-132">The implementation of **Initialize** simply stores the transport proxy in a member variable.</span></span>  
  
### <a name="terminate"></a><span data-ttu-id="af0f7-133">Terminate</span><span class="sxs-lookup"><span data-stu-id="af0f7-133">Terminate</span></span>  
 <span data-ttu-id="af0f7-134">BizTalk Server appelle le **Terminate** méthode lors de l’arrêt du service pour permettre à l’adaptateur le temps de terminer l’exécution de tous les lots.</span><span class="sxs-lookup"><span data-stu-id="af0f7-134">BizTalk Server calls the **Terminate** method on service shutdown to give the adapter time to finish the execution of all batches.</span></span> <span data-ttu-id="af0f7-135">L’implémentation de la **Terminate** méthode beaucoup plus compliqué.</span><span class="sxs-lookup"><span data-stu-id="af0f7-135">This makes the implementation of the **Terminate** method much more involved.</span></span>  
  
 <span data-ttu-id="af0f7-136">L’adaptateur ne doit pas répondre à une **Terminate** appeler jusqu'à la fin de n’importe quel travail en attente, il a.</span><span class="sxs-lookup"><span data-stu-id="af0f7-136">The adapter should not return from a **Terminate** call until any pending work it has is complete.</span></span> <span data-ttu-id="af0f7-137">Lorsque BizTalk Server appelle **Terminate**, l’adaptateur doit essayer d’arrêter toutes ses tâches en cours et ne démarre pas de nouvelles.</span><span class="sxs-lookup"><span data-stu-id="af0f7-137">When BizTalk Server calls **Terminate**, the adapter should try to stop all its current tasks and not start any new ones.</span></span>  
  
 <span data-ttu-id="af0f7-138">Étant donné que **Terminate** est appelée dans le cadre de l’arrêt du service, le Gestionnaire de contrôle de service termine le processus si l’adaptateur bloque perpétuelle **Terminate**.</span><span class="sxs-lookup"><span data-stu-id="af0f7-138">Because **Terminate** is called as part of the service shutdown, the service control manager ends the process if the adapter perpetually blocks in **Terminate**.</span></span> <span data-ttu-id="af0f7-139">Dans ce cas, vous recevez un avertissement du gestionnaire de contrôle de service lorsqu'il arrête le service BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="af0f7-139">In this case, you see the warning from the service control manager as it stops the BizTalk Server service.</span></span> <span data-ttu-id="af0f7-140">Si possible, évitez d'arrêter l'adaptateur prématurément.</span><span class="sxs-lookup"><span data-stu-id="af0f7-140">If possible, avoid terminating the adapter prematurely like this.</span></span> <span data-ttu-id="af0f7-141">Si l'adaptateur ne traite pas le processus d'arrêt de façon appropriée et que des threads sont toujours en cours d'exécution au début du processus d'arrêt, il se peut que vous receviez un message de violation d'accès de la part de BizTalk Server au moment de l'arrêt.</span><span class="sxs-lookup"><span data-stu-id="af0f7-141">If the adapter does not handle the termination process appropriately, and still has threads running when the process starts to shut down, then you may occasionally see an access violation from BizTalk Server on shutdown.</span></span>  
  
 <span data-ttu-id="af0f7-142">En raison de la nature asynchrone de l'interface vers BizTalk Server, il est probable que, en condition de charge, de nombreux lots, et donc de nombreux threads, soient encore en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="af0f7-142">Because of the asynchronous nature of the interface to BizTalk Server, it is likely that under load there will be many batches and therefore threads still being executed.</span></span> <span data-ttu-id="af0f7-143">Le **Terminate** appel doit être implémenté pour attendre la fin de chaque lot que l’adaptateur a correctement exécuté sur le serveur BizTalk avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="af0f7-143">The **Terminate** call should be implemented to wait on the conclusion of every batch the adapter has successfully executed on BizTalk Server before proceeding.</span></span> <span data-ttu-id="af0f7-144">La fin du lot est signalée par le **BatchComplete** rappel à partir de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="af0f7-144">The conclusion of the batch is signaled by the **BatchComplete** callback from BizTalk Server.</span></span> <span data-ttu-id="af0f7-145">Le **Terminate** appel doit attendre tous les rappels **BatchComplete** doit se produire.</span><span class="sxs-lookup"><span data-stu-id="af0f7-145">The **Terminate** call should wait on every pending **BatchComplete** to happen.</span></span> <span data-ttu-id="af0f7-146">En outre, l'exécution des lots doit être réussie.</span><span class="sxs-lookup"><span data-stu-id="af0f7-146">However, the execution of the batch must be successful.</span></span> <span data-ttu-id="af0f7-147">Autrement dit, l’appel à **IBTTransportBatch**::**fait** ne doit pas échouer.</span><span class="sxs-lookup"><span data-stu-id="af0f7-147">That is, the call to **IBTTransportBatch**::**Done** must not fail.</span></span> <span data-ttu-id="af0f7-148">Si l’appel à **IBTTransportBatch**::**fait** échoue, il n’existe aucun rappel de lot.</span><span class="sxs-lookup"><span data-stu-id="af0f7-148">If the call to **IBTTransportBatch**::**Done** fails, there is no batch callback.</span></span>  
  
 <span data-ttu-id="af0f7-149">Ensuite, vous devez ajouter du code de synchronisation à votre adaptateur, procédure relativement simple.</span><span class="sxs-lookup"><span data-stu-id="af0f7-149">After you realize that you have to add synchronization code to your adapter, the implementation is fairly straightforward.</span></span>  
  
 <span data-ttu-id="af0f7-150">Une méthode simple consiste à implémenter un objet de synchronisation composé avec **entrez** et **laisser** méthodes pour les threads de travail et un **Terminer** méthode qui entraîne un blocage lors de l’une thread est toujours à l’intérieur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="af0f7-150">One simple approach is to implement a compound synchronization object with **enter** and **leave** methods for the worker threads and a **terminate** method that blocks while a thread is still within the protected execution.</span></span> <span data-ttu-id="af0f7-151">(D’ailleurs, la solution est très similaire à la structure de lecteurs multiples, seul l’enregistreur familier où les threads de travail peuvent être considérés comme des lecteurs et la **arrêter** le writer de la méthode.)</span><span class="sxs-lookup"><span data-stu-id="af0f7-151">(Incidentally, the solution is very similar to the familiar multiple-reader, single-writer structure where the worker threads can be thought of as readers and the **terminate** method as the writer.)</span></span>  
  
 <span data-ttu-id="af0f7-152">Le **Terminer** méthode est la suivante :</span><span class="sxs-lookup"><span data-stu-id="af0f7-152">The **terminate** method is as follows:</span></span>  
  
```  
void terminate ()  
{  
this.control.Terminate();  
}  
```  
  
 <span data-ttu-id="af0f7-153">Pour chaque thread de travail :</span><span class="sxs-lookup"><span data-stu-id="af0f7-153">For each worker thread:</span></span>  
  
```  
If (!this.control.Enter())  
return; // we can’t enter because Terminate has been called  
try  
{  
//  create and fill batch  
batch.Done();  
}  
catch (Exception)  
{  
//  we are not expecting a callback  
This.control.Leave();  
}  
```  
  
 <span data-ttu-id="af0f7-154">Dans le rappel émis par BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="af0f7-154">In the callback from BizTalk Server:</span></span>  
  
```  
batchComplete (…)  
{  
//  the callback from BizTalk Server  
//  process results  
this.control.Leave();  
}  
```  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="af0f7-155"> est fourni avec l'exemple de code ControlledTermination.cs, dans l'exemple de l'adaptateur de base (Base Adapter), qui illustre le mécanisme de synchronisation décrit ici.</span><span class="sxs-lookup"><span data-stu-id="af0f7-155"> ships with sample code ControlledTermination.cs in the Base Adapter sample, showing the synchronization mechanism described here.</span></span>