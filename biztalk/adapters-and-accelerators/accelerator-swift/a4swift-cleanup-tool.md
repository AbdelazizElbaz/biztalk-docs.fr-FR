---
title: Outil de nettoyage A4SWIFT | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- A4SWIFT Cleanup tool
ms.assetid: e694f824-6097-4d60-bc7b-b4f1a40acea0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b2d0e251bf5e8a4169ff0d86cc6635944ca12e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="a4swift-cleanup-tool"></a><span data-ttu-id="eb0eb-102">Outil de nettoyage A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="eb0eb-102">A4SWIFT Cleanup Tool</span></span>
<span data-ttu-id="eb0eb-103">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] outil de nettoyage vous permet de préparer un serveur qui a le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] installé dessus pour une nouvelle installation de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0eb-103">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] cleanup tool enables you to prepare a server that has the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] installed on it for a new installation of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="eb0eb-104">L’outil supprime les artefacts de A4SWIFT, tels que les contrats, les services et les stratégies du moteur de règles d’entreprise (BRE) et annule le déploiement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-104">The tool removes A4SWIFT artifacts such as agreements, departments, and Business Rule Engine (BRE) policies, and undeploys assemblies.</span></span> <span data-ttu-id="eb0eb-105">Exécution de l’outil vous permet d’éviter la suppression manuelle de nombreux artefacts A4SWIFT et résout les problèmes d’annulation du déploiement des assemblys qui peuvent être référencées à partir d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-105">Running the tool enables you to avoid manually removing many A4SWIFT artifacts, and resolves problems with undeploying assemblies that might be referenced from other assemblies.</span></span>  
  
 <span data-ttu-id="eb0eb-106">Lorsque vous exécutez l’outil de nettoyage, vous avez le choix de laisser A4SWIFT installé sur l’ordinateur (par défaut), ou A4SWIFT désinstallation après avoir supprimé les artefacts.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-106">When you run the cleanup tool, you have the choice of leaving A4SWIFT installed on the computer (the default), or uninstalling A4SWIFT after removing the artifacts.</span></span> <span data-ttu-id="eb0eb-107">Vous devez exécuter l’outil avant de désinstaller A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-107">You should run the tool before uninstalling A4SWIFT.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="eb0eb-108">N’utilisez pas l’outil de nettoyage A4SWIFT dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-108">Do not use the A4SWIFT cleanup tool in a production environment.</span></span> <span data-ttu-id="eb0eb-109">L’outil est destiné à être utilisée dans un environnement de développement de serveur unique, pas dans un déploiement multiserveur.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-109">The tool is intended to be used in a single-server development environment, not in a multiserver deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb0eb-110">Par défaut, l’outil de nettoyage ne fonctionne pas pour une autre langue que l’anglais.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-110">By default, the cleanup tool does not work for any other language than English.</span></span> <span data-ttu-id="eb0eb-111">Toutefois, vous pouvez modifier l’environnement afin que l’outil de nettoyage fonctionne sur un ordinateur localisé.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-111">You can, however, modify the environment so that the cleanup tool works on a localized computer.</span></span> <span data-ttu-id="eb0eb-112">Exécutez l’outil de FormPublish avec le paramètre t et la chaîne localisée pour la bibliothèque de documents modèles, par exemple, **t:VorLagen** dans un environnement en allemand.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-112">Run the FormPublish tool with the t parameter and the localized string for the Templates document library, for example, **t:VorLagen** in a German environment.</span></span> <span data-ttu-id="eb0eb-113">Vous pouvez ensuite exécuter l’outil de nettoyage dans un environnement localisé.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-113">You can then run the cleanup tool in a localized environment.</span></span>  
  
 <span data-ttu-id="eb0eb-114">Les éléments suivants doivent être remplis pour l’outil de nettoyage à exécuter :</span><span class="sxs-lookup"><span data-stu-id="eb0eb-114">The following must be true for the cleanup tool to run:</span></span>  
  
-   <span data-ttu-id="eb0eb-115">Vous devez être membre du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupes d’administrateurs.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-115">You must be a member the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators groups.</span></span>  
  
-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]<span data-ttu-id="eb0eb-116">doit être installé sur le serveur sur lequel vous exécutez l’outil.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-116"> must be installed on the server on which you run the tool.</span></span>  
  
-   <span data-ttu-id="eb0eb-117">MrsrConfiguration.dll, Shared.dll et RuleEngineExtension.dll doivent être déployés sur le serveur sur lequel vous exécutez l’outil.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-117">MrsrConfiguration.dll, Shared.dll, and RuleEngineExtension.dll must be deployed on the server on which you run the tool.</span></span>  
  
## <a name="what-the-cleanup-tool-does"></a><span data-ttu-id="eb0eb-118">Ce que fait l’outil de nettoyage</span><span class="sxs-lookup"><span data-stu-id="eb0eb-118">What the cleanup tool does</span></span>  
 <span data-ttu-id="eb0eb-119">L’outil de nettoyage A4SWIFT effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb0eb-119">The A4SWIFT cleanup tool performs the following operations:</span></span>  
  
-   <span data-ttu-id="eb0eb-120">S’exécute **annuler le déploiement de BM** contre ForActivities.xml et MRSRBAM.xml</span><span class="sxs-lookup"><span data-stu-id="eb0eb-120">Runs **BM Undeploy** against ForActivities.xml and MRSRBAM.xml</span></span>  
  
-   <span data-ttu-id="eb0eb-121">Supprime les fichiers FrrActivities_ConnectionStrings.xml et MRSRActivities_ConnectionStrings.xml, s’ils existent</span><span class="sxs-lookup"><span data-stu-id="eb0eb-121">Removes the FrrActivities_ConnectionStrings.xml and MRSRActivities_ConnectionStrings.xml files, if they exist</span></span>  
  
-   <span data-ttu-id="eb0eb-122">Supprime les 2.1 A4SWIFT s’il existe (si vous avez mis à niveau le serveur à [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], mais le programme d’installation n’a pas A4SWIFT 2.1 est installé) et supprime le dossier A4SWIFT 2.1</span><span class="sxs-lookup"><span data-stu-id="eb0eb-122">Removes A4SWIFT 2.1 if it exists (if you have upgraded the server to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], but Setup has left A4SWIFT 2.1 installed) and deletes the A4SWIFT 2.1 folder</span></span>  
  
-   <span data-ttu-id="eb0eb-123">Annule le déploiement de tous les assemblys A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="eb0eb-123">Undeploys all A4SWIFT assemblies</span></span>  
  
-   <span data-ttu-id="eb0eb-124">Supprime le groupe administrateur de A4SWIFT et le groupe utilisateurs d’A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="eb0eb-124">Deletes the A4SWIFT Administrator group and the A4SWIFT Users group</span></span>  
  
-   <span data-ttu-id="eb0eb-125">Supprime la base de données A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="eb0eb-125">Deletes the A4SWIFT database</span></span>  
  
-   <span data-ttu-id="eb0eb-126">Supprime le répertoire virtuel A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="eb0eb-126">Deletes the A4SWIFT virtual directory</span></span>  
  
-   <span data-ttu-id="eb0eb-127">Exécute une désinstallation sans assistance complète de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] et supprime la [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] dossier (si)</span><span class="sxs-lookup"><span data-stu-id="eb0eb-127">Runs a complete silent uninstall of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] and deletes the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] folder (if selected)</span></span>  
  
 <span data-ttu-id="eb0eb-128">Supprime les artefacts et annule le déploiement des assemblys, l’outil de nettoyage effectue également les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb0eb-128">As it removes artifacts and undeploys assemblies, the cleanup tool also does the following:</span></span>  
  
-   <span data-ttu-id="eb0eb-129">Démarre le Service d’administration Internet Information Services (IIS) pour pouvoir s’exécuter</span><span class="sxs-lookup"><span data-stu-id="eb0eb-129">Starts Internet Information Services (IIS) Admin Service in order to run</span></span>  
  
-   <span data-ttu-id="eb0eb-130">Arrête et redémarre les services MSSQLSERVER, SQLSERVERAGENT, BizTalk et Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="eb0eb-130">Stops and then restarts the MSSQLSERVER, SQLSERVERAGENT, BizTalk, and Enterprise Single Sign-On services</span></span>  
  
#### <a name="to-run-the-a4swift-cleanup-tool"></a><span data-ttu-id="eb0eb-131">Pour exécuter l’outil de nettoyage A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="eb0eb-131">To run the A4SWIFT cleanup tool</span></span>  
  
1.  <span data-ttu-id="eb0eb-132">Avant d’exécuter l’outil de nettoyage A4SWIFT, annuler le déploiement d’un projet qui fait référence à des assemblys par défaut A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-132">Prior to running the A4SWIFT cleanup tool, undeploy any project that refers to any of the A4SWIFT default assemblies.</span></span>  
  
2.  <span data-ttu-id="eb0eb-133">Ouvrez une invite de commandes et la déplacer vers \< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\SDK\Tools.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-133">Open a command prompt and move to \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools.</span></span>  
  
3.  <span data-ttu-id="eb0eb-134">Type **A4SWIFTCleanupTool.exe** , puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-134">Type **A4SWIFTCleanupTool.exe** and then press **ENTER**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb0eb-135">Lorsque vous exécutez initialement A4SWIFTCleanupTool.exe, l’outil affiche un écran d’aide et vous invite à entrer un paramètre.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-135">When you initially run A4SWIFTCleanupTool.exe, the tool displays a help screen, and prompts you to enter a parameter.</span></span> <span data-ttu-id="eb0eb-136">L’outil ne s’exécutera pas jusqu'à ce que vous entrez le paramètre.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-136">The tool will not run until you enter the parameter.</span></span>  
  
4.  <span data-ttu-id="eb0eb-137">Selon les actions que vous souhaitez que l’outil prenne, appuyez sur une des clés suivantes, puis appuyez sur **entrée**:</span><span class="sxs-lookup"><span data-stu-id="eb0eb-137">Depending upon the actions that you want the tool to take, press one of the following keys, and then press **ENTER**:</span></span>  
  
    -   <span data-ttu-id="eb0eb-138">**0** pour aucune action effectuée (par défaut)</span><span class="sxs-lookup"><span data-stu-id="eb0eb-138">**0** for no actions taken (the default)</span></span>  
  
    -   <span data-ttu-id="eb0eb-139">**1** pour supprimer toutes les ressources A4SWIFT locales sur l’ordinateur, y compris les paramètres de répertoire et Registre virtuels</span><span class="sxs-lookup"><span data-stu-id="eb0eb-139">**1** to remove all the local A4SWIFT resources on the computer, including the virtual directory and registry settings</span></span>  
  
    -   <span data-ttu-id="eb0eb-140">**2** pour supprimer toutes les ressources A4SWIFT partagées sur le groupe BizTalk Server, y compris les dossiers Sharepoint Web, les modèles de message FIN, les stratégies BRE vocabulaires, artefacts BizTalk et la base de données A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="eb0eb-140">**2** to remove all the shared A4SWIFT resources on the BizTalk Server group, including Sharepoint Web folders, FIN message templates, BRE policies and vocabularies, BizTalk artifacts, and the A4SWIFT database</span></span>  
  
    -   <span data-ttu-id="eb0eb-141">**3** pour supprimer toutes les ressources locales et partagées</span><span class="sxs-lookup"><span data-stu-id="eb0eb-141">**3** to remove all the local and shared resources</span></span>  
  
    -   <span data-ttu-id="eb0eb-142">**4** pour supprimer toutes les ressources locales et partagés et désinstaller le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] produit.</span><span class="sxs-lookup"><span data-stu-id="eb0eb-142">**4** to remove all the local and shared resources and uninstall the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] product.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb0eb-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb0eb-143">See Also</span></span>  
 [<span data-ttu-id="eb0eb-144">Outils</span><span class="sxs-lookup"><span data-stu-id="eb0eb-144">Tools</span></span>](../../adapters-and-accelerators/accelerator-swift/tools.md)