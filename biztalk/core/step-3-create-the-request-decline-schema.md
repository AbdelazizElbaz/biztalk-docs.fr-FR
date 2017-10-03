---
title: "Étape 3 : Créer le schéma de refus de demande | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1ce166c-1be1-4ef4-9d00-3da7038d4ada
caps.latest.revision: "39"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ff343c58e836bc0738f0200016308eb7a4d90b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-create-the-request-decline-schema"></a><span data-ttu-id="aef7d-102">Étape 3 : création du schéma de refus de demande</span><span class="sxs-lookup"><span data-stu-id="aef7d-102">Step 3: Create the Request Decline Schema</span></span>
<span data-ttu-id="aef7d-103">![Étape 3 sur 5](../core/media/step-3of5.gif "Step_3of5")</span><span class="sxs-lookup"><span data-stu-id="aef7d-103">![Step 3 of 5](../core/media/step-3of5.gif "Step_3of5")</span></span>  
  
 <span data-ttu-id="aef7d-104">**Durée :** 7 minutes</span><span class="sxs-lookup"><span data-stu-id="aef7d-104">**Time to complete:** 7 minutes</span></span>  
  
 <span data-ttu-id="aef7d-105">**Objectif :** dans cette étape, vous créez le schéma du message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] renvoie à l’entrepôt si le processus d’entreprise rejette la demande de réapprovisionnement de stock.</span><span class="sxs-lookup"><span data-stu-id="aef7d-105">**Objective:** In this step, you create the schema for the message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends back to the warehouse if the business process rejects the inventory replenishment request.</span></span>  
  
 <span data-ttu-id="aef7d-106">**Objectif :** le schéma définit les données et la structure du message de refus de demande.</span><span class="sxs-lookup"><span data-stu-id="aef7d-106">**Purpose:** The schema defines the data and the structure of the request decline message.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="aef7d-107"> utilise le schéma pour identifier et interagir avec les données du message.</span><span class="sxs-lookup"><span data-stu-id="aef7d-107"> uses the schema to identify and interact with the data in the message.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aef7d-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="aef7d-108">Prerequisites</span></span>  
 <span data-ttu-id="aef7d-109">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="aef7d-109">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="aef7d-110">Avant de commencer cette étape, vous devez effectuer [étape 1 : créer un projet EAISchemas](../core/step-1-create-eaischemas-project.md).</span><span class="sxs-lookup"><span data-stu-id="aef7d-110">Before you begin this step you must complete [Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="aef7d-111">Procédures</span><span class="sxs-lookup"><span data-stu-id="aef7d-111">Procedures</span></span>  
  
#### <a name="to-create-the-request-decline-schema"></a><span data-ttu-id="aef7d-112">Pour créer le schéma de refus de demande</span><span class="sxs-lookup"><span data-stu-id="aef7d-112">To create the Request Decline schema</span></span>  
  
1.  <span data-ttu-id="aef7d-113">Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="aef7d-113">In Solution Explorer, right-click the **EAISchemas** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="aef7d-114">Dans le **ajouter un nouvel élément - EAISchemas** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="aef7d-114">In the **Add New Item - EAISchemas** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="aef7d-115">Utiliser</span><span class="sxs-lookup"><span data-stu-id="aef7d-115">Use this</span></span>|<span data-ttu-id="aef7d-116">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="aef7d-116">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="aef7d-117">**Modèles installés**</span><span class="sxs-lookup"><span data-stu-id="aef7d-117">**Installed Templates**</span></span>|<span data-ttu-id="aef7d-118">Cliquez sur **les fichiers de schéma**, puis cliquez sur **schéma**.</span><span class="sxs-lookup"><span data-stu-id="aef7d-118">Click **Schema Files**, and then click **Schema**.</span></span>|  
    |<span data-ttu-id="aef7d-119">**Nom**</span><span class="sxs-lookup"><span data-stu-id="aef7d-119">**Name**</span></span>|<span data-ttu-id="aef7d-120">Tapez `RequestDecline.xsd`.</span><span class="sxs-lookup"><span data-stu-id="aef7d-120">Type `RequestDecline.xsd`.</span></span>|  
  
3.  <span data-ttu-id="aef7d-121">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="aef7d-121">Click **Add**.</span></span>  
  
4.  <span data-ttu-id="aef7d-122">Dans l’Éditeur BizTalk, à partir de l’arborescence du schéma, cliquez sur le **racine** nœud pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="aef7d-122">In BizTalk Editor, from schema tree, click the **Root** node to select it.</span></span>  
  
5.  <span data-ttu-id="aef7d-123">Dans le volet Propriétés, modifiez la valeur de la **nom de nœud** propriété `DeclineReq`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="aef7d-123">In the Properties pane, change the value of the **Node Name** property to `DeclineReq`, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="aef7d-124">Dans l’arborescence du schéma, cliquez sur le **DeclineReq** nœud **insérer un nœud de schéma**, puis cliquez sur **élément de champ enfant**.</span><span class="sxs-lookup"><span data-stu-id="aef7d-124">In schema tree, right-click the **DeclineReq** node, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span>  
  
7.  <span data-ttu-id="aef7d-125">Type `ReqID` comme nouveau nom pour l’élément et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="aef7d-125">Type `ReqID` as the new name for the element, and then press ENTER.</span></span>  
  
8.  <span data-ttu-id="aef7d-126">Ajouter un deuxième élément de champ enfant nommé `GrandTotal`.</span><span class="sxs-lookup"><span data-stu-id="aef7d-126">Add a second child field element named `GrandTotal`.</span></span>  
  
9. <span data-ttu-id="aef7d-127">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="aef7d-127">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="aef7d-128">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="aef7d-128">What did I just do?</span></span>  
 <span data-ttu-id="aef7d-129">Dans cette étape, vous créez le schéma du message que renvoie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'entrepôt si le processus d'entreprise rejette le message de demande de stock.</span><span class="sxs-lookup"><span data-stu-id="aef7d-129">In this step, you created the schema for the message that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends back to the warehouse if the business process rejects the inventory request.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aef7d-130">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="aef7d-130">Next Steps</span></span>  
 <span data-ttu-id="aef7d-131">Vous créez le mappage nécessaire à l'orchestration pour créer le message de refus de demande en reformatant le message de demande.</span><span class="sxs-lookup"><span data-stu-id="aef7d-131">You create the map needed by the orchestration to create request decline message by reformatting request message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef7d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aef7d-132">See Also</span></span>  
 [<span data-ttu-id="aef7d-133">Étape 1 : Création du projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="aef7d-133">Step 1: Create EAISchemas Project</span></span>](../core/step-1-create-eaischemas-project.md)  
 <span data-ttu-id="aef7d-134">[Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="aef7d-134">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="aef7d-135">[Étape 4 : Créer la carte](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="aef7d-135">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="aef7d-136">[Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="aef7d-136">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 [<span data-ttu-id="aef7d-137">Création de schémas à l’aide de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="aef7d-137">Creating Schemas Using BizTalk Editor</span></span>](../core/creating-schemas-using-biztalk-editor.md)