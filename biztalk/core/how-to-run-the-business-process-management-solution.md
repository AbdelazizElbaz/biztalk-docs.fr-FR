---
title: "Comment exécuter la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, validating
- process management solution tutorial, submitting orders
- process management solution tutorial, stopping orders
- process management solution tutorial, updating orders
ms.assetid: cb77651e-e16c-49dc-9f8a-88584cd68a8b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3997fb18e7498ab2bc5f8c77b53740fb87ab6f93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-run-the-business-process-management-solution"></a><span data-ttu-id="af157-102">Exécution de la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="af157-102">How to Run the Business Process Management Solution</span></span>
<span data-ttu-id="af157-103">Les procédures suivantes décrivent l'exécution et la validation d'une solution de gestion des processus d'entreprise sur un seul ordinateur.</span><span class="sxs-lookup"><span data-stu-id="af157-103">The following steps describe how to run and validate the Business Process Management solution on a single computer.</span></span>  
  
-   [<span data-ttu-id="af157-104">Démarrer la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="af157-104">Start the Business Process Management Solution</span></span>](#step1)  
  
-   [<span data-ttu-id="af157-105">Exécution et la validation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="af157-105">Run and validate the Business Process Management Solution</span></span>](#step3)  
  
## <a name="prerequisites"></a><span data-ttu-id="af157-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="af157-106">Prerequisites</span></span>  
 <span data-ttu-id="af157-107">Avant d’exécuter la solution de gestion des processus métiers, vous devez effectuer les étapes de [l’installation de la Solution de gestion des processus métier](../core/how-to-install-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="af157-107">Before running the BPM solution, you must perform the steps in [How to Install the Business Process Management Solution](../core/how-to-install-the-business-process-management-solution.md).</span></span>  
  
##  <a name="step1"></a><span data-ttu-id="af157-108">Démarrer la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="af157-108">Start the Business Process Management Solution</span></span>  
  
#### <a name="to-start-the-business-process-management-solution"></a><span data-ttu-id="af157-109">Pour démarrer la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="af157-109">To start the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="af157-110">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="af157-110">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="af157-111">Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, développez **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="af157-111">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Platform Settings**, expand **Host Instances**, right-click **BizTalkServerApplication**, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="af157-112">Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="af157-112">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
    1.  <span data-ttu-id="af157-113">Sur BTSScn.BPM.MessagingApp, cliquez **Démarrer**, puis cliquez sur **Démarrer** sur la **démarrer l’Application** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="af157-113">Right-click BTSScn.BPM.MessagingApp, click **Start**, and then click **Start** on the **Start Application** dialog box.</span></span>  
  
    2.  <span data-ttu-id="af157-114">Sur BTSScn.BPM.OrderBrokerApp, cliquez **Démarrer**, puis cliquez sur **Démarrer** sur la **démarrer l’Application** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="af157-114">Right-click BTSScn.BPM.OrderBrokerApp, click **Start**, and then click **Start** on the **Start Application** dialog box.</span></span>  
  
    3.  <span data-ttu-id="af157-115">Sur BTSScn.BPM.CableOrderApp, cliquez **Démarrer**, puis cliquez sur **Démarrer** sur la **démarrer l’Application** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="af157-115">Right-click BTSScn.BPM.CableOrderApp, click **Start**, and then click **Start** on the **Start Application** dialog box.</span></span>  
  
    4.  <span data-ttu-id="af157-116">Cliquez sur BTSScn.BPM.OrderBrokerApp.Test, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="af157-116">Right-click BTSScn.BPM.OrderBrokerApp.Test, and click **Stop**.</span></span> <span data-ttu-id="af157-117">Dans le **arrêter l’Application** boîte de dialogue, sélectionnez **arrêt complet - arrêter l’instance**, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="af157-117">In the **Stop Application** dialog box, select **Full Stop - Terminate instance**, and then click **Stop**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af157-118">Pour insérer des informations dans la base de données de l’historique.</span><span class="sxs-lookup"><span data-stu-id="af157-118">To insert information in the history database.</span></span> <span data-ttu-id="af157-119">l’orchestration OrderBroker utilise le port d’envoi historyport dont le **accusé de réception** propriété a la valeur **transmis**.</span><span class="sxs-lookup"><span data-stu-id="af157-119">the OrderBroker orchestration uses the HistoryPort send port of which the **Delivery Notification** property is set **Transmitted**.</span></span> <span data-ttu-id="af157-120">Le port d'envoi est lié au groupe d'envoi HistoryInsert-SPG qui inclut les ports d'envoi HistoryInsert-SP et HistoryInsert-Test-SP.</span><span class="sxs-lookup"><span data-stu-id="af157-120">The send port is bounded to the HistoryInsert-SPG send group which includes the HistoryInsert-SP and HistoryInsert-Test-SP send ports.</span></span> <span data-ttu-id="af157-121">Pour ces deux ports d'envoi, le moteur de messagerie publie deux accusés de réception sur l'orchestration OrderBroker.</span><span class="sxs-lookup"><span data-stu-id="af157-121">For these two send ports the message engine will publish two acknowledgment messages to the OrderBroker orchestration.</span></span> <span data-ttu-id="af157-122">Il interrompt l'orchestration en raison de messages non utilisés.</span><span class="sxs-lookup"><span data-stu-id="af157-122">It makes the orchestration suspended due to unconsumed messages.</span></span> <span data-ttu-id="af157-123">Pour éviter cette situation, vous devez désinscrire l'un des ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="af157-123">To avoid this situation, you must unenlist one of the send ports.</span></span> <span data-ttu-id="af157-124">Dans cette procédure pas à pas, désinscrivez le port d'envoi HistoryInsert-Test-SP en arrêtant complètement l'application BTSScn.BPM.OrderBrokerApp.Test.</span><span class="sxs-lookup"><span data-stu-id="af157-124">In this walkthrough, unenlist HistoryInsert-Test-SP send port by fully stopping the BTSScn.BPM.OrderBrokerApp.Test application.</span></span> <span data-ttu-id="af157-125">Pour plus d’informations sur l’orchestration OrderBroker, consultez [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="af157-125">For more information about the OrderBroker orchestration, see [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).</span></span> <span data-ttu-id="af157-126">Pour plus d’informations sur **accusé de réception** propriété, consultez [accusés de réception à l’aide de](../core/using-acknowledgments.md).</span><span class="sxs-lookup"><span data-stu-id="af157-126">For more information about **Delivery Notification** property, see [Using Acknowledgments](../core/using-acknowledgments.md).</span></span>  
  
4.  <span data-ttu-id="af157-127">Exécutez le simulateur d'installations comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-127">Run the Facilities Simulator as follows:</span></span>  
  
    1.  <span data-ttu-id="af157-128">Ouvrez une invite de commandes, accédez au dossier %BTSSolutionsPath%\BPM\FacilitiesSimulator\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="af157-128">Open a command prompt, change the directory to the %BTSSolutionsPath%\BPM\FacilitiesSimulator\bin\debug folder.</span></span>  
  
    2.  <span data-ttu-id="af157-129">Type `BTSScnBPMFacilities.exe`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="af157-129">Type `BTSScnBPMFacilities.exe`, and then press ENTER.</span></span> <span data-ttu-id="af157-130">Maintenez l'exécution du simulateur d'installations.</span><span class="sxs-lookup"><span data-stu-id="af157-130">Keep the FacilitiesSimulator running.</span></span> <span data-ttu-id="af157-131">Cette application simule les systèmes principaux de traitement des installations à Southridge Video.</span><span class="sxs-lookup"><span data-stu-id="af157-131">This application simulates the facilities processing back-end systems at Southridge Video.</span></span>  
  
    3.  <span data-ttu-id="af157-132">Dans le simulateur d'installations, tapez les files d'attente de réception et de transmission suivantes :</span><span class="sxs-lookup"><span data-stu-id="af157-132">In the FacilitiesSimulator, type the following receive and transmit queues:</span></span>  
  
        |<span data-ttu-id="af157-133">Nom</span><span class="sxs-lookup"><span data-stu-id="af157-133">Name</span></span>|<span data-ttu-id="af157-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="af157-134">Value</span></span>|  
        |----------|-----------|  
        |<span data-ttu-id="af157-135">**File d’attente de réception**</span><span class="sxs-lookup"><span data-stu-id="af157-135">**Receive Queue**</span></span>|`.\private$\ToFacilitiesQ`|  
        |<span data-ttu-id="af157-136">**File d’attente de transmission**</span><span class="sxs-lookup"><span data-stu-id="af157-136">**Transmit Queue**</span></span>|`.\private$\FromFacilitiesQ`|  
  
    4.  <span data-ttu-id="af157-137">Dans le simulateur d’installations, cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="af157-137">In the FacilitiesSimulator, Click **Start**.</span></span>  
  
5.  <span data-ttu-id="af157-138">Exécutez le serveur d'opérations comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-138">Run the Operation Server as follows:</span></span>  
  
    1.  <span data-ttu-id="af157-139">Ouvrez une nouvelle invite de commandes, accédez au dossier %BTSSolutionsPath%\BPM\OperationsServer\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="af157-139">Open a new command prompt, change the current directory to the %BTSSolutionsPath%\BPM\OperationsServer\bin\debug folder.</span></span>  
  
    2.  <span data-ttu-id="af157-140">Type `BTSScnBPMOperations.exe 8881` à l’invite de commandes et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="af157-140">Type `BTSScnBPMOperations.exe 8881` at the command prompt, and then press ENTER.</span></span> <span data-ttu-id="af157-141">Maintenez l'exécution du serveur d'opérations.</span><span class="sxs-lookup"><span data-stu-id="af157-141">Keep the Operation Server running.</span></span> <span data-ttu-id="af157-142">Le serveur d'opérations écoute sur le port TCP, 8881, pour recevoir des messages d'erreur de l'adaptateur Ops.</span><span class="sxs-lookup"><span data-stu-id="af157-142">The Operation Server listens on the TCP port, 8881, to receive error messages from the Ops Adapter.</span></span> <span data-ttu-id="af157-143">Il affiche les messages d'erreur reçus par l'adaptateur Ops.</span><span class="sxs-lookup"><span data-stu-id="af157-143">It displays the error messages received by the Ops Adapter.</span></span>  
  
6.  <span data-ttu-id="af157-144">Exécutez le système d'approvisionnement en câble comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-144">Run the Cable Provisioning System as follows:</span></span>  
  
    1.  <span data-ttu-id="af157-145">Ouvrez une nouvelle invite de commandes, accédez au dossier %BTSSolutionsPath%\BPM\CableProvisioningSystemServer\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="af157-145">Open a new command prompt, change the current directory to the %BTSSolutionsPath%\BPM\CableProvisioningSystemServer\bin\debug folder.</span></span>  
  
    2.  <span data-ttu-id="af157-146">Type `BTSScnBPMProvisioning.exe 8880`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="af157-146">Type `BTSScnBPMProvisioning.exe 8880`, and then press ENTER.</span></span> <span data-ttu-id="af157-147">Puis, maintenez l'exécution du système d'approvisionnement en câble.</span><span class="sxs-lookup"><span data-stu-id="af157-147">Then, keep the Cable Provisioning System running.</span></span> <span data-ttu-id="af157-148">Le système d'approvisionnement en câble écoute sur le port TCP, 8880.</span><span class="sxs-lookup"><span data-stu-id="af157-148">The Cable Provisioning System listens on the TCP port, 8880.</span></span> <span data-ttu-id="af157-149">Cette application simule un système de commande principal, puis affiche les commandes finales.</span><span class="sxs-lookup"><span data-stu-id="af157-149">This application simulates a back-end order system, and displays the final orders.</span></span>  
  
##  <a name="step3"></a><span data-ttu-id="af157-150">Exécution et la validation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="af157-150">Run and validate the Business Process Management Solution</span></span>  
  
#### <a name="to-submit-a-new-order-and-validate-the-solution"></a><span data-ttu-id="af157-151">Pour envoyer une nouvelle commande et valider la solution</span><span class="sxs-lookup"><span data-stu-id="af157-151">To submit a new order and validate the solution</span></span>  
  
1.  <span data-ttu-id="af157-152">Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-152">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="af157-153">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande.**</span><span class="sxs-lookup"><span data-stu-id="af157-153">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order.**</span></span>  
  
    |<span data-ttu-id="af157-154">Entrée</span><span class="sxs-lookup"><span data-stu-id="af157-154">Entry</span></span>|<span data-ttu-id="af157-155">Valeur</span><span class="sxs-lookup"><span data-stu-id="af157-155">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="af157-156">ID de client</span><span class="sxs-lookup"><span data-stu-id="af157-156">Customer ID</span></span>|<span data-ttu-id="af157-157">1</span><span class="sxs-lookup"><span data-stu-id="af157-157">1</span></span>|  
    |<span data-ttu-id="af157-158">Order ID</span><span class="sxs-lookup"><span data-stu-id="af157-158">Order ID</span></span>|<span data-ttu-id="af157-159">1</span><span class="sxs-lookup"><span data-stu-id="af157-159">1</span></span>|  
    |<span data-ttu-id="af157-160">Numéro de séquence</span><span class="sxs-lookup"><span data-stu-id="af157-160">Sequence Number</span></span>|<span data-ttu-id="af157-161">1</span><span class="sxs-lookup"><span data-stu-id="af157-161">1</span></span>|  
    |<span data-ttu-id="af157-162">Code du type de service</span><span class="sxs-lookup"><span data-stu-id="af157-162">Service Type Code</span></span>|<span data-ttu-id="af157-163">Nouveau service standard</span><span class="sxs-lookup"><span data-stu-id="af157-163">New Standard Service</span></span>|  
  
3.  <span data-ttu-id="af157-164">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-164">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="af157-165">**ID de commande client ID 1 1 numéro de séquence 1**</span><span class="sxs-lookup"><span data-stu-id="af157-165">**Customer ID 1 Order ID 1 Sequence Number 1**</span></span>  
  
4.  <span data-ttu-id="af157-166">Examinez la commande placée à l'invite de commandes exécutant le système d'approvisionnement en câble.</span><span class="sxs-lookup"><span data-stu-id="af157-166">Validate that the placed order at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="af157-167">L'application affiche les messages indiquant que la commande envoyée est analysée, activée, puis terminée.</span><span class="sxs-lookup"><span data-stu-id="af157-167">The application display the messages that the submitted order is analyzed, activated, and then completed.</span></span>  
  
5.  <span data-ttu-id="af157-168">Assurez-vous que le nombre total de messages est incrémenté d'un sur le simulateur d'installations.</span><span class="sxs-lookup"><span data-stu-id="af157-168">Validate that the number of the total messages is incremented by one on the Facilities Simulator.</span></span>  
  
#### <a name="to-submit-a-duplicate-while-the-biztalk-server-is-processing-the-original-order"></a><span data-ttu-id="af157-169">Pour envoyer une copie lorsque BizTalk Server traite la commande d'origine</span><span class="sxs-lookup"><span data-stu-id="af157-169">To submit a duplicate while the BizTalk Server is processing the original order</span></span>  
  
1.  <span data-ttu-id="af157-170">Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-170">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="af157-171">Dans le simulateur d’installations, cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="af157-171">In the FacilitiesSimulator, click **Stop**.</span></span> <span data-ttu-id="af157-172">Cela empêche les commandes envoyées de poursuivre leur traitement.</span><span class="sxs-lookup"><span data-stu-id="af157-172">It prevents submitted orders from being processed further.</span></span>  
  
3.  <span data-ttu-id="af157-173">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande** à deux reprises pour simuler des commandes en double.</span><span class="sxs-lookup"><span data-stu-id="af157-173">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order** twice to simulate duplicated orders.</span></span>  
  
    |<span data-ttu-id="af157-174">Entrée</span><span class="sxs-lookup"><span data-stu-id="af157-174">Entry</span></span>|<span data-ttu-id="af157-175">Valeur</span><span class="sxs-lookup"><span data-stu-id="af157-175">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="af157-176">ID de client</span><span class="sxs-lookup"><span data-stu-id="af157-176">Customer ID</span></span>|<span data-ttu-id="af157-177">2</span><span class="sxs-lookup"><span data-stu-id="af157-177">2</span></span>|  
    |<span data-ttu-id="af157-178">Order ID</span><span class="sxs-lookup"><span data-stu-id="af157-178">Order ID</span></span>|<span data-ttu-id="af157-179">1</span><span class="sxs-lookup"><span data-stu-id="af157-179">1</span></span>|  
    |<span data-ttu-id="af157-180">Numéro de séquence</span><span class="sxs-lookup"><span data-stu-id="af157-180">Sequence Number</span></span>|<span data-ttu-id="af157-181">1</span><span class="sxs-lookup"><span data-stu-id="af157-181">1</span></span>|  
    |<span data-ttu-id="af157-182">Code du type de service</span><span class="sxs-lookup"><span data-stu-id="af157-182">Service Type Code</span></span>|<span data-ttu-id="af157-183">Nouveau service standard</span><span class="sxs-lookup"><span data-stu-id="af157-183">New Standard Service</span></span>|  
  
4.  <span data-ttu-id="af157-184">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-184">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="af157-185">**ID de commande client ID 2 1 numéro de séquence 1**</span><span class="sxs-lookup"><span data-stu-id="af157-185">**Customer ID 2 Order ID 1 Sequence Number 1**</span></span>  
  
5.  <span data-ttu-id="af157-186">Dans le simulateur d’installations, cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="af157-186">In the FacilitiesSimulator, click **Start**.</span></span> <span data-ttu-id="af157-187">Les orchestrations en attente de réponses du simulateur d'installations reprennent.</span><span class="sxs-lookup"><span data-stu-id="af157-187">The orchestrations waiting for the responses from the Facilities Simulator will resume.</span></span> <span data-ttu-id="af157-188">Cela simule l'envoi d'une commande en double pendant le traitement de la première commande.</span><span class="sxs-lookup"><span data-stu-id="af157-188">It simulates that a duplicate order is submitted while the first order is being processed.</span></span>  
  
6.  <span data-ttu-id="af157-189">Examinez les commandes placées à l'invite de commandes exécutant le système d'approvisionnement en câble.</span><span class="sxs-lookup"><span data-stu-id="af157-189">Check the placed orders at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="af157-190">L'application affiche les messages indiquant que seule la première commande est analysée, activée, puis terminée.</span><span class="sxs-lookup"><span data-stu-id="af157-190">The application displays the messages that only the first order is analyzed, activated, and then completed.</span></span>  
  
7.  <span data-ttu-id="af157-191">Examinez le message d'erreur pour rechercher les commandes en double à l'invite de commandes exécutant le serveur d'opérations.</span><span class="sxs-lookup"><span data-stu-id="af157-191">Check the error message for the duplicated orders at the command prompt running the Operation Server.</span></span>  
  
#### <a name="to-update-an-order-while-the-biztalk-server-is-processing-the-order"></a><span data-ttu-id="af157-192">Pour mettre à jour une commande lorsque BizTalk Server traite la commande</span><span class="sxs-lookup"><span data-stu-id="af157-192">To update an order while the BizTalk Server is processing the order</span></span>  
  
1.  <span data-ttu-id="af157-193">Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-193">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="af157-194">Dans le simulateur d’installations, cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="af157-194">In the FacilitiesSimulator, click **Stop**.</span></span>  
  
3.  <span data-ttu-id="af157-195">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande**.</span><span class="sxs-lookup"><span data-stu-id="af157-195">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order**.</span></span>  
  
    |<span data-ttu-id="af157-196">Entrée</span><span class="sxs-lookup"><span data-stu-id="af157-196">Entry</span></span>|<span data-ttu-id="af157-197">Valeur</span><span class="sxs-lookup"><span data-stu-id="af157-197">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="af157-198">ID de client</span><span class="sxs-lookup"><span data-stu-id="af157-198">Customer ID</span></span>|<span data-ttu-id="af157-199">3</span><span class="sxs-lookup"><span data-stu-id="af157-199">3</span></span>|  
    |<span data-ttu-id="af157-200">Order ID</span><span class="sxs-lookup"><span data-stu-id="af157-200">Order ID</span></span>|<span data-ttu-id="af157-201">1</span><span class="sxs-lookup"><span data-stu-id="af157-201">1</span></span>|  
    |<span data-ttu-id="af157-202">Numéro de séquence</span><span class="sxs-lookup"><span data-stu-id="af157-202">Sequence Number</span></span>|<span data-ttu-id="af157-203">1</span><span class="sxs-lookup"><span data-stu-id="af157-203">1</span></span>|  
    |<span data-ttu-id="af157-204">Code du type de service</span><span class="sxs-lookup"><span data-stu-id="af157-204">Service Type Code</span></span>|<span data-ttu-id="af157-205">Nouveau service standard</span><span class="sxs-lookup"><span data-stu-id="af157-205">New Standard Service</span></span>|  
  
4.  <span data-ttu-id="af157-206">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-206">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="af157-207">**ID de commande client ID 3 1 numéro de séquence 1**</span><span class="sxs-lookup"><span data-stu-id="af157-207">**Customer ID 3 Order ID 1 Sequence Number 1**</span></span>  
  
5.  <span data-ttu-id="af157-208">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une commande de mise à jour dans le tableau suivant, puis cliquez sur **envoyer la commande**.</span><span class="sxs-lookup"><span data-stu-id="af157-208">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter an updated order in the following table, and then click **Submit Order**.</span></span>  
  
    |<span data-ttu-id="af157-209">Entrée</span><span class="sxs-lookup"><span data-stu-id="af157-209">Entry</span></span>|<span data-ttu-id="af157-210">Valeur</span><span class="sxs-lookup"><span data-stu-id="af157-210">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="af157-211">ID de client</span><span class="sxs-lookup"><span data-stu-id="af157-211">Customer ID</span></span>|<span data-ttu-id="af157-212">3</span><span class="sxs-lookup"><span data-stu-id="af157-212">3</span></span>|  
    |<span data-ttu-id="af157-213">Order ID</span><span class="sxs-lookup"><span data-stu-id="af157-213">Order ID</span></span>|<span data-ttu-id="af157-214">1</span><span class="sxs-lookup"><span data-stu-id="af157-214">1</span></span>|  
    |<span data-ttu-id="af157-215">Numéro de séquence</span><span class="sxs-lookup"><span data-stu-id="af157-215">Sequence Number</span></span>|<span data-ttu-id="af157-216">2</span><span class="sxs-lookup"><span data-stu-id="af157-216">2</span></span>|  
    |<span data-ttu-id="af157-217">Code du type de service</span><span class="sxs-lookup"><span data-stu-id="af157-217">Service Type Code</span></span>|<span data-ttu-id="af157-218">Nouveau service Deluxe</span><span class="sxs-lookup"><span data-stu-id="af157-218">New Deluxe Service</span></span>|  
  
6.  <span data-ttu-id="af157-219">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-219">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="af157-220">**ID de commande client ID 3 1 numéro de séquence 2**</span><span class="sxs-lookup"><span data-stu-id="af157-220">**Customer ID 3 Order ID 1 Sequence Number 2**</span></span>  
  
7.  <span data-ttu-id="af157-221">Dans le simulateur d’installations, cliquez sur **Démarrer**</span><span class="sxs-lookup"><span data-stu-id="af157-221">In the FacilitiesSimulator, click **Start**</span></span>  
  
8.  <span data-ttu-id="af157-222">Vérifiez le message de résultat sur la **formulaire entrée de commande Southridge Video client Service Rep** page.</span><span class="sxs-lookup"><span data-stu-id="af157-222">Check the result message on the **Southridge Video Customer Service Rep Order Entry Form** page.</span></span>  
  
9. <span data-ttu-id="af157-223">Examinez les commandes placées à l'invite de commandes exécutant le système d'approvisionnement en câble.</span><span class="sxs-lookup"><span data-stu-id="af157-223">Check the placed orders at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="af157-224">L'application affiche les messages indiquant que deux commandes sont analysées mais que seule la commande mise à jour est activée et terminée.</span><span class="sxs-lookup"><span data-stu-id="af157-224">The application displays the messages that two orders are analyzed, but only the updated order is activated and completed.</span></span>  
  
10. <span data-ttu-id="af157-225">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **Observateur d’événements**et vérifiez ensuite un nouveau avertissement qui le ordre d’origine a été interrompue.</span><span class="sxs-lookup"><span data-stu-id="af157-225">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Event Viewer**, and then check a new warning that the original order was interrupted.</span></span>  
  
11. <span data-ttu-id="af157-226">Examinez le message d'erreur d'échec de routage à l'invite de commandes exécutant le serveur d'opérations.</span><span class="sxs-lookup"><span data-stu-id="af157-226">Checked the routing failure error message at the command prompt running the Operation Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af157-227">Il y a une erreur dans le journal des événements et sur le serveur d'opérations.</span><span class="sxs-lookup"><span data-stu-id="af157-227">There will be an error in the event log and in the operations server.</span></span> <span data-ttu-id="af157-228">Le message de réponse du système d'installations n'est plus corrélé à une instance du processus d'entreprise car il a été terminé par l'interruption causée par la nouvelle commande avec un numéro de séquence supérieur.</span><span class="sxs-lookup"><span data-stu-id="af157-228">The response message from the Facilities System no longer correlates back to an instance of the business process as it was terminated by the interruption caused by the new order with a higher sequence number.</span></span> <span data-ttu-id="af157-229">Par conséquent, le message de réponse est orphelin et routé vers le serveur d'opérations.</span><span class="sxs-lookup"><span data-stu-id="af157-229">Therefore response message is orphaned and will get routed to the operations server.</span></span> <span data-ttu-id="af157-230">Pour plus d’informations sur les mises à jour, consultez [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md).</span><span class="sxs-lookup"><span data-stu-id="af157-230">For more information about order updates, see [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).</span></span>  
  
12. <span data-ttu-id="af157-231">Ouvrez le dernier message dans le dossier %SystemDrive%:\BPMTest\HistoryUpdate-SP dans le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="af157-231">Open the latest message in the %SystemDrive%:\BPMTest\HistoryUpdate-SP folder with Notepad.</span></span> <span data-ttu-id="af157-232">Vérifiez **CustName**, **OrderNum**, **OrderSeqNum**, et **état** champs pour voir si le message a été créé pour la nouvelle commande et le **État** champ est **terminé**.</span><span class="sxs-lookup"><span data-stu-id="af157-232">Check **CustName**, **OrderNum**, **OrderSeqNum**, and **Status** fields to see if the message has been created for the new order and the **Status** field is **COMPLETED**.</span></span>  
  
#### <a name="to-terminate-an-order-while-the-biztalk-server-is-processing-the-order"></a><span data-ttu-id="af157-233">Pour terminer une commande lorsque BizTalk Server traite la commande</span><span class="sxs-lookup"><span data-stu-id="af157-233">To terminate an order while the BizTalk Server is processing the order</span></span>  
  
1.  <span data-ttu-id="af157-234">Dans Internet Explorer, dans le **adresse** zone, tapez l’URL de l’application Web Service clientèle comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-234">In Internet Explorer, in the **Address** box, type the URL for the Customer Service Web application as following:</span></span>  
  
    -   `http://localhost/CSRWebApp/CSRMainForm.aspx`  
  
2.  <span data-ttu-id="af157-235">Dans le simulateur d’installations, cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="af157-235">In the FacilitiesSimulator, click **Stop**.</span></span>  
  
3.  <span data-ttu-id="af157-236">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, entrez une nouvelle commande dans le tableau suivant, puis cliquez sur **envoyer la commande**.</span><span class="sxs-lookup"><span data-stu-id="af157-236">On the **Southridge Video Customer Service Rep Order Entry Form** page, enter a new order in the following table, and then click **Submit Order**.</span></span>  
  
    |<span data-ttu-id="af157-237">Entrée</span><span class="sxs-lookup"><span data-stu-id="af157-237">Entry</span></span>|<span data-ttu-id="af157-238">Valeur</span><span class="sxs-lookup"><span data-stu-id="af157-238">Value</span></span>|  
    |-----------|-----------|  
    |<span data-ttu-id="af157-239">ID de client</span><span class="sxs-lookup"><span data-stu-id="af157-239">Customer ID</span></span>|<span data-ttu-id="af157-240">4</span><span class="sxs-lookup"><span data-stu-id="af157-240">4</span></span>|  
    |<span data-ttu-id="af157-241">Order ID</span><span class="sxs-lookup"><span data-stu-id="af157-241">Order ID</span></span>|<span data-ttu-id="af157-242">1</span><span class="sxs-lookup"><span data-stu-id="af157-242">1</span></span>|  
    |<span data-ttu-id="af157-243">Numéro de séquence</span><span class="sxs-lookup"><span data-stu-id="af157-243">Sequence Number</span></span>|<span data-ttu-id="af157-244">1</span><span class="sxs-lookup"><span data-stu-id="af157-244">1</span></span>|  
    |<span data-ttu-id="af157-245">Code du type de service</span><span class="sxs-lookup"><span data-stu-id="af157-245">Service Type Code</span></span>|<span data-ttu-id="af157-246">Nouveau service standard</span><span class="sxs-lookup"><span data-stu-id="af157-246">New Standard Service</span></span>|  
  
4.  <span data-ttu-id="af157-247">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-247">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="af157-248">**ID de commande client ID 4 1 numéro de séquence 1**</span><span class="sxs-lookup"><span data-stu-id="af157-248">**Customer ID 4 Order ID 1 Sequence Number 1**</span></span>  
  
5.  <span data-ttu-id="af157-249">Sur le **formulaire entrée de commande Southridge Video client Service Rep** , cliquez sur **terminer la commande**.</span><span class="sxs-lookup"><span data-stu-id="af157-249">On the **Southridge Video Customer Service Rep Order Entry Form** page, click **Terminate Order**.</span></span>  
  
6.  <span data-ttu-id="af157-250">Sur le **formulaire entrée de commande Southridge Video client Service Rep** page, le message de résultat comme suit :</span><span class="sxs-lookup"><span data-stu-id="af157-250">On the **Southridge Video Customer Service Rep Order Entry Form** page, the result message as follows:</span></span>  
  
     <span data-ttu-id="af157-251">**ID de commande client ID 4 1 numéro de séquence 1**</span><span class="sxs-lookup"><span data-stu-id="af157-251">**Customer ID 4 Order ID 1 Sequence Number 1**</span></span>  
  
7.  <span data-ttu-id="af157-252">Dans le simulateur d’installations, cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="af157-252">In the FacilitiesSimulator, click **Start**.</span></span>  
  
8.  <span data-ttu-id="af157-253">Examinez les commandes placées à l'invite de commandes exécutant le système d'approvisionnement en câble.</span><span class="sxs-lookup"><span data-stu-id="af157-253">Check the placed orders at the command prompt running the Cable Provisioning System.</span></span> <span data-ttu-id="af157-254">L'application affiche les messages indiquant que la commande est uniquement analysée et activée.</span><span class="sxs-lookup"><span data-stu-id="af157-254">The application displays the messages that order is only analyzed and activated.</span></span>  
  
9. <span data-ttu-id="af157-255">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **Observateur d’événements**et vérifiez ensuite un nouveau avertissement qui le commande a été arrêté par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="af157-255">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Event Viewer**, and then check a new warning that the order was terminated by user.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af157-256">Pour plus d’informations sur l’arrêt des commandes, consultez [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md).</span><span class="sxs-lookup"><span data-stu-id="af157-256">For more information about terminating orders, see [Order Flow through the Process Manager](../core/order-flow-through-the-process-manager.md).</span></span>  
  
10. <span data-ttu-id="af157-257">Examinez le message d'erreur d'échec de routage à l'invite de commandes exécutant le serveur d'opérations.</span><span class="sxs-lookup"><span data-stu-id="af157-257">Checked the routing failure error message at the command prompt running the Operation Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af157-258">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af157-258">See Also</span></span>  
 <span data-ttu-id="af157-259">[Avant d’installer la Solution gestion des processus d’entreprise](../core/before-installing-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="af157-259">[Before Installing the Business Process Management Solution](../core/before-installing-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="af157-260">Programme d’installation de développeur Machine pour la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="af157-260">Developer Machine Setup for the Business Process Management Solution</span></span>](../core/developer-machine-setup-for-the-business-process-management-solution.md)