---
title: "Utilisation des filtres avec la forme d’un Message de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters, receive messages
- messages, filters
ms.assetid: 5310039b-6719-4971-933a-2da0573fb5e7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1434e9704e073cfef1503ef550409e6d6414bb7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-filters-with-the-receive-message-shape"></a><span data-ttu-id="d1c7f-102">Utilisation des filtres avec la forme d’un Message de réception</span><span class="sxs-lookup"><span data-stu-id="d1c7f-102">Using Filters With the Receive Message Shape</span></span>
<span data-ttu-id="d1c7f-103">Une expression de filtre est un paramètre facultatif qu'il est possible d'appliquer à une forme de réception d'une orchestration spécifiant la valeur True pour la propriété Activer.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-103">A filter expression is an optional parameter that can be applied to an orchestration receive shape that specifies a value of True for the Activate property.</span></span> <span data-ttu-id="d1c7f-104">Si vous définissez une expression de filtre, l'orchestration ne sera activée que si un message entrant remplit les conditions spécifiées dans l'expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-104">If a filter expression is specified then the orchestration will only be activated if an incoming message matches the condition(s) specified in the filter expression.</span></span> <span data-ttu-id="d1c7f-105">En l'absence d'expression de filtre, tout message entrant auquel est abonnée l'orchestration pourra activer cette dernière.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-105">If no filter expression is specified then any incoming message that the orchestration subscribes to will activate the orchestration.</span></span>  
  
 <span data-ttu-id="d1c7f-106">La création d'une expression de filtre permet de comparer la propriété d'un message entrant sur la partie gauche de l'expression avec une constante de la partie droite de l'expression.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-106">To create a filter expression, you compare a property of an incoming message on the left side of the expression with a constant on the right side of the expression.</span></span> <span data-ttu-id="d1c7f-107">Vous pouvez également créer des expressions composées en appliquant des opérateurs AND et OR à deux ou plusieurs expressions.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-107">You can also create compound expressions by applying the AND and OR operators to two or more expressions.</span></span> <span data-ttu-id="d1c7f-108">Enfin, vous avez la possibilité de ne pas définir d'expression de filtre, auquel cas tous les messages seront acceptés.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-108">You can also leave blank the filter expression, in which case all messages will be accepted.</span></span>  
  
 <span data-ttu-id="d1c7f-109">Une expression de filtre peut ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d1c7f-109">A filter expression might look like the following:</span></span>  
  
```  
InvoiceSchema.Quantity >= 1000  
```  
  
 <span data-ttu-id="d1c7f-110">Dans cet exemple, un message entrant est présenté à l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-110">In this example, an incoming message is presented to the orchestration.</span></span> <span data-ttu-id="d1c7f-111">L’orchestration a une activation **réception** forme (le **Activation** est définie sur **True** afin que la réception d’un message donné entraînent l’orchestration à exécuter ) avec l’expression de filtre précédente appliquée.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-111">The orchestration has an activation **Receive** shape (the **Activation** property is set to **True** so that receipt of a certain message will cause the orchestration to be run) with the preceding filter expression applied to it.</span></span> <span data-ttu-id="d1c7f-112">Le message entrant doit avoir la propriété nommée Quantity dans l’espace de noms **InvoiceSchema**.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-112">The incoming message is expected to have property called Quantity in the namespace **InvoiceSchema**.</span></span> <span data-ttu-id="d1c7f-113">L'orchestration n'acceptant que les factures portant sur au moins 1 000 articles, le moteur d'exécution vérifie le message entrant avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-113">The orchestration accepts only invoices for 1000 or more items, so the runtime engine checks the incoming message before it runs.</span></span>  
  
 <span data-ttu-id="d1c7f-114">Le tableau suivant montre les opérateurs qu'il est possible d'utiliser dans les expressions de filtre.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-114">The following table shows operators that you can use in filter expressions.</span></span>  
  
|<span data-ttu-id="d1c7f-115">Opérateur</span><span class="sxs-lookup"><span data-stu-id="d1c7f-115">Operator</span></span>|<span data-ttu-id="d1c7f-116"> Description</span><span class="sxs-lookup"><span data-stu-id="d1c7f-116">Description</span></span>|<span data-ttu-id="d1c7f-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="d1c7f-117">Example</span></span>|  
|--------------|-----------------|-------------|  
|==|<span data-ttu-id="d1c7f-118">égal à</span><span class="sxs-lookup"><span data-stu-id="d1c7f-118">equal to</span></span>|<span data-ttu-id="d1c7f-119">ReqMsg(Total) == 100</span><span class="sxs-lookup"><span data-stu-id="d1c7f-119">ReqMsg(Total) == 100</span></span>|  
|<span data-ttu-id="d1c7f-120">!=</span><span class="sxs-lookup"><span data-stu-id="d1c7f-120">!=</span></span>|<span data-ttu-id="d1c7f-121">différent de</span><span class="sxs-lookup"><span data-stu-id="d1c7f-121">not equal to</span></span>|<span data-ttu-id="d1c7f-122">ReqMsg(Total) != 100</span><span class="sxs-lookup"><span data-stu-id="d1c7f-122">ReqMsg(Total) != 100</span></span>|  
|<|<span data-ttu-id="d1c7f-123">inférieur à</span><span class="sxs-lookup"><span data-stu-id="d1c7f-123">less than</span></span>|<span data-ttu-id="d1c7f-124">ReqMsg(Total) \< 100</span><span class="sxs-lookup"><span data-stu-id="d1c7f-124">ReqMsg(Total) \< 100</span></span>|  
|>|<span data-ttu-id="d1c7f-125">supérieur à</span><span class="sxs-lookup"><span data-stu-id="d1c7f-125">greater than</span></span>|<span data-ttu-id="d1c7f-126">ReqMsg(Total) > 100</span><span class="sxs-lookup"><span data-stu-id="d1c7f-126">ReqMsg(Total) > 100</span></span>|  
|<=|<span data-ttu-id="d1c7f-127">inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="d1c7f-127">less than or equal to</span></span>|<span data-ttu-id="d1c7f-128">ReqMsg(Total) \<= 100</span><span class="sxs-lookup"><span data-stu-id="d1c7f-128">ReqMsg(Total) \<= 100</span></span>|  
|>=|<span data-ttu-id="d1c7f-129">supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="d1c7f-129">greater than or equal to</span></span>|<span data-ttu-id="d1c7f-130">ReqMsg(Total) >= 100</span><span class="sxs-lookup"><span data-stu-id="d1c7f-130">ReqMsg(Total) >= 100</span></span>|  
|<span data-ttu-id="d1c7f-131">existe</span><span class="sxs-lookup"><span data-stu-id="d1c7f-131">exists</span></span>|<span data-ttu-id="d1c7f-132">existe</span><span class="sxs-lookup"><span data-stu-id="d1c7f-132">exists</span></span>|<span data-ttu-id="d1c7f-133">ReqMsg(Description) existe</span><span class="sxs-lookup"><span data-stu-id="d1c7f-133">ReqMsg(Description) exists</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d1c7f-134">Les valeurs de chaîne dans les expressions de filtre sont placées entre guillemets, par exemple : reqmsg (description) = « État ».</span><span class="sxs-lookup"><span data-stu-id="d1c7f-134">String values in filter expressions are enclosed in quotation marks, for example: ReqMsg(Description) = "Purchase Order Status".</span></span> <span data-ttu-id="d1c7f-135">Les valeurs de caractère sont interdites dans une expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-135">You cannot use a character value in a filter expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1c7f-136">Si votre réception avec activation est associée à un port à liaison directe et que vous envoyez par la suite un message du même type doté de la même valeur pour la propriété testée dans votre filtre, vous allez créer une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-136">If your activate receive is associated with a direct-bound port, and you subsequently send a message of the same type with the same value for the property tested in your filter, you will create an infinite loop.</span></span> <span data-ttu-id="d1c7f-137">Le message sera envoyé dans la base de données MessageBox, où il sera de nouveau récupéré, car il remplit les critères du filtre.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-137">The message will go to the MessageBox, where it will be picked up again because it matches the filter criteria.</span></span> <span data-ttu-id="d1c7f-138">Pour éviter ce problème, vous pouvez filtrer sur une autre propriété, envoyer un message d'un type différent ou penser à modifier la valeur de la propriété avant d'envoyer un message du même type.</span><span class="sxs-lookup"><span data-stu-id="d1c7f-138">To avoid this, you should either filter on a different property, send a message of a different type, or be sure to change the value of the property before sending out a message of the same type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c7f-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1c7f-139">See Also</span></span>  
 <span data-ttu-id="d1c7f-140">[Comment configurer la forme réception](../core/how-to-configure-the-receive-shape.md) </span><span class="sxs-lookup"><span data-stu-id="d1c7f-140">[How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md) </span></span>  
 <span data-ttu-id="d1c7f-141">[À l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="d1c7f-141">[Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md) </span></span>  
 <span data-ttu-id="d1c7f-142">[À l’aide des champs distinctifs et les champs de propriété](../core/using-distinguished-fields-and-property-fields.md) </span><span class="sxs-lookup"><span data-stu-id="d1c7f-142">[Using Distinguished Fields and Property Fields](../core/using-distinguished-fields-and-property-fields.md) </span></span>  
 [<span data-ttu-id="d1c7f-143">À l’aide de Messages dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="d1c7f-143">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)