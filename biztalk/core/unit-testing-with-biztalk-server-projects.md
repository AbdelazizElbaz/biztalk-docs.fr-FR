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
# <a name="unit-testing-with-biztalk-server-projects"></a>Test unitaire avec des projets BizTalk Server
BizTalk Server introduit une fonctionnalité qui peut être activée sur de test unitaire la **déploiement** page de propriétés d’un projet BizTalk. La capture d’écran suivante montre ce paramètre de projet accédé à partir du Concepteur de projet lorsque vous cliquez sur un projet, cliquez sur le **propriétés**.  
  
 ![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")  
  
 **Capture d’écran de l’onglet du déploiement dans le Concepteur de projet qui expose la propriété de projet activer le test unitaire.**  
  
 Cette fonctionnalité permet de créer des tests unitaires pour les schémas, mappages et pipelines. Les rubriques de cette section fournissent des exemples d'utilisation de la fonctionnalité de test unitaire. Lorsque cette fonctionnalité est activée et le projet recréé, les classes d'artefact sont dérivées des classes de base suivantes dans le cadre de la prise en charge du test unitaire.  
  
|Type d'artefact|Classe de base|  
|-------------------|----------------|  
|schéma|**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**|  
|Mappage|**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**|  
|Pipeline|**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [À l’aide de la fonctionnalité de schémas et mappages de test unitaire](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)  
  
-   [À l’aide de la fonctionnalité avec des Pipelines de test unitaire](../core/using-the-unit-testing-feature-with-pipelines.md)  
  
## <a name="related-sections"></a>Sections connexes  
 [Travailler avec des Tests unitaires (Visual Studio)](http://go.microsoft.com/fwlink/?LinkId=128890)