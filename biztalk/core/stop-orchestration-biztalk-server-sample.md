---
title: "Arrêter l’Orchestration (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- orchestrations, stopping
ms.assetid: 83be44e9-819d-4ac5-8b75-84c23e6b5ba2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0c88bdeb85b8ad493b85d2569061c35bd516e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="stop-orchestration-biztalk-server-sample"></a><span data-ttu-id="3d5fa-102">Arrêter l’Orchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="3d5fa-102">Stop Orchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="3d5fa-103">L'exemple d'arrêt d'une orchestration (Stop Orchestration) décrit l'arrêt d'une orchestration BizTalk Server et sa désinscription éventuelle.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-103">The Stop Orchestration sample demonstrates how to stop a BizTalk Server orchestration and, optionally, to unenlist it.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3d5fa-104">Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="3d5fa-105">Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="3d5fa-106">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="3d5fa-106">What This Sample Does</span></span>  
 <span data-ttu-id="3d5fa-107">Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="3d5fa-107">The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:</span></span>  
  
-   <span data-ttu-id="3d5fa-108">pour un nom d'orchestration et un nom d'assembly, création d'une requête pour une orchestration BizTalk Server déployée spécifique ;</span><span class="sxs-lookup"><span data-stu-id="3d5fa-108">Given an orchestration name and an assembly name, query for a specific deployed BizTalk Server orchestration.</span></span>  
  
-   <span data-ttu-id="3d5fa-109">arrêt de cette orchestration.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-109">Stop that orchestration.</span></span>  
  
-   <span data-ttu-id="3d5fa-110">désinscription de cette orchestration (facultatif).</span><span class="sxs-lookup"><span data-stu-id="3d5fa-110">Unenlist that orchestration (optionally).</span></span>  
  
-   <span data-ttu-id="3d5fa-111">gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-111">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="3d5fa-112">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="3d5fa-112">Where to Find This Sample</span></span>  
 <span data-ttu-id="3d5fa-113">Les fichiers de l'exemple se trouvent dans l'emplacement SDK suivant :</span><span class="sxs-lookup"><span data-stu-id="3d5fa-113">The sample files are located in the following SDK location:</span></span>  
  
 <span data-ttu-id="3d5fa-114">\<*Exemples de chemin d’accès*\>\Admin\WMI\Stop Orchestration\\</span><span class="sxs-lookup"><span data-stu-id="3d5fa-114">\<*Samples Path*\>\Admin\WMI\Stop Orchestration\\</span></span>  
  
 <span data-ttu-id="3d5fa-115">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-115">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="3d5fa-116">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="3d5fa-116">File(s)</span></span>|<span data-ttu-id="3d5fa-117"> Description</span><span class="sxs-lookup"><span data-stu-id="3d5fa-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d5fa-118">Dans le dossier \VBScript :</span><span class="sxs-lookup"><span data-stu-id="3d5fa-118">In the \VBScript folder:</span></span><br /><br /> <span data-ttu-id="3d5fa-119">StopOrch.vbs</span><span class="sxs-lookup"><span data-stu-id="3d5fa-119">StopOrch.vbs</span></span>|<span data-ttu-id="3d5fa-120">Fichier VBScript qui utilise des paramètres pour spécifier une orchestration à arrêter et, éventuellement, à désinscrire.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-120">VBScript file that takes parameters to specify an orchestration to be stopped and, optionally, unenlisted.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="3d5fa-121">Création et initialisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="3d5fa-121">Building and Initializing This Sample</span></span>  
 <span data-ttu-id="3d5fa-122">L'exemple Stop Orchestration est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-122">The Stop Orchestration sample consists of a single VBScript file that you do not need to build or initialize.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="3d5fa-123">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="3d5fa-123">Running This Sample</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="3d5fa-124">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3d5fa-124">To run this sample</span></span>  
  
1.  <span data-ttu-id="3d5fa-125">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="3d5fa-125">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="3d5fa-126">\<*Exemples de chemin d’accès*\>\Admin\WMI\Stop Orchestration\VBScript\\</span><span class="sxs-lookup"><span data-stu-id="3d5fa-126">\<*Samples Path*\>\Admin\WMI\Stop Orchestration\VBScript\\</span></span>  
  
2.  <span data-ttu-id="3d5fa-127">Exécutez le fichier StopOrch.vbs à l'aide du programme cscript en transmettant les arguments de ligne de commande suivants (le troisième argument est facultatif) :</span><span class="sxs-lookup"><span data-stu-id="3d5fa-127">Run the file StopOrch.vbs using the cscript program, passing the following command-line arguments, of which the third one is optional:</span></span>  
  
    -   <span data-ttu-id="3d5fa-128">**\<** ***OrchestrationName* \>.**</span><span class="sxs-lookup"><span data-stu-id="3d5fa-128">**\<** ***OrchestrationName* \>.**</span></span> <span data-ttu-id="3d5fa-129">Nom de l'orchestration BizTalk Server à arrêter et, éventuellement, à désinscrire.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-129">The name of the BizTalk Server orchestration to be stopped and, optionally, unenlisted.</span></span>  
  
    -   <span data-ttu-id="3d5fa-130">**\<** ***AssemblyName* \>.**</span><span class="sxs-lookup"><span data-stu-id="3d5fa-130">**\<** ***AssemblyName* \>.**</span></span> <span data-ttu-id="3d5fa-131">Nom de l'assembly BizTalk dans lequel l'orchestration spécifiée a été déployée.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-131">The name of the BizTalk assembly in which the specified orchestration was deployed.</span></span> <span data-ttu-id="3d5fa-132">Si le nom de l'assembly contient des espaces, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-132">If the assembly name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="3d5fa-133">**Annuler l’inscription.**</span><span class="sxs-lookup"><span data-stu-id="3d5fa-133">**Unenlist.**</span></span> <span data-ttu-id="3d5fa-134">Chaîne littérale facultative qui permet d'indiquer que l'orchestration spécifiée doit être arrêtée et désinscrite.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-134">An optional, literal string used to indicate that the specified orchestration should be unenlisted in addition to being stopped.</span></span>  
  
         <span data-ttu-id="3d5fa-135">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3d5fa-135">For example:</span></span>  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         <span data-ttu-id="3d5fa-136">-OU-</span><span class="sxs-lookup"><span data-stu-id="3d5fa-136">-OR-</span></span>  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration MyBusinessAssembly Unenlist  
        ```  
  
## <a name="comments"></a><span data-ttu-id="3d5fa-137">Commentaires</span><span class="sxs-lookup"><span data-stu-id="3d5fa-137">Comments</span></span>  
 <span data-ttu-id="3d5fa-138">Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide de scripts qui accèdent au modèle objet WMI de Windows.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-138">All tasks that you can perform in the BizTalk Server Administration console can also be performed by using scripts that access the Windows WMI object model.</span></span>  
  
 <span data-ttu-id="3d5fa-139">Le fichier de script StopOrch.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue.</span><span class="sxs-lookup"><span data-stu-id="3d5fa-139">The script file StopOrch.vbs contains detailed comments with further explanation about the operations that it performs.</span></span> <span data-ttu-id="3d5fa-140">Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span><span class="sxs-lookup"><span data-stu-id="3d5fa-140">For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d5fa-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d5fa-141">See Also</span></span>  
 [<span data-ttu-id="3d5fa-142">Admin-WMI (dossier d’exemples BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="3d5fa-142">Admin-WMI (BizTalk Server Samples Folder)</span></span>](../core/admin-wmi-biztalk-server-samples-folder.md)