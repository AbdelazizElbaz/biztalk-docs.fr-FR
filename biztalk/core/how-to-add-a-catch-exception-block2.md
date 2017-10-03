---
title: "Comment ajouter un Block2 d’Exception Catch | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Catch Exception blocks
- exceptions, Catch Exception blocks
ms.assetid: 7c8b6024-e8dc-4417-83f9-bf4032644b91
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e48ce1e6f0646acdf63ed33582f382f1baed797
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="edbf8-102">Ajout d'un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="edbf8-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="edbf8-103">Le **intercepter l’Exception** bloc représente un gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="edbf8-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="edbf8-104">**Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="edbf8-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="edbf8-105">Vous pouvez joindre autant **intercepter l’Exception** bloque dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="edbf8-105">You can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="edbf8-106">Vous pouvez configurer les gestionnaires d'exceptions afin qu'ils gèrent différents types d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="edbf8-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="edbf8-107">Vous devez spécifier un type d'exception sur chaque gestionnaire d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="edbf8-107">On each exception handler, you specify an exception type.</span></span> <span data-ttu-id="edbf8-108">Il peut s'agir d'une exception ou d'un objet dérivé de la classe `System`.</span><span class="sxs-lookup"><span data-stu-id="edbf8-108">This must be either an exception or an object derived from the class `System`.</span></span> <span data-ttu-id="edbf8-109">Si une exception est levée qui correspond au type spécifié dans un gestionnaire d’exceptions, ce gestionnaire d’exceptions sera appelé.</span><span class="sxs-lookup"><span data-stu-id="edbf8-109">If an exception is thrown that matches the specified type in an exception handler, that exception handler will be called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edbf8-110">Pour ajouter un bloc intercepter l’Exception à une forme étendue, la propriété de Type de Transaction de la forme étendue doit être définie **aucun** ou **Long terme**.</span><span class="sxs-lookup"><span data-stu-id="edbf8-110">To add a Catch Exception block to a Scope shape, the Transaction Type property of the Scope shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-and-populate-a-catch-exception-block"></a><span data-ttu-id="edbf8-111">Pour ajouter et remplir un bloc intercepter l’Exception</span><span class="sxs-lookup"><span data-stu-id="edbf8-111">To add and populate a Catch Exception block</span></span>  
  
1.  <span data-ttu-id="edbf8-112">Avec le bouton droit le **étendue** forme à laquelle vous souhaitez ajouter un **intercepter l’Exception** bloquer, puis cliquez sur **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="edbf8-112">Right-click the **Scope** shape to which you want to add a **Catch Exception** block, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="edbf8-113">A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="edbf8-113">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="edbf8-114">Dans le **propriétés** fenêtre, spécifiez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="edbf8-114">In the **Properties** window, specify the properties.</span></span>  
  
     <span data-ttu-id="edbf8-115">La propriété la plus importante est la **Type d’objet Exception**; il s’agit du type de message, elle intercepte.</span><span class="sxs-lookup"><span data-stu-id="edbf8-115">The most important property is the **Exception Object Type**; this is the type of message it will catch.</span></span>  
  
3.  <span data-ttu-id="edbf8-116">Dans le **propriétés** windows, dans le **Type d’objet Exception** liste, sélectionnez **Exception générale**.</span><span class="sxs-lookup"><span data-stu-id="edbf8-116">In the **Properties** windows, in the **Exception Object Type** list, select  **General Exception**.</span></span>  
  
    |<span data-ttu-id="edbf8-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="edbf8-117">Property</span></span>|<span data-ttu-id="edbf8-118"> Description</span><span class="sxs-lookup"><span data-stu-id="edbf8-118">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="edbf8-119">**Nom de l’objet exception**</span><span class="sxs-lookup"><span data-stu-id="edbf8-119">**Exception Object Name**</span></span>|<span data-ttu-id="edbf8-120">Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="edbf8-120">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="edbf8-121">**Type d’objet exception**</span><span class="sxs-lookup"><span data-stu-id="edbf8-121">**Exception Object Type**</span></span>|<span data-ttu-id="edbf8-122">Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.</span><span class="sxs-lookup"><span data-stu-id="edbf8-122">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
4.  <span data-ttu-id="edbf8-123">Dans le bloc Intercepter l'exception, ajoutez des formes afin de créer la procédure de gestion de l'exception.</span><span class="sxs-lookup"><span data-stu-id="edbf8-123">Inside the Catch Exception block, add shapes to create the process for handling the exception.</span></span>  
  
    1.  <span data-ttu-id="edbf8-124">Avec le bouton ci-dessous le **CatchException** et pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.</span><span class="sxs-lookup"><span data-stu-id="edbf8-124">Right-click below the **CatchException** and point to **Insert Shape**, and then select **Construct Message**.</span></span>  
  
    2.  <span data-ttu-id="edbf8-125">Double-cliquez dans **MessageAssignment** pour ouvrir l’éditeur de texte et entrez l’assignation du Message.</span><span class="sxs-lookup"><span data-stu-id="edbf8-125">Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.</span></span>  
  
         <span data-ttu-id="edbf8-126">Par exemple, tapez `Message_3 = Test`.</span><span class="sxs-lookup"><span data-stu-id="edbf8-126">For example, type `Message_3 = Test`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbf8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edbf8-127">See Also</span></span>  
 <span data-ttu-id="edbf8-128">[Exécution du Message d’Exception](../core/completing-the-exception-message4.md) </span><span class="sxs-lookup"><span data-stu-id="edbf8-128">[Completing the Exception Message](../core/completing-the-exception-message4.md) </span></span>  
 <span data-ttu-id="edbf8-129">[Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape4.md) </span><span class="sxs-lookup"><span data-stu-id="edbf8-129">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape4.md) </span></span>  
 [<span data-ttu-id="edbf8-130">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="edbf8-130">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling4.md)