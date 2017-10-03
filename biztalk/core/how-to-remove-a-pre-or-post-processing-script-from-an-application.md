---
title: "Comment supprimer un Script de pré-traitement ou de post-traitement à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [scripts], deleting
- deleting, scripts
- managing [applications], scripts
- scripts, deleting
- applications, scripts
ms.assetid: 7911f098-97f2-4a5d-87fe-20b55231113e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25d60bdec2857d9d84042e184f0bbfbb2307806a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-pre--or-post-processing-script-from-an-application"></a><span data-ttu-id="526fc-102">Suppression d'un script de pré-traitement ou de post-traitement d'une application</span><span class="sxs-lookup"><span data-stu-id="526fc-102">How to Remove a Pre- or Post-processing Script from an Application</span></span>
<span data-ttu-id="526fc-103">Cette rubrique décrit comment supprimer un script de prétraitement ou de post-traitement dans une application à l'aide de la console Administration de BizTalk Server ou de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="526fc-103">This topic describes how to use the BizTalk Server Administration console or the command line to remove a pre- or post-processing script from an application.</span></span> <span data-ttu-id="526fc-104">Cette opération supprime le script de la base de données de gestion BizTalk, afin qu'il ne soit pas exporté dans le fichier .msi de l'application.</span><span class="sxs-lookup"><span data-stu-id="526fc-104">This removes the script from the BizTalk Management database, so that it will not be exported in the application .msi file.</span></span> <span data-ttu-id="526fc-105">Elle ne supprime pas le script du système de fichiers local, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="526fc-105">This does not remove the script from the local file system, if it exists there.</span></span>  
  
 <span data-ttu-id="526fc-106">Si l'application contenant le script a été installé sur le système de fichiers local et que le script a été conçu de manière à s'exécuter lors de la désinstallation, vous devez supprimer le script du système de fichiers pour éviter qu'il ne s'exécute lors de la désinstallation de l'application.</span><span class="sxs-lookup"><span data-stu-id="526fc-106">If the application containing the script has been installed on the local file system, and the script is designed to run during uninstallation, you must remove the script from the file system to prevent it from running when the application is uninstalled.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="526fc-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="526fc-107">Prerequisites</span></span>  
 <span data-ttu-id="526fc-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="526fc-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="526fc-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="526fc-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-a-script-from-an-application"></a><span data-ttu-id="526fc-110">Pour supprimer un script d'une application</span><span class="sxs-lookup"><span data-stu-id="526fc-110">To remove a script from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="526fc-111">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="526fc-111">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="526fc-112">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="526fc-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="526fc-113">Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant le script à supprimer, puis l'application contenant le script.</span><span class="sxs-lookup"><span data-stu-id="526fc-113">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the script to remove, and then expand the application containing the script.</span></span>  
  
3.  <span data-ttu-id="526fc-114">Cliquez sur le **ressources** dossier, cliquez sur le script, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="526fc-114">Click the **Resources** folder, right-click the script, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="526fc-115">À l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="526fc-115">Using the command line</span></span>  
  
1.  <span data-ttu-id="526fc-116">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="526fc-116">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="526fc-117">Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="526fc-117">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="526fc-118">**BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="526fc-118">**BTSTask RemoveResource** [**/ApplicationName:***value*] **/Luid:***value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="526fc-119">Exemple :</span><span class="sxs-lookup"><span data-stu-id="526fc-119">Example:</span></span>  
  
     <span data-ttu-id="526fc-120">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApplication:MyScript.vbs »**</span><span class="sxs-lookup"><span data-stu-id="526fc-120">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApplication:MyScript.vbs"**</span></span>  
  
    |<span data-ttu-id="526fc-121">Paramètre</span><span class="sxs-lookup"><span data-stu-id="526fc-121">Parameter</span></span>|<span data-ttu-id="526fc-122"> Description</span><span class="sxs-lookup"><span data-stu-id="526fc-122">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="526fc-123">**/ ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="526fc-123">**/ApplicationName**</span></span>|<span data-ttu-id="526fc-124">Nom de l'application BizTalk contenant le script BizTalk à supprimer.</span><span class="sxs-lookup"><span data-stu-id="526fc-124">Name of the BizTalk application containing the BizTalk script to delete.</span></span> <span data-ttu-id="526fc-125">Si le nom comprend des espaces, vous devez le placer entre guillemets doubles (").</span><span class="sxs-lookup"><span data-stu-id="526fc-125">If the name includes spaces, it must be enclosed in double quotation marks (").</span></span> <span data-ttu-id="526fc-126">L'application par défaut est utilisée si ce paramètre n'est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="526fc-126">If this parameter is not specified, the default application is used.</span></span>|  
    |<span data-ttu-id="526fc-127">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="526fc-127">**/Luid**</span></span>|<span data-ttu-id="526fc-128">Identificateur unique local (LUID) du script.</span><span class="sxs-lookup"><span data-stu-id="526fc-128">Locally unique identifier (LUID) of the script.</span></span> <span data-ttu-id="526fc-129">Vous pouvez obtenir l’identificateur LUID à l’aide de la [commande ListApp](../core/listapp-command.md).</span><span class="sxs-lookup"><span data-stu-id="526fc-129">You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="526fc-130">**/ Serveur**</span><span class="sxs-lookup"><span data-stu-id="526fc-130">**/Server**</span></span>|<span data-ttu-id="526fc-131">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.</span><span class="sxs-lookup"><span data-stu-id="526fc-131">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="526fc-132">Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="526fc-132">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="526fc-133">Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).</span><span class="sxs-lookup"><span data-stu-id="526fc-133">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="526fc-134">Exemples :</span><span class="sxs-lookup"><span data-stu-id="526fc-134">Examples:</span></span><br /><br /> <span data-ttu-id="526fc-135">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="526fc-135">Server=MyServer</span></span><br /><br /> <span data-ttu-id="526fc-136">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="526fc-136">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="526fc-137">Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="526fc-137">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="526fc-138">**/ Base de données**</span><span class="sxs-lookup"><span data-stu-id="526fc-138">**/Database**</span></span>|<span data-ttu-id="526fc-139">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="526fc-139">Name of the BizTalk Management database.</span></span> <span data-ttu-id="526fc-140">Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="526fc-140">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="526fc-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="526fc-141">See Also</span></span>  
 <span data-ttu-id="526fc-142">[Gestion des Scripts de pré-traitement et post-traitement](../core/managing-pre-and-post-processing-scripts.md) </span><span class="sxs-lookup"><span data-stu-id="526fc-142">[Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md) </span></span>  
 [<span data-ttu-id="526fc-143">Commande RemoveResource</span><span class="sxs-lookup"><span data-stu-id="526fc-143">RemoveResource Command</span></span>](../core/removeresource-command.md)