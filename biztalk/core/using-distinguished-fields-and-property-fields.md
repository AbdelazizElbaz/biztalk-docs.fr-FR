---
title: "À l’aide des champs distinctifs et les champs de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, distinquished fields
- messages, properties
ms.assetid: 264ee15e-be9a-4ba2-9c61-a1570b20378e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18b5d5ee3b29c068b3a37d248b9fb20f07bdfbb2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-distinguished-fields-and-property-fields"></a>À l’aide des champs distinctifs et les champs de propriété
les champs distinctifs constituent des données de message d'un intérêt particulier, que vous utilisez essentiellement pour prendre des décisions ou pour manipuler des données dans l'orchestration.  
  
 Les propriétés de message sont des données (contenu du message) ou des « métadonnées » (informations contextuelles relatives au message, telles que les horodatages ou les informations de routage). Vous pouvez utiliser les propriétés de contexte des messages ou du transport définies par le système, ou définir vos propres propriétés en faisant référence aux champs d'un schéma de propriété. Les propriétés sont utilisées dans les abonnements et les corrélations.  
  
-   Vous pouvez désigner un champ dans un schéma en tant que champ distinctif ou champ de propriété à l’aide de la **promouvoir les propriétés** boîte de dialogue à partir de l’éditeur. Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md)  
  
-   Vous pouvez désigner un champ d'un type .NET comme champ distinctif en le décorant avec l'attribut DistinguishedField, ou comme propriété avec l'attribut Propriété.  
  
## <a name="using-distinguished-fields"></a>Utilisation des champs distinctifs  
 Les champs distinctifs sont désignés par le chemin d'accès au champ dans le message, avec des points séparant le nom du message, les noms des enregistrements qui entourent le champ (le cas échéant) et le nom du champ lui-même :  
  
```  
MyMessage.MyRecord.MySubrecord.MyDistinguishedField  
```  
  
## <a name="using-property-fields"></a>Utilisation des champs de propriété  
 Une fois un champ ajouté au schéma de propriété, sa valeur est accessible dans le code de l'orchestration et dans les expressions de filtre. Pour plus d’informations sur les schémas de propriété, consultez [les schémas de propriété](../core/property-schemas.md).  
  
> [!NOTE]
>  Propriétés de contenu ou les données de message sont essentiellement des raccourcis vers les données sous-jacentes : Si vous modifiez la propriété, les données seront modifiées et vice versa.  
  
 Les propriétés de message sont désignées par le nom du message suivi par l'espace de noms (le schéma) et le nom de propriété entre parenthèses :  
  
```  
MyMessage(Invoice.PropertySchema.InvoiceID)  
```  
  
> [!NOTE]
>  Lorsque vous utilisez un mot clé réservé comme nom d’un champ dans un schéma et promouvoir le champ en sélectionnant Promotion rapide, le nom de propriété du champ est modifié en __\<mot clé réservé\>. (Un double trait de soulignement est ajouté devant le nom de la propriété.) Cependant, si vous utilisez ce nom de propriété dans une expression d'orchestration, vous recevrez une erreur du compilateur lors de la création de l'orchestration.  Pour éviter cette erreur, vous devez ajouter manuellement @ devant le double trait de soulignement. Par exemple :  
>   
>  `MyMessage(Invoice.PropertySchema.@__Name) = "Product Name";`  
  
## <a name="property-sets"></a>Jeux de propriétés  
 Vous pouvez également assigner toutes les propriétés de contexte d'un message (ou jeu de propriétés) aux propriétés de contexte d'un autre message. Pour assigner un jeu de propriétés, vous devez simplement placer un astérisque entre parenthèses après le nom de chaque message, de la même manière que vous placez une propriété entre parenthèses :  
  
```  
MyMessage2(*)=MyMessage1(*);  
```  
  
 Une fois le jeu de propriétés assigné à MyMessage2 dans l'exemple, toutes les propriétés de MyMessage2 ont les mêmes valeurs que les propriétés de MyMessage1.  
  
## <a name="see-also"></a>Voir aussi  
 [Promotion des propriétés](../core/promoting-properties.md)   
 [Utilisation des filtres avec la forme d’un Message de réception](../core/using-filters-with-the-receive-message-shape.md)   
 [À l’aide de Messages dans les Orchestrations](../core/using-messages-in-orchestrations.md)   
 [À propos des propriétés de contexte de message BizTalk](../core/about-biztalk-message-context-properties.md)