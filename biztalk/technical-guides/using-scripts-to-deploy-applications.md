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
ms.openlocfilehash: 4566a810489a9f6c46424a525908aa5a2fbb6bee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-scripts-to-deploy-applications"></a><span data-ttu-id="7f7f5-102">À l’aide de Scripts pour déployer des Applications</span><span class="sxs-lookup"><span data-stu-id="7f7f5-102">Using Scripts to Deploy Applications</span></span>
<span data-ttu-id="7f7f5-103">Vous devez utiliser des scripts pour déployer des applications BizTalk lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="7f7f5-103">You should use scripts to deploy BizTalk applications where possible.</span></span> <span data-ttu-id="7f7f5-104">Écriture de scripts permet de réduire le risque d’erreur humaine pendant le processus de déploiement.</span><span class="sxs-lookup"><span data-stu-id="7f7f5-104">Scripting reduces the risk of human error during the deployment process.</span></span> <span data-ttu-id="7f7f5-105">Vous devez également documenter vos procédures de déploiement en détail.</span><span class="sxs-lookup"><span data-stu-id="7f7f5-105">You should also document your deployment procedures in depth.</span></span> <span data-ttu-id="7f7f5-106">Vous devez documenter tout ce que vous ne pas générer de script avec des instructions très détaillées.</span><span class="sxs-lookup"><span data-stu-id="7f7f5-106">You should document anything that you do not script with very detailed steps.</span></span> <span data-ttu-id="7f7f5-107">Cela inclut les documenter les modifications vers des systèmes externes et au déploiement des composants de non Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7f7f5-107">This includes documenting any changes to external systems and to deployment of non-Microsoft components.</span></span>  
  
## <a name="using-btstask"></a><span data-ttu-id="7f7f5-108">À l’aide de BTSTask</span><span class="sxs-lookup"><span data-stu-id="7f7f5-108">Using BTSTask</span></span>  
 <span data-ttu-id="7f7f5-109">Vous pouvez utiliser BTSTask.exe un script de la création d’applications BizTalk, ainsi que pour importer existant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] packages .msi.</span><span class="sxs-lookup"><span data-stu-id="7f7f5-109">You can use BTSTask.exe to script the creation of BizTalk applications, as well as to import existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi packages.</span></span> <span data-ttu-id="7f7f5-110">Si la création des applications est l’objet d’un script, puis les packages peuvent être créées automatiquement à l’aide d’un processus automatisé sur un serveur de builds.</span><span class="sxs-lookup"><span data-stu-id="7f7f5-110">If the creation of the applications is scripted, then the packages can be automatically built using an automated process on a build server.</span></span>  
  
 <span data-ttu-id="7f7f5-111">Consultez les rubriques suivantes pour plus d’informations sur les scripts de déploiements d’applications BizTalk :</span><span class="sxs-lookup"><span data-stu-id="7f7f5-111">See the following topics for more information about scripting BizTalk application deployments:</span></span>  
  
-   <span data-ttu-id="7f7f5-112">[Déploiement et gestion des Applications BizTalk](http://go.microsoft.com/fwlink/?LinkId=154210) (http://go.microsoft.com/fwlink/?LinkId=154210)</span><span class="sxs-lookup"><span data-stu-id="7f7f5-112">[Deploying and Managing BizTalk Applications](http://go.microsoft.com/fwlink/?LinkId=154210) (http://go.microsoft.com/fwlink/?LinkId=154210)</span></span>  
  
-   <span data-ttu-id="7f7f5-113">[Présentation du déploiement d’Application BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=101599) (http://go.microsoft.com/fwlink/?LinkId=101599)</span><span class="sxs-lookup"><span data-stu-id="7f7f5-113">[Understanding BizTalk Server Application Deployment](http://go.microsoft.com/fwlink/?LinkId=101599) (http://go.microsoft.com/fwlink/?LinkId=101599)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f7f5-114">Ce dernier article s’applique également aux [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f7f5-114">This latter article also applies to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7f5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f7f5-115">See Also</span></span>  
 [<span data-ttu-id="7f7f5-116">Liste de vérification : Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7f7f5-116">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)