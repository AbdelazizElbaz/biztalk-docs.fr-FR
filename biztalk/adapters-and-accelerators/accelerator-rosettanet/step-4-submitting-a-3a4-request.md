---
title: "Étape 4 : Envoi d’une demande de 3 a 4 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 2d812cbc-51bc-48d5-b0b2-3698d33664ec
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2436d33033163b32c4ead0fdab807b7db0b0158f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-submitting-a-3a4-request"></a><span data-ttu-id="e1ce6-102">Étape 4 : Envoi d’une demande de 3 a 4</span><span class="sxs-lookup"><span data-stu-id="e1ce6-102">Step 4: Submitting a 3A4 Request</span></span>
<span data-ttu-id="e1ce6-103">Dans cette étape, vous préparez et soumettez une demande à l’aide du processus PIP (Partner Interface) pour un 3 a 4 - demande de bon de commande.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 3A4 - Request Purchase Order.</span></span> <span data-ttu-id="e1ce6-104">Ce processus PIP permet à une organisation de l’acheteur soumettre une demande de bon de commande à un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-104">This PIP enables a buyer organization to submit a purchase order request to a supplier.</span></span> <span data-ttu-id="e1ce6-105">En règle générale, vous demandez le 3 a 4 - demande de bon de commande après l’exécution d’une requête de disponibilité de produit à l’aide de la 3A2 - demande de prix et disponibilité PIP.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-105">Generally, you request the 3A4 - Request Purchase Order after running a product availability query using the 3A2 - Request Price and Availability PIP.</span></span> <span data-ttu-id="e1ce6-106">Le PIP 3 a 4 est une adresse PIP asynchrone qui envoie les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-106">The 3A4 PIP is an asynchronous PIP that sends receipt acknowledgements.</span></span>  
  
 <span data-ttu-id="e1ce6-107">![&#60; Aucune modification &#62; ] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a4flow.gif "RN3_Intro_EETut_3A4Flow")</span><span class="sxs-lookup"><span data-stu-id="e1ce6-107">![&#60;No Change&#62;](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a4flow.gif "RN3_Intro_EETut_3A4Flow")</span></span>  
  
### <a name="to-submit-a-3a4---request-purchase-order"></a><span data-ttu-id="e1ce6-108">Pour soumettre un 3 a 4 - demande de bon de commande</span><span class="sxs-lookup"><span data-stu-id="e1ce6-108">To submit a 3A4 - Request Purchase Order</span></span>  
  
1.  <span data-ttu-id="e1ce6-109">Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-109">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="e1ce6-110">Dans la page **Envoyer un Message** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e1ce6-110">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="e1ce6-111">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-111">**Use this**</span></span>|<span data-ttu-id="e1ce6-112">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="e1ce6-113">**Organisation d’origine**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-113">**Home Organization**</span></span>|<span data-ttu-id="e1ce6-114">Tapez **FABRIKAM**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-114">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="e1ce6-115">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-115">**Partner Organization**</span></span>|<span data-ttu-id="e1ce6-116">Type **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-116">Type **Contoso**.</span></span>|  
    |<span data-ttu-id="e1ce6-117">**Code PIP**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-117">**Pip Code**</span></span>|<span data-ttu-id="e1ce6-118">Type **3 a 4**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-118">Type **3A4**.</span></span>|  
    |<span data-ttu-id="e1ce6-119">**Version du PIP**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-119">**Pip Version**</span></span>|<span data-ttu-id="e1ce6-120">Type **V02.02.00**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-120">Type **V02.02.00**.</span></span>|  
    |<span data-ttu-id="e1ce6-121">**ID d’Instance PIP**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-121">**Pip Instance ID**</span></span>|<span data-ttu-id="e1ce6-122">Type **3A4_Test**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-122">Type **3A4_Test**.</span></span> <span data-ttu-id="e1ce6-123">**Important :** pour éviter les erreurs d’ID de message en double, vous devez vous assurer que le **ID d’Instance Pip** est unique pour chaque message que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-123">**Important:**  To avoid duplicate message ID errors, you must make sure that the **Pip Instance ID** is unique for each message that you submit.</span></span> <span data-ttu-id="e1ce6-124">Si vous exécutez le test de 3 a 4 dans le futur, vous devrez modifier ce champ.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-124">If you run the 3A4 test in the future, you will have to change this field.</span></span>|  
    |<span data-ttu-id="e1ce6-125">**Catégorie de message**</span><span class="sxs-lookup"><span data-stu-id="e1ce6-125">**Message Category**</span></span>|<span data-ttu-id="e1ce6-126">Tapez **Action**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-126">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="e1ce6-127">Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 3A4_Request.xml dans le \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBApplication\ SampleInstances dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-127">Using Notepad or another text editor, open the 3A4_Request.xml file in the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
4.  <span data-ttu-id="e1ce6-128">Cliquez sur **Submit** pour envoyer la demande de 3 a 4 à l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-128">Click **Submit** to submit the 3A4 request to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="e1ce6-129">Pour vérifier la communication sur l'ordinateur Fabrikam</span><span class="sxs-lookup"><span data-stu-id="e1ce6-129">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="e1ce6-130">Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-130">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1ce6-131">Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-131">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="e1ce6-132">Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-132">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="e1ce6-133">Un message de catégorie -99 indique une erreur.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-133">A category -99 message signifies an error.</span></span> <span data-ttu-id="e1ce6-134">Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-134">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="e1ce6-135">Pour vérifier la communication sur l'ordinateur Contoso</span><span class="sxs-lookup"><span data-stu-id="e1ce6-135">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="e1ce6-136">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-136">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="e1ce6-137">Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-137">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="e1ce6-138">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-138">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="e1ce6-139">Dans le \<table > boîte de dialogue texte, sélectionnez **BTARNDATA** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-139">In the \<table> text dialog box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="e1ce6-140">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="e1ce6-140">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="e1ce6-141">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-141">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="e1ce6-142">Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-142">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1ce6-143">Vous devez tout d’abord recevoir un message de catégorie 10 qui représente la demande d’origine envoyée par l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-143">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="e1ce6-144">Vous devez ensuite recevoir un message de catégorie 25, ce qui signifie le message acknowledegment de réception.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-144">You should then receive a category 25 message signifying the receipt acknowledegment message.</span></span>  
  
8.  <span data-ttu-id="e1ce6-145">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="e1ce6-145">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="e1ce6-146">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-146">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="e1ce6-147">Dans la fenêtre de requête, dans le **résultats** volet, vérifiez que vous voyez un message sortant.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-147">In the Query window, in the **Results** pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1ce6-148">Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-148">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="e1ce6-149">Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-149">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ce6-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1ce6-150">See Also</span></span>  
 <span data-ttu-id="e1ce6-151">[Didacticiel double Action](../../adapters-and-accelerators/accelerator-rosettanet/double-action-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="e1ce6-151">[Double Action Tutorial](../../adapters-and-accelerators/accelerator-rosettanet/double-action-tutorial.md) </span></span>  
 [<span data-ttu-id="e1ce6-152">Flux de messages de BTARN</span><span class="sxs-lookup"><span data-stu-id="e1ce6-152">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)