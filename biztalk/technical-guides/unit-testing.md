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
ms.openlocfilehash: faa6dd215aee23f49442e614649fa33f7321d42e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unit-testing"></a><span data-ttu-id="67988-102">Tests unitaires</span><span class="sxs-lookup"><span data-stu-id="67988-102">Unit Testing</span></span>
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]<span data-ttu-id="67988-103">introduit une fonctionnalité qui peut être activée sur de test unitaire la **déploiement** page de propriétés d’un projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="67988-103"> introduces a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project.</span></span> <span data-ttu-id="67988-104">La capture d’écran suivante montre ce paramètre de projet accédé à partir du Concepteur de projet lorsque vous cliquez sur un projet, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="67988-104">The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click **Properties**.</span></span>  
  
 ![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")  
  
 <span data-ttu-id="67988-105">**Capture d’écran de l’onglet du déploiement dans le Concepteur de projet qui expose la propriété de projet activer le test unitaire**</span><span class="sxs-lookup"><span data-stu-id="67988-105">**Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property**</span></span>  
  
 <span data-ttu-id="67988-106">Cette fonctionnalité permet de créer des tests unitaires pour les schémas, mappages et pipelines.</span><span class="sxs-lookup"><span data-stu-id="67988-106">This feature allows you to create unit tests for schemas, maps, and pipelines.</span></span> <span data-ttu-id="67988-107">Les rubriques de la [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] documentation fournissent des exemples à l’aide de la fonctionnalité de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="67988-107">The topics in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] documentation provide some example approaches to using the unit testing feature.</span></span> <span data-ttu-id="67988-108">Lorsque cette fonctionnalité est activée et le projet recréé, les classes d'artefact sont dérivées des classes de base suivantes dans le cadre de la prise en charge du test unitaire.</span><span class="sxs-lookup"><span data-stu-id="67988-108">When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.</span></span>  
  
|<span data-ttu-id="67988-109">Type d'artefact</span><span class="sxs-lookup"><span data-stu-id="67988-109">Artifact type</span></span>|<span data-ttu-id="67988-110">Classe de base</span><span class="sxs-lookup"><span data-stu-id="67988-110">Base class</span></span>|  
|-------------------|----------------|  
|<span data-ttu-id="67988-111">schéma</span><span class="sxs-lookup"><span data-stu-id="67988-111">Schema</span></span>|<span data-ttu-id="67988-112">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span><span class="sxs-lookup"><span data-stu-id="67988-112">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span></span>|  
|<span data-ttu-id="67988-113">Mappage</span><span class="sxs-lookup"><span data-stu-id="67988-113">Map</span></span>|<span data-ttu-id="67988-114">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span><span class="sxs-lookup"><span data-stu-id="67988-114">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span></span>|  
|<span data-ttu-id="67988-115">Pipeline</span><span class="sxs-lookup"><span data-stu-id="67988-115">Pipeline</span></span>|<span data-ttu-id="67988-116">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span><span class="sxs-lookup"><span data-stu-id="67988-116">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span></span>|  
  
 <span data-ttu-id="67988-117">Pour plus d’informations sur l’unité de fonctionnalité de test introduits avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], consultez les rubriques suivantes dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide :</span><span class="sxs-lookup"><span data-stu-id="67988-117">For more information about the unit testing feature introduced with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], see the following topics in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help:</span></span>  
  
-   <span data-ttu-id="67988-118">[À l’aide de la fonctionnalité de schémas et mappages de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150482) (http://go.microsoft.com/fwlink/?LinkId=150482).</span><span class="sxs-lookup"><span data-stu-id="67988-118">[Using the Unit Testing Feature with Schemas and Maps](http://go.microsoft.com/fwlink/?LinkId=150482) (http://go.microsoft.com/fwlink/?LinkId=150482).</span></span>  
  
-   <span data-ttu-id="67988-119">[À l’aide de la fonctionnalité avec des Pipelines de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150483) (http://go.microsoft.com/fwlink/?LinkId=150483)</span><span class="sxs-lookup"><span data-stu-id="67988-119">[Using the Unit Testing Feature with Pipelines](http://go.microsoft.com/fwlink/?LinkId=150483) (http://go.microsoft.com/fwlink/?LinkId=150483)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67988-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67988-120">See Also</span></span>  
 [<span data-ttu-id="67988-121">Implémentation d’un test automatisé</span><span class="sxs-lookup"><span data-stu-id="67988-121">Implementing Automated Testing</span></span>](../technical-guides/implementing-automated-testing.md)