---
title: "Comment supprimer un Assembly .NET, certificat ou autre artefact de ressource à partir d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directories, deleting
- managing [.NET assemblies], deleting
- managing [applications], COM components
- managing [applications], deleting artifcats
- managing [certificates], deleting
- deleting, binding files
- binding files, deleting
- managing, COM components
- COM components, deleting
- managing [artifacts], deleting
- .NET assemblies, deleting
- deleting, virtual directories
- deleting, definitions [BAM]
- applications, .NET assemblies
- certificates, deleting
- deleting, .NET assemblies
- deleting, artifacts
- deleting, certificates
ms.assetid: b84eebac-261d-495f-80cd-ddda5bb08bef
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12196886285a84b391eb3037064f36f08aa5b1fe
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-remove-a-net-assembly-certificate-or-other-resource-artifact-from-an-application"></a><span data-ttu-id="0d191-102">Suppression d'un assembly .NET, d'un certificat ou d'un autre artefact de ressource d'une application</span><span class="sxs-lookup"><span data-stu-id="0d191-102">How to Remove a .NET Assembly, Certificate, or Other Resource Artifact from an Application</span></span>
<span data-ttu-id="0d191-103">Cette rubrique explique comment supprimer les artefacts de ressource suivants d'une application BizTalk à l'aide de la console Administration de BizTalk Server ou de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="0d191-103">This topic describes how to use the BizTalk Server Administration console or the command line to remove the following resource artifacts from a BizTalk application.</span></span> <span data-ttu-id="0d191-104">L'utilisation des procédures de cette rubrique supprime l'artefact de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0d191-104">Using the procedures in this topic removes the artifact from the BizTalk Management database.</span></span> <span data-ttu-id="0d191-105">Elle ne supprime pas l'artefact du système de fichiers, du magasin de certificats, des services IIS (Internet Information Services) ou du registre Windows s'il existe à ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="0d191-105">It does not remove the artifact from the file system, certificate store, Internet Information Services (IIS), or the Windows registry, if it exists in any of these locations.</span></span> <span data-ttu-id="0d191-106">Par ailleurs, si vous supprimez un fichier de liaison, les liaisons restantes ne sont pas modifiées : seul le fichier de liaison est supprimé.</span><span class="sxs-lookup"><span data-stu-id="0d191-106">In addition, if you remove a binding file, the bindings remain unchanged – only the binding file is removed.</span></span>  
  
-   <span data-ttu-id="0d191-107">assemblys .NET</span><span class="sxs-lookup"><span data-stu-id="0d191-107">.NET assemblies</span></span>  
  
-   <span data-ttu-id="0d191-108">composants des services COM</span><span class="sxs-lookup"><span data-stu-id="0d191-108">COM components</span></span>  
  
-   <span data-ttu-id="0d191-109">Certificats</span><span class="sxs-lookup"><span data-stu-id="0d191-109">Certificates</span></span>  
  
-   <span data-ttu-id="0d191-110">Fichiers ad hoc</span><span class="sxs-lookup"><span data-stu-id="0d191-110">Ad hoc files</span></span>  
  
-   <span data-ttu-id="0d191-111">définitions BAM</span><span class="sxs-lookup"><span data-stu-id="0d191-111">BAM definitions</span></span>  
  
-   <span data-ttu-id="0d191-112">Fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="0d191-112">Binding files</span></span>  
  
-   <span data-ttu-id="0d191-113">Répertoires virtuels</span><span class="sxs-lookup"><span data-stu-id="0d191-113">Virtual directories</span></span>  
  
 <span data-ttu-id="0d191-114">Si un répertoire virtuel est ajouté de manière explicite à une application, en étant importé ou ajouté, vous pouvez le supprimer à l'aide des procédures de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0d191-114">If a virtual directory is explicitly added to an application, either by being imported from or added, it can be removed by using the procedures in this topic.</span></span> <span data-ttu-id="0d191-115">S'il n'a pas été ajouté de manière explicite, mais par référence lors de la configuration d'un emplacement de réception, vous ne pouvez pas le supprimer à l'aide de ces procédures.</span><span class="sxs-lookup"><span data-stu-id="0d191-115">If it was not explicitly added, but rather was added by reference when a receive location was configured, you cannot remove it by using the procedures in this topic.</span></span> <span data-ttu-id="0d191-116">Cela est dû au fait qu'il n'est pas stocké dans la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0d191-116">This is because the virtual directory is not stored in the BizTalk Management database.</span></span> <span data-ttu-id="0d191-117">Si vous exportez le fichier .msi de l'application, le répertoire virtuel sera obtenu à partir de IIS et sera ajouté au fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="0d191-117">When you export the application .msi file the virtual directory will be obtained from IIS and added to the .msi file.</span></span> <span data-ttu-id="0d191-118">Si vous exportez le fichier .msi, le répertoire virtuel sera ajouté à la base de gestion BizTalk Management de ce groupe.</span><span class="sxs-lookup"><span data-stu-id="0d191-118">When you import the .msi file, the virtual directory will be added to the BizTalk Management database for that group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0d191-119">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="0d191-119">Prerequisites</span></span>  
 <span data-ttu-id="0d191-120">Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0d191-120">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="0d191-121">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="0d191-121">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-remove-a-resource-artifact-from-an-application"></a><span data-ttu-id="0d191-122">Pour supprimer un artefact de ressource d'une application</span><span class="sxs-lookup"><span data-stu-id="0d191-122">To remove a resource artifact from an application</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="0d191-123">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0d191-123">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="0d191-124">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="0d191-124">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0d191-125">Dans l’arborescence de la console, développez Administration de BizTalk Server, développez le groupe BizTalk contenant l’artefact de ressource à supprimer, puis développez l’application contenant l’artefact.</span><span class="sxs-lookup"><span data-stu-id="0d191-125">In the console tree, expand BizTalk Server Administration, expand the BizTalk group containing the resource artifact to remove, and then expand the application containing the artifact.</span></span>  
  
3.  <span data-ttu-id="0d191-126">Cliquez sur le **ressources** dossier, cliquez sur l’artefact, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="0d191-126">Click the **Resources** folder, right-click the artifact, and then click **Remove**.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="0d191-127">À l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="0d191-127">Using the command line</span></span>  
  
1.  <span data-ttu-id="0d191-128">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d191-128">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="0d191-129">Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="0d191-129">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="0d191-130">**BTSTask RemoveResource** [**« ApplicationName » :***valeur*] **ApplicationName :***valeur* [  **/Server :**  *valeur*] [**/Database :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="0d191-130">**BTSTask RemoveResource** [**/ApplicationName:***value*] **/Luid:***value* [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="0d191-131">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0d191-131">Example:</span></span>  
  
     <span data-ttu-id="0d191-132">**BTSTask RemoveResource /ApplicationName:MyApplication ApplicationName : « MyAssembly, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 0123456789ABCDEF »**</span><span class="sxs-lookup"><span data-stu-id="0d191-132">**BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**</span></span>  
  
    |<span data-ttu-id="0d191-133">Paramètre</span><span class="sxs-lookup"><span data-stu-id="0d191-133">Parameter</span></span>|<span data-ttu-id="0d191-134"> Description</span><span class="sxs-lookup"><span data-stu-id="0d191-134">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="0d191-135">**/ ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="0d191-135">**/ApplicationName**</span></span>|<span data-ttu-id="0d191-136">Nom de l'application BizTalk contenant l'artefact à supprimer.</span><span class="sxs-lookup"><span data-stu-id="0d191-136">Name of the BizTalk application containing the artifact to delete.</span></span> <span data-ttu-id="0d191-137">Si cette valeur n'est pas définie, l'application par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0d191-137">If not specified, the default application is used.</span></span> <span data-ttu-id="0d191-138">Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).</span><span class="sxs-lookup"><span data-stu-id="0d191-138">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="0d191-139">**/ Luid**</span><span class="sxs-lookup"><span data-stu-id="0d191-139">**/Luid**</span></span>|<span data-ttu-id="0d191-140">Identificateur unique local (LUID) de l'artefact.</span><span class="sxs-lookup"><span data-stu-id="0d191-140">Locally unique identifier (LUID) of the artifact.</span></span> <span data-ttu-id="0d191-141">Vous pouvez obtenir l’identificateur LUID à l’aide de la **ListApp** de commande, comme décrit dans [commande ListApp](../core/listapp-command.md).</span><span class="sxs-lookup"><span data-stu-id="0d191-141">You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).</span></span>|  
    |<span data-ttu-id="0d191-142">**/ Serveur**</span><span class="sxs-lookup"><span data-stu-id="0d191-142">**/Server**</span></span>|<span data-ttu-id="0d191-143">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.</span><span class="sxs-lookup"><span data-stu-id="0d191-143">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="0d191-144">Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="0d191-144">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="0d191-145">Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).</span><span class="sxs-lookup"><span data-stu-id="0d191-145">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="0d191-146">Exemples :</span><span class="sxs-lookup"><span data-stu-id="0d191-146">Examples:</span></span><br /><br /> <span data-ttu-id="0d191-147">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="0d191-147">Server=MyServer</span></span><br /><br /> <span data-ttu-id="0d191-148">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="0d191-148">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="0d191-149">Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0d191-149">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="0d191-150">**/ Base de données**</span><span class="sxs-lookup"><span data-stu-id="0d191-150">**/Database**</span></span>|<span data-ttu-id="0d191-151">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0d191-151">Name of the BizTalk Management database.</span></span> <span data-ttu-id="0d191-152">Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0d191-152">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d191-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d191-153">See Also</span></span>  
 <span data-ttu-id="0d191-154">[La gestion des assemblys .NET, certificats et autres ressources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span><span class="sxs-lookup"><span data-stu-id="0d191-154">[Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md) </span></span>  
 [<span data-ttu-id="0d191-155">Commande RemoveResource</span><span class="sxs-lookup"><span data-stu-id="0d191-155">RemoveResource Command</span></span>](../core/removeresource-command.md)