---
title: "Comment ajouter un Block6 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exception handling, Catch Exception block
- Catch Exception blocks
- exceptions, Catch Exception block
ms.assetid: 404312dd-773b-44fe-8b65-7de3d0af2f79
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4be60ddbe45ef4b4f293d7959dc774254e7cd3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="e8ae8-102">Ajout d'un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="e8ae8-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="e8ae8-103">Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="e8ae8-104">**Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="e8ae8-105">Dans BizTalk Server, vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-105">In BizTalk Server, you can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="e8ae8-106">Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="e8ae8-107">Sur chaque gestionnaire d'exceptions, vous devez indiquer le type d'exception, qui est un message d'erreur ou un objet provenant de la classe `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-107">On each exception handler, you specify an exception type, which must be either a fault message or an object derived from the class `System.Exception`.</span></span> <span data-ttu-id="e8ae8-108">Si vous ne précisez pas le type d'erreur, le bloc d'exception est alors traité comme un gestionnaire d'exceptions général et pourra intercepter des exceptions qui ne proviennent pas de la classe `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-108">If you do not specify an exception type, the exception block is treated as a general exception handler, and can catch exceptions that do not derive from `System.Exception`.</span></span>  
  
 <span data-ttu-id="e8ae8-109">Lorsqu'une exception générée correspond au type spécifié, le gestionnaire d'exceptions approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-109">If an exception is thrown that matches the specified type in an exception handler, that exception handler is called.</span></span> <span data-ttu-id="e8ae8-110">Si une autre exception est levée, elle est gérée par le Gestionnaire d’exceptions par défaut.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-110">If some other exception is thrown, it is handled by the default exception handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8ae8-111">Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur None ou Long En cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-111">To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to None or Long Running.</span></span>  
  
## <a name="adding-and-populating-a-catch-exception-block"></a><span data-ttu-id="e8ae8-112">Ajout et renseignement d'un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="e8ae8-112">Adding and Populating a Catch Exception Block</span></span>  
  
#### <a name="to-add-and-populate-a-catch-exception-block"></a><span data-ttu-id="e8ae8-113">Pour ajouter et renseigner un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="e8ae8-113">To add and populate a catch exception block</span></span>  
  
1.  <span data-ttu-id="e8ae8-114">Avec le bouton droit le **étendue** forme que vous souhaitez ajouter un **intercepter l’Exception** bloquer à, puis cliquez sur **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-114">Right-click the **Scope** shape that you want to add a **Catch Exception** block to, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="e8ae8-115">A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-115">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="e8ae8-116">Dans le **propriétés** fenêtre, spécifiez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-116">In the **Properties** window, specify the properties.</span></span> <span data-ttu-id="e8ae8-117">La propriété la plus importante est la **Type d’objet Exception** , car il s’agit du type de message, elle intercepte.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-117">The most important property is the **Exception Object Type** because this is the type of message it will catch.</span></span>  
  
    |<span data-ttu-id="e8ae8-118">Propriété</span><span class="sxs-lookup"><span data-stu-id="e8ae8-118">Property</span></span>|<span data-ttu-id="e8ae8-119"> Description</span><span class="sxs-lookup"><span data-stu-id="e8ae8-119">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="e8ae8-120">Nom d'objet d'exception</span><span class="sxs-lookup"><span data-stu-id="e8ae8-120">Exception Object Name</span></span>|<span data-ttu-id="e8ae8-121">Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-121">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="e8ae8-122">Type d'objet d'exception</span><span class="sxs-lookup"><span data-stu-id="e8ae8-122">Exception Object Type</span></span>|<span data-ttu-id="e8ae8-123">Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-123">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="e8ae8-124">Dans le **propriétés** fenêtre, cliquez sur le **Type d’objet Exception** liste.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-124">In the **Properties** window, click the **Exception Object Type** list.</span></span> <span data-ttu-id="e8ae8-125">Cette liste contient l'exception générale qui est générée par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-125">This list contains the general exception that is thrown by the adapter.</span></span>  
  
     <span data-ttu-id="e8ae8-126">Le nom apparaît comme l'erreur que vous définissez dans le port vers le système principal (par exemple, PS.SQLExecute.Fault).</span><span class="sxs-lookup"><span data-stu-id="e8ae8-126">The name appears as the fault you set in the port to the back-end system, for example, PS.SQLExecute.Fault.</span></span>  
  
4.  <span data-ttu-id="e8ae8-127">Ajouter un nom pour le **nom de l’objet Exception**, par exemple, de Test.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-127">Add a name for the **Exception Object Name**, for example, Test.</span></span>  
  
     <span data-ttu-id="e8ae8-128">À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-128">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
    1.  <span data-ttu-id="e8ae8-129">Avec le bouton ci-dessous le **intercepter l’Exception**, pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-129">Right-click below the **Catch Exception**, point to **Insert Shape**, and select **Construct Message**.</span></span>  
  
         ![](../core/media/siebeladapter-20-exceptionhandling-constructmessage.gif "SiebelAdapter_20_ExceptionHandling_ConstructMessage")  
  
    2.  <span data-ttu-id="e8ae8-130">Double-cliquez dans **MessageAssignment** pour ouvrir l’éditeur de texte et entrez l’assignation du Message.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-130">Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.</span></span>  
  
         <span data-ttu-id="e8ae8-131">Entrez le nom que vous définissez dans le **nom de l’objet Exception** à partir de la **intercepter l’Exception**et le nouveau message que vous avez créé pour l’erreur.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-131">Enter the name that you set in the **Exception Object Name** from the **Catch Exception**, and the new message you created for the fault.</span></span>  
  
         <span data-ttu-id="e8ae8-132">Par exemple, tapez `Message_3 = Test`.</span><span class="sxs-lookup"><span data-stu-id="e8ae8-132">For example, type `Message_3 = Test`.</span></span>  
  
         ![](../core/media/siebeladapter-21-exceptionhandling-message3test.gif "SiebelAdapter_21_ExceptionHandling_Message3Test")  
  
## <a name="see-also"></a><span data-ttu-id="e8ae8-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8ae8-133">See Also</span></span>  
 <span data-ttu-id="e8ae8-134">[Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape1.md) </span><span class="sxs-lookup"><span data-stu-id="e8ae8-134">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape1.md) </span></span>  
 <span data-ttu-id="e8ae8-135">[Exécution du Message d’Exception](../core/completing-the-exception-message3.md) </span><span class="sxs-lookup"><span data-stu-id="e8ae8-135">[Completing the Exception Message](../core/completing-the-exception-message3.md) </span></span>  
 [<span data-ttu-id="e8ae8-136">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e8ae8-136">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling2.md)