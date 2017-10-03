---
title: "Comment exporter des liaisons d’un groupe BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- groups, bindings
- groups, exporting
ms.assetid: 51955266-f87f-41c9-992c-93036b40f663
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df08f99a9e37bf1a4d4a794c17d483fdc381f463
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bindings-for-a-biztalk-group"></a><span data-ttu-id="814df-102">Exportation des liaisons d'un groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="814df-102">How to Export Bindings for a BizTalk Group</span></span>
<span data-ttu-id="814df-103">Cette rubrique décrit comment exporter des liaisons pour un groupe BizTalk vers un fichier .xml à l'aide de la console Administration de BizTalk Server ou de l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="814df-103">This topic describes how to use the BizTalk Server Administration console or the command line to export the bindings for a BizTalk group to an .xml file.</span></span> <span data-ttu-id="814df-104">Vous pouvez ensuite importer ces liaisons dans un groupe BizTalk ou d’une application, comme décrit dans [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md) et [comment importer les liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="814df-104">You can then import these bindings into a BizTalk group or application, as described in [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md) and [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md).</span></span> <span data-ttu-id="814df-105">Pour plus d’informations sur l’utilisation de fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="814df-105">For more information about using binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="814df-106">L'exportation de liaisons pour un groupe entraîne toujours l'exportation des informations du tiers global, que cette option soit spécifiée ou non.</span><span class="sxs-lookup"><span data-stu-id="814df-106">Exporting bindings for a group always exports global party information, whether this option is specified or not.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="814df-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="814df-107">Prerequisites</span></span>  
 <span data-ttu-id="814df-108">Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server ou opérateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="814df-108">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="814df-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="814df-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-export-bindings-for-a-biztalk-group"></a><span data-ttu-id="814df-110">Exportation des liaisons pour un groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="814df-110">To export bindings for a BizTalk group</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="814df-111">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="814df-111">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="814df-112">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="814df-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="814df-113">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **Applications**, pointez sur **exporter**, puis cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="814df-113">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, right-click **Applications**, point to **Export**, and then click **Bindings**.</span></span>  
  
3.  <span data-ttu-id="814df-114">Dans la page Exporter les liaisons, dans **exportation vers le fichier**, tapez le chemin d’accès absolu du fichier .xml vers lequel exporter les liaisons.</span><span class="sxs-lookup"><span data-stu-id="814df-114">On the Export Bindings page, in **Export to file**, type the absolute path of the .xml file to which to export the bindings.</span></span>  
  
     <span data-ttu-id="814df-115">Exemple : C:\Bindings\Group1Bindings_Staging1.xml</span><span class="sxs-lookup"><span data-stu-id="814df-115">Example: C:\Bindings\Group1Bindings_Staging1.xml</span></span>  
  
4.  <span data-ttu-id="814df-116">Vérifiez que **exporter toutes les liaisons du groupe actif** est sélectionné, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="814df-116">Ensure that **Export all bindings from the current group** is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="814df-117">Les liaisons sont exportées vers un fichier .xml à l'emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="814df-117">The bindings are exported to an .xml file in the location that you specified.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="814df-118">À l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="814df-118">Using the command line</span></span>  
  
1.  <span data-ttu-id="814df-119">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="814df-119">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="814df-120">Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="814df-120">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="814df-121">**Facultatif /Destination de BTSTask ExportBindings :** *valeur* **paramètre « GroupLevel »** [**/GlobalParties**] [**/Server :**  *valeur*] [**/Database :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="814df-121">**BTSTask ExportBindings /Destination:** *value* **/GroupLevel** [**/GlobalParties**] [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="814df-122">Exemple :</span><span class="sxs-lookup"><span data-stu-id="814df-122">Example:</span></span>  
  
     <span data-ttu-id="814df-123">**Facultatif /Destination de BTSTask ExportBindings : « C:\Binding Files\MyBindings.xml » GroupLevel /Server:MyDatabaseServer Server**</span><span class="sxs-lookup"><span data-stu-id="814df-123">**BTSTask ExportBindings /Destination:"C:\Binding Files\MyBindings.xml" /GroupLevel /Server:MyDatabaseServer /Database:BizTalkMgmtDb**</span></span>  
  
    |<span data-ttu-id="814df-124">Paramètre</span><span class="sxs-lookup"><span data-stu-id="814df-124">Parameter</span></span>|<span data-ttu-id="814df-125">Valeur</span><span class="sxs-lookup"><span data-stu-id="814df-125">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="814df-126">**Et de destination**</span><span class="sxs-lookup"><span data-stu-id="814df-126">**/Destination**</span></span>|<span data-ttu-id="814df-127">Chemin d'accès complet du fichier de liaison à créer, nom du fichier inclus.</span><span class="sxs-lookup"><span data-stu-id="814df-127">Full path of the binding file to create, including the file name.</span></span> <span data-ttu-id="814df-128">Si un fichier de liaison doté du même chemin d'accès existe déjà, il est remplacé.</span><span class="sxs-lookup"><span data-stu-id="814df-128">If a binding file having the same path already exists, it is overwritten.</span></span> <span data-ttu-id="814df-129">Si le chemin d’accès contient des espaces, vous devez le placer entre guillemets doubles («).</span><span class="sxs-lookup"><span data-stu-id="814df-129">If there are spaces in the path, you must enclose it in double quotation marks (").</span></span>|  
    |<span data-ttu-id="814df-130">**/ GroupLevel**</span><span class="sxs-lookup"><span data-stu-id="814df-130">**/GroupLevel**</span></span>|<span data-ttu-id="814df-131">Lorsque ce paramètre est défini, toutes les liaisons du groupe BizTalk actif sont exportées.</span><span class="sxs-lookup"><span data-stu-id="814df-131">When specified, all bindings in the current BizTalk group are exported.</span></span>|  
    |<span data-ttu-id="814df-132">**/ GlobalParties**</span><span class="sxs-lookup"><span data-stu-id="814df-132">**/GlobalParties**</span></span>|<span data-ttu-id="814df-133">Si spécifié, exporte les informations du tiers global pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="814df-133">When specified, exports global party information for the group.</span></span>|  
    |<span data-ttu-id="814df-134">**/ Serveur**</span><span class="sxs-lookup"><span data-stu-id="814df-134">**/Server**</span></span>|<span data-ttu-id="814df-135">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.</span><span class="sxs-lookup"><span data-stu-id="814df-135">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="814df-136">Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="814df-136">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="814df-137">Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).</span><span class="sxs-lookup"><span data-stu-id="814df-137">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="814df-138">Exemples :</span><span class="sxs-lookup"><span data-stu-id="814df-138">Examples:</span></span><br /><br /> <span data-ttu-id="814df-139">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="814df-139">Server=MyServer</span></span><br /><br /> <span data-ttu-id="814df-140">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="814df-140">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="814df-141">Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="814df-141">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="814df-142">**/ Base de données**</span><span class="sxs-lookup"><span data-stu-id="814df-142">**/Database**</span></span>|<span data-ttu-id="814df-143">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="814df-143">Name of the BizTalk Management database.</span></span> <span data-ttu-id="814df-144">Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="814df-144">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="814df-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="814df-145">See Also</span></span>  
 <span data-ttu-id="814df-146">[L’exportation des liaisons](../core/exporting-bindings6.md) </span><span class="sxs-lookup"><span data-stu-id="814df-146">[Exporting Bindings](../core/exporting-bindings6.md) </span></span>  
 <span data-ttu-id="814df-147">[Commande ExportBindings](../core/exportbindings-command.md) </span><span class="sxs-lookup"><span data-stu-id="814df-147">[ExportBindings Command](../core/exportbindings-command.md) </span></span>  
 [<span data-ttu-id="814df-148">L’importation de stratégies, les liaisons et les Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="814df-148">Importing BizTalk Applications, Bindings, and Policies</span></span>](../core/importing-biztalk-applications-bindings-and-policies.md)