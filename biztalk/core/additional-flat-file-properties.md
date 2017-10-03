---
title: "Propriétés de fichier plat supplémentaires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c88ad2f-b5a8-46e6-b1b8-61ce6ba910d1
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9989d29eadf2487b84e2520755e879cd201b1798
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="additional-flat-file-properties"></a>Propriétés de fichier plat supplémentaires 

## <a name="hidden-properties"></a>Propriétés masquées
Le tableau ci-dessous répertorie les propriétés de nœud de fichier plat supplémentaires qui n'apparaissent pas dans l'Éditeur de schéma. L'utilisation de ces propriétés requiert la modification manuelle du fichier de schéma dans un éditeur de texte.  
  
|Propriété|Valeurs|Valeur par défaut| Description|  
|--------------|------------|-------------------|-----------------|  
|suppress_empty_nodes|**true** ou **false**|**false**|Indique si les nœuds XML vides doivent être supprimés une fois que l'analyseur a généré des données d'instance XML.|  
|generate_empty_nodes|**true** ou **false**|**true**|Génère des nœuds vides pour les enregistrements existant dans les données d'instance XML.|  
|parser_optimization|**vitesse** ou **complexité**|**vitesse**|L'optimisation de la vitesse réduit le temps d'analyse, mais génère quelques ambiguïtés dans les données. L'optimisation de la complexité gère un plus large éventail d'ambiguïtés, au détriment cependant de la vitesse de traitement.|  
|lookahead_depth|N'importe quel nombre entier positif ; zéro (0) indique une antémémoire infinie.|3|Indique jusqu'où une recherche peut être poussée pour trouver des données correspondantes.|  
|allow_early_termination|**true** ou **false**|**false**|Indique si les enregistrements positionnels peuvent se terminer tôt (**true**) ou doit contenir des données pour tous les champs d’enregistrement (**false**).|  
|early_terminate_optional_fields|**true** ou **false**|**false**|Permet une fin anticipée des champs de fin facultatifs (**true**). Si le schéma existant sans cette annotation est ouvert dans l’Éditeur BizTalk, cette annotation figurera lui avec la valeur par défaut (**false**). **Remarque :** l’annotation early_terminate_optional_fields ne s’applique seulement en vigueur si allow_early_termination est définie sur « true ».|  
  
 Toutes ces propriétés sont des attributs de la **/annotation/appinfo/schemaInfo** élément.  
  
 Lorsque **parser_optimization** a la valeur **complexité**, vous devrez peut-être des erreurs de validation par rapport à un schéma lorsqu’il existe de nombreux nœuds facultatifs dans le même groupe ou enregistrement. Vous devrez peut-être définir **lookahead_depth** à zéro (0) pour éviter les erreurs de validation.  
  
## <a name="see-also"></a>Voir aussi  
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Schémas de fichier plat, les propriétés de nœud supplémentaires**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]