---
title: "Annuler le déploiement d’autres projets de didacticiel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fce837f-1853-4d5d-a680-8ae2a974c750
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b00e829ad569790b257e1d5f0c16290cca68d176
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="undeploy-other-tutorial-projects"></a><span data-ttu-id="1ff32-102">Annuler le déploiement d’autres projets de didacticiel</span><span class="sxs-lookup"><span data-stu-id="1ff32-102">Undeploy Other Tutorial Projects</span></span>
<span data-ttu-id="1ff32-103">Lorsque vous déployez un BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) didacticiels, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] stocke les fichiers de l’assembly du didacticiel dans la base de données de Configuration (également appelée la base de données BizTalk Management) et le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="1ff32-103">When you deploy a BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) tutorials, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] stores the tutorial assembly files in the Configuration database (also known as the BizTalk Management database) and the global assembly cache.</span></span> <span data-ttu-id="1ff32-104">Si vous avez exécuté une autre [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] didacticiel et déployé les assemblys que vous avez créé dans ce didacticiel, vous pouvez rencontrer les erreurs lorsque vous testez vos assemblys dans les trois parties du didacticiel de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="1ff32-104">If you have run another [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] tutorial, and deployed the assemblies that you created in that tutorial, you may encounter errors when you test your assemblies in the three parts of the Batching tutorial.</span></span> <span data-ttu-id="1ff32-105">Cela peut se produire, car vous ne pouvez déployer un schéma de message à la fois.</span><span class="sxs-lookup"><span data-stu-id="1ff32-105">This may occur because you can only deploy one message schema at one time.</span></span>  
  
 <span data-ttu-id="1ff32-106">Vous pouvez éviter ces erreurs par l’annulation du déploiement des assemblys que vous avez déployé dans les didacticiels précédents.</span><span class="sxs-lookup"><span data-stu-id="1ff32-106">You can avoid these errors by undeploying assemblies that you deployed in previous tutorials.</span></span> <span data-ttu-id="1ff32-107">Vous pouvez redéployer l’assembly ultérieurement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1ff32-107">You can re-deploy the assembly later if needed.</span></span>  
  
 <span data-ttu-id="1ff32-108">Avant l’annulation du déploiement d’un assembly, vous devez désinscrire les orchestrations dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1ff32-108">Before undeploying an assembly, you need to unenlist orchestrations in the assembly.</span></span> <span data-ttu-id="1ff32-109">Vous devez également supprimer toute référence à l’assembly que vous souhaitez annuler le déploiement, à partir de n’importe quel autre assembly que vous souhaitez conserver déployé.</span><span class="sxs-lookup"><span data-stu-id="1ff32-109">You also need to remove any reference to the assembly that you want to undeploy, from any other assembly that you want to keep deployed.</span></span> <span data-ttu-id="1ff32-110">Une alternative consiste à supprimer toutes les DLL associées à un didacticiel, avant de démarrer un autre didacticiel.</span><span class="sxs-lookup"><span data-stu-id="1ff32-110">An alternative is to delete all DLLs associated with one tutorial, before starting another tutorial.</span></span>  
  
### <a name="to-undeploy-an-assembly"></a><span data-ttu-id="1ff32-111">Pour annuler le déploiement d’un assembly</span><span class="sxs-lookup"><span data-stu-id="1ff32-111">To undeploy an assembly</span></span>  
  
1.  <span data-ttu-id="1ff32-112">Désinscrire les orchestrations utilisées dans l’assembly que vous souhaitez annuler le déploiement en cliquant sur l’orchestration dans l’Explorateur BizTalk de Visual Studio, puis en cliquant sur **désinscrire**.</span><span class="sxs-lookup"><span data-stu-id="1ff32-112">Unenlist orchestrations used in the assembly that you want to undeploy by clicking the orchestration in BizTalk Explorer of Visual Studio, and then clicking **Unenlist**.</span></span>  
  
2.  <span data-ttu-id="1ff32-113">Dans n’importe quel assembly que vous souhaitez conserver déployé, supprimez les références aux assemblys que vous souhaitez annuler le déploiement.</span><span class="sxs-lookup"><span data-stu-id="1ff32-113">In any assembly that you want to keep deployed, remove references to assemblies that you want to undeploy.</span></span> <span data-ttu-id="1ff32-114">Cliquez avec le bouton droit sur la référence dans l’Explorateur de solutions, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="1ff32-114">Right click the reference in Solution Explorer, and then click **Remove**.</span></span>  
  
3.  <span data-ttu-id="1ff32-115">Ouvrez l’Explorateur BizTalk, cliquez sur l’assembly que vous souhaitez annuler le déploiement, puis cliquez sur **annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="1ff32-115">Open BizTalk Explorer, right-click the assembly that you want to undeploy, and then click **Undeploy**.</span></span>  
  
 <span data-ttu-id="1ff32-116">Pour plus d’informations sur l’annulation du déploiement d’un assembly, consultez « Annulation du déploiement un Assembly à l’aide de l’Explorateur BizTalk » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="1ff32-116">For more information about undeploying an assembly, see "Undeploying an Assembly Using BizTalk Explorer" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff32-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ff32-117">See Also</span></span>  
 [<span data-ttu-id="1ff32-118">Préparation à l’utilisation du didacticiel de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="1ff32-118">Preparing to Use the Batching Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)