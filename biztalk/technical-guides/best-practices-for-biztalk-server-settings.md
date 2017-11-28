---
title: "Meilleures pratiques pour les paramètres de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e62024e1-f502-45a8-932f-edd8460bcf5f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf1f89ced33be6f10ceaae37ccb2c899c4e01eac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-biztalk-server-settings"></a><span data-ttu-id="afc40-102">Meilleures pratiques pour les paramètres de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="afc40-102">Best Practices for BizTalk Server Settings</span></span>
<span data-ttu-id="afc40-103">Cette rubrique répertorie les meilleures pratiques à suivre quand vous effectuez les procédures de préparation opérationnel pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="afc40-103">This topic lists best practices that you should follow as you perform operational readiness procedures for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="afc40-104">**Configurer le traitement par lots du message pour augmenter les performances de l’adaptateur**</span><span class="sxs-lookup"><span data-stu-id="afc40-104">**Configure message batching to increase adapter performance**</span></span>  
  
-   <span data-ttu-id="afc40-105">Réduisez le nombre de transactions effectuées par un adaptateur en combinant plusieurs opérations dans un lot unique.</span><span class="sxs-lookup"><span data-stu-id="afc40-105">Minimize the number of transactions performed by an adapter by combining more than one operation into a single batch.</span></span>  
  
-   <span data-ttu-id="afc40-106">Limiter la taille de lot en fonction du nombre total d’octets dans le lot, en plus du nombre de messages.</span><span class="sxs-lookup"><span data-stu-id="afc40-106">Limit the batch size based on the total number of bytes in the batch, in addition to message count.</span></span> <span data-ttu-id="afc40-107">Pour plus d’informations sur la limitation de la taille de lot, consultez [configurer le traitement par lot pour améliorer les performances de l’adaptateur](../technical-guides/configuring-batching-to-improve-adapter-performance.md).</span><span class="sxs-lookup"><span data-stu-id="afc40-107">For more information about limiting the batch size, see [Configuring Batching to Improve Adapter Performance](../technical-guides/configuring-batching-to-improve-adapter-performance.md).</span></span>  
  
 <span data-ttu-id="afc40-108">**Ajustez le seuil de messages volumineux**</span><span class="sxs-lookup"><span data-stu-id="afc40-108">**Adjust the large message threshold**</span></span>  
  
-   <span data-ttu-id="afc40-109">Pour améliorer le débit, augmentez le seuil de messages volumineux, ce qui réduit le nombre de messages volumineux qui sont en mémoire tampon sur le disque lors du mappage.</span><span class="sxs-lookup"><span data-stu-id="afc40-109">To improve throughput, increase the large message threshold, which lowers the number of large messages that are buffered to disk during mapping.</span></span>  
  
 <span data-ttu-id="afc40-110">**Déterminer les informations que vous devez suivre lors de la planification**</span><span class="sxs-lookup"><span data-stu-id="afc40-110">**Determine the information you need to track during planning**</span></span>  
  
-   <span data-ttu-id="afc40-111">Pendant les phases de planification, vous devez déterminer les informations que vous avez besoin pour effectuer le suivi. Ainsi, après avoir déployé le projet, vous pouvez définir les options de suivi et limiter la quantité de données suivies afin de vous donner uniquement les informations que vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="afc40-111">You should decide during the planning stages which information you need to track. This way, after you deploy the project, you can set the tracking options and limit the amount of tracked data to give you only the information you need.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="afc40-112">Pour plus d’informations sur les meilleures pratiques relatives au suivi, consultez [planification pour le suivi](../technical-guides/planning-for-tracking.md) dans ce guide et [suivi des activités et](http://go.microsoft.com/fwlink/p/?LinkId=154187) (http://go.microsoft.com/fwlink/p/?LinkId=154187).</span><span class="sxs-lookup"><span data-stu-id="afc40-112">For more information about best practices related to tracking, see [Planning for Tracking](../technical-guides/planning-for-tracking.md) in this guide and [Health and Activity Tracking](http://go.microsoft.com/fwlink/p/?LinkId=154187) (http://go.microsoft.com/fwlink/p/?LinkId=154187).</span></span>  
  
 <span data-ttu-id="afc40-113">**Ne suivez pas tous les messages**</span><span class="sxs-lookup"><span data-stu-id="afc40-113">**Do not track all messages**</span></span>  
  
-   <span data-ttu-id="afc40-114">Nous vous recommandons de pas suivre tous les messages.</span><span class="sxs-lookup"><span data-stu-id="afc40-114">We recommend that you not track all messages.</span></span> <span data-ttu-id="afc40-115">Il s’agit, car chaque fois qu’un message est couvertes, BizTalk Server effectue une autre copie du message.</span><span class="sxs-lookup"><span data-stu-id="afc40-115">This is because each time a message is touched, BizTalk Server makes another copy of the message.</span></span> <span data-ttu-id="afc40-116">Vous pouvez limiter à la place de la portée en effectuant le suivi d’un port spécifique uniquement.</span><span class="sxs-lookup"><span data-stu-id="afc40-116">You can instead narrow the scope by tracking only a specific port.</span></span> <span data-ttu-id="afc40-117">Cela permet d’optimiser les performances de votre système et de conserver les bases de données ne soit pas encombré.</span><span class="sxs-lookup"><span data-stu-id="afc40-117">This helps to maximize the performance of your system and to keep the databases uncluttered.</span></span>  
  
 <span data-ttu-id="afc40-118">**Définition du suivi sur les ports d’envoi et ports au lieu d’un pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="afc40-118">**Set tracking on send ports and receive ports instead of on a pipeline**</span></span>  
  
-   <span data-ttu-id="afc40-119">Si vous définissez des options de suivi sur les pipelines, vous allez également définir les options de suivi global pour tous les ports qui utilise le pipeline.</span><span class="sxs-lookup"><span data-stu-id="afc40-119">If you set tracking options on pipelines, you will also set the tracking options globally for every port that uses the pipeline.</span></span> <span data-ttu-id="afc40-120">Cela peut à son tour entraîner beaucoup plus de données en cours de suivi que vous avez l’intention, qui ralentit les performances du système.</span><span class="sxs-lookup"><span data-stu-id="afc40-120">This in turn may result in far more data being tracked than you intend, which will slow system performance.</span></span> <span data-ttu-id="afc40-121">Au lieu de cela, vous pouvez définir les options de suivi de l’envoi de ports et les ports de réception.</span><span class="sxs-lookup"><span data-stu-id="afc40-121">Instead, you can set tracking options on send ports and receive ports.</span></span>  
  
 <span data-ttu-id="afc40-122">**Ajuster la limitation basée sur l’utilisation des ressources**</span><span class="sxs-lookup"><span data-stu-id="afc40-122">**Adjust throttling based on resource utilization**</span></span>  
  
-   <span data-ttu-id="afc40-123">La limitation dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est configuré par défaut pour fournir une protection intégrée satisfaisante du système.</span><span class="sxs-lookup"><span data-stu-id="afc40-123">Throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured by default to provide good protection for the system.</span></span> <span data-ttu-id="afc40-124">Surveillez les compteurs de performances pour la limitation des États pour voir si la limitation est en cours.</span><span class="sxs-lookup"><span data-stu-id="afc40-124">Monitor the performance counters for throttling states to see if throttling is taking place.</span></span> <span data-ttu-id="afc40-125">Évaluer par vous-même si la ressource sur laquelle la limitation est basée (par exemple, la base de données d’utilisation de taille ou de la mémoire) est sous ou surutilisée.</span><span class="sxs-lookup"><span data-stu-id="afc40-125">Then gauge for yourself if the resource on which throttling is based (for example, database size or memory usage) is under or over utilized.</span></span> <span data-ttu-id="afc40-126">Ensuite, ajustez la limitation les seuils au-dessus ou au-dessous.</span><span class="sxs-lookup"><span data-stu-id="afc40-126">Next, adjust the throttling thresholds up or down accordingly.</span></span> <span data-ttu-id="afc40-127">Pour plus d’informations, consultez [ajuster les seuils de limitation : quand et pourquoi](http://go.microsoft.com/fwlink/p/?LinkId=154188) (http://go.microsoft.com/fwlink/p/?LinkId=154188).</span><span class="sxs-lookup"><span data-stu-id="afc40-127">For more information, see [Adjusting Throttling Thresholds: When and Why](http://go.microsoft.com/fwlink/p/?LinkId=154188) (http://go.microsoft.com/fwlink/p/?LinkId=154188).</span></span>  
  
 <span data-ttu-id="afc40-128">**Utilisez le pipeline PassThruTransmit si possible**</span><span class="sxs-lookup"><span data-stu-id="afc40-128">**Use the PassThruTransmit pipeline if possible**</span></span>  
  
-   <span data-ttu-id="afc40-129">Si aucun traitement de document n’est requis avant d’envoyer un message vers sa destination, utilisez le pipeline PassThruTransmit au lieu du pipeline d’envoi XML.</span><span class="sxs-lookup"><span data-stu-id="afc40-129">If no document processing is required before sending a message to its destination, use the PassThruTransmit pipeline instead of the XML send pipeline.</span></span>  
  
 <span data-ttu-id="afc40-130">**Réduire l’utilisation de l’orchestration « de début de la forme et de fin » suivi d’événements**</span><span class="sxs-lookup"><span data-stu-id="afc40-130">**Minimize usage of orchestration “Shape start and end” tracking events**</span></span>  
  
-   <span data-ttu-id="afc40-131">Lors de la forme de suivi de l’orchestration présente des avantages évidents pour le débogage de l’orchestration, il a des implications en matière d’évolutivité et de performances.</span><span class="sxs-lookup"><span data-stu-id="afc40-131">While orchestration shape tracking has obvious benefits for orchestration debugging, it has performance and scalability implications.</span></span> <span data-ttu-id="afc40-132">Le **forme début et fin** le suivi des événements peuvent provoquer un surcroît de traitement.</span><span class="sxs-lookup"><span data-stu-id="afc40-132">The **Shape start and end** tracking event can cause significant overhead.</span></span> <span data-ttu-id="afc40-133">Il est préférable réduire son utilisation dans des environnements de production où un débit élevé est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="afc40-133">It is best to minimize its usage in production environments where high throughput is necessary.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="afc40-134">**La forme début et fin** événements de suivi sont activées par défaut sur toutes les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="afc40-134">**Shape start and end** tracking events are ENABLED by default on all orchestrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc40-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afc40-135">See Also</span></span>  
 [<span data-ttu-id="afc40-136">Liste de vérification : Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="afc40-136">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)