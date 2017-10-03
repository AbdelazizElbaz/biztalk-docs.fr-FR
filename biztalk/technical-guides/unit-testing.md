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
# <a name="unit-testing"></a>Tests unitaires
[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]introduit une fonctionnalité qui peut être activée sur de test unitaire la **déploiement** page de propriétés d’un projet BizTalk. La capture d’écran suivante montre ce paramètre de projet accédé à partir du Concepteur de projet lorsque vous cliquez sur un projet, cliquez sur **propriétés**.  
  
 ![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")  
  
 **Capture d’écran de l’onglet du déploiement dans le Concepteur de projet qui expose la propriété de projet activer le test unitaire**  
  
 Cette fonctionnalité permet de créer des tests unitaires pour les schémas, mappages et pipelines. Les rubriques de la [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] documentation fournissent des exemples à l’aide de la fonctionnalité de test unitaire. Lorsque cette fonctionnalité est activée et le projet recréé, les classes d'artefact sont dérivées des classes de base suivantes dans le cadre de la prise en charge du test unitaire.  
  
|Type d'artefact|Classe de base|  
|-------------------|----------------|  
|schéma|**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**|  
|Mappage|**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**|  
|Pipeline|**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**|  
  
 Pour plus d’informations sur l’unité de fonctionnalité de test introduits avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], consultez les rubriques suivantes dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] aide :  
  
-   [À l’aide de la fonctionnalité de schémas et mappages de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150482) (http://go.microsoft.com/fwlink/?LinkId=150482).  
  
-   [À l’aide de la fonctionnalité avec des Pipelines de test unitaire](http://go.microsoft.com/fwlink/?LinkId=150483) (http://go.microsoft.com/fwlink/?LinkId=150483)  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un test automatisé](../technical-guides/implementing-automated-testing.md)