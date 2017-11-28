---
title: "Gestion d’un Message non analysé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unparsed messages
- messages, unparsed messages
ms.assetid: c6a67ff3-3295-489f-9d5f-fb35b2bf8b19
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b7683a598169b8ece75788584e8bb9b3c7f4861
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="handling-an-unparsed-message"></a><span data-ttu-id="85378-102">Gestion d’un Message non analysé</span><span class="sxs-lookup"><span data-stu-id="85378-102">Handling an Unparsed Message</span></span>
<span data-ttu-id="85378-103">Cette section décrit comment gérer un message non analysé.</span><span class="sxs-lookup"><span data-stu-id="85378-103">This section describes how to handle an unparsed message.</span></span> <span data-ttu-id="85378-104">Contrairement aux messages dont la validation échouent, vous ne pouvez pas réparer un message qui [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ne peut pas analyser.</span><span class="sxs-lookup"><span data-stu-id="85378-104">Unlike messages that fail validation, you cannot repair a message that [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] cannot parse.</span></span> <span data-ttu-id="85378-105">Message Repair et New Submission affiche le message et la nature de l’erreur d’analyse et vous permet d’afficher le message ou l’enregistrer dans un fichier local.</span><span class="sxs-lookup"><span data-stu-id="85378-105">Message Repair and New Submission displays the message and the nature of the parsing error, and enables you to print the message or save it to a local file.</span></span> <span data-ttu-id="85378-106">Vous pouvez ensuite avertir l’entité qui a envoyé le message de la nature spécifique de l’échec de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="85378-106">You can then alert the entity that sent the message to the specific nature of the parsing failure.</span></span>  
  
### <a name="to-handle-an-unparsed-message"></a><span data-ttu-id="85378-107">Pour gérer un message non analysé</span><span class="sxs-lookup"><span data-stu-id="85378-107">To handle an unparsed message</span></span>  
  
1.  <span data-ttu-id="85378-108">Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.</span><span class="sxs-lookup"><span data-stu-id="85378-108">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="85378-109">Dans la fenêtre d’accueil, cliquez sur **Documents**.</span><span class="sxs-lookup"><span data-stu-id="85378-109">In the Home window, click **Documents**.</span></span>  
  
3.  <span data-ttu-id="85378-110">Dans la fenêtre de Documents sous **bibliothèques de documents**, cliquez sur **Unparsed**.</span><span class="sxs-lookup"><span data-stu-id="85378-110">In the Documents window, under **Document Libraries**, click **Unparsed**.</span></span>  
  
4.  <span data-ttu-id="85378-111">Dans la fenêtre non analysée, cliquez sur **boîte de réception**.</span><span class="sxs-lookup"><span data-stu-id="85378-111">In the Unparsed window, click **Inbox**.</span></span>  
  
5.  <span data-ttu-id="85378-112">Dans la fenêtre de la boîte de réception non analysée, pointez sur le message qui ne pas analyser, cliquez sur la flèche à droite du message et puis cliquez sur **modifier dans Microsoft Office InfoPath**.</span><span class="sxs-lookup"><span data-stu-id="85378-112">In the Unparsed Inbox window, point to the message that did not parse, click the arrow to the right of the message, and then click **Edit in Microsoft Office InfoPath**.</span></span>  
  
6.  <span data-ttu-id="85378-113">Dans le volet SWIFT accélérateur, cliquez sur **erreurs**.</span><span class="sxs-lookup"><span data-stu-id="85378-113">In the SWIFT Accelerator pane, click **Errors**.</span></span>  
  
7.  <span data-ttu-id="85378-114">Dans le volet analyse et des erreurs de Validation XML, lire l’erreur d’analyse.</span><span class="sxs-lookup"><span data-stu-id="85378-114">In the Parse and XML Validation Errors pane, read the parse error.</span></span>  
  
8.  <span data-ttu-id="85378-115">Dans le volet de Message non analysée, examinez le message.</span><span class="sxs-lookup"><span data-stu-id="85378-115">In the Unparsed Message pane, review the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85378-116">Si vous souhaitez afficher le message, dans le volet de Message non analysée, sur le **fichier** menu, cliquez sur **imprimer**.</span><span class="sxs-lookup"><span data-stu-id="85378-116">If you want to print the message, in the Unparsed Message pane, on the **File** menu, click **Print**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85378-117">Si vous souhaitez enregistrer le message dans un fichier local, dans le volet de Message non analysée, dans le **fichier** menu, cliquez sur **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="85378-117">If you want to save the message to a local file, in the Unparsed Message pane, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="85378-118">Dans le **enregistrer en tant que** boîte de dialogue le **enregistrer dans** la liste déroulante, accédez au dossier que vous souhaitez enregistrer le fichier, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="85378-118">In the **Save As** dialog box, in the **Save in** drop-down list, move to the folder that you want to save the file in, and then click **OK**.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="85378-119">enregistre le message au format XML.</span><span class="sxs-lookup"><span data-stu-id="85378-119"> saves the message in XML format.</span></span>  
  
9. <span data-ttu-id="85378-120">Dans le volet de Message non analysée, apportez les modifications nécessaires, puis cliquez sur **Submit**.</span><span class="sxs-lookup"><span data-stu-id="85378-120">In the Unparsed Message pane, make the necessary changes, and then click **Submit**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85378-121">Impossible de valider un message non analysé que vous avez réparé.</span><span class="sxs-lookup"><span data-stu-id="85378-121">You cannot validate an unparsed message that you have repaired.</span></span>  
  
10. <span data-ttu-id="85378-122">Dans la boîte de dialogue Envoyer un Message, cliquez sur **accepter** pour envoyer le message réparé avec les modifications acceptées, cliquez sur **rejeter** pour rejeter les modifications, ou cliquez sur **Annuler** pour annuler la soumission, puis revenez à l’écran.</span><span class="sxs-lookup"><span data-stu-id="85378-122">In the Submit Message dialog box, click **Accept** to submit the repaired message with changes accepted, click **Reject** to reject the changes, or click **Cancel** to cancel the submission and return to the form.</span></span>  
  
11. <span data-ttu-id="85378-123">Si vous avez cliqué sur **accepter** ou **rejeter** à l’étape 11, dans la page Assistant Signature numérique, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le Réparateur), puis Cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="85378-123">If you clicked **Accept** or **Reject** in step 11, on the Digital Signature Wizard page, select the certificate that you want to use to sign the form (the certificate that you created for the repairer), and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85378-124">Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**.</span><span class="sxs-lookup"><span data-stu-id="85378-124">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="85378-125">Tout utilisateur d’effectuer n’importe quel rôle peut envoyer un message de non analysé qui leur ont réparé.</span><span class="sxs-lookup"><span data-stu-id="85378-125">Any user performing any role can submit an unparsed message that they have repaired.</span></span>  
  
12. <span data-ttu-id="85378-126">Dans la page Assistant Signature numérique permettant d’entrer des commentaires, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="85378-126">On the Digital Signature Wizard page for entering comments, click **Finish**.</span></span>  
  
13. <span data-ttu-id="85378-127">Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous vous connectez est correct.</span><span class="sxs-lookup"><span data-stu-id="85378-127">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct.</span></span> <span data-ttu-id="85378-128">Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte.</span><span class="sxs-lookup"><span data-stu-id="85378-128">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="85378-129">Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.</span><span class="sxs-lookup"><span data-stu-id="85378-129">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  
  
14. <span data-ttu-id="85378-130">Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="85378-130">In the Verify Digital Signature window, click **Close**.</span></span>  
  
15. <span data-ttu-id="85378-131">Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="85378-131">In the Submission Success dialog box, click **OK**.</span></span>  
  
16. <span data-ttu-id="85378-132">Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.</span><span class="sxs-lookup"><span data-stu-id="85378-132">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>