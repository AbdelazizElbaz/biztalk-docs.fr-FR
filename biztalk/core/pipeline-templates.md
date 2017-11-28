---
title: "Modèles de pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, templates
- Pipeline Designer, templates
- send pipelines, templates
- receive pipelines, templates
ms.assetid: b9779159-e49d-47fb-aa1c-06be5d604c67
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed6af41d3c23c889b7a7e9bd2529adc80bc7bcd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pipeline-templates"></a><span data-ttu-id="4f77c-102">Modèles de pipeline</span><span class="sxs-lookup"><span data-stu-id="4f77c-102">Pipeline Templates</span></span>
<span data-ttu-id="4f77c-103">En plus des pipelines par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut deux modèles de pipeline : un modèle de pipeline de réception et un modèle de pipeline d’envoi.</span><span class="sxs-lookup"><span data-stu-id="4f77c-103">In addition to the default pipelines, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes two pipeline templates: a receive pipeline template and a send pipeline template.</span></span> <span data-ttu-id="4f77c-104">À partir d’un projet BizTalk dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez ajouter un modèle de pipeline à votre projet à l’aide de la **ajouter un nouvel élément** commande sur le **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="4f77c-104">From a BizTalk project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can add a pipeline template to your project by using the **Add New Item** command on the **Project** menu.</span></span> <span data-ttu-id="4f77c-105">À chaque modèle est associé un fichier de stratégie qui détermine les étapes du pipeline et indique quels composants de pipeline sont autorisés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f77c-105">Each template has an associated policy file, which determines the pipeline's stages and indicates which pipeline components are allowed in the pipeline.</span></span> <span data-ttu-id="4f77c-106">Vous ne pouvez pas changer l'ordre des étapes d'un fichier de stratégie, mais vous pouvez utiliser le Concepteur de pipeline pour réagencer les composants d'une étape.</span><span class="sxs-lookup"><span data-stu-id="4f77c-106">While you cannot reorder the stages in a policy file, you can use Pipeline Designer to reorder the components within a stage.</span></span>  
  
 <span data-ttu-id="4f77c-107">Un fichier de stratégie spécifie :</span><span class="sxs-lookup"><span data-stu-id="4f77c-107">A policy file specifies:</span></span>  
  
-   <span data-ttu-id="4f77c-108">l'ordre des étapes ;</span><span class="sxs-lookup"><span data-stu-id="4f77c-108">The sequence of stages.</span></span>  
  
-   <span data-ttu-id="4f77c-109">le nombre de composants autorisés par étape ;</span><span class="sxs-lookup"><span data-stu-id="4f77c-109">The number of components allowed per stage.</span></span>  
  
-   <span data-ttu-id="4f77c-110">le mode d'exécution de chaque étape.</span><span class="sxs-lookup"><span data-stu-id="4f77c-110">The execution mode of each stage.</span></span>  
  
 <span data-ttu-id="4f77c-111">Les fichiers de stratégie pour les modèles de pipeline sont stockés dans  *\<répertoire d’installation de BizTalk Server >*\Developer Tools\Pipeline les fichiers de stratégie.</span><span class="sxs-lookup"><span data-stu-id="4f77c-111">The policy files for the pipeline templates are stored in *\<BizTalk Server installation directory>*\Developer Tools\Pipeline Policy Files.</span></span> <span data-ttu-id="4f77c-112">Vous ne devez pas les modifier.</span><span class="sxs-lookup"><span data-stu-id="4f77c-112">Do not modify the policy files.</span></span> <span data-ttu-id="4f77c-113">Pour modifier un pipeline, ouvrez le modèle de pipeline et utilisez le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f77c-113">To make changes to a pipeline, open the pipeline template and use Pipeline Designer to modify it.</span></span> <span data-ttu-id="4f77c-114">Pour plus d’informations sur l’utilisation du Concepteur de Pipeline, consultez [à l’aide du Concepteur de Pipeline](../core/using-pipeline-designer.md).</span><span class="sxs-lookup"><span data-stu-id="4f77c-114">For more information about using Pipeline Designer, see [Using Pipeline Designer](../core/using-pipeline-designer.md).</span></span>  
  
 <span data-ttu-id="4f77c-115">Les fichiers de modèle de pipeline vide sont stockés dans  *\<répertoire d’installation de BizTalk Server >*\Developer Tools\BizTalkProjectItems et sont nommés BTSReceivePipeline.btp et BTSTransmitPipeline.btp.</span><span class="sxs-lookup"><span data-stu-id="4f77c-115">The empty pipeline template files are stored in *\<BizTalk Server installation directory>*\Developer Tools\BizTalkProjectItems, and are named BTSReceivePipeline.btp and BTSTransmitPipeline.btp.</span></span> <span data-ttu-id="4f77c-116">L’extension de fichier .btp indique que le fichier est un pipeline BizTalk Server et peut être modifié dans le Concepteur de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="4f77c-116">The file name extension .btp indicates that the file is a BizTalk Server pipeline and can be edited in Pipeline Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f77c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f77c-117">See Also</span></span>  
 <span data-ttu-id="4f77c-118">[Types de Pipelines](../core/types-of-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="4f77c-118">[Types of Pipelines](../core/types-of-pipelines.md) </span></span>  
 <span data-ttu-id="4f77c-119">[Types de composants de Pipeline](../core/types-of-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="4f77c-119">[Types of Pipeline Components](../core/types-of-pipeline-components.md) </span></span>  
 <span data-ttu-id="4f77c-120">[Pipelines par défaut](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="4f77c-120">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="4f77c-121">[Composants de pipeline](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="4f77c-121">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="4f77c-122">À propos des Pipelines, des étapes et des composants</span><span class="sxs-lookup"><span data-stu-id="4f77c-122">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)