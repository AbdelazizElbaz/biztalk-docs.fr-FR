---
title: "Étape 1 : Créer et déployer des en-tête commun et schémas d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, headers
ms.assetid: e0f11f58-9a8c-4567-a537-3d182fa7dce2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a134071ee1973961e0fb4ed9b4da73ad87d8dbb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-and-deploy-common-header-and-acknowledgment-schemas"></a><span data-ttu-id="1e0cb-102">Étape 1 : Créer et déployer des en-tête commun et schémas d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="1e0cb-102">Step 1: Create and Deploy Common Header and Acknowledgment Schemas</span></span>
<span data-ttu-id="1e0cb-103">Vous utilisez le schéma d’en-tête pour valider l’en-tête (segment MSH) de l’instance de message.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-103">You use the header schema to validate the header (MSH segment) of the message instance.</span></span> <span data-ttu-id="1e0cb-104">Le schéma d’accusé de réception vous permet de générer l’accusé de réception pour l’instance de message.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-104">You use the acknowledgment schema to generate the acknowledgment for the message instance.</span></span> <span data-ttu-id="1e0cb-105">Ce processus est commun à toutes les versions de schéma HL7.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-105">This process is common across all HL7 schema versions.</span></span>  
  
### <a name="to-create-the-header-and-acknowledgment-schemas"></a><span data-ttu-id="1e0cb-106">Pour créer les schémas d’en-tête et d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="1e0cb-106">To create the header and acknowledgment schemas</span></span>  
  
1.  <span data-ttu-id="1e0cb-107">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-107">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="1e0cb-108">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-108">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="1e0cb-109">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis sélectionnez **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-109">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then select **BTAHL7Projects**.</span></span>  
  
4.  <span data-ttu-id="1e0cb-110">Dans le **modèles** liste, sélectionnez **BTAHL7V2XCommon projet**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-110">In the **Templates** list, select **BTAHL7V2XCommon Project**.</span></span>  
  
5.  <span data-ttu-id="1e0cb-111">Dans le **nom** , tapez **Interrogative_2XSchemas**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-111">In the **Name** field, type **Interrogative_2XSchemas**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1e0cb-112">Dans l’Explorateur de solutions, notez que trois schémas (ACK_24_GLO_DEF.xsd, ACK_25_GLO_DEF.xsd et MSH_25_GLO_DEF.xsd) sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-112">In Solution Explorer, notice that three schemas (ACK_24_GLO_DEF.xsd, ACK_25_GLO_DEF.xsd, and MSH_25_GLO_DEF.xsd) are included in the project.</span></span>  
  
     <span data-ttu-id="1e0cb-113">Laissez Visual Studio ouvert.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-113">Leave Visual Studio open.</span></span>  
  
## <a name="step-1a-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="1e0cb-114">Étape 1 a : assigner une clé forte à l’Assembly et le déployer</span><span class="sxs-lookup"><span data-stu-id="1e0cb-114">Step 1A: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="1e0cb-115">Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-115">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="1e0cb-116">Pour affecter une clé forte et de déployer l’assembly</span><span class="sxs-lookup"><span data-stu-id="1e0cb-116">To assign a strong key and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="1e0cb-117">Démarrez une **invite de commandes Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-117">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="1e0cb-118">À la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes, remplacez votre répertoire à la \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator pour le dossier du didacticiel de HL7\SDK\Interrogative.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-118">At the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, change your directory to the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\Interrogative Tutorial folder.</span></span>  
  
3.  <span data-ttu-id="1e0cb-119">À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-119">At the command prompt, type **sn –k key.snk**, and then press **Enter**.</span></span> <span data-ttu-id="1e0cb-120">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-120">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e0cb-121">Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre assembly.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-121">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.</span></span>  
  
4.  <span data-ttu-id="1e0cb-122">Dans l’Explorateur de solutions, cliquez sur **Interrogative_2XSchemas** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-122">In Solution Explorer, right-click **Interrogative_2XSchemas** project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="1e0cb-123">Dans la boîte de dialogue Pages de propriétés Interrogative_2XSchemas, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-123">In the Interrogative_2XSchemas Property Pages dialog box, click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="1e0cb-124">Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="1e0cb-124">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
7.  <span data-ttu-id="1e0cb-125">Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\Interrogative didacticiel, cliquez sur **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-125">In the Assembly Key File dialog box, browse to \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="1e0cb-126">Dans la boîte de dialogue Pages de propriétés Interrogative_2XSchemas, cliquez sur **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-126">In the Interrogative_2XSchemas Property Pages dialog box, click **OK** to save your changes.</span></span>  
  
9. <span data-ttu-id="1e0cb-127">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **Interrogative_2XSchemas** de projet, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-127">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click **Interrogative_2XSchemas** project, and then click **Deploy**.</span></span> <span data-ttu-id="1e0cb-128">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-128">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e0cb-129">Si le message de déploiement approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="1e0cb-129">If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.</span></span>  
  
 <span data-ttu-id="1e0cb-130">Passez à [étape 2 : créer des schémas courants pour V2.4](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md).</span><span class="sxs-lookup"><span data-stu-id="1e0cb-130">Proceed to [Step 2: Create Common Schemas for V2.4](../../adapters-and-accelerators/accelerator-hl7/step-2-create-common-schemas-for-v2-4.md).</span></span>