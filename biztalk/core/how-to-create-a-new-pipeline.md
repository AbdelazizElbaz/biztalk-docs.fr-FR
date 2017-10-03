---
title: "Comment créer un Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipelines, warnings
- Pipeline Designer, warnings
- pipelines, creating
ms.assetid: bd95325e-1a72-4705-80f6-37ac092d11a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83c1df14c0015ac26b99ad8f0760fe18438e8024
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-pipeline"></a>Création d'un pipeline
Vous pouvez ajouter un modèle de pipeline à votre projet pour créer un pipeline.  
  
> [!WARNING]
>  Vous ne devez pas ajouter un projet qui contient une implémentation d’un composant de pipeline personnalisé à une solution qui contient un projet qui utilise ce composant de pipeline. En effet, si vous le faites, la prochaine fois que vous reconstruirez la solution, vous obtiendrez un message d'erreur indiquant que le fichier dll de sortie est actuellement utilisé par un autre processus.  
  
### <a name="to-create-a-new-pipeline"></a>Pour créer un pipeline  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet où vous souhaitez créer le pipeline.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez un **Pipeline de réception** ou **Pipeline d’envoi** en cliquant dessus une fois.  
  
    > [!NOTE]
    >  Si vous double-cliquez sur le modèle, celui-ci sera automatiquement créé avec le nom par défaut qui s’affiche dans le **nom** champ.  
  
4.  Dans le **nom** , tapez un nom pour le pipeline.  
  
5.  Cliquez sur **Ouvrir**.  
  
     Le nouveau pipeline apparaît dans l'Explorateur de solutions. La surface de conception affiche les étapes du pipeline et un ensemble de composants par défaut.  
  
 Pour plus d’informations sur l’ajout de composants de pipeline au pipeline, consultez [l’ajout d’un composant de pipeline](../core/how-to-add-a-component-to-a-pipeline.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ouvrir un Pipeline](../core/how-to-open-a-pipeline.md)   
 [Comment enregistrer un Pipeline](../core/how-to-save-a-pipeline.md)   
 [L’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md)   
 [Comment accéder à l’aide du clavier](../core/how-to-navigate-with-the-keyboard.md)   
 [Création de Pipelines avec le Concepteur de Pipeline](../core/creating-pipelines-with-pipeline-designer.md)