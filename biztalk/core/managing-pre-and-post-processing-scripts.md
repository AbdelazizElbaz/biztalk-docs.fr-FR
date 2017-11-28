---
title: "Gérer les Scripts de pré-traitement et post-traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 107ada12-fef2-4b56-8ff8-228c13761104
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18926a0c51e5ab5f65b32373d20b2931ccaa627d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-pre--and-post-processing-scripts"></a><span data-ttu-id="e86a0-102">Gérer les Scripts de pré-traitement et post-traitement</span><span class="sxs-lookup"><span data-stu-id="e86a0-102">Manage Pre- and Post-processing Scripts</span></span>

## <a name="overview"></a><span data-ttu-id="e86a0-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e86a0-103">Overview</span></span>
<span data-ttu-id="e86a0-104">Cette section fournit des instructions sur l'utilisation de la console Administration de BizTalk ou de l'outil de ligne de commande BTSTask pour la gestion les scripts de prétraitement et de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="e86a0-104">This section provides instructions on using the BizTalk Server Administration console or the BTSTask command-line tool to manage pre- and post-processing scripts.</span></span> <span data-ttu-id="e86a0-105">Vous pouvez créer un script à exécuter lors de l'importation, l'installation ou la désinstallation (suppression) d'une application BizTalk, puis ajouter le script à l'application.</span><span class="sxs-lookup"><span data-stu-id="e86a0-105">You can create a script that you want to have run when a BizTalk application is imported, installed, or uninstalled (removed), and then add the script to the application.</span></span> <span data-ttu-id="e86a0-106">Lorsque vous ajoutez un script, vous pouvez spécifier s'il s'agit d'un script de prétraitement qui s'exécute avant l'importation, l'installation ou la désinstallation d'une application, ou un script de post-traitement qui s'exécute après l'importation, l'installation ou la désinstallation d'une application.</span><span class="sxs-lookup"><span data-stu-id="e86a0-106">When you add a script, you specify whether it is a pre-preprocessing script, which runs before import, installation and after uninstallation, or a post-processing script, which runs after import or installation, and before uninstallation.</span></span>  
  
 <span data-ttu-id="e86a0-107">Si vous sélectionnez le script lors de l'exportation de l'application, le script est inclus dans le fichier .msi de l'application.</span><span class="sxs-lookup"><span data-stu-id="e86a0-107">If you select the script when exporting the application, the script is included in the .msi file for the application.</span></span> <span data-ttu-id="e86a0-108">Lorsque vous installez, désinstallez ou importez l'application, le script s'exécute automatiquement, en fonction de la manière dont vous l'avez écrit.</span><span class="sxs-lookup"><span data-stu-id="e86a0-108">When you install, uninstall, or import the application, the script automatically runs, depending on how you have written the script.</span></span> <span data-ttu-id="e86a0-109">Pour plus d’informations sur la création et à l’aide de scripts, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="e86a0-109">For more information about creating and using scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e86a0-110">Vous pouvez utiliser le Modèle objet de Microsoft Windows Management Instrumentation (WMI) pour créer et exécuter des scripts automatisant certaines tâches administratives.</span><span class="sxs-lookup"><span data-stu-id="e86a0-110">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="e86a0-111">Pour plus d’informations sur l’utilisation de WMI, consultez le **référence de classe WMI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="e86a0-111">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="e86a0-112">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e86a0-112">Next steps</span></span> 
  
-   [<span data-ttu-id="e86a0-113">Ajouter un Script de pré-traitement ou de post-traitement à une Application</span><span class="sxs-lookup"><span data-stu-id="e86a0-113">Add a Pre- or Post-processing Script to an Application</span></span>](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [<span data-ttu-id="e86a0-114">Modifier l’emplacement de Destination d’un Script de pré-traitement ou post-traitement</span><span class="sxs-lookup"><span data-stu-id="e86a0-114">Change the Destination Location of a Pre- or Post-processing Script</span></span>](../core/how-to-change-the-destination-location-of-a-pre-or-post-processing-script.md)  
  
-   [<span data-ttu-id="e86a0-115">Supprimer un Script de pré-traitement ou de post-traitement d’une Application</span><span class="sxs-lookup"><span data-stu-id="e86a0-115">Remove a Pre- or Post-processing Script from an Application</span></span>](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)