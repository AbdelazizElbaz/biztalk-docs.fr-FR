---
title: "Création et envoi d’un nouveau Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- submitting, messages
- messages, submitting
- messages, creating
ms.assetid: 88b7a2d3-44a4-44e4-ba8c-527c10290925
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42cd2a82fe0ecde75446e68f9f58e17f103e5efa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-submitting-a-new-message"></a><span data-ttu-id="27800-102">Création et envoi d’un nouveau Message</span><span class="sxs-lookup"><span data-stu-id="27800-102">Creating and Submitting a New Message</span></span>
<span data-ttu-id="27800-103">Cette section décrit comment envoyer un message.</span><span class="sxs-lookup"><span data-stu-id="27800-103">This section describes how to submit a new message.</span></span> <span data-ttu-id="27800-104">Comme avec un message réparé, un nouveau message doit être vérifié et approuvé par des personnes autres que le créateur de message.</span><span class="sxs-lookup"><span data-stu-id="27800-104">As with a repaired message, a new message must be verified and approved by people other than the message creator.</span></span>  
  
 <span data-ttu-id="27800-105">Pour envoyer un message, vous devez télécharger dans la bibliothèque de documents de nouveaux Messages SWIFT un fichier de modèle de message pour le type de message que vous souhaitez envoyer.</span><span class="sxs-lookup"><span data-stu-id="27800-105">To submit a new message, you must upload into the New SWIFT Messages document library a message template file for the type of message that you want to submit.</span></span> <span data-ttu-id="27800-106">Vous pouvez télécharger manuellement un modèle de message unique, ou vous pouvez télécharger tous les modèles de message à l’aide de l’outil FormPublish.</span><span class="sxs-lookup"><span data-stu-id="27800-106">You can upload a single message template manually, or you can upload all message templates using the FormPublish tool.</span></span>  
  
### <a name="to-upload-a-single-message-template-into-the-new-document-library"></a><span data-ttu-id="27800-107">Pour télécharger un modèle de message unique dans la bibliothèque de documents</span><span class="sxs-lookup"><span data-stu-id="27800-107">To upload a single message template into the new document library</span></span>  
  
1.  <span data-ttu-id="27800-108">Reportez-vous à la section [formulaire générateur utilitaire pour générer des formulaires InfoPath MT/MX](../../adapters-and-accelerators/accelerator-swift/form-generator-utility-to-generate-mt-mx-infopath-forms.md) pour obtenir des instructions.</span><span class="sxs-lookup"><span data-stu-id="27800-108">Refer to the section [Form Generator Utility to Generate MT/MX InfoPath Forms](../../adapters-and-accelerators/accelerator-swift/form-generator-utility-to-generate-mt-mx-infopath-forms.md) for instructions.</span></span>  
  
### <a name="to-create-and-submit-a-new-message"></a><span data-ttu-id="27800-109">Pour créer et envoyer un message</span><span class="sxs-lookup"><span data-stu-id="27800-109">To create and submit a new message</span></span>  
  
1.  <span data-ttu-id="27800-110">Dans Internet Explorer, ouvrez votre site MRSR http://localhost/sites/bassite.</span><span class="sxs-lookup"><span data-stu-id="27800-110">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="27800-111">Cliquez sur **Documents**, puis cliquez sur **nouveaux Messages SWIFT**.</span><span class="sxs-lookup"><span data-stu-id="27800-111">Click **Documents**, and then click **New SWIFT Messages**.</span></span>  
  
3.  <span data-ttu-id="27800-112">Dans la page nouveaux Messages SWIFT, double-cliquez sur le nom de la catégorie qui contient le type du message que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="27800-112">On the New SWIFT Messages page, double-click the name of the category containing the type of the message that you would like to create.</span></span>  
  
4.  <span data-ttu-id="27800-113">Cliquez sur le modèle de formulaire pour le message que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="27800-113">Click the form template for the message that you want to create.</span></span>  
  
5.  <span data-ttu-id="27800-114">Dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre 2007, dans le message d’écran, données de message de type pour tous les champs obligatoires (tel que signalé par un astérisque) et les champs facultatifs que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="27800-114">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, in the message form, type message data for all required fields (as denoted by an asterisk) and any optional fields you want to use.</span></span>  
  
6.  <span data-ttu-id="27800-115">Pour rechercher un BIC, dans le rôle actuel : créer le volet, cliquez sur **recherche BIC**.</span><span class="sxs-lookup"><span data-stu-id="27800-115">To look up a BIC, in the Current Role: Create pane, click **BIC Lookup**.</span></span>  
  
7.  <span data-ttu-id="27800-116">Tapez le nom de l’établissement, le code de la banque et le pays/région, puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="27800-116">Type the name of the financial institution, the bank code, and the country/region, and then click **Search**.</span></span>  
  
8.  <span data-ttu-id="27800-117">Dans le volet de recherche BIC, copiez le code BIC dans le champ de code bancaire approprié sous la forme de message.</span><span class="sxs-lookup"><span data-stu-id="27800-117">From the BIC Lookup pane, copy the BIC into the appropriate bank code field in the message form.</span></span>  
  
9. <span data-ttu-id="27800-118">Dans le rôle actuel : créer le volet, cliquez sur **Validation**, puis cliquez sur **valider le Message**.</span><span class="sxs-lookup"><span data-stu-id="27800-118">In the Current Role: Create pane, click **Validation**, and then click **Validate Message**.</span></span>  
  
10. <span data-ttu-id="27800-119">Dans le volet de résultats du rôle actuel : créer le volet, déterminer les erreurs que vous devez corriger dans le message.</span><span class="sxs-lookup"><span data-stu-id="27800-119">In the Results pane of the Current Role: Create pane, determine the errors that you need to fix in the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27800-120">Vous pouvez uniquement soumettre un nouveau message si vous avez résolu toutes les erreurs de validation dans le message.</span><span class="sxs-lookup"><span data-stu-id="27800-120">You can only submit a new message if you have fixed all validation errors in the message.</span></span>  
  
11. <span data-ttu-id="27800-121">Dans la barre d’outils Standard en haut de la fenêtre, cliquez sur **Submit**.</span><span class="sxs-lookup"><span data-stu-id="27800-121">From the Standard toolbar at the top of the window, click **Submit**.</span></span>  
  
12. <span data-ttu-id="27800-122">Dans la page Assistant Signature numérique pour sélectionner le certificat de signature de l’écran, sélectionnez le certificat que vous souhaitez utiliser pour signer le formulaire (le certificat que vous avez créé pour le créateur).</span><span class="sxs-lookup"><span data-stu-id="27800-122">On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the creator).</span></span> <span data-ttu-id="27800-123">Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte.</span><span class="sxs-lookup"><span data-stu-id="27800-123">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="27800-124">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="27800-124">Click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27800-125">Pour vérifier la validité d’une signature numérique, cliquez sur **Signatures numériques** sur la **outils** menu, cliquez sur la signature numérique que vous souhaitez vérifier, puis cliquez sur **afficher le formulaire signé**.</span><span class="sxs-lookup"><span data-stu-id="27800-125">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span>  
  
13. <span data-ttu-id="27800-126">Dans la page Assistant Signature numérique permettant d’entrer des commentaires, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="27800-126">On the Digital Signature Wizard page for entering comments, click **Finish**.</span></span>  
  
14. <span data-ttu-id="27800-127">Dans la page Assistant Signature numérique pour la vérification de l’écran, vérifiez que le message que vous vous connectez est correct.</span><span class="sxs-lookup"><span data-stu-id="27800-127">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct.</span></span> <span data-ttu-id="27800-128">Cliquez sur **afficher le certificat** si vous souhaitez vérifier que vous utilisez la signature correcte.</span><span class="sxs-lookup"><span data-stu-id="27800-128">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="27800-129">Cliquez sur **j’ai vérifié ce contenu avant de le signer**, puis cliquez sur **signe**.</span><span class="sxs-lookup"><span data-stu-id="27800-129">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  
  
15. <span data-ttu-id="27800-130">Dans la fenêtre Vérifier la Signature numérique, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="27800-130">In the Verify Digital Signature window, click **Close**.</span></span>  
  
16. <span data-ttu-id="27800-131">Dans la boîte de dialogue de réussite de l’envoi, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="27800-131">In the Submission Success dialog box, click **OK**.</span></span>  
  
17. <span data-ttu-id="27800-132">Fermer la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fenêtre.</span><span class="sxs-lookup"><span data-stu-id="27800-132">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>