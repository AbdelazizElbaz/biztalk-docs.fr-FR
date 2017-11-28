---
title: "Comment ajouter un Block5 d’Exception Catch | Documents Microsoft"
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
ms.assetid: 4875060c-976c-40e7-830a-ffd1a47ba68a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c045677fb2d177377725a3f11e81a5c5c70f9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="fc86b-102">Ajout d'un bloc Intercepter l'exception</span><span class="sxs-lookup"><span data-stu-id="fc86b-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="fc86b-103">Pour ajouter un **intercepter l’Exception** bloquer à un **étendue** mettre en forme le **Type de Transaction** propriété de la **étendue** forme doit être définie sur **Aucun** ou **longue**.</span><span class="sxs-lookup"><span data-stu-id="fc86b-103">To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-a-catch-exception-block"></a><span data-ttu-id="fc86b-104">Pour ajouter un bloc intercepter l’exception</span><span class="sxs-lookup"><span data-stu-id="fc86b-104">To add a catch exception block</span></span>  
  
1.  <span data-ttu-id="fc86b-105">Cliquez sur le **étendue** mettre en forme, puis cliquez sur **nouveau gestionnaire d’exceptions**.</span><span class="sxs-lookup"><span data-stu-id="fc86b-105">Right-click the **Scope** shape, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="fc86b-106">A **intercepter l’Exception** bloc est ajouté à l’orchestration qui suit immédiatement la **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="fc86b-106">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="fc86b-107">Dans le **propriétés** fenêtre, spécifiez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="fc86b-107">In the **Properties** window, specify the properties.</span></span>  
  
     <span data-ttu-id="fc86b-108">La propriété la plus importante est la **Type d’objet Exception**; il s’agit du type de message, elle intercepte.</span><span class="sxs-lookup"><span data-stu-id="fc86b-108">The most important property is the **Exception Object Type**; this is the type of message it will catch.</span></span>  
  
    |<span data-ttu-id="fc86b-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="fc86b-109">Property</span></span>|<span data-ttu-id="fc86b-110"> Description</span><span class="sxs-lookup"><span data-stu-id="fc86b-110">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="fc86b-111">**Nom de l’objet exception**</span><span class="sxs-lookup"><span data-stu-id="fc86b-111">**Exception Object Name**</span></span>|<span data-ttu-id="fc86b-112">Affecte un nom à l'objet d'exception intercepté par le gestionnaire d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="fc86b-112">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="fc86b-113">**Type d’objet exception**</span><span class="sxs-lookup"><span data-stu-id="fc86b-113">**Exception Object Type**</span></span>|<span data-ttu-id="fc86b-114">Détermine le type d'objet (issu de la classe System.Exception) que ce gestionnaire interceptera.</span><span class="sxs-lookup"><span data-stu-id="fc86b-114">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="fc86b-115">Dans le **propriétés** fenêtre, dans le **Type d’objet Exception** liste, sélectionnez **Exception générale**.</span><span class="sxs-lookup"><span data-stu-id="fc86b-115">In the **Properties** window, in the **Exception Object Type** list, select **General Exception**.</span></span>  
  
4.  <span data-ttu-id="fc86b-116">À l’intérieur de la **intercepter l’Exception** bloquer, ajouter des formes pour créer le processus de gestion de l’exception.</span><span class="sxs-lookup"><span data-stu-id="fc86b-116">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
    1.  <span data-ttu-id="fc86b-117">Avec le bouton ci-dessous le **CatchException** et pointez sur **insérer une forme**, puis sélectionnez **construire un Message**.</span><span class="sxs-lookup"><span data-stu-id="fc86b-117">Right-click below the **CatchException** and point to **Insert Shape**, and then select **Construct Message**.</span></span>  
  
    2.  <span data-ttu-id="fc86b-118">Double-cliquez dans **MessageAssignment** pour ouvrir l’éditeur de texte et entrez l’assignation du Message.</span><span class="sxs-lookup"><span data-stu-id="fc86b-118">Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.</span></span>  
  
         <span data-ttu-id="fc86b-119">Par exemple, tapez `Message_3 = Test`.</span><span class="sxs-lookup"><span data-stu-id="fc86b-119">For example, type `Message_3 = Test`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc86b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc86b-120">See Also</span></span>  
 <span data-ttu-id="fc86b-121">[Exécution du Message d’Exception](../core/completing-the-exception-message1.md) </span><span class="sxs-lookup"><span data-stu-id="fc86b-121">[Completing the Exception Message](../core/completing-the-exception-message1.md) </span></span>  
 <span data-ttu-id="fc86b-122">[Comment ajouter une forme étendue](../core/how-to-add-a-scope-shape5.md) </span><span class="sxs-lookup"><span data-stu-id="fc86b-122">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape5.md) </span></span>  
 [<span data-ttu-id="fc86b-123">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="fc86b-123">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling5.md)