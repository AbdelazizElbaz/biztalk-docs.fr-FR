---
title: "Utilisation de grands schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8348036d-6edb-46a3-badd-0223cfe0a92f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5c5ef679070009b5dfb5fdd403d238cfe243cb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-large-schemas"></a>Utilisation de grands schémas
Si vos schémas deviennent très volumineux, vous constaterez que l'actualisation de la vue XSD prend de plus en plus de temps et éventuellement que la réponse d'autres aspects de l'interface utilisateur est affectée. La solution à ce problème consiste à désactiver la fonctionnalité d’actualisation automatique, mais plutôt le manuel **Actualiser** lien dans la vue XSD pour actualiser périodiquement la vue XSD. Pour activer des instructions détaillées sur la façon la fonctionnalité d’actualisation automatique sur un arrêt, voir la procédure « pour activer et désactiver la l’actualisation automatique de la vue XSD » dans [la gestion de la vue XSD](../core/how-to-manage-the-xsd-view.md).  
  
 Performances peuvent également être lentes dans les grands schémas avec plusieurs racines attachés à la **schéma** nœud. Définition de la **référence de racine** propriété peut améliorer les performances de l’interface utilisateur. Paramètre **référence de racine** améliore les performances car le compilateur crée des classes c# pour tous les schémas racine. Une racine unique implique la création d'un nombre moins important de classes.  
  
 **Valider l’Instance** semble lent dans l’interface utilisateur, car une validation est toujours effectuée sur le schéma avant la validation de l’instance. La validation de schémas n'a lieu que dans l'interface utilisateur. Définition de la **référence de racine** propriété améliore également les performances de l’interface utilisateur dans ce cas.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md)