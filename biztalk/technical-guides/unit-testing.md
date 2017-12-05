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
# <a name="unit-testing"></a>Tests unitaires
BizTalk Server introduit une fonctionnalité qui peut être activée sur de test unitaire la **déploiement** page de propriétés d’un projet BizTalk. La capture d’écran suivante montre ce paramètre de projet accédé à partir du Concepteur de projet lorsque vous cliquez sur un projet, cliquez sur **propriétés**.  
  
 ![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")  
  
 **Capture d’écran de l’onglet du déploiement dans le Concepteur de projet qui expose la propriété de projet activer le test unitaire**  
  
 Cette fonctionnalité permet de créer des tests unitaires pour les schémas, mappages et pipelines. Les rubriques de la documentation de BizTalk Server fournissent des exemples à l’aide de la fonctionnalité de test unitaire. Lorsque cette fonctionnalité est activée et le projet recréé, les classes d'artefact sont dérivées des classes de base suivantes dans le cadre de la prise en charge du test unitaire.  
  
|Type d'artefact|Classe de base|  
|-------------------|----------------|  
|schéma|**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**|  
|Mappage|**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**|  
|Pipeline|**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**|  
  
 Pour plus d’informations sur la fonctionnalité introduite avec BizTalk Server de test unitaire, consultez les rubriques suivantes dans l’aide de BizTalk Server :  
  
-   [À l’aide de la fonctionnalité de schémas et mappages de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150482) (http://go.microsoft.com/fwlink/?LinkId=150482).  
  
-   [À l’aide de la fonctionnalité avec des Pipelines de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150483) (http://go.microsoft.com/fwlink/?LinkId=150483)  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation de tests automatisés](../technical-guides/implementing-automated-testing.md)