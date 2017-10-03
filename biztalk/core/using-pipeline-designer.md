---
title: "À l’aide du Concepteur de Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, how to
- pipelines, Pipeline Designer
ms.assetid: bdb2f5c7-f8a2-4bd6-a8d8-8b7a64f97bd0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce7a8bc7c7943ff96f0d70a802a2756f8d8c4783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-pipeline-designer"></a><span data-ttu-id="99de1-102">Utilisation du Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="99de1-102">Using Pipeline Designer</span></span>
<span data-ttu-id="99de1-103">Le Concepteur de pipeline est un éditeur graphique hébergé dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] qui permet de créer des pipelines, d'afficher les modèles de pipeline inclus dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], de déplacer les composants de pipeline au sein d'un pipeline et de configurer les pipelines, leurs étapes et leurs composants.</span><span class="sxs-lookup"><span data-stu-id="99de1-103">Pipeline Designer is a graphical editor, hosted in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], which enables you to create new pipelines; view the pipeline templates included with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]; move pipeline components within a pipeline; and configure pipelines, stages, and pipeline components.</span></span>  
  
 <span data-ttu-id="99de1-104">Le Concepteur de pipeline utilise trois outils principaux du shell [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="99de1-104">Pipeline Designer uses three key tools of the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell as part of the design experience:</span></span>  
  
-   <span data-ttu-id="99de1-105">la fenêtre Propriétés, qui permet d'afficher et de modifier la plupart des caractéristiques des objets d'un pipeline ;</span><span class="sxs-lookup"><span data-stu-id="99de1-105">The Properties window, where most of the characteristics of pipeline objects are viewed and modified.</span></span>  
  
-   <span data-ttu-id="99de1-106">la boîte à outils, utilisée en tant que source pour la surface de conception ;</span><span class="sxs-lookup"><span data-stu-id="99de1-106">The Toolbox, which is used as a source for the design surface.</span></span>  
  
-   <span data-ttu-id="99de1-107">la surface de conception, où l'on fait glisser et où l'on dépose les composants de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="99de1-107">The design surface, where components from the Toolbox are dragged and dropped.</span></span>  
  
 <span data-ttu-id="99de1-108">La figure suivante présente l'environnement du Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="99de1-108">The following figure shows the Pipeline Designer environment.</span></span>  
  
 <span data-ttu-id="99de1-109">![L’environnement d’édition du Concepteur de Pipeline](../core/media/ebiz-prog-usepipe.gif "ebiz_prog_usepipe")</span><span class="sxs-lookup"><span data-stu-id="99de1-109">![The Pipeline Designer editing environment](../core/media/ebiz-prog-usepipe.gif "ebiz_prog_usepipe")</span></span>  
<span data-ttu-id="99de1-110">Illustration de l'environnement du Concepteur de pipeline</span><span class="sxs-lookup"><span data-stu-id="99de1-110">Depicts the Pipeline Designer environment.</span></span>  
  
 <span data-ttu-id="99de1-111">Le Concepteur de pipeline est intégré au modèle de projet BizTalk pour faciliter le développement.</span><span class="sxs-lookup"><span data-stu-id="99de1-111">Pipeline Designer is integrated with the BizTalk project template to enhance your development experience.</span></span> <span data-ttu-id="99de1-112">Après avoir utilisé le système de projet pour créer un projet BizTalk, vous pouvez utiliser la **ajouter un nouvel élément** commande sur le **fichier** menu pour ajouter un pipeline à votre solution.</span><span class="sxs-lookup"><span data-stu-id="99de1-112">After using the project system to create a new BizTalk project, you can use the **Add New Item** command on the **File** menu to add a pipeline to your solution.</span></span> <span data-ttu-id="99de1-113">Pour plus d’informations sur le modèle de projet BizTalk, consultez [à l’aide du système de projet BizTalk](../core/using-the-biztalk-project-system.md).</span><span class="sxs-lookup"><span data-stu-id="99de1-113">For more information about the BizTalk project template, see [Using the BizTalk Project System](../core/using-the-biztalk-project-system.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99de1-114">Dans les précédentes versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le concept de pipeline était encapsulé dans les ports et les canaux de message qui définissaient un ensemble de composants spécifiques qui étaient appliqués à un document.</span><span class="sxs-lookup"><span data-stu-id="99de1-114">In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the concept of a pipeline was encapsulated in message channels and ports, which defined a set order of specific components that were applied to a document.</span></span> <span data-ttu-id="99de1-115">Dans cette version, le pipeline est souple, car vous êtes libre de réagencer les composants à chaque étape du pipeline et vous pouvez insérer facilement des composants personnalisés dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="99de1-115">In this version, the pipeline is flexible because you are free to reorder the components in each stage of the pipeline and can easily insert multiple custom components throughout the pipeline.</span></span>  
  
 <span data-ttu-id="99de1-116">La surface de conception du Concepteur de pipeline permet de tracer une représentation graphique d'un pipeline.</span><span class="sxs-lookup"><span data-stu-id="99de1-116">The Pipeline Designer design surface enables you to draw a graphical representation of a pipeline.</span></span> <span data-ttu-id="99de1-117">Elle occupe la section principale de la fenêtre [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et permet de modifier les pipelines d'un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="99de1-117">The design surface occupies the main section of the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] window and enables you to edit the pipelines belonging to a BizTalk project.</span></span> <span data-ttu-id="99de1-118">Vous pouvez naviguer entre les pipelines en cliquant sur les onglets situés au-dessus de la surface de conception.</span><span class="sxs-lookup"><span data-stu-id="99de1-118">You can navigate between pipelines by clicking the tabs above the design surface.</span></span>  
  
 <span data-ttu-id="99de1-119">Chaque pipeline est composé d'étapes dont chacune contient un ou plusieurs composants.</span><span class="sxs-lookup"><span data-stu-id="99de1-119">Each pipeline is composed of stages, with each stage containing one or more components.</span></span> <span data-ttu-id="99de1-120">Si une étape n'a pas de composants, un filigrane avec du texte indique qu'il est possible d'insérer des formes à partir de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="99de1-120">If there are no components in a stage, a watermark with text indicates that shapes can be inserted from the Toolbox.</span></span> <span data-ttu-id="99de1-121">Quand la première forme est insérée dans une étape, le texte initial disparaît.</span><span class="sxs-lookup"><span data-stu-id="99de1-121">When the first shape is inserted into a stage, the initial text disappears.</span></span> <span data-ttu-id="99de1-122">La surface de conception présente le pipeline verticalement, s'exécutant du haut (début) vers le bas (fin).</span><span class="sxs-lookup"><span data-stu-id="99de1-122">The design surface shows the pipeline vertically, running from top (start) to bottom (end).</span></span>  
  
 <span data-ttu-id="99de1-123">Comme avec d’autres programmes Microsoft Windows courants, vous pouvez effectuer plusieurs tâches, telles que **ouvrir** et **enregistrer** à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="99de1-123">As with other common Microsoft Windows programs, you can perform several tasks, such as **Open** and **Save** from the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99de1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99de1-124">See Also</span></span>  
 <span data-ttu-id="99de1-125">[Création de Pipelines avec le Concepteur de Pipeline](../core/creating-pipelines-with-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="99de1-125">[Creating Pipelines with Pipeline Designer](../core/creating-pipelines-with-pipeline-designer.md) </span></span>  
 [<span data-ttu-id="99de1-126">Création de Pipelines à l’aide du Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="99de1-126">Creating Pipelines Using Pipeline Designer</span></span>](../core/creating-pipelines-using-pipeline-designer.md)