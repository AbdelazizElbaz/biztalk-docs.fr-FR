---
title: "Comment déployer ou annuler le déploiement d’une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [policies], undeploying
- deploying, policies
- policies, deploying
- managing [policies], deploying
- policies, undeploying
- undeploying, policies
ms.assetid: 9d26d4fe-9673-4baa-9927-02efda56b7a4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4913dbfa6f3d027d5540234b5af9370eb69f67a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-or-undeploy-a-policy"></a><span data-ttu-id="ada4d-102">Déploiement ou annulation du déploiement d'une stratégie</span><span class="sxs-lookup"><span data-stu-id="ada4d-102">How to Deploy or Undeploy a Policy</span></span>
<span data-ttu-id="ada4d-103">Cette rubrique explique comment déployer ou annuler le déploiement d'une stratégie manuellement à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ada4d-103">This topic describes how to use the BizTalk Server Administration console to deploy or undeploy a policy manually.</span></span> <span data-ttu-id="ada4d-104">Par ailleurs, le démarrage d'une application déploie automatiquement les stratégies qu'elle contient, et son arrêt annule automatiquement leur déploiement.</span><span class="sxs-lookup"><span data-stu-id="ada4d-104">In addition, starting an application automatically deploys any policies it contains, and stopping an application automatically undeploys its policies.</span></span> <span data-ttu-id="ada4d-105">Le déploiement d'une stratégie l'applique dans l'application qui l'utilise.</span><span class="sxs-lookup"><span data-stu-id="ada4d-105">Deploying a policy puts it into effect in the application that uses it.</span></span> <span data-ttu-id="ada4d-106">L'annulation du déploiement d'une stratégie la rend inactive et celle-ci ne fonctionne donc plus dans les applications qui l'utilisent dans le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ada4d-106">Undeploying a policy makes it inactive so that it no longer functions in any application that uses it in the BizTalk group.</span></span>  
  
 <span data-ttu-id="ada4d-107">Lorsque vous déployez ou annulez le déploiement d'une stratégie, gardez les points importants suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="ada4d-107">When deploying or undeploying a policy, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="ada4d-108">Pour pouvoir déployer une stratégie, elle doit exister dans la base de données de gestion BizTalk pour le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ada4d-108">Before you can deploy a policy, it must exist in the Rule Engine database for the BizTalk group.</span></span> <span data-ttu-id="ada4d-109">Si vous importez une application qui contient une stratégie, la stratégie est automatiquement importée dans la base de données du moteur de règles, ou vous pouvez explicitement importer une stratégie de la base de données du moteur de règles à l’aide de la console d’administration ou de BTSTask, comme décrit dans [Comment importer une stratégie](../core/how-to-import-a-policy.md).</span><span class="sxs-lookup"><span data-stu-id="ada4d-109">If you import an application that contains a policy, the policy is automatically imported into the Rule Engine database, or you can explicitly import a policy into the Rule Engine database by using the administration console or BTSTask, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).</span></span> <span data-ttu-id="ada4d-110">Vous pouvez également ajouter une stratégie à la base de données du moteur de règles à l’aide de l’Assistant Déploiement du moteur de règles, comme décrit dans [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span><span class="sxs-lookup"><span data-stu-id="ada4d-110">Alternatively, you can add a policy to the Rule Engine database by using the Rule Engine Deployment Wizard, as described in [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span></span>  
  
-   <span data-ttu-id="ada4d-111">Avant de pouvoir déployer une stratégie, elle doit être publiée, comme décrit dans [comment publier une stratégie](../core/how-to-publish-a-policy.md).</span><span class="sxs-lookup"><span data-stu-id="ada4d-111">Before you can deploy a policy, it must be published, as described in [How to Publish a Policy](../core/how-to-publish-a-policy.md).</span></span>  
  
-   <span data-ttu-id="ada4d-112">Une stratégie déployée n'est pas modifiable.</span><span class="sxs-lookup"><span data-stu-id="ada4d-112">A deployed policy cannot be modified.</span></span> <span data-ttu-id="ada4d-113">Pour modifier une stratégie déployée, vous devez d'abord annuler son déploiement.</span><span class="sxs-lookup"><span data-stu-id="ada4d-113">If you want to modify a deployed policy, you must first undeploy it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ada4d-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ada4d-114">Prerequisites</span></span>  
 <span data-ttu-id="ada4d-115">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ada4d-115">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="ada4d-116">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="ada4d-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-deploy-or-undeploy-a-policy"></a><span data-ttu-id="ada4d-117">Pour déployer une stratégie ou annuler son déploiement</span><span class="sxs-lookup"><span data-stu-id="ada4d-117">To deploy or undeploy a policy</span></span>  
  
1.  <span data-ttu-id="ada4d-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ada4d-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ada4d-119">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant la stratégie que vous souhaitez déployer ou annuler le déploiement, puis cliquez sur  **\<tous les artefacts >**.</span><span class="sxs-lookup"><span data-stu-id="ada4d-119">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the policy that you want to deploy or undeploy, and then expand **\<All Artifacts>**.</span></span>  
  
3.  <span data-ttu-id="ada4d-120">Cliquez sur **stratégies**, avec le bouton droit de la stratégie, puis cliquez sur **déployer** ou **annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="ada4d-120">Click **Policies**, right-click the policy, and then click **Deploy** or **Undeploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada4d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ada4d-121">See Also</span></span>  
 <span data-ttu-id="ada4d-122">[Gestion des stratégies](../core/managing-policies.md) </span><span class="sxs-lookup"><span data-stu-id="ada4d-122">[Managing Policies](../core/managing-policies.md) </span></span>  
 [<span data-ttu-id="ada4d-123">Comment démarrer et arrêter une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="ada4d-123">How to Start and Stop a BizTalk Application</span></span>](../core/how-to-start-and-stop-a-biztalk-application.md)