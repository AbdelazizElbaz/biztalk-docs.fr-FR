---
title: Gestion des Exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, handlers
- scopes, errors
- errors, scopes
- handlers [adapters], errors
ms.assetid: 30b88d8a-8737-4700-b856-1b49fdf6b6d0
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 004e4f29bcfc292edb33bae816a52b588a89771c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-exceptions-are-handled"></a><span data-ttu-id="84d59-102">Gestion des Exceptions </span><span class="sxs-lookup"><span data-stu-id="84d59-102">How Exceptions Are Handled</span></span>
<span data-ttu-id="84d59-103">Lorsqu’une exception se produit dans une étendue, chaque thread d’exécution logique présent de l’étendue est arrêté.</span><span class="sxs-lookup"><span data-stu-id="84d59-103">When an exception occurs within a scope, each logical thread of execution in the scope is stopped.</span></span> <span data-ttu-id="84d59-104">Le moteur d'exécution recherche un gestionnaire d'exceptions pour l’exception appropriée.</span><span class="sxs-lookup"><span data-stu-id="84d59-104">The runtime engine tries to find an exception handler for the appropriate exception.</span></span>  
  
 <span data-ttu-id="84d59-105">Si le gestionnaire d’exception trouvé correspond au type spécifique ou à un de ses types de base, le contrôle est transmis au gestionnaire et son code est exécuté.</span><span class="sxs-lookup"><span data-stu-id="84d59-105">If the exception handler is found that matches the specific type or one of its base types, control passes to that handler and its code runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84d59-106">Le type d’exception doit être dérivé **System.Exception**.</span><span class="sxs-lookup"><span data-stu-id="84d59-106">The exception type must be derived from **System.Exception**.</span></span>  
  
 <span data-ttu-id="84d59-107">Les gestionnaires d’exception sont séquentiels ; c’est-à-dire qu’ils feront l’objet d’une vérification afin de déterminer s’ils peuvent ou non gérer une exception particulière.</span><span class="sxs-lookup"><span data-stu-id="84d59-107">Exception handlers are sequential; that is, they will be checked in order to see if they can handle a particular exception.</span></span> <span data-ttu-id="84d59-108">Pour qu’ils fonctionnent correctement, les gestionnaires d’exception doivent être placés de telle sorte que ceux qui assurent la gestion de types spécifiques arrivent en premier, suivi de ceux qui gèrent les types plus généraux.</span><span class="sxs-lookup"><span data-stu-id="84d59-108">To work properly, exception handlers must be placed so that those handling more specific types come first, followed by those handling more general types.</span></span> <span data-ttu-id="84d59-109">Cela permet de garantir qu'une exception d'un type spécifique est gérée par le gestionnaire approprié, et non par un gestionnaire conçu pour gérer un type de base.</span><span class="sxs-lookup"><span data-stu-id="84d59-109">This is so that you can ensure that an exception of a specific type is handled by the appropriate handler, rather than one designed to handle a base type.</span></span>  
  
 <span data-ttu-id="84d59-110">Si le gestionnaire d’exception fonctionne normalement, le contrôle est transmis à l'étendue voisine.</span><span class="sxs-lookup"><span data-stu-id="84d59-110">If the exception handler completes normally, control passes to the surrounding scope.</span></span> <span data-ttu-id="84d59-111">Si aucune exception n’est émise dans l'étendue voisine, l'exécution de l'orchestration se poursuit.</span><span class="sxs-lookup"><span data-stu-id="84d59-111">If no exception has been thrown in the surrounding scope, the orchestration continues to run.</span></span> <span data-ttu-id="84d59-112">Si le gestionnaire d’exception se termine par une instruction throw, l'exception d'origine est à nouveau émise pour agir sur l’étendue voisine, sauf si vous avez précisé qu’une exception différente doit être émise.</span><span class="sxs-lookup"><span data-stu-id="84d59-112">If the exception handler ends with a throw statement, the original exception is thrown again for the surrounding scope to act upon, unless you specify a different exception that you want to be thrown.</span></span>  
  
 <span data-ttu-id="84d59-113">Si aucun gestionnaire ne peut être localisé, le gestionnaire d'exceptions par défaut est exécuté.</span><span class="sxs-lookup"><span data-stu-id="84d59-113">If no exception handler can be located, the default exception handler will run.</span></span> <span data-ttu-id="84d59-114">Le gestionnaire d’exception par défaut pour une étendue appellera les compensations pour toutes les transactions imbriquées, puis émettra à nouveau l'exception.</span><span class="sxs-lookup"><span data-stu-id="84d59-114">The default exception handler for a scope will call the compensations for any nested transactions, and then throw the exception again.</span></span> <span data-ttu-id="84d59-115">Si vous écrivez votre propre gestionnaire d'exception, vous pouvez choisir de ne pas propager l’exception.</span><span class="sxs-lookup"><span data-stu-id="84d59-115">If you write your own exception handler, you can choose not to propagate the exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d59-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84d59-116">See Also</span></span>  
 [<span data-ttu-id="84d59-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="84d59-117">Exceptions</span></span>](../core/exceptions.md)