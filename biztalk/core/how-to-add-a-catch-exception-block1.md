---
title: "Comment ajouter un SMB1 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding Catch Exception block
- Catch Exception blocks, adding
- exception handling, Catch Exception blocks
ms.assetid: 8e4b264b-b3b0-4d83-81df-a14dc2ddeea2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7922a1527e0f6359427be992c4cc9963f8c7d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="b0af0-102">Ajout d'un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="b0af0-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="b0af0-103">Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="b0af0-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="b0af0-104">**Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="b0af0-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="b0af0-105">Vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="b0af0-105">You can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="b0af0-106">Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="b0af0-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="b0af0-107">Sur chaque gestionnaire d'exceptions, vous devez indiquer le type d'exception, qui est une exception ou un objet provenant de la classe `System`.</span><span class="sxs-lookup"><span data-stu-id="b0af0-107">On each exception handler, you specify an exception type, which must be either an exception or an object derived from the class `System`.</span></span> <span data-ttu-id="b0af0-108">Si une exception est levée qui correspond au type spécifié dans un gestionnaire d’exceptions, ce gestionnaire d’exceptions sera appelé.</span><span class="sxs-lookup"><span data-stu-id="b0af0-108">If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0af0-109">Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme, la propriété Type de Transaction de la **étendue** forme doit être définie sur **aucun** ou  **Long terme**.</span><span class="sxs-lookup"><span data-stu-id="b0af0-109">To add a **Catch Exception** block to a **Scope** shape, the Transaction Type property of the **Scope** shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a><span data-ttu-id="b0af0-110">Pour ajouter et remplir un bloc intercepter l’Exception</span><span class="sxs-lookup"><span data-stu-id="b0af0-110">To add and populate a Catch Exception block</span></span>  
  
1.  <span data-ttu-id="b0af0-111">Avec le bouton droit le **étendue** forme à laquelle vous souhaitez ajouter un **intercepter l’Exception** bloquer, puis cliquez sur **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="b0af0-111">Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="b0af0-112">A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="b0af0-112">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="b0af0-113">Dans le **propriétés** fenêtre, spécifiez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b0af0-113">In the **Properties** window, specify the properties.</span></span>  
  
     <span data-ttu-id="b0af0-114">La plus importante des propriétés est Type d'objet d'exception ; il s'agit du type de message à intercepter.</span><span class="sxs-lookup"><span data-stu-id="b0af0-114">The most important property is the Exception Object Type; this is the type of message it will catch.</span></span>  
  
    |<span data-ttu-id="b0af0-115">Propriété</span><span class="sxs-lookup"><span data-stu-id="b0af0-115">Property</span></span>|<span data-ttu-id="b0af0-116"> Description</span><span class="sxs-lookup"><span data-stu-id="b0af0-116">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="b0af0-117">Nom d'objet d'exception</span><span class="sxs-lookup"><span data-stu-id="b0af0-117">Exception Object Name</span></span>|<span data-ttu-id="b0af0-118">Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="b0af0-118">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="b0af0-119">Type d'objet d'exception</span><span class="sxs-lookup"><span data-stu-id="b0af0-119">Exception Object Type</span></span>|<span data-ttu-id="b0af0-120">Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.</span><span class="sxs-lookup"><span data-stu-id="b0af0-120">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="b0af0-121">Dans le **propriétés** fenêtre, dans le **Type d’objet Exception** liste, sélectionnez le **Exception générale**.</span><span class="sxs-lookup"><span data-stu-id="b0af0-121">In the **Properties** window, in the **Exception Object Type** list, select the **General Exception**.</span></span>  
  
4.  <span data-ttu-id="b0af0-122">À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.</span><span class="sxs-lookup"><span data-stu-id="b0af0-122">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
5.  <span data-ttu-id="b0af0-123">Avec le bouton ci-dessous le **intercepter l’Exception** bloquer, pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.</span><span class="sxs-lookup"><span data-stu-id="b0af0-123">Right-click below the **Catch Exception** block, point to **Insert Shape**, and then select **Construct Message**.</span></span>  
  
6.  <span data-ttu-id="b0af0-124">Double-cliquez dans **MessageAssignment** pour activer l’éditeur de texte et entrez l’assignation du Message.</span><span class="sxs-lookup"><span data-stu-id="b0af0-124">Double-click inside **MessageAssignment** to activate the Text Editor and enter the Message assignment.</span></span>  
  
     <span data-ttu-id="b0af0-125">Par exemple, tapez `Message_3 = Test`.</span><span class="sxs-lookup"><span data-stu-id="b0af0-125">For example, type `Message_3 = Test`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0af0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0af0-126">See Also</span></span>  
 <span data-ttu-id="b0af0-127">[Exécution du Message d’Exception](../core/completing-the-exception-message5.md) </span><span class="sxs-lookup"><span data-stu-id="b0af0-127">[Completing the Exception Message](../core/completing-the-exception-message5.md) </span></span>  
 <span data-ttu-id="b0af0-128">[Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape2.md) </span><span class="sxs-lookup"><span data-stu-id="b0af0-128">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape2.md) </span></span>  
 [<span data-ttu-id="b0af0-129">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b0af0-129">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling3.md)