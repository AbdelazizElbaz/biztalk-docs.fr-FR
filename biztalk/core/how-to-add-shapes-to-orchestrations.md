---
title: Comment ajouter des formes aux Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes, orchestrations
- orchestrations, shapes
- Construct Message shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Scope shape [Orchestration Designer]
ms.assetid: d39eb12c-cdc6-4918-93d9-536db1dfb889
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9fa6634adb20ffcf927da0af6f58e9daa2800ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-shapes-to-orchestrations"></a><span data-ttu-id="fc808-102">Comment ajouter des formes aux Orchestrations</span><span class="sxs-lookup"><span data-stu-id="fc808-102">How to Add Shapes to Orchestrations</span></span>
<span data-ttu-id="fc808-103">Cette section décrit les procédures d'ajout et de suppression de formes dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="fc808-103">This section describes the procedures for adding and removing shapes in your orchestration.</span></span> <span data-ttu-id="fc808-104">Pour plus d’informations sur les formes disponibles, consultez [formes d’Orchestration](../core/orchestration-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="fc808-104">For more information about the available shapes, see [Orchestration Shapes](../core/orchestration-shapes.md).</span></span>  
  
### <a name="to-add-a-shape-to-an-orchestration"></a><span data-ttu-id="fc808-105">Pour ajouter une forme à une orchestration</span><span class="sxs-lookup"><span data-stu-id="fc808-105">To add a shape to an orchestration</span></span>  
  
1.  <span data-ttu-id="fc808-106">Dans la boîte à outils, sur le **Orchestrations BizTalk** onglet, faites glisser la forme vers une ligne de connexion sur l’aire de conception d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="fc808-106">In the Toolbox, on the **BizTalk Orchestrations** tab, drag the shape onto a connecting line on the Orchestration Design Surface.</span></span>  
  
     <span data-ttu-id="fc808-107">— Ou :</span><span class="sxs-lookup"><span data-stu-id="fc808-107">—Or—</span></span>  
  
2.  <span data-ttu-id="fc808-108">Avec le bouton droit de la ligne de connexion ou l’espace réservé où vous souhaitez ajouter la forme, pointez sur **insérer une forme**, puis cliquez sur le nom de la forme à ajouter.</span><span class="sxs-lookup"><span data-stu-id="fc808-108">Right-click the connecting line or the shape placeholder where you want to add the shape, point to **Insert Shape**, and then click the shape name you want to add.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc808-109">Une balise active apparaît sur les formes dont la configuration n'est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="fc808-109">A Smart Tag appears on shapes that are not yet fully configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc808-110">**Transformer** formes et **assignation du Message** ne peuvent exister dans un **construire un Message** forme.</span><span class="sxs-lookup"><span data-stu-id="fc808-110">**Transform** shapes and **Message Assignment** shapes can only exist within a **Construct Message** shape.</span></span> <span data-ttu-id="fc808-111">Si vous ajoutez une de ces formes à votre orchestration en dehors d’un **construire un Message** forme, il est placé automatiquement dans une nouvelle **construire un Message** forme.</span><span class="sxs-lookup"><span data-stu-id="fc808-111">If you add one of these shapes to your orchestration outside of a **Construct Message** shape, it is placed automatically inside a new **Construct Message** shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc808-112">**Intercepter Exception** et **Compensation** blocs peuvent exister uniquement après un **étendue** forme.</span><span class="sxs-lookup"><span data-stu-id="fc808-112">**Catch Exception** and **Compensation** blocks can only exist following a **Scope** shape.</span></span>  
  
### <a name="to-remove-a-shape-from-an-orchestration"></a><span data-ttu-id="fc808-113">Pour supprimer une forme d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="fc808-113">To remove a shape from an orchestration</span></span>  
  
1.  <span data-ttu-id="fc808-114">Avec le bouton droit de la forme sur l’aire de conception, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="fc808-114">Right-click the shape on the design surface, and then click **Delete**.</span></span>  
  
     <span data-ttu-id="fc808-115">— Ou :</span><span class="sxs-lookup"><span data-stu-id="fc808-115">—Or—</span></span>  
  
2.  <span data-ttu-id="fc808-116">Sélectionnez la forme et appuyez sur la **supprimer** clé.</span><span class="sxs-lookup"><span data-stu-id="fc808-116">Select the shape and press the **DELETE** key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc808-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc808-117">See Also</span></span>  
 [<span data-ttu-id="fc808-118">Création d’Orchestrations</span><span class="sxs-lookup"><span data-stu-id="fc808-118">Creating Orchestrations</span></span>](../core/creating-orchestrations.md)