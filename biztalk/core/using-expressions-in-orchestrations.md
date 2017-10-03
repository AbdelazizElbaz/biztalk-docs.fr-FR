---
title: "Utilisation d’Expressions dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1947cd39-6ef2-4b2d-afeb-a0132b19db97
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 880e1ee08a232aca3a04763c5d5c1797fd238fbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-expressions-in-orchestrations"></a><span data-ttu-id="59c01-102">Utilisation d'expressions dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="59c01-102">Using Expressions in Orchestrations</span></span>
<span data-ttu-id="59c01-103">Vous pouvez utiliser l'Éditeur d'expression BizTalk pour entrer des expressions XLANG/s et ajouter une logique afin de manipuler et de tester les valeurs des variables et messages de votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="59c01-103">You can use BizTalk Expression Editor to enter XLANG/s expressions to add logic to manipulate and test the values of your orchestration variables and messages.</span></span> <span data-ttu-id="59c01-104">Cependant, il est généralement déconseillé de l'utiliser pour exécuter une logique d'orchestration de niveau supérieur, qu'il serait préférable de voir dans le dessin de l'orchestration lui-même.</span><span class="sxs-lookup"><span data-stu-id="59c01-104">However, it is not a good practice to use it to perform high-level orchestration logic, which preferably would be visible in the orchestration drawing itself.</span></span> <span data-ttu-id="59c01-105">Pour la transparence et la reconfiguration simple de votre processus d'entreprise, il est recommandé d'utiliser des expressions simples et modulables.</span><span class="sxs-lookup"><span data-stu-id="59c01-105">For business process transparency and easy of reconfiguration, we recommend that you use simple and modular expressions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59c01-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="59c01-106">In This Section</span></span>  
 [<span data-ttu-id="59c01-107">Configuration requise et Limitations pour les Expressions</span><span class="sxs-lookup"><span data-stu-id="59c01-107">Requirements and Limitations for Expressions</span></span>](../core/requirements-and-limitations-for-expressions.md)  
  
 [<span data-ttu-id="59c01-108">Formes qui prennent des Expressions</span><span class="sxs-lookup"><span data-stu-id="59c01-108">Shapes that Take Expressions</span></span>](../core/shapes-that-take-expressions.md)  
  
 [<span data-ttu-id="59c01-109">Comment créer des Expressions</span><span class="sxs-lookup"><span data-stu-id="59c01-109">How to Create Expressions</span></span>](../core/how-to-create-expressions.md)  
  
 [<span data-ttu-id="59c01-110">Utilisation d’opérateurs dans des Expressions</span><span class="sxs-lookup"><span data-stu-id="59c01-110">Using Operators in Expressions</span></span>](../core/using-operators-in-expressions.md)  
  
 [<span data-ttu-id="59c01-111">Comment utiliser des Expressions pour effectuer l’assignation de Message</span><span class="sxs-lookup"><span data-stu-id="59c01-111">How to Use Expressions to Perform Message Assignments</span></span>](../core/how-to-use-expressions-to-perform-message-assignments.md)  
  
 [<span data-ttu-id="59c01-112">Comment utiliser des Expressions pour transformer dynamiquement des Messages</span><span class="sxs-lookup"><span data-stu-id="59c01-112">How to Use Expressions to Dynamic Transform Messages</span></span>](../core/how-to-use-expressions-to-dynamic-transform-messages.md)  
  
 [<span data-ttu-id="59c01-113">Comment utiliser des Expressions pour exécuter des Pipelines</span><span class="sxs-lookup"><span data-stu-id="59c01-113">How to Use Expressions to Execute Pipelines</span></span>](../core/how-to-use-expressions-to-execute-pipelines.md)  
  
 [<span data-ttu-id="59c01-114">Comment utiliser des Expressions pour créer des objets et appeler les méthodes d’objet</span><span class="sxs-lookup"><span data-stu-id="59c01-114">How to Use Expressions to Create Objects and Call Object Methods</span></span>](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md)  
  
 [<span data-ttu-id="59c01-115">Comment utiliser des Expressions pour affecter des valeurs à des Ports dynamiques</span><span class="sxs-lookup"><span data-stu-id="59c01-115">How to Use Expressions to Assign Values to Dynamic Ports</span></span>](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)  
  
## <a name="see-also"></a><span data-ttu-id="59c01-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59c01-116">See Also</span></span>  
 <span data-ttu-id="59c01-117">[Langage XLANG-s](../core/xlang-s-language.md) </span><span class="sxs-lookup"><span data-stu-id="59c01-117">[XLANG-s Language](../core/xlang-s-language.md) </span></span>  
 <span data-ttu-id="59c01-118">[À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="59c01-118">[Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="59c01-119">Utilisation de Variables dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="59c01-119">Using Variables in Orchestrations</span></span>](../core/using-variables-in-orchestrations.md)