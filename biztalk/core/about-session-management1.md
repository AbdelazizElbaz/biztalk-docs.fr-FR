---
title: "À propos de la Session Management1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1848619-d97a-4f1e-ba94-59861bd7aedf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 336deb34e5587e64c5177cd0a439c756cf0f2b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-session-management"></a><span data-ttu-id="73dfc-102">À propos de la gestion des sessions</span><span class="sxs-lookup"><span data-stu-id="73dfc-102">About Session Management</span></span>
<span data-ttu-id="73dfc-103">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld crée une session de connexion permettant d'envoyer un appel au serveur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="73dfc-103">The Microsoft BizTalk Adapter for JD Edwards OneWorld creates a connection session to send a call to the JD Edwards OneWorld server.</span></span> <span data-ttu-id="73dfc-104">Lorsque l'appel est terminé, la session est placée dans un pool afin d'être réutilisée lors d'un appel suivant.</span><span class="sxs-lookup"><span data-stu-id="73dfc-104">When the call terminates, the session is put in a pool to be re-used by a subsequent call.</span></span> <span data-ttu-id="73dfc-105">L'adaptateur crée plusieurs sessions de connexion afin de traiter des appels simultanés en direction du serveur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="73dfc-105">The adapter creates multiple connection sessions to handle concurrent calls to the JD Edwards OneWorld server.</span></span> <span data-ttu-id="73dfc-106">Le pool est régulièrement nettoyé afin de supprimer les sessions qui ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="73dfc-106">The pool is periodically cleaned to remove sessions that are no longer necessary.</span></span>  
  
 <span data-ttu-id="73dfc-107">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld fournit deux propriétés de contexte de message permettant de contrôler le moment d'exécution des appels au sein d'une même session.</span><span class="sxs-lookup"><span data-stu-id="73dfc-107">The Microsoft BizTalk Adapter for JD Edwards OneWorld provides two message context properties to control when calls must occur within the same session.</span></span>  
  
|<span data-ttu-id="73dfc-108">Nom</span><span class="sxs-lookup"><span data-stu-id="73dfc-108">Name</span></span>|<span data-ttu-id="73dfc-109">Type</span><span class="sxs-lookup"><span data-stu-id="73dfc-109">Type</span></span>|<span data-ttu-id="73dfc-110">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="73dfc-110">Default</span></span>|  
|----------|----------|-------------|  
|<span data-ttu-id="73dfc-111">JDE.SessionID</span><span class="sxs-lookup"><span data-stu-id="73dfc-111">JDE.SessionID</span></span>|<span data-ttu-id="73dfc-112">int</span><span class="sxs-lookup"><span data-stu-id="73dfc-112">Int</span></span>|<span data-ttu-id="73dfc-113">0</span><span class="sxs-lookup"><span data-stu-id="73dfc-113">0</span></span>|  
|<span data-ttu-id="73dfc-114">JDE.ReserveSession</span><span class="sxs-lookup"><span data-stu-id="73dfc-114">JDE.ReserveSession</span></span>|<span data-ttu-id="73dfc-115">boolean</span><span class="sxs-lookup"><span data-stu-id="73dfc-115">boolean</span></span>|<span data-ttu-id="73dfc-116">false</span><span class="sxs-lookup"><span data-stu-id="73dfc-116">false</span></span>|  
  
 <span data-ttu-id="73dfc-117">La gestion de session n'est pas requise si la fonction commerciale nécessite un appel unique au serveur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="73dfc-117">Session management is unnecessary if the business function requires a single call to the JD Edwards OneWorld server.</span></span> <span data-ttu-id="73dfc-118">L'adaptateur peut récupérer toute session disponible et celle-ci reste accessible pour tout appel suivant.</span><span class="sxs-lookup"><span data-stu-id="73dfc-118">The adapter can pick any available session and the session remains available for any following calls.</span></span> <span data-ttu-id="73dfc-119">Dans ce scénario, vous pouvez ignorer les propriétés de contexte de message étant donné que leur valeur par défaut est appropriée.</span><span class="sxs-lookup"><span data-stu-id="73dfc-119">In this scenario, you can ignore the message context properties as the defaults are appropriate.</span></span>  
  
 <span data-ttu-id="73dfc-120">Certaines fonctionnalités de JD Edwards OneWorld, telles que la création de SalesOrder, nécessitent d'effectuer plusieurs appels au serveur JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="73dfc-120">Some JD Edwards OneWorld functionality requires multiple calls to the JD Edwards OneWorld server; for example, the creation of a SalesOrder.</span></span> <span data-ttu-id="73dfc-121">Le premier appel effectué à BeginDoc crée un élément SalesOrder vide.</span><span class="sxs-lookup"><span data-stu-id="73dfc-121">The first call to BeginDoc creates an empty SalesOrder.</span></span> <span data-ttu-id="73dfc-122">Chaque appel suivant effectué à EditLine lui ajoute un élément de ligne.</span><span class="sxs-lookup"><span data-stu-id="73dfc-122">Each subsequent call to EditLine adds one line item to the SalesOrder.</span></span> <span data-ttu-id="73dfc-123">Pour terminer, l'appel effectué à EndDoc termine SalesOrder.</span><span class="sxs-lookup"><span data-stu-id="73dfc-123">Finally the call to EndDoc closes the SalesOrder.</span></span>  
  
```  
BeginDoc  
   EditLine  
   EditLine  
   ...  
EndDoc  
```  
  
 <span data-ttu-id="73dfc-124">Pour que cette opération réussisse, tous les appels passés à SalesOrder doivent être effectués sous la même session.</span><span class="sxs-lookup"><span data-stu-id="73dfc-124">To be successful, all the calls for a single SalesOrder must be sent on the same session.</span></span> <span data-ttu-id="73dfc-125">Pour ce faire, affectez des propriétés de contexte de message pour indiquer à l'adaptateur les actions que la session doit effectuer.</span><span class="sxs-lookup"><span data-stu-id="73dfc-125">To do this, assign message context properties to instruct the adapter what to do with the session.</span></span> <span data-ttu-id="73dfc-126">Pour SalesOrder par exemple, voici les valeurs qui doivent être affectées aux propriétés de contexte de message afin de gérer la session JD OneWorld :</span><span class="sxs-lookup"><span data-stu-id="73dfc-126">For the SalesOrder example, these are the values that would be assigned to the message context properties to handle the JD OneWorld session:</span></span>  
  
|<span data-ttu-id="73dfc-127">Fonction</span><span class="sxs-lookup"><span data-stu-id="73dfc-127">Function</span></span>|<span data-ttu-id="73dfc-128">SessionID</span><span class="sxs-lookup"><span data-stu-id="73dfc-128">SessionID</span></span>|<span data-ttu-id="73dfc-129">ReserveSession</span><span class="sxs-lookup"><span data-stu-id="73dfc-129">ReserveSession</span></span>|  
|--------------|---------------|--------------------|  
|<span data-ttu-id="73dfc-130">BeginDoc</span><span class="sxs-lookup"><span data-stu-id="73dfc-130">BeginDoc</span></span>|<span data-ttu-id="73dfc-131">0</span><span class="sxs-lookup"><span data-stu-id="73dfc-131">0</span></span>|<span data-ttu-id="73dfc-132">true</span><span class="sxs-lookup"><span data-stu-id="73dfc-132">true</span></span>|  
|<span data-ttu-id="73dfc-133">EditLine</span><span class="sxs-lookup"><span data-stu-id="73dfc-133">EditLine</span></span>|<span data-ttu-id="73dfc-134">Copié de la réponse BeginDoc</span><span class="sxs-lookup"><span data-stu-id="73dfc-134">Copied from BeginDoc reply</span></span>|<span data-ttu-id="73dfc-135">true</span><span class="sxs-lookup"><span data-stu-id="73dfc-135">true</span></span>|  
|<span data-ttu-id="73dfc-136">EditLine</span><span class="sxs-lookup"><span data-stu-id="73dfc-136">EditLine</span></span>|<span data-ttu-id="73dfc-137">Copié de la réponse BeginDoc</span><span class="sxs-lookup"><span data-stu-id="73dfc-137">Copied from BeginDoc reply</span></span>|<span data-ttu-id="73dfc-138">true</span><span class="sxs-lookup"><span data-stu-id="73dfc-138">true</span></span>|  
|<span data-ttu-id="73dfc-139">EndDoc</span><span class="sxs-lookup"><span data-stu-id="73dfc-139">EndDoc</span></span>|<span data-ttu-id="73dfc-140">Copié de la réponse BeginDoc</span><span class="sxs-lookup"><span data-stu-id="73dfc-140">Copied from BeginDoc reply</span></span>|<span data-ttu-id="73dfc-141">false</span><span class="sxs-lookup"><span data-stu-id="73dfc-141">false</span></span>|  
  
-   <span data-ttu-id="73dfc-142">Pour le premier appel, l'adaptateur est libre de choisir une session disponible (car la valeur de SessionID est zéro).</span><span class="sxs-lookup"><span data-stu-id="73dfc-142">For the first call, the adapter is free to choose any available session (because the SessionID is zero).</span></span>  
  
-   <span data-ttu-id="73dfc-143">L'adaptateur renvoie l'élément SessionID qui a été utilisé dans la réponse BeginDoc.</span><span class="sxs-lookup"><span data-stu-id="73dfc-143">The adapter returns the SessionID that was used in the BeginDoc reply.</span></span>  
  
-   <span data-ttu-id="73dfc-144">La propriété ReserveSession indique à l'adaptateur de réserver cette session pour des appels ultérieurs qui exigent explicitement l'utilisation de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="73dfc-144">The ReserveSession property tells the adapter to reserve this session for following calls that explicitly requests this session.</span></span> <span data-ttu-id="73dfc-145">Ainsi, aucun autre appel ne pourra réutiliser accidentellement la session, car celle-ci est réservée.</span><span class="sxs-lookup"><span data-stu-id="73dfc-145">No other calls can accidentally re-use the session because it is reserved.</span></span>  
  
-   <span data-ttu-id="73dfc-146">En attribuant à l'élément SessionID la valeur renvoyée dans BeginDoc, les appels suivants peuvent passer une requête pour la session.</span><span class="sxs-lookup"><span data-stu-id="73dfc-146">Subsequent calls request the session by setting the SessionID to the value returned in BeginDoc.</span></span>  
  
-   <span data-ttu-id="73dfc-147">La propriété ReserveSession est définie sur true, du moins jusqu'au dernier appel de la série.</span><span class="sxs-lookup"><span data-stu-id="73dfc-147">The ReserveSession property is set to true, at least until the last call in the series.</span></span>  
  
-   <span data-ttu-id="73dfc-148">Le dernier appel définit la propriété ReserveSession sur false ; de cette manière, la session devient disponible pour n'importe quel appel ultérieur.</span><span class="sxs-lookup"><span data-stu-id="73dfc-148">The last call sets ReserveSession to false to make the session available to any following call.</span></span> <span data-ttu-id="73dfc-149">Toutefois, l'orchestration peut décider de conserver la session pour effectuer d'autres appels.</span><span class="sxs-lookup"><span data-stu-id="73dfc-149">However, the orchestration can elect to keep the session for more calls.</span></span>  
  
 <span data-ttu-id="73dfc-150">Si la session reste inactive pendant un certain moment, elle est récupérée par le garbage collector (ramasse-miettes), même si, par erreur, la session est toujours réservée.</span><span class="sxs-lookup"><span data-stu-id="73dfc-150">If the session is not used for a while, it will be garbage-collected by the pool, even if the session is still reserved by mistake.</span></span>  
  
 <span data-ttu-id="73dfc-151">Pour plus de détails sur les propriétés de contexte de message, consultez la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="73dfc-151">Refer to BizTalk Server documentation for more details on message context properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73dfc-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73dfc-152">See Also</span></span>  
 <span data-ttu-id="73dfc-153">[À l’aide des propriétés de contexte de Message](../core/using-message-context-properties2.md) </span><span class="sxs-lookup"><span data-stu-id="73dfc-153">[Using Message Context Properties](../core/using-message-context-properties2.md) </span></span>  
 <span data-ttu-id="73dfc-154">[Comment attribuer des valeurs de propriété de contexte de Message](../core/how-to-assign-message-context-property-values2.md) </span><span class="sxs-lookup"><span data-stu-id="73dfc-154">[How to Assign Message Context Property Values](../core/how-to-assign-message-context-property-values2.md) </span></span>  
 [<span data-ttu-id="73dfc-155">Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="73dfc-155">Tutorial: Using the BizTalk Adapter for JD Edwards OneWorld</span></span>](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld.md)