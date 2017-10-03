---
title: "Comment s’inscrire et supprimer BizTalk Assembly Viewer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f80b906-0a9e-4bcd-984d-db4550f2e51f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deae453be1a89049f223e2da9813e449d68eeb07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-register-and-remove-the-biztalk-assembly-viewer"></a><span data-ttu-id="89fcc-102">Inscription et suppression de BizTalk Assembly Viewer</span><span class="sxs-lookup"><span data-stu-id="89fcc-102">How to Register and Remove the BizTalk Assembly Viewer</span></span>
<span data-ttu-id="89fcc-103">BizTalk Assembly Viewer n'est pas inscrit automatiquement lors de la configuration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="89fcc-103">The BizTalk Assembly Viewer is not registered automatically during BizTalk Server setup.</span></span> <span data-ttu-id="89fcc-104">Pour inscrire ou supprimer BizTalk Assembly Viewer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="89fcc-104">To register or remove the BizTalk Assembly Viewer, follow these steps.</span></span>  
  
### <a name="to-add-assembly-viewer-to-the-windows-registry"></a><span data-ttu-id="89fcc-105">Pour ajouter Assembly Viewer au registre Windows</span><span class="sxs-lookup"><span data-stu-id="89fcc-105">To add Assembly Viewer to the Windows registry</span></span>  
  
1.  <span data-ttu-id="89fcc-106">À partir de la **Démarrer** menu, cliquez sur **exécuter**.</span><span class="sxs-lookup"><span data-stu-id="89fcc-106">From the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="89fcc-107">Dans la boîte de dialogue Exécuter, tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="89fcc-107">In the Run dialog box, type **cmd**.</span></span>  
  
3.  <span data-ttu-id="89fcc-108">À partir de la ligne de commande, accédez à \< *dossier d’Installation de BizTalk Server*> \Developer Tools\ où BTSAsmExt.dll réside.</span><span class="sxs-lookup"><span data-stu-id="89fcc-108">From the command line, navigate to \<*BizTalk Server Installation Folder*>\Developer Tools\ where BTSAsmExt.dll resides.</span></span>  
  
4.  <span data-ttu-id="89fcc-109">Sur la ligne de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="89fcc-109">At the command line, type:</span></span>  
  
     <span data-ttu-id="89fcc-110">regsvr32 BTSAsmExt.dll</span><span class="sxs-lookup"><span data-stu-id="89fcc-110">regsvr32 BTSAsmExt.dll</span></span>  
  
5.  <span data-ttu-id="89fcc-111">Pour commencer à utiliser Assembly Viewer, déconnectez-vous et reconnectez-vous sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="89fcc-111">To begin using Assembly View, log off and then log back onto the computer.</span></span>  
  
### <a name="to-remove-assembly-viewer-from-the-windows-registry"></a><span data-ttu-id="89fcc-112">Pour supprimer Assembly Viewer du registre Windows</span><span class="sxs-lookup"><span data-stu-id="89fcc-112">To remove Assembly Viewer from the Windows registry</span></span>  
  
1.  <span data-ttu-id="89fcc-113">À partir de la **Démarrer** menu, cliquez sur **exécuter**.</span><span class="sxs-lookup"><span data-stu-id="89fcc-113">From the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="89fcc-114">Dans le **exécuter** boîte de dialogue, tapez **cmd**.</span><span class="sxs-lookup"><span data-stu-id="89fcc-114">In the **Run** dialog box, type **cmd**.</span></span>  
  
3.  <span data-ttu-id="89fcc-115">À partir de la ligne de commande, accédez à \< *dossier d’Installation de BizTalk Server*> \Developer Tools\ où BTSAsmExt.dll réside.</span><span class="sxs-lookup"><span data-stu-id="89fcc-115">From the command line, navigate to \<*BizTalk Server Installation Folder*>\Developer Tools\ where BTSAsmExt.dll resides.</span></span>  
  
4.  <span data-ttu-id="89fcc-116">Sur la ligne de commande, tapez :</span><span class="sxs-lookup"><span data-stu-id="89fcc-116">At the command line, type:</span></span>  
  
     <span data-ttu-id="89fcc-117">regsvr32/u BTSAsmExt.dll</span><span class="sxs-lookup"><span data-stu-id="89fcc-117">regsvr32/u BTSAsmExt.dll</span></span>  
  
5.  <span data-ttu-id="89fcc-118">Pour terminer la suppression, déconnectez-vous et reconnectez-vous sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="89fcc-118">To complete the removal, log off and then log back onto the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89fcc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89fcc-119">See Also</span></span>  
 [<span data-ttu-id="89fcc-120">Afficher des assemblys avec BizTalk Assembly Viewer</span><span class="sxs-lookup"><span data-stu-id="89fcc-120">Viewing Assemblies with the BizTalk Assembly Viewer</span></span>](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)