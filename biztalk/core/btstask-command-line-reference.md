---
title: "Référence de ligne de commande BTSTask | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c350695-13e9-441a-9f1e-03cdc3e41328
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c2de1e2e616b57d0cc8eda0cb9de9eae5c72d26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btstask-command-line-reference"></a><span data-ttu-id="33bb0-102">Informations techniques sur l'outil de ligne de commande BTSTask</span><span class="sxs-lookup"><span data-stu-id="33bb0-102">BTSTask Command-Line Reference</span></span>
<span data-ttu-id="33bb0-103">Les rubriques de cette section contiennent des informations d'ordre technique relatives à l'outil de ligne de commande BTSTask inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33bb0-103">The topics in this section provide reference information for the BTSTask command-line tool included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="33bb0-104">Vous pouvez utiliser l'outil BTSTask pour effectuer de nombreuses tâches de déploiement des applications à partir d'une ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="33bb0-104">You can use BTSTask to perform many application deployment tasks from the command line, as follows:</span></span>  
  
-   <span data-ttu-id="33bb0-105">Utilisez la commande AddApp pour ajouter une application BizTalk à la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="33bb0-105">Add a BizTalk application to the BizTalk Management database by using the AddApp command.</span></span>  
  
-   <span data-ttu-id="33bb0-106">Utilisez la commande AddResource pour ajouter un artefact à une application.</span><span class="sxs-lookup"><span data-stu-id="33bb0-106">Add an artifact to an application by using the AddResource command.</span></span>  
  
-   <span data-ttu-id="33bb0-107">Servez-vous de la commande ExportApp pour exporter une application et ses artefacts vers un fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="33bb0-107">Export an application and its artifacts to an .msi file by using the ExportApp command.</span></span>  
  
-   <span data-ttu-id="33bb0-108">Exportez les informations de liaison vers un fichier .xml à l'aide de la commande ExportBindings.</span><span class="sxs-lookup"><span data-stu-id="33bb0-108">Export binding information to an .xml file by using the ExportBindings command.</span></span>  
  
-   <span data-ttu-id="33bb0-109">Importez une application d'un fichier .msi en utilisant la commande ImportApp.</span><span class="sxs-lookup"><span data-stu-id="33bb0-109">Import an application from an .msi file by using the ImportApp command.</span></span>  
  
-   <span data-ttu-id="33bb0-110">Utilisez la commande ImportBindings pour importer les informations de liaison dans un fichier .xml.</span><span class="sxs-lookup"><span data-stu-id="33bb0-110">Import binding information from an .xml file by using the ImportBindings command.</span></span>  
  
-   <span data-ttu-id="33bb0-111">Répertoriez les artefacts inclus dans une application ainsi que leurs identificateurs uniques locaux (LUID) en utilisant la commande ListApp.</span><span class="sxs-lookup"><span data-stu-id="33bb0-111">List the artifacts included in an application along with their locally unique identifiers (LUIDs) by using the ListApp command.</span></span>  
  
-   <span data-ttu-id="33bb0-112">Dressez la liste de toutes les applications dans la base de données de gestion BizTalk pour le groupe BizTalk à l'aide de la commande ListApps.</span><span class="sxs-lookup"><span data-stu-id="33bb0-112">List all applications in the BizTalk Management database for the BizTalk group by using the ListApps command.</span></span>  
  
-   <span data-ttu-id="33bb0-113">Servez-vous de la commande ListPackage pour répertorier les ressources dans un fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="33bb0-113">List the resources in an .msi file by using the ListPackage command.</span></span>  
  
-   <span data-ttu-id="33bb0-114">Dressez la liste de tous les types d'artefacts pris en charge par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de la commande ListTypes.</span><span class="sxs-lookup"><span data-stu-id="33bb0-114">List all of the artifact types supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the ListTypes command.</span></span>  
  
-   <span data-ttu-id="33bb0-115">Utilisez la commande RemoveApp pour supprimer une application de la base de données de gestion BizTalk et de la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="33bb0-115">Remove an application from the BizTalk Management database and the BizTalk Administration console by using the RemoveApp command.</span></span>  
  
-   <span data-ttu-id="33bb0-116">Utilisez la commande RemoveResource pour supprimer un artefact d'une application.</span><span class="sxs-lookup"><span data-stu-id="33bb0-116">Remove an artifact from an application by using the RemoveResource command.</span></span>  
  
-   <span data-ttu-id="33bb0-117">Désinstallez une application de l'ordinateur local à l'aide de la commande UninstallApp.</span><span class="sxs-lookup"><span data-stu-id="33bb0-117">Uninstall an application from the local computer by using the UninstallApp command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33bb0-118">Vous ne pouvez pas utiliser les commandes BTSTask dans un script de pré-traitement ou de post-traitement qui s'exécute pendant l'importation d'une application.</span><span class="sxs-lookup"><span data-stu-id="33bb0-118">You cannot use BTSTask commands in a preprocessing or postprocessing script that will run during application import.</span></span> <span data-ttu-id="33bb0-119">L'utilisation d'une telle commande peut entraîner l'échec de l'importation.</span><span class="sxs-lookup"><span data-stu-id="33bb0-119">If you do, the import may fail.</span></span> <span data-ttu-id="33bb0-120">En effet, les modifications apportées lors d'une importation ne sont pas visibles pour les scripts.</span><span class="sxs-lookup"><span data-stu-id="33bb0-120">This is because changes being made during import are not visible to scripts.</span></span>  
  
 <span data-ttu-id="33bb0-121">En outre, vous pouvez obtenir des informations sur la façon dont les couleurs de premier plan de la console peuvent être modifiées pour BTSTask.</span><span class="sxs-lookup"><span data-stu-id="33bb0-121">In addition, you can learn how to edit the console foreground colors for BTSTask.</span></span> <span data-ttu-id="33bb0-122">Si l'arrière-plan de votre console est blanc, vous aurez des difficultés à lire les données de sortie BTSTask de la console. Il se peut donc que vous deviez modifier les couleurs de premier plan de la console.</span><span class="sxs-lookup"><span data-stu-id="33bb0-122">If your console background color is white, you will have difficulty reading the BTSTask console output and will need to modify the console foreground colors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33bb0-123">Lorsqu'un script est terminé, il renvoie zéro (0) pour indiquer qu'il s'est terminé correctement ou un nombre différent de zéro en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="33bb0-123">When a script completes, it returns a zero (0) to indicate successful completion or a non-zero number to indicate failure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33bb0-124">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="33bb0-124">In This Section</span></span>  
  
-   [<span data-ttu-id="33bb0-125">Commande AddApp</span><span class="sxs-lookup"><span data-stu-id="33bb0-125">AddApp Command</span></span>](../core/addapp-command.md)  
  
-   [<span data-ttu-id="33bb0-126">Commande AddResource</span><span class="sxs-lookup"><span data-stu-id="33bb0-126">AddResource Command</span></span>](../core/addresource-command.md)  
  
-   [<span data-ttu-id="33bb0-127">Commande ExportApp</span><span class="sxs-lookup"><span data-stu-id="33bb0-127">ExportApp Command</span></span>](../core/exportapp-command.md)  
  
-   [<span data-ttu-id="33bb0-128">Commande ExportBindings</span><span class="sxs-lookup"><span data-stu-id="33bb0-128">ExportBindings Command</span></span>](../core/exportbindings-command.md)  

- [<span data-ttu-id="33bb0-129">Commande de ExportParties</span><span class="sxs-lookup"><span data-stu-id="33bb0-129">ExportParties Command</span></span>](../core/exportparties-command.md)

- [<span data-ttu-id="33bb0-130">Commande ExportSettings</span><span class="sxs-lookup"><span data-stu-id="33bb0-130">ExportSettings Command</span></span>](../core/exportsettings-command.md)
  
-   [<span data-ttu-id="33bb0-131">Commande ImportApp</span><span class="sxs-lookup"><span data-stu-id="33bb0-131">ImportApp Command</span></span>](../core/importapp-command.md)  
  
-   [<span data-ttu-id="33bb0-132">Commande ImportBindings</span><span class="sxs-lookup"><span data-stu-id="33bb0-132">ImportBindings Command</span></span>](../core/importbindings-command.md)  

- [<span data-ttu-id="33bb0-133">Commande de ImportParties</span><span class="sxs-lookup"><span data-stu-id="33bb0-133">ImportParties Command</span></span>](../core/importparties-command.md)

- [<span data-ttu-id="33bb0-134">Commande ImportSettings</span><span class="sxs-lookup"><span data-stu-id="33bb0-134">ImportSettings Command</span></span>](../core/importsettings-command.md)
  
-   [<span data-ttu-id="33bb0-135">Commande ListApp</span><span class="sxs-lookup"><span data-stu-id="33bb0-135">ListApp Command</span></span>](../core/listapp-command.md)  
  
-   [<span data-ttu-id="33bb0-136">Commande ListApps</span><span class="sxs-lookup"><span data-stu-id="33bb0-136">ListApps Command</span></span>](../core/listapps-command.md)  
  
-   [<span data-ttu-id="33bb0-137">Commande ListPackage</span><span class="sxs-lookup"><span data-stu-id="33bb0-137">ListPackage Command</span></span>](../core/listpackage-command.md)  
  
-   [<span data-ttu-id="33bb0-138">Commande ListTypes</span><span class="sxs-lookup"><span data-stu-id="33bb0-138">ListTypes Command</span></span>](../core/listtypes-command.md)  
  
-   [<span data-ttu-id="33bb0-139">Commande RemoveApp</span><span class="sxs-lookup"><span data-stu-id="33bb0-139">RemoveApp Command</span></span>](../core/removeapp-command.md)  
  
-   [<span data-ttu-id="33bb0-140">Commande RemoveResource</span><span class="sxs-lookup"><span data-stu-id="33bb0-140">RemoveResource Command</span></span>](../core/removeresource-command.md)  
  
-   [<span data-ttu-id="33bb0-141">Commande UninstallApp</span><span class="sxs-lookup"><span data-stu-id="33bb0-141">UninstallApp Command</span></span>](../core/uninstallapp-command.md)  
  
-   [<span data-ttu-id="33bb0-142">Comment modifier les couleurs de Console pour BTSTask</span><span class="sxs-lookup"><span data-stu-id="33bb0-142">How to Edit the Console Colors for BTSTask</span></span>](../core/how-to-edit-the-console-colors-for-btstask.md)