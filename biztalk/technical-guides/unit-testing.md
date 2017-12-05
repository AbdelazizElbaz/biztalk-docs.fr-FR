---
title: Tests unitaires | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c40e5b82-dbb2-4767-8286-88e2de4129f3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5f792adf73fb1e3791f0dfe6c8c5f60a3bb81e6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing"></a><span data-ttu-id="4d12d-102">Tests unitaires</span><span class="sxs-lookup"><span data-stu-id="4d12d-102">Unit Testing</span></span>
<span data-ttu-id="4d12d-103">BizTalk Server introduit une fonctionnalité qui peut être activée sur de test unitaire la **déploiement** page de propriétés d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4d12d-103">BizTalk Server introduces a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project.</span></span> <span data-ttu-id="4d12d-104">La capture d’écran suivante montre ce paramètre de projet accédé à partir du Concepteur de projet lorsque vous cliquez sur un projet, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4d12d-104">The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click **Properties**.</span></span>  
  
 <span data-ttu-id="4d12d-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span><span class="sxs-lookup"><span data-stu-id="4d12d-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span></span>  
  
 <span data-ttu-id="4d12d-106">**Capture d’écran de l’onglet du déploiement dans le Concepteur de projet qui expose la propriété de projet activer le test unitaire**</span><span class="sxs-lookup"><span data-stu-id="4d12d-106">**Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property**</span></span>  
  
 <span data-ttu-id="4d12d-107">Cette fonctionnalité permet de créer des tests unitaires pour les schémas, mappages et pipelines.</span><span class="sxs-lookup"><span data-stu-id="4d12d-107">This feature allows you to create unit tests for schemas, maps, and pipelines.</span></span> <span data-ttu-id="4d12d-108">Les rubriques de la documentation de BizTalk Server fournissent des exemples à l’aide de la fonctionnalité de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="4d12d-108">The topics in the BizTalk Server documentation provide some example approaches to using the unit testing feature.</span></span> <span data-ttu-id="4d12d-109">Lorsque cette fonctionnalité est activée et le projet recréé, les classes d'artefact sont dérivées des classes de base suivantes dans le cadre de la prise en charge du test unitaire.</span><span class="sxs-lookup"><span data-stu-id="4d12d-109">When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.</span></span>  
  
|<span data-ttu-id="4d12d-110">Type d'artefact</span><span class="sxs-lookup"><span data-stu-id="4d12d-110">Artifact type</span></span>|<span data-ttu-id="4d12d-111">Classe de base</span><span class="sxs-lookup"><span data-stu-id="4d12d-111">Base class</span></span>|  
|-------------------|----------------|  
|<span data-ttu-id="4d12d-112">schéma</span><span class="sxs-lookup"><span data-stu-id="4d12d-112">Schema</span></span>|<span data-ttu-id="4d12d-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span><span class="sxs-lookup"><span data-stu-id="4d12d-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span></span>|  
|<span data-ttu-id="4d12d-114">Mappage</span><span class="sxs-lookup"><span data-stu-id="4d12d-114">Map</span></span>|<span data-ttu-id="4d12d-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span><span class="sxs-lookup"><span data-stu-id="4d12d-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span></span>|  
|<span data-ttu-id="4d12d-116">Pipeline</span><span class="sxs-lookup"><span data-stu-id="4d12d-116">Pipeline</span></span>|<span data-ttu-id="4d12d-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span><span class="sxs-lookup"><span data-stu-id="4d12d-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span></span>|  
  
 <span data-ttu-id="4d12d-118">Pour plus d’informations sur la fonctionnalité introduite avec BizTalk Server de test unitaire, consultez les rubriques suivantes dans l’aide de BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="4d12d-118">For more information about the unit testing feature introduced with BizTalk Server, see the following topics in the BizTalk Server Help:</span></span>  
  
-   <span data-ttu-id="4d12d-119">[À l’aide de la fonctionnalité de schémas et mappages de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150482) (http://go.microsoft.com/fwlink/?LinkId=150482).</span><span class="sxs-lookup"><span data-stu-id="4d12d-119">[Using the Unit Testing Feature with Schemas and Maps](http://go.microsoft.com/fwlink/?LinkId=150482) (http://go.microsoft.com/fwlink/?LinkId=150482).</span></span>  
  
-   <span data-ttu-id="4d12d-120">[À l’aide de la fonctionnalité avec des Pipelines de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150483) (http://go.microsoft.com/fwlink/?LinkId=150483)</span><span class="sxs-lookup"><span data-stu-id="4d12d-120">[Using the Unit Testing Feature with Pipelines](http://go.microsoft.com/fwlink/?LinkId=150483) (http://go.microsoft.com/fwlink/?LinkId=150483)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d12d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d12d-121">See Also</span></span>  
 [<span data-ttu-id="4d12d-122">Implémentation de tests automatisés</span><span class="sxs-lookup"><span data-stu-id="4d12d-122">Implementing Automated Testing</span></span>](../technical-guides/implementing-automated-testing.md)