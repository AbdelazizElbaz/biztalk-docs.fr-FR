---
title: "Comment supprimer une Orchestration à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, orchestrations
- deleting, orchestrations
- managing [orchestrations], deleting
- orchestrations, applications
- orchestrations, deleting
ms.assetid: e6d635ea-3513-42de-a667-b56c536e5328
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef4909f5430ae2d0435d519823abe9735cbc1cc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-an-orchestration-from-an-application"></a><span data-ttu-id="93e01-102">Suppression d'une orchestration dans une application</span><span class="sxs-lookup"><span data-stu-id="93e01-102">How to Remove an Orchestration from an Application</span></span>
<span data-ttu-id="93e01-103">Cette rubrique décrit comment supprimer une orchestration dans une application BizTalk à l'aide de la console Administration de BizTalk Server ou de l'invite de commande.</span><span class="sxs-lookup"><span data-stu-id="93e01-103">This topic describes how to use the BizTalk Server Administration console or the command line to remove an orchestration from a BizTalk application.</span></span> <span data-ttu-id="93e01-104">La suppression d'une orchestration dans une application entraîne également sa suppression dans la base de données de gestion BizTalk pour le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="93e01-104">Removing an orchestration from an application also deletes it from the BizTalk Management database for the BizTalk group.</span></span>  
  
 <span data-ttu-id="93e01-105">Lorsque vous supprimez une orchestration, voici ce qui se produit :</span><span class="sxs-lookup"><span data-stu-id="93e01-105">When you remove an orchestration, the following occurs:</span></span>  
  
-   <span data-ttu-id="93e01-106">L'orchestration est supprimée de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="93e01-106">The orchestration is deleted from the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="93e01-107">L'assembly BizTalk qui contient l'orchestration est supprimé de la base de données de gestion BizTalk, mais pas du système de fichiers local ou du Global Assembly Cache (GAC), s'il existe dans ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="93e01-107">The BizTalk assembly that contains the orchestration is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.</span></span>  
  
-   <span data-ttu-id="93e01-108">Par conséquent, tous les artefacts contenus dans l'assembly sont également supprimés de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="93e01-108">As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are deleted from the BizTalk Management database as well.</span></span>  
  
 <span data-ttu-id="93e01-109">Avant de supprimer une orchestration dans une application, gardez les points suivants à l'esprit :</span><span class="sxs-lookup"><span data-stu-id="93e01-109">Before removing an orchestration from an application, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="93e01-110">Si d'autres artefacts ont des dépendances avec cette orchestration ou avec les artefacts contenus dans l'assembly également supprimé, ils ne fonctionneront plus correctement une fois l'orchestration supprimée.</span><span class="sxs-lookup"><span data-stu-id="93e01-110">If other artifacts have dependencies on this orchestration or the artifacts contained in the assembly that will also be removed, they will no longer function correctly when you remove the orchestration.</span></span> <span data-ttu-id="93e01-111">Pour des informations générales sur les dépendances, consultez [des dépendances et déploiement d’applications](../core/dependencies-and-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="93e01-111">For background information about dependencies, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).</span></span>  
  
-   <span data-ttu-id="93e01-112">Vous ne pouvez pas supprimer d'orchestrations ayant des instances en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="93e01-112">You cannot remove an orchestration that has running instances.</span></span> <span data-ttu-id="93e01-113">Vous devez mettre fin à toute instance en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="93e01-113">You must terminate any running instances.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="93e01-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="93e01-114">Prerequisites</span></span>  
 <span data-ttu-id="93e01-115">Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="93e01-115">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="93e01-116">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="93e01-116">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-an-orchestration-from-an-application"></a><span data-ttu-id="93e01-117">Pour supprimer une orchestration dans une application</span><span class="sxs-lookup"><span data-stu-id="93e01-117">To remove an orchestration from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="93e01-118">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="93e01-118">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="93e01-119">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="93e01-119">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="93e01-120">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **Applications**, puis développez l’application contenant l’orchestration que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="93e01-120">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to remove.</span></span>  
  
3.  <span data-ttu-id="93e01-121">Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, puis cliquez sur **désinscrire**.</span><span class="sxs-lookup"><span data-stu-id="93e01-121">Click **Orchestrations**, right-click the orchestration, and then click **Unenlist**.</span></span>  
  
4.  <span data-ttu-id="93e01-122">Sélectionnez l’orchestration, pointez sur **vue**, puis cliquez sur **informations sur l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="93e01-122">Select the orchestration, point to **View**, and then click **Instance Information**.</span></span>  
  
5.  <span data-ttu-id="93e01-123">Dans le volet de résultats de requête, cliquez sur les instances d’orchestration, puis cliquez sur **Terminate**.</span><span class="sxs-lookup"><span data-stu-id="93e01-123">In the query results pane, right-click the orchestration instances, and then click **Terminate**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93e01-124">Vous pouvez désinscrire, arrêter les instances en cours d’exécution et arrêter tous les orchestrations dans une application à la fois à l’aide de l’option arrêt complet de l’application, comme décrit dans [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="93e01-124">You can unenlist, terminate running instances, and stop all of the orchestrations in an application at once by using the Full Stop option for the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).</span></span>  
  
6.  <span data-ttu-id="93e01-125">Cliquez sur **Orchestrations**, avec le bouton droit de l’orchestration, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="93e01-125">Click **Orchestrations**, right-click the orchestration, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="93e01-126">À l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="93e01-126">Using the command line</span></span>  
  
1.  <span data-ttu-id="93e01-127">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="93e01-127">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="93e01-128">Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="93e01-128">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="93e01-129">**BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="93e01-129">**BTSTask RemoveResource** [**/ApplicationName:***value*] **/Luid:***value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="93e01-130">Exemple :</span><span class="sxs-lookup"><span data-stu-id="93e01-130">Example:</span></span>  
  
     <span data-ttu-id="93e01-131">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 0123456789ABCDEF »**</span><span class="sxs-lookup"><span data-stu-id="93e01-131">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
    |<span data-ttu-id="93e01-132">Paramètre</span><span class="sxs-lookup"><span data-stu-id="93e01-132">Parameter</span></span>|<span data-ttu-id="93e01-133"> Description</span><span class="sxs-lookup"><span data-stu-id="93e01-133">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="93e01-134">**/ ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="93e01-134">**/ApplicationName**</span></span>|<span data-ttu-id="93e01-135">Nom de l'application BizTalk contenant l'orchestration à supprimer.</span><span class="sxs-lookup"><span data-stu-id="93e01-135">Name of the BizTalk application containing the orchestration to delete.</span></span> <span data-ttu-id="93e01-136">Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).</span><span class="sxs-lookup"><span data-stu-id="93e01-136">If the name includes spaces, you must enclose it in double quotation marks (").</span></span> <span data-ttu-id="93e01-137">L'application par défaut est utilisée si ce paramètre n'est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="93e01-137">If this parameter is not specified, the default application is used.</span></span>|  
    |<span data-ttu-id="93e01-138">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="93e01-138">**/Luid**</span></span>|<span data-ttu-id="93e01-139">Identificateur unique local (LUID) de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="93e01-139">Locally unique identifier (LUID) of the orchestration.</span></span> <span data-ttu-id="93e01-140">Vous pouvez obtenir l’identificateur LUID à l’aide de la [commande ListApp](../core/listapp-command.md).</span><span class="sxs-lookup"><span data-stu-id="93e01-140">You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="93e01-141">**/ Serveur**</span><span class="sxs-lookup"><span data-stu-id="93e01-141">**/Server**</span></span>|<span data-ttu-id="93e01-142">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="93e01-142">Name of the SQL Server instance hosting the BizTalk Management database.</span></span> <span data-ttu-id="93e01-143">Obligatoire si vous spécifiez le paramètre Database.</span><span class="sxs-lookup"><span data-stu-id="93e01-143">Required if you specify the Database parameter.</span></span> <span data-ttu-id="93e01-144">Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="93e01-144">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
    |<span data-ttu-id="93e01-145">**/ Base de données**</span><span class="sxs-lookup"><span data-stu-id="93e01-145">**/Database**</span></span>|<span data-ttu-id="93e01-146">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="93e01-146">Name of the BizTalk Management database.</span></span> <span data-ttu-id="93e01-147">Obligatoire si vous spécifiez le paramètre Server.</span><span class="sxs-lookup"><span data-stu-id="93e01-147">Required if you specify the Server parameter.</span></span> <span data-ttu-id="93e01-148">Si les paramètres Database et Server ne sont pas spécifiés, la base de données de gestion BizTalk du groupe par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="93e01-148">If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93e01-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93e01-149">See Also</span></span>  
 <span data-ttu-id="93e01-150">[La gestion des Orchestrations](../core/managing-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="93e01-150">[Managing Orchestrations](../core/managing-orchestrations.md) </span></span>  
 [<span data-ttu-id="93e01-151">Commande RemoveResource</span><span class="sxs-lookup"><span data-stu-id="93e01-151">RemoveResource Command</span></span>](../core/removeresource-command.md)