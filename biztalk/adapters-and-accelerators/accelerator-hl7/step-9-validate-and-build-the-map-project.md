---
title: "Étape 9 : Valider et générez le projet de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, maps
- message enrichment tutorial, maps
- maps, building
- maps, validating
ms.assetid: 10716b0b-702c-48bb-85a9-d58d8f33b68b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1eb4580a9c89534204e492aebdd21988a6ce0e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-validate-and-build-the-map-project"></a><span data-ttu-id="88ade-102">Étape 9 : Valider et générez le projet de carte</span><span class="sxs-lookup"><span data-stu-id="88ade-102">Step 9: Validate and Build the Map Project</span></span>
<span data-ttu-id="88ade-103">Dans cette étape, vous utilisez la **valider le mappage** commande afin de déterminer si le mappage contient des incohérences internes ou autres problèmes qui empêcheraient d’utilisé de manière efficace pour les schémas de mappage.</span><span class="sxs-lookup"><span data-stu-id="88ade-103">In this step, you use the **Validate Map** command to determine if the map contains any internal inconsistencies, or has other issues that would prevent it from being used effectively for mapping schemas.</span></span> <span data-ttu-id="88ade-104">Aussi, vous générez le projet pour générer un assembly qui contient les ressources (schémas et le mappage) que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="88ade-104">You also build the project to generate an assembly that contains the resources (schemas and the map) that you created.</span></span> <span data-ttu-id="88ade-105">Cela garantit également qu’il n’y a aucune erreur de compilation dans le travail qui ont été effectuées jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="88ade-105">This also ensures that there are no compile errors in the work that you have completed so far.</span></span>  
  
### <a name="to-validate-the-map-project"></a><span data-ttu-id="88ade-106">Pour valider le plan de projet</span><span class="sxs-lookup"><span data-stu-id="88ade-106">To validate the map project</span></span>  
  
1.  <span data-ttu-id="88ade-107">Dans l’Explorateur de solutions, cliquez sur le **DoorbellMap.btm** mapper, puis cliquez sur **valider le mappage**.</span><span class="sxs-lookup"><span data-stu-id="88ade-107">In Solution Explorer, right-click the **DoorbellMap.btm** map, and then click **Validate Map**.</span></span>  
  
2.  <span data-ttu-id="88ade-108">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="88ade-108">Ensure that a success message appears in the output window.</span></span> <span data-ttu-id="88ade-109">Des avertissements peuvent apparaître, car vous ne mappez pas à tous les éléments disponibles dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="88ade-109">Some warnings may appear because you are not mapping to all available elements in the destination schema.</span></span>  
  
     <span data-ttu-id="88ade-110">Si aucun message de réussite s’affiche, résolvez les problèmes du projet de la carte.</span><span class="sxs-lookup"><span data-stu-id="88ade-110">If no success message appears, troubleshoot the map project.</span></span>  
  
### <a name="to-build-the-map-project"></a><span data-ttu-id="88ade-111">Pour générer le projet de carte</span><span class="sxs-lookup"><span data-stu-id="88ade-111">To build the map project</span></span>  
  
-   <span data-ttu-id="88ade-112">Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="88ade-112">In Solution Explorer, right-click **BTAHL7 Project**, and then click **Build**.</span></span> <span data-ttu-id="88ade-113">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="88ade-113">Ensure that a success message appears in the output window.</span></span>  
  
     <span data-ttu-id="88ade-114">Si aucun message de réussite s’affiche, résolvez les problèmes du projet de la carte.</span><span class="sxs-lookup"><span data-stu-id="88ade-114">If no success message appears, troubleshoot the map project.</span></span>  
  
 <span data-ttu-id="88ade-115">Passez à [étape 10 : créer une Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="88ade-115">Proceed to [Step 10: Create an Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ade-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88ade-116">See Also</span></span>  
 [<span data-ttu-id="88ade-117">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="88ade-117">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)