---
title: "Comment publier une stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, publishing
- managing [policies], publishing
- publishing, policies
ms.assetid: 730c57a7-526f-40ca-8610-88216558e375
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a64c4764459eecd0d1a4fceedf7a7e8e61159503
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-publish-a-policy"></a><span data-ttu-id="76ba9-102">Publication d'une stratégie</span><span class="sxs-lookup"><span data-stu-id="76ba9-102">How to Publish a Policy</span></span>
<span data-ttu-id="76ba9-103">Cette rubrique décrit comment publier une stratégie dans un groupe BizTalk à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="76ba9-103">This topic describes how to use the BizTalk Server Administration console to publish a policy in a BizTalk group.</span></span> <span data-ttu-id="76ba9-104">Une stratégie de publication rend disponibles à ajouter à une application BizTalk, comme décrit dans [comment ajouter une stratégie à une Application](../core/how-to-add-a-policy-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="76ba9-104">Publishing a policy makes it available to add to a BizTalk application, as described in [How to Add a Policy to an Application](../core/how-to-add-a-policy-to-an-application.md).</span></span>  
  
 <span data-ttu-id="76ba9-105">Pour pouvoir publier une stratégie, elle doit exister dans la base de données de gestion BizTalk pour le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="76ba9-105">Before you can publish a policy, it must exist in the Rule Engine database for the BizTalk group.</span></span> <span data-ttu-id="76ba9-106">Il existe trois façons d’importer une stratégie dans la base de données du moteur de règles :</span><span class="sxs-lookup"><span data-stu-id="76ba9-106">There are three ways to import a policy into the Rule Engine database:</span></span>  
  
-   <span data-ttu-id="76ba9-107">Vous pouvez importer une application contenant une stratégie.</span><span class="sxs-lookup"><span data-stu-id="76ba9-107">You can import an application that contains a policy.</span></span> <span data-ttu-id="76ba9-108">Lors de cette opération, la stratégie est automatiquement importée dans la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="76ba9-108">When you do this, the policy is automatically imported into the Rule Engine database.</span></span>  
  
-   <span data-ttu-id="76ba9-109">Vous pouvez explicitement importer une stratégie de la base de données du moteur de règles à l’aide de la console d’administration ou de BTSTask, comme décrit dans [comment importer une stratégie](../core/how-to-import-a-policy.md).</span><span class="sxs-lookup"><span data-stu-id="76ba9-109">You can explicitly import a policy into the Rule Engine database by using the administration console or BTSTask, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).</span></span>  
  
-   <span data-ttu-id="76ba9-110">Vous pouvez ajouter une stratégie à la base de données du moteur de règles à l’aide de l’Assistant Déploiement du moteur de règles, comme décrit dans [comment déployer et annuler le déploiement de stratégies et vocabulaires](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span><span class="sxs-lookup"><span data-stu-id="76ba9-110">You can add a policy to the Rule Engine database by using the Rule Engine Deployment Wizard, as described in [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76ba9-111">Si vous publiez une stratégie qui risque d'être écrasée par une autre stratégie que vous importez, vous devez préciser l'option spécifiant qu'un vocabulaire publié ne doit jamais être remplacé.</span><span class="sxs-lookup"><span data-stu-id="76ba9-111">While a published policy can be overwritten by another policy that you import, should you specify this option, a published vocabulary can never be overwritten.</span></span> <span data-ttu-id="76ba9-112">Pour mettre à jour un vocabulaire publié, vous devez le supprimer de la base de données du moteur de règles, puis importer la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="76ba9-112">To update a published vocabulary, you must remove it from the Rule Engine database and then import the new version.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="76ba9-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="76ba9-113">Prerequisites</span></span>  
 <span data-ttu-id="76ba9-114">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="76ba9-114">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="76ba9-115">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="76ba9-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-publish-a-policy"></a><span data-ttu-id="76ba9-116">Pour publier une stratégie</span><span class="sxs-lookup"><span data-stu-id="76ba9-116">To publish a policy</span></span>  
  
1.  <span data-ttu-id="76ba9-117">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="76ba9-117">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="76ba9-118">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk contenant la stratégie à publier, **Applications**, puis développez  **\<tous les artefacts >**.</span><span class="sxs-lookup"><span data-stu-id="76ba9-118">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the policy to publish, expand **Applications**, and then expand **\<All Artifacts>**.</span></span>  
  
3.  <span data-ttu-id="76ba9-119">Cliquez sur **stratégies**, avec le bouton droit de la stratégie, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="76ba9-119">Click **Policies**, right-click the policy, and then click **Publish**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76ba9-120">Pour publier une stratégie, tous les assemblys qui sont référencés par la stratégie doivent être installés dans le Global Assembly Cache (GAC) de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur avant d’ouvrir **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="76ba9-120">In order to publish a policy, any assemblies that are referenced by the policy must be installed in the Global Assembly Cache (GAC) of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer before you open **BizTalk Server Administration**.</span></span> <span data-ttu-id="76ba9-121">Lorsque **Administration de BizTalk Server** est ouvert, il gère un cache des assemblys qui sont installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="76ba9-121">When **BizTalk Server Administration** is opened, it maintains a cache of the assemblies that are installed into the GAC.</span></span> <span data-ttu-id="76ba9-122">Ce cache n’est pas mis à jour jusqu'à ce que **Administration de BizTalk Server** est fermée et rouverte.</span><span class="sxs-lookup"><span data-stu-id="76ba9-122">This cache is not updated until **BizTalk Server Administration** is closed and reopened.</span></span> <span data-ttu-id="76ba9-123">Si vous essayez de publier une stratégie et la publication échoue en raison d’un assembly référencé n’est pas installé dans le GAC, vous devez fermer **Administration de BizTalk Server**, installer l’assembly référencé dans le GAC, ouvrir  **Administration de BizTalk Server**, puis publier la stratégie.</span><span class="sxs-lookup"><span data-stu-id="76ba9-123">If you attempt to publish a policy and publication fails because a referenced assembly is not installed in the GAC you must close **BizTalk Server Administration**, install the referenced assembly into the GAC, open **BizTalk Server Administration**, and then publish the policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ba9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76ba9-124">See Also</span></span>  
 [<span data-ttu-id="76ba9-125">Gestion des stratégies</span><span class="sxs-lookup"><span data-stu-id="76ba9-125">Managing Policies</span></span>](../core/managing-policies.md)