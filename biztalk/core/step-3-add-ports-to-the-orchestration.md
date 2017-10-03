---
title: "Étape 3 : Ajouter des Ports à l’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 245df16e-d327-4c79-be85-004134d5ea6f
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13af336b2162e0f784195bf7c789c0dff984cb04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-ports-to-the-orchestration"></a><span data-ttu-id="ff6e0-102">Étape 3 : ajout des ports à l'orchestration</span><span class="sxs-lookup"><span data-stu-id="ff6e0-102">Step 3: Add Ports to the Orchestration</span></span>
<span data-ttu-id="ff6e0-103">![Étape 3 sur 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span><span class="sxs-lookup"><span data-stu-id="ff6e0-103">![Step 3 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")</span></span>  
  
 <span data-ttu-id="ff6e0-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="ff6e0-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="ff6e0-105">**Objectif :** dans cette étape, vous ajoutez trois ports à l’orchestration EAIProcess et les configurer.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-105">**Objective:** In this step, you add three ports to the EAIProcess orchestration and configure them.</span></span>  
  
 <span data-ttu-id="ff6e0-106">**Objectif :** Ports indiquent comment votre orchestration envoie des messages à et recevoir des messages à partir d’autres processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-106">**Purpose:** Ports specify how your orchestration will send messages to and receive messages from other business processes.</span></span> <span data-ttu-id="ff6e0-107">Chaque port possède un type, une direction et une liaison qui déterminent ensemble la direction de communication, le modèle de communication, l'emplacement vers et à partir duquel le message est envoyé ou reçu, et comment la communication a lieu.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-107">Each port has a type, a direction, and a binding, which together determine the direction of communication, the pattern of communication, the location to or from which the message is sent or received, and how the communication takes place.</span></span> <span data-ttu-id="ff6e0-108">Les trois ports que vous allez créer et configurer lors de cette étape remplissent les rôles suivants :</span><span class="sxs-lookup"><span data-stu-id="ff6e0-108">The three ports you create and configure in this step fulfill the following roles:</span></span>  
  
-   <span data-ttu-id="ff6e0-109">**ReceiveRequestPort** reçoit des messages de demande de réapprovisionnement de stock de l’entrepôt.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-109">**ReceiveRequestPort** receives inventory replenishment request messages from the warehouse.</span></span>  
  
-   <span data-ttu-id="ff6e0-110">**SendToERP** transfère les messages de demande au système ERP.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-110">**SendToERP** forwards the request messages to the ERP system.</span></span>  
  
-   <span data-ttu-id="ff6e0-111">**SendDeclinePort** envoie la demande des messages de refus à l’entrepôt.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-111">**SendDeclinePort** sends request decline messages back to the warehouse.</span></span>  
  
 <span data-ttu-id="ff6e0-112">Pour plus d’informations, consultez [à l’aide des Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e0-112">For more information, see [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ff6e0-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ff6e0-113">Prerequisites</span></span>  
 <span data-ttu-id="ff6e0-114">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="ff6e0-114">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="ff6e0-115">Avant de commencer cette étape, vous devez effectuer [étape 2 : définir le processus d’entreprise](../core/step-2-define-the-business-process.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e0-115">Before you begin this step you must complete [Step 2: Define the Business Process](../core/step-2-define-the-business-process.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ff6e0-116">Procédures</span><span class="sxs-lookup"><span data-stu-id="ff6e0-116">Procedures</span></span>  
  
#### <a name="to-create-and-configure-receiverequestport"></a><span data-ttu-id="ff6e0-117">Pour créer et configurer le port ReceiveRequestPort</span><span class="sxs-lookup"><span data-stu-id="ff6e0-117">To create and configure ReceiveRequestPort</span></span>  
  
1.  <span data-ttu-id="ff6e0-118">Dans l’Explorateur de solutions, double-cliquez sur **EAIProcess.odx**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-118">In Solution Explorer, double-click **EAIProcess.odx**.</span></span>  
  
2.  <span data-ttu-id="ff6e0-119">Dans le Concepteur d’Orchestration, l’orchestration de boîte à outils, faites glisser le **Port** forme vers la gauche **Surface du Port**, parallèlement à la **ReceiveRequest** forme.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-119">In Orchestration Designer, from the orchestration Toolbox, drag the **Port** shape to the left-side **Port Surface**, parallel to the **ReceiveRequest** shape.</span></span> <span data-ttu-id="ff6e0-120">L'Assistant Configuration du port démarre automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-120">The Port Configuration Wizard starts automatically.</span></span>  
  
3.  <span data-ttu-id="ff6e0-121">Dans la page **Bienvenue dans l'Assistant Configuration du port** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-121">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="ff6e0-122">Sur le **propriétés de Port** page, procédez comme suit, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-122">On the **Port Properties** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="ff6e0-123">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ff6e0-123">Use this</span></span>|<span data-ttu-id="ff6e0-124">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ff6e0-124">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ff6e0-125">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-125">**Name**</span></span>|<span data-ttu-id="ff6e0-126">Type **ReceiveRequestPort**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-126">Type **ReceiveRequestPort**.</span></span>|  
  
5.  <span data-ttu-id="ff6e0-127">Sur le **sélectionner un Type de Port** page, procédez comme suit, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-127">On the **Select a Port Type** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="ff6e0-128">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ff6e0-128">Use this</span></span>|<span data-ttu-id="ff6e0-129">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ff6e0-129">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ff6e0-130">**Sélectionnez le type de port à utiliser pour ce port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-130">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="ff6e0-131">Sélectionnez le **créer un nouveau Type de Port** option.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-131">Select the **Create a new Port Type** option.</span></span>|  
    |<span data-ttu-id="ff6e0-132">**Nom du Type de port :**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-132">**Port Type Name:**</span></span>|<span data-ttu-id="ff6e0-133">Type **ReceiveRequestPortType**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-133">Type **ReceiveRequestPortType**.</span></span>|  
    |<span data-ttu-id="ff6e0-134">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-134">**Communication Pattern**</span></span>|<span data-ttu-id="ff6e0-135">Sélectionnez **unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-135">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="ff6e0-136">**Restrictions d’accès**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-136">**Access Restrictions**</span></span>|<span data-ttu-id="ff6e0-137">Sélectionnez **interne - limité au projet**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-137">Select **Internal - limited to this project**.</span></span>|  
  
6.  <span data-ttu-id="ff6e0-138">Sur le **liaison de Port** page, procédez comme suit, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-138">On the **Port Binding** page, do the following, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="ff6e0-139">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ff6e0-139">Use this</span></span>|<span data-ttu-id="ff6e0-140">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ff6e0-140">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ff6e0-141">**Direction de communication du port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-141">**Port direction of communication**</span></span>|<span data-ttu-id="ff6e0-142">Sélectionnez **toujours recevoir les messages sur ce port**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-142">Select **I'll always be receiving messages on this port**.</span></span>|  
    |<span data-ttu-id="ff6e0-143">**Liaison de port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-143">**Port binding**</span></span>|<span data-ttu-id="ff6e0-144">À partir de select **spécifier plus tard**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-144">From select **Specify later**.</span></span>|  
  
7.  <span data-ttu-id="ff6e0-145">Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-145">On the **Completing the Port Wizard** page, click **Finish**.</span></span>  
  
#### <a name="to-create-and-configure-senddeclineport"></a><span data-ttu-id="ff6e0-146">Pour créer et configurer le port SendDeclinePort</span><span class="sxs-lookup"><span data-stu-id="ff6e0-146">To create and configure SendDeclinePort</span></span>  
  
1.  <span data-ttu-id="ff6e0-147">À partir de l’orchestration de boîte à outils, faites glisser le **Port** forme vers la gauche **Surface du Port**, parallèlement à la **SendRequestDecline** forme.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-147">From the orchestration Toolbox, drag the **Port** shape to the left-side **Port Surface**, parallel to the **SendRequestDecline** shape.</span></span>  
  
2.  <span data-ttu-id="ff6e0-148">Utilisez les informations dans le tableau suivant pour créer le **SendDeclinePort** port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-148">Use the information in the following table to create the **SendDeclinePort** send port.</span></span>  
  
    |<span data-ttu-id="ff6e0-149">Propriété</span><span class="sxs-lookup"><span data-stu-id="ff6e0-149">Property</span></span>|<span data-ttu-id="ff6e0-150">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff6e0-150">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="ff6e0-151">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-151">**Name**</span></span>|<span data-ttu-id="ff6e0-152">Type **SendDeclinePort**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-152">Type **SendDeclinePort**.</span></span>|  
    |<span data-ttu-id="ff6e0-153">**Sélectionnez le type de port à utiliser pour ce port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-153">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="ff6e0-154">Sélectionnez **créer un nouveau Type de Port**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-154">Select **Create a new Port Type**.</span></span>|  
    |<span data-ttu-id="ff6e0-155">**Nom de Type de port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-155">**Port Type Name**</span></span>|<span data-ttu-id="ff6e0-156">Type **SendDeclinePortType**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-156">Type **SendDeclinePortType**.</span></span>|  
    |<span data-ttu-id="ff6e0-157">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-157">**Communication Pattern**</span></span>|<span data-ttu-id="ff6e0-158">Sélectionnez **unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-158">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="ff6e0-159">**Restrictions d’accès**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-159">**Access Restrictions**</span></span>|<span data-ttu-id="ff6e0-160">Sélectionnez **interne - limité au projet**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-160">Select **Internal - limited to this project**.</span></span>|  
    |<span data-ttu-id="ff6e0-161">**Direction de communication du port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-161">**Port direction of communication**</span></span>|<span data-ttu-id="ff6e0-162">Dans la liste déroulante, sélectionnez **toujours envoyer les messages sur ce port**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-162">From the drop-down list, select **I'll always be sending messages on this port**.</span></span>|  
    |<span data-ttu-id="ff6e0-163">**Liaisons de port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-163">**Port bindings**</span></span>|<span data-ttu-id="ff6e0-164">Dans la liste déroulante, sélectionnez **spécifier plus tard**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-164">From the drop-down list, select **Specify later**.</span></span>|  
  
#### <a name="to-create-and-configure-sendtoerpport"></a><span data-ttu-id="ff6e0-165">Pour créer et configurer le port SendToERPPort</span><span class="sxs-lookup"><span data-stu-id="ff6e0-165">To create and configure SendToERPPort</span></span>  
  
1.  <span data-ttu-id="ff6e0-166">À partir de l’orchestration de boîte à outils, faites glisser le **Port** forme sur le côté droit **Surface du Port**, parallèlement à la **SendToERP** forme.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-166">From the orchestration Toolbox, drag the **Port** shape to the right-side **Port Surface**, parallel to the **SendToERP** shape.</span></span>  
  
2.  <span data-ttu-id="ff6e0-167">Utilisez les informations dans le tableau suivant pour terminer l’Assistant de Configuration de Port pour le **SendToERP** port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-167">Use the information in the following table to complete the Port Configuration Wizard for the **SendToERP** send port.</span></span>  
  
    |<span data-ttu-id="ff6e0-168">Propriété</span><span class="sxs-lookup"><span data-stu-id="ff6e0-168">Property</span></span>|<span data-ttu-id="ff6e0-169">Valeur</span><span class="sxs-lookup"><span data-stu-id="ff6e0-169">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="ff6e0-170">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-170">**Name**</span></span>|<span data-ttu-id="ff6e0-171">Type **SendToERPPort**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-171">Type **SendToERPPort**.</span></span>|  
    |<span data-ttu-id="ff6e0-172">**Sélectionnez le type de port à utiliser pour ce port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-172">**Select the port type to be used for this port**</span></span>|<span data-ttu-id="ff6e0-173">Sélectionnez **créer un nouveau Type de Port**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-173">Select **Create a new Port Type**.</span></span>|  
    |<span data-ttu-id="ff6e0-174">**Nom de Type de port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-174">**Port Type Name**</span></span>|<span data-ttu-id="ff6e0-175">Type **SendToERPPortType**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-175">Type **SendToERPPortType**.</span></span>|  
    |<span data-ttu-id="ff6e0-176">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-176">**Communication Pattern**</span></span>|<span data-ttu-id="ff6e0-177">Sélectionnez le **unidirectionnel** option.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-177">Select the **One-Way** option.</span></span>|  
    |<span data-ttu-id="ff6e0-178">**Restrictions d’accès**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-178">**Access Restrictions**</span></span>|<span data-ttu-id="ff6e0-179">Sélectionnez le **interne - limité au projet** option.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-179">Select the **Internal - limited to this project** option.</span></span>|  
    |<span data-ttu-id="ff6e0-180">**Direction de communication du port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-180">**Port direction of communication**</span></span>|<span data-ttu-id="ff6e0-181">Dans la liste déroulante, sélectionnez **toujours envoyer les messages sur ce port**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-181">From the drop-down list, select **I'll always be sending messages on this port**.</span></span>|  
    |<span data-ttu-id="ff6e0-182">**Liaison de port**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-182">**Port binding**</span></span>|<span data-ttu-id="ff6e0-183">Dans la liste déroulante, sélectionnez **spécifier plus tard**.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-183">From the drop-down list, select **Specify later**.</span></span>|  
  
#### <a name="to-connect-the-ports-to-the-action-shapes"></a><span data-ttu-id="ff6e0-184">Pour connecter les ports aux formes d'action</span><span class="sxs-lookup"><span data-stu-id="ff6e0-184">To connect the ports to the action shapes</span></span>  
  
-   <span data-ttu-id="ff6e0-185">Dans le Concepteur d'orchestration, dans la surface de conception, faites glisser la poignée (flèche verte) pour chaque port vers la poignée (flèche verte) correspondante de la forme d'action :</span><span class="sxs-lookup"><span data-stu-id="ff6e0-185">In Orchestration Designer, on the design surface, drag the green arrow-shaped handle for each port to the corresponding green handle of the action shape:</span></span>  
  
    |<span data-ttu-id="ff6e0-186">Connexion de ce port</span><span class="sxs-lookup"><span data-stu-id="ff6e0-186">Connect this port</span></span>|<span data-ttu-id="ff6e0-187">À cette forme d'action</span><span class="sxs-lookup"><span data-stu-id="ff6e0-187">To this action shape</span></span>|  
    |-----------------------|--------------------------|  
    |<span data-ttu-id="ff6e0-188">**ReceiveReqPort**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-188">**ReceiveReqPort**</span></span>|<span data-ttu-id="ff6e0-189">**Receive_Request**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-189">**Receive_Request**</span></span>|  
    |<span data-ttu-id="ff6e0-190">**SendDeclinePort**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-190">**SendDeclinePort**</span></span>|<span data-ttu-id="ff6e0-191">**Send_ReqDenied**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-191">**Send_ReqDenied**</span></span>|  
    |<span data-ttu-id="ff6e0-192">**SendToERP**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-192">**SendToERP**</span></span>|<span data-ttu-id="ff6e0-193">**Send_ReqToERP**</span><span class="sxs-lookup"><span data-stu-id="ff6e0-193">**Send_ReqToERP**</span></span>|  
  
     <span data-ttu-id="ff6e0-194">L'illustration suivante montre l'orchestration EAIProcess avec tous les ports connectés.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-194">The following figure shows the EAIProcess orchestration with all of the ports connected.</span></span>  
  
     <span data-ttu-id="ff6e0-195">![Orchestration EAIProcess avec ports connectés. ] (../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")</span><span class="sxs-lookup"><span data-stu-id="ff6e0-195">![EAIProcess orchestration with connected ports.](../core/media/tut1-eaiprocessportsconnected.gif "Tut1_EAIProcessPortsConnected")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="ff6e0-196">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="ff6e0-196">What did I just do?</span></span>  
 <span data-ttu-id="ff6e0-197">Au cours de cette étape, vous avez ajouté trois ports à l'orchestration EAIProcess et vous les avez configurés.</span><span class="sxs-lookup"><span data-stu-id="ff6e0-197">In this step, you added three ports to the EAIProcess orchestration and configured them.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ff6e0-198">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff6e0-198">Next Steps</span></span>  
 <span data-ttu-id="ff6e0-199">Vous générez le projet [étape 4 : création du projet EAIOrchestration](../core/step-4-build-the-eaiorchestration-project.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e0-199">You build the project in [Step 4: Build the EAIOrchestration Project](../core/step-4-build-the-eaiorchestration-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6e0-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff6e0-200">See Also</span></span>  
 <span data-ttu-id="ff6e0-201">[Étape 1 : Ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span><span class="sxs-lookup"><span data-stu-id="ff6e0-201">[Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span></span>  
 <span data-ttu-id="ff6e0-202">[Étape 2 : Définir le processus d’entreprise](../core/step-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="ff6e0-202">[Step 2: Define the Business Process](../core/step-2-define-the-business-process.md) </span></span>  
 [<span data-ttu-id="ff6e0-203">Étape 4 : Création du projet EAIOrchestration</span><span class="sxs-lookup"><span data-stu-id="ff6e0-203">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)