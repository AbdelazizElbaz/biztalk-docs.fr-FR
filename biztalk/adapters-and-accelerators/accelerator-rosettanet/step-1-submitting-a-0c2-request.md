---
title: "Étape 1 : Envoi d’un 0C 2 demande | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: double action tutorial, submitting requests
ms.assetid: 698c4a43-20b9-46b7-ab66-1dfa24232024
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f05aa5200bd1df6207a962849cd776a03fe71805
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-submitting-a-0c2-request"></a><span data-ttu-id="75df7-102">Étape 1 : Envoi d’un 0C la demande 2</span><span class="sxs-lookup"><span data-stu-id="75df7-102">Step 1: Submitting a 0C2 Request</span></span>
<span data-ttu-id="75df7-103">Dans cette étape, vous préparez et soumettez une demande à l’aide du processus PIP (Partner Interface) pour un C 0 2 - asynchrone demande de Test.</span><span class="sxs-lookup"><span data-stu-id="75df7-103">In this step, you prepare and submit a request using the Partner Interface Process (PIP) for an 0C2 - Asynchronous Test Request.</span></span> <span data-ttu-id="75df7-104">Ce processus PIP garantit qu’un canal de communication asynchrone fonctionne correctement entre les deux organisations différentes.</span><span class="sxs-lookup"><span data-stu-id="75df7-104">This PIP ensures that an asynchronous communication channel is working correctly between two different organizations.</span></span> <span data-ttu-id="75df7-105">Ce processus PIP suit le même modèle que les autres processus PIP action double asynchrones, telles que les 3 a 4 - demande de bon ordre PIP.</span><span class="sxs-lookup"><span data-stu-id="75df7-105">This PIP follows the same pattern as other asynchronous double action PIPs, such as the 3A4 - Request Purchase Order PIP.</span></span>  
  
### <a name="to-submit-a-0c2---asynchronous-test-request"></a><span data-ttu-id="75df7-106">Pour envoyer un 0C 2 - asynchrone demande de Test</span><span class="sxs-lookup"><span data-stu-id="75df7-106">To submit a 0C2 - Asynchronous Test Request</span></span>  
  
1.  <span data-ttu-id="75df7-107">Sur l'ordinateur Fabrikam, dans Internet Explorer, recherchez et ouvrez http://localhost/LOBWebApplication/default.aspx.</span><span class="sxs-lookup"><span data-stu-id="75df7-107">On the Fabrikam computer, in Internet Explorer, locate and open http://localhost/LOBWebApplication/default.aspx.</span></span>  
  
2.  <span data-ttu-id="75df7-108">Dans la page **Envoyer un Message** , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="75df7-108">On the **Submit Message** page, do the following:</span></span>  
  
    |<span data-ttu-id="75df7-109">Propriété</span><span class="sxs-lookup"><span data-stu-id="75df7-109">Use this</span></span>|<span data-ttu-id="75df7-110">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="75df7-110">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="75df7-111">**Organisation d’origine**</span><span class="sxs-lookup"><span data-stu-id="75df7-111">**Home Organization**</span></span>|<span data-ttu-id="75df7-112">Tapez **FABRIKAM**.</span><span class="sxs-lookup"><span data-stu-id="75df7-112">Type **FABRIKAM**.</span></span>|  
    |<span data-ttu-id="75df7-113">**Organisation du partenaire**</span><span class="sxs-lookup"><span data-stu-id="75df7-113">**Partner Organization**</span></span>|<span data-ttu-id="75df7-114">Tapez **CONTOSO**.</span><span class="sxs-lookup"><span data-stu-id="75df7-114">Type **CONTOSO**.</span></span>|  
    |<span data-ttu-id="75df7-115">**Code PIP**</span><span class="sxs-lookup"><span data-stu-id="75df7-115">**Pip Code**</span></span>|<span data-ttu-id="75df7-116">Type **0C 2**.</span><span class="sxs-lookup"><span data-stu-id="75df7-116">Type **0C2**.</span></span>|  
    |<span data-ttu-id="75df7-117">**Version du PIP**</span><span class="sxs-lookup"><span data-stu-id="75df7-117">**Pip Version**</span></span>|<span data-ttu-id="75df7-118">Tapez **R01.02**.</span><span class="sxs-lookup"><span data-stu-id="75df7-118">Type **R01.02**.</span></span>|  
    |<span data-ttu-id="75df7-119">**ID d’Instance PIP**</span><span class="sxs-lookup"><span data-stu-id="75df7-119">**Pip Instance ID**</span></span>|<span data-ttu-id="75df7-120">Type **0C2_Test**.</span><span class="sxs-lookup"><span data-stu-id="75df7-120">Type **0C2_Test**.</span></span> <span data-ttu-id="75df7-121">**Important :** vous devez vous assurer que le **PIP** est unique pour chaque message que vous envoyez pour éviter les erreurs d’ID de message en double.</span><span class="sxs-lookup"><span data-stu-id="75df7-121">**Important:**  You must make sure that the **PIP** is unique for each message that you submit to avoid duplicate message ID errors.</span></span> <span data-ttu-id="75df7-122">Si vous exécutez le 0 C 2 de test à l’avenir, vous devrez modifier ce champ.</span><span class="sxs-lookup"><span data-stu-id="75df7-122">If you run the 0C2 test in the future, you will have to change this field.</span></span>|  
    |<span data-ttu-id="75df7-123">**Catégorie de message**</span><span class="sxs-lookup"><span data-stu-id="75df7-123">**Message Category**</span></span>|<span data-ttu-id="75df7-124">Tapez **Action**.</span><span class="sxs-lookup"><span data-stu-id="75df7-124">Type **Action**.</span></span>|  
  
3.  <span data-ttu-id="75df7-125">Utilisez le bloc-notes ou un autre éditeur de texte, ouvrez le fichier 0C2_Request.xml dans le \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\ LOBApplication\SampleInstances dossier, puis copiez et collez le contenu dans le **Service contenu** champ LOBWebApplication.</span><span class="sxs-lookup"><span data-stu-id="75df7-125">Using Notepad or another text editor, open the 0C2_Request.xml file in the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder, and then copy and paste the contents into the **Service Content** field in LOBWebApplication.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75df7-126">Pour supprimer le texte existant dans le champ contenu du Service sous la forme d’envoyer un Message, placez le curseur au début du texte, maintenez la **MAJ** et **Ctrl** boutons, cliquez sur **fin** , puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="75df7-126">To delete the existing text in the Service Content field of the Submit Message form, place the cursor at the beginning of the text, press and hold the **Shift** and **Ctrl** buttons, click **End**, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="75df7-127">Cliquez sur **Submit** pour envoyer la valeur 0, C 2 demande à l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="75df7-127">Click **Submit** to submit the 0C2 request to the Contoso computer.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-fabrikam-computer"></a><span data-ttu-id="75df7-128">Pour vérifier la communication sur l'ordinateur Fabrikam</span><span class="sxs-lookup"><span data-stu-id="75df7-128">To verify successful communication on the Fabrikam computer</span></span>  
  
-   <span data-ttu-id="75df7-129">Dans la page **État du message** de LOBWebApplication, vérifiez que vous recevez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="75df7-129">On the **Message Status** page in LOBWebApplication, verify that you receive two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75df7-130">Vous devez tout d’abord recevoir un message de catégorie 25, ce qui signifie un accusé de réception reçu à partir de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="75df7-130">You should first receive a category 25 message signifying a receipt acknowledgement from the Contoso computer.</span></span> <span data-ttu-id="75df7-131">Vous devez ensuite recevoir un message de catégorie 50 qui est le message de réponse de l’ordinateur Contoso.</span><span class="sxs-lookup"><span data-stu-id="75df7-131">You should then receive a category 50 message that is the response message from the Contoso computer.</span></span> <span data-ttu-id="75df7-132">Un message de catégorie -99 indique une erreur.</span><span class="sxs-lookup"><span data-stu-id="75df7-132">A category -99 message signifies an error.</span></span> <span data-ttu-id="75df7-133">Vous pouvez utiliser **Observateur d’événements** pour déterminer le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="75df7-133">You can use **Event Viewer** to determine the actual error message.</span></span>  
  
### <a name="to-verify-successful-communication-on-the-contoso-computer"></a><span data-ttu-id="75df7-134">Pour vérifier la communication sur l'ordinateur Contoso</span><span class="sxs-lookup"><span data-stu-id="75df7-134">To verify successful communication on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="75df7-135">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2005**et cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="75df7-135">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="75df7-136">Dans la boîte de dialogue **Connexion au serveur** , dans la zone **SQL Server** , tapez **localhost**, sélectionnez **Authentification Windows**, puis cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="75df7-136">In the **Connect to Server** dialog box, in the **SQL Server** box, type **localhost**, select **Windows Authentication**, and then click **Connect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75df7-137">Si l’Agent SQL Server n’est pas démarré, faites un clic droit, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="75df7-137">If the SQL Server Agent is not started, right-click it, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="75df7-138">Dans Microsoft SQL Server Management Studio, cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="75df7-138">In the Microsoft SQL Server Management Studio, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="75df7-139">Dans le \<table\> boîte de dialogue texte, sélectionnez **BTARNDATA** dans la liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="75df7-139">In the \<table\> text dialog box, select **BTARNDATA** from the list, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="75df7-140">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="75df7-140">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesToLOB  
    ```  
  
6.  <span data-ttu-id="75df7-141">Sur le **requête** menu, cliquez sur **Execute** pour exécuter l’instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="75df7-141">On the **Query** menu, click **Execute** to run the SQL statement.</span></span>  
  
7.  <span data-ttu-id="75df7-142">Dans la fenêtre de requête, dans le volet de résultats, vérifiez que vous voyez deux messages entrants.</span><span class="sxs-lookup"><span data-stu-id="75df7-142">In the Query window, in the Results pane, verify that you see two incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75df7-143">Vous devez tout d’abord recevoir un message de catégorie 10 qui représente la demande d’origine envoyée par l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="75df7-143">You should first receive a category 10 message that represents the original request sent by the Fabrikam computer.</span></span> <span data-ttu-id="75df7-144">Vous devez ensuite recevoir un message de catégorie 25, ce qui signifie l’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="75df7-144">You should then receive a category 25 message signifying the receipt acknowledgement message.</span></span>  
  
8.  <span data-ttu-id="75df7-145">Dans la fenêtre SQL, tapez l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="75df7-145">In the SQL window, type the following SQL statement:</span></span>  
  
    ```  
    SELECT * From MessagesFromLOB  
    ```  
  
9. <span data-ttu-id="75df7-146">Cliquez sur **Exécuter** pour exécuter l'instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="75df7-146">Click **Execute** to run the SQL statement.</span></span>  
  
10. <span data-ttu-id="75df7-147">Dans le volet de résultats de la fenêtre Requête, vérifiez que vous voyez un message sortant.</span><span class="sxs-lookup"><span data-stu-id="75df7-147">In the Query window, in the Results pane, verify that you see one outgoing message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75df7-148">Vous devez voir un message de 25 catégorie qui représente l’accusé de réception envoyé par Contoso à l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="75df7-148">You should see a category 25 message that represents the receipt acknowledgement sent from Contoso to the Fabrikam computer.</span></span> <span data-ttu-id="75df7-149">Vous devez également voir un message de catégorie 50 qui représente la réponse envoyée de l’application Contoso line-of-business (LOB) l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="75df7-149">You should also see a category 50 message that represents the response sent from the Contoso line-of-business (LOB) application to the Fabrikam computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75df7-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75df7-150">See Also</span></span>  
 <span data-ttu-id="75df7-151">[Étape 2 : Envoi d’un 0C de requête 4](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md) </span><span class="sxs-lookup"><span data-stu-id="75df7-151">[Step 2: Submitting a 0C4 Query](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md) </span></span>  
 [<span data-ttu-id="75df7-152">Flux de messages BTARN</span><span class="sxs-lookup"><span data-stu-id="75df7-152">Message Flow in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)