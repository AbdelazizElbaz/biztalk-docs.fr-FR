---
title: "Étape 3 : Envoi d’une demande de 3A2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 09f22be8-6d7d-48bf-862b-73248bae0506
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 312e5980636d211f1e023331826e016eb141eb4b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-submitting-a-3a2-request"></a><span data-ttu-id="19196-102">Étape 3 : Envoi d’une demande de 3A2</span><span class="sxs-lookup"><span data-stu-id="19196-102">Step 3: Submitting a 3A2 Request</span></span>
<span data-ttu-id="19196-103">Dans cette étape, vous préparez et soumettez une demande à l’aide du processus PIP (Partner Interface) pour un 3A2 - demande de prix et disponibilité.</span><span class="sxs-lookup"><span data-stu-id="19196-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for a 3A2 - Request Price and Availability.</span></span> <span data-ttu-id="19196-104">Ce processus PIP permet à une organisation de l’acheteur obtenir des informations sur un produit donné, telles que le prix et le nombre d’unités disponibles.</span><span class="sxs-lookup"><span data-stu-id="19196-104">This PIP enables a buyer organization to obtain information about a certain product, such as price and number of available units.</span></span> <span data-ttu-id="19196-105">L’acheteur peut ensuite traiter ces informations via des règles d’entreprise pour déterminer si vous devez acheter le produit du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="19196-105">The buyer can then process that information through business rules to determine whether to purchase the product from the supplier.</span></span>  
  
### <a name="to-submit-a-3a2---request-price-and-availability"></a><span data-ttu-id="19196-106">Pour envoyer un 3A2 - demande de prix et disponibilité</span><span class="sxs-lookup"><span data-stu-id="19196-106">To submit a 3A2 - Request Price and Availability</span></span>  
  
1.  <span data-ttu-id="19196-107">Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.</span><span class="sxs-lookup"><span data-stu-id="19196-107">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="19196-108">Dans la page **Envoyer un Message** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="19196-108">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="19196-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="19196-109">Use this</span></span>|<span data-ttu-id="19196-110">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="19196-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="19196-111">**Organisation d’origine**</span><span class="sxs-lookup"><span data-stu-id="19196-111">**Home Organization**</span></span>|<span data-ttu-id="19196-112">Tapez **FABRIKAM**.</span><span class="sxs-lookup"><span data-stu-id="19196-112">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="19196-113">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="19196-113">**Partner Organization**</span></span>|<span data-ttu-id="19196-114">Type **Contoso**.</span><span class="sxs-lookup"><span data-stu-id="19196-114">Type **Contoso**.</span></span>|  
    |<span data-ttu-id="19196-115">**Code PIP**</span><span class="sxs-lookup"><span data-stu-id="19196-115">**Pip Code**</span></span>|<span data-ttu-id="19196-116">Type **3A2**.</span><span class="sxs-lookup"><span data-stu-id="19196-116">Type **3A2**.</span></span> <span data-ttu-id="19196-117">**Important :** pour éviter les erreurs d’ID de message en double, vous devez vous assurer que le **Pip** est unique pour chaque message que vous envoyez.</span><span class="sxs-lookup"><span data-stu-id="19196-117">**Important:**  To avoid duplicate message ID errors, you must make sure that the **Pip** is unique for each message that you submit.</span></span> <span data-ttu-id="19196-118">Si vous exécutez le test 3A2 à l’avenir, vous devez modifier ce champ.</span><span class="sxs-lookup"><span data-stu-id="19196-118">If you run the 3A2 test in the future, you have to change this field.</span></span>|  
    |<span data-ttu-id="19196-119">**Version du PIP**</span><span class="sxs-lookup"><span data-stu-id="19196-119">**Pip Version**</span></span>|<span data-ttu-id="19196-120">Type **R02.00.00A**.</span><span class="sxs-lookup"><span data-stu-id="19196-120">Type **R02.00.00A**.</span></span>|  
    |<span data-ttu-id="19196-121">**ID d’Instance PIP**</span><span class="sxs-lookup"><span data-stu-id="19196-121">**Pip Instance ID**</span></span>|<span data-ttu-id="19196-122">Type **3A2_Test**.</span><span class="sxs-lookup"><span data-stu-id="19196-122">Type **3A2_Test**.</span></span>|  
    |<span data-ttu-id="19196-123">**Catégorie de message**</span><span class="sxs-lookup"><span data-stu-id="19196-123">**Message Category**</span></span>|<span data-ttu-id="19196-124">Tapez **Action**.</span><span class="sxs-lookup"><span data-stu-id="19196-124">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="19196-125">Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 3A2_Request.xml dans le  *\<lecteur\>*: \ Programme Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances, dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="19196-125">Using Notepad or another text editor, open the file 3A2_Request.xml in the *\<drive\>*:\ Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
4.  <span data-ttu-id="19196-126">Cliquez sur **Submit** pour envoyer la demande 3A2 à l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="19196-126">Click **Submit** to submit the 3A2 request to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="19196-127">Pour vérifier la communication sur l'ordinateur Fabrikam</span><span class="sxs-lookup"><span data-stu-id="19196-127">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="19196-128">Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="19196-128">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19196-129">Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="19196-129">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="19196-130">Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="19196-130">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="19196-131">Un message de catégorie -99 indique une erreur.</span><span class="sxs-lookup"><span data-stu-id="19196-131">A category -99 message signifies an error.</span></span> <span data-ttu-id="19196-132">Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="19196-132">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="19196-133">Pour vérifier la communication sur l'ordinateur Contoso</span><span class="sxs-lookup"><span data-stu-id="19196-133">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="19196-134">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="19196-134">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="19196-135">Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="19196-135">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="19196-136">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="19196-136">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="19196-137">Dans le \<table\> zone de texte, sélectionnez **BTARNDATA** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="19196-137">In the \<table\> text box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="19196-138">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="19196-138">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="19196-139">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="19196-139">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="19196-140">Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="19196-140">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19196-141">Vous devez tout d’abord recevoir un message de catégorie 10 qui représente la demande d’origine envoyée par l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="19196-141">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="19196-142">Vous devez ensuite recevoir un message de catégorie 25, ce qui signifie l’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="19196-142">You should then receive a category 25 message signifying the receipt acknowledgement message.</span></span>  
  
8.  <span data-ttu-id="19196-143">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="19196-143">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="19196-144">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="19196-144">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="19196-145">Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message sortant.</span><span class="sxs-lookup"><span data-stu-id="19196-145">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19196-146">Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="19196-146">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="19196-147">Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="19196-147">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19196-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19196-148">See Also</span></span>  
 <span data-ttu-id="19196-149">[Étape 4 : Envoi d’une demande de 3 a 4](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md) </span><span class="sxs-lookup"><span data-stu-id="19196-149">[Step 4: Submitting a 3A4 Request](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md) </span></span>  
 [<span data-ttu-id="19196-150">Flux de messages BTARN</span><span class="sxs-lookup"><span data-stu-id="19196-150">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)