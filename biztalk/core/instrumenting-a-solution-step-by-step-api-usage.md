---
title: "Instrumentation d’une Solution : utilisation de l’API détaillées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9e027ab-1927-4905-8970-8061ac55d591
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73c59ab28c228c779fd9e6e84d836b87415d6386
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instrumenting-a-solution-step-by-step-api-usage"></a><span data-ttu-id="8941f-102">Instrumentation d’une Solution : utilisation de l’API pas à pas</span><span class="sxs-lookup"><span data-stu-id="8941f-102">Instrumenting a Solution: Step-by-Step API Usage</span></span>
<span data-ttu-id="8941f-103">Cette rubrique décrit la procédure d'instrumentation d'une application à l'aide de la classe clé de l'API BAM.</span><span class="sxs-lookup"><span data-stu-id="8941f-103">This topic describes how to instrument an application using the key BAM API class.</span></span> <span data-ttu-id="8941f-104">Dans les extraits suivants, nous avons simplifié l'exemple de code, en utilisant des constantes, ainsi que le code minimal nécessaire pour instrumenter une application.</span><span class="sxs-lookup"><span data-stu-id="8941f-104">In the following code snippets we have simplified the sample code by using constants and by using the minimum code necessary to instrument an application.</span></span>  
  
 <span data-ttu-id="8941f-105">L'extrait de code suivant montre comment créer un objet [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) , en particulier [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).</span><span class="sxs-lookup"><span data-stu-id="8941f-105">The following code snippet demonstrates how you create a new [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) object, specifically a [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).</span></span> <span data-ttu-id="8941f-106">Dans cet extrait, le premier paramètre spécifie la chaîne de connexion vers la banque de données de la base de données d'importation principale BAM. Le deuxième paramètre indique la fréquence à laquelle les événements sont inscrits dans la banque de données.</span><span class="sxs-lookup"><span data-stu-id="8941f-106">In this snippet, the first parameter specifies the connection string to the data store of the BAM Primary Import database and the second parameter specifies the frequency with which the events are written to the data store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8941f-107">BAM prend en charge les connexions vers les banques de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] uniquement.</span><span class="sxs-lookup"><span data-stu-id="8941f-107">BAM supports connections only to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] data stores.</span></span> <span data-ttu-id="8941f-108">L'exemple de chaîne de connexion représente la chaîne minimale requise pour établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="8941f-108">The sample connection string represents the minimal connection string required to establish a connection.</span></span> <span data-ttu-id="8941f-109">Votre configuration nécessitera peut-être la spécification d'autres paramètres dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="8941f-109">Your configuration may require additional parameters to be specified in the connection string.</span></span>  
  
 <span data-ttu-id="8941f-110">Une valeur *FlushThreshold* de 0 indique que les événements ne sont pas automatiquement inscrits et que vous devez appeler la méthode Flush pour les inscrire.</span><span class="sxs-lookup"><span data-stu-id="8941f-110">A *FlushThreshold* value of 0 specifies that events are not automatically written and that you must call the Flush method to write the events.</span></span> <span data-ttu-id="8941f-111">La valeur un entraîne l'inscription de tous les événements au moment où ils surviennent.</span><span class="sxs-lookup"><span data-stu-id="8941f-111">A value of one causes each event to be written when it occurs.</span></span> <span data-ttu-id="8941f-112">Les valeurs supérieures à un indiquent que les événements sont inscrits lorsqu'un lot a atteint le nombre d'événements défini pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="8941f-112">Values of greater than one specify that events are written when a batch of the specified accumulation has occurred.</span></span> <span data-ttu-id="8941f-113">L'utilisation d'une valeur supérieure à un peut permettre d'améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="8941f-113">Using a value of greater than one can be useful to enhance performance.</span></span>  
  
```  
// Specify the DES connection string.  
const string connBAMPIT =  
   "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
// Write the activity update data on every call.  
int flushThreshold = 1;  
// Create a DES instance  
EventStream es =   
   new DirectEventStream(connBAMPIT, flushThreshold);  
```  
  
 <span data-ttu-id="8941f-114">Une fois l'objet [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) créé, vous pouvez commencer l'activité et mettre à jour la table d'activité avec les données et étapes majeures collectées.</span><span class="sxs-lookup"><span data-stu-id="8941f-114">Once the [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) object has been created, you can begin the activity and start updating the activity table with the collected milestones and data.</span></span> <span data-ttu-id="8941f-115">Lorsque l'activité BAM a été déployée, cinq tables ont été créées dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="8941f-115">When the BAM activity was deployed, five tables were created in the BAM Primary Import database.</span></span> <span data-ttu-id="8941f-116">Pour plus d’informations sur le processus de développement, consultez [vue d’ensemble du processus de développement BAM](../core/overview-of-the-bam-development-process.md).</span><span class="sxs-lookup"><span data-stu-id="8941f-116">For more information about the development process, see [Overview of the BAM Development Process](../core/overview-of-the-bam-development-process.md).</span></span>  
  
 <span data-ttu-id="8941f-117">L'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) permet d'ajouter un enregistrement à la table bam_ PurchaseOrder_Activity.</span><span class="sxs-lookup"><span data-stu-id="8941f-117">Calling the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method adds a record to the bam_ PurchaseOrder_Activity table.</span></span> <span data-ttu-id="8941f-118">Le premier paramètre contient le nom de l'activité mise à jour, tandis que le deuxième contient un identificateur pour cette instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8941f-118">The first parameter contains the name of the activity being updated and the second parameter contains an identifier for this instance of the activity.</span></span> <span data-ttu-id="8941f-119">L'identificateur peut être une chaîne, mais il doit être unique dans le jeu d'enregistrements de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8941f-119">The identifier can be any string, but it must be unique in the record set for the activity.</span></span>  
  
 <span data-ttu-id="8941f-120">À ce stade, l'enregistrement ne contient pas de données.</span><span class="sxs-lookup"><span data-stu-id="8941f-120">At this point the record does not contain any data.</span></span> <span data-ttu-id="8941f-121">La méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) met à jour l'enregistrement à l'aide des données d'événement capturées.</span><span class="sxs-lookup"><span data-stu-id="8941f-121">The [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method updates the record with the captured event data.</span></span> <span data-ttu-id="8941f-122">À nouveau, vous spécifiez une activité et l'identificateur d'instance de cette activité.</span><span class="sxs-lookup"><span data-stu-id="8941f-122">Once again you specify an activity and the activity instance identifier.</span></span> <span data-ttu-id="8941f-123">Vous transmettez les paires nom-valeur de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) des éléments de données et étapes majeures que vous avez définis dans l'activité.</span><span class="sxs-lookup"><span data-stu-id="8941f-123">You pass the [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method name value pairs of data items and milestones you defined in the activity.</span></span> <span data-ttu-id="8941f-124">Par exemple, notre activité a défini une étape majeure MS_Received.</span><span class="sxs-lookup"><span data-stu-id="8941f-124">For example, our activity defined a milestone MS_Received.</span></span> <span data-ttu-id="8941f-125">Lorsque l'activité a été déployée, une colonne de la table bam_ PurchaseOrder_Activity a été créée pour l'étape majeure.</span><span class="sxs-lookup"><span data-stu-id="8941f-125">When the activity was deployed, a column in the bam_ PurchaseOrder_Activity table was created for the milestone.</span></span> <span data-ttu-id="8941f-126">L'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) spécifie la paire nom-valeur de MS_Received et DateTime.UtcNow pour la mise à jour de l'activité avec la date de réception du bon de commande.</span><span class="sxs-lookup"><span data-stu-id="8941f-126">The call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method specifies the name value pair of MS_Received and DateTime.UtcNow to update the activity with received date for the purchase order.</span></span>  
  
```  
// When a purchase order is received, you call the  
// BeginActivity method in the receive application.  
// You can then capture the event data by calling   
// the UpdateActivity method.  
es.BeginActivity ("PurchaseOrder", "PO123");  
es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
```  
  
 <span data-ttu-id="8941f-127">Dans cet exemple, nous continuons vers une deuxième activité.</span><span class="sxs-lookup"><span data-stu-id="8941f-127">In this sample we continue to a second activity.</span></span> <span data-ttu-id="8941f-128">Pour plus d’informations sur les continuations, consultez [Continuation d’activités](../core/activity-continuation.md).</span><span class="sxs-lookup"><span data-stu-id="8941f-128">For more information about continuations, see [Activity Continuation](../core/activity-continuation.md).</span></span>  
  
 <span data-ttu-id="8941f-129">Pour permettre à d'autres applications instrumentées de mettre à jour l'activité PurchaseOrder, vous incluez un appel à la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8941f-129">To enable other instrumented applications to update the PurchaseOrder activity, you include a call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method.</span></span> <span data-ttu-id="8941f-130">L'appel spécifie l'activité à laquelle les autres applications peuvent contribuer, l'identificateur de l'instance de l'activité faisant l'objet du suivi, ainsi que le jeton de continuation que les autres applications utilisent pour mettre l'activité à jour.</span><span class="sxs-lookup"><span data-stu-id="8941f-130">The call specifies the activity to which other applications can contribute, the identifier for the instance of the activity being tracked, and the continuation token that other applications will use to update the activity.</span></span> <span data-ttu-id="8941f-131">Un enregistrement est inscrit dans la table bam_ PurchaseOrder_continuations pour effectuer le suivi de l'état de la continuation.</span><span class="sxs-lookup"><span data-stu-id="8941f-131">A record is written to the bam_ PurchaseOrder_continuations table to track the status of the continuation.</span></span> <span data-ttu-id="8941f-132">Si l'activité continue sur d'autres processus, un enregistrement est inscrit pour chaque appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) avec un jeton de continuation.</span><span class="sxs-lookup"><span data-stu-id="8941f-132">If the activity continues to other processes, a record is written for each call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method with a unique continuation token.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8941f-133">Tous les segments de code d'un scénario de continuation doivent avoir leur propre appel de méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8941f-133">Every code segment in a continuation scenario must have its own [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method call.</span></span> <span data-ttu-id="8941f-134">Autrement, l'enregistrement de l'activité sera en suspens/orphelin.</span><span class="sxs-lookup"><span data-stu-id="8941f-134">Failing to do so will result in a dangling/orphaned activity record.</span></span>  
>   
>  <span data-ttu-id="8941f-135">Cependant, seul le premier segment (qui utilise l'ID d'activité réel) possède la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) . Les autres segments (qui utilisent leur propre ID de jeton unique) ne doivent pas appeler la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8941f-135">However, only the first segment (that uses the actual activity ID) has the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method; all the other segments (that use their own unique token ID) must not call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method.</span></span>  
  
 <span data-ttu-id="8941f-136">Après l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) , les autres composants peuvent mettre à jour l'activité de bon de commande à l'aide de [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) en spécifiant le jeton de continuation au lieu de l'ID d'activité.</span><span class="sxs-lookup"><span data-stu-id="8941f-136">After the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method is called, other components can update the purchase order activity using [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) specifying the continuation token instead of the activity ID.</span></span> <span data-ttu-id="8941f-137">Une fois leurs tâches achevées, les autres composants doivent appeler [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) avec le jeton de continuation pour informer l'infrastructure BAM qu'aucun autre événement n'est prévu.</span><span class="sxs-lookup"><span data-stu-id="8941f-137">When the other components have completed their tasks, each of the components must call [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) with the continuation token to inform the BAM infrastructure that no more events are expected.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8941f-138">Une fois la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) appelée, une activité peut devenir orpheline si le processus dans lequel cette activité est continuée n'appelle jamais la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) avec le jeton de continuation.</span><span class="sxs-lookup"><span data-stu-id="8941f-138">Once the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method is called, it is possible for an activity to become orphaned if the process in which the activity is continued never calls an [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method with the continuation token.</span></span>  
  
```  
// Continue the activity to the next process that has been  
// instrumented to handle the continuation.  
es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
```  
  
 <span data-ttu-id="8941f-139">Pour finir, l'activité est finalisée par l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) spécifiant le nom et l'identificateur de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8941f-139">Finally, the activity is finalized by calling the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method specifying the activity name and the activity identifier.</span></span> <span data-ttu-id="8941f-140">Si toutes les continuations sont terminées, l'activité est déplacée dans la table bam_ PurchaseOrder _completed.</span><span class="sxs-lookup"><span data-stu-id="8941f-140">If there are no unfinished continuations, the activity is moved to the bam_ PurchaseOrder _completed table.</span></span> <span data-ttu-id="8941f-141">Les activités peuvent devenir orphelines si les activités de continuation ne se terminent pas.</span><span class="sxs-lookup"><span data-stu-id="8941f-141">It is possible for activities to become orphaned if continuation activities fail to complete.</span></span>  
  
```  
// Activity from this segment (PO submission) is completed  
es.EndActivity("PurchaseOrder", “PO123”);  
```  
  
 <span data-ttu-id="8941f-142">Quand l'activité continue dans un processus distinct, l'application est instrumentée pour mettre à jour la table d'activité avec l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) , en spécifiant le nom de l'activité et le jeton de continuation déclarés dans l'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8941f-142">When the activity continues to separate process, the application is instrumented to update the activity table by calling [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) specifying the activity name and the continuation token declared in the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8941f-143">Le processus gérant l'activité continuée n'appelle pas la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8941f-143">The process handling the continued activity does not call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method.</span></span> <span data-ttu-id="8941f-144">La méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) crée une instance de l'activité en créant les tables de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="8941f-144">The [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method creates an instance of the activity by creating the tables in the BAM Primary Import database.</span></span> <span data-ttu-id="8941f-145">Le processus dans lequel l'activité est continuée met à jour l'instance de l'activité déjà existante.</span><span class="sxs-lookup"><span data-stu-id="8941f-145">The process to which the activity is continued is updating the instance of the already existing activity.</span></span>  
  
```  
// update when the order is approved  
es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                    DateTime.UtcNow, "T_Product", "Widget");  
  
// update when the product is ready for shipment  
es.UpdateActivity ("PurchaseOrder", “AP123”,  
                   "MS_Ready", DateTime.UtcNow);  
```  
  
 <span data-ttu-id="8941f-146">Dans le cadre du workflow de cet exemple, le code indique une référence, dans ce cas, un type précis de référence, à savoir une activité associée.</span><span class="sxs-lookup"><span data-stu-id="8941f-146">Part of the workflow for this sample the code specifies a reference, in this case a specific type of reference - a related activity.</span></span> <span data-ttu-id="8941f-147">En spécifiant une activité associée, vous créez un lien entre l'activité principale et les autres activités susceptibles d'intéresser l'utilisateur visualisant l'activité dans le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="8941f-147">By specifying a related activity you create a link from your primary activity to other activities that are of interest to a user viewing the activity in the BAM portal.</span></span>  
  
 <span data-ttu-id="8941f-148">L'appel de la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.AddRelatedActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.addrelatedactivity.aspx) entraîne l'écriture d'un enregistrement dans la table bam_ PurchaseOrder_ActiveRelationships liant les activités.</span><span class="sxs-lookup"><span data-stu-id="8941f-148">The call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.AddRelatedActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.addrelatedactivity.aspx) method writes a record to the bam_ PurchaseOrder_ActiveRelationships linking the activities.</span></span>  
  
```  
// These are shipped in two shipments.  
// Relates the current purchase order   
// instance to two shippings.  
// Note: only one direction  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS101”);  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS102”);  
```  
  
 <span data-ttu-id="8941f-149">Pour mettre fin à l'activité continuée, vous appelez la méthode [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) en spécifiant le jeton de la continuation qui s'achève.</span><span class="sxs-lookup"><span data-stu-id="8941f-149">To end the continued activity you call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method specifying the continuation token for the continuation that is ending.</span></span> <span data-ttu-id="8941f-150">Si toutes les continuations sont terminées, l'activité du bon de commande est déplacée dans la table terminée.</span><span class="sxs-lookup"><span data-stu-id="8941f-150">If there are no other unfinished continuations, the purchase order activity is moved to the completed table.</span></span>  
  
```  
// Activity from this segment (ApprovalProcess) is completed  
es.EndActivity("PurchaseOrder", “AP123”);  
```  
  
## <a name="complete-code-sample"></a><span data-ttu-id="8941f-151">Exemple de code complet</span><span class="sxs-lookup"><span data-stu-id="8941f-151">Complete Code Sample</span></span>  
  
```  
//---------------------------------------------------------------------  
// File:BAMMinimalSample.cs  
//   
// Summary: Demonstrates how to instrument an application   
//using BAM APIs to track useful information.  
//  
// Sample: BAM Api Sample  
//  
//---------------------------------------------------------------------  
// This file is part of the Microsoft BizTalk Server SDK  
//  
// Copyright (c) Microsoft Corporation. All rights reserved.  
//  
// This source code is intended only as a supplement to Microsoft   
// BizTalk Server release and/or on-line documentation. See   
// these other materials for detailed information regarding Microsoft // code samples.  
//  
// THIS CODE AND INFORMATION ARE PROVIDED "AS IS" WITHOUT WARRANTY OF  
// ANY KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO // THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A   
// PARTICULAR PURPOSE.  
//---------------------------------------------------------------------  
// This sample requires that you add the     
// Microsoft.BizTalk.Bam.EventObservation.dll to the   
// references in the Visual Studio Solution.  
  
using System;  
using System.Text;  
using Microsoft.BizTalk.Bam.EventObservation;  
  
namespace EventStreamSample  
{  
  
    static void Main(string[] args)  
    {  
        //   
  // The following code would appear in a purchase order  
   // receipt application.  
        //  
  
        // Specify the DES connection string.  
        const string connBAMPIT =  
            "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
  
        // Write the activity update data on every call.  
        int flushThreshold = 1;  
  
        // Create an instance of the DirectEventStream.  
        EventStream es =   
               new DirectEventStream(connBAMPIT, flushThreshold);  
  
        // When a purchase order is received, you call the  
       // BeginActivity method in the receive application.  
  // You can then capture the event data by calling   
        // the UpdateActivity method.  
        es.BeginActivity ("PurchaseOrder", "PO123");  
        es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
  
   // Continue the activity to the next process that has been  
   // instrumented to handle the continuation.  
        es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
  
        // Activity from this segment (PO submission) is completed  
        // end activity is synonymous to IsCompleted = 1  
        es.EndActivity("PurchaseOrder", “PO123”);  
  
        //  
        // The following code would typically appear in a separate   
        // application that monitors the approval process  
        // (ApprovalProcess.exe)  
        //  
  
        // update when the order is approved  
        es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                            DateTime.UtcNow, "T_Product", "Widget");  
  
        // update when the product is ready for shipment  
        es.UpdateActivity ("PurchaseOrder", “AP123”,  
                            "MS_Ready", DateTime.UtcNow);  
  
        // These are shipped in two shipments.  
        // Relates the current purchase order  
        // instance to two shippings.  
        // Note: only one direction  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS101”);  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS102”);  
  
        // Activity from this segment (ApprovalProcess) is completed  
        es.EndActivity("PurchaseOrder", “AP123”);  
  
        // In another Shipping application, two shipments with  
            ID’s UPS101 and UPS102 will be created.  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8941f-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8941f-152">See Also</span></span>  
 [<span data-ttu-id="8941f-153">Implémentation d’activités BAM avec les flux d’événements</span><span class="sxs-lookup"><span data-stu-id="8941f-153">Implementing BAM Activities with Event Streams</span></span>](../core/implementing-bam-activities-with-event-streams.md)