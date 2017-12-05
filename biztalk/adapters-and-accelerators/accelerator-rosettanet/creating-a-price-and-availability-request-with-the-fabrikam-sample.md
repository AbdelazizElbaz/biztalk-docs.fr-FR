---
title: "Création d’un prix et la disponibilité de demande avec l’exemple Fabrikam | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating requests
ms.assetid: 6e4f4589-8f01-4b9e-93ee-c9371f32e04a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0619dc77496fd1547505221ff2f437bf486fb8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-price-and-availability-request-with-the-fabrikam-sample"></a><span data-ttu-id="ddf67-102">Création d’un prix et la demande de disponibilité avec l’exemple Fabrikam</span><span class="sxs-lookup"><span data-stu-id="ddf67-102">Creating a Price and Availability Request with the Fabrikam Sample</span></span>
<span data-ttu-id="ddf67-103">Dans cette étape, vous créez une demande de prix et de disponibilité 3A2 à l’aide de l’outil LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="ddf67-103">In this step, you create a 3A2 Price and Availability request using the LOBWebApplication tool.</span></span>  
  
### <a name="to-submit-a-3a2-price-and-availability-request-to-contoso"></a><span data-ttu-id="ddf67-104">Pour envoyer une demande de prix et de disponibilité 3A2 à Contoso</span><span class="sxs-lookup"><span data-stu-id="ddf67-104">To submit a 3A2 Price and Availability request to Contoso</span></span>  
  
1.  <span data-ttu-id="ddf67-105">Dans Internet Explorer, accédez à http://\<*fabrikam_computername*\>/LOBWebApplication/default.aspx.</span><span class="sxs-lookup"><span data-stu-id="ddf67-105">In Internet Explorer, move to http://\<*fabrikam_computername*\>/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="ddf67-106">Sur le **LOBWebApplication** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ddf67-106">On the **LOBWebApplication** page, do the following:</span></span>  
  
    |<span data-ttu-id="ddf67-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ddf67-107">Use this</span></span>|<span data-ttu-id="ddf67-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ddf67-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ddf67-109">**Organisation d’origine**</span><span class="sxs-lookup"><span data-stu-id="ddf67-109">**Home Organization**</span></span>|<span data-ttu-id="ddf67-110">Tapez **FABRIKAM**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-110">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="ddf67-111">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="ddf67-111">**Partner Organization**</span></span>|<span data-ttu-id="ddf67-112">Tapez **CONTOSO**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-112">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="ddf67-113">**Code PIP**</span><span class="sxs-lookup"><span data-stu-id="ddf67-113">**PIP Code**</span></span>|<span data-ttu-id="ddf67-114">Type **3A2**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-114">Type **3A2**.</span></span>|  
    |<span data-ttu-id="ddf67-115">**Version PIP**</span><span class="sxs-lookup"><span data-stu-id="ddf67-115">**PIP Version**</span></span>|<span data-ttu-id="ddf67-116">Type **R02.00.00A**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-116">Type **R02.00.00A**.</span></span>|  
    |<span data-ttu-id="ddf67-117">**Catégorie de message**</span><span class="sxs-lookup"><span data-stu-id="ddf67-117">**Message Category**</span></span>|<span data-ttu-id="ddf67-118">Tapez **Action**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-118">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="ddf67-119">À l’aide du bloc-notes ou un autre éditeur de texte, ouvrez le **3A2_Request.xml** fichier dans C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstancesfolder Copiez et collez le texte dans le **contenu du Service** champ dans l’outil LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="ddf67-119">Using Notepad or another text editor, open the **3A2_Request.xml** file in the C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstancesfolder and copy and paste the text into the **Service Content** field in the LOBWebApplication tool.</span></span>  
  
4.  <span data-ttu-id="ddf67-120">Cliquez sur **Submit** pour envoyer la demande 3A2 à Contoso.</span><span class="sxs-lookup"><span data-stu-id="ddf67-120">Click **Submit** to submit the 3A2 request to Contoso.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="ddf67-121">Pour vérifier la communication sur l'ordinateur Fabrikam</span><span class="sxs-lookup"><span data-stu-id="ddf67-121">To verify successful communication on the Fabrikam computer</span></span>  
  
1.  <span data-ttu-id="ddf67-122">Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="ddf67-122">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddf67-123">Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="ddf67-123">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="ddf67-124">Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="ddf67-124">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="ddf67-125">Un message de catégorie -99 indique une erreur.</span><span class="sxs-lookup"><span data-stu-id="ddf67-125">A category -99 message signifies an error.</span></span> <span data-ttu-id="ddf67-126">Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ddf67-126">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
2.  <span data-ttu-id="ddf67-127">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-127">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
3.  <span data-ttu-id="ddf67-128">Dans la connexion de la boîte de dialogue, dans le **SQL Server** , tapez **localhost**, sélectionnez **l’authentification Windows**, puis cliquez sur **Connect**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-128">In the Connect to Server dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="ddf67-129">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-129">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
5.  <span data-ttu-id="ddf67-130">Dans le  **\<table\> texte** boîte de dialogue, sélectionnez **BTARNDATA** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ddf67-130">In the **\<table\> text** dialog box, select **BTARNDATA** from the list.</span></span>  
  
6.  <span data-ttu-id="ddf67-131">Dans le **SQL** fenêtre, tapez l’instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="ddf67-131">In the **SQL** window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
7.  <span data-ttu-id="ddf67-132">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="ddf67-132">Click **Execute** to run the SQL statement.</span></span>  
  
8.  <span data-ttu-id="ddf67-133">Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="ddf67-133">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddf67-134">Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ddf67-134">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="ddf67-135">Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ddf67-135">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span> <span data-ttu-id="ddf67-136">Vous pouvez également utiliser le champ ServiceContent pour vérifier la réponse.</span><span class="sxs-lookup"><span data-stu-id="ddf67-136">You can also use the ServiceContent field to verify the response.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="ddf67-137">Pour vérifier la communication sur l'ordinateur Contoso</span><span class="sxs-lookup"><span data-stu-id="ddf67-137">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="ddf67-138">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-138">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="ddf67-139">Dans la connexion de la boîte de dialogue, dans le **SQL Server** , tapez **localhost**, sélectionnez **l’authentification Windows**, puis cliquez sur **Connect**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-139">In the Connect to Server dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="ddf67-140">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="ddf67-140">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="ddf67-141">Dans le  **\<table\> texte** boîte de dialogue, sélectionnez **BTARNDATA** dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ddf67-141">In the **\<table\> text** dialog box, select **BTARNDATA** from the list.</span></span>  
  
5.  <span data-ttu-id="ddf67-142">Dans le **SQL** fenêtre, tapez l’instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="ddf67-142">In the **SQL** window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="ddf67-143">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="ddf67-143">Click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="ddf67-144">Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="ddf67-144">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddf67-145">Vous devez tout d’abord recevoir un message de catégorie 10 qui représente la demande d’origine envoyée par l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ddf67-145">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="ddf67-146">Vous devez ensuite recevoir un message de catégorie 25, ce qui signifie l’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="ddf67-146">You should then receive a category 25 message signifying the receipt acknowledgement message.</span></span>  
  
8.  <span data-ttu-id="ddf67-147">Dans le **SQL** fenêtre, tapez l’instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="ddf67-147">In the **SQL** window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="ddf67-148">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="ddf67-148">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="ddf67-149">Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message sortant.</span><span class="sxs-lookup"><span data-stu-id="ddf67-149">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddf67-150">Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ddf67-150">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="ddf67-151">Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="ddf67-151">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf67-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddf67-152">See Also</span></span>  
 [<span data-ttu-id="ddf67-153">Didacticiel sur le processus privé</span><span class="sxs-lookup"><span data-stu-id="ddf67-153">Private Process Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/private-process-tutorial.md)