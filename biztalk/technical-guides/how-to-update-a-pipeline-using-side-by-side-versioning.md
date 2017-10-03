---
title: "Comment mettre à jour d’un Pipeline à l’aide de la gestion des versions côte-à-côte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd884a76-71dd-4c90-b4ba-f1cd7f48eb04
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c4e8803128f2232905229de3b5de49994e039ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a><span data-ttu-id="f7d77-102">Comment mettre à jour d’un Pipeline à l’aide de la gestion des versions côte à côte</span><span class="sxs-lookup"><span data-stu-id="f7d77-102">How to Update a Pipeline Using Side-by-Side Versioning</span></span>
<span data-ttu-id="f7d77-103">Pour utiliser un pipeline ajouté par le contrôle de version côte à côte, la simple consiste à sélectionner la version de pipeline qui vient d’être déployé dans le port d’envoi ou emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f7d77-103">The simple way to use a new pipeline added by side-by-side versioning is to select the newly deployed pipeline version in the send port or receive location.</span></span> <span data-ttu-id="f7d77-104">Cela remplace le pipeline ancien par le nouveau.</span><span class="sxs-lookup"><span data-stu-id="f7d77-104">This will replace the old pipeline with the new one.</span></span> <span data-ttu-id="f7d77-105">Toutefois, si vous avez besoin des fonctionnalités côte-à-côte true pour la compatibilité descendante, puis vous devez créer nouveaux ports d’envoi et emplacements de réception et les lier à la nouvelle version de pipeline spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f7d77-105">However, if you need true side-by-side functionality for backwards-compatibility, then you must create new send ports and receive locations and bind them to the new pipeline version specified.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f7d77-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f7d77-106">Prerequisites</span></span>  
 <span data-ttu-id="f7d77-107">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f7d77-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a><span data-ttu-id="f7d77-108">Pour ajouter une nouvelle version d’un composant de pipeline</span><span class="sxs-lookup"><span data-stu-id="f7d77-108">To add a new version of a pipeline component</span></span>  
  
1.  <span data-ttu-id="f7d77-109">Dans Visual Studio, créez une nouvelle version du composant de pipeline, et signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f7d77-109">In Visual Studio, create a new version of the pipeline component, and sign the assembly.</span></span>  
  
2.  <span data-ttu-id="f7d77-110">Ajouter le composant de pipeline dans le **composants de Pipeline** dossier (\<*dossier d’installation*> \Pipeline Components).</span><span class="sxs-lookup"><span data-stu-id="f7d77-110">Add the pipeline component in the **Pipeline Components** folder (\<*installation folder*>\Pipeline Components).</span></span>  
  
3.  <span data-ttu-id="f7d77-111">Ajouter le composant de pipeline à votre pipeline.</span><span class="sxs-lookup"><span data-stu-id="f7d77-111">Add the pipeline component to your pipeline.</span></span>  
  
4.  <span data-ttu-id="f7d77-112">Après la création du pipeline ou déploiement de votre solution, supprimer le composant de pipeline à partir de la **composants de Pipeline** dossier.</span><span class="sxs-lookup"><span data-stu-id="f7d77-112">After building the pipeline or deploying your solution, remove the pipeline component from the **Pipeline Components** folder.</span></span>  
  
5.  <span data-ttu-id="f7d77-113">Ajouter le composant de pipeline dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="f7d77-113">Add the pipeline component to the global assembly cache (GAC).</span></span>  
  
 <span data-ttu-id="f7d77-114">Une fois que vous avez effectué ces étapes, l’assembly de pipeline compilé fait référence à la version correcte du composant de pipeline, et le domaine d’application utilisés par [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] trouverez la nouvelle version du composant de pipeline dans le GAC, au lieu de recherche précédent version du composant de pipeline dans le dossier composants de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="f7d77-114">After you have completed these steps, the compiled pipeline assembly will refer to the correct version of the pipeline component, and the AppDomain used by [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] will find the new version of the pipeline component in the GAC, rather than finding the previous version of the pipeline component in the Pipeline Components folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d77-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7d77-115">See Also</span></span>  
 [<span data-ttu-id="f7d77-116">La mise à jour à l’aide du contrôle de version côte à côte</span><span class="sxs-lookup"><span data-stu-id="f7d77-116">Updating Using Side-by-Side Versioning</span></span>](../technical-guides/updating-using-side-by-side-versioning.md)