---
title: "Étape 2 : Envoi d’une 0c4 requête | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: ce50b892-c87c-414a-94c5-b40947fec68f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c621b6891b816f72603202bd6f2214882eb4b5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-submitting-a-0c4-query"></a><span data-ttu-id="d00ea-102">Étape 2 : Envoi d’un 0C de requête 4</span><span class="sxs-lookup"><span data-stu-id="d00ea-102">Step 2: Submitting a 0C4 Query</span></span>
<span data-ttu-id="d00ea-103">Au cours de cette étape, vous allez préparer une demande et l'envoyer à l'aide du processus d'interface entre partenaires (PIP) pour une requête de test synchrone 0C4.</span><span class="sxs-lookup"><span data-stu-id="d00ea-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 0C4 - Synchronous Test Query.</span></span> <span data-ttu-id="d00ea-104">RosettaNet définit ce processus PIP pour vérifier qu'un canal de communication synchrone fonctionne correctement entre deux organisations différentes.</span><span class="sxs-lookup"><span data-stu-id="d00ea-104">RosettaNet defines this PIP to make sure a successful synchronous communication channel is working correctly between two different organizations.</span></span> <span data-ttu-id="d00ea-105">Étant donné que ce processus PIP a un modèle de communication synchrone, [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] n’envoie pas d’accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="d00ea-105">Because this PIP has a synchronous communication pattern, [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] does not send receipt acknowledgements.</span></span> <span data-ttu-id="d00ea-106">Ce processus PIP suit le même modèle que les autres processus PIP double action synchrones, comme le processus PIP 2A9 (requête d'informations techniques sur un produit).</span><span class="sxs-lookup"><span data-stu-id="d00ea-106">This PIP follows the same pattern as other synchronous double action PIPs, such as PIP 2A9 - Query Technical Product Information.</span></span>  
  
### <a name="to-submit-a-0c4---synchronous-test-query"></a><span data-ttu-id="d00ea-107">Pour envoyer une requête de test synchrone 0C4</span><span class="sxs-lookup"><span data-stu-id="d00ea-107">To submit a 0C4 - Synchronous Test Query</span></span>  
  
1.  <span data-ttu-id="d00ea-108">Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.</span><span class="sxs-lookup"><span data-stu-id="d00ea-108">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="d00ea-109">Dans la page **Envoyer un Message** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d00ea-109">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="d00ea-110">Propriété</span><span class="sxs-lookup"><span data-stu-id="d00ea-110">Use this</span></span>|<span data-ttu-id="d00ea-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d00ea-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d00ea-112">**Organisation d’origine**</span><span class="sxs-lookup"><span data-stu-id="d00ea-112">**Home Organization**</span></span>|<span data-ttu-id="d00ea-113">Tapez **FABRIKAM**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-113">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="d00ea-114">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="d00ea-114">**Partner Organization**</span></span>|<span data-ttu-id="d00ea-115">Tapez **CONTOSO**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-115">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="d00ea-116">**Code PIP**</span><span class="sxs-lookup"><span data-stu-id="d00ea-116">**Pip Code**</span></span>|<span data-ttu-id="d00ea-117">Tapez **0C4**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-117">Type **0C4**.</span></span>|  
    |<span data-ttu-id="d00ea-118">**Version du PIP**</span><span class="sxs-lookup"><span data-stu-id="d00ea-118">**Pip Version**</span></span>|<span data-ttu-id="d00ea-119">Tapez **R01.02**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-119">Type **R01.02**.</span></span>|  
    |<span data-ttu-id="d00ea-120">**ID d’Instance PIP**</span><span class="sxs-lookup"><span data-stu-id="d00ea-120">**Pip Instance ID**</span></span>|<span data-ttu-id="d00ea-121">Tapez **0C4_Test**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-121">Type **0C4_Test**.</span></span> <span data-ttu-id="d00ea-122">**Important :** pour éviter les erreurs d’ID de message en double, vous devez vous assurer que le **PIP** est unique pour chaque message que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="d00ea-122">**Important:**  To avoid duplicate message ID errors, you must make sure that the **PIP** is unique for each message that you submit.</span></span> <span data-ttu-id="d00ea-123">Si vous exécutez le test 0C4 ultérieurement, vous devrez modifier ce champ.</span><span class="sxs-lookup"><span data-stu-id="d00ea-123">If you run the 0C4 test in the future, you will have to change this field.</span></span>|  
    |<span data-ttu-id="d00ea-124">**Catégorie de message**</span><span class="sxs-lookup"><span data-stu-id="d00ea-124">**Message Category**</span></span>|<span data-ttu-id="d00ea-125">Tapez **Action**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-125">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="d00ea-126">Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 0C4_Request.xml dans le  *\<lecteur\>*: \Program Files\Microsoft BizTalk 2009 Accelerator pour RosettaNet\SDK\LOBApplication\SampleInstances, dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="d00ea-126">Using Notepad or another text editor, open the 0C4_Request.xml file in the *\<drive\>*:\Program Files\Microsoft BizTalk 2009 Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
4.  <span data-ttu-id="d00ea-127">Cliquez sur **Envoyer** pour envoyer la requête 0C4 à l'ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="d00ea-127">Click **Submit** to submit the 0C4 query to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="d00ea-128">Pour vérifier la communication sur l'ordinateur Fabrikam</span><span class="sxs-lookup"><span data-stu-id="d00ea-128">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="d00ea-129">Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="d00ea-129">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d00ea-130">Vous devez recevoir un message de catégorie 50 qui correspond au message de réponse de l'ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="d00ea-130">You should receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="d00ea-131">Un message de catégorie -99 indique une erreur.</span><span class="sxs-lookup"><span data-stu-id="d00ea-131">A category -99 message signifies an error.</span></span> <span data-ttu-id="d00ea-132">Vous pouvez utiliser l'Observateur d'événements pour déterminer le message d'erreur réel.</span><span class="sxs-lookup"><span data-stu-id="d00ea-132">You can use the Event Viewer to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="d00ea-133">Pour vérifier la communication sur l'ordinateur Contoso</span><span class="sxs-lookup"><span data-stu-id="d00ea-133">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="d00ea-134">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2005**et cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-134">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="d00ea-135">Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-135">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d00ea-136">Si l’Agent SQL Server n’est pas démarré, faites un clic droit, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-136">If the SQL Server Agent is not started, right-click it, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="d00ea-137">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="d00ea-137">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="d00ea-138">Dans le \<table\> zone de texte, sélectionnez **BTARNDATA** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="d00ea-138">In the \<table\> text box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="d00ea-139">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="d00ea-139">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="d00ea-140">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="d00ea-140">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="d00ea-141">Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message entrant.</span><span class="sxs-lookup"><span data-stu-id="d00ea-141">In the Query window, in the Results pane, verify that you see one incoming message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d00ea-142">Vous devez voir un message de catégorie 10 qui correspond à la demande d'origine envoyée par l'ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="d00ea-142">You should see a category 10 message that represents the original request that the Fabrikam computer sent.</span></span>  
  
8.  <span data-ttu-id="d00ea-143">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="d00ea-143">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="d00ea-144">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="d00ea-144">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="d00ea-145">Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message sortant.</span><span class="sxs-lookup"><span data-stu-id="d00ea-145">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d00ea-146">Vous devez voir un message de catégorie 50 qui correspond à la réponse Contoso à la requête PIP 0C4 envoyée par Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="d00ea-146">You should see a category 50 message that represents the Contoso response to the PIP 0C4 query that Fabrikam sent.</span></span> <span data-ttu-id="d00ea-147">Dans un scénario synchrone double action, l'ordinateur récepteur n'envoie pas d'accusé de réception à l'ordinateur initiateur en réponse au message de requête initial.</span><span class="sxs-lookup"><span data-stu-id="d00ea-147">In a double action synchronous scenario, the responder computer does not send an acknowledgement to the initiator computer in response to the initial query message.</span></span> <span data-ttu-id="d00ea-148">Le message de réponse sert d'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="d00ea-148">The response message serves as the acknowledgement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d00ea-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d00ea-149">See Also</span></span>  
 <span data-ttu-id="d00ea-150">[Étape 3 : Envoi d’une demande de 3A2](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md) </span><span class="sxs-lookup"><span data-stu-id="d00ea-150">[Step 3: Submitting a 3A2 Request](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md) </span></span>  
 [<span data-ttu-id="d00ea-151">Flux de messages BTARN</span><span class="sxs-lookup"><span data-stu-id="d00ea-151">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)