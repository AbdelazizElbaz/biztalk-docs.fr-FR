---
title: "Comment créer un Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipelines, warnings
- Pipeline Designer, warnings
- pipelines, creating
ms.assetid: bd95325e-1a72-4705-80f6-37ac092d11a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83c1df14c0015ac26b99ad8f0760fe18438e8024
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-pipeline"></a><span data-ttu-id="ba198-102">Création d'un pipeline</span><span class="sxs-lookup"><span data-stu-id="ba198-102">How to Create a New Pipeline</span></span>
<span data-ttu-id="ba198-103">Vous pouvez ajouter un modèle de pipeline à votre projet pour créer un pipeline.</span><span class="sxs-lookup"><span data-stu-id="ba198-103">You can add a pipeline template to your project to create a new pipeline.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ba198-104">Vous ne devez pas ajouter un projet qui contient une implémentation d’un composant de pipeline personnalisé à une solution qui contient un projet qui utilise ce composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ba198-104">You should not add a project that contains an implementation of a custom pipeline component to a solution that contains a project that uses that pipleine component.</span></span> <span data-ttu-id="ba198-105">En effet, si vous le faites, la prochaine fois que vous reconstruirez la solution, vous obtiendrez un message d'erreur indiquant que le fichier dll de sortie est actuellement utilisé par un autre processus.</span><span class="sxs-lookup"><span data-stu-id="ba198-105">If you do, the next time you rebuild the solution you will get an error saying the output dll is being used by another process.</span></span>  
  
### <a name="to-create-a-new-pipeline"></a><span data-ttu-id="ba198-106">Pour créer un pipeline</span><span class="sxs-lookup"><span data-stu-id="ba198-106">To create a new pipeline</span></span>  
  
1.  <span data-ttu-id="ba198-107">Dans l'Explorateur de solutions, sélectionnez le projet où vous souhaitez créer le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ba198-107">In Solution Explorer, select the project in which you want to create the pipeline.</span></span>  
  
2.  <span data-ttu-id="ba198-108">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="ba198-108">On the **Project** menu, click **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="ba198-109">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez un **Pipeline de réception** ou **Pipeline d’envoi** en cliquant dessus une fois.</span><span class="sxs-lookup"><span data-stu-id="ba198-109">In the **Add New Item** dialog box, select a **Receive Pipeline** or **Send Pipeline** template by clicking it once.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba198-110">Si vous double-cliquez sur le modèle, celui-ci sera automatiquement créé avec le nom par défaut qui s’affiche dans le **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="ba198-110">If you double-click the template, the pipeline will automatically be created with the default name that appears in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="ba198-111">Dans le **nom** , tapez un nom pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="ba198-111">In the **Name** field, type a name for the pipeline.</span></span>  
  
5.  <span data-ttu-id="ba198-112">Cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="ba198-112">Click **Open**.</span></span>  
  
     <span data-ttu-id="ba198-113">Le nouveau pipeline apparaît dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="ba198-113">The new pipeline appears in Solution Explorer.</span></span> <span data-ttu-id="ba198-114">La surface de conception affiche les étapes du pipeline et un ensemble de composants par défaut.</span><span class="sxs-lookup"><span data-stu-id="ba198-114">The design surface displays pipeline stages and a default set of components.</span></span>  
  
 <span data-ttu-id="ba198-115">Pour plus d’informations sur l’ajout de composants de pipeline au pipeline, consultez [l’ajout d’un composant de pipeline](../core/how-to-add-a-component-to-a-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="ba198-115">For information about adding pipeline components to the pipeline, see [How to Add a Component to a Pipeline](../core/how-to-add-a-component-to-a-pipeline.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba198-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba198-116">See Also</span></span>  
 <span data-ttu-id="ba198-117">[Comment ouvrir un Pipeline](../core/how-to-open-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="ba198-117">[How to Open a Pipeline](../core/how-to-open-a-pipeline.md) </span></span>  
 <span data-ttu-id="ba198-118">[Comment enregistrer un Pipeline](../core/how-to-save-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="ba198-118">[How to Save a Pipeline](../core/how-to-save-a-pipeline.md) </span></span>  
 <span data-ttu-id="ba198-119">[L’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md) </span><span class="sxs-lookup"><span data-stu-id="ba198-119">[How to Use the Toolbox](../core/how-to-use-the-toolbox.md) </span></span>  
 <span data-ttu-id="ba198-120">[Comment accéder à l’aide du clavier](../core/how-to-navigate-with-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="ba198-120">[How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md) </span></span>  
 [<span data-ttu-id="ba198-121">Création de Pipelines avec le Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="ba198-121">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)