---
title: "Optimisation des performances de l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 437c7325-f037-451a-8dbd-f8d8c8889e20
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cbd45901afb229cf884390c2a5120deac0daa90d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-orchestration-performance"></a><span data-ttu-id="d6b72-102">Optimisation des performances de l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-102">Optimizing Orchestration Performance</span></span>
<span data-ttu-id="d6b72-103">Cette rubrique décrit les meilleures pratiques pour l’utilisation d’orchestrations dans les solutions BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d6b72-103">This topic describes best practices for using orchestrations in BizTalk Server solutions.</span></span> <span data-ttu-id="d6b72-104">Cela inclut des recommandations pour :</span><span class="sxs-lookup"><span data-stu-id="d6b72-104">This includes recommendations for:</span></span>  
  
-   <span data-ttu-id="d6b72-105">Ce qui réduit la latence des solutions BizTalk Server qui utilisent des orchestrations</span><span class="sxs-lookup"><span data-stu-id="d6b72-105">Reducing latency of BizTalk Server solutions that use orchestrations</span></span>  
  
    -   <span data-ttu-id="d6b72-106">Élimination des orchestrations pour seulement les modèles de messagerie</span><span class="sxs-lookup"><span data-stu-id="d6b72-106">Eliminating orchestrations for messaging only patterns</span></span>  
  
    -   <span data-ttu-id="d6b72-107">Utilisant inline envoie des orchestrations</span><span class="sxs-lookup"><span data-stu-id="d6b72-107">Utilizing inline sends from orchestrations</span></span>  
  
    -   <span data-ttu-id="d6b72-108">Réduction des points de persistance d’orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-108">Minimizing orchestration persistence points</span></span>  
  
-   <span data-ttu-id="d6b72-109">Imbrication des orchestrations</span><span class="sxs-lookup"><span data-stu-id="d6b72-109">Nesting orchestrations</span></span>  
  
-   <span data-ttu-id="d6b72-110">Modèles de conception d’orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-110">Orchestration design patterns</span></span>  
  
-   <span data-ttu-id="d6b72-111">Blocs de gestion des exceptions d’orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-111">Orchestration exception handling blocks</span></span>  
  
## <a name="recommendations-for-optimizing-orchestrations-for-low-latency-scenarios"></a><span data-ttu-id="d6b72-112">Recommandations pour l’optimisation des orchestrations pour des scénarios à faible latence</span><span class="sxs-lookup"><span data-stu-id="d6b72-112">Recommendations for optimizing orchestrations for low latency scenarios</span></span>  
 <span data-ttu-id="d6b72-113">Les techniques suivantes peuvent être utilisées pour réduire la latence des solutions BizTalk Server qui utilisent des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d6b72-113">The following techniques can be used to reduce latency of BizTalk Server solutions that use orchestrations.</span></span>  
  
### <a name="eliminate-orchestrations-for-messaging-only-patterns"></a><span data-ttu-id="d6b72-114">Éliminer les orchestrations pour seulement les modèles de messagerie</span><span class="sxs-lookup"><span data-stu-id="d6b72-114">Eliminate orchestrations for messaging only patterns</span></span>  
 <span data-ttu-id="d6b72-115">Lorsqu’il est possible de réduire l’utilisation des orchestrations pour augmenter le débit global et de réduire la latence des processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="d6b72-115">When possible minimize the use of orchestrations to increase overall throughput and reduce the latency of business processes.</span></span> <span data-ttu-id="d6b72-116">S’il est inutile d’exécuter longue en cours d’exécution des transactions et il n’est pas nécessaire pour appeler plusieurs systèmes pour chaque demande, puis prendre en compte en éliminant les orchestrations et le déplacement de logique métier pour les Ports d’envoi et réception afin de réduire la quantité totale d’allers-retours vers la BizTalkMsgBoxDb et diminuer la latence en raison de l’accès de la base de données.</span><span class="sxs-lookup"><span data-stu-id="d6b72-116">If there is no need to run long running transactions and there is no need to invoke several systems for each request, then consider eliminating orchestrations and moving business logic to Receive and Send Ports to reduce the total amount of roundtrips to the BizTalkMsgBoxDb and decrease the latency due to database access.</span></span> <span data-ttu-id="d6b72-117">Dans ce cas, implémentez les pipelines personnalisés et réutiliser les classes d’assistance qui ont été précédemment appelés à partir d’orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d6b72-117">In this case, implement custom pipelines and reuse helper classes that were previously invoked from orchestrations.</span></span> <span data-ttu-id="d6b72-118">Utilisation des orchestrations uniquement lorsque strictement nécessaire pour implémenter des modèles de conception, à nuages de points et de collecter ou de convois.</span><span class="sxs-lookup"><span data-stu-id="d6b72-118">Use orchestrations only when strictly needed to implement design patterns as Scatter and Gather or Convoys.</span></span> <span data-ttu-id="d6b72-119">Pour plus d’informations sur les modèles de conception d’Orchestration, consultez la rubrique [implémentation des modèles de conception dans les Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.microsoft.com/fwlink/?LinkId=140042) dans la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d6b72-119">For more information about Orchestration Design Patterns, see the topic [Implementing Design Patterns in Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.microsoft.com/fwlink/?LinkId=140042) in the BizTalk Server documentation.</span></span>  
  
### <a name="use-inline-sends-from-orchestrations-to-accommodate-low-latency-scenarios"></a><span data-ttu-id="d6b72-120">Utilisez inline envoie à partir d’orchestrations pour prendre en charge les scénarios de faible latence</span><span class="sxs-lookup"><span data-stu-id="d6b72-120">Use inline sends from orchestrations to accommodate low latency scenarios</span></span>  
 <span data-ttu-id="d6b72-121">Chaque fois que possible, réduisez l’utilisation des orchestrations et favoriser des modèles de messagerie seule pour augmenter le débit global et de réduire la latence des processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="d6b72-121">Whenever possible, minimize the use of orchestrations and favor messaging-only patterns to increase the overall throughput and reduce the latency of the business processes.</span></span> <span data-ttu-id="d6b72-122">Si n’est pas nécessaire pour les transactions à long terme, et il est inutile de logique métier appeler plusieurs systèmes, envisagez de déplacer la logique métier pour les Ports d’envoi et de réception et en supprimant l’utilisation des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d6b72-122">If there is no need for long-running transactions and there is no need for business logic to invoke several systems, then consider moving business logic to receive and send Ports and eliminating the use of orchestrations.</span></span> <span data-ttu-id="d6b72-123">Cette approche peut être implémentée avec les pipelines personnalisés et qui réutiliser les classes d’assistance qui ont été précédemment appelés à partir d’orchestrations.</span><span class="sxs-lookup"><span data-stu-id="d6b72-123">This approach can be implemented with custom pipelines and which reuse the helper classes that were previously invoked from orchestrations.</span></span> <span data-ttu-id="d6b72-124">Afin d’obtenir de meilleures performances dans les scénarios de faible latence, adoptez une des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6b72-124">In order to achieve better performance in low latency scenarios, adopt one of the following approaches:</span></span>  
  
-   <span data-ttu-id="d6b72-125">Éliminer les orchestrations inutiles et adoptent les modèles de messagerie seule afin de réduire la quantité totale d’allers-retours à la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d6b72-125">Eliminate unnecessary orchestrations and adopt messaging-only patterns to reduce the total amount of roundtrips to the BizTalk MessageBox database.</span></span> <span data-ttu-id="d6b72-126">Cette approche permet à faible latence, car inline envoie contourner l’associé et moteur de messagerie BizTalk surcharge.</span><span class="sxs-lookup"><span data-stu-id="d6b72-126">This approach accommodates low latency because inline sends bypass the BizTalk messaging engine and the associated overhead.</span></span> <span data-ttu-id="d6b72-127">Fonctionnalité d’envoi orchestration inline est fournie avec BizTalk Server 2006 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d6b72-127">Orchestration inline send functionality is provided with BizTalk Server 2006 and later.</span></span>  
  
-   <span data-ttu-id="d6b72-128">Les orchestrations à l’intérieur, éliminer les ports logiques aux ports physiques et l’utilisation en ligne envoie à leur place.</span><span class="sxs-lookup"><span data-stu-id="d6b72-128">Inside orchestrations, eliminate logical ports bound to physical ports and use in-line sends in their place.</span></span> <span data-ttu-id="d6b72-129">Par exemple, un envoi inline utilisable pour créer une instance d’une classe de proxy WCF pour appeler un service Web en aval ou un composant d’ADO.NET pour accéder à une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d6b72-129">For example, an inline send could be used to create an instance of a  WCF proxy class to invoke a downstream Web service or an ADO.NET component to access a SQL Server database.</span></span> <span data-ttu-id="d6b72-130">Dans le diagramme suivant, un envoi inline est effectué lorsque l’orchestration instancie un composant métier, qui utilise en interne d’un service WCF objet proxy pour appeler directement un service Web en aval :</span><span class="sxs-lookup"><span data-stu-id="d6b72-130">In the following diagram, an inline send is performed when the orchestration instantiates a business component, which internally makes use of a WCF  proxy object to directly invoke a downstream Web service:</span></span>  
  
     <span data-ttu-id="d6b72-131">![Description de l’envoi Inline de l’Orchestration BizTalk](../technical-guides/media/inlinesend.gif "InlineSend")</span><span class="sxs-lookup"><span data-stu-id="d6b72-131">![Depiction of BizTalk Orchestration Inline Send](../technical-guides/media/inlinesend.gif "InlineSend")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6b72-132">Bien qu’à l’aide d’envoie inline à partir d’orchestrations réduit considérablement le temps de latence, il existe des limitations de cette approche.</span><span class="sxs-lookup"><span data-stu-id="d6b72-132">Although using inline sends from orchestrations will significantly reduce latency, there are limitations to this approach.</span></span> <span data-ttu-id="d6b72-133">Étant donné qu’inline envoie contourner le moteur de messagerie BizTalk, les fonctionnalités suivantes fournies avec le moteur de messagerie ne sont pas disponible :</span><span class="sxs-lookup"><span data-stu-id="d6b72-133">Because inline sends bypass the BizTalk messaging engine, the following functionality provided with the messaging engine is not available:</span></span>  
>   
>  -   <span data-ttu-id="d6b72-134">Pipelines transactionnels</span><span class="sxs-lookup"><span data-stu-id="d6b72-134">Transactional pipelines</span></span>  
> -   <span data-ttu-id="d6b72-135">Pipelines récupérables</span><span class="sxs-lookup"><span data-stu-id="d6b72-135">Recoverable pipelines</span></span>  
> -   <span data-ttu-id="d6b72-136">Pipelines qui appellent l’API de l’intercepteur BAM</span><span class="sxs-lookup"><span data-stu-id="d6b72-136">Pipelines that call the BAM interceptor API</span></span>  
> -   <span data-ttu-id="d6b72-137">Prise en charge de l’adaptateur de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d6b72-137">BizTalk Server adapter support</span></span>  
> -   <span data-ttu-id="d6b72-138">Traitement par lot</span><span class="sxs-lookup"><span data-stu-id="d6b72-138">Batching</span></span>  
> -   <span data-ttu-id="d6b72-139">Tentatives</span><span class="sxs-lookup"><span data-stu-id="d6b72-139">Retries</span></span>  
> -   <span data-ttu-id="d6b72-140">L’initialisation du jeu de corrélations</span><span class="sxs-lookup"><span data-stu-id="d6b72-140">Correlation set initialization</span></span>  
> -   <span data-ttu-id="d6b72-141">Configuration déclarative</span><span class="sxs-lookup"><span data-stu-id="d6b72-141">Declarative configuration</span></span>  
> -   <span data-ttu-id="d6b72-142">Transports secondaires</span><span class="sxs-lookup"><span data-stu-id="d6b72-142">Secondary transports</span></span>  
> -   <span data-ttu-id="d6b72-143">Suivi</span><span class="sxs-lookup"><span data-stu-id="d6b72-143">Tracking</span></span>  
> -   <span data-ttu-id="d6b72-144">Utilisation déclarative de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="d6b72-144">Declarative use of BAM</span></span>  
  
 <span data-ttu-id="d6b72-145">Pour plus d’informations sur les types de pipelines qui ne peut pas être exécutées à partir d’une orchestration, consultez la section « Limitations » de la rubrique [comment utiliser des Expressions pour exécuter des Pipelines](http://go.microsoft.com/fwlink/?LinkId=158008) (http://go.Microsoft.com/fwlink/?) LinkId = 158008) dans la documentation de BizTalk Server 2010.</span><span class="sxs-lookup"><span data-stu-id="d6b72-145">For more information about the types of pipelines that cannot be executed from within an orchestration, see the “Restrictions” section of the topic [How to Use Expressions to Execute Pipelines](http://go.microsoft.com/fwlink/?LinkId=158008) (http://go.microsoft.com/fwlink/?LinkId=158008) in the BizTalk Server 2010 documentation.</span></span>  
  
### <a name="optimize-orchestration-latency-by-reducing-the-number-of-persistence-points-if-possible"></a><span data-ttu-id="d6b72-146">Optimiser la latence de l’orchestration en réduisant le nombre de points de persistance, si possible</span><span class="sxs-lookup"><span data-stu-id="d6b72-146">Optimize orchestration latency by reducing the number of persistence points, if possible</span></span>  
 <span data-ttu-id="d6b72-147">Une étendue de l’orchestration doit uniquement être marqué comme « transactionnel longue » si vous souhaitez utiliser des délais d’attente de compensation ou de la portée.</span><span class="sxs-lookup"><span data-stu-id="d6b72-147">An orchestration scope only needs to be marked as “long-running transactional” if you want to use compensation or scope timeouts.</span></span> <span data-ttu-id="d6b72-148">Une étendue transactionnelle longue provoque un point de persistance supplémentaire à la fin de l’étendue, afin qu’ils doivent être évités lorsque vous n’avez pas besoin d’utiliser la compensation ou les délais d’attente de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="d6b72-148">A long-running transactional scope causes an extra persistence point at the end of the scope, so they should be avoided when you don’t need to use compensation or scope timeouts.</span></span> <span data-ttu-id="d6b72-149">Une étendue atomique provoque un point de persistance à la fin de l’étendue, mais également garantit qu’aucun point de persistance ne se produira à l’intérieur de l’étendue atomique.</span><span class="sxs-lookup"><span data-stu-id="d6b72-149">An atomic scope causes a persistence point at the end of the scope, but also guarantees that no persistence points will occur inside the atomic scope.</span></span> <span data-ttu-id="d6b72-150">Cet effet d’aucune persistance à l’intérieur de l’étendue peut parfois servir à votre avantage pour les points de persistance de lot (lorsque effectuant plusieurs envoie, par exemple).</span><span class="sxs-lookup"><span data-stu-id="d6b72-150">This side-effect of no persistence inside the scope can sometimes be used to your advantage to batch persistence points (when doing multiple sends, for example).</span></span> <span data-ttu-id="d6b72-151">En général, toutefois, nous recommandons d’éviter les étendues atomiques si possible.</span><span class="sxs-lookup"><span data-stu-id="d6b72-151">In general, though, we recommend avoiding atomic scopes if possible.</span></span> <span data-ttu-id="d6b72-152">Le moteur d’orchestration enregistre dans le stockage persistant l’état global d’une instance d’orchestration en cours d’exécution à différents stades, afin que l’instance ultérieurement peut être restauré dans la mémoire et effectuée jusqu'à la fin.</span><span class="sxs-lookup"><span data-stu-id="d6b72-152">The orchestration engine saves to persistent storage the entire state of a running orchestration instance at various points, so that the instance can later be restored in memory and carried out to completion.</span></span>   
<span data-ttu-id="d6b72-153">**Le nombre de points de persistance dans une orchestration est un des principaux facteurs qui influencent la latence des messages transitant via des orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="d6b72-153">**The number of persistence points in an orchestration is one of the key factors influencing the latency of messages flowing through orchestrations**.</span></span> <span data-ttu-id="d6b72-154">Chaque fois que le moteur atteint un point de persistance, l’état interne d’une orchestration en cours d’exécution est sérialisé et enregistré dans la MessageBox et cette opération implique un coût de latence.</span><span class="sxs-lookup"><span data-stu-id="d6b72-154">Each time the engine hits a persistence point, the internal state of a running orchestration is serialized and saved to the MessageBox and this operation incurs a latency cost.</span></span> <span data-ttu-id="d6b72-155">La sérialisation de l’état interne inclut tous les messages et les variables instancié et pas encore publié dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="d6b72-155">The serialization of the internal state includes all messages and variables instantiated and not yet released in the orchestration.</span></span> <span data-ttu-id="d6b72-156">Les messages sont volumineux et les variables et les plus le nombre de ces, il sera plus longue pour rendre persistant l’état interne d’une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d6b72-156">The larger the messages and variables and the greater the number of these, the longer it will take to persist the internal state of an orchestration.</span></span> <span data-ttu-id="d6b72-157">Un nombre excessif de points de persistance peut conduire à une dégradation significative des performances.</span><span class="sxs-lookup"><span data-stu-id="d6b72-157">An excessive number of persistence points can lead to significant performance degradation.</span></span> <span data-ttu-id="d6b72-158">Pour cette raison, nous vous recommandons d’élimination des points de persistance inutiles à partir d’orchestrations en réduisant le nombre d’étendues transactionnelles et formes envoi.</span><span class="sxs-lookup"><span data-stu-id="d6b72-158">For this reason, we recommend eliminating unnecessary persistence points from orchestrations by reducing the number of transactional scopes and Send shapes.</span></span> <span data-ttu-id="d6b72-159">Cette approche permet de réduire la contention sur la MessageBox en raison de la mise en attente de l’orchestration et la réactivation, augmenter l’évolutivité globale et de réduire la latence de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="d6b72-159">This approach allows decreasing the contention on the MessageBox due to orchestration dehydration and rehydration, increasing the overall scalability, and reducing orchestration latency.</span></span>   
<span data-ttu-id="d6b72-160">Un autre recommandation est de toujours conserver l’état interne d’une orchestration aussi petite que possible.</span><span class="sxs-lookup"><span data-stu-id="d6b72-160">Another recommendation is to always keep the internal state of an orchestration as small as possible.</span></span> <span data-ttu-id="d6b72-161">Cette technique peut réduire considérablement le temps passé par le moteur XLANG sérialisation, la persistance et la restauration de l’état interne d’une orchestration en cas de point de persistance.</span><span class="sxs-lookup"><span data-stu-id="d6b72-161">This technique can significantly reduce the time spent by the XLANG Engine serializing, persisting and restoring the internal state of an orchestration in case of persistence point.</span></span> <span data-ttu-id="d6b72-162">Une façon d’effectuer cette opération consiste à créer des variables et les messages plus tard que possible et de libérer les dès que possible ; par exemple, introduisent des étendues non transactionnels à l’intérieur de vos orchestrations et déclarer des variables et des messages au sein de ces étendues internes au lieu de déclarer les au niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="d6b72-162">One way to achieve this is to create variables and messages as late as possible and release them as early as possible; for example introduce non transactional scopes inside your orchestrations and declare variables and messages within these inner scopes instead of declaring them at the top-most level.</span></span> <span data-ttu-id="d6b72-163">Pour plus d’informations sur la limitation des points de persistance d’orchestration, consultez les rubriques suivantes dans la documentation de BizTalk Server 2010 :</span><span class="sxs-lookup"><span data-stu-id="d6b72-163">For more information about minimizing orchestration persistence points, see the following topics in the BizTalk Server  2010 documentation:</span></span>  
  
-   <span data-ttu-id="d6b72-164">[Persistance et le moteur d’Orchestration](http://go.microsoft.com/fwlink/?LinkID=155292) (http://go.microsoft.com/fwlink/?LinkID=155292).</span><span class="sxs-lookup"><span data-stu-id="d6b72-164">[Persistence and the Orchestration Engine](http://go.microsoft.com/fwlink/?LinkID=155292) (http://go.microsoft.com/fwlink/?LinkID=155292).</span></span>  
  
-   <span data-ttu-id="d6b72-165">[Mise en attente de l’orchestration et la réactivation](http://go.microsoft.com/fwlink/?LinkID=155284) (http://go.microsoft.com/fwlink/?LinkID=155292).</span><span class="sxs-lookup"><span data-stu-id="d6b72-165">[Orchestration Dehydration and Rehydration](http://go.microsoft.com/fwlink/?LinkID=155284) (http://go.microsoft.com/fwlink/?LinkID=155292).</span></span>  
  
## <a name="guidelines-for-using-promoted-properties-to-access-message-tags-or-attributes-from-an-orchestration"></a><span data-ttu-id="d6b72-166">Instructions d’utilisation promues propriétés attributs ou de balises de message d’accès à partir d’une orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-166">Guidelines for using promoted properties to access message tags or attributes from an orchestration</span></span>  
 <span data-ttu-id="d6b72-167">Si vous n’avez pas besoin de promouvoir des propriétés, promouvoir uniquement les propriétés qui sont utilisées pour le routage des messages, de filtres et de corrélation du message.</span><span class="sxs-lookup"><span data-stu-id="d6b72-167">If you do need to promote properties, promote only those properties that are used for message routing, filters, and message correlation.</span></span> <span data-ttu-id="d6b72-168">La promotion de chaque propriété requiert le composant désassembleur (personnalisé de deux dimensions, XML,) pour reconnaître le type de document et récupérer des données à partir du message à l’aide de l’expression XPath de l’annotation relative contenue dans le schéma XSD qui définit le type de document.</span><span class="sxs-lookup"><span data-stu-id="d6b72-168">The promotion of each property requires the disassembler component (XML, Flat, custom) to recognize the document type and to retrieve data from the message using the XPath expression from the relative annotation contained in the XSD that defines the document type.</span></span> <span data-ttu-id="d6b72-169">En outre, chaque promotion de propriété provoque un appel distinct de la procédure stockée de bts_InsertProperty lorsque l’Agent des messages publie le message dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="d6b72-169">In addition, each property promotion causes a separate call of the bts_InsertProperty stored procedure when the Message Agent publishes the message to the MessageBox database.</span></span> <span data-ttu-id="d6b72-170">Si une orchestration doit accéder à un élément ou attribut spécifique contenu dans un document XML, utilisez une des techniques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6b72-170">If an orchestration needs to access a particular element or attribute contained by an XML document, use one of the following techniques:</span></span>  
  
-   <span data-ttu-id="d6b72-171">Réduisez le nombre de propriétés écrites et promues et supprimer ceux qui ne sont pas strictement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d6b72-171">Reduce the number of written and promoted properties and eliminate those that are not strictly necessary.</span></span>  
  
-   <span data-ttu-id="d6b72-172">Éliminer les champs distinctifs inutiles.</span><span class="sxs-lookup"><span data-stu-id="d6b72-172">Eliminate unnecessary distinguished fields.</span></span> <span data-ttu-id="d6b72-173">Les champs distinctifs sont écrits les propriétés de contexte et peuvent facilement occuper significatifs que leur nom est égal à l’expression XPath qui est utilisée pour récupérer des données.</span><span class="sxs-lookup"><span data-stu-id="d6b72-173">The distinguished fields are written context properties and they can easily occupy significant space as their name is equal to the XPath expression that is used to retrieve data.</span></span> <span data-ttu-id="d6b72-174">La propriété unique est définie sous forme d’annotations dans le schéma XSD qui définit le type de document.</span><span class="sxs-lookup"><span data-stu-id="d6b72-174">The distinguished property is defined as annotations in the XSD that defines the document type.</span></span> <span data-ttu-id="d6b72-175">Le composant désassembleur utilise la même approche adoptée pour les propriétés promues et l’expression XPath qui définit un champ unique pour le rechercher dans le document entrant.</span><span class="sxs-lookup"><span data-stu-id="d6b72-175">The disassembler component uses the same approach adopted for promoted properties and uses the XPath expression that defines a distinguished field to find it within in the incoming document.</span></span> <span data-ttu-id="d6b72-176">Ensuite, le composant désassembleur écrit une propriété dans le contexte où :</span><span class="sxs-lookup"><span data-stu-id="d6b72-176">Then, the disassembler component writes a property in the context where:</span></span>  
  
    -   <span data-ttu-id="d6b72-177">**Nom**: Expression XPath est définie dans l’annotation.</span><span class="sxs-lookup"><span data-stu-id="d6b72-177">**Name**: XPath Expression defined in the annotation.</span></span>  
  
    -   <span data-ttu-id="d6b72-178">**Valeur**: valeur de l’élément identifié par l’expression XPath dans un document entrant.</span><span class="sxs-lookup"><span data-stu-id="d6b72-178">**Value**: Value of the element identified by the XPath expression within an incoming document.</span></span>  
  
     <span data-ttu-id="d6b72-179">Les Expressions XPath peuvent être très longues, en particulier lorsque l’élément en question est très profonde du schéma de document.</span><span class="sxs-lookup"><span data-stu-id="d6b72-179">The XPath Expressions can be very long, especially when the element in question is very deep in the document schema.</span></span> <span data-ttu-id="d6b72-180">Par conséquent, plus distinguent les champs, plus la taille du contexte.</span><span class="sxs-lookup"><span data-stu-id="d6b72-180">So, the more distinguished fields, the larger the context size.</span></span> <span data-ttu-id="d6b72-181">Cela à son tour affecte les performances globales.</span><span class="sxs-lookup"><span data-stu-id="d6b72-181">This in turn adversely affects the overall performance.</span></span>  
  
-   <span data-ttu-id="d6b72-182">Utilisez la fonction intégrée XPath fournie par le runtime de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="d6b72-182">Use the XPath built-in function provided by the orchestration runtime.</span></span>  
  
-   <span data-ttu-id="d6b72-183">Si les messages sont assez petits (quelques kilo-octets) au format XML, vous pouvez désérialiser le message dans une instance de la classe .NET et travailler avec des champs et propriétés publics.</span><span class="sxs-lookup"><span data-stu-id="d6b72-183">If messages are quite small (a few kilobytes) and XML-formatted, you can de-serialize the message into a .NET class instance and work with public fields and properties.</span></span> <span data-ttu-id="d6b72-184">Si le message doit être une élaboration complexe (code personnalisé, les stratégies de moteur de règles métier, etc.) l’accès aux données en utilisant les propriétés exposées par une instance d’une classe .NET est beaucoup plus rapide à l’aide d’expressions XPath.</span><span class="sxs-lookup"><span data-stu-id="d6b72-184">If the message needs a complex elaboration (custom code, Business Rule Engine policies, etc.) accessing data using the properties exposed by an instance of a .NET class is much faster using XPath expressions.</span></span> <span data-ttu-id="d6b72-185">Lorsque la logique métier appelée par l’orchestration est terminée, l’objet d’entité peut être sérialisé dans un message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d6b72-185">When the business logic invoked by the orchestration has completed, the entity object can be serialized back into a BizTalk message.</span></span> <span data-ttu-id="d6b72-186">Vous pouvez créer des classes .NET à partir d’un schéma XML à l’aide d’un des outils suivants : l’outil XSD (.NET Framework 2.0) ou SVCUTIL (.NET Framework 3.0).</span><span class="sxs-lookup"><span data-stu-id="d6b72-186">You can create .NET classes from an XML schema using one of the following tools: XSD tool (.NET Framework 2.0) or SVCUTIL (.NET Framework 3.0).</span></span>  
  
-   <span data-ttu-id="d6b72-187">Activer un composant d’assistance à partir d’une orchestration.</span><span class="sxs-lookup"><span data-stu-id="d6b72-187">Enable a helper component from an orchestration.</span></span> <span data-ttu-id="d6b72-188">Cette technique a un avantage par rapport à l’aide des champs distinctifs.</span><span class="sxs-lookup"><span data-stu-id="d6b72-188">This technique has an advantage over using distinguished fields.</span></span> <span data-ttu-id="d6b72-189">En fait, une orchestration peut lire le XPath expression à partir d’une configuration stocker (fichier de configuration, magasin de configuration SSO, base de données personnalisée et ainsi de suite), par conséquent, lorsque vous devez modifier l’expression XPath, vous n’avez pas à modifier et redéployer un schéma, en tant que vous devez effectuer pour les propriétés promues et d champs d’istinguished.</span><span class="sxs-lookup"><span data-stu-id="d6b72-189">In fact, an orchestration may read the XPath expression from a config store (config file, SSO Config Store, custom Db, and so on) so, when you have to change the XPath expression, you do not have to change and redeploy a schema, as you should do for promoted properties and distinguished fields.</span></span> <span data-ttu-id="d6b72-190">L’exemple de code suivant fournit un exemple d’un composant d’assistance.</span><span class="sxs-lookup"><span data-stu-id="d6b72-190">The following code sample provides an example of a helper component.</span></span> <span data-ttu-id="d6b72-191">Le composant utilise la classe XPathReader fournie par le moteur d’exécution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d6b72-191">The component uses the XPathReader class that is provided by the BizTalk runtime.</span></span> <span data-ttu-id="d6b72-192">Ainsi, le code lire le flux de document jusqu'à ce que l’expression XPath est trouvée.</span><span class="sxs-lookup"><span data-stu-id="d6b72-192">This allows the code to read through the document stream until the XPath expression is found.</span></span>  
  
```  
#region Copyright  
//===  
//Microsoft Windows Server AppFabric Customer Advisory Team (CAT)   
//  
// This sample is supplemental to the technical guidance published on the community  
// blog.  
//   
// Author: Paolo Salvatori.  
//===  
// Copyright © 2010 Microsoft Corporation. All rights reserved.  
//   
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER   
// EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE IMPLIED WARRANTIES OF   
// MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. YOU BEAR THE RISK OF USING IT.  
//===  
#endregion  
#region Using Directives  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Xml;  
using System.Linq;  
using System.Text;  
using System.Globalization;  
using Microsoft.XLANGs.BaseTypes;   
using Microsoft.BizTalk.Streaming;  
using Microsoft.BizTalk.XPath;  
#endregion  
namespace Microsoft.AppFabric.CAT.Samples.DuplexMEP.Helpers  
{  
public class XPathHelper  
{  
#region Private Constants   
private const string MessageCannotBeNull = "[XPathReader] The message cannot be null.";  
#endregion  
#region Public Static Methods  
public static string GetValue(XLANGMessage message, int partIndex, string xpath)  
{  
try  
{  
if (message == null)  
{  
throw new ApplicationException(MessageCannotBeNull);  
}  
using (Stream stream = message[partIndex].RetrieveAs(typeof(Stream)) as Stream)  
{  
XmlTextReader xmlTextReader = new XmlTextReader(stream);  
XPathCollection xPathCollection = new XPathCollection();  
XPathReader xPathReader = new XPathReader(xmlTextReader, xPathCollection);  
xPathCollection.Add(xpath);  
while (xPathReader.Read())  
{  
if (xPathReader.HasAttributes)  
{  
for (int i = 0; i < xPathReader.AttributeCount; i++)  
{  
xPathReader.MoveToAttribute(i);  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.GetAttribute(i);  
}  
}  
}  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.ReadString();  
}  
}  
}  
}  
finally  
{  
message.Dispose();  
}  
return string.Empty;  
}  
#endregion  
}  
}  
```  
  
## <a name="minimize-orchestration-complexity-to-improve-performance"></a><span data-ttu-id="d6b72-193">Réduire la complexité d’orchestration pour améliorer les performances</span><span class="sxs-lookup"><span data-stu-id="d6b72-193">Minimize orchestration complexity to improve performance</span></span>  
 <span data-ttu-id="d6b72-194">La complexité des orchestrations a un impact significatif sur les performances.</span><span class="sxs-lookup"><span data-stu-id="d6b72-194">The complexity of orchestrations has a significant impact on performance.</span></span> <span data-ttu-id="d6b72-195">Avec l’accroissement de complexité de l’orchestration, les performances globales diminuent.</span><span class="sxs-lookup"><span data-stu-id="d6b72-195">As orchestration complexity increases, overall performance decreases.</span></span> <span data-ttu-id="d6b72-196">Orchestrations peuvent être utilisées dans une diversité presque infinie de scénarios, et chaque scénario peut impliquer des orchestrations de complexité variable.</span><span class="sxs-lookup"><span data-stu-id="d6b72-196">Orchestrations can be used in an almost infinite variety of scenarios, and each scenario might involve orchestrations of varying complexity.</span></span> <span data-ttu-id="d6b72-197">Évitez d’orchestrations complexes lorsque cela est possible en faveur d’une approche modulaire.</span><span class="sxs-lookup"><span data-stu-id="d6b72-197">Avoid complex orchestrations when possible in favor of a modular approach.</span></span> <span data-ttu-id="d6b72-198">En d’autres termes, fractionnez votre logique métier en plusieurs orchestrations réutilisables.</span><span class="sxs-lookup"><span data-stu-id="d6b72-198">In other words, split your business logic into multiple, reusable orchestrations.</span></span>  
  
 <span data-ttu-id="d6b72-199">Si vous n’avez pas besoin d’implémenter une orchestration complexe, définissez des messages et des variables dans des étendues internes chaque fois que possible, plutôt qu’au niveau racine.</span><span class="sxs-lookup"><span data-stu-id="d6b72-199">If you do need to implement a complex orchestration, define messages and variables into inner scopes whenever possible rather than at the root level.</span></span> <span data-ttu-id="d6b72-200">Cette technique conserve un plus faible encombrement en mémoire pour chaque orchestration, car les variables et les messages sont supprimés lorsque le flux quitte l’étendue où les variables et les messages ont été définies.</span><span class="sxs-lookup"><span data-stu-id="d6b72-200">This technique maintains a smaller footprint in memory for each orchestration because variables and messages are disposed of when the flow leaves the scope where the variables and messages were defined.</span></span> <span data-ttu-id="d6b72-201">Cette approche est particulièrement utile lorsque les orchestrations sont enregistrées dans la MessageBox à des points de persistance.</span><span class="sxs-lookup"><span data-stu-id="d6b72-201">This approach is particularly beneficial when orchestrations are saved to the MessageBox at persistence points.</span></span>  
  
## <a name="use-the-call-orchestration-shape-versus-the-start-orchestration-shape-to-improve-performance"></a><span data-ttu-id="d6b72-202">La forme appeler Orchestration par rapport à la forme Démarrer Orchestration permet d’améliorer les performances</span><span class="sxs-lookup"><span data-stu-id="d6b72-202">Use the Call Orchestration shape versus the Start Orchestration shape to improve performance</span></span>  
 <span data-ttu-id="d6b72-203">Éviter le **démarrer Orchestration** mettre en forme et utiliser le **appeler Orchestration** forme pour exécuter une orchestration imbriquée.</span><span class="sxs-lookup"><span data-stu-id="d6b72-203">Avoid the **Start Orchestration** shape and use the **Call Orchestration** shape to execute a nested orchestration.</span></span> <span data-ttu-id="d6b72-204">En fait, le **appeler Orchestration** forme peut être utilisée pour appeler de façon synchrone une orchestration qui est référencée dans un autre projet.</span><span class="sxs-lookup"><span data-stu-id="d6b72-204">In fact, The **Call Orchestration** shape can be used to synchronously call an orchestration that is referenced in another project.</span></span> <span data-ttu-id="d6b72-205">Cette approche permet la réutilisation des modèles de flux de travail courants d’orchestration pour les projets BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d6b72-205">This approach allows for reuse of common orchestration workflow patterns across BizTalk projects.</span></span> <span data-ttu-id="d6b72-206">Quand vous appelez une autre orchestration synchrone avec la **appeler Orchestration** forme, l’orchestration associée attend que l’orchestration imbriquée soit terminée avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d6b72-206">When you invoke another nested orchestration synchronously with the **Call Orchestration** shape, the enclosing orchestration waits for the nested orchestration to finish before continuing.</span></span> <span data-ttu-id="d6b72-207">L’orchestration imbriquée est exécutée sur le même thread que celui qui exécute l’orchestration d’appel.</span><span class="sxs-lookup"><span data-stu-id="d6b72-207">The nested orchestration is executed on the same thread that runs the calling orchestration.</span></span>  
  
 <span data-ttu-id="d6b72-208">Le **démarrer Orchestration** forme est similaire à la **appeler Orchestration** forme, mais dans ce cas, l’orchestration imbriquée est appelée de manière asynchrone : le flux de contrôle dans l’appel orchestration se poursuit au-delà de l’appel, sans attendre que l’orchestration appelée terminer son travail.</span><span class="sxs-lookup"><span data-stu-id="d6b72-208">The **Start Orchestration** shape is similar to the **Call Orchestration** shape, but in this case the nested orchestration is called in an asynchronous manner: the flow of control in the invoking orchestration proceeds beyond the invocation, without waiting for the invoked orchestration to finish its work.</span></span> <span data-ttu-id="d6b72-209">Pour implémenter ce découplage entre l’appelant et les orchestrations appelées, le **démarrer Orchestration** est implémentée via la publication d’un message dans la BizTalk Messagebox.</span><span class="sxs-lookup"><span data-stu-id="d6b72-209">In order to implement this decoupling between the caller and the called orchestrations, the **Start Orchestration** is implemented via publication of a message to the BizTalk Messagebox.</span></span> <span data-ttu-id="d6b72-210">Ce message est ensuite utilisé par une instance d’hôte BizTalk in-process qui exécute l’orchestration imbriquée.</span><span class="sxs-lookup"><span data-stu-id="d6b72-210">This message is then consumed by an in-process BizTalk host instance which executes the nested orchestration.</span></span> <span data-ttu-id="d6b72-211">Si possible, utilisez **appeler Orchestration**, surtout si l’orchestration d’appel doit attendre le résultat à partir de l’orchestration imbriquée afin de poursuivre le traitement.</span><span class="sxs-lookup"><span data-stu-id="d6b72-211">When possible, use **Call Orchestration**, especially if the calling orchestration needs to wait for a result from the nested orchestration in order to continue processing.</span></span>  <span data-ttu-id="d6b72-212">Pour plus d’informations sur l’utilisation de la forme appeler Orchestration, consultez les rubriques suivantes dans la documentation de BizTalk Server 2010 :</span><span class="sxs-lookup"><span data-stu-id="d6b72-212">For more information about using the Call Orchestration shape, see the following topics in the BizTalk Server 2010 documentation:</span></span>  
  
-   <span data-ttu-id="d6b72-213">[Utilisation de Ports à liaison directe dans les Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139902) (http://go.microsoft.com/fwlink/?LinkId=139902).</span><span class="sxs-lookup"><span data-stu-id="d6b72-213">[Working with Direct Bound Ports in Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139902) (http://go.microsoft.com/fwlink/?LinkId=139902).</span></span>  
  
-   <span data-ttu-id="d6b72-214">[Imbrication des Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139903) (http://go.microsoft.com/fwlink/?LinkId=139903).</span><span class="sxs-lookup"><span data-stu-id="d6b72-214">[Nesting Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139903) (http://go.microsoft.com/fwlink/?LinkId=139903).</span></span>  
  
## <a name="use-xmlreader-with-xlangmessage-versus-using-xmlreader-with-xmldocument-to-improve-orchestration-performance"></a><span data-ttu-id="d6b72-215">Utiliser XmlReader avec XLANGMessage et à l’aide de XmlReader avec un XmlDocument pour améliorer les performances de l’orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-215">Use XmlReader with XLANGMessage versus using XmlReader with XmlDocument to improve orchestration performance</span></span>  
 <span data-ttu-id="d6b72-216">Pour améliorer les performances d’orchestration pour les méthodes .NET appelé à partir d’une orchestration, utilisez XmlReader avec XLANGMessage, pas un XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="d6b72-216">To improve orchestration performance for .NET methods called from an orchestration, use XmlReader with XLANGMessage, not XmlDocument.</span></span> <span data-ttu-id="d6b72-217">L’exemple de code suivant illustre cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="d6b72-217">The following code example illustrates this functionality.</span></span>  
  
```csharp  
// As a general rule, use XmlReader with XLANGMessage, not XmlDocument.   
// This is illustrated in the parameter passed into the following code.   
// The XLANG/s compiler doesn't allow a return value of XmlReader   
// so documents must be initially constructed as XmlDocument()  
public static XmlDocument FromMsg(XLANGMessage old)  
{  
    //get at the data  
    XmlDocument ret = new XmlDocument();  
  
    try{  
        XmlReader reader = (XmlReader)old[0].RetrieveAs(typeof(XmlReader));  
        //construct new message from old  
        //read property  
        object msgid = old.GetPropertyValue(typeof(BTS.MessageID));  
    }  
    finally {  
        // Call Dispose on the XLANGMessage object   
        // because the message doesn't belong to the   
        // .NET runtime - it belongs to the Messagebox database   
        old.Dispose();  
    }  
    return ret;  
}  
```  
  
 <span data-ttu-id="d6b72-218">Est une autre méthode pour créer une classe .NET basée sur le schéma.</span><span class="sxs-lookup"><span data-stu-id="d6b72-218">Another method would be to create a .NET class based on the schema.</span></span> <span data-ttu-id="d6b72-219">Cette opération prend moins de mémoire que le chargement du document dans un **XmlDocument** objet, ainsi que de fournir un accès facile aux éléments du schéma pour les développeurs .NET.</span><span class="sxs-lookup"><span data-stu-id="d6b72-219">This takes less memory than loading the document into an **XmlDocument** object, as well as providing easy access to the schema elements for .NET developers.</span></span> <span data-ttu-id="d6b72-220">Pour générer une classe basée sur un schéma BizTalk, vous pouvez utiliser l’outil xsd.exe fourni avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6b72-220">To generate a class based on a BizTalk schema, you can use the xsd.exe tool provided with Visual Studio.</span></span> <span data-ttu-id="d6b72-221">Par exemple, en cours d’exécution **xsd.exe \<schema.xsd >/classes** par rapport à un schéma simple contenant des champs nommés ItemA, ItemB, ItemC, génère la classe suivante.</span><span class="sxs-lookup"><span data-stu-id="d6b72-221">For example, running **xsd.exe \<schema.xsd> /classes** against a simple schema containing fields named ItemA, ItemB, ItemC, will produce the following class.</span></span>  
  
```csharp  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1433  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
using System.Xml.Serialization;  
  
//   
// This source code was auto-generated by xsd, Version=2.0.50727.42.  
//  
  
/// <remarks/>  
[System.CodeDom.Compiler.GeneratedCodeAttribute("xsd", "2.0.50727.42")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://Schemas.MySchema")]  
[System.Xml.Serialization.XmlRootAttribute(Namespace="http://Schemas.MySchema", IsNullable=false)]  
public partial class MySchemaRoot {  
  
    private string itemAField;  
  
    private string itemBField;  
  
    private string itemCField;  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemA {  
        get {  
            return this.itemAField;  
        }  
        set {  
            this.itemAField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemB {  
        get {  
            return this.itemBField;  
        }  
        set {  
            this.itemBField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemC {  
        get {  
            return this.itemCField;  
        }  
        set {  
            this.itemCField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="d6b72-222">Cette classe peut ensuite être référencée dans votre assembly .NET afin d’accéder aux éléments de message et l’objet retourné peut être directement attribué à un message.</span><span class="sxs-lookup"><span data-stu-id="d6b72-222">This class can then be referenced in your .NET assembly in order to access the message elements, and the returned object can be directly assigned to a message.</span></span> <span data-ttu-id="d6b72-223">Voici un exemple d’utilisation de la classe générée ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="d6b72-223">The following is an example use of the class generated above.</span></span>  
  
```csharp  
public static Root SetValues(Microsoft.XLANGs.BaseTypes.XLANGMessage msg)  
{  
   try  
   {  
   MySchemaRoot rootObj=(MySchemaRoot)msg[0].RetrieveAs(typeof(MySchemaRoot);  
   rootObj.ItemA="value a";  
   rootObj.ItemB="value b";  
   rootObj.ItemC="value c";  
   }  
    finally {  
        msg.Dispose();  
            }  
  
   return rootObj;  
}  
```  
  
 <span data-ttu-id="d6b72-224">Cette technique vous permet d’utiliser une approche orientée objet lors du traitement des messages.</span><span class="sxs-lookup"><span data-stu-id="d6b72-224">This technique allows you to use an object-oriented approach when processing messages.</span></span> <span data-ttu-id="d6b72-225">Cette technique doit être utilisée principalement avec relativement petits messages.</span><span class="sxs-lookup"><span data-stu-id="d6b72-225">This technique should be used primarily with relatively small messages.</span></span> <span data-ttu-id="d6b72-226">Effet, même si cette technique utilise beaucoup moins de mémoire que lorsque le chargement du message dans une **XmlDocument** de l’objet, le message entier est toujours chargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d6b72-226">This is because even though this technique uses considerably less memory than when loading the message into an **XmlDocument** object, the entire message is still loaded into memory.</span></span> <span data-ttu-id="d6b72-227">Lors du traitement des messages plus volumineux, utilisez le **XmlReader** classe pour lire les messages et les **XmlWriter** classe pour écrire des messages.</span><span class="sxs-lookup"><span data-stu-id="d6b72-227">When processing larger messages, use the **XmlReader** class to read messages and the **XmlWriter** class to write messages.</span></span> <span data-ttu-id="d6b72-228">Lorsque vous utilisez **XmlReader** et **XmlWriter**, le message est contenu dans un **VirtualStream** objet.</span><span class="sxs-lookup"><span data-stu-id="d6b72-228">When using **XmlReader** and **XmlWriter**, the message is contained in a **VirtualStream** object.</span></span> <span data-ttu-id="d6b72-229">Si la taille du message dépasse la valeur spécifiée pour **seuil de messages volumineux (en octets)** qui est exposé dans la page de configuration des propriétés du groupe BizTalk, le message est écrit dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="d6b72-229">If the message size exceeds the value specified for **Large message threshold (bytes)** that is exposed on the BizTalk Group Properties configuration page, the message is written to the file system.</span></span> <span data-ttu-id="d6b72-230">Cela diminue les performances globales, mais évite les exceptions de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="d6b72-230">This decreases overall performance, but avoids out of memory exceptions.</span></span>  
  
## <a name="improve-performance-by-minimizing-the-use-of-logical-ports-bound-to-physical-ports"></a><span data-ttu-id="d6b72-231">Améliorer les performances en réduisant l’utilisation des ports logiques aux ports physiques</span><span class="sxs-lookup"><span data-stu-id="d6b72-231">Improve performance by minimizing the use of logical ports bound to physical ports</span></span>  
 <span data-ttu-id="d6b72-232">Vous pouvez augmenter les performances en réduisant l’utilisation des ports logiques aux ports physiques qui utilisent les adaptateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="d6b72-232">You can increase performance by minimizing the use of logical ports bound to physical ports that use the following adapters:</span></span>  
  
-   <span data-ttu-id="d6b72-233">SQL Server, Oracle</span><span class="sxs-lookup"><span data-stu-id="d6b72-233">SQL Server, Oracle</span></span>  
  
-   <span data-ttu-id="d6b72-234">WSE, HTTP, WCF</span><span class="sxs-lookup"><span data-stu-id="d6b72-234">WSE, HTTP, WCF</span></span>  
  
-   <span data-ttu-id="d6b72-235">MSMQ, MQSeries</span><span class="sxs-lookup"><span data-stu-id="d6b72-235">MSMQ, MQSeries</span></span>  
  
 <span data-ttu-id="d6b72-236">Dans BizTalk Server 2010, envoyer et recevoir des pipelines peuvent être appelées directement à partir d’une orchestration à l’aide de la classe XLANGPipelineManager contenue dans le Microsoft.XLANGs.Pipeline.dll.</span><span class="sxs-lookup"><span data-stu-id="d6b72-236">In BizTalk Server 2010, send and receive pipelines can be directly invoked from an orchestration using the XLANGPipelineManager class contained in the Microsoft.XLANGs.Pipeline.dll.</span></span> <span data-ttu-id="d6b72-237">Par conséquent, le traitement des pipelines peut être déplacé à partir des ports à des orchestrations ; les ports logiques dans une orchestration peuvent être remplacés par une forme Expression, ce qui permet d’appeler une instance d’une classe .NET donnée (par exemple, un composant d’accès aux données à l’aide d’ADO.NET).</span><span class="sxs-lookup"><span data-stu-id="d6b72-237">Thus, the processing of pipelines can be moved from ports to orchestrations; logical ports in an orchestration can be substituted with an Expression shape, which invokes an instance of a given .NET class (for example, a Data Access component using ADO.NET).</span></span> <span data-ttu-id="d6b72-238">Avant d’adopter cette technique, sachez que si vous n’utilisez pas de cartes et les ports physiques, vous perdez la possibilité de tirer parti de leurs fonctions, telles que le traitement par lot, nouvelles tentatives, une configuration déclarative et transports secondaires.</span><span class="sxs-lookup"><span data-stu-id="d6b72-238">Before adopting this technique, you should be aware that if you do not use adapters and physical ports, you lose the ability to leverage their functions, such as batching, retries, declarative configuration, and secondary transports.</span></span>  
  
## <a name="orchestration-design-patterns"></a><span data-ttu-id="d6b72-239">Modèles de conception d’orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-239">Orchestration Design Patterns</span></span>  
 <span data-ttu-id="d6b72-240">Le Concepteur d’Orchestration permet aux développeurs d’implémenter une large gamme de modèles d’intégration d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="d6b72-240">The Orchestration Designer allows developers to implement a wide range of enterprise integration patterns.</span></span> <span data-ttu-id="d6b72-241">Certains modèles courants incluent Aggregator, la gestion des exceptions et Compensation, service Broker de Message, à nuages de points et collecte et séquentiel et de convoi parallèle.</span><span class="sxs-lookup"><span data-stu-id="d6b72-241">Some common patterns include Aggregator, Exception Handling and Compensation, Message Broker, Scatter and Gather, and Sequential and Parallel Convoy.</span></span> <span data-ttu-id="d6b72-242">Ces modèles peuvent être utilisées pour développer des solutions d’intégration d’Application d’entreprise (IAE), Architecture orientée services (SOA) et gestion de processus d’entreprise (BPM) complexes avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d6b72-242">Those patterns can be utilized to develop complex Enterprise Application Integration (EAI), Service-Oriented Architecture (SOA), and Business Process Management (BPM) solutions with BizTalk Server.</span></span> <span data-ttu-id="d6b72-243">Pour plus d’informations sur les modèles de conception d’Orchestration, consultez la rubrique [implémentation des modèles de conception dans les Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.Microsoft.com/fwlink/?) LinkId = 140042) dans la documentation de BizTalk Server et [modèles et meilleures pratiques pour l’intégration d’entreprise](http://go.microsoft.com/fwlink/?LinkId=140043) (http://go.Microsoft.com/fwlink/?) LinkId = 140043).</span><span class="sxs-lookup"><span data-stu-id="d6b72-243">For more information about Orchestration Design Patterns, see the topic [Implementing Design Patterns in Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.microsoft.com/fwlink/?LinkId=140042) in the BizTalk Server documentation and [Patterns and Best Practices for Enterprise Integration](http://go.microsoft.com/fwlink/?LinkId=140043) (http://go.microsoft.com/fwlink/?LinkId=140043).</span></span>  
  
## <a name="make-appropriate-use-of-net-classes-in-orchestrations-to-maximize-performance"></a><span data-ttu-id="d6b72-244">Faire un usage approprié de classes .NET dans les orchestrations pour optimiser les performances</span><span class="sxs-lookup"><span data-stu-id="d6b72-244">Make appropriate use of .NET classes in orchestrations to maximize performance</span></span>  
 <span data-ttu-id="d6b72-245">En général, les classes .NET Framework utilisées à l’intérieur d’une orchestration peuvent être divisés en deux catégories distinctes :</span><span class="sxs-lookup"><span data-stu-id="d6b72-245">In general, the .NET classes used inside an orchestration can be divided into two distinct categories:</span></span>  
  
-   <span data-ttu-id="d6b72-246">**Programmes d’assistance et des services -** ces classes fournissent des services communs aux orchestrations telles que le suivi, la gestion des erreurs, la mise en cache et la sérialisation/désérialisation.</span><span class="sxs-lookup"><span data-stu-id="d6b72-246">**Helpers and services -** These classes provide common services to orchestrations such as tracing, error handling, caching, and serialization/deserialization.</span></span> <span data-ttu-id="d6b72-247">La plupart de ces classes peut être implémentée en tant que classes statiques avec aucun état interne et plusieurs méthodes statiques publiques.</span><span class="sxs-lookup"><span data-stu-id="d6b72-247">Most of these classes can be implemented as static classes with no internal state and multiple public static methods.</span></span> <span data-ttu-id="d6b72-248">Cette approche évite la création de plusieurs objets de la même classe dans les différentes orchestrations en cours d’exécution en même temps, ce qui permet de réduire l’espace de travail de processus hôte et d’économiser de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="d6b72-248">This approach avoids creating multiple objects of the same class in different orchestrations running at the same time, which helps to reduce the working space of host processes and save memory.</span></span> <span data-ttu-id="d6b72-249">Une classe qui est sans état permet de réduire la taille globale de l’état interne qui doit être sérialisé et rendues persistantes dans la BizTalk MessageBox si une orchestration est en attente.</span><span class="sxs-lookup"><span data-stu-id="d6b72-249">A class that is stateless helps to reduce the overall size of the internal state that must be serialized and persisted to the BizTalk MessageBox when an orchestration is dehydrated.</span></span>  
  
-   <span data-ttu-id="d6b72-250">**Entités et des objets métier -** vous pouvez utiliser ces classes pour gérer les entités, telles que des commandes, des éléments de commande et des clients.</span><span class="sxs-lookup"><span data-stu-id="d6b72-250">**Entities and Business Objects -** You can use these classes to manage entities, such as orders, order items, and customers.</span></span> <span data-ttu-id="d6b72-251">Une seule orchestration en interne, créez et gérer plusieurs instances du même type.</span><span class="sxs-lookup"><span data-stu-id="d6b72-251">A single orchestration can internally create and manage multiple instances of the same type.</span></span> <span data-ttu-id="d6b72-252">Ces classes sont généralement avec état et exposent les champs publics et/ou propriétés ainsi que les méthodes pour modifier l’état interne de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d6b72-252">These classes are typically stateful, and expose public fields and/or properties along with methods to modify the internal state of the object.</span></span> <span data-ttu-id="d6b72-253">Instances de ces classes peuvent être créés de façon dynamique par la désérialisation d’une partie de XLANGMessage dans un objet .NET à l’aide de la **XmlSerializer** ou **DataContractSerializer** classes ou à l’aide de la  **XLANGPart.RetrieveAs** (méthode).</span><span class="sxs-lookup"><span data-stu-id="d6b72-253">Instances of these classes can be dynamically created by deserializing an XLANGMessage part into a .NET object by using the **XmlSerializer** or the **DataContractSerializer** classes or by using the **XLANGPart.RetrieveAs** method.</span></span> <span data-ttu-id="d6b72-254">Vous devez structurer une orchestration en utilisant les étendues non transactionnel de sorte que les instances de classes avec état sont créées plus tard que possible et libérées dès qu’ils ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="d6b72-254">You should structure an orchestration using non-transactional scopes in such a way that instances of stateful classes are created as late as possible and released as soon as they are no longer needed.</span></span> <span data-ttu-id="d6b72-255">Cette approche permet de réduire l’espace de travail de processus hôte et réduit la taille globale de l’état interne qui est sérialisée et rendues persistantes dans la base de données MessageBox si une orchestration est en attente.</span><span class="sxs-lookup"><span data-stu-id="d6b72-255">This approach reduces the working space of host processes and minimizes the overall size of the internal state that is serialized and persisted to the MessageBox database when an orchestration is dehydrated.</span></span> <span data-ttu-id="d6b72-256">Pour plus d’informations sur l’utilisation d’orchestrations dans BizTalk Server, consultez l’article [FAQ pour les Orchestrations BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=116886) (http://go.microsoft.com/fwlink/?LinkID=116886).</span><span class="sxs-lookup"><span data-stu-id="d6b72-256">For more information about using orchestrations in BizTalk Server, see the article [FAQ for BizTalk Server Orchestrations](http://go.microsoft.com/fwlink/?LinkID=116886) (http://go.microsoft.com/fwlink/?LinkID=116886).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6b72-257">Alors que cet article est écrit pour BizTalk Server 2004 et BizTalk Server 2006, les concepts présentés s’appliquent également aux orchestrations de BizTalk Server 2010.</span><span class="sxs-lookup"><span data-stu-id="d6b72-257">While this article is written for BizTalk Server 2004 and BizTalk Server 2006, the concepts presented also apply to BizTalk Server 2010 orchestrations.</span></span>  
  
## <a name="orchestration-exception-handler-blocks"></a><span data-ttu-id="d6b72-258">Blocs de gestionnaire d’Exception d’orchestration</span><span class="sxs-lookup"><span data-stu-id="d6b72-258">Orchestration Exception Handler Blocks</span></span>  
 <span data-ttu-id="d6b72-259">Lorsque vous utilisez des blocs de gestionnaire d’exception d’Orchestration, incluent toutes les formes d’orchestration dans une ou plusieurs étendues (non transactionnels étendues autant que possible) et créer au moins les blocs de gestionnaire d’exception suivants :</span><span class="sxs-lookup"><span data-stu-id="d6b72-259">When using Orchestration exception Handler blocks, include all orchestration shapes in one or multiple scopes (non transactional scopes whenever possible) and create at least the following exception handler blocks:</span></span>  
  
-   <span data-ttu-id="d6b72-260">Un bloc de gestionnaire d’exceptions pour la gestion d’une erreur générique de System.Exception.</span><span class="sxs-lookup"><span data-stu-id="d6b72-260">An exception handler block for handling a generic System.Exception error.</span></span>  
  
-   <span data-ttu-id="d6b72-261">Un bloc de gestionnaire d’exceptions pour gérer une exception générale afin d’intercepter et gérer les erreurs possibles non managées, telles que les exceptions COM.</span><span class="sxs-lookup"><span data-stu-id="d6b72-261">An exception handler block for handling a general exception in order to catch and handle possible unmanaged errors, such as COM exceptions.</span></span>  
  
 <span data-ttu-id="d6b72-262">Pour plus d’informations sur l’utilisation des blocs d’exceptions d’Orchestration, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="d6b72-262">For more information about using Orchestration exception handling blocks, see the following articles:</span></span>  
  
-   <span data-ttu-id="d6b72-263">[À l’aide de la gestion des exceptions de BizTalk Server](http://msdn.microsoft.com/library/aa561229.aspx) (http://msdn.microsoft.com/library/aa561229.aspx).</span><span class="sxs-lookup"><span data-stu-id="d6b72-263">[Using BizTalk Server Exception Handling](http://msdn.microsoft.com/library/aa561229.aspx) (http://msdn.microsoft.com/library/aa561229.aspx).</span></span>  
  
-   <span data-ttu-id="d6b72-264">[Blog de Charles Young, BizTalk Server 2006 : Le modèle de Compensation](http://go.microsoft.com/fwlink/?LinkId=158017) (http://go.microsoft.com/fwlink/?LinkId=158017).</span><span class="sxs-lookup"><span data-stu-id="d6b72-264">[Charles Young Blog, BizTalk Server 2006: The Compensation Model](http://go.microsoft.com/fwlink/?LinkId=158017) (http://go.microsoft.com/fwlink/?LinkId=158017).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6b72-265">Pendant ce billet de blog a été écrit avec [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] à l’esprit les principes décrits dans le blog s’appliquent également aux [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6b72-265">While this blog was written with [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] in mind, the principles described in the blog also apply to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
## <a name="considerations-when-using-maps-in-orchestrations"></a><span data-ttu-id="d6b72-266">Considérations sur l’utilisation de mappages dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="d6b72-266">Considerations when using maps in orchestrations</span></span>  
 <span data-ttu-id="d6b72-267">Les considérations suivantes s’appliquent lors de l’utilisation de mappages dans les orchestrations :</span><span class="sxs-lookup"><span data-stu-id="d6b72-267">The following considerations apply when using maps in orchestrations:</span></span>  
  
-   <span data-ttu-id="d6b72-268">Si vous utilisez une carte à extraire ou définir les propriétés utilisées avec la logique métier dans une orchestration, utilisez les champs distinctifs ou des propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="d6b72-268">If you are using a map to extract or set properties used with business logic in an orchestration, use distinguished fields or promoted properties.</span></span> <span data-ttu-id="d6b72-269">Cette pratique doit être suivie, car lorsque extraction ou de la définition des valeurs avec une carte du document est chargé en mémoire toutefois lorsque des champs distinctifs ou les propriétés promues, le moteur d’orchestration accède au contexte du message et ne charge pas le document en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d6b72-269">This practice should be followed because when extracting or setting values with a map the document is loaded into memory however when using distinguished fields or promoted properties, the orchestration engine accesses the message context and does not load the document into memory.</span></span>  
  
-   <span data-ttu-id="d6b72-270">Si vous utilisez un mappage pour regrouper plusieurs champs en un seul, utilisez des champs distinctifs ou des propriétés promues avec une variable d'orchestration pour obtenir le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="d6b72-270">If you are using a map to aggregate several fields into one field, use distinguished fields or promoted properties with an orchestration variable to accumulate the result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b72-271">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6b72-271">See Also</span></span>  
 [<span data-ttu-id="d6b72-272">Optimisation des performances</span><span class="sxs-lookup"><span data-stu-id="d6b72-272">Optimizing Performance</span></span>](../technical-guides/optimizing-performance.md)