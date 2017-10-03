---
title: "Comment supprimer une stratégie à partir d’une Application et le groupe BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, policies
- managing [policies], applications
- managing [policies], deleting
- groups, policies
- managing [policies], groups
- applications, policies
ms.assetid: e9882cb3-8808-4258-a107-a24905290288
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4bb4b162d90811a4eddaa513556ecb1f6c6cd8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-policy-from-an-application-and-the-biztalk-group"></a><span data-ttu-id="8f5bc-102">Suppression d'une stratégie d'une application et du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-102">How to Remove a Policy from an Application and the BizTalk Group</span></span>
<span data-ttu-id="8f5bc-103">Cette rubrique explique comment utiliser la console Administration de BizTalk Server ou la ligne de commande pour supprimer une stratégie d'une application et de la base de données du moteur de règles du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-103">This topic describes how to use the BizTalk Server Administration console or the command-line to remove a policy from an application and the Rule Engine database for the BizTalk group.</span></span>  
  
 <span data-ttu-id="8f5bc-104">Avant de supprimer une stratégie, gardez les points importants suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="8f5bc-104">Before removing a policy, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="8f5bc-105">Vous ne pouvez pas supprimer une stratégie déployée.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-105">You cannot remove a deployed policy.</span></span> <span data-ttu-id="8f5bc-106">Vous devez tout d’abord annuler le déploiement la stratégie, comme décrit dans [comment déployer ou annuler le déploiement d’une stratégie](../core/how-to-deploy-or-undeploy-a-policy.md).</span><span class="sxs-lookup"><span data-stu-id="8f5bc-106">You must first undeploy the policy, as described in [How to Deploy or Undeploy a Policy](../core/how-to-deploy-or-undeploy-a-policy.md).</span></span> <span data-ttu-id="8f5bc-107">L'annulation du déploiement d'une stratégie la rend inactive et celle-ci ne fonctionne donc plus dans les applications qui l'utilisent dans le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-107">Undeploying a policy makes it inactive so that it no longer functions in any application that uses it in the BizTalk group.</span></span>  
  
-   <span data-ttu-id="8f5bc-108">Le fait de supprimer une stratégie supprime également celle-ci de la base de données du moteur de règles.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-108">Removing a policy deletes it from the Rule Engine database.</span></span> <span data-ttu-id="8f5bc-109">Si vous souhaitez pouvoir la réutiliser, vous devez l'exporter dans un fichier .xml avant de la supprimer.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-109">If you want to use this policy again, you should export it to an .xml file before removing it.</span></span> <span data-ttu-id="8f5bc-110">Pour obtenir des instructions, consultez [comment exporter une stratégie](../core/how-to-export-a-policy.md).</span><span class="sxs-lookup"><span data-stu-id="8f5bc-110">For instructions, see [How to Export a Policy](../core/how-to-export-a-policy.md).</span></span>  
  
-   <span data-ttu-id="8f5bc-111">Si la stratégie est utilisée par d'autres applications, elle ne pourra plus l'être par la suite.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-111">If the policy is used by other applications, it will no longer be in effect for the other applications.</span></span> <span data-ttu-id="8f5bc-112">Vérifiez que vous n'avez plus besoin de la stratégie avec d'autres applications qui lui font référence avant de la supprimer.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-112">Verify that you no longer want to use the policy for any other applications that reference it before you remove it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f5bc-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8f5bc-113">Prerequisites</span></span>  
 <span data-ttu-id="8f5bc-114">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-114">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="8f5bc-115">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="8f5bc-115">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-a-policy"></a><span data-ttu-id="8f5bc-116">Pour supprimer une stratégie</span><span class="sxs-lookup"><span data-stu-id="8f5bc-116">To remove a policy</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="8f5bc-117">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8f5bc-117">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="8f5bc-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-118">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="8f5bc-119">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk contenant la stratégie à supprimer, puis développez l’application contenant la stratégie</span><span class="sxs-lookup"><span data-stu-id="8f5bc-119">In the console tree, expand  **BizTalk Server Administration**, expand the BizTalk group containing the policy to remove, and then expand the application containing the policy</span></span>  
  
3.  <span data-ttu-id="8f5bc-120">Cliquez sur **stratégies**, avec le bouton droit de la stratégie, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-120">Click **Policies**, right-click the policy, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="8f5bc-121">À l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8f5bc-121">Using the command line</span></span>  
  
1.  <span data-ttu-id="8f5bc-122">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-122">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="8f5bc-123">Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="8f5bc-123">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="8f5bc-124">**BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="8f5bc-124">**BTSTask RemoveResource** [**/ApplicationName:***value*] **/Luid:***value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="8f5bc-125">Exemple :</span><span class="sxs-lookup"><span data-stu-id="8f5bc-125">Example:</span></span>  
  
     <span data-ttu-id="8f5bc-126">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"Rule/Policy1/1.0 »**</span><span class="sxs-lookup"><span data-stu-id="8f5bc-126">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"Rule/Policy1/1.0"**</span></span>  
  
    |<span data-ttu-id="8f5bc-127">Paramètre</span><span class="sxs-lookup"><span data-stu-id="8f5bc-127">Parameter</span></span>|<span data-ttu-id="8f5bc-128"> Description</span><span class="sxs-lookup"><span data-stu-id="8f5bc-128">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="8f5bc-129">**/ ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="8f5bc-129">**/ApplicationName**</span></span>|<span data-ttu-id="8f5bc-130">Nom de l'application BizTalk contenant la stratégie à supprimer.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-130">Name of the BizTalk application containing the policy to delete.</span></span> <span data-ttu-id="8f5bc-131">L'application par défaut est utilisée si ce paramètre n'est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-131">If this parameter is not specified, the default application is used.</span></span>|  
    |<span data-ttu-id="8f5bc-132">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="8f5bc-132">**/Luid**</span></span>|<span data-ttu-id="8f5bc-133">Identificateur unique local (LUID) de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-133">Locally unique identifier (LUID) of the policy.</span></span> <span data-ttu-id="8f5bc-134">Vous pouvez obtenir l’identificateur LUID à l’aide de la **ListApp** de commande, comme décrit dans [commande ListApp](../core/listapp-command.md).</span><span class="sxs-lookup"><span data-stu-id="8f5bc-134">You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="8f5bc-135">**/ Serveur**</span><span class="sxs-lookup"><span data-stu-id="8f5bc-135">**/Server**</span></span>|<span data-ttu-id="8f5bc-136">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-136">Name of the SQL Server instance hosting the BizTalk Management database.</span></span> <span data-ttu-id="8f5bc-137">Obligatoire si vous spécifiez le paramètre Database.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-137">Required if you specify the Database parameter.</span></span> <span data-ttu-id="8f5bc-138">Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-138">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
    |<span data-ttu-id="8f5bc-139">**/ Base de données**</span><span class="sxs-lookup"><span data-stu-id="8f5bc-139">**/Database**</span></span>|<span data-ttu-id="8f5bc-140">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-140">Name of the BizTalk Management database.</span></span> <span data-ttu-id="8f5bc-141">Obligatoire si vous spécifiez le paramètre Server.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-141">Required if you specify the Server parameter.</span></span> <span data-ttu-id="8f5bc-142">Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8f5bc-142">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f5bc-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f5bc-143">See Also</span></span>  
 [<span data-ttu-id="8f5bc-144">Gestion des stratégies</span><span class="sxs-lookup"><span data-stu-id="8f5bc-144">Managing Policies</span></span>](../core/managing-policies.md)