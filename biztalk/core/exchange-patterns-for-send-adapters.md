---
title: "Modèles d’échange pour les adaptateurs d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ad65fb5-640d-4bd2-aabe-946210f58a22
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 997aaa9a92f90f30bdaaeb59cc9cecb0c454496f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exchange-patterns-for-send-adapters"></a><span data-ttu-id="66415-102">Remplacement des modèles pour les adaptateurs d'envoi</span><span class="sxs-lookup"><span data-stu-id="66415-102">Exchange Patterns for Send Adapters</span></span>
<span data-ttu-id="66415-103">Les adaptateurs d'envoi sont des messages remis du moteur de messagerie BizTalk à transmettre sur le câble.</span><span class="sxs-lookup"><span data-stu-id="66415-103">Send adapters are delivered messages from the BizTalk Messaging Engine to be transmitted over the wire.</span></span> <span data-ttu-id="66415-104">Ces messages peuvent être envoyés via un modèle d'échange de message unidirectionnel ou bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="66415-104">These messages may be sent by using a one-way or two-way message exchange pattern.</span></span> <span data-ttu-id="66415-105">Un adaptateur qui traite ce modèle d'échange de message bidirectionnel est nommé adaptateur de sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="66415-105">An adapter that handles this two-way message exchange pattern is called a Solicit-Response adapter.</span></span>  
  
## <a name="blocking-vs-non-blocking-transmissions"></a><span data-ttu-id="66415-106">Blocage de Visual Studio. Transmissions non bloquantes</span><span class="sxs-lookup"><span data-stu-id="66415-106">Blocking vs. Non-Blocking Transmissions</span></span>  
 <span data-ttu-id="66415-107">Le moteur de messagerie remet les messages à l’adaptateur d’envoi à l’aide du **IBTTransmitter.TransmitMessage** méthode ou la **IBTTransmitterBatch.TransmitMessage** (méthode), selon que l’adaptateur prend en charge de traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="66415-107">The Messaging Engine delivers messages to the send adapter by using either the **IBTTransmitter.TransmitMessage** method or the **IBTTransmitterBatch.TransmitMessage** method, depending on whether the adapter is batch-aware.</span></span> <span data-ttu-id="66415-108">Les deux versions de la méthode comportent une valeur de retour booléenne qui indique comment l'adaptateur a transmis le message.</span><span class="sxs-lookup"><span data-stu-id="66415-108">Both versions of the method have a Boolean return value that indicates how the adapter transmitted the message.</span></span> <span data-ttu-id="66415-109">Si l'adaptateur retourne `true`, il a complètement envoyé le message avant de renvoyer.</span><span class="sxs-lookup"><span data-stu-id="66415-109">If the adapter returns `true`, it has completely sent the message before returning.</span></span> <span data-ttu-id="66415-110">Dans ce cas, le moteur de messagerie supprime le message de la base de données MessageBox pour l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="66415-110">In this case the Messaging Engine deletes the message from the MessageBox database on behalf of the adapter.</span></span> <span data-ttu-id="66415-111">Si l'adaptateur renvoie `false`, il a commencé à transmettre le message et a renvoyé avant la fin de la transmission.</span><span class="sxs-lookup"><span data-stu-id="66415-111">If the adapter returns `false`, it started message transmission and returned before the transmission completed.</span></span> <span data-ttu-id="66415-112">Dans ce cas, l'adaptateur est responsable non seulement de la suppression du message de la file d'attente de son application mais aussi du traitement des erreurs de transmission qui nécessitent que le message soit extrait pour être transmis ou suspendu.</span><span class="sxs-lookup"><span data-stu-id="66415-112">In this case, the adapter is responsible not only for deleting the message from its application queue but also for handling transmission failures that require the message to be retried for transmission or suspended.</span></span>  
  
 <span data-ttu-id="66415-113">L’adaptateur retournant `false` est un appel non bloquant, ce qui signifie que la **TransmitMessage** code d’implémentation ne bloque pas le thread appelant du moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="66415-113">The adapter returning `false` is a nonblocking call, meaning that the **TransmitMessage** implementation code does not block the calling thread of the Messaging Engine.</span></span> <span data-ttu-id="66415-114">L'adaptateur ajoute simplement le message à une file d'attente en mémoire prête à être transmise puis renvoie.</span><span class="sxs-lookup"><span data-stu-id="66415-114">The adapter simply adds the message to an in-memory queue ready to be transmitted and then returns.</span></span> <span data-ttu-id="66415-115">L'adaptateur doit normalement disposer de sa propre réserve de threads qui traite la file d'attente en mémoire, transmet le message, puis informe le moteur du résultat de la transmission.</span><span class="sxs-lookup"><span data-stu-id="66415-115">The adapter should have its own thread pool that services the in-memory queue, transmits the message, and then notifies the engine of the outcome of the transmission.</span></span>  
  
 <span data-ttu-id="66415-116">Les threads du moteur de messagerie sont généralement plus liés au processeur que ceux utilisés pour envoyer des données sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="66415-116">The Messaging Engine’s threads are typically more CPU bound than the threads used to send data over the wire.</span></span> <span data-ttu-id="66415-117">L'utilisation combinée ces deux types de threads affecte les performances.</span><span class="sxs-lookup"><span data-stu-id="66415-117">Mixing these two types of threads has a negative impact on performance.</span></span> <span data-ttu-id="66415-118">Les envois non bloquants permettent de découpler ces deux types de threads et améliorent sensiblement les performances par rapport aux appels bloquants.</span><span class="sxs-lookup"><span data-stu-id="66415-118">Non-blocking sends enable the decoupling of these two types of threads and yield a significant performance improvement over blocking calls.</span></span>  
  
 <span data-ttu-id="66415-119">Le diagramme suivant présente la réserve de threads de l'adaptateur qui peuvent avoir tendance à être liés par les opérations d'E/S.</span><span class="sxs-lookup"><span data-stu-id="66415-119">The following diagram shows the adapter's thread pool which can tend to be bound by I/O operations.</span></span> <span data-ttu-id="66415-120">La réserve de threads du moteur de messagerie BizTalk Server est davantage liée au traitement effectué par le processeur.</span><span class="sxs-lookup"><span data-stu-id="66415-120">The BizTalk Server Messaging Engine's thread pool is more bound by the CPU processing.</span></span> <span data-ttu-id="66415-121">En conservant deux réserves de threads différentes et en ne combinant pas le même type de thread, le système opère plus efficacement.</span><span class="sxs-lookup"><span data-stu-id="66415-121">By keeping two different thread pools and not mixing the same type of threads the system can operate more efficiently.</span></span>  
  
 ![](../core/media/io-cpu-bound-threadpools.gif "Io_cpu_bound_threadpools")  
  
 <span data-ttu-id="66415-122">**Conseil de performances :** pour des performances optimales, adaptateurs d’envoi sont non bloquant et reconnaissent les lots.</span><span class="sxs-lookup"><span data-stu-id="66415-122">**Performance Tip:** For the best performance, send adapters should be nonblocking and batch aware.</span></span> <span data-ttu-id="66415-123">Lorsque l'adaptateur BizTalk File est passé de bloquant et ne reconnaissant pas les lots à non bloquant et reconnaissant les lots, les performances ont été multipliées par trois.</span><span class="sxs-lookup"><span data-stu-id="66415-123">When the BizTalk File adapter was changed from blocking and non-batch aware to nonblocking and batch aware, a threefold performance gain was realized.</span></span>  
  
 <span data-ttu-id="66415-124">**Conseil de dépannage :** transmet de blocage peut entraîner une dégradation des performances d’une instance de l’intégralité de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="66415-124">**Troubleshooting Tip:** Blocking transmits can cause a performance degradation of an entire host instance.</span></span> <span data-ttu-id="66415-125">Si l’adaptateur effectue un blocage excessif **TransmitMessage** cela empêchera les threads du moteur de remettre des messages à d’autres cartes.</span><span class="sxs-lookup"><span data-stu-id="66415-125">If the adapter does excessive blocking in **TransmitMessage** it will prevent engine threads from delivering messages to other adapters.</span></span>  
  
## <a name="non-batched-sends"></a><span data-ttu-id="66415-126">Envois hors lots</span><span class="sxs-lookup"><span data-stu-id="66415-126">Non-Batched Sends</span></span>  
 <span data-ttu-id="66415-127">Les adaptateurs qui ne sont pas reconnaissent les lots doivent implémenter **IBTTransmitter** comme détaillé dans [Interfaces pour un adaptateur d’envoi asynchrone](../core/interfaces-for-an-asynchronous-send-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="66415-127">Adapters that are not batch aware should implement **IBTTransmitter** as detailed in [Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md).</span></span> <span data-ttu-id="66415-128">Pour chaque message que l’adaptateur doit transmettre le moteur de messagerie appelle **IBTTransmitter.TransmitMessage**.</span><span class="sxs-lookup"><span data-stu-id="66415-128">For each message that the adapter needs to transmit the Messaging Engine calls **IBTTransmitter.TransmitMessage**.</span></span> <span data-ttu-id="66415-129">Le diagramme d'interaction d'objets ci-dessous décrit la méthode standard de transmission des messages, qui comporte les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="66415-129">The object interaction diagram below details the typical approach for transmitting messages, which consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="66415-130">Le moteur remet le message à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="66415-130">The engine delivers the message to the adapter.</span></span>  
  
2.  <span data-ttu-id="66415-131">L'adaptateur place le message dans une file d'attente en mémoire prête à être transmise.</span><span class="sxs-lookup"><span data-stu-id="66415-131">The adapter enqueues the message to an in-memory queue ready to be transmitted.</span></span>  
  
3.  <span data-ttu-id="66415-132">Un thread de la réserve de threads de l'adaptateur extrait le message de la file d'attente, lit la configuration du message, puis transmet le message sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="66415-132">A thread from the adapter's thread pool dequeues the message from the queue, reads the configuration for the message, and transmits the message over the wire.</span></span>  
  
4.  <span data-ttu-id="66415-133">L'adaptateur reçoit un nouveau lot du moteur.</span><span class="sxs-lookup"><span data-stu-id="66415-133">The adapter gets a new batch from the engine.</span></span>  
  
5.  <span data-ttu-id="66415-134">L’adaptateur appelle la méthode **DeleteMessage** sur le lot, en passant le message qu’il vient de transmettre.</span><span class="sxs-lookup"><span data-stu-id="66415-134">The adapter calls **DeleteMessage** on the batch, passing in the message that it has just transmitted.</span></span>  
  
6.  <span data-ttu-id="66415-135">L’adaptateur appelle la méthode **fait** sur le lot.</span><span class="sxs-lookup"><span data-stu-id="66415-135">The adapter calls **Done** on the batch.</span></span>  
  
7.  <span data-ttu-id="66415-136">Le moteur traite le lot et supprime le message de la file d'attente de l'application.</span><span class="sxs-lookup"><span data-stu-id="66415-136">The engine processes the batch and deletes the message from the application queue.</span></span>  
  
8.  <span data-ttu-id="66415-137">Le moteur rappelle l’adaptateur pour l’informer du résultat de la **DeleteMessage** opération.</span><span class="sxs-lookup"><span data-stu-id="66415-137">The engine calls back the adapter to notify it of the outcome of the **DeleteMessage** operation.</span></span>  
  
 ![](../core/media/deleting-from-message-queue.gif "Deleting_from_message_queue")  
  
 <span data-ttu-id="66415-138">Le diagramme d'interaction d'objets précédent présente l'adaptateur supprimant un seul message de la file d'attente de l'application.</span><span class="sxs-lookup"><span data-stu-id="66415-138">The preceding object interaction diagram shows the adapter deleting a single message from the application queue.</span></span> <span data-ttu-id="66415-139">L'idéal est que l'adaptateur regroupe les opérations de message plutôt que d'opérer sur un seul message à la fois.</span><span class="sxs-lookup"><span data-stu-id="66415-139">Ideally the adapter batches up message operations as opposed to operating on a single message at a time.</span></span>  
  
## <a name="batched-sends"></a><span data-ttu-id="66415-140">Envois par lots</span><span class="sxs-lookup"><span data-stu-id="66415-140">Batched Sends</span></span>  
 <span data-ttu-id="66415-141">Adaptateurs qui reconnaissent les lots doivent implémenter **IBTBatchTransmitter** et **IBTTransmitterBatch** comme détaillé dans [Interfaces pour les adaptateurs d’envoi](../core/interfaces-for-send-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="66415-141">Adapters that are batch aware should implement **IBTBatchTransmitter** and **IBTTransmitterBatch** as detailed in [Interfaces for Send Adapters](../core/interfaces-for-send-adapters.md).</span></span> <span data-ttu-id="66415-142">Lorsque le moteur dispose de l’adaptateur transmettre les messages, le moteur reçoit un nouveau lot de l’adaptateur en appelant **IBTBatchTransmitter.GetBatch**.</span><span class="sxs-lookup"><span data-stu-id="66415-142">When the engine has messages for the adapter to transmit, the engine gets a new batch from the adapter by calling **IBTBatchTransmitter.GetBatch**.</span></span> <span data-ttu-id="66415-143">L’adaptateur retourne un nouvel objet de lot qui implémente **IBTTransmitterBatch**.</span><span class="sxs-lookup"><span data-stu-id="66415-143">The adapter returns a new batch object that implements **IBTTransmitterBatch**.</span></span> <span data-ttu-id="66415-144">Le moteur commence alors le lot en appelant **IBTTransmitterBatch.BeginBatch**.</span><span class="sxs-lookup"><span data-stu-id="66415-144">The engine then starts the batch by calling **IBTTransmitterBatch.BeginBatch**.</span></span> <span data-ttu-id="66415-145">Cette API dispose d'un paramètre Out qui permet à l'adaptateur de spécifier le nombre maximal de messages qu'il accepte dans le lot.</span><span class="sxs-lookup"><span data-stu-id="66415-145">This API has an out parameter that allows the adapter to specify the maximum number of messages that it will accept on the batch.</span></span> <span data-ttu-id="66415-146">Le cas échéant, l'adaptateur peut retourner une transaction DTC.</span><span class="sxs-lookup"><span data-stu-id="66415-146">The adapter may optionally return a DTC transaction.</span></span> <span data-ttu-id="66415-147">Le moteur appelle **IBTTransmitterBatch.TransmitMessage** une fois pour chaque message sortant à ajouter au lot.</span><span class="sxs-lookup"><span data-stu-id="66415-147">The engine then calls **IBTTransmitterBatch.TransmitMessage** once for each outgoing message to be added to the batch.</span></span> <span data-ttu-id="66415-148">Le nombre d'appels est supérieur à zéro mais inférieur ou égal à la taille maximale du lot indiquée par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="66415-148">The number of times this is called is greater than zero but less than or equal to the maximum size of the batch as indicated by the adapter.</span></span> <span data-ttu-id="66415-149">Lorsque tous les messages ont été ajoutés au lot, l’adaptateur appelle **IBTTransmitterBatch.Done**.</span><span class="sxs-lookup"><span data-stu-id="66415-149">When all the messages have been added to the batch, the adapter calls **IBTTransmitterBatch.Done**.</span></span> <span data-ttu-id="66415-150">À ce stade, l'adaptateur place généralement tous les messages du lot dans sa file d'attente en mémoire.</span><span class="sxs-lookup"><span data-stu-id="66415-150">At this point the adapter typically enqueues all the messages in the batch to its in-memory queue.</span></span> <span data-ttu-id="66415-151">L'adaptateur transmet les messages d'un ou plusieurs threads de sa propre réserve de threads comme dans le cas des adaptateurs ne reconnaissant pas les lots.</span><span class="sxs-lookup"><span data-stu-id="66415-151">The adapter transmits the messages from a thread or threads in its own thread pool as in the case of non-batch-aware adapters.</span></span> <span data-ttu-id="66415-152">Il informe ensuite le moteur du résultat de la transmission.</span><span class="sxs-lookup"><span data-stu-id="66415-152">The adapter then notifies the engine of the outcome of the transmission.</span></span>  
  
 <span data-ttu-id="66415-153">Le diagramme d'interaction d'objets suivant présente la transmission de deux messages par un adaptateur d'envois par lots.</span><span class="sxs-lookup"><span data-stu-id="66415-153">The following object interaction diagram illustrates the transmission of two messages by a batched send adapter.</span></span>  
  
 ![](../core/media/batchedsends.gif "BatchedSends")  
  
## <a name="handling-transmission-failures"></a><span data-ttu-id="66415-154">Gestion des erreurs de transmission</span><span class="sxs-lookup"><span data-stu-id="66415-154">Handling Transmission Failures</span></span>  
 <span data-ttu-id="66415-155">La sémantique recommandée pour les erreurs de transmission est présentée dans la figure ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="66415-155">The recommended semantics for transmission failures are illustrated in the figure below.</span></span> <span data-ttu-id="66415-156">Il ne s'agit que de recommandations non appliquées par le moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="66415-156">These are only recommendations and are not enforced by the Messaging Engine.</span></span> <span data-ttu-id="66415-157">Si besoin, vous pouvez développer un adaptateur ne suivant pas ces directives, mais dans ce cas procédez avec précaution.</span><span class="sxs-lookup"><span data-stu-id="66415-157">You can develop an adapter that deviates from these guidelines if there are valid reasons for doing so but you should be careful in this case.</span></span> <span data-ttu-id="66415-158">Par exemple, en règle générale, un adaptateur doit toujours déplacer les messages vers le transport secondaire une fois le nombre maximal de tentatives atteint.</span><span class="sxs-lookup"><span data-stu-id="66415-158">For example, in general an adapter should always move messages to the backup transport after all retries have been exhausted.</span></span>  
  
 <span data-ttu-id="66415-159">Plus généralement, un transport peut avoir besoin d'utiliser plus de tentatives que le nombre de tentatives défini.</span><span class="sxs-lookup"><span data-stu-id="66415-159">More commonly a transport may need to use more retries than are configured.</span></span> <span data-ttu-id="66415-160">Bien qu'il s'agisse d'un cas légèrement différent, ceci est acceptable car la couche de transport s'en trouve alors plus tolérante.</span><span class="sxs-lookup"><span data-stu-id="66415-160">While this is slightly different it is considered acceptable because the resilience of the transport layer is being increased.</span></span> <span data-ttu-id="66415-161">En général, les API exposées par le moteur de messagerie sont conçues pour permettre à l'adaptateur un contrôle maximal lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="66415-161">In general the APIs exposed by the Messaging Engine are designed to give the adapter maximum control where possible.</span></span> <span data-ttu-id="66415-162">Ce contrôle s'accompagne d'un niveau de responsabilité plus élevé.</span><span class="sxs-lookup"><span data-stu-id="66415-162">With this control comes a greater level of responsibility.</span></span>  
  
 ![](../core/media/handlingerrors.gif "HandlingErrors")  
  
 <span data-ttu-id="66415-163">L’adaptateur détermine le nombre de nouvelles tentatives disponibles sur un message en activant la propriété de contexte système **RetryCount**.</span><span class="sxs-lookup"><span data-stu-id="66415-163">The adapter determines the number of retries available on a message by checking the system context property **RetryCount**.</span></span> <span data-ttu-id="66415-164">L’adaptateur appelle la **renvoyer** API qu’une seule fois pour chaque nouvelle tentative tentative et transmet le message à renvoyer.</span><span class="sxs-lookup"><span data-stu-id="66415-164">The adapter calls the **Resubmit** API once for each retry attempt and passes in the message to be resubmitted.</span></span> <span data-ttu-id="66415-165">Il transmet également l'horodatage indiquant quand le moteur doit remettre à nouveau le message à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="66415-165">Along with the message it passes the time stamp indicating when the engine should deliver the message back to the adapter.</span></span> <span data-ttu-id="66415-166">Cette valeur doit être généralement l’heure actuelle plus la valeur de **RetryInterval**.</span><span class="sxs-lookup"><span data-stu-id="66415-166">This value should typically be the current time plus the value of **RetryInterval**.</span></span> <span data-ttu-id="66415-167">**RetryInterval** est une propriété de contexte système dont les unités sont les minutes.</span><span class="sxs-lookup"><span data-stu-id="66415-167">**RetryInterval** is a system context property whose units are minutes.</span></span> <span data-ttu-id="66415-168">Les deux le **RetryCount** et **RetryInterval** dans le contexte du message sont les valeurs qui sont configurés sur le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="66415-168">Both the **RetryCount** and **RetryInterval** in the message context are the values that are configured on the send port.</span></span> <span data-ttu-id="66415-169">Considérez un déploiement évolutif avec les instances du même hôte BizTalk déployées sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="66415-169">Consider a scaled-out deployment with instances of the same BizTalk Host deployed on multiple computers.</span></span> <span data-ttu-id="66415-170">Si le message est remis une fois l'intervalle de nouvelle tentative expiré, il peut être remis à n'importe laquelle des instances de l'hôte sur n'importe quel ordinateur où ces instances sont configurées pour s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="66415-170">If the message is delivered after the retry interval has expired, the message may be delivered to the any one of the host instances on any of the computers where they are configured to run.</span></span> <span data-ttu-id="66415-171">Pour cette raison, l'adaptateur ne doit conserver aucun état associé à un message à utiliser avec la nouvelle tentative car rien ne garantit que la même instance de l'adaptateur sera responsable de la transmission par la suite.</span><span class="sxs-lookup"><span data-stu-id="66415-171">For this reason the adapter should not hold any state associated with a message to be used on the retry attempt because there is no guarantee that same instance of the adapter will be responsible for the transmission at a later time.</span></span>  
  
 <span data-ttu-id="66415-172">L'adaptateur doit uniquement tenter de déplacer le message vers le transport secondaire une fois le nombre de tentatives inférieur ou égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="66415-172">The adapter should only attempt to move the message to the backup transport after the retry count is less than or equal to zero.</span></span> <span data-ttu-id="66415-173">Une tentative de déplacement du message vers le transport secondaire échoue si aucun transport secondaire n'est configuré pour le port.</span><span class="sxs-lookup"><span data-stu-id="66415-173">An attempt to move the message to the backup transport will fail if there is no backup transport configured for the port.</span></span> <span data-ttu-id="66415-174">Dans ce cas, le message doit être suspendu.</span><span class="sxs-lookup"><span data-stu-id="66415-174">In this case the message should be suspended.</span></span>  
  
 <span data-ttu-id="66415-175">Le fragment de code suivant indique comment déterminer le nombre de tentatives et l'intervalle à partir du contexte du message, ainsi que le nouvel envoi ou le déplacement suivant vers le transport secondaire.</span><span class="sxs-lookup"><span data-stu-id="66415-175">The following code fragment illustrates how to determine the retry count and interval from the message context, and the subsequent resubmit or move to the backup transport.</span></span>  
  
```  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
 …  
// RetryCount and RetyInterval are system context properties...  
private static readonly PropertyBase RetryCountProperty =   
 new BTS.RetryCount();  
private static readonly PropertyBase RetryIntervalProperty =   
 new BTS.RetryInterval();  
  
public void HandleRetry(IBaseMessage msg, IBTTransportBatch batch)  
{  
int retryCount = 0;  
int retryInterval = 0;  
  
// Get the RetryCount and RetryInterval off the msg ctx...  
 GetMessageRetryState(msg, out retryCount, out retryInterval);  
  
// If we have retries available resubmit, else move to   
 // backup transport...  
 if ( retryCount > 0 )  
batch.Resubmit(  
 msg, DateTime.Now.AddMinutes(retryInterval));  
else  
batch.MoveToNextTransport(msg);  
}  
  
public void GetMessageRetryState(  
 IBaseMessage msg,   
 out int retryCount,   
 out int retryInterval )  
{  
retryCount = 0;  
retryInterval = 0;  
  
object obj =  msg.Context.Read(  
RetryCountProperty.Name.Name,    
RetryCountProperty.Name.Namespace);   
  
if ( null != obj )  
retryCount = (int)obj;  
  
obj =  msg.Context.Read(  
RetryIntervalProperty.Name.Name,    
RetryIntervalProperty.Name.Namespace);   
  
if ( null != obj )  
retryInterval = (int)obj;  
}  
```  
  
## <a name="throwing-an-exception-from-transmitmessage"></a><span data-ttu-id="66415-176">Génération d'une exception à partir de TransmitMessage</span><span class="sxs-lookup"><span data-stu-id="66415-176">Throwing an Exception from TransmitMessage</span></span>  
 <span data-ttu-id="66415-177">Si l’adaptateur lève une exception sur chacune des API **IBTTransmitter.TransmitMessage**, **IBTTransmitterBatch.TransmitMessage**, **IBTTransmitterBatch.Done**, moteur traite la transmission des messages impliqués en tant qu’erreurs de transmission et prend les mesures appropriées pour le message, comme détaillé dans [comment gérer les défaillances d’adaptateur](../core/how-to-handle-adapter-failures.md).</span><span class="sxs-lookup"><span data-stu-id="66415-177">If the adapter throws an exception on any of the APIs **IBTTransmitter.TransmitMessage**, **IBTTransmitterBatch.TransmitMessage**, **IBTTransmitterBatch.Done**, the engine treats the transmission of the messages involved as transmission failures and takes the appropriate action for the message, as detailed in [How to Handle Adapter Failures](../core/how-to-handle-adapter-failures.md).</span></span>  
  
 <span data-ttu-id="66415-178">Pour les adaptateurs d'envoi reconnaissant les lots, la génération d'une exception sur l'API TransmitMessage a pour résultat d'effacer le lot entier et d'effectuer les opérations d'échec de transmission par défaut pour tous les messages de ce lot.</span><span class="sxs-lookup"><span data-stu-id="66415-178">For batch-aware send adapters, throwing an exception on the TransmitMessage API results in the entire batch being cleared and the default transmit failure actions being performed for all messages in that batch.</span></span>  
  
## <a name="solicit-response"></a><span data-ttu-id="66415-179">Sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="66415-179">Solicit-Response</span></span>  
 <span data-ttu-id="66415-180">Les adaptateurs d'envoi bidirectionnels prennent généralement en charge les transmissions unidirectionnelles et bidirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="66415-180">Two-way send adapters typically support both one-way and two-way transmissions.</span></span> <span data-ttu-id="66415-181">L’adaptateur d’envoi détermine si le message doit être transmis en tant qu’un envoi unidirectionnel ou bidirectionnel en examinant le **IsSolicitResponse** propriété de contexte système dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="66415-181">The send adapter determines whether the message should be transmitted as a one-way or two-way send by inspecting the **IsSolicitResponse** system context property in the message context.</span></span>  
  
 <span data-ttu-id="66415-182">Le fragment de code suivant illustre ceci :</span><span class="sxs-lookup"><span data-stu-id="66415-182">The following code fragment demonstrates this:</span></span>  
  
```  
private bool portIsTwoWay = false;  
private static readonly PropertyBase IsSolicitResponseProperty= new BTS.IsSolicitResponse();  
  
...  
  
 // Port is one way or two way...  
 object obj =  this.message.Context.Read(  
 IsSolicitResponseProperty.Name.Name,    
 IsSolicitResponseProperty.Name.Namespace);   
  
if ( null != obj )  
 this.portIsTwoWay = (bool)obj;  
```  
  
 <span data-ttu-id="66415-183">Pendant une transmission de type sollicitation-réponse, l'adaptateur transmet le message de sollicitation.</span><span class="sxs-lookup"><span data-stu-id="66415-183">During a solicit-response transmission the adapter transmits the solicit message.</span></span> <span data-ttu-id="66415-184">Une fois cette opération effectuée, il envoie la réponse associée et indique au moteur de messagerie de supprimer le message de sollicitation d'origine de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="66415-184">After this completed it submits the associated response and tells the Messaging Engine to delete the original solicit message from the MessageBox database.</span></span> <span data-ttu-id="66415-185">La suppression du message de la file d'attente de l'application doit être effectuée dans le même lot de proxy de transport que l'envoi du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="66415-185">The action of deleting the message from the application queue should be performed in the same transport proxy batch as the submission of the response message.</span></span> <span data-ttu-id="66415-186">Ceci assure l'atomicité de la suppression et de l'envoi de la réponse.</span><span class="sxs-lookup"><span data-stu-id="66415-186">This ensures atomicity of the deletion and submission of the response.</span></span> <span data-ttu-id="66415-187">Pour que l'atomicité soit totale, l'adaptateur doit utiliser une transaction DTC par laquelle la transmission du message de sollicitation vers une ressource reconnaissant les transactions, l'envoi du message de réponse et la suppression du message de sollicitation figurent toutes dans le contexte de la même transaction DTC.</span><span class="sxs-lookup"><span data-stu-id="66415-187">For complete atomicity the adapter should use a DTC transaction whereby the transmission of the solicit message to a transaction-aware resource, submission of the response message, and deletion of the solicit message are all in the context of the same DTC transaction.</span></span> <span data-ttu-id="66415-188">Comme toujours, nous recommandons que le message de sollicitation soit transmis via un envoi non bloquant.</span><span class="sxs-lookup"><span data-stu-id="66415-188">As always, we recommend that the solicit message is transmitted using a non-blocking send.</span></span>  
  
 <span data-ttu-id="66415-189">Le fragment de code suivant illustre les aspects principaux d'un envoi bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="66415-189">The following code fragment illustrates the main aspects of a two-way send.</span></span> <span data-ttu-id="66415-190">Lorsque le moteur appelle **IBTTransmitter.TransmitMessage** l’adaptateur place le message à transmettre à une file d’attente en mémoire.</span><span class="sxs-lookup"><span data-stu-id="66415-190">When the engine calls **IBTTransmitter.TransmitMessage** the adapter enqueues the message to be transmitted to an in-memory queue.</span></span> <span data-ttu-id="66415-191">L'adaptateur retourne `false` pour indiquer qu'il effectue un envoi non bloquant.</span><span class="sxs-lookup"><span data-stu-id="66415-191">The adapter returns `false` to indicate that it is performing a non-blocking send.</span></span> <span data-ttu-id="66415-192">Pool de threads de l’adaptateur (**WorkerThreadThunk**) traite la file d’attente en mémoire et enlève un message à transmettre à une méthode d’assistance.</span><span class="sxs-lookup"><span data-stu-id="66415-192">The adapter's thread pool (**WorkerThreadThunk**) services the in-memory queue and dequeues a message to hand it off to a helper method.</span></span> <span data-ttu-id="66415-193">Cette méthode est responsable de l'envoi du message de sollicitation et de la réception du message de réponse.</span><span class="sxs-lookup"><span data-stu-id="66415-193">This method is responsible for sending the solicit message and receiving the response message.</span></span> <span data-ttu-id="66415-194">(L'implémentation de cette méthode d'assistance dépasse le cadre de cette rubrique.) Le message de réponse est envoyé au moteur et le message de sollicitation supprimé de la file d'attente de l'application.</span><span class="sxs-lookup"><span data-stu-id="66415-194">(The implementation of this helper method is outside the scope of this topic.) The response message is submitted into the engine, and the solicit message is deleted from the application queue.</span></span>  
  
```  
using System.Collections;  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
  
     static private Queue _transmitQueue = new Queue();  
  static private IBTTransportProxy _transportProxy = null;   
// IBTTransmitter...  
 public bool TransmitMessage(IBaseMessage msg)  
{  
// Add message to the transmit queue...  
lock(_transmitQueue.SyncRoot)  
 {  
_transmitQueue.Enqueue(msg);  
 }  
  
 return false;  
}  
  
 // Threadpool worker thread...   
private void WorkerThreadThunk()  
{  
try  
{  
 IBaseMessage solicitMsg = null;  
  
 lock(_transmitQueue.SyncRoot)  
 {  
 solicitMsg =   
 (IBaseMessage)_transmitQueue.Dequeue();  
}  
  
 IBaseMessage responseMsg = SendSolicitResponse(   
 solicitMsg );  
Callback cb = new Callback();  
  
IBTTransportBatch batch = _transportProxy.GetBatch(  
 cb, null);  
batch.SubmitResponseMessage( solicitMsg, responseMsg );  
batch.DeleteMessage( solicitMsg );  
batch.Done(null);  
}  
catch(Exception)  
{  
// Handle failure....  
}  
}  
  
static private IBaseMessage SendSolicitResponse(  
 IBaseMessage solicitMsg )  
{  
// Helper method to send solicit message and receive   
 // response message...  
IBaseMessage responseMsg = null;  
return responseMsg;  
}  
```  
  
## <a name="dynamic-sends"></a><span data-ttu-id="66415-195">Envois dynamiques</span><span class="sxs-lookup"><span data-stu-id="66415-195">Dynamic Sends</span></span>  
 <span data-ttu-id="66415-196">Les ports d'envoi dynamique ne sont pas associés à une configuration d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="66415-196">Dynamic send ports do not have adapter configuration associated with them.</span></span> <span data-ttu-id="66415-197">Ils utilisent à la place la configuration du gestionnaire pour les propriétés par défaut nécessaires à l'adaptateur pour transmettre les messages sur un port dynamique.</span><span class="sxs-lookup"><span data-stu-id="66415-197">Instead they use handler configuration for any default properties that the adapter needs to transmit messages on a dynamic port.</span></span> <span data-ttu-id="66415-198">Par exemple, un adaptateur HTTP peut avoir besoin d'utiliser un proxy et de fournir des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="66415-198">For example, an HTTP adapter may need to use a proxy and need to provide credentials.</span></span> <span data-ttu-id="66415-199">Le nom d'utilisateur, le mot de passe et le port peuvent être spécifiés dans la configuration du gestionnaire, que l'adaptateur met en cache lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="66415-199">The user name, password, and port could be specified in the handler configuration that the adapter caches at run time.</span></span>  
  
 <span data-ttu-id="66415-200">Le moteur de déterminer le protocole de transport un message dynamique à être envoyés sur, la **OutboundTransportLocation** est préfixé avec un alias de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="66415-200">For the engine to determine the transport that a dynamic message is to be sent over, the **OutboundTransportLocation** is prefixed with the adapter's alias.</span></span> <span data-ttu-id="66415-201">Un adaptateur peut inscrire un ou plusieurs alias avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors de l'installation.</span><span class="sxs-lookup"><span data-stu-id="66415-201">An adapter can register one or more aliases with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] at install time.</span></span> <span data-ttu-id="66415-202">Le moteur analyse la **OutboundTransportLocation** au moment de l’exécution pour rechercher une correspondance.</span><span class="sxs-lookup"><span data-stu-id="66415-202">The engine parses the **OutboundTransportLocation** at run time to find a match.</span></span> <span data-ttu-id="66415-203">L’adaptateur est responsable du traitement du **OutboundTransportLocation** avec ou sans l’alias à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="66415-203">The adapter is responsible for handling the **OutboundTransportLocation** with or without the alias prepended to it.</span></span> <span data-ttu-id="66415-204">La table suivante affiche quelques exemples d'alias inscrits pour des adaptateurs BizTalk prêts à l'emploi.</span><span class="sxs-lookup"><span data-stu-id="66415-204">The following table shows some examples of aliases registered for out-of-the-box BizTalk adapters.</span></span>  
  
|<span data-ttu-id="66415-205">Alias d'adaptateur</span><span class="sxs-lookup"><span data-stu-id="66415-205">Adapter alias</span></span>|<span data-ttu-id="66415-206">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="66415-206">Adapter</span></span>|<span data-ttu-id="66415-207">Exemple de OutboundTransportLocation</span><span class="sxs-lookup"><span data-stu-id="66415-207">OutboundTransportLocation example</span></span>|  
|-------------------|-------------|---------------------------------------|  
|<span data-ttu-id="66415-208">HTTP://</span><span class="sxs-lookup"><span data-stu-id="66415-208">HTTP://</span></span>|<span data-ttu-id="66415-209">HTTP</span><span class="sxs-lookup"><span data-stu-id="66415-209">HTTP</span></span>|<span data-ttu-id="66415-210">http://www.</span><span class="sxs-lookup"><span data-stu-id="66415-210">http://www.</span></span> <span data-ttu-id="66415-211">MaSociété.com/bar</span><span class="sxs-lookup"><span data-stu-id="66415-211">MyCompany.com/bar</span></span>|  
|<span data-ttu-id="66415-212">HTTPS://</span><span class="sxs-lookup"><span data-stu-id="66415-212">HTTPS://</span></span>|<span data-ttu-id="66415-213">HTTP</span><span class="sxs-lookup"><span data-stu-id="66415-213">HTTP</span></span>|<span data-ttu-id="66415-214">https://www.</span><span class="sxs-lookup"><span data-stu-id="66415-214">https://www.</span></span> <span data-ttu-id="66415-215">MaSociété.com/bar</span><span class="sxs-lookup"><span data-stu-id="66415-215">MyCompany.com/bar</span></span>|  
|<span data-ttu-id="66415-216">mailto:</span><span class="sxs-lookup"><span data-stu-id="66415-216">mailto:</span></span>|<span data-ttu-id="66415-217">SMTP</span><span class="sxs-lookup"><span data-stu-id="66415-217">SMTP</span></span>|mailto:A.User@MyCompany.com|  
|<span data-ttu-id="66415-218">FILE://</span><span class="sxs-lookup"><span data-stu-id="66415-218">FILE://</span></span>|<span data-ttu-id="66415-219">FILE</span><span class="sxs-lookup"><span data-stu-id="66415-219">FILE</span></span>|<span data-ttu-id="66415-220">FILE://C:\ MyCompany \\%MessageID%.xml</span><span class="sxs-lookup"><span data-stu-id="66415-220">FILE://C:\ MyCompany \\%MessageID%.xml</span></span>|