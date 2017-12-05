---
title: "Étape 1 : Créer et déployer des schémas d’en-tête et d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, header schemas
- header schemas
ms.assetid: 3ff013a4-6c67-4bac-be97-81b2dc5b6119
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9ffa8ab8d80a8b2da172378349eb9761a728fb7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-create-and-deploy-header-and-acknowledgment-schemas"></a><span data-ttu-id="fdae7-102">Étape 1 : Créer et déployer des schémas d’en-tête et d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fdae7-102">Step 1: Create and Deploy Header and Acknowledgment Schemas</span></span>
<span data-ttu-id="fdae7-103">Vous utilisez le schéma d’en-tête pour valider l’en-tête (segment MSH) de l’instance de message.</span><span class="sxs-lookup"><span data-stu-id="fdae7-103">You use the header schema to validate the header (MSH segment) of the message instance.</span></span> <span data-ttu-id="fdae7-104">Le schéma d’accusé de réception vous permet de générer l’accusé de réception pour l’instance de message.</span><span class="sxs-lookup"><span data-stu-id="fdae7-104">You use the acknowledgment schema to generate the acknowledgment for the message instance.</span></span> <span data-ttu-id="fdae7-105">Ce processus est commun à toutes les versions de schémas de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.</span><span class="sxs-lookup"><span data-stu-id="fdae7-105">This process is common across all schemas versions of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.</span></span>  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a><span data-ttu-id="fdae7-106">Pour créer les schémas d’en-tête et d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fdae7-106">To create the header and acknowledgment schemas</span></span>  
  
1.  <span data-ttu-id="fdae7-107">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-107">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="fdae7-108">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="fdae7-109">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** , développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-109">In the New Project dialog box, in the **Project Types** section, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
4.  <span data-ttu-id="fdae7-110">Dans la section modèles, sélectionnez **BTAHL7V2XCommon projet**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-110">In the Templates section, select **BTAHL7V2XCommon Project**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="fdae7-111">Dans l’Explorateur de solutions, notez que les trois schémas (ACK_24_GLO_DEF.xsd ACK_25_GLO_DEF.xsd et MSH_25_GLO_DEF.xsd) sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="fdae7-111">In Solution Explorer, notice that the three schemas (ACK_24_GLO_DEF.xsd ACK_25_GLO_DEF.xsd, and MSH_25_GLO_DEF.xsd) are included in the project.</span></span>  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="fdae7-112">Étape 1 a : assigner une clé forte à l’Assembly et le déployer</span><span class="sxs-lookup"><span data-stu-id="fdae7-112">Step 1A: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="fdae7-113">Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="fdae7-113">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="fdae7-114">Pour affecter une clé forte et de déployer l’assembly</span><span class="sxs-lookup"><span data-stu-id="fdae7-114">To assign a strong key and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="fdae7-115">Démarrez une **invite de commandes Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-115">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="fdae7-116">À la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes, accédez à la \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator pour HL7 \SDK\ Dossier didacticiel de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="fdae7-116">At the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, browse to the \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7 \SDK\End-to-End Tutorial folder.</span></span>  
  
3.  <span data-ttu-id="fdae7-117">À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="fdae7-117">At the command prompt, type **sn –k key.snk**, and then press ENTER.</span></span> <span data-ttu-id="fdae7-118">Vérifiez que le message suivant s’affiche dans la fenêtre Sortie, puis fermez la fenêtre de commande.</span><span class="sxs-lookup"><span data-stu-id="fdae7-118">Ensure the following success message appears in the output window, and then close the command window.</span></span>  
  
     <span data-ttu-id="fdae7-119">**« Paire de clés écrite dans key.snk. »**</span><span class="sxs-lookup"><span data-stu-id="fdae7-119">**"Key pair written to key.snk."**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fdae7-120">Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre assembly.</span><span class="sxs-lookup"><span data-stu-id="fdae7-120">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.</span></span>  
  
4.  <span data-ttu-id="fdae7-121">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V2XCommon Projet1**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-121">In Solution Explorer, right-click **BTAHL7V2XCommon Project1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="fdae7-122">Dans la page des Pages de propriétés Projet1 BTAHL7V2XCommon, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-122">On the BTAHL7V2XCommon Project1 Property Pages page, click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="fdae7-123">Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="fdae7-123">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (**…**) button.</span></span>  
  
7.  <span data-ttu-id="fdae7-124">Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\SDK\End en bout Didacticiel, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-124">In the Assembly Key File dialog box, browse to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial, select **key.snk**, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="fdae7-125">Dans la page de propriété du projet BTAHL7V2XCommon, cliquez sur **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="fdae7-125">On the BTAHL7V2XCommon Project Property page, click **OK** to save your changes.</span></span>  
  
9. <span data-ttu-id="fdae7-126">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans **l’Explorateur de solutions**, avec le bouton droit **BTAHL7V2XCommon projet**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="fdae7-126">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in **Solution Explorer**, right-click **BTAHL7V2XCommon Project**, and then click **Deploy**.</span></span> <span data-ttu-id="fdae7-127">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="fdae7-127">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fdae7-128">Si le message de déploiement approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="fdae7-128">If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.</span></span>  
  
 <span data-ttu-id="fdae7-129">Passez à [étape 2 : créer des schémas courants pour V2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="fdae7-129">Proceed to [Step 2: Create Common Schemas for V2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-3-1.md).</span></span>