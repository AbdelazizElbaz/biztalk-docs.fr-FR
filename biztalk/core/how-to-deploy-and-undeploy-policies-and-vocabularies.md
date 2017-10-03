---
title: "Comment déployer et annuler le déploiement de stratégies et des vocabulaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, policies
- policies, deploying
- deploying, vocabularies
- policies, undeploying
- vocabularies, deploying
ms.assetid: 9a7e3310-54b7-482c-8210-b4b11fde4c49
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef36df71459935b588f54c1dadc30ab02a7e722e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-and-undeploy-policies-and-vocabularies"></a><span data-ttu-id="b1bc0-102">Déploiement et annulation du déploiement des stratégies et vocabulaires</span><span class="sxs-lookup"><span data-stu-id="b1bc0-102">How to Deploy and Undeploy Policies and Vocabularies</span></span>
<span data-ttu-id="b1bc0-103">Vous pouvez utiliser l'Assistant Déploiement du moteur de règles pour déployer une stratégie ou annuler son déploiement.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-103">You can use the Rule Engine Deployment Wizard to deploy or undeploy a policy.</span></span>  
  
 <span data-ttu-id="b1bc0-104">Dans cet Assistant, quand vous tentez un déploiement, seules les versions de stratégie publiées sont visibles dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-104">In the Rule Engine Deployment Wizard, when you try to deploy, only published policy versions are shown in the drop-down list.</span></span> <span data-ttu-id="b1bc0-105">Lorsque vous essayez d’annuler le déploiement, uniquement déployé de stratégie versions s’affichent dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-105">When you try to undeploy, only deployed policy versions are shown in the drop-down list.</span></span>  
  
### <a name="to-deploy-or-undeploy-a-policy"></a><span data-ttu-id="b1bc0-106">Pour déployer une stratégie ou annuler son déploiement</span><span class="sxs-lookup"><span data-stu-id="b1bc0-106">To deploy or undeploy a policy</span></span>  
  
1.  <span data-ttu-id="b1bc0-107">Cliquez sur **Démarrer**, pointez sur **Program Files**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant de déploiement du moteur de règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-107">Click **Start**, point to **Program Files**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1bc0-108">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-108">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="b1bc0-109">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-109">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="b1bc0-110">Sur le **Assistant Déploiement du moteur de règles** page d’accueil, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-110">On the **Rules Engine Deployment Wizard** welcome page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="b1bc0-111">Sélectionnez **déployer la stratégie de** ou **annuler le déploiement de la stratégie**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-111">Select either **Deploy Policy** or **Undeploy Policy**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="b1bc0-112">Dans la liste déroulante, sélectionnez un ordinateur SQL Server disponible et la base de données, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-112">From the drop-down lists, select an available SQL Server computer and database, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1bc0-113">Le déploiement ne peut se faire que vers la base de données du magasin de règles pour laquelle vous êtes configuré.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-113">You can only deploy to the rule store database that you are configured against.</span></span> <span data-ttu-id="b1bc0-114">Toute tentative de déploiement vers une autre base de données générera une erreur.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-114">An attempt to deploy to a different DB will give an error.</span></span>  
  
5.  <span data-ttu-id="b1bc0-115">Dans la liste déroulante, sélectionnez une stratégie, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-115">From the drop-down list, select a policy, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1bc0-116">Quand vous tentez un déploiement, seules les versions de stratégie publiées sont visibles dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-116">When you try to deploy, only published policy versions are shown in the drop-down list.</span></span> <span data-ttu-id="b1bc0-117">Lorsque vous essayez d’annuler le déploiement, uniquement déployé de stratégie versions s’affichent dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-117">When you try to undeploy, only deployed policy versions are shown in the drop-down list.</span></span>  
  
6.  <span data-ttu-id="b1bc0-118">Passez en revue le serveur, base de données et les informations de stratégie, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-118">Review the server, database, and policy information, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="b1bc0-119">Suivez l'avancement du déploiement ou de son annulation. </span><span class="sxs-lookup"><span data-stu-id="b1bc0-119">Watch the progress of the deployment or undeployment.</span></span> <span data-ttu-id="b1bc0-120">Lorsqu’il est terminé, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-120">When it is finished, click **Next**.</span></span>  
  
8.  <span data-ttu-id="b1bc0-121">Passez en revue l’état d’achèvement du déploiement ou annulation du déploiement, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-121">Review the completion status of the deployment or undeployment, and then click **Finish**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1bc0-122">Vous pouvez également déployer ou annuler le déploiement d’une version de stratégie à partir de l’éditeur des règles d’entreprise en cliquant sur la version de stratégie, puis sur **déployer** ou **annuler le déploiement**.</span><span class="sxs-lookup"><span data-stu-id="b1bc0-122">You can also deploy or undeploy a policy version from within the Business Rule Composer by right-clicking the policy version and then clicking **Deploy** or **Undeploy**.</span></span>