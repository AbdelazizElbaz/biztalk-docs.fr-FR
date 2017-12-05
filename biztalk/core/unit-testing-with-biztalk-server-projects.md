---
title: Tests unitaires avec les projets BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2594f29-fc34-4dda-9316-2afd4e0056d7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da7147f4c2500946fb97c47592a2a4a35d3dcf62
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing-with-biztalk-server-projects"></a><span data-ttu-id="0bf19-102">Test unitaire avec des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0bf19-102">Unit Testing with BizTalk Server Projects</span></span>
<span data-ttu-id="0bf19-103">BizTalk Server introduit une fonctionnalité qui peut être activée sur de test unitaire la **déploiement** page de propriétés d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0bf19-103">BizTalk Server introduced a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project.</span></span> <span data-ttu-id="0bf19-104">La capture d’écran suivante montre ce paramètre de projet accédé à partir du Concepteur de projet lorsque vous cliquez sur un projet, cliquez sur le **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0bf19-104">The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click the **Properties**.</span></span>  
  
 <span data-ttu-id="0bf19-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span><span class="sxs-lookup"><span data-stu-id="0bf19-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span></span>  
  
 <span data-ttu-id="0bf19-106">**Capture d’écran de l’onglet du déploiement dans le Concepteur de projet qui expose la propriété de projet activer le test unitaire.**</span><span class="sxs-lookup"><span data-stu-id="0bf19-106">**Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property.**</span></span>  
  
 <span data-ttu-id="0bf19-107">Cette fonctionnalité permet de créer des tests unitaires pour les schémas, mappages et pipelines.</span><span class="sxs-lookup"><span data-stu-id="0bf19-107">This feature allows you to create unit tests for schemas, maps, and pipelines.</span></span> <span data-ttu-id="0bf19-108">Les rubriques de cette section fournissent des exemples d'utilisation de la fonctionnalité de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="0bf19-108">The topics in this section provide some example approaches to using the unit testing feature.</span></span> <span data-ttu-id="0bf19-109">Lorsque cette fonctionnalité est activée et le projet recréé, les classes d'artefact sont dérivées des classes de base suivantes dans le cadre de la prise en charge du test unitaire.</span><span class="sxs-lookup"><span data-stu-id="0bf19-109">When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.</span></span>  
  
|<span data-ttu-id="0bf19-110">Type d'artefact</span><span class="sxs-lookup"><span data-stu-id="0bf19-110">Artifact type</span></span>|<span data-ttu-id="0bf19-111">Classe de base</span><span class="sxs-lookup"><span data-stu-id="0bf19-111">Base class</span></span>|  
|-------------------|----------------|  
|<span data-ttu-id="0bf19-112">schéma</span><span class="sxs-lookup"><span data-stu-id="0bf19-112">Schema</span></span>|<span data-ttu-id="0bf19-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span><span class="sxs-lookup"><span data-stu-id="0bf19-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span></span>|  
|<span data-ttu-id="0bf19-114">Mappage</span><span class="sxs-lookup"><span data-stu-id="0bf19-114">Map</span></span>|<span data-ttu-id="0bf19-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span><span class="sxs-lookup"><span data-stu-id="0bf19-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span></span>|  
|<span data-ttu-id="0bf19-116">Pipeline</span><span class="sxs-lookup"><span data-stu-id="0bf19-116">Pipeline</span></span>|<span data-ttu-id="0bf19-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span><span class="sxs-lookup"><span data-stu-id="0bf19-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="0bf19-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0bf19-118">In This Section</span></span>  
  
-   [<span data-ttu-id="0bf19-119">À l’aide de la fonctionnalité de schémas et mappages de test unitaire</span><span class="sxs-lookup"><span data-stu-id="0bf19-119">Using the Unit Testing Feature with Schemas and Maps</span></span>](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)  
  
-   [<span data-ttu-id="0bf19-120">À l’aide de la fonctionnalité avec des Pipelines de test unitaire</span><span class="sxs-lookup"><span data-stu-id="0bf19-120">Using the Unit Testing Feature with Pipelines</span></span>](../core/using-the-unit-testing-feature-with-pipelines.md)  
  
## <a name="related-sections"></a><span data-ttu-id="0bf19-121">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0bf19-121">Related Sections</span></span>  
 [<span data-ttu-id="0bf19-122">Travailler avec des Tests unitaires (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="0bf19-122">Working with Unit Tests (Visual Studio)</span></span>](http://go.microsoft.com/fwlink/?LinkId=128890)