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
ms.openlocfilehash: 15f73b9c343e62e0a0a83bf76f8c762b9ce9ede9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unit-testing-with-biztalk-server-projects"></a><span data-ttu-id="7ad09-102">Test unitaire avec des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7ad09-102">Unit Testing with BizTalk Server Projects</span></span>
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="7ad09-103">a introduit une fonctionnalité qui peut être activée sur de test unitaire la **déploiement** page de propriétés d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7ad09-103"> introduced a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project.</span></span> <span data-ttu-id="7ad09-104">La capture d’écran suivante montre ce paramètre de projet accédé à partir du Concepteur de projet lorsque vous cliquez sur un projet, cliquez sur le **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7ad09-104">The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click the **Properties**.</span></span>  
  
 ![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")  
  
 <span data-ttu-id="7ad09-105">**Capture d’écran de l’onglet du déploiement dans le Concepteur de projet qui expose la propriété de projet activer le test unitaire.**</span><span class="sxs-lookup"><span data-stu-id="7ad09-105">**Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property.**</span></span>  
  
 <span data-ttu-id="7ad09-106">Cette fonctionnalité permet de créer des tests unitaires pour les schémas, mappages et pipelines.</span><span class="sxs-lookup"><span data-stu-id="7ad09-106">This feature allows you to create unit tests for schemas, maps, and pipelines.</span></span> <span data-ttu-id="7ad09-107">Les rubriques de cette section fournissent des exemples d'utilisation de la fonctionnalité de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="7ad09-107">The topics in this section provide some example approaches to using the unit testing feature.</span></span> <span data-ttu-id="7ad09-108">Lorsque cette fonctionnalité est activée et le projet recréé, les classes d'artefact sont dérivées des classes de base suivantes dans le cadre de la prise en charge du test unitaire.</span><span class="sxs-lookup"><span data-stu-id="7ad09-108">When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.</span></span>  
  
|<span data-ttu-id="7ad09-109">Type d'artefact</span><span class="sxs-lookup"><span data-stu-id="7ad09-109">Artifact type</span></span>|<span data-ttu-id="7ad09-110">Classe de base</span><span class="sxs-lookup"><span data-stu-id="7ad09-110">Base class</span></span>|  
|-------------------|----------------|  
|<span data-ttu-id="7ad09-111">schéma</span><span class="sxs-lookup"><span data-stu-id="7ad09-111">Schema</span></span>|<span data-ttu-id="7ad09-112">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span><span class="sxs-lookup"><span data-stu-id="7ad09-112">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span></span>|  
|<span data-ttu-id="7ad09-113">Mappage</span><span class="sxs-lookup"><span data-stu-id="7ad09-113">Map</span></span>|<span data-ttu-id="7ad09-114">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span><span class="sxs-lookup"><span data-stu-id="7ad09-114">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span></span>|  
|<span data-ttu-id="7ad09-115">Pipeline</span><span class="sxs-lookup"><span data-stu-id="7ad09-115">Pipeline</span></span>|<span data-ttu-id="7ad09-116">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span><span class="sxs-lookup"><span data-stu-id="7ad09-116">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="7ad09-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7ad09-117">In This Section</span></span>  
  
-   [<span data-ttu-id="7ad09-118">À l’aide de la fonctionnalité de schémas et mappages de test unitaire</span><span class="sxs-lookup"><span data-stu-id="7ad09-118">Using the Unit Testing Feature with Schemas and Maps</span></span>](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)  
  
-   [<span data-ttu-id="7ad09-119">À l’aide de la fonctionnalité avec des Pipelines de test unitaire</span><span class="sxs-lookup"><span data-stu-id="7ad09-119">Using the Unit Testing Feature with Pipelines</span></span>](../core/using-the-unit-testing-feature-with-pipelines.md)  
  
## <a name="related-sections"></a><span data-ttu-id="7ad09-120">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="7ad09-120">Related Sections</span></span>  
 [<span data-ttu-id="7ad09-121">Travailler avec des Tests unitaires (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="7ad09-121">Working with Unit Tests (Visual Studio)</span></span>](http://go.microsoft.com/fwlink/?LinkId=128890)