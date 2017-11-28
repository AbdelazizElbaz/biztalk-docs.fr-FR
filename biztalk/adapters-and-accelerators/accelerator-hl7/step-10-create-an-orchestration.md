---
title: "Étape 10 : Créer une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, creating
- creating, orchestrations
- message enrichment tutorial, orchestrations
ms.assetid: 10f5cf3d-4a34-4c80-89d1-c390552cfc09
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfc554a6f3c94a077b34ae79a36b8e484eadcd5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-10-create-an-orchestration"></a><span data-ttu-id="8d699-102">Étape 10 : Créer une Orchestration</span><span class="sxs-lookup"><span data-stu-id="8d699-102">Step 10: Create an Orchestration</span></span>
<span data-ttu-id="8d699-103">Dans cette étape, vous utilisez le Concepteur d’Orchestration pour créer une orchestration pour représenter le processus d’entreprise pour la récupération des détails des patients supplémentaires pour remplir entièrement un message ADT_A04.</span><span class="sxs-lookup"><span data-stu-id="8d699-103">In this step, you use Orchestration Designer to create an orchestration to represent the business process for retrieving additional patient details to fully populate an ADT_A04 message.</span></span> <span data-ttu-id="8d699-104">À l’aide du Concepteur d’Orchestration, sélectionnez les formes orchestration nécessaires pour représenter les actions pour ce processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="8d699-104">Using Orchestration Designer, you select the orchestration shapes required to represent actions for this business process.</span></span> <span data-ttu-id="8d699-105">Dans les exercices ultérieure, vous fournissez des informations supplémentaires pour configurer les formes afin qu’ils puissent fonctionner.</span><span class="sxs-lookup"><span data-stu-id="8d699-105">In later exercises, you provide additional information to configure the shapes so that they can function properly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d699-106">L’orchestration créée dans la procédure suivante fonctionne uniquement dans le contexte de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="8d699-106">The orchestration created in the following steps only works in the context of this tutorial.</span></span> <span data-ttu-id="8d699-107">Pour l’orchestration fonctionne correctement, il doit les références d’assembly, mappages et les autres artefacts que vous créez lors de l’utilisation de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="8d699-107">In order for the orchestration to work correctly, it needs the assembly references, maps, and the other artifacts that you create while using this tutorial.</span></span>  
  
### <a name="to-create-an-orchestration"></a><span data-ttu-id="8d699-108">Pour créer une orchestration</span><span class="sxs-lookup"><span data-stu-id="8d699-108">To create an orchestration</span></span>  
  
1.  <span data-ttu-id="8d699-109">Dans l’Explorateur de solutions, cliquez sur **BTAHL7 projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8d699-109">In Solution Explorer, right-click **BTAHL7 Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="8d699-110">Dans le **ajouter un nouvel élément** boîte de dialogue le **catégories** volet, cliquez sur **fichiers d’Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="8d699-110">In the **Add New Item** dialog box, in the **Categories** pane, click **Orchestration Files**.</span></span>  
  
3.  <span data-ttu-id="8d699-111">Dans le **modèles** volet, cliquez sur **Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="8d699-111">In the **Templates** pane, click **BizTalk Orchestration**.</span></span>  
  
4.  <span data-ttu-id="8d699-112">Dans le **nom** , tapez **sonnette Orchestration.odx** (Notez qu’il y a un espace entre le mot **sonnette** et **Orchestration** ) comme le nom de l’orchestration, puis cliquez sur **ajouter** pour créer un nouveau fichier d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8d699-112">In the **Name** field, type **Doorbell Orchestration.odx** (note that there is a space between the word **Doorbell** and **Orchestration**) as the orchestration name, and then click **Add** to create a new orchestration file.</span></span>  
  
5.  <span data-ttu-id="8d699-113">Dans le **vue** menu, cliquez sur **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="8d699-113">In the **View** menu, click **Toolbox**.</span></span>  
  
6.  <span data-ttu-id="8d699-114">Dans le **boîte à outils** volet, faites glisser le **réception** forme sur la surface en mode conception et déposez-la sur la zone de **déposez une forme à partir de la boîte à outils ici**.</span><span class="sxs-lookup"><span data-stu-id="8d699-114">In the **Toolbox** pane, drag the **Receive** shape to the Design view surface and drop it on the area labeled **Drop a shape from the toolbox here**.</span></span>  
  
7.  <span data-ttu-id="8d699-115">Dans la fenêtre Propriétés (en bas à droite de votre écran), cliquez sur le **nom** propriété et le type **DoorbellReceive** comme nom de la **réception** mettre en forme, puis appuyez sur  **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="8d699-115">In the Properties window (on the bottom right of your screen), click the **Name** property and type **DoorbellReceive** as the name of the **Receive** shape, and then press **Enter**.</span></span>  
  
8.  <span data-ttu-id="8d699-116">Dans la fenêtre Propriétés, modifiez la **activer** propriété **True**.</span><span class="sxs-lookup"><span data-stu-id="8d699-116">In the Properties window, change the **Activate** property to **True**.</span></span>  
  
9. <span data-ttu-id="8d699-117">Faites glisser le **transformer** mettre en forme à partir de la boîte à outils et déposez-le sous le **DoorbellReceive** forme.</span><span class="sxs-lookup"><span data-stu-id="8d699-117">Drag the **Transform** shape from the Toolbox and drop it directly below the **DoorbellReceive** shape.</span></span>  
  
10. <span data-ttu-id="8d699-118">Dans la fenêtre Propriétés (en bas à droite de votre écran), cliquez sur le **nom** propriété à modifier le nom de la **transformer** à mettre en forme **DoorbellTransform**, puis appuyez sur **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="8d699-118">In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Transform** shape to **DoorbellTransform**, and then press **Enter**.</span></span>  
  
11. <span data-ttu-id="8d699-119">Dans le **boîte à outils** volet, faites glisser le **assignation du Message** forme sur la surface en mode conception et déposez-la sur la zone sous la **ConstructMessage_1** forme.</span><span class="sxs-lookup"><span data-stu-id="8d699-119">In the **Toolbox** pane, drag the **Message Assignment** shape to the Design view surface and drop it on the area directly below the **ConstructMessage_1** shape.</span></span>  
  
12. <span data-ttu-id="8d699-120">Dans la surface en mode Design d’orchestration, cliquez sur le **MessageAssignment_1** forme, puis, dans le **propriétés** volet, cliquez sur **nom** et tapez le nouveau nom  **DoorbellFinalTransform**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="8d699-120">In the orchestration Design view surface, click the **MessageAssignment_1** shape, and in the **Properties** pane, click **Name** and type the new name **DoorbellFinalTransform**, and then press **Enter**.</span></span>  
  
13. <span data-ttu-id="8d699-121">Faites glisser le **envoyer** mettre en forme à partir de la boîte à outils et déposez-la sur la ligne de connexion directement sous la **DoorbellFinalTransform** forme.</span><span class="sxs-lookup"><span data-stu-id="8d699-121">Drag the **Send** shape from the Toolbox and drop it on the connecting line directly below the **DoorbellFinalTransform** shape.</span></span>  
  
14. <span data-ttu-id="8d699-122">Dans la fenêtre Propriétés (en bas à droite de votre écran), cliquez sur le **nom** propriété à modifier le nom de la **envoyer** à mettre en forme **DoorbellSend**, puis appuyez sur  **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="8d699-122">In the Properties window (on the bottom right of your screen), click the **Name** property to change the name of the **Send** shape to **DoorbellSend**, and then press **Enter**.</span></span>  
  
 <span data-ttu-id="8d699-123">Passez à [étape 11 : créer des Variables d’Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md).</span><span class="sxs-lookup"><span data-stu-id="8d699-123">Proceed to [Step 11: Create Orchestration Variables](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d699-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d699-124">See Also</span></span>  
 [<span data-ttu-id="8d699-125">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="8d699-125">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)