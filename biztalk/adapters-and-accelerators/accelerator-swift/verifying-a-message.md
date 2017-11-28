---
title: "Vérification d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, verifying
- verifying, messages
ms.assetid: df2b72bb-4dc1-4fdd-8f63-35fc73a12151
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e22d5c24b0c2d29c225fa2206d47b67e3d166a2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="verifying-a-message"></a><span data-ttu-id="85228-102">Vérification d’un Message</span><span class="sxs-lookup"><span data-stu-id="85228-102">Verifying a Message</span></span>
<span data-ttu-id="85228-103">Cette section décrit comment vérifier si un message a été réparé.</span><span class="sxs-lookup"><span data-stu-id="85228-103">This section describes how to verify a message that has been repaired.</span></span>  
  
### <a name="to-verify-a-message"></a><span data-ttu-id="85228-104">Pour vérifier un message</span><span class="sxs-lookup"><span data-stu-id="85228-104">To verify a message</span></span>  
  
1.  <span data-ttu-id="85228-105">Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.</span><span class="sxs-lookup"><span data-stu-id="85228-105">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="85228-106">Dans la fenêtre d’accueil, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="85228-106">In the Home window, click **Documents**.</span></span>  
  
3.  <span data-ttu-id="85228-107">Dans la fenêtre de Documents sous **bibliothèques de documents**, cliquez sur  **\<* nom du service informatique*> _Verifier **.</span><span class="sxs-lookup"><span data-stu-id="85228-107">In the Documents window, under **Document Libraries**, click **\<*Department name*>_Verifier**.</span></span>  
  
4.  <span data-ttu-id="85228-108">Dans la fenêtre de confirmation, cliquez sur **boîte de réception**.</span><span class="sxs-lookup"><span data-stu-id="85228-108">In the Verify window, click **Inbox**.</span></span>  
  
5.  <span data-ttu-id="85228-109">Dans la fenêtre Vérifier la boîte de réception, pointez sur le titre du message, cliquez sur la flèche à droite du titre du message, puis cliquez sur **modifier dans Microsoft Office InfoPath**.</span><span class="sxs-lookup"><span data-stu-id="85228-109">In the Verify Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.</span></span>  
  
6.  <span data-ttu-id="85228-110">Dans le **télécharger le fichier** boîte de dialogue, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="85228-110">In the **File Download** dialog box, click **Open**.</span></span>  
  
7.  <span data-ttu-id="85228-111">Dans les rôles actuels : volet RekeyVerify de le [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, cliquez sur **erreurs**.</span><span class="sxs-lookup"><span data-stu-id="85228-111">In the Current Roles: RekeyVerify pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Errors**.</span></span> <span data-ttu-id="85228-112">Consulter toutes les erreurs affichées dans le **Parse et erreurs de Validation XML** boîte et la **BRE les erreurs de Validation** boîte.</span><span class="sxs-lookup"><span data-stu-id="85228-112">Review any errors shown in the **Parse and XML Validation Errors** box and the **BRE Validation Errors** box.</span></span>  
  
8.  <span data-ttu-id="85228-113">Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forme, faites défiler jusqu'à l’emplacement de l’erreur et vérifiez que l’erreur a été corrigée.</span><span class="sxs-lookup"><span data-stu-id="85228-113">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error and verify that the error has been corrected.</span></span> <span data-ttu-id="85228-114">Vous pouvez voir ce que l’erreur d’origine a été en cliquant sur **erreurs** dans le rôle actuel : RekeyVerify volet et l’affichage de l’erreur dans un des volets de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="85228-114">You can see what the original error was by clicking **Errors** in the Current Role: RekeyVerify pane, and viewing the error in one of the error panes.</span></span> <span data-ttu-id="85228-115">Vous pouvez également comparer les versions non réparées et réparées du message en cliquant sur **détails du Message** dans le rôle actuel : RekeyVerify volet.</span><span class="sxs-lookup"><span data-stu-id="85228-115">You can also compare the unrepaired and repaired versions of the message by clicking **Message Details** in the Current Role: RekeyVerify pane.</span></span>  
  
9. <span data-ttu-id="85228-116">Pour vous assurer que ce dernier est validé, cliquez sur **Validation** dans le rôle actuel : RekeyVerify volet, puis cliquez sur **valider le Message**.</span><span class="sxs-lookup"><span data-stu-id="85228-116">To ensure that the message will validate, click **Validation** in the Current Role: RekeyVerify pane, and then click **Validate Message**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85228-117">Le volet de résultats sous la Validation du Message dans le rôle actuel : RekeyVerify volet indique tous les champs dans le message que vous devez générer une nouvelle clé.</span><span class="sxs-lookup"><span data-stu-id="85228-117">The Results pane under Message Validation in the Current Role: RekeyVerify pane indicates all fields in the message that you need to rekey.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="85228-118">marque ces champs dans le volet de Message avec un astérisque rouge.</span><span class="sxs-lookup"><span data-stu-id="85228-118"> marks these fields in the Message pane with a red asterisk.</span></span>  
  
10. <span data-ttu-id="85228-119">Recomposition des données dans tous les champs dans le volet messages signalés par un astérisque rouge (indiquant que les données doivent être régénérées avant la soumission).</span><span class="sxs-lookup"><span data-stu-id="85228-119">Rekey data into all fields in the Message pane marked with a red asterisk (indicating that the data must be rekeyed before submission).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85228-120">Vous pouvez afficher les données dont vous avez besoin pour générer une nouvelle clé dans les champs de message en cliquant sur **détails du Message** dans le rôle actuel : RekeyVerify volet et faire défiler le message d’origine dans le champ.</span><span class="sxs-lookup"><span data-stu-id="85228-120">You can display the data that you need to rekey into message fields by clicking **Message Details** in the Current Role: RekeyVerify pane, and scrolling through the original message to the field.</span></span> <span data-ttu-id="85228-121">Cela est vrai, sauf si une erreur de validation dans un des champs de changement de clé dans le message d’origine, auquel cas vous devez réparer le champ lorsque vous le recomposition.</span><span class="sxs-lookup"><span data-stu-id="85228-121">This is true unless there was a validation error in one of the rekey fields in the original message, in which case you have to repair the field when you rekey it.</span></span>  
  
11. <span data-ttu-id="85228-122">Cliquez sur **Validation** dans les **rôle actuel : RekeyVerify** volet, puis cliquez sur **valider le Message**.</span><span class="sxs-lookup"><span data-stu-id="85228-122">Click **Validation** in the **Current Role: RekeyVerify** pane, and then click **Validate Message**.</span></span> <span data-ttu-id="85228-123">Vérifiez que le volet de résultats affiche le message **le message est valide**.</span><span class="sxs-lookup"><span data-stu-id="85228-123">Verify that the Results pane displays the message **The message is valid**.</span></span>  
  
12. <span data-ttu-id="85228-124">Cliquez sur **Submit** dans les [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007.</span><span class="sxs-lookup"><span data-stu-id="85228-124">Click **Submit** in the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85228-125">Lorsque vous cliquez sur **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] exécute une validation XML sur le message.</span><span class="sxs-lookup"><span data-stu-id="85228-125">When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message.</span></span> <span data-ttu-id="85228-126">Si la validation ne réussit pas, vous devez corriger les erreurs de validation avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="85228-126">If the validation is not successful, you must fix the validation errors before proceeding.</span></span>  
  
13. <span data-ttu-id="85228-127">Dans la boîte de dialogue Envoyer un Message, cliquez sur **accepter** pour envoyer le message vérifié avec les modifications acceptées.</span><span class="sxs-lookup"><span data-stu-id="85228-127">In the Submit Message dialog box, click **Accept** to submit the verified message with changes accepted.</span></span> <span data-ttu-id="85228-128">Cliquez sur **rejeter** pour envoyer le message avec les modifications rejetées.</span><span class="sxs-lookup"><span data-stu-id="85228-128">Click **Reject** to submit the message with changes rejected.</span></span> <span data-ttu-id="85228-129">Cliquez sur **Annuler** pour annuler l’envoi et de revenir à l’écran.</span><span class="sxs-lookup"><span data-stu-id="85228-129">Click **Cancel** to cancel the submission and return to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85228-130">Si vous acceptez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] effectue les validations BRE sur le message.</span><span class="sxs-lookup"><span data-stu-id="85228-130">If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85228-131">Si vous le rejetez les modifications de message, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] renvoie le message à la première étape du flux de travail (créer ou réparer) et réinitialise le flux de travail de réparation.</span><span class="sxs-lookup"><span data-stu-id="85228-131">If you reject the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] returns the message to the first stage of the workflow (create or repair) and resets the repair workflow.</span></span>  
  
14. <span data-ttu-id="85228-132">Dans la page Assistant Signature numérique pour sélectionner le certificat de signature de l’écran, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le vérificateur), puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="85228-132">On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the verifier), and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85228-133">Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**.</span><span class="sxs-lookup"><span data-stu-id="85228-133">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span> <span data-ttu-id="85228-134">Si vous devez ajouter une autre signature pour ce rôle, effectuez cette opération dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="85228-134">If you need to add another signature for this role, do so in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console.</span></span>  
  
15. <span data-ttu-id="85228-135">Dans la page Assistant Signature numérique permettant d’entrer des commentaires, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="85228-135">On the Digital Signature Wizard page for entering comments, click **Finish**.</span></span>  
  
16. <span data-ttu-id="85228-136">Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous vous connectez est correct.</span><span class="sxs-lookup"><span data-stu-id="85228-136">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct.</span></span> <span data-ttu-id="85228-137">Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte.</span><span class="sxs-lookup"><span data-stu-id="85228-137">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="85228-138">Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.</span><span class="sxs-lookup"><span data-stu-id="85228-138">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  
  
17. <span data-ttu-id="85228-139">Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="85228-139">In the Verify Digital Signature window, click **Close**.</span></span>  
  
18. <span data-ttu-id="85228-140">Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="85228-140">In the Submission Success dialog box, click **OK**.</span></span>  
  
19. <span data-ttu-id="85228-141">Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.</span><span class="sxs-lookup"><span data-stu-id="85228-141">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>  
  
20. <span data-ttu-id="85228-142">Dans le site MRSR, cliquez sur **Documents et listes**.</span><span class="sxs-lookup"><span data-stu-id="85228-142">In MRSR site, click **Documents and Lists**.</span></span> <span data-ttu-id="85228-143">Si vous avez cliqué sur **accepter** pour accepter les modifications apportées à l’étape 13, vérifiez que le \<nom service > bibliothèque de documents _Approve contient le message qui a été modifié.</span><span class="sxs-lookup"><span data-stu-id="85228-143">If you clicked **Accept** to accept the changes in step 13, verify that the \<Department name>_Approve document library contains the message that was just modified.</span></span> <span data-ttu-id="85228-144">Si vous avez déjà ouvert la fenêtre de Documents et listes, cliquez sur **Actualiser** sur la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="85228-144">If you already had the Documents and Lists window open, click **Refresh** on the **View** menu.</span></span> <span data-ttu-id="85228-145">Si vous avez cliqué sur **rejeter** pour rejeter les modifications apportées à l’étape 13, vérifiez que le  *\<nom de l’ordinateur >*bibliothèque de documents _Outbox contient le message qui a été modifié.</span><span class="sxs-lookup"><span data-stu-id="85228-145">If you clicked **Reject** to reject the changes in step 13, verify that the *\<computer name>*_Outbox document library contains the message that was just modified.</span></span>