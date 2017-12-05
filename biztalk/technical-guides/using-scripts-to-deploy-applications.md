---
title: "À l’aide de Scripts pour déployer des Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e683c5f-7576-4382-9952-d577cd00186c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bc96c3b591baf81806182b6c3e988a46dd208ba
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-scripts-to-deploy-applications"></a><span data-ttu-id="4d852-102">À l’aide de Scripts pour déployer des Applications</span><span class="sxs-lookup"><span data-stu-id="4d852-102">Using Scripts to Deploy Applications</span></span>
<span data-ttu-id="4d852-103">Vous devez utiliser des scripts pour déployer des applications BizTalk lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="4d852-103">You should use scripts to deploy BizTalk applications where possible.</span></span> <span data-ttu-id="4d852-104">Écriture de scripts permet de réduire le risque d’erreur humaine pendant le processus de déploiement.</span><span class="sxs-lookup"><span data-stu-id="4d852-104">Scripting reduces the risk of human error during the deployment process.</span></span> <span data-ttu-id="4d852-105">Vous devez également documenter vos procédures de déploiement en détail.</span><span class="sxs-lookup"><span data-stu-id="4d852-105">You should also document your deployment procedures in depth.</span></span> <span data-ttu-id="4d852-106">Vous devez documenter tout ce que vous ne pas générer de script avec des instructions très détaillées.</span><span class="sxs-lookup"><span data-stu-id="4d852-106">You should document anything that you do not script with very detailed steps.</span></span> <span data-ttu-id="4d852-107">Cela inclut les documenter les modifications vers des systèmes externes et au déploiement des composants de non Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4d852-107">This includes documenting any changes to external systems and to deployment of non-Microsoft components.</span></span>  
  
## <a name="using-btstask"></a><span data-ttu-id="4d852-108">À l’aide de BTSTask</span><span class="sxs-lookup"><span data-stu-id="4d852-108">Using BTSTask</span></span>  
 <span data-ttu-id="4d852-109">Vous pouvez utiliser BTSTask.exe un script de la création d’applications BizTalk, ainsi que pour importer existant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] packages .msi.</span><span class="sxs-lookup"><span data-stu-id="4d852-109">You can use BTSTask.exe to script the creation of BizTalk applications, as well as to import existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi packages.</span></span> <span data-ttu-id="4d852-110">Si la création des applications est l’objet d’un script, puis les packages peuvent être créées automatiquement à l’aide d’un processus automatisé sur un serveur de builds.</span><span class="sxs-lookup"><span data-stu-id="4d852-110">If the creation of the applications is scripted, then the packages can be automatically built using an automated process on a build server.</span></span>  
  
 <span data-ttu-id="4d852-111">Consultez les rubriques suivantes pour plus d’informations sur les scripts de déploiements d’applications BizTalk :</span><span class="sxs-lookup"><span data-stu-id="4d852-111">See the following topics for more information about scripting BizTalk application deployments:</span></span>  
  
-   <span data-ttu-id="4d852-112">[Déploiement et gestion des Applications BizTalk](http://go.microsoft.com/fwlink/?LinkId=154210) (http://go.microsoft.com/fwlink/?LinkId=154210)</span><span class="sxs-lookup"><span data-stu-id="4d852-112">[Deploying and Managing BizTalk Applications](http://go.microsoft.com/fwlink/?LinkId=154210) (http://go.microsoft.com/fwlink/?LinkId=154210)</span></span>  
  
-   <span data-ttu-id="4d852-113">[Présentation du déploiement d’Application BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=101599) (http://go.microsoft.com/fwlink/?LinkId=101599)</span><span class="sxs-lookup"><span data-stu-id="4d852-113">[Understanding BizTalk Server Application Deployment](http://go.microsoft.com/fwlink/?LinkId=101599) (http://go.microsoft.com/fwlink/?LinkId=101599)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d852-114">Ce dernier article s’applique également à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4d852-114">This latter article also applies to BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d852-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d852-115">See Also</span></span>  
 [<span data-ttu-id="4d852-116">Liste de contrôle : Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4d852-116">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)