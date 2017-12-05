---
title: "Modèles de pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, templates
- Pipeline Designer, templates
- send pipelines, templates
- receive pipelines, templates
ms.assetid: b9779159-e49d-47fb-aa1c-06be5d604c67
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92cff5e945fad7716f31aa666731fe5d6a365146
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="pipeline-templates"></a>Modèles de pipeline
En plus des pipelines par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut deux modèles de pipeline : un modèle de pipeline de réception et un modèle de pipeline d’envoi. À partir d’un projet BizTalk dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez ajouter un modèle de pipeline à votre projet à l’aide de la **ajouter un nouvel élément** commande sur le **projet** menu. À chaque modèle est associé un fichier de stratégie qui détermine les étapes du pipeline et indique quels composants de pipeline sont autorisés dans le pipeline. Vous ne pouvez pas changer l'ordre des étapes d'un fichier de stratégie, mais vous pouvez utiliser le Concepteur de pipeline pour réagencer les composants d'une étape.  
  
 Un fichier de stratégie spécifie :  
  
-   l'ordre des étapes ;  
  
-   le nombre de composants autorisés par étape ;  
  
-   le mode d'exécution de chaque étape.  
  
 Les fichiers de stratégie pour les modèles de pipeline sont stockés dans  *\<répertoire d’installation de BizTalk Server\>*\Developer Tools\Pipeline les fichiers de stratégie. Vous ne devez pas les modifier. Pour modifier un pipeline, ouvrez le modèle de pipeline et utilisez le Concepteur de pipeline. Pour plus d’informations sur l’utilisation du Concepteur de Pipeline, consultez [à l’aide du Concepteur de Pipeline](../core/using-pipeline-designer.md).  
  
 Les fichiers de modèle de pipeline vide sont stockés dans  *\<répertoire d’installation de BizTalk Server\>*\Developer Tools\BizTalkProjectItems et sont nommés BTSReceivePipeline.btp et BTSTransmitPipeline.btp . L’extension de fichier .btp indique que le fichier est un pipeline BizTalk Server et peut être modifié dans le Concepteur de Pipeline.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de Pipelines](../core/types-of-pipelines.md)   
 [Types de composants de Pipeline](../core/types-of-pipeline-components.md)   
 [Pipelines par défaut](../core/default-pipelines.md)   
 [Composants de pipeline](../core/pipeline-components.md)   
 [À propos des pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md)