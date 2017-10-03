---
title: "Problèmes connus avec la mise à jour des Applications et artefacts | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ea03c-d453-40cc-8ddb-18a96f8ddfe5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a42fb3ca8381faedbd2283b9f4d297738bbb040d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-updating-applications-and-artifacts"></a><span data-ttu-id="fe5ea-102">Problèmes connus avec la mise à jour des Applications et des artefacts</span><span class="sxs-lookup"><span data-stu-id="fe5ea-102">Known Issues with Updating Applications and Artifacts</span></span>
## <a name="updating-an-application"></a><span data-ttu-id="fe5ea-103">Mise à jour d’une Application</span><span class="sxs-lookup"><span data-stu-id="fe5ea-103">Updating an Application</span></span>  
 <span data-ttu-id="fe5ea-104">**Suppression d’un artefact ne le supprime pas de tous les emplacements**</span><span class="sxs-lookup"><span data-stu-id="fe5ea-104">**Removing or deleting an artifact does not remove it from all locations**</span></span>  
  
 <span data-ttu-id="fe5ea-105">La suppression d'un artefact l'élimine des bases de données BizTalk Server de sorte qu'il n'apparaît plus ni dans la console d'administration, ni dans la liste des artefacts d'une application générée par la commande BTSTask ListApp.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-105">Removing or deleting an artifact deletes it from the BizTalk Server databases, so that it no longer appears in the administration console or in the list of artifacts for an application generated by the BTSTask ListApp command.</span></span> <span data-ttu-id="fe5ea-106">Elle ne supprime pas l’artefact à partir du Registre Windows, le global assembly cache (GAC), un répertoire virtuel ou le système de fichiers, s’il existe dans ces emplacements.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-106">It does not remove the artifact from the Windows registry, the global assembly cache (GAC), a virtual directory, or the file system, if it exists in any of these locations.</span></span> <span data-ttu-id="fe5ea-107">Dans le cas des ports d'envoi, des groupes de ports d'envoi, des ports de réception et des emplacements de réception, qui n'existent que dans la base de données de gestion BizTalk, cette opération efface entièrement l'artefact.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-107">In the case of send ports, send port groups, receive ports, and receive locations, which exist only in the BizTalk Management database, this operation deletes the artifact entirely.</span></span>  
  
## <a name="updating-an-artifact"></a><span data-ttu-id="fe5ea-108">Mise à jour d’un artefact</span><span class="sxs-lookup"><span data-stu-id="fe5ea-108">Updating an Artifact</span></span>  
 <span data-ttu-id="fe5ea-109">**Suppression ou modification de l’état d’un artefact peut entraîner une application de fonctionner**</span><span class="sxs-lookup"><span data-stu-id="fe5ea-109">**Removing or changing the state of an artifact can cause an application not to work**</span></span>  
  
 <span data-ttu-id="fe5ea-110">Lorsque vous ajoutez une référence à partir d’une application à l’autre et apportez des modifications à l’état d’un artefact sur lesquels dépend d’une autre application ou supprimer de l’artefact, l’application qui possède la dépendance ne fonctionnera pas correctement.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-110">When you add a reference from one application to another and make any changes to the state of an artifact on which another application depends, or you remove the artifact, the application that has the dependency will not function correctly.</span></span> <span data-ttu-id="fe5ea-111">Pour plus d’informations sur la modification de l’état d’un artefact, consultez la section sur l’artefact approprié dans [la gestion des artefacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725).</span><span class="sxs-lookup"><span data-stu-id="fe5ea-111">For more information about changing the state of an artifact, see the section on the appropriate artifact in [Managing Artifacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725).</span></span>  
  
 <span data-ttu-id="fe5ea-112">**Fichiers de stratégie .NET ne sont pas pris en charge.**</span><span class="sxs-lookup"><span data-stu-id="fe5ea-112">**.NET policy files are not supported**</span></span>  
  
 <span data-ttu-id="fe5ea-113">L'utilisation des fichiers de stratégie .NET n'est pas prise en charge dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe5ea-113">The use of .NET policy files is not supported in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="fe5ea-114">En effet, il arrive que les fichiers de stratégie ne fonctionnent pas comme prévu.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-114">This is because a policy file may not work as expected.</span></span> <span data-ttu-id="fe5ea-115">Ils redirigent .NET vers une version de l’assembly spécifié dans le GAC, mais [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accède souvent aux assemblys et les données des artefacts à partir d’un cache ou la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-115">Policy files redirect .NET to a specified assembly version in the GAC, but [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] often accesses assemblies and artifact data from a cache or the BizTalk Management database.</span></span> <span data-ttu-id="fe5ea-116">En fonction du type d'artefact, de la mise en cache et du redémarrage ou non des instances d'hôte, les fichiers de stratégie peuvent ne pas répondre correctement.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-116">Depending on the artifact type, caching situation, and whether host instances are restarted, the policy file may not do what is desired.</span></span>  
  
## <a name="updating-an-assembly"></a><span data-ttu-id="fe5ea-117">Mise à jour d’un Assembly</span><span class="sxs-lookup"><span data-stu-id="fe5ea-117">Updating an Assembly</span></span>  
 <span data-ttu-id="fe5ea-118">**Modifications apportées à un assembly ne prendront effet si l’hôte n’est pas arrêté.**</span><span class="sxs-lookup"><span data-stu-id="fe5ea-118">**Changes to an assembly may not take effect if the host is not stopped**</span></span>  
  
 <span data-ttu-id="fe5ea-119">Assemblys BizTalk doivent respecter les règles de contrôle de version de .NET.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-119">BizTalk assemblies must follow .NET versioning rules.</span></span> <span data-ttu-id="fe5ea-120">La principale implication de tout ceci est qu'un projet BizTalk, une fois élaboré à partir d'une version donnée d'un autre projet .NET ou assembly (incluant des projets BizTalk), continue à utiliser cette version jusqu'à ce qu'il soit reconstruit à partir d'une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-120">The main implication of this is that a BizTalk project, once built against a particular version of another .NET project or assembly (including BizTalk projects), continues to use that version until it has been rebuilt against a newer version.</span></span>  
  
 <span data-ttu-id="fe5ea-121">Un problème d'établissement de versions .NET se produit fréquemment pendant le développement lorsque les numéros de version d'un projet BizTalk ne sont pas modifiés et que l'assembly est redéployé sans arrêter et démarrer l'instance de l'hôte BizTalk dans laquelle les types sont chargés.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-121">A common problem occurs during development related to .NET versioning when the version numbers on a BizTalk project are not changed and the assembly is redeployed without stopping and starting the BizTalk host instance that the types are loaded into.</span></span>  
  
 <span data-ttu-id="fe5ea-122">Quand le processus est exécuté à nouveau, les modifications ne prennent pas effet.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-122">When the process is run again, the changes do not take effect.</span></span> <span data-ttu-id="fe5ea-123">Ceci est dû au mode de chargement en mémoire des assemblys .NET.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-123">This is due to the way in which .NET assemblies are loaded into memory.</span></span> <span data-ttu-id="fe5ea-124">Étant donné que l’ordinateur hôte dispose déjà d’une copie en mémoire de l’assembly, il ne recharge pas l’assembly lorsqu’une nouvelle copie est placée dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="fe5ea-124">Because the host already has an in-memory copy of the assembly, it does not reload the assembly when a new copy is put into the global assembly cache (GAC).</span></span> <span data-ttu-id="fe5ea-125">Par exemple, si la version 1.0.0.0 d'un assembly avec orchestration est déployée et exécutée, et que des modifications sont apportées à l'orchestration mais que le numéro de version n'est pas modifié, les modifications ne prennent pas effet.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-125">For example, if version 1.0.0.0 of an assembly with an orchestration is deployed and running, and changes are made to the orchestration but the version number is not changed, then the changes do not take effect.</span></span> <span data-ttu-id="fe5ea-126">Une fois l'instance de l'hôte arrêtée, la copie en mémoire de l'assembly est publiée. Ensuite, lorsque l'instance de l'hôte redémarre, elle recharge la copie nouvelle de l'assembly et reçoit les modifications.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-126">After the host instance is stopped, the in-memory copy of the assembly is released and when the host instance starts again it reloads the new copy of the assembly and gets the changes.</span></span> <span data-ttu-id="fe5ea-127">Si une nouvelle version a été déployée, par exemple la version 2.0.0.0 et il a été chargé, puis la modification entrera en vigueur.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-127">If a new version was deployed, for example version 2.0.0.0, and it was loaded, then the changes would take effect.</span></span>  
  
 <span data-ttu-id="fe5ea-128">**Modification de la version de l’assembly peut rompre la relation entre un assembly et les éléments qui y font référence à la version**</span><span class="sxs-lookup"><span data-stu-id="fe5ea-128">**Changing the assembly version may break the relationship between an assembly and items that reference it by version**</span></span>  
  
 <span data-ttu-id="fe5ea-129">Dans le développement de .NET Framework, il est courant de mettre à jour le numéro de version d’assembly pour le numéro de build en cours lorsqu’une génération se produit.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-129">In .NET Framework development it is typical to update the assembly version number to the current build number when a build takes place.</span></span> <span data-ttu-id="fe5ea-130">Cependant, lors du développement d'une solution BizTalk, le changement du numéro de version de l'assembly peut entraîner une rupture de la relation entre l'assembly et les éléments dépendants qui font référence au fichier DLL en utilisant le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-130">However, when developing a BizTalk solution, changing the assembly version number can break the relationship between an assembly and the dependent items that reference the DLL by its assembly version number.</span></span> <span data-ttu-id="fe5ea-131">Le tableau suivant répertorie les éléments qui font référence à un assembly BizTalk Server à l’aide de son numéro de version et l’effet de la modification d’un numéro de version d’assembly.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-131">The following table lists items that refer to a BizTalk Server assembly by using its version number and the effect of changing an assembly version number.</span></span>  
  
|<span data-ttu-id="fe5ea-132">Entité</span><span class="sxs-lookup"><span data-stu-id="fe5ea-132">Entity</span></span>|<span data-ttu-id="fe5ea-133">Implications du changement dans le numéro de version de l'assembly</span><span class="sxs-lookup"><span data-stu-id="fe5ea-133">Effect of changing assembly version number</span></span>|  
|------------|------------------------------------------------|  
|<span data-ttu-id="fe5ea-134">Fichiers de liaison</span><span class="sxs-lookup"><span data-stu-id="fe5ea-134">Binding files</span></span>|<span data-ttu-id="fe5ea-135">Le changement du numéro de version de l'assembly entraîne l'échec de tous les fichiers de liaison qui font référence à cet assembly.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-135">Changing the assembly version number causes any existing binding files that reference the assembly to fail.</span></span> <span data-ttu-id="fe5ea-136">Cela est dû au fait que le fichier de liaison fait référence à l'assembly au moyen d'attributs qui comprennent le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-136">This is because the binding file references the assembly by attributes including its version number.</span></span><br /><br /> <span data-ttu-id="fe5ea-137">Vous pouvez mettre à jour les informations de version dans le fichier de liaison à l'aide du Bloc-notes ou d'un autre éditeur.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-137">You can update the version information in the binding file by using Notepad or another editor.</span></span> <span data-ttu-id="fe5ea-138">Vous pouvez également redéployez la solution et puis régénérer le fichier de liaison à l’aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-138">You can also redeploy the solution and then regenerate the binding file by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="fe5ea-139">Enfin, vous avez la possibilité d'utiliser des scripts pour automatiser le déploiement et la gestion des versions.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-139">Finally, you can use scripts to automate deployment and versioning.</span></span> <span data-ttu-id="fe5ea-140">Pour plus d’informations sur le déploiement, consultez [déploiement et la gestion des Applications BizTalk](http://go.microsoft.com/fwlink/?LinkID=154210) (http://go.microsoft.com/fwlink/?LinkID=154210).</span><span class="sxs-lookup"><span data-stu-id="fe5ea-140">For more information about deployment, see [Deploying and Managing BizTalk Applications](http://go.microsoft.com/fwlink/?LinkID=154210) (http://go.microsoft.com/fwlink/?LinkID=154210).</span></span>|  
|<span data-ttu-id="fe5ea-141">Fichiers de définition du modèle de suivi BAM (.btt)</span><span class="sxs-lookup"><span data-stu-id="fe5ea-141">BAM tracking profile definition (.btt) files</span></span>|<span data-ttu-id="fe5ea-142">Le changement du numéro de version de l'assembly entraîne l'échec de tous les fichiers de définition du modèle de suivi BAM.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-142">Changing the assembly version number causes any existing BAM tracking profile definition files to fail.</span></span> <span data-ttu-id="fe5ea-143">Étant donné que les fichiers de suivi BAM sont dans un format binaire, ils ne peuvent pas être modifiés et doivent donc être régénérés.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-143">The BAM tracking files are in a binary file format so they cannot be edited and instead must be regenerated.</span></span> <span data-ttu-id="fe5ea-144">Si les modèles de suivi BAM sont nécessaires, il vous faut respecter l'une ou l'autre de ces instructions :</span><span class="sxs-lookup"><span data-stu-id="fe5ea-144">If BAM tracking profiles are required it may be necessary to do either of the following:</span></span><br /><br /> <span data-ttu-id="fe5ea-145">-Éviter la mise à jour fréquemment des numéros de version pendant le processus de génération</span><span class="sxs-lookup"><span data-stu-id="fe5ea-145">-   Avoid frequently updating version numbers during the build process</span></span><br /><span data-ttu-id="fe5ea-146">-Retarder la création de profils de suivi jusqu'à ce que les numéros de version sont stables BAM</span><span class="sxs-lookup"><span data-stu-id="fe5ea-146">-   Delay building BAM tracking profiles until version numbers are stable</span></span>|  
|<span data-ttu-id="fe5ea-147">Services Web publiés à l'aide de l'Assistant Publication de services Web</span><span class="sxs-lookup"><span data-stu-id="fe5ea-147">Web services published by using the Web Services Publishing Wizard</span></span>|<span data-ttu-id="fe5ea-148">Lorsque l’Assistant Publication de Services Web est utilisé pour produire une interface Web ASP.NET, la version d’assembly de l’assembly BizTalk Server est incluse dans le code source ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-148">When the Web Services Publishing Wizard is used to produce an ASP.NET Web interface, the assembly version of the BizTalk Server assembly is included in the ASP.NET source code.</span></span> <span data-ttu-id="fe5ea-149">Le numéro de version d’assembly est utilisé lors de l’exécution par l’interface ASP.NET dans le cadre de la propriété bodyTypeAssemblyQualifiedName de l’opération de service Web.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-149">The assembly version number is used at runtime by the ASP.NET interface as part of the bodyTypeAssemblyQualifiedName property of the Web service operation.</span></span> <span data-ttu-id="fe5ea-150">Si le numéro de version de l’assembly BizTalk Server change sans mettre à jour la propriété bodyTypeAssemblyQualifiedName, les opérations de service Web suivantes seront rejetées par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-150">If the version number of the BizTalk Server assembly changes without updating the bodyTypeAssemblyQualifiedName property, then subsequent Web service operations will be rejected by BizTalk Server.</span></span><br /><br /> <span data-ttu-id="fe5ea-151">Lorsque l'emplacement de réception utilise le pipeline XmlDefaultPipeline, l'abonnement se réfère au type de document.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-151">If the receive location uses the XmlDefaultPipeline, the subscription relies on the document type.</span></span> <span data-ttu-id="fe5ea-152">Ce dernier se sert des informations d'assembly incorporées et il échoue si l'assembly n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-152">It uses the embedded assembly information and will fail if the assembly does not exist.</span></span> <span data-ttu-id="fe5ea-153">Si le pipeline utilisé est PassThruPipeline (pipeline par défaut lorsqu'un port est exposé et que l'Assistant crée de lui-même l'emplacement de réception), l'abonnement ignore ces informations d'assembly incorporées.</span><span class="sxs-lookup"><span data-stu-id="fe5ea-153">If you use the PassThruPipeline (which is the default if you expose a port and let the wizard create the receive location), the subscription ignores this embedded assembly information.</span></span>|