---
title: "Considérations sur l’utilisation du débogueur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, modified orchestrations
- Orchestration Debugger, planning
- atomic scopes
- planning, Orchestration Debugger
- Orchestration Debugger, atomic scopes
- Orchestration Debugger, simple types
- orchestrations, modifying
ms.assetid: 55bfef48-08bd-48bb-abd5-7264e683da46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2815da55bc74d822cb5fe2540347855db75b3a8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-orchestration-debugger"></a><span data-ttu-id="0cde3-102">Informations sur l'utilisation du débogueur de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="0cde3-102">Considerations when Using Orchestration Debugger</span></span>
<span data-ttu-id="0cde3-103">Les informations suivantes sont à prendre en compte lors de l'utilisation du débogueur de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="0cde3-103">Following are some things to consider when you work with the Orchestration Debugger.</span></span>  
  
## <a name="tracking-atomic-scopes"></a><span data-ttu-id="0cde3-104">Suivi des étendues atomiques</span><span class="sxs-lookup"><span data-stu-id="0cde3-104">Tracking atomic scopes</span></span>  
 <span data-ttu-id="0cde3-105">Une orchestration peut contenir des étendues atomiques permettant d'inclure des appels dans le moteur des règles.</span><span class="sxs-lookup"><span data-stu-id="0cde3-105">An orchestration can contain atomic scopes to include calls to the Rule Engine.</span></span> <span data-ttu-id="0cde3-106">Si vous joignez une instance dans le débogueur de l'orchestration, toute étendue atomique dans l'instance de l'orchestration provoquera l'apparition d'emplacements vides dans la liste des événements suivis.</span><span class="sxs-lookup"><span data-stu-id="0cde3-106">When you attach to an instance in the orchestration debugger, any atomic scopes in the orchestration instance will cause gaps to appear in the tracked events list.</span></span> <span data-ttu-id="0cde3-107">Ceci se produit pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="0cde3-107">This happens for two reasons:</span></span>  
  
-   <span data-ttu-id="0cde3-108">Les événements pour les formes à l'intérieur des transactions atomiques ne sont pas conservées tant que l'étendue n'est pas validée.</span><span class="sxs-lookup"><span data-stu-id="0cde3-108">Because events for the shapes inside atomic transactions do not get persisted until the scope commits</span></span>  
  
-   <span data-ttu-id="0cde3-109">Le débogueur recharge des événements à la fin de la liste, de sorte que tous les emplacements vides le restent pendant la session active. </span><span class="sxs-lookup"><span data-stu-id="0cde3-109">The debugger reloads events onto the end of the list, so any gaps remain unfilled during the live session.</span></span>  
  
 <span data-ttu-id="0cde3-110">Pour éliminer les emplacements vides, actualisez la vue.</span><span class="sxs-lookup"><span data-stu-id="0cde3-110">You can eliminate the gaps if you refresh the view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cde3-111">Vous ne pouvez pas définir un point d'arrêt sur des formes à l'intérieur d'une étendue atomique.</span><span class="sxs-lookup"><span data-stu-id="0cde3-111">You cannot set a breakpoint on shapes inside an atomic scope.</span></span>  
  
## <a name="setting-breakpoints-in-the-exception-handler-scope"></a><span data-ttu-id="0cde3-112">Définition de points d'arrêt dans l'étendue du gestionnaire d'exception</span><span class="sxs-lookup"><span data-stu-id="0cde3-112">Setting breakpoints in the exception handler scope</span></span>  
 <span data-ttu-id="0cde3-113">Si le point d'arrêt est défini au niveau du gestionnaire catch d'exception, les types d'exceptions doivent être marqués comme étant sérialisables, faute de quoi le débogueur d'orchestrations ne s'arrêtera pas aux points d'arrêt définis.</span><span class="sxs-lookup"><span data-stu-id="0cde3-113">If the breakpoint is set at the exception catch handler, the exception types must be marked as serializable, or the orchestration debugger will not stop at the breakpoints you set.</span></span> <span data-ttu-id="0cde3-114">Cela est dû au fait que le débogueur d'orchestrations effectue une persistance au niveau du point d'arrêt. Par conséquent, lorsque l'état de l'instance d'orchestration comporte un objet non sérialisable, une exception de persistance est générée, et, dans le cas présent, une exception DebugBreakPointFailedException est également envoyée.</span><span class="sxs-lookup"><span data-stu-id="0cde3-114">This is because of that the orchestration debugger does persistence at the breakpoint, therefore, when there is a non-serializable object in the orchestration instance state, a persistence exception will be thrown, and in this case, you will also receive a DebugBreakPointFailedException exception.</span></span>  
  
## <a name="tracking-a-modified-orchestration"></a><span data-ttu-id="0cde3-115">Suivi d'une orchestration modifiée</span><span class="sxs-lookup"><span data-stu-id="0cde3-115">Tracking a modified orchestration</span></span>  
 <span data-ttu-id="0cde3-116">Si vous suivez une orchestration modifiée sans changer le numéro de version, vous devez redémarrer toutes les instances hôtes auxquelles l'orchestration est inscrite.</span><span class="sxs-lookup"><span data-stu-id="0cde3-116">If you track an orchestration modified without changing the version number, you must restart all the host instances to which the orchestration is enlisted.</span></span> <span data-ttu-id="0cde3-117">Cette opération garantit que toute modification de forme dans la nouvelle version déployée s'affiche correctement pendant votre utilisation du débogueur de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="0cde3-117">This insures that any shape change in the newly deployed version displays correctly, as you step through the Orchestration Debugger.</span></span>  
  
## <a name="tracking-simple-types"></a><span data-ttu-id="0cde3-118">Suivi des types simples</span><span class="sxs-lookup"><span data-stu-id="0cde3-118">Tracking simple types</span></span>  
 <span data-ttu-id="0cde3-119">Le débogueur de l'orchestration ne prend en charge que les types simples.</span><span class="sxs-lookup"><span data-stu-id="0cde3-119">The Orchestration Debugger only supports simple types.</span></span> <span data-ttu-id="0cde3-120">Par exemple, si vous effectuez le suivi d'un message multipartie contenant un objet .NET, vous pouvez afficher les propriétés de toutes les parties du message, à l'exception des propriétés de l'objet .NET.</span><span class="sxs-lookup"><span data-stu-id="0cde3-120">For example, if you track a multipart message that contains a .NET object you can view the properties of all message parts, with the exception of the .NET object properties.</span></span>  
  
 <span data-ttu-id="0cde3-121">Lorsqu'une orchestration apparaît avec l'état Point d'arrêt et que le débogueur de l'orchestration démarre, vous pouvez exécuter les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="0cde3-121">When an orchestration appears in the In Breakpoint state and the Orchestration Debugger starts, you can perform the following actions:</span></span>  
  
-   <span data-ttu-id="0cde3-122">Utilisez le **attacher** option de service.</span><span class="sxs-lookup"><span data-stu-id="0cde3-122">Use the **Attach** service option.</span></span>  
  
-   <span data-ttu-id="0cde3-123">vérifier les étapes déjà achevées ;</span><span class="sxs-lookup"><span data-stu-id="0cde3-123">Review the steps that have already completed.</span></span>  
  
-   <span data-ttu-id="0cde3-124">afficher l'état des variables et des messages ;</span><span class="sxs-lookup"><span data-stu-id="0cde3-124">View the state of variables and messages.</span></span>  
  
-   <span data-ttu-id="0cde3-125">définir des points d'arrêt supplémentaires ;</span><span class="sxs-lookup"><span data-stu-id="0cde3-125">Set additional breakpoints.</span></span>  
  
-   <span data-ttu-id="0cde3-126">Sélectionnez le **continuer les services** option.</span><span class="sxs-lookup"><span data-stu-id="0cde3-126">Select the **Continue Service** option.</span></span>  
  
-   <span data-ttu-id="0cde3-127">répéter une étape autant de fois que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0cde3-127">Repeat any steps as required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cde3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cde3-128">See Also</span></span>  
 <span data-ttu-id="0cde3-129">[Mode interactif dans le débogueur de l’Orchestration](../core/interactive-mode-in-orchestration-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="0cde3-129">[Interactive Mode in Orchestration Debugger](../core/interactive-mode-in-orchestration-debugger.md) </span></span>  
 [<span data-ttu-id="0cde3-130">Débogage d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="0cde3-130">Debugging an Orchestration</span></span>](../core/debugging-an-orchestration.md)