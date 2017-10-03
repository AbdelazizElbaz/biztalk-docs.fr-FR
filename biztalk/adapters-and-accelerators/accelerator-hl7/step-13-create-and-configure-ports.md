---
title: "Étape 13 : Créer et configurer des Ports | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, creating
- message enrichment tutorial, ports
- creating, ports
- configuring, ports
- ports, configuring
ms.assetid: cc0540d7-46fc-4d9f-bcf3-0b0e0179fd51
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 256b1618313605f0847d9328abfd003f41ac61cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-13-create-and-configure-ports"></a><span data-ttu-id="40a09-102">Étape 13 : Créer et configurer des Ports</span><span class="sxs-lookup"><span data-stu-id="40a09-102">Step 13: Create and Configure Ports</span></span>
<span data-ttu-id="40a09-103">Dans cette étape, vous utilisez l’Assistant Configuration du Port pour créer et configurer des ports dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="40a09-103">In this step, you use the Port Configuration Wizard to create and configure ports in Orchestration Designer.</span></span> <span data-ttu-id="40a09-104">Ports indiquent comment votre orchestration envoie et reçoit des messages vers et depuis des processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="40a09-104">Ports specify how your orchestration sends and receives messages to and from business processes.</span></span> <span data-ttu-id="40a09-105">Chaque port a un type, une direction et une liaison.</span><span class="sxs-lookup"><span data-stu-id="40a09-105">Each port has a type, a direction, and a binding.</span></span> <span data-ttu-id="40a09-106">Les propriétés déterminent ensemble la direction de communication, le modèle de communication de l’emplacement vers ou à partir de laquelle [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] envoie ou reçoit le message, et comment la communication a lieu.</span><span class="sxs-lookup"><span data-stu-id="40a09-106">The properties together determine the direction of communication, the pattern of communication, the location to or from which [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] sends or receives the message, and how the communication takes place.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="40a09-107">utilise l’adaptateur minimale inférieure couche protocole (MLLP) comme un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="40a09-107"> uses the Minimum Lower Layer Protocol (MLLP) adapter as a send port.</span></span> <span data-ttu-id="40a09-108">L’adaptateur MLLP utilise les communications de sockets TCP pour interagir avec d’autres applications, telles que les applications de laboratoire, des applications d’assurance et les applications héritées line-of-business.</span><span class="sxs-lookup"><span data-stu-id="40a09-108">The MLLP adapter uses TCP sockets communication to interface with other applications, such as laboratory applications, insurance applications, and legacy line-of-business applications.</span></span> <span data-ttu-id="40a09-109">L’adaptateur d’envoi MLLP représente un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] carte :</span><span class="sxs-lookup"><span data-stu-id="40a09-109">The MLLP Send Adapter represents a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter that is:</span></span>  
  
-   <span data-ttu-id="40a09-110">Personnalisé.</span><span class="sxs-lookup"><span data-stu-id="40a09-110">Customized.</span></span> <span data-ttu-id="40a09-111">L’adaptateur est uniquement fourni avec [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], par opposition à l’envoi de journaux avec [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40a09-111">The adapter only ships with [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], as opposed to shipping with [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
-   <span data-ttu-id="40a09-112">Protocole/Transport.</span><span class="sxs-lookup"><span data-stu-id="40a09-112">Protocol/Transport.</span></span> <span data-ttu-id="40a09-113">La carte n’est pas un adaptateur de données ou application.</span><span class="sxs-lookup"><span data-stu-id="40a09-113">The adapter is not an application or data adapter.</span></span>  
  
-   <span data-ttu-id="40a09-114">Statique.</span><span class="sxs-lookup"><span data-stu-id="40a09-114">Static.</span></span> <span data-ttu-id="40a09-115">La configuration de l’adaptateur n’implique pas une interface utilisateur personnalisée.</span><span class="sxs-lookup"><span data-stu-id="40a09-115">The adapter configuration does not involve a custom user interface.</span></span>  
  
-   <span data-ttu-id="40a09-116">Asynchrone.</span><span class="sxs-lookup"><span data-stu-id="40a09-116">Asynchronous.</span></span> <span data-ttu-id="40a09-117">L’adaptateur ne bloque pas le thread du moteur de messagerie, ce qui permet d’améliorer les performances de toutes les cartes qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hôtes.</span><span class="sxs-lookup"><span data-stu-id="40a09-117">The adapter does not block the Messaging Engine thread, which enables increased performance of all adapters that [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hosts.</span></span>  
  
-   <span data-ttu-id="40a09-118">Non transactionnel.</span><span class="sxs-lookup"><span data-stu-id="40a09-118">Nontransacted.</span></span> <span data-ttu-id="40a09-119">L’adaptateur n’est pas une réception traitée ou envoyer [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] carte.</span><span class="sxs-lookup"><span data-stu-id="40a09-119">The adapter is not a transacted receive or send [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] adapter.</span></span>  
  
-   <span data-ttu-id="40a09-120">Régulière.</span><span class="sxs-lookup"><span data-stu-id="40a09-120">Regular.</span></span> <span data-ttu-id="40a09-121">L’adaptateur ne fonctionne pas dans un processus d’application distincte.</span><span class="sxs-lookup"><span data-stu-id="40a09-121">The adapter does not run in a separate application process.</span></span>  
  
-   <span data-ttu-id="40a09-122">Unidirectionnelles et bidirectionnelles.</span><span class="sxs-lookup"><span data-stu-id="40a09-122">Both One-Way and Two-Way.</span></span> <span data-ttu-id="40a09-123">L’adaptateur prend en charge unidirectionnelles et requête-réponse/avec sollicitation-réponse modes d’interaction.</span><span class="sxs-lookup"><span data-stu-id="40a09-123">The adapter supports both One-way and Request-Response/Solicit-Response modes of interaction.</span></span>  
  
 <span data-ttu-id="40a09-124">L’adaptateur MLLP peut envoyer des messages individuels ou envoyer des messages dans un lot.</span><span class="sxs-lookup"><span data-stu-id="40a09-124">The MLLP adapter can submit individual messages or submit messages in a batch.</span></span> <span data-ttu-id="40a09-125">Le début d’un message MLLP est marqué avec un caractère de wrapper, 0x0b hexadécimal (également connu sous le début de bloc ou SB caractère), et la fin du message est marquée par la combinaison d’un caractère 0x1c hexadécimal (également connu sous le caractère de fin de bloc ou EB) immédiatement suivis par le caractère 0x0d (retour chariot).</span><span class="sxs-lookup"><span data-stu-id="40a09-125">The beginning of an MLLP message is marked with a wrapper character, hexadecimal 0x0b (also known as the Start Block or SB character), and the end of the message is marked by the combination of a hexadecimal 0x1c character (also known as the End Block or EB character) immediately followed by the 0x0d character (Carriage Return).</span></span> <span data-ttu-id="40a09-126">Les compteurs de performance BTAHL7 comptent uniquement ces caractères de wrapper pour les messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="40a09-126">BTAHL7 performance counters only count these wrapper characters for sent messages.</span></span> <span data-ttu-id="40a09-127">Les compteurs de performance BTAHL7 ne comptent pas ces caractères de wrapper lors de la réception des messages.</span><span class="sxs-lookup"><span data-stu-id="40a09-127">BTAHL7 performance counters do not count these wrapper characters when receiving messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40a09-128">Le protocole MLLP standard n’autorise pas les caractères sous 0 x 20 dans la charge utile du message, car il interfère avec la possibilité de détecter les caractères SB et EB.</span><span class="sxs-lookup"><span data-stu-id="40a09-128">The MLLP protocol standard does not allow characters under 0x20 in the message payload because it interferes with the ability to detect the SB and EB characters.</span></span> <span data-ttu-id="40a09-129">Vous pouvez configurer les valeurs de caractère SB et EB, par conséquent, veillez à ne pas ce problème lorsque des modifications apportées.</span><span class="sxs-lookup"><span data-stu-id="40a09-129">You can configure the SB and EB character values, so be wary of this issue when making changes.</span></span>  
  
 <span data-ttu-id="40a09-130">Dans cette étape, vous configurez l’adaptateur MLLP et l’adaptateur SOAP.</span><span class="sxs-lookup"><span data-stu-id="40a09-130">In this step, you configure the MLLP adapter and SOAP adapter.</span></span>  
  
### <a name="to-create-and-configure-the-ports"></a><span data-ttu-id="40a09-131">Pour créer et configurer les ports</span><span class="sxs-lookup"><span data-stu-id="40a09-131">To create and configure the ports</span></span>  
  
1.  <span data-ttu-id="40a09-132">Dans le Concepteur d’Orchestration, faites glisser le **Port** mettre en forme à partir de la boîte à outils vers la Surface du Port sur le côté gauche de la surface en mode conception et déposez-la afin qu’il s’aligne horizontalement avec la **DoorbellReceive** forme.</span><span class="sxs-lookup"><span data-stu-id="40a09-132">In Orchestration Designer, drag the **Port** shape from the Toolbox to the Port Surface on the left side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellReceive** shape.</span></span>  
  
2.  <span data-ttu-id="40a09-133">Dans le **Assistant Configuration du Port**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="40a09-133">In the **Port Configuration Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="40a09-134">Sur le **propriétés de Port** page, dans le **nom** , tapez **SOAPReceivePort**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="40a09-134">On the **Port Properties** page, in the **Name** field, type **SOAPReceivePort**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="40a09-135">Sur le **sélectionner un Type de Port** page, entrez les informations suivantes, puis cliquez sur **suivant** pour continuer.</span><span class="sxs-lookup"><span data-stu-id="40a09-135">On the **Select a Port Type** page, enter the following information, and then click **Next** to continue.</span></span>  
  
    |<span data-ttu-id="40a09-136">Utiliser</span><span class="sxs-lookup"><span data-stu-id="40a09-136">Use this</span></span>|<span data-ttu-id="40a09-137">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="40a09-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="40a09-138">**Nom de Type de port**</span><span class="sxs-lookup"><span data-stu-id="40a09-138">**Port Type Name**</span></span>|<span data-ttu-id="40a09-139">Type **SOAPReceivePortType**.</span><span class="sxs-lookup"><span data-stu-id="40a09-139">Type **SOAPReceivePortType**.</span></span>|  
    |<span data-ttu-id="40a09-140">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="40a09-140">**Communication Pattern**</span></span>|<span data-ttu-id="40a09-141">Sélectionnez **unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="40a09-141">Select **One-Way**.</span></span>|  
    |<span data-ttu-id="40a09-142">**Restrictions d’accès**</span><span class="sxs-lookup"><span data-stu-id="40a09-142">**Access Restrictions**</span></span>|<span data-ttu-id="40a09-143">Sélectionnez **Public - aucune limite**.</span><span class="sxs-lookup"><span data-stu-id="40a09-143">Select **Public - no limit**.</span></span>|  
  
5.  <span data-ttu-id="40a09-144">Sur le **liaison de Port** , cliquez sur **suivant** pour accepter les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="40a09-144">On the **Port Binding** page, click **Next** to accept the default values.</span></span>  
  
6.  <span data-ttu-id="40a09-145">Sur le **fin de l’Assistant Port** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="40a09-145">On the **Completing the Port Wizard** page, click **Finish**.</span></span>  
  
7.  <span data-ttu-id="40a09-146">Faites glisser le **Port** mettre en forme à partir de la boîte à outils vers la Surface du Port sur le côté droit de la surface en mode conception et déposez-la afin qu’il s’aligne horizontalement avec la **DoorbellSend** forme.</span><span class="sxs-lookup"><span data-stu-id="40a09-146">Drag the **Port** shape from the Toolbox to the Port Surface on the right side of the Design view surface, and drop the shape so that it aligns horizontally with the **DoorbellSend** shape.</span></span>  
  
8.  <span data-ttu-id="40a09-147">À l’aide de la **Assistant Configuration du Port** comme vous l’avez fait dans les étapes 2 à 7, créez un port d’envoi supplémentaires avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="40a09-147">Using the **Port Configuration Wizard** as you did in steps 2 through 7, create an additional send port using the following parameters:</span></span>  
  
    |<span data-ttu-id="40a09-148">Propriété</span><span class="sxs-lookup"><span data-stu-id="40a09-148">Property</span></span>|<span data-ttu-id="40a09-149">Paramètre</span><span class="sxs-lookup"><span data-stu-id="40a09-149">Parameter</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="40a09-150">**Nom des propriétés de port**</span><span class="sxs-lookup"><span data-stu-id="40a09-150">**Port Properties Name**</span></span>|<span data-ttu-id="40a09-151">MLLPSendPort</span><span class="sxs-lookup"><span data-stu-id="40a09-151">MLLPSendPort</span></span>|  
    |<span data-ttu-id="40a09-152">**Nom de Type de port**</span><span class="sxs-lookup"><span data-stu-id="40a09-152">**Port Type Name**</span></span>|<span data-ttu-id="40a09-153">MLLPSendPortType</span><span class="sxs-lookup"><span data-stu-id="40a09-153">MLLPSendPortType</span></span>|  
    |<span data-ttu-id="40a09-154">**Modèle de communication**</span><span class="sxs-lookup"><span data-stu-id="40a09-154">**Communication Pattern**</span></span>|<span data-ttu-id="40a09-155">Unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="40a09-155">One-Way</span></span>|  
    |<span data-ttu-id="40a09-156">**Restrictions d’accès**</span><span class="sxs-lookup"><span data-stu-id="40a09-156">**Access Restrictions**</span></span>|<span data-ttu-id="40a09-157">Public - aucune limite</span><span class="sxs-lookup"><span data-stu-id="40a09-157">Public - no limit</span></span>|  
    |<span data-ttu-id="40a09-158">**Liaison de port**</span><span class="sxs-lookup"><span data-stu-id="40a09-158">**Port Binding**</span></span>|<span data-ttu-id="40a09-159">Spécifier plus tard</span><span class="sxs-lookup"><span data-stu-id="40a09-159">Specify Later</span></span>|  
    |<span data-ttu-id="40a09-160">**Direction de communication du port**</span><span class="sxs-lookup"><span data-stu-id="40a09-160">**Port direction of communication**</span></span>|<span data-ttu-id="40a09-161">Toujours envoyer les messages sur ce port.</span><span class="sxs-lookup"><span data-stu-id="40a09-161">I'll always be sending messages on this port.</span></span>|  
  
9. <span data-ttu-id="40a09-162">Dans le **Vue Orchestration** fenêtre, avec les **Types**, **les Types de Ports**, et **SOAPReceivePortType** nœuds développés, développez  **Operation_1**, puis cliquez sur **demande**.</span><span class="sxs-lookup"><span data-stu-id="40a09-162">In the **Orchestration View** window, with the **Types**, **Ports Types**, and **SOAPReceivePortType** nodes expanded, expand **Operation_1**, and then click **Request**.</span></span>  
  
10. <span data-ttu-id="40a09-163">Dans le **propriétés** fenêtre, dans la liste déroulante pour **Type de Message**, développez **schémas**, puis cliquez sur **BTAHL7_Project.Doorbell** .</span><span class="sxs-lookup"><span data-stu-id="40a09-163">In the **Properties** window, in the drop-down list for **Message Type**, expand **Schemas**, and then click **BTAHL7_Project.Doorbell**.</span></span>  
  
11. <span data-ttu-id="40a09-164">Dans le **Vue Orchestration** fenêtre, développez **MLLPSendPortType**, développez **Operation_1**, puis cliquez sur **demande**.</span><span class="sxs-lookup"><span data-stu-id="40a09-164">In the **Orchestration View** window, expand **MLLPSendPortType**, expand **Operation_1**, and then click **Request**.</span></span>  
  
12. <span data-ttu-id="40a09-165">Dans le **propriétés** fenêtre, dans la liste déroulante pour **Type de Message**, développez **Types Message à parties multiples**, puis cliquez sur **BTAHL7_ Project.DoorbellFinalMessageType**.</span><span class="sxs-lookup"><span data-stu-id="40a09-165">In the **Properties** window, in the drop-down list for **Message Type**, expand **Multi-part Message Types**, and then click **BTAHL7_Project.DoorbellFinalMessageType**.</span></span>  
  
13. <span data-ttu-id="40a09-166">Dans le **nom** , tapez **réponse**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="40a09-166">In the **Name** field, type **Response**, then press **Enter**.</span></span>  
  
14. <span data-ttu-id="40a09-167">Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellReceive** forme action.</span><span class="sxs-lookup"><span data-stu-id="40a09-167">On the orchestration Design view surface, click the **DoorbellReceive** action shape.</span></span>  
  
15. <span data-ttu-id="40a09-168">Dans le **propriétés** fenêtre, dans la liste déroulante pour **Message**, sélectionnez **DoorbellInputMessage**.</span><span class="sxs-lookup"><span data-stu-id="40a09-168">In the **Properties** window, in the drop-down list for **Message**, select **DoorbellInputMessage**.</span></span>  
  
16. <span data-ttu-id="40a09-169">Sur la surface en mode Design d’orchestration, cliquez sur le **DoorbellSend** forme.</span><span class="sxs-lookup"><span data-stu-id="40a09-169">On the orchestration Design view surface, click the **DoorbellSend** shape.</span></span>  
  
17. <span data-ttu-id="40a09-170">Dans le **propriétés** fenêtre, dans la liste déroulante pour **Message**, sélectionnez **DoorbellFinalMessage**.</span><span class="sxs-lookup"><span data-stu-id="40a09-170">In the **Properties** window, in the drop-down list for **Message**, select **DoorbellFinalMessage**.</span></span>  
  
18. <span data-ttu-id="40a09-171">Cliquez sur la poignée verte dans la **SOAPReceivePort** et faites-le glisser vers la poignée verte le **DoorbellReceive** réception shape pour se connecter le **SOAPReceivePort** à la  **DoorbellReceive** forme réception.</span><span class="sxs-lookup"><span data-stu-id="40a09-171">Click the green handle in the **SOAPReceivePort** and drag it to the green handle on the **DoorbellReceive** receive shape to connect the **SOAPReceivePort** to the **DoorbellReceive** receive shape.</span></span>  
  
19. <span data-ttu-id="40a09-172">Cliquez sur la poignée verte dans la **DoorbellSend** mettre en forme et faites-la glisser sur la poignée verte sur le **MLLPSendPort** port à connecter le **DoorbellSend** forme envoi pour le **MLLPSendPort** port.</span><span class="sxs-lookup"><span data-stu-id="40a09-172">Click the green handle in the **DoorbellSend** shape and drag it to the green handle on the **MLLPSendPort** port to connect the **DoorbellSend** send shape to the **MLLPSendPort** port.</span></span>  
  
20. <span data-ttu-id="40a09-173">Cliquez sur le **l’Explorateur de solutions** onglet sous la vue Orchestration.</span><span class="sxs-lookup"><span data-stu-id="40a09-173">Click the **Solution Explorer** tab under the Orchestration View.</span></span>  
  
21. <span data-ttu-id="40a09-174">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V22Common**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="40a09-174">In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Build**.</span></span> <span data-ttu-id="40a09-175">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="40a09-175">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40a09-176">Si aucun message de réussite s’affiche, résolvez les problèmes de la solution.</span><span class="sxs-lookup"><span data-stu-id="40a09-176">If no success message appears, troubleshoot the solution.</span></span>  
  
22. <span data-ttu-id="40a09-177">Avec le bouton droit **BTAHL7 projet**, puis cliquez sur **déployer** pour déployer le projet de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="40a09-177">Right-click **BTAHL7 Project**, and click **Deploy** to deploy the BTAHL7 project.</span></span>  
  
 <span data-ttu-id="40a09-178">Passez à [étape 14 : publier l’Orchestration en tant que Service Web](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="40a09-178">Proceed to [Step 14: Publish the Orchestration as a Web Service](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a09-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40a09-179">See Also</span></span>  
 [<span data-ttu-id="40a09-180">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="40a09-180">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)