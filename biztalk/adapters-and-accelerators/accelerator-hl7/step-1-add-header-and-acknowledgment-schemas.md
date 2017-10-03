---
title: "Étape 1 : Ajouter des schémas d’en-tête et d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 808132bf-02e7-4ff4-b914-9fae5d27e5fd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b5fb871bed9f6a4f54261db7e54587c65244344
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-add-header-and-acknowledgment-schemas"></a><span data-ttu-id="d319e-102">Étape 1 : Ajouter des schémas d’en-tête et d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="d319e-102">Step 1: Add Header and Acknowledgment Schemas</span></span>
<span data-ttu-id="d319e-103">Dans cette étape, vous créez un projet basé sur le modèle de projet de BTAHL72XCommon.</span><span class="sxs-lookup"><span data-stu-id="d319e-103">In this step, you create a new project based on the BTAHL72XCommon Project template.</span></span> <span data-ttu-id="d319e-104">Ce modèle contient les trois schémas courants pour les en-têtes de message (MSH_25_GLO_DEF.xsd) et les accusés de réception (ACK_24_GLO_DEF.xsd) et (ACK_25_GLO_DEF.xsd).</span><span class="sxs-lookup"><span data-stu-id="d319e-104">This template contains the three common schemas for message headers (MSH_25_GLO_DEF.xsd) and acknowledgments (ACK_24_GLO_DEF.xsd) and (ACK_25_GLO_DEF.xsd).</span></span> <span data-ttu-id="d319e-105">Vous devez inclure ces schémas dans un projet, ainsi que de BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) génère et/ou valide correctement les en-têtes de message et les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="d319e-105">You must include these schemas in a project so that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) builds and/or validates the message headers and acknowledgments correctly.</span></span> <span data-ttu-id="d319e-106">Ce processus est commun à toutes les versions de schéma de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.</span><span class="sxs-lookup"><span data-stu-id="d319e-106">This process is common across all schema versions of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2.X.</span></span>  
  
 <span data-ttu-id="d319e-107">Vous également créez une clé forte, affectez à l’assembly, puis déployez l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d319e-107">You also create a strong key, assign it to the assembly, and then deploy the assembly.</span></span> <span data-ttu-id="d319e-108">La clé forte fournit la sécurité et l’identité à l’assembly et n’est nécessaire pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="d319e-108">The strong key provides security and identity to the assembly, and is necessary for deployment.</span></span> <span data-ttu-id="d319e-109">Lorsque vous déployez l’assembly, il est stocké dans la base de données de Configuration (également appelée la base de données BizTalk Management) et le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="d319e-109">When you deploy the assembly, it is stored in the Configuration database (also known as the BizTalk Management database) and the global assembly cache (GAC).</span></span>  
  
### <a name="to-create-the-project-and-add-header-and-acknowledgment-schemas"></a><span data-ttu-id="d319e-110">Pour créer le projet et ajouter des schémas d’en-tête et d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="d319e-110">To create the project and add header and acknowledgment schemas</span></span>  
  
1.  <span data-ttu-id="d319e-111">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="d319e-111">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d319e-112">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis cliquez sur **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="d319e-112">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then click **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="d319e-113">Dans le **modèles** , cliquez sur **BTAHL7V2XCommon projet**.</span><span class="sxs-lookup"><span data-stu-id="d319e-113">In the **Templates** list, click **BTAHL7V2XCommon Project**.</span></span>  
  
4.  <span data-ttu-id="d319e-114">Dans le **nom** , tapez **BTAHL7V2XCommon** comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="d319e-114">In the **Name** box, type **BTAHL7V2XCommon** as the project name.</span></span>  
  
5.  <span data-ttu-id="d319e-115">Dans le **emplacement** , naviguez jusqu’au  **\<**  *lecteur***: > \Batching didacticiel**.</span><span class="sxs-lookup"><span data-stu-id="d319e-115">In the **Location** box, browse to **\<***drive***:>\Batching Tutorial**.</span></span>  
  
6.  <span data-ttu-id="d319e-116">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d319e-116">Click **OK**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d319e-117">Dans l’Explorateur de solutions, les trois schémas (MSH_25_GLO_DEF.xsd, ACK_24_GLO_DEF.xsd et ACK_25_GLO_DEF.xsd) sont inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="d319e-117">In Solution Explorer, three schemas (MSH_25_GLO_DEF.xsd, ACK_24_GLO_DEF.xsd, and ACK_25_GLO_DEF.xsd) are included in the project.</span></span>  
  
### <a name="to-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="d319e-118">Pour attribuer une clé forte à l’assembly et le déployer</span><span class="sxs-lookup"><span data-stu-id="d319e-118">To assign a strong key to the assembly and deploy</span></span>  
  
1.  <span data-ttu-id="d319e-119">Ouvrez  **[!INCLUDE[vs2012](../../includes/vs2012-md.md)] invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="d319e-119">Open **[!INCLUDE[vs2012](../../includes/vs2012-md.md)] Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="d319e-120">Sur le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] invite de commandes, accédez à la  **\<**  *lecteur***> : \Batching didacticiel** dossier.</span><span class="sxs-lookup"><span data-stu-id="d319e-120">On the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt, browse to the **\<***drive***>:\Batching Tutorial** folder.</span></span>  
  
3.  <span data-ttu-id="d319e-121">À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="d319e-121">At the command prompt, type **sn –k key.snk**, and then press ENTER.</span></span> <span data-ttu-id="d319e-122">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="d319e-122">Ensure that a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d319e-123">Si le message approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre assembly.</span><span class="sxs-lookup"><span data-stu-id="d319e-123">If the correct message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your assembly.</span></span>  
  
4.  <span data-ttu-id="d319e-124">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V2Xcommon projet**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d319e-124">In Solution Explorer, right-click **BTAHL7V2Xcommon Project**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="d319e-125">Dans le **Page de propriétés du projet BTAHL7V2XCommon** boîte de dialogue, cliquez sur **signature**.</span><span class="sxs-lookup"><span data-stu-id="d319e-125">In the **BTAHL7V2XCommon Project Property Page** dialog box, click **Signing**.</span></span>  
  
6.  <span data-ttu-id="d319e-126">Vérifiez **signer l’assembly** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="d319e-126">Check **Sign the assembly** check box.</span></span>  
  
7.  <span data-ttu-id="d319e-127">Dans **choisir un nom fort** déroulante de fichier de clé de liste, sélectionnez  **\<Parcourir... >**.</span><span class="sxs-lookup"><span data-stu-id="d319e-127">In **Choose a Strong name** key file drop down list select **\<Browse…>**.</span></span>  
  
8.  <span data-ttu-id="d319e-128">Accédez à \< *lecteur*> : \Batching Tutorial, sélectionnez **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="d319e-128">Browse to \<*drive*>:\Batching Tutorial, select **key.snk**, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="d319e-129">Dans la fenêtre de Pages de propriétés du projet BTAHL7V2XCommon, cliquez sur **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="d319e-129">In the BTAHL7V2XCommon Project Property Pages window, click **OK** to save your changes.</span></span>  
  
10. <span data-ttu-id="d319e-130">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V2Xcommon projet**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="d319e-130">In Solution Explorer, right-click **BTAHL7V2Xcommon Project**, and then click **Deploy**.</span></span> <span data-ttu-id="d319e-131">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="d319e-131">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d319e-132">Si le message de déploiement approprié n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de votre déploiement.</span><span class="sxs-lookup"><span data-stu-id="d319e-132">If the correct deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your deployment.</span></span>  
  
 <span data-ttu-id="d319e-133">Passez à [étape 2 : ajouter des schémas courants pour v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="d319e-133">Proceed to [Step 2: Add Common Schemas for v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md).</span></span>