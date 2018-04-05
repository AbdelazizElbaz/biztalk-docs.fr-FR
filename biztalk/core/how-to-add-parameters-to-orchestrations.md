---
title: Comment ajouter des paramètres aux Orchestrations | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, parameters
ms.assetid: 35c731ed-6327-4de7-8d2e-4d14024bda77
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8328a97631efb2b8454e0a2679b257d35402cf4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-parameters-to-orchestrations"></a><span data-ttu-id="86598-102">Ajout de paramètres aux orchestrations</span><span class="sxs-lookup"><span data-stu-id="86598-102">How to Add Parameters to Orchestrations</span></span>
<span data-ttu-id="86598-103">Vous pouvez spécifier les paramètres de votre orchestration dans la fenêtre Vue Orchestration.</span><span class="sxs-lookup"><span data-stu-id="86598-103">You can specify what parameters your orchestration should take in the Orchestration View window.</span></span> <span data-ttu-id="86598-104">Une orchestration accepte les éléments suivants comme paramètres :</span><span class="sxs-lookup"><span data-stu-id="86598-104">An orchestration can take the following items as parameters:</span></span>  
  
-   <span data-ttu-id="86598-105">Messages</span><span class="sxs-lookup"><span data-stu-id="86598-105">Messages</span></span>  
  
-   <span data-ttu-id="86598-106">Variables (objets inclus)</span><span class="sxs-lookup"><span data-stu-id="86598-106">Variables (including objects)</span></span>  
  
-   <span data-ttu-id="86598-107">Ensembles de corrélations</span><span class="sxs-lookup"><span data-stu-id="86598-107">Correlation sets</span></span>  
  
-   <span data-ttu-id="86598-108">Liens de rôle</span><span class="sxs-lookup"><span data-stu-id="86598-108">Role links</span></span>  
  
-   <span data-ttu-id="86598-109">Ports</span><span class="sxs-lookup"><span data-stu-id="86598-109">Ports</span></span>  
  
 <span data-ttu-id="86598-110">Les paramètres peuvent être transmis entre les orchestrations en tant que paramètres d'entrée ou de sortie.</span><span class="sxs-lookup"><span data-stu-id="86598-110">Parameters can be passed between orchestrations as in parameters or out parameters.</span></span> <span data-ttu-id="86598-111">Les premiers peuvent être transmis par valeur ou référence,</span><span class="sxs-lookup"><span data-stu-id="86598-111">In parameters can be passed by value or by reference.</span></span> <span data-ttu-id="86598-112">et les seconds uniquement par référence.</span><span class="sxs-lookup"><span data-stu-id="86598-112">Out parameters can only be passed by reference.</span></span> <span data-ttu-id="86598-113">Les paramètres incluent les variables, messages, ensembles de corrélations, liens de rôle et ports.</span><span class="sxs-lookup"><span data-stu-id="86598-113">Parameters can include variables, messages, correlation sets, role links, and ports.</span></span>  
  
### <a name="to-set-orchestration-parameters"></a><span data-ttu-id="86598-114">Pour définir des paramètres d'orchestration</span><span class="sxs-lookup"><span data-stu-id="86598-114">To set orchestration parameters</span></span>  
  
1.  <span data-ttu-id="86598-115">Dans la fenêtre Vue Orchestration, utilisez le **paramètres de l’Orchestration** dossier pour ajouter des ports, des messages et des variables.</span><span class="sxs-lookup"><span data-stu-id="86598-115">In the Orchestration View window, use the **Orchestration Parameters** folder to add variables, messages, and ports.</span></span>  
  
2.  <span data-ttu-id="86598-116">Pour chaque élément ajouté à la **paramètres de l’Orchestration** dossier, utilisez la fenêtre Propriétés pour spécifier la **Direction** propriété :</span><span class="sxs-lookup"><span data-stu-id="86598-116">For each item added to the **Orchestration Parameters** folder, use the Properties window to specify the **Direction** property:</span></span>  
  
    -   <span data-ttu-id="86598-117">Avant : paramètre transmis par valeur.</span><span class="sxs-lookup"><span data-stu-id="86598-117">In—A parameter passed in by value.</span></span>  
  
    -   <span data-ttu-id="86598-118">Réf. : paramètre transmis par référence.</span><span class="sxs-lookup"><span data-stu-id="86598-118">Ref—A parameter passed in by reference.</span></span>  
  
    -   <span data-ttu-id="86598-119">Arrière : paramètre transmis par référence.</span><span class="sxs-lookup"><span data-stu-id="86598-119">Out—A parameter passed out by reference.</span></span>  
  
### <a name="to-add-a-parameter-to-an-orchestration"></a><span data-ttu-id="86598-120">Pour ajouter un paramètre à une orchestration</span><span class="sxs-lookup"><span data-stu-id="86598-120">To add a parameter to an orchestration</span></span>  
  
1.  <span data-ttu-id="86598-121">Dans la fenêtre Vue Orchestration, cliquez sur le **paramètres de l’Orchestration** dossier puis cliquez sur le type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="86598-121">In the Orchestration View window, right-click the **Orchestration Parameters** folder and then click the kind of parameter you want.</span></span>  
  
2.  <span data-ttu-id="86598-122">Pour les liens de rôle et les ports configurés, servez-vous de l'Assistant pour configurer le paramètre.</span><span class="sxs-lookup"><span data-stu-id="86598-122">For configured ports and role links, use the wizard to configure the parameter.</span></span>  
  
     <span data-ttu-id="86598-123">— Ou :</span><span class="sxs-lookup"><span data-stu-id="86598-123">—Or—</span></span>  
  
     <span data-ttu-id="86598-124">Pour tout autre type de paramètre, effectuez la configuration dans la page des propriétés.</span><span class="sxs-lookup"><span data-stu-id="86598-124">For other parameter types, use the properties page to configure the parameter.</span></span>  
  
 <span data-ttu-id="86598-125">**Types de paramètres**</span><span class="sxs-lookup"><span data-stu-id="86598-125">**Parameter types**</span></span>  
  
 <span data-ttu-id="86598-126">Les paramètres peuvent être passés par valeur, en tant que paramètres de référence ou paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="86598-126">Parameters can be passed by value, as reference parameters, and as out parameters.</span></span> <span data-ttu-id="86598-127">Lorsqu'un paramètre est passé par valeur à une orchestration, une copie des données est effectuée et utilisée par l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="86598-127">When a parameter is passed by value to an orchestration, a copy of the data is made and used by the orchestration.</span></span>  
  
 <span data-ttu-id="86598-128">Lorsque vous utilisez un paramètre de référence, aucune copie n'est réalisée.</span><span class="sxs-lookup"><span data-stu-id="86598-128">When you use a reference parameter, no copy is made.</span></span> <span data-ttu-id="86598-129">L'emplacement de mémoire contenant les données est partagé entre le programme appelant et l'orchestration, et son contenu peut être modifié par l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="86598-129">The memory location that contains the data is shared between the calling program and the orchestration, and the contents of this memory location can be modified by the orchestration.</span></span> <span data-ttu-id="86598-130">Une telle modification implique la modification de la valeur du paramètre dans l'orchestration mais aussi dans le programme appelant.</span><span class="sxs-lookup"><span data-stu-id="86598-130">Such a modification means that the value of the parameter is changed not only in the orchestration, but also in the calling program.</span></span>  
  
 <span data-ttu-id="86598-131">Un paramètre de sortie est similaire au paramètre de référence, mais l'orchestration ne peut pas supposer qu'il contient des données valides lors de sa transmission. Le programme appelant attend de l'orchestration qu'elle affecte une valeur au paramètre.</span><span class="sxs-lookup"><span data-stu-id="86598-131">An out parameter is similar to a reference parameter, but the orchestration cannot assume that it contains valid data when passed in; rather, the calling program expects the orchestration to assign a value to this parameter.</span></span>  
  
 <span data-ttu-id="86598-132">**Règles pour les paramètres de l’orchestration**</span><span class="sxs-lookup"><span data-stu-id="86598-132">**Rules for orchestration parameters**</span></span>  
  
-   <span data-ttu-id="86598-133">Vous ne pouvez transmettre les messages et les variables (objets inclus) qu'en tant que paramètres de référence ou de sortie.</span><span class="sxs-lookup"><span data-stu-id="86598-133">You can pass only messages and variables (including objects) as out or reference parameters.</span></span>  
  
-   <span data-ttu-id="86598-134">Impossible de transmettre ou de référencer des paramètres à une orchestration dans un **démarrer Orchestration** forme.</span><span class="sxs-lookup"><span data-stu-id="86598-134">You cannot pass out or reference parameters to an orchestration in a **Start Orchestration** shape.</span></span>  
  
-   <span data-ttu-id="86598-135">Les paramètres d'entrée, incluant les liens de rôle et les ports dynamiques, doivent se voir attribuer une valeur avant d'être transmis à une orchestration.</span><span class="sxs-lookup"><span data-stu-id="86598-135">In parameters, including any role links and dynamic ports, must be definitely assigned before being passed to an orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86598-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86598-136">See Also</span></span>  
 <span data-ttu-id="86598-137">[Formes d’orchestration](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="86598-137">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 <span data-ttu-id="86598-138">[Comment ajouter des formes aux Orchestrations](../core/how-to-add-shapes-to-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="86598-138">[How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md) </span></span>  
 [<span data-ttu-id="86598-139">Comment utiliser le Type de boîte de dialogue Sélectionnez artefact</span><span class="sxs-lookup"><span data-stu-id="86598-139">How to Use the Select Artifact Type Dialog Box</span></span>](../core/how-to-use-the-select-artifact-type-dialog-box.md)