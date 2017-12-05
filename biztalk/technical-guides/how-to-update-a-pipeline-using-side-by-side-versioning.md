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
ms.openlocfilehash: 8a5b977d8f0d1964df33c2b2f549bd420d0d3179
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a><span data-ttu-id="868ed-102">Comment mettre à jour d’un Pipeline à l’aide de la gestion des versions côte à côte</span><span class="sxs-lookup"><span data-stu-id="868ed-102">How to Update a Pipeline Using Side-by-Side Versioning</span></span>
<span data-ttu-id="868ed-103">Pour utiliser un pipeline ajouté par le contrôle de version côte à côte, la simple consiste à sélectionner la version de pipeline qui vient d’être déployé dans le port d’envoi ou emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="868ed-103">The simple way to use a new pipeline added by side-by-side versioning is to select the newly deployed pipeline version in the send port or receive location.</span></span> <span data-ttu-id="868ed-104">Cela remplace le pipeline ancien par le nouveau.</span><span class="sxs-lookup"><span data-stu-id="868ed-104">This will replace the old pipeline with the new one.</span></span> <span data-ttu-id="868ed-105">Toutefois, si vous avez besoin des fonctionnalités côte-à-côte true pour la compatibilité descendante, puis vous devez créer nouveaux ports d’envoi et emplacements de réception et les lier à la nouvelle version de pipeline spécifiée.</span><span class="sxs-lookup"><span data-stu-id="868ed-105">However, if you need true side-by-side functionality for backwards-compatibility, then you must create new send ports and receive locations and bind them to the new pipeline version specified.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="868ed-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="868ed-106">Prerequisites</span></span>  
 <span data-ttu-id="868ed-107">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="868ed-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a><span data-ttu-id="868ed-108">Pour ajouter une nouvelle version d’un composant de pipeline</span><span class="sxs-lookup"><span data-stu-id="868ed-108">To add a new version of a pipeline component</span></span>  
  
1.  <span data-ttu-id="868ed-109">Dans Visual Studio, créez une nouvelle version du composant de pipeline, et signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="868ed-109">In Visual Studio, create a new version of the pipeline component, and sign the assembly.</span></span>  
  
2.  <span data-ttu-id="868ed-110">Ajouter le composant de pipeline dans le **composants de Pipeline** dossier (\<*dossier d’installation*\>\Pipeline Components).</span><span class="sxs-lookup"><span data-stu-id="868ed-110">Add the pipeline component in the **Pipeline Components** folder (\<*installation folder*\>\Pipeline Components).</span></span>  
  
3.  <span data-ttu-id="868ed-111">Ajouter le composant de pipeline à votre pipeline.</span><span class="sxs-lookup"><span data-stu-id="868ed-111">Add the pipeline component to your pipeline.</span></span>  
  
4.  <span data-ttu-id="868ed-112">Après la création du pipeline ou déploiement de votre solution, supprimer le composant de pipeline à partir de la **composants de Pipeline** dossier.</span><span class="sxs-lookup"><span data-stu-id="868ed-112">After building the pipeline or deploying your solution, remove the pipeline component from the **Pipeline Components** folder.</span></span>  
  
5.  <span data-ttu-id="868ed-113">Ajouter le composant de pipeline dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="868ed-113">Add the pipeline component to the global assembly cache (GAC).</span></span>  
  
 <span data-ttu-id="868ed-114">Une fois que vous aurez effectué ces étapes, l’assembly de pipeline compilé fait référence à la version correcte du composant de pipeline, et que le domaine d’application utilisé par BizTalk Server trouvera la nouvelle version du composant de pipeline dans le GAC, au lieu de recherche précédent version du composant de pipeline dans le dossier composants de Pipeline.</span><span class="sxs-lookup"><span data-stu-id="868ed-114">After you have completed these steps, the compiled pipeline assembly will refer to the correct version of the pipeline component, and the AppDomain used by BizTalk Server will find the new version of the pipeline component in the GAC, rather than finding the previous version of the pipeline component in the Pipeline Components folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868ed-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="868ed-115">See Also</span></span>  
 [<span data-ttu-id="868ed-116">Mise à jour en utilisant la gestion des versions côte à côte</span><span class="sxs-lookup"><span data-stu-id="868ed-116">Updating Using Side-by-Side Versioning</span></span>](../technical-guides/updating-using-side-by-side-versioning.md)