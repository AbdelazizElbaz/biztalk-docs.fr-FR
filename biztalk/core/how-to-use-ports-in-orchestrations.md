---
title: Comment utiliser des Ports dans les Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, adding ports
- Port Configuration Wizard [Orchestration Designer], configuring ports
- ports, operations
- operations, adding to ports
- configuring, ports
- ports, deleting
- deleting, ports
- ports, Port Configuration Wizard [Orchestration Designer]
- ports, adding to orchestrations
- ports, configuring
ms.assetid: da8665cd-ccde-4949-b5f5-01f9f8be5ce8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3edef29376d8724d93192040ee88951ced245ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-ports-in-orchestrations"></a><span data-ttu-id="dac8f-102">Utilisation des ports dans les orchestrations</span><span class="sxs-lookup"><span data-stu-id="dac8f-102">How to Use Ports in Orchestrations</span></span>
<span data-ttu-id="dac8f-103">Pour ajouter des ports à une orchestration, on procède sensiblement de la même façon que pour ajouter des contrôles à un formulaire Web ou Windows.</span><span class="sxs-lookup"><span data-stu-id="dac8f-103">You add ports to an orchestration in much the same way that you add controls to a Web Form or Windows Form.</span></span> <span data-ttu-id="dac8f-104">Vous pouvez également ajouter des ports en utilisant la fenêtre Vue Orchestration.</span><span class="sxs-lookup"><span data-stu-id="dac8f-104">You can also add ports by using the Orchestration View window.</span></span>  
  
### <a name="to-add-a-new-port"></a><span data-ttu-id="dac8f-105">Pour ajouter un nouveau port</span><span class="sxs-lookup"><span data-stu-id="dac8f-105">To add a new port</span></span>  
  
-   <span data-ttu-id="dac8f-106">Avec le bouton droit une **Surface du Port** ou un **lien de rôle**, puis cliquez sur **nouveau Port**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-106">Right-click a **Port Surface** or a **Role Link**, and then click **New Port**.</span></span>  
  
     <span data-ttu-id="dac8f-107">— Ou :</span><span class="sxs-lookup"><span data-stu-id="dac8f-107">—Or—</span></span>  
  
     <span data-ttu-id="dac8f-108">Dans la fenêtre Vue Orchestration, cliquez sur **Ports** puis cliquez sur **nouveau Port**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-108">In the Orchestration View window, right-click **Ports** and then click **New Port**.</span></span>  
  
     <span data-ttu-id="dac8f-109">Un conseil DesignTip apparaît sur les ports dont la configuration n'est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="dac8f-109">A DesignTip appears on ports that are not yet fully configured.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="dac8f-110">Vous pouvez également faire glisser les ports en un **lien de rôle**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-110">You can also drag ports into a **Role Link**.</span></span>  
  
### <a name="to-add-and-configure-a-new-port"></a><span data-ttu-id="dac8f-111">Pour ajouter et configurer un nouveau port</span><span class="sxs-lookup"><span data-stu-id="dac8f-111">To add and configure a new port</span></span>  
  
1.  <span data-ttu-id="dac8f-112">À partir de la **Orchestrations BizTalk** onglet de la boîte à outils, faites glisser le **Port** forme sur un **Surface du Port** ou un **lien de rôle**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-112">From the **BizTalk Orchestrations** tab of the Toolbox, drag the **Port** shape onto a **Port Surface** or a **Role Link**.</span></span>  
  
     <span data-ttu-id="dac8f-113">— Ou :</span><span class="sxs-lookup"><span data-stu-id="dac8f-113">—Or—</span></span>  
  
     <span data-ttu-id="dac8f-114">Avec le bouton droit une **Surface du Port** ou un **lien de rôle**, puis cliquez sur **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-114">Right-click a **Port Surface** or a **Role Link**, and then click **New Configured Port**.</span></span>  
  
     <span data-ttu-id="dac8f-115">— Ou :</span><span class="sxs-lookup"><span data-stu-id="dac8f-115">—Or—</span></span>  
  
     <span data-ttu-id="dac8f-116">Dans la fenêtre Vue Orchestration, cliquez sur **Ports** puis cliquez sur **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-116">In the Orchestration View window, right-click **Ports** and then click **New Configured Port**.</span></span>  
  
     <span data-ttu-id="dac8f-117">L'Assistant Configuration du port s'affiche.</span><span class="sxs-lookup"><span data-stu-id="dac8f-117">The Port Configuration Wizard appears.</span></span>  
  
2.  <span data-ttu-id="dac8f-118">Suivez les instructions de l'Assistant pour configurer le port.</span><span class="sxs-lookup"><span data-stu-id="dac8f-118">Follow the steps in the wizard to configure the port.</span></span> <span data-ttu-id="dac8f-119">Pour plus d’informations, consultez [comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="dac8f-119">For more information, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).</span></span>  
  
### <a name="to-remove-a-port"></a><span data-ttu-id="dac8f-120">Pour supprimer un port</span><span class="sxs-lookup"><span data-stu-id="dac8f-120">To remove a port</span></span>  
  
-   <span data-ttu-id="dac8f-121">Cliquez sur le port à supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-121">Right-click the port to remove, and then click **Delete**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dac8f-122">Si vous supprimez un port qu’il a été connectée à un **envoyer** ou **réception** forme dans une orchestration qui a été compilée, les opérations de port sur la forme ne sera pas supprimé, et vous recevez des erreurs lors de la vous essayez de compiler.</span><span class="sxs-lookup"><span data-stu-id="dac8f-122">If you delete a port after it has been connected to a **Send** or **Receive** shape in an orchestration that has been compiled, the port operations on the shape will not be deleted, and you will receive errors when you try to compile.</span></span> <span data-ttu-id="dac8f-123">Connectez la forme à un autre port et reconfigurez les opérations associées au port.</span><span class="sxs-lookup"><span data-stu-id="dac8f-123">Connect the shape to another port and reconfigure the port operations.</span></span>  
  
### <a name="to-configure-a-port-by-using-the-port-configuration-wizard"></a><span data-ttu-id="dac8f-124">Pour configurer un port à l'aide de l'Assistant Configuration du port</span><span class="sxs-lookup"><span data-stu-id="dac8f-124">To configure a port by using the Port Configuration Wizard</span></span>  
  
1.  <span data-ttu-id="dac8f-125">Cliquez sur le port à configurer, puis cliquez sur **configurer le Port**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-125">Right-click the port to configure, and then click **Configure Port**.</span></span>  
  
2.  <span data-ttu-id="dac8f-126">Suivez les instructions de l'Assistant Configuration du port pour configurer le port.</span><span class="sxs-lookup"><span data-stu-id="dac8f-126">Follow the steps in the Port Configuration Wizard to configure the port.</span></span> <span data-ttu-id="dac8f-127">Pour plus d’informations, consultez [comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="dac8f-127">For more information, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).</span></span>  
  
### <a name="to-configure-a-port-manually-by-using-the-properties-window"></a><span data-ttu-id="dac8f-128">Pour configurer un port manuellement à l'aide de la fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="dac8f-128">To configure a port manually by using the Properties window</span></span>  
  
1.  <span data-ttu-id="dac8f-129">Sélectionnez le port à configurer.</span><span class="sxs-lookup"><span data-stu-id="dac8f-129">Select the port to configure.</span></span>  
  
2.  <span data-ttu-id="dac8f-130">Dans la fenêtre Propriétés, définissez les propriétés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="dac8f-130">In the Properties window, specify the following properties:</span></span>  
  
    |<span data-ttu-id="dac8f-131">Propriété</span><span class="sxs-lookup"><span data-stu-id="dac8f-131">Property</span></span>|<span data-ttu-id="dac8f-132"> Description</span><span class="sxs-lookup"><span data-stu-id="dac8f-132">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="dac8f-133">Type de port</span><span class="sxs-lookup"><span data-stu-id="dac8f-133">Port Type</span></span>|<span data-ttu-id="dac8f-134">Détermine le modèle de communication, les opérations et les types de messages à parties multiples associés à un port.</span><span class="sxs-lookup"><span data-stu-id="dac8f-134">Determines the communication pattern, operations, and multi-part message types associated with a port.</span></span>|  
    |<span data-ttu-id="dac8f-135">Direction de la communication</span><span class="sxs-lookup"><span data-stu-id="dac8f-135">Communication Direction</span></span>|<span data-ttu-id="dac8f-136">Détermine si cette orchestration est l'expéditeur ou le récepteur de la communication.</span><span class="sxs-lookup"><span data-stu-id="dac8f-136">Determines whether this orchestration is the sender or the receiver for this communication.</span></span>|  
    |<span data-ttu-id="dac8f-137">Modèle de communication</span><span class="sxs-lookup"><span data-stu-id="dac8f-137">Communication Pattern</span></span>|<span data-ttu-id="dac8f-138">Détermine si ce port est utilisé pour une requête-réponse ou une communication unidirectionnelle.</span><span class="sxs-lookup"><span data-stu-id="dac8f-138">Determines if this port is used for request-response or one-way communication.</span></span> <span data-ttu-id="dac8f-139">(Cette propriété est déterminée par le **Type de Port** propriété et est en lecture seule.)</span><span class="sxs-lookup"><span data-stu-id="dac8f-139">(This property is determined by the **Port Type** property and is read-only.)</span></span>|  
    |<span data-ttu-id="dac8f-140">Binding</span><span class="sxs-lookup"><span data-stu-id="dac8f-140">Binding</span></span>|<span data-ttu-id="dac8f-141">Détermine comment un message atteint sa destination:</span><span class="sxs-lookup"><span data-stu-id="dac8f-141">Determines how a message gets to its destination:</span></span><br /><br /> <span data-ttu-id="dac8f-142">Direct — La communication se fait avec une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="dac8f-142">Direct—Communication is with another orchestration.</span></span><br /><br /> <span data-ttu-id="dac8f-143">Dynamique — La communication se fait avec un point de terminaison déterminé au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="dac8f-143">Dynamic—Communication is with an endpoint that is determined at run time.</span></span><br /><br /> <span data-ttu-id="dac8f-144">Spécifier plus tard — La communication se fait avec un point de terminaison déterminé par un administrateur au moment de la configuration.</span><span class="sxs-lookup"><span data-stu-id="dac8f-144">Specify later—Communication is with an endpoint that is determined by an administrator at configuration time.</span></span><br /><br /> <span data-ttu-id="dac8f-145">Spécifier maintenant — La communication se fait avec un point de terminaison connu au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="dac8f-145">Specify now—Communication is with an endpoint that is known at design time.</span></span>|  
    |<span data-ttu-id="dac8f-146">Identificateur</span><span class="sxs-lookup"><span data-stu-id="dac8f-146">Identifier</span></span>|<span data-ttu-id="dac8f-147">Nom utilisé pour ce port dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="dac8f-147">The name used for this port in the orchestration.</span></span>|  
    |<span data-ttu-id="dac8f-148">livraison chronologique des messages (éventuellement en anglais)</span><span class="sxs-lookup"><span data-stu-id="dac8f-148">Ordered Delivery</span></span>|<span data-ttu-id="dac8f-149">Pour les ports de réception, garantit que les messages publiés dans la base de données MessageBox dans un ordre indiqué sont remis à chaque abonné correspondant dans le même ordre que celui dans lequel ils ont été publiés dans la base MessageBox.</span><span class="sxs-lookup"><span data-stu-id="dac8f-149">For receive ports, ensures that messages that are published to the MessageBox database in a given order are delivered to each matching subscriber in the same order in which they were published to the message box.</span></span> <span data-ttu-id="dac8f-150">Pour plus d’informations, consultez [classés de remise de Messages](../core/ordered-delivery-of-messages.md).</span><span class="sxs-lookup"><span data-stu-id="dac8f-150">For more information, see [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md).</span></span>|  
    |<span data-ttu-id="dac8f-151">Accusé de réception</span><span class="sxs-lookup"><span data-stu-id="dac8f-151">Delivery Notification</span></span>|<span data-ttu-id="dac8f-152">Pour les ports d'envoi, détermine si vous souhaitez recevoir un accusé de réception lorsqu'un message est correctement envoyé.</span><span class="sxs-lookup"><span data-stu-id="dac8f-152">For send ports, determines whether want to receive an acknowledgment when a message is sent successfully.</span></span> <span data-ttu-id="dac8f-153">Pour plus d’informations, consultez « Remise de Notification » dans [comment configurer la forme envoi](../core/how-to-configure-the-send-shape.md).</span><span class="sxs-lookup"><span data-stu-id="dac8f-153">For more information, see "Delivery Notification" in [How to Configure the Send Shape](../core/how-to-configure-the-send-shape.md).</span></span>|  
  
3.  <span data-ttu-id="dac8f-154">Les propriétés restantes pour spécifier sont déterminées par la **liaison** propriété :</span><span class="sxs-lookup"><span data-stu-id="dac8f-154">The remaining properties to specify are determined by the **Binding** property:</span></span>  
  
    -   <span data-ttu-id="dac8f-155">Liaison directe — utilisée lors d'une communication directe avec une autre orchestration.</span><span class="sxs-lookup"><span data-stu-id="dac8f-155">Direct binding—Used when communicating directly with another orchestration.</span></span>  
  
        |<span data-ttu-id="dac8f-156">Propriété</span><span class="sxs-lookup"><span data-stu-id="dac8f-156">Property</span></span>|<span data-ttu-id="dac8f-157"> Description</span><span class="sxs-lookup"><span data-stu-id="dac8f-157">Description</span></span>|  
        |--------------|-----------------|  
        |<span data-ttu-id="dac8f-158">Port d'orchestration des partenaires</span><span class="sxs-lookup"><span data-stu-id="dac8f-158">Partner Orchestration Port</span></span>|<span data-ttu-id="dac8f-159">Détermine le port auquel les orchestrations des partenaires sont automatiquement liées.</span><span class="sxs-lookup"><span data-stu-id="dac8f-159">Determines to which port the partner orchestrations will be directly bound.</span></span>|  
  
    -   <span data-ttu-id="dac8f-160">Liaison dynamique — utilisée lors d'une communication avec un point de terminaison déterminé au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="dac8f-160">Dynamic binding—Used when communicating with an endpoint that is determined at run time.</span></span>  
  
        |<span data-ttu-id="dac8f-161">Propriété</span><span class="sxs-lookup"><span data-stu-id="dac8f-161">Property</span></span>|<span data-ttu-id="dac8f-162"> Description</span><span class="sxs-lookup"><span data-stu-id="dac8f-162">Description</span></span>|  
        |--------------|-----------------|  
        |<span data-ttu-id="dac8f-163">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="dac8f-163">Receive Pipeline</span></span>|<span data-ttu-id="dac8f-164">Détermine le pipeline à utiliser pour les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="dac8f-164">Determines which pipeline to use for incoming messages.</span></span>|  
        |<span data-ttu-id="dac8f-165">Pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="dac8f-165">Send Pipeline</span></span>|<span data-ttu-id="dac8f-166">Détermine le pipeline à utiliser pour les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="dac8f-166">Determines which pipeline to use for outgoing messages.</span></span>|  
  
    -   <span data-ttu-id="dac8f-167">Spécifier plus tard — utilisée lors de la communication avec un point de terminaison configuré par un administrateur.</span><span class="sxs-lookup"><span data-stu-id="dac8f-167">Specify later—Used when communicating with an endpoint that is configured by an administrator.</span></span>  
  
    -   <span data-ttu-id="dac8f-168">Spécifier maintenant — utilisée lors de la communication avec un point de terminaison connu au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="dac8f-168">Specify now—Used when communicating with an endpoint that is known at design time.</span></span>  
  
        |<span data-ttu-id="dac8f-169">Propriété</span><span class="sxs-lookup"><span data-stu-id="dac8f-169">Property</span></span>|<span data-ttu-id="dac8f-170"> Description</span><span class="sxs-lookup"><span data-stu-id="dac8f-170">Description</span></span>|  
        |--------------|-----------------|  
        |<span data-ttu-id="dac8f-171">Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="dac8f-171">Receive Pipeline</span></span>|<span data-ttu-id="dac8f-172">Détermine le pipeline à utiliser pour les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="dac8f-172">Determines which pipeline to use for incoming messages.</span></span>|  
        |<span data-ttu-id="dac8f-173">Pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="dac8f-173">Send Pipeline</span></span>|<span data-ttu-id="dac8f-174">Détermine le pipeline à utiliser pour les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="dac8f-174">Determines which pipeline to use for outgoing messages.</span></span>|  
        |<span data-ttu-id="dac8f-175">Transport</span><span class="sxs-lookup"><span data-stu-id="dac8f-175">Transport</span></span>|<span data-ttu-id="dac8f-176">Détermine le transport à utiliser pour envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="dac8f-176">Determines which transport to use for sending messages.</span></span>|  
        |<span data-ttu-id="dac8f-177">URI</span><span class="sxs-lookup"><span data-stu-id="dac8f-177">URI</span></span>|<span data-ttu-id="dac8f-178">Détermine l'emplacement d'envoi des messages.</span><span class="sxs-lookup"><span data-stu-id="dac8f-178">Determines where to send messages.</span></span>|  
  
### <a name="to-add-a-port-operation"></a><span data-ttu-id="dac8f-179">Pour ajouter une opération de port</span><span class="sxs-lookup"><span data-stu-id="dac8f-179">To add a port operation</span></span>  
  
-   <span data-ttu-id="dac8f-180">Cliquez sur le port auquel vous souhaitez ajouter une opération, puis cliquez sur **nouvelle opération**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-180">Right-click the port to which you want to add an operation, and then click **New Operation**.</span></span>  
  
### <a name="to-remove-a-port-operation"></a><span data-ttu-id="dac8f-181">Pour supprimer une opération de port</span><span class="sxs-lookup"><span data-stu-id="dac8f-181">To remove a port operation</span></span>  
  
-   <span data-ttu-id="dac8f-182">Avec le bouton droit de l’opération de port à supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="dac8f-182">Right-click the port operation to remove, and then click **Delete**.</span></span>