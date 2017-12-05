---
title: "VisualStudioHostRestart (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0b82627-1552-479d-a083-cdc9fe4843c3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d98a3a5e497a4476de897c8008f3a9976812209a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="visualstudiohostrestart-application-deployment-sample"></a><span data-ttu-id="22c04-102">VisualStudioHostRestart (exemple de déploiement d'application)</span><span class="sxs-lookup"><span data-stu-id="22c04-102">VisualStudioHostRestart (Application Deployment Sample)</span></span>
<span data-ttu-id="22c04-103">Cette rubrique décrit l'utilisation de l'exemple de script VisualStudioHostRestart pour redémarrer l'instance d'un hôte exécutée sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="22c04-103">This topic explains how to use the VisualStudioHostRestart sample script to restart a host instance running under [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="22c04-104">Vous pouvez utiliser ce script lors du redéploiement des assemblys dans Visual Studio afin que le moteur d'exécution BizTalk Server récupère les modifications immédiatement.</span><span class="sxs-lookup"><span data-stu-id="22c04-104">You can use this script when redeploying assemblies in Visual Studio so that the BizTalk Server runtime immediately picks up the changes.</span></span> <span data-ttu-id="22c04-105">Vous pouvez également utiliser l'option pour redémarrer les instances de l'hôte, que vous pouvez définir dans les propriétés de déploiement du projet.</span><span class="sxs-lookup"><span data-stu-id="22c04-105">Alternatively, you can use the option to restart host instances, which you can set in Deployment properties for the project.</span></span> <span data-ttu-id="22c04-106">Pour plus d’informations, consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="22c04-106">For more information, see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="22c04-107">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="22c04-107">What This Sample Does</span></span>  
 <span data-ttu-id="22c04-108">Cet exemple de script effectue les actions ci-dessous dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="22c04-108">This sample script performs the following actions, in order:</span></span>  
  
1.  <span data-ttu-id="22c04-109">arrêt des instances de l'hôte In-process sur l'ordinateur local ;</span><span class="sxs-lookup"><span data-stu-id="22c04-109">Stops all in-process host instances on the local computer.</span></span>  
  
2.  <span data-ttu-id="22c04-110">démarrage des instances de l'hôte In-process sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="22c04-110">Starts all in-process host instances on the local computer.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="22c04-111">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="22c04-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="22c04-112">L’exemple se trouve dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dossier d’installation, comme suit :  *\<exemples de chemin\>*\Application Deployment\VisualStudioHostRestart.</span><span class="sxs-lookup"><span data-stu-id="22c04-112">The sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder, as follows: *\<Samples path\>*\Application Deployment\VisualStudioHostRestart.</span></span>  
  
 <span data-ttu-id="22c04-113">L'exemple inclut le fichier suivant :</span><span class="sxs-lookup"><span data-stu-id="22c04-113">The sample includes the following file:</span></span>  
  
-   <span data-ttu-id="22c04-114">RestartBizTalkHostInstances.vbs</span><span class="sxs-lookup"><span data-stu-id="22c04-114">RestartBizTalkHostInstances.vbs</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="22c04-115">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="22c04-115">How to Use This Sample</span></span>  
 <span data-ttu-id="22c04-116">Les procédures suivantes permettent d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="22c04-116">Use the following procedures to run this sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="22c04-117">Pour exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="22c04-117">To run the sample</span></span>  
  
-   <span data-ttu-id="22c04-118">Exécutez RestartBizTalkHostInstances.vbs.</span><span class="sxs-lookup"><span data-stu-id="22c04-118">Run RestartBizTalkHostInstances.vbs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c04-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22c04-119">See Also</span></span>  
 <span data-ttu-id="22c04-120">[Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="22c04-120">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 <span data-ttu-id="22c04-121">[Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="22c04-121">[Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="22c04-122">Déploiement des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="22c04-122">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)