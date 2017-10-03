---
title: "Comment mettre à jour les Versions de stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, publishing
- publishing policies
- updating, policies
- versioning, policies
- policies, versioning
- policies, updating
ms.assetid: 6e35b2bd-1ecd-45ea-aff3-4ad2437568a4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09c73b3575ec484ab611fccac920cef6d96d3800
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-maintain-policy-versions"></a><span data-ttu-id="41430-102">Comment mettre à jour les Versions de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-102">How to Maintain Policy Versions</span></span>
<span data-ttu-id="41430-103">Une fois que vous avez ajouté des règles à une version de votre stratégie, vous pouvez soit enregistrer cette version dans le magasin de règles pour un développement ultérieur, soit la publier afin de créer un ensemble de règles bien défini et immuable pouvant être déployé afin d'être utilisé dans une application basée sur des règles.</span><span class="sxs-lookup"><span data-stu-id="41430-103">After you add rules to a version of your policy, you can save the version to the rule store for further development, or you can publish it to create a well-defined, immutable set of rules that can be deployed for use in a rule-based application.</span></span>  
  
 <span data-ttu-id="41430-104">Cette rubrique contient les procédures des tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="41430-104">This topic contains procedures for the following tasks:</span></span>  
  
-   <span data-ttu-id="41430-105">Pour créer une version vide de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-105">To create an empty new version of a policy</span></span>  
  
-   <span data-ttu-id="41430-106">Pour enregistrer une version de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-106">To save a policy version</span></span>  
  
-   <span data-ttu-id="41430-107">Pour publier une version de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-107">To publish a policy version</span></span>  
  
-   <span data-ttu-id="41430-108">Pour créer une version mise à jour de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-108">To create an updated version of a policy</span></span>  
  
-   <span data-ttu-id="41430-109">Pour mettre à jour une stratégie afin d'utiliser un assembly mis à jour</span><span class="sxs-lookup"><span data-stu-id="41430-109">To update a policy to use an updated assembly</span></span>  
  
### <a name="to-create-an-empty-new-version-of-a-policy"></a><span data-ttu-id="41430-110">Pour créer une version vide de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-110">To create an empty new version of a policy</span></span>  
  
-   <span data-ttu-id="41430-111">Cliquez sur le dossier de stratégie, puis cliquez sur **ajouter une nouvelle Version**.</span><span class="sxs-lookup"><span data-stu-id="41430-111">Right-click the policy folder, and then click **Add New Version**.</span></span>  
  
### <a name="to-save-a-policy-version"></a><span data-ttu-id="41430-112">Pour enregistrer une version de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-112">To save a policy version</span></span>  
  
-   <span data-ttu-id="41430-113">Avec le bouton droit de la version de stratégie, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="41430-113">Right-click the policy version, and then click **Save**.</span></span>  
  
### <a name="to-publish-a-policy-version"></a><span data-ttu-id="41430-114">Pour publier une version de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-114">To publish a policy version</span></span>  
  
-   <span data-ttu-id="41430-115">Avec le bouton droit de la version de stratégie, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="41430-115">Right-click the policy version, and then click **Publish**.</span></span>  
  
### <a name="to-create-an-updated-version-of-a-policy"></a><span data-ttu-id="41430-116">Pour créer une version mise à jour de stratégie</span><span class="sxs-lookup"><span data-stu-id="41430-116">To create an updated version of a policy</span></span>  
  
1.  <span data-ttu-id="41430-117">Cliquez sur une version de stratégie existante, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="41430-117">Right-click an existing policy version, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="41430-118">Cliquez sur le dossier de stratégie, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="41430-118">Right-click the policy folder, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="41430-119">Une nouvelle version est alors créée. Ses éléments sont les mêmes que ceux de la version copiée.</span><span class="sxs-lookup"><span data-stu-id="41430-119">A new version is created, with the same elements as the copied version.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41430-120">Si votre stratégie utilise un assembly .NET et que cet assembly est mis à jour, vous devrez la lier à la dernière version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="41430-120">If your policy uses a .NET assembly, and the assembly is updated, you should bind your policy to the newer version of the assembly.</span></span>  
  
### <a name="to-update-a-policy-to-use-an-updated-assembly"></a><span data-ttu-id="41430-121">Pour mettre à jour une stratégie afin d'utiliser un assembly mis à jour</span><span class="sxs-lookup"><span data-stu-id="41430-121">To update a policy to use an updated assembly</span></span>  
  
1.  <span data-ttu-id="41430-122">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, pointez sur **.NET Framework Configuration**, puis cliquez sur **assemblys configurés** .</span><span class="sxs-lookup"><span data-stu-id="41430-122">Click **Start**, point to **Administrative Tools**, point to **.NET Framework Configuration**, and then click **Configured Assemblies**.</span></span>  
  
2.  <span data-ttu-id="41430-123">Accédez aux propriétés de l’assembly cible et cliquez sur le **stratégie de liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="41430-123">Go to properties for the target assembly and click the **Binding Policy** tab.</span></span>  
  
3.  <span data-ttu-id="41430-124">Dans le Global Assembly Cache, remplacez le numéro de version par celui de la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="41430-124">In the global assembly cache, change the version number to the newer version.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41430-125">Tous les assemblys utilisés par les stratégies doivent être ajoutés au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="41430-125">All assemblies used by policies should be added to the global assembly cache.</span></span>