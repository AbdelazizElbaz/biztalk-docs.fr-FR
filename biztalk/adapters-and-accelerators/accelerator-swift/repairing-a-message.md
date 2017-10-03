---
title: "La réparation d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: repairing messages
ms.assetid: 3a61b73b-5433-4249-b580-6194ccb4aebc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4071fd04b89681f9f7d6948798dd665b96a0c1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-a-message"></a><span data-ttu-id="da318-102">La réparation d’un Message</span><span class="sxs-lookup"><span data-stu-id="da318-102">Repairing a Message</span></span>
<span data-ttu-id="da318-103">Cette section décrit comment réparer un message d’échec de la validation.</span><span class="sxs-lookup"><span data-stu-id="da318-103">This section describes how to repair a message that has failed validation.</span></span>  
  
### <a name="to-repair-a-message"></a><span data-ttu-id="da318-104">Pour réparer un message</span><span class="sxs-lookup"><span data-stu-id="da318-104">To repair a message</span></span>  
  
1.  <span data-ttu-id="da318-105">Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.</span><span class="sxs-lookup"><span data-stu-id="da318-105">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="da318-106">Dans la fenêtre d’accueil, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="da318-106">In the Home window, click **Documents**.</span></span>  
  
3.  <span data-ttu-id="da318-107">Dans la fenêtre de Documents sous **bibliothèques de documents**, cliquez sur  **\<* nom du service informatique*>**_** Réparateur **.</span><span class="sxs-lookup"><span data-stu-id="da318-107">In the Documents window, under **Document Libraries**, click **\<*Department name*>**_**Repairer**.</span></span>  
  
4.  <span data-ttu-id="da318-108">Dans le \< *nom du service informatique*> _Repair fenêtre, cliquez sur **boîte de réception**.</span><span class="sxs-lookup"><span data-stu-id="da318-108">In the \<*Department name*>_Repair window, click **Inbox**.</span></span>  
  
5.  <span data-ttu-id="da318-109">Dans la fenêtre de la boîte de réception, pointez sur le titre du message, cliquez sur la flèche à droite du titre du message, puis cliquez sur **modifier dans Microsoft Office InfoPath**.</span><span class="sxs-lookup"><span data-stu-id="da318-109">In the Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.</span></span>  
  
6.  <span data-ttu-id="da318-110">Dans le volet SWIFT accélérateur de le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, assurez-vous que **erreurs** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="da318-110">In the SWIFT Accelerator pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, ensure that **Errors** is selected.</span></span> <span data-ttu-id="da318-111">Examinez les erreurs affichées dans le **Parse et erreurs de Validation XML**, **BRE les erreurs de Validation**, et **erreurs d’exécution** zones.</span><span class="sxs-lookup"><span data-stu-id="da318-111">Review any errors shown in the **Parse and XML Validation Errors**, **BRE Validation Errors**, and **Runtime Errors** boxes.</span></span>  
  
7.  <span data-ttu-id="da318-112">Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran, faites défiler jusqu'à l’emplacement de l’erreur et corrigez l’erreur.</span><span class="sxs-lookup"><span data-stu-id="da318-112">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error, and correct the error.</span></span> <span data-ttu-id="da318-113">S’il s’agit d’une erreur de validation XML, l’erreur est mises en surbrillance en rouge.</span><span class="sxs-lookup"><span data-stu-id="da318-113">If it is an XML validation error, the error will be highlighted in red.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da318-114">Erreurs de validation BRE ne seront pas mis en surbrillance en rouge dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire.</span><span class="sxs-lookup"><span data-stu-id="da318-114">BRE validation errors will not be highlighted in red in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form.</span></span> <span data-ttu-id="da318-115">Pour plus d’informations sur les erreurs de validation BRE, consultez [Codes d’erreur SWIFT](../../adapters-and-accelerators/accelerator-swift/swift-error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="da318-115">For more information about BRE validation errors, see [SWIFT Error Codes](../../adapters-and-accelerators/accelerator-swift/swift-error-codes.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da318-116">Si l’erreur se produit dans un champ qui est accompagné d’une liste déroulante, vous ne serez pas en mesure d’afficher la valeur d’origine qui a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="da318-116">If the error occurs in a field that is accompanied by a drop-down list, you will not be able to see the original value that caused the error.</span></span> <span data-ttu-id="da318-117">Le champ affiche « Select » au lieu de la valeur d’origine.</span><span class="sxs-lookup"><span data-stu-id="da318-117">The field will display "Select" instead of the original value.</span></span> <span data-ttu-id="da318-118">Dans la liste déroulante, sélectionnez la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="da318-118">Select the appropriate value from the drop-down list.</span></span>  
  
8.  <span data-ttu-id="da318-119">Pour vous assurer que ce dernier est validé, cliquez sur **Validation** dans le rôle actuel : réparer volet, puis cliquez sur **valider le Message**.</span><span class="sxs-lookup"><span data-stu-id="da318-119">To ensure that the message will validate, click **Validation** in the Current Role: Repair pane, and then click **Validate Message**.</span></span> <span data-ttu-id="da318-120">Vérifiez que le volet de résultats affiche **le message est valide**.</span><span class="sxs-lookup"><span data-stu-id="da318-120">Verify that the Results pane displays **The message is valid**.</span></span>  
  
9. <span data-ttu-id="da318-121">Dans le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, cliquez sur **Submit**.</span><span class="sxs-lookup"><span data-stu-id="da318-121">In the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Submit**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da318-122">Lorsque vous cliquez sur **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] exécute une validation XML sur le message.</span><span class="sxs-lookup"><span data-stu-id="da318-122">When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message.</span></span> <span data-ttu-id="da318-123">Si la validation ne réussit pas, vous devez corriger les erreurs de validation avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="da318-123">If the validation is not successful, you must fix the validation errors before proceeding.</span></span>  
  
10. <span data-ttu-id="da318-124">Dans la boîte de dialogue Envoyer un Message, cliquez sur **accepter** pour envoyer le message réparé avec les modifications acceptées, cliquez sur **rejeter** pour rejeter les modifications, ou cliquez sur **Annuler** pour annuler la soumission, puis revenez à l’écran.</span><span class="sxs-lookup"><span data-stu-id="da318-124">In the Submit Message dialog box, click **Accept** to submit the repaired message with changes accepted, click **Reject** to reject the changes, or click **Cancel** to cancel the submission and return to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da318-125">Si vous acceptez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] effectue les validations BRE sur le message.</span><span class="sxs-lookup"><span data-stu-id="da318-125">If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da318-126">Si vous le rejetez les modifications de message dans la phase de réparation, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] achemine le message vers la MessageBox et publications dans l’Observateur d’événement de message d’erreur « Impossible de réinitialiser à la première étape dans le flux de travail. ».</span><span class="sxs-lookup"><span data-stu-id="da318-126">If you reject the message changes in the repair stage, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] routes the message to the MessageBox, and posts to the Event Viewer an error that reads "Could not reset to the first stage in the workflow.".</span></span>  
  
11. <span data-ttu-id="da318-127">Si vous avez cliqué sur **accepter** ou **rejeter** à l’étape 10, sur le **Assistant Signature numérique** page, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le Réparateur), puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="da318-127">If you clicked **Accept** or **Reject** in step 10, on the **Digital Signature Wizard** page, select the certificate that you want to use to sign the form (the certificate that you created for the repairer), and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da318-128">Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**.</span><span class="sxs-lookup"><span data-stu-id="da318-128">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span>  
  
12. <span data-ttu-id="da318-129">Dans la page Assistant Signature numérique permettant d’entrer un commentaire, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="da318-129">On the Digital Signature Wizard page for entering a comment, click **Finish**.</span></span>  
  
13. <span data-ttu-id="da318-130">Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous signez et votre signature sont corrects.</span><span class="sxs-lookup"><span data-stu-id="da318-130">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing and your signature are correct.</span></span> <span data-ttu-id="da318-131">Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.</span><span class="sxs-lookup"><span data-stu-id="da318-131">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  
  
14. <span data-ttu-id="da318-132">Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="da318-132">In the Verify Digital Signature window, click **Close**.</span></span>  
  
15. <span data-ttu-id="da318-133">Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da318-133">In the Submission Success dialog box, click **OK**.</span></span>  
  
16. <span data-ttu-id="da318-134">Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.</span><span class="sxs-lookup"><span data-stu-id="da318-134">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>  
  
17. <span data-ttu-id="da318-135">Dans le site MRSR, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="da318-135">In MRSR site, click **Documents**.</span></span> <span data-ttu-id="da318-136">Si vous avez cliqué sur **accepter** pour accepter les modifications apportées à l’étape 11, vérifiez que le  *\<nom service >*bibliothèque de documents _ReKeyVerify contient le message que vous venez de réparer.</span><span class="sxs-lookup"><span data-stu-id="da318-136">If you clicked **Accept** to accept the changes in step 11, verify that the *\<Department name>*_ReKeyVerify document library contains the message that you just repaired.</span></span> <span data-ttu-id="da318-137">Si vous avez cliqué sur **rejeter** pour rejeter les modifications apportées à l’étape 11, vérifiez que la bibliothèque de documents A4SWIFT_Outbox contient le message qui a été modifié.</span><span class="sxs-lookup"><span data-stu-id="da318-137">If you clicked **Reject** to reject the changes in step 11, verify that the A4SWIFT_Outbox document library contains the message that was just modified.</span></span>