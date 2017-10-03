---
title: "Comment détecter les problèmes de Configuration d’un fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32afc333-934c-4ffb-b1b5-61af07157200
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 322a97aba4ec5e02cf754106df30b0c9f0088e1b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-detect-configuration-issues-for-a-functoid"></a>Détection des problèmes de configuration d'un fonctoid
Vous pouvez rencontrer des problèmes de configuration d'un fonctoid et/ou d'un lien dans le cadre de l'utilisation des mappages. Le Mappeur BizTalk utilise un mécanisme de visualisation facilitant l'identification rapide des problèmes associés à la configuration d'un fonctoid. Cette indication visuelle est rendu sous la forme d’une annotation d’avertissement sur l’icône du fonctoid (pour par exemple, ![Functoid IntelliSense](../core/media/mapper-functoidintellisense.gif "Mapper_FunctoidIntelliSense")) dans la vue de relation. Cette rubrique fournit des informations sur la détection des problèmes de configuration d'un fonctoid.  
  
 L'icône d'avertissement apparaît lorsque le Mappeur détecte qu'un fonctoid n'est pas correctement configuré. Déplacer le curseur de la souris sur le fonctoid affiche également des informations succinctes sur le problème identifié par le Mappeur. Par exemple, si un fonctoid ne possède pas le nombre minimal d'entrées valides, l'info-bulle associée mentionne le nombre de paramètres d'entrée requis.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Cette opération nécessite l'exécution du Mappeur BizTalk.  
  
### <a name="to-detect-configuration-issues-for-a-functoid"></a>Pour détecter les problèmes de configuration d'un fonctoid  
  
1.  Faites glisser le fonctoid requis de la barre d'outils sur la page de grille. Le fonctoid est affiché avec une icône d'avertissement.  
  
2.  Vous pouvez effectuer l'une des opérations suivantes :  
  
    -   déplacer le pointeur de la souris sur le fonctoid. L'info-bulle affiche des informations sur l'erreur et sur ce que vous devez faire.  
  
         La figure suivante montre une info-bulle avec des informations d'erreur lors de la configuration du fonctoid « Addition ».  
  
         ![Détection d’erreur dans la configuration du fonctoid](../core/media/errordetectionfunctoid.gif "ErrorDetectionFunctoid")  
  
    -   double-cliquer sur le fonctoid. Le **configurer \<fonctoid > fonctoid** boîte de dialogue affiche des icônes d’avertissement sur les paramètres d’entrée. Ceci indique que les paramètres d'entrée du fonctoid sélectionné ne sont pas configurés.  
  
         La figure suivante affiche des informations d'erreur sur les paramètres d'entrée du fonctoid « Addition ».  
  
         ![Avertissement affiché lorsque le fonctoid n’est pas configuré](../core/media/configure-input-parameters-warningicon.gif "Configure_input_parameters_WarningIcon")  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)