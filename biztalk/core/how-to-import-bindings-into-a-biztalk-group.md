---
title: Comment importer des liaisons dans un groupe BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- groups, importing
- importing, bindings
- groups, bindings
- bindings, groups
ms.assetid: 38da14fb-3522-4274-a633-2ff24e4bd574
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cfc20fea950c737d59e6b325744a02ee67bb63f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-bindings-into-a-biztalk-group"></a><span data-ttu-id="b22c6-102">Importation des liaisons dans un groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="b22c6-102">How to Import Bindings into a BizTalk Group</span></span>
<span data-ttu-id="b22c6-103">Cette rubrique décrit comment importer des liaisons dans un groupe BizTalk à partir d'un fichier .xml à l'aide de la console Administration de BizTalk Server ou de l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b22c6-103">This topic describes how to use the BizTalk Server Administration console or the command line to import bindings into a BizTalk group from an .xml file.</span></span> <span data-ttu-id="b22c6-104">Pour obtenir des instructions sur l’exportation des liaisons dans un fichier .xml que vous pouvez importer à partir d’un groupe BizTalk, consultez [comment exporter les liaisons pour un groupe BizTalk](../core/how-to-export-bindings-for-a-biztalk-group.md).</span><span class="sxs-lookup"><span data-stu-id="b22c6-104">For instructions on exporting the bindings from a BizTalk group into an .xml file that you can import, see [How to Export Bindings for a BizTalk Group](../core/how-to-export-bindings-for-a-biztalk-group.md).</span></span>  
  
 <span data-ttu-id="b22c6-105">Vous pouvez également importer des liaisons dans une application BizTalk, comme décrit dans [comment importer les liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="b22c6-105">You can also import bindings into a BizTalk application, as described in [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b22c6-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b22c6-106">Prerequisites</span></span>  
 <span data-ttu-id="b22c6-107">Pour effectuer les procédures décrites dans cette rubrique, vous devez être connecté avec un compte qui est membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b22c6-107">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="b22c6-108">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="b22c6-108">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
## <a name="to-import-bindings-into-a-biztalk-group"></a><span data-ttu-id="b22c6-109">Pour importer des liaisons dans un groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="b22c6-109">To import bindings into a BizTalk group</span></span>  
  
#### <a name="using-the-biztalk-server-administration-console"></a><span data-ttu-id="b22c6-110">Utilisation de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b22c6-110">Using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="b22c6-111">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="b22c6-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="b22c6-112">Dans l’arborescence de la console, développez **Administration de BizTalk Server**, le groupe BizTalk, puis cliquez sur **Applications**.</span><span class="sxs-lookup"><span data-stu-id="b22c6-112">In the console tree, expand  **BizTalk Server Administration**, expand the BizTalk group, and then right-click **Applications**.</span></span>  
  
3.  <span data-ttu-id="b22c6-113">Pointez sur **importation**, puis cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="b22c6-113">Point to **Import**, and then click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="b22c6-114">Cliquez sur le fichier de liaison et cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="b22c6-114">Click the binding file and click **Open**.</span></span>  
  
     <span data-ttu-id="b22c6-115">Les artefacts du fichier de liaison sont écrits dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="b22c6-115">The artifacts in the binding file are written to the group.</span></span> <span data-ttu-id="b22c6-116">Elles s’affichent dans les dossiers appropriés de le \<tous les artefacts > nœud.</span><span class="sxs-lookup"><span data-stu-id="b22c6-116">They display in appropriate folders of the \<All Artifacts> node.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="b22c6-117">À l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="b22c6-117">Using the command line</span></span>  
  
1.  <span data-ttu-id="b22c6-118">Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b22c6-118">Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b22c6-119">Tapez la commande suivante en utilisant les valeurs appropriées, comme décrit dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="b22c6-119">Type the following command, substituting the appropriate values, as described in the following table:</span></span>  
  
     <span data-ttu-id="b22c6-120">**BTSTask ImportBindings /Source :** *valeur* **paramètre « GroupLevel »** [**/Server :***valeur*] [**/ Base de données :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="b22c6-120">**BTSTask ImportBindings /Source:** *value* **/GroupLevel** [**/Server:***value*] [**/Database:***value*]</span></span>  
  
     <span data-ttu-id="b22c6-121">La commande suivante permet d'importer des liaisons dans le groupe défini dans la base de données de gestion BizTalk qui s'exécute sur une instance de SQL Server appelée MyServer.</span><span class="sxs-lookup"><span data-stu-id="b22c6-121">For example, the following command imports bindings into the group defined in the BizTalk Management database running on a SQL Server instance named MyServer.</span></span>  
  
     <span data-ttu-id="b22c6-122">**BTSTask ImportBindings GroupLevel /Server:MyServer Server /Source:C:\Bindings\Binding1.xml**</span><span class="sxs-lookup"><span data-stu-id="b22c6-122">**BTSTask ImportBindings /GroupLevel /Server:MyServer /Database:BiztalkMgmtDb /Source:C:\Bindings\Binding1.xml**</span></span>  
  
    |<span data-ttu-id="b22c6-123">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b22c6-123">Parameter</span></span>|<span data-ttu-id="b22c6-124">Valeur</span><span class="sxs-lookup"><span data-stu-id="b22c6-124">Value</span></span>|  
    |---------------|-----------|  
    |<span data-ttu-id="b22c6-125">**/ Source**</span><span class="sxs-lookup"><span data-stu-id="b22c6-125">**/Source**</span></span>|<span data-ttu-id="b22c6-126">Chemin d'accès complet du fichier de liaison à importer, nom du fichier inclus.</span><span class="sxs-lookup"><span data-stu-id="b22c6-126">Full path of the binding file to import, including the file name.</span></span> <span data-ttu-id="b22c6-127">Si le chemin d'accès comprend des espaces, vous devez le placer entre guillemets (").</span><span class="sxs-lookup"><span data-stu-id="b22c6-127">Paths that include spaces must be enclosed in quotation marks (").</span></span>|  
    |<span data-ttu-id="b22c6-128">**/ GroupLevel**</span><span class="sxs-lookup"><span data-stu-id="b22c6-128">**/GroupLevel**</span></span>|<span data-ttu-id="b22c6-129">Option permettant d'importer le fichier de liaison dans le groupe actuel.</span><span class="sxs-lookup"><span data-stu-id="b22c6-129">Option to import the binding file into the current group.</span></span>|  
    |<span data-ttu-id="b22c6-130">**/ Serveur**</span><span class="sxs-lookup"><span data-stu-id="b22c6-130">**/Server**</span></span>|<span data-ttu-id="b22c6-131">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.</span><span class="sxs-lookup"><span data-stu-id="b22c6-131">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="b22c6-132">Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="b22c6-132">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="b22c6-133">Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).</span><span class="sxs-lookup"><span data-stu-id="b22c6-133">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="b22c6-134">Exemples :</span><span class="sxs-lookup"><span data-stu-id="b22c6-134">Examples:</span></span><br /><br /> <span data-ttu-id="b22c6-135">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="b22c6-135">Server=MyServer</span></span><br /><br /> <span data-ttu-id="b22c6-136">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="b22c6-136">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="b22c6-137">Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b22c6-137">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
    |<span data-ttu-id="b22c6-138">**/ Base de données**</span><span class="sxs-lookup"><span data-stu-id="b22c6-138">**/Database**</span></span>|<span data-ttu-id="b22c6-139">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="b22c6-139">Name of the BizTalk Management database.</span></span> <span data-ttu-id="b22c6-140">Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b22c6-140">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b22c6-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b22c6-141">See Also</span></span>  
 <span data-ttu-id="b22c6-142">[L’importation de stratégies, les liaisons et les Applications BizTalk](../core/importing-biztalk-applications-bindings-and-policies.md) </span><span class="sxs-lookup"><span data-stu-id="b22c6-142">[Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md) </span></span>  
 [<span data-ttu-id="b22c6-143">Commande ImportBindings</span><span class="sxs-lookup"><span data-stu-id="b22c6-143">ImportBindings Command</span></span>](../core/importbindings-command.md)