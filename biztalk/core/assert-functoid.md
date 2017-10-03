---
title: "Fonctoid déclarer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e91dac06-f909-4fb2-8c87-828a3dfe2c27
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03237c27e0e35642be197b549c8b0102d9350702
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="assert-functoid"></a>Fonctoid déclarer

## <a name="overview"></a>Vue d'ensemble
Le **Assert** fonctoid génère une valeur de chaîne ou lève une exception basée sur une valeur booléenne. Si vous combinez ce fonctoid avec un ou plusieurs de la **logiques** fonctoids, vous pouvez tester efficacement des hypothèses sur les conditions dans votre carte. Par exemple, si vous disposez d’une carte qui attend des montants de commande fournisseur jamais à dépasser un seuil donné, vous pouvez tester la valeur de bon de commande à l’aide de la **supérieur à** fonctoid et connectez-la à la **Assert**fonctoid. Si le fonctoid logique retourne **True**, le **Assert** fonctoid lève une exception à l’aide d’une chaîne que vous fournissez.  
  
 ![Fonctoid déclarer](../core/media/assertfunctoid.gif "AssertFunctoid")  
  
## <a name="see-also"></a>Voir aussi  
 **Référence du fonctoid déclarer** et **référence des fonctoids logiques**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]