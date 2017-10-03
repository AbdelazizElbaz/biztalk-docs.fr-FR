---
title: "Étape 3 : Assigner un nom fort à l’Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies
- message enrichment tutorial, strong name assemblies
- strong name assemblies
ms.assetid: 8709e4e1-b428-42af-ba3c-08225c17a9eb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85c8b74a40ee5a3e265e68197c97b1d9560daffe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-assign-a-strong-name-to-the-assembly"></a><span data-ttu-id="d23a6-102">Étape 3 : Assigner un nom fort à l’Assembly</span><span class="sxs-lookup"><span data-stu-id="d23a6-102">Step 3: Assign a Strong Name to the Assembly</span></span>
<span data-ttu-id="d23a6-103">Dans cette étape, vous créez et attribuez un nom fort pour le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembly.</span><span class="sxs-lookup"><span data-stu-id="d23a6-103">In this step, you create and assign a strong name for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] assembly.</span></span> <span data-ttu-id="d23a6-104">Un assembly avec nom fort présente plusieurs avantages de sécurité et est nécessaire pour déployer votre projet dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="d23a6-104">A strong-named assembly provides several security benefits and is required in order to deploy your project in the global assembly cache (GAC).</span></span> <span data-ttu-id="d23a6-105">Un nom fort garantit l’unicité de l’assembly en assignant une signature numérique et une paire de clés unique.</span><span class="sxs-lookup"><span data-stu-id="d23a6-105">A strong name guarantees the uniqueness of the assembly by assigning a digital signature and a unique key pair.</span></span> <span data-ttu-id="d23a6-106">Cela protège également l’enregistrement en ligne de l’assembly en veillant à ce que personne ne peut générer une version ultérieure de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d23a6-106">This also protects the lineage of the assembly by ensuring that no one can generate a subsequent version of the assembly.</span></span> <span data-ttu-id="d23a6-107">Enfin, un nom fort fournit un contrôle d’intégrité fort pour garantir que le contenu de l’assembly n’a pas modifié, car vous les avez générées.</span><span class="sxs-lookup"><span data-stu-id="d23a6-107">Lastly, a strong name provides a strong integrity check to guarantee that the contents of the assembly have not changed since you built it.</span></span>  
  
### <a name="to-assign-a-strong-name-to-the-assembly"></a><span data-ttu-id="d23a6-108">Pour attribuer un nom fort à l’assembly</span><span class="sxs-lookup"><span data-stu-id="d23a6-108">To assign a strong name to the assembly</span></span>  
  
1.  <span data-ttu-id="d23a6-109">Démarrer  **[!INCLUDE[vs2012](../../includes/vs2012-md.md)] invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="d23a6-109">Start **[!INCLUDE[vs2012](../../includes/vs2012-md.md)] Command Prompt**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d23a6-110">Si vous avez déjà créé une clé de nom fort, vous pouvez la réutiliser.</span><span class="sxs-lookup"><span data-stu-id="d23a6-110">If you have already created a strong name key, you can reuse it.</span></span>  
  
2.  <span data-ttu-id="d23a6-111">À l’invite de commandes, accédez au**\<*lecteur*> : \Tutorial\BTAHL7V22Common** (où \< *lecteur*> est le lecteur d’installation lettre), puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="d23a6-111">At the command prompt, move to**\<*drive*>:\Tutorial\BTAHL7V22Common** (where \<*drive*> is your installation drive letter) and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="d23a6-112">À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="d23a6-112">At the command prompt, type **sn –k key.snk**, and then press **Enter**.</span></span> <span data-ttu-id="d23a6-113">Un message s’affiche indiquant que [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] écriture de la paire de clés dans le fichier de clé key.snk.</span><span class="sxs-lookup"><span data-stu-id="d23a6-113">A message appears indicating that [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] wrote the key pair to the key file key.snk.</span></span>  
  
4.  <span data-ttu-id="d23a6-114">Dans l’Explorateur de solutions, cliquez sur le **BTAHL7V22Common** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d23a6-114">In Solution Explorer, right-click the **BTAHL7V22Common** project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="d23a6-115">Dans la boîte de dialogue Pages de propriétés BTAHL7V22Common, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="d23a6-115">In the BTAHL7V22Common Property Pages dialog box, click **Assembly**.</span></span>  
  
6.  <span data-ttu-id="d23a6-116">Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="d23a6-116">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
7.  <span data-ttu-id="d23a6-117">Dans la boîte de dialogue de fichier de clé d’Assembly, accédez à  **\<* lecteur*> : \Tutorial\BTAHL7V22Common\key.snk**, cliquez sur **ouvrez**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d23a6-117">In the Assembly Key File dialog box, browse to **\<*drive*>:\Tutorial\BTAHL7V22Common\key.snk**, click **Open**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="d23a6-118">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V22Common**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="d23a6-118">In Solution Explorer, right-click **BTAHL7V22Common**, and then click **Deploy**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="d23a6-119">Crée un assembly que vous pouvez référencer à partir de votre prochain projet.</span><span class="sxs-lookup"><span data-stu-id="d23a6-119"> creates an assembly that you can reference from your next project.</span></span>  
  
9. <span data-ttu-id="d23a6-120">Répétez les étapes 4 à 8 pour le projet BTAHL7V2XCommon.</span><span class="sxs-lookup"><span data-stu-id="d23a6-120">Repeat steps 4 through 8 for the BTAHL7V2XCommon project.</span></span>  
  
 <span data-ttu-id="d23a6-121">Passez à [étape 4 : créer les schémas](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="d23a6-121">Proceed to [Step 4: Create the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d23a6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d23a6-122">See Also</span></span>  
 [<span data-ttu-id="d23a6-123">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="d23a6-123">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)