---
title: BtarnClean | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BtarnClean utility
- assemblies, undeploying
- BTARN, deleting artifacts
- orchestrations, unenlisting
- ports, stopping
- orchestrations, stopping
- ports, deleting
- BTARN, BtarnClean utility
ms.assetid: fbecbb88-9b18-4b4b-a286-0bfa783f2320
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa8e448d4799329a798cc7b33f222b42c4a28b4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="btarnclean"></a><span data-ttu-id="9ac2b-102">BtarnClean</span><span class="sxs-lookup"><span data-stu-id="9ac2b-102">BtarnClean</span></span>
<span data-ttu-id="9ac2b-103">Vous utilisez l’utilitaire BtarnClean pour nettoyer [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] artefacts sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-103">You use the BtarnClean utility to clean [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] artifacts off a computer.</span></span> <span data-ttu-id="9ac2b-104">Cette opération inclut les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="9ac2b-104">This includes the following actions:</span></span>  
  
-   <span data-ttu-id="9ac2b-105">L’arrêt et désinscription de toutes les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] orchestrations</span><span class="sxs-lookup"><span data-stu-id="9ac2b-105">Stopping and unenlisting all the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] orchestrations</span></span>  
  
-   <span data-ttu-id="9ac2b-106">Arrêt et suppression de tous les ports associés</span><span class="sxs-lookup"><span data-stu-id="9ac2b-106">Stopping and deleting all the associated ports</span></span>  
  
-   <span data-ttu-id="9ac2b-107">Annulation du déploiement de tous les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Assemblys Solutions.BTARN.\*</span><span class="sxs-lookup"><span data-stu-id="9ac2b-107">Undeploying all the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.BTARN.\* assemblies</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="9ac2b-108">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="9ac2b-108">Location in SDK</span></span>  
 <span data-ttu-id="9ac2b-109">\<*lecteur*\>\Program Files\ Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK</span><span class="sxs-lookup"><span data-stu-id="9ac2b-109">\<*drive*\>\Program Files\ Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK</span></span>  
  
## <a name="running-btarnclean"></a><span data-ttu-id="9ac2b-110">Exécution de BtarnClean</span><span class="sxs-lookup"><span data-stu-id="9ac2b-110">Running BtarnClean</span></span>  
  
#### <a name="to-run-btarnclean"></a><span data-ttu-id="9ac2b-111">Pour exécuter BtarnClean</span><span class="sxs-lookup"><span data-stu-id="9ac2b-111">To run BtarnClean</span></span>  
  
1.  <span data-ttu-id="9ac2b-112">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-112">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="9ac2b-113">Déplacer vers \< *lecteur*\>\ programme Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\\.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-113">Move to \<*drive*\>\ Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\\.</span></span>  
  
3.  <span data-ttu-id="9ac2b-114">À l'invite de commandes, tapez **BtarnClean**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-114">At the command prompt, type **BtarnClean**, and then press ENTER.</span></span>  
  
     <span data-ttu-id="9ac2b-115">L'utilitaire vous invite à confirmer que vous souhaitez continuer.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-115">The utility prompts you to verify that you want to continue.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac2b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="9ac2b-116">Remarks</span></span>  
 <span data-ttu-id="9ac2b-117">Si vous exécutez l'utilitaire BtarnClean sur un ordinateur disposant d'un artefact BizTalk qui dépend d'autres artefacts, BtarnClean indique qu'il ne peut pas supprimer cet artefact.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-117">If you run the BtarnClean utility on a computer that has a BizTalk artifact that depends on other artifacts, BtarnClean will indicate that it cannot remove the artifact.</span></span> <span data-ttu-id="9ac2b-118">L'utilitaire laisse cet artefact en place et continue à supprimer d'autres artefacts.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-118">The utility will leave that artifact in place and continue to remove other artifacts.</span></span> <span data-ttu-id="9ac2b-119">Vous pouvez supprimer des dépendances, puis réexécuter l'utilitaire.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-119">You can remove dependencies, and then run the utility again.</span></span>  
  
 <span data-ttu-id="9ac2b-120">Si vous exécutez l'utilitaire BtarnClean sur un ordinateur qui fait partie d'un déploiement sur plusieurs ordinateurs, la suppression des artefacts affecte le reste des serveurs de ce déploiement.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-120">If you run the BtarnClean utility on a computer that is part of a multi-computer deployment, removing the artifacts will affect the rest of the servers in that deployment.</span></span>  
  
 <span data-ttu-id="9ac2b-121">Si vous exécutez l'utilitaire BtarnClean lorsqu'il existe plusieurs processus créés par des développeurs, l'utilitaire ne supprime pas les processus qui sont encore en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-121">If you run the BtarnClean utility when multiple processes created by developers exist, the utility will not remove processes that are still in use.</span></span>  
  
 <span data-ttu-id="9ac2b-122">L'utilitaire BtarnClean ne supprime pas un emplacement de réception principal si l'artefact de l'utilisateur utilise cet emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-122">The BtarnClean utility will not remove a primary receive location if a user's artifact uses that receive location.</span></span> <span data-ttu-id="9ac2b-123">Si c'est le cas, vous devez supprimer le port de réception.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-123">If this is the case, you must delete the receive port.</span></span>  
  
 <span data-ttu-id="9ac2b-124">Si vous souhaitez annuler la configuration [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] après l’exécution de l’utilitaire, exécutez Configuration.exe /u à partir de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier.</span><span class="sxs-lookup"><span data-stu-id="9ac2b-124">If you want to unconfigure [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] after running the utility, run Configuration.exe /u from the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac2b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ac2b-125">See Also</span></span>  
 [<span data-ttu-id="9ac2b-126">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="9ac2b-126">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)